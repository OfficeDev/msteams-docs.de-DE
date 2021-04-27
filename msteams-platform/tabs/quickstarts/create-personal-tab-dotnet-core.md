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
# <a name="create-a-personal-tab-with-aspnet-core"></a>Erstellen einer persönlichen Registerkarte mit ASP.NET Core

In dieser Schnellstartanleitung wird eine benutzerdefinierte persönliche Registerkarte mit C# und ASP.Net erstellt. Außerdem verwenden wir [App Studio für Microsoft Teams,](~/concepts/build-and-test/app-studio-overview.md) um Ihr App-Manifest zu finalisieren und Ihre Registerkarte in Teams zu bereitstellen.

[!INCLUDE [dotnet-core-prereq](~/includes/tabs/dotnet-core-prereq.md)]

## <a name="get-the-source-code"></a>Den Quellcode erhalten

Öffnen Sie eine Eingabeaufforderung, und erstellen Sie ein neues Verzeichnis für Ihr Registerkartenprojekt. Wir haben ein einfaches Projekt bereitgestellt, mit dem Sie beginnen können. Zum Abrufen des Quellcodes können Sie den Zip-Ordner herunterladen und die Dateien extrahieren oder das Beispielrepository in Ihr neues Verzeichnis klonen:

```bash
git clone https://github.com/OfficeDev/microsoft-teams-sample-tabs.git
```

Sobald Sie den Quellcode haben, öffnen Sie Visual Studio, und wählen **Sie Projekt oder Projektmappe öffnen aus.** Navigieren Sie zum Verzeichnis der Registerkartenanwendung, und öffnen **Sie PersonalTab.sln**.

Drücken Sie **F5,** um die Anwendung zu erstellen und auszuführen, oder wählen Sie **Debuggen starten** im Menü **Debuggen** aus. Navigieren Sie in einem Browser zu den folgenden URLs, um zu überprüfen, ob die Anwendung ordnungsgemäß geladen wurde:

- `http://localhost:44325/`
- `http://localhost:44325/personal`
- `http://localhost:44325/privacy`
- `http://localhost:44325/tou`

## <a name="review-the-source-code"></a>Überprüfen des Quellcodes

### <a name="startupcs"></a>Startup.cs

Dieses Projekt wurde aus einer leeren ASP.NET Core 2.2-Webanwendung erstellt, deren Kontrollkästchen *Erweitert – Konfigurieren* für HTTPS beim Setup aktiviert ist. Die MVC-Dienste werden von der Methode des Abhängigkeitsinjektionsframeworks `ConfigureServices()` registriert. Darüber hinaus ermöglicht die leere Vorlage die Standardmäßige Entladung statischer Inhalte nicht, sodass die Middleware für statische Dateien der Methode hinzugefügt `Configure()` wird:

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

In ASP.NET Core befindet sich der Webstammordner, in dem die Anwendung nach statischen Dateien sucht.

### <a name="indexcshtml"></a>Index.cshtml

ASP.NET Core behandelt Dateien mit dem Namen *Index* als Standard-/Homepage für die Website. Wenn Ihre Browser-URL auf den Stamm der Website verweist, wird **Index.cshtml** als Homepage für Ihre Anwendung angezeigt.

### <a name="appmanifest-folder"></a>Ordner "AppManifest"

Dieser Ordner enthält die folgenden erforderlichen App-Paketdateien:

- Ein **Vollfarbsymbol** mit einer Breite von 192 x 192 Pixeln.
- Ein **transparentes Gliederungssymbol** mit einer Breite von 32 x 32 Pixeln.
- Eine **manifest.json-Datei,** die die Attribute Ihrer App angibt.

Diese Dateien müssen in einem App-Paket für die Verwendung beim Hochladen Ihrer Registerkarte in Teams gezippt werden. Microsoft Teams laden das in Ihrem Manifest angegebene, betten es in einen <ein und rendern ihn `contentUrl` \> auf Ihrer Registerkarte.

### <a name="csproj"></a>.csproj

Klicken Sie Visual Studio Projektmappen-Explorer mit der rechten Maustaste auf das Projekt, und wählen Sie **Projektdatei bearbeiten aus.** Unten in der Datei wird der Code angezeigt, mit dem Ihr ZIP-Ordner erstellt und aktualisiert wird, wenn die Anwendung erstellt:

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

- Öffnen Sie eine Eingabeaufforderung im Stammverzeichnis Ihres Projektverzeichnisses, und führen Sie den folgenden Befehl aus:

```bash
ngrok http https://localhost:44325 -host-header="localhost:44325"
```

- Ngrok lauscht Anforderungen aus dem Internet und führt sie an Ihre Anwendung weiter, wenn sie an Port 44325 ausgeführt wird.  Es sollte so `https://y8rPrT2b.ngrok.io/` aussehen, *dass y8rPrT2b* durch Ihre ngrok-alphanumerische HTTPS-URL ersetzt wird.

- Achten Sie darauf, dass die Eingabeaufforderung mit ngrok ausgeführt wird, und notieren Sie sich die URL – Sie benötigen sie später.

- Stellen Sie sicher, dass *ngrok* ordnungsgemäß ausgeführt und funktioniert, indem Sie Ihren Browser öffnen und über die ngrok-HTTPS-URL, die im Eingabeaufforderungsfenster bereitgestellt wurde, zu Ihrer Inhaltsseite wechseln.

>[!TIP]
>Sie müssen ihre Anwendung in Visual Studio und ngrok ausführen, um diesen Schnellstart ausführen zu können. Wenn Sie die Ausführung Ihrer Anwendung in Visual Studio ausführen müssen, halten Sie **ngrok am Laufen.** Sie lauscht weiterhin und setzt das Routing der Anforderung Ihrer Anwendung fort, wenn sie in einem Visual Studio. Wenn Sie den ngrok-Dienst neu starten müssen, gibt er eine neue URL zurück, und Sie müssen jeden Ort aktualisieren, der diese URL verwendet.

### <a name="run-your-application"></a>Ausführen der Anwendung

- Drücken Visual Studio **F5,** oder wählen Sie **Debuggen starten** im Menü **Debuggen** Ihrer Anwendung aus.

[!INCLUDE [dotnet-personal-use-appstudio](~/includes/tabs/dotnet-personal-use-appstudio.md)]
