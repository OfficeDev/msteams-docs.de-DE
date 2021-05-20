---
title: Erstellen einer Inhaltsseite
author: laujan
description: Erstellen einer Inhaltsseite
keywords: Teams Registerkarten Gruppenkanal konfigurierbar statisch
localization_priority: Normal
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 136160cb9154d62be40d8e29075ac1fc86135a6b
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566677"
---
# <a name="create-a-content-page-for-your-tab"></a><span data-ttu-id="1e33a-104">Erstellen einer Inhaltsseite für Ihre Registerkarte</span><span class="sxs-lookup"><span data-stu-id="1e33a-104">Create a content page for your tab</span></span>

<span data-ttu-id="1e33a-105">Eine Inhaltsseite ist eine Webseite, die innerhalb des Teams-Clients gerendert wird.</span><span class="sxs-lookup"><span data-stu-id="1e33a-105">A content page is a webpage that is rendered within the Teams client.</span></span> <span data-ttu-id="1e33a-106">In der Regel sind diese Teil von:</span><span class="sxs-lookup"><span data-stu-id="1e33a-106">Typically these are part of:</span></span>

* <span data-ttu-id="1e33a-107">Eine benutzerdefinierte Registerkarte mit persönlichem Umfang: In diesem Fall ist die Inhaltsseite die erste Seite, auf die der Benutzer trifft.</span><span class="sxs-lookup"><span data-stu-id="1e33a-107">A personal-scoped custom tab: In this instance the content page is the first page the user encounters.</span></span>
* <span data-ttu-id="1e33a-108">Eine benutzerdefinierte Registerkarte "Kanal/Gruppe": Nachdem der Benutzer die Registerkarte im entsprechenden Kontext fixiert und konfiguriert hat, wird die Inhaltsseite angezeigt.</span><span class="sxs-lookup"><span data-stu-id="1e33a-108">A channel/group custom tab: After the user pins and configures the tab in the appropriate context, the content page is displayed.</span></span>
* <span data-ttu-id="1e33a-109">Ein [Aufgabenmodul](~/task-modules-and-cards/what-are-task-modules.md): Sie können eine Inhaltsseite erstellen und als Webansicht in ein Aufgabenmodul einbetten.</span><span class="sxs-lookup"><span data-stu-id="1e33a-109">A [task module](~/task-modules-and-cards/what-are-task-modules.md): You can create a content page and embed it as a webview inside a task module.</span></span> <span data-ttu-id="1e33a-110">Die Seite wird im modalen Popup gerendert.</span><span class="sxs-lookup"><span data-stu-id="1e33a-110">The page will be rendered inside the modal popup.</span></span>

<span data-ttu-id="1e33a-111">Dieser Artikel ist spezifisch für die Verwendung von Inhaltsseiten als Registerkarten; Der Großteil der Anleitungen würde hier jedoch unabhängig davon gelten, wie die Inhaltsseite dem Endbenutzer präsentiert wird.</span><span class="sxs-lookup"><span data-stu-id="1e33a-111">This article is specific to using content pages as tabs; however the majority of the guidance here would apply regardless of how the content page is presented to the end-user.</span></span>

## <a name="tab-content-and-design-guidelines"></a><span data-ttu-id="1e33a-112">Tab-Inhalt und Designrichtlinien</span><span class="sxs-lookup"><span data-stu-id="1e33a-112">Tab content and design guidelines</span></span>

<span data-ttu-id="1e33a-113">Das übergeordnete Ziel Ihrer Registerkarte sollte darin bestehen, den Zugriff auf aussagekräftige und ansprechende Inhalte zu ermöglichen, die einen praktischen Wert und einen offensichtlichen Zweck haben.</span><span class="sxs-lookup"><span data-stu-id="1e33a-113">Your tab's overall objective should be to provide access to meaningful and engaging content that has a practical value and an evident purpose.</span></span> <span data-ttu-id="1e33a-114">Das bedeutet nicht, dass Sie auf einen ansprechenden Stil verzichten sollten, aber Sie sollten sich auf die Minimierung von Unordnung konzentrieren, indem Sie Ihr Tab-Design sauber, Navigation intuitiv und Inhalt immersive.</span><span class="sxs-lookup"><span data-stu-id="1e33a-114">That does not mean that you should forego a pleasing style, but you should focus on minimizing clutter by making your tab design clean, navigation intuitive, and content immersive.</span></span>

<span data-ttu-id="1e33a-115">Weitere Informationen finden Sie in den Richtlinien für den [Tab-Design](~/tabs/design/tabs.md) und [Microsoft Teams-Richtlinien für](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md) die Speichervalidierung</span><span class="sxs-lookup"><span data-stu-id="1e33a-115">For more information, see the [tab design guidelines](~/tabs/design/tabs.md) and [Microsoft Teams store validation guidelines](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md)</span></span>

## <a name="integrate-your-code-with-teams"></a><span data-ttu-id="1e33a-116">Integrieren Sie Ihren Code in Teams</span><span class="sxs-lookup"><span data-stu-id="1e33a-116">Integrate your code with Teams</span></span>

<span data-ttu-id="1e33a-117">Damit Ihre Seite in Teams angezeigt wird, müssen Sie das [Microsoft Teams JavaScript-Client-SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) und einen Aufruf an die Seite nach dem `microsoftTeams.initialize()` Laden der Seite einfügen.</span><span class="sxs-lookup"><span data-stu-id="1e33a-117">For your page to display in Teams, you must include the [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) and include a call to `microsoftTeams.initialize()` after your page loads.</span></span> <span data-ttu-id="1e33a-118">So kommunizieren Ihre Seite und der Teams Client:</span><span class="sxs-lookup"><span data-stu-id="1e33a-118">That is how your page and the Teams client communicate:</span></span>

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

## <a name="accessing-additional-content"></a><span data-ttu-id="1e33a-119">Zugriff auf zusätzliche Inhalte</span><span class="sxs-lookup"><span data-stu-id="1e33a-119">Accessing additional content</span></span>

### <a name="using-the-sdk-to-interact-with-teams"></a><span data-ttu-id="1e33a-120">Verwenden des SDK zur Interaktion mit Teams</span><span class="sxs-lookup"><span data-stu-id="1e33a-120">Using the SDK to interact with Teams</span></span>

<span data-ttu-id="1e33a-121">Das [Teams Client JavaScript SDK](~/tabs/how-to/using-teams-client-sdk.md) bietet viele zusätzliche Funktionen, die Sie beim Entwickeln Ihrer Inhaltsseite nützlich finden können.</span><span class="sxs-lookup"><span data-stu-id="1e33a-121">The [Teams client JavaScript SDK](~/tabs/how-to/using-teams-client-sdk.md) provides many additional functions you may find useful while developing your content page.</span></span>

### <a name="deep-links"></a><span data-ttu-id="1e33a-122">Deep-Links</span><span class="sxs-lookup"><span data-stu-id="1e33a-122">Deep links</span></span>

<span data-ttu-id="1e33a-123">Sie können tiefe Verknüpfungen zu Entitäten in Teams erstellen.</span><span class="sxs-lookup"><span data-stu-id="1e33a-123">You can create deep links to entities in Teams.</span></span> <span data-ttu-id="1e33a-124">In der Regel werden diese verwendet, um Links zu erstellen, die zu Inhalten und Informationen auf Ihrer Registerkarte navigieren. Weitere Informationen finden Sie unter [Erstellen von Deep Links zu Inhalten und Features in Microsoft Teams](~/concepts/build-and-test/deep-links.md).</span><span class="sxs-lookup"><span data-stu-id="1e33a-124">Typically, these are used to create links that navigate to content and information within your tab. For more information, see [Create deep links to content and features in Microsoft Teams](~/concepts/build-and-test/deep-links.md).</span></span>

### <a name="task-modules"></a><span data-ttu-id="1e33a-125">Aufgabenmodule</span><span class="sxs-lookup"><span data-stu-id="1e33a-125">Task Modules</span></span>

<span data-ttu-id="1e33a-126">Ein Taskmodul ist eine modale Popup-ähnliche Erfahrung, die Sie von Ihrer Registerkarte aus auslösen können. In der Regel möchten Sie auf einer Inhaltsseite nicht durch mehrere Seiten navigieren.</span><span class="sxs-lookup"><span data-stu-id="1e33a-126">A task module is a modal popup-like experience that you can trigger from your tab. Typically in a content page you do not want to navigate your user through multiple pages.</span></span> <span data-ttu-id="1e33a-127">Stattdessen verwenden Sie Aufgabenmodule, um Formulare zum Sammeln zusätzlicher Informationen, Anzeigen der Details eines Elements in einer Liste oder zu jeder anderen Zeit, die Sie benötigen, um dem Benutzer zusätzliche Informationen zu präsentieren.</span><span class="sxs-lookup"><span data-stu-id="1e33a-127">Instead, you will use task modules to present forms for gathering additional information, displaying the details of an item in a list, or any other time you need to present the user with additional information.</span></span> <span data-ttu-id="1e33a-128">Die Aufgabenmodule selbst können zusätzliche Inhaltsseiten sein oder vollständig mit Adaptive Cards erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="1e33a-128">The task modules themselves can be additional content pages, or created completely using Adaptive Cards.</span></span> <span data-ttu-id="1e33a-129">Weitere Informationen finden Sie unter [Verwenden von Aufgabenmodulen in Registerkarten.](~/task-modules-and-cards/task-modules/task-modules-tabs.md)</span><span class="sxs-lookup"><span data-stu-id="1e33a-129">See [Using task modules in tabs](~/task-modules-and-cards/task-modules/task-modules-tabs.md) for complete information.</span></span>

### <a name="valid-domains"></a><span data-ttu-id="1e33a-130">Gültige Domänen</span><span class="sxs-lookup"><span data-stu-id="1e33a-130">Valid Domains</span></span>

<span data-ttu-id="1e33a-131">Stellen Sie sicher, dass alle URL-Domänen, die auf Ihren Registerkarten verwendet werden, im Array in Ihrem Manifest enthalten `validDomains` sind. [](~/concepts/build-and-test/apps-package.md)</span><span class="sxs-lookup"><span data-stu-id="1e33a-131">Ensure that the all URL domains used in your tabs are included in the `validDomains` array in your [manifest](~/concepts/build-and-test/apps-package.md).</span></span> <span data-ttu-id="1e33a-132">Weitere Informationen finden Sie unter [validDomains](~/resources/schema/manifest-schema.md#validdomains) im Manifestschemaverweis.</span><span class="sxs-lookup"><span data-stu-id="1e33a-132">For more information, see [validDomains](~/resources/schema/manifest-schema.md#validdomains) in the manifest schema reference.</span></span> <span data-ttu-id="1e33a-133">Beachten Sie jedoch, dass die Kernfunktionalität Ihrer Registerkarte innerhalb Teams und nicht außerhalb von Teams vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="1e33a-133">However, be mindful that the core functionality of your tab exists within Teams and not outside of Teams.</span></span>

## <a name="reorder-static-personal-tabs"></a><span data-ttu-id="1e33a-134">Neuanordnen statischer persönlicher Registerkarten</span><span class="sxs-lookup"><span data-stu-id="1e33a-134">Reorder static personal tabs</span></span>

<span data-ttu-id="1e33a-135">Ab Manifestversion 1.7 können Entwickler alle Registerkarten in ihrer persönlichen App neu anordnen.</span><span class="sxs-lookup"><span data-stu-id="1e33a-135">Starting with manifest version 1.7, developers can rearrange all tabs in their personal app.</span></span> <span data-ttu-id="1e33a-136">Insbesondere kann ein Entwickler die *Bot-Chat-Registerkarte* verschieben, die immer standardmäßig an die erste Position, an einer beliebigen Stelle im Header der persönlichen App-Registerkarte ist.</span><span class="sxs-lookup"><span data-stu-id="1e33a-136">In particular, a developer can move the *bot chat* tab, which always defaults to the first position, anywhere in the personal app tab header.</span></span> <span data-ttu-id="1e33a-137">Wir haben zwei reservierte Tab-EntitätId-Schlüsselwörter, *Unterhaltungen* und *über* deklariert.</span><span class="sxs-lookup"><span data-stu-id="1e33a-137">We’ve declared two reserved tab entityId keywords, *conversations* and *about*.</span></span>

<span data-ttu-id="1e33a-138">Wenn Sie einen Bot mit einem *persönlichen* Bereich erstellen, wird er standardmäßig an der ersten Tabstoppposition in einer persönlichen App angezeigt.</span><span class="sxs-lookup"><span data-stu-id="1e33a-138">If you create a bot with a *personal* scope, it will show up in the first tab position in a personal app by default.</span></span> <span data-ttu-id="1e33a-139">Wenn Sie es an eine andere Position verschieben möchten, müssen Sie Ihrem Manifest ein statisches Tabstoppobjekt mit dem reservierten Schlüsselwort *Unterhaltungen* hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="1e33a-139">If you wish to move it to another position, you must add a static tab object to your manifest with the reserved keyword, *conversations*.</span></span> <span data-ttu-id="1e33a-140">Die *Registerkarte Unterhaltung* wird im Web oder Desktop angezeigt, je nach dem Ort, an dem Sie die *Unterhaltungsregisterkarte* im `staticTabs` Array hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="1e33a-140">The *conversation* tab appears on web or desktop based on where you add the *conversation* tab in the `staticTabs` array.</span></span> 

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

## <a name="show-a-native-loading-indicator"></a><span data-ttu-id="1e33a-141">Anzeigen einer nativen Ladeanzeige</span><span class="sxs-lookup"><span data-stu-id="1e33a-141">Show a native loading indicator</span></span>

<span data-ttu-id="1e33a-142">Ab [dem Manifestschema v1.7](../../../resources/schema/manifest-schema.md)können Sie überall dort, wo Ihre Webinhalte in Teams geladen werden, eine [systemeigene Ladeanzeige](../../../resources/schema/manifest-schema.md#showloadingindicator) bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="1e33a-142">Starting with [manifest schema v1.7](../../../resources/schema/manifest-schema.md), you can provide a [native loading indicator](../../../resources/schema/manifest-schema.md#showloadingindicator) wherever your web content is loaded in Teams.</span></span> <span data-ttu-id="1e33a-143">Beispiel: [Registerkarteninhaltsseite](#integrate-your-code-with-teams), [Konfigurationsseite](configuration-page.md), [Entfernungsseite](removal-page.md)und [Aufgabenmodule in Registerkarten](../../../task-modules-and-cards/task-modules/task-modules-tabs.md).</span><span class="sxs-lookup"><span data-stu-id="1e33a-143">For example, [tab content page](#integrate-your-code-with-teams), [configuration page](configuration-page.md), [removal page](removal-page.md), and [task modules in tabs](../../../task-modules-and-cards/task-modules/task-modules-tabs.md).</span></span>

> [!NOTE]
> * <span data-ttu-id="1e33a-144">Das Verhalten auf mobilen Clients kann über diese Manifesteigenschaft nicht konfiguriert werden.</span><span class="sxs-lookup"><span data-stu-id="1e33a-144">The behavior on mobile clients is not configurable through this manifest property.</span></span> <span data-ttu-id="1e33a-145">Mobile Clients zeigen standardmäßig eine systemeigene Ladeanzeige über Inhaltsseiten und iframe-basierte Aufgabenmodule hinweg an.</span><span class="sxs-lookup"><span data-stu-id="1e33a-145">Mobile clients show a native loading indicator by default across content pages and iframe-based task modules.</span></span> <span data-ttu-id="1e33a-146">Dieser Indikator auf Mobilgeräten wird angezeigt, wenn eine Anforderung zum Abrufen von Inhalten gestellt wird, und wird abgelehnt, sobald die Anforderung abgeschlossen wird.</span><span class="sxs-lookup"><span data-stu-id="1e33a-146">This indicator on mobile is shown when a request is made to fetch content and gets dismissed as soon as the request gets completed.</span></span>
> * <span data-ttu-id="1e33a-147">Wenn Sie  `"showLoadingIndicator : true`  in Ihrem App-Manifest angeben, müssen alle Registerkartenkonfigurations-, Inhalts- und Entfernungsseiten sowie alle iframe-basierten Aufgabenmodule dem obligatorischen Protokoll folgen:</span><span class="sxs-lookup"><span data-stu-id="1e33a-147">If you indicate  `"showLoadingIndicator : true`  in your app manifest, then all tab configuration, content, and removal pages and all iframe-based task modules must follow the mandatory protocol, below:</span></span>

<span data-ttu-id="1e33a-148">**So zeigen Sie die Ladeanzeige an**</span><span class="sxs-lookup"><span data-stu-id="1e33a-148">**To show the loading indicator**</span></span>

* <span data-ttu-id="1e33a-149">Fügen Sie `"showLoadingIndicator": true` Ihrem Manifest hinzu.</span><span class="sxs-lookup"><span data-stu-id="1e33a-149">Add `"showLoadingIndicator": true` to your manifest.</span></span> 
* <span data-ttu-id="1e33a-150">Denken Sie daran, `microsoftTeams.initialize();` anzurufen.</span><span class="sxs-lookup"><span data-stu-id="1e33a-150">Remember to call `microsoftTeams.initialize();`.</span></span>
* <span data-ttu-id="1e33a-151">**Optional**: Wenn Sie bereit sind, auf dem Bildschirm zu drucken und den Rest des Anwendungsinhalts nicht mehr laden möchten, können Sie die Ladeanzeige manuell ausblenden, indem Sie `microsoftTeams.appInitialization.notifyAppLoaded();`</span><span class="sxs-lookup"><span data-stu-id="1e33a-151">**Optional**: If you're ready to print to the screen and wish to lazy load the rest of your application's content, you can manually hide the loading indicator by calling `microsoftTeams.appInitialization.notifyAppLoaded();`</span></span>
* <span data-ttu-id="1e33a-152">**Obligatorisch**: Rufen Sie schließlich `microsoftTeams.appInitialization.notifySuccess()` an, um Teams zu benachrichtigen, dass Ihre App erfolgreich geladen wurde.</span><span class="sxs-lookup"><span data-stu-id="1e33a-152">**Mandatory**: Finally, call `microsoftTeams.appInitialization.notifySuccess()` to notify Teams that your app has successfully loaded.</span></span> <span data-ttu-id="1e33a-153">Teams blenden dann ggf. die Ladeanzeige aus.</span><span class="sxs-lookup"><span data-stu-id="1e33a-153">Teams will then hide the loading indicator if applicable.</span></span> <span data-ttu-id="1e33a-154">Wenn  `notifySuccess`  nicht innerhalb von 30 Sekunden aufgerufen wird, wird davon ausgegangen, dass eine Zeitlupe ihrer App auftritt und ein Fehlerbildschirm mit einer Wiederholungsoption angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="1e33a-154">If  `notifySuccess`  is not called within 30 seconds, it will be assumed that your app timed out and an error screen with a retry option will appear.</span></span>
* <span data-ttu-id="1e33a-155">Wenn Ihre Anwendung nicht geladen werden kann, können Sie `microsoftTeams.appInitialization.notifyFailure(reason);` aufrufen, um Teams zu informieren, dass ein Fehler aufgetreten ist.</span><span class="sxs-lookup"><span data-stu-id="1e33a-155">If your application fails to load, you can call `microsoftTeams.appInitialization.notifyFailure(reason);` to let Teams know there was an error.</span></span> <span data-ttu-id="1e33a-156">Anschließend wird dem Benutzer ein Fehlerbildschirm angezeigt:</span><span class="sxs-lookup"><span data-stu-id="1e33a-156">An error screen will then be shown to the user:</span></span>

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
