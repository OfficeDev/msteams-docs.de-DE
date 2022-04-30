---
title: Senden und empfangen Sie Nachrichten mit einem Bot
description: Beschreibt das Senden und Empfangen von Nachrichten mit Bots in Microsoft Teams
ms.topic: overview
ms.localizationpriority: high
keywords: Teams-Bots-Nachrichten
ms.date: 05/20/2019
ms.openlocfilehash: dd43c31147c43c06b4f96c709fb0e5af5cd6bb41
ms.sourcegitcommit: f15bd0e90eafb00e00cf11183b129038de8354af
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/28/2022
ms.locfileid: "65111598"
---
# <a name="have-a-conversation-with-a-microsoft-teams-bot"></a>Führen Sie ein Gespräch mit einem Microsoft Teams-Bot

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Eine Unterhaltung ist eine Reihe von Nachrichten, die zwischen Ihrem Bot und einem oder mehreren Benutzern gesendet werden. In Teams gibt es drei Arten von Unterhaltungen (auch als Bereiche bezeichnet):

* `teams` Auch als Kanalunterhaltungen bezeichnet, die für alle Mitglieder des Kanals sichtbar sind.
* `personal` Gespräche zwischen Bots und einem einzelnen Benutzer.
* `groupChat` Chatten Sie zwischen einem Bot und zwei oder mehr Benutzern.

Ein Bot verhält sich etwas anders, je nachdem, an welcher Art von Konversation er beteiligt ist:

* [Bots in Kanal- und Gruppenchat-Gesprächen](~/resources/bot-v3/bot-conversations/bots-conv-channel.md) erfordern, dass der Benutzer den Bot @erwähnt, um ihn in einem Kanal aufzurufen.
* [Bots in Konversationen](~/resources/bot-v3/bot-conversations/bots-conv-personal.md) mit einzelnen Benutzern erfordern keine @Erwähnung – der Benutzer kann einfach tippen.

Damit der Bot in einem bestimmten Bereich funktioniert, sollte er im Manifest als unterstützend für diesen Bereich aufgeführt sein. Bereiche werden in der [Manifestreferenz](~/resources/schema/manifest-schema.md) definiert und weiter erläutert.

## <a name="proactive-messages"></a>Proaktive Nachrichten

Bots können an einer Unterhaltung teilnehmen oder eine unterhaltung initiieren. Die meisten Kommunikation erfolgt als Reaktion auf eine andere Nachricht. Wenn ein Bot eine Unterhaltung initiiert, wird dies als *proaktive Nachricht* bezeichnet. Dazu gehören:

* Willkommensnachrichten
* Ereignisbenachrichtigungen
* Abfragen von Nachrichten

## <a name="conversation-basics"></a>Grundlagen zu Unterhaltungen

Jede Nachricht ist ein `Activity`-Objekt vom Typ `messageType: message`. Wenn ein Benutzer eine Nachricht sendet, postet Teams die Nachricht auf Ihrem Bot. Spezifisch erfolgt dies durch Senden eines JSON-Objekts an den Nachrichtenendpunkt des Bots. Ihr Bot untersucht die Nachricht, um ihren Typ zu bestimmen und entsprechend zu reagieren.

Bots unterstützen auch Nachrichten im Ereignisstil. Weitere Informationen finden Sie unter [Behandeln von Botereignissen in Microsoft Teams](~/resources/bot-v3/bots-notifications.md). Die Spracherkennung wird derzeit nicht unterstützt.

Nachrichten sind größtenteils in allen Bereichen identisch, aber es gibt Unterschiede in der Art und Weise, wie auf den Bot in der Benutzeroberfläche zugegriffen wird, und Unterschiede im Hintergrund, die Sie kennen müssen.

Grundlegende Konversationen werden über den Bot Framework Connector abgewickelt, eine einzelne REST-API, mit der Ihr Bot mit Teams und anderen Kanälen kommunizieren kann. Das Bot Builder SDK bietet einfachen Zugriff auf diese API, zusätzliche Funktionen zur Verwaltung des Konversationsflusses und -status sowie einfache Möglichkeiten zur Integration kognitiver Dienste wie Natural Language Processing (NLP).

## <a name="message-content"></a>Nachrichteninhalt

Ihr Bot kann Rich-Text, Bilder und Karten senden. Benutzer können Rich-Text und Bilder an Ihren Bot senden. Sie können den Inhaltstyp, den Ihr Bot verarbeiten kann, auf der Microsoft Teams-Einstellungsseite für Ihren Bot angeben.

| Format | Vom Benutzer zum Bot  | Vom Bot zum Benutzer |  Anmerkungen |
| --- | :---: | :---: | --- |
| Rich-Text  | ✔ | ✔ |  |
| Bilder | ✔ | ✔ | Maximal 1024×1024 und 1 MB im PNG-, JPEG- oder GIF-Format; animierte GIFs werden nicht unterstützt. |
| Karten | ✖ | ✔ | Informationen zu unterstützten [Karten finden](~/task-modules-and-cards/cards/cards-reference.md) Sie in der Teams-Kartenreferenz. |
| Emojis | ✖ | ✔ | Teams unterstützt derzeit Emojis über UTF-16, z. B. U+1F600 für ein grinsendes Gesicht. |
|

Weitere Informationen zu den vom Bot Framework unterstützten Bot-Interaktionstypen, auf denen Bots in Teams basieren, finden Sie in der Bot Framework-Dokumentation zum [Konversationsfluss](/azure/bot-service/dotnet/bot-builder-dotnet-manage-conversation-flow?view=azure-bot-service-3.0&preserve-view=true) und verwandten Konzepten in der Dokumentation für [das Bot Builder SDK für .NET](/azure/bot-service/dotnet/bot-builder-dotnet-overview?view=azure-bot-service-3.0&preserve-view=true) und [das Bot Builder SDK für Node.js](/azure/bot-service/nodejs/bot-builder-nodejs-overview?view=azure-bot-service-3.0&preserve-view=true).

## <a name="message-formatting"></a>Mitteilungsformatierung

Sie können die optionale [`TextFormat`](/azure/bot-service/dotnet/bot-builder-dotnet-create-messages?view=azure-bot-service-3.0#customizing-a-message&preserve-view=true)Eigenschaft von a `message` festlegen, um zu steuern, wie der Textinhalt Ihrer Nachricht gerendert wird. Eine detaillierte [Beschreibung](~/resources/bot-v3/bots-message-format.md) der unterstützten Formatierung in Bot-Nachrichten finden Sie unter Nachrichtenformatierung.
Sie können die optionale [`TextFormat`](/azure/bot-service/dotnet/bot-builder-dotnet-create-messages?view=azure-bot-service-3.0#customizing-a-message&preserve-view=true)Eigenschaft festlegen, um zu steuern, wie der Textinhalt Ihrer Nachricht gerendert wird.

Ausführliche Informationen dazu, wie Teams die Textformatierung in Teams unterstützt, finden Sie unter [Textformatierung in Bot-Nachrichten](~/resources/bot-v3/bots-text-formats.md).

Weitere Informationen zum Formatieren von Karten in Nachrichten finden Sie unter [Kartenformatierung](~/task-modules-and-cards/cards/cards-format.md).

## <a name="picture-messages"></a>Bildnachrichten

Bilder werden gesendet, indem Anhänge zu einer Nachricht hinzugefügt werden. Weitere Informationen zu Anhängen finden Sie in der [Bot Framework-Dokumentation](/azure/bot-service/dotnet/bot-builder-dotnet-add-media-attachments?view=azure-bot-service-3.0&preserve-view=true).

Bilder können höchstens 1024 × 1024 und 1 MB im PNG-, JPEG- oder GIF-Format haben; animiertes GIF wird nicht unterstützt.

Wir empfehlen, dass Sie die Höhe und Breite jedes Bildes mithilfe von XML angeben. Wenn Sie Markdown verwenden, beträgt die Bildgröße standardmäßig 256 × 256. Beispiel:

* Verwenden von `<img src="http://aka.ms/Fo983c" alt="Duck on a rock" height="150" width="223"></img>`
* `![Duck on a rock](http://aka.ms/Fo983c)` nicht verwenden

## <a name="receiving-messages"></a>Nachrichten empfangen

Je nachdem, welche Bereiche deklariert sind, kann Ihr Bot Nachrichten in den folgenden Kontexten empfangen:

* **persönlicher Chat** Benutzer können in einer privaten Konversation mit einem Bot interagieren, indem sie einfach den hinzugefügten Bot im Chatverlauf auswählen oder seinen Namen oder seine App-ID in das Feld An: in einem neuen Chat eingeben.
* **Kanäle** Ein Bot kann in einem Kanal erwähnt werden ("@*botname*"), wenn er dem Team hinzugefügt wurde. Beachten Sie, dass zusätzliche Antworten auf einen Bot in einem Kanal die Erwähnung des Bots erfordern. Es wird nicht auf Antworten geantwortet, wo es nicht erwähnt wird.

Für eingehende Nachrichten erhält Ihr Bot ein [Activity](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference?view=azure-bot-service-4.0#activity-object&preserve-view=true) Objekt vom Typ `messageType: message`. Obwohl das `Activity` Objekt andere Arten von Informationen enthalten kann, wie [Kanalaktualisierungen, die an Ihren Bot](~/resources/bot-v3/bots-notifications.md#channel-updates) gesendet werden, repräsentiert der `message` Typ die Kommunikation zwischen Bot und Benutzer.

Ihr Bot erhält eine Nutzlast, die die Benutzernachricht `Text` sowie andere Informationen über den Benutzer, die Quelle der Nachricht und Teams-Informationen enthält. Bemerkenswert:

* `timestamp` Datum und Uhrzeit der Nachricht in koordinierter Weltzeit (UTC).
* `localTimestamp` Datum und Uhrzeit der Nachricht in der Zeitzone des Absenders.
* `channelId` Immer "msteams". Dies bezieht sich auf einen Bot-Framework-Kanal, nicht auf einen Teams-Kanal.
* `from.id` Eine eindeutige und verschlüsselte ID für diesen Benutzer für Ihren Bot; geeignet als Schlüssel, wenn Ihre App Benutzerdaten speichern muss. Es ist einzigartig für Ihren Bot und kann nicht direkt außerhalb Ihrer Bot-Instanz verwendet werden, um diesen Benutzer auf sinnvolle Weise zu identifizieren.
* `channelData.tenant.id` Die Mandanten-ID für den Benutzer.

> [!NOTE]
> `from.id` ist einzigartig für Ihren Bot und kann nicht direkt außerhalb Ihrer Bot-Instanz verwendet werden, um diesen Benutzer auf sinnvolle Weise zu identifizieren..

## <a name="combining-channel-and-private-interactions-with-your-bot"></a>Kombinieren von Kanal- und privaten Interaktionen mit Ihrem Bot

Bei der Interaktion in einem Kanal sollte Ihr Bot schlau sein, bestimmte Konversationen mit einem Benutzer offline zu nehmen.. Angenommen, ein Benutzer versucht beispielsweise, eine komplexe Aufgabe zu koordinieren, z. B. die Planung mit einer Gruppe von Teammitgliedern. Anstatt die gesamte Abfolge der Interaktionen für den Kanal sichtbar zu machen, sollten Sie eine persönliche Chat-Nachricht an den Benutzer senden. Ihr Bot sollte in der Lage sein, den Benutzer problemlos zwischen persönlichen und Kanalgesprächen zu wechseln, ohne den Status zu verlieren.

> [!NOTE]
>Vergessen Sie nicht, den Kanal zu aktualisieren, wenn die Interaktion abgeschlossen ist, um die anderen Teammitglieder zu benachrichtigen.

## <a name="full-inbound-schema-example"></a>Vollständiges Beispiel für ein eingehendes Schema

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
> Das Textfeld für eingehende Nachrichten enthält manchmal Erwähnungen. Stellen Sie sicher, dass Sie diese ordnungsgemäß überprüfen und entfernen. Weitere Informationen finden Sie unter [Erwähnungen](~/resources/bot-v3/bot-conversations/bots-conv-channel.md#-mentions).

## <a name="teams-channel-data"></a>Teams-Kanaldaten

Das `channelData` Objekt enthält teamspezifische Informationen und ist die endgültige Quelle für Team- und Kanal-IDs. Sie sollten diese IDs zwischenspeichern und als Schlüssel für den lokalen Speicher verwenden.

Ein typisches channelData-Objekt in einer an Ihren Bot gesendeten Aktivität enthält die folgenden Informationen:

* `eventType` Art der Teams-Veranstaltung; nur bei [Kanaländerungsereignissen bestanden](~/resources/bot-v3/bots-notifications.md#channel-updates).
* `tenant.id` Mandanten-ID von Microsoft Azure Active Directory (Azure AD); in allen Zusammenhängen bestanden.
* `team` Nur in Kanalkontexten bestanden, nicht im persönlichen Chat.
  * `id` GUID für den Kanal.
  * `name` Name des Teams; nur bei [Teamumbenennungsereignissen bestanden](~/resources/bot-v3/bots-notifications.md#team-name-updates).
* `channel` Wird nur in Kanalkontexten weitergegeben, wenn der Bot erwähnt wird, oder für Ereignisse in Kanälen in Teams, in denen der Bot hinzugefügt wurde.
  * `id` GUID für den Kanal.
  * `name` Kanal Name; nur bei [Kanaländerungsereignissen bestanden](~/resources/bot-v3/bots-notifications.md#channel-updates).
* `channelData.teamsTeamId` Veraltet. Diese Eigenschaft ist nur aus Gründen der Abwärtskompatibilität enthalten.
* `channelData.teamsChannelId` Veraltet. Diese Eigenschaft ist nur aus Gründen der Abwärtskompatibilität enthalten.

### <a name="example-channeldata-object-channelcreated-event"></a>Beispiel eines channelData-Objekts (channelCreated-Ereignis)

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

Das [Microsoft.Bot.Connector.Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) NuGet-Paket stellt ein spezielles `TeamsChannelData` Objekt bereit, das Eigenschaften für den Zugriff auf Teams-spezifische Informationen verfügbar macht.

```csharp
TeamsChannelData channelData = activity.GetChannelData<TeamsChannelData>();
string tenantId = channelData.Tenant.Id;
```

## <a name="sending-replies-to-messages"></a>Senden von Antworten auf Nachrichten

Um auf eine vorhandene Nachricht zu antworten, rufen Sie [`ReplyToActivity`](/dotnet/api/microsoft.bot.connector.conversationsextensions.replytoactivityasync?view=botbuilder-dotnet-3.0#Microsoft_Bot_Connector_ConversationsExtensions_ReplyToActivityAsync_Microsoft_Bot_Connector_IConversations_System_String_System_String_Microsoft_Bot_Connector_Activity_System_Threading_CancellationToken_&preserve-view=true) in .NET oder [`session.send`](/javascript/api/botbuilder-core/TurnContext?view=botbuilder-ts-latest&viewFallbackFrom=botbuilder-ts-3.0#sendactivities&preserve-view=true) in Node.js auf. Das Bot Builder SDK kümmert sich um alle Details.

Wenn Sie sich für die Verwendung der REST-API entscheiden, können Sie auch den [`/v3/conversations/{conversationId}/activities/{activityId}`](/azure/bot-service/rest-api/bot-framework-rest-connector-send-and-receive-messages?view=azure-bot-service-3.0&preserve-view=true) Endpunkt aufrufen.

Der Nachrichteninhalt selbst kann einfachen Text oder einige der vom Bot Framework bereitgestellten [Karten und Kartenaktionen enthalten](~/task-modules-and-cards/cards/cards-actions.md).

Bitte beachten Sie, dass Sie in Ihrem ausgehenden Schema immer das gleiche verwenden sollten, das `serviceUrl` Sie erhalten haben. Beachten Sie, dass der Wert von `serviceUrl` tendenziell stabil ist, sich aber ändern kann. Wenn eine neue Nachricht eintrifft, sollte Ihr Bot den gespeicherten Wert von überprüfen `serviceUrl`.

## <a name="updating-messages"></a>Nachrichten aktualisieren

Anstatt dass Ihre Nachrichten statische Momentaufnahmen von Daten sind, kann Ihr Bot Nachrichten nach dem Senden dynamisch inline aktualisieren. Sie können dynamische Nachrichtenaktualisierungen für Szenarien wie Abfrageaktualisierungen, das Ändern verfügbarer Aktionen nach einem Tastendruck oder jede andere asynchrone Zustandsänderung verwenden.

Die neue Nachricht muss nicht mit dem ursprünglichen Typ übereinstimmen. Wenn die ursprüngliche Nachricht beispielsweise einen Anhang enthielt, kann die neue Nachricht eine einfache Textnachricht sein.

> [!NOTE]
> Sie können nur Inhalte aktualisieren, die in Nachrichten mit einem einzelnen Anhang und in Karussell-Layouts gesendet werden. Das Veröffentlichen von Aktualisierungen für Nachrichten mit mehreren Anhängen im Listenlayout wird nicht unterstützt.

### <a name="rest-api"></a>REST-API

Um eine Nachrichtenaktualisierung auszugeben, führen Sie einfach eine PUT-Anforderung `/v3/conversations/<conversationId>/activities/<activityId>/` an den Endpunkt mit einer bestimmten Aktivitäts-ID aus. Um dieses Szenario abzuschließen, sollten Sie die vom ursprünglichen POST-Aufruf zurückgegebene Aktivitäts-ID zwischenspeichern..

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

## <a name="starting-a-conversation-proactive-messaging"></a>Gespräch beginnen (proaktives Messaging)

Sie können eine persönliche Konversation mit einem Benutzer erstellen oder eine neue Antwortkette in einem Kanal für Ihren Team-Bot starten. Auf diese Weise können Sie Ihrem Benutzer oder Ihren Benutzern eine Nachricht senden, ohne dass sie zuerst Kontakt mit Ihrem Bot aufnehmen müssen. Weitere Informationen finden Sie in den folgenden Themen:

Unter [Proaktives Messaging für Bots](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md) finden Sie allgemeine Informationen zu Unterhaltungen, die von Bots gestartet wurden.

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
