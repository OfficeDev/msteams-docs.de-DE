---
title: Live Share-Medienfunktionen
author: surbhigupta
description: In diesem Modul erfahren Sie mehr über die Medienfunktionen von Live Share, Unterbrechungen und Wartepunkte, Audio-Ducking und das Synchronisieren von Video und Audio.
ms.topic: conceptual
ms.localizationpriority: high
ms.author: v-ypalikila
ms.date: 04/07/2022
ms.openlocfilehash: bf9d7c071a337a56373a9c58879d23a8d2638af7
ms.sourcegitcommit: 79d525c0be309200e930cdd942bc2c753d0b718c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/19/2022
ms.locfileid: "66841875"
---
# <a name="live-share-media-capabilities"></a>Live Share-Medienfunktionen

Video und Audio sind wichtige Bestandteile der modernen Welt und des Arbeitsplatzes. Wir haben umfassendes Feedback erhalten, dass wir mehr tun können, um die Qualität, die Barrierefreiheit und den Lizenzschutz beim gemeinsamen Ansehen von Videos in Besprechungen zu verbessern.

Das Live Share-SDK ermöglicht die **Mediensynchronisierung** in jedes HTML `<video>`- und `<audio>`-Element einfacher als je zuvor.  Durch die Mediensynchronisierung auf der Ebene des Playerstatus und der Transportsteuerelemente können Sie Ansichten und Lizenzen individuell zuweisen und gleichzeitig die bestmögliche Qualität bieten, die über Ihre Anwendung verfügbar ist.

## <a name="install"></a>Installieren

So fügen Sie ihrer Anwendung mithilfe von NPM die neueste Version des SDK hinzu:

```bash
npm install @microsoft/live-share --save
npm install @microsoft/live-share-media --save
```

ODER

So fügen Sie die neueste Version des SDK mit [Yarn](https://yarnpkg.com/) zu Ihrer Anwendung hinzu:

```bash
yarn add @microsoft/live-share
yarn add @microsoft/live-share-media
```

## <a name="media-sync-overview"></a>Übersicht über die Mediensynchronisierung

Das Live Share-SDK verfügt über zwei primäre Klassen, die sich auf die Mediensynchronisation beziehen:

| Klassen                                                                                                                  | Beschreibung                                                                                                              |
| ------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------ |
| [EphemeralMediaSession](/javascript/api/@microsoft/live-share-media/ephemeralmediasession)     | Benutzerdefiniertes kurzlebiges Objekt, das entwickelt wurde, um Medientransportsteuerelemente und den Wiedergabestatus in unabhängigen Medienstreams zu koordinieren. |
| [MediaPlayerSynchronizer](/javascript/api/@microsoft/live-share-media/mediaplayersynchronizer) | Synchronisiert ein lokales HTML-Medienelement mit einer Gruppe von entfernten HTML-Medienelementen für eine `EphemeralMediaSession`.|

Beispiel:

```html
<body>
  <video id="player">
    <source src="YOUR_VIDEO_SRC" type="video/mp4" />
  </video>
</body>
```

```javascript
import * as microsoftTeams from "@microsoft/teams-js";
import { TeamsFluidClient } from "@microsoft/live-share";
import { EphemeralMediaSession } from "@microsoft/live-share-media";

// Initialize the Teams Client SDK
await microsoftTeams.app.initialize();

// Setup the Fluid container
const client = new TeamsFluidClient();
const schema = {
  initialObjects: { mediaSession: EphemeralMediaSession },
};
const { container } = await client.joinContainer(schema);
const { mediaSession } = container.initialObjects;

// Get the player from your document and create synchronizer
const player = document.getElementById("player");
const synchronizer = mediaSession.synchronize(player);

// Define roles you want to allow playback control and start sync
const allowedRoles = ["Organizer", "Presenter"];
await mediaSession.start(allowedRoles);
```

Die `EphemeralMediaSession` lauscht automatisch auf Änderungen des Wiedergabestatus der Gruppe und wendet die Änderungen über den Befehl `MediaPlayerSynchronizer` an. Um Wiedergabestatusänderungen zu vermeiden, die ein Benutzer nicht absichtlich initiiert hat, z. B. ein Pufferereignis, müssen Transportsteuerelemente über den Synchronizer und nicht direkt über den Player aufgerufen werden.

Beispiel:

```html
<body>
  <video id="player">
    <source src="YOUR_VIDEO_SRC" type="video/mp4" />
  </video>
  <div class="player-controls">
    <button id="play-button">Play</button>
    <button id="pause-button">Pause</button>
    <button id="restart-button">Restart</button>
    <button id="change-track-button">Change track</button>
  </div>
</body>
```

```javascript
// ...

document.getElementById("play-button").onclick = () => {
  synchronizer.play();
};

document.getElementById("pause-button").onclick = () => {
  synchronizer.pause();
};

document.getElementById("restart-button").onclick = () => {
  synchronizer.seekTo(0);
};

document.getElementById("change-track-button").onclick = () => {
  synchronizer.setTrack({
    trackIdentifier: "SOME_OTHER_VIDEO_SRC",
  });
};
```

 > [!Note]
 > Sie können das `EphemeralMediaSession`-Objekt zwar zum direkten Synchronisieren von Medien mithilfe des `MediaPlayerSynchronizer` verwenden, wenn Sie allerdings eine feinere Steuerung der Synchronisierungslogik möchten, sollten Sie das vermeiden. Je nachdem, welchen Player Sie in Ihrer App verwenden, sollten Sie eventuell ein Delegat-Shim erstellen, damit die Oberfläche Ihres Webplayers mit der HTML-Medienoberfläche übereinstimmt.

## <a name="suspensions-and-wait-points"></a>Unterbrechungen und Wartepunkte

Wenn Sie die Synchronisierung für das `EphemeralMediaSession`-Objekt vorübergehend anhalten möchten, können Sie Unterbrechungen verwenden. Ein [MediaSessionCoordinatorSuspension](/javascript/api/@microsoft/live-share-media/ephemeralmediasessioncoordinatorsuspension)-Objekt ist standardmäßig lokal, was in Fällen hilfreich sein kann, in denen ein Benutzer etwas nachholen möchte, das er verpasst hat, eine Pause einlegen möchte usw. Wenn der Benutzer die Unterbrechung beendet, wird die Synchronisierung automatisch fortgesetzt.

```javascript
// Suspend the media session coordinator
const suspension = mediaSession.coordinator.beginSuspension();

// End the suspension when ready
suspension.end();
```

Wenn Sie eine Unterbrechung beginnen, können Sie auch einen optionalen [CoordinationWaitPoint](/javascript/api/@microsoft/live-share-media/coordinationwaitpoint)-Parameter einfügen, der es den Benutzern ermöglicht, die Zeitstempel zu definieren, in denen eine Unterbrechung für alle Benutzer erfolgen soll. Die Synchronisierung wird erst dann fortgesetzt, wenn alle Benutzer die Unterbrechung für diesen Wartepunkt beendet haben. Dies ist z. B. nützlich, um an bestimmten Stellen im Video ein Quiz oder eine Umfrage einzufügen.

```javascript
// Suspend the media session coordinator
const waitPoint = {
  position: 0,
  reason: "ReadyUp", // Optional.
};
const suspension = mediaSession.coordinator.beginSuspension();
// End the suspension when the user readies up
document.getElementById("ready-up-button").onclick = () => {
  // Sync will resume when everyone has ended suspension
  suspension.end();
};
```

## <a name="audio-ducking"></a>Audio-Ducking

Das Live Share-SDK unterstützt intelligentes Audio-Ducking. Sie können das _experimentelle_ Feature in Ihrer Anwendung verwenden und Folgendes zu Ihrem Code hinzuzufügen:

```javascript
import * as microsoftTeams from "@microsoft/teams-js";

// ...

let volumeTimer;
microsoftTeams.meeting.registerSpeakingStateChangeHandler((speakingState) => {
  if (speakingState.isSpeakingDetected && !volumeTimer) {
    volumeTimer = setInterval(() => {
      synchronizer.volumeLimiter?.lowerVolume();
    }, 250);
  } else if (volumeTimer) {
    clearInterval(volumeTimer);
    volumeTimer = undefined;
  }
});
```

Um Audio-Ducking zu aktivieren, fügen Sie Ihrem Anwendungsmanifest die folgenden [RSC](/microsoftteams/platform/graph-api/rsc/resource-specific-consent)-Berechtigungen hinzu:

```json
{
  // ...rest of your manifest here
  "authorization": {
    "permissions": {
      "resourceSpecific": [
        // ...other permissions here
        {
          "name": "OnlineMeetingIncomingAudio.Detect.Chat",
          "type": "Delegated"
        },
        {
          "name": "OnlineMeetingIncomingAudio.Detect.Group",
          "type": "Delegated"
        }
      ]
    }
  }
}
```

> [!Note]
> Die für das Audio-Ducking verwendete `registerSpeakingStateChangeHandler`-API funktioniert derzeit nur für nicht-lokale Benutzer, die sprechen.

## <a name="code-samples"></a>Codebeispiele

| Beispielname   | Beschreibung | JavaScript |
| -------------------- | ----------------------------| -----------------|
| React-Video          | Einfaches Beispiel, das zeigt, wie das EphemeralMediaSession-Objekt mit HTML5-Video funktioniert.                                                        | [View](https://aka.ms/liveshare-reactvideo)    |
| React-Medienvorlage | Ermöglichen Sie es allen angeschlossenen Clients, Videos gemeinsam anzusehen, eine gemeinsame Wiedergabeliste zu erstellen, zu übertragen, wer die Kontrolle hat und das Video mit Anmerkungen zu versehen. | [Anzeigen](https://aka.ms/liveshare-mediatemplate) |

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Agiles Poker-Tutorial](../sbs-teams-live-share.yml)

## <a name="see-also"></a>Siehe auch

* [Live Share SDK – FAQ](teams-live-share-faq.md)
* [Live Share SDK-Referenzdokumente](/javascript/api/@microsoft/live-share/)
* [Referenzdokumentation zum Live Share Media SDK](/javascript/api/@microsoft/live-share-media/)
* [Referenzdokumente](https://aka.ms/livesharedocs)
* [Teams-Apps in Besprechungen](teams-apps-in-meetings.md)
