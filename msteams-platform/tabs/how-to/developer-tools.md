---
title: Entwicklertools für Microsoft Teams-Registerkarten
description: Beschreibt, wie Sie zu den DevTools bei Verwendung des Microsoft Teams Desktopclients
localization_priority: Normal
ms.topic: how-to
keywords: Devtools debuggen mobile Chrome-Desktop-Client-Entwicklertools
ms.openlocfilehash: 70c9a2bab94ceb97e8dcd5cf5cdb98261d037f74
ms.sourcegitcommit: 25c9ad27f99682caaa7347840578b118c63b8f69
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2021
ms.locfileid: "52101828"
---
# <a name="devtools-for-microsoft-teams-tabs"></a><span data-ttu-id="d2672-104">Entwicklertools für Microsoft Teams-Registerkarten</span><span class="sxs-lookup"><span data-stu-id="d2672-104">DevTools for Microsoft Teams tabs</span></span>

<span data-ttu-id="d2672-105">Wenn Teams in einem Browser ausgeführt wird, ist es einfach, auf devTools: F12 des Browsers unter Windows oder Command-Option-I unter MacOS zu zugreifen.</span><span class="sxs-lookup"><span data-stu-id="d2672-105">When Teams is running in a browser, it is easy to access the browser's DevTools: F12 on Windows or Command-Option-I on MacOS.</span></span> <span data-ttu-id="d2672-106">Die DevTools bietet Ihnen Zugriff auf:</span><span class="sxs-lookup"><span data-stu-id="d2672-106">The DevTools gives you access to:</span></span>

1. <span data-ttu-id="d2672-107">Anzeigen von Konsolenprotokollen.</span><span class="sxs-lookup"><span data-stu-id="d2672-107">View console logs.</span></span>
1. <span data-ttu-id="d2672-108">Anzeigen oder Ändern von HTML-, CSS- und Netzwerkanforderungen während der Laufzeit.</span><span class="sxs-lookup"><span data-stu-id="d2672-108">View or modify HTML, CSS, and network requests during runtime.</span></span>
1. <span data-ttu-id="d2672-109">Fügen Sie Ihrem JavaScript-Code Haltepunkte hinzu, und führen Sie interaktives Debuggen aus.</span><span class="sxs-lookup"><span data-stu-id="d2672-109">Add breakpoints to your JavaScript code and perform interactive debugging.</span></span>

> [!NOTE]
> <span data-ttu-id="d2672-110">Das Feature ist nur für Desktop- und **Android-Clients** verfügbar, nachdem Developer Preview aktiviert wurde.</span><span class="sxs-lookup"><span data-stu-id="d2672-110">The feature is only available for desktop and Android clients after the **Developer Preview** has been enabled.</span></span> <span data-ttu-id="d2672-111">Weitere Informationen finden Sie unter [Aktivieren der Entwicklervorschau](~/resources/dev-preview/developer-preview-intro.md).</span><span class="sxs-lookup"><span data-stu-id="d2672-111">For more information, see [How do I enable developer preview](~/resources/dev-preview/developer-preview-intro.md).</span></span>

## <a name="access-devtools-on-the-desktop"></a><span data-ttu-id="d2672-112">Zugreifen auf DevTools auf dem Desktop</span><span class="sxs-lookup"><span data-stu-id="d2672-112">Access DevTools on the desktop</span></span>

<span data-ttu-id="d2672-113">Obwohl die Webversion und die Desktopversion von Teams nahezu identisch sind, gibt es einige Unterschiede in Bezug auf die Authentifizierung.</span><span class="sxs-lookup"><span data-stu-id="d2672-113">While the web version and the desktop version of Teams are almost the same, there are some differences concerning authentication.</span></span> <span data-ttu-id="d2672-114">Manchmal ist die einzige Möglichkeit, herauszufinden, was vor sich geht, die Verwendung der DevTools.</span><span class="sxs-lookup"><span data-stu-id="d2672-114">Sometimes the only way to figure out what is going on is to use the DevTools.</span></span> <span data-ttu-id="d2672-115">Um DevTools im Desktopclient zu verwenden, müssen Sie:</span><span class="sxs-lookup"><span data-stu-id="d2672-115">To use DevTools in the desktop client, you must:</span></span>

1. <span data-ttu-id="d2672-116">Stellen Sie sicher, dass Sie die [Entwicklervorschau aktiviert haben.](~/resources/dev-preview/developer-preview-intro.md)</span><span class="sxs-lookup"><span data-stu-id="d2672-116">Ensure you have enabled [developer preview](~/resources/dev-preview/developer-preview-intro.md).</span></span>
1. <span data-ttu-id="d2672-117">Öffnen Sie eine Registerkarte, damit Sie etwas mit den DevTools überprüfen können.</span><span class="sxs-lookup"><span data-stu-id="d2672-117">Open up a tab so you have something to inspect with the DevTools.</span></span>
1. <span data-ttu-id="d2672-118">Öffnen Sie devTools auf eine der folgenden Arten:</span><span class="sxs-lookup"><span data-stu-id="d2672-118">Open the DevTools one of the following ways:</span></span>
    * <span data-ttu-id="d2672-119">Auf Windows öffnen Sie DevTools über das Microsoft Teams im Desktoptablett:</span><span class="sxs-lookup"><span data-stu-id="d2672-119">On Windows, you open DevTools via the Microsoft Teams icon in the desktop tray:</span></span><br>
  <span data-ttu-id="d2672-120">![Klicken Sie mit der rechten Maustaste, um DevTools zu öffnen](~/assets/images/dev-preview/devtools-right-click.png)</span><span class="sxs-lookup"><span data-stu-id="d2672-120">![Right-click to open DevTools](~/assets/images/dev-preview/devtools-right-click.png)</span></span>
    * <span data-ttu-id="d2672-121">Klicken Sie auf MacOS auf das Microsoft Teams im Dock.</span><span class="sxs-lookup"><span data-stu-id="d2672-121">On MacOS, click on the Microsoft Teams icon in the Dock.</span></span>

<span data-ttu-id="d2672-122">Im folgenden Beispiel wird gezeigt, wie DevTools ein Dialogfeld zur Registerkartenkonfiguration öffnet und überprüft:</span><span class="sxs-lookup"><span data-stu-id="d2672-122">The following example shows DevTools open and inspecting a tab configuration dialog:</span></span>

   ![Tab und DevTools](~/assets/images/dev-preview/tab-and-devtools.png)

## <a name="access-devtools-from-an-android-device"></a><span data-ttu-id="d2672-124">Zugreifen auf DevTools von einem Android-Gerät</span><span class="sxs-lookup"><span data-stu-id="d2672-124">Access DevTools from an Android device</span></span>

<span data-ttu-id="d2672-125">Sie können die DevTools auch über den Teams aktivieren.</span><span class="sxs-lookup"><span data-stu-id="d2672-125">You can also enable the DevTools from the Teams Android client.</span></span> <span data-ttu-id="d2672-126">Um DevTools zu aktivieren, müssen Sie:</span><span class="sxs-lookup"><span data-stu-id="d2672-126">To enable DevTools, you must:</span></span>

1. <span data-ttu-id="d2672-127">Aktivieren Sie [die Entwicklervorschau](~/resources/dev-preview/developer-preview-intro.md).</span><span class="sxs-lookup"><span data-stu-id="d2672-127">Enable the [developer preview](~/resources/dev-preview/developer-preview-intro.md).</span></span>
1. <span data-ttu-id="d2672-128">Verbinden Sie Ihr Gerät auf Ihrem Desktopcomputer an, und richten Sie Ihr Android-Gerät für das [Remotedebubugen ein.](https://developers.google.com/web/tools/chrome-devtools/remote-debugging/)</span><span class="sxs-lookup"><span data-stu-id="d2672-128">Connect your device to your desktop computer, and set up your Android device for [remote debugging](https://developers.google.com/web/tools/chrome-devtools/remote-debugging/).</span></span>
1. <span data-ttu-id="d2672-129">Öffnen Sie in Ihrem Chrome-Browser `chrome://inspect/#devices` .</span><span class="sxs-lookup"><span data-stu-id="d2672-129">In your Chrome browser, open `chrome://inspect/#devices`.</span></span>
1. <span data-ttu-id="d2672-130">Wählen **Sie überprüfen** unter der Registerkarte aus, die Sie debuggen möchten, wie in der folgenden Abbildung:</span><span class="sxs-lookup"><span data-stu-id="d2672-130">Select **inspect** under the tab you wish to debug, as in the following image:</span></span>

   ![Android DevTools](~/assets/images/android-devtools.png)
