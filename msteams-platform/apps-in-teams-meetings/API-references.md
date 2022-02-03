---
title: API-Referenzen für Besprechungs-Apps
author: surbhigupta
description: Identifizieren der API-Referenzen für Besprechungs-Apps mit Beispielen und Codebeispielen
ms.topic: conceptual
ms.author: lajanuar
ms.localizationpriority: medium
keywords: Teams-Apps besprechungen – Benutzerteilnehmer-Rollen-API – Signalsignalabfrage für Benutzerteilnehmer
ms.openlocfilehash: dd46dc2622915055e46e07ae34d48c690d6d8d8e
ms.sourcegitcommit: 58a24422bb04a529b6629a56803ed2efabc17cb1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/02/2022
ms.locfileid: "62323148"
---
# <a name="meeting-apps-api-references"></a>API-Referenzen für Besprechungs-Apps

Die Besprechungserweiterungen bieten APIs zum Transformieren der Besprechungsumgebung:

* Erstellen von Apps oder Integrieren vorhandener Apps innerhalb des Besprechungslebenszyklus.
* Verwenden Sie die APIs, um Ihre App auf die Besprechung aufmerksam zu machen.
* Wählen Sie die APIs aus, die Sie verwenden möchten, um die Besprechungserfahrung zu verbessern.

Die folgende Tabelle enthält eine Liste der APIs:

|API|Beschreibung|Anforderung|Source|
|---|---|----|---|
|**GetUserContext**| Ermöglicht das Abrufen von Kontextinformationen zum Anzeigen relevanter Inhalte auf einer Teams Registerkarte. |_**microsoftTeams.getContext( ( ) => { /*...* / } )**_|Microsoft Teams-Client-SDK|
|**GetParticipant**| Ermöglicht es einem Bot, Teilnehmerinformationen nach Besprechungs-ID und Teilnehmer-ID abzurufen. |**GET** _**/v1/meetings/{meetingId}/participants/{participantId}?tenantId={tenantId}**_ |Microsoft Bot Framework SDK|
|**NotificationSignal** | Ermöglicht die Bereitstellung von Besprechungssignalen, die mithilfe der vorhandenen Unterhaltungsbenachrichtigungs-API für den Benutzer-Bot-Chat übermittelt werden. Sie können ein Signal basierend auf einer Benutzeraktion senden, die ein Dialogfeld in der Besprechung anzeigt. |**POST** _**/v3/conversations/{conversationId}/activities**_|Microsoft Bot Framework SDK|
|**Besprechungsdetails** | Ermöglicht das Abrufen statischer Besprechungsmetadaten. |**GET** _**/v1/meetings/{meetingId}**_| Bot SDK |
|**WARENKORB**|Ermöglicht das Posten von Beschriftungen für eine Besprechung, die gestartet wurde.|**POST /cartcaption?meetingid=04751eac-30e6-47d9-9c3f-0b4ebe8e30d9&token=04751eac&lang=en-us HTTP/1.1**|Microsoft Teams-Client-SDK|

## <a name="getusercontext-api"></a>GetUserContext-API

Informationen zum Identifizieren und Abrufen von Kontextinformationen für Ihre Registerkarteninhalte finden Sie unter [Abrufen des Kontexts für Ihre Teams Registerkarte](../tabs/how-to/access-teams-context.md#get-context-by-using-the-microsoft-teams-javascript-library). `meetingId` Wird von einer Registerkarte verwendet, wenn sie im Besprechungskontext ausgeführt wird, und wird für die Antwortnutzlast hinzugefügt.

## <a name="getparticipant-api"></a>GetParticipant-API

> [!NOTE]
> * Teilnehmerrollen nicht zwischenspeichern, da der Besprechungsorganisator die Rollen jederzeit ändern kann.
> * Teams unterstützt derzeit keine großen Verteilerlisten oder Listengrößen von mehr als 350 Teilnehmern für die `GetParticipant` API.

Die `GetParticipant` API ermöglicht es einem Bot, Teilnehmerinformationen nach Besprechungs-ID und Teilnehmer-ID abzurufen. Die API enthält Abfrageparameter, Beispiele und Antwortcodes.

### <a name="query-parameters"></a>Abfrageparameter

Die `GetParticipant` API enthält die folgenden Abfrageparameter:

|Wert|Typ|Erforderlich|Beschreibung|
|---|---|----|---|
|**meetingId**| Zeichenfolge | Ja | Der Besprechungsbezeichner ist über Bot Invoke und Teams Client SDK verfügbar.|
|**participantId**| Zeichenfolge | Ja | Die Teilnehmer-ID ist die Benutzer-ID. Es ist in Tab SSO, Bot Invoke und Teams Client SDK verfügbar. Es wird empfohlen, eine Teilnehmer-ID vom Tab-SSO abzurufen. |
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

Alle Benutzer in einer Besprechung erhalten die Benachrichtigungen, die über die `NotificationSignal` API gesendet werden.

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
> * Der `completionBotId` Parameter des `externalResourceUrl` Parameters ist im angeforderten Nutzlastbeispiel optional. `Bot ID` wird im Manifest deklariert, und der Bot erhält ein Ergebnisobjekt.
> * Die `externalResourceUrl` Parameter für Breite und Höhe müssen in Pixeln angegeben werden. Um sicherzustellen, dass die Abmessungen den zulässigen Grenzwerten entsprechen, lesen Sie die [Entwurfsrichtlinien](design/designing-apps-in-meetings.md).
> * Die URL ist die Seite, die als `<iframe>` in das Dialogfeld in der Besprechung geladen wird. Die Domäne muss sich im Array der App `validDomains` in Ihrem App-Manifest befinden.

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

> [!NOTE] 
> Überprüfen Sie, ob Ihre App alle unter ["Voraussetzungen für Apps" in Teams Besprechungen aufgeführten](~/apps-in-teams-meetings/create-apps-for-teams-meetings.md) Voraussetzungen erfüllt.

Um die Besprechungsdetails-API zu verwenden, müssen Sie RSC-Berechtigungen abrufen. Verwenden Sie das folgende Beispiel, um die Eigenschaft Ihres App-Manifests `webApplicationInfo` zu konfigurieren:

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

## <a name="cart-api"></a>CART-API

Die KOMMUNIKATIONSZUGRIFF-CART-API (Real-Time Translation) stellt einen POST-Endpunkt für Microsoft Teams CART-Untertitel, vom Menschen eingegebene Untertitel, bereit. Textinhalte, die an diesen Endpunkt gesendet werden, werden Endbenutzern in einer Microsoft Teams Besprechung angezeigt, wenn beschriftungen aktiviert sind.

### <a name="cart-url"></a>EINKAUFSWAGEN-URL

Sie können die CART-URL für den POST-Endpunkt auf der Seite **"Besprechungsoptionen**" in einer Microsoft Teams Besprechung abrufen. Weitere Informationen finden Sie unter [CART-Beschriftungen in einer Microsoft Teams Besprechung](https://support.microsoft.com/office/use-cart-captions-in-a-microsoft-teams-meeting-human-generated-captions-2dd889e8-32a8-4582-98b8-6c96cf14eb47). Sie müssen die CART-URL nicht ändern, um CART-Beschriftungen zu verwenden.

#### <a name="query-parameter"></a>Abfrageparameter

Die CART-URL enthält die folgenden Abfrageparameter:

|Wert|Typ|Erforderlich|Beschreibung|
|---|---|----|----|
|**meetingId**| Zeichenfolge | Ja |Der Besprechungsbezeichner ist über Bot Invoke und Teams Client SDK verfügbar. <br/>Beispiel: meetingid=%7b%22tId%22%3a%2272f234bf-86f1-41af-91ab-2d7cd0321b47%22%2c%22oId%22%3a%22e071f268-4241-47f8-8cf3-fc6b84437f23%22%2c%22thId%22%3a%2219%3ameeting_NzJiMjNkMGQtYzk3NS00ZDI1LWJjN2QtMDgyODVhZmI3NzJj%40thread.v2%22%2c%22mId%22%3a%220%22%7d|
|**Token**| Zeichenfolge | Ja |Autorisierungstoken.<br/> Beispiel: token=04751eac |

#### <a name="example"></a>Beispiel

```http
https://api.captions.office.microsoft.com/cartcaption?meetingid=%7b%22tId%22%3a%2272f234bf-86f1-41af-91ab-2d7cd0321b47%22%2c%22oId%22%3a%22e071f268-4241-47f8-8cf3-fc6b84437f23%22%2c%22thId%22%3a%2219%3ameeting_NzJiMjNkMGQtYzk3NS00ZDI1LWJjN2QtMDgyODVhZmI3NzJj%40thread.v2%22%2c%22mId%22%3a%220%22%7d&token=gjs44ra
```

### <a name="method"></a>Methode

|Ressource|Methode|Beschreibung|
|----|----|----|
|/cartcaption|POST|Behandeln von Beschriftungen für eine Besprechung, die gestartet wurde|

> [!NOTE]
> Stellen Sie sicher, dass der Inhaltstyp für alle Anforderungen Nur-Text mit UTF-8-Codierung ist. Der Anforderungstext enthält nur Beschriftungen.

#### <a name="example"></a>Beispiel

```http
POST /cartcaption?meetingid=04751eac-30e6-47d9-9c3f-0b4ebe8e30d9&token=04751eac&lang=en-us HTTP/1.1
Host: api.captions.office.microsoft.com
Content-Type: text/plain
Content-Length: 22
Hello I’m Cortana, welcome to my meeting. 
```

> [!Note]  
> Jede POST-Anforderung generiert eine neue Beschriftungszeile. Um sicherzustellen, dass der Endbenutzer genügend Zeit zum Lesen des Inhalts hat, beschränken Sie jeden POST-Anforderungstext auf 80 bis 120 Zeichen.

### <a name="error-codes"></a>Fehlercodes

Die CART-API enthält die folgenden Fehlercodes:

|Fehlercode|Beschreibung|
|---|---|
| **400** | Ungültige Anforderung. Der Antworttext enthält weitere Informationen. Beispielsweise werden nicht alle erforderlichen Parameter angezeigt.|
| **401** | Unbefugte. Ungültiges oder abgelaufenes Token. Wenn dieser Fehler angezeigt wird, generieren Sie eine neue EINKAUFSWAGEN-URL in Teams. |
| **404** | Besprechung nicht gefunden oder nicht gestartet. Wenn dieser Fehler angezeigt wird, stellen Sie sicher, dass Sie die Besprechung starten und Die Überschriften starten auswählen. Nachdem Beschriftungen in der Besprechung aktiviert wurden, können Sie mit dem Posting von Beschriftungen in der Besprechung beginnen.|
| **500** |Internal server error. (Interner Serverfehler) Wenden [Sie sich an den Support, oder geben Sie Feedback, um weitere Informationen zu erhalten](../feedback.md).|

## <a name="real-time-teams-meeting-events"></a>Besprechungsereignisse in Echtzeit Teams

Der Benutzer kann Besprechungsereignisse in Echtzeit empfangen. Sobald eine App einer Besprechung zugeordnet ist, werden die tatsächliche Start- und Endzeit der Besprechung für den Bot freigegeben.

Die tatsächliche Start- und Endzeit einer Besprechung unterscheidet sich von der geplanten Start- und Endzeit. Die Besprechungsdetails-API stellt die geplante Start- und Endzeit bereit. Das Ereignis gibt die tatsächliche Start- und Endzeit an.

### <a name="prerequisite"></a>Voraussetzungen

> [!NOTE] 
> Überprüfen Sie, ob Ihre App alle unter ["Voraussetzungen für Apps in Teams Besprechungen" aufgeführten](~/apps-in-teams-meetings/create-apps-for-teams-meetings.md) Voraussetzungen erfüllt.

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
> * Abrufen der Besprechungs-ID von `turnContext.ChannelData`.    
> * Verwenden Sie die Unterhaltungs-ID nicht als Besprechungs-ID.     
> * Verwenden Sie keine Besprechungs-ID aus der Nutzlast `turncontext.activity.value`für Besprechungsereignisse. 
      
Der folgende Code zeigt, wie die Metadaten einer Besprechung erfasst werden, die , , , `JoinUrl`und aus einem Besprechungsstart-/-end-Ereignis besteht`MeetingType``Title`:`EndTime` `StartTime``Id`

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
| Erweiterbarkeit von Besprechungen | Microsoft Teams Beispiel für die Erweiterbarkeit von Besprechungen zum Übergeben von Token. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-token-app/csharp) | [Anzeigen](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-token-app/nodejs) |
| Besprechungsinhalts-Blasen-Bot | Microsoft Teams Besprechungserweiterungsbeispiel für die Interaktion mit einem Inhaltsblasen-Bot in einer Besprechung. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-content-bubble/csharp) |  [Anzeigen](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-content-bubble/nodejs)|
| Meeting MeetingSidePanel | Microsoft Teams Besprechungserweiterungsbeispiel für die Interaktion mit dem Seitenbereich in besprechungsinternen Besprechungen. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-sidepanel/csharp) | [Anzeigen](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-sidepanel/nodejs)|
| Registerkarte "Details" in der Besprechung | Microsoft Teams Besprechungserweiterungsbeispiel für die Interaktion mit der Registerkarte "Details" in der Besprechung. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-details-tab/csharp) | [Anzeigen](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-details-tab/nodejs)|
|Beispiel für Besprechungsereignisse|Beispiel-App zum Anzeigen von Teams Besprechungsereignissen in Echtzeit|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-events/csharp)|[Anzeigen](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-events/nodejs)|
|Beispiel für die Besprechungsrekrutierung|Beispiel-App zum Anzeigen der Besprechungserfahrung für das Einstellungsszenario.|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meeting-recruitment-app/csharp)|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meeting-recruitment-app/nodejs)|
|App-Installation mit QR-Code|Beispiel-App, die den QR-Code generiert und die App mit dem QR-Code installiert|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-installation-using-qr-code/csharp)|[Anzeigen](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-installation-using-qr-code/nodejs)|


## <a name="see-also"></a>Siehe auch

* [Teams Authentifizierungsfluss für Registerkarten](../tabs/how-to/authentication/auth-flow-tab.md)
* [Apps für Teams-Besprechungen](teams-apps-in-meetings.md)

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Aktivieren und Konfigurieren Ihrer Apps für Teams Besprechungen](enable-and-configure-your-app-for-teams-meetings.md)
