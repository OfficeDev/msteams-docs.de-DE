---
title: Apps für Teams-Besprechungen erstellen
author: laujan
description: Erstellen von Apps für Teams-Besprechungen
ms.topic: conceptual
ms.author: lajanuar
keywords: Rollen-API für Teams-Apps-Besprechungen für Benutzerteilnehmer
ms.openlocfilehash: bd0f53ae34a23bdbbdc2e6f3992c7dd0836e9f28
ms.sourcegitcommit: 5cb3453e918bec1173899e7591b48a48113cf8f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/04/2021
ms.locfileid: "50449493"
---
# <a name="create-apps-for-teams-meetings"></a>Apps für Teams-Besprechungen erstellen

## <a name="prerequisites-and-considerations"></a>Voraussetzungen und Überlegungen

* Apps in Besprechungen erfordern grundlegende Kenntnisse der [Teams-App-Entwicklung.](../overview.md) Eine App in einer Besprechung kann aus Features [](../messaging-extensions/what-are-messaging-extensions.md) für Registerkarten, [Bots](../tabs/what-are-tabs.md)und Messagingerweiterungen bestehen und erfordert Updates für das Teams-App-Manifest, um anzugeben, dass die App für Besprechungen verfügbar ist. [](../bots/what-are-bots.md) [](#update-your-app-manifest)

* Damit Ihre App im Besprechungslebenszyklus als Registerkarte funktioniert, muss sie konfigurierbare Registerkarten im [Gruppenchatbereich](../resources/schema/manifest-schema.md#configurabletabs) unterstützen (siehe Erstellen einer [Gruppenregisterkarte](../build-your-first-app/build-channel-tab.md)). Wenn Sie `groupchat` den Bereich unterstützen, wird Ihre App in [Chats](teams-apps-in-meetings.md#pre-meeting-app-experience) vor und [nach besprechungen](teams-apps-in-meetings.md#post-meeting-app-experience) aktiviert.

* Besprechungs-API-URL-Parameter erfordern möglicherweise , und die tenantId Diese sind im Rahmen der `meetingId` `userId` Teams Client SDK- und Botaktivität verfügbar. [](/onedrive/find-your-office-365-tenant-id) Darüber hinaus können zuverlässige Informationen zur Benutzer-ID und Mandanten-ID mithilfe der [Tab-SSO-Authentifizierung abgerufen werden.](../tabs/how-to/authentication/auth-aad-sso.md)

* Einige Besprechungs-APIs, z. B. , erfordern eine `GetParticipant` [Botregistrierung und -ID,](../build-your-first-app/build-bot.md) um Authentifizierungstoken zu generieren.

* Sie müssen die allgemeinen Richtlinien zum [Entwerfen von Teams-Registerkarten für](../tabs/design/tabs.md) Szenarien vor und nach Besprechungen einhalten. Informationen zu Erfahrungen während Besprechungen finden Sie [in](../apps-in-teams-meetings/design/designing-apps-in-meetings.md#use-an-in-meeting-tab) den Entwurfsrichtlinien für Besprechungsdialogfeldern [](../apps-in-teams-meetings/design/designing-apps-in-meetings.md#use-an-in-meeting-dialog) und Besprechungsdialogfeldern.

* Damit Ihre App in Echtzeit aktualisiert werden kann, muss sie basierend auf den Ereignisaktivitäten in der Besprechung auf dem neuesten Stand sein. Diese Ereignisse können sich innerhalb des Besprechungsdialogfelds (siehe Abschlussparameter in ) und andere Oberflächen im `bot Id` `Notification Signal API` gesamten Besprechungslebenszyklus

## <a name="meeting-apps-api-reference"></a>Apireferenz für Besprechungs-Apps

|API|Beschreibung|Anforderung|Quelle|
|---|---|----|---|
|**GetUserContext**| Erhalten Sie Kontextinformationen, um relevante Inhalte auf einer Registerkarte Teams anzuzeigen. |_**microsoftTeams.getContext( ( ) => { /*...* / } )**_|Microsoft Teams client SDK|
|**GetParticipant**|Diese API ermöglicht einem Bot das Abrufen von Teilnehmerinformationen nach Besprechungs-ID und Teilnehmer-ID.|**GET** _**/v1/meetings/{meetingId}/participants/{participantId}?tenantId={tenantId}**_ |Microsoft Bot Framework SDK|
|**NotificationSignal** |Besprechungssignale werden mithilfe der folgenden vorhandenen Unterhaltungsbenachrichtigungs-API (für Benutzer-Bot-Chat) zugestellt. Mit dieser API können Entwickler basierend auf der Aktion des Endbenutzers signalisieren, dass eine Dialogblase in besprechungsbezogenen Fällen angezeigt wird.|**POST** _**/v3/conversations/{conversationId}/activities**_|Microsoft Bot Framework SDK|

### <a name="getusercontext"></a>GetUserContext

Informationen zum [](../tabs/how-to/access-teams-context.md#getting-context-by-using-the-microsoft-teams-javascript-library) Identifizieren und Abrufen von Kontextinformationen für Ihre Registerkarteninhalte finden Sie in der Dokumentation zum Abrufen des Kontexts für Ihre Registerkarteninhalte. Im Rahmen der Erweiterbarkeit von Besprechungen wurde ein neuer Wert für die Antwortnutzlast hinzugefügt:

✔ **meetingId**: wird von einer Registerkarte verwendet, wenn sie im Besprechungskontext ausgeführt wird.

### <a name="getparticipant-api"></a>GetParticipant-API

> [!NOTE]
>
> * Zwischenspeichern Sie keine Teilnehmerrollen, da der Besprechungsorganisator eine Rolle jederzeit ändern kann.
>
> * Teams unterstützt derzeit keine großen Verteilerlisten oder Listengrößen von mehr als 350 Teilnehmern für die `GetParticipant` API.

#### <a name="query-parameters"></a>Abfrageparameter

|Wert|Typ|Erforderlich|Beschreibung|
|---|---|----|---|
|**meetingId**| string | Ja | Der Besprechungsbezeichner ist über Bot Invoke und Teams Client SDK verfügbar.|
|**participantId**| string | Ja | Die participantId ist die Benutzer-ID. Sie ist in Tab SSO, Bot Invoke und Teams Client SDK verfügbar. Es wird dringend empfohlen, eine participantId aus dem Tab-SSO zu erhalten. |
|**tenantId**| string | Ja | Die tenantId ist für die Mandantenbenutzer erforderlich. Sie ist in Tab SSO, Bot Invoke und Teams Client SDK verfügbar. Es wird dringend empfohlen, eine tenantId aus dem Tab-SSO zu erhalten. |

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
GET /v1/meetings/{meetingId}/participants/{participantId}?tenantId={tenantId}
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

* **403**: Die App darf keine Teilnehmerinformationen erhalten. Dies ist die häufigste Fehlerantwort und wird ausgelöst, wenn die App nicht in der Besprechung installiert ist. Beispiel: Wenn die App vom Mandantenadministrator deaktiviert oder während der Risikominderung von Livesite blockiert wird.
* **200**: Teilnehmerinformationen wurden erfolgreich abgerufen.
* **401**: Ungültiges Token.
* **404**: Teilnehmer kann nicht gefunden werden.
* **500**: Die Besprechung ist entweder abgelaufen (mehr als 60 Tage seit dem Ende der Besprechung), oder der Teilnehmer verfügt nicht über Berechtigungen basierend auf seiner Rolle.


**Bald verfügbar**

* **404**: Die Besprechung ist entweder abgelaufen, oder der Teilnehmer kann nicht gefunden werden.


### <a name="notificationsignal-api"></a>NotificationSignal-API

Alle Benutzer in einer Besprechung erhalten die Benachrichtigungen, die über die NotificationSignal-API gesendet werden.

> [!NOTE]
> Derzeit wird das Senden von Zielbenachrichtigungen nicht unterstützt.
> Wenn ein Besprechungsdialogfeld aufgerufen wird, wird derselbe Inhalt auch als Chatnachricht angezeigt.

#### <a name="query-parameters"></a>Abfrageparameter

|Wert|Typ|Erforderlich|Beschreibung|
|---|---|----|---|
|**conversationId**| string | Ja | Die Unterhaltungs-ID ist als Teil des Botaufrufs verfügbar. |

#### <a name="example"></a>Beispiel

Der `Bot ID` wird im Manifest deklariert, und der Bot empfängt ein Ergebnisobjekt. Im folgenden Beispiel ist der Parameter von optional `completionBotId` `externalResourceUrl` in der angeforderten Nutzlast:

> [!NOTE]
> * Die `externalResourceUrl` Parameter für Breite und Höhe müssen in Pixel angegeben werden. Um sicherzustellen, dass die Abmessungen innerhalb der zulässigen Grenzwerte liegen, finden Sie unter [Entwurfsrichtlinien](design/designing-apps-in-meetings.md).
> * Die URL ist die Im Besprechungsdialogfeld `<iframe>` geladene Seite. Die Domäne muss sich im Array der App `validDomains` im App-Manifest befinden.

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

* **201**: Aktivität mit Signal wird erfolgreich gesendet. 
* **401**: Ungültiges Token.
* **403**: Die App kann das Signal nicht senden. Dies kann aus verschiedenen Gründen geschehen, z. B. wenn der Mandantenadministrator die App deaktiviert, die App während der Livewebsitemigration blockiert wird und so weiter. In diesem Fall enthält die Nutzlast eine detaillierte Fehlermeldung. 
* **404**: Besprechungschat ist nicht vorhanden.
 

## <a name="enable-your-app-for-teams-meetings"></a>Aktivieren Ihrer App für Teams-Besprechungen

### <a name="update-your-app-manifest"></a>Aktualisieren Des App-Manifests

Die Funktionen der Besprechungs-App werden in Ihrem App-Manifest über die **konfigurierbarenTabs-Bereiche**  ->  und **Kontextarrays** deklariert. *Scope* definiert, für wen *und welchen Kontext* definiert wird, wo Ihre App verfügbar sein soll.

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

### <a name="context-property"></a>Context-Eigenschaft

Die Registerkarte und die Eigenschaften funktionieren in Übereinstimmung, damit Sie bestimmen können, wo Ihre `context` App angezeigt werden `scopes` soll. Registerkarten im `team` Bereich oder können mehrere `groupchat` Kontexte haben. Die möglichen Werte für die Context-Eigenschaft sind wie folgt:

* **channelTab**: eine Registerkarte in der Kopfzeile eines Teamkanals.
* **privateChatTab**: eine Registerkarte in der Kopfzeile eines Gruppenchats zwischen einer Gruppe von Benutzern, die sich nicht im Kontext eines Teams oder einer Besprechung befindet.
* **meetingChatTab**: eine Registerkarte in der Kopfzeile eines Gruppenchats zwischen einer Gruppe von Benutzern im Kontext einer geplanten Besprechung.
* **meetingDetailsTab**: eine Registerkarte in der Kopfzeile der Besprechungsdetailsetage des Kalenders.
* **meetingSidePanel**: ein in-Meeting-Panel, das über die einheitliche Leiste (U-Leiste) geöffnet wird.

> [!NOTE]
> Die "Context"-Eigenschaft wird derzeit nicht unterstützt und wird daher auf mobilen Clients ignoriert.

## <a name="configure-your-app-for-meeting-scenarios"></a>Konfigurieren Ihrer App für Besprechungsszenarien

> [!NOTE]
> * Damit Ihre App im Registerkartenkatalog angezeigt wird, muss sie konfigurierbare **Registerkarten** und den **Gruppenchatbereich unterstützen.**
>
> * Mobile Clients unterstützen Registerkarten nur in Pre- und Post Meeting Surfaces. Die Besprechungserfahrungen (In-Meeting-Dialog und Registerkarte) auf mobilen Geräten werden in Kürze verfügbar sein. Befolgen Sie [die Anleitungen für Registerkarten auf Mobilgeräten,](../tabs/design/tabs-mobile.md) wenn Sie Ihre Registerkarten für Mobilgeräte erstellen.

### <a name="before-a-meeting"></a>Vor einer Besprechung

Benutzer mit Organisator- und/oder Organisatorrollen fügen einer Besprechung registerkarten mithilfe  der Schaltfläche plus ➕ auf den Seiten Besprechungschat und **Besprechungsdetails** hinzu. Nachrichtenerweiterungen werden über die Ellipsen-/Überlaufmenüleiste hinzugefügt, &#x25CF;&#x25CF;&#x25CF; sich unterhalb des Verfassennachrichtenbereichs im Chat befindet. Bots werden einem Besprechungschat mithilfe der Taste " hinzugefügt und **@** **Bots erhalten ausgewählt.**

✔ Die Benutzeridentität *muss* über [Tabs SSO bestätigt werden.](../tabs/how-to/authentication/auth-aad-sso.md) Nach dieser Authentifizierung kann die App die Benutzerrolle über die GetParticipant-API abrufen.

 ✔ Basierend auf der Benutzerrolle kann die App nun rollenspezifische Erfahrungen präsentieren. Beispielsweise kann eine Abruf-App nur Organisatoren und Organisatoren das Erstellen einer neuen Umfrage ermöglichen.

> **HINWEIS:** Rollenzuweisungen können geändert werden, während eine Besprechung ausgeführt wird.  *Weitere Informationen* [finden Sie unter Rollen in einer Teams-Besprechung.](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019) 

### <a name="during-a-meeting"></a>Während einer Besprechung

#### <a name="sidepanel"></a>**sidePanel**

✔ Fügen Sie in Ihrem App-Manifest  dem Kontextarray wie oben beschrieben **sidePanel** hinzu.

✔ In der Besprechung und in allen Szenarien wird die App auf einer Registerkarte in der Besprechung gerendert, die eine Breite von 320 px hat. Ihre Registerkarte muss dafür optimiert sein. *Siehe*, [FrameContext-Schnittstelle](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/framecontext?view=msteams-client-js-latest&preserve-view=true
)

✔Refer an das [Teams SDK,](../tabs/how-to/access-teams-context.md#user-context) um die **userContext-API** zu verwenden, um Anforderungen entsprechend weiter zu routen.

✔ Lesen Sie den [Teams-Authentifizierungsfluss für Registerkarten](../tabs/how-to/authentication/auth-flow-tab.md). Der Authentifizierungsfluss für Registerkarten ähnelt dem Authentifizierungsfluss für Websites. Daher können Registerkarten OAuth 2.0 direkt verwenden. *Siehe auch*, [Microsoft Identity Platform und OAuth 2.0 Authorization Code Flow](/azure/active-directory/develop/v2-oauth2-auth-code-flow).

✔ Nachrichtenerweiterung sollte wie erwartet funktionieren, wenn sich ein Benutzer in einer Besprechungsansicht befindet und Nachrichtenerweiterungskarten verfassen können.

✔ AppName in der Besprechung – QuickInfo sollte den App-Namen in der Besprechungs-U-Leiste enthalten.

#### <a name="in-meeting-dialog"></a>**Dialogfeld "Besprechung"**

✔ Sie müssen die [Entwurfsrichtlinien für Besprechungsdialogfeldern einhalten.](design/designing-apps-in-meetings.md#use-an-in-meeting-dialog)

✔ Lesen Sie den [Teams-Authentifizierungsfluss für Registerkarten](../tabs/how-to/authentication/auth-flow-tab.md).

✔ Verwenden Sie die [NotificationSignal-API,](create-apps-for-teams-meetings.md#notificationsignal-api) um zu signalisieren, dass eine Blasenbenachrichtigung ausgelöst werden muss.

✔ Als Teil der Benachrichtigungsanforderungsnutzlast die URL ein, in der der anzuzeigende Inhalt gehostet wird.

✔ In-Meeting-Dialogfeld darf kein Aufgabenmodul verwenden.

> [!NOTE]
>
> * Diese Benachrichtigungen sind beständig. Sie müssen die [**submitTask()-Funktion**](../task-modules-and-cards/task-modules/task-modules-bots.md#submitting-the-result-of-a-task-module) aufrufen, um automatisch zu schließen, nachdem ein Benutzer eine Aktion in der Webansicht ergreift. Dies ist eine Anforderung für die App-Übermittlung. *Siehe auch*, [Teams SDK: task module](/javascript/api/@microsoft/teams-js/microsoftteams.tasks?view=msteams-client-js-latest#submittask-string---object--string---string---&preserve-view=true).
>
> * Wenn Sie möchten, dass Ihre App anonyme Benutzer unterstützt, muss die Nutzlast der ursprünglichen Aufrufanforderung auf den Anforderungsmetadaten (ID des Benutzers) im Objekt und nicht auf den Anforderungsmetadaten `from.id` `from` `from.aadObjectId` (Azure Active Directory ID des Benutzers) beruhen. *Weitere* Informationen finden Sie unter Verwenden [von Aufgabenmodulen in Registerkarten](../task-modules-and-cards/task-modules/task-modules-tabs.md) [und Erstellen und Senden des Aufgabenmoduls.](../messaging-extensions/how-to/action-commands/create-task-module.md?tabs=dotnet#the-initial-invoke-request)

### <a name="after-a-meeting"></a>Nach einer Besprechung

Die Konfigurationen nach der Besprechung und vor der Besprechung sind äquivalent.

## <a name="meeting-app-sample"></a>Beispiel für Besprechungs-App

 > [!div class="nextstepaction"]
> [App für den Besprechungstokengenerator](https://github.com/OfficeDev/microsoft-teams-sample-meetings-token)
