---
title: Tabs link unfurling and Stage View
author: Rajeshwari-v
description: So öffnen Sie einen Link, öffnen Sie die Stage View, und anheften Sie eine Registerkarte mit Microsoft Teams App.
ms.topic: conceptual
ms.author: surbhigupta
ms.openlocfilehash: 7dfabfa58c49237e776af37a1ee40d707783d0dc
ms.sourcegitcommit: e1fe46c574cec378319814f8213209ad3063b2c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2021
ms.locfileid: "52631279"
---
# <a name="tabs-link-unfurling-and-stage-view"></a><span data-ttu-id="a1313-103">Tabs link unfurling and Stage View</span><span class="sxs-lookup"><span data-stu-id="a1313-103">Tabs link unfurling and Stage View</span></span>

> [!NOTE]
> <span data-ttu-id="a1313-104">Dieses Feature ist nur in [der öffentlichen Entwicklervorschau](../resources/dev-preview/developer-preview-intro.md) verfügbar.</span><span class="sxs-lookup"><span data-stu-id="a1313-104">This feature is available in [public developer preview](../resources/dev-preview/developer-preview-intro.md) only.</span></span>

<span data-ttu-id="a1313-105">Die Stage View ist eine neue Benutzeroberflächenkomponente, mit der Sie inhalte rendern können, die im Vollbildmodus in Teams geöffnet und als Registerkarte angeheftet werden.</span><span class="sxs-lookup"><span data-stu-id="a1313-105">Stage View is a new UI component, which allows you to render the content that is opened in full screen in Teams and pinned as a tab.</span></span>
 
> [!NOTE]
> <span data-ttu-id="a1313-106">Derzeit unterstützen Teams mobile Clients keine Registerkartenlinks zum Entffurling und zur Stage View.</span><span class="sxs-lookup"><span data-stu-id="a1313-106">Currently, Teams mobile clients do no support tabs link unfurling and Stage View.</span></span> <span data-ttu-id="a1313-107">Mobile Clients verwenden das vom Entwickler bereitgestellte Attribut, um die Seite im Webbrowser des `websiteUrl` Geräts zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="a1313-107">Mobile clients use the `websiteUrl` attribute provided by the developer to open the page in the device's web browser.</span></span>

## <a name="stage-view"></a><span data-ttu-id="a1313-108">Stage View</span><span class="sxs-lookup"><span data-stu-id="a1313-108">Stage View</span></span>

<span data-ttu-id="a1313-109">Die Stage View ist eine Vollbild-UI-Komponente, die Sie aufrufen können, um Ihre Webinhalte anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="a1313-109">Stage View is a full screen UI component that you can invoke to surface your web content.</span></span> <span data-ttu-id="a1313-110">Der vorhandene Link-Entf?ndungsdienst wird so aktualisiert, dass er verwendet wird, um URLs mithilfe einer adaptiven Karte und Chatdiensten in eine Registerkarte zu verwandeln.</span><span class="sxs-lookup"><span data-stu-id="a1313-110">The existing link unfurling service is updated so that it is used to turn URLs into a tab using an Adaptive Card and Chat Services.</span></span> <span data-ttu-id="a1313-111">Wenn ein Benutzer eine URL in einem Chat oder Kanal sendet, wird die URL auf eine adaptive Karte entsperrt.</span><span class="sxs-lookup"><span data-stu-id="a1313-111">When a user sends a URL in a chat or channel, the URL is unfurled to an Adaptive Card.</span></span> <span data-ttu-id="a1313-112">Der Benutzer kann **auf** der Karte Ansicht auswählen und den Inhalt direkt aus der Stage View als Registerkarte anheften.</span><span class="sxs-lookup"><span data-stu-id="a1313-112">The user can select **View** in the card, and pin the content as a tab directly from the Stage View.</span></span>

## <a name="advantage-of-stage-view"></a><span data-ttu-id="a1313-113">Vorteile der Stage View</span><span class="sxs-lookup"><span data-stu-id="a1313-113">Advantage of Stage View</span></span>

<span data-ttu-id="a1313-114">Die Stage View bietet eine nahtlose Darstellung von Inhalten in Teams.</span><span class="sxs-lookup"><span data-stu-id="a1313-114">Stage View helps provide a more seamless experience of viewing content in Teams.</span></span> <span data-ttu-id="a1313-115">Benutzer können die von Ihrer App bereitgestellten Inhalte öffnen und anzeigen, ohne den Kontext zu verlassen, und sie können die Inhalte an den Chat oder Kanal anheften, um künftig schnell darauf zugreifen zu können.</span><span class="sxs-lookup"><span data-stu-id="a1313-115">Users can open and view the content provided by your app without leaving the context, and they can pin the content to the chat or channel for future quick access.</span></span> <span data-ttu-id="a1313-116">Dies führt zu einer höheren Benutzerbindung mit Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="a1313-116">This leads to a higher user engagement with your app.</span></span>

##  <a name="stage-view-vs-task-module"></a><span data-ttu-id="a1313-117">Stage View vs. Task Module</span><span class="sxs-lookup"><span data-stu-id="a1313-117">Stage View vs. Task module</span></span>

|<span data-ttu-id="a1313-118">Stage View</span><span class="sxs-lookup"><span data-stu-id="a1313-118">Stage View</span></span>|<span data-ttu-id="a1313-119">Aufgabenmodul</span><span class="sxs-lookup"><span data-stu-id="a1313-119">Task module</span></span>|
|:-----------|:-----------|
|<span data-ttu-id="a1313-120">Die Stage View ist hilfreich, wenn Sie den Benutzern einen reichhaltigen Inhalt anzeigen können, z. B. eine Seite, ein Dashboard, eine Datei und so weiter.</span><span class="sxs-lookup"><span data-stu-id="a1313-120">Stage View is useful when you have a rich content to display to the users, such as a page, a dashboard, a file, and so on.</span></span> <span data-ttu-id="a1313-121">Es bietet maximale Immobilie, die hilft, Ihre Inhalte im Vollbildbereich zu rendern.</span><span class="sxs-lookup"><span data-stu-id="a1313-121">It provides  maximum real estate that helps to render your content in the full-screen canvas.</span></span>|<span data-ttu-id="a1313-122">[Das Aufgabenmodul](../task-modules-and-cards/task-modules/task-modules-tabs.md) ist besonders nützlich, um Nachrichten anzeigen zu können, die die Aufmerksamkeit des Benutzers erfordern, oder informationen zu sammeln, die zum Nächsten Schritt erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="a1313-122">[Task module](../task-modules-and-cards/task-modules/task-modules-tabs.md) is especially useful to display messages that requires user's attention, or collect information required to move to the next step.</span></span>|
  
## <a name="invoke-the-stage-view"></a><span data-ttu-id="a1313-123">Aufrufen der Stage View</span><span class="sxs-lookup"><span data-stu-id="a1313-123">Invoke the Stage View</span></span>

<span data-ttu-id="a1313-124">Sie können die Stage View auf folgende Weise aufrufen:</span><span class="sxs-lookup"><span data-stu-id="a1313-124">You can invoke the Stage View in the following  ways:</span></span> 

* [<span data-ttu-id="a1313-125">Aufrufen der Stage View von adaptiver Karte</span><span class="sxs-lookup"><span data-stu-id="a1313-125">Invoke Stage View from Adaptive Card</span></span>](#invoke-stage-view-from-adaptive-card)
* [<span data-ttu-id="a1313-126">Aufrufen der Stage View über einen tiefen Link</span><span class="sxs-lookup"><span data-stu-id="a1313-126">Invoke Stage View through deep link</span></span>](#invoke-stage-view-through-deep-link)

## <a name="invoke-stage-view-from-adaptive-card"></a><span data-ttu-id="a1313-127">Aufrufen der Stage View von adaptiver Karte</span><span class="sxs-lookup"><span data-stu-id="a1313-127">Invoke Stage View from Adaptive Card</span></span>

<span data-ttu-id="a1313-128">Wenn der Benutzer eine URL auf dem Teams-Desktopclient eingibt, wird der Bot aufgerufen und gibt eine [adaptive](../task-modules-and-cards/cards/cards-actions.md) Karte mit der Option zurück, die URL in einer Phase zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="a1313-128">When the user enters a URL on the Teams desktop client, the bot is invoked and returns an [Adaptive Card](../task-modules-and-cards/cards/cards-actions.md) with the option to open the URL in a stage.</span></span> <span data-ttu-id="a1313-129">Nachdem eine Phase gestartet und die übergeben wurde, können Sie die Möglichkeit hinzufügen, die Phase als `tabInfo` Registerkarte anheften.</span><span class="sxs-lookup"><span data-stu-id="a1313-129">After a stage is launched and the `tabInfo` is passed in, you can add the ability to pin the stage as a tab.</span></span>  

<span data-ttu-id="a1313-130">In den folgenden Bildern wird eine Phase angezeigt, die von einer adaptiven Karte geöffnet wurde:</span><span class="sxs-lookup"><span data-stu-id="a1313-130">The following images display a stage opened from an Adaptive Card:</span></span>

<img src="~/assets/images/tab-images/open-stage-from-adaptive-card1.png" alt="Open a stage from Adaptive Card" width="400"/>

<img src="~/assets/images/tab-images/open-stage-from-adaptive-card2.png" alt="Open a stage" width="400"/>

### <a name="example"></a><span data-ttu-id="a1313-131">Beispiel</span><span class="sxs-lookup"><span data-stu-id="a1313-131">Example</span></span> 

<span data-ttu-id="a1313-132">Im Folgenden finden Sie den Code zum Öffnen einer Phase über eine adaptive Karte:</span><span class="sxs-lookup"><span data-stu-id="a1313-132">Following is the code to open a stage from an Adaptive Card:</span></span>

```json
{
    type: "Action.Submit",
    name: "View",
    data: {
          msteams: {
            type: "invoke",
            value: {
                type: "tab/tabInfoAction",
                tabInfo: {
                    contentUrl: contentUrl,
                    websiteUrl: websiteUrl,
                    name: "Tasks",
                    entityId: "entityId"
                 }
                }
            }
        }
} 
```

<span data-ttu-id="a1313-133">Der `invoke` Anforderungstyp muss `composeExtension/queryLink` sein.</span><span class="sxs-lookup"><span data-stu-id="a1313-133">The `invoke` request type must be `composeExtension/queryLink`.</span></span> 

> [!NOTE]
> * <span data-ttu-id="a1313-134">`invoke` workflow ähnelt dem aktuellen `appLinking` Workflow.</span><span class="sxs-lookup"><span data-stu-id="a1313-134">`invoke` workflow is similar to the current `appLinking` workflow.</span></span> 
> * <span data-ttu-id="a1313-135">Um konsistenzkonsistent zu bleiben, wird empfohlen, die als `Action.Submit` zu `View` benennen.</span><span class="sxs-lookup"><span data-stu-id="a1313-135">To maintain consistency, it is recommended to name the `Action.Submit` as `View`.</span></span>
> * <span data-ttu-id="a1313-136">`websiteUrl` ist eine erforderliche Eigenschaft, die im Objekt übergeben `TabInfo` werden muss.</span><span class="sxs-lookup"><span data-stu-id="a1313-136">`websiteUrl` is a required property to be passed in the `TabInfo` object.</span></span>

<span data-ttu-id="a1313-137">**Prozess zum Aufrufen der Stage View**</span><span class="sxs-lookup"><span data-stu-id="a1313-137">**Process to invoke Stage View**</span></span>

1. <span data-ttu-id="a1313-138">Wenn der Benutzer Ansicht **auswählt,** empfängt der Bot eine `invoke` Anforderung.</span><span class="sxs-lookup"><span data-stu-id="a1313-138">When the user selects **View**, the bot receives an `invoke` request.</span></span> <span data-ttu-id="a1313-139">Der Anforderungstyp ist `composeExtension/queryLink` .</span><span class="sxs-lookup"><span data-stu-id="a1313-139">The request type is `composeExtension/queryLink`.</span></span>
1. <span data-ttu-id="a1313-140">`invoke` Antwort vom Bot enthält eine adaptive Karte mit `tab/tabInfoAction` typ.</span><span class="sxs-lookup"><span data-stu-id="a1313-140">`invoke` response from bot contains an Adaptive Card with type `tab/tabInfoAction` in it.</span></span>
1. <span data-ttu-id="a1313-141">Der Bot antwortet mit einem `200` Code.</span><span class="sxs-lookup"><span data-stu-id="a1313-141">The bot responds with a `200` code.</span></span>

> [!NOTE]
> <span data-ttu-id="a1313-142">Derzeit unterstützen Teams mobile Clients die Stage View-Funktion nicht.</span><span class="sxs-lookup"><span data-stu-id="a1313-142">Currently, Teams mobile clients do not support the Stage View capability.</span></span> <span data-ttu-id="a1313-143">Wenn ein Benutzer **ansicht** auf einem mobilen Client auswählt, wird der Benutzer zum Browser des Geräts übernommen.</span><span class="sxs-lookup"><span data-stu-id="a1313-143">When a user selects **View** on a mobile client, the user is taken to the device's browser.</span></span> <span data-ttu-id="a1313-144">Der Browser öffnet die im Parameter des `websiteUrl` Objekts angegebene `TabInfo` URL.</span><span class="sxs-lookup"><span data-stu-id="a1313-144">The browser opens the URL specified in the `websiteUrl` parameter of the `TabInfo` object.</span></span>

## <a name="invoke-stage-view-through-deep-link"></a><span data-ttu-id="a1313-145">Aufrufen der Stage View über einen tiefen Link</span><span class="sxs-lookup"><span data-stu-id="a1313-145">Invoke Stage View through deep link</span></span>

<span data-ttu-id="a1313-146">Zum Aufrufen der Stage View über einen tiefen Link von Ihrer Registerkarte müssen Sie die Deep Link-URL in der `microsoftTeams.executeDeeplink(url)` API umschließen.</span><span class="sxs-lookup"><span data-stu-id="a1313-146">To invoke the Stage View through deep link from your tab, you must wrap the deep link URL in the `microsoftTeams.executeDeeplink(url)` API.</span></span> <span data-ttu-id="a1313-147">Der Deeplink kann auch über eine Aktion `OpenURL` auf der Karte übergeben werden.</span><span class="sxs-lookup"><span data-stu-id="a1313-147">The deeplink can also be passed through an `OpenURL` action in the card.</span></span>

<span data-ttu-id="a1313-148">In der folgenden Abbildung wird eine Stage View angezeigt, die über einen tiefen Link aufgerufen wird:</span><span class="sxs-lookup"><span data-stu-id="a1313-148">The following image displays a Stage View invoked through a deep link:</span></span>

<img src="~/assets/images/tab-images/invoke-stage-view-through-deep-link.png" alt="Invoke a Stage View through a deep link" width="400"/>

### <a name="syntax"></a><span data-ttu-id="a1313-149">Syntax</span><span class="sxs-lookup"><span data-stu-id="a1313-149">Syntax</span></span> 

<span data-ttu-id="a1313-150">Im Folgenden finden Sie die Deeplinksyntax:</span><span class="sxs-lookup"><span data-stu-id="a1313-150">Following is the deeplink syntax:</span></span>  
 
<span data-ttu-id="a1313-151"> https://teams.microsoft.com/l/stage/{appId}/0?context={"contentUrl":"[contentUrl]","websiteUrl":"[websiteUrl]","name":"[name]"}</span><span class="sxs-lookup"><span data-stu-id="a1313-151">https://teams.microsoft.com/l/stage/{appId}/0?context={“contentUrl”:”[contentUrl]”,“websiteUrl”:”[websiteUrl]”,“name”:”[name]”}</span></span>

### <a name="examples"></a><span data-ttu-id="a1313-152">Beispiele</span><span class="sxs-lookup"><span data-stu-id="a1313-152">Examples</span></span>

<span data-ttu-id="a1313-153">Wenn ein Benutzer eine URL eintritt, wird sie in einer adaptiven Karte entsperrt.</span><span class="sxs-lookup"><span data-stu-id="a1313-153">When a user enters a URL, it is unfurled into an Adaptive card.</span></span>
<span data-ttu-id="a1313-154">Im Folgenden finden Sie die Deep Link-Beispiele zum Aufrufen der Stage View:</span><span class="sxs-lookup"><span data-stu-id="a1313-154">Following are the deep link examples to invoke the Stage View:</span></span>

<span data-ttu-id="a1313-155">**Beispiel 1**</span><span class="sxs-lookup"><span data-stu-id="a1313-155">**Example 1**</span></span>

<span data-ttu-id="a1313-156"> https://teams.microsoft.com/l/stage/2a527703-1f6f-4559-a332-d8a7d288cd88/0?context={"contentUrl":"https%3A%2F%2Fmicrosoft.sharepoint.com%2Fteams%2FLokisSandbox%2FSitePages%2FSandbox-Page.aspx","websiteUrl":"https%3A%2F%2Fmicrosoft.sharepoint.com%2Fteams%2FLokisSandbox%2FSitePages%2FSandbox-Page.aspx","name":"Contoso"}</span><span class="sxs-lookup"><span data-stu-id="a1313-156">https://teams.microsoft.com/l/stage/2a527703-1f6f-4559-a332-d8a7d288cd88/0?context={“contentUrl”:”https%3A%2F%2Fmicrosoft.sharepoint.com%2Fteams%2FLokisSandbox%2FSitePages%2FSandbox-Page.aspx”,“websiteUrl”:”https%3A%2F%2Fmicrosoft.sharepoint.com%2Fteams%2FLokisSandbox%2FSitePages%2FSandbox-Page.aspx”,“name”:”Contoso”}</span></span>

<span data-ttu-id="a1313-157">**Beispiel 2**</span><span class="sxs-lookup"><span data-stu-id="a1313-157">**Example 2**</span></span>

<span data-ttu-id="a1313-158"> https://teams.microsoft.com/l/Meeting_Stage/2a527703-1f6f-4559-a332-d8a7d288cd88/0?context={"contentUrl":"https%3A%2F%2Fmicrosoft.sharepoint.com%2Fteams%2FLokisSandbox%2FSitePages%2FSandbox-Page.aspx","websiteUrl":"https%3A%2F%2Fmicrosoft.sharepoint.com%2Fteams%2FLokisSandbox%2FSitePages%2FSandbox-Page.aspx","name":"Contoso"}</span><span class="sxs-lookup"><span data-stu-id="a1313-158">https://teams.microsoft.com/l/Meeting_Stage/2a527703-1f6f-4559-a332-d8a7d288cd88/0?context={“contentUrl”:”https%3A%2F%2Fmicrosoft.sharepoint.com%2Fteams%2FLokisSandbox%2FSitePages%2FSandbox-Page.aspx”,“websiteUrl”:”https%3A%2F%2Fmicrosoft.sharepoint.com%2Fteams%2FLokisSandbox%2FSitePages%2FSandbox-Page.aspx”,“name”:”Contoso”}</span></span>

> [!NOTE]
> * <span data-ttu-id="a1313-159">Das `name` ist optional in deep link.</span><span class="sxs-lookup"><span data-stu-id="a1313-159">The `name` is optional in deep link.</span></span> <span data-ttu-id="a1313-160">Wenn er nicht enthalten ist, wird er durch den App-Namen ersetzt.</span><span class="sxs-lookup"><span data-stu-id="a1313-160">If not included, the app name replaces it.</span></span> 
> * <span data-ttu-id="a1313-161">Der Deep Link kann auch über eine Aktion übergeben `OpenURL` werden.</span><span class="sxs-lookup"><span data-stu-id="a1313-161">The deep link can also be passed through  an `OpenURL` action.</span></span>
> * <span data-ttu-id="a1313-162">Derzeit unterstützen Teams mobile Clients die Stage View-Funktion nicht.</span><span class="sxs-lookup"><span data-stu-id="a1313-162">Currently, Teams mobile clients do not support the Stage View capability.</span></span> <span data-ttu-id="a1313-163">Wenn Benutzer einen tiefen Link zu einer Stage View auswählen, werden sie zum Webbrowser ihres Geräts übernommen.</span><span class="sxs-lookup"><span data-stu-id="a1313-163">When users selects a deep link to a Stage View, they are taken to their device's web browser.</span></span> <span data-ttu-id="a1313-164">Der Webbrowser öffnet die im Parameter des Deep-Links angegebene `websiteUrl` URL.</span><span class="sxs-lookup"><span data-stu-id="a1313-164">The web browser opens the URL specified in the `websiteUrl` parameter of the deep link.</span></span>
> * <span data-ttu-id="a1313-165">Wenn Sie eine Phase aus einem bestimmten Kontext starten, stellen Sie sicher, dass Ihre App in diesem Kontext funktioniert.</span><span class="sxs-lookup"><span data-stu-id="a1313-165">When you launch a Stage from a certain context, ensure that your app works in that context.</span></span> <span data-ttu-id="a1313-166">Wenn Ihre Stage View beispielsweise über eine persönliche App gestartet wird, müssen Sie sicherstellen, dass Ihre App einen persönlichen Bereich hat.</span><span class="sxs-lookup"><span data-stu-id="a1313-166">For example, if your Stage View is launched from a personal app, you must ensure your app has a personal scope.</span></span>

## <a name="tab-information-property"></a><span data-ttu-id="a1313-167">Tabinformationseigenschaft</span><span class="sxs-lookup"><span data-stu-id="a1313-167">Tab information property</span></span>

| <span data-ttu-id="a1313-168">Eigenschaftenname</span><span class="sxs-lookup"><span data-stu-id="a1313-168">Property name</span></span> | <span data-ttu-id="a1313-169">Typ</span><span class="sxs-lookup"><span data-stu-id="a1313-169">Type</span></span> | <span data-ttu-id="a1313-170">Anzahl der Zeichen</span><span class="sxs-lookup"><span data-stu-id="a1313-170">Number of characters</span></span> | <span data-ttu-id="a1313-171">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="a1313-171">Description</span></span> |
|:-----------|:---------|:------------|:-----------------------|
| `entityId` | <span data-ttu-id="a1313-172">String</span><span class="sxs-lookup"><span data-stu-id="a1313-172">String</span></span> | <span data-ttu-id="a1313-173">64</span><span class="sxs-lookup"><span data-stu-id="a1313-173">64</span></span> | <span data-ttu-id="a1313-174">Diese Eigenschaft ist ein eindeutiger Bezeichner für die Entität, die auf der Registerkarte angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="a1313-174">This property is a  unique identifier for the entity that the tab displays.</span></span> <span data-ttu-id="a1313-175">Dies ist ein Pflichtfeld.</span><span class="sxs-lookup"><span data-stu-id="a1313-175">This is a required field.</span></span>|
| `name` | <span data-ttu-id="a1313-176">String</span><span class="sxs-lookup"><span data-stu-id="a1313-176">String</span></span> | <span data-ttu-id="a1313-177">128</span><span class="sxs-lookup"><span data-stu-id="a1313-177">128</span></span> | <span data-ttu-id="a1313-178">Diese Eigenschaft ist der Anzeigename der Registerkarte in der Kanalschnittstelle.</span><span class="sxs-lookup"><span data-stu-id="a1313-178">This property is the display name of the tab in the channel interface.</span></span> <span data-ttu-id="a1313-179">Dieses Feld ist optional.</span><span class="sxs-lookup"><span data-stu-id="a1313-179">This is an optional field.</span></span>|
| `contentUrl` | <span data-ttu-id="a1313-180">String</span><span class="sxs-lookup"><span data-stu-id="a1313-180">String</span></span> | <span data-ttu-id="a1313-181">2048</span><span class="sxs-lookup"><span data-stu-id="a1313-181">2048</span></span> | <span data-ttu-id="a1313-182">Diese Eigenschaft ist die https://-URL, die auf die Entitätsbenutzeroberfläche verweist, die im Zeichenbereich Teams werden soll.</span><span class="sxs-lookup"><span data-stu-id="a1313-182">This property is the https:// URL that points to the entity UI to be displayed in the Teams canvas.</span></span> <span data-ttu-id="a1313-183">Dies ist ein Pflichtfeld.</span><span class="sxs-lookup"><span data-stu-id="a1313-183">This is a required field.</span></span>|
| `websiteUrl?` | <span data-ttu-id="a1313-184">String</span><span class="sxs-lookup"><span data-stu-id="a1313-184">String</span></span> | <span data-ttu-id="a1313-185">2048</span><span class="sxs-lookup"><span data-stu-id="a1313-185">2048</span></span> | <span data-ttu-id="a1313-186">Diese Eigenschaft ist die https:// URL, auf die verweisen soll, wenn ein Benutzer die Ansicht in einem Browser auswählt.</span><span class="sxs-lookup"><span data-stu-id="a1313-186">This property is the https:// URL to point at, if a user selects to view in a browser.</span></span> <span data-ttu-id="a1313-187">Dies ist ein Pflichtfeld.</span><span class="sxs-lookup"><span data-stu-id="a1313-187">This is a required field.</span></span>|
| `removeUrl?` | <span data-ttu-id="a1313-188">String</span><span class="sxs-lookup"><span data-stu-id="a1313-188">String</span></span> | <span data-ttu-id="a1313-189">2048</span><span class="sxs-lookup"><span data-stu-id="a1313-189">2048</span></span> | <span data-ttu-id="a1313-190">Diese Eigenschaft ist die https://-URL, die auf die Benutzeroberfläche verweist, die angezeigt werden soll, wenn der Benutzer die Registerkarte löscht. Dies ist ein optionales Feld.</span><span class="sxs-lookup"><span data-stu-id="a1313-190">This property is the https:// URL that points to the UI to be displayed when the user deletes the tab. This is an optional field.</span></span>|

## <a name="see-also"></a><span data-ttu-id="a1313-191">Sehen Sie ebenfalls</span><span class="sxs-lookup"><span data-stu-id="a1313-191">See also</span></span>

[<span data-ttu-id="a1313-192">Verknüpfung mit Messagingerweiterungen wird entf?ndt</span><span class="sxs-lookup"><span data-stu-id="a1313-192">Messaging extensions link unfurling</span></span>](~/messaging-extensions/how-to/link-unfurling.md)


