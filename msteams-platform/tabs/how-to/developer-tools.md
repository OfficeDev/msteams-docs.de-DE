---
title: Entwicklertools für Microsoft Teams-Registerkarten
description: Beschreibt, wie Sie bei Verwendung des Microsoft Teams-Desktopclients zu den DevTools kommen
ms.topic: how-to
keywords: Devtools debuggen mobile Chrome-Desktop-Client-Entwicklertools
ms.openlocfilehash: 7bd9403a74fd33619a2f8ac1b4b3a4c74a21175d
ms.sourcegitcommit: 9404c2e3a30887b9e17e0c89b12dd26fd9b8033e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2021
ms.locfileid: "51654390"
---
# <a name="devtools-for-microsoft-teams-tabs"></a><span data-ttu-id="43def-104">Entwicklertools für Microsoft Teams-Registerkarten</span><span class="sxs-lookup"><span data-stu-id="43def-104">DevTools for Microsoft Teams tabs</span></span>

<span data-ttu-id="43def-105">Wenn Teams in einem Browser ausgeführt wird, ist es einfach, auf devTools des Browsers zu zugreifen: F12 unter Windows oder Command-Option-I unter MacOS.</span><span class="sxs-lookup"><span data-stu-id="43def-105">When Teams is running in a browser, it is easy to access the browser's DevTools: F12 on Windows or Command-Option-I on MacOS.</span></span> <span data-ttu-id="43def-106">Die DevTools bietet Ihnen Zugriff auf:</span><span class="sxs-lookup"><span data-stu-id="43def-106">The DevTools gives you access to:</span></span>

1. <span data-ttu-id="43def-107">Anzeigen von Konsolenprotokollen.</span><span class="sxs-lookup"><span data-stu-id="43def-107">View console logs.</span></span>
1. <span data-ttu-id="43def-108">Anzeigen oder Ändern von HTML-, CSS- und Netzwerkanforderungen während der Laufzeit.</span><span class="sxs-lookup"><span data-stu-id="43def-108">View or modify HTML, CSS, and network requests during runtime.</span></span>
1. <span data-ttu-id="43def-109">Fügen Sie Ihrem JavaScript-Code Haltepunkte hinzu, und führen Sie interaktives Debuggen aus.</span><span class="sxs-lookup"><span data-stu-id="43def-109">Add breakpoints to your JavaScript code and perform interactive debugging.</span></span>

> [!NOTE]
> <span data-ttu-id="43def-110">Das Feature ist nur für Desktop- und **Android-Clients** verfügbar, nachdem Developer Preview aktiviert wurde.</span><span class="sxs-lookup"><span data-stu-id="43def-110">The feature is only available for desktop and Android clients after the **Developer Preview** has been enabled.</span></span> <span data-ttu-id="43def-111">Weitere Informationen finden Sie unter [Aktivieren der Entwicklervorschau](~/resources/dev-preview/developer-preview-intro.md).</span><span class="sxs-lookup"><span data-stu-id="43def-111">For more information, see [How do I enable developer preview](~/resources/dev-preview/developer-preview-intro.md).</span></span>

## <a name="access-devtools-in-the-desktop"></a><span data-ttu-id="43def-112">Zugreifen auf DevTools im Desktop</span><span class="sxs-lookup"><span data-stu-id="43def-112">Access DevTools in the Desktop</span></span>

<span data-ttu-id="43def-113">Obwohl die Webversion und die Desktopversion von Teams nahezu identisch sind, gibt es einige Unterschiede in Bezug auf die Authentifizierung.</span><span class="sxs-lookup"><span data-stu-id="43def-113">While the web version and the desktop version of Teams are almost the same, there are some differences concerning authentication.</span></span> <span data-ttu-id="43def-114">Manchmal ist die einzige Möglichkeit, herauszufinden, was vor sich geht, die Verwendung der DevTools.</span><span class="sxs-lookup"><span data-stu-id="43def-114">Sometimes the only way to figure out what is going on is to use the DevTools.</span></span> <span data-ttu-id="43def-115">Um DevTools im Desktopclient zu verwenden, müssen Sie:</span><span class="sxs-lookup"><span data-stu-id="43def-115">To use DevTools in the desktop client, you must:</span></span>

1. <span data-ttu-id="43def-116">Stellen Sie sicher, dass Sie die [Entwicklervorschau aktiviert haben.](~/resources/dev-preview/developer-preview-intro.md)</span><span class="sxs-lookup"><span data-stu-id="43def-116">Ensure you have enabled [developer preview](~/resources/dev-preview/developer-preview-intro.md).</span></span>
1. <span data-ttu-id="43def-117">Öffnen Sie eine Registerkarte, damit Sie etwas mit den DevTools überprüfen können.</span><span class="sxs-lookup"><span data-stu-id="43def-117">Open up a tab so you have something to inspect with the DevTools.</span></span>
1. <span data-ttu-id="43def-118">Öffnen Sie devTools auf eine der folgenden Arten:</span><span class="sxs-lookup"><span data-stu-id="43def-118">Open the DevTools in one of the following ways:</span></span>
    * <span data-ttu-id="43def-119">**Windows**: Wählen Sie das Symbol Teams im Desktoptablett aus.</span><span class="sxs-lookup"><span data-stu-id="43def-119">**Windows**: Select the Teams icon in the desktop tray.</span></span>
    * <span data-ttu-id="43def-120">**macOS**: Wählen Sie das Symbol Teams im Dock aus.</span><span class="sxs-lookup"><span data-stu-id="43def-120">**macOS**: Select the Teams icon in the Dock.</span></span>
 
   <span data-ttu-id="43def-121">Die folgende Abbildung zeigt DevTools, die ein Element in einem Registerkartenkonfigurationsdialogfeld überprüfen:</span><span class="sxs-lookup"><span data-stu-id="43def-121">The following image shows DevTools inspecting an element in a tab configuration dialog:</span></span>

   ![Tab und DevTools](~/assets/images/dev-preview/tab-and-devtools.png)

## <a name="access-devtools-from-an-android-client"></a><span data-ttu-id="43def-123">Zugreifen auf DevTools über einen Android-Client</span><span class="sxs-lookup"><span data-stu-id="43def-123">Access DevTools from an Android client</span></span>

<span data-ttu-id="43def-124">Sie können devTools auch über den Teams Android-Client aktivieren.</span><span class="sxs-lookup"><span data-stu-id="43def-124">You can also enable the DevTools from the Teams Android client.</span></span> <span data-ttu-id="43def-125">Um DevTools zu aktivieren, müssen Sie:</span><span class="sxs-lookup"><span data-stu-id="43def-125">To enable DevTools, you must:</span></span>

1. <span data-ttu-id="43def-126">Aktivieren Sie [die Entwicklervorschau](~/resources/dev-preview/developer-preview-intro.md).</span><span class="sxs-lookup"><span data-stu-id="43def-126">Enable the [developer preview](~/resources/dev-preview/developer-preview-intro.md).</span></span>
1. <span data-ttu-id="43def-127">Verbinden Sie Ihr Gerät mit Ihrem Desktopcomputer, und richten Sie Ihr Android-Gerät für das [Remotedebugen ein.](https://developers.google.com/web/tools/chrome-devtools/remote-debugging/)</span><span class="sxs-lookup"><span data-stu-id="43def-127">Connect your device to your desktop computer, and set up your Android device for [remote debugging](https://developers.google.com/web/tools/chrome-devtools/remote-debugging/).</span></span>
1. <span data-ttu-id="43def-128">Öffnen Sie in Ihrem Chrome-Browser `chrome://inspect/#devices` .</span><span class="sxs-lookup"><span data-stu-id="43def-128">In your Chrome browser, open `chrome://inspect/#devices`.</span></span>
1. <span data-ttu-id="43def-129">Wählen **Sie überprüfen** unter der Registerkarte aus, die Sie debuggen möchten, wie in der folgenden Abbildung:</span><span class="sxs-lookup"><span data-stu-id="43def-129">Select **inspect** under the tab you wish to debug, as in the following image:</span></span>

   ![Android DevTools](~/assets/images/android-devtools.png)
