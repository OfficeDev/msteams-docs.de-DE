---
title: proaktive Nachrichten senden
description: beschreibt, wie Sie proaktive Nachrichten mit Ihrem Microsoft Teams-Bot senden.
ms.topic: overview
ms.author: anclear
Keywords: Senden einer Nachricht erhalten Benutzer-ID Kanal-ID Unterhaltungs-ID
ms.openlocfilehash: 2d7ff10469a181bb06fda5029c8f6b2725b0402d
ms.sourcegitcommit: 7db6eabe3ef128ac7f14b32d07e9e86c995d187f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/04/2021
ms.locfileid: "50103605"
---
# <a name="send-proactive-messages"></a>Versenden proaktiver Nachrichten

[!INCLUDE [v4 to v3 pointer](~/includes/v4-to-v3-pointer-bots.md)]

Eine proaktive Nachricht ist jede Nachricht, die von einem Bot gesendet wird, die nicht direkt auf eine Anforderung eines Benutzers reagiert. Dies kann Nachrichten wie die folgenden umfassen:

* Willkommensnachrichten
* Benachrichtigungen
* Geplante Nachrichten

Damit Ihr Bot eine proaktive Nachricht senden kann, muss er Zugriff auf den Benutzer, Gruppenchat oder das Team haben, an den Sie die Nachricht senden möchten. Für einen Gruppenchat oder ein Gruppenteam bedeutet dies, dass die App, die Ihren Bot enthält, zuerst an diesem Speicherort installiert werden muss. Sie können [Ihre App](#proactively-install-your-app-using-graph) proaktiv mithilfe von Graph in [](/microsoftteams/teams-custom-app-policies-and-settings) einem Team installieren, falls erforderlich, oder eine App-Richtlinie verwenden, um Apps an Teams und Benutzer in Ihrem Mandanten zu pushen. Für Benutzer muss Ihre App entweder für den Benutzer installiert werden, oder Ihr Benutzer muss Teil eines Teams sein, in dem Die App installiert ist.

Das Senden einer proaktiven Nachricht ist anders als das Senden einer regulären Nachricht. In that, there is no active `turnContext` to use for a reply. Möglicherweise müssen Sie auch die Unterhaltung erstellen, bevor Sie die Nachricht senden. Beispielsweise ein neuer 1:1-Chat oder ein neuer Unterhaltungsthread in einem Kanal. Sie können keinen neuen Gruppenchat oder einen neuen Kanal in einem Team mit proaktivem Messaging erstellen.

Auf hoher Ebene müssen Sie die folgenden Schritte ausführen, um eine proaktive Nachricht zu senden:

1. [Erhalten Sie die Benutzer-ID oder die Team-/Kanal-ID](#get-the-user-id-or-teamchannel-id) (falls erforderlich).
1. [Erstellen Sie den Unterhaltungs- oder Unterhaltungsthread](#create-the-conversation) (falls erforderlich).
1. [Erhalten Sie die Unterhaltungs-ID.](#get-the-conversation-id)
1. [Senden Sie die Nachricht](#send-the-message).

Die Codeausschnitte im [Beispielabschnitt](#examples) sind zum Erstellen einer 1:1-Unterhaltung. Links zum Vervollständigen von Arbeitsbeispielen für 1:1-Unterhaltungen und Gruppen oder Kanäle finden Sie in [den Codebeispielen.](#code-samples)

## <a name="get-the-user-id-or-teamchannel-id"></a>Benutzer-ID oder Team-/Kanal-ID erhalten

Um eine neue Unterhaltung oder einen neuen Unterhaltungsthread in einem Kanal zu erstellen, benötigen Sie die richtige ID. Sie können diese ID auf verschiedene Arten empfangen oder abrufen:

1. Wenn Ihre App in einem bestimmten Kontext installiert ist, erhalten Sie eine [ `onMembersAdded` Aktivität.](~/bots/how-to/conversations/subscribe-to-conversation-events.md)
1. Wenn ein neuer Benutzer zu einem Kontext hinzugefügt wird, in dem Ihre App installiert ist, erhalten Sie eine [ `onMembersAdded` Aktivität.](~/bots/how-to/conversations/subscribe-to-conversation-events.md)
1. Sie können die Liste [der Kanäle](~/bots/how-to/get-teams-context.md) in einem Team abrufen, in dem Ihre App installiert ist.
1. Sie können die Liste [der Mitglieder eines Teams](~/bots/how-to/get-teams-context.md) abrufen, in dem Ihre App installiert ist.
1. Jede Aktivität, die Ihr Bot empfängt, muss die erforderlichen Informationen enthalten.

Unabhängig davon, wie Sie die Informationen erhalten, müssen Sie die und entweder die oder eine `tenantId` `userId` neue Unterhaltung `channelId` speichern. Sie können den auch `teamId` verwenden, um einen neuen Unterhaltungsthread im allgemeinen oder Standardkanal eines Teams zu erstellen.

Die ist für Ihre Bot-ID und einen bestimmten Benutzer eindeutig. Sie können sie nicht zwischen `userId` Bots erneut verwenden. Der Bot muss jedoch global im Team installiert sein, bevor Sie eine proaktive Nachricht an `channelId` einen Kanal senden können.

## <a name="create-the-conversation"></a>Erstellen der Unterhaltung

Nachdem Sie über die Benutzer- oder Kanalinformationen verfügen, müssen Sie die Unterhaltung erstellen, wenn sie noch nicht vorhanden ist oder Sie die nicht `conversationId` kennen. Sie müssen die Unterhaltung nur einmal erstellen und sicherstellen, dass Sie den Wert oder das Objekt speichern, `conversationId` der zukünftig verwendet werden `conversationReference` soll.

## <a name="get-the-conversation-id"></a>Unterhaltungs-ID erhalten

Nachdem die Unterhaltung erstellt wurde, verwenden Sie entweder das `conversationReference` Objekt oder und senden Sie die `conversationId` `tenantId` Nachricht. Sie können diese ID erhalten, indem Sie entweder die Unterhaltung erstellen oder sie aus jeder Aktivität speichern, die aus diesem Kontext an Sie gesendet wird. Stellen Sie sicher, dass Sie diese ID speichern.

## <a name="send-the-message"></a>Senden der Nachricht

Nachdem Sie nun über die richtigen Adressinformationen verfügen, können Sie Ihre Nachricht senden. Wenn Sie das SDK verwenden, verwenden Sie dazu die Methode und den direkten `continueConversation` `conversationId` `tenantId` API-Aufruf. Sie müssen dies `conversationParameters` ordnungsgemäß festlegen, damit die Nachricht erfolgreich gesendet werden kann. Weitere Informationen [finden Sie im](#examples) Abschnitt "Beispiele", oder verwenden Sie eines der Beispiele, die im Abschnitt mit den [Codebeispielen aufgeführt](#code-samples) sind.

## <a name="best-practices-for-proactive-messaging"></a>Bewährte Methoden für proaktives Messaging

Das Senden proaktiver Nachrichten an Benutzer ist eine sehr effektive Möglichkeit, mit Ihren Benutzern zu kommunizieren. Aus ihrer Sicht kann diese Nachricht jedoch völlig unprompt angezeigt werden, und im Falle von Willkommensnachrichten ist es das erste Mal, dass sie mit Ihrer App interagiert haben. Daher ist es sehr wichtig, diese Funktion sparsam zu verwenden, Keine Spamnachrichten für Ihre Benutzer zu senden und genügend Informationen bereitzustellen, damit Benutzer verstehen können, warum sie nachrichteniert werden.

### <a name="welcome-messages"></a>Willkommensnachrichten

Wenn Sie proaktives Messaging verwenden, um eine Willkommensnachricht an einen Benutzer zu senden, müssen Sie bedenken, dass für die meisten Empfänger der Nachricht kein Kontext dafür besteht, warum sie empfangen werden. Dies ist auch das erste Mal, dass sie mit Ihrer App interagiert haben. Es ist Ihre Gelegenheit, einen guten ersten Eindruck zu erzeugen. Die besten Willkommensnachrichten müssen Folgendes enthalten:

* **Warum ein Benutzer die Nachricht empfängt.** Es muss dem Benutzer klar sein, warum er die Nachricht empfängt. Wenn Ihr Bot in einem Kanal installiert wurde und Sie eine Willkommensnachricht an alle Benutzer gesendet haben, teilen Sie ihnen mit, in welchem Kanal er installiert wurde und wer ihn möglicherweise installiert hat.
* **Was bieten Sie an?** Was können sie mit Ihrer App tun? Welchen Wert können Sie ihnen mitbringen?
* **Was sollten sie als Nächstes tun?** Laden Sie sie ein, einen Befehl auszuprobieren oder auf eine bestimmte Weise mit Ihrer App zu interagieren.

Denken Sie daran, dass schlechte Willkommensnachrichten dazu führen können, dass Benutzer Ihren Bot blockieren. Verbringen Sie viel Zeit mit dem Erstellen Ihrer Willkommensnachrichten, und iterieren Sie sie, wenn sie nicht den gewünschten Effekt haben.

### <a name="notification-messages"></a>Benachrichtigungen

Wenn Sie proaktives Messaging zum Senden von Benachrichtigungen verwenden, müssen Sie sicherstellen, dass Ihre Benutzer über einen klaren Pfad verfügen, um allgemeine Aktionen basierend auf Ihrer Benachrichtigung zu ergreifen und klar zu verstehen, warum die Benachrichtigung aufgetreten ist. Gute Benachrichtigungen umfassen im Allgemeinen Folgendes:

* **Was ist passiert.** Ein eindeutiger Hinweis darauf, was die Benachrichtigung verursacht hat.
* **Was war das Ergebnis?** Es muss klar sein, welches Element oder welche Elemente aktualisiert wurden, um die Benachrichtigung zu verursachen.
* **Wer/was hat es ausgelöst?** Wer oder was eine Aktion ausgelöst hat, die dazu führte, dass die Benachrichtigung gesendet wurde.
* **Was können Benutzer als Reaktion tun?** Machen Sie es Ihren Benutzern einfach, Aktionen basierend auf Ihren Benachrichtigungen zu ergreifen.
* **Wie können Benutzer abmelden?** Sie müssen einen Pfad für Benutzer bereitstellen, um zusätzliche Benachrichtigungen abmelden zu können.

## <a name="proactively-install-your-app-using-graph"></a>Proaktives Installieren Ihrer App mithilfe von Graph

> [!Note]
> Die proaktive Installation von Apps mit Microsoft Graph befindet sich derzeit in der Betaversion.

Gelegentlich kann es erforderlich sein, Benutzer, die ihre App zuvor nicht installiert oder interagiert haben, proaktiv zu senden. Sie möchten z. B. den Unternehmens [communicator](~/samples/app-templates.md#company-communicator) verwenden, um Nachrichten an Die gesamte Organisation zu senden. Für dieses Szenario können Sie die Graph-API verwenden, um Ihre App proaktiv für Ihre Benutzer zu installieren und dann die erforderlichen Werte aus dem Ereignis zwischenspeichern, das Ihre App bei der Installation `conversationUpdate` empfängt.

Sie können nur Apps installieren, die sich in Ihrem Organisations-App-Katalog oder im Teams-App-Store befinden.

Weitere Informationen finden Sie unter ["Installieren von Apps für Benutzer"](/graph/api/userteamwork-post-installedapps) in der Graph-Dokumentation sowie in der proaktiven Botinstallation und [-messaging in Teams mit Microsoft Graph.](../../../graph-api/proactive-bots-and-messages/graph-proactive-bots-and-messages.md) Es gibt auch ein [Microsoft .NET -Framework-Beispiel](https://github.com/microsoftgraph/contoso-airlines-teams-sample/blob/283523d45f5ce416111dfc34b8e49728b5012739/project/Models/GraphService.cs#L176) auf der GitHub-Plattform.

## <a name="examples"></a>Beispiele

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

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

# <a name="typescriptnodejs"></a>[TypeScript/Node.js](#tab/typescript)

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

# <a name="json"></a>[Json](#tab/json)

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

Sie müssen die Benutzer-ID und die Mandanten-ID liefern. Wenn der Aufruf erfolgreich ist, wird die API mit dem folgenden Antwortobjekt zurückgegeben.

```json
{
  "id":"a:1qhNLqpUtmuI6U35gzjsJn7uRnCkW8NiZALHfN8AMxdbprS1uta2aT-jytfIlsZR3UZeg3TsIONNInBHsdjzj3PtfHuhkxxvS1jZZ61UAbw8fIdXcNSJyTJm7YvHFOgxo"
}
```

---

## <a name="code-samples"></a>Codebeispiele

Die offiziellen Beispiele für proaktive Nachrichten sind wie folgt:

| Beispielname           | Beschreibung                                                                      | .NET    | JavaScript   | Python  |
|:----------------------|:---------------------------------------------------------------------------------|:--------|:-------------|:--------|
|Grundlegendes zu Unterhaltungen in Teams  | Veranschaulicht die Grundlagen von Unterhaltungen in Teams, einschließlich des Sendens proaktiver 1:1-Nachrichten.|[.NET &nbsp; Core](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/csharp_dotnetcore/57.teams-conversation-bot)|[JavaScript](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/57.teams-conversation-bot) | [Python](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/python/57.teams-conversation-bot)|
|Starten eines neuen Threads in einem Kanal     | Veranschaulicht das Erstellen eines neuen Threads in einem Kanal. |[.NET &nbsp; Core](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/csharp_dotnetcore/58.teams-start-new-thread-in-channel)|[JavaScript](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/javascript_nodejs/58.teams-start-new-thread-in-channel)|[Python](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/python/58.teams-start-thread-in-channel) |

## <a name="view-additional-code-samples"></a>Anzeigen zusätzlicher Codebeispiele
>
> [!div class="nextstepaction"]
> [**Proaktive Messagingcodebeispiele für Teams**](/samples/officedev/msteams-samples-proactive-messaging/msteams-samples-proactive-messaging/)
>
