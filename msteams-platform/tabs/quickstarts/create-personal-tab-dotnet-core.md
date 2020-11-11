---
title: Erstellen einer persönlichen Registerkarte mit ASP.net Core
author: laujan
description: Eine Schnellstartanleitung zum Erstellen einer benutzerdefinierten persönlichen Registerkarte mit ASP.net Core.
ms.topic: quickstart
ms.author: lajanuar
ms.openlocfilehash: 3eb0c42bb81ec8b2d906863051bd551c88c35f57
ms.sourcegitcommit: fdb53284a20285f7e8a7daf25e85cb5d06c52b95
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/11/2020
ms.locfileid: "48992631"
---
# <a name="create-a-personal-tab-with-aspnet-core"></a>Erstellen einer persönlichen Registerkarte mit ASP.net Core

In diesem Schnellstart werden wir durch das Erstellen einer benutzerdefinierten persönlichen Registerkarte mit C#-und ASP.net-Core-Razor-Seiten Schritt halten. Wir verwenden auch [App Studio für Microsoft Teams](~/concepts/build-and-test/app-studio-overview.md) , um Ihr App-Manifest abzuschließen und die Registerkarte in Teams bereitzustellen.

[!INCLUDE [dotnet-core-prereq](~/includes/tabs/dotnet-core-prereq.md)]

## <a name="get-the-source-code"></a>Abrufen des Quellcodes

Öffnen Sie eine Eingabeaufforderung, und erstellen Sie ein neues Verzeichnis für Ihr Tab-Projekt. Wir haben ein einfaches Projekt zur Verfügung gestellt, damit Sie loslegen können. Zum Abrufen des Quellcodes können Sie den ZIP-Ordner herunterladen und die Dateien extrahieren oder das Beispiel-Repository in Ihr neues Verzeichnis kopieren:

```bash
git clone https://github.com/OfficeDev/microsoft-teams-sample-tabs.git
```

Nachdem Sie den Quellcode haben, öffnen Sie Visual Studio, und wählen Sie **Projekt oder Lösung öffnen** aus. Navigieren Sie zum Anwendungsverzeichnis der Registerkarte, und öffnen Sie **PersonalTab. sln**.

Drücken Sie zum Erstellen und Ausführen der Anwendung **F5** , oder wählen Sie im Menü **Debuggen** die Option **Debuggen starten** aus. Navigieren Sie in einem Browser zu den folgenden URLs, um zu überprüfen, ob die Anwendung ordnungsgemäß geladen wurde:

- `http://localhost:44325/`
- `http://localhost:44325/personal`
- `http://localhost:44325/privacy`
- `http://localhost:44325/tou`

## <a name="review-the-source-code"></a>Überprüfen des Quellcodes

### <a name="startupcs"></a>Startup.cs

Dieses Projekt wurde aus einer leeren Vorlage für ASP.net Core 2,2-Webanwendungen erstellt, wobei das Kontrollkästchen *Erweiterte Konfiguration für HTTPS* beim Setup aktiviert ist. Die MVC-Dienste werden von der Dependency Injection Framework- `ConfigureServices()` Methode registriert. Darüber hinaus wird die Bereitstellung statischer Inhalte nicht standardmäßig durch die leere Vorlage aktiviert, sodass der Methode die statische Datei Middleware hinzugefügt wird `Configure()` :

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

### <a name="wwwroot-folder"></a>WWWRoot-Ordner

In ASP.net Core ist der Webstammordner, in dem die Anwendung nach statischen Dateien sucht.

### <a name="indexcshtml"></a>Index. cshtml

ASP.net Core behandelt Dateien namens " *Index* " als Standard/Homepage für die Website. Wenn Ihre Browser-URL auf den Stamm der Website zeigt, wird **Index. cshtml** als Startseite für Ihre Anwendung angezeigt.

### <a name="appmanifest-folder"></a>AppManifest-Ordner

Dieser Ordner enthält die folgenden erforderlichen App-Paketdateien:

- Ein **vollfarbiges Symbol** , das 192 x 192 Pixel misst.
- Ein **transparentes Umrisssymbol** , das 32 x 32 Pixel misst.
- Ein **manifest.jsfür** die Datei, die die Attribute Ihrer APP angibt.

Diese Dateien müssen in einem App-Paket gezippt werden, damit Sie Ihre Registerkarte in Microsoft Teams hochladen können. Microsoft Teams lädt das `contentUrl` angegebene in ihrem Manifest, bettet es in einen iframe ein und rendert es in ihrer Registerkarte.

### <a name="csproj"></a>. csproj

Klicken Sie im Fenster Visual Studio Projektmappen-Explorer mit der rechten Maustaste auf das Projekt, und wählen Sie **Projektdatei bearbeiten** aus. Unten in der Datei sehen Sie den Code, der Ihren ZIP-Ordner erstellt und aktualisiert, wenn die Anwendung erstellt wird:

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

- Öffnen Sie eine Eingabeaufforderung im Stammverzeichnis des Projektverzeichnisses, und führen Sie den folgenden Befehl aus:

```bash
ngrok http https://localhost:44325 -host-header="localhost:44325"
```

- Ngrok wird Anfragen aus dem Internet abhören und wird Sie an Ihre Anwendung weiterleiten, wenn Sie auf Port 44325 läuft.  Es sollte ähneln `https://y8rPrT2b.ngrok.io/` , wo *y8rPrT2b* durch ihre ngrok Alpha-numerische HTTPS-URL ersetzt wird.

- Achten Sie darauf, dass Sie die Eingabeaufforderung mit ngrok weiterhin ausführen, und notieren Sie sich die URL, die Sie später benötigen.

- Stellen Sie sicher, dass *ngrok* ausgeführt wird und ordnungsgemäß funktioniert, indem Sie Ihren Browser öffnen und zu ihrer Inhaltsseite über die ngrok-HTTPS-URL wechseln, die in Ihrem Eingabeaufforderungsfenster bereitgestellt wurde.

>[!TIP]
>Sie müssen sowohl Ihre Anwendung in Visual Studio als auch ngrok ausführen, um diesen Schnellstart abzuschließen. Wenn Sie die Ausführung der Anwendung in Visual Studio beenden müssen, um Sie zu bearbeiten, **halten Sie ngrok auf dem laufenden**. Sie wird weiterhin überwacht und setzt die Weiterleitung der Anforderung Ihrer Anwendung fort, wenn Sie in Visual Studio neu gestartet wird. Wenn Sie den ngrok-Dienst neu starten müssen, wird eine neue URL zurückgegeben, und Sie müssen jeden Ort aktualisieren, der diese URL verwendet.

### <a name="run-your-application"></a>Ausführen Ihrer Anwendung

- Drücken Sie in Visual Studio **F5** , oder klicken Sie im Menü **Debuggen** Ihrer Anwendung auf **Debuggen starten** .

[!INCLUDE [dotnet-personal-use-appstudio](~/includes/tabs/dotnet-personal-use-appstudio.md)]
