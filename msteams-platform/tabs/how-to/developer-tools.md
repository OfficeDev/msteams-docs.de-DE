---
title: Entwicklertools für Microsoft Teams-Registerkarten
description: Beschreibt, wie Sie bei Verwendung des Microsoft Teams-Desktopclients zu den DevTools kommen
ms.topic: how-to
keywords: Devtools debuggen mobile Chrome-Desktop-Client-Entwicklertools
ms.openlocfilehash: 1c540c94adc080d9495097f8e3b427eeb14c56d8
ms.sourcegitcommit: 5b3ba227c2e5e6f7a2c629961993f168da6a504d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2021
ms.locfileid: "51634741"
---
# <a name="devtools-for-microsoft-teams-tabs"></a><span data-ttu-id="e3ce4-104">Entwicklertools für Microsoft Teams-Registerkarten</span><span class="sxs-lookup"><span data-stu-id="e3ce4-104">DevTools for Microsoft Teams tabs</span></span>

<span data-ttu-id="e3ce4-105">Wenn Teams in einem Browser ausgeführt wird, ist es einfach, auf devTools des Browsers zu zugreifen: F12 unter Windows oder Command-Option-I unter MacOS.</span><span class="sxs-lookup"><span data-stu-id="e3ce4-105">When Teams is running in a browser, it is easy to access the browser's DevTools: F12 on Windows or Command-Option-I on MacOS.</span></span> <span data-ttu-id="e3ce4-106">Die DevTools bietet Ihnen Zugriff auf:</span><span class="sxs-lookup"><span data-stu-id="e3ce4-106">The DevTools gives you access to:</span></span>

1. <span data-ttu-id="e3ce4-107">Anzeigen von Konsolenprotokollen.</span><span class="sxs-lookup"><span data-stu-id="e3ce4-107">View console logs.</span></span>
1. <span data-ttu-id="e3ce4-108">Anzeigen oder Ändern von HTML-, CSS- und Netzwerkanforderungen während der Laufzeit.</span><span class="sxs-lookup"><span data-stu-id="e3ce4-108">View or modify HTML, CSS, and network requests during runtime.</span></span>
1. <span data-ttu-id="e3ce4-109">Fügen Sie Ihrem JavaScript-Code Haltepunkte hinzu, und führen Sie interaktives Debuggen aus.</span><span class="sxs-lookup"><span data-stu-id="e3ce4-109">Add breakpoints to your JavaScript code and perform interactive debugging.</span></span>

> [!NOTE]
> <span data-ttu-id="e3ce4-110">Das Feature ist nur auf Desktop- und **Android-Clients verfügbar, Developer Preview** aktiviert wurde.</span><span class="sxs-lookup"><span data-stu-id="e3ce4-110">The feature is only available in desktop and Android clients after **Developer Preview** has been enabled.</span></span> <span data-ttu-id="e3ce4-111">Weitere Informationen finden Sie unter [Aktivieren der Entwicklervorschau](~/resources/dev-preview/developer-preview-intro.md).</span><span class="sxs-lookup"><span data-stu-id="e3ce4-111">For more information, see [How do I enable developer preview](~/resources/dev-preview/developer-preview-intro.md).</span></span>

## <a name="access-devtools-in-the-desktop"></a><span data-ttu-id="e3ce4-112">Zugreifen auf DevTools im Desktop</span><span class="sxs-lookup"><span data-stu-id="e3ce4-112">Access DevTools in the Desktop</span></span>

<span data-ttu-id="e3ce4-113">Obwohl die Webversion und die Desktopversion von Teams nahezu identisch sind, gibt es einige Unterschiede in Bezug auf die Authentifizierung.</span><span class="sxs-lookup"><span data-stu-id="e3ce4-113">While the web version and the desktop version of Teams are almost exactly the same, there are some differences with respect to authentication.</span></span> <span data-ttu-id="e3ce4-114">Manchmal ist die einzige Möglichkeit, herauszufinden, was vor sich geht, die Verwendung der DevTools.</span><span class="sxs-lookup"><span data-stu-id="e3ce4-114">Sometimes the only way to figure out what is going on is to use the DevTools.</span></span> <span data-ttu-id="e3ce4-115">Um DevTools im Desktopclient zu verwenden, müssen Sie:</span><span class="sxs-lookup"><span data-stu-id="e3ce4-115">To use DevTools in the desktop client, you must:</span></span>

1. <span data-ttu-id="e3ce4-116">Stellen Sie sicher, dass Sie die [Entwicklervorschau aktiviert haben.](~/resources/dev-preview/developer-preview-intro.md)</span><span class="sxs-lookup"><span data-stu-id="e3ce4-116">Ensure you have enabled [developer preview](~/resources/dev-preview/developer-preview-intro.md).</span></span>
1. <span data-ttu-id="e3ce4-117">Öffnen Sie eine Registerkarte, damit Sie etwas mit den DevTools überprüfen können.</span><span class="sxs-lookup"><span data-stu-id="e3ce4-117">Open up a tab so you have something to inspect with the DevTools.</span></span>
1. <span data-ttu-id="e3ce4-118">Öffnen Sie devTools auf eine der folgenden Arten:</span><span class="sxs-lookup"><span data-stu-id="e3ce4-118">Open the DevTools in one of the following ways:</span></span>
    * <span data-ttu-id="e3ce4-119">**Windows**: Wählen Sie das Symbol Teams im Desktoptablett aus.</span><span class="sxs-lookup"><span data-stu-id="e3ce4-119">**Windows**: Select the Teams icon in the desktop tray.</span></span>
    * <span data-ttu-id="e3ce4-120">**MacOS**: Wählen Sie das Symbol Teams im Dock aus.</span><span class="sxs-lookup"><span data-stu-id="e3ce4-120">**MacOS**: Select the Teams icon in the Dock.</span></span>
 
   <span data-ttu-id="e3ce4-121">Die folgende Abbildung zeigt DevTools, die ein Element in einem Registerkartenkonfigurationsdialogfeld überprüfen:</span><span class="sxs-lookup"><span data-stu-id="e3ce4-121">The following image shows DevTools inspecting an element in a tab configuration dialog:</span></span>

   ![Tab und DevTools](~/assets/images/dev-preview/tab-and-devtools.png)

## <a name="access-devtools-from-an-android-client"></a><span data-ttu-id="e3ce4-123">Zugreifen auf DevTools über einen Android-Client</span><span class="sxs-lookup"><span data-stu-id="e3ce4-123">Access DevTools from an Android client</span></span>

<span data-ttu-id="e3ce4-124">Sie können devTools auch über den Teams Android-Client aktivieren.</span><span class="sxs-lookup"><span data-stu-id="e3ce4-124">You can also enable the DevTools from the Teams Android client.</span></span> <span data-ttu-id="e3ce4-125">Um DevTools zu aktivieren, müssen Sie:</span><span class="sxs-lookup"><span data-stu-id="e3ce4-125">To enable DevTools, you must:</span></span>

1. <span data-ttu-id="e3ce4-126">Aktivieren Sie [die Entwicklervorschau](~/resources/dev-preview/developer-preview-intro.md).</span><span class="sxs-lookup"><span data-stu-id="e3ce4-126">Enable the [developer preview](~/resources/dev-preview/developer-preview-intro.md).</span></span>
1. <span data-ttu-id="e3ce4-127">Verbinden Sie Ihr Gerät mit Ihrem Desktopcomputer, und richten Sie Ihr Android-Gerät für das [Remotedebubugen ein.](https://developers.google.com/web/tools/chrome-devtools/remote-debugging/)</span><span class="sxs-lookup"><span data-stu-id="e3ce4-127">Connect your device to your desktop computer, and setup your Android device for [remote debugging](https://developers.google.com/web/tools/chrome-devtools/remote-debugging/).</span></span>
1. <span data-ttu-id="e3ce4-128">Öffnen Sie in Ihrem Chrome-Browser `chrome://inspect/#devices` .</span><span class="sxs-lookup"><span data-stu-id="e3ce4-128">In your Chrome browser, open `chrome://inspect/#devices`.</span></span>
1. <span data-ttu-id="e3ce4-129">Wählen **Sie überprüfen** unter der Registerkarte aus, die Sie debuggen möchten, wie in der folgenden Abbildung:</span><span class="sxs-lookup"><span data-stu-id="e3ce4-129">Select **inspect** under the tab you wish to debug, as in the following image:</span></span>

   ![Android DevTools](~/assets/images/android-devtools.png)
