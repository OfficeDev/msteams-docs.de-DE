---
title: Vorbereiten des Microsoft 365-Mandanten
description: Erste Schritte mit Teams in Microsoft 365
ms.topic: how-to
keywords: Konfigurieren des Hochladens von Microsoft 365-Mandantenteams
ms.openlocfilehash: aa7f994744f8b1c62aa32122a5006cfa0f22d391
ms.sourcegitcommit: 5b3ba227c2e5e6f7a2c629961993f168da6a504d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2021
ms.locfileid: "51634754"
---
# <a name="prepare-your-microsoft-365-tenant"></a><span data-ttu-id="523ae-104">Vorbereiten des Microsoft 365-Mandanten</span><span class="sxs-lookup"><span data-stu-id="523ae-104">Prepare your Microsoft 365 tenant</span></span>

<span data-ttu-id="523ae-105">Microsoft 365-Abonnenten können Apps für Microsoft Teams mit einem der folgenden Pläne entwickeln:</span><span class="sxs-lookup"><span data-stu-id="523ae-105">Microsoft 365 subscribers can develop apps for Microsoft Teams with one of the following plans:</span></span>

* <span data-ttu-id="523ae-106">Standard</span><span class="sxs-lookup"><span data-stu-id="523ae-106">Basic</span></span>
* <span data-ttu-id="523ae-107">Standard</span><span class="sxs-lookup"><span data-stu-id="523ae-107">Standard</span></span>
* <span data-ttu-id="523ae-108">Enterprise E1, E3 und E5</span><span class="sxs-lookup"><span data-stu-id="523ae-108">Enterprise E1, E3, and E5</span></span>
* <span data-ttu-id="523ae-109">Developer</span><span class="sxs-lookup"><span data-stu-id="523ae-109">Developer</span></span>
* <span data-ttu-id="523ae-110">Education, Education Plus, and Education E5</span><span class="sxs-lookup"><span data-stu-id="523ae-110">Education, Education Plus, and Education E5</span></span>

> [!NOTE]
> <span data-ttu-id="523ae-111">Weitere Informationen zu Microsoft 365-Abonnements finden Sie unter [Pläne](https://products.office.com/business/compare-more-office-365-for-business-plans).</span><span class="sxs-lookup"><span data-stu-id="523ae-111">For more information on Microsoft 365 subscriptions, see [plans](https://products.office.com/business/compare-more-office-365-for-business-plans).</span></span>
> 
> <span data-ttu-id="523ae-112">Microsoft Teams steht auch Kunden zur Verfügung, die E4 vor der Rente [abonniert haben.](https://support.office.com//article/important-information-for-office-365-enterprise-e4-customers-f9572348-43a2-43fa-a3d8-3b6c9c042147)</span><span class="sxs-lookup"><span data-stu-id="523ae-112">Microsoft Teams is also available to customers who subscribed to E4 prior to its [retirement](https://support.office.com//article/important-information-for-office-365-enterprise-e4-customers-f9572348-43a2-43fa-a3d8-3b6c9c042147).</span></span>

## <a name="create-your-development-environment"></a><span data-ttu-id="523ae-113">Erstellen Ihrer Entwicklungsumgebung</span><span class="sxs-lookup"><span data-stu-id="523ae-113">Create your development environment</span></span>

<span data-ttu-id="523ae-114">Wenn Sie kein Microsoft 365-Konto haben, müssen Sie sich für ein [Microsoft 365 Developer Program-Abonnement](https://developer.microsoft.com/microsoft-365/dev-program) registrieren.</span><span class="sxs-lookup"><span data-stu-id="523ae-114">If you do not have a Microsoft 365 account, you must sign up for a [Microsoft 365 Developer Program](https://developer.microsoft.com/microsoft-365/dev-program) subscription.</span></span> <span data-ttu-id="523ae-115">Das Abonnement ist für 90 Tage kostenlos und wird weiterhin verlängert, solange Sie es für Entwicklungsaktivitäten verwenden.</span><span class="sxs-lookup"><span data-stu-id="523ae-115">The subscription is free for 90 days and continues to renew as long as you are using it for development activity.</span></span> <span data-ttu-id="523ae-116">Wenn Sie über ein Visual Studio Enterprise- oder Professional-Abonnement verfügen, enthalten beide Programme ein kostenloses Microsoft [365-Entwicklerabonnement.](https://aka.ms/MyVisualStudioBenefits)</span><span class="sxs-lookup"><span data-stu-id="523ae-116">If you have a Visual Studio Enterprise or Professional subscription, both programs include a free Microsoft 365 [developer subscription](https://aka.ms/MyVisualStudioBenefits).</span></span> <span data-ttu-id="523ae-117">Sie ist so lange aktiv, wie Visual Studio Abonnement aktiv ist.</span><span class="sxs-lookup"><span data-stu-id="523ae-117">It is active for as long as your Visual Studio subscription is active.</span></span> <span data-ttu-id="523ae-118">Weitere Informationen finden Sie unter [Einrichten eines Microsoft 365-Entwicklerabonnements](https://docs.microsoft.com/office/developer-program/office-365-developer-program-get-started).</span><span class="sxs-lookup"><span data-stu-id="523ae-118">For more inforamtion, see [Set up a Microsoft 365 developer subscription](https://docs.microsoft.com/office/developer-program/office-365-developer-program-get-started).</span></span>

## <a name="enable-microsoft-teams-for-your-organization"></a><span data-ttu-id="523ae-119">Aktivieren von Microsoft Teams für Ihre Organisation</span><span class="sxs-lookup"><span data-stu-id="523ae-119">Enable Microsoft Teams for your organization</span></span>

<span data-ttu-id="523ae-120">Aktivieren Sie Microsoft Teams für Ihre Organisation, und sehen Sie sich unsere detaillierten Anleitungen zum Aktivieren [von Teams für Ihre Organisation an.](/microsoftteams/enable-features-office-365)</span><span class="sxs-lookup"><span data-stu-id="523ae-120">Enable Microsoft Teams for your organization and take a look at our detailed guidance for [enabling Teams for your organization](/microsoftteams/enable-features-office-365).</span></span>

## <a name="enable-custom-teams-apps-and-turn-on-custom-app-uploading"></a><span data-ttu-id="523ae-121">Aktivieren benutzerdefinierter Teams-Apps und Aktivieren des Hochladens benutzerdefinierter Apps</span><span class="sxs-lookup"><span data-stu-id="523ae-121">Enable custom Teams apps and turn on custom app uploading</span></span>

<span data-ttu-id="523ae-122">**So aktivieren Sie das Hochladen oder Querladen der benutzerdefinierten App für Ihren Entwickler-Mandanten**</span><span class="sxs-lookup"><span data-stu-id="523ae-122">**To turn on the custom app uploading or sideloading for your developer tenant**</span></span>

1. <span data-ttu-id="523ae-123">Melden Sie sich [beim Microsoft 365 Admin Center](https://admin.microsoft.com/Adminportal/Home?source=applauncher#/homepage#/) mit Ihren Administratoranmeldeinformationen an.</span><span class="sxs-lookup"><span data-stu-id="523ae-123">Sign in to [Microsoft 365 admin center](https://admin.microsoft.com/Adminportal/Home?source=applauncher#/homepage#/) with your admin credentials.</span></span>

2. <span data-ttu-id="523ae-124">Wählen **Sie Alle Teams** anzeigen  >  **aus.**</span><span class="sxs-lookup"><span data-stu-id="523ae-124">Select **Show All** > **Teams**.</span></span>

    ![Abbildung des Admin Center-Menüs](~/assets/images/prepare-test-tenant/admin-center.png)

    > [!Note]
    > <span data-ttu-id="523ae-126">Es kann bis zu 24 Stunden dauern, bis die **Option Teams** angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="523ae-126">It can take up to 24 hours for the **Teams** option to appear.</span></span> <span data-ttu-id="523ae-127">Sie können [Ihre benutzerdefinierte App in dieser](/microsoftteams/upload-custom-apps#validate) Zeit zu Test- und Validierungszwecken in eine Teams-Umgebung hochladen.</span><span class="sxs-lookup"><span data-stu-id="523ae-127">You can [upload your custom app to a Teams environment](/microsoftteams/upload-custom-apps#validate) for testing and validation in that time.</span></span>

3. <span data-ttu-id="523ae-128">Navigieren Sie zu **Teams apps**  >  **Setup Policies**  >  **Global**.</span><span class="sxs-lookup"><span data-stu-id="523ae-128">Navigate to **Teams apps** > **Setup Policies** > **Global**.</span></span>

   ![Aktivieren der Querladenansicht](~/assets/images/prepare-test-tenant/turn-on-sideload.png)

4. <span data-ttu-id="523ae-130">**Umschalten Sie benutzerdefinierte Apps hochladen** an die **Ein-Position.**</span><span class="sxs-lookup"><span data-stu-id="523ae-130">Toggle **upload custom apps** to the **on** position.</span></span>

5. <span data-ttu-id="523ae-131">Wählen Sie **Speichern** aus.</span><span class="sxs-lookup"><span data-stu-id="523ae-131">Select **Save**.</span></span>
   <span data-ttu-id="523ae-132">Ihr Test-Mandant kann das Querladen benutzerdefinierter Apps zulassen.</span><span class="sxs-lookup"><span data-stu-id="523ae-132">Your test tenant can permit custom app sideloading.</span></span>

    > [!Note]
    > <span data-ttu-id="523ae-133">Es kann bis zu 24 Stunden dauern, bis das Querladen aktiv ist.</span><span class="sxs-lookup"><span data-stu-id="523ae-133">It can take up to 24 hours for the sideloading to be active.</span></span> <span data-ttu-id="523ae-134">Zwischenzeit können Sie upload **\<your tenant> für verwenden,** um Ihre App zu testen.</span><span class="sxs-lookup"><span data-stu-id="523ae-134">During interim, you can use **upload for \<your tenant>** to test your app.</span></span>

    ![Updload-App-Ansicht](~/assets/images/prepare-test-tenant/upload-for-contoso.png)

<span data-ttu-id="523ae-136">Vollständige Informationen zur Interaktion dieser Einstellungen finden Sie unter [Manage custom app policies and settings in Microsoft Teams](https://docs.microsoft.com/microsoftteams/teams-custom-app-policies-and-settings) und Manage app setup policies in Microsoft [Teams](https://docs.microsoft.com/microsoftteams/teams-app-setup-policies).</span><span class="sxs-lookup"><span data-stu-id="523ae-136">For complete information on how these settings interact, see [Manage custom app policies and settings in Microsoft Teams](https://docs.microsoft.com/microsoftteams/teams-custom-app-policies-and-settings) and [Manage app setup policies in Microsoft Teams](https://docs.microsoft.com/microsoftteams/teams-app-setup-policies).</span></span>

## <a name="next-step"></a><span data-ttu-id="523ae-137">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="523ae-137">Next step</span></span>

> [!div class="nextstepaction"] 
> [<span data-ttu-id="523ae-138">Auswählen einer Testeinrichtung</span><span class="sxs-lookup"><span data-stu-id="523ae-138">Choose a test setup</span></span>](~/concepts/build-and-test/debug.md)
> 


