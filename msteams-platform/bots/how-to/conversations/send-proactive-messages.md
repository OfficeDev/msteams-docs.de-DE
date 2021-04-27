---
title: Senden proaktiver Nachrichten
description: Beschreibt das Senden proaktiver Nachrichten mit Ihrem Microsoft Teams-Bot.
ms.topic: conceptual
ms.author: anclear
localization_priority: Normal
Keywords: 'Senden einer Nachricht: Benutzer-ID-Kanal-ID-Unterhaltungs-ID erhalten'
ms.openlocfilehash: ae651ac94b1b092374f6fae284b67070036b561f
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020919"
---
# <a name="send-proactive-messages"></a>Senden proaktiver Nachrichten

[!INCLUDE [v4 to v3 pointer](~/includes/v4-to-v3-pointer-bots.md)]

Eine proaktive Nachricht ist jede Nachricht, die von einem Bot gesendet wird, die nicht auf eine Anforderung eines Benutzers reagiert. Dies kann Nachrichten umfassen, z. B.:

* Willkommensnachrichten
* Benachrichtigungen
* Geplante Nachrichten

Damit Ihr Bot eine proaktive Nachricht an einen Benutzer, Gruppenchat oder ein Team senden kann, muss er Zugriff auf das Senden der Nachricht haben. Für einen Gruppenchat oder ein Team muss die App, die Ihren Bot enthält, zuerst an diesem Speicherort installiert werden. Sie können Ihre App bei Bedarf proaktiv mithilfe von Microsoft [](/microsoftteams/teams-custom-app-policies-and-settings) [Graph](#proactively-install-your-app-using-graph) in einem Team installieren oder eine App-Richtlinie verwenden, um Apps an Teams und Benutzer in Ihrem Mandanten zu senden. Für Benutzer muss Ihre App entweder für den Benutzer installiert sein, oder Ihr Benutzer muss Teil eines Teams sein, in dem Ihre App installiert ist.

Das Senden einer proaktiven Nachricht ist anders als das Senden einer regulären Nachricht. Es ist nicht `turnContext` aktiv, eine Antwort zu verwenden. Sie müssen die Unterhaltung erstellen, bevor Sie die Nachricht senden. Beispielsweise ein neuer 1:1-Chat oder ein neuer Unterhaltungsthread in einem Kanal. Sie können keinen neuen Gruppenchat oder einen neuen Kanal in einem Team mit proaktivem Messaging erstellen.

**So senden Sie eine proaktive Nachricht**

1. Wenn erforderlich, erhalten Sie die [Benutzer-, Team- oder Kanal-ID.](#get-the-user-id-team-id-or-channel-id)
1. [Erstellen Sie die Unterhaltung](#create-the-conversation), falls erforderlich.
1. [Die Unterhaltungs-ID erhalten.](#get-the-conversation-id)
1. [Senden Sie die Nachricht](#send-the-message).

Die Codeausschnitte im [Abschnitt Beispiele](#samples) sind zum Erstellen einer 1:1-Unterhaltung. Links zum Abschließen von Arbeitsbeispielen für 1:1-Unterhaltungen und Gruppen oder Kanäle finden Sie unter [Codebeispiel](#code-sample).

Informationen zur effektiven Verwendung proaktiver Nachrichten finden Sie [unter Best Practices for proactive messaging](#best-practices-for-proactive-messaging). In bestimmten Szenarien müssen Sie Ihre App [proaktiv mithilfe von Graph installieren.](#proactively-install-your-app-using-graph) Die Codeausschnitte im [Abschnitt Beispiele](#samples) sind zum Erstellen einer 1:1-Unterhaltung. Vollständige Arbeitsbeispiele für 1:1-Unterhaltungen und Gruppen oder Kanäle finden Sie unter [Codebeispiel](#code-sample).

## <a name="get-the-user-id-team-id-or-channel-id"></a>Benutzer-ID, Team-ID oder Kanal-ID erhalten

Zum Erstellen einer neuen Unterhaltung oder eines neuen Unterhaltungsthreads in einem Kanal müssen Sie über die richtige ID verfügen. Sie können diese ID mithilfe einer der folgenden Optionen empfangen oder abrufen:

* Wenn Ihre App in einem bestimmten Kontext installiert ist, erhalten Sie eine [ `onMembersAdded` Aktivität](~/bots/how-to/conversations/subscribe-to-conversation-events.md).
* Wenn einem Kontext, in dem Ihre App installiert ist, ein neuer Benutzer hinzugefügt wird, erhalten Sie eine [ `onMembersAdded` Aktivität](~/bots/how-to/conversations/subscribe-to-conversation-events.md).
* Sie können die Liste [der Kanäle](~/bots/how-to/get-teams-context.md) in einem Team abrufen, in dem Ihre App installiert ist.
* Sie können die Liste [der Mitglieder eines Teams](~/bots/how-to/get-teams-context.md) abrufen, in dem Ihre App installiert ist.
* Jede Aktivität, die Ihr Bot empfängt, muss die erforderlichen Informationen enthalten.

Unabhängig davon, wie Sie die Informationen erhalten, müssen Sie die und entweder die oder speichern, um `tenantId` eine neue Unterhaltung zu `userId` `channelId` erstellen. Sie können auch den `teamId` verwenden, um einen neuen Unterhaltungsthread im allgemeinen oder Standardkanal eines Teams zu erstellen.

Die `userId` ist für Ihre Bot-ID und einen bestimmten Benutzer eindeutig. Sie können die zwischen `userId` Bots nicht wiederverwenden. Der `channelId` ist global. Ihr Bot muss jedoch im Team installiert sein, bevor Sie eine proaktive Nachricht an einen Kanal senden können.

Nachdem Sie über die Benutzer- oder Kanalinformationen verfügen, müssen Sie die Unterhaltung erstellen.

## <a name="create-the-conversation"></a>Erstellen der Unterhaltung

Sie müssen die Unterhaltung erstellen, wenn sie nicht vorhanden ist oder Sie die `conversationId` nicht kennen. Sie müssen die Unterhaltung nur einmal erstellen und den `conversationId` Wert oder das Objekt `conversationReference` speichern.

Nachdem die Unterhaltung erstellt wurde, müssen Sie die Unterhaltungs-ID erhalten.

## <a name="get-the-conversation-id"></a>Die Unterhaltungs-ID erhalten

Verwenden Sie entweder `conversationReference` das Objekt oder und um die Nachricht zu `conversationId` `tenantId` senden. Sie können diese ID erhalten, indem Sie die Unterhaltung entweder erstellen oder aus allen Aktivitäten speichern, die aus diesem Kontext an Sie gesendet werden. Speichern Sie diese ID als Referenz.

Nachdem Sie die entsprechenden Adressinformationen erhalten haben, können Sie Ihre Nachricht senden.

## <a name="send-the-message"></a>Senden der Nachricht

Nachdem Sie nun über die richtigen Adressinformationen verfügen, können Sie Ihre Nachricht senden. Wenn Sie das SDK verwenden, verwenden Sie dazu die -Methode und und einen direkten `continueConversation` `conversationId` `tenantId` API-Aufruf. Sie müssen die korrekt `conversationParameters` festlegen, damit Ihre Nachricht erfolgreich gesendet wird. Lesen Sie [den Abschnitt](#samples) Beispiele, oder verwenden Sie eines der Im [Codebeispielabschnitt aufgeführten](#code-sample) Beispiele.

Wenn Sie das SDK verwenden, müssen Sie die -Methode und das und verwenden, um einen direkten API-Aufruf zum Senden `continueConversation` `conversationId` der Nachricht zu `tenantId` erstellen. Sie müssen die korrekt `conversationParameters` festlegen, damit Ihre Nachricht erfolgreich gesendet wird.

Nachdem Sie die proaktive Nachricht gesendet haben, müssen Sie diese bewährten Methoden befolgen und gleichzeitig proaktive Nachrichten senden, um einen besseren Informationsaustausch zwischen Benutzern und dem Bot zu ermöglichen.

## <a name="best-practices-for-proactive-messaging"></a>Bewährte Methoden für proaktives Messaging

Das Senden proaktiver Nachrichten an Benutzer ist eine sehr effektive Möglichkeit, mit Ihren Benutzern zu kommunizieren. Aus ihrer Sicht kann diese Nachricht jedoch völlig unprompted angezeigt werden, und im Falle von Willkommensnachrichten ist es das erste Mal, dass sie mit Ihrer App interagiert haben. Daher ist es sehr wichtig, proaktives Messaging sparsam zu verwenden, keine Spamnachrichten für Ihre Benutzer zu verwenden und genügend Informationen zur Verfügung zu stellen, damit Benutzer verstehen können, warum sie die Nachrichten empfangen.

### <a name="welcome-messages"></a>Willkommensnachrichten

Wenn proaktives Messaging zum Senden einer Willkommensnachricht an einen Benutzer verwendet wird, gibt es keinen Kontext dafür, warum die Benutzer die Nachricht empfangen. Dies ist auch das erste Mal, dass Benutzer mit Ihrer App interagieren. Es ist eine Gelegenheit, einen guten ersten Eindruck zu erzeugen. Die besten Willkommensnachrichten müssen Folgendes enthalten:

* Warum ein Benutzer die Nachricht empfängt: Es muss dem Benutzer sehr klar sein, warum er die Nachricht empfängt. Wenn Ihr Bot in einem Kanal installiert wurde und Sie eine Willkommensnachricht an alle Benutzer gesendet haben, teilen Sie ihnen mit, in welchem Kanal er installiert wurde und wer ihn installiert hat.
* Was bieten Sie: Benutzer müssen in der Lage sein, zu ermitteln, was sie mit Ihrer App tun können und welchen Wert Sie ihnen bieten können.
* Was sollten sie als Nächstes tun: Laden Sie Benutzer ein, einen Befehl auszuprobieren oder mit Ihrer App zu interagieren.

Schlechte Willkommensnachrichten können dazu führen, dass Benutzer Ihren Bot blockieren. Schreiben Sie auf den Punkt, und löschen Sie Begrüßungsnachrichten. Iterate on the welcome messages if they are not having the desired effect.

### <a name="notification-messages"></a>Benachrichtigungen

Um Benachrichtigungen mit proaktivem Messaging zu senden, stellen Sie sicher, dass Ihre Benutzer über einen klaren Pfad verfügen, um allgemeine Aktionen basierend auf Ihrer Benachrichtigung zu ergreifen. Stellen Sie sicher, dass Benutzer ein klares Verständnis dafür haben, warum sie eine Benachrichtigung erhalten haben. Gute Benachrichtigungen umfassen im Allgemeinen Folgendes:

* Was passiert ist: Ein eindeutiger Hinweis darauf, was die Benachrichtigung verursacht hat.
* Das Ergebnis: Es muss klar sein, welches Element aktualisiert wurde, um die Benachrichtigung zu verursachen.
* Wer oder was hat sie ausgelöst: Wer oder welche Aktion hat die Benachrichtigung gesendet.
* Was können Benutzer als Reaktion tun: Machen Sie es Ihren Benutzern leicht, Aktionen basierend auf Ihren Benachrichtigungen zu ergreifen.
* Wie können Benutzer sich abmelden: Sie müssen einen Pfad für Benutzer bereitstellen, um zusätzliche Benachrichtigungen abmelden zu können.

Um Nachrichten an eine große Gruppe von Benutzern zu senden, z. B. an Ihre Organisation, installieren Sie Ihre App proaktiv mithilfe von Graph.

### <a name="scheduled-messages"></a>Geplante Nachrichten

Wenn Sie proaktives Messaging zum Senden geplanter Nachrichten an Benutzer verwenden, stellen Sie sicher, dass Ihre Zeitzone auf ihre Zeitzone aktualisiert wird. Dadurch wird sichergestellt, dass die Nachrichten zum entsprechenden Zeitpunkt an die Benutzer zugestellt werden. Zu den Geplanten Nachrichten gehören im Allgemeinen:

* Warum empfängt der Benutzer die Nachricht: Machen Sie es Ihren Benutzern leicht, den Grund zu verstehen, warum sie die Nachricht empfangen.
* Was der Benutzer als Nächstes tun kann: Benutzer können die erforderliche Aktion basierend auf dem Nachrichteninhalt ergreifen.

## <a name="proactively-install-your-app-using-graph"></a>Proaktive Installation Ihrer App mithilfe von Graph

> [!Note]
> Die proaktive Installation von Apps mithilfe von Graph befindet sich derzeit in der Betaversion.

Proaktiv nachrichtenbenutzer, die zuvor nicht installiert oder mit Ihrer App interagiert haben. Beispielsweise möchten Sie den Unternehmens [communicator](~/samples/app-templates.md#company-communicator) verwenden, um Nachrichten an Ihre gesamte Organisation zu senden. In diesem Fall können Sie die Graph-API verwenden, um Ihre App proaktiv für Ihre Benutzer zu installieren. Speichern Sie die erforderlichen Werte aus dem `conversationUpdate` Ereignis, das Ihre App bei der Installation empfängt.

Sie können nur Apps installieren, die sich im App-Katalog Ihrer Organisation oder im Teams App Store befinden.

Weitere [Informationen finden Sie](/graph/api/userteamwork-post-installedapps) unter Installieren von Apps für Benutzer in der Graph-Dokumentation und proaktiver Botinstallation und [-messaging in Teams mit Graph](../../../graph-api/proactive-bots-and-messages/graph-proactive-bots-and-messages.md). Es gibt auch ein [Microsoft .NET-Frameworkbeispiel](https://github.com/microsoftgraph/contoso-airlines-teams-sample/blob/283523d45f5ce416111dfc34b8e49728b5012739/project/Models/GraphService.cs#L176) auf der GitHub-Plattform.

## <a name="samples"></a>Beispiele

Der folgende Code zeigt ein einfaches Codebeispiel, das Ihre App proaktiv mithilfe von Graph installiert:

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

Sie müssen die Benutzer-ID und die Mandanten-ID liefern. Wenn der Aufruf erfolgreich ist, gibt die API das folgende Antwortobjekt zurück:

```json
{
  "id":"a:1qhNLqpUtmuI6U35gzjsJn7uRnCkW8NiZALHfN8AMxdbprS1uta2aT-jytfIlsZR3UZeg3TsIONNInBHsdjzj3PtfHuhkxxvS1jZZ61UAbw8fIdXcNSJyTJm7YvHFOgxo"
}
```

---

## <a name="code-sample"></a>Codebeispiel

Die folgende Tabelle enthält ein einfaches Codebeispiel, das grundlegenden Unterhaltungsfluss in eine Teams-Anwendung integriert und wie Sie einen neuen Unterhaltungsthread in einem Kanal in Teams erstellen:

| **Beispielname** | **Beschreibung** | **.NET** | **Node.js** | **Python** |
|---------------|--------------|--------|-------------|--------|
| Grundlagen für Teams-Unterhaltungen  | Veranschaulicht grundlagen von Unterhaltungen in Teams, einschließlich des Sendens von proaktiven 1:1-Nachrichten.| [View](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/csharp_dotnetcore/57.teams-conversation-bot) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/57.teams-conversation-bot) | [View](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/python/57.teams-conversation-bot) |
| Starten eines neuen Threads in einem Kanal | Veranschaulicht das Erstellen eines neuen Threads in einem Kanal. | [View](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/csharp_dotnetcore/58.teams-start-new-thread-in-channel) | [View](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/javascript_nodejs/58.teams-start-new-thread-in-channel) | [View](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/python/58.teams-start-thread-in-channel) |

### <a name="additional-code-sample"></a>Zusätzliches Codebeispiel

> [!div class="nextstepaction"]
> [Proaktive Messagingcodebeispiele für Teams](/samples/officedev/msteams-samples-proactive-messaging/msteams-samples-proactive-messaging/)

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [**Proaktive Messagingcodebeispiele für Teams**](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-proactive-messaging/csharp) 
>  [Formatieren von Botnachrichten](~/bots/how-to/format-your-bot-messages.md)
