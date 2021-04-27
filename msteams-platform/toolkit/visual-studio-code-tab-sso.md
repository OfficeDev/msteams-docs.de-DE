---
title: Einmalige Anmeldung mit Teams Toolkit und Visual Studio Code für Registerkarten
description: Erstellen einer Registerkarte, die einmaliges Anmelden und Microsoft Graph-Aufrufe direkt in Visual Studio Code mit dem Microsoft Teams Toolkit unterstützt
keywords: Registerkarten des visual studio code toolkits sso graph authentication Azure identity platform
localization_priority: Normal
ms.topic: how-to
ms.author: lajanuar
ms.openlocfilehash: daf9a1b0bb64fee9584d0f58d749cf2b1ccaa4ef
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2021
ms.locfileid: "52018425"
---
# <a name="single-sign-on-authentication-with-teams-toolkit-and-visual-studio-code-for-tabs"></a><span data-ttu-id="57cb7-104">Einmalige Anmeldung mit Teams Toolkit und Visual Studio Code für Registerkarten</span><span class="sxs-lookup"><span data-stu-id="57cb7-104">Single sign-on authentication with Teams Toolkit and Visual Studio Code for tabs</span></span>

<span data-ttu-id="57cb7-105">Mit dem Microsoft Teams Toolkit können Sie die einmalige Anmeldung (Single Sign-On, SSO)-Authentifizierung für Registerkarten-Apps direkt innerhalb Visual Studio erstellen.</span><span class="sxs-lookup"><span data-stu-id="57cb7-105">The Microsoft Teams Toolkit enables you to create single sign-on (SSO) authentication  for tab apps directly within Visual Studio Code.</span></span> <span data-ttu-id="57cb7-106">Das Toolkit führt Sie durch den Prozess und bietet alles, was Sie benötigen, einschließlich der Bereitstellung Ihrer Microsoft Identity Platform-Registrierung im Azure-Portal.</span><span class="sxs-lookup"><span data-stu-id="57cb7-106">The toolkit guides you through the process and provides everything you need including provisioning your Microsoft identity platform registration in the Azure portal.</span></span>

## <a name="get-started--create-a-project"></a><span data-ttu-id="57cb7-107">Erste Schritte – Erstellen eines Projekts</span><span class="sxs-lookup"><span data-stu-id="57cb7-107">Get started — create a project</span></span>

1. <span data-ttu-id="57cb7-108">Erstellen Sie ein neues Projekt im Toolkit.</span><span class="sxs-lookup"><span data-stu-id="57cb7-108">Create a new project in the toolkit.</span></span>
1. <span data-ttu-id="57cb7-109">Wählen Sie tab als Den Typ der Erweiterung aus, den Sie erstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="57cb7-109">Select tab as the type of extension you'd like to create.</span></span>
1. <span data-ttu-id="57cb7-110">Wählen Sie die Option aus, um SSO zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="57cb7-110">Select the option to support SSO.</span></span>

> [!TIP]
> <span data-ttu-id="57cb7-111">Nach der Installation sollte das Teams Toolkit in der Visual Studio Code-Aktivitätsleiste angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="57cb7-111">After installation, you should see the Teams Toolkit in the Visual Studio Code activity bar.</span></span> <span data-ttu-id="57cb7-112">Wenn nicht, klicken Sie mit der rechten Maustaste in der Aktivitätsleiste, und wählen **Sie Microsoft Teams aus,** um das Toolkit für den einfachen Zugriff anheften.</span><span class="sxs-lookup"><span data-stu-id="57cb7-112">If not, right-click within the activity bar and select **Microsoft Teams** to pin the toolkit for easy access.</span></span>

## <a name="configure-your-project"></a><span data-ttu-id="57cb7-113">Konfigurieren Ihres Projekts</span><span class="sxs-lookup"><span data-stu-id="57cb7-113">Configure your project</span></span>

1. <span data-ttu-id="57cb7-114">Um SSO in Teams zu aktivieren, muss Ihre App über eine Azure-App-Registrierungsressource verfügen.</span><span class="sxs-lookup"><span data-stu-id="57cb7-114">To enable SSO within Teams, your app must have an Azure app registration resource.</span></span> <span data-ttu-id="57cb7-115">Das Teams Toolkit stellt die App-Registrierung in Ihrem Namen zur Bereitstellung.</span><span class="sxs-lookup"><span data-stu-id="57cb7-115">The Teams Toolkit will provision the app registration on your behalf.</span></span>
1. <span data-ttu-id="57cb7-116">Geben Sie die URL ein, in der Ihre App gehostet wird, und wählen Sie als **Nächstes aus.**</span><span class="sxs-lookup"><span data-stu-id="57cb7-116">Enter the URL where your app will be hosted and select **next**.</span></span> <span data-ttu-id="57cb7-117">Ihre App-Registrierung wird mithilfe der bereitgestellten URL konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="57cb7-117">Your app registration will be configured using the provided URL.</span></span>
1. <span data-ttu-id="57cb7-118">Die Konfigurationsdetails der App-Registrierung werden in den Dateien im Quellcode Ihres `.env` Projekts gespeichert.</span><span class="sxs-lookup"><span data-stu-id="57cb7-118">The app registration's configuration details will be stored in the `.env` files in your project's source code.</span></span>

<span data-ttu-id="57cb7-119">Wenn Sie mehr darüber erfahren möchten, wie Ihre Azure-App-Registrierung bereitgestellt wird, lesen Sie unsere Unterstützung für einmaliges Anmelden [(Single Sign-On, SSO)](../tabs/how-to/authentication/auth-aad-sso.md) für die Registerkartendokumentation. </span><span class="sxs-lookup"><span data-stu-id="57cb7-119">If you would like to learn more about how your Azure app registration will be provisioned, please _see_  our [single sign-on (SSO) support for tabs](../tabs/how-to/authentication/auth-aad-sso.md) documentation.</span></span>

> [!TIP]
> <span data-ttu-id="57cb7-120">Sie müssen zu **Azure App-Registrierungen** wechseln und Ihren *API-URI aktualisieren* und *URLs* umleiten, wenn Sie diese URL ändern.</span><span class="sxs-lookup"><span data-stu-id="57cb7-120">You will need to go to **Azure App Registrations** and update your *API URI* and *redirect URLs* whenever you change this URL.</span></span>

## <a name="run-your-project"></a><span data-ttu-id="57cb7-121">Ausführen des Projekts</span><span class="sxs-lookup"><span data-stu-id="57cb7-121">Run your project</span></span>

1. <span data-ttu-id="57cb7-122">Wählen **Sie npm install** aus dem Ordner `api-server` aus.</span><span class="sxs-lookup"><span data-stu-id="57cb7-122">Select **npm install** from the `api-server` folder.</span></span> <span data-ttu-id="57cb7-123">Starten Sie **dann npm.**</span><span class="sxs-lookup"><span data-stu-id="57cb7-123">Then **npm start**.</span></span>
1. <span data-ttu-id="57cb7-124">Wählen **Sie npm install** aus dem Ordner `.src` aus.</span><span class="sxs-lookup"><span data-stu-id="57cb7-124">Select **npm install** from the `.src` folder.</span></span> <span data-ttu-id="57cb7-125">Starten Sie **dann npm.**</span><span class="sxs-lookup"><span data-stu-id="57cb7-125">Then **npm start**.</span></span>
1. <span data-ttu-id="57cb7-126">Wenn Sie einen Tunneldienst wie [ngrok](https://ngrok.com/)verwenden, führen Sie ihn aus, und stellen Sie sicher, dass die URL mit dem entspricht, was Sie im Assistenten zum Erstellen des Projekts eingegeben haben.</span><span class="sxs-lookup"><span data-stu-id="57cb7-126">If you are using a tunneling service like [ngrok](https://ngrok.com/), run it and make sure the URL matches with what you entered in the project creation wizard.</span></span> <span data-ttu-id="57cb7-127">Andern falls nicht, müssen Sie Ihren _API-URI_ aktualisieren und _die URL_ in der app-Registrierung umleiten, die in Azure erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="57cb7-127">If it doesn't, you will need to update your _API URI_ and _redirect URL_ in the app registration that was created in Azure.</span></span>
1. <span data-ttu-id="57cb7-128">Navigieren Sie zur Aktivitätsleiste auf der linken Seite des Visual Studio Codefensters.</span><span class="sxs-lookup"><span data-stu-id="57cb7-128">Navigate to the activity bar on the left side of the Visual Studio Code window.</span></span>
1. <span data-ttu-id="57cb7-129">Wählen Sie das **Symbol Ausführen** aus, um die Ansicht Ausführen **und Debuggen anzeigen.**</span><span class="sxs-lookup"><span data-stu-id="57cb7-129">Select the **Run** icon to display the **Run and Debug** view.</span></span>
1. <span data-ttu-id="57cb7-130">Sie können auch die Tastenkombination **STRG+Umschalt+D verwenden.**</span><span class="sxs-lookup"><span data-stu-id="57cb7-130">You can also use the keyboard shortcut **Ctrl+Shift+D**.</span></span>

> [!TIP]
> <span data-ttu-id="57cb7-131">Möglicherweise wird der Dialog zur App-Installation im Browser nicht angezeigt, wenn Popupfenster für Ihren Browser deaktiviert sind.</span><span class="sxs-lookup"><span data-stu-id="57cb7-131">You may not see the app install dialogue in the browser if pop-up windows are disabled for your browser.</span></span> <span data-ttu-id="57cb7-132">Aktivieren Sie in diesem Fall Popupfenster, und aktualisieren Sie die Seite.</span><span class="sxs-lookup"><span data-stu-id="57cb7-132">If this happens, enable pop-up windows and refresh the page.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="57cb7-133">Weitere Informationen: Erstellen von Apps mit dem Microsoft Teams Toolkit und Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="57cb7-133">Learn more: Build apps with the Microsoft Teams Toolkit and Visual Studio Code</span></span>](visual-studio-code-overview.md)
