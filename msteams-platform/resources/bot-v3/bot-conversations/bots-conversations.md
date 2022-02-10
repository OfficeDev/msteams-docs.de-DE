---
title: Senden und Empfangen von Nachrichten mit einem Bot
description: Beschreibt, wie Nachrichten mit Bots in Microsoft Teams gesendet und empfangen werden
ms.topic: overview
ms.localizationpriority: medium
keywords: Teams-Bots-Nachrichten
ms.date: 05/20/2019
ms.openlocfilehash: ce3d3d1dd39707d08c720e75c67ec61b606f676a
ms.sourcegitcommit: 90587b1ec04bf20d716ed6feb8ccca4313e87f8c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/10/2022
ms.locfileid: "62518499"
---
# <a name="have-a-conversation-with-a-microsoft-teams-bot"></a>Unterhaltung mit einem Microsoft Teams Bot

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Eine Unterhaltung ist eine Reihe von Nachrichten, die zwischen Ihrem Bot und einem oder mehreren Benutzern gesendet werden. In Teams gibt es drei Arten von Unterhaltungen (auch als Bereiche bezeichnet):

* `teams` Auch kanalunterhaltungen genannt, sichtbar für alle Mitglieder des Kanals.
* `personal` Unterhaltungen zwischen Bots und einem einzelnen Benutzer.
* `groupChat` Chatten Sie zwischen einem Bot und zwei oder mehr Benutzern.

Ein Bot verhält sich je nach Art der Unterhaltung, an der er beteiligt ist, geringfügig anders:

* [Bots in Kanal- und Gruppenchatunterhaltungen](~/resources/bot-v3/bot-conversations/bots-conv-channel.md) erfordern, dass der Benutzer den Bot @mention, um ihn in einem Kanal aufzurufen.
* [Bots in Einzelbenutzerunterhaltungen](~/resources/bot-v3/bot-conversations/bots-conv-personal.md) erfordern keine @mention – der Benutzer kann einfach eingeben.

Damit der Bot in einem bestimmten Bereich funktioniert, sollte er als Unterstützung für diesen Bereich im Manifest aufgeführt werden. Bereiche werden in der [Manifestreferenz](~/resources/schema/manifest-schema.md) definiert und weiter erläutert.

## <a name="proactive-messages"></a>Proaktive Nachrichten

Bots können an einer Unterhaltung teilnehmen oder eine initiieren. Der Großteil der Kommunikation erfolgt als Reaktion auf eine andere Nachricht. Wenn ein Bot eine Unterhaltung initiiert, wird er als *proaktive Nachricht* bezeichnet. Dazu gehören:

* Willkommensnachrichten
* Ereignisbenachrichtigungen
* Abrufen von Nachrichten

## <a name="conversation-basics"></a>Grundlagen zu Unterhaltungen

Jede Nachricht ist ein `Activity`-Objekt vom Typ `messageType: message`. Wenn ein Benutzer eine Nachricht sendet, postet Teams die Nachricht auf Ihrem Bot. Spezifisch erfolgt dies durch Senden eines JSON-Objekts an den Nachrichtenendpunkt des Bots. Ihr Bot überprüft die Nachricht, um ihren Typ zu ermitteln, und antwortet entsprechend.

Bots unterstützen auch Nachrichten im Ereignisstil. Weitere Informationen finden Sie unter [Behandeln von Botereignissen in Microsoft Teams](~/resources/bot-v3/bots-notifications.md). Die Spracherkennung wird derzeit nicht unterstützt.

Nachrichten sind in allen Bereichen größtenteils gleich, aber es gibt Unterschiede in der Art und Weise, wie auf den Bot in der Benutzeroberfläche zugegriffen wird, und Unterschiede im Hintergrund, die Sie kennen müssen.

Grundlegende Unterhaltungen werden über den Bot Framework-Connector verarbeitet, eine einzelne REST-API, mit der Ihr Bot mit Teams und anderen Kanälen kommunizieren kann. Das Bot Builder SDK bietet einfachen Zugriff auf diese API, zusätzliche Funktionen zum Verwalten von Unterhaltungsfluss und -zustand sowie einfache Möglichkeiten, kognitive Dienste wie die Verarbeitung natürlicher Sprache (Natural Language Processing, NLP) zu integrieren.

## <a name="message-content"></a>Nachrichteninhalt

Ihr Bot kann Rich-Text, Bilder und Karten senden. Benutzer können Rich-Text und Bilder an Ihren Bot senden. Sie können den Inhaltstyp angeben, den Ihr Bot auf der Seite Microsoft Teams Einstellungen für Ihren Bot verarbeiten kann.

| Format | Vom Benutzer zum Bot  | Vom Bot zum Benutzer |  Notes |
| --- | :---: | :---: | --- |
| Rich-Text  | ✔ | ✔ |  |
| Bilder | ✔ | ✔ | Maximal 1024×1024 und 1 MB im PNG-, JPEG- oder GIF-Format; Animierte GIF-Dateien werden nicht unterstützt. |
| Karten | ✖ | ✔ | Unterstützte Karten finden Sie in der [Teams-Kartenreferenz](~/task-modules-and-cards/cards/cards-reference.md). |
| Emojis | ✖ | ✔ | Teams unterstützt zurzeit Emojis über UTF-16, z. B. U+1F600 für das graunen Gesicht. |
|

Weitere Informationen zu den Vom Bot Framework unterstützten Bot-Interaktionstypen, auf denen Bots in Teams basieren, finden Sie in der Bot Framework-Dokumentation zum [Unterhaltungsfluss](/azure/bot-service/dotnet/bot-builder-dotnet-manage-conversation-flow?view=azure-bot-service-3.0&preserve-view=true) und verwandten Konzepten in der Dokumentation für [das Bot Builder SDK für .NET](/azure/bot-service/dotnet/bot-builder-dotnet-overview?view=azure-bot-service-3.0&preserve-view=true) und [das Bot Builder SDK für Node.js](/azure/bot-service/nodejs/bot-builder-nodejs-overview?view=azure-bot-service-3.0&preserve-view=true).

## <a name="message-formatting"></a>Mitteilungsformatierung

Sie können die optionale [`TextFormat`](/azure/bot-service/dotnet/bot-builder-dotnet-create-messages?view=azure-bot-service-3.0#customizing-a-message&preserve-view=true) Eigenschaft von a `message` festlegen, um zu steuern, wie der Textinhalt Ihrer Nachricht gerendert wird. Eine ausführliche Beschreibung der unterstützten Formatierung in Botnachrichten finden Sie unter [Nachrichtenformatierung](~/resources/bot-v3/bots-message-format.md) .
Sie können die optionale [`TextFormat`](/azure/bot-service/dotnet/bot-builder-dotnet-create-messages?view=azure-bot-service-3.0#customizing-a-message&preserve-view=true) Eigenschaft festlegen, um zu steuern, wie der Textinhalt Ihrer Nachricht gerendert wird.

Ausführliche Informationen dazu, wie Teams Textformatierungen in Teams unterstützt, finden Sie unter [Textformatierung in Botnachrichten](~/resources/bot-v3/bots-text-formats.md).

Weitere Informationen zum Formatieren von Karten in Nachrichten finden Sie unter [Kartenformatierung](~/task-modules-and-cards/cards/cards-format.md).

## <a name="picture-messages"></a>Bildnachrichten

Bilder werden durch Hinzufügen von Anlagen zu einer Nachricht gesendet. Weitere Informationen zu Anlagen finden Sie in der [Bot Framework-Dokumentation](/azure/bot-service/dotnet/bot-builder-dotnet-add-media-attachments?view=azure-bot-service-3.0&preserve-view=true).

Bilder können höchstens 1024×1024 und 1 MB im PNG-, JPEG- oder GIF-Format sein. Animierte GIF-Dateien werden nicht unterstützt.

Es wird empfohlen, die Höhe und Breite jedes Bilds mithilfe von XML anzugeben. Wenn Sie Markdown verwenden, beträgt die Bildgröße standardmäßig 256×256. Beispiel:

* Verwenden von `<img src="http://aka.ms/Fo983c" alt="Duck on a rock" height="150" width="223"></img>`
* `![Duck on a rock](http://aka.ms/Fo983c)` nicht verwenden

## <a name="receiving-messages"></a>Empfangen von Nachrichten

Je nachdem, welche Bereiche deklariert werden, kann Ihr Bot Nachrichten in den folgenden Kontexten empfangen:

* **Persönlicher Chat** Benutzer können in einer privaten Unterhaltung mit einem Bot interagieren, indem sie einfach den hinzugefügten Bot im Chatverlauf auswählen oder den Namen oder die App-ID in das Feld "An:" in einen neuen Chat eingeben.
* **Kanäle** Ein Bot kann in einem Kanal ("@_botname_") erwähnt werden, wenn er dem Team hinzugefügt wurde. Beachten Sie, dass für zusätzliche Antworten auf einen Bot in einem Kanal der Bot erwähnt werden muss. Sie antwortet nicht auf Antworten, in denen sie nicht erwähnt wird.

Bei eingehenden Nachrichten empfängt Ihr Bot ein [Activity-Objekt](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0#activity-object&preserve-view=true) vom Typ `messageType: message`. Obwohl das `Activity` Objekt andere Arten von Informationen enthalten kann, z. B. [Kanalaktualisierungen](~/resources/bot-v3/bots-notifications.md#channel-updates) , die an Ihren Bot gesendet werden, stellt der Typ die `message` Kommunikation zwischen Bot und Benutzer dar.

Ihr Bot empfängt eine Nutzlast, die die Benutzernachricht `Text` sowie andere Informationen über den Benutzer, die Quelle der Nachricht und Teams Informationen enthält. Beachten Sie Folgendes:

* `timestamp` Datum und Uhrzeit der Nachricht in koordinierter Weltzeit (UTC).
* `localTimestamp` Datum und Uhrzeit der Nachricht in der Zeitzone des Absenders.
* `channelId` Immer "msteams". Dies bezieht sich auf einen Bot-Framework-Kanal, nicht auf einen Teams-Kanal.
* `from.id` Eine eindeutige und verschlüsselte ID für diesen Benutzer für Ihren Bot; als Schlüssel geeignet, wenn Ihre App Benutzerdaten speichern muss. Es ist einzigartig für Ihren Bot und kann nicht direkt außerhalb Ihrer Bot-Instanz auf sinnvolle Weise verwendet werden, um diesen Benutzer zu identifizieren.
* `channelData.tenant.id` Die Mandanten-ID für den Benutzer.

> [!NOTE]
> `from.id` ist eindeutig für Ihren Bot und kann nicht direkt außerhalb Ihrer Bot-Instanz auf sinnvolle Weise verwendet werden, um diesen Benutzer zu identifizieren.

## <a name="combining-channel-and-private-interactions-with-your-bot"></a>Kombinieren von Kanal- und privaten Interaktionen mit Ihrem Bot

Bei der Interaktion in einem Kanal sollte Ihr Bot intelligent sein, bestimmte Unterhaltungen mit einem Benutzer offline zu schalten. Angenommen, ein Benutzer versucht, eine komplexe Aufgabe zu koordinieren, z. B. die Planung mit einer Gruppe von Teammitgliedern. Anstatt die gesamte Sequenz von Interaktionen für den Kanal sichtbar zu haben, sollten Sie erwägen, eine persönliche Chatnachricht an den Benutzer zu senden. Ihr Bot sollte in der Lage sein, den Benutzer problemlos zwischen persönlichen Unterhaltungen und Kanalunterhaltungen zu wechseln, ohne den Status zu verlieren.

> [!NOTE]
>Vergessen Sie nicht, den Kanal zu aktualisieren, wenn die Interaktion abgeschlossen ist, um die anderen Teammitglieder zu benachrichtigen.

## <a name="full-inbound-schema-example"></a>Beispiel für ein vollständiges eingehendes Schema

```json
{
    "type": "message",
    "id": "1485983408511",
    "timestamp": "2017-02-01T21:10:07.437Z",
    "localTimestamp": "2017-02-01T14:10:07.437-07:00",
    "serviceUrl": "https://smba.trafficmanager.net/amer/",
    "channelId": "msteams",
    "from": {
        "id": "29:1XJKJMvc5GBtc2JwZq0oj8tHZmzrQgFmB39ATiQWA85gQtHieVkKilBZ9XHoq9j7Zaqt7CZ-NJWi7me2kHTL3Bw",
        "name": "Megan Bowen",
        "aadObjectId": "7faf8ab2-3d56-4244-b585-20c8a42ed2b8"
    },
    "conversation": {
        "conversationType": "personal",
        "id": "a:17I0kl9EkpE1O9PH5TWrzrLNwnWWcfrU7QZjKR0WSfOpzbfcAg2IaydGElSo10tVr4C7Fc6GtieTJX663WuJCc1uA83n4CSrHSgGBj5XNYLcVlJAs2ZX8DbYBPck201w-"
    },
    "recipient": {
        "id": "28:c9e8c047-2a74-40a2-b28a-b162d5f5327c",
        "name": "Teams TestBot"
    },
    "textFormat": "plain",
    "text": "Hello Teams TestBot",
    "entities": [
      { 
        "locale": "en-US",
        "country": "US",
        "platform": "Windows",
        "timezone": "America/Los_Angeles",
        "type": "clientInfo"
      }
    ],
    "channelData": {
        "tenant": {
            "id": "72f988bf-86f1-41af-91ab-2d7cd011db47"
        }
    },
    "locale": "en-US"
}
```

> [!NOTE]
> Das Textfeld für eingehende Nachrichten enthält manchmal Erwähnungen. Achten Sie darauf, diese ordnungsgemäß zu überprüfen und zu entfernen. Weitere Informationen finden Sie unter ["Erwähnungen"](~/resources/bot-v3/bot-conversations/bots-conv-channel.md#-mentions).

## <a name="teams-channel-data"></a>Teams Kanaldaten

Das `channelData` Objekt enthält Teams-spezifische Informationen und ist die endgültige Quelle für Team- und Kanal-IDs. Sie sollten diese IDs zwischenspeichern und als Schlüssel für den lokalen Speicher verwenden.

Ein typisches channelData-Objekt in einer Aktivität, die an Ihren Bot gesendet wird, enthält die folgenden Informationen:

* `eventType`Teams Ereignistyp; wird nur bei [Kanaländerungsereignissen](~/resources/bot-v3/bots-notifications.md#channel-updates) übergeben.
* `tenant.id`Microsoft Azure Active Directory (Azure AD) Mandanten-ID; wird in allen Kontexten übergeben.
* `team` Wird nur in Kanalkontexten übergeben, nicht im persönlichen Chat.
  * `id` GUID für den Kanal.
  * `name` Name des Teams; wird nur in Fällen von [Team-Umbenennungsereignissen](~/resources/bot-v3/bots-notifications.md#team-name-updates) übergeben.
* `channel` Wird nur in Kanalkontexten übergeben, wenn der Bot erwähnt wird, oder für Ereignisse in Kanälen in Teams, in denen der Bot hinzugefügt wurde.
  * `id` GUID für den Kanal.
  * `name` Kanalname; wird nur in Fällen von [Kanaländerungsereignissen](~/resources/bot-v3/bots-notifications.md#channel-updates) übergeben.
* `channelData.teamsTeamId` Veraltet. Diese Eigenschaft ist nur aus Gründen der Abwärtskompatibilität enthalten.
* `channelData.teamsChannelId` Veraltet. Diese Eigenschaft ist nur aus Gründen der Abwärtskompatibilität enthalten.

### <a name="example-channeldata-object-channelcreated-event"></a>ChannelData-Beispielobjekt (channelCreated-Ereignis)

```json
"channelData": {
    "eventType": "channelCreated",
    "tenant": {
        "id": "72f988bf-86f1-41af-91ab-2d7cd011db47"
    },
    "channel": {
        "id": "19:693ecdb923ac4458a5c23661b505fc84@thread.skype",
        "name": "My New Channel"
    },
    "team": {
        "id": "19:693ecdb923ac4458a5c23661b505fc84@thread.skype"
    }
}
```

### <a name="net-example"></a>.NET-Beispiel

Das [Paket "Microsoft.Bot.Connector.Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) NuGet" stellt ein spezielles `TeamsChannelData` Objekt bereit, das Eigenschaften für den Zugriff auf Teams-spezifische Informationen verfügbar macht.

```csharp
TeamsChannelData channelData = activity.GetChannelData<TeamsChannelData>();
string tenantId = channelData.Tenant.Id;
```

## <a name="sending-replies-to-messages"></a>Senden von Antworten auf Nachrichten

Um auf eine vorhandene Nachricht zu antworten, rufen Sie [`ReplyToActivity`](/dotnet/api/microsoft.bot.connector.conversationsextensions.replytoactivityasync?view=botbuilder-dotnet-3.0#Microsoft_Bot_Connector_ConversationsExtensions_ReplyToActivityAsync_Microsoft_Bot_Connector_IConversations_System_String_System_String_Microsoft_Bot_Connector_Activity_System_Threading_CancellationToken_&preserve-view=true) in .NET oder [`session.send`](/javascript/api/botbuilder-core/TurnContext?view=botbuilder-ts-latest&viewFallbackFrom=botbuilder-ts-3.0#sendactivities&preserve-view=true) in Node.js auf. Das Bot Builder SDK verarbeitet alle Details.

Wenn Sie die REST-API verwenden, können Sie auch den [`/v3/conversations/{conversationId}/activities/{activityId}`](/azure/bot-service/rest-api/bot-framework-rest-connector-send-and-receive-messages?view=azure-bot-service-3.0&preserve-view=true) Endpunkt aufrufen.

Der Nachrichteninhalt selbst kann einfachen Text oder einige von Bot Framework bereitgestellte [Karten und Kartenaktionen](~/task-modules-and-cards/cards/cards-actions.md) enthalten.

Bitte beachten Sie, dass Sie in Ihrem ausgehenden Schema immer dasselbe `serviceUrl` wie das empfangene Schema verwenden sollten. Beachten Sie, dass der Wert von `serviceUrl` Stabil eher stabil ist, sich aber ändern kann. Wenn eine neue Nachricht eintrifft, sollte Ihr Bot den gespeicherten Wert von `serviceUrl`überprüfen.

## <a name="updating-messages"></a>Aktualisieren von Nachrichten

Anstatt dass Ihre Nachrichten statische Momentaufnahmen von Daten sind, kann Ihr Bot Nachrichten nach dem Senden dynamisch inline aktualisieren. Sie können dynamische Nachrichtenupdates für Szenarien wie Abrufaktualisierungen, das Ändern verfügbarer Aktionen nach einem Tastendruck oder andere asynchrone Zustandsänderungen verwenden.

Die neue Nachricht muss nicht mit dem originalen Typ übereinstimmen. Wenn die ursprüngliche Nachricht beispielsweise eine Anlage enthielt, kann es sich bei der neuen Nachricht um eine einfache Textnachricht handeln.

> [!NOTE]
> Sie können nur Inhalte aktualisieren, die in Einzelanlagennachrichten und Karusselllayouts gesendet werden. Das Veröffentlichen von Updates für Nachrichten mit mehreren Anlagen im Listenlayout wird nicht unterstützt.

### <a name="rest-api"></a>REST-API

Um eine Nachrichtenaktualisierung auszustellen, führen Sie einfach eine PUT-Anforderung für den `/v3/conversations/<conversationId>/activities/<activityId>/` Endpunkt mithilfe einer bestimmten Aktivitäts-ID aus. Um dieses Szenario abzuschließen, sollten Sie die Aktivitäts-ID zwischenspeichern, die vom ursprünglichen POST-Aufruf zurückgegeben wird.

```json
PUT /v3/conversations/19%3Aja0cu120i1jod12j%40skype.net/activities/012ujdo0128
{
    "type": "message",
    "text": "This message has been updated"
}
```

### <a name="net-example"></a>.NET-Beispiel

Sie können die `UpdateActivityAsync` Methode im Bot Builder SDK verwenden, um eine vorhandene Nachricht zu aktualisieren.

```csharp
public async Task<HttpResponseMessage> Post([FromBody]Activity activity)
{
  if (activity.Type == ActivityTypes.Message)
  {
    ConnectorClient connector = new ConnectorClient(new Uri(activity.ServiceUrl));
    Activity reply = activity.CreateReply($"You sent {activity.Text} which was {activity.Text.Length} characters");
    var msgToUpdate = await connector.Conversations.ReplyToActivityAsync(reply);
    Activity updatedReply = activity.CreateReply($"This is an updated message");
    await connector.Conversations.UpdateActivityAsync(reply.Conversation.Id, msgToUpdate.Id, updatedReply);
  }
}
```

### <a name="nodejs-example"></a>Node.js Beispiel

Sie können die `session.connector.update` Methode im Bot Builder SDK verwenden, um eine vorhandene Nachricht zu aktualisieren.

```javascript
function sendCardUpdate(bot, session, originalMessage, address) {

  var origAttachment = originalMessage.data.attachments[0];
  origAttachment.content.subtitle = 'Assigned to Larry Jin';

  var updatedMsg = new builder.Message()
    .address(address)
    .textFormat(builder.TextFormat.markdown)
    .addAttachment(origAttachment)
    .toMessage();

  session.connector.update(updatedMsg, function(err, addresses) {
    if (err) {
      console.log(`Could not update the message`);
    }
  });
}
```

## <a name="starting-a-conversation-proactive-messaging"></a>Starten einer Unterhaltung (proaktives Messaging)

Sie können eine persönliche Unterhaltung mit einem Benutzer erstellen oder eine neue Antwortkette in einem Kanal für Ihren Team-Bot starten. Auf diese Weise können Sie Ihre Benutzer benachrichtigen, ohne dass sie zuerst Kontakt mit Ihrem Bot aufnehmen müssen. Weitere Informationen finden Sie in den folgenden Themen:

Weitere allgemeine Informationen zu Unterhaltungen, die von Bots gestartet werden, finden Sie unter [Proaktives Messaging für Bots](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md) .

## <a name="deleting-messages"></a>Löschen von Nachrichten

Nachrichten können mithilfe der Connectors-Methode [`delete()`](https://docs.botframework.com/node/builder/chat-reference/interfaces/_botbuilder_d_.iconnector.html#delete) im [BotBuilder SDK](/bot-framework/bot-builder-overview-getstarted) gelöscht werden.

```typescript
bot.dialog('BotDeleteMessage', function (session: builder.Session) {
  var msg = new teams.TeamsMessage(session).text("Bot will delete this message in 5 sec.")
  bot.send(msg, function (err, response) {
    if (err) {
      console.log(err);
      session.endDialog();
    }

    console.log('Proactive message response:');
    console.log(response);
    console.log('---------------------------------------------------')
    setTimeout(function () {
      var activityId: string = null;
      var messageAddress: builder.IChatConnectorAddress = null;
      if (response[0]){
        messageAddress = response[0];
        activityId = messageAddress.id;
      }

      if (activityId == null)
      {
        console.log('Message failed to send.');
        session.endDialog();
        return;
      }

      // Bot delete message
      let address: builder.IChatConnectorAddress  = {
        channelId: 'msteams',
        user: messageAddress.user,
        bot: messageAddress.bot,
        id : activityId,
        serviceUrl : (<builder.IChatConnectorAddress>session.message.address).serviceUrl,
        conversation: {
          id: session.message.address.conversation.id
        }
      };

      connector.delete(address, function (err) {
        if (err)
        {
          console.log(err);
        }
        else
        {
          console.log("Message: " + activityId + " deleted successfully.");
        }

        // Try editing deleted message would fail
        var newMsg = new builder.Message().address(address).text("To edit message.");
        connector.update(newMsg.toMessage(), function (err, address) {
          if (err)
          {
            console.log(err);
            console.log('Deleted message can not be edited.');
          }
          else
          {
            console.log("There is something wrong. Message: " + activityId + " edited successfully.");
            console.log(address);
          }

          session.endDialog();
        });
      });
    }, 5000);
  });
})
```
