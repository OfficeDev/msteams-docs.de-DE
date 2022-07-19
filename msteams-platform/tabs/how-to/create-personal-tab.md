---
title: Erstellen einer persönlichen Registerkarte
author: laujan
description: In diesem Modul erfahren Sie, wie Sie mithilfe von Node.js eine persönliche Registerkarte mit dem Yeoman-Generator, ASP.NET Core oder ASP.NET Core MVC für Microsoft Teams erstellen und das App-Manifest aktualisieren.
ms.localizationpriority: high
ms.topic: quickstart
ms.author: lajanuar
zone_pivot_groups: teams-app-environment
ms.openlocfilehash: dcc000c64068cbcbd24a03da365e799e9dd1c155
ms.sourcegitcommit: 79d525c0be309200e930cdd942bc2c753d0b718c
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 07/19/2022
ms.locfileid: "66841694"
---
# <a name="create-a-personal-tab"></a>Erstellen einer persönlichen Registerkarte

Persönliche Registerkarten sind zusammen mit auf eine Person bezogene Bots Bestandteil persönlicher Apps und sind auf einen einzelnen Benutzer beschränkt. Sie können an den linken Bereich angeheftet werden, um den Zugriff zu erleichtern. Sie können Ihre persönlichen Registerkarten auch [neu anordnen](#reorder-static-personal-tabs).

Stellen Sie sicher, dass all [Voraussetzungen](~/tabs/how-to/tab-requirements.md) erfüllt sind, um Ihre persönliche Registerkarte zu erstellen.

[!INCLUDE [sdk-include](~/includes/sdk-include.md)]

::: zone pivot="node-java-script"

## <a name="create-a-personal-tab-with-nodejs"></a>Erstellen einer persönlichen Registerkarte mit Node.js

1. Installieren Sie an der Eingabeaufforderung die Pakete [Yeoman](https://yeoman.io/) und [gulp-cli](https://www.npmjs.com/package/gulp-cli), indem Sie nach der Installation von Node.js den folgenden Befehl eingeben:

    ```cmd
    npm install yo gulp-cli --global
    ```

1. Installieren Sie an der Eingabeaufforderung den Microsoft Teams-App-Generator, indem Sie den folgenden Befehl eingeben:

    ```cmd
    npm install generator-teams --global
    ```

Im Folgenden finden Sie die Schritte zum Erstellen einer persönlichen Registerkarte:

1. [Generieren Ihrer Anwendung mit einer persönlichen Registerkarte](#generate-your-application-with-a-personal-tab)
1. [Hinzufügen einer Inhaltsseite zur persönlichen Registerkarte](#add-a-content-page-to-the-personal-tab)
1. [Erstellen Ihres App-Pakets](#create-your-app-package)
1. [Erstellen und Ausführen Ihre Anwendung](#build-and-run-your-application)
1. [Einrichten eines sicheren Tunnels zu Ihrer persönlichen Registerkarte](#establish-a-secure-tunnel-to-your-tab)
1. [Hochladen Ihrer Anwendung in Teams](#upload-your-application-to-teams)

### <a name="generate-your-application-with-a-personal-tab"></a>Generieren Ihrer Anwendung mit einer persönlichen Registerkarte

1. Erstellen Sie an der Eingabeaufforderung ein neues Verzeichnis für Ihre persönliche Registerkarte.

1. Geben Sie den folgenden Befehl in Ihr neues Verzeichnis ein, um den Microsoft Teams App-Generator zu starten:

    ```cmd
    yo teams
    ```

1. Geben Sie Ihre Werte für eine Reihe von Fragen an, die vom Microsoft Teams App-Generator gestellt werden, um Ihre `manifest.json`-Datei zu aktualisieren.

    :::image type="content" source="~/assets/images/tab-images/teamsTabScreenshot.PNG" alt-text="Teams-Generator":::

    <details>
    <summary><b>Reihe von Fragen zum Aktualisieren der Manifest.json-Datei</b></summary>

    * **Wie lautet der Name Ihrer Lösung?**

      Der Lösungsname ist Ihr Projektname. Sie können den vorgeschlagenen Namen annehmen, indem Sie die **EINGABETASTE** drücken.

    * **Wohin möchten Sie die Daten verschieben?**

      Sie befinden sich derzeit in Ihrem Projektverzeichnis. Drücken Sie die **EINGABETASTE**.

    * **Titel Ihres Microsoft Teams App-Projektes?**

      Der Titel ist der Name Ihres App-Pakets und wird im App-Manifest und in der Beschreibung verwendet. Geben Sie einen Titel ein, oder drücken Sie die **EINGABETASTE**, um den Standardnamen zu übernehmen.

    * **Ihr (Firmen)name? (max. 32 Zeichen)**

      Ihr Firmenname wird im App-Manifest verwendet. Geben Sie einen Firmennamen ein, oder drücken **Sie die EINGABETASTE**, um den Standardnamen zu übernehmen.

    * **Welche Manifestversion möchten Sie verwenden?**

      Wählen Sie das Standardschema aus.

    * **Schnelle Gerüsterstellung? (J/n)**

      Der Standardwert ist "ja". geben Sie **n** ein, um Ihre Microsoft Partner-ID einzugeben.

    * **Geben Sie Ihre Microsoft Partner-ID ein, sofern Sie über eine verfügen (zum Überspringen leer lassen).**

      Dieses Feld ist nicht erforderlich und darf nur verwendet werden, wenn Sie bereits Teil des [Microsoft Partner-Netzwerks](https://partner.microsoft.com) sind.

    * **Was möchten Sie zu Ihrem Projekt hinzufügen?**

      Wählen Sie **( &ast; ) Eine Registerkarte** aus.

    * **Die URL, unter der Sie diese Lösung hosten möchten?**: 

      Standardmäßig schlägt der Generator eine Azure-Website-URL vor. Sie testen Ihre App nur lokal, daher ist keine gültige URL erforderlich.

    * **Soll ein Ladeindikator angezeigt werden, während Ihre App/Registerkarte geladen wird?**

      Legen Sie fest, dass beim Laden Ihrer App oder Registerkarte **keine** Ladeanzeige eingeschlossen werden soll. Der Standardwert ist "nein", geben Sie "**n**" ein.

    * **Möchten Sie, dass persönliche Apps ohne eine Registerkarten-Kopfleiste dargestellt werden?**

      Legen Sie fest, **keine** persönliche Apps ohne Registerkarten-Kopfzeilenleiste dargestellt werden sollen. Der Standardwert ist "nein", geben Sie "**n**" ein.

    * **Möchten Sie ein Testframework und anfängliche Tests einschließen? (j/N)**

      Legen Sie fest, **kein** Testframework für dieses Projekt einzuschließen. Der Standardwert ist "nein", geben Sie "**n**" ein.

    * **Möchten Sie ESLint-Unterstützung einschließen? (y/N)**

      Legen Sie fest, keine ESLint-Unterstützung einzuschließen. Der Standardwert ist "nein", geben Sie "**n**" ein.

    * **Möchten Sie Azure Applications Insights für Telemetriedaten verwenden? (y/N)**

      Legen Sie fest, [Azure Application Insights](/azure/azure-monitor/app/app-insights-overview) **nicht** einzuschließen. Die Standardeinstellung ist "nein". geben Sie "**n**" ein.

    * **Standardregisterkartenname (max. 16 Zeichen)?**

      Benennen Sie Ihre Registerkarte. Dieser Registerkartenname wird im gesamten Projekt als eine Datei- oder URL-Pfadkomponente verwendet.

    * **Welche Art von Registerkarte möchten Sie erstellen?**

      Verwenden Sie die Pfeiltasten, um **Persönlich (statisch)** auszuwählen.

    * **Benötigen Sie Microsoft Azure Active Directory (Azure AD) SSO-Unterstützung für die Registerkarte?**

      Legen Sie fest, **keine** Azure AD SSO-Unterstützung für die Registerkarte einzuschließen. Der Standardwert ist „ja“, geben Sie **n** ein.

    </details>

### <a name="add-a-content-page-to-the-personal-tab"></a>Hinzufügen einer Inhaltsseite zur persönlichen Registerkarte

Erstellen Sie eine Inhaltsseite, und aktualisieren Sie die vorhandenen Dateien der persönlichen Registerkartenanwendung:

1. Erstellen Sie eine neue **personal.html**-Datei in Ihrem Visual Studio Code mit dem folgenden Markup:

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

1. Speichern Sie **personal.html** im Ordner **public** Ihrer Anwendung am folgenden Speicherort:

    ```
    ./src/public/<yourDefaultTabNameTab>/personal.html
    ```

1. Öffnen Sie `manifest.json` aus dem folgenden Speicherort in Ihrem Visual Studio Code:

    ```
     ./src/manifest/manifest.json
    ```

1. Fügen Sie dem leeren `staticTabs`-Array (`staticTabs":[]`) Folgendes hinzu, und fügen Sie das folgende JSON-Objekt hinzu:

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
    > Die Pfadkomponente **yourDefaultTabNameTab** ist der Wert, den Sie im Generator für **Standardregisterkartenname** eingegeben haben, plus das Wort **Tab**.
    >
    > Beispiel: DefaultTabName ist **MyTab** dann **/MyTabTab/**

1. Aktualisieren Sie die **contentURL**-Pfadkomponente **yourDefaultTabNameTabTab** mit Ihrem tatsächlichen Registerkartennamen.

1. Speichern Sie die aktualisierte `manifest.json`-Datei.

1. Öffnen Sie **Tab.ts** in Ihrem Visual Studio Code aus dem folgenden Pfad, um Ihre Inhaltsseite in einem IFrame bereitzustellen:

    ```bash
    ./src/server/<yourDefaultTabNameTab>/<yourDefaultTabNameTab>.ts
    ```

1. Fügen Sie der Liste der IFrame-Decorators Folgendes hinzu:

    ```typescript
     @PreventIframe("/<yourDefaultTabName Tab>/personal.html")
    ```

1. Speichern Sie die aktualisierte Datei. Ihr Registerkartencode ist vollständig.

### <a name="create-your-app-package"></a>Erstellen Ihres App-Pakets

Sie benötigen ein App-Paket, um Ihre Anwendung in Microsoft Teams erstellen und ausführen zu können. Das App-Paket wird über eine gulp-Aufgabe erstellt, welche die `manifest.json`-Datei überprüft und den ZIP-Ordner im Verzeichnis `./package` generiert. Verwenden Sie an der Eingabeaufforderung den Befehl `gulp manifest`.

### <a name="build-and-run-your-application"></a>Erstellen und Ausführen Ihrer Anwendung

#### <a name="build-your-application"></a>Erstellen Ihrer Anwendung

Geben Sie an der Eingabeaufforderung den folgenden Befehl ein, um Ihre Lösung in den Ordner **./dist** zu transpilieren (transkompilieren):

```cmd
gulp build
```

#### <a name="run-your-application"></a>Ausführen Ihrer Anwendung

1. Geben Sie an der Eingabeaufforderung den folgenden Befehl ein, um einen lokalen Webserver zu starten:

    ```cmd
    gulp serve
    ```

1. Geben Sie `http://localhost:3007/<yourDefaultAppNameTab>/` in Ihren Browser ein, um die Startseite Ihrer Anwendung anzuzeigen.

    :::image type="content" source="~/assets/images/tab-images/homePage.png" alt-text="Standardregisterkarte":::

1. Durchsuchen Sie `http://localhost:3007/<yourDefaultAppNameTab>/personal.html`, um Ihre persönliche Registerkarte anzuzeigen.

    :::image type="content" source="~/assets/images/tab-images/personalTab.PNG" alt-text="Standard HTML-Registerkarte":::

### <a name="establish-a-secure-tunnel-to-your-tab"></a>Einrichten eines sicheren Tunnels zu Ihrer Registerkarte

Beenden Sie an der Eingabeaufforderung den localhost, und geben Sie den folgenden Befehl ein, um einen sicheren Tunnel zu Ihrer Registerkarte einzurichten:

```cmd
gulp ngrok-serve
```

> [!IMPORTANT]
> Nachdem Ihre Registerkarte über **ngrok** in Microsoft Teams hochgeladen und erfolgreich gespeichert wurde, können Sie diese in Teams anzeigen, bis Ihre Tunnelsitzung endet.

### <a name="upload-your-application-to-teams"></a>Hochladen Ihrer Anwendung in Teams

1. Wechseln Sie zu Teams, und wählen Sie **Apps**&nbsp;:::image type="content" source="~/assets/images/tab-images/store.png" alt-text="Teams Store"::: aus.
1. Wählen Sie **Ihre Apps verwalten** und **Eine benutzerdefinierte App hochladen** aus.
1. Wechseln Sie zu Ihrem Projektverzeichnis, navigieren Sie zum Ordner **./package**, wählen Sie den ZIP-Ordner aus und dann **Öffnen**.

    :::image type="content" source="~/assets/images/tab-images/addingpersonaltab.png" alt-text="Hinzufügen Ihrer persönlichen Registerkarte":::

1. Wählen Sie **Hinzufügen** im Dialogfeld aus. Ihre Registerkarte wird in Teams hochgeladen.

    :::image type="content" source="~/assets/images/tab-images/personaltabuploaded.png" alt-text="Persönliche Registerkarte hochgeladen":::

1. Wählen Sie im linken Bereich von Teams die Auslassungspunkte &#x25CF;&#x25CF;&#x25CF; aus, und wählen Sie dann Ihre hochgeladene App aus, um Ihre persönliche Registerkarte anzuzeigen.

   Jetzt haben Sie Ihre persönliche Registerkarte erfolgreich erstellt und in Teams hinzugefügt.
  
   Da Sie ihre persönliche Registerkarte in Teams haben, können Sie Ihre persönlichen Registerkarte auch [neu anordnen](#reorder-static-personal-tabs).

::: zone-end

::: zone pivot="razor-csharp"

## <a name="create-a-personal-tab-with-aspnet-core"></a>Erstellen einer persönlichen Registerkarte mit ASP.NET Core

1. Erstellen Sie an der Eingabeaufforderung ein neues Verzeichnis für Ihr Registerkartenprojekt.

1. Klonen Sie das Beispielrepository mit dem folgenden Befehl in Ihr neues Verzeichnis, oder laden Sie den [Quellcode](https://github.com/OfficeDev/Microsoft-Teams-Samples) herunter, und extrahieren Sie die Dateien:

    ```cmd
    git clone https://github.com/OfficeDev/Microsoft-Teams-Samples.git
    ```

Im Folgenden finden Sie die Schritte zum Erstellen einer persönlichen Registerkarte:

1. [Generieren Ihrer Anwendung mit einer persönlichen Registerkarte](#generate-your-application-with-a-personal-tab-1)
1. [Aktualisieren und Ausführen Ihre Anwendung](#update-and-run-your-application)
1. [Einrichten eines sicheren Tunnels zu Ihrer Registerkarte](#establish-a-secure-tunnel-to-your-tab-1)
1. [Aktualisieren Ihres App-Pakets mit dem Entwicklerportal](#update-your-app-package-with-developer-portal)
1. [Vorschau Ihrer App in Teams](#preview-your-app-in-teams)

### <a name="generate-your-application-with-a-personal-tab"></a>Generieren Ihrer Anwendung mit einer persönlichen Registerkarte

1. Öffnen Sie Visual Studio, und wählen Sie **Öffnen eines Projekt oder einer Lösung** aus.

1. Wechseln Sie zu Ordner **Microsoft_Teams-Samples** > **samples** > **tab-personal** > **razor-csharp**, und öffnen Sie **PersonalTab.sln**.

1. Wählen Sie in Visual Studio **F5** oder **Debuggen starten** im Menü **Debuggen** Ihrer Anwendung aus, um zu überprüfen, ob die Anwendung ordnungsgemäß geladen wurde. Wechseln Sie in einem Browser zu den folgenden URLs:

    * `<http://localhost:3978/>`
    * `<http://localhost:3978/personalTab>`
    * `<http://localhost:3978/privacy>`
    * `<http://localhost:3978/tou>`

<details>
<summary><b>Überprüfen des Quellcodes</b></summary>

#### <a name="startupcs"></a>Startup.cs

Dieses Projekt wurde aus einer leeren Vorlage für ASP.NET Core 3.1-Webanwendungen erstellt, wobei das Kontrollkästchen **Erweitert – Für HTTPS konfigurieren** beim Setup aktiviert ist. Die MVC-Dienste werden von der `ConfigureServices()`-Methode des Frameworks für die Abhängigkeitsinjektion registriert. Außerdem ermöglicht die leere Vorlage nicht die standardmäßige Bereitstellung statischer Inhalte, sodass die Middleware für statische Dateien der Methode `Configure()` mit dem folgenden Code hinzugefügt wird:

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

#### <a name="wwwroot-folder"></a>Webstammordner

In ASP.NET Core sucht die Anwendung im Webstammordner nach statischen Dateien.

#### <a name="indexcshtml"></a>Index.cshtml

ASP.NET Core behandelt Dateien namens **Index** als Standard- oder Startseite für die Website. Wenn Ihre Browser-URL auf das Stammverzeichnis der Website zeigt, wird **Index.cshtml** als Startseite für Ihre Anwendung angezeigt.

#### <a name="appmanifest-folder"></a>Ordner „AppManifest“

Dieser Ordner enthält die folgenden erforderlichen App-Paketdateien:

* Ein Vollfarbsymbol mit einer Größe von 192 x 192 Pixeln.
* Ein transparentes Kontursymbol mit einer Größe von 32 x 32 Pixeln.
* Eine `manifest.json`-Datei, welche die Attribute Ihrer App angibt.

Diese Dateien müssen in einem App-Paket gezippt werden, damit sie beim Hochladen Ihrer Registerkarte in Teams verwendet werden können. Teams lädt die in Ihrem Manifest angegebene `contentUrl`, bettet sie in ein <IFrame\> ein, und rendert sie in Ihrer Registerkarte.

#### <a name="csproj"></a>.csproj

Klicken Sie im Visual Studio-Lösungsexplorer mit der rechten Maustaste auf das Projekt, und wählen Sie **Projektdatei bearbeiten** aus. Am Ende der Datei können Sie den folgenden Code sehen, der Ihren ZIP-Ordner erstellt und aktualisiert, wenn die Anwendung erstellt wird:

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

### <a name="update-and-run-your-application"></a>Aktualisieren und Ausführen Ihrer Anwendung

1. Öffnen Sie den Visual Studio-Lösungsexplorer, und wechseln Sie zum Ordner **Pages** > **Shared**, öffnen Sie **_Layout.cshtml**, und fügen Sie dem Abschnitt `<head>`-Kategorien Folgendes hinzu:

    ```HTML
    <script src="https://ajax.aspnetcdn.com/ajax/jQuery/jquery-3.4.1.min.js"></script>
    <script src="https://res.cdn.office.net/teams-js/2.0.0/js/MicrosoftTeams.min.js" integrity="sha384-QtTBFeFlfRDZBfwHJHYQp7MdLJ2C3sfAEB1Qpy+YblvjavBye+q87TELpTnvlXw4" crossorigin="anonymous"></script>
    ```

1. Öffnen Sie in Visual Studio-Lösungsexplorer **PersonalTab.cshtml** aus dem Ordner **Pages**, und fügen Sie `app.initialize()` in den `<script>`-Kategorien hinzu, und speichern Sie.

1. Wählen Sie in Visual Studio **F5** oder **Debuggen starten** im Menü **Debuggen** Ihrer Anwendung aus.

### <a name="establish-a-secure-tunnel-to-your-tab"></a>Einrichten eines sicheren Tunnels zu Ihrer Registerkarte

Führen Sie an der Eingabeaufforderung im Stammverzeichnis Ihres Projektverzeichnisses den folgenden Befehl aus, um einen sicheren Tunnel zu Ihrer Registerkarte einzurichten:

```cmd
ngrok http 3978 --host-header=localhost
```

### <a name="update-your-app-package-with-developer-portal"></a>Aktualisieren Ihres App-Pakets mit dem Entwicklerportal

1. Wechseln Sie zum [**Entwicklerportal**](https://dev.teams.microsoft.com/home).

1. Öffnen Sie **Apps**, und wählen Sie **App importieren** aus.

1. Der Name der App-Paketdatei lautet `tab.zip` und ist unter dem `/bin/Debug/netcoreapp3.1/tab.zip`-Pfad verfügbar.

1. Wählen Sie `tab.zip` aus, und öffnen Sie es im Entwicklerportal.

1. Eine Standard-**App-ID** wird erstellt und im Abschnitt **Allgemeine Informationen** aufgefüllt.

1. Fügen Sie die Kurz- und Langbeschreibung für Ihre App in **Beschreibungen** hinzu.

1. Fügen Sie in **Entwicklerinformationen** die erforderlichen Details hinzu, und geben Sie unter **Website (muss eine gültige HTTPS-URL sein)** Ihre ngrok-HTTPS-URL ein.

1. Aktualisieren Sie in **App-URLs** die Datenschutzrichtlinie auf `https://<yourngrokurl>/privacy` und die Nutzungsbedingungen auf `https://<yourngrokurl>/tou`, und speichern Sie.

1. In **App-Features** wählen Sie **Persönliche App** > **Erstellen Ihrer ersten persönliche App-Registerkarte** aus, geben Sie den Namen ein, und aktualisieren Sie die **Inhalts-URL** mit `https://<yourngrokurl>/personalTab`. Lassen Sie das Feld „Website-URL“ leer, und wählen Sie für „personalTab“ in der Dropdownliste **Kontext** und **Hinzufügen** aus.

1. Wählen Sie **Speichern**.

1. Im Abschnitt "Domänen" müssen Domänen auf Ihren Registerkarten Ihre ngrok-URL ohne das HTTPS-Präfix `<yourngrokurl>.ngrok.io` enthalten.

### <a name="preview-your-app-in-teams"></a>Anzeigen einer Vorschau Ihrer App in Teams

1. Wählen Sie auf der Entwicklerportal-Symbolleiste **Vorschau in Microsoft Teams** aus; das Entwicklerportal informiert Sie, dass Ihre App erfolgreich quergeladen wurde. Die Seite **Hinzufügen** wird für Ihre App in Teams angezeigt.

1. Wählen Sie **Hinzufügen** aus, um die Registerkarte in Teams zu laden. Ihre Registerkarte ist jetzt in Teams verfügbar.

    :::image type="content" source="~/assets/images/tab-images/personaltabaspnetuploaded.png" alt-text="Standardregisterkarte":::

   Jetzt haben Sie Ihre persönliche Registerkarte erfolgreich erstellt und in Teams hinzugefügt.
  
   Da Sie ihre persönliche Registerkarte in Teams haben, können Sie Ihre persönlichen Registerkarte auch [neu anordnen](#reorder-static-personal-tabs).

::: zone-end

::: zone pivot="mvc-csharp"

## <a name="create-a-personal-tab-with-aspnet-core-mvc"></a>Erstellen einer persönlichen Registerkarte mit ASP.NET Core MVC

1. Erstellen Sie an der Eingabeaufforderung ein neues Verzeichnis für Ihr Registerkartenprojekt.

1. Klonen Sie das Beispielrepository mit dem folgenden Befehl in Ihr neues Verzeichnis, oder laden Sie den [Quellcode](https://github.com/OfficeDev/Microsoft-Teams-Samples) herunter, und extrahieren Sie die Dateien:

    ```cmd
    git clone https://github.com/OfficeDev/Microsoft-Teams-Samples.git
    ```

Im Folgenden finden Sie die Schritte zum Erstellen einer persönlichen Registerkarte:

1. [Generieren Ihrer Anwendung mit einer persönlichen Registerkarte](#generate-your-application-with-a-personal-tab-2)
1. [Aktualisieren und Ausführen der Anwendung](#update-and-run-your-application-1)
1. [Einrichten eines sicheren Tunnels zu Ihrer Registerkarte](#establish-a-secure-tunnel-to-your-tab-2)
1. [Aktualisieren Ihres App-Pakets mit dem Entwicklerportal](#update-your-app-package-with-developer-portal-1)
1. [Vorschau Ihrer App in Teams](#preview-your-app-in-teams-1)

### <a name="generate-your-application-with-a-personal-tab"></a>Generieren Ihrer Anwendung mit einer persönlichen Registerkarte

1. Öffnen Sie Visual Studio, und wählen Sie **Öffnen eines Projekt oder einer Lösung** aus.

1. Wechseln Sie zum Ordner **Microsoft-Teams-Samples** > **samples** > **tab-personal** > **mvc-csharp**, und öffnen Sie **PersonalTabMVC.sln** in Visual Studio.

1. Wählen Sie in Visual Studio **F5** oder **Debuggen starten** im Menü **Debuggen** Ihrer Anwendung aus, um zu überprüfen, ob die Anwendung ordnungsgemäß geladen wurde. Wechseln Sie in einem Browser zu den folgenden URLs:

    * `<http://localhost:3978>`
    * `<http://localhost:3978/personalTab>`
    * `<http://localhost:3978/privacy>`
    * `<http://localhost:3978/tou>`

<details>
<summary><b>Überprüfen des Quellcodes</b></summary>

#### <a name="startupcs"></a>Startup.cs

Dieses Projekt wurde aus einer leeren Vorlage für ASP.NET Core 3.1-Webanwendungen erstellt, wobei das Kontrollkästchen **Erweitert – Für HTTPS konfigurieren** beim Setup aktiviert ist. Die MVC-Dienste werden von der `ConfigureServices()`-Methode des Frameworks für die Abhängigkeitsinjektion registriert. Außerdem ermöglicht die leere Vorlage nicht die standardmäßige Bereitstellung statischer Inhalte, sodass die Middleware für statische Dateien der Methode `Configure()` mit dem folgenden Code hinzugefügt wird:

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

#### <a name="wwwroot-folder"></a>Webstammordner

In ASP.NET Core sucht die Anwendung im Webstammordner nach statischen Dateien.

#### <a name="appmanifest-folder"></a>AppManifest-Ordner

Dieser Ordner enthält die folgenden erforderlichen App-Paketdateien:

* Ein **Vollfarbsymbol** mit einer Größe von 192 x 192 Pixeln.
* Ein **transparentes Kontursymbol** mit einer Größe von 32 x 32 Pixeln.
* Eine `manifest.json`-Datei, welche die Attribute Ihrer App angibt.

Diese Dateien müssen in einem App-Paket gezippt werden, damit sie beim Hochladen Ihrer Registerkarte in Teams verwendet werden können. Teams lädt die in Ihrem Manifest angegebene `contentUrl`, bettet sie in ein IFrame ein, und rendert sie in Ihrer Registerkarte.

#### <a name="csproj"></a>.csproj

Klicken Sie im Visual Studio-Lösungsexplorer mit der rechten Maustaste auf das Projekt, und wählen Sie **Projektdatei bearbeiten** aus. Am Ende der Datei sehen Sie den folgenden Code, der Ihren ZIP-Ordner erstellt und aktualisiert, wenn die Anwendung erstellt wird:

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

**PersonalTab.cs** stellt ein Nachrichtenobjekt und Methoden dar, die vom **PersonalTabController** aufgerufen werden, wenn ein Benutzer eine Schaltfläche in der **PersonalTab**-Ansicht auswählt.

#### <a name="views"></a>Ansichten

Diese Ansichten sind verschiedenen Ansichten in ASP.NET Core MVC:

* Startseite: ASP.NET Core behandelt Dateien namens **Index** als die Standard- oder Startseite für die Website. Wenn Ihre Browser-URL auf das Stammverzeichnis der Website zeigt, wird **Index.cshtml** als Startseite für Ihre Anwendung angezeigt.

* Freigegeben: Das Markup der Teilansicht **_Layout.cshtml** enthält die allgemeine Seitenstruktur der Anwendung und freigegebene visuelle Elemente. Außerdem wird auf die Teams-Bibliothek verwiesen.

#### <a name="controllers"></a>Controller

Die Controller verwenden die `ViewBag`-Eigenschaft, um Werte dynamisch in die Ansichten zu übertragen.

</details>

### <a name="update-and-run-your-application"></a>Aktualisieren und Ausführen Ihrer Anwendung

1. Öffnen Sie den Visual Studio-Lösungsexplorer, und wechseln Sie zum Ordner **Views** > **Shared**, öffnen Sie **_Layout.cshtml**, und fügen Sie dem Abschnitt `<head>`-Kategorien Folgendes hinzu:

    ```HTML
    <script src="https://ajax.aspnetcdn.com/ajax/jQuery/jquery-3.4.1.min.js"></script>
    <script src="https://res.cdn.office.net/teams-js/2.0.0/js/MicrosoftTeams.min.js" integrity="sha384-QtTBFeFlfRDZBfwHJHYQp7MdLJ2C3sfAEB1Qpy+YblvjavBye+q87TELpTnvlXw4" crossorigin="anonymous"></script>
    ```

1. Öffnen Sie im Visual Studio-Lösungsexplorer **PersonalTab.cshtml** aus dem Ordner **Views** > **PersonalTab**, und fügen Sie `app.initialize()` innerhalb der `<script>`-Kategorien hinzu, und speichern Sie.

1. Wählen Sie in Visual Studio **F5** oder **Debuggen starten** im Menü **Debuggen** Ihrer Anwendung aus.

### <a name="establish-a-secure-tunnel-to-your-tab"></a>Einrichten eines sicheren Tunnels zu Ihrer Registerkarte

Führen Sie an der Eingabeaufforderung im Stammverzeichnis Ihres Projektverzeichnisses den folgenden Befehl aus, um einen sicheren Tunnel zu Ihrer Registerkarte einzurichten:

```cmd
ngrok http 3978 --host-header=localhost
```

### <a name="update-your-app-package-with-developer-portal"></a>Aktualisieren Ihres App-Pakets mit dem Entwicklerportal

1. Wechseln Sie zum [**Entwicklerportal**](https://dev.teams.microsoft.com/home).

1. Öffnen Sie **Apps**, und wählen Sie **App importieren** aus.

1. Der Name Ihres App-Pakets lautet **tab.zip**. Es ist im folgenden Pfad verfügbar:

    ```
    /bin/Debug/netcoreapp3.1/tab.zip
    ```

1. Wählen Sie **tab.zip** aus, und öffnen Sie es im Entwicklerportal.

1. Eine Standard-**App-ID** wird erstellt und im Abschnitt **Allgemeine Informationen** aufgefüllt.

1. Fügen Sie die Kurz- und Langbeschreibung für Ihre App in **Beschreibungen** hinzu.

1. Fügen Sie in **Entwicklerinformationen** die erforderlichen Details hinzu, und geben Sie unter **Website (muss eine gültige HTTPS-URL sein)** Ihre ngrok-HTTPS-URL ein.

1. Aktualisieren Sie in **App-URLs** die Datenschutzrichtlinie auf `https://<yourngrokurl>/privacy` und die Nutzungsbedingungen auf `https://<yourngrokurl>/tou`, und speichern Sie.

1. In **App-Features** wählen Sie **Persönliche App** > **Erstellen Ihrer ersten persönliche App-Registerkarte** aus, geben Sie den Namen ein, und aktualisieren Sie die **Inhalts-URL** mit `https://<yourngrokurl>/personalTab`. Lassen Sie das Feld „Website-URL“ leer, und wählen Sie für „personalTab“ in der Dropdownliste **Kontext** und **Hinzufügen** aus.

1. Wählen Sie **Speichern**.

1. Im Abschnitt „Domänen“ müssen Domänen auf Ihren Registerkarten Ihre ngrok-URL ohne das HTTPS-Präfix `<yourngrokurl>.ngrok.io` enthalten.

### <a name="preview-your-app-in-teams"></a>Anzeigen einer Vorschau Ihrer App in Teams

1. Wählen Sie auf der Entwicklerportal-Symbolleiste **Vorschau in Microsoft Teams** aus; das Entwicklerportal informiert Sie, dass Ihre App erfolgreich quergeladen wurde. Die Seite **Hinzufügen** wird für Ihre App in Teams angezeigt.

1. Wählen Sie **Hinzufügen** aus, um die Registerkarte in Teams zu laden. Ihre Registerkarte ist jetzt in Teams verfügbar.

    :::image type="content" source="~/assets/images/tab-images/personaltabaspnetmvccoreuploaded.png" alt-text="Registerkarte „Persönlich“":::
  
   Jetzt haben Sie Ihre persönliche Registerkarte erfolgreich erstellt und in Teams hinzugefügt.

   Da Sie ihre persönliche Registerkarte in Teams haben, können Sie Ihre persönlichen Registerkarte auch [neu anordnen](#reorder-static-personal-tabs).

::: zone-end

## <a name="reorder-static-personal-tabs"></a>Statische persönliche Registerkarten neu anordnen

Ab Manifestversion 1.7 können Entwickler alle Registerkarten in ihrer persönlichen App neu anordnen. Insbesondere kann ein Entwickler die Registerkarte **Bot-Chat**, die standardmäßig immer an erster Stelle steht, an eine beliebige Stelle in der Kopfzeile der persönlichen App-Registerkarte verschieben. Es werden zwei reservierte `entityId`-Schlüsselwörter für die Registerkarte deklariert, **Unterhaltungen** und **Info**.

Wenn Sie einen Bot mit einem **persönlichen** Bereich erstellen, wird er standardmäßig in der ersten Registerkartenposition in einer persönlichen App angezeigt. Wenn Sie ihn an eine andere Position verschieben möchten, müssen Sie Ihrem Manifest ein statisches Registerkartenobjekt mit dem reservierten Schlüsselwort **Unterhaltungen** hinzufügen. Die Registerkarte **Unterhaltung** wird im Web oder Desktop angezeigt, je nachdem, wo Sie die Registerkarte **Unterhaltung** im `staticTabs`-Array hinzufügen.

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

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Erstellen einer Kanal- oder Gruppenregisterkarte](~/tabs/how-to/create-channel-group-tab.md)

## <a name="see-also"></a>Siehe auch

* [Teams-Registerkarten](~/tabs/what-are-tabs.md)
* [Registerkarten auf mobilen Geräten](~/tabs/design/tabs-mobile.md)
* [Erstellen von Registerkarten mit adaptiven Karten](~/tabs/how-to/build-adaptive-card-tabs.md)
* [Registerkarten für Unterhaltungen erstellen](~/tabs/how-to/conversational-tabs.md)
* [Für Teams über persönliche App oder Registerkarte freigeben](~/concepts/build-and-test/share-to-teams-from-personal-app-or-tab.md)
