---
title: Entfalten von Links
author: clearab
description: Ausführen der Verknüpfungsentschnappung mit der Messagingerweiterung in einer Microsoft Teams App.
localization_priority: Normal
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: 405b320b887300837d51332a9548ff60aff450d0
ms.sourcegitcommit: e1fe46c574cec378319814f8213209ad3063b2c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2021
ms.locfileid: "52630684"
---
# <a name="link-unfurling"></a><span data-ttu-id="f5ede-103">Entfalten von Links</span><span class="sxs-lookup"><span data-stu-id="f5ede-103">Link unfurling</span></span>

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

<span data-ttu-id="f5ede-104">In diesem Dokument erfahren Sie, wie Sie ihrem App-Manifest mithilfe von App Studio und manuell link unfurling hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="f5ede-104">This document guides you on how to add link unfurling to your app manifest using App studio and manually.</span></span> <span data-ttu-id="f5ede-105">Mit der Verbreitung von Links kann Ihre App sich registrieren, um eine `invoke`-Aktivität zu empfangen, wenn URLs mit einer bestimmten Domäne in den Bereich zum Verfassen von Nachrichten eingefügt werden.</span><span class="sxs-lookup"><span data-stu-id="f5ede-105">With link unfurling your app can register to receive an `invoke` activity when URLs with a particular domain are pasted into the compose message area.</span></span> <span data-ttu-id="f5ede-106">Der enthält die vollständige URL, die in den Bereich "Verfassen von Nachrichten" eingegeben wurde, und Sie können mit einer Karte antworten, die der Benutzer entfurlen kann, und zusätzliche Informationen oder `invoke` Aktionen bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="f5ede-106">The `invoke` contains the full URL that was pasted into the compose message area, and you can respond with a card that the user can unfurl, providing additional information or actions.</span></span> <span data-ttu-id="f5ede-107">Dies funktioniert ähnlich wie bei einem Suchbefehl, bei dem die URL als Suchbegriff dient.</span><span class="sxs-lookup"><span data-stu-id="f5ede-107">This works similar to a search command with the URL serving as the search term.</span></span>

> [!NOTE]
> <span data-ttu-id="f5ede-108">Derzeit wird die Verknüpfungsentfurling auf mobilen Clients nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="f5ede-108">Currently, link unfurling is not supported on Mobile clients.</span></span>

<span data-ttu-id="f5ede-109">Die Azure DevOps messaging-Erweiterung verwendet die Verknüpfungsentwennung, um nach URLs zu suchen, die in den Bereich verfassen von Nachrichten, die auf eine Arbeitsaufgabe zeigen, eingefügt werden.</span><span class="sxs-lookup"><span data-stu-id="f5ede-109">The Azure DevOps messaging extension uses link unfurling to look for URLs pasted into the compose message area pointing to a work item.</span></span> <span data-ttu-id="f5ede-110">In der folgenden Abbildung hat ein Benutzer eine URL für eine Arbeitsaufgabe in Azure DevOps, die die Messagingerweiterung in eine Karte aufgelöst hat:</span><span class="sxs-lookup"><span data-stu-id="f5ede-110">In the following image, a user has pasted a URL for a work item in Azure DevOps, which the messaging extension has resolved into a card:</span></span>

![Beispiel für die Verknüpfungsentfurling](~/assets/images/compose-extensions/messagingextensions_linkunfurling.png)

## <a name="add-link-unfurling-to-your-app-manifest"></a><span data-ttu-id="f5ede-112">Hinzufügen der Verknüpfungsentfurling zu Ihrem App-Manifest</span><span class="sxs-lookup"><span data-stu-id="f5ede-112">Add link unfurling to your app manifest</span></span>

<span data-ttu-id="f5ede-113">Fügen Sie dem Abschnitt Ihres App-Manifests JSON ein neues Array hinzu, um dem App-Manifest ein neues Array `messageHandlers` `composeExtensions` hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="f5ede-113">To add link unfurling to your app manifest, add a new `messageHandlers` array to the `composeExtensions` section of your app manifest JSON.</span></span> <span data-ttu-id="f5ede-114">Sie können das Array entweder mithilfe von App Studio oder manuell hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="f5ede-114">You can add the array either with the help of App Studio or manually.</span></span> <span data-ttu-id="f5ede-115">Domänenauflistungen können Platzhalter enthalten, z. B. `*.example.com` .</span><span class="sxs-lookup"><span data-stu-id="f5ede-115">Domain listings can include wildcards, for example `*.example.com`.</span></span> <span data-ttu-id="f5ede-116">Dies entspricht genau einem Abschnitt der Domäne. wenn Sie übereinstimmen müssen, `a.b.example.com` verwenden Sie `*.*.example.com` .</span><span class="sxs-lookup"><span data-stu-id="f5ede-116">This matches exactly one segment of the domain; if you need to match `a.b.example.com` then use `*.*.example.com`.</span></span>

> [!NOTE]
> <span data-ttu-id="f5ede-117">Fügen Sie keine Domänen hinzu, die sich weder direkt noch über Platzhalter in Ihrem Steuerelement befinden.</span><span class="sxs-lookup"><span data-stu-id="f5ede-117">Donot add domains that are not in your control, either directly or through wildcards.</span></span> <span data-ttu-id="f5ede-118">Beispielsweise ist `yourapp.onmicrosoft.com` gültig, aber `*.onmicrosoft.com` nicht gültig.</span><span class="sxs-lookup"><span data-stu-id="f5ede-118">For example, `yourapp.onmicrosoft.com` is valid, but `*.onmicrosoft.com` is not valid.</span></span> <span data-ttu-id="f5ede-119">Außerdem sind Domänen auf oberster Ebene verboten.</span><span class="sxs-lookup"><span data-stu-id="f5ede-119">Also, the top-level domains are prohibited.</span></span> <span data-ttu-id="f5ede-120">Beispiel: `*.com` , `*.org` .</span><span class="sxs-lookup"><span data-stu-id="f5ede-120">For example, `*.com`, `*.org`.</span></span>

### <a name="add-link-unfurling-using-app-studio"></a><span data-ttu-id="f5ede-121">Hinzufügen der Verknüpfungsentfurling mithilfe von App Studio</span><span class="sxs-lookup"><span data-stu-id="f5ede-121">Add link unfurling using App Studio</span></span>

1. <span data-ttu-id="f5ede-122">Öffnen **Sie App Studio** im Microsoft Teams Client, und wählen Sie die Registerkarte **Manifest-Editor** aus.</span><span class="sxs-lookup"><span data-stu-id="f5ede-122">Open **App Studio** from the Microsoft Teams client, and select the **Manifest Editor** tab.</span></span>
1. <span data-ttu-id="f5ede-123">Laden Sie Ihr App-Manifest.</span><span class="sxs-lookup"><span data-stu-id="f5ede-123">Load your app manifest.</span></span>
1. <span data-ttu-id="f5ede-124">Fügen Sie **auf der** Seite Messagingerweiterung die Domäne hinzu, nach der Sie suchen möchten, im Abschnitt **Nachrichtenhandler.**</span><span class="sxs-lookup"><span data-stu-id="f5ede-124">On the **Messaging Extension** page, add the domain that you want to look for in the **Message handlers** section.</span></span> <span data-ttu-id="f5ede-125">In der folgenden Abbildung wird der Vorgang erläutert:</span><span class="sxs-lookup"><span data-stu-id="f5ede-125">The following image explains the process:</span></span>

    ![Abschnitt "message handlers" in App Studio](~/assets/images/link-unfurling.png)
    
### <a name="add-link-unfurling-manually"></a><span data-ttu-id="f5ede-127">Manuelles Hinzufügen der Verknüpfungsentfurling</span><span class="sxs-lookup"><span data-stu-id="f5ede-127">Add link unfurling manually</span></span>

<span data-ttu-id="f5ede-128">Damit Ihre Messagingerweiterung mit Links interagieren kann, müssen Sie zuerst das `messageHandlers` Array zu Ihrem App-Manifest hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="f5ede-128">To enable your messaging extension to interact with links, first you must add the `messageHandlers` array to your app manifest.</span></span> <span data-ttu-id="f5ede-129">Im folgenden Beispiel wird erläutert, wie Sie die Verknüpfung manuell entfernen:</span><span class="sxs-lookup"><span data-stu-id="f5ede-129">The following example explains how to add link unfurling manually:</span></span> 


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

<span data-ttu-id="f5ede-130">Ein vollständiges Manifestbeispiel finden Sie unter [Manifestreferenz](~/resources/schema/manifest-schema.md).</span><span class="sxs-lookup"><span data-stu-id="f5ede-130">For a complete manifest example, see [manifest reference](~/resources/schema/manifest-schema.md).</span></span>

## <a name="handle-the-composeextensionquerylink-invoke"></a><span data-ttu-id="f5ede-131">Behandeln des `composeExtension/queryLink` Aufrufs</span><span class="sxs-lookup"><span data-stu-id="f5ede-131">Handle the `composeExtension/queryLink` invoke</span></span>

<span data-ttu-id="f5ede-132">Nachdem Sie die Domäne zum App-Manifest hinzugefügt haben, müssen Sie den Webdienstcode aktualisieren, um die Aufrufanforderung zu verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="f5ede-132">After adding the domain to the app manifest, you must update your web service code to handle the invoke request.</span></span> <span data-ttu-id="f5ede-133">Verwenden Sie die empfangene URL, um Ihren Dienst zu durchsuchen und eine Kartenantwort zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="f5ede-133">Use the received URL to search your service and create a card response.</span></span> <span data-ttu-id="f5ede-134">Wenn Sie mit mehreren Karten antworten, wird nur die erste Kartenantwort verwendet.</span><span class="sxs-lookup"><span data-stu-id="f5ede-134">If you respond with more than one card, only the first card response is used.</span></span>

<span data-ttu-id="f5ede-135">Die folgenden Kartentypen werden unterstützt:</span><span class="sxs-lookup"><span data-stu-id="f5ede-135">The following card types are supported:</span></span>

* [<span data-ttu-id="f5ede-136">Miniaturansichtskarte</span><span class="sxs-lookup"><span data-stu-id="f5ede-136">Thumbnail card</span></span>](~/task-modules-and-cards/cards/cards-reference.md#thumbnail-card)
* [<span data-ttu-id="f5ede-137">Heldenkarte</span><span class="sxs-lookup"><span data-stu-id="f5ede-137">Hero card</span></span>](~/task-modules-and-cards/cards/cards-reference.md#hero-card)
* [<span data-ttu-id="f5ede-138">Office 365 Connectorkarte</span><span class="sxs-lookup"><span data-stu-id="f5ede-138">Office 365 Connector card</span></span>](~/task-modules-and-cards/cards/cards-reference.md#office-365-connector-card)
* [<span data-ttu-id="f5ede-139">Adaptive Karte</span><span class="sxs-lookup"><span data-stu-id="f5ede-139">Adaptive Card</span></span>](~/task-modules-and-cards/cards/cards-reference.md#adaptive-card)

### <a name="example"></a><span data-ttu-id="f5ede-140">Beispiel</span><span class="sxs-lookup"><span data-stu-id="f5ede-140">Example</span></span>

# <a name="cnet"></a>[<span data-ttu-id="f5ede-141">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="f5ede-141">C#/.NET</span></span>](#tab/dotnet)

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

# <a name="javascriptnodejs"></a>[<span data-ttu-id="f5ede-142">JavaScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="f5ede-142">JavaScript/Node.js</span></span>](#tab/javascript)

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

# <a name="json"></a>[<span data-ttu-id="f5ede-143">Json</span><span class="sxs-lookup"><span data-stu-id="f5ede-143">JSON</span></span>](#tab/json)

<span data-ttu-id="f5ede-144">Im Folgenden finden Sie ein Beispiel für die an `invoke` Ihren Bot gesendeten:</span><span class="sxs-lookup"><span data-stu-id="f5ede-144">Following is an example of the `invoke` sent to your bot:</span></span>

```json
{
  "type": "invoke",
  "name": "composeExtension/queryLink",
  "value": {
    "url": "https://theurlsubmittedbyyouruser.trackeddomain.com/id/1234"
  }
}
```

<span data-ttu-id="f5ede-145">Im Folgenden finden Sie ein Beispiel für die Antwort:</span><span class="sxs-lookup"><span data-stu-id="f5ede-145">Following is an example of the response:</span></span>

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
        }
      }
    ]
  }
}
```

* * *

## <a name="see-also"></a><span data-ttu-id="f5ede-146">Sehen Sie ebenfalls</span><span class="sxs-lookup"><span data-stu-id="f5ede-146">See also</span></span> 

* [<span data-ttu-id="f5ede-147">Karten</span><span class="sxs-lookup"><span data-stu-id="f5ede-147">Cards</span></span>](~/task-modules-and-cards/what-are-cards.md)
* [<span data-ttu-id="f5ede-148">Tabs link unfurling and Stage View</span><span class="sxs-lookup"><span data-stu-id="f5ede-148">Tabs link unfurling and Stage View</span></span>](~/tabs/tabs-link-unfurling.md)
