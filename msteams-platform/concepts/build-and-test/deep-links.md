---
title: Erstellen von Tiefenlinks zu Inhalten
description: Beschreibt Deep Links und deren Verwendung in Ihren Apps
ms.topic: how-to
keywords: Teams deep link deeplink
ms.openlocfilehash: d6efe7332035320d2114e0e834d1c971ccc7108c
ms.sourcegitcommit: e3b6bc31059ec77de5fbef9b15c17d358abbca0f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/12/2021
ms.locfileid: "50231561"
---
# <a name="create-deep-links-to-content-and-features-in-microsoft-teams"></a>Erstellen von Tiefenlinks zu Inhalten und Features in Microsoft Teams

Sie können Links zu Informationen und Features in Teams erstellen. Beispiele, in denen das Erstellen von Deep Links hilfreich ist, sind die folgenden:

* Navigieren des Benutzers zu Inhalten auf einer der Registerkarten Ihrer App. Beispielsweise kann Ihre App über einen Bot verfügen, der Nachrichten sendet, die den Benutzer über eine wichtige Aktivität informieren. Wenn der Benutzer auf die Benachrichtigung tippt, navigiert der Deep-Link zur Registerkarte, damit der Benutzer weitere Details zur Aktivität anzeigen kann.
* Ihre App automatisiert oder vereinfacht bestimmte Benutzeraufgaben, z. B. das Erstellen eines Chats oder das Planen einer Besprechung, indem die Deep-Links vorab mit den erforderlichen Parametern auffüllt. Dies vermeidet, dass Benutzer Informationen manuell eingeben müssen.

> [!NOTE]
>
> Ein Deeplink startet den Browser zuerst, bevor er wie folgt zu Inhalten und Informationen navigiert:
>
> **Registerkarte**:  
> ✔ Navigiert direkt zur Deeplink-URL.
>
> **Bot:**  
> ✔ Deeplink im Kartentext - Wird zuerst im Browser geöffnet.  
> ✔ Der Aktion "OpenURL" in der adaptiven Karte hinzugefügte Deeplink - Navigiert direkt zur Deeplink-URL.  
> ✔ Link-Markdown-Text auf der Karte – Wird zuerst im Browser geöffnet.  
>
> **Chat:**  
> ✔ Link "Markdown" für Textnachricht: Navigiert direkt zu deeplink-URL.  
> ✔ in allgemeine Chat-Unterhaltungen einfügenden Link – Navigiert direkt zur Deeplink-URL.

## <a name="deep-linking-to-your-tab"></a>Deep linking to your tab

Sie können Deep-Links zu Entitäten in Teams erstellen. In der Regel wird dies zum Erstellen von Links verwendet, die zu Inhalten und Informationen auf Ihrer Registerkarte navigieren. Wenn Ihre Registerkarte beispielsweise eine Aufgabenliste enthält, können Teammitglieder Links zu einzelnen Vorgängen erstellen und freigeben. Wenn Sie den Link auswählen, navigiert er zu Ihrer Registerkarte, die sich auf das bestimmte Element konzentriert. Um dies zu implementieren, fügen Sie jedem Element eine "Link kopieren"-Aktion hinzu, ganz gleich, wie dies für Ihre Benutzeroberfläche am besten geeignet ist. Wenn der Benutzer diese Aktion ergreift, rufen Sie ein Dialogfeld mit einem Link auf, den der Benutzer in die `shareDeepLink()` Zwischenablage kopieren kann. Wenn Sie diesen Aufruf machen, übergeben Sie auch eine ID [](~/tabs/how-to/access-teams-context.md) für Ihr Element, die Sie wieder im Kontext erhalten, wenn der Link folgt und Die Registerkarte neu geladen wird.

Alternativ können Sie auch mit dem weiter unten in diesem Thema angegebenen Format programmgesteuert Deep-Links generieren. Sie können diese in [Bot-](~/bots/what-are-bots.md) und [Connectornachrichten](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md) verwenden, die Benutzer über Änderungen an Ihrer Registerkarte oder an Elementen in der Registerkarte informieren.

> [!NOTE]
> Dieser Deep Link ist anders als  der Link zum Registerkartenmenüelement zum Kopieren, der nur einen Deep-Link generiert, der auf diese Registerkarte verweist.

>[!NOTE]
> ShareDeepLink funktioniert derzeit nicht auf mobilen Plattformen.

### <a name="showing-a-deep-link-to-an-item-within-your-tab"></a>Anzeigen eines Deep-Links zu einem Element auf ihrer Registerkarte

Um ein Dialogfeld anzuzeigen, das einen DeepLink zu einem Element auf Ihrer Registerkarte enthält, rufen Sie `microsoftTeams.shareDeepLink({ subEntityId: <subEntityId>, subEntityLabel: <subEntityLabel>, subEntityWebUrl: <subEntityWebUrl> })`

Geben Sie die folgenden Felder an:

* `subEntityId`&emsp;Ein eindeutiger Bezeichner für das Element auf ihrer Registerkarte, mit dem Sie eine Deep-Linking-Verbindung verwenden
* `subEntityLabel`&emsp;Eine Bezeichnung für das Element, das zum Anzeigen des DeepLinks verwendet werden soll
* `subEntityWebUrl`&emsp;Ein optionales Feld mit einer Fallback-URL, das verwendet werden soll, wenn der Client das Rendern der Registerkarte nicht unterstützt

### <a name="generating-a-deep-link-to-your-tab"></a>Generieren eines Deep-Links zu Ihrer Registerkarte

> [!NOTE]
> Persönliche Registerkarten haben einen `personal` Bereich, während Kanal- und Gruppenregisterkarten `team` Bereiche verwenden oder `group` verwenden. Die beiden Registerkartentypen haben eine etwas andere Syntax, da nur die konfigurierbare Registerkarte über eine Eigenschaft verfügt, die `channel` dem Kontextobjekt zugeordnet ist. Weitere Informationen [zu Registerkartenbereiche](~/resources/schema/manifest-schema.md) finden Sie in der Manifestreferenz.

> [!NOTE]
> Deep Links funktionieren nur ordnungsgemäß, wenn die Registerkarte mit der Bibliothek v0.4 oder höher konfiguriert wurde und daher eine Entitäts-ID hat. Deep-Links zu Registerkarten ohne Entitäts-IDs navigieren weiterhin zur Registerkarte, können jedoch die Unterentitäts-ID nicht auf der Registerkarte bereitstellen.

Verwenden Sie das folgende Format für einen Deep-Link, den Sie in einer Bot-, Connector- oder Messaging-Erweiterungskarte verwenden können:

`https://teams.microsoft.com/l/entity/<appId>/<entityId>?webUrl=<entityWebUrl>&label=<entityLabel>&context=<context>`

> [!NOTE]
> Wenn der Bot eine Nachricht mit einem Deep-Link sendet, wird eine neue Browserregisterkarte geöffnet, wenn der Benutzer `TextBlock` den Link auswählt. Dies geschieht in Chrome und in der Microsoft Teams-Desktop-App, die beide unter Linux ausgeführt werden.
> Wenn der Bot dieselbe Deep-Link-URL an eine sendet, wird die Registerkarte "Teams" auf der aktuellen Browserregisterkarte geöffnet, wenn der Benutzer `Action.OpenUrl` den Link auswählt. Es wird keine neue Browserregisterkarte geöffnet.

Die Abfrageparameter sind:

* `appId`&emsp;Die ID aus Ihrem Manifest; Beispiel: "fe4a8eba-2a31-4737-8e33-e5fae6fee194"
* `entityId`&emsp;Die ID für das Element auf der Registerkarte, die Sie beim Konfigurieren [der Registerkarte angegeben haben;](~/tabs/how-to/create-tab-pages/configuration-page.md) Beispiel: "tasklist123"
* `entityWebUrl`oder ein optionales Feld mit `subEntityWebUrl` &emsp; einer Fallback-URL, die verwendet werden soll, wenn der Client das Rendern der Registerkarte nicht unterstützt, z. B. " https://tasklist.example.com/123 oder https://tasklist.example.com/list123/task456 "
* `entityLabel`oder eine Bezeichnung für das Element auf Ihrer Registerkarte, die beim Anzeigen des #A0 verwendet werden soll, z. B. `subEntityLabel` &emsp; "Aufgabenliste 123" oder "Aufgabe 456"
* `context`&emsp;Ein JSON-Objekt, das die folgenden Felder enthält:
  * `subEntityId`&emsp;Eine ID für das Element _auf_ der Registerkarte; Beispiel: "task456"
  * `channelId`&emsp;Die Microsoft Teams-Kanal-ID, die im Registerkartenkontext verfügbar [ist;](~/tabs/how-to/access-teams-context.md) Beispiel: "19:cbe3683f25094106b826c9cada3afbe0@thread.skype". Diese Eigenschaft ist nur auf konfigurierbaren Registerkarten mit dem Bereich "Team" verfügbar. Es ist nicht in statischen Registerkarten verfügbar, die den Bereich "persönlich" haben.

Beispiele:

* Link zu einer konfigurierbaren Registerkarte selbst: `https://teams.microsoft.com/l/entity/fe4a8eba-2a31-4737-8e33-e5fae6fee194/tasklist123?webUrl=https://tasklist.example.com/123&label=Task List 123&context={"channelId": "19:cbe3683f25094106b826c9cada3afbe0@thread.skype"}`
* Link zu einem Aufgabenelement auf der konfigurierbaren Registerkarte: `https://teams.microsoft.com/l/entity/fe4a8eba-2a31-4737-8e33-e5fae6fee194/tasklist123?webUrl=https://tasklist.example.com/123/456&label=Task 456&context={"subEntityId": "task456","channelId": "19:cbe3683f25094106b826c9cada3afbe0@thread.skype"}`
* Link zu einer statischen Registerkarte selbst: `https://teams.microsoft.com/l/entity/fe4a8eba-2a31-4737-8e33-e5fae6fee194/tasklist123?webUrl=https://tasklist.example.com/123&label=Task List 123`
* Link zu einem Aufgabenelement auf der statischen Registerkarte: `https://teams.microsoft.com/l/entity/fe4a8eba-2a31-4737-8e33-e5fae6fee194/tasklist123?webUrl=https://tasklist.example.com/123/456&label=Task 456&context={"subEntityId": "task456"}`

> [!IMPORTANT]
> Stellen Sie sicher, dass alle Abfrageparameter ordnungsgemäß URI-codiert sind. Sie müssen die voransenden Beispiele anhand des letzten Beispiels befolgen:
> ```javascript
> var encodedWebUrl = encodeURI('https://tasklist.example.com/123/456&label=Task 456');
> var encodedContext = encodeURI('{"subEntityId": "task456"}');
> var taskItemUrl = 'https://teams.microsoft.com/l/entity/fe4a8eba-2a31-4737-8e33-e5fae6fee194/tasklist123?webUrl=' + encodedWebUrl + '&context=' + encodedContext;
> ```

### <a name="consuming-a-deep-link-from-a-tab"></a>Verwenden eines Deep-Links von einer Registerkarte

Beim Navigieren zu einem Deep-Link navigiert Microsoft Teams einfach zur Registerkarte und stellt einen Mechanismus über die Microsoft Teams-JavaScript-Bibliothek zum Abrufen der Id der Unterentität zur Verfügung, falls vorhanden.

Der [`microsoftTeams.getContext`](/javascript/api/@microsoft/teams-js#getcontext--context--context-----void-) Aufruf gibt einen Kontext zurück, der das Feld `subEntityId` enthält, wenn die Registerkarte über einen Deep-Link navigiert wird.

## <a name="deep-linking-from-your-tab"></a>Deep linking from your tab

Sie können von Ihrer Registerkarte aus eine Verknüpfung zu Inhalten in Teams erstellen. Dies ist hilfreich, wenn Ihre Registerkarte eine Verknüpfung zu anderen Inhalten in Teams erstellen muss, z. B. zu einem Kanal, einer Nachricht, einer anderen Registerkarte oder sogar zum Öffnen eines Planungsdialogfelds. Um einen Deeplink von Ihrer Registerkarte aus auszulösen, sollten Sie dies aufrufen:

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

## <a name="deep-linking-to-a-chat"></a>Deep linking to a chat

Sie können deep-Links zu privaten Chats zwischen Benutzern erstellen, indem Sie den Teilnehmersatz angeben. Wenn kein Chat mit den angegebenen Teilnehmern vorhanden ist, navigiert der Link den Benutzer zu einem leeren neuen Chat. Neue Chats werden im Entwurfsstatus erstellt, bis der Benutzer die erste Nachricht sendet. Andernfalls können Sie den Namen des Chats, sofern er noch nicht vorhanden ist, zusammen mit Text angeben, der in das Feld zum Verfassen des Benutzers eingefügt werden soll. Sie können sich dieses Feature als Verknüpfung für den Benutzer ausmalen, der manuell zu dem Chat navigiert oder den Chat erstellt und dann die Nachricht eintippt.

Wenn Sie beispielsweise ein Office 365-Benutzerprofil von Ihrem Bot als Karte zurückgeben, kann dieser Deep Link dem Benutzer ermöglichen, einfach mit dieser Person zu chatten.

### <a name="generating-a-deep-link-to-a-chat"></a>Generieren eines Deep-Links zu einem Chat

Verwenden Sie dieses Format für einen Deep-Link, den Sie in einer Bot-, Connector- oder Messaging-Erweiterungskarte verwenden können:

`https://teams.microsoft.com/l/chat/0/0?users=<user1>,<user2>,...&topicName=<chat name>&message=<precanned text>`

Beispiel: `https://teams.microsoft.com/l/chat/0/0?users=joe@contoso.com,bob@contoso.com&topicName=Prep%20For%20Meeting%20Tomorrow&message=Hi%20folks%2C%20kicking%20off%20a%20chat%20about%20our%20meeting%20tomorrow`

Die Abfrageparameter sind:

* `users`: Die durch Kommas getrennte Liste der Benutzer-IDs, die die Teilnehmer des Chats darstellen. Der Benutzer, der die Aktion ausführt, ist immer als Teilnehmer enthalten. Derzeit unterstützt das Feld "Benutzer-ID" den Azure AD UserPrincipalName, in der Regel nur eine E-Mail-Adresse.
* `topicName`: Ein optionales Feld für den Anzeigenamen des Chats bei einem Chat mit drei oder mehr Benutzern. Wenn dieses Feld nicht angegeben ist, basiert der Anzeigename des Chats auf den Namen der Teilnehmer.
* `message`: Ein optionales Feld für den Nachrichtentext, den Sie in das Feld zum Verfassen des aktuellen Benutzers einfügen möchten, während sich der Chat im Entwurfszustand befindet.

Um diesen Deep-Link mit Ihrem Bot zu verwenden, können Sie dies als das URL-Ziel in der Schaltfläche Ihrer Karte angeben oder auf die Aktion durch den `openUrl` Aktionstyp tippen.

### <a name="generating-a-deep-link-to-a-call"></a>Generieren eines DeepLinks zu einem Anruf

Verwenden Sie dieses Format für einen Deep-Link, den Sie in einer Bot-, Connector- oder Messaging-Erweiterungskarte verwenden können:

`https://teams.microsoft.com/l/call/0/0?users=<user1>,<user2>`

Beispiel: `https://teams.microsoft.com/l/call/0/0?users=joe@contoso.com,bob@contoso.com&topicName=Prep%20For%20Meeting%20Tomorrow&message=Hi%20folks%2C%20kicking%20off%20a%20chat%20about%20our%20meeting%20tomorrow`

Die Abfrageparameter sind:

* `users`: Die durch Kommas getrennte Liste der Benutzer-IDs, die die Teilnehmer des Anrufs darstellen. Der Benutzer, der die Aktion ausführt, ist immer als Teilnehmer enthalten. Derzeit unterstützt das Feld "Benutzer-ID" den Azure AD UserPrincipalName, in der Regel nur eine E-Mail-Adresse.

## <a name="linking-to-the-scheduling-dialog"></a>Verknüpfen mit dem Planungsdialogfeld

> [!Note]
> Dieses Feature befindet sich derzeit in der Entwicklervorschau.

Sie können Deep-Links zum integrierten Planungsdialogfeld von Teams erstellen. Dies ist besonders hilfreich, wenn Ihre App dem Benutzer hilft, Kalender- oder Zeitplanungsaufgaben auszuführen.

### <a name="generating-a-deep-link-to-the-scheduling-dialog"></a>Generieren eines DeepLinks zum Planungsdialogfeld

Verwenden Sie das folgende Format für einen Deep-Link, den Sie in einer Bot-, Connector- oder Messaging-Erweiterungskarte verwenden können: `https://teams.microsoft.com/l/meeting/new?subject=<meeting subject>&startTime=<date>&endTime=<date>&content=<content>&attendees=<user1>,<user2>,<user3>,...`

Beispiel: `https://teams.microsoft.com/l/meeting/new?subject=test%20subject&attendees=joe@contoso.com,bob@contoso.com&startTime=10%2F24%2F2018%2010%3A30%3A00&endTime=10%2F24%2F2018%2010%3A30%3A00&content=test%3Acontent`

Die Abfrageparameter sind:

* `attendees`: Die optionale durch Kommas getrennte Liste der Benutzer-IDs, die die Teilnehmer der Besprechung darstellen. Der Benutzer, der die Aktion ausführen, ist der Besprechungsorganisator. Das Feld "Benutzer-ID" unterstützt derzeit nur den Azure AD UserPrincipalName, in der Regel eine E-Mail-Adresse.
* `startTime`: Die optionale Startzeit des Ereignisses. Dies sollte im langen [ISO 8601-Format](https://en.wikipedia.org/wiki/ISO_8601)vorliegen, z. B. "2018-03-12T23:55:25+02:00".
* `endTime`: Die optionale Endzeit des Ereignisses, auch im ISO 8601-Format.
* `subject`: Ein optionales Feld für den Besprechungsthema.
* `content`: Ein optionales Feld für das Feld "Besprechungsdetails".

Derzeit wird die Angabe des Speicherorts nicht unterstützt. Sie müssen den UTC-Offset angeben, d. h. Zeitzonen beim Generieren der Start- und Endzeiten.

Um diesen Deep-Link mit Ihrem Bot zu verwenden, können Sie dies als das URL-Ziel in der Schaltfläche Ihrer Karte angeben oder auf die Aktion durch den `openUrl` Aktionstyp tippen.
