---
title: Erstellen einer persönlichen Registerkarte
author: laujan
description: Eine Schnellstartanleitung zum Erstellen einer persönlichen Registerkarte mit dem Yeoman-Generator, ASP.NET Core oder ASP.NET Core MVC für Microsoft Teams mit Node.js und aktualisieren des App-Manifests.
ms.localizationpriority: medium
ms.topic: quickstart
ms.author: lajanuar
keywords: Yeoman ASP.NET Berechtigungsspeicher des MVC-Pakets "appmanifest conversation"
zone_pivot_groups: teams-app-environment
ms.openlocfilehash: 43302047a3c5712a17e2bc506eca2eeb350db825
ms.sourcegitcommit: 3dc9b539c6f7fbfb844c47a78e3b4d2200dabdad
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/31/2022
ms.locfileid: "64571364"
---
# <a name="create-a-personal-tab"></a>Erstellen einer persönlichen Registerkarte

Persönliche Registerkarten sind zusammen mit auf eine Person bezogene Bots Bestandteil persönlicher Apps und sind auf einen einzelnen Benutzer beschränkt. Sie können für einen einfachen Zugriff an den linken Bereich angeheftet werden. Sie können auch die API für persönliche Registerkarten [neu anordnen](#reorder-static-personal-tabs) und hinzufügen[`registerOnFocused`](#add-registeronfocused-api-for-tabs-or-personal-apps).

Stellen Sie sicher, dass Sie über alle [Vorabversionen](~/tabs/how-to/tab-requirements.md) verfügen, um Ihre persönliche Registerkarte zu erstellen.

::: zone pivot="node-java-script"

## <a name="create-a-personal-tab-with-nodejs"></a>Erstellen einer persönlichen Registerkarte mit Node.js

So erstellen Sie eine persönliche Registerkarte mit Node.js

1. Installieren Sie an der Eingabeaufforderung die [Yeoman](https://yeoman.io/) - und [gulp-cli-Pakete](https://www.npmjs.com/package/gulp-cli) , indem Sie nach der Installation des Node.js den folgenden Befehl eingeben:

    ```cmd
    npm install yo gulp-cli --global
    ```

1. Installieren Sie an der Eingabeaufforderung Microsoft Teams App-Generator, indem Sie den folgenden Befehl eingeben:

    ```cmd
    npm install generator-teams --global
    ```

Führen Sie die folgenden Schritte zum Erstellen einer persönlichen Registerkarte aus:

1. [Generieren Ihrer Anwendung mit einer persönlichen Registerkarte](#generate-your-application-with-a-personal-tab)
1. [Hinzufügen einer Inhaltsseite zur persönlichen Registerkarte](#add-a-content-page-to-the-personal-tab)
1. [Erstellen Ihres App-Pakets](#create-your-app-package)
1. [Erstellen und Ausführen der Anwendung](#build-and-run-your-application)
1. [Einrichten eines sicheren Tunnels zu Ihrer persönlichen Registerkarte](#establish-a-secure-tunnel-to-your-tab)
1. [Hochladen Der Anwendung Teams](#upload-your-application-to-teams)

### <a name="generate-your-application-with-a-personal-tab"></a>Generieren Ihrer Anwendung mit einer persönlichen Registerkarte

1. Erstellen Sie an der Eingabeaufforderung ein neues Verzeichnis für Ihre persönliche Registerkarte.

1. Geben Sie den folgenden Befehl in Ihr neues Verzeichnis ein, um den Microsoft Teams App-Generator zu starten:

    ```cmd
    yo teams
    ```

1. Geben Sie Ihre Werte für eine Reihe von Fragen ein, die von Microsoft Teams App-Generator zum Aktualisieren der **Manifest.json-Datei** aufgefordert werden.

    :::image type="content" source="~/assets/images/tab-images/teamsTabScreenshot.PNG" alt-text="Teams-Generator" border="true":::

    <details>
    <summary><b>Reihe von Fragen zum Aktualisieren der Datei "manifest.json"</b></summary>

    * **Wie lautet der Name Ihrer Lösung?**

      Der Projektmappenname ist Ihr Projektname. Sie können den vorgeschlagenen Namen akzeptieren, indem Sie die **EINGABETASTE** drücken.

    * **Wohin möchten Sie die Daten verschieben?**

      Sie befinden sich derzeit in Ihrem Projektverzeichnis. Drücken Sie **die EINGABETASTE**.

    * **Titel Ihres Microsoft Teams-App-Projekts?**

      Der Titel ist ihr App-Paketname und wird im App-Manifest und in der Beschreibung verwendet. Geben Sie einen Titel ein, oder drücken Sie **die EINGABETASTE** , um den Standardnamen zu übernehmen.

    * **Ihr (Firmen-)Name? (max. 32 Zeichen)**

      Ihr Firmenname wird im App-Manifest verwendet. Geben Sie einen Firmennamen ein, oder drücken Sie die **EINGABETASTE** , um den Standardnamen zu übernehmen.

    * **Welche Manifestversion möchten Sie verwenden?**

      Wählen Sie das Standardschema aus.

    * **Schnelles Gerüst? (J/n)**

      Der Standardwert ist "ja". Geben Sie **n** ein, um Ihre Microsoft Partner-ID einzugeben.

    * **Geben Sie Ihre Microsoft Partner-ID ein, wenn Sie eine haben? (Leer lassen, um zu überspringen)**

      Dieses Feld ist nicht erforderlich und muss nur verwendet werden, wenn Sie bereits Teil des [Microsoft Partner Network](https://partner.microsoft.com) sind.

    * **Was möchten Sie Ihrem Projekt hinzufügen?**

      Select **( &ast; ) A Tab**.

    * **Die URL, unter der Sie diese Lösung hosten werden?**

      Standardmäßig schlägt der Generator eine Azure-Website-URL vor. Sie testen Ihre App nur lokal, sodass keine gültige URL erforderlich ist.

    * **Möchten Sie eine Ladeanzeige anzeigen, wenn Ihre App/Registerkarte geladen wird?**

      Schließen Sie beim Laden ihrer App oder Registerkarte **keine** Ladeanzeige ein. Der Standardwert ist "Nein", geben Sie **"n**" ein.

    * **Möchten Sie, dass persönliche Apps ohne eine Registerkarten-Kopfleiste dargestellt werden?**

      Verwenden Sie **keine** persönlichen Apps, die ohne Registerkartenkopfleiste gerendert werden sollen. Default is no, enter **n**.

    * **Möchten Sie testframework und erste Tests einbeziehen? (y/N)**

      Schließen Sie **kein** Testframework für dieses Projekt ein. Der Standardwert ist "Nein", geben Sie **"n**" ein.

    * **Möchten Sie ESLint-Support einschließen? (y/N)**

      Schließen Sie keine ESLint-Unterstützung ein. Der Standardwert ist "Nein", geben Sie **"n**" ein.

    * **Möchten Sie Azure Applications Insights für Telemetrie verwenden? (y/N)**

      Wählen Sie **, Azure-Anwendung Insights nicht** einzuschließen.[](/azure/azure-monitor/app/app-insights-overview) Der Standardwert ist "nein". geben Sie **n** ein

    * **Standardregisterkartenname (max. 16 Zeichen)?**

      Nennen Sie Ihre Registerkarte. Dieser Registerkartenname wird im gesamten Projekt als Datei- oder URL-Pfadkomponente verwendet.

    * **Welche Art von Registerkarte möchten Sie erstellen?**

      Verwenden Sie die Pfeiltasten, um **"Persönlich" (statisch)** auszuwählen.

    * **Benötigen Sie Microsoft Azure Active Directory (Azure AD) Single Sign-On-Unterstützung für die Registerkarte?**

      Wählen Sie aus, Azure AD Single Sign-On-Unterstützung für die Registerkarte **nicht** einzuschließen. Der Standardwert ist "Ja", geben Sie **"n**" ein.

    </details>

### <a name="add-a-content-page-to-the-personal-tab"></a>Hinzufügen einer Inhaltsseite zur persönlichen Registerkarte

Erstellen Sie eine Inhaltsseite, und aktualisieren Sie die vorhandenen Dateien der persönlichen Registerkartenanwendung:

1. Erstellen Sie eine neue **personal.html-Datei** in Ihrer Visual Studio Code mit dem folgenden Markup:

    ```html
    <!DOCTYPE html>
    <html>
        <head>
            <meta charset="UTF-8">
            <title>
                <!-- Todo: add your a title here -->
            </title>
            <meta name="viewport" content="width=device-width, initial-scale=1.0">
            <!-- inject:css -->
            <!-- endinject -->
        </head>
            <body>
                <h1>Personal Tab</h1>
                <p><img src="/assets/icon.png"></p>
                <p>This is your personal tab!</p>
            </body>
    </html>
    ```

1. Speichern Sie **personal.html** im **öffentlichen** Ordner Ihrer Anwendung am folgenden Speicherort:

    ```
    ./src/public/<yourDefaultTabNameTab>/personal.html
    ```

1. Öffnen Sie **"manifest.json**" am folgenden Speicherort in Ihrem Visual Studio Code:

    ```
     ./src/manifest/manifest.json
    ```

1. Fügen Sie dem leeren `staticTabs` Array (`staticTabs":[]`) Folgendes hinzu, und fügen Sie das folgende JSON-Objekt hinzu:

    ```json
    {
        "entityId": "personalTab",
        "name": "Personal Tab ",
        "contentUrl": "https://{{HOSTNAME}}/<yourDefaultTabNameTab>/personal.html",
        "websiteUrl": "https://{{HOSTNAME}}",
        "scopes": ["personal"]
    }
    ```

    > [!IMPORTANT]
    > The path component **yourDefaultTabNameTab** is the value that you entered in the generator for **Default Tab Name** plus the word **Tab**.
    >
    > Beispiel: DefaultTabName ist **MyTab** und **dann /MyTabTab/**

1. Aktualisieren Sie die **contentURL-Pfadkomponente** **"yourDefaultTabNameTab"** mit dem tatsächlichen Registerkartennamen.

1. Save the updated **manifest.json** file.

1. Öffnen Sie **Tab.ts** in Ihrem Visual Studio Code über den folgenden Pfad, um Ihre Inhaltsseite in einem IFrame bereitzustellen:

    ```bash
    ./src/server/<yourDefaultTabNameTab>/<yourDefaultTabNameTab>.ts
    ```

1. Fügen Sie der Liste der IFrame-Decoratoren Folgendes hinzu:

    ```typescript
     @PreventIframe("/<yourDefaultTabName Tab>/personal.html")
    ```

1. Speichern Sie die aktualisierte Datei. Der Registerkartencode ist vollständig.

### <a name="create-your-app-package"></a>Erstellen Ihres App-Pakets

Sie benötigen ein App-Paket zum Erstellen und Ausführen der Anwendung in Teams. The app package is created through a gulp task that validates the **manifest.json** file and generates the zip folder in the **./package** directory. Geben Sie an der Eingabeaufforderung den folgenden Befehl ein:

```cmd
gulp manifest
```

### <a name="build-and-run-your-application"></a>Erstellen und Ausführen der Anwendung

#### <a name="build-your-application"></a>Erstellen Der Anwendung

Geben Sie an der Eingabeaufforderung den folgenden Befehl ein, um Ihre Lösung in den Ordner **"./dist"** zu transpilieren:

```cmd
gulp build
```

#### <a name="run-your-application"></a>Ausführen der Anwendung

1. Geben Sie an der Eingabeaufforderung den folgenden Befehl ein, um einen lokalen Webserver zu starten:

    ```cmd
    gulp serve
    ```

1. Geben Sie `http://localhost:3007/<yourDefaultAppNameTab>/` in Ihren Browser ein, um die Startseite Ihrer Anwendung anzuzeigen.

    :::image type="content" source="~/assets/images/tab-images/homePage.png" alt-text="Standardregisterkarte" border="true":::

1. Navigieren Sie `http://localhost:3007/<yourDefaultAppNameTab>/personal.html`, um Ihre persönliche Registerkarte anzuzeigen.

    :::image type="content" source="~/assets/images/tab-images/personalTab.PNG" alt-text="Standard-HTML-Registerkarte" border="true":::

### <a name="establish-a-secure-tunnel-to-your-tab"></a>Einrichten eines sicheren Tunnels zu Ihrer Registerkarte

Beenden Sie an der Eingabeaufforderung den localhost, und geben Sie den folgenden Befehl ein, um einen sicheren Tunnel zu Ihrer Registerkarte einzurichten:

```cmd
gulp ngrok-serve
```

> [!IMPORTANT]
> Nachdem Die Registerkarte in Microsoft Teams über **ngrok** hochgeladen und erfolgreich gespeichert wurde, können Sie sie in Teams anzeigen, bis die Tunnelsitzung endet.

### <a name="upload-your-application-to-teams"></a>Hochladen Der Anwendung Teams

1. Wechseln Sie zu Microsoft Teams, und wählen Sie **Store**&nbsp; :::image type="content" source="~/assets/images/tab-images/store.png" alt-text="Teams Store"::: aus.
1. Wählen Sie **"Apps verwalten" aus**.
1. Wählen Sie **"App veröffentlichen"** und **Hochladen einer benutzerdefinierten App** aus.

    :::image type="content" source="~/assets/images/tab-images/publish-app.png" alt-text="Hochladen benutzerdefinierte App" border="true":::

1. Wechseln Sie zu Ihrem Projektverzeichnis, navigieren Sie zum Ordner **"./package** ", wählen Sie den ZIP-Ordner aus, und wählen Sie " **Öffnen**" aus.

    :::image type="content" source="~/assets/images/tab-images/addingpersonaltab.png" alt-text="Hinzufügen Ihrer persönlichen Registerkarte" border="true":::

1. Wählen Sie im Popupfenster " **Hinzufügen** " aus. Ihre Registerkarte wird in Teams hochgeladen.

    :::image type="content" source="~/assets/images/tab-images/personaltabuploaded.png" alt-text="Persönliche Registerkarte hochgeladen" border="true":::

1. Wählen Sie im linken Bereich von Teams Ellipsen &#x25CF;&#x25CF;&#x25CF; aus, und wählen Sie dann Ihre hochgeladene App aus, um Ihre persönliche Registerkarte anzuzeigen.

   Jetzt haben Sie erfolgreich Ihre persönliche Registerkarte in Teams erstellt und hinzugefügt.
  
   Da Sie Ihre persönliche Registerkarte in Teams haben, können Sie auch die API für Ihre persönliche Registerkarte [neu anordnen](#reorder-static-personal-tabs) und hinzufügen[`registerOnFocused`](#add-registeronfocused-api-for-tabs-or-personal-apps).

::: zone-end

::: zone pivot="razor-csharp"

## <a name="create-a-personal-tab-with-aspnet-core"></a>Erstellen einer persönlichen Registerkarte mit ASP.NET Core

Sie können eine benutzerdefinierte persönliche Registerkarte mit C# und ASP.NET Core Razor-Seiten erstellen. So erstellen Sie eine persönliche Registerkarte mit ASP.NET Core

1. Erstellen Sie an der Eingabeaufforderung ein neues Verzeichnis für Ihr Registerkartenprojekt.

1. Klonen Sie das Beispiel-Repository mit dem folgenden Befehl in Ihr neues Verzeichnis, oder Sie können den [Quellcode](https://github.com/OfficeDev/Microsoft-Teams-Samples) herunterladen und die Dateien extrahieren:

    ```cmd
    git clone https://github.com/OfficeDev/Microsoft-Teams-Samples.git
    ```

Führen Sie die folgenden Schritte zum Erstellen einer persönlichen Registerkarte aus:

1. [Generieren Ihrer Anwendung mit einer persönlichen Registerkarte](#generate-your-application-with-a-personal-tab-1)
1. [Aktualisieren und Ausführen der Anwendung](#update-and-run-your-application)
1. [Einrichten eines sicheren Tunnels zu Ihrer Registerkarte](#establish-a-secure-tunnel-to-your-tab-1)
1. [Aktualisieren Des App-Pakets mit dem Entwicklerportal](#update-your-app-package-with-developer-portal)
1. [Anzeigen einer Vorschau Ihrer App in Teams](#preview-your-app-in-teams)

### <a name="generate-your-application-with-a-personal-tab"></a>Generieren Ihrer Anwendung mit einer persönlichen Registerkarte

1. Öffnen Sie Visual Studio, und wählen Sie **"Projekt oder Projektmappe öffnen**" aus.

1. Wechseln Sie zum Ordner "Microsoft-Teams-Samplessamplestab-personalrazor-csharp >  >  > ", und öffnen Sie **"PersonalTab.sln"**.

1. Wählen Sie in Visual Studio **F5** aus, oder wählen Sie im **Menü "Debuggen**" der Anwendung die Option **"Debuggen starten**" aus, um zu überprüfen, ob die Anwendung ordnungsgemäß geladen wurde. Wechseln Sie in einem Browser zu den folgenden URLs:

    * <http://localhost:3978/>
    * <http://localhost:3978/personalTab>
    * <http://localhost:3978/privacy>
    * <http://localhost:3978/tou>

<details>
<summary><b>Überprüfen des Quellcodes</b></summary>

#### <a name="startupcs"></a>Startup.cs

Dieses Projekt wurde aus einer leeren Vorlage ASP.NET Core 3.1-Webanwendung erstellt, wobei das Kontrollkästchen **"Erweitert – Für HTTPS konfigurieren**" beim Setup aktiviert ist. Die MVC-Dienste werden durch die Methode des Abhängigkeitsinjektionsframeworks `ConfigureServices()` registriert. Darüber hinaus ermöglicht die leere Vorlage nicht standardmäßig die Bereitstellung statischer Inhalte, sodass die Middleware für statische Dateien der Methode mit dem folgenden Code hinzugefügt `Configure()` wird:

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

#### <a name="wwwroot-folder"></a>Wwwroot-Ordner

In ASP.NET Core sucht die Anwendung im Webstammordner nach statischen Dateien.

#### <a name="indexcshtml"></a>Index.cshtml

ASP.NET Core behandelt Dateien mit dem Namen **Index** als Standard- oder Startseite für die Website. Wenn Ihre Browser-URL auf den Stamm der Website zeigt, wird **Index.cshtml** als Startseite für Ihre Anwendung angezeigt.

#### <a name="appmanifest-folder"></a>AppManifest-Ordner

Dieser Ordner enthält die folgenden erforderlichen App-Paketdateien:

* Ein **Vollfarbsymbol** mit einer Auflösung von 192 x 192 Pixeln.
* Ein **transparentes Gliederungssymbol** mit einer Auflösung von 32 x 32 Pixeln.
* Eine **Manifest.json-Datei** , die die Attribute Ihrer App angibt.

Diese Dateien müssen in einem App-Paket gezippt werden, um Ihre Registerkarte in Teams hochzuladen. Microsoft Teams das `contentUrl` angegebene Element in Ihrem Manifest lädt, es in einen <iframe\> einbettet und auf der Registerkarte rendert.

#### <a name="csproj"></a>CSPROJ

Klicken Sie in Visual Studio Projektmappen-Explorer mit der rechten Maustaste auf das Projekt, und wählen Sie **Project Datei bearbeiten** aus. Am Ende der Datei sehen Sie den folgenden Code, der Ihren ZIP-Ordner erstellt und aktualisiert, wenn die Anwendung erstellt wird:

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

</details>

### <a name="update-and-run-your-application"></a>Aktualisieren und Ausführen der Anwendung

1. Wechseln Sie zum Ordner **"PagesShared** > "**,** öffnen **Sie _Layout.cshtml**, und fügen Sie Dem Tags-Abschnitt Folgendes `<head>` hinzu:

    ```HTML
    <script src="https://ajax.aspnetcdn.com/ajax/jQuery/jquery-3.4.1.min.js"></script>
    <script src="https://statics.teams.cdn.office.net/sdk/v1.6.0/js/MicrosoftTeams.min.js"></script>
    ```

1. Öffnen Sie **"PersonalTab.cshtml**" im Ordner **"Pages**", fügen Sie die `<script>` Tags hinzu`microsoftTeams.initialize()`, und speichern Sie sie.

1. Wählen Sie in Visual Studio **F5** aus, oder wählen Sie im **Menü "Debuggen**" der Anwendung die Option **"Debuggen starten**" aus.

### <a name="establish-a-secure-tunnel-to-your-tab"></a>Einrichten eines sicheren Tunnels zu Ihrer Registerkarte

Führen Sie an der Eingabeaufforderung im Stammverzeichnis des Projekts den folgenden Befehl aus, um einen sicheren Tunnel zu Ihrer Registerkarte einzurichten:

```cmd
ngrok http 3978 --host-header=localhost
```

### <a name="update-your-app-package-with-developer-portal"></a>Aktualisieren Des App-Pakets mit dem Entwicklerportal

1. Wechseln Sie zum **Entwicklerportal** in Teams.

1. Öffnen Sie **Apps** , und wählen Sie **"App importieren**" aus.

1. Der Name Ihres App-Pakets lautet **tab.zip**. Es ist im folgenden Pfad verfügbar:

    ```
    /bin/Debug/netcoreapp3.1/tab.zip
    ```

1. Wählen Sie **tab.zip** aus, und öffnen Sie es im Entwicklerportal.

1. Im Abschnitt "**Grundlegende Informationen**" wird eine **Standard-App-ID** erstellt und ausgefüllt.

1. Fügen Sie die Kurz- und Langbeschreibung für Ihre App in **"Beschreibungen" hinzu**.

1. Fügen Sie in den **Entwicklerinformationen** die erforderlichen Details hinzu, und geben Sie ihrer ngrok **HTTPS-URL auf der Website (muss eine gültige HTTPS-URL sein).**

1. Aktualisieren Sie in **App-URLs** die Datenschutzrichtlinie `https://<yourngrokurl>/privacy` und die Nutzungsbedingungen, `https://<yourngrokurl>/tou` und speichern Sie sie.

1. Wählen Sie in **app-Features** persönliche App aus, geben Sie den Namen ein, und aktualisieren **Sie die Inhalts-URL** mit `https://<yourngrokurl>/personalTab`. Lassen Sie das Feld "Website-URL" leer.

1. Klicken Sie auf **Speichern**.

1. Im Abschnitt "Domänen" müssen Domänen von Ihren Registerkarten Ihre ngrok-URL ohne das HTTPS-Präfix `<yourngrokurl>.ngrok.io`enthalten.

### <a name="preview-your-app-in-teams"></a>Anzeigen einer Vorschau Ihrer App in Teams

1. Wählen Sie in Teams auf der Symbolleiste des Entwicklerportals die Option **"Vorschau**" aus. Das Entwicklerportal informiert Sie darüber, dass Ihre App erfolgreich quergeladen wurde.

1. Wählen Sie **"Apps verwalten" aus**. Ihre App ist in den quergeladenen Apps aufgeführt.

1. Suchen Sie Ihre App mithilfe der Suche, und wählen Sie die drei Punkte in der Zeile aus.

1. Wählen Sie die Option **"Anzeigen** " aus. Die Seite **"Hinzufügen"** wird für Ihre App angezeigt.

1. Wählen Sie **"Hinzufügen**" aus, um die Registerkarte auf Teams zu laden. Ihre Registerkarte ist jetzt in Teams verfügbar.

    :::image type="content" source="~/assets/images/tab-images/personaltabaspnetuploaded.png" alt-text="Standardregisterkarte" border="true":::

   Jetzt haben Sie erfolgreich Ihre persönliche Registerkarte in Teams erstellt und hinzugefügt.
  
   Da Sie Ihre persönliche Registerkarte in Teams haben, können Sie auch die API für Ihre persönliche Registerkarte [neu anordnen](#reorder-static-personal-tabs) und hinzufügen[`registerOnFocused`](#add-registeronfocused-api-for-tabs-or-personal-apps).

::: zone-end

::: zone pivot="mvc-csharp"

## <a name="create-a-personal-tab-with-aspnet-core-mvc"></a>Erstellen einer persönlichen Registerkarte mit ASP.NET Core MVC

Sie können eine benutzerdefinierte persönliche Registerkarte mit C# und ASP.NET Core MVC erstellen. So erstellen Sie eine persönliche Registerkarte mit ASP.NET Core MVC

1. Erstellen Sie an der Eingabeaufforderung ein neues Verzeichnis für Ihr Registerkartenprojekt.

1. Klonen Sie das Beispiel-Repository mit dem folgenden Befehl in Ihr neues Verzeichnis, oder Sie können den [Quellcode](https://github.com/OfficeDev/Microsoft-Teams-Samples) herunterladen und die Dateien extrahieren:

    ```cmd
    git clone https://github.com/OfficeDev/Microsoft-Teams-Samples.git
    ```

Führen Sie die folgenden Schritte zum Erstellen einer persönlichen Registerkarte aus:

1. [Generieren Ihrer Anwendung mit einer persönlichen Registerkarte](#generate-your-application-with-a-personal-tab-2)
1. [Aktualisieren und Ausführen der Anwendung](#update-and-run-your-application-1)
1. [Einrichten eines sicheren Tunnels zu Ihrer Registerkarte](#establish-a-secure-tunnel-to-your-tab-2)
1. [Aktualisieren Des App-Pakets mit dem Entwicklerportal](#update-your-app-package-with-developer-portal-1)
1. [Anzeigen einer Vorschau Ihrer App in Teams](#preview-your-app-in-teams-1)

### <a name="generate-your-application-with-a-personal-tab"></a>Generieren Ihrer Anwendung mit einer persönlichen Registerkarte

1. Öffnen Sie Visual Studio, und wählen Sie **"Projekt oder Projektmappe öffnen**" aus.

1. Wechseln Sie zum Ordner "Microsoft-Teams-Samplessamplestab-personalmvc-csharp >  >  > ", und öffnen Sie **"PersonalTabMVC.sln**" in Visual Studio.

1. Wählen Sie in Visual Studio **F5** aus, oder wählen Sie im **Menü "Debuggen**" der Anwendung die Option **"Debuggen starten**" aus, um zu überprüfen, ob die Anwendung ordnungsgemäß geladen wurde. Wechseln Sie in einem Browser zu den folgenden URLs:

    * <http://localhost:3978>
    * <http://localhost:3978/personalTab>
    * <http://localhost:3978/privacy>
    * <http://localhost:3978/tou>

<details>
<summary><b>Überprüfen des Quellcodes</b></summary>

#### <a name="startupcs"></a>Startup.cs

Dieses Projekt wurde aus einer leeren Vorlage ASP.NET Core 3.1-Webanwendung erstellt, wobei das Kontrollkästchen **"Erweitert – Für HTTPS konfigurieren**" beim Setup aktiviert ist. Die MVC-Dienste werden durch die Methode des Abhängigkeitsinjektionsframeworks `ConfigureServices()` registriert. Darüber hinaus ermöglicht die leere Vorlage nicht standardmäßig die Bereitstellung statischer Inhalte, sodass die Middleware für statische Dateien der Methode mit dem folgenden Code hinzugefügt `Configure()` wird:

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

#### <a name="wwwroot-folder"></a>Wwwroot-Ordner

In ASP.NET Core sucht die Anwendung im Webstammordner nach statischen Dateien.

#### <a name="appmanifest-folder"></a>AppManifest-Ordner

Dieser Ordner enthält die folgenden erforderlichen App-Paketdateien:

* Ein **Vollfarbsymbol** mit einer Auflösung von 192 x 192 Pixeln.
* Ein **transparentes Gliederungssymbol** mit einer Auflösung von 32 x 32 Pixeln.
* Eine **Manifest.json-Datei** , die die Attribute Ihrer App angibt.

Diese Dateien müssen in einem App-Paket gezippt werden, um Ihre Registerkarte in Teams hochzuladen. Microsoft Teams das `contentUrl` angegebene Element in Ihrem Manifest lädt, es in einen IFrame einbettet und auf der Registerkarte rendert.

#### <a name="csproj"></a>CSPROJ

Klicken Sie im Visual Studio Projektmappen-Explorer mit der rechten Maustaste auf das Projekt, und wählen Sie **"Project Datei bearbeiten**" aus. Am Ende der Datei wird der folgende Code angezeigt, der Ihren ZIP-Ordner erstellt und aktualisiert, wenn die Anwendung erstellt wird:

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

#### <a name="models"></a>Modelle

**PersonalTab.cs** stellt ein Nachrichtenobjekt und Methoden dar, die von **PersonalTabController** aufgerufen werden, wenn ein Benutzer eine Schaltfläche in der **PersonalTab-Ansicht auswählt** .

#### <a name="views"></a>Ansichten

Diese Ansichten sind die verschiedenen Ansichten in ASP.NET Core MVC:

* Start: ASP.NET Core behandelt Dateien mit dem Namen **Index** als Standard- oder Startseite für die Website. Wenn Ihre Browser-URL auf den Stamm der Website zeigt, wird **Index.cshtml** als Startseite für Ihre Anwendung angezeigt.

* Freigegeben: Das Partielle Ansichtsmarkup **_Layout.cshtml** enthält die allgemeine Seitenstruktur der Anwendung und freigegebene visuelle Elemente. Außerdem wird auf die Teams Bibliothek verwiesen.

#### <a name="controllers"></a>Controller

Die Controller verwenden die `ViewBag` Eigenschaft, um Werte dynamisch in die Ansichten zu übertragen.

</details>

### <a name="update-and-run-your-application"></a>Aktualisieren und Ausführen der Anwendung

1. Wechseln Sie zum Ordner **"****ViewsShared** > ", öffnen Sie **_Layout.cshtml**, und fügen Sie dem `<head>` Tags-Abschnitt Folgendes hinzu:

    ```HTML
    <script src="https://ajax.aspnetcdn.com/ajax/jQuery/jquery-3.4.1.min.js"></script>
    <script src="https://statics.teams.cdn.office.net/sdk/v1.6.0/js/MicrosoftTeams.min.js"></script>
    ```

1. Öffnen Sie **"PersonalTab.cshtml**" im Ordner **"ViewsPersonalTab** > **",** fügen Sie sie in die `<script>` Tags ein`microsoftTeams.initialize()`, und speichern Sie sie.

1. Wählen Sie in Visual Studio **F5** aus, oder wählen Sie im **Menü "Debuggen**" der Anwendung die Option **"Debuggen starten**" aus.

### <a name="establish-a-secure-tunnel-to-your-tab"></a>Einrichten eines sicheren Tunnels zu Ihrer Registerkarte

Führen Sie an der Eingabeaufforderung im Stammverzeichnis des Projekts den folgenden Befehl aus, um einen sicheren Tunnel zu Ihrer Registerkarte einzurichten:

```cmd
ngrok http 3978 --host-header=localhost
```

### <a name="update-your-app-package-with-developer-portal"></a>Aktualisieren Des App-Pakets mit dem Entwicklerportal

1. Wechseln Sie zum **Entwicklerportal** in Teams.

1. Öffnen Sie **Apps** , und wählen Sie **"App importieren**" aus.

1. Der Name Ihres App-Pakets lautet **tab.zip**. Es ist im folgenden Pfad verfügbar:

    ```
    /bin/Debug/netcoreapp3.1/tab.zip
    ```

1. Wählen Sie **tab.zip** aus, und öffnen Sie es im Entwicklerportal.

1. Im Abschnitt "**Grundlegende Informationen**" wird eine **Standard-App-ID** erstellt und ausgefüllt.

1. Fügen Sie die Kurz- und Langbeschreibung für Ihre App in **"Beschreibungen" hinzu**.

1. Fügen Sie in den **Entwicklerinformationen** die erforderlichen Details hinzu, und geben Sie ihrer ngrok **HTTPS-URL auf der Website (muss eine gültige HTTPS-URL sein).**

1. Aktualisieren Sie in **App-URLs** die Datenschutzrichtlinie `https://<yourngrokurl>/privacy` und die Nutzungsbedingungen, `https://<yourngrokurl>/tou` und speichern Sie sie.

1. Wählen Sie in **app-Features** persönliche App aus, geben Sie den Namen ein, und aktualisieren **Sie die Inhalts-URL** mit `https://<yourngrokurl>/personalTab`. Lassen Sie das Feld "Website-URL" leer.

1. Klicken Sie auf **Speichern**.

1. Im Abschnitt "Domänen" müssen Domänen von Ihren Registerkarten Ihre ngrok-URL ohne das HTTPS-Präfix `<yourngrokurl>.ngrok.io`enthalten.

### <a name="preview-your-app-in-teams"></a>Anzeigen einer Vorschau Ihrer App in Teams

1. Wählen Sie in Teams auf der Symbolleiste des Entwicklerportals die Option **"Vorschau**" aus. Das Entwicklerportal informiert Sie darüber, dass Ihre App erfolgreich quergeladen wurde.

1. Wählen Sie **"Apps verwalten" aus**. Ihre App ist in den quergeladenen Apps aufgeführt.

1. Suchen Sie Ihre App mithilfe der Suche, und wählen Sie die drei Punkte in der Zeile aus.

1. Wählen Sie die Option **"Anzeigen** " aus. Die Seite **"Hinzufügen"** wird für Ihre App angezeigt.

1. Wählen Sie **"Hinzufügen**" aus, um die Registerkarte auf Teams zu laden. Ihre Registerkarte ist jetzt in Teams verfügbar.

    :::image type="content" source="~/assets/images/tab-images/personaltabaspnetmvccoreuploaded.png" alt-text="Registerkarte „Persönlich“" border="true":::
  
   Jetzt haben Sie erfolgreich Ihre persönliche Registerkarte in Teams erstellt und hinzugefügt.

   Da Sie Ihre persönliche Registerkarte in Teams haben, können Sie auch die API für Ihre persönliche Registerkarte [neu anordnen](#reorder-static-personal-tabs) und hinzufügen[`registerOnFocused`](#add-registeronfocused-api-for-tabs-or-personal-apps).

::: zone-end

## <a name="reorder-static-personal-tabs"></a>Neu anordnen statischer persönlicher Registerkarten

Ab Manifestversion 1.7 können Entwickler alle Registerkarten in ihrer persönlichen App neu anordnen. Insbesondere kann ein Entwickler die **Registerkarte "Bot-Chat** ", die standardmäßig immer an die erste Position festgelegt ist, an eine beliebige Stelle in der Kopfzeile der persönlichen App-Registerkarte verschieben. Es werden zwei reservierte Registerkartenschlüsselwörter `entityId` deklariert, **Unterhaltungen** und **Informationen**.

Wenn Sie einen Bot mit einem **persönlichen** Bereich erstellen, wird er standardmäßig an der ersten Registerkartenposition in einer persönlichen App angezeigt. Wenn Sie es an eine andere Position verschieben möchten, müssen Sie Ihrem Manifest ein statisches Registerkartenobjekt mit dem **reservierten Schlüsselwort Unterhaltungen** hinzufügen. Die **Registerkarte "Unterhaltung** " wird im Web oder Desktop angezeigt, je nachdem, wo Sie die **Unterhaltungsregisterkarte** im `staticTabs` Array hinzufügen.

``` JSON

{
   "staticTabs":[
      {
         
      },
      {
         "entityId":"conversations",
         "scopes":[
            "personal"
         ]
      }
   ]
}

```

## <a name="add-registeronfocused-api-for-tabs-or-personal-apps"></a>Hinzufügen einer `registerOnFocused` API für Registerkarten oder persönliche Apps

Mit `registerOnFocused` der SDK-API können Sie eine Tastatur auf Teams verwenden. Sie können zu einer persönlichen App zurückkehren und den Fokus auf einer Registerkarte oder einer persönlichen App mithilfe der Tasten STRG, UMSCHALT UND F6 behalten. Sie können sich beispielsweise von der persönlichen App entfernen, um nach etwas zu suchen, und dann zur persönlichen App zurückkehren oder STRG+F6 verwenden, um die erforderlichen Stellen zu umgehen.

Der folgende Code enthält ein Beispiel für eine Handlerdefinition im `registerFocusEnterHandler` SDK, wenn der Fokus auf die Registerkarte oder die persönliche App zurückgegeben werden muss:

``` C#

export function registerFocusEnterHandler(handler: (navigateForward: boolean) => void): 
void {
  HandlersPrivate.focusEnterHandler = handler;
  handler && sendMessageToParent('registerHandler', ['focusEnter']);
}
function handleFocusEnter(navigateForward: boolean): void
 {
  if (HandlersPrivate.focusEnterHandler)
   {
    HandlersPrivate.focusEnterHandler(navigateForward);
  }
}

```

Nachdem der Handler mit dem Schlüsselwort `focusEnter`ausgelöst wurde, wird der Handler `registerFocusEnterHandler` mit einer Rückruffunktion `focusEnterHandler` aufgerufen, die einen aufgerufenen `navigateForward`Parameter akzeptiert. Der Wert von `navigateForward` bestimmt den Ereignistyp. Sie `focusEnterHandler` wird nur durch STRG+F6 und nicht durch die Tabulatortaste aufgerufen.
Folgende Schlüssel sind für das Verschieben von Ereignissen innerhalb Teams hilfreich:

* Forward-Ereignis: STRG+F6-TASTEN
* Backward-Ereignis: STRG+UMSCHALT+F6-TASTE

``` C#

case 'focusEnter':     
this.registerFocusEnterHandler((navigateForward: boolean = true) => {
this.sdkWindowMessageHandler.sendRequestMessage(this.frame, this.constants.SdkMessageTypes.focusEnter, [navigateForward]);
// Set focus on iframe or webview
if (this.frame && this.frame.sourceElem) {
  this.frame.sourceElem.focus();
}
return true;
});
}

// callback function to be passed to the handler
private focusEnterHandler: (navigateForward: boolean) => boolean;

// function that gets invoked after handler is registered.
private registerFocusEnterHandler(focusEnterHandler: (navigateForward: boolean) => boolean): void {
this.focusEnterHandler = focusEnterHandler;
this.layoutService.registerAppFocusEnterCallback(this.focusEnterHandler);
}

```

### <a name="personal-app"></a>Persönliche App

:::image type="content" source="../../assets/images/personal-apps/registerfocus.png" alt-text="Beispiel zeigt Optionen zum Hinzufügen der registerOnFocussed-API" border="true":::

#### <a name="personal-app-forward-event"></a>Persönliche App: Weiterleitungsereignis

:::image type="content" source="../../assets/images/personal-apps/registerfocus-forward-event.png" alt-text="Beispiel zeigt Optionen zum Hinzufügen von registerOnFocussed-API-Vorwärtsbewegung" border="true":::

#### <a name="personal-app-backward-event"></a>Persönliche App: Backward-Ereignis

:::image type="content" source="../../assets/images/personal-apps/registerfocus-backward-event.png" alt-text="Beispiel zeigt Optionen zum Hinzufügen der registerOnFocussed-API für die Rückwärtsbewegung" border="true":::

### <a name="tab"></a>Registerkarte

:::image type="content" source="../../assets/images/personal-apps/registerfocus-tab.png" alt-text="Beispiel zeigt Optionen zum Hinzufügen der registerOnFocussed-API für Registerkarten" border="true":::

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Erstellen einer Kanal- oder Gruppenregisterkarte](~/tabs/how-to/create-channel-group-tab.md)

## <a name="see-also"></a>Weitere Informationen

* [registerkarten Teams](~/tabs/what-are-tabs.md)
* [Registerkarten auf mobilen Geräten](~/tabs/design/tabs-mobile.md)
* [Erstellen von Registerkarten mit adaptiven Karten](~/tabs/how-to/build-adaptive-card-tabs.md)
* [Registerkarten für Unterhaltungen erstellen](~/tabs/how-to/conversational-tabs.md)
