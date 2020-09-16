---
title: Erstellen einer Kanal-und Gruppenregisterkarte mit ASP.net-Kern
author: laujan
description: Eine Schnellstartanleitung zum Erstellen einer benutzerdefinierten Kanal-und Gruppenregisterkarte mit ASP.net Core.
ms.topic: quickstart
ms.author: lajanuar
ms.openlocfilehash: 6a21d40d4d474fd587b43760d818082b4ab2502d
ms.sourcegitcommit: e8dfcb167274e996395b77d65999991a18f2051a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/15/2020
ms.locfileid: "47818920"
---
# <a name="create-a-custom-channel-and-group-tab-with-aspnet-core"></a><span data-ttu-id="f6d5a-103">Erstellen einer benutzerdefinierten Kanal-und Gruppenregisterkarte mit ASP.net Core</span><span class="sxs-lookup"><span data-stu-id="f6d5a-103">Create a Custom Channel and Group Tab with ASP.NET Core</span></span>

<span data-ttu-id="f6d5a-104">In diesem Schnellstart werden wir durch das Erstellen einer benutzerdefinierten Kanal-Gruppe-Registerkarte mit C#-und ASP.net-Kern-Rasierer-Seite Schritt halten.</span><span class="sxs-lookup"><span data-stu-id="f6d5a-104">In this quickstart we'll walk-through creating a custom channel/group tab with C# and ASP.Net Core Razor page.</span></span> <span data-ttu-id="f6d5a-105">Wir verwenden auch [App Studio für Microsoft Teams](~/concepts/build-and-test/app-studio-overview.md) , um Ihr App-Manifest abzuschließen und die Registerkarte in Teams bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="f6d5a-105">We'll also use [App Studio for Microsoft Teams](~/concepts/build-and-test/app-studio-overview.md) to finalize your app manifest and deploy your tab to Teams.</span></span>

[!INCLUDE [dotnet-core-prereq](~/includes/tabs/dotnet-core-prereq.md)]

## <a name="get-the-source-code"></a><span data-ttu-id="f6d5a-106">Abrufen des Quellcodes</span><span class="sxs-lookup"><span data-stu-id="f6d5a-106">Get the source code</span></span>

<span data-ttu-id="f6d5a-107">Öffnen Sie eine Eingabeaufforderung, und erstellen Sie ein neues Verzeichnis für Ihr Tab-Projekt.</span><span class="sxs-lookup"><span data-stu-id="f6d5a-107">Open a command prompt and create a new directory for your tab project.</span></span> <span data-ttu-id="f6d5a-108">Wir haben ein einfaches Projekt zur Verfügung gestellt, damit Sie loslegen können.</span><span class="sxs-lookup"><span data-stu-id="f6d5a-108">We have provided a simple project to get you started.</span></span> <span data-ttu-id="f6d5a-109">Zum Abrufen des Quellcodes können Sie den ZIP-Ordner herunterladen und die Dateien extrahieren oder das Beispiel-Repository in Ihr neues Verzeichnis kopieren:</span><span class="sxs-lookup"><span data-stu-id="f6d5a-109">To retrieve the source code you can download the zip folder and extract the files or clone the sample repository into your new directory:</span></span>

```bash
git clone https://github.com/OfficeDev/microsoft-teams-sample-tabs.git
```

<span data-ttu-id="f6d5a-110">Nachdem Sie den Quellcode haben, öffnen Sie Visual Studio, und wählen Sie **Projekt oder Lösung öffnen**aus.</span><span class="sxs-lookup"><span data-stu-id="f6d5a-110">Once you have the source code, open Visual Studio and select **Open a project or solution**.</span></span> <span data-ttu-id="f6d5a-111">Navigieren Sie zum Anwendungsverzeichnis der Registerkarte, und öffnen Sie **ChannelGroupTab. sln**.</span><span class="sxs-lookup"><span data-stu-id="f6d5a-111">Navigate to the tab application directory and open **ChannelGroupTab.sln**.</span></span>

<span data-ttu-id="f6d5a-112">Drücken Sie zum Erstellen und Ausführen der Anwendung **F5** , oder wählen Sie im Menü **Debuggen** die Option **Debuggen starten** aus.</span><span class="sxs-lookup"><span data-stu-id="f6d5a-112">To build and run your application press **F5** or choose **Start Debugging** from the **Debug** menu.</span></span> <span data-ttu-id="f6d5a-113">Navigieren Sie in einem Browser zu den folgenden URLs, und überprüfen Sie, ob die Anwendung ordnungsgemäß geladen wurde:</span><span class="sxs-lookup"><span data-stu-id="f6d5a-113">In a browser navigate to the URLs below and verify the application loaded properly:</span></span>

- `http://localhost:44355`
- `http://localhost:44355/privacy`
- `http://localhost:44355/tou`

## <a name="review-the-source-code"></a><span data-ttu-id="f6d5a-114">Überprüfen des Quellcodes</span><span class="sxs-lookup"><span data-stu-id="f6d5a-114">Review the source code</span></span>

### <a name="startupcs"></a><span data-ttu-id="f6d5a-115">Startup.cs</span><span class="sxs-lookup"><span data-stu-id="f6d5a-115">Startup.cs</span></span>

<span data-ttu-id="f6d5a-116">Dieses Projekt wurde aus einer leeren Vorlage für ASP.net Core 2,2-Webanwendungen erstellt, wobei das Kontrollkästchen *Erweiterte Konfiguration für HTTPS* beim Setup aktiviert ist.</span><span class="sxs-lookup"><span data-stu-id="f6d5a-116">This project was created from an ASP.NET Core 2.2 Web Application empty template with the *Advanced - Configure for HTTPS* check box selected at setup.</span></span> <span data-ttu-id="f6d5a-117">Die MVC-Dienste werden von der Dependency Injection Framework- `ConfigureServices()` Methode registriert.</span><span class="sxs-lookup"><span data-stu-id="f6d5a-117">The MVC services are registered by the dependency injection framework's `ConfigureServices()` method.</span></span> <span data-ttu-id="f6d5a-118">Darüber hinaus wird die Bereitstellung statischer Inhalte nicht standardmäßig durch die leere Vorlage aktiviert, sodass der Methode die statische Datei Middleware hinzugefügt wird `Configure()` :</span><span class="sxs-lookup"><span data-stu-id="f6d5a-118">Additionally, the empty template doesn't enable serving static content by default, so the static files middleware is added to the `Configure()` method:</span></span>

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

### <a name="wwwroot-folder"></a><span data-ttu-id="f6d5a-119">WWWRoot-Ordner</span><span class="sxs-lookup"><span data-stu-id="f6d5a-119">wwwroot folder</span></span>

<span data-ttu-id="f6d5a-120">In ASP.net Core ist der Webstammordner, in dem die Anwendung nach statischen Dateien sucht.</span><span class="sxs-lookup"><span data-stu-id="f6d5a-120">In ASP.NET Core, the web root folder is where the application looks for static files.</span></span>

### <a name="indexcshtml"></a><span data-ttu-id="f6d5a-121">Index. cshtml</span><span class="sxs-lookup"><span data-stu-id="f6d5a-121">Index.cshtml</span></span>

<span data-ttu-id="f6d5a-122">ASP.net Core behandelt Dateien namens " *Index* " als Standard/Homepage für die Website.</span><span class="sxs-lookup"><span data-stu-id="f6d5a-122">ASP.NET Core treats files called *Index* as the default/home page for the site.</span></span> <span data-ttu-id="f6d5a-123">Wenn Ihre Browser-URL auf den Stamm der Website zeigt, wird **Index. cshtml** als Startseite für Ihre Anwendung angezeigt.</span><span class="sxs-lookup"><span data-stu-id="f6d5a-123">When your browser URL points to the root of the site, **Index.cshtml** will be displayed as the home page for your application.</span></span>

### <a name="tabcs"></a><span data-ttu-id="f6d5a-124">Tab.cs</span><span class="sxs-lookup"><span data-stu-id="f6d5a-124">Tab.cs</span></span>

<span data-ttu-id="f6d5a-125">Diese C#-Datei enthält eine Methode, die während der Konfiguration von **Tab. cshtml** aufgerufen wird.</span><span class="sxs-lookup"><span data-stu-id="f6d5a-125">This C# file contains a method that will be called from **Tab.cshtml** during configuration.</span></span>

### <a name="appmanifest-folder"></a><span data-ttu-id="f6d5a-126">AppManifest-Ordner</span><span class="sxs-lookup"><span data-stu-id="f6d5a-126">AppManifest folder</span></span>

<span data-ttu-id="f6d5a-127">Dieser Ordner enthält die folgenden erforderlichen App-Paketdateien:</span><span class="sxs-lookup"><span data-stu-id="f6d5a-127">This folder contains the following required app package files:</span></span>

- <span data-ttu-id="f6d5a-128">Ein **vollfarbiges Symbol** , das 192 x 192 Pixel misst.</span><span class="sxs-lookup"><span data-stu-id="f6d5a-128">A **full color icon** measuring 192 x 192 pixels.</span></span>
- <span data-ttu-id="f6d5a-129">Ein **transparentes Umrisssymbol** , das 32 x 32 Pixel misst.</span><span class="sxs-lookup"><span data-stu-id="f6d5a-129">A **transparent outline icon** measuring 32 x 32 pixels.</span></span>
- <span data-ttu-id="f6d5a-130">Ein **manifest.jsfür** die Datei, die die Attribute Ihrer APP angibt.</span><span class="sxs-lookup"><span data-stu-id="f6d5a-130">A **manifest.json** file that specifies the attributes of your app.</span></span>

<span data-ttu-id="f6d5a-131">Diese Dateien müssen in einem App-Paket gezippt werden, damit Sie Ihre Registerkarte in Microsoft Teams hochladen können.</span><span class="sxs-lookup"><span data-stu-id="f6d5a-131">These files need to be zipped in an app package for use in uploading your tab to Teams.</span></span> <span data-ttu-id="f6d5a-132">Wenn ein Benutzer das Hinzufügen oder Aktualisieren der Registerkarte vornimmt, lädt Microsoft Teams das `configurationUrl` angegebene in ihrem Manifest, bettet es in einen iframe ein und rendert es in der Registerkarte.</span><span class="sxs-lookup"><span data-stu-id="f6d5a-132">When a user chooses to add or update your tab, Microsoft Teams will load the `configurationUrl` specified in your manifest, embed it in an IFrame, and render it in your tab.</span></span>

### <a name="csproj"></a><span data-ttu-id="f6d5a-133">. csproj</span><span class="sxs-lookup"><span data-stu-id="f6d5a-133">.csproj</span></span>

<span data-ttu-id="f6d5a-134">Klicken Sie im Fenster Visual Studio Projektmappen-Explorer mit der rechten Maustaste auf das Projekt, und wählen Sie **Projektdatei bearbeiten**aus.</span><span class="sxs-lookup"><span data-stu-id="f6d5a-134">In the Visual Studio Solution Explorer window right-click on the project and select **Edit Project File**.</span></span> <span data-ttu-id="f6d5a-135">Unten in der Datei sehen Sie den Code, der Ihren ZIP-Ordner erstellt und aktualisiert, wenn die Anwendung erstellt wird:</span><span class="sxs-lookup"><span data-stu-id="f6d5a-135">At the bottom of the file you'll see the code that creates and updates your zip folder when the application builds:</span></span>

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

- <span data-ttu-id="f6d5a-136">Öffnen Sie eine Eingabeaufforderung im Stammverzeichnis des Projektverzeichnisses, und führen Sie den folgenden Befehl aus:</span><span class="sxs-lookup"><span data-stu-id="f6d5a-136">Open a command prompt in the root of your project directory and run the following command:</span></span>

```bash
ngrok http https://localhost:44355 -host-header="localhost:44355"
```

- <span data-ttu-id="f6d5a-137">Ngrok wird Anfragen aus dem Internet abhören und wird Sie an Ihre Anwendung weiterleiten, wenn Sie auf Port 44355 läuft.</span><span class="sxs-lookup"><span data-stu-id="f6d5a-137">Ngrok will listen to requests from the internet and will route them to your application when it is running on port 44355.</span></span> <span data-ttu-id="f6d5a-138">Es sollte ähneln `https://y8rCgT2b.ngrok.io/` , wo *y8rCgT2b* durch ihre ngrok Alpha-numerische HTTPS-URL ersetzt wird.</span><span class="sxs-lookup"><span data-stu-id="f6d5a-138">It should resemble `https://y8rCgT2b.ngrok.io/` where *y8rCgT2b* is replaced by your ngrok alpha-numeric HTTPS URL.</span></span>

- <span data-ttu-id="f6d5a-139">Achten Sie darauf, die Eingabeaufforderung mit ngrok beizubehalten, und notieren Sie sich die URL, die Sie später benötigen.</span><span class="sxs-lookup"><span data-stu-id="f6d5a-139">Be sure to keep the command prompt with ngrok running and to make note of the URL — you'll need it later.</span></span>

## <a name="update-your-application"></a><span data-ttu-id="f6d5a-140">Aktualisieren Ihrer Anwendung</span><span class="sxs-lookup"><span data-stu-id="f6d5a-140">Update your application</span></span>

<span data-ttu-id="f6d5a-141">In *Tab. cshtml* zeigt die Anwendung dem Benutzer zwei Optionsschaltflächen zum Anzeigen der Registerkarte mit einem roten oder grauen Symbol an.</span><span class="sxs-lookup"><span data-stu-id="f6d5a-141">Within *Tab.cshtml* the application presents the user with two option buttons for displaying the tab with either a red or gray icon.</span></span> <span data-ttu-id="f6d5a-142">Wenn **Sie die Option grau auswählen** oder **Rote** Schaltfläche auswählen auswählen, wird `saveGray()` `saveRed()` `settings.setValidityState(true)` die Schaltfläche **Speichern** auf der Konfigurationsseite ausgelöst oder aktiviert.</span><span class="sxs-lookup"><span data-stu-id="f6d5a-142">Choosing the **Select Gray** or **Select Red** button fires `saveGray()` or `saveRed()`, respectively, sets `settings.setValidityState(true)`, and enables the **Save** button on the configuration page.</span></span> <span data-ttu-id="f6d5a-143">Mit diesem Code können Teams wissen, dass Sie die Konfigurationsanforderungen erfüllt haben und die Installation fortgesetzt werden kann.</span><span class="sxs-lookup"><span data-stu-id="f6d5a-143">This code lets Teams know that you have satisfied the configuration requirements and the installation can proceed.</span></span> <span data-ttu-id="f6d5a-144">Bei Save werden die Parameter von `settings.setSettings` festgelegt.</span><span class="sxs-lookup"><span data-stu-id="f6d5a-144">On save, the parameters of `settings.setSettings` are set.</span></span> <span data-ttu-id="f6d5a-145">Schließlich `saveEvent.notifySuccess()` wird aufgerufen, um anzugeben, dass die Inhalts-URL erfolgreich aufgelöst wurde.</span><span class="sxs-lookup"><span data-stu-id="f6d5a-145">Finally, `saveEvent.notifySuccess()` is called to indicate that the content URL has successfully resolved.</span></span>

[!INCLUDE [dotnet-update-app](~/includes/tabs/dotnet-update-chan-grp-app.md)]

