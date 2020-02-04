---
title: Erstellen Sie eine persönliche Registerkarte mit ASP. NET-Core-MVC
author: laujan
description: Eine Schnellstartanleitung zum Erstellen einer benutzerdefinierten persönlichen Registerkarte mit ASP. NET-Kern-MVC.
ms.topic: quickstart
ms.author: laujan
ms.openlocfilehash: 3bdd23692eca5ff3f6fc3f82cdaa233d34d4c69f
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674080"
---
# <a name="create-a-custom-personal-tab-with-asp-net-core-mvc"></a><span data-ttu-id="5802c-105">Erstellen einer benutzerdefinierten persönlichen Registerkarte mit ASP.</span><span class="sxs-lookup"><span data-stu-id="5802c-105">Create a Custom Personal Tab with ASP.</span></span> <span data-ttu-id="5802c-106">NET-Core-MVC</span><span class="sxs-lookup"><span data-stu-id="5802c-106">NET Core MVC</span></span>

<span data-ttu-id="5802c-107">In diesem Schnellstart werden Sie durch das Erstellen einer benutzerdefinierten persönlichen Registerkarte mit C# und ASP durchlaufen.</span><span class="sxs-lookup"><span data-stu-id="5802c-107">In this quickstart we'll walk-through creating a custom personal tab with C# and ASP.</span></span> <span data-ttu-id="5802c-108">NET-Kern-MVC.</span><span class="sxs-lookup"><span data-stu-id="5802c-108">Net Core MVC.</span></span> <span data-ttu-id="5802c-109">Wir verwenden auch [App Studio für Microsoft Teams](~/concepts/build-and-test/app-studio-overview.md) , um Ihr App-Manifest abzuschließen und die Registerkarte in Teams bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="5802c-109">We'll also use [App Studio for Microsoft Teams](~/concepts/build-and-test/app-studio-overview.md) to finalize your app manifest and deploy your tab to Teams.</span></span>

[!INCLUDE [dotnet-core-prereq](~/includes/tabs/dotnet-core-prereq.md)]

## <a name="get-the-source-code"></a><span data-ttu-id="5802c-110">Abrufen des Quellcodes</span><span class="sxs-lookup"><span data-stu-id="5802c-110">Get the source code</span></span>

<span data-ttu-id="5802c-111">Öffnen Sie eine Eingabeaufforderung, und erstellen Sie ein neues Verzeichnis für Ihr Tab-Projekt.</span><span class="sxs-lookup"><span data-stu-id="5802c-111">Open a command prompt and create a new directory for your tab project.</span></span> <span data-ttu-id="5802c-112">Wir haben ein einfaches Projekt zur Verfügung gestellt, damit Sie loslegen können.</span><span class="sxs-lookup"><span data-stu-id="5802c-112">We have provided a simple project to get you started.</span></span> <span data-ttu-id="5802c-113">Zum Abrufen des Quellcodes können Sie den ZIP-Ordner herunterladen und die Dateien extrahieren oder das Beispiel-Repository in Ihr neues Verzeichnis kopieren:</span><span class="sxs-lookup"><span data-stu-id="5802c-113">To retrieve the source code you can download the zip folder and extract the files or clone the sample repository into your new directory:</span></span>

``` bash
git clone https://github.com/OfficeDev/microsoft-teams-sample-tabs.git
```

<span data-ttu-id="5802c-114">Nachdem Sie den Quellcode haben, öffnen Sie Visual Studio, und wählen Sie **Projekt oder Lösung öffnen**aus.</span><span class="sxs-lookup"><span data-stu-id="5802c-114">Once you have the source code, open Visual Studio and select **Open a project or solution**.</span></span> <span data-ttu-id="5802c-115">Navigieren Sie zum Anwendungsverzeichnis der Registerkarte, und öffnen Sie **PersonalTabMVC. sln**.</span><span class="sxs-lookup"><span data-stu-id="5802c-115">Navigate to the tab application directory and open **PersonalTabMVC.sln**.</span></span>

<span data-ttu-id="5802c-116">Drücken Sie zum Erstellen und Ausführen der Anwendung **F5** , oder wählen Sie im Menü **Debuggen** die Option **Debuggen starten** aus.</span><span class="sxs-lookup"><span data-stu-id="5802c-116">To build and run your application press **F5** or choose **Start Debugging** from the **Debug** menu.</span></span> <span data-ttu-id="5802c-117">Navigieren Sie in einem Browser zu den folgenden URLs, um zu überprüfen, ob die Anwendung ordnungsgemäß geladen wurde:</span><span class="sxs-lookup"><span data-stu-id="5802c-117">In a browser navigate to the URLs below to verify that the application loaded properly:</span></span>

* `http://localhost:44335`
* `http://localhost:44335/privacy`
* `http://localhost:44335/tou`

## <a name="review-the-source-code"></a><span data-ttu-id="5802c-118">Überprüfen des Quellcodes</span><span class="sxs-lookup"><span data-stu-id="5802c-118">Review the source code</span></span>

### <a name="startupcs"></a><span data-ttu-id="5802c-119">Startup.cs</span><span class="sxs-lookup"><span data-stu-id="5802c-119">Startup.cs</span></span>

<span data-ttu-id="5802c-120">Dieses Projekt wurde aus einer ASP.</span><span class="sxs-lookup"><span data-stu-id="5802c-120">This project was created from an ASP.</span></span> <span data-ttu-id="5802c-121">NET Core 2,2-Webanwendung leere Vorlage, wobei das Kontrollkästchen *Erweiterte-configure for HTTPS* beim Setup aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="5802c-121">NET Core 2.2 Web Application empty template with the *Advanced - Configure for HTTPS* check box selected at setup.</span></span> <span data-ttu-id="5802c-122">Die MVC `ConfigureServices()` -Dienste werden von der Dependency Injection Framework-Methode registriert.</span><span class="sxs-lookup"><span data-stu-id="5802c-122">The MVC services are registered by the dependency injection framework's `ConfigureServices()` method.</span></span> <span data-ttu-id="5802c-123">Darüber hinaus wird die Bereitstellung statischer Inhalte nicht standardmäßig durch die leere Vorlage aktiviert, sodass der `Configure()` Methode die statische Datei Middleware hinzugefügt wird:</span><span class="sxs-lookup"><span data-stu-id="5802c-123">Additionally, the empty template doesn't enable serving static content by default, so the static files middleware is added to the `Configure()` method:</span></span>

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

### <a name="wwwroot-folder"></a><span data-ttu-id="5802c-124">WWWRoot-Ordner</span><span class="sxs-lookup"><span data-stu-id="5802c-124">wwwroot folder</span></span>

<span data-ttu-id="5802c-125">In ASP.</span><span class="sxs-lookup"><span data-stu-id="5802c-125">In ASP.</span></span> <span data-ttu-id="5802c-126">NET-Kern ist der Webstammordner der Ort, an dem die Anwendung nach statischen Dateien sucht.</span><span class="sxs-lookup"><span data-stu-id="5802c-126">NET Core, the web root folder is where the application looks for static files.</span></span>

### <a name="appmanifest-folder"></a><span data-ttu-id="5802c-127">AppManifest-Ordner</span><span class="sxs-lookup"><span data-stu-id="5802c-127">AppManifest folder</span></span>

<span data-ttu-id="5802c-128">Dieser Ordner enthält die folgenden erforderlichen App-Paketdateien:</span><span class="sxs-lookup"><span data-stu-id="5802c-128">This folder contains the following required app package files:</span></span>

* <span data-ttu-id="5802c-129">Ein **vollfarbiges Symbol** , das 192 x 192 Pixel misst.</span><span class="sxs-lookup"><span data-stu-id="5802c-129">A **full color icon** measuring 192 x 192 pixels.</span></span>
* <span data-ttu-id="5802c-130">Ein **transparentes Umrisssymbol** , das 32 x 32 Pixel misst.</span><span class="sxs-lookup"><span data-stu-id="5802c-130">A **transparent outline icon** measuring 32 x 32 pixels.</span></span>
* <span data-ttu-id="5802c-131">Eine **Manifest. JSON** -Datei, die die Attribute Ihrer APP angibt.</span><span class="sxs-lookup"><span data-stu-id="5802c-131">A **manifest.json** file that specifies the attributes of your app.</span></span>

<span data-ttu-id="5802c-132">Diese Dateien müssen in einem App-Paket gezippt werden, damit Sie Ihre Registerkarte in Microsoft Teams hochladen können.</span><span class="sxs-lookup"><span data-stu-id="5802c-132">These files need to be zipped in an app package for use in uploading your tab to Teams.</span></span> <span data-ttu-id="5802c-133">Microsoft Teams lädt das `contentUrl` angegebene in ihrem Manifest, bettet es in einen iframe ein und rendert es in ihrer Registerkarte.</span><span class="sxs-lookup"><span data-stu-id="5802c-133">Microsoft Teams will load the `contentUrl` specified in your manifest, embed it in an IFrame, and render it in your tab.</span></span>

### <a name="csproj"></a><span data-ttu-id="5802c-134">. csproj</span><span class="sxs-lookup"><span data-stu-id="5802c-134">.csproj</span></span>

<span data-ttu-id="5802c-135">Klicken Sie im Fenster Visual Studio Projektmappen-Explorer mit der rechten Maustaste auf das Projekt, und wählen Sie **Projektdatei bearbeiten**aus.</span><span class="sxs-lookup"><span data-stu-id="5802c-135">In the Visual Studio Solution Explorer window right-click on the project and select **Edit Project File**.</span></span> <span data-ttu-id="5802c-136">Unten in der Datei sehen Sie den Code, der Ihren ZIP-Ordner erstellt und aktualisiert, wenn die Anwendung erstellt wird:</span><span class="sxs-lookup"><span data-stu-id="5802c-136">At the bottom of the file you'll see the code that creates and updates your zip folder when the application builds:</span></span>

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

### <a name="models"></a><span data-ttu-id="5802c-137">Modelle</span><span class="sxs-lookup"><span data-stu-id="5802c-137">Models</span></span>

<span data-ttu-id="5802c-138">*PersonalTab.cs* zeigt ein Message-Objekt und Methoden, die von *PersonalTabController* aufgerufen werden, wenn ein Benutzer eine Schaltfläche in der *PersonalTab* -Ansicht auswählt.</span><span class="sxs-lookup"><span data-stu-id="5802c-138">*PersonalTab.cs* presents a Message object and methods that will be called from *PersonalTabController* when a user selects a button in the *PersonalTab* View.</span></span>

### <a name="views"></a><span data-ttu-id="5802c-139">Ansichten</span><span class="sxs-lookup"><span data-stu-id="5802c-139">Views</span></span>

#### <a name="home"></a><span data-ttu-id="5802c-140">Startseite</span><span class="sxs-lookup"><span data-stu-id="5802c-140">Home</span></span>

<span data-ttu-id="5802c-141">ASP.</span><span class="sxs-lookup"><span data-stu-id="5802c-141">ASP.</span></span> <span data-ttu-id="5802c-142">NET Core werden Dateien mit dem Namen " *Index* " als Standard/Homepage für die Website behandelt.</span><span class="sxs-lookup"><span data-stu-id="5802c-142">NET Core treats files called *Index* as the default/home page for the site.</span></span> <span data-ttu-id="5802c-143">Wenn Ihre Browser-URL auf den Stamm der Website zeigt, wird *Index. cshtml* als Startseite für Ihre Anwendung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="5802c-143">When your browser URL points to the root of the site, *Index.cshtml* will be displayed as the home page for your application.</span></span>

#### <a name="shared"></a><span data-ttu-id="5802c-144">Shared</span><span class="sxs-lookup"><span data-stu-id="5802c-144">Shared</span></span>

<span data-ttu-id="5802c-145">Das Markup *_Layout. cshtml* der partiellen Ansicht enthält die gesamte Seitenstruktur der Anwendung sowie freigegebene visuelle Elemente.</span><span class="sxs-lookup"><span data-stu-id="5802c-145">The partial view markup *_Layout.cshtml* contains the application's overall page structure and shared visual elements.</span></span> <span data-ttu-id="5802c-146">Außerdem wird auf die Microsoft Teams-Bibliothek verwiesen.</span><span class="sxs-lookup"><span data-stu-id="5802c-146">It will also reference the Teams Library.</span></span>

### <a name="controllers"></a><span data-ttu-id="5802c-147">Controller</span><span class="sxs-lookup"><span data-stu-id="5802c-147">Controllers</span></span>

<span data-ttu-id="5802c-148">Die Controller verwenden die ViewBag-Eigenschaft, um Werte dynamisch zu den Ansichten zu übertragen.</span><span class="sxs-lookup"><span data-stu-id="5802c-148">The controllers use the ViewBag property to transfer values dynamically to the Views.</span></span>

[!INCLUDE [dotnet-update-personal-app](~/includes/tabs/dotnet-update-personal-app.md)]

[!INCLUDE [dotnet-ngrok-intro](~/includes/tabs/dotnet-ngrok-intro.md)]

* <span data-ttu-id="5802c-149">Öffnen Sie eine Eingabeaufforderung im Stammverzeichnis des Projektverzeichnisses, und führen Sie den folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="5802c-149">Open a command prompt in the root of your project directory and run the following command:</span></span>

``` bash
ngrok http https://localhost:44345 -host-header="localhost:44345"
```

* <span data-ttu-id="5802c-150">Ngrok wird Anfragen aus dem Internet abhören und wird Sie an Ihre Anwendung weiterleiten, wenn Sie auf Port 44325 läuft.</span><span class="sxs-lookup"><span data-stu-id="5802c-150">Ngrok will listen to requests from the internet and will route them to your application when it is running on port 44325.</span></span>  <span data-ttu-id="5802c-151">Es sollte ähneln `https://y8rPrT2b.ngrok.io/` , wo *y8rPrT2b* durch ihre ngrok Alpha-numerische HTTPS-URL ersetzt wird.</span><span class="sxs-lookup"><span data-stu-id="5802c-151">It should resemble `https://y8rPrT2b.ngrok.io/` where *y8rPrT2b* is replaced by your ngrok alpha-numeric HTTPS URL.</span></span>

* <span data-ttu-id="5802c-152">Achten Sie darauf, dass Sie die Eingabeaufforderung mit ngrok weiterhin ausführen, und notieren Sie sich die URL, die Sie später benötigen.</span><span class="sxs-lookup"><span data-stu-id="5802c-152">Be sure to keep the command prompt with ngrok running, and to make a note of the URL — you'll need it later.</span></span>

* <span data-ttu-id="5802c-153">Stellen Sie sicher, dass *ngrok* ausgeführt wird und ordnungsgemäß funktioniert, indem Sie Ihren Browser öffnen und zu ihrer Inhaltsseite über die ngrok-HTTPS-URL wechseln, die in Ihrem Eingabeaufforderungsfenster bereitgestellt wurde.</span><span class="sxs-lookup"><span data-stu-id="5802c-153">Verify that *ngrok* is running and working properly by opening your browser and going to your content page via the ngrok HTTPS URL that was provided in your command prompt window.</span></span>

> <span data-ttu-id="5802c-154">[!</span><span class="sxs-lookup"><span data-stu-id="5802c-154">[!</span></span> <span data-ttu-id="5802c-155">Tipp] Sie müssen sowohl Ihre Anwendung in Visual Studio als auch ngrok ausführen, um diesen Schnellstart abzuschließen.</span><span class="sxs-lookup"><span data-stu-id="5802c-155">TIP] You need to have both your application in Visual Studio and ngrok running to complete this quickstart.</span></span> <span data-ttu-id="5802c-156">Wenn Sie die Ausführung der Anwendung in Visual Studio beenden müssen, um Sie zu bearbeiten, **halten Sie ngrok auf dem laufenden**.</span><span class="sxs-lookup"><span data-stu-id="5802c-156">If you need to stop running your application in Visual Studio to work on it, **keep ngrok running**.</span></span> <span data-ttu-id="5802c-157">Sie wird weiterhin überwacht und setzt die Weiterleitung der Anforderung Ihrer Anwendung fort, wenn Sie in Visual Studio neu gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="5802c-157">It will continue to listen and will resume routing your application's request when it restarts in Visual Studio.</span></span> <span data-ttu-id="5802c-158">Wenn Sie den ngrok-Dienst neu starten müssen, wird eine neue URL zurückgegeben, und Sie müssen jeden Ort aktualisieren, der diese URL verwendet.</span><span class="sxs-lookup"><span data-stu-id="5802c-158">If you have to restart the ngrok service it will return a new URL and you'll have to update every place that uses that URL.</span></span>

### <a name="run-your-application"></a><span data-ttu-id="5802c-159">Ausführen Ihrer Anwendung</span><span class="sxs-lookup"><span data-stu-id="5802c-159">Run your application</span></span>

* <span data-ttu-id="5802c-160">Drücken Sie in Visual Studio **F5** , oder klicken Sie im Menü **Debuggen** Ihrer Anwendung auf **Debuggen starten** .</span><span class="sxs-lookup"><span data-stu-id="5802c-160">In Visual Studio press **F5** or choose **Start Debugging** from your application's **Debug** menu.</span></span>

[!INCLUDE [dotnet-personal-use-appstudio](~/includes/tabs/dotnet-personal-use-appstudio.md)]
