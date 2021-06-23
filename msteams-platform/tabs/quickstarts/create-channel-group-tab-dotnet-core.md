---
title: Erstellen einer Kanal- und Gruppenregisterkarte mit ASP.NET Core
author: surbhigupta
description: Eine Schnellstartanleitung zum Erstellen einer benutzerdefinierten Kanal- und Gruppenregisterkarte mit ASP.NET Core.
localization_priority: Normal
ms.topic: quickstart
ms.author: lajanuar
ms.openlocfilehash: 2f7906f1fb9874503cecabdeb607251daf863e97
ms.sourcegitcommit: 623d81eb079d1842813265746a5fe0fe6311b196
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/22/2021
ms.locfileid: "53069117"
---
# <a name="create-a-custom-channel-and-group-tab-with-aspnetcore"></a><span data-ttu-id="21275-103">Erstellen eines benutzerdefinierten Kanals und einer Gruppenregisterkarte mit ASP.NETCore</span><span class="sxs-lookup"><span data-stu-id="21275-103">Create a Custom Channel and Group Tab with ASP.NETCore</span></span>

<span data-ttu-id="21275-104">In dieser Schnellstartanleitung werden wir schrittweise durch das Erstellen einer benutzerdefinierten Kanal-/Gruppenregisterkarte mit C# und ASP.Net Core Razor-Seite geführt.</span><span class="sxs-lookup"><span data-stu-id="21275-104">In this quickstart we'll walk-through creating a custom channel/group tab with C# and ASP.Net Core Razor page.</span></span> <span data-ttu-id="21275-105">Wir verwenden App Studio auch [für Microsoft Teams,](~/concepts/build-and-test/app-studio-overview.md) um Ihr App-Manifest fertig zu stellen und Ihre Registerkarte für Teams bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="21275-105">We'll also use [App Studio for Microsoft Teams](~/concepts/build-and-test/app-studio-overview.md) to finalize your app manifest and deploy your tab to Teams.</span></span>

[!INCLUDE [dotnet-core-prereq](~/includes/tabs/dotnet-core-prereq.md)]

## <a name="get-the-source-code"></a><span data-ttu-id="21275-106">Abrufen des Quellcodes</span><span class="sxs-lookup"><span data-stu-id="21275-106">Get the source code</span></span>

<span data-ttu-id="21275-107">Öffnen Sie eine Eingabeaufforderung, und erstellen Sie ein neues Verzeichnis für Ihr Registerkartenprojekt.</span><span class="sxs-lookup"><span data-stu-id="21275-107">Open a command prompt and create a new directory for your tab project.</span></span> <span data-ttu-id="21275-108">Wir haben ein einfaches Projekt bereitgestellt, um Ihnen den Einstieg zu erleichtern.</span><span class="sxs-lookup"><span data-stu-id="21275-108">We have provided a simple project to get you started.</span></span> <span data-ttu-id="21275-109">Um den Quellcode abzurufen, können Sie den ZIP-Ordner herunterladen und die Dateien extrahieren oder das Beispiel-Repository in Ihr neues Verzeichnis klonen:</span><span class="sxs-lookup"><span data-stu-id="21275-109">To retrieve the source code you can download the zip folder and extract the files or clone the sample repository into your new directory:</span></span>

```bash
git clone https://github.com/OfficeDev/microsoft-teams-sample-tabs.git
```

<span data-ttu-id="21275-110">Sobald Sie den Quellcode haben, öffnen Sie Visual Studio, und wählen Sie **Projekt oder Projektmappe öffnen** aus.</span><span class="sxs-lookup"><span data-stu-id="21275-110">Once you have the source code, open Visual Studio and select **Open a project or solution**.</span></span> <span data-ttu-id="21275-111">Navigieren Sie zum Registerkartenanwendungsverzeichnis, und öffnen **Sie "ChannelGroupTab.sln".**</span><span class="sxs-lookup"><span data-stu-id="21275-111">Navigate to the tab application directory and open **ChannelGroupTab.sln**.</span></span>

<span data-ttu-id="21275-112">Drücken Sie **F5,** oder wählen Sie im Menü **"Debuggen"** die Option **"Debuggen starten"** aus, um die Anwendung zu erstellen und auszuführen.</span><span class="sxs-lookup"><span data-stu-id="21275-112">To build and run your application press **F5** or choose **Start Debugging** from the **Debug** menu.</span></span> <span data-ttu-id="21275-113">Navigieren Sie in einem Browser zu den folgenden URLs, und überprüfen Sie, ob die Anwendung ordnungsgemäß geladen wurde:</span><span class="sxs-lookup"><span data-stu-id="21275-113">In a browser navigate to the URLs below and verify the application loaded properly:</span></span>

- `http://localhost:44355`
- `http://localhost:44355/privacy`
- `http://localhost:44355/tou`

## <a name="review-the-source-code"></a><span data-ttu-id="21275-114">Überprüfen des Quellcodes</span><span class="sxs-lookup"><span data-stu-id="21275-114">Review the source code</span></span>

### <a name="startupcs"></a><span data-ttu-id="21275-115">Startup.cs</span><span class="sxs-lookup"><span data-stu-id="21275-115">Startup.cs</span></span>

<span data-ttu-id="21275-116">Dieses Projekt wurde aus einer leeren Vorlage für ASP.NET Core 2.2-Webanwendung erstellt, wobei das Kontrollkästchen *"Erweitert – Für HTTPS konfigurieren"* beim Setup aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="21275-116">This project was created from an ASP.NET Core 2.2 Web Application empty template with the *Advanced - Configure for HTTPS* check box selected at setup.</span></span> <span data-ttu-id="21275-117">Die MVC-Dienste werden durch die Methode des Abhängigkeitsinjektionsframeworks `ConfigureServices()` registriert.</span><span class="sxs-lookup"><span data-stu-id="21275-117">The MVC services are registered by the dependency injection framework's `ConfigureServices()` method.</span></span> <span data-ttu-id="21275-118">Darüber hinaus ermöglicht die leere Vorlage nicht standardmäßig die Bereitstellung statischer Inhalte, sodass die Middleware für statische Dateien der Methode hinzugefügt `Configure()` wird:</span><span class="sxs-lookup"><span data-stu-id="21275-118">Additionally, the empty template doesn't enable serving static content by default, so the static files middleware is added to the `Configure()` method:</span></span>

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

### <a name="wwwroot-folder"></a><span data-ttu-id="21275-119">Wwwroot-Ordner</span><span class="sxs-lookup"><span data-stu-id="21275-119">wwwroot folder</span></span>

<span data-ttu-id="21275-120">In ASP.NET Core sucht die Anwendung im Webstammordner nach statischen Dateien.</span><span class="sxs-lookup"><span data-stu-id="21275-120">In ASP.NET Core, the web root folder is where the application looks for static files.</span></span>

### <a name="indexcshtml"></a><span data-ttu-id="21275-121">Index.cshtml</span><span class="sxs-lookup"><span data-stu-id="21275-121">Index.cshtml</span></span>

<span data-ttu-id="21275-122">ASP.NET Core behandelt Dateien mit dem Namen *Index* als Standard-/Startseite für die Website.</span><span class="sxs-lookup"><span data-stu-id="21275-122">ASP.NET Core treats files called *Index* as the default/home page for the site.</span></span> <span data-ttu-id="21275-123">Wenn Ihre Browser-URL auf den Stamm der Website zeigt, wird **Index.cshtml** als Startseite für Ihre Anwendung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="21275-123">When your browser URL points to the root of the site, **Index.cshtml** will be displayed as the home page for your application.</span></span>

### <a name="tabcs"></a><span data-ttu-id="21275-124">Tab.cs</span><span class="sxs-lookup"><span data-stu-id="21275-124">Tab.cs</span></span>

<span data-ttu-id="21275-125">Diese C#-Datei enthält eine Methode, die während der Konfiguration von **Tab.cshtml** aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="21275-125">This C# file contains a method that will be called from **Tab.cshtml** during configuration.</span></span>

### <a name="appmanifest-folder"></a><span data-ttu-id="21275-126">AppManifest-Ordner</span><span class="sxs-lookup"><span data-stu-id="21275-126">AppManifest folder</span></span>

<span data-ttu-id="21275-127">Dieser Ordner enthält die folgenden erforderlichen App-Paketdateien:</span><span class="sxs-lookup"><span data-stu-id="21275-127">This folder contains the following required app package files:</span></span>

- <span data-ttu-id="21275-128">Ein **Vollfarbsymbol** mit einer Auflösung von 192 x 192 Pixeln.</span><span class="sxs-lookup"><span data-stu-id="21275-128">A **full color icon** measuring 192 x 192 pixels.</span></span>
- <span data-ttu-id="21275-129">Ein **transparentes Gliederungssymbol** mit einer Auflösung von 32 x 32 Pixeln.</span><span class="sxs-lookup"><span data-stu-id="21275-129">A **transparent outline icon** measuring 32 x 32 pixels.</span></span>
- <span data-ttu-id="21275-130">Ein **manifest.jsfür** die Datei, die die Attribute Ihrer App angibt.</span><span class="sxs-lookup"><span data-stu-id="21275-130">A **manifest.json** file that specifies the attributes of your app.</span></span>

<span data-ttu-id="21275-131">Diese Dateien müssen in einem App-Paket gezippt werden, um Ihre Registerkarte auf Teams hochzuladen.</span><span class="sxs-lookup"><span data-stu-id="21275-131">These files need to be zipped in an app package for use in uploading your tab to Teams.</span></span> <span data-ttu-id="21275-132">Wenn ein Benutzer die Registerkarte hinzufügt oder aktualisiert, lädt Microsoft Teams das `configurationUrl` angegebene Element in Ihrem Manifest, einbettet es in einen IFrame und rendert es auf der Registerkarte.</span><span class="sxs-lookup"><span data-stu-id="21275-132">When a user chooses to add or update your tab, Microsoft Teams will load the `configurationUrl` specified in your manifest, embed it in an IFrame, and render it in your tab.</span></span>

### <a name="csproj"></a><span data-ttu-id="21275-133">CSPROJ</span><span class="sxs-lookup"><span data-stu-id="21275-133">.csproj</span></span>

<span data-ttu-id="21275-134">Klicken Sie im Visual Studio Projektmappen-Explorer-Fenster mit der rechten Maustaste auf das Projekt, und wählen Sie **Bearbeiten Project Datei** aus.</span><span class="sxs-lookup"><span data-stu-id="21275-134">In the Visual Studio Solution Explorer window right-click on the project and select **Edit Project File**.</span></span> <span data-ttu-id="21275-135">Am Ende der Datei sehen Sie den Code, der Ihren ZIP-Ordner erstellt und aktualisiert, wenn die Anwendung erstellt wird:</span><span class="sxs-lookup"><span data-stu-id="21275-135">At the bottom of the file you'll see the code that creates and updates your zip folder when the application builds:</span></span>

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

- <span data-ttu-id="21275-136">Öffnen Sie eine Eingabeaufforderung im Stammverzeichnis des Projekts, und führen Sie den folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="21275-136">Open a command prompt in the root of your project directory and run the following command:</span></span>

    ```bash
    ngrok http https://localhost:44355 -host-header="localhost:44355"
    ```

- <span data-ttu-id="21275-137">Ngrok lauscht auf Anforderungen aus dem Internet und leitet sie an Ihre Anwendung weiter, wenn sie auf Port 44355 ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="21275-137">Ngrok will listen to requests from the internet and will route them to your application when it is running on port 44355.</span></span> <span data-ttu-id="21275-138">Es sollte etwa so `https://y8rCgT2b.ngrok.io/` aussehen, wo *y8rCgT2b* durch Ihre alphangrok-numerische HTTPS-URL ersetzt wird.</span><span class="sxs-lookup"><span data-stu-id="21275-138">It should resemble `https://y8rCgT2b.ngrok.io/` where *y8rCgT2b* is replaced by your ngrok alpha-numeric HTTPS URL.</span></span>

- <span data-ttu-id="21275-139">Achten Sie darauf, dass die Eingabeaufforderung mit ngrok ausgeführt wird, und notieren Sie sich die URL . Sie benötigen sie später.</span><span class="sxs-lookup"><span data-stu-id="21275-139">Be sure to keep the command prompt with ngrok running and to make note of the URL — you'll need it later.</span></span>

## <a name="update-your-application"></a><span data-ttu-id="21275-140">Aktualisieren Der Anwendung</span><span class="sxs-lookup"><span data-stu-id="21275-140">Update your application</span></span>

<span data-ttu-id="21275-141">Innerhalb von *Tab.cshtml* zeigt die Anwendung dem Benutzer zwei Optionsschaltflächen zum Anzeigen der Registerkarte mit einem roten oder grauen Symbol an.</span><span class="sxs-lookup"><span data-stu-id="21275-141">Within *Tab.cshtml* the application presents the user with two option buttons for displaying the tab with either a red or gray icon.</span></span> <span data-ttu-id="21275-142">Wenn Sie die Schaltfläche **"Grau auswählen"** oder **"Rot auswählen"** auswählen, wird diese ausgelöst `saveGray()` `saveRed()` bzw. `settings.setValidityState(true)` festgelegt, und die Schaltfläche **"Speichern"** wird auf der Konfigurationsseite aktiviert.</span><span class="sxs-lookup"><span data-stu-id="21275-142">Choosing the **Select Gray** or **Select Red** button fires `saveGray()` or `saveRed()`, respectively, sets `settings.setValidityState(true)`, and enables the **Save** button on the configuration page.</span></span> <span data-ttu-id="21275-143">Dieser Code teilt Teams mit, dass sie die Konfigurationsanforderungen erfüllt haben und die Installation fortgesetzt werden kann.</span><span class="sxs-lookup"><span data-stu-id="21275-143">This code lets Teams know that you have satisfied the configuration requirements and the installation can proceed.</span></span> <span data-ttu-id="21275-144">Beim Speichern werden die Parameter `settings.setSettings` von festgelegt.</span><span class="sxs-lookup"><span data-stu-id="21275-144">On save, the parameters of `settings.setSettings` are set.</span></span> <span data-ttu-id="21275-145">Schließlich `saveEvent.notifySuccess()` wird aufgerufen, um anzugeben, dass die Inhalts-URL erfolgreich aufgelöst wurde.</span><span class="sxs-lookup"><span data-stu-id="21275-145">Finally, `saveEvent.notifySuccess()` is called to indicate that the content URL has successfully resolved.</span></span>

[!INCLUDE [dotnet-update-app](~/includes/tabs/dotnet-update-chan-grp-app.md)]

## <a name="next-step"></a><span data-ttu-id="21275-146">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="21275-146">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="21275-147">Erstellen eines benutzerdefinierten Kanals und einer Gruppenregisterkarte mit ASP.NETCore MVC</span><span class="sxs-lookup"><span data-stu-id="21275-147">Create a Custom Channel and Group Tab with ASP.NETCore MVC</span></span>](~/tabs/quickstarts/create-channel-group-tab-dotnet-core-mvc.md)
