---
title: Tools und SDKs
author: surbhigupta
description: Übersicht über die Tools und SDKs zum Erstellen Microsoft Teams Bots.
ms.topic: overview
ms.localizationpriority: medium
ms.author: anclear
ms.openlocfilehash: 52f933aaddd5a02319ae1c0a35e9a4a26b617b57
ms.sourcegitcommit: 0117c4e750a388a37cc189bba8fc0deafc3fd230
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2022
ms.locfileid: "65104322"
---
# <a name="bots-and-sdks"></a>Tools und SDKs

Sie können einen Bot erstellen, der in Microsoft Teams mit einem der folgenden Tools oder Funktionen funktioniert:

* [Microsoft Bot Framework SDK](#bots-with-the-microsoft-bot-framework)
* [Power Virtual Agents](#bots-with-power-virtual-agents)
* [Virtual Assistant](~/samples/virtual-assistant.md)
* [Webhooks und Connectors](#bots-with-webhooks-and-connectors)

## <a name="bots-with-the-microsoft-bot-framework"></a>Bots mit der Microsoft Bot Framework

Ihr Teams Bot besteht aus folgenden Komponenten:

* Ein öffentlich zugänglicher Webdienst, der von Ihnen gehostet wird.
* Eine Bot Framework-Registrierung für Ihren Webdienst.
* Ihr Teams App-Paket, das den Teams-Client mit Ihrem Webdienst verbindet.

> [!TIP]
> Verwenden Sie das Entwicklerportal, um Ihren Webdienst beim Bot Framework zu registrieren und Ihre App-Konfigurationen anzugeben. Weitere Informationen finden Sie unter [Verwalten Ihrer Apps mit dem Entwicklerportal für Teams](~/concepts/build-and-test/teams-developer-portal.md).

Das [Bot Framework](https://dev.botframework.com/) ist ein umfangreiches SDK zum Erstellen von Bots mit C#, Java, Python und JavaScript. Wenn Sie bereits über einen Bot verfügen, der auf dem Bot Framework basiert, können Sie ihn ganz einfach so ändern, dass er in Teams funktioniert. Nutzen Sie entweder C# oder Node.js, um unsere [SDKs](/microsoftteams/platform/#pivot=sdk-tools) zu nutzen. Diese Pakete erweitern die grundlegenden Klassen und Methoden des Bot Builder-SDKs folgendermaßen:

* Verwenden Sie spezielle Kartentypen wie die Office 365 Connectorkarte.
* Legen Sie Teams spezifischen Kanaldaten zu Aktivitäten fest.
* Verarbeiten von Nachrichtenerweiterungsanforderungen.

> [!IMPORTANT]
> Sie können Teams-Apps in jeder Webprogrammiertechnologie entwickeln und die [Bot Framework-REST-APIs](/bot-framework/rest-api/bot-framework-rest-overview) direkt aufrufen. Sie müssen jedoch in allen Fällen eine Tokenbehandlung durchführen.

## <a name="bots-with-power-virtual-agents"></a>Bots mit Power Virtual Agents

[Power Virtual Agents](/power-virtual-agents/fundamentals-what-is-power-virtual-agents) ist ein Chatbot-Dienst, der auf der Microsoft Power-Plattform und Bot Framework basiert. Der Power Virtual Agent-Entwicklungsprozess verwendet einen geführten, codefreien und grafischen Benutzeroberflächenansatz, der es Ihren Teammitgliedern ermöglicht, auf einfache Weise einen intelligenten virtuellen Agent zu erstellen und zu verwalten. Nachdem Sie Ihren Chatbot im [Power Virtual Agents Portal](https://powervirtualagents.microsoft.com) erstellt haben, können Sie ihn ganz einfach [in Teams integrieren](how-to/add-power-virtual-agents-bot-to-teams.md). Weitere Informationen zu den ersten Schritten finden Sie [in Power Virtual Agents Dokumentation](/power-virtual-agents).

>[!NOTE]
>Sie dürfen Microsoft Power Platform nicht verwenden, um Apps zu erstellen, die im Teams App Store veröffentlicht werden sollen. Microsoft Power Platform-Apps können nur im App Store einer Organisation veröffentlicht werden.

## <a name="bots-with-webhooks-and-connectors"></a>Bots mit Webhooks und Connectors

Webhooks und Connectors verbinden Ihren Bot mit Ihren Webdiensten. Mithilfe von Webhooks und Connectors können Sie einen Bot für grundlegende Interaktionen erstellen, z. B. einen Workflow oder andere einfache Befehle erstellen. Sie sind nur im Team verfügbar, in dem Sie sie erstellen, und sind für einfache Prozesse vorgesehen, die für den Workflow Ihres Unternehmens spezifisch sind. Weitere Informationen finden Sie unter [Webhooks und Connectors](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md).

## <a name="advantages-of-bots"></a>Vorteile von Bots

Bots in Microsoft Teams können Teil einer 1:1-Unterhaltung, eines Gruppenchats oder eines Kanals in einem Team sein. Jeder Bereich bietet einzigartige Möglichkeiten und Herausforderungen für Ihren Unterhaltungsbot.

| In einem Kanal | In einem Gruppenchat | In einem 1:1-Chat. |
| :-- | :-- | :-- |
| Massive Reichweite | Weniger Mitglieder | Traditionelle Art und Weise |
| Präzise individuelle Interaktionen | @mention bot  | F&A-Bots |
| @mention bot | Ähnlich wie Kanal | Bots, die Witze erzählen und Notizen machen |

### <a name="in-a-channel"></a>In einem Kanal

Kanäle enthalten Unterhaltungsthreads zwischen mehreren Personen, sogar bis zu zweitausend. Dies gibt Ihrem Bot potenziell massive Reichweite, aber einzelne Interaktionen müssen präzise sein. Herkömmliche Multi-Turn-Interaktionen funktionieren nicht. Stattdessen müssen Sie nach interaktiven Karten oder Aufgabenmodulen suchen oder die Unterhaltung in eine 1:1-Unterhaltung verschieben, um viele Informationen zu sammeln. Ihr Bot hat nur Zugriff auf Nachrichten, in denen er sich befindet `@mentioned`. Sie können zusätzliche Nachrichten aus der Unterhaltung mithilfe von Microsoft Graph und Berechtigungen auf Organisationsebene abrufen.

Bots funktionieren in einem Kanal in den folgenden Fällen besser:

* Benachrichtigungen, bei denen Sie eine interaktive Karte für Benutzer bereitstellen, um zusätzliche Informationen zu erhalten.
* Feedbackszenarien, z. B. Umfragen und Umfragen.
* Ein einzelner Anforderungs- oder Antwortzyklus löst Interaktionen auf, und die Ergebnisse sind für mehrere Mitglieder der Unterhaltung nützlich.
* Soziale oder lustige Bots, bei denen Sie ein fantastisches Katzenbild erhalten, nach dem Zufallsprinzip einen Gewinner auswählen usw.

### <a name="in-a-group-chat"></a>In einem Gruppenchat

Gruppenchats sind Unterhaltungen ohne Threading zwischen drei oder mehr Personen. Sie weisen tendenziell weniger Mitglieder auf als ein Kanal und sind kurzlebiger. Ähnlich wie bei einem Kanal hat Ihr Bot nur Zugriff auf Nachrichten, in denen er sich direkt befindet `@mentioned` .

In den Fällen, in denen Bots in einem Kanal besser funktionieren, funktionieren auch in einem Gruppenchat besser.

### <a name="in-a-one-to-one-chat"></a>In einem 1:1-Chat.

1:1-Chats sind eine herkömmliche Möglichkeit für einen Unterhaltungs-Bot, mit einem Benutzer zu interagieren. Einige Beispiele für 1:1-Unterhaltungs-Bots sind:

* F&A-Bots
* Bots, die Workflows in anderen Systemen initiieren
* Bots, die Witze erzählen
* bots that take notes Before creating 1-to-one chatbots, consider whether a conversation-based interface is the best way to present your functionality.

## <a name="disadvantages-of-bots"></a>Nachteile von Bots

Ein umfangreiches Dialogfeld zwischen Ihrem Bot und dem Benutzer ist eine langsame und komplexe Möglichkeit, eine Aufgabe zu erledigen. Ein Bot, der übermäßige Befehle unterstützt, insbesondere eine breite Palette von Befehlen, ist nicht erfolgreich oder wird von Benutzern nicht positiv gesehen.

### <a name="have-multi-turn-experiences-in-chat"></a>Multi-Turn-Erfahrungen im Chat

Ein umfangreiches Dialogfeld erfordert, dass der Entwickler den Status aufrechterhält. Um diesen Zustand zu beenden, muss ein Benutzer entweder ein Timeout oder **"Abbrechen"** auswählen. Auch der Prozess ist mühsam. Sehen Sie sich beispielsweise das folgende Unterhaltungsszenario an:

BENUTZER: Plane eine Besprechung mit Marie.

BOT: Ich habe 200 Ergebnisse gefunden, bitte geben Sie einen Vor- und Nachnamen an.

BENUTZER: Plane eine Besprechung mit Marie Krause.

BOT: OK, Wann möchten Sie sich mit Marie Krause treffen?

BENUTZER: um 13:00 Uhr.

BOT: An welchem Tag?

### <a name="support-too-many-commands"></a>Zu viele Befehle unterstützen

Da es im aktuellen Bot-Menü nur sechs sichtbare Befehle gibt, ist es unwahrscheinlich, dass weitere Befehle mit beliebiger Häufigkeit verwendet werden. Bots, die tief in einen bestimmten Bereich gehen, anstatt zu versuchen, eine breite Hilfsarbeit zu sein und es besser zu machen.

### <a name="maintain-a-large-knowledge-base"></a>Verwalten eines großen Wissensdatenbank

Einer der Nachteile von Bots ist, dass es schwierig ist, einen großen Abruf Wissensdatenbank mit nicht gerankten Antworten aufrechtzuerhalten. Bots eignen sich am besten für kurze, schnelle Interaktionen und nicht für lange Listen, die nach einer Antwort suchen.

## <a name="code-snippets"></a>Codeausschnitte

Der folgende Code enthält ein Beispiel für Bot-Aktivitäten für einen Kanalteambereich:

# <a name="c"></a>[C#](#tab/dotnet)

```csharp

protected override async Task OnMessageActivityAsync(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
{
    var mention = new Mention
    {
        Mentioned = turnContext.Activity.From,
        Text = $"<at>{XmlConvert.EncodeName(turnContext.Activity.From.Name)}</at>",
    };

    var replyActivity = MessageFactory.Text($"Hello {mention.Text}.");
    replyActivity.Entities = new List<Entity> { mention };

    await turnContext.SendActivityAsync(replyActivity, cancellationToken);
}

```

# <a name="nodejs"></a>[Node.js](#tab/nodejs)

```javascript

this.onMessage(async (turnContext, next) => {
    const mention = {
        mentioned: turnContext.activity.from,
        text: `<at>${ new TextEncoder().encode(turnContext.activity.from.name) }</at>`,
    } as Mention;

    const replyActivity = MessageFactory.text(`Hello ${mention.text}`);
    replyActivity.entities = [mention];

    await turnContext.sendActivity(replyActivity);

    // By calling next() you ensure that the next BotHandler is run.
    await next();
});

```

---

Der folgende Code enthält ein Beispiel für Bot-Aktivitäten für einen 1:1-Chat:

# <a name="c"></a>[C#](#tab/dotnet)

```csharp

// Handle message activity
protected override async Task OnMessageActivityAsync(ITurnContext<IMessageActivity> turnContext, CancellationToken cancellationToken)
{
    turnContext.Activity.RemoveRecipientMention();
    var text = turnContext.Activity.Text.Trim().ToLower();
  await turnContext.SendActivityAsync(MessageFactory.Text($"Your message is {text}."), cancellationToken);
}
```

# <a name="nodejs"></a>[Node.js](#tab/nodejs)

```javascript
this.onMessage(async (context, next) => {
    await context.sendActivity(MessageFactory.text("Your message is:" + context.activity.text));
    await next();
});
```

---

## <a name="code-sample"></a>Codebeispiel

|Beispielname | Beschreibung | .NETCore | Node.js | Python|
|----------------|-----------------|--------------|----------------|-------|
| Teams-Unterhaltungsbot | Verarbeitung von Nachrichten- und Unterhaltungsereignissen. |[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/57.teams-conversation-bot)|[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/57.teams-conversation-bot)|[View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python/57.teams-conversation-bot)|
| Bot-Beispiele | Gruppe von Bot-Beispielen | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore) |[View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs)|[View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python)|

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Bot-Aktivitätenhandler](~/bots/bot-basics.md)

## <a name="see-also"></a>Siehe auch

* [Bots für Anrufe und Besprechungen](~/bots/calls-and-meetings/calls-meetings-bots-overview.md)
* [Bot-Unterhaltungen](~/bots/how-to/conversations/conversation-basics.md)
* [Bot-Befehlsmenüs](~/bots/how-to/create-a-bot-commands-menu.md)
* [Authentifizierungsfluss für Bots in Microsoft Teams](~/bots/how-to/authentication/auth-flow-bot.md)
* [Verwenden von Aufgabenmodulen aus Bots](~/task-modules-and-cards/task-modules/task-modules-bots.md)
