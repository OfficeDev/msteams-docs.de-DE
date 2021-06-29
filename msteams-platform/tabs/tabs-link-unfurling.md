---
title: Aufgeklappte Registerkartenverknüpfung und Phasenansicht
author: Rajeshwari-v
description: So heben Sie einen Link auf, öffnen die Phasenansicht und heften eine Registerkarte mit Microsoft Teams App an.
ms.topic: conceptual
ms.author: surbhigupta
ms.openlocfilehash: b54eb5942d19749b39bb9bb504dd8645f5655ef3
ms.sourcegitcommit: 85a52119df6c4cb4536572e6d2e7407f0e5e8a23
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/29/2021
ms.locfileid: "53179944"
---
# <a name="tabs-link-unfurling-and-stage-view"></a><span data-ttu-id="7e21a-103">Aufgeklappte Registerkartenverknüpfung und Phasenansicht</span><span class="sxs-lookup"><span data-stu-id="7e21a-103">Tabs link unfurling and Stage View</span></span>

> [!NOTE]
> <span data-ttu-id="7e21a-104">Dieses Feature ist nur in der [öffentlichen Entwicklervorschau](../resources/dev-preview/developer-preview-intro.md) verfügbar.</span><span class="sxs-lookup"><span data-stu-id="7e21a-104">This feature is available in [public developer preview](../resources/dev-preview/developer-preview-intro.md) only.</span></span>

<span data-ttu-id="7e21a-105">Die Phasenansicht ist eine neue Benutzeroberflächenkomponente, mit der Sie den Inhalt rendern können, der im Vollbildmodus in Teams geöffnet und als Registerkarte angeheftet ist.</span><span class="sxs-lookup"><span data-stu-id="7e21a-105">Stage View is a new user interface (UI) component, which allows you to render the content that is opened in full screen in Teams and pinned as a tab.</span></span>
 
> [!NOTE]
> <span data-ttu-id="7e21a-106">Derzeit unterstützen Teams mobile Clients die Verbreitung von Registerkarten und die Phasenansicht nicht.</span><span class="sxs-lookup"><span data-stu-id="7e21a-106">Currently, Teams mobile clients do no support tabs link unfurling and Stage View.</span></span> <span data-ttu-id="7e21a-107">Mobile Clients verwenden das `websiteUrl` vom Entwickler bereitgestellte Attribut, um die Seite im Webbrowser des Geräts zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="7e21a-107">Mobile clients use the `websiteUrl` attribute provided by the developer to open the page in the device's web browser.</span></span>

## <a name="stage-view"></a><span data-ttu-id="7e21a-108">Phasenansicht</span><span class="sxs-lookup"><span data-stu-id="7e21a-108">Stage View</span></span>

<span data-ttu-id="7e21a-109">Die Phasenansicht ist eine Vollbild-UI-Komponente, die Sie aufrufen können, um Ihre Webinhalte anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="7e21a-109">Stage View is a full screen UI component that you can invoke to surface your web content.</span></span> <span data-ttu-id="7e21a-110">Der vorhandene Link-Verbreitungsdienst wird so aktualisiert, dass er verwendet wird, um URLs mithilfe einer adaptiven Karte und Chatdiensten in eine Registerkarte umzuwandeln.</span><span class="sxs-lookup"><span data-stu-id="7e21a-110">The existing link unfurling service is updated so that it is used to turn URLs into a tab using an Adaptive Card and Chat Services.</span></span> <span data-ttu-id="7e21a-111">Wenn ein Benutzer eine URL in einem Chat oder Kanal sendet, wird die URL auf eine adaptive Karte entrollt.</span><span class="sxs-lookup"><span data-stu-id="7e21a-111">When a user sends a URL in a chat or channel, the URL is unfurled to an Adaptive Card.</span></span> <span data-ttu-id="7e21a-112">Der Benutzer kann auf der Karte **"Anzeigen"** auswählen und den Inhalt direkt in der Phasenansicht als Registerkarte anheften.</span><span class="sxs-lookup"><span data-stu-id="7e21a-112">The user can select **View** in the card, and pin the content as a tab directly from Stage View.</span></span>

## <a name="advantage-of-stage-view"></a><span data-ttu-id="7e21a-113">Vorteile der Phasenansicht</span><span class="sxs-lookup"><span data-stu-id="7e21a-113">Advantage of Stage View</span></span>

<span data-ttu-id="7e21a-114">Die Phasenansicht bietet eine nahtlosere Erfahrung beim Anzeigen von Inhalten in Teams.</span><span class="sxs-lookup"><span data-stu-id="7e21a-114">Stage View helps provide a more seamless experience of viewing content in Teams.</span></span> <span data-ttu-id="7e21a-115">Benutzer können die von Ihrer App bereitgestellten Inhalte öffnen und anzeigen, ohne den Kontext zu verlassen, und sie können den Inhalt für zukünftigen Schnellzugriff an den Chat oder Kanal anheften.</span><span class="sxs-lookup"><span data-stu-id="7e21a-115">Users can open and view the content provided by your app without leaving the context, and they can pin the content to the chat or channel for future quick access.</span></span> <span data-ttu-id="7e21a-116">Dies führt zu einer höheren Benutzerbindung für Ihre App.</span><span class="sxs-lookup"><span data-stu-id="7e21a-116">This leads to a higher user engagement with your app.</span></span>

## <a name="stage-view-vs-task-module"></a><span data-ttu-id="7e21a-117">Phasenansicht im Vergleich zum Aufgabenmodul</span><span class="sxs-lookup"><span data-stu-id="7e21a-117">Stage View vs. Task module</span></span>

|<span data-ttu-id="7e21a-118">Phasenansicht</span><span class="sxs-lookup"><span data-stu-id="7e21a-118">Stage View</span></span>|<span data-ttu-id="7e21a-119">Aufgabenmodul</span><span class="sxs-lookup"><span data-stu-id="7e21a-119">Task module</span></span>|
|:-----------|:-----------|
|<span data-ttu-id="7e21a-120">Die Phasenansicht ist nützlich, wenn Sie benutzern umfangreiche Inhalte anzeigen können, z. B. eine Seite, ein Dashboard, eine Datei usw.</span><span class="sxs-lookup"><span data-stu-id="7e21a-120">Stage View is useful when you have rich content to display to the users, such as a page, a dashboard, a file, and so on.</span></span> <span data-ttu-id="7e21a-121">Es bietet umfangreiche Features, mit denen Sie Ihre Inhalte im Vollbildbereich rendern können.</span><span class="sxs-lookup"><span data-stu-id="7e21a-121">It provides  rich features that helps to render your content in the full-screen canvas.</span></span>|<span data-ttu-id="7e21a-122">[Das Aufgabenmodul](../task-modules-and-cards/task-modules/task-modules-tabs.md) ist besonders nützlich, um Nachrichten anzuzeigen, die Die Aufmerksamkeit des Benutzers erfordern, oder um Informationen zu sammeln, die zum Nächsten Schritt erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="7e21a-122">[Task module](../task-modules-and-cards/task-modules/task-modules-tabs.md) is especially useful to display messages that require user attention, or collect information required to move to the next step.</span></span>|
  
## <a name="invoke-stage-view"></a><span data-ttu-id="7e21a-123">Aufrufen der Phasenansicht</span><span class="sxs-lookup"><span data-stu-id="7e21a-123">Invoke Stage View</span></span>

<span data-ttu-id="7e21a-124">Sie können die Phasenansicht auf folgende Weise aufrufen:</span><span class="sxs-lookup"><span data-stu-id="7e21a-124">You can invoke Stage View in the following  ways:</span></span>

* [<span data-ttu-id="7e21a-125">Aufrufen der Phasenansicht von einer adaptiven Karte</span><span class="sxs-lookup"><span data-stu-id="7e21a-125">Invoke Stage View from Adaptive Card</span></span>](#invoke-stage-view-from-adaptive-card)
* [<span data-ttu-id="7e21a-126">Aufrufen der Phasenansicht über deep-Link</span><span class="sxs-lookup"><span data-stu-id="7e21a-126">Invoke Stage View through deep link</span></span>](#invoke-stage-view-through-deep-link)

## <a name="invoke-stage-view-from-adaptive-card"></a><span data-ttu-id="7e21a-127">Aufrufen der Phasenansicht von einer adaptiven Karte</span><span class="sxs-lookup"><span data-stu-id="7e21a-127">Invoke Stage View from Adaptive Card</span></span>

<span data-ttu-id="7e21a-128">Wenn der Benutzer eine URL auf dem Teams Desktopclient eingibt, wird der Bot aufgerufen und gibt eine [adaptive Karte](../task-modules-and-cards/cards/cards-actions.md) mit der Option zum Öffnen der URL in einer Phase zurück.</span><span class="sxs-lookup"><span data-stu-id="7e21a-128">When the user enters a URL on the Teams desktop client, the bot is invoked and returns an [Adaptive Card](../task-modules-and-cards/cards/cards-actions.md) with the option to open the URL in a stage.</span></span> <span data-ttu-id="7e21a-129">Nachdem eine Phase gestartet und `tabInfo` bereitgestellt wurde, können Sie die Phase als Registerkarte anheften.</span><span class="sxs-lookup"><span data-stu-id="7e21a-129">After a stage is launched and the `tabInfo` is provided, you can add the ability to pin the stage as a tab.</span></span>  

<span data-ttu-id="7e21a-130">Die folgenden Bilder zeigen eine Phase, die von einer adaptiven Karte geöffnet wurde:</span><span class="sxs-lookup"><span data-stu-id="7e21a-130">The following images display a stage opened from an Adaptive Card:</span></span>

<img src="~/assets/images/tab-images/open-stage-from-adaptive-card1.png" alt="Open a stage from Adaptive Card" width="700"/>

<img src="~/assets/images/tab-images/open-stage-from-adaptive-card2.png" alt="Open a stage" width="700"/>

### <a name="example"></a><span data-ttu-id="7e21a-131">Beispiel</span><span class="sxs-lookup"><span data-stu-id="7e21a-131">Example</span></span>

<span data-ttu-id="7e21a-132">Es folgt der Code zum Öffnen einer Phase von einer adaptiven Karte aus:</span><span class="sxs-lookup"><span data-stu-id="7e21a-132">Following is the code to open a stage from an Adaptive Card:</span></span>

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

<span data-ttu-id="7e21a-133">Der `invoke` Anforderungstyp muss `composeExtension/queryLink` .</span><span class="sxs-lookup"><span data-stu-id="7e21a-133">The `invoke` request type must be `composeExtension/queryLink`.</span></span>

> [!NOTE]
> * <span data-ttu-id="7e21a-134">`invoke` workflow is similar to the current `appLinking` workflow.</span><span class="sxs-lookup"><span data-stu-id="7e21a-134">`invoke` workflow is similar to the current `appLinking` workflow.</span></span> 
> * <span data-ttu-id="7e21a-135">Um die Konsistenz zu gewährleisten, wird empfohlen, den Namen `Action.Submit` `View` ".</span><span class="sxs-lookup"><span data-stu-id="7e21a-135">To maintain consistency, it is recommended to name `Action.Submit` as `View`.</span></span>
> * <span data-ttu-id="7e21a-136">`websiteUrl` ist eine erforderliche Eigenschaft, die im Objekt übergeben werden `TabInfo` muss.</span><span class="sxs-lookup"><span data-stu-id="7e21a-136">`websiteUrl` is a required property to be passed in the `TabInfo` object.</span></span>

<span data-ttu-id="7e21a-137">Nachfolgend sehen Sie den Prozess zum Aufrufen der Phasenansicht:</span><span class="sxs-lookup"><span data-stu-id="7e21a-137">Following is the process to invoke Stage View:</span></span>

* <span data-ttu-id="7e21a-138">Wenn der Benutzer **"Anzeigen"** auswählt, erhält der Bot eine `invoke` Anforderung.</span><span class="sxs-lookup"><span data-stu-id="7e21a-138">When the user selects **View**, the bot receives an `invoke` request.</span></span> <span data-ttu-id="7e21a-139">Der Anforderungstyp lautet `composeExtension/queryLink` .</span><span class="sxs-lookup"><span data-stu-id="7e21a-139">The request type is `composeExtension/queryLink`.</span></span>
* <span data-ttu-id="7e21a-140">`invoke` antwort von Bot enthält eine adaptive Karte mit Typ `tab/tabInfoAction` darin.</span><span class="sxs-lookup"><span data-stu-id="7e21a-140">`invoke` response from bot contains an Adaptive Card with type `tab/tabInfoAction` in it.</span></span>
* <span data-ttu-id="7e21a-141">Der Bot antwortet mit einem `200` Code.</span><span class="sxs-lookup"><span data-stu-id="7e21a-141">The bot responds with a `200` code.</span></span>

> [!NOTE]
> <span data-ttu-id="7e21a-142">Derzeit unterstützen Teams mobile Clients die Stage View-Funktion nicht.</span><span class="sxs-lookup"><span data-stu-id="7e21a-142">Currently, Teams mobile clients do not support the Stage View capability.</span></span> <span data-ttu-id="7e21a-143">Wenn ein Benutzer auf einem mobilen Client **"Anzeigen"** auswählt, wird der Benutzer zum Browser des Geräts weitergeleitet.</span><span class="sxs-lookup"><span data-stu-id="7e21a-143">When a user selects **View** on a mobile client, the user is taken to the device's browser.</span></span> <span data-ttu-id="7e21a-144">Der Browser öffnet die im Parameter des Objekts angegebene `websiteUrl` `TabInfo` URL.</span><span class="sxs-lookup"><span data-stu-id="7e21a-144">The browser opens the URL specified in the `websiteUrl` parameter of the `TabInfo` object.</span></span>

## <a name="invoke-stage-view-through-deep-link"></a><span data-ttu-id="7e21a-145">Aufrufen der Phasenansicht über deep-Link</span><span class="sxs-lookup"><span data-stu-id="7e21a-145">Invoke Stage View through deep link</span></span>

<span data-ttu-id="7e21a-146">Um die Phasenansicht über den Deep-Link von Ihrer Registerkarte aus aufzurufen, müssen Sie die DEEP-Link-URL in der `microsoftTeams.executeDeeplink(url)` API umschließen.</span><span class="sxs-lookup"><span data-stu-id="7e21a-146">To invoke the Stage View through deep link from your tab, you must wrap the deep link URL in the `microsoftTeams.executeDeeplink(url)` API.</span></span> <span data-ttu-id="7e21a-147">Der Deep-Link kann auch über eine Aktion auf der Karte übergeben `OpenURL` werden.</span><span class="sxs-lookup"><span data-stu-id="7e21a-147">The deep link can also be passed through an `OpenURL` action in the card.</span></span>

<span data-ttu-id="7e21a-148">In der folgenden Abbildung wird eine Phasenansicht angezeigt, die über einen Deep-Link aufgerufen wird:</span><span class="sxs-lookup"><span data-stu-id="7e21a-148">The following image displays a Stage View invoked through a deep link:</span></span>

<img src="~/assets/images/tab-images/invoke-stage-view-through-deep-link.png" alt="Invoke a Stage View through a deep link" width="400"/>

### <a name="syntax"></a><span data-ttu-id="7e21a-149">Syntax</span><span class="sxs-lookup"><span data-stu-id="7e21a-149">Syntax</span></span>

<span data-ttu-id="7e21a-150">Es folgt die Deeplinksyntax:</span><span class="sxs-lookup"><span data-stu-id="7e21a-150">Following is the deeplink syntax:</span></span>  
 
<span data-ttu-id="7e21a-151"> https://teams.microsoft.com/l/stage/{appId}/0?context={"contentUrl":"[contentUrl]","websiteUrl":"[websiteUrl]","name":"[name]"}</span><span class="sxs-lookup"><span data-stu-id="7e21a-151">https://teams.microsoft.com/l/stage/{appId}/0?context={“contentUrl”:”[contentUrl]”,“websiteUrl”:”[websiteUrl]”,“name”:”[name]”}</span></span>

### <a name="examples"></a><span data-ttu-id="7e21a-152">Beispiele</span><span class="sxs-lookup"><span data-stu-id="7e21a-152">Examples</span></span>

<span data-ttu-id="7e21a-153">Wenn ein Benutzer eine URL eingibt, wird diese in eine adaptive Karte entrollt.</span><span class="sxs-lookup"><span data-stu-id="7e21a-153">When a user enters a URL, it is unfurled into an Adaptive card.</span></span>

<span data-ttu-id="7e21a-154">Nachfolgend sind die Deep-Linkbeispiele zum Aufrufen der Phasenansicht aufgeführt:</span><span class="sxs-lookup"><span data-stu-id="7e21a-154">Following are the deep link examples to invoke Stage View:</span></span>

<span data-ttu-id="7e21a-155">**Beispiel 1**</span><span class="sxs-lookup"><span data-stu-id="7e21a-155">**Example 1**</span></span>

<span data-ttu-id="7e21a-156"> https://teams.microsoft.com/l/stage/2a527703-1f6f-4559-a332-d8a7d288cd88/0?context={"contentUrl":"https%3A%2F%2Fmicrosoft.sharepoint.com%2Fteams%2FLokisSandbox%2FSitePages%2FSandbox-Page.aspx","websiteUrl":"https%3A%2F%2Fmicrosoft.sharepoint.com%2Fteams%2FLokisSandbox%2FSitePages%2FSandbox-Page.aspx","name":"Contoso"}</span><span class="sxs-lookup"><span data-stu-id="7e21a-156">https://teams.microsoft.com/l/stage/2a527703-1f6f-4559-a332-d8a7d288cd88/0?context={“contentUrl”:”https%3A%2F%2Fmicrosoft.sharepoint.com%2Fteams%2FLokisSandbox%2FSitePages%2FSandbox-Page.aspx”,“websiteUrl”:”https%3A%2F%2Fmicrosoft.sharepoint.com%2Fteams%2FLokisSandbox%2FSitePages%2FSandbox-Page.aspx”,“name”:”Contoso”}</span></span>

<span data-ttu-id="7e21a-157">**Beispiel 2**</span><span class="sxs-lookup"><span data-stu-id="7e21a-157">**Example 2**</span></span>

<span data-ttu-id="7e21a-158"> https://teams.microsoft.com/l/Meeting_Stage/2a527703-1f6f-4559-a332-d8a7d288cd88/0?context={"contentUrl":"https%3A%2F%2Fmicrosoft.sharepoint.com%2Fteams%2FLokisSandbox%2FSitePages%2FSandbox-Page.aspx","websiteUrl":"https%3A%2F%2Fmicrosoft.sharepoint.com%2Fteams%2FLokisSandbox%2FSitePages%2FSandbox-Page.aspx","name":"Contoso"}</span><span class="sxs-lookup"><span data-stu-id="7e21a-158">https://teams.microsoft.com/l/Meeting_Stage/2a527703-1f6f-4559-a332-d8a7d288cd88/0?context={“contentUrl”:”https%3A%2F%2Fmicrosoft.sharepoint.com%2Fteams%2FLokisSandbox%2FSitePages%2FSandbox-Page.aspx”,“websiteUrl”:”https%3A%2F%2Fmicrosoft.sharepoint.com%2Fteams%2FLokisSandbox%2FSitePages%2FSandbox-Page.aspx”,“name”:”Contoso”}</span></span>

> [!NOTE]
> * <span data-ttu-id="7e21a-159">Dies `name` ist optional im Deep-Link.</span><span class="sxs-lookup"><span data-stu-id="7e21a-159">The `name` is optional in deep link.</span></span> <span data-ttu-id="7e21a-160">Wenn er nicht enthalten ist, wird er durch den App-Namen ersetzt.</span><span class="sxs-lookup"><span data-stu-id="7e21a-160">If not included, the app name replaces it.</span></span>
> * <span data-ttu-id="7e21a-161">Der Deep-Link kann auch über eine Aktion übergeben `OpenURL` werden.</span><span class="sxs-lookup"><span data-stu-id="7e21a-161">The deep link can also be passed through an `OpenURL` action.</span></span>
> * <span data-ttu-id="7e21a-162">Derzeit unterstützen Teams mobile Clients die Stage View-Funktion nicht.</span><span class="sxs-lookup"><span data-stu-id="7e21a-162">Currently, Teams mobile clients do not support the Stage View capability.</span></span> <span data-ttu-id="7e21a-163">Wenn Benutzer einen Deep-Link zu einer Phasenansicht auswählen, werden sie zum Webbrowser ihres Geräts geleitet.</span><span class="sxs-lookup"><span data-stu-id="7e21a-163">When users select a deep link to a Stage View, they are taken to their device's web browser.</span></span> <span data-ttu-id="7e21a-164">Der Webbrowser öffnet die URL, die im `websiteUrl` Parameter des Deep-Links angegeben ist.</span><span class="sxs-lookup"><span data-stu-id="7e21a-164">The web browser opens the URL specified in the `websiteUrl` parameter of the deep link.</span></span>
> * <span data-ttu-id="7e21a-165">Wenn Sie eine Phase aus einem bestimmten Kontext starten, stellen Sie sicher, dass Ihre App in diesem Kontext funktioniert.</span><span class="sxs-lookup"><span data-stu-id="7e21a-165">When you launch a Stage from a certain context, ensure that your app works in that context.</span></span> <span data-ttu-id="7e21a-166">Wenn Ihre Phasenansicht beispielsweise über eine persönliche App gestartet wird, müssen Sie sicherstellen, dass Ihre App einen persönlichen Bereich aufweist.</span><span class="sxs-lookup"><span data-stu-id="7e21a-166">For example, if your Stage View is launched from a personal app, you must ensure your app has a personal scope.</span></span>

## <a name="tab-information-property"></a><span data-ttu-id="7e21a-167">Tabinformationseigenschaft</span><span class="sxs-lookup"><span data-stu-id="7e21a-167">Tab information property</span></span>

| <span data-ttu-id="7e21a-168">Eigenschaftsname</span><span class="sxs-lookup"><span data-stu-id="7e21a-168">Property name</span></span> | <span data-ttu-id="7e21a-169">Typ</span><span class="sxs-lookup"><span data-stu-id="7e21a-169">Type</span></span> | <span data-ttu-id="7e21a-170">Anzahl der Zeichen</span><span class="sxs-lookup"><span data-stu-id="7e21a-170">Number of characters</span></span> | <span data-ttu-id="7e21a-171">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="7e21a-171">Description</span></span> |
|:-----------|:---------|:------------|:-----------------------|
| `entityId` | <span data-ttu-id="7e21a-172">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="7e21a-172">String</span></span> | <span data-ttu-id="7e21a-173">64</span><span class="sxs-lookup"><span data-stu-id="7e21a-173">64</span></span> | <span data-ttu-id="7e21a-174">Diese Eigenschaft ist ein eindeutiger Bezeichner für die Entität, die auf der Registerkarte angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="7e21a-174">This property is a  unique identifier for the entity that the tab displays.</span></span> <span data-ttu-id="7e21a-175">Dies ist ein Pflichtfeld.</span><span class="sxs-lookup"><span data-stu-id="7e21a-175">This is a required field.</span></span>|
| `name` | <span data-ttu-id="7e21a-176">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="7e21a-176">String</span></span> | <span data-ttu-id="7e21a-177">128</span><span class="sxs-lookup"><span data-stu-id="7e21a-177">128</span></span> | <span data-ttu-id="7e21a-178">Diese Eigenschaft ist der Anzeigename der Registerkarte in der Kanalschnittstelle.</span><span class="sxs-lookup"><span data-stu-id="7e21a-178">This property is the display name of the tab in the channel interface.</span></span> <span data-ttu-id="7e21a-179">Dieses Feld ist optional.</span><span class="sxs-lookup"><span data-stu-id="7e21a-179">This is an optional field.</span></span>|
| `contentUrl` | <span data-ttu-id="7e21a-180">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="7e21a-180">String</span></span> | <span data-ttu-id="7e21a-181">2048</span><span class="sxs-lookup"><span data-stu-id="7e21a-181">2048</span></span> | <span data-ttu-id="7e21a-182">Diese Eigenschaft ist die https://-URL, die auf die Entitätsbenutzeroberfläche verweist, die im Teams Canvas angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="7e21a-182">This property is the https:// URL that points to the entity UI to be displayed in the Teams canvas.</span></span> <span data-ttu-id="7e21a-183">Dies ist ein Pflichtfeld.</span><span class="sxs-lookup"><span data-stu-id="7e21a-183">This is a required field.</span></span>|
| `websiteUrl?` | <span data-ttu-id="7e21a-184">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="7e21a-184">String</span></span> | <span data-ttu-id="7e21a-185">2048</span><span class="sxs-lookup"><span data-stu-id="7e21a-185">2048</span></span> | <span data-ttu-id="7e21a-186">Diese Eigenschaft ist die https:// URL, auf die sie zeigen soll, wenn ein Benutzer die Anzeige in einem Browser auswählt.</span><span class="sxs-lookup"><span data-stu-id="7e21a-186">This property is the https:// URL to point at, if a user selects to view in a browser.</span></span> <span data-ttu-id="7e21a-187">Dies ist ein Pflichtfeld.</span><span class="sxs-lookup"><span data-stu-id="7e21a-187">This is a required field.</span></span>|
| `removeUrl?` | <span data-ttu-id="7e21a-188">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="7e21a-188">String</span></span> | <span data-ttu-id="7e21a-189">2048</span><span class="sxs-lookup"><span data-stu-id="7e21a-189">2048</span></span> | <span data-ttu-id="7e21a-190">Diese Eigenschaft ist die https:// URL, die auf die Benutzeroberfläche zeigt, die angezeigt werden soll, wenn der Benutzer die Registerkarte löscht. Dies ist ein optionales Feld.</span><span class="sxs-lookup"><span data-stu-id="7e21a-190">This property is the https:// URL that points to the UI to be displayed when the user deletes the tab. This is an optional field.</span></span>|

## <a name="see-also"></a><span data-ttu-id="7e21a-191">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="7e21a-191">See also</span></span>

* [<span data-ttu-id="7e21a-192">Verbreitung von Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="7e21a-192">Messaging extensions link unfurling</span></span>](~/messaging-extensions/how-to/link-unfurling.md)
* [<span data-ttu-id="7e21a-193">registerkarten Teams</span><span class="sxs-lookup"><span data-stu-id="7e21a-193">Teams tabs</span></span>](~/tabs/what-are-tabs.md)
* [<span data-ttu-id="7e21a-194">Erstellen einer persönlichen Registerkarte</span><span class="sxs-lookup"><span data-stu-id="7e21a-194">Create a personal tab</span></span>](~/tabs/how-to/create-personal-tab.md)
* [<span data-ttu-id="7e21a-195">Erstellen einer Kanal- oder Gruppenregisterkarte</span><span class="sxs-lookup"><span data-stu-id="7e21a-195">Create a channel or group tab</span></span>](~/tabs/how-to/create-channel-group-tab.md)

## <a name="next-step"></a><span data-ttu-id="7e21a-196">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="7e21a-196">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7e21a-197">Registerkarten für Unterhaltungen erstellen</span><span class="sxs-lookup"><span data-stu-id="7e21a-197">Create conversational tabs</span></span>](~/tabs/how-to/conversational-tabs.md)