---
title: Antworten auf Suchbefehl
author: clearab
description: So reagieren Sie auf den Suchbefehl über eine Messagingerweiterung in einer Microsoft Teams-App.
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: 044c6eebe9489ed404c9fa89b29c306cde8c7363
ms.sourcegitcommit: a732789190f59ec1f3699e8ad2f06387e8fe1458
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2021
ms.locfileid: "52058586"
---
# <a name="respond-to-search-command"></a><span data-ttu-id="ed0ec-103">Antworten auf Suchbefehl</span><span class="sxs-lookup"><span data-stu-id="ed0ec-103">Respond to search command</span></span>

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

<span data-ttu-id="ed0ec-104">Nachdem der Benutzer den Suchbefehl übermittelt hat, empfängt ihr Webdienst eine Aufrufnachricht, die ein Objekt mit `composeExtension/query` `value` den Suchparametern enthält.</span><span class="sxs-lookup"><span data-stu-id="ed0ec-104">After the user submits the search command, your web service receives a `composeExtension/query` invoke message that contains a `value` object with the search parameters.</span></span> <span data-ttu-id="ed0ec-105">Dieser Aufruf wird mit den folgenden Bedingungen ausgelöst:</span><span class="sxs-lookup"><span data-stu-id="ed0ec-105">This invoke is triggered with the following conditions:</span></span>

* <span data-ttu-id="ed0ec-106">As characters are entered into the search box.</span><span class="sxs-lookup"><span data-stu-id="ed0ec-106">As characters are entered into the search box.</span></span>
* <span data-ttu-id="ed0ec-107">`initialRun` in Ihrem App-Manifest auf true festgelegt ist, erhalten Sie die Aufrufnachricht, sobald der Suchbefehl aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="ed0ec-107">`initialRun` is set to true in your app manifest, you receive the invoke message as soon as the search command is invoked.</span></span> <span data-ttu-id="ed0ec-108">Weitere Informationen finden Sie unter [Standardabfrage](#default-query).</span><span class="sxs-lookup"><span data-stu-id="ed0ec-108">For more information, see [default query](#default-query).</span></span>

<span data-ttu-id="ed0ec-109">In diesem Dokument erfahren Sie, wie Sie auf Benutzeranforderungen in Form von Karten und Vorschauen reagieren und unter welchen Bedingungen Microsoft Teams eine Standardabfrage aust.</span><span class="sxs-lookup"><span data-stu-id="ed0ec-109">This document guides you on how to respond to user requests in the form of cards and previews, and the conditions under which Microsoft Teams issues a default query.</span></span>

<span data-ttu-id="ed0ec-110">Die Anforderungsparameter befinden sich im `value` Objekt in der Anforderung, das die folgenden Eigenschaften enthält:</span><span class="sxs-lookup"><span data-stu-id="ed0ec-110">The request parameters are found in the `value` object in the request, which includes the following properties:</span></span>

| <span data-ttu-id="ed0ec-111">Eigenschaftenname</span><span class="sxs-lookup"><span data-stu-id="ed0ec-111">Property name</span></span> | <span data-ttu-id="ed0ec-112">Zweck</span><span class="sxs-lookup"><span data-stu-id="ed0ec-112">Purpose</span></span> |
|---|---|
| `commandId` | <span data-ttu-id="ed0ec-113">Der Name des Befehls, der vom Benutzer aufgerufen wird und einem der befehle, die im App-Manifest deklariert sind, zustimmungen.</span><span class="sxs-lookup"><span data-stu-id="ed0ec-113">The name of the command invoked by the user, matching one of the commands declared in the app manifest.</span></span> |
| `parameters` | <span data-ttu-id="ed0ec-114">Array von Parametern.</span><span class="sxs-lookup"><span data-stu-id="ed0ec-114">Array of parameters.</span></span> <span data-ttu-id="ed0ec-115">Jedes Parameterobjekt enthält den Parameternamen sowie den vom Benutzer bereitgestellten Parameterwert.</span><span class="sxs-lookup"><span data-stu-id="ed0ec-115">Each parameter object contains the parameter name, along with the parameter value provided by the user.</span></span> |
| `queryOptions` | <span data-ttu-id="ed0ec-116">Paginierungsparameter:</span><span class="sxs-lookup"><span data-stu-id="ed0ec-116">Pagination parameters:</span></span> <br><span data-ttu-id="ed0ec-117">`skip`: Anzahl für diese Abfrage überspringen</span><span class="sxs-lookup"><span data-stu-id="ed0ec-117">`skip`: Skip count for this query</span></span> <br><span data-ttu-id="ed0ec-118">`count`: Anzahl der zurückzukehrenden Elemente.</span><span class="sxs-lookup"><span data-stu-id="ed0ec-118">`count`: Number of elements to return.</span></span> |

# <a name="cnet"></a>[<span data-ttu-id="ed0ec-119">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="ed0ec-119">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task<MessagingExtensionResponse> OnTeamsMessagingExtensionQueryAsync(ITurnContext<IInvokeActivity> turnContext, MessagingExtensionQuery query, CancellationToken cancellationToken)
{
  //code to handle the query
}
```

# <a name="typescriptnodejs"></a>[<span data-ttu-id="ed0ec-120">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="ed0ec-120">TypeScript/Node.js</span></span>](#tab/typescript)

```typescript
class TeamsMessagingExtensionsSearch extends TeamsActivityHandler {
    async handleTeamsMessagingExtensionQuery(context, query) {
  //code to handle the query
    }
}
```

# <a name="json"></a>[<span data-ttu-id="ed0ec-121">Json</span><span class="sxs-lookup"><span data-stu-id="ed0ec-121">JSON</span></span>](#tab/json)

<span data-ttu-id="ed0ec-122">Die folgende JSON wird verkürzt, um die relevantesten Abschnitte zu markieren.</span><span class="sxs-lookup"><span data-stu-id="ed0ec-122">The JSON below is shortened to highlight the most relevant sections.</span></span>

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

## <a name="respond-to-user-requests"></a><span data-ttu-id="ed0ec-123">Reagieren auf Benutzeranforderungen</span><span class="sxs-lookup"><span data-stu-id="ed0ec-123">Respond to user requests</span></span>

<span data-ttu-id="ed0ec-124">Wenn der Benutzer eine Abfrage ausführt, stellt Microsoft Teams eine synchrone HTTP-Anforderung an Ihren Dienst aus.</span><span class="sxs-lookup"><span data-stu-id="ed0ec-124">When the user performs a query, Microsoft Teams issues a synchronous HTTP request to your service.</span></span> <span data-ttu-id="ed0ec-125">An diesem Punkt verfügt Ihr Code über `5` Sekunden, um eine HTTP-Antwort auf die Anforderung zu senden.</span><span class="sxs-lookup"><span data-stu-id="ed0ec-125">At that point, your code has `5` seconds to provide an HTTP response to the request.</span></span> <span data-ttu-id="ed0ec-126">Während dieser Zeit kann Ihr Dienst zusätzliche Nachschlage- oder sonstige Geschäftslogik ausführen, die für die Anforderung erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="ed0ec-126">During this time, your service can perform additional lookup, or any other business logic needed to serve the request.</span></span>

<span data-ttu-id="ed0ec-127">Ihr Dienst muss mit den Ergebnissen antworten, die mit der Benutzerabfrage übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="ed0ec-127">Your service must respond with the results matching the user query.</span></span> <span data-ttu-id="ed0ec-128">Die Antwort muss einen HTTP-Statuscode von und eine gültige Anwendung oder `200 OK` ein JSON-Objekt mit den folgenden Eigenschaften angeben:</span><span class="sxs-lookup"><span data-stu-id="ed0ec-128">The response must indicate an HTTP status code of `200 OK` and a valid application or JSON object with the following properties:</span></span>

|<span data-ttu-id="ed0ec-129">Eigenschaftenname</span><span class="sxs-lookup"><span data-stu-id="ed0ec-129">Property name</span></span>|<span data-ttu-id="ed0ec-130">Zweck</span><span class="sxs-lookup"><span data-stu-id="ed0ec-130">Purpose</span></span>|
|---|---|
|`composeExtension`|<span data-ttu-id="ed0ec-131">Antwortumschlag auf oberster Ebene.</span><span class="sxs-lookup"><span data-stu-id="ed0ec-131">Top-level response envelope.</span></span>|
|`composeExtension.type`|<span data-ttu-id="ed0ec-132">Antworttyp.</span><span class="sxs-lookup"><span data-stu-id="ed0ec-132">Type of response.</span></span> <span data-ttu-id="ed0ec-133">Die folgenden Typen werden unterstützt:</span><span class="sxs-lookup"><span data-stu-id="ed0ec-133">The following types are supported:</span></span> <br><span data-ttu-id="ed0ec-134">`result`: Zeigt eine Liste der Suchergebnisse an</span><span class="sxs-lookup"><span data-stu-id="ed0ec-134">`result`: Displays a list of search results</span></span> <br><span data-ttu-id="ed0ec-135">`auth`: Fordert den Benutzer zur Authentifizierung auf</span><span class="sxs-lookup"><span data-stu-id="ed0ec-135">`auth`: Asks the user to authenticate</span></span> <br><span data-ttu-id="ed0ec-136">`config`: Fordert den Benutzer auf, die Messagingerweiterung einrichten</span><span class="sxs-lookup"><span data-stu-id="ed0ec-136">`config`: Asks the user to set up the messaging extension</span></span> <br><span data-ttu-id="ed0ec-137">`message`: Zeigt eine Nur-Text-Nachricht an</span><span class="sxs-lookup"><span data-stu-id="ed0ec-137">`message`: Displays a plain text message</span></span> |
|`composeExtension.attachmentLayout`|<span data-ttu-id="ed0ec-138">Gibt das Layout der Anlagen an.</span><span class="sxs-lookup"><span data-stu-id="ed0ec-138">Specifies the layout of the attachments.</span></span> <span data-ttu-id="ed0ec-139">Wird für Antworten vom Typ `result` verwendet.</span><span class="sxs-lookup"><span data-stu-id="ed0ec-139">Used for responses of type `result`.</span></span> <br><span data-ttu-id="ed0ec-140">Derzeit werden die folgenden Typen unterstützt:</span><span class="sxs-lookup"><span data-stu-id="ed0ec-140">Currently, the following types are supported:</span></span> <br><span data-ttu-id="ed0ec-141">`list`: Eine Liste von Kartenobjekten, die Miniaturansichten, Titel und Textfelder enthalten</span><span class="sxs-lookup"><span data-stu-id="ed0ec-141">`list`: A list of card objects containing thumbnail, title, and text fields</span></span> <br><span data-ttu-id="ed0ec-142">`grid`: Ein Raster von Miniaturansichtsbildern</span><span class="sxs-lookup"><span data-stu-id="ed0ec-142">`grid`: A grid of thumbnail images</span></span> |
|`composeExtension.attachments`|<span data-ttu-id="ed0ec-143">Array gültiger Anlagenobjekte.</span><span class="sxs-lookup"><span data-stu-id="ed0ec-143">Array of valid attachment objects.</span></span> <span data-ttu-id="ed0ec-144">Wird für Antworten vom Typ `result` verwendet.</span><span class="sxs-lookup"><span data-stu-id="ed0ec-144">Used for responses of type `result`.</span></span> <br><span data-ttu-id="ed0ec-145">Derzeit werden die folgenden Typen unterstützt:</span><span class="sxs-lookup"><span data-stu-id="ed0ec-145">Currently, the following types are supported:</span></span> <br>`application/vnd.microsoft.card.thumbnail` <br>`application/vnd.microsoft.card.hero` <br>`application/vnd.microsoft.teams.card.o365connector` <br>`application/vnd.microsoft.card.adaptive`|
|`composeExtension.suggestedActions`|<span data-ttu-id="ed0ec-146">Vorgeschlagene Aktionen.</span><span class="sxs-lookup"><span data-stu-id="ed0ec-146">Suggested actions.</span></span> <span data-ttu-id="ed0ec-147">Wird für Antworten vom Typ oder `auth` `config` verwendet.</span><span class="sxs-lookup"><span data-stu-id="ed0ec-147">Used for responses of type `auth` or `config`.</span></span> |
|`composeExtension.text`|<span data-ttu-id="ed0ec-148">Meldung, die angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="ed0ec-148">Message to display.</span></span> <span data-ttu-id="ed0ec-149">Wird für Antworten vom Typ `message` verwendet.</span><span class="sxs-lookup"><span data-stu-id="ed0ec-149">Used for responses of type `message`.</span></span> |

### <a name="response-card-types-and-previews"></a><span data-ttu-id="ed0ec-150">Typen und Vorschauen von Antwortkarten</span><span class="sxs-lookup"><span data-stu-id="ed0ec-150">Response card types and previews</span></span>

<span data-ttu-id="ed0ec-151">Teams unterstützt die folgenden Kartentypen:</span><span class="sxs-lookup"><span data-stu-id="ed0ec-151">Teams supports the following card types:</span></span>

* [<span data-ttu-id="ed0ec-152">Miniaturansichtskarte</span><span class="sxs-lookup"><span data-stu-id="ed0ec-152">Thumbnail card</span></span>](~/task-modules-and-cards/cards/cards-reference.md#thumbnail-card)
* [<span data-ttu-id="ed0ec-153">Heldenkarte</span><span class="sxs-lookup"><span data-stu-id="ed0ec-153">Hero card</span></span>](~/task-modules-and-cards/cards/cards-reference.md#hero-card)
* [<span data-ttu-id="ed0ec-154">Office 365 Connector-Karte</span><span class="sxs-lookup"><span data-stu-id="ed0ec-154">Office 365 Connector card</span></span>](~/task-modules-and-cards/cards/cards-reference.md#office-365-connector-card)
* [<span data-ttu-id="ed0ec-155">Adaptive Karte</span><span class="sxs-lookup"><span data-stu-id="ed0ec-155">Adaptive Card</span></span>](~/task-modules-and-cards/cards/cards-reference.md#adaptive-card)

<span data-ttu-id="ed0ec-156">Ein besseres Verständnis und eine bessere Übersicht über Karten finden Sie unter [Was sind Karten.](~/task-modules-and-cards/what-are-cards.md)</span><span class="sxs-lookup"><span data-stu-id="ed0ec-156">To have a better understanding and overview on cards, see [what are cards](~/task-modules-and-cards/what-are-cards.md).</span></span>

<span data-ttu-id="ed0ec-157">Informationen zur Verwendung der Miniaturansichts- und Heldenkartentypen finden Sie unter [Hinzufügen von Karten und Kartenaktionen.](~/task-modules-and-cards/cards/cards-actions.md)</span><span class="sxs-lookup"><span data-stu-id="ed0ec-157">To learn how to use the thumbnail and hero card types, see [add cards and card actions](~/task-modules-and-cards/cards/cards-actions.md).</span></span>

<span data-ttu-id="ed0ec-158">Weitere Informationen zur Office 365 Connector-Karte finden Sie unter [Using Office 365 Connector cards](~/task-modules-and-cards/cards/cards-reference.md#office-365-connector-card).</span><span class="sxs-lookup"><span data-stu-id="ed0ec-158">For additional information regarding the Office 365 Connector card, see [Using Office 365 Connector cards](~/task-modules-and-cards/cards/cards-reference.md#office-365-connector-card).</span></span>

<span data-ttu-id="ed0ec-159">Die Ergebnisliste wird in der Benutzeroberfläche von Microsoft Teams mit einer Vorschau der einzelnen Elemente angezeigt.</span><span class="sxs-lookup"><span data-stu-id="ed0ec-159">The result list is displayed in the Microsoft Teams UI with a preview of each item.</span></span> <span data-ttu-id="ed0ec-160">Die Vorschau wird auf eine der beiden Arten generiert:</span><span class="sxs-lookup"><span data-stu-id="ed0ec-160">The preview is generated in one of the two ways:</span></span>

* <span data-ttu-id="ed0ec-161">Verwenden der `preview` Eigenschaft innerhalb des `attachment` Objekts.</span><span class="sxs-lookup"><span data-stu-id="ed0ec-161">Using the `preview` property within the `attachment` object.</span></span> <span data-ttu-id="ed0ec-162">Die `preview` Anlage kann nur eine Hero- oder Miniaturansichtskarte sein.</span><span class="sxs-lookup"><span data-stu-id="ed0ec-162">The `preview` attachment can only be a Hero or Thumbnail card.</span></span>
* <span data-ttu-id="ed0ec-163">Extrahiert aus den grundlegenden `title` Eigenschaften , und der `text` `image` Anlage.</span><span class="sxs-lookup"><span data-stu-id="ed0ec-163">Extracted from the basic `title`, `text`, and `image` properties of the attachment.</span></span> <span data-ttu-id="ed0ec-164">Diese werden nur verwendet, wenn `preview` die Eigenschaft nicht festgelegt ist und diese Eigenschaften verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="ed0ec-164">These are used only if the `preview` property is not set and these properties are available.</span></span>
* <span data-ttu-id="ed0ec-165">Die Schaltfläche "Held" oder "Miniaturansicht" und "Tippen" (außer aufrufen) werden auf der Vorschaukarte nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="ed0ec-165">The Hero or Thumbnail card button and tap actions, except invoke, are not supported in the preview card.</span></span>

<span data-ttu-id="ed0ec-166">Sie können eine Vorschau einer adaptiven Karte oder einer Office 365 Connector-Karte in der Ergebnisliste mit der Vorschaueigenschaft anzeigen.</span><span class="sxs-lookup"><span data-stu-id="ed0ec-166">You can display a preview of an Adaptive Card or Office 365 Connector card in the result list using its preview property.</span></span> <span data-ttu-id="ed0ec-167">Die Preview-Eigenschaft ist nicht erforderlich, wenn die Ergebnisse bereits Hero- oder Miniaturansichtskarten sind.</span><span class="sxs-lookup"><span data-stu-id="ed0ec-167">The preview property is not necessary if the results are already Hero or Thumbnail cards.</span></span> <span data-ttu-id="ed0ec-168">Wenn Sie die Vorschauanlage verwenden, muss es sich entweder um eine Hero- oder Miniaturansichtskarte geben.</span><span class="sxs-lookup"><span data-stu-id="ed0ec-168">If you use the preview attachment, it must be either a Hero or Thumbnail card.</span></span> <span data-ttu-id="ed0ec-169">Wenn keine Vorschaueigenschaft angegeben ist, schlägt die Vorschau der Karte fehl, und es wird nichts angezeigt.</span><span class="sxs-lookup"><span data-stu-id="ed0ec-169">If no preview property is specified, the preview of the card fails and nothing is displayed.</span></span>

### <a name="response-example"></a><span data-ttu-id="ed0ec-170">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="ed0ec-170">Response example</span></span>

# <a name="cnet"></a>[<span data-ttu-id="ed0ec-171">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="ed0ec-171">C#/.NET</span></span>](#tab/dotnet)

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

# <a name="typescriptnodejs"></a>[<span data-ttu-id="ed0ec-172">TypeScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="ed0ec-172">TypeScript/Node.js</span></span>](#tab/typescript)

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

# <a name="json"></a>[<span data-ttu-id="ed0ec-173">Json</span><span class="sxs-lookup"><span data-stu-id="ed0ec-173">JSON</span></span>](#tab/json)

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

## <a name="default-query"></a><span data-ttu-id="ed0ec-174">Standardabfrage</span><span class="sxs-lookup"><span data-stu-id="ed0ec-174">Default query</span></span>

<span data-ttu-id="ed0ec-175">Wenn Sie im Manifest auf festlegen, gibt Microsoft Teams eine Standardabfrage aus, wenn der Benutzer die `initialRun` `true` Messagingerweiterung zum ersten Mal öffnet. </span><span class="sxs-lookup"><span data-stu-id="ed0ec-175">If you set `initialRun` to `true` in the manifest, Microsoft Teams issues a **default** query when the user first opens the messaging extension.</span></span> <span data-ttu-id="ed0ec-176">Ihr Dienst kann auf diese Abfrage mit einer Reihe von vorab ausgefüllten Ergebnissen reagieren.</span><span class="sxs-lookup"><span data-stu-id="ed0ec-176">Your service can respond to this query with a set of pre-populated results.</span></span> <span data-ttu-id="ed0ec-177">Dies ist hilfreich, wenn ihr Suchbefehl eine Authentifizierung oder Konfiguration erfordert und zuletzt angezeigte Elemente, Favoriten oder andere Informationen, die nicht von benutzereingaben abhängig sind, angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="ed0ec-177">This is useful when your search command requires authentication or configuration, displaying recently viewed items, favorites, or any other information that is not dependent on user input.</span></span>

<span data-ttu-id="ed0ec-178">Die Standardabfrage hat dieselbe Struktur wie jede normale Benutzerabfrage, und das Feld wird wie im folgenden Objekt dargestellt auf `name` `initialRun` festgelegt und auf `value` `true` festgelegt:</span><span class="sxs-lookup"><span data-stu-id="ed0ec-178">The default query has the same structure as any regular user query, with the `name` field set to `initialRun` and `value` set to `true` as shown in the following object:</span></span>

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

## <a name="code-sample"></a><span data-ttu-id="ed0ec-179">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="ed0ec-179">Code sample</span></span>

| <span data-ttu-id="ed0ec-180">Beispielname</span><span class="sxs-lookup"><span data-stu-id="ed0ec-180">Sample Name</span></span>           | <span data-ttu-id="ed0ec-181">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ed0ec-181">Description</span></span> | <span data-ttu-id="ed0ec-182">.NET</span><span class="sxs-lookup"><span data-stu-id="ed0ec-182">.NET</span></span>    | <span data-ttu-id="ed0ec-183">Node.js</span><span class="sxs-lookup"><span data-stu-id="ed0ec-183">Node.js</span></span>   |   
|:---------------------|:--------------|:---------|:--------|
|<span data-ttu-id="ed0ec-184">Messagingerweiterungsaktion für Teams</span><span class="sxs-lookup"><span data-stu-id="ed0ec-184">Teams messaging extension action</span></span>| <span data-ttu-id="ed0ec-185">Beschreibt, wie Sie Aktionsbefehle definieren, Aufgabenmodul erstellen und auf Die Absendenaktion des Aufgabenmoduls reagieren.</span><span class="sxs-lookup"><span data-stu-id="ed0ec-185">Describes how to define action commands, create task module, and  respond to task module submit action.</span></span> |[<span data-ttu-id="ed0ec-186">View</span><span class="sxs-lookup"><span data-stu-id="ed0ec-186">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/51.teams-messaging-extensions-action)|[<span data-ttu-id="ed0ec-187">View</span><span class="sxs-lookup"><span data-stu-id="ed0ec-187">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/51.teams-messaging-extensions-action) | 
|<span data-ttu-id="ed0ec-188">Suche nach Messagingerweiterungen in Teams</span><span class="sxs-lookup"><span data-stu-id="ed0ec-188">Teams messaging extension search</span></span>   |  <span data-ttu-id="ed0ec-189">Beschreibt, wie Sie Suchbefehle definieren und auf Suchbefehle reagieren.</span><span class="sxs-lookup"><span data-stu-id="ed0ec-189">Describes how to define search commands and respond to searches.</span></span>        |[<span data-ttu-id="ed0ec-190">View</span><span class="sxs-lookup"><span data-stu-id="ed0ec-190">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/50.teams-messaging-extensions-search)|[<span data-ttu-id="ed0ec-191">View</span><span class="sxs-lookup"><span data-stu-id="ed0ec-191">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/50.teams-messaging-extensions-search)|

## <a name="see-also"></a><span data-ttu-id="ed0ec-192">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="ed0ec-192">See also</span></span>

- [<span data-ttu-id="ed0ec-193">Hinzufügen einer Konfiguration zu einer Messagingerweiterung</span><span class="sxs-lookup"><span data-stu-id="ed0ec-193">Add configuration to a messaging extension</span></span>](~/messaging-extensions/how-to/add-configuration-page.md)
 
## <a name="next-step"></a><span data-ttu-id="ed0ec-194">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="ed0ec-194">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ed0ec-195">Hinzufügen der Authentifizierung zu einer Messagingerweiterung</span><span class="sxs-lookup"><span data-stu-id="ed0ec-195">Add authentication to a messaging extension</span></span>](~/messaging-extensions/how-to/add-authentication.md)



