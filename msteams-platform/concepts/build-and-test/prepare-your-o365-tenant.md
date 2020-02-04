---
title: Vorbereiten des Office 365 Mandanten
description: Erste Schritte mit Microsoft Teams in Office 365
keywords: Konfigurieren des Uploads von Office 365 Mandanten Teams
ms.openlocfilehash: 62cd640196631f50c72762253ff1bd75a143337d
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674445"
---
# <a name="prepare-your-office-365-tenant"></a><span data-ttu-id="b3c96-104">Vorbereiten des Office 365 Mandanten</span><span class="sxs-lookup"><span data-stu-id="b3c96-104">Prepare your Office 365 tenant</span></span>

<span data-ttu-id="b3c96-105">Um Apps für Microsoft Teams zu entwickeln, müssen Sie ein [Office 365 Kunde mit einem der folgenden Pläne](https://products.office.com/business/compare-more-office-365-for-business-plans)sein.</span><span class="sxs-lookup"><span data-stu-id="b3c96-105">To develop apps for Microsoft Teams, you need to be an [Office 365 customer with one of the following plans](https://products.office.com/business/compare-more-office-365-for-business-plans).</span></span>

* <span data-ttu-id="b3c96-106">Business Essentials</span><span class="sxs-lookup"><span data-stu-id="b3c96-106">Business Essentials</span></span>
* <span data-ttu-id="b3c96-107">Business Premium</span><span class="sxs-lookup"><span data-stu-id="b3c96-107">Business Premium</span></span>
* <span data-ttu-id="b3c96-108">Enterprise E1, E3 und E5</span><span class="sxs-lookup"><span data-stu-id="b3c96-108">Enterprise E1, E3, and E5</span></span>
* <span data-ttu-id="b3c96-109">Developer</span><span class="sxs-lookup"><span data-stu-id="b3c96-109">Developer</span></span>
* <span data-ttu-id="b3c96-110">Education, Education Plus und Education E5</span><span class="sxs-lookup"><span data-stu-id="b3c96-110">Education, Education Plus, and Education E5</span></span>

<span data-ttu-id="b3c96-111">Microsoft Teams steht Kunden, die E4 vor dem Ruhestand erworben haben, ebenfalls zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="b3c96-111">Microsoft Teams will also be available to customers who purchased E4 prior to its retirement.</span></span>

## <a name="just-need-a-development-environment"></a><span data-ttu-id="b3c96-112">Sie benötigen lediglich eine Entwicklungsumgebung?</span><span class="sxs-lookup"><span data-stu-id="b3c96-112">Just need a development environment?</span></span>

<span data-ttu-id="b3c96-113">Wenn Sie derzeit kein Office 365 Konto haben, können Sie sich für das Office 365- [Entwicklerprogramm](https://dev.office.com/devprogram) registrieren, um eine *﻿Kostenlose* 90 Tage (kann verlängert werden, solange Sie es für die Entwicklungsaktivität verwenden) Office 365 Entwickler Mandanten zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="b3c96-113">If you don't currently have an Office 365 account, you can sign up for the [Office 365 Developer program](https://dev.office.com/devprogram) to get a *free* 90 days (can be renewed for as long as you're using it for development activity) Office 365 Developer Tenant.</span></span> <span data-ttu-id="b3c96-114">Dieses Konto kann nur zu Testzwecken verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="b3c96-114">This account can only be used for testing purposes.</span></span> <span data-ttu-id="b3c96-115">Weitere Informationen finden Sie unter [Einrichten von Testkonten](https://support.office.com/article/Add-users-individually-or-in-bulk-to-Office-365-Admin-Help-1970f7d6-03b5-442f-b385-5880b9c256ec?ui=en-US&rs=en-US&ad=US).</span><span class="sxs-lookup"><span data-stu-id="b3c96-115">See more information on [setting up your test accounts](https://support.office.com/article/Add-users-individually-or-in-bulk-to-Office-365-Admin-Help-1970f7d6-03b5-442f-b385-5880b9c256ec?ui=en-US&rs=en-US&ad=US).</span></span>

## <a name="enable-microsoft-teams-for-your-organization"></a><span data-ttu-id="b3c96-116">Aktivieren von Microsoft Teams für Ihre Organisation</span><span class="sxs-lookup"><span data-stu-id="b3c96-116">Enable Microsoft Teams for your organization</span></span>

<span data-ttu-id="b3c96-117">Wenn Microsoft Teams noch nicht für Ihre Organisation aktiviert ist, müssen Sie dies zunächst tun.</span><span class="sxs-lookup"><span data-stu-id="b3c96-117">If Microsoft Teams is not yet enabled for your organization, you'll need to do that first.</span></span> <span data-ttu-id="b3c96-118">Werfen Sie einen Blick auf unsere detaillierten Anleitungen für [die Aktivierung von Teams für Ihre Organisation](/microsoftteams/how-to-roll-out-teams).</span><span class="sxs-lookup"><span data-stu-id="b3c96-118">Take a look at our detailed guidance for [enabling Teams for your organization](/microsoftteams/how-to-roll-out-teams).</span></span>

## <a name="enable-custom-teams-apps-and-turn-on-custom-app-uploading"></a><span data-ttu-id="b3c96-119">Aktivieren benutzerdefinierter Teams-apps und Aktivieren des benutzerdefinierten App-Uploads</span><span class="sxs-lookup"><span data-stu-id="b3c96-119">Enable custom Teams apps and turn on custom app uploading</span></span>

> <span data-ttu-id="b3c96-120">Hinweis: Wenn Sie eine O365-Entwickler Organisation zum Erstellen Ihrer APP verwenden, sollten diese Einstellungen bereits so konfiguriert sein, dass Sie Ihre APP erstellen, hochladen und testen können.</span><span class="sxs-lookup"><span data-stu-id="b3c96-120">Note: If you're using an O365 Developer Organization to build your app, these settings should already be configured to allow you to build, upload and test your app.</span></span>

<span data-ttu-id="b3c96-121">Es gibt drei Einstellungen für die Aktivierung benutzerdefinierter apps und benutzerdefinierter App-Uploads:</span><span class="sxs-lookup"><span data-stu-id="b3c96-121">There are three settings involved in enabling custom apps and custom app uploading:</span></span>

* <span data-ttu-id="b3c96-122">**Org-weite benutzerdefinierte app-Einstellung** – mit dieser Einstellung können Sie benutzerdefinierte Apps für Ihre Organisation entweder aktivieren oder deaktivieren.</span><span class="sxs-lookup"><span data-stu-id="b3c96-122">**Org-wide custom app setting** - This setting either enables or disables custom apps for your organization.</span></span> <span data-ttu-id="b3c96-123">Es muss eingeschaltet sein.</span><span class="sxs-lookup"><span data-stu-id="b3c96-123">It needs to be on.</span></span> 
* <span data-ttu-id="b3c96-124">**Einstellung für Team benutzerdefinierte App** : Diese Einstellung gilt für jedes einzelne Team in Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="b3c96-124">**Team custom app setting** - This setting is for each individual team inside Microsoft Teams.</span></span> <span data-ttu-id="b3c96-125">Wenn Sie Ihre APP für ein bestimmtes Team installieren möchten, muss diese für dieses Team eingeschaltet sein.</span><span class="sxs-lookup"><span data-stu-id="b3c96-125">If you want to install your app for a specific team, this will need to be on for that team.</span></span>
* <span data-ttu-id="b3c96-126">**Benutzerdefinierte App-Richtlinie** – diese Gruppe von Einstellungen steuert die Berechtigungen für einen einzelnen Benutzer.</span><span class="sxs-lookup"><span data-stu-id="b3c96-126">**User custom app policy** - This set of settings controls the permissions for an individual user.</span></span> <span data-ttu-id="b3c96-127">Sie müssen dies für Personen aktivieren, die benutzerdefinierte apps hochladen möchten.</span><span class="sxs-lookup"><span data-stu-id="b3c96-127">You'll need to enable this for individuals you want to upload custom apps.</span></span>

<span data-ttu-id="b3c96-128">Umfassende Informationen zur Interaktion dieser Einstellungen finden Sie unter [Verwalten benutzerdefinierter App-Richtlinien und-Einstellungen in Microsoft Teams](/MicrosoftTeams/teams-custom-app-policies-and-settings).</span><span class="sxs-lookup"><span data-stu-id="b3c96-128">For complete information on how these settings interact see [Manage custom app policies and settings in Microsoft Teams](/MicrosoftTeams/teams-custom-app-policies-and-settings).</span></span>
