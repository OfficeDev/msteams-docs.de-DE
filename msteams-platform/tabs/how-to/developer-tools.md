---
title: Entwicklertools für Microsoft Teams-Registerkarten
description: Beschreibt, wie Sie bei Verwendung des Microsoft Teams-Desktopclients zu den DevTools kommen
ms.topic: how-to
keywords: Devtools debuggen Entwicklertools für mobile Chrome-Desktopclients
ms.openlocfilehash: 8f23a5d56faa00d40451d2bbeadde32f6a5d0f7f
ms.sourcegitcommit: 976e870cc925f61b76c3830ec04ba6e4bdfde32f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/27/2021
ms.locfileid: "50014579"
---
# <a name="devtools-for-microsoft-teams-tabs"></a><span data-ttu-id="a39ac-104">Entwicklertools für Microsoft Teams-Registerkarten</span><span class="sxs-lookup"><span data-stu-id="a39ac-104">DevTools for Microsoft Teams tabs</span></span>

<span data-ttu-id="a39ac-105">Wenn Teams in einem Browser ausgeführt wird, ist es einfach, auf devTools des Browsers zu zugreifen: F12 (unter Windows) oder Command-Option-I (unter MacOS).</span><span class="sxs-lookup"><span data-stu-id="a39ac-105">When Teams is running in a browser, it’s easy to access the browser's DevTools: F12 (on Windows) or Command-Option-I (on MacOS).</span></span> <span data-ttu-id="a39ac-106">Die DevTools bietet Ihnen Zugriff auf:</span><span class="sxs-lookup"><span data-stu-id="a39ac-106">The DevTools gives you access to:</span></span>

1. <span data-ttu-id="a39ac-107">Anzeigen von Konsolenprotokollen.</span><span class="sxs-lookup"><span data-stu-id="a39ac-107">View console logs.</span></span>
1. <span data-ttu-id="a39ac-108">Html-, CSS- und Netzwerkanforderungen während der Laufzeit anzeigen/ändern.</span><span class="sxs-lookup"><span data-stu-id="a39ac-108">View/modify html, css, and network requests during runtime.</span></span>
1. <span data-ttu-id="a39ac-109">Fügen Sie Ihrem JavaScript-Code Haltepunkte hinzu, und führen Sie ein interaktives Debuggen aus.</span><span class="sxs-lookup"><span data-stu-id="a39ac-109">Add breakpoints to your JavaScript code, and perform interactive debugging.</span></span>

<span data-ttu-id="a39ac-110">Das Feature ist nur in Desktop- und Android-Clients verfügbar, Developer Preview aktiviert wurde.</span><span class="sxs-lookup"><span data-stu-id="a39ac-110">The feature is only available in desktop and Android clients after Developer Preview has been enabled.</span></span> <span data-ttu-id="a39ac-111">Weitere [Informationen finden Sie unter "Developer Preview](~/resources/dev-preview/developer-preview-intro.md) aktivieren".</span><span class="sxs-lookup"><span data-stu-id="a39ac-111">See [How do I enable Developer Preview](~/resources/dev-preview/developer-preview-intro.md) for more information.</span></span>

## <a name="accessing-devtools-in-the-desktop"></a><span data-ttu-id="a39ac-112">Zugreifen auf DevTools auf dem Desktop</span><span class="sxs-lookup"><span data-stu-id="a39ac-112">Accessing DevTools in the Desktop</span></span>

<span data-ttu-id="a39ac-113">Obwohl die Webversion von Teams und die Desktopversion von Teams fast identisch sind, gibt es einige Unterschiede, insbesondere im Hinblick auf die Authentifizierung.</span><span class="sxs-lookup"><span data-stu-id="a39ac-113">While the web version of Teams and the desktop version of teams are almost exactly the same, there are some differences, particularly with respect to authentication.</span></span> <span data-ttu-id="a39ac-114">Manchmal ist die einzige Möglichkeit, herauszufinden, was vor sich geht, die Verwendung der DevTools.</span><span class="sxs-lookup"><span data-stu-id="a39ac-114">Sometimes the only way to figure out what’s going on is to use the DevTools.</span></span> <span data-ttu-id="a39ac-115">Hier erfahren Sie, wie Sie über den Teams-Desktopclient zu ihnen kommen.</span><span class="sxs-lookup"><span data-stu-id="a39ac-115">Here's how to get to them from the Teams desktop client.</span></span> <span data-ttu-id="a39ac-116">So verwenden Sie DevTools im Desktopclient:</span><span class="sxs-lookup"><span data-stu-id="a39ac-116">To use DevTools in the desktop client:</span></span>

1. <span data-ttu-id="a39ac-117">Stellen Sie sicher, dass Sie die [Entwicklervorschau aktiviert haben.](~/resources/dev-preview/developer-preview-intro.md)</span><span class="sxs-lookup"><span data-stu-id="a39ac-117">Make sure you have enabled [developer preview](~/resources/dev-preview/developer-preview-intro.md)</span></span>
1. <span data-ttu-id="a39ac-118">Öffnen Sie eine Registerkarte, damit Sie etwas mit devTools überprüfen können.</span><span class="sxs-lookup"><span data-stu-id="a39ac-118">Open up a tab so you have something to inspect with the DevTools.</span></span>
1. <span data-ttu-id="a39ac-119">Öffnen der DevTools</span><span class="sxs-lookup"><span data-stu-id="a39ac-119">Open the DevTools</span></span>
    * <span data-ttu-id="a39ac-120">Unter Windows öffnen Sie DevTools über das Microsoft Teams-Symbol in der Taskleiste des Desktops:</span><span class="sxs-lookup"><span data-stu-id="a39ac-120">On Windows, you open DevTools via the Microsoft Teams icon in the desktop tray:</span></span>

  ![Klicken Sie mit der rechten Maustaste, um DevTools zu öffnen.](~/assets/images/dev-preview/devtools-right-click.png)

    * <span data-ttu-id="a39ac-122">Klicken Sie unter MacOS im Dock auf das Microsoft Teams-Symbol.</span><span class="sxs-lookup"><span data-stu-id="a39ac-122">On MacOS, click on the Microsoft Teams icon in the Dock.</span></span>

<span data-ttu-id="a39ac-123">So sieht eine Beispielregisterkarte aus, wenn devTools geöffnet und ein Element ausgewählt ist:</span><span class="sxs-lookup"><span data-stu-id="a39ac-123">Here’s what a sample tab looks like with the DevTools open and an element selected:</span></span>

![Registerkarte und DevTools](~/assets/images/dev-preview/tab-and-devtools.png)

## <a name="accessing-devtools-from-an-android-client"></a><span data-ttu-id="a39ac-125">Zugreifen auf DevTools über einen Android-Client</span><span class="sxs-lookup"><span data-stu-id="a39ac-125">Accessing DevTools from an Android client</span></span>

<span data-ttu-id="a39ac-126">Sie können die DevTools auch über den Teams -Android-Client aktivieren.</span><span class="sxs-lookup"><span data-stu-id="a39ac-126">You can also enable the DevTools from the Teams Android client.</span></span> <span data-ttu-id="a39ac-127">Gehen Sie hierzu folgendermaßen vor:</span><span class="sxs-lookup"><span data-stu-id="a39ac-127">To do so:</span></span>

1. <span data-ttu-id="a39ac-128">Stellen Sie sicher, dass Sie die [Entwicklervorschau aktiviert haben.](~/resources/dev-preview/developer-preview-intro.md)</span><span class="sxs-lookup"><span data-stu-id="a39ac-128">Make sure you have enabled [developer preview](~/resources/dev-preview/developer-preview-intro.md)</span></span>
1. <span data-ttu-id="a39ac-129">Verbinden Sie Ihr Gerät mit Ihrem Desktopcomputer, und richten Sie Ihr Android-Gerät für remote [debuggen ein.](https://developers.google.com/web/tools/chrome-devtools/remote-debugging/)</span><span class="sxs-lookup"><span data-stu-id="a39ac-129">Connect your device to your desktop computer, and setup your Android device for [remote debugging](https://developers.google.com/web/tools/chrome-devtools/remote-debugging/)</span></span>
1. <span data-ttu-id="a39ac-130">Öffnen Sie in Ihrem Browser Chrome `chrome://inspect/#devices` .</span><span class="sxs-lookup"><span data-stu-id="a39ac-130">In your Chrome browser, open `chrome://inspect/#devices`.</span></span>
1. <span data-ttu-id="a39ac-131">Klicken **Sie unterhalb** der Registerkarte, die Sie debuggen möchten, auf "Überprüfen", wie im folgenden Screenshot dargestellt.</span><span class="sxs-lookup"><span data-stu-id="a39ac-131">Click **inspect** below the tab you wish to debug, as in the screenshot below.</span></span>

![Android DevTools](~/assets/images/android-devtools.png)
