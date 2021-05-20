---
title: Apps für Teams-Besprechungen erstellen
author: laujan
description: Erstellen von Apps für Teambesprechungen
ms.topic: conceptual
ms.author: lajanuar
localization_priority: Normal
keywords: Teams Apps Meetings Benutzer Teilnehmer Rolle api
ms.openlocfilehash: 84d0f5564d7e8e6e34dde1f3d59cc6e7a68d3332
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52565914"
---
# <a name="create-apps-for-teams-meetings"></a>Apps für Teams-Besprechungen erstellen

## <a name="prerequisites-and-considerations"></a>Voraussetzungen und Überlegungen

Bevor Sie Apps für Teams Besprechungen erstellen, müssen Sie Folgendes verstehen:

* Sie müssen wissen, wie Sie Teams Apps entwickeln können. Weitere Informationen finden Sie [unter Teams App-Entwicklung](../overview.md).

* Sie müssen das Teams-App-Manifest aktualisieren, um anzugeben, dass die App für Besprechungen verfügbar ist. Weitere Informationen finden Sie unter [App-Manifest](#update-your-app-manifest).

* Damit Ihre App im Besprechungslebenszyklus als Registerkarte funktioniert, muss sie konfigurierbare Registerkarten im Groupchat-Bereich unterstützen. Weitere Informationen finden Sie unter [groupchat-Bereich](../resources/schema/manifest-schema.md#configurabletabs) und [Erstellen einer Gruppenregisterkarte](../build-your-first-app/build-channel-tab.md).

* Sie müssen allgemeine richtlinien für Teams Registerkartenentwurfs für Vor- und Nachbesprechungsszenarien einhalten. Erfahrungen während Besprechungen finden Sie auf der Registerkarte in Besprechungen und in Besprechungsdialogentwurfsrichtlinien. Weitere Informationen finden Sie unter [Teams Richtlinien für den Entwurf der Registerkarte](../tabs/design/tabs.md), Richtlinien für den Entwurf von [Registerkarten in Besprechungen](../apps-in-teams-meetings/design/designing-apps-in-meetings.md#use-an-in-meeting-tab) und [Richtlinien für den Entwurf von Besprechungsdialogen](../apps-in-teams-meetings/design/designing-apps-in-meetings.md#use-an-in-meeting-dialog).

* Sie müssen den `groupchat` Bereich unterstützen, um Ihre App in Chats vor Besprechungen und nach Besprechungen zu aktivieren. Mit der App-Erfahrung vor der Besprechung können Sie Besprechungs-Apps suchen und hinzufügen und Vorbesprechungsaufgaben ausführen. Mit der App-Erfahrung nach dem Meeting können Sie die Ergebnisse der Besprechung anzeigen, z. B. Umfrageergebnisse oder Feedback.

* Besprechungs-API-URL-Parameter müssen `meetingId` , `userId` und haben `tenantId` . Diese sind als Teil des Teams Client-SDK und der Bot-Aktivität verfügbar. Darüber hinaus können zuverlässige Informationen für Benutzer-ID und Mandanten-ID mithilfe der [Tab-SSO-Authentifizierung](../tabs/how-to/authentication/auth-aad-sso.md)abgerufen werden.

* Die `GetParticipant` API muss über eine Bot-Registrierung und eine ID verfügen, um Auth-Token zu generieren. Weitere Informationen finden Sie unter [Bot-Registrierung und ID](../build-your-first-app/build-bot.md).

* Damit Ihre App in Echtzeit aktualisiert werden kann, muss sie basierend auf den Ereignisaktivitäten in der Besprechung auf dem neuesten Stand sein. Diese Ereignisse können sich innerhalb des Dialogfelds in der Besprechung und in anderen Phasen des Besprechungslebenszyklus befinden. Das Dialogfeld in der Besprechung finden Sie `bot Id` unter Abschlussparameter in `Notification Signal API` .

## <a name="meeting-apps-api-reference"></a>API-Referenz für Besprechungs-Apps

|API|Beschreibung|Anforderung|Quelle|
|---|---|----|---|
|**GetUserContext**| Mit dieser API können Sie Kontextinformationen abrufen, um relevante Inhalte auf einer Teams Registerkarte anzuzeigen. |_**microsoftTeams.getContext( ( ) => / } )**_|Microsoft Teams Client-SDK|
|**GetParticipant**| Diese API ermöglicht es einem Bot, Teilnehmerinformationen durch Besprechungs-ID und Teilnehmer-ID abzurufen. |**GET** _**/v1/meetings/'meetingId'/participants/'participantId'?tenantId='tenantId'**_ |Microsoft Bot Framework Sdk|
|**NotificationSignal** | Mit dieser API können Sie Besprechungssignale bereitstellen, die mithilfe der vorhandenen Konversationsbenachrichtigungs-API für Dener-Bot-Chats bereitgestellt werden. Es ermöglicht Ihnen, basierend auf Benutzeraktion zu signalisieren, die ein Dialogfeld in der Besprechung anzeigt. |**POST** _**/v3/conversations/-conversationId/-Aktivitäten**_|Microsoft Bot Framework Sdk|

### <a name="getusercontext"></a>GetUserContext

Informationen zum Identifizieren und Abrufen von Kontextinformationen für Ihren Registerkarteninhalt finden Sie unter [Kontext abrufen für Ihre Registerkarte Teams](../tabs/how-to/access-teams-context.md#getting-context-by-using-the-microsoft-teams-javascript-library). `meetingId`wird von einer Registerkarte verwendet, wenn sie im Besprechungskontext ausgeführt wird, und wird für die Antwortnutzlast hinzugefügt.

### <a name="getparticipant-api"></a>GetParticipant-API

> [!NOTE]
> * Cache-Teilnehmerrollen nicht, da der Besprechungsorganisator eine Rolle jederzeit ändern kann.
> * Teams unterstützt derzeit keine großen Verteilerlisten oder Dienstplangrößen von mehr als 350 Teilnehmern für die `GetParticipant` API.

#### <a name="query-parameters"></a>Abfrageparameter

|Wert|Typ|Erforderlich|Beschreibung|
|---|---|----|---|
|**meetingId**| Zeichenfolge | Ja | Der Besprechungsbezeichner ist über Bot Invoke und Teams Client SDK verfügbar.|
|**participantId**| Zeichenfolge | Ja | Die Teilnehmer-ID ist die Benutzer-ID. Sie ist in Tab SSO, Bot Invoke und Teams Client SDK verfügbar. Es wird empfohlen, eine Teilnehmer-ID vom Tab-SSO zu erhalten. |
|**tenantId**| Zeichenfolge | Ja | Die Mandanten-ID ist für die Mandantenbenutzer erforderlich. Sie ist in Tab SSO, Bot Invoke und Teams Client SDK verfügbar. Es wird empfohlen, eine Mandanten-ID vom Tab-SSO abzubekommen. |

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

Der JSON-Antworttext für `GetParticipant` API lautet:

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
| **403** | Die App ist nicht berechtigt, Teilnehmerinformationen zu erhalten. Dies ist die häufigste Fehlerantwort und wird ausgelöst, wenn die App nicht in der Besprechung installiert ist. Wenn die App z. B. vom Mandantenadministrator deaktiviert oder während der Livesitemigration blockiert wird.|
| **200** | Die Teilnehmerinformationen werden erfolgreich abgerufen.|
| **401** | Die App antwortet mit einem ungültigen Token.|
| **404** | Die Besprechung ist entweder abgelaufen, oder der Teilnehmer wurde nicht gefunden.|
| **500** | Die Besprechung ist entweder mehr als 60 Tage nach dem Ende der Besprechung abgelaufen, oder der Teilnehmer verfügt nicht über Berechtigungen basierend auf seiner Rolle.|

### <a name="notificationsignal-api"></a>NotificationSignal-API

Alle Benutzer in einer Besprechung erhalten die über die API gesendeten `NotificationSignal` Benachrichtigungen.

> [!NOTE]
> * Wenn ein Dialogfeld in der Besprechung aufgerufen wird, wird der Inhalt als Chatnachricht angezeigt.
> * Derzeit wird das Senden gezielter Benachrichtigungen nicht unterstützt.

#### <a name="query-parameters"></a>Abfrageparameter

|Wert|Typ|Erforderlich|Beschreibung|
|---|---|----|---|
|**conversationId**| Zeichenfolge | Ja | Der Konversationsbezeichner ist als Teil des Bot-Aufrufs verfügbar. |

#### <a name="example"></a>Beispiel

Der `Bot ID` wird im Manifest deklariert und der Bot erhält ein Ergebnisobjekt.

> [!NOTE]
> * Der `completionBotId` Parameter des ist im `externalResourceUrl` angeforderten Nutzlastbeispiel optional. `Bot ID` wird im Manifest deklariert und der Bot erhält ein Ergebnisobjekt.
> * Die `externalResourceUrl` Parameter breite und höhen müssen in Pixeln sein. Informationen zu den Bemaßungen innerhalb der zulässigen Grenzwerte finden Sie unter [Entwurfsrichtlinien](design/designing-apps-in-meetings.md).
> * Die URL ist die Seite, die als `<iframe>` in das Dialogfeld "In-Meeting" geladen wird. Die Domäne muss sich im Array der App `validDomains` in Ihrem App-Manifest befinden.

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
| **403** | Die App kann das Signal nicht senden. Dies kann aus verschiedenen Gründen geschehen, z. B. wenn der Mandantenadministrator die App deaktiviert, die App während der Live-Websitemigration blockiert wird usw. In diesem Fall enthält die Nutzlast eine detaillierte Fehlermeldung. |
| **404** | Der Besprechungschat ist nicht vorhanden. |

## <a name="enable-your-app-for-teams-meetings"></a>Aktivieren Sie Ihre App für Teams Besprechungen

### <a name="update-your-app-manifest"></a>Aktualisieren Ihres App-Manifests

Die Besprechungs-App-Funktionen werden in Ihrem App-Manifest mit den `configurableTabs` , `scopes` und `context` Arrays deklariert. Der Bereich definiert, für wen und den Kontext definiert, wo Ihre App verfügbar ist.

> [!NOTE]
> Versuchen Sie, Ihr App-Manifest mit dem [Manifestschema](../resources/schema/manifest-schema-dev-preview.md)zu aktualisieren.
> Apps in Besprechungen benötigen *gruppenchat-Bereich.* Der *Teambereich* funktioniert nur für Registerkarten in Kanälen.

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

### <a name="context-property"></a>Kontexteigenschaft

Mit der Registerkarte `context` und den Eigenschaften können Sie `scopes` bestimmen, wo Ihre App angezeigt werden muss. Registerkarten im `team` `groupchat` Oderbereich können mehr als einen Kontext haben. Im Folgenden sind die Werte für die `context` Eigenschaft, von der aus Sie alle oder einige der Werte verwenden können:

|Wert|Beschreibung|
|---|---|
| **channelTab** | Eine Registerkarte in der Kopfzeile eines Teamkanals. |
| **privateChatTab** | Eine Registerkarte in der Kopfzeile eines Gruppenchats zwischen einer Gruppe von Benutzern, die sich nicht im Kontext eines Teams oder einer Besprechung befinden. |
| **meetingChatTab** | Eine Registerkarte in der Kopfzeile eines Gruppenchats zwischen einer Gruppe von Benutzern im Kontext einer geplanten Besprechung. |
| **MeetingDetailsTab** | Eine Registerkarte in der Kopfzeile der Besprechungsdetails Ansicht des Kalenders. |
| **meetingSidePanel** | Ein In-Meeting-Panel wurde über die einheitliche Bar (U-Bar) geöffnet. |
| **meetingStage** | Eine App aus dem Sidepanel kann für die Besprechungsphase freigegeben werden. |

> [!NOTE]
> `Context` Wird die Eigenschaft derzeit auf mobilen Clients nicht unterstützt.

## <a name="configure-your-app-for-meeting-scenarios"></a>Konfigurieren Ihrer App für Besprechungsszenarien

> [!NOTE]
> * Damit Ihre App in der Registerkartengalerie sichtbar ist, muss sie konfigurierbare Registerkarten und den Gruppenchatbereich unterstützen.
> * Mobile Clients unterstützen Registerkarten nur in Pre- und Post-Meeting-Phasen.
> * Die Besprechungsfunktionen, die sich im Besprechungsdialogfeld und auf der Registerkarte befinden, werden derzeit auf mobilen Clients nicht unterstützt. Weitere Informationen finden Sie in der [Anleitung zu Registerkarten auf Mobilgeräten,](../tabs/design/tabs-mobile.md) wenn Sie Ihre Registerkarten für Mobilgeräte erstellen.

### <a name="before-a-meeting"></a>Vor einer Besprechung

Vor einer Besprechung können Benutzer Registerkarten, Bots und Messagingerweiterungen zu einer Besprechung hinzufügen. Benutzer mit Organisator- und Referentenrollen können einer Besprechung Registerkarten hinzufügen.

**So fügen Sie einer Besprechung eine Registerkarte hinzu**

1. Wählen Sie in Ihrem Kalender eine Besprechung aus, der Sie eine Registerkarte hinzufügen möchten.
1. Wählen Sie die Registerkarte **Details** und wählen Sie plus <img src="~/assets/images/apps-in-meetings/plusbutton.png" alt="Plus button" width="30"/>. Die Registerkartengalerie wird angezeigt.

    ![Pre-Meeting-Erfahrung](../assets/images/apps-in-meetings/PreMeeting.png)

1. Wählen Sie im Registerkartenkatalog die App aus, die Sie hinzufügen möchten, und führen Sie die erforderlichen Schritte aus. Die App wird als Registerkarte installiert.
    > [!NOTE] 
    > Derzeit wird das Abrufen von Besprechungsdetails und Teilnehmerinformationen auf der Registerkarte Besprechungen nicht unterstützt.

**So fügen Sie einer Besprechung eine Messagingerweiterung hinzu**

1. Wählen Sie die Ellipsen oder das Überlaufmenü &#x25CF;&#x25CF;&#x25CF; im Nachrichtenbereich zum Verfassen im Chat.
1. Wählen Sie die App aus, die Sie hinzufügen möchten, und führen Sie die erforderlichen Schritte aus. Die App wird als Messagingerweiterung installiert.

**So fügen Sie einer Besprechung einen Bot hinzu**

Geben Sie in einem Besprechungschat die Taste ein **@** und wählen **Sie Bots abrufen** aus.

> [!NOTE]
> * Die Benutzeridentität muss mithilfe von [Tabs SSO](../tabs/how-to/authentication/auth-aad-sso.md)bestätigt werden. Nach der Authentifizierung kann die App die Benutzerrolle mithilfe der `GetParticipant` API abrufen.
> * Basierend auf der Benutzerrolle bietet die App rollenspezifische Erlebnisse. Eine Umfrage-App ermöglicht z. B. nur Organisatoren und Moderatoren, eine neue Umfrage zu erstellen.
> * Rollenzuweisungen können während einer Besprechung geändert werden. Weitere Informationen finden Sie unter [Rollen in einer besprechung Teams](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019).

### <a name="during-a-meeting"></a>Während eines Meetings

#### <a name="sidepanel"></a>sidePanel

Mit dem sidePanel können Sie Erlebnisse in einer Besprechung anpassen, die es Organisatoren und Referenten ermöglichen, unterschiedliche Ansichten und Aktionen zu haben. In Ihrem App-Manifest müssen Sie dem Kontextarray sidePanel hinzufügen. In der Besprechung und in allen Szenarien wird die App in einer Besprechungsregisterkarte mit einer Breite von 320 Pixeln gerendert. Weitere Informationen finden Sie unter [FrameContext-Schnittstelle](/javascript/api/@microsoft/teams-js/framecontext?view=msteams-client-js-latest&preserve-view=true
).

Informationen zur Verwendung der API zum entsprechenden Weiterleiten von Anforderungen finden Sie `userContext` [unter Teams SDK](../tabs/how-to/access-teams-context.md#user-context). Weitere Informationen [finden Sie unter Teams Authentifizierungsablauf für Registerkarten](../tabs/how-to/authentication/auth-flow-tab.md). Der Authentifizierungsfluss für Registerkarten ist dem Authentifizierungsfluss für Websites sehr ähnlich. Tabs können OAuth 2.0 also direkt verwenden. Siehe, [Microsoft Identity Platform und OAuth 2.0 Autorisierungscodefluss](/azure/active-directory/develop/v2-oauth2-auth-code-flow).

Die Messagingerweiterung funktioniert wie erwartet, wenn sich ein Benutzer in einer Besprechungsansicht befindet und der Benutzer Nachrichtenerweiterungskarten verfassen kann. AppName in Meeting ist eine QuickInfo, die den App-Namen in der Besprechungs-U-Leiste angibt.

> [!NOTE]
> Verwenden Sie Version 1.7.0 oder höher von [Teams SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true), da die Versionen davor die Seitenleiste nicht unterstützen.

#### <a name="in-meeting-dialog"></a>Dialogfeld "Besprechung"

Das Dialogfeld in der Besprechung kann verwendet werden, um Teilnehmer während der Besprechung zu engagieren und während der Besprechung Informationen oder Feedback zu sammeln. Verwenden Sie die [`NotificationSignal`](/graph/api/resources/notifications-api-overview?view=graph-rest-beta&preserve-view=true) API, um zu signalisieren, dass eine Blasenbenachrichtigung ausgelöst werden muss. Fügen Sie als Teil der Nutzlast der Benachrichtigungsanforderung die URL ein, unter der der anzuzeigende Inhalt gehostet wird.

Das Dialogfeld im Besprechungsdialogfeld darf kein Taskmodul verwenden. Das Aufgabenmodul wird in einem Besprechungschat nicht aufgerufen. Eine externe Ressourcen-URL wird verwendet, um die Inhaltsblase in einer Besprechung anzuzeigen. Sie können die `submitTask` Methode verwenden, um Daten in einem Besprechungschat zu übermitteln.

> [!NOTE]
> * Sie müssen die [submitTask()-Funktion](../task-modules-and-cards/task-modules/task-modules-bots.md#submitting-the-result-of-a-task-module) aufrufen, um sie automatisch zu schließen, nachdem ein Benutzer eine Aktion in der Webansicht ausgeführt hat. Dies ist eine Voraussetzung für die App-Übermittlung. Weitere Informationen finden Sie [unter Teams SDK-Taskmodul](/javascript/api/@microsoft/teams-js/microsoftteams.tasks?view=msteams-client-js-latest#submittask-string---object--string---string---&preserve-view=true).
> * Wenn Ihre App anonyme Benutzer unterstützen soll, muss sich die Nutzlast der ursprünglichen Aufrufanforderung seinerseits auf die `from.id` Anforderungsmetadaten im `from` Objekt und nicht auf die `from.aadObjectId` Anforderungsmetadaten verlassen. `from.id`ist die Benutzer-ID und `from.aadObjectId` die Azure Active Directory-ID (AAD) des Benutzers. Weitere Informationen finden Sie [unter Verwenden von Aufgabenmodulen in Registerkarten](../task-modules-and-cards/task-modules/task-modules-tabs.md) und [Erstellen und Senden des Aufgabenmoduls](../messaging-extensions/how-to/action-commands/create-task-module.md?tabs=dotnet#the-initial-invoke-request).

#### <a name="share-to-stage"></a>Teilen zur Bühne 

> [!NOTE]
> * Diese Funktion ist derzeit nur in der Entwicklervorschau verfügbar.
> * Um diese Funktion nutzen zu können, muss die App ein In-Meeting-Sidepanel unterstützen.


Diese Funktion gibt Entwicklern die Möglichkeit, eine App für die Besprechungsphase freizugeben. Durch die Aktivierung der Freigabe für die Besprechungsphase können Besprechungsteilnehmer in Echtzeit zusammenarbeiten. 

Der erforderliche Kontext befindet sich `meetingStage` im App-Manifest. Voraussetzung dafür ist, den Kontext zu `meetingSidePanel` haben. Dadurch wird die **Share-Taste** im Sidepanel aktiviert, wie in der folgenden Abbildung dargestellt:

  ![share_to_stage_during_meeting Erfahrung](~/assets/images/apps-in-meetings/share_to_stage_during_meeting.png)

Die manifeste Änderung, die erforderlich ist, um diese Funktion zu aktivieren, lautet wie folgt: 

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



### <a name="after-a-meeting"></a>Nach einem Meeting

Die Konfigurationen nach dem Meeting und vor dem Meeting sind gleichwertig.

## <a name="code-sample"></a>Codebeispiel

|Beispielname | Beschreibung | .NET | Node.js |
|----------------|-----------------|--------------|--------------|
| Erweiterbarkeit von Besprechungen | Microsoft Teams Beispiel für die Besprechungserweiterbarkeit zum Übergeben von Token. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-token-app/csharp) | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-token-app/nodejs) |
| Meeting Content Bubble Bot | Microsoft Teams Beispiel für die Erweiterbarkeit von Besprechungen für die Interaktion mit Inhaltsblasenbot in einer Besprechung. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-content-bubble/csharp) |  [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-content-bubble/nodejs)|
| Meeting SidePanel | Microsoft Teams Sitzungserweiterbarkeitsbeispiel für iteracting mit dem Sidepanel in-Meeting. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/meetings-sidepanel/csharp) |

## <a name="see-also"></a>Siehe auch

* [Richtlinien für den Entwurf von Dialogen im Besprechungsdialog](design/designing-apps-in-meetings.md#use-an-in-meeting-dialog)
* [Teams Authentifizierungsablauf für Registerkarten](../tabs/how-to/authentication/auth-flow-tab.md)
