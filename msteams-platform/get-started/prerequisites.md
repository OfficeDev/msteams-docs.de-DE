---
title: Erste Schritte – Voraussetzungen
author: adrianhall
description: Erfahren Sie, wie Sie mit der Entwicklung Microsoft Teams App beginnen und Ihre Umgebung einrichten.
ms.author: adhal
ms.date: 05/24/2021
ms.topic: quickstart
ms.openlocfilehash: 73d99f2bbbc69bf13242110a56e13e662655283c
ms.sourcegitcommit: 9cabeaed9baf96c8caeb1497f0bc37abdb787d22
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/25/2021
ms.locfileid: "52646771"
---
# <a name="prerequisites-get-started-with-microsoft-teams-app-development"></a><span data-ttu-id="2dc2d-103">Voraussetzungen: Erste Schritte mit Microsoft Teams App-Entwicklung</span><span class="sxs-lookup"><span data-stu-id="2dc2d-103">Prerequisites: Get started with Microsoft Teams app development</span></span>

<span data-ttu-id="2dc2d-104">Bevor Sie Ihre erste Teams erstellen, müssen Sie einige Tools installieren und Ihre Entwicklungsumgebung einrichten.</span><span class="sxs-lookup"><span data-stu-id="2dc2d-104">Before your create your first Teams app, you must install a few tools and set up your development environment.</span></span>

## <a name="install-required-tools"></a><span data-ttu-id="2dc2d-105">Installieren erforderlicher Tools</span><span class="sxs-lookup"><span data-stu-id="2dc2d-105">Install required tools</span></span>

<span data-ttu-id="2dc2d-106">Einige der benötigten Tools hängen davon ab, wie Sie Ihre App Teams möchten:</span><span class="sxs-lookup"><span data-stu-id="2dc2d-106">Some of the tools you need depend on how you you prefer to build your Teams app:</span></span>

- <span data-ttu-id="2dc2d-107">[Node.js](https://nodejs.org/en/download/) (verwenden Sie die neueste Version von v14 LTS)</span><span class="sxs-lookup"><span data-stu-id="2dc2d-107">[Node.js](https://nodejs.org/en/download/) (use the latest v14 LTS release)</span></span> 
- <span data-ttu-id="2dc2d-108">Ein Browser mit Entwicklertools – [z. B. Microsoft Edge](https://www.microsoft.com/edge) (empfohlen) oder [Google Chrome](https://www.google.com/chrome/)</span><span class="sxs-lookup"><span data-stu-id="2dc2d-108">A browser with developer tools - such as [Microsoft Edge](https://www.microsoft.com/edge) (recommended) or [Google Chrome](https://www.google.com/chrome/)</span></span>
- <span data-ttu-id="2dc2d-109">Wenn Sie mit JavaScript, TypeScript oder dem SharePoint-Framework (SPFx) entwickeln, installieren Sie [Visual Studio Code](https://code.visualstudio.com/download), Version 1.55 oder höher.</span><span class="sxs-lookup"><span data-stu-id="2dc2d-109">If you're developing with JavaScript, TypeScript, or the SharePoint Framework (SPFx), install [Visual Studio Code](https://code.visualstudio.com/download), version 1.55 or later.</span></span>  
- <span data-ttu-id="2dc2d-110">Wenn Sie mit .NET entwickeln, installieren Sie [Visual Studio 2019](https://visualstudio.com/download).</span><span class="sxs-lookup"><span data-stu-id="2dc2d-110">If you're developing with .NET, install [Visual Studio 2019](https://visualstudio.com/download).</span></span>  <span data-ttu-id="2dc2d-111">Stellen Sie sicher, **dass ASP.NET und Webentwicklung** oder **.NET Core plattformübergreifende Entwicklungsarbeitsauslastung installieren.**</span><span class="sxs-lookup"><span data-stu-id="2dc2d-111">Ensure you install the **ASP.NET and web development** or **.NET Core cross-platform development** workload.</span></span>

> [!WARNING]
> <span data-ttu-id="2dc2d-112">Es gibt bekannte Probleme mit `npm@7` , verpackt mit Knoten v15 und höher.</span><span class="sxs-lookup"><span data-stu-id="2dc2d-112">There are known issues with `npm@7`, packaged with Node v15 and later.</span></span> <span data-ttu-id="2dc2d-113">Wenn Probleme beim Ausführen auftreten, stellen Sie sicher, dass Sie `npm install` Knoten v14 (LTS) verwenden.</span><span class="sxs-lookup"><span data-stu-id="2dc2d-113">If you have problems running `npm install`, ensure you're using Node v14 (LTS)</span></span>

## <a name="install-the-teams-toolkit"></a><span data-ttu-id="2dc2d-114">Installieren des Teams Toolkits</span><span class="sxs-lookup"><span data-stu-id="2dc2d-114">Install the Teams Toolkit</span></span>

<span data-ttu-id="2dc2d-115">Das Teams Toolkit vereinfacht den Entwicklungsprozess mit Tools zum Bereitstellen und Bereitstellen von Cloudressourcen für Ihre App, zum Veröffentlichen im Teams Store und mehr.</span><span class="sxs-lookup"><span data-stu-id="2dc2d-115">The Teams Toolkit helps simplify the development process with tools to provision and deploy cloud resources for your app, publish to the Teams store, and more.</span></span> <span data-ttu-id="2dc2d-116">Sie können das Toolkit mit Visual Studio Code, Visual Studio oder als CLI `teamsfx` (genannt) verwenden.</span><span class="sxs-lookup"><span data-stu-id="2dc2d-116">You can use the toolkit with Visual Studio Code, Visual Studio, or as a CLI (called `teamsfx`).</span></span>

# <a name="visual-studio-code"></a>[<span data-ttu-id="2dc2d-117">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="2dc2d-117">Visual Studio Code</span></span>](#tab/vscode)

1. <span data-ttu-id="2dc2d-118">Öffnen Sie Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="2dc2d-118">Open Visual Studio Code.</span></span>
1. <span data-ttu-id="2dc2d-119">Wählen Sie die Ansicht Erweiterungen (**STRG+Umschalt+X**  /  **.⇧-X** oder **Ansicht > Erweiterungen ).**</span><span class="sxs-lookup"><span data-stu-id="2dc2d-119">Select the Extensions view (**Ctrl+Shift+X** / **⌘⇧-X** or **View > Extensions**).</span></span>
1. <span data-ttu-id="2dc2d-120">Geben Sie im Suchfeld Teams _Toolkit ein._</span><span class="sxs-lookup"><span data-stu-id="2dc2d-120">In the search box, enter _Teams Toolkit_.</span></span>
1. <span data-ttu-id="2dc2d-121">Wählen Sie auf der grünen Installationsschaltfläche neben dem Teams Toolkit aus.</span><span class="sxs-lookup"><span data-stu-id="2dc2d-121">Select on the green install button next to the Teams Toolkit.</span></span>

<span data-ttu-id="2dc2d-122">Sie finden auch das Teams Toolkit im [Visual Studio Code Marketplace](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension).</span><span class="sxs-lookup"><span data-stu-id="2dc2d-122">You also can find the Teams Toolkit on the [Visual Studio Code Marketplace](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension).</span></span>

<span data-ttu-id="2dc2d-123">Die folgenden Tools werden von der erweiterung Visual Studio Code installiert, wenn sie benötigt werden.</span><span class="sxs-lookup"><span data-stu-id="2dc2d-123">The following tools will be installed by the Visual Studio Code extension when they are needed.</span></span>  <span data-ttu-id="2dc2d-124">Wenn sie bereits installiert ist, wird stattdessen die installierte Version verwendet.</span><span class="sxs-lookup"><span data-stu-id="2dc2d-124">If already installed, the installed version will be used instead.</span></span>  <span data-ttu-id="2dc2d-125">Wenn Sie Linux (einschließlich WSL) verwenden, müssen Sie diese Tools vor der Verwendung installieren:</span><span class="sxs-lookup"><span data-stu-id="2dc2d-125">If using Linux (including WSL), you must install these tools before use:</span></span>

- [<span data-ttu-id="2dc2d-126">Azure Functions Core Tools</span><span class="sxs-lookup"><span data-stu-id="2dc2d-126">Azure Functions Core Tools</span></span>](/azure/azure-functions/functions-run-local)

    <span data-ttu-id="2dc2d-127">Azure Functions Core Tools wird verwendet, um alle Back-End-Komponenten während einer lokalen Debug ausgeführt, einschließlich der Authentifizierungshilfen, die beim Ausführen Ihrer Dienste in Azure erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="2dc2d-127">Azure Functions Core Tools is used to run any backend components locally during a local debug run, including the authentication helpers required when running your services in Azure.</span></span>  <span data-ttu-id="2dc2d-128">Es wird im Projektverzeichnis installiert (mit npm `devDependencies` ).</span><span class="sxs-lookup"><span data-stu-id="2dc2d-128">It is installed within the project directory (using the npm `devDependencies`).</span></span>

- [<span data-ttu-id="2dc2d-129">.NET SDK</span><span class="sxs-lookup"><span data-stu-id="2dc2d-129">.NET SDK</span></span>](/dotnet/core/install/)

    <span data-ttu-id="2dc2d-130">Das .NET SDK wird verwendet, um angepasste Bindungen für lokale Debugging- und Azure Functions-App-Bereitstellungen zu installieren.</span><span class="sxs-lookup"><span data-stu-id="2dc2d-130">The .NET SDK is used to install customized bindings for local debugging and Azure Functions app deployments.</span></span>  <span data-ttu-id="2dc2d-131">Wenn Sie das .NET 3.1 (oder höher) SDK nicht global installiert haben, wird die portable Version installiert.</span><span class="sxs-lookup"><span data-stu-id="2dc2d-131">If you have not installed the .NET 3.1 (or later) SDK globally, the portable version will be installed.</span></span>

- [<span data-ttu-id="2dc2d-132">ngrok</span><span class="sxs-lookup"><span data-stu-id="2dc2d-132">ngrok</span></span>](https://ngrok.com/download)

    <span data-ttu-id="2dc2d-133">Einige Teams (Unterhaltungsbots, Messagingerweiterungen und eingehende Webhooks) erfordern eingehende Verbindungen.</span><span class="sxs-lookup"><span data-stu-id="2dc2d-133">Some Teams app features (conversational bots, messaging extensions, and incoming webhooks) require inbound connections.</span></span>  <span data-ttu-id="2dc2d-134">Sie müssen Ihr Entwicklungssystem für die Teams Tunnel verfügbar machen.</span><span class="sxs-lookup"><span data-stu-id="2dc2d-134">You need to expose your development system to Teams through a tunnel.</span></span>  <span data-ttu-id="2dc2d-135">Für Apps, die nur Registerkarten enthalten, ist kein Tunnel erforderlich.</span><span class="sxs-lookup"><span data-stu-id="2dc2d-135">A tunnel is not required for apps that only include tabs.</span></span>  <span data-ttu-id="2dc2d-136">Dieses Paket wird im Projektverzeichnis installiert (mithilfe von npm `devDependencies` ).</span><span class="sxs-lookup"><span data-stu-id="2dc2d-136">This package is installed within the project directory (using npm `devDependencies`).</span></span>

# <a name="visual-studio-2019"></a>[<span data-ttu-id="2dc2d-137">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="2dc2d-137">Visual Studio 2019</span></span>](#tab/vs)

<span data-ttu-id="2dc2d-138">Sie können Visual Studio 2019 verwenden, um Teams mit Blazor Server in .NET zu entwickeln.</span><span class="sxs-lookup"><span data-stu-id="2dc2d-138">You can use Visual Studio 2019 to develop Teams apps with Blazor Server in .NET.</span></span>  <span data-ttu-id="2dc2d-139">Wenn Sie nicht beabsichtigen, Teams in .NET zu entwickeln, installieren Sie die Visual Studio Code version von Teams Toolkit.</span><span class="sxs-lookup"><span data-stu-id="2dc2d-139">If you're not intending to develop Teams apps in .NET, install the Visual Studio Code version of Teams Toolkit.</span></span>

<span data-ttu-id="2dc2d-140">So installieren Sie Teams Toolkit-Erweiterung:</span><span class="sxs-lookup"><span data-stu-id="2dc2d-140">To install the Teams Toolkit extension:</span></span>

1. <span data-ttu-id="2dc2d-141">Öffnen Visual Studio 2019.</span><span class="sxs-lookup"><span data-stu-id="2dc2d-141">Open Visual Studio 2019.</span></span>
1. <span data-ttu-id="2dc2d-142">Wählen **Sie Erweiterungen** Erweiterungen verwalten  >  **aus.**</span><span class="sxs-lookup"><span data-stu-id="2dc2d-142">Select **Extensions** > **Manage Extensions**.</span></span>
1. <span data-ttu-id="2dc2d-143">Geben Sie im Suchfeld Teams _Toolkit ein._</span><span class="sxs-lookup"><span data-stu-id="2dc2d-143">In the search box, enter _Teams Toolkit_.</span></span>
1. <span data-ttu-id="2dc2d-144">Wählen Sie die Teams Toolkiterweiterung aus, und wählen Sie **Herunterladen aus.**</span><span class="sxs-lookup"><span data-stu-id="2dc2d-144">Select the Teams Toolkit extension and select **Download**.</span></span>

<span data-ttu-id="2dc2d-145">Die Erweiterung wird heruntergeladen.</span><span class="sxs-lookup"><span data-stu-id="2dc2d-145">The extension will be downloaded.</span></span>  <span data-ttu-id="2dc2d-146">Schließen Visual Studio 2019, um die Erweiterung zu installieren.</span><span class="sxs-lookup"><span data-stu-id="2dc2d-146">Close Visual Studio 2019 to install the extension.</span></span>

# <a name="command-line"></a>[<span data-ttu-id="2dc2d-147">Befehlszeile</span><span class="sxs-lookup"><span data-stu-id="2dc2d-147">Command line</span></span>](#tab/cli)

<span data-ttu-id="2dc2d-148">Verwenden Sie den Paket-Manager, um die TeamsFx CLI `npm` zu installieren:</span><span class="sxs-lookup"><span data-stu-id="2dc2d-148">To install the TeamsFx CLI, use the `npm` package manager:</span></span>

``` bash
npm install -g @microsoft/teamsfx-cli
```

<span data-ttu-id="2dc2d-149">Je nach Konfiguration müssen Sie möglicherweise verwenden, um `sudo` die CLI zu installieren:</span><span class="sxs-lookup"><span data-stu-id="2dc2d-149">Depending on your configuration, you may need to use `sudo` to install the CLI:</span></span>

``` bash
sudo npm install -g --unsafe-perm @microsoft/teamsfx-cli
```

<span data-ttu-id="2dc2d-150">Dies ist auf Linux- und macOS-Systemen häufiger.</span><span class="sxs-lookup"><span data-stu-id="2dc2d-150">This is more common on Linux and macOS systems.</span></span>

<span data-ttu-id="2dc2d-151">Stellen Sie sicher, dass Sie den globalen npm-Cache zu Path hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="2dc2d-151">Ensure you add the npm global cache to your PATH.</span></span>  <span data-ttu-id="2dc2d-152">Dies geschieht normalerweise im Rahmen des Node.js Installationsprogramms.</span><span class="sxs-lookup"><span data-stu-id="2dc2d-152">This is normally done as part of the Node.js installer.</span></span>  

<span data-ttu-id="2dc2d-153">Sie können die CLI mit dem Befehl `teamsfx` verwenden.</span><span class="sxs-lookup"><span data-stu-id="2dc2d-153">You can use the CLI with the `teamsfx` command.</span></span>  <span data-ttu-id="2dc2d-154">Stellen Sie sicher, dass der Befehl funktioniert, indem Sie `teamsfx -h` ausführen.</span><span class="sxs-lookup"><span data-stu-id="2dc2d-154">Verify that the command is working by running `teamsfx -h`.</span></span>

> [!CAUTION]
> <span data-ttu-id="2dc2d-155">Bevor Sie TeamsFx in PowerShell-Terminalen ausführen können, müssen Sie die Ausführungsrichtlinie "Remote signiert" für PowerShell aktivieren.</span><span class="sxs-lookup"><span data-stu-id="2dc2d-155">Before you can run TeamsFx in PowerShell terminals, you need to enable the "remote signed" execution policy for PowerShell.</span></span>  <span data-ttu-id="2dc2d-156">Weitere Informationen finden Sie in der [PowerShell-Dokumentation](/powershell/module/microsoft.powershell.core/about/about_signing).</span><span class="sxs-lookup"><span data-stu-id="2dc2d-156">For more information, refer to the [PowerShell documentation](/powershell/module/microsoft.powershell.core/about/about_signing).</span></span>

---

## <a name="install-optional-tools"></a><span data-ttu-id="2dc2d-157">Installieren optionaler Tools</span><span class="sxs-lookup"><span data-stu-id="2dc2d-157">Install optional tools</span></span>

<span data-ttu-id="2dc2d-158">Installieren Sie Browsertools für die App-Entwicklung.</span><span class="sxs-lookup"><span data-stu-id="2dc2d-158">Install browser tools for app development.</span></span> <span data-ttu-id="2dc2d-159">Wenn Ihre App z. B. mit React geschrieben wird, können Sie React Verwenden:</span><span class="sxs-lookup"><span data-stu-id="2dc2d-159">For instance, if your app is written with React, you can use React Developer Tools:</span></span>

- [<span data-ttu-id="2dc2d-160">React Entwicklertools für Chrome</span><span class="sxs-lookup"><span data-stu-id="2dc2d-160">React Developer Tools for Chrome</span></span>](https://chrome.google.com/webstore/detail/react-developer-tools/fmkadmapgofadopljbjfkapdkoienihi)

<span data-ttu-id="2dc2d-161">Wenn Sie auf in Azure gespeicherte Daten zugreifen oder ein cloudbasiertes Back-End für Ihre Teams in Azure bereitstellen möchten, installieren Sie die folgenden Tools:</span><span class="sxs-lookup"><span data-stu-id="2dc2d-161">If you want to access data stored in Azure or deploy a cloud-based backend for your Teams app in Azure, install these tools:</span></span>

- [<span data-ttu-id="2dc2d-162">Azure Tools for Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="2dc2d-162">Azure Tools for Visual Studio Code</span></span>](https://marketplace.visualstudio.com/items?itemName=ms-vscode.vscode-node-azure-pack)
- [<span data-ttu-id="2dc2d-163">Azure CLI</span><span class="sxs-lookup"><span data-stu-id="2dc2d-163">Azure CLI</span></span>](/cli/azure/install-azure-cli)

<span data-ttu-id="2dc2d-164">Wenn Sie mit Microsoft Graph arbeiten, sollten Sie mehr über den Microsoft Graph explorer erfahren und ein Lesezeichen setzen.</span><span class="sxs-lookup"><span data-stu-id="2dc2d-164">If you work with Microsoft Graph data, you should learn about and bookmark the Microsoft Graph Explorer.</span></span> <span data-ttu-id="2dc2d-165">Mit diesem browserbasierten Tool können Sie Microsoft Graph außerhalb einer App abfragen.</span><span class="sxs-lookup"><span data-stu-id="2dc2d-165">This browser-based tool allows you to query Microsoft Graph outside of an app.</span></span>

- [<span data-ttu-id="2dc2d-166">Microsoft Graph-Tester</span><span class="sxs-lookup"><span data-stu-id="2dc2d-166">Microsoft Graph Explorer</span></span>](https://developer.microsoft.com/graph/graph-explorer)

<span data-ttu-id="2dc2d-167">Mit dem Entwicklerportal für Teams können Sie Ihre Teams-App konfigurieren, verwalten und verteilen (einschließlich an Ihre Organisation oder den Teams Store).</span><span class="sxs-lookup"><span data-stu-id="2dc2d-167">With the Developer Portal for Teams, you can configure, manage, and distribute your Teams app (including to your org or the Teams store).</span></span>

- [<span data-ttu-id="2dc2d-168">Entwicklerportal für Teams</span><span class="sxs-lookup"><span data-stu-id="2dc2d-168">Developer Portal for Teams</span></span>](https://dev.teams.microsoft.com/)

## <a name="enable-sideloading"></a><span data-ttu-id="2dc2d-169">Aktivieren des Querladens</span><span class="sxs-lookup"><span data-stu-id="2dc2d-169">Enable sideloading</span></span>

<span data-ttu-id="2dc2d-170">Während der Entwicklung müssen Sie Ihre App innerhalb von Teams laden, ohne sie zu verteilen.</span><span class="sxs-lookup"><span data-stu-id="2dc2d-170">During development, you will need to load your app within Teams without distributing it.</span></span>  <span data-ttu-id="2dc2d-171">Dies wird als "Querladen" bezeichnet.</span><span class="sxs-lookup"><span data-stu-id="2dc2d-171">This is known as "sideloading".</span></span>

1. <span data-ttu-id="2dc2d-172">Wenn Sie über ein Teams verfügen, überprüfen Sie, ob Sie Apps in einem Teams:</span><span class="sxs-lookup"><span data-stu-id="2dc2d-172">If you have a Teams account, verify if you can sideload apps in Teams:</span></span>

    1. <span data-ttu-id="2dc2d-173">Wählen Sie im Teams Die Option **Apps aus.**</span><span class="sxs-lookup"><span data-stu-id="2dc2d-173">In the Teams client, select **Apps**.</span></span>
    1. <span data-ttu-id="2dc2d-174">Suchen Sie nach einer Option zum **Hochladen einer benutzerdefinierten App**.</span><span class="sxs-lookup"><span data-stu-id="2dc2d-174">Look for an option to **Upload a custom app**.</span></span>

    :::image type="content" source="~/assets/images/teams-toolkit-v2/upload-custom-app-closeup.png" alt-text="Abbildung, in der Teams sie eine benutzerdefinierte App hochladen können.":::

> [!NOTE]
> <span data-ttu-id="2dc2d-176">Wenn Sie Apps weiterhin nicht querladen können, wenden Sie sich an Ihren Teams Administrator.</span><span class="sxs-lookup"><span data-stu-id="2dc2d-176">If you still can't sideload apps, talk to your Teams administrator.</span></span> <span data-ttu-id="2dc2d-177">Weitere Informationen finden Sie unter Aktivieren Teams benutzerdefinierter Apps und [Aktivieren des Hochladens benutzerdefinierter](~/concepts/build-and-test/prepare-your-o365-tenant.md#enable-custom-teams-apps-and-turn-on-custom-app-uploading) Apps.</span><span class="sxs-lookup"><span data-stu-id="2dc2d-177">See [enable custom Teams apps and turn on custom app uploading](~/concepts/build-and-test/prepare-your-o365-tenant.md#enable-custom-teams-apps-and-turn-on-custom-app-uploading) for details.</span></span>

## <a name="get-a-free-teams-developer-tenant-optional"></a><span data-ttu-id="2dc2d-178">Get a free Teams developer tenant (optional)</span><span class="sxs-lookup"><span data-stu-id="2dc2d-178">Get a free Teams developer tenant (optional)</span></span>

<span data-ttu-id="2dc2d-179">Wenn die Querladenoption nicht angezeigt wird oder Sie nicht über ein Teams-Konto verfügen, können Sie ein kostenloses Teams-Entwicklerkonto erhalten, indem Sie am M365-Entwicklerprogramm teilnehmen.</span><span class="sxs-lookup"><span data-stu-id="2dc2d-179">If you cannot see the sideload option, or you don't have a Teams account, you can get a free Teams developer account by joining the M365 developer program.</span></span>  <span data-ttu-id="2dc2d-180">Der Registrierungsprozess dauert ca. zwei Minuten.</span><span class="sxs-lookup"><span data-stu-id="2dc2d-180">The registration process takes approximately two minutes.</span></span>

1. <span data-ttu-id="2dc2d-181">Wechseln Sie zum [Microsoft 365 Entwicklerprogramm](https://developer.microsoft.com/microsoft-365/dev-program).</span><span class="sxs-lookup"><span data-stu-id="2dc2d-181">Go to the [Microsoft 365 developer program](https://developer.microsoft.com/microsoft-365/dev-program).</span></span>
1. <span data-ttu-id="2dc2d-182">Wählen **Sie Jetzt beitreten** aus, und folgen Sie den Anweisungen auf dem Bildschirm.</span><span class="sxs-lookup"><span data-stu-id="2dc2d-182">Select **Join Now** and follow the onscreen instructions.</span></span>
1. <span data-ttu-id="2dc2d-183">Wenn Sie zum Willkommensbildschirm kommen, wählen Sie **E5-Abonnement einrichten aus.**</span><span class="sxs-lookup"><span data-stu-id="2dc2d-183">When you get to the welcome screen, select **Set up E5 subscription**.</span></span>
1. <span data-ttu-id="2dc2d-184">Richten Sie Ihr Administratorkonto ein.</span><span class="sxs-lookup"><span data-stu-id="2dc2d-184">Set up your administrator account.</span></span> <span data-ttu-id="2dc2d-185">Sobald Sie fertig sind, sollte ein Bildschirm wie dieser angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="2dc2d-185">Once you finish, you should see a screen like this.</span></span>

    :::image type="content" source="~/assets/images/build-your-first-app/dev-program-subscription.png" alt-text="Beispiel für das, was Sie nach der Anmeldung für das Microsoft 365 sehen.":::

1. <span data-ttu-id="2dc2d-187">Melden Sie sich mit Teams Administratorkonto an, das Sie gerade eingerichtet haben.</span><span class="sxs-lookup"><span data-stu-id="2dc2d-187">Log in to Teams using the administrator account you just set up.</span></span>
1. <span data-ttu-id="2dc2d-188">Überprüfen Sie, ob Sie **jetzt über Hochladen benutzerdefinierte App-Option** verfügen.</span><span class="sxs-lookup"><span data-stu-id="2dc2d-188">Verify if you now have the **Upload a custom app** option.</span></span>

## <a name="get-a-free-azure-account"></a><span data-ttu-id="2dc2d-189">Kostenloses Azure-Konto erhalten</span><span class="sxs-lookup"><span data-stu-id="2dc2d-189">Get a free Azure account</span></span>

<span data-ttu-id="2dc2d-190">Wenn Sie Ihre App hosten oder auf Ressourcen in Azure zugreifen möchten, benötigen Sie ein Azure-Abonnement.</span><span class="sxs-lookup"><span data-stu-id="2dc2d-190">If you wish to host your app or access resources within Azure, you will need an Azure subscription.</span></span>  <span data-ttu-id="2dc2d-191">Sie können [ein kostenloses Konto erstellen,](https://azure.microsoft.com/free/) bevor Sie beginnen.</span><span class="sxs-lookup"><span data-stu-id="2dc2d-191">You can [create a free account](https://azure.microsoft.com/free/) before you begin.</span></span>

## <a name="sign-in-to-your-microsoft-365-and-azure-accounts"></a><span data-ttu-id="2dc2d-192">Melden Sie sich bei Ihren Microsoft 365- und Azure-Konten an</span><span class="sxs-lookup"><span data-stu-id="2dc2d-192">Sign in to your Microsoft 365 and Azure accounts</span></span>

<span data-ttu-id="2dc2d-193">Sie benötigen Zugriff auf zwei Konten:</span><span class="sxs-lookup"><span data-stu-id="2dc2d-193">You will need access to two accounts:</span></span>

- <span data-ttu-id="2dc2d-194">Ihre Microsoft 365 Kontoanmeldeinformationen.</span><span class="sxs-lookup"><span data-stu-id="2dc2d-194">Your Microsoft 365 account credentials.</span></span> <span data-ttu-id="2dc2d-195">Dies ist das Konto, das Sie zum Anmelden bei Teams.</span><span class="sxs-lookup"><span data-stu-id="2dc2d-195">This is the account that you use to sign in to Teams.</span></span> <span data-ttu-id="2dc2d-196">Wenn Sie einen mandanten Microsoft 365 verwenden, ist dies das Administratorkonto, das Sie bei der Registrierung für das Programm eingerichtet haben.</span><span class="sxs-lookup"><span data-stu-id="2dc2d-196">If you're using an Microsoft 365 developer program tenant, this is the admin account you set up when you registered for the program.</span></span>
- - <span data-ttu-id="2dc2d-197">Ihre Azure-Anmeldeinformationen.</span><span class="sxs-lookup"><span data-stu-id="2dc2d-197">Your Azure credentials.</span></span> <span data-ttu-id="2dc2d-198">Dies ist das Konto, das Sie für den Zugriff auf das Azure-Portal und für die Bereitstellung neuer Cloudressourcen zur Unterstützung Ihrer App verwenden.</span><span class="sxs-lookup"><span data-stu-id="2dc2d-198">This is the account that you use to access the Azure Portal and for provisioning new cloud resources to support your app.</span></span>

# <a name="visual-studio-code"></a>[<span data-ttu-id="2dc2d-199">Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="2dc2d-199">Visual Studio Code</span></span>](#tab/vscode)

1. <span data-ttu-id="2dc2d-200">Öffnen Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="2dc2d-200">Open Visual Studio Code</span></span>
1. <span data-ttu-id="2dc2d-201">Wählen Sie Teams Symbol in der Seitenleiste aus:</span><span class="sxs-lookup"><span data-stu-id="2dc2d-201">Select the Teams icon in the sidebar:</span></span>

    :::image type="content" source="~/assets/images/teams-toolkit-v2/sidebar-icon.png" alt-text="Das Teams Symbol in der Visual Studio Code Seitenleiste.":::

1. <span data-ttu-id="2dc2d-203">Wählen **Sie Anmelden bei M365 aus.**</span><span class="sxs-lookup"><span data-stu-id="2dc2d-203">Select **Sign in to M365**.</span></span>

    :::image type="content" source="~/assets/images/teams-toolkit-v2/account-commands.png" alt-text="Speicherort des Abschnitts Konten, der für die Anmeldung verwendet wird.":::

1. <span data-ttu-id="2dc2d-205">Der Anmeldevorgang beginnt mit dem normalen Webbrowser.</span><span class="sxs-lookup"><span data-stu-id="2dc2d-205">The sign-in process will start using your normal web browser.</span></span>  <span data-ttu-id="2dc2d-206">Schließen Sie den Anmeldevorgang für Ihr M365-Konto ab.</span><span class="sxs-lookup"><span data-stu-id="2dc2d-206">Complete the sign-in process for your M365 account.</span></span>  <span data-ttu-id="2dc2d-207">Sie werden aufgefordert, den Browser zu schließen und zu Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="2dc2d-207">You will be prompted when you can close the browser and return to Visual Studio Code.</span></span>
1. <span data-ttu-id="2dc2d-208">Kehren Sie zum Teams Toolkit innerhalb Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="2dc2d-208">Return to the Teams Toolkit within Visual Studio Code.</span></span>
1. <span data-ttu-id="2dc2d-209">Wählen **Sie Anmelden bei Azure aus.**</span><span class="sxs-lookup"><span data-stu-id="2dc2d-209">Select **Sign in to Azure**.</span></span>

    > [!TIP]
    > <span data-ttu-id="2dc2d-210">Wenn Sie die Azure Account-Erweiterung installiert haben und dasselbe Konto verwenden, können Sie diesen Schritt überspringen.</span><span class="sxs-lookup"><span data-stu-id="2dc2d-210">If you have the Azure Account extension installed and are using the same account, you can skip this step.</span></span>  <span data-ttu-id="2dc2d-211">Sie verwenden automatisch dasselbe Konto wie in anderen Erweiterungen.</span><span class="sxs-lookup"><span data-stu-id="2dc2d-211">You will automatically use the same account as you are using in other extensions.</span></span>

1. <span data-ttu-id="2dc2d-212">Der Anmeldevorgang beginnt mit dem normalen Webbrowser.</span><span class="sxs-lookup"><span data-stu-id="2dc2d-212">The sign-in process will start using your normal web browser.</span></span>  <span data-ttu-id="2dc2d-213">Führen Sie den Anmeldevorgang für Ihr Azure-Konto aus.</span><span class="sxs-lookup"><span data-stu-id="2dc2d-213">Complete the sign-in process for your Azure account.</span></span>  <span data-ttu-id="2dc2d-214">Sie werden aufgefordert, den Browser zu schließen und zu Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="2dc2d-214">You will be prompted when you can close the browser and return to Visual Studio Code.</span></span>

<span data-ttu-id="2dc2d-215">Nach Abschluss des Vorgangs zeigt der Abschnitt **ACCOUNTS** der Seitenleiste die beiden Konten zusammen mit der Anzahl der verwendbaren Azure-Abonnements an, die Ihnen zur Verfügung stehen.</span><span class="sxs-lookup"><span data-stu-id="2dc2d-215">When complete, the **ACCOUNTS** section of the sidebar will show the two accounts separately, together with the number of usable Azure subscriptions available to you.</span></span>  <span data-ttu-id="2dc2d-216">Stellen Sie sicher, dass mindestens ein verwendbares Azure-Abonnement verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="2dc2d-216">Ensure you have at least one usable Azure subscription available.</span></span>  <span data-ttu-id="2dc2d-217">Wenn nicht, melden Sie sich ab, und verwenden Sie ein anderes Konto.</span><span class="sxs-lookup"><span data-stu-id="2dc2d-217">If not, sign out and use a different account.</span></span>

# <a name="visual-studio-2019"></a>[<span data-ttu-id="2dc2d-218">Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="2dc2d-218">Visual Studio 2019</span></span>](#tab/vs)

<span data-ttu-id="2dc2d-219">Visual Studio 2019 werden Sie aufgefordert, sich bei jedem Dienst bei Bedarf zu melden.</span><span class="sxs-lookup"><span data-stu-id="2dc2d-219">Visual Studio 2019 will prompt you to log in to each service as it is needed.</span></span>  <span data-ttu-id="2dc2d-220">Sie müssen sich nicht vorab bei Ihren M365- und Azure-Konten anmelden.</span><span class="sxs-lookup"><span data-stu-id="2dc2d-220">You do not need to sign in to your M365 and Azure accounts in advance.</span></span>

# <a name="command-line"></a>[<span data-ttu-id="2dc2d-221">Befehlszeile</span><span class="sxs-lookup"><span data-stu-id="2dc2d-221">Command line</span></span>](#tab/cli)

1. <span data-ttu-id="2dc2d-222">Melden Sie sich bei Microsoft 365 mit der TeamsFx CLI an:</span><span class="sxs-lookup"><span data-stu-id="2dc2d-222">Sign in to Microsoft 365 with the TeamsFx CLI:</span></span>

    ``` bash
    teamsfx account login m365
    ```

    <span data-ttu-id="2dc2d-223">Der Anmeldevorgang beginnt mit dem normalen Webbrowser.</span><span class="sxs-lookup"><span data-stu-id="2dc2d-223">The sign-in process will start using your normal web browser.</span></span>  <span data-ttu-id="2dc2d-224">Schließen Sie den Anmeldevorgang für Ihr M365-Konto ab.</span><span class="sxs-lookup"><span data-stu-id="2dc2d-224">Complete the sign-in process for your M365 account.</span></span>  <span data-ttu-id="2dc2d-225">Sie werden aufgefordert, den Browser zu schließen.</span><span class="sxs-lookup"><span data-stu-id="2dc2d-225">You will be prompted when you can close the browser.</span></span>

2. <span data-ttu-id="2dc2d-226">Melden Sie sich mit der TeamsFx CLI bei Azure an:</span><span class="sxs-lookup"><span data-stu-id="2dc2d-226">Sign in to Azure with the TeamsFx CLI:</span></span>

    ``` bash
    teamsfx account login azure
    ```

    <span data-ttu-id="2dc2d-227">Der Anmeldevorgang beginnt mit dem normalen Webbrowser.</span><span class="sxs-lookup"><span data-stu-id="2dc2d-227">The sign-in process will start using your normal web browser.</span></span>  <span data-ttu-id="2dc2d-228">Führen Sie den Anmeldevorgang für Ihr Azure-Konto aus.</span><span class="sxs-lookup"><span data-stu-id="2dc2d-228">Complete the sign-in process for your Azure account.</span></span>  <span data-ttu-id="2dc2d-229">Sie werden aufgefordert, den Browser zu schließen.</span><span class="sxs-lookup"><span data-stu-id="2dc2d-229">You will be prompted when you can close the browser.</span></span>

<span data-ttu-id="2dc2d-230">Die Kontoanmeldungen werden von Visual Studio Code und der TeamsFx CLI freigegeben.</span><span class="sxs-lookup"><span data-stu-id="2dc2d-230">The account logins are shared between Visual Studio Code and the TeamsFx CLI.</span></span>

---

## <a name="next-steps"></a><span data-ttu-id="2dc2d-231">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="2dc2d-231">Next steps</span></span>

<span data-ttu-id="2dc2d-232">Nachdem Ihre Entwicklungsumgebung konfiguriert ist, können Sie Ihre erste App erstellen, erstellen und Teams bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="2dc2d-232">Now that your development environment is configured, you can create, build, and deploy your first Teams app.</span></span>

- [<span data-ttu-id="2dc2d-233">Erstellen Sie Ihre erste Teams-App mithilfe React</span><span class="sxs-lookup"><span data-stu-id="2dc2d-233">Create your first Teams app using React</span></span>](first-app-react.md)
- [<span data-ttu-id="2dc2d-234">Erstellen Ihrer ersten Teams-App mit Blazor</span><span class="sxs-lookup"><span data-stu-id="2dc2d-234">Create your first Teams app with Blazor</span></span>](first-app-blazor.md)
- [<span data-ttu-id="2dc2d-235">Erstellen Ihrer ersten Teams-App mithilfe SharePoint-Framework (SPFx)</span><span class="sxs-lookup"><span data-stu-id="2dc2d-235">Create your first Teams app using SharePoint Framework (SPFx)</span></span>](first-app-spfx.md)
- [<span data-ttu-id="2dc2d-236">Erstellen einer Unterhaltungsbot-App</span><span class="sxs-lookup"><span data-stu-id="2dc2d-236">Create a conversational bot app</span></span>](first-app-bot.md)
- [<span data-ttu-id="2dc2d-237">Erstellen einer Messaging-Erweiterung</span><span class="sxs-lookup"><span data-stu-id="2dc2d-237">Create a messaging extension</span></span>](first-message-extension.md)
