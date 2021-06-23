---
title: Erstellen Sie eine persönliche Registerkarte mit ASP. NET Core MVC
author: surbhigupta
description: Eine Schnellstartanleitung zum Erstellen einer benutzerdefinierten persönlichen Registerkarte mit ASP. NET Core MVC.
localization_priority: Normal
ms.topic: quickstart
ms.author: lajanuar
ms.openlocfilehash: ac01ae64f44ccf3e06476d4412b16ac9a4730f6c
ms.sourcegitcommit: 623d81eb079d1842813265746a5fe0fe6311b196
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/22/2021
ms.locfileid: "53069151"
---
# <a name="create-a-custom-personal-tab-with-aspnet-core-mvc"></a>Erstellen einer benutzerdefinierten persönlichen Registerkarte mit ASP.NET Core MVC

In dieser Schnellstartanleitung werden wir schrittweise durch das Erstellen einer benutzerdefinierten persönlichen Registerkarte mit C# und ASP.Net Core MVC geführt. Wir verwenden App Studio auch [für Microsoft Teams,](~/concepts/build-and-test/app-studio-overview.md) um Ihr App-Manifest fertig zu stellen und Ihre Registerkarte für Teams bereitzustellen.

[!INCLUDE [dotnet-core-prereq](~/includes/tabs/dotnet-core-prereq.md)]

## <a name="get-the-source-code"></a>Abrufen des Quellcodes

Öffnen Sie eine Eingabeaufforderung, und erstellen Sie ein neues Verzeichnis für Ihr Registerkartenprojekt. Wir haben ein einfaches Projekt bereitgestellt, um Ihnen den Einstieg zu erleichtern. Um den Quellcode abzurufen, können Sie den ZIP-Ordner herunterladen und die Dateien extrahieren oder das Beispiel-Repository in Ihr neues Verzeichnis klonen:

``` bash
git clone https://github.com/OfficeDev/microsoft-teams-sample-tabs.git
```

Sobald Sie den Quellcode haben, öffnen Sie Visual Studio, und wählen Sie **Projekt oder Projektmappe öffnen** aus. Navigieren Sie zum Registerkartenanwendungsverzeichnis, und öffnen Sie **PersonalTabMVC.sln**.

Drücken Sie **F5,** oder wählen Sie im Menü **"Debuggen"** die Option **"Debuggen starten"** aus, um die Anwendung zu erstellen und auszuführen. Navigieren Sie in einem Browser zu den folgenden URLs, um zu überprüfen, ob die Anwendung ordnungsgemäß geladen wurde:

* `http://localhost:44335`
* `http://localhost:44335/privacy`
* `http://localhost:44335/tou`

## <a name="review-the-source-code"></a>Überprüfen des Quellcodes

### <a name="startupcs"></a>Startup.cs

Dieses Projekt wurde aus einem ASP erstellt. Leere Vorlage der NET Core 2.2-Webanwendung mit dem Kontrollkästchen *"Erweitert – Für HTTPS konfigurieren"* beim Setup aktiviert. Die MVC-Dienste werden durch die Methode des Abhängigkeitsinjektionsframeworks `ConfigureServices()` registriert. Darüber hinaus ermöglicht die leere Vorlage nicht standardmäßig die Bereitstellung statischer Inhalte, sodass die Middleware für statische Dateien der Methode hinzugefügt `Configure()` wird:

``` csharp
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

In ASP. NET Core, der Webstammordner, in dem die Anwendung nach statischen Dateien sucht.

### <a name="appmanifest-folder"></a>AppManifest-Ordner

Dieser Ordner enthält die folgenden erforderlichen App-Paketdateien:

* Ein **Vollfarbsymbol** mit einer Auflösung von 192 x 192 Pixeln.
* Ein **transparentes Gliederungssymbol** mit einer Auflösung von 32 x 32 Pixeln.
* Ein **manifest.jsfür** die Datei, die die Attribute Ihrer App angibt.

Diese Dateien müssen in einem App-Paket gezippt werden, um Ihre Registerkarte in Teams hochzuladen. Microsoft Teams lädt das `contentUrl` angegebene Element in Ihrem Manifest, betten es in einen IFrame ein und rendert es auf der Registerkarte.

### <a name="csproj"></a>CSPROJ

Klicken Sie im Fenster Visual Studio Projektmappen-Explorer mit der rechten Maustaste auf das Projekt, und wählen Sie **"Bearbeiten Project Datei"** aus. Am Ende der Datei sehen Sie den Code, der Ihren ZIP-Ordner erstellt und aktualisiert, wenn die Anwendung erstellt wird:

``` xml
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

**PersonalTab.cs** stellt ein Message-Objekt und Methoden dar, die von *PersonalTabController* aufgerufen werden, wenn ein Benutzer eine Schaltfläche in der **PersonalTab-Ansicht auswählt.**

### <a name="views"></a>Ansichten

#### <a name="home"></a>Start

Asp. NET Core behandelt Dateien mit dem Namen **Index** als Standard- oder Startseite für die Website. Wenn Ihre Browser-URL auf den Stamm der Website zeigt, wird **Index.cshtml** als Startseite für Ihre Anwendung angezeigt.

#### <a name="shared"></a>Shared

Das Partielle Ansichtsmarkup *_Layout.cshtml* enthält die allgemeine Seitenstruktur der Anwendung und freigegebene visuelle Elemente. Außerdem wird auf die Teams Bibliothek verwiesen.

### <a name="controllers"></a>Controller

Die Controller verwenden die ViewBag-Eigenschaft, um Werte dynamisch in die Ansichten zu übertragen.

[!INCLUDE [dotnet-update-personal-app](~/includes/tabs/dotnet-update-personal-app.md)]

[!INCLUDE [dotnet-ngrok-intro](~/includes/tabs/dotnet-ngrok-intro.md)]

* Öffnen Sie eine Eingabeaufforderung im Stammverzeichnis des Projekts, und führen Sie den folgenden Befehl aus:

    ``` bash
    ngrok http https://localhost:44345 -host-header="localhost:44345"
    ```

* Ngrok lauscht auf Anforderungen aus dem Internet und leitet sie an Ihre Anwendung weiter, wenn sie an Port 44325 ausgeführt wird.  Es sollte etwa so `https://y8rPrT2b.ngrok.io/` aussehen, wo *y8rPrT2b* durch Ihre alphangrok-numerische HTTPS-URL ersetzt wird.

* Achten Sie darauf, dass die Eingabeaufforderung mit ngrok ausgeführt wird, und notieren Sie sich die URL . Sie benötigen sie später.

* Stellen Sie sicher, dass **ngrok** ausgeführt wird und ordnungsgemäß funktioniert, indem Sie Ihren Browser öffnen und über die ngrok-HTTPS-URL, die im Eingabeaufforderungsfenster bereitgestellt wurde, zur Inhaltsseite wechseln.

> [!TIP]
> Sie müssen ihre Anwendung sowohl in Visual Studio als auch in ngrok ausführen, um diese Schnellstartanleitung abzuschließen. Wenn Sie die Ausführung der Anwendung in Visual Studio beenden müssen, um daran zu arbeiten, **führen Sie ngrok weiter aus.** Sie lauscht weiterhin und setzt das Routing der Anforderung Ihrer Anwendung fort, wenn sie in Visual Studio neu gestartet wird. Wenn Sie den ngrok-Dienst neu starten müssen, wird eine neue URL zurückgegeben, und Sie müssen jeden Ort aktualisieren, der diese URL verwendet.

### <a name="run-your-application"></a>Ausführen der Anwendung

* Drücken Sie in Visual Studio **F5,** oder wählen Sie **"Debuggen starten"** aus dem **Menü "Debuggen"** der Anwendung aus.

[!INCLUDE [dotnet-personal-use-appstudio](~/includes/tabs/dotnet-personal-use-appstudio.md)]

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Erstellen einer benutzerdefinierten Kanal- und Gruppenregisterkarte mit Node.js und dem Yeoman-Generator für Microsoft Teams](~/tabs/quickstarts/create-channel-group-tab-node-yeoman.md)
