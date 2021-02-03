---
title: Apps für Teams-Besprechungen erstellen
author: laujan
description: Erstellen von Apps für Teambesprechungen
ms.topic: conceptual
ms.author: lajanuar
keywords: Teams-Apps-Besprechungen – Benutzerteilnehmer-Rollen-API
ms.openlocfilehash: 7f6d8fec735aa21033c6bcb2462c20458634f10a
ms.sourcegitcommit: 843da1730443ff8474a05295f60a6b376ed140da
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/02/2021
ms.locfileid: "50073096"
---
# <a name="create-apps-for-teams-meetings"></a>Apps für Teams-Besprechungen erstellen

## <a name="prerequisites-and-considerations"></a>Voraussetzungen und Überlegungen

* Apps in Besprechungen erfordern einige grundlegende Kenntnisse der [Entwicklung von Teams-Apps.](../overview.md) Eine App in einer Besprechung kann aus Registerkarten, Bots und Messagingerweiterungsfeatures bestehen und erfordert Aktualisierungen des [](../bots/what-are-bots.md)Teams-App-Manifests, um anzugeben, dass die App für Besprechungen verfügbar ist. [](../tabs/what-are-tabs.md) [](../messaging-extensions/what-are-messaging-extensions.md) [](#update-your-app-manifest)

* Damit Ihre App im Besprechungslebenszyklus als Registerkarte funktioniert, muss sie konfigurierbare Registerkarten im Bereich ["Groupchat"](../resources/schema/manifest-schema.md#configurabletabs) unterstützen (siehe Erstellen einer [Gruppenregisterkarte).](../build-your-first-app/build-channel-tab.md) Wenn Sie `groupchat` den Bereich unterstützen, wird Ihre App in [Chats](teams-apps-in-meetings.md#pre-meeting-app-experience) vor und [nach der](teams-apps-in-meetings.md#post-meeting-app-experience) Besprechung aktiviert.

* Besprechungs-API-URL-Parameter erfordern möglicherweise , und die tenantId Diese sind als Teil des Teams Client SDK und der `meetingId` `userId` Botaktivität verfügbar. [](/onedrive/find-your-office-365-tenant-id) Darüber hinaus können zuverlässige Informationen zur Benutzer-ID und Mandanten-ID mithilfe der [Tab-SSO-Authentifizierung abgerufen werden.](../tabs/how-to/authentication/auth-aad-sso.md)

* Einige Besprechungs-APIs, z. B. , erfordern eine Botregistrierung und `GetParticipant` [ID,](../build-your-first-app/build-bot.md) um Authentifizierungstoken zu generieren.

* Sie müssen die allgemeinen Richtlinien für [den Entwurf von Teams-Registerkarten](../tabs/design/tabs.md) für Szenarien vor und nach Besprechungen einhalten. Informationen zu Erfahrungen während Besprechungen finden Sie [in](../apps-in-teams-meetings/design/designing-apps-in-meetings.md#use-an-in-meeting-tab) den Entwurfsrichtlinien für Die Registerkarte "Besprechungen" und "Dialoge [](../apps-in-teams-meetings/design/designing-apps-in-meetings.md#use-an-in-meeting-dialog) in Besprechungen".

* Damit Ihre App in Echtzeit aktualisiert werden kann, muss sie basierend auf den Ereignisaktivitäten in der Besprechung auf dem neuesten Stand sein. Diese Ereignisse können sich innerhalb des Dialogfelds in der Besprechung (siehe Fertigstellungsparameter in) und andere Oberflächen über den `bot Id` `Notification Signal API` gesamten Besprechungslebenszyklus hinweg sein.

## <a name="meeting-apps-api-reference"></a>Referenz zur Besprechungs-Apps-API

|API|Beschreibung|Anforderung|Quelle|
|---|---|----|---|
|**GetUserContext**| Erhalten Sie kontextbezogene Informationen, um relevante Inhalte auf einer Registerkarte "Teams" anzuzeigen. |_**microsoftTeams.getContext( ( ) => { /*...* / } )**_|Microsoft Teams client SDK|
|**GetParticipant**|Diese API ermöglicht einem Bot das Abrufen von Teilnehmerinformationen nach Besprechungs-ID und Teilnehmer-ID.|**GET** _**/v1/meetings/{meetingId}/participants/{participantId}?tenantId={tenantId}**_ |Microsoft Bot Framework SDK|
|**NotificationSignal** |Besprechungssignale werden mithilfe der folgenden vorhandenen Unterhaltungsbenachrichtigungs-API (für Benutzer-Bot-Chat) übermittelt. Diese API ermöglicht Es Entwicklern, basierend auf einer Endbenutzeraktion zu signalisieren, dass eine Dialogblase in besprechungsbezogenen Fällen angezeigt wird.|**POST** _**/v3/conversations/{conversationId}/activities**_|Microsoft Bot Framework SDK|

### <a name="getusercontext"></a>GetUserContext

Informationen zum Identifizieren und Abrufen kontextbezogener Informationen für Ihre Registerkarteninhalte finden Sie in der Dokumentation "Get context for your [Teams](../tabs/how-to/access-teams-context.md#getting-context-by-using-the-microsoft-teams-javascript-library) tab". Im Rahmen der Erweiterbarkeit von Besprechungen wurde ein neuer Wert für die Antwortnutzlast hinzugefügt:

✔ **meetingId**: wird von einer Registerkarte verwendet, wenn sie im Besprechungskontext ausgeführt wird.

### <a name="getparticipant-api"></a>GetParticipant-API

> [!NOTE]
>
> * Speichern Sie die Teilnehmerrollen nicht zwischen, da der Besprechungsorganisator jederzeit eine Rolle ändern kann.
>
> * Teams unterstützt derzeit keine großen Verteilerlisten oder Listengrößen von mehr als 350 Teilnehmern für die `GetParticipant` API.

#### <a name="query-parameters"></a>Abfrageparameter

|Wert|Typ|Erforderlich|Beschreibung|
|---|---|----|---|
|**meetingId**| Zeichenfolge | Ja | Der Besprechungsbezeichner ist über Bot Invoke und Teams Client SDK verfügbar.|
|**participantId**| Zeichenfolge | Ja | Die participantId ist die Benutzer-ID. Sie ist im SSO-, Bot Invoke- und Teams-Client-SDK verfügbar. Es wird dringend empfohlen, eine participantId vom Registerkarten-SSO zu erhalten. |
|**tenantId**| Zeichenfolge | Ja | Die tenantId ist für die Mandantenbenutzer erforderlich. Sie ist im SSO-, Bot Invoke- und Teams-Client-SDK verfügbar. Es wird dringend empfohlen, eine TenantId vom Registerkarten-SSO zu erhalten. |

#### <a name="example"></a>Beispiel

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

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
            TeamsMeetingParticipant participant = GetMeetingParticipantAsync(turnContext, "yourMeetingId", "yourParticipantId", "yourTenantId");
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
GET /v3/meetings/{meetingId}/participants/{participantId}?tenantId={tenantId}
```

Der Antworttext ist:

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

* * *

#### <a name="response-codes"></a>Antwortcodes

* **403:** Die App darf keine Teilnehmerinformationen erhalten.  Dies ist die häufigste Fehlerantwort und wird ausgelöst, wenn die App nicht in der Besprechung installiert ist. Beispielsweise, wenn die App vom Mandantenadministrator deaktiviert oder während der Livemigration der Website blockiert wird.
* **200**: Teilnehmerinformationen wurden erfolgreich abgerufen.
* **401**: Ungültiges Token.
* **404**: Teilnehmer konnte nicht gefunden werden.
* **500**: Die Besprechung ist entweder abgelaufen (mehr als 60 Tage seit Dem Ende der Besprechung), oder der Teilnehmer verfügt nicht über Berechtigungen basierend auf seiner Rolle.


**Bald verfügbar**

* **404:** Die Besprechung ist entweder abgelaufen, oder der Teilnehmer wurde nicht gefunden.


### <a name="notificationsignal-api"></a>NotificationSignal-API

> [!NOTE]
> Wenn ein Besprechungsdialogfeld aufgerufen wird, wird derselbe Inhalt auch als Chatnachricht angezeigt.

#### <a name="query-parameters"></a>Abfrageparameter

|Wert|Typ|Erforderlich|Beschreibung|
|---|---|----|---|
|**conversationId**| Zeichenfolge | Ja | Der Unterhaltungsbezeichner ist als Teil des Botaufrufs verfügbar. |

#### <a name="example"></a>Beispiel

> [!NOTE]
>
Der `completionBotId` Parameter des Parameters ist im Beispiel für die `externalResourceUrl` angeforderte Nutzlast optional. `Bot ID` wird im Manifest deklariert, und der Bot empfängt ein Ergebnisobjekt.
> * Die Parameter "externalResourceUrl width" und "height" müssen in Pixel angegeben werden. Lesen Sie die [Entwurfsrichtlinien,](design/designing-apps-in-meetings.md) um sicherzustellen, dass die Abmessungen innerhalb der zulässigen Grenzwerte liegen.
> * Die URL ist die Seite, die im `<iframe>` Dialogfeld "Besprechung" geladen wird. Die Domäne muss sich im Array der App `validDomains` in Ihrem App-Manifest befinden.

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

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

* * *

#### <a name="response-codes"></a>Antwortcodes

* **201**: Aktivität mit Signal wurde erfolgreich gesendet  
* **401**: Ungültiges Token  
* **201**: Aktivität mit Signal wurde erfolgreich gesendet. 
* **401**: Ungültiges Token.
* **403:** Die App kann das Signal nicht senden. Dies kann aus verschiedenen Gründen geschehen, z. B. wenn der Mandantenadministrator die App deaktiviert, die App während der Livemigration der Website blockiert wird und so weiter. In diesem Fall enthält die Nutzlast eine detaillierte Fehlermeldung. 
* **404**: Besprechungschat ist nicht vorhanden.
 

## <a name="enable-your-app-for-teams-meetings"></a>Aktivieren Ihrer App für Teams-Besprechungen

### <a name="update-your-app-manifest"></a>Aktualisieren des App-Manifests

Die Funktionen der Besprechungs-App werden in Ihrem App-Manifest über die **konfigurierbarenTabs-Bereiche**  ->  und **Kontextarrays** deklariert. *Der* Bereich definiert, für wen *und der* Kontext definiert, wo Ihre App verfügbar sein wird.

> [!NOTE]
> Verwenden Sie [Developer Preview Manifestschema,](../resources/schema/manifest-schema-dev-preview.md) um dies in Ihrem App-Manifest auszuprobieren.

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

### <a name="context-property"></a>Kontexteigenschaft

Die Registerkarte und die Eigenschaften funktionieren in Übereinstimmung, damit Sie bestimmen können, wo `context` Ihre App angezeigt werden `scopes` soll. Registerkarten im Bereich `team` oder Bereich können mehrere `groupchat` Kontexte haben. Folgende Werte sind für die Kontexteigenschaft möglich:

* **channelTab:** eine Registerkarte in der Kopfzeile eines Teamkanals.
* **privateChatTab**: eine Registerkarte in der Kopfzeile eines Gruppenchats zwischen einer Gruppe von Benutzern, die sich nicht im Kontext eines Teams oder einer Besprechung befindet.
* **meetingChatTab**: eine Registerkarte in der Kopfzeile eines Gruppenchats zwischen einer Gruppe von Benutzern im Kontext einer geplanten Besprechung.
* **meetingDetailsTab**: eine Registerkarte in der Kopfzeile der Besprechungsdetailsansicht des Kalenders.
* **meetingSidePanel**: ein Besprechungsfenster, das über die einheitliche Leiste (U-Leiste) geöffnet wird.

> [!NOTE]
> Die Eigenschaft "Context" wird derzeit nicht unterstützt und wird daher auf mobilen Clients ignoriert.

## <a name="configure-your-app-for-meeting-scenarios"></a>Konfigurieren Ihrer App für Besprechungsszenarien

> [!NOTE]
> * Damit Ihre App im Registerkartenkatalog sichtbar ist, muss sie konfigurierbare **Registerkarten** und den **Gruppenchatbereich unterstützen.**
>
> * Mobile Clients unterstützen Registerkarten nur in Oberflächen vor und nach Besprechungen. Die Besprechungserfahrungen (Dialogfeld und Registerkarte in Besprechungen) auf mobilen Geräten werden in Kürze verfügbar sein. Befolgen Sie [die Anleitungen für Registerkarten auf mobilgeräten,](../tabs/design/tabs-mobile.md) wenn Sie Ihre Registerkarten für mobile Geräte erstellen.

### <a name="before-a-meeting"></a>Vor einer Besprechung

Benutzer mit Organisator- und/oder Organisatorrollen fügen registerkarten zu einer Besprechung  hinzu, indem sie die Schaltfläche "plus ➕" auf den Seiten "Besprechungschat" und "Besprechungsdetails" verwenden.  Messagingerweiterungen werden über die Ellipsen/das Überlaufmenü hinzugefügt, &#x25CF;&#x25CF;&#x25CF; sich unterhalb des Bereichs zum Verfassen von Nachrichten im Chat befindet. Bots werden einem Besprechungschat mithilfe des Schlüssels "" hinzugefügt und **@** wählen **Bots erhalten aus.**

✔ Die Benutzeridentität *muss* über [Registerkarten-SSO bestätigt werden.](../tabs/how-to/authentication/auth-aad-sso.md) Nach dieser Authentifizierung kann die App die Benutzerrolle über die GetParticipant-API abrufen.

 ✔ Basierend auf der Benutzerrolle kann die App nun rollenspezifische Erfahrungen präsentieren. Beispielsweise kann eine Abruf-App nur Organisatoren und Organisatoren das Erstellen einer neuen Umfrage ermöglichen.

> **HINWEIS:** Rollenzuweisungen können geändert werden, während eine Besprechung läuft.  *Siehe "Rollen* [in einer Teams-Besprechung".](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019) 

### <a name="during-a-meeting"></a>Während einer Besprechung

#### <a name="sidepanel"></a>**sidePanel**

✔ In Ihrem App-Manifest fügen Sie  **dem Kontextarray sidePanel** hinzu, wie oben beschrieben.

✔ in der Besprechung und in allen Szenarien wird die App auf einer Registerkarte in der Besprechung gerendert, die eine Breite von 320 px hat. Ihre Registerkarte muss dafür optimiert sein. *Siehe*, [FrameContext-Schnittstelle](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/framecontext?view=msteams-client-js-latest&preserve-view=true
)

✔Refer zum Teams [SDK,](../tabs/how-to/access-teams-context.md#user-context) um die **userContext-API** zu verwenden, um Anforderungen entsprechend weiter zu routen.

✔ Sie den Authentifizierungsfluss [von Teams für Registerkarten.](../tabs/how-to/authentication/auth-flow-tab.md) Der Authentifizierungsfluss für Registerkarten ist dem Authentifizierungsfluss für Websites sehr ähnlich. Daher können Registerkarten OAuth 2.0 direkt verwenden. *Siehe auch*, [Microsoft Identity Platform und OAuth 2.0-Autorisierungscodefluss.](/azure/active-directory/develop/v2-oauth2-auth-code-flow)

✔ Nachrichtenerweiterung sollte wie erwartet funktionieren, wenn sich ein Benutzer in einer Besprechungsansicht befindet und in der Lage sein sollte, Nachrichtenerweiterungskarten zum Verfassen zu veröffentlichen.

✔ "AppName" in der Besprechung : QuickInfo sollte den Namen der App in der Besprechungs-U-Leiste enthalten.

#### <a name="in-meeting-dialog"></a>**Dialogfeld "Besprechung"**

✔ Sie müssen die Entwurfsrichtlinien für [Besprechungsdialoge einhalten.](design/designing-apps-in-meetings.md#use-an-in-meeting-dialog)

✔ Sie den Authentifizierungsfluss [von Teams für Registerkarten.](../tabs/how-to/authentication/auth-flow-tab.md)

✔ Verwenden Sie die [NotificationSignal-API,](create-apps-for-teams-meetings.md#notificationsignal-api) um zu signalisieren, dass eine Blasenbenachrichtigung ausgelöst werden muss.

✔ Als Teil der Benachrichtigungsanforderungsnutzlast die URL ein, unter der der zu präsentierende Inhalt gehostet wird.

✔ In-Meeting-Dialogfeld darf kein Aufgabenmodul verwenden.

> [!NOTE]
>
> * Diese Benachrichtigungen sind dauerhaft. Sie müssen die [**submitTask()-Funktion**](../task-modules-and-cards/task-modules/task-modules-bots.md#submitting-the-result-of-a-task-module) aufrufen, um die Funktion automatisch zu schließen, nachdem ein Benutzer eine Aktion in der Webansicht ergreift. Dies ist eine Voraussetzung für die App-Übermittlung. *Siehe auch*, [Teams SDK: Aufgabenmodul](/javascript/api/@microsoft/teams-js/microsoftteams.tasks?view=msteams-client-js-latest#submittask-string---object--string---string---&preserve-view=true).
>
> * Wenn Ihre App anonyme Benutzer unterstützen soll, muss ihre ursprüngliche Aufrufanforderungsnutzlast auf den Anforderungsmetadaten (ID des Benutzers) im Objekt und nicht auf den Anforderungsmetadaten `from.id` `from` `from.aadObjectId` (Azure Active Directory-ID des Benutzers) beruhen. *Siehe "Verwenden* [von Aufgabenmodulen in Registerkarten"](../task-modules-and-cards/task-modules/task-modules-tabs.md) und ["Erstellen und Senden des Aufgabenmoduls".](../messaging-extensions/how-to/action-commands/create-task-module.md?tabs=dotnet#the-initial-invoke-request)

### <a name="after-a-meeting"></a>Nach einer Besprechung

Die Konfigurationen nach der Besprechung und vor der Besprechung sind gleichwertig.

## <a name="meeting-app-sample"></a>Beispiel für eine Besprechungs-App

 > [!div class="nextstepaction"]
> [App für den Besprechungstokengenerator](https://github.com/OfficeDev/microsoft-teams-sample-meetings-token)
