---
title: Senden proaktiver Nachrichten
author: clearab
description: Wie Sie proaktive Nachrichten mit Ihrem Microsoft Teams-bot senden.
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: e60fdbfb909abec2c6d64ed0d32fa1a4c4b463a6
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674224"
---
# <a name="send-proactive-messages"></a>Senden proaktiver Nachrichten

> [!Note]
> In den Codebeispielen in diesem Artikel werden das V3 bot Framework SDK und V3 Teams bot Builder SDK-Erweiterungen verwendet. Konzeptionell gelten die Informationen bei der Verwendung der V4-Versionen des SDK, aber der Code unterscheidet sich geringfügig.

Eine proaktive Nachricht ist eine Nachricht, die von einem bot gesendet wird, um eine Unterhaltung zu starten. Möglicherweise möchten Sie, dass Ihr bot eine Unterhaltung aus einer Reihe von Gründen startet, einschließlich:

* Begrüßungsnachrichten für persönliche bot-Unterhaltungen
* Umfrage Antworten
* Externe Ereignisbenachrichtigungen

Das Senden einer Nachricht zum Starten eines neuen Unterhaltungs Threads unterscheidet sich vom Senden einer Nachricht als Reaktion auf eine vorhandene Unterhaltung: Wenn Ihr bot eine neue Unterhaltung startet, gibt es keine bereits vorhandene Unterhaltung, an die die Nachricht gesendet werden soll. Um eine proaktive Nachricht zu senden, müssen Sie Folgendes tun:

1. [Entscheiden, was Sie sagen werden](#best-practices-for-proactive-messaging)
1. [Abrufen der eindeutigen ID des Benutzers und der Mandanten-ID](#obtain-necessary-user-information)
1. [Senden der Nachricht](#examples)

Wenn Sie proaktive nach **** richten erstellen `MicrosoftAppCredentials.TrustServiceUrl`, müssen Sie die Dienst-URL aufrufen und weiter `ConnectorClient` geben, bevor Sie die Nachricht senden, die Sie verwenden werden. Wenn dies nicht der Fall ist, erhält Ihre APP `401: Unauthorized` eine Antwort. 

## <a name="best-practices-for-proactive-messaging"></a>Bewährte Methoden für proaktives Messaging

Das Senden proaktiver Nachrichten an Benutzer kann eine sehr effektive Möglichkeit zur Kommunikation mit ihren Benutzern sein. Aus ihrer Perspektive kann diese Nachricht jedoch scheinbar völlig unaufgefordert angezeigt werden, und im Fall von Begrüßungsnachrichten ist das erste Mal, dass Sie mit Ihrer APP interagieren. Daher ist es sehr wichtig, diese Funktionalität sparsam zu verwenden (keine Spam-e-Mail-Benutzer) und Ihnen genügend Informationen zur Verfügung zu stellen, damit Sie verstehen, warum Sie Nachrichten erhalten.

Proaktive Nachrichten fallen im Allgemeinen in eine von zwei Kategorien, Begrüßungsnachrichten oder Benachrichtigungen.

### <a name="welcome-messages"></a>Begrüßungsnachrichten

Bei der Verwendung von proaktivem Messaging zum Senden einer Willkommensnachricht an einen Benutzer müssen Sie Bedenken, dass für die meisten Personen, die die Nachricht erhalten, kein Kontext dafür vorhanden ist, warum Sie Sie empfangen. Dies ist auch das erste Mal, dass Sie mit Ihrer APP interagieren; Es ist Ihre Gelegenheit, einen guten ersten Eindruck zu erstellen. Die besten Begrüßungsnachrichten umfassen Folgendes:

* **Warum erhalten Sie diese Nachricht.** Dem Benutzer sollte sehr deutlich sein, warum er die Nachricht empfängt. Wenn Ihr bot in einem Kanal installiert wurde und Sie eine Willkommensnachricht an alle Benutzer gesendet haben, sollten Sie wissen, in welchem Kanal Sie installiert wurde und wer Sie möglicherweise installiert hat.
* **Was bieten Sie an?** Was können Sie mit Ihrer APP tun? Welchen Wert können Sie Ihnen bringen?
* **Was sollten Sie als nächstes tun?** Laden Sie Sie ein, einen Befehl auszuprobieren oder mit ihrer app in irgendeiner Weise zu interagieren.

### <a name="notification-messages"></a>Benachrichtigungsmeldungen

Bei der Verwendung von proaktivem Messaging zum Senden von Benachrichtigungen müssen Sie sicherstellen, dass Ihre Benutzer über einen klaren Pfad verfügen, um häufige Aktionen basierend auf Ihrer Benachrichtigung durchzuführen, und ein klares Verständnis dafür, warum die Benachrichtigung erfolgt ist. Gute Benachrichtigungsnachrichten umfassen im Allgemeinen Folgendes:

* **Was ist passiert.** Ein klarer Hinweis darauf, was passiert ist, um die Benachrichtigung zu verursachen.
* **Was passiert ist.** Es sollte klar sein, welches Element/Ding aktualisiert wurde, um die Benachrichtigung zu verursachen.
* **Wer hat es getan?** Wer hat die Aktion durchgeführt, die die Benachrichtigung gesendet hat.
* **Was Sie dagegen tun können.** Erleichtern Sie Ihren Benutzern das Ausführen von Aktionen basierend auf Ihren Benachrichtigungen.
* **Wie Sie sich abmelden können.** Sie müssen einen Pfad angeben, damit Benutzer zusätzliche Benachrichtigungen deaktivieren können.

## <a name="obtain-necessary-user-information"></a>Abrufen der erforderlichen Benutzerinformationen

Bots können neue Unterhaltungen mit einem einzelnen Microsoft Teams-Benutzer erstellen, indem Sie die *eindeutige ID* und die *Mandanten-ID* des Benutzers abrufen. Sie können diese Werte mit einer der folgenden Methoden abrufen:

* Indem Sie [die Team Liste](../get-teams-context.md#fetching-the-roster-or-user-profile) von einem Kanal abrufen, in dem Ihre APP installiert ist.
* Durch Zwischenspeicherung, wenn ein Benutzer [mit Ihrem bot in einem Kanal interagiert](./channel-and-group-conversations.md).
* Wenn ein Benutzer [in einer Kanal Unterhaltung @mentioned](./channel-and-group-conversations.md#retrieving-mentions) wird, ist der bot ein Teil von.
* Durch Zwischenspeicherung, wenn Sie [das `conversationUpdate` Ereignis empfangen](./subscribe-to-conversation-events.md#team-members-added) , wenn Ihre APP im persönlichen Bereich installiert ist, oder neue Mitglieder zu einem Kanal oder Gruppenchat hinzugefügt werden, der

### <a name="proactively-install-your-app-using-graph"></a>Proaktive Installation Ihrer App mithilfe von Graph

> [!Note]
> Die proaktive Installation von apps mithilfe von Graph befindet sich derzeit in der Betaphase.

Gelegentlich kann es erforderlich sein, Benutzer proaktiv Nachrichten zu verständigen, die zuvor noch nicht mit Ihrer APP installiert oder mit ihr interagiert haben. Beispielsweise möchten Sie das [Unternehmens Communicator](~/samples/app-templates.md#company-communicator) verwenden, um Nachrichten an die gesamte Organisation zu senden. In diesem Szenario können Sie die Graph-API verwenden, um Ihre APP proaktiv für Ihre Benutzer zu installieren, und dann die erforderlichen Werte aus `conversationUpdate` dem Ereignis Zwischenspeichern, das Ihre APP bei der Installation empfangen wird.

Sie können nur apps installieren, die sich in Ihrem Organisations-App-Katalog oder im Microsoft Teams-App-Store befinden.

Ausführliche Informationen finden Sie unter [Installieren von Apps für Benutzer](/graph/teams-proactive-messaging) in der Graph-Dokumentation. Es gibt auch ein [Beispiel in .net](https://github.com/microsoftgraph/contoso-airlines-teams-sample/blob/283523d45f5ce416111dfc34b8e49728b5012739/project/Models/GraphService.cs#L176).

## <a name="examples"></a>Beispiele

Stellen Sie sicher, dass Sie sich authentifizieren und über ein Bearer-Token verfügen, bevor Sie eine neue Unterhaltung mit der Rest-API erstellen. Das `members.id` Feld im folgenden Objekt ist für die Kombination aus Ihrem bot und einem Benutzer eindeutig. Sie können es nicht über eine andere Methode als die oben beschriebenen erhalten.

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

Diese ID ist die eindeutige Unterhaltungs-ID des persönlichen Chats. Speichern Sie diesen Wert, und verwenden Sie ihn für zukünftige Interaktionen mit dem Benutzer.

# <a name="cnettabdotnet"></a>[C#-/.net](#tab/dotnet)

In diesem Beispiel wird das [Microsoft. bot. Connector. Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) -NuGet-Paket verwendet.

```csharp
// Create or get existing chat conversation with user
var response = client.Conversations.CreateOrGetDirectConversation(activity.Recipient, activity.From, activity.GetTenantId());

// Construct the message to post to conversation
Activity newActivity = new Activity()
{
    Text = "Hello",
    Type = ActivityTypes.Message,
    Conversation = new ConversationAccount
    {
        Id = response.Id
    },
};

// Post the message to chat conversation with user
await client.Conversations.SendToConversationAsync(newActivity, response.Id);
```

# <a name="javascripttabjavascript"></a>[JavaScript](#tab/javascript)

In diesem Beispiel wird das NPM [-Paket botbuilder-Teams](https://www.npmjs.com/package/botbuilder-teams) verwendet.

```javascript
var address =
{
    channelId: 'msteams',
    user: { id: userId },
    channelData: {
        tenant: {
            id: tenantId
        }
    },
    bot:
    {
        id: appId,
        name: appName
    },
    serviceUrl: session.message.address.serviceUrl,
    useAuth: true
}

var msg = new builder.Message().address(address);
msg.text('Hello, this is a notification');
bot.send(msg);
```

# <a name="pythontabpython"></a>[Python](#tab/python)

```python
async def _send_proactive_message():
  for conversation_reference in CONVERSATION_REFERENCES.values():
    return await ADAPTER.continue_conversation(APP_ID, conversation_reference,
      lambda turn_context: turn_context.send_activity("proactive hello")
    )

```

---

## <a name="creating-a-channel-conversation"></a>Erstellen einer Kanal Unterhaltung

Ihr von einem Team hinzugefügter bot kann in einem Kanal Posten, um eine neue Antwort Kette zu erstellen. Wenn Sie das Node. js Teams-SDK verwenden, verwenden `startReplyChain()` Sie das, das Ihnen eine vollständig aufgefüllte Adresse mit der korrekten Aktivitäts-ID und der entsprechenden Unterhaltungs-ID zur Verfügung stellt. Wenn Sie C# verwenden, lesen Sie das Beispiel unten.

Alternativ können Sie die Rest-API verwenden und eine Post-Anforderung an [`/conversations`](https://docs.microsoft.com/azure/bot-service/rest-api/bot-framework-rest-connector-send-and-receive-messages?#start-a-conversation) die Ressource ausgeben.

# <a name="cnettabdotnet"></a>[C#-/.net](#tab/dotnet)

Der folgende Codeausschnitt stammt aus [diesem Beispiel](https://github.com/OfficeDev/microsoft-teams-sample-complete-csharp/blob/32c39268d60078ef54f21fb3c6f42d122b97da22/template-bot-master-csharp/src/dialogs/examples/teams/ProactiveMsgTo1to1Dialog.cs).


```csharp
using Microsoft.Bot.Builder.Dialogs;
using Microsoft.Bot.Connector;
using Microsoft.Bot.Connector.Teams.Models;
using Microsoft.Teams.TemplateBotCSharp.Properties;
using System;
using System.Threading.Tasks;

namespace Microsoft.Teams.TemplateBotCSharp.Dialogs
{
    [Serializable]
    public class ProactiveMsgTo1to1Dialog : IDialog<object>
    {
        public async Task StartAsync(IDialogContext context)
        {
            if (context == null)
            {
                throw new ArgumentNullException(nameof(context));
            }

            var channelData = context.Activity.GetChannelData<TeamsChannelData>();
            var message = Activity.CreateMessageActivity();
            message.Text = "Hello World";

            var conversationParameters = new ConversationParameters
            {
                  IsGroup = true,
                  ChannelData = new TeamsChannelData
                  {
                      Channel = new ChannelInfo(channelData.Channel.Id),
                  },
                  Activity = (Activity) message
            };

            MicrosoftAppCredentials.TrustServiceUrl(serviceUrl, DateTime.MaxValue);
            var connectorClient = new ConnectorClient(new Uri(activity.ServiceUrl));
            var response = await connectorClient.Conversations.CreateConversationAsync(conversationParameters);

            context.Done<object>(null);
        }
    }
}
```

# <a name="javascripttabjavascript"></a>[JavaScript](#tab/javascript)

In diesem Beispiel wird das NPM [-Paket botbuilder-Teams](https://www.npmjs.com/package/botbuilder-teams) verwendet. Der folgende Codeausschnitt stammt aus [teamsConversationBot. js](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/javascript_nodejs/57.teams-conversation-bot/bots/teamsConversationBot.js).

[!code-javascript[messageAllMembersAsync](~/../botbuilder-samples/samples/javascript_nodejs/57.teams-conversation-bot/bots/teamsConversationBot.js?range=115-134&highlight=13-15)]

# <a name="pythontabpython"></a>[Python](#tab/python)

[!code-python[message-all-members](~/../botbuilder-samples/samples/python/57.teams-conversation-bot/bots/teams_conversation_bot.py?range=101-135)]

---
