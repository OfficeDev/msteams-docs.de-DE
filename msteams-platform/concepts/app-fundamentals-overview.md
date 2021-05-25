---
title: Übersicht über die Grundlagen der App-Entwicklung
author: heath-hamilton
description: Beschreiben der grundlegenden Konzepte Teams Plattformentwicklung.
ms.topic: conceptual
localization_priority: Normal
ms.author: lajanuar
ms.openlocfilehash: 1ecae34c38950f16e49fc123f73bdc746c4b28cc
ms.sourcegitcommit: e1fe46c574cec378319814f8213209ad3063b2c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2021
ms.locfileid: "52630158"
---
# <a name="microsoft-teams-app-development-fundamentals"></a><span data-ttu-id="8c361-103">Microsoft Teams der App-Entwicklung</span><span class="sxs-lookup"><span data-stu-id="8c361-103">Microsoft Teams app development fundamentals</span></span>

<span data-ttu-id="8c361-104">Microsoft Teams-App-Grundlagen geben die Richtung, die Sie zum Erstellen Ihrer benutzerdefinierten app Teams müssen.</span><span class="sxs-lookup"><span data-stu-id="8c361-104">Microsoft Teams app fundamentals give the direction you need to create your custom Teams app.</span></span> <span data-ttu-id="8c361-105">Sie können das framework erkennen, das erforderlich ist, um Ihre Teams planen.</span><span class="sxs-lookup"><span data-stu-id="8c361-105">You can recognize the framework required to plan your Teams app.</span></span> <span data-ttu-id="8c361-106">Das Dokument hilft Ihnen, die Benutzer-App-Kommunikation zu verstehen und herauszufinden, welche Art von App-Oberflächen Sie verwenden müssen oder welche APIs Ihre App dabei möglicherweise benötigt.</span><span class="sxs-lookup"><span data-stu-id="8c361-106">The document helps you to understand the user-app communication and figure out the kind of app surfaces you need to use or the APIs your app might require in the process.</span></span> <span data-ttu-id="8c361-107">Lassen Sie sich inspirieren, interaktiv zu sein, um die App-Erfahrung zu vertiefen, wenn Sie sich in Teams.</span><span class="sxs-lookup"><span data-stu-id="8c361-107">Get some inspiration to embrace interactivity that can deepen the app experience when you integrate with Teams.</span></span>

## <a name="capabilities-and-entry-points"></a><span data-ttu-id="8c361-108">Funktionen und Einstiegspunkte</span><span class="sxs-lookup"><span data-stu-id="8c361-108">Capabilities and entry points</span></span>

<span data-ttu-id="8c361-109">Sie können Ihre Teams app auf verschiedene Weise erweitern.</span><span class="sxs-lookup"><span data-stu-id="8c361-109">You can extend your Teams app in multiple ways.</span></span> <span data-ttu-id="8c361-110">Um Ihre App erweitern zu können, müssen Sie alle zentralen Funktionen und Einstiegspunkte kennen, die in einem gemeinsamen Raum funktionieren.</span><span class="sxs-lookup"><span data-stu-id="8c361-110">To be able to extend your app you must understand all the core capabilities and the entry points that work in a collaborative space.</span></span> <span data-ttu-id="8c361-111">Sie können mit den Erweiterungspunkten für das Erstellen Ihrer Apps experimentieren.</span><span class="sxs-lookup"><span data-stu-id="8c361-111">You can experiment with the extension points for building your apps.</span></span> <span data-ttu-id="8c361-112">Wichtige App-Projektkomponenten helfen Ihnen bei der ordnungsgemäßen Konfiguration Ihrer App-Seite.</span><span class="sxs-lookup"><span data-stu-id="8c361-112">Important app project components help you to correctly configure your app page.</span></span> <span data-ttu-id="8c361-113">Teams App kann über [mehrere Funktionen und](../concepts/capabilities-overview.md) [Einstiegspunkte verfügen.](../concepts/extensibility-points.md)</span><span class="sxs-lookup"><span data-stu-id="8c361-113">Teams app can have [multiple capabilities](../concepts/capabilities-overview.md) and [entry points](../concepts/extensibility-points.md).</span></span>

## <a name="understand-your-use-cases"></a><span data-ttu-id="8c361-114">Grundlegendes zu Ihren Anwendungsfällen</span><span class="sxs-lookup"><span data-stu-id="8c361-114">Understand your use cases</span></span>

<span data-ttu-id="8c361-115">Sie können Benutzerprobleme erkennen und die Antworten auf einige häufige Probleme identifizieren, mit denen die Benutzer zu kämpfen haben.</span><span class="sxs-lookup"><span data-stu-id="8c361-115">You can recognize user issues and identify the answers to some common problems the users face.</span></span> <span data-ttu-id="8c361-116">Sie können Ihre Teams erstellen, indem Sie die richtige Kombination finden, um die Anforderungen Ihres Benutzers zu erfüllen.</span><span class="sxs-lookup"><span data-stu-id="8c361-116">You can build your Teams app by finding the right combination to meet your user's needs.</span></span> <span data-ttu-id="8c361-117">[Verstehen von Anwendungsfällen,](../concepts/design/understand-use-cases.md) um zu wissen, wie ein Endbenutzer mit Ihrer App interagiert.</span><span class="sxs-lookup"><span data-stu-id="8c361-117">[Understand use cases](../concepts/design/understand-use-cases.md) to know how an end-user interacts with your app.</span></span> <span data-ttu-id="8c361-118">Sie lernen, den Benutzer und sein Problem zu verstehen.</span><span class="sxs-lookup"><span data-stu-id="8c361-118">You learn to understand the user and their problem.</span></span> <span data-ttu-id="8c361-119">Einige häufig beantwortete Fragen sind wie folgt:</span><span class="sxs-lookup"><span data-stu-id="8c361-119">Some common questions answered are as follows:</span></span>

* <span data-ttu-id="8c361-120">Benötigen Sie Authentifizierung?</span><span class="sxs-lookup"><span data-stu-id="8c361-120">Do you need authentication?</span></span>
* <span data-ttu-id="8c361-121">Welches Problem wird ihre App lösen?</span><span class="sxs-lookup"><span data-stu-id="8c361-121">What problem is your app going to solve?</span></span>
* <span data-ttu-id="8c361-122">Wer sind die Endbenutzer der App?</span><span class="sxs-lookup"><span data-stu-id="8c361-122">Who are the end-users of the app?</span></span>
* <span data-ttu-id="8c361-123">Wie sollte die Onboardingerfahrung sein und was kann die App sonst noch tun?</span><span class="sxs-lookup"><span data-stu-id="8c361-123">How should the onboarding experience be and what else the app can do?</span></span>

## <a name="map-your-use-cases-to-teams-app-capabilities"></a><span data-ttu-id="8c361-124">Ordnen Sie Ihre Anwendungsfälle Teams App-Funktionen zu.</span><span class="sxs-lookup"><span data-stu-id="8c361-124">Map your use cases to Teams app capabilities</span></span>

<span data-ttu-id="8c361-125">[Map your use cases](../concepts/design/map-use-cases.md) covers some common scenarios and how to choose your app's capabilities.</span><span class="sxs-lookup"><span data-stu-id="8c361-125">[Map your use cases](../concepts/design/map-use-cases.md) covers some common scenarios and how to choose your app's capabilities.</span></span> <span data-ttu-id="8c361-126">Es werden Informationen zur Freigabe Ihrer App und zur Zusammenarbeit an Elementen in einem externen System bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="8c361-126">Information to share your app and collaborate on items in an external system is provided.</span></span> <span data-ttu-id="8c361-127">Sie können auch erfahren, wie Sie Workflows initiieren und Benachrichtigungen an Benutzer senden.</span><span class="sxs-lookup"><span data-stu-id="8c361-127">You can also learn how to initiate workflows and send notifications to users.</span></span> <span data-ttu-id="8c361-128">Erhalten Sie zusätzliche Tipps, wo Sie beginnen können, wie Sie soziale Netzwerke mit Benutzern, Unterhaltungsbots und die Kombination mehrerer Features erhalten.</span><span class="sxs-lookup"><span data-stu-id="8c361-128">Get additional tips on where to start, how to get social with users, conversational bots, and combining multiple features.</span></span>

## <a name="see-also"></a><span data-ttu-id="8c361-129">Sehen Sie ebenfalls</span><span class="sxs-lookup"><span data-stu-id="8c361-129">See also</span></span>

* [<span data-ttu-id="8c361-130">Integrieren von Web-Apps in Teams</span><span class="sxs-lookup"><span data-stu-id="8c361-130">Integrate web apps with Teams</span></span>](../samples/integrating-web-apps.md)
* [<span data-ttu-id="8c361-131">Erstellen Ihrer ersten Microsoft Teams App</span><span class="sxs-lookup"><span data-stu-id="8c361-131">Build your first Microsoft Teams app</span></span>](../build-your-first-app/build-first-app-overview.md)

## <a name="next-step"></a><span data-ttu-id="8c361-132">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="8c361-132">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="8c361-133">Verstehen Teams App-Funktionen</span><span class="sxs-lookup"><span data-stu-id="8c361-133">Understand Teams app capabilities</span></span>](capabilities-overview.md)

