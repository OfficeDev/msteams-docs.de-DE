---
title: Erstellen von Deep-Links
description: In diesem Artikel erfahren Sie, wie Sie Deep-Links erstellen und in Ihren Microsoft Teams-Apps mit Registerkarten navigieren.
ms.topic: how-to
ms.localizationpriority: high
ms.openlocfilehash: 463a7f37ca481058133ca5dbd646225f02bab4ab
ms.sourcegitcommit: d8183bad448990f7c79b1956a6c9761c27712b4c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/29/2022
ms.locfileid: "67452360"
---
# <a name="create-deep-links"></a>Erstellen von Deep-Links

Deep-Links sind ein Navigationsinstrument, mit dem Sie Informationen und Features für Benutzer in Microsoft Teams und Microsoft Teams-Apps verlinken können. Das Erstellen von Deep-Links kann u.a. in den folgenden Szenarien nützlich sein:

* Navigieren des Benutzers zum Inhalt auf einer der Registerkarten Ihrer App. Ihre App kann beispielsweise über einen Bot verfügen, der Nachrichten sendet, welche den Benutzer in Bezug auf eine wichtige Aktivität benachrichtigen. Wenn der Benutzer auf die Benachrichtigung tippt, navigiert der Deeplink zur Registerkarte, sodass der Benutzer weitere Details zur Aktivität anzeigen kann.
* Ihre App automatisiert oder vereinfacht bestimmte Benutzeraufgaben. Sie können einen Chat erstellen oder eine Besprechung planen, indem Sie die Deep-Links mit den erforderlichen Parametern vorab auffüllen. Benutzer müssen die Informationen nicht manuell eingeben.

Das Microsoft Teams JavaScript-Client-SDK (TeamsJS) vereinfacht den Navigationsprozess. In vielen Szenarien, z. B. beim Navigieren zu Inhalten und Informationen auf Ihrer Registerkarte oder beim Starten eines Chatdialogfelds. Das SDK bietet typisierte APIs, die eine verbesserte Benutzererfahrung bieten und die Verwendung von Deep-Links ersetzen können. Diese APIs werden für Microsoft Teams-Apps empfohlen, die u. U. auf anderen Hosts ausgeführt werden (Outlook, Office), da sie auch eine Möglichkeit bieten, zu überprüfen, ob die verwendete Funktion von diesem Host unterstützt wird. In den folgenden Abschnitten finden Sie Informationen zur Erstellung von Deep-Links sowie zu den Änderungen in Szenarien, in denen dies erforderlich war, nach der Veröffentlichung von TeamsJS V2.

[!INCLUDE [sdk-include](~/includes/sdk-include.md)]

> [!NOTE]
> Das Verhalten von Deep-Links hängt von einer Reihe von Faktoren ab. In der folgenden Liste wird das Verhalten von Deep-Links in Bezug auf Microsoft Teams-Entitäten beschrieben.
>
> **Registerkarte**:  
> ✔ Navigiert direkt zur Deep-Link-URL.
>
> **Bot**:  
> ✔ Deep-Link im Kartentext: Wird zuerst im Browser geöffnet.  
> ✔ Deep-Link zu OpenURL-Aktion in adaptiver Karte hinzugefügt: Navigiert direkt zur Deep-Link-URL.  
> ✔ Hyperlinkmarkdowntext auf der Karte: Wird zuerst im Browser geöffnet.  
>
> **Chat**:  
> ✔ Textnachrichten-Hyperlink-Markdown: Navigiert direkt zur Deep-Link-URL.  
> ✔ In allgemeine Chatunterhaltung eingefügter Link: Navigiert direkt zur Deep-Link-URL.
>
>
>Das Navigationsverhalten einer Microsoft Teams-App, die auf Microsoft 365 (Outlook/Office) erweitert wird, hängt von zwei Faktoren ab:
>
> * Das Ziel, auf das der Deep-Link verweist.
> * Der Host, auf dem die Teams-App ausgeführt wird.
>
> Wenn die Microsoft Teams-App auf dem Host ausgeführt wird, auf den der Deep-Link ausgerichtet ist, wird Ihre App direkt auf dem Host geöffnet. Wenn die Microsoft Teams-App jedoch auf einem anderen Host ausgeführt wird, als jenem, auf den der Deep-Link ausgerichtet ist, wird die App zuerst im Browser geöffnet.

## <a name="deep-link-to-your-tab"></a>Deep-Link-Verknüpfung mit Ihrer Registerkarte

Sie können Deep-Links zu Entitäten in Microsoft Teams-Apps erstellen. Diese Methode wird verwendet, um Links zu erstellen, die zu Inhalten und Informationen auf Ihrer Registerkarte führen. Wenn Ihre Registerkarte beispielsweise eine Aufgabenliste enthält, können Teammitglieder Links zu einzelnen Aufgaben erstellen und weitergeben. Wenn Sie den Link auswählen, navigieren Sie darüber zu Ihrer Registerkarte, die sich auf das jeweilige Element konzentriert.

# <a name="teamsjs-v2"></a>[TeamsJS v2](#tab/teamsjs-v2)

Um dies zu implementieren, fügen Sie jedem Element eine Aktion **Link kopieren** auf die Art und Weise hinzu, wie es Ihrer Benutzeroberfläche am ehesten entspricht. Wenn der Benutzer diese Aktion ausführt, wird [pages.shareDeepLink()](/javascript/api/@microsoft/teams-js/pages?view=msteams-client-js-latest#@microsoft-teams-js-pages-sharedeeplink&preserve-view=true) aufgerufen, um ein Dialogfeld mit einem Link anzuzeigen, den der Benutzer in die Zwischenablage kopieren kann. Wenn Sie diesen Aufruf ausführen, übergeben Sie eine ID für Ihr Element. Sie erhalten sie wieder im [Kontext](~/tabs/how-to/access-teams-context.md), wenn dem Link gefolgt und Ihre Registerkarte neu geladen wird.

```javascript
pages.shareDeepLink({ subPageId: <subPageId>, subPageLabel: <subPageLabel>, subPageWebUrl: <subPageWebUrl> })
```

Sie müssen die Felder durch die entsprechenden Informationen ersetzen:

* `subPageId`: Ein eindeutiger Bezeichner für das Element auf Ihrer Seite, zu dem Sie eine Deep-Link-Verknüpfung erstellen.
* `subPageLabel`: Eine Beschriftung für das Element, das zum Anzeigen des Deeplinks verwendet werden soll.
* `subPageWebUrl`: Eine Fallback-URL, die verwendet werden soll, wenn der Client die Seite nicht rendern kann.

Weitere Informationen finden Sie unter [pages.shareDeepLink()](/javascript/api/@microsoft/teams-js/pages?view=msteams-client-js-latest#@microsoft-teams-js-pages-sharedeeplink&preserve-view=true).

# <a name="teamsjs-v1"></a>[TeamsJS v1](#tab/teamsjs-v1)

Um dies zu implementieren, fügen Sie jedem Element eine Aktion **Link kopieren** hinzu, unabhängig davon, welche Art und Weise Ihrer Benutzeroberfläche am ehesten entspricht. Wenn der Benutzer diese Aktion ausführt, rufen Sie `shareDeepLink()` auf, um ein Dialogfeld mit einem Link anzuzeigen, den der Benutzer in die Zwischenablage kopieren kann. Bei diesem Aufruf übermitteln Sie auch eine ID für Ihr Element, die Sie im [Kontext](~/tabs/how-to/access-teams-context.md)zurückerhalten, wenn dem Link gefolgt wird und Ihre Registerkarte neu geladen wird.

```javascript
microsoftTeams.shareDeepLink({ subEntityId: <subEntityId>, subEntityLabel: <subEntityLabel>, subEntityWebUrl: <subEntityWebUrl> })
```

Sie müssen die Felder durch die entsprechenden Informationen ersetzen:

* `subEntityId`: Ein eindeutiger Bezeichner für das Element auf Ihrer Registerkarte, zu dem Sie eine Deeplink-Verknüpfung erstellen.
* `subEntityLabel`: Eine Beschriftung für das Element, das zum Anzeigen des Deeplinks verwendet werden soll.
* `subEntityWebUrl`: Ein optionales Feld mit einer Fallback-URL, das verwendet werden soll, wenn der Client das Rendern der Registerkarte nicht unterstützt.

---

Alternativ können Sie Deeplinks auch programmgesteuert unter Verwendung des später in diesem Artikel angegebenen Formats generieren. Sie können Deeplinks in [Bot](~/bots/what-are-bots.md)- und [Connector](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md)-Nachrichten verwenden, die Benutzer über Änderungen an Ihrer Registerkarte oder an darin enthaltenen Elementen informieren.

> [!NOTE]
> Dieser Deeplink unterscheidet sich von den Links, die vom Menüelement **Link zur Registerkarte kopieren** bereitgestellt werden. Dadurch wird lediglich ein Deeplink generiert, der auf diese Registerkarte verweist.

>[!IMPORTANT]
> Derzeit funktioniert shareDeepLink nicht auf mobilen Plattformen.

### <a name="consume-a-deep-link-from-a-tab"></a>Verwenden eines Deeplinks von einer Registerkarte

Beim Navigieren zu einem Deep-Link navigiert Microsoft Teams einfach zur Registerkarte und bietet über die Microsoft Teams-JavaScript-Bibliothek einen Mechanismus zum Abrufen der Unterseiten-ID, sofern diese vorhanden ist.

Der [`app.getContext()`](/javascript/api/@microsoft/teams-js/app?view=msteams-client-js-latest#@microsoft-teams-js-app-getcontext&preserve-view=true)-Aufruf (`microsoftTeams.getContext()`) in TeamsJS v1) gibt eine Zusage zurück, die mit dem Kontext aufgelöst wird, der die `subPageId`-Eigenschaft (subEntityId für TeamsJS v1) enthält, wenn über einen Deep-Link zur Registerkarte navigiert wird. Weitere Informationen finden Sie unter [PageInfo-Schnittstelle](/javascript/api/@microsoft/teams-js/app?view=msteams-client-js-latest#@microsoft-teams-js-app-pageinfo&preserve-view=true).

### <a name="generate-a-deep-link-to-your-tab"></a>Generieren eines Deeplinks zu Ihrer Registerkarte

Es wird zwar empfohlen, einen Deep-Link zu Ihrer Registerkarte mit `shareDeepLink()` zu generieren, aber es ist auch möglich, einen manuell zu erstellen.

> [!NOTE]
>
> * Persönliche Registerkarten haben einen `personal` Bereich, während Kanal- und Gruppenregisterkarten `team` oder `group` Bereiche nutzen. Die Syntax der beiden Registerkartentypen unterscheidet sich geringfügig, da nur dem Kontextobjekt der konfigurierbaren Registerkarte eine `channel` Eigenschaft zugeordnet ist. Weitere Informationen zu Registerkartenbereichen finden Sie in der [Manifest](~/resources/schema/manifest-schema.md)-Referenz.
> * Deeplinks funktionieren nur ordnungsgemäß, wenn die Registerkarte mithilfe der Bibliothek v0.4 oder höher konfiguriert wurde und daher eine Entitäts-ID vorhanden ist. Deeplinks zu Registerkarten ohne Entitäts-IDs navigieren weiterhin zur Registerkarte, können aber die Unterentitäts-ID nicht auf der Registerkarte bereitstellen.

Verwenden Sie das folgende Format für einen Deep-Link, den Sie in einem Bot, Connector oder einer Nachrichtenerweiterungskarte verwenden können:

`https://teams.microsoft.com/l/entity/<appId>/<entityId>?webUrl=<entityWebUrl>&label=<entityLabel>&context=<context>`

> [!NOTE]
> Wenn der Bot eine Nachricht `TextBlock` mit einem Deeplink sendet, wird eine neue Browserregisterkarte geöffnet, wenn der Benutzer den Link auswählt. Dies geschieht in Chrome und in der Teams Desktop-App, die beide unter Linux ausgeführt werden.
> Wenn der Bot dieselbe Deeplink-URL an eine(n) `Action.OpenUrl` sendet, wird die Registerkarte Teams in der aktuellen Browserregisterkarte geöffnet, wenn der Benutzer den Link auswählt. Eine neue Browserregisterkarte wird nicht geöffnet.

<!--- TBD: Edit this article.
* Admonitions/alerts seem to be overused. 
* An important alert at the end of this table does not make sense. Also, it has a code snippet inside it.
* List items in the table are not formatted well in output.
* Some headings use -ing verbs.
* Example values and some URLs should be in backticks and not emphasized.
* Codeblock are missing language.
* Check for markdownlint errors.
* Table with just a row isn't really needed. Provide the content without tabulating it.
--->

Die Abfrageparameter sind:

| Parametername | Beschreibung | Beispiel |
|:------------|:--------------|:---------------------|
| `appId`&emsp; | Die ID aus dem Teams Admin Center. |fe4a8eba-2a31-4737-8e33-e5fae6fee194|
| `entityId`&emsp; | Die ID für das Element auf der Registerkarte, die Sie beim [Konfigurieren der Registerkarte](~/tabs/how-to/create-tab-pages/configuration-page.md) angegeben haben. Verwenden Sie beim Generieren einer URL für das Deep Linking weiterhin entityID als Parameternamen in der URL. Beim Konfigurieren der Registerkarte bezieht sich das Kontextobjekt auf die entityID als {page.id}. |Tasklist123|
| `entityWebUrl` oder `subEntityWebUrl`&emsp; | Ein optionales Feld mit einer Fallback-URL, das verwendet werden soll, wenn der Client das Rendern der Registerkarte nicht unterstützt. | `https://tasklist.example.com/123` oder `https://tasklist.example.com/list123/task456` |
| `entityLabel` oder `subEntityLabel`&emsp; | Eine Beschriftung für das Element auf Ihrer Registerkarte, die beim Anzeigen des Deeplinks verwendet werden soll. | Task List 123 oder Task 456 |
| `context.subEntityId`&emsp; | Eine ID für das Element auf der Registerkarte. Verwenden Sie beim Generieren einer URL für das Deep Linking weiterhin subEntityId als Parameternamen in der URL. Beim Konfigurieren der Registerkarte bezieht sich das Kontextobjekt auf die subEntityID als subPageID. |Task456 |
| `context.channelId`&emsp; | Microsoft Teams-Kanal-ID, die auf der Registerkarte [Kontext](~/tabs/how-to/access-teams-context.md)verfügbar ist. Diese Eigenschaft ist nur in konfigurierbaren Registerkarten mit einem **Team**-Bereich verfügbar. Sie ist in statischen Registerkarten, die einen **persönlichen** Bereich haben, nicht verfügbar.| 19:cbe3683f25094106b826c9cada3afbe0@thread.skype |
| `chatId`&emsp; | ChatId, die auf der Registerkarte [Kontext](~/tabs/how-to/access-teams-context.md) für Gruppen- und Besprechungschats verfügbar ist | 17:b42de192376346a7906a7dd5cb84b673@thread.v2 |
| `contextType`&emsp; |  Chat ist der einzige unterstützte contextType für Besprechungen. | Chat |

**Beispiele**:

* Link zu einer eigentlichen statischen (persönlichen) Registerkarte:

    >`https://teams.microsoft.com/l/entity/fe4a8eba-2a31-4737-8e33-e5fae6fee194/tasklist123?webUrl=https://tasklist.example.com/123&label=Task List 123`

* Link zu einem Aufgabenelement auf der statischen (persönlichen) Registerkarte:

    >`https://teams.microsoft.com/l/entity/fe4a8eba-2a31-4737-8e33-e5fae6fee194/tasklist123?webUrl=https://tasklist.example.com/123/456&label=Task 456&context={"subEntityId": "task456"}`

* Link zu der jeweiligen konfigurierbaren Registerkarte: 

    >`https://teams.microsoft.com/l/entity/fe4a8eba-2a31-4737-8e33-e5fae6fee194/tasklist123?webUrl=https://tasklist.example.com/123&label=Task List 123&context={"channelId": "19:cbe3683f25094106b826c9cada3afbe0@thread.skype"}`

* Link zu einem Aufgabenelement auf der konfigurierbaren Registerkarte: 

    >`https://teams.microsoft.com/l/entity/fe4a8eba-2a31-4737-8e33-e5fae6fee194/tasklist123?webUrl=https://tasklist.example.com/123/456&label=Task 456&context={"subEntityId": "task456","channelId": "19:cbe3683f25094106b826c9cada3afbe0@thread.skype"}`

* Link zu einer Registerkarten-App, die einem Besprechungs- oder Gruppenchat hinzugefügt wurde:

    >`https://teams.microsoft.com/l/entity/fe4a8eba-2a31-4737-8e33-e5fae6fee194/tasklist123?webUrl=https://tasklist.example.com/123/456&label=Task 456?context={"chatId": "17:b42de192376346a7906a7dd5cb84b673@thread.v2","contextType":"chat"}`

> [!IMPORTANT]
> Stellen Sie sicher, dass alle Abfrageparameter ordnungsgemäß URI-codiert sind. Sie müssen den vorangehenden Beispielen anhand des letzten Beispiels folgen:
>
> ```javascript
> var encodedWebUrl = encodeURI('https://tasklist.example.com/123/456&label=Task 456');
> var encodedContext = encodeURI('{"subEntityId": "task456"}');
> var taskItemUrl = 'https://teams.microsoft.com/l/entity/fe4a8eba-2a31-4737-8e33-e5fae6fee194/tasklist123?webUrl=' + encodedWebUrl + '&context=' + encodedContext;
> ```

## <a name="navigation-from-your-tab"></a>Navigation über Ihre Registerkarte

Sie können mithilfe von TeamsJS oder Deep-Links von Ihrer Registerkarte aus zu Inhalten in Microsoft Teams navigieren. Dies ist nützlich, wenn andere Inhalte in Microsoft Teams über Ihre Registerkarte verlinkt werden sollen, z. B. ein Kanal, eine Nachricht, eine andere Registerkarte oder sogar ein Planungsdialogfeld geöffnet werden soll. Früher war für die Navigation u. U. ein Deep-Link erforderlich, dies ist jetzt hingegen in vielen Fällen mithilfe des SDK möglich. In den folgenden Abschnitten werden beide Methoden erläutert, es wird jedoch empfohlen, wo möglich die typisierten Funktionen des SDK zu verwenden.

Einer der Vorteile der Verwendung von TeamsJS, insbesondere für Microsoft Teams-Apps, die eventuell auf anderen Hosts (Outlook und Office) ausgeführt werden, besteht darin, dass überprüft werden kann, ob der Host die Funktion unterstützt, die Sie verwenden möchten. Um die Unterstützung einer Funktion durch einen Host zu überprüfen, können Sie die `isSupported()`-Funktion verwenden, die dem Namespace der API zugeordnet ist. Das TeamsJS-SDK organisiert APIs in Funktionen mithilfe von Namespaces. Vor der Verwendung einer API im `pages`-Namespace können Sie beispielsweise den zurückgegebenen booleschen Wert aus `pages.isSupported()` überprüfen und die entsprechende Aktion im Kontext der App und App-Benutzeroberfläche ausführen.  

Weitere Informationen zu Funktionen und den APIs in TeamsJS finden Sie unter [Erstellen von Registerkarten und anderen gehosteten Umgebungen mit dem Microsoft Teams JavaScript-Client-SDK](~/tabs/how-to/using-teams-client-sdk.md#apis-organized-into-capabilities).

### <a name="navigate-within-your-app"></a>Navigation in Ihrer App

Es ist möglich, in einer App mit TeamsJS zu navigieren. Der folgende Code veranschaulicht, wie Sie zu einer bestimmten Entität innerhalb Ihrer Microsoft Teams-App navigieren.

# <a name="teamsjs-v2"></a>[TeamsJS v2](#tab/teamsjs-v2)

Sie können die Navigation von Ihrer Registerkarte aus mithilfe der [pages.navigateToApp()](/javascript/api/@microsoft/teams-js/pages?view=msteams-client-js-latest#@microsoft-teams-js-pages-navigatetoapp&preserve-view=true)-Funktion auslösen, wie im folgenden Code dargestellt:

```javascript
if (pages.isSupported()) {
  const navPromise = pages.navigateToApp({ appId: <appId>, pageId: <pageId>, webUrl: <webUrl>, subPageId: <subPageId>, channelId:<channelId>});
  navPromise.
     then((result) => {/*Successful navigation*/}).
     catch((error) => {/*Failed navigation*/});
}
else { /* handle case where capability isn't supported */ }
```

Weitere Informationen zur Verwendung der pages-Funktion finden Sie unter [pages.navigateToApp()](/javascript/api/@microsoft/teams-js/pages?view=msteams-client-js-latest#@microsoft-teams-js-pages-navigatetoapp&preserve-view=true) und im [pages](/javascript/api/@microsoft/teams-js/pages?view=msteams-client-js-latest&preserve-view=true)-Namespace für andere Navigationsoptionen. Bei Bedarf ist es auch möglich, einen Deep-Link direkt mithilfe der [app.openLink()](/javascript/api/@microsoft/teams-js/app?view=msteams-client-js-latest#@microsoft-teams-js-app-openlink&preserve-view=true)-Funktion zu öffnen.

# <a name="teamsjs-v1"></a>[TeamsJS v1](#tab/teamsjs-v1)

Um einen Deep-Link von Ihrer Registerkarte aus auszulösen, rufen Sie Folgendes auf:

```javascript
microsoftTeams.executeDeepLink(/*deepLink*/);
```

---

### <a name="open-a-scheduling-dialog"></a>Öffnen eines Planungsdialogfelds

> [!NOTE]
> Um den Planungsdialog in Teams zu öffnen, müssen Entwickler weiterhin die ursprüngliche Deep-Link-URL-basierte Methode verwenden, da Teams die Kalenderfunktion noch nicht unterstützt.

Weitere Informationen zum Arbeiten mit dem Kalender finden Sie in der API-Referenzdokumentation unter [calendar](/javascript/api/@microsoft/teams-js/calendar?view=msteams-client-js-latest&preserve-view=true)-Namespace.

# <a name="teamsjs-v2"></a>[TeamsJS v2](#tab/teamsjs-v2)

```javascript
// Open a scheduling dialog from your tab
if(calendar.isSupported()) {
   const calendarPromise = calendar.composeMeeting({
      attendees: ["joe@contoso.com", "bob@contoso.com"],
      content: "test content",
      endTime: "2018-10-24T10:30:00-07:00",
      startTime: "2018-10-24T10:00:00-07:00",
      subject: "test subject"});
   calendarPromise.
      then((result) => {/*Successful operation*/}).
      catch((error) => {/*Unsuccessful operation*/});
}
else { /* handle case where capability isn't supported */ }
```

# <a name="teamsjs-v1"></a>[TeamsJS v1](#tab/teamsjs-v1)

```javascript
// Open a scheduling dialog from your tab
microsoftTeams.executeDeepLink("https://teams.microsoft.com/l/meeting/new?subject=test%20subject&attendees=joe@contoso.com,bob@contoso.com&startTime=10%2F24%2F2018%2010%3A30%3A00&endTime=10%2F24%2F2018%2010%3A30%3A00&content=test%3Acontent");
```

---

Alternativ können Sie Deep-Links zu dem in Teams integrierten Planungsdialogfeld erstellen.

#### <a name="generate-a-deep-link-to-the-scheduling-dialog"></a>Generieren eines Deeplinks zum Planungsdialogfeld

Es wird zwar empfohlen, die typisierten APIs von TeamsJS zu verwenden, Deep-Links zu dem in Microsoft Teams integrierten Planungsdialogfeld können aber auch manuell erstellt werden. Verwenden Sie das folgende Format für einen Deep-Link, den Sie auf einer Bot-, Connector- oder Nachrichtenerweiterungskarte verwenden können: `https://teams.microsoft.com/l/meeting/new?subject=<meeting subject>&startTime=<date>&endTime=<date>&content=<content>&attendees=<user1>,<user2>,<user3>,...`

Beispiel: `https://teams.microsoft.com/l/meeting/new?subject=test%20subject&attendees=joe@contoso.com,bob@contoso.com&startTime=10%2F24%2F2018%2010%3A30%3A00&endTime=10%2F24%2F2018%2010%3A30%3A00&content=test%3Acontent`

> [!NOTE]
> Die Suchparameter unterstützen kein `+` Signal anstelle von Leerzeichen (``). Stellen Sie sicher, dass der URI-Codierungscode `%20` für Leerzeichen ausgibt, z. B. `?subject=test%20subject` ist gut, aber `?subject=test+subject` ist schlecht.

Die Abfrageparameter sind:

* `attendees`: Die optionale durch Kommas getrennte Liste der Benutzer-IDs, auf der die Teilnehmer der Besprechung angegeben sind. Der Benutzer, der die Aktion ausführt, ist der Besprechungsorganisator. Derzeit unterstützt das Feld „Benutzer-ID“ nur den Azure AD UserPrincipalName, in der Regel eine E-Mail-Adresse.
* `startTime`: Die optionale Startzeit des Ereignisses. Diese sollte im [langen ISO 8601-Format](https://en.wikipedia.org/wiki/ISO_8601)vorliegen, wie z. B. *2018-03-12T23:55:25+02:00*.
* `endTime`: Die optionale Endzeit des Ereignisses, ebenfalls im ISO 8601-Format.
* `subject`: Ein optionales Feld für den Betreff der Besprechung.
* `content`: Ein optionales Feld für das Besprechungsdetails-Feld.

> [!NOTE]
> Derzeit wird die Angabe des Standorts nicht unterstützt. Sie müssen den UTC-Offset angeben. Dies bedeutet Zeitzonen, wenn Sie Ihre Start- und Endzeiten generieren.

Um diesen Deeplink mit Ihrem Bot zu verwenden, können Sie diesen als URL-Ziel auf der Schaltfläche Ihrer Karte angeben oder über den Aktionstyp `openUrl` auf die Aktion tippen.

### <a name="open-an-app-install-dialog"></a>Öffnen eines Dialogfelds für die App-Installation

Sie können ein Dialogfeld für die App-Installation über Ihre Microsoft Teams-App öffnen, wie im folgenden Code dargestellt.

# <a name="teamsjs-v2"></a>[TeamsJS v2](#tab/teamsjs-v2)

```javascript
// Open an app install dialog from your tab
if(appInstallDialog.isSupported()) {
    const dialogPromise = appInstallDialog.openAppInstallDialog({ appId: <appId>});
    dialogPromise.
      then((result) => {/*Successful operation*/}).
      catch((error) => {/*Unsuccessful operation*/});
}
else { /* handle case where capability isn't supported */ }
```

Weitere Informationen zum Installationsdialogfeld finden Sie in der API-Referenzdokumentation in der Funktion [appInstallDialog.openAppInstallDialog()](/javascript/api/@microsoft/teams-js/appinstalldialog?view=msteams-client-js-latest#@microsoft-teams-js-appinstalldialog-openappinstalldialog&preserve-view=true).

# <a name="teamsjs-v1"></a>[TeamsJS v1](#tab/teamsjs-v1)

```javascript
// Open an app install dialog from your tab
microsoftTeams.executeDeepLink("https://teams.microsoft.com/l/app/f46ad259-0fe5-4f12-872d-c737b174bcb4");
```

---

### <a name="navigate-to-a-chat"></a>Navigieren zu einem Chat

Sie können mit TeamsJS private Chats zwischen Benutzern erstellen oder zu diesen navigieren, indem Sie die Teilnehmergruppe angeben. Wenn kein Chat mit den angegebenen Teilnehmern vorhanden ist, wird der Benutzer zu einem leeren neuen Chat geleitet. Neue Chats werden im Entwurfsstatus erstellt, bis der Benutzer die erste Nachricht sendet. Andernfalls können Sie den Namen des Chats angeben, falls er noch nicht vorhanden ist, zusammen mit Text, der in das Verfassen-Feld des Benutzers eingefügt werden soll. Sie können sich dieses Feature als eine Verknüpfung vorstellen, mit der der Benutzer manuell zum Chat navigieren oder diesen erstellen und dann die Nachricht eingeben kann.

Wenn Sie beispielsweise ein Office 365-Benutzerprofil von Ihrem Bot als Karte ausgeben, kann der Benutzer über diesen Deeplink einfach mit dieser Person chatten. Im folgenden Beispiel wird veranschaulicht, wie eine Chatnachricht für eine Gruppe von Teilnehmern mit einer ersten Nachricht geöffnet wird.

```javascript
if(chat.isSupported()) {
    const chatPromise = chat.openGroupChat({ users: ["joe@contoso.com","bob@contoso.com"], topic: "Prep For Meeting Tomorrow", message: "Hi folks kicking off chat about our meeting tomorrow"});
    chatPromise.
      then((result) => {/*Successful operation*/}).
      catch((error) => {/*Unsuccessful operation*/});
}
else { /* handle case where capability isn't supported */ }
```

Die Verwendung der typisierten APIs wird zwar empfohlen, alternativ können Sie aber auch das folgende Format für einen manuell erstellten Deep-Link verwenden, der in einer Bot-, Connector- oder Nachrichtenerweiterungskarte verwendet werden kann:

`https://teams.microsoft.com/l/chat/0/0?users=<user1>,<user2>,...&topicName=<chat name>&message=<precanned text>`

Beispiel: `https://teams.microsoft.com/l/chat/0/0?users=joe@contoso.com,bob@contoso.com&topicName=Prep%20For%20Meeting%20Tomorrow&message=Hi%20folks%2C%20kicking%20off%20a%20chat%20about%20our%20meeting%20tomorrow`

Die Abfrageparameter sind:

* `users`: Die durch Kommas getrennte Liste der Benutzer-IDs, auf der die Chat-Teilnehmer angegeben sind. Der Benutzer, der die Aktion ausführt, ist immer als Teilnehmer enthalten. Derzeit unterstützt das Feld „Benutzer-ID“ das Microsoft Azure Active Directory (Azure AD) UserPrincipalName, wie z. B. nur eine E-Mail-Adresse.
* `topicName`: Ein optionales Feld für den Anzeigenamen eines Chats mit drei oder mehr Benutzern. Wenn dieses Feld nicht angegeben wird, basiert der Bildschirmname des Chats auf den Namen der Teilnehmer.
* `message`: Ein optionales Feld für den Nachrichtentext, den Sie in das Feld zum Verfassen des aktuellen Benutzers einfügen möchten, während sich der Chat im Entwurfszustand befindet.

Um diesen Deeplink mit Ihrem Bot zu verwenden, geben Sie diesen als URL-Ziel auf der Schaltfläche Ihrer Karte an, oder tippen Sie über den Aktionstyp `openUrl` auf die Aktion.

### <a name="generate-deep-links-to-channel-conversation"></a>Erzeugen von Deep Links zu Channel-Konversationen

Verwenden Sie dieses Deep-Link-Format, um zu einer bestimmten Konversation innerhalb eines Kanal-Threads zu navigieren:

`https://teams.microsoft.com/l/message/<channelId>/<parentMessageId>?tenantId=<tenantId>&groupId=<groupId>&parentMessageId=<parentMessageId>&teamName=<teamName>&channelName=<channelName>&createdTime=<createdTime>`

Beispiel: `https://teams.microsoft.com/l/message/<channelId>/1648741500652?tenantId=<tenantId>&groupId=<groupId>&parentMessageId=1648741500652&teamName=<teamName>&channelName=<channelName>&createdTime=1648741500652`

Die Abfrageparameter sind:

* `channelId`: Kanal-ID der Unterhaltung. Beispiel: `19:3997a8734ee5432bb9cdedb7c432ae7d@thread.tacv2`.
* `tenantId`: Mandanten-ID, z. B. `0d9b645f-597b-41f0-a2a3-ef103fbd91bb`.
* `groupId`: Gruppen-ID der Datei. Beispiel: `3606f714-ec2e-41b3-9ad1-6afb331bd35d`.
* `parentMessageId`: ID der übergeordneten Nachricht der Konversation.
* `teamName`: Name des Teams.
* `channelName`: Name des Kanals des Teams.

> [!NOTE]
> Sie können `channelId` und `groupId` in der URL dieses Kanals sehen.

### <a name="generate-deep-links-to-file-in-channel"></a>Generieren von Deeplinks zu Dateien im Kanal

Das folgende Deep Link-Format kann in einem Bot, Connector oder einer Nachrichtenerweiterungskarte verwendet werden:

`https://teams.microsoft.com/l/file/<fileId>?tenantId=<tenantId>&fileType=<fileType>&objectURL=<objectURL>&baseUrl=<baseURL>&serviceName=<Name>&threadId=<threadId>&groupId=<groupId>`

Die Abfrageparameter sind:

* `fileId`: Eindeutige Datei-ID aus Sharepoint Online, auch bekannt als `sourcedoc`. Beispiel:`1FA202A5-3762-4F10-B550-C04F81F6ACBD`.
* `tenantId`: Mandanten-ID, z. B. `0d9b645f-597b-41f0-a2a3-ef103fbd91bb`.
* `fileType`: Unterstützter Dateityp, z. B. docx, pptx, xlsx und pdf.
* `objectUrl`: Objekt-URL der Datei. Das Format ist `https://{tenantName}.sharepoint.com/sites/{TeamName}/SharedDocuments/{ChannelName}/FileName.ext`. Beispiel: `https://microsoft.sharepoint.com/teams/(filepath)`.
* `baseUrl`: Basis-URL der Datei. Das Format ist `https://{tenantName}.sharepoint.com/sites/{TeamName}`. Beispiel: `https://microsoft.sharepoint.com/teams`.
* `serviceName`: Name des Diensts, App-ID. Beispiel: `teams`.
* `threadId`: Die threadId ist die Team-ID des Teams, in dem die Datei gespeichert ist. Sie ist optional und kann nicht für Dateien festgelegt werden, die im OneDrive-Ordner eines Benutzers gespeichert sind. threadId - 19:f8fbfc4d89e24ef5b3b8692538cebeb7@thread.skype.
* `groupId`: Gruppen-ID der Datei. Beispiel: `ae063b79-5315-4ddb-ba70-27328ba6c31e`.

> [!NOTE]
> Sie können `threadId` und `groupId` in der URL dieses Kanals sehen.  

Das folgende Deep Link-Format wird in einem Bot, Connector oder einer Nachrichtenerweiterungskarte verwendet:

`https://teams.microsoft.com/l/file/<fileId>?tenantId=<tenantId>&fileType=<fileType>&objectURL=<objectURL>&baseUrl=<baseURL>&serviceName=<Name>&threadId=<threadId>&groupId=<groupId>`

Das folgende Beispielformat veranschaulicht den Deep-Link zu Dateien:

`https://teams.microsoft.com/l/file/5E0154FC-F2B4-4DA5-8CDA-F096E72C0A80?tenantId=0d9b645f-597b-41f0-a2a3-ef103fbd91bb&fileType=pptx&objectUrl=https%3A%2F%2Fmicrosoft.sharepoint.com%2Fteams%2FActionPlatform%2FShared%20Documents%2FFC7-%20Bot%20and%20Action%20Infra%2FKaizala%20Actions%20in%20Adaptive%20Cards%20-%20Deck.pptx&baseUrl=https%3A%2F%2Fmicrosoft.sharepoint.com%2Fteams%2FActionPlatform&serviceName=teams&threadId=19:f8fbfc4d89e24ef5b3b8692538cebeb7@thread.skype&groupId=ae063b79-5315-4ddb-ba70-27328ba6c31e`

#### <a name="serialization-of-this-object"></a>Serialisierung dieses Objekts:

```javascript
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

### <a name="deep-linking-to-an-app"></a>Deeplinks zu einer App

Erstellen Sie einen Deep-Link für die App, nachdem die App im Microsoft Teams Store aufgeführt wurde. Um einen Link zum Starten von Teams zu erstellen, fügen Sie die App-ID der folgenden URL hinzu: `https://teams.microsoft.com/l/app/<your-app-id>`. Es wird ein Dialogfeld angezeigt, um die App zu installieren.

> [!NOTE]
> Wenn Ihre App für die mobile Plattform genehmigt wurde, können Sie deep-Links zu einer App auf mobilgeräten erstellen. Apple App Store Connect Team ID ist zusätzlich erforderlich, damit der Deep-Link unter Teams-iOS funktioniert. Weitere Informationen finden Sie unter [Aktualisieren von Apple App Store Connect Team ID](../deploy-and-publish/appsource/prepare/create-partner-center-dev-account.md#update-apple-app-store-connect-team-id-on-partner-center).

### <a name="deep-linking-for-sharepoint-framework-tabs"></a>Deeplink-Verknüpfung für SharePoint-Framework-Registerkarten

Das folgende Deep Link-Format kann in einem Bot, Connector oder einer Nachrichtenerweiterungskarte verwendet werden: `https://teamsc.microsoft.com/l/entity/<AppId>/<EntityId>?webUrl=<entityWebUrl>/<EntityName>`

> [!NOTE]
> Wenn ein Bot eine TextBlock-Nachricht mit einem Deeplink sendet, wird eine neue Browserregisterkarte geöffnet, wenn Benutzer den Link auswählen. Dies erfolgt in der Chrome und Microsoft Teams Desktop-App, die unter Linux ausgeführt wird.
> Wenn der Bot dieselbe Deeplink-URL an eine(n) `Action.OpenUrl` sendet, wird die Registerkarte Teams im aktuellen Browser geöffnet, wenn der Benutzer den Link auswählt. Es wird keine neue Browserregisterkarte geöffnet.

Die Abfrageparameter sind:

* `appID`: Ihre Manifest-ID, z. B. `fe4a8eba-2a31-4737-8e33-e5fae6fee194`.

* `entityID`: Die Element-ID, die Sie beim [Konfigurieren der Registerkarte](~/tabs/how-to/create-tab-pages/configuration-page.md)angegeben haben. Zum Beispiel: `tasklist123`.
* `entityWebUrl`: Ein optionales Feld mit einer Fallback URL, das verwendet werden soll, wenn der Client das Rendern der Registerkarte nicht unterstützt - `https://tasklist.example.com/123` oder `https://tasklist.example.com/list123/task456`.
* `entityName`: Eine Beschriftung für das Element auf Ihrer Registerkarte, das beim Anzeigen des Deeplinks, Task List 123 oder Task 456, verwendet werden soll.

Beispiel: `https://teams.microsoft.com/l/entity/fe4a8eba-2a31-4737-8e33-e5fae6fee194/tasklist123?webUrl=https://tasklist.example.com/123&TaskList`

### <a name="navigate-to-an-audio-or-audio-video-call"></a>Navigieren zu einem Audio- oder Audiovideoanruf

Sie können nur Audio- oder Audiovideoanrufe an einen einzelnen Benutzer oder eine Gruppe von Benutzern aufrufen, indem Sie den Anruftyp und die Teilnehmer angeben. Bevor der Anruf erfolgt, fordert der Microsoft Teams-Client eine Bestätigung für den Anruf an. Bei einem Gruppenanruf können Sie eine Gruppe von VoIP-Benutzern und eine Gruppe von PSTN-Benutzern mit demselben Deep-Link-Aufruf anrufen.

Bei einem Videoanruf fordert der Client eine Bestätigung an und aktiviert das Video des Anrufers für den Anruf. Der Empfänger des Anrufs kann über das Teams Anrufbenachrichtigungsfenster nur über Audio oder Video antworten.

> [!NOTE]
> Diese Methode kann nicht zum Aufrufen einer Besprechung verwendet werden.

Der folgende Code veranschaulicht die Verwendung des TeamsJS-SDK zum Starten eines Aufrufs:

```javascript
if(call.isSupported()) {
    const callPromise = call.startCall({ targets: ["joe@contoso.com","bob@contoso.com","4:9876543210"], requestedModalities: [call.CallModalities.Audio], source: "demoApp"});
    callPromise.
      then((result) => {/*Successful operation*/}).
      catch((error) => {/*Unsuccessful operation*/});
}
else { /* handle case where capability isn't supported */ }

```

#### <a name="generate-a-deep-link-to-a-call"></a>Generieren eines Deeplinks zu einem Anruf

Zwar wird Verwendung der typisierten APIs von TeamsJS empfohlen, Sie können jedoch auch einen manuell erstellten Deep-Link verwenden, um einen Anruf zu starten.

| Deep-Link | Format | Beispiel |
|-----------|--------|---------|
| Tätigen eines Audioanrufs | `https://teams.microsoft.com/l/call/0/0?users=<user1>,<user2>` | `https://teams.microsoft.com/l/call/0/0?users=joe@contoso.com` |
| Tätigen eines Audio- und Videoanrufs | `https://teams.microsoft.com/l/call/0/0?users=<user1>,<user2>&withVideo=true` | `https://teams.microsoft.com/l/call/0/0?users=joe@contoso.com&withVideo=true` |
|Tätigen eines Audio- und Videoanrufs mit einer optionalen Parameterquelle | `https://teams.microsoft.com/l/call/0/0?users=<user1>,<user2>&withVideo=true&source=demoApp` | `https://teams.microsoft.com/l/call/0/0?users=joe@contoso.com&withVideo=true&source=demoApp` |  
| Tätigen eines Audio- und Videoanrufs an eine Kombination aus VoIP- und PSTN-Benutzern | `https://teams.microsoft.com/l/call/0/0?users=<user1>,4:<phonenumber>` | `https://teams.microsoft.com/l/call/0/0?users=joe@contoso.com,4:9876543210` |
  
Nachfolgend sind die Abfrageparameter aufgeführt:

* `users`: Die durch Kommas getrennte Liste der Benutzer-IDs, die die Teilnehmer des Anrufs darstellen. Derzeit unterstützt das Benutzer-ID-Feld den Azure AD UserPrincipalName, in der Regel eine E-Mail-Adresse. Bei einem PSTN-Anruf unterstützt es eine pstn mri 4:&lt;phonenumber&gt;.
* `withVideo`: Dies ist ein optionaler Parameter, den Sie für einen Videoanruf verwenden können. Durch Festlegen dieses Parameters wird nur die Kamera des Anrufers aktiviert. Der Empfänger des Anrufs hat die Möglichkeit, Audio- oder Audio- und Videoanrufe über das Teams Anrufbenachrichtigungsfenster entgegen zu nehmen.
* `Source`: Dies ist ein optionaler Parameter, der über die Deep-Link-Quelle informiert.

## <a name="code-sample"></a>Codebeispiel

| Beispielname | Beschreibung | C# |Node.js|
|-------------|-------------|------|----|
|Unterentitäts-ID für die Deeplink-Nutzung  | Teams-Beispiel-App zum Demonstrieren einer Deep-Link-Verknüpfung vom Bot-Chat zu der Registerkarte, welche die untergeordnete Entitäts-ID konsumiert.|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-deeplink/csharp)|[Anzeigen](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-deeplink/nodejs)|

## <a name="see-also"></a>Siehe auch

* [Integrieren von Web-Apps](~/samples/integrate-web-apps-overview.md)
* [Moodle LMS](~/resources/moodleinstructions.md)
