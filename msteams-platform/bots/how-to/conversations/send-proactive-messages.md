---
title: Senden proaktiver Nachrichten
description: Erfahren Sie, wie Sie proaktive Nachrichten mit Ihrem Teams-Bot senden, Ihre App mit Microsoft Graph installieren und Codebeispiele basierend auf Bot Framework SDK v4 überprüfen.
ms.topic: conceptual
ms.author: surbhigupta
ms.localizationpriority: high
ms.openlocfilehash: adecf29766909fb9a8692aa135e09c41a307c867
ms.sourcegitcommit: 82c585d287d61924ce3a3bba3e9caeff35c9a27a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/02/2022
ms.locfileid: "67586903"
---
# <a name="proactive-messages"></a>Proaktive Nachrichten

[!INCLUDE [v4 to v3 pointer](~/includes/v4-to-v3-pointer-bots.md)]

Eine proaktive Nachricht ist jede Nachricht, die von einem Bot gesendet wird, die nicht als Antwort auf eine Anforderung eines Benutzers gesendet wurde. Diese Nachricht kann Inhalte enthalten, z. B.:

* Willkommensnachrichten
* Benachrichtigungen
* Geplante Nachrichten

> [!IMPORTANT]
> Bots sind in Government Community Cloud (GCC) und GCC-High aber nicht in DOD-Umgebungen (Department of Defense) verfügbar.
>
> Für proaktive Nachrichten sollten die Bots die folgenden Endpunkte für Government Cloud-Umgebungen verwenden:
>
> * GCC: `https://smba.infra.gcc.teams.microsoft.com/gcc`.
> * GCCH: `https://smba.infra.gov.teams.microsoft.us/gcch`.

Um eine proaktive Nachricht an einen Benutzer, einen Gruppenchat oder ein Team zu senden, muss Ihr Bot über den erforderlichen Zugriff zum Senden der Nachricht verfügen. Für einen Gruppenchat oder ein Team muss die App, die Ihren Bot enthält, zuerst an diesem Speicherort installiert werden.

Sie können [Ihre App bei Bedarf proaktiv mitHilfe von Microsoft Graph](#proactively-install-your-app-using-graph) in einem Team installieren oder eine [benutzerdefinierte App-Richtlinie](/microsoftteams/teams-custom-app-policies-and-settings) verwenden, um eine App in Ihren Teams und für die Benutzer der Organisation zu installieren. Für bestimmte Szenarien müssen Sie [Ihre App proaktiv mithilfe von Graph installieren](#proactively-install-your-app-using-graph). Damit ein Benutzer proaktive Nachrichten empfängt, installieren Sie die App für den Benutzer, oder machen Sie den Benutzer zu einem Teil eines Teams, in dem die App installiert ist.

Das Senden einer proaktiven Nachricht unterscheidet sich vom Senden einer regulären Nachricht. Es ist keine aktive `turnContext` für eine Antwort vorhanden. Sie müssen die Unterhaltung erstellen, bevor Sie die Nachricht senden. Beispielsweise ein neuer 1:1-Chat oder ein neuer Unterhaltungsthread in einem Kanal. Sie können keinen neuen Gruppenchat oder einen neuen Kanal in einem Team mit proaktivem Messaging erstellen.

Folgen Sie diesen Schritten, um eine proaktive Nachricht zu senden:

1. [Abrufen der Benutzer-ID, Team-ID oder Kanal-ID](#get-the-user-id-team-id-or-channel-id), falls erforderlich.
1. [Erstellen der Unterhaltung](#create-the-conversation), falls erforderlich.
1. [Abrufen der Konversations-ID](#get-the-conversation-id).
1. [Senden der Nachricht](#send-the-message).

Die Codeausschnitte im [Beispielabschnitt](#samples) dienen zum Erstellen einer 1:1-Unterhaltung. Links zu Beispielen für 1:1-Unterhaltungen und Gruppen- oder Kanalnachrichten finden Sie im [Codebeispiel](#code-sample). Um proaktive Nachrichten effektiv zu verwenden, lesen Sie [bewährte Methoden für proaktives Messaging](#best-practices-for-proactive-messaging).

## <a name="get-the-user-id-team-id-or-channel-id"></a>Abrufen der Benutzer-ID, Team-ID oder Kanal-ID

Um eine neue Unterhaltung oder einen Unterhaltungsthread in einem Kanal zu erstellen, müssen Sie über die richtige ID verfügen. Sie können diese ID auf eine der folgenden Arten empfangen oder abrufen:

* Wenn Ihre App in einem bestimmten Kontext installiert wird, erhalten Sie eine [`onMembersAdded` Aktivität](~/bots/how-to/conversations/subscribe-to-conversation-events.md).
* Wenn ein neuer Benutzer zu einem Kontext hinzugefügt wird, in dem Ihre App installiert ist, erhalten Sie eine [`onMembersAdded` Aktivität](~/bots/how-to/conversations/subscribe-to-conversation-events.md).
* Jedes Ereignis, das der Bot empfängt, enthält die erforderlichen Informationen, die Sie aus dem Botkontext abrufen können (TurnContext-Objekt).
* Sie können in einem Team, in dem Ihre App installiert ist, die [Liste der Kanäle](~/bots/how-to/get-teams-context.md) abrufen.
* Sie können die [Liste der Mitglieder](~/bots/how-to/get-teams-context.md) eines Teams abrufen, in dem Ihre App installiert ist.

Unabhängig davon, wie Sie die Informationen erhalten, speichern Sie die `tenantId` und entweder die `userId` oder `channelId` um eine neue Unterhaltung zu erstellen. Sie können auch die `teamId` verwenden, um einen neuen Unterhaltungsthread im allgemeinen oder Standardkanal eines Teams zu erstellen.

Die `userId` ist für Ihre Bot-ID und einen bestimmten Benutzer eindeutig. Sie können die `userId` zwischen Bots nicht wiederverwenden. Die `channelId` ist global. Installieren Sie den Bot jedoch im Team, bevor Sie eine proaktive Nachricht an einen Kanal senden können.

Erstellen Sie die Unterhaltung, nachdem Sie die Benutzer- oder Kanalinformationen erhalten haben.

## <a name="create-the-conversation"></a>Erstellen der Unterhaltung

Erstellen Sie die Unterhaltung, wenn sie nicht vorhanden ist oder Sie die `conversationId`Unterhaltung nicht kennen. Erstellen Sie die Unterhaltung nur einmal, und speichern Sie den Wert oder `conversationReference` das `conversationId` Objekt.

Sie können die Unterhaltung abrufen, wenn die App zum ersten Mal installiert wird. Rufen Sie nach dem Erstellen [der Unterhaltung die Unterhaltungs-ID ab](#get-the-conversation-id). Die `conversationId` ist in den Aktualisierungsereignissen der Unterhaltung verfügbar.

Wenn Sie nicht über die `conversationId`verfügen, können Sie [Ihre App proaktiv mit Graph installieren](#proactively-install-your-app-using-graph) , um die `conversationId`App abzurufen.

## <a name="get-the-conversation-id"></a>Abrufen der Konversations-ID

Verwenden Sie entweder das `conversationReference`-Objekt oder `conversationId` und `tenantId`, um die Nachricht zu senden. Sie können diese ID abrufen, indem Sie entweder die Konversation erstellen oder sie aus jeder Aktivität speichern, die aus diesem Kontext an Sie gesendet wird. Speichern Sie diese ID als Referenz.

Nachdem Sie die entsprechenden Adressinformationen erhalten haben, können Sie Ihre Nachricht senden.

## <a name="send-the-message"></a>Senden der Nachricht

Nachdem Sie nun über die richtigen Adressinformationen verfügen, können Sie Ihre Nachricht senden. Wenn Sie das SDK verwenden, müssen Sie die `continueConversation`-Methode sowie die `conversationId` und `tenantId` verwenden, um einen direkten API-Aufruf zu tätigen. Um Ihre Nachricht zu senden, legen Sie den Wert fest `conversationParameters`. Sehen Sie sich den Abschnitt [Beispiele](#samples) an, oder verwenden Sie eines der Beispiele, die im Abschnitt [Codebeispiel](#code-sample) aufgeführt sind.

> [!NOTE]
> Teams unterstützt nicht das Senden proaktiver Nachrichten mithilfe von E-Mail oder Benutzerprinzipalname (User Principal Name, UPN).

Nachdem Sie die proaktive Nachricht gesendet haben, müssen Sie diese bewährten Methoden befolgen und proaktive Nachrichten senden, um einen besseren Informationsaustausch zwischen Benutzern und dem Bot zu ermöglichen.

Im folgenden Video erfahren Sie, wie Sie proaktive Nachrichten aus Bots senden:

<br>

> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4NHyk]
<br>

### <a name="understand-who-blocked-muted-or-uninstalled-a-bot"></a>Verstehen, wer einen Bot blockiert, stummgeschaltet oder deinstalliert hat

Als Entwickler können Sie einen Bericht erstellen, um zu verstehen, welche Benutzer in Ihrer Organisation einen Bot blockiert, stummgeschaltet oder deinstalliert haben. Diese Informationen können den Administratoren Ihrer Organisation helfen, organisationsweite Nachrichten zu übertragen oder die App-Nutzung zu fördern.

Mithilfe von Teams können Sie eine proaktive Nachricht an den Bot senden, um zu überprüfen, ob ein Benutzer einen Bot blockiert oder deinstalliert hat. Wenn der Bot blockiert oder deinstalliert wird, gibt Teams einen Antwortcode mit einem `403` `subCode: MessageWritesBlocked`zurück. Diese Antwort gibt an, dass die vom Bot gesendete Nachricht nicht an den Benutzer übermittelt wird.

Der Antwortcode wird pro Benutzer gesendet und enthält die Identität des Benutzers. Sie können die Antwortcodes für jeden Benutzer zusammen mit seiner Identität kompilieren, um einen Bericht aller Benutzer zu erstellen, die den Bot blockiert haben.

Nachfolgend finden Sie ein Beispiel für einen 403-Antwortcode.

```http

HTTP/1.1 403 Forbidden

Cache-Control: no-store, must-revalidate, no-cache

 Pragma: no-cache

 Content-Length: 196

 Content-Type: application/json; charset=utf-8

 Server: Microsoft-HTTPAPI/2.0

 Strict-Transport-Security: max-age=31536000; includeSubDomains

 MS-CV: NXZpLk030UGsuHjPdwyhLw.5.0

 ContextId: tcid=0,server=msgapi-canary-eus2-0,cv=NXZpLk030UGsuHjPdwyhLw.5.0

 Date: Tue, 29 Mar 2022 17:34:33 GMT

{"errorCode":209,"message":"{\r\n  \"subCode\": \"MessageWritesBlocked\",\r\n  \"details\": \"Thread is blocked from message writes.\",\r\n  \"errorCode\": null,\r\n  \"errorSubCode\": null\r\n}"}
```

## <a name="best-practices-for-proactive-messaging"></a>Bewährte Methoden für proaktives Messaging

Das Senden proaktiver Nachrichten an die Benutzer ist eine effektive Möglichkeit, mit Ihren Benutzern zu kommunizieren. Aus Sicht des Benutzers wird die Nachricht jedoch unaufgefordert angezeigt. Wenn es eine Willkommensnachricht gibt, ist dies das erste Mal, dass er mit Ihrer App interagiert. Es ist wichtig, diese Funktion zu verwenden und dem Benutzer die vollständigen Informationen bereitzustellen, damit sie den Zweck dieser Nachricht verstehen.

### <a name="welcome-messages"></a>Willkommensnachrichten

Wenn proaktives Messaging verwendet wird, um eine Willkommensnachricht an einen Benutzer zu senden, gibt es keinen Kontext dafür, warum der Benutzer die Nachricht empfängt. Außerdem ist dies die erste Interaktion des Benutzers mit Ihrer App. Es ist eine Gelegenheit, für einen guten ersten Eindruck zu sorgen. Eine gute Benutzererfahrung sorgt für eine bessere Akzeptanz der App. Schlechte Begrüßungsnachrichten können die Benutzer dazu führen, Ihre App zu blockieren. Schreiben Sie eine klare Willkommensnachricht, und durchlaufen Sie die Willkommensnachricht, wenn sie nicht die gewünschte Wirkung hat.

Eine gute Willkommensnachricht kann Folgendes umfassen:

* Grund für die Nachricht – Dem Benutzer muss klar sein, warum er die Nachricht empfängt. Wenn Ihr Bot in einem Kanal installiert wurde und Sie allen Benutzern eine Willkommensnachricht gesendet haben, teilen Sie ihnen mit, in welchem Kanal er installiert wurde und wer ihn installiert hat.

* Ihr Angebot – Benutzer müssen in der Lage sein, zu erkennen, was sie mit Ihrer App tun können und welchen Wert Sie ihnen bringen können.

* Nächste Schritte – Benutzer sollten die nächsten Schritte verstehen. Laden Sie z. B. Benutzer ein, einen Befehl auszuprobieren oder mit Ihrer App zu interagieren.

### <a name="notification-messages"></a>Benachrichtigungen

Um Benachrichtigungen mit proaktivem Messaging zu senden, stellen Sie sicher, dass Ihre Benutzer einen eindeutigen Pfad haben, um allgemeine Aktionen basierend auf Ihrer Benachrichtigung auszuführen. Stellen Sie sicher, dass Benutzer über ein klares Verständnis dafür verfügen, warum sie eine Benachrichtigung erhalten haben. Gute Benachrichtigungen enthalten im Allgemeinen die folgenden Elemente:

* Was ist geschehen? Klare Angaben dazu, wodurch die Benachrichtigung ausgelöst wurde.

* Was war das Ergebnis? Es muss klar sein, welches Element aktualisiert wird, um die Benachrichtigung zu erhalten.

* Wer oder was hat es ausgelöst? Wer oder was eine Aktion ausgeführt hat, was dazu führte, dass die Benachrichtigung gesendet wurde.

* Was können die Benutzer als Reaktion darauf tun? Erleichtern Sie es Ihren Benutzern, Aktionen basierend auf Ihren Benachrichtigungen durchzuführen.

* Wie können Benutzer sich vom Erhalt von Benachrichtigungen abmelden? Sie müssen einen Pfad angeben, über den Benutzer weitere Benachrichtigungen ablehnen können.

Um Nachrichten an eine große Gruppe von Benutzern zu senden, z. B. an Ihre Organisation, installieren Sie Ihre App proaktiv mithilfe von Graph.

### <a name="scheduled-messages"></a>Geplante Nachrichten

Wenn Sie proaktives Messaging verwenden, um geplante Nachrichten an Benutzer zu senden, überprüfen Sie, ob Ihre Zeitzone auf ihre Zeitzone aktualisiert wurde. Dadurch wird sichergestellt, dass die Nachrichten zum entsprechenden Zeitpunkt an die Benutzer übermittelt werden. Geplante Nachrichten umfassen in der Regel Folgendes:

* Warum erhält der Benutzer die Nachricht? Erleichtern Sie es Ihren Benutzern, zu verstehen, warum sie die Nachricht erhalten.

* Was kann der Benutzer als Nächstes tun? Benutzer können die erforderliche Aktion basierend auf dem Nachrichteninhalt ausführen.

## <a name="proactively-install-your-app-using-graph"></a>Proaktives Installieren Ihrer App mit Graph

Proaktive Nachricht an Benutzer senden, die Ihre App zuvor nicht installiert oder mit Ihr interagiert haben. Sie sollten beispielsweise den [Unternehmens-Communicator](~/samples/app-templates.md#company-communicator) verwenden, um Nachrichten an Ihre gesamte Organisation zu senden. In diesem Fall können Sie die Graph-API verwenden, um Ihre App proaktiv für Ihre Benutzer zu installieren. Speichern Sie die erforderlichen Werte aus dem `conversationUpdate` Ereignis zwischen, das Ihre App bei der Installation empfängt.

Sie können nur Apps installieren, die sich im App-Katalog Ihrer Organisation oder im Teams-App Store befinden.

Weitere Informationen finden Sie unter [Installieren von Apps für Benutzer](/graph/api/userteamwork-post-installedapps) in der Graph-Dokumentation und [proaktive Botinstallation und -messaging in Teams mit Graph](../../../graph-api/proactive-bots-and-messages/graph-proactive-bots-and-messages.md). Es gibt auch ein [Microsoft .NET Frameworkbeispiel](https://github.com/microsoftgraph/contoso-airlines-teams-sample/blob/283523d45f5ce416111dfc34b8e49728b5012739/project/Models/GraphService.cs#L176) auf der GitHub-Plattform.

## <a name="samples"></a>Beispiele

Der folgende Code zeigt, wie Proaktive Nachrichten gesendet werden:

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

# <a name="json"></a>[JSON](#tab/json)

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

## <a name="code-sample"></a>Codebeispiel

Die folgende Tabelle enthält ein einfaches Codebeispiel, das den grundlegenden Konversationsfluss in eine Microsoft Teams-Anwendung einbezieht und wie Sie einen neuen Konversationsthread in einem Kanal in Microsoft Teams erstellen:

| **Beispielname** | **Beschreibung** | **.NET** | **Node.js** | **Python** |
|---------------|--------------|--------|-------------|--------|
| Grundlagen zu Teams-Unterhaltungen  | Veranschaulicht die Grundlagen von Unterhaltungen in Teams, einschließlich des Sendens proaktiver 1:1-Nachrichten.| [View](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/csharp_dotnetcore/57.teams-conversation-bot) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/57.teams-conversation-bot) | [View](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/python/57.teams-conversation-bot) |
| Starten eines neuen Threads in einem Kanal | Veranschaulicht das Erstellen eines neuen Threads in einem Kanal. | [View](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/csharp_dotnetcore/58.teams-start-new-thread-in-channel) | [View](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/javascript_nodejs/58.teams-start-new-thread-in-channel) | [View](https://github.com/microsoft/BotBuilder-Samples/blob/master/samples/python/58.teams-start-thread-in-channel) |
| Proaktive Installation der App und Senden proaktiver Benachrichtigungen | Dieses Beispiel zeigt, wie Sie die proaktive Installation der App für Benutzer verwenden und proaktive Benachrichtigungen senden können, indem Sie Microsoft Graph APIs aufrufen. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/graph-proactive-installation/csharp) | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/graph-proactive-installation/nodejs) | |
| Proaktives Messaging | Dies ist ein Beispiel, das zeigt, wie Sie die Unterhaltungsreferenzinformationen des Benutzers speichern, um proaktive Erinnerungsnachrichten mithilfe von Bots zu senden. | In Kürze verfügbar | [Anzeigen](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-proactive-messaging-teamsfx) | - |

> [!div class="nextstepaction"]
> [Weitere Codebeispiele für proaktives Messaging](/samples/officedev/msteams-samples-proactive-messaging/msteams-samples-proactive-messaging/)

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Formatieren von Bot-Nachrichten](~/bots/how-to/format-your-bot-messages.md)

## <a name="see-also"></a>Siehe auch

* [**Codebeispiele für proaktives Messaging in Teams**](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-proactive-messaging/csharp)
* [Kanal- und Gruppenchatunterhaltungen mit einem Bot](~/bots/how-to/conversations/channel-and-group-conversations.md)
* [Auf die Aktion zum Absenden des Aufgabenmoduls reagieren](~/messaging-extensions/how-to/action-commands/respond-to-task-module-submit.md)
* [Proaktive Benachrichtigungen an Benutzer senden](/azure/bot-service/bot-builder-howto-proactive-message)
* [Erstellen Ihrer ersten Bot-App mit JavaScript](../../../sbs-gs-bot.yml)
* [Erstellen eines Benachrichtigungs-Bots mit JavaScript zum Senden einer proaktiven Nachricht](../../../sbs-gs-notificationbot.yml)
* [TurnContext](/javascript/api/botbuilder-core/turncontext?view=botbuilder-ts-latest"&preserve-view=true")
