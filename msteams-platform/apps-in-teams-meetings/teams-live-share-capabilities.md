---
title: Live Share – Erste Schritte
description: In diesem Modul erfahren Sie mehr über Live Share SDK-Funktionen, RSC-Berechtigungen und kurzlebige Datenstrukturen.
ms.topic: concept
ms.localizationpriority: high
ms.author: v-ypalikila
ms.openlocfilehash: c6ea321cf9a0bee33b44c54f273662663f23b433
ms.sourcegitcommit: eeaa8cbb10b9dfa97e9c8e169e9940ddfe683a7b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/27/2022
ms.locfileid: "65756604"
---
---

# <a name="live-share-capabilities"></a>Live Share-Funktionen

Das Live Share SDK kann mit minimalem Aufwand den `sidePanel` und `meetingStage` Kontexten Ihrer Besprechungserweiterung hinzugefügt werden. Dieser Artikel konzentriert sich auf die Integration des Live Share SDK in Ihre App und wichtige Funktionen des SDK.

> [!Note]
> Derzeit werden nur geplante Besprechungen unterstützt, und alle Teilnehmer müssen sich im Besprechungskalender befinden. Besprechungstypen wie 1:1-Anrufe, Gruppenanrufe und Besprechungen werden derzeit nicht unterstützt.

:::image type="content" source="../assets/images/teams-live-share/Teams-live-share-dashboard.png" alt-text="Teams Live Share":::

## <a name="install-the-javascript-sdk"></a>Installieren des JavaScript SDK

Das [Live Share SDK](https://github.com/microsoft/live-share-sdk) ist ein auf [npm](https://www.npmjs.com/package/@microsoft/live-share) veröffentlichtes JavaScript-Paket, das Sie über npm oder Yarn herunterladen können.

**npm**

```bash
$ npm install @microsoft/live-share --save
```

**Yarn**

```bash
$ yarn add @microsoft/live-share
```

## <a name="register-rsc-permissions"></a>Registrieren von RSC-Berechtigungen

Um das Live Share SDK für Ihre Besprechungserweiterung zu aktivieren, müssen Sie Ihrem App-Manifest zunächst die folgenden RSC-Berechtigungen hinzufügen:

```json
{
  // ...rest of your manifest here
  "configurableTabs": [
    {
        "configurationUrl": "https://<<BASE_URI_ORIGIN>>/config",
        "canUpdateConfiguration": false,
        "scopes": [
            "groupchat"
        ],
        "context": [
            "meetingSidePanel",
            "meetingStage"
        ]
    }
  ],
  "validDomains": [
    "<<BASE_URI_ORIGIN>>"
  ],
  "authorization": {
    "permissions": {
      "resourceSpecific": [
        // ...other permissions here
        {
          "name": "LiveShareSession.ReadWrite.Chat",
          "type": "Delegated"
        },
        {
          "name": "LiveShareSession.ReadWrite.Group",
          "type": "Delegated"
        },
        {
          "name": "MeetingStage.Write.Chat",
          "type": "Delegated"
        },
        {
          "name": "ChannelMeetingStage.Write.Group",
          "type": "Delegated"
        }
      ]
    }
  }
}
```

## <a name="join-a-meeting-session"></a>Beitreten einer Besprechungssitzung

Führen Sie die Schritte aus, um einer Sitzung beizutreten, die der Besprechung eines Benutzers zugeordnet ist:

1. Initialisieren des Teams-Client-SDK
2. Initialisieren des [TeamsFluidClient](/javascript/api/@microsoft/live-share/teamsfluidclient)
3. Definieren der vertraulichen Daten, die Sie schützen möchten. Beispiel: `SharedMap`
4. Dem Container beitreten

Beispiel:

```javascript
import * as microsoftTeams from "@microsoft/teams-js";
import { TeamsFluidClient } from "@microsoft/live-share";
import { SharedMap } from "fluid-framework";

// Initialize the Teams Client SDK
await microsoftTeams.app.initialize();

// Setup the Fluid container
const client = new TeamsFluidClient();
const schema = {
  initialObjects: { exampleMap: SharedMap },
};
const { container } = await client.joinContainer(schema);

// ... ready to start app sync logic
```

Das war alles, was zum Einrichten des Containers und zum Teilnehmen an der Besprechungssitzung erforderlich war. Sehen wir uns nun die verschiedenen Arten von _verteilten Datenstrukturen_ an, die Sie mit dem Live Share SDK verwenden können.

## <a name="fluid-distributed-data-structures"></a>Fluid-verteilte Datenstrukturen

Das Live Share SDK unterstützt alle in Fluid Framework enthaltenen [verteilten Datenstrukturen](https://fluidframework.com/docs/data-structures/overview/). Hier ist eine kurze Übersicht über einige der verschiedenen verfügbaren Objekttypen:

| Freigegebenes Objekt                                                                       | Beschreibung                                                                                                                                  |
| ----------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------- |
| [SharedMap](https://fluidframework.com/docs/data-structures/map/)                   | Ein verteilter Schlüsselwertspeicher. Legen Sie ein beliebiges JSON-serialisierbares Objekt für einen bestimmten Schlüssel fest, um dieses Objekt für alle Teilnehmer der Sitzung zu synchronisieren. |
| [SharedSegmentSequence](https://fluidframework.com/docs/data-structures/sequences/) | Eine listenähnliche Datenstruktur zum Speichern einer Gruppe von Elementen (als Segmente bezeichnet) an festgelegten Positionen.                                                    |
| [SharedString](https://fluidframework.com/docs/data-structures/string/)             | Sequenz mit verteilter Zeichenfolge, die für die Bearbeitung von Dokumenttext optimiert ist.                                                                     |

Sehen wir uns an, wie `SharedMap` funktioniert. In diesem Beispiel haben wir `SharedMap` verwendet, um ein Wiedergabelistenfeature zu erstellen.

```javascript
import { SharedMap } from "fluid-framework";
// ...
const schema = {
  initialObjects: { playlistMap: SharedMap },
};
const { container } = await client.joinContainer(schema);
const { playlistMap } = container.initialObjects;

// Listen for changes to values in the map
playlistMap.on("valueChanged", (changed, local) => {
  const video = playlistMap.get(changed.key);
  // Update UI with added video
});

function onClickAddToPlaylist(video) {
  // Add video to map
  playlistMap.set(video.id, video);
}
// ...
```

> [!Note]
> Kern-Fluid Framework DDS-Objekte unterstützen die Überprüfung der Besprechungsrolle nicht. Jeder in der Besprechung kann Daten ändern, die über diese Objekte gespeichert sind.

## <a name="live-share-ephemeral-data-structures"></a>Live Share kurzlebige Datenstrukturen

Das Live Share SDK enthält eine Reihe neuer kurzlebiger `SharedObject`-Klassen, die zustandsbehaftete und zustandslose Objekte bereitstellen, die nicht im Fluid-Container gespeichert sind. Wenn Sie beispielsweise ein Laserpointerfeature in Ihre App integrieren möchten, z. B. die beliebte PowerPoint Live-Integration, können Sie unsere Objekte `EphemeralEvent` bzw. `EphemeralState` verwenden.

| Kurzlebiges Objekt                                                                                                       | Beschreibung                                                                                                                     |
| ---------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------- |
| [EphemeralPresence](/javascript/api/@microsoft/live-share/ephemeralpresence) | Sehen Sie, welche Benutzer online sind, legen Sie benutzerdefinierte Eigenschaften für jeden Benutzer fest, und übertragen Sie Änderungen an ihren Anwesenheitsinformationen.                       |
| [EphemeralEvent](/javascript/api/@microsoft/live-share/ephemeralevent)       | Übertragen einzelner Ereignisse mit benutzerdefinierten Datenattributen in der Nutzlast.                                                     |
| [EphemeralState](/javascript/api/@microsoft/live-share/ephemeralstate)       | Ähnlich wie bei SharedMap, einem verteilten Schlüsselwertspeicher, der eingeschränkte Zustandsänderungen basierend auf der Rolle zulässt, z. B. dem Referenten.|

### <a name="ephemeralpresence-example"></a>EphemeralPresence-Beispiel

Die `EphemeralPresence`-Klasse erleichtert das Nachverfolgen, wer an einer Besprechung teilnimmt. Beim Aufrufen der Methoden `.start()` bzw. `.updatePresence()` können Sie benutzerdefinierte Metadaten für diesen Benutzer zuweisen, z. B. einen eindeutigen Bezeichner oder Namen.

Beispiel:

```javascript
import { EphemeralPresence, PresenceState } from "@microsoft/live-share";
// ...
const schema = {
  initialObjects: { presence: EphemeralPresence },
};
const { container } = await client.joinContainer(schema);
const { presence } = container.initialObjects;

// Listen for changes to presence
presence.on("presenceChanged", (userPresence, local) => {
  // Update UI with presence
});

// Start tracking presence
presence.start("YOUR_CUSTOM_USER_ID", {
  name: "Anonymous",
  picture: "DEFAULT_PROFILE_PICTURE_URL",
});

function onUserDidLogIn(userName, profilePicture) {
  presence.updatePresence(PresenceState.online, {
    name: userName,
    picture: profilePicture,
  });
}
```

### <a name="ephemeralevent-example"></a>EphemeralEvent-Beispiel

`EphemeralEvent` ist eine hervorragende Möglichkeit, einfache Ereignisse an andere Clients in einer Besprechung zu senden. Es ist nützlich für Szenarien wie das Senden von Sitzungsbenachrichtigungen.

```javascript
import { EphemeralEvent } from "@microsoft/live-share";
// ...
const schema = {
  initialObjects: { notifications: EphemeralEvent },
};
const { container } = await client.joinContainer(schema);
const { notifications } = container.initialObjects;

// Listen for incoming notifications
notifications.on("received", (event, local) => {
  let notificationToDisplay;
  if (local) {
    notificationToDisplay = `You ${event.text}`;
  } else {
    notificationToDisplay = `${event.senderName} ${event.text}`;
  }
  // Display notification in your UI
});

// Start tracking notifications
await notifications.start();

notifications.sendEvent({
  senderName: "LOCAL_USER_NAME",
  text: "joined the session",
});
```

## <a name="role-verification-for-ephemeral-data-structures"></a>Rollenüberprüfung für kurzlebige Datenstrukturen

Besprechungen in Teams können von Einzelanrufen bis hin zu Besprechungen mit allen Mitarbeitern reichen und Mitglieder aus verschiedenen Organisationen umfassen. Kurzlebige Objekte unterstützen die Rollenüberprüfung, sodass Sie die Rollen definieren können, die zum Senden von Nachrichten für jedes einzelne kurzlebige Objekt zulässig sind. Sie können beispielsweise festlegen, dass nur Besprechungsreferenten und Organisatoren die Videowiedergabe steuern können, Gäste und Teilnehmer jedoch weiterhin die Möglichkeit haben, Videos anzufordern, die sie als Nächstes ansehen können.

Beispiel:

```javascript
import { EphemeralState, UserMeetingRole } from "@microsoft/live-share";
// ...
const schema = {
  initialObjects: { appState: EphemeralState },
};
const { container } = await client.joinContainer(schema);
const { appState } = container.initialObjects;

// Listen for changes to values in the map
appState.on("stateChanged", (state, value, local) => {
  // Update local app state
});

// Set roles who can change state and start
const allowedRoles = [UserMeetingRole.organizer, UserMeetingRole.presenter];
appState.start(allowedRoles);

function onSelectEditMode(documentId) {
  appState.changeState("editing", {
    documentId,
  });
}

function onSelectPresentMode(documentId) {
  appState.changeState("presenting", {
    documentId,
    presentingUserId: "LOCAL_USER_ID",
  });
}
```

Achten Sie darauf, dass Ihre Kunden ihre Szenarien verstehen, bevor Sie die Rollenüberprüfung in Ihre App implementieren, insbesondere für die Rolle **Organisator**. Es gibt keine Garantie dafür, dass ein Besprechungsorganisator in der Besprechung anwesend ist. Als Faustregel gilt, dass alle Benutzer entweder **Organisator** oder **Referent** sind, wenn sie innerhalb einer Organisation zusammenarbeiten. Wenn ein Benutzer ein **Teilnehmer** ist, handelt es sich in der Regel um eine absichtliche Entscheidung im Namen eines Besprechungsorganisators.

## <a name="code-samples"></a>Codebeispiele

| Beispielname | Beschreibung  | JavaScript  |
| ----------- | ---------------------------------------------- | -------------- |
| Dice Roller | Ermöglichen Sie allen verbundenen Clients, einen Würfel zu rollen und das Ergebnis anzuzeigen. | [Anzeigen](https://aka.ms/liveshare-diceroller) |
| Agile Poker | Ermöglichen Sie allen verbundenen Clients, Agile Poker zu spielen.| [Anzeigen](https://aka.ms/liveshare-agilepoker) |

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Live Share-Medienfunktionen](teams-live-share-media-capabilities.md)

## <a name="see-also"></a>Siehe auch

* [GitHub-Repository](https://github.com/microsoft/live-share-sdk)
* [Live Share SDK-Referenzdokumente](/javascript/api/@microsoft/live-share/)
* [Live Share Media SDK-Referenzdokumente](/javascript/api/@microsoft/live-share-media/)
* [Live Share – FAQ](teams-live-share-faq.md)
* [Teams-Apps in Besprechungen](teams-apps-in-meetings.md)
