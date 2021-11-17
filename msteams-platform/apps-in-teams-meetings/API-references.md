---
title: API-Referenzen für Besprechungs-Apps
author: surbhigupta
description: Identifizieren der API-Referenzen für Besprechungs-Apps mit Beispielen und Codebeispielen
ms.topic: conceptual
ms.author: lajanuar
ms.localizationpriority: medium
keywords: Teams-Apps besprechungen – Benutzerteilnehmer-Rollen-API – Signalsignalabfrage für Benutzerteilnehmer
ms.openlocfilehash: ba7996e0c33823c3f296d18350ea33421c844c68
ms.sourcegitcommit: 1ac0bd55adfd49c42cd870dc71ceca3dcac70941
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/16/2021
ms.locfileid: "61041629"
---
# <a name="meeting-apps-api-references"></a>API-Referenzen für Besprechungs-Apps

Die Besprechungserweiterungen bieten APIs zum Transformieren der Besprechungsumgebung:

* Erstellen von Apps oder Integrieren vorhandener Apps innerhalb des Besprechungslebenszyklus.
* Verwenden Sie die APIs, um Ihre App auf die Besprechung aufmerksam zu machen.
* Wählen Sie die APIs aus, die Sie verwenden möchten, um die Besprechungserfahrung zu verbessern.

Die folgende Tabelle enthält eine Liste der APIs:

|API|Beschreibung|Anforderung|Source|
|---|---|----|---|
|**GetUserContext**| Mit dieser API können Sie Kontextinformationen abrufen, um relevante Inhalte auf einer Teams Registerkarte anzuzeigen. |_**microsoftTeams.getContext( ( ) => { /*...* / } )**_|Microsoft Teams Client SDK|
|**GetParticipant**| Diese API ermöglicht es einem Bot, Teilnehmerinformationen nach Besprechungs-ID und Teilnehmer-ID abzurufen. |**GET** _**/v1/meetings/{meetingId}/participants/{participantId}?tenantId={tenantId}**_ |Microsoft Bot Framework SDK|
|**NotificationSignal** | Mit dieser API können Sie Besprechungssignale bereitstellen, die mithilfe der vorhandenen Unterhaltungsbenachrichtigungs-API für den Benutzer-Bot-Chat übermittelt werden. Sie können ein Signal basierend auf einer Benutzeraktion senden, die ein Dialogfeld in der Besprechung anzeigt. |**POST** _**/v3/conversations/{conversationId}/activities**_|Microsoft Bot Framework SDK|
|**Besprechungsdetails** | Mit dieser API können Sie statische Besprechungsmetadaten abrufen. |**GET** _**/v1/meetings/{meetingId}**_| Bot SDK |

Die folgende Tabelle enthält die Bot Framework SDK-Methoden für die APIs:

|API|Bot Framework SDK-Methode|
|---|---|
|**GetParticipant**| `GetMeetingParticipantAsync (Microsoft.Bot.Builder.ITurnContext turnContext, string meetingId = default, string participantId = default, string tenantId = default, System.Threading.CancellationToken cancellationToken = default);` |
|**NotificationSignal** | `activity.TeamsNotifyUser(true, "https://teams.microsoft.com/l/bubble/APP_ID?url=&height=&width=&title=<title>&completionBotId=BOT_APP_ID");` |
|**Besprechungsdetails** | `TeamsMeetingInfo (string id = default);` |

## <a name="getusercontext-api"></a>GetUserContext-API

Informationen zum Identifizieren und Abrufen von Kontextinformationen für Ihre Registerkarteninhalte finden Sie unter Abrufen des [Kontexts für Ihre Teams Registerkarte.](../tabs/how-to/access-teams-context.md#get-context-by-using-the-microsoft-teams-javascript-library) `meetingId` Wird von einer Registerkarte verwendet, wenn sie im Besprechungskontext ausgeführt wird, und wird für die Antwortnutzlast hinzugefügt.

## <a name="getparticipant-api"></a>GetParticipant-API

> [!NOTE]
> * Teilnehmerrollen nicht zwischenspeichern, da der Besprechungsorganisator die Rollen jederzeit ändern kann.
> * Teams unterstützt derzeit keine großen Verteilerlisten oder Listengrößen von mehr als 350 Teilnehmern für die `GetParticipant` API.

Die `GetParticipant` API ermöglicht es einem Bot, Teilnehmerinformationen nach Besprechungs-ID und Teilnehmer-ID abzurufen. Die API enthält Abfrageparameter, Beispiele und Antwortcodes.

### <a name="query-parameters"></a>Abfrageparameter

Die `GetParticipant` API enthält die folgenden Abfrageparameter:

|Wert|Typ|Erforderlich|Beschreibung|
|---|---|----|---|
|**meetingId**| String | Ja | Der Besprechungsbezeichner ist über Bot Invoke und Teams Client SDK verfügbar.|
|**participantId**| String | Ja | Die Teilnehmer-ID ist die Benutzer-ID. Es ist in Tab SSO, Bot Invoke und Teams Client SDK verfügbar. Es wird empfohlen, eine Teilnehmer-ID vom Tab-SSO abzurufen. |
|**tenantId**| Zeichenfolge | Ja | Die Mandanten-ID ist für die Mandantenbenutzer erforderlich. Es ist in Tab SSO, Bot Invoke und Teams Client SDK verfügbar. Es wird empfohlen, eine Mandanten-ID vom Tab-SSO abzurufen. | 

### <a name="example"></a>Beispiel

Die `GetParticipant` API enthält die folgenden Beispiele:

# <a name="c"></a>[C#](#tab/dotnet)

```csharp
protected override async Task OnMessageActivityAsync(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
{
  TeamsMeetingParticipant participant = await TeamsInfo.GetMeetingParticipantAsync(turnContext, "yourMeetingId", "yourParticipantId", "yourParticipantTenantId").ConfigureAwait(false);
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

# <a name="json"></a>[JSON](#tab/json)

```http
GET /v1/meetings/{meetingId}/participants/{participantId}?tenantId={tenantId}
```

---

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

### <a name="response-codes"></a>Antwortcodes

Die `GetParticipant` API gibt die folgenden Antwortcodes zurück:

|Antwortcode|Beschreibung|
|---|---|
| **403** | Das Abrufen von Teilnehmerinformationen wird nicht für die App freigegeben. Wenn die App nicht in der Besprechung installiert ist, löst sie die häufigste Fehlerantwort 403 aus. Wenn der Mandantenadministrator die App während der Migration einer Livewebsite deaktiviert oder blockiert, wird die 403-Fehlerantwort ausgelöst. |
| **200** | Die Teilnehmerinformationen werden erfolgreich abgerufen.|
| **401** | Die App antwortet mit einem ungültigen Token.|
| **404** | Die Besprechung ist entweder abgelaufen, oder der Teilnehmer konnte nicht gefunden werden.|

## <a name="notificationsignal-api"></a>NotificationSignal-API

Alle Benutzer in einer Besprechung erhalten die Benachrichtigungen, die über die API gesendet `NotificationSignal` werden.

> [!NOTE]
> * Wenn ein Dialogfeld in einer Besprechung aufgerufen wird, wird der Inhalt als Chatnachricht angezeigt.
> * Derzeit wird das Senden von gezielten Benachrichtigungen nicht unterstützt.

`NotificationSignal` Mithilfe der API können Sie Besprechungssignale bereitstellen, die mithilfe der vorhandenen Unterhaltungsbenachrichtigungs-API für den Benutzer-Bot-Chat übermittelt werden. Diese API ermöglicht es Ihnen, basierend auf einer Benutzeraktion, die ein Dialogfeld in der Besprechung anzeigt, ein Signal zu senden. Die API enthält Abfrageparameter, Beispiele und Antwortcodes.

### <a name="query-parameter"></a>Abfrageparameter

Die `NotificationSignal` API enthält den folgenden Abfrageparameter:

|Wert|Typ|Erforderlich|Beschreibung|
|---|---|----|---|
|**conversationId**| Zeichenfolge | Ja | Der Unterhaltungsbezeichner ist als Teil des Bot-Aufrufs verfügbar. |

### <a name="examples"></a>Beispiele

Der `Bot ID` wird im Manifest deklariert, und der Bot erhält ein Ergebnisobjekt.

> [!NOTE]
> * Der `completionBotId` Parameter des Parameters ist im `externalResourceUrl` angeforderten Nutzlastbeispiel optional. `Bot ID` wird im Manifest deklariert, und der Bot erhält ein Ergebnisobjekt.
> * Die `externalResourceUrl` Parameter für Breite und Höhe müssen in Pixeln angegeben werden. Um sicherzustellen, dass die Abmessungen innerhalb der zulässigen Grenzwerte liegen, lesen Sie die [Entwurfsrichtlinien.](design/designing-apps-in-meetings.md)
> * Die URL ist die Seite, die als in das Dialogfeld in der Besprechung geladen `<iframe>` wird. Die Domäne muss sich im Array der App `validDomains` in Ihrem App-Manifest befinden.

Die `NotificationSignal` API enthält die folgenden Beispiele:

# <a name="c"></a>[C#](#tab/dotnet)

```csharp
Activity activity = MessageFactory.Text("This is a meeting signal test");
activity.TeamsNotifyUser(true, "https://teams.microsoft.com/l/bubble/APP_ID?url=<url>&height=<height>&width=<width>&title=<title>&completionBotId=BOT_APP_ID");
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

# <a name="json"></a>[JSON](#tab/json)

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

### <a name="response-codes"></a>Antwortcodes

Die `NotificationSignal` API enthält die folgenden Antwortcodes:

|Antwortcode|Beschreibung|
|---|---|
| **201** | Die Aktivität mit Signal wird erfolgreich gesendet. |
| **401** | Die App antwortet mit einem ungültigen Token. |
| **403** | Die App kann das Signal nicht senden. Der Antwortcode 403 kann aus verschiedenen Gründen auftreten, z. B. wenn der Mandantenadministrator die App während der Migration der Livewebsite deaktiviert und blockiert. In diesem Fall enthält die Nutzlast eine detaillierte Fehlermeldung. |
| **404** | Der Besprechungschat ist nicht vorhanden. |

## <a name="meeting-details-api"></a>Besprechungsdetails-API

> [!NOTE]
> Dieses Feature ist derzeit nur in der [öffentlichen Entwicklervorschau](../resources/dev-preview/developer-preview-intro.md) verfügbar.

Die Besprechungsdetails-API ermöglicht Ihrer App das Abrufen statischer Besprechungsmetadaten. Die Metadaten stellen Datenpunkte bereit, die sich nicht dynamisch ändern.
Die API ist über Bot Services verfügbar.

### <a name="prerequisite"></a>Voraussetzungen

Um die Besprechungsdetails-API zu verwenden, müssen Sie RSC-Berechtigungen abrufen. Verwenden Sie das folgende Beispiel, um die Eigenschaft Ihres App-Manifests zu `webApplicationInfo` konfigurieren:

```json
"webApplicationInfo": {
    "id": "<bot id>",
    "resource": "https://RscPermission",
    "applicationPermissions": [
      "OnlineMeeting.ReadBasic.Chat"
    ]
}
 ```
 
### <a name="query-parameter"></a>Abfrageparameter

Die Besprechungsdetails-API enthält den folgenden Abfrageparameter:

|Wert|Typ|Erforderlich|Beschreibung|
|---|---|----|---|
|**meetingId**| Zeichenfolge | Ja | Der Besprechungsbezeichner ist über Bot Invoke und Teams Client SDK verfügbar. |

### <a name="example"></a>Beispiel

Die Besprechungsdetails-API enthält die folgenden Beispiele:

# <a name="c"></a>[C#](#tab/dotnet)

```csharp
MeetingInfo result = await TeamsInfo.GetMeetingInfoAsync(turnContext);
await turnContext.SendActivityAsync(JsonConvert.SerializeObject(result));
```

# <a name="javascript"></a>[JavaScript](#tab/javascript)

Nicht verfügbar

# <a name="json"></a>[JSON](#tab/json)

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

Der Benutzer kann Besprechungsereignisse in Echtzeit empfangen. Sobald eine App einer Besprechung zugeordnet ist, werden die tatsächliche Start- und Endzeit der Besprechung für den Bot freigegeben.

Die tatsächliche Start- und Endzeit einer Besprechung unterscheidet sich von der geplanten Start- und Endzeit. Die Besprechungsdetails-API stellt die geplante Start- und Endzeit bereit. Das Ereignis gibt die tatsächliche Start- und Endzeit an.

### <a name="prerequisite"></a>Voraussetzungen

Ihr App-Manifest muss über die `webApplicationInfo` Eigenschaft verfügen, um die Besprechungsstart- und -endereignisse zu empfangen. Verwenden Sie das folgende Beispiel, um Ihr Manifest zu konfigurieren:

```json
"webApplicationInfo": {
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
        "Id": "meeting id", 
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
     
> [!NOTE]      
> * Abrufen der Besprechungs-ID von `turnContext.ChannelData` .    
> * Verwenden Sie die Unterhaltungs-ID nicht als Besprechungs-ID.     
> * Verwenden Sie keine Besprechungs-ID aus der Nutzlast für `turncontext.activity.value` Besprechungsereignisse. 
      
Der folgende Code zeigt, wie die Metadaten einer Besprechung erfasst werden, die , `MeetingType` , , und aus einem `Title` `Id` `JoinUrl` `StartTime` `EndTime` Besprechungsstart-/-end-Ereignis besteht:

Besprechungsstartereignis
```csharp
protected override async Task OnTeamsMeetingStartAsync(MeetingEndEventDetails meeting, ITurnContext<IEventActivity> turnContext, CancellationToken cancellationToken)
{
    await turnContext.SendActivityAsync(JsonConvert.SerializeObject(meeting));
}
```

Besprechungsendereignis
```csharp
protected override async Task OnTeamsMeetingEndAsync(MeetingEndEventDetails meeting, ITurnContext<IEventActivity> turnContext, CancellationToken cancellationToken)
{
    await turnContext.SendActivityAsync(JsonConvert.SerializeObject(meeting));
}
```

## <a name="code-sample"></a>Codebeispiel

|Beispielname | Beschreibung | C# | Node.js | 
|----------------|-----------------|--------------|--------------|
| Erweiterbarkeit von Besprechungen | Microsoft Teams Beispiel für die Erweiterbarkeit von Besprechungen zum Übergeben von Token. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-token-app/csharp) | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-token-app/nodejs) |
| Besprechungsinhalts-Blasen-Bot | Microsoft Teams Besprechungserweiterungsbeispiel für die Interaktion mit einem Inhaltsblasen-Bot in einer Besprechung. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-content-bubble/csharp) |  [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-content-bubble/nodejs)|
| Meeting MeetingSidePanel | Microsoft Teams Besprechungserweiterungsbeispiel für die Interaktion mit dem Seitenbereich in besprechungsinternen Besprechungen. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-sidepanel/csharp) | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-sidepanel/nodejs)|
| Registerkarte "Details" in der Besprechung | Microsoft Teams Besprechungserweiterungsbeispiel für die Interaktion mit der Registerkarte "Details" in der Besprechung. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-details-tab/csharp) | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-details-tab/nodejs)|
|Beispiel für Besprechungsereignisse|Beispiel-App zum Anzeigen von Teams Besprechungsereignissen in Echtzeit|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-events/csharp)|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-events/nodejs)|
|Beispiel für die Besprechungsrekrutierung|Beispiel-App zum Anzeigen der Besprechungserfahrung für das Einstellungsszenario.|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meeting-recruitment-app/csharp)|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meeting-recruitment-app/nodejs)|
|App-Installation mit QR-Code|Beispiel-App, die den QR-Code generiert und die App mit dem QR-Code installiert|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-installation-using-qr-code/csharp)|[Anzeigen](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-installation-using-qr-code/nodejs)|

## <a name="see-also"></a>Siehe auch

* [Teams Authentifizierungsfluss für Registerkarten](../tabs/how-to/authentication/auth-flow-tab.md)
* [Apps für Teams Besprechungen](teams-apps-in-meetings.md)
