---
title: Erstellen einer persönlichen Registerkarte mit ASP.NET Core
author: laujan
description: Eine Schnellstartanleitung zum Erstellen einer benutzerdefinierten persönlichen Registerkarte mit ASP.NET Core.
ms.topic: quickstart
localization_priority: Normal
ms.author: lajanuar
ms.openlocfilehash: 41aa916f4c69d50e48254d0f4934109429dab83c
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566894"
---
# <a name="create-a-personal-tab-using-aspnetcore"></a>Erstellen einer persönlichen Registerkarte mit ASP.NETCore

In dieser Schnellstartanleitung werden wir eine benutzerdefinierte persönliche Registerkarte mit den Seiten "C" und ASP.Net Core Razor erstellen. Wir verwenden App Studio auch [für Microsoft Teams,](~/concepts/build-and-test/app-studio-overview.md) um Ihr App-Manifest fertigzustellen und Ihre Registerkarte auf Teams bereitzustellen.

[!INCLUDE [dotnet-core-prereq](~/includes/tabs/dotnet-core-prereq.md)]

## <a name="get-the-source-code"></a>Abrufen des Quellcodes

Öffnen Sie eine Eingabeaufforderung, und erstellen Sie ein neues Verzeichnis für Ihr Registerkartenprojekt. Wir haben ein einfaches Projekt zur Verfügung gestellt, um Ihnen den Einstieg zu erleichtern. Um den Quellcode abzurufen, können Sie den ZIP-Ordner herunterladen und die Dateien extrahieren oder das Beispiel-Repository in Ihr neues Verzeichnis klonen:

```bash
git clone https://github.com/OfficeDev/microsoft-teams-sample-tabs.git
```

Sobald Sie den Quellcode haben, öffnen Sie Visual Studio und wählen Sie **Projekt oder Projektmappe öffnen** aus. Navigieren Sie zum Registerkartenanwendungsverzeichnis, und öffnen Sie **PersonalTab.sln**.

Um Ihre Anwendung zu erstellen und auszuführen, drücken Sie **F5** oder wählen Sie **Debuggen** starten im **Debugmenü** aus. Navigieren Sie in einem Browser zu den folgenden URLs, um die ordnungsgemäß geladene Anwendung zu überprüfen:

- `http://localhost:44325/`
- `http://localhost:44325/personal`
- `http://localhost:44325/privacy`
- `http://localhost:44325/tou`

## <a name="review-the-source-code"></a>Überprüfen des Quellcodes

### <a name="startupcs"></a>Startup.cs

Dieses Projekt wurde aus einer leeren Vorlage ASP.NET Core 2.2 Web Application mit dem Kontrollkästchen **Erweitert - Konfigurieren für HTTPS** erstellt, das bei Setup ausgewählt wurde. Die MVC-Dienste werden von der Methode des Abhängigkeitsinjektionsframeworks `ConfigureServices()` registriert. Darüber hinaus ermöglicht die leere Vorlage standardmäßig nicht die Bereitstellung statischer Inhalte, sodass die Middleware für statische Dateien der Methode hinzugefügt `Configure()` wird:

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

### <a name="wwwroot-folder"></a>wwwroot-Ordner

In ASP.NET Core ist der Webstammordner der Ort, an dem die Anwendung nach statischen Dateien sucht.

### <a name="indexcshtml"></a>Index.cshtml

ASP.NET Core behandelt Dateien mit dem Namen *Index* als Standard-/Homepage für die Website. Wenn Ihre Browser-URL auf den Stamm der Website verweist, wird **Index.cshtml** als Homepage für Ihre Anwendung angezeigt.

### <a name="appmanifest-folder"></a>AppManifest-Ordner

Dieser Ordner enthält die folgenden erforderlichen App-Paketdateien:

- Ein **Vollfarbsymbol** mit 192 x 192 Pixeln.
- Ein **transparentes Umrisssymbol** mit 32 x 32 Pixeln.
- Eine **manifest.jsin der** Datei, die die Attribute Ihrer App angibt.

Diese Dateien müssen in einem App-Paket gezippt werden, damit Sie Ihre Registerkarte in Teams hochladen können. Microsoft Teams lädt das `contentUrl` in Ihrem Manifest angegebene, bettet es in ein <iframe ein \> und rendert es in Der Registerkarte.

### <a name="csproj"></a>.csproj

Klicken Sie im Fenster Visual Studio Projektmappen-Explorer mit der rechten Maustaste auf das Projekt, und wählen Sie **Project Datei bearbeiten** aus. Am unteren Rand der Datei sehen Sie den Code, der Ihren ZIP-Ordner erstellt und aktualisiert, wenn die Anwendung erstellt wird:

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

- Ngrok hört Anfragen aus dem Internet ab und leitet sie an Ihre Anwendung weiter, wenn sie auf Port 44325 ausgeführt wird.  Es sollte der Stelle ähneln, an der `https://y8rPrT2b.ngrok.io/` *y8rPrT2b* durch Ihre alphanumerische HTTPS-URL von ngrok ersetzt wird.

- Achten Sie darauf, die Eingabeaufforderung zu halten, wenn ngrok ausgeführt wird, und notieren Sie sich die URL – Sie werden sie später benötigen.

- Stellen Sie sicher, dass **ngrok** ordnungsgemäß ausgeführt wird und ordnungsgemäß funktioniert, indem Sie Ihren Browser öffnen und über die ngrok HTTPS-URL, die in Ihrem Eingabeaufforderungsfenster bereitgestellt wurde, zur Inhaltsseite wechseln.

>[!TIP]
>Sie müssen sowohl Ihre Anwendung in Visual Studio als auch ngrok ausführen, um diese Schnellstartanleitung abzuschließen. Wenn Sie die Ausführung Ihrer Anwendung in Visual Studio beenden müssen, um daran zu arbeiten, **führen Sie ngrok aus.** Sie wird weiterhin überwacht und die Weiterleitung der Anforderung Ihrer Anwendung fortgesetzt, wenn sie in Visual Studio neu gestartet wird. Wenn Sie den ngrok-Dienst neu starten müssen, wird eine neue URL zurückgegeben, und Sie müssen jeden Ort aktualisieren, der diese URL verwendet.

### <a name="run-your-application"></a>Führen Sie Ihre Anwendung aus

- Drücken Sie Visual Studio **F5** oder wählen Sie **Debuggen** starten aus dem **Debug-Menü** Ihrer Anwendung aus.

[!INCLUDE [dotnet-personal-use-appstudio](~/includes/tabs/dotnet-personal-use-appstudio.md)]

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Erstellen einer benutzerdefinierten persönlichen Registerkarte mit ASP.NETCore MVC](~/tabs/quickstarts/create-personal-tab-dotnet-core-mvc.md)
