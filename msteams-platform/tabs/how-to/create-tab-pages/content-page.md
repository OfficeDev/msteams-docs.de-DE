---
title: Erstellen einer Inhaltsseite
author: laujan
description: ''
keywords: Teams-Registerkartengruppe Kanal konfigurierbar statisch
ms.topic: conceptual
ms.author: v-laujan
ms.openlocfilehash: ac85e000c9bdaebf28cb33143a7c82a348d3771e
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674332"
---
# <a name="create-a-content-page-for-your-tab"></a><span data-ttu-id="4346d-103">Erstellen einer Inhaltsseite für die Registerkarte</span><span class="sxs-lookup"><span data-stu-id="4346d-103">Create a content page for your tab</span></span>

<span data-ttu-id="4346d-104">Eine Inhaltsseite ist eine Webseite, die im Microsoft Teams-Client gerendert wird.</span><span class="sxs-lookup"><span data-stu-id="4346d-104">A content page is a webpage that is rendered within the Teams client.</span></span> <span data-ttu-id="4346d-105">Diese sind in der Regel Bestandteil von:</span><span class="sxs-lookup"><span data-stu-id="4346d-105">Typically these are part of:</span></span>

* <span data-ttu-id="4346d-106">Eine benutzerdefinierte Registerkarte auf persönlicher Ebene – in dieser Instanz ist die Inhaltsseite die erste Seite, auf die der Benutzer stößt.</span><span class="sxs-lookup"><span data-stu-id="4346d-106">A personal-scoped custom tab - In this instance the content page is the first page the user encounters.</span></span>
* <span data-ttu-id="4346d-107">Eine benutzerdefinierte Kanal/Gruppe-Registerkarte – nachdem der Benutzer die Registerkarte im entsprechenden Kontext fixiert und konfiguriert hat, wird die Inhaltsseite angezeigt.</span><span class="sxs-lookup"><span data-stu-id="4346d-107">A channel/group custom tab - After the user pins and configures the tab in the appropriate context, the content page is displayed.</span></span>
* <span data-ttu-id="4346d-108">Ein [Aufgabenmodul](~/task-modules-and-cards/what-are-task-modules.md) -Sie können eine Inhaltsseite erstellen und als WebView in ein Aufgabenmodul einbetten.</span><span class="sxs-lookup"><span data-stu-id="4346d-108">A [task module](~/task-modules-and-cards/what-are-task-modules.md) - You can create a content page and embed it as a webview inside a task module.</span></span> <span data-ttu-id="4346d-109">Die Seite wird innerhalb des modalen Popups gerendert.</span><span class="sxs-lookup"><span data-stu-id="4346d-109">The page will be rendered inside the modal popup.</span></span>

<span data-ttu-id="4346d-110">Dieser Artikel ist spezifisch für die Verwendung von Inhaltsseiten als Registerkarten; Allerdings würde der Großteil der Anleitung hier angewendet, unabhängig davon, wie die Inhaltsseite dem Endbenutzer angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="4346d-110">This article is specific to using content pages as tabs; however the majority of the guidance here would apply regardless of how the content page is presented to the end-user.</span></span>

## <a name="tab-content-and-style-guidelines"></a><span data-ttu-id="4346d-111">Inhalts-und Stilrichtlinien für Registerkarten</span><span class="sxs-lookup"><span data-stu-id="4346d-111">Tab content and style guidelines</span></span>

<span data-ttu-id="4346d-112">Das allgemeine Ziel ihrer Registerkarte sollte es sein, den Zugriff auf aussagekräftige und ansprechende Inhalte zu ermöglichen, die einen praktischen Nutzen und einen offensichtlichen Zweck haben.</span><span class="sxs-lookup"><span data-stu-id="4346d-112">Your tab's overall objective should be to provide access to meaningful and engaging content that has a practical value and an evident purpose.</span></span> <span data-ttu-id="4346d-113">Das bedeutet nicht, dass Sie auf eine erfreuliche Art verzichten sollten, aber Sie sollten sich darauf konzentrieren, die Übersichtlichkeit zu minimieren, indem Sie das Design Ihrer Registerkarte sauber, die Navigation intuitiv und die Inhalte immersive machen.</span><span class="sxs-lookup"><span data-stu-id="4346d-113">That does not mean that you should forego a pleasing style, but you should focus on minimizing clutter by making your tab design clean, navigation intuitive, and content immersive.</span></span> <span data-ttu-id="4346d-114">Informationen [zu Inhalten und Unterhaltungen auf einmal mithilfe von Tabs](~/tabs/design/tabs.md) und [Microsoft Teams-App-Genehmigungsprozess Anleitungen](~/concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md)</span><span class="sxs-lookup"><span data-stu-id="4346d-114">See [Content and conversations, all at once using tabs](~/tabs/design/tabs.md) and [Microsoft Teams app approval process guidance](~/concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md)</span></span>

## <a name="integrate-your-code-with-teams"></a><span data-ttu-id="4346d-115">Integrieren von Code in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="4346d-115">Integrate your code with Teams</span></span>

<span data-ttu-id="4346d-116">Damit Ihre Seite in Teams angezeigt wird, müssen Sie das [Microsoft Teams-JavaScript-Client-SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest) einschließen und `microsoftTeams.initialize()` nach dem Laden einer Seite einen Anruf hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="4346d-116">For your page to display in Teams, you must include the [Microsoft Teams JavaScript client SDK](/javascript/api/overview/msteams-client?view=msteams-client-js-latest) and include a call to `microsoftTeams.initialize()` after your page loads.</span></span> <span data-ttu-id="4346d-117">So kommunizieren Ihre Seite und der Microsoft Teams-Client:</span><span class="sxs-lookup"><span data-stu-id="4346d-117">That is how your page and the Teams client communicate:</span></span>

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

## <a name="accessing-additional-content"></a><span data-ttu-id="4346d-118">Zugreifen auf zusätzlichen Inhalt</span><span class="sxs-lookup"><span data-stu-id="4346d-118">Accessing additional content</span></span>

### <a name="using-the-sdk-to-interact-with-teams"></a><span data-ttu-id="4346d-119">Verwenden des SDK für die Interaktion mit Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="4346d-119">Using the SDK to interact with Teams</span></span>

<span data-ttu-id="4346d-120">Das Microsoft [Teams-Client-JavaScript-SDK](~/tabs/how-to/using-teams-client-sdk.md) bietet viele zusätzliche Funktionen, die Sie beim Entwickler Ihrer Inhaltsseite möglicherweise nützlich finden.</span><span class="sxs-lookup"><span data-stu-id="4346d-120">The [Teams client JavaScript SDK](~/tabs/how-to/using-teams-client-sdk.md) provides many additional functions you may find useful while developer your content page.</span></span>

### <a name="deep-links"></a><span data-ttu-id="4346d-121">Deep links</span><span class="sxs-lookup"><span data-stu-id="4346d-121">Deep links</span></span>

<span data-ttu-id="4346d-122">Sie können tiefe Links zu Entitäten in Microsoft Teams erstellen.</span><span class="sxs-lookup"><span data-stu-id="4346d-122">You can create deep links to entities in Teams.</span></span> <span data-ttu-id="4346d-123">Diese werden normalerweise verwendet, um Links zu erstellen, die zu Inhalten und Informationen in ihrer Registerkarte navigieren. Weitere Informationen finden Sie unter [Erstellen von tiefen Links zu Inhalten und Features in Microsoft Teams](~/concepts/build-and-test/deep-links.md).</span><span class="sxs-lookup"><span data-stu-id="4346d-123">Typically, these are used to create links that navigate to content and information within your tab. See [Create deep links to content and features in Microsoft Teams](~/concepts/build-and-test/deep-links.md).</span></span>

### <a name="task-modules"></a><span data-ttu-id="4346d-124">Aufgaben Module</span><span class="sxs-lookup"><span data-stu-id="4346d-124">Task Modules</span></span>

<span data-ttu-id="4346d-125">Ein Aufgabenmodul ist eine modale Popup-ähnliche Erfahrung, die Sie auf der Registerkarte auslösen können. in der Regel auf einer Inhaltsseite möchten Sie nicht über mehrere Seiten in den Benutzer navigieren.</span><span class="sxs-lookup"><span data-stu-id="4346d-125">A task module is a modal popup-like experience that you can trigger from your tab. Typically in a content page you do not want to navigate your user through multiple pages.</span></span> <span data-ttu-id="4346d-126">Stattdessen verwenden Sie Aufgaben Module zum Darstellen von Formularen zum Sammeln zusätzlicher Informationen, zum Anzeigen der Details eines Elements in einer Liste oder zu einem anderen Zeitpunkt, zu dem Sie dem Benutzer zusätzliche Informationen zur Verfügung stellen müssen.</span><span class="sxs-lookup"><span data-stu-id="4346d-126">Instead, you will use task modules to present forms for gathering additional information, displaying the details of an item in a list, or any other time you need to present the user with additional information.</span></span> <span data-ttu-id="4346d-127">Die Aufgaben Module selbst können zusätzliche Inhaltsseiten sein oder vollständig mit adaptiven Karten erstellt werden.</span><span class="sxs-lookup"><span data-stu-id="4346d-127">The task modules themselves can be additional content pages, or created completely using Adaptive Cards.</span></span> <span data-ttu-id="4346d-128">Vollständige Informationen finden Sie unter [Verwenden von Aufgaben Modulen in Registerkarten](~/task-modules-and-cards/task-modules/task-modules-tabs.md) .</span><span class="sxs-lookup"><span data-stu-id="4346d-128">See [Using task modules in tabs](~/task-modules-and-cards/task-modules/task-modules-tabs.md) for complete information.</span></span>

### <a name="valid-domains"></a><span data-ttu-id="4346d-129">Gültige Domänen</span><span class="sxs-lookup"><span data-stu-id="4346d-129">Valid Domains</span></span>

<span data-ttu-id="4346d-130">Stellen Sie sicher, dass die in ihren Registerkarten verwendeten URL-Domänen `validDomains` in dem Array in Ihrem [Manifest](~/concepts/build-and-test/apps-package.md)enthalten sind.</span><span class="sxs-lookup"><span data-stu-id="4346d-130">Ensure that the all URL domains used in your tabs are included in the `validDomains` array in your [manifest](~/concepts/build-and-test/apps-package.md).</span></span> <span data-ttu-id="4346d-131">Weitere Informationen finden Sie unter [validDomains](~/resources/schema/manifest-schema.md#validdomains) in der Manifest-Schemareferenz.</span><span class="sxs-lookup"><span data-stu-id="4346d-131">For more information, see [validDomains](~/resources/schema/manifest-schema.md#validdomains) in the manifest schema reference.</span></span> <span data-ttu-id="4346d-132">Beachten Sie jedoch, dass die Kernfunktionen Ihrer Registerkarte in Microsoft Teams und nicht außerhalb von Teams vorhanden sind.</span><span class="sxs-lookup"><span data-stu-id="4346d-132">However, be mindful that the core functionality of your tab exists within Teams and not outside of Teams.</span></span>
