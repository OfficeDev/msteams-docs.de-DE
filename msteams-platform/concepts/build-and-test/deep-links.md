---
title: Erstellen von Deep-Links
description: Beschreibt tiefe Links und deren Verwendung in Ihren Apps
ms.topic: how-to
localization_priority: Normal
keywords: deep link deeplink für Teams
ms.openlocfilehash: cd7735595f260431524edf1431ff22a1eeb361bc
ms.sourcegitcommit: e1fe46c574cec378319814f8213209ad3063b2c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2021
ms.locfileid: "52630145"
---
# <a name="create-deep-links"></a>Erstellen von Deep-Links 

Sie können Links zu Informationen und Features innerhalb von Teams. Die folgenden Szenarien sind hilfreich, in denen das Erstellen von Tiefenverknüpfungen hilfreich ist:

* Navigieren Sie den Benutzer zu den Inhalten auf einer der Registerkarten Ihrer App. Beispielsweise kann Ihre App über einen Bot verfügen, der Nachrichten sendet, die den Benutzer über eine wichtige Aktivität benachrichtigen. Wenn der Benutzer auf die Benachrichtigung tippt, navigiert der Deep Link zur Registerkarte, damit der Benutzer weitere Details zur Aktivität anzeigen kann.
* Ihre App automatisiert oder vereinfacht bestimmte Benutzeraufgaben, z. B. das Erstellen eines Chats oder das Planen einer Besprechung, indem sie die Tiefenlinks mit den erforderlichen Parametern auffüllt. Dadurch wird vermieden, dass Benutzer Manuell Informationen eingeben müssen.

> [!NOTE]
>
> Ein Deeplink startet den Browser zuerst, bevor er zu Inhalt navigiert. Das Verhalten von tiefen Links Teams Entitäten lautet wie folgt:
>
> **Registerkarte**:  
> ✔ Navigiert direkt zur Deeplink-URL.
>
> **Bot**:  
> ✔ Deeplink im Kartentext: Wird zuerst im Browser geöffnet.  
> ✔ Der OpenURL-Aktion in adaptive Karte hinzugefügte Deeplink: Navigiert direkt zur Deeplink-URL.  
> ✔ link markdown text in the card: Wird zuerst im Browser geöffnet.  
>
> **Chat**:  
> ✔ Text message hyperlink markdown: Navigiert direkt zu deeplink url.  
> ✔ Link, der in der allgemeinen Chatunterhaltung eingegeben wird: Navigiert direkt zu deeplink-URL.

## <a name="deep-linking-to-your-tab"></a>Tiefe Verknüpfung mit Ihrer Registerkarte

Sie können tiefe Links zu Entitäten in Teams. Dies wird verwendet, um Links zu Erstellen, die zu Inhalten und Informationen auf Ihrer Registerkarte navigieren. Wenn Ihre Registerkarte beispielsweise eine Aufgabenliste enthält, können Teammitglieder Links zu einzelnen Aufgaben erstellen und freigeben. Wenn Sie den Link auswählen, navigiert er zu Ihrer Registerkarte, die sich auf das bestimmte Element konzentriert. Um dies zu  implementieren, fügen Sie jedem Element eine Kopierlinkaktion hinzu, unabhängig davon, wie die Benutzeroberfläche am besten geeignet ist. Wenn der Benutzer diese Aktion ergreift, rufen Sie ein Dialogfeld mit einem Link auf, den der Benutzer in die `shareDeepLink()` Zwischenablage kopieren kann. Wenn Sie diesen Aufruf machen, übergeben Sie auch eine ID [](~/tabs/how-to/access-teams-context.md) für Ihr Element, die Sie im Kontext erhalten, wenn der Link gefolgt wird und Ihre Registerkarte neu geladen wird.

Alternativ können Sie mithilfe des weiter unten in diesem Thema angegebenen Formats auch programmgesteuert DeepLinks generieren. Sie können DeepLinks in [Bot-](~/bots/what-are-bots.md) und [Connectornachrichten](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md) verwenden, die Benutzer über Änderungen an Ihrer Registerkarte oder an Elementen in der Registerkarte informieren.

> [!NOTE]
> Dieser deep link ist anders als  die Links, die durch den Link zum Registerkartenmenüelement kopieren bereitgestellt werden, wodurch nur ein tiefer Link generiert wird, der auf diese Registerkarte verweist.

>[!NOTE]
> Derzeit funktioniert shareDeepLink nicht auf mobilen Plattformen.

### <a name="show-a-deep-link-to-an-item-within-your-tab"></a>Anzeigen eines tiefen Links zu einem Element auf Ihrer Registerkarte

Rufen Sie auf, um ein Dialogfeld anzuzeigen, das einen tiefen Link zu einem Element auf Ihrer Registerkarte `microsoftTeams.shareDeepLink({ subEntityId: <subEntityId>, subEntityLabel: <subEntityLabel>, subEntityWebUrl: <subEntityWebUrl> })` enthält.

Geben Sie die folgenden Felder an:

* `subEntityId`: Ein eindeutiger Bezeichner für das Element auf Ihrer Registerkarte, mit dem Sie eine tiefe Verknüpfung verwenden.
* `subEntityLabel`: Eine Bezeichnung für das Element, das zum Anzeigen des Tiefenlinks verwendet werden soll.
* `subEntityWebUrl`: Ein optionales Feld mit einer Fallback-URL, die verwendet werden soll, wenn der Client das Rendern der Registerkarte nicht unterstützt.

### <a name="generate-a-deep-link-to-your-tab"></a>Generieren eines tiefen Links zu Ihrer Registerkarte

> [!NOTE]
> Persönliche Registerkarten haben einen `personal` Bereich, während Kanal- und Gruppenregisterkarten `team` Bereiche verwenden oder `group` verwenden. Die beiden Registerkartentypen haben eine leicht unterschiedliche Syntax, da nur der konfigurierbaren Registerkarte eine Eigenschaft mit `channel` dem Kontextobjekt zugeordnet ist. Weitere Informationen [zu Registerkartenbereich](~/resources/schema/manifest-schema.md) finden Sie in der Manifestreferenz.

> [!NOTE]
> Tiefenlinks funktionieren nur dann ordnungsgemäß, wenn die Registerkarte mit der v0.4- oder höher-Bibliothek konfiguriert wurde und daher über eine Entitäts-ID verfügt. Tiefe Links zu Registerkarten ohne Entitäts-IDs navigieren weiterhin zur Registerkarte, können jedoch die Unterentitäts-ID nicht auf der Registerkarte bereitstellen.

Verwenden Sie das folgende Format für einen tiefen Link, den Sie auf einer Bot-, Connector- oder Messagingerweiterungskarte verwenden können:

`https://teams.microsoft.com/l/entity/<appId>/<entityId>?webUrl=<entityWebUrl>&label=<entityLabel>&context=<context>`

> [!NOTE]
> Wenn der Bot eine Nachricht mit einem deep link sendet, wird eine neue Browserregisterkarte geöffnet, wenn der Benutzer `TextBlock` den Link auswählt. Dies geschieht in Chrome und in Microsoft Teams Desktop-App, die beide unter Linux ausgeführt werden.
> Wenn der Bot dieselbe Deep Link-URL an sendet, wird die Registerkarte Teams auf der aktuellen Browserregisterkarte geöffnet, wenn der Benutzer `Action.OpenUrl` den Link auswählt. Eine neue Browserregisterkarte wird nicht geöffnet.

Die Abfrageparameter sind:

| Parametername | Beschreibung | Beispiel |
|:------------|:--------------|:---------------------|
| `appId`&emsp; | Die ID aus Ihrem Manifest. |fe4a8eba-2a31-4737-8e33-e5fae6fee194|
| `entityId`&emsp; | Die ID für das Element auf der Registerkarte, die Sie beim Konfigurieren der [Registerkarte angegeben haben.](~/tabs/how-to/create-tab-pages/configuration-page.md)|Tasklist123|
| `entityWebUrl` oder `subEntityWebUrl`&emsp; | Ein optionales Feld mit einer Fallback-URL, die verwendet werden soll, wenn der Client das Rendern der Registerkarte nicht unterstützt. | `https://tasklist.example.com/123` oder `https://tasklist.example.com/list123/task456` |
| `entityLabel` oder `subEntityLabel`&emsp; | Eine Bezeichnung für das Element auf Ihrer Registerkarte, die beim Anzeigen des Tiefenlinks verwendet werden soll. | Aufgabenliste 123 oder "Aufgabe 456 |
| `context`&emsp; </br></br>* `subEntityId`&emsp;</br></br> * `channelId`&emsp;| Ein JSON-Objekt mit den folgenden Feldern:</br></br> * Eine ID für das Element auf der Registerkarte. </br></br> * Die Microsoft Teams Kanal-ID, die im Registerkartenkontext verfügbar [ist.](~/tabs/how-to/access-teams-context.md) | 
| `subEntityId`&emsp; | Eine ID für das Element auf der Registerkarte. |Task456 |
| `channelId`&emsp; | Die Microsoft Teams Kanal-ID, die im Registerkartenkontext verfügbar [ist.](~/tabs/how-to/access-teams-context.md) Diese Eigenschaft ist nur auf konfigurierbaren Registerkarten mit teamfähigem **Bereich verfügbar.** Es ist nicht in statischen Registerkarten verfügbar, die einen Bereich von **persönlichen haben.**| 19:cbe3683f25094106b826c9cada3afbe0@thread.skype |

Beispiele:

* Link zu einer konfigurierbaren Registerkarte selbst: `https://teams.microsoft.com/l/entity/fe4a8eba-2a31-4737-8e33-e5fae6fee194/tasklist123?webUrl=https://tasklist.example.com/123&label=Task List 123&context={"channelId": "19:cbe3683f25094106b826c9cada3afbe0@thread.skype"}`
* Link zu einem Aufgabenelement auf der konfigurierbaren Registerkarte: `https://teams.microsoft.com/l/entity/fe4a8eba-2a31-4737-8e33-e5fae6fee194/tasklist123?webUrl=https://tasklist.example.com/123/456&label=Task 456&context={"subEntityId": "task456","channelId": "19:cbe3683f25094106b826c9cada3afbe0@thread.skype"}`
* Link zu einer statischen Registerkarte selbst: `https://teams.microsoft.com/l/entity/fe4a8eba-2a31-4737-8e33-e5fae6fee194/tasklist123?webUrl=https://tasklist.example.com/123&label=Task List 123`
* Link zu einem Aufgabenelement auf der statischen Registerkarte: `https://teams.microsoft.com/l/entity/fe4a8eba-2a31-4737-8e33-e5fae6fee194/tasklist123?webUrl=https://tasklist.example.com/123/456&label=Task 456&context={"subEntityId": "task456"}`

> [!IMPORTANT]
> Stellen Sie sicher, dass alle Abfrageparameter ordnungsgemäß URI codiert sind. Sie müssen den voran folgenden Beispielen folgen, indem Sie das letzte Beispiel verwenden:

> ```javascript
> var encodedWebUrl = encodeURI('https://tasklist.example.com/123/456&label=Task 456');
> var encodedContext = encodeURI('{"subEntityId": "task456"}');
> var taskItemUrl = 'https://teams.microsoft.com/l/entity/fe4a8eba-2a31-4737-8e33-e5fae6fee194/tasklist123?webUrl=' + encodedWebUrl + '&context=' + encodedContext;
> ```

### <a name="consume-a-deep-link-from-a-tab"></a>Verwenden eines Tiefenlinks von einer Registerkarte

Beim Navigieren zu einem tiefen Link navigiert Microsoft Teams einfach zur Registerkarte und stellt einen Mechanismus über die Microsoft Teams-JavaScript-Bibliothek zum Abrufen der Unterentitäts-ID zur Verfügung, falls vorhanden.

Der [`microsoftTeams.getContext`](/javascript/api/@microsoft/teams-js#getcontext--context--context-----void-) Aufruf gibt einen Kontext zurück, der das Feld enthält, wenn die Registerkarte über einen tiefen Link `subEntityId` navigiert wird.

## <a name="deep-linking-from-your-tab"></a>Tiefe Verknüpfung von Ihrer Registerkarte aus

Sie können eine Deeplink-Verknüpfung mit Inhalten in Teams Ihrer Registerkarte erstellen. Dies ist hilfreich, wenn Ihre Registerkarte mit anderen Inhalten in Teams verknüpfen muss, z. B. zu einem Kanal, einer Nachricht, einer anderen Registerkarte oder sogar zum Öffnen eines Terminplanungsdialogfelds. Um einen Deeplink von Ihrer Registerkarte auszulösen, rufen Sie auf:

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

## <a name="deep-linking-to-a-chat"></a>Tiefe Verknüpfung mit einem Chat

Sie können tiefe Links zu privaten Chats zwischen Benutzern erstellen, indem Sie den Teilnehmersatz angeben. Wenn kein Chat mit den angegebenen Teilnehmern vorhanden ist, navigiert der Link den Benutzer zu einem leeren neuen Chat. Neue Chats werden im Entwurfszustand erstellt, bis der Benutzer die erste Nachricht sendet. Andernfalls können Sie den Namen des Chats angeben, wenn er noch nicht vorhanden ist, zusammen mit Text, der in das Verfassenfeld des Benutzers eingefügt werden soll. Sie können sich dieses Feature als Verknüpfung für den Benutzer ausmalen, der die manuelle Aktion des Navigierens zu oder erstellen des Chats und anschließendes Eingeben der Nachricht.

Wenn Sie beispielsweise ein Office 365 Benutzerprofil von Ihrem Bot als Karte zurückgeben, kann dieser deep link dem Benutzer ermöglichen, einfach mit dieser Person zu chatten.

### <a name="generate-a-deep-link-to-a-chat"></a>Generieren eines tiefen Links zu einem Chat

Verwenden Sie dieses Format für einen tiefen Link, den Sie auf einer Bot-, Connector- oder Messagingerweiterungskarte verwenden können:

`https://teams.microsoft.com/l/chat/0/0?users=<user1>,<user2>,...&topicName=<chat name>&message=<precanned text>`

Beispiel: `https://teams.microsoft.com/l/chat/0/0?users=joe@contoso.com,bob@contoso.com&topicName=Prep%20For%20Meeting%20Tomorrow&message=Hi%20folks%2C%20kicking%20off%20a%20chat%20about%20our%20meeting%20tomorrow`

Die Abfrageparameter sind:

* `users`: Die durch Kommas getrennte Liste der Benutzer-IDs, die die Teilnehmer des Chats darstellen. Der Benutzer, der die Aktion ausführt, ist immer als Teilnehmer enthalten. Derzeit unterstützt das Feld Benutzer-ID den Azure AD UserPrincipalName, z. B. nur eine E-Mail-Adresse.
* `topicName`: Ein optionales Feld für den Anzeigenamen des Chats, bei einem Chat mit 3 oder mehr Benutzern. Wenn dieses Feld nicht angegeben ist, basiert der Anzeigename des Chats auf den Namen der Teilnehmer.
* `message`: Ein optionales Feld für den Nachrichtentext, den Sie in das Verfassenfeld des aktuellen Benutzers einfügen möchten, während sich der Chat im Entwurfszustand befindet.

Um diesen tiefen Link mit Ihrem Bot zu verwenden, geben Sie dies als URL-Ziel in der Schaltfläche Ihrer Karte an, oder tippen Sie über den `openUrl` Aktionstyp auf Aktion.

## <a name="generate-deep-links-to-file-in-channel"></a>Generieren von tiefen Links zu Dateien im Kanal

Das folgende Deep Link-Format kann in einer Bot-, Connector- oder Messagingerweiterungskarte verwendet werden:

`https://teams.microsoft.com/l/file/5E0154FC-F2B4-4DA5-8CDA-F096E72C0A80?tenantId=<tenantid>&fileType=<filetype>&objectURL=<objectURL>&baseUrl=<baseURL>&serviceName=<Name>&threadId=<threadid>&groupId=<groupId>`

Die Abfrageparameter sind:

* `tenantId`: Mandanten-ID-Beispiel, 0d9b645f-597b-41f0-a2a3-ef103fbd91bb
* `fileType`: Unterstützter Dateityp, z. B. docx, pptx, xlsx und pdf
* `objectUrl`: Objekt-URL der Datei, `https://microsoft.sharepoint.com/teams/(filepath)`
* `baseUrl`: Basis-URL der Datei, `https://microsoft.sharepoint.com/teams`
* `serviceName`: Name des Diensts, App-ID
* `threadId`: Die threadId ist die Team-ID des Teams, in dem die Datei gespeichert ist. Sie ist optional und kann nicht für Dateien festgelegt werden, die im Ordner "OneDrive" eines Benutzers gespeichert sind. threadId – 19:f8fbfc4d89e24ef5b3b8692538cebeb7@thread.skype
* `groupId`: Gruppen-ID der Datei, ae063b79-5315-4ddb-ba70-27328ba6c31e

Im Folgenden finden Sie das Beispielformat von Deeplink zu Dateien:

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
## <a name="deep-linking-for-sharepoint-framework-tabs"></a>Tiefe Verknüpfung für SharePoint-Framework Registerkarten

Das folgende Deep Link-Format kann in einer Bot-, Connector- oder Messagingerweiterungskarte verwendet werden: `https://teams.microsoft.com/l/entity/<AppId>/<EntityId>?webUrl=<entityWebUrl>/<EntityName>`

> [!NOTE]
> Wenn ein Bot eine TextBlock-Nachricht mit einem tiefen Link sendet, wird eine neue Browserregisterkarte geöffnet, wenn Benutzer den Link auswählen. Dies geschieht in Chrome und Microsoft Teams Desktop-App, die unter Linux ausgeführt wird.
> Wenn der Bot dieselbe Deep Link-URL an sendet, wird die Registerkarte Teams im aktuellen Browser geöffnet, wenn der Benutzer `Action.OpenUrl` den Link auswählt. Es wird keine neue Browserregisterkarte geöffnet.

Die Abfrageparameter sind:

* `appID`: Ihre Manifest-ID **fe4a8eba-2a31-4737-8e33-e5fae6fee194**.

* `entityID`: Die Element-ID, die Sie beim [Konfigurieren der Registerkarte angegeben haben.](~/tabs/how-to/create-tab-pages/configuration-page.md) Beispiel: **tasklist123**.
* `entityWebUrl`: Ein optionales Feld mit einer Fallback-URL, die verwendet werden soll, wenn der Client das Rendern der Registerkarte nicht unterstützt – `https://tasklist.example.com/123` oder `https://tasklist.example.com/list123/task456` .
* `entityName`: Eine Bezeichnung für das Element auf Ihrer Registerkarte, die beim Anzeigen des Tiefenlinks, Aufgabenliste 123 oder Aufgabe 456 verwendet werden soll.

Beispiel: https://teams.microsoft.com/l/entity/fe4a8eba-2a31-4737-8e33-e5fae6fee194/tasklist123?webUrl=https://tasklist.example.com/123&TaskList

## <a name="deep-linking-to-the-scheduling-dialog"></a>Tiefe Verknüpfung mit dem Planungsdialogfeld

> [!NOTE]
> Dieses Feature befindet sich derzeit in der Entwicklervorschau.

Sie können tiefe Links zum integrierten Teams erstellen. Dies ist besonders hilfreich, wenn Ihre App dem Benutzer dabei hilft, kalender- oder terminbezogene Aufgaben auszuführen.

### <a name="generate-a-deep-link-to-the-scheduling-dialog"></a>Generieren eines tiefen Links zum Planungsdialogfeld

Verwenden Sie das folgende Format für einen tiefen Link, den Sie auf einer Bot-, Connector- oder Messagingerweiterungskarte verwenden können: `https://teams.microsoft.com/l/meeting/new?subject=<meeting subject>&startTime=<date>&endTime=<date>&content=<content>&attendees=<user1>,<user2>,<user3>,...`

Beispiel: `https://teams.microsoft.com/l/meeting/new?subject=test%20subject&attendees=joe@contoso.com,bob@contoso.com&startTime=10%2F24%2F2018%2010%3A30%3A00&endTime=10%2F24%2F2018%2010%3A30%3A00&content=test%3Acontent`

Die Abfrageparameter sind:

* `attendees`: Die optionale durch Kommas getrennte Liste der Benutzer-IDs, die die Teilnehmer der Besprechung darstellen. Der Benutzer, der die Aktion ausführen, ist der Besprechungsorganisator. Das Feld Benutzer-ID unterstützt derzeit nur den Azure AD UserPrincipalName, in der Regel eine E-Mail-Adresse.
* `startTime`: Die optionale Startzeit des Ereignisses. Dies sollte im langen [ISO 8601-Format](https://en.wikipedia.org/wiki/ISO_8601)vorliegen, z. B. *2018-03-12T23:55:25+02:00*.
* `endTime`: Die optionale Endzeit des Ereignisses, auch im ISO 8601-Format.
* `subject`: Ein optionales Feld für den Besprechungsthema.
* `content`: Ein optionales Feld für das Besprechungsdetailsfeld.

> [!NOTE]
> Derzeit wird das Angeben des Speicherorts nicht unterstützt. Sie müssen den UTC-Offset angeben, d. h. Zeitzonen beim Generieren der Start- und Endzeiten.

Um diesen tiefen Link mit Ihrem Bot zu verwenden, können Sie dies als URL-Ziel in der Schaltfläche Ihrer Karte angeben oder über den `openUrl` Aktionstyp auf Aktion tippen.

## <a name="deep-linking-to-an-audio-or-audio-video-call"></a>Tiefe Verknüpfung mit einem Audio- oder Audiovideoanruf

Sie können tiefe Links erstellen, um nur Audio- oder Audiovideoanrufe an einen einzelnen Benutzer oder eine Gruppe von Benutzern aufrufen zu können, indem Sie den Anruftyp als *Audio* oder *av* und die Teilnehmer angeben. Nach dem Aufrufen des Tiefenlinks und vor dem Anruf fordert Teams Desktopclient eine Bestätigung für den Anruf an. Bei Gruppenanrufen können Sie eine Gruppe von VoIP-Benutzern und eine Gruppe von PSTN-Benutzern im gleichen Deeplinkaufruf aufrufen. 

Bei einem Videoanruf bittet der Client um Bestätigung und das Video des Anrufers für den Anruf. Der Empfänger des Anrufs hat die Wahl, nur über Audio oder Audio und Video über das Teams Benachrichtigungsfenster zu antworten.

> [!NOTE]
> Diese Deeplink kann nicht zum Aufrufen einer Besprechung verwendet werden.

### <a name="generate-a-deep-link-to-a-call"></a>Generieren eines tiefen Links zu einem Anruf

| Deep Link | Format | Beispiel |
|-----------|--------|---------|
| Audioanrufe | https://teams.microsoft.com/l/call/0/0?users=&lt;user1 &gt; , &lt; user2&gt; | https://teams.microsoft.com/l/call/0/0?users=joe@contoso.com |
| Audio- und Videoanrufe | https://teams.microsoft.com/l/call/0/0?users=&lt;user1 &gt; , &lt; user2&&gt; withvideo=true | https://teams.microsoft.com/l/call/0/0?users=joe@contoso.com&withvideo=true |
|Audio- und Videoanrufe mit einer optionalen Parameterquelle | https://teams.microsoft.com/l/call/0/0?users=&lt;user1 &gt; , &lt; user2&&gt; withvideo=true&source=demoApp | https://teams.microsoft.com/l/call/0/0?users=joe@contoso.com&withvideo=true&source=demoApp |  
| Audio- und Videoanrufe für eine Kombination von VoIP- und PSTN-Benutzern | https://teams.microsoft.com/l/call/0/0?users=&lt;user1 &gt; ,4: &lt; phonenumber&gt; | https://teams.microsoft.com/l/call/0/0?users=joe@contoso.com,4:9876543210 |
  
Es folgen die Abfrageparameter:
* `users`: Die durch Kommas getrennte Liste der Benutzer-IDs, die die Teilnehmer des Anrufs darstellen. Derzeit unterstützt das Feld Benutzer-ID den Azure AD UserPrincipalName, in der Regel eine E-Mail-Adresse, oder im Falle eines PSTN-Anrufs unterstützt es ein pstn mri 4: &lt; phonenumber &gt; .
* `Withvideo`: Dies ist ein optionaler Parameter, den Sie für einen Videoanruf verwenden können. Wenn Sie diesen Parameter festlegen, wird nur die Kamera des Anrufers aktivieren. Der Empfänger des Anrufs hat die Wahl, über audio- oder audio- und videoanrufe über das Teams Anrufbenachrichtigungsfenster zu beantworten. 
* `Source`: Dies ist ein optionaler Parameter, der über die Quelle des Deeplinks informiert.

## <a name="code-sample"></a>Codebeispiel

| Beispielname | Beschreibung | C# |Node.js|
|-------------|-------------|------|----|
|Deep Link, der die Subentity-ID verwendet  |Microsoft Teams Beispiel-App zum Demonstrieren der Deeplinks vom Botchat zur Registerkarte, die die Subentity-ID verwendet.|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-deeplink/csharp)|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-deeplink/nodejs)|

## <a name="see-also"></a>Sehen Sie ebenfalls

[Integrieren von Web-Apps](~/samples/integrate-web-apps-overview.md)

