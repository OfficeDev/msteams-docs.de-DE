---
title: Messaging-Erweiterungen
author: surbhigupta
description: Eine Übersicht über Messaging-Erweiterungen auf der Microsoft Teams-Plattform
ms.localizationpriority: medium
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: 696bd7e97cd2588dc62d934c79a9cd2e9310d07d
ms.sourcegitcommit: 2fdca6fb0ade3f6b460eb9a4dfea0a8e2ab8d3b9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/08/2022
ms.locfileid: "63355993"
---
# <a name="messaging-extensions"></a>Messaging-Erweiterungen

Messaging-Erweiterungen ermöglichen benutzern die Interaktion mit Ihrem Webdienst über Schaltflächen und Formulare im Microsoft Teams Client. Sie können Aktionen in einem externen System im Bereich zum Verfassen von Nachrichten, im Befehlsfeld oder direkt in einer Nachricht suchen oder initiieren. Sie können die Ergebnisse dieser Interaktion in Form einer rich-formatierten Karte an den Microsoft Teams-Client zurücksenden. Dieses Dokument bietet eine Übersicht über die Messaging-Erweiterung, Aufgaben, die in verschiedenen Szenarien ausgeführt werden, das Arbeiten mit Messaging-Erweiterungen, Aktions- und Suchbefehle sowie die Verbreitung von Links.

In der folgenden Abbildung werden die Speicherorte angezeigt, von denen Messaging-Erweiterungen aufgerufen werden:

![Aufrufen von Speicherorten für Messaging-Erweiterungen](~/assets/images/messaging-extension-invoke-locations.png)

> [!NOTE]
> @mentioning Nachrichtenerweiterungen werden im Feld zum Verfassen nicht mehr unterstützt.

## <a name="scenarios-where-messaging-extensions-are-used"></a>Szenarien, in denen Messaging-Erweiterungen verwendet werden

| Szenario | Beispiel |
|:-----------------|:-----------------|
|Sie möchten, dass ein externes System eine Aktion ausführt und das Ergebnis der Aktion zurück an Ihre Unterhaltung gesendet wird.|Reservieren Sie eine Ressource und lassen Sie den Kanal das reservierte Zeitfenster kennen.|
|Sie möchten etwas in einem externen System finden und die Ergebnisse für die Unterhaltung freigeben.|Suchen Sie in Azure DevOps nach einer Arbeitsaufgabe, und geben Sie sie für die Gruppe als adaptive Karte frei.|
|Sie möchten eine komplexe Aufgabe mit mehreren Schritten oder vielen Informationen in einem externen System abschließen und die Ergebnisse mit einer Unterhaltung teilen.|Erstellen Sie einen Fehler in Ihrem Tracking-System basierend auf einer Teams Nachricht, weisen Sie bob diesen Fehler zu, und senden Sie eine Karte mit den Details des Fehlers an den Unterhaltungsthread.|

## <a name="understand-how-messaging-extensions-work"></a>Grundlegendes zur Funktionsweise von Messaging-Erweiterungen

Eine Messaging-Erweiterung besteht aus einem Webdienst, den Sie hosten, und einem App-Manifest, das definiert, wo Ihr Webdienst im Microsoft Teams-Client aufgerufen wird. Der Webdienst nutzt das Messaging-Schema und das sichere Kommunikationsprotokoll des Bot-Frameworks, daher müssen Sie Ihren Webdienst als Bot im Bot Framework registrieren.

> [!NOTE]
> Obwohl Sie den Webdienst manuell erstellen können, verwenden Sie [das Bot Framework SDK](https://github.com/microsoft/botframework-sdk) , um mit dem Protokoll zu arbeiten.

Im App-Manifest für Microsoft Teams App wird eine einzelne Messaging-Erweiterung mit bis zu zehn verschiedenen Befehlen definiert. Jeder Befehl definiert einen Typ, z. B. Aktion oder Suche und die Speicherorte im Client, von wo aus er aufgerufen wird. Die Aufrufspeicherorte sind Verfassen-Nachrichtenbereich, Befehlsleiste und Nachricht. Beim Aufrufen empfängt der Webdienst eine HTTPS-Nachricht mit einer JSON-Nutzlast, die alle relevanten Informationen enthält. Antworten Sie mit einer JSON-Nutzlast, sodass der Teams-Client die nächste zu aktivierende Interaktion kennen kann.

## <a name="types-of-messaging-extension-commands"></a>Typen von Messaging-Erweiterungsbefehlen

Es gibt zwei Arten von Messaging-Erweiterungsbefehlen: Aktionsbefehl und Suchbefehl. Der Befehlstyp der Messaging-Erweiterung definiert die Ui-Elemente und Interaktionsflüsse, die für Ihren Webdienst verfügbar sind. Einige Interaktionen, z. B. Authentifizierung und Konfiguration, sind für beide Befehlstypen verfügbar.

### <a name="action-commands"></a>Aktionsbefehle

Aktionsbefehle werden verwendet, um benutzern ein modales Popup anzuzeigen, um Informationen zu sammeln oder anzuzeigen. Wenn der Benutzer das Formular sendet, antwortet Ihr Webdienst, indem er eine Nachricht direkt in die Unterhaltung einfügt oder eine Nachricht in den Bereich zum Verfassen von Nachrichten einfügt. Danach kann der Benutzer die Nachricht übermitteln. Sie können mehrere Formulare für komplexere Workflows miteinander verketten.

Die Aktionsbefehle werden aus dem Bereich zum Verfassen von Nachrichten, aus dem Befehlsfeld oder aus einer Nachricht ausgelöst. Wenn der Befehl aus einer Nachricht aufgerufen wird, enthält die ursprüngliche JSON-Nutzlast, die an Ihren Bot gesendet wird, die gesamte Nachricht, von der aus er aufgerufen wurde. Die folgende Abbildung zeigt das Aktionsbefehls-Aufgabenmodul der Messaging-Erweiterung: ![Aktionsbefehls-Aufgabenmodul der Messaging-Erweiterung](~/assets/images/task-module.png)

### <a name="search-commands"></a>Suchbefehle

MitHilfe von Suchbefehlen können Benutzer ein externes System entweder manuell über ein Suchfeld oder durch Einfügen eines Links zu einer überwachten Domäne in den Bereich zum Verfassen von Nachrichten durchsuchen und die Ergebnisse der Suche in eine Nachricht einfügen. Im grundlegendsten Suchbefehlsfluss enthält die anfängliche Aufrufnachricht die Suchzeichenfolge, die der Benutzer übermittelt hat. Sie antworten mit einer Liste von Karten und Kartenvorschau. Der Teams-Client rendert eine Liste der Kartenvorschau für den Benutzer. Wenn der Benutzer eine Karte aus der Liste auswählt, wird die Karte in voller Größe in den Bereich zum Verfassen von Nachrichten eingefügt.

Die Karten werden aus dem Bereich zum Verfassen von Nachrichten oder dem Befehlsfeld ausgelöst und nicht von einer Nachricht ausgelöst. Sie können nicht von einer Nachricht ausgelöst werden.
In der folgenden Abbildung wird das Befehlsaufgabenmodul für die Messaging-Erweiterungssuche angezeigt:

![Suchbefehl für Messaging-Erweiterungen](~/assets/images/search-extension.png)

> [!NOTE]
> Weitere Informationen zu Karten finden Sie unter ["Karten"](../task-modules-and-cards/what-are-cards.md).

## <a name="link-unfurling"></a>Verbreiten von Links

Ein Webdienst wird aufgerufen, wenn eine URL in den Bereich zum Verfassen von Nachrichten eingefügt wird. Diese Funktion wird als Verbreitung von Verknüpfungen bezeichnet. Sie können den Empfang eines Aufrufs abonnieren, wenn URLs, die eine bestimmte Domäne enthalten, in den Bereich zum Verfassen von Nachrichten eingefügt werden. Ihr Webdienst kann die URL in eine detaillierte Karte "entrollen", um mehr Informationen als die standardmäßige Websitevorschaukarte bereitzustellen. Sie können Schaltflächen hinzufügen, damit die Benutzer sofort Maßnahmen ergreifen können, ohne den Microsoft Teams Client verlassen zu müssen.
Die folgenden Bilder zeigen das Feature zum Aufheben von Links, wenn ein Link in die Messaging-Erweiterung eingefügt wird:

![Unfurl-Link](../assets/images/messaging-extension/unfurl-link.png)

![Verbreitung von Links](../assets/images/messaging-extension/link-unfurl.gif)

## <a name="code-snippets"></a>Codeausschnitte

Der folgende Code enthält ein Beispiel für eine Aktion, die auf Messaging-Erweiterungen basiert:

# <a name="c"></a>[C#](#tab/dotnet)

```csharp

 protected override Task<MessagingExtensionActionResponse> OnTeamsMessagingExtensionFetchTaskAsync(ITurnContext<IInvokeActivity> turnContext, MessagingExtensionAction action, CancellationToken cancellationToken)
        {
            // Handle different actions using switch
            switch (action.CommandId)
            {
                case "HTML":
                    return new MessagingExtensionActionResponse
                    {
                        Task = new TaskModuleContinueResponse
                        {
                            Value = new TaskModuleTaskInfo
                            {
                                Height = 200,
                                Width = 400,
                                Title = "Task Module HTML Page",
                                Url = baseUrl + "/htmlpage.html",
                            },
                        },
                    };
                // return TaskModuleHTMLPage(turnContext, action);
                default:
                    string memberName = "";
                    var member = await TeamsInfo.GetMemberAsync(turnContext, turnContext.Activity.From.Id, cancellationToken);
                    memberName = member.Name;
                    return new MessagingExtensionActionResponse
                    {
                        Task = new TaskModuleContinueResponse
                        {
                            Value = new TaskModuleTaskInfo
                            {
                                Card = <<AdaptiveAction card json>>,
                                Height = 200,
                                Width = 400,
                                Title = $"Welcome {memberName}",
                            },
                        },
                    };
            }
```

# <a name="nodejs"></a>[Node.js](#tab/nodejs)

```javascript

    async handleTeamsMessagingExtensionFetchTask(context, action) {
        switch (action.commandId) {
            case 'Static HTML':
                return staticHtmlPage();
        }
    }

    staticHtmlPage(){
        return {
            task: {
                type: 'continue',
                value: {
                    width: 450,
                    height: 125,
                    title: 'Task module Static HTML',
                    url: `${baseurl}/StaticPage.html`
                }
            }
        };
    }

```

---

Der folgende Code enthält ein Beispiel für die Suche basierend auf Messaging-Erweiterungen:

# <a name="c"></a>[C#](#tab/dotnet)

```csharp

protected override async Task<MessagingExtensionResponse> OnTeamsMessagingExtensionQueryAsync(ITurnContext<IInvokeActivity> turnContext, MessagingExtensionQuery query, CancellationToken cancellationToken)
        {
            var text = query?.Parameters?[0]?.Value as string ?? string.Empty;

            var packages = new[] {
            new { title = "A very extensive set of extension methods", value = "FluentAssertions" },
            new { title = "Fluent UI Library", value = "FluentUI" }};

            // We take every row of the results and wrap them in cards wrapped in MessagingExtensionAttachment objects.
            // The Preview is optional, if it includes a Tap, that will trigger the OnTeamsMessagingExtensionSelectItemAsync event back on this bot.
            var attachments = packages.Select(package =>
            {
                var previewCard = new ThumbnailCard { Title = package.title, Tap = new CardAction { Type = "invoke", Value = package } };
                if (!string.IsNullOrEmpty(package.title))
                {
                    previewCard.Images = new List<CardImage>() { new CardImage(package.title, "Icon") };
                }

                var attachment = new MessagingExtensionAttachment
                {
                    ContentType = HeroCard.ContentType,
                    Content = new HeroCard { Title = package.title },
                    Preview = previewCard.ToAttachment()
                };

                return attachment;
            }).ToList();

            // The list of MessagingExtensionAttachments must we wrapped in a MessagingExtensionResult wrapped in a MessagingExtensionResponse.
            return new MessagingExtensionResponse
            {
                ComposeExtension = new MessagingExtensionResult
                {
                    Type = "result",
                    AttachmentLayout = "list",
                    Attachments = attachments
                }
            };
        }
```

# <a name="nodejs"></a>[Node.js](#tab/nodejs)

```javascript

async handleTeamsMessagingExtensionQuery(context, query) {
        const searchQuery = query.parameters[0].value;     
        const attachments = [];
                const response = await axios.get(`http://registry.npmjs.com/-/v1/search?${ querystring.stringify({ text: searchQuery, size: 8 }) }`);
                
                response.data.objects.forEach(obj => {
                        const heroCard = CardFactory.heroCard(obj.package.name);
                        const preview = CardFactory.heroCard(obj.package.name);
                        preview.content.tap = { type: 'invoke', value: { description: obj.package.description } };
                        const attachment = { ...heroCard, preview };
                        attachments.push(attachment);
                });
    
                return {
                    composeExtension:  {
                           type: 'result',
                           attachmentLayout: 'list',
                           attachments: attachments
                    }
                };
            }       
        }
```

---

## <a name="code-sample"></a>Codebeispiel

| **Beispielname** | **Beschreibung** | **.NET** | **Node.js** | **Python** |
|------------|-------------|----------------|------------|------------|
| Messaging-Erweiterung mit aktionsbasierten Befehlen | In diesem Beispiel wird veranschaulicht, wie Sie eine aktionsbasierte Messaging-Erweiterung erstellen. | [View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/51.teams-messaging-extensions-action) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/51.teams-messaging-extensions-action) | [Anzeigen](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python/51.teams-messaging-extensions-action) |
| Messaging-Erweiterung mit suchbasierten Befehlen | In diesem Beispiel wird veranschaulicht, wie Sie eine suchbasierte Messaging-Erweiterung erstellen. | [View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/50.teams-messaging-extensions-search) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/50.teams-messaging-extensions-search) | [Anzeigen](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python/50.teams-messaging-extension-search) |
|Messaging-Erweiterungsaktion für die Aufgabenplanung|In diesem Beispiel wird veranschaulicht, wie Sie eine Aufgabe über den Aktionsbefehl für die Messaging-Erweiterung planen und eine Erinnerungskarte zu einem geplanten Datum und zu einer geplanten Uhrzeit abrufen.|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/msgext-message-reminder/csharp)|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/msgext-message-reminder/nodejs)|

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Definieren des Befehls für die Messaging-Erweiterung für Aktionen](~/messaging-extensions/how-to/action-commands/define-action-command.md)

## <a name="see-also"></a>Siehe auch

* [Definieren des Befehls für die Messaging-Erweiterung für die Suche](~/messaging-extensions/how-to/search-commands/define-search-command.md)
* [Erstellen einer Messaging-Erweiterung](../build-your-first-app/build-messaging-extension.md)
