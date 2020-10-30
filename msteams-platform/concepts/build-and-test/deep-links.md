---
title: Erstellen von Deep-Links
description: Beschreibt Deep Links und deren Verwendung in ihren apps
keywords: Teams Deep Link Deeplink
ms.openlocfilehash: 03580c4d15c82da70402d68d85b0d28f8afa670e
ms.sourcegitcommit: 3fc7ad33e2693f07170c3cb1a0d396261fc5c619
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "48796330"
---
# <a name="create-deep-links-to-content-and-features-in-microsoft-teams"></a>Erstellen von tiefen Links zu Inhalten und Features in Microsoft Teams

Sie können Links zu Informationen und Features innerhalb des Teams-Clients erstellen. Beispiele dafür, wo dies hilfreich sein kann:

* Navigieren des Benutzers zu Inhalten in einer der Registerkarten Ihrer APP. Beispielsweise kann Ihre APP einen bot haben, der Nachrichten sendet, die den Benutzer über eine wichtige Aktivität informieren. Wenn der Benutzer die Benachrichtigung antippt, navigiert der Deep Link zur Registerkarte, damit der Benutzer weitere Details zur Aktivität anzeigen kann.
* Ihre APP automatisiert oder vereinfacht bestimmte Benutzer Aufgaben, wie das Erstellen eines Chats oder das Planen einer Besprechung, indem die tiefen Verknüpfungen mit den erforderlichen Parametern vorab aufgefüllt werden. Dadurch wird vermieden, dass Benutzerinformationen manuell eingeben müssen.

## <a name="deep-linking-to-your-tab"></a>Tiefes verknüpfen mit ihrer Registerkarte

Sie können tiefe Links zu Entitäten in Microsoft Teams erstellen. Normalerweise wird dies verwendet, um Links zu erstellen, die zu Inhalten und Informationen in ihrer Registerkarte navigieren. Wenn Ihre Registerkarte beispielsweise eine Aufgabenliste enthält, können Mitglieder Links zu einzelnen Aufgaben erstellen und freigeben. Wenn Sie darauf klicken, navigiert der Link zu ihrer Registerkarte, die sich auf das jeweilige Element konzentriert. Um dies zu implementieren, fügen Sie eine "Copy Link"-Aktion zu jedem Element hinzu, in welcher Weise am besten zu Ihrer Benutzeroberfläche passt. Wenn der Benutzer diese Aktion ausführt, rufen Sie `shareDeepLink()` an, um ein Dialogfeld anzuzeigen, das einen Link enthält, den der Benutzer in die Zwischenablage kopieren kann. Wenn Sie diesen Anruf tätigen, übergeben Sie auch eine ID für Ihr Element, das Sie zurück im [Kontext](~/tabs/how-to/access-teams-context.md) erhalten, wenn der Link befolgt wird und ihre Registerkarte erneut lädt.

Alternativ können Sie auch Deep Links programmgesteuert mit dem Format erstellen, das weiter unten in diesem Thema beschrieben wird. Möglicherweise möchten Sie diese in [bot](~/bots/what-are-bots.md) -und [Connector](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md) -Nachrichten verwenden, die Benutzer über Änderungen an ihrer Registerkarte oder zu den darin enthaltenen Elementen informieren.

> [!NOTE]
> Dies unterscheidet sich von den Links, die im Menüelement **Copy Link to Tab** zur Verfügung gestellt werden, das lediglich einen tiefen Link generiert, der auf diese Registerkarte zeigt.

### <a name="showing-a-deep-link-to-an-item-within-your-tab"></a>Anzeigen einer tiefen Verknüpfung zu einem Element auf der Registerkarte

Wenn Sie ein Dialogfeld mit einer tiefen Verknüpfung zu einem Element in ihrer Registerkarte anzeigen möchten, rufen Sie `microsoftTeams.shareDeepLink({ subEntityId: <subEntityId>, subEntityLabel: <subEntityLabel>, subEntityWebUrl: <subEntityWebUrl> })`

Geben Sie die folgenden Felder an:

* `subEntityId`&emsp;Ein eindeutiger Bezeichner für das Element in der Registerkarte, zu der Sie eine Tiefe Verknüpfung herstellen.
* `subEntityLabel`&emsp;Eine Bezeichnung für das Element, das zum Anzeigen der tiefen Verknüpfung verwendet werden soll.
* `subEntityWebUrl`&emsp;Ein optionales Feld mit einer Fallback-URL, die verwendet werden soll, wenn der Client das Rendern der Registerkarte nicht unterstützt

### <a name="generating-a-deep-link-to-your-tab"></a>Erstellen einer tiefen Verknüpfung zu ihrer Registerkarte

> [!NOTE]
> Statische Registerkarten haben einen Bereich von "persönlich" und konfigurierbare Registerkarten haben einen Bereich von "Team". Die zwei Registerkartentypen weisen eine geringfügig unterschiedliche Syntax auf, da nur der konfigurierbaren Registerkarte eine `channel` Eigenschaft zugeordnet ist, die mit Ihrem Kontextobjekt verknüpft ist. In der [Manifest](~/resources/schema/manifest-schema.md) -Referenz finden Sie weitere Informationen zu persönlichen und teambezogenen Bereichen.
> [!NOTE]
> Deep-Links funktionieren nur dann ordnungsgemäß, wenn die Registerkarte mit der Bibliothek v 0.4 oder höher konfiguriert wurde und aufgrund dessen eine Entitäts-ID vorliegt. Deep-Links zu Registerkarten ohne Entitäts-IDs navigieren weiterhin zur Registerkarte, können aber die unter Entitäts-ID nicht zur Registerkarte bereitstellen.

Verwenden Sie dieses Format für einen tiefen Link, den Sie in einer bot-, Connector-oder Messaging Erweiterungskarte verwenden können:

`https://teams.microsoft.com/l/entity/<appId>/<entityId>?webUrl=<entityWebUrl>&label=<entityLabel>&context=<context>`

Die Abfrageparameter lauten wie folgt:

* `appId`&emsp;Die ID aus ihrem Manifest; Beispiel: "fe4a8eba-2a31-4737-8e33-e5fae6fee194"
* `entityId`&emsp;Die ID für das Element auf der Registerkarte, das Sie beim [Konfigurieren der Registerkarte](~/tabs/how-to/create-tab-pages/configuration-page.md)angegeben haben; Beispiel: "tasklist123"
* `entityWebUrl`oder `subEntityWebUrl` &emsp; ein optionales Feld mit einer Fallback-URL, das verwendet werden soll, wenn der Client das Rendern der Registerkarte nicht unterstützt, beispielsweise " https://tasklist.example.com/123 " oder " https://tasklist.example.com/list123/task456 "
* `entityLabel`oder `subEntityLabel` &emsp; eine Bezeichnung für das Element auf der Registerkarte, das beim Anzeigen der tiefen Verknüpfung verwendet werden soll, beispielsweise "Aufgabenliste 123" oder "Aufgabe 456".
* `context`&emsp;Ein JSON-Objekt, das die folgenden Felder enthält:
  * `subEntityId`&emsp;Eine ID für das Element _auf_ der Registerkarte; Beispiel: "task456"
  * `channelId`&emsp;Die Microsoft Teams-Kanal-ID (verfügbar über den Registerkarten [Kontext](~/tabs/how-to/access-teams-context.md), beispielsweise "19: cbe3683f25094106b826c9cada3afbe0@Thread. Skype". Diese Eigenschaft ist nur in konfigurierbaren Registerkarten mit einem Bereich von "Team" verfügbar. Es ist nicht in statischen Registerkarten verfügbar, die einen Bereich von "persönlich" haben.

Beispiele:

* Link zu einer konfigurierbaren Registerkarte selbst: `https://teams.microsoft.com/l/entity/fe4a8eba-2a31-4737-8e33-e5fae6fee194/tasklist123?webUrl=https://tasklist.example.com/123&label=Task List 123&context={"channelId": "19:cbe3683f25094106b826c9cada3afbe0@thread.skype"}`
* Link zu einem Aufgabenelement auf der konfigurierbaren Registerkarte: `https://teams.microsoft.com/l/entity/fe4a8eba-2a31-4737-8e33-e5fae6fee194/tasklist123?webUrl=https://tasklist.example.com/123/456&label=Task 456&context={"subEntityId": "task456","channelId": "19:cbe3683f25094106b826c9cada3afbe0@thread.skype"}`
* Link zu einer statischen Registerkarte selbst: `https://teams.microsoft.com/l/entity/fe4a8eba-2a31-4737-8e33-e5fae6fee194/tasklist123?webUrl=https://tasklist.example.com/123&label=Task List 123`
* Link zu einem Aufgabenelement auf der Registerkarte static: `https://teams.microsoft.com/l/entity/fe4a8eba-2a31-4737-8e33-e5fae6fee194/tasklist123?webUrl=https://tasklist.example.com/123/456&label=Task 456&context={"subEntityId": "task456"}`

> [!IMPORTANT]
> Stellen Sie sicher, dass alle Abfrageparameter ordnungsgemäß URI-codiert sind. Aus Gründen der Lesbarkeit sind die obigen Beispiele nicht, aber Sie sollten. Verwenden des letzten Beispiels:
> ```javascript
> var encodedWebUrl = encodeURI('https://tasklist.example.com/123/456&label=Task 456');
> var encodedContext = encodeURI('{"subEntityId": "task456"}');
> var taskItemUrl = 'https://teams.microsoft.com/l/entity/fe4a8eba-2a31-4737-8e33-e5fae6fee194/tasklist123?webUrl=' + encodedWebUrl + '&context=' + encodedContext;
> ```

### <a name="consuming-a-deep-link-from-a-tab"></a>Verwenden eines Deep-Links von einer Registerkarte

Bei der Navigation zu einem Deep Link navigiert Microsoft Teams einfach zur Registerkarte und stellt einen Mechanismus über die JavaScript-Bibliothek von Microsoft Teams bereit, um die unter Entitäts-ID abzurufen (sofern vorhanden).

Der [`microsoftTeams.getContext`](/javascript/api/@microsoft/teams-js#getcontext--context--context-----void-) Aufruf gibt einen Kontext zurück, der das Feld enthält, `subEntityId` Wenn die Registerkarte über einen tiefen Link navigiert wurde.

## <a name="deep-linking-from-your-tab"></a>Deep Linking von ihrer Registerkarte

Sie können Inhalte in Microsoft Teams auf Ihrer Registerkarte Deeplink. Dies ist hilfreich, wenn Ihre Registerkarte einen Link zu anderen Inhalten in Microsoft Teams wie einem Kanal, einer Nachricht, einer anderen Registerkarte oder sogar zum Öffnen eines Planungs Dialogfelds erstellen muss. Um eine Deeplink von ihrer Registerkarte auszulösen, sollten Sie Folgendes aufrufen:

```Javascript
microsoftTeams.executeDeepLink(/*deepLink*/);
```

Dadurch werden Sie zur korrekten URL navigiert oder eine Clientaktion wie das Öffnen eines Zeit Plan-oder App-Installationsdialogfelds ausgelöst. Beispiel:

```Javascript
// Open a scheduling dialog from your tab
microsoftTeams.executeDeepLink("https://teams.microsoft.com/l/meeting/new?subject=test%20subject&attendees=joe@contoso.com,bob@contoso.com&startTime=10%2F24%2F2018%2010%3A30%3A00&endTime=10%2F24%2F2018%2010%3A30%3A00&content=test%3Acontent");

// Open an app install dialog from your tab
microsoftTeams.executeDeepLink("https://teams.microsoft.com/l/app/f46ad259-0fe5-4f12-872d-c737b174bcb4");
```

## <a name="deep-linking-to-a-chat"></a>Deep Linking to a Chat

Sie können tiefe Links zu privaten Chats zwischen Benutzern erstellen, indem Sie die Gruppe der Teilnehmer angeben. Wenn ein Chat mit den angegebenen Teilnehmern nicht vorhanden ist, wird der Benutzer durch den Link zu einem leeren neuen Chat navigiert. Neue Chats werden im Entwurfszustand erstellt, bis der Benutzer die erste Nachricht sendet. Optional können Sie den Namen des Chats (sofern er noch nicht vorhanden ist) zusammen mit dem Text angeben, der in das Feld "Verfassen" des Benutzers eingefügt werden soll. Sie können sich dieses Feature als Verknüpfung für den Benutzer vorstellen, der die manuelle Aktion beim Navigieren zu oder Erstellen des Chats durchführt, und dann die Nachricht eingeben.

Wenn Sie als Beispiel einen Office 365 Benutzerprofil von Ihrem bot als Karte zurückgeben, kann dieser Deep Link dem Benutzer erlauben, problemlos mit dieser Person zu chatten.

### <a name="generating-a-deep-link-to-a-chat"></a>Erstellen einer tiefen Verknüpfung zu einem Chat

Verwenden Sie dieses Format für einen tiefen Link, den Sie in einer bot-, Connector-oder Messaging Erweiterungskarte verwenden können:

`https://teams.microsoft.com/l/chat/0/0?users=<user1>,<user2>,...&topicName=<chat name>&message=<precanned text>`

Beispiel: `https://teams.microsoft.com/l/chat/0/0?users=joe@contoso.com,bob@contoso.com&topicName=Prep%20For%20Meeting%20Tomorrow&message=Hi%20folks%2C%20kicking%20off%20a%20chat%20about%20our%20meeting%20tomorrow`

Die Abfrageparameter lauten wie folgt:

* `users`&emsp;Die durch trennzeichengetrennte Liste der Benutzer-IDs, die die Teilnehmer des Chats darstellen. Der Benutzer, der die Aktion ausführt, wird immer als Teilnehmer einbezogen. Das Feld Benutzer-ID unterstützt derzeit nur die Azure AD userPrincipalName (in der Regel eine e-Mail-Adresse).
* `topicName`&emsp;Ein optionales Feld für den Anzeigenamen des Chats, im Falle eines Chats mit 3 oder mehr Benutzern. Wenn dieses Feld nicht angegeben wird, basiert der Anzeigename des Chats auf den Namen der Teilnehmer.
* `message`&emsp;Ein optionales Feld für den Nachrichtentext, den Sie in das Feld "Verfassen" des aktuellen Benutzers einfügen möchten, während sich der Chat im Entwurfsstatus befindet.

Um diesen tiefen Link mit Ihrem bot zu verwenden, können Sie diesen als URL-Ziel in der Schaltfläche Ihrer Karte angeben oder auf Aktion durch den `openUrl` Aktionstyp tippen.

## <a name="linking-to-the-scheduling-dialog"></a>Verknüpfen mit dem Dialogfeld "Planung"

> [!Note]
> Dieses Feature befindet sich derzeit in der Entwicklervorschau.

Sie können tiefe Links zum integrierten Planungsdialogfeld des Teams-Clients erstellen. Dies ist besonders nützlich, wenn Ihre APP dem Benutzer hilft, Kalender-oder Planungsbezogene Aufgaben abzuschließen.

### <a name="generating-a-deep-link-to-the-scheduling-dialog"></a>Erstellen einer tiefen Verknüpfung zum Planungsdialogfeld

Verwenden Sie dieses Format für einen tiefen Link, den Sie in einer bot-, Connector-oder Messaging Erweiterungskarte verwenden können: `https://teams.microsoft.com/l/meeting/new?subject=<meeting subject>&startTime=<date>&endTime=<date>&content=<content>&attendees=<user1>,<user2>,<user3>,...`

Beispiel: `https://teams.microsoft.com/l/meeting/new?subject=test%20subject&attendees=joe@contoso.com,bob@contoso.com&startTime=10%2F24%2F2018%2010%3A30%3A00&endTime=10%2F24%2F2018%2010%3A30%3A00&content=test%3Acontent`

Die Abfrageparameter lauten wie folgt:

* `attendees`&emsp;Die optionale durch trennzeichengetrennte Liste der Benutzer-IDs, die die Teilnehmer der Besprechung darstellen. Der Benutzer, der die Aktion ausführt, ist der Besprechungsorganisator. Das Feld Benutzer-ID unterstützt derzeit nur die Azure AD userPrincipalName (in der Regel eine e-Mail-Adresse).
* `startTime`&emsp;Die optionale Startzeit des Ereignisses. Dies sollte im [langen Format ISO 8601](https://en.wikipedia.org/wiki/ISO_8601)sein, beispielsweise "2018-03-12T23:55:25 + 02:00".
* `endTime`&emsp;Die optionale Endzeit des Ereignisses, auch im Format ISO 8601.
* `subject`&emsp;Ein optionales Feld für den Besprechungs Betreff.
* `content`&emsp;Ein optionales Feld für das Feld Besprechungsdetails.

Die Angabe des Speicherorts wird derzeit nicht unterstützt. Achten Sie beim Generieren ihrer Start-und Endzeiten darauf, den UTC-Offset (Zeitzonen) anzugeben.

Um diesen tiefen Link mit Ihrem bot zu verwenden, können Sie diesen als URL-Ziel in der Schaltfläche Ihrer Karte angeben oder auf Aktion durch den `openUrl` Aktionstyp tippen.
