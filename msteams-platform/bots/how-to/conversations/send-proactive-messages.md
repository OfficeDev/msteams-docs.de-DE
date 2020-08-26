---
title: Versenden proaktiver Nachrichten
author: clearab
description: Wie Sie proaktive Nachrichten mit Ihrem Microsoft Teams-bot senden.
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: 2dfb8e18243079ca38d505f4b80deb7abf2de32f
ms.sourcegitcommit: 52732714105fac07c331cd31e370a9685f45d3e1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "46874849"
---
# <a name="send-proactive-messages"></a>Versenden proaktiver Nachrichten

[!INCLUDE [v4 to v3 pointer](~/includes/v4-to-v3-pointer-bots.md)]

Eine proaktive Nachricht ist eine Nachricht, die von einem bot gesendet wird, die nicht direkt auf eine Anforderung eines Benutzers reagiert. Dies kann beispielsweise folgende Nachrichten enthalten:

* Willkommensnachrichten
* Benachrichtigungen
* Geplante Nachrichten

Damit Ihr bot eine proaktive Nachricht senden kann, muss er Zugriff auf den Benutzer, den Gruppenchat oder das Team haben, an das Sie die Nachricht senden möchten. Für einen Gruppenchat oder ein Team bedeutet dies, dass die APP, die ihren bot enthält, zuerst an diesem Speicherort installiert werden muss. Sie können [Ihre APP bei Bedarf proaktiv mithilfe von Graph](#proactively-install-your-app-using-graph) in einem Team installieren oder mithilfe einer APP- [Richtlinie](/microsoftteams/teams-custom-app-policies-and-settings) apps an Microsoft Teams und Benutzer in Ihrem Mandanten verschieben. Für Benutzer muss Ihre APP entweder für diesen Benutzer installiert sein, oder der Benutzer muss Teil eines Teams sein, in dem die APP installiert ist.

Das Senden einer proaktiven Nachricht unterscheidet sich vom Senden einer regulären Nachricht dadurch, dass Sie keine aktive Person `turnContext` für eine Antwort verwenden müssen. Möglicherweise müssen Sie auch die Unterhaltung erstellen (beispielsweise einen neuen eins-zu-eins-Chat oder einen neuen Unterhaltungsthread in einem Kanal), bevor Sie die Nachricht senden. Sie können keinen neuen Gruppenchat oder einen neuen Kanal in einem Team mit proaktivem Messaging erstellen.

Auf einer hohen Ebene müssen Sie die folgenden Schritte ausführen, um eine proaktive Nachricht zu senden:

1. [Rufen Sie die Benutzer-ID oder die Team-/Kanal-ID](#get-the-user-id-or-teamchannel-id) (falls erforderlich) ab.
1. [Erstellen Sie den Unterhaltung-oder Unterhaltungsthread](#create-the-conversation) (falls erforderlich).
1. [Rufen Sie die Unterhaltungs-ID](#get-the-conversation-id)ab.
1. [Senden Sie die Nachricht](#send-the-message).

Die Codeausschnitte im folgenden Abschnitt " [Beispiele](#examples) " dienen zum Erstellen einer 1:1-Unterhaltung, im Abschnitt " [Verweise](#references) " finden Sie Links zu vollständigen Arbeitsbeispielen für einmalige Unterhaltungen und Gruppen/Kanäle.

## <a name="get-the-user-id-or-teamchannel-id"></a>Abrufen der Benutzer-ID oder der Team/Kanal-ID

Wenn Sie einen neuen Unterhaltungs-oder Unterhaltungsthread in einem Kanal erstellen müssen, benötigen Sie zunächst die richtige ID, um die Unterhaltung zu erstellen. Sie können diese ID auf verschiedene Arten empfangen/abrufen:

1. Wenn Ihre APP in einem bestimmten Kontext installiert ist, erhalten Sie eine [ `onMembersAdded` Aktivität](~/bots/how-to/conversations/subscribe-to-conversation-events.md).
1. Wenn einem Kontext, in dem Ihre APP installiert ist, ein neuer Benutzer hinzugefügt wird, erhalten Sie eine [ `onMembersAdded` Aktivität](~/bots/how-to/conversations/subscribe-to-conversation-events.md).
1. Sie können die [Liste der Kanäle](~/bots/how-to/get-teams-context.md) in einem Team abrufen, auf dem Ihre APP installiert ist.
1. Sie können die [Liste der Mitglieder](~/bots/how-to/get-teams-context.md) eines Teams abrufen, auf dem Ihre APP installiert ist.
1. Jede Aktivität, die ihr bot erhält, enthält die notwendigen Informationen.

Unabhängig davon, wie Sie die Informationen erhalten, müssen Sie die `tenantId` -und entweder die oder-speichern, um `userId` `channelId` eine neue Unterhaltung zu erstellen. Sie können auch die verwenden `teamId` , um einen neuen Unterhaltungsthread im allgemeinen/Standardkanal eines Teams zu erstellen.

Die `userId` ist für Ihre bot-ID und einen bestimmten Benutzer eindeutig, Sie können Sie nicht zwischen Bots wieder verwenden. Das `channelId` ist Global, aber Ihr bot _muss_ im Team installiert sein, bevor Sie eine proaktive Nachricht an einen Kanal senden können.

## <a name="create-the-conversation"></a>Erstellen der Unterhaltung

Sobald Sie über die Benutzer/Kanal-Informationen verfügen, müssen Sie die Unterhaltung erstellen, wenn Sie noch nicht vorhanden ist (oder Sie wissen nicht, welche `conversationId` ). Sie sollten die Unterhaltung nur einmal erstellen; Stellen Sie sicher, dass Sie den `conversationId` Wert oder das `conversationReference` Objekt speichern, das in Zukunft verwendet werden soll.

## <a name="get-the-conversation-id"></a>Abrufen der Unterhaltungs-ID

Nachdem die Unterhaltung erstellt wurde, verwenden Sie entweder das `conversationReference` -Objekt oder das `conversationId` und- `tenantId` , um die Nachricht zu senden. Sie können diese ID abrufen, indem Sie die Unterhaltung entweder erstellen oder aus einer Aktivität speichern, die Sie aus diesem Kontext erhalten haben. Stellen Sie sicher, dass Sie diese ID speichern.

## <a name="send-the-message"></a>Senden der Nachricht

Da Sie nun über die richtigen Adressinformationen verfügen, können Sie Ihre Nachricht senden. Wenn Sie das SDK verwenden, verwenden Sie die `continueConversation` -Methode und den `conversationId` und `tenantId` , um einen direkten API-Aufruf zu tätigen.  Sie müssen das `conversationParameters` ordnungsgemäße festlegen, um Ihre Nachricht erfolgreich zu senden-siehe die [Beispiele](#examples) unten oder verwenden Sie eines der Beispiele im Abschnitt [Verweise](#references) aufgeführt.

## <a name="best-practices-for-proactive-messaging"></a>Bewährte Methoden für proaktives Messaging

Das Senden proaktiver Nachrichten an Benutzer kann eine sehr effektive Möglichkeit zur Kommunikation mit ihren Benutzern sein. Aus ihrer Perspektive kann diese Nachricht jedoch vollständig unaufgefordert angezeigt werden, und im Fall von Begrüßungsnachrichten ist dies das erste Mal, dass Sie mit Ihrer APP interagieren. Daher ist es sehr wichtig, diese Funktionalität sparsam zu verwenden (keine Spam-e-Mail-Benutzer) und genügend Informationen bereitzustellen, damit Benutzer verstehen, warum Sie Nachrichten erhalten.

### <a name="welcome-messages"></a>Willkommensnachrichten

Bei Verwendung von proaktivem Messaging zum Senden einer Willkommensnachricht an einen Benutzer müssen Sie Bedenken, dass für die meisten Personen, die die Nachricht erhalten, kein Kontext dafür vorhanden ist, warum Sie Sie empfangen. Dies ist auch das erste Mal, dass Sie mit Ihrer APP interagieren; Es ist Ihre Gelegenheit, einen guten ersten Eindruck zu erstellen. Die besten Begrüßungsnachrichten umfassen Folgendes:

* **Warum ein Benutzer die Nachricht empfängt.** Dem Benutzer sollte sehr deutlich sein, warum er die Nachricht empfängt. Wenn Ihr bot in einem Kanal installiert wurde und Sie eine Willkommensnachricht an alle Benutzer gesendet haben, sollten Sie wissen, in welchem Kanal Sie installiert wurde und wer Sie möglicherweise installiert hat.
* **Was bieten Sie an?** Was können Sie mit Ihrer APP tun? Welchen Wert können Sie Ihnen bringen?
* **Was sollten Sie als nächstes tun?** Laden Sie Sie ein, einen Befehl auszuprobieren oder mit ihrer app in irgendeiner Weise zu interagieren.

Denken Sie daran, dass schlechte Begrüßungsnachrichten dazu führen können, dass Benutzer ihren bot blockieren. Sie sollten viel Zeit damit verbringen, ihre Begrüßungsnachrichten zu entwerfen und Sie zu durchlaufen, wenn Sie nicht den gewünschten Effekt haben.

### <a name="notification-messages"></a>Benachrichtigungen

Bei der Verwendung von proaktivem Messaging zum Senden von Benachrichtigungen müssen Sie sicherstellen, dass Ihre Benutzer über einen klaren Pfad verfügen, um häufige Aktionen basierend auf Ihrer Benachrichtigung durchzuführen, und ein klares Verständnis dafür, warum die Benachrichtigung erfolgt ist. Gute Benachrichtigungsnachrichten umfassen im Allgemeinen Folgendes:

* **Was ist passiert.** Ein klarer Hinweis darauf, was passiert ist, um die Benachrichtigung zu verursachen.
* **Was war das Ergebnis?** Es sollte klar sein, welches Element/Ding aktualisiert wurde, um die Benachrichtigung zu verursachen.
* **Wer/was hat ihn ausgelöst.** Die Person oder die Aktion, die die Benachrichtigung gesendet hat.
* **Was können Benutzer als Antwort tun?** Erleichtern Sie Ihren Benutzern das Ausführen von Aktionen basierend auf Ihren Benachrichtigungen.
* **Wie können sich Benutzer abmelden?** Sie müssen einen Pfad angeben, damit Benutzer zusätzliche Benachrichtigungen deaktivieren können.

## <a name="proactively-install-your-app-using-graph"></a>Proaktive Installation Ihrer App mithilfe von Graph

> [!Note]
> Die proaktive Installation von apps mithilfe von Microsoft Graph befindet sich derzeit in der Betaphase.

Gelegentlich kann es erforderlich sein, Benutzer proaktiv Nachrichten zu verständigen, die zuvor noch nicht mit Ihrer APP installiert oder mit ihr interagiert haben. Beispielsweise möchten Sie das [Unternehmens Communicator](~/samples/app-templates.md#company-communicator) verwenden, um Nachrichten an die gesamte Organisation zu senden. In diesem Szenario können Sie die Graph-API verwenden, um Ihre APP proaktiv für Ihre Benutzer zu installieren, und dann die erforderlichen Werte aus dem Ereignis Zwischenspeichern, das `conversationUpdate` Ihre APP bei der Installation empfangen wird.

Sie können nur apps installieren, die sich in Ihrem Organisations-App-Katalog oder im Microsoft Teams-App-Store befinden.

Siehe [Installieren von Apps für Benutzer](/graph/teams-proactive-messaging) in der Graph-Dokumentation und [proaktive bot-Installation und-Messaging in Microsoft Teams mit Microsoft Graph](../../../graph-api/proactive-bots-and-messages/graph-proactive-bots-and-messages.md). Es gibt auch ein [Microsoft .NET Framework-Beispiel](https://github.com/microsoftgraph/contoso-airlines-teams-sample/blob/283523d45f5ce416111dfc34b8e49728b5012739/project/Models/GraphService.cs#L176)  auf der GitHub-Plattform.

## <a name="examples"></a>Beispiele

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

```csharp
private async Task MessageAllMembersAsync(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
{
    var teamsChannelId = turnContext.Activity.TeamsGetChannelId();
    var serviceUrl = turnContext.Activity.ServiceUrl;
    var credentials = new MicrosoftAppCredentials(_appId, _appPassword);
    ConversationReference conversationReference = null;

    //Get the set of member IDs to send the message to
    var members = await GetPagedMembers(turnContext, cancellationToken);

    foreach (var teamMember in members)
    {
        var proactiveMessage = MessageFactory.Text($"Hello {teamMember.GivenName} {teamMember.Surname}. I'm a Teams conversation bot.");

        var conversationParameters = new ConversationParameters
        {
            IsGroup = false,
            Bot = turnContext.Activity.Recipient,
            Members = new ChannelAccount[] { teamMember },
            TenantId = turnContext.Activity.Conversation.TenantId,
        };
        //create the new one-to-one conversations
        await ((BotFrameworkAdapter)turnContext.Adapter).CreateConversationAsync(
            teamsChannelId,
            serviceUrl,
            credentials,
            conversationParameters,
            async (t1, c1) =>
            {
                //Get the conversationReference
                conversationReference = t1.Activity.GetConversationReference();
                //Send the proactive message
                await ((BotFrameworkAdapter)turnContext.Adapter).ContinueConversationAsync(
                    _appId,
                    conversationReference,
                    async (t2, c2) =>
                    {
                        await t2.SendActivityAsync(proactiveMessage, c2);
                    },
                    cancellationToken);
            },
            cancellationToken);
    }

    await turnContext.SendActivityAsync(MessageFactory.Text("All messages have been sent."), cancellationToken);
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

Sie müssen die Benutzer-ID und die Mandanten-ID angeben. Wenn der Aufruf erfolgreich ist, gibt die API mit dem folgenden Response-Objekt zurück.

```json
{
  "id":"a:1qhNLqpUtmuI6U35gzjsJn7uRnCkW8NiZALHfN8AMxdbprS1uta2aT-jytfIlsZR3UZeg3TsIONNInBHsdjzj3PtfHuhkxxvS1jZZ61UAbw8fIdXcNSJyTJm7YvHFOgxo"
}
```

---

## <a name="references"></a>Informationsquellen

Die offiziellen Proactive Messaging-Beispiele sind unten aufgeführt.

|  Nein.  | Beispiel Name           | Beschreibung                                                                      | .NET    | JavaScript   | Python  |
|:--:|:----------------------|:---------------------------------------------------------------------------------|:--------|:-------------|:--------|
|57|Grundlagen der Microsoft Teams-Konversation  | Veranschaulicht Grundlagen der Unterhaltungen in Microsoft Teams, einschließlich des Sendens von 1:1-Nachrichten.|[.Net- &nbsp; Kern](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/csharp_dotnetcore/57.teams-conversation-bot)|[JavaScript](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/57.teams-conversation-bot) | [Python](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/python/57.teams-conversation-bot)|
|58|Neuen Thread in einem Kanal starten     | Veranschaulicht das Erstellen eines neuen Threads in einem Kanal. |[.Net- &nbsp; Kern](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/csharp_dotnetcore/58.teams-start-new-thread-in-channel)|[JavaScript](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/javascript_nodejs/58.teams-start-new-thread-in-channel)|[Python](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/python/58.teams-start-thread-in-channel) |

Das Beispiel unten veranschaulicht die minimale Menge an Informationen, die zum Senden einer proaktiven Nachricht benötigt werden (ohne Verwendung eines `conversationReference` Objekts). Dieses Beispiel kann hilfreich sein, wenn Sie Rest-API-Aufrufe direkt verwenden oder keine vollständigen `conversationReference` Objekte gespeichert haben.

* [Proaktive Messaging Teams](https://github.com/clearab/teamsProactiveMessaging)

## <a name="view-additional-code"></a>Anzeigen von zusätzlichem Code
>
> [!div class="nextstepaction"]
> [**Proaktive Messaging-Codebeispiele für Teams**](/samples/officedev/msteams-samples-proactive-messaging/msteams-samples-proactive-messaging/)
>