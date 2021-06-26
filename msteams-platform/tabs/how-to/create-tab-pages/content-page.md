---
title: Erstellen einer Inhaltsseite
author: surbhigupta
description: Erstellen einer Inhaltsseite
keywords: teams tabs group channel configurable static
localization_priority: Normal
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: d1ec2c0381ba371393a03cda69ffc44a5f49924e
ms.sourcegitcommit: 4d9d1542e04abacfb252511c665a7229d8bb7162
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/25/2021
ms.locfileid: "53140201"
---
# <a name="create-a-content-page-for-your-tab"></a><span data-ttu-id="fde7a-104">Erstellen einer Inhaltsseite für Ihre Registerkarte</span><span class="sxs-lookup"><span data-stu-id="fde7a-104">Create a content page for your tab</span></span>

<span data-ttu-id="fde7a-105">Eine Inhaltsseite ist eine Webseite, die im Teams-Client gerendert wird.</span><span class="sxs-lookup"><span data-stu-id="fde7a-105">A content page is a webpage that is rendered within the Teams client.</span></span> <span data-ttu-id="fde7a-106">Diese sind Teil von:</span><span class="sxs-lookup"><span data-stu-id="fde7a-106">These are part of:</span></span>

* <span data-ttu-id="fde7a-107">Eine benutzerdefinierte Registerkarte mit persönlichem Bereich: In diesem Fall ist die Inhaltsseite die erste Seite, auf die der Benutzer trifft.</span><span class="sxs-lookup"><span data-stu-id="fde7a-107">A personal-scoped custom tab: In this case, the content page is the first page the user encounters.</span></span>
* <span data-ttu-id="fde7a-108">Eine benutzerdefinierte Kanal- oder Gruppenregisterkarte: Die Inhaltsseite wird angezeigt, nachdem der Benutzer die Registerkarte im entsprechenden Kontext angeheftet und konfiguriert hat.</span><span class="sxs-lookup"><span data-stu-id="fde7a-108">A channel or group custom tab: The content page is displayed after the user pins and configures the tab in the appropriate context.</span></span>
* <span data-ttu-id="fde7a-109">Ein [Aufgabenmodul:](~/task-modules-and-cards/what-are-task-modules.md)Sie können eine Inhaltsseite erstellen und als Webansicht in ein Aufgabenmodul einbetten.</span><span class="sxs-lookup"><span data-stu-id="fde7a-109">A [task module](~/task-modules-and-cards/what-are-task-modules.md): You can create a content page and embed it as a webview inside a task module.</span></span> <span data-ttu-id="fde7a-110">Die Seite wird innerhalb des modalen Popups gerendert.</span><span class="sxs-lookup"><span data-stu-id="fde7a-110">The page is rendered inside the modal pop-up.</span></span>

<span data-ttu-id="fde7a-111">Dieser Artikel ist spezifisch für die Verwendung von Inhaltsseiten als Registerkarten. Der Großteil der hier aufgeführten Anleitungen gilt jedoch unabhängig davon, wie die Inhaltsseite dem Benutzer angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="fde7a-111">This article is specific to using content pages as tabs; however the majority of the guidance here applies regardless of how the content page is presented to the user.</span></span>

## <a name="tab-content-and-design-guidelines"></a><span data-ttu-id="fde7a-112">Registerkarteninhalte und Entwurfsrichtlinien</span><span class="sxs-lookup"><span data-stu-id="fde7a-112">Tab content and design guidelines</span></span>

<span data-ttu-id="fde7a-113">Das übergeordnete Ziel Ihrer Registerkarte besteht darin, den Zugriff auf aussagekräftige und ansprechende Inhalte zu ermöglichen, die einen praktischen Nutzen und einen offensichtlichen Zweck haben.</span><span class="sxs-lookup"><span data-stu-id="fde7a-113">Your tab's overall objective is to provide access to meaningful and engaging content that has practical value and an evident purpose.</span></span> <span data-ttu-id="fde7a-114">Sie müssen sich darauf konzentrieren, das Registerkartendesign übersichtlich, navigations intuitiv und inhaltssiv zu gestalten.</span><span class="sxs-lookup"><span data-stu-id="fde7a-114">You must focus on making your tab design clean, navigation intuitive, and content immersive.</span></span>

<span data-ttu-id="fde7a-115">Weitere Informationen finden Sie in den Richtlinien für das [Registerkartendesign](~/tabs/design/tabs.md) und [Microsoft Teams Richtlinien für die Speichervalidierung.](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md)</span><span class="sxs-lookup"><span data-stu-id="fde7a-115">For more information, see [tab design guidelines](~/tabs/design/tabs.md) and [Microsoft Teams store validation guidelines](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md).</span></span>

## <a name="integrate-your-code-with-teams"></a><span data-ttu-id="fde7a-116">Integrieren von Code in Teams</span><span class="sxs-lookup"><span data-stu-id="fde7a-116">Integrate your code with Teams</span></span>

<span data-ttu-id="fde7a-117">Damit Ihre Seite in Teams angezeigt werden kann, müssen Sie das [Microsoft Teams JavaScript-Client-SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) und einen Aufruf nach `microsoftTeams.initialize()` dem Laden der Seite einschließen.</span><span class="sxs-lookup"><span data-stu-id="fde7a-117">For your page to display in Teams, you must include the [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest&preserve-view=true) and include a call to `microsoftTeams.initialize()` after your page loads.</span></span> 

<span data-ttu-id="fde7a-118">Der folgende Code enthält ein Beispiel dafür, wie Ihre Seite und der Teams-Client kommunizieren:</span><span class="sxs-lookup"><span data-stu-id="fde7a-118">The following code provides an example of how your page and the Teams client communicate:</span></span>

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

## <a name="access-additional-content"></a><span data-ttu-id="fde7a-119">Zugreifen auf zusätzliche Inhalte</span><span class="sxs-lookup"><span data-stu-id="fde7a-119">Access additional content</span></span>

<span data-ttu-id="fde7a-120">Sie können mithilfe des SDK auf zusätzliche Inhalte zugreifen, um mit Teams zu interagieren, Deep-Links zu erstellen, Aufgabenmodule zu verwenden und zu überprüfen, ob URL-Domänen im Array enthalten `validDomains` sind.</span><span class="sxs-lookup"><span data-stu-id="fde7a-120">You can access additional content by using the SDK to interact with Teams, creating deep links, using task modules, and verifying if URL domains are included in the `validDomains` array.</span></span>

### <a name="use-the-sdk-to-interact-with-teams"></a><span data-ttu-id="fde7a-121">Verwenden des SDK für die Interaktion mit Teams</span><span class="sxs-lookup"><span data-stu-id="fde7a-121">Use the SDK to interact with Teams</span></span>

<span data-ttu-id="fde7a-122">Das [Teams-Client-JavaScript-SDK](~/tabs/how-to/using-teams-client-sdk.md) bietet viele zusätzliche Funktionen, die Sie beim Entwickeln Ihrer Inhaltsseite hilfreich finden können.</span><span class="sxs-lookup"><span data-stu-id="fde7a-122">The [Teams client JavaScript SDK](~/tabs/how-to/using-teams-client-sdk.md) provides many additional functions that you can find useful while developing your content page.</span></span>

### <a name="deep-links"></a><span data-ttu-id="fde7a-123">Deep-Links</span><span class="sxs-lookup"><span data-stu-id="fde7a-123">Deep links</span></span>

<span data-ttu-id="fde7a-124">Sie können Deep-Links zu Entitäten in Teams erstellen.</span><span class="sxs-lookup"><span data-stu-id="fde7a-124">You can create deep links to entities in Teams.</span></span> <span data-ttu-id="fde7a-125">Diese werden verwendet, um Links zu erstellen, die zu Inhalten und Informationen auf Ihrer Registerkarte navigieren. Weitere Informationen finden Sie unter [Erstellen von Deep-Links zu Inhalten und Features in Teams.](~/concepts/build-and-test/deep-links.md)</span><span class="sxs-lookup"><span data-stu-id="fde7a-125">These are used to create links that navigate to content and information within your tab. For more information, see [create deep links to content and features in Teams](~/concepts/build-and-test/deep-links.md).</span></span>

### <a name="task-modules"></a><span data-ttu-id="fde7a-126">Aufgabenmodule</span><span class="sxs-lookup"><span data-stu-id="fde7a-126">Task modules</span></span>

<span data-ttu-id="fde7a-127">Ein Aufgabenmodul ist eine modale Popupoberfläche, die Sie von Ihrer Registerkarte aus auslösen können. Auf einer Inhaltsseite können Sie Aufgabenmodule verwenden, um Formulare zum Sammeln zusätzlicher Informationen, zum Anzeigen der Details eines Elements in einer Liste oder zum Darstellen zusätzlicher Informationen für den Benutzer anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="fde7a-127">A task module is a modal pop-up experience that you can trigger from your tab. In a content page, you can use task modules to present forms for gathering additional information, displaying the details of an item in a list, or presenting the user with additional information.</span></span> <span data-ttu-id="fde7a-128">Die Aufgabenmodule selbst können zusätzliche Inhaltsseiten sein oder vollständig mit adaptiven Karten erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="fde7a-128">The task modules themselves can be additional content pages, or created completely using Adaptive Cards.</span></span> <span data-ttu-id="fde7a-129">Weitere Informationen finden Sie unter [Verwenden von Aufgabenmodulen in Registerkarten.](~/task-modules-and-cards/task-modules/task-modules-tabs.md)</span><span class="sxs-lookup"><span data-stu-id="fde7a-129">For more information, see [using task modules in tabs](~/task-modules-and-cards/task-modules/task-modules-tabs.md).</span></span>

### <a name="valid-domains"></a><span data-ttu-id="fde7a-130">Gültige Domänen</span><span class="sxs-lookup"><span data-stu-id="fde7a-130">Valid domains</span></span>

<span data-ttu-id="fde7a-131">Stellen Sie sicher, dass alle URL-Domänen, die in Ihren Registerkarten verwendet werden, im `validDomains` Array ihres [Manifests](~/concepts/build-and-test/apps-package.md)enthalten sind.</span><span class="sxs-lookup"><span data-stu-id="fde7a-131">Ensure that all URL domains used in your tabs are included in the `validDomains` array in your [manifest](~/concepts/build-and-test/apps-package.md).</span></span> <span data-ttu-id="fde7a-132">Weitere Informationen finden Sie unter ["validDomains"](~/resources/schema/manifest-schema.md#validdomains) in der Manifestschemareferenz.</span><span class="sxs-lookup"><span data-stu-id="fde7a-132">For more information, see [validDomains](~/resources/schema/manifest-schema.md#validdomains) in the manifest schema reference.</span></span>

> [!NOTE]
> <span data-ttu-id="fde7a-133">Die Kernfunktionalität Ihrer Registerkarte befindet sich innerhalb Teams und nicht außerhalb von Teams.</span><span class="sxs-lookup"><span data-stu-id="fde7a-133">The core functionality of your tab exists within Teams and not outside of Teams.</span></span>

## <a name="show-a-native-loading-indicator"></a><span data-ttu-id="fde7a-134">Anzeigen einer systemeigenen Ladeanzeige</span><span class="sxs-lookup"><span data-stu-id="fde7a-134">Show a native loading indicator</span></span>

<span data-ttu-id="fde7a-135">Ab [Manifestschema v1.7](../../../resources/schema/manifest-schema.md)können Sie eine [systemeigene Ladeanzeige](../../../resources/schema/manifest-schema.md#showloadingindicator)bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="fde7a-135">Starting with [manifest schema v1.7](../../../resources/schema/manifest-schema.md), you can provide a [native loading indicator](../../../resources/schema/manifest-schema.md#showloadingindicator).</span></span> <span data-ttu-id="fde7a-136">Beispiel: [Registerkarteninhaltsseite,](#integrate-your-code-with-teams) [Konfigurationsseite,](configuration-page.md) [Entfernungsseite](removal-page.md)und [Aufgabenmodule in Registerkarten.](../../../task-modules-and-cards/task-modules/task-modules-tabs.md)</span><span class="sxs-lookup"><span data-stu-id="fde7a-136">For example, [tab content page](#integrate-your-code-with-teams), [configuration page](configuration-page.md), [removal page](removal-page.md), and [task modules in tabs](../../../task-modules-and-cards/task-modules/task-modules-tabs.md).</span></span>

> [!NOTE]
> * <span data-ttu-id="fde7a-137">Das Verhalten auf mobilen Clients kann nicht über die systemeigene Ladeindikatoreigenschaft konfiguriert werden.</span><span class="sxs-lookup"><span data-stu-id="fde7a-137">The behavior on mobile clients is not configurable through the native loading indicator property.</span></span> <span data-ttu-id="fde7a-138">Mobile Clients zeigen diesen Indikator standardmäßig auf Inhaltsseiten und iframebasierten Aufgabenmodulen an.</span><span class="sxs-lookup"><span data-stu-id="fde7a-138">Mobile clients show this indicator by default across content pages and iframe-based task modules.</span></span> <span data-ttu-id="fde7a-139">Dieser Indikator wird auf mobilen Geräten angezeigt, wenn eine Anforderung zum Abrufen von Inhalten gestellt wird, und wird geschlossen, sobald die Anforderung abgeschlossen ist.</span><span class="sxs-lookup"><span data-stu-id="fde7a-139">This indicator on mobile is shown when a request is made to fetch content and gets dismissed as soon as the request gets completed.</span></span>

<span data-ttu-id="fde7a-140">Wenn Sie `showLoadingIndicator : true`  in Ihrem App-Manifest angeben, müssen alle Registerkartenkonfigurations-, Inhalts- und Entfernungsseiten und alle iframebasierten Aufgabenmodule die folgenden Schritte ausführen:</span><span class="sxs-lookup"><span data-stu-id="fde7a-140">If you indicate `showLoadingIndicator : true`  in your app manifest, then all tab configuration, content, and removal pages and all iframe-based task modules must follow these steps:</span></span>

<span data-ttu-id="fde7a-141">**So zeigen Sie die Ladeanzeige an**</span><span class="sxs-lookup"><span data-stu-id="fde7a-141">**To show the loading indicator**</span></span>

1. <span data-ttu-id="fde7a-142">Zu `"showLoadingIndicator": true` Ihrem Manifest hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="fde7a-142">Add `"showLoadingIndicator": true` to your manifest.</span></span>
1. <span data-ttu-id="fde7a-143">Aufrufen von `microsoftTeams.initialize();`</span><span class="sxs-lookup"><span data-stu-id="fde7a-143">Call `microsoftTeams.initialize();`.</span></span>
1. <span data-ttu-id="fde7a-144">Rufen Sie als **obligatorischen** Schritt `microsoftTeams.appInitialization.notifySuccess()` Teams auf, dass Ihre App erfolgreich geladen wurde.</span><span class="sxs-lookup"><span data-stu-id="fde7a-144">As a **mandatory** step, call `microsoftTeams.appInitialization.notifySuccess()` to notify Teams that your app has successfully loaded.</span></span> <span data-ttu-id="fde7a-145">Teams blendet dann ggf. die Ladeanzeige aus.</span><span class="sxs-lookup"><span data-stu-id="fde7a-145">Teams then hides the loading indicator, if applicable.</span></span> <span data-ttu-id="fde7a-146">Wenn `notifySuccess`  die App nicht innerhalb von 30 Sekunden aufgerufen wird, wird davon ausgegangen, dass ein Timeout für Ihre App aufgetreten ist und ein Fehlerbildschirm mit einer Wiederholungsoption angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="fde7a-146">If `notifySuccess`  is not called within 30 seconds, it is assumed that your app timed out and an error screen with a retry option appears.</span></span>
1. <span data-ttu-id="fde7a-147">**Optional** können Sie, wenn Sie bereit sind, auf dem Bildschirm zu drucken und den restlichen Inhalt Der Anwendung zu laden, die Ladeanzeige manuell ausblenden, indem Sie `microsoftTeams.appInitialization.notifyAppLoaded();` aufrufen.</span><span class="sxs-lookup"><span data-stu-id="fde7a-147">**Optionally**, if you are ready to print to the screen and wish to lazy load the rest of your application's content, you can manually hide the loading indicator by calling `microsoftTeams.appInitialization.notifyAppLoaded();`.</span></span>
1. <span data-ttu-id="fde7a-148">Wenn die Anwendung nicht geladen werden kann, können Sie Teams mitteilen, `microsoftTeams.appInitialization.notifyFailure(reason);` dass ein Fehler aufgetreten ist.</span><span class="sxs-lookup"><span data-stu-id="fde7a-148">If your application fails to load, you can call `microsoftTeams.appInitialization.notifyFailure(reason);` to let Teams know there was an error.</span></span> <span data-ttu-id="fde7a-149">Dem Benutzer wird ein Fehlerbildschirm angezeigt.</span><span class="sxs-lookup"><span data-stu-id="fde7a-149">An error screen is shown to the user.</span></span> <span data-ttu-id="fde7a-150">Der folgende Code enthält ein Beispiel für Anwendungsfehlerursachen:</span><span class="sxs-lookup"><span data-stu-id="fde7a-150">The following code provides an example of application failure reasons:</span></span>

    ```typescript
    /* List of failure reasons */
    export const enum FailedReason {
        AuthFailed = "AuthFailed",
        Timeout = "Timeout",
        Other = "Other"
    }
    ```

## <a name="see-also"></a><span data-ttu-id="fde7a-151">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="fde7a-151">See also</span></span>

* [<span data-ttu-id="fde7a-152">registerkarten Teams</span><span class="sxs-lookup"><span data-stu-id="fde7a-152">Teams tabs</span></span>](~/tabs/what-are-tabs.md)
* [<span data-ttu-id="fde7a-153">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="fde7a-153">Prerequisites</span></span>](~/tabs/how-to/tab-requirements.md)
* [<span data-ttu-id="fde7a-154">Erstellen einer persönlichen Registerkarte</span><span class="sxs-lookup"><span data-stu-id="fde7a-154">Create a personal tab</span></span>](~/tabs/how-to/create-personal-tab.md)
* [<span data-ttu-id="fde7a-155">Erstellen einer Kanal- oder Gruppenregisterkarte</span><span class="sxs-lookup"><span data-stu-id="fde7a-155">Create a channel or group tab</span></span>](~/tabs/how-to/create-channel-group-tab.md)
* [<span data-ttu-id="fde7a-156">Erstellen einer Inhaltsseite</span><span class="sxs-lookup"><span data-stu-id="fde7a-156">Create a content page</span></span>](~/tabs/how-to/create-tab-pages/content-page.md)
* [<span data-ttu-id="fde7a-157">Erstellen einer Seite zum Entfernen ihrer Registerkarte</span><span class="sxs-lookup"><span data-stu-id="fde7a-157">Create a removal page for your tab</span></span>](~/tabs/how-to/create-tab-pages/removal-page.md)
* [<span data-ttu-id="fde7a-158">Registerkarten auf mobilen Geräten</span><span class="sxs-lookup"><span data-stu-id="fde7a-158">Tabs on mobile</span></span>](~/tabs/design/tabs-mobile.md)
* [<span data-ttu-id="fde7a-159">Kontext für Ihre Registerkarte erhalten</span><span class="sxs-lookup"><span data-stu-id="fde7a-159">Get context for your tab</span></span>](~/tabs/how-to/access-teams-context.md)
* [<span data-ttu-id="fde7a-160">Erstellen von Registerkarten mit adaptiven Karten</span><span class="sxs-lookup"><span data-stu-id="fde7a-160">Build tabs with Adaptive Cards</span></span>](~/tabs/how-to/build-adaptive-card-tabs.md)
* [<span data-ttu-id="fde7a-161">Aufgeklappte Registerkartenverknüpfung und Phasenansicht</span><span class="sxs-lookup"><span data-stu-id="fde7a-161">Tabs link unfurling and Stage View</span></span>](~/tabs/tabs-link-unfurling.md)
* [<span data-ttu-id="fde7a-162">Registerkarten für Unterhaltungen erstellen</span><span class="sxs-lookup"><span data-stu-id="fde7a-162">Create conversational tabs</span></span>](~/tabs/how-to/conversational-tabs.md)
* [<span data-ttu-id="fde7a-163">Änderungen am Registerkartenrand</span><span class="sxs-lookup"><span data-stu-id="fde7a-163">Tab margin changes</span></span>](~/resources/removing-tab-margins.md)

## <a name="next-step"></a><span data-ttu-id="fde7a-164">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="fde7a-164">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="fde7a-165">Erstellen einer Konfigurationsseite</span><span class="sxs-lookup"><span data-stu-id="fde7a-165">Create a configuration page</span></span>](~/tabs/how-to/create-tab-pages/configuration-page.md)
