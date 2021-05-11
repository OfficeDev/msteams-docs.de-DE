---
title: Erstellen einer persönlichen Registerkarte mit ASP.NET Core
author: laujan
description: Eine Schnellstartanleitung zum Erstellen einer benutzerdefinierten persönlichen Registerkarte mit ASP.NET Core.
ms.topic: quickstart
localization_priority: Normal
ms.author: lajanuar
ms.openlocfilehash: 858175c5afa742d7f2d818204fe1a6f09f6e2245
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020296"
---
# <a name="create-a-personal-tab-with-aspnet-core"></a><span data-ttu-id="ba3a6-103">Erstellen einer persönlichen Registerkarte mit ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ba3a6-103">Create a personal tab with ASP.NET Core</span></span>

<span data-ttu-id="ba3a6-104">In dieser Schnellstartanleitung wird eine benutzerdefinierte persönliche Registerkarte mit C# und ASP.Net erstellt.</span><span class="sxs-lookup"><span data-stu-id="ba3a6-104">In this quickstart, we'll walk-through creating a custom personal tab with C# and ASP.Net Core Razor pages.</span></span> <span data-ttu-id="ba3a6-105">Außerdem verwenden wir [App Studio für Microsoft Teams,](~/concepts/build-and-test/app-studio-overview.md) um Ihr App-Manifest zu finalisieren und Ihre Registerkarte für die Teams.</span><span class="sxs-lookup"><span data-stu-id="ba3a6-105">We'll also use [App Studio for Microsoft Teams](~/concepts/build-and-test/app-studio-overview.md) to finalize your app manifest and deploy your tab to Teams.</span></span>

[!INCLUDE [dotnet-core-prereq](~/includes/tabs/dotnet-core-prereq.md)]

## <a name="get-the-source-code"></a><span data-ttu-id="ba3a6-106">Den Quellcode erhalten</span><span class="sxs-lookup"><span data-stu-id="ba3a6-106">Get the source code</span></span>

<span data-ttu-id="ba3a6-107">Öffnen Sie eine Eingabeaufforderung, und erstellen Sie ein neues Verzeichnis für Ihr Registerkartenprojekt.</span><span class="sxs-lookup"><span data-stu-id="ba3a6-107">Open a command prompt and create a new directory for your tab project.</span></span> <span data-ttu-id="ba3a6-108">Wir haben ein einfaches Projekt bereitgestellt, mit dem Sie beginnen können.</span><span class="sxs-lookup"><span data-stu-id="ba3a6-108">We have provided a simple project to get you started.</span></span> <span data-ttu-id="ba3a6-109">Zum Abrufen des Quellcodes können Sie den Zip-Ordner herunterladen und die Dateien extrahieren oder das Beispielrepository in Ihr neues Verzeichnis klonen:</span><span class="sxs-lookup"><span data-stu-id="ba3a6-109">To retrieve the source code you can download the zip folder and extract the files or clone the sample repository into your new directory:</span></span>

```bash
git clone https://github.com/OfficeDev/microsoft-teams-sample-tabs.git
```

<span data-ttu-id="ba3a6-110">Nachdem Sie den Quellcode verwendet haben, öffnen Sie Visual Studio, und wählen **Sie Projekt oder Projektmappe öffnen aus.**</span><span class="sxs-lookup"><span data-stu-id="ba3a6-110">Once you have the source code, open Visual Studio and select **Open a project or solution**.</span></span> <span data-ttu-id="ba3a6-111">Navigieren Sie zum Verzeichnis der Registerkartenanwendung, und öffnen **Sie PersonalTab.sln**.</span><span class="sxs-lookup"><span data-stu-id="ba3a6-111">Navigate to the tab application directory and open **PersonalTab.sln**.</span></span>

<span data-ttu-id="ba3a6-112">Drücken Sie **F5,** um die Anwendung zu erstellen und auszuführen, oder wählen Sie **Debuggen starten** im Menü **Debuggen** aus.</span><span class="sxs-lookup"><span data-stu-id="ba3a6-112">To build and run your application press **F5** or choose **Start Debugging** from the **Debug** menu.</span></span> <span data-ttu-id="ba3a6-113">Navigieren Sie in einem Browser zu den folgenden URLs, um zu überprüfen, ob die Anwendung ordnungsgemäß geladen wurde:</span><span class="sxs-lookup"><span data-stu-id="ba3a6-113">In a browser navigate to the URLs below to verify the application loaded properly:</span></span>

- `http://localhost:44325/`
- `http://localhost:44325/personal`
- `http://localhost:44325/privacy`
- `http://localhost:44325/tou`

## <a name="review-the-source-code"></a><span data-ttu-id="ba3a6-114">Überprüfen des Quellcodes</span><span class="sxs-lookup"><span data-stu-id="ba3a6-114">Review the source code</span></span>

### <a name="startupcs"></a><span data-ttu-id="ba3a6-115">Startup.cs</span><span class="sxs-lookup"><span data-stu-id="ba3a6-115">Startup.cs</span></span>

<span data-ttu-id="ba3a6-116">Dieses Projekt wurde aus einer leeren ASP.NET Core 2.2-Webanwendung erstellt, deren Kontrollkästchen *Advanced – Configure for HTTPS* beim Setup aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="ba3a6-116">This project was created from an ASP.NET Core 2.2 Web Application empty template with the *Advanced - Configure for HTTPS* check box selected at setup.</span></span> <span data-ttu-id="ba3a6-117">Die MVC-Dienste werden von der Methode des Abhängigkeitsinjektionsframeworks `ConfigureServices()` registriert.</span><span class="sxs-lookup"><span data-stu-id="ba3a6-117">The MVC services are registered by the dependency injection framework's `ConfigureServices()` method.</span></span> <span data-ttu-id="ba3a6-118">Darüber hinaus ermöglicht die leere Vorlage die Standardmäßige Entladung statischer Inhalte nicht, sodass die Middleware für statische Dateien der Methode hinzugefügt `Configure()` wird:</span><span class="sxs-lookup"><span data-stu-id="ba3a6-118">Additionally, the empty template doesn't enable serving static content by default, so the static files middleware is added to the `Configure()` method:</span></span>

```csharp
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

### <a name="wwwroot-folder"></a><span data-ttu-id="ba3a6-119">Ordner "wwwroot"</span><span class="sxs-lookup"><span data-stu-id="ba3a6-119">wwwroot folder</span></span>

<span data-ttu-id="ba3a6-120">In ASP.NET Core ist der Webstammordner der Ort, in dem die Anwendung nach statischen Dateien sucht.</span><span class="sxs-lookup"><span data-stu-id="ba3a6-120">In ASP.NET Core, the web root folder is where the application looks for static files.</span></span>

### <a name="indexcshtml"></a><span data-ttu-id="ba3a6-121">Index.cshtml</span><span class="sxs-lookup"><span data-stu-id="ba3a6-121">Index.cshtml</span></span>

<span data-ttu-id="ba3a6-122">ASP.NET Core behandelt Dateien mit dem Namen *Index* als Standard-/Homepage für die Website.</span><span class="sxs-lookup"><span data-stu-id="ba3a6-122">ASP.NET Core treats files called *Index* as the default/home page for the site.</span></span> <span data-ttu-id="ba3a6-123">Wenn Ihre Browser-URL auf den Stamm der Website verweist, wird **Index.cshtml** als Homepage für Ihre Anwendung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="ba3a6-123">When your browser URL points to the root of the site, **Index.cshtml** will be displayed as the home page for your application.</span></span>

### <a name="appmanifest-folder"></a><span data-ttu-id="ba3a6-124">Ordner "AppManifest"</span><span class="sxs-lookup"><span data-stu-id="ba3a6-124">AppManifest folder</span></span>

<span data-ttu-id="ba3a6-125">Dieser Ordner enthält die folgenden erforderlichen App-Paketdateien:</span><span class="sxs-lookup"><span data-stu-id="ba3a6-125">This folder contains the following required app package files:</span></span>

- <span data-ttu-id="ba3a6-126">Ein **Vollfarbsymbol** mit einer Breite von 192 x 192 Pixeln.</span><span class="sxs-lookup"><span data-stu-id="ba3a6-126">A **full color icon** measuring 192 x 192 pixels.</span></span>
- <span data-ttu-id="ba3a6-127">Ein **transparentes Gliederungssymbol** mit einer Breite von 32 x 32 Pixeln.</span><span class="sxs-lookup"><span data-stu-id="ba3a6-127">A **transparent outline icon** measuring 32 x 32 pixels.</span></span>
- <span data-ttu-id="ba3a6-128">Eine **manifest.json-Datei,** die die Attribute Ihrer App angibt.</span><span class="sxs-lookup"><span data-stu-id="ba3a6-128">A **manifest.json** file that specifies the attributes of your app.</span></span>

<span data-ttu-id="ba3a6-129">Diese Dateien müssen in einem App-Paket gezippt werden, damit sie zum Hochladen Ihrer Registerkarte in das Teams.</span><span class="sxs-lookup"><span data-stu-id="ba3a6-129">These files need to be zipped in an app package for use in uploading your tab to Teams.</span></span> <span data-ttu-id="ba3a6-130">Microsoft Teams laden sie das in Ihrem Manifest angegebene, betten sie in einen iframe <ein, und rendern Sie ihn `contentUrl` \> auf Ihrer Registerkarte.</span><span class="sxs-lookup"><span data-stu-id="ba3a6-130">Microsoft Teams will load the `contentUrl` specified in your manifest, embed it in an <iframe\>, and render it in your tab.</span></span>

### <a name="csproj"></a><span data-ttu-id="ba3a6-131">.csproj</span><span class="sxs-lookup"><span data-stu-id="ba3a6-131">.csproj</span></span>

<span data-ttu-id="ba3a6-132">Klicken Sie Visual Studio Projektmappen-Explorer mit der rechten Maustaste auf das Projekt, und wählen Sie **Bearbeiten Project Datei aus.**</span><span class="sxs-lookup"><span data-stu-id="ba3a6-132">In the Visual Studio Solution Explorer window, right-click on the project and select **Edit Project File**.</span></span> <span data-ttu-id="ba3a6-133">Unten in der Datei wird der Code angezeigt, mit dem Ihr ZIP-Ordner erstellt und aktualisiert wird, wenn die Anwendung erstellt:</span><span class="sxs-lookup"><span data-stu-id="ba3a6-133">At the bottom of the file you'll see the code that creates and updates your zip folder when the application builds:</span></span>

```xml
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

[!INCLUDE  [dotnet-update-personal-app](~/includes/tabs/dotnet-update-personal-app.md)]

[!INCLUDE [dotnet-ngrok-intro](~/includes/tabs/dotnet-ngrok-intro.md)]

- <span data-ttu-id="ba3a6-134">Öffnen Sie eine Eingabeaufforderung im Stammverzeichnis Ihres Projektverzeichnisses, und führen Sie den folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="ba3a6-134">Open a command prompt in the root of your project directory and run the following command:</span></span>

```bash
ngrok http https://localhost:44325 -host-header="localhost:44325"
```

- <span data-ttu-id="ba3a6-135">Ngrok lauscht Anforderungen aus dem Internet und führt sie an Ihre Anwendung weiter, wenn sie an Port 44325 ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="ba3a6-135">Ngrok will listen to requests from the internet and will route them to your application when it is running on port 44325.</span></span>  <span data-ttu-id="ba3a6-136">Es sollte so `https://y8rPrT2b.ngrok.io/` aussehen, *dass y8rPrT2b* durch Ihre ngrok-alphanumerische HTTPS-URL ersetzt wird.</span><span class="sxs-lookup"><span data-stu-id="ba3a6-136">It should resemble `https://y8rPrT2b.ngrok.io/` where *y8rPrT2b* is replaced by your ngrok alpha-numeric HTTPS URL.</span></span>

- <span data-ttu-id="ba3a6-137">Achten Sie darauf, dass die Eingabeaufforderung mit ngrok ausgeführt wird, und notieren Sie sich die URL – Sie benötigen sie später.</span><span class="sxs-lookup"><span data-stu-id="ba3a6-137">Be sure to keep the command prompt with ngrok running, and to make a note of the URL — you'll need it later.</span></span>

- <span data-ttu-id="ba3a6-138">Stellen Sie sicher, dass *ngrok* ordnungsgemäß ausgeführt und funktioniert, indem Sie Ihren Browser öffnen und über die ngrok-HTTPS-URL, die im Eingabeaufforderungsfenster bereitgestellt wurde, zu Ihrer Inhaltsseite wechseln.</span><span class="sxs-lookup"><span data-stu-id="ba3a6-138">Verify that *ngrok* is running and working properly by opening your browser and going to your content page via the ngrok HTTPS URL that was provided in your command prompt window.</span></span>

>[!TIP]
><span data-ttu-id="ba3a6-139">Sie müssen ihre Anwendung in Visual Studio und ngrok ausführen, um diesen Schnellstart ausführen zu können.</span><span class="sxs-lookup"><span data-stu-id="ba3a6-139">You need to have both your application in Visual Studio and ngrok running to complete this quickstart.</span></span> <span data-ttu-id="ba3a6-140">Wenn Sie die Ausführung Ihrer Anwendung in Visual Studio ausführen müssen, halten Sie **ngrok am Laufen.**</span><span class="sxs-lookup"><span data-stu-id="ba3a6-140">If you need to stop running your application in Visual Studio to work on it, **keep ngrok running**.</span></span> <span data-ttu-id="ba3a6-141">Sie lauscht weiterhin und setzt das Routing der Anforderung Ihrer Anwendung fort, wenn sie in einem Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ba3a6-141">It will continue to listen and will resume routing your application's request when it restarts in Visual Studio.</span></span> <span data-ttu-id="ba3a6-142">Wenn Sie den ngrok-Dienst neu starten müssen, gibt er eine neue URL zurück, und Sie müssen jeden Ort aktualisieren, der diese URL verwendet.</span><span class="sxs-lookup"><span data-stu-id="ba3a6-142">If you have to restart the ngrok service it will return a new URL and you'll have to update every place that uses that URL.</span></span>

### <a name="run-your-application"></a><span data-ttu-id="ba3a6-143">Ausführen der Anwendung</span><span class="sxs-lookup"><span data-stu-id="ba3a6-143">Run your application</span></span>

- <span data-ttu-id="ba3a6-144">Drücken Visual Studio **F5,** oder wählen Sie **Debuggen starten** im Menü **Debuggen** Ihrer Anwendung aus.</span><span class="sxs-lookup"><span data-stu-id="ba3a6-144">In Visual Studio press **F5** or choose **Start Debugging** from your application's **Debug** menu.</span></span>

[!INCLUDE [dotnet-personal-use-appstudio](~/includes/tabs/dotnet-personal-use-appstudio.md)]
