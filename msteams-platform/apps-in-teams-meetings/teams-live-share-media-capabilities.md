---
title: Live Share-Medienfunktionen
author: surbhigupta
description: In diesem Modul erfahren Sie mehr über die Medienfunktionen von Live Share, Unterbrechungen und Wartepunkte, Audio-Ducking und das Synchronisieren von Video und Audio.
ms.topic: conceptual
ms.localizationpriority: high
ms.author: v-ypalikila
ms.date: 04/07/2022
ms.openlocfilehash: 0a1b7a48ffaf0cd71fd0aac2ecf7c1fe2c5970f1
ms.sourcegitcommit: 1248901a5e59db67bae091f60710aabe7562016a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/13/2022
ms.locfileid: "68560589"
---
# <a name="live-share-media-capabilities"></a>Live Share-Medienfunktionen

:::image type="content" source="../assets/images/teams-live-share/live-share-media-capabilities-docs-feature-1.png" alt-text="Teams Live Share-Mediensynchronisierung":::

Video und Audio sind wichtige Bestandteile der modernen Welt und des Arbeitsplatzes. Wir haben breit gefächertes Feedback gehört, dass wir noch mehr tun können, um die Qualität, Barrierefreiheit und den Lizenzschutz beim gemeinsamen Ansehen von Videos in Besprechungen zu erhöhen.

Das Live Share SDK ermöglicht eine stabile **Mediensynchronisierung** für jeden HTML-Code `<video>` und `<audio>` jedes Element mit nur wenigen Codezeilen. Durch die Mediensynchronisierung auf der Ebene des Playerstatus und der Transportsteuerelemente können Sie Ansichten und Lizenzen individuell zuweisen und gleichzeitig die bestmögliche Qualität bieten, die über Ihre Anwendung verfügbar ist.

## <a name="install"></a>Installieren

So fügen Sie ihrer Anwendung mithilfe von NPM die neueste Version des SDK hinzu:

```bash
npm install @microsoft/live-share@next --save
npm install @microsoft/live-share-media@next --save
```

ODER

So fügen Sie die neueste Version des SDK mit [Yarn](https://yarnpkg.com/) zu Ihrer Anwendung hinzu:

```bash
yarn add @microsoft/live-share@next
yarn add @microsoft/live-share-media@next
```

## <a name="media-sync-overview"></a>Übersicht über die Mediensynchronisierung

Das Live Share-SDK verfügt über zwei primäre Klassen, die sich auf die Mediensynchronisation beziehen:

| Klassen                                                                                        | Beschreibung                                                                                                                                       |
| ---------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------- |
| [LiveMediaSession](/javascript/api/@microsoft/live-share-media/livemediasession)     | Benutzerdefiniertes Liveobjekt zum Koordinieren von Medientransportsteuerelementen und Wiedergabestatus in unabhängigen Medienstreams.                          |
| [MediaPlayerSynchronizer](/javascript/api/@microsoft/live-share-media/mediaplayersynchronizer) | Synchronisiert alle Objekte, die die `IMediaPlayer` Schnittstelle implementieren , einschließlich HTML5 `<video>` und `<audio>` -- mithilfe `LiveMediaSession`von . |

Beispiel:

```html
<body>
  <video id="player">
    <source src="YOUR_VIDEO_SRC" type="video/mp4" />
  </video>
</body>
```

# <a name="javascript"></a>[JavaScript](#tab/javascript)

```javascript
import { LiveShareClient, UserMeetingRole } from "@microsoft/live-share";
import { LiveMediaSession } from "@microsoft/live-share-media";

// Setup the Fluid container
const liveShare = new LiveShareClient();
const schema = {
  initialObjects: { mediaSession: LiveMediaSession },
};
const { container } = await liveShare.joinContainer(schema);
const { mediaSession } = container.initialObjects;

// Get the player from your document and create synchronizer
const player = document.getElementById("player");
const synchronizer = mediaSession.synchronize(player);

// Define roles you want to allow playback control and start sync
const allowedRoles = [UserMeetingRole.organizer, UserMeetingRole.presenter];
await mediaSession.initialize(allowedRoles);
```

# <a name="typescript"></a>[TypeScript](#tab/typescript)

```TypeScript
import { LiveShareClient, UserMeetingRole } from "@microsoft/live-share";
import { LiveMediaSession, IMediaPlayer, MediaPlayerSynchronizer } from "@microsoft/live-share-media";
import { ContainerSchema } from "fluid-framework";

// Join the Fluid container
const liveShare = new LiveShareClient();
const schema: ContainerSchema = {
  initialObjects: { mediaSession: LiveMediaSession },
};
const { container } = await liveShare.joinContainer(schema);
const mediaSession = container.initialObjects.mediaSession as LiveMediaSession;

// Get the player from your document and create synchronizer
const player: IMediaPlayer = document.getElementById("player") as HTMLVideoElement;
const synchronizer: MediaPlayerSynchronizer = mediaSession.synchronize(player);

// Define roles you want to allow playback control and start sync
const allowedRoles: UserMeetingRole[] = [UserMeetingRole.organizer, UserMeetingRole.presenter];
await mediaSession.initialize(allowedRoles);
```

---

Die `LiveMediaSession` App lauscht automatisch auf Änderungen am Wiedergabezustand der Gruppe. `MediaPlayerSynchronizer` überwacht zustandsänderungen, die von `LiveMediaSession` ausgegeben werden, und wendet sie auf das bereitgestellte `IMediaPlayer` Objekt an, z. B. ein HTML5 `<video>` oder `<audio>` Element. Um Wiedergabestatusänderungen zu vermeiden, die ein Benutzer nicht absichtlich initiiert hat, z. B. ein Pufferereignis, müssen Transportsteuerelemente über den Synchronizer und nicht direkt über den Player aufgerufen werden.

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

> [!NOTE]
> Sie können das `LiveMediaSession` Objekt zwar zum manuellen Synchronisieren von Medien verwenden, es wird jedoch im Allgemeinen empfohlen, das `MediaPlayerSynchronizer`Objekt zu verwenden. Abhängig vom Player, den Sie in Ihrer App verwenden, müssen Sie möglicherweise einen Stellvertretungsshim erstellen, damit die Schnittstelle Ihres Webplayers der [IMediaPlayer-Schnittstelle](/javascript/api/@microsoft/live-share-media/imediaplayer) entspricht.

## <a name="suspensions-and-wait-points"></a>Unterbrechungen und Wartepunkte

:::image type="content" source="../assets/images/teams-live-share/live-share-media-out-of-sync.png" alt-text="Screenshot, der eine Ansetzungssynchronisierung mit dem Referenten zeigt.":::

Wenn Sie die Synchronisierung für das `LiveMediaSession`-Objekt vorübergehend anhalten möchten, können Sie Unterbrechungen verwenden. Ein [MediaSessionCoordinatorSuspension](/javascript/api/@microsoft/live-share-media/livemediasessioncoordinatorsuspension)-Objekt ist standardmäßig lokal, was in Fällen hilfreich sein kann, in denen ein Benutzer etwas nachholen möchte, das er verpasst hat, eine Pause einlegen möchte usw. Wenn der Benutzer die Unterbrechung beendet, wird die Synchronisierung automatisch fortgesetzt.

# <a name="javascript"></a>[JavaScript](#tab/javascript)

```javascript
// Suspend the media session coordinator
const suspension = mediaSession.coordinator.beginSuspension();

// End the suspension when ready
suspension.end();
```

# <a name="typescript"></a>[TypeScript](#tab/typescript)

```TypeScript
import { MediaSessionCoordinatorSuspension } from "@microsoft/live-share-media";

// Suspend the media session coordinator
const suspension: MediaSessionCoordinatorSuspension = mediaSession.coordinator.beginSuspension();

// End the suspension when ready
suspension.end();
```

---

Wenn Sie eine Unterbrechung beginnen, können Sie auch einen optionalen [CoordinationWaitPoint](/javascript/api/@microsoft/live-share-media/coordinationwaitpoint)-Parameter einfügen, der es den Benutzern ermöglicht, die Zeitstempel zu definieren, in denen eine Unterbrechung für alle Benutzer erfolgen soll. Die Synchronisierung wird erst dann fortgesetzt, wenn alle Benutzer die Unterbrechung für diesen Wartepunkt beendet haben.

Hier sind einige Szenarien, in denen Wartepunkte besonders hilfreich sind:

- Hinzufügen eines Quiz oder einer Umfrage an bestimmten Punkten im Video.
- Warten, bis jeder ein Video entsprechend laden kann, bevor es gestartet wird oder während des Pufferns.
- Zulassen, dass ein Referent Punkte im Video für gruppendiskutieren wählt.

# <a name="javascript"></a>[JavaScript](#tab/javascript)

```javascript
// Suspend the media session coordinator
const waitPoint = {
  position: 0,
  reason: "ReadyUp", // Optional.
};
const suspension = mediaSession.coordinator.beginSuspension(waitPoint);
// End the suspension when the user readies up
document.getElementById("ready-up-button").onclick = () => {
  // Sync will resume when everyone has ended suspension
  suspension.end();
};
```

# <a name="typescript"></a>[TypeScript](#tab/typescript)

```TypeScript
import { MediaSessionCoordinatorSuspension, CoordinationWaitPoint } from "@microsoft/live-share-media";

// Suspend the media session coordinator
const waitPoint: CoordinationWaitPoint = {
  position: 0,
  reason: "ReadyUp", // Optional.
};
const suspension = mediaSession.coordinator.beginSuspension(waitPoint);

// End the suspension when the user readies up
document.getElementById("ready-up-button")!.onclick = () => {
  // Sync will resume when everyone has ended suspension
  suspension.end();
};
```

---

## <a name="audio-ducking"></a>Audio-Ducking

Das Live Share-SDK unterstützt intelligentes Audio-Ducking. Sie können das Feature in Ihrer Anwendung verwenden, indem Sie Folgendes zu Ihrem Code hinzufügen:

# <a name="javascript"></a>[JavaScript](#tab/javascript)

```javascript
import { meeting } from "@microsoft/teams-js";

// ... set up MediaPlayerSynchronizer

// Register speaking state change handler through Teams Client SDK
let volumeTimer;
meeting.registerSpeakingStateChangeHandler((speakingState) => {
  if (speakingState.isSpeakingDetected && !volumeTimer) {
    // If someone in the meeting starts speaking, periodically
    // lower the volume using your MediaPlayerSynchronizer's
    // VolumeLimiter.
    synchronizer.volumeLimiter?.lowerVolume();
    volumeTimer = setInterval(() => {
      synchronizer.volumeLimiter?.lowerVolume();
    }, 250);
  } else if (volumeTimer) {
    // If everyone in the meeting stops speaking and the
    // interval timer is active, clear the interval.
    clearInterval(volumeTimer);
    volumeTimer = undefined;
  }
});
```

# <a name="typescript"></a>[TypeScript](#tab/typescript)

```TypeScript
import { meeting } from "@microsoft/teams-js";

// ... set up MediaPlayerSynchronizer

// Register speaking state change handler through Teams Client SDK
let volumeTimer: NodeJS.Timeout | undefined;
meeting.registerSpeakingStateChangeHandler((speakingState: meeting.ISpeakingState) => {
  if (speakingState.isSpeakingDetected && !volumeTimer) {
    // If someone in the meeting starts speaking, periodically
    // lower the volume using your MediaPlayerSynchronizer's
    // VolumeLimiter.
    synchronizer.volumeLimiter?.lowerVolume();
    volumeTimer = setInterval(() => {
      synchronizer.volumeLimiter?.lowerVolume();
    }, 250);
  } else if (volumeTimer) {
    // If everyone in the meeting stops speaking and the
    // interval timer is active, clear the interval.
    clearInterval(volumeTimer);
    volumeTimer = undefined;
  }
});
```

---

Fügen Sie ihrem App-Manifest außerdem die folgenden [RSC-Berechtigungen](/microsoftteams/platform/graph-api/rsc/resource-specific-consent) hinzu:

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

> [!NOTE]
> Die `registerSpeakingStateChangeHandler` für Audio-Ducking verwendete API funktioniert derzeit nur auf dem Microsoft Teams-Desktop und in geplanten Besprechungstypen und Besprechungsterminen.

## <a name="code-samples"></a>Codebeispiele

| Beispielname          | Beschreibung                                                                                                                               | JavaScript                                     |
| -------------------- | ----------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------- |
| React-Video          | Einfaches Beispiel, das zeigt, wie das LiveMediaSession-Objekt mit HTML5-Video funktioniert.                                                        | [View](https://aka.ms/liveshare-reactvideo)    |
| React-Medienvorlage | Ermöglichen Sie es allen angeschlossenen Clients, Videos gemeinsam anzusehen, eine gemeinsame Wiedergabeliste zu erstellen, zu übertragen, wer die Kontrolle hat und das Video mit Anmerkungen zu versehen. | [Anzeigen](https://aka.ms/liveshare-mediatemplate) |

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Live-Freigabe-Canvas](teams-live-share-canvas.md)

## <a name="see-also"></a>Siehe auch

- [Live Share SDK – FAQ](teams-live-share-faq.md)
- [Live Share SDK-Referenzdokumente](/javascript/api/@microsoft/live-share/)
- [Referenzdokumentation zum Live Share Media SDK](/javascript/api/@microsoft/live-share-media/)
- [Teams-Apps in Besprechungen](teams-apps-in-meetings.md)
