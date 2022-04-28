---
title: Nachrichtenerweiterungen
author: surbhigupta
description: Eine Übersicht über Nachrichtenerweiterungen auf der Microsoft Teams-Plattform
ms.localizationpriority: medium
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: c81f8ec4b1158275ab796883b268d2c7fa6ecfe8
ms.sourcegitcommit: 0117c4e750a388a37cc189bba8fc0deafc3fd230
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2022
ms.locfileid: "65104112"
---
# <a name="message-extensions"></a>Nachrichtenerweiterungen

Nachrichtenerweiterungen ermöglichen es den Benutzern, mit Ihrem Webdienst über Schaltflächen und Formulare im Microsoft Teams-Client zu interagieren. Sie können Aktionen in einem externen System über den Nachrichtenbereich zum Verfassen, das Befehlsfeld oder direkt aus einer Nachricht durchsuchen oder initiieren. Sie können die Ergebnisse dieser Interaktion in Form einer reich formatierten Karte an den Microsoft Teams Client zurücksenden. Dieses Dokument bietet einen Überblick über die Nachrichtenerweiterung, Aufgaben, die in verschiedenen Szenarien ausgeführt werden, das Arbeiten mit Nachrichtenerweiterungen, Aktions- und Suchbefehle sowie die Verbreitung von Links.

In der folgenden Abbildung werden die Speicherorte angezeigt, an denen Nachrichtenerweiterungen aufgerufen werden:

![Nachrichtenerweiterung ruft Speicherorte auf](~/assets/images/messaging-extension-invoke-locations.png)

> [!NOTE]
> @mentioning Nachrichtenerweiterungen werden im Feld zum Verfassen nicht mehr unterstützt.

## <a name="scenarios-where-message-extensions-are-used"></a>Szenarien, in denen Nachrichtenerweiterungen verwendet werden

| Szenario | Beispiel |
|:-----------------|:-----------------|
|Sie möchten, dass ein externes System eine Aktion und das Ergebnis der Aktion an Ihre Unterhaltung zurücksendet.|Reservieren Sie eine Ressource und lassen Sie den Kanal das reservierte Zeitfenster kennen.|
|Sie möchten etwas in einem externen System finden und die Ergebnisse mit der Unterhaltung teilen.|Suchen Sie in Azure DevOps nach einem Arbeitselement, und geben Sie es als adaptive Karte für die Gruppe frei.|
|Sie möchten eine komplexe Aufgabe ausführen, die mehrere Schritte oder viele Informationen in einem externen System umfasst, und die Ergebnisse mit einer Unterhaltung teilen.|Erstellen Sie einen Fehler in Ihrem Nachverfolgungssystem basierend auf einer Teams Nachricht, weisen Sie diesen Fehler Bob zu, und senden Sie eine Karte mit den Details des Fehlers an den Unterhaltungsthread.|

## <a name="understand-how-message-extensions-work"></a>Verstehen, wie Nachrichtenerweiterungen funktionieren

Eine Nachrichtenerweiterung besteht aus einem Webdienst, den Sie hosten, und einem App-Manifest, das definiert, von wo aus Ihr Webdienst im Microsoft Teams-Client aufgerufen wird. Der Webdienst nutzt das Messagingschema und das Sichere Kommunikationsprotokoll des Bot-Frameworks, sodass Sie Ihren Webdienst als Bot im Bot Framework registrieren müssen.

> [!NOTE]
> Obwohl Sie den Webdienst manuell erstellen können, verwenden Sie [das Bot Framework SDK](https://github.com/microsoft/botframework-sdk) , um mit dem Protokoll zu arbeiten.

Im App-Manifest für Microsoft Teams App wird eine einzelne Nachrichtenerweiterung mit bis zu zehn verschiedenen Befehlen definiert. Jeder Befehl definiert einen Typ, z. B. Aktion oder Suche, und die Speicherorte im Client, von wo aus er aufgerufen wird. Die Aufrufspeicherorte sind Nachrichtenbereich, Befehlsleiste und Nachricht verfassen. Beim Aufruf empfängt der Webdienst eine HTTPS-Nachricht mit einer JSON-Nutzlast einschließlich aller relevanten Informationen. Antworten Sie mit einer JSON-Nutzlast, sodass der Teams Client die nächste zu aktivierenden Interaktion kennen kann.

## <a name="types-of-message-extension-commands"></a>Typen von Nachrichtenerweiterungsbefehlen

Es gibt zwei Arten von Nachrichtenerweiterungsbefehlen: Aktionsbefehl und Suchbefehl. Der Befehlstyp "Nachrichtenerweiterung" definiert die UI-Elemente und Interaktionsflüsse, die für Ihren Webdienst verfügbar sind. Einige Interaktionen, z. B. Authentifizierung und Konfiguration, sind für beide Arten von Befehlen verfügbar.

### <a name="action-commands"></a>Aktionsbefehle

Aktionsbefehle werden verwendet, um den Benutzern ein modales Popup zum Sammeln oder Anzeigen von Informationen zu präsentieren. Wenn der Benutzer das Formular sendet, antwortet Ihr Webdienst, indem er eine Nachricht direkt in die Unterhaltung einfügt oder eine Nachricht in den Nachrichtenbereich zum Verfassen einfügt. Danach kann der Benutzer die Nachricht übermitteln. Sie können mehrere Formulare für komplexere Workflows miteinander verketten.

Die Aktionsbefehle werden aus dem Nachrichtenbereich zum Verfassen, dem Befehlsfeld oder einer Nachricht ausgelöst. Wenn der Befehl aus einer Nachricht aufgerufen wird, enthält die ursprüngliche JSON-Nutzlast, die an Ihren Bot gesendet wird, die gesamte Nachricht, aus der er aufgerufen wurde. In der folgenden Abbildung wird das Aufgabenmodul für die Nachrichtenerweiterungsaktion angezeigt: ![Aufgabenmodul für Die Nachrichtenerweiterungsaktion](~/assets/images/task-module.png)

### <a name="search-commands"></a>Suchbefehle

Suchbefehle ermöglichen es benutzern, ein externes System entweder manuell über ein Suchfeld oder durch Einfügen eines Links zu einer überwachten Domäne in den Nachrichtenbereich zum Verfassen von Informationen zu durchsuchen und die Ergebnisse der Suche in eine Nachricht einzufügen. Im grundlegendsten Suchbefehlsfluss enthält die ursprüngliche Aufrufnachricht die Suchzeichenfolge, die der Benutzer übermittelt hat. Sie antworten mit einer Liste von Karten und Kartenvorschauen. Der Teams-Client rendert eine Liste der Kartenvorschauen für den Benutzer. Wenn der Benutzer eine Karte aus der Liste auswählt, wird die Karte in voller Größe in den Nachrichtenbereich zum Verfassen eingefügt.

Die Karten werden aus dem Nachrichtenbereich zum Verfassen oder dem Befehlsfeld ausgelöst und nicht von einer Nachricht ausgelöst. Sie können nicht durch eine Nachricht ausgelöst werden.
Die folgende Abbildung zeigt das Aufgabenmodul für die Nachrichtenerweiterungssuche:

![Nachrichtenerweiterungssuchbefehl](~/assets/images/search-extension.png)

> [!NOTE]
> Weitere Informationen zu Karten finden Sie unter ["Karten"](../task-modules-and-cards/what-are-cards.md).

## <a name="link-unfurling"></a>Verbreiten von Links

Ein Webdienst wird aufgerufen, wenn eine URL in den Bereich zum Verfassen von Nachrichten eingefügt wird. Diese Funktionalität wird als Link-Entknüpfung bezeichnet. Sie können einen Aufruf abonnieren, wenn URLs, die eine bestimmte Domäne enthalten, in den Nachrichtenbereich zum Verfassen eingefügt werden. Ihr Webdienst kann die URL in einer detaillierten Karte "entpacken", wodurch mehr Informationen als die standardmäßige Websitevorschaukarte bereitgestellt werden. Sie können Schaltflächen hinzufügen, damit die Benutzer sofort Maßnahmen ergreifen können, ohne den Microsoft Teams Client verlassen zu müssen.
In den folgenden Bildern wird das Feature zum Erweitern von Links angezeigt, wenn ein Link in die Nachrichtenerweiterung eingefügt wird:

![Unfurl-Link](../assets/images/messaging-extension/unfurl-link.png)

![Link-Entknüpfung](../assets/images/messaging-extension/link-unfurl.gif)

## <a name="code-snippets"></a>Codeausschnitte

Der folgende Code enthält ein Beispiel für eine Aktion, die auf Nachrichtenerweiterungen basiert:

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

Der folgende Code enthält ein Beispiel für die Suche basierend auf Nachrichtenerweiterungen:

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
| Nachrichtenerweiterung mit aktionsbasierten Befehlen | In diesem Beispiel wird veranschaulicht, wie Sie eine aktionsbasierte Nachrichtenerweiterung erstellen. | [View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/51.teams-messaging-extensions-action) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/51.teams-messaging-extensions-action) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python/51.teams-messaging-extensions-action) |
| Nachrichtenerweiterung mit suchbasierten Befehlen | In diesem Beispiel wird das Erstellen einer suchbasierten Nachrichtenerweiterung veranschaulicht. | [View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/50.teams-messaging-extensions-search) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/50.teams-messaging-extensions-search) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python/50.teams-messaging-extension-search) |
|Nachrichtenerweiterungsaktion für die Aufgabenplanung|In diesem Beispiel wird veranschaulicht, wie Sie eine Aufgabe über den Aktionsbefehl "Nachrichtenerweiterung" planen und eine Erinnerungskarte zu einem geplanten Datum und einer geplanten Uhrzeit abrufen.|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/msgext-message-reminder/csharp)|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/msgext-message-reminder/nodejs)|

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Befehl "Aktionsnachrichtenerweiterung definieren"](~/messaging-extensions/how-to/action-commands/define-action-command.md)

## <a name="see-also"></a>Siehe auch

* [Definieren des Suchnachrichtenerweiterungsbefehls](~/messaging-extensions/how-to/search-commands/define-search-command.md)
* [Erstellen einer Nachrichtenerweiterung](../build-your-first-app/build-messaging-extension.md)
