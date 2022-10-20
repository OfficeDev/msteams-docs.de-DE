---
title: Erstellen von Apps für teams-Besprechungsphase
author: v-sdhakshina
description: Erfahren Sie, wie Sie Apps für die Teams-Besprechungsphase erstellen, apIs bereitstellen und einen Deep-Link generieren, um Inhalte für die Phase in Besprechungen freizugeben.
ms.topic: conceptual
ms.author: v-sdhakshina
ms.localizationpriority: medium
ms.date: 04/07/2022
ms.openlocfilehash: 440e48d370d18564f5bba869d95c63bc25b11e4e
ms.sourcegitcommit: 40d4bde10b6820c62e49e2400b10ab3569c8c815
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/20/2022
ms.locfileid: "68615436"
---
# <a name="build-apps-for-teams-meeting-stage"></a>Erstellen von Apps für teams-Besprechungsphase

Mit "In Phase freigeben" können Benutzer eine App über den Besprechungsbereich in einer laufenden Besprechung für die Besprechungsphase freigeben. Diese Freigabe ist interaktiv und zusammenarbeitend im Vergleich zur passiven Bildschirmfreigabe.

Um die Freigabe für die Phase aufzurufen, können Benutzer das Symbol " **In Phase freigeben** " oben rechts im Besprechungsbereich auswählen. Das Symbol "**In Phase teilen**" ist nativ für den Teams-Client, und wenn Sie auswählen, dass die gesamte App für die Besprechungsphase freigegeben wird.

## <a name="app-manifest-settings-for-apps-in-meeting-stage"></a>App-Manifesteinstellungen für Apps in der Besprechungsphase

Um eine App für die Besprechungsphase freizugeben, aktualisieren Sie die `context` Eigenschaft im App-Manifest wie folgt:

```json
"context":[ 
    "meetingSidePanel", 
    "meetingStage" 
     ] 
```

## <a name="advanced-share-to-stage-apis"></a>Erweiterte Freigabe für Phasen-APIs

Es gibt viele Szenarien, in denen das Teilen der gesamten App für die Besprechungsphase nicht so nützlich ist wie das Freigeben bestimmter Teile der App:  

1. Bei einer Brainstorming- oder Whiteboard-App möchte ein Benutzer möglicherweise ein bestimmtes Board in einer Besprechung im Vergleich zur gesamten App mit allen Boards teilen.  

1. Bei einer medizinischen App möchte ein Arzt möglicherweise nur die Röntgenaufnahme auf dem Bildschirm mit dem Patienten teilen, anstatt die gesamte App mit allen Patientendatensätzen oder -ergebnissen zu teilen usw.

1. Ein Benutzer möchte möglicherweise Inhalte von einem einzelnen Inhaltsanbieter gleichzeitig freigeben (z. B. YouTube), statt einen gesamten Videokatalog auf der Bühne freizugeben.

Um Benutzern in solchen Szenarien zu helfen, haben wir APIs im Teams Client SDK veröffentlicht, mit denen Sie die Freigabe für bestimmte Teile der App programmgesteuert über eine Schaltfläche im Besprechungsbereich aufrufen können.

:::image type="content" source="../assets/images/apps-in-meetings/shared-meeting-stage-edit-review-component.png" alt-text="Der Screenshot zeigt die Ansicht &quot;Für Besprechungsphase freigeben&quot;.":::

Verwenden Sie die folgenden APIs, um einen bestimmten Teil der App freizugeben:

|Methode| Beschreibung| Quelle|
|---|---|----|
|[**Teilen Sie App-Inhalte auf der Bühne**](#share-app-content-to-stage-api)| Teilen Sie bestimmte Teile der App über den Besprechungsseitenbereich in einer Besprechung für die Besprechungsphase. | [JavaScript-Bibliotheks-SDK für Microsoft Teams](/javascript/api/@microsoft/teams-js/meeting) |
|[**Rufen Sie den Freigabestatus für App-Inhalte ab**](#get-app-content-stage-sharing-state-api)| Rufen Sie Informationen über den Freigabestatus der App in der Besprechungsphase ab. | [JavaScript-Bibliotheks-SDK für Microsoft Teams](/javascript/api/@microsoft/teams-js/meeting.iappcontentstagesharingstate) |
|[**Holen Sie sich Funktionen zum Teilen von App-Inhalten**](#get-app-content-stage-sharing-capabilities-api)| Rufen Sie die Funktionen der App zum Teilen in der Besprechungsphase ab. | [JavaScript-Bibliotheks-SDK für Microsoft Teams](/javascript/api/@microsoft/teams-js/meeting.iappcontentstagesharingcapabilities) |

## <a name="share-app-content-to-stage-api"></a>Teilen Sie App-Inhalte mit der Staging-API

Die `shareAppContentToStage` API ermöglicht es Ihnen, bestimmte Teile Ihrer App für die Besprechungsbühne freizugeben. Die API ist über das Teams-Client-SDK verfügbar.

### <a name="prerequisite"></a>Voraussetzungen

* Um die `shareAppContentToStage` API zu verwenden, müssen Sie die RSC-Berechtigungen erhalten. Konfigurieren Sie im App-Manifest die `authorization` Eigenschaft `name` und `type` das und im `resourceSpecific` Feld. Beispiel:

    ```json
    "authorization": {
        "permissions": { 
        "resourceSpecific": [
        { 
         "name": "MeetingStage.Write.Chat",
         "type": "Delegated"
        }
        ]
    }
    }
    ```

* `appContentUrl` muss vom Array innerhalb von `validDomains` manifest.json zulässig sein, andernfalls gibt die API einen 501-Fehler zurück.

### <a name="query-parameter"></a>Abfrageparameter

Die folgende Tabelle enthält die Abfrageparameter:

|Wert|Typ|Erforderlich|Beschreibung|
|---|---|----|---|
|**callback**| Zeichenfolge | Ja | Callback enthält zwei Parameter, Fehler und Ergebnis. Der *Fehler* kann entweder einen Fehler vom Typ *SdkError* enthalten oder null sein, wenn die Freigabe erfolgreich ist. Das *Ergebnis* kann entweder einen echten Wert enthalten, wenn eine erfolgreiche Freigabe vorhanden ist, oder NULL, wenn die Freigabe fehlschlägt. |
|**appContentURL**| Zeichenfolge | Ja | Die URL, die auf der Bühne geteilt wird. |

### <a name="example"></a>Beispiel

```javascript
const appContentUrl = "https://www.bing.com/";

microsoftTeams.meeting.shareAppContentToStage((err, result) => {
    if (result) {
        // handle success
    }
    if (err) {
        // handle error
    }
}, appContentUrl);
```

### <a name="response-codes"></a>Antwortcodes

Die folgende Tabelle enthält die Antwortcodes:

|Antwortcode|Beschreibung|
|---|---|
| **500** | Interner Fehler. |
| **501** | DIE API wird im aktuellen Kontext nicht unterstützt.|
| **1000** | Die App verfügt nicht über die erforderlichen Berechtigungen, um die Freigabe für die Phase zuzulassen.|

## <a name="get-app-content-stage-sharing-state-api"></a>Rufen Sie die App-Content-Stage-Sharing-Status-API ab

Mithilfe `getAppContentStageSharingState` der API können Sie Informationen zur Freigabe von Apps in der Besprechungsphase abrufen.

### <a name="query-parameter"></a>Abfrageparameter

Die folgende Tabelle enthält den Abfrageparameter:

|Wert|Typ|Erforderlich|Beschreibung|
|---|---|----|---|
|**callback**| Zeichenfolge | Ja | Der Rückruf enthält zwei Parameter: Fehler und Ergebnis. Der *Fehler* kann entweder einen Fehler vom Typ *SdkError* im Fehlerfall oder null enthalten, wenn die Freigabe erfolgreich ist. Das *Ergebnis* kann entweder ein `IAppContentStageSharingState` Objekt enthalten, wenn die Freigabe erfolgreich ist, oder null im Falle eines Fehlers.|

### <a name="example"></a>Beispiel

```javascript
microsoftTeams.meeting.getAppContentStageSharingState((err, result) => {
    if (result.isAppSharing) {
        // Indicates if app is sharing content on the meeting stage.
    }
});
```

Der JSON-Antworttext für die `getAppContentStageSharingState` API lautet:

```json
{
   "isAppSharing":true
} 
```

### <a name="response-codes"></a>Antwortcodes

Die folgende Tabelle enthält die Antwortcodes:

|Antwortcode|Beschreibung|
|---|---|
| **500** | Interner Fehler. |
| **501** | DIE API wird im aktuellen Kontext nicht unterstützt.|
| **1000** | Die App verfügt nicht über die erforderlichen Berechtigungen, um die Freigabe für die Phase zuzulassen.|

## <a name="get-app-content-stage-sharing-capabilities-api"></a>Holen Sie sich die API für die Freigabe von App-Inhalten

Die `getAppContentStageSharingCapabilities` API ermöglicht es Ihnen, die Funktionen der App zum Teilen für die Besprechungsphase abzurufen.

### <a name="query-parameter"></a>Abfrageparameter

Die folgende Tabelle enthält den Abfrageparameter:

|Wert|Typ|Erforderlich|Beschreibung|
|---|---|----|---|
|**callback**| Zeichenfolge | Ja | Der Rückruf enthält zwei Parameter: Fehler und Ergebnis. Der *Fehler* kann entweder einen Fehler vom Typ *SdkError* enthalten oder null sein, wenn die Freigabe erfolgreich ist. Das Ergebnis kann entweder ein `IAppContentStageSharingCapabilities` Objekt enthalten, wenn die Freigabe erfolgreich ist, oder null im Falle eines Fehlers.|

### <a name="example"></a>Beispiel

```javascript
microsoftTeams.meeting.getAppContentStageSharingCapabilities((err, result) => {
    if (result.doesAppHaveSharePermission) {
        // Indicates app has permission to share contents to meeting stage.
    }
});
```

Der JSON-Antworttext für die `getAppContentStageSharingCapabilities` API lautet:

```json
{
   "doesAppHaveSharePermission":true
} 
```

### <a name="response-codes"></a>Antwortcodes

Die folgende Tabelle enthält die Antwortcodes:

|Antwortcode|Beschreibung|
|---|---|
| **500** | Interner Fehler. |
| **501** | DIE API wird im aktuellen Kontext nicht unterstützt.|
| **1000** | Die App verfügt nicht über Berechtigungen, um die Freigabe für die Phase zuzulassen.|

## <a name="generate-a-deep-link-to-share-content-to-stage-in-meetings"></a>Generieren eines Deep-Links zum Freigeben von Inhalten für die Phase in Besprechungen

Sie können auch einen Deep-Link generieren, um die App für das Bereitstellen und Starten oder Teilnehmen an einer Besprechung freizugeben.

> [!NOTE]
>
> * Derzeit wird der Deep-Link zum Freigeben von Inhalten für die Phase in Besprechungen verbessert und ist nur in [der öffentlichen Entwicklervorschau](~/resources/dev-preview/developer-preview-intro.md) verfügbar.
> * Deep-Link zum Freigeben von Inhalten in der Phase der Besprechung wird nur im Teams-Desktopclient unterstützt.

Wenn in einer App ein Deep-Link von einem Benutzer ausgewählt wird, der Teil einer laufenden Besprechung ist, wird die App für die Phase freigegeben, und ein Popupfenster für Berechtigungen wird angezeigt. Benutzer können den Teilnehmern Zugriff auf die Zusammenarbeit mit einer App gewähren.

:::image type="content" source="../assets/images/intergrate-with-teams/screenshot-of-pop-up-permission.png" alt-text="Der Screenshot ist ein Beispiel für ein Popupfenster mit Berechtigungen.":::

Wenn sich ein Benutzer nicht in einer Besprechung befindet, wird der Benutzer zum Teams-Kalender umgeleitet, in dem er an einer Besprechung teilnehmen oder eine sofort Besprechung initiieren kann (jetzt besprechen).

:::image type="content" source="../assets/images/intergrate-with-teams/Instant-meetnow-pop-up.png" alt-text="Der Screenshot ist ein Beispiel für ein Popupfenster, wenn keine Besprechung ausgeführt wird.":::

Sobald der Benutzer eine Sofortbesprechung initiiert (jetzt besprechen), kann er Teilnehmer hinzufügen und mit der App interagieren.

:::image type="content" source="../assets/images/intergrate-with-teams/Screenshot-ofmeet-now-option-pop-up.png" alt-text="Der Screenshot ist ein Beispiel, das eine Option zum Hinzufügen von Teilnehmern und die Interaktion mit der App zeigt.":::

Um einen Deep-Link hinzuzufügen, um Inhalte auf der Bühne freizugeben, benötigen Sie einen App-Kontext. Der App-Kontext ermöglicht es dem Teams-Client, das App-Manifest abzurufen und zu überprüfen, ob die Freigabe in der Phase möglich ist. Es folgt ein Beispiel für einen App-Kontext.

`{ "appSharingUrl" : "https://teams.microsoft.com/extensibility-apps/meetingapis/view", "appId": "9ec80a73-1d41-4bcb-8190-4b9eA9e29fbb" , "useMeetNow": false }`

Die Abfrageparameter für den App-Kontext lauten:

* `appID`: Dies ist die ID, die aus dem App-Manifest abgerufen werden kann.
* `appSharingUrl`: Die URL, die in der Phase freigegeben werden muss, sollte eine gültige Domäne sein, die im App-Manifest definiert ist. Wenn die URL keine gültige Domäne ist, wird ein Fehlerdialogfeld angezeigt, um dem Benutzer eine Beschreibung des Fehlers bereitzustellen.
* `useMeetNow`: Dazu gehört ein boolescher Parameter, der entweder "true" oder "false" sein kann.
  * **True**: Wenn der `UseMeetNow` Wert wahr ist und keine laufende Besprechung vorhanden ist, wird eine neue Besprechung "Jetzt besprechen" initiiert. Wenn eine Besprechung läuft, wird dieser Wert ignoriert.

  * **False**: Der Standardwert ist `UseMeetNow` "false", d. h., wenn ein Deep-Link für die Phase freigegeben wird und keine Besprechung ausgeführt wird, wird ein Kalender-Popup angezeigt. Sie können die Freigabe jedoch direkt während einer Besprechung ausführen.

Stellen Sie sicher, dass alle Abfrageparameter ordnungsgemäß URI-codiert sind und der App-Kontext zweimal in der endgültigen URL codiert werden muss. Es folgt ein Beispiel.

```json
var appContext= JSON.stringify({ "appSharingUrl" : "https://teams.microsoft.com/extensibility-apps/meetingapis/view", "appId": "9cc80a93-1d41-4bcb-8170-4b9ec9e29fbb", "useMeetNow":false })
var encodedContext = encodeURIComponent(appcontext).replace(/'/g,"%27").replace(/"/g,"%22")
var encodedAppContext = encodeURIComponent(encodedContext).replace(/'/g,"%27").replace(/"/g,"%22")
```

Ein Deep-Link kann entweder über das Teams-Web oder über den Teams-Desktopclient gestartet werden.

* **Teams-Web**: Verwenden Sie das folgende Format, um einen Deep-Link aus dem Teams-Web zu starten, um Inhalte auf der Bühne freizugeben.

    `https://teams.microsoft.com/l/meeting-share?deeplinkId={deeplinkid}&fqdn={fqdn}}&lm=deeplink%22&appContext={encoded app context}`

    Beispiel: `https://teams.microsoft.com/l/meeting-share?deeplinkId={sampleid}&fqdn=teams.microsoft.com&lm=deeplink%22&appContext=%257B%2522appSharingUrl%2522%253A%2522https%253A%252F%252Fteams.microsoft.com%252Fextensibility-apps%252Fmeetingapis%252Fview%2522%252C%2522appId%2522%253A%25229cc80a93-1d41-4bcb-8170-4b9ec9e29fbb%2522%252C%2522useMeetNow%2522%253Atrue%257D`

    |Deep-Link|Format|Beispiel|
    |---------|---------|---------|
    |Wenn Sie die App freigeben und den Teams-Kalender öffnen möchten, ist UseMeeetNow **standardmäßig "false**".|`https://teams.microsoft.com/l/meeting-share?deeplinkId={deeplinkid}&fqdn={fqdn}}&lm=deeplink%22&appContext={encoded app context}`|`https://teams.microsoft.com/l/meeting-share?deeplinkId={sampleid}&fqdn=teams.microsoft.com&lm=deeplink%22&appContext=%257B%2522appSharingUrl%2522%253A%2522https%253A%252F%252Fteams.microsoft.com%252Fextensibility-apps%252Fmeetingapis%252Fview%2522%252C%2522appId%2522%253A%25229cc80a93-1d41-4bcb-8170-4b9ec9e29fbb%2522%252C%2522useMeetNow%2522%253Afalse%257D`|
    |Um die App freizugeben und eine sofortige Besprechung zu initiieren, wenn UseMeeetNow **wahr** ist.|`https://teams.microsoft.com/l/meeting-share?deeplinkId={deeplinkid}&fqdn={fqdn}}&lm=deeplink%22&appContext={encoded app context}`|`https://teams.microsoft.com/l/meeting-share?deeplinkId={sampleid}&fqdn=teams.microsoft.com&lm=deeplink%22&appContext=%257B%2522appSharingUrl%2522%253A%2522https%253A%252F%252Fteams.microsoft.com%252Fextensibility-apps%252Fmeetingapis%252Fview%2522%252C%2522appId%2522%253A%25229cc80a93-1d41-4bcb-8170-4b9ec9e29fbb%2522%252C%2522useMeetNow%2522%253Atrue%257D`|

* **Teamdesktopclient**: Verwenden Sie das folgende Format, um einen Deep-Link vom Teams-Desktopclient aus zu starten, um Inhalte auf der Bühne freizugeben.

    `msteams:/l/meeting-share?   deeplinkId={deeplinkid}&fqdn={fqdn}&lm=deeplink%22&appContext={encoded app context}`

    Beispiel: `msteams:/l/meeting-share?deeplinkId={sampleid}&fqdn=teams.microsoft.com&lm=deeplink%22&appContext=%257B%2522appSharingUrl%2522%253A%2522https%253A%252F%252Fteams.microsoft.com%252Fextensibility-apps%252Fmeetingapis%252Fview%2522%252C%2522appId%2522%253A%25229cc80a93-1d41-4bcb-8170-4b9ec9e29fbb%2522%252C%2522useMeetNow%2522%253Atrue%257D`

    |Deep-Link|Format|Beispiel|
    |---------|---------|---------|
    |Wenn Sie die App freigeben und den Teams-Kalender öffnen möchten, ist UseMeeetNow **standardmäßig "false**".|`msteams:/l/meeting-share?   deeplinkId={deeplinkid}&fqdn={fqdn}&lm=deeplink%22&appContext={encoded app context}`|`msteams:/l/meeting-share?deeplinkId={sampleid}&fqdn=teams.microsoft.com&lm=deeplink%22&appContext=%257B%2522appSharingUrl%2522%253A%2522https%253A%252F%252Fteams.microsoft.com%252Fextensibility-apps%252Fmeetingapis%252Fview%2522%252C%2522appId%2522%253A%25229cc80a93-1d41-4bcb-8170-4b9ec9e29fbb%2522%252C%2522useMeetNow%2522%253Afalse%257D`|
    |Um die App freizugeben und eine sofortige Besprechung zu initiieren, wenn UseMeeetNow **wahr** ist.|`msteams:/l/meeting-share?   deeplinkId={deeplinkid}&fqdn={fqdn}&lm=deeplink%22&appContext={encoded app context}`|`msteams:/l/meeting-share?deeplinkId={sampleid}&fqdn=teams.microsoft.com&lm=deeplink%22&appContext=%257B%2522appSharingUrl%2522%253A%2522https%253A%252F%252Fteams.microsoft.com%252Fextensibility-apps%252Fmeetingapis%252Fview%2522%252C%2522appId%2522%253A%25229cc80a93-1d41-4bcb-8170-4b9ec9e29fbb%2522%252C%2522useMeetNow%2522%253Atrue%257D`|

Die Abfrageparameter sind:

* `deepLinkId`: Jeder Bezeichner, der für die Telemetriekorrelation verwendet wird.
* `fqdn`: `fqdn` ist ein optionaler Parameter, der verwendet werden kann, um zu einer geeigneten Umgebung einer Besprechung zu wechseln, um eine App auf der Bühne freizugeben. Es unterstützt Szenarien, in denen eine bestimmte App-Freigabe in einer bestimmten Umgebung erfolgt. Der Standardwert ist die `fqdn` Unternehmens-URL, und die möglichen Werte gelten `Teams.live.com` für Teams for Life `teams.microsoft.com`oder `teams.microsoft.us`.

Um die gesamte App für die Phase freizugeben, müssen Sie im App-Manifest konfigurieren `meetingStage` und `meetingSidePanel` als Framekontexte das [App-Manifest anzeigen](../resources/schema/manifest-schema.md). Andernfalls können Besprechungsteilnehmer den Inhalt möglicherweise nicht auf der Bühne sehen.

> [!NOTE]
> Damit Ihre App die Überprüfung besteht, verwenden Sie beim Erstellen eines Deep-Links von Ihrer Website, Web-App oder adaptiven Karte " **In Besprechung freigeben** " als Zeichenfolge oder Kopie.

## <a name="code-sample"></a>Codebeispiel

|Beispielname | Beschreibung | C# | Node.js |
|----------------|-----------------|--------------|----------------|
|Beispiel für Freigabefenster | Beispiel-App zum Anzeigen einer Registerkarte im Freigabefenster für die Zusammenarbeit | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-stage-view/csharp) | [Anzeigen](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-stage-view/nodejs) |
| Besprechungsinterne Benachrichtigung | Veranschaulicht die Implementierung von Benachrichtigungen in Besprechungen mithilfe eines Bots. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-content-bubble/csharp) | [Anzeigen](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-content-bubble/nodejs) |
| Dokumentsignierung in der Besprechung | Veranschaulicht die Implementierung einer Teams-App zum Signieren von Dokumenten. Umfasst die Freigabe bestimmter App-Inhalte für die Stufe, teams-SSO und benutzerspezifische Phasenansicht. | [Anzeigen](https://github.com/officedev/microsoft-teams-samples/tree/main/samples/meetings-share-to-stage-signing/csharp) | – |

## <a name="see-also"></a>Siehe auch

* [Teams-Authentifizierungsablauf für Registerkarten](../tabs/how-to/authentication/auth-flow-tab.md)
* [Apps für Teams-Besprechungen](teams-apps-in-meetings.md)
* [Erstellen von Registerkarten für Besprechungen](build-tabs-for-meeting.md)
* [Erstellen erweiterbarer Unterhaltungen für Besprechungschats](build-extensible-conversation-for-meeting-chat.md)
* [Erstellen von Apps für anonyme Benutzer](build-apps-for-anonymous-user.md)
* [Erweiterte Besprechungs-APIs](meeting-apps-apis.md)
* [Benutzerdefinierte Zusammen-Modus-Szenen](~/apps-in-teams-meetings/teams-together-mode.md)
* [Live Share SDK](teams-live-share-overview.md)
