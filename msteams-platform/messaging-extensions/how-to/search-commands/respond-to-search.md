---
title: " Reagieren Sie auf den Suchbefehl "
author: surbhigupta
description: Erfahren Sie, wie Sie über eine Nachrichtenerweiterung in einer Microsoft Teams-App auf den Suchbefehl reagieren. Erfahren Sie, wie Sie auf die Benutzeranforderung reagieren.
ms.topic: conceptual
ms.author: anclear
ms.localizationpriority: medium
ms.openlocfilehash: 97fe20097e98a015759ba030004fb8c0b3b5e3f9
ms.sourcegitcommit: 9ea9a70d2591bce6b8c980d22014e160f7b45f91
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/02/2022
ms.locfileid: "68819947"
---
# <a name="respond-to-search-command"></a> Reagieren Sie auf den Suchbefehl 

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

Nachdem der Benutzer den Suchbefehl übermittelt hat, empfängt Ihr Webdienst eine `composeExtension/query` Aufrufnachricht, die ein `value` -Objekt mit den Suchparametern enthält. Dieser Aufruf wird mit den folgenden Bedingungen ausgelöst:

* Wenn Zeichen in das Suchfeld eingegeben werden.
* `initialRun` in Ihrem App-Manifest auf TRUE festgelegt ist, erhalten Sie die Aufrufnachricht, sobald der Suchbefehl aufgerufen wird. Weitere Informationen finden Sie unter [Standardabfrage](#default-query).

In diesem Dokument erfahren Sie, wie Sie auf Benutzeranforderungen in Form von Karten und Vorschauen reagieren und unter welchen Bedingungen Microsoft Teams eine Standardabfrage ausgibt.

Die Anforderungsparameter befinden sich im `value` -Objekt in der Anforderung, das die folgenden Eigenschaften enthält:

| Eigenschaftenname | Zweck |
|---|---|
| `commandId` | Der Name des vom Benutzer aufgerufenen Befehls, der mit einem der im App-Manifest deklarierten Befehle übereinstimmt. |
| `parameters` | Array von Parametern. Jedes Parameterobjekt enthält den Parameternamen zusammen mit dem vom Benutzer bereitgestellten Parameterwert. |
| `queryOptions` | Paginierungsparameter: <br>`skip`: Anzahl für diese Abfrage überspringen <br>`count`: Anzahl der zurückzugebenden Elemente. |

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

```csharp
protected override async Task<MessagingExtensionResponse> OnTeamsMessagingExtensionQueryAsync(ITurnContext<IInvokeActivity> turnContext, MessagingExtensionQuery query, CancellationToken cancellationToken)
{
  //code to handle the query
}
```

# <a name="typescriptnodejs"></a>[TypeScript/Node.js](#tab/typescript)

```typescript
class TeamsMessagingExtensionsSearch extends TeamsActivityHandler {
    async handleTeamsMessagingExtensionQuery(context, query) {
  //code to handle the query
    }
}
```

# <a name="json"></a>[JSON](#tab/json)

Der folgende JSON-Code wird gekürzt, um die relevantesten Abschnitte hervorzuheben.

```json
{
  "type": "invoke",
  "name": "composeExtension/query",
  "value": {
    "commandId": "searchCmd",
    "parameters": [
      {
        "name": "searchKeywords",
        "value": "Toronto"
      }
    ],
    "queryOptions": {
      "skip": 0,
      "count": 25
    }
  },
...
}
```

* * *

## <a name="respond-to-user-requests"></a>Reagieren auf Benutzeranforderungen

Wenn der Benutzer eine Abfrage ausführt, stellt Microsoft Teams eine synchrone HTTP-Anforderung an Ihren Dienst. An diesem Punkt hat `5` Ihr Code Sekunden, um eine HTTP-Antwort auf die Anforderung bereitzustellen. Während dieser Zeit kann Ihr Dienst zusätzliche Suchvorgänge oder eine andere Geschäftslogik durchführen, die für die Anforderung erforderlich ist.

Ihr Dienst muss mit den Ergebnissen antworten, die der Benutzerabfrage entsprechen. Die Antwort muss einen HTTP-Statuscode von `200 OK` und eine gültige Anwendung oder ein JSON-Objekt mit den folgenden Eigenschaften angeben:

|Eigenschaftenname|Zweck|
|---|---|
|`composeExtension`|Antwortumschlag der obersten Ebene.|
|`composeExtension.type`|Typ der Antwort. Die folgenden Typen werden unterstützt: <br>`result`: Zeigt eine Liste der Suchergebnisse an. <br>`auth`: Fordert den Benutzer zur Authentifizierung auf. <br>`config`: Fordert den Benutzer auf, die Nachrichtenerweiterung einzurichten. <br>`message`: Zeigt eine Nur-Text-Nachricht an |
|`composeExtension.attachmentLayout`|Gibt das Layout der Anlagen an. Wird für Antworten vom Typ `result`verwendet. <br>Derzeit werden die folgenden Typen unterstützt: <br>`list`: Eine Liste von Kartenobjekten, die Miniaturansichten, Titel und Textfelder enthalten <br>`grid`: Ein Raster mit Miniaturansichten |
|`composeExtension.attachments`|Array gültiger Anlagenobjekte. Wird für Antworten vom Typ `result`verwendet. <br>Derzeit werden die folgenden Typen unterstützt: <br>`application/vnd.microsoft.card.thumbnail` <br>`application/vnd.microsoft.card.hero` <br>`application/vnd.microsoft.teams.card.o365connector` <br>`application/vnd.microsoft.card.adaptive`|
|`composeExtension.suggestedActions`|Vorgeschlagene Aktionen. Wird für Antworten vom Typ `auth` oder `config`verwendet. |
|`composeExtension.text`|Anzuzeigende Meldung. Wird für Antworten vom Typ `message`verwendet. |

### <a name="response-card-types-and-previews"></a>Antwortkartentypen und Vorschauen

Teams unterstützt die folgenden Kartentypen:

* [Miniaturbildkarte](~/task-modules-and-cards/cards/cards-reference.md#thumbnail-card)
* [Hero-Karte](~/task-modules-and-cards/cards/cards-reference.md#hero-card)
* [Office 365-Connectorkarte](~/task-modules-and-cards/cards/cards-reference.md#office-365-connector-card)
* [Adaptive Karte](~/task-modules-and-cards/cards/cards-reference.md#adaptive-card)

Um ein besseres Verständnis und einen besseren Überblick über Karten zu erhalten, sehen Sie [, was Karten sind](~/task-modules-and-cards/what-are-cards.md).

Informationen zum Verwenden der Miniaturansichten- und Herokartentypen finden [Sie unter Hinzufügen von Karten und Kartenaktionen](~/task-modules-and-cards/cards/cards-actions.md).

Weitere Informationen zur Office 365 Connector-Karte finden [Sie unter Verwenden von Office 365 Connectorkarten](~/task-modules-and-cards/cards/cards-reference.md#office-365-connector-card).

Die Ergebnisliste wird auf der Microsoft Teams-Benutzeroberfläche mit einer Vorschau der einzelnen Elemente angezeigt. Die Vorschau wird auf eine der beiden Arten generiert:

* Verwenden der `preview` -Eigenschaft im `attachment` -Objekt. Die `preview` Anlage kann nur eine Hero- oder Miniaturansichtskarte sein.
* Extrahieren aus den grundlegenden `title`Eigenschaften , `text`und `image` des `attachment` -Objekts. Die grundlegenden Eigenschaften werden nur verwendet, wenn die `preview` Eigenschaft nicht angegeben ist.

Für die Hero- oder Miniaturansichtskarte werden mit Ausnahme der Aufrufaktion andere Aktionen wie Schaltflächen und Tippen in der Vorschaukarte nicht unterstützt.

Um eine adaptive Karte oder eine Office 365 Connector-Karte zu senden, müssen Sie eine Vorschau einschließen. Die `preview` Eigenschaft muss eine Hero- oder Miniaturansichtskarte sein. Wenn Sie die Vorschaueigenschaft im `attachment` -Objekt nicht angeben, wird keine Vorschau generiert.

Für Hero- und Miniaturansichtskarten müssen Sie keine Vorschaueigenschaft angeben, es wird standardmäßig eine Vorschau generiert.

### <a name="response-example"></a>Anforderungsbeispiel

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

```csharp
protected override async Task<MessagingExtensionResponse> OnTeamsMessagingExtensionQueryAsync(ITurnContext<IInvokeActivity> turnContext, MessagingExtensionQuery query, CancellationToken cancellationToken) 
{
  var text = query?.Parameters?[0]?.Value as string ?? string.Empty;

  //searches NuGet for a package
  var obj = JObject.Parse(await (new HttpClient()).GetStringAsync($"https://azuresearch-usnc.nuget.org/query?q=id:{text}&prerelease=true"));
  var packages = obj["data"].Select(item => (item["id"].ToString(), item["version"].ToString(), item["description"].ToString()));

  // We take every row of the results and wrap them in cards wrapped in in MessagingExtensionAttachment objects.
  // The Preview is optional, if it includes a Tap, that will trigger the OnTeamsMessagingExtensionSelectItemAsync event back on this bot.
  var attachments = packages.Select(package => new MessagingExtensionAttachment
      {
          ContentType = HeroCard.ContentType,
          Content = new HeroCard { Title = package.Item1 },
          Preview = new HeroCard { Title = package.Item1, Tap = new CardAction { Type = "invoke", Value = package } }.ToAttachment()
      })
      .ToList();

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

# <a name="typescriptnodejs"></a>[TypeScript/Node.js](#tab/typescript)

```typescript
class TeamsMessagingExtensionsSearchBot extends TeamsActivityHandler {
    async handleTeamsMessagingExtensionQuery(context, query) {
        const searchQuery = query.parameters[0].value;
        const response = await axios.get(`http://registry.npmjs.com/-/v1/search?${ querystring.stringify({ text: searchQuery, size: 8 }) }`);

        const attachments = [];
        response.data.objects.forEach(obj => {
            const heroCard = CardFactory.heroCard(obj.package.name);
            const preview = CardFactory.heroCard(obj.package.name);
            const attachment = { ...heroCard, preview };
            attachments.push(attachment);
        });

        return {
            composeExtension: {
                type: 'result',
                attachmentLayout: 'list',
                attachments: attachments
            }
        };
    }
}
```

# <a name="json"></a>[JSON](#tab/json)

```json
{
  "composeExtension": {
    "type": "result",
    "attachmentLayout": "list",
    "attachments": [
      {
        "contentType": "application/vnd.microsoft.teams.card.o365connector",
        "content": {
          "sections": [
            {
              "activityTitle": "[85069]: Create a cool app",
              "activityImage&quot;: &quot;https://placekitten.com/200/200"
            },
            {
              "title": "Details",
              "facts": [
                {
                  "name": "Assigned to:",
                  "value&quot;: &quot;[Larry Brown](mailto:larryb@example.com)"
                },
                {
                  "name": "State:",
                  "value": "Active"
                }
              ]
            }
          ]
        },
        "preview": {
          "contentType": "application/vnd.microsoft.card.thumbnail",
          "content": {
            "title": "85069: Create a cool app",
            "images": [
              {
                "url": "https://placekitten.com/200/200"
              }
            ]
          }
        }
      },
      {
        "contentType": "application/vnd.microsoft.card.adaptive",
        "content": {
          "type": "AdaptiveCard",
          "body": [
            {
              "type": "Container",
              "items": [
                {
                  "type": "TextBlock",
                  "text": "Microsoft Corp (NASDAQ: MSFT)",
                  "size": "medium",
                  "isSubtle": true
                },
                {
                  "type": "TextBlock",
                  "text": "September 19, 4:00 PM EST",
                  "isSubtle": true
                }
              ]
            },
            {
              "type": "Container",
              "spacing": "none",
              "items": [
                {
                  "type": "ColumnSet",
                  "columns": [
                    {
                      "type": "Column",
                      "width": "stretch",
                      "items": [
                        {
                          "type": "TextBlock",
                          "text": "75.30",
                          "size": "extraLarge"
                        },
                        {
                          "type": "TextBlock",
                          "text": "▼ 0.20 (0.32%)",
                          "size": "small",
                          "color": "attention",
                          "spacing": "none"
                        }
                      ]
                    },
                    {
                      "type": "Column",
                      "width": "auto",
                      "items": [
                        {
                          "type": "FactSet",
                          "facts": [
                            {
                              "title": "Open",
                              "value": "62.24"
                            },
                            {
                              "title": "High",
                              "value": "62.98"
                            },
                            {
                              "title": "Low",
                              "value": "62.20"
                            }
                          ]
                        }
                      ]
                    }
                  ]
                }
              ]
            }
          ],
          "version": "1.0"
        },
        "preview": {
          "contentType": "application/vnd.microsoft.card.thumbnail",
          "content": {
            "title": "Microsoft Corp (NASDAQ: MSFT)",
            "text": "75.30 ▼ 0.20 (0.32%)"
          }
        }
      }
    ]
  }
}
```

* * *

### <a name="enable-and-handle-tap-actions"></a>Aktivieren und Behandeln von Tippaktionen

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

```csharp
protected override Task<MessagingExtensionResponse> OnTeamsMessagingExtensionSelectItemAsync(ITurnContext<IInvokeActivity> turnContext, JObject query, CancellationToken cancellationToken)
{
    // The Preview card's Tap should have a Value property assigned, this will be returned to the bot in this event. 
    var (packageId, version, description, projectUrl, iconUrl) = query.ToObject<(string, string, string, string, string)>();

    var card = new ThumbnailCard
    {
        Title = "Card Select Item",
        Subtitle = description
    };

    var attachment = new MessagingExtensionAttachment
    {
        ContentType = ThumbnailCard.ContentType,
        Content = card,
    };

    return Task.FromResult(new MessagingExtensionResponse
    {
        ComposeExtension = new MessagingExtensionResult
        {
            Type = "result",
            AttachmentLayout = "list",
            Attachments = new List<MessagingExtensionAttachment> { attachment }
        }
    });
}
```

# <a name="typescriptnodejs"></a>[TypeScript/Node.js](#tab/typescript)

```typescript
async handleTeamsMessagingExtensionSelectItem(context, obj) {
        return {
            composeExtension: {
                  type: 'result',
                  attachmentLayout: 'list',
                  attachments: [CardFactory.thumbnailCard(obj.Item3)]
            }
        };
    } 
```

# <a name="json"></a>[JSON](#tab/json)

```json
{
    "name": "composeExtension/selectItem",
    "type": "invoke",
    "value": {
        "Item1": "Package_Name",
        "Item2": "Version",
        "Item3": "Package Description"
    },
    .
    .
    .
}
```

* * *

> [!NOTE]
> `OnTeamsMessagingExtensionSelectItemAsync` wird in der mobilen Teams-Anwendung nicht ausgelöst.

## <a name="default-query"></a>Standardabfrage

Wenn Sie im Manifest auf `true` festlegen`initialRun`, gibt Microsoft Teams eine **Standardabfrage** aus, wenn der Benutzer die Nachrichtenerweiterung zum ersten Mal öffnet. Ihr Dienst kann auf diese Abfrage mit einer Reihe vorab aufgefüllter Ergebnisse antworten. Dies ist nützlich, wenn Ihr Suchbefehl eine Authentifizierung oder Konfiguration erfordert, die zuletzt angezeigten Elemente, Favoriten oder andere Informationen anzeigt, die nicht von der Benutzereingabe abhängig sind.

Die Standardabfrage hat dieselbe Struktur wie jede reguläre Benutzerabfrage, wobei das `name` Feld auf `initialRun` und `value` auf `true` festgelegt ist, wie im folgenden Objekt gezeigt:

```json
{
  "type": "invoke",
  "name": "composeExtension/query",
  "value": {
    "commandId": "searchCmd",
    "parameters": [
      {
        "name": "initialRun",
        "value": "true"
      }
    ],
    "queryOptions": {
      "skip": 0,
      "count": 25
    }
  },
  ⋮
}
```

## <a name="code-sample"></a>Codebeispiel

| Beispielname           | Beschreibung | .NET    | Node.js   |
|:---------------------|:--------------|:---------|:--------|
|Teams-Nachrichtenerweiterungen – Aktion| Beschreibt, wie Aktionsbefehle definiert werden, ein Aufgabenmodul erstellt und auf Aufgabenmodul-Sendeaktionen reagiert wird. |[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/51.teams-messaging-extensions-action)|[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/51.teams-messaging-extensions-action) |
|Teams Nachrichtenerweiterungen – Suche   |  Beschreibt, wie Suchbefehle definiert und auf Suchvorgänge reagiert wird.        |[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/50.teams-messaging-extensions-search)|[Anzeigen](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/50.teams-messaging-extensions-search)|

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Hinzufügen der Authentifizierung zu einer Nachrichtenerweiterung](~/messaging-extensions/how-to/add-authentication.md)

## <a name="see-also"></a>Siehe auch

* [Nachrichtenerweiterungen](../../what-are-messaging-extensions.md)
* [Erstellen Ihrer ersten Registerkarten-App mit JavaScript](../../../sbs-gs-javascript.yml)
* [composeExtensions](../../../resources/schema/manifest-schema.md#composeextensions)
