---
title: Nachrichtenerweiterungen
author: surbhigupta
description: Erfahren Sie, wie Nachrichtenerweiterungen verwendet werden, welche Typen und Szenarien auf der Microsoft Teams-Plattform verwendet werden. Beispiele für Aktion und durchsuchte basierte Nachrichtenerweiterung.
ms.localizationpriority: medium
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: 766a135a55b3894c985a0701bb883d45519b496b
ms.sourcegitcommit: 75d0072c021609af33ce584d671f610d78b3aaef
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/28/2022
ms.locfileid: "68100273"
---
# <a name="message-extensions"></a>Nachrichtenerweiterungen

Nachrichtenerweiterungen ermöglichen den Benutzern die Interaktion mit Ihrem Webdienst über Schaltflächen und Formulare im Microsoft Teams-Client. Sie können in einem externen System über den Nachrichtenbereich „Verfassen“, das Befehlsfeld oder direkt aus einer Nachricht heraus suchen oder Aktionen starten. Sie können die Ergebnisse dieser Interaktion in Form einer reich formatierten Karte an den Teams-Client zurücksenden.

> [!IMPORTANT]
> Nachrichtenerweiterungen sind in Government Community Cloud (GCC) und GCC-High Umgebungen verfügbar, jedoch nicht in der DoD-Umgebung (Department of Defense).

Dieses Dokument bietet einen Überblick über die Nachrichtenerweiterung, Aufgaben, die in verschiedenen Szenarien ausgeführt werden, das Arbeiten mit Nachrichtenerweiterungen, Aktions- und Suchbefehle sowie die Verbreitung von Links.

In der folgenden Abbildung werden die Speicherorte angezeigt, von denen Nachrichtenerweiterungen aufgerufen werden:

:::image type="content" source="~/assets/images/messaging-extension-invoke-locations.png" alt-text="Aufruforte für Nachrichtenerweiterungen":::

> [!NOTE]
> @mentioning Nachrichtenerweiterungen werden im Feld „Verfassen“ nicht mehr unterstützt.

## <a name="scenarios-where-message-extensions-are-used"></a>Szenarien, in denen Nachrichtenerweiterungen verwendet werden

| Szenario | Beispiel |
|:-----------------|:-----------------|
|Sie möchten, dass ein externes System eine Aktion ausführt und das Ergebnis der Aktion an Ihre Unterhaltung zurückgesendet wird.|Reservieren Sie eine Ressource und lassen Sie den Kanal das reservierte Zeitfenster kennen.|
|Sie möchten etwas in einem externen System finden und die Ergebnisse für die Konversation freigeben.|Suchen Sie in Azure DevOps nach einem Arbeitselement, und geben Sie es als adaptive Karte für die Gruppe frei.|
|Sie möchten eine komplexe Aufgabe ausführen, die mehrere Schritte oder viele Informationen in einem externen System umfasst, und die Ergebnisse für eine Unterhaltung freigeben.|Erstellen Sie auf der Grundlage einer Teams-Nachricht einen Bug in Ihrem Tracking-System, weisen Sie diesen Bug Bob zu, und senden Sie eine Karte mit den Details des Bugs an den Unterhaltungsthread.|

## <a name="understand-how-message-extensions-work"></a>Grundlegendes zur Funktionsweise von Nachrichtenerweiterungen

Eine Nachrichtenerweiterung besteht aus einem Webdienst, den Sie hosten, und einem App-Manifest, das definiert, von wo aus Ihr Webdienst im Teams-Client aufgerufen wird. Der Webdienst nutzt das Messaging-Schema und das sichere Kommunikationsprotokoll des Bot-Frameworks, sodass Sie Ihren Webdienst auch als Bot im Bot-Framework registrieren müssen.

> [!NOTE]
> Obwohl Sie den Webdienst manuell erstellen können, verwenden Sie das[Bot Framework SDK](https://github.com/microsoft/botframework-sdk), um mit dem Protokoll zu arbeiten.

Im App-Manifest für Die Teams-App wird eine einzelne Nachrichtenerweiterung mit bis zu 10 verschiedenen Befehlen definiert. Jeder Befehl definiert einen Typ, z. B. Aktion oder Suche, und die Speicherorte im Client, von denen aus er aufgerufen wird. Die Aufruforte sind der Nachrichtenbereich „Verfassen“, die Befehlsleiste und die Nachricht. Beim Aufruf empfängt der Webdienst eine HTTPS-Nachricht mit einer JSON-Nutzlast einschließlich aller relevanten Informationen. Antworten Sie mit einer JSON-Nutzlast, sodass der Teams-Client die nächste zu aktivierende Interaktion kennen kann.

## <a name="types-of-message-extension-commands"></a>Typen von Befehlen für Nachrichtenerweiterungen

Es gibt zwei Typen von Befehlen für Nachrichtenerweiterungen: Aktionsbefehl und Suchbefehl. Der Befehlstyp „Nachrichtenerweiterung“ definiert die Benutzeroberflächenelemente und Interaktionsflüsse, die für Ihren Webdienst verfügbar sind. Einige Interaktionen, z. B. Authentifizierung und Konfiguration, sind für beide Befehlstypen verfügbar.

### <a name="action-commands"></a>Aktionsbefehle

Aktionsbefehle werden verwendet, um benutzern ein modales Popup zum Sammeln oder Anzeigen von Informationen zu präsentieren. Wenn der Benutzer das Formular übermittelt, antwortet Ihr Webdienst, indem er eine Nachricht direkt in die Unterhaltung einfügt oder eine Nachricht in den Nachrichtenbereich „Verfassen“ einfügt. Danach kann der Benutzer die Nachricht übermitteln. Sie können mehrere Formulare für komplexere Workflows miteinander verketten.

Die Aktionsbefehle werden aus dem Nachrichtenbereich „Verfassen“, aus dem Befehlsfeld oder aus einer Nachricht heraus ausgelöst. Wenn der Befehl von einer Nachricht aus aufgerufen wird, enthält die ursprüngliche JSON-Nutzlast, die an Ihren Bot gesendet wird, die gesamte Nachricht, von der aus sie aufgerufen wurde. Die folgende Abbildung zeigt das Aufgabenmodul für die Nachrichtenerweiterungsaktion:

:::image type="content" source="~/assets/images/task-module.png" alt-text="Nachrichtenerweiterung Aktion Befehl Aufgabenmodul":::

### <a name="search-commands"></a>Suchbefehle

Mit den Suchbefehlen können die Benutzer ein externes System nach Informationen durchsuchen, entweder manuell über ein Suchfeld oder indem sie einen Link zu einer überwachten Domäne in den Bereich zum Verfassen von Nachrichten einfügen und die Ergebnisse der Suche in eine Nachricht einfügen. Im einfachsten Suchbefehlsfluss enthält die anfängliche Aufrufnachricht die vom Benutzer übermittelte Suchzeichenfolge. Sie antworten mit einer Liste von Karten und Kartenvorschauen. Der Teams-Client rendert eine Liste der Kartenvorschauen für den Benutzer. Wenn der Benutzer eine Karte aus der Liste auswählt, wird sie in voller Größe in den Nachrichtenbereich „Verfassen“ eingefügt.

Die Karten werden aus dem Nachrichtenbereich „Verfassen“ oder dem Befehlsfeld ausgelöst und nicht von einer Nachricht ausgelöst. Sie können nicht von einer Nachricht ausgelöst werden.
Im folgenden Bild wird das Aufgabenmodul für die Nachrichtenerweiterung aus Suchbasis angezeigt:

:::image type="content" source="~/assets/images/search-extension.png" alt-text="Suchbefehl für Nachrichtenerweiterung":::

> [!NOTE]
> Weitere Informationen zu Karten finden Sie unter [Was sind Karten](../task-modules-and-cards/what-are-cards.md).

## <a name="link-unfurling"></a>Verbreiten von Links

Ein Webdienst wird aufgerufen, wenn eine URL in den Nachrichtenbereich „Verfassen“ eingefügt wird. Diese Funktionalität wird als Verbreiten von Links bezeichnet. Sie können abonnieren, um einen Aufruf zu erhalten, wenn URLs, die eine bestimmte Domäne enthalten, in den Nachrichtenbereich „Verfassen“ eingefügt werden. Ihr Webdienst kann die URL in eine detaillierte Karte „verbreiten", wodurch mehr Informationen als die standardmäßige Website-Vorschaukarte bereitgestellt werden. Sie können Schaltflächen hinzufügen, damit die Benutzer sofort Maßnahmen ergreifen können, ohne den Teams-Client verlassen zu müssen.
In den folgenden Bildern wird das Feature zum Verbreiten von Links angezeigt, wenn ein Link in die Nachrichtenerweiterung eingefügt wird:

:::image type="content" source="../assets/images/messaging-extension/unfurl-link.png" alt-text="Link verbreiten":::

![Verbreiten von Links](../assets/images/messaging-extension/link-unfurl.gif)

## <a name="code-snippets"></a>Codeausschnitte

Der folgende Code enthält ein Beispiel für eine Aktion, die Nachrichtenerweiterungen zugrunde liegt:

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

Der folgende Code enthält ein Beispiel für die Suche, die Nachrichtenerweiterungen zugrunde liegt:

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
| Nachrichtenerweiterung mit suchbasierten Befehlen | In diesem Beispiel wird das Erstellen einer suchbasierten Nachrichtenerweiterung veranschaulicht. | [View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/50.teams-messaging-extensions-search) | [View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/50.teams-messaging-extensions-search) | [Anzeigen](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/python/50.teams-messaging-extension-search) |
|Nachrichtenerweiterungsaktion für die Aufgabenplanung|In diesem Beispiel wird veranschaulicht, wie Sie eine Aufgabe über den Aktionsbefehl „Nachrichtenerweiterung“ planen und eine Erinnerungskarte zu einem geplanten Datum und einer geplanten Uhrzeit erhalten.|[View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/msgext-message-reminder/csharp)|[Anzeigen](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/msgext-message-reminder/nodejs)|

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Definieren des Befehls zur Nachrichtenerweiterung auf Aktionsbasis](~/messaging-extensions/how-to/action-commands/define-action-command.md)

## <a name="see-also"></a>Siehe auch

* [Definieren des Befehls zur Nachrichtenerweiterung auf Suchbasis](~/messaging-extensions/how-to/search-commands/define-search-command.md)
* [Erstellen einer Nachrichtenerweiterung](../build-your-first-app/build-messaging-extension.md)
* [Universelle Aktionen für suchbasierte Messaging-Erweiterungen](how-to/search-commands/universal-actions-for-search-based-message-extensions.md)
