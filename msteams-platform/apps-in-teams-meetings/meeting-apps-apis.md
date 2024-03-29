---
title: Besprechungs-Apps-APIs
author: v-sdhakshina
description: In diesem Artikel lernen Sie API-Referenzen für Besprechungs-Apps kennen, die für Teams-Clients und Bot Framework-SDK verfügbar sind, mit Beispielen, Codebeispielen und Antwortcodes.
ms.topic: conceptual
ms.author: lajanuar
ms.localizationpriority: medium
ms.date: 04/07/2022
ms.openlocfilehash: f3d44317dbc8ea317e8fe3c5bdeb19404df75265
ms.sourcegitcommit: 10debe0f01574a21aab54bfac692a4c8373263a8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2022
ms.locfileid: "68789863"
---
# <a name="meeting-apps-apis"></a>Besprechungs-Apps-APIs

Die Erweiterbarkeit von Besprechungen stellt APIs bereit, um die Besprechungserfahrung zu verbessern. Mit Hilfe der aufgeführten APIs können Sie Folgendes ausführen:

* Erstellen Sie Apps oder integrieren Sie vorhandene Apps in den Meeting-Lebenszyklus.
* Verwenden Sie APIs, um Ihre App auf Meetings aufmerksam zu machen.
* Wählen Sie die erforderlichen APIs aus, um das Besprechungserlebnis zu verbessern.

> [!NOTE]
> Verwenden Sie Teams [JavaScript SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) (*Version*: 1.10 und höher) für SSO, um im Meeting-Seitenbereich zu arbeiten.

Die folgende Tabelle enthält eine Liste der APIs, die in der JavaScript-Bibliothek von Microsoft Teams und Microsoft Bot Framework SDKs verfügbar sind:

|Methode| Beschreibung| Quelle|
|---|---|----|
|[**Benutzerkontext abrufen**](#get-user-context-api)| Rufen Sie Kontextinformationen ab, um relevante Inhalte auf einer Microsoft Teams-Registerkarte anzuzeigen.| [Microsoft Teams JavaScript-Bibliotheks-SDK](/microsoftteams/platform/tabs/how-to/access-teams-context#get-context-by-using-the-microsoft-teams-javascript-library) |
|[**Teilnehmer abrufen**](#get-participant-api)| Rufen Sie Teilnehmerinformationen nach Meeting-ID und Teilnehmer-ID ab. | [Microsoft Bot Framework SDK](/dotnet/api/microsoft.bot.builder.teams.teamsinfo.getmeetingparticipantasync?view=botbuilder-dotnet-stable&preserve-view=true)
|[**Senden Sie eine Besprechungsbenachrichtigung**](#send-an-in-meeting-notification)| Stellen Sie Meeting-Signale mithilfe der vorhandenen Konversationsbenachrichtigungs-API für den Benutzer-Bot-Chat bereit und ermöglichen Sie die Benachrichtigung von Benutzeraktionen, die eine Benachrichtigung im Meeting anzeigen. | [Microsoft Bot Framework SDK](/dotnet/api/microsoft.bot.builder.teams.teamsactivityextensions.teamsnotifyuser?view=botbuilder-dotnet-stable&preserve-view=true) |
|[**Besprechungsdetails abrufen**](#get-meeting-details-api)| Rufen Sie die statischen Metadaten eines Meetings ab. | [Microsoft Bot Framework SDK](/dotnet/api/microsoft.bot.builder.teams.teamsinfo.getmeetinginfoasync?view=botbuilder-dotnet-stable&preserve-view=true) |
|[**Senden Sie Untertitel in Echtzeit**](#send-real-time-captions-api)| Senden Sie Untertitel in Echtzeit an ein laufendes Meeting. | [Microsoft Teams JavaScript-Bibliotheks-SDK](/azure/cognitive-services/speech-service/speech-sdk?tabs=nodejs%2Cubuntu%2Cios-xcode%2Cmac-xcode%2Candroid-studio#get-the-speech-sdk&preserve-view=true) |
|[**Teilen Sie App-Inhalte auf der Bühne**](build-apps-for-teams-meeting-stage.md#share-app-content-to-stage-api)| Teilen Sie bestimmte Teile der App für die Meeting-Phase aus dem Seitenbereich der App in einem Meeting. | [Microsoft Teams JavaScript-Bibliotheks-SDK](/javascript/api/@microsoft/teams-js/meeting) |
|[**Holen Sie sich Team-Meeting-Events in Echtzeit**](#get-real-time-teams-meeting-events-api)|Rufen Sie Meeting-Ereignisse in Echtzeit ab, z. B. die tatsächliche Start- und Endzeit.| [Microsoft Bot Framework SDK](/dotnet/api/microsoft.bot.builder.teams.teamsactivityhandler.onteamsmeetingstartasync?view=botbuilder-dotnet-stable&preserve-view=true) |
| [**Abrufen des eingehenden Audiozustands**](#get-incoming-audio-state) | Ermöglicht es einer App, die Einstellung für den eingehenden Audiozustand für den Besprechungsbenutzer abzurufen.| [Microsoft Teams JavaScript-Bibliotheks-SDK](/javascript/api/@microsoft/teams-js/microsoftteams.meeting?view=msteams-client-js-latest&preserve-view=true) |
| [**Eingehende Audiodaten umschalten**](#toggle-incoming-audio) | Ermöglicht einer App das Umschalten der Einstellung für den eingehenden Audiozustand für den Besprechungsbenutzer von Stummschaltung zu Stummschaltung aufheben oder umgekehrt.| [Microsoft Teams JavaScript-Bibliotheks-SDK](/javascript/api/@microsoft/teams-js/microsoftteams.meeting?view=msteams-client-js-latest&preserve-view=true) |

## <a name="get-user-context-api"></a>Holen Sie sich die Benutzerkontext-API

Informationen zum Identifizieren und Abrufen von Kontextinformationen für Ihre Registerkarteninhalte finden Sie un[ter Abrufen von Kontext für Ihre Registerkarte "Teams"](../tabs/how-to/access-teams-context.md#get-context-by-using-the-microsoft-teams-javascript-library). wird von einer `meetingId` Registerkarte verwendet, die im Besprechungskontext ausgeführt wird, und wird für die Antwortnutzlast hinzugefügt.

## <a name="get-participant-api"></a>Teilnehmer-API abrufen

Die `GetParticipant` API muss über eine Bot-Registrierung und -ID verfügen, um Authentifizierungstoken zu generieren. Weitere Informationen finden Sie unter [Bot-Registrierung und -ID](../build-your-first-app/build-bot.md).

> [!NOTE]
>
> * Der Benutzertyp ist nicht in der **getParticipantRole-API** enthalten.
> * Teilnehmerrollen nicht zwischenspeichern, da der Besprechungsorganisator die Rollen jederzeit ändern kann.
> * Derzeit wird die `GetParticipant` API nur für Verteilerlisten oder Dienstpläne mit weniger als 350 Teilnehmern unterstützt.

### <a name="query-parameters"></a>Abfrageparameter

> [!TIP]
> Rufen Sie Teilnehmer-IDs und Mandanten-IDs [auf der Registerkarte SSO-Authentifizierung ab](../tabs/how-to/authentication/tab-sso-overview.md).

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
      "conversationType": "groupChat", 
      "isGroup":true
   }
}
```

---

| Eigenschaftenname | Beschreibung |
|---|---|
| **user.id** | ID des Benutzers. |
| **user.aadObjectId** | Azure Active Directory-Objekt-ID des Benutzers. |
| **user.name** | Der Name des Benutzers. |
| **user.givenName** | Vorname des Benutzers.|
| **user.surname** | Nachname des Benutzers. |
| **user.email** | E-Mail-ID des Benutzers. |
| **user.userPrincipalName** | UPN des Benutzers. |
| **user.tenantId** | Azure Active Directory Mandanten-ID. |
| **user.userRole** | Rolle des Benutzers. Beispiel: "admin" oder "user". |
| **meeting.role** | Die Rolle des Teilnehmers in der Besprechung. Beispiel: "Organizer" oder "Presenter" oder "Attendee". |
| **meeting.inMeeting** | Der Wert, der angibt, ob der Teilnehmer an der Besprechung teilnimmt. |
| **conversation.id** | Die Chat-ID der Besprechung. |
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

Die folgende Tabelle enthält den Abfrageparameter:

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
            "externalResourceUrl": "https://teams.microsoft.com/l/bubble/APP_ID?url=<url>&height=<height>&width=<width>&title=<title>&<completionBotId>=<BOT_APP_ID>"
        }
    },
    "replyToId": "1493070356924"
}
```

---

| Eigenschaftenname | Beschreibung |
|---|---|
| **type** | Aktivitätstyp. |
| **text** | Der Textinhalt der Nachricht. |
| **summary** | Der Zusammenfassungstext der Nachricht. |
| **channelData.notification.alertInMeeting** | Boolescher Wert, der angibt, ob dem Benutzer während einer Besprechung eine Benachrichtigung angezeigt werden soll. |
| **channelData.notification.externalResourceUrl** | Der Wert der externen Ressourcen-URL der Benachrichtigung.|
| **replyToId** | Die ID der übergeordneten oder Stammnachricht des Threads. |
| **APP_ID** | Im Manifest deklarierte App-ID. |
| **completionBotId** | Bot-App-ID |

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

<summary><b>Für App-Manifestversion 1.12 und höher</b></summary>

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

<summary><b>Für App-Manifestversion 1.11 und früher</b></summary>

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
>
> * Der Bot kann Meeting-Start- oder -Endereignisse automatisch von allen Meetings empfangen, die in allen Kanälen erstellt wurden, indem er zum `ChannelMeeting.ReadBasic.Group` Manifest die RSC-Berechtigung hinzufügt.
> * Bei einem Einzelanruf `organizer` ist der Initiator des Chats und bei Gruppenanrufen `organizer` der Anrufinitiator. Bei Besprechungen `organizer` im öffentlichen Kanal ist die Person, die den Kanalbeitrag erstellt hat.

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

```javascript

Not available

```

# <a name="json"></a>[JSON](#tab/json)

```http
GET /v1/meetings/{meetingId}
```

Der JSON-Antworttext für die Besprechungsdetails-API lautet wie folgt:

* **Geplante Besprechungen:**

    ```json

    {
       "details":  { 
             "id": "<meeting ID>", 
             "msGraphResourceId": "MSowYmQ0M2I4OS1lN2QxLTQxNzAtOGZhYi00OWJjYjkwOTk1YWYqMCoqMTk6bWVldGluZ19OVEkyT0RjM01qUXROV1UyW", 
             "scheduledStartTime": "2022-04-24T22:00:00Z", 
             "scheduledEndTime": "2022-04-24T23:00:00Z", 
             "joinUrl": "https://teams.microsoft.com/l/xx", 
             "title": "All Hands", 
             "type": "Scheduled" 
         },
        "conversation": { 
             "isGroup": true, 
             "conversationType": "groupChat", 
             "id": "meeting chat ID" 
             }, 
        "organizer": { 
             "id": "<organizer user ID>", 
             "aadObjectId": "<AAD object ID>",
             "objectId": "<organizer object ID>",
             "tenantId": "<Tenant ID>" 
         }
    } 
    ```

* **Geplante Kanalbesprechungen:**

    ```json
    { 
        "details": { 
        "msGraphResourceId": "MSoxNmUwYjdiYi05M2Q1LTQzNTItOTllMC0yM2VlNWYyZmZmZTIqMTY2MDc1ODYwNzc0MCoqMTk6a0RtQkpEWFZsYWl0QWhHcVB2SzBtRExZbHVTWnJub01WX1MxeFNkTjQxNDFAdGhyZWFkLnRhY3Yy", 
        "scheduledStartTime": "2022-08-17T18:00:00Z", 
        "scheduledEndTime": "2022-08-17T18:30:00Z", 
        "type": "ChannelScheduled", 
        "id": "MCMxOTprRG1CSkRYVmxhaXRBaEdxUHZLMG1ETFlsdVNacm5vTVZfUzF4U2RONDE0MUB0aHJlYWQudGFjdjIjMTY2MDc1ODYwNzc0MA==", 
        "joinUrl": "https://teams.microsoft.com/l/meetup-join/19%3akDmBJDXVlaitAhGqPvK0mDLYluSZrnoMV_S1xSdN4141%40thread.tacv2/1660758607740?context=%7b%22Tid%22%3a%229f044231-b634-4bdd-b29d-2776e3dbd699%22%2c%22Oid%22%3a%2216e0b7bb-93d5-4352-99e0-23ee5f2fffe2%22%7d", 
        "title": "Test channel meeting"
    }, 
    "conversation": { 
        "isGroup": true, 
        "conversationType": "channel", 
        "id": "19:kDmBJDXVlaitAhGqPvK0mDLYluSZrnoMV_S1xSdN4141@thread.tacv2;messageid=1660758607740"
    }, 
    "organizer": { 
        "tenantId": "9f044231-b634-4bdd-b29d-2776e3dbd699", 
        "objectId": "16e0b7bb-93d5-4352-99e0-23ee5f2fffe2", 
        "id": "29:1q4D6ekLXEAALkrqyLXUIcwtVSdXx31bf6vMdfahmkTb9euYVYSsN9x4133pXLV_I2idpVriFe40e19XEZt57bQ", 
        "aadObjectId": "16e0b7bb-93d5-4352-99e0-23ee5f2fffe2"
    }
    }
    ```

* **Einzelanrufe:**

    ```json
    {
        "details": {
             "id": "<meeting ID>",
             "type": "OneToOneCall"
         },
        "conversation": {
             "isGroup": true,
             "conversationType": "groupChat",
             "id": "meeting chat ID"
         },
        "organizer  ": {
             "id": "<organizer user ID>",
             "aadObjectId": "<AAD object ID>",
             "objectId": "<organizer object ID>",
             "tenantId": "<Tenant ID>" 
         }
    }
    
    ```

* **Gruppenanrufe:**

    ```json
    {
        "details": {
             "id": "<meeting ID>",
             "type": "GroupCall",
             "joinUrl": "https://teams.microsoft.com/l/xx"
         },
        "conversation": {
             "isGroup": true,
             "conversationType": "groupChat",
             "id": "meeting chat ID"
         },
        "organizer": {
             "id": "<organizer user ID>",
             "objectId": "<organizer object ID>",
             "aadObjectId": "<AAD object ID>",
             "tenantId": "<Tenant ID>" 
         }
    }
    
    ```

* **Sofortige Besprechungen:**

    ```json
    { 
       "details": { 
             "id": "<meeting ID>", 
             "msGraphResourceId": "MSowYmQ0M2I4OS1lN2QxLTQxNzAtOGZhYi00OWJjYjkwOTk1YWYqMCoqMTk6bWVldGluZ19OVEkyT0RjM01qUXROV1UyW", 
             "scheduledStartTime": "2022-04-24T22:00:00Z", 
             "scheduledEndTime": "2022-04-24T23:00:00Z", 
             "joinUrl": "https://teams.microsoft.com/l/xx", 
             "title": "All Hands", 
             "type": "MeetNow" 
         }, 
        "conversation": { 
             "isGroup": true, 
             "conversationType": "groupChat", 
             "id": "meeting chat ID" 
         },
        "organizer": { 
             "id": "<organizer user ID>", 
             "aadObjectId": "<AAD object ID>", 
             "tenantId": "<Tenant ID>" ,
             "objectId": "<organizer object ID>"
         }
    }
    
    ```

---

| Eigenschaftenname | Beschreibung |
|---|---|
| **details.id** | Die ID der Besprechung, codiert als BASE64-Zeichenfolge. |
| **details.msGraphResourceId** | Die MsGraphResourceId, die speziell für MS Graph-API-Aufrufe verwendet wird. |
| **details.scheduledStartTime** | Die geplante Startzeit der Besprechung in UTC. |
| **details.scheduledEndTime** | Die geplante Endzeit der Besprechung in UTC. |
| **details.joinUrl** | Die URL, die für die Teilnahme an der Besprechung verwendet wird. |
| **details.title** | Der Titel der Besprechung. |
| **details.type** | Der Typ der Besprechung (OneToOneCall, GroupCall, Scheduled, Recurring, MeetNow, ChannelScheduled und ChannelRecurring). |
| **conversation.isGroup** | Boolescher Wert, der angibt, ob die Unterhaltung mehr als zwei Teilnehmer hat. |
| **conversation.conversationType** | Der Konversationstyp. |
| **conversation.id** | Die Chat-ID der Besprechung. |
| **organizer.id** | Die Benutzer-ID des Organisators. |
| **organizer.aadObjectId** | Die Azure Active Directory-Objekt-ID des Organisators. |
| **organizer.tenantId** | Die Azure Active Directory-Mandanten-ID des Organisators. |

Im Fall eines Besprechungsserientyps:

**startDate**: Gibt das Datum an, an dem mit der Anwendung des Musters begonnen werden soll. Der Wert von startDate muss dem Datumswert der start-Eigenschaft für die Ereignisressource entsprechen. Beachten Sie, dass das erste Vorkommen der Besprechung möglicherweise nicht an diesem Datum auftritt, wenn es nicht zum Muster passt.

**endDate**: Gibt das Datum an, an dem die Anwendung des Musters beendet werden soll. Beachten Sie, dass das letzte Vorkommen der Besprechung möglicherweise nicht an diesem Datum stattfindet, wenn es nicht zum Muster passt.

## <a name="send-real-time-captions-api"></a>API zum Senden von Beschriftungen in Echtzeit

Die API zum Senden von Beschriftungen in Echtzeit macht einen POST-Endpunkt für Teams-Cart-Untertitel (Communication Access Real-Time Translation, Echtzeitübersetzung) verfügbar, also von Menschen typisierte Untertitel. An diesen Endpunkt gesendeter Textinhalt wird endbenutzern in einer Teams-Besprechung angezeigt, wenn für sie Untertitel aktiviert sind.

### <a name="cart-url"></a>CART-URL

Sie können die CART-URL für den POST-Endpunkt auf der Seite **Besprechungsoptionen** in einer Teams-Besprechung abrufen. Weitere Informationen finden Sie [unter CART-Beschriftungen in einer Microsoft Teams Besprechung](https://support.microsoft.com/office/use-cart-captions-in-a-microsoft-teams-meeting-human-generated-captions-2dd889e8-32a8-4582-98b8-6c96cf14eb47). Sie müssen die CART-URL nicht ändern, um CART-Beschriftungen zu verwenden.

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

> [!NOTE]  
> Jede POST-Anforderung generiert eine neue Zeile mit Untertiteln. Um sicherzustellen, dass der Endbenutzer genügend Zeit hat, den Inhalt zu lesen, begrenzen Sie jeden POST-Anforderungstext auf 80–120 Zeichen.

### <a name="error-codes"></a>Fehlercodes

Die folgende Tabelle enthält die Fehlercodes:

|Fehlercode|Beschreibung|
|---|---|
| **400** | Ungültige Anforderung. Der Antworttext enthält weitere Informationen. Beispielsweise werden nicht alle erforderlichen Parameter dargestellt.|
| **401** | Unbefugt. Ungültiges oder abgelaufenes Token. Wenn Sie diesen Fehler erhalten, generieren Sie eine neue WARENKORB-URL in Teams. |
| **404** | Besprechung nicht gefunden oder nicht gestartet. Wenn Sie diese Fehlermeldung erhalten, stellen Sie sicher, dass Sie das Meeting starten und Startuntertitel auswählen. Nachdem Untertitel im Meeting aktiviert wurden, können Sie damit beginnen, Untertitel in das Meeting zu posten.|
| **500** |Internal server error. (Interner Serverfehler) Wenden Sie sich für weitere [Informationen an den Support oder geben Sie Feedback](../feedback.md).|

## <a name="get-real-time-teams-meeting-events-api"></a>Holen Sie sich die API für Team-Meeting-Events in Echtzeit

> [!NOTE]
> Teams-Besprechungsereignisse in Echtzeit werden nur für geplante Besprechungen unterstützt.

Der Benutzer kann Meeting-Ereignisse in Echtzeit empfangen. Sobald eine App mit einem Meeting verknüpft ist, werden die tatsächliche Start- und Endzeit des Meetings mit dem Bot geteilt. Die tatsächliche Start- und Endzeit eines Meetings unterscheidet sich von der geplanten Start- und Endzeit. Die Besprechungsdetails-API stellt die geplante Start- und Endzeit bereit. Das Ereignis gibt die tatsächliche Start- und Endzeit an.

Sie müssen mit dem über das Bot SDK verfügbaren `TurnContext` Objekt vertraut sein. Das `Activity` Objekt in `TurnContext` enthält die Payload mit der tatsächlichen Start- und Endzeit. Echtzeit-Besprechungsereignisse erfordern eine registrierte Bot-ID von der Teams-Plattform. Der Bot kann das Start- oder Endereignis des Meetings automatisch empfangen, indem er das `ChannelMeeting.ReadBasic.Group` Manifest hinzufügt.

### <a name="prerequisite"></a>Voraussetzungen

Ihr App-Manifest muss über die `webApplicationInfo` Eigenschaft verfügen, die Start- und Endereignisse des Meetings zu empfangen. Verwenden Sie die folgenden Beispiele, um Ihr Manifest zu konfigurieren:

<br>

<details>

<summary><b>Für App-Manifestversion 1.12 und höher</b></summary>

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

<summary><b>Für App-Manifestversion 1.11 und früher</b></summary>

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

| Eigenschaftenname | Beschreibung |
|---|---|
| **name** | Der Name des Benutzers.|
| **type** | Aktivitätstyp. |
| **Timestamp** | Lokales Datum und uhrzeit der Nachricht, ausgedrückt im ISO-8601-Format. |
| **id** | ID für die Aktivität. |
| **channelId** | Kanal, dem diese Aktivität zugeordnet ist. |
| **serviceUrl** | Dienst-URL, an die Antworten auf diese Aktivität gesendet werden sollen. |
| **from.id** | ID des Benutzers, der die Anforderung gesendet hat. |
| **from.aadObjectId** | Azure Active Directory-Objekt-ID des Benutzers, der die Anforderung gesendet hat. |
| **conversation.isGroup** | Boolescher Wert, der angibt, ob die Unterhaltung mehr als zwei Teilnehmer hat. |
| **conversation.tenantId** | Azure Active Directory-Mandanten-ID der Unterhaltung oder Besprechung. |
| **conversation.id** | Die Chat-ID der Besprechung. |
| **recipient.id** | ID des Benutzers, der die Anforderung erhält. |
| **recipient.name** | Der Name des Benutzers, der die Anforderung erhält. |
| **entities.locale** | Entität, die Metadaten zum Gebietsschema enthält. |
| **entities.country** | Entität, die Metadaten zum Land enthält. |
| **entities.type** | Entität, die Metadaten zum Client enthält. |
| **channelData.tenant.id** | Azure Active Directory Mandanten-ID. |
| **channelData.source** | Der Quellname, von dem aus das Ereignis ausgelöst oder aufgerufen wird. |
| **channelData.meeting.id** | Die standard-ID, die der Besprechung zugeordnet ist. |
| **Wert. MeetingType** | Der Besprechungstyp. |
| **Wert. Titel** | Das Thema der Besprechung. |
| **Wert. Id** | Die standard-ID, die der Besprechung zugeordnet ist. |
| **Wert. JoinUrl** | Die Teilnahme-URL der Besprechung. |
| **Wert. Starttime** | Die Startzeit der Besprechung in UTC. |
| **Wert. Endtime** | Die Endzeit der Besprechung in UTC. |
| **locale**| Das Gebietsschema der nachricht, die vom Client festgelegt wurde. |

## <a name="get-incoming-audio-state"></a>Abrufen des eingehenden Audiozustands

Die `getIncomingClientAudioState` API ermöglicht es einer App, die Einstellung für den eingehenden Audiozustand für den Besprechungsbenutzer abzurufen. Die API ist über das Teams-Client-SDK verfügbar.

> [!NOTE]
>
> * Die `getIncomingClientAudioState` API für Mobilgeräte ist derzeit in [der Öffentlichen Entwicklervorschau](../resources/dev-preview/developer-preview-intro.md) verfügbar.
> * Die ressourcenspezifische Zustimmung ist für Manifestversion 1.12 und höhere Versionen verfügbar, daher funktioniert diese API nicht für Manifestversion 1.11 und frühere Versionen.

### <a name="manifest"></a>Manifest

```JSON
"authorization": {
    "permissions": {
      "resourceSpecific": [
        {
          "name": "OnlineMeetingParticipant.ToggleIncomingAudio.Chat",
          "type": "Delegated"
        }
      ]
    }
  }
```
  
### <a name="example"></a>Beispiel

```javascript
callback = (errcode, result) => {
        if (errcode) {
            // Handle error code
        }
        else {
            // Handle success code
        }
    }

microsoftTeams.meeting.getIncomingClientAudioState(this.callback)
```

### <a name="query-parameter"></a>Abfrageparameter

Die folgende Tabelle enthält den Abfrageparameter:

|Wert|Typ|Erforderlich|Beschreibung|
|---|---|----|---|
|**callback**| Zeichenfolge | Ja | Callback enthält zwei Parameter `error` und `result`. Der *Fehler* kann entweder einen Fehlertyp `SdkError` enthalten oder `null` wenn der Audioabruf erfolgreich ist. Das *Ergebnis* kann entweder den Wert true oder false enthalten, wenn der Audioabruf erfolgreich ist, oder NULL, wenn der Audioabruf fehlschlägt. Die eingehende Audiowiedergabe wird stummgeschaltet, wenn das Ergebnis true ist, und nicht stummgeschaltet, wenn das Ergebnis false ist. |
  
### <a name="response-codes"></a>Antwortcodes

Die folgende Tabelle enthält die Antwortcodes:

|Antwortcode|Beschreibung|
|---|---|
| **500** | Interner Fehler. |
| **501** | Die API wird im aktuellen Kontext nicht unterstützt.|
| **1000** | Die App verfügt nicht über die richtigen Berechtigungen, um das Staging der Freigabe zuzulassen.|

## <a name="toggle-incoming-audio"></a>Eingehende Audiodaten umschalten

Die `toggleIncomingClientAudio` API ermöglicht es einer App, die Einstellung für den eingehenden Audiozustand für den Besprechungsbenutzer von Stummschaltung auf Stummschaltung aufheben oder umgekehrt umzuschalten. Die API ist über das Teams-Client-SDK verfügbar.

> [!NOTE]
>
> * Die `toggleIncomingClientAudio` API für Mobilgeräte ist derzeit in [der Öffentlichen Entwicklervorschau](../resources/dev-preview/developer-preview-intro.md) verfügbar.
> * Die ressourcenspezifische Zustimmung ist für Manifestversion 1.12 und höhere Versionen verfügbar, daher funktioniert diese API nicht für Manifestversion 1.11 und frühere Versionen.

### <a name="manifest"></a>Manifest

```JSON
"authorization": {
 "permissions": {
  "resourceSpecific": [
   {
    "name": "OnlineMeetingParticipant.ToggleIncomingAudio.Chat",
    "type": "Delegated"
   }
  ]
 }
}
```

### <a name="example"></a>Beispiel

```javascript
callback = (error, result) => {
        if (error) {
            // Handle error code
        }
        else {
            // Handle success code
        }
    }

microsoftTeams.meeting.toggleIncomingClientAudio(this.callback)
```
  
### <a name="query-parameter"></a>Abfrageparameter

Die folgende Tabelle enthält den Abfrageparameter:

|Wert|Typ|Erforderlich|Beschreibung|
|---|---|----|---|
|**callback**| Zeichenfolge | Ja | Callback enthält zwei Parameter `error` und `result`. Der *Fehler* kann entweder einen Fehlertyp `SdkError` enthalten oder `null` wenn der Umschalter erfolgreich ist. Das *Ergebnis* kann entweder den Wert true oder false enthalten, wenn der Umschalter erfolgreich ist, oder NULL, wenn die Umschaltfläche fehlschlägt. Die eingehende Audiowiedergabe wird stummgeschaltet, wenn das Ergebnis true ist, und nicht stummgeschaltet, wenn das Ergebnis false ist.
  
### <a name="response-code"></a>Antwortcode

Die folgende Tabelle enthält die Antwortcodes:

|Antwortcode|Beschreibung|
|---|---|
| **500** | Interner Fehler. |
| **501** | Die API wird im aktuellen Kontext nicht unterstützt.|
| **1000** | Die App verfügt nicht über die richtigen Berechtigungen, um das Staging der Freigabe zuzulassen.|

## <a name="code-sample"></a>Codebeispiel

|Beispielname | Beschreibung | C# | Node.js |
|----------------|-----------------|--------------|--------------|
| Erweiterbarkeit von Besprechungen | Beispiel für die Erweiterbarkeit von Teams-Besprechungen für die Übergabe von Token. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-token-app/csharp) | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-token-app/nodejs) |
| Bubble-Bot für Besprechungsinhalte | Beispiel für die Erweiterbarkeit von Teams-Besprechungen für die Interaktion mit einem Inhaltsblasenbot in einer Besprechung. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-content-bubble/csharp) |  [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-content-bubble/nodejs)|
| Besprechungsseitenbereich | Beispiel für die Erweiterbarkeit von Teams-Besprechungen für die Interaktion mit dem Seitenbereich in der Besprechung. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-sidepanel/csharp) | [Anzeigen](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-sidepanel/nodejs)|
| Registerkarte „Details“ im Meeting | Beispiel für die Erweiterbarkeit von Teams-Besprechungen für die Interaktion mit der Registerkarte "Details" in besprechungsinternen Besprechungen. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-details-tab/csharp) | [Anzeigen](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-details-tab/nodejs)|
| Beispiel für Meeting-Ereignisse | Beispiel-App zum Anzeigen von Teams-Besprechungsereignissen in Echtzeit|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-events/csharp)|[Anzeigen](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-events/nodejs)|
| Beispiel für die Rekrutierung von Meetings |Beispiel-App, um die Meeting-Erfahrung für das Rekrutierungsszenario zu zeigen.|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meeting-recruitment-app/csharp)|[Anzeigen](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meeting-recruitment-app/nodejs)|
| App-Installation mit QR-Code |Beispiel-App, die den QR-Code generiert und die App mithilfe des QR-Codes installiert|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-installation-using-qr-code/csharp)|[Anzeigen](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-installation-using-qr-code/nodejs)|

## <a name="see-also"></a>Siehe auch

* [Teams-Authentifizierungsablauf für Registerkarten](../tabs/how-to/authentication/auth-flow-tab.md)
* [Apps für Teams-Besprechungen](teams-apps-in-meetings.md)
* [Live Share SDK](teams-live-share-overview.md)
* [Aufzeichnung einer Teams-Cloudbesprechung](/microsoftteams/cloud-recording)

## <a name="next-steps"></a>Nächste Schritte

[Registerkarten erstellen für Besprechungen](build-tabs-for-meeting.md)
