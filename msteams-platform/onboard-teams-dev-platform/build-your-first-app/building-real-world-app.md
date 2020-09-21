---
title: Erste Schritte beim Erstellen Ihrer ersten Teams-App
author: heath-hamilton
ms.author: lajanuar
description: Übersicht und Voraussetzungen für die Erstellung Ihrer ersten Microsoft Teams-App
ms.openlocfilehash: 9392096a285a43d3a1f8bed5020e3464da0f7f18
ms.sourcegitcommit: d3bb4bbcdff9545c9869647dcdbe563a2db868be
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/18/2020
ms.locfileid: "47964703"
---
# <a name="get-started-building-your-first-teams-app"></a><span data-ttu-id="2f8aa-103">Erste Schritte beim Erstellen Ihrer ersten Teams-App</span><span class="sxs-lookup"><span data-stu-id="2f8aa-103">Get started building your first Teams app</span></span>

<span data-ttu-id="2f8aa-104">In den **ersten App** -Lektionen erstellen Sie grundlegende Teams-apps.</span><span class="sxs-lookup"><span data-stu-id="2f8aa-104">In the **build your first app** lessons, you create basic Teams apps.</span></span> <span data-ttu-id="2f8aa-105">In jedem Lernprogramm wird erläutert, wie Sie eine einfache Real-World-Teams-app erstellen, während Sie allgemeine Tools, grundlegende Konzepte und einige erweiterte Funktionen einführen.</span><span class="sxs-lookup"><span data-stu-id="2f8aa-105">Each tutorial walks through how to build a simple, real-world Teams app while introducing you to common tools, fundamental concepts, and some more advanced features.</span></span>

## <a name="what-youll-learn"></a><span data-ttu-id="2f8aa-106">Was Sie lernen</span><span class="sxs-lookup"><span data-stu-id="2f8aa-106">What you'll learn</span></span>

<span data-ttu-id="2f8aa-107">Hier ist eine Vorstellung davon, was Sie wissen, nachdem Sie die Lektionen durchlaufen haben.</span><span class="sxs-lookup"><span data-stu-id="2f8aa-107">Here's an idea of what you'll know after going through the lessons.</span></span>

> [!div class="checklist"]
  >
  > * <span data-ttu-id="2f8aa-108">Mit dem Microsoft Teams Toolkit für Visual Studio Code können Sie **schnell mit dem Team-Toolkit in Kontakt**treten, um ein App-Projekt und ein Gerüst zu erstellen, damit Sie in wenigen Minuten eine laufende APP haben.</span><span class="sxs-lookup"><span data-stu-id="2f8aa-108">**Get up and running quickly with the Teams Toolkit**: The Microsoft Teams Toolkit for Visual Studio Code takes care of creating your app project and scaffolding so you can have a running app in minutes.</span></span>
  > * <span data-ttu-id="2f8aa-109">**Definieren Sie Ihre APP mit dem Manifest**: im App-Manifest geben Sie die Funktionen und Dienste an, die ihre Teams-App verwendet.</span><span class="sxs-lookup"><span data-stu-id="2f8aa-109">**Define your app with the manifest**: The app manifest is where you specify the capabilities and services your Teams app uses.</span></span>
  > * <span data-ttu-id="2f8aa-110">**Bereich der Benutzergruppe Ihrer APP**: Erstellen einer Teams-App für den persönlichen Gebrauch, die Zusammenarbeit oder beides.</span><span class="sxs-lookup"><span data-stu-id="2f8aa-110">**Scope your app's audience**: Build a Teams app for personal use, collaboration, or both.</span></span>
  > * <span data-ttu-id="2f8aa-111">**Holen Sie sich Erfahrung mit Frameworks**: passen Sie Ihre APP an (ändern Sie beispielsweise Ihr Farbschema entsprechend dem Teams-Design) mit Hilfe des Teams-JavaScript-SDK.</span><span class="sxs-lookup"><span data-stu-id="2f8aa-111">**Get experience with frameworks**: Customize your app (for example, change its color scheme to match the Teams theme) with help from the Teams JavaScript SDK.</span></span> <span data-ttu-id="2f8aa-112">Außerdem finden Sie Informationen zu allgemeinen Tools zum Erstellen und Verwalten von Bots.</span><span class="sxs-lookup"><span data-stu-id="2f8aa-112">Also, learn about common tools for creating and managing bots.</span></span>
  > * <span data-ttu-id="2f8aa-113">**Erweitern Sie Ihre APP**: in den Lektionen finden Sie Verwandte Themen, die Sie wahrscheinlich interessieren (beispielsweise Authentifizierungs-und Entwurfsrichtlinien).</span><span class="sxs-lookup"><span data-stu-id="2f8aa-113">**Expand on your app**: Throughout the lessons, you'll find related topics you're probably interested in (such as authentication and design guidelines).</span></span>

## <a name="teams-app-fundamentals"></a><span data-ttu-id="2f8aa-114">Grundlagen der Microsoft Teams-App</span><span class="sxs-lookup"><span data-stu-id="2f8aa-114">Teams app fundamentals</span></span>

<span data-ttu-id="2f8aa-115">Bevor Sie mit den Lernprogrammen beginnen, sollten Sie die folgenden Informationen zum Erstellen von Apps für Microsoft Teams kennen.</span><span class="sxs-lookup"><span data-stu-id="2f8aa-115">Before you begin the tutorials, you should know the following about building apps for Teams.</span></span>

### <a name="apps-can-have-multiple-capabilities"></a><span data-ttu-id="2f8aa-116">Apps können mehrere Funktionen haben</span><span class="sxs-lookup"><span data-stu-id="2f8aa-116">Apps can have multiple capabilities</span></span>

<span data-ttu-id="2f8aa-117">Microsoft Teams-apps bestehen aus einer oder mehreren [Plattformfunktionen](../capabilities-overview.md).</span><span class="sxs-lookup"><span data-stu-id="2f8aa-117">Teams apps are made up of one or more [platform capabilities](../capabilities-overview.md).</span></span> <span data-ttu-id="2f8aa-118">Sie können diese Funktionen mithilfe einer Reihe von Teams-spezifischen [UI-Komponenten und Konventionen](../doc-links/teams-ui-conventions.md)anzeigen, beispielsweise Karten und Aufgaben Module.</span><span class="sxs-lookup"><span data-stu-id="2f8aa-118">You can display these capabilities using a number of Teams-specific [UI components and conventions](../doc-links/teams-ui-conventions.md), such as cards and task modules.</span></span>

### <a name="teams-doesnt-host-your-app"></a><span data-ttu-id="2f8aa-119">Ihre APP wird von Microsoft Teams nicht gehostet.</span><span class="sxs-lookup"><span data-stu-id="2f8aa-119">Teams doesn't host your app</span></span>

<span data-ttu-id="2f8aa-120">Eine Teams-App umfasst drei wichtige Teile:</span><span class="sxs-lookup"><span data-stu-id="2f8aa-120">A Teams app includes three important pieces:</span></span>

* <span data-ttu-id="2f8aa-121">Die Logik, Datenspeicherung und API-Aufrufe, mit denen Ihre APP versorgt wird.</span><span class="sxs-lookup"><span data-stu-id="2f8aa-121">The logic, data storage, and API calls that power your app.</span></span> <span data-ttu-id="2f8aa-122">Diese Dienste werden nicht von Microsoft Teams gehostet und müssen über HTTPS zugänglich sein.</span><span class="sxs-lookup"><span data-stu-id="2f8aa-122">These services are not hosted by Teams and must be accessible via HTTPS.</span></span>
* <span data-ttu-id="2f8aa-123">Der Microsoft Teams-Client ("Internet", "Desktop" oder "Mobil"), auf dem Benutzer Ihre APP verwenden.</span><span class="sxs-lookup"><span data-stu-id="2f8aa-123">The Teams client (web, desktop, or mobile) where people use your app.</span></span>
* <span data-ttu-id="2f8aa-124">Ihr App-Paket, mit dem Sie die app in Microsoft Teams installieren.</span><span class="sxs-lookup"><span data-stu-id="2f8aa-124">Your app package, which you use to install the app in Teams.</span></span> <span data-ttu-id="2f8aa-125">Sie enthält App-Metadaten und Zeiger auf Ihre gehosteten Dienste.</span><span class="sxs-lookup"><span data-stu-id="2f8aa-125">It contains app metadata and pointers to your hosted services.</span></span>

## <a name="get-prerequisites"></a><span data-ttu-id="2f8aa-126">Abrufen von Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="2f8aa-126">Get prerequisites</span></span>

<span data-ttu-id="2f8aa-127">Stellen Sie sicher, dass Sie das richtige Konto für die Erstellung von Teams-apps haben, und installieren Sie einige empfohlene Entwicklungstools.</span><span class="sxs-lookup"><span data-stu-id="2f8aa-127">Verify you have the right account for building Teams apps and install some recommended development tools.</span></span>

### <a name="set-up-your-development-account"></a><span data-ttu-id="2f8aa-128">Einrichten Ihres entwicklungskontos</span><span class="sxs-lookup"><span data-stu-id="2f8aa-128">Set up your development account</span></span>

<span data-ttu-id="2f8aa-129">Sie benötigen ein Teams-Konto, das benutzerdefinierte App-Sideloading zulässt.</span><span class="sxs-lookup"><span data-stu-id="2f8aa-129">You need a Teams account that allows custom app sideloading.</span></span> <span data-ttu-id="2f8aa-130">(Dies wird möglicherweise bereits von Ihrem Konto bereitgestellt.)</span><span class="sxs-lookup"><span data-stu-id="2f8aa-130">(Your account may already provide this.)</span></span>

1. <span data-ttu-id="2f8aa-131">Wenn Sie über ein Teams-Konto verfügen, überprüfen Sie, ob Sie apps in Microsoft Teams querladen können:</span><span class="sxs-lookup"><span data-stu-id="2f8aa-131">If you have a Teams account, verify if you can sideload apps in Teams:</span></span>
    1. <span data-ttu-id="2f8aa-132">Wählen Sie im Microsoft Teams-Client **apps**aus.</span><span class="sxs-lookup"><span data-stu-id="2f8aa-132">In the Teams client, select **Apps**.</span></span>
    1. <span data-ttu-id="2f8aa-133">Suchen Sie nach einer Option zum **Hochladen einer benutzerdefinierten App**.</span><span class="sxs-lookup"><span data-stu-id="2f8aa-133">Look for an option to **Upload a custom app**.</span></span>

    :::image type="content" source="../doc-links/images/upload-custom-app-closeup.png" alt-text="querladen-Option (Ansicht)":::

<!-- markdownlint-disable MD033 -->
<details>

<summary><span data-ttu-id="2f8aa-135"><b>Wählen Sie hier aus</b> , wenn die querladen-Option nicht angezeigt wird oder kein Teams-Konto vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="2f8aa-135"><b>Select here</b> if you can't see the sideload option or don't have a Teams account.</span></span></summary>

<span data-ttu-id="2f8aa-136">Sie können ein kostenloses Test Konto für Teams erhalten, das App-Sideloading ermöglicht, indem Sie dem Microsoft 365-Entwicklerprogramm beitreten.</span><span class="sxs-lookup"><span data-stu-id="2f8aa-136">You can get a free Teams test account that allows app sideloading by joining the Microsoft 365 developer program.</span></span> <span data-ttu-id="2f8aa-137">(Der Registrierungsvorgang dauert ungefähr zwei Minuten.)</span><span class="sxs-lookup"><span data-stu-id="2f8aa-137">(The registration process takes approximately two minutes.)</span></span>

1. <span data-ttu-id="2f8aa-138">Wechseln Sie zum [Microsoft 365-Entwicklerprogramm](https://developer.microsoft.com/microsoft-365/dev-program).</span><span class="sxs-lookup"><span data-stu-id="2f8aa-138">Go to the [Microsoft 365 developer program](https://developer.microsoft.com/microsoft-365/dev-program).</span></span>
1. <span data-ttu-id="2f8aa-139">Wählen Sie **jetzt beitreten** aus, und folgen Sie den Anweisungen auf dem Bildschirm.</span><span class="sxs-lookup"><span data-stu-id="2f8aa-139">Select **Join Now** and follow the onscreen instructions.</span></span>
1. <span data-ttu-id="2f8aa-140">Wenn Sie zum Begrüßungsbildschirm gelangen, wählen Sie **E5-Abonnement einrichten**aus.</span><span class="sxs-lookup"><span data-stu-id="2f8aa-140">When you get to the welcome screen, select **Set up E5 subscription**.</span></span>
1. <span data-ttu-id="2f8aa-141">Richten Sie Ihr Administratorkonto ein.</span><span class="sxs-lookup"><span data-stu-id="2f8aa-141">Set up your administrator account.</span></span> <span data-ttu-id="2f8aa-142">Wenn Sie fertig sind, sollten Sie einen Bildschirm wie den folgenden sehen.</span><span class="sxs-lookup"><span data-stu-id="2f8aa-142">Once you finish, you should see a screen like this.</span></span>
:::image type="content" source="../doc-links/images/dev-program-subscription.png" alt-text="Entwicklerprogramm-Abonnement Ansicht":::
1. <span data-ttu-id="2f8aa-144">Melden Sie sich mit dem soeben eingerichteten Administratorkonto bei Microsoft Teams an.</span><span class="sxs-lookup"><span data-stu-id="2f8aa-144">Log in to Teams using the administrator account you just set up.</span></span>
1. <span data-ttu-id="2f8aa-145">Überprüfen Sie, ob Sie nun die Option **benutzerdefinierte App hochladen** haben.</span><span class="sxs-lookup"><span data-stu-id="2f8aa-145">Verify if you now have the **Upload a custom app** option.</span></span>

</details>

### <a name="install-your-development-tools"></a><span data-ttu-id="2f8aa-146">Installieren der Entwicklungstools</span><span class="sxs-lookup"><span data-stu-id="2f8aa-146">Install your development tools</span></span>

<span data-ttu-id="2f8aa-147">Sie können Teams-apps mit Ihren bevorzugten Tools erstellen, doch in diesen Lektionen wird gezeigt, wie Sie mit dem Microsoft Teams-Toolkit für Visual Studio-Code schnell loslegen können.</span><span class="sxs-lookup"><span data-stu-id="2f8aa-147">You can build Teams apps with your preferred tools, but these lessons show how you can get started quickly with the Microsoft Teams Toolkit for Visual Studio Code.</span></span>

<span data-ttu-id="2f8aa-148">Microsoft Teams zeigt App-Inhalte nur über HTTPS-Verbindungen an.</span><span class="sxs-lookup"><span data-stu-id="2f8aa-148">Teams displays app content only through HTTPS connections.</span></span> <span data-ttu-id="2f8aa-149">Da Sie die erste APP lokal hosten, erfahren Sie, wie Sie mithilfe von [ngrok einen sicheren Tunnel](../doc-links/debug.md#locally-hosted) zwischen Teams und ihrer App einrichten.</span><span class="sxs-lookup"><span data-stu-id="2f8aa-149">Since you'll host your first app locally, you'll learn how to use [ngrok to set up a secure tunnel](../doc-links/debug.md#locally-hosted) between Teams and your app.</span></span>

1. <span data-ttu-id="2f8aa-150">Installieren Sie [Node.js](https://nodejs.org/en/).</span><span class="sxs-lookup"><span data-stu-id="2f8aa-150">Install [Node.js](https://nodejs.org/en/).</span></span>
1. <span data-ttu-id="2f8aa-151">Installieren Sie die neueste Version von [Visual Studio-Code](https://code.visualstudio.com/download).</span><span class="sxs-lookup"><span data-stu-id="2f8aa-151">Install the latest version of [Visual Studio Code](https://code.visualstudio.com/download).</span></span> <span data-ttu-id="2f8aa-152">(Frühere Versionen funktionieren möglicherweise nicht mit dem Toolkit.)</span><span class="sxs-lookup"><span data-stu-id="2f8aa-152">(Earlier versions might not work with the toolkit.)</span></span>
1. Wählen Sie in Visual Studio Code in der linken Aktivitäts Leiste die Option **Extensions** aus, :::image type="icon" source="../doc-links/images/vs-code-extensions.png"::: und installieren Sie das **Microsoft Teams-Toolkit**.
    :::image type="content" source="../doc-links/images/vsc-install-toolkit.png" alt-text="Installieren der Toolkit-Ansicht":::
1. <span data-ttu-id="2f8aa-155">Installieren Sie [ngrok](https://ngrok.com/download).</span><span class="sxs-lookup"><span data-stu-id="2f8aa-155">Install [ngrok](https://ngrok.com/download).</span></span>

## <a name="next-step"></a><span data-ttu-id="2f8aa-156">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="2f8aa-156">Next step</span></span>

<span data-ttu-id="2f8aa-157">Nachdem Sie Ihr Konto und Ihre Umgebung eingerichtet haben, können Sie mit dem Erstellen beginnen.</span><span class="sxs-lookup"><span data-stu-id="2f8aa-157">Once you set up your account and environment, you can start building.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2f8aa-158">Erstellen und Ausführen ihrer ersten App</span><span class="sxs-lookup"><span data-stu-id="2f8aa-158">Build and run your first app</span></span>](../build-your-first-app/build-and-run.md)
