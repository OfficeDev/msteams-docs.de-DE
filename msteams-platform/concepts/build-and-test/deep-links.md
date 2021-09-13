---
title: Erstellen von Deep-Links
description: Beschreibt Deep-Links und deren Verwendung in Ihren Apps
ms.topic: how-to
ms.localizationpriority: medium
keywords: DeepLink für Teams
ms.openlocfilehash: e61f926e36d379cb6a69816922cca7a8f3a3d17f
ms.sourcegitcommit: fc9f906ea1316028d85b41959980b81f2c23ef2f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2021
ms.locfileid: "59156709"
---
# <a name="create-deep-links"></a>Erstellen von Deep-Links 

Sie können Links zu Informationen und Features in Teams erstellen. Die folgenden Szenarien sind hilfreich, wenn Sie Deep-Links erstellen:

* Navigieren des Benutzers zum Inhalt auf einer der Registerkarten Ihrer App. Ihre App kann beispielsweise über einen Bot verfügen, der Nachrichten sendet, die den Benutzer über eine wichtige Aktivität benachrichtigen. Wenn der Benutzer auf die Benachrichtigung tippt, navigiert der Deep-Link zur Registerkarte, sodass der Benutzer weitere Details zu der Aktivität anzeigen kann.
* Ihre App automatisiert oder vereinfacht bestimmte Benutzeraufgaben, z. B. das Erstellen eines Chats oder das Planen einer Besprechung, indem die Deep-Links vorab mit den erforderlichen Parametern aufgefüllt werden. Dies verhindert, dass Benutzer manuell Informationen eingeben müssen.

> [!NOTE]
>
> Ein Deeplink startet den Browser zuerst, bevor zu Inhalten navigiert wird. Das Verhalten von Deep-Links auf Teams Entitäten lautet wie folgt:
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
> ✔ Textnachrichten-Hyperlinkmarkdown: Navigiert direkt zur Deeplink-URL.  
> ✔ In allgemeine Chatunterhaltung eingefügte Link: Navigiert direkt zur Deeplink-URL.

## <a name="deep-linking-to-your-tab"></a>Deep-Verknüpfung zu Ihrer Registerkarte

Sie können Deep-Links zu Entitäten in Teams erstellen. Dies wird verwendet, um Links zu erstellen, die zu Inhalten und Informationen auf Ihrer Registerkarte navigieren. Wenn Ihre Registerkarte beispielsweise eine Aufgabenliste enthält, können Teammitglieder Links zu einzelnen Aufgaben erstellen und freigeben. Wenn Sie den Link auswählen, navigiert er zu Ihrer Registerkarte, die sich auf das jeweilige Element konzentriert. Um dies zu implementieren, fügen Sie jedem Element eine **Kopierlinkaktion** hinzu, unabhängig davon, welche Art und Weise ihrer Benutzeroberfläche am besten entspricht. Wenn der Benutzer diese Aktion ausführt, rufen Sie `shareDeepLink()` auf, ein Dialogfeld mit einem Link anzuzeigen, den der Benutzer in die Zwischenablage kopieren kann. Wenn Sie diesen Aufruf ausführen, übergeben Sie auch eine ID für Ihr Element, die Sie wieder im [Kontext](~/tabs/how-to/access-teams-context.md) erhalten, wenn dem Link gefolgt wird und Ihre Registerkarte neu geladen wird.

Alternativ können Sie deep-Links auch programmgesteuert mithilfe des später in diesem Thema angegebenen Formats generieren. Sie können Deep-Links in [Bot-](~/bots/what-are-bots.md) und [Connector-Nachrichten](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md) verwenden, die Benutzer über Änderungen an Ihrer Registerkarte oder an darin enthaltenen Elementen informieren.

> [!NOTE]
> Dieser Deep-Link unterscheidet sich von den Links, die vom Menüelement **"Link zum Tab kopieren"** bereitgestellt werden. Dadurch wird lediglich ein Deep-Link generiert, der auf diese Registerkarte verweist.

>[!NOTE]
> Derzeit funktioniert shareDeepLink nicht auf mobilen Plattformen.

### <a name="show-a-deep-link-to-an-item-within-your-tab"></a>Anzeigen eines Deep-Links zu einem Element auf Ihrer Registerkarte

Rufen Sie auf, um ein Dialogfeld anzuzeigen, das einen Deep-Link zu einem Element auf der Registerkarte `microsoftTeams.shareDeepLink({ subEntityId: <subEntityId>, subEntityLabel: <subEntityLabel>, subEntityWebUrl: <subEntityWebUrl> })` enthält.

Geben Sie die folgenden Felder an:

* `subEntityId`: Ein eindeutiger Bezeichner für das Element auf Ihrer Registerkarte, mit dem Sie eine Deep-Verknüpfung erstellen.
* `subEntityLabel`: Eine Beschriftung für das Element, das zum Anzeigen des Deep-Links verwendet werden soll.
* `subEntityWebUrl`: Ein optionales Feld mit einer Fallback-URL, das verwendet werden soll, wenn der Client das Rendern der Registerkarte nicht unterstützt.

### <a name="generate-a-deep-link-to-your-tab"></a>Generieren eines Deep-Links zu Ihrer Registerkarte

> [!NOTE]
> Persönliche Registerkarten haben einen `personal` Bereich, während Kanal- und Gruppenregisterkarten oder `team` Bereiche `group` verwenden. Die Syntax der beiden Registerkartentypen unterscheidet sich geringfügig, da nur der konfigurierbaren Registerkarte eine `channel` Eigenschaft zugeordnet ist, die dem Kontextobjekt zugeordnet ist. Weitere Informationen zu Registerkartenbereichen finden Sie in der [Manifestreferenz.](~/resources/schema/manifest-schema.md)

> [!NOTE]
> Deep-Links funktionieren nur ordnungsgemäß, wenn die Registerkarte mithilfe der v0.4- oder höher-Bibliothek konfiguriert wurde und daher eine Entitäts-ID vorhanden ist. Deep links to tabs without entity IDs still navigate to the tab but cannot provide the sub entity ID to the tab.

Verwenden Sie das folgende Format für einen Deep-Link, den Sie in einer Bot-, Connector- oder Messaging-Erweiterungskarte verwenden können:

`https://teams.microsoft.com/l/entity/<appId>/<entityId>?webUrl=<entityWebUrl>&label=<entityLabel>&context=<context>`

> [!NOTE]
> Wenn der Bot eine Nachricht `TextBlock` mit einem Deep-Link sendet, wird eine neue Browserregisterkarte geöffnet, wenn der Benutzer den Link auswählt. Dies geschieht in Chrome und in der Microsoft Teams Desktop-App, die beide unter Linux ausgeführt werden.
> Wenn der Bot dieselbe Deep-Link-URL in eine `Action.OpenUrl` sendet, wird die Registerkarte Teams in der aktuellen Browserregisterkarte geöffnet, wenn der Benutzer den Link auswählt. Eine neue Browserregisterkarte wird nicht geöffnet.

Die Abfrageparameter sind:

| Parametername | Beschreibung | Beispiel |
|:------------|:--------------|:---------------------|
| `appId`&emsp; | Die ID aus Ihrem Manifest. |fe4a8eba-2a31-4737-8e33-e5fae6fee194|
| `entityId`&emsp; | Die ID für das Element auf der Registerkarte, die Sie beim [Konfigurieren der Registerkarte](~/tabs/how-to/create-tab-pages/configuration-page.md)angegeben haben.|Tasklist123|
| `entityWebUrl` Oder `subEntityWebUrl`&emsp; | Ein optionales Feld mit einer Fallback-URL, das verwendet werden soll, wenn der Client das Rendern der Registerkarte nicht unterstützt. | `https://tasklist.example.com/123` oder `https://tasklist.example.com/list123/task456` |
| `entityLabel` Oder `subEntityLabel`&emsp; | Eine Beschriftung für das Element auf Ihrer Registerkarte, die beim Anzeigen des Deep-Links verwendet werden soll. | Aufgabenliste 123 oder "Aufgabe 456" |
| `context`&emsp; </br></br>* `subEntityId`&emsp;</br></br> * `channelId`&emsp;| Ein JSON-Objekt, das die folgenden Felder enthält:</br></br> * Eine ID für das Element auf der Registerkarte. </br></br> * Die Microsoft Teams Kanal-ID, die im [Registerkartenkontext](~/tabs/how-to/access-teams-context.md)verfügbar ist. | 
| `subEntityId`&emsp; | Eine ID für das Element auf der Registerkarte. |Task456 |
| `channelId`&emsp; | Die Microsoft Teams Kanal-ID, die im [Registerkartenkontext](~/tabs/how-to/access-teams-context.md)verfügbar ist. Diese Eigenschaft ist nur in konfigurierbaren Registerkarten mit einem Bereich von **Team** verfügbar. Es ist nicht in statischen Registerkarten verfügbar, die einen **Persönlichen** Bereich haben.| 19:cbe3683f25094106b826c9cada3afbe0@thread.skype |

Beispiele:

* Link zu einer konfigurierbaren Registerkarte selbst: `https://teams.microsoft.com/l/entity/fe4a8eba-2a31-4737-8e33-e5fae6fee194/tasklist123?webUrl=https://tasklist.example.com/123&label=Task List 123&context={"channelId": "19:cbe3683f25094106b826c9cada3afbe0@thread.skype"}`
* Link zu einem Aufgabenelement auf der konfigurierbaren Registerkarte: `https://teams.microsoft.com/l/entity/fe4a8eba-2a31-4737-8e33-e5fae6fee194/tasklist123?webUrl=https://tasklist.example.com/123/456&label=Task 456&context={"subEntityId": "task456","channelId": "19:cbe3683f25094106b826c9cada3afbe0@thread.skype"}`
* Link zu einer statischen Registerkarte selbst: `https://teams.microsoft.com/l/entity/fe4a8eba-2a31-4737-8e33-e5fae6fee194/tasklist123?webUrl=https://tasklist.example.com/123&label=Task List 123`
* Link zu einem Aufgabenelement auf der statischen Registerkarte: `https://teams.microsoft.com/l/entity/fe4a8eba-2a31-4737-8e33-e5fae6fee194/tasklist123?webUrl=https://tasklist.example.com/123/456&label=Task 456&context={"subEntityId": "task456"}`

> [!IMPORTANT]
> Stellen Sie sicher, dass alle Abfrageparameter ordnungsgemäß URI-codiert sind. Sie müssen den vorangehenden Beispielen mithilfe des letzten Beispiels folgen:

> ```javascript
> var encodedWebUrl = encodeURI('https://tasklist.example.com/123/456&label=Task 456');
> var encodedContext = encodeURI('{"subEntityId": "task456"}');
> var taskItemUrl = 'https://teams.microsoft.com/l/entity/fe4a8eba-2a31-4737-8e33-e5fae6fee194/tasklist123?webUrl=' + encodedWebUrl + '&context=' + encodedContext;
> ```

### <a name="consume-a-deep-link-from-a-tab"></a>Verwenden eines Deep-Links von einer Registerkarte

Beim Navigieren zu einem Deep-Link navigiert Microsoft Teams einfach zur Registerkarte und stellt einen Mechanismus über die Microsoft Teams JavaScript-Bibliothek bereit, um die Unterentitäts-ID abzurufen, falls vorhanden.

Der [`microsoftTeams.getContext`](/javascript/api/@microsoft/teams-js#getcontext--context--context-----void-) Aufruf gibt einen Kontext zurück, der das Feld `subEntityId` enthält, wenn die Registerkarte durch einen Deep-Link navigiert wird.

## <a name="deep-linking-from-your-tab"></a>Deep-Verknüpfung von Ihrer Registerkarte

Sie können Deeplinks zu Inhalten in Teams von Ihrer Registerkarte aus ausführen. Dies ist nützlich, wenn Ihre Registerkarte mit anderen Inhalten in Teams verknüpft werden muss, z. B. mit einem Kanal, einer Nachricht, einer anderen Registerkarte oder sogar zum Öffnen eines Planungsdialogfelds. Um einen Deeplink von Ihrer Registerkarte aus auszulösen, sollten Sie Folgendes aufrufen:

```Javascript
microsoftTeams.executeDeepLink(/*deepLink*/);
```

Dieser Aufruf navigiert Sie zur richtigen URL oder löst eine Clientaktion aus, z. B. das Öffnen eines Planungs- oder App-Installationsdialogfelds. Sehen Sie sich das folgende Beispiel an:

```Javascript
// Open a scheduling dialog from your tab
microsoftTeams.executeDeepLink("https://teams.microsoft.com/l/meeting/new?subject=test%20subject&attendees=joe@contoso.com,bob@contoso.com&startTime=10%2F24%2F2018%2010%3A30%3A00&endTime=10%2F24%2F2018%2010%3A30%3A00&content=test%3Acontent");

// Open an app install dialog from your tab
microsoftTeams.executeDeepLink("https://teams.microsoft.com/l/app/f46ad259-0fe5-4f12-872d-c737b174bcb4");
```

## <a name="deep-linking-to-a-chat"></a>Deep-Links zu einem Chat

Sie können Deep-Links zu privaten Chats zwischen Benutzern erstellen, indem Sie die Teilnehmergruppe angeben. Wenn kein Chat mit den angegebenen Teilnehmern vorhanden ist, navigiert der Link den Benutzer zu einem leeren neuen Chat. Neue Chats werden im Entwurfsstatus erstellt, bis der Benutzer die erste Nachricht sendet. Andernfalls können Sie den Namen des Chats angeben, falls er noch nicht vorhanden ist, zusammen mit Text, der in das Feld zum Verfassen des Benutzers eingefügt werden soll. Sie können sich dieses Feature als eine Verknüpfung vorstellen, mit der der Benutzer manuell zu dem Chat navigieren oder diesen erstellen und dann die Nachricht eingeben kann.

Wenn Sie beispielsweise ein Office 365 Benutzerprofil von Ihrem Bot als Karte zurückgeben, kann dieser Deep-Link es dem Benutzer ermöglichen, einfach mit dieser Person zu chatten.

### <a name="generate-a-deep-link-to-a-chat"></a>Generieren eines Deep-Links zu einem Chat

Verwenden Sie dieses Format für einen Deep-Link, den Sie in einer Bot-, Connector- oder Messaging-Erweiterungskarte verwenden können:

`https://teams.microsoft.com/l/chat/0/0?users=<user1>,<user2>,...&topicName=<chat name>&message=<precanned text>`

Beispiel: `https://teams.microsoft.com/l/chat/0/0?users=joe@contoso.com,bob@contoso.com&topicName=Prep%20For%20Meeting%20Tomorrow&message=Hi%20folks%2C%20kicking%20off%20a%20chat%20about%20our%20meeting%20tomorrow`

Die Abfrageparameter sind:

* `users`: Die durch Kommas getrennte Liste der Benutzer-IDs, die die Teilnehmer des Chats darstellen. Der Benutzer, der die Aktion ausführt, ist immer als Teilnehmer enthalten. Derzeit unterstützt das Feld "Benutzer-ID" den Azure AD UserPrincipalName, z. B. nur eine E-Mail-Adresse.
* `topicName`: Ein optionales Feld für den Anzeigenamen des Chats, im Falle eines Chats mit 3 oder mehr Benutzern. Wenn dieses Feld nicht angegeben ist, basiert der Anzeigename des Chats auf den Namen der Teilnehmer.
* `message`: Ein optionales Feld für den Nachrichtentext, den Sie in das Feld zum Verfassen des aktuellen Benutzers einfügen möchten, während sich der Chat im Entwurfszustand befindet.

Um diesen Deep-Link mit Ihrem Bot zu verwenden, geben Sie dies als URL-Ziel in der Schaltfläche Ihrer Karte an, oder tippen Sie über den Aktionstyp auf die `openUrl` Aktion.

## <a name="generate-deep-links-to-file-in-channel"></a>Generieren von Deep-Links zu Dateien im Kanal

Das folgende Deep Link-Format kann in einer Bot-, Connector- oder Messaging-Erweiterungskarte verwendet werden:

`https://teams.microsoft.com/l/file/5E0154FC-F2B4-4DA5-8CDA-F096E72C0A80?tenantId=<tenantid>&fileType=<filetype>&objectURL=<objectURL>&baseUrl=<baseURL>&serviceName=<Name>&threadId=<threadid>&groupId=<groupId>`

Die Abfrageparameter sind:

* `tenantId`: Tenant ID example, 0d9b645f-597b-41f0-a2a3-ef103fbd91bb
* `fileType`: Unterstützter Dateityp, z. B. docx, pptx, xlsx und pdf
* `objectUrl`: Objekt-URL der Datei. Das Format ist `https://{tenantName}.sharepoint.com/sites/{TeamName}/SharedDocuments/{ChannelName}/FileName.ext`. Beispiel: `https://microsoft.sharepoint.com/teams/(filepath)`
* `baseUrl`: Basis-URL der Datei. Das Format ist `https://{tenantName}.sharepoint.com/sites/{TeamName}`. Beispiel: `https://microsoft.sharepoint.com/teams`
* `serviceName`: Name des Diensts, App-ID. Beispielsweise Teams.
* `threadId`: Die threadId ist die Team-ID des Teams, in dem die Datei gespeichert ist. Sie ist optional und kann nicht für Dateien festgelegt werden, die im ordner OneDrive eines Benutzers gespeichert sind. threadId – 19:f8fbfc4d89e24ef5b3b8692538cebeb7@thread.skype
* `groupId`: Gruppen-ID der Datei, ae063b79-5315-4ddb-ba70-27328ba6c31e 

> [!NOTE]
> Sie können die URL aus dem Kanal anzeigen `threadId` und `groupId` in dieser anzeigen.  

Das folgende Deep-Link-Format wird in einer Bot-, Connector- oder Messaging-Erweiterungskarte verwendet: `https://teams.microsoft.com/l/file/5E0154FC-F2B4-4DA5-8CDA-F096E72C0A80?tenantId=<tenantid>&fileType=<filetype>&objectURL=<objectURL>&baseUrl=<baseURL>&serviceName=<Name>&threadId=<threadid>&groupId=<groupId>`

Das folgende Beispielformat zeigt den Deeplink zu Dateien:

`https://teams.microsoft.com/l/file/5E0154FC-F2B4-4DA5-8CDA-F096E72C0A80 ?tenantId=0d9b645f-597b-41f0-a2a3-ef103fbd91bb&fileType=pptx&objectUrl=https%3A%2F%2Fmicrosoft.sharepoint.com%2Fteams%2FActionPlatform%2FShared%20Documents%2FFC7-%20Bot%20and%20Action%20Infra%2FKaizala%20Actions%20in%20Adaptive%20Cards%20-%20Deck.pptx&baseUrl=https%3A%2F%2Fmicrosoft.sharepoint.com%2Fteams%2FActionPlatform&serviceName=teams&threadId=19:f8fbfc4d89e24ef5b3b8692538cebeb7@thread.skype&groupId=ae063b79-5315-4ddb-ba70-27328ba6c31e`

### <a name="serialization-of-this-object"></a>Serialisierung dieses Objekts:
```
{
tenantId: "0d9b645f-597b-41f0-a2a3-ef103fbd91bb",
filetype: = "pptx",
objectUrl: "https://microsoft.sharepoint.com/teams/ActionPlatform/Shared Documents/FC7- Bot and Action Infra/Kaizala Actions in Adaptive Cards - Deck.pptx",
baseUrl: "https://microsoft.sharepoint.com/teams/ActionPlatform",
serviceName: "teams",
threadId: = "19:f8fbfc4d89e24ef5b3b8692538cebeb7@thread.skype",
groupId: "ae063b79-5315-4ddb-ba70-27328ba6c31e"
}
```

## <a name="deep-linking-to-an-app"></a>Deep-Links zu einer App

Erstellen Sie Deeplinks für die App, nachdem die App im Teams Store aufgeführt wurde. Um einen Link zum Starten Teams zu erstellen, fügen Sie die folgende URL an Ihre App-ID an: `https://teams.microsoft.com/l/app/<your-app-id>` . Ein Dialogfeld wird angezeigt, um die App zu installieren. 
  
## <a name="deep-linking-for-sharepoint-framework-tabs"></a>Deep-Verknüpfung für SharePoint-Framework Registerkarten

Das folgende Deep Link-Format kann in einer Bot-, Connector- oder Messaging-Erweiterungskarte verwendet werden: `https://teams.microsoft.com/l/entity/<AppId>/<EntityId>?webUrl=<entityWebUrl>/<EntityName>`

> [!NOTE]
> Wenn ein Bot eine TextBlock-Nachricht mit einem Deep-Link sendet, wird eine neue Browserregisterkarte geöffnet, wenn Benutzer den Link auswählen. Dies geschieht in Chrome und Microsoft Teams Desktop-App, die unter Linux ausgeführt wird.
> Wenn der Bot dieselbe Deep-Link-URL an eine `Action.OpenUrl` sendet, wird die Registerkarte Teams im aktuellen Browser geöffnet, wenn der Benutzer den Link auswählt. Es wird keine neue Browserregisterkarte geöffnet.

Die Abfrageparameter sind:

* `appID`: Ihre Manifest-ID **fe4a8eba-2a31-4737-8e33-e5fae6fee194**.

* `entityID`: Die Element-ID, die Sie beim [Konfigurieren der Registerkarte](~/tabs/how-to/create-tab-pages/configuration-page.md)angegeben haben. Beispiel: **tasklist123**.
* `entityWebUrl`: Ein optionales Feld mit einer Fallback-URL, das verwendet werden soll, wenn der Client das Rendern der Registerkarte - `https://tasklist.example.com/123` oder `https://tasklist.example.com/list123/task456` .
* `entityName`: Eine Beschriftung für das Element auf Ihrer Registerkarte, das beim Anzeigen des Deep-Links, Task List 123 oder Task 456, verwendet werden soll.

Beispiel: https://teams.microsoft.com/l/entity/fe4a8eba-2a31-4737-8e33-e5fae6fee194/tasklist123?webUrl=https://tasklist.example.com/123&TaskList

## <a name="deep-linking-to-the-scheduling-dialog"></a>Deep linking to the scheduling dialog

> [!NOTE]
> Dieses Feature befindet sich derzeit in der Entwicklervorschau.

Sie können Deep-Links zum Teams integrierten Planungsdialogfeld erstellen. Dies ist besonders nützlich, wenn Ihre App dem Benutzer beim Ausführen von Kalender- oder Planungsaufgaben hilft.

### <a name="generate-a-deep-link-to-the-scheduling-dialog"></a>Generieren eines Deep-Links zum Planungsdialogfeld

Verwenden Sie das folgende Format für einen Deep-Link, den Sie in einer Bot-, Connector- oder Messaging-Erweiterungskarte verwenden können: `https://teams.microsoft.com/l/meeting/new?subject=<meeting subject>&startTime=<date>&endTime=<date>&content=<content>&attendees=<user1>,<user2>,<user3>,...`

Beispiel: `https://teams.microsoft.com/l/meeting/new?subject=test%20subject&attendees=joe@contoso.com,bob@contoso.com&startTime=10%2F24%2F2018%2010%3A30%3A00&endTime=10%2F24%2F2018%2010%3A30%3A00&content=test%3Acontent`

Die Abfrageparameter sind:

* `attendees`: Die optionale durch Kommas getrennte Liste der Benutzer-IDs, die die Teilnehmer der Besprechung darstellen. Der Benutzer, der die Aktion ausführt, ist der Besprechungsorganisator. Das Feld "Benutzer-ID" unterstützt derzeit nur den Azure AD UserPrincipalName, in der Regel eine E-Mail-Adresse.
* `startTime`: Die optionale Startzeit des Ereignisses. Dies sollte im [langen ISO 8601-Format](https://en.wikipedia.org/wiki/ISO_8601)vorliegen, z. B. *2018-03-12T23:55:25+02:00*.
* `endTime`: Die optionale Endzeit des Ereignisses, auch im ISO 8601-Format.
* `subject`: Ein optionales Feld für den Besprechungsbetreff.
* `content`: Ein optionales Feld für das Besprechungsdetailsefeld.

> [!NOTE]
> Derzeit wird die Angabe des Speicherorts nicht unterstützt. Sie müssen den UTC-Offset angeben, d. h. Zeitzonen beim Generieren der Start- und Endzeiten.

Um diesen Deep-Link mit Ihrem Bot zu verwenden, können Sie dies als URL-Ziel in der Schaltfläche Ihrer Karte angeben oder über den Aktionstyp auf die Aktion `openUrl` tippen.

## <a name="deep-linking-to-an-audio-or-audio-video-call"></a>Deep-Links zu einem Audio- oder Audiovideoanruf

Sie können Deep-Links erstellen, um nur Audio- oder Audiovideoanrufe an einen einzelnen Benutzer oder eine Gruppe von Benutzern aufzurufen, indem Sie den Anruftyp als *Audio* oder *Av* und die Teilnehmer angeben. Nachdem der Deep-Link aufgerufen wurde und vor dem Tätigen des Anrufs fordert Teams Desktopclient eine Bestätigung für den Anruf an. Im Falle eines Gruppenanrufs können Sie eine Gruppe von VoIP-Benutzern und eine Gruppe von PSTN-Benutzern im selben Deeplink-Aufruf aufrufen. 

Bei einem Videoanruf fordert der Client die Bestätigung an und aktiviert das Video des Anrufers für den Anrufer. Der Empfänger des Anrufs hat die Wahl, nur über Audio oder Audio und Video über das Teams Anrufbenachrichtigungsfenster zu antworten.

> [!NOTE]
> Dieser Deeplink kann nicht zum Aufrufen einer Besprechung verwendet werden.

### <a name="generate-a-deep-link-to-a-call"></a>Generieren eines Deep-Links zu einem Anruf

| Deep-Link | Format | Beispiel |
|-----------|--------|---------|
| Tätigen eines Audioanrufs | https://teams.microsoft.com/l/call/0/0?users=&lt;user1 &gt; , &lt; user2&gt; | https://teams.microsoft.com/l/call/0/0?users=joe@contoso.com |
| Tätigen eines Audio- und Videoanrufs | https://teams.microsoft.com/l/call/0/0?users=&lt;user1 &gt; , &lt; user2&&gt; withVideo=true | https://teams.microsoft.com/l/call/0/0?users=joe@contoso.com&withVideo=true |
|Tätigen eines Audio- und Videoanrufs mit einer optionalen Parameterquelle | https://teams.microsoft.com/l/call/0/0?users=&lt;user1 &gt; , &lt; user2&&gt; withVideo=true&source=demoApp | https://teams.microsoft.com/l/call/0/0?users=joe@contoso.com&withVideo=true&source=demoApp |  
| Tätigen eines Audio- und Videoanrufs für eine Kombination aus VoIP- und PSTN-Benutzern | https://teams.microsoft.com/l/call/0/0?users=&lt;user1 &gt; ,4: &lt; Phonenumber&gt; | https://teams.microsoft.com/l/call/0/0?users=joe@contoso.com,4:9876543210 |
  
Es folgen die Abfrageparameter:
* `users`: Die durch Kommas getrennte Liste der Benutzer-IDs, die die Teilnehmer des Anrufs darstellen. Derzeit unterstützt das Benutzer-ID-Feld den Azure AD UserPrincipalName, in der Regel eine E-Mail-Adresse, oder im Falle eines PSTN-Anrufs unterstützt es eine pstn mri 4: &lt; &gt; Telefonnummer.
* `withVideo`: Dies ist ein optionaler Parameter, den Sie für einen Videoanruf verwenden können. Durch Festlegen dieses Parameters wird nur die Kamera des Anrufers aktiviert. Der Empfänger des Anrufs hat die Möglichkeit, audio- oder audio- und videoanrufe über das Teams Anrufbenachrichtigungsfenster zu beantworten. 
* `Source`: Dies ist ein optionaler Parameter, der über die Quelle des Deeplinks informiert.

## <a name="code-sample"></a>Codebeispiel

| Beispielname | Beschreibung | C # |Node.js|
|-------------|-------------|------|----|
|Deep Link consuming Subentity ID  |Microsoft Teams Beispiel-App zum Demonstrieren von Deeplink vom Bot-Chat zu registerkartenverwendenden Subentity-ID.|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-deeplink/csharp)|[Anzeigen](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-deeplink/nodejs)|

## <a name="see-also"></a>Siehe auch

[Integrieren von Web-Apps](~/samples/integrate-web-apps-overview.md)

