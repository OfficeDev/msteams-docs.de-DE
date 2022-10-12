---
title: Aktivieren und Konfigurieren Ihrer Apps für Teams-Besprechungen
author: surbhigupta
description: Erfahren Sie, wie Sie Ihre Apps für Teams-Besprechungen und verschiedene Besprechungsszenarien aktivieren und konfigurieren, das App-Manifest aktualisieren, Features konfigurieren und vieles mehr.
ms.topic: conceptual
ms.author: surbhigupta
ms.localizationpriority: high
ms.date: 04/07/2022
ms.openlocfilehash: b551513d61e7bb9ab2b9c118f756b3ce5232dde4
ms.sourcegitcommit: 20070f1708422d800d7b1d84b85cbce264616ead
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2022
ms.locfileid: "68537584"
---
# <a name="enable-and-configure-apps-for-meetings"></a>Aktivieren und Konfigurieren von Apps für Besprechungen

Jedes Team hat eine andere Art, zu kommunizieren und Aufgaben gemeinsam zu erledigen. Um diese verschiedenen Aufgaben zu erfüllen, passen Sie Teams mit Apps für Besprechungen an. Aktivieren Sie Ihre Apps für Teams-Besprechungen, und konfigurieren Sie die Apps so, dass sie im Besprechungsbereich innerhalb ihres App-Manifests verfügbar sind.

## <a name="prerequisites"></a>Voraussetzungen

Mit Apps für Teams-Besprechungen können Sie die Funktionen Ihrer Apps über den gesamten Besprechungslebenszyklus erweitern. Bevor Sie mit Apps für Teams-Besprechungen arbeiten, müssen Sie die folgenden Voraussetzungen erfüllen:

* Erfahren Sie, wie Sie Teams-Apps entwickeln. Weitere Informationen zum Entwickeln von Teams-Apps finden Sie unter [Teams-App-Entwicklung](../overview.md).

* Verwenden Sie Ihre App, die konfigurierbare Registerkarten im Gruppenchat- und/oder Teambereich unterstützt. Weitere Informationen finden Sie unter ["Bereiche"](../resources/schema/manifest-schema.md#configurabletabs) , und [erstellen Sie Ihre erste Registerkarten-App](../build-your-first-app/build-channel-tab.md).

* Halten Sie sich an die allgemeinen [Entwurfsrichtlinien für Teams-Registerkarten](../tabs/design/tabs.md) für Szenarien vor und nach der Besprechung. Informationen über Erfahrungen während Besprechungen finden Sie in den Entwurfsrichtlinien für [besprechungsinterne Registerkarten](../apps-in-teams-meetings/design/designing-apps-in-meetings.md#use-an-in-meeting-tab) und [besprechungsinternes Design](../apps-in-teams-meetings/design/designing-apps-in-meetings.md#use-an-in-meeting-dialog).

* Damit Ihre App in Echtzeit aktualisiert werden kann, muss sie basierend auf den Ereignisaktivitäten in der Besprechung auf dem neuesten Stand sein. Diese Ereignisse können sich innerhalb des besprechungsinternen Dialogfelds und in anderen Phasen des Besprechungslebenszyklus befinden. Informationen zum besprechungsinternen Dialogfeld finden Sie unter dem `completionBotId`-Parameter in [besprechungsinterne Benachrichtigungsnutzdaten](API-references.md#send-an-in-meeting-notification).

## <a name="enable-your-app-for-teams-meetings"></a>Aktivieren Ihrer App für Teams-Besprechungen

Um Ihre App für Teams-Besprechungen zu aktivieren, aktualisieren Sie Ihr App-Manifest, und verwenden Sie die Kontexteigenschaften, um zu bestimmen, wo Ihre App angezeigt werden muss.

### <a name="update-your-app-manifest"></a>Aktualisieren Ihres App-Manifests

Die Funktionen der Besprechungs-App werden in Ihrem App-Manifest mithilfe der Arrays `configurableTabs`, `scopes` und `context` deklariert. Der Bereich definiert, wer zugreifen kann, und der Kontext definiert, wo Ihre App verfügbar ist.

> [!NOTE]
>
> * Apps in Besprechungen erfordern `groupchat` oder `team` bereichsbezogene. Der `team` Bereich funktioniert für Registerkarten in Kanälen oder Kanalbesprechungen.
> * Um das Hinzufügen von Registerkarten in geplanten Kanalbesprechungen zu unterstützen, geben Sie den **Teambereich** im **Bereichsabschnitt** in Ihrem App-Manifest an. Ohne **Teambereich** würde die App nicht im Flyout für Kanalbesprechungen angezeigt.
> * Apps in Besprechungen können die folgenden Kontexte verwenden: `meetingChatTab`, `meetingDetailsTab`, `meetingSidePanel` und `meetingStage`.
> * Die delegierten RSC-Berechtigungen `MeetingStage.Write.Chat` und `ChannelMeetingStage.Write.Group` sind im Manifest erforderlich, um die Freigabe der Besprechungsphase zu aktivieren.

Der folgende Codeausschnitt ist ein Beispiel für eine konfigurierbare Registerkarte, die in einer App für Teams Besprechungen verwendet wird:

```json

"configurableTabs": [
    {
      "configurationUrl": "https://contoso.com/teamstab/configure",
      "canUpdateConfiguration": true,
      "scopes": [
        "team",
        "groupchat"
      ],
      "context":[
        "channelTab",
        "privateChatTab",
        "meetingChatTab",
        "meetingDetailsTab",
        "meetingSidePanel",
        "meetingStage"
     ]
    }
  ]
```

### <a name="context-property"></a>Context-Eigenschaft

Die `context`-Eigenschaft der Registerkarte bestimmt, was angezeigt werden muss, wenn ein Benutzer eine App in einer Besprechung aufruft, je nachdem, wo er die App aufruft. Mithilfe der Eigenschaften `context` und `scopes` der Registerkarte können Sie bestimmen, wo Ihre App angezeigt werden muss. Die Registerkarten im Bereich `team` oder `groupchat` können mehr als einen Kontext aufweisen.

Unterstützen Sie den Bereich `groupchat`, um Ihre App in Chats vor und nach der Besprechung zu aktivieren. Mit der App-Erfahrung vor der Besprechung können Sie Besprechungs-Apps suchen und hinzufügen und die Aufgaben vor der Besprechung ausführen. Mit der App-Erfahrung nach der Besprechung können Sie die Ergebnisse der Besprechung anzeigen, z. B. Umfrageergebnisse oder Gebühren.

 Im Folgenden finden Sie die Werte für die Eigenschaft `context`, aus der Sie alle oder einige der Werte verwenden können:

|Wert|Beschreibung|
|---|---|
| **channelTab** | Eine Registerkarte in der Kopfzeile eines Teamkanals. |
| **privateChatTab** | Eine Registerkarte in der Kopfzeile eines Gruppenchats zwischen einer Gruppe von Benutzern, nicht im Kontext eines Teams oder einer Besprechung. |
| **meetingChatTab** | Eine Registerkarte in der Kopfzeile eines Gruppenchats zwischen einer Gruppe von Benutzern für eine geplante Besprechung. Sie können entweder **meetingChatTab** oder **meetingDetailsTab** angeben, um sicherzustellen, dass die Apps auf Mobilgeräten funktionieren. |
| **meetingDetailsTab** | Eine Registerkarte in der Kopfzeile der Ansicht der Besprechungsdetails des Kalenders. Sie können entweder **meetingChatTab** oder **meetingDetailsTab** angeben, um sicherzustellen, dass die Apps auf Mobilgeräten funktionieren. |
| **meetingSidePanel** | Ein besprechungsinterner Bereich, der über die einheitliche Leiste (U-Leiste) geöffnet wird. |
| **meetingStage** | Eine App aus dem `meetingSidePanel` kann im Freigabefenster angezeigt werden. Sie können diese App weder auf mobilen noch auf Microsoft Teams-Raum-Clients verwenden. |

Nachdem Sie Ihre App für Teams-Besprechungen aktiviert haben, müssen Sie Ihre App vor einer Besprechung, während einer Besprechung und nach einer Besprechung konfigurieren.

## <a name="configure-your-app-for-meeting-scenarios"></a>Konfigurieren Ihrer App für Besprechungsszenarien

Teams-Besprechungen bieten eine gemeinschaftliche Erfahrung für Ihre Organisation. Konfigurieren Sie Ihre App für verschiedene Besprechungsszenarien, um die Besprechungserfahrung zu verbessern. Nun können Sie ermitteln, welche Aktionen in den folgenden Besprechungsszenarien ausgeführt werden können:

* [Vor einer Besprechung](#before-a-meeting)
* [Während einer Besprechung](#during-a-meeting)
* [Nach einer Besprechung](#after-a-meeting)

### <a name="before-a-meeting"></a>Vor einer Besprechung

Vor einer Besprechung können Benutzer Registerkarten, Bots und Nachrichtenerweiterungen hinzufügen. Benutzer mit Organisator- und Referentenrollen können einer Besprechung Registerkarten hinzufügen.

So fügen Sie einer Besprechung eine Registerkarte hinzu:

1. Wählen Sie in Ihrem Kalender eine Besprechung aus, der Sie eine Registerkarte hinzufügen möchten.
1. Wählen Sie die Registerkarte **Details** aus, und wählen Sie <img src="~/assets/images/apps-in-meetings/plusbutton.png" alt="Plus button" width="30"/>.

    <img src="../assets/images/apps-in-meetings/PreMeeting1.png" alt="Pre-meeting experience" width="900"/>

1. Wählen Sie im angezeigten Registerkartenkatalog die App aus, die Sie hinzufügen möchten, und führen Sie die erforderlichen Schritte aus. Die App wird als Registerkarte installiert.

So fügen Sie einer Besprechung eine Nachrichtenerweiterung hinzu:

1. Wählen Sie die Auslassungspunkte &#x25CF;&#x25CF;&#x25CF; aus, die sich im Bereich „Nachricht verfassen“ im Chat befinden.
1. Wählen Sie die App aus, die Sie hinzufügen möchten, und führen Sie die erforderlichen Schritte aus. Die App wird als Nachrichtenerweiterung installiert.

So fügen Sie einer Besprechung einen Bot hinzu:

Geben Sie in einem Besprechungschat den Schlüssel **@** ein, und wählen Sie **Bots abrufen** aus.

> [!NOTE]
>
> * Das besprechungsinterne Dialogfeld zeigt ein Dialogfeld in einer Besprechung an und postet gleichzeitig eine adaptive Karte im Besprechungschat, auf die Benutzer zugreifen können. Die adaptive Karte im Besprechungschat hilft Benutzern während der Teilnahme an der Besprechung, oder wenn die Teams-App minimiert ist.
> * Die Benutzeridentität muss mit den [SSO-Registerkarten](../tabs/how-to/authentication/tab-sso-overview.md) bestätigt werden. Nach der Authentifizierung kann die App die Benutzerrolle mithilfe der `GetParticipant`-API abrufen.
> * Basierend auf der Benutzerrolle kann die App rollenspezifische Erfahrungen bieten. Beispielsweise ermöglicht eine Umfrage-App nur Organisatoren und Referenten das Erstellen einer neuen Umfrage.
> * Rollenzuweisungen können geändert werden, während eine Besprechung ausgeführt wird. Weitere Informationen finden Sie unter [Rollen in einer Teams-Besprechung](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019).

### <a name="during-a-meeting"></a>Während einer Besprechung

Während einer Besprechung können Sie die `meetingSidePanel` oder die besprechungsinterne Benachrichtigung verwenden, um einzigartige Erfahrungen für Ihre Apps zu erstellen.

#### <a name="meeting-sidepanel"></a>Besprechungsseitenbereich

Mit dem `meetingSidePanel` können Sie Erfahrungen in einer Besprechung anpassen, die es Organisatoren und Referenten ermöglichen, einen unterschiedlichen Satz von Ansichten und Aktionen zu haben. In Ihrem App-Manifest müssen Sie dem Kontextarray `meetingSidePanel` hinzufügen. In der Besprechung und in allen Szenarien wird die App auf einer besprechungsinterne Registerkarte mit einer Breite von 320 Pixel gerendert. Weitere Informationen finden Sie unter [FrameInfo-Schnittstelle](/javascript/api/@microsoft/teams-js/frameinfo) (vor TeamsJS v.2.0.0 bekannt als `FrameContext`).

Sie können den [Kontext des Benutzers verwenden, um Anforderungen weiterzuleiten](../tabs/how-to/access-teams-context.md#user-context). Weitere Informationen finden Sie unter [Teams-Authentifizierungsablauf für Registerkarten](../tabs/how-to/authentication/auth-flow-tab.md). Der Authentifizierungsablauf für Registerkarten ähnelt dem Authentifizierungsfluss für Websites. Registerkarten können OAuth 2.0 direkt verwenden. Weitere Informationen finden Sie unter [Microsoft-Identitätsplattform und OAuth 2.0-Autorisierungscodefluss](/azure/active-directory/develop/v2-oauth2-auth-code-flow).

Die Nachrichtenerweiterung funktioniert erwartungsgemäß, wenn sich ein Benutzer in einer besprechungsinternen Ansicht befindet. Der Benutzer kann Erweiterungskarten zum Verfassen von Nachrichten posten. AppName in der Besprechung ist eine QuickInfo, die den App-Namen in der besprechungsinternen U-Leiste angibt.

> [!NOTE]
> Verwenden Sie die Version 1.7.0 oder höher von [Teams-SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true), da frühere Versionen den Seitenbereich nicht unterstützen.

#### <a name="in-meeting-notification"></a>Besprechungsinterne Benachrichtigung

Die besprechungsinterne Benachrichtigung wird verwendet, um Teilnehmer während der Besprechung einzubeziehen und während der Besprechung Informationen oder Feedback zu sammeln. Verwenden Sie [besprechungsinterne Benachrichtigungsnutzdaten](API-references.md#send-an-in-meeting-notification), um eine besprechungsinterne Benachrichtigung auszulösen. Fügen Sie als Teil der Nutzdaten der Benachrichtigungsanforderung die URL ein, unter welcher der anzuzeigende Inhalt gehostet wird.

Besprechungsinterne Benachrichtigungen dürfen kein Aufgabenmodul verwenden. Das Aufgabenmodul wird nicht in einem Besprechungschat aufgerufen. Eine externe Ressourcen-URL wird verwendet, um besprechungsinterne Benachrichtigungen anzuzeigen. Sie können die Methode `submitTask` verwenden, um Daten in einem Besprechungschat zu übermitteln.

:::image type="content" source="../assets/images/apps-in-meetings/in-meeting-dialogbox.png" alt-text="Beispiel zeigt, wie Sie ein besprechungsinternes Dialogfeld verwenden können.":::

Sie können das Microsoft Teams-Anzeigebild und die Personenkarte des Benutzers auch zu Benachrichtigungen in Besprechungen hinzufügen, basierend auf einem `onBehalfOf`-Token mit Benutzer-MRI und dem in der Nutzlast übergebenen Anzeigenamen. Folgendes ist eine Beispielnutzlast:

```json
    {
       "type": "message",
       "text": "John Phillips assigned you a weekly todo",
       "summary": "Don't forget to meet with Marketing next week",
       "channelData": {
           onBehalfOf: [
             { 
               itemId: 0, 
               mentionType: 'person', 
               mri: context.activity.from.id, 
               displayname: context.activity.from.name 
             }
            ],
           "notification": {
           "alertInMeeting": true,
           "externalResourceUrl": "https://teams.microsoft.com/l/bubble/APP_ID?url=<url>&height=<height>&width=<width>&title=<title>&completionBotId=BOT_APP_ID"
            }
        },
       "replyToId": "1493070356924"
    }
```

:::image type="content" source="../assets/images/apps-in-meetings/in-meeting-people-card.png" alt-text="Das Beispiel zeigt, wie das Microsoft Teams-Anzeigebild und die Personenkarte in Besprechungsdialogfeldern verwendet werden." border="true":::

#### <a name="shared-meeting-stage"></a>Freigegebenes Besprechungsfreigabefenster

Das geteilte Freigabefenster ermöglicht Besprechungsteilnehmern die Interaktion mit und die Zusammenarbeit an App-Inhalten in Echtzeit. Sie können Ihre Apps auf folgende Weise für das gemeinschaftliche Freigabefenster freigeben:

* [Teilen Sie die gesamte App mithilfe](#share-entire-app-to-stage) der Schaltfläche "Teilen auf Stufe" im Besprechungsseitenbereich des Teams-Clients oder über [[Deep-Links](#generate-a-deep-link-to-share-content-to-stage-in-meetings)".
* [Freigabe bestimmter Teile der App für das Freigabefenster](#share-specific-parts-of-the-app-to-stage) mithilfe von APIs im Teams-Client-SDK.

##### <a name="share-entire-app-to-stage"></a>Freigeben der gesamten App für das Freigabefenster

Teilnehmer können die gesamte App mithilfe der Schaltfläche „Freigabe für Freigabefenster“ im App-Seitenbereich für das gemeinschaftliche Freigabefenster freigeben.

<img src="../assets/images/apps-in-meetings/share_to_stage_during_meeting.png" alt="Share full app" width = "900"/>

Um die gesamte App für das Freigabefenster freizugeben, müssen Sie im App-Manifest `meetingStage` und `meetingSidePanel` als Framekontexte konfigurieren. Beispiel:

```json
"configurableTabs": [
   {
      "configurationUrl": "https://contoso.com/teamstab/configure",
      "canUpdateConfiguration": true,
      "scopes": [
         "groupchat"
        ],
      "context":[
         "meetingSidePanel",
         "meetingStage"
        ]
    }
]
```

Weitere Informationen finden Sie unter [App-Manifest](../resources/schema/manifest-schema-dev-preview.md#configurabletabs).

##### <a name="share-specific-parts-of-the-app-to-stage"></a>Freigeben bestimmter Teile der App für das Freigabefenster.

Teilnehmer können bestimmte Teile der App für das gemeinschaftliche Freigabefenster freigeben, indem sie das Freigabefenster zum Bereitstellen von APIs verwenden. Die APIs sind im Teams-Client-SDK verfügbar und werden über den App-Seitenbereich aufgerufen.

<img src="../assets/images/apps-in-meetings/share-specific-content-to-stage.png" alt="Share specific parts of the app" width = "900"/>

Um bestimmte Teile der App für das Freigabefenster freizugeben, müssen Sie die zugehörigen APIs in der Teams-Client-SDK-Bibliothek aufrufen. Weitere Informationen finden Sie unter [API-Referenz](API-references.md).

> [!NOTE]
>
> * Verwenden Sie die Teams-Manifestversion 1.12 oder höher, um bestimmte Teile der App für das Freigabefenster freizugeben.
> * Sie können bestimmte Teile der App nur auf Teams-Desktopclients für die Besprechungsphase freigeben. Mobile Benutzer können bestimmte Teile der App freigeben, um sie mithilfe der [Api für die Freigabe zu inszenieren](API-references.md#share-app-content-to-stage-api).

### <a name="after-a-meeting"></a>Nach einer Besprechung

Die Konfigurationen für nach und [vor Besprechungen](#before-a-meeting) sind identisch.

## <a name="generate-a-deep-link-to-share-content-to-stage-in-meetings"></a>Generieren eines Deep-Links zum Freigeben von Inhalten für die Phase in Besprechungen

Sie können auch einen Deep-Link generieren, um [die App für das Bereitstellen](#share-entire-app-to-stage) und Starten oder Teilnehmen an einer Besprechung freizugeben.

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
* `appSharingUrl`: Die URL, die in der Phase freigegeben werden muss, sollte eine gültige Domäne sein, die im App-Manifest definiert ist. Wenn die URL keine gültige Domäne ist, wird ein Fehlerdialogfeld angezeigt, in dem dem Benutzer eine Beschreibung des Fehlers angezeigt wird.
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
| Besprechungs-App | Veranschaulicht, wie die Generator-App für Besprechungstoken verwendet wird, um ein Token anzufordern. Das Token wird sequenziell generiert, sodass jeder Teilnehmer eine angemessene Gelegenheit hat, in einer Besprechung mitzuwirken. Das Token ist in Situationen wie Scrum-Besprechungen und Q&A-Sitzungen nützlich. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-token-app/csharp) | [Anzeigen](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-token-app/nodejs) |
|Beispiel für Freigabefenster | Beispiel-App zum Anzeigen einer Registerkarte im Freigabefenster für die Zusammenarbeit | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-stage-view/csharp) | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-stage-view/nodejs) |
|Besprechungsseitenbereich | Beispiel-App zum zeigen, wie eine Agenda in einem Besprechungsseitenbereich hinzugefügt wird | [Anzeigen](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-sidepanel/csharp) |-|

## <a name="step-by-step-guides"></a>Schritt-für-Schritt-Anleitungen

* Befolgen Sie die [Schritt-für-Schritt-Anleitung](../sbs-meeting-token-generator.yml), um in Ihrer Teams-Besprechung Besprechungstoken zu generieren.
* Befolgen Sie die [Schritt-für-Schritt-Anleitung](../sbs-meetings-sidepanel.yml), um in Ihrer Teams-Besprechung einen Besprechungsseitenbereich zu generieren.
* Befolgen Sie die [Schritt-für-Schritt-Anleitung](../sbs-meetings-stage-view.yml), um in Ihrer Teams-Besprechung die Freigabefensteransicht freizugeben.
* Befolgen Sie die [Schritt-für-Schritt-Anleitung](../sbs-meeting-content-bubble.yml), um in Ihrer Teams-Besprechung eine Besprechungsinhaltsblase zu generieren.

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [API-Referenzen für Besprechungs-Apps](API-references.md)

## <a name="see-also"></a>Siehe auch

* [Entwurfsrichtlinien für besprechungsinternes Dialogfeld](design/designing-apps-in-meetings.md#use-an-in-meeting-dialog)
* [Teams-Authentifizierungsablauf für Registerkarten](../tabs/how-to/authentication/auth-flow-tab.md)
* [Entwurfsrichtlinien für die Erfahrung geteilter Freigabefenster](~/apps-in-teams-meetings/design/designing-apps-in-meetings.md)
* [Apps über Microsoft Graph zu Besprechungen hinzufügen](/graph/api/chat-post-installedapps?view=graph-rest-1.0&tabs=http&preserve-view=true)
