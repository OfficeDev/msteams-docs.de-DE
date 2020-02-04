---
title: Auf Suchbefehl Antworten
author: clearab
description: Gewusst wie Antworten auf den Suchbefehl von einer Messaging Erweiterung in einer Microsoft Teams-app.
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: e8b40dd8f422ffbd2537e8fa76a38c15eb6208de
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674578"
---
# <a name="respond-to-the-search-command"></a>Antworten auf den Suchbefehl

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

Der Webdienst erhält eine `composeExtension/query` Invoke-Nachricht, die ein `value` Objekt mit den Suchparametern enthält. Dieser Aufruf wird ausgelöst:

* Als Zeichen werden in das Suchfeld eingegeben.
* Wenn `initialRun` im App-Manifest auf true festgelegt ist, erhalten Sie die Invoke-Meldung, sobald der Suchbefehl aufgerufen wird. Siehe [Standardabfrage](#default-query).

Die Anforderungsparameter selbst werden im- `value` Objekt in der Anforderung gefunden, die die folgenden Eigenschaften enthält:

| Eigenschaftenname | Zweck |
|---|---|
| `commandId` | Der Name des vom Benutzer aufgerufenen Befehls, der einem der im App-Manifest deklarierten Befehle entspricht. |
| `parameters` | Array von Parametern. Jedes Parameter-Objekt enthält den Namen des Parameters sowie den vom Benutzer bereitgestellten Parameterwert. |
| `queryOptions` | Paginierung Parameter: <br>`skip`: Skip count für diese Abfrage <br>`count`: Anzahl der zurückzugebenden Elemente |

# <a name="cnettabdotnet"></a>[C#-/.net](#tab/dotnet)

```csharp
protected override async Task<MessagingExtensionResponse> OnTeamsMessagingExtensionQueryAsync(ITurnContext<IInvokeActivity> turnContext, MessagingExtensionQuery query, CancellationToken cancellationToken)
{
  //code to handle the query
}
```

# <a name="typescriptnodejstabtypescript"></a>[Manuskript/Node. js](#tab/typescript)

```typescript
class TeamsMessagingExtensionsSearch extends TeamsActivityHandler {
    async handleTeamsMessagingExtensionQuery(context, query) {
  //code to handle the query
    }
}
```

# <a name="jsontabjson"></a>[Json](#tab/json)

Die folgende JSON wird verkürzt, um die relevantesten Abschnitte hervorzuheben.

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

Wenn der Benutzer eine Abfrage ausführt, gibt Microsoft Teams eine synchrone http-Anforderung an Ihren Dienst aus. An diesem Zeitpunkt hat der Code 5 Sekunden, um eine HTTP-Antwort auf die Anforderung bereitzustellen. Während dieser Zeit kann der Dienst zusätzliche Suchvorgänge durchführen oder eine andere Geschäftslogik, die für die Zustellung der Anforderung benötigt wird.

Ihr Dienst sollte mit den Ergebnissen Antworten, die mit der Benutzerabfrage übereinstimmen. Die Antwort muss einen HTTP-Statuscode `200 OK` und ein gültiges Application/JSON-Objekt mit folgendem Text angeben:

|Eigenschaftenname|Zweck|
|---|---|
|`composeExtension`|Antwortumschlag auf oberster Ebene.|
|`composeExtension.type`|Typ der Antwort. Die folgenden Typen werden unterstützt: <br>`result`: zeigt eine Liste der Suchergebnisse an. <br>`auth`: der Benutzer wird aufgefordert, sich zu authentifizieren. <br>`config`: der Benutzer wird aufgefordert, die Messaging Erweiterung einzurichten. <br>`message`: zeigt eine nur-Text-Nachricht an. |
|`composeExtension.attachmentLayout`|Gibt das Layout der Anlagen an. Wird für Antworten vom Typ `result`verwendet. <br>Derzeit werden die folgenden Typen unterstützt: <br>`list`: eine Liste von Kartenobjekten, die Miniaturansichten, Titel und Textfelder enthalten <br>`grid`: ein Raster von Miniaturbildern |
|`composeExtension.attachments`|Array gültiger Attachment-Objekte. Wird für Antworten vom Typ `result`verwendet. <br>Derzeit werden die folgenden Typen unterstützt: <br>`application/vnd.microsoft.card.thumbnail` <br>`application/vnd.microsoft.card.hero` <br>`application/vnd.microsoft.teams.card.o365connector` <br>`application/vnd.microsoft.card.adaptive`|
|`composeExtension.suggestedActions`|Vorgeschlagene Aktionen. Wird für Antworten vom Typ `auth` oder `config`verwendet. |
|`composeExtension.text`|Anzuzeigende Meldung. Wird für Antworten vom Typ `message`verwendet. |

### <a name="response-card-types-and-previews"></a>Antwortkarten Typen und-Vorschauen

Wir unterstützen die folgenden Anlagentypen:

* [Miniatur Ansichtskarte](~/task-modules-and-cards/cards/cards-reference.md#thumbnail-card)
* [Hero Card](~/task-modules-and-cards/cards/cards-reference.md#hero-card)
* [Office 365-Anschluss Karte](~/task-modules-and-cards/cards/cards-reference.md#office-365-connector-card)
* [Adaptive Karte](~/task-modules-and-cards/cards/cards-reference.md#adaptive-card)

Eine Übersicht finden Sie unter [Was sind Karten](~/task-modules-and-cards/what-are-cards.md) .

Weitere Informationen zur Verwendung der Miniaturansicht-und Hero-Kartentypen finden Sie unter [Add Cards and Card Actions](~/task-modules-and-cards/cards/cards-actions.md).

Weitere Informationen zur Office 365-Verbindungskarte finden Sie unter [using Office 365 Connector Cards](~/task-modules-and-cards/cards/cards-reference.md#office-365-connector-card).

Die Ergebnisliste wird auf der Microsoft Teams-Benutzeroberfläche mit einer Vorschau der einzelnen Elemente angezeigt. Die Vorschau wird auf eine von zwei Arten generiert:

* Verwenden der `preview` -Eigenschaft innerhalb `attachment` des-Objekts. Die `preview` Anlage kann nur eine Hero-oder Thumbnail-Karte sein.
* Extrahiert aus den Eigenschaften `title`Basic `text`, und `image` und der Anlage. Diese werden nur verwendet, wenn `preview` die Eigenschaft nicht festgelegt ist und diese Eigenschaften verfügbar sind.

Sie können eine Vorschau einer adaptiven Karte oder Office 365-connectorkarte in der Ergebnisliste einfach über die Vorschau-Eigenschaft anzeigen. Dies ist nicht erforderlich, wenn die Ergebnisse bereits Hero-oder Thumbnail-Karten sind. Wenn Sie die Vorschau Anlage verwenden, muss es sich entweder um eine Hero-oder eine Miniatur Ansichtskarte handeln. Wenn keine Preview-Eigenschaft angegeben wird, schlägt die Vorschau der Karte fehl, und es wird nichts angezeigt.

### <a name="response-example"></a>Anforderungsbeispiel

# <a name="cnettabdotnet"></a>[C#-/.net](#tab/dotnet)

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

# <a name="typescriptnodejstabtypescript"></a>[Manuskript/Node. js](#tab/typescript)

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

# <a name="jsontabjson"></a>[Json](#tab/json)

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
              "activityImage": "https://placekitten.com/200/200"
            },
            {
              "title": "Details",
              "facts": [
                {
                  "name": "Assigned to:",
                  "value": "[Larry Brown](mailto:larryb@example.com)"
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

Wenn Sie im `initialRun` Manifest `true` auf festlegen, gibt Microsoft Teams eine "Standard"-Abfrage aus, wenn der Benutzer die Messaging Erweiterung zum ersten Mal öffnet. Ihr Dienst kann auf diese Abfrage mit einer Reihe vorab aufgefüllter Ergebnisse Antworten. Dies kann hilfreich sein, wenn Ihr Suchbefehl Authentifizierung oder Konfiguration erfordert, wobei zuletzt angezeigte Elemente, Favoriten oder andere Informationen angezeigt werden, die nicht von der Benutzereingabe abhängig sind.

Die Standard `name` Abfrage hat dieselbe Struktur wie jede reguläre Benutzerabfrage, wobei das Feld auf `initialRun` festgelegt und `value` auf `true` wie in dem unten stehenden Objekt festgelegt ist.

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

## <a name="next-steps"></a>Nächste Schritte

Hinzufügen von Authentifizierung und/oder Konfiguration

* [Hinzufügen einer Authentifizierung zu einer Messaging Erweiterung](~/messaging-extensions/how-to/add-authentication.md)
* [Hinzufügen einer Konfiguration zu einer Messaging Erweiterung](~/messaging-extensions/how-to/add-configuration-page.md)

Bereitstellen der Konfiguration

* [Bereitstellen des App-Pakets](~/concepts/deploy-and-publish/apps-upload.md)

[!include[messaging-extension-learn-more](~/includes/messaging-extensions/learn-more.md)]
