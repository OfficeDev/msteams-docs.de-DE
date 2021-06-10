---
title: Entfalten von Links
author: clearab
description: So führen Sie die Verbreitung von Links mit der Messaging-Erweiterung in einer Microsoft Teams-App durch.
localization_priority: Normal
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: 726ba47d1290b4dc38bb2b90e5ce9fc8a3c5fb6b
ms.sourcegitcommit: 37325179a532897fafbe827dcf9a7ca5fa5e7d0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2021
ms.locfileid: "52853550"
---
# <a name="link-unfurling"></a><span data-ttu-id="556a6-103">Entfalten von Links</span><span class="sxs-lookup"><span data-stu-id="556a6-103">Link unfurling</span></span>

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

<span data-ttu-id="556a6-104">In diesem Dokument erfahren Sie, wie Sie Ihrem App-Manifest mitHilfe von App Studio und manuell eine Verknüpfung hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="556a6-104">This document guides you on how to add link unfurling to your app manifest using App studio and manually.</span></span> <span data-ttu-id="556a6-105">Mit der Verbreitung von Links kann Ihre App sich registrieren, um eine `invoke`-Aktivität zu empfangen, wenn URLs mit einer bestimmten Domäne in den Bereich zum Verfassen von Nachrichten eingefügt werden.</span><span class="sxs-lookup"><span data-stu-id="556a6-105">With link unfurling your app can register to receive an `invoke` activity when URLs with a particular domain are pasted into the compose message area.</span></span> <span data-ttu-id="556a6-106">Die `invoke` enthält die vollständige URL, die in den Bereich zum Verfassen von Nachrichten eingefügt wurde, und Sie können mit einer Karte antworten, die der Benutzer freigeben kann, und zusätzliche Informationen oder Aktionen bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="556a6-106">The `invoke` contains the full URL that was pasted into the compose message area, and you can respond with a card that the user can unfurl, providing additional information or actions.</span></span> <span data-ttu-id="556a6-107">Dies funktioniert ähnlich wie ein Suchbefehl mit der URL, die als Suchbegriff dient.</span><span class="sxs-lookup"><span data-stu-id="556a6-107">This works similar to a search command with the URL serving as the search term.</span></span>

> [!NOTE]
> * <span data-ttu-id="556a6-108">Derzeit wird die Verbreitung von Links auf mobilen Clients nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="556a6-108">Currently, link unfurling is not supported on Mobile clients.</span></span>
> * <span data-ttu-id="556a6-109">Das Ergebnis der Verknüpfungsentrollung wird 30 Minuten zwischengespeichert.</span><span class="sxs-lookup"><span data-stu-id="556a6-109">The link unfurling result is cached for 30 minutes.</span></span>

<span data-ttu-id="556a6-110">Die Azure DevOps Messaging-Erweiterung verwendet die Verbreitung von Links, um nach URLs zu suchen, die in den Bereich zum Verfassen von Nachrichten eingefügt sind, die auf eine Arbeitsaufgabe verweisen.</span><span class="sxs-lookup"><span data-stu-id="556a6-110">The Azure DevOps messaging extension uses link unfurling to look for URLs pasted into the compose message area pointing to a work item.</span></span> <span data-ttu-id="556a6-111">In der folgenden Abbildung hat ein Benutzer eine URL für eine Arbeitsaufgabe in Azure DevOps eingefügt, die die Messaging-Erweiterung in eine Karte aufgelöst hat:</span><span class="sxs-lookup"><span data-stu-id="556a6-111">In the following image, a user has pasted a URL for a work item in Azure DevOps, which the messaging extension has resolved into a card:</span></span>

![Beispiel für die Verbreitung von Links](~/assets/images/compose-extensions/messagingextensions_linkunfurling.png)

## <a name="add-link-unfurling-to-your-app-manifest"></a><span data-ttu-id="556a6-113">Hinzufügen der Verbreitung von Links zu Ihrem App-Manifest</span><span class="sxs-lookup"><span data-stu-id="556a6-113">Add link unfurling to your app manifest</span></span>

<span data-ttu-id="556a6-114">Zum Hinzufügen der Verbreitung von Links zu Ihrem App-Manifest fügen Sie `messageHandlers` dem Abschnitt Ihres App-Manifest-JSON ein neues Array `composeExtensions` hinzu.</span><span class="sxs-lookup"><span data-stu-id="556a6-114">To add link unfurling to your app manifest, add a new `messageHandlers` array to the `composeExtensions` section of your app manifest JSON.</span></span> <span data-ttu-id="556a6-115">Sie können das Array entweder mithilfe von App Studio oder manuell hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="556a6-115">You can add the array either with the help of App Studio or manually.</span></span> <span data-ttu-id="556a6-116">Domäneneinträge können Platzhalter enthalten, `*.example.com` z. B. .</span><span class="sxs-lookup"><span data-stu-id="556a6-116">Domain listings can include wildcards, for example `*.example.com`.</span></span> <span data-ttu-id="556a6-117">Dies entspricht genau einem Segment der Domäne. wenn Sie übereinstimmen `a.b.example.com` müssen, verwenden Sie `*.*.example.com` .</span><span class="sxs-lookup"><span data-stu-id="556a6-117">This matches exactly one segment of the domain; if you need to match `a.b.example.com` then use `*.*.example.com`.</span></span>

> [!NOTE]
> <span data-ttu-id="556a6-118">Fügen Sie keine Domänen hinzu, die sich nicht in Ihrem Steuerelement befinden, entweder direkt oder über Platzhalter.</span><span class="sxs-lookup"><span data-stu-id="556a6-118">Donot add domains that are not in your control, either directly or through wildcards.</span></span> <span data-ttu-id="556a6-119">Ist z. `yourapp.onmicrosoft.com` B. gültig, aber `*.onmicrosoft.com` nicht gültig.</span><span class="sxs-lookup"><span data-stu-id="556a6-119">For example, `yourapp.onmicrosoft.com` is valid, but `*.onmicrosoft.com` is not valid.</span></span> <span data-ttu-id="556a6-120">Außerdem sind die Domänen auf oberster Ebene nicht zulässig.</span><span class="sxs-lookup"><span data-stu-id="556a6-120">Also, the top-level domains are prohibited.</span></span> <span data-ttu-id="556a6-121">Beispiel: `*.com` , `*.org` .</span><span class="sxs-lookup"><span data-stu-id="556a6-121">For example, `*.com`, `*.org`.</span></span>

### <a name="add-link-unfurling-using-app-studio"></a><span data-ttu-id="556a6-122">Hinzufügen der Verbreitung von Links mit App Studio</span><span class="sxs-lookup"><span data-stu-id="556a6-122">Add link unfurling using App Studio</span></span>

1. <span data-ttu-id="556a6-123">Öffnen Sie **App Studio** im Microsoft Teams-Client, und wählen Sie die Registerkarte **"Manifest-Editor"** aus.</span><span class="sxs-lookup"><span data-stu-id="556a6-123">Open **App Studio** from the Microsoft Teams client, and select the **Manifest Editor** tab.</span></span>
1. <span data-ttu-id="556a6-124">Laden Sie Das App-Manifest.</span><span class="sxs-lookup"><span data-stu-id="556a6-124">Load your app manifest.</span></span>
1. <span data-ttu-id="556a6-125">Fügen Sie auf der Seite **"Messaging-Erweiterung"** die Domäne hinzu, nach der Sie im Abschnitt **"Nachrichtenhandler"** suchen möchten.</span><span class="sxs-lookup"><span data-stu-id="556a6-125">On the **Messaging Extension** page, add the domain that you want to look for in the **Message handlers** section.</span></span> <span data-ttu-id="556a6-126">In der folgenden Abbildung wird der Prozess erläutert:</span><span class="sxs-lookup"><span data-stu-id="556a6-126">The following image explains the process:</span></span>

    ![Abschnitt "message handlers" in App Studio](~/assets/images/link-unfurling.png)
    
### <a name="add-link-unfurling-manually"></a><span data-ttu-id="556a6-128">Manuelles Hinzufügen der Verknüpfungsweitergabe</span><span class="sxs-lookup"><span data-stu-id="556a6-128">Add link unfurling manually</span></span>

<span data-ttu-id="556a6-129">Damit Ihre Messaging-Erweiterung mit Links interagieren kann, müssen Sie zuerst das `messageHandlers` Array zu Ihrem App-Manifest hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="556a6-129">To enable your messaging extension to interact with links, first you must add the `messageHandlers` array to your app manifest.</span></span> <span data-ttu-id="556a6-130">Im folgenden Beispiel wird erläutert, wie Sie die Verknüpfungsweitergabe manuell hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="556a6-130">The following example explains how to add link unfurling manually:</span></span> 


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

<span data-ttu-id="556a6-131">Ein vollständiges Manifestbeispiel finden Sie in der [Manifestreferenz.](~/resources/schema/manifest-schema.md)</span><span class="sxs-lookup"><span data-stu-id="556a6-131">For a complete manifest example, see [manifest reference](~/resources/schema/manifest-schema.md).</span></span>

## <a name="handle-the-composeextensionquerylink-invoke"></a><span data-ttu-id="556a6-132">Behandeln des `composeExtension/queryLink` Aufrufs</span><span class="sxs-lookup"><span data-stu-id="556a6-132">Handle the `composeExtension/queryLink` invoke</span></span>

<span data-ttu-id="556a6-133">Nachdem Sie die Domäne zum App-Manifest hinzugefügt haben, müssen Sie den Webdienstcode aktualisieren, um die Aufrufanforderung zu verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="556a6-133">After adding the domain to the app manifest, you must update your web service code to handle the invoke request.</span></span> <span data-ttu-id="556a6-134">Verwenden Sie die empfangene URL, um Ihren Dienst zu durchsuchen und eine Kartenantwort zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="556a6-134">Use the received URL to search your service and create a card response.</span></span> <span data-ttu-id="556a6-135">Wenn Sie mit mehr als einer Karte antworten, wird nur die erste Kartenantwort verwendet.</span><span class="sxs-lookup"><span data-stu-id="556a6-135">If you respond with more than one card, only the first card response is used.</span></span>

<span data-ttu-id="556a6-136">Die folgenden Kartentypen werden unterstützt:</span><span class="sxs-lookup"><span data-stu-id="556a6-136">The following card types are supported:</span></span>

* [<span data-ttu-id="556a6-137">Miniaturansichtskarte</span><span class="sxs-lookup"><span data-stu-id="556a6-137">Thumbnail card</span></span>](~/task-modules-and-cards/cards/cards-reference.md#thumbnail-card)
* [<span data-ttu-id="556a6-138">Hero-Karte</span><span class="sxs-lookup"><span data-stu-id="556a6-138">Hero card</span></span>](~/task-modules-and-cards/cards/cards-reference.md#hero-card)
* [<span data-ttu-id="556a6-139">Office 365 Connectorkarte</span><span class="sxs-lookup"><span data-stu-id="556a6-139">Office 365 Connector card</span></span>](~/task-modules-and-cards/cards/cards-reference.md#office-365-connector-card)
* [<span data-ttu-id="556a6-140">Adaptive Karte</span><span class="sxs-lookup"><span data-stu-id="556a6-140">Adaptive Card</span></span>](~/task-modules-and-cards/cards/cards-reference.md#adaptive-card)

### <a name="example"></a><span data-ttu-id="556a6-141">Beispiel</span><span class="sxs-lookup"><span data-stu-id="556a6-141">Example</span></span>

# <a name="cnet"></a>[<span data-ttu-id="556a6-142">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="556a6-142">C#/.NET</span></span>](#tab/dotnet)

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

# <a name="javascriptnodejs"></a>[<span data-ttu-id="556a6-143">JavaScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="556a6-143">JavaScript/Node.js</span></span>](#tab/javascript)

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

# <a name="json"></a>[<span data-ttu-id="556a6-144">Json</span><span class="sxs-lookup"><span data-stu-id="556a6-144">JSON</span></span>](#tab/json)

<span data-ttu-id="556a6-145">Es folgt ein Beispiel für das `invoke` An Ihren Bot gesendete:</span><span class="sxs-lookup"><span data-stu-id="556a6-145">Following is an example of the `invoke` sent to your bot:</span></span>

```json
{
  "type": "invoke",
  "name": "composeExtension/queryLink",
  "value": {
    "url": "https://theurlsubmittedbyyouruser.trackeddomain.com/id/1234"
  }
}
```

<span data-ttu-id="556a6-146">Es folgt ein Beispiel für die Antwort:</span><span class="sxs-lookup"><span data-stu-id="556a6-146">Following is an example of the response:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="556a6-147">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="556a6-147">See also</span></span> 

* [<span data-ttu-id="556a6-148">Karten</span><span class="sxs-lookup"><span data-stu-id="556a6-148">Cards</span></span>](~/task-modules-and-cards/what-are-cards.md)
* [<span data-ttu-id="556a6-149">Aufgeklappte Registerkartenverknüpfung und Phasenansicht</span><span class="sxs-lookup"><span data-stu-id="556a6-149">Tabs link unfurling and Stage View</span></span>](~/tabs/tabs-link-unfurling.md)
