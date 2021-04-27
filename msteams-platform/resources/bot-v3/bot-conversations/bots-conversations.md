---
title: Senden und Empfangen von Nachrichten mit einem Bot
description: Beschreibt das Senden und Empfangen von Nachrichten mit Bots in Microsoft Teams
ms.topic: overview
localization_priority: Normal
keywords: teams bots messages
ms.date: 05/20/2019
ms.openlocfilehash: 67dae46d0d34ff842d3fe6717f51e00ad4b8c80a
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020667"
---
# <a name="have-a-conversation-with-a-microsoft-teams-bot"></a>Führen einer Unterhaltung mit einem Microsoft Teams-Bot

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Eine Unterhaltung ist eine Reihe von Nachrichten, die zwischen Ihrem Bot und einem oder mehreren Benutzern gesendet werden. In Teams gibt es drei Arten von Unterhaltungen (auch als Bereiche bezeichnet):

* `teams` Wird auch als Kanalunterhaltungen bezeichnet, die für alle Mitglieder des Kanals sichtbar sind.
* `personal` Unterhaltungen zwischen Bots und einem einzelnen Benutzer.
* `groupChat` Chatten zwischen einem Bot und zwei oder mehr Benutzern.

Ein Bot verhält sich je nach Art der Unterhaltung etwas anders:

* [Bots in Kanal- und Gruppenchatunterhaltungen](~/resources/bot-v3/bot-conversations/bots-conv-channel.md) erfordern, dass der Benutzer den Bot @ erwähnt, um ihn in einem Kanal aufgerufen zu haben.
* [Bots in Unterhaltungen mit](~/resources/bot-v3/bot-conversations/bots-conv-personal.md) einem einzelnen Benutzer erfordern keine @-Erwähnung - der Benutzer kann einfach eingeben.

Damit der Bot in einem bestimmten Bereich funktioniert, sollte er im Manifest als Unterstützung für diesen Bereich aufgeführt werden. Bereiche werden im Manifestverweis definiert [und weiter erläutert.](~/resources/schema/manifest-schema.md)

## <a name="proactive-messages"></a>Proaktive Nachrichten

Bots können an einer Unterhaltung teilnehmen oder eine Unterhaltung initiieren. Die meisten Kommunikationen werden auf eine andere Nachricht reagiert. Wenn ein Bot eine Unterhaltung initiiert, wird er als proaktive *Nachricht bezeichnet.* Dazu gehören:

* Willkommensnachrichten
* Ereignisbenachrichtigungen
* Abruf von Nachrichten

## <a name="conversation-basics"></a>Grundlagen zu Unterhaltungen

Jede Nachricht ist ein `Activity`-Objekt vom Typ `messageType: message`. Wenn ein Benutzer eine Nachricht sendet, postet Teams die Nachricht auf Ihrem Bot. Spezifisch erfolgt dies durch Senden eines JSON-Objekts an den Nachrichtenendpunkt des Bots. Ihr Bot untersucht die Nachricht, um ihren Typ zu bestimmen, und antwortet entsprechend.

Bots unterstützen auch Nachrichten im Ereignisformat. Weitere Informationen finden Sie unter Behandeln von [Botereignissen in Microsoft Teams.](~/resources/bot-v3/bots-notifications.md) Die Sprache wird derzeit nicht unterstützt.

Nachrichten sind in allen Bereiche zum größten Teil identisch, es gibt jedoch Unterschiede beim Zugriff auf den Bot auf der Benutzeroberfläche und Unterschiede hinter den Kulissen, die Sie kennen müssen.

Grundlegende Unterhaltungen werden über den Bot Framework Connector, eine einzelne REST-API, behandelt, damit Ihr Bot mit Teams und anderen Kanälen kommunizieren kann. Das Bot Builder SDK bietet einfachen Zugriff auf diese API, zusätzliche Funktionen zum Verwalten des Unterhaltungsflusses und -zustands sowie einfache Möglichkeiten, kognitive Dienste wie die Verarbeitung natürlicher Sprachen (Natural Language Processing, NLP) zu integrieren.

## <a name="message-content"></a>Nachrichteninhalt

Ihr Bot kann Rich-Text, Bilder und Karten senden. Benutzer können Rich-Text und Bilder an Ihren Bot senden. Sie können den Inhaltstyp angeben, den Ihr Bot auf der Seite Microsoft Teams-Einstellungen für Ihren Bot verarbeiten kann.

| Format | Vom Benutzer zum Bot  | Vom Bot zum Benutzer |  Notes |
| --- | :---: | :---: | --- |
| Rich-Text  | ✔ | ✔ |  |
| Bilder | ✔ | ✔ | Maximal 1024×1024 und 1 MB im PNG-, JPEG- oder GIF-Format; animierte GIF werden nicht unterstützt |
| Karten | ✖ | ✔ | Informationen zu unterstützten Karten finden Sie in [der Teams-Kartenreferenz](~/task-modules-and-cards/cards/cards-reference.md) |
| Emojis | ✖ | ✔ | Teams unterstützt derzeit Emojis über UTF-16 (z. B. U+1F600 zum Schmunzeln des Gesichts) |
|

Weitere Informationen zu den vom Bot Framework unterstützten Botinteraktionen (auf denen Bots in [](/azure/bot-service/dotnet/bot-builder-dotnet-manage-conversation-flow?view=azure-bot-service-3.0&preserve-view=true) Teams basieren) finden Sie in der Bot Framework-Dokumentation zu Unterhaltungsfluss und verwandten Konzepten in der Dokumentation für das [Bot Builder SDK für .NET](/azure/bot-service/dotnet/bot-builder-dotnet-overview?view=azure-bot-service-3.0&preserve-view=true) und das Bot Builder SDK [für Node.js](/azure/bot-service/nodejs/bot-builder-nodejs-overview?view=azure-bot-service-3.0&preserve-view=true).

## <a name="message-formatting"></a>Mitteilungsformatierung

Sie können die optionale Eigenschaft von a festlegen, um zu steuern, wie der Textinhalt Ihrer Nachricht [`TextFormat`](/azure/bot-service/dotnet/bot-builder-dotnet-create-messages?view=azure-bot-service-3.0#customizing-a-message&preserve-view=true) `message` gerendert wird. Eine [detaillierte Beschreibung der unterstützten](~/resources/bot-v3/bots-message-format.md) Formatierung in Botnachrichten finden Sie unter Nachrichtenformatierung.
Sie können die optionale Eigenschaft festlegen, um zu steuern, wie der Textinhalt Ihrer Nachricht [`TextFormat`](/azure/bot-service/dotnet/bot-builder-dotnet-create-messages?view=azure-bot-service-3.0#customizing-a-message&preserve-view=true) gerendert wird.

Ausführliche Informationen dazu, wie Teams die Textformatierung in Teams unterstützt, finden Sie unter [Textformatierung in Botnachrichten](~/resources/bot-v3/bots-text-formats.md).

Informationen zum Formatieren von Karten in Nachrichten finden Sie unter [Kartenformatierung](~/task-modules-and-cards/cards/cards-format.md).

## <a name="picture-messages"></a>Bildnachrichten

Bilder werden durch Hinzufügen von Anlagen zu einer Nachricht gesendet. Weitere Informationen zu Anlagen finden Sie in der [Bot Framework-Dokumentation](/azure/bot-service/dotnet/bot-builder-dotnet-add-media-attachments?view=azure-bot-service-3.0&preserve-view=true).

Bilder können im PNG-, JPEG- oder GIF-Format mindestens 1024×1024 und 1 MB groß sein. animierte GIF wird nicht unterstützt.

Es wird empfohlen, die Höhe und Breite der einzelnen Bilder mithilfe von XML anzugeben. Wenn Sie Markdown verwenden, ist die Bildgröße standardmäßig auf 256×256 festgelegt. Beispiel:

* `<img src="http://aka.ms/Fo983c" alt="Duck on a rock" height="150" width="223"></img>` verwenden
* Nicht verwenden `![Duck on a rock](http://aka.ms/Fo983c)`

## <a name="receiving-messages&quot;></a>Empfangen von Nachrichten

Je nachdem, welche Bereiche deklariert werden, kann Ihr Bot Nachrichten in den folgenden Kontexten empfangen:

* **Persönlicher Chat** Benutzer können in einer privaten Unterhaltung mit einem Bot interagieren, indem sie einfach den hinzugefügten Bot im Chatverlauf auswählen oder den Namen oder die App-ID in das Feld An: in einen neuen Chat eingeben.
* **Kanäle** Ein Bot kann in einem Kanal (&quot;@_botname")_ erwähnt werden, wenn er dem Team hinzugefügt wurde. Beachten Sie, dass für zusätzliche Antworten auf einen Bot in einem Kanal der Bot erwähnt werden muss. Sie antwortet nicht auf Antworten, wenn sie nicht erwähnt wird.

Für eingehende Nachrichten empfängt Ihr Bot ein [`Activity`](/azure/bot-service/rest-api/bot-framework-rest-connector-activities?view=azure-bot-service-3.0&preserve-view=true) Objekt vom Typ `messageType: message` . Obwohl das Objekt andere Arten von Informationen enthalten kann, z. B. Kanalupdates, die an Ihren Bot gesendet werden, stellt der Typ die Kommunikation `Activity` zwischen Bot und Benutzer [](~/resources/bot-v3/bots-notifications.md#channel-updates) `message` dar.

Ihr Bot empfängt eine Nutzlast, die die Benutzernachricht sowie andere Informationen über den Benutzer, die Quelle der Nachricht und `Text` Teams-Informationen enthält. Beachten Sie:

* `timestamp` Datum und Uhrzeit der Nachricht in koordinierter Weltzeit (COORDINATED Universal Time, UTC)
* `localTimestamp` Datum und Uhrzeit der Nachricht in der Zeitzone des Absenders
* `channelId` Immer "msteams". Dies bezieht sich auf einen Botframeworkkanal, nicht auf einen Teams-Kanal.
* `from.id` Eine eindeutige und verschlüsselte ID für den Benutzer für Ihren Bot; geeignet als Schlüssel, wenn Ihre App Benutzerdaten speichern muss. Es ist für Ihren Bot eindeutig und kann nicht auf sinnvolle Weise direkt außerhalb Ihrer Botinstanz verwendet werden, um diesen Benutzer zu identifizieren.
* `channelData.tenant.id` Die Mandanten-ID für den Benutzer.

> [!NOTE]
> `from.id` ist für Ihren Bot eindeutig und kann nicht direkt außerhalb Ihrer Botinstanz auf sinnvolle Weise verwendet werden, um diesen Benutzer zu identifizieren.

## <a name="combining-channel-and-private-interactions-with-your-bot"></a>Kombinieren von Kanal- und privaten Interaktionen mit Ihrem Bot

Bei der Interaktion in einem Kanal sollte Ihr Bot intelligent sein, bestimmte Unterhaltungen mit einem Benutzer offline zu schalten. Angenommen, ein Benutzer versucht, eine komplexe Aufgabe zu koordinieren, z. B. die Planung mit einer Gruppe von Teammitgliedern. Anstatt die gesamte Abfolge von Interaktionen für den Kanal sichtbar zu machen, sollten Sie eine persönliche Chatnachricht an den Benutzer senden. Ihr Bot sollte in der Lage sein, den Benutzer problemlos zwischen persönlichen und Kanalunterhaltungen zu überwechseln, ohne den Status zu verlieren.

> [!NOTE]
>Vergessen Sie nicht, den Kanal zu aktualisieren, wenn die Interaktion abgeschlossen ist, um die anderen Teammitglieder zu benachrichtigen.

## <a name="full-inbound-schema-example"></a>Vollständiges eingehendes Schemabeispiel

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
> Das Textfeld für eingehende Nachrichten enthält manchmal Erwähnungen. Achten Sie darauf, diese ordnungsgemäß zu überprüfen und zu bestreifen. Weitere Informationen finden Sie unter [Erwähnungen](~/resources/bot-v3/bot-conversations/bots-conv-channel.md#-mentions).

## <a name="teams-channel-data"></a>Teams-Kanaldaten

Das `channelData` Objekt enthält Teams-spezifische Informationen und ist die endgültige Quelle für Team- und Kanal-IDs. Sie sollten diese IDs zwischenspeichern und als Schlüssel für den lokalen Speicher verwenden.

Das `channelData` Objekt ist nicht in Nachrichten in persönlichen Unterhaltungen enthalten, da diese außerhalb eines Kanals stattfinden.

Ein typisches channelData-Objekt in einer Aktivität, die an Ihren Bot gesendet wird, enthält die folgenden Informationen:

* `eventType` #A0 Nur bei [Kanaländerungsereignissen übergeben](~/resources/bot-v3/bots-notifications.md#channel-updates)
* `tenant.id` Azure Active #A0 in allen Kontexten übergeben
* `team` Wird nur in Kanalkontexten übergeben, nicht in persönlichen Chats.
  * `id` GUID für den Kanal
  * `name` Name des Teams; Nur bei [Teambenennungsereignissen übergeben](~/resources/bot-v3/bots-notifications.md#team-name-updates)
* `channel` Wird nur in Kanalkontexten übergeben, wenn der Bot erwähnt wird, oder für Ereignisse in Kanälen in Teams, in denen der Bot hinzugefügt wurde
  * `id` GUID für den Kanal
  * `name`Kanalname; nur bei [Kanaländerungsereignissen übergeben.](~/resources/bot-v3/bots-notifications.md#channel-updates)
* `channelData.teamsTeamId` Veraltet. Diese Eigenschaft ist nur aus Abwärtskompatibilität enthalten.
* `channelData.teamsChannelId` Veraltet. Diese Eigenschaft ist nur aus Abwärtskompatibilität enthalten.

### <a name="example-channeldata-object-channelcreated-event"></a>Beispiel-channelData-Objekt (channelCreated-Ereignis)

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

Das [Microsoft.Bot.Connector.Teams-NuGet-Paket](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) stellt ein spezielles Objekt zur Verfügung, das Eigenschaften für den Zugriff auf `TeamsChannelData` teamsspezifische Informationen verfügbar macht.

```csharp
TeamsChannelData channelData = activity.GetChannelData<TeamsChannelData>();
string tenantId = channelData.Tenant.Id;
```

## <a name="sending-replies-to-messages"></a>Senden von Antworten auf Nachrichten

Um auf eine vorhandene Nachricht zu antworten, rufen Sie [`ReplyToActivity`](/dotnet/api/microsoft.bot.connector.conversationsextensions.replytoactivityasync?view=botbuilder-dotnet-3.0#Microsoft_Bot_Connector_ConversationsExtensions_ReplyToActivityAsync_Microsoft_Bot_Connector_IConversations_System_String_System_String_Microsoft_Bot_Connector_Activity_System_Threading_CancellationToken_&preserve-view=true) in .NET oder [`session.send`](/javascript/api/botbuilder-core/TurnContext?view=botbuilder-ts-latest&viewFallbackFrom=botbuilder-ts-3.0#sendactivities&preserve-view=true) in Node.js. Das Bot Builder SDK verarbeitet alle Details.

Wenn Sie die REST-API verwenden möchten, können Sie auch den Endpunkt [`/v3/conversations/{conversationId}/activities/{activityId}`](/azure/bot-service/rest-api/bot-framework-rest-connector-send-and-receive-messages?view=azure-bot-service-3.0&preserve-view=true) aufrufen.

Der Nachrichteninhalt selbst kann einfachen Text oder einige der von Bot Framework bereitgestellten [Karten und Kartenaktionen enthalten.](~/task-modules-and-cards/cards/cards-actions.md)

Bitte beachten Sie, dass Sie in Ihrem ausgehenden Schema immer dasselbe wie das `serviceUrl` empfangene schema verwenden sollten. Beachten Sie, dass der Wert von `serviceUrl` in der Regel stabil ist, sich aber ändern kann. Wenn eine neue Nachricht eintrifft, sollte Ihr Bot den gespeicherten Wert von `serviceUrl` überprüfen.

## <a name="updating-messages"></a>Aktualisieren von Nachrichten

Anstatt ihre Nachrichten als statische Momentaufnahmen von Daten zu verwenden, kann Ihr Bot Nachrichten nach dem Senden dynamisch inline aktualisieren. Sie können dynamische Nachrichtenupdates für Szenarien wie Abrufupdates, Ändern verfügbarer Aktionen nach dem Drücken einer Schaltfläche oder andere asynchrone Zustandsänderung verwenden.

Die neue Nachricht muss nicht mit dem ursprünglichen Typ übereinstimmen. Wenn die ursprüngliche Nachricht beispielsweise eine Anlage enthielt, kann die neue Nachricht eine einfache Textnachricht sein.

> [!NOTE]
> Sie können nur Inhalte aktualisieren, die in Nachrichten mit einzelnen Anlagen und Karusselllayouts gesendet werden. Das Veröffentlichen von Aktualisierungen für Nachrichten mit mehreren Anlagen im Listenlayout wird nicht unterstützt.

### <a name="rest-api"></a>REST-API

Führen Sie zum Ausführen eines Nachrichtenupdates einfach eine PUT-Anforderung für den Endpunkt `/v3/conversations/<conversationId>/activities/<activityId>/` mithilfe einer bestimmten Aktivitäts-ID aus. Zum Abschließen dieses Szenarios sollten Sie die vom ursprünglichen POST-Aufruf zurückgegebene Aktivitäts-ID zwischenspeichern.

```json
PUT /v3/conversations/19%3Aja0cu120i1jod12j%40skype.net/activities/012ujdo0128
{
    "type": "message",
    "text": "This message has been updated"
}
```

### <a name="net-example"></a>.NET-Beispiel

Sie können die Methode `UpdateActivityAsync` im Bot Builder SDK verwenden, um eine vorhandene Nachricht zu aktualisieren.

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

Sie können die Methode `session.connector.update` im Bot Builder SDK verwenden, um eine vorhandene Nachricht zu aktualisieren.

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

Sie können eine persönliche Unterhaltung mit einem Benutzer erstellen oder eine neue Antwortkette in einem Kanal für Ihren Teambot starten. Auf diese Weise können Sie Ihre Benutzer oder Benutzer ohne vorherigen Kontakt mit Ihrem Bot initiieren. Weitere Informationen finden Sie in den folgenden Themen:

Weitere allgemeine Informationen zu von Bots gestarteten Unterhaltungen finden Sie unter [Proaktives](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md) Messaging für Bots.

## <a name="deleting-messages"></a>Löschen von Nachrichten

Nachrichten können mit der [`delete()`](https://docs.botframework.com/node/builder/chat-reference/interfaces/_botbuilder_d_.iconnector.html#delete) Connectors-Methode im [BotBuilder SDK gelöscht werden.](/bot-framework/bot-builder-overview-getstarted)

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
