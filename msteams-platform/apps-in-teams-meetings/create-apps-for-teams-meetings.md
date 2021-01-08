---
title: Apps für Teams-Besprechungen erstellen
author: laujan
description: Erstellen von Apps für Microsoft Teams-Besprechungen
ms.topic: conceptual
ms.author: lajanuar
keywords: Teams-apps-Besprechungen Benutzer Teilnehmer-Rollen-API
ms.openlocfilehash: e768c2dc6722d006c89927adfe60e03243a076d0
ms.sourcegitcommit: f0dfae429385ef02f61896ad49172c4803ef6622
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/31/2020
ms.locfileid: "49740871"
---
# <a name="create-apps-for-teams-meetings"></a>Apps für Teams-Besprechungen erstellen

## <a name="prerequisites-and-considerations"></a>Voraussetzungen und Überlegungen

1. Apps in Besprechungen erfordern grundlegende Kenntnisse der [Teams-App-Entwicklung](../overview.md). Eine app in einer Besprechung kann aus [Registerkarten](../tabs/what-are-tabs.md), [Bots](../bots/what-are-bots.md)und [Messaging Erweiterungs](../messaging-extensions/what-are-messaging-extensions.md) Features bestehen und erfordert Aktualisierungen des Teams-APP- [Manifests](#update-your-app-manifest) , um anzugeben, dass die APP für Besprechungen zur Verfügung steht.

1. Damit Ihre APP im Besprechungs Lebenszyklus als Registerkarte funktioniert, muss Sie konfigurierbare Registerkarten im [Groupchat-Bereich](../resources/schema/manifest-schema.md#configurabletabs)unterstützen. *Weitere Informationen finden Sie unter* [Erweitern Ihrer Teams-App mit einer benutzerdefinierten Registerkarte](../tabs/how-to/add-tab.md). Durch die Unterstützung des `groupchat` Bereichs wird Ihre APP in [Besprechungen vor](teams-apps-in-meetings.md#pre-meeting-app-experience) und [nach](teams-apps-in-meetings.md#post-meeting-app-experience) dem Chatten aktiviert.

1. Die URL-Parameter der Besprechungs-API erfordern möglicherweise, `meetingId` `userId` und die [Mandanten](/onedrive/find-your-office-365-tenant-id) -Nr sind im Rahmen des Teams-Client-SDK und der Bot-Aktivität verfügbar. Außerdem können zuverlässige Informationen für Benutzer-ID und Mandanten-ID mithilfe der [Registerkarten-SSO-Authentifizierung](../tabs/how-to/authentication/auth-aad-sso.md)abgerufen werden.

1. Einige Besprechungs-APIs, wie zum Beispiel, `GetParticipant` erfordern eine [bot-Registrierung und eine bot-APP-ID](../bots/how-to/create-a-bot-for-teams.md#with-an-azure-subscription) zum Generieren von auth-Token.

1. Als Entwickler müssen Sie sich an die allgemeinen [Entwurfsrichtlinien für Teams-Registerkarten](../tabs/design/tabs.md) für vor-und nach Besprechungen sowie an die [in-Meeting-Dialogfeld Richtlinien](design/designing-apps-in-meetings.md#use-an-in-meeting-dialog) für das in-Meeting-Dialogfeld halten, das während einer Teams-Besprechung ausgelöst wurde.

1. Beachten Sie, dass die app in der Regel auf dem neuesten Stand sein muss, damit Ihre APP in Echtzeit aktualisiert werden kann, wenn Sie auf den Ereignis Aktivitäten in der Besprechung basiert. Diese Ereignisse können sich innerhalb des in-Meeting-Dialogs befinden (siehe completion- `bot Id` Parameter in `Notification Signal API` ) und andere Oberflächen im gesamten Besprechungs Lebenszyklus.

## <a name="meeting-apps-api-reference"></a>Besprechungs-apps-API-Referenz

|API|Beschreibung|Anforderung|Source|
|---|---|----|---|
|**Getusercontext**| Abrufen von Kontextinformationen zum Anzeigen relevanter Inhalte auf einer Registerkarte Teams. |_**verläuft. GetContext (() => {/*...* / } )**_|Microsoft Teams-Client-SDK|
|**Getparticipant**|Mit dieser API kann ein bot eine Teilnehmer Information nach Besprechungs-ID und Teilnehmer-ID abrufen.| _**/V1/Meetings/{meetingId}/participants/{participantId} abrufen? Mandanten-Nr = {Mandanten** -Nr}_ |Microsoft bot Framework SDK|
|**NotificationSignal** |Besprechungs Signale werden über die folgende vorhandene Benachrichtigungs-API für Unterhaltungen (für Benutzer-bot-Chat) übermittelt. Mit dieser API können Entwickler basierend auf der Endbenutzer Aktion signalisieren, dass eine Dialog Blase in einer Besprechung angezeigt wird.|**Post** _**/V3/Conversations/{conversationId}/Activities**_|Microsoft bot Framework SDK|

### <a name="getusercontext"></a>Getusercontext

Eine Anleitung zum Identifizieren und Abrufen von Kontextinformationen für die Registerkarteninhalte finden Sie in der Dokumentation zu [Get Context for your Teams](../tabs/how-to/access-teams-context.md#getting-context-by-using-the-microsoft-teams-javascript-library) . Im Rahmen der Erweiterbarkeit von Besprechungen wurde für die Antwort Nutzlast ein neuer Wert hinzugefügt:

✔- **Besprechungs**-Nr: wird von einer Registerkarte bei der Ausführung im Besprechungs Kontext verwendet.

### <a name="getparticipant-api"></a>Getparticipant-API

> [!NOTE]
>
> * Sie sollten keine Teilnehmerrollen Zwischenspeichern, da der Besprechungsorganisator zu einem beliebigen Zeitpunkt eine Rolle ändern kann.
>
> * Microsoft Teams unterstützt derzeit keine großen Verteilerlisten oder Dienstplan Größen von mehr als 350 Teilnehmern für die `GetParticipant` API.

#### <a name="query-parameters"></a>Abfrageparameter

|Wert|Typ|Erforderlich|Beschreibung|
|---|---|----|---|
|**meetingId**| Zeichenfolge | Ja | Die Besprechungs-ID steht über bot Invoke und Microsoft Teams Client SDK zur Verfügung.|
|**Teilnehmer-Nr**| Zeichenfolge | Ja | Die Teilnehmerkennung ist die Benutzer-ID. Sie ist in Tab SSO, bot Invoke und Microsoft Teams Client SDK verfügbar. Es wird dringend empfohlen, eine Teilnehmer-Nr aus der Registerkarte SSO zu erhalten. |
|**tenantId**| Zeichenfolge | Ja | Die Mandanten-Nr ist für die Mandanten Benutzer erforderlich. Sie ist in Tab SSO, bot Invoke und Microsoft Teams Client SDK verfügbar. Es wird dringend empfohlen, eine Mandanten-Nr aus der Registerkarte SSO zu erhalten. |

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

Der Antworttext lautet wie folgt:

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

* **403**: die APP darf keine Teilnehmer Informationen erhalten.  Dies ist die häufigste Fehlerantwort und wird ausgelöst, wenn die APP nicht in der Besprechung installiert ist. Wenn die APP beispielsweise vom mandantenadministrator deaktiviert oder während einer Live-Websitemigration blockiert wird.
* **200**: Teilnehmer Informationen erfolgreich abgerufen.
* **401**: Ungültiges Token.
* **404**: Teilnehmer kann nicht gefunden werden.
* **500**: die Besprechung ist entweder abgelaufen (mehr als 60 Tage seit der Beendigung der Besprechung) oder der Teilnehmer verfügt nicht über die Berechtigungen basierend auf seiner Rolle.


**Bald verfügbar**

* **404**: die Besprechung ist entweder abgelaufen oder der Teilnehmer kann nicht gefunden werden.


### <a name="notificationsignal-api"></a>NotificationSignal-API

> [!NOTE]
> Wenn ein in-Meeting-Dialogfeld aufgerufen wird, wird derselbe Inhalt auch als Chatnachricht angezeigt.

#### <a name="query-parameters"></a>Abfrageparameter

|Wert|Typ|Erforderlich|Beschreibung|
|---|---|----|---|
|**conversationId**| Zeichenfolge | Ja | Die Konversations-ID ist im Rahmen von bot Invoke verfügbar |

#### <a name="example"></a>Beispiel

> [!NOTE]
>
Der `completionBotId` Parameter von `externalResourceUrl` ist im angeforderten Payload-Beispiel optional. `Bot ID` wird im Manifest deklariert, und der bot erhält ein Result-Objekt.
> * Die externalResourceUrl-Parameter width und Height müssen in Pixel angegeben werden. Lesen Sie die [Entwurfsrichtlinien](design/designing-apps-in-meetings.md) , um sicherzustellen, dass sich die Dimensionen innerhalb der zulässigen Grenzen befinden.
> * Die URL ist die Seite, die `<iframe>` im Dialogfeld in der Besprechung geladen wird. Die Domäne muss sich im APP- `validDomains` Array im App-Manifest befinden.

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

#### <a name="response-codes"></a>Antwort Codes

* **201**: Aktivität mit Signal wurde erfolgreich gesendet  
* **401**: Ungültiges Token  
* **201**: die Aktivität mit dem Signal wurde erfolgreich gesendet. 
* **401**: Ungültiges Token.
* **403**: die APP kann das Signal nicht senden. Dies kann auf verschiedene Ursachen zurückzuführen sein, beispielsweise, wenn der mandantenadministrator die APP deaktiviert, die APP während einer Live-Websitemigration blockiert wird usw. In diesem Fall enthält die Nutzlast eine ausführliche Fehlermeldung. 
* **404**: der Besprechungs Chat ist nicht vorhanden.
 

## <a name="enable-your-app-for-teams-meetings"></a>Aktivieren Ihrer APP für Microsoft Teams-Besprechungen

### <a name="update-your-app-manifest"></a>Aktualisieren des App-Manifests

Die APP-Funktionen für Besprechungen werden in Ihrem App-Manifest über die **configurableTabs**  ->  -**Bereiche** und **Kontext** Arrays deklariert. *Scope* definiert, an wen und in welchem *Kontext* definiert wird, wo Ihre app verfügbar sein wird.

> [!NOTE]
> Verwenden Sie das [Manifest-Schema für Entwicklervorschau](../resources/schema/manifest-schema-dev-preview.md) , um dieses in Ihrem App-Manifest zu testen.

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

* **channelTab**: eine Registerkarte in der Kopfzeile eines Team Kanals.
* **privateChatTab**: eine Registerkarte in der Kopfzeile eines Gruppenchats zwischen einer Gruppe von Benutzern, die sich nicht im Kontext eines Teams oder einer Besprechung befinden.
* **meetingChatTab**: eine Registerkarte in der Kopfzeile eines Gruppenchats zwischen einer Gruppe von Benutzern im Kontext einer geplanten Besprechung.
* **meetingDetailsTab**: eine Registerkarte in der Kopfzeile der Ansicht "Besprechungsdetails" des Kalenders.
* **meetingSidePanel**: ein in-Meeting-Bereich, der über den einheitlichen Balken geöffnet wird (u-Leiste).

> [!NOTE]
> Die Eigenschaft "Context" wird derzeit nicht unterstützt und wird daher auf mobilen Clients ignoriert.

## <a name="configure-your-app-for-meeting-scenarios"></a>Konfigurieren Ihrer APP für Besprechungs Szenarien

> [!NOTE]
> * Damit Ihre APP im Registerkarten Katalog sichtbar ist, muss Sie **konfigurierbare Registerkarten** und den **Gruppenchat Bereich** unterstützen.
>
> * Mobile Clients unterstützen Registerkarten nur in Pre-und Post-Besprechungs Oberflächen. Die in-Meeting-Erlebnisse (in-Meeting-Dialog und Tab) auf mobilen Geräten werden in Kürze verfügbar sein. Befolgten Sie die [Anleitungen für Registerkarten auf mobilen Geräten](../tabs/design/tabs-mobile.md) beim Erstellen Ihrer Registerkarten für mobile Geräte.

### <a name="before-a-meeting"></a>Vor einer Besprechung

Benutzer mit Organizer-und/oder Presenter-Rollen fügen mithilfe der Schaltfläche Plus ➕ auf der Seite Besprechungs- **Chat** und Besprechungs **Details** Registerkarten zu einer Besprechung hinzu. Messaging Erweiterungen werden über das Menü Ellipsen/Überlauf hinzugefügt, &#x25CF;&#x25CF;&#x25CF; unterhalb des Bereichs zum Verfassen von Nachrichten im Chat angezeigt wird. Bots werden mit der Taste "" zu einem Besprechungs Chat hinzugefügt **@** und die Option **Bots abrufen** ausgewählt.

✔ Die Benutzeridentität *muss* über die [Registerkarten SSO](../tabs/how-to/authentication/auth-aad-sso.md)bestätigt werden. Nach dieser Authentifizierung kann die APP die Benutzerrolle über die getteilnehmer-API abrufen.

 ✔ Basierend auf der Benutzerrolle kann die App nun rollenspezifische Erlebnisse vorlegen. Beispielsweise kann eine Polling-app nur Organisatoren und Referenten das Erstellen einer neuen Umfrage gestatten.

> **Hinweis**: Rollenzuweisungen können geändert werden, während eine Besprechung ausgeführt wird.  *Siehe* [roles in a Teams Meeting](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019). 

### <a name="during-a-meeting"></a>Während einer Besprechung

#### <a name="sidepanel"></a>**sidePanel**

✔ In Ihrem App-Manifest fügen Sie **sidePanel** dem **Kontext** Array hinzu, wie oben beschrieben.

✔ In der Besprechung als auch in allen Szenarien wird die app in einer in-Meeting-Registerkarte gerendert, die 320 Pixel groß in der Breite ist. Die Registerkarte muss dafür optimiert werden. *Siehe*, [framecontext-Schnittstelle](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/framecontext?view=msteams-client-js-latest&preserve-view=true
)

✔ Sie im Microsoft [Teams-SDK](../tabs/how-to/access-teams-context.md#user-context) nach, um die **benutzercontext** -API zu verwenden, um Anforderungen entsprechend weiterzuleiten.

✔ Bezieht sich auf den Microsoft [Teams-Authentifizierungs Fluss für Registerkarten](../tabs/how-to/authentication/auth-flow-tab.md). Der Authentifizierungs Fluss für Registerkarten ähnelt dem auth-Fluss für Websites. Daher können Registerkarten OAuth 2,0 direkt verwenden. *Siehe auch*, [Microsoft Identity Platform und OAuth 2,0-Autorisierungscode Fluss](/azure/active-directory/develop/v2-oauth2-auth-code-flow).

✔ Nachrichten Erweiterung sollte wie erwartet funktionieren, wenn sich ein Benutzer in einer Besprechungs Ansicht befindet und in der Lage sein sollte, Verfassen von Nachrichten Erweiterungskarten bereitzustellen.

✔ AppName in-Meeting-ToolTip sollte den APP-Namen in der Besprechungs-U-Leiste angeben.

#### <a name="in-meeting-dialog"></a>**Dialogfeld "Besprechung"**

✔ Sie die Entwurfsrichtlinien für das [in-Meeting-Dialogfeld](design/designing-apps-in-meetings.md#use-an-in-meeting-dialog)einhalten.

✔ Bezieht sich auf den Microsoft [Teams-Authentifizierungs Fluss für Registerkarten](../tabs/how-to/authentication/auth-flow-tab.md).

✔ Verwenden Sie die [Benachrichtigungs](/graph/api/resources/notifications-api-overview?view=graph-rest-beta&preserve-view=true) -API, um zu signalisieren, dass eine Blasen Benachrichtigung ausgelöst werden muss.

✔ Als Teil der Nutzlast der Benachrichtigungsanforderung enthalten die URL, in der der zu präsentierende Inhalt gehostet wird.

✔ In-Meeting-Dialogfeld darf nicht Aufgabenmodul verwenden.

> [!NOTE]
>
> * Diese Benachrichtigungen sind in der Natur persistent. Sie müssen die [**submitTask ()**](../task-modules-and-cards/task-modules/task-modules-bots.md#submitting-the-result-of-a-task-module) -Funktion aufrufen, um automatisch zu entlassen, nachdem ein Benutzer eine Aktion in der-Webansicht durchführt. Dies ist eine Voraussetzung für die APP-Übermittlung. *Siehe auch* Microsoft [Teams SDK: Aufgabenmodul](/javascript/api/@microsoft/teams-js/microsoftteams.tasks?view=msteams-client-js-latest#submittask-string---object--string---string---&preserve-view=true).
>
> * Wenn Ihre APP anonyme Benutzer unterstützen soll, muss ihre anfängliche Anforderungsnutzlast auf die `from.id`  (ID der Benutzer)-Anforderungs Metadaten im `from` Objekt und nicht auf die `from.aadObjectId` Anforderungs Metadaten (Azure Active Directory ID des Benutzers) zurückgreifen. *Weitere Informationen finden Sie unter* [Verwenden von Aufgaben Modulen in Registerkarten](../task-modules-and-cards/task-modules/task-modules-tabs.md) und [Erstellen und Senden des Aufgabenmoduls](../messaging-extensions/how-to/action-commands/create-task-module.md?tabs=dotnet#the-initial-invoke-request).

### <a name="after-a-meeting"></a>Nach einer Besprechung

Die Konfigurationen nach der Besprechung und vor der Besprechung sind äquivalent.

## <a name="meeting-app-sample"></a>Beispiel für eine Besprechungs-App

 > [!div class="nextstepaction"]
> [App für die Besprechungs Token-Generator](https://github.com/OfficeDev/microsoft-teams-sample-meetings-token)
