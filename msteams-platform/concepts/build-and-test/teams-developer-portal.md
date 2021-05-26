---
title: Verwalten Ihrer Apps mit dem Entwicklerportal
description: Erfahren Sie, wie Sie Ihre Apps mithilfe des Entwicklerportals für Microsoft Teams.
keywords: Erste Schritte für Entwicklerportalteams
localization_priority: Normal
ms.topic: overview
ms.author: surbhigupta
ms.openlocfilehash: 5f3335470a442fc8a3c94e9563e21fea75c4ef4b
ms.sourcegitcommit: c55b0d2a4c1f8945e49b0b7c0b08c0eb3da3d2be
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/25/2021
ms.locfileid: "52646333"
---
# <a name="manage-your-apps-with-the-developer-portal-for-microsoft-teams"></a><span data-ttu-id="38a8c-104">Verwalten Sie Ihre Apps mit dem Entwicklerportal für Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="38a8c-104">Manage your apps with the Developer Portal for Microsoft Teams</span></span>

> [!NOTE]
> <span data-ttu-id="38a8c-105">Das Entwicklerportal für Teams befindet sich derzeit in [der öffentlichen Entwicklervorschau](~/resources/dev-preview/developer-preview-intro.md).</span><span class="sxs-lookup"><span data-stu-id="38a8c-105">The Developer Portal for Teams is currently in [public developer preview](~/resources/dev-preview/developer-preview-intro.md).</span></span>

<span data-ttu-id="38a8c-106">Das Entwicklerportal für Teams ist das primäre Tool zum Konfigurieren, Verteilen und Verwalten Microsoft Teams Apps.</span><span class="sxs-lookup"><span data-stu-id="38a8c-106">The Developer Portal for Teams is the primary tool for configuring, distributing, and managing your Microsoft Teams apps.</span></span> <span data-ttu-id="38a8c-107">Mit dem Entwicklerportal können Sie mit Kollegen in Ihrer App zusammenarbeiten, Laufzeitumgebungen einrichten und vieles mehr.</span><span class="sxs-lookup"><span data-stu-id="38a8c-107">With the Developer Portal, you can collaborate with colleagues on your app, set up runtime environments, and much more.</span></span>

:::image type="content" source="../../assets/images/tdp/tdp_home_1.png" alt-text="Screenshot der Startseite des Entwicklerportals für Teams.":::

## <a name="register-an-app"></a><span data-ttu-id="38a8c-109">Registrieren einer App</span><span class="sxs-lookup"><span data-stu-id="38a8c-109">Register an app</span></span>

<span data-ttu-id="38a8c-110">Das Entwicklerportal bietet mehrere Möglichkeiten zum Registrieren einer Teams App:</span><span class="sxs-lookup"><span data-stu-id="38a8c-110">The Developer Portal provides a couple ways to register a Teams app:</span></span>

* <span data-ttu-id="38a8c-111">Registrieren einer brandneuen App</span><span class="sxs-lookup"><span data-stu-id="38a8c-111">Register a brand new app</span></span>
* <span data-ttu-id="38a8c-112">Importieren eines vorhandenen App-Pakets</span><span class="sxs-lookup"><span data-stu-id="38a8c-112">Import an existing app package</span></span>

> [!NOTE]
> <span data-ttu-id="38a8c-113">Wenn Sie eine App mit dem [Microsoft Teams Toolkit für](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension)Visual Studio Code erstellen, können Sie diese App im Entwicklerportal verwalten.</span><span class="sxs-lookup"><span data-stu-id="38a8c-113">If you create an app using the [Microsoft Teams Toolkit for Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension), you can manage that app in the Developer Portal.</span></span>

## <a name="set-up-an-environment"></a><span data-ttu-id="38a8c-114">Einrichten einer Umgebung</span><span class="sxs-lookup"><span data-stu-id="38a8c-114">Set up an environment</span></span>

<span data-ttu-id="38a8c-115">Sie können Umgebungen und globale Variablen konfigurieren, um die Umstellung Ihrer App von ihrer lokalen Laufzeit auf die Produktion zu erleichtern.</span><span class="sxs-lookup"><span data-stu-id="38a8c-115">You can configure environments and global variables to help transition your app from your local runtime to production.</span></span> <span data-ttu-id="38a8c-116">Globale Variablen werden in allen Umgebungen verwendet.</span><span class="sxs-lookup"><span data-stu-id="38a8c-116">Global variables are used across all environments.</span></span>

<span data-ttu-id="38a8c-117">**So richten Sie eine Umgebung ein**</span><span class="sxs-lookup"><span data-stu-id="38a8c-117">**To set up an environment**</span></span>

1. <span data-ttu-id="38a8c-118">Wählen Sie im Entwicklerportal die App aus, an der Sie arbeiten.</span><span class="sxs-lookup"><span data-stu-id="38a8c-118">In the Developer Portal, select the app you're working on.</span></span>
2. <span data-ttu-id="38a8c-119">Wechseln Sie zur **Seite Umgebungen,** und wählen **Sie + Umgebung hinzufügen aus.**</span><span class="sxs-lookup"><span data-stu-id="38a8c-119">Go to the **Environments** page and select **+ Add an environment**.</span></span>
3. <span data-ttu-id="38a8c-120">Wählen **Sie + Variable hinzufügen aus,** um Konfigurationsvariablen für Ihre Umgebung zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="38a8c-120">Select **+ Add a variable** to create configuration variables for your environment.</span></span>

<span data-ttu-id="38a8c-121">**So verwenden Sie Variablen**</span><span class="sxs-lookup"><span data-stu-id="38a8c-121">**To use variables**</span></span>

<span data-ttu-id="38a8c-122">Verwenden Sie die Variablennamen anstelle von hart codierten Werten, um Ihre App-Konfigurationen zu konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="38a8c-122">Use the variable names instead of hard-coded values to set your app configurations.</span></span>

1. <span data-ttu-id="38a8c-123">Geben `{{` Sie in ein beliebiges Feld im Entwicklerportal ein.</span><span class="sxs-lookup"><span data-stu-id="38a8c-123">Enter `{{` in any field in the Developer Portal.</span></span> <span data-ttu-id="38a8c-124">Es wird ein Dropdown mit allen Variablen angezeigt, die Sie für die ausgewählte Umgebung zusammen mit den globalen Variablen erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="38a8c-124">A dropdown with all the variables you've created for the chosen environment along with the global variables appears.</span></span>  
1. <span data-ttu-id="38a8c-125">Wählen Sie vor dem Herunterladen Ihres App-Pakets (z. B. wenn Sie bereit sind, im Teams zu veröffentlichen), die Umgebung aus, die Sie verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="38a8c-125">Before downloading your app package (for example, when getting ready to publish to the Teams store), select the environment you want to use.</span></span> <span data-ttu-id="38a8c-126">Ihre App-Konfigurationen werden automatisch basierend auf der Umgebung aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="38a8c-126">Your app configurations update automatically based on the environment.</span></span> 

## <a name="identify-app-owners"></a><span data-ttu-id="38a8c-127">Identifizieren von App-Besitzern</span><span class="sxs-lookup"><span data-stu-id="38a8c-127">Identify app owners</span></span>

<span data-ttu-id="38a8c-128">Jede App enthält eine **Besitzerseite,** auf der Sie Ihre App-Registrierung mit Kollegen in Ihrer Organisation teilen können. Die  Mitwirkenderolle verfügt über dieselben Berechtigungen wie die **Besitzerrolle,** mit Ausnahme der Möglichkeit, eine App zu löschen.</span><span class="sxs-lookup"><span data-stu-id="38a8c-128">Each app includes an **Owners** page, where you can share your app registration with colleagues in your org. The **Contributor** role has the same permissions as the **Owner** role except the ability to delete an app.</span></span>

## <a name="configure-your-apps-capabilities-and-other-important-metadata"></a><span data-ttu-id="38a8c-129">Konfigurieren der Funktionen Ihrer App und anderer wichtiger Metadaten</span><span class="sxs-lookup"><span data-stu-id="38a8c-129">Configure your app's capabilities and other important metadata</span></span>

<span data-ttu-id="38a8c-130">Eine Teams ist eine Web-App.</span><span class="sxs-lookup"><span data-stu-id="38a8c-130">A Teams app is a web app.</span></span> <span data-ttu-id="38a8c-131">Wie alle Web-Apps wird der Quellcode in der Regel in einer IDE oder einem Code-Editor entwickelt und irgendwo in der Cloud gehostet (z. B. Azure).</span><span class="sxs-lookup"><span data-stu-id="38a8c-131">Like all web apps, its source code is typically developed in an IDE or code editor and hosted somewhere in the cloud (like Azure).</span></span>

<span data-ttu-id="38a8c-132">Zum Installieren und Rendern Ihrer App in Teams müssen Sie eine Reihe von Konfigurationen enthalten, die Teams erkennen.</span><span class="sxs-lookup"><span data-stu-id="38a8c-132">To install and render your app in Teams, you must include a set of configurations that Teams recognizes.</span></span> <span data-ttu-id="38a8c-133">Dies wurde traditionell durch das Erstellen eines App-Manifests durchgeführt, einer JSON-Datei, die alle Metadaten enthält, Teams Ihre App-Inhalte anzeigen müssen.</span><span class="sxs-lookup"><span data-stu-id="38a8c-133">This has traditionally been done by crafting an app manifest, a JSON file that contains all the metadata Teams needs to display your app content.</span></span> <span data-ttu-id="38a8c-134">Das Entwicklerportal abstrahiert diesen Prozess und enthält neue Features und Tools, die Ihnen helfen, erfolgreicher zu sein.</span><span class="sxs-lookup"><span data-stu-id="38a8c-134">The Developer Portal abstracts this process and includes new features and tooling to help you be more successful.</span></span>

## <a name="test-your-app-directly-in-teams"></a><span data-ttu-id="38a8c-135">Testen Sie Ihre App direkt in Teams</span><span class="sxs-lookup"><span data-stu-id="38a8c-135">Test your app directly in Teams</span></span>

<span data-ttu-id="38a8c-136">Das Entwicklerportal bietet Optionen zum Testen und Debuggen Ihrer App:</span><span class="sxs-lookup"><span data-stu-id="38a8c-136">The Developer Portal provides options for testing and debugging your app:</span></span>

* <span data-ttu-id="38a8c-137">Auf der **Seite Übersicht** sehen Sie eine Momentaufnahme, ob die Konfigurationen Ihrer App anhand Teams Testfälle überprüft werden.</span><span class="sxs-lookup"><span data-stu-id="38a8c-137">On the **Overview** page, you can see a snapshot of whether your app's configurations validate against Teams store test cases.</span></span>
* <span data-ttu-id="38a8c-138">Mit **der Schaltfläche Vorschau in Teams** können Sie Ihre App schnell im Teams Debuggen starten.</span><span class="sxs-lookup"><span data-stu-id="38a8c-138">The **Preview in Teams** button lets you launch your app quickly in the Teams client for debugging.</span></span>

## <a name="distribute-your-app"></a><span data-ttu-id="38a8c-139">Verteilen Ihrer App</span><span class="sxs-lookup"><span data-stu-id="38a8c-139">Distribute your app</span></span>

<span data-ttu-id="38a8c-140">Verwenden Sie im Entwicklerportal die Schaltfläche Verteilen, um ein App-Paket herunterzuladen, in Ihrer Organisation zu veröffentlichen oder im Teams veröffentlichen. </span><span class="sxs-lookup"><span data-stu-id="38a8c-140">From the Developer Portal, use the **Distribute** button to download an app package, publish to your org, or publish to the Teams store.</span></span>

<span data-ttu-id="38a8c-141">Weitere Informationen finden Sie unter [Verteilen ihrer Teams App.](~/concepts/deploy-and-publish/apps-publish-overview.md)</span><span class="sxs-lookup"><span data-stu-id="38a8c-141">For more information, see [distribute your Teams app](~/concepts/deploy-and-publish/apps-publish-overview.md).</span></span>

## <a name="analyze-your-apps-usage"></a><span data-ttu-id="38a8c-142">Analysieren der Nutzung Ihrer App</span><span class="sxs-lookup"><span data-stu-id="38a8c-142">Analyze your app's usage</span></span>

<span data-ttu-id="38a8c-143">Auf der **Seite Übersicht** sehen Sie die Gesamtzahl der aktiven Benutzer für Ihre App.</span><span class="sxs-lookup"><span data-stu-id="38a8c-143">On the **Overview** page, you can see the total number of active users for your app.</span></span> <span data-ttu-id="38a8c-144">Diese Metriken sind für Apps verfügbar, die im Teams store oder im App-Katalog einer Organisation über das Entwicklerportal veröffentlicht und auf die App-ID begrenzt sind.</span><span class="sxs-lookup"><span data-stu-id="38a8c-144">These metrics are available for apps published to the Teams store or an org's app catalog through Developer Portal and scoped to the app ID.</span></span>

| <span data-ttu-id="38a8c-145">Metrik</span><span class="sxs-lookup"><span data-stu-id="38a8c-145">Metric</span></span> | <span data-ttu-id="38a8c-146">Definition</span><span class="sxs-lookup"><span data-stu-id="38a8c-146">Definition</span></span> |
| :-----------------------| :------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="38a8c-147">*Monatlicher R30*</span><span class="sxs-lookup"><span data-stu-id="38a8c-147">*Monthly R30*</span></span> | <span data-ttu-id="38a8c-148">Die Standardverwendungsmetrik.</span><span class="sxs-lookup"><span data-stu-id="38a8c-148">The default usage metric.</span></span> <span data-ttu-id="38a8c-149">Es zeigt die Anzahl der eindeutigen aktiven Benutzer an, die Ihre App innerhalb dieses rollenden 30-Tage-Fensters in UTC verwendet haben.</span><span class="sxs-lookup"><span data-stu-id="38a8c-149">It shows you the count of unique active users that used your app within that rolling 30-day window in UTC.</span></span> |
| <span data-ttu-id="38a8c-150">*Täglich*</span><span class="sxs-lookup"><span data-stu-id="38a8c-150">*Daily*</span></span> | <span data-ttu-id="38a8c-151">Zeigt die Anzahl der eindeutigen aktiven Benutzer an, die Ihre App an einem bestimmten Tag in UTC verwendet haben.</span><span class="sxs-lookup"><span data-stu-id="38a8c-151">Shows you the count of unique active users that used your app in a given day in UTC.</span></span> |

<span data-ttu-id="38a8c-152">Die monatliche und tägliche Nutzung wird für die letzten sieben, 30 Tage und 60 Tage angezeigt.</span><span class="sxs-lookup"><span data-stu-id="38a8c-152">Monthly and daily usage is shown for the past seven, 30 days, and 60 days.</span></span> <span data-ttu-id="38a8c-153">Die Verwendung sollte für einen bestimmten Tag innerhalb von 24-48 Stunden widergespiegelt werden.</span><span class="sxs-lookup"><span data-stu-id="38a8c-153">You should see usage reflected for a given day within 24-48 hours.</span></span> <span data-ttu-id="38a8c-154">Die Verwendung für neue Apps kann bis zu 3-5 Tage dauern.</span><span class="sxs-lookup"><span data-stu-id="38a8c-154">Usage for new apps can take up to 3-5 days to display.</span></span>

## <a name="use-tools-to-create-app-features"></a><span data-ttu-id="38a8c-155">Verwenden von Tools zum Erstellen von App-Features</span><span class="sxs-lookup"><span data-stu-id="38a8c-155">Use tools to create app features</span></span>

<span data-ttu-id="38a8c-156">Das Entwicklerportal enthält auch Tools, mit deren Hilfe Sie einige wichtige Features von Teams erstellen können.</span><span class="sxs-lookup"><span data-stu-id="38a8c-156">The Developer Portal also includes tools to help you build some key features of Teams apps.</span></span> <span data-ttu-id="38a8c-157">Zu diesen Tools gehören:</span><span class="sxs-lookup"><span data-stu-id="38a8c-157">Some of these tools include:</span></span>

* <span data-ttu-id="38a8c-158">**Szenenstudio:** Entwerfen sie benutzerdefinierte Szenen im gemeinsamen Modus für Teams Besprechungen.</span><span class="sxs-lookup"><span data-stu-id="38a8c-158">**Scene studio**: Design custom Together mode scenes for Teams meetings.</span></span>
* <span data-ttu-id="38a8c-159">**Editor für adaptive** Karten: Erstellen und Anzeigen einer Vorschau adaptiver Karten, die in Ihre Apps mit einpassen.</span><span class="sxs-lookup"><span data-stu-id="38a8c-159">**Adaptive Cards editor**: Create and preview Adaptive Cards to include with your apps.</span></span>
* <span data-ttu-id="38a8c-160">**Microsoft Identity Platform:** Registrieren Sie Ihre Apps bei Azure Active Directory (Azure AD), um Benutzern bei der Anmeldung und dem Zugriff auf APIs zu helfen.</span><span class="sxs-lookup"><span data-stu-id="38a8c-160">**Microsoft identity platform management**: Register your apps with Azure Active Directory (Azure AD) to help users sign in and provide access to APIs.</span></span>
