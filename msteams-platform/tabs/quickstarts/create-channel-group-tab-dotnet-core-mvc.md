---
title: Erstellen einer Kanal- und Gruppenregisterkarte mit ASP.NET Core MVC
author: surbhigupta
description: Eine Schnellstartanleitung zum Erstellen einer benutzerdefinierten Kanal- und Gruppenregisterkarte mit ASP.NET Core MVC
localization_priority: Normal
ms.topic: quickstart
ms.author: lajanuar
ms.openlocfilehash: b265e413d1f1d1239eda8285ea7066ad01750bba
ms.sourcegitcommit: 623d81eb079d1842813265746a5fe0fe6311b196
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/22/2021
ms.locfileid: "53069126"
---
# <a name="create-a-custom-channel-and-group-tab-with-aspnet-core-mvc"></a><span data-ttu-id="5f8cf-103">Erstellen eines benutzerdefinierten Kanals und einer Gruppenregisterkarte mit ASP.NET Core MVC</span><span class="sxs-lookup"><span data-stu-id="5f8cf-103">Create a Custom Channel and Group Tab with ASP.NET Core MVC</span></span>

<span data-ttu-id="5f8cf-104">In diesem Schnellstart werden wir schrittweise durch das Erstellen einer benutzerdefinierten Kanal-/Gruppenregisterkarte mit C# und ASP.Net Core MVC geführt.</span><span class="sxs-lookup"><span data-stu-id="5f8cf-104">In this quickstart we'll walk-through creating a custom channel/group tab with C# and ASP.Net Core MVC.</span></span> <span data-ttu-id="5f8cf-105">Wir verwenden App Studio auch [für Microsoft Teams,](~/concepts/build-and-test/app-studio-overview.md) um Ihr App-Manifest fertig zu stellen und Ihre Registerkarte für Teams bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="5f8cf-105">We'll also use [App Studio for Microsoft Teams](~/concepts/build-and-test/app-studio-overview.md) to finalize your app manifest and deploy your tab to Teams.</span></span>

[!INCLUDE [dotnet-core-prereq](~/includes/tabs/dotnet-core-prereq.md)]

## <a name="get-the-source-code"></a><span data-ttu-id="5f8cf-106">Abrufen des Quellcodes</span><span class="sxs-lookup"><span data-stu-id="5f8cf-106">Get the source code</span></span>

<span data-ttu-id="5f8cf-107">Öffnen Sie eine Eingabeaufforderung, und erstellen Sie ein neues Verzeichnis für Ihr Registerkartenprojekt.</span><span class="sxs-lookup"><span data-stu-id="5f8cf-107">Open a command prompt and create a new directory for your tab project.</span></span> <span data-ttu-id="5f8cf-108">Wir haben ein einfaches [Kanalgruppen-Registerkartenprojekt](https://github.com/OfficeDev/microsoft-teams-sample-tabs/tree/master/ChannelGroupTabMVC) bereitgestellt, um Ihnen den Einstieg zu erleichtern.</span><span class="sxs-lookup"><span data-stu-id="5f8cf-108">We have provided a simple [Channel Group Tab](https://github.com/OfficeDev/microsoft-teams-sample-tabs/tree/master/ChannelGroupTabMVC) project to get you started.</span></span> <span data-ttu-id="5f8cf-109">Um den Quellcode abzurufen, können Sie den ZIP-Ordner herunterladen und die Dateien extrahieren oder das Beispiel-Repository in Ihr neues Verzeichnis klonen:</span><span class="sxs-lookup"><span data-stu-id="5f8cf-109">To retrieve the source code you can download the zip folder and extract the files or clone the sample repository into your new directory:</span></span>

```bash
git clone https://github.com/OfficeDev/microsoft-teams-sample-tabs.git
```

<span data-ttu-id="5f8cf-110">Sobald Sie den Quellcode haben, öffnen Sie Visual Studio, und wählen Sie **Projekt oder Projektmappe öffnen** aus.</span><span class="sxs-lookup"><span data-stu-id="5f8cf-110">Once you have the source code, open Visual Studio and select **Open a project or solution**.</span></span> <span data-ttu-id="5f8cf-111">Navigieren Sie zum Registerkartenanwendungsverzeichnis, und öffnen Sie **ChannelGroupTabMVC.sln**.</span><span class="sxs-lookup"><span data-stu-id="5f8cf-111">Navigate to the tab application directory and open **ChannelGroupTabMVC.sln**.</span></span>

<span data-ttu-id="5f8cf-112">Drücken Sie **F5,** oder wählen Sie im Menü **"Debuggen"** die Option **"Debuggen starten"** aus, um die Anwendung zu erstellen und auszuführen.</span><span class="sxs-lookup"><span data-stu-id="5f8cf-112">To build and run your application press **F5** or choose **Start Debugging** from the **Debug** menu.</span></span> <span data-ttu-id="5f8cf-113">Navigieren Sie in einem Browser zu den folgenden URLs, und stellen Sie sicher, dass die Anwendung ordnungsgemäß geladen wurde:</span><span class="sxs-lookup"><span data-stu-id="5f8cf-113">In a browser, navigate to the URLs below and verify that the application loaded properly:</span></span>

- `http://localhost:44360`
- `http://localhost:44360/privacy`
- `http://localhost:44360/tou`

## <a name="review-the-source-code"></a><span data-ttu-id="5f8cf-114">Überprüfen des Quellcodes</span><span class="sxs-lookup"><span data-stu-id="5f8cf-114">Review the source code</span></span>

### <a name="startupcs"></a><span data-ttu-id="5f8cf-115">Startup.cs</span><span class="sxs-lookup"><span data-stu-id="5f8cf-115">Startup.cs</span></span>

<span data-ttu-id="5f8cf-116">Dieses Projekt wurde aus einer leeren Vorlage für ASP.NET Core 2.2-Webanwendung erstellt, wobei das Kontrollkästchen *"Erweitert – Für HTTPS konfigurieren"* beim Setup aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="5f8cf-116">This project was created from an ASP.NET Core 2.2 Web Application empty template with the *Advanced - Configure for HTTPS* check box selected at setup.</span></span> <span data-ttu-id="5f8cf-117">Die MVC-Dienste werden durch die Methode des Abhängigkeitsinjektionsframeworks `ConfigureServices()` registriert.</span><span class="sxs-lookup"><span data-stu-id="5f8cf-117">The MVC services are registered by the dependency injection framework's `ConfigureServices()` method.</span></span> <span data-ttu-id="5f8cf-118">Darüber hinaus ermöglicht die leere Vorlage nicht standardmäßig die Bereitstellung statischer Inhalte, sodass die Middleware für statische Dateien der Methode hinzugefügt `Configure()` wird:</span><span class="sxs-lookup"><span data-stu-id="5f8cf-118">Additionally, the empty template doesn't enable serving static content by default, so the static files middleware is added to the `Configure()` method:</span></span>

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

### <a name="wwwroot-folder"></a><span data-ttu-id="5f8cf-119">Wwwroot-Ordner</span><span class="sxs-lookup"><span data-stu-id="5f8cf-119">wwwroot folder</span></span>

<span data-ttu-id="5f8cf-120">In ASP.NET Core sucht die Anwendung im Webstammordner nach statischen Dateien.</span><span class="sxs-lookup"><span data-stu-id="5f8cf-120">In ASP.NET Core, the web root folder is where the application looks for static files.</span></span>

### <a name="appmanifest-folder"></a><span data-ttu-id="5f8cf-121">AppManifest-Ordner</span><span class="sxs-lookup"><span data-stu-id="5f8cf-121">AppManifest folder</span></span>

<span data-ttu-id="5f8cf-122">Dieser Ordner enthält die folgenden erforderlichen App-Paketdateien:</span><span class="sxs-lookup"><span data-stu-id="5f8cf-122">This folder contains the following required app package files:</span></span>

- <span data-ttu-id="5f8cf-123">Ein **Vollfarbsymbol** mit einer Auflösung von 192 x 192 Pixeln.</span><span class="sxs-lookup"><span data-stu-id="5f8cf-123">A **full color icon** measuring 192 x 192 pixels.</span></span>
- <span data-ttu-id="5f8cf-124">Ein **transparentes Gliederungssymbol** mit einer Auflösung von 32 x 32 Pixeln.</span><span class="sxs-lookup"><span data-stu-id="5f8cf-124">A **transparent outline icon** measuring 32 x 32 pixels.</span></span>
- <span data-ttu-id="5f8cf-125">Ein **manifest.jsfür** die Datei, die die Attribute Ihrer App angibt.</span><span class="sxs-lookup"><span data-stu-id="5f8cf-125">A **manifest.json** file that specifies the attributes of your app.</span></span>

<span data-ttu-id="5f8cf-126">Diese Dateien müssen in einem App-Paket gezippt werden, um Ihre Registerkarte in Teams hochzuladen.</span><span class="sxs-lookup"><span data-stu-id="5f8cf-126">These files need to be zipped in an app package for use in uploading your tab to Teams.</span></span>

### <a name="csproj"></a><span data-ttu-id="5f8cf-127">CSPROJ</span><span class="sxs-lookup"><span data-stu-id="5f8cf-127">.csproj</span></span>

<span data-ttu-id="5f8cf-128">Klicken Sie im Fenster Visual Studio Projektmappen-Explorer mit der rechten Maustaste auf das Projekt, und wählen Sie **"Bearbeiten Project Datei"** aus.</span><span class="sxs-lookup"><span data-stu-id="5f8cf-128">In the Visual Studio Solution Explorer window right-click on the project and select **Edit Project File**.</span></span> <span data-ttu-id="5f8cf-129">Am Ende der Datei sehen Sie den Code, der Ihren ZIP-Ordner erstellt und aktualisiert, wenn die Anwendung erstellt wird:</span><span class="sxs-lookup"><span data-stu-id="5f8cf-129">At the bottom of the file you'll see the code that creates and updates your zip folder when the application builds:</span></span>

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

### <a name="models"></a><span data-ttu-id="5f8cf-130">Modelle</span><span class="sxs-lookup"><span data-stu-id="5f8cf-130">Models</span></span>

<span data-ttu-id="5f8cf-131">*ChannelGroup.cs* stellt ein Message-Objekt und Methoden vor, die während der Konfiguration von den Controllern aufgerufen werden.</span><span class="sxs-lookup"><span data-stu-id="5f8cf-131">*ChannelGroup.cs* presents a Message object and methods that will be called from the Controllers during configuration.</span></span>

### <a name="views"></a><span data-ttu-id="5f8cf-132">Ansichten</span><span class="sxs-lookup"><span data-stu-id="5f8cf-132">Views</span></span>

#### <a name="home"></a><span data-ttu-id="5f8cf-133">Start</span><span class="sxs-lookup"><span data-stu-id="5f8cf-133">Home</span></span>

<span data-ttu-id="5f8cf-134">ASP.NET Core behandelt Dateien mit dem Namen *Index* als Standard-/Startseite für die Website.</span><span class="sxs-lookup"><span data-stu-id="5f8cf-134">ASP.NET Core treats files called *Index* as the default/home page for the site.</span></span> <span data-ttu-id="5f8cf-135">Wenn Ihre Browser-URL auf den Stamm der Website zeigt, wird **Index.cshtml** als Startseite für Ihre Anwendung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="5f8cf-135">When your browser URL points to the root of the site, **Index.cshtml** will be displayed as the home page for your application.</span></span>

#### <a name="shared"></a><span data-ttu-id="5f8cf-136">Shared</span><span class="sxs-lookup"><span data-stu-id="5f8cf-136">Shared</span></span>

<span data-ttu-id="5f8cf-137">Das Partielle Ansichtsmarkup *_Layout.cshtml* enthält die allgemeine Seitenstruktur der Anwendung und freigegebene visuelle Elemente.</span><span class="sxs-lookup"><span data-stu-id="5f8cf-137">The partial view markup *_Layout.cshtml* contains the application's overall page structure and shared visual elements.</span></span> <span data-ttu-id="5f8cf-138">Außerdem wird auf die Teams Bibliothek verwiesen.</span><span class="sxs-lookup"><span data-stu-id="5f8cf-138">It will also reference the Teams Library.</span></span>

### <a name="controllers"></a><span data-ttu-id="5f8cf-139">Controller</span><span class="sxs-lookup"><span data-stu-id="5f8cf-139">Controllers</span></span>

<span data-ttu-id="5f8cf-140">Die Controller verwenden die ViewBag-Eigenschaft, um Werte dynamisch in die Ansichten zu übertragen.</span><span class="sxs-lookup"><span data-stu-id="5f8cf-140">The controllers use the ViewBag property to transfer values dynamically to the Views.</span></span>

[!INCLUDE [dotnet-ngrok-intro](~/includes/tabs/dotnet-ngrok-intro.md)]

- <span data-ttu-id="5f8cf-141">Öffnen Sie eine Eingabeaufforderung im Stammverzeichnis des Projekts, und führen Sie den folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="5f8cf-141">Open a command prompt in the root of your project directory and run the following command:</span></span>

    ```bash
    ngrok http https://localhost:443560 -host-header="localhost:44360"
    ```

- <span data-ttu-id="5f8cf-142">Ngrok lauscht auf Anforderungen aus dem Internet und leitet sie an Ihre Anwendung weiter, wenn sie auf Port 44355 ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="5f8cf-142">Ngrok will listen to requests from the internet and will route them to your application when it is running on port 44355.</span></span>  <span data-ttu-id="5f8cf-143">Es sollte etwa so `https://y8rCgT2b.ngrok.io/` aussehen, wo *y8rCgT2b* durch Ihre alphangrok-numerische HTTPS-URL ersetzt wird.</span><span class="sxs-lookup"><span data-stu-id="5f8cf-143">It should resemble `https://y8rCgT2b.ngrok.io/` where *y8rCgT2b* is replaced by your ngrok alpha-numeric HTTPS URL.</span></span>

- <span data-ttu-id="5f8cf-144">Achten Sie darauf, dass die Eingabeaufforderung mit ngrok ausgeführt wird, und notieren Sie sich die URL . Sie benötigen sie später.</span><span class="sxs-lookup"><span data-stu-id="5f8cf-144">Be sure to keep the command prompt with ngrok running and to make note of the URL — you'll need it later.</span></span>

## <a name="update-your-application"></a><span data-ttu-id="5f8cf-145">Aktualisieren Der Anwendung</span><span class="sxs-lookup"><span data-stu-id="5f8cf-145">Update your application</span></span>

<span data-ttu-id="5f8cf-146">Innerhalb von **Tab.cshtml** zeigt die Anwendung dem Benutzer zwei Optionsschaltflächen zum Anzeigen der Registerkarte mit einem roten oder grauen Symbol an.</span><span class="sxs-lookup"><span data-stu-id="5f8cf-146">Within **Tab.cshtml** the application presents the user with two option buttons for displaying the tab with either a red or gray icon.</span></span> <span data-ttu-id="5f8cf-147">Wenn Sie die Schaltfläche **"Grau auswählen"** oder **"Rot auswählen"** auswählen, wird diese ausgelöst `saveGray()` `saveRed()` bzw. `settings.setValidityState(true)` festgelegt, und die Schaltfläche **"Speichern"** wird auf der Konfigurationsseite aktiviert.</span><span class="sxs-lookup"><span data-stu-id="5f8cf-147">Choosing the **Select Gray** or **Select Red** button fires `saveGray()` or `saveRed()`, respectively, sets `settings.setValidityState(true)`, and enables the **Save** button on the configuration page.</span></span> <span data-ttu-id="5f8cf-148">Dieser Code teilt Teams mit, dass sie die Konfigurationsanforderungen erfüllt haben und die Installation fortgesetzt werden kann.</span><span class="sxs-lookup"><span data-stu-id="5f8cf-148">This code lets Teams know that you have satisfied the configuration requirements and the installation can proceed.</span></span> <span data-ttu-id="5f8cf-149">Beim Speichern werden die Parameter `settings.setSettings` von festgelegt.</span><span class="sxs-lookup"><span data-stu-id="5f8cf-149">On save, the parameters of `settings.setSettings` are set.</span></span> <span data-ttu-id="5f8cf-150">Schließlich `saveEvent.notifySuccess()` wird aufgerufen, um anzugeben, dass die Inhalts-URL erfolgreich aufgelöst wurde.</span><span class="sxs-lookup"><span data-stu-id="5f8cf-150">Finally, `saveEvent.notifySuccess()` is called to indicate that the content URL has successfully resolved.</span></span>

[!INCLUDE [dotnet-update-app](~/includes/tabs/dotnet-update-chan-grp-app.md)]
