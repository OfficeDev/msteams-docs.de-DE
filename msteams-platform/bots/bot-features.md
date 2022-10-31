---
title: Tools und SDKs
author: surbhigupta
description: In diesem Artikel erfahren Sie mehr über Tools und Bot Framework SDKs (C#, Python, Java, JavaScript) für Microsoft Teams-Bots und ihre Vor- und Nachteile.
ms.topic: overview
ms.localizationpriority: medium
ms.author: anclear
ms.openlocfilehash: e1be981a381846ab17220254336571ea40bf2752
ms.sourcegitcommit: 10debe0f01574a21aab54bfac692a4c8373263a8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2022
ms.locfileid: "68789898"
---
# <a name="bots-and-sdks"></a>Tools und SDKs

Mit den folgenden Tools oder Funktionen können Sie einen Bot für die Verwendung in Microsoft Teams erstellen:

* [Microsoft Bot Framework SDK](#bots-with-the-microsoft-bot-framework)
* [Azure Active Directory](~/bots/how-to/authentication/auth-aad-sso-bots.md#develop-an-sso-teams-bot)
* [Entwicklerportal](~/concepts/build-and-test/manage-your-apps-in-developer-portal.md#configure)
* [Power Virtual Agents](#bots-with-power-virtual-agents)
* [Virtual Assistant](~/samples/virtual-assistant.md)
* [Webhooks und Connectors](#bots-with-webhooks-and-connectors)

## <a name="bots-with-the-microsoft-bot-framework"></a>Bots mit Microsoft Bot Framework

Ihr Teams-Bot besteht aus folgenden Komponenten:

* Einem öffentlich zugänglichen von Ihnen gehosteten Webdienst.
* Eine Microsoft Bot Framework-Registrierung für Ihren Webdienst.
* Ihrem Teams App-Paket, das den Teams-Client mit Ihrem Webdienst verbindet.

> [!TIP]
> Verwenden Sie das Entwicklerportal, um Ihren Webdienst bei Microsoft Bot Framework zu registrieren und Ihre App-Konfigurationen anzugeben. Weitere Informationen finden Sie unter [Verwalten Ihrer Apps mit dem Entwicklerportal für Microsoft Teams](~/concepts/build-and-test/teams-developer-portal.md).

[Microsoft Bot Framework](https://dev.botframework.com/) ist ein umfangreiches SDK zur Erstellung von Bots mit C#, Java, Python und JavaScript. Wenn Sie bereits über einen Bot verfügen, der auf Microsoft Bot Framework basiert, können Sie ihn mühelos zur Verwendung in Microsoft Teams ändern. Microsoft empfiehlt die Verwendung von C# oder Node.js, um unsere [SDKs](/microsoftteams/platform/#pivot=sdk-tools) nutzen zu können. Diese Pakete erweitern die grundlegenden Klassen und Methoden des Bot Builder-SDKs folgendermaßen:

* Sie können spezielle Kartentypen wie die Office 365-Connector-Karte verwenden.
* Sie können Teams-spezifische Kanaldaten zu Aktivitäten festlegen.
* Sie können Nachrichtenerweiterungsanforderungen verarbeiten.

> [!IMPORTANT]
> You can develop Teams apps in any web programming technology and call the [Bot Framework REST APIs](/bot-framework/rest-api/bot-framework-rest-overview) directly. But you must perform token handling in all cases.

## <a name="bots-with-power-virtual-agents"></a>Bots mit Power Virtual Agents

[Power Virtual Agents](/power-virtual-agents/fundamentals-what-is-power-virtual-agents) ist ein Chatbotdienst, der auf Microsoft Power Platform und Microsoft Bot Framework aufbaut. Der Power Virtual Agent-Entwicklungsprozess verwendet einen geführten Ansatz ohne Code mit einer grafischen Schnittstelle, um Ihre Teammitglieder in die Lage zu versetzen, mühelos einen intelligenten virtuellen Agent zu erstellen und zu pflegen. Sobald Sie Ihr Chatbot im [Power Virtual Agents-Portal](https://powervirtualagents.microsoft.com) erstellt haben, können Sie ihn mühelos [in Microsoft Teams integrieren](how-to/add-power-virtual-agents-bot-to-teams.md). Weitere Informationen zu den ersten Schritten finden Sie in der [Power Virtual Agents-Dokumentation](/power-virtual-agents).

>[!NOTE]
>Sie dürfen mit Microsoft Power Platform erstellte Apps nicht im Teams App Store veröffentlichen. Microsoft Power Platform-Apps können nur im App Store einer Organisation veröffentlicht werden.

## <a name="bots-with-webhooks-and-connectors"></a>Bots mit Webhooks und Connectors

Webhooks und Connectors verbinden Ihren Bot mit Ihren Webdiensten. Mit Webhooks und Connectors können Sie einen Bot für grundlegende Interaktionen erstellen, wie das Erstellen eines Workflows oder andere einfache Befehle. Sie sind nur in dem Team verfügbar, in dem Sie sie erstellen, und sind für einfache Prozesse vorgesehen, die für den Workflow Ihres Unternehmens spezifisch sind. Unter [Was sind Webhooks und Connectors?](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md) finden Sie weitere Informationen.

## <a name="advantages-of-bots"></a>Vorteile von Bots

Bots in Microsoft Teams können Teil einer 1:1-Unterhaltung, eines Gruppenchats oder eines Kanals in einem Team sein. Jeder Bereich bietet für Ihren Unterhaltungs-Bot besondere Chancen und Herausforderungen.

| In einem Kanal | In einem Gruppenchat | In einem 1:1-Chat. |
| :-- | :-- | :-- |
| Massive Reichweite | Weniger Mitglieder | Traditionelle Art und Weise |
| Präzise individuelle Interaktionen | @erwähnen-Bot  | F&A-Bots |
| @erwähnen-Bot | Ähnlich wie Kanal | Bots, die Witze erzählen und Notizen machen |

### <a name="in-a-channel"></a>In einem Kanal

Kanäle enthalten Unterhaltungsthreads zwischen mehreren Personen (bis zu 2.000). Dadurch erhält Ihr Bot potenziell eine enorme Reichweite, die einzelnen Interaktionen müssen aber präzise sein. Herkömmliche Multi-Turn-Interaktionen funktionieren nicht. Stattdessen müssen Sie versuchen, interaktive Karten oder Aufgabenmodule einzusetzen, oder die Unterhaltung in eine 1:1-Unterhaltung auszulagern, um viele Informationen zu sammeln. Ihr Bot hat nur Zugriff auf Nachrichten, bei denen es sich um handelt `@mentioned`. Mithilfe von Microsoft Graph und Berechtigungen auf Organisationsebene können Sie zusätzliche Nachrichten aus der Unterhaltung abrufen.

Bots funktionieren in einem Kanal in den folgenden Fällen besser:

* Benachrichtigungen, wenn Sie eine interaktive Karte für die Benutzer bereitstellen, die weitere Informationen aufnimmt.
* Feedbackszenarien wie Abstimmungen und Umfragen.
* Ein einzelner Anforderungs- oder Antwortzyklus löst Interaktionen auf, und die Ergebnisse sind für mehrere Mitglieder der Unterhaltung nützlich.
* Soziale/Spaß-Bots, bei denen Sie tolle Katzenbilder erhalten, zufällig einen Gewinner auswählen, usw.

### <a name="in-a-group-chat"></a>In einem Gruppenchat

Gruppenchats sind Unterhaltungen ohne Threading zwischen drei oder mehr Personen. Sie weisen tendenziell weniger Mitglieder auf als ein Kanal und sind kurzlebiger. Ähnlich wie bei einem Kanal hat Ihr Bot nur Zugriff auf Nachrichten, bei denen er sich direkt befindet `@mentioned` .

In den Fällen, in denen Bots in einem Kanal besser funktionieren, funktionieren auch in einem Gruppenchat besser.

### <a name="in-a-one-to-one-chat"></a>In einem 1:1-Chat.

Ein 1:1-Chat ist ein herkömmliches Interaktionsverfahren eines Unterhaltungs-Bots mit einem Benutzer. Einige Beispiele für 1:1-Unterhaltungs-Bots sind:

* F&A-Bots
* Bots, die Workflows in anderen Systemen initiieren.
* Bots, die Witze erzählen.
* Bots, die Notizen erstellen.
Überlegen Sie vor dem Erstellen von 1:1-Chatbots, ob eine konversationsbasierte Schnittstelle die beste Möglichkeit ist, Ihre Funktionalität darzustellen.

## <a name="disadvantages-of-bots"></a>Nachteile von Bots

Ein umfangreicher Dialog zwischen Ihrem Bot und dem Benutzer ist ein langsamer und übermäßig komplexer Weg, um eine Aufgabe zu erledigen. Ein Bot, der übermäßige Befehle unterstützt, insbesondere eine breite Palette von Befehlen, wird von Benutzern nicht erfolgreich oder positiv angesehen.

### <a name="have-multi-turn-experiences-in-chat"></a>Komplexe Aufgaben im Chat

Ein umfangreiches Dialogfeld erfordert, dass der Entwickler den Status beibehält. Um diesen Zustand zu beenden, muss ein Benutzer entweder ein Timeout ausführen oder **Abbrechen** auswählen. Auch der Prozess ist mühsam. Sehen Sie sich beispielsweise das folgende Unterhaltungsszenario an:

BENUTZER: Plane eine Besprechung mit Marie.

BOT: Ich habe 200 Ergebnisse gefunden, bitte geben Sie einen Vor- und Nachnamen an.

BENUTZER: Plane eine Besprechung mit Marie Krause.

BOT: OK, Wann möchten Sie sich mit Marie Krause treffen?

BENUTZER: um 13:00 Uhr.

BOT: An welchem Tag?

### <a name="support-too-many-commands"></a>Unterstützung zu vieler Befehle

Da es im aktuellen Bot-Menü nur sechs sichtbare Befehle gibt, wird alles andere wahrscheinlich nicht häufig verwendet. Bots, die detailliert auf einen bestimmten Bereich eingehen, anstatt zu versuchen, ein allgemeiner Assistent zu sein, werden besser funktionieren und besser abschneiden.

### <a name="maintain-a-large-knowledge-base"></a>Verwalten eines großen Wissensdatenbank

Einer der Nachteile von Bots besteht darin, dass es schwierig ist, eine große Abruf-Wissensdatenbank mit Antworten ohne Rangfolge aufrechtzuerhalten. Bots sind am besten für kurze, schnelle Interaktionen geeignet, nicht für das Durchsuchen langer Listen auf der Suche nach einer Antwort.

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
| Teams-Unterhaltungsbot | Verarbeitung von Nachrichten- und Unterhaltungsereignissen. |[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/57.teams-conversation-bot)|[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/57.teams-conversation-bot)|[Anzeigen](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python/57.teams-conversation-bot)|
| Bot-Beispiele | Gruppe von Bot-Beispielen | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore) |[View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs)|[Anzeigen](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python)|

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Bot-Aktivitätenhandler](~/bots/bot-basics.md)

## <a name="see-also"></a>Siehe auch

* [Bots für Anrufe und Besprechungen](~/bots/calls-and-meetings/calls-meetings-bots-overview.md)
* [Bot-Unterhaltungen](~/bots/how-to/conversations/conversation-basics.md)
* [Bot-Befehlsmenüs](~/bots/how-to/create-a-bot-commands-menu.md)
* [Erstellen von benutzerdefinierten Triggern in Bot Framework Composer](/composer/how-to-create-custom-triggers)
* [Authentifizierungsfluss für Bots in Microsoft Teams](~/bots/how-to/authentication/auth-flow-bot.md)
* [Verwenden von Aufgabenmodulen aus Bots](~/task-modules-and-cards/task-modules/task-modules-bots.md)
* [Veröffentlichen Ihres Bots in Azure](/azure/bot-service/bot-builder-deploy-az-cli)
* [API-Referenz für den Bot Framework Connector-Dienst](/azure/bot-service/rest-api/bot-framework-rest-connector-api-reference)
