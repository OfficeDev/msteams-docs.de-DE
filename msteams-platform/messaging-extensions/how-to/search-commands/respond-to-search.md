---
title: Antworten auf Suchbefehl
author: surbhigupta
description: Erfahren Sie, wie Sie mithilfe von Codebeispielen und Beispielen auf den Suchbefehl aus einer Nachrichtenerweiterung in einer Microsoft Teams-App reagieren.
ms.topic: conceptual
ms.author: anclear
ms.localizationpriority: none
ms.openlocfilehash: 4dcf3d5743471daa034d138818cf11a9a516a32e
ms.sourcegitcommit: 0117c4e750a388a37cc189bba8fc0deafc3fd230
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2022
ms.locfileid: "65104504"
---
# <a name="respond-to-search-command"></a>Antworten auf Suchbefehl

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

Nachdem der Benutzer den Suchbefehl übermittelt hat, erhält Ihr Webdienst eine `composeExtension/query` Aufrufmeldung, die ein `value` Objekt mit den Suchparametern enthält. Dieser Aufruf, der mit den folgenden Bedingungen ausgelöst wird:

* Wenn Zeichen in das Suchfeld eingegeben werden.
* `initialRun` in Ihrem App-Manifest auf "true" festgelegt ist, erhalten Sie die Aufrufmeldung, sobald der Suchbefehl aufgerufen wird. Weitere Informationen finden Sie unter [Standardabfrage](#default-query).

In diesem Dokument erfahren Sie, wie Sie auf Benutzeranforderungen in Form von Karten und Vorschauen reagieren und unter welchen Bedingungen Microsoft Teams eine Standardabfrage ausgibt.

Die Anforderungsparameter werden im `value` Objekt in der Anforderung gefunden, das die folgenden Eigenschaften enthält:

| Eigenschaftenname | Zweck |
|---|---|
| `commandId` | Der Name des vom Benutzer aufgerufenen Befehls, der einem der im App-Manifest deklarierten Befehle entspricht. |
| `parameters` | Array von Parametern. Jedes Parameterobjekt enthält den Parameternamen zusammen mit dem vom Benutzer bereitgestellten Parameterwert. |
| `queryOptions` | Paginierungsparameter: <br>`skip`: Überspringen der Anzahl für diese Abfrage <br>`count`: Anzahl der zurückzugebenden Elemente. |

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

Wenn der Benutzer eine Abfrage ausführt, gibt Microsoft Teams eine synchrone HTTP-Anforderung an Ihren Dienst aus. An diesem Punkt hat `5` Der Code Sekunden, um eine HTTP-Antwort auf die Anforderung bereitzustellen. Während dieser Zeit kann Ihr Dienst zusätzliche Nachschlagevorgänge oder eine andere Geschäftslogik ausführen, die zum Bedienen der Anforderung erforderlich ist.

Ihr Dienst muss mit den Ergebnissen antworten, die mit der Benutzerabfrage übereinstimmen. Die Antwort muss einen HTTP-Statuscode und ein gültiges `200 OK` Anwendungs- oder JSON-Objekt mit den folgenden Eigenschaften angeben:

|Eigenschaftenname|Zweck|
|---|---|
|`composeExtension`|Antwortumschlag der obersten Ebene.|
|`composeExtension.type`|Antworttyp. Die folgenden Typen werden unterstützt: <br>`result`: Zeigt eine Liste der Suchergebnisse an. <br>`auth`: Fordert den Benutzer auf, sich zu authentifizieren <br>`config`: Fordert den Benutzer auf, die Nachrichtenerweiterung einzurichten. <br>`message`: Zeigt eine Nur-Text-Nachricht an. |
|`composeExtension.attachmentLayout`|Gibt das Layout der Anlagen an. Wird für Antworten vom Typ `result`verwendet. <br>Derzeit werden die folgenden Typen unterstützt: <br>`list`: Eine Liste der Kartenobjekte, die Miniaturansichten, Titel und Textfelder enthalten <br>`grid`: Ein Raster mit Miniaturansichten |
|`composeExtension.attachments`|Array gültiger Anlagenobjekte. Wird für Antworten vom Typ `result`verwendet. <br>Derzeit werden die folgenden Typen unterstützt: <br>`application/vnd.microsoft.card.thumbnail` <br>`application/vnd.microsoft.card.hero` <br>`application/vnd.microsoft.teams.card.o365connector` <br>`application/vnd.microsoft.card.adaptive`|
|`composeExtension.suggestedActions`|Vorgeschlagene Aktionen. Wird für Antworten vom Typ `auth` oder `config`verwendet. |
|`composeExtension.text`|Anzuzeigende Meldung. Wird für Antworten vom Typ `message`verwendet. |

### <a name="response-card-types-and-previews"></a>Antwortkartentypen und Vorschauen

Teams unterstützt die folgenden Kartentypen:

* [Miniaturbildkarte](~/task-modules-and-cards/cards/cards-reference.md#thumbnail-card)
* [Hero-Karte](~/task-modules-and-cards/cards/cards-reference.md#hero-card)
* [Office 365-Connectorkarte](~/task-modules-and-cards/cards/cards-reference.md#office-365-connector-card)
* [Adaptive Karte](~/task-modules-and-cards/cards/cards-reference.md#adaptive-card)

Um ein besseres Verständnis und einen besseren Überblick über Karten zu erhalten, sehen Sie, [was Karten sind](~/task-modules-and-cards/what-are-cards.md).

Informationen zum Verwenden der Miniaturansichten- und Hero-Kartentypen finden Sie unter ["Hinzufügen von Karten und Kartenaktionen"](~/task-modules-and-cards/cards/cards-actions.md).

Weitere Informationen zur Office 365 Connectorkarte finden [Sie unter Verwenden von Office 365 Connectorkarten](~/task-modules-and-cards/cards/cards-reference.md#office-365-connector-card).

Die Ergebnisliste wird in der benutzeroberfläche Microsoft Teams mit einer Vorschau der einzelnen Elemente angezeigt. Die Vorschau wird auf eine der beiden folgenden Arten generiert:

* Verwenden der `preview` Eigenschaft innerhalb des Objekts `attachment` . Die `preview` Anlage kann nur ein Held oder eine Miniaturansichtskarte sein.
* Extrahieren aus den grundlegenden `title`, `text`und `image` Eigenschaften des Objekts `attachment` . Die grundlegenden Eigenschaften werden nur verwendet, wenn die `preview` Eigenschaft nicht angegeben ist.

Bei Hero- oder Miniaturansichtenkarten werden mit Ausnahme der Aktion zum Aufrufen anderer Aktionen wie Schaltfläche und Tippen in der Vorschaukarte nicht unterstützt.

Um eine adaptive Karte oder Office 365 Connectorkarte zu senden, müssen Sie eine Vorschau einschließen. Die `preview` Eigenschaft muss eine Hero- oder Miniaturansichtenkarte sein. Wenn Sie die Vorschaueigenschaft nicht im `attachment` Objekt angeben, wird keine Vorschau generiert.

Für Hero- und Miniaturansichtenkarten müssen Sie keine Vorschaueigenschaft angeben, eine Vorschau wird standardmäßig generiert.

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
> `OnTeamsMessagingExtensionSelectItemAsync` wird in der Mobilen Teams-Anwendung nicht ausgelöst.

## <a name="default-query"></a>Standardabfrage

Wenn Sie im Manifest festlegen `initialRun` `true`, gibt Microsoft Teams eine **Standardabfrage** aus, wenn der Benutzer die Nachrichtenerweiterung zum ersten Mal öffnet. Ihr Dienst kann auf diese Abfrage mit einer Reihe von vorab ausgefüllten Ergebnissen antworten. Dies ist nützlich, wenn ihr Suchbefehl eine Authentifizierung oder Konfiguration erfordert und zuletzt angezeigte Elemente, Favoriten oder andere Informationen angezeigt werden, die nicht von benutzereingaben abhängig sind.

Die Standardabfrage hat die gleiche Struktur wie jede normale Benutzerabfrage, wobei das Feld auf `initialRun` das `name` folgende Objekt festgelegt und `value` festgelegt `true` ist:

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
|Teams Nachrichtenerweiterungsaktion| Beschreibt das Definieren von Aktionsbefehlen, das Erstellen eines Aufgabenmoduls und das Reagieren auf Aufgabenmodul-Sendeaktionen. |[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/51.teams-messaging-extensions-action)|[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/51.teams-messaging-extensions-action) |
|Teams Nachrichtenerweiterungssuche   |  Beschreibt, wie Sie Suchbefehle definieren und auf Suchvorgänge reagieren.        |[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/50.teams-messaging-extensions-search)|[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/50.teams-messaging-extensions-search)|

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Hinzufügen der Authentifizierung zu einer Nachrichtenerweiterung](~/messaging-extensions/how-to/add-authentication.md)

## <a name="see-also"></a>Siehe auch

[Hinzufügen einer Konfiguration zu einer Nachrichtenerweiterung](~/get-started/first-message-extension.md)
