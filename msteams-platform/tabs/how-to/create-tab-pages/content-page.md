---
title: Erstellen einer Inhaltsseite
author: laujan
description: Vorgehensweise Erstellen einer Inhaltsseite
keywords: Teams-Registerkartengruppe Kanal konfigurierbar statisch
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 62a398c87b681013c89e540d2bdc463c97877307
ms.sourcegitcommit: 3fc7ad33e2693f07170c3cb1a0d396261fc5c619
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/29/2020
ms.locfileid: "48796316"
---
# <a name="create-a-content-page-for-your-tab"></a><span data-ttu-id="18399-104">Erstellen einer Inhaltsseite für die Registerkarte</span><span class="sxs-lookup"><span data-stu-id="18399-104">Create a content page for your tab</span></span>

<span data-ttu-id="18399-105">Eine Inhaltsseite ist eine Webseite, die im Microsoft Teams-Client gerendert wird.</span><span class="sxs-lookup"><span data-stu-id="18399-105">A content page is a webpage that is rendered within the Teams client.</span></span> <span data-ttu-id="18399-106">Diese sind in der Regel Bestandteil von:</span><span class="sxs-lookup"><span data-stu-id="18399-106">Typically these are part of:</span></span>

* <span data-ttu-id="18399-107">Eine benutzerdefinierte Registerkarte auf persönlicher Ebene – in dieser Instanz ist die Inhaltsseite die erste Seite, auf die der Benutzer stößt.</span><span class="sxs-lookup"><span data-stu-id="18399-107">A personal-scoped custom tab - In this instance the content page is the first page the user encounters.</span></span>
* <span data-ttu-id="18399-108">Eine benutzerdefinierte Kanal/Gruppe-Registerkarte – nachdem der Benutzer die Registerkarte im entsprechenden Kontext fixiert und konfiguriert hat, wird die Inhaltsseite angezeigt.</span><span class="sxs-lookup"><span data-stu-id="18399-108">A channel/group custom tab - After the user pins and configures the tab in the appropriate context, the content page is displayed.</span></span>
* <span data-ttu-id="18399-109">Ein [Aufgabenmodul](~/task-modules-and-cards/what-are-task-modules.md) -Sie können eine Inhaltsseite erstellen und als WebView in ein Aufgabenmodul einbetten.</span><span class="sxs-lookup"><span data-stu-id="18399-109">A [task module](~/task-modules-and-cards/what-are-task-modules.md) - You can create a content page and embed it as a webview inside a task module.</span></span> <span data-ttu-id="18399-110">Die Seite wird innerhalb des modalen Popups gerendert.</span><span class="sxs-lookup"><span data-stu-id="18399-110">The page will be rendered inside the modal popup.</span></span>

<span data-ttu-id="18399-111">Dieser Artikel ist spezifisch für die Verwendung von Inhaltsseiten als Registerkarten; Allerdings würde der Großteil der Anleitung hier angewendet, unabhängig davon, wie die Inhaltsseite dem Endbenutzer angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="18399-111">This article is specific to using content pages as tabs; however the majority of the guidance here would apply regardless of how the content page is presented to the end-user.</span></span>

## <a name="tab-content-and-style-guidelines"></a><span data-ttu-id="18399-112">Inhalts-und Stilrichtlinien für Registerkarten</span><span class="sxs-lookup"><span data-stu-id="18399-112">Tab content and style guidelines</span></span>

<span data-ttu-id="18399-113">Das allgemeine Ziel ihrer Registerkarte sollte es sein, den Zugriff auf aussagekräftige und ansprechende Inhalte zu ermöglichen, die einen praktischen Nutzen und einen offensichtlichen Zweck haben.</span><span class="sxs-lookup"><span data-stu-id="18399-113">Your tab's overall objective should be to provide access to meaningful and engaging content that has a practical value and an evident purpose.</span></span> <span data-ttu-id="18399-114">Das bedeutet nicht, dass Sie auf eine erfreuliche Art verzichten sollten, aber Sie sollten sich darauf konzentrieren, die Übersichtlichkeit zu minimieren, indem Sie das Design Ihrer Registerkarte sauber, die Navigation intuitiv und die Inhalte immersive machen.</span><span class="sxs-lookup"><span data-stu-id="18399-114">That does not mean that you should forego a pleasing style, but you should focus on minimizing clutter by making your tab design clean, navigation intuitive, and content immersive.</span></span> <span data-ttu-id="18399-115">Informationen [zu Inhalten und Unterhaltungen auf einmal mithilfe von Tabs](~/tabs/design/tabs.md) und [Microsoft Teams-App-Genehmigungsprozess Anleitungen](~/concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md)</span><span class="sxs-lookup"><span data-stu-id="18399-115">See [Content and conversations, all at once using tabs](~/tabs/design/tabs.md) and [Microsoft Teams app approval process guidance](~/concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md)</span></span>

## <a name="integrate-your-code-with-teams"></a><span data-ttu-id="18399-116">Integrieren von Code in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="18399-116">Integrate your code with Teams</span></span>

<span data-ttu-id="18399-117">Damit Ihre Seite in Teams angezeigt wird, müssen Sie das [Microsoft Teams-JavaScript-Client-SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latestadd &preserve-view=true) einschließen und nach dem Laden einer Seite einen Anruf hinzufügen `microsoftTeams.initialize()` .</span><span class="sxs-lookup"><span data-stu-id="18399-117">For your page to display in Teams, you must include the [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latestadd &preserve-view=true) and include a call to `microsoftTeams.initialize()` after your page loads.</span></span> <span data-ttu-id="18399-118">So kommunizieren Ihre Seite und der Microsoft Teams-Client:</span><span class="sxs-lookup"><span data-stu-id="18399-118">That is how your page and the Teams client communicate:</span></span>

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

## <a name="accessing-additional-content"></a><span data-ttu-id="18399-119">Zugreifen auf zusätzlichen Inhalt</span><span class="sxs-lookup"><span data-stu-id="18399-119">Accessing additional content</span></span>

### <a name="using-the-sdk-to-interact-with-teams"></a><span data-ttu-id="18399-120">Verwenden des SDK für die Interaktion mit Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="18399-120">Using the SDK to interact with Teams</span></span>

<span data-ttu-id="18399-121">Das Microsoft [Teams-Client-JavaScript-SDK](~/tabs/how-to/using-teams-client-sdk.md) bietet viele zusätzliche Funktionen, die Sie beim Entwickeln Ihrer Inhaltsseite nützlich finden können.</span><span class="sxs-lookup"><span data-stu-id="18399-121">The [Teams client JavaScript SDK](~/tabs/how-to/using-teams-client-sdk.md) provides many additional functions you may find useful while developing your content page.</span></span>

### <a name="deep-links"></a><span data-ttu-id="18399-122">Deep-Links</span><span class="sxs-lookup"><span data-stu-id="18399-122">Deep links</span></span>

<span data-ttu-id="18399-123">Sie können tiefe Links zu Entitäten in Microsoft Teams erstellen.</span><span class="sxs-lookup"><span data-stu-id="18399-123">You can create deep links to entities in Teams.</span></span> <span data-ttu-id="18399-124">Diese werden normalerweise verwendet, um Links zu erstellen, die zu Inhalten und Informationen in ihrer Registerkarte navigieren. Weitere Informationen finden Sie unter [Erstellen von tiefen Links zu Inhalten und Features in Microsoft Teams](~/concepts/build-and-test/deep-links.md).</span><span class="sxs-lookup"><span data-stu-id="18399-124">Typically, these are used to create links that navigate to content and information within your tab. See [Create deep links to content and features in Microsoft Teams](~/concepts/build-and-test/deep-links.md).</span></span>

### <a name="task-modules"></a><span data-ttu-id="18399-125">Aufgaben Module</span><span class="sxs-lookup"><span data-stu-id="18399-125">Task Modules</span></span>

<span data-ttu-id="18399-126">Ein Aufgabenmodul ist eine modale Popup-ähnliche Erfahrung, die Sie auf der Registerkarte auslösen können. Normalerweise möchten Sie auf einer Inhaltsseite nicht durch mehrere Seiten navigieren.</span><span class="sxs-lookup"><span data-stu-id="18399-126">A task module is a modal popup-like experience that you can trigger from your tab. Typically in a content page you do not want to navigate your user through multiple pages.</span></span> <span data-ttu-id="18399-127">Stattdessen verwenden Sie Aufgaben Module zum Darstellen von Formularen zum Sammeln zusätzlicher Informationen, zum Anzeigen der Details eines Elements in einer Liste oder zu einem anderen Zeitpunkt, zu dem Sie dem Benutzer zusätzliche Informationen zur Verfügung stellen müssen.</span><span class="sxs-lookup"><span data-stu-id="18399-127">Instead, you will use task modules to present forms for gathering additional information, displaying the details of an item in a list, or any other time you need to present the user with additional information.</span></span> <span data-ttu-id="18399-128">Die Aufgaben Module selbst können zusätzliche Inhaltsseiten sein oder vollständig mit adaptiven Karten erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="18399-128">The task modules themselves can be additional content pages, or created completely using Adaptive Cards.</span></span> <span data-ttu-id="18399-129">Vollständige Informationen finden Sie unter [Verwenden von Aufgaben Modulen in Registerkarten](~/task-modules-and-cards/task-modules/task-modules-tabs.md) .</span><span class="sxs-lookup"><span data-stu-id="18399-129">See [Using task modules in tabs](~/task-modules-and-cards/task-modules/task-modules-tabs.md) for complete information.</span></span>

### <a name="valid-domains"></a><span data-ttu-id="18399-130">Gültige Domänen</span><span class="sxs-lookup"><span data-stu-id="18399-130">Valid Domains</span></span>

<span data-ttu-id="18399-131">Stellen Sie sicher, dass die in ihren Registerkarten verwendeten URL-Domänen in dem `validDomains` Array in Ihrem [Manifest](~/concepts/build-and-test/apps-package.md)enthalten sind.</span><span class="sxs-lookup"><span data-stu-id="18399-131">Ensure that the all URL domains used in your tabs are included in the `validDomains` array in your [manifest](~/concepts/build-and-test/apps-package.md).</span></span> <span data-ttu-id="18399-132">Weitere Informationen finden Sie unter [validDomains](~/resources/schema/manifest-schema.md#validdomains) in der Manifest-Schemareferenz.</span><span class="sxs-lookup"><span data-stu-id="18399-132">For more information, see [validDomains](~/resources/schema/manifest-schema.md#validdomains) in the manifest schema reference.</span></span> <span data-ttu-id="18399-133">Beachten Sie jedoch, dass die Kernfunktionen Ihrer Registerkarte in Microsoft Teams und nicht außerhalb von Teams vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="18399-133">However, be mindful that the core functionality of your tab exists within Teams and not outside of Teams.</span></span>

## <a name="show-a-native-loading-indicator"></a><span data-ttu-id="18399-134">Anzeigen eines systemeigenen Lade Indikators</span><span class="sxs-lookup"><span data-stu-id="18399-134">Show a native loading indicator</span></span>

<span data-ttu-id="18399-135">Beginnend mit dem [Manifest-Schema v 1.7](../../../resources/schema/manifest-schema.md)können Sie einen [systemeigenen Lade Indikator](../../../resources/schema/manifest-schema.md#showloadingindicator) bereitstellen, unabhängig davon, wo Ihre Webinhalte in Microsoft Teams geladen werden, beispielsweise [Registerkarteninhalts Seite](#integrate-your-code-with-teams), [Konfigurationsseite](configuration-page.md), [Entfernungs Seite](removal-page.md) und [Aufgaben Module in Registerkarten](../../../task-modules-and-cards/task-modules/task-modules-tabs.md).</span><span class="sxs-lookup"><span data-stu-id="18399-135">Starting with [manifest schema v1.7](../../../resources/schema/manifest-schema.md), you can provide a [native loading indicator](../../../resources/schema/manifest-schema.md#showloadingindicator) wherever your web content is loaded in Teams, e.g., [tab content page](#integrate-your-code-with-teams), [configuration page](configuration-page.md), [removal page](removal-page.md) and [task modules in tabs](../../../task-modules-and-cards/task-modules/task-modules-tabs.md).</span></span>

> [!NOTE]
> <span data-ttu-id="18399-136">Wenn Sie  `"showLoadingIndicator : true`  in Ihrem App-Manifest angeben, müssen alle Seiten für Registerkartenkonfiguration, Inhalt und Entfernung sowie alle IFRAME-basierten Aufgaben Module dem obligatorischen Protokoll unten entsprechen:</span><span class="sxs-lookup"><span data-stu-id="18399-136">If you indicate  `"showLoadingIndicator : true`  in your app manifest, then all tab configuration, content, and removal pages and all iframe-based task modules must follow the mandatory protocol, below:</span></span>

1. <span data-ttu-id="18399-137">Um den Lade Indikator anzuzeigen, fügen Sie `"showLoadingIndicator": true` zu ihrem Manifest hinzu.</span><span class="sxs-lookup"><span data-stu-id="18399-137">To show the loading indicator, add `"showLoadingIndicator": true` to your manifest.</span></span> 
2. <span data-ttu-id="18399-138">Denken Sie daran, anzurufen `microsoftTeams.initialize();` .</span><span class="sxs-lookup"><span data-stu-id="18399-138">Remember to call `microsoftTeams.initialize();`.</span></span>
3. <span data-ttu-id="18399-139">**Optional** .</span><span class="sxs-lookup"><span data-stu-id="18399-139">**Optional** .</span></span> <span data-ttu-id="18399-140">Wenn Sie zum Drucken auf dem Bildschirm und zum verzögerten Laden des restlichen Inhalts Ihrer Anwendung fähig sind, können Sie den Lade Indikator manuell ausblenden, indem Sie `microsoftTeams.appInitialization.notifyAppLoaded();`</span><span class="sxs-lookup"><span data-stu-id="18399-140">If you're ready to print to the screen and wish to lazy load the rest of your application's content, you can manually hide the loading indicator by calling `microsoftTeams.appInitialization.notifyAppLoaded();`</span></span>
4. <span data-ttu-id="18399-141">**Obligatorisch** .</span><span class="sxs-lookup"><span data-stu-id="18399-141">**Mandatory** .</span></span> <span data-ttu-id="18399-142">Schließlich rufen Sie die Teams darauf hin `microsoftTeams.appInitialization.notifySuccess()` , dass Ihre APP erfolgreich geladen wurde.</span><span class="sxs-lookup"><span data-stu-id="18399-142">Finally, call `microsoftTeams.appInitialization.notifySuccess()` to notify Teams that your app has successfully loaded.</span></span> <span data-ttu-id="18399-143">Teams werden dann den Lade Indikator ausblenden, falls zutreffend.</span><span class="sxs-lookup"><span data-stu-id="18399-143">Teams will then hide the loading indicator if applicable.</span></span> <span data-ttu-id="18399-144">Wenn  `notifySuccess`  nicht innerhalb von 30 Sekunden aufgerufen wird, wird davon ausgegangen, dass Ihre APP abgelaufen ist und ein Fehlerbildschirm mit einer Wiederholungsoption angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="18399-144">If  `notifySuccess`  is not called within 30 seconds, it will be assumed that your app timed out and an error screen with a retry option will appear.</span></span>
5. <span data-ttu-id="18399-145">Wenn Ihre Anwendung nicht laden kann, können Sie aufrufen `microsoftTeams.appInitialization.notifyFailure(reason);` , um Microsoft Teams mitzuteilen, dass ein Fehler aufgetreten ist.</span><span class="sxs-lookup"><span data-stu-id="18399-145">If your application fails to load, you can call `microsoftTeams.appInitialization.notifyFailure(reason);` to let Teams know there was an error.</span></span> <span data-ttu-id="18399-146">Dem Benutzer wird dann ein Fehlerbildschirm angezeigt:</span><span class="sxs-lookup"><span data-stu-id="18399-146">An error screen will then be shown to the user:</span></span>

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
