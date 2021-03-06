---
title: Erstellen einer Inhaltsseite
author: laujan
description: Erstellen einer Inhaltsseite
keywords: teams tabs group channel configurable static
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 619ca1079fcdb5a44eec2fa63d6687a0eb65cd4d
ms.sourcegitcommit: 9cfbc44912980a33d2d7c7c85739aeea6ccb41de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "50479872"
---
# <a name="create-a-content-page-for-your-tab"></a><span data-ttu-id="617bf-104">Erstellen einer Inhaltsseite für Ihre Registerkarte</span><span class="sxs-lookup"><span data-stu-id="617bf-104">Create a content page for your tab</span></span>

<span data-ttu-id="617bf-105">Eine Inhaltsseite ist eine Webseite, die im Teams-Client gerendert wird.</span><span class="sxs-lookup"><span data-stu-id="617bf-105">A content page is a webpage that is rendered within the Teams client.</span></span> <span data-ttu-id="617bf-106">In der Regel sind diese Teil von:</span><span class="sxs-lookup"><span data-stu-id="617bf-106">Typically these are part of:</span></span>

* <span data-ttu-id="617bf-107">Eine benutzerdefinierte Registerkarte mit persönlichem Bereich: In diesem Fall ist die Inhaltsseite die erste Seite, auf die der Benutzer trifft.</span><span class="sxs-lookup"><span data-stu-id="617bf-107">A personal-scoped custom tab - In this instance the content page is the first page the user encounters.</span></span>
* <span data-ttu-id="617bf-108">Eine benutzerdefinierte Kanal-/Gruppenregisterkarte – Nachdem der Benutzer die Registerkarte im entsprechenden Kontext anheftet und konfiguriert hat, wird die Inhaltsseite angezeigt.</span><span class="sxs-lookup"><span data-stu-id="617bf-108">A channel/group custom tab - After the user pins and configures the tab in the appropriate context, the content page is displayed.</span></span>
* <span data-ttu-id="617bf-109">Ein [Aufgabenmodul:](~/task-modules-and-cards/what-are-task-modules.md) Sie können eine Inhaltsseite erstellen und als Webansicht in ein Aufgabenmodul einbetten.</span><span class="sxs-lookup"><span data-stu-id="617bf-109">A [task module](~/task-modules-and-cards/what-are-task-modules.md) - You can create a content page and embed it as a webview inside a task module.</span></span> <span data-ttu-id="617bf-110">Die Seite wird im modalen Popup gerendert.</span><span class="sxs-lookup"><span data-stu-id="617bf-110">The page will be rendered inside the modal popup.</span></span>

<span data-ttu-id="617bf-111">Dieser Artikel ist speziell für die Verwendung von Inhaltsseiten als Registerkarten. Der Großteil der hier gezeigten Anleitungen würde jedoch unabhängig davon gelten, wie die Inhaltsseite dem Endbenutzer präsentiert wird.</span><span class="sxs-lookup"><span data-stu-id="617bf-111">This article is specific to using content pages as tabs; however the majority of the guidance here would apply regardless of how the content page is presented to the end-user.</span></span>

## <a name="tab-content-and-style-guidelines"></a><span data-ttu-id="617bf-112">Richtlinien für Registerkarteninhalte und -stile</span><span class="sxs-lookup"><span data-stu-id="617bf-112">Tab content and style guidelines</span></span>

<span data-ttu-id="617bf-113">Das übergeordnete Ziel Ihrer Registerkarte sollte es sein, Zugriff auf aussagekräftige und ansprechende Inhalte zu bieten, die einen praktischen und offensichtlichen Zweck haben.</span><span class="sxs-lookup"><span data-stu-id="617bf-113">Your tab's overall objective should be to provide access to meaningful and engaging content that has a practical value and an evident purpose.</span></span> <span data-ttu-id="617bf-114">Dies bedeutet nicht, dass Sie auf einen ansprechenden Stil verzichten sollten, aber Sie sollten sich auf die Minimierung von Unübersichtlichkeit konzentrieren, indem Sie Das Tabdesign sauber, intuitiv und inhalteverdingend gestalten.</span><span class="sxs-lookup"><span data-stu-id="617bf-114">That does not mean that you should forego a pleasing style, but you should focus on minimizing clutter by making your tab design clean, navigation intuitive, and content immersive.</span></span> <span data-ttu-id="617bf-115">Informationen [zu Inhalten und Unterhaltungen finden](~/tabs/design/tabs.md) Sie unter Gleichzeitige Verwendung von Registerkarten und Anleitungen zum [Genehmigungsprozess für Microsoft Teams-Apps](~/concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md)</span><span class="sxs-lookup"><span data-stu-id="617bf-115">See [Content and conversations, all at once using tabs](~/tabs/design/tabs.md) and [Microsoft Teams app approval process guidance](~/concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md)</span></span>

## <a name="integrate-your-code-with-teams"></a><span data-ttu-id="617bf-116">Integrieren von Code in Teams</span><span class="sxs-lookup"><span data-stu-id="617bf-116">Integrate your code with Teams</span></span>

<span data-ttu-id="617bf-117">Damit Ihre Seite in Teams angezeigt werden kann, müssen Sie das [Microsoft Teams JavaScript-Client-SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest) und einen Aufruf nach dem Laden `microsoftTeams.initialize()` der Seite hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="617bf-117">For your page to display in Teams, you must include the [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest) and include a call to `microsoftTeams.initialize()` after your page loads.</span></span> <span data-ttu-id="617bf-118">So kommunizieren Ihre Seite und der Teams-Client:</span><span class="sxs-lookup"><span data-stu-id="617bf-118">That is how your page and the Teams client communicate:</span></span>

```html
<!DOCTYPE html>
<html>
<head>
...
    <script src= 'https://statics.teams.cdn.office.net/sdk/v1.6.0/js/MicrosoftTeams.min.js'></script>
...
</head>

<body>
...
    <script>
    microsoftTeams.initialize();
    </script>
...
</body>
```

## <a name="accessing-additional-content"></a><span data-ttu-id="617bf-119">Zugreifen auf zusätzliche Inhalte</span><span class="sxs-lookup"><span data-stu-id="617bf-119">Accessing additional content</span></span>

### <a name="using-the-sdk-to-interact-with-teams"></a><span data-ttu-id="617bf-120">Verwenden des SDK für die Interaktion mit Teams</span><span class="sxs-lookup"><span data-stu-id="617bf-120">Using the SDK to interact with Teams</span></span>

<span data-ttu-id="617bf-121">Das [JavaScript SDK](~/tabs/how-to/using-teams-client-sdk.md) des Teams-Clients bietet viele zusätzliche Funktionen, die Sie bei der Entwicklung Ihrer Inhaltsseite möglicherweise hilfreich finden.</span><span class="sxs-lookup"><span data-stu-id="617bf-121">The [Teams client JavaScript SDK](~/tabs/how-to/using-teams-client-sdk.md) provides many additional functions you may find useful while developing your content page.</span></span>

### <a name="deep-links"></a><span data-ttu-id="617bf-122">Deep-Links</span><span class="sxs-lookup"><span data-stu-id="617bf-122">Deep links</span></span>

<span data-ttu-id="617bf-123">Sie können tiefe Links zu Entitäten in Teams erstellen.</span><span class="sxs-lookup"><span data-stu-id="617bf-123">You can create deep links to entities in Teams.</span></span> <span data-ttu-id="617bf-124">In der Regel werden diese zum Erstellen von Links verwendet, die zu Inhalten und Informationen auf Ihrer Registerkarte navigieren. Weitere [Informationen finden Sie unter Erstellen von tiefen Links zu Inhalten und Features in Microsoft Teams](~/concepts/build-and-test/deep-links.md).</span><span class="sxs-lookup"><span data-stu-id="617bf-124">Typically, these are used to create links that navigate to content and information within your tab. See [Create deep links to content and features in Microsoft Teams](~/concepts/build-and-test/deep-links.md).</span></span>

### <a name="task-modules"></a><span data-ttu-id="617bf-125">Aufgabenmodule</span><span class="sxs-lookup"><span data-stu-id="617bf-125">Task Modules</span></span>

<span data-ttu-id="617bf-126">Ein Aufgabenmodul ist eine modale Popuperfahrung, die Sie von Ihrer Registerkarte aus auslösen können. In der Regel möchten Sie auf einer Inhaltsseite ihren Benutzer nicht durch mehrere Seiten navigieren.</span><span class="sxs-lookup"><span data-stu-id="617bf-126">A task module is a modal popup-like experience that you can trigger from your tab. Typically in a content page you do not want to navigate your user through multiple pages.</span></span> <span data-ttu-id="617bf-127">Stattdessen verwenden Sie Aufgabenmodule, um Formulare zum Sammeln zusätzlicher Informationen, zum Anzeigen der Details eines Elements in einer Liste oder zum anderen Zeitpunkt, zu dem Sie dem Benutzer zusätzliche Informationen präsentieren müssen, zu präsentieren.</span><span class="sxs-lookup"><span data-stu-id="617bf-127">Instead, you will use task modules to present forms for gathering additional information, displaying the details of an item in a list, or any other time you need to present the user with additional information.</span></span> <span data-ttu-id="617bf-128">Die Aufgabenmodule selbst können zusätzliche Inhaltsseiten sein oder vollständig mit adaptiven Karten erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="617bf-128">The task modules themselves can be additional content pages, or created completely using Adaptive Cards.</span></span> <span data-ttu-id="617bf-129">Vollständige Informationen finden Sie unter Verwenden [von Aufgabenmodulen in](~/task-modules-and-cards/task-modules/task-modules-tabs.md) Registerkarten.</span><span class="sxs-lookup"><span data-stu-id="617bf-129">See [Using task modules in tabs](~/task-modules-and-cards/task-modules/task-modules-tabs.md) for complete information.</span></span>

### <a name="valid-domains"></a><span data-ttu-id="617bf-130">Gültige Domänen</span><span class="sxs-lookup"><span data-stu-id="617bf-130">Valid Domains</span></span>

<span data-ttu-id="617bf-131">Stellen Sie sicher, dass alle in Ihren Registerkarten verwendeten URL-Domänen im `validDomains` Array in Ihrem Manifest enthalten [sind.](~/concepts/build-and-test/apps-package.md)</span><span class="sxs-lookup"><span data-stu-id="617bf-131">Ensure that the all URL domains used in your tabs are included in the `validDomains` array in your [manifest](~/concepts/build-and-test/apps-package.md).</span></span> <span data-ttu-id="617bf-132">Weitere Informationen finden Sie unter [validDomains](~/resources/schema/manifest-schema.md#validdomains) in der Manifestschemareferenz.</span><span class="sxs-lookup"><span data-stu-id="617bf-132">For more information, see [validDomains](~/resources/schema/manifest-schema.md#validdomains) in the manifest schema reference.</span></span> <span data-ttu-id="617bf-133">Beachten Sie jedoch, dass die Kernfunktionalität Ihrer Registerkarte in Teams und nicht außerhalb von Teams vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="617bf-133">However, be mindful that the core functionality of your tab exists within Teams and not outside of Teams.</span></span>

## <a name="reorder-static-personal-tabs"></a><span data-ttu-id="617bf-134">Neu anordnen von statischen persönlichen Registerkarten</span><span class="sxs-lookup"><span data-stu-id="617bf-134">Reorder static personal tabs</span></span>

<span data-ttu-id="617bf-135">Ab Manifestversion 1.7 können Entwickler alle Registerkarten in ihrer persönlichen App neu anordnen.</span><span class="sxs-lookup"><span data-stu-id="617bf-135">Starting with manifest version 1.7, developers can rearrange all tabs in their personal app.</span></span> <span data-ttu-id="617bf-136">Insbesondere kann ein Entwickler  die Registerkarte Botchat, die immer an die erste Position festgelegt ist, an eine beliebige Stelle in der Persönlichen App-Registerkartenkopfzeile verschieben.</span><span class="sxs-lookup"><span data-stu-id="617bf-136">In particular, a developer can move the *bot chat* tab, which always defaults to the first position, anywhere in the personal app tab header.</span></span> <span data-ttu-id="617bf-137">Wir haben zwei reservierte Tab-EntityId-Schlüsselwörter deklariert, *Unterhaltungen* und *über*.</span><span class="sxs-lookup"><span data-stu-id="617bf-137">We’ve declared two reserved tab entityId keywords, *conversations* and *about*.</span></span>

<span data-ttu-id="617bf-138">Wenn Sie einen Bot  mit einem persönlichen Bereich erstellen, wird er standardmäßig an der ersten Registerkartenposition in einer persönlichen App angezeigt.</span><span class="sxs-lookup"><span data-stu-id="617bf-138">If you create a bot with a *personal* scope, it will show up in the first tab position in a personal app by default.</span></span> <span data-ttu-id="617bf-139">Wenn Sie es an eine andere Position verschieben möchten, müssen Sie dem Manifest ein statisches Tab-Objekt mit dem reservierten Schlüsselwort *Unterhaltungen hinzufügen.*</span><span class="sxs-lookup"><span data-stu-id="617bf-139">If you wish to move it to another position, you must add a static tab object to your manifest with the reserved keyword, *conversations*.</span></span> <span data-ttu-id="617bf-140">Die *Registerkarte* Unterhaltung wird im Web oder Desktop angezeigt, je nach der Stelle, an der Sie die *Registerkarte* Unterhaltung im Array `staticTabs` hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="617bf-140">The *conversation* tab appears on web or desktop based on where you add the *conversation* tab in the `staticTabs` array.</span></span> 

```json
{
   "staticTabs":[
      {
         
      },
      {
         "entityId":"conversations",
         "scopes":[
            "personal"
         ]
      }
   ]
}
```

## <a name="show-a-native-loading-indicator"></a><span data-ttu-id="617bf-141">Anzeigen eines systemeigenen Ladeindikators</span><span class="sxs-lookup"><span data-stu-id="617bf-141">Show a native loading indicator</span></span>

<span data-ttu-id="617bf-142">Ab [Manifestschema v1.7](../../../resources/schema/manifest-schema.md)können Sie [](../../../resources/schema/manifest-schema.md#showloadingindicator) eine systemeigene Ladeanzeige überall dort bereitstellen, wo Ihre Webinhalte in [](removal-page.md) Teams geladen werden, z. B. Registerkarteninhaltsseite, [](#integrate-your-code-with-teams)Konfigurationsseite, [](configuration-page.md) [Entfernungsseite](../../../task-modules-and-cards/task-modules/task-modules-tabs.md)und Aufgabenmodule in Registerkarten .</span><span class="sxs-lookup"><span data-stu-id="617bf-142">Starting with [manifest schema v1.7](../../../resources/schema/manifest-schema.md), you can provide a [native loading indicator](../../../resources/schema/manifest-schema.md#showloadingindicator) wherever your web content is loaded in Teams, e.g., [tab content page](#integrate-your-code-with-teams), [configuration page](configuration-page.md), [removal page](removal-page.md) and [task modules in tabs](../../../task-modules-and-cards/task-modules/task-modules-tabs.md).</span></span>

> [!NOTE]
> 1. <span data-ttu-id="617bf-143">Die systemeigene Ladeanzeige wird auf mobilen Geräten noch nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="617bf-143">The native loading indicator is not yet supported on mobile devices.</span></span>
> 2. <span data-ttu-id="617bf-144">Wenn Sie im App-Manifest angeben, müssen alle Registerkartenkonfigurations-, Inhalts- und Entfernungsseiten sowie alle iframebasierten Aufgabenmodule dem obligatorischen Protokoll folgen, das unten  `"showLoadingIndicator : true`  aufgeführt ist:</span><span class="sxs-lookup"><span data-stu-id="617bf-144">If you indicate  `"showLoadingIndicator : true`  in your app manifest, then all tab configuration, content, and removal pages and all iframe-based task modules must follow the mandatory protocol, below:</span></span>


1. <span data-ttu-id="617bf-145">Um den Ladeindikator zu zeigen, fügen Sie `"showLoadingIndicator": true` dem Manifest hinzu.</span><span class="sxs-lookup"><span data-stu-id="617bf-145">To show the loading indicator, add `"showLoadingIndicator": true` to your manifest.</span></span> 
2. <span data-ttu-id="617bf-146">Denken Sie daran, `microsoftTeams.initialize();` auf zu rufen.</span><span class="sxs-lookup"><span data-stu-id="617bf-146">Remember to call `microsoftTeams.initialize();`.</span></span>
3. <span data-ttu-id="617bf-147">**Optional**.</span><span class="sxs-lookup"><span data-stu-id="617bf-147">**Optional**.</span></span> <span data-ttu-id="617bf-148">Wenn Sie bereit sind, auf den Bildschirm zu drucken und den Rest des Anwendungsinhalts verzögert laden möchten, können Sie die Ladeanzeige manuell ausblenden, indem Sie `microsoftTeams.appInitialization.notifyAppLoaded();`</span><span class="sxs-lookup"><span data-stu-id="617bf-148">If you're ready to print to the screen and wish to lazy load the rest of your application's content, you can manually hide the loading indicator by calling `microsoftTeams.appInitialization.notifyAppLoaded();`</span></span>
4. <span data-ttu-id="617bf-149">**Obligatorisch**.</span><span class="sxs-lookup"><span data-stu-id="617bf-149">**Mandatory**.</span></span> <span data-ttu-id="617bf-150">Rufen Sie schließlich Teams auf, um zu benachrichtigen, dass Ihre App `microsoftTeams.appInitialization.notifySuccess()` erfolgreich geladen wurde.</span><span class="sxs-lookup"><span data-stu-id="617bf-150">Finally, call `microsoftTeams.appInitialization.notifySuccess()` to notify Teams that your app has successfully loaded.</span></span> <span data-ttu-id="617bf-151">Teams blendet dann ggf. die Ladeanzeige aus.</span><span class="sxs-lookup"><span data-stu-id="617bf-151">Teams will then hide the loading indicator if applicable.</span></span> <span data-ttu-id="617bf-152">Wenn nicht innerhalb von 30 Sekunden aufgerufen wird, wird davon ausgegangen, dass für Ihre App ein Zeitsprung aufgetreten ist und ein Fehlerbildschirm mit einer  `notifySuccess`  Wiederholungsoption angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="617bf-152">If  `notifySuccess`  is not called within 30 seconds, it will be assumed that your app timed out and an error screen with a retry option will appear.</span></span>
5. <span data-ttu-id="617bf-153">Wenn ihre Anwendung nicht geladen werden kann, können Sie Teams über `microsoftTeams.appInitialization.notifyFailure(reason);` einen Fehler in Verbindung mit dem Server rufen.</span><span class="sxs-lookup"><span data-stu-id="617bf-153">If your application fails to load, you can call `microsoftTeams.appInitialization.notifyFailure(reason);` to let Teams know there was an error.</span></span> <span data-ttu-id="617bf-154">Dem Benutzer wird dann ein Fehlerbildschirm angezeigt:</span><span class="sxs-lookup"><span data-stu-id="617bf-154">An error screen will then be shown to the user:</span></span>

```typescript
``
/* List of failure reasons */
export const enum FailedReason {
    AuthFailed = "AuthFailed",
    Timeout = "Timeout",
    Other = "Other"
}
```
>
