---
title: Senden und empfangen von Nachrichten mit einem bot
description: Beschreibt das Senden und empfangen von Nachrichten mit Bots in Microsoft Teams
keywords: Teams-Bots-Nachrichten
ms.date: 05/20/2019
ms.openlocfilehash: 4a15bb9b4ae8c0ede3214d3a534649e2769baf6e
ms.sourcegitcommit: 2b1fd50466d807869fd173371ba7dfd82a0064ac
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2020
ms.locfileid: "44801324"
---
# <a name="have-a-conversation-with-a-microsoft-teams-bot"></a>Unterhaltung mit einem Microsoft Teams-bot

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-bots.md)]

Eine Unterhaltung ist eine Reihe von Nachrichten, die zwischen Ihrem Bot und einem oder mehreren Benutzern gesendet werden. In Teams gibt es drei Arten von Unterhaltungen (auch als Bereiche bezeichnet):

* `teams`Wird auch als Kanal Unterhaltungen bezeichnet, die für alle Mitglieder des Kanals sichtbar sind.
* `personal`Unterhaltungen zwischen Bots und einem einzelnen Benutzer.
* `groupChat`Chat zwischen einem bot und zwei oder mehr Benutzern.

Ein bot verhält sich je nach Art der Unterhaltung, in der er beteiligt ist, etwas anders:

* [Bots in Kanal-und Gruppenchat Unterhaltungen](~/resources/bot-v3/bot-conversations/bots-conv-channel.md) erfordern, dass der Benutzer @ den bot erwähnt, um ihn in einem Kanal aufzurufen.
* [Bots in einzelnen Benutzer Unterhaltungen](~/resources/bot-v3/bot-conversations/bots-conv-personal.md) erfordern keine @ mention-der Benutzer kann einfach eingeben.

Damit der bot in einem bestimmten Bereich funktioniert, sollte er als Unterstützung für diesen Bereich im Manifest aufgelistet werden. Bereiche werden im [Manifest-Verweis](~/resources/schema/manifest-schema.md)definiert und weiter behandelt.

## <a name="proactive-messages"></a>Proaktive Nachrichten

Bots können an einer Unterhaltung teilnehmen oder eine initiieren. Die meiste Kommunikation erfolgt als Reaktion auf eine andere Nachricht. Wenn ein bot eine Unterhaltung initiiert, wird er als *proaktive Nachricht*bezeichnet. Beispiele sind:

* Willkommensnachrichten
* Ereignisbenachrichtigungen
* Abrufen von Nachrichten

## <a name="conversation-basics"></a>Grundlagen der Unterhaltung

Jede Nachricht ist ein `Activity`-Objekt vom Typ `messageType: message`. Wenn ein Benutzer eine Nachricht sendet, postet Teams die Nachricht auf Ihrem Bot. Spezifisch erfolgt dies durch Senden eines JSON-Objekts an den Nachrichtenendpunkt des Bots. Ihr bot überprüft die Nachricht, um den Typ zu bestimmen, und antwortet dementsprechend.

Bots unterstützen auch Nachrichten im Ereignis Stil. Weitere Informationen finden Sie unter [Behandeln von bot-Ereignissen in Microsoft Teams](~/resources/bot-v3/bots-notifications.md) . Die Sprache wird derzeit nicht unterstützt.

Nachrichten sind größtenteils in allen Bereichen gleich, aber es gibt Unterschiede in der Art und Weise, wie der bot auf der Benutzeroberfläche aufgerufen wird, und Unterschiede hinter den Szenen, über die Sie Bescheid wissen müssen.

Grundlegende Unterhaltungen werden über den bot-Framework-Konnektor behandelt, eine einzelne Rest-API, mit der ihr bot mit Teams und anderen Kanälen kommunizieren kann. Das bot-Generator-SDK bietet einfachen Zugriff auf diese API, zusätzliche Funktionen zum Verwalten des Unterhaltungs Flusses und-Zustands sowie einfache Methoden zum Integrieren von kognitiven Diensten wie etwa die Natural Language Processing (NLP).

## <a name="message-content"></a>Nachrichteninhalt

Ihr Bot kann Rich-Text, Bilder und Karten senden. Benutzer können Rich-Text und Bilder an Ihren bot senden. Sie können den Typ des Inhalts angeben, den Ihr bot auf der Seite Microsoft Teams-Einstellungen für Ihren bot verarbeiten kann.

| Format | Von Benutzer zu bot  | Von bot zu Benutzer |  Anmerkungen |
| --- | :---: | :---: | --- |
| Rich-Text  | ✔ | ✔ |  |
| Bilder | ✔ | ✔ | Maximal 1024 × 1024 und 1 MB im PNG-, JPEG-oder GIF-Format; animierte GIF-Zeichen werden nicht unterstützt |
| Karten | ✖ | ✔ | Siehe die Microsoft [Teams-Karten Referenz](~/task-modules-and-cards/cards/cards-reference.md) für unterstützte Karten |
| Emojis | ✖ | ✔ | Teams unterstützen derzeit Emojis über UTF-16 (wie U + 1F600 für grinsende Fläche) |
|

Weitere Informationen zu den Typen von bot-Interaktionen, die vom bot-Framework unterstützt werden (die Bots in Microsoft Teams basieren), finden Sie in der Dokumentation zum bot-Framework zu [Unterhaltungs Fluss](/azure/bot-service/dotnet/bot-builder-dotnet-manage-conversation-flow?view=azure-bot-service-3.0) und verwandten Konzepten in der Dokumentation für [das bot Builder SDK für .net](/azure/bot-service/dotnet/bot-builder-dotnet-overview?view=azure-bot-service-3.0) und [das bot Builder SDK für Node.js](/azure/bot-service/nodejs/bot-builder-nodejs-overview?view=azure-bot-service-3.0).

## <a name="message-formatting"></a>Mitteilungsformatierung

Sie können die optionale Eigenschaft eines festlegen [`TextFormat`](/azure/bot-service/dotnet/bot-builder-dotnet-create-messages?view=azure-bot-service-3.0#customizing-a-message) `message` , um zu steuern, wie der Textinhalt Ihrer Nachricht gerendert wird. Eine detaillierte Beschreibung der unterstützten Formatierung in bot-Nachrichten finden Sie unter [Nachrichtenformatierung](~/resources/bot-v3/bots-message-format.md) .
Sie können die optionale [`TextFormat`](/azure/bot-service/dotnet/bot-builder-dotnet-create-messages?view=azure-bot-service-3.0#customizing-a-message) Eigenschaft festlegen, um zu steuern, wie der Textinhalt Ihrer Nachricht gerendert wird.

Ausführliche Informationen dazu, wie Microsoft Teams Textformatierungen in Microsoft Teams unterstützt, finden Sie unter [Textformatierung in bot-Nachrichten](~/resources/bot-v3/bots-text-formats.md).

Informationen zum Formatieren von Karten in Nachrichten finden Sie unter [Kartenformatierung](~/task-modules-and-cards/cards/cards-format.md).

## <a name="picture-messages"></a>Bildnachrichten

Bilder werden durch Hinzufügen von Anlagen zu einer Nachricht gesendet. Weitere Informationen zu Anlagen finden Sie in der [bot-Framework-Dokumentation](/azure/bot-service/dotnet/bot-builder-dotnet-add-media-attachments?view=azure-bot-service-3.0).

Bilder können im Format PNG, JPEG oder GIF maximal 1024 × 1024 und 1 MB sein; animierte GIF-Zeichen werden nicht unterstützt.

Es wird empfohlen, die Höhe und Breite jedes Bilds mithilfe von XML anzugeben. Wenn Sie den Abschlag verwenden, beträgt die Bildgröße standardmäßig 256 × 256. Beispiel:

* Verwenden`<img src="http://aka.ms/Fo983c" alt="Duck on a rock" height="150" width="223"></img>`
* Nicht verwenden`![Duck on a rock](http://aka.ms/Fo983c)`

## <a name="receiving-messages"></a>Empfangen von Nachrichten

Je nachdem, welche Bereiche deklariert werden, kann Ihr bot Nachrichten in den folgenden Kontexten empfangen:

* **persönlicher Chat** Benutzer können in einer privaten Unterhaltung mit einem bot interagieren, indem Sie einfach den hinzugefügten bot im Chatverlauf auswählen oder den Namen oder die APP-ID in das Feld an: in einem neuen Chat eingeben.
* **Kanäle** Ein Bot kann ("@_botname_") in einem Kanal erwähnt werden, wenn er dem Team hinzugefügt wurde. Beachten Sie, dass zusätzliche Antworten auf einen bot in einem Kanal den bot erwähnen müssen. Er antwortet nicht auf Antworten, wenn er nicht erwähnt wird.

Bei eingehenden Nachrichten erhält Ihr bot ein [`Activity`](/azure/bot-service/rest-api/bot-framework-rest-connector-activities?view=azure-bot-service-3.0) Objekt vom Typ `messageType: message` . Obwohl das `Activity` Objekt andere Arten von Informationen enthalten kann, wie [Kanal Aktualisierungen](~/resources/bot-v3/bots-notifications.md#channel-updates) , die an Ihren bot gesendet werden, `message` stellt der Typ die Kommunikation zwischen bot und Benutzer dar.

Ihr bot erhält eine Nutzlast, die die Benutzernachricht sowie `Text` andere Informationen über den Benutzer, die Quelle der Nachricht und die Informationen zu Teams enthält. Hinweis:

* `timestamp`Das Datum und die Uhrzeit der Nachricht in koordinierter Weltzeit (Coordinated Universal Time, UTC)
* `localTimestamp`Das Datum und die Uhrzeit der Nachricht in der Zeitzone des Absenders.
* `channelId`Immer "msteams". Dies bezieht sich auf einen bot-Framework-Kanal und nicht auf einen Teams-Kanal.
* `from.id`Eine eindeutige und verschlüsselte ID für diesen Benutzer für Ihren bot; geeignet als Schlüssel, wenn Ihre APP Benutzerdaten speichern muss. Es ist für Ihren bot eindeutig und kann nicht direkt außerhalb ihrer bot-Instanz auf sinnvolle Weise verwendet werden, um diesen Benutzer zu identifizieren.
* `channelData.tenant.id`Die Mandanten-ID für den Benutzer.

> [!NOTE]
> `from.id`ist für Ihren bot eindeutig und kann nicht direkt außerhalb ihrer bot-Instanz auf sinnvolle Weise verwendet werden, um diesen Benutzer zu identifizieren.

## <a name="combining-channel-and-private-interactions-with-your-bot"></a>Kombinieren von Kanal-und privaten Interaktionen mit Ihrem bot

Bei der Interaktion in einem Kanal sollte Ihr bot intelligent sein, bestimmte Unterhaltungen mit einem Benutzer offline zu führen. Nehmen wir beispielsweise an, dass ein Benutzer versucht, eine komplexe Aufgabe zu koordinieren, wie etwa die Planung mit einer Gruppe von Teammitgliedern. Anstatt die gesamte Sequenz von Interaktionen für den Kanal sichtbar zu machen, sollten Sie eine persönliche Chatnachricht an den Benutzer senden. Ihr bot sollte in der Lage sein, den Benutzer problemlos zwischen persönlichen und Kanal Unterhaltungen zu wechseln, ohne den Zustand zu verlieren.

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
> Das Textfeld für eingehende Nachrichten enthält manchmal Erwähnungen. Achten Sie darauf, diese ordnungsgemäß zu überprüfen und zu entfernen. Weitere Informationen finden Sie unter [Mentions](~/resources/bot-v3/bot-conversations/bots-conv-channel.md#-mentions).

## <a name="teams-channel-data"></a>Teams-Kanaldaten

Das `channelData` Objekt enthält Teams-spezifische Informationen und ist die endgültige Quelle für Team-und Kanal-IDs. Sie sollten diese IDs Zwischenspeichern und als Schlüssel für den lokalen Speicher verwenden.

Das `channelData` Objekt wird nicht in Nachrichten in persönlichen Unterhaltungen eingeschlossen, da diese außerhalb eines Kanals stattfinden.

Ein typisches channelData-Objekt in einer an Ihren bot gesendeten Aktivität enthält die folgenden Informationen:

* `eventType`Teams-Ereignistyp; nur in Fällen von [Kanal Änderungsereignissen](~/resources/bot-v3/bots-notifications.md#channel-updates) übergeben
* `tenant.id`Azure Active Directory-Mandanten-ID; in allen Kontexten übergeben
* `team`Wird nur in Kanal Kontexten übergeben, nicht im persönlichen Chat.
  * `id`GUID für den Kanal
  * `name`Name des Teams; nur in Fällen von [Team Umbenennungs Ereignissen](~/resources/bot-v3/bots-notifications.md#team-name-updates) übergeben
* `channel`Wird nur in Kanal Kontexten übergeben, wenn der bot erwähnt wird, oder für Ereignisse in Kanälen in Microsoft Teams, in denen der bot hinzugefügt wurde.
  * `id`GUID für den Kanal
  * `name`Kanal Name; nur in Fällen von [Kanal Änderungsereignissen](~/resources/bot-v3/bots-notifications.md#channel-updates)übergeben.
* `channelData.teamsTeamId`Veraltet. Diese Eigenschaft ist nur für die Abwärtskompatibilität enthalten.
* `channelData.teamsChannelId`Veraltet. Diese Eigenschaft ist nur für die Abwärtskompatibilität enthalten.

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

Das NuGet-Paket " [Microsoft. bot. Connector. Teams](https://www.nuget.org/packages/Microsoft.Bot.Connector.Teams) " stellt ein spezielles `TeamsChannelData` Objekt bereit, das Eigenschaften für den Zugriff auf Teams-spezifische Informationen verfügbar macht.

```csharp
TeamsChannelData channelData = activity.GetChannelData<TeamsChannelData>();
string tenantId = channelData.Tenant.Id;
```

## <a name="sending-replies-to-messages"></a>Senden von Antworten an Nachrichten

Um auf eine vorhandene Nachricht zu antworten, rufen Sie [`ReplyToActivity`](/dotnet/api/microsoft.bot.connector.conversationsextensions.replytoactivityasync?view=botbuilder-dotnet-3.0#Microsoft_Bot_Connector_ConversationsExtensions_ReplyToActivityAsync_Microsoft_Bot_Connector_IConversations_System_String_System_String_Microsoft_Bot_Connector_Activity_System_Threading_CancellationToken_) .net oder [`session.send`](/javascript/api/botbuilder-core/TurnContext?view=botbuilder-ts-latest&viewFallbackFrom=botbuilder-ts-3.0#sendactivities) Node.js auf. Das Robot Builder SDK verarbeitet alle Details.

Wenn Sie sich für die Verwendung der Rest-API entscheiden, können Sie auch den [`/v3/conversations/{conversationId}/activities/{activityId}`](/azure/bot-service/rest-api/bot-framework-rest-connector-send-and-receive-messages?view=azure-bot-service-3.0) Endpunkt aufrufen.

Der Nachrichteninhalt selbst kann einfachen Text oder einige der bereitgestellten [Karten-und Karten Aktionen](~/task-modules-and-cards/cards/cards-actions.md)für bot-Framework enthalten.

Beachten Sie, dass Sie in Ihrem ausgehenden Schema immer das gleiche verwenden sollten, das `serviceUrl` Sie erhalten haben. Beachten Sie, dass der Wert `serviceUrl` tendenziell stabil ist, sich jedoch ändern kann. Wenn eine neue Nachricht eintrifft, sollte Ihr bot den gespeicherten Wert von überprüfen `serviceUrl` .

## <a name="updating-messages"></a>Aktualisieren von Nachrichten

Anstatt Ihre Nachrichten als statische Momentaufnahmen von Daten zu haben, kann Ihr bot Nachrichten Inline nach dem Senden dynamisch aktualisieren. Sie können dynamische Nachrichten Aktualisierungen für Szenarien wie Abruf Aktualisierungen, das Ändern von verfügbaren Aktionen nach einer Tastendruck oder andere asynchrone Statusänderungen verwenden.

Die neue Nachricht muss nicht mit dem Original in Type übereinstimmen. Wenn die ursprüngliche Nachricht beispielsweise eine Anlage enthielt, kann es sich bei der neuen Nachricht um eine einfache Textnachricht handeln.

> [!NOTE]
> Sie können nur Inhalte aktualisieren, die in Einzelanlagen Nachrichten und Karussell Layouts gesendet wurden. Das Veröffentlichen von Aktualisierungen an Nachrichten mit mehreren Anlagen im Listenlayout wird nicht unterstützt.

### <a name="rest-api"></a>REST-API

Um eine Nachrichten Aktualisierung auszugeben, führen Sie einfach eine PUT-Anforderung für den `/v3/conversations/<conversationId>/activities/<activityId>/` Endpunkt mithilfe einer bestimmten Aktivitäts-ID aus. Um dieses Szenario abzuschließen, sollten Sie die vom ursprünglichen Post-Aufruf zurückgegebene Aktivitäts-ID Zwischenspeichern.

```json
PUT /v3/conversations/19%3Aja0cu120i1jod12j%40skype.net/activities/012ujdo0128
{
    "type": "message",
    "text": "This message has been updated"
}
```

### <a name="net-example"></a>.NET-Beispiel

Sie können die `UpdateActivityAsync` -Methode im bot Builder SDK verwenden, um eine vorhandene Nachricht zu aktualisieren.

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

Sie können die `session.connector.update` -Methode im bot Builder SDK verwenden, um eine vorhandene Nachricht zu aktualisieren.

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

Sie können ein persönliches Gespräch mit einem Benutzer erstellen oder eine neue Antwort Kette in einem Kanal für Ihr Team bot starten. Auf diese Weise können Sie Ihre Benutzer oder Benutzer Nachrichten, ohne dass Sie zuerst Kontakt mit Ihrem bot initiieren müssen. Weitere Informationen hierzu finden Sie in den folgenden Themen:

Weitere allgemeine Informationen zu Unterhaltungen, die von Bots gestartet wurden, finden Sie unter [proaktives Messaging für Bots](~/resources/bot-v3/bot-conversations/bots-conv-proactive.md) .

## <a name="deleting-messages"></a>Löschen von Nachrichten

Nachrichten können mithilfe der Connectors [`delete()`](https://docs.botframework.com/node/builder/chat-reference/interfaces/_botbuilder_d_.iconnector.html#delete) -Methode im [BotBuilder SDK](/bot-framework/bot-builder-overview-getstarted)gelöscht werden.

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
