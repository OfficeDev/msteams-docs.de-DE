---
title: Übersicht über die Grundlagen der App-Entwicklung
author: heath-hamilton
description: Beschreiben der grundlegenden Konzepte der Teams-Plattformentwicklung.
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 4af23e06cbf7a3f630b77ee1693e0931c9c9c03e
ms.sourcegitcommit: 9404c2e3a30887b9e17e0c89b12dd26fd9b8033e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2021
ms.locfileid: "51654272"
---
# <a name="microsoft-teams-app-development-fundamentals"></a><span data-ttu-id="156e2-103">Grundlagen der Microsoft Teams-App-Entwicklung</span><span class="sxs-lookup"><span data-stu-id="156e2-103">Microsoft Teams app development fundamentals</span></span>

<span data-ttu-id="156e2-104">Microsoft Teams-App-Grundlagen geben die Richtung, die Sie zum Erstellen Ihrer benutzerdefinierten Teams-App benötigen.</span><span class="sxs-lookup"><span data-stu-id="156e2-104">Microsoft Teams app fundamentals give the direction you need to create your custom Teams app.</span></span> <span data-ttu-id="156e2-105">Sie können das framework erkennen, das für die Planung Ihrer Teams-App erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="156e2-105">You can recognize the framework required to plan your Teams app.</span></span> <span data-ttu-id="156e2-106">Das Dokument hilft Ihnen, die Benutzer-App-Kommunikation zu verstehen und herauszufinden, welche Art von App-Oberflächen Sie verwenden müssen oder welche APIs Ihre App dabei möglicherweise benötigt.</span><span class="sxs-lookup"><span data-stu-id="156e2-106">The document helps you to understand the user-app communication and figure out the kind of app surfaces you need to use or the APIs your app might require in the process.</span></span> <span data-ttu-id="156e2-107">Lassen Sie sich inspirieren, Interaktivität zu nutzen, die die App-Erfahrung bei der Integration in Teams vertiefen kann.</span><span class="sxs-lookup"><span data-stu-id="156e2-107">Get some inspiration to embrace interactivity that can deepen the app experience when you integrate with Teams.</span></span>

## <a name="capabilities-and-entry-points"></a><span data-ttu-id="156e2-108">Funktionen und Einstiegspunkte</span><span class="sxs-lookup"><span data-stu-id="156e2-108">Capabilities and entry points</span></span>

<span data-ttu-id="156e2-109">Sie können Ihre Teams-App auf verschiedene Arten erweitern.</span><span class="sxs-lookup"><span data-stu-id="156e2-109">You can extend your Teams app in multiple ways.</span></span> <span data-ttu-id="156e2-110">Um Ihre App erweitern zu können, müssen Sie alle zentralen Funktionen und Einstiegspunkte kennen, die in einem gemeinsamen Raum funktionieren.</span><span class="sxs-lookup"><span data-stu-id="156e2-110">To be able to extend your app you must understand all the core capabilities and the entry points that work in a collaborative space.</span></span> <span data-ttu-id="156e2-111">Sie können mit den Erweiterungspunkten für das Erstellen Ihrer Apps experimentieren.</span><span class="sxs-lookup"><span data-stu-id="156e2-111">You can experiment with the extension points for building your apps.</span></span> <span data-ttu-id="156e2-112">Wichtige App-Projektkomponenten helfen Ihnen bei der ordnungsgemäßen Konfiguration Ihrer App-Seite.</span><span class="sxs-lookup"><span data-stu-id="156e2-112">Important app project components help you to correctly configure your app page.</span></span> <span data-ttu-id="156e2-113">Die Teams-App kann über [mehrere Funktionen und](../concepts/capabilities-overview.md) [Einstiegspunkte verfügen.](../concepts/extensibility-points.md)</span><span class="sxs-lookup"><span data-stu-id="156e2-113">Teams app can have [multiple capabilities](../concepts/capabilities-overview.md) and [entry points](../concepts/extensibility-points.md).</span></span>

## <a name="understand-your-use-cases"></a><span data-ttu-id="156e2-114">Grundlegendes zu Ihren Anwendungsfällen</span><span class="sxs-lookup"><span data-stu-id="156e2-114">Understand your use cases</span></span>

<span data-ttu-id="156e2-115">Sie können Benutzerprobleme erkennen und die Antworten auf einige häufige Probleme identifizieren, mit denen die Benutzer zu kämpfen haben.</span><span class="sxs-lookup"><span data-stu-id="156e2-115">You can recognize user issues and identify the answers to some common problems the users face.</span></span> <span data-ttu-id="156e2-116">Sie können Ihre Teams-App erstellen, indem Sie die richtige Kombination finden, um die Anforderungen Ihres Benutzers zu erfüllen.</span><span class="sxs-lookup"><span data-stu-id="156e2-116">You can build your Teams app by finding the right combination to meet your user's needs.</span></span> <span data-ttu-id="156e2-117">[Verstehen von Anwendungsfällen,](../concepts/design/understand-use-cases.md) um zu wissen, wie ein Endbenutzer mit Ihrer App interagiert.</span><span class="sxs-lookup"><span data-stu-id="156e2-117">[Understand use cases](../concepts/design/understand-use-cases.md) to know how an end-user interacts with your app.</span></span> <span data-ttu-id="156e2-118">Sie lernen, den Benutzer und sein Problem zu verstehen.</span><span class="sxs-lookup"><span data-stu-id="156e2-118">You learn to understand the user and their problem.</span></span> <span data-ttu-id="156e2-119">Einige häufig beantwortete Fragen sind wie folgt:</span><span class="sxs-lookup"><span data-stu-id="156e2-119">Some common questions answered are as follows:</span></span>

* <span data-ttu-id="156e2-120">Benötigen Sie Authentifizierung?</span><span class="sxs-lookup"><span data-stu-id="156e2-120">Do you need authentication?</span></span>
* <span data-ttu-id="156e2-121">Welches Problem wird ihre App lösen?</span><span class="sxs-lookup"><span data-stu-id="156e2-121">What problem is your app going to solve?</span></span>
* <span data-ttu-id="156e2-122">Wer sind die Endbenutzer der App?</span><span class="sxs-lookup"><span data-stu-id="156e2-122">Who are the end-users of the app?</span></span>
* <span data-ttu-id="156e2-123">Wie sollte die Onboardingerfahrung sein und was kann die App sonst noch tun?</span><span class="sxs-lookup"><span data-stu-id="156e2-123">How should the onboarding experience be and what else the app can do?</span></span>

## <a name="map-your-use-cases-to-teams-app-capabilities"></a><span data-ttu-id="156e2-124">Ordnen Sie Ihre Anwendungsfälle den Funktionen der Teams-App zu.</span><span class="sxs-lookup"><span data-stu-id="156e2-124">Map your use cases to Teams app capabilities</span></span>

<span data-ttu-id="156e2-125">[Map your use cases](../concepts/design/map-use-cases.md) covers some common scenarios and how to choose your app's capabilities.</span><span class="sxs-lookup"><span data-stu-id="156e2-125">[Map your use cases](../concepts/design/map-use-cases.md) covers some common scenarios and how to choose your app's capabilities.</span></span> <span data-ttu-id="156e2-126">Es werden Informationen zur Freigabe Ihrer App und zur Zusammenarbeit an Elementen in einem externen System bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="156e2-126">Information to share your app and collaborate on items in an external system is provided.</span></span> <span data-ttu-id="156e2-127">Sie können auch erfahren, wie Sie Workflows initiieren und Benachrichtigungen an Benutzer senden.</span><span class="sxs-lookup"><span data-stu-id="156e2-127">You can also learn how to initiate workflows and send notifications to users.</span></span> <span data-ttu-id="156e2-128">Erhalten Sie zusätzliche Tipps, wo Sie beginnen können, wie Sie soziale Netzwerke mit Benutzern, Unterhaltungsbots und die Kombination mehrerer Features erhalten.</span><span class="sxs-lookup"><span data-stu-id="156e2-128">Get additional tips on where to start, how to get social with users, conversational bots, and combining multiple features.</span></span>

## <a name="see-also"></a><span data-ttu-id="156e2-129">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="156e2-129">See also</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="156e2-130">Integrieren von Web-Apps in Teams</span><span class="sxs-lookup"><span data-stu-id="156e2-130">Integrate web apps with Teams</span></span>](../samples/integrating-web-apps.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="156e2-131">Erstellen Ihrer ersten Microsoft Teams-App</span><span class="sxs-lookup"><span data-stu-id="156e2-131">Build your first Microsoft Teams app</span></span>](../build-your-first-app/build-first-app-overview.md)

## <a name="next-step"></a><span data-ttu-id="156e2-132">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="156e2-132">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="156e2-133">Verstehen der Funktionen von Teams-Apps</span><span class="sxs-lookup"><span data-stu-id="156e2-133">Understand Teams app capabilities</span></span>](capabilities-overview.md)

