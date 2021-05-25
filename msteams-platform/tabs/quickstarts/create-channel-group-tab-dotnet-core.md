---
title: Erstellen einer Kanal- und Gruppenregisterkarte mit ASP.NET Core
author: laujan
description: Eine Schnellstartanleitung zum Erstellen eines benutzerdefinierten Kanals und einer Gruppenregisterkarte mit ASP.NET Core.
localization_priority: Normal
ms.topic: quickstart
ms.author: lajanuar
ms.openlocfilehash: 1004e40e28875524ea1f38a3f6b3c2c53330fec1
ms.sourcegitcommit: e1fe46c574cec378319814f8213209ad3063b2c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2021
ms.locfileid: "52630370"
---
# <a name="create-a-custom-channel-and-group-tab-with-aspnetcore"></a><span data-ttu-id="2a081-103">Erstellen eines benutzerdefinierten Kanals und einer Registerkarte "Gruppe" mit ASP.NETCore</span><span class="sxs-lookup"><span data-stu-id="2a081-103">Create a Custom Channel and Group Tab with ASP.NETCore</span></span>

<span data-ttu-id="2a081-104">In diesem Schnellstart werden wir durch das Erstellen einer benutzerdefinierten Kanal-/Gruppenregisterkarte mit C# und ASP.Net Core -Gestochenseite gehen.</span><span class="sxs-lookup"><span data-stu-id="2a081-104">In this quickstart we'll walk-through creating a custom channel/group tab with C# and ASP.Net Core Razor page.</span></span> <span data-ttu-id="2a081-105">Außerdem verwenden wir [App Studio für Microsoft Teams,](~/concepts/build-and-test/app-studio-overview.md) um Ihr App-Manifest zu finalisieren und Ihre Registerkarte für die Teams.</span><span class="sxs-lookup"><span data-stu-id="2a081-105">We'll also use [App Studio for Microsoft Teams](~/concepts/build-and-test/app-studio-overview.md) to finalize your app manifest and deploy your tab to Teams.</span></span>

[!INCLUDE [dotnet-core-prereq](~/includes/tabs/dotnet-core-prereq.md)]

## <a name="get-the-source-code"></a><span data-ttu-id="2a081-106">Den Quellcode erhalten</span><span class="sxs-lookup"><span data-stu-id="2a081-106">Get the source code</span></span>

<span data-ttu-id="2a081-107">Öffnen Sie eine Eingabeaufforderung, und erstellen Sie ein neues Verzeichnis für Ihr Registerkartenprojekt.</span><span class="sxs-lookup"><span data-stu-id="2a081-107">Open a command prompt and create a new directory for your tab project.</span></span> <span data-ttu-id="2a081-108">Wir haben ein einfaches Projekt bereitgestellt, mit dem Sie beginnen können.</span><span class="sxs-lookup"><span data-stu-id="2a081-108">We have provided a simple project to get you started.</span></span> <span data-ttu-id="2a081-109">Zum Abrufen des Quellcodes können Sie den Zip-Ordner herunterladen und die Dateien extrahieren oder das Beispielrepository in Ihr neues Verzeichnis klonen:</span><span class="sxs-lookup"><span data-stu-id="2a081-109">To retrieve the source code you can download the zip folder and extract the files or clone the sample repository into your new directory:</span></span>

```bash
git clone https://github.com/OfficeDev/microsoft-teams-sample-tabs.git
```

<span data-ttu-id="2a081-110">Nachdem Sie den Quellcode verwendet haben, öffnen Sie Visual Studio, und wählen **Sie Projekt oder Projektmappe öffnen aus.**</span><span class="sxs-lookup"><span data-stu-id="2a081-110">Once you have the source code, open Visual Studio and select **Open a project or solution**.</span></span> <span data-ttu-id="2a081-111">Navigieren Sie zum Verzeichnis der Registerkartenanwendung, und öffnen **Sie ChannelGroupTab.sln**.</span><span class="sxs-lookup"><span data-stu-id="2a081-111">Navigate to the tab application directory and open **ChannelGroupTab.sln**.</span></span>

<span data-ttu-id="2a081-112">Drücken Sie **F5,** um die Anwendung zu erstellen und auszuführen, oder wählen Sie **Debuggen starten** im Menü **Debuggen** aus.</span><span class="sxs-lookup"><span data-stu-id="2a081-112">To build and run your application press **F5** or choose **Start Debugging** from the **Debug** menu.</span></span> <span data-ttu-id="2a081-113">Navigieren Sie in einem Browser zu den folgenden URLs, und überprüfen Sie, ob die Anwendung ordnungsgemäß geladen wurde:</span><span class="sxs-lookup"><span data-stu-id="2a081-113">In a browser navigate to the URLs below and verify the application loaded properly:</span></span>

- `http://localhost:44355`
- `http://localhost:44355/privacy`
- `http://localhost:44355/tou`

## <a name="review-the-source-code"></a><span data-ttu-id="2a081-114">Überprüfen des Quellcodes</span><span class="sxs-lookup"><span data-stu-id="2a081-114">Review the source code</span></span>

### <a name="startupcs"></a><span data-ttu-id="2a081-115">Startup.cs</span><span class="sxs-lookup"><span data-stu-id="2a081-115">Startup.cs</span></span>

<span data-ttu-id="2a081-116">Dieses Projekt wurde aus einer leeren ASP.NET Core 2.2-Webanwendung erstellt, deren Kontrollkästchen *Advanced – Configure for HTTPS* beim Setup aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="2a081-116">This project was created from an ASP.NET Core 2.2 Web Application empty template with the *Advanced - Configure for HTTPS* check box selected at setup.</span></span> <span data-ttu-id="2a081-117">Die MVC-Dienste werden von der Methode des Abhängigkeitsinjektionsframeworks `ConfigureServices()` registriert.</span><span class="sxs-lookup"><span data-stu-id="2a081-117">The MVC services are registered by the dependency injection framework's `ConfigureServices()` method.</span></span> <span data-ttu-id="2a081-118">Darüber hinaus ermöglicht die leere Vorlage die Standardmäßige Entladung statischer Inhalte nicht, sodass die Middleware für statische Dateien der Methode hinzugefügt `Configure()` wird:</span><span class="sxs-lookup"><span data-stu-id="2a081-118">Additionally, the empty template doesn't enable serving static content by default, so the static files middleware is added to the `Configure()` method:</span></span>

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

### <a name="wwwroot-folder"></a><span data-ttu-id="2a081-119">Ordner "wwwroot"</span><span class="sxs-lookup"><span data-stu-id="2a081-119">wwwroot folder</span></span>

<span data-ttu-id="2a081-120">In ASP.NET Core ist der Webstammordner der Ort, in dem die Anwendung nach statischen Dateien sucht.</span><span class="sxs-lookup"><span data-stu-id="2a081-120">In ASP.NET Core, the web root folder is where the application looks for static files.</span></span>

### <a name="indexcshtml"></a><span data-ttu-id="2a081-121">Index.cshtml</span><span class="sxs-lookup"><span data-stu-id="2a081-121">Index.cshtml</span></span>

<span data-ttu-id="2a081-122">ASP.NET Core behandelt Dateien mit dem Namen *Index* als Standard-/Homepage für die Website.</span><span class="sxs-lookup"><span data-stu-id="2a081-122">ASP.NET Core treats files called *Index* as the default/home page for the site.</span></span> <span data-ttu-id="2a081-123">Wenn Ihre Browser-URL auf den Stamm der Website verweist, wird **Index.cshtml** als Homepage für Ihre Anwendung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="2a081-123">When your browser URL points to the root of the site, **Index.cshtml** will be displayed as the home page for your application.</span></span>

### <a name="tabcs"></a><span data-ttu-id="2a081-124">Tab.cs</span><span class="sxs-lookup"><span data-stu-id="2a081-124">Tab.cs</span></span>

<span data-ttu-id="2a081-125">Diese C# enthält eine Methode, die während der Konfiguration von **Tab.cshtml** aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="2a081-125">This C# file contains a method that will be called from **Tab.cshtml** during configuration.</span></span>

### <a name="appmanifest-folder"></a><span data-ttu-id="2a081-126">Ordner "AppManifest"</span><span class="sxs-lookup"><span data-stu-id="2a081-126">AppManifest folder</span></span>

<span data-ttu-id="2a081-127">Dieser Ordner enthält die folgenden erforderlichen App-Paketdateien:</span><span class="sxs-lookup"><span data-stu-id="2a081-127">This folder contains the following required app package files:</span></span>

- <span data-ttu-id="2a081-128">Ein **Vollfarbsymbol** mit einer Breite von 192 x 192 Pixeln.</span><span class="sxs-lookup"><span data-stu-id="2a081-128">A **full color icon** measuring 192 x 192 pixels.</span></span>
- <span data-ttu-id="2a081-129">Ein **transparentes Gliederungssymbol** mit einer Breite von 32 x 32 Pixeln.</span><span class="sxs-lookup"><span data-stu-id="2a081-129">A **transparent outline icon** measuring 32 x 32 pixels.</span></span>
- <span data-ttu-id="2a081-130">Eine **manifest.json-Datei,** die die Attribute Ihrer App angibt.</span><span class="sxs-lookup"><span data-stu-id="2a081-130">A **manifest.json** file that specifies the attributes of your app.</span></span>

<span data-ttu-id="2a081-131">Diese Dateien müssen in einem App-Paket gezippt werden, damit sie zum Hochladen Ihrer Registerkarte in das Teams.</span><span class="sxs-lookup"><span data-stu-id="2a081-131">These files need to be zipped in an app package for use in uploading your tab to Teams.</span></span> <span data-ttu-id="2a081-132">Wenn ein Benutzer ihre Registerkarte hinzufügen oder aktualisieren möchte, wird Microsoft Teams in Ihr Manifest geladen, in einen IFrame eingebettet und auf Ihrer Registerkarte `configurationUrl` gerendert.</span><span class="sxs-lookup"><span data-stu-id="2a081-132">When a user chooses to add or update your tab, Microsoft Teams will load the `configurationUrl` specified in your manifest, embed it in an IFrame, and render it in your tab.</span></span>

### <a name="csproj"></a><span data-ttu-id="2a081-133">.csproj</span><span class="sxs-lookup"><span data-stu-id="2a081-133">.csproj</span></span>

<span data-ttu-id="2a081-134">Klicken Sie Visual Studio Projektmappen-Explorer mit der rechten Maustaste auf das Projekt, und wählen Sie **Bearbeiten Project Datei aus.**</span><span class="sxs-lookup"><span data-stu-id="2a081-134">In the Visual Studio Solution Explorer window right-click on the project and select **Edit Project File**.</span></span> <span data-ttu-id="2a081-135">Unten in der Datei wird der Code angezeigt, mit dem Ihr ZIP-Ordner erstellt und aktualisiert wird, wenn die Anwendung erstellt:</span><span class="sxs-lookup"><span data-stu-id="2a081-135">At the bottom of the file you'll see the code that creates and updates your zip folder when the application builds:</span></span>

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

[!INCLUDE [dotnet-ngrok-intro](~/includes/tabs/dotnet-ngrok-intro.md)]

- <span data-ttu-id="2a081-136">Öffnen Sie eine Eingabeaufforderung im Stammverzeichnis Ihres Projektverzeichnisses, und führen Sie den folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="2a081-136">Open a command prompt in the root of your project directory and run the following command:</span></span>

    ```bash
    ngrok http https://localhost:44355 -host-header="localhost:44355"
    ```

- <span data-ttu-id="2a081-137">Ngrok lauscht Anforderungen aus dem Internet und führt sie an Ihre Anwendung weiter, wenn sie an Port 44355 ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="2a081-137">Ngrok will listen to requests from the internet and will route them to your application when it is running on port 44355.</span></span> <span data-ttu-id="2a081-138">Es sollte so `https://y8rCgT2b.ngrok.io/` aussehen, *dass y8rCgT2b* durch Ihre ngrok-alphanumerische HTTPS-URL ersetzt wird.</span><span class="sxs-lookup"><span data-stu-id="2a081-138">It should resemble `https://y8rCgT2b.ngrok.io/` where *y8rCgT2b* is replaced by your ngrok alpha-numeric HTTPS URL.</span></span>

- <span data-ttu-id="2a081-139">Achten Sie darauf, dass die Eingabeaufforderung mit ngrok ausgeführt wird, und notieren Sie sich die URL – Sie benötigen sie später.</span><span class="sxs-lookup"><span data-stu-id="2a081-139">Be sure to keep the command prompt with ngrok running and to make note of the URL — you'll need it later.</span></span>

## <a name="update-your-application"></a><span data-ttu-id="2a081-140">Aktualisieren Ihrer Anwendung</span><span class="sxs-lookup"><span data-stu-id="2a081-140">Update your application</span></span>

<span data-ttu-id="2a081-141">In *Tab.cshtml* stellt die Anwendung dem Benutzer zwei Optionsschaltflächen zum Anzeigen der Registerkarte mit einem roten oder einem grauen Symbol zur Auswahl.</span><span class="sxs-lookup"><span data-stu-id="2a081-141">Within *Tab.cshtml* the application presents the user with two option buttons for displaying the tab with either a red or gray icon.</span></span> <span data-ttu-id="2a081-142">Wenn Sie die  Schaltfläche **Grau auswählen** oder Rot auswählen aktivieren, wird bzw. wird die Schaltfläche Speichern auf der `saveGray()` `saveRed()` `settings.setValidityState(true)` Konfigurationsseite aktiviert. </span><span class="sxs-lookup"><span data-stu-id="2a081-142">Choosing the **Select Gray** or **Select Red** button fires `saveGray()` or `saveRed()`, respectively, sets `settings.setValidityState(true)`, and enables the **Save** button on the configuration page.</span></span> <span data-ttu-id="2a081-143">Dieser Code Teams, dass Sie die Konfigurationsanforderungen erfüllt haben und die Installation fortgesetzt werden kann.</span><span class="sxs-lookup"><span data-stu-id="2a081-143">This code lets Teams know that you have satisfied the configuration requirements and the installation can proceed.</span></span> <span data-ttu-id="2a081-144">Beim Speichern werden die Parameter `settings.setSettings` von festgelegt.</span><span class="sxs-lookup"><span data-stu-id="2a081-144">On save, the parameters of `settings.setSettings` are set.</span></span> <span data-ttu-id="2a081-145">Schließlich wird `saveEvent.notifySuccess()` aufgerufen, um anzugeben, dass die Inhalts-URL erfolgreich aufgelöst wurde.</span><span class="sxs-lookup"><span data-stu-id="2a081-145">Finally, `saveEvent.notifySuccess()` is called to indicate that the content URL has successfully resolved.</span></span>

[!INCLUDE [dotnet-update-app](~/includes/tabs/dotnet-update-chan-grp-app.md)]

## <a name="next-step"></a><span data-ttu-id="2a081-146">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="2a081-146">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2a081-147">Erstellen einer benutzerdefinierten Kanal- und Gruppenregisterkarte mit ASP.NETCore MVC</span><span class="sxs-lookup"><span data-stu-id="2a081-147">Create a Custom Channel and Group Tab with ASP.NETCore MVC</span></span>](~/tabs/quickstarts/create-channel-group-tab-dotnet-core-mvc.md)
