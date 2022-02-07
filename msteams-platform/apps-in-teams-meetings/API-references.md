---
title: API-Referenzen für Besprechungs-Apps
author: surbhigupta
description: Identifizieren der API-Referenzen für Besprechungs-Apps mit Beispielen und Codebeispielen
ms.topic: conceptual
ms.author: lajanuar
ms.localizationpriority: medium
keywords: Teams-Apps– Benutzerteilnehmer-Rollen-API für Benutzerkontextbenachrichtigung – Signalabfrage
---

# <a name="meeting-apps-api-references"></a>API-Referenzen für Besprechungs-Apps

Die Besprechungserweiterung bietet APIs, um die Besprechungserfahrung zu verbessern. Mithilfe der aufgeführten APIs können Sie Folgendes ausführen:

* Erstellen von Apps oder Integrieren vorhandener Apps innerhalb des Besprechungslebenszyklus.
* Verwenden Sie APIs, um Ihre App auf Besprechungen aufmerksam zu machen.
* Wählen Sie erforderliche APIs aus, um die Besprechungserfahrung zu verbessern.

Die folgende Tabelle enthält eine Liste der APIs, die in den SDKs Microsoft Teams Client (MSTC) und Microsoft Bot Framework (MSBF) verfügbar sind:

|Methode| Beschreibung| Quelle|
|---|---|----|
|[**Abrufen des Benutzerkontexts**](#get-user-context-api)| Rufen Sie Kontextinformationen ab, um relevante Inhalte auf einer Teams Registerkarte anzuzeigen.| MSTC SDK|
|[**Teilnehmer abrufen**](#get-participant-api)| Abrufen von Teilnehmerinformationen nach Besprechungs-ID und Teilnehmer-ID. |MSBF SDK|
|[**Benachrichtigungssignal senden**](#send-notification-signal-api)| Bereitstellen von Besprechungssignalen mithilfe der vorhandenen Unterhaltungsbenachrichtigungs-API für den Benutzer-Bot-Chat und Benachrichtigen von Benutzeraktionen, die ein Dialogfeld in einer Besprechung anzeigen. |MSBF SDK|
|[**Besprechungsdetails abrufen**](#get-meeting-details-api)| Abrufen der statischen Metadaten einer Besprechung. |MSBF SDK |
|[**Senden von Untertiteln in Echtzeit**](#send-real-time-captions-api)| Senden von Untertiteln in Echtzeit an eine laufende Besprechung. |MSTC SDK|
|[**Freigeben von App-Inhalten für die Phase**](#share-app-content-to-stage-api)| Geben Sie bestimmte Teile der App über den App-Seitenbereich in einer Besprechung für die Besprechungsphase frei. |MSTC SDK|
|[**Abrufen des Freigabestatus der App-Inhaltsphasen**](#get-app-content-stage-sharing-state-api)| Abrufen von Informationen zum Freigabestatus der App in der Besprechungsphase. |MSTC SDK|
|[**Abrufen von Funktionen für die Freigabe von App-Inhalten**](#get-app-content-stage-sharing-capabilities-api)| Rufen Sie die Funktionen der App für die Freigabe in der Besprechungsphase ab. |MSTC SDK|
|[**Abrufen von Echtzeit-Teams Besprechungsereignissen**](#get-real-time-teams-meeting-events-api)|Abrufen von Echtzeitbesprechungsereignissen, z. B. der tatsächlichen Start- und Endzeit.| MSBF SDK|

## <a name="get-user-context-api"></a>Abrufen der Benutzerkontext-API

Informationen zum Identifizieren und Abrufen von Kontextinformationen für Ihre Registerkarteninhalte finden Sie unter [Abrufen des Kontexts für Ihre Teams Registerkarte](../tabs/how-to/access-teams-context.md#get-context-by-using-the-microsoft-teams-javascript-library). `meetingId` Wird von einer Registerkarte verwendet, die im Besprechungskontext ausgeführt wird, und wird für die Antwortnutzlast hinzugefügt.

## <a name="get-participant-api"></a>Teilnehmer-API abrufen

> [!NOTE]
> * Teilnehmerrollen nicht zwischenspeichern, da der Besprechungsorganisator die Rollen jederzeit ändern kann.
> * Derzeit wird die `GetParticipant` API nur für Verteilerlisten oder Listen mit weniger als 350 Teilnehmern unterstützt.

### <a name="query-parameters"></a>Abfrageparameter

> [!TIP]
> Rufen Sie Teilnehmer-IDs und Mandanten-IDs aus dem Registerkarten-SSO ab.

Die folgende Tabelle enthält die Abfrageparameter:

|Wert|Typ|Erforderlich|Beschreibung|
|---|---|----|---|
|**meetingId**| Zeichenfolge | Ja | Der Besprechungsbezeichner ist über Bot Invoke und Teams Client SDK verfügbar.|
|**participantId**| String | Ja | Die Teilnehmer-ID ist die Benutzer-ID. Es ist in Tab SSO, Bot Invoke und Teams Client SDK verfügbar. Es wird empfohlen, eine Teilnehmer-ID vom Tab-SSO abzurufen. |
|**tenantId**| String | Ja | Die Mandanten-ID ist für die Mandantenbenutzer erforderlich. Es ist in Tab SSO, Bot Invoke und Teams Client SDK verfügbar. Es wird empfohlen, eine Mandanten-ID vom Tab-SSO abzurufen. |

### <a name="example"></a>Beispiel

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

Die folgende Tabelle enthält die Antwortcodes:

|Antwortcode|Beschreibung|
|---|---|
| **403** | Das Abrufen von Teilnehmerinformationen wird nicht für die App freigegeben. Wenn die App nicht in der Besprechung installiert ist, wird die Fehlerantwort 403 ausgelöst. Wenn der Mandantenadministrator die App während der Migration einer Livewebsite deaktiviert oder blockiert, wird die Fehlerantwort 403 ausgelöst. |
| **200** | Die Teilnehmerinformationen werden erfolgreich abgerufen.|
| **401** | Die App antwortet mit einem ungültigen Token.|
| **404** | Die Besprechung ist entweder abgelaufen, oder die Teilnehmer sind nicht verfügbar.|

## <a name="send-notification-signal-api"></a>Api zum Senden von Benachrichtigungssignalen

Alle Benutzer in einer Besprechung erhalten die Benachrichtigungen, die über die `NotificationSignal` API gesendet werden. `NotificationSignal` Mithilfe der API können Sie Besprechungssignale bereitstellen, die mithilfe der vorhandenen Unterhaltungsbenachrichtigungs-API für den Benutzer-Bot-Chat übermittelt werden. Sie können ein Signal basierend auf einer Benutzeraktion senden, einem Dialogfeld in der Besprechung. Die API enthält Abfrageparameter, Beispiele und Antwortcodes.

> [!NOTE]
> * Wenn ein Dialogfeld in einer Besprechung aufgerufen wird, wird der Inhalt als Chatnachricht angezeigt.
> * Derzeit wird das Senden von gezielten Benachrichtigungen nicht unterstützt.

### <a name="query-parameter"></a>Abfrageparameter

Die folgende Tabelle enthält die Abfrageparameter:

|Wert|Typ|Erforderlich|Beschreibung|
|---|---|----|---|
|**conversationId**| Zeichenfolge | Ja | Der Unterhaltungsbezeichner ist als Teil des Bot-Aufrufs verfügbar. |

### <a name="examples"></a>Beispiele

Der `Bot ID` wird im Manifest deklariert, und der Bot erhält ein Ergebnisobjekt.

> [!NOTE]
> * Der `completionBotId` Parameter des `externalResourceUrl` Parameters ist im angeforderten Nutzlastbeispiel optional.
> * Die `externalResourceUrl` Parameter für Breite und Höhe müssen in Pixeln angegeben werden. Weitere Informationen finden Sie in den [Entwurfsrichtlinien](design/designing-apps-in-meetings.md).
> * Die URL ist die Seite, die wie `<iframe>` im Besprechungsdialogfeld geladen wird. Die Domäne muss sich im Array der Apps `validDomains` in Ihrem App-Manifest befinden.

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

Die folgende Tabelle enthält die Antwortcodes:

|Antwortcode|Beschreibung|
|---|---|
| **201** | Die Aktivität mit Signal wird erfolgreich gesendet. |
| **401** | Die App antwortet mit einem ungültigen Token. |
| **403** | Die App kann das Signal nicht senden. Der Antwortcode 403 kann aus verschiedenen Gründen auftreten, z. B. wenn der Mandantenadministrator die App während der Migration der Livewebsite deaktiviert und blockiert. In diesem Fall enthält die Nutzlast eine detaillierte Fehlermeldung. |
| **404** | Der Besprechungschat ist nicht vorhanden. |

## <a name="get-meeting-details-api"></a>Api zum Abrufen von Besprechungsdetails

> [!NOTE]
> Derzeit ist das Feature nur in der [öffentlichen Entwicklervorschau](../resources/dev-preview/developer-preview-intro.md) verfügbar.

Mit der Besprechungsdetails-API kann Ihre App die statischen Metadaten einer Besprechung abrufen. Die Metadaten stellen Datenpunkte bereit, die sich nicht dynamisch ändern. Die API ist über Bot Services verfügbar. Derzeit unterstützen sowohl private geplante oder wiederkehrende Besprechungen als auch geplante oder wiederkehrende Kanalbesprechungen die API mit unterschiedlichen RSC-Berechtigungen.

### <a name="prerequisite"></a>Voraussetzungen

Um die Besprechungsdetails-API zu verwenden, müssen Sie unterschiedliche RSC-Berechtigungen basierend auf dem Umfang einer Besprechung abrufen, z. B. private Besprechungen oder Kanalbesprechung.

<br>

<details>

<summary><b>Für App-Manifestversion 1.12</b></summary>

Verwenden Sie das folgende Beispiel, um die Eigenschaften Ihres App-Manifests `webApplicationInfo`  für `authorization` jede private Besprechung zu konfigurieren:

```json
"webApplicationInfo": {
    "id": "<bot id>",
    "resource": "https://RscPermission",
},
"authorization": {
    "permissions": {
        "resourceSpecific": [
            {
                "name": "OnlineMeeting.ReadBasic.Chat",
                "type": "Application"
            }
        ]
    }
}
 ```

Verwenden Sie das folgende Beispiel, um die Eigenschaften Ihres App-Manifests `webApplicationInfo` für `authorization` jede Kanalbesprechung zu konfigurieren:

```json
"webApplicationInfo": {
    "id": "<bot id>",
    "resource": "https://RscPermission",
},
"authorization": {
    "permissions": {
        "resourceSpecific": [
            {
                "name": "ChannelMeeting.ReadBasic.Group",
                "type": "Application"
            }
        ]
    }
}
 ```

<br>

</details>

<br>

<details>

<summary><b>Für App-Manifestversion 1.11 oder frühere Versionen</b></summary>

Verwenden Sie das folgende Beispiel, um die Eigenschaft Ihres App-Manifests `webApplicationInfo` für jede private Besprechung zu konfigurieren:

```json
"webApplicationInfo": {
    "id": "<bot id>",
    "resource": "https://RscPermission",
    "applicationPermissions": [
      "OnlineMeeting.ReadBasic.Chat"
    ]
}
 ```

Verwenden Sie das folgende Beispiel, um die Eigenschaft Ihres App-Manifests `webApplicationInfo` für jede Kanalbesprechung zu konfigurieren:

```json
"webApplicationInfo": {
    "id": "<bot id>",
    "resource": "https://RscPermission",
    "applicationPermissions": [
      "ChannelMeeting.ReadBasic.Group"
    ]
}
 ```

<br>

</details>

> [!NOTE]
> Der Bot kann Besprechungsstart- oder -endereignisse automatisch von allen Besprechungen empfangen, die in allen Kanälen erstellt wurden, indem er dem Manifest für die RSC-Berechtigung hinzugefügt `ChannelMeeting.ReadBasic.Group` wird.
 
### <a name="query-parameter"></a>Abfrageparameter

In der folgenden Tabelle ist der Abfrageparameter aufgeführt:

|Wert|Typ|Erforderlich|Beschreibung|
|---|---|----|---|
|**meetingId**| String | Ja | Der Besprechungsbezeichner ist über Bot Invoke und Teams Client SDK verfügbar. |

### <a name="example"></a>Beispiel

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
            "conversationType": "groupchat", 
            "id": "meeting chat ID" 
    }, 
    "organizer": { 
        "id": "<organizer user ID>", 
        "aadObjectId": "<AAD ID>", 
        "tenantId": "<Tenant ID>" 
    }
} 
```

## <a name="send-real-time-captions-api"></a>API zum Senden von Beschriftungen in Echtzeit

Die API zum Senden von Echtzeituntertiteln stellt einen POST-Endpunkt für Microsoft Teams Kommunikationszugriff auf Untertitel für Echtzeitübersetzungen (CART) und vom Menschen eingegebene Untertitel bereit. Textinhalte, die an diesen Endpunkt gesendet werden, werden Endbenutzern in einer Microsoft Teams Besprechung angezeigt, wenn beschriftungen aktiviert sind.

### <a name="cart-url"></a>EINKAUFSWAGEN-URL

Sie können die CART-URL für den POST-Endpunkt auf der Seite **"Besprechungsoptionen**" in einer Microsoft Teams Besprechung abrufen. Weitere Informationen finden Sie unter [CART-Beschriftungen in einer Microsoft Teams Besprechung](https://support.microsoft.com/office/use-cart-captions-in-a-microsoft-teams-meeting-human-generated-captions-2dd889e8-32a8-4582-98b8-6c96cf14eb47). Sie müssen die CART-URL nicht ändern, um CART-Beschriftungen zu verwenden.

#### <a name="query-parameter"></a>Abfrageparameter

Die CART-URL enthält die folgenden Abfrageparameter:

|Wert|Typ|Erforderlich|Beschreibung|
|---|---|----|----|
|**meetingId**| String | Ja |Der Besprechungsbezeichner ist über Bot Invoke und Teams Client SDK verfügbar. <br/>Beispiel: meetingid=%7b%22tId%22%3a%2272f234bf-86f1-41af-91ab-2d7cd0321b47%22%2c%22oId%22%3a%22e071f268-4241-47f8-8cf3-fc6b84437f23%22%2c%22thId%22%3a%2219%3ameeting_NzJiMjNkMGQtYzk3NS00ZDI1LWJjN2QtMDgyODVhZmI3NzJj%40thread.v2%22%2c%22mId%22%3a%220%22%7d|
|**Token**| String | Ja |Autorisierungstoken.<br/> Beispiel: token=04751eac |

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

Die folgende Tabelle enthält die Fehlercodes:

|Fehlercode|Beschreibung|
|---|---|
| **400** | Ungültige Anforderung. Der Antworttext enthält weitere Informationen. Beispielsweise werden nicht alle erforderlichen Parameter angezeigt.|
| **401** | Unbefugte. Ungültiges oder abgelaufenes Token. Wenn dieser Fehler angezeigt wird, generieren Sie eine neue EINKAUFSWAGEN-URL in Teams. |
| **404** | Besprechung nicht gefunden oder nicht gestartet. Wenn dieser Fehler angezeigt wird, stellen Sie sicher, dass Sie die Besprechung starten und Die Überschriften starten auswählen. Nachdem Beschriftungen in der Besprechung aktiviert wurden, können Sie mit dem Posting von Beschriftungen in der Besprechung beginnen.|
| **500** |Internal server error. (Interner Serverfehler) Wenden [Sie sich an den Support, oder geben Sie Feedback, um weitere Informationen zu erhalten](../feedback.md).|

## <a name="share-app-content-to-stage-api"></a>Freigeben von App-Inhalten für die Phasen-API

Mit `shareAppContentToStage` der API können Sie bestimmte Teile Ihrer App für die Besprechungsphase freigeben. Die API ist über das Teams-Client-SDK verfügbar.

### <a name="prerequisite"></a>Voraussetzungen

Um die `shareAppContentToStage` API zu verwenden, müssen Sie die RSC-Berechtigungen abrufen. Konfigurieren Sie im App-Manifest die `authorization` Eigenschaft und das `name` Und `type` im `resourceSpecific` Feld. Beispiel:

```json
"authorization": {
    "permission": { 
    "resourceSpecific": [
      { 
      "name": "MeetingStage.Write.Chat",
      "type": "Delegated"
      }
    ]
   }
}
 ```

### <a name="query-parameter"></a>Abfrageparameter

Die folgende Tabelle enthält die Abfrageparameter:

|Wert|Typ|Erforderlich|Beschreibung|
|---|---|----|---|
|**callback**| String | Ja | Rückruf enthält zwei Parameter, Fehler und Ergebnis. Der *Fehler* kann entweder einen Fehler vom Typ *SdkError* oder null enthalten, wenn die Freigabe erfolgreich ist. Das *Ergebnis* kann im Falle einer erfolgreichen Freigabe entweder einen true-Wert enthalten oder null, wenn die Freigabe fehlschlägt.|
|**appContentURL**| String | Ja | Die URL, die für die Phase freigegeben wird.|

### <a name="example"></a>Beispiel

```javascript
const appContentUrl = "https://www.bing.com/";

microsoftTeams.meeting.shareAppContentToStage((err, result) => {
    if (result) {
        // handle success
    }
    if (err) {
        // handle error
    }
}, appContentUrl);
```

### <a name="response-codes"></a>Antwortcodes

Die folgende Tabelle enthält die Antwortcodes:

|Antwortcode|Beschreibung|
|---|---|
| **500** | Interner Fehler. |
| **501** | Die API wird im aktuellen Kontext nicht unterstützt.|
| **1000** | Die App verfügt nicht über die richtigen Berechtigungen, um die Freigabe in der Phase zuzulassen.|

## <a name="get-app-content-stage-sharing-state-api"></a>Abrufen der Status-API für die Freigabe von App-Inhalten

Mit `getAppContentStageSharingState` der API können Sie Informationen zur Freigabe von Apps in der Besprechungsphase abrufen.

### <a name="query-parameter"></a>Abfrageparameter

Die folgende Tabelle enthält die Abfrageparameter:

|Wert|Typ|Erforderlich|Beschreibung|
|---|---|----|---|
|**callback**| String | Ja | Rückruf enthält zwei Parameter, Fehler und Ergebnis. Der *Fehler* kann entweder einen Fehler vom Typ *SdkError* enthalten, falls ein Fehler auftritt, oder null, wenn die Freigabe erfolgreich ist. Das *Ergebnis* kann entweder ein `AppContentStageSharingState` Objekt enthalten, das einen erfolgreichen Abruf angibt, oder null, was auf einen fehlgeschlagenen Abruf hinweist.|

### <a name="example"></a>Beispiel

```javascript
microsoftTeams.meeting.getAppContentStageSharingState((err, result) => {
    if (result.isAppSharing) {
        // Indicates app has permission to share contents to meeting stage.
    }
});
``` 

Der JSON-Antworttext für die `getAppContentStageSharingState` API lautet:

```json
{
   "isAppSharing":true
} 
```

### <a name="response-codes"></a>Antwortcodes

Die folgende Tabelle enthält die Antwortcodes:

|Antwortcode|Beschreibung|
|---|---|
| **500** | Interner Fehler. |
| **501** | Die API wird im aktuellen Kontext nicht unterstützt.|
| **1000** | Die App verfügt nicht über die richtigen Berechtigungen, um die Freigabe in der Phase zuzulassen.|

## <a name="get-app-content-stage-sharing-capabilities-api"></a>Api zum Abrufen von Funktionen für die Freigabe von App-Inhalten

Mit `getAppContentStageSharingCapabilities` der API können Sie die Funktionen der App für die Freigabe in die Besprechungsphase abrufen.

### <a name="query-parameter"></a>Abfrageparameter

Die folgende Tabelle enthält die Abfrageparameter:

|Wert|Typ|Erforderlich|Beschreibung|
|---|---|----|---|
|**callback**| String | Ja | Rückruf enthält zwei Parameter, Fehler und Ergebnis. Der *Fehler* kann entweder einen Fehler vom Typ *SdkError* oder null enthalten, wenn die Freigabe erfolgreich ist. Das Ergebnis kann entweder ein `AppContentStageSharingState` Objekt enthalten, das einen erfolgreichen Abruf angibt, oder null, was auf einen fehlgeschlagenen Abruf hinweist.|

### <a name="example"></a>Beispiel

```javascript
microsoftTeams.meeting.getAppContentStageSharingCapabilities((err, result) => {
    if (result.doesAppHaveSharePermission) {
        // Indicates app has permission to share contents to meeting stage.
    }
});
``` 

Der JSON-Antworttext für `getAppContentStageSharingCapabilities` die API lautet:

```json
{
   "doesAppHaveSharePermission":true
} 
```

### <a name="response-codes"></a>Antwortcodes

Die folgende Tabelle enthält die Antwortcodes:

|Antwortcode|Beschreibung|
|---|---|
| **500** | Interner Fehler. |
| **1000** | Die App verfügt nicht über die Berechtigungen zum Bereitstellen der Freigabe.|

## <a name="get-real-time-teams-meeting-events-api"></a>Abrufen Teams Besprechungsereignis-API in Echtzeit

Der Benutzer kann Besprechungsereignisse in Echtzeit empfangen. Sobald eine App einer Besprechung zugeordnet ist, werden die tatsächliche Start- und Endzeit der Besprechung für den Bot freigegeben. Die tatsächliche Start- und Endzeit einer Besprechung unterscheidet sich von der geplanten Start- und Endzeit. Die Besprechungsdetails-API stellt die geplante Start- und Endzeit bereit. Das Ereignis gibt die tatsächliche Start- und Endzeit an.

### <a name="prerequisite"></a>Voraussetzungen

Ihr App-Manifest muss über die `webApplicationInfo` Eigenschaft verfügen, um die Besprechungsstart- und -endereignisse zu empfangen. Verwenden Sie die folgenden Beispiele, um Ihr Manifest zu konfigurieren:

<br>

<details>

<summary><b>Für App-Manifestversion 1.12</b></summary>

```json
"webApplicationInfo": {
    "id": "<bot id>",
    "resource": "https://RscPermission",
    },
"authorization": {
    "permissions": {
        "resourceSpecific": [
            {
                "name": "OnlineMeeting.ReadBasic.Chat",
                "type": "Application"
            }
        ]    
    }
}
 ```

<br>

</details>

<br>

<details>

<summary><b>Für App-Manifestversion 1.11 oder frühere Versionen</b></summary>

```json
"webApplicationInfo": {
    "id": "<bot id>",
    "resource": "https://RscPermission",
    "applicationPermissions": [
      "OnlineMeeting.ReadBasic.Chat"
    ]
}
 ```

<br>

</details>

### <a name="example-of-getting-meetingstartendeventvalue"></a>Beispiel für das Abrufen `MeetingStartEndEventvalue`

Der Bot empfängt das Ereignis über den `OnEventActivityAsync` Handler. Um die JSON-Nutzlast zu deserialisieren, wird ein Modellobjekt eingeführt, um die Metadaten einer Besprechung abzurufen. Die Metadaten einer Besprechung befinden sich in der `value` Eigenschaft in der Ereignisnutzlast. Das `MeetingStartEndEventvalue` Modellobjekt wird erstellt, dessen Membervariablen den Schlüsseln unter der `value` Eigenschaft in der Ereignisnutzlast entsprechen.

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

## <a name="code-sample"></a>Codebeispiel

|Beispielname | Beschreibung | C# | Node.js |
|----------------|-----------------|--------------|--------------|
| Erweiterbarkeit von Besprechungen | Microsoft Teams Beispiel für die Erweiterbarkeit von Besprechungen zum Übergeben von Token. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-token-app/csharp) | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-token-app/nodejs) |
| Besprechungsinhalts-Blasen-Bot | Microsoft Teams Besprechungserweiterungsbeispiel für die Interaktion mit einem Inhaltsblasen-Bot in einer Besprechung. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-content-bubble/csharp) |  [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-content-bubble/nodejs)|
| Meeting MeetingSidePanel | Microsoft Teams Besprechungserweiterungsbeispiel für die Interaktion mit dem Seitenbereich in einer Besprechung. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-sidepanel/csharp) | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-sidepanel/nodejs)|
| Registerkarte "Details" in der Besprechung | Microsoft Teams Besprechungserweiterungsbeispiel für die Interaktion mit der Registerkarte "Details" in der Besprechung. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-details-tab/csharp) | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-details-tab/nodejs)|
|Beispiel für Besprechungsereignisse|Beispiel-App zum Anzeigen von Teams Besprechungsereignissen in Echtzeit|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-events/csharp)|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-events/nodejs)|
|Beispiel für die Besprechungsrekrutierung|Beispiel-App zum Anzeigen der Besprechungserfahrung für das Einstellungsszenario.|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meeting-recruitment-app/csharp)|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meeting-recruitment-app/nodejs)|
|App-Installation mit QR-Code|Beispiel-App, die den QR-Code generiert und die App mit dem QR-Code installiert|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-installation-using-qr-code/csharp)|[Anzeigen](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-installation-using-qr-code/nodejs)|

## <a name="see-also"></a>Siehe auch

* [Teams Authentifizierungsfluss für Registerkarten](../tabs/how-to/authentication/auth-flow-tab.md)
* [Apps für Teams-Besprechungen](teams-apps-in-meetings.md)

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Aktivieren und Konfigurieren Ihrer Apps für Teams Besprechungen](enable-and-configure-your-app-for-teams-meetings.md)
