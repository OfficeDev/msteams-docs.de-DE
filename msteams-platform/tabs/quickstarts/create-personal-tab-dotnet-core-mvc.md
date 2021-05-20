---
title: Erstellen Sie eine persönliche Registerkarte mit ASP. NET Core MVC
author: laujan
description: Eine Schnellstartanleitung zum Erstellen einer benutzerdefinierten persönlichen Registerkarte mit ASP. NET Core MVC.
localization_priority: Normal
ms.topic: quickstart
ms.author: lajanuar
ms.openlocfilehash: 01418adb32335660bb20f74ecfaa0e7e27230c93
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566628"
---
# <a name="create-a-custom-personal-tab-with-aspnet-core-mvc"></a><span data-ttu-id="700a9-105">Erstellen einer benutzerdefinierten persönlichen Registerkarte mit ASP.NET Core MVC</span><span class="sxs-lookup"><span data-stu-id="700a9-105">Create a Custom Personal Tab with ASP.NET Core MVC</span></span>

<span data-ttu-id="700a9-106">In dieser Schnellstartanleitung werden wir eine benutzerdefinierte persönliche Registerkarte mit C- und ASP.Net Core MVC erstellen.</span><span class="sxs-lookup"><span data-stu-id="700a9-106">In this quickstart we'll walk-through creating a custom personal tab with C# and ASP.Net Core MVC.</span></span> <span data-ttu-id="700a9-107">Wir verwenden App Studio auch [für Microsoft Teams,](~/concepts/build-and-test/app-studio-overview.md) um Ihr App-Manifest fertigzustellen und Ihre Registerkarte auf Teams bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="700a9-107">We'll also use [App Studio for Microsoft Teams](~/concepts/build-and-test/app-studio-overview.md) to finalize your app manifest and deploy your tab to Teams.</span></span>

[!INCLUDE [dotnet-core-prereq](~/includes/tabs/dotnet-core-prereq.md)]

## <a name="get-the-source-code"></a><span data-ttu-id="700a9-108">Abrufen des Quellcodes</span><span class="sxs-lookup"><span data-stu-id="700a9-108">Get the source code</span></span>

<span data-ttu-id="700a9-109">Öffnen Sie eine Eingabeaufforderung, und erstellen Sie ein neues Verzeichnis für Ihr Registerkartenprojekt.</span><span class="sxs-lookup"><span data-stu-id="700a9-109">Open a command prompt and create a new directory for your tab project.</span></span> <span data-ttu-id="700a9-110">Wir haben ein einfaches Projekt zur Verfügung gestellt, um Ihnen den Einstieg zu erleichtern.</span><span class="sxs-lookup"><span data-stu-id="700a9-110">We have provided a simple project to get you started.</span></span> <span data-ttu-id="700a9-111">Um den Quellcode abzurufen, können Sie den ZIP-Ordner herunterladen und die Dateien extrahieren oder das Beispiel-Repository in Ihr neues Verzeichnis klonen:</span><span class="sxs-lookup"><span data-stu-id="700a9-111">To retrieve the source code you can download the zip folder and extract the files or clone the sample repository into your new directory:</span></span>

``` bash
git clone https://github.com/OfficeDev/microsoft-teams-sample-tabs.git
```

<span data-ttu-id="700a9-112">Sobald Sie den Quellcode haben, öffnen Sie Visual Studio und wählen Sie **Projekt oder Projektmappe öffnen** aus.</span><span class="sxs-lookup"><span data-stu-id="700a9-112">Once you have the source code, open Visual Studio and select **Open a project or solution**.</span></span> <span data-ttu-id="700a9-113">Navigieren Sie zum Registerkartenanwendungsverzeichnis, und öffnen **Sie PersonalTabMVC.sln**.</span><span class="sxs-lookup"><span data-stu-id="700a9-113">Navigate to the tab application directory and open **PersonalTabMVC.sln**.</span></span>

<span data-ttu-id="700a9-114">Um Ihre Anwendung zu erstellen und auszuführen, drücken Sie **F5** oder wählen Sie **Debuggen** starten im **Debugmenü** aus.</span><span class="sxs-lookup"><span data-stu-id="700a9-114">To build and run your application press **F5** or choose **Start Debugging** from the **Debug** menu.</span></span> <span data-ttu-id="700a9-115">Navigieren Sie in einem Browser zu den folgenden URLs, um zu überprüfen, ob die Anwendung ordnungsgemäß geladen wurde:</span><span class="sxs-lookup"><span data-stu-id="700a9-115">In a browser navigate to the URLs below to verify that the application loaded properly:</span></span>

* `http://localhost:44335`
* `http://localhost:44335/privacy`
* `http://localhost:44335/tou`

## <a name="review-the-source-code"></a><span data-ttu-id="700a9-116">Überprüfen des Quellcodes</span><span class="sxs-lookup"><span data-stu-id="700a9-116">Review the source code</span></span>

### <a name="startupcs"></a><span data-ttu-id="700a9-117">Startup.cs</span><span class="sxs-lookup"><span data-stu-id="700a9-117">Startup.cs</span></span>

<span data-ttu-id="700a9-118">Dieses Projekt wurde aus einem ASP erstellt.</span><span class="sxs-lookup"><span data-stu-id="700a9-118">This project was created from an ASP.</span></span> <span data-ttu-id="700a9-119">Net Core 2.2 Leere Vorlage für Webanwendung mit dem Kontrollkästchen *Erweitert - Konfigurieren für HTTPS,* das bei Setup ausgewählt wurde.</span><span class="sxs-lookup"><span data-stu-id="700a9-119">NET Core 2.2 Web Application empty template with the *Advanced - Configure for HTTPS* check box selected at setup.</span></span> <span data-ttu-id="700a9-120">Die MVC-Dienste werden von der Methode des Abhängigkeitsinjektionsframeworks `ConfigureServices()` registriert.</span><span class="sxs-lookup"><span data-stu-id="700a9-120">The MVC services are registered by the dependency injection framework's `ConfigureServices()` method.</span></span> <span data-ttu-id="700a9-121">Darüber hinaus ermöglicht die leere Vorlage standardmäßig nicht die Bereitstellung statischer Inhalte, sodass die Middleware für statische Dateien der Methode hinzugefügt `Configure()` wird:</span><span class="sxs-lookup"><span data-stu-id="700a9-121">Additionally, the empty template doesn't enable serving static content by default, so the static files middleware is added to the `Configure()` method:</span></span>

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

### <a name="wwwroot-folder"></a><span data-ttu-id="700a9-122">wwwroot-Ordner</span><span class="sxs-lookup"><span data-stu-id="700a9-122">wwwroot folder</span></span>

<span data-ttu-id="700a9-123">In ASP.</span><span class="sxs-lookup"><span data-stu-id="700a9-123">In ASP.</span></span> <span data-ttu-id="700a9-124">NET Core, der Webstammordner ist der Ort, an dem die Anwendung nach statischen Dateien sucht.</span><span class="sxs-lookup"><span data-stu-id="700a9-124">NET Core, the web root folder is where the application looks for static files.</span></span>

### <a name="appmanifest-folder"></a><span data-ttu-id="700a9-125">AppManifest-Ordner</span><span class="sxs-lookup"><span data-stu-id="700a9-125">AppManifest folder</span></span>

<span data-ttu-id="700a9-126">Dieser Ordner enthält die folgenden erforderlichen App-Paketdateien:</span><span class="sxs-lookup"><span data-stu-id="700a9-126">This folder contains the following required app package files:</span></span>

* <span data-ttu-id="700a9-127">Ein **Vollfarbsymbol** mit 192 x 192 Pixeln.</span><span class="sxs-lookup"><span data-stu-id="700a9-127">A **full color icon** measuring 192 x 192 pixels.</span></span>
* <span data-ttu-id="700a9-128">Ein **transparentes Umrisssymbol** mit 32 x 32 Pixeln.</span><span class="sxs-lookup"><span data-stu-id="700a9-128">A **transparent outline icon** measuring 32 x 32 pixels.</span></span>
* <span data-ttu-id="700a9-129">Eine **manifest.jsin der** Datei, die die Attribute Ihrer App angibt.</span><span class="sxs-lookup"><span data-stu-id="700a9-129">A **manifest.json** file that specifies the attributes of your app.</span></span>

<span data-ttu-id="700a9-130">Diese Dateien müssen in einem App-Paket gezippt werden, damit Sie Ihre Registerkarte in Teams hochladen können.</span><span class="sxs-lookup"><span data-stu-id="700a9-130">These files need to be zipped in an app package for use in uploading your tab to Teams.</span></span> <span data-ttu-id="700a9-131">Microsoft Teams lädt das `contentUrl` in Ihrem Manifest angegebene, bettet es in ein IFrame ein und rendert es in Ihrer Registerkarte.</span><span class="sxs-lookup"><span data-stu-id="700a9-131">Microsoft Teams will load the `contentUrl` specified in your manifest, embed it in an IFrame, and render it in your tab.</span></span>

### <a name="csproj"></a><span data-ttu-id="700a9-132">.csproj</span><span class="sxs-lookup"><span data-stu-id="700a9-132">.csproj</span></span>

<span data-ttu-id="700a9-133">Klicken Sie im Fenster Visual Studio Projektmappen-Explorer mit der rechten Maustaste auf das Projekt, und wählen Sie **Project Datei bearbeiten** aus.</span><span class="sxs-lookup"><span data-stu-id="700a9-133">In the Visual Studio Solution Explorer window right-click on the project and select **Edit Project File**.</span></span> <span data-ttu-id="700a9-134">Am unteren Rand der Datei sehen Sie den Code, der Ihren ZIP-Ordner erstellt und aktualisiert, wenn die Anwendung erstellt wird:</span><span class="sxs-lookup"><span data-stu-id="700a9-134">At the bottom of the file you'll see the code that creates and updates your zip folder when the application builds:</span></span>

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

### <a name="models"></a><span data-ttu-id="700a9-135">Modelle</span><span class="sxs-lookup"><span data-stu-id="700a9-135">Models</span></span>

<span data-ttu-id="700a9-136">**PersonalTab.cs** stellt ein Message-Objekt und Methoden vor, die von *PersonalTabController* aufgerufen werden, wenn ein Benutzer eine Schaltfläche in der **PersonalTab-Ansicht** auswählt.</span><span class="sxs-lookup"><span data-stu-id="700a9-136">**PersonalTab.cs** presents a Message object and methods that will be called from *PersonalTabController* when a user selects a button in the **PersonalTab** View.</span></span>

### <a name="views"></a><span data-ttu-id="700a9-137">Ansichten</span><span class="sxs-lookup"><span data-stu-id="700a9-137">Views</span></span>

#### <a name="home"></a><span data-ttu-id="700a9-138">Start</span><span class="sxs-lookup"><span data-stu-id="700a9-138">Home</span></span>

<span data-ttu-id="700a9-139">Asp.</span><span class="sxs-lookup"><span data-stu-id="700a9-139">ASP.</span></span> <span data-ttu-id="700a9-140">NET Core behandelt Dateien, die **Index** genannt werden, als Standard- oder Homepage für die Website.</span><span class="sxs-lookup"><span data-stu-id="700a9-140">NET Core treats files called **Index** as the default or home page for the site.</span></span> <span data-ttu-id="700a9-141">Wenn Ihre Browser-URL auf den Stamm der Website verweist, wird **Index.cshtml** als Homepage für Ihre Anwendung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="700a9-141">When your browser URL points to the root of the site, **Index.cshtml** will be displayed as the home page for your application.</span></span>

#### <a name="shared"></a><span data-ttu-id="700a9-142">Shared</span><span class="sxs-lookup"><span data-stu-id="700a9-142">Shared</span></span>

<span data-ttu-id="700a9-143">Das Partansichtsmarkup *_Layout.cshtml* enthält die gesamte Seitenstruktur der Anwendung und freigegebene visuelle Elemente.</span><span class="sxs-lookup"><span data-stu-id="700a9-143">The partial view markup *_Layout.cshtml* contains the application's overall page structure and shared visual elements.</span></span> <span data-ttu-id="700a9-144">Sie wird auch auf die Teams Library verweisen.</span><span class="sxs-lookup"><span data-stu-id="700a9-144">It will also reference the Teams Library.</span></span>

### <a name="controllers"></a><span data-ttu-id="700a9-145">Controller</span><span class="sxs-lookup"><span data-stu-id="700a9-145">Controllers</span></span>

<span data-ttu-id="700a9-146">Die Controller verwenden die ViewBag-Eigenschaft, um Werte dynamisch in die Ansichten zu übertragen.</span><span class="sxs-lookup"><span data-stu-id="700a9-146">The controllers use the ViewBag property to transfer values dynamically to the Views.</span></span>

[!INCLUDE [dotnet-update-personal-app](~/includes/tabs/dotnet-update-personal-app.md)]

[!INCLUDE [dotnet-ngrok-intro](~/includes/tabs/dotnet-ngrok-intro.md)]

* <span data-ttu-id="700a9-147">Öffnen Sie eine Eingabeaufforderung im Stammverzeichnis Ihres Projektverzeichnisses, und führen Sie den folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="700a9-147">Open a command prompt in the root of your project directory and run the following command:</span></span>

    ``` bash
    ngrok http https://localhost:44345 -host-header="localhost:44345"
    ```

* <span data-ttu-id="700a9-148">Ngrok hört Anfragen aus dem Internet ab und leitet sie an Ihre Anwendung weiter, wenn sie auf Port 44325 ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="700a9-148">Ngrok will listen to requests from the internet and will route them to your application when it is running on port 44325.</span></span>  <span data-ttu-id="700a9-149">Es sollte der Stelle ähneln, an der `https://y8rPrT2b.ngrok.io/` *y8rPrT2b* durch Ihre alphanumerische HTTPS-URL von ngrok ersetzt wird.</span><span class="sxs-lookup"><span data-stu-id="700a9-149">It should resemble `https://y8rPrT2b.ngrok.io/` where *y8rPrT2b* is replaced by your ngrok alpha-numeric HTTPS URL.</span></span>

* <span data-ttu-id="700a9-150">Achten Sie darauf, die Eingabeaufforderung zu halten, wenn ngrok ausgeführt wird, und notieren Sie sich die URL – Sie werden sie später benötigen.</span><span class="sxs-lookup"><span data-stu-id="700a9-150">Be sure to keep the command prompt with ngrok running, and to make a note of the URL — you'll need it later.</span></span>

* <span data-ttu-id="700a9-151">Stellen Sie sicher, dass **ngrok** ordnungsgemäß ausgeführt wird und ordnungsgemäß funktioniert, indem Sie Ihren Browser öffnen und über die ngrok HTTPS-URL, die in Ihrem Eingabeaufforderungsfenster bereitgestellt wurde, zur Inhaltsseite wechseln.</span><span class="sxs-lookup"><span data-stu-id="700a9-151">Verify that **ngrok** is running and working properly by opening your browser and going to your content page via the ngrok HTTPS URL that was provided in your command prompt window.</span></span>

> [!TIP]
> <span data-ttu-id="700a9-152">Sie müssen sowohl Ihre Anwendung in Visual Studio als auch ngrok ausführen, um diese Schnellstartanleitung abzuschließen.</span><span class="sxs-lookup"><span data-stu-id="700a9-152">You need to have both your application in Visual Studio and ngrok running to complete this quickstart.</span></span> <span data-ttu-id="700a9-153">Wenn Sie die Ausführung Ihrer Anwendung in Visual Studio beenden müssen, um daran zu arbeiten, **führen Sie ngrok aus.**</span><span class="sxs-lookup"><span data-stu-id="700a9-153">If you need to stop running your application in Visual Studio to work on it, **keep ngrok running**.</span></span> <span data-ttu-id="700a9-154">Sie wird weiterhin überwacht und die Weiterleitung der Anforderung Ihrer Anwendung fortgesetzt, wenn sie in Visual Studio neu gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="700a9-154">It will continue to listen and will resume routing your application's request when it restarts in Visual Studio.</span></span> <span data-ttu-id="700a9-155">Wenn Sie den ngrok-Dienst neu starten müssen, wird eine neue URL zurückgegeben, und Sie müssen jeden Ort aktualisieren, der diese URL verwendet.</span><span class="sxs-lookup"><span data-stu-id="700a9-155">If you have to restart the ngrok service it will return a new URL and you'll have to update every place that uses that URL.</span></span>

### <a name="run-your-application"></a><span data-ttu-id="700a9-156">Führen Sie Ihre Anwendung aus</span><span class="sxs-lookup"><span data-stu-id="700a9-156">Run your application</span></span>

* <span data-ttu-id="700a9-157">Drücken Sie Visual Studio **F5** oder wählen Sie **Debuggen** starten aus dem **Debug-Menü** Ihrer Anwendung aus.</span><span class="sxs-lookup"><span data-stu-id="700a9-157">In Visual Studio press **F5** or choose **Start Debugging** from your application's **Debug** menu.</span></span>

[!INCLUDE [dotnet-personal-use-appstudio](~/includes/tabs/dotnet-personal-use-appstudio.md)]

## <a name="next-step"></a><span data-ttu-id="700a9-158">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="700a9-158">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="700a9-159">Erstellen Sie eine benutzerdefinierte Kanal- und Gruppenregisterkarte mit Node.js und dem Yeoman Generator für Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="700a9-159">Create a custom channel and group tab using Node.js and the Yeoman Generator for Microsoft Teams</span></span>](~/tabs/quickstarts/create-channel-group-tab-node-yeoman.md)
