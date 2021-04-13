---
title: Senden proaktiver Nachrichten
description: beschreibt, wie Sie proaktive Nachrichten mit Ihrem Microsoft Teams-Bot senden.
ms.topic: overview
ms.author: anclear
Keywords: 'Senden einer Nachricht: Benutzer-ID-Kanal-ID-Unterhaltungs-ID erhalten'
ms.openlocfilehash: 7da470eaba6ae9ecb82c9a7ba04d69b2f196a9d7
ms.sourcegitcommit: 9404c2e3a30887b9e17e0c89b12dd26fd9b8033e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2021
ms.locfileid: "51654293"
---
# <a name="send-proactive-messages"></a>Versenden proaktiver Nachrichten

[!INCLUDE [v4 to v3 pointer](~/includes/v4-to-v3-pointer-bots.md)]

Eine proaktive Nachricht ist jede Nachricht, die von einem Bot gesendet wird, die nicht direkt auf eine Anforderung eines Benutzers reagiert. Dies kann Nachrichten wie:

* Willkommensnachrichten
* Benachrichtigungen
* Geplante Nachrichten

Damit Ihr Bot eine proaktive Nachricht senden kann, muss er Zugriff auf den Benutzer, den Gruppenchat oder das Team haben, an den Sie die Nachricht senden möchten. Für einen Gruppenchat oder ein Team bedeutet dies, dass die App, die Ihren Bot enthält, zuerst an diesem Speicherort installiert werden muss. Sie können [Ihre App proaktiv](#proactively-install-your-app-using-graph) mithilfe von Graph in [](/microsoftteams/teams-custom-app-policies-and-settings) einem Team installieren, falls erforderlich, oder eine App-Richtlinie verwenden, um Apps an Teams und Benutzer in Ihrem Mandanten zu pushen. Für Benutzer muss Ihre App entweder für den Benutzer installiert sein, oder Ihr Benutzer muss Teil eines Teams sein, in dem Ihre App installiert ist.

Das Senden einer proaktiven Nachricht ist anders als das Senden einer regulären Nachricht. In diesem Bereich ist keine aktive `turnContext` Für eine Antwort zu verwenden. Möglicherweise müssen Sie auch die Unterhaltung erstellen, bevor Sie die Nachricht senden. Beispielsweise ein neuer 1:1-Chat oder ein neuer Unterhaltungsthread in einem Kanal. Sie können keinen neuen Gruppenchat oder einen neuen Kanal in einem Team mit proaktivem Messaging erstellen.

Auf einer hohen Ebene sind die Schritte, die Sie ausführen müssen, um eine proaktive Nachricht zu senden:

1. [Die Benutzer-ID oder die Team-/Kanal-ID](#get-the-user-id-or-teamchannel-id) (falls erforderlich) erhalten.
1. [Erstellen Sie den Unterhaltungs- oder Unterhaltungsthread](#create-the-conversation) (falls erforderlich).
1. [Die Unterhaltungs-ID erhalten.](#get-the-conversation-id)
1. [Senden Sie die Nachricht](#send-the-message).

Die Codeausschnitte im Abschnitt [Beispiele](#examples) sind zum Erstellen einer 1:1-Unterhaltung. Links zum Abschließen von Arbeitsbeispielen für 1:1-Unterhaltungen und Gruppen oder Kanäle finden Sie unter [Codebeispiele](#code-samples).

## <a name="get-the-user-id-or-teamchannel-id"></a>Benutzer-ID oder Team-/Kanal-ID erhalten

Zum Erstellen einer neuen Unterhaltung oder eines neuen Unterhaltungsthreads in einem Kanal benötigen Sie die richtige ID. Sie können diese ID auf verschiedene Weise empfangen oder abrufen:

1. Wenn Ihre App in einem bestimmten Kontext installiert ist, erhalten Sie eine [ `onMembersAdded` Aktivität](~/bots/how-to/conversations/subscribe-to-conversation-events.md).
1. Wenn einem Kontext, in dem Ihre App installiert ist, ein neuer Benutzer hinzugefügt wird, erhalten Sie eine [ `onMembersAdded` Aktivität](~/bots/how-to/conversations/subscribe-to-conversation-events.md).
1. Sie können die Liste [der Kanäle](~/bots/how-to/get-teams-context.md) in einem Team abrufen, in dem Ihre App installiert ist.
1. Sie können die Liste [der Mitglieder eines Teams abrufen,](~/bots/how-to/get-teams-context.md) in dem Ihre App installiert ist.
1. Jede Aktivität, die Ihr Bot empfängt, muss die erforderlichen Informationen enthalten.

Unabhängig davon, wie Sie die Informationen erhalten, müssen Sie die und entweder die oder speichern, um `tenantId` eine neue Unterhaltung zu `userId` `channelId` erstellen. Sie können auch den `teamId` verwenden, um einen neuen Unterhaltungsthread im allgemeinen oder Standardkanal eines Teams zu erstellen.

Die ist für Ihre Bot-ID und einen bestimmten Benutzer eindeutig. Sie können sie nicht zwischen `userId` Bots erneut verwenden. The `channelId` is global, however, your bot must be installed in the team before you can send a proactive message to a channel.

## <a name="create-the-conversation"></a>Erstellen der Unterhaltung

Nachdem Sie über die Benutzer- oder Kanalinformationen verfügen, müssen Sie die Unterhaltung erstellen, wenn sie noch nicht vorhanden ist oder Sie die `conversationId` nicht kennen. Sie müssen die Unterhaltung nur einmal erstellen und sicherstellen, dass Sie den Wert oder das Objekt speichern, das `conversationId` in Zukunft verwendet werden `conversationReference` soll.

## <a name="get-the-conversation-id"></a>Die Unterhaltungs-ID erhalten

Nachdem die Unterhaltung erstellt wurde, verwenden Sie entweder das `conversationReference` Objekt oder und um die Nachricht zu `conversationId` `tenantId` senden. Sie können diese ID erhalten, indem Sie die Unterhaltung erstellen oder aus allen Aktivitäten speichern, die aus diesem Kontext an Sie gesendet werden. Stellen Sie sicher, dass Sie diese ID speichern.

## <a name="send-the-message"></a>Senden der Nachricht

Nachdem Sie nun über die richtigen Adressinformationen verfügen, können Sie Ihre Nachricht senden. Wenn Sie das SDK verwenden, verwenden Sie dazu die -Methode und und einen direkten `continueConversation` `conversationId` `tenantId` API-Aufruf. Sie müssen die korrekt `conversationParameters` festlegen, damit Ihre Nachricht erfolgreich gesendet wird. Sehen Sie [sich den Abschnitt](#examples) Beispiele an, oder verwenden Sie eines der Beispiele, die im Abschnitt [Codebeispiele aufgeführt](#code-samples) sind.

## <a name="best-practices-for-proactive-messaging"></a>Bewährte Methoden für proaktives Messaging

Das Senden proaktiver Nachrichten an Benutzer ist eine sehr effektive Möglichkeit, mit Ihren Benutzern zu kommunizieren. Aus ihrer Sicht kann diese Nachricht jedoch völlig unprompted angezeigt werden, und im Falle von Willkommensnachrichten ist es das erste Mal, dass sie mit Ihrer App interagiert haben. Daher ist es sehr wichtig, diese Funktionalität sparsam zu verwenden, Ihre Benutzer nicht zu spamen und genügend Informationen bereitzustellen, damit Benutzer verstehen können, warum sie gesendet werden.

### <a name="welcome-messages"></a>Willkommensnachrichten

Wenn Sie proaktives Messaging verwenden, um eine Willkommensnachricht an einen Benutzer zu senden, müssen Sie bedenken, dass für die meisten Empfänger der Nachricht kein Kontext dafür besteht, warum sie sie empfängt. Dies ist auch das erste Mal, dass sie mit Ihrer App interagieren. Es ist Ihre Gelegenheit, einen guten ersten Eindruck zu erzeugen. Die besten Willkommensnachrichten müssen Folgendes enthalten:

* **Warum ein Benutzer die Nachricht empfängt.** Es muss dem Benutzer sehr klar sein, warum er die Nachricht empfängt. Wenn Ihr Bot in einem Kanal installiert wurde und Sie eine Willkommensnachricht an alle Benutzer gesendet haben, teilen Sie ihnen mit, in welchem Kanal er installiert wurde und wer ihn möglicherweise installiert hat.
* **Was bieten Sie?** Was können sie mit Ihrer App tun? Welchen Wert können Sie ihnen bringen?
* **Was sollten sie als Nächstes tun?** Laden Sie sie ein, einen Befehl auszuprobieren oder auf eine Weise mit Ihrer App zu interagieren.

Denken Sie daran, dass schlechte Willkommensnachrichten dazu führen können, dass Benutzer Ihren Bot blockieren. Verbringen Sie viel Zeit damit, Ihre Willkommensnachrichten zu erstellen, und iterieren Sie sie, wenn sie nicht den gewünschten Effekt haben.

### <a name="notification-messages"></a>Benachrichtigungen

Wenn Sie proaktives Messaging zum Senden von Benachrichtigungen verwenden, müssen Sie sicherstellen, dass Ihre Benutzer einen klaren Pfad haben, um allgemeine Aktionen basierend auf Ihrer Benachrichtigung und einem klaren Verständnis der Gründe für die Benachrichtigung zu ergreifen. Gute Benachrichtigungen umfassen im Allgemeinen Folgendes:

* **Was ist passiert.** Ein eindeutiger Hinweis darauf, was die Benachrichtigung verursacht hat.
* **Was war das Ergebnis?** Es muss klar sein, welche Elemente oder Elemente aktualisiert wurden, um die Benachrichtigung zu verursachen.
* **Wer/was hat es ausgelöst.** Wer oder was hat maßnahmen, die dazu führte, dass die Benachrichtigung gesendet wurde.
* **Was können Benutzer als Antwort tun?** Machen Sie es Ihren Benutzern leicht, Aktionen basierend auf Ihren Benachrichtigungen zu ergreifen.
* **Wie können Benutzer abmelden?** Sie müssen einen Pfad für Benutzer bereitstellen, um zusätzliche Benachrichtigungen abmelden zu können.

### <a name="scheduled-messages"></a>Geplante Nachrichten

Wenn Sie proaktives Messaging zum Senden geplanter Nachrichten an Benutzer verwenden, stellen Sie sicher, dass Ihre Zeitzone auf ihre Zeitzone aktualisiert wird. Dadurch wird sichergestellt, dass die Nachrichten zum entsprechenden Zeitpunkt an die Benutzer zugestellt werden. Zu den Geplanten Nachrichten gehören im Allgemeinen:

* **Warum empfängt der Benutzer die Nachricht:** Machen Sie es Ihren Benutzern leicht, den Grund zu verstehen, warum sie die Nachricht empfangen.
* **Wie kann der Benutzer als Nächstes** vorgehen: Benutzer können die erforderliche Aktion basierend auf dem Nachrichteninhalt ergreifen.

## <a name="proactively-install-your-app-using-graph"></a>Proaktive Installation Ihrer App mithilfe von Graph

> [!Note]
> Die proaktive Installation von Apps mit Microsoft Graph befindet sich derzeit in der Betaversion.

Gelegentlich ist es möglicherweise erforderlich, Benutzer proaktiv zu entsenden, die ihre App zuvor nicht installiert oder mit ihr interagiert haben. Beispielsweise möchten Sie den Unternehmens [communicator](~/samples/app-templates.md#company-communicator) verwenden, um Nachrichten an Ihre gesamte Organisation zu senden. Für dieses Szenario können Sie die Graph-API verwenden, um Ihre App proaktiv für Ihre Benutzer zu installieren, und dann die erforderlichen Werte aus dem Ereignis zwischenspeichern, das Ihre App bei der Installation `conversationUpdate` empfängt.

Sie können nur Apps installieren, die sich im App-Katalog Ihrer Organisation oder im Teams-App-Store befinden.

Weitere [Informationen finden Sie](/graph/api/userteamwork-post-installedapps) unter Installieren von Apps für Benutzer in der Graph-Dokumentation und proaktiver Botinstallation und [-messaging in Teams mit Microsoft Graph](../../../graph-api/proactive-bots-and-messages/graph-proactive-bots-and-messages.md). Es gibt auch ein [Microsoft .NET-Frameworkbeispiel](https://github.com/microsoftgraph/contoso-airlines-teams-sample/blob/283523d45f5ce416111dfc34b8e49728b5012739/project/Models/GraphService.cs#L176) auf der GitHub-Plattform.

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

Sie müssen die Benutzer-ID und die Mandanten-ID liefern. Wenn der Aufruf erfolgreich ist, gibt die API mit dem folgenden Antwortobjekt zurück.

```json
{
  "id":"a:1qhNLqpUtmuI6U35gzjsJn7uRnCkW8NiZALHfN8AMxdbprS1uta2aT-jytfIlsZR3UZeg3TsIONNInBHsdjzj3PtfHuhkxxvS1jZZ61UAbw8fIdXcNSJyTJm7YvHFOgxo"
}
```

---

## <a name="code-samples"></a>Codebeispiele

Die offiziellen proaktiven Messagingbeispiele sind wie folgt:

| Beispielname           | Beschreibung                                                                      | .NET    | JavaScript   | Python  |
|:----------------------|:---------------------------------------------------------------------------------|:--------|:-------------|:--------|
|Grundlagen für Teams-Unterhaltungen  | Veranschaulicht grundlagen von Unterhaltungen in Teams, einschließlich des Sendens von proaktiven 1:1-Nachrichten.|[.NET &nbsp; Core](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/csharp_dotnetcore/57.teams-conversation-bot)|[JavaScript](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/57.teams-conversation-bot) | [Python](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/python/57.teams-conversation-bot)|
|Starten eines neuen Threads in einem Kanal     | Veranschaulicht das Erstellen eines neuen Threads in einem Kanal. |[.NET &nbsp; Core](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/csharp_dotnetcore/58.teams-start-new-thread-in-channel)|[JavaScript](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/javascript_nodejs/58.teams-start-new-thread-in-channel)|[Python](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/python/58.teams-start-thread-in-channel) |

## <a name="view-additional-code-samples"></a>Anzeigen zusätzlicher Codebeispiele
>
> [!div class="nextstepaction"]
> [**Proaktive Messagingcodebeispiele für Teams**](/samples/officedev/msteams-samples-proactive-messaging/msteams-samples-proactive-messaging/)
>
