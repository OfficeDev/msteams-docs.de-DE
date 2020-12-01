---
title: Authentifizierung mit einmaligem Anmelden mit Microsoft Teams Toolkit und Visual Studio Code für Registerkarten
description: Erstellen Sie eine Registerkarte, die Single-Sign-on-und Microsoft Graph-Aufrufe direkt in Visual Studio Code mit dem Microsoft Teams-Toolkit unterstützt.
keywords: Teams Visual Studio Code Toolkit-Registerkarten SSO-Graph-Authentifizierung Azure Identity Platform
ms.topic: how-to
ms.author: lajanuar
ms.openlocfilehash: fe734143975688cd35c510cd68cd0779a2200a18
ms.sourcegitcommit: 7e47bf158249050c36d97509eea00e77089a54e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/30/2020
ms.locfileid: "49477736"
---
# <a name="single-sign-on-authentication-with-teams-toolkit-and-visual-studio-code-for-tabs"></a><span data-ttu-id="81133-104">Authentifizierung mit einmaligem Anmelden mit Microsoft Teams Toolkit und Visual Studio Code für Registerkarten</span><span class="sxs-lookup"><span data-stu-id="81133-104">Single sign-on authentication with Teams Toolkit and Visual Studio Code for tabs</span></span>

<span data-ttu-id="81133-105">Mit dem Microsoft Teams-Toolkit können Sie die SSO-Authentifizierung (Single Sign-on, einmaliges Anmelden) für Registerkarten-apps direkt in Visual Studio Code erstellen.</span><span class="sxs-lookup"><span data-stu-id="81133-105">The Microsoft Teams Toolkit enables you to create single sign-on (SSO) authentication  for tab apps directly within Visual Studio Code.</span></span> <span data-ttu-id="81133-106">Das Toolkit führt Sie durch den Prozess und bietet alles, was Sie benötigen, einschließlich der Bereitstellung Ihrer Microsoft Identity Platform-Registrierung im Azure-Portal.</span><span class="sxs-lookup"><span data-stu-id="81133-106">The toolkit guides you through the process and provides everything you need including provisioning your Microsoft identity platform registration in the Azure portal.</span></span>

## <a name="get-started--create-a-project"></a><span data-ttu-id="81133-107">Erste Schritte – Erstellen eines Projekts</span><span class="sxs-lookup"><span data-stu-id="81133-107">Get started — create a project</span></span>

1. <span data-ttu-id="81133-108">Erstellen Sie ein neues Projekt im Toolkit.</span><span class="sxs-lookup"><span data-stu-id="81133-108">Create a new project in the toolkit.</span></span>
1. <span data-ttu-id="81133-109">Wählen Sie Tab als den Typ der Erweiterung aus, die Sie erstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="81133-109">Select tab as the type of extension you'd like to create.</span></span>
1. <span data-ttu-id="81133-110">Wählen Sie die Option zur Unterstützung von SSO aus.</span><span class="sxs-lookup"><span data-stu-id="81133-110">Select the option to support SSO.</span></span>

> [!TIP]
> <span data-ttu-id="81133-111">Nach der Installation sollte das Teams-Toolkit in der Leiste Visual Studio Code-Aktivität angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="81133-111">After installation, you should see the Teams Toolkit in the Visual Studio Code activity bar.</span></span> <span data-ttu-id="81133-112">Wenn dies nicht der Fall ist, klicken Sie mit der rechten Maustaste in die Aktivitäts Leiste, und wählen Sie **Microsoft Teams** aus, um das Toolkit für einfachen Zugriff zu fixieren</span><span class="sxs-lookup"><span data-stu-id="81133-112">If not, right-click within the activity bar and select **Microsoft Teams** to pin the toolkit for easy access.</span></span>

## <a name="configure-your-project"></a><span data-ttu-id="81133-113">Konfigurieren des Projekts</span><span class="sxs-lookup"><span data-stu-id="81133-113">Configure your project</span></span>

1. <span data-ttu-id="81133-114">Um SSO in Microsoft Teams zu aktivieren, muss Ihre APP über eine Azure-App-Registrierungs Ressource verfügen.</span><span class="sxs-lookup"><span data-stu-id="81133-114">To enable SSO within Teams, your app must have an Azure app registration resource.</span></span> <span data-ttu-id="81133-115">Das Teams-Toolkit stellt die APP-Registrierung in Ihrem Namen zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="81133-115">The Teams Toolkit will provision the app registration on your behalf.</span></span>
1. <span data-ttu-id="81133-116">Geben Sie die URL ein, unter der Ihre APP gehostet wird, und wählen Sie **weiter** aus.</span><span class="sxs-lookup"><span data-stu-id="81133-116">Enter the URL where your app will be hosted and select **next**.</span></span> <span data-ttu-id="81133-117">Ihre APP-Registrierung wird mithilfe der bereitgestellten URL konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="81133-117">Your app registration will be configured using the provided URL.</span></span>
1. <span data-ttu-id="81133-118">Die Konfigurationsdetails der APP-Registrierung werden in den `.env` Dateien des Quellcodes Ihres Projekts gespeichert.</span><span class="sxs-lookup"><span data-stu-id="81133-118">The app registration's configuration details will be stored in the `.env` files in your project's source code.</span></span>

<span data-ttu-id="81133-119">Wenn Sie mehr über die Einrichtung ihrer Azure-App-Registrierung erfahren möchten _, lesen Sie bitte unsere_ [Unterstützung für einmaliges Anmelden (Single Sign-on, SSO) für die Registerkarten](../tabs/how-to/authentication/auth-aad-sso.md) Dokumentation.</span><span class="sxs-lookup"><span data-stu-id="81133-119">If you would like to learn more about how your Azure app registration will be provisioned, please _see_  our [single sign-on (SSO) support for tabs](../tabs/how-to/authentication/auth-aad-sso.md) documentation.</span></span>

> [!TIP]
> <span data-ttu-id="81133-120">Sie müssen zu **Azure-App-Registrierungen** wechseln und den *API-URI* aktualisieren und *URLs umleiten* , wenn Sie diese URL ändern.</span><span class="sxs-lookup"><span data-stu-id="81133-120">You will need to go to **Azure App Registrations** and update your *API URI* and *redirect URLs* whenever you change this URL.</span></span>

## <a name="run-your-project"></a><span data-ttu-id="81133-121">Ausführen des Projekts</span><span class="sxs-lookup"><span data-stu-id="81133-121">Run your project</span></span>

1. <span data-ttu-id="81133-122">Wählen Sie **NPM-Installation** aus dem Ordner aus `api-server` .</span><span class="sxs-lookup"><span data-stu-id="81133-122">Select **npm install** from the `api-server` folder.</span></span> <span data-ttu-id="81133-123">Dann **Starten Sie NPM**.</span><span class="sxs-lookup"><span data-stu-id="81133-123">Then **npm start**.</span></span>
1. <span data-ttu-id="81133-124">Wählen Sie **NPM-Installation** aus dem Ordner aus `.src` .</span><span class="sxs-lookup"><span data-stu-id="81133-124">Select **npm install** from the `.src` folder.</span></span> <span data-ttu-id="81133-125">Dann **Starten Sie NPM**.</span><span class="sxs-lookup"><span data-stu-id="81133-125">Then **npm start**.</span></span>
1. <span data-ttu-id="81133-126">Wenn Sie einen Tunnel Dienst wie [ngrok](https://ngrok.com/)verwenden, führen Sie ihn aus, und stellen Sie sicher, dass die URL mit den Angaben übereinstimmt, die Sie im Assistenten zum Erstellen von Projekten eingegeben haben.</span><span class="sxs-lookup"><span data-stu-id="81133-126">If you are using a tunneling service like [ngrok](https://ngrok.com/), run it and make sure the URL matches with what you entered in the project creation wizard.</span></span> <span data-ttu-id="81133-127">Wenn dies nicht der Fall ist, müssen Sie den _API-URI_ und die _Umleitungs-URL_ in der APP-Registrierung aktualisieren, die in Azure erstellt wurde.</span><span class="sxs-lookup"><span data-stu-id="81133-127">If it doesn't, you will need to update your _API URI_ and _redirect URL_ in the app registration that was created in Azure.</span></span>
1. <span data-ttu-id="81133-128">Navigieren Sie auf der linken Seite des Visual Studio Code Fensters zur Aktivitäts Leiste.</span><span class="sxs-lookup"><span data-stu-id="81133-128">Navigate to the activity bar on the left side of the Visual Studio Code window.</span></span>
1. <span data-ttu-id="81133-129">Wählen Sie das Symbol **Ausführen** aus, um die Ansicht **ausführen und Debuggen** anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="81133-129">Select the **Run** icon to display the **Run and Debug** view.</span></span>
1. <span data-ttu-id="81133-130">Sie können auch die Tastenkombination **STRG + UMSCHALT + D** verwenden.</span><span class="sxs-lookup"><span data-stu-id="81133-130">You can also use the keyboard shortcut **Ctrl+Shift+D**.</span></span>

> [!TIP]
> <span data-ttu-id="81133-131">Möglicherweise wird der Dialog "App-Installation" im Browser nicht angezeigt, wenn Popupfenster für Ihren Browser deaktiviert sind.</span><span class="sxs-lookup"><span data-stu-id="81133-131">You may not see the app install dialogue in the browser if pop-up windows are disabled for your browser.</span></span> <span data-ttu-id="81133-132">Aktivieren Sie in diesem Fall Popupfenster, und aktualisieren Sie die Seite.</span><span class="sxs-lookup"><span data-stu-id="81133-132">If this happens, enable pop-up windows and refresh the page.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="81133-133">Weitere Informationen: Erstellen von apps mit dem Microsoft Teams-Toolkit und Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="81133-133">Learn more: Build apps with the Microsoft Teams Toolkit and Visual Studio Code</span></span>](visual-studio-code-overview.md)
