---
title: Senden proaktiver Nachrichten
description: Beschreibt, wie proaktive Nachrichten mit Ihrem Microsoft Teams Bot gesendet werden.
ms.topic: conceptual
ms.author: anclear
localization_priority: Normal
Keywords: Nachricht senden Benutzer-ID Kanal-ID Unterhaltungs-ID abrufen
ms.openlocfilehash: 5c169e8ef7735b42233bef9992de3540a6fbbee1
ms.sourcegitcommit: a6253e89cb8c8c34d45b06e08c9668daeebc30a3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/06/2021
ms.locfileid: "53300298"
---
# <a name="proactive-messages"></a>Proaktive Nachrichten

[!INCLUDE [v4 to v3 pointer](~/includes/v4-to-v3-pointer-bots.md)]

Eine proaktive Nachricht ist jede Nachricht, die von einem Bot gesendet wird, die nicht als Antwort auf eine Anforderung eines Benutzers erfolgt. Dies kann Nachrichten umfassen, z. B.:

* Willkommensnachrichten
* Benachrichtigungen
* Geplante Nachrichten

Damit Ihr Bot eine proaktive Nachricht an einen Benutzer, einen Gruppenchat oder ein Team senden kann, muss er Zugriff haben, um die Nachricht zu senden. Für einen Gruppenchat oder ein Team muss die App, die Ihren Bot enthält, zuerst an diesem Speicherort installiert werden. Sie können [Ihre App proaktiv mithilfe von Microsoft Graph](#proactively-install-your-app-using-graph) in einem Team installieren, falls erforderlich, oder eine [App-Richtlinie](/microsoftteams/teams-custom-app-policies-and-settings) verwenden, um Apps an Teams und Benutzer in Ihrem Mandanten zu übertragen. Für Benutzer muss Ihre App entweder für den Benutzer installiert werden, oder Ihr Benutzer muss Teil eines Teams sein, in dem Ihre App installiert ist.

Das Senden einer proaktiven Nachricht unterscheidet sich vom Senden einer regulären Nachricht. Es ist nicht aktiv `turnContext` für eine Antwort zu verwenden. Sie müssen die Unterhaltung erstellen, bevor Sie die Nachricht senden. Beispielsweise ein neuer 1:1-Chat oder ein neuer Unterhaltungsthread in einem Kanal. Sie können keinen neuen Gruppenchat oder einen neuen Kanal in einem Team mit proaktiven Nachrichten erstellen.

**So senden Sie eine proaktive Nachricht**

1. Rufen Sie bei Bedarf [die Benutzer-ID, Team-ID oder Kanal-ID](#get-the-user-id-team-id-or-channel-id)ab.
1. [Erstellen Sie die Unterhaltung,](#create-the-conversation)falls erforderlich.
1. [Rufen Sie die Unterhaltungs-ID](#get-the-conversation-id)ab.
1. [Senden Sie die Nachricht.](#send-the-message)

Die Codeausschnitte im [Beispielabschnitt](#samples) dienen zum Erstellen einer 1:1-Unterhaltung. Links zum Ausführen von Arbeitsbeispielen für 1:1-Unterhaltungen und Gruppen oder Kanäle finden Sie im [Codebeispiel.](#code-sample)

Informationen zur effektiven Verwendung proaktiver Nachrichten finden Sie in [den bewährten Methoden für proaktives Messaging.](#best-practices-for-proactive-messaging) Für bestimmte Szenarien müssen Sie [Ihre App proaktiv mit Graph installieren.](#proactively-install-your-app-using-graph) Die Codeausschnitte im [Beispielabschnitt](#samples) dienen zum Erstellen einer 1:1-Unterhaltung. Vollständige Arbeitsbeispiele für 1:1-Unterhaltungen und Gruppen oder Kanäle finden Sie im [Codebeispiel.](#code-sample)

## <a name="get-the-user-id-team-id-or-channel-id"></a>Abrufen der Benutzer-ID, Team-ID oder Kanal-ID

Zum Erstellen eines neuen Unterhaltungs- oder Unterhaltungsthreads in einem Kanal benötigen Sie die richtige ID. Sie können diese ID mit einer der folgenden Optionen empfangen oder abrufen:

* Wenn Ihre App in einem bestimmten Kontext installiert ist, erhalten Sie eine [ `onMembersAdded` Aktivität.](~/bots/how-to/conversations/subscribe-to-conversation-events.md)
* Wenn ein neuer Benutzer zu einem Kontext hinzugefügt wird, in dem Ihre App installiert ist, erhalten Sie eine [ `onMembersAdded` Aktivität.](~/bots/how-to/conversations/subscribe-to-conversation-events.md)
* Sie können die [Liste der Kanäle](~/bots/how-to/get-teams-context.md) in einem Team abrufen, in dem Ihre App installiert ist.
* Sie können die [Liste der Mitglieder](~/bots/how-to/get-teams-context.md) eines Teams abrufen, in dem Ihre App installiert ist.
* Jede Aktivität, die Ihr Bot empfängt, muss die erforderlichen Informationen enthalten.

Unabhängig davon, wie Sie die Informationen erhalten, müssen Sie die `tenantId` und entweder die oder zum Erstellen einer neuen Unterhaltung `userId` `channelId` speichern. Sie können den auch `teamId` verwenden, um einen neuen Unterhaltungsthread im allgemeinen oder Standardkanal eines Teams zu erstellen.

Dies `userId` ist für Ihre Bot-ID und einen bestimmten Benutzer eindeutig. Sie können die zwischen Bots nicht `userId` wiederverwenden. Dies `channelId` ist global. Ihr Bot muss jedoch im Team installiert sein, bevor Sie eine proaktive Nachricht an einen Kanal senden können.

Nachdem Sie die Benutzer- oder Kanalinformationen erhalten haben, müssen Sie die Unterhaltung erstellen.

## <a name="create-the-conversation"></a>Erstellen der Unterhaltung

Sie müssen die Unterhaltung erstellen, wenn sie nicht vorhanden ist oder Sie die `conversationId` . Sie müssen die Unterhaltung nur einmal erstellen und den Wert oder das `conversationId` `conversationReference` Objekt speichern.

Nachdem die Unterhaltung erstellt wurde, müssen Sie die Unterhaltungs-ID abrufen.

## <a name="get-the-conversation-id"></a>Abrufen der Unterhaltungs-ID

Verwenden Sie entweder das `conversationReference` Objekt oder senden Sie die `conversationId` `tenantId` Nachricht. Sie können diese ID abrufen, indem Sie entweder die Unterhaltung erstellen oder sie aus jeder Aktivität speichern, die Aus diesem Kontext an Sie gesendet wird. Store diese ID als Referenz.

Nachdem Sie die entsprechenden Adressinformationen erhalten haben, können Sie Ihre Nachricht senden.

## <a name="send-the-message"></a>Senden der Nachricht

Nachdem Sie nun über die richtigen Adressinformationen verfügen, können Sie Ihre Nachricht senden. Wenn Sie das SDK verwenden, müssen Sie die `continueConversation` Methode und die und einen direkten `conversationId` `tenantId` API-Aufruf verwenden. Sie müssen die richtige Einstellung `conversationParameters` festlegen, um Ihre Nachricht erfolgreich zu senden. Sehen Sie [sich](#samples) den Beispielabschnitt an, oder verwenden Sie eines der Im [Codebeispielabschnitt](#code-sample) aufgeführten Beispiele.

Nachdem Sie die proaktive Nachricht gesendet haben, müssen Sie diese bewährten Methoden befolgen und proaktive Nachrichten senden, um einen besseren Informationsaustausch zwischen Benutzern und dem Bot zu erzielen.

## <a name="best-practices-for-proactive-messaging"></a>Bewährte Methoden für proaktives Messaging

Das Senden proaktiver Nachrichten an Benutzer ist eine sehr effektive Möglichkeit, mit Ihren Benutzern zu kommunizieren. Aus ihrer Sicht kann diese Nachricht jedoch völlig unaufgeladen erscheinen, und im Falle von Willkommensnachrichten ist es das erste Mal, dass sie mit Ihrer App interagiert haben. Daher ist es sehr wichtig, proaktives Messaging sparsam zu verwenden, nicht Ihre Benutzer zu spammen, und genügend Informationen bereitzustellen, damit Benutzer verstehen können, warum sie die Nachrichten empfangen.

### <a name="welcome-messages"></a>Willkommensnachrichten

Wenn proaktives Messaging verwendet wird, um eine Willkommensnachricht an einen Benutzer zu senden, gibt es keinen Kontext dafür, warum die Benutzer die Nachricht empfangen. Dies ist auch das erste Mal, dass Benutzer mit Ihrer App interagieren. Es ist eine Gelegenheit, einen guten ersten Eindruck zu erzeugen. Die besten Willkommensnachrichten müssen Folgendes enthalten:

* Warum ein Benutzer die Nachricht empfängt: Dem Benutzer muss klar sein, warum er die Nachricht empfängt. Wenn Ihr Bot in einem Kanal installiert wurde und Sie eine Willkommensnachricht an alle Benutzer gesendet haben, teilen Sie ihm mit, in welchem Kanal er installiert wurde und wer ihn installiert hat.
* Was bieten Sie an: Benutzer müssen in der Lage sein, zu erkennen, was sie mit Ihrer App tun können und welchen Wert Sie ihnen bieten können.
* Was sollten sie als Nächstes tun: Benutzer einladen, einen Befehl auszuprobieren oder mit Ihrer App zu interagieren.

Nachrichten mit schlechter Willkommensseite können dazu führen, dass Benutzer Ihren Bot blockieren. Schreiben Sie auf den Punkt, und löschen Sie Willkommensnachrichten. Iterieren Sie die Willkommensnachrichten, wenn sie nicht den gewünschten Effekt haben.

### <a name="notification-messages"></a>Benachrichtigungen

Um Benachrichtigungen mithilfe proaktiver Nachrichten zu senden, stellen Sie sicher, dass Ihre Benutzer über einen klaren Pfad verfügen, um allgemeine Aktionen basierend auf Ihrer Benachrichtigung auszuführen. Stellen Sie sicher, dass die Benutzer genau wissen, warum sie eine Benachrichtigung erhalten haben. Gute Benachrichtigungen umfassen im Allgemeinen Folgendes:

* Was passiert ist: Ein eindeutiger Hinweis darauf, was passiert ist, um die Benachrichtigung zu verursachen.
* Was war das Ergebnis: Es muss klar sein, welches Element aktualisiert wurde, um die Benachrichtigung zu verursachen.
* Wer oder was ausgelöst wurde: Wer oder welche Aktion ausgeführt wurde, durch die die Benachrichtigung gesendet wurde.
* Was können Benutzer als Reaktion tun: Erleichtern Sie Es Ihren Benutzern, Aktionen basierend auf Ihren Benachrichtigungen zu ergreifen.
* Wie können Benutzer sich abmelden: Sie müssen einen Pfad angeben, über den Benutzer zusätzliche Benachrichtigungen deaktivieren können.

Um Nachrichten an eine große Gruppe von Benutzern zu senden, z. B. an Ihre Organisation, installieren Sie Ihre App proaktiv mit Graph.

### <a name="scheduled-messages"></a>Geplante Nachrichten

Wenn Sie proaktive Nachrichten verwenden, um geplante Nachrichten an Benutzer zu senden, überprüfen Sie, ob Ihre Zeitzone auf ihre Zeitzone aktualisiert wurde. Dadurch wird sichergestellt, dass die Nachrichten zum entsprechenden Zeitpunkt an die Benutzer übermittelt werden. Zum Planen von Nachrichten gehören in der Regel:

* Warum erhält der Benutzer die Nachricht: Machen Sie es Ihren Benutzern leicht, den Grund zu verstehen, aus dem sie die Nachricht empfangen.
* Was der Benutzer als Nächstes tun kann: Benutzer können die erforderliche Aktion basierend auf dem Nachrichteninhalt ausführen.

## <a name="proactively-install-your-app-using-graph"></a>Proaktives Installieren Ihrer App mit Graph

> [!Note]
> Die proaktive Installation von Apps mit Graph befindet sich derzeit in der Betaversion.

Proaktive Meldung von Benutzern, die zuvor nicht installiert oder mit Ihrer App interagiert haben. Sie möchten z. B. den [Unternehmenskommunikator](~/samples/app-templates.md#company-communicator) verwenden, um Nachrichten an Ihre gesamte Organisation zu senden. In diesem Fall können Sie die Graph-API verwenden, um Ihre App proaktiv für Ihre Benutzer zu installieren. Speichern Sie die erforderlichen Werte aus dem Ereignis zwischen, das `conversationUpdate` Ihre App bei der Installation empfängt.

Sie können nur Apps installieren, die sich im App-Katalog Ihrer Organisation oder im Teams App-Store befinden.

Informationen zum [Installieren von Apps für Benutzer](/graph/api/userteamwork-post-installedapps) finden Sie in der Dokumentation zu Graph sowie zur [proaktiven Bot-Installation und -Messaging in Teams mit Graph.](../../../graph-api/proactive-bots-and-messages/graph-proactive-bots-and-messages.md) Es gibt auch ein [Microsoft .NET Framework-Beispiel](https://github.com/microsoftgraph/contoso-airlines-teams-sample/blob/283523d45f5ce416111dfc34b8e49728b5012739/project/Models/GraphService.cs#L176) auf der GitHub-Plattform.

## <a name="samples"></a>Beispiele

Der folgende Code zeigt, wie proaktive Nachrichten gesendet werden:

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

Die folgende Tabelle enthält ein einfaches Codebeispiel, das den grundlegenden Unterhaltungsfluss in eine Teams Anwendung integriert und wie Sie einen neuen Unterhaltungsthread in einem Kanal in Teams erstellen:

| **Beispielname** | **Beschreibung** | **.NET** | **Node.js** | **Python** |
|---------------|--------------|--------|-------------|--------|
| Teams Grundlagen zu Unterhaltungen  | Veranschaulicht die Grundlagen von Unterhaltungen in Teams, einschließlich des Sendens proaktiver 1:1-Nachrichten.| [View](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/csharp_dotnetcore/57.teams-conversation-bot) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/57.teams-conversation-bot) | [View](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/python/57.teams-conversation-bot) |
| Starten eines neuen Threads in einem Kanal | Veranschaulicht das Erstellen eines neuen Threads in einem Kanal. | [View](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/csharp_dotnetcore/58.teams-start-new-thread-in-channel) | [View](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/javascript_nodejs/58.teams-start-new-thread-in-channel) | [View](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/python/58.teams-start-thread-in-channel) |
| Proaktive Installation der App und Senden proaktiver Benachrichtigungen | Dieses Beispiel zeigt, wie Sie die proaktive Installation von Apps für Benutzer verwenden und proaktive Benachrichtigungen senden können, indem Sie Microsoft Graph APIs aufrufen. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/graph-proactive-installation/csharp) | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/graph-proactive-installation/nodejs) | |

### <a name="additional-code-sample"></a>Zusätzliches Codebeispiel

> [!div class="nextstepaction"]
> [Codebeispiele für proaktives Messaging Teams](/samples/officedev/msteams-samples-proactive-messaging/msteams-samples-proactive-messaging/)

## <a name="see-also"></a>Siehe auch

[**Codebeispiele für proaktives Messaging Teams**](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-proactive-messaging/csharp)

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Formatieren von Bot-Nachrichten](~/bots/how-to/format-your-bot-messages.md)
