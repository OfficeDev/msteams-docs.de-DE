---
title: Erstellen einer Kanal-und Gruppenregisterkarte mit ASP.net-Kern-MVC
author: laujan
description: Eine Schnellstartanleitung zum Erstellen einer benutzerdefinierten Kanal-und Gruppenregisterkarte mit ASP.net Core MVC.
ms.topic: quickstart
ms.author: laujan
ms.openlocfilehash: 57c22d10414eb8ec93249584219488397f0b6b33
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674297"
---
# <a name="create-a-custom-channel-and-group-tab-with-aspnet-core-mvc"></a>Erstellen einer benutzerdefinierten Kanal-und Gruppenregisterkarte mit ASP.net-Kern-MVC

In diesem Schnellstart werden wir durch das Erstellen einer benutzerdefinierten Kanal-Gruppe-Registerkarte mit C#-und ASP.net-Kern-MVC Schritt halten. Wir verwenden auch [App Studio für Microsoft Teams](~/concepts/build-and-test/app-studio-overview.md) , um Ihr App-Manifest abzuschließen und die Registerkarte in Teams bereitzustellen.

[!INCLUDE [dotnet-core-prereq](~/includes/tabs/dotnet-core-prereq.md)]

## <a name="get-the-source-code"></a>Abrufen des Quellcodes

Öffnen Sie eine Eingabeaufforderung, und erstellen Sie ein neues Verzeichnis für Ihr Tab-Projekt. Wir haben ein einfaches [Kanalgruppen-Registerkarten](https://github.com/OfficeDev/microsoft-teams-sample-tabs/ChannelGroupTabMVC) Projekt zur Verfügung gestellt, damit Sie loslegen können. Zum Abrufen des Quellcodes können Sie den ZIP-Ordner herunterladen und die Dateien extrahieren oder das Beispiel-Repository in Ihr neues Verzeichnis kopieren:

```bash
git clone https://github.com/OfficeDev/microsoft-teams-sample-tabs.git
```

Nachdem Sie den Quellcode haben, öffnen Sie Visual Studio, und wählen Sie **Projekt oder Lösung öffnen**aus. Navigieren Sie zum Anwendungsverzeichnis der Registerkarte, und öffnen Sie **ChannelGroupTabMVC. sln**.

Drücken Sie zum Erstellen und Ausführen der Anwendung **F5** , oder wählen Sie im Menü **Debuggen** die Option **Debuggen starten** aus. Navigieren Sie in einem Browser zu den folgenden URLs, und überprüfen Sie, ob die Anwendung ordnungsgemäß geladen wurde:

- `http://localhost:44360`
- `http://localhost:44360/privacy`
- `http://localhost:44360/tou`

## <a name="review-the-source-code"></a>Überprüfen des Quellcodes

### <a name="startupcs"></a>Startup.cs

Dieses Projekt wurde aus einer leeren Vorlage für ASP.net Core 2,2-Webanwendungen erstellt, wobei das Kontrollkästchen *Erweiterte Konfiguration für HTTPS* beim Setup aktiviert ist. Die MVC `ConfigureServices()` -Dienste werden von der Dependency Injection Framework-Methode registriert. Darüber hinaus wird die Bereitstellung statischer Inhalte nicht standardmäßig durch die leere Vorlage aktiviert, sodass der `Configure()` Methode die statische Datei Middleware hinzugefügt wird:

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

### <a name="appmanifest-folder"></a>AppManifest-Ordner

Dieser Ordner enthält die folgenden erforderlichen App-Paketdateien:

- Ein **vollfarbiges Symbol** , das 192 x 192 Pixel misst.
- Ein **transparentes Umrisssymbol** , das 32 x 32 Pixel misst.
- Eine **Manifest. JSON** -Datei, die die Attribute Ihrer APP angibt.

Diese Dateien müssen in einem App-Paket gezippt werden, damit Sie Ihre Registerkarte in Microsoft Teams hochladen können.

### <a name="csproj"></a>. csproj

Klicken Sie im Fenster Visual Studio Projektmappen-Explorer mit der rechten Maustaste auf das Projekt, und wählen Sie **Projektdatei bearbeiten**aus. Unten in der Datei sehen Sie den Code, der Ihren ZIP-Ordner erstellt und aktualisiert, wenn die Anwendung erstellt wird:

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

### <a name="models"></a>Modelle

*ChannelGroup.cs* zeigt ein Message-Objekt und Methoden an, die während der Konfiguration von den Controllern aufgerufen werden.

### <a name="views"></a>Ansichten

#### <a name="home"></a>Startseite

ASP.net Core behandelt Dateien namens " *Index* " als Standard/Homepage für die Website. Wenn Ihre Browser-URL auf den Stamm der Website zeigt, wird **Index. cshtml** als Startseite für Ihre Anwendung angezeigt.

#### <a name="shared"></a>Shared

Das Markup *_Layout. cshtml* der partiellen Ansicht enthält die gesamte Seitenstruktur der Anwendung sowie freigegebene visuelle Elemente. Außerdem wird auf die Microsoft Teams-Bibliothek verwiesen.

### <a name="controllers"></a>Controller

Die Controller verwenden die ViewBag-Eigenschaft, um Werte dynamisch zu den Ansichten zu übertragen.

[!INCLUDE [dotnet-ngrok-intro](~/includes/tabs/dotnet-ngrok-intro.md)]

- Öffnen Sie eine Eingabeaufforderung im Stammverzeichnis des Projektverzeichnisses, und führen Sie den folgenden Befehl aus:

```bash
ngrok http https://localhost:443560 -host-header="localhost:44360"
```

- Ngrok wird Anfragen aus dem Internet abhören und wird Sie an Ihre Anwendung weiterleiten, wenn Sie auf Port 44355 läuft.  Es sollte ähneln `https://y8rCgT2b.ngrok.io/` , wo *y8rCgT2b* durch ihre ngrok Alpha-numerische HTTPS-URL ersetzt wird.

- Achten Sie darauf, die Eingabeaufforderung mit ngrok beizubehalten, und notieren Sie sich die URL, die Sie später benötigen.

## <a name="update-your-application"></a>Aktualisieren Ihrer Anwendung

In **Tab. cshtml** zeigt die Anwendung dem Benutzer zwei Optionsschaltflächen zum Anzeigen der Registerkarte mit einem roten oder grauen Symbol an. Wenn **Sie die Option grau auswählen** oder **Rote** Schalt `saveGray()` Fläche `saveRed()`auswählen auswählen, wird `settings.setValidityState(true)`die Schaltfläche **Speichern** auf der Konfigurationsseite ausgelöst oder aktiviert. Mit diesem Code können Teams wissen, dass Sie die Konfigurationsanforderungen erfüllt haben und die Installation fortgesetzt werden kann. Bei Save werden die Parameter von `settings.setSettings` festgelegt. Schließlich `saveEvent.notifySuccess()` wird aufgerufen, um anzugeben, dass die Inhalts-URL erfolgreich aufgelöst wurde.

[!INCLUDE [dotnet-update-app](~/includes/tabs/dotnet-update-chan-grp-app.md)]

[!INCLUDE [dotnet-upload-to-teams](~/includes/tabs/dotnet-upload-to-teams.md)]
