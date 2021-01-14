---
title: Entfalten von Links
author: clearab
description: So führen Sie in einer Microsoft Teams-App das Aufblinken von Links mit der Messagingerweiterung aus.
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: 0d488638e63b8ec78bfa5bed8cf6f4f037883fb1
ms.sourcegitcommit: bf61ae5ad2afa4efdb0311158184d0cbb9c40174
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2021
ms.locfileid: "49845637"
---
# <a name="link-unfurling"></a><span data-ttu-id="f4289-103">Entfalten von Links</span><span class="sxs-lookup"><span data-stu-id="f4289-103">Link unfurling</span></span>

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

> [!NOTE]
> <span data-ttu-id="f4289-104">Derzeit wird das Entf?nden von Links auf mobilen Clients nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="f4289-104">Currently, Link unfurling is not supported on Mobile clients.</span></span>

<span data-ttu-id="f4289-105">Mit der Verbreitung von Links kann Ihre App sich registrieren, um eine `invoke`-Aktivität zu empfangen, wenn URLs mit einer bestimmten Domäne in den Bereich zum Verfassen von Nachrichten eingefügt werden.</span><span class="sxs-lookup"><span data-stu-id="f4289-105">With link unfurling your app can register to receive an `invoke` activity when URLs with a particular domain are pasted into the compose message area.</span></span> <span data-ttu-id="f4289-106">Die enthält die vollständige URL, die in den Bereich zum Verfassen von Nachrichten eingegeben wurde, und Sie können mit einer Karte antworten, die der Benutzer ausf?nnen kann, um zusätzliche Informationen oder `invoke` Aktionen zur Verfügung zu stellen. </span><span class="sxs-lookup"><span data-stu-id="f4289-106">The `invoke` will contain the full URL that was pasted into the compose message area, and you can respond with a card the user can *unfurl*, providing additional information or actions.</span></span> <span data-ttu-id="f4289-107">Dies funktioniert ähnlich wie bei einem [Suchbefehl,](~/messaging-extensions/how-to/search-commands/define-search-command.md)bei dem die URL als Suchbegriff dient.</span><span class="sxs-lookup"><span data-stu-id="f4289-107">This works very similarly to a [search command](~/messaging-extensions/how-to/search-commands/define-search-command.md), with the URL serving as the search term.</span></span>

<span data-ttu-id="f4289-108">Die Azure DevOps-Messaging-Erweiterung verwendet das Wiederverteilen von Links, um nach URLs zu suchen, die in den Bereich zum Verfassen von Nachrichten, die auf eine Arbeitsaufgabe zeigen, eingef?ndert sind.</span><span class="sxs-lookup"><span data-stu-id="f4289-108">The Azure DevOps messaging extension uses link unfurling to look for URLs pasted into the compose message area pointing to a work item.</span></span> <span data-ttu-id="f4289-109">Im folgenden Screenshot hat ein Benutzer eine URL für eine Arbeitsaufgabe in Azure DevOps eingegeben, die die Messagingerweiterung in eine Karte aufgelöst hat.</span><span class="sxs-lookup"><span data-stu-id="f4289-109">In the screenshot below, a user has pasted in a URL for a work item in Azure DevOps which the messaging extension has resolved into a card.</span></span>

![Beispiel für die Verknüpfungsentbündelung](~/assets/images/compose-extensions/messagingextensions_linkunfurling.png)

## <a name="add-link-unfurling-to-your-app-manifest"></a><span data-ttu-id="f4289-111">Hinzufügen der Linkentleierung zu Ihrem App-Manifest</span><span class="sxs-lookup"><span data-stu-id="f4289-111">Add link unfurling to your app manifest</span></span>

 <span data-ttu-id="f4289-112">Fügen Sie zum Hinzufügen von Links zum Entfingen ihres App-Manifests dem Abschnitt ihres `messageHandlers` `composeExtensions` App-Manifest-JSON ein neues Array hinzu.</span><span class="sxs-lookup"><span data-stu-id="f4289-112">To add link unfurling to your app manifest add a new `messageHandlers` array to the `composeExtensions` section of your app manifest JSON.</span></span> <span data-ttu-id="f4289-113">Sie können das Array mithilfe von App Studio oder manuell hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="f4289-113">You can add the array either with the help of App Studio or manually.</span></span> <span data-ttu-id="f4289-114">Domänenauflistungen können Platzhalter enthalten, z. B. `*.example.com` .</span><span class="sxs-lookup"><span data-stu-id="f4289-114">Domain listings can include wildcards, for example `*.example.com`.</span></span> <span data-ttu-id="f4289-115">Dies entspricht genau einem Segment der Domäne. Wenn Sie übereinstimmen müssen, `a.b.example.com` verwenden Sie `*.*.example.com` .</span><span class="sxs-lookup"><span data-stu-id="f4289-115">This matches exactly one segment of the domain; if you need to match `a.b.example.com` then use `*.*.example.com`.</span></span>

> [!NOTE]
> <span data-ttu-id="f4289-116">Fügen Sie keine Domänen hinzu, die sich außerhalb Ihres Steuerelements befinden, entweder direkt oder über Platzhalter.</span><span class="sxs-lookup"><span data-stu-id="f4289-116">Do not add domains that are outside your control, either directly or through wildcards.</span></span> <span data-ttu-id="f4289-117">Beispielsweise ist yourapp.onmicrosoft.com gültig, \*.onmicrosoft.com ist jedoch ungültig.</span><span class="sxs-lookup"><span data-stu-id="f4289-117">For example, yourapp.onmicrosoft.com is valid, but \*.onmicrosoft.com is not valid.</span></span> <span data-ttu-id="f4289-118">Außerdem sind Domänen auf oberster Ebene unzulässig.</span><span class="sxs-lookup"><span data-stu-id="f4289-118">Also, the top-level domains are prohibited.</span></span> <span data-ttu-id="f4289-119">Beispiel: \*.com, \*.org.</span><span class="sxs-lookup"><span data-stu-id="f4289-119">For example, \*.com, \*.org.</span></span>

### <a name="using-app-studio"></a><span data-ttu-id="f4289-120">Verwenden von App Studio</span><span class="sxs-lookup"><span data-stu-id="f4289-120">Using App Studio</span></span>

1. <span data-ttu-id="f4289-121">Laden Sie in App Studio auf der Registerkarte "Manifest-Editor" Ihr App-Manifest.</span><span class="sxs-lookup"><span data-stu-id="f4289-121">In App Studio, on the Manifest editor tab, load your app manifest.</span></span>
1. <span data-ttu-id="f4289-122">Fügen Sie **auf der Seite "Messagingerweiterung"** die Domäne hinzu, nach der Sie suchen möchten, im Abschnitt **"Nachrichtenhandler",** wie im folgenden Screenshot dargestellt.</span><span class="sxs-lookup"><span data-stu-id="f4289-122">On the **Messaging Extension** page, add the domain you want to look for in the **Message handlers** section as in the screenshot below.</span></span>

![Abschnitt "Message Handlers" in App Studio](~/assets/images/link-unfurling.png)

### <a name="manually"></a><span data-ttu-id="f4289-124">Manuell</span><span class="sxs-lookup"><span data-stu-id="f4289-124">Manually</span></span>

<span data-ttu-id="f4289-125">Damit Ihre Messagingerweiterung auf diese Weise mit Links interagieren kann, müssen Sie zuerst das Array zu Ihrem App-Manifest hinzufügen, wie im folgenden `messageHandlers` Beispiel gezeigt.</span><span class="sxs-lookup"><span data-stu-id="f4289-125">To enable your messaging extension to interact with links this way you'll first need to add the `messageHandlers` array to your app manifest as in the example below.</span></span> <span data-ttu-id="f4289-126">Dieses Beispiel ist nicht das vollständige Manifest, siehe [Manifestreferenz](~/resources/schema/manifest-schema.md) für ein vollständiges Manifestbeispiel.</span><span class="sxs-lookup"><span data-stu-id="f4289-126">This example is not the complete manifest, see [manifest reference](~/resources/schema/manifest-schema.md) for a complete manifest example.</span></span>

```json
...
"composeExtensions": [
  {
    "botId": "abc123456-ab12-ab12-ab12-abcdef123456",
    "messageHandlers": [
      {
        "type": "link",
        "value": {
          "domains": [
            "*.trackeddomain.com"
          ]
        }
      }
    ]
  }
],
...
```

## <a name="handle-the-composeextensionquerylink-invoke"></a><span data-ttu-id="f4289-127">Behandeln des `composeExtension/queryLink` Aufrufs</span><span class="sxs-lookup"><span data-stu-id="f4289-127">Handle the `composeExtension/queryLink` invoke</span></span>

<span data-ttu-id="f4289-128">Nachdem Sie die Domäne zum Abhören des App-Manifests hinzugefügt haben, müssen Sie Ihren Webdienstcode aktualisieren, um die Aufrufanforderung zu verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="f4289-128">Once you've added the domain to listen on to the app manifest, you'll need to update your web service code to handle the invoke request.</span></span> <span data-ttu-id="f4289-129">Verwenden Sie die URL, die Sie erhalten, um Ihren Dienst zu durchsuchen und eine Kartenantwort zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="f4289-129">Use the URL you receive to search your service and create a card response.</span></span> <span data-ttu-id="f4289-130">Wenn Sie mit mehr als einer Karte antworten, wird nur die erste Karte verwendet.</span><span class="sxs-lookup"><span data-stu-id="f4289-130">If you respond with more than one card, only the first will be used.</span></span>

<span data-ttu-id="f4289-131">Wir unterstützen die folgenden Kartentypen:</span><span class="sxs-lookup"><span data-stu-id="f4289-131">We support the following card types:</span></span>

* [<span data-ttu-id="f4289-132">Miniaturansichtkarte</span><span class="sxs-lookup"><span data-stu-id="f4289-132">Thumbnail card</span></span>](~/task-modules-and-cards/cards/cards-reference.md#thumbnail-card)
* [<span data-ttu-id="f4289-133">Herokarte</span><span class="sxs-lookup"><span data-stu-id="f4289-133">Hero card</span></span>](~/task-modules-and-cards/cards/cards-reference.md#hero-card)
* [<span data-ttu-id="f4289-134">Office 365-Connectorkarte</span><span class="sxs-lookup"><span data-stu-id="f4289-134">Office 365 Connector card</span></span>](~/task-modules-and-cards/cards/cards-reference.md#office-365-connector-card)
* [<span data-ttu-id="f4289-135">Adaptive Karte</span><span class="sxs-lookup"><span data-stu-id="f4289-135">Adaptive Card</span></span>](~/task-modules-and-cards/cards/cards-reference.md#adaptive-card)

<span data-ttu-id="f4289-136">Eine [Übersicht finden Sie unter "Was sind](~/task-modules-and-cards/what-are-cards.md) Karten".</span><span class="sxs-lookup"><span data-stu-id="f4289-136">See [What are cards](~/task-modules-and-cards/what-are-cards.md) for an overview.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="f4289-137">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="f4289-137">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task<MessagingExtensionResponse> OnTeamsAppBasedLinkQueryAsync(ITurnContext<IInvokeActivity> turnContext, AppBasedLinkQuery query, CancellationToken cancellationToken)
{
    //You'll use the query.link value to search your service and create a card response
    var card = new HeroCard
    {
        Title = "Hero Card",
        Text = query.Url,
        Images = new List<CardImage> { new CardImage("https://raw.githubusercontent.com/microsoft/botframework-sdk/master/icon.png") },
    };

    var attachments = new MessagingExtensionAttachment(HeroCard.ContentType, null, card);
    var result = new MessagingExtensionResult(AttachmentLayoutTypes.List, "result", new[] { attachments }, null, "test unfurl");

    return new MessagingExtensionResponse(result);
}
```

# <a name="javascriptnodejs"></a>[<span data-ttu-id="f4289-138">JavaScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="f4289-138">JavaScript/Node.js</span></span>](#tab/javascript)

```javascript
class TeamsLinkUnfurlingBot extends TeamsActivityHandler {
  handleTeamsAppBasedLinkQuery(context, query) {
    const attachment = CardFactory.thumbnailCard('Thumbnail Card',
      query.url,
      ['https://raw.githubusercontent.com/microsoft/botframework-sdk/master/icon.png']);

    const result = {
      attachmentLayout: 'list',
      type: 'result',
      attachments: [attachment]
    };

    const response = {
      composeExtension: result
    };
    return response;
  }
}
```

# <a name="json"></a>[<span data-ttu-id="f4289-139">Json</span><span class="sxs-lookup"><span data-stu-id="f4289-139">JSON</span></span>](#tab/json)

<span data-ttu-id="f4289-140">Dies ist ein Beispiel für das an `invoke` Ihren Bot gesendete.</span><span class="sxs-lookup"><span data-stu-id="f4289-140">This is an example of the `invoke` sent to your bot.</span></span>

```json
{
  "type": "invoke",
  "name": "composeExtension/queryLink",
  "value": {
    "url": "https://theurlsubmittedbyyouruser.trackeddomain.com/id/1234"
  }
}
```

<span data-ttu-id="f4289-141">Ein Beispiel für die Antwort ist unten dargestellt.</span><span class="sxs-lookup"><span data-stu-id="f4289-141">An example of the response is shown below.</span></span>

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
        }
      }
    ]
  }
}
```

* * *
