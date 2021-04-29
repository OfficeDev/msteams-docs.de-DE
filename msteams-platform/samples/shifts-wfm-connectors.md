---
title: Produktionsfertige Shifts-Connectors
description: Mitarbeiterverwaltung Verschiebt Connectors für Teams
ms.topic: reference
author: laujan
ms.date: 03/09/2020
localization_priority: Normal
keywords: Microsoft Teams Connectors kronos
ms.author: lajanuar
ms.openlocfilehash: 459797dd3f8425223c0dcbedc335955bf106ae37
ms.sourcegitcommit: d90c5dafea09e2893dea8da46ee49516bbaa04b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/28/2021
ms.locfileid: "52075738"
---
# <a name="production-ready-shifts-connectors"></a><span data-ttu-id="057e0-104">Produktionsfertige Shifts-Connectors</span><span class="sxs-lookup"><span data-stu-id="057e0-104">Production-ready Shifts Connectors</span></span>  

<span data-ttu-id="057e0-105">Teams Shifts Workforce Management (WFM)-Connectors sind produktionsbereite, Open-Source- und communitygesteuerte Integrationen, die für Mitarbeiter in erster Front nützlich sind.</span><span class="sxs-lookup"><span data-stu-id="057e0-105">Teams Shifts Workforce management (WFM) connectors are production-ready, open-source, and community-driven integrations, useful for firstline workers.</span></span> <span data-ttu-id="057e0-106">Sie bieten eine nahtlose Erfahrung und einen schnellen Prozess für die digitale Transformation von FirstLine-Mitarbeitern mit Teams Shifts.</span><span class="sxs-lookup"><span data-stu-id="057e0-106">They offer a seamless experience and quick process for the digital transformation of firstline workers with Teams Shifts.</span></span> 

<span data-ttu-id="057e0-107">Jeder Connector bietet detaillierte Anleitungen für die Bereitstellung und Integration in Ihre Organisation.</span><span class="sxs-lookup"><span data-stu-id="057e0-107">Each connector provides detailed guidance for deployment and integration to your organization.</span></span> <span data-ttu-id="057e0-108">Der vollständige Quellcode ist im GitHub-Repository verfügbar.</span><span class="sxs-lookup"><span data-stu-id="057e0-108">The complete source code is available in GitHub repository.</span></span> <span data-ttu-id="057e0-109">Sie können details oder fork untersuchen und anpassen, um Ihre spezifischen Anforderungen zu erfüllen.</span><span class="sxs-lookup"><span data-stu-id="057e0-109">You can explore in detail or fork, and customize to meet your specific needs.</span></span>   

<span data-ttu-id="057e0-110">Dieses Dokument enthält eine Übersicht über die wichtigsten Vorteile von Teams Shifts WFM Connectors, Kronos-to-Teams Shifts Connector und JDA-to-Teams Shifts Connector.</span><span class="sxs-lookup"><span data-stu-id="057e0-110">This document gives an overview of key benefits of Teams Shifts WFM connectors, Kronos-to-Teams Shifts connector, and JDA-to-Teams Shifts connector.</span></span>

## <a name="key-benefits-of-teams-shifts-wfm-connectors"></a><span data-ttu-id="057e0-111">Wichtige Vorteile von Teams Shifts WFM Connectors</span><span class="sxs-lookup"><span data-stu-id="057e0-111">Key benefits of Teams Shifts WFM connectors</span></span>

<span data-ttu-id="057e0-112">Nachfolgend finden Sie die wichtigsten Vorteile von Teams Shifts-WFM-Connectors:</span><span class="sxs-lookup"><span data-stu-id="057e0-112">Following are the key benefits of Teams Shifts WFM connectors:</span></span>

* <span data-ttu-id="057e0-113">**Plug -and-Play-Erfahrung:** Alle Shifts-WFM-Connectors enthalten ARM Azure-Bereitstellungsskripts, mit denen Sie alle erforderlichen Dienste in Microsoft Azure hosten können.</span><span class="sxs-lookup"><span data-stu-id="057e0-113">**Plug and play experience:** All Shifts WFM connectors include ARM Azure deployment scripts that allow you to host all necessary services in Microsoft Azure.</span></span> <span data-ttu-id="057e0-114">Für die Bereitstellung der Apps ist keine Codierung erforderlich.</span><span class="sxs-lookup"><span data-stu-id="057e0-114">No coding is required to deploy the apps.</span></span>

* <span data-ttu-id="057e0-115">**Produktionsbereiter Code:** Alle Shifts-Connectors entsprechen den empfohlenen bewährten Methoden für Sicherheit und Infrastruktur, und alle von der Community übermittelten Änderungen werden überprüft, um eine kontinuierliche Konformität sicherzustellen.</span><span class="sxs-lookup"><span data-stu-id="057e0-115">**Production-ready code:** All  Shifts connectors conform to the recommended security and infrastructure best practices and all community-submitted changes are reviewed to ensure continued conformance.</span></span>

* <span data-ttu-id="057e0-116">**Anpassbar und erweiterbar:**   Zwar sind alle Shifts-WFM-Connectors bereit für die sofortige Verwendung, wobei die gesamte Codebasis und Bereitstellungsskripts verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="057e0-116">**Customizable and extensible:**  While all Shifts WFM connectors are ready to deploy for immediate use, with the entire code base and deployment scripts readily available.</span></span> <span data-ttu-id="057e0-117">Sie können sie ganz einfach an Ihre individuellen Anforderungen anpassen oder erweitern.</span><span class="sxs-lookup"><span data-stu-id="057e0-117">You can easily customize or extend them to fit your unique needs.</span></span>

* <span data-ttu-id="057e0-118">**Ausführliche Dokumentation & Support:**   Alle Shifts-WFM-Connectors werden von einer End-to-End-Dokumentation für Lösungsarchitektur, Bereitstellung und Konfigurationsschritte begleitet.</span><span class="sxs-lookup"><span data-stu-id="057e0-118">**Detailed documentation & support:**  All Shifts WFM connectors are accompanied by end-to-end documentation for solution architecture, deployment, and configuration steps.</span></span> <span data-ttu-id="057e0-119">Die Connectorrepositorys werden überwacht, sodass Sie alle Probleme, Herausforderungen oder Schwierigkeiten melden können, die sie über den GitHub Issues Tracker des Repositorys haben.</span><span class="sxs-lookup"><span data-stu-id="057e0-119">The connector repositories are monitored, so that you can report any issues, challenges or difficulties you encounter through the repo's GitHub Issues tracker.</span></span>

* <span data-ttu-id="057e0-120">**Nahtlose Integration:** Durch die Integration zwischen WFM-Lösungen und Teams Shifts können Mitarbeiter von Firstline die Teams Shifts-App verwenden, um ihre Zeitpläne und Schichtzeiten ein- oder zu verwalten, und alle anderen features für die umfassende Zusammenarbeit, die in Teams bereitgestellt werden, direkt vom mobilen Gerät oder Desktop aus nutzen, ohne den Kontext auf eine andere App umschalten zu müssen.</span><span class="sxs-lookup"><span data-stu-id="057e0-120">**Seamless integration:** The integration between WFM solutions and Teams Shifts allows firstline workers to use the Teams Shifts app to view or manage their schedules and shift times, and use all the other rich collaboration features provided in Teams right from their mobile device or desktop without having to switch context to another app.</span></span>  

<span data-ttu-id="057e0-121">**Ansicht "Offene Schichten" in Teams**</span><span class="sxs-lookup"><span data-stu-id="057e0-121">**Open shifts view in Teams**</span></span> 

<span data-ttu-id="057e0-122">Die Verschiebungsansicht in Teams wird in der folgenden Abbildung angezeigt:</span><span class="sxs-lookup"><span data-stu-id="057e0-122">The shifts view in Teams is shown in the following image:</span></span> 

![Offene Schichten in Teams](../assets/images/teams-open-shifts-view.png)

## <a name="kronos-to-teams-shifts-connector"></a><span data-ttu-id="057e0-124">Kronos-zu-Teams-Schichtconnector</span><span class="sxs-lookup"><span data-stu-id="057e0-124">Kronos-to-Teams Shifts connector</span></span>

<span data-ttu-id="057e0-125">Mit Open-Source-Code können Sie Kronos Workforce Central Version 8.1 und höher mit Teams Shifts wie Desktop- oder mobilen Teams-Apps für die folgenden Firstline-Worker- und Managerszenarien integrieren:</span><span class="sxs-lookup"><span data-stu-id="057e0-125">With open-source code, you can integrate Kronos Workforce Central Version 8.1 and above, with Teams Shifts such as, desktop or mobile Teams app for the following firstline worker and manager scenarios:</span></span>

* <span data-ttu-id="057e0-126">Anzeigezeitplan.</span><span class="sxs-lookup"><span data-stu-id="057e0-126">View schedule.</span></span>

* <span data-ttu-id="057e0-127">Veröffentlichen und Anfordern offener Schichten.</span><span class="sxs-lookup"><span data-stu-id="057e0-127">Publish and request open shifts.</span></span>

* <span data-ttu-id="057e0-128">Swapverschiebungen.</span><span class="sxs-lookup"><span data-stu-id="057e0-128">Swap shifts.</span></span>

* <span data-ttu-id="057e0-129">Fordern Sie eine Auszeit an.</span><span class="sxs-lookup"><span data-stu-id="057e0-129">Request time off.</span></span>

* <span data-ttu-id="057e0-130">Bieten Sie Schichten an.</span><span class="sxs-lookup"><span data-stu-id="057e0-130">Offer shifts.</span></span>

<span data-ttu-id="057e0-131">Weitere Informationen zur Bereitstellung des Kronos-to-Teams Shifts-Connectors finden Sie unter [Abrufen auf GitHub](https://aka.ms/KronosShiftsConnector).</span><span class="sxs-lookup"><span data-stu-id="057e0-131">For more information on deployment of Kronos-to-Teams Shifts connector, see [Get it on GitHub](https://aka.ms/KronosShiftsConnector).</span></span>

## <a name="jda-to-teams-shifts-connector"></a><span data-ttu-id="057e0-132">JDA-zu-Teams-Schichtconnector</span><span class="sxs-lookup"><span data-stu-id="057e0-132">JDA-to-Teams Shifts connector</span></span>

<span data-ttu-id="057e0-133">Mit Open-Source-Code können Sie JDA, z. B. BlueYonder, Version 17.2 und höher, mit Teams Shifts wie Desktop- oder mobilen Teams-Apps für die folgenden FirstLine-Worker- und Managerszenarien integrieren:</span><span class="sxs-lookup"><span data-stu-id="057e0-133">With open-source code, you can integrate JDA, such as BlueYonder Version 17.2 and above, with Teams Shifts  such as, desktop or mobile Teams app for the following firstline worker and manager scenarios:</span></span>

* <span data-ttu-id="057e0-134">Veröffentlichen Sie Schichten und Planen von Gruppen in JDA, und zeigen Sie sie in Teams an.</span><span class="sxs-lookup"><span data-stu-id="057e0-134">Publish shifts and schedule groups in JDA and view them in Teams.</span></span>

* <span data-ttu-id="057e0-135">Aktivieren Sie umfangreiche Zeitplanungsszenarien, einschließlich anfordern von Schichtswaps und Auszeit.</span><span class="sxs-lookup"><span data-stu-id="057e0-135">Enable rich scheduling scenarios, including requesting shift swaps and time off.</span></span>

* <span data-ttu-id="057e0-136">Festlegen der Benutzerverfügbarkeit mithilfe der [Microsoft Graph-API für Schichten](/graph/api/resources/shift?view=graph-rest-beta&preserve-view=true).</span><span class="sxs-lookup"><span data-stu-id="057e0-136">Set user availability using the [Microsoft Graph API for Shifts](/graph/api/resources/shift?view=graph-rest-beta&preserve-view=true).</span></span>

<span data-ttu-id="057e0-137">Weitere Informationen zu Beitrag und Vorschlag finden Sie unter [Get it on GitHub](https://aka.ms/JDAShiftsConnector).</span><span class="sxs-lookup"><span data-stu-id="057e0-137">For more information on contribution and suggestion, see [Get it on GitHub](https://aka.ms/JDAShiftsConnector).</span></span></br></br>

## <a name="see-also"></a><span data-ttu-id="057e0-138">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="057e0-138">See also</span></span>

[<span data-ttu-id="057e0-139">Integrieren von Web-Apps</span><span class="sxs-lookup"><span data-stu-id="057e0-139">Integrate web apps</span></span>](~/samples/integrate-web-apps-overview.md)
