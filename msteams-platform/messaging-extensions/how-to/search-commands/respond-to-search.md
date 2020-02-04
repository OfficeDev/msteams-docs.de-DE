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
# <a name="respond-to-the-search-command"></a><span data-ttu-id="8d836-103">Antworten auf den Suchbefehl</span><span class="sxs-lookup"><span data-stu-id="8d836-103">Respond to the search command</span></span>

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

<span data-ttu-id="8d836-104">Der Webdienst erhält eine `composeExtension/query` Invoke-Nachricht, die ein `value` Objekt mit den Suchparametern enthält.</span><span class="sxs-lookup"><span data-stu-id="8d836-104">Your web service will receive a `composeExtension/query` invoke message that contains a `value` object with the search parameters.</span></span> <span data-ttu-id="8d836-105">Dieser Aufruf wird ausgelöst:</span><span class="sxs-lookup"><span data-stu-id="8d836-105">This invoke is triggered:</span></span>

* <span data-ttu-id="8d836-106">Als Zeichen werden in das Suchfeld eingegeben.</span><span class="sxs-lookup"><span data-stu-id="8d836-106">As characters are entered into the search box.</span></span>
* <span data-ttu-id="8d836-107">Wenn `initialRun` im App-Manifest auf true festgelegt ist, erhalten Sie die Invoke-Meldung, sobald der Suchbefehl aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="8d836-107">If `initialRun` is set to true in your app manifest, you'll receive the invoke message as soon as the search command is invoked.</span></span> <span data-ttu-id="8d836-108">Siehe [Standardabfrage](#default-query).</span><span class="sxs-lookup"><span data-stu-id="8d836-108">See [default query](#default-query).</span></span>

<span data-ttu-id="8d836-109">Die Anforderungsparameter selbst werden im- `value` Objekt in der Anforderung gefunden, die die folgenden Eigenschaften enthält:</span><span class="sxs-lookup"><span data-stu-id="8d836-109">The request parameters itself are found in the `value` object in the request, which includes the following properties:</span></span>

| <span data-ttu-id="8d836-110">Eigenschaftenname</span><span class="sxs-lookup"><span data-stu-id="8d836-110">Property name</span></span> | <span data-ttu-id="8d836-111">Zweck</span><span class="sxs-lookup"><span data-stu-id="8d836-111">Purpose</span></span> |
|---|---|
| `commandId` | <span data-ttu-id="8d836-112">Der Name des vom Benutzer aufgerufenen Befehls, der einem der im App-Manifest deklarierten Befehle entspricht.</span><span class="sxs-lookup"><span data-stu-id="8d836-112">The name of the command invoked by the user, matching one of the commands declared in the app manifest.</span></span> |
| `parameters` | <span data-ttu-id="8d836-113">Array von Parametern.</span><span class="sxs-lookup"><span data-stu-id="8d836-113">Array of parameters.</span></span> <span data-ttu-id="8d836-114">Jedes Parameter-Objekt enthält den Namen des Parameters sowie den vom Benutzer bereitgestellten Parameterwert.</span><span class="sxs-lookup"><span data-stu-id="8d836-114">Each parameter object contains the parameter name, along with the parameter value provided by the user.</span></span> |
| `queryOptions` | <span data-ttu-id="8d836-115">Paginierung Parameter:</span><span class="sxs-lookup"><span data-stu-id="8d836-115">Pagination parameters:</span></span> <br><span data-ttu-id="8d836-116">`skip`: Skip count für diese Abfrage</span><span class="sxs-lookup"><span data-stu-id="8d836-116">`skip`: skip count for this query</span></span> <br><span data-ttu-id="8d836-117">`count`: Anzahl der zurückzugebenden Elemente</span><span class="sxs-lookup"><span data-stu-id="8d836-117">`count`: number of elements to return</span></span> |

# <a name="cnettabdotnet"></a>[<span data-ttu-id="8d836-118">C#-/.net</span><span class="sxs-lookup"><span data-stu-id="8d836-118">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task<MessagingExtensionResponse> OnTeamsMessagingExtensionQueryAsync(ITurnContext<IInvokeActivity> turnContext, MessagingExtensionQuery query, CancellationToken cancellationToken)
{
  //code to handle the query
}
```

# <a name="typescriptnodejstabtypescript"></a>[<span data-ttu-id="8d836-119">Manuskript/Node. js</span><span class="sxs-lookup"><span data-stu-id="8d836-119">TypeScript/Node.js</span></span>](#tab/typescript)

```typescript
class TeamsMessagingExtensionsSearch extends TeamsActivityHandler {
    async handleTeamsMessagingExtensionQuery(context, query) {
  //code to handle the query
    }
}
```

# <a name="jsontabjson"></a>[<span data-ttu-id="8d836-120">Json</span><span class="sxs-lookup"><span data-stu-id="8d836-120">JSON</span></span>](#tab/json)

<span data-ttu-id="8d836-121">Die folgende JSON wird verkürzt, um die relevantesten Abschnitte hervorzuheben.</span><span class="sxs-lookup"><span data-stu-id="8d836-121">The JSON below is shortened to highlight the most relevant sections.</span></span>

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

## <a name="respond-to-user-requests"></a><span data-ttu-id="8d836-122">Reagieren auf Benutzeranforderungen</span><span class="sxs-lookup"><span data-stu-id="8d836-122">Respond to user requests</span></span>

<span data-ttu-id="8d836-123">Wenn der Benutzer eine Abfrage ausführt, gibt Microsoft Teams eine synchrone http-Anforderung an Ihren Dienst aus.</span><span class="sxs-lookup"><span data-stu-id="8d836-123">When the user performs a query, Microsoft Teams issues a synchronous HTTP request to your service.</span></span> <span data-ttu-id="8d836-124">An diesem Zeitpunkt hat der Code 5 Sekunden, um eine HTTP-Antwort auf die Anforderung bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="8d836-124">At that point, your code has 5 seconds to provide an HTTP response to the request.</span></span> <span data-ttu-id="8d836-125">Während dieser Zeit kann der Dienst zusätzliche Suchvorgänge durchführen oder eine andere Geschäftslogik, die für die Zustellung der Anforderung benötigt wird.</span><span class="sxs-lookup"><span data-stu-id="8d836-125">During this time, your service can perform additional lookup, or any other business logic needed to serve the request.</span></span>

<span data-ttu-id="8d836-126">Ihr Dienst sollte mit den Ergebnissen Antworten, die mit der Benutzerabfrage übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="8d836-126">Your service should respond with the results matching the user query.</span></span> <span data-ttu-id="8d836-127">Die Antwort muss einen HTTP-Statuscode `200 OK` und ein gültiges Application/JSON-Objekt mit folgendem Text angeben:</span><span class="sxs-lookup"><span data-stu-id="8d836-127">The response must indicate an HTTP status code of `200 OK` and a valid application/json object with the following body:</span></span>

|<span data-ttu-id="8d836-128">Eigenschaftenname</span><span class="sxs-lookup"><span data-stu-id="8d836-128">Property name</span></span>|<span data-ttu-id="8d836-129">Zweck</span><span class="sxs-lookup"><span data-stu-id="8d836-129">Purpose</span></span>|
|---|---|
|`composeExtension`|<span data-ttu-id="8d836-130">Antwortumschlag auf oberster Ebene.</span><span class="sxs-lookup"><span data-stu-id="8d836-130">Top-level response envelope.</span></span>|
|`composeExtension.type`|<span data-ttu-id="8d836-131">Typ der Antwort.</span><span class="sxs-lookup"><span data-stu-id="8d836-131">Type of response.</span></span> <span data-ttu-id="8d836-132">Die folgenden Typen werden unterstützt:</span><span class="sxs-lookup"><span data-stu-id="8d836-132">The following types are supported:</span></span> <br><span data-ttu-id="8d836-133">`result`: zeigt eine Liste der Suchergebnisse an.</span><span class="sxs-lookup"><span data-stu-id="8d836-133">`result`: displays a list of search results</span></span> <br><span data-ttu-id="8d836-134">`auth`: der Benutzer wird aufgefordert, sich zu authentifizieren.</span><span class="sxs-lookup"><span data-stu-id="8d836-134">`auth`: asks the user to authenticate</span></span> <br><span data-ttu-id="8d836-135">`config`: der Benutzer wird aufgefordert, die Messaging Erweiterung einzurichten.</span><span class="sxs-lookup"><span data-stu-id="8d836-135">`config`: asks the user to set up the messaging extension</span></span> <br><span data-ttu-id="8d836-136">`message`: zeigt eine nur-Text-Nachricht an.</span><span class="sxs-lookup"><span data-stu-id="8d836-136">`message`: displays a plain text message</span></span> |
|`composeExtension.attachmentLayout`|<span data-ttu-id="8d836-137">Gibt das Layout der Anlagen an.</span><span class="sxs-lookup"><span data-stu-id="8d836-137">Specifies the layout of the attachments.</span></span> <span data-ttu-id="8d836-138">Wird für Antworten vom Typ `result`verwendet.</span><span class="sxs-lookup"><span data-stu-id="8d836-138">Used for responses of type `result`.</span></span> <br><span data-ttu-id="8d836-139">Derzeit werden die folgenden Typen unterstützt:</span><span class="sxs-lookup"><span data-stu-id="8d836-139">Currently the following types are supported:</span></span> <br><span data-ttu-id="8d836-140">`list`: eine Liste von Kartenobjekten, die Miniaturansichten, Titel und Textfelder enthalten</span><span class="sxs-lookup"><span data-stu-id="8d836-140">`list`: a list of card objects containing thumbnail, title, and text fields</span></span> <br><span data-ttu-id="8d836-141">`grid`: ein Raster von Miniaturbildern</span><span class="sxs-lookup"><span data-stu-id="8d836-141">`grid`: a grid of thumbnail images</span></span> |
|`composeExtension.attachments`|<span data-ttu-id="8d836-142">Array gültiger Attachment-Objekte.</span><span class="sxs-lookup"><span data-stu-id="8d836-142">Array of valid attachment objects.</span></span> <span data-ttu-id="8d836-143">Wird für Antworten vom Typ `result`verwendet.</span><span class="sxs-lookup"><span data-stu-id="8d836-143">Used for responses of type `result`.</span></span> <br><span data-ttu-id="8d836-144">Derzeit werden die folgenden Typen unterstützt:</span><span class="sxs-lookup"><span data-stu-id="8d836-144">Currently the following types are supported:</span></span> <br>`application/vnd.microsoft.card.thumbnail` <br>`application/vnd.microsoft.card.hero` <br>`application/vnd.microsoft.teams.card.o365connector` <br>`application/vnd.microsoft.card.adaptive`|
|`composeExtension.suggestedActions`|<span data-ttu-id="8d836-145">Vorgeschlagene Aktionen.</span><span class="sxs-lookup"><span data-stu-id="8d836-145">Suggested actions.</span></span> <span data-ttu-id="8d836-146">Wird für Antworten vom Typ `auth` oder `config`verwendet.</span><span class="sxs-lookup"><span data-stu-id="8d836-146">Used for responses of type `auth` or `config`.</span></span> |
|`composeExtension.text`|<span data-ttu-id="8d836-147">Anzuzeigende Meldung.</span><span class="sxs-lookup"><span data-stu-id="8d836-147">Message to display.</span></span> <span data-ttu-id="8d836-148">Wird für Antworten vom Typ `message`verwendet.</span><span class="sxs-lookup"><span data-stu-id="8d836-148">Used for responses of type `message`.</span></span> |

### <a name="response-card-types-and-previews"></a><span data-ttu-id="8d836-149">Antwortkarten Typen und-Vorschauen</span><span class="sxs-lookup"><span data-stu-id="8d836-149">Response card types and previews</span></span>

<span data-ttu-id="8d836-150">Wir unterstützen die folgenden Anlagentypen:</span><span class="sxs-lookup"><span data-stu-id="8d836-150">We support the following attachment types:</span></span>

* [<span data-ttu-id="8d836-151">Miniatur Ansichtskarte</span><span class="sxs-lookup"><span data-stu-id="8d836-151">Thumbnail card</span></span>](~/task-modules-and-cards/cards/cards-reference.md#thumbnail-card)
* [<span data-ttu-id="8d836-152">Hero Card</span><span class="sxs-lookup"><span data-stu-id="8d836-152">Hero card</span></span>](~/task-modules-and-cards/cards/cards-reference.md#hero-card)
* [<span data-ttu-id="8d836-153">Office 365-Anschluss Karte</span><span class="sxs-lookup"><span data-stu-id="8d836-153">Office 365 Connector card</span></span>](~/task-modules-and-cards/cards/cards-reference.md#office-365-connector-card)
* [<span data-ttu-id="8d836-154">Adaptive Karte</span><span class="sxs-lookup"><span data-stu-id="8d836-154">Adaptive Card</span></span>](~/task-modules-and-cards/cards/cards-reference.md#adaptive-card)

<span data-ttu-id="8d836-155">Eine Übersicht finden Sie unter [Was sind Karten](~/task-modules-and-cards/what-are-cards.md) .</span><span class="sxs-lookup"><span data-stu-id="8d836-155">See [What are cards](~/task-modules-and-cards/what-are-cards.md) for an overview.</span></span>

<span data-ttu-id="8d836-156">Weitere Informationen zur Verwendung der Miniaturansicht-und Hero-Kartentypen finden Sie unter [Add Cards and Card Actions](~/task-modules-and-cards/cards/cards-actions.md).</span><span class="sxs-lookup"><span data-stu-id="8d836-156">To learn how to use the thumbnail and hero card types, see [Add cards and card actions](~/task-modules-and-cards/cards/cards-actions.md).</span></span>

<span data-ttu-id="8d836-157">Weitere Informationen zur Office 365-Verbindungskarte finden Sie unter [using Office 365 Connector Cards](~/task-modules-and-cards/cards/cards-reference.md#office-365-connector-card).</span><span class="sxs-lookup"><span data-stu-id="8d836-157">For additional documentation regarding the Office 365 Connector card, see [Using Office 365 Connector cards](~/task-modules-and-cards/cards/cards-reference.md#office-365-connector-card).</span></span>

<span data-ttu-id="8d836-158">Die Ergebnisliste wird auf der Microsoft Teams-Benutzeroberfläche mit einer Vorschau der einzelnen Elemente angezeigt.</span><span class="sxs-lookup"><span data-stu-id="8d836-158">The result list is displayed in the Microsoft Teams UI with a preview of each item.</span></span> <span data-ttu-id="8d836-159">Die Vorschau wird auf eine von zwei Arten generiert:</span><span class="sxs-lookup"><span data-stu-id="8d836-159">The preview is generated in one of two ways:</span></span>

* <span data-ttu-id="8d836-160">Verwenden der `preview` -Eigenschaft innerhalb `attachment` des-Objekts.</span><span class="sxs-lookup"><span data-stu-id="8d836-160">Using the `preview` property within the `attachment` object.</span></span> <span data-ttu-id="8d836-161">Die `preview` Anlage kann nur eine Hero-oder Thumbnail-Karte sein.</span><span class="sxs-lookup"><span data-stu-id="8d836-161">The `preview` attachment can only be a Hero or Thumbnail card.</span></span>
* <span data-ttu-id="8d836-162">Extrahiert aus den Eigenschaften `title`Basic `text`, und `image` und der Anlage.</span><span class="sxs-lookup"><span data-stu-id="8d836-162">Extracted from the basic `title`, `text`, and `image` properties of the attachment.</span></span> <span data-ttu-id="8d836-163">Diese werden nur verwendet, wenn `preview` die Eigenschaft nicht festgelegt ist und diese Eigenschaften verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="8d836-163">These are used only if the `preview` property is not set and these properties are available.</span></span>

<span data-ttu-id="8d836-164">Sie können eine Vorschau einer adaptiven Karte oder Office 365-connectorkarte in der Ergebnisliste einfach über die Vorschau-Eigenschaft anzeigen.</span><span class="sxs-lookup"><span data-stu-id="8d836-164">You can display a preview of an Adaptive Card or Office 365 Connector card in the result list simply by its preview property.</span></span> <span data-ttu-id="8d836-165">Dies ist nicht erforderlich, wenn die Ergebnisse bereits Hero-oder Thumbnail-Karten sind.</span><span class="sxs-lookup"><span data-stu-id="8d836-165">This is not necessary if the results are already hero or thumbnail cards.</span></span> <span data-ttu-id="8d836-166">Wenn Sie die Vorschau Anlage verwenden, muss es sich entweder um eine Hero-oder eine Miniatur Ansichtskarte handeln.</span><span class="sxs-lookup"><span data-stu-id="8d836-166">If you use the preview attachment, it must be either a Hero or Thumbnail card.</span></span> <span data-ttu-id="8d836-167">Wenn keine Preview-Eigenschaft angegeben wird, schlägt die Vorschau der Karte fehl, und es wird nichts angezeigt.</span><span class="sxs-lookup"><span data-stu-id="8d836-167">If no preview property is specified, the preview of the card will fail and nothing will be displayed.</span></span>

### <a name="response-example"></a><span data-ttu-id="8d836-168">Anforderungsbeispiel</span><span class="sxs-lookup"><span data-stu-id="8d836-168">Response example</span></span>

# <a name="cnettabdotnet"></a>[<span data-ttu-id="8d836-169">C#-/.net</span><span class="sxs-lookup"><span data-stu-id="8d836-169">C#/.NET</span></span>](#tab/dotnet)

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

# <a name="typescriptnodejstabtypescript"></a>[<span data-ttu-id="8d836-170">Manuskript/Node. js</span><span class="sxs-lookup"><span data-stu-id="8d836-170">TypeScript/Node.js</span></span>](#tab/typescript)

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

# <a name="jsontabjson"></a>[<span data-ttu-id="8d836-171">Json</span><span class="sxs-lookup"><span data-stu-id="8d836-171">JSON</span></span>](#tab/json)

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

## <a name="default-query"></a><span data-ttu-id="8d836-172">Standardabfrage</span><span class="sxs-lookup"><span data-stu-id="8d836-172">Default query</span></span>

<span data-ttu-id="8d836-173">Wenn Sie im `initialRun` Manifest `true` auf festlegen, gibt Microsoft Teams eine "Standard"-Abfrage aus, wenn der Benutzer die Messaging Erweiterung zum ersten Mal öffnet.</span><span class="sxs-lookup"><span data-stu-id="8d836-173">If you set `initialRun` to `true` in the manifest, Microsoft Teams issues a "default" query when the user first opens the messaging extension.</span></span> <span data-ttu-id="8d836-174">Ihr Dienst kann auf diese Abfrage mit einer Reihe vorab aufgefüllter Ergebnisse Antworten.</span><span class="sxs-lookup"><span data-stu-id="8d836-174">Your service can respond to this query with a set of pre-populated results.</span></span> <span data-ttu-id="8d836-175">Dies kann hilfreich sein, wenn Ihr Suchbefehl Authentifizierung oder Konfiguration erfordert, wobei zuletzt angezeigte Elemente, Favoriten oder andere Informationen angezeigt werden, die nicht von der Benutzereingabe abhängig sind.</span><span class="sxs-lookup"><span data-stu-id="8d836-175">This can be useful when your search command requires authentication or configuration, displaying recently viewed items, favorites, or any other information that is not dependent on user input.</span></span>

<span data-ttu-id="8d836-176">Die Standard `name` Abfrage hat dieselbe Struktur wie jede reguläre Benutzerabfrage, wobei das Feld auf `initialRun` festgelegt und `value` auf `true` wie in dem unten stehenden Objekt festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="8d836-176">The default query has the same structure as any regular user query, with the `name` field set to `initialRun` and `value` set to `true` as in the object below.</span></span>

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

## <a name="next-steps"></a><span data-ttu-id="8d836-177">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="8d836-177">Next Steps</span></span>

<span data-ttu-id="8d836-178">Hinzufügen von Authentifizierung und/oder Konfiguration</span><span class="sxs-lookup"><span data-stu-id="8d836-178">Add authentication and/or configuration</span></span>

* [<span data-ttu-id="8d836-179">Hinzufügen einer Authentifizierung zu einer Messaging Erweiterung</span><span class="sxs-lookup"><span data-stu-id="8d836-179">Add authentication to a messaging extension</span></span>](~/messaging-extensions/how-to/add-authentication.md)
* [<span data-ttu-id="8d836-180">Hinzufügen einer Konfiguration zu einer Messaging Erweiterung</span><span class="sxs-lookup"><span data-stu-id="8d836-180">Add configuration to a messaging extension</span></span>](~/messaging-extensions/how-to/add-configuration-page.md)

<span data-ttu-id="8d836-181">Bereitstellen der Konfiguration</span><span class="sxs-lookup"><span data-stu-id="8d836-181">Deploy configuration</span></span>

* [<span data-ttu-id="8d836-182">Bereitstellen des App-Pakets</span><span class="sxs-lookup"><span data-stu-id="8d836-182">Deploy your app package</span></span>](~/concepts/deploy-and-publish/apps-upload.md)

[!include[messaging-extension-learn-more](~/includes/messaging-extensions/learn-more.md)]
