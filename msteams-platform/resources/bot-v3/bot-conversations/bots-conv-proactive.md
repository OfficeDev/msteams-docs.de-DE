---
title: Proaktive Nachrichten
description: Beschreibt, wie Bots eine Unterhaltung in Microsoft Teams
ms.topic: conceptual
ms.localizationpriority: medium
keywords: Teams-Szenarien – Proaktiver Bot für Messaging-Unterhaltungen
ms.openlocfilehash: c84b504fc6dba84f33ecaf76a0ce0cdebea82255
ms.sourcegitcommit: 22c9e44437720d30c992a4a3626a2a9f745983c1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/03/2021
ms.locfileid: "60720064"
---
# <a name="proactive-messaging-for-bots"></a>Proaktives Messaging für Bots

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Eine proaktive Nachricht ist eine Nachricht, die von einem Bot gesendet wird, um eine Unterhaltung zu starten. Vielleicht möchten Sie, dass Ihr Bot aus verschiedenen Gründen eine Unterhaltung beginnt, darunter:

* Willkommensnachrichten für persönliche Bot-Unterhaltungen
* Abstimmungsantworten
* Externe Ereignisbenachrichtigungen

Das Senden einer Nachricht zum Starten eines neuen Unterhaltungsthreads unterscheidet sich vom Senden einer Nachricht als Reaktion auf eine vorhandene Unterhaltung: Wenn Ihr Bot eine neue Unterhaltung startet, gibt es keine bereits vorhandene Unterhaltung, in der die Nachricht gesendet werden kann. Um eine proaktive Nachricht zu senden, müssen Sie:

1. [Entscheiden, was Sie sagen werden](#best-practices-for-proactive-messaging)
1. [Abrufen der eindeutigen ID und Mandanten-ID des Benutzers](#obtain-necessary-user-information)
1. [Senden der Nachricht](#examples)

Beim Erstellen proaktiver Nachrichten **müssen** Sie `MicrosoftAppCredentials.TrustServiceUrl` die Dienst-URL aufrufen und übergeben, bevor Sie die `ConnectorClient` zum Senden der Nachricht verwendete Erstellen. Wenn Sie dies nicht tun, wird eine `401: Unauthorized` Antwort von Ihrer App empfangen. Weitere Informationen finden Sie [in den Beispielen unten.](#net-example-from-this-sample)

## <a name="best-practices-for-proactive-messaging"></a>Bewährte Methoden für proaktives Messaging

Das Senden proaktiver Nachrichten ist eine effektive Möglichkeit, mit Ihren Benutzern zu kommunizieren. Aus Sicht des Benutzers wird die Nachricht jedoch nicht angezeigt. Wenn eine Willkommensnachricht vorhanden ist, ist es das erste Mal, dass sie mit Ihrer App interagiert haben. Es ist wichtig, diese Funktion zu verwenden und dem Benutzer die vollständigen Informationen bereitzustellen, um den Zweck dieser Nachricht zu verstehen.

Proaktive Nachrichten können generell in zwei Kategorien unterteilt werden: Willkommensnachrichten und Benachrichtigungen.

### <a name="welcome-messages"></a>Willkommensnachrichten

Wenn Sie proaktives Messaging verwenden, um eine Willkommensnachricht an einen Benutzer zu senden, stellen Sie sicher, dass die Nachricht aus Sicht des Benutzers nicht empfangen wird. Wenn eine Willkommensnachricht vorhanden ist, ist es das erste Mal, dass sie mit Ihrer App interagiert haben. Die besten Willkommensnachrichten umfassen:

* **Warum er diese Nachricht empfängt:** Dem Benutzer sollte klar sein, warum er diese Nachricht empfängt. Wenn Ihr Bot in einem Kanal installiert wurde und Sie eine Willkommensnachricht an alle Benutzer gesendet haben, teilen Sie ihnen mit, in welchem Kanal er installiert wurde und wer ihn installiert hat.
* **Was bieten Sie an:** Was können sie mit Ihrer App tun? Welchen Wert können Sie ihnen bieten?
* **Was sollten sie als Nächstes tun:** Laden Sie sie ein, einen Befehl auszuprobieren oder auf irgendeine Weise mit Ihrer App zu interagieren.

### <a name="notification-messages"></a>Benachrichtigungen

Wenn Sie proaktives Messaging verwenden, um Benachrichtigungen zu senden, müssen Sie sicherstellen, dass Ihre Benutzer einen klaren Weg haben, allgemeine Aktionen basierend auf Ihrer Benachrichtigung auszuführen, und ein klares Verständnis dafür haben, warum die Benachrichtigung aufgetreten ist. Gute Benachrichtigungen umfassen in der Regel Folgendes:

* **Was passiert ist:** Ein eindeutiger Hinweis darauf, was passiert ist, um die Benachrichtigung zu verursachen.
* **Was passiert ist mit:** Es sollte klar sein, welches Element/was aktualisiert wurde, um die Benachrichtigung zu verursachen.
* **Wer:** Wer die Aktion ausgeführt, durch die die Benachrichtigung gesendet wurde?
* **Was sie dagegen tun können:** Erleichtern Sie Es Ihren Benutzern, Aktionen basierend auf Ihren Benachrichtigungen zu ergreifen.
* **Wie sie sich abmelden können:** Geben Sie einen Pfad für Benutzer an, um sich von zusätzlichen Benachrichtigungen abzumelden.

## <a name="obtain-necessary-user-information"></a>Abrufen der erforderlichen Benutzerinformationen

Bots können neue Unterhaltungen mit einem einzelnen Microsoft Teams Benutzer erstellen, indem sie die *eindeutige ID* und *Mandanten-ID* des Benutzers abrufen. Sie können diese Werte mithilfe einer der folgenden Methoden abrufen:

* Durch [Abrufen der Teamliste](~/resources/bot-v3/bots-context.md#fetch-the-team-roster) aus einem Kanal wird Ihre App installiert.
* Durch zwischenspeichern, wenn ein Benutzer [mit Ihrem Bot in einem Kanal interagiert.](~/resources/bot-v3/bot-conversations/bots-conv-channel.md)
* Wenn ein Benutzer [in einer Kanalunterhaltung @mentioned](~/resources/bot-v3/bot-conversations/bots-conv-channel.md#-mentions) wird, ist der Bot Teil davon.
* Durch zwischenspeichern, wenn Sie [das `conversationUpdate` ](~/resources/bot-v3/bots-notifications.md#team-member-or-bot-addition) Ereignis erhalten, wenn Ihre App in einem persönlichen Bereich installiert wird oder neue Mitglieder zu einem Kanal- oder Gruppenchat hinzugefügt werden.

### <a name="proactively-install-your-app-using-graph"></a>Proaktives Installieren Ihrer App mit Graph

> [!Note]
> Die proaktive Installation von Apps mithilfe von Graph befindet sich derzeit in der Betaversion.

Gelegentlich kann es erforderlich sein, proaktiv Benutzer zu kommunizieren, die Ihre App zuvor nicht installiert oder mit ihr interagiert haben. Sie möchten z. B. den [Unternehmenskommunikator](~/samples/app-templates.md#company-communicator) verwenden, um Nachrichten an Ihre gesamte Organisation zu senden. In diesem Szenario können Sie die Graph-API verwenden, um Ihre App proaktiv für Ihre Benutzer zu installieren und dann die erforderlichen Werte aus dem Ereignis zwischenzuspeichern, `conversationUpdate` das Ihre App bei der Installation erhält.

Sie können nur Apps installieren, die sich im App-Katalog Ihrer Organisation oder im Teams App Store befinden.

Ausführliche Informationen finden Sie in der Dokumentation zum installieren von [Apps für Benutzer](/graph/api/userteamwork-post-installedapps?view=graph-rest-1.0&tabs=http&preserve-view=true) in der Graph. Es gibt auch ein [Beispiel in .NET](https://github.com/microsoftgraph/contoso-airlines-teams-sample/blob/283523d45f5ce416111dfc34b8e49728b5012739/project/Models/GraphService.cs#L176).

## <a name="examples"></a>Beispiele

Stellen Sie sicher, dass Sie sich authentifizieren und über ein Bearertoken verfügen, bevor Sie eine neue Unterhaltung mithilfe der REST-API erstellen.

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

Diese ID ist die eindeutige Unterhaltungs-ID des persönlichen Chats. Store diesen Wert für zukünftige Interaktionen mit dem Benutzer wieder.

### <a name="using-net"></a>Verwenden von .NET

In diesem Beispiel wird das [Paket "Microsoft.Bot.Connector.Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) NuGet" verwendet.

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

### <a name="using-nodejs"></a>Verwenden von Node.js

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

Der von Ihrem Team hinzugefügte Bot kann Beiträge in einen Kanal versenden, um eine neue Antwortkette zu erstellen. Wenn Sie das Node.js Teams SDK verwenden, verwenden `startReplyChain()` Sie , um eine vollständig ausgefüllte Adresse mit der richtigen Aktivitäts-ID und Unterhaltungs-ID zu erhalten. Wenn Sie C# verwenden, sehen Sie sich das folgende Beispiel an.

Alternativ können Sie die REST-API verwenden und eine POST-Anforderung an die [`/conversations`](/azure/bot-service/rest-api/bot-framework-rest-connector-send-and-receive-messages?#start-a-conversation) Ressource ausgeben.

### <a name="net-example-from-this-sample"></a>.NET-Beispiel (aus [diesem Beispiel)](https://github.com/OfficeDev/microsoft-teams-sample-complete-csharp/blob/32c39268d60078ef54f21fb3c6f42d122b97da22/template-bot-master-csharp/src/dialogs/examples/teams/ProactiveMsgTo1to1Dialog.cs)

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
