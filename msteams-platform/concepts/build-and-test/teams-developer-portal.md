---
title: Verwalten Ihrer Apps mit dem Entwicklerportal
description: Erfahren Sie, wie Sie Ihre Apps mithilfe des Entwicklerportals für Microsoft Teams verwalten.
keywords: Erste Schritte für Entwicklerportal-Teams
localization_priority: Normal
ms.topic: overview
ms.author: surbhigupta
ms.openlocfilehash: 6dca8723248441c3cf672931295b4b68e02cc24c
ms.sourcegitcommit: 9f499908437655d6ebdc6c4b3c3603ee220315b7
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/15/2021
ms.locfileid: "52949686"
---
# <a name="manage-your-apps-with-the-developer-portal-for-microsoft-teams"></a><span data-ttu-id="84d24-104">Verwalten Ihrer Apps mit dem Entwicklerportal für Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="84d24-104">Manage your apps with the Developer Portal for Microsoft Teams</span></span>

> [!NOTE]
> <span data-ttu-id="84d24-105">Das Entwicklerportal für Teams befindet sich derzeit in der [öffentlichen Entwicklervorschau.](~/resources/dev-preview/developer-preview-intro.md)</span><span class="sxs-lookup"><span data-stu-id="84d24-105">The Developer Portal for Teams is currently in [public developer preview](~/resources/dev-preview/developer-preview-intro.md).</span></span>

<span data-ttu-id="84d24-106">Das <a href="https://dev.teams.microsoft.com" target="_blank">Entwicklerportal für Teams</a> ist das primäre Tool zum Konfigurieren, Verteilen und Verwalten Ihrer Microsoft Teams-Apps.</span><span class="sxs-lookup"><span data-stu-id="84d24-106">The <a href="https://dev.teams.microsoft.com" target="_blank">Developer Portal for Teams</a> is the primary tool for configuring, distributing, and managing your Microsoft Teams apps.</span></span> <span data-ttu-id="84d24-107">Mit dem Entwicklerportal können Sie mit Kollegen an Ihrer App zusammenarbeiten, Laufzeitumgebungen einrichten und vieles mehr.</span><span class="sxs-lookup"><span data-stu-id="84d24-107">With the Developer Portal, you can collaborate with colleagues on your app, set up runtime environments, and much more.</span></span>

:::image type="content" source="../../assets/images/tdp/tdp_home_1.png" alt-text="Screenshot der Startseite des Entwicklerportals für Teams.":::

## <a name="register-an-app"></a><span data-ttu-id="84d24-109">Registrieren einer App</span><span class="sxs-lookup"><span data-stu-id="84d24-109">Register an app</span></span>

<span data-ttu-id="84d24-110">Das Entwicklerportal bietet verschiedene Möglichkeiten zum Registrieren einer Teams-App:</span><span class="sxs-lookup"><span data-stu-id="84d24-110">The Developer Portal provides a couple ways to register a Teams app:</span></span>

* <span data-ttu-id="84d24-111">Registrieren einer völlig neuen App</span><span class="sxs-lookup"><span data-stu-id="84d24-111">Register a brand new app</span></span>
* <span data-ttu-id="84d24-112">Importieren eines vorhandenen App-Pakets</span><span class="sxs-lookup"><span data-stu-id="84d24-112">Import an existing app package</span></span>

> [!NOTE]
> <span data-ttu-id="84d24-113">Wenn Sie eine App mit dem [Microsoft Teams-Toolkit für Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension)erstellen, können Sie diese App im Entwicklerportal verwalten.</span><span class="sxs-lookup"><span data-stu-id="84d24-113">If you create an app using the [Microsoft Teams Toolkit for Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension), you can manage that app in the Developer Portal.</span></span>

## <a name="set-up-an-environment"></a><span data-ttu-id="84d24-114">Einrichten einer Umgebung</span><span class="sxs-lookup"><span data-stu-id="84d24-114">Set up an environment</span></span>

<span data-ttu-id="84d24-115">Sie können Umgebungen und globale Variablen konfigurieren, um den Übergang Ihrer App von Ihrer lokalen Laufzeit zur Produktion zu unterstützen.</span><span class="sxs-lookup"><span data-stu-id="84d24-115">You can configure environments and global variables to help transition your app from your local runtime to production.</span></span> <span data-ttu-id="84d24-116">Globale Variablen werden in allen Umgebungen verwendet.</span><span class="sxs-lookup"><span data-stu-id="84d24-116">Global variables are used across all environments.</span></span>

<span data-ttu-id="84d24-117">**So richten Sie eine Umgebung ein**</span><span class="sxs-lookup"><span data-stu-id="84d24-117">**To set up an environment**</span></span>

1. <span data-ttu-id="84d24-118">Wählen Sie im Entwicklerportal die App aus, an der Sie arbeiten.</span><span class="sxs-lookup"><span data-stu-id="84d24-118">In the Developer Portal, select the app you're working on.</span></span>
2. <span data-ttu-id="84d24-119">Wechseln Sie zur Seite **"Umgebungen",** und wählen Sie **+Umgebung hinzufügen** aus.</span><span class="sxs-lookup"><span data-stu-id="84d24-119">Go to the **Environments** page and select **+ Add an environment**.</span></span>
3. <span data-ttu-id="84d24-120">Wählen Sie **+ Fügen Sie eine Variable** hinzu, um Konfigurationsvariablen für Ihre Umgebung zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="84d24-120">Select **+ Add a variable** to create configuration variables for your environment.</span></span>

<span data-ttu-id="84d24-121">**So verwenden Sie Variablen**</span><span class="sxs-lookup"><span data-stu-id="84d24-121">**To use variables**</span></span>

<span data-ttu-id="84d24-122">Verwenden Sie die Variablennamen anstelle von hartcodierten Werten, um Ihre App-Konfigurationen festzulegen.</span><span class="sxs-lookup"><span data-stu-id="84d24-122">Use the variable names instead of hard-coded values to set your app configurations.</span></span>

1. <span data-ttu-id="84d24-123">Geben Sie `{{` in ein beliebiges Feld im Entwicklerportal ein.</span><span class="sxs-lookup"><span data-stu-id="84d24-123">Enter `{{` in any field in the Developer Portal.</span></span> <span data-ttu-id="84d24-124">Es wird eine Dropdownliste mit allen Variablen angezeigt, die Sie für die ausgewählte Umgebung zusammen mit den globalen Variablen erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="84d24-124">A dropdown with all the variables you've created for the chosen environment along with the global variables appears.</span></span>  
1. <span data-ttu-id="84d24-125">Wählen Sie vor dem Herunterladen Ihres App-Pakets (z. B. wenn Sie sich auf die Veröffentlichung im Teams Store vorbereiten) die Umgebung aus, die Sie verwenden möchten.</span><span class="sxs-lookup"><span data-stu-id="84d24-125">Before downloading your app package (for example, when getting ready to publish to the Teams store), select the environment you want to use.</span></span> <span data-ttu-id="84d24-126">Ihre App-Konfigurationen werden basierend auf der Umgebung automatisch aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="84d24-126">Your app configurations update automatically based on the environment.</span></span> 

## <a name="identify-app-owners"></a><span data-ttu-id="84d24-127">Identifizieren von App-Besitzern</span><span class="sxs-lookup"><span data-stu-id="84d24-127">Identify app owners</span></span>

<span data-ttu-id="84d24-128">Jede App enthält eine **Besitzerseite,** auf der Sie Ihre App-Registrierung für Kollegen in Ihrer Organisation freigeben können. Die **Rolle "Mitwirkender"** verfügt über die gleichen Berechtigungen wie die **Besitzerrolle,** mit Ausnahme der Möglichkeit, eine App zu löschen.</span><span class="sxs-lookup"><span data-stu-id="84d24-128">Each app includes an **Owners** page, where you can share your app registration with colleagues in your org. The **Contributor** role has the same permissions as the **Owner** role except the ability to delete an app.</span></span>

## <a name="configure-your-apps-capabilities-and-other-important-metadata"></a><span data-ttu-id="84d24-129">Konfigurieren der Funktionen Ihrer App und anderer wichtiger Metadaten</span><span class="sxs-lookup"><span data-stu-id="84d24-129">Configure your app's capabilities and other important metadata</span></span>

<span data-ttu-id="84d24-130">Eine Teams-App ist eine Web-App.</span><span class="sxs-lookup"><span data-stu-id="84d24-130">A Teams app is a web app.</span></span> <span data-ttu-id="84d24-131">Wie alle Web-Apps wird der Quellcode in der Regel in einer IDE oder einem Code-Editor entwickelt und an einer beliebigen Stelle in der Cloud (z. B. Azure) gehostet.</span><span class="sxs-lookup"><span data-stu-id="84d24-131">Like all web apps, its source code is typically developed in an IDE or code editor and hosted somewhere in the cloud (like Azure).</span></span>

<span data-ttu-id="84d24-132">Um Ihre App in Teams zu installieren und zu rendern, müssen Sie eine Reihe von Konfigurationen einschließen, die Teams erkennt.</span><span class="sxs-lookup"><span data-stu-id="84d24-132">To install and render your app in Teams, you must include a set of configurations that Teams recognizes.</span></span> <span data-ttu-id="84d24-133">Dies geschieht traditionell durch das Erstellen eines App-Manifests, einer JSON-Datei, die alle Metadaten enthält, die Teams zum Anzeigen Ihrer App-Inhalte benötigt.</span><span class="sxs-lookup"><span data-stu-id="84d24-133">This has traditionally been done by crafting an app manifest, a JSON file that contains all the metadata Teams needs to display your app content.</span></span> <span data-ttu-id="84d24-134">Das Entwicklerportal abstrahiert diesen Prozess und enthält neue Features und Tools, die Ihnen helfen, erfolgreicher zu sein.</span><span class="sxs-lookup"><span data-stu-id="84d24-134">The Developer Portal abstracts this process and includes new features and tooling to help you be more successful.</span></span>

## <a name="test-your-app-directly-in-teams"></a><span data-ttu-id="84d24-135">Testen Ihrer App direkt in Teams</span><span class="sxs-lookup"><span data-stu-id="84d24-135">Test your app directly in Teams</span></span>

<span data-ttu-id="84d24-136">Das Entwicklerportal bietet Optionen zum Testen und Debuggen Ihrer App:</span><span class="sxs-lookup"><span data-stu-id="84d24-136">The Developer Portal provides options for testing and debugging your app:</span></span>

* <span data-ttu-id="84d24-137">Auf der **Übersichtsseite** sehen Sie eine Momentaufnahme, ob die Konfigurationen Ihrer App anhand von Teams Store-Testfällen überprüft werden.</span><span class="sxs-lookup"><span data-stu-id="84d24-137">On the **Overview** page, you can see a snapshot of whether your app's configurations validate against Teams store test cases.</span></span>
* <span data-ttu-id="84d24-138">Mit der Schaltfläche **"Vorschau in Teams"** können Sie Ihre App schnell im Teams-Client zum Debuggen starten.</span><span class="sxs-lookup"><span data-stu-id="84d24-138">The **Preview in Teams** button lets you launch your app quickly in the Teams client for debugging.</span></span>

## <a name="distribute-your-app"></a><span data-ttu-id="84d24-139">Verteilen Ihrer App</span><span class="sxs-lookup"><span data-stu-id="84d24-139">Distribute your app</span></span>

<span data-ttu-id="84d24-140">Verwenden Sie im Entwicklerportal die Schaltfläche **"Verteilen",** um ein App-Paket herunterzuladen, es in Ihrer Organisation zu veröffentlichen oder im Teams Store zu veröffentlichen.</span><span class="sxs-lookup"><span data-stu-id="84d24-140">From the Developer Portal, use the **Distribute** button to download an app package, publish to your org, or publish to the Teams store.</span></span>

<span data-ttu-id="84d24-141">Weitere Informationen finden Sie unter [Verteilen Ihrer Teams-App.](~/concepts/deploy-and-publish/apps-publish-overview.md)</span><span class="sxs-lookup"><span data-stu-id="84d24-141">For more information, see [distribute your Teams app](~/concepts/deploy-and-publish/apps-publish-overview.md).</span></span>

## <a name="analyze-your-apps-usage"></a><span data-ttu-id="84d24-142">Analysieren der Nutzung Ihrer App</span><span class="sxs-lookup"><span data-stu-id="84d24-142">Analyze your app's usage</span></span>

<span data-ttu-id="84d24-143">Auf der **Übersichtsseite** sehen Sie die Gesamtzahl der aktiven Benutzer für Ihre App.</span><span class="sxs-lookup"><span data-stu-id="84d24-143">On the **Overview** page, you can see the total number of active users for your app.</span></span> <span data-ttu-id="84d24-144">Diese Metriken sind für Apps verfügbar, die im Teams Store oder im App-Katalog einer Organisation über das Entwicklerportal veröffentlicht und auf die App-ID beschränkt sind.</span><span class="sxs-lookup"><span data-stu-id="84d24-144">These metrics are available for apps published to the Teams store or an org's app catalog through Developer Portal and scoped to the app ID.</span></span>

| <span data-ttu-id="84d24-145">Metrik</span><span class="sxs-lookup"><span data-stu-id="84d24-145">Metric</span></span> | <span data-ttu-id="84d24-146">Definition</span><span class="sxs-lookup"><span data-stu-id="84d24-146">Definition</span></span> |
| :-----------------------| :------------------------------------------------------------------------------------------------------|
| <span data-ttu-id="84d24-147">*Monatlich R30*</span><span class="sxs-lookup"><span data-stu-id="84d24-147">*Monthly R30*</span></span> | <span data-ttu-id="84d24-148">Die Standardverwendungsmetrik.</span><span class="sxs-lookup"><span data-stu-id="84d24-148">The default usage metric.</span></span> <span data-ttu-id="84d24-149">Sie zeigt die Anzahl der eindeutigen aktiven Benutzer an, die Ihre App innerhalb dieses rollenden 30-Tage-Fensters in UTC verwendet haben.</span><span class="sxs-lookup"><span data-stu-id="84d24-149">It shows you the count of unique active users that used your app within that rolling 30-day window in UTC.</span></span> |
| <span data-ttu-id="84d24-150">*Täglich*</span><span class="sxs-lookup"><span data-stu-id="84d24-150">*Daily*</span></span> | <span data-ttu-id="84d24-151">Zeigt die Anzahl der eindeutigen aktiven Benutzer an, die Ihre App an einem bestimmten Tag in UTC verwendet haben.</span><span class="sxs-lookup"><span data-stu-id="84d24-151">Shows you the count of unique active users that used your app in a given day in UTC.</span></span> |

<span data-ttu-id="84d24-152">Die monatliche und tägliche Nutzung wird für die letzten sieben, 30 und 60 Tage angezeigt.</span><span class="sxs-lookup"><span data-stu-id="84d24-152">Monthly and daily usage is shown for the past seven, 30 days, and 60 days.</span></span> <span data-ttu-id="84d24-153">Die Nutzung sollte innerhalb von 24 bis 48 Stunden für einen bestimmten Tag widergespiegelt werden.</span><span class="sxs-lookup"><span data-stu-id="84d24-153">You should see usage reflected for a given day within 24-48 hours.</span></span> <span data-ttu-id="84d24-154">Die Anzeige neuer Apps kann bis zu 3 bis 5 Tage dauern.</span><span class="sxs-lookup"><span data-stu-id="84d24-154">Usage for new apps can take up to 3-5 days to display.</span></span>

## <a name="use-tools-to-create-app-features"></a><span data-ttu-id="84d24-155">Verwenden von Tools zum Erstellen von App-Features</span><span class="sxs-lookup"><span data-stu-id="84d24-155">Use tools to create app features</span></span>

<span data-ttu-id="84d24-156">Das Entwicklerportal enthält auch Tools, mit denen Sie einige wichtige Features von Teams-Apps erstellen können.</span><span class="sxs-lookup"><span data-stu-id="84d24-156">The Developer Portal also includes tools to help you build some key features of Teams apps.</span></span> <span data-ttu-id="84d24-157">Einige dieser Tools umfassen:</span><span class="sxs-lookup"><span data-stu-id="84d24-157">Some of these tools include:</span></span>

* <span data-ttu-id="84d24-158">**Szenenstudio:** Entwerfen [sie benutzerdefinierte Szenen für den Gemeinsamen Modus](~/apps-in-teams-meetings/teams-together-mode.md) für Teams-Besprechungen.</span><span class="sxs-lookup"><span data-stu-id="84d24-158">**Scene studio**: Design [custom Together Mode scenes](~/apps-in-teams-meetings/teams-together-mode.md) for Teams meetings.</span></span>
* <span data-ttu-id="84d24-159">**Editor für adaptive Karten:** Erstellen und Anzeigen einer Vorschau adaptiver Karten, die in Ihre Apps aufgenommen werden sollen.</span><span class="sxs-lookup"><span data-stu-id="84d24-159">**Adaptive Cards editor**: Create and preview Adaptive Cards to include with your apps.</span></span>
* <span data-ttu-id="84d24-160">**Microsoft Identity Platform Management:** Registrieren Sie Ihre Apps bei Azure Active Directory (Azure AD), um Benutzern zu helfen, sich anzumelden und Zugriff auf APIs zu gewähren.</span><span class="sxs-lookup"><span data-stu-id="84d24-160">**Microsoft identity platform management**: Register your apps with Azure Active Directory (Azure AD) to help users sign in and provide access to APIs.</span></span>
