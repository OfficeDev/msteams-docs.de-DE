---
title: Senden proaktiver Nachrichten
description: Beschreibt, wie Proaktive Nachrichten mit Ihrem Microsoft Teams-Bot gesendet werden.
ms.topic: conceptual
ms.author: anclear
ms.localizationpriority: high
Keywords: 'Nachricht senden: Kanal-ID der Benutzer-ID abrufen: Konversations-ID'
ms.openlocfilehash: fc08e9413925f04a0f6e1a01ed7feb6fccd5e8d2
ms.sourcegitcommit: 9e448dcdfd78f4278e9600808228e8158d830ef7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/17/2022
ms.locfileid: "62059772"
---
# <a name="proactive-messages"></a>Proaktive Nachrichten

[!INCLUDE [v4 to v3 pointer](~/includes/v4-to-v3-pointer-bots.md)]

Eine proaktive Nachricht ist jede Nachricht, die von einem Bot gesendet wird, die nicht als Antwort auf eine Anforderung eines Benutzers gesendet wurde. Dies kann Nachrichten enthalten, wie z. B.:

* Willkommensnachrichten
* Benachrichtigungen
* Geplante Nachrichten

Damit Ihr Bot eine proaktive Nachricht an einen Benutzer, einen Gruppenchat oder ein Team senden kann, muss er Zugriff haben, um die Nachricht zu senden. Für einen Gruppenchat oder ein Team muss die App, die Ihren Bot enthält, zuerst an diesem Speicherort installiert werden. Sie können bei Bedarf in einem Team [Ihre App proaktiv mithilfe von Microsoft Graph installieren](#proactively-install-your-app-using-graph) oder eine [App-Richtlinie](/microsoftteams/teams-custom-app-policies-and-settings) verwenden, um Apps an Teams und Benutzer in Ihrem Mandanten zu pushen. Für Benutzer muss Ihre App entweder für den Benutzer installiert sein, oder Ihr Benutzer muss Teil eines Teams sein, in dem Ihre App installiert ist.

Das Senden einer proaktiven Nachricht unterscheidet sich vom Senden einer regulären Nachricht. Es ist keine aktive `turnContext` für eine Antwort vorhanden. Sie müssen die Unterhaltung erstellen, bevor Sie die Nachricht senden. Beispielsweise ein neuer 1:1-Chat oder ein neuer Unterhaltungsthread in einem Kanal. Sie können keinen neuen Gruppenchat oder einen neuen Kanal in einem Team mit proaktivem Messaging erstellen.

**Um eine proaktive Nachricht zu senden**

1. [Rufen Sie die Benutzer-ID, Team-ID oder Kanal-ID ab](#get-the-user-id-team-id-or-channel-id), falls erforderlich.
1. [Erstellen der Unterhaltung](#create-the-conversation), falls erforderlich.
1. [Abrufen der Konversations-ID](#get-the-conversation-id).
1. [Senden der Nachricht](#send-the-message).

Die Codeausschnitte im Abschnitt [Beispiele](#samples) dienen zum Erstellen einer 1:1-Konversation. Links zu vollständigen Arbeitsbeispielen für 1:1-Unterhaltungen und Gruppen oder Kanäle finden Sie unter [Codebeispiel](#code-sample).

Informationen zur effektiven Verwendung proaktiver Nachrichten finden Sie unter [bewährten Methoden für proaktives Messaging](#best-practices-for-proactive-messaging). Für bestimmte Szenarien müssen Sie [Ihre App proaktiv mithilfe von Graph installieren](#proactively-install-your-app-using-graph). Die Codeausschnitte im Abschnitt [Beispiele](#samples) dienen zum Erstellen einer 1:1-Konversation. Vollständige Arbeitsbeispiele für 1:1-Unterhaltungen und Gruppen oder Kanäle finden Sie unter [Codebeispiel](#code-sample).

## <a name="get-the-user-id-team-id-or-channel-id"></a>Abrufen der Benutzer-ID, Team-ID oder Kanal-ID

Um eine neue Unterhaltung oder einen neuen Konversationsthread in einem Kanal zu erstellen, müssen Sie über die richtige ID verfügen. Sie können diese ID mit einer der folgenden Methoden empfangen oder abrufen:

* Wenn Ihre App in einem bestimmten Kontext installiert ist, erhalten Sie eine [`onMembersAdded` Aktivität](~/bots/how-to/conversations/subscribe-to-conversation-events.md).
* Wenn ein neuer Benutzer zu einem Kontext hinzugefügt wird, in dem Ihre App installiert ist, erhalten Sie eine [`onMembersAdded` Aktivität](~/bots/how-to/conversations/subscribe-to-conversation-events.md).
* Sie können in einem Team, in dem Ihre App installiert ist, die [Liste der Kanäle](~/bots/how-to/get-teams-context.md) abrufen.
* Sie können die [Liste der Mitglieder](~/bots/how-to/get-teams-context.md) eines Teams abrufen, in dem Ihre App installiert ist.
* Jede Aktivität, die Ihr Bot empfängt, muss die erforderlichen Informationen enthalten.

Unabhängig davon, wie Sie die Informationen erhalten, müssen Sie die `tenantId` und entweder die `userId` oder `channelId` speichern, um eine neue Unterhaltung zu erstellen. Sie können auch die `teamId` verwenden, um einen neuen Unterhaltungsthread im allgemeinen oder Standardkanal eines Teams zu erstellen.

Die `userId` ist für Ihre Bot-ID und einen bestimmten Benutzer eindeutig. Sie können die `userId` zwischen Bots nicht wiederverwenden. Die `channelId` ist global. Ihr Bot muss jedoch im Team installiert sein, bevor Sie eine proaktive Nachricht an einen Kanal senden können.

Nachdem Sie über die Benutzer- oder Kanalinformationen verfügen, müssen Sie die Unterhaltung erstellen.

## <a name="create-the-conversation"></a>Erstellen der Unterhaltung

Sie müssen die Konversation erstellen, wenn sie nicht vorhanden ist oder Sie die `conversationId` nicht kennen. Sie dürfen die Konversation nur einmal erstellen und den `conversationId` Wert oder `conversationReference` Objekt speichern.

Nachdem die Unterhaltung erstellt wurde, müssen Sie die Konversations-ID abrufen.

## <a name="get-the-conversation-id"></a>Abrufen der Konversations-ID

Verwenden Sie entweder das `conversationReference`-Objekt oder `conversationId` und `tenantId`, um die Nachricht zu senden. Sie können diese ID abrufen, indem Sie entweder die Konversation erstellen oder sie aus jeder Aktivität speichern, die aus diesem Kontext an Sie gesendet wird. Speichern Sie diese ID als Referenz.

Nachdem Sie die entsprechenden Adressinformationen erhalten haben, können Sie Ihre Nachricht senden.

## <a name="send-the-message"></a>Senden der Nachricht

Nachdem Sie nun über die richtigen Adressinformationen verfügen, können Sie Ihre Nachricht senden. Wenn Sie das SDK verwenden, müssen Sie die `continueConversation`-Methode sowie die `conversationId` und `tenantId` verwenden, um einen direkten API-Aufruf zu tätigen. Sie müssen die `conversationParameters` richtig festlegen, um Ihre Nachricht erfolgreich zu senden. Sehen Sie sich den Abschnitt [Beispiele](#samples) an, oder verwenden Sie eines der Beispiele, die im Abschnitt [Codebeispiel](#code-sample) aufgeführt sind.

Nachdem Sie die proaktive Nachricht gesendet haben, müssen Sie diese bewährten Methoden befolgen und proaktive Nachrichten senden, um einen besseren Informationsaustausch zwischen Benutzern und dem Bot zu ermöglichen.

## <a name="best-practices-for-proactive-messaging"></a>Bewährte Methoden für proaktives Messaging

Das Senden proaktiver Nachrichten an die Benutzer ist eine effektive Möglichkeit, mit Ihren Benutzern zu kommunizieren. Aus Sicht des Benutzers wird die Nachricht jedoch unaufgefordert angezeigt. Wenn es eine Willkommensnachricht gibt, ist dies das erste Mal, dass sie mit Ihrer App interagieren. Es ist wichtig, diese Funktion zu verwenden und dem Benutzer die vollständigen Informationen bereitzustellen, damit sie den Zweck dieser Nachricht verstehen.

### <a name="welcome-messages"></a>Willkommensnachrichten

Wenn proaktives Messaging verwendet wird, um eine Willkommensnachricht an einen Benutzer zu senden, gibt es keinen Kontext dafür, warum die Benutzer die Nachricht erhalten. Dies ist auch das erste Mal, dass Benutzer mit Ihrer App interagieren. Es ist eine Gelegenheit, einen guten ersten Eindruck zu hinterlassen. Die besten Willkommensnachrichten müssen Folgendes enthalten:

* Warum ein Benutzer die Nachricht empfängt: Es muss für den Benutzer sehr klar sein, warum er die Nachricht empfängt. Wenn Ihr Bot in einem Kanal installiert wurde und Sie allen Benutzern eine Willkommensnachricht gesendet haben, teilen Sie ihnen mit, in welchem Kanal er installiert wurde und wer ihn installiert hat.
* Was bieten Sie: Benutzer müssen in der Lage sein, zu identifizieren, was sie mit Ihrer App tun können und welchen Wert Sie ihnen bieten können.
* Was sollten sie als Nächstes tun: Laden Sie Benutzer ein, einen Befehl auszuprobieren oder mit Ihrer App zu interagieren.
Schlechte Willkommensnachricht können dazu führen, dass die Benutzer Ihren Bot blockieren. Schreiben Sie klare und deutliche Willkommensnachrichten. Probieren Sie verschiedene Versionen der Willkommensnachrichten, wenn sie nicht den gewünschten Effekt haben.

### <a name="notification-messages"></a>Benachrichtigungen

Um Benachrichtigungen mit proaktivem Messaging zu senden, stellen Sie sicher, dass Ihre Benutzer einen eindeutigen Pfad haben, um allgemeine Aktionen basierend auf Ihrer Benachrichtigung auszuführen. Stellen Sie sicher, dass Benutzer über ein klares Verständnis dafür verfügen, warum sie eine Benachrichtigung erhalten haben. Gute Benachrichtigungen umfassen im Allgemeinen Folgendes:

* Was passiert ist: Ein eindeutiger Hinweis darauf, was die Benachrichtigung verursacht hat.
* Was war das Ergebnis: Es muss klar sein, welches Element aktualisiert wird, um die Benachrichtigung zu erhalten.
* Wer oder was es ausgelöst hat: Wer oder was eine Aktion ausgeführt hat, die dazu geführt hat, dass die Benachrichtigung gesendet wurde.
* Was können Benutzer als Reaktion tun: Erleichtern Sie Es Ihren Benutzern, Aktionen basierend auf Ihren Benachrichtigungen durchzuführen.
* Wie können Benutzer sich abmelden? Sie müssen einen Pfad angeben, über den Benutzer zusätzliche Benachrichtigungen deaktivieren können.

Um Nachrichten an eine große Gruppe von Benutzern zu senden, z. B. an Ihre Organisation, installieren Sie Ihre App proaktiv mithilfe von Graph.

### <a name="scheduled-messages"></a>Geplante Nachrichten

Wenn Sie proaktives Messaging verwenden, um geplante Nachrichten an Benutzer zu senden, überprüfen Sie, ob Ihre Zeitzone auf ihre Zeitzone aktualisiert wurde. Dadurch wird sichergestellt, dass die Nachrichten zum entsprechenden Zeitpunkt an die Benutzer übermittelt werden. Geplante Nachrichten umfassen in der Regel Folgendes:

* Warum erhält der Benutzer die Nachricht: Erleichtern Sie es Ihren Benutzern, den Grund zu verstehen, aus dem sie die Nachricht erhalten.
* Was der Benutzer als Nächstes tun kann: Benutzer können die erforderliche Aktion basierend auf dem Nachrichteninhalt ausführen.

## <a name="proactively-install-your-app-using-graph"></a>Proaktives Installieren Ihrer App mit Graph

> [!Note]
> Die proaktive Installation von Apps mit Graph befindet sich derzeit in der Betaphase.

Proaktive Nachricht an Benutzer senden, die Ihre App zuvor nicht installiert oder mit Ihr interagiert haben. Sie sollten beispielsweise den [Unternehmens-Communicator](~/samples/app-templates.md#company-communicator) verwenden, um Nachrichten an Ihre gesamte Organisation zu senden. In diesem Fall können Sie die Graph-API verwenden, um Ihre App proaktiv für Ihre Benutzer zu installieren. Speichern Sie die erforderlichen Werte aus dem `conversationUpdate` Ereignis zwischen, das Ihre App bei der Installation empfängt.

Sie können nur Apps installieren, die sich im App-Katalog Ihrer Organisation oder im Teams-App Store befinden.

Weitere Informationen finden Sie unter [Installieren von Apps für Benutzer](/graph/api/userteamwork-post-installedapps) in der Graph-Dokumentation und [proaktive Botinstallation und -messaging in Teams mit Graph](../../../graph-api/proactive-bots-and-messages/graph-proactive-bots-and-messages.md). Es gibt auch ein [Microsoft .NET Frameworkbeispiel](https://github.com/microsoftgraph/contoso-airlines-teams-sample/blob/283523d45f5ce416111dfc34b8e49728b5012739/project/Models/GraphService.cs#L176) auf der GitHub-Plattform.

## <a name="samples"></a>Beispiele

Der folgende Code zeigt, wie Proaktive Nachrichten gesendet werden:

# <a name="c"></a>[C#](#tab/dotnet)

```csharp
[Route("api/notify")]
[ApiController]
public class NotifyController : ControllerBase
{
    private readonly IBotFrameworkHttpAdapter _adapter;
    private readonly string _appId;
    private readonly ConcurrentDictionary<string, ConversationReference> _conversationReferences;

    public NotifyController(IBotFrameworkHttpAdapter adapter, IConfiguration configuration, ConcurrentDictionary<string, ConversationReference> conversationReferences)
    {
        _adapter = adapter;
        _conversationReferences = conversationReferences;
        _appId = configuration["MicrosoftAppId"] ?? string.Empty;
    }

    public async Task<IActionResult> Get()
    {
        foreach (var conversationReference in _conversationReferences.Values)
        {
            await ((BotAdapter)_adapter).ContinueConversationAsync(_appId, conversationReference, BotCallback, default(CancellationToken));
        }
        
        // Let the caller know proactive messages have been sent
        return new ContentResult()
        {
            Content = "<html><body><h1>Proactive messages have been sent.</h1></body></html>",
            ContentType = "text/html",
            StatusCode = (int)HttpStatusCode.OK,
        };
    }

    private async Task BotCallback(ITurnContext turnContext, CancellationToken cancellationToken)
    {
        // If you encounter permission-related errors when sending this message, see
        // https://aka.ms/BotTrustServiceUrl
        await turnContext.SendActivityAsync("proactive hello");
    }
}
```

# <a name="typescript"></a>[TypeScript](#tab/typescript)

```javascript

async messageAllMembersAsync(context) {
    const members = await this.getPagedMembers(context);

    members.forEach(async (teamMember) => {
        const message = MessageFactory.text('Hello ${ teamMember.givenName } ${ teamMember.surname }. I\'m a Teams conversation bot.');

        var ref = TurnContext.getConversationReference(context.activity);
        ref.user = teamMember;

        await context.adapter.createConversation(ref,
            async (t1) => {
                const ref2 = TurnContext.getConversationReference(t1.activity);
                await t1.adapter.continueConversation(ref2, async (t2) => {
                    await t2.sendActivity(message);
                });
            });
    });

    await context.sendActivity(MessageFactory.text('All messages have been sent.'));
}
```

# <a name="python"></a>[Python](#tab/python)

```python
async def _message_all_members(self, turn_context: TurnContext):
    team_members = await self._get_paged_members(turn_context)

    for member in team_members:
        conversation_reference = TurnContext.get_conversation_reference(
            turn_context.activity
        )

        conversation_parameters = ConversationParameters(
            is_group=False,
            bot=turn_context.activity.recipient,
            members=[member],
            tenant_id=turn_context.activity.conversation.tenant_id,
        )

        async def get_ref(tc1):
            conversation_reference_inner = TurnContext.get_conversation_reference(
                tc1.activity
            )
            return await tc1.adapter.continue_conversation(
                conversation_reference_inner, send_message, self._app_id
            )

        async def send_message(tc2: TurnContext):
            return await tc2.send_activity(
                f"Hello {member.name}. I'm a Teams conversation bot."
            )

        await turn_context.adapter.create_conversation(
            conversation_reference, get_ref, conversation_parameters
        )

    await turn_context.send_activity(
        MessageFactory.text("All messages have been sent")
    )

```

# <a name="json"></a>[JSON](#tab/json)

```json
POST /v3/conversations
{
  "bot": {
    "id": "28:10j12ou0d812-2o1098-c1mjojzldxcj-1098028n ",
    "name": "The Bot"
  },
  "members": [
    {
      "id": "29:012d20j1cjo20211"
    }
  ],
  "channelData": {
    "tenant": {
      "id": "197231joe-1209j01821-012kdjoj"
    }
  }
}
```

Sie müssen die Benutzer-ID und die Mandanten-ID angeben. Wenn der Aufruf erfolgreich ist, gibt die API das folgende Antwortobjekt zurück:

```json
{
  "id":"a:1qhNLqpUtmuI6U35gzjsJn7uRnCkW8NiZALHfN8AMxdbprS1uta2aT-jytfIlsZR3UZeg3TsIONNInBHsdjzj3PtfHuhkxxvS1jZZ61UAbw8fIdXcNSJyTJm7YvHFOgxo"
}
```

---

> [!NOTE]
> Derzeit können Bots keinen Gruppenchat über Bot-APIs oder Graph erstellen. `createConversation` ist nur für 1:1-Chats verfügbar.

## <a name="code-sample"></a>Codebeispiel

Die folgende Tabelle enthält ein einfaches Codebeispiel, das den grundlegenden Konversationsfluss in eine Teams-Anwendung einbezieht und wie Sie einen neuen Konversationsthread in einem Kanal in Teams erstellen:

| **Beispielname** | **Beschreibung** | **.NET** | **Node.js** | **Python** |
|---------------|--------------|--------|-------------|--------|
| Grundlagen zu Teams-Unterhaltungen  | Veranschaulicht die Grundlagen von Unterhaltungen in Teams, einschließlich des Sendens proaktiver 1:1-Nachrichten.| [View](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/csharp_dotnetcore/57.teams-conversation-bot) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/57.teams-conversation-bot) | [View](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/python/57.teams-conversation-bot) |
| Starten eines neuen Threads in einem Kanal | Veranschaulicht das Erstellen eines neuen Threads in einem Kanal. | [View](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/csharp_dotnetcore/58.teams-start-new-thread-in-channel) | [View](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/javascript_nodejs/58.teams-start-new-thread-in-channel) | [View](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/python/58.teams-start-thread-in-channel) |
| Proaktive Installation der App und Senden proaktiver Benachrichtigungen | Dieses Beispiel zeigt, wie Sie die proaktive Installation der App für Benutzer verwenden und proaktive Benachrichtigungen senden können, indem Sie Microsoft Graph APIs aufrufen. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/graph-proactive-installation/csharp) | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/graph-proactive-installation/nodejs) | |

### <a name="additional-code-sample"></a>Zusätzliches Codebeispiel

> [!div class="nextstepaction"]
> [Codebeispiele für proaktives Messaging in Teams](/samples/officedev/msteams-samples-proactive-messaging/msteams-samples-proactive-messaging/)

## <a name="step-by-step-guide"></a>Schrittweise Anleitung

Befolgen Sie die [schrittweisen Anleitung](../../../sbs-send-proactive.yml), die Ihnen hilft, eine proaktive Nachricht von einem Bot zu senden.

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Formatieren von Bot-Nachrichten](~/bots/how-to/format-your-bot-messages.md)

## <a name="see-also"></a>Siehe auch

* [**Codebeispiele für proaktives Messaging in Teams**](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-proactive-messaging/csharp)
* [Kanal- und Gruppenchatunterhaltungen mit einem Bot](~/bots/how-to/conversations/channel-and-group-conversations.md)
* [Auf die Aktion zum Absenden des Aufgabenmoduls reagieren](~/messaging-extensions/how-to/action-commands/respond-to-task-module-submit.md)
