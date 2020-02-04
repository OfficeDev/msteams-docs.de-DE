---
title: DevTools für Microsoft Teams-Registerkarten
description: Beschreibt, wie Sie bei Verwendung des Microsoft Teams-Desktop Clients zum devtools gelangen
keywords: DevTools Debugging Mobile Chrome Desktop Client Developer Tools
ms.openlocfilehash: 6c8ac15caf64c979b23155be847e8791988486e6
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674330"
---
# <a name="devtools-for-microsoft-teams-tabs"></a><span data-ttu-id="9c071-104">DevTools für Microsoft Teams-Registerkarten</span><span class="sxs-lookup"><span data-stu-id="9c071-104">DevTools for Microsoft Teams tabs</span></span>

<span data-ttu-id="9c071-105">Wenn Microsoft Teams in einem Browser läuft, können Sie ganz einfach auf die devtools des Browsers zugreifen: F12 (unter Windows) oder Command-Option-I (unter MacOS).</span><span class="sxs-lookup"><span data-stu-id="9c071-105">When Teams is running in a browser, it’s easy to access the browser's DevTools: F12 (on Windows) or Command-Option-I (on MacOS).</span></span> <span data-ttu-id="9c071-106">Die devtools ermöglicht den Zugriff auf:</span><span class="sxs-lookup"><span data-stu-id="9c071-106">The DevTools gives you access to:</span></span>

1. <span data-ttu-id="9c071-107">Anzeigen von Konsolen Protokollen</span><span class="sxs-lookup"><span data-stu-id="9c071-107">View console logs.</span></span>
1. <span data-ttu-id="9c071-108">Anzeigen/Ändern von HTML-, CSS-und Netzwerkanforderungen während der Laufzeit.</span><span class="sxs-lookup"><span data-stu-id="9c071-108">View/modify html, css, and network requests during runtime.</span></span>
1. <span data-ttu-id="9c071-109">Fügen Sie Ihrem JavaScript-Code Haltepunkte hinzu, und führen Sie ein interaktives Debugging aus.</span><span class="sxs-lookup"><span data-stu-id="9c071-109">Add breakpoints to your JavaScript code, and perform interactive debugging.</span></span>

<span data-ttu-id="9c071-110">Das Feature steht nur in Desktop-und Android-Clients zur Verfügung, nachdem die Entwicklervorschau aktiviert wurde.</span><span class="sxs-lookup"><span data-stu-id="9c071-110">The feature is only available in desktop and Android clients after Developer Preview has been enabled.</span></span> <span data-ttu-id="9c071-111">Weitere Informationen finden Sie unter [How do I enable Developer Preview](~/resources/dev-preview/developer-preview-intro.md) .</span><span class="sxs-lookup"><span data-stu-id="9c071-111">See [How do I enable Developer Preview](~/resources/dev-preview/developer-preview-intro.md) for more information.</span></span>

## <a name="accessing-devtools-in-the-desktop"></a><span data-ttu-id="9c071-112">Zugreifen auf devtools auf dem Desktop</span><span class="sxs-lookup"><span data-stu-id="9c071-112">Accessing DevTools in the Desktop</span></span>

<span data-ttu-id="9c071-113">Während die Webversion von Teams und die Desktop Version von Microsoft Teams nahezu identisch sind, gibt es einige Unterschiede, insbesondere im Hinblick auf die Authentifizierung.</span><span class="sxs-lookup"><span data-stu-id="9c071-113">While the web version of Teams and the desktop version of teams are almost exactly the same, there are some differences, particularly with respect to authentication.</span></span> <span data-ttu-id="9c071-114">Manchmal ist die Verwendung der devtools die einzige Möglichkeit, um herauszufinden, was vor sich geht.</span><span class="sxs-lookup"><span data-stu-id="9c071-114">Sometimes the only way to figure out what’s going on is to use the DevTools.</span></span> <span data-ttu-id="9c071-115">Hier erfahren Sie, wie Sie vom Microsoft Teams-Desktop Client aus dorthin gelangen.</span><span class="sxs-lookup"><span data-stu-id="9c071-115">Here's how to get to them from the Teams desktop client.</span></span> <span data-ttu-id="9c071-116">So verwenden Sie devtools im Desktop Client:</span><span class="sxs-lookup"><span data-stu-id="9c071-116">To use DevTools in the desktop client:</span></span>

1. <span data-ttu-id="9c071-117">Stellen Sie sicher, dass Sie die [Entwicklervorschau](~/resources/dev-preview/developer-preview-intro.md) aktiviert haben</span><span class="sxs-lookup"><span data-stu-id="9c071-117">Make sure you have enabled [developer preview](~/resources/dev-preview/developer-preview-intro.md)</span></span>
1. <span data-ttu-id="9c071-118">Öffnen Sie eine Registerkarte, damit Sie mit dem devtools etwas zu inspizieren haben.</span><span class="sxs-lookup"><span data-stu-id="9c071-118">Open up a tab so you have something to inspect with the DevTools.</span></span>
1. <span data-ttu-id="9c071-119">Öffnen des devtools</span><span class="sxs-lookup"><span data-stu-id="9c071-119">Open the DevTools</span></span>
    * <span data-ttu-id="9c071-120">Unter Windows öffnen Sie devtools über das Microsoft Teams-Symbol in der Desktop Ablage:</span><span class="sxs-lookup"><span data-stu-id="9c071-120">On Windows, you open DevTools via the Microsoft Teams icon in the desktop tray:</span></span>

  ![Klicken Sie mit der rechten Maustaste, um devtools zu öffnen](~/assets/images/dev-preview/devtools-right-click.png)

    * <span data-ttu-id="9c071-122">Klicken Sie unter MacOS auf das Microsoft Teams-Symbol im Dock.</span><span class="sxs-lookup"><span data-stu-id="9c071-122">On MacOS, click on the Microsoft Teams icon in the Dock.</span></span>

<span data-ttu-id="9c071-123">Hier sehen Sie, wie eine Beispielregisterkarte aussieht, wenn das devtools geöffnet und ein Element ausgewählt ist:</span><span class="sxs-lookup"><span data-stu-id="9c071-123">Here’s what a sample tab looks like with the DevTools open and an element selected:</span></span>

![Tab-und DevTools](~/assets/images/dev-preview/tab-and-devtools.png)

## <a name="accessing-devtools-from-an-android-client"></a><span data-ttu-id="9c071-125">Zugriff auf devtools von einem Android-Client aus</span><span class="sxs-lookup"><span data-stu-id="9c071-125">Accessing DevTools from an Android client</span></span>

<span data-ttu-id="9c071-126">Sie können die devtools auch über den Android-Client von Teams aktivieren.</span><span class="sxs-lookup"><span data-stu-id="9c071-126">You can also enable the DevTools from the Teams Android client.</span></span> <span data-ttu-id="9c071-127">Gehen Sie hierzu folgendermaßen vor:</span><span class="sxs-lookup"><span data-stu-id="9c071-127">To do so:</span></span>

1. <span data-ttu-id="9c071-128">Stellen Sie sicher, dass Sie die [Entwicklervorschau](~/resources/dev-preview/developer-preview-intro.md) aktiviert haben</span><span class="sxs-lookup"><span data-stu-id="9c071-128">Make sure you have enabled [developer preview](~/resources/dev-preview/developer-preview-intro.md)</span></span>
1. <span data-ttu-id="9c071-129">Verbinden des Geräts mit dem Desktopcomputer und Einrichten des Android-Geräts für das [Remote Debugging](https://developers.google.com/web/tools/chrome-devtools/remote-debugging/)</span><span class="sxs-lookup"><span data-stu-id="9c071-129">Connect your device to your desktop computer, and setup your Android device for [remote debugging](https://developers.google.com/web/tools/chrome-devtools/remote-debugging/)</span></span>
1. <span data-ttu-id="9c071-130">Öffnen `chrome://inspect/#devices`Sie in Ihrem Chrome-Browser.</span><span class="sxs-lookup"><span data-stu-id="9c071-130">In your Chrome browser, open `chrome://inspect/#devices`.</span></span>
1. <span data-ttu-id="9c071-131">Klicken Sie auf über **prüfen** unter der Registerkarte, die Sie debuggen möchten, wie im Screenshot unten beschrieben.</span><span class="sxs-lookup"><span data-stu-id="9c071-131">Click **inspect** below the tab you wish to debug, as in the screenshot below.</span></span>

![Android-devtools](~/assets/images/android-devtools.png)
