---
title: Apps für Teams-Besprechungen erstellen
author: laujan
description: Erstellen von Apps für Teams-Besprechungen
ms.topic: conceptual
ms.author: lajanuar
localization_priority: Normal
keywords: Rollen-API für Teams-Apps-Besprechungen für Benutzerteilnehmer
ms.openlocfilehash: 3bfbcd0eed1bd287303315ae57cd2f0db039890c
ms.sourcegitcommit: e1fe46c574cec378319814f8213209ad3063b2c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2021
ms.locfileid: "52630180"
---
# <a name="create-apps-for-teams-meetings"></a>Apps für Teams-Besprechungen erstellen

## <a name="prerequisites-and-considerations"></a>Voraussetzungen und Überlegungen

Bevor Sie Apps für Teams erstellen, müssen Sie folgendes wissen:

* Sie müssen wissen, wie Sie apps Teams entwickeln. Weitere Informationen finden Sie unter [Teams App Development](../overview.md).

* Sie müssen das Teams-App-Manifest aktualisieren, um anzugeben, dass die App für Besprechungen verfügbar ist. Weitere Informationen finden Sie unter [App-Manifest](#update-your-app-manifest).

* Damit Ihre App im Besprechungslebenszyklus als Registerkarte funktioniert, muss sie konfigurierbare Registerkarten im Gruppenchatbereich unterstützen. Weitere Informationen finden Sie unter [groupchat scope](../resources/schema/manifest-schema.md#configurabletabs) und [build a group tab](../build-your-first-app/build-channel-tab.md).

* Sie müssen die allgemeinen Richtlinien Teams Registerkartendesigns für Szenarien vor und nach Besprechungen einhalten. Informationen zu Erfahrungen während Besprechungen finden Sie in den Entwurfsrichtlinien für Besprechungsdialogfeldern und Besprechungsdialogfeldern. Weitere Informationen finden Sie unter [Teams Richtlinien](../tabs/design/tabs.md)für den Registerkartenentwurf, Richtlinien für das Design von Registerkarten [in](../apps-in-teams-meetings/design/designing-apps-in-meetings.md#use-an-in-meeting-tab) Besprechungen und Entwurfsrichtlinien für [Besprechungsdialogdialog.](../apps-in-teams-meetings/design/designing-apps-in-meetings.md#use-an-in-meeting-dialog)

* Sie müssen den Bereich `groupchat` unterstützen, um Ihre App in Chats vor und nach besprechungen zu aktivieren. Mit der App vor der Besprechung können Sie Besprechungs-Apps finden und hinzufügen und Aufgaben vor besprechungen ausführen. Mit der App nach der Besprechung können Sie die Ergebnisse der Besprechung anzeigen, z. B. Umfrageergebnisse oder Feedback.

* Die Parameter für die Besprechungs-API-URL müssen `meetingId` über `userId` , und `tenantId` verfügen. Diese sind im Rahmen der Client-SDK- Teams Bot-Aktivität verfügbar. Darüber hinaus können zuverlässige Informationen für Benutzer-ID und Mandanten-ID mithilfe der [Tab-SSO-Authentifizierung abgerufen werden.](../tabs/how-to/authentication/auth-aad-sso.md)

* Die `GetParticipant` API muss über eine Botregistrierung und -ID verfügen, um Authentifizierungstoken zu generieren. Weitere Informationen finden Sie unter [Botregistrierung und ID](../build-your-first-app/build-bot.md).

* Damit Ihre App in Echtzeit aktualisiert werden kann, muss sie basierend auf den Ereignisaktivitäten in der Besprechung auf dem neuesten Stand sein. Diese Ereignisse können sich innerhalb des Dialogfelds in der Besprechung und in anderen Phasen des gesamten Besprechungslebenszyklus finden. Das Dialogfeld in der Besprechung finden Sie unter `bot Id` Completion-Parameter in `Notification Signal API` .

## <a name="meeting-apps-api-reference"></a>Apireferenz für Besprechungs-Apps

|API|Beschreibung|Anforderung|Quelle|
|---|---|----|---|
|**GetUserContext**| Mit dieser API können Sie Kontextinformationen abrufen, um relevante Inhalte auf einer Registerkarte Teams anzuzeigen. |_**microsoftTeams.getContext( ( ) => { /*...* / } )**_|Microsoft Teams Client SDK|
|**GetParticipant**| Mit dieser API kann ein Bot Teilnehmerinformationen nach Besprechungs-ID und Teilnehmer-ID abrufen. |**GET** _**/v1/meetings/{meetingId}/participants/{participantId}?tenantId={tenantId}**_ |Microsoft Bot Framework SDK|
|**NotificationSignal** | Mit dieser API können Sie Besprechungssignale bereitstellen, die mithilfe der vorhandenen Unterhaltungsbenachrichtigungs-API für den Benutzer-Bot-Chat übermittelt werden. Damit können Sie basierend auf der Benutzeraktion, die ein Dialogfeld in der Besprechung zeigt, ein Signal senden. |**POST** _**/v3/conversations/{conversationId}/activities**_|Microsoft Bot Framework SDK|

### <a name="getusercontext"></a>GetUserContext

Informationen zum Identifizieren und Abrufen von Kontextinformationen für Ihre Registerkarteninhalte finden Sie unter [Abrufen des Kontexts für Teams Registerkarte](../tabs/how-to/access-teams-context.md#getting-context-by-using-the-microsoft-teams-javascript-library). `meetingId`wird von einer Registerkarte verwendet, wenn sie im Besprechungskontext ausgeführt wird, und wird für die Antwortnutzlast hinzugefügt.

### <a name="getparticipant-api"></a>GetParticipant-API

> [!NOTE]
> * Zwischenspeichern Sie keine Teilnehmerrollen, da der Besprechungsorganisator eine Rolle jederzeit ändern kann.
> * Teams unterstützt derzeit keine großen Verteilerlisten oder Listengrößen von mehr als 350 Teilnehmern für die `GetParticipant` API.

#### <a name="query-parameters"></a>Abfrageparameter

|Wert|Typ|Erforderlich|Beschreibung|
|---|---|----|---|
|**meetingId**| Zeichenfolge | Ja | Der Besprechungsbezeichner ist über Bot Invoke und Teams Client SDK verfügbar.|
|**participantId**| Zeichenfolge | Ja | Die Teilnehmer-ID ist die Benutzer-ID. Sie ist in Tab SSO, Bot Invoke und Teams Client SDK verfügbar. Es wird empfohlen, eine Teilnehmer-ID aus dem Tab-SSO zu erhalten. |
|**tenantId**| Zeichenfolge | Ja | Die Mandanten-ID ist für die Mandantenbenutzer erforderlich. Sie ist in Tab SSO, Bot Invoke und Teams Client SDK verfügbar. Es wird empfohlen, eine Mandanten-ID aus dem Tab-SSO zu erhalten. |

#### <a name="example"></a>Beispiel

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

|Antwortcode|Beschreibung|
|---|---|
| **403** | Die App darf keine Teilnehmerinformationen erhalten. Dies ist die häufigste Fehlerantwort und wird ausgelöst, wenn die App nicht in der Besprechung installiert ist. Beispiel: Wenn die App vom Mandantenadministrator deaktiviert oder während der Livewebsitemigration blockiert wird.|
| **200** | Die Teilnehmerinformationen werden erfolgreich abgerufen.|
| **401** | Die App antwortet mit einem ungültigen Token.|
| **404** | Die Besprechung ist entweder abgelaufen, oder der Teilnehmer wurde nicht gefunden.|
| **500** | Die Besprechung ist entweder länger als 60 Tage seit dem Ende der Besprechung abgelaufen, oder der Teilnehmer verfügt nicht über Berechtigungen basierend auf seiner Rolle.|

### <a name="notificationsignal-api"></a>NotificationSignal-API

Alle Benutzer in einer Besprechung erhalten die über die API gesendeten `NotificationSignal` Benachrichtigungen.

> [!NOTE]
> * Wenn ein Dialogfeld in der Besprechung aufgerufen wird, wird der Inhalt als Chatnachricht angezeigt.
> * Derzeit wird das Senden gezielter Benachrichtigungen nicht unterstützt.

#### <a name="query-parameters"></a>Abfrageparameter

|Wert|Typ|Erforderlich|Beschreibung|
|---|---|----|---|
|**conversationId**| Zeichenfolge | Ja | Der Unterhaltungsbezeichner ist als Teil des Botaufrufs verfügbar. |

#### <a name="example"></a>Beispiel

Der `Bot ID` wird im Manifest deklariert, und der Bot empfängt ein Ergebnisobjekt.

> [!NOTE]
> * Der `completionBotId` Parameter von ist im `externalResourceUrl` angeforderten Nutzlastbeispiel optional. `Bot ID` wird im Manifest deklariert, und der Bot empfängt ein Ergebnisobjekt.
> * Die `externalResourceUrl` Parameter für Breite und Höhe müssen in Pixel angegeben werden. Um sicherzustellen, dass die Abmessungen innerhalb der zulässigen Grenzwerte liegen, finden Sie unter [Entwurfsrichtlinien](design/designing-apps-in-meetings.md).
> * Die URL ist die Im Besprechungsdialogfeld `<iframe>` geladene Seite. Die Domäne muss sich im Array der App `validDomains` im App-Manifest befinden.

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

* * *

#### <a name="response-codes"></a>Antwortcodes

|Antwortcode|Beschreibung|
|---|---|
| **201** | Die Aktivität mit Signal wird erfolgreich gesendet. |
| **401** | Die App antwortet mit einem ungültigen Token. |
| **403** | Die App kann das Signal nicht senden. Dies kann aus verschiedenen Gründen geschehen, z. B. wenn der Mandantenadministrator die App deaktiviert, die App während der Livewebsitemigration blockiert wird und so weiter. In diesem Fall enthält die Nutzlast eine detaillierte Fehlermeldung. |
| **404** | Der Besprechungschat ist nicht vorhanden. |

## <a name="enable-your-app-for-teams-meetings"></a>Aktivieren Ihrer App für Teams Besprechungen

### <a name="update-your-app-manifest"></a>Aktualisieren Des App-Manifests

Die Funktionen der Besprechungs-App werden in Ihrem App-Manifest mit `configurableTabs` den Arrays , und `scopes` `context` deklariert. Scope definiert, für wen und der Kontext definiert, wo Ihre App verfügbar ist.

> [!NOTE]
> Versuchen Sie, Ihr App-Manifest mit dem [Manifestschema zu aktualisieren.](../resources/schema/manifest-schema-dev-preview.md)
> Apps in Besprechungen benötigen *Gruppenchatbereich.* Der *Teambereich* funktioniert nur für Registerkarten in Kanälen.

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
        "meetingSidePanel",
        "meetingStage"
     ]
    }
  ]
```
> [!NOTE]
> `meetingStage` ist derzeit nur in der Entwicklervorschau verfügbar.

### <a name="context-property"></a>Context-Eigenschaft

Mit der `context` Registerkarte und den Eigenschaften können Sie `scopes` bestimmen, wo Ihre App angezeigt werden muss. Registerkarten im `team` Bereich oder können mehrere `groupchat` Kontexte haben. Es folgen die Werte für die Eigenschaft, aus der Sie `context` alle oder einige der Werte verwenden können:

|Wert|Beschreibung|
|---|---|
| **channelTab** | Eine Registerkarte in der Kopfzeile eines Teamkanals. |
| **privateChatTab** | Eine Registerkarte in der Kopfzeile eines Gruppenchats zwischen einer Gruppe von Benutzern, die sich nicht im Kontext eines Teams oder einer Besprechung befindet. |
| **meetingChatTab** | Eine Registerkarte in der Kopfzeile eines Gruppenchats zwischen einer Gruppe von Benutzern im Kontext einer geplanten Besprechung. |
| **meetingDetailsTab** | Eine Registerkarte in der Kopfzeile der Besprechungsdetailsansicht des Kalenders. |
| **meetingSidePanel** | Ein In-Meeting-Panel, das über die einheitliche Leiste (U-Leiste) geöffnet wird. |
| **meetingStage** | Eine App aus der Sidepanel kann für die Besprechungsphase freigegeben werden. |

> [!NOTE]
> `Context` wird derzeit auf mobilen Clients nicht unterstützt.

## <a name="configure-your-app-for-meeting-scenarios"></a>Konfigurieren Ihrer App für Besprechungsszenarien

> [!NOTE]
> * Damit Ihre App im Registerkartenkatalog angezeigt wird, muss sie konfigurierbare Registerkarten und den Gruppenchatbereich unterstützen.
> * Mobile Clients unterstützen Registerkarten nur in Vor- und Nachbesprechungsphasen.
> * Die Besprechungserfahrungen, die im Dialogfeld "Besprechung" und "Registerkarte" angezeigt werden, werden derzeit auf mobilen Clients nicht unterstützt. Weitere Informationen finden Sie unter [Anleitungen für Registerkarten auf mobilen](../tabs/design/tabs-mobile.md) Geräten beim Erstellen Ihrer Registerkarten für Mobilgeräte.

### <a name="before-a-meeting"></a>Vor einer Besprechung

Vor einer Besprechung können Benutzer Einer Besprechung Registerkarten, Bots und Messagingerweiterungen hinzufügen. Benutzer mit Organisator- und Organisatorrollen können einer Besprechung Registerkarten hinzufügen.

**So fügen Sie einer Besprechung eine Registerkarte hinzu**

1. Wählen Sie in Ihrem Kalender eine Besprechung aus, der Sie eine Registerkarte hinzufügen möchten.
1. Wählen Sie die **Registerkarte Details** aus, und wählen Sie plus aus. <img src="~/assets/images/apps-in-meetings/plusbutton.png" alt="Plus button" width="30"/>. Der Registerkartenkatalog wird angezeigt.

    ![Pre-Meeting-Erfahrung](../assets/images/apps-in-meetings/PreMeeting.png)

1. Wählen Sie im Registerkartenkatalog die App aus, die Sie hinzufügen möchten, und führen Sie die erforderlichen Schritte aus. Die App wird als Registerkarte installiert.
    > [!NOTE] 
    > Derzeit wird das Abrufen von Besprechungsdetails und Teilnehmerinformationen auf der Registerkarte Besprechungen nicht unterstützt.

**So fügen Sie einer Besprechung eine Messagingerweiterung hinzu**

1. Wählen Sie die Ellipsen oder das Überlaufmenü &#x25CF;&#x25CF;&#x25CF; sich im Bereich Verfassen von Nachrichten im Chat befindet.
1. Wählen Sie die App aus, die Sie hinzufügen möchten, und führen Sie die Schritte nach Bedarf aus. Die App wird als Messagingerweiterung installiert.

**So fügen Sie einer Besprechung einen Bot hinzu**

Geben Sie in einem Besprechungschat den **@** Schlüssel ein, und wählen **Sie Bots erhalten aus.**

> [!NOTE]
> * Die Benutzeridentität muss mithilfe von [Tabs SSO bestätigt werden.](../tabs/how-to/authentication/auth-aad-sso.md) Nach der Authentifizierung kann die App die Benutzerrolle mithilfe der `GetParticipant` API abrufen.
> * Basierend auf der Benutzerrolle kann die App rollenspezifische Benutzeroberflächen bereitstellen. Beispielsweise ermöglicht eine Abruf-App nur Organisatoren und Organisatoren, eine neue Umfrage zu erstellen.
> * Rollenzuweisungen können geändert werden, während eine Besprechung ausgeführt wird. Weitere Informationen finden Sie unter [Rollen in einer Teams Besprechung](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019).

### <a name="during-a-meeting"></a>Während einer Besprechung

#### <a name="sidepanel"></a>sidePanel

Mit dem sidePanel können Sie die Erfahrungen in einer Besprechung anpassen, mit denen Organisatoren und Organisatoren unterschiedliche Ansichten und Aktionen ermöglichen. In Ihrem App-Manifest müssen Sie dem Kontextarray sidePanel hinzufügen. In der Besprechung und in allen Szenarien wird die App auf einer Registerkarte in der Besprechung gerendert, die 320 Pixel breit ist. Weitere Informationen finden Sie unter [FrameContext-Schnittstelle](/javascript/api/@microsoft/teams-js/microsoftteams.framecontext?view=msteams-client-js-latest&preserve-view=true).

Informationen zur Verwendung der `userContext` API zum Entsprechend routen von Anforderungen finden Sie unter Teams [SDK](../tabs/how-to/access-teams-context.md#user-context). Weitere [Teams finden Sie unter Authentifizierungsfluss für Registerkarten](../tabs/how-to/authentication/auth-flow-tab.md). Der Authentifizierungsfluss für Registerkarten ähnelt dem Authentifizierungsfluss für Websites. Registerkarten können also OAuth 2.0 direkt verwenden. Siehe, [Microsoft Identity Platform und OAuth 2.0 Autorisierungscodefluss](/azure/active-directory/develop/v2-oauth2-auth-code-flow).

Die Messagingerweiterung funktioniert wie erwartet, wenn sich ein Benutzer in einer Besprechungsansicht befindet und der Benutzer Nachrichtenerweiterungskarten verfassen kann. AppName in-meeting ist eine QuickInfo, in der der App-Name in der Besprechungs-U-Leiste steht.

> [!NOTE]
> Verwenden Sie Version 1.7.0 oder höher von [Teams SDK,](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true)da die Versionen zuvor die Seitenleiste nicht unterstützen.

#### <a name="in-meeting-dialog"></a>Dialogfeld "Besprechung"

Das Dialogfeld in der Besprechung kann verwendet werden, um Teilnehmer während der Besprechung zu engagieren und Während der Besprechung Informationen oder Feedback zu sammeln. Verwenden Sie die [`NotificationSignal`](/graph/api/resources/notifications-api-overview?view=graph-rest-beta&preserve-view=true) API, um zu signalisieren, dass eine Blasenbenachrichtigung ausgelöst werden muss. Geben Sie im Rahmen der Nutzlast der Benachrichtigungsanforderung die URL an, in der der anzuzeigende Inhalt gehostet wird.

Im Besprechungsdialogfeld darf kein Aufgabenmodul verwendet werden. Das Aufgabenmodul wird in einem Besprechungschat nicht aufgerufen. Eine externe Ressourcen-URL wird zum Anzeigen von Inhaltsblasen in einer Besprechung verwendet. Sie können die Methode `submitTask` verwenden, um Daten in einem Besprechungschat zu übermitteln.

> [!NOTE]
> * Sie müssen die [submitTask()-Funktion](../task-modules-and-cards/task-modules/task-modules-bots.md#submitting-the-result-of-a-task-module) aufrufen, um automatisch zu schließen, nachdem ein Benutzer eine Aktion in der Webansicht ausgeführt hat. Dies ist eine Anforderung für die App-Übermittlung. Weitere Informationen finden Sie unter [Teams SDK Task Module](/javascript/api/@microsoft/teams-js/microsoftteams?view=msteams-client-js-latest&preserve-view=true).
> * Wenn Sie möchten, dass Ihre App anonyme Benutzer unterstützt, muss die Nutzlast der ursprünglichen Aufrufanforderung auf den Anforderungsmetadaten im Objekt und nicht auf den `from.id` `from` `from.aadObjectId` Anforderungsmetadaten beruhen. `from.id`ist die Benutzer-ID und `from.aadObjectId` Azure Active Directory (AAD)-ID des Benutzers. Weitere Informationen finden Sie unter [Verwenden von Aufgabenmodulen in Registerkarten](../task-modules-and-cards/task-modules/task-modules-tabs.md) und [Erstellen und Senden des Aufgabenmoduls.](../messaging-extensions/how-to/action-commands/create-task-module.md?tabs=dotnet#the-initial-invoke-request)

#### <a name="share-to-stage"></a>Freigeben in der Phase 

> [!NOTE]
> * Diese Funktion ist derzeit nur in der Entwicklervorschau verfügbar.
> * Um dieses Feature verwenden zu können, muss die App eine Besprechungs-Sidepanel unterstützen.


Mit dieser Funktion können Entwickler eine App für die Besprechungsphase freigeben. Durch aktivieren der Freigabe für die Besprechungsphase können Besprechungsteilnehmer in Echtzeit zusammenarbeiten. 

Der erforderliche Kontext befindet `meetingStage` sich im App-Manifest. Voraussetzung dafür ist der `meetingSidePanel` Kontext. Dadurch wird die **Schaltfläche Freigeben** im Sidepanel wie in der folgenden Abbildung depeziiert aktiviert:

  ![share_to_stage_during_meeting-Erfahrung](~/assets/images/apps-in-meetings/share_to_stage_during_meeting.png)

Die manifeste Änderung, die zum Aktivieren dieser Funktion erforderlich ist, lautet wie folgt: 

```json

"configurableTabs": [
    {
      "configurationUrl": "https://contoso.com/teamstab/configure",
      "canUpdateConfiguration": true,
      "scopes": [
        "groupchat"
      ],
      "context":[
        
        "meetingSidePanel",
        "meetingStage"
     ]
    }
  ]
```



### <a name="after-a-meeting"></a>Nach einer Besprechung

Die Konfigurationen nach der Besprechung und vor der Besprechung sind äquivalent.

## <a name="code-sample"></a>Codebeispiel

|Beispielname | Beschreibung | .NET | Node.js |
|----------------|-----------------|--------------|--------------|
| Erweiterbarkeit von Besprechungen | Microsoft Teams Beispiel für die Besprechungsergehnbarkeit zum Übergeben von Token. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-token-app/csharp) | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-token-app/nodejs) |
| Besprechungsinhaltsblasen-Bot | Microsoft Teams beispiel für die Besprechungsergehnbarkeit für die Interaktion mit dem Inhaltsblasenbot in einer Besprechung. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-content-bubble/csharp) |  [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-content-bubble/nodejs)|
| Meeting SidePanel | Microsoft Teams beispiel für die Besprechungsergehnbarkeit für die Iteracting mit dem Seitenbereich in der Besprechung. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-sidepanel/csharp) |

## <a name="see-also"></a>Sehen Sie ebenfalls

* [Entwurfsrichtlinien für Besprechungsdialogdialog](design/designing-apps-in-meetings.md#use-an-in-meeting-dialog)
* [Teams Authentifizierungsfluss für Registerkarten](../tabs/how-to/authentication/auth-flow-tab.md)
