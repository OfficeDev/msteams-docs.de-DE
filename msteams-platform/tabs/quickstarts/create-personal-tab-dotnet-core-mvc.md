---
title: Erstellen sie eine persönliche Registerkarte mit ASP. NET Core MVC
author: laujan
description: Eine Schnellstartanleitung zum Erstellen einer benutzerdefinierten persönlichen Registerkarte mit ASP. NET Core MVC.
localization_priority: Normal
ms.topic: quickstart
ms.author: lajanuar
ms.openlocfilehash: 3ec6b5c054384653e30e46cbffed4a2af6662c33
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2021
ms.locfileid: "52019566"
---
# <a name="create-a-custom-personal-tab-with-asp-net-core-mvc"></a><span data-ttu-id="aef59-105">Erstellen Sie eine benutzerdefinierte persönliche Registerkarte mit ASP.</span><span class="sxs-lookup"><span data-stu-id="aef59-105">Create a Custom Personal Tab with ASP.</span></span> <span data-ttu-id="aef59-106">NET Core MVC</span><span class="sxs-lookup"><span data-stu-id="aef59-106">NET Core MVC</span></span>

<span data-ttu-id="aef59-107">In diesem Schnellstart werden wir durch das Erstellen einer benutzerdefinierten persönlichen Registerkarte mit C# ASP gehen.</span><span class="sxs-lookup"><span data-stu-id="aef59-107">In this quickstart we'll walk-through creating a custom personal tab with C# and ASP.</span></span> <span data-ttu-id="aef59-108">Net Core MVC.</span><span class="sxs-lookup"><span data-stu-id="aef59-108">Net Core MVC.</span></span> <span data-ttu-id="aef59-109">Außerdem verwenden wir [App Studio für Microsoft Teams,](~/concepts/build-and-test/app-studio-overview.md) um Ihr App-Manifest zu finalisieren und Ihre Registerkarte für die Teams.</span><span class="sxs-lookup"><span data-stu-id="aef59-109">We'll also use [App Studio for Microsoft Teams](~/concepts/build-and-test/app-studio-overview.md) to finalize your app manifest and deploy your tab to Teams.</span></span>

[!INCLUDE [dotnet-core-prereq](~/includes/tabs/dotnet-core-prereq.md)]

## <a name="get-the-source-code"></a><span data-ttu-id="aef59-110">Den Quellcode erhalten</span><span class="sxs-lookup"><span data-stu-id="aef59-110">Get the source code</span></span>

<span data-ttu-id="aef59-111">Öffnen Sie eine Eingabeaufforderung, und erstellen Sie ein neues Verzeichnis für Ihr Registerkartenprojekt.</span><span class="sxs-lookup"><span data-stu-id="aef59-111">Open a command prompt and create a new directory for your tab project.</span></span> <span data-ttu-id="aef59-112">Wir haben ein einfaches Projekt bereitgestellt, mit dem Sie beginnen können.</span><span class="sxs-lookup"><span data-stu-id="aef59-112">We have provided a simple project to get you started.</span></span> <span data-ttu-id="aef59-113">Zum Abrufen des Quellcodes können Sie den Zip-Ordner herunterladen und die Dateien extrahieren oder das Beispielrepository in Ihr neues Verzeichnis klonen:</span><span class="sxs-lookup"><span data-stu-id="aef59-113">To retrieve the source code you can download the zip folder and extract the files or clone the sample repository into your new directory:</span></span>

``` bash
git clone https://github.com/OfficeDev/microsoft-teams-sample-tabs.git
```

<span data-ttu-id="aef59-114">Nachdem Sie den Quellcode verwendet haben, öffnen Sie Visual Studio, und wählen **Sie Projekt oder Projektmappe öffnen aus.**</span><span class="sxs-lookup"><span data-stu-id="aef59-114">Once you have the source code, open Visual Studio and select **Open a project or solution**.</span></span> <span data-ttu-id="aef59-115">Navigieren Sie zum Verzeichnis der Registerkartenanwendung, und öffnen **Sie PersonalTabMVC.sln**.</span><span class="sxs-lookup"><span data-stu-id="aef59-115">Navigate to the tab application directory and open **PersonalTabMVC.sln**.</span></span>

<span data-ttu-id="aef59-116">Drücken Sie **F5,** um die Anwendung zu erstellen und auszuführen, oder wählen Sie **Debuggen starten** im Menü **Debuggen** aus.</span><span class="sxs-lookup"><span data-stu-id="aef59-116">To build and run your application press **F5** or choose **Start Debugging** from the **Debug** menu.</span></span> <span data-ttu-id="aef59-117">Navigieren Sie in einem Browser zu den folgenden URLs, um zu überprüfen, ob die Anwendung ordnungsgemäß geladen wurde:</span><span class="sxs-lookup"><span data-stu-id="aef59-117">In a browser navigate to the URLs below to verify that the application loaded properly:</span></span>

* `http://localhost:44335`
* `http://localhost:44335/privacy`
* `http://localhost:44335/tou`

## <a name="review-the-source-code"></a><span data-ttu-id="aef59-118">Überprüfen des Quellcodes</span><span class="sxs-lookup"><span data-stu-id="aef59-118">Review the source code</span></span>

### <a name="startupcs"></a><span data-ttu-id="aef59-119">Startup.cs</span><span class="sxs-lookup"><span data-stu-id="aef59-119">Startup.cs</span></span>

<span data-ttu-id="aef59-120">Dieses Projekt wurde aus einem ASP erstellt.</span><span class="sxs-lookup"><span data-stu-id="aef59-120">This project was created from an ASP.</span></span> <span data-ttu-id="aef59-121">Leere Vorlage für NET Core 2.2-Webanwendung mit dem Kontrollkästchen Erweitert – Konfigurieren für *HTTPS,* das beim Setup aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="aef59-121">NET Core 2.2 Web Application empty template with the *Advanced - Configure for HTTPS* check box selected at setup.</span></span> <span data-ttu-id="aef59-122">Die MVC-Dienste werden von der Methode des Abhängigkeitsinjektionsframeworks `ConfigureServices()` registriert.</span><span class="sxs-lookup"><span data-stu-id="aef59-122">The MVC services are registered by the dependency injection framework's `ConfigureServices()` method.</span></span> <span data-ttu-id="aef59-123">Darüber hinaus ermöglicht die leere Vorlage die Standardmäßige Entladung statischer Inhalte nicht, sodass die Middleware für statische Dateien der Methode hinzugefügt `Configure()` wird:</span><span class="sxs-lookup"><span data-stu-id="aef59-123">Additionally, the empty template doesn't enable serving static content by default, so the static files middleware is added to the `Configure()` method:</span></span>

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

### <a name="wwwroot-folder"></a><span data-ttu-id="aef59-124">Ordner "wwwroot"</span><span class="sxs-lookup"><span data-stu-id="aef59-124">wwwroot folder</span></span>

<span data-ttu-id="aef59-125">In ASP.</span><span class="sxs-lookup"><span data-stu-id="aef59-125">In ASP.</span></span> <span data-ttu-id="aef59-126">NET Core: Im Webstammordner sucht die Anwendung nach statischen Dateien.</span><span class="sxs-lookup"><span data-stu-id="aef59-126">NET Core, the web root folder is where the application looks for static files.</span></span>

### <a name="appmanifest-folder"></a><span data-ttu-id="aef59-127">Ordner "AppManifest"</span><span class="sxs-lookup"><span data-stu-id="aef59-127">AppManifest folder</span></span>

<span data-ttu-id="aef59-128">Dieser Ordner enthält die folgenden erforderlichen App-Paketdateien:</span><span class="sxs-lookup"><span data-stu-id="aef59-128">This folder contains the following required app package files:</span></span>

* <span data-ttu-id="aef59-129">Ein **Vollfarbsymbol** mit einer Breite von 192 x 192 Pixeln.</span><span class="sxs-lookup"><span data-stu-id="aef59-129">A **full color icon** measuring 192 x 192 pixels.</span></span>
* <span data-ttu-id="aef59-130">Ein **transparentes Gliederungssymbol** mit einer Breite von 32 x 32 Pixeln.</span><span class="sxs-lookup"><span data-stu-id="aef59-130">A **transparent outline icon** measuring 32 x 32 pixels.</span></span>
* <span data-ttu-id="aef59-131">Eine **manifest.json-Datei,** die die Attribute Ihrer App angibt.</span><span class="sxs-lookup"><span data-stu-id="aef59-131">A **manifest.json** file that specifies the attributes of your app.</span></span>

<span data-ttu-id="aef59-132">Diese Dateien müssen in einem App-Paket gezippt werden, damit sie zum Hochladen Ihrer Registerkarte in das Teams.</span><span class="sxs-lookup"><span data-stu-id="aef59-132">These files need to be zipped in an app package for use in uploading your tab to Teams.</span></span> <span data-ttu-id="aef59-133">Microsoft Teams laden das in Ihrem Manifest angegebene, betten Sie es in einen `contentUrl` IFrame ein, und rendern Sie es auf Ihrer Registerkarte.</span><span class="sxs-lookup"><span data-stu-id="aef59-133">Microsoft Teams will load the `contentUrl` specified in your manifest, embed it in an IFrame, and render it in your tab.</span></span>

### <a name="csproj"></a><span data-ttu-id="aef59-134">.csproj</span><span class="sxs-lookup"><span data-stu-id="aef59-134">.csproj</span></span>

<span data-ttu-id="aef59-135">Klicken Sie Visual Studio Projektmappen-Explorer mit der rechten Maustaste auf das Projekt, und wählen Sie **Bearbeiten Project Datei aus.**</span><span class="sxs-lookup"><span data-stu-id="aef59-135">In the Visual Studio Solution Explorer window right-click on the project and select **Edit Project File**.</span></span> <span data-ttu-id="aef59-136">Unten in der Datei wird der Code angezeigt, mit dem Ihr ZIP-Ordner erstellt und aktualisiert wird, wenn die Anwendung erstellt:</span><span class="sxs-lookup"><span data-stu-id="aef59-136">At the bottom of the file you'll see the code that creates and updates your zip folder when the application builds:</span></span>

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

### <a name="models"></a><span data-ttu-id="aef59-137">Modelle</span><span class="sxs-lookup"><span data-stu-id="aef59-137">Models</span></span>

<span data-ttu-id="aef59-138">*PersonalTab.cs* stellt ein Message-Objekt und Methoden vor, die von *PersonalTabController* aufgerufen werden, wenn ein Benutzer eine Schaltfläche in der *PersonalTab-Ansicht* auswählt.</span><span class="sxs-lookup"><span data-stu-id="aef59-138">*PersonalTab.cs* presents a Message object and methods that will be called from *PersonalTabController* when a user selects a button in the *PersonalTab* View.</span></span>

### <a name="views"></a><span data-ttu-id="aef59-139">Ansichten</span><span class="sxs-lookup"><span data-stu-id="aef59-139">Views</span></span>

#### <a name="home"></a><span data-ttu-id="aef59-140">Start</span><span class="sxs-lookup"><span data-stu-id="aef59-140">Home</span></span>

<span data-ttu-id="aef59-141">ASP.</span><span class="sxs-lookup"><span data-stu-id="aef59-141">ASP.</span></span> <span data-ttu-id="aef59-142">NET Core behandelt Dateien mit dem Namen *Index* als Standard-/Homepage für die Website.</span><span class="sxs-lookup"><span data-stu-id="aef59-142">NET Core treats files called *Index* as the default/home page for the site.</span></span> <span data-ttu-id="aef59-143">Wenn Ihre Browser-URL auf den Stamm der Website verweist, wird *Index.cshtml* als Homepage für Ihre Anwendung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="aef59-143">When your browser URL points to the root of the site, *Index.cshtml* will be displayed as the home page for your application.</span></span>

#### <a name="shared"></a><span data-ttu-id="aef59-144">Shared</span><span class="sxs-lookup"><span data-stu-id="aef59-144">Shared</span></span>

<span data-ttu-id="aef59-145">Das Teilansichts *markup _Layout.cshtml* enthält die allgemeine Seitenstruktur der Anwendung und freigegebene visuelle Elemente.</span><span class="sxs-lookup"><span data-stu-id="aef59-145">The partial view markup *_Layout.cshtml* contains the application's overall page structure and shared visual elements.</span></span> <span data-ttu-id="aef59-146">Außerdem wird auf die Teams verwiesen.</span><span class="sxs-lookup"><span data-stu-id="aef59-146">It will also reference the Teams Library.</span></span>

### <a name="controllers"></a><span data-ttu-id="aef59-147">Controller</span><span class="sxs-lookup"><span data-stu-id="aef59-147">Controllers</span></span>

<span data-ttu-id="aef59-148">Die Controller verwenden die ViewBag-Eigenschaft, um Werte dynamisch in die Ansichten zu übertragen.</span><span class="sxs-lookup"><span data-stu-id="aef59-148">The controllers use the ViewBag property to transfer values dynamically to the Views.</span></span>

[!INCLUDE [dotnet-update-personal-app](~/includes/tabs/dotnet-update-personal-app.md)]

[!INCLUDE [dotnet-ngrok-intro](~/includes/tabs/dotnet-ngrok-intro.md)]

* <span data-ttu-id="aef59-149">Öffnen Sie eine Eingabeaufforderung im Stammverzeichnis Ihres Projektverzeichnisses, und führen Sie den folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="aef59-149">Open a command prompt in the root of your project directory and run the following command:</span></span>

``` bash
ngrok http https://localhost:44345 -host-header="localhost:44345"
```

* <span data-ttu-id="aef59-150">Ngrok lauscht Anforderungen aus dem Internet und führt sie an Ihre Anwendung weiter, wenn sie an Port 44325 ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="aef59-150">Ngrok will listen to requests from the internet and will route them to your application when it is running on port 44325.</span></span>  <span data-ttu-id="aef59-151">Es sollte so `https://y8rPrT2b.ngrok.io/` aussehen, *dass y8rPrT2b* durch Ihre ngrok-alphanumerische HTTPS-URL ersetzt wird.</span><span class="sxs-lookup"><span data-stu-id="aef59-151">It should resemble `https://y8rPrT2b.ngrok.io/` where *y8rPrT2b* is replaced by your ngrok alpha-numeric HTTPS URL.</span></span>

* <span data-ttu-id="aef59-152">Achten Sie darauf, dass die Eingabeaufforderung mit ngrok ausgeführt wird, und notieren Sie sich die URL – Sie benötigen sie später.</span><span class="sxs-lookup"><span data-stu-id="aef59-152">Be sure to keep the command prompt with ngrok running, and to make a note of the URL — you'll need it later.</span></span>

* <span data-ttu-id="aef59-153">Stellen Sie sicher, dass *ngrok* ordnungsgemäß ausgeführt und funktioniert, indem Sie Ihren Browser öffnen und über die ngrok-HTTPS-URL, die im Eingabeaufforderungsfenster bereitgestellt wurde, zu Ihrer Inhaltsseite wechseln.</span><span class="sxs-lookup"><span data-stu-id="aef59-153">Verify that *ngrok* is running and working properly by opening your browser and going to your content page via the ngrok HTTPS URL that was provided in your command prompt window.</span></span>

> <span data-ttu-id="aef59-154">[!</span><span class="sxs-lookup"><span data-stu-id="aef59-154">[!</span></span> <span data-ttu-id="aef59-155">TIPP] Sie müssen ihre Anwendung in Visual Studio und ngrok ausführen, um diesen Schnellstart ausführen zu können.</span><span class="sxs-lookup"><span data-stu-id="aef59-155">TIP] You need to have both your application in Visual Studio and ngrok running to complete this quickstart.</span></span> <span data-ttu-id="aef59-156">Wenn Sie die Ausführung Ihrer Anwendung in Visual Studio ausführen müssen, halten Sie **ngrok am Laufen.**</span><span class="sxs-lookup"><span data-stu-id="aef59-156">If you need to stop running your application in Visual Studio to work on it, **keep ngrok running**.</span></span> <span data-ttu-id="aef59-157">Sie lauscht weiterhin und setzt das Routing der Anforderung Ihrer Anwendung fort, wenn sie in einem Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="aef59-157">It will continue to listen and will resume routing your application's request when it restarts in Visual Studio.</span></span> <span data-ttu-id="aef59-158">Wenn Sie den ngrok-Dienst neu starten müssen, gibt er eine neue URL zurück, und Sie müssen jeden Ort aktualisieren, der diese URL verwendet.</span><span class="sxs-lookup"><span data-stu-id="aef59-158">If you have to restart the ngrok service it will return a new URL and you'll have to update every place that uses that URL.</span></span>

### <a name="run-your-application"></a><span data-ttu-id="aef59-159">Ausführen der Anwendung</span><span class="sxs-lookup"><span data-stu-id="aef59-159">Run your application</span></span>

* <span data-ttu-id="aef59-160">Drücken Visual Studio **F5,** oder wählen Sie **Debuggen starten** im Menü **Debuggen** Ihrer Anwendung aus.</span><span class="sxs-lookup"><span data-stu-id="aef59-160">In Visual Studio press **F5** or choose **Start Debugging** from your application's **Debug** menu.</span></span>

[!INCLUDE [dotnet-personal-use-appstudio](~/includes/tabs/dotnet-personal-use-appstudio.md)]
