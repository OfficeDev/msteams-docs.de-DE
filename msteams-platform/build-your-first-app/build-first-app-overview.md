---
title: Erste Schritte – Erstellen Der ersten App-Übersicht und der voraussetzungen
author: heath-hamilton
description: Erfahren Sie, wie Sie mit der Entwicklung von Microsoft Teams-Apps beginnen und Ihre Umgebung einrichten.
ms.author: lajanuar
localization_priority: Normal
ms.date: 11/03/2020
ms.topic: quickstart
ms.openlocfilehash: d975383022089579a04317de73595106e7920c56
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2021
ms.locfileid: "52019993"
---
# <a name="build-your-first-microsoft-teams-app-overview"></a><span data-ttu-id="a4008-103">Erstellen Der ersten Microsoft Teams-App-Übersicht</span><span class="sxs-lookup"><span data-stu-id="a4008-103">Build your first Microsoft Teams app overview</span></span>

<span data-ttu-id="a4008-104">In den **ersten Lektionen** erfahren Sie, wie Sie grundlegende Teams-Apps erstellen.</span><span class="sxs-lookup"><span data-stu-id="a4008-104">In the **get started** lessons, you learn how to create basic Teams apps.</span></span> <span data-ttu-id="a4008-105">In jedem Lernprogramm wird das Erstellen einer einfachen, realen Teams-App erläutert, während Sie allgemeine Tools, grundlegende Konzepte und erweiterte Features kennen lernen.</span><span class="sxs-lookup"><span data-stu-id="a4008-105">Each tutorial walks through how to build a simple, real-world Teams app while introducing you to common tools, fundamental concepts, and more advanced features.</span></span>

## <a name="what-youll-learn"></a><span data-ttu-id="a4008-106">Was Sie lernen werden</span><span class="sxs-lookup"><span data-stu-id="a4008-106">What you'll learn</span></span>

<span data-ttu-id="a4008-107">Hier finden Sie eine Vorstellung davon, was Sie wissen werden, nachdem Sie die Lektionen durchgef?llt haben.</span><span class="sxs-lookup"><span data-stu-id="a4008-107">Here's an idea of what you'll know after going through the lessons.</span></span>

> [!div class="checklist"]
  >
  > * <span data-ttu-id="a4008-108">Starten Sie schnell mit dem **Teams Toolkit:** Das Microsoft Teams Toolkit für Visual Studio Code sorgt für die Erstellung Ihres App-Projekts und des Gerüsts, sodass Sie eine ausgeführte App in Minuten haben können.</span><span class="sxs-lookup"><span data-stu-id="a4008-108">**Get up and running quickly with the Teams Toolkit**: The Microsoft Teams Toolkit for Visual Studio Code takes care of creating your app project and scaffolding so you can have a running app in minutes.</span></span>
  > * <span data-ttu-id="a4008-109">**Konfigurieren Sie Ihre App mit App Studio:** Geben Sie die Funktionen und Dienste an, die Ihre Teams-App verwendet.</span><span class="sxs-lookup"><span data-stu-id="a4008-109">**Configure your app with App Studio**: Specify the capabilities and services your Teams app uses.</span></span>
  > * <span data-ttu-id="a4008-110">**Bereich der Zielgruppe Ihrer App:** Erstellen Sie eine Teams-App für den persönlichen Gebrauch, die Zusammenarbeit oder beides.</span><span class="sxs-lookup"><span data-stu-id="a4008-110">**Scope your app's audience**: Build a Teams app for personal use, collaboration, or both.</span></span>
> * <span data-ttu-id="a4008-111">**Erhalten Sie Erfahrung mit Teams-Tools und SDKs:** Passen Sie Ihre App mithilfe des Teams JavaScript-Client-SDK an.</span><span class="sxs-lookup"><span data-stu-id="a4008-111">**Get experience with Teams tools and SDKs**: Customize your app with help from the Teams JavaScript client SDK.</span></span> <span data-ttu-id="a4008-112">Ändern Sie beispielsweise das Farbschema Ihrer App so, dass es mit dem Teams-Design übereinstimmen kann.</span><span class="sxs-lookup"><span data-stu-id="a4008-112">For example, change your app's color scheme to match the Teams theme.</span></span> <span data-ttu-id="a4008-113">Außerdem erfahren Sie mehr über gängige Tools zum Erstellen und Verwalten von Bots.</span><span class="sxs-lookup"><span data-stu-id="a4008-113">Also, learn about common tools for creating and managing bots.</span></span>
  > * <span data-ttu-id="a4008-114">**Erweitern Sie Ihre App:** Im Laufe der Lektionen finden Sie verwandte Themen, die Sie wahrscheinlich interessieren (z. B. Authentifizierungs- und Entwurfsrichtlinien).</span><span class="sxs-lookup"><span data-stu-id="a4008-114">**Expand on your app**: Throughout the lessons, you'll find related topics you're probably interested in (such as authentication and design guidelines).</span></span>

## <a name="teams-app-fundamentals"></a><span data-ttu-id="a4008-115">Grundlagen der Teams-App</span><span class="sxs-lookup"><span data-stu-id="a4008-115">Teams app fundamentals</span></span>

<span data-ttu-id="a4008-116">Bevor Sie mit den Lernprogrammen beginnen, sollten Sie Folgendes über das Erstellen von Apps für Teams wissen.</span><span class="sxs-lookup"><span data-stu-id="a4008-116">Before you begin the tutorials, you should know the following about building apps for Teams.</span></span>

### <a name="apps-can-have-multiple-capabilities-and-entry-points"></a><span data-ttu-id="a4008-117">Apps können über mehrere Funktionen und Einstiegspunkte verfügen</span><span class="sxs-lookup"><span data-stu-id="a4008-117">Apps can have multiple capabilities and entry points</span></span>

<span data-ttu-id="a4008-118">Eine Teams-App besteht aus einer oder mehreren Plattformfunktionen [(wie](../concepts/capabilities-overview.md) Personen die App verwenden) und Einstiegspunkten [(wo](../concepts/extensibility-points.md) Personen die App verwenden).</span><span class="sxs-lookup"><span data-stu-id="a4008-118">A Teams app is made up of one or more [platform capabilities](../concepts/capabilities-overview.md) (how people use the app) and [entry points](../concepts/extensibility-points.md) (where people use the app).</span></span>

### <a name="teams-doesnt-host-your-app"></a><span data-ttu-id="a4008-119">Teams hosten Ihre App nicht</span><span class="sxs-lookup"><span data-stu-id="a4008-119">Teams doesn't host your app</span></span>

<span data-ttu-id="a4008-120">Eine Teams-App enthält die folgenden wichtigen Teile:</span><span class="sxs-lookup"><span data-stu-id="a4008-120">A Teams app includes the following important pieces:</span></span>

* <span data-ttu-id="a4008-121">Die Logik, datenspeicherung und API-Aufrufe, die Ihre App unterstützen.</span><span class="sxs-lookup"><span data-stu-id="a4008-121">The logic, data storage, and API calls that power your app.</span></span> <span data-ttu-id="a4008-122">Diese Dienste werden nicht von Teams gehostet und müssen über HTTPS zugänglich sein.</span><span class="sxs-lookup"><span data-stu-id="a4008-122">These services are not hosted by Teams and must be accessible via HTTPS.</span></span>
* <span data-ttu-id="a4008-123">Der Teams-Client (Web, Desktop oder Mobile), auf dem Personen Ihre App verwenden.</span><span class="sxs-lookup"><span data-stu-id="a4008-123">The Teams client (web, desktop, or mobile) where people use your app.</span></span>
* <span data-ttu-id="a4008-124">Ihre App-ID, mit der Sie Ihre App mit App Studio konfigurieren können.</span><span class="sxs-lookup"><span data-stu-id="a4008-124">Your app ID, which lets you configure your app with App Studio.</span></span>

## <a name="get-prerequisites"></a><span data-ttu-id="a4008-125">Erforderliche Komponenten erhalten</span><span class="sxs-lookup"><span data-stu-id="a4008-125">Get prerequisites</span></span>

<span data-ttu-id="a4008-126">Überprüfen Sie, ob Sie über das richtige Konto zum Erstellen von Teams-Apps verfügen und einige empfohlene Entwicklungstools installieren.</span><span class="sxs-lookup"><span data-stu-id="a4008-126">Verify you have the right account for building Teams apps and install some recommended development tools.</span></span>

### <a name="set-up-your-development-account"></a><span data-ttu-id="a4008-127">Einrichten Ihres Entwicklungskontos</span><span class="sxs-lookup"><span data-stu-id="a4008-127">Set up your development account</span></span>

<span data-ttu-id="a4008-128">Sie benötigen ein Teams-Konto, das das Querladen benutzerdefinierter Apps zulässt.</span><span class="sxs-lookup"><span data-stu-id="a4008-128">You need a Teams account that allows custom app sideloading.</span></span> <span data-ttu-id="a4008-129">(Ihr Konto kann dies bereits bereitstellen.)</span><span class="sxs-lookup"><span data-stu-id="a4008-129">(Your account may already provide this.)</span></span>

1. <span data-ttu-id="a4008-130">Wenn Sie über ein Teams-Konto verfügen, überprüfen Sie, ob Sie Apps in Teams querladen können:</span><span class="sxs-lookup"><span data-stu-id="a4008-130">If you have a Teams account, verify if you can sideload apps in Teams:</span></span>
    1. <span data-ttu-id="a4008-131">Wählen Sie im Teams-Client **Apps aus.**</span><span class="sxs-lookup"><span data-stu-id="a4008-131">In the Teams client, select **Apps**.</span></span>
    1. <span data-ttu-id="a4008-132">Suchen Sie nach einer Option zum **Hochladen einer benutzerdefinierten App.**</span><span class="sxs-lookup"><span data-stu-id="a4008-132">Look for an option to **Upload a custom app**.</span></span>

    :::image type="content" source="../assets/images/build-your-first-app/upload-custom-app-closeup.png" alt-text="Abbildung, die zeigt, wo in Teams Sie eine benutzerdefinierte App hochladen können.":::
    
    <span data-ttu-id="a4008-134">Wenn die Schaltfläche nicht angezeigt wird, verfügen Sie nicht über die Berechtigung zum Hochladen benutzerdefinierter Apps in Ihrer Organisation. Sie können dieses Feature erhalten, indem Sie sich für ein kostenloses Microsoft 365-Entwicklerabonnement anmelden.</span><span class="sxs-lookup"><span data-stu-id="a4008-134">If you don't see the button, you don't have permission to upload custom apps in your org. You can get this feature by signing up for a free Microsoft 365 developer subscription.</span></span>

<!-- markdownlint-disable MD033 -->
<details>

<summary><span data-ttu-id="a4008-135"><b>Kostenloses Microsoft 365-Entwicklerabonnement</b></span><span class="sxs-lookup"><span data-stu-id="a4008-135"><b>Get your free Microsoft 365 developer subscription</b></span></span></summary>

<span data-ttu-id="a4008-136">Sie können ein kostenloses Teams-Testkonto erhalten, das das Querladen von Apps ermöglicht, indem Sie am Microsoft 365-Entwicklerprogramm teilnehmen.</span><span class="sxs-lookup"><span data-stu-id="a4008-136">You can get a free Teams test account that allows app sideloading by joining the Microsoft 365 developer program.</span></span> <span data-ttu-id="a4008-137">(Der Registrierungsprozess dauert ca. zwei Minuten.)</span><span class="sxs-lookup"><span data-stu-id="a4008-137">(The registration process takes approximately two minutes.)</span></span>

1. <span data-ttu-id="a4008-138">Wechseln Sie zum [Microsoft 365-Entwicklerprogramm](https://developer.microsoft.com/microsoft-365/dev-program).</span><span class="sxs-lookup"><span data-stu-id="a4008-138">Go to the [Microsoft 365 developer program](https://developer.microsoft.com/microsoft-365/dev-program).</span></span>
1. <span data-ttu-id="a4008-139">Wählen **Sie Jetzt beitreten** aus, und folgen Sie den Anweisungen auf dem Bildschirm.</span><span class="sxs-lookup"><span data-stu-id="a4008-139">Select **Join Now** and follow the onscreen instructions.</span></span>
1. <span data-ttu-id="a4008-140">Wenn Sie zum Willkommensbildschirm kommen, wählen Sie **E5-Abonnement einrichten aus.**</span><span class="sxs-lookup"><span data-stu-id="a4008-140">When you get to the welcome screen, select **Set up E5 subscription**.</span></span>
1. <span data-ttu-id="a4008-141">Richten Sie Ihr Administratorkonto ein.</span><span class="sxs-lookup"><span data-stu-id="a4008-141">Set up your administrator account.</span></span> <span data-ttu-id="a4008-142">Sobald Sie fertig sind, sollte ein Bildschirm wie dieser angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="a4008-142">Once you finish, you should see a screen like this.</span></span>
:::image type="content" source="../assets/images/build-your-first-app/dev-program-subscription.png" alt-text="Beispiel für das, was Sie nach der Anmeldung für das Microsoft 365-Entwicklerprogramm sehen.":::
1. <span data-ttu-id="a4008-144">Melden Sie sich mit dem Administratorkonto, das Sie gerade eingerichtet haben, bei Teams an.</span><span class="sxs-lookup"><span data-stu-id="a4008-144">Log in to Teams using the administrator account you just set up.</span></span>
1. <span data-ttu-id="a4008-145">Überprüfen Sie, ob Sie jetzt über die **Option Benutzerdefinierte App hochladen** verfügen.</span><span class="sxs-lookup"><span data-stu-id="a4008-145">Verify if you now have the **Upload a custom app** option.</span></span>

</details>

> [!Note]
> <span data-ttu-id="a4008-146">Wenn Sie Apps weiterhin nicht querladen können, lesen Sie Aktivieren von benutzerdefinierten [Teams-Apps und Aktivieren des Hochladens benutzerdefinierter Apps.](https://docs.microsoft.com/microsoftteams/platform/concepts/build-and-test/prepare-your-o365-tenant#enable-custom-teams-apps-and-turn-on-custom-app-uploading)</span><span class="sxs-lookup"><span data-stu-id="a4008-146">If you still can't sideload apps, see [enable custom Teams apps and turn on custom app uploading](https://docs.microsoft.com/microsoftteams/platform/concepts/build-and-test/prepare-your-o365-tenant#enable-custom-teams-apps-and-turn-on-custom-app-uploading).</span></span>

### <a name="install-your-development-tools"></a><span data-ttu-id="a4008-147">Installieren der Entwicklungstools</span><span class="sxs-lookup"><span data-stu-id="a4008-147">Install your development tools</span></span>

<span data-ttu-id="a4008-148">Sie können Teams-Apps mit Ihren bevorzugten Tools erstellen, aber diese Lektionen zeigen, wie Sie schnell mit dem Microsoft Teams Toolkit for Visual Studio Code beginnen können.</span><span class="sxs-lookup"><span data-stu-id="a4008-148">You can build Teams apps with your preferred tools, but these lessons show how you can get started quickly with the Microsoft Teams Toolkit for Visual Studio Code.</span></span>

<span data-ttu-id="a4008-149">Teams zeigt App-Inhalte nur über HTTPS-Verbindungen an.</span><span class="sxs-lookup"><span data-stu-id="a4008-149">Teams displays app content only through HTTPS connections.</span></span> <span data-ttu-id="a4008-150">Um bestimmte Arten von Apps lokal zu debuggen, z. B. einen Bot, erfahren Sie, wie Sie [ngrok](../concepts/build-and-test/debug.md#locally-hosted) zum Einrichten eines sicheren Tunnels zwischen Teams und Ihrer App verwenden.</span><span class="sxs-lookup"><span data-stu-id="a4008-150">To debug certain types of apps locally, such as a bot, you'll learn how to use [ngrok to set up a secure tunnel](../concepts/build-and-test/debug.md#locally-hosted) between Teams and your app.</span></span> <span data-ttu-id="a4008-151">(Produktionsteams-Apps werden in der Cloud gehostet.)</span><span class="sxs-lookup"><span data-stu-id="a4008-151">(Production Teams apps are hosted in the cloud.)</span></span>

1. <span data-ttu-id="a4008-152">Installieren Sie [Node.js](https://nodejs.org/en/).</span><span class="sxs-lookup"><span data-stu-id="a4008-152">Install [Node.js](https://nodejs.org/en/).</span></span>
1. <span data-ttu-id="a4008-153">Installieren [Sie ngrok,](https://ngrok.com/download) wenn Sie eine Bot- oder Messagingerweiterung erstellen und einen [Tunnel mit ngrok erstellen.](https://docs.microsoft.com/microsoftteams/platform/tutorials/get-started-dotnet-app-studio#tunnel-using-ngrok)</span><span class="sxs-lookup"><span data-stu-id="a4008-153">Install [ngrok](https://ngrok.com/download) if you are building a bot or messaging extension and [create a tunnel using ngrok](https://docs.microsoft.com/microsoftteams/platform/tutorials/get-started-dotnet-app-studio#tunnel-using-ngrok).</span></span>
1. <span data-ttu-id="a4008-154">Installieren Sie die neueste Version von [Visual Studio Code](https://code.visualstudio.com/download).</span><span class="sxs-lookup"><span data-stu-id="a4008-154">Install the latest version of [Visual Studio Code](https://code.visualstudio.com/download).</span></span> <span data-ttu-id="a4008-155">(Frühere Versionen funktionieren möglicherweise nicht mit dem Toolkit.)</span><span class="sxs-lookup"><span data-stu-id="a4008-155">(Earlier versions might not work with the toolkit.)</span></span>
1. Wählen Visual Studio Code **auf** der linken :::image type="icon" source="../assets/icons/vs-code-extensions.png"::: Aktivitätsleiste Erweiterungen aus, und installieren Sie **das Microsoft Teams Toolkit**.

    :::image type="content" source="../assets/images/build-your-first-app/vsc-install-toolkit.png" alt-text="Abbildung, in der Visual Studio Code die Microsoft Teams Toolkit-Erweiterung installieren können.":::

## <a name="about-the-tutorials"></a><span data-ttu-id="a4008-158">Informationen zu den Lernprogrammen</span><span class="sxs-lookup"><span data-stu-id="a4008-158">About the tutorials</span></span>

<span data-ttu-id="a4008-159">Sie können mit einem der teams **get started-Lektionen** beginnen.</span><span class="sxs-lookup"><span data-stu-id="a4008-159">You can start with any of the Teams **get started** lessons.</span></span> <span data-ttu-id="a4008-160">Wenn Sie nicht sicher sind, wo Sie zuerst hingehen sollten, folgen Sie unserem anfängerfreundlichen Pfad und erstellen Sie ein "Hello, World!"</span><span class="sxs-lookup"><span data-stu-id="a4008-160">If you're not sure where to go first, follow our beginner friendly path and build a "Hello, World!"</span></span> <span data-ttu-id="a4008-161">app.</span><span class="sxs-lookup"><span data-stu-id="a4008-161">app.</span></span>

:::image type="content" source="../assets/images/build-your-first-app/skill-tree-overview.png" alt-text="Skill tree showing learning paths for the Teams 'get started' lessons." border="false":::

## <a name="next-step"></a><span data-ttu-id="a4008-163">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="a4008-163">Next step</span></span>

<span data-ttu-id="a4008-164">Nachdem Sie Ihr Konto und Ihre Umgebung eingerichtet haben, können Sie mit der Einrichtung beginnen.</span><span class="sxs-lookup"><span data-stu-id="a4008-164">Once you set up your account and environment, you can start building.</span></span>

### <a name="beginner-friendly-tutorial"></a><span data-ttu-id="a4008-165">Lernprogramm für Anfänger</span><span class="sxs-lookup"><span data-stu-id="a4008-165">Beginner friendly tutorial</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a4008-166">Erstellen einer "Hello, World!"-App</span><span class="sxs-lookup"><span data-stu-id="a4008-166">Build a "Hello, World!" app</span></span>](../build-your-first-app/build-and-run.md)

### <a name="other-tutorials"></a><span data-ttu-id="a4008-167">Andere Lernprogramme</span><span class="sxs-lookup"><span data-stu-id="a4008-167">Other tutorials</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a4008-168">Erstellen eines Bots</span><span class="sxs-lookup"><span data-stu-id="a4008-168">Build a bot</span></span>](../build-your-first-app/build-bot.md)
> [!div class="nextstepaction"]
> [<span data-ttu-id="a4008-169">Erstellen einer Messaging-Erweiterung</span><span class="sxs-lookup"><span data-stu-id="a4008-169">Build a messaging extension</span></span>](../build-your-first-app/build-messaging-extension.md)
