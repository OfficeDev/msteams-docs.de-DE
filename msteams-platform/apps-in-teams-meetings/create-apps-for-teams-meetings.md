---
title: Apps für Teams-Besprechungen erstellen
author: laujan
description: Erstellen von Apps für Microsoft Teams-Besprechungen
ms.topic: conceptual
ms.author: lajanuar
keywords: Teams-apps-Besprechungen Benutzer Teilnehmer-Rollen-API
ms.openlocfilehash: cf42d660c9b4a82f8e28d4d4379194c1bcc681e1
ms.sourcegitcommit: 3fc7ad33e2693f07170c3cb1a0d396261fc5c619
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "48796169"
---
# <a name="create-apps-for-teams-meetings-developer-preview"></a>Erstellen von Apps für Microsoft Teams-Besprechungen (Entwicklervorschau)

>[!IMPORTANT]
> In der Entwicklervorschau von Microsoft Teams enthaltene Features werden nur für frühere Zugriffs-, Test-und Feedback Zwecke bereitgestellt. Sie werden möglicherweise geändert, bevor Sie in der öffentlichen Version verfügbar werden und sollten nicht in Produktionsanwendungen verwendet werden.

## <a name="prerequisites-and-considerations"></a>Voraussetzungen und Überlegungen

1. Apps in Besprechungen erfordern grundlegende Kenntnisse der [Teams-App-Entwicklung](../overview.md). Eine app in einer Besprechung kann aus [Registerkarten](../tabs/what-are-tabs.md), [Bots](../bots/what-are-bots.md)und [Messaging Erweiterungs](../messaging-extensions/what-are-messaging-extensions.md) Features bestehen und erfordert Aktualisierungen des Teams-APP- [Manifests](#update-your-app-manifest) , um anzugeben, dass die APP für Besprechungen zur Verfügung steht.

1. Damit Ihre APP im Besprechungs Lebenszyklus als Registerkarte funktioniert, muss Sie konfigurierbare Registerkarten im [Groupchat-Bereich](../resources/schema/manifest-schema.md#configurabletabs)unterstützen. *Weitere Informationen finden Sie unter* [Erweitern Ihrer Teams-App mit einer benutzerdefinierten Registerkarte](../tabs/how-to/add-tab.md). Durch die Unterstützung des `groupchat` Bereichs wird Ihre APP in [Besprechungen vor](teams-apps-in-meetings.md#pre-meeting-app-experience) und [nach](teams-apps-in-meetings.md#post-meeting-app-experience) dem Chatten aktiviert.

1. Die URL-Parameter der Besprechungs-API erfordern möglicherweise, `meetingId` `userId` und die [Mandanten](/onedrive/find-your-office-365-tenant-id) -Nr sind im Rahmen des Teams-Client-SDK und der Bot-Aktivität verfügbar. Außerdem können zuverlässige Informationen für Benutzer-ID und Mandanten-ID mithilfe der [Registerkarten-SSO-Authentifizierung](../tabs/how-to/authentication/auth-aad-sso.md)abgerufen werden.

1. Einige Besprechungs-APIs, wie zum Beispiel, `GetParticipant` erfordern eine [bot-Registrierung und eine bot-APP-ID](../bots/how-to/create-a-bot-for-teams.md#with-an-azure-subscription) zum Generieren von auth-Token.

1. Entwickler müssen sich an die allgemeinen [Entwurfsrichtlinien für Teams-Registerkarten](../tabs/design/tabs.md) für Pre-und Post-Meeting-Szenarien sowie die [in-Meeting-Dialogfeld Richtlinien](design/designing-in-meeting-dialog.md) für das in-Meeting-Dialogfeld halten, das während einer Teambesprechung ausgelöst wird.

## <a name="meeting-apps-api-reference"></a>Besprechungs-apps-API-Referenz

|API|Beschreibung|Anforderung|Source|
|---|---|----|---|
|**Getusercontext**| Abrufen von Kontextinformationen zum Anzeigen relevanter Inhalte auf einer Registerkarte Teams. |_**verläuft. GetContext (() => {/ *...* / } )**_|Microsoft Teams-Client-SDK|
|**Getparticipant**|Mit dieser API kann ein bot eine Teilnehmer Information nach Besprechungs-ID und Teilnehmer-ID abrufen.|**GET** _**/V1/Meetings/{meetingId}/participants/{participantId} abrufen? Mandanten-Nr = {Mandanten** -Nr}_ |Microsoft bot Framework SDK|
|**NotificationSignal** |Besprechungs Signale werden über die folgende vorhandene Benachrichtigungs-API für Unterhaltungen (für Benutzer-bot-Chat) übermittelt. Mit dieser API können Entwickler basierend auf der Endbenutzer Aktion signalisieren, dass eine Dialog Blase in einer Besprechung angezeigt wird.|**Post** _**/V3/Conversations/{conversationId}/Activities**_|Microsoft bot Framework SDK|

### <a name="getusercontext"></a>Getusercontext

Eine Anleitung zum Identifizieren und Abrufen von Kontextinformationen für die Registerkarteninhalte finden Sie in der Dokumentation zu [Get Context for your Teams](../tabs/how-to/access-teams-context.md#getting-context-by-using-the-microsoft-teams-javascript-library) . Im Rahmen der Erweiterbarkeit von Besprechungen wurde für die Antwort Nutzlast ein neuer Wert hinzugefügt:

✔- **Besprechungs** -Nr: wird von einer Registerkarte bei der Ausführung im Besprechungs Kontext verwendet.

### <a name="getparticipant-api"></a>Getparticipant-API

> [!NOTE]
>
> * Sie sollten keine Teilnehmerrollen Zwischenspeichern, da der Besprechungsorganisator zu einem beliebigen Zeitpunkt eine Rolle ändern kann.
>
> * Microsoft Teams unterstützt derzeit keine großen Verteilerlisten oder Dienstplan Größen von mehr als 350 Teilnehmern für die `GetParticipant` API.
>
> * Die Unterstützung für das bot Framework SDK wird in Kürze verfügbar sein.

#### <a name="request"></a>Anforderung

```http
GET /v3/meetings/{meetingId}/participants/{participantId}?tenantId={tenantId}
```

*Siehe* [bot Framework-API-Referenz](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0&preserve-view=true).

<!-- markdownlint-disable MD025 -->

**C#-Beispiel**

```csharp
string meetingId = "meetingid?";
string participantId = "participantidhere";
var connectorClient = turnContext.TurnState.Get<IConnectorClient>();
var creds = connectorClient.Credentials as AppCredentials;
var bearerToken = await creds.GetTokenAsync().ConfigureAwait(false);
var request = new HttpRequestMessage();
request.Headers.Authorization = new AuthenticationHeaderValue("Bearer", bearerToken);
request.Method = new HttpMethod("GET");
request.RequestUri = new System.Uri(Path.Combine(connectorClient.BaseUri.OriginalString, $"/meetings/{meetingId}/participants/{participantId}"));
HttpResponseMessage response = await (connectorClient as ServiceClient<ConnectorClient>).HttpClient.SendAsync(request, cancellationToken).ConfigureAwait(false);
if (response.StatusCode == System.Net.HttpStatusCode.OK)
{
    var content = await response.Content.ReadAsStringAsync().ConfigureAwait(false);
    var theObject = Rest.Serialization.SafeJsonConvert.DeserializeObject<WhateverObjectIsReturned>(content, connectorClient.DeserializationSettings);
}
```

* * *
<!-- markdownlint-disable MD001 -->

#### <a name="query-parameters"></a>Abfrageparameter

|Wert|Typ|Erforderlich|Beschreibung|
|---|---|----|---|
|**meetingId**| Zeichenfolge | Ja | Die Besprechungs-ID ist über bot Invoke und Microsoft Teams Client SDK verfügbar.|
|**Teilnehmer-Nr**| Zeichenfolge | Ja | Dieses Feld ist die Benutzer-ID und steht in der Registerkarte "SSO", im bot-Invoke und im Microsoft Teams-Client-SDK zur Verfügung. Die Registerkarte SSO wird dringend empfohlen.|
|**tenantId**| Zeichenfolge | Ja | Dies ist für Mandanten Benutzer erforderlich. Sie ist in Tab SSO, bot Invoke und Microsoft Teams Client SDK verfügbar. Die Registerkarte SSO wird dringend empfohlen.|

#### <a name="response-payload"></a>Antwort Nutzlast
<!-- markdownlint-disable MD036 -->

**Rolle** unter "Besprechung" kann *Organisator* , *Referent* oder *Teilnehmer* sein.

**Beispiel 1**

```json
{
  "user":
  {
      "id": "29:1JKiJGPAX9TTxtGxhVo0wLx_zwzo-gG8Z-X03306vBwi9p-xMTEbDXsT6KH7-0kkTS8cD-2zkrsoV6f5WJ6_aYw",
      "aadObjectId": "6aebbad0-e5a5-424a-834a-20fb051f3c1a",
      "name": "Allan Deyoung",
      "givenName": "Allan",
      "surname": "Deyoung",
      "email": "Allan.Deyoung@microsoft.com",
      "userPrincipalName": "Allan.Deyoung@microsoft.com",
      "tenantId": "72f988bf-86f1-41af-91ab-2d7cd011db47",
      "userRole": "user"
  },
  "meeting":
  {
      "role ": "Presenter",
      "inMeeting":true
  },
  "conversation":
  {
      "id": "<conversation id>"
  }
}
```
#### <a name="response-codes"></a>Antwort Codes

**403** : die APP darf keine Teilnehmer Informationen erhalten. Dies ist die häufigste Fehlerantwort und wird ausgelöst, wenn die APP nicht in der Besprechung installiert wird, beispielsweise wenn die APP vom mandantenadministrator deaktiviert oder während der Live-Website Minderung blockiert wird.  
**200** : Teilnehmer Informationen erfolgreich abgerufen  
**401** : Ungültiges Token  
**404** : die Besprechung ist nicht vorhanden, oder der Teilnehmer kann nicht gefunden werden.

<!-- markdownlint-disable MD024 -->
### <a name="notificationsignal-api"></a>NotificationSignal-API

> [!NOTE]
> Wenn ein in-Meeting-Dialogfeld aufgerufen wird, wird derselbe Inhalt auch als Chatnachricht angezeigt.

#### <a name="request"></a>Anforderung

```http
POST /v3/conversations/{conversationId}/activities
```

#### <a name="query-parameters"></a>Abfrageparameter

|Wert|Typ|Erforderlich|Beschreibung|
|---|---|----|---|
|**conversationId**| Zeichenfolge | Ja | Die Konversations-ID ist im Rahmen von bot Invoke verfügbar |

#### <a name="request-payload"></a>Anforderungsnutzlast

> [!NOTE]
>
> Das completionBotId in der externalResourceUrl in der folgenden Nutzlast ist ein optionaler Parameter. Es ist die bot-ID, die im Manifest deklariert wird. Der bot erhält ein Result-Objekt.

# <a name="json"></a>[Json](#tab/json)

```json
{
    "type": "message",
    "text": "John Phillips assigned you a weekly todo",
    "summary": "Don't forget to meet with Marketing next week",
    "channelData": {
        "notification": {
            "alertInMeeting": true,
            "externalResourceUrl": "https://teams.microsoft.com/l/bubble/APP_ID?url=<TaskInfo.url>&height=<TaskInfo.height>&width=<TaskInfo.width>&title=<TaskInfo.title>&completionBotId=BOT_APP_ID"
        }
    },
    "replyToId": "1493070356924"
}
```

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

```csharp
Activity activity = MessageFactory.Text("This is a meeting signal test");
MeetingNotification notification = new MeetingNotification
  {
    AlertInMeeting = true,
    ExternalResourceUrl = "https://teams.microsoft.com/l/bubble/APP_ID?url=<TaskInfo.url>&height=<TaskInfo.height>&width=<TaskInfo.width>&title=<TaskInfo.title>&completionBotId=BOT_APP_ID"
  };
activity.ChannelData = new TeamsChannelData
  {
    Notification = notification
  };
await turnContext.SendActivityAsync(activity).ConfigureAwait(false);
```

# <a name="javascript"></a>[JavaScript](#tab/javascript)

```javascript

const replyActivity = MessageFactory.text('Hi'); // this could be an adaptive card instead
replyActivity.channelData = {
    notification: {
        alertInMeeting: true,
        externalResourceUrl: 'https://teams.microsoft.com/l/bubble/APP_ID?url=<TaskInfo.url>&height=<TaskInfo.height>&width=<TaskInfo.width>&title=<TaskInfo.title>&completionBotId=BOT_APP_ID’
    }
};
await context.sendActivity(replyActivity);
```

* * *

> [!IMPORTANT]
> Die URL in der Inhalts Blase (taskInfo-URL) muss in der Liste [gültiger Domänen](../resources/schema/manifest-schema.md#validdomains) enthalten sein, die im App-Manifest für Teams enthalten ist.

#### <a name="response-codes"></a>Antwort Codes

**201** : Aktivität mit Signal wurde erfolgreich gesendet  
**401** : Ungültiges Token  
**403** : die APP darf das Signal nicht senden. In diesem Fall sollte die Nutzlast eine ausführlichere Fehlermeldung enthalten. Es kann viele Gründe geben: app, die vom mandantenadministrator deaktiviert, während einer Live-Standort Minderung blockiert wird, usw.  
**404** : Besprechungs Chat nicht vorhanden  

## <a name="enable-your-app-for-teams-meetings"></a>Aktivieren Ihrer APP für Microsoft Teams-Besprechungen

### <a name="update-your-app-manifest"></a>Aktualisieren des App-Manifests

Die APP-Funktionen für Besprechungen werden in Ihrem App-Manifest über die **configurableTabs**  ->  - **Bereiche** und **Kontext** Arrays deklariert. *Scope* definiert, an wen und in welchem *Kontext* definiert wird, wo Ihre app verfügbar sein wird.

> [!NOTE]
> * Verwenden Sie das [Manifest-Schema für Entwicklervorschau](../resources/schema/manifest-schema-dev-preview.md) , um dieses in Ihrem App-Manifest zu testen.

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
        "meetingSidePanel"
     ]
    }
  ]
```

### <a name="context-property"></a>Context-Eigenschaft

Die Registerkarte `context` und die `scopes` Eigenschaften funktionieren in Harmonie, damit Sie bestimmen können, wo Ihre APP angezeigt werden soll. Registerkarten im `team` `groupchat` Bereich oder können mehr als einen Kontext aufweisen. Die möglichen Werte für die Context-Eigenschaft lauten wie folgt:

* **channelTab** : eine Registerkarte in der Kopfzeile eines Team Kanals.
* **privateChatTab** : eine Registerkarte in der Kopfzeile eines Gruppenchats zwischen einer Gruppe von Benutzern, die sich nicht im Kontext eines Teams oder einer Besprechung befinden.
* **meetingChatTab** : eine Registerkarte in der Kopfzeile eines Gruppenchats zwischen einer Gruppe von Benutzern im Kontext einer geplanten Besprechung.
* **meetingDetailsTab** : eine Registerkarte in der Kopfzeile der Ansicht "Besprechungsdetails" des Kalenders.
* **meetingSidePanel** : ein in-Meeting-Bereich, der über den einheitlichen Balken geöffnet wird (u-Leiste).

> [!NOTE]
> Die Eigenschaft "Context" wird derzeit nicht unterstützt und wird daher auf mobilen Clients ignoriert.

## <a name="configure-your-app-for-meeting-scenarios"></a>Konfigurieren Ihrer APP für Besprechungs Szenarien

> [!NOTE]
> * Damit Ihre APP im Registerkarten Katalog sichtbar ist, muss Sie **konfigurierbare Registerkarten** und den **Gruppenchat Bereich** unterstützen.
>
> * Mobile Clients unterstützen Registerkarten nur in Pre-und Post-Besprechungs Oberflächen. Die in-Meeting-Erlebnisse (in-Meeting-Dialog und-Panel) auf mobilen Geräten werden in Kürze verfügbar sein. Befolgten Sie die [Anleitungen für Registerkarten auf mobilen Geräten](../tabs/design/tabs-mobile.md) beim Erstellen Ihrer Registerkarten für mobile Geräte. 

### <a name="pre-meeting"></a>Pre-Meeting

Benutzer mit Organizer-und/oder Presenter-Rollen fügen mithilfe der Schaltfläche Plus ➕ auf der Seite Besprechungs- **Chat** und Besprechungs **Details** Registerkarten zu einer Besprechung hinzu. Messaging Erweiterungen werden über das Menü Ellipsen/Überlauf hinzugefügt, &#x25CF;&#x25CF;&#x25CF; unterhalb des Bereichs zum Verfassen von Nachrichten im Chat angezeigt wird. Bots werden mit der Taste "" zu einem Besprechungs Chat hinzugefügt **@** und die Option **Bots abrufen** ausgewählt.

✔ Die Benutzeridentität *muss* über die [Registerkarten SSO](../tabs/how-to/authentication/auth-aad-sso.md)bestätigt werden. Nach dieser Authentifizierung kann die APP die Benutzerrolle über die getteilnehmer-API abrufen.

 ✔ Basierend auf der Benutzerrolle kann die App nun rollenspezifische Erlebnisse vorlegen. Beispielsweise kann eine Polling-app nur Organisatoren und Referenten das Erstellen einer neuen Umfrage gestatten.

> **Hinweis** : Rollenzuweisungen können geändert werden, während eine Besprechung ausgeführt wird.  *Siehe* [roles in a Teams Meeting](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019). 

### <a name="in-meeting"></a>In-Meeting

#### <a name="sidepanel"></a>**sidePanel**

✔ In Ihrem App-Manifest fügen Sie **sidePanel** dem **Kontext** Array hinzu, wie oben beschrieben.

✔ In der Besprechung als auch in allen Szenarien wird die app in einer in-Meeting-Registerkarte gerendert, die 320 Pixel groß in der Breite ist. Die Registerkarte muss dafür optimiert werden. *Siehe* , [framecontext-Schnittstelle](/javascript/api/@microsoft/teams-js/microsoftteams.framecontext?view=msteams-client-js-latest&preserve-view=true)

✔ Sie im Microsoft [Teams-SDK](../tabs/how-to/access-teams-context.md#user-context) nach, um die **benutzercontext** -API zu verwenden, um Anforderungen entsprechend weiterzuleiten.

✔ Bezieht sich auf den Microsoft [Teams-Authentifizierungs Fluss für Registerkarten](../tabs/how-to/authentication/auth-flow-tab.md). Der Authentifizierungs Fluss für Registerkarten ähnelt dem auth-Fluss für Websites. Daher können Registerkarten OAuth 2,0 direkt verwenden. *Siehe auch* , [Microsoft Identity Platform und OAuth 2,0-Autorisierungscode Fluss](/azure/active-directory/develop/v2-oauth2-auth-code-flow).

#### <a name="in-meeting-dialog"></a>**in-Meeting-Dialog**

✔ Sie die Entwurfsrichtlinien für das [in-Meeting-Dialogfeld](design/designing-in-meeting-dialog.md)einhalten.

✔ Bezieht sich auf den Microsoft [Teams-Authentifizierungs Fluss für Registerkarten](../tabs/how-to/authentication/auth-flow-tab.md).

✔ Verwenden Sie die [Benachrichtigungs](/graph/api/resources/notifications-api-overview?view=graph-rest-beta&preserve-view=true) -API, um zu signalisieren, dass eine Blasen Benachrichtigung ausgelöst werden muss.

✔ Als Teil der Nutzlast der Benachrichtigungsanforderung enthalten die URL, in der der zu präsentierende Inhalt gehostet wird.

> [!NOTE]
>
> * Diese Benachrichtigungen sind in der Natur persistent. Sie müssen die [**submitTask ()**](../task-modules-and-cards/task-modules/task-modules-bots.md#submitting-the-result-of-a-task-module) -Funktion aufrufen, um automatisch zu entlassen, nachdem ein Benutzer eine Aktion in der-Webansicht durchführt. Dies ist eine Voraussetzung für die APP-Übermittlung. *Siehe auch* Microsoft [Teams SDK: Aufgabenmodul](/javascript/api/@microsoft/teams-js/microsoftteams.tasks?view=msteams-client-js-latest#submittask-string---object--string---string---&preserve-view=true).
>
> * Wenn Ihre APP anonyme Benutzer unterstützen soll, muss ihre anfängliche Anforderungsnutzlast auf die `from.id`  (ID der Benutzer)-Anforderungs Metadaten im `from` Objekt und nicht auf die `from.aadObjectId` Anforderungs Metadaten (Azure Active Directory ID des Benutzers) zurückgreifen. *Weitere Informationen finden Sie unter* [Verwenden von Aufgaben Modulen in Registerkarten](../task-modules-and-cards/task-modules/task-modules-tabs.md) und [Erstellen und Senden des Aufgabenmoduls](../messaging-extensions/how-to/action-commands/create-task-module.md?tabs=dotnet#the-initial-invoke-request).

### <a name="post-meeting"></a>Nachbesprechung

Die Konfigurationen nach der Besprechung und vor der Besprechung sind äquivalent.

## <a name="meeting-app-sample"></a>Beispiel für eine Besprechungs-App

 > [!div class="nextstepaction"]
> [App für die Besprechungs Token-Generator](https://github.com/OfficeDev/microsoft-teams-sample-meetings-token)
