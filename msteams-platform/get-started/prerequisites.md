---
title: Erste Schritte – Voraussetzungen
author: adrianhall
description: Erfahren Sie, wie Sie mit der Entwicklung von Microsoft Teams-Apps beginnen und Ihre Umgebung einrichten.
ms.author: adhal
ms.date: 05/24/2021
ms.topic: quickstart
ms.openlocfilehash: 6496d238b3858c1df974732fa57c28eed7c54eb2
ms.sourcegitcommit: 14409950307b135265c8582408be5277b35131dd
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2021
ms.locfileid: "52994189"
---
# <a name="prerequisites-get-started-with-microsoft-teams-app-development"></a><span data-ttu-id="e5df8-103">Voraussetzungen: Erste Schritte bei der Entwicklung von Microsoft Teams-Apps</span><span class="sxs-lookup"><span data-stu-id="e5df8-103">Prerequisites: Get started with Microsoft Teams app development</span></span>

<span data-ttu-id="e5df8-104">Bevor Sie Ihre erste Teams-App erstellen, müssen Sie ein paar Tools installieren und Ihre Entwicklungsumgebung einrichten.</span><span class="sxs-lookup"><span data-stu-id="e5df8-104">Before your create your first Teams app, you must install a few tools and set up your development environment.</span></span>

## <a name="install-required-tools"></a><span data-ttu-id="e5df8-105">Installieren erforderlicher Tools</span><span class="sxs-lookup"><span data-stu-id="e5df8-105">Install required tools</span></span>

<span data-ttu-id="e5df8-106">Einige der benötigten Tools hängen davon ab, wie Sie Ihre Teams-App erstellen möchten:</span><span class="sxs-lookup"><span data-stu-id="e5df8-106">Some of the tools you need depend on how you you prefer to build your Teams app:</span></span>

- <span data-ttu-id="e5df8-107">[Node.js](https://nodejs.org/en/download/) (verwenden Sie die neueste Version von v14 LTS)</span><span class="sxs-lookup"><span data-stu-id="e5df8-107">[Node.js](https://nodejs.org/en/download/) (use the latest v14 LTS release)</span></span>
- <span data-ttu-id="e5df8-108">Ein Browser mit Entwicklertools wie [Microsoft Edge](https://www.microsoft.com/edge) (empfohlen) oder [Google Chrome](https://www.google.com/chrome/)</span><span class="sxs-lookup"><span data-stu-id="e5df8-108">A browser with developer tools - such as [Microsoft Edge](https://www.microsoft.com/edge) (recommended) or [Google Chrome](https://www.google.com/chrome/)</span></span>
- <span data-ttu-id="e5df8-109">Wenn Sie mit JavaScript, TypeScript oder dem SharePoint Framework (SPFx) entwickeln, installieren Sie [Visual Studio Code,](https://code.visualstudio.com/download)Version 1.55 oder höher.</span><span class="sxs-lookup"><span data-stu-id="e5df8-109">If you are developing with JavaScript, TypeScript, or the SharePoint Framework (SPFx), install [Visual Studio Code](https://code.visualstudio.com/download), version 1.55 or later.</span></span>  
- <span data-ttu-id="e5df8-110">Wenn Sie mit .NET entwickeln, installieren Sie [Visual Studio 2019.](https://visualstudio.com/download)</span><span class="sxs-lookup"><span data-stu-id="e5df8-110">If you are developing with .NET, install [Visual Studio 2019](https://visualstudio.com/download).</span></span> <span data-ttu-id="e5df8-111">Stellen Sie sicher, dass Sie die **ASP.NET- und Webentwicklung** oder **die plattformübergreifende .NET Core-Entwicklungsworkload** installieren.</span><span class="sxs-lookup"><span data-stu-id="e5df8-111">Ensure you install the **ASP.NET and web development** or **.NET Core cross-platform development** workload.</span></span>

> [!WARNING]
> <span data-ttu-id="e5df8-112">Es gibt bekannte Probleme mit `npm@7` , die mit Node v15 und höher gepackt sind.</span><span class="sxs-lookup"><span data-stu-id="e5df8-112">There are known issues with `npm@7`, packaged with Node v15 and later.</span></span> <span data-ttu-id="e5df8-113">Wenn Beim Ausführen Probleme `npm install` auftreten, stellen Sie sicher, dass Sie Node v14 (LTS) verwenden.</span><span class="sxs-lookup"><span data-stu-id="e5df8-113">If you have problems running `npm install`, ensure you're using Node v14 (LTS)</span></span>

## <a name="install-the-teams-toolkit"></a><span data-ttu-id="e5df8-114">Installieren des Teams-Toolkits</span><span class="sxs-lookup"><span data-stu-id="e5df8-114">Install the Teams Toolkit</span></span>

<span data-ttu-id="e5df8-115">Das Teams-Toolkit vereinfacht den Entwicklungsprozess mit Tools zum Bereitstellen und Bereitstellen von Cloudressourcen für Ihre App, zum Veröffentlichen im Teams Store und vieles mehr.</span><span class="sxs-lookup"><span data-stu-id="e5df8-115">The Teams Toolkit helps simplify the development process with tools to provision and deploy cloud resources for your app, publish to the Teams store, and more.</span></span> <span data-ttu-id="e5df8-116">Sie können das Toolkit mit Visual Studio Code, Visual Studio oder als CLI `teamsfx` (called) verwenden.</span><span class="sxs-lookup"><span data-stu-id="e5df8-116">You can use the toolkit with Visual Studio Code, Visual Studio, or as a CLI (called `teamsfx`).</span></span>

# <a name="visual-studio-code"></a>[<span data-ttu-id="e5df8-117">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="e5df8-117">Visual Studio Code</span></span>](#tab/vscode)

1. <span data-ttu-id="e5df8-118">Öffnen Sie Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="e5df8-118">Open Visual Studio Code.</span></span>
1. <span data-ttu-id="e5df8-119">Wählen Sie die Erweiterungsansicht (**STRG+UMSCHALT+X**  /  **⌘⇧-X** oder **Ansicht > Erweiterungen) aus.**</span><span class="sxs-lookup"><span data-stu-id="e5df8-119">Select the Extensions view (**Ctrl+Shift+X** / **⌘⇧-X** or **View > Extensions**).</span></span>
1. <span data-ttu-id="e5df8-120">Geben Sie im Suchfeld das **Teams-Toolkit** ein.</span><span class="sxs-lookup"><span data-stu-id="e5df8-120">In the search box, enter **Teams Toolkit**.</span></span>
1. <span data-ttu-id="e5df8-121">Wählen Sie die grüne Installationsschaltfläche neben dem Teams-Toolkit aus.</span><span class="sxs-lookup"><span data-stu-id="e5df8-121">Select the green install button next to the Teams Toolkit.</span></span>

<span data-ttu-id="e5df8-122">Sie finden das Teams-Toolkit auch im [Visual Studio Code Marketplace.](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension)</span><span class="sxs-lookup"><span data-stu-id="e5df8-122">You also can find the Teams Toolkit on the [Visual Studio Code Marketplace](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension).</span></span>

<span data-ttu-id="e5df8-123">Die folgenden Tools können von der Visual Studio Code-Erweiterung installiert werden, wenn sie benötigt werden.</span><span class="sxs-lookup"><span data-stu-id="e5df8-123">The following tools can be installed by the Visual Studio Code extension when they are needed.</span></span> <span data-ttu-id="e5df8-124">Wenn sie bereits installiert ist, kann stattdessen die installierte Version verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="e5df8-124">If already installed, the installed version can be used instead.</span></span> <span data-ttu-id="e5df8-125">Wenn Sie Linux einschließlich WSL verwenden, müssen Sie diese Tools vor der Verwendung installieren:</span><span class="sxs-lookup"><span data-stu-id="e5df8-125">If using Linux including WSL, you must install these tools before use:</span></span>

- [<span data-ttu-id="e5df8-126">Azure Functions Core Tools</span><span class="sxs-lookup"><span data-stu-id="e5df8-126">Azure Functions Core Tools</span></span>](/azure/azure-functions/functions-run-local)

    <span data-ttu-id="e5df8-127">Azure Functions Core Tools wird verwendet, um alle Back-End-Komponenten während einer lokalen Debugausführung lokal auszuführen, einschließlich der Authentifizierungshilfsprogramme, die beim Ausführen Ihrer Dienste in Azure erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="e5df8-127">Azure Functions Core Tools is used to run any backend components locally during a local debug run, including the authentication helpers required when running your services in Azure.</span></span> <span data-ttu-id="e5df8-128">Sie wird im Projektverzeichnis installiert (mithilfe des `devDependencies` npm).</span><span class="sxs-lookup"><span data-stu-id="e5df8-128">It is installed within the project directory (using the npm `devDependencies`).</span></span>

- [<span data-ttu-id="e5df8-129">.NET SDK</span><span class="sxs-lookup"><span data-stu-id="e5df8-129">.NET SDK</span></span>](/dotnet/core/install/)

    <span data-ttu-id="e5df8-130">Das .NET SDK wird verwendet, um angepasste Bindungen für lokales Debuggen und Azure Functions-App-Bereitstellungen zu installieren.</span><span class="sxs-lookup"><span data-stu-id="e5df8-130">The .NET SDK is used to install customized bindings for local debugging and Azure Functions app deployments.</span></span> <span data-ttu-id="e5df8-131">Wenn Sie das .NET 3.1 SDK (oder höher) nicht global installiert haben, kann die portierbare Version installiert werden.</span><span class="sxs-lookup"><span data-stu-id="e5df8-131">If you have not installed the .NET 3.1 (or later) SDK globally, the portable version can be installed.</span></span>

- [<span data-ttu-id="e5df8-132">ngrok</span><span class="sxs-lookup"><span data-stu-id="e5df8-132">ngrok</span></span>](https://ngrok.com/download)

    <span data-ttu-id="e5df8-133">Einige Teams-App-Features (Unterhaltungsbots, Messaging-Erweiterungen und eingehende Webhooks) erfordern eingehende Verbindungen.</span><span class="sxs-lookup"><span data-stu-id="e5df8-133">Some Teams app features (conversational bots, messaging extensions, and incoming webhooks) require inbound connections.</span></span> <span data-ttu-id="e5df8-134">Sie müssen Ihr Entwicklungssystem über einen Tunnel für Teams verfügbar machen.</span><span class="sxs-lookup"><span data-stu-id="e5df8-134">You need to expose your development system to Teams through a tunnel.</span></span> <span data-ttu-id="e5df8-135">Für Apps, die nur Registerkarten enthalten, ist kein Tunnel erforderlich.</span><span class="sxs-lookup"><span data-stu-id="e5df8-135">A tunnel is not required for apps that only include tabs.</span></span> <span data-ttu-id="e5df8-136">Dieses Paket wird im Projektverzeichnis installiert (mit `devDependencies` npm).</span><span class="sxs-lookup"><span data-stu-id="e5df8-136">This package is installed within the project directory (using npm `devDependencies`).</span></span>

# <a name="visual-studio-2019"></a>[<span data-ttu-id="e5df8-137">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="e5df8-137">Visual Studio 2019</span></span>](#tab/vs)

<span data-ttu-id="e5df8-138">Sie können Visual Studio 2019 verwenden, um Microsoft Teams-Apps mit Demenkserver in .NET zu entwickeln.</span><span class="sxs-lookup"><span data-stu-id="e5df8-138">You can use Visual Studio 2019 to develop Teams apps with Blazor Server in .NET.</span></span> <span data-ttu-id="e5df8-139">Wenn Sie nicht beabsichtigen, Teams-Apps in .NET zu entwickeln, installieren Sie die Visual Studio Code-Version des Teams-Toolkits.</span><span class="sxs-lookup"><span data-stu-id="e5df8-139">If you are not intending to develop Teams apps in .NET, install the Visual Studio Code version of Teams Toolkit.</span></span>

<span data-ttu-id="e5df8-140">So installieren Sie die Teams-Toolkit-Erweiterung:</span><span class="sxs-lookup"><span data-stu-id="e5df8-140">To install the Teams Toolkit extension:</span></span>

1. <span data-ttu-id="e5df8-141">Öffnen Sie Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="e5df8-141">Open Visual Studio 2019.</span></span>
1. <span data-ttu-id="e5df8-142">Wählen Sie **Erweiterungen**  >  **aus, um Erweiterungen zu verwalten.**</span><span class="sxs-lookup"><span data-stu-id="e5df8-142">Select **Extensions** > **Manage Extensions**.</span></span>
1. <span data-ttu-id="e5df8-143">Geben Sie im Suchfeld das **Teams-Toolkit** ein.</span><span class="sxs-lookup"><span data-stu-id="e5df8-143">In the search box, enter **Teams Toolkit**.</span></span>
1. <span data-ttu-id="e5df8-144">Wählen Sie die Teams-Toolkit-Erweiterung aus, und wählen Sie **"Herunterladen"** aus.</span><span class="sxs-lookup"><span data-stu-id="e5df8-144">Select the Teams Toolkit extension and select **Download**.</span></span>

<span data-ttu-id="e5df8-145">Die Erweiterung kann heruntergeladen werden.</span><span class="sxs-lookup"><span data-stu-id="e5df8-145">The extension can be downloaded.</span></span> <span data-ttu-id="e5df8-146">Schließen Sie Visual Studio 2019, um die Erweiterung zu installieren.</span><span class="sxs-lookup"><span data-stu-id="e5df8-146">Close Visual Studio 2019 to install the extension.</span></span>

# <a name="command-line"></a>[<span data-ttu-id="e5df8-147">Befehlszeile</span><span class="sxs-lookup"><span data-stu-id="e5df8-147">Command line</span></span>](#tab/cli)

<span data-ttu-id="e5df8-148">Um die TeamsFx CLI zu installieren, verwenden Sie den `npm` Paket-Manager:</span><span class="sxs-lookup"><span data-stu-id="e5df8-148">To install the TeamsFx CLI, use the `npm` package manager:</span></span>

``` bash
npm install -g @microsoft/teamsfx-cli
```

<span data-ttu-id="e5df8-149">Je nach Konfiguration müssen Sie die CLI möglicherweise `sudo` verwenden:</span><span class="sxs-lookup"><span data-stu-id="e5df8-149">Depending on your configuration, you may need to use `sudo` to install the CLI:</span></span>

``` bash
sudo npm install -g --unsafe-perm @microsoft/teamsfx-cli
```

<span data-ttu-id="e5df8-150">Dies ist auf Linux- und macOS-Systemen häufiger.</span><span class="sxs-lookup"><span data-stu-id="e5df8-150">This is more common on Linux and macOS systems.</span></span>

<span data-ttu-id="e5df8-151">Stellen Sie sicher, dass Sie dem PFAD den globalen npm-Cache hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="e5df8-151">Ensure you add the npm global cache to your PATH.</span></span> <span data-ttu-id="e5df8-152">Dies geschieht normalerweise als Teil des Node.js-Installationsprogramms.</span><span class="sxs-lookup"><span data-stu-id="e5df8-152">This is normally done as part of the Node.js installer.</span></span>  

<span data-ttu-id="e5df8-153">Sie können die CLI mit dem `teamsfx` Befehl verwenden.</span><span class="sxs-lookup"><span data-stu-id="e5df8-153">You can use the CLI with the `teamsfx` command.</span></span> <span data-ttu-id="e5df8-154">Stellen Sie sicher, dass der Befehl funktioniert, indem Sie `teamsfx -h` .</span><span class="sxs-lookup"><span data-stu-id="e5df8-154">Verify that the command is working by running `teamsfx -h`.</span></span>

> [!CAUTION]
> <span data-ttu-id="e5df8-155">Bevor Sie TeamsFx in PowerShell-Terminalen ausführen können, müssen Sie die Ausführungsrichtlinie "Remotesignierung" für PowerShell aktivieren.</span><span class="sxs-lookup"><span data-stu-id="e5df8-155">Before you can run TeamsFx in PowerShell terminals, you must enable the "remote signed" execution policy for PowerShell.</span></span> <span data-ttu-id="e5df8-156">Weitere Informationen finden Sie in der [PowerShell-Dokumentation.](/powershell/module/microsoft.powershell.core/about/about_signing)</span><span class="sxs-lookup"><span data-stu-id="e5df8-156">For more information, refer to the [PowerShell documentation](/powershell/module/microsoft.powershell.core/about/about_signing).</span></span>

---

## <a name="install-optional-tools"></a><span data-ttu-id="e5df8-157">Installieren optionaler Tools</span><span class="sxs-lookup"><span data-stu-id="e5df8-157">Install optional tools</span></span>

<span data-ttu-id="e5df8-158">Installieren Sie Browsertools für die App-Entwicklung.</span><span class="sxs-lookup"><span data-stu-id="e5df8-158">Install browser tools for app development.</span></span> <span data-ttu-id="e5df8-159">Wenn Ihre App beispielsweise mit React geschrieben wurde, können Sie React Developer Tools verwenden:</span><span class="sxs-lookup"><span data-stu-id="e5df8-159">For instance, if your app is written with React, you can use React Developer Tools:</span></span>

- [<span data-ttu-id="e5df8-160">React Developer Tools für Chrome</span><span class="sxs-lookup"><span data-stu-id="e5df8-160">React Developer Tools for Chrome</span></span>](https://chrome.google.com/webstore/detail/react-developer-tools/fmkadmapgofadopljbjfkapdkoienihi)

<span data-ttu-id="e5df8-161">Wenn Sie auf in Azure gespeicherte Daten zugreifen oder ein cloudbasiertes Back-End für Ihre Teams-App in Azure bereitstellen möchten, installieren Sie diese Tools:</span><span class="sxs-lookup"><span data-stu-id="e5df8-161">If you want to access data stored in Azure or deploy a cloud-based backend for your Teams app in Azure, install these tools:</span></span>

- [<span data-ttu-id="e5df8-162">Azure Tools für Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="e5df8-162">Azure Tools for Visual Studio Code</span></span>](https://marketplace.visualstudio.com/items?itemName=ms-vscode.vscode-node-azure-pack)
- [<span data-ttu-id="e5df8-163">Azure CLI</span><span class="sxs-lookup"><span data-stu-id="e5df8-163">Azure CLI</span></span>](/cli/azure/install-azure-cli)

<span data-ttu-id="e5df8-164">Wenn Sie mit Microsoft Graph-Daten arbeiten, sollten Sie den Microsoft Graph-Tester kennenlernen und mit einem Lesezeichen versehen.</span><span class="sxs-lookup"><span data-stu-id="e5df8-164">If you work with Microsoft Graph data, you should learn about and bookmark the Microsoft Graph Explorer.</span></span> <span data-ttu-id="e5df8-165">Mit diesem browserbasierten Tool können Sie Microsoft Graph außerhalb einer App abfragen.</span><span class="sxs-lookup"><span data-stu-id="e5df8-165">This browser-based tool allows you to query Microsoft Graph outside of an app.</span></span>

- [<span data-ttu-id="e5df8-166">Microsoft Graph-Tester</span><span class="sxs-lookup"><span data-stu-id="e5df8-166">Microsoft Graph Explorer</span></span>](https://developer.microsoft.com/graph/graph-explorer)

<span data-ttu-id="e5df8-167">Mit dem Entwicklerportal für Teams können Sie Ihre Teams-App konfigurieren, verwalten und verteilen, einschließlich in Ihrer Organisation oder im Teams Store.</span><span class="sxs-lookup"><span data-stu-id="e5df8-167">With the Developer Portal for Teams, you can configure, manage, and distribute your Teams app including to your organization or the Teams store.</span></span>

- [<span data-ttu-id="e5df8-168">Entwicklerportal für Teams</span><span class="sxs-lookup"><span data-stu-id="e5df8-168">Developer Portal for Teams</span></span>](https://dev.teams.microsoft.com/)

## <a name="enable-sideloading"></a><span data-ttu-id="e5df8-169">Aktivieren des Querladens</span><span class="sxs-lookup"><span data-stu-id="e5df8-169">Enable sideloading</span></span>

<span data-ttu-id="e5df8-170">Während der Entwicklung müssen Sie Ihre App in Teams laden, ohne sie zu verteilen.</span><span class="sxs-lookup"><span data-stu-id="e5df8-170">During development, you must load your app within Teams without distributing it.</span></span> <span data-ttu-id="e5df8-171">Dies wird als "Querladen" bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="e5df8-171">This is known as "sideloading".</span></span>

1. <span data-ttu-id="e5df8-172">Wenn Sie über ein Teams-Konto verfügen, überprüfen Sie, ob Sie Apps in Teams querladen können:</span><span class="sxs-lookup"><span data-stu-id="e5df8-172">If you have a Teams account, verify if you can sideload apps in Teams:</span></span>

    1. <span data-ttu-id="e5df8-173">Wählen Sie im Teams-Client **Apps** aus.</span><span class="sxs-lookup"><span data-stu-id="e5df8-173">In the Teams client, select **Apps**.</span></span>
    1. <span data-ttu-id="e5df8-174">Suchen Sie nach einer Option zum **Hochladen einer benutzerdefinierten App.**</span><span class="sxs-lookup"><span data-stu-id="e5df8-174">Look for an option to **Upload a custom app**.</span></span>

    :::image type="content" source="~/assets/images/teams-toolkit-v2/upload-custom-app-closeup.png" alt-text="Abbildung, die zeigt, wo Sie in Teams eine benutzerdefinierte App hochladen können.":::

> [!NOTE]
> <span data-ttu-id="e5df8-176">Wenn Sie Apps immer noch nicht querladen können, wenden Sie sich an Ihren Teams-Administrator.</span><span class="sxs-lookup"><span data-stu-id="e5df8-176">If you still cannot sideload apps, talk to your Teams administrator.</span></span> <span data-ttu-id="e5df8-177">Weitere Informationen finden Sie unter [Aktivieren benutzerdefinierter Teams-Apps und Aktivieren des Hochladens benutzerdefinierter Apps.](~/concepts/build-and-test/prepare-your-o365-tenant.md#enable-custom-teams-apps-and-turn-on-custom-app-uploading)</span><span class="sxs-lookup"><span data-stu-id="e5df8-177">See [enable custom Teams apps and turn on custom app uploading](~/concepts/build-and-test/prepare-your-o365-tenant.md#enable-custom-teams-apps-and-turn-on-custom-app-uploading) for details.</span></span>

## <a name="get-a-free-teams-developer-tenant-optional"></a><span data-ttu-id="e5df8-178">Abrufen eines kostenlosen Teams-Entwicklermandanten (optional)</span><span class="sxs-lookup"><span data-stu-id="e5df8-178">Get a free Teams developer tenant (optional)</span></span>

<span data-ttu-id="e5df8-179">Wenn die Option zum Querladen nicht angezeigt wird oder Sie kein Teams-Konto haben, können Sie ein kostenloses Teams-Entwicklerkonto erhalten, indem Sie am M365-Entwicklerprogramm teilnehmen.</span><span class="sxs-lookup"><span data-stu-id="e5df8-179">If you cannot see the sideload option, or you do not have a Teams account, you can get a free Teams developer account by joining the M365 developer program.</span></span>  <span data-ttu-id="e5df8-180">Der Registrierungsvorgang dauert ungefähr zwei Minuten.</span><span class="sxs-lookup"><span data-stu-id="e5df8-180">The registration process takes approximately two minutes.</span></span>

1. <span data-ttu-id="e5df8-181">Wechseln Sie zum [Microsoft 365-Entwicklerprogramm.](https://developer.microsoft.com/microsoft-365/dev-program)</span><span class="sxs-lookup"><span data-stu-id="e5df8-181">Go to the [Microsoft 365 developer program](https://developer.microsoft.com/microsoft-365/dev-program).</span></span>
1. <span data-ttu-id="e5df8-182">Wählen Sie **"Jetzt beitreten"** aus, und folgen Sie den Anweisungen auf dem Bildschirm.</span><span class="sxs-lookup"><span data-stu-id="e5df8-182">Select **Join Now** and follow the onscreen instructions.</span></span>
1. <span data-ttu-id="e5df8-183">Wenn Sie zur Willkommensseite gelangen, wählen Sie **E5-Abonnement einrichten** aus.</span><span class="sxs-lookup"><span data-stu-id="e5df8-183">When you get to the welcome screen, select **Set up E5 subscription**.</span></span>
1. <span data-ttu-id="e5df8-184">Richten Sie Ihr Administratorkonto ein.</span><span class="sxs-lookup"><span data-stu-id="e5df8-184">Set up your administrator account.</span></span> <span data-ttu-id="e5df8-185">Sobald Sie fertig sind, sollte ein Bildschirm wie dieser angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="e5df8-185">Once you finish, you should see a screen like this.</span></span>

    :::image type="content" source="~/assets/images/build-your-first-app/dev-program-subscription.png" alt-text="Beispiel für die Anzeige nach der Registrierung für das Microsoft 365-Entwicklerprogramm.":::

1. <span data-ttu-id="e5df8-187">Melden Sie sich bei Teams mit dem Administratorkonto an, das Sie gerade eingerichtet haben.</span><span class="sxs-lookup"><span data-stu-id="e5df8-187">Sign in to Teams using the administrator account you just set up.</span></span>
1. <span data-ttu-id="e5df8-188">Überprüfen Sie, ob Sie jetzt über die Option zum **Hochladen einer benutzerdefinierten App** verfügen.</span><span class="sxs-lookup"><span data-stu-id="e5df8-188">Verify if you now have the **Upload a custom app** option.</span></span>

## <a name="get-a-free-azure-account"></a><span data-ttu-id="e5df8-189">Abrufen eines kostenlosen Azure-Kontos</span><span class="sxs-lookup"><span data-stu-id="e5df8-189">Get a free Azure account</span></span>

<span data-ttu-id="e5df8-190">Wenn Sie Ihre App hosten oder auf Ressourcen in Azure zugreifen möchten, benötigen Sie ein Azure-Abonnement.</span><span class="sxs-lookup"><span data-stu-id="e5df8-190">If you wish to host your app or access resources within Azure, you must have an Azure subscription.</span></span>  <span data-ttu-id="e5df8-191">Sie können [ein kostenloses Konto erstellen,](https://azure.microsoft.com/free/) bevor Sie beginnen.</span><span class="sxs-lookup"><span data-stu-id="e5df8-191">You can [create a free account](https://azure.microsoft.com/free/) before you begin.</span></span>

## <a name="sign-in-to-your-microsoft-365-and-azure-accounts"></a><span data-ttu-id="e5df8-192">Melden Sie sich bei Ihren Microsoft 365- und Azure-Konten an.</span><span class="sxs-lookup"><span data-stu-id="e5df8-192">Sign in to your Microsoft 365 and Azure accounts</span></span>

<span data-ttu-id="e5df8-193">Sie müssen Zugriff auf zwei Konten haben:</span><span class="sxs-lookup"><span data-stu-id="e5df8-193">You must have access to two accounts:</span></span>

- <span data-ttu-id="e5df8-194">Ihre Microsoft 365-Kontoanmeldeinformationen.</span><span class="sxs-lookup"><span data-stu-id="e5df8-194">Your Microsoft 365 account credentials.</span></span> <span data-ttu-id="e5df8-195">Dies ist das Konto, mit dem Sie sich bei Teams anmelden.</span><span class="sxs-lookup"><span data-stu-id="e5df8-195">This is the account that you use to sign in to Teams.</span></span> <span data-ttu-id="e5df8-196">Wenn Sie einen Mandanten des Microsoft 365-Entwicklerprogramms verwenden, ist dies das Administratorkonto, das Sie bei der Registrierung für das Programm eingerichtet haben.</span><span class="sxs-lookup"><span data-stu-id="e5df8-196">If you're using an Microsoft 365 developer program tenant, this is the admin account you set up when you registered for the program.</span></span>
- - <span data-ttu-id="e5df8-197">Ihre Azure-Anmeldeinformationen.</span><span class="sxs-lookup"><span data-stu-id="e5df8-197">Your Azure credentials.</span></span> <span data-ttu-id="e5df8-198">Dies ist das Konto, das Sie für den Zugriff auf das Azure-Portal und für die Bereitstellung neuer Cloudressourcen zur Unterstützung Ihrer App verwenden.</span><span class="sxs-lookup"><span data-stu-id="e5df8-198">This is the account that you use to access the Azure Portal and for provisioning new cloud resources to support your app.</span></span>

# <a name="visual-studio-code"></a>[<span data-ttu-id="e5df8-199">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="e5df8-199">Visual Studio Code</span></span>](#tab/vscode)

1. <span data-ttu-id="e5df8-200">Öffnen von Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="e5df8-200">Open Visual Studio Code</span></span>
1. <span data-ttu-id="e5df8-201">Wählen Sie das Symbol "Teams" in der Randleiste aus:</span><span class="sxs-lookup"><span data-stu-id="e5df8-201">Select the Teams icon in the sidebar:</span></span>

    :::image type="content" source="~/assets/images/teams-toolkit-v2/sidebar-icon.png" alt-text="Das Microsoft Teams-Symbol in der Visual Studio Code-Randleiste.":::

1. <span data-ttu-id="e5df8-203">Wählen Sie **"Bei M365 anmelden"** aus.</span><span class="sxs-lookup"><span data-stu-id="e5df8-203">Select **Sign in to M365**.</span></span>

    :::image type="content" source="~/assets/images/teams-toolkit-v2/account-commands.png" alt-text="Speicherort des Abschnitts &quot;Konten&quot;, der für die Anmeldung verwendet wird.":::

1. <span data-ttu-id="e5df8-205">Der Anmeldevorgang beginnt mit ihrem normalen Webbrowser.</span><span class="sxs-lookup"><span data-stu-id="e5df8-205">The sign-in process starts using your normal web browser.</span></span> <span data-ttu-id="e5df8-206">Schließen Sie den Anmeldevorgang für Ihr M365-Konto ab.</span><span class="sxs-lookup"><span data-stu-id="e5df8-206">Complete the sign-in process for your M365 account.</span></span> <span data-ttu-id="e5df8-207">Sie werden aufgefordert, wenn Sie den Browser schließen und zu Visual Studio Code zurückkehren können.</span><span class="sxs-lookup"><span data-stu-id="e5df8-207">You are prompted when you can close the browser and return to Visual Studio Code.</span></span>
1. <span data-ttu-id="e5df8-208">Kehren Sie zum Teams-Toolkit in Visual Studio Code zurück.</span><span class="sxs-lookup"><span data-stu-id="e5df8-208">Return to the Teams Toolkit within Visual Studio Code.</span></span>
1. <span data-ttu-id="e5df8-209">Wählen Sie **"Bei Azure anmelden"** aus.</span><span class="sxs-lookup"><span data-stu-id="e5df8-209">Select **Sign in to Azure**.</span></span>

    > [!TIP]
    > <span data-ttu-id="e5df8-210">Wenn Sie die Azure-Kontoerweiterung installiert haben und dasselbe Konto verwenden, können Sie diesen Schritt überspringen.</span><span class="sxs-lookup"><span data-stu-id="e5df8-210">If you have the Azure Account extension installed and are using the same account, you can skip this step.</span></span> <span data-ttu-id="e5df8-211">Verwenden Sie das gleiche Konto wie in anderen Erweiterungen.</span><span class="sxs-lookup"><span data-stu-id="e5df8-211">Use the same account as you are using in other extensions.</span></span>

1. <span data-ttu-id="e5df8-212">Der Anmeldevorgang beginnt mit ihrem normalen Webbrowser.</span><span class="sxs-lookup"><span data-stu-id="e5df8-212">The sign-in process starts using your normal web browser.</span></span>  <span data-ttu-id="e5df8-213">Schließen Sie den Anmeldevorgang für Ihr Azure-Konto ab.</span><span class="sxs-lookup"><span data-stu-id="e5df8-213">Complete the sign-in process for your Azure account.</span></span> <span data-ttu-id="e5df8-214">Sie werden aufgefordert, wenn Sie den Browser schließen und zu Visual Studio Code zurückkehren können.</span><span class="sxs-lookup"><span data-stu-id="e5df8-214">You are prompted when you can close the browser and return to Visual Studio Code.</span></span>

<span data-ttu-id="e5df8-215">Nach Abschluss des Vorgangs werden im Abschnitt **"KONTEN"** der Randleiste die beiden Konten separat zusammen mit der Anzahl der verwendbaren Azure-Abonnements angezeigt, die Ihnen zur Verfügung stehen.</span><span class="sxs-lookup"><span data-stu-id="e5df8-215">When complete, the **ACCOUNTS** section of the sidebar shows the two accounts separately, together with the number of usable Azure subscriptions available to you.</span></span> <span data-ttu-id="e5df8-216">Stellen Sie sicher, dass mindestens ein verwendbares Azure-Abonnement verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="e5df8-216">Ensure you have at least one usable Azure subscription available.</span></span> <span data-ttu-id="e5df8-217">Wenn nicht, melden Sie sich ab, und verwenden Sie ein anderes Konto.</span><span class="sxs-lookup"><span data-stu-id="e5df8-217">If not, sign out and use a different account.</span></span>

# <a name="visual-studio-2019"></a>[<span data-ttu-id="e5df8-218">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="e5df8-218">Visual Studio 2019</span></span>](#tab/vs)

<span data-ttu-id="e5df8-219">Visual Studio 2019 fordert Sie auf, sich bei jedem Dienst nach Bedarf anzumelden.</span><span class="sxs-lookup"><span data-stu-id="e5df8-219">Visual Studio 2019 prompts you to log in to each service as required.</span></span> <span data-ttu-id="e5df8-220">Sie müssen sich nicht vorab bei Ihren M365- und Azure-Konten anmelden.</span><span class="sxs-lookup"><span data-stu-id="e5df8-220">You do not need to sign in to your M365 and Azure accounts in advance.</span></span>

# <a name="command-line"></a>[<span data-ttu-id="e5df8-221">Befehlszeile</span><span class="sxs-lookup"><span data-stu-id="e5df8-221">Command line</span></span>](#tab/cli)

1. <span data-ttu-id="e5df8-222">Melden Sie sich bei Microsoft 365 mit der TeamsFx CLI an:</span><span class="sxs-lookup"><span data-stu-id="e5df8-222">Sign in to Microsoft 365 with the TeamsFx CLI:</span></span>

    ``` bash
    teamsfx account login m365
    ```

    <span data-ttu-id="e5df8-223">Der Anmeldevorgang beginnt mit ihrem normalen Webbrowser.</span><span class="sxs-lookup"><span data-stu-id="e5df8-223">The sign-in process starts using your normal web browser.</span></span> <span data-ttu-id="e5df8-224">Schließen Sie den Anmeldevorgang für Ihr M365-Konto ab.</span><span class="sxs-lookup"><span data-stu-id="e5df8-224">Complete the sign-in process for your M365 account.</span></span> <span data-ttu-id="e5df8-225">Sie werden aufgefordert, den Browser zu schließen.</span><span class="sxs-lookup"><span data-stu-id="e5df8-225">You are prompted when you can close the browser.</span></span>

2. <span data-ttu-id="e5df8-226">Melden Sie sich bei Azure mit der TeamsFx CLI an:</span><span class="sxs-lookup"><span data-stu-id="e5df8-226">Sign in to Azure with the TeamsFx CLI:</span></span>

    ``` bash
    teamsfx account login azure
    ```

    <span data-ttu-id="e5df8-227">Der Anmeldevorgang beginnt mit ihrem normalen Webbrowser.</span><span class="sxs-lookup"><span data-stu-id="e5df8-227">The sign-in process starts using your normal web browser.</span></span> <span data-ttu-id="e5df8-228">Schließen Sie den Anmeldevorgang für Ihr Azure-Konto ab.</span><span class="sxs-lookup"><span data-stu-id="e5df8-228">Complete the sign-in process for your Azure account.</span></span> <span data-ttu-id="e5df8-229">Sie werden aufgefordert, den Browser zu schließen.</span><span class="sxs-lookup"><span data-stu-id="e5df8-229">You are prompted when you can close the browser.</span></span>

<span data-ttu-id="e5df8-230">Die Kontoanmeldungen werden von Visual Studio Code und der TeamsFx CLI gemeinsam verwendet.</span><span class="sxs-lookup"><span data-stu-id="e5df8-230">The account logins are shared between Visual Studio Code and the TeamsFx CLI.</span></span>

---

<span data-ttu-id="e5df8-231">Nachdem Ihre Entwicklungsumgebung konfiguriert ist, können Sie Ihre erste Teams-App erstellen, erstellen und bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="e5df8-231">Now that your development environment is configured, you can create, build, and deploy your first Teams app.</span></span>

## <a name="see-also"></a><span data-ttu-id="e5df8-232">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="e5df8-232">See also</span></span>

- [<span data-ttu-id="e5df8-233">Erstellen Ihrer ersten Teams-App mit Demerz</span><span class="sxs-lookup"><span data-stu-id="e5df8-233">Create your first Teams app with Blazor</span></span>](first-app-blazor.md)
- [<span data-ttu-id="e5df8-234">Erstellen Ihrer ersten Teams-App mit SharePoint Framework (SPFx)</span><span class="sxs-lookup"><span data-stu-id="e5df8-234">Create your first Teams app using SharePoint Framework (SPFx)</span></span>](first-app-spfx.md)
- [<span data-ttu-id="e5df8-235">Erstellen einer Unterhaltungs-Bot-App</span><span class="sxs-lookup"><span data-stu-id="e5df8-235">Create a conversational bot app</span></span>](first-app-bot.md)
- [<span data-ttu-id="e5df8-236">Erstellen einer Messaging-Erweiterung</span><span class="sxs-lookup"><span data-stu-id="e5df8-236">Create a messaging extension</span></span>](first-message-extension.md)

## <a name="next-step"></a><span data-ttu-id="e5df8-237">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="e5df8-237">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e5df8-238">Erstellen Ihrer ersten Teams-App mit React</span><span class="sxs-lookup"><span data-stu-id="e5df8-238">Create your first Teams app using React</span></span>](first-app-react.md)
