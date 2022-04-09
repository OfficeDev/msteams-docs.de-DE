---
title: Erstellen einer persönlichen Registerkarte
author: laujan
description: Eine Schnellstartanleitung zum Erstellen einer persönlichen Registerkarte mit dem Yeoman-Generator, ASP.NET Core oder ASP.NET Core MVC für Microsoft Teams mithilfe von Node.js und Aktualisieren des App-Manifests.
ms.localizationpriority: medium
ms.topic: quickstart
ms.author: lajanuar
keywords: Yeoman ASP.NET MVC-Paket-Appmanifest-Domänenberechtigungsspeicher für Unterhaltungen
zone_pivot_groups: teams-app-environment
ms.openlocfilehash: 40afdd1692b0f5d7c99eaaf228969ba8c95ba20b
ms.sourcegitcommit: 61003a14e8a179e1268bbdbd9cf5e904c5259566
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2022
ms.locfileid: "64737212"
---
# <a name="create-a-personal-tab"></a>Erstellen einer persönlichen Registerkarte

Persönliche Registerkarten sind zusammen mit auf eine Person bezogene Bots Bestandteil persönlicher Apps und sind auf einen einzelnen Benutzer beschränkt. Sie können an den linken Bereich angeheftet werden, um einfach darauf zugreifen zu können. Sie können auch die API für persönliche Registerkarten [neu anordnen](#reorder-static-personal-tabs) und hinzufügen[`registerOnFocused`](#add-registeronfocused-api-for-tabs-or-personal-apps).

Stellen Sie sicher, dass Sie über alle [Prerequsites](~/tabs/how-to/tab-requirements.md) zum Erstellen Ihrer persönlichen Registerkarte verfügen.

::: zone pivot="node-java-script"

## <a name="create-a-personal-tab-with-nodejs"></a>Erstellen einer persönlichen Registerkarte mit Node.js

1. Installieren Sie an der Eingabeaufforderung die [Yeoman](https://yeoman.io/) - und [gulp-cli-Pakete](https://www.npmjs.com/package/gulp-cli) , indem Sie nach der Installation des Node.js den folgenden Befehl eingeben:

    ```cmd
    npm install yo gulp-cli --global
    ```

1. Installieren Sie an der Eingabeaufforderung Microsoft Teams App-Generator, indem Sie den folgenden Befehl eingeben:

    ```cmd
    npm install generator-teams --global
    ```

Im Folgenden sind die Schritte zum Erstellen einer persönlichen Registerkarte aufgeführt:

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

1. Stellen Sie Ihre Werte für eine Reihe von Fragen bereit, die Microsoft Teams App-Generator zum Aktualisieren Der `manifest.json` Datei auffordert.

    :::image type="content" source="~/assets/images/tab-images/teamsTabScreenshot.PNG" alt-text="Teams-Generator" border="true":::

    <details>
    <summary><b>Reihe von Fragen zum Aktualisieren der Datei "manifest.json"</b></summary>

    * **Wie lautet der Name Ihrer Lösung?**

      Der Projektmappenname ist Ihr Projektname. Sie können den vorgeschlagenen Namen annehmen, indem **Sie die EINGABETASTE drücken**.

    * **Wohin möchten Sie die Daten verschieben?**

      Sie befinden sich derzeit in Ihrem Projektverzeichnis. Wählen Sie **die EINGABETASTE** aus.

    * **Titel Ihres Microsoft Teams App-Projekts?**

      Der Titel ist der Name Ihres App-Pakets und wird im App-Manifest und in der Beschreibung verwendet. Geben Sie einen Titel ein, oder drücken **Sie die EINGABETASTE** , um den Standardnamen zu übernehmen.

    * **Ihr (Firmen-)Name? (max. 32 Zeichen)**

      Ihr Firmenname wird im App-Manifest verwendet. Geben Sie einen Firmennamen ein, oder drücken **Sie die EINGABETASTE** , um den Standardnamen zu übernehmen.

    * **Welche Manifestversion möchten Sie verwenden?**

      Wählen Sie das Standardschema aus.

    * **Schnelles Gerüst? (Y/n)**

      Der Standardwert ist "ja". geben Sie **n** ein, um Ihre Microsoft Partner-ID einzugeben.

    * **Geben Sie Ihre Microsoft-Partner-ID ein, wenn Sie über eine verfügen? (Leer lassen, um zu überspringen)**

      Dieses Feld ist nicht erforderlich und darf nur verwendet werden, wenn Sie bereits Teil des [Microsoft Partner Network](https://partner.microsoft.com) sind.

    * **Was möchten Sie Ihrem Projekt hinzufügen?**

      Wählen Sie **( &ast; ) eine Registerkarte** aus.

    * **Die URL, unter der Sie diese Lösung hosten werden?**

      Standardmäßig schlägt der Generator eine Azure-Websites-URL vor. Sie testen Ihre App nur lokal, daher ist keine gültige URL erforderlich.

    * **Möchten Sie eine Ladeanzeige anzeigen, wenn Ihre App/Registerkarte geladen wird?**

      Wählen Sie aus, dass beim Laden Ihrer App oder Registerkarte **keine** Ladeanzeige eingeschlossen werden soll. Der Standardwert ist "nein", geben Sie **"n"** ein.

    * **Möchten Sie, dass persönliche Apps ohne eine Registerkarten-Kopfleiste dargestellt werden?**

      Wählen Sie **aus, dass keine** persönlichen Apps einbezogen werden sollen, die ohne Eine Registerkartenkopfleiste gerendert werden sollen. Der Standardwert ist "nein", geben Sie **"n**" ein.

    * **Möchten Sie das Testframework und erste Tests einbeziehen? (y/N)**

      Wählen Sie **aus, kein** Testframework für dieses Projekt einzuschließen. Der Standardwert ist "nein", geben Sie **"n"** ein.

    * **Möchten Sie die ESLint-Unterstützung einbeziehen? (y/N)**

      Wählen Sie aus, dass die ESLint-Unterstützung nicht einbezogen werden soll. Der Standardwert ist "nein", geben Sie **"n"** ein.

    * **Möchten Sie Azure Applications Insights für Telemetrie verwenden? (y/N)**

      Wählen Sie **aus, Azure-Anwendung Insights nicht** [einzuschließen](/azure/azure-monitor/app/app-insights-overview). Die Standardeinstellung ist "nein". geben Sie **"n**" ein.

    * **Standardregisterkartenname (max. 16 Zeichen)?**

      Benennen Sie Ihre Registerkarte. Dieser Registerkartenname wird im gesamten Projekt als Datei- oder URL-Pfadkomponente verwendet.

    * **Welche Art von Registerkarte möchten Sie erstellen?**

      Verwenden Sie die Pfeiltasten, um **Persönlich (statisch)** auszuwählen.

    * **Benötigen Sie Microsoft Azure Active Directory (Azure AD) Single Sign-On-Unterstützung für die Registerkarte?**

      Wählen Sie **aus, Azure AD** Single Sign-On-Unterstützung für die Registerkarte nicht einzuschließen. Der Standardwert ist "Ja", geben Sie **"n**" ein.

    </details>

### <a name="add-a-content-page-to-the-personal-tab"></a>Hinzufügen einer Inhaltsseite zur persönlichen Registerkarte

Erstellen Sie eine Inhaltsseite, und aktualisieren Sie die vorhandenen Dateien der persönlichen Registerkartenanwendung:

1. Erstellen Sie eine neue **personal.html-Datei** in Ihrem Visual Studio Code mit dem folgenden Markup:

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

1. Öffnen Sie `manifest.json` in Ihrem Visual Studio Code den folgenden Speicherort:

    ```
     ./src/manifest/manifest.json
    ```

1. Fügen Sie Dem leeren `staticTabs` Array (`staticTabs":[]`) Folgendes hinzu, und fügen Sie das folgende JSON-Objekt hinzu:

    ```json
    {
        "entityId": "personalTab",
        "name": "Personal Tab ",
        "contentUrl": "https://{{PUBLIC_HOSTNAME}}/<yourDefaultTabNameTab>/personal.html",
        "websiteUrl": "https://{{PUBLIC_HOSTNAME}}",
        "scopes": ["personal"]
    }
    ```

    > [!IMPORTANT]
    > Die Pfadkomponente **"yourDefaultTabNameTab** " ist der Wert, den Sie im Generator für den **Standardregisterkartennamen** plus das Wort **Tab** eingegeben haben.
    >
    > Beispiel: "DefaultTabName" ist **"MyTab"** und " **/MyTabTab/"**

1. Aktualisieren Sie die **contentURL-Pfadkomponente** **"yourDefaultTabNameTab** " mit Ihrem tatsächlichen Registerkartennamen.

1. Speichern Sie die aktualisierte `manifest.json` Datei.

1. Öffnen Sie **Tab.ts** in Ihrem Visual Studio Code über den folgenden Pfad, um Die Inhaltsseite in einem IFrame bereitzustellen:

    ```bash
    ./src/server/<yourDefaultTabNameTab>/<yourDefaultTabNameTab>.ts
    ```

1. Fügen Sie Der Liste der IFrame-Dekorateure Folgendes hinzu:

    ```typescript
     @PreventIframe("/<yourDefaultTabName Tab>/personal.html")
    ```

1. Speichern Sie die aktualisierte Datei. Der Registerkartencode ist abgeschlossen.

### <a name="create-your-app-package"></a>Erstellen Ihres App-Pakets

Sie müssen über ein App-Paket verfügen, um Ihre Anwendung in Teams erstellen und ausführen zu können. Das App-Paket wird mithilfe einer gulp-Aufgabe erstellt, die die `manifest.json` Datei überprüft und den ZIP-Ordner im `./package` Verzeichnis generiert. Verwenden Sie an der Eingabeaufforderung den Befehl `gulp manifest`.

### <a name="build-and-run-your-application"></a>Erstellen und Ausführen der Anwendung

#### <a name="build-your-application"></a>Erstellen Ihrer Anwendung

Geben Sie an der Eingabeaufforderung den folgenden Befehl ein, um die Lösung in den Ordner **"./dist** " zu transpilieren:

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

### <a name="establish-a-secure-tunnel-to-your-tab"></a>Einrichten eines sicheren Tunnels auf Ihrer Registerkarte

Beenden Sie an der Eingabeaufforderung den localhost, und geben Sie den folgenden Befehl ein, um einen sicheren Tunnel zu Ihrer Registerkarte einzurichten:

```cmd
gulp ngrok-serve
```

> [!IMPORTANT]
> Nachdem Ihre Registerkarte über **ngrok** in Microsoft Teams hochgeladen und erfolgreich gespeichert wurde, können Sie sie in Teams anzeigen, bis Ihre Tunnelsitzung endet.

### <a name="upload-your-application-to-teams"></a>Hochladen Der Anwendung Teams

1. Wechseln Sie zu Microsoft Teams, und wählen Sie **"Apps**&nbsp; :::image type="content" source="~/assets/images/tab-images/store.png" alt-text="Teams Store&quot; aus":::.
1. Wählen Sie **"Apps verwalten"** und **Hochladen einer benutzerdefinierten App** aus.
1. Wechseln Sie zu Ihrem Projektverzeichnis, navigieren Sie zum Ordner **"./package** ", wählen Sie den ZIP-Ordner aus, und wählen Sie **"Öffnen**" aus.

    :::image type="content" source="~/assets/images/tab-images/addingpersonaltab.png" alt-text="Hinzufügen Ihrer persönlichen Registerkarte" border="true":::

1. Wählen Sie im Dialogfeld **"Hinzufügen"** aus. Ihre Registerkarte wird in Teams hochgeladen.

    :::image type="content" source="~/assets/images/tab-images/personaltabuploaded.png" alt-text="Persönliche Registerkarte hochgeladen" border="true":::

1. Wählen Sie im linken Bereich von Teams die Auslassungszeichen &#x25CF;&#x25CF;&#x25CF; aus, und wählen Sie dann Ihre hochgeladene App aus, um Ihre persönliche Registerkarte anzuzeigen.

   Jetzt haben Sie erfolgreich Ihre persönliche Registerkarte in Teams erstellt und hinzugefügt.
  
   Da Ihre persönliche Registerkarte in Teams ist, können Sie auch die API für Ihre persönliche Registerkarte [neu anordnen](#reorder-static-personal-tabs) und hinzufügen[`registerOnFocused`](#add-registeronfocused-api-for-tabs-or-personal-apps).

::: zone-end

::: zone pivot="razor-csharp"

## <a name="create-a-personal-tab-with-aspnet-core"></a>Erstellen einer persönlichen Registerkarte mit ASP.NET Core

1. Erstellen Sie an der Eingabeaufforderung ein neues Verzeichnis für Ihr Registerkartenprojekt.

1. Klonen Sie das Beispielrepository mithilfe des folgenden Befehls in Ihr neues Verzeichnis, oder Laden Sie den [Quellcode](https://github.com/OfficeDev/Microsoft-Teams-Samples) herunter, und extrahieren Sie die Dateien:

    ```cmd
    git clone https://github.com/OfficeDev/Microsoft-Teams-Samples.git
    ```

Im Folgenden sind die Schritte zum Erstellen einer persönlichen Registerkarte aufgeführt:

1. [Generieren Ihrer Anwendung mit einer persönlichen Registerkarte](#generate-your-application-with-a-personal-tab-1)
1. [Aktualisieren und Ausführen der Anwendung](#update-and-run-your-application)
1. [Einrichten eines sicheren Tunnels auf Ihrer Registerkarte](#establish-a-secure-tunnel-to-your-tab-1)
1. [Aktualisieren Ihres App-Pakets mit dem Entwicklerportal](#update-your-app-package-with-developer-portal)
1. [Vorschau ihrer App in Teams](#preview-your-app-in-teams)

### <a name="generate-your-application-with-a-personal-tab"></a>Generieren Ihrer Anwendung mit einer persönlichen Registerkarte

1. Öffnen Sie Visual Studio, und wählen Sie **"Projekt oder Lösung öffnen" aus**.

1. Wechseln Sie zum Ordner "Microsoft-Teams-Samplessamplestab-personalrazor-csharp >  >  > ", und öffnen Sie **"PersonalTab.sln**".

1. Wählen Sie in Visual Studio **F5** aus, oder wählen Sie im Menü **"Debuggen**" der Anwendung die Option **"Debuggen starten**" aus, um zu überprüfen, ob die Anwendung ordnungsgemäß geladen wurde. Wechseln Sie in einem Browser zu den folgenden URLs:

    * <http://localhost:3978/>
    * <http://localhost:3978/personalTab>
    * <http://localhost:3978/privacy>
    * <http://localhost:3978/tou>

<details>
<summary><b>Überprüfen des Quellcodes</b></summary>

#### <a name="startupcs"></a>Startup.cs

Dieses Projekt wurde aus einer leeren Vorlage für ASP.NET Core 3.1-Webanwendung erstellt, wobei das Kontrollkästchen **"Erweitert – Für HTTPS konfigurieren**" beim Setup aktiviert ist. Die MVC-Dienste werden von der Methode des Abhängigkeitsinjektionsframeworks `ConfigureServices()` registriert. Darüber hinaus ermöglicht die leere Vorlage nicht standardmäßig die Bereitstellung statischer Inhalte. Daher wird die Middleware für statische Dateien der `Configure()` Methode mit dem folgenden Code hinzugefügt:

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

#### <a name="wwwroot-folder"></a>Ordner "wwwroot"

In ASP.NET Core sucht die Anwendung im Webstammordner nach statischen Dateien.

#### <a name="indexcshtml"></a>Index.cshtml

ASP.NET Core behandelt Dateien, die als **Index** bezeichnet werden, als Standard- oder Homepage für die Website. Wenn Ihre Browser-URL auf den Stamm der Website verweist, wird **Index.cshtml** als Startseite für Ihre Anwendung angezeigt.

#### <a name="appmanifest-folder"></a>AppManifest-Ordner

Dieser Ordner enthält die folgenden erforderlichen App-Paketdateien:

* Ein Vollfarbsymbol mit einer Abmessung von 192 x 192 Pixeln.
* Ein transparentes Gliederungssymbol mit einer Abmessung von 32 x 32 Pixeln.
* Eine `manifest.json` Datei, die die Attribute Ihrer App angibt.

Diese Dateien müssen in einem App-Paket gezippt werden, damit Sie Ihre Registerkarte in Teams hochladen können. Microsoft Teams lädt das `contentUrl` in Ihrem Manifest angegebene Element, bettet es in einen <iframe\> ein und rendert es auf der Registerkarte.

#### <a name="csproj"></a>.csproj

Klicken Sie in Visual Studio Projektmappen-Explorer mit der rechten Maustaste auf das Projekt, und wählen **Sie "Project Datei bearbeiten**" aus. Am Ende der Datei sehen Sie den folgenden Code, der Ihren ZIP-Ordner erstellt und aktualisiert, wenn die Anwendung erstellt wird:

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

1. Öffnen Sie Visual Studio Projektmappen-Explorer, wechseln Sie zum Ordner **"****PagesShared** > ", öffnen Sie **_Layout.cshtml**, und fügen Sie Dem `<head>` Tags-Abschnitt Folgendes hinzu:

    ```HTML
    <script src="https://ajax.aspnetcdn.com/ajax/jQuery/jquery-3.4.1.min.js"></script>
    <script src="https://statics.teams.cdn.office.net/sdk/v1.6.0/js/MicrosoftTeams.min.js"></script>
    ```

1. Öffnen Sie in Visual Studio Projektmappen-Explorer **"PersonalTab.cshtml**" aus dem Ordner **"Pages**", fügen Sie die `<script>` Tags hinzu`microsoftTeams.initialize()`, und speichern Sie sie.

1. Wählen Sie in Visual Studio **F5** aus, oder wählen Sie im Menü **"Debuggen**" Der Anwendung die Option **"Debuggen starten**" aus.

### <a name="establish-a-secure-tunnel-to-your-tab"></a>Einrichten eines sicheren Tunnels auf Ihrer Registerkarte

Führen Sie an der Eingabeaufforderung im Stammverzeichnis ihres Projektverzeichnisses den folgenden Befehl aus, um einen sicheren Tunnel auf Ihrer Registerkarte einzurichten:

```cmd
ngrok http 3978 --host-header=localhost
```

### <a name="update-your-app-package-with-developer-portal"></a>Aktualisieren Ihres App-Pakets mit dem Entwicklerportal

1. Wechseln Sie zum [**Entwicklerportal**](https://dev.teams.microsoft.com/home).

1. Öffnen Sie **Apps** , und wählen Sie **"App importieren**" aus.

1. Der Dateiname des App-Pakets ist `tab.zip` und ist im `/bin/Debug/netcoreapp3.1/tab.zip` Pfad verfügbar.

1. Wählen Sie sie aus, und öffnen Sie `tab.zip` sie im Entwicklerportal.

1. Eine **Standard-App-ID** wird im Abschnitt **"Grundlegende Informationen** " erstellt und aufgefüllt.

1. Fügen Sie die kurz- und lange Beschreibung für Ihre App in **"Beschreibungen" hinzu**.

1. Fügen Sie in **den Entwicklerinformationen** die erforderlichen Details hinzu, und geben Sie auf der **Website (muss eine gültige HTTPS-URL sein)** Ihre ngrok HTTPS-URL an.

1. Aktualisieren Sie in **App-URLs** die Datenschutzrichtlinie und `https://<yourngrokurl>/privacy` die Nutzungsbedingungen, um sie zu `https://<yourngrokurl>/tou` speichern.

1. Wählen Sie in **app-Features** **persönliche appErstellen** >  **Sie Ihre erste persönliche App-Registerkarte** aus, geben Sie den Namen ein, und aktualisieren Sie die **Inhalts-URL** mit `https://<yourngrokurl>/personalTab`. Lassen Sie das Feld "Website-URL" leer, und wählen Sie **"Kontext** als persönliche Registerkarte" aus der Dropdownliste und **"Hinzufügen"** aus.

1. Klicken Sie auf **Speichern**.

1. Im Abschnitt "Domänen" müssen Domänen von Ihren Registerkarten Ihre ngrok-URL ohne das HTTPS-Präfix `<yourngrokurl>.ngrok.io`enthalten.

### <a name="preview-your-app-in-teams"></a>Vorschau ihrer App in Teams

1. Wählen Sie **"Vorschau" in Teams** auf der Symbolleiste des Entwicklerportals aus. Das Entwicklerportal informiert Sie darüber, dass Ihre App erfolgreich quergeladen wurde. Die Seite **"Hinzufügen"** wird für Ihre App in Teams angezeigt.

1. Wählen Sie **"Hinzufügen"** aus, um die Registerkarte in Teams zu laden. Ihre Registerkarte ist jetzt in Teams verfügbar.

    :::image type="content" source="~/assets/images/tab-images/personaltabaspnetuploaded.png" alt-text="Standardregisterkarte" border="true":::

   Jetzt haben Sie erfolgreich Ihre persönliche Registerkarte in Teams erstellt und hinzugefügt.
  
   Da Ihre persönliche Registerkarte in Teams ist, können Sie auch die API für Ihre persönliche Registerkarte [neu anordnen](#reorder-static-personal-tabs) und hinzufügen[`registerOnFocused`](#add-registeronfocused-api-for-tabs-or-personal-apps).

::: zone-end

::: zone pivot="mvc-csharp"

## <a name="create-a-personal-tab-with-aspnet-core-mvc"></a>Erstellen einer persönlichen Registerkarte mit ASP.NET Core MVC

1. Erstellen Sie an der Eingabeaufforderung ein neues Verzeichnis für Ihr Registerkartenprojekt.

1. Klonen Sie das Beispielrepository mithilfe des folgenden Befehls in Ihr neues Verzeichnis, oder Laden Sie den [Quellcode](https://github.com/OfficeDev/Microsoft-Teams-Samples) herunter, und extrahieren Sie die Dateien:

    ```cmd
    git clone https://github.com/OfficeDev/Microsoft-Teams-Samples.git
    ```

Im Folgenden sind die Schritte zum Erstellen einer persönlichen Registerkarte aufgeführt:

1. [Generieren Ihrer Anwendung mit einer persönlichen Registerkarte](#generate-your-application-with-a-personal-tab-2)
1. [Aktualisieren und Ausführen der Anwendung](#update-and-run-your-application-1)
1. [Einrichten eines sicheren Tunnels auf Ihrer Registerkarte](#establish-a-secure-tunnel-to-your-tab-2)
1. [Aktualisieren Ihres App-Pakets mit dem Entwicklerportal](#update-your-app-package-with-developer-portal-1)
1. [Vorschau ihrer App in Teams](#preview-your-app-in-teams-1)

### <a name="generate-your-application-with-a-personal-tab"></a>Generieren Ihrer Anwendung mit einer persönlichen Registerkarte

1. Öffnen Sie Visual Studio, und wählen Sie **"Projekt oder Lösung öffnen" aus**.

1. Wechseln Sie zum Ordner "Microsoft-Teams-Samplessamplestab-personalmvc-csharp >  >  > ", und öffnen **Sie "PersonalTabMVC.sln"** in Visual Studio.

1. Wählen Sie in Visual Studio **F5** aus, oder wählen Sie im Menü **"Debuggen**" der Anwendung die Option **"Debuggen starten**" aus, um zu überprüfen, ob die Anwendung ordnungsgemäß geladen wurde. Wechseln Sie in einem Browser zu den folgenden URLs:

    * <http://localhost:3978>
    * <http://localhost:3978/personalTab>
    * <http://localhost:3978/privacy>
    * <http://localhost:3978/tou>

<details>
<summary><b>Überprüfen des Quellcodes</b></summary>

#### <a name="startupcs"></a>Startup.cs

Dieses Projekt wurde aus einer leeren Vorlage für ASP.NET Core 3.1-Webanwendung erstellt, wobei das Kontrollkästchen **"Erweitert – Für HTTPS konfigurieren**" beim Setup aktiviert ist. Die MVC-Dienste werden von der Methode des Abhängigkeitsinjektionsframeworks `ConfigureServices()` registriert. Darüber hinaus ermöglicht die leere Vorlage nicht standardmäßig die Bereitstellung statischer Inhalte. Daher wird die Middleware für statische Dateien der `Configure()` Methode mit dem folgenden Code hinzugefügt:

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

#### <a name="wwwroot-folder"></a>Ordner "wwwroot"

In ASP.NET Core sucht die Anwendung im Webstammordner nach statischen Dateien.

#### <a name="appmanifest-folder"></a>AppManifest-Ordner

Dieser Ordner enthält die folgenden erforderlichen App-Paketdateien:

* Ein **Vollfarbsymbol** mit einer Abmessung von 192 x 192 Pixeln.
* Ein **transparentes Gliederungssymbol** mit einer Abmessung von 32 x 32 Pixeln.
* Eine `manifest.json` Datei, die die Attribute Ihrer App angibt.

Diese Dateien müssen in einem App-Paket gezippt werden, damit Sie Ihre Registerkarte in Teams hochladen können. Microsoft Teams lädt die `contentUrl` in Ihrem Manifest angegebene Datei, bettet sie in einen IFrame ein und rendert sie auf ihrer Registerkarte.

#### <a name="csproj"></a>.csproj

Klicken Sie im Visual Studio Projektmappen-Explorer mit der rechten Maustaste auf das Projekt, und wählen **Sie "Project Datei bearbeiten**" aus. Am Ende der Datei wird der folgende Code angezeigt, der Ihren ZIP-Ordner erstellt und aktualisiert, wenn die Anwendung erstellt wird:

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

**PersonalTab.cs** stellt ein Nachrichtenobjekt und Methoden dar, die von **PersonalTabController** aufgerufen werden, wenn ein Benutzer eine Schaltfläche in der **PersonalTab-Ansicht** auswählt.

#### <a name="views"></a>Ansichten

Diese Ansichten sind die verschiedenen Ansichten in ASP.NET Core MVC:

* Startseite: ASP.NET Core behandelt Dateien, die als **Index** bezeichnet werden, als Standard- oder Homepage für die Website. Wenn Ihre Browser-URL auf den Stamm der Website verweist, wird **Index.cshtml** als Startseite für Ihre Anwendung angezeigt.

* Freigegeben: Das Partielle Ansichtsmarkup **_Layout.cshtml** enthält die gesamte Seitenstruktur der Anwendung und freigegebene visuelle Elemente. Es verweist auch auf die Teams Library.

#### <a name="controllers"></a>Controller

Die Controller verwenden die `ViewBag` Eigenschaft, um Werte dynamisch in die Ansichten zu übertragen.

</details>

### <a name="update-and-run-your-application"></a>Aktualisieren und Ausführen der Anwendung

1. Öffnen Sie Visual Studio Projektmappen-Explorer, wechseln Sie zum Ordner **"****ViewsShared** > ", öffnen Sie **_Layout.cshtml**, und fügen Sie Dem `<head>` Tags-Abschnitt Folgendes hinzu:

    ```HTML
    <script src="https://ajax.aspnetcdn.com/ajax/jQuery/jquery-3.4.1.min.js"></script>
    <script src="https://statics.teams.cdn.office.net/sdk/v1.6.0/js/MicrosoftTeams.min.js"></script>
    ```

1. Öffnen Sie in Visual Studio Projektmappen-Explorer **PersonalTab.cshtml** aus dem Ordner **"****ViewsPersonalTab** > ", fügen Sie die `<script>` Tags hinzu`microsoftTeams.initialize()`, und speichern Sie sie.

1. Wählen Sie in Visual Studio **F5** aus, oder wählen Sie im Menü **"Debuggen**" Der Anwendung die Option **"Debuggen starten**" aus.

### <a name="establish-a-secure-tunnel-to-your-tab"></a>Einrichten eines sicheren Tunnels auf Ihrer Registerkarte

Führen Sie an der Eingabeaufforderung im Stammverzeichnis ihres Projektverzeichnisses den folgenden Befehl aus, um einen sicheren Tunnel auf Ihrer Registerkarte einzurichten:

```cmd
ngrok http 3978 --host-header=localhost
```

### <a name="update-your-app-package-with-developer-portal"></a>Aktualisieren Ihres App-Pakets mit dem Entwicklerportal

1. Wechseln Sie zum [**Entwicklerportal**](https://dev.teams.microsoft.com/home).

1. Öffnen Sie **Apps** , und wählen Sie **"App importieren**" aus.

1. Der Name Des App-Pakets ist **tab.zip**. Es ist im folgenden Pfad verfügbar:

    ```
    /bin/Debug/netcoreapp3.1/tab.zip
    ```

1. Wählen Sie **tab.zip** aus, und öffnen Sie es im Entwicklerportal.

1. Eine **Standard-App-ID** wird im Abschnitt **"Grundlegende Informationen** " erstellt und aufgefüllt.

1. Fügen Sie die kurz- und lange Beschreibung für Ihre App in **"Beschreibungen" hinzu**.

1. Fügen Sie in **den Entwicklerinformationen** die erforderlichen Details hinzu, und geben Sie auf der **Website (muss eine gültige HTTPS-URL sein)** Ihre ngrok HTTPS-URL an.

1. Aktualisieren Sie in **App-URLs** die Datenschutzrichtlinie und `https://<yourngrokurl>/privacy` die Nutzungsbedingungen, um sie zu `https://<yourngrokurl>/tou` speichern.

1. Wählen Sie in **app-Features** **persönliche appErstellen** >  **Sie Ihre erste persönliche App-Registerkarte** aus, geben Sie den Namen ein, und aktualisieren Sie die **Inhalts-URL** mit `https://<yourngrokurl>/personalTab`. Lassen Sie das Feld "Website-URL" leer, und wählen Sie **"Kontext** als persönliche Registerkarte" aus der Dropdownliste und **"Hinzufügen"** aus.

1. Klicken Sie auf **Speichern**.

1. Im Abschnitt "Domänen" müssen Domänen von Ihren Registerkarten Ihre ngrok-URL ohne das HTTPS-Präfix `<yourngrokurl>.ngrok.io`enthalten.

### <a name="preview-your-app-in-teams"></a>Vorschau ihrer App in Teams

1. Wählen Sie **"Vorschau" in Teams** auf der Symbolleiste des Entwicklerportals aus. Das Entwicklerportal informiert Sie darüber, dass Ihre App erfolgreich quergeladen wurde. Die Seite **"Hinzufügen"** wird für Ihre App in Teams angezeigt.

1. Wählen Sie **"Hinzufügen"** aus, um die Registerkarte auf Teams zu laden. Ihre Registerkarte ist jetzt in Teams verfügbar.

    :::image type="content" source="~/assets/images/tab-images/personaltabaspnetmvccoreuploaded.png" alt-text="Registerkarte „Persönlich“" border="true":::
  
   Jetzt haben Sie erfolgreich Ihre persönliche Registerkarte in Teams erstellt und hinzugefügt.

   Da Ihre persönliche Registerkarte in Teams ist, können Sie auch die API für Ihre persönliche Registerkarte [neu anordnen](#reorder-static-personal-tabs) und hinzufügen[`registerOnFocused`](#add-registeronfocused-api-for-tabs-or-personal-apps).

::: zone-end

## <a name="reorder-static-personal-tabs"></a>Neuanordnen statischer persönlicher Registerkarten

Ab Manifestversion 1.7 können Entwickler alle Registerkarten in ihrer persönlichen App neu anordnen. Insbesondere kann ein Entwickler die **Registerkarte "Bot-Chat** " an eine beliebige Stelle in der Kopfzeile der persönlichen App-Registerkarte verschieben, die immer auf die erste Position festgelegt ist. Zwei reservierte Registerkartenstichwörter `entityId` werden deklariert, **Unterhaltungen** und **weitere** Informationen.

Wenn Sie einen Bot mit einem **persönlichen** Bereich erstellen, wird er standardmäßig an der ersten Registerkartenposition in einer persönlichen App angezeigt. Wenn Sie es an eine andere Position verschieben möchten, müssen Sie ihrem Manifest ein statisches Registerkartenobjekt mit dem reservierten Schlüsselwort **Unterhaltungen** hinzufügen. Die Registerkarte " **Unterhaltung** " wird im Web oder desktop angezeigt, je nachdem, wo Sie die Registerkarte " **Unterhaltung** " im `staticTabs` Array hinzufügen.

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

## <a name="add-registeronfocused-api-for-tabs-or-personal-apps"></a>Hinzufügen `registerOnFocused` einer API für Registerkarten oder persönliche Apps

Mit `registerOnFocused` der SDK-API können Sie eine Tastatur auf Teams verwenden. Sie können zu einer persönlichen App zurückkehren und mithilfe von STRG, UMSCHALT und F6 den Fokus auf einer Registerkarte oder persönlichen App behalten. Sie können z. B. von der persönlichen App weggehen, um nach etwas zu suchen, und dann zur persönlichen App zurückkehren oder STRG+F6 verwenden, um die erforderlichen Stellen zu durchlaufen.

Der folgende Code enthält ein Beispiel für eine Handlerdefinition im `registerFocusEnterHandler` SDK, wenn der Fokus auf die Registerkarte oder persönliche App zurückgegeben werden muss:

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

Nachdem der Handler mit dem Schlüsselwort `focusEnter`ausgelöst wurde, wird der Handler `registerFocusEnterHandler` mit einer Rückruffunktion `focusEnterHandler` aufgerufen, die einen Parameter namens `navigateForward`übernimmt. Der Wert von `navigateForward` bestimmt den Ereignistyp. Dies `focusEnterHandler` wird nur durch STRG+F6 und nicht durch die TAB-TASTE aufgerufen.
Die folgenden Tasten sind für Verschiebungsereignisse innerhalb Teams hilfreich:

* Forward-Ereignis: STRG+F6-Tasten
* Backward-Ereignis: STRG+UMSCHALT+F6-Tasten

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

#### <a name="personal-app-forward-event"></a>Persönliche App: Forward-Ereignis

:::image type="content" source="../../assets/images/personal-apps/registerfocus-forward-event.png" alt-text="Beispiel zeigt Optionen zum Hinzufügen von registerOnFocussed-API-Vorwärtsverschiebung" border="true":::

#### <a name="personal-app-backward-event"></a>Persönliche App: Backward-Ereignis

:::image type="content" source="../../assets/images/personal-apps/registerfocus-backward-event.png" alt-text="Beispiel zeigt Optionen zum Hinzufügen der registerOnFocussed-API nach hinten" border="true":::

### <a name="tab"></a>Registerkarte

:::image type="content" source="../../assets/images/personal-apps/registerfocus-tab.png" alt-text="Beispiel zeigt Optionen zum Hinzufügen der registerOnFocussed-API für die Registerkarte" border="true":::

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Erstellen einer Kanal- oder Gruppenregisterkarte](~/tabs/how-to/create-channel-group-tab.md)

## <a name="see-also"></a>Siehe auch

* [Teams Registerkarten](~/tabs/what-are-tabs.md)
* [Registerkarten auf mobilen Geräten](~/tabs/design/tabs-mobile.md)
* [Erstellen von Registerkarten mit adaptiven Karten](~/tabs/how-to/build-adaptive-card-tabs.md)
* [Registerkarten für Unterhaltungen erstellen](~/tabs/how-to/conversational-tabs.md)
* [Für Teams über persönliche App oder Registerkarte freigeben](~/concepts/build-and-test/share-to-teams-from-personal-app-or-tab.md)
