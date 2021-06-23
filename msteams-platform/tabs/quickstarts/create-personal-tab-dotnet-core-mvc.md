---
title: Erstellen Sie eine persönliche Registerkarte mit ASP. NET Core MVC
author: surbhigupta
description: Eine Schnellstartanleitung zum Erstellen einer benutzerdefinierten persönlichen Registerkarte mit ASP. NET Core MVC.
localization_priority: Normal
ms.topic: quickstart
ms.author: lajanuar
ms.openlocfilehash: ac01ae64f44ccf3e06476d4412b16ac9a4730f6c
ms.sourcegitcommit: 623d81eb079d1842813265746a5fe0fe6311b196
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/22/2021
ms.locfileid: "53069151"
---
# <a name="create-a-custom-personal-tab-with-aspnet-core-mvc"></a><span data-ttu-id="a27bc-105">Erstellen einer benutzerdefinierten persönlichen Registerkarte mit ASP.NET Core MVC</span><span class="sxs-lookup"><span data-stu-id="a27bc-105">Create a Custom Personal Tab with ASP.NET Core MVC</span></span>

<span data-ttu-id="a27bc-106">In dieser Schnellstartanleitung werden wir schrittweise durch das Erstellen einer benutzerdefinierten persönlichen Registerkarte mit C# und ASP.Net Core MVC geführt.</span><span class="sxs-lookup"><span data-stu-id="a27bc-106">In this quickstart we'll walk-through creating a custom personal tab with C# and ASP.Net Core MVC.</span></span> <span data-ttu-id="a27bc-107">Wir verwenden App Studio auch [für Microsoft Teams,](~/concepts/build-and-test/app-studio-overview.md) um Ihr App-Manifest fertig zu stellen und Ihre Registerkarte für Teams bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="a27bc-107">We'll also use [App Studio for Microsoft Teams](~/concepts/build-and-test/app-studio-overview.md) to finalize your app manifest and deploy your tab to Teams.</span></span>

[!INCLUDE [dotnet-core-prereq](~/includes/tabs/dotnet-core-prereq.md)]

## <a name="get-the-source-code"></a><span data-ttu-id="a27bc-108">Abrufen des Quellcodes</span><span class="sxs-lookup"><span data-stu-id="a27bc-108">Get the source code</span></span>

<span data-ttu-id="a27bc-109">Öffnen Sie eine Eingabeaufforderung, und erstellen Sie ein neues Verzeichnis für Ihr Registerkartenprojekt.</span><span class="sxs-lookup"><span data-stu-id="a27bc-109">Open a command prompt and create a new directory for your tab project.</span></span> <span data-ttu-id="a27bc-110">Wir haben ein einfaches Projekt bereitgestellt, um Ihnen den Einstieg zu erleichtern.</span><span class="sxs-lookup"><span data-stu-id="a27bc-110">We have provided a simple project to get you started.</span></span> <span data-ttu-id="a27bc-111">Um den Quellcode abzurufen, können Sie den ZIP-Ordner herunterladen und die Dateien extrahieren oder das Beispiel-Repository in Ihr neues Verzeichnis klonen:</span><span class="sxs-lookup"><span data-stu-id="a27bc-111">To retrieve the source code you can download the zip folder and extract the files or clone the sample repository into your new directory:</span></span>

``` bash
git clone https://github.com/OfficeDev/microsoft-teams-sample-tabs.git
```

<span data-ttu-id="a27bc-112">Sobald Sie den Quellcode haben, öffnen Sie Visual Studio, und wählen Sie **Projekt oder Projektmappe öffnen** aus.</span><span class="sxs-lookup"><span data-stu-id="a27bc-112">Once you have the source code, open Visual Studio and select **Open a project or solution**.</span></span> <span data-ttu-id="a27bc-113">Navigieren Sie zum Registerkartenanwendungsverzeichnis, und öffnen Sie **PersonalTabMVC.sln**.</span><span class="sxs-lookup"><span data-stu-id="a27bc-113">Navigate to the tab application directory and open **PersonalTabMVC.sln**.</span></span>

<span data-ttu-id="a27bc-114">Drücken Sie **F5,** oder wählen Sie im Menü **"Debuggen"** die Option **"Debuggen starten"** aus, um die Anwendung zu erstellen und auszuführen.</span><span class="sxs-lookup"><span data-stu-id="a27bc-114">To build and run your application press **F5** or choose **Start Debugging** from the **Debug** menu.</span></span> <span data-ttu-id="a27bc-115">Navigieren Sie in einem Browser zu den folgenden URLs, um zu überprüfen, ob die Anwendung ordnungsgemäß geladen wurde:</span><span class="sxs-lookup"><span data-stu-id="a27bc-115">In a browser navigate to the URLs below to verify that the application loaded properly:</span></span>

* `http://localhost:44335`
* `http://localhost:44335/privacy`
* `http://localhost:44335/tou`

## <a name="review-the-source-code"></a><span data-ttu-id="a27bc-116">Überprüfen des Quellcodes</span><span class="sxs-lookup"><span data-stu-id="a27bc-116">Review the source code</span></span>

### <a name="startupcs"></a><span data-ttu-id="a27bc-117">Startup.cs</span><span class="sxs-lookup"><span data-stu-id="a27bc-117">Startup.cs</span></span>

<span data-ttu-id="a27bc-118">Dieses Projekt wurde aus einem ASP erstellt.</span><span class="sxs-lookup"><span data-stu-id="a27bc-118">This project was created from an ASP.</span></span> <span data-ttu-id="a27bc-119">Leere Vorlage der NET Core 2.2-Webanwendung mit dem Kontrollkästchen *"Erweitert – Für HTTPS konfigurieren"* beim Setup aktiviert.</span><span class="sxs-lookup"><span data-stu-id="a27bc-119">NET Core 2.2 Web Application empty template with the *Advanced - Configure for HTTPS* check box selected at setup.</span></span> <span data-ttu-id="a27bc-120">Die MVC-Dienste werden durch die Methode des Abhängigkeitsinjektionsframeworks `ConfigureServices()` registriert.</span><span class="sxs-lookup"><span data-stu-id="a27bc-120">The MVC services are registered by the dependency injection framework's `ConfigureServices()` method.</span></span> <span data-ttu-id="a27bc-121">Darüber hinaus ermöglicht die leere Vorlage nicht standardmäßig die Bereitstellung statischer Inhalte, sodass die Middleware für statische Dateien der Methode hinzugefügt `Configure()` wird:</span><span class="sxs-lookup"><span data-stu-id="a27bc-121">Additionally, the empty template doesn't enable serving static content by default, so the static files middleware is added to the `Configure()` method:</span></span>

``` csharp
public void ConfigureServices(IServiceCollection services)
  {
    services.AddMvc().SetCompatibilityVersion(CompatibilityVersion.Version_2_2);
  }
public void Configure(IApplicationBuilder app)
  {
    app.UseStaticFiles();
    app.UseMvc();
  }
```

### <a name="wwwroot-folder"></a><span data-ttu-id="a27bc-122">Wwwroot-Ordner</span><span class="sxs-lookup"><span data-stu-id="a27bc-122">wwwroot folder</span></span>

<span data-ttu-id="a27bc-123">In ASP.</span><span class="sxs-lookup"><span data-stu-id="a27bc-123">In ASP.</span></span> <span data-ttu-id="a27bc-124">NET Core, der Webstammordner, in dem die Anwendung nach statischen Dateien sucht.</span><span class="sxs-lookup"><span data-stu-id="a27bc-124">NET Core, the web root folder is where the application looks for static files.</span></span>

### <a name="appmanifest-folder"></a><span data-ttu-id="a27bc-125">AppManifest-Ordner</span><span class="sxs-lookup"><span data-stu-id="a27bc-125">AppManifest folder</span></span>

<span data-ttu-id="a27bc-126">Dieser Ordner enthält die folgenden erforderlichen App-Paketdateien:</span><span class="sxs-lookup"><span data-stu-id="a27bc-126">This folder contains the following required app package files:</span></span>

* <span data-ttu-id="a27bc-127">Ein **Vollfarbsymbol** mit einer Auflösung von 192 x 192 Pixeln.</span><span class="sxs-lookup"><span data-stu-id="a27bc-127">A **full color icon** measuring 192 x 192 pixels.</span></span>
* <span data-ttu-id="a27bc-128">Ein **transparentes Gliederungssymbol** mit einer Auflösung von 32 x 32 Pixeln.</span><span class="sxs-lookup"><span data-stu-id="a27bc-128">A **transparent outline icon** measuring 32 x 32 pixels.</span></span>
* <span data-ttu-id="a27bc-129">Ein **manifest.jsfür** die Datei, die die Attribute Ihrer App angibt.</span><span class="sxs-lookup"><span data-stu-id="a27bc-129">A **manifest.json** file that specifies the attributes of your app.</span></span>

<span data-ttu-id="a27bc-130">Diese Dateien müssen in einem App-Paket gezippt werden, um Ihre Registerkarte in Teams hochzuladen.</span><span class="sxs-lookup"><span data-stu-id="a27bc-130">These files need to be zipped in an app package for use in uploading your tab to Teams.</span></span> <span data-ttu-id="a27bc-131">Microsoft Teams lädt das `contentUrl` angegebene Element in Ihrem Manifest, betten es in einen IFrame ein und rendert es auf der Registerkarte.</span><span class="sxs-lookup"><span data-stu-id="a27bc-131">Microsoft Teams will load the `contentUrl` specified in your manifest, embed it in an IFrame, and render it in your tab.</span></span>

### <a name="csproj"></a><span data-ttu-id="a27bc-132">CSPROJ</span><span class="sxs-lookup"><span data-stu-id="a27bc-132">.csproj</span></span>

<span data-ttu-id="a27bc-133">Klicken Sie im Fenster Visual Studio Projektmappen-Explorer mit der rechten Maustaste auf das Projekt, und wählen Sie **"Bearbeiten Project Datei"** aus.</span><span class="sxs-lookup"><span data-stu-id="a27bc-133">In the Visual Studio Solution Explorer window right-click on the project and select **Edit Project File**.</span></span> <span data-ttu-id="a27bc-134">Am Ende der Datei sehen Sie den Code, der Ihren ZIP-Ordner erstellt und aktualisiert, wenn die Anwendung erstellt wird:</span><span class="sxs-lookup"><span data-stu-id="a27bc-134">At the bottom of the file you'll see the code that creates and updates your zip folder when the application builds:</span></span>

``` xml
<PropertyGroup>
    <PostBuildEvent>powershell.exe Compress-Archive -Path \"$(ProjectDir)AppManifest\*\" -DestinationPath \"$(TargetDir)tab.zip\" -Force</PostBuildEvent>
  </PropertyGroup>

  <ItemGroup>
    <EmbeddedResource Include="AppManifest\icon-outline.png">
      <CopyToOutputDirectory>Always</CopyToOutputDirectory>
    </EmbeddedResource>
    <EmbeddedResource Include="AppManifest\icon-color.png">
      <CopyToOutputDirectory>Always</CopyToOutputDirectory>
    </EmbeddedResource>
    <EmbeddedResource Include="AppManifest\manifest.json">
      <CopyToOutputDirectory>Always</CopyToOutputDirectory>
    </EmbeddedResource>
  </ItemGroup>
```

### <a name="models"></a><span data-ttu-id="a27bc-135">Modelle</span><span class="sxs-lookup"><span data-stu-id="a27bc-135">Models</span></span>

<span data-ttu-id="a27bc-136">**PersonalTab.cs** stellt ein Message-Objekt und Methoden dar, die von *PersonalTabController* aufgerufen werden, wenn ein Benutzer eine Schaltfläche in der **PersonalTab-Ansicht auswählt.**</span><span class="sxs-lookup"><span data-stu-id="a27bc-136">**PersonalTab.cs** presents a Message object and methods that will be called from *PersonalTabController* when a user selects a button in the **PersonalTab** View.</span></span>

### <a name="views"></a><span data-ttu-id="a27bc-137">Ansichten</span><span class="sxs-lookup"><span data-stu-id="a27bc-137">Views</span></span>

#### <a name="home"></a><span data-ttu-id="a27bc-138">Start</span><span class="sxs-lookup"><span data-stu-id="a27bc-138">Home</span></span>

<span data-ttu-id="a27bc-139">Asp.</span><span class="sxs-lookup"><span data-stu-id="a27bc-139">ASP.</span></span> <span data-ttu-id="a27bc-140">NET Core behandelt Dateien mit dem Namen **Index** als Standard- oder Startseite für die Website.</span><span class="sxs-lookup"><span data-stu-id="a27bc-140">NET Core treats files called **Index** as the default or home page for the site.</span></span> <span data-ttu-id="a27bc-141">Wenn Ihre Browser-URL auf den Stamm der Website zeigt, wird **Index.cshtml** als Startseite für Ihre Anwendung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="a27bc-141">When your browser URL points to the root of the site, **Index.cshtml** will be displayed as the home page for your application.</span></span>

#### <a name="shared"></a><span data-ttu-id="a27bc-142">Shared</span><span class="sxs-lookup"><span data-stu-id="a27bc-142">Shared</span></span>

<span data-ttu-id="a27bc-143">Das Partielle Ansichtsmarkup *_Layout.cshtml* enthält die allgemeine Seitenstruktur der Anwendung und freigegebene visuelle Elemente.</span><span class="sxs-lookup"><span data-stu-id="a27bc-143">The partial view markup *_Layout.cshtml* contains the application's overall page structure and shared visual elements.</span></span> <span data-ttu-id="a27bc-144">Außerdem wird auf die Teams Bibliothek verwiesen.</span><span class="sxs-lookup"><span data-stu-id="a27bc-144">It will also reference the Teams Library.</span></span>

### <a name="controllers"></a><span data-ttu-id="a27bc-145">Controller</span><span class="sxs-lookup"><span data-stu-id="a27bc-145">Controllers</span></span>

<span data-ttu-id="a27bc-146">Die Controller verwenden die ViewBag-Eigenschaft, um Werte dynamisch in die Ansichten zu übertragen.</span><span class="sxs-lookup"><span data-stu-id="a27bc-146">The controllers use the ViewBag property to transfer values dynamically to the Views.</span></span>

[!INCLUDE [dotnet-update-personal-app](~/includes/tabs/dotnet-update-personal-app.md)]

[!INCLUDE [dotnet-ngrok-intro](~/includes/tabs/dotnet-ngrok-intro.md)]

* <span data-ttu-id="a27bc-147">Öffnen Sie eine Eingabeaufforderung im Stammverzeichnis des Projekts, und führen Sie den folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="a27bc-147">Open a command prompt in the root of your project directory and run the following command:</span></span>

    ``` bash
    ngrok http https://localhost:44345 -host-header="localhost:44345"
    ```

* <span data-ttu-id="a27bc-148">Ngrok lauscht auf Anforderungen aus dem Internet und leitet sie an Ihre Anwendung weiter, wenn sie an Port 44325 ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="a27bc-148">Ngrok will listen to requests from the internet and will route them to your application when it is running on port 44325.</span></span>  <span data-ttu-id="a27bc-149">Es sollte etwa so `https://y8rPrT2b.ngrok.io/` aussehen, wo *y8rPrT2b* durch Ihre alphangrok-numerische HTTPS-URL ersetzt wird.</span><span class="sxs-lookup"><span data-stu-id="a27bc-149">It should resemble `https://y8rPrT2b.ngrok.io/` where *y8rPrT2b* is replaced by your ngrok alpha-numeric HTTPS URL.</span></span>

* <span data-ttu-id="a27bc-150">Achten Sie darauf, dass die Eingabeaufforderung mit ngrok ausgeführt wird, und notieren Sie sich die URL . Sie benötigen sie später.</span><span class="sxs-lookup"><span data-stu-id="a27bc-150">Be sure to keep the command prompt with ngrok running, and to make a note of the URL — you'll need it later.</span></span>

* <span data-ttu-id="a27bc-151">Stellen Sie sicher, dass **ngrok** ausgeführt wird und ordnungsgemäß funktioniert, indem Sie Ihren Browser öffnen und über die ngrok-HTTPS-URL, die im Eingabeaufforderungsfenster bereitgestellt wurde, zur Inhaltsseite wechseln.</span><span class="sxs-lookup"><span data-stu-id="a27bc-151">Verify that **ngrok** is running and working properly by opening your browser and going to your content page via the ngrok HTTPS URL that was provided in your command prompt window.</span></span>

> [!TIP]
> <span data-ttu-id="a27bc-152">Sie müssen ihre Anwendung sowohl in Visual Studio als auch in ngrok ausführen, um diese Schnellstartanleitung abzuschließen.</span><span class="sxs-lookup"><span data-stu-id="a27bc-152">You need to have both your application in Visual Studio and ngrok running to complete this quickstart.</span></span> <span data-ttu-id="a27bc-153">Wenn Sie die Ausführung der Anwendung in Visual Studio beenden müssen, um daran zu arbeiten, **führen Sie ngrok weiter aus.**</span><span class="sxs-lookup"><span data-stu-id="a27bc-153">If you need to stop running your application in Visual Studio to work on it, **keep ngrok running**.</span></span> <span data-ttu-id="a27bc-154">Sie lauscht weiterhin und setzt das Routing der Anforderung Ihrer Anwendung fort, wenn sie in Visual Studio neu gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="a27bc-154">It will continue to listen and will resume routing your application's request when it restarts in Visual Studio.</span></span> <span data-ttu-id="a27bc-155">Wenn Sie den ngrok-Dienst neu starten müssen, wird eine neue URL zurückgegeben, und Sie müssen jeden Ort aktualisieren, der diese URL verwendet.</span><span class="sxs-lookup"><span data-stu-id="a27bc-155">If you have to restart the ngrok service it will return a new URL and you'll have to update every place that uses that URL.</span></span>

### <a name="run-your-application"></a><span data-ttu-id="a27bc-156">Ausführen der Anwendung</span><span class="sxs-lookup"><span data-stu-id="a27bc-156">Run your application</span></span>

* <span data-ttu-id="a27bc-157">Drücken Sie in Visual Studio **F5,** oder wählen Sie **"Debuggen starten"** aus dem **Menü "Debuggen"** der Anwendung aus.</span><span class="sxs-lookup"><span data-stu-id="a27bc-157">In Visual Studio press **F5** or choose **Start Debugging** from your application's **Debug** menu.</span></span>

[!INCLUDE [dotnet-personal-use-appstudio](~/includes/tabs/dotnet-personal-use-appstudio.md)]

## <a name="next-step"></a><span data-ttu-id="a27bc-158">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="a27bc-158">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="a27bc-159">Erstellen einer benutzerdefinierten Kanal- und Gruppenregisterkarte mit Node.js und dem Yeoman-Generator für Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="a27bc-159">Create a custom channel and group tab using Node.js and the Yeoman Generator for Microsoft Teams</span></span>](~/tabs/quickstarts/create-channel-group-tab-node-yeoman.md)
