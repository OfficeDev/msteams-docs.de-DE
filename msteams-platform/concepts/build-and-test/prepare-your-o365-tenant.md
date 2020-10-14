---
title: Vorbereiten Ihres Microsoft 365-Mandanten
description: Erste Schritte mit Microsoft Teams in Microsoft 365
keywords: Konfigurieren des Uploads von Microsoft 365-Mandanten Teams
ms.openlocfilehash: 67a0342a7e8605097eed53dd1b0bdf273d537c0e
ms.sourcegitcommit: d61f14053fc695bc1956bf50e83956613c19ccca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/13/2020
ms.locfileid: "48452764"
---
# <a name="prepare-your-microsoft-365-tenant"></a><span data-ttu-id="ad517-104">Vorbereiten Ihres Microsoft 365-Mandanten</span><span class="sxs-lookup"><span data-stu-id="ad517-104">Prepare your Microsoft 365 tenant</span></span>

<span data-ttu-id="ad517-105">Wenn Sie ein Microsoft 365-Abonnent sind, können Sie Apps für Microsoft Teams mit einem der folgenden [Pläne](https://products.office.com/business/compare-more-office-365-for-business-plans)entwickeln:</span><span class="sxs-lookup"><span data-stu-id="ad517-105">If you are a Microsoft 365 subscriber, you can develop apps for Microsoft Teams with one of the following [plans](https://products.office.com/business/compare-more-office-365-for-business-plans):</span></span>

* <span data-ttu-id="ad517-106">Standard</span><span class="sxs-lookup"><span data-stu-id="ad517-106">Basic</span></span>
* <span data-ttu-id="ad517-107">Standard</span><span class="sxs-lookup"><span data-stu-id="ad517-107">Standard</span></span>
* <span data-ttu-id="ad517-108">Enterprise E1, E3 und E5</span><span class="sxs-lookup"><span data-stu-id="ad517-108">Enterprise E1, E3, and E5</span></span>
* <span data-ttu-id="ad517-109">Developer</span><span class="sxs-lookup"><span data-stu-id="ad517-109">Developer</span></span>
* <span data-ttu-id="ad517-110">Education, Education Plus und Education E5</span><span class="sxs-lookup"><span data-stu-id="ad517-110">Education, Education Plus, and Education E5</span></span>

<span data-ttu-id="ad517-111">Microsoft Teams steht auch Kunden, die E4 abonniert haben, vor dem [Ruhestand](https://support.office.com//article/important-information-for-office-365-enterprise-e4-customers-f9572348-43a2-43fa-a3d8-3b6c9c042147)zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="ad517-111">Microsoft Teams will also be available to customers who subscribed to E4 prior to its [retirement](https://support.office.com//article/important-information-for-office-365-enterprise-e4-customers-f9572348-43a2-43fa-a3d8-3b6c9c042147).</span></span>

## <a name="just-need-a-development-environment"></a><span data-ttu-id="ad517-112">Sie benötigen lediglich eine Entwicklungsumgebung?</span><span class="sxs-lookup"><span data-stu-id="ad517-112">Just need a development environment?</span></span>

<span data-ttu-id="ad517-113">Wenn Sie derzeit kein Microsoft 365-Konto haben, können Sie sich für ein [Microsoft 365-Entwicklerprogramm](https://developer.microsoft.com/microsoft-365/dev-program) Abonnement anmelden.</span><span class="sxs-lookup"><span data-stu-id="ad517-113">If you don't currently have a Microsoft 365 account, you can sign up for a [Microsoft 365 Developer Program](https://developer.microsoft.com/microsoft-365/dev-program) subscription.</span></span> <span data-ttu-id="ad517-114">Es ist für 90 Tage *kostenlos* und wird ständig erneuert, solange Sie es für Entwicklungsaktivitäten verwenden.</span><span class="sxs-lookup"><span data-stu-id="ad517-114">It's *free* for 90 days and will continually renew as long as you're using it for development activity.</span></span> <span data-ttu-id="ad517-115">Wenn Sie über ein Visual Studio *Enterprise* -oder *Professional* -Abonnement verfügen, enthalten beide Programme ein kostenloses Microsoft 365- [Entwickler Abonnement](https://aka.ms/MyVisualStudioBenefits), das für die Dauer Ihres Visual Studio Abonnements aktiv ist.</span><span class="sxs-lookup"><span data-stu-id="ad517-115">If you have a Visual Studio *Enterprise* or *Professional* subscription, both programs include a free Microsoft 365 [developer subscription](https://aka.ms/MyVisualStudioBenefits), active for the life of your Visual Studio subscription.</span></span> <span data-ttu-id="ad517-116">*Weitere Informationen finden Sie unter* [Einrichten eines Microsoft 365 Developer-Abonnements](https://docs.microsoft.com/office/developer-program/office-365-developer-program-get-started).</span><span class="sxs-lookup"><span data-stu-id="ad517-116">*See* [Set up a Microsoft 365 developer subscription](https://docs.microsoft.com/office/developer-program/office-365-developer-program-get-started).</span></span>

## <a name="enable-microsoft-teams-for-your-organization"></a><span data-ttu-id="ad517-117">Aktivieren von Microsoft Teams für Ihre Organisation</span><span class="sxs-lookup"><span data-stu-id="ad517-117">Enable Microsoft Teams for your organization</span></span> 

<span data-ttu-id="ad517-118">Wenn Microsoft Teams nicht für Ihre Organisation aktiviert wurde, müssen Sie dies zunächst tun.</span><span class="sxs-lookup"><span data-stu-id="ad517-118">If Microsoft Teams has not been enabled for your organization, you'll need to do that first.</span></span> <span data-ttu-id="ad517-119">Werfen Sie einen Blick auf unsere detaillierten Anleitungen für [die Aktivierung von Teams für Ihre Organisation](/microsoftteams/enable-features-office-365).</span><span class="sxs-lookup"><span data-stu-id="ad517-119">Take a look at our detailed guidance for [enabling Teams for your organization](/microsoftteams/enable-features-office-365).</span></span>

## <a name="enable-custom-teams-apps-and-turn-on-custom-app-uploading"></a><span data-ttu-id="ad517-120">Aktivieren benutzerdefinierter Teams-apps und Aktivieren des benutzerdefinierten App-Uploads</span><span class="sxs-lookup"><span data-stu-id="ad517-120">Enable custom Teams apps and turn on custom app uploading</span></span>

<span data-ttu-id="ad517-121">Aktivieren Sie wie folgt benutzerdefinierte App-Sideloading für den Entwickler Mandanten:</span><span class="sxs-lookup"><span data-stu-id="ad517-121">Turn on custom app sideloading for your developer tenant as follows:</span></span>

1. <span data-ttu-id="ad517-122">Melden Sie sich bei [Microsoft 365 Admin Center](https://admin.microsoft.com/Adminportal/Home?source=applauncher#/homepage#/) mit Ihren Administratoranmeldeinformationen an.</span><span class="sxs-lookup"><span data-stu-id="ad517-122">Login to [Microsoft 365 admin center](https://admin.microsoft.com/Adminportal/Home?source=applauncher#/homepage#/) with your admin credential.</span></span> 

2. <span data-ttu-id="ad517-123">Wählen Sie **alle**  -->  **Teams**anzeigen aus.</span><span class="sxs-lookup"><span data-stu-id="ad517-123">Select **Show All** --> **Teams**.</span></span> 

![Bild des Admin Center-Menüs](~/assets/images/prepare-test-tenant/admin-center.png)

> [!Note] 
> <span data-ttu-id="ad517-125">Es kann bis zu 24 Stunden dauern, bis die Option "Teams" angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="ad517-125">It can take up to 24 hours for the "Teams" option to appear.</span></span> <span data-ttu-id="ad517-126">Während der Zwischenzeit können Sie [Ihre benutzerdefinierte app in eine Teams-Umgebung hochladen](/microsoftteams/upload-custom-apps#validate) , um Sie zu testen und zu validieren.</span><span class="sxs-lookup"><span data-stu-id="ad517-126">During interim, you can [Upload your custom app to a Teams environment](/microsoftteams/upload-custom-apps#validate) for testing and validation.</span></span>

3. <span data-ttu-id="ad517-127">Navigieren Sie zu **Teams**  -->  -**Setup Richtlinien**für apps  -->  **Global (organisationsweit Standard)**</span><span class="sxs-lookup"><span data-stu-id="ad517-127">Navigate to **Teams apps** --> **Setup Policies** --> **Global(Org-wide default)**</span></span>  

![Aktivieren der querladen-Ansicht](~/assets/images/prepare-test-tenant/turn-on-sideload.png)

4. <span data-ttu-id="ad517-129">Schalten Sie **benutzerdefinierte apps** in die Position **on** hoch.</span><span class="sxs-lookup"><span data-stu-id="ad517-129">Toggle **upload custom apps** to the **on** position.</span></span>

<span data-ttu-id="ad517-130">Das ist alles.</span><span class="sxs-lookup"><span data-stu-id="ad517-130">That's it!</span></span> <span data-ttu-id="ad517-131">Der Testmandant lässt jetzt benutzerdefinierte App-Sideloading.</span><span class="sxs-lookup"><span data-stu-id="ad517-131">Your test tenant will now allow custom app sideloading.</span></span>

> [!Note] 
> <span data-ttu-id="ad517-132">Es kann bis zu 24 Stunden dauern, bis Sideloading aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="ad517-132">It can take up to 24 hours before sideloading is enabled.</span></span> <span data-ttu-id="ad517-133">Während der Zwischenzeit können Sie \*\*Upload for \<your tenant> \*\* verwenden, um Ihre APP zu testen.</span><span class="sxs-lookup"><span data-stu-id="ad517-133">During interim, you can use **upload for \<your tenant>** to test your app.</span></span>

![Updload-App-Ansicht](~/assets/images/prepare-test-tenant/upload-for-contoso.png)

<span data-ttu-id="ad517-135">Umfassende Informationen zur Interaktion dieser Einstellungen *finden Sie unter* [Verwalten benutzerdefinierter App-Richtlinien und-Einstellungen in Microsoft Teams](https://docs.microsoft.com/microsoftteams/teams-custom-app-policies-and-settings) und [Verwalten von App-Setup Richtlinien in Microsoft Teams](https://docs.microsoft.com/microsoftteams/teams-app-setup-policies).</span><span class="sxs-lookup"><span data-stu-id="ad517-135">For complete information on how these settings interact, *See*, [Manage custom app policies and settings in Microsoft Teams](https://docs.microsoft.com/microsoftteams/teams-custom-app-policies-and-settings) and [Manage app setup policies in Microsoft Teams](https://docs.microsoft.com/microsoftteams/teams-app-setup-policies).</span></span>
