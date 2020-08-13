---
title: Vorbereiten der Entwicklungsumgebung für Teams
description: Einrichten der Umgebung für die Entwicklung von Apps für Teams
keywords: Konfigurieren von Office 365 Mandanten Teams hochladen der Umgebungs Entwicklung
ms.openlocfilehash: 701c6c110026007cf1670e783348bbdbe1aff498
ms.sourcegitcommit: 9fbc701a9a039ecdc360aefbe86df52b9c3593f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/12/2020
ms.locfileid: "46652018"
---
# <a name="prepare-your-development-environment"></a><span data-ttu-id="95054-104">Vorbereiten Ihrer Entwicklungsumgebung</span><span class="sxs-lookup"><span data-stu-id="95054-104">Prepare your development environment</span></span>

<span data-ttu-id="95054-105">Wenn Sie ein Office 365 Abonnent sind, können Sie Apps für Microsoft Teams mit einem der folgenden [Pläne](https://products.office.com/business/compare-more-office-365-for-business-plans)entwickeln:</span><span class="sxs-lookup"><span data-stu-id="95054-105">If you are an Office 365 subscriber, you can develop apps for Microsoft Teams with one of the following [plans](https://products.office.com/business/compare-more-office-365-for-business-plans):</span></span>

* <span data-ttu-id="95054-106">Business Essentials</span><span class="sxs-lookup"><span data-stu-id="95054-106">Business Essentials</span></span>
* <span data-ttu-id="95054-107">Business Premium</span><span class="sxs-lookup"><span data-stu-id="95054-107">Business Premium</span></span>
* <span data-ttu-id="95054-108">Enterprise E1, E3 und E5</span><span class="sxs-lookup"><span data-stu-id="95054-108">Enterprise E1, E3, and E5</span></span>
* <span data-ttu-id="95054-109">Developer</span><span class="sxs-lookup"><span data-stu-id="95054-109">Developer</span></span>
* <span data-ttu-id="95054-110">Education, Education Plus und Education E5</span><span class="sxs-lookup"><span data-stu-id="95054-110">Education, Education Plus, and Education E5</span></span>

<span data-ttu-id="95054-111">Microsoft Teams steht auch Kunden, die E4 abonniert haben, vor dem [Ruhestand](https://support.office.com//article/important-information-for-office-365-enterprise-e4-customers-f9572348-43a2-43fa-a3d8-3b6c9c042147)zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="95054-111">Microsoft Teams will also be available to customers who subscribed to E4 prior to its [retirement](https://support.office.com//article/important-information-for-office-365-enterprise-e4-customers-f9572348-43a2-43fa-a3d8-3b6c9c042147).</span></span>

## <a name="just-need-a-development-environment"></a><span data-ttu-id="95054-112">Sie benötigen lediglich eine Entwicklungsumgebung?</span><span class="sxs-lookup"><span data-stu-id="95054-112">Just need a development environment?</span></span>

<span data-ttu-id="95054-113">Wenn Sie derzeit kein Office 365 Konto haben, können Sie sich für ein [Microsoft 365-Entwicklerprogramm](https://developer.microsoft.com/microsoft-365/dev-program) Abonnement anmelden.</span><span class="sxs-lookup"><span data-stu-id="95054-113">If you don't currently have an Office 365 account, you can sign up for a [Microsoft 365 Developer Program](https://developer.microsoft.com/microsoft-365/dev-program) subscription.</span></span> <span data-ttu-id="95054-114">Es ist für 90 Tage *kostenlos* und wird ständig erneuert, solange Sie es für Entwicklungsaktivitäten verwenden.</span><span class="sxs-lookup"><span data-stu-id="95054-114">It's *free* for 90 days and will continually renew as long as you're using it for development activity.</span></span> <span data-ttu-id="95054-115">Wenn Sie über ein Visual Studio *Enterprise* -oder *Professional* -Abonnement verfügen, enthalten beide Programme ein kostenloses Microsoft 365- [Entwickler Abonnement](https://aka.ms/MyVisualStudioBenefits), das für die Dauer Ihres Visual Studio Abonnements aktiv ist.</span><span class="sxs-lookup"><span data-stu-id="95054-115">If you have a Visual Studio *Enterprise* or *Professional* subscription, both programs include a free Microsoft 365 [developer subscription](https://aka.ms/MyVisualStudioBenefits), active for the life of your Visual Studio subscription.</span></span> <span data-ttu-id="95054-116">*Weitere Informationen finden Sie unter* [Einrichten eines Microsoft 365 Developer-Abonnements](https://docs.microsoft.com/office/developer-program/office-365-developer-program-get-started).</span><span class="sxs-lookup"><span data-stu-id="95054-116">*See* [Set up a Microsoft 365 developer subscription](https://docs.microsoft.com/office/developer-program/office-365-developer-program-get-started).</span></span>

## <a name="enable-microsoft-teams-for-your-organization"></a><span data-ttu-id="95054-117">Aktivieren von Microsoft Teams für Ihre Organisation</span><span class="sxs-lookup"><span data-stu-id="95054-117">Enable Microsoft Teams for your organization</span></span>

<span data-ttu-id="95054-118">Wenn Microsoft Teams nicht für Ihre Organisation aktiviert wurde, müssen Sie dies zunächst tun.</span><span class="sxs-lookup"><span data-stu-id="95054-118">If Microsoft Teams has not been enabled for your organization, you'll need to do that first.</span></span> <span data-ttu-id="95054-119">Werfen Sie einen Blick auf unsere detaillierten Anleitungen für [die Aktivierung von Teams für Ihre Organisation](https://docs.microsoft.com/microsoftteams/enable-features-office-365).</span><span class="sxs-lookup"><span data-stu-id="95054-119">Take a look at our detailed guidance for [enabling Teams for your organization](https://docs.microsoft.com/microsoftteams/enable-features-office-365).</span></span>

## <a name="enable-custom-teams-apps-and-turn-on-custom-app-uploading"></a><span data-ttu-id="95054-120">Aktivieren benutzerdefinierter Teams-apps und Aktivieren des benutzerdefinierten App-Uploads</span><span class="sxs-lookup"><span data-stu-id="95054-120">Enable custom Teams apps and turn on custom app uploading</span></span>

<span data-ttu-id="95054-121">Aktivieren Sie wie folgt benutzerdefinierte App-Sideloading für den Entwickler Mandanten:</span><span class="sxs-lookup"><span data-stu-id="95054-121">Turn on custom app sideloading for your developer tenant as follows:</span></span>

1. <span data-ttu-id="95054-122">Melden Sie sich bei [Microsoft 365 Admin Center](https://admin.microsoft.com/Adminportal/Home?source=applauncher#/homepage#/) mit Ihren Administratoranmeldeinformationen an.</span><span class="sxs-lookup"><span data-stu-id="95054-122">Login to [Microsoft 365 admin center](https://admin.microsoft.com/Adminportal/Home?source=applauncher#/homepage#/) with your admin credential.</span></span> 

2. <span data-ttu-id="95054-123">Wählen Sie **alle**  -->  **Teams**anzeigen aus.</span><span class="sxs-lookup"><span data-stu-id="95054-123">Select **Show All** --> **Teams**.</span></span> 

![Bild des Menüs "App-Überlauf"](~/assets/images/prepare-test-tenant/admin-center.png)

3. <span data-ttu-id="95054-125">Navigieren Sie zu **Teams**  -->  -**Setup Richtlinien**für apps  -->  **Global (organisationsweit Standard)**</span><span class="sxs-lookup"><span data-stu-id="95054-125">Navigate to **Teams apps** --> **Setup Policies** --> **Global(Org-wide default)**</span></span>  

![Bild des Menüs "App-Überlauf"](~/assets/images/prepare-test-tenant/turn-on-sideload.png)

4. <span data-ttu-id="95054-127">Schalten Sie **benutzerdefinierte apps** in die Position **on** hoch.</span><span class="sxs-lookup"><span data-stu-id="95054-127">Toggle **upload custom apps** to the **on** position.</span></span>

<span data-ttu-id="95054-128">Das ist alles.</span><span class="sxs-lookup"><span data-stu-id="95054-128">That's it!</span></span> <span data-ttu-id="95054-129">Der Testmandant lässt jetzt benutzerdefinierte App-Sideloading.</span><span class="sxs-lookup"><span data-stu-id="95054-129">Your test tenant will now allow custom app sideloading.</span></span>

> [!Note] 
> <span data-ttu-id="95054-130">Es kann bis zu 24 Stunden dauern, bis Sideloading aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="95054-130">It can take up to 24 hours before sideloading is enabled.</span></span> <span data-ttu-id="95054-131">Während der Zwischenzeit können Sie \*\*Upload for \<your tenant> \*\* verwenden, um Ihre APP zu testen.</span><span class="sxs-lookup"><span data-stu-id="95054-131">During interim, you can use **upload for \<your tenant>** to test your app.</span></span>

![Bild des Menüs "App-Überlauf"](~/assets/images/prepare-test-tenant/upload-for-contoso.png)

<span data-ttu-id="95054-133">Umfassende Informationen zur Interaktion dieser Einstellungen *finden Sie unter* [Verwalten benutzerdefinierter App-Richtlinien und-Einstellungen in Microsoft Teams](https://docs.microsoft.com/microsoftteams/teams-custom-app-policies-and-settings) und [Verwalten von App-Setup Richtlinien in Microsoft Teams](https://docs.microsoft.com/microsoftteams/teams-app-setup-policies).</span><span class="sxs-lookup"><span data-stu-id="95054-133">For complete information on how these settings interact, *See*, [Manage custom app policies and settings in Microsoft Teams](https://docs.microsoft.com/microsoftteams/teams-custom-app-policies-and-settings) and [Manage app setup policies in Microsoft Teams](https://docs.microsoft.com/microsoftteams/teams-app-setup-policies).</span></span>