---
title: Erstellen einer persönlichen Registerkarte mit ASP.net Core
author: laujan
description: Eine Schnellstartanleitung zum Erstellen einer benutzerdefinierten persönlichen Registerkarte mit ASP.net Core.
ms.topic: quickstart
ms.author: laujan
ms.openlocfilehash: b279c96f47265fe1928ae90d661e7dc042085b39
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674545"
---
# <a name="create-a-custom-personal-tab-with-aspnet-core"></a><span data-ttu-id="87bfb-103">Erstellen einer benutzerdefinierten persönlichen Registerkarte mit ASP.net Core</span><span class="sxs-lookup"><span data-stu-id="87bfb-103">Create a Custom Personal Tab with ASP.NET Core</span></span>

<span data-ttu-id="87bfb-104">In diesem Schnellstart werden wir durch das Erstellen einer benutzerdefinierten persönlichen Registerkarte mit C#-und ASP.net-Core-Razor-Seiten Schritt halten.</span><span class="sxs-lookup"><span data-stu-id="87bfb-104">In this quickstart we'll walk-through creating a custom personal tab with C# and ASP.Net Core Razor pages.</span></span> <span data-ttu-id="87bfb-105">Wir verwenden auch [App Studio für Microsoft Teams](~/concepts/build-and-test/app-studio-overview.md) , um Ihr App-Manifest abzuschließen und die Registerkarte in Teams bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="87bfb-105">We'll also use [App Studio for Microsoft Teams](~/concepts/build-and-test/app-studio-overview.md) to finalize your app manifest and deploy your tab to Teams.</span></span>

[!INCLUDE [dotnet-core-prereq](~/includes/tabs/dotnet-core-prereq.md)]

## <a name="get-the-source-code"></a><span data-ttu-id="87bfb-106">Abrufen des Quellcodes</span><span class="sxs-lookup"><span data-stu-id="87bfb-106">Get the source code</span></span>

<span data-ttu-id="87bfb-107">Öffnen Sie eine Eingabeaufforderung, und erstellen Sie ein neues Verzeichnis für Ihr Tab-Projekt.</span><span class="sxs-lookup"><span data-stu-id="87bfb-107">Open a command prompt and create a new directory for your tab project.</span></span> <span data-ttu-id="87bfb-108">Wir haben ein einfaches Projekt zur Verfügung gestellt, damit Sie loslegen können.</span><span class="sxs-lookup"><span data-stu-id="87bfb-108">We have provided a simple project to get you started.</span></span> <span data-ttu-id="87bfb-109">Zum Abrufen des Quellcodes können Sie den ZIP-Ordner herunterladen und die Dateien extrahieren oder das Beispiel-Repository in Ihr neues Verzeichnis kopieren:</span><span class="sxs-lookup"><span data-stu-id="87bfb-109">To retrieve the source code you can download the zip folder and extract the files or clone the sample repository into your new directory:</span></span>

```bash
git clone https://github.com/OfficeDev/microsoft-teams-sample-tabs.git
```

<span data-ttu-id="87bfb-110">Nachdem Sie den Quellcode haben, öffnen Sie Visual Studio, und wählen Sie **Projekt oder Lösung öffnen**aus.</span><span class="sxs-lookup"><span data-stu-id="87bfb-110">Once you have the source code, open Visual Studio and select **Open a project or solution**.</span></span> <span data-ttu-id="87bfb-111">Navigieren Sie zum Anwendungsverzeichnis der Registerkarte, und öffnen Sie **PersonalTab. sln**.</span><span class="sxs-lookup"><span data-stu-id="87bfb-111">Navigate to the tab application directory and open **PersonalTab.sln**.</span></span>

<span data-ttu-id="87bfb-112">Drücken Sie zum Erstellen und Ausführen der Anwendung **F5** , oder wählen Sie im Menü **Debuggen** die Option **Debuggen starten** aus.</span><span class="sxs-lookup"><span data-stu-id="87bfb-112">To build and run your application press **F5** or choose **Start Debugging** from the **Debug** menu.</span></span> <span data-ttu-id="87bfb-113">Navigieren Sie in einem Browser zu den folgenden URLs, um zu überprüfen, ob die Anwendung ordnungsgemäß geladen wurde:</span><span class="sxs-lookup"><span data-stu-id="87bfb-113">In a browser navigate to the URLs below to verify the application loaded properly:</span></span>

- `http://localhost:44325/`
- `http://localhost:44325/personal`
- `http://localhost:44325/privacy`
- `http://localhost:44325/tou`

## <a name="review-the-source-code"></a><span data-ttu-id="87bfb-114">Überprüfen des Quellcodes</span><span class="sxs-lookup"><span data-stu-id="87bfb-114">Review the source code</span></span>

### <a name="startupcs"></a><span data-ttu-id="87bfb-115">Startup.cs</span><span class="sxs-lookup"><span data-stu-id="87bfb-115">Startup.cs</span></span>

<span data-ttu-id="87bfb-116">Dieses Projekt wurde aus einer leeren Vorlage für ASP.net Core 2,2-Webanwendungen erstellt, wobei das Kontrollkästchen *Erweiterte Konfiguration für HTTPS* beim Setup aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="87bfb-116">This project was created from an ASP.NET Core 2.2 Web Application empty template with the *Advanced - Configure for HTTPS* check box selected at setup.</span></span> <span data-ttu-id="87bfb-117">Die MVC `ConfigureServices()` -Dienste werden von der Dependency Injection Framework-Methode registriert.</span><span class="sxs-lookup"><span data-stu-id="87bfb-117">The MVC services are registered by the dependency injection framework's `ConfigureServices()` method.</span></span> <span data-ttu-id="87bfb-118">Darüber hinaus wird die Bereitstellung statischer Inhalte nicht standardmäßig durch die leere Vorlage aktiviert, sodass der `Configure()` Methode die statische Datei Middleware hinzugefügt wird:</span><span class="sxs-lookup"><span data-stu-id="87bfb-118">Additionally, the empty template doesn't enable serving static content by default, so the static files middleware is added to the `Configure()` method:</span></span>

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

### <a name="wwwroot-folder"></a><span data-ttu-id="87bfb-119">WWWRoot-Ordner</span><span class="sxs-lookup"><span data-stu-id="87bfb-119">wwwroot folder</span></span>

<span data-ttu-id="87bfb-120">In ASP.net Core ist der Webstammordner, in dem die Anwendung nach statischen Dateien sucht.</span><span class="sxs-lookup"><span data-stu-id="87bfb-120">In ASP.NET Core, the web root folder is where the application looks for static files.</span></span>

### <a name="indexcshtml"></a><span data-ttu-id="87bfb-121">Index. cshtml</span><span class="sxs-lookup"><span data-stu-id="87bfb-121">Index.cshtml</span></span>

<span data-ttu-id="87bfb-122">ASP.net Core behandelt Dateien namens " *Index* " als Standard/Homepage für die Website.</span><span class="sxs-lookup"><span data-stu-id="87bfb-122">ASP.NET Core treats files called *Index* as the default/home page for the site.</span></span> <span data-ttu-id="87bfb-123">Wenn Ihre Browser-URL auf den Stamm der Website zeigt, wird **Index. cshtml** als Startseite für Ihre Anwendung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="87bfb-123">When your browser URL points to the root of the site, **Index.cshtml** will be displayed as the home page for your application.</span></span>

### <a name="appmanifest-folder"></a><span data-ttu-id="87bfb-124">AppManifest-Ordner</span><span class="sxs-lookup"><span data-stu-id="87bfb-124">AppManifest folder</span></span>

<span data-ttu-id="87bfb-125">Dieser Ordner enthält die folgenden erforderlichen App-Paketdateien:</span><span class="sxs-lookup"><span data-stu-id="87bfb-125">This folder contains the following required app package files:</span></span>

- <span data-ttu-id="87bfb-126">Ein **vollfarbiges Symbol** , das 192 x 192 Pixel misst.</span><span class="sxs-lookup"><span data-stu-id="87bfb-126">A **full color icon** measuring 192 x 192 pixels.</span></span>
- <span data-ttu-id="87bfb-127">Ein **transparentes Umrisssymbol** , das 32 x 32 Pixel misst.</span><span class="sxs-lookup"><span data-stu-id="87bfb-127">A **transparent outline icon** measuring 32 x 32 pixels.</span></span>
- <span data-ttu-id="87bfb-128">Eine **Manifest. JSON** -Datei, die die Attribute Ihrer APP angibt.</span><span class="sxs-lookup"><span data-stu-id="87bfb-128">A **manifest.json** file that specifies the attributes of your app.</span></span>

<span data-ttu-id="87bfb-129">Diese Dateien müssen in einem App-Paket gezippt werden, damit Sie Ihre Registerkarte in Microsoft Teams hochladen können.</span><span class="sxs-lookup"><span data-stu-id="87bfb-129">These files need to be zipped in an app package for use in uploading your tab to Teams.</span></span> <span data-ttu-id="87bfb-130">Microsoft Teams lädt das `contentUrl` angegebene in ihrem Manifest, bettet es in einen iframe ein und rendert es in ihrer Registerkarte.</span><span class="sxs-lookup"><span data-stu-id="87bfb-130">Microsoft Teams will load the `contentUrl` specified in your manifest, embed it in an IFrame, and render it in your tab.</span></span>

### <a name="csproj"></a><span data-ttu-id="87bfb-131">. csproj</span><span class="sxs-lookup"><span data-stu-id="87bfb-131">.csproj</span></span>

<span data-ttu-id="87bfb-132">Klicken Sie im Fenster Visual Studio Projektmappen-Explorer mit der rechten Maustaste auf das Projekt, und wählen Sie **Projektdatei bearbeiten**aus.</span><span class="sxs-lookup"><span data-stu-id="87bfb-132">In the Visual Studio Solution Explorer window right-click on the project and select **Edit Project File**.</span></span> <span data-ttu-id="87bfb-133">Unten in der Datei sehen Sie den Code, der Ihren ZIP-Ordner erstellt und aktualisiert, wenn die Anwendung erstellt wird:</span><span class="sxs-lookup"><span data-stu-id="87bfb-133">At the bottom of the file you'll see the code that creates and updates your zip folder when the application builds:</span></span>

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

- <span data-ttu-id="87bfb-134">Öffnen Sie eine Eingabeaufforderung im Stammverzeichnis des Projektverzeichnisses, und führen Sie den folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="87bfb-134">Open a command prompt in the root of your project directory and run the following command:</span></span>

```bash
ngrok http https://localhost:44325 -host-header="localhost:44325"
```

- <span data-ttu-id="87bfb-135">Ngrok wird Anfragen aus dem Internet abhören und wird Sie an Ihre Anwendung weiterleiten, wenn Sie auf Port 44325 läuft.</span><span class="sxs-lookup"><span data-stu-id="87bfb-135">Ngrok will listen to requests from the internet and will route them to your application when it is running on port 44325.</span></span>  <span data-ttu-id="87bfb-136">Es sollte ähneln `https://y8rPrT2b.ngrok.io/` , wo *y8rPrT2b* durch ihre ngrok Alpha-numerische HTTPS-URL ersetzt wird.</span><span class="sxs-lookup"><span data-stu-id="87bfb-136">It should resemble `https://y8rPrT2b.ngrok.io/` where *y8rPrT2b* is replaced by your ngrok alpha-numeric HTTPS URL.</span></span>

- <span data-ttu-id="87bfb-137">Achten Sie darauf, dass Sie die Eingabeaufforderung mit ngrok weiterhin ausführen, und notieren Sie sich die URL, die Sie später benötigen.</span><span class="sxs-lookup"><span data-stu-id="87bfb-137">Be sure to keep the command prompt with ngrok running, and to make a note of the URL—you'll need it later.</span></span>

- <span data-ttu-id="87bfb-138">Stellen Sie sicher, dass *ngrok* ausgeführt wird und ordnungsgemäß funktioniert, indem Sie Ihren Browser öffnen und zu ihrer Inhaltsseite über die ngrok-HTTPS-URL wechseln, die in Ihrem Eingabeaufforderungsfenster bereitgestellt wurde.</span><span class="sxs-lookup"><span data-stu-id="87bfb-138">Verify that *ngrok* is running and working properly by opening your browser and going to your content page via the ngrok HTTPS URL that was provided in your command prompt window.</span></span>

>[!TIP]
><span data-ttu-id="87bfb-139">Sie müssen sowohl Ihre Anwendung in Visual Studio als auch ngrok ausführen, um diesen Schnellstart abzuschließen.</span><span class="sxs-lookup"><span data-stu-id="87bfb-139">You need to have both your application in Visual Studio and ngrok running to complete this quickstart.</span></span> <span data-ttu-id="87bfb-140">Wenn Sie die Ausführung der Anwendung in Visual Studio beenden müssen, um Sie zu bearbeiten, **halten Sie ngrok auf dem laufenden**.</span><span class="sxs-lookup"><span data-stu-id="87bfb-140">If you need to stop running your application in Visual Studio to work on it, **keep ngrok running**.</span></span> <span data-ttu-id="87bfb-141">Sie wird weiterhin überwacht und setzt die Weiterleitung der Anforderung Ihrer Anwendung fort, wenn Sie in Visual Studio neu gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="87bfb-141">It will continue to listen and will resume routing your application's request when it restarts in Visual Studio.</span></span> <span data-ttu-id="87bfb-142">Wenn Sie den ngrok-Dienst neu starten müssen, wird eine neue URL zurückgegeben, und Sie müssen jeden Ort aktualisieren, der diese URL verwendet.</span><span class="sxs-lookup"><span data-stu-id="87bfb-142">If you have to restart the ngrok service it will return a new URL and you'll have to update every place that uses that URL.</span></span>

### <a name="run-your-application"></a><span data-ttu-id="87bfb-143">Ausführen Ihrer Anwendung</span><span class="sxs-lookup"><span data-stu-id="87bfb-143">Run your application</span></span>

- <span data-ttu-id="87bfb-144">Drücken Sie in Visual Studio **F5** , oder klicken Sie im Menü **Debuggen** Ihrer Anwendung auf **Debuggen starten** .</span><span class="sxs-lookup"><span data-stu-id="87bfb-144">In Visual Studio press **F5** or choose **Start Debugging** from your application's **Debug** menu.</span></span>

[!INCLUDE [dotnet-personal-use-appstudio](~/includes/tabs/dotnet-personal-use-appstudio.md)]