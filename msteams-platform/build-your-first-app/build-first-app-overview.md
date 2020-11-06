---
title: Erste Schritte – Erstellen Ihrer ersten App-Übersicht und Voraussetzungen
author: heath-hamilton
description: Erfahren Sie, wie Sie mit der Microsoft Teams-App-Entwicklung beginnen und Ihre Umgebung einrichten.
ms.author: lajanuar
ms.date: 11/03/2020
ms.topic: quickstart
ms.openlocfilehash: 7fc3f7e9fd9d3c2a028999be53ba6bdcd5b3ba72
ms.sourcegitcommit: 99c35de7e2c604bd8bce392242c2c2fa709cd50b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/06/2020
ms.locfileid: "48931792"
---
# <a name="build-your-first-microsoft-teams-app-overview"></a><span data-ttu-id="bcf46-103">Erstellen Ihrer ersten Microsoft Teams-App-Übersicht</span><span class="sxs-lookup"><span data-stu-id="bcf46-103">Build your first Microsoft Teams app overview</span></span>

<span data-ttu-id="bcf46-104">In den **ersten App** -Lektionen erstellen Sie grundlegende Teams-apps.</span><span class="sxs-lookup"><span data-stu-id="bcf46-104">In the **build your first app** lessons, you create basic Teams apps.</span></span> <span data-ttu-id="bcf46-105">In jedem Lernprogramm wird erläutert, wie Sie eine einfache Real-World-Teams-app erstellen, während Sie allgemeine Tools, grundlegende Konzepte und erweiterte Funktionen einführen.</span><span class="sxs-lookup"><span data-stu-id="bcf46-105">Each tutorial walks through how to build a simple, real-world Teams app while introducing you to common tools, fundamental concepts, and more advanced features.</span></span>

## <a name="what-youll-learn"></a><span data-ttu-id="bcf46-106">Was Sie lernen</span><span class="sxs-lookup"><span data-stu-id="bcf46-106">What you'll learn</span></span>

<span data-ttu-id="bcf46-107">Hier ist eine Vorstellung davon, was Sie wissen, nachdem Sie die Lektionen durchlaufen haben.</span><span class="sxs-lookup"><span data-stu-id="bcf46-107">Here's an idea of what you'll know after going through the lessons.</span></span>

> [!div class="checklist"]
  >
  > * <span data-ttu-id="bcf46-108">Mit dem Microsoft Teams Toolkit für Visual Studio Code können Sie **schnell mit dem Team-Toolkit in Kontakt** treten, um ein App-Projekt und ein Gerüst zu erstellen, damit Sie in wenigen Minuten eine laufende APP haben.</span><span class="sxs-lookup"><span data-stu-id="bcf46-108">**Get up and running quickly with the Teams Toolkit** : The Microsoft Teams Toolkit for Visual Studio Code takes care of creating your app project and scaffolding so you can have a running app in minutes.</span></span>
  > * <span data-ttu-id="bcf46-109">**Konfigurieren Ihrer APP mit App Studio** : Geben Sie die Funktionen und Dienste an, die ihre Teams-App verwendet.</span><span class="sxs-lookup"><span data-stu-id="bcf46-109">**Configure your app with App Studio** : Specify the capabilities and services your Teams app uses.</span></span>
  > * <span data-ttu-id="bcf46-110">**Bereich der Benutzergruppe Ihrer APP** : Erstellen einer Teams-App für den persönlichen Gebrauch, die Zusammenarbeit oder beides.</span><span class="sxs-lookup"><span data-stu-id="bcf46-110">**Scope your app's audience** : Build a Teams app for personal use, collaboration, or both.</span></span>
  > * <span data-ttu-id="bcf46-111">**Erfahren Sie mehr über Microsoft Teams-Tools und SDKs** : passen Sie Ihre APP an (ändern Sie beispielsweise Ihr Farbschema so, dass Sie mit dem Microsoft Teams-Design übereinstimmt), und helfen Sie dem Microsoft Teams-JavaScript-SDK.</span><span class="sxs-lookup"><span data-stu-id="bcf46-111">**Get experience with Teams tools and SDKs** : Customize your app (for example, change its color scheme to match the Teams theme) with help from the Teams JavaScript SDK.</span></span> <span data-ttu-id="bcf46-112">Außerdem finden Sie Informationen zu allgemeinen Tools zum Erstellen und Verwalten von Bots.</span><span class="sxs-lookup"><span data-stu-id="bcf46-112">Also, learn about common tools for creating and managing bots.</span></span>
  > * <span data-ttu-id="bcf46-113">**Erweitern Sie Ihre APP** : in den Lektionen finden Sie Verwandte Themen, die Sie wahrscheinlich interessieren (beispielsweise Authentifizierungs-und Entwurfsrichtlinien).</span><span class="sxs-lookup"><span data-stu-id="bcf46-113">**Expand on your app** : Throughout the lessons, you'll find related topics you're probably interested in (such as authentication and design guidelines).</span></span>

## <a name="teams-app-fundamentals"></a><span data-ttu-id="bcf46-114">Grundlagen der Microsoft Teams-App</span><span class="sxs-lookup"><span data-stu-id="bcf46-114">Teams app fundamentals</span></span>

<span data-ttu-id="bcf46-115">Bevor Sie mit den Lernprogrammen beginnen, sollten Sie die folgenden Informationen zum Erstellen von Apps für Microsoft Teams kennen.</span><span class="sxs-lookup"><span data-stu-id="bcf46-115">Before you begin the tutorials, you should know the following about building apps for Teams.</span></span>

### <a name="apps-can-have-multiple-capabilities-and-entry-points"></a><span data-ttu-id="bcf46-116">Apps können über mehrere Funktionen und Einstiegspunkte verfügen.</span><span class="sxs-lookup"><span data-stu-id="bcf46-116">Apps can have multiple capabilities and entry points</span></span>

<span data-ttu-id="bcf46-117">Eine Teams-App besteht aus einer oder mehreren [Plattformfunktionen](../concepts/capabilities-overview.md) (wie die Benutzer die APP verwenden) und [Einstiegspunkten](../concepts/extensibility-points.md) (bei denen Personen die APP entdecken).</span><span class="sxs-lookup"><span data-stu-id="bcf46-117">A Teams app is made up of one or more [platform capabilities](../concepts/capabilities-overview.md) (how people use the app) and [entry points](../concepts/extensibility-points.md) (where people discover the app).</span></span>

### <a name="teams-doesnt-host-your-app"></a><span data-ttu-id="bcf46-118">Ihre APP wird von Microsoft Teams nicht gehostet.</span><span class="sxs-lookup"><span data-stu-id="bcf46-118">Teams doesn't host your app</span></span>

<span data-ttu-id="bcf46-119">Eine Teams-App umfasst die folgenden wichtigen Teile:</span><span class="sxs-lookup"><span data-stu-id="bcf46-119">A Teams app includes the following important pieces:</span></span>

* <span data-ttu-id="bcf46-120">Die Logik, Datenspeicherung und API-Aufrufe, mit denen Ihre APP versorgt wird.</span><span class="sxs-lookup"><span data-stu-id="bcf46-120">The logic, data storage, and API calls that power your app.</span></span> <span data-ttu-id="bcf46-121">Diese Dienste werden nicht von Microsoft Teams gehostet und müssen über HTTPS zugänglich sein.</span><span class="sxs-lookup"><span data-stu-id="bcf46-121">These services are not hosted by Teams and must be accessible via HTTPS.</span></span>
* <span data-ttu-id="bcf46-122">Der Microsoft Teams-Client ("Internet", "Desktop" oder "Mobil"), auf dem Benutzer Ihre APP verwenden.</span><span class="sxs-lookup"><span data-stu-id="bcf46-122">The Teams client (web, desktop, or mobile) where people use your app.</span></span>
* <span data-ttu-id="bcf46-123">Ihre APP-ID, mit der Sie Ihre APP mit App Studio konfigurieren können.</span><span class="sxs-lookup"><span data-stu-id="bcf46-123">Your app ID, which lets you configure your app with App Studio.</span></span>

## <a name="get-prerequisites"></a><span data-ttu-id="bcf46-124">Abrufen von Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="bcf46-124">Get prerequisites</span></span>

<span data-ttu-id="bcf46-125">Stellen Sie sicher, dass Sie das richtige Konto für die Erstellung von Teams-apps haben, und installieren Sie einige empfohlene Entwicklungstools.</span><span class="sxs-lookup"><span data-stu-id="bcf46-125">Verify you have the right account for building Teams apps and install some recommended development tools.</span></span>

### <a name="set-up-your-development-account"></a><span data-ttu-id="bcf46-126">Einrichten Ihres entwicklungskontos</span><span class="sxs-lookup"><span data-stu-id="bcf46-126">Set up your development account</span></span>

<span data-ttu-id="bcf46-127">Sie benötigen ein Teams-Konto, das benutzerdefinierte App-Sideloading zulässt.</span><span class="sxs-lookup"><span data-stu-id="bcf46-127">You need a Teams account that allows custom app sideloading.</span></span> <span data-ttu-id="bcf46-128">(Dies wird möglicherweise bereits von Ihrem Konto bereitgestellt.)</span><span class="sxs-lookup"><span data-stu-id="bcf46-128">(Your account may already provide this.)</span></span>

1. <span data-ttu-id="bcf46-129">Wenn Sie über ein Teams-Konto verfügen, überprüfen Sie, ob Sie apps in Microsoft Teams querladen können:</span><span class="sxs-lookup"><span data-stu-id="bcf46-129">If you have a Teams account, verify if you can sideload apps in Teams:</span></span>
    1. <span data-ttu-id="bcf46-130">Wählen Sie im Microsoft Teams-Client **apps** aus.</span><span class="sxs-lookup"><span data-stu-id="bcf46-130">In the Teams client, select **Apps**.</span></span>
    1. <span data-ttu-id="bcf46-131">Suchen Sie nach einer Option zum **Hochladen einer benutzerdefinierten App**.</span><span class="sxs-lookup"><span data-stu-id="bcf46-131">Look for an option to **Upload a custom app**.</span></span>

    :::image type="content" source="../assets/images/build-your-first-app/upload-custom-app-closeup.png" alt-text="Abbildung zeigt, wo in Microsoft Teams eine benutzerdefinierte App hochgeladen werden kann.":::

<!-- markdownlint-disable MD033 -->
<details>

<summary><span data-ttu-id="bcf46-133"><b>Wählen Sie hier aus</b> , wenn die querladen-Option nicht angezeigt wird oder kein Teams-Konto vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="bcf46-133"><b>Select here</b> if you can't see the sideload option or don't have a Teams account.</span></span></summary>

<span data-ttu-id="bcf46-134">Sie können ein kostenloses Test Konto für Teams erhalten, das App-Sideloading ermöglicht, indem Sie dem Microsoft 365-Entwicklerprogramm beitreten.</span><span class="sxs-lookup"><span data-stu-id="bcf46-134">You can get a free Teams test account that allows app sideloading by joining the Microsoft 365 developer program.</span></span> <span data-ttu-id="bcf46-135">(Der Registrierungsvorgang dauert ungefähr zwei Minuten.)</span><span class="sxs-lookup"><span data-stu-id="bcf46-135">(The registration process takes approximately two minutes.)</span></span>

1. <span data-ttu-id="bcf46-136">Wechseln Sie zum [Microsoft 365-Entwicklerprogramm](https://developer.microsoft.com/microsoft-365/dev-program).</span><span class="sxs-lookup"><span data-stu-id="bcf46-136">Go to the [Microsoft 365 developer program](https://developer.microsoft.com/microsoft-365/dev-program).</span></span>
1. <span data-ttu-id="bcf46-137">Wählen Sie **jetzt beitreten** aus, und folgen Sie den Anweisungen auf dem Bildschirm.</span><span class="sxs-lookup"><span data-stu-id="bcf46-137">Select **Join Now** and follow the onscreen instructions.</span></span>
1. <span data-ttu-id="bcf46-138">Wenn Sie zum Begrüßungsbildschirm gelangen, wählen Sie **E5-Abonnement einrichten** aus.</span><span class="sxs-lookup"><span data-stu-id="bcf46-138">When you get to the welcome screen, select **Set up E5 subscription**.</span></span>
1. <span data-ttu-id="bcf46-139">Richten Sie Ihr Administratorkonto ein.</span><span class="sxs-lookup"><span data-stu-id="bcf46-139">Set up your administrator account.</span></span> <span data-ttu-id="bcf46-140">Wenn Sie fertig sind, sollten Sie einen Bildschirm wie den folgenden sehen.</span><span class="sxs-lookup"><span data-stu-id="bcf46-140">Once you finish, you should see a screen like this.</span></span>
:::image type="content" source="../assets/images/build-your-first-app/dev-program-subscription.png" alt-text="Beispiel dessen, was nach der Anmeldung für das Microsoft 365-Entwicklerprogramm angezeigt wird.":::
1. <span data-ttu-id="bcf46-142">Melden Sie sich mit dem soeben eingerichteten Administratorkonto bei Microsoft Teams an.</span><span class="sxs-lookup"><span data-stu-id="bcf46-142">Log in to Teams using the administrator account you just set up.</span></span>
1. <span data-ttu-id="bcf46-143">Überprüfen Sie, ob Sie nun die Option **benutzerdefinierte App hochladen** haben.</span><span class="sxs-lookup"><span data-stu-id="bcf46-143">Verify if you now have the **Upload a custom app** option.</span></span>

</details>

### <a name="install-your-development-tools"></a><span data-ttu-id="bcf46-144">Installieren der Entwicklungstools</span><span class="sxs-lookup"><span data-stu-id="bcf46-144">Install your development tools</span></span>

<span data-ttu-id="bcf46-145">Sie können Teams-apps mit Ihren bevorzugten Tools erstellen, doch in diesen Lektionen wird gezeigt, wie Sie mit dem Microsoft Teams-Toolkit für Visual Studio-Code schnell loslegen können.</span><span class="sxs-lookup"><span data-stu-id="bcf46-145">You can build Teams apps with your preferred tools, but these lessons show how you can get started quickly with the Microsoft Teams Toolkit for Visual Studio Code.</span></span>

<span data-ttu-id="bcf46-146">Microsoft Teams zeigt App-Inhalte nur über HTTPS-Verbindungen an.</span><span class="sxs-lookup"><span data-stu-id="bcf46-146">Teams displays app content only through HTTPS connections.</span></span> <span data-ttu-id="bcf46-147">Um bestimmte Arten von apps lokal zu debuggen, beispielsweise einen bot, erfahren Sie, wie Sie [ngrok verwenden, um einen sicheren Tunnel](../concepts/build-and-test/debug.md#locally-hosted) zwischen Teams und ihrer App einzurichten.</span><span class="sxs-lookup"><span data-stu-id="bcf46-147">To debug certain types of apps locally, such as a bot, you'll learn how to use [ngrok to set up a secure tunnel](../concepts/build-and-test/debug.md#locally-hosted) between Teams and your app.</span></span> <span data-ttu-id="bcf46-148">(Produktions Teams-apps werden in der Cloud gehostet.)</span><span class="sxs-lookup"><span data-stu-id="bcf46-148">(Production Teams apps are hosted in the cloud.)</span></span>

1. <span data-ttu-id="bcf46-149">Installieren Sie [Node.js](https://nodejs.org/en/).</span><span class="sxs-lookup"><span data-stu-id="bcf46-149">Install [Node.js](https://nodejs.org/en/).</span></span>
1. <span data-ttu-id="bcf46-150">Installieren Sie [ngrok](https://ngrok.com/download) , wenn Sie eine bot-oder Messaging-Erweiterung erstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="bcf46-150">Install [ngrok](https://ngrok.com/download) if you plan to build a bot or messaging extension.</span></span>
1. <span data-ttu-id="bcf46-151">Installieren Sie die neueste Version von [Visual Studio-Code](https://code.visualstudio.com/download).</span><span class="sxs-lookup"><span data-stu-id="bcf46-151">Install the latest version of [Visual Studio Code](https://code.visualstudio.com/download).</span></span> <span data-ttu-id="bcf46-152">(Frühere Versionen funktionieren möglicherweise nicht mit dem Toolkit.)</span><span class="sxs-lookup"><span data-stu-id="bcf46-152">(Earlier versions might not work with the toolkit.)</span></span>
1. Wählen Sie in Visual Studio Code in der linken Aktivitäts Leiste die Option **Extensions** aus, :::image type="icon" source="../assets/icons/vs-code-extensions.png"::: und installieren Sie das **Microsoft Teams-Toolkit**.

    :::image type="content" source="../assets/images/build-your-first-app/vsc-install-toolkit.png" alt-text="Abbildung zeigt, wo in Visual Studio Code Sie die Microsoft Teams Toolkit-Erweiterung installieren können.":::

## <a name="about-the-tutorials"></a><span data-ttu-id="bcf46-155">Informationen zu den Lernprogrammen</span><span class="sxs-lookup"><span data-stu-id="bcf46-155">About the tutorials</span></span>

<span data-ttu-id="bcf46-156">Sie können mit einem der Teams beginnen, **Ihre ersten App** -Lektionen zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="bcf46-156">You can start with any of the Teams **build your first app** lessons.</span></span> <span data-ttu-id="bcf46-157">Wenn Sie sich nicht sicher sind, wo Sie zuerst suchen, begeben Sie sich auf unseren anfängerfreundlichen Pfad und erstellen Sie ein "Hello, World!".</span><span class="sxs-lookup"><span data-stu-id="bcf46-157">If you're not sure where to go first, follow our beginner friendly path and build a "Hello, World!"</span></span> <span data-ttu-id="bcf46-158">App.</span><span class="sxs-lookup"><span data-stu-id="bcf46-158">app.</span></span>

:::image type="content" source="../assets/images/build-your-first-app/skill-tree-overview.png" alt-text="Skill Tree mit Lernpfaden für die Lernprogramme zum Erstellen Ihrer ersten app." border="false":::

## <a name="next-step"></a><span data-ttu-id="bcf46-160">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="bcf46-160">Next step</span></span>

<span data-ttu-id="bcf46-161">Nachdem Sie Ihr Konto und Ihre Umgebung eingerichtet haben, können Sie mit dem Erstellen beginnen.</span><span class="sxs-lookup"><span data-stu-id="bcf46-161">Once you set up your account and environment, you can start building.</span></span>

### <a name="beginner-friendly-tutorial"></a><span data-ttu-id="bcf46-162">Anfänger freundliches Tutorial</span><span class="sxs-lookup"><span data-stu-id="bcf46-162">Beginner friendly tutorial</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="bcf46-163">Erstellen einer "Hello, World!"-App</span><span class="sxs-lookup"><span data-stu-id="bcf46-163">Build a "Hello, World!" app</span></span>](../build-your-first-app/build-and-run.md)

### <a name="other-tutorials"></a><span data-ttu-id="bcf46-164">Andere Lernprogramme</span><span class="sxs-lookup"><span data-stu-id="bcf46-164">Other tutorials</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="bcf46-165">Erstellen eines Bots</span><span class="sxs-lookup"><span data-stu-id="bcf46-165">Build a bot</span></span>](../build-your-first-app/build-bot.md)
> [!div class="nextstepaction"]
> [<span data-ttu-id="bcf46-166">Erstellen einer Messaging-Erweiterung</span><span class="sxs-lookup"><span data-stu-id="bcf46-166">Build a messaging extension</span></span>](../build-your-first-app/build-messaging-extension.md)
