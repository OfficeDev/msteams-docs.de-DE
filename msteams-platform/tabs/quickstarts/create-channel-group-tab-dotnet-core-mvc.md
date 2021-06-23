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
# <a name="create-a-custom-channel-and-group-tab-with-aspnet-core-mvc"></a>Erstellen eines benutzerdefinierten Kanals und einer Gruppenregisterkarte mit ASP.NET Core MVC

In diesem Schnellstart werden wir schrittweise durch das Erstellen einer benutzerdefinierten Kanal-/Gruppenregisterkarte mit C# und ASP.Net Core MVC geführt. Wir verwenden App Studio auch [für Microsoft Teams,](~/concepts/build-and-test/app-studio-overview.md) um Ihr App-Manifest fertig zu stellen und Ihre Registerkarte für Teams bereitzustellen.

[!INCLUDE [dotnet-core-prereq](~/includes/tabs/dotnet-core-prereq.md)]

## <a name="get-the-source-code"></a>Abrufen des Quellcodes

Öffnen Sie eine Eingabeaufforderung, und erstellen Sie ein neues Verzeichnis für Ihr Registerkartenprojekt. Wir haben ein einfaches [Kanalgruppen-Registerkartenprojekt](https://github.com/OfficeDev/microsoft-teams-sample-tabs/tree/master/ChannelGroupTabMVC) bereitgestellt, um Ihnen den Einstieg zu erleichtern. Um den Quellcode abzurufen, können Sie den ZIP-Ordner herunterladen und die Dateien extrahieren oder das Beispiel-Repository in Ihr neues Verzeichnis klonen:

```bash
git clone https://github.com/OfficeDev/microsoft-teams-sample-tabs.git
```

Sobald Sie den Quellcode haben, öffnen Sie Visual Studio, und wählen Sie **Projekt oder Projektmappe öffnen** aus. Navigieren Sie zum Registerkartenanwendungsverzeichnis, und öffnen Sie **ChannelGroupTabMVC.sln**.

Drücken Sie **F5,** oder wählen Sie im Menü **"Debuggen"** die Option **"Debuggen starten"** aus, um die Anwendung zu erstellen und auszuführen. Navigieren Sie in einem Browser zu den folgenden URLs, und stellen Sie sicher, dass die Anwendung ordnungsgemäß geladen wurde:

- `http://localhost:44360`
- `http://localhost:44360/privacy`
- `http://localhost:44360/tou`

## <a name="review-the-source-code"></a>Überprüfen des Quellcodes

### <a name="startupcs"></a>Startup.cs

Dieses Projekt wurde aus einer leeren Vorlage für ASP.NET Core 2.2-Webanwendung erstellt, wobei das Kontrollkästchen *"Erweitert – Für HTTPS konfigurieren"* beim Setup aktiviert ist. Die MVC-Dienste werden durch die Methode des Abhängigkeitsinjektionsframeworks `ConfigureServices()` registriert. Darüber hinaus ermöglicht die leere Vorlage nicht standardmäßig die Bereitstellung statischer Inhalte, sodass die Middleware für statische Dateien der Methode hinzugefügt `Configure()` wird:

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

### <a name="wwwroot-folder"></a>Wwwroot-Ordner

In ASP.NET Core sucht die Anwendung im Webstammordner nach statischen Dateien.

### <a name="appmanifest-folder"></a>AppManifest-Ordner

Dieser Ordner enthält die folgenden erforderlichen App-Paketdateien:

- Ein **Vollfarbsymbol** mit einer Auflösung von 192 x 192 Pixeln.
- Ein **transparentes Gliederungssymbol** mit einer Auflösung von 32 x 32 Pixeln.
- Ein **manifest.jsfür** die Datei, die die Attribute Ihrer App angibt.

Diese Dateien müssen in einem App-Paket gezippt werden, um Ihre Registerkarte in Teams hochzuladen.

### <a name="csproj"></a>CSPROJ

Klicken Sie im Fenster Visual Studio Projektmappen-Explorer mit der rechten Maustaste auf das Projekt, und wählen Sie **"Bearbeiten Project Datei"** aus. Am Ende der Datei sehen Sie den Code, der Ihren ZIP-Ordner erstellt und aktualisiert, wenn die Anwendung erstellt wird:

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

*ChannelGroup.cs* stellt ein Message-Objekt und Methoden vor, die während der Konfiguration von den Controllern aufgerufen werden.

### <a name="views"></a>Ansichten

#### <a name="home"></a>Start

ASP.NET Core behandelt Dateien mit dem Namen *Index* als Standard-/Startseite für die Website. Wenn Ihre Browser-URL auf den Stamm der Website zeigt, wird **Index.cshtml** als Startseite für Ihre Anwendung angezeigt.

#### <a name="shared"></a>Shared

Das Partielle Ansichtsmarkup *_Layout.cshtml* enthält die allgemeine Seitenstruktur der Anwendung und freigegebene visuelle Elemente. Außerdem wird auf die Teams Bibliothek verwiesen.

### <a name="controllers"></a>Controller

Die Controller verwenden die ViewBag-Eigenschaft, um Werte dynamisch in die Ansichten zu übertragen.

[!INCLUDE [dotnet-ngrok-intro](~/includes/tabs/dotnet-ngrok-intro.md)]

- Öffnen Sie eine Eingabeaufforderung im Stammverzeichnis des Projekts, und führen Sie den folgenden Befehl aus:

    ```bash
    ngrok http https://localhost:443560 -host-header="localhost:44360"
    ```

- Ngrok lauscht auf Anforderungen aus dem Internet und leitet sie an Ihre Anwendung weiter, wenn sie auf Port 44355 ausgeführt wird.  Es sollte etwa so `https://y8rCgT2b.ngrok.io/` aussehen, wo *y8rCgT2b* durch Ihre alphangrok-numerische HTTPS-URL ersetzt wird.

- Achten Sie darauf, dass die Eingabeaufforderung mit ngrok ausgeführt wird, und notieren Sie sich die URL . Sie benötigen sie später.

## <a name="update-your-application"></a>Aktualisieren Der Anwendung

Innerhalb von **Tab.cshtml** zeigt die Anwendung dem Benutzer zwei Optionsschaltflächen zum Anzeigen der Registerkarte mit einem roten oder grauen Symbol an. Wenn Sie die Schaltfläche **"Grau auswählen"** oder **"Rot auswählen"** auswählen, wird diese ausgelöst `saveGray()` `saveRed()` bzw. `settings.setValidityState(true)` festgelegt, und die Schaltfläche **"Speichern"** wird auf der Konfigurationsseite aktiviert. Dieser Code teilt Teams mit, dass sie die Konfigurationsanforderungen erfüllt haben und die Installation fortgesetzt werden kann. Beim Speichern werden die Parameter `settings.setSettings` von festgelegt. Schließlich `saveEvent.notifySuccess()` wird aufgerufen, um anzugeben, dass die Inhalts-URL erfolgreich aufgelöst wurde.

[!INCLUDE [dotnet-update-app](~/includes/tabs/dotnet-update-chan-grp-app.md)]
