---
title: Erste Schritte – Erstellen und Ausführen Ihrer ersten App
author: girliemac
description: Erstellen Sie schnell Microsoft Teams App, die ein "Hello, World!" anzeigt. message using the Microsoft Teams Toolkit.
ms.author: timura
ms.date: 03/22/2021
ms.topic: quickstart
ms.openlocfilehash: 6c3d215a3f2c1aa89a9a2bf28aad081d98c6dc33
ms.sourcegitcommit: 25c9ad27f99682caaa7347840578b118c63b8f69
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2021
ms.locfileid: "52101723"
---
# <a name="create-your-first-microsoft-teams-app"></a><span data-ttu-id="c45b8-104">Erstellen Ihrer ersten Microsoft Teams App</span><span class="sxs-lookup"><span data-stu-id="c45b8-104">Create your first Microsoft Teams app</span></span>

<span data-ttu-id="c45b8-105">Dieser Schnellstart vermittelt Ihnen das Erstellen und Ausführen Microsoft Teams App, die "Hello, World!" anzeigt.</span><span class="sxs-lookup"><span data-stu-id="c45b8-105">This quickstart teaches you to build and run Microsoft Teams app that displays "Hello, World!"</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c45b8-106">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="c45b8-106">Prerequisites</span></span>

<span data-ttu-id="c45b8-107">Bevor Sie beginnen, müssen Sie Ihren mandanten [Teams einrichten](#set-up-your-teams-development-tenant) und ihre Teams [installieren.](#install-your-development-tools)</span><span class="sxs-lookup"><span data-stu-id="c45b8-107">Before you begin, you need to [set up your Teams development tenant](#set-up-your-teams-development-tenant) and [install your Teams development tools](#install-your-development-tools).</span></span>

### <a name="set-up-your-teams-development-tenant"></a><span data-ttu-id="c45b8-108">Einrichten ihres Teams-Entwicklungs-Mandanten</span><span class="sxs-lookup"><span data-stu-id="c45b8-108">Set up your Teams development tenant</span></span>

<span data-ttu-id="c45b8-109">Ein **Mandant** ist wie ein Container für eine Organisation.</span><span class="sxs-lookup"><span data-stu-id="c45b8-109">A **tenant** is like a container for an organization.</span></span> <span data-ttu-id="c45b8-110">In Teams ist ein Mandant der Ort, an dem Personen aus dieser Organisation chatten, Dateien freigeben und Besprechungen ausführen.</span><span class="sxs-lookup"><span data-stu-id="c45b8-110">In Teams terms, a tenant is where people from that org chat, share files, and run meetings.</span></span> <span data-ttu-id="c45b8-111">Als Entwickler benötigen Sie einen Mandanten zum Querladen und Testen der Teams, die Sie erstellen.</span><span class="sxs-lookup"><span data-stu-id="c45b8-111">As a developer, you need a tenant to sideload and test the Teams apps that you are building.</span></span>  

# <a name="do-not-have-a-tenant"></a>[<span data-ttu-id="c45b8-112">Kein Mandant</span><span class="sxs-lookup"><span data-stu-id="c45b8-112">Do not have a tenant</span></span>](#tab/do-not-have-a-tenant)

<span data-ttu-id="c45b8-113">Sie können ein kostenloses Teams, das einen Mandanten enthält, der das Querladen von Apps zulässt, indem Sie am Microsoft 365 teilnehmen.</span><span class="sxs-lookup"><span data-stu-id="c45b8-113">You can get a free Teams test account, which includes a tenant that allows app sideloading, by joining the Microsoft 365 developer program.</span></span> <span data-ttu-id="c45b8-114">Der Registrierungsprozess dauert ca. zwei Minuten.</span><span class="sxs-lookup"><span data-stu-id="c45b8-114">The registration process takes approximately two minutes.</span></span>

<span data-ttu-id="c45b8-115">**So erhalten Sie einen Mandanten**</span><span class="sxs-lookup"><span data-stu-id="c45b8-115">**To get a tenant**</span></span>

1. <span data-ttu-id="c45b8-116">Wechseln Sie zum [Microsoft 365 Entwicklerprogramm](https://developer.microsoft.com/microsoft-365/dev-program).</span><span class="sxs-lookup"><span data-stu-id="c45b8-116">Go to the [Microsoft 365 developer program](https://developer.microsoft.com/microsoft-365/dev-program).</span></span>
1. <span data-ttu-id="c45b8-117">Wählen **Sie Jetzt beitreten** aus, und folgen Sie den Anweisungen auf dem Bildschirm.</span><span class="sxs-lookup"><span data-stu-id="c45b8-117">Select **Join Now** and follow the onscreen instructions.</span></span>
1. <span data-ttu-id="c45b8-118">Wählen Sie auf dem Bildschirm Willkommen die Option **E5-Abonnement einrichten aus.**</span><span class="sxs-lookup"><span data-stu-id="c45b8-118">In the Welcome screen, select **Set up E5 subscription**.</span></span>
1. <span data-ttu-id="c45b8-119">Richten Sie Ihr Microsoft 365 Entwicklerkonto ein.</span><span class="sxs-lookup"><span data-stu-id="c45b8-119">Set up your Microsoft 365 developer account.</span></span> 
   <span data-ttu-id="c45b8-120">Nachdem Sie fertig sind, wird der folgende Bildschirm angezeigt:</span><span class="sxs-lookup"><span data-stu-id="c45b8-120">After you finish, the following screen appears:</span></span>

   :::image type="content" source="../assets/images/build-your-first-app/dev-program-subscription.png" alt-text="Beispiel für das, was Sie nach der Anmeldung für das Microsoft 365 sehen.":::

1. <span data-ttu-id="c45b8-122">Melden Sie sich bei Teams mit Ihrem neuen Konto an.</span><span class="sxs-lookup"><span data-stu-id="c45b8-122">Sign in to Teams with your new account.</span></span>
1. <span data-ttu-id="c45b8-123">Wählen Sie im Teams Die Option **Apps aus.**</span><span class="sxs-lookup"><span data-stu-id="c45b8-123">In the Teams client, select **Apps**.</span></span>
1. <span data-ttu-id="c45b8-124">Stellen Sie sicher, dass die **Option Hochladen app angezeigt** wird.</span><span class="sxs-lookup"><span data-stu-id="c45b8-124">Verify that you can see the **Upload a custom app** option.</span></span> <span data-ttu-id="c45b8-125">Wenn Sie dies tun, bedeutet dies, dass Sie Apps querladen können.</span><span class="sxs-lookup"><span data-stu-id="c45b8-125">If you do, this means you can sideload apps.</span></span>

   :::image type="content" source="../assets/images/build-your-first-app/upload-custom-app-closeup.png" alt-text="Abbildung, in der Teams sie eine benutzerdefinierte App hochladen können.":::

# <a name="have-a-tenant"></a>[<span data-ttu-id="c45b8-127">Verfügen über einen Mandanten</span><span class="sxs-lookup"><span data-stu-id="c45b8-127">Have a tenant</span></span>](#tab/have-a-tenant)

<span data-ttu-id="c45b8-128">Wenn Sie bereits über einen Mandanten verfügen, überprüfen Sie, ob Sie Apps in einem Teams.</span><span class="sxs-lookup"><span data-stu-id="c45b8-128">If you already have a tenant, verify if you can sideload apps in Teams.</span></span>

<span data-ttu-id="c45b8-129">**Überprüfen, ob Sie Ihre Apps querladen können**</span><span class="sxs-lookup"><span data-stu-id="c45b8-129">**Verify that you can sideload your apps**</span></span> 

1. <span data-ttu-id="c45b8-130">Wählen Sie im Teams Client die Option **Apps aus.**</span><span class="sxs-lookup"><span data-stu-id="c45b8-130">In the Teams Client, select **Apps**.</span></span> 
1.  <span data-ttu-id="c45b8-131">Stellen Sie sicher, dass die **Option Hochladen app angezeigt** wird.</span><span class="sxs-lookup"><span data-stu-id="c45b8-131">Verify that you can see the **Upload a custom app** option.</span></span> <span data-ttu-id="c45b8-132">Wenn Sie dies tun, bedeutet dies, dass Sie Apps querladen können.</span><span class="sxs-lookup"><span data-stu-id="c45b8-132">If you do, this means you can sideload apps.</span></span> 

   :::image type="content" source="../assets/images/build-your-first-app/upload-custom-app-closeup.png" alt-text="Abbildung, in der Teams sie eine benutzerdefinierte App hochladen können.":::

---

### <a name="install-your-development-tools"></a><span data-ttu-id="c45b8-134">Installieren der Entwicklungstools</span><span class="sxs-lookup"><span data-stu-id="c45b8-134">Install your development tools</span></span>

<span data-ttu-id="c45b8-135">Zum Erstellen dieser App verwenden Sie das Teams Toolkit für Visual Studio Code, um schnell zu beginnen.</span><span class="sxs-lookup"><span data-stu-id="c45b8-135">To build this app, you'll use the Teams Toolkit for Visual Studio Code to quickly get started.</span></span> <span data-ttu-id="c45b8-136">Sie können auch Teams apps mit einem ihrer vordefinierten Tools erstellen.</span><span class="sxs-lookup"><span data-stu-id="c45b8-136">You can also build Teams apps with any of your preffered tools.</span></span> 

> [!NOTE]
> <span data-ttu-id="c45b8-137">Teams zeigt App-Inhalte nur über HTTPS-Verbindungen an.</span><span class="sxs-lookup"><span data-stu-id="c45b8-137">Teams displays app content only through HTTPS connections.</span></span> <span data-ttu-id="c45b8-138">Um bestimmte Arten von Apps lokal zu debuggen, z. B. einen Bot, erfahren Sie, wie Sie ngrok zum Einrichten eines sicheren Tunnels zwischen Teams und Ihrer App verwenden.</span><span class="sxs-lookup"><span data-stu-id="c45b8-138">To debug certain types of apps locally, such as a bot, you'll learn how to use ngrok to set up a secure tunnel between Teams and your app.</span></span>
> 
> <span data-ttu-id="c45b8-139">Produktions Teams apps werden in der Cloud gehostet.</span><span class="sxs-lookup"><span data-stu-id="c45b8-139">Production Teams apps are hosted in the cloud.</span></span>

<span data-ttu-id="c45b8-140">**So installieren Sie Microsoft Teams Tools**</span><span class="sxs-lookup"><span data-stu-id="c45b8-140">**To install Microsoft Teams tools**</span></span>

1. <span data-ttu-id="c45b8-141">Installieren Sie [Node.js](https://nodejs.org/en/).</span><span class="sxs-lookup"><span data-stu-id="c45b8-141">Install [Node.js](https://nodejs.org/en/).</span></span>
1. <span data-ttu-id="c45b8-142">Wenn Sie planen, einen Bot oder eine Messagingerweiterung zu erstellen, installieren Sie [ngrok](https://ngrok.com/download) und stellen Sie Ihren localhost mithilfe von [ngrok für](../tutorials/get-started-dotnet-app-studio.md#tunnel-using-ngrok)das Internet zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="c45b8-142">If you plan to build a bot or messaging extension, install [ngrok](https://ngrok.com/download) and [expose your localhost to the Internet using ngrok](../tutorials/get-started-dotnet-app-studio.md#tunnel-using-ngrok).</span></span>
1. <span data-ttu-id="c45b8-143">Installieren Sie die neueste Version [von Visual Studio Code](https://code.visualstudio.com/download).</span><span class="sxs-lookup"><span data-stu-id="c45b8-143">Install the latest version of [Visual Studio Code](https://code.visualstudio.com/download).</span></span> 
   
   > [!NOTE]
   > <span data-ttu-id="c45b8-144">Das Toolkit unterstützt frühere Versionen von Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="c45b8-144">The toolkit does not support earlier versions of Visual Studio Code.</span></span>

1. Wählen Sie in der linken Aktivitätsleiste **Erweiterungen aus.** :::image type="icon" source="../assets/icons/vs-code-extensions.png":::
1. <span data-ttu-id="c45b8-146">Wählen **Microsoft Teams Toolkit** installieren **aus.**</span><span class="sxs-lookup"><span data-stu-id="c45b8-146">In **Microsoft Teams Toolkit**, select **Install**.</span></span>

   :::image type="content" source="../assets/images/build-your-first-app/vsc-install-toolkit.png" alt-text="Abbildung, die zeigt, Visual Studio Code Sie die Erweiterung Microsoft Teams Toolkit installieren können.":::

## <a name="1-create-your-app-project"></a><span data-ttu-id="c45b8-148">1. Erstellen Ihres App-Projekts</span><span class="sxs-lookup"><span data-stu-id="c45b8-148">1. Create your app project</span></span>

1. <span data-ttu-id="c45b8-149">Öffnen Sie Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="c45b8-149">Open Visual Studio Code.</span></span>
1. Wählen **Microsoft Teams Toolkit** Erstellen einer neuen Teams App :::image type="icon" source="../assets/icons/vsc-toolkit.png":::  >  **aus.**

   :::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-02.png" alt-text="Screenshot, der zeigt, wie Sie Ihr App-Projekt mit dem Visual Studio Code Teams erstellen.":::
   
1. <span data-ttu-id="c45b8-152">Melden Sie sich mit Ihrem Microsoft 365-Entwicklungskonto an.</span><span class="sxs-lookup"><span data-stu-id="c45b8-152">Sign in with your Microsoft 365 development account.</span></span> <span data-ttu-id="c45b8-153">Entweder das konto, das Sie gerade erstellt haben, oder das Konto, das das Querladen von Apps ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="c45b8-153">Either the one you just created or the account you already had that allows app sideloading.</span></span>
1. <span data-ttu-id="c45b8-154">Wechseln Sie **auf dem Bildschirm** Projekt auswählen zu Persönliche **App,** und wählen **Sie JS** (JavaScript) > **Weiter aus.**</span><span class="sxs-lookup"><span data-stu-id="c45b8-154">On the **Select project** screen, go to **Personal app** and select **JS** (JavaScript) > **Next**.</span></span>

   :::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-03.png" alt-text="Screenshot, der zeigt, wie Sie Ihr App-Projekt mit dem Visual Studio Code Teams konfigurieren.":::

1. <span data-ttu-id="c45b8-156">Geben Sie einen Namen für Ihre Teams ein.</span><span class="sxs-lookup"><span data-stu-id="c45b8-156">Enter a name for your Teams app.</span></span>

    :::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-04.png" alt-text="Screenshot zum Hinzufügen eines Namens zu Ihrem App-Projekt mit dem Visual Studio Code Teams Toolkit.":::

1. <span data-ttu-id="c45b8-158">Klicken Sie auf **Fertigstellen**.</span><span class="sxs-lookup"><span data-stu-id="c45b8-158">Select **Finish**.</span></span> 
   <span data-ttu-id="c45b8-159">Ihr Projekt ist jetzt konfiguriert.</span><span class="sxs-lookup"><span data-stu-id="c45b8-159">Your project is now configured.</span></span> 

## <a name="2-understand-your-app-project-components"></a><span data-ttu-id="c45b8-160">2. Verstehen Ihrer App-Projektkomponenten</span><span class="sxs-lookup"><span data-stu-id="c45b8-160">2. Understand your app project components</span></span>

<span data-ttu-id="c45b8-161">Nachdem das Toolkit Ihr App-Projekt konfiguriert hat, verfügen Sie über die Komponenten, um Ihre "Hello, World!" zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="c45b8-161">After the toolkit configures your app project, you have the components to build your "Hello, World!"</span></span> <span data-ttu-id="c45b8-162">Teams App.</span><span class="sxs-lookup"><span data-stu-id="c45b8-162">Teams app.</span></span> <span data-ttu-id="c45b8-163">Die Verzeichnisse und Dateien des Projekts befinden sich im Visual Studio Code Explorer.</span><span class="sxs-lookup"><span data-stu-id="c45b8-163">The project's directories and files are located in the Visual Studio Code Explorer.</span></span> 

   :::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-05.png" alt-text="Screenshot des Gerüsts in Ihrem App-Projekt mit dem Visual Studio Code Teams Toolkit.":::

<span data-ttu-id="c45b8-165">Das Toolkit erstellt automatisch ein App-Gerüst im Verzeichnis basierend auf den `src` Funktionen, die Sie während des Setups hinzugefügt haben.</span><span class="sxs-lookup"><span data-stu-id="c45b8-165">The toolkit automatically creates app scaffolding in the `src` directory based on the capabilities you added during setup.</span></span> <span data-ttu-id="c45b8-166">Da Sie während des Setups eine Registerkarte erstellt haben, übernimmt die Datei im Verzeichnis die `App.js` `src/components` Initialisierung und das Routing Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="c45b8-166">Since you created a tab during setup, the `App.js` file in the `src/components` directory handles the initialization and routing of your app.</span></span> <span data-ttu-id="c45b8-167">Die Datei ruft außerdem das Microsoft Teams JavaScript-Client-SDK auf, um die Kommunikation zwischen Ihrer App und ihrem Teams.</span><span class="sxs-lookup"><span data-stu-id="c45b8-167">The file also calls the Microsoft Teams JavaScript client SDK to establish communication between your app and Teams.</span></span> 

## <a name="3-build-and-run-your-app"></a><span data-ttu-id="c45b8-168">3. Erstellen und Ausführen Ihrer App</span><span class="sxs-lookup"><span data-stu-id="c45b8-168">3. Build and run your app</span></span>

<span data-ttu-id="c45b8-169">Erstellen und ausführen Sie Ihre App lokal, um Zeit zu sparen.</span><span class="sxs-lookup"><span data-stu-id="c45b8-169">Build and run your app locally to save time.</span></span> 

<span data-ttu-id="c45b8-170">**So erstellen und ausführen Sie Ihre App**</span><span class="sxs-lookup"><span data-stu-id="c45b8-170">**To build and run your app**</span></span>

1. <span data-ttu-id="c45b8-171">Wählen Visual Studio Code **Terminal**  >  **anzeigen aus.**</span><span class="sxs-lookup"><span data-stu-id="c45b8-171">In Visual Studio Code, select **View** > **Terminal**.</span></span>
1. <span data-ttu-id="c45b8-172">Führen Sie `npm install` aus.</span><span class="sxs-lookup"><span data-stu-id="c45b8-172">Run `npm install`.</span></span>
1. <span data-ttu-id="c45b8-173">Führen Sie `npm start` aus.</span><span class="sxs-lookup"><span data-stu-id="c45b8-173">Run `npm start`.</span></span>
  
  <span data-ttu-id="c45b8-174">A **Compiled successfully!**</span><span class="sxs-lookup"><span data-stu-id="c45b8-174">A **Compiled successfully!**</span></span> <span data-ttu-id="c45b8-175">wird im Terminal angezeigt.</span><span class="sxs-lookup"><span data-stu-id="c45b8-175">message appears in the terminal.</span></span> <span data-ttu-id="c45b8-176">Ihre App wird jetzt auf Ihrem localhost unter `https://localhost:3000` ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="c45b8-176">Your app is now running on your localhost at `https://localhost:3000`.</span></span> 

## <a name="4-sideload-your-app-in-teams"></a><span data-ttu-id="c45b8-177">4. Querladen Ihrer App in Teams</span><span class="sxs-lookup"><span data-stu-id="c45b8-177">4. Sideload your app in Teams</span></span>

<span data-ttu-id="c45b8-178">Querladen ist der Vorgang der Installation einer App in Teams, die nicht von Ihrem Administrator oder Von Microsoft genehmigt wurde.</span><span class="sxs-lookup"><span data-stu-id="c45b8-178">Sideloading is the process of installing an app in Teams that hasn't been approved by your admin or Microsoft.</span></span> <span data-ttu-id="c45b8-179">Das Querladen ist häufig beim Testen und Debuggen Teams Apps.</span><span class="sxs-lookup"><span data-stu-id="c45b8-179">Sideloading is common when testing and debugging Teams apps.</span></span>

<span data-ttu-id="c45b8-180">Standardmäßig ist Teams das Querladen von Apps nicht zulässig.</span><span class="sxs-lookup"><span data-stu-id="c45b8-180">By default, Teams doesn't allow app sideloading.</span></span> <span data-ttu-id="c45b8-181">Sie können diese Einstellung im Teams ändern.</span><span class="sxs-lookup"><span data-stu-id="c45b8-181">You can change this setting in the Teams admin center.</span></span>

<span data-ttu-id="c45b8-182">**So aktivieren Sie das Querladen von Apps in Teams**</span><span class="sxs-lookup"><span data-stu-id="c45b8-182">**To enable app sideloading in Teams**</span></span>

1. <span data-ttu-id="c45b8-183">Melden Sie sich beim [Microsoft 365 Admin Center mit](https://admin.microsoft.com/Adminportal/Home?source=applauncher#/homepage#/) Ihren Administratoranmeldeinformationen an.</span><span class="sxs-lookup"><span data-stu-id="c45b8-183">Sign in to the [Microsoft 365 admin center](https://admin.microsoft.com/Adminportal/Home?source=applauncher#/homepage#/) with your admin credentials.</span></span>  
1. <span data-ttu-id="c45b8-184">Wählen **Sie Alle Teams**  >  aus.</span><span class="sxs-lookup"><span data-stu-id="c45b8-184">Select **Show All** > **Teams**.</span></span> 

   ![Abbildung des Admin Center-Menüs](~/assets/images/prepare-test-tenant/admin-center.png)

   > [!Note] 
   > <span data-ttu-id="c45b8-186">Es kann bis zu 24 Stunden dauern, bis **die Teams** angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="c45b8-186">It can take up to 24 hours for the **Teams** option to appear.</span></span> 

1. <span data-ttu-id="c45b8-187">Wechseln Sie **zu Teams**  >  **Setuprichtlinien**  >  **für Apps global** (Organisationsweite Standardeinstellung).</span><span class="sxs-lookup"><span data-stu-id="c45b8-187">Go to **Teams apps** > **Setup policies** > **Global** (Org-wide default).</span></span>

   ![Aktivieren der Querladenansicht](~/assets/images/prepare-test-tenant/turn-on-sideload.png)

1. <span data-ttu-id="c45b8-189">Aktivieren Sie das **Umschalten benutzerdefinierter Apps** hochladen.</span><span class="sxs-lookup"><span data-stu-id="c45b8-189">Turn on the **upload custom apps** toggle.</span></span>

1. <span data-ttu-id="c45b8-190">Wählen **Sie Speichern** aus, um die Änderungen zu speichern.</span><span class="sxs-lookup"><span data-stu-id="c45b8-190">Select **Save** to save the changes.</span></span>

   <span data-ttu-id="c45b8-191">Ihr Test-Mandant ermöglicht jetzt das Querladen benutzerdefinierter Apps.</span><span class="sxs-lookup"><span data-stu-id="c45b8-191">Your test tenant now allows custom app sideloading.</span></span>

   > [!Note]
   > <span data-ttu-id="c45b8-192">Suchen Sie nach Problemen, bevor Sie Ihre App mit dem Validierungsfeature in App Studio querladen, das im Toolkit enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="c45b8-192">Check for issues before sideloading your app using the validation feature in App Studio, which is included in the toolkit.</span></span> <span data-ttu-id="c45b8-193">Beheben Sie die Fehler, um die App erfolgreich querladen zu können.</span><span class="sxs-lookup"><span data-stu-id="c45b8-193">Fix the errors to successfully sideload the app.</span></span>


### <a name="sideload-your-app"></a><span data-ttu-id="c45b8-194">Querladen Ihrer App</span><span class="sxs-lookup"><span data-stu-id="c45b8-194">Sideload your app</span></span>

1. <span data-ttu-id="c45b8-195">Öffnen Visual Studio Code sie das Teams Toolkit.</span><span class="sxs-lookup"><span data-stu-id="c45b8-195">In Visual Studio Code, open the Teams Toolkit.</span></span>
1. <span data-ttu-id="c45b8-196">Wechseln Sie zu **App Studio**.</span><span class="sxs-lookup"><span data-stu-id="c45b8-196">Go to **App Studio**.</span></span>  
1. <span data-ttu-id="c45b8-197">Wählen **Sie Test and Distribute** Install  >  **aus.**</span><span class="sxs-lookup"><span data-stu-id="c45b8-197">Select **Test and Distribute** > **Install**.</span></span>

   :::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-appstudio.png" alt-text="Screenshot, der zeigt, wie Sie Ihre App mit dem Teams Visual Studio Code Teams-Toolkit querladen.":::

<span data-ttu-id="c45b8-199">**Alternativ**</span><span class="sxs-lookup"><span data-stu-id="c45b8-199">**Alternatively**</span></span>

1. <span data-ttu-id="c45b8-200">Wählen Sie **die F5-Taste** aus, um das zu installierende Browserfenster zu öffnen.</span><span class="sxs-lookup"><span data-stu-id="c45b8-200">Select the **F5** key to open browser window to install.</span></span> <span data-ttu-id="c45b8-201">Dadurch wird der Installationsprozess im **App Studio** übersprungen und Teams Browser angezeigt.</span><span class="sxs-lookup"><span data-stu-id="c45b8-201">This will skip the installation process in the **App Studio** and lauch Teams in your browser.</span></span>
1. <span data-ttu-id="c45b8-202">Wählen Sie im Installationsdialogfeld **Hinzufügen** aus, um Ihre App zu installieren, Teams.</span><span class="sxs-lookup"><span data-stu-id="c45b8-202">In the installation dialog, select **Add** to install your app to Teams.</span></span>

   :::image type="content" source="../assets/images/build-your-first-app/vscode-teams-toolkit-install.png" alt-text="Screenshot, der zeigt, wie Sie Ihre App querladen, um Teams zu laden.":::

   > [!Note]
   > <span data-ttu-id="c45b8-204">App Studio ist auch als eigenständige App für Teams verfügbar.</span><span class="sxs-lookup"><span data-stu-id="c45b8-204">App Studio is also available as a stand-alone app for Teams client.</span></span>

### <a name="troubleshoot-sideloading-issues"></a><span data-ttu-id="c45b8-205">Behandeln von Problemen beim Querladen</span><span class="sxs-lookup"><span data-stu-id="c45b8-205">Troubleshoot sideloading issues</span></span>

<span data-ttu-id="c45b8-206">**Installation fehlgeschlagen**</span><span class="sxs-lookup"><span data-stu-id="c45b8-206">**Installation failed**</span></span>

<span data-ttu-id="c45b8-207">Wenn die Fehlermeldung während der Installation Ihrer App angezeigt wird, stellen Sie sicher, dass `Manifest parsing has failed` die App-Informationen richtig eingegeben wurden.</span><span class="sxs-lookup"><span data-stu-id="c45b8-207">If the `Manifest parsing has failed` error message appears while installing your app, verify that the app information is correctly entered.</span></span>

<span data-ttu-id="c45b8-208">**So überprüfen Sie die App-Informationen**</span><span class="sxs-lookup"><span data-stu-id="c45b8-208">**To verify the app information**</span></span>

* <span data-ttu-id="c45b8-209">Wechseln Sie Teams Toolkit zu **App Studio** App Details, und überprüfen Sie, ob alle erforderlichen  >   Informationen korrekt eingegeben wurden.</span><span class="sxs-lookup"><span data-stu-id="c45b8-209">In the Teams Toolkit, go to **App Studio** > **App details** and verify that all the required information is correctly entered.</span></span>
*  <span data-ttu-id="c45b8-210">Wenn Sie die Datei manuell bearbeitet haben, stellen Sie sicher, dass das `manifest.json` JSON im **App-Manifest-Tool** in App Studio definiert ist.</span><span class="sxs-lookup"><span data-stu-id="c45b8-210">If you manually edited the `manifest.json` file, verify that the JSON is well-defined in the **App Manifest** tool in App Studio.</span></span>

<span data-ttu-id="c45b8-211">**Tabulatorinhalt wird nicht angezeigt**</span><span class="sxs-lookup"><span data-stu-id="c45b8-211">**Tab content not displayed**</span></span>

<span data-ttu-id="c45b8-212">Vergewissern Sie sich, dass Ihre App ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="c45b8-212">Verify that your app is running.</span></span> <span data-ttu-id="c45b8-213">Wenn nicht, wechseln Sie zum Terminal, und führen Sie `npm start` aus.</span><span class="sxs-lookup"><span data-stu-id="c45b8-213">If it isn't, go to the terminal and run `npm start`.</span></span>

## <a name="see-also"></a><span data-ttu-id="c45b8-214">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="c45b8-214">See also</span></span>

* [<span data-ttu-id="c45b8-215">Vorbereiten Ihres Microsoft 365-Mandanten</span><span class="sxs-lookup"><span data-stu-id="c45b8-215">Prepare your Microsoft 365 tenant</span></span>](https://docs.microsoft.com/microsoftteams/platform/concepts/build-and-test/prepare-your-o365-tenant)
* [<span data-ttu-id="c45b8-216">Auswählen eines Setups zum Testen und Debuggen ihrer Microsoft Teams App</span><span class="sxs-lookup"><span data-stu-id="c45b8-216">Choosing a setup to test and debug your Microsoft Teams app</span></span>](../concepts/build-and-test/debug.md)
* [<span data-ttu-id="c45b8-217">Erstellen von Registerkarten und anderen gehosteten Erfahrungen mit dem Microsoft Teams JavaScript-Client-SDK</span><span class="sxs-lookup"><span data-stu-id="c45b8-217">Building tabs and other hosted experiences with the Microsoft Teams JavaScript client SDK</span></span>](../tabs/how-to/using-teams-client-sdk.md)
* [<span data-ttu-id="c45b8-218">Vorbereiten der AppSource-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="c45b8-218">Prepare for AppSource submission</span></span>](../concepts/deploy-and-publish/appsource/prepare/submission-checklist.md)
* [<span data-ttu-id="c45b8-219">Entwickeln Sie schnell Apps mit App Studio für Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="c45b8-219">Quickly develop apps with App Studio for Microsoft Teams</span></span>](../concepts/build-and-test/app-studio-overview.md)
* [<span data-ttu-id="c45b8-220">Erstellen einer Kanalregisterkarte</span><span class="sxs-lookup"><span data-stu-id="c45b8-220">Build a channel tab</span></span>](../build-your-first-app/build-channel-tab.md)

## <a name="next-step"></a><span data-ttu-id="c45b8-221">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="c45b8-221">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c45b8-222">Erstellen einer persönlichen Registerkarte für Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="c45b8-222">Build a personal tab for Microsoft Teams</span></span>](../build-your-first-app/build-personal-tab.md)
