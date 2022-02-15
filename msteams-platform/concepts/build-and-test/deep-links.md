---
title: Erstellen von Deep-Links
description: Beschreibt Deeplinks und deren Verwendung in Ihren Apps
ms.topic: how-to
ms.localizationpriority: high
keywords: Deeplink für Teams
ms.openlocfilehash: 9d9e0ff794d413be1959e8e8ddaef1086acc307d
ms.sourcegitcommit: b9af51e24c9befcf46945400789e750c34723e56
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 02/15/2022
ms.locfileid: "62821388"
---
# <a name="create-deep-links"></a>Erstellen von Deep-Links 

Sie können Links zu Informationen und Features in Teams erstellen. Die folgenden Szenarien beim Erstellen von Deeplinks hilfreich:

* Navigieren des Benutzers zum Inhalt auf einer der Registerkarten Ihrer App. Ihre App kann beispielsweise über einen Bot verfügen, der Nachrichten sendet, welche den Benutzer in Bezug auf eine wichtige Aktivität benachrichtigen. Wenn der Benutzer auf die Benachrichtigung tippt, navigiert der Deeplink zur Registerkarte, sodass der Benutzer weitere Details zur Aktivität anzeigen kann.
* Ihre App automatisiert oder vereinfacht bestimmte Benutzeraufgaben, z. B. das Erstellen eines Chats oder das Planen einer Besprechung, indem die Deeplinks vorab mit den erforderlichen Parametern versehen werden. Dadurch müssen Benutzer die Informationen nicht manuell eingeben.

> [!NOTE]
>
> Ein Deeplink startet zunächst den Browser, bevor er zu Inhalten navigiert. Deeplinks verhalten sich bei Teams-Entitäten folgendermaßen:
>
> **Registerkarte**:  
> ✔ navigiert direkt zur Deeplink-URL.
>
> **Bot**:  
> ✔ Deeplink im Kartentext: Wird zuerst im Browser geöffnet.  
> ✔ Deeplink zur OpenURL-Aktion in adaptiver Karte hinzugefügt: Navigiert direkt zur Deeplink-URL.  
> ✔ Hyperlinkmarkdowntext auf der Karte: Wird zuerst im Browser geöffnet.  
>
> **Chat**:  
> ✔ Textnachrichten-Hyperlink-Markdown: Navigiert direkt zur Deeplink-URL.  
> ✔ In allgemeine Chatunterhaltung eingefügte Link: Navigiert direkt zur Deeplink-URL.

## <a name="deep-linking-to-your-tab"></a>Deeplink-Verknüpfung mit Ihrer Registerkarte

Sie können Deeplinks zu Entitäten in Teams erstellen. Dies wird verwendet, um Links zu erstellen, die zu Inhalten und Informationen auf Ihrer Registerkarte navigieren. Wenn Ihre Registerkarte beispielsweise eine Aufgabenliste enthält, können Teammitglieder Links zu einzelnen Aufgaben erstellen und freigeben. Wenn Sie den Link auswählen, navigieren Sie darüber zu Ihrer Registerkarte, die sich auf das jeweilige Element konzentriert. Um dies zu implementieren, fügen Sie jedem Element eine Aktion **Link kopieren** hinzu, unabhängig davon, welche Art und Weise Ihrer Benutzeroberfläche am ehesten entspricht. Wenn der Benutzer diese Aktion ausführt, rufen Sie `shareDeepLink()` auf, um ein Dialogfeld mit einem Link anzuzeigen, den der Benutzer in die Zwischenablage kopieren kann. Bei diesem Aufruf übermitteln Sie auch eine ID für Ihr Element, die Sie im [Kontext](~/tabs/how-to/access-teams-context.md)zurückerhalten, wenn dem Link gefolgt wird und Ihre Registerkarte neu geladen wird.

Alternativ können Sie Deeplinks auch programmgesteuert unter Verwendung des später in diesem Thema aufgeführten Formats generieren. Sie können Deeplinks in [Bot](~/bots/what-are-bots.md)- und [Connector](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md)-Nachrichten verwenden, die Benutzer über Änderungen an Ihrer Registerkarte oder an darin enthaltenen Elementen informieren.

> [!NOTE]
> Dieser Deeplink unterscheidet sich von den Links, die vom Menüelement **Link zur Registerkarte kopieren** bereitgestellt werden. Dadurch wird lediglich ein Deeplink generiert, der auf diese Registerkarte verweist.

>[!NOTE]
> Derzeit funktioniert shareDeepLink nicht auf mobilen Plattformen.

### <a name="show-a-deep-link-to-an-item-within-your-tab"></a>Anzeigen eines Deeplinks zu einem Element auf Ihrer Registerkarte

Rufen Sie `microsoftTeams.shareDeepLink({ subEntityId: <subEntityId>, subEntityLabel: <subEntityLabel>, subEntityWebUrl: <subEntityWebUrl> })` auf, um ein Dialogfeld anzuzeigen, das einen Deeplink zu einem Element auf der Registerkarte enthält.

Geben Sie die folgenden Felder an:

* `subEntityId`: Ein eindeutiger Bezeichner für das Element auf Ihrer Registerkarte, zu dem Sie eine Deeplink-Verknüpfung erstellen.
* `subEntityLabel`: Eine Beschriftung für das Element, das zum Anzeigen des Deeplinks verwendet werden soll.
* `subEntityWebUrl`: Ein optionales Feld mit einer Fallback-URL, das verwendet werden soll, wenn der Client das Rendern der Registerkarte nicht unterstützt.

### <a name="generate-a-deep-link-to-your-tab"></a>Generieren eines Deeplinks zu Ihrer Registerkarte

> [!NOTE]
> Persönliche Registerkarten haben einen `personal` Bereich, während Kanal- und Gruppenregisterkarten `team` oder `group` Bereiche nutzen. Die Syntax der beiden Registerkartentypen unterscheidet sich geringfügig, da nur dem Kontextobjekt der konfigurierbaren Registerkarte eine `channel` Eigenschaft zugeordnet ist. Weitere Informationen zu Registerkartenbereichen finden Sie in der [Manifest](~/resources/schema/manifest-schema.md)-Referenz.

> [!NOTE]
> Deeplinks funktionieren nur ordnungsgemäß, wenn die Registerkarte mithilfe der Bibliothek v0.4 oder höher konfiguriert wurde und daher eine Entitäts-ID vorhanden ist. Deeplinks zu Registerkarten ohne Entitäts-IDs navigieren weiterhin zur Registerkarte, können aber die Unterentitäts-ID nicht auf der Registerkarte bereitstellen.

Verwenden Sie das folgende Format für einen Deeplink, den Sie in einer Bot-, Connector- oder Messaging-Erweiterungskarte verwenden können:

`https://teams.microsoft.com/l/entity/<appId>/<entityId>?webUrl=<entityWebUrl>&label=<entityLabel>&context=<context>`

> [!NOTE]
> Wenn der Bot eine Nachricht `TextBlock` mit einem Deeplink sendet, wird eine neue Browserregisterkarte geöffnet, wenn der Benutzer den Link auswählt. Dies geschieht in Chrome und in der Microsoft Teams Desktop-App, die beide unter Linux ausgeführt werden.
> Wenn der Bot dieselbe Deeplink-URL an eine(n) `Action.OpenUrl` sendet, wird die Registerkarte Teams in der aktuellen Browserregisterkarte geöffnet, wenn der Benutzer den Link auswählt. Es wird keine neue Browserregisterkarte geöffnet.

Die Abfrageparameter sind:

| Parametername | Beschreibung | Beispiel |
|:------------|:--------------|:---------------------|
| `appId`&emsp; | Die ID aus Ihrem Manifest. |fe4a8eba-2a31-4737-8e33-e5fae6fee194|
| `entityId`&emsp; | Die ID für das Element auf der Registerkarte, die Sie beim [Konfigurieren der Registerkarte](~/tabs/how-to/create-tab-pages/configuration-page.md)angegeben haben.|Tasklist123|
| `entityWebUrl` oder `subEntityWebUrl`&emsp; | Ein optionales Feld mit einer Fallback-URL, das verwendet werden soll, wenn der Client das Rendern der Registerkarte nicht unterstützt. | `https://tasklist.example.com/123` oder `https://tasklist.example.com/list123/task456` |
| `entityLabel` oder `subEntityLabel`&emsp; | Eine Beschriftung für das Element auf Ihrer Registerkarte, die beim Anzeigen des Deeplinks verwendet werden soll. | Task List 123 oder Task 456 |
| `context`&emsp; </br></br>* `subEntityId`&emsp;</br></br> * `channelId`&emsp;| Ein JSON-Objekt, das die folgenden Felder enthält:</br></br> * Eine ID für das Element auf der Registerkarte. </br></br> * Die Microsoft Teams Kanal-ID, die auf der Registerkarte [Kontext](~/tabs/how-to/access-teams-context.md) verfügbar ist. | 
| `subEntityId`&emsp; | Eine ID für das Element auf der Registerkarte. |Task456 |
| `channelId`&emsp; | Die Microsoft Teams Kanal-ID, die auf der Registerkarte [Kontext](~/tabs/how-to/access-teams-context.md) verfügbar ist. Diese Eigenschaft ist nur in konfigurierbaren Registerkarten mit einem **Team**-Bereich verfügbar. Sie ist nicht auf statischen Registerkarten verfügbar, die über einen **persönlichen** Bereich verfügen.| 19:cbe3683f25094106b826c9cada3afbe0@thread.skype |

Beispiele:

* Link zu der jeweiligen konfigurierbaren Registerkarte: `https://teams.microsoft.com/l/entity/fe4a8eba-2a31-4737-8e33-e5fae6fee194/tasklist123?webUrl=https://tasklist.example.com/123&label=Task List 123&context={"channelId": "19:cbe3683f25094106b826c9cada3afbe0@thread.skype"}`
* Link zu einem Aufgabenelement auf der konfigurierbaren Registerkarte: `https://teams.microsoft.com/l/entity/fe4a8eba-2a31-4737-8e33-e5fae6fee194/tasklist123?webUrl=https://tasklist.example.com/123/456&label=Task 456&context={"subEntityId": "task456","channelId": "19:cbe3683f25094106b826c9cada3afbe0@thread.skype"}`
* Link zu der jeweiligen statischen Registerkarte: `https://teams.microsoft.com/l/entity/fe4a8eba-2a31-4737-8e33-e5fae6fee194/tasklist123?webUrl=https://tasklist.example.com/123&label=Task List 123`
* Link zu einem Aufgabenelement auf der statischen Registerkarte: `https://teams.microsoft.com/l/entity/fe4a8eba-2a31-4737-8e33-e5fae6fee194/tasklist123?webUrl=https://tasklist.example.com/123/456&label=Task 456&context={"subEntityId": "task456"}`

> [!IMPORTANT]
> Stellen Sie sicher, dass alle Abfrageparameter ordnungsgemäß URI-codiert sind. Sie müssen den vorangehenden Beispielen mithilfe des letzten Beispiels folgen:

> ```javascript
> var encodedWebUrl = encodeURI('https://tasklist.example.com/123/456&label=Task 456');
> var encodedContext = encodeURI('{"subEntityId": "task456"}');
> var taskItemUrl = 'https://teams.microsoft.com/l/entity/fe4a8eba-2a31-4737-8e33-e5fae6fee194/tasklist123?webUrl=' + encodedWebUrl + '&context=' + encodedContext;
> ```

### <a name="consume-a-deep-link-from-a-tab"></a>Verwenden eines Deeplinks von einer Registerkarte

Beim Navigieren zu einem Deeplink navigiert Microsoft Teams einfach zur Registerkarte und bietet einen Mechanismus über die Microsoft Teams JavaScript-Bibliothek zum Abrufen der Unterentitäts-ID, sofern vorhanden.

Beim Aufruf von [`microsoftTeams.getContext`](/javascript/api/@microsoft/teams-js#getcontext--context--context-----void-) wird ein Kontext ausgegeben, der das Feld `subEntityId` enthält, wenn die Navigation Registerkartennavigation über einen Deeplink erfolgt.

## <a name="deep-linking-from-your-tab"></a>Deeplink-Verknüpfung von Ihrer Registerkarte aus

Sie können Deeplinks zu Inhalten in Teams von Ihrer Registerkarte aus erstellen. Dies ist nützlich, wenn Ihre Registerkarte mit anderen Inhalten in Teams verknüpft werden muss, z. B. zu einem Kanal, einer Nachricht, einer anderen Registerkarte oder sogar zum Öffnen eines Planungsdialogfelds. Um einen Deeplink von Ihrer Registerkarte aus auszulösen, sollten Sie Folgendes aufrufen:

```Javascript
microsoftTeams.executeDeepLink(/*deepLink*/);
```

Mit diesem Aufruf navigieren Sie zur richtigen URL oder lösen eine Clientaktion aus, wie z. B. das Öffnen eines Planungs- oder App-Installationsdialogfelds. Sehen Sie sich das folgende Beispiel an:

```Javascript
// Open a scheduling dialog from your tab
microsoftTeams.executeDeepLink("https://teams.microsoft.com/l/meeting/new?subject=test%20subject&attendees=joe@contoso.com,bob@contoso.com&startTime=10%2F24%2F2018%2010%3A30%3A00&endTime=10%2F24%2F2018%2010%3A30%3A00&content=test%3Acontent");

// Open an app install dialog from your tab
microsoftTeams.executeDeepLink("https://teams.microsoft.com/l/app/f46ad259-0fe5-4f12-872d-c737b174bcb4");
```

## <a name="deep-linking-to-a-chat"></a>Deeplinks zu einem Chat

Sie können Deeplinks zu privaten Chats zwischen Benutzern erstellen, indem Sie die Teilnehmergruppe angeben. Wenn kein Chat mit den angegebenen Teilnehmern vorhanden ist, navigiert der Benutzer über den Link zu einem leeren neuen Chat. Neue Chats werden im Entwurfsstatus erstellt, bis der Benutzer die erste Nachricht sendet. Andernfalls können Sie den Namen des Chats angeben, falls er noch nicht vorhanden ist, zusammen mit Text, der in das Feld zum Verfassen des Benutzers eingefügt werden soll. Sie können sich dieses Feature als eine Verknüpfung vorstellen, mit der der Benutzer manuell zum Chat navigieren oder diesen erstellen und dann die Nachricht eingeben kann.

Wenn Sie beispielsweise ein Office 365 Benutzerprofil von Ihrem Bot als Karte ausgeben, kann der Benutzer über diesen Deeplink einfach mit dieser Person chatten.

### <a name="generate-a-deep-link-to-a-chat"></a>Generieren eines Deeplinks zu einem Chat

Verwenden Sie dieses Format für einen Deeplink, den Sie auf einer Bot-, Connector- oder Messaging-Erweiterungskarte verwenden können:

`https://teams.microsoft.com/l/chat/0/0?users=<user1>,<user2>,...&topicName=<chat name>&message=<precanned text>`

Beispiel: `https://teams.microsoft.com/l/chat/0/0?users=joe@contoso.com,bob@contoso.com&topicName=Prep%20For%20Meeting%20Tomorrow&message=Hi%20folks%2C%20kicking%20off%20a%20chat%20about%20our%20meeting%20tomorrow`

Die Abfrageparameter sind:

* `users`: Die durch Kommas getrennte Liste der Benutzer-IDs, auf der die Chat-Teilnehmer angegeben sind. Der Benutzer, der die Aktion ausführt, ist immer als Teilnehmer enthalten. Derzeit unterstützt das Feld „Benutzer-ID“ das Microsoft Azure Active Directory (Azure AD) UserPrincipalName, wie z. B. nur eine E-Mail-Adresse.
* `topicName`: Ein optionales Feld für den Anzeigenamen des Chats, für einen Chats mit 3 oder mehr Benutzern. Wenn dieses Feld nicht angegeben ist, basiert der Anzeigename des Chats auf den Namen der Teilnehmer.
* `message`: Ein optionales Feld für den Nachrichtentext, den Sie in das Feld zum Verfassen des aktuellen Benutzers einfügen möchten, während sich der Chat im Entwurfszustand befindet.

Um diesen Deeplink mit Ihrem Bot zu verwenden, geben Sie diesen als URL-Ziel auf der Schaltfläche Ihrer Karte an, oder tippen Sie über den Aktionstyp `openUrl` auf die Aktion.

## <a name="generate-deep-links-to-file-in-channel"></a>Generieren von Deeplinks zu Dateien im Kanal

Das folgende Deeplink-Format kann auf einer Bot-, Connector- oder Messaging-Erweiterungskarte verwendet werden:

`https://teams.microsoft.com/l/file/<fileId>?tenantId=<tenantId>&fileType=<fileType>&objectURL=<objectURL>&baseUrl=<baseURL>&serviceName=<Name>&threadId=<threadId>&groupId=<groupId>`

Die Abfrageparameter sind:

* `fileId`: Eindeutige Datei-ID aus Sharepoint Online, auch als sourcedoc bezeichnet. Beispiel: 1FA202A5-3762-4F10-B550-C04F81F6ACBD
* `tenantId`: Beispiel für eine Mandanten-ID, 0d9b645f-597b-41f0-a2a3-ef103fbd91bb
* `fileType`: Unterstützter Dateityp, wie beispielsweise docx, pptx, xlsx und pdf
* `objectUrl`: Objekt-URL der Datei. Das Format ist `https://{tenantName}.sharepoint.com/sites/{TeamName}/SharedDocuments/{ChannelName}/FileName.ext`. Beispiel: `https://microsoft.sharepoint.com/teams/(filepath)`
* `baseUrl`: Basis-URL der Datei. Das Format ist `https://{tenantName}.sharepoint.com/sites/{TeamName}`. Beispiel: `https://microsoft.sharepoint.com/teams`
* `serviceName`: Name des Diensts, App-ID. Beispielsweise Teams.
* `threadId`: Die threadId ist die Team-ID des Teams, in dem die Datei gespeichert ist. Sie ist optional und kann nicht für Dateien festgelegt werden, die im OneDrive Ordner eines Benutzers gespeichert sind. threadId – 19:f8fbfc4d89e24ef5b3b8692538cebeb7@thread.skype
* `groupId`: Gruppen-ID der Datei, ae063b79-5315-4ddb-ba70-27328ba6c31e 

> [!NOTE]
> Sie können `threadId` und `groupId` in der URL dieses Kanals sehen.  

Das folgende Deeplink-Format wird in einer Bot-, Connector- oder Messaging-Erweiterungskarte verwendet: `https://teams.microsoft.com/l/file/<fileId>?tenantId=<tenantId>&fileType=<fileType>&objectURL=<objectURL>&baseUrl=<baseURL>&serviceName=<Name>&threadId=<threadId>&groupId=<groupId>`

Das folgende Beispielformat zeigt den Deeplink zu Dateien:

`https://teams.microsoft.com/l/file/5E0154FC-F2B4-4DA5-8CDA-F096E72C0A80?tenantId=0d9b645f-597b-41f0-a2a3-ef103fbd91bb&fileType=pptx&objectUrl=https%3A%2F%2Fmicrosoft.sharepoint.com%2Fteams%2FActionPlatform%2FShared%20Documents%2FFC7-%20Bot%20and%20Action%20Infra%2FKaizala%20Actions%20in%20Adaptive%20Cards%20-%20Deck.pptx&baseUrl=https%3A%2F%2Fmicrosoft.sharepoint.com%2Fteams%2FActionPlatform&serviceName=teams&threadId=19:f8fbfc4d89e24ef5b3b8692538cebeb7@thread.skype&groupId=ae063b79-5315-4ddb-ba70-27328ba6c31e`

### <a name="serialization-of-this-object"></a>Serialisierung dieses Objekts:
```
{
fileId: "5E0154FC-F2B4-4DA5-8CDA-F096E72C0A80",
tenantId: "0d9b645f-597b-41f0-a2a3-ef103fbd91bb",
filetype: = "pptx",
objectUrl: "https://microsoft.sharepoint.com/teams/ActionPlatform/Shared Documents/FC7- Bot and Action Infra/Kaizala Actions in Adaptive Cards - Deck.pptx",
baseUrl: "https://microsoft.sharepoint.com/teams/ActionPlatform",
serviceName: "teams",
threadId: = "19:f8fbfc4d89e24ef5b3b8692538cebeb7@thread.skype",
groupId: "ae063b79-5315-4ddb-ba70-27328ba6c31e"
}
```

## <a name="deep-linking-to-an-app"></a>Deeplinks zu einer App

Erstellen Sie Deeplinks für die App, nachdem die App im Teams Store aufgeführt wurde. Um einen Link zum Starten von Teams zu erstellen, fügen Sie die App-ID der folgenden URL hinzu: `https://teams.microsoft.com/l/app/<your-app-id>`. Es wird ein Dialogfeld angezeigt, um die App zu installieren. 
  
## <a name="deep-linking-for-sharepoint-framework-tabs"></a>Deeplink-Verknüpfung für SharePoint-Framework-Registerkarten

Das folgende Deeplink-Format kann auf einer Bot-, Connector- oder Messaging-Erweiterungskarte verwendet werden: `https://teams.microsoft.com/l/entity/<AppId>/<EntityId>?webUrl=<entityWebUrl>/<EntityName>`

> [!NOTE]
> Wenn ein Bot eine TextBlock-Nachricht mit einem Deeplink sendet, wird eine neue Browserregisterkarte geöffnet, wenn Benutzer den Link auswählen. Dies erfolgt in der Chrome und Microsoft Teams Desktop-App, die unter Linux ausgeführt wird.
> Wenn der Bot dieselbe Deeplink-URL an eine(n) `Action.OpenUrl` sendet, wird die Registerkarte Teams im aktuellen Browser geöffnet, wenn der Benutzer den Link auswählt. Es wird keine neue Browserregisterkarte geöffnet.

Die Abfrageparameter sind:

* `appID`: Ihre Manifest-ID, z. B. **fe4a8eba-2a31-4737-8e33-e5fae6fee194**.

* `entityID`: Die Element-ID, die Sie beim [Konfigurieren der Registerkarte](~/tabs/how-to/create-tab-pages/configuration-page.md)angegeben haben. Zum Beispiel: **tasklist123**.
* `entityWebUrl`: Ein optionales Feld mit einer Fallback-URL, das verwendet werden soll, wenn der Client das Rendern der Registerkarte – `https://tasklist.example.com/123` oder `https://tasklist.example.com/list123/task456` – nicht unterstützt.
* `entityName`: Eine Beschriftung für das Element auf Ihrer Registerkarte, das beim Anzeigen des Deeplinks, Task List 123 oder Task 456, verwendet werden soll.

Beispiel: https://teams.microsoft.com/l/entity/fe4a8eba-2a31-4737-8e33-e5fae6fee194/tasklist123?webUrl=https://tasklist.example.com/123&TaskList

## <a name="deep-linking-to-the-scheduling-dialog"></a>Generieren einer Deeplink-Verknüpfung zum Planungsdialogfeld

> [!NOTE]
> Dieses Feature befindet sich derzeit in der Entwicklervorschau.

Sie können Deeplinks zu dem in Teams integrierten Planungsdialogfeld erstellen. Dies ist besonders nützlich, wenn Ihre App dem Benutzer beim Ausführen von Kalender- oder Planungsaufgaben hilft.

### <a name="generate-a-deep-link-to-the-scheduling-dialog"></a>Generieren eines Deeplinks zum Planungsdialogfeld

Verwenden Sie das folgende Format für einen Deeplink, den Sie auf einer Bot-, Connector- oder Messaging-Erweiterungskarte verwenden können: `https://teams.microsoft.com/l/meeting/new?subject=<meeting subject>&startTime=<date>&endTime=<date>&content=<content>&attendees=<user1>,<user2>,<user3>,...`

Beispiel: `https://teams.microsoft.com/l/meeting/new?subject=test%20subject&attendees=joe@contoso.com,bob@contoso.com&startTime=10%2F24%2F2018%2010%3A30%3A00&endTime=10%2F24%2F2018%2010%3A30%3A00&content=test%3Acontent`

> [!NOTE]
> Die Suchparameter unterstützen kein `+` Signal anstelle von Leerzeichen (` `). Stellen Sie sicher, dass der URI-Codierungscode `%20` für Leerzeichen ausgibt, z. B. `?subject=test%20subject` ist gut, aber `?subject=test+subject` ist schlecht.

Die Abfrageparameter sind:

* `attendees`: Die optionale durch Kommas getrennte Liste der Benutzer-IDs, auf der die Teilnehmer der Besprechung angegeben sind. Der Benutzer, der die Aktion ausführt, ist der Besprechungsorganisator. Derzeit unterstützt das Feld „Benutzer-ID“ nur den Azure AD UserPrincipalName, in der Regel eine E-Mail-Adresse.
* `startTime`: Die optionale Startzeit des Ereignisses. Diese sollte im [langen ISO 8601-Format](https://en.wikipedia.org/wiki/ISO_8601)vorliegen, wie z. B. *2018-03-12T23:55:25+02:00*.
* `endTime`: Die optionale Endzeit des Ereignisses, ebenfalls im ISO 8601-Format.
* `subject`: Ein optionales Feld für den Betreff der Besprechung.
* `content`: Ein optionales Feld für das Besprechungsdetails-Feld.

> [!NOTE]
> Derzeit wird die Angabe des Speicherorts nicht unterstützt. Sie müssen den UTC-Offset angeben, d. h. Zeitzonen beim Generieren der Start- und Endzeiten.

Um diesen Deeplink mit Ihrem Bot zu verwenden, können Sie diesen als URL-Ziel auf der Schaltfläche Ihrer Karte angeben oder über den Aktionstyp `openUrl` auf die Aktion tippen.

## <a name="deep-linking-to-an-audio-or-audio-video-call"></a>Deeplink-Verknüpfung mit einem Audio- oder Audio-Video-Anruf

Sie können Deeplinks erstellen, um nur Audio- oder Audiovideoanrufe an einen einzelnen Benutzer oder eine Gruppe von Benutzern aufzurufen, indem Sie den Anruftyp als *Audio* oder *Av* festlegen und die Teilnehmer angeben. Nachdem der Deeplink aufgerufen wurde und bevor der Anruf erfolgt, fordert der Teams Desktopclient eine Bestätigung für den Anruf an. Im Falle eines Gruppenanrufs können Sie eine Gruppe von VoIP-Benutzern und eine Gruppe von PSTN-Benutzern mit demselben Deeplink-Aufruf anrufen. 

Bei einem Videoanruf fordert der Client eine Bestätigung an und aktiviert das Video des Anrufers für den Anruf. Der Empfänger des Anrufs kann über das Teams Anrufbenachrichtigungsfenster nur über Audio oder Video antworten.

> [!NOTE]
> Dieser Deeplink kann nicht zum Aufrufen einer Besprechung verwendet werden.

### <a name="generate-a-deep-link-to-a-call"></a>Generieren eines Deeplinks zu einem Anruf

| Deep-Link | Format | Beispiel |
|-----------|--------|---------|
| Tätigen eines Audioanrufs | https://teams.microsoft.com/l/call/0/0?users=&lt;user1&gt;,&lt;user2&gt; | https://teams.microsoft.com/l/call/0/0?users=joe@contoso.com |
| Tätigen eines Audio- und Videoanrufs | https://teams.microsoft.com/l/call/0/0?users=&lt;user1&gt;,&lt;user2&gt;&withVideo=true | https://teams.microsoft.com/l/call/0/0?users=joe@contoso.com&withVideo=true |
|Tätigen eines Audio- und Videoanrufs mit einer optionalen Parameterquelle | https://teams.microsoft.com/l/call/0/0?users=&lt;user1&gt;,&lt;user2&gt;&withVideo=true&source=demoApp | https://teams.microsoft.com/l/call/0/0?users=joe@contoso.com&withVideo=true&source=demoApp |  
| Tätigen eines Audio- und Videoanrufs an eine Kombination aus VoIP- und PSTN-Benutzern | https://teams.microsoft.com/l/call/0/0?users=&lt;user1&gt;,4:&lt;phonenumber&gt; | https://teams.microsoft.com/l/call/0/0?users=joe@contoso.com,4:9876543210 |
  
Nachfolgend sind die Abfrageparameter aufgeführt:
* `users`: Die durch Kommas getrennte Liste der Benutzer-IDs, die die Teilnehmer des Anrufs darstellen. Derzeit unterstützt das Benutzer-ID-Feld die Azure AD UserPrincipalName, in der Regel eine E-Mail-Adresse. Bei einem PSTN-Anruf unterstützt es eine pstn mri 4:&lt;phonenumber&gt;.
* `withVideo`: Dies ist ein optionaler Parameter, den Sie für einen Videoanruf verwenden können. Durch Festlegen dieses Parameters wird nur die Kamera des Anrufers aktiviert. Der Empfänger des Anrufs hat die Möglichkeit, Audio- oder Audio- und Videoanrufe über das Teams Anrufbenachrichtigungsfenster entgegen zu nehmen. 
* `Source`: Dies ist ein optionaler Parameter, der über die Deeplink-Quelle informiert.

## <a name="code-sample"></a>Codebeispiel

| Beispielname | Beschreibung | C# |Node.js|
|-------------|-------------|------|----|
|Unterentitäts-ID für die Deeplink-Nutzung  |Microsoft Teams Beispiel-App zum Demonstrieren einer Deeplink-Verknüpfung vom Bot-Chat zu der Registerkarte, die die Unterentitäts-ID verwendet.|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-deeplink/csharp)|[Anzeigen](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-deeplink/nodejs)|

## <a name="see-also"></a>Siehe auch

* [Integrieren von Web-Apps](~/samples/integrate-web-apps-overview.md)
* [Moodle LMS](~/resources/moodleinstructions.md)
