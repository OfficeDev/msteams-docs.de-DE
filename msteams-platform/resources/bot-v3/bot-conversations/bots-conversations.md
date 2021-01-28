---
title: Senden und Empfangen von Nachrichten mit einem Bot
description: Beschreibt das Senden und Empfangen von Nachrichten mit Bots in Microsoft Teams
ms.topic: overview
keywords: Teams bots messages
ms.date: 05/20/2019
ms.openlocfilehash: 20c285a0cd06ac929d628edbc059b2a00b937eec
ms.sourcegitcommit: 976e870cc925f61b76c3830ec04ba6e4bdfde32f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/27/2021
ms.locfileid: "50014117"
---
# <a name="have-a-conversation-with-a-microsoft-teams-bot"></a>Unterhaltung mit einem Microsoft Teams-Bot

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Eine Unterhaltung ist eine Reihe von Nachrichten, die zwischen Ihrem Bot und einem oder mehreren Benutzern gesendet werden. In Teams gibt es drei Arten von Unterhaltungen (auch als Bereiche bezeichnet):

* `teams` Auch Kanalunterhaltungen genannt, die für alle Mitglieder des Kanals sichtbar sind.
* `personal` Unterhaltungen zwischen Bots und einem einzelnen Benutzer.
* `groupChat` Chatten zwischen einem Bot und zwei oder mehr Benutzern.

Ein Bot verhält sich etwas anders, je nachdem, an welcher Art von Unterhaltung er beteiligt ist:

* [Bots in Kanal- und Gruppenchatunterhaltungen](~/resources/bot-v3/bot-conversations/bots-conv-channel.md) erfordern, dass der Benutzer den Bot @ erwähnt, um ihn in einem Kanal aufrief.
* [Bots in Unterhaltungen einzelner](~/resources/bot-v3/bot-conversations/bots-conv-personal.md) Benutzer erfordern keine @-Erwähnung – der Benutzer kann einfach eingeben.

Damit der Bot in einem bestimmten Bereich funktioniert, sollte er als Unterstützung für diesen Bereich im Manifest aufgeführt werden. Bereiche werden in der Manifestreferenz definiert [und weiter erläutert.](~/resources/schema/manifest-schema.md)

## <a name="proactive-messages"></a>Proaktive Nachrichten

Bots können an einer Unterhaltung teilnehmen oder eine Unterhaltung initiieren. Die meisten Kommunikationen werden als Reaktion auf eine andere Nachricht verwendet. Wenn ein Bot eine Unterhaltung initiiert, wird er als proaktive *Nachricht bezeichnet.* Dazu gehören:

* Willkommensnachrichten
* Ereignisbenachrichtigungen
* Abruf von Nachrichten

## <a name="conversation-basics"></a>Grundlagen zu Unterhaltungen

Jede Nachricht ist ein `Activity`-Objekt vom Typ `messageType: message`. Wenn ein Benutzer eine Nachricht sendet, postet Teams die Nachricht auf Ihrem Bot. Spezifisch erfolgt dies durch Senden eines JSON-Objekts an den Nachrichtenendpunkt des Bots. Ihr Bot untersucht die Nachricht, um ihren Typ zu ermitteln, und antwortet entsprechend.

Bots unterstützen auch Nachrichten im Ereignisstil. Weitere [Informationen finden Sie unter Behandeln von Botereignissen in Microsoft Teams.](~/resources/bot-v3/bots-notifications.md) Die Spracherkennung wird derzeit nicht unterstützt.

Nachrichten sind in den meisten Umfangen gleich, aber es gibt Unterschiede in der Art und Weise, wie auf den Bot in der Benutzeroberfläche zugegriffen wird, und Unterschiede im Hintergrund, die Sie kennen müssen.

Die grundlegende Unterhaltung wird über den Bot Framework Connector, eine einzelne REST-API, verarbeitet, damit Ihr Bot mit Teams und anderen Kanälen kommunizieren kann. Das Bot Builder SDK bietet einfachen Zugriff auf diese API, zusätzliche Funktionen zum Verwalten des Unterhaltungsflusses und -zustands sowie einfache Möglichkeiten zur Integration kognitiver Dienste wie die Verarbeitung natürlicher Sprache (NlP).

## <a name="message-content"></a>Nachrichteninhalt

Ihr Bot kann Rich-Text, Bilder und Karten senden. Benutzer können Rich-Text- und Bilder an Ihren Bot senden. Auf der Einstellungsseite von Microsoft Teams für Ihren Bot können Sie den Inhaltstyp angeben, den Ihr Bot verarbeiten kann.

| Format | Von Benutzer zu Bot  | Vom Bot zum Benutzer |  Notes |
| --- | :---: | :---: | --- |
| Rich-Text  | ✔ | ✔ |  |
| Bilder | ✔ | ✔ | Maximal 1024×1024 und 1 MB im PNG-, JPEG- oder GIF-Format; Animierte GIF werden nicht unterstützt |
| Karten | ✖ | ✔ | Informationen zu [unterstützten Karten finden Sie](~/task-modules-and-cards/cards/cards-reference.md) in der Referenz zu Teams-Karten. |
| Emojis | ✖ | ✔ | Teams unterstützt derzeit Emojis über UTF-16 (z. B. U+1F600 für Das Gesicht) |
|

Weitere Informationen zu den Typen von Botinteraktionen, die vom Bot Framework unterstützt werden (auf denen Bots in Teams basieren), finden Sie in der Bot Framework-Dokumentation zum Unterhaltungsfluss und verwandten Konzepten in der Dokumentation für das Bot Builder SDK für [.NET](/azure/bot-service/dotnet/bot-builder-dotnet-overview?view=azure-bot-service-3.0) und das [Bot Builder SDK für Node.js](/azure/bot-service/nodejs/bot-builder-nodejs-overview?view=azure-bot-service-3.0). [](/azure/bot-service/dotnet/bot-builder-dotnet-manage-conversation-flow?view=azure-bot-service-3.0)

## <a name="message-formatting"></a>Mitteilungsformatierung

Sie können die optionale Eigenschaft eines Steuerelements festlegen, um zu steuern, wie der Textinhalt [`TextFormat`](/azure/bot-service/dotnet/bot-builder-dotnet-create-messages?view=azure-bot-service-3.0#customizing-a-message) `message` Ihrer Nachricht gerendert wird. Eine [ausführliche Beschreibung der unterstützten](~/resources/bot-v3/bots-message-format.md) Formatierung in Botnachrichten finden Sie unter "Nachrichtenformatierung".
Sie können die optionale Eigenschaft festlegen, um zu steuern, wie der Textinhalt [`TextFormat`](/azure/bot-service/dotnet/bot-builder-dotnet-create-messages?view=azure-bot-service-3.0#customizing-a-message) Ihrer Nachricht gerendert wird.

Ausführliche Informationen dazu, wie Teams Textformatierungen in Teams unterstützt, finden Sie [unter "Textformatierung" in Botnachrichten.](~/resources/bot-v3/bots-text-formats.md)

Informationen zum Formatieren von Karten in Nachrichten finden Sie unter [Kartenformatierung.](~/task-modules-and-cards/cards/cards-format.md)

## <a name="picture-messages"></a>Bildmeldungen

Bilder werden durch Hinzufügen von Anlagen zu einer Nachricht gesendet. Weitere Informationen zu Anlagen finden Sie in der [Bot Framework-Dokumentation.](/azure/bot-service/dotnet/bot-builder-dotnet-add-media-attachments?view=azure-bot-service-3.0)

Bilder können im PNG-, JPEG- oder #A0 bis zu 1024×1024 und 1 MB groß sein. Animierte GIF wird nicht unterstützt.

Es wird empfohlen, die Höhe und Breite der einzelnen Bilder mithilfe von XML anzugeben. Wenn Sie Markdown verwenden, ist die Bildgröße standardmäßig auf 256×256 festgelegt. Beispiel:

* `<img src="http://aka.ms/Fo983c" alt="Duck on a rock" height="150" width="223"></img>` verwenden
* Nicht verwenden `![Duck on a rock](http://aka.ms/Fo983c)`

## <a name="receiving-messages"></a>Empfangen von Nachrichten

Je nachdem, welche Bereiche deklariert sind, kann Ihr Bot Nachrichten in den folgenden Kontexten empfangen:

* **Persönlicher Chat** Benutzer können in einer privaten Unterhaltung mit einem Bot interagieren, indem sie einfach den hinzugefügten Bot im Chatverlauf auswählen oder den Namen oder die App-ID in das Feld "An:" in einem neuen Chat eingeben.
* **Kanäle** Ein Bot kann in einem Kanal ("@_Botname")_ erwähnt werden, wenn er dem Team hinzugefügt wurde. Beachten Sie, dass für zusätzliche Antworten auf einen Bot in einem Kanal der Bot erwähnt werden muss. Antworten, in denen sie nicht erwähnt wird, werden nicht beantwortet.

Bei eingehenden Nachrichten empfängt Ihr Bot ein [`Activity`](/azure/bot-service/rest-api/bot-framework-rest-connector-activities?view=azure-bot-service-3.0) Objekt vom Typ `messageType: message` . Obwohl das Objekt andere Arten von Informationen enthalten kann, z. B. Kanalupdates, die an Ihren Bot gesendet werden, stellt der Typ die Kommunikation `Activity` zwischen Bot und Benutzer [](~/resources/bot-v3/bots-notifications.md#channel-updates) `message` dar.

Ihr Bot empfängt eine Nutzlast, die die Benutzernachricht sowie weitere Informationen über den Benutzer, die Quelle der Nachricht und `Text` Teams-Informationen enthält. Hinweis:

* `timestamp` Datum und Uhrzeit der Nachricht in koordinierter Weltzeit (UTC)
* `localTimestamp` Datum und Uhrzeit der Nachricht in der Zeitzone des Absenders
* `channelId` Immer "msteams". Dies bezieht sich auf einen Bot-Framework-Kanal, nicht auf einen Teams-Kanal.
* `from.id` Eine eindeutige und verschlüsselte ID für den Benutzer für Ihren Bot; geeignet als Schlüssel, wenn Ihre App Benutzerdaten speichern muss. Sie ist für Ihren Bot einzigartig und kann nicht auf sinnvolle Weise direkt außerhalb Ihrer Botinstanz verwendet werden, um diesen Benutzer zu identifizieren.
* `channelData.tenant.id` Die Mandanten-ID für den Benutzer.

> [!NOTE]
> `from.id` ist für Ihren Bot eindeutig und kann nicht auf sinnvolle Weise direkt außerhalb Ihrer Botinstanz verwendet werden, um diesen Benutzer zu identifizieren.

## <a name="combining-channel-and-private-interactions-with-your-bot"></a>Kombinieren von Kanal- und privaten Interaktionen mit Ihrem Bot

Bei der Interaktion in einem Kanal sollte Ihr Bot mit dem Offline schalten bestimmter Unterhaltungen mit einem Benutzer intelligent sein. Angenommen, ein Benutzer versucht, eine komplexe Aufgabe zu koordinieren, z. B. die Planung mit einer Gruppe von Teammitgliedern. Anstatt die gesamte Abfolge von Interaktionen für den Kanal sichtbar zu machen, sollten Sie erwägen, eine persönliche Chatnachricht an den Benutzer zu senden. Ihr Bot sollte in der Lage sein, den Benutzer problemlos zwischen persönlichen Unterhaltungen und Kanalunterhaltungen zu übertragen, ohne den Status zu verlieren.

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
> Das Textfeld für eingehende Nachrichten enthält manchmal Erwähnungen. Achten Sie darauf, diese ordnungsgemäß zu überprüfen und zu bestreifen. Weitere Informationen finden Sie unter [Erwähnungen](~/resources/bot-v3/bot-conversations/bots-conv-channel.md#-mentions).

## <a name="teams-channel-data"></a>Teams-Kanaldaten

Das `channelData` Objekt enthält Teams-spezifische Informationen und ist die definitive Quelle für Team- und Kanal-IDs. Sie sollten diese IDs zwischenspeichern und als Schlüssel für den lokalen Speicher verwenden.

Das `channelData` Objekt ist nicht in Nachrichten in persönlichen Unterhaltungen enthalten, da diese außerhalb eines Kanals stattfinden.

Ein typisches channelData-Objekt in einer Aktivität, die an Ihren Bot gesendet wird, enthält die folgenden Informationen:

* `eventType` #A0 Nur bei [Kanaländerungsereignissen übergeben](~/resources/bot-v3/bots-notifications.md#channel-updates)
* `tenant.id` Azure Active Directory-Mandanten-ID; In allen Kontexten übergeben
* `team` Wird nur im Kanalkontext übergeben, nicht im persönlichen Chat.
  * `id` GUID für den Kanal
  * `name` Name des Teams; Wird nur bei Ereignissen zur [Teambenennung übergeben](~/resources/bot-v3/bots-notifications.md#team-name-updates)
* `channel` Wird nur in Kanalkontexten übergeben, wenn der Bot erwähnt wird, oder für Ereignisse in Kanälen in Teams, in denen der Bot hinzugefügt wurde
  * `id` GUID für den Kanal
  * `name`Kanalname; nur bei [Kanaländerungsereignissen übergeben.](~/resources/bot-v3/bots-notifications.md#channel-updates)
* `channelData.teamsTeamId` Veraltet. Diese Eigenschaft ist nur aus Abwärtskompatibilität enthalten.
* `channelData.teamsChannelId` Veraltet. Diese Eigenschaft ist nur aus Abwärtskompatibilität enthalten.

### <a name="example-channeldata-object-channelcreated-event"></a>Beispiel für ein channelData-Objekt (channelCreated-Ereignis)

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

Das [Microsoft.Bot.Connector.Teams-NuGet-Paket](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) stellt ein spezielles Objekt zur Verfügung, das Eigenschaften für den Zugriff auf `TeamsChannelData` Teams-spezifische Informationen verfügbar macht.

```csharp
TeamsChannelData channelData = activity.GetChannelData<TeamsChannelData>();
string tenantId = channelData.Tenant.Id;
```

## <a name="sending-replies-to-messages"></a>Senden von Antworten auf Nachrichten

Um auf eine vorhandene Nachricht zu antworten, rufen Sie [`ReplyToActivity`](/dotnet/api/microsoft.bot.connector.conversationsextensions.replytoactivityasync?view=botbuilder-dotnet-3.0#Microsoft_Bot_Connector_ConversationsExtensions_ReplyToActivityAsync_Microsoft_Bot_Connector_IConversations_System_String_System_String_Microsoft_Bot_Connector_Activity_System_Threading_CancellationToken_) in .NET oder [`session.send`](/javascript/api/botbuilder-core/TurnContext?view=botbuilder-ts-latest&viewFallbackFrom=botbuilder-ts-3.0#sendactivities) in Node.js. Das Bot Builder SDK verarbeitet alle Details.

Wenn Sie die REST-API verwenden möchten, können Sie auch den Endpunkt [`/v3/conversations/{conversationId}/activities/{activityId}`](/azure/bot-service/rest-api/bot-framework-rest-connector-send-and-receive-messages?view=azure-bot-service-3.0) aufrufen.

Der Nachrichteninhalt selbst kann einfachen Text oder einige der von Bot Framework bereitgestellten Karten [und Kartenaktionen enthalten.](~/task-modules-and-cards/cards/cards-actions.md)

Bitte beachten Sie, dass Sie in Ihrem ausgehenden Schema immer dieselbe Wiesn verwenden sollten, die `serviceUrl` Sie erhalten haben. Beachten Sie, dass der Wert `serviceUrl` von in der Regel stabil ist, sich aber ändern kann. Wenn eine neue Nachricht eintrifft, sollte Ihr Bot den gespeicherten Wert von `serviceUrl` überprüfen.

## <a name="updating-messages"></a>Aktualisieren von Nachrichten

Anstatt ihre Nachrichten als statische Momentaufnahmen von Daten zu verwenden, kann Ihr Bot Nachrichten nach dem Senden dynamisch inline aktualisieren. Sie können dynamische Nachrichtenaktualisierungen für Szenarien wie z. B. Abrufaktualisierungen, Das Ändern verfügbarer Aktionen nach dem Drücken einer Schaltfläche oder andere asynchrone Statusänderung verwenden.

Die neue Nachricht muss nicht mit dem ursprünglichen Typ übereinstimmen. Wenn die ursprüngliche Nachricht beispielsweise eine Anlage enthielt, kann die neue Nachricht eine einfache Textnachricht sein.

> [!NOTE]
> Sie können nur Inhalte aktualisieren, die in Einzelanlagennachrichten und Karusselllayouts gesendet werden. Das Veröffentlichen von Aktualisierungen für Nachrichten mit mehreren Anlagen im Listenlayout wird nicht unterstützt.

### <a name="rest-api"></a>REST-API

Um ein Nachrichtenupdate aus senden zu können, führen Sie einfach eine PUT-Anforderung für den Endpunkt mit `/v3/conversations/<conversationId>/activities/<activityId>/` einer bestimmten Aktivitäts-ID aus. Zum Abschließen dieses Szenarios sollten Sie die Aktivitäts-ID zwischenspeichern, die vom ursprünglichen POST-Aufruf zurückgegeben wurde.

```json
PUT /v3/conversations/19%3Aja0cu120i1jod12j%40skype.net/activities/012ujdo0128
{
    "type": "message",
    "text": "This message has been updated"
}
```

### <a name="net-example"></a>.NET-Beispiel

Sie können die Methode im Bot Builder SDK verwenden, `UpdateActivityAsync` um eine vorhandene Nachricht zu aktualisieren.

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

Sie können die Methode im Bot Builder SDK verwenden, `session.connector.update` um eine vorhandene Nachricht zu aktualisieren.

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

Sie können eine persönliche Unterhaltung mit einem Benutzer erstellen oder eine neue Antwortkette in einem Kanal für Ihren Teambot starten. Auf diese Weise können Sie Ihren Oder-Benutzern eine Nachricht senden, ohne dass sie zuerst den Kontakt mit Ihrem Bot initiieren müssen. Weitere Informationen hierzu finden Sie in den folgenden Themen:

Weitere allgemeine Informationen zu Unterhaltungen, die von Bots gestartet wurden, finden Sie unter [proaktives](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md) Messaging für Bots.

## <a name="deleting-messages"></a>Löschen von Nachrichten

Nachrichten können mit der Connectorsmethode [`delete()`](https://docs.botframework.com/node/builder/chat-reference/interfaces/_botbuilder_d_.iconnector.html#delete) im [BotBuilder SDK gelöscht werden.](/bot-framework/bot-builder-overview-getstarted)

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
