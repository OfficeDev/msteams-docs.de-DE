---
title: Proaktive Nachrichten
description: Beschreibt, dass Bots eine Konversation in Microsoft Teams
ms.topic: conceptual
localization_priority: Normal
keywords: Teams Szenarien proaktive Messaging-Konversation Bot
ms.openlocfilehash: baf148d0f4d0a669de582dfca70ed5d5bed0274c
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566789"
---
# <a name="proactive-messaging-for-bots"></a>Proaktives Messaging für Bots

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Eine proaktive Nachricht ist eine Nachricht, die von einem Bot gesendet wird, um eine Unterhaltung zu starten. Vielleicht möchten Sie, dass Ihr Bot aus verschiedenen Gründen eine Unterhaltung beginnt, darunter:

* Willkommensbotschaften für persönliche Bot-Gespräche.
* Umfrageantworten.
* Externe Ereignisbenachrichtigungen.

Das Senden einer Nachricht zum Starten eines neuen Unterhaltungsthreads unterscheidet sich von dem Senden einer Nachricht als Antwort auf eine vorhandene Unterhaltung: Wenn Ihr Bot eine neue Unterhaltung startet, gibt es keine bereits vorhandene Unterhaltung, an die die Nachricht gesendet werden kann. Um eine proaktive Nachricht zu senden, müssen Sie:

1. [Entscheiden Sie, was Sie sagen werden](#best-practices-for-proactive-messaging)
1. [Abrufen der eindeutigen ID und Mandanten-ID des Benutzers](#obtain-necessary-user-information)
1. [Senden der Nachricht](#examples)

Beim Erstellen proaktiver Nachrichten **müssen** Sie anrufen `MicrosoftAppCredentials.TrustServiceUrl` und die Dienst-URL übergeben, bevor Sie die `ConnectorClient` zum Senden der Nachricht verwenden. Andernfalls erhält Ihre App eine `401: Unauthorized` Antwort. Weitere Informationen finden Sie [in den folgenden Beispielen](#net-example-from-this-sample).

## <a name="best-practices-for-proactive-messaging"></a>Bewährte Methoden für proaktives Messaging

Das Senden proaktiver Nachrichten an Benutzer kann eine sehr effektive Möglichkeit sein, mit Ihren Benutzern zu kommunizieren. Aus ihrer Sicht kann diese Nachricht jedoch völlig unaufgefordert zu ihnen kommen, und im Falle von Begrüßungsnachrichten wird es das erste Mal sein, dass sie mit Ihrer App interagieren. Daher ist es sehr wichtig, diese Funktionalität sparsam zu nutzen (Spam für Ihre Benutzer) und ihnen genügend Informationen zur Verfügung zu stellen, damit sie verstehen können, warum sie informiert werden.

Proaktive Nachrichten können generell in zwei Kategorien unterteilt werden: Willkommensnachrichten und Benachrichtigungen.

### <a name="welcome-messages"></a>Willkommensnachrichten

Wenn Sie proaktives Messaging verwenden, um eine Willkommensnachricht an einen Benutzer zu senden, müssen Sie bedenken, dass sie für die meisten Personen, die die Nachricht erhalten, keinen Kontext haben, warum sie sie erhalten. Dies ist auch das erste Mal, dass sie mit Ihrer App interagiert haben. es ist Ihre Chance, einen guten ersten Eindruck zu schaffen. Zu den besten Willkommensbotschaften gehören:

* **Warum erhalten sie diese Nachricht?** Es sollte dem Benutzer sehr klar sein, warum er die Nachricht erhält. Wenn Ihr Bot in einem Kanal installiert wurde und Sie eine Willkommensnachricht an alle Benutzer gesendet haben, teilen Sie ihnen mit, in welchem Kanal er installiert wurde und wer ihn möglicherweise installiert hat.
* **Was bieten Sie an?** Was können sie mit Ihrer App tun? Welchen Wert können Sie ihnen bringen?
* **Was sollen sie als nächstes tun?** Bitten Sie sie, einen Befehl auszuprobieren oder in irgendeiner Weise mit Ihrer App zu interagieren.

### <a name="notification-messages"></a>Benachrichtigungen

Wenn Sie proaktives Messaging zum Senden von Benachrichtigungen verwenden, müssen Sie sicherstellen, dass Ihre Benutzer über einen klaren Pfad verfügen, um basierend auf Ihrer Benachrichtigung allgemeine Aktionen zu ergreifen und ein klares Verständnis dafür zu haben, warum die Benachrichtigung aufgetreten ist. Gute Benachrichtigungen umfassen in der Regel:

* **Was ist passiert.** Ein klarer Hinweis darauf, was die Meldung verursacht hat.
* **Was es passiert ist.** Es sollte klar sein, welches Element/Ding aktualisiert wurde, um die Benachrichtigung zu verursachen.
* **Wer hat es getan.** Wer die Aktion ergriffen, die dazu führte, dass die Benachrichtigung gesendet wurde.
* **Was sie dagegen tun können.** Machen Sie es Ihren Benutzern leicht, Aktionen basierend auf Ihren Benachrichtigungen durchzuführen.
* **Wie sie sich abmelden können.** Sie müssen einen Pfad angeben, damit Benutzer zusätzliche Benachrichtigungen deaktivieren können.

## <a name="obtain-necessary-user-information"></a>Erforderliche Benutzerinformationen abrufen

Bots können neue Unterhaltungen mit einem einzelnen Microsoft Teams Benutzer erstellen, indem sie die *eindeutige ID* und *Mandanten-ID* des Benutzers abrufen. Sie können diese Werte mit einer der folgenden Methoden abrufen:

* Durch [Abrufen des Team-Rosters](~/resources/bot-v3/bots-context.md#fetch-the-team-roster) von einem Kanal, in dem Ihre App installiert ist.
* Indem sie zwischenspeichern, wenn ein Benutzer [mit Ihrem Bot in einem Kanal interagiert.](~/resources/bot-v3/bot-conversations/bots-conv-channel.md)
* Wenn ein Benutzer [in einer Kanalunterhaltung @mentioned](~/resources/bot-v3/bot-conversations/bots-conv-channel.md#-mentions) wird, ist der Bot Ein Teil davon.
* Indem Sie sie [zwischenspeichern, `conversationUpdate` ](~/resources/bot-v3/bots-notifications.md#team-member-or-bot-addition) wenn Sie das Ereignis erhalten, wenn Ihre App in einem persönlichen Bereich installiert ist oder neue Mitglieder zu einem Kanal oder Gruppenchat hinzugefügt werden.

### <a name="proactively-install-your-app-using-graph"></a>Proaktive Installation Ihrer App mithilfe Graph

> [!Note]
> Die proaktive Installation von Apps mit Graph befindet sich derzeit in der Betaversion.

Gelegentlich kann es erforderlich sein, Benutzer, die zuvor nicht installiert oder mit Ihrer App interagiert haben, proaktiv zu melden. Sie möchten z. B. den [Unternehmenskommunikator](~/samples/app-templates.md#company-communicator) verwenden, um Nachrichten an Ihre gesamte Organisation zu senden. In diesem Szenario können Sie die Graph-API verwenden, um Ihre App proaktiv für Ihre Benutzer zu installieren, und dann die erforderlichen Werte aus dem Ereignis zwischenspeichern, das `conversationUpdate` Ihre App bei der Installation erhält.

Sie können nur Apps installieren, die sich in Ihrem Organisations-App-Katalog befinden, oder im Teams App Store.

Ausführliche Informationen finden Sie unter Installieren von [Apps für Benutzer](/graph/teams-proactive-messaging) in der Graph-Dokumentation. Es gibt auch ein [Beispiel in .NET](https://github.com/microsoftgraph/contoso-airlines-teams-sample/blob/283523d45f5ce416111dfc34b8e49728b5012739/project/Models/GraphService.cs#L176).

## <a name="examples"></a>Beispiele

Stellen Sie sicher, dass Sie sich authentifizieren und über ein Inhabertoken verfügen, bevor Sie eine neue Unterhaltung mithilfe der REST-API erstellen.

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

Sie müssen die Benutzer-ID und die Mandanten-ID angeben. Wenn der Aufruf erfolgreich ist, wird die API mit dem folgenden Antwortobjekt zurückgegeben.

```json
{
  "id":"a:1qhNLqpUtmuI6U35gzjsJn7uRnCkW8NiZALHfN8AMxdbprS1uta2aT-jytfIlsZR3UZeg3TsIONNInBHsdjzj3PtfHuhkxxvS1jZZ61UAbw8fIdXcNSJyTJm7YvHFOgxo"
}
```

Diese ID ist die eindeutige Konversations-ID des persönlichen Chats. Speichern Sie diesen Wert, und verwenden Sie ihn für zukünftige Interaktionen mit dem Benutzer.

### <a name="using-net"></a>Verwenden von .NET

In diesem Beispiel wird das [NuGet-Paket Microsoft.Bot.Connector.Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) verwendet.

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

### <a name="using-nodejs"></a>Verwenden Node.js

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

## <a name="creating-a-channel-conversation"></a>Erstellen einer Kanalunterhaltung

Der von Ihrem Team hinzugefügte Bot kann Beiträge in einen Kanal versenden, um eine neue Antwortkette zu erstellen. Wenn Sie das Node.js Teams SDK verwenden, verwenden Sie diese Verwendung, die `startReplyChain()` Ihnen eine voll ausgefüllte Adresse mit der richtigen Aktivitäts-ID und Konversations-ID gibt. Wenn Sie c- verwenden, lesen Sie das folgende Beispiel.

Alternativ können Sie die REST-API verwenden und eine POST-Anforderung an die [`/conversations`](/azure/bot-service/rest-api/bot-framework-rest-connector-send-and-receive-messages?#start-a-conversation) Ressource ausstellen.

### <a name="net-example-from-this-sample"></a>.NET-Beispiel (aus [diesem Beispiel](https://github.com/OfficeDev/microsoft-teams-sample-complete-csharp/blob/32c39268d60078ef54f21fb3c6f42d122b97da22/template-bot-master-csharp/src/dialogs/examples/teams/ProactiveMsgTo1to1Dialog.cs))

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

## <a name="see-also"></a>Siehe auch

[Bot Framework-Beispiele](https://github.com/Microsoft/BotBuilder-Samples/blob/master/README.md)