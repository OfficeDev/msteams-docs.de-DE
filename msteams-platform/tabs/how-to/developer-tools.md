---
title: Entwicklertools für Microsoft Teams-Registerkarten
description: Beschreibt, wie Sie bei Verwendung des Microsoft Teams-Desktopclients zu den DevTools kommen
ms.topic: how-to
keywords: Devtools debuggen mobile Chrome-Desktop-Client-Entwicklertools
ms.openlocfilehash: 1bf7d246136a24316309ae144ac9552c5fd4f57d
ms.sourcegitcommit: f5ee3fa5ef6126d9bf845948d27d9067b3bbb994
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2021
ms.locfileid: "51596273"
---
# <a name="devtools-for-microsoft-teams-tabs"></a><span data-ttu-id="43256-104">Entwicklertools für Microsoft Teams-Registerkarten</span><span class="sxs-lookup"><span data-stu-id="43256-104">DevTools for Microsoft Teams tabs</span></span>

<span data-ttu-id="43256-105">Wenn Teams in einem Browser ausgeführt wird, ist es einfach, auf devTools des Browsers zu zugreifen: F12 (unter Windows) oder Command-Option-I (unter MacOS).</span><span class="sxs-lookup"><span data-stu-id="43256-105">When Teams is running in a browser, it’s easy to access the browser's DevTools: F12 (on Windows) or Command-Option-I (on MacOS).</span></span> <span data-ttu-id="43256-106">Die DevTools bietet Ihnen Zugriff auf:</span><span class="sxs-lookup"><span data-stu-id="43256-106">The DevTools gives you access to:</span></span>

1. <span data-ttu-id="43256-107">Anzeigen von Konsolenprotokollen.</span><span class="sxs-lookup"><span data-stu-id="43256-107">View console logs.</span></span>
1. <span data-ttu-id="43256-108">Anzeigen/Ändern von HTML-, CSS- und Netzwerkanforderungen während der Laufzeit.</span><span class="sxs-lookup"><span data-stu-id="43256-108">View/modify html, css, and network requests during runtime.</span></span>
1. <span data-ttu-id="43256-109">Fügen Sie Ihrem JavaScript-Code Haltepunkte hinzu, und führen Sie interaktives Debuggen aus.</span><span class="sxs-lookup"><span data-stu-id="43256-109">Add breakpoints to your JavaScript code, and perform interactive debugging.</span></span>

<span data-ttu-id="43256-110">Das Feature ist nur auf Desktop- und Android-Clients verfügbar, nachdem Developer Preview aktiviert wurde.</span><span class="sxs-lookup"><span data-stu-id="43256-110">The feature is only available in desktop and Android clients after Developer Preview has been enabled.</span></span> <span data-ttu-id="43256-111">Weitere Informationen finden Sie unter [How do I enable Developer Preview.](~/resources/dev-preview/developer-preview-intro.md)</span><span class="sxs-lookup"><span data-stu-id="43256-111">See [How do I enable Developer Preview](~/resources/dev-preview/developer-preview-intro.md) for more information.</span></span>

## <a name="accessing-devtools-in-the-desktop"></a><span data-ttu-id="43256-112">Zugreifen auf DevTools im Desktop</span><span class="sxs-lookup"><span data-stu-id="43256-112">Accessing DevTools in the Desktop</span></span>

<span data-ttu-id="43256-113">Obwohl die Webversion von Teams und die Desktopversion von Teams nahezu identisch sind, gibt es einige Unterschiede, insbesondere im Hinblick auf die Authentifizierung.</span><span class="sxs-lookup"><span data-stu-id="43256-113">While the web version of Teams and the desktop version of teams are almost exactly the same, there are some differences, particularly with respect to authentication.</span></span> <span data-ttu-id="43256-114">Manchmal ist die einzige Möglichkeit, herauszufinden, was passiert, die Verwendung der DevTools.</span><span class="sxs-lookup"><span data-stu-id="43256-114">Sometimes the only way to figure out what’s going on is to use the DevTools.</span></span> <span data-ttu-id="43256-115">Hier erfahren Sie, wie Sie über den Teams-Desktopclient zu ihnen kommen.</span><span class="sxs-lookup"><span data-stu-id="43256-115">Here's how to get to them from the Teams desktop client.</span></span> <span data-ttu-id="43256-116">So verwenden Sie DevTools im Desktopclient:</span><span class="sxs-lookup"><span data-stu-id="43256-116">To use DevTools in the desktop client:</span></span>

1. <span data-ttu-id="43256-117">Stellen Sie sicher, dass Sie die [Entwicklervorschau aktiviert haben](~/resources/dev-preview/developer-preview-intro.md)</span><span class="sxs-lookup"><span data-stu-id="43256-117">Make sure you have enabled [developer preview](~/resources/dev-preview/developer-preview-intro.md)</span></span>
1. <span data-ttu-id="43256-118">Öffnen Sie eine Registerkarte, damit Sie etwas mit den DevTools überprüfen können.</span><span class="sxs-lookup"><span data-stu-id="43256-118">Open up a tab so you have something to inspect with the DevTools.</span></span>
1. <span data-ttu-id="43256-119">Öffnen Sie devTools auf eine der folgenden Arten:</span><span class="sxs-lookup"><span data-stu-id="43256-119">Open the DevTools one of the following ways:</span></span>
    * <span data-ttu-id="43256-120">**Windows**: Wählen Sie das Symbol Teams im Desktoptablett aus.</span><span class="sxs-lookup"><span data-stu-id="43256-120">**Windows**: Select the Teams icon in the desktop tray.</span></span>
    * <span data-ttu-id="43256-121">**macOS**: Wählen Sie das Symbol Teams im Dock aus.</span><span class="sxs-lookup"><span data-stu-id="43256-121">**macOS**: Select the Teams icon in the Dock.</span></span>

<span data-ttu-id="43256-122">Der folgende Screenshot zeigt DevTools, das ein Element in einem Registerkartenkonfigurationsdialogfeld überprüft:</span><span class="sxs-lookup"><span data-stu-id="43256-122">The following screenshot shows DevTools inspecting an element in a tab configuration dialog:</span></span>

![Tab und DevTools](~/assets/images/dev-preview/tab-and-devtools.png)

## <a name="accessing-devtools-from-an-android-client"></a><span data-ttu-id="43256-124">Zugreifen auf DevTools von einem Android-Client</span><span class="sxs-lookup"><span data-stu-id="43256-124">Accessing DevTools from an Android client</span></span>

<span data-ttu-id="43256-125">Sie können devTools auch über den Teams Android-Client aktivieren.</span><span class="sxs-lookup"><span data-stu-id="43256-125">You can also enable the DevTools from the Teams Android client.</span></span>

1. <span data-ttu-id="43256-126">Stellen Sie sicher, dass Sie die [Entwicklervorschau aktiviert haben](~/resources/dev-preview/developer-preview-intro.md)</span><span class="sxs-lookup"><span data-stu-id="43256-126">Make sure you have enabled [developer preview](~/resources/dev-preview/developer-preview-intro.md)</span></span>
1. <span data-ttu-id="43256-127">Verbinden Sie Ihr Gerät mit Ihrem Desktopcomputer, und richten Sie Ihr Android-Gerät für das [Remotedebugen ein.](https://developers.google.com/web/tools/chrome-devtools/remote-debugging/)</span><span class="sxs-lookup"><span data-stu-id="43256-127">Connect your device to your desktop computer, and setup your Android device for [remote debugging](https://developers.google.com/web/tools/chrome-devtools/remote-debugging/)</span></span>
1. <span data-ttu-id="43256-128">Öffnen Sie in Ihrem Chrome-Browser `chrome://inspect/#devices` .</span><span class="sxs-lookup"><span data-stu-id="43256-128">In your Chrome browser, open `chrome://inspect/#devices`.</span></span>
1. <span data-ttu-id="43256-129">Klicken **Sie auf Überprüfen** unter der Registerkarte, die Sie debuggen möchten, wie im screenshot unten.</span><span class="sxs-lookup"><span data-stu-id="43256-129">Click **inspect** below the tab you wish to debug, as in the screenshot below.</span></span>

![Android DevTools](~/assets/images/android-devtools.png)
