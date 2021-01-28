---
title: Vorbereiten des Microsoft 365-Mandanten
description: Erste Schritte mit Teams in Microsoft 365
ms.topic: how-to
keywords: Konfigurieren des Hochladens von Microsoft 365-Mandantenteams
ms.openlocfilehash: bfeb1a5d39b8a6ad8d1dd4d631f984ecec4e26f1
ms.sourcegitcommit: 976e870cc925f61b76c3830ec04ba6e4bdfde32f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/27/2021
ms.locfileid: "50014453"
---
# <a name="prepare-your-microsoft-365-tenant"></a><span data-ttu-id="66bfc-104">Vorbereiten des Microsoft 365-Mandanten</span><span class="sxs-lookup"><span data-stu-id="66bfc-104">Prepare your Microsoft 365 tenant</span></span>

<span data-ttu-id="66bfc-105">Wenn Sie ein Microsoft 365-Abonnent sind, können Sie Apps für Microsoft Teams mit einem der folgenden Pläne [entwickeln:](https://products.office.com/business/compare-more-office-365-for-business-plans)</span><span class="sxs-lookup"><span data-stu-id="66bfc-105">If you are a Microsoft 365 subscriber, you can develop apps for Microsoft Teams with one of the following [plans](https://products.office.com/business/compare-more-office-365-for-business-plans):</span></span>

* <span data-ttu-id="66bfc-106">Standard</span><span class="sxs-lookup"><span data-stu-id="66bfc-106">Basic</span></span>
* <span data-ttu-id="66bfc-107">Standard</span><span class="sxs-lookup"><span data-stu-id="66bfc-107">Standard</span></span>
* <span data-ttu-id="66bfc-108">Enterprise E1, E3 und E5</span><span class="sxs-lookup"><span data-stu-id="66bfc-108">Enterprise E1, E3, and E5</span></span>
* <span data-ttu-id="66bfc-109">Developer</span><span class="sxs-lookup"><span data-stu-id="66bfc-109">Developer</span></span>
* <span data-ttu-id="66bfc-110">Education, Education Plus und Education E5</span><span class="sxs-lookup"><span data-stu-id="66bfc-110">Education, Education Plus, and Education E5</span></span>

<span data-ttu-id="66bfc-111">Microsoft Teams steht auch Kunden zur Verfügung, die E4 vor der Dehierung [abonniert haben.](https://support.office.com//article/important-information-for-office-365-enterprise-e4-customers-f9572348-43a2-43fa-a3d8-3b6c9c042147)</span><span class="sxs-lookup"><span data-stu-id="66bfc-111">Microsoft Teams will also be available to customers who subscribed to E4 prior to its [retirement](https://support.office.com//article/important-information-for-office-365-enterprise-e4-customers-f9572348-43a2-43fa-a3d8-3b6c9c042147).</span></span>

## <a name="just-need-a-development-environment"></a><span data-ttu-id="66bfc-112">Benötigen Sie nur eine Entwicklungsumgebung?</span><span class="sxs-lookup"><span data-stu-id="66bfc-112">Just need a development environment?</span></span>

<span data-ttu-id="66bfc-113">Wenn Sie derzeit kein Microsoft 365-Konto haben, können Sie sich für ein Abonnement des [Microsoft 365-Entwicklerprogramms](https://developer.microsoft.com/microsoft-365/dev-program) registrieren.</span><span class="sxs-lookup"><span data-stu-id="66bfc-113">If you don't currently have a Microsoft 365 account, you can sign up for a [Microsoft 365 Developer Program](https://developer.microsoft.com/microsoft-365/dev-program) subscription.</span></span> <span data-ttu-id="66bfc-114">Es ist *90* Tage lang kostenlos und wird kontinuierlich verlängert, solange Sie es für Entwicklungsaktivitäten verwenden.</span><span class="sxs-lookup"><span data-stu-id="66bfc-114">It's *free* for 90 days and will continually renew as long as you're using it for development activity.</span></span> <span data-ttu-id="66bfc-115">Wenn Sie über ein Visual Studio  *Enterprise-* oder Professional-Abonnement verfügen, enthalten beide Programme ein kostenloses Microsoft 365-Entwicklerabonnement, das für die Lebensdauer Ihres Visual Studio ist. [](https://aka.ms/MyVisualStudioBenefits)</span><span class="sxs-lookup"><span data-stu-id="66bfc-115">If you have a Visual Studio *Enterprise* or *Professional* subscription, both programs include a free Microsoft 365 [developer subscription](https://aka.ms/MyVisualStudioBenefits), active for the life of your Visual Studio subscription.</span></span> <span data-ttu-id="66bfc-116">*Siehe* ["Einrichten eines Microsoft 365-Entwicklerabonnements".](https://docs.microsoft.com/office/developer-program/office-365-developer-program-get-started)</span><span class="sxs-lookup"><span data-stu-id="66bfc-116">*See* [Set up a Microsoft 365 developer subscription](https://docs.microsoft.com/office/developer-program/office-365-developer-program-get-started).</span></span>

## <a name="enable-microsoft-teams-for-your-organization"></a><span data-ttu-id="66bfc-117">Aktivieren von Microsoft Teams für Ihre Organisation</span><span class="sxs-lookup"><span data-stu-id="66bfc-117">Enable Microsoft Teams for your organization</span></span> 

<span data-ttu-id="66bfc-118">Wenn Microsoft Teams für Ihre Organisation nicht aktiviert wurde, müssen Sie dies zuerst tun.</span><span class="sxs-lookup"><span data-stu-id="66bfc-118">If Microsoft Teams has not been enabled for your organization, you'll need to do that first.</span></span> <span data-ttu-id="66bfc-119">Sehen Sie sich unsere detaillierten Anleitungen zum Aktivieren [von Teams für Ihre Organisation an.](/microsoftteams/enable-features-office-365)</span><span class="sxs-lookup"><span data-stu-id="66bfc-119">Take a look at our detailed guidance for [enabling Teams for your organization](/microsoftteams/enable-features-office-365).</span></span>

## <a name="enable-custom-teams-apps-and-turn-on-custom-app-uploading"></a><span data-ttu-id="66bfc-120">Aktivieren benutzerdefinierter Teams-Apps und Aktivieren des Hochladens benutzerdefinierter Apps</span><span class="sxs-lookup"><span data-stu-id="66bfc-120">Enable custom Teams apps and turn on custom app uploading</span></span>

<span data-ttu-id="66bfc-121">Aktivieren Sie das Sideloading von benutzerdefinierten Apps für Ihren Entwickler mandanten wie folgt:</span><span class="sxs-lookup"><span data-stu-id="66bfc-121">Turn on custom app sideloading for your developer tenant as follows:</span></span>

1. <span data-ttu-id="66bfc-122">Melden Sie [sich mit Ihren Administratoranmeldeinformationen beim Microsoft 365](https://admin.microsoft.com/Adminportal/Home?source=applauncher#/homepage#/) Admin Center an.</span><span class="sxs-lookup"><span data-stu-id="66bfc-122">Login to [Microsoft 365 admin center](https://admin.microsoft.com/Adminportal/Home?source=applauncher#/homepage#/) with your admin credential.</span></span> 

2. <span data-ttu-id="66bfc-123">Wählen **Sie "Alle Teams**  -->  **anzeigen" aus.**</span><span class="sxs-lookup"><span data-stu-id="66bfc-123">Select **Show All** --> **Teams**.</span></span> 

![Abbildung des Admin Center-Menüs](~/assets/images/prepare-test-tenant/admin-center.png)

> [!Note] 
> <span data-ttu-id="66bfc-125">Es kann bis zu 24 Stunden dauern, bis die Option "Teams" angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="66bfc-125">It can take up to 24 hours for the "Teams" option to appear.</span></span> <span data-ttu-id="66bfc-126">In der Zwischenzeit können Sie Ihre benutzerdefinierte App [zu Test-](/microsoftteams/upload-custom-apps#validate) und Validierungszwecken in eine Teams-Umgebung hochladen.</span><span class="sxs-lookup"><span data-stu-id="66bfc-126">During interim, you can [Upload your custom app to a Teams environment](/microsoftteams/upload-custom-apps#validate) for testing and validation.</span></span>

3. <span data-ttu-id="66bfc-127">Navigieren Sie zu **"Setuprichtlinien**  -->  **für**  -->  **Teams-Apps" global (organisationsweite Standardeinstellung)**</span><span class="sxs-lookup"><span data-stu-id="66bfc-127">Navigate to **Teams apps** --> **Setup Policies** --> **Global(Org-wide default)**</span></span>  

![Aktivieren der Querladenansicht](~/assets/images/prepare-test-tenant/turn-on-sideload.png)

4. <span data-ttu-id="66bfc-129">Schalten Sie **benutzerdefinierte Apps in** die "On"-Position hoch. </span><span class="sxs-lookup"><span data-stu-id="66bfc-129">Toggle **upload custom apps** to the **on** position.</span></span>

<span data-ttu-id="66bfc-130">Das ist alles.</span><span class="sxs-lookup"><span data-stu-id="66bfc-130">That's it!</span></span> <span data-ttu-id="66bfc-131">Ihr Test mandant lässt jetzt das Querladen benutzerdefinierter Apps zu.</span><span class="sxs-lookup"><span data-stu-id="66bfc-131">Your test tenant will now allow custom app sideloading.</span></span>

> [!Note] 
> <span data-ttu-id="66bfc-132">Es kann bis zu 24 Stunden dauern, bis das Querladen aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="66bfc-132">It can take up to 24 hours before sideloading is enabled.</span></span> <span data-ttu-id="66bfc-133">In der Zwischenzeit können Sie den **Upload \<your tenant> für verwenden,** um Ihre App zu testen.</span><span class="sxs-lookup"><span data-stu-id="66bfc-133">During interim, you can use **upload for \<your tenant>** to test your app.</span></span>

![Updload-App-Ansicht](~/assets/images/prepare-test-tenant/upload-for-contoso.png)

<span data-ttu-id="66bfc-135">Vollständige Informationen zur Interaktion dieser Einstellungen finden Sie unter *,* Verwalten von benutzerdefinierten Richtlinien und Einstellungen für Apps in [Microsoft Teams](https://docs.microsoft.com/microsoftteams/teams-custom-app-policies-and-settings) und Verwalten von Setuprichtlinien für Apps in [Microsoft Teams.](https://docs.microsoft.com/microsoftteams/teams-app-setup-policies)</span><span class="sxs-lookup"><span data-stu-id="66bfc-135">For complete information on how these settings interact, *See*, [Manage custom app policies and settings in Microsoft Teams](https://docs.microsoft.com/microsoftteams/teams-custom-app-policies-and-settings) and [Manage app setup policies in Microsoft Teams](https://docs.microsoft.com/microsoftteams/teams-app-setup-policies).</span></span>
