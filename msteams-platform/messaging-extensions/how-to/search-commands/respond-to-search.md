---
title: Auf Suchbefehl antworten
author: surbhigupta
description: Antworten auf den Suchbefehl aus einer Messaging-Erweiterung in einer Microsoft Teams-App.
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: 3d82c7be0a0bbe5cf0ef991a90b277de38fcf4d5
ms.sourcegitcommit: 623d81eb079d1842813265746a5fe0fe6311b196
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/22/2021
ms.locfileid: "53068939"
---
# <a name="respond-to-search-command"></a>Auf Suchbefehl antworten

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

Nachdem der Benutzer den Suchbefehl übermittelt hat, empfängt Ihr Webdienst eine `composeExtension/query` Aufrufnachricht, die ein `value` Objekt mit den Suchparametern enthält. Dieser Aufruf wird mit den folgenden Bedingungen ausgelöst:

* Wenn Zeichen in das Suchfeld eingegeben werden.
* `initialRun` in Ihrem App-Manifest auf "true" festgelegt ist, erhalten Sie die Aufrufnachricht, sobald der Suchbefehl aufgerufen wird. Weitere Informationen finden Sie unter [Standardabfrage.](#default-query)

In diesem Dokument erfahren Sie, wie Sie auf Benutzeranforderungen in Form von Karten und Vorschauen reagieren und unter welchen Bedingungen Microsoft Teams eine Standardabfrage ausgibt.

Die Anforderungsparameter befinden sich im `value` Objekt in der Anforderung, das die folgenden Eigenschaften enthält:

| Eigenschaftenname | Zweck |
|---|---|
| `commandId` | Der Name des vom Benutzer aufgerufenen Befehls, der einem der im App-Manifest deklarierten Befehle entspricht. |
| `parameters` | Array von Parametern. Jedes Parameterobjekt enthält den Parameternamen sowie den vom Benutzer bereitgestellten Parameterwert. |
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

# <a name="json"></a>[Json](#tab/json)

Der json unten ist gekürzt, um die relevantesten Abschnitte hervorzuheben.

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

## <a name="respond-to-user-requests"></a>Antworten auf Benutzeranforderungen

Wenn der Benutzer eine Abfrage ausführt, gibt Microsoft Teams eine synchrone HTTP-Anforderung an Ihren Dienst aus. An diesem Punkt hat Ihr Code Sekunden Zeit, `5` um eine HTTP-Antwort auf die Anforderung bereitzustellen. Während dieser Zeit kann Ihr Dienst zusätzliche Nachschlagevorgänge oder eine beliebige andere Geschäftslogik ausführen, die für die Bearbeitung der Anforderung erforderlich ist.

Ihr Dienst muss mit den Ergebnissen antworten, die der Benutzerabfrage entsprechen. Die Antwort muss einen HTTP-Statuscode `200 OK` und ein gültiges Anwendungs- oder JSON-Objekt mit den folgenden Eigenschaften angeben:

|Eigenschaftenname|Zweck|
|---|---|
|`composeExtension`|Antwortumschlag auf oberster Ebene.|
|`composeExtension.type`|Antworttyp. Die folgenden Typen werden unterstützt: <br>`result`: Zeigt eine Liste der Suchergebnisse an <br>`auth`: Fordert den Benutzer zur Authentifizierung auf <br>`config`: Fordert den Benutzer auf, die Messaging-Erweiterung einzurichten <br>`message`: Zeigt eine Nur-Text-Nachricht an |
|`composeExtension.attachmentLayout`|Gibt das Layout der Anlagen an. Wird für Antworten vom Typ `result` verwendet. <br>Derzeit werden die folgenden Typen unterstützt: <br>`list`: Eine Liste von Kartenobjekten, die Miniaturansichten, Titel und Textfelder enthalten <br>`grid`: Ein Raster mit Miniaturansichten |
|`composeExtension.attachments`|Array gültiger Anlagenobjekte. Wird für Antworten vom Typ `result` verwendet. <br>Derzeit werden die folgenden Typen unterstützt: <br>`application/vnd.microsoft.card.thumbnail` <br>`application/vnd.microsoft.card.hero` <br>`application/vnd.microsoft.teams.card.o365connector` <br>`application/vnd.microsoft.card.adaptive`|
|`composeExtension.suggestedActions`|Vorgeschlagene Aktionen. Wird für Antworten vom Typ `auth` oder `config` verwendet. |
|`composeExtension.text`|Anzuzeigende Meldung. Wird für Antworten vom Typ `message` verwendet. |

### <a name="response-card-types-and-previews"></a>Antwortkartentypen und Vorschauen

Teams unterstützt die folgenden Kartentypen:

* [Miniaturansichtskarte](~/task-modules-and-cards/cards/cards-reference.md#thumbnail-card)
* [Hero-Karte](~/task-modules-and-cards/cards/cards-reference.md#hero-card)
* [Office 365 Connectorkarte](~/task-modules-and-cards/cards/cards-reference.md#office-365-connector-card)
* [Adaptive Karte](~/task-modules-and-cards/cards/cards-reference.md#adaptive-card)

Um ein besseres Verständnis und einen besseren Überblick über Karten zu haben, sehen Sie sich an, [was Karten sind.](~/task-modules-and-cards/what-are-cards.md)

Informationen zur Verwendung der Miniaturansicht- und Herokartentypen finden Sie unter [Hinzufügen von Karten und Kartenaktionen.](~/task-modules-and-cards/cards/cards-actions.md)

Weitere Informationen zur Office 365 Connectorkarte finden Sie unter [Using Office 365 Connector cards](~/task-modules-and-cards/cards/cards-reference.md#office-365-connector-card).

Die Ergebnisliste wird auf der Microsoft Teams Benutzeroberfläche mit einer Vorschau der einzelnen Elemente angezeigt. Die Vorschau wird auf eine der beiden folgenden Arten generiert:

* Verwenden der `preview` Eigenschaft innerhalb des `attachment` Objekts. Die `preview` Anlage kann nur eine Hero- oder Miniaturansichtskarte sein.
* Extrahiert aus den `title` grundlegenden `text` , und Eigenschaften `image` der Anlage. Diese werden nur verwendet, wenn die `preview` Eigenschaft nicht festgelegt ist und diese Eigenschaften verfügbar sind.
* Die Schaltfläche "Hero"- oder "Miniaturansichtskarte" und tippen auf Aktionen mit Ausnahme des Aufrufs werden in der Vorschaukarte nicht unterstützt.

Sie können eine Vorschau einer adaptiven Karte oder Office 365 Connectorkarte in der Ergebnisliste mithilfe der Vorschaueigenschaft anzeigen. Die Vorschaueigenschaft ist nicht erforderlich, wenn die Ergebnisse bereits Hero- oder Miniaturansichtskarten sind. Wenn Sie die Vorschauanlage verwenden, muss es sich entweder um eine Hero- oder eine Miniaturansichtskarte handeln. Wenn keine Vorschaueigenschaft angegeben ist, schlägt die Vorschau der Karte fehl, und es wird nichts angezeigt.

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

Wenn Sie `initialRun` `true` dies im Manifest festlegen, gibt Microsoft Teams eine **Standardabfrage** aus, wenn der Benutzer die Messaging-Erweiterung zum ersten Mal öffnet. Ihr Dienst kann auf diese Abfrage mit einer Reihe vorab ausgefüllter Ergebnisse antworten. Dies ist nützlich, wenn ihr Suchbefehl eine Authentifizierung oder Konfiguration erfordert und zuletzt angezeigte Elemente, Favoriten oder andere Informationen anzeigt, die nicht von benutzereingaben abhängig sind.

Die Standardabfrage weist die gleiche Struktur wie jede normale Benutzerabfrage auf, wobei das `name` Feld auf das folgende Objekt festgelegt und festgelegt `initialRun` `value` `true` ist:

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
|Teams Messaging-Erweiterungsaktion| Beschreibt, wie Aktionsbefehle definiert, Aufgabenmodul erstellt und auf Aufgabenmodul-Sendeaktion reagiert wird. |[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/51.teams-messaging-extensions-action)|[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/51.teams-messaging-extensions-action) | 
|Teams Messaging-Erweiterungssuche   |  Beschreibt, wie Suchbefehle definiert und auf Suchvorgänge reagiert wird.        |[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/50.teams-messaging-extensions-search)|[View](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/50.teams-messaging-extensions-search)|

## <a name="see-also"></a>Siehe auch

[Hinzufügen einer Konfiguration zu einer Messaging-Erweiterung](~/get-started/first-message-extension.md)

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Hinzufügen der Authentifizierung zu einer Messaging-Erweiterung](~/messaging-extensions/how-to/add-authentication.md)



