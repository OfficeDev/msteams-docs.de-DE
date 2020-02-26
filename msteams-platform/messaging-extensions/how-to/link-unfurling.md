---
title: Link-Entfaltung
author: clearab
description: Vorgehensweise durchführen einer Link Entfaltung mit Messaging Erweiterung in einer Microsoft Teams-app.
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: ccc23f06fbe759dc4c38dfc63dfa356d38352c27
ms.sourcegitcommit: 67c021fa20eb5ea70c059fcc35be1c19c6c97c95
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/26/2020
ms.locfileid: "42279774"
---
# <a name="link-unfurling"></a><span data-ttu-id="2a4f1-103">Link-Entfaltung</span><span class="sxs-lookup"><span data-stu-id="2a4f1-103">Link unfurling</span></span>

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

<span data-ttu-id="2a4f1-104">Mit dem Aufheben der Verknüpfung kann Ihre APP registrieren, um `invoke` eine Aktivität zu empfangen, wenn URLs mit einer bestimmten Domäne in den Bereich zum Verfassen von Nachrichten eingefügt werden.</span><span class="sxs-lookup"><span data-stu-id="2a4f1-104">With link unfurling your app can register to receive an `invoke` activity when URLs with a particular domain are pasted into the compose message area.</span></span> <span data-ttu-id="2a4f1-105">Der `invoke` enthält die vollständige URL, die in den Bereich zum Verfassen von Nachrichten eingefügt wurde, und Sie können mit einer Karte Antworten, die der Benutzer *entfalten*kann, indem zusätzliche Informationen oder Aktionen bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="2a4f1-105">The `invoke` will contain the full URL that was pasted into the compose message area, and you can respond with a card the user can *unfurl*, providing additional information or actions.</span></span> <span data-ttu-id="2a4f1-106">Dies funktioniert ähnlich wie ein [Suchbefehl](~/messaging-extensions/how-to/search-commands/define-search-command.md), wobei die URL als Suchbegriff dient.</span><span class="sxs-lookup"><span data-stu-id="2a4f1-106">This works very similarly to a [search command](~/messaging-extensions/how-to/search-commands/define-search-command.md), with the URL serving as the search term.</span></span>

<span data-ttu-id="2a4f1-107">Die Azure DevOps-Messaging Erweiterung verwendet Link-Entfaltung, um nach URLs zu suchen, die in den Nachrichtenbereich verfassen eingefügt werden, der auf ein Arbeitselement zeigt.</span><span class="sxs-lookup"><span data-stu-id="2a4f1-107">The Azure DevOps messaging extension uses link unfurling to look for URLs pasted into the compose message area pointing to a work item.</span></span> <span data-ttu-id="2a4f1-108">Im folgenden Screenshot wurde ein Benutzer in eine URL für eine Arbeitsaufgabe in Azure DevOps eingefügt, die von der Messaging Erweiterung in eine Karte aufgelöst wurde.</span><span class="sxs-lookup"><span data-stu-id="2a4f1-108">In the screenshot below, a user has pasted in a URL for a work item in Azure DevOps which the messaging extension has resolved into a card.</span></span>

![Beispiel für eine Link-Entfaltung](~/assets/images/compose-extensions/messagingextensions_linkunfurling.png)

## <a name="add-link-unfurling-to-your-app-manifest"></a><span data-ttu-id="2a4f1-110">Hinzufügen eines Links, der Ihrem App-Manifest entrollt</span><span class="sxs-lookup"><span data-stu-id="2a4f1-110">Add link unfurling to your app manifest</span></span>

<span data-ttu-id="2a4f1-111">Dazu fügen Sie dem `messageHandlers` `composeExtensions` Abschnitt Ihres App-Manifests JSON ein neues Array hinzu.</span><span class="sxs-lookup"><span data-stu-id="2a4f1-111">To do this you'll add a new `messageHandlers` array to the `composeExtensions` section of your app manifest JSON.</span></span> <span data-ttu-id="2a4f1-112">Sie können dies entweder mit Hilfe von App Studio oder manuell tun.</span><span class="sxs-lookup"><span data-stu-id="2a4f1-112">You can either do so with the help of App Studio, or manually.</span></span> <span data-ttu-id="2a4f1-113">Domänen Auflistungen können beispielsweise `*.example.com`Platzhalterzeichen enthalten.</span><span class="sxs-lookup"><span data-stu-id="2a4f1-113">Domain listings can include wildcards, for example `*.example.com`.</span></span> <span data-ttu-id="2a4f1-114">Dies entspricht genau einem Segment der Domäne. Wenn Sie eine Übereinstimmung `a.b.example.com` benötigen, `*.*.example.com`verwenden Sie.</span><span class="sxs-lookup"><span data-stu-id="2a4f1-114">This matches exactly one segment of the domain; if you need to match `a.b.example.com` then use `*.*.example.com`.</span></span>

### <a name="using-app-studio"></a><span data-ttu-id="2a4f1-115">Verwenden von App Studio</span><span class="sxs-lookup"><span data-stu-id="2a4f1-115">Using App Studio</span></span>

1. <span data-ttu-id="2a4f1-116">Laden Sie in App Studio auf der Registerkarte Manifest-Editor Ihr App-Manifest.</span><span class="sxs-lookup"><span data-stu-id="2a4f1-116">In App Studio, on the Manifest editor tab, load your app manifest.</span></span>
1. <span data-ttu-id="2a4f1-117">Fügen Sie auf der Seite **Messaging Erweiterung** im Abschnitt **Nachrichtenhandler** die Domäne hinzu, nach der Sie suchen möchten (siehe Screenshot unten).</span><span class="sxs-lookup"><span data-stu-id="2a4f1-117">On the **Messaging Extension** page, add the domain you want to look for in the **Message handlers** section as in the screenshot below.</span></span>

![Abschnitt "Nachrichtenhandler" in App Studio](~/assets/images/link-unfurling.png)

### <a name="manually"></a><span data-ttu-id="2a4f1-119">Manuell</span><span class="sxs-lookup"><span data-stu-id="2a4f1-119">Manually</span></span>

<span data-ttu-id="2a4f1-120">Damit Ihre Messaging Erweiterung auf diese Weise mit Links interagieren kann, müssen Sie zuerst das `messageHandlers` Array wie im folgenden Beispiel zu Ihrem App-Manifest hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="2a4f1-120">To enable your messaging extension to interact with links this way you'll first need to add the `messageHandlers` array to your app manifest as in the example below.</span></span> <span data-ttu-id="2a4f1-121">Dieses Beispiel ist nicht das vollständige Manifest, siehe [Manifest-Referenz](~/resources/schema/manifest-schema.md) für ein vollständiges Manifest-Beispiel.</span><span class="sxs-lookup"><span data-stu-id="2a4f1-121">This example is not the complete manifest, see [manifest reference](~/resources/schema/manifest-schema.md) for a complete manifest example.</span></span>

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

## <a name="handle-the-composeextensionquerylink-invoke"></a><span data-ttu-id="2a4f1-122">Behandeln des `composeExtension/queryLink` Aufrufs</span><span class="sxs-lookup"><span data-stu-id="2a4f1-122">Handle the `composeExtension/queryLink` invoke</span></span>

<span data-ttu-id="2a4f1-123">Nachdem Sie die Domäne zum Überwachen des App-Manifests hinzugefügt haben, müssen Sie den Webdienstcode aktualisieren, um die Invoke-Anforderung zu verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="2a4f1-123">Once you've added the domain to listen on to the app manifest, you'll need to update your web service code to handle the invoke request.</span></span> <span data-ttu-id="2a4f1-124">Verwenden Sie die URL, die Sie erhalten, um Ihren Dienst zu durchsuchen und eine Karten Antwort zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="2a4f1-124">Use the URL you receive to search your service and create a card response.</span></span> <span data-ttu-id="2a4f1-125">Wenn Sie mit mehr als einer Karte Antworten, wird nur der erste verwendet.</span><span class="sxs-lookup"><span data-stu-id="2a4f1-125">If you respond with more than one card, only the first will be used.</span></span>

<span data-ttu-id="2a4f1-126">Wir unterstützen die folgenden Kartentypen:</span><span class="sxs-lookup"><span data-stu-id="2a4f1-126">We support the following card types:</span></span>

* [<span data-ttu-id="2a4f1-127">Miniatur Ansichtskarte</span><span class="sxs-lookup"><span data-stu-id="2a4f1-127">Thumbnail card</span></span>](~/task-modules-and-cards/cards/cards-reference.md#thumbnail-card)
* [<span data-ttu-id="2a4f1-128">Hero Card</span><span class="sxs-lookup"><span data-stu-id="2a4f1-128">Hero card</span></span>](~/task-modules-and-cards/cards/cards-reference.md#hero-card)
* [<span data-ttu-id="2a4f1-129">Office 365-Anschluss Karte</span><span class="sxs-lookup"><span data-stu-id="2a4f1-129">Office 365 Connector card</span></span>](~/task-modules-and-cards/cards/cards-reference.md#office-365-connector-card)
* [<span data-ttu-id="2a4f1-130">Adaptive Karte</span><span class="sxs-lookup"><span data-stu-id="2a4f1-130">Adaptive Card</span></span>](~/task-modules-and-cards/cards/cards-reference.md#adaptive-card)

<span data-ttu-id="2a4f1-131">Eine Übersicht finden Sie unter [Was sind Karten](~/task-modules-and-cards/what-are-cards.md) .</span><span class="sxs-lookup"><span data-stu-id="2a4f1-131">See [What are cards](~/task-modules-and-cards/what-are-cards.md) for an overview.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="2a4f1-132">C#-/.net</span><span class="sxs-lookup"><span data-stu-id="2a4f1-132">C#/.NET</span></span>](#tab/dotnet)

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

# <a name="javascriptnodejs"></a>[<span data-ttu-id="2a4f1-133">JavaScript/Node. js</span><span class="sxs-lookup"><span data-stu-id="2a4f1-133">JavaScript/Node.js</span></span>](#tab/javascript)

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

# <a name="json"></a>[<span data-ttu-id="2a4f1-134">Json</span><span class="sxs-lookup"><span data-stu-id="2a4f1-134">JSON</span></span>](#tab/json)

<span data-ttu-id="2a4f1-135">Dies ist ein Beispiel für die `invoke` an Ihren bot gesendet.</span><span class="sxs-lookup"><span data-stu-id="2a4f1-135">This is an example of the `invoke` sent to your bot.</span></span>

```json
{
  "type": "invoke",
  "name": "composeExtension/queryLink",
  "value": {
    "url": "https://theurlsubmittedbyyouruser.trackeddomain.com/id/1234"
  }
}
```

<span data-ttu-id="2a4f1-136">Unten sehen Sie ein Beispiel für die Antwort.</span><span class="sxs-lookup"><span data-stu-id="2a4f1-136">An example of the response is shown below.</span></span>

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
