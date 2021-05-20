---
title: Erstellen von Deep-Links
description: Beschreibt tiefe Links und deren Verwendung in Ihren Apps
ms.topic: how-to
localization_priority: Normal
keywords: Teams Deep Link Deeplink
ms.openlocfilehash: 837d180b06f69b9be49d898c62b9ab8ee64d51d0
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566054"
---
# <a name="create-deep-links"></a>Erstellen von Deep-Links 

Sie können Links zu Informationen und Features innerhalb Teams erstellen. Die Szenarien, in denen das Erstellen von Deep-Links nützlich ist, sind wie folgt:

* Navigieren des Benutzers zum Inhalt innerhalb einer der Registerkarten Ihrer App. Ihre App kann beispielsweise über einen Bot verfügen, der Nachrichten sendet, die den Benutzer über eine wichtige Aktivität benachrichtigen. Wenn der Benutzer auf die Benachrichtigung tippt, navigiert der Deep Link zur Registerkarte, sodass der Benutzer weitere Details zur Aktivität anzeigen kann.
* Ihre App automatisiert oder vereinfacht bestimmte Benutzeraufgaben, z. B. das Erstellen eines Chats oder das Planen einer Besprechung, indem die Deep Links mit erforderlichen Parametern vorab aufgepopt werden. Dadurch wird vermieden, dass Benutzer Informationen manuell eingeben müssen.

> [!NOTE]
>
> Ein Deeplink startet den Browser zuerst, bevor er zu Inhalten navigiert. Das Verhalten tiefer Verbindungen auf Teams Entitäten ist wie folgt:
>
> **Tab**:  
> ✔ Navigiert direkt zur deeplink-URL.
>
> **Bot**:  
> ✔ Deeplink im Kartentext: Wird zuerst im Browser geöffnet.  
> ✔ Deeplink zur OpenURL-Aktion in adaptiver Karte hinzugefügt: Navigiert direkt zur Deeplink-URL.  
> ✔ Hyperlink-Markdowntext auf der Karte: Wird zuerst im Browser geöffnet.  
>
> **Chat**:  
> ✔ Textnachrichten-Hyperlink-Markdown: Navigiert direkt zur Deeplink-URL.  
> ✔ Link in der allgemeinen Chat-Unterhaltung eingefügt: Navigiert direkt zu deeplink URL.

## <a name="deep-linking-to-your-tab"></a>Tiefe Verknüpfung mit Ihrer Registerkarte

Sie können tiefe Verknüpfungen zu Entitäten in Teams erstellen. Dies wird verwendet, um Links zu erstellen, die zu Inhalten und Informationen auf Ihrer Registerkarte navigieren. Wenn Ihre Registerkarte beispielsweise eine Aufgabenliste enthält, können Teammitglieder Verknüpfungen zu einzelnen Aufgaben erstellen und freigeben. Wenn Sie den Link auswählen, navigiert er zu Ihrer Registerkarte, die sich auf das jeweilige Element konzentriert. Um dies zu implementieren, fügen Sie jedem Element eine **Kopierverknüpfungsaktion** hinzu, auf welche Weise auch immer die Benutzeroberfläche am besten passt. Wenn der Benutzer diese Aktion ausführt, rufen Sie an, `shareDeepLink()` um ein Dialogfeld anzuzeigen, das einen Link enthält, den der Benutzer in die Zwischenablage kopieren kann. Wenn Sie diesen Aufruf tätigen, übergeben Sie auch eine ID für Ihr Element, die Sie im [Kontext](~/tabs/how-to/access-teams-context.md) zurückerhalten, wenn der Link gefolgt wird und Ihre Registerkarte neu geladen wird.

Alternativ können Sie Deep Links auch programmgesteuert generieren, indem Sie das später in diesem Thema angegebene Format verwenden. Sie können Deep Links in [Bot-](~/bots/what-are-bots.md) und [Connector-Nachrichten](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md) verwenden, die Benutzer über Änderungen an Ihrer Registerkarte oder an Elementen darin informieren.

> [!NOTE]
> Dieser Deep-Link unterscheidet sich von den Links, die durch den **Link Kopieren zum Menüelement** der Registerkarte bereitgestellt werden, der nur einen tiefen Link generiert, der auf diese Registerkarte verweist.

>[!NOTE]
> Derzeit funktioniert shareDeepLink nicht auf mobilen Plattformen.

### <a name="show-a-deep-link-to-an-item-within-your-tab"></a>Anzeigen eines tiefen Links zu einem Element auf Ihrer Registerkarte

Rufen Sie an, um ein Dialogfeld anzuzeigen, das einen tiefen Link zu einem Element auf Ihrer Registerkarte `microsoftTeams.shareDeepLink({ subEntityId: <subEntityId>, subEntityLabel: <subEntityLabel>, subEntityWebUrl: <subEntityWebUrl> })` enthält.

Geben Sie die folgenden Felder an:

* `subEntityId`: Ein eindeutiger Bezeichner für das Element auf Ihrer Registerkarte, mit dem Sie eine tiefe Verknüpfung herstellen.
* `subEntityLabel`: Eine Bezeichnung für das Element, das zum Anzeigen des Tiefenverknüpfungs verwendet werden soll.
* `subEntityWebUrl`: Ein optionales Feld mit einer Fallback-URL, das verwendet werden soll, wenn der Client das Rendern der Registerkarte nicht unterstützt.

### <a name="generate-a-deep-link-to-your-tab"></a>Generieren eines tiefen Links zu Ihrer Registerkarte

> [!NOTE]
> Persönliche Registerkarten haben einen `personal` Bereich, während Kanal- und Gruppenregisterkarten `team` oder Bereiche `group` verwenden. Die beiden Registerkartentypen haben eine etwas andere Syntax, da nur die konfigurierbare Registerkarte über eine `channel` Eigenschaft verfügt, die ihrem Kontextobjekt zugeordnet ist. Weitere Informationen zu Registerkartenbereichen finden Sie in der [Manifestreferenz.](~/resources/schema/manifest-schema.md)

> [!NOTE]
> Deep-Links funktionieren nur dann ordnungsgemäß, wenn die Registerkarte mit der Bibliothek v0.4 oder höher konfiguriert wurde und diese eine Entitäts-ID hat. Deep-Links zu Registerkarten ohne Entitäts-IDs navigieren immer noch zur Registerkarte, können jedoch die Unterentitäts-ID nicht für die Registerkarte bereitstellen.

Verwenden Sie das folgende Format für eine Deep Link, die Sie in einer Bot-, Connector- oder Messagingerweiterungskarte verwenden können:

`https://teams.microsoft.com/l/entity/<appId>/<entityId>?webUrl=<entityWebUrl>&label=<entityLabel>&context=<context>`

> [!NOTE]
> Wenn der Bot eine Nachricht sendet, die eine `TextBlock` mit einem tiefen Link enthält, wird eine neue Browser-Registerkarte geöffnet, wenn der Benutzer den Link auswählt. Dies geschieht in Chrome und in der Microsoft Teams Desktop-App, die beide unter Linux ausgeführt werden.
> Wenn der Bot dieselbe Deep Link-URL an eine `Action.OpenUrl` sendet, wird die Registerkarte Teams in der aktuellen Browser-Registerkarte geöffnet, wenn der Benutzer den Link auswählt. Eine neue Browser-Registerkarte wird nicht geöffnet.

Die Abfrageparameter sind:

| Parametername | Beschreibung | Beispiel |
|:------------|:--------------|:---------------------|
| `appId`&emsp; | Die ID aus Ihrem Manifest. |fe4a8eba-2a31-4737-8e33-e5fae6fee194|
| `entityId`&emsp; | Die ID für das Element auf der Registerkarte, die Sie beim [Konfigurieren der Registerkarte](~/tabs/how-to/create-tab-pages/configuration-page.md)angegeben haben.|Aufgabenliste123|
| `entityWebUrl` Oder `subEntityWebUrl`&emsp; | Ein optionales Feld mit einer Fallback-URL, das verwendet werden soll, wenn der Client das Rendern der Registerkarte nicht unterstützt. | https://tasklist.example.com/123 oder https://tasklist.example.com/list123/task456 |
| `entityLabel` Oder `subEntityLabel`&emsp; | Eine Bezeichnung für das Element auf Ihrer Registerkarte, die beim Anzeigen des Tiefenverknüpfungs verwendet werden soll. | Aufgabenliste 123 oder "Aufgabe 456 |
| `context`&emsp; </br></br>* `subEntityId`&emsp;</br></br> * `channelId`&emsp;| Ein JSON-Objekt, das die folgenden Felder enthält:</br></br> * Eine ID für das Element auf der Registerkarte. </br></br> * Die Microsoft Teams Kanal-ID, die im [Tab-Kontext](~/tabs/how-to/access-teams-context.md)verfügbar ist. | 
| `subEntityId`&emsp; | Eine ID für das Element auf der Registerkarte. |Aufgabe456 |
| `channelId`&emsp; | Die Microsoft Teams Kanal-ID, die im [Registerkartenkontext](~/tabs/how-to/access-teams-context.md)verfügbar ist. Diese Eigenschaft ist nur in konfigurierbaren Registerkarten mit einem Teambereich **verfügbar.** Sie ist nicht in statischen Registerkarten verfügbar, die einen persönlichen Bereich **haben.**| 19:cbe3683f25094106b826c9cada3afbe0@thread.skype |

Beispiele:

* Link zu einer konfigurierbaren Registerkarte selbst: `https://teams.microsoft.com/l/entity/fe4a8eba-2a31-4737-8e33-e5fae6fee194/tasklist123?webUrl=https://tasklist.example.com/123&label=Task List 123&context={"channelId": "19:cbe3683f25094106b826c9cada3afbe0@thread.skype"}`
* Link zu einem Aufgabenelement auf der Registerkarte Konfigurierbar: `https://teams.microsoft.com/l/entity/fe4a8eba-2a31-4737-8e33-e5fae6fee194/tasklist123?webUrl=https://tasklist.example.com/123/456&label=Task 456&context={"subEntityId": "task456","channelId": "19:cbe3683f25094106b826c9cada3afbe0@thread.skype"}`
* Link zu einer statischen Registerkarte selbst: `https://teams.microsoft.com/l/entity/fe4a8eba-2a31-4737-8e33-e5fae6fee194/tasklist123?webUrl=https://tasklist.example.com/123&label=Task List 123`
* Verknüpfung mit einem Aufgabenelement auf der statischen Registerkarte: `https://teams.microsoft.com/l/entity/fe4a8eba-2a31-4737-8e33-e5fae6fee194/tasklist123?webUrl=https://tasklist.example.com/123/456&label=Task 456&context={"subEntityId": "task456"}`

> [!IMPORTANT]
> Stellen Sie sicher, dass alle Abfrageparameter ordnungsgemäß URI-codiert sind. Sie müssen den Vorbeispielen anhand des letzten Beispiels folgen:

> ```javascript
> var encodedWebUrl = encodeURI('https://tasklist.example.com/123/456&label=Task 456');
> var encodedContext = encodeURI('{"subEntityId": "task456"}');
> var taskItemUrl = 'https://teams.microsoft.com/l/entity/fe4a8eba-2a31-4737-8e33-e5fae6fee194/tasklist123?webUrl=' + encodedWebUrl + '&context=' + encodedContext;
> ```

### <a name="consume-a-deep-link-from-a-tab"></a>Verwenden eines tiefen Links von einer Registerkarte

Beim Navigieren zu einer Tiefenverknüpfung navigiert Microsoft Teams einfach zur Registerkarte und stellt einen Mechanismus durch die Microsoft Teams JavaScript-Bibliothek bereit, um die Unterentitäts-ID abzurufen, falls vorhanden.

Der [`microsoftTeams.getContext`](/javascript/api/@microsoft/teams-js#getcontext--context--context-----void-) Aufruf gibt einen Kontext zurück, der das Feld `subEntityId` enthält, wenn die Registerkarte durch eine tiefe Verknüpfung navigiert wird.

## <a name="deep-linking-from-your-tab"></a>Tiefe Verknüpfung von Ihrem Tab

Sie können deeplink zu Inhalten in Teams von Ihrer Registerkarte. Dies ist nützlich, wenn Ihre Registerkarte mit anderen Inhalten in Teams verknüpft werden muss, z. B. zu einem Kanal, einer Nachricht, einer anderen Registerkarte oder sogar zum Öffnen eines Planungsdialogfelds. Um einen Deeplink von Ihrer Registerkarte auszulösen, sollten Sie Folgendes aufrufen:

```Javascript
microsoftTeams.executeDeepLink(/*deepLink*/);
```

Dieser Aufruf navigiert Sie zur richtigen URL oder löst eine Clientaktion aus, z. B. das Öffnen eines Planungs- oder App-Installationsdialogfelds. Sehen Sie sich folgendes Beispiel an:

```Javascript
// Open a scheduling dialog from your tab
microsoftTeams.executeDeepLink("https://teams.microsoft.com/l/meeting/new?subject=test%20subject&attendees=joe@contoso.com,bob@contoso.com&startTime=10%2F24%2F2018%2010%3A30%3A00&endTime=10%2F24%2F2018%2010%3A30%3A00&content=test%3Acontent");

// Open an app install dialog from your tab
microsoftTeams.executeDeepLink("https://teams.microsoft.com/l/app/f46ad259-0fe5-4f12-872d-c737b174bcb4");
```

## <a name="deep-linking-to-a-chat"></a>Tiefe Verknüpfung zu einem Chat

Sie können tiefe Links zu privaten Chats zwischen Benutzern erstellen, indem Sie die Gruppe der Teilnehmer angeben. Wenn kein Chat mit den angegebenen Teilnehmern vorhanden ist, navigiert der Link den Benutzer zu einem leeren neuen Chat. Neue Chats werden im Entwurfszustand erstellt, bis der Benutzer die erste Nachricht sendet. Andernfalls können Sie den Namen des Chats angeben, wenn er noch nicht vorhanden ist, zusammen mit Text, der in das Verfassenfeld des Benutzers eingefügt werden soll. Sie können sich diese Funktion als Eine Verknüpfung für den Benutzer vorstellen, der die manuelle Aktion des Navigierens zum Chat oder Erstellen des Chats und anschließenden Eingeben der Nachricht ausführt.

Als Beispiel anwendungsfall, wenn Sie ein Office 365 Benutzerprofil von Ihrem Bot als Karte zurückgeben, kann dieser Deep Link dem Benutzer erlauben, einfach mit dieser Person zu chatten.

### <a name="generate-a-deep-link-to-a-chat"></a>Generieren eines tiefen Links zu einem Chat

Verwenden Sie dieses Format für eine Deep-Link-Verbindung, die Sie in einer Bot-, Connector- oder Messaging-Erweiterungskarte verwenden können:

`https://teams.microsoft.com/l/chat/0/0?users=<user1>,<user2>,...&topicName=<chat name>&message=<precanned text>`

Beispiel: `https://teams.microsoft.com/l/chat/0/0?users=joe@contoso.com,bob@contoso.com&topicName=Prep%20For%20Meeting%20Tomorrow&message=Hi%20folks%2C%20kicking%20off%20a%20chat%20about%20our%20meeting%20tomorrow`

Die Abfrageparameter sind:

* `users`: Die durch Kommas getrennte Liste der Benutzer-IDs, die die Teilnehmer des Chats darstellen. Der Benutzer, der die Aktion ausführt, wird immer als Teilnehmer einbezogen. Derzeit unterstützt das Feld Benutzer-ID den Azure AD UserPrincipalName, z. B. nur eine E-Mail-Adresse.
* `topicName`: Ein optionales Feld für den Anzeigenamen des Chats, im Falle eines Chats mit 3 oder mehr Benutzern. Wenn dieses Feld nicht angegeben ist, basiert der Anzeigename des Chats auf den Namen der Teilnehmer.
* `message`: Ein optionales Feld für den Nachrichtentext, den Sie in das Verfassenfeld des aktuellen Benutzers einfügen möchten, während sich der Chat in einem Entwurfszustand befindet.

Um diese Deep-Link mit Ihrem Bot zu verwenden, geben Sie dies als URL-Ziel in der Schaltfläche Ihrer Karte an oder tippen Sie auf Aktion durch den `openUrl` Aktionstyp.

## <a name="generate-deep-links-to-file-in-channel"></a>Generieren von Deep-Links zu Dateien im Kanal

Das folgende Deep Link-Format kann in einem Bot, Connector oder einer Messaging-Erweiterungskarte verwendet werden:

`https://teams.microsoft.com/l/file/5E0154FC-F2B4-4DA5-8CDA-F096E72C0A80?tenantId=<tenantid>&fileType=<filetype>&objectURL=<objectURL>&baseUrl=<baseURL>&serviceName=<Name>&threadId=<threadid>&groupId=<groupId>`

Die Abfrageparameter sind:

* `tenantId`: Mieter-ID-Beispiel, 0d9b645f-597b-41f0-a2a3-ef103fbd91bb
* `fileType`: Unterstützter Dateityp, z. B. docx, pptx, xlsx und pdf
* `objectUrl`: Objekt-URL der Datei, https://microsoft.sharepoint.com/teams/(filepath)
* `baseUrl`: Basis-URL der Datei, https://microsoft.sharepoint.com/teams
* `serviceName`: Name des Dienstes, App-ID
* `threadId`: Die threadId ist die Team-ID des Teams, in dem die Datei gespeichert ist. Sie ist optional und kann nicht für Dateien festgelegt werden, die im OneDrive Ordner eines Benutzers gespeichert sind. threadId - 19:f8fbfc4d89e24ef5b3b8692538cebeb7@thread.skype
* `groupId`: Gruppen-ID der Datei, ae063b79-5315-4ddb-ba70-27328ba6c31e

Im Folgenden finden Sie das Beispielformat von deeplink zu Dateien:

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
## <a name="deep-linking-for-sharepoint-framework-tabs"></a>Tiefenverknüpfung für SharePoint-Framework Registerkarten

Das folgende Deep-Link-Format kann in einem Bot, Connector oder Messaging-Erweiterungskarte verwendet werden: `https://teams.microsoft.com/l/entity/<AppId>/<EntityId>?webUrl=<entityWebUrl>/<EntityName>`

> [!NOTE]
> Wenn ein Bot eine TextBlock-Nachricht mit einem Deep Link sendet, wird eine neue Browser-Registerkarte geöffnet, wenn Benutzer den Link auswählen. Dies geschieht in Chrome und Microsoft Teams Desktop-App unter Linux ausgeführt.
> Wenn der Bot dieselbe Deep Link-URL an `Action.OpenUrl` sendet, wird die Registerkarte Teams im aktuellen Browser geöffnet, wenn der Benutzer den Link auswählt. Es wird keine neue Browser-Registerkarte geöffnet.

Die Abfrageparameter sind:

* `appID`: Ihre Manifest-ID **fe4a8eba-2a31-4737-8e33-e5fae6fee194**.

* `entityID`: Die Element-ID, die Sie beim [Konfigurieren der Registerkarte](~/tabs/how-to/create-tab-pages/configuration-page.md)angegeben haben. Beispiel: **tasklist123**.
* `entityWebUrl`: Ein optionales Feld mit einer Fallback-URL, das verwendet werden soll, wenn der Client das Rendern der Registerkarte - https://tasklist.example.com/123 oder https://tasklist.example.com/list123/task456 .
* `entityName`: Eine Bezeichnung für das Element auf Ihrer Registerkarte, die beim Anzeigen des Tiefenlinks, der Aufgabenliste 123 oder der Aufgabe 456 verwendet werden soll.

Beispiel: https://teams.microsoft.com/l/entity/fe4a8eba-2a31-4737-8e33-e5fae6fee194/tasklist123?webUrl=https://tasklist.example.com/123&TaskList

## <a name="deep-linking-to-the-scheduling-dialog"></a>Tiefenverknüpfung mit dem Planungsdialog

> [!NOTE]
> Diese Funktion befindet sich derzeit in der Entwicklervorschau.

Sie können tiefe Verknüpfungen zum Teams integrierten Planungsdialog feldieren. Dies ist besonders nützlich, wenn Ihre App dem Benutzer hilft, Kalender abzuschließen oder verwandte Aufgaben zu planen.

### <a name="generate-a-deep-link-to-the-scheduling-dialog"></a>Generieren einer Tiefenverknüpfung zum Planungsdialogfeld

Verwenden Sie das folgende Format für einen Deep Link, den Sie in einer Bot-, Connector- oder Messagingerweiterungskarte verwenden können: `https://teams.microsoft.com/l/meeting/new?subject=<meeting subject>&startTime=<date>&endTime=<date>&content=<content>&attendees=<user1>,<user2>,<user3>,...`

Beispiel: `https://teams.microsoft.com/l/meeting/new?subject=test%20subject&attendees=joe@contoso.com,bob@contoso.com&startTime=10%2F24%2F2018%2010%3A30%3A00&endTime=10%2F24%2F2018%2010%3A30%3A00&content=test%3Acontent`

Die Abfrageparameter sind:

* `attendees`: Die durch optionale Kommas getrennte Liste der Benutzer-IDs, die die Teilnehmer der Besprechung darstellen. Der Benutzer, der die Aktion ausführt, ist der Besprechungsorganisator. Das Feld Benutzer-ID unterstützt derzeit nur den Azure AD UserPrincipalName, in der Regel eine E-Mail-Adresse.
* `startTime`: Die optionale Startzeit des Ereignisses. Dies sollte im [langen ISO 8601-Format](https://en.wikipedia.org/wiki/ISO_8601)sein, zum Beispiel *2018-03-12T23:55:25+02:00*.
* `endTime`: Die optionale Endzeit des Ereignisses, auch im ISO 8601-Format.
* `subject`: Ein optionales Feld für das Besprechungsthema.
* `content`: Ein optionales Feld für das Besprechungsdetailsfeld.

> [!NOTE]
> Derzeit wird das Angeben des Speicherorts nicht unterstützt. Sie müssen den UTC-Offset angeben, d. h. Zeitzonen beim Generieren Ihrer Start- und Endzeiten.

Um diese deep Link mit Ihrem Bot zu verwenden, können Sie dies als URL-Ziel in der Schaltfläche Ihrer Karte angeben oder auf Aktion durch den `openUrl` Aktionstyp tippen.

## <a name="deep-linking-to-an-audio-or-audio-video-call"></a>Tiefenverknüpfung mit einem Audio- oder Audio-Videoanruf

Sie können tiefe Links erstellen, um nur Audio- oder Audiovideoaufrufe an einen einzelnen Benutzer oder eine Gruppe von Benutzern aufzurufen, indem Sie den Anruftyp als *Audio* oder *av* und die Teilnehmer angeben. Nachdem der Deep Link aufgerufen wurde und vor dem Aufruf, fordert Teams Desktopclient eine Bestätigung auf, um den Anruf zu tätigen. Im Falle eines Gruppenaufrufs können Sie eine Gruppe von VoIP-Benutzern und eine Gruppe von PSTN-Benutzern in demselben Deeplink-Aufruf aufrufen. 

Im Falle eines Videoanrufs wird der Client um Bestätigung bitten und das Video des Anrufers für den Anruf einschalten. Der Empfänger des Anrufs hat die Wahl, nur über Audio oder Audio und Video, über das Teams Anrufbenachrichtigungsfenster zu reagieren.

> [!NOTE]
> Dieser Deeplink kann nicht zum Aufrufen einer Besprechung verwendet werden.

### <a name="generate-a-deep-link-to-a-call"></a>Generieren einer tiefen Verknüpfung zu einem Anruf

| Deep Link | Format | Beispiel |
|-----------|--------|---------|
| Tätigen eines Audioanrufs | https://teams.microsoft.com/l/call/0/0?users=&lt;user1 &gt; , &lt; user2&gt; | https://teams.microsoft.com/l/call/0/0?users=joe@contoso.com |
| Erstellen eines Audio- und Videoanrufs | https://teams.microsoft.com/l/call/0/0?users=&lt;user1 &gt; , &lt; user2&&gt; withvideo=true | https://teams.microsoft.com/l/call/0/0?users=joe@contoso.com&withvideo=true |
|Erstellen eines Audio- und Videoanrufs mit einer optionalen Parameterquelle | https://teams.microsoft.com/l/call/0/0?users=&lt;user1 &gt; , &lt; user2&&gt; withvideo=true&source=demoApp | https://teams.microsoft.com/l/call/0/0?users=joe@contoso.com&withvideo=true&source=demoApp |  
| Erstellen eines Audio- und Videoanrufs an eine Kombination von VoIP- und PSTN-Benutzern | https://teams.microsoft.com/l/call/0/0?users=&lt;user1 &gt; ,4: &lt; Telefonnummer&gt; | https://teams.microsoft.com/l/call/0/0?users=joe@contoso.com,4:9876543210 |
  
Im Folgenden sind die Abfrageparameter:
* `users`: Die durch Kommas getrennte Liste der Benutzer-IDs, die die Teilnehmer des Aufrufs darstellen. Derzeit unterstützt das Feld Benutzer-ID den Azure AD UserPrincipalName, in der Regel eine E-Mail-Adresse, oder im Falle eines PSTN-Anrufs unterstützt es eine pstn mri 4: &lt; telefonnummer &gt; .
* `Withvideo`: Dies ist ein optionaler Parameter, den Sie verwenden können, um einen Videoanruf zu tätigen. Wenn Sie diesen Parameter festlegen, wird nur die Kamera des Anrufers eingeschaltet. Der Empfänger des Anrufs hat die Wahl, durch Audio- oder Audio- und Videoanruf über das Teams Anrufbenachrichtigungsfenster zu antworten. 
* `Source`: Dies ist ein optionaler Parameter, der über die Quelle des Deeplink informiert.

## <a name="code-sample"></a>Codebeispiel

| Beispielname | Beschreibung | C# |Node.js|
|-------------|-------------|------|----|
|Deep Link verbrauchen Subentity ID  |Microsoft Teams Beispiel-App zum Demonstrieren von Deeplink vom Bot-Chat bis zum Tab-Verbrauch der Subentity-ID.|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-deeplink/csharp)|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-deeplink/nodejs)|

## <a name="see-also"></a>Siehe auch

[Integrieren von Web-Apps](~/samples/integrate-web-apps-overview.md)

