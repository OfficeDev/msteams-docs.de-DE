---
title: Erstellen von Apps mit dem Teams Toolkit und Visual Studio
description: Erste Schritte beim Erstellen von großartigen benutzerdefinierten Apps direkt in Visual Studio mit dem Microsoft Teams Toolkit
keywords: Visual Studio-Toolkit für Teams
localization_priority: Normal
ms.topic: overview
ms.author: johmil
ms.openlocfilehash: 6a0f466ba0d95312695be8b5460fc949e3f70811
ms.sourcegitcommit: 4ac93d69927791a8ccf678ca5ee83e63b51566b4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/23/2021
ms.locfileid: "53095514"
---
# <a name="build-apps-with-the-teams-toolkit-and-visual-studio"></a><span data-ttu-id="ee5bc-104">Erstellen von Apps mit dem Teams Toolkit und Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ee5bc-104">Build apps with the Teams Toolkit and Visual Studio</span></span>

<span data-ttu-id="ee5bc-105">Mithilfe des Microsoft Teams-Toolkits können Sie benutzerdefinierte Teams-Apps direkt innerhalb der integrierten Entwicklungsumgebung (Integrated Development Environment, IDE) von Visual Studio erstellen.</span><span class="sxs-lookup"><span data-stu-id="ee5bc-105">The Microsoft Teams Toolkit enables you to create custom Teams apps directly within the Visual Studio integrated development environment (IDE).</span></span> <span data-ttu-id="ee5bc-106">Das Microsoft Teams-Toolkit führt Sie durch den Vorgang und bietet alles, was Sie zum Erstellen, Debuggen und Starten Ihrer Teams-App benötigen.</span><span class="sxs-lookup"><span data-stu-id="ee5bc-106">The Microsoft Teams toolkit guides you through the process and provides everything you need to build, debug, and launch your Teams app.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ee5bc-107">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="ee5bc-107">Prerequisites</span></span>

1. <span data-ttu-id="ee5bc-108">[Aktivieren Sie die Entwicklervorschau.](../resources/dev-preview/developer-preview-intro.md#enable-developer-preview)</span><span class="sxs-lookup"><span data-stu-id="ee5bc-108">[Enable developer preview](../resources/dev-preview/developer-preview-intro.md#enable-developer-preview).</span></span>

2. <span data-ttu-id="ee5bc-109">Stellen Sie sicher, dass das **<span>ASP.NET-</span> und Webentwicklungsmodul** ihrer Visual Studio Instanz hinzugefügt wurde.</span><span class="sxs-lookup"><span data-stu-id="ee5bc-109">Make sure that the **<span>ASP.NET</span> and web development module** has been added to your Visual Studio instance.</span></span> <span data-ttu-id="ee5bc-110">Weitere Informationen finden Sie unter [Ändern Visual Studio durch Hinzufügen oder Entfernen von Workloads und Komponenten.](/visualstudio/install/modify-visual-studio?view=vs-2019&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="ee5bc-110">For more information, see [Modify Visual Studio by adding or removing workloads and components](/visualstudio/install/modify-visual-studio?view=vs-2019&preserve-view=true).</span></span>

![Visual Studio asp.net-Modul](../assets/images/visual-studio-web-dev-module.png)

## <a name="install-the-teams-toolkit"></a><span data-ttu-id="ee5bc-112">Installieren des Teams Toolkits</span><span class="sxs-lookup"><span data-stu-id="ee5bc-112">Install the Teams Toolkit</span></span>

<span data-ttu-id="ee5bc-113">The Microsoft Teams Toolkit for Visual Studio is available to download from the [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=msft-vsteamstoolkit.vsteamstoolkit) or directly from the **Extensions** menu within Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ee5bc-113">The Microsoft Teams Toolkit for Visual Studio is available for download from the [Visual Studio Marketplace](https://marketplace.visualstudio.com/items?itemName=msft-vsteamstoolkit.vsteamstoolkit) or directly from the **Extensions** menu within Visual Studio.</span></span>

## <a name="use-the-toolkit"></a><span data-ttu-id="ee5bc-114">Verwenden des Toolkits</span><span class="sxs-lookup"><span data-stu-id="ee5bc-114">Use the toolkit</span></span>

- [<span data-ttu-id="ee5bc-115">Einrichten eines neuen Projekts</span><span class="sxs-lookup"><span data-stu-id="ee5bc-115">Set up a new project</span></span>](#set-up-a-new-teams-project)
- [<span data-ttu-id="ee5bc-116">Konfigurieren Sie die App</span><span class="sxs-lookup"><span data-stu-id="ee5bc-116">Configure your app</span></span>](#configure-your-app)
- [<span data-ttu-id="ee5bc-117">Ausführen Ihrer App in Teams</span><span class="sxs-lookup"><span data-stu-id="ee5bc-117">Run your app in Teams</span></span>](#install-and-run-your-app-locally)
- [<span data-ttu-id="ee5bc-118">Validieren Ihrer App</span><span class="sxs-lookup"><span data-stu-id="ee5bc-118">Validate your app</span></span>](#validate-your-app)
- [<span data-ttu-id="ee5bc-119">Veröffentlichen eigener Apps</span><span class="sxs-lookup"><span data-stu-id="ee5bc-119">Publish your app</span></span>](#publish-your-app-to-teams)

## <a name="set-up-a-new-teams-project"></a><span data-ttu-id="ee5bc-120">Einrichten eines neuen Teams Projekts</span><span class="sxs-lookup"><span data-stu-id="ee5bc-120">Set up a new Teams project</span></span>

1. <span data-ttu-id="ee5bc-121">Starten Sie Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="ee5bc-121">Launch Visual Studio 2019.</span></span>
2. <span data-ttu-id="ee5bc-122">Wählen Sie **"Neues Projekt erstellen"** aus.</span><span class="sxs-lookup"><span data-stu-id="ee5bc-122">Select **Create a new project**.</span></span>
3. <span data-ttu-id="ee5bc-123">Suchen Sie nach **Microsoft Teams App,** und wählen Sie **"Weiter"** aus.</span><span class="sxs-lookup"><span data-stu-id="ee5bc-123">Search for **Microsoft Teams App** and select **Next**.</span></span>
4. <span data-ttu-id="ee5bc-124">Geben Sie im **Feld "Neues Projekt konfigurieren"** den **Namen Project,** **den Speicherort** und den **Projektmappennamen ein.**</span><span class="sxs-lookup"><span data-stu-id="ee5bc-124">In the **Configure your new project**, enter the **Project name**, **Location**, and **Solution name**.</span></span>
5. <span data-ttu-id="ee5bc-125">Wählen Sie **"Weiter"** aus, um einen Namen für die App einzugeben.</span><span class="sxs-lookup"><span data-stu-id="ee5bc-125">Select **Next** to enter a name for the app.</span></span>
6. <span data-ttu-id="ee5bc-126">Geben Sie im Bildschirm "Zusätzliche Informationen" einen **Anwendungsnamen** und einen **Entwickler- oder Firmennamen** für Ihre Teams-App ein.</span><span class="sxs-lookup"><span data-stu-id="ee5bc-126">In the Additional Information screen, enter an **Application Name** and **Developer or Company name** for your Teams app.</span></span>

## <a name="configure-your-app"></a><span data-ttu-id="ee5bc-127">Konfigurieren Sie die App</span><span class="sxs-lookup"><span data-stu-id="ee5bc-127">Configure your app</span></span>

<span data-ttu-id="ee5bc-128">Im Kern umfasst die Teams App drei Komponenten:</span><span class="sxs-lookup"><span data-stu-id="ee5bc-128">At its core, the Teams app embraces three components:</span></span>

- <span data-ttu-id="ee5bc-129">Der Microsoft Teams Client (Web, Desktop oder Mobil), auf dem Benutzer mit Ihrer App interagieren.</span><span class="sxs-lookup"><span data-stu-id="ee5bc-129">The Microsoft Teams client (web, desktop or mobile) where users interact with your app.</span></span>
- <span data-ttu-id="ee5bc-130">Ein Server, der auf Anforderungen für Inhalte reagiert, die in Teams angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="ee5bc-130">A server that responds to requests for content displayed in Teams.</span></span> <span data-ttu-id="ee5bc-131">Beispiel: HTML-Registerkarteninhalt oder eine adaptive Bot-Karte.</span><span class="sxs-lookup"><span data-stu-id="ee5bc-131">For example, HTML tab content or a bot adaptive card.</span></span>
- <span data-ttu-id="ee5bc-132">Ein Teams-App-Paket besteht aus drei Dateien:</span><span class="sxs-lookup"><span data-stu-id="ee5bc-132">A Teams app package consists of three files:</span></span>

    > [!div class="checklist"]
    >
    > - <span data-ttu-id="ee5bc-133">Die manifest.json</span><span class="sxs-lookup"><span data-stu-id="ee5bc-133">The manifest.json</span></span>
    > - <span data-ttu-id="ee5bc-134">Ein [Farbsymbol](../resources/schema/manifest-schema.md#icons) für Ihre App, das im öffentlichen App- oder Organisations-App-Katalog angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="ee5bc-134">A [color icon](../resources/schema/manifest-schema.md#icons) for your app to display in the public or organization app catalog.</span></span>
    > - <span data-ttu-id="ee5bc-135">Ein [Gliederungssymbol](../resources/schema/manifest-schema.md#icons) für die Anzeige auf der Teams Aktivitätsleiste.</span><span class="sxs-lookup"><span data-stu-id="ee5bc-135">An [outline icon](../resources/schema/manifest-schema.md#icons) for display on the Teams activity bar.</span></span>

<span data-ttu-id="ee5bc-136">Wenn eine App installiert ist, analysiert der Teams Client die Manifestdatei, um die erforderlichen Informationen wie den Namen Ihrer App und die URL zu ermitteln, unter der sich die Dienste befinden.</span><span class="sxs-lookup"><span data-stu-id="ee5bc-136">When an app is installed, the Teams client parses the manifest file to determine needed information like the name of your app and the URL where the services are located.</span></span>

> [!NOTE]
><span data-ttu-id="ee5bc-137">Wenn sie dies noch nicht getan haben, müssen Sie sich bei Ihrem Microsoft 365 Konto anmelden, um den Entwicklungsprozess fortzusetzen.</span><span class="sxs-lookup"><span data-stu-id="ee5bc-137">If you have not done so already, you must sign in to your Microsoft 365 account to continue with the development process.</span></span>
>
> <span data-ttu-id="ee5bc-138">Wenn Sie nicht über ein Microsoft 365 Konto verfügen, können Sie sich für ein [Abonnement des Microsoft 365 Entwicklerprogramms](https://developer.microsoft.com/microsoft-365/dev-program) registrieren.</span><span class="sxs-lookup"><span data-stu-id="ee5bc-138">If you do not have a Microsoft 365 account, you can sign up for a [Microsoft 365 Developer Program](https://developer.microsoft.com/microsoft-365/dev-program) subscription.</span></span> <span data-ttu-id="ee5bc-139">Es ist 90 Tage kostenlos und wird verlängert, solange Sie es für Entwicklungsaktivitäten verwenden.</span><span class="sxs-lookup"><span data-stu-id="ee5bc-139">It's free for 90 days and renews as long as you are using it for development activity.</span></span> <span data-ttu-id="ee5bc-140">Wenn Sie über ein Visual Studio Enterprise- oder Professional-Abonnement verfügen, enthalten beide Programme ein kostenloses Microsoft 365 [Entwicklerabonnement,](https://aka.ms/MyVisualStudioBenefits)das für die Lebensdauer Ihres Visual Studio Abonnements aktiv ist.</span><span class="sxs-lookup"><span data-stu-id="ee5bc-140">If you have a Visual Studio Enterprise or Professional subscription, both programs include a free Microsoft 365 [developer subscription](https://aka.ms/MyVisualStudioBenefits), active for the life of your Visual Studio subscription.</span></span> <span data-ttu-id="ee5bc-141">Weitere Informationen finden Sie unter [Einrichten eines Microsoft 365 Entwicklerabonnements.](/office/developer-program/office-365-developer-program-get-started)</span><span class="sxs-lookup"><span data-stu-id="ee5bc-141">For more information, see [set up a Microsoft 365 developer subscription](/office/developer-program/office-365-developer-program-get-started).</span></span>

### <a name="configuration-steps"></a><span data-ttu-id="ee5bc-142">Konfigurationsschritte </span><span class="sxs-lookup"><span data-stu-id="ee5bc-142">Configuration steps</span></span>

1. <span data-ttu-id="ee5bc-143">Um Ihre App zu konfigurieren, wählen Sie das Menü **Project > TeamsFx > Konfigurieren für SSO...** aus.</span><span class="sxs-lookup"><span data-stu-id="ee5bc-143">To configure your app, select the **Project > TeamsFx > Configure for SSO...** menu.</span></span>

<span data-ttu-id="ee5bc-144">Wenn Sie dazu aufgefordert werden, melden Sie sich bei Ihrem Microsoft-Konto an, das über einen M365-Mandanten verfügt.</span><span class="sxs-lookup"><span data-stu-id="ee5bc-144">When prompted, sign in to your Microsoft account that has an M365 tenant.</span></span>

## <a name="install-and-run-your-app-locally"></a><span data-ttu-id="ee5bc-145">Lokales Installieren und Ausführen der App</span><span class="sxs-lookup"><span data-stu-id="ee5bc-145">Install and run your app locally</span></span>

<span data-ttu-id="ee5bc-146">Drücken Sie F5, um das Debuggen zu starten.</span><span class="sxs-lookup"><span data-stu-id="ee5bc-146">Press F5 to start debugging.</span></span> <span data-ttu-id="ee5bc-147">Das Dialogfeld für die App-Installation wird im Teams Client angezeigt.</span><span class="sxs-lookup"><span data-stu-id="ee5bc-147">The app installation dialog box appears in the Teams client.</span></span>

## <a name="validate-your-app"></a><span data-ttu-id="ee5bc-148">Validieren Ihrer App</span><span class="sxs-lookup"><span data-stu-id="ee5bc-148">Validate your app</span></span>

<span data-ttu-id="ee5bc-149">Im Menü **Project > TeamsFx Validate > Teams Manifest** können Sie überprüfen, ob Ihr App-Paket gültig ist.</span><span class="sxs-lookup"><span data-stu-id="ee5bc-149">The **Project > TeamsFx Validate > Teams Manifest** menu allows you to check that your app package is valid.</span></span>

## <a name="publish-your-app-to-teams"></a><span data-ttu-id="ee5bc-150">Veröffentlichen Ihrer App in Teams</span><span class="sxs-lookup"><span data-stu-id="ee5bc-150">Publish your app to Teams</span></span>

<span data-ttu-id="ee5bc-151">Im [Teams Entwicklerportal](https://dev.teams.microsoft.com/home)können Sie Ihre App in ein Team hochladen, Ihre App an den benutzerdefinierten App-Store Ihres Unternehmens für Benutzer in Ihrer Organisation übermitteln oder Ihre App für alle Teams Benutzer an app Source übermitteln.</span><span class="sxs-lookup"><span data-stu-id="ee5bc-151">In the [Teams Developer Portal](https://dev.teams.microsoft.com/home), you can upload your app to a team, submit your app to your company custom app store for users in your organization, or submit your app to App Source for all Teams users.</span></span>

- <span data-ttu-id="ee5bc-152">Ihr IT-Administrator wird diese Übermittlungen überprüfen.</span><span class="sxs-lookup"><span data-stu-id="ee5bc-152">Your IT admin will review these submissions.</span></span>
- <span data-ttu-id="ee5bc-153">Sie können zur **Veröffentlichungsseite** zurückkehren, um ihren Übermittlungsstatus zu überprüfen und zu erfahren, ob Ihre App von Ihrem IT-Administrator genehmigt oder abgelehnt wurde. Hier können Sie auch Updates für Ihre App übermitteln oder alle derzeit aktiven Übermittlungen abbrechen.</span><span class="sxs-lookup"><span data-stu-id="ee5bc-153">You can return to the **Publish** page to check on your submission status and learn if your app was approved or rejected by your IT admin. This is also where you can submit updates to your app or cancel any currently active submissions.</span></span>

## <a name="next-step"></a><span data-ttu-id="ee5bc-154">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="ee5bc-154">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ee5bc-155">Erstellen und Ausführen Ihrer ersten Microsoft Teams-App mit Demerz</span><span class="sxs-lookup"><span data-stu-id="ee5bc-155">Build and run your first Microsoft Teams app with Blazor</span></span>](../get-started/first-app-blazor.md)
