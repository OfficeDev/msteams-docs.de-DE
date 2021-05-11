---
title: Erstellen einer Kanal- und Gruppenregisterkarte mit ASP.NET Core
author: laujan
description: Eine Schnellstartanleitung zum Erstellen eines benutzerdefinierten Kanals und einer Gruppenregisterkarte mit ASP.NET Core.
localization_priority: Normal
ms.topic: quickstart
ms.author: lajanuar
ms.openlocfilehash: 8271e2d225d5ae3f6458b17b9595c4d23c3ca6c9
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2021
ms.locfileid: "52019573"
---
# <a name="create-a-custom-channel-and-group-tab-with-aspnet-core"></a>Erstellen eines benutzerdefinierten Kanals und einer Registerkarte "Gruppe" mit ASP.NET Core

In diesem Schnellstart werden wir durch das Erstellen einer benutzerdefinierten Kanal-/Gruppenregisterkarte mit C# und ASP.Net Core -Gestochenseite gehen. Außerdem verwenden wir [App Studio für Microsoft Teams,](~/concepts/build-and-test/app-studio-overview.md) um Ihr App-Manifest zu finalisieren und Ihre Registerkarte für die Teams.

[!INCLUDE [dotnet-core-prereq](~/includes/tabs/dotnet-core-prereq.md)]

## <a name="get-the-source-code"></a>Den Quellcode erhalten

Öffnen Sie eine Eingabeaufforderung, und erstellen Sie ein neues Verzeichnis für Ihr Registerkartenprojekt. Wir haben ein einfaches Projekt bereitgestellt, mit dem Sie beginnen können. Zum Abrufen des Quellcodes können Sie den Zip-Ordner herunterladen und die Dateien extrahieren oder das Beispielrepository in Ihr neues Verzeichnis klonen:

```bash
git clone https://github.com/OfficeDev/microsoft-teams-sample-tabs.git
```

Nachdem Sie den Quellcode verwendet haben, öffnen Sie Visual Studio, und wählen **Sie Projekt oder Projektmappe öffnen aus.** Navigieren Sie zum Verzeichnis der Registerkartenanwendung, und öffnen **Sie ChannelGroupTab.sln**.

Drücken Sie **F5,** um die Anwendung zu erstellen und auszuführen, oder wählen Sie **Debuggen starten** im Menü **Debuggen** aus. Navigieren Sie in einem Browser zu den folgenden URLs, und überprüfen Sie, ob die Anwendung ordnungsgemäß geladen wurde:

- `http://localhost:44355`
- `http://localhost:44355/privacy`
- `http://localhost:44355/tou`

## <a name="review-the-source-code"></a>Überprüfen des Quellcodes

### <a name="startupcs"></a>Startup.cs

Dieses Projekt wurde aus einer leeren ASP.NET Core 2.2-Webanwendung erstellt, deren Kontrollkästchen *Advanced – Configure for HTTPS* beim Setup aktiviert ist. Die MVC-Dienste werden von der Methode des Abhängigkeitsinjektionsframeworks `ConfigureServices()` registriert. Darüber hinaus ermöglicht die leere Vorlage die Standardmäßige Entladung statischer Inhalte nicht, sodass die Middleware für statische Dateien der Methode hinzugefügt `Configure()` wird:

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

### <a name="wwwroot-folder"></a>Ordner "wwwroot"

In ASP.NET Core ist der Webstammordner der Ort, in dem die Anwendung nach statischen Dateien sucht.

### <a name="indexcshtml"></a>Index.cshtml

ASP.NET Core behandelt Dateien mit dem Namen *Index* als Standard-/Homepage für die Website. Wenn Ihre Browser-URL auf den Stamm der Website verweist, wird **Index.cshtml** als Homepage für Ihre Anwendung angezeigt.

### <a name="tabcs"></a>Tab.cs

Diese C# enthält eine Methode, die während der Konfiguration von **Tab.cshtml** aufgerufen wird.

### <a name="appmanifest-folder"></a>Ordner "AppManifest"

Dieser Ordner enthält die folgenden erforderlichen App-Paketdateien:

- Ein **Vollfarbsymbol** mit einer Breite von 192 x 192 Pixeln.
- Ein **transparentes Gliederungssymbol** mit einer Breite von 32 x 32 Pixeln.
- Eine **manifest.json-Datei,** die die Attribute Ihrer App angibt.

Diese Dateien müssen in einem App-Paket gezippt werden, damit sie zum Hochladen Ihrer Registerkarte in das Teams. Wenn ein Benutzer ihre Registerkarte hinzufügen oder aktualisieren möchte, wird Microsoft Teams in Ihr Manifest geladen, in einen IFrame eingebettet und auf Ihrer Registerkarte `configurationUrl` gerendert.

### <a name="csproj"></a>.csproj

Klicken Sie Visual Studio Projektmappen-Explorer mit der rechten Maustaste auf das Projekt, und wählen Sie **Bearbeiten Project Datei aus.** Unten in der Datei wird der Code angezeigt, mit dem Ihr ZIP-Ordner erstellt und aktualisiert wird, wenn die Anwendung erstellt:

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

- Öffnen Sie eine Eingabeaufforderung im Stammverzeichnis Ihres Projektverzeichnisses, und führen Sie den folgenden Befehl aus:

```bash
ngrok http https://localhost:44355 -host-header="localhost:44355"
```

- Ngrok lauscht Anforderungen aus dem Internet und führt sie an Ihre Anwendung weiter, wenn sie an Port 44355 ausgeführt wird. Es sollte so `https://y8rCgT2b.ngrok.io/` aussehen, *dass y8rCgT2b* durch Ihre ngrok-alphanumerische HTTPS-URL ersetzt wird.

- Achten Sie darauf, dass die Eingabeaufforderung mit ngrok ausgeführt wird, und notieren Sie sich die URL – Sie benötigen sie später.

## <a name="update-your-application"></a>Aktualisieren Ihrer Anwendung

In *Tab.cshtml* stellt die Anwendung dem Benutzer zwei Optionsschaltflächen zum Anzeigen der Registerkarte mit einem roten oder einem grauen Symbol zur Auswahl. Wenn Sie die  Schaltfläche **Grau auswählen** oder Rot auswählen aktivieren, wird bzw. wird die Schaltfläche Speichern auf der `saveGray()` `saveRed()` `settings.setValidityState(true)` Konfigurationsseite aktiviert.  Dieser Code Teams, dass Sie die Konfigurationsanforderungen erfüllt haben und die Installation fortgesetzt werden kann. Beim Speichern werden die Parameter `settings.setSettings` von festgelegt. Schließlich wird `saveEvent.notifySuccess()` aufgerufen, um anzugeben, dass die Inhalts-URL erfolgreich aufgelöst wurde.

[!INCLUDE [dotnet-update-app](~/includes/tabs/dotnet-update-chan-grp-app.md)]

