---
title: Testen Der App-Übersicht
description: Beschreibt den Prozess zum Testen der Teams benutzerdefinierten App in Microsoft 365
ms.topic: how-to
localization_priority: Normal
keywords: Konfigurieren Microsoft 365 Mandanten Teams Hochladen der Test-App
ms.openlocfilehash: 2c9f23a5c6ae286ff4b7d911f370bd45b854a647
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52565186"
---
# <a name="test-your-app"></a><span data-ttu-id="de467-104">Testen eigener Apps</span><span class="sxs-lookup"><span data-stu-id="de467-104">Test your app</span></span>

<span data-ttu-id="de467-105">Nachdem Sie Ihre App in Microsoft Teams integriert haben, müssen Sie ihre App testen, bevor Sie sie veröffentlichen.</span><span class="sxs-lookup"><span data-stu-id="de467-105">After integrating your app with Microsoft Teams, you must test your app before publishing it.</span></span> <span data-ttu-id="de467-106">Das ultimative Ziel besteht darin, so viele Benutzer für Ihre App zu erhalten, daher stellen Sie sicher, dass die App auf mehreren Geräten getestet wird, die Benutzer verwenden könnten.</span><span class="sxs-lookup"><span data-stu-id="de467-106">The ultimate goal is to get as many users for your app, therefore, ensure to test the app on multiple devices that users could use.</span></span> <span data-ttu-id="de467-107">Zum Testen Ihrer App:</span><span class="sxs-lookup"><span data-stu-id="de467-107">For testing your app:</span></span>

* <span data-ttu-id="de467-108">Bereiten Sie Ihren Microsoft 365 Mandanten vor.</span><span class="sxs-lookup"><span data-stu-id="de467-108">Prepare your Microsoft 365 tenant.</span></span>
* <span data-ttu-id="de467-109">Wählen Sie einen Arbeitsbereich aus, um Ihre App zu testen und zu debuggen.</span><span class="sxs-lookup"><span data-stu-id="de467-109">Choose a workspace to test and debug your app.</span></span>
* <span data-ttu-id="de467-110">Fügen Sie Ihrem Microsoft 365 Mandanten Testdaten hinzu.</span><span class="sxs-lookup"><span data-stu-id="de467-110">Add test data to your Microsoft 365 tenant.</span></span>

## <a name="prepare-your-microsoft-365-tenant"></a><span data-ttu-id="de467-111">Vorbereiten Ihres Microsoft 365-Mandanten</span><span class="sxs-lookup"><span data-stu-id="de467-111">Prepare your Microsoft 365 tenant</span></span>

<span data-ttu-id="de467-112">Bevor Sie mit dem Testen Ihrer App beginnen, bereiten Sie Ihren Microsoft 365 Testmandanten vor und aktivieren Sie benutzerdefinierte Teams App, mit der Sie Ihre App hochladen können.</span><span class="sxs-lookup"><span data-stu-id="de467-112">Before you start testing your app, prepare your Microsoft 365 test tenant and enable custom Teams app allow you to upload your app.</span></span> <span data-ttu-id="de467-113">Sie müssen sich für Microsoft 365 Entwicklerprogramm anmelden und die Teams Einstellungen für Ihre Organisation verwalten.</span><span class="sxs-lookup"><span data-stu-id="de467-113">You must sign-up for Microsoft 365 developer program and manage the Teams settings for your organization.</span></span> <span data-ttu-id="de467-114">Richten Sie Ihr Entwicklerabonnement ein, und konfigurieren Sie es, indem [Sie Ihre Microsoft 365 Mandanten vorbereiten.](~/concepts/build-and-test/prepare-your-o365-tenant.md)</span><span class="sxs-lookup"><span data-stu-id="de467-114">Set up your developer subscription and configure it through [prepare your Microsoft 365 Tenant](~/concepts/build-and-test/prepare-your-o365-tenant.md).</span></span>

## <a name="test-and-debug"></a><span data-ttu-id="de467-115">Testen und Debuggen</span><span class="sxs-lookup"><span data-stu-id="de467-115">Test and debug</span></span>

<span data-ttu-id="de467-116">Zum Testen und Debuggen Ihrer App müssen Sie mindestens einen Arbeitsbereich erstellen.</span><span class="sxs-lookup"><span data-stu-id="de467-116">To test and debug your app, you must create at least one workspace.</span></span> <span data-ttu-id="de467-117">Sie können ein Test-Setup auswählen, z. B. einen lokalen oder cloudbasierten Host, um die App zu testen und zu debuggen.</span><span class="sxs-lookup"><span data-stu-id="de467-117">You can select a test setup, such as local host or cloud-based host to test and debug the app.</span></span> <span data-ttu-id="de467-118">Anleitungzum Debuggen Ihrer Teams-App wird zum Laden und Ausführen ihrer App-Erfahrung bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="de467-118">Guidance to debug your Teams app is provided to load and run your app experience.</span></span> <span data-ttu-id="de467-119">Weitere Informationen finden [Sie unter Auswählen eines Setups und Ausführen ihrer Microsoft Teams-App](~/concepts/build-and-test/debug.md).</span><span class="sxs-lookup"><span data-stu-id="de467-119">For more information, see [choose a set up and run your Microsoft Teams app](~/concepts/build-and-test/debug.md).</span></span>

<span data-ttu-id="de467-120">Testen Sie Ihren Bot lokal.</span><span class="sxs-lookup"><span data-stu-id="de467-120">Test your bot locally.</span></span> <span data-ttu-id="de467-121">Weitere Informationen finden Sie unter [Debuggen des Bots lokal mit einer IDE](~/bots/how-to/debug/locally-with-an-ide.md).</span><span class="sxs-lookup"><span data-stu-id="de467-121">For more information, see [debug your bot locally with an IDE](~/bots/how-to/debug/locally-with-an-ide.md).</span></span> <span data-ttu-id="de467-122">Sie können Ihren Bot auch mit [Inspektionsmiddleware](/azure/bot-service/bot-service-debug-inspection-middleware?view=azure-bot-service-4.0&tabs=csharp&preserve-view=true) und [adaptiven Tools](/azure/bot-service/bot-service-debug-adaptive-tools?view=azure-bot-service-4.0&preserve-view=true)debuggen.</span><span class="sxs-lookup"><span data-stu-id="de467-122">You can also debug your bot with [inspection middleware](/azure/bot-service/bot-service-debug-inspection-middleware?view=azure-bot-service-4.0&tabs=csharp&preserve-view=true) and [adaptive tools](/azure/bot-service/bot-service-debug-adaptive-tools?view=azure-bot-service-4.0&preserve-view=true).</span></span> 

<span data-ttu-id="de467-123">Um die Konsolenprotokolle anzuzeigen, HTML-, css- und Netzwerkanforderungen während der Laufzeit anzuzeigen oder zu ändern, fügen Sie Ihrem JavaScript-Code Haltepunkte hinzu, und führen Sie interaktiven Debugzugriff auf die DevTools durch.</span><span class="sxs-lookup"><span data-stu-id="de467-123">To view the console logs, view or modify html, css, and network requests during runtime, add breakpoints to your JavaScript code, and perform interactive debugging access the DevTools.</span></span> <span data-ttu-id="de467-124">Weitere Informationen finden [Sie unter Zugriff auf die DevTools für Teams Registerkarten](~/tabs/how-to/developer-tools.md).</span><span class="sxs-lookup"><span data-stu-id="de467-124">For more information, see [Access the DevTools for Teams tabs](~/tabs/how-to/developer-tools.md).</span></span> 

## <a name="add-test-data-to-your-microsoft-365-tenant"></a><span data-ttu-id="de467-125">Hinzufügen von Testdaten zu Ihrem Microsoft 365 Mandanten</span><span class="sxs-lookup"><span data-stu-id="de467-125">Add test data to your Microsoft 365 tenant</span></span>

<span data-ttu-id="de467-126">Fügen Sie die Testdaten Microsoft 365 Testmandanten hinzu.</span><span class="sxs-lookup"><span data-stu-id="de467-126">Add the test data to Microsoft 365 test tenant.</span></span> <span data-ttu-id="de467-127">Weitere Informationen finden Sie unter [Hinzufügen von Testdaten zu Ihrem Office 365 Testmandanten](~/concepts/build-and-test/test-data.md), und schließen Sie alle Voraussetzungen ab, bevor Sie mit dem Hochladen der Testdaten beginnen.</span><span class="sxs-lookup"><span data-stu-id="de467-127">For more information, see [add test data to your Office 365 test tenant](~/concepts/build-and-test/test-data.md), and complete all the prerequisites before you start uploading your test data.</span></span>

## <a name="see-also"></a><span data-ttu-id="de467-128">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="de467-128">See also</span></span>

- [<span data-ttu-id="de467-129">Debuggen Sie Ihre Registerkarte</span><span class="sxs-lookup"><span data-stu-id="de467-129">Debug your tab</span></span>](~/tabs/how-to/developer-tools.md)
 
- [<span data-ttu-id="de467-130">Debuggen Sie Ihre Bots</span><span class="sxs-lookup"><span data-stu-id="de467-130">Debug your bots</span></span>](~/bots/how-to/debug/locally-with-an-ide.md)

- [<span data-ttu-id="de467-131">RSC-Berechtigungen testen</span><span class="sxs-lookup"><span data-stu-id="de467-131">Test RSC permissions</span></span>](~/graph-api/rsc/test-resource-specific-consent.md)

## <a name="next-step"></a><span data-ttu-id="de467-132">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="de467-132">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="de467-133">Vorbereiten Ihres Microsoft 365-Mandanten</span><span class="sxs-lookup"><span data-stu-id="de467-133">Prepare your Microsoft 365 tenant</span></span>](~/concepts/build-and-test/prepare-your-o365-tenant.md)
