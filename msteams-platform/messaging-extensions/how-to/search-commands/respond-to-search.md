---
title: Antworten auf Suchbefehl
author: clearab
description: So reagieren Sie auf den Suchbefehl aus einer Messagingerweiterung in einer Microsoft Teams App.
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: 15b48b135f656feeb3cfb28ffbe12852ddb66359
ms.sourcegitcommit: e50cdeb6b7f481e12911b2bb74a8da22af0bffac
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/01/2021
ms.locfileid: "52710634"
---
# <a name="respond-to-search-command"></a>Antworten auf Suchbefehl

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

Nachdem der Benutzer den Suchbefehl übermittelt hat, empfängt ihr Webdienst eine Aufrufnachricht, die ein Objekt mit `composeExtension/query` `value` den Suchparametern enthält. Dieser Aufruf wird mit den folgenden Bedingungen ausgelöst:

* As characters are entered into the search box.
* `initialRun` in Ihrem App-Manifest auf true festgelegt ist, erhalten Sie die Aufrufnachricht, sobald der Suchbefehl aufgerufen wird. Weitere Informationen finden Sie unter [Standardabfrage](#default-query).

In diesem Dokument erfahren Sie, wie Sie auf Benutzeranforderungen in Form von Karten und Vorschauen reagieren, und die Bedingungen, unter denen Microsoft Teams standardabfragen.

Die Anforderungsparameter befinden sich im `value` Objekt in der Anforderung, das die folgenden Eigenschaften enthält:

| Eigenschaftenname | Zweck |
|---|---|
| `commandId` | Der Name des Befehls, der vom Benutzer aufgerufen wird und einem der befehle, die im App-Manifest deklariert sind, zustimmungen. |
| `parameters` | Array von Parametern. Jedes Parameterobjekt enthält den Parameternamen sowie den vom Benutzer bereitgestellten Parameterwert. |
| `queryOptions` | Paginierungsparameter: <br>`skip`: Anzahl für diese Abfrage überspringen <br>`count`: Anzahl der zurückzukehrenden Elemente. |

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

# <a name="json"></a>[Json](#tab/json)

Die folgende JSON wird verkürzt, um die relevantesten Abschnitte zu markieren.

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

Wenn der Benutzer eine Abfrage ausführt, Microsoft Teams eine synchrone HTTP-Anforderung an Ihren Dienst aus. An diesem Punkt verfügt Ihr Code über `5` Sekunden, um eine HTTP-Antwort auf die Anforderung zu senden. Während dieser Zeit kann Ihr Dienst zusätzliche Nachschlage- oder sonstige Geschäftslogik ausführen, die für die Anforderung erforderlich ist.

Ihr Dienst muss mit den Ergebnissen antworten, die mit der Benutzerabfrage übereinstimmen. Die Antwort muss einen HTTP-Statuscode von und eine gültige Anwendung oder `200 OK` ein JSON-Objekt mit den folgenden Eigenschaften angeben:

|Eigenschaftenname|Zweck|
|---|---|
|`composeExtension`|Antwortumschlag auf oberster Ebene.|
|`composeExtension.type`|Antworttyp. Die folgenden Typen werden unterstützt: <br>`result`: Zeigt eine Liste der Suchergebnisse an <br>`auth`: Fordert den Benutzer zur Authentifizierung auf <br>`config`: Fordert den Benutzer auf, die Messagingerweiterung einrichten <br>`message`: Zeigt eine Nur-Text-Nachricht an |
|`composeExtension.attachmentLayout`|Gibt das Layout der Anlagen an. Wird für Antworten vom Typ `result` verwendet. <br>Derzeit werden die folgenden Typen unterstützt: <br>`list`: Eine Liste von Kartenobjekten, die Miniaturansichten, Titel und Textfelder enthalten <br>`grid`: Ein Raster von Miniaturansichtsbildern |
|`composeExtension.attachments`|Array gültiger Anlagenobjekte. Wird für Antworten vom Typ `result` verwendet. <br>Derzeit werden die folgenden Typen unterstützt: <br>`application/vnd.microsoft.card.thumbnail` <br>`application/vnd.microsoft.card.hero` <br>`application/vnd.microsoft.teams.card.o365connector` <br>`application/vnd.microsoft.card.adaptive`|
|`composeExtension.suggestedActions`|Vorgeschlagene Aktionen. Wird für Antworten vom Typ oder `auth` `config` verwendet. |
|`composeExtension.text`|Meldung, die angezeigt werden soll. Wird für Antworten vom Typ `message` verwendet. |

### <a name="response-card-types-and-previews"></a>Typen und Vorschauen von Antwortkarten

Teams unterstützt die folgenden Kartentypen:

* [Miniaturansichtskarte](~/task-modules-and-cards/cards/cards-reference.md#thumbnail-card)
* [Heldenkarte](~/task-modules-and-cards/cards/cards-reference.md#hero-card)
* [Office 365 Connectorkarte](~/task-modules-and-cards/cards/cards-reference.md#office-365-connector-card)
* [Adaptive Karte](~/task-modules-and-cards/cards/cards-reference.md#adaptive-card)

Ein besseres Verständnis und eine bessere Übersicht über Karten finden Sie unter [Was sind Karten.](~/task-modules-and-cards/what-are-cards.md)

Informationen zur Verwendung der Miniaturansichts- und Heldenkartentypen finden Sie unter [Hinzufügen von Karten und Kartenaktionen.](~/task-modules-and-cards/cards/cards-actions.md)

Weitere Informationen zur Office 365 Connectorkarte finden Sie unter [Using Office 365 Connector cards](~/task-modules-and-cards/cards/cards-reference.md#office-365-connector-card).

Die Ergebnisliste wird in der benutzeroberfläche Microsoft Teams mit einer Vorschau der einzelnen Elemente angezeigt. Die Vorschau wird auf eine der beiden Arten generiert:

* Verwenden der `preview` Eigenschaft innerhalb des `attachment` Objekts. Die `preview` Anlage kann nur eine Hero- oder Miniaturansichtskarte sein.
* Extrahiert aus den grundlegenden `title` Eigenschaften , und der `text` `image` Anlage. Diese werden nur verwendet, wenn `preview` die Eigenschaft nicht festgelegt ist und diese Eigenschaften verfügbar sind.
* Die Schaltfläche "Held" oder "Miniaturansicht" und "Tippen" (außer aufrufen) werden auf der Vorschaukarte nicht unterstützt.

Sie können eine Vorschau einer adaptiven Karte oder einer Office 365 in der Ergebnisliste anzeigen, indem Sie die Vorschaueigenschaft verwenden. Die Preview-Eigenschaft ist nicht erforderlich, wenn die Ergebnisse bereits Hero- oder Miniaturansichtskarten sind. Wenn Sie die Vorschauanlage verwenden, muss es sich entweder um eine Hero- oder Miniaturansichtskarte geben. Wenn keine Vorschaueigenschaft angegeben ist, schlägt die Vorschau der Karte fehl, und es wird nichts angezeigt.

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

# <a name="json"></a>[Json](#tab/json)

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

## <a name="default-query"></a>Standardabfrage

Wenn Sie im Manifest auf festgelegt Microsoft Teams eine Standardabfrage aus, wenn der Benutzer die `initialRun` `true` Messagingerweiterung zum ersten Mal öffnet.  Ihr Dienst kann auf diese Abfrage mit einer Reihe von vorab ausgefüllten Ergebnissen reagieren. Dies ist hilfreich, wenn ihr Suchbefehl eine Authentifizierung oder Konfiguration erfordert und zuletzt angezeigte Elemente, Favoriten oder andere Informationen, die nicht von benutzereingaben abhängig sind, angezeigt wird.

Die Standardabfrage hat dieselbe Struktur wie jede normale Benutzerabfrage, und das Feld wird wie im folgenden Objekt dargestellt auf `name` `initialRun` festgelegt und auf `value` `true` festgelegt:

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
|Teams Messagingerweiterungsaktion| Beschreibt, wie Sie Aktionsbefehle definieren, Aufgabenmodul erstellen und auf Die Absendenaktion des Aufgabenmoduls reagieren. |[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/51.teams-messaging-extensions-action)|[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/51.teams-messaging-extensions-action) | 
|Teams messaging extension search   |  Beschreibt, wie Sie Suchbefehle definieren und auf Suchbefehle reagieren.        |[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/50.teams-messaging-extensions-search)|[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/50.teams-messaging-extensions-search)|

## <a name="see-also"></a>Siehe auch

[Hinzufügen einer Konfiguration zu einer Messagingerweiterung](~/get-started/first-message-extension.md)

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Hinzufügen der Authentifizierung zu einer Messagingerweiterung](~/messaging-extensions/how-to/add-authentication.md)



