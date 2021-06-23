---
title: Erstellen einer persönlichen Registerkarte mit ASP.NET Core
author: surbhigupta
description: Eine Schnellstartanleitung zum Erstellen einer benutzerdefinierten persönlichen Registerkarte mit ASP.NET Core.
ms.topic: quickstart
localization_priority: Normal
ms.author: lajanuar
ms.openlocfilehash: a839ae126a2cfdb137b22108038dd15a4b47b95a
ms.sourcegitcommit: 623d81eb079d1842813265746a5fe0fe6311b196
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/22/2021
ms.locfileid: "53069044"
---
# <a name="create-a-personal-tab-using-aspnetcore"></a><span data-ttu-id="f37ef-103">Erstellen einer persönlichen Registerkarte mit ASP.NETCore</span><span class="sxs-lookup"><span data-stu-id="f37ef-103">Create a personal tab using ASP.NETCore</span></span>

<span data-ttu-id="f37ef-104">In dieser Schnellstartanleitung werden wir schrittweise durch das Erstellen einer benutzerdefinierten persönlichen Registerkarte mit C# und ASP.Net Core Razor-Seiten geführt.</span><span class="sxs-lookup"><span data-stu-id="f37ef-104">In this quickstart, we'll walk-through creating a custom personal tab with C# and ASP.Net Core Razor pages.</span></span> <span data-ttu-id="f37ef-105">Wir verwenden App Studio auch [für Microsoft Teams,](~/concepts/build-and-test/app-studio-overview.md) um Ihr App-Manifest fertig zu stellen und Ihre Registerkarte für Teams bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="f37ef-105">We'll also use [App Studio for Microsoft Teams](~/concepts/build-and-test/app-studio-overview.md) to finalize your app manifest and deploy your tab to Teams.</span></span>

[!INCLUDE [dotnet-core-prereq](~/includes/tabs/dotnet-core-prereq.md)]

## <a name="get-the-source-code"></a><span data-ttu-id="f37ef-106">Abrufen des Quellcodes</span><span class="sxs-lookup"><span data-stu-id="f37ef-106">Get the source code</span></span>

<span data-ttu-id="f37ef-107">Öffnen Sie eine Eingabeaufforderung, und erstellen Sie ein neues Verzeichnis für Ihr Registerkartenprojekt.</span><span class="sxs-lookup"><span data-stu-id="f37ef-107">Open a command prompt and create a new directory for your tab project.</span></span> <span data-ttu-id="f37ef-108">Wir haben ein einfaches Projekt bereitgestellt, um Ihnen den Einstieg zu erleichtern.</span><span class="sxs-lookup"><span data-stu-id="f37ef-108">We have provided a simple project to get you started.</span></span> <span data-ttu-id="f37ef-109">Um den Quellcode abzurufen, können Sie den ZIP-Ordner herunterladen und die Dateien extrahieren oder das Beispiel-Repository in Ihr neues Verzeichnis klonen:</span><span class="sxs-lookup"><span data-stu-id="f37ef-109">To retrieve the source code you can download the zip folder and extract the files or clone the sample repository into your new directory:</span></span>

```bash
git clone https://github.com/OfficeDev/microsoft-teams-sample-tabs.git
```

<span data-ttu-id="f37ef-110">Sobald Sie den Quellcode haben, öffnen Sie Visual Studio, und wählen Sie **Projekt oder Projektmappe öffnen** aus.</span><span class="sxs-lookup"><span data-stu-id="f37ef-110">Once you have the source code, open Visual Studio and select **Open a project or solution**.</span></span> <span data-ttu-id="f37ef-111">Navigieren Sie zum Registerkartenanwendungsverzeichnis, und öffnen Sie **"PersonalTab.sln".**</span><span class="sxs-lookup"><span data-stu-id="f37ef-111">Navigate to the tab application directory and open **PersonalTab.sln**.</span></span>

<span data-ttu-id="f37ef-112">Drücken Sie **F5,** oder wählen Sie im Menü **"Debuggen"** die Option **"Debuggen starten"** aus, um die Anwendung zu erstellen und auszuführen.</span><span class="sxs-lookup"><span data-stu-id="f37ef-112">To build and run your application press **F5** or choose **Start Debugging** from the **Debug** menu.</span></span> <span data-ttu-id="f37ef-113">Navigieren Sie in einem Browser zu den folgenden URLs, um zu überprüfen, ob die Anwendung ordnungsgemäß geladen wurde:</span><span class="sxs-lookup"><span data-stu-id="f37ef-113">In a browser navigate to the URLs below to verify the application loaded properly:</span></span>

- `http://localhost:44325/`
- `http://localhost:44325/personal`
- `http://localhost:44325/privacy`
- `http://localhost:44325/tou`

## <a name="review-the-source-code"></a><span data-ttu-id="f37ef-114">Überprüfen des Quellcodes</span><span class="sxs-lookup"><span data-stu-id="f37ef-114">Review the source code</span></span>

### <a name="startupcs"></a><span data-ttu-id="f37ef-115">Startup.cs</span><span class="sxs-lookup"><span data-stu-id="f37ef-115">Startup.cs</span></span>

<span data-ttu-id="f37ef-116">Dieses Projekt wurde aus einer leeren Vorlage für ASP.NET Core 2.2-Webanwendung erstellt, wobei das Kontrollkästchen **"Erweitert – Für HTTPS konfigurieren"** beim Setup aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="f37ef-116">This project was created from an ASP.NET Core 2.2 Web Application empty template with the **Advanced - Configure for HTTPS** check box selected at setup.</span></span> <span data-ttu-id="f37ef-117">Die MVC-Dienste werden durch die Methode des Abhängigkeitsinjektionsframeworks `ConfigureServices()` registriert.</span><span class="sxs-lookup"><span data-stu-id="f37ef-117">The MVC services are registered by the dependency injection framework's `ConfigureServices()` method.</span></span> <span data-ttu-id="f37ef-118">Darüber hinaus ermöglicht die leere Vorlage nicht standardmäßig die Bereitstellung statischer Inhalte, sodass die Middleware für statische Dateien der Methode hinzugefügt `Configure()` wird:</span><span class="sxs-lookup"><span data-stu-id="f37ef-118">Additionally, the empty template doesn't enable serving static content by default, so the static files middleware is added to the `Configure()` method:</span></span>

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

### <a name="wwwroot-folder"></a><span data-ttu-id="f37ef-119">Wwwroot-Ordner</span><span class="sxs-lookup"><span data-stu-id="f37ef-119">wwwroot folder</span></span>

<span data-ttu-id="f37ef-120">In ASP.NET Core sucht die Anwendung im Webstammordner nach statischen Dateien.</span><span class="sxs-lookup"><span data-stu-id="f37ef-120">In ASP.NET Core, the web root folder is where the application looks for static files.</span></span>

### <a name="indexcshtml"></a><span data-ttu-id="f37ef-121">Index.cshtml</span><span class="sxs-lookup"><span data-stu-id="f37ef-121">Index.cshtml</span></span>

<span data-ttu-id="f37ef-122">ASP.NET Core behandelt Dateien mit dem Namen *Index* als Standard-/Startseite für die Website.</span><span class="sxs-lookup"><span data-stu-id="f37ef-122">ASP.NET Core treats files called *Index* as the default/home page for the site.</span></span> <span data-ttu-id="f37ef-123">Wenn Ihre Browser-URL auf den Stamm der Website zeigt, wird **Index.cshtml** als Startseite für Ihre Anwendung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="f37ef-123">When your browser URL points to the root of the site, **Index.cshtml** will be displayed as the home page for your application.</span></span>

### <a name="appmanifest-folder"></a><span data-ttu-id="f37ef-124">AppManifest-Ordner</span><span class="sxs-lookup"><span data-stu-id="f37ef-124">AppManifest folder</span></span>

<span data-ttu-id="f37ef-125">Dieser Ordner enthält die folgenden erforderlichen App-Paketdateien:</span><span class="sxs-lookup"><span data-stu-id="f37ef-125">This folder contains the following required app package files:</span></span>

- <span data-ttu-id="f37ef-126">Ein **Vollfarbsymbol** mit einer Auflösung von 192 x 192 Pixeln.</span><span class="sxs-lookup"><span data-stu-id="f37ef-126">A **full color icon** measuring 192 x 192 pixels.</span></span>
- <span data-ttu-id="f37ef-127">Ein **transparentes Gliederungssymbol** mit einer Auflösung von 32 x 32 Pixeln.</span><span class="sxs-lookup"><span data-stu-id="f37ef-127">A **transparent outline icon** measuring 32 x 32 pixels.</span></span>
- <span data-ttu-id="f37ef-128">Ein **manifest.jsfür** die Datei, die die Attribute Ihrer App angibt.</span><span class="sxs-lookup"><span data-stu-id="f37ef-128">A **manifest.json** file that specifies the attributes of your app.</span></span>

<span data-ttu-id="f37ef-129">Diese Dateien müssen in einem App-Paket gezippt werden, um Ihre Registerkarte in Teams hochzuladen.</span><span class="sxs-lookup"><span data-stu-id="f37ef-129">These files need to be zipped in an app package for use in uploading your tab to Teams.</span></span> <span data-ttu-id="f37ef-130">Microsoft Teams lädt das `contentUrl` angegebene Element in Ihrem Manifest, betten es in einen <iframe ein \> und rendert es auf der Registerkarte.</span><span class="sxs-lookup"><span data-stu-id="f37ef-130">Microsoft Teams will load the `contentUrl` specified in your manifest, embed it in an <iframe\>, and render it in your tab.</span></span>

### <a name="csproj"></a><span data-ttu-id="f37ef-131">CSPROJ</span><span class="sxs-lookup"><span data-stu-id="f37ef-131">.csproj</span></span>

<span data-ttu-id="f37ef-132">Klicken Sie im Fenster Visual Studio Projektmappen-Explorer mit der rechten Maustaste auf das Projekt, und wählen Sie **"Bearbeiten Project Datei"** aus.</span><span class="sxs-lookup"><span data-stu-id="f37ef-132">In the Visual Studio Solution Explorer window, right-click on the project and select **Edit Project File**.</span></span> <span data-ttu-id="f37ef-133">Am Ende der Datei sehen Sie den Code, der Ihren ZIP-Ordner erstellt und aktualisiert, wenn die Anwendung erstellt wird:</span><span class="sxs-lookup"><span data-stu-id="f37ef-133">At the bottom of the file you'll see the code that creates and updates your zip folder when the application builds:</span></span>

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

- <span data-ttu-id="f37ef-134">Öffnen Sie eine Eingabeaufforderung im Stammverzeichnis des Projekts, und führen Sie den folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="f37ef-134">Open a command prompt in the root of your project directory and run the following command:</span></span>

    ```bash
    ngrok http https://localhost:44325 -host-header="localhost:44325"
    ```

- <span data-ttu-id="f37ef-135">Ngrok lauscht auf Anforderungen aus dem Internet und leitet sie an Ihre Anwendung weiter, wenn sie an Port 44325 ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="f37ef-135">Ngrok will listen to requests from the internet and will route them to your application when it is running on port 44325.</span></span>  <span data-ttu-id="f37ef-136">Es sollte etwa so `https://y8rPrT2b.ngrok.io/` aussehen, wo *y8rPrT2b* durch Ihre alphangrok-numerische HTTPS-URL ersetzt wird.</span><span class="sxs-lookup"><span data-stu-id="f37ef-136">It should resemble `https://y8rPrT2b.ngrok.io/` where *y8rPrT2b* is replaced by your ngrok alpha-numeric HTTPS URL.</span></span>

- <span data-ttu-id="f37ef-137">Achten Sie darauf, dass die Eingabeaufforderung mit ngrok ausgeführt wird, und notieren Sie sich die URL . Sie benötigen sie später.</span><span class="sxs-lookup"><span data-stu-id="f37ef-137">Be sure to keep the command prompt with ngrok running, and to make a note of the URL — you'll need it later.</span></span>

- <span data-ttu-id="f37ef-138">Stellen Sie sicher, dass **ngrok** ausgeführt wird und ordnungsgemäß funktioniert, indem Sie Ihren Browser öffnen und über die ngrok-HTTPS-URL, die im Eingabeaufforderungsfenster bereitgestellt wurde, zur Inhaltsseite wechseln.</span><span class="sxs-lookup"><span data-stu-id="f37ef-138">Verify that **ngrok** is running and working properly by opening your browser and going to your content page via the ngrok HTTPS URL that was provided in your command prompt window.</span></span>

>[!TIP]
><span data-ttu-id="f37ef-139">Sie müssen ihre Anwendung sowohl in Visual Studio als auch in ngrok ausführen, um diese Schnellstartanleitung abzuschließen.</span><span class="sxs-lookup"><span data-stu-id="f37ef-139">You need to have both your application in Visual Studio and ngrok running to complete this quickstart.</span></span> <span data-ttu-id="f37ef-140">Wenn Sie die Ausführung der Anwendung in Visual Studio beenden müssen, um daran zu arbeiten, **führen Sie ngrok weiter aus.**</span><span class="sxs-lookup"><span data-stu-id="f37ef-140">If you need to stop running your application in Visual Studio to work on it, **keep ngrok running**.</span></span> <span data-ttu-id="f37ef-141">Sie lauscht weiterhin und setzt das Routing der Anforderung Ihrer Anwendung fort, wenn sie in Visual Studio neu gestartet wird.</span><span class="sxs-lookup"><span data-stu-id="f37ef-141">It will continue to listen and will resume routing your application's request when it restarts in Visual Studio.</span></span> <span data-ttu-id="f37ef-142">Wenn Sie den ngrok-Dienst neu starten müssen, wird eine neue URL zurückgegeben, und Sie müssen jeden Ort aktualisieren, der diese URL verwendet.</span><span class="sxs-lookup"><span data-stu-id="f37ef-142">If you have to restart the ngrok service it will return a new URL and you'll have to update every place that uses that URL.</span></span>

### <a name="run-your-application"></a><span data-ttu-id="f37ef-143">Ausführen der Anwendung</span><span class="sxs-lookup"><span data-stu-id="f37ef-143">Run your application</span></span>

- <span data-ttu-id="f37ef-144">Drücken Sie in Visual Studio **F5,** oder wählen Sie **"Debuggen starten"** aus dem **Menü "Debuggen"** der Anwendung aus.</span><span class="sxs-lookup"><span data-stu-id="f37ef-144">In Visual Studio press **F5** or choose **Start Debugging** from your application's **Debug** menu.</span></span>

[!INCLUDE [dotnet-personal-use-appstudio](~/includes/tabs/dotnet-personal-use-appstudio.md)]

## <a name="next-step"></a><span data-ttu-id="f37ef-145">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="f37ef-145">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="f37ef-146">Erstellen einer benutzerdefinierten persönlichen Registerkarte mit ASP.NETCore MVC</span><span class="sxs-lookup"><span data-stu-id="f37ef-146">Create a Custom Personal Tab with ASP.NETCore MVC</span></span>](~/tabs/quickstarts/create-personal-tab-dotnet-core-mvc.md)
