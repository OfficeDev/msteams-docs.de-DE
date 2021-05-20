---
title: Erstellen einer persönlichen Registerkarte mit ASP.NET Core
author: laujan
description: Eine Schnellstartanleitung zum Erstellen einer benutzerdefinierten persönlichen Registerkarte mit ASP.NET Core.
ms.topic: quickstart
localization_priority: Normal
ms.author: lajanuar
ms.openlocfilehash: 41aa916f4c69d50e48254d0f4934109429dab83c
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566894"
---
# <a name="create-a-personal-tab-using-aspnetcore"></a><span data-ttu-id="ce5c0-103">Erstellen einer persönlichen Registerkarte mit ASP.NETCore</span><span class="sxs-lookup"><span data-stu-id="ce5c0-103">Create a personal tab using ASP.NETCore</span></span>

<span data-ttu-id="ce5c0-104">In dieser Schnellstartanleitung werden wir eine benutzerdefinierte persönliche Registerkarte mit den Seiten "C" und ASP.Net Core Razor erstellen.</span><span class="sxs-lookup"><span data-stu-id="ce5c0-104">In this quickstart, we'll walk-through creating a custom personal tab with C# and ASP.Net Core Razor pages.</span></span> <span data-ttu-id="ce5c0-105">Wir verwenden App Studio auch [für Microsoft Teams,](~/concepts/build-and-test/app-studio-overview.md) um Ihr App-Manifest fertigzustellen und Ihre Registerkarte auf Teams bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="ce5c0-105">We'll also use [App Studio for Microsoft Teams](~/concepts/build-and-test/app-studio-overview.md) to finalize your app manifest and deploy your tab to Teams.</span></span>

[!INCLUDE [dotnet-core-prereq](~/includes/tabs/dotnet-core-prereq.md)]

## <a name="get-the-source-code"></a><span data-ttu-id="ce5c0-106">Abrufen des Quellcodes</span><span class="sxs-lookup"><span data-stu-id="ce5c0-106">Get the source code</span></span>

<span data-ttu-id="ce5c0-107">Öffnen Sie eine Eingabeaufforderung, und erstellen Sie ein neues Verzeichnis für Ihr Registerkartenprojekt.</span><span class="sxs-lookup"><span data-stu-id="ce5c0-107">Open a command prompt and create a new directory for your tab project.</span></span> <span data-ttu-id="ce5c0-108">Wir haben ein einfaches Projekt zur Verfügung gestellt, um Ihnen den Einstieg zu erleichtern.</span><span class="sxs-lookup"><span data-stu-id="ce5c0-108">We have provided a simple project to get you started.</span></span> <span data-ttu-id="ce5c0-109">Um den Quellcode abzurufen, können Sie den ZIP-Ordner herunterladen und die Dateien extrahieren oder das Beispiel-Repository in Ihr neues Verzeichnis klonen:</span><span class="sxs-lookup"><span data-stu-id="ce5c0-109">To retrieve the source code you can download the zip folder and extract the files or clone the sample repository into your new directory:</span></span>

```bash
git clone https://github.com/OfficeDev/microsoft-teams-sample-tabs.git
```

<span data-ttu-id="ce5c0-110">Sobald Sie den Quellcode haben, öffnen Sie Visual Studio und wählen Sie **Projekt oder Projektmappe öffnen** aus.</span><span class="sxs-lookup"><span data-stu-id="ce5c0-110">Once you have the source code, open Visual Studio and select **Open a project or solution**.</span></span> <span data-ttu-id="ce5c0-111">Navigieren Sie zum Registerkartenanwendungsverzeichnis, und öffnen Sie **PersonalTab.sln**.</span><span class="sxs-lookup"><span data-stu-id="ce5c0-111">Navigate to the tab application directory and open **PersonalTab.sln**.</span></span>

<span data-ttu-id="ce5c0-112">Um Ihre Anwendung zu erstellen und auszuführen, drücken Sie **F5** oder wählen Sie **Debuggen** starten im **Debugmenü** aus.</span><span class="sxs-lookup"><span data-stu-id="ce5c0-112">To build and run your application press **F5** or choose **Start Debugging** from the **Debug** menu.</span></span> <span data-ttu-id="ce5c0-113">Navigieren Sie in einem Browser zu den folgenden URLs, um die ordnungsgemäß geladene Anwendung zu überprüfen:</span><span class="sxs-lookup"><span data-stu-id="ce5c0-113">In a browser navigate to the URLs below to verify the application loaded properly:</span></span>

- `http://localhost:44325/`
- `http://localhost:44325/personal`
- `http://localhost:44325/privacy`
- `http://localhost:44325/tou`

## <a name="review-the-source-code"></a><span data-ttu-id="ce5c0-114">Überprüfen des Quellcodes</span><span class="sxs-lookup"><span data-stu-id="ce5c0-114">Review the source code</span></span>

### <a name="startupcs"></a><span data-ttu-id="ce5c0-115">Startup.cs</span><span class="sxs-lookup"><span data-stu-id="ce5c0-115">Startup.cs</span></span>

<span data-ttu-id="ce5c0-116">Dieses Projekt wurde aus einer leeren Vorlage ASP.NET Core 2.2 Web Application mit dem Kontrollkästchen **Erweitert - Konfigurieren für HTTPS** erstellt, das bei Setup ausgewählt wurde.</span><span class="sxs-lookup"><span data-stu-id="ce5c0-116">This project was created from an ASP.NET Core 2.2 Web Application empty template with the **Advanced - Configure for HTTPS** check box selected at setup.</span></span> <span data-ttu-id="ce5c0-117">Die MVC-Dienste werden von der Methode des Abhängigkeitsinjektionsframeworks `ConfigureServices()` registriert.</span><span class="sxs-lookup"><span data-stu-id="ce5c0-117">The MVC services are registered by the dependency injection framework's `ConfigureServices()` method.</span></span> <span data-ttu-id="ce5c0-118">Darüber hinaus ermöglicht die leere Vorlage standardmäßig nicht die Bereitstellung statischer Inhalte, sodass die Middleware für statische Dateien der Methode hinzugefügt `Configure()` wird:</span><span class="sxs-lookup"><span data-stu-id="ce5c0-118">Additionally, the empty template doesn't enable serving static content by default, so the static files middleware is added to the `Configure()` method:</span></span>

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

### <a name="wwwroot-folder"></a><span data-ttu-id="ce5c0-119">wwwroot-Ordner</span><span class="sxs-lookup"><span data-stu-id="ce5c0-119">wwwroot folder</span></span>

<span data-ttu-id="ce5c0-120">In ASP.NET Core ist der Webstammordner der Ort, an dem die Anwendung nach statischen Dateien sucht.</span><span class="sxs-lookup"><span data-stu-id="ce5c0-120">In ASP.NET Core, the web root folder is where the application looks for static files.</span></span>

### <a name="indexcshtml"></a><span data-ttu-id="ce5c0-121">Index.cshtml</span><span class="sxs-lookup"><span data-stu-id="ce5c0-121">Index.cshtml</span></span>

<span data-ttu-id="ce5c0-122">ASP.NET Core behandelt Dateien mit dem Namen *Index* als Standard-/Homepage für die Website.</span><span class="sxs-lookup"><span data-stu-id="ce5c0-122">ASP.NET Core treats files called *Index* as the default/home page for the site.</span></span> <span data-ttu-id="ce5c0-123">Wenn Ihre Browser-URL auf den Stamm der Website verweist, wird **Index.cshtml** als Homepage für Ihre Anwendung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="ce5c0-123">When your browser URL points to the root of the site, **Index.cshtml** will be displayed as the home page for your application.</span></span>

### <a name="appmanifest-folder"></a><span data-ttu-id="ce5c0-124">AppManifest-Ordner</span><span class="sxs-lookup"><span data-stu-id="ce5c0-124">AppManifest folder</span></span>

<span data-ttu-id="ce5c0-125">Dieser Ordner enthält die folgenden erforderlichen App-Paketdateien:</span><span class="sxs-lookup"><span data-stu-id="ce5c0-125">This folder contains the following required app package files:</span></span>

- <span data-ttu-id="ce5c0-126">Ein **Vollfarbsymbol** mit 192 x 192 Pixeln.</span><span class="sxs-lookup"><span data-stu-id="ce5c0-126">A **full color icon** measuring 192 x 192 pixels.</span></span>
- <span data-ttu-id="ce5c0-127">Ein **transparentes Umrisssymbol** mit 32 x 32 Pixeln.</span><span class="sxs-lookup"><span data-stu-id="ce5c0-127">A **transparent outline icon** measuring 32 x 32 pixels.</span></span>
- <span data-ttu-id="ce5c0-128">Eine **manifest.jsin der** Datei, die die Attribute Ihrer App angibt.</span><span class="sxs-lookup"><span data-stu-id="ce5c0-128">A **manifest.json** file that specifies the attributes of your app.</span></span>

<span data-ttu-id="ce5c0-129">Diese Dateien müssen in einem App-Paket gezippt werden, damit Sie Ihre Registerkarte in Teams hochladen können.</span><span class="sxs-lookup"><span data-stu-id="ce5c0-129">These files need to be zipped in an app package for use in uploading your tab to Teams.</span></span> <span data-ttu-id="ce5c0-130">Microsoft Teams lädt das `contentUrl` in Ihrem Manifest angegebene, bettet es in ein <iframe ein \> und rendert es in Der Registerkarte.</span><span class="sxs-lookup"><span data-stu-id="ce5c0-130">Microsoft Teams will load the `contentUrl` specified in your manifest, embed it in an <iframe\>, and render it in your tab.</span></span>

### <a name="csproj"></a><span data-ttu-id="ce5c0-131">.csproj</span><span class="sxs-lookup"><span data-stu-id="ce5c0-131">.csproj</span></span>

<span data-ttu-id="ce5c0-132">Klicken Sie im Fenster Visual Studio Projektmappen-Explorer mit der rechten Maustaste auf das Projekt, und wählen Sie **Project Datei bearbeiten** aus.</span><span class="sxs-lookup"><span data-stu-id="ce5c0-132">In the Visual Studio Solution Explorer window, right-click on the project and select **Edit Project File**.</span></span> <span data-ttu-id="ce5c0-133">Am unteren Rand der Datei sehen Sie den Code, der Ihren ZIP-Ordner erstellt und aktualisiert, wenn die Anwendung erstellt wird:</span><span class="sxs-lookup"><span data-stu-id="ce5c0-133">At the bottom of the file you'll see the code that creates and updates your zip folder when the application builds:</span></span>

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

- <span data-ttu-id="ce5c0-134">Öffnen Sie eine Eingabeaufforderung im Stammverzeichnis Ihres Projektverzeichnisses, und führen Sie den folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="ce5c0-134">Open a command prompt in the root of your project directory and run the following command:</span></span>

    ```bash
    ngrok http https://localhost:44325 -host-header="localhost:44325"
    ```

- <span data-ttu-id="ce5c0-135">Ngrok hört Anfragen aus dem Internet ab und leitet sie an Ihre Anwendung weiter, wenn sie auf Port 44325 ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="ce5c0-135">Ngrok will listen to requests from the internet and will route them to your application when it is running on port 44325.</span></span>  <span data-ttu-id="ce5c0-136">Es sollte der Stelle ähneln, an der `https://y8rPrT2b.ngrok.io/` *y8rPrT2b* durch Ihre alphanumerische HTTPS-URL von ngrok ersetzt wird.</span><span class="sxs-lookup"><span data-stu-id="ce5c0-136">It should resemble `https://y8rPrT2b.ngrok.io/` where *y8rPrT2b* is replaced by your ngrok alpha-numeric HTTPS URL.</span></span>

- <span data-ttu-id="ce5c0-137">Achten Sie darauf, die Eingabeaufforderung zu halten, wenn ngrok ausgeführt wird, und notieren Sie sich die URL – Sie werden sie später benötigen.</span><span class="sxs-lookup"><span data-stu-id="ce5c0-137">Be sure to keep the command prompt with ngrok running, and to make a note of the URL — you'll need it later.</span></span>

- <span data-ttu-id="ce5c0-138">Stellen Sie sicher, dass **ngrok** ordnungsgemäß ausgeführt wird und ordnungsgemäß funktioniert, indem Sie Ihren Browser öffnen und über die ngrok HTTPS-URL, die in Ihrem Eingabeaufforderungsfenster bereitgestellt wurde, zur Inhaltsseite wechseln.</span><span class="sxs-lookup"><span data-stu-id="ce5c0-138">Verify that **ngrok** is running and working properly by opening your browser and going to your content page via the ngrok HTTPS URL that was provided in your command prompt window.</span></span>

>[!TIP]
><span data-ttu-id="ce5c0-139">Sie müssen sowohl Ihre Anwendung in Visual Studio als auch ngrok ausführen, um diese Schnellstartanleitung abzuschließen.</span><span class="sxs-lookup"><span data-stu-id="ce5c0-139">You need to have both your application in Visual Studio and ngrok running to complete this quickstart.</span></span> <span data-ttu-id="ce5c0-140">Wenn Sie die Ausführung Ihrer Anwendung in Visual Studio beenden müssen, um daran zu arbeiten, **führen Sie ngrok aus.**</span><span class="sxs-lookup"><span data-stu-id="ce5c0-140">If you need to stop running your application in Visual Studio to work on it, **keep ngrok running**.</span></span> <span data-ttu-id="ce5c0-141">Sie wird weiterhin überwacht und die Weiterleitung der Anforderung Ihrer Anwendung fortgesetzt, wenn sie in Visual Studio neu gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="ce5c0-141">It will continue to listen and will resume routing your application's request when it restarts in Visual Studio.</span></span> <span data-ttu-id="ce5c0-142">Wenn Sie den ngrok-Dienst neu starten müssen, wird eine neue URL zurückgegeben, und Sie müssen jeden Ort aktualisieren, der diese URL verwendet.</span><span class="sxs-lookup"><span data-stu-id="ce5c0-142">If you have to restart the ngrok service it will return a new URL and you'll have to update every place that uses that URL.</span></span>

### <a name="run-your-application"></a><span data-ttu-id="ce5c0-143">Führen Sie Ihre Anwendung aus</span><span class="sxs-lookup"><span data-stu-id="ce5c0-143">Run your application</span></span>

- <span data-ttu-id="ce5c0-144">Drücken Sie Visual Studio **F5** oder wählen Sie **Debuggen** starten aus dem **Debug-Menü** Ihrer Anwendung aus.</span><span class="sxs-lookup"><span data-stu-id="ce5c0-144">In Visual Studio press **F5** or choose **Start Debugging** from your application's **Debug** menu.</span></span>

[!INCLUDE [dotnet-personal-use-appstudio](~/includes/tabs/dotnet-personal-use-appstudio.md)]

## <a name="next-step"></a><span data-ttu-id="ce5c0-145">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="ce5c0-145">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="ce5c0-146">Erstellen einer benutzerdefinierten persönlichen Registerkarte mit ASP.NETCore MVC</span><span class="sxs-lookup"><span data-stu-id="ce5c0-146">Create a Custom Personal Tab with ASP.NETCore MVC</span></span>](~/tabs/quickstarts/create-personal-tab-dotnet-core-mvc.md)
