---
title: API-Referenzen für Besprechungs-Apps
author: surbhigupta
description: Identifizieren Sie die API-Verweise auf Besprechungs-Apps anhand von Beispielen und Codebeispielen, Teams Apps-Besprechungs-Benutzerteilnehmer-Rollen-API- Benutzerkontextbenachrichtigungs-Signalabfrage.
ms.topic: conceptual
ms.author: lajanuar
ms.localizationpriority: medium
ms.openlocfilehash: cb28e893a9c0460290294893800f77c90829edda
ms.sourcegitcommit: eeaa8cbb10b9dfa97e9c8e169e9940ddfe683a7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/27/2022
ms.locfileid: "65756583"
---
# <a name="meeting-apps-api-references"></a>API-Referenzen für Besprechungs-Apps

Die Meeting-Erweiterbarkeit bietet APIs zur Verbesserung des Meeting-Erlebnisses. Mit Hilfe der aufgeführten APIs können Sie Folgendes ausführen:

* Erstellen Sie Apps oder integrieren Sie vorhandene Apps in den Meeting-Lebenszyklus.
* Verwenden Sie APIs, um Ihre App auf Meetings aufmerksam zu machen.
* Wählen Sie die erforderlichen APIs aus, um das Besprechungserlebnis zu verbessern.

> [!NOTE]
> Verwenden Sie Teams [JavaScript SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) (*Version*: 1.10 und höher) für SSO, um im Meeting-Seitenbereich zu arbeiten.

Die folgende Tabelle enthält eine Liste der APIs, die in den Microsoft Teams Client (MSTC)- und Microsoft Bot Framework (MSBF)-SDKs verfügbar sind:

|Methode| Beschreibung| Quelle|
|---|---|----|
|[**Benutzerkontext abrufen**](#get-user-context-api)| Rufen Sie kontextbezogene Informationen ab, um relevante Inhalte auf einer Registerkarte „Teams“ anzuzeigen.| [MSTC SDK](/microsoftteams/platform/tabs/how-to/access-teams-context#get-context-by-using-the-microsoft-teams-javascript-library) |
|[**Teilnehmer abrufen**](#get-participant-api)| Rufen Sie Teilnehmerinformationen nach Meeting-ID und Teilnehmer-ID ab. | [MSBF SDK](/dotnet/api/microsoft.bot.builder.teams.teamsinfo.getmeetingparticipantasync?view=botbuilder-dotnet-stable&preserve-view=true)
|[**Senden Sie eine Besprechungsbenachrichtigung**](#send-an-in-meeting-notification)| Stellen Sie Meeting-Signale mithilfe der vorhandenen Konversationsbenachrichtigungs-API für den Benutzer-Bot-Chat bereit und ermöglichen Sie die Benachrichtigung von Benutzeraktionen, die eine Benachrichtigung im Meeting anzeigen. | [MSBF SDK](/dotnet/api/microsoft.bot.builder.teams.teamsactivityextensions.teamsnotifyuser?view=botbuilder-dotnet-stable&preserve-view=true) |
|[**Besprechungsdetails abrufen**](#get-meeting-details-api)| Rufen Sie die statischen Metadaten eines Meetings ab. | [MSBF SDK](/dotnet/api/microsoft.bot.builder.teams.teamsinfo.getmeetinginfoasync?view=botbuilder-dotnet-stable&preserve-view=true) |
|[**Senden Sie Untertitel in Echtzeit**](#send-real-time-captions-api)| Senden Sie Untertitel in Echtzeit an ein laufendes Meeting. | [MSTC SDK](/azure/cognitive-services/speech-service/speech-sdk?tabs=nodejs%2Cubuntu%2Cios-xcode%2Cmac-xcode%2Candroid-studio#get-the-speech-sdk&preserve-view=true) |
|[**Teilen Sie App-Inhalte auf der Bühne**](#share-app-content-to-stage-api)| Teilen Sie bestimmte Teile der App für die Meeting-Phase aus dem Seitenbereich der App in einem Meeting. | [MSTC SDK](/javascript/api/@microsoft/teams-js/microsoftteams.meeting?view=msteams-client-js-latest&preserve-view=true) |
|[**Rufen Sie den Freigabestatus für App-Inhalte ab**](#get-app-content-stage-sharing-state-api)| Rufen Sie Informationen über den Freigabestatus der App in der Besprechungsphase ab. | [MSTC SDK](/javascript/api/@microsoft/teams-js/microsoftteams.meeting.iappcontentstagesharingstate?view=msteams-client-js-latest&preserve-view=true) |
|[**Holen Sie sich Funktionen zum Teilen von App-Inhalten**](#get-app-content-stage-sharing-capabilities-api)| Rufen Sie die Funktionen der App zum Teilen in der Besprechungsphase ab. | [MSTC SDK](/javascript/api/@microsoft/teams-js/microsoftteams.meeting.iappcontentstagesharingcapabilities?view=msteams-client-js-latest&preserve-view=true) |
|[**Holen Sie sich Team-Meeting-Events in Echtzeit**](#get-real-time-teams-meeting-events-api)|Rufen Sie Meeting-Ereignisse in Echtzeit ab, z. B. die tatsächliche Start- und Endzeit.| [MSBF SDK](/dotnet/api/microsoft.bot.builder.teams.teamsactivityhandler.onteamsmeetingstartasync?view=botbuilder-dotnet-stable&preserve-view=true) |

## <a name="get-user-context-api"></a>Holen Sie sich die Benutzerkontext-API

Informationen zum Identifizieren und Abrufen von Kontextinformationen für Ihre Registerkarteninhalte finden Sie un[ter Abrufen von Kontext für Ihre Registerkarte "Teams"](../tabs/how-to/access-teams-context.md#get-context-by-using-the-microsoft-teams-javascript-library). wird von einer `meetingId` Registerkarte verwendet, die im Besprechungskontext ausgeführt wird, und wird für die Antwortnutzlast hinzugefügt.

## <a name="get-participant-api"></a>Teilnehmer-API abrufen

Die `GetParticipant` API muss über eine Bot-Registrierung und -ID verfügen, um Authentifizierungstoken zu generieren. Weitere Informationen finden Sie unter [Bot-Registrierung und -ID](../build-your-first-app/build-bot.md).

> [!NOTE]
>
> * Teilnehmerrollen nicht zwischenspeichern, da der Besprechungsorganisator die Rollen jederzeit ändern kann.
> * Derzeit wird die `GetParticipant` API nur für Verteilerlisten oder Dienstpläne mit weniger als 350 Teilnehmern unterstützt.

### <a name="query-parameters"></a>Abfrageparameter

> [!TIP]
> Rufen Sie Teilnehmer-IDs und Mandanten-IDs [auf der Registerkarte SSO-Authentifizierung ab](../tabs/how-to/authentication/auth-aad-sso.md).

Die `Meeting` API muss `meetingId`, `participantId` und als URL-Parameter `tenantId` haben. Die Parameter sind als Teil des Teams-Client-SDK und der bot-Aktivität verfügbar.

Die folgende Tabelle enthält die Abfrageparameter:

|Wert|Typ|Erforderlich|Beschreibung|
|---|---|----|---|
|**meetingId**| Zeichenfolge | Ja | Die Meeting-ID ist über Bot Invoke und Teams Client SDK verfügbar.|
|**participantId**| Zeichenfolge | Ja | Die Teilnehmer-ID ist die Benutzer-ID. Es ist in Tab SSO, Bot Invoke und Teams Client SDK verfügbar. Es wird empfohlen, eine Teilnehmer-ID vom Tab SSO zu erhalten. |
|**tenantId**| Zeichenfolge | Ja | Die Mandanten-ID ist für die Mandantenbenutzer erforderlich. Es ist in Tab SSO, Bot Invoke und Teams Client SDK verfügbar. Es wird empfohlen, eine Mandanten-ID von Tab SSO zu erhalten. |

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

---

| Eigenschaftenname | Zweck |
|---|---|
| **user.id** | ID des Benutzers. |
| **user.aadObjectId** | Azure Active Directory Objekt-ID des Benutzers. |
| **user.name** | Der Name des Benutzers. |
| **user.givenName** | Vorname des Benutzers.|
| **user.surname** | Nachname des Benutzers. |
| **user.email** | E-Mail-ID des Benutzers. |
| **user.userPrincipalName** | UPN des Benutzers. |
| **user.tenantId** | Azure Active Directory Mandanten-ID. |
| **user.userRole** | Rolle des Benutzers, z. B. "Administrator" oder "Benutzer". |
| **meeting.role** | Die Rolle des Teilnehmers in der Besprechung. z. B. "Organisator" oder "Referent" oder "Teilnehmer". |
| **meeting.inMeeting** | Der Wert, der angibt, ob sich der Teilnehmer an der Besprechung befindet. |
| **conversation.id** | Die Besprechungschat-ID. |
| **conversation.isGroup** | Boolescher Wert, der angibt, ob die Unterhaltung mehr als zwei Teilnehmer hat. |

### <a name="response-codes"></a>Antwortcodes

Die folgende Tabelle enthält die Antwortcodes:

|Antwortcode|Beschreibung|
|---|---|
| **403** | Get-Teilnehmerinformationen werden nicht mit der App geteilt. Wenn die App nicht im Meeting installiert ist, löst sie die Fehlerantwort 403 aus. Wenn der Mandantenadministrator die App während der Live-Site-Migration deaktiviert oder blockiert, wird die Fehlerantwort 403 ausgelöst. |
| **200** | Die Teilnehmerinformationen wurden erfolgreich abgerufen.|
| **401** | Die App antwortet mit einem ungültigen Token.|
| **404** | Die Besprechung ist entweder abgelaufen, oder die Teilnehmer sind nicht verfügbar.|

## <a name="send-an-in-meeting-notification"></a>Senden Sie eine Besprechungsbenachrichtigung

Alle Benutzer in einem Meeting erhalten die Benachrichtigungen, die über die Nutzlast für Benachrichtigungen im Meeting gesendet werden. Die Payload „In-Meeting-Benachrichtigung“ löst eine In-Meeting-Benachrichtigung aus und ermöglicht es Ihnen, Meeting-Signale bereitzustellen, die mithilfe der vorhandenen Konversationsbenachrichtigungs-API für Benutzer-Bot-Chat bereitgestellt werden. Sie können eine Meeting-Benachrichtigung basierend auf einer Benutzeraktion senden. Die Nutzlast ist über Bot Services verfügbar.

> [!NOTE]
>
> * Wenn eine Meeting-Benachrichtigung aufgerufen wird, wird der Inhalt als Chat-Nachricht präsentiert.
> * Derzeit werden das Senden gezielter Benachrichtigungen und die Unterstützung für Webapp nicht unterstützt.
> * Sie müssen die Funktion [submitTask()](../task-modules-and-cards/task-modules/task-modules-bots.md#submit-the-result-of-a-task-module) aufrufen, damit sie automatisch geschlossen wird, nachdem ein Benutzer eine Aktion in der Webansicht ausgeführt hat. Dies ist eine Voraussetzung für die App-Übermittlung. Weitere Informationen finden Sie unter [Teams SDK-Aufgabenmodul](/javascript/api/@microsoft/teams-js/microsoftteams.tasks?view=msteams-client-js-latest#submittask-string---object--string---string---&preserve-view=true).
> * Wenn Sie möchten, dass Ihre App anonyme Benutzer unterstützt, muss sich die Nutzlast der anfänglichen Aufrufanforderung auf `from.id` Anforderungsmetadaten im `from` Objekt und nicht auf `from.aadObjectId` Anforderungsmetadaten stützen. `from.id` ist die Benutzer-ID und `from.aadObjectId` die Microsoft Azure Active Directory (Azure AD)-ID des Benutzers. Weitere Informationen [finden Sie unter Aufgabenmodule in Registerkarten](../task-modules-and-cards/task-modules/task-modules-tabs.md) verwenden und Aufgabenmodul [erstellen und senden](../messaging-extensions/how-to/action-commands/create-task-module.md?tabs=dotnet#the-initial-invoke-request).

### <a name="query-parameter"></a>Abfrageparameter

Die folgende Tabelle enthält die Abfrageparameter:

|Wert|Typ|Erforderlich|Beschreibung|
|---|---|----|---|
|**conversationId**| Zeichenfolge | Ja | Die Konversations-ID ist als Teil von Bot Invoke verfügbar. |

### <a name="examples"></a>Beispiele

Der `Bot ID` wird im Manifest deklariert und der Bot erhält ein Ergebnisobjekt.

> [!NOTE]
>
> * Der `completionBotId` Parameter von `externalResourceUrl` ist im angeforderten Payload-Beispiel optional.
> * Die `externalResourceUrl` Breiten- und Höhenparameter müssen in Pixel angegeben werden. Weitere Informationen finden [Sie unter Designrichtlinien](design/designing-apps-in-meetings.md).
> * Die URL ist die Seite, die wie in `<iframe>` der Besprechungsbenachrichtigung geladen wird. Die Domäne muss sich im `validDomains` Array der Apps in Ihrem App-Manifest befinden.

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
```

```json

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

| Eigenschaftenname | Zweck |
|---|---|
| **type** | Aktivitätstyp. |
| **text** | Der Textinhalt der Nachricht. |
| **summary** | Der Zusammenfassungstext der Nachricht. |
| **channelData.notification.alertInMeeting** | Boolescher Wert, der angibt, ob dem Benutzer während einer Besprechung eine Benachrichtigung angezeigt werden soll. |
| **channelData.notification.externalResourceUrl** | Der Wert der externen Ressourcen-URL der Benachrichtigung.|
| **replyToId** | Die ID der übergeordneten oder Stammnachricht des Threads. |

### <a name="response-codes"></a>Antwortcodes

Die folgende Tabelle hat die Antwortcodes:

|Antwortcode|Beschreibung|
|---|---|
| **201** | Die Aktivität mit Signal wurde erfolgreich gesendet. |
| **401** | Die App antwortet mit einem ungültigen Token. |
| **403** | Die App kann das Signal nicht senden. Der Antwortcode 403 kann aus verschiedenen Gründen auftreten, z. B. wenn der Mandantenadministrator die App während der Live-Site-Migration deaktiviert und blockiert. In diesem Fall enthält die Payload eine detaillierte Fehlermeldung. |
| **404** | Der Meeting-Chat existiert nicht. |

## <a name="get-meeting-details-api"></a>Rufen Sie die Besprechungsdetails-API ab

Die Meeting-Details-API ermöglicht Ihrer App, die statischen Metadaten eines Meetings abzurufen. Die Metadaten stellen Datenpunkte bereit, die sich nicht dynamisch ändern. Die API ist über Bot Services verfügbar. Derzeit unterstützen sowohl private geplante oder wiederkehrende Meetings als auch geplante oder wiederkehrende Channel-Meetings APIs mit jeweils unterschiedlichen RSC-Berechtigungen.

Die `Meeting Details` API muss über eine Bot-Registrierung und eine Bot-ID verfügen. Es erfordert das Bot SDK, um es zu erhalten `TurnContext`. Um die Besprechungsdetails-API zu verwenden, müssen Sie basierend auf dem Umfang einer Besprechung, wie z. B. einer privaten Besprechung oder einer Kanalbesprechung, unterschiedliche RSC-Berechtigungen erhalten.

### <a name="prerequisite"></a>Voraussetzungen

Um die Besprechungsdetails-API zu verwenden, müssen Sie basierend auf dem Umfang einer Besprechung, wie z. B. einer privaten Besprechung oder einer Kanalbesprechung, unterschiedliche RSC-Berechtigungen erhalten.

<br>

<details>

<summary><b>Für App-Manifest-Version 1.12</b></summary>

Verwenden Sie das folgende Beispiel, um die Manifeste`webApplicationInfo`  und `authorization` Eigenschaften Ihrer App für ein beliebiges privates Meeting zu konfigurieren:

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

Verwenden Sie das folgende Beispiel, um die Manifeste `webApplicationInfo` und `authorization` Eigenschaften Ihrer App für ein beliebiges Kanalmeeting zu konfigurieren:

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

<summary><b>Für App-Manifestversion 1.11 oder früher</b></summary>

Verwenden Sie das folgende Beispiel, um die `webApplicationInfo` Eigenschaft Ihres App-Manifests für ein privates Meeting zu konfigurieren:

```json
"webApplicationInfo": {
    "id": "<bot id>",
    "resource": "https://RscPermission",
    "applicationPermissions": [
      "OnlineMeeting.ReadBasic.Chat"
    ]
}
 ```

Verwenden Sie das folgende Beispiel, um die `webApplicationInfo` Eigenschaft Ihres App-Manifests für ein beliebiges Kanalmeeting zu konfigurieren:

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
> Der Bot kann Meeting-Start- oder -Endereignisse automatisch von allen Meetings empfangen, die in allen Kanälen erstellt wurden, indem er zum `ChannelMeeting.ReadBasic.Group` Manifest die RSC-Berechtigung hinzufügt.

### <a name="query-parameter"></a>Abfrageparameter

Die folgende Tabelle listet die Abfrageparameter auf:

|Wert|Typ|Erforderlich|Beschreibung|
|---|---|----|---|
|**meetingId**| Zeichenfolge | Ja | Die Meeting-ID ist über Bot Invoke und Teams Client SDK verfügbar. |

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

---

| Eigenschaftenname | Zweck |
|---|---|
| **details.id** | Die ID der Besprechung, codiert als BASE64-Zeichenfolge. |
| **details.msGraphResourceId** | Die MsGraphResourceId, die speziell für MS-Graph-API-Aufrufe verwendet wird. |
| **details.scheduledStartTime** | Die geplante Startzeit der Besprechung in UTC. |
| **details.scheduledEndTime** | Die geplante Endzeit der Besprechung in UTC. |
| **details.joinUrl** | Die URL, die für die Teilnahme an der Besprechung verwendet wird. |
| **details.title** | Der Titel der Besprechung. |
| **details.type** | Der Typ der Besprechung – z. B. Adhoc, Broadcast, MeetNow, Recurring, Scheduled, Unknown. |
| **conversation.isGroup** | Boolescher Wert, der angibt, ob die Unterhaltung mehr als zwei Teilnehmer hat. |
| **conversation.conversationType** | Der Unterhaltungstyp. |
| **conversation.id** | Die Besprechungschat-ID. |
| **organizer.id** | Die Benutzer-ID des Organisators. |
| **organizer.aadObjectId** | Die Azure Active Directory Objekt-ID des Organisators. |
| **organizer.tenantId** | Die Azure Active Directory Mandanten-ID des Organisators. |

Im Falle eines Besprechungsserientyps:

**startDate**: Gibt das Datum an, an dem mit der Anwendung des Musters begonnen werden soll. Der Wert von "startDate" muss dem Datumswert der Starteigenschaft für die Ereignisressource entsprechen. Hinweis: Das erste Vorkommen der Besprechung kann nicht an diesem Datum stattfinden, wenn es nicht in das Muster passt.

**endDate**: Gibt das Datum an, an dem das Anwenden des Musters beendet werden soll. Hinweis: Das letzte Vorkommen der Besprechung kann nicht an diesem Datum auftreten, wenn es nicht in das Muster passt.

## <a name="send-real-time-captions-api"></a>API zum Senden von Beschriftungen in Echtzeit

Die API zum Senden von Beschriftungen in Echtzeit macht einen POST-Endpunkt für Microsoft Teams Kommunikationszugriff für Cart-Untertitel (Real-Time Translation) verfügbar, von Menschen eingegebene Untertitel. Textinhalte, die an diesen Endpunkt gesendet werden, werden Endbenutzern in einer Microsoft Teams Besprechung angezeigt, wenn sie Untertitel aktiviert haben.

### <a name="cart-url"></a>CART-URL

Sie können die CART-URL für den POST-Endpunkt von der Seite **"Besprechungsoptionen"** in einer Microsoft Teams Besprechung abrufen. Weitere Informationen finden Sie [unter CART-Beschriftungen in einer Microsoft Teams Besprechung](https://support.microsoft.com/office/use-cart-captions-in-a-microsoft-teams-meeting-human-generated-captions-2dd889e8-32a8-4582-98b8-6c96cf14eb47). Sie müssen die CART-URL nicht ändern, um CART-Beschriftungen zu verwenden.

#### <a name="query-parameter"></a>Abfrageparameter

Die CART-URL enthält die folgenden Abfrageparameter:

|Wert|Typ|Erforderlich|Beschreibung|
|---|---|----|----|
|**meetingId**| Zeichenfolge | Ja |Die Meeting-ID ist über Bot Invoke und Teams Client SDK verfügbar. <br/>Beispiel: meetingid=%7b%22tId%22%3a%2272f234bf-86f1-41af-91ab-2d7cd0321b47%22%2c%22oId%22%3a%22e071f268-4241-47f8-8cf3-fc6b84437f23%22%2c%22thId%22%3a%2219%3ameeting_NzJiMjNkMGQtYzk3NS00ZDI1LWJjN2QtMDgyODVhZmI3NzJj%40thread.v2%22%2c%22mId%22%3a%220%22%7d|
|**token**| Zeichenfolge | Ja |Autorisierungstoken.<br/> Beispiel: token=04751eac |

#### <a name="example"></a>Beispiel

```http
https://api.captions.office.microsoft.com/cartcaption?meetingid=%7b%22tId%22%3a%2272f234bf-86f1-41af-91ab-2d7cd0321b47%22%2c%22oId%22%3a%22e071f268-4241-47f8-8cf3-fc6b84437f23%22%2c%22thId%22%3a%2219%3ameeting_NzJiMjNkMGQtYzk3NS00ZDI1LWJjN2QtMDgyODVhZmI3NzJj%40thread.v2%22%2c%22mId%22%3a%220%22%7d&token=gjs44ra
```

### <a name="method"></a>Methode

|Ressource|Methode|Beschreibung|
|----|----|----|
|/cartcaption|POST|Behandeln Sie Beschriftungen für das Meeting, das gestartet wurde|

> [!NOTE]
> Stellen Sie sicher, dass der Inhaltstyp für alle Anforderungen Klartext mit UTF-8-Codierung ist. Der Anfragetext enthält nur Bildunterschriften.

#### <a name="example"></a>Beispiel

```http
POST /cartcaption?meetingid=04751eac-30e6-47d9-9c3f-0b4ebe8e30d9&token=04751eac&lang=en-us HTTP/1.1
Host: api.captions.office.microsoft.com
Content-Type: text/plain
Content-Length: 22
Hello I’m Cortana, welcome to my meeting. 
```

> [!Note]  
> Jede POST-Anforderung generiert eine neue Zeile mit Untertiteln. Um sicherzustellen, dass der Endbenutzer genügend Zeit hat, den Inhalt zu lesen, begrenzen Sie jeden POST-Anforderungstext auf 80–120 Zeichen.

### <a name="error-codes"></a>Fehlercodes

Die folgende Tabelle enthält die Fehlercodes:

|Fehlercode|Beschreibung|
|---|---|
| **400** | Ungültige Anforderung. Der Antworttext enthält weitere Informationen. Beispielsweise werden nicht alle erforderlichen Parameter dargestellt.|
| **401** | Unbefugt. Ungültiges oder abgelaufenes Token. Wenn Sie diesen Fehler erhalten, generieren Sie eine neue WARENKORB-URL in Teams. |
| **404** | Besprechung nicht gefunden oder nicht gestartet. Wenn Sie diese Fehlermeldung erhalten, stellen Sie sicher, dass Sie das Meeting starten und Startuntertitel auswählen. Nachdem Untertitel im Meeting aktiviert wurden, können Sie damit beginnen, Untertitel in das Meeting zu posten.|
| **500** |Internal server error. (Interner Serverfehler) Wenden Sie sich für weitere [Informationen an den Support oder geben Sie Feedback](../feedback.md).|

## <a name="share-app-content-to-stage-api"></a>Teilen Sie App-Inhalte mit der Staging-API

Die `shareAppContentToStage` API ermöglicht es Ihnen, bestimmte Teile Ihrer App für die Besprechungsbühne freizugeben. Die API ist über das Teams-Client-SDK verfügbar.

### <a name="prerequisite"></a>Voraussetzungen

*  Um die `shareAppContentToStage` API zu verwenden, müssen Sie die RSC-Berechtigungen erhalten. Konfigurieren Sie im App-Manifest die `authorization` Eigenschaft `name` und `type` das und im `resourceSpecific` Feld. Beispiel:

    ```json
    "authorization": {
        "permissions": { 
        "resourceSpecific": [
        { 
        "name": "MeetingStage.Write.Chat",
        "type": "Delegated"
        }
        ]
    }
    }
    ```
*  `appContentUrl` muss vom `validDomains` Array innerhalb von manifest.json zugelassen werden, sonst würde die API 501 zurückgeben.

### <a name="query-parameter"></a>Abfrageparameter

Die folgende Tabelle enthält die Abfrageparameter:

|Wert|Typ|Erforderlich|Beschreibung|
|---|---|----|---|
|**callback**| Zeichenfolge | Ja | Callback enthält zwei Parameter, Fehler und Ergebnis. Der *Fehler* kann entweder einen Fehler vom Typ *SdkError* enthalten oder null sein, wenn die Freigabe erfolgreich ist. Das *Ergebnis* kann entweder einen wahren Wert enthalten, wenn die Freigabe erfolgreich war, oder null, wenn die Freigabe fehlschlägt.|
|**appContentURL**| Zeichenfolge | Ja | Die URL, die auf der Bühne geteilt wird.|

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
| **501** | DIE API wird im aktuellen Kontext nicht unterstützt.|
| **1000** | Die App verfügt nicht über die erforderlichen Berechtigungen, um die Freigabe für die Phase zuzulassen.|

## <a name="get-app-content-stage-sharing-state-api"></a>Rufen Sie die App-Content-Stage-Sharing-Status-API ab

Die `getAppContentStageSharingState` API ermöglicht es Ihnen, Informationen über das Teilen von Apps auf der Meeting-Bühne abzurufen.

### <a name="query-parameter"></a>Abfrageparameter

Die folgende Tabelle enthält die Abfrageparameter:

|Wert|Typ|Erforderlich|Beschreibung|
|---|---|----|---|
|**callback**| Zeichenfolge | Ja | Callback enthält zwei Parameter, Fehler und Ergebnis. Der *Fehler* kann entweder einen Fehler vom Typ *SdkError* im Fehlerfall oder null enthalten, wenn die Freigabe erfolgreich ist. Das *Ergebnis* kann entweder ein `AppContentStageSharingState` Objekt enthalten, was einen erfolgreichen Abruf anzeigt, oder null, was einen fehlgeschlagenen Abruf anzeigt.|

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
| **501** | DIE API wird im aktuellen Kontext nicht unterstützt.|
| **1000** | Die App verfügt nicht über die erforderlichen Berechtigungen, um die Freigabe für die Phase zuzulassen.|

## <a name="get-app-content-stage-sharing-capabilities-api"></a>Holen Sie sich die API für die Freigabe von App-Inhalten

Die `getAppContentStageSharingCapabilities` API ermöglicht es Ihnen, die Funktionen der App zum Teilen für die Besprechungsphase abzurufen.

### <a name="query-parameter"></a>Abfrageparameter

Die folgende Tabelle enthält die Abfrageparameter:

|Wert|Typ|Erforderlich|Beschreibung|
|---|---|----|---|
|**callback**| Zeichenfolge | Ja | Callback enthält zwei Parameter, Fehler und Ergebnis. Der *Fehler* kann entweder einen Fehler vom Typ *SdkError* enthalten oder null sein, wenn die Freigabe erfolgreich ist. Das Ergebnis kann entweder ein `AppContentStageSharingState` Objekt enthalten, was einen erfolgreichen Abruf anzeigt, oder null, was einen fehlgeschlagenen Abruf anzeigt.|

### <a name="example"></a>Beispiel

```javascript
microsoftTeams.meeting.getAppContentStageSharingCapabilities((err, result) => {
    if (result.doesAppHaveSharePermission) {
        // Indicates app has permission to share contents to meeting stage.
    }
});
```

Der JSON-Antworttext für die `getAppContentStageSharingCapabilities` API lautet:

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
| **1000** | Die App verfügt nicht über Berechtigungen, um die Freigabe für die Phase zuzulassen.|

## <a name="get-real-time-teams-meeting-events-api"></a>Holen Sie sich die API für Team-Meeting-Events in Echtzeit

Der Benutzer kann Meeting-Ereignisse in Echtzeit empfangen. Sobald eine App mit einem Meeting verknüpft ist, werden die tatsächliche Start- und Endzeit des Meetings mit dem Bot geteilt. Die tatsächliche Start- und Endzeit eines Meetings unterscheidet sich von der geplanten Start- und Endzeit. Die Besprechungsdetails-API stellt die geplante Start- und Endzeit bereit. Das Ereignis gibt die tatsächliche Start- und Endzeit an.

Sie müssen mit dem über das Bot SDK verfügbaren `TurnContext` Objekt vertraut sein. Das `Activity` Objekt in `TurnContext` enthält die Payload mit der tatsächlichen Start- und Endzeit. Echtzeit-Besprechungsereignisse erfordern eine registrierte Bot-ID von der Teams-Plattform. Der Bot kann das Start- oder Endereignis des Meetings automatisch empfangen, indem er das `ChannelMeeting.ReadBasic.Group` Manifest hinzufügt.

### <a name="prerequisite"></a>Voraussetzungen

Ihr App-Manifest muss über die `webApplicationInfo` Eigenschaft verfügen, die Start- und Endereignisse des Meetings zu empfangen. Verwenden Sie die folgenden Beispiele, um Ihr Manifest zu konfigurieren:

<br>

<details>

<summary><b>Für App-Manifest-Version 1.12</b></summary>

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

<summary><b>Für App-Manifestversion 1.11 oder früher</b></summary>

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

### <a name="example-of-getting-meetingstartendeventvalue"></a>Beispiel für bekommen `MeetingStartEndEventvalue`

Der Bot empfängt das Ereignis über den `OnEventActivityAsync` Handler. Um die JSON-Nutzdaten zu deserialisieren, wird ein Modellobjekt eingeführt, um die Metadaten eines Meetings abzurufen. Die Metadaten eines Meetings befinden sich in der `value` Eigenschaft in der Ereignisnutzlast. Das `MeetingStartEndEventvalue` Modellobjekt wird erstellt, dessen Elementvariablen den Schlüsseln unter der `value` Eigenschaft in der Ereignisnutzlast entsprechen.

> [!NOTE]
>
> * Besprechungs-ID abrufen von `turnContext.ChannelData`.
> * Konversations-ID nicht als Besprechungs-ID verwenden.
> * Verwenden Sie keine Besprechungs-ID aus der Nutzlast der Besprechungsereignisse `turncontext.activity.value`.

Der folgende Code zeigt, wie die Metadaten eines Meetings erfasst werden, das `MeetingType`, `Title`, `Id`, `JoinUrl`, `StartTime` und `EndTime` von einem Start-/Endereignis eines Meetings ist:

Meeting-Startereignis

```csharp
protected override async Task OnTeamsMeetingStartAsync(MeetingStartEventDetails meeting, ITurnContext<IEventActivity> turnContext, CancellationToken cancellationToken)
{
    await turnContext.SendActivityAsync(JsonConvert.SerializeObject(meeting));
}
```

Meeting-Ende-Ereignis

```csharp
protected override async Task OnTeamsMeetingEndAsync(MeetingEndEventDetails meeting, ITurnContext<IEventActivity> turnContext, CancellationToken cancellationToken)
{
    await turnContext.SendActivityAsync(JsonConvert.SerializeObject(meeting));
}
```

### <a name="example-of-meeting-start-event-payload"></a>Beispiel für die Nutzlast eines Besprechungsstartereignisses

Der folgende Code stellt ein Beispiel für die Nutzlast eines Besprechungsstartereignisses bereit:

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

### <a name="example-of-meeting-end-event-payload"></a>Beispiel für die Nutzlast eines Besprechungsende-Ereignisses

Der folgende Code stellt ein Beispiel für die Nutzlast eines Besprechungsende-Ereignisses bereit:

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

| Eigenschaftenname | Zweck |
|---|---|
| **name** | Der Name des Benutzers.|
| **type** | Aktivitätstyp. |
| **Timestamp** | Lokales Datum und Uhrzeit der Nachricht, ausgedrückt im ISO-8601-Format. |
| **id** | ID für die Aktivität. |
| **channelId** | Kanal, dem diese Aktivität zugeordnet ist. |
| **serviceUrl** | Dienst-URL, an die Antworten auf diese Aktivität gesendet werden sollen. |
| **from.id** | ID des Benutzers, der die Anforderung gesendet hat. |
| **from.aadObjectId** | Azure Active Directory-Objekt-ID des Benutzers, der die Anforderung gesendet hat. |
| **conversation.isGroup** | Boolescher Wert, der angibt, ob die Unterhaltung mehr als zwei Teilnehmer hat. |
| **conversation.tenantId** | Azure Active Directory Mandanten-ID der Unterhaltung oder Besprechung. |
| **conversation.id** | Die Besprechungschat-ID. |
| **recipient.id** | DIE ID des Benutzers, der die Anforderung empfängt. |
| **recipient.name** | Der Name des Benutzers, der die Anforderung empfängt. |
| **entities.locale** | Entität, die Metadaten zum Gebietsschema enthält. |
| **entities.country** | Entität, die Metadaten zum Land enthält. |
| **entities.type** | Entität, die Metadaten zum Client enthält. |
| **channelData.tenant.id** | Azure Active Directory Mandanten-ID. |
| **channelData.source** | Der Quellname, aus dem das Ereignis ausgelöst oder aufgerufen wird. |
| **channelData.meeting.id** | Die der Besprechung zugeordnete Standard-ID. |
| **Wert. MeetingType** | Der Besprechungstyp. |
| **Wert. Titel** | Der Betreff der Besprechung. |
| **Wert. Id** | Die der Besprechung zugeordnete Standard-ID. |
| **Wert. JoinUrl** | Die Teilnahme-URL der Besprechung. |
| **Wert. Starttime** | Die Startzeit der Besprechung in UTC. |
| **Wert. Endtime** | Die Besprechungsendzeit in UTC. |
| **locale**| Das Gebietsschema der vom Client festgelegten Nachricht. |

## <a name="code-sample"></a>Codebeispiel

|Beispielname | Beschreibung | C# | Node.js |
|----------------|-----------------|--------------|--------------|
| Erweiterbarkeit von Besprechungen | Erweiterbarkeitsbeispiel für Microsoft Teams-Meetings zum Übergeben von Token. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-token-app/csharp) | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-token-app/nodejs) |
| Bubble-Bot für Besprechungsinhalte | Beispiel für die Erweiterbarkeit von Microsoft Teams-Meetings für die Interaktion mit dem Inhaltsblasen-Bot in einem Meeting. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-content-bubble/csharp) |  [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-content-bubble/nodejs)|
| BesprechungsmeetingSidePanel | Beispiel für die Erweiterbarkeit von Microsoft Teams-Meetings für die Interaktion mit dem Seitenbereich in Meetings. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-sidepanel/csharp) | [Anzeigen](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-sidepanel/nodejs)|
| Registerkarte „Details“ im Meeting | Beispiel für die Erweiterbarkeit von Microsoft Teams-Meetings für die Interaktion mit der Registerkarte „Details“ im Meeting. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-details-tab/csharp) | [Anzeigen](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-details-tab/nodejs)|
|Beispiel für Meeting-Ereignisse|Beispiel-App zum Anzeigen von Teams-Besprechungsereignissen in Echtzeit|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-events/csharp)|[Anzeigen](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-events/nodejs)|
|Beispiel für die Rekrutierung von Meetings|Beispiel-App, um die Meeting-Erfahrung für das Rekrutierungsszenario zu zeigen.|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meeting-recruitment-app/csharp)|[Anzeigen](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meeting-recruitment-app/nodejs)|
|App-Installation mit QR-Code|Beispiel-App, die den QR-Code generiert und die App mithilfe des QR-Codes installiert|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-installation-using-qr-code/csharp)|[Anzeigen](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-installation-using-qr-code/nodejs)|

## <a name="see-also"></a>Siehe auch

* [Teams-Authentifizierungsablauf für Registerkarten](../tabs/how-to/authentication/auth-flow-tab.md)
* [Apps für Teams-Besprechungen](teams-apps-in-meetings.md)
* [Live Share SDK](teams-live-share-overview.md)

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Aktivieren und konfigurieren Sie Ihre Apps für Teams-Besprechungen](enable-and-configure-your-app-for-teams-meetings.md)
