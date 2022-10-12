---
title: Live Share – Erste Schritte
author: surbhigupta
description: In diesem Modul erfahren Sie mehr über die Funktionen des Live Share SDK, RSC-Berechtigungen und Live-Datenstrukturen.
ms.topic: conceptual
ms.localizationpriority: high
ms.author: v-ypalikila
ms.date: 04/07/2022
ms.openlocfilehash: 6d2e1dc9d49ab1ec551fd814ba8baa330e9ace3f
ms.sourcegitcommit: 0fa0bc081da05b2a241fd8054488d9fd0104e17b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2022
ms.locfileid: "68552549"
---
# <a name="live-share-core-capabilities"></a>Live Share Kernfunktionen

:::image type="content" source="../assets/images/teams-live-share/Teams-live-share-core-capabilities-hero.png" alt-text="Teams Live Share":::

Das Live Share SDK kann mit minimalem Aufwand den `sidePanel` und `meetingStage` Kontexten Ihrer Besprechungserweiterung hinzugefügt werden. Dieser Artikel konzentriert sich auf die Integration des Live Share SDK in Ihre App und wichtige Funktionen des SDK.

## <a name="install-the-javascript-sdk"></a>Installieren des JavaScript SDK

Das [Live Share SDK](https://github.com/microsoft/live-share-sdk) ist ein auf [npm](https://www.npmjs.com/package/@microsoft/live-share) veröffentlichtes JavaScript-Paket, das Sie über npm oder Yarn herunterladen können.

### <a name="npm"></a>npm

```bash
npm install @microsoft/live-share@next --save
```

### <a name="yarn"></a>Garn

```bash
yarn add @microsoft/live-share@next
```

## <a name="register-rsc-permissions"></a>Registrieren von RSC-Berechtigungen

Um das Live Share SDK für Ihre Besprechungserweiterung zu aktivieren, müssen Sie Ihrem App-Manifest zunächst die folgenden RSC-Berechtigungen hinzufügen:

```json
{
  // ...rest of your manifest here
  "configurableTabs": [
    {
        "configurationUrl": "<<YOUR_CONFIGURATION_URL>>",
        "canUpdateConfiguration": true,
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

1. Initialisieren Sie [LiveShareClient](/javascript/api/@microsoft/live-share/liveshareclient).
2. Definieren der vertraulichen Daten, die Sie schützen möchten. Beispiel: `SharedMap`.
3. Dem Container beitreten.

Beispiel:

# <a name="javascript"></a>[JavaScript](#tab/javascript)

```javascript
import { LiveShareClient } from "@microsoft/live-share";
import { SharedMap } from "fluid-framework";

// Join the Fluid container
const liveShare = new LiveShareClient();
const schema = {
  initialObjects: { exampleMap: SharedMap },
};
const { container } = await liveShare.joinContainer(schema);

// ... ready to start app sync logic
```

# <a name="typescript"></a>[TypeScript](#tab/typescript)

```TypeScript
import { LiveShareClient } from "@microsoft/live-share";
import { ContainerSchema, SharedMap } from "fluid-framework";

// Join the Fluid container
const liveShare = new LiveShareClient();
const schema: ContainerSchema = {
  initialObjects: { exampleMap: SharedMap },
};
const { container } = await liveShare.joinContainer(schema);

// ... ready to start app sync logic
```

---

Das war alles, was zum Einrichten des Containers und zum Teilnehmen an der Besprechungssitzung erforderlich war. Sehen wir uns nun die verschiedenen Arten von _verteilten Datenstrukturen_ an, die Sie mit dem Live Share SDK verwenden können.

> [!TIP]
> Stellen Sie sicher, dass das Teams Client SDK initialisiert wird, bevor Sie die Live Share-APIs verwenden.

## <a name="fluid-distributed-data-structures"></a>Fluid-verteilte Datenstrukturen

Das Live Share SDK unterstützt alle in Fluid Framework enthaltenen [verteilten Datenstrukturen](https://fluidframework.com/docs/data-structures/overview/). Hier ist eine kurze Übersicht über einige der verschiedenen verfügbaren Objekttypen:

| Freigegebenes Objekt                                                                       | Beschreibung                                                                                                                             |
| ----------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------- |
| [SharedMap](https://fluidframework.com/docs/data-structures/map/)                   | Ein verteilter Schlüsselwertspeicher. Legen Sie ein beliebiges JSON-serialisierbares Objekt für einen bestimmten Schlüssel fest, um dieses Objekt für alle Teilnehmer der Sitzung zu synchronisieren. |
| [SharedSegmentSequence](https://fluidframework.com/docs/data-structures/sequences/) | Eine listenähnliche Datenstruktur zum Speichern einer Gruppe von Elementen (als Segmente bezeichnet) an festgelegten Positionen.                                               |
| [SharedString](https://fluidframework.com/docs/data-structures/string/)             | Sequenz mit verteilter Zeichenfolge, die für die Bearbeitung von Dokumenttext optimiert ist.                                                                |

Sehen wir uns an, wie `SharedMap` funktioniert. In diesem Beispiel haben wir `SharedMap` verwendet, um ein Wiedergabelistenfeature zu erstellen.

# <a name="javascript"></a>[JavaScript](#tab/javascript)

```javascript
import { LiveShareClient } from "@microsoft/live-share";
import { SharedMap } from "fluid-framework";

// Join the Fluid container
const liveShare = new LiveShareClient();
const schema = {
  initialObjects: { playlistMap: SharedMap },
};
const { container } = await liveShare.joinContainer(schema);
const playlistMap = container.initialObjects.playlistMap as SharedMap;

// Register listener for changes to values in the map
playlistMap.on("valueChanged", (changed, local) => {
  const video = playlistMap.get(changed.key);
  // Update UI with added video
});

function onClickAddToPlaylist(video) {
  // Add video to map
  playlistMap.set(video.id, video);
}
```

# <a name="typescript"></a>[TypeScript](#tab/typescript)

```TypeScript
import { LiveShareClient } from "@microsoft/live-share";
import { ContainerSchema, SharedMap, IValueChanged } from "fluid-framework";

// Join the Fluid container
const liveShare = new LiveShareClient();
const schema: ContainerSchema = {
  initialObjects: { exampleMap: SharedMap },
};
const { container } = await liveShare.joinContainer(schema);
const playlistMap = container.initialObjects.playlistMap as SharedMap;

// Declare interface for object being stored in map
interface IVideo {
  id: string;
  url: string;
}

// Register listener for changes to values in the map
playlistMap.on("valueChanged", (changed: IValueChanged, local: boolean) => {
  const video: IVideo | undefined = playlistMap.get(changed.key);
  // Update UI with added video
});

function onClickAddToPlaylist(video: IVideo) {
  // Add video to map
  playlistMap.set(video.id, video);
}
```

---

> [!NOTE]
> Kern-Fluid Framework DDS-Objekte unterstützen die Überprüfung der Besprechungsrolle nicht. Jeder in der Besprechung kann Daten ändern, die über diese Objekte gespeichert sind.

## <a name="live-share-data-structures"></a>Live Share-Datenstrukturen

Das Live Share SDK enthält eine Reihe neuer Live Share-Klassen `SharedObject` , die zustandsbehaftete und zustandslose Objekte bereitstellen, die nicht im Fluid-Container gespeichert sind. Wenn Sie beispielsweise ein Laserpointerfeature in Ihre App integrieren möchten, z. B. die beliebte PowerPoint Live-Integration, können Sie unsere Objekte `LiveEvent` bzw. `LiveState` verwenden.

| Live-Objekt                                                        | Beschreibung                                                                                                                             |
| ------------------------------------------------------------------ | --------------------------------------------------------------------------------------------------------------------------------------- |
| [LivePresence](/javascript/api/@microsoft/live-share/livepresence) | Sehen Sie, welche Benutzer online sind, legen Sie benutzerdefinierte Eigenschaften für jeden Benutzer fest, und übertragen Sie Änderungen an ihren Anwesenheitsinformationen.                               |
| [LiveEvent](/javascript/api/@microsoft/live-share/liveevent)       | Übertragen einzelner Ereignisse mit benutzerdefinierten Datenattributen in der Nutzlast.                                                             |
| [Livestate](/javascript/api/@microsoft/live-share/livestate)       | Ähnlich wie bei SharedMap, einem verteilten Schlüsselwertspeicher, der eingeschränkte Zustandsänderungen basierend auf der Rolle zulässt, z. B. dem Referenten. |
| [LiveTimer](/javascript/api/@microsoft/live-share/livetimer)       | Synchronisieren eines Countdown-Timers für ein bestimmtes Intervall.                                                                                     |

### <a name="livepresence-example"></a>LivePresence-Beispiel

:::image type="content" source="../assets/images/teams-live-share/live-share-presence.png" alt-text="Teams Live Share-Anwesenheit":::

Die `LivePresence` Klasse erleichtert das Nachverfolgen, wer sich in der Sitzung befindet. Beim Aufrufen der `.initialize()` oder `.updatePresence()` Methoden können Sie benutzerdefinierte Metadaten für diesen Benutzer zuweisen, z. B. Name oder Profilbild. Durch das Überwachen von `presenceChanged` Ereignissen empfängt jeder Client das neueste `LivePresenceUser` Objekt, wodurch alle Anwesenheitsaktualisierungen in einem einzigen Datensatz für jeden eindeutigen `userId`Datensatz zusammengefasst werden.

> [!NOTE]
> Die jedem `LivePresenceUser` zugewiesene Standardeinstellung `userId` ist eine zufällige UUID und ist nicht direkt an eine AAD-Identität gebunden. Sie können dies außer Kraft setzen, indem Sie einen benutzerdefinierten `userId` Schlüssel als Primärschlüssel festlegen, wie im folgenden Beispiel gezeigt.

Beispiel:

# <a name="javascript"></a>[JavaScript](#tab/javascript)

```javascript
import {
  LiveShareClient,
  LivePresence,
  PresenceState,
} from "@microsoft/live-share";

// Join the Fluid container
const liveShare = new LiveShareClient();
const schema = {
  initialObjects: {
    presence: LivePresence,
  },
};
const { container } = await liveShare.joinContainer(schema);
const presence = container.initialObjects.presence;

// Register listener for changes to presence
presence.on("presenceChanged", (userPresence, local) => {
  // Update UI with presence
});

// Start tracking presence
presence.initialize("YOUR_CUSTOM_USER_ID", {
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

# <a name="typescript"></a>[TypeScript](#tab/typescript)

```TypeScript
import {
  LiveShareClient,
  LivePresence,
  PresenceState,
  LivePresenceUser,
} from "@microsoft/live-share";

// Declare interface for type of custom data for user
interface ICustomUserData {
  name: string;
  picture: string;
}

// Join the Fluid container
const liveShare = new LiveShareClient();
const schema = {
  initialObjects: {
    presence: LivePresence<ICustomUserData>,
  },
};
const { container } = await liveShare.joinContainer(schema);
const presence = container.initialObjects.presence as LivePresence<ICustomUserData>;

// Register listener for changes to presence
presence.on("presenceChanged", (userPresence: LivePresenceUser<ICustomUserData>, local: boolean) => {
  // Update UI with presence
});

// Start tracking presence
presence.initialize("YOUR_CUSTOM_USER_ID", {
  name: "Anonymous",
  picture: "DEFAULT_PROFILE_PICTURE_URL",
});

function onUserDidLogIn(userName: string, profilePicture: string) {
  presence.updatePresence(PresenceState.online, {
    name: userName,
    picture: profilePicture,
  });
}
```

---

### <a name="liveevent-example"></a>LiveEvent-Beispiel

:::image type="content" source="../assets/images/teams-live-share/live-share-event.png" alt-text="Teams Live Share-Ereignis zum Anzeigen von Benachrichtigungen":::

`LiveEvent` ist eine hervorragende Möglichkeit, einfache Ereignisse an andere Clients in einer Besprechung zu senden. Es ist nützlich für Szenarien wie das Senden von Sitzungsbenachrichtigungen.

# <a name="javascript"></a>[JavaScript](#tab/javascript)

```javascript
import { LiveEvent, LiveShareClient } from "@microsoft/live-share";

// Join the Fluid container
const liveShare = new LiveShareClient();
const schema = {
  initialObjects: { notifications: LiveEvent },
};
const { container } = await liveShare.joinContainer(schema);
const { notifications } = container.initialObjects;

// Register listener for incoming notifications
notifications.on("received", (event, local) => {
  let notificationToDisplay;
  if (local) {
    notificationToDisplay = `You ${event.text}`;
  } else {
    notificationToDisplay = `${event.senderName} ${event.text}`;
  }
  // Display notification in your UI
});

// Start listening for incoming notifications
await notifications.initialize();

notifications.sendEvent({
  senderName: "LOCAL_USER_NAME",
  text: "joined the session",
});
```

# <a name="typescript"></a>[TypeScript](#tab/typescript)

```TypeScript
import { LiveShareClient, LiveEvent, ILiveEvent } from "@microsoft/live-share";

// Declare interface for type of custom data for user
interface ICustomEvent extends ILiveEvent {
  senderName: string;
  text: string;
}

// Join the Fluid container
const liveShare = new LiveShareClient();
const schema = {
  initialObjects: {
    notifications: LiveEvent<ICustomEvent>,
  },
};
const { container } = await liveShare.joinContainer(schema);
const notifications = container.initialObjects.notifications as LiveEvent<ICustomEvent>;

// Register listener for incoming notifications
notifications.on("received", (event: ICustomEvent, local: boolean) => {
  let notificationToDisplay: string;
  if (local) {
    notificationToDisplay = `You ${event.text}`;
  } else {
    notificationToDisplay = `${event.senderName} ${event.text}`;
  }
  // Display notification in your UI
});

// Start listening for incoming notifications
await notifications.initialize();

notifications.sendEvent({
  senderName: "LOCAL_USER_NAME",
  text: "joined the session",
});
```

---

### <a name="livetimer-example"></a>LiveTimer-Beispiel

:::image type="content" source="../assets/images/teams-live-share/live-share-timer.png" alt-text="Countdown-Timer für Teams Live Share":::

`LiveTimer` ermöglicht Szenarien, die ein Zeitlimit haben, z. B. einen Gruppenmeditationszeitgeber oder einen Rundentimer für ein Spiel.

# <a name="javascript"></a>[JavaScript](#tab/javascript)

```javascript
import { LiveShareClient, LiveTimer } from "@microsoft/live-share";

// Join the Fluid container
const liveShare = new LiveShareClient();
const schema = {
  initialObjects: { timer: LiveTimer },
};
const { container } = await liveShare.joinContainer(schema);
const { timer } = container.initialObjects;

// Register listener for when the timer starts its countdown
timer.on("started", (config, local) => {
  // Update UI to show timer has started
});

// Register listener for when a paused timer has resumed
timer.on("played", (config, local) => {
  // Update UI to show timer has resumed
});

// Register listener for when a playing timer has paused
timer.on("paused", (config, local) => {
  // Update UI to show timer has paused
});

// Register listener for when a playing timer has finished
timer.on("finished", (config) => {
  // Update UI to show timer is finished
});

// Register listener for the timer progressed by 20 milliseconds
timer.on("onTick", (milliRemaining) => {
  // Update UI to show remaining time
});

// Start synchronizing timer events for users in session
await timer.initialize();

// Start a 60 second timer
const durationInMilliseconds = 1000 * 60;
timer.start(durationInMilliseconds);

// Pause the timer for users in session
timer.pause();

// Resume the timer for users in session
timer.play();
```

# <a name="typescript"></a>[TypeScript](#tab/typescript)

```TypeScript
import {
  LiveShareClient,
  LiveTimer,
  LiveTimerEvents,
  ITimerConfig,
} from "@microsoft/live-share";

// Join the Fluid container
const liveShare = new LiveShareClient();
const schema = {
  initialObjects: { timer: LiveTimer },
};
const { container } = await liveShare.joinContainer(schema);
const timer = container.initialObjects.timer as LiveTimer;

// Register listener for when the timer starts its countdown
timer.on(LiveTimerEvents.started, (config: ITimerConfig, local: boolean) => {
  // Update UI to show timer has started
});

// Register listener for when a paused timer has resumed
timer.on(LiveTimerEvents.played, (config: ITimerConfig, local: boolean) => {
  // Update UI to show timer has resumed
});

// Register listener for when a playing timer has paused
timer.on(LiveTimerEvents.paused, (config: ITimerConfig, local: boolean) => {
  // Update UI to show timer has paused
});

// Register listener for when a playing timer has finished
timer.on(LiveTimerEvents.finished, (config: ITimerConfig) => {
  // Update UI to show timer is finished
});

// Register listener for the timer progressed by 20 milliseconds
timer.on(LiveTimerEvents.onTick, (milliRemaining: number) => {
  // Update UI to show remaining time
});

// Start synchronizing timer events
await timer.initialize();

// Start a 60 second timer for users in session
const durationInMilliseconds = 1000 * 60;
timer.start(durationInMilliseconds);

// Pause the timer for users in session
timer.pause();

// Resume the timer for users in session
timer.play();
```

---

## <a name="role-verification-for-live-data-structures"></a>Rollenüberprüfung für Livedatenstrukturen

Besprechungen in Teams können von Einzelanrufen bis hin zu Besprechungen mit allen Mitarbeitern reichen und Mitglieder aus verschiedenen Organisationen umfassen. Liveobjekte unterstützen die Rollenüberprüfung, sodass Sie die Rollen definieren können, die Nachrichten für jedes einzelne Liveobjekt senden dürfen. Sie können beispielsweise festlegen, dass nur Besprechungsreferenten und Organisatoren die Videowiedergabe steuern können, Gäste und Teilnehmer jedoch weiterhin die Möglichkeit haben, Videos anzufordern, die sie als Nächstes ansehen können.

> [!NOTE]
> Die `LivePresence` Klasse unterstützt die Rollenüberprüfung nicht. Das `LivePresenceUser` Objekt verfügt über eine `getRoles` Methode, die die Besprechungsrollen für einen bestimmten Benutzer zurückgibt.

Beispiel für die Verwendung von `LiveState`:

# <a name="javascript"></a>[JavaScript](#tab/javascript)

```javascript
import { LiveShareClient, LiveState, UserMeetingRole } from "@microsoft/live-share";

// Join the Fluid container
const liveShare = new LiveShareClient();
const schema = {
  initialObjects: { appState: LiveState },
};
const { container } = await liveShare.joinContainer(schema);
const { appState } = container.initialObjects;

// Register listener for changes to state and corresponding custom data
appState.on("stateChanged", (state, data, local) => {
  // Update local app state
});

// Set roles who can change state and start listening for changes
const allowedRoles = [UserMeetingRole.organizer, UserMeetingRole.presenter];
appState.initialize(allowedRoles);

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

# <a name="typescript"></a>[TypeScript](#tab/typescript)

```TypeScript
import { LiveShareClient, LiveState, UserMeetingRole } from "@microsoft/live-share";

// Declare interface for type of custom data for user
interface ICustomState {
  documentId: string;
  presentingUserId?: string;
}

// Join the Fluid container
const liveShare = new LiveShareClient();
const schema = {
  initialObjects: {
    appState: LiveState<ICustomState>,
  },
};
const { container } = await liveShare.joinContainer(schema);
const appState = container.initialObjects.appState as LiveState<ICustomState>;

// Register listener for changes to state and corresponding custom data
appState.on("stateChanged", (state: string, data: ICustomState | undefined, local: boolean) => {
  // Update local app state
});

// Set roles who can change state and start listening for changes
const allowedRoles: UserMeetingRole[] = [UserMeetingRole.organizer, UserMeetingRole.presenter];
appState.initialize(allowedRoles);

function onSelectEditMode(documentId: string) {
  appState.changeState("editing", {
    documentId,
  });
}

function onSelectPresentMode(documentId: string) {
  appState.changeState("presenting", {
    documentId,
    presentingUserId: "LOCAL_USER_ID",
  });
}
```

---

Achten Sie darauf, dass Ihre Kunden ihre Szenarien verstehen, bevor Sie die Rollenüberprüfung in Ihre App implementieren, insbesondere für die Rolle **Organisator**. Es gibt keine Garantie dafür, dass ein Besprechungsorganisator in der Besprechung anwesend ist. Als Faustregel gilt, dass alle Benutzer entweder **Organisator** oder **Referent** sind, wenn sie innerhalb einer Organisation zusammenarbeiten. Wenn ein Benutzer ein **Teilnehmer** ist, handelt es sich in der Regel um eine absichtliche Entscheidung im Namen eines Besprechungsorganisators.

> [!NOTE]
> Derzeit unterstützt Live Share keine Kanalbesprechungen.

## <a name="code-samples"></a>Codebeispiele

| Beispielname | Beschreibung                                                     | JavaScript                                  |
| ----------- | --------------------------------------------------------------- | ------------------------------------------- |
| Dice Roller | Ermöglichen Sie allen verbundenen Clients, einen Würfel zu rollen und das Ergebnis anzuzeigen. | [Anzeigen](https://aka.ms/liveshare-diceroller) |
| Agile Poker | Ermöglichen Sie allen verbundenen Clients, Agile Poker zu spielen.               | [Anzeigen](https://aka.ms/liveshare-agilepoker) |

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Live Teilen von Medien](teams-live-share-media-capabilities.md)

## <a name="see-also"></a>Siehe auch

- [GitHub-Repository](https://github.com/microsoft/live-share-sdk)
- [Live Share SDK-Referenzdokumente](/javascript/api/@microsoft/live-share/)
- [Live Share Media SDK-Referenzdokumente](/javascript/api/@microsoft/live-share-media/)
- [Live Share – FAQ](teams-live-share-faq.md)
- [Teams-Apps in Besprechungen](teams-apps-in-meetings.md)
