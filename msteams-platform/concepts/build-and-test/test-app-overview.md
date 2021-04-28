---
title: Testen der App-Übersicht
description: Beschreibt den Prozess zum Testen Ihrer benutzerdefinierten Teams-App in Microsoft 365
ms.topic: how-to
localization_priority: Normal
keywords: Konfigurieren der Microsoft 365-Mandantenteams zum Hochladen der Test-App
ms.openlocfilehash: d95d65961b060ff1938d51c0f3fafc2b1e56fa7e
ms.sourcegitcommit: a732789190f59ec1f3699e8ad2f06387e8fe1458
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2021
ms.locfileid: "52058607"
---
# <a name="test-your-app"></a><span data-ttu-id="6a9a1-104">Testen eigener Apps</span><span class="sxs-lookup"><span data-stu-id="6a9a1-104">Test your app</span></span>

<span data-ttu-id="6a9a1-105">Nachdem Sie Ihre App in Microsoft Teams integriert haben, müssen Sie Ihre App testen, bevor Sie sie veröffentlichen.</span><span class="sxs-lookup"><span data-stu-id="6a9a1-105">After integrating your app with Microsoft Teams, you must test your app before publishing it.</span></span> <span data-ttu-id="6a9a1-106">Das letztendliche Ziel ist es, so viele Benutzer für Ihre App zu erhalten, dass Sie die App auf mehreren Geräten testen, die Benutzer verwenden können.</span><span class="sxs-lookup"><span data-stu-id="6a9a1-106">The ultimate goal is to get as many users for your app, therefore, ensure to test the app on multiple devices that users could use.</span></span> <span data-ttu-id="6a9a1-107">Zum Testen Ihrer App:</span><span class="sxs-lookup"><span data-stu-id="6a9a1-107">For testing your app:</span></span>

* <span data-ttu-id="6a9a1-108">Vorbereiten Ihres Microsoft 365-Mandanten</span><span class="sxs-lookup"><span data-stu-id="6a9a1-108">Prepare your Microsoft 365 tenant</span></span>
* <span data-ttu-id="6a9a1-109">Auswählen eines Arbeitsbereichs zum Testen und Debuggen Ihrer App</span><span class="sxs-lookup"><span data-stu-id="6a9a1-109">Choose a workspace to test and debug your app</span></span>
* <span data-ttu-id="6a9a1-110">Hinzufügen von Testdaten zu Ihrem Microsoft 365-Mandanten</span><span class="sxs-lookup"><span data-stu-id="6a9a1-110">Add test data to your Microsoft 365 tenant</span></span>

## <a name="prepare-your-microsoft-365-tenant"></a><span data-ttu-id="6a9a1-111">Vorbereiten Ihres Microsoft 365-Mandanten</span><span class="sxs-lookup"><span data-stu-id="6a9a1-111">Prepare your Microsoft 365 tenant</span></span>

<span data-ttu-id="6a9a1-112">Bevor Sie mit dem Testen Ihrer App beginnen, bereiten Sie Ihren Microsoft 365-Test-Mandanten vor, und aktivieren Sie die benutzerdefinierte Teams-App, mit der Sie Ihre App hochladen können.</span><span class="sxs-lookup"><span data-stu-id="6a9a1-112">Before you start testing your app, prepare your Microsoft 365 test tenant and enable custom Teams app allow you to upload your app.</span></span> <span data-ttu-id="6a9a1-113">Sie müssen sich für das Microsoft 365-Entwicklerprogramm registrieren und die Teams-Einstellungen für Ihre Organisation verwalten.</span><span class="sxs-lookup"><span data-stu-id="6a9a1-113">You must sign-up for Microsoft 365 developer program and manage the Teams settings for your organization.</span></span> <span data-ttu-id="6a9a1-114">Richten Sie Ihr Entwicklerabonnement ein, und konfigurieren Sie es, wenn [Sie Ihren Microsoft 365-Mandanten vorbereiten.](~/concepts/build-and-test/prepare-your-o365-tenant.md)</span><span class="sxs-lookup"><span data-stu-id="6a9a1-114">Set up your developer subscription and configure it through [prepare your Microsoft 365 Tenant](~/concepts/build-and-test/prepare-your-o365-tenant.md).</span></span>

## <a name="test-and-debug"></a><span data-ttu-id="6a9a1-115">Testen und Debuggen</span><span class="sxs-lookup"><span data-stu-id="6a9a1-115">Test and debug</span></span>

<span data-ttu-id="6a9a1-116">Zum Testen und Debuggen Ihrer App müssen Sie mindestens einen Arbeitsbereich erstellen.</span><span class="sxs-lookup"><span data-stu-id="6a9a1-116">To test and debug your app, you must create at least one workspace.</span></span> <span data-ttu-id="6a9a1-117">Sie können eine Testeinrichtung auswählen, z. B. einen lokalen Host oder einen cloudbasierten Host, um die App zu testen und zu debuggen.</span><span class="sxs-lookup"><span data-stu-id="6a9a1-117">You can select a test setup, such as local host or cloud-based host to test and debug the app.</span></span> <span data-ttu-id="6a9a1-118">Anleitungen zum Debuggen Ihrer Teams-App finden Sie zum Laden und Ausführen Ihrer App-Erfahrung.</span><span class="sxs-lookup"><span data-stu-id="6a9a1-118">Guidance to debug your Teams app is provided to load and run your app experience.</span></span> <span data-ttu-id="6a9a1-119">Weitere Informationen finden Sie [unter Auswählen einer Einrichtung und Ausführen Ihrer Microsoft Teams-App.](~/concepts/build-and-test/debug.md)</span><span class="sxs-lookup"><span data-stu-id="6a9a1-119">For more information, see [choose a set up and run your Microsoft Teams app](~/concepts/build-and-test/debug.md).</span></span>

<span data-ttu-id="6a9a1-120">Testen Sie Ihren Bot lokal.</span><span class="sxs-lookup"><span data-stu-id="6a9a1-120">Test your bot locally.</span></span> <span data-ttu-id="6a9a1-121">Weitere Informationen finden Sie unter [Debuggen Des Bots lokal mit einer IDE](~/bots/how-to/debug/locally-with-an-ide.md).</span><span class="sxs-lookup"><span data-stu-id="6a9a1-121">For more information, see [debug your bot locally with an IDE](~/bots/how-to/debug/locally-with-an-ide.md).</span></span> <span data-ttu-id="6a9a1-122">Sie können Ihren Bot auch mit [Prüf-Middleware und](/azure/bot-service/bot-service-debug-inspection-middleware?view=azure-bot-service-4.0&tabs=csharp&preserve-view=true) [adaptiven Tools debuggen.](/azure/bot-service/bot-service-debug-adaptive-tools?view=azure-bot-service-4.0&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="6a9a1-122">You can also debug your bot with [inspection middleware](/azure/bot-service/bot-service-debug-inspection-middleware?view=azure-bot-service-4.0&tabs=csharp&preserve-view=true) and [adaptive tools](/azure/bot-service/bot-service-debug-adaptive-tools?view=azure-bot-service-4.0&preserve-view=true).</span></span> 

<span data-ttu-id="6a9a1-123">Wenn Sie die Konsolenprotokolle anzeigen, html-, css- und Netzwerkanforderungen während der Laufzeit anzeigen oder ändern möchten, fügen Sie Ihrem JavaScript-Code Haltepunkte hinzu, und führen Sie interaktiven Debugzugriff auf devTools aus.</span><span class="sxs-lookup"><span data-stu-id="6a9a1-123">To view the console logs, view or modify html, css, and network requests during runtime, add breakpoints to your JavaScript code, and perform interactive debugging access the DevTools.</span></span> <span data-ttu-id="6a9a1-124">Weitere Informationen finden Sie unter [Access the DevTools for Teams tabs](~/tabs/how-to/developer-tools.md).</span><span class="sxs-lookup"><span data-stu-id="6a9a1-124">For more information, see [Access the DevTools for Teams tabs](~/tabs/how-to/developer-tools.md).</span></span> 

## <a name="add-test-data-to-your-microsoft-365-tenant"></a><span data-ttu-id="6a9a1-125">Hinzufügen von Testdaten zu Ihrem Microsoft 365-Mandanten</span><span class="sxs-lookup"><span data-stu-id="6a9a1-125">Add test data to your Microsoft 365 tenant</span></span>

<span data-ttu-id="6a9a1-126">Fügen Sie die Testdaten dem Microsoft 365-Test-Mandanten hinzu.</span><span class="sxs-lookup"><span data-stu-id="6a9a1-126">Add the test data to Microsoft 365 test tenant.</span></span> <span data-ttu-id="6a9a1-127">Weitere Informationen finden Sie unter Hinzufügen von Testdaten zu [Ihrem Office 365-Test-Mandanten,](~/concepts/build-and-test/test-data.md)und füllen Sie alle erforderlichen Komponenten aus, bevor Sie mit dem Hochladen ihrer Testdaten beginnen.</span><span class="sxs-lookup"><span data-stu-id="6a9a1-127">For more information, see [add test data to your Office 365 test tenant](~/concepts/build-and-test/test-data.md), and complete all the prerequisites before you start uploading your test data.</span></span>

## <a name="see-also"></a><span data-ttu-id="6a9a1-128">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="6a9a1-128">See also</span></span>

- [<span data-ttu-id="6a9a1-129">Debuggen Ihrer Registerkarte</span><span class="sxs-lookup"><span data-stu-id="6a9a1-129">Debug your tab</span></span>](~/tabs/how-to/developer-tools.md)
 
- [<span data-ttu-id="6a9a1-130">Debuggen Ihrer Bots</span><span class="sxs-lookup"><span data-stu-id="6a9a1-130">Debug your bots</span></span>](~/bots/how-to/debug/locally-with-an-ide.md)

- [<span data-ttu-id="6a9a1-131">Testen von RSC-Berechtigungen</span><span class="sxs-lookup"><span data-stu-id="6a9a1-131">Test RSC permissions</span></span>](~/graph-api/rsc/test-resource-specific-consent.md)

## <a name="next-step"></a><span data-ttu-id="6a9a1-132">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="6a9a1-132">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="6a9a1-133">Vorbereiten Ihres Microsoft 365-Mandanten</span><span class="sxs-lookup"><span data-stu-id="6a9a1-133">Prepare your Microsoft 365 tenant</span></span>](~/concepts/build-and-test/prepare-your-o365-tenant.md)
