---
title: Erste Schritte – Erstellen der ersten App-Übersicht und voraussetzungen
author: heath-hamilton
description: Erfahren Sie, wie Sie mit der Entwicklung von Microsoft Teams-Apps beginnen und Ihre Umgebung einrichten.
ms.author: lajanuar
ms.date: 11/03/2020
ms.topic: quickstart
ms.openlocfilehash: 06e26c57e6f6d3fd0bbeb981ef7ab46c8217bb4a
ms.sourcegitcommit: 5687a901d48bcf2f5a3a086e0f703f854e8b9c21
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/11/2021
ms.locfileid: "49795461"
---
# <a name="build-your-first-microsoft-teams-app-overview"></a><span data-ttu-id="95fa2-103">Erstellen Einer Übersicht über Ihre erste Microsoft Teams-App</span><span class="sxs-lookup"><span data-stu-id="95fa2-103">Build your first Microsoft Teams app overview</span></span>

<span data-ttu-id="95fa2-104">In der **Erstellung Ihrer ersten App-Lektionen** erstellen Sie grundlegende Teams-Apps.</span><span class="sxs-lookup"><span data-stu-id="95fa2-104">In the **build your first app** lessons, you create basic Teams apps.</span></span> <span data-ttu-id="95fa2-105">Jedes Lernprogramm führt Sie durch das Erstellen einer einfachen, realen Teams-App und führt Sie gleichzeitig mit gängigen Tools, grundlegenden Konzepten und erweiterten Features ein.</span><span class="sxs-lookup"><span data-stu-id="95fa2-105">Each tutorial walks through how to build a simple, real-world Teams app while introducing you to common tools, fundamental concepts, and more advanced features.</span></span>

## <a name="what-youll-learn"></a><span data-ttu-id="95fa2-106">Was Sie lernen werden</span><span class="sxs-lookup"><span data-stu-id="95fa2-106">What you'll learn</span></span>

<span data-ttu-id="95fa2-107">Hier sehen Sie eine Vorstellung davon, was Sie wissen werden, nachdem Sie die Lektionen durchgef llt.</span><span class="sxs-lookup"><span data-stu-id="95fa2-107">Here's an idea of what you'll know after going through the lessons.</span></span>

> [!div class="checklist"]
  >
  > * <span data-ttu-id="95fa2-108">Starten Sie schnell mit dem **Teams Toolkit:** Das Microsoft Teams Toolkit für Visual Studio Code übernimmt die Erstellung Ihres App-Projekts und -Gerüsts, damit Sie eine ausgeführte App in Minuten haben können.</span><span class="sxs-lookup"><span data-stu-id="95fa2-108">**Get up and running quickly with the Teams Toolkit**: The Microsoft Teams Toolkit for Visual Studio Code takes care of creating your app project and scaffolding so you can have a running app in minutes.</span></span>
  > * <span data-ttu-id="95fa2-109">**Konfigurieren Sie Ihre App mit App Studio:** Geben Sie die Funktionen und Dienste an, die Ihre Teams-App verwendet.</span><span class="sxs-lookup"><span data-stu-id="95fa2-109">**Configure your app with App Studio**: Specify the capabilities and services your Teams app uses.</span></span>
  > * <span data-ttu-id="95fa2-110">**Umfang der Zielgruppe Ihrer App:** Erstellen Sie eine Teams-App für die persönliche Verwendung, Zusammenarbeit oder beides.</span><span class="sxs-lookup"><span data-stu-id="95fa2-110">**Scope your app's audience**: Build a Teams app for personal use, collaboration, or both.</span></span>
> * <span data-ttu-id="95fa2-111">**Erfahren Sie mehr über Teams-Tools und SDKs:** Passen Sie Ihre App mithilfe des JavaScript-Client-SDK für Teams an.</span><span class="sxs-lookup"><span data-stu-id="95fa2-111">**Get experience with Teams tools and SDKs**: Customize your app with help from the Teams JavaScript client SDK.</span></span> <span data-ttu-id="95fa2-112">Ändern Sie z. B. das Farbschema Ihrer App so, dass es dem Design "Teams" zu entsprechen.</span><span class="sxs-lookup"><span data-stu-id="95fa2-112">For example, change your app's color scheme to match the Teams theme.</span></span> <span data-ttu-id="95fa2-113">Erfahren Sie außerdem mehr über allgemeine Tools zum Erstellen und Verwalten von Bots.</span><span class="sxs-lookup"><span data-stu-id="95fa2-113">Also, learn about common tools for creating and managing bots.</span></span>
  > * <span data-ttu-id="95fa2-114">**Erweitern Sie Ihre App:** Im Laufe der Lektionen finden Sie verwandte Themen, an denen Sie wahrscheinlich interessiert sind (z. B. Authentifizierungs- und Entwurfsrichtlinien).</span><span class="sxs-lookup"><span data-stu-id="95fa2-114">**Expand on your app**: Throughout the lessons, you'll find related topics you're probably interested in (such as authentication and design guidelines).</span></span>

## <a name="teams-app-fundamentals"></a><span data-ttu-id="95fa2-115">Grundlagen der Teams-App</span><span class="sxs-lookup"><span data-stu-id="95fa2-115">Teams app fundamentals</span></span>

<span data-ttu-id="95fa2-116">Bevor Sie mit den Lernprogrammen beginnen, sollten Sie Folgendes zum Erstellen von Apps für Teams wissen.</span><span class="sxs-lookup"><span data-stu-id="95fa2-116">Before you begin the tutorials, you should know the following about building apps for Teams.</span></span>

### <a name="apps-can-have-multiple-capabilities-and-entry-points"></a><span data-ttu-id="95fa2-117">Apps können über mehrere Funktionen und Einstiegspunkte verfügen</span><span class="sxs-lookup"><span data-stu-id="95fa2-117">Apps can have multiple capabilities and entry points</span></span>

<span data-ttu-id="95fa2-118">Eine Teams-App besteht aus einer oder mehreren Plattformfunktionen [(wie](../concepts/capabilities-overview.md) Personen die App verwenden) und Einstiegspunkten [(wo](../concepts/extensibility-points.md) Personen die App entdecken).</span><span class="sxs-lookup"><span data-stu-id="95fa2-118">A Teams app is made up of one or more [platform capabilities](../concepts/capabilities-overview.md) (how people use the app) and [entry points](../concepts/extensibility-points.md) (where people discover the app).</span></span>

### <a name="teams-doesnt-host-your-app"></a><span data-ttu-id="95fa2-119">Teams hosten Ihre App nicht</span><span class="sxs-lookup"><span data-stu-id="95fa2-119">Teams doesn't host your app</span></span>

<span data-ttu-id="95fa2-120">Eine Teams-App enthält die folgenden wichtigen Teile:</span><span class="sxs-lookup"><span data-stu-id="95fa2-120">A Teams app includes the following important pieces:</span></span>

* <span data-ttu-id="95fa2-121">Die Logik, Datenspeicherung und API-Aufrufe, die Ihre App unterstützen.</span><span class="sxs-lookup"><span data-stu-id="95fa2-121">The logic, data storage, and API calls that power your app.</span></span> <span data-ttu-id="95fa2-122">Diese Dienste werden nicht von Teams gehostet und müssen über HTTPS zugänglich sein.</span><span class="sxs-lookup"><span data-stu-id="95fa2-122">These services are not hosted by Teams and must be accessible via HTTPS.</span></span>
* <span data-ttu-id="95fa2-123">Der Teams-Client (Web, Desktop oder Mobil), auf dem Personen Ihre App verwenden.</span><span class="sxs-lookup"><span data-stu-id="95fa2-123">The Teams client (web, desktop, or mobile) where people use your app.</span></span>
* <span data-ttu-id="95fa2-124">Ihre App-ID, mit der Sie Ihre App mit App Studio konfigurieren können.</span><span class="sxs-lookup"><span data-stu-id="95fa2-124">Your app ID, which lets you configure your app with App Studio.</span></span>

## <a name="get-prerequisites"></a><span data-ttu-id="95fa2-125">Voraussetzungen erhalten</span><span class="sxs-lookup"><span data-stu-id="95fa2-125">Get prerequisites</span></span>

<span data-ttu-id="95fa2-126">Stellen Sie sicher, dass Sie über das richtige Konto zum Erstellen von Teams-Apps verfügen, und installieren Sie einige empfohlene Entwicklungstools.</span><span class="sxs-lookup"><span data-stu-id="95fa2-126">Verify you have the right account for building Teams apps and install some recommended development tools.</span></span>

### <a name="set-up-your-development-account"></a><span data-ttu-id="95fa2-127">Einrichten Ihres Entwicklungskontos</span><span class="sxs-lookup"><span data-stu-id="95fa2-127">Set up your development account</span></span>

<span data-ttu-id="95fa2-128">Sie benötigen ein Teams-Konto, das das Querladen benutzerdefinierter Apps ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="95fa2-128">You need a Teams account that allows custom app sideloading.</span></span> <span data-ttu-id="95fa2-129">(Ihr Konto stellt dies möglicherweise bereits zur Verfügung.)</span><span class="sxs-lookup"><span data-stu-id="95fa2-129">(Your account may already provide this.)</span></span>

1. <span data-ttu-id="95fa2-130">Wenn Sie über ein Teams-Konto verfügen, überprüfen Sie, ob Sie Apps in Teams querladen können:</span><span class="sxs-lookup"><span data-stu-id="95fa2-130">If you have a Teams account, verify if you can sideload apps in Teams:</span></span>
    1. <span data-ttu-id="95fa2-131">Wählen Sie im Teams-Client **Apps aus.**</span><span class="sxs-lookup"><span data-stu-id="95fa2-131">In the Teams client, select **Apps**.</span></span>
    1. <span data-ttu-id="95fa2-132">Suchen Sie nach einer Option zum **Hochladen einer benutzerdefinierten App.**</span><span class="sxs-lookup"><span data-stu-id="95fa2-132">Look for an option to **Upload a custom app**.</span></span>

    :::image type="content" source="../assets/images/build-your-first-app/upload-custom-app-closeup.png" alt-text="Abbildung, die zeigt, wo Sie in Teams eine benutzerdefinierte App hochladen können.":::

<!-- markdownlint-disable MD033 -->
<details>

<summary><span data-ttu-id="95fa2-134"><b>Wählen Sie hier</b> aus, wenn die Option zum Querladen nicht angezeigt wird oder sie kein Konto für Teams hat.</span><span class="sxs-lookup"><span data-stu-id="95fa2-134"><b>Select here</b> if you can't see the sideload option or don't have a Teams account.</span></span></summary>

<span data-ttu-id="95fa2-135">Sie können ein kostenloses Teams-Testkonto erhalten, das das Querladen von Apps ermöglicht, indem Sie am Microsoft 365-Entwicklerprogramm teilnehmen.</span><span class="sxs-lookup"><span data-stu-id="95fa2-135">You can get a free Teams test account that allows app sideloading by joining the Microsoft 365 developer program.</span></span> <span data-ttu-id="95fa2-136">(Der Registrierungsprozess dauert ca. zwei Minuten.)</span><span class="sxs-lookup"><span data-stu-id="95fa2-136">(The registration process takes approximately two minutes.)</span></span>

1. <span data-ttu-id="95fa2-137">Wechseln Sie zum [Microsoft 365-Entwicklerprogramm.](https://developer.microsoft.com/microsoft-365/dev-program)</span><span class="sxs-lookup"><span data-stu-id="95fa2-137">Go to the [Microsoft 365 developer program](https://developer.microsoft.com/microsoft-365/dev-program).</span></span>
1. <span data-ttu-id="95fa2-138">Wählen Sie **"Jetzt beitreten"** aus, und folgen Sie den Anweisungen auf dem Bildschirm.</span><span class="sxs-lookup"><span data-stu-id="95fa2-138">Select **Join Now** and follow the onscreen instructions.</span></span>
1. <span data-ttu-id="95fa2-139">Wenn Sie zum Willkommensbildschirm kommen, wählen **Sie "E5-Abonnement einrichten" aus.**</span><span class="sxs-lookup"><span data-stu-id="95fa2-139">When you get to the welcome screen, select **Set up E5 subscription**.</span></span>
1. <span data-ttu-id="95fa2-140">Richten Sie Ihr Administratorkonto ein.</span><span class="sxs-lookup"><span data-stu-id="95fa2-140">Set up your administrator account.</span></span> <span data-ttu-id="95fa2-141">Sobald Sie fertig sind, sollte ein Bildschirm wie dieser angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="95fa2-141">Once you finish, you should see a screen like this.</span></span>
:::image type="content" source="../assets/images/build-your-first-app/dev-program-subscription.png" alt-text="Beispiel für das, was nach der Anmeldung für das Microsoft 365-Entwicklerprogramm zu sehen ist.":::
1. <span data-ttu-id="95fa2-143">Melden Sie sich mit dem Administratorkonto, das Sie gerade eingerichtet haben, bei Teams an.</span><span class="sxs-lookup"><span data-stu-id="95fa2-143">Log in to Teams using the administrator account you just set up.</span></span>
1. <span data-ttu-id="95fa2-144">Überprüfen Sie, ob Sie jetzt über die **Option zum Hochladen einer benutzerdefinierten App** verfügen.</span><span class="sxs-lookup"><span data-stu-id="95fa2-144">Verify if you now have the **Upload a custom app** option.</span></span>

</details>

> [!Note]
> <span data-ttu-id="95fa2-145">Wenn Sie Apps weiterhin nicht querladen können, lesen Sie die Informationen zum Aktivieren von benutzerdefinierten Teams-Apps, und aktivieren Sie das Hochladen [benutzerdefinierter Apps.](https://docs.microsoft.com/microsoftteams/platform/concepts/build-and-test/prepare-your-o365-tenant#enable-custom-teams-apps-and-turn-on-custom-app-uploading)</span><span class="sxs-lookup"><span data-stu-id="95fa2-145">If you still can't sideload apps, see [enable custom Teams apps and turn on custom app uploading](https://docs.microsoft.com/microsoftteams/platform/concepts/build-and-test/prepare-your-o365-tenant#enable-custom-teams-apps-and-turn-on-custom-app-uploading).</span></span>

### <a name="install-your-development-tools"></a><span data-ttu-id="95fa2-146">Installieren der Entwicklungstools</span><span class="sxs-lookup"><span data-stu-id="95fa2-146">Install your development tools</span></span>

<span data-ttu-id="95fa2-147">Sie können Teams-Apps mit Ihren bevorzugten Tools erstellen, aber diese Lektionen zeigen, wie Sie schnell mit dem Microsoft Teams Toolkit for Visual Studio Code beginnen können.</span><span class="sxs-lookup"><span data-stu-id="95fa2-147">You can build Teams apps with your preferred tools, but these lessons show how you can get started quickly with the Microsoft Teams Toolkit for Visual Studio Code.</span></span>

<span data-ttu-id="95fa2-148">Teams zeigt den Inhalt von Apps nur über HTTPS-Verbindungen an.</span><span class="sxs-lookup"><span data-stu-id="95fa2-148">Teams displays app content only through HTTPS connections.</span></span> <span data-ttu-id="95fa2-149">Um bestimmte Arten von Apps lokal zu debuggen, z. B. einen Bot, erfahren Sie, wie Sie [ngrok](../concepts/build-and-test/debug.md#locally-hosted) zum Einrichten eines sicheren Tunnels zwischen Teams und Ihrer App verwenden.</span><span class="sxs-lookup"><span data-stu-id="95fa2-149">To debug certain types of apps locally, such as a bot, you'll learn how to use [ngrok to set up a secure tunnel](../concepts/build-and-test/debug.md#locally-hosted) between Teams and your app.</span></span> <span data-ttu-id="95fa2-150">(Produktions-Teams-Apps werden in der Cloud gehostet.)</span><span class="sxs-lookup"><span data-stu-id="95fa2-150">(Production Teams apps are hosted in the cloud.)</span></span>

1. <span data-ttu-id="95fa2-151">Installieren Sie [Node.js](https://nodejs.org/en/).</span><span class="sxs-lookup"><span data-stu-id="95fa2-151">Install [Node.js](https://nodejs.org/en/).</span></span>
1. <span data-ttu-id="95fa2-152">Installieren [Sie ngrok,](https://ngrok.com/download) wenn Sie planen, einen Bot oder eine Messagingerweiterung zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="95fa2-152">Install [ngrok](https://ngrok.com/download) if you plan to build a bot or messaging extension.</span></span>
1. <span data-ttu-id="95fa2-153">Installieren Sie die neueste Version von [Visual Studio Code](https://code.visualstudio.com/download).</span><span class="sxs-lookup"><span data-stu-id="95fa2-153">Install the latest version of [Visual Studio Code](https://code.visualstudio.com/download).</span></span> <span data-ttu-id="95fa2-154">(Frühere Versionen funktionieren möglicherweise nicht mit dem Toolkit.)</span><span class="sxs-lookup"><span data-stu-id="95fa2-154">(Earlier versions might not work with the toolkit.)</span></span>
1. Wählen Visual Studio Code auf  der linken Aktivitätsleiste Erweiterungen :::image type="icon" source="../assets/icons/vs-code-extensions.png"::: aus, und installieren Sie **das Microsoft Teams Toolkit.**

    :::image type="content" source="../assets/images/build-your-first-app/vsc-install-toolkit.png" alt-text="Illustration showing where in Visual Studio Code you can install the Microsoft Teams Toolkit extension.":::

## <a name="about-the-tutorials"></a><span data-ttu-id="95fa2-157">Informationen zu den Lernprogrammen</span><span class="sxs-lookup"><span data-stu-id="95fa2-157">About the tutorials</span></span>

<span data-ttu-id="95fa2-158">Sie können mit jedem der Teams beginnen, **Ihre ersten App-Lektionen zu** erstellen.</span><span class="sxs-lookup"><span data-stu-id="95fa2-158">You can start with any of the Teams **build your first app** lessons.</span></span> <span data-ttu-id="95fa2-159">Wenn Sie nicht sicher sind, wo Sie zuerst hingehen sollten, folgen Sie unserem anfängerfreundlichen Pfad, und erstellen Sie ein "Hello, World!"</span><span class="sxs-lookup"><span data-stu-id="95fa2-159">If you're not sure where to go first, follow our beginner friendly path and build a "Hello, World!"</span></span> <span data-ttu-id="95fa2-160">app.</span><span class="sxs-lookup"><span data-stu-id="95fa2-160">app.</span></span>

:::image type="content" source="../assets/images/build-your-first-app/skill-tree-overview.png" alt-text="Fertigkeitenstruktur mit Lernpfaden für die Lernprogramme zum Erstellen Ihrer ersten App in Teams." border="false":::

## <a name="next-step"></a><span data-ttu-id="95fa2-162">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="95fa2-162">Next step</span></span>

<span data-ttu-id="95fa2-163">Nachdem Sie Ihr Konto und Ihre Umgebung eingerichtet haben, können Sie mit der Einrichtung beginnen.</span><span class="sxs-lookup"><span data-stu-id="95fa2-163">Once you set up your account and environment, you can start building.</span></span>

### <a name="beginner-friendly-tutorial"></a><span data-ttu-id="95fa2-164">Lernprogramm für Anfänger</span><span class="sxs-lookup"><span data-stu-id="95fa2-164">Beginner friendly tutorial</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="95fa2-165">Erstellen einer "Hello, World!"-App</span><span class="sxs-lookup"><span data-stu-id="95fa2-165">Build a "Hello, World!" app</span></span>](../build-your-first-app/build-and-run.md)

### <a name="other-tutorials"></a><span data-ttu-id="95fa2-166">Weitere Lernprogramme</span><span class="sxs-lookup"><span data-stu-id="95fa2-166">Other tutorials</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="95fa2-167">Erstellen eines Bots</span><span class="sxs-lookup"><span data-stu-id="95fa2-167">Build a bot</span></span>](../build-your-first-app/build-bot.md)
> [!div class="nextstepaction"]
> [<span data-ttu-id="95fa2-168">Erstellen einer Messaging-Erweiterung</span><span class="sxs-lookup"><span data-stu-id="95fa2-168">Build a messaging extension</span></span>](../build-your-first-app/build-messaging-extension.md)
