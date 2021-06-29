---
title: Voraussetzungen und API-Verweise für Apps in Teams-Besprechungen
author: surbhigupta
description: Arbeiten mit Apps für Teams Besprechungen
ms.topic: conceptual
ms.author: lajanuar
localization_priority: Normal
keywords: Teams-Apps – Benutzerteilnehmer-Rollen-API für Besprechungen
ms.openlocfilehash: dbab038c6e006003fb4525c6d58ea8a151e9592d
ms.sourcegitcommit: 85a52119df6c4cb4536572e6d2e7407f0e5e8a23
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/29/2021
ms.locfileid: "53179699"
---
# <a name="prerequisites-and-api-references-for-apps-in-teams-meetings"></a>Voraussetzungen und API-Verweise für Apps in Teams-Besprechungen

Um die Funktionen Ihrer Apps über den gesamten Besprechungslebenszyklus zu erweitern, können Sie mit Teams mit Apps für Teams Besprechungen arbeiten. Sie müssen die Voraussetzungen durchlaufen, und Sie können die Api-Verweise auf Besprechungs-Apps verwenden, um die Besprechungserfahrung zu verbessern.

## <a name="prerequisites"></a>Voraussetzungen

Bevor Sie mit Apps für Teams Besprechungen arbeiten, müssen Sie Folgendes verstehen:

* Sie müssen über Kenntnisse in der Entwicklung von Teams-Apps verfügen. Weitere Informationen finden Sie unter [Teams App-Entwicklung.](../overview.md)

* Sie müssen das Teams App-Manifest aktualisieren, um anzugeben, dass die App für Besprechungen verfügbar ist. Weitere Informationen finden Sie unter [App-Manifest.](enable-and-configure-your-app-for-teams-meetings.md#update-your-app-manifest)

* Ihre App muss konfigurierbare Registerkarten im Gruppenchatbereich unterstützen, damit Ihre App im Besprechungslebenszyklus als Registerkarte funktioniert. Weitere Informationen finden Sie unter [Gruppenchatbereich](../resources/schema/manifest-schema.md#configurabletabs) und [Erstellen einer Gruppenregisterkarte.](../build-your-first-app/build-channel-tab.md)

* Sie müssen allgemeine Teams Entwurfsrichtlinien für Registerkarten für Szenarien vor und nach der Besprechung einhalten. Informationen zu Erfahrungen während Besprechungen finden Sie auf der Registerkarte "Besprechung" und in den Entwurfsrichtlinien des Dialogfelds "In-Meeting". Weitere Informationen finden Sie unter [Teams Entwurfsrichtlinien für Registerkarten,](../tabs/design/tabs.md) [Entwurfsrichtlinien für Registerkarten in Besprechungen](../apps-in-teams-meetings/design/designing-apps-in-meetings.md#use-an-in-meeting-tab)und Entwurfsrichtlinien für [Dialogfelder in Besprechungen.](../apps-in-teams-meetings/design/designing-apps-in-meetings.md#use-an-in-meeting-dialog)

* Sie müssen den `groupchat` Bereich unterstützen, um Ihre App in Chats vor und nach der Besprechung zu aktivieren. Mit der App-Erfahrung vor der Besprechung können Sie Besprechungs-Apps suchen und hinzufügen und Aufgaben vor der Besprechung ausführen. Mit der App-Erfahrung nach der Besprechung können Sie die Ergebnisse der Besprechung anzeigen, z. B. Umfrageergebnisse oder Feedback.

* Die URL-Parameter der Besprechungs-API müssen `meetingId` über `userId` , und `tenantId` verfügen. Diese sind als Teil der Teams Client SDK- und Bot-Aktivität verfügbar. Darüber hinaus können Sie mithilfe der [SSO-Authentifizierung](../tabs/how-to/authentication/auth-aad-sso.md)der Registerkarte zuverlässige Informationen zu Benutzer-ID und Mandanten-ID abrufen.

* Die `GetParticipant` API muss über eine Bot-Registrierung und -ID verfügen, um Authentifizierungstoken zu generieren. Weitere Informationen finden Sie unter [Bot-Registrierung und -ID.](../build-your-first-app/build-bot.md)

* Damit Ihre App in Echtzeit aktualisiert werden kann, muss sie basierend auf den Ereignisaktivitäten in der Besprechung auf dem neuesten Stand sein. Diese Ereignisse können sich innerhalb des Besprechungsdialogfelds und in anderen Phasen des Besprechungslebenszyklus befinden. Das Dialogfeld in besprechungsinternen Besprechungen finden Sie unter `bot Id` Abschlussparameter in `NotificationSignal` der API.

* Die Besprechungsdetails-API muss über eine Bot-Registrierung und Bot-ID verfügen. Es erfordert Bot SDK, um `TurnContext` .

* Bei Echtzeitbesprechungsereignissen müssen Sie mit dem objekt vertraut sein, `TurnContext` das über das Bot SDK verfügbar ist. Das `Activity` Objekt enthält die Nutzlast mit der `TurnContext` tatsächlichen Start- und Endzeit. Echtzeitbesprechungsereignisse erfordern eine registrierte Bot-ID von der Teams-Plattform.

Nachdem Sie die Voraussetzungen erfüllt haben, können Sie die API-Verweise auf Besprechungs-Apps , und die `GetUserContext` `GetParticipant` Api für `NotificationSignal` Besprechungsdetails verwenden, mit der Sie mithilfe von Attributen auf Informationen zugreifen und relevante Inhalte anzeigen können.

## <a name="meeting-apps-api-references"></a>API-Referenzen für Besprechungs-Apps

Die neuen Besprechungserweiterungen bieten Ihnen APIs, die die Besprechungsumgebung transformieren. Mit dieser neuen Funktion können Sie Apps erstellen oder vorhandene Apps in den Besprechungslebenszyklus integrieren. Sie können die APIs verwenden, um Ihre App auf die Besprechung aufmerksam zu machen. Sie können auswählen, welche APIs Sie verwenden möchten, um die Besprechungserfahrung zu verbessern.

Die folgende Tabelle enthält eine Liste dieser APIs:

|API|Beschreibung|Anforderung|Quelle|
|---|---|----|---|
|**GetUserContext**| Mit dieser API können Sie Kontextinformationen abrufen, um relevante Inhalte auf einer Teams Registerkarte anzuzeigen. |_**microsoftTeams.getContext( ( ) => { /*...* / } )**_|Microsoft Teams Client SDK|
|**GetParticipant**| Diese API ermöglicht es einem Bot, Teilnehmerinformationen nach Besprechungs-ID und Teilnehmer-ID abzurufen. |**GET** _**/v1/meetings/{meetingId}/participants/{participantId}?tenantId={tenantId}**_ |Microsoft Bot Framework Sdk|
|**NotificationSignal** | Mit dieser API können Sie Besprechungssignale bereitstellen, die mithilfe der vorhandenen Unterhaltungsbenachrichtigungs-API für den Benutzer-Bot-Chat übermittelt werden. Sie können ein Signal basierend auf einer Benutzeraktion senden, die ein Dialogfeld in der Besprechung anzeigt. |**POST** _**/v3/conversations/{conversationId}/activities**_|Microsoft Bot Framework Sdk|
|**Besprechungsdetails** | Mit dieser API können Sie statische Besprechungsmetadaten abrufen. |**GET** _**/v1/meetings/{meetingId}**_| Bot SDK |

### <a name="getusercontext-api"></a>GetUserContext-API

Informationen zum Identifizieren und Abrufen von Kontextinformationen für Ihre Registerkarteninhalte finden Sie unter Abrufen des [Kontexts für Ihre Teams Registerkarte.](../tabs/how-to/access-teams-context.md#get-context-by-using-the-microsoft-teams-javascript-library) `meetingId`wird von einer Registerkarte verwendet, wenn sie im Besprechungskontext ausgeführt wird, und wird für die Antwortnutzlast hinzugefügt.

### <a name="getparticipant-api"></a>GetParticipant-API

> [!NOTE]
> * Teilnehmerrollen nicht zwischenspeichern, da der Besprechungsorganisator die Rollen jederzeit ändern kann.
> * Teams unterstützt derzeit keine großen Verteilerlisten oder Listengrößen von mehr als 350 Teilnehmern für die `GetParticipant` API.

Die `GetParticipant` API ermöglicht es einem Bot, Teilnehmerinformationen nach Besprechungs-ID und Teilnehmer-ID abzurufen. Die API enthält Abfrageparameter, Beispiele und Antwortcodes.

#### <a name="query-parameters"></a>Abfrageparameter

Die `GetParticipant` API enthält die folgenden Abfrageparameter:

|Wert|Typ|Erforderlich|Beschreibung|
|---|---|----|---|
|**meetingId**| Zeichenfolge | Ja | Der Besprechungsbezeichner ist über Bot Invoke und Teams Client SDK verfügbar.|
|**participantId**| Zeichenfolge | Ja | Die Teilnehmer-ID ist die Benutzer-ID. Es ist in Tab SSO, Bot Invoke und Teams Client SDK verfügbar. Es wird empfohlen, eine Teilnehmer-ID vom Tab-SSO abzurufen. |
|**tenantId**| Zeichenfolge | Ja | Die Mandanten-ID ist für die Mandantenbenutzer erforderlich. Es ist in Tab SSO, Bot Invoke und Teams Client SDK verfügbar. Es wird empfohlen, eine Mandanten-ID aus dem Tab-SSO abzurufen. |

#### <a name="example"></a>Beispiel

Die `GetParticipant` API enthält die folgenden Beispiele:

# <a name="c"></a>[C#](#tab/dotnet)

```csharp
protected override async Task OnMessageActivityAsync(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
{
  TeamsMeetingParticipant participant = GetMeetingParticipantAsync(turnContext, "yourMeetingId", "yourParticipantId", "yourTenantId");
  TeamsChannelAccount member = participant.User;
  MeetingParticipantInfo meetingInfo = participant.Meeting;
  ConversationAccount conversation = participant.Conversation;

  await turnContext.SendActivityAsync(MessageFactory.Text($"The participant role is: {meetingInfo.Role}"), cancellationToken);
}

```

# <a name="javascript"></a>[JavaScript](#tab/javascript)

```typescript

export class MyBot extends TeamsActivityHandler {
    constructor() {
        super();
        this.onMessage(async (context, next) => {
            TeamsMeetingParticipant participant = getMeetingParticipant(turnContext, "yourMeetingId", "yourParticipantId", "yourTenantId");
            let member = participant.user;
            let meetingInfo = participant.meeting;
            let conversation = participant.conversation;
            
            await context.sendActivity(`The participant role is: '${meetingInfo.role}'`);
            await next();
        });
    }
}

```

# <a name="json"></a>[Json](#tab/json)

```http
GET /v1/meetings/{meetingId}/participants/{participantId}?tenantId={tenantId}
```

* * *

Der JSON-Antworttext für `GetParticipant` die API lautet:

```json
{
   "user":{
      "id":"29:1JKiJGPAX9TTxtGxhVo0wLx_zwzo-gG8Z-X03306vBwi9p-xMTEbDXsT6KH7-0kkTS8cD-2zkrsoV6f5WJ6_aYw",
      "aadObjectId":"e236c4bf-88b1-4f3a-b1d7-8891dfc332b5",
      "name":"Bob Young",
      "givenName":"Bob",
      "surname":"Young",
      "email":"Bob.young@microsoft.com",
      "userPrincipalName":"Bob.young@microsoft.com",
      "tenantId":"2fe477ab-0efc-4dfd-bde2-484374e2c373",
      "userRole":"user"
   },
   "meeting":{
      "role ":"Presenter",
      "inMeeting":true
   },
   "conversation":{
      "id":"<conversation id>",
      "isGroup":true
   }
}
```

#### <a name="response-codes"></a>Antwortcodes

Die `GetParticipant` API enthält die folgenden Antwortcodes:

|Antwortcode|Beschreibung|
|---|---|
| **403** | Die App darf keine Teilnehmerinformationen abrufen. Dies ist die häufigste Fehlerantwort und wird ausgelöst, wenn die App nicht in der Besprechung installiert ist. Wenn die App beispielsweise vom Mandantenadministrator deaktiviert oder während der Migration einer Livewebsite blockiert wird.|
| **200** | Die Teilnehmerinformationen werden erfolgreich abgerufen.|
| **401** | Die App antwortet mit einem ungültigen Token.|
| **404** | Die Besprechung ist entweder abgelaufen, oder der Teilnehmer konnte nicht gefunden werden.|
| **500** | Die Besprechung ist entweder abgelaufen (mehr als 60 Tage), seit die Besprechung endete, oder die Teilnehmer verfügen nicht über Berechtigungen basierend auf ihrer Rolle.|

### <a name="notificationsignal-api"></a>NotificationSignal-API

Alle Benutzer in einer Besprechung erhalten die Benachrichtigungen, die über die API gesendet `NotificationSignal` werden.

> [!NOTE]
> * Wenn ein Dialogfeld in einer Besprechung aufgerufen wird, wird der Inhalt als Chatnachricht angezeigt.
> * Derzeit wird das Senden von gezielten Benachrichtigungen nicht unterstützt.

`NotificationSignal` Mithilfe der API können Sie Besprechungssignale bereitstellen, die mithilfe der vorhandenen Unterhaltungsbenachrichtigungs-API für den Benutzer-Bot-Chat übermittelt werden. Diese API ermöglicht es Ihnen, basierend auf einer Benutzeraktion, die ein Dialogfeld in der Besprechung anzeigt, ein Signal zu senden. Die API enthält Abfrageparameter, Beispiele und Antwortcodes.

#### <a name="query-parameter"></a>Abfrageparameter

Die `NotificationSignal` API enthält den folgenden Abfrageparameter:

|Wert|Typ|Erforderlich|Beschreibung|
|---|---|----|---|
|**conversationId**| Zeichenfolge | Ja | Der Unterhaltungsbezeichner ist als Teil des Bot-Aufrufs verfügbar. |

#### <a name="examples"></a>Beispiele

Der `Bot ID` wird im Manifest deklariert, und der Bot erhält ein Ergebnisobjekt.

> [!NOTE]
> * Der `completionBotId` Parameter des Parameters ist im `externalResourceUrl` angeforderten Nutzlastbeispiel optional. `Bot ID` wird im Manifest deklariert, und der Bot erhält ein Ergebnisobjekt.
> * Die `externalResourceUrl` Parameter für Breite und Höhe müssen in Pixeln angegeben werden. Um sicherzustellen, dass die Abmessungen innerhalb der zulässigen Grenzwerte liegen, lesen Sie die [Entwurfsrichtlinien.](design/designing-apps-in-meetings.md)
> * Die URL ist die Seite, die als in das Dialogfeld in der Besprechung geladen `<iframe>` wird. Die Domäne muss sich im Array der App `validDomains` in Ihrem App-Manifest befinden.

Die `NotificationSignal` API enthält die folgenden Beispiele:

# <a name="c"></a>[C#](#tab/dotnet)

```csharp
Activity activity = MessageFactory.Text("This is a meeting signal test");

activity.ChannelData = new TeamsChannelData
  {
    Notification = new NotificationInfo()
                    {
                        AlertInMeeting = true,
                        ExternalResourceUrl = "https://teams.microsoft.com/l/bubble/APP_ID?url=<url>&height=<height>&width=<width>&title=<title>&completionBotId=BOT_APP_ID"
                    }
  };
await turnContext.SendActivityAsync(activity).ConfigureAwait(false);
```

# <a name="javascript"></a>[JavaScript](#tab/javascript)

```javascript

const replyActivity = MessageFactory.text('Hi'); // this could be an adaptive card instead
replyActivity.channelData = {
    notification: {
        alertInMeeting: true,
        externalResourceUrl: 'https://teams.microsoft.com/l/bubble/APP_ID?url=<url>&height=<height>&width=<width>&title=<title>&completionBotId=BOT_APP_ID’
    }
};
await context.sendActivity(replyActivity);
```

# <a name="json"></a>[Json](#tab/json)

```http
POST /v3/conversations/{conversationId}/activities

{
    "type": "message",
    "text": "John Phillips assigned you a weekly todo",
    "summary": "Don't forget to meet with Marketing next week",
    "channelData": {
        "notification": {
            "alertInMeeting": true,
            "externalResourceUrl": "https://teams.microsoft.com/l/bubble/APP_ID?url=<url>&height=<height>&width=<width>&title=<title>&completionBotId=BOT_APP_ID"
        }
    },
    "replyToId": "1493070356924"
}
```

---

#### <a name="response-codes"></a>Antwortcodes

Die `NotificationSignal` API enthält die folgenden Antwortcodes:

|Antwortcode|Beschreibung|
|---|---|
| **201** | Die Aktivität mit Signal wird erfolgreich gesendet. |
| **401** | Die App antwortet mit einem ungültigen Token. |
| **403** | Die App kann das Signal nicht senden. Dies kann aus verschiedenen Gründen geschehen, z. B. wenn der Mandantenadministrator die App deaktiviert, die App während der Migration einer Livewebsite blockiert wird usw. In diesem Fall enthält die Nutzlast eine detaillierte Fehlermeldung. |
| **404** | Der Besprechungschat ist nicht vorhanden. |

### <a name="meeting-details-api"></a>Besprechungsdetails-API

> [!NOTE]
> Dieses Feature ist derzeit nur in der [öffentlichen Entwicklervorschau](../resources/dev-preview/developer-preview-intro.md) verfügbar.

Die Besprechungsdetails-API ermöglicht Ihrer App das Abrufen statischer Besprechungsmetadaten. Dies sind Datenpunkte, die sich nicht dynamisch ändern.
Die API ist über Bot Services verfügbar.
#### <a name="pre-requisite"></a>Voraussetzungen
Vor der Verwendung der Besprechungsdetails-API müssen die erforderlichen RSC-Berechtigungen abgerufen werden. Das App-Manifest muss über die folgende webApplicationInfo verfügen:

# <a name="json"></a>[Json](#tab/json)

```"webApplicationInfo": {
    "id": "<bot id>",
    "resource": "https://RscPermission",
    "applicationPermissions": [
      "OnlineMeeting.ReadBasic.Chat"
    ]
  }
 ```

#### <a name="query-parameter"></a>Abfrageparameter

Die Besprechungsdetails-API enthält den folgenden Abfrageparameter:

|Wert|Typ|Erforderlich|Beschreibung|
|---|---|----|---|
|**meetingId**| Zeichenfolge | Ja | Der Besprechungsbezeichner ist über Bot Invoke und Teams Client SDK verfügbar. |

#### <a name="example"></a>Beispiel

Die Besprechungsdetails-API enthält die folgenden Beispiele:

# <a name="c"></a>[C#](#tab/dotnet)

```csharp
var connectorClient = parameters.TurnContext.TurnState.Get<IConnectorClient>();
var creds = connectorClient.Credentials as AppCredentials;
var bearerToken = await creds.GetTokenAsync().ConfigureAwait(false);
var request = new HttpRequestMessage(HttpMethod.Get, new Uri(new Uri(connectorClient.BaseUri.OriginalString), $"v1/meetings/{meetingId}"));
request.Headers.Authorization = new AuthenticationHeaderValue("Bearer", bearerToken);
HttpResponseMessage response = await (connectorClient as ServiceClient<ConnectorClient>).HttpClient.SendAsync(request, CancellationToken.None).ConfigureAwait(false);
string content;
if (response.Content != null)
{
    content = await response.Content.ReadAsStringAsync().ConfigureAwait(false);
}
```

# <a name="javascript"></a>[JavaScript](#tab/javascript)

Nicht verfügbar

# <a name="json"></a>[Json](#tab/json)

```http
GET /v1/meetings/{meetingId}
```

---

Der JSON-Antworttext für die Besprechungsdetails-API lautet wie folgt:

```json
{ 
   "details": { 
        "id": "meeting ID", 
        "msGraphResourceId": "", 
        "scheduledStartTime": "2020-08-21T02:30:00+00:00", 
        "scheduledEndTime": "2020-08-21T03:00:00+00:00", 
        "joinUrl": "https://teams.microsoft.com/l/xx", 
        "title": "All Hands", 
        "type": "Scheduled" 
    }, 
    "conversation": { 
            "isGroup": true, 
            “conversationType”: “groupchat”, 
            "id": "meeting chat ID" 
    }, 
    "organizer": { 
        "id": "<organizer user ID>", 
        "aadObjectId": "<AAD ID>", 
        "tenantId": "<Tenant ID>" 
    }
} 
```

## <a name="real-time-teams-meeting-events"></a>Besprechungsereignisse in Echtzeit Teams

> [!NOTE]
> Dieses Feature ist derzeit nur in der [öffentlichen Entwicklervorschau](../resources/dev-preview/developer-preview-intro.md) verfügbar.

Der Benutzer kann Besprechungsereignisse in Echtzeit empfangen. Sobald eine App einer Besprechung zugeordnet ist, werden die tatsächliche Start- und Besprechungsendzeit für den Bot freigegeben.

Die tatsächliche Anfangs- und Endzeit einer Besprechung unterscheidet sich von der geplanten Start- und Endzeit. Die Besprechungsdetails-API stellt die geplante Start- und Endzeit bereit, während das Ereignis die tatsächliche Start- und Endzeit bereitstellt.

#### <a name="pre-requisite"></a>Voraussetzungen
Das App-Manifest muss über die folgende webApplicationInfo verfügen, um die Besprechungsstart- und -endereignisse erfolgreich empfangen zu können.

# <a name="json"></a>[Json](#tab/json)

```"webApplicationInfo": {
    "id": "<bot id>",
    "resource": "https://RscPermission",
    "applicationPermissions": [
      "OnlineMeeting.ReadBasic.Chat"
    ]
  }
 ```

### <a name="example-of-meeting-start-event-payload"></a>Beispiel für die Nutzlast des Besprechungsstartereignisses

Der folgende Code enthält ein Beispiel für die Nutzlast des Besprechungsstartereignisses:

```json
{ 
    "name": "application/vnd.microsoft.meetingStart", 
    "type": "event", 
    "timestamp": "2021-04-29T16:10:41.1252256Z", 
    "id": "123", 
    "channelId": "msteams", 
    "serviceUrl": "https://microsoft.com", 
    "from": { 
        "id": "userID", 
        "aadObjectId": "aadOnjectId" 
    }, 
    "conversation": { 
        "isGroup": true, 
        "tenantId": "tenantId", 
        "id": "thread id" 
    }, 
    "recipient": { 
        "id": "user Id", 
        "name": "user name" 
    }, 
    "entities": [ 
        { 
            "locale": "en-US", 
            "country": "US", 
            "type": "clientInfo" 
        } 
    ], 
    "channelData": { 
        "tenant": { 
            "id": "channel id" 
        }, 
        "source": null, 
        "meeting": { 
            "id": "meeting id" 
        } 
    }, 
    "value": { 
        "MeetingType": "Scheduled", 
        "Title": "Meeting Start/End Event", 
        "Id":"meeting id", 
        "JoinUrl": "url" 
        "StartTime": "2021-04-29T16:17:17.4388966Z" 
    }, 
    "locale": "en-US" 
}
```

### <a name="example-of-meeting-end-event-payload"></a>Beispiel für die Nutzlast des Besprechungsendereignisses

Der folgende Code enthält ein Beispiel für die Nutzlast des Besprechungsendereignisses:

```json
{ 
    "name": "application/vnd.microsoft.meetingEnd", 
    "type": "event", 
    "timestamp": "2021-04-29T16:17:17.4388966Z", 
    "id": "123", 
    "channelId": "msteams", 
    "serviceUrl": "https://microsoft.com", 
    "from": { 
        "id": "user id", 
        "aadObjectId": "aadObjectId" 
    }, 
    "conversation": { 
        "isGroup": true, 
        "tenantId": "tenantId", 
        "id": "thread id" 
    }, 
    "recipient": { 
        "id": "user id", 
        "name": "user name" 
    }, 
    "entities": [ 
        { 
            "locale": "en-US", 
            "country": "US", 
            "type": "clientInfo" 
        } 
    ], 
    "channelData": { 
        "tenant": { 
            "id": "channel id" 
        }, 
        "source": null, 
        "meeting": { 
            "id": "meeting Id" 
        } 
    }, 
    "value": { 
        "MeetingType": "Scheduled", 
        "Title": "Meeting Start/End Event in Canary", 
        "Id": "19:meeting_NTM3ZDJjOTUtZGRhOS00MzYxLTk5NDAtMzY4M2IzZWFjZGE1@thread.v2", 
        "JoinUrl": "url", 
        "EndTime": "2021-04-29T16:17:17.4388966Z" 
    }, 
    "locale": "en-US" 
}
```

### <a name="example-of-getting-metadata-of-a-meeting"></a>Beispiel für das Abrufen von Metadaten einer Besprechung

Ihr Bot empfängt das Ereignis über den `OnEventActivityAsync` Handler.

Um die JSON-Nutzlast zu deserialisieren, wird ein Modellobjekt eingeführt, um die Metadaten einer Besprechung abzurufen. Die Metadaten einer Besprechung befinden sich in der `value` Eigenschaft in der Ereignisnutzlast. Das `MeetingStartEndEventvalue` Modellobjekt wird erstellt, dessen Membervariablen den Schlüsseln unter der `value` Eigenschaft in der Ereignisnutzlast entsprechen.

Der folgende Code zeigt, wie die Metadaten einer Besprechung erfasst werden, die , `MeetingType` , , und aus einem `Title` `Id` `JoinUrl` `StartTime` `EndTime` Besprechungsstart- und -endereignis besteht:

```csharp
protected override async Task OnEventActivityAsync(
ITurnContext<IEventActivity> turnContext, CancellationToken cancellationToken)
{
    // Event Name is either 'application/vnd.microsoft.meetingStart' or 'application/vnd.microsoft.meetingEnd'
    var meetingEventName = turnContext.Activity.Name;
    // Value contains meeting information (ex: meeting type, start time, etc).
    var meetingEventInfo = turnContext.Activity.Value as JObject; 
    var meetingEventInfoObject =
meetingEventInfo.ToObject<MeetingStartEndEventValue>();
    // Create a very simple adaptive card with meeting information
var attachmentCard = createMeetingStartOrEndEventAttachment(meetingEventName,
meetingEventInfoObject);
    await turnContext.SendActivityAsync(MessageFactory.Attachment(attachmentCard));
}
```

"MeetingStartEndEventvalue.cs" enthält den folgenden Code:

```csharp
public class MeetingStartEndEventValue
{
    public string Id { get; set; }
    public string Title { get; set; }
    public string MeetingType { get; set; }
    public string JoinUrl { get; set; }
    public string StartTime { get; set; }
    public string EndTime { get; set; }
}
```

## <a name="code-sample"></a>Codebeispiel

|Beispielname | Beschreibung | .NET | Node.js |
|----------------|-----------------|--------------|--------------|
| Erweiterbarkeit von Besprechungen | Microsoft Teams Besprechungserweiterungsbeispiel für das Übergeben von Token. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-token-app/csharp) | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-token-app/nodejs) |
| Besprechungsinhalts-Blasen-Bot | Microsoft Teams Besprechungserweiterbarkeitsbeispiel für die Interaktion mit einem Inhaltsblasen-Bot in einer Besprechung. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-content-bubble/csharp) |  [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-content-bubble/nodejs)|
| Meeting MeetingSidePanel | Microsoft Teams Besprechungserweiterungsbeispiel für die Interaktion mit dem Seitenbereich in besprechungsinternen Besprechungen. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-sidepanel/csharp) | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-sidepanel/nodejs)|
| Registerkarte "Details" in der Besprechung | Microsoft Teams Besprechungserweiterbarkeitsbeispiel für das Iteracting mit der Registerkarte "Details" in der Besprechung. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-details-tab/csharp) | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-details-tab/nodejs)|

## <a name="see-also"></a>Siehe auch

* [Entwurfsrichtlinien für Besprechungsdialoge](design/designing-apps-in-meetings.md#use-an-in-meeting-dialog)
* [Teams Authentifizierungsfluss für Registerkarten](../tabs/how-to/authentication/auth-flow-tab.md)
* [Apps für Teams Besprechungen](teams-apps-in-meetings.md)

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Aktivieren und Konfigurieren Ihrer Apps für Teams Besprechungen](enable-and-configure-your-app-for-teams-meetings.md)
