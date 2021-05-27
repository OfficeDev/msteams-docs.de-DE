---
title: Voraussetzungen und API-Verweise für Apps in Teams-Besprechungen
author: laujan
description: Arbeiten mit Apps für Teams Besprechungen
ms.topic: conceptual
ms.author: lajanuar
localization_priority: Normal
keywords: Rollen-API für Teams-Apps-Besprechungen für Benutzerteilnehmer
ms.openlocfilehash: aeedd6ff4ee1e075d24020d872b5ebd216be4fb0
ms.sourcegitcommit: 2c8b35899dd845acd66f1f927e40d99523c29a91
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/27/2021
ms.locfileid: "52684642"
---
# <a name="prerequisites-and-api-references-for-apps-in-teams-meetings"></a>Voraussetzungen und API-Verweise für Apps in Teams-Besprechungen

Um die Funktionen Ihrer Apps über den gesamten Besprechungslebenszyklus zu erweitern, Teams Sie mit Apps für Teams arbeiten. Sie müssen die Voraussetzungen durchgehen und die Besprechungs-Apps-API-Verweise verwenden, um die Besprechungserfahrung zu verbessern.

## <a name="prerequisites"></a>Voraussetzungen

Bevor Sie mit Apps für Teams arbeiten, müssen Sie folgendes wissen:

* Sie müssen wissen, wie Sie apps Teams entwickeln. Weitere Informationen finden Sie unter [Teams App Development](../overview.md).

* Sie müssen das Teams-App-Manifest aktualisieren, um anzugeben, dass die App für Besprechungen verfügbar ist. Weitere Informationen finden Sie unter [App-Manifest](enable-and-configure-your-app-for-teams-meetings.md#update-your-app-manifest).

* Ihre App muss konfigurierbare Registerkarten im Gruppenchatbereich unterstützen, damit Ihre App im Besprechungslebenszyklus als Registerkarte funktioniert. Weitere Informationen finden Sie unter [groupchat scope](../resources/schema/manifest-schema.md#configurabletabs) und [build a group tab](../build-your-first-app/build-channel-tab.md).

* Sie müssen die allgemeinen Richtlinien Teams Registerkartendesigns für Szenarien vor und nach Besprechungen einhalten. Informationen zu Erfahrungen während Besprechungen finden Sie in den Entwurfsrichtlinien für Besprechungsdialogfeldern und Besprechungsdialogfeldern. Weitere Informationen finden Sie unter [Teams Richtlinien](../tabs/design/tabs.md)für den Registerkartenentwurf, Richtlinien zum Entwerfen von Registerkarten [in](../apps-in-teams-meetings/design/designing-apps-in-meetings.md#use-an-in-meeting-tab)Besprechungen und Entwurfsrichtlinien für [Besprechungsdialogdialog.](../apps-in-teams-meetings/design/designing-apps-in-meetings.md#use-an-in-meeting-dialog)

* Sie müssen den Bereich `groupchat` unterstützen, um Ihre App in Chats vor und nach besprechungen zu aktivieren. Mit der App vor der Besprechung können Sie Besprechungs-Apps finden und hinzufügen und Aufgaben vor besprechungen ausführen. Mit der App nach der Besprechung können Sie die Ergebnisse der Besprechung anzeigen, z. B. Umfrageergebnisse oder Feedback.

* Die Parameter für die Besprechungs-API-URL müssen `meetingId` über `userId` , und `tenantId` verfügen. Diese sind im Rahmen der Teams Client SDK und Bot-Aktivität verfügbar. Darüber hinaus können Sie zuverlässige Informationen für Benutzer-ID und Mandanten-ID mithilfe [der Registerkarte SSO-Authentifizierung abrufen.](../tabs/how-to/authentication/auth-aad-sso.md)

* Die `GetParticipant` API muss über eine Botregistrierung und -ID verfügen, um Authentifizierungstoken zu generieren. Weitere Informationen finden Sie unter [Botregistrierung und ID](../build-your-first-app/build-bot.md).

* Damit Ihre App in Echtzeit aktualisiert werden kann, muss sie basierend auf den Ereignisaktivitäten in der Besprechung auf dem neuesten Stand sein. Diese Ereignisse können sich innerhalb des Dialogfelds in der Besprechung und in anderen Phasen des gesamten Besprechungslebenszyklus finden. Das Dialogfeld In-Meeting finden Sie unter Completion `bot Id` parameter in `NotificationSignal` API.

* Die Besprechungsdetails-API muss über eine Botregistrierung und bot-ID verfügen. Es erfordert Bot SDK, um zu `TurnContext` erhalten.

* Bei Besprechungsereignissen in Echtzeit müssen Sie mit dem über das Bot SDK verfügbaren `TurnContext` Objekt vertraut sein. Das `Activity` Objekt in enthält die Nutzlast mit der `TurnContext` tatsächlichen Start- und Endzeit. Für Echtzeit-Besprechungsereignisse ist eine registrierte Bot-ID von der Teams erforderlich.

Nachdem Sie die Voraussetzungen erfüllt haben, können Sie die API-Verweise auf die Besprechungs-Apps , , und die Besprechungsdetails-API verwenden, mit der Sie mithilfe von Attributen auf Informationen zugreifen und relevante `GetUserContext` `GetParticipant` Inhalte anzeigen `NotificationSignal` können.

## <a name="meeting-apps-api-references"></a>Apireferenzen für Besprechungs-Apps

Die neuen Besprechungsergehnmöglichkeiten bieten Ihnen APIs, die die Besprechungserfahrung transformieren. Mit dieser neuen Funktion können Sie Apps erstellen oder vorhandene Apps innerhalb des Besprechungslebenszyklus integrieren. Sie können die APIs verwenden, um Ihre App auf die Besprechung aufmerksam zu machen. Sie können auswählen, welche APIs Sie verwenden möchten, um die Besprechungserfahrung zu verbessern.

Die folgende Tabelle enthält eine Liste dieser APIs:

|API|Beschreibung|Anforderung|Quelle|
|---|---|----|---|
|**GetUserContext**| Mit dieser API können Sie Kontextinformationen abrufen, um relevante Inhalte auf einer Registerkarte Teams anzuzeigen. |_**microsoftTeams.getContext( ( ) => { /*...* / } )**_|Microsoft Teams Client SDK|
|**GetParticipant**| Mit dieser API kann ein Bot Teilnehmerinformationen nach Besprechungs-ID und Teilnehmer-ID abrufen. |**GET** _**/v1/meetings/{meetingId}/participants/{participantId}?tenantId={tenantId}**_ |Microsoft Bot Framework SDK|
|**NotificationSignal** | Mit dieser API können Sie Besprechungssignale bereitstellen, die mithilfe der vorhandenen Unterhaltungsbenachrichtigungs-API für den Benutzer-Bot-Chat übermittelt werden. Damit können Sie basierend auf der Benutzeraktion, die ein Dialogfeld in der Besprechung zeigt, ein Signal senden. |**POST** _**/v3/conversations/{conversationId}/activities**_|Microsoft Bot Framework SDK|
|**Besprechungsdetails** | Mit dieser API können Sie statische Besprechungsmetadaten abrufen. |**GET** _**/v1/meetings/{meetingId}**_| Bot SDK |

### <a name="getusercontext-api"></a>GetUserContext-API

Informationen zum Identifizieren und Abrufen von Kontextinformationen für Ihre Registerkarteninhalte finden Sie unter [Abrufen des Kontexts für Teams Registerkarte](../tabs/how-to/access-teams-context.md#getting-context-by-using-the-microsoft-teams-javascript-library). `meetingId`wird von einer Registerkarte verwendet, wenn sie im Besprechungskontext ausgeführt wird, und wird für die Antwortnutzlast hinzugefügt.

### <a name="getparticipant-api"></a>GetParticipant-API

> [!NOTE]
> * Zwischenspeichern Sie die Teilnehmerrollen nicht, da der Besprechungsorganisator die Rollen jederzeit ändern kann.
> * Teams unterstützt derzeit keine großen Verteilerlisten oder Listengrößen von mehr als 350 Teilnehmern für die `GetParticipant` API.

Die `GetParticipant` API ermöglicht einem Bot das Abrufen von Teilnehmerinformationen nach Besprechungs-ID und Teilnehmer-ID. Die API enthält Abfrageparameter, Beispiele und Antwortcodes.

#### <a name="query-parameters"></a>Abfrageparameter

Die `GetParticipant` API enthält die folgenden Abfrageparameter:

|Wert|Typ|Erforderlich|Beschreibung|
|---|---|----|---|
|**meetingId**| Zeichenfolge | Ja | Der Besprechungsbezeichner ist über Bot Invoke und Teams Client SDK verfügbar.|
|**participantId**| Zeichenfolge | Ja | Die Teilnehmer-ID ist die Benutzer-ID. Sie ist in Tab SSO, Bot Invoke und Teams Client SDK verfügbar. Es wird empfohlen, eine Teilnehmer-ID aus dem Tab-SSO zu erhalten. |
|**tenantId**| Zeichenfolge | Ja | Die Mandanten-ID ist für die Mandantenbenutzer erforderlich. Sie ist in Tab SSO, Bot Invoke und Teams Client SDK verfügbar. Es wird empfohlen, eine Mandanten-ID aus dem Tab-SSO zu erhalten. |

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

Der JSON-Antworttext für `GetParticipant` API ist:

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
| **403** | Die App darf keine Teilnehmerinformationen erhalten. Dies ist die häufigste Fehlerantwort und wird ausgelöst, wenn die App nicht in der Besprechung installiert ist. Beispiel: Wenn die App vom Mandantenadministrator deaktiviert oder während der Livewebsitemigration blockiert wird.|
| **200** | Die Teilnehmerinformationen werden erfolgreich abgerufen.|
| **401** | Die App antwortet mit einem ungültigen Token.|
| **404** | Die Besprechung ist entweder abgelaufen, oder der Teilnehmer wurde nicht gefunden.|
| **500** | Die Besprechung ist entweder (mehr als 60 Tage) seit dem Ende der Besprechung abgelaufen, oder die Teilnehmer verfügen nicht über Berechtigungen basierend auf ihrer Rolle.|

### <a name="notificationsignal-api"></a>NotificationSignal-API

Alle Benutzer in einer Besprechung erhalten die über die API gesendeten `NotificationSignal` Benachrichtigungen.

> [!NOTE]
> * Wenn ein Dialogfeld in der Besprechung aufgerufen wird, wird der Inhalt als Chatnachricht angezeigt.
> * Derzeit wird das Senden gezielter Benachrichtigungen nicht unterstützt.

`NotificationSignal` Mit der API können Sie Besprechungssignale bereitstellen, die mithilfe der vorhandenen Unterhaltungsbenachrichtigungs-API für den Benutzer-Bot-Chat übermittelt werden. Mit dieser API können Sie basierend auf der Benutzeraktion, die ein Dialogfeld in der Besprechung zeigt, ein Signal senden. Die API enthält Abfrageparameter, Beispiele und Antwortcodes.

#### <a name="query-parameter"></a>Abfrageparameter

Die `NotificationSignal` API enthält den folgenden Abfrageparameter:

|Wert|Typ|Erforderlich|Beschreibung|
|---|---|----|---|
|**conversationId**| Zeichenfolge | Ja | Der Unterhaltungsbezeichner ist als Teil von Bot Invoke verfügbar. |

#### <a name="examples"></a>Beispiele

Der `Bot ID` wird im Manifest deklariert, und der Bot empfängt ein Ergebnisobjekt.

> [!NOTE]
> * Der `completionBotId` Parameter von ist im `externalResourceUrl` angeforderten Nutzlastbeispiel optional. `Bot ID` wird im Manifest deklariert, und der Bot empfängt ein Ergebnisobjekt.
> * Die `externalResourceUrl` Parameter für Breite und Höhe müssen in Pixel angegeben werden. Um sicherzustellen, dass die Abmessungen innerhalb der zulässigen Grenzwerte liegen, finden Sie unter [Entwurfsrichtlinien](design/designing-apps-in-meetings.md).
> * Die URL ist die Im Besprechungsdialogfeld `<iframe>` geladene Seite. Die Domäne muss sich im Array der App `validDomains` im App-Manifest befinden.

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
| **403** | Die App kann das Signal nicht senden. Dies kann aus verschiedenen Gründen geschehen, z. B. wenn der Mandantenadministrator die App deaktiviert, die App während der Livewebsitemigration blockiert wird und so weiter. In diesem Fall enthält die Nutzlast eine detaillierte Fehlermeldung. |
| **404** | Der Besprechungschat ist nicht vorhanden. |

### <a name="meeting-details-api"></a>Api für Besprechungsdetails

> [!NOTE]
> Dieses Feature ist derzeit nur in der [öffentlichen Entwicklervorschau](../resources/dev-preview/developer-preview-intro.md) verfügbar.

Mit der Besprechungsdetails-API kann Ihre App statische Besprechungsmetadaten abrufen. Dies sind Datenpunkte, die sich nicht dynamisch ändern.
Die API ist über Bot Services verfügbar.

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

## <a name="real-time-teams-meeting-events"></a>Echtzeit-Teams Besprechungsereignisse

> [!NOTE]
> Dieses Feature ist derzeit nur in der [öffentlichen Entwicklervorschau](../resources/dev-preview/developer-preview-intro.md) verfügbar.

Der Benutzer kann Besprechungsereignisse in Echtzeit empfangen. Sobald eine App einer Besprechung zugeordnet ist, werden der tatsächliche Beginn und die Endzeit der Besprechung für den Bot freigegeben.

Die tatsächliche Start- und Endzeit einer Besprechung unterscheiden sich von der geplanten Start- und Endzeit. Die Besprechungsdetails-API stellt die geplante Start- und Endzeit bereit, während das Ereignis die tatsächliche Start- und Endzeit liefert.

### <a name="example-of-meeting-start-event-payload"></a>Beispiel für die Nutzlast des Besprechungsstartereigniss

Der folgende Code enthält ein Beispiel für die Nutzlast des Besprechungsstartereigniss:

```json
{ 
    "name": "Microsoft/MeetingStart", 
    "type": "event", 
    "timestamp": "2021-04-29T16:10:41.1252256Z", 
    "id": "123", 
    "channelId": "msteams", 
    "serviceUrl": "https://microsoft.com", 
    "from": { 
        "id": "userID", 
        "name": "", 
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

### <a name="example-of-meeting-end-event-payload"></a>Beispiel für die Nutzlast des Besprechungsendereigniss

Der folgende Code enthält ein Beispiel für die Nutzlast des Besprechungsendereigniss:

```json
{ 
    "name": "Microsoft/MeetingEnd", 
    "type": "event", 
    "timestamp": "2021-04-29T16:17:17.4388966Z", 
    "id": "123", 
    "channelId": "msteams", 
    "serviceUrl": "https://microsoft.com", 
    "from": { 
        "id": "user id", 
        "name": "", 
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

Zum Deserialisieren der json-Nutzlast wird ein Modellobjekt eingeführt, um die Metadaten einer Besprechung zu erhalten. Die Metadaten einer Besprechung befinden sich in der `value` Eigenschaft in der Ereignisnutzlast. Das `MeetingStartEndEventvalue` Modellobjekt wird erstellt, dessen Membervariablen den Schlüsseln unter der `value` Eigenschaft in der Ereignisnutzlast entsprechen.

Der folgende Code zeigt, wie Sie die Metadaten einer Besprechung erfassen, die , , , ist, und von einem `MeetingType` `Title` `Id` Besprechungsanfangs- und `JoinUrl` `StartTime` `EndTime` -endereignis:

```csharp
protected override async Task OnEventActivityAsync(
ITurnContext<IEventActivity> turnContext, CancellationToken cancellationToken)
{
    // Event Name is either `Microsoft/MeetingStart` or `Microsoft/MeetingEnd`
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

MeetingStartEndEventvalue.cs enthält den folgenden Code:

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
| Erweiterbarkeit von Besprechungen | Microsoft Teams Beispiel für die Besprechungsergehnbarkeit zum Übergeben von Token. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-token-app/csharp) | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-token-app/nodejs) |
| Besprechungsinhaltsblasen-Bot | Microsoft Teams beispiel für die Besprechungsergehnbarkeit für die Interaktion mit dem Inhaltsblasenbot in einer Besprechung. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-content-bubble/csharp) |  [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-content-bubble/nodejs)|
| Meeting meetingSidePanel | Microsoft Teams beispiel für die Besprechungsergehnbarkeit für die Interaktion mit dem Seitenbereich in der Besprechung. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-sidepanel/csharp) | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-sidepanel/nodejs)|

## <a name="see-also"></a>Weitere Artikel

* [Entwurfsrichtlinien für Besprechungsdialogdialog](design/designing-apps-in-meetings.md#use-an-in-meeting-dialog)
* [Teams Authentifizierungsfluss für Registerkarten](../tabs/how-to/authentication/auth-flow-tab.md)
* [Apps für Teams Besprechungen](teams-apps-in-meetings.md)

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Aktivieren und Konfigurieren Ihrer Apps für Teams Besprechungen](enable-and-configure-your-app-for-teams-meetings.md)
