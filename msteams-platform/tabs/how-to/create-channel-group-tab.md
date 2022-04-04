---
title: Erstellen einer Kanal- oder Gruppenregisterkarte
author: laujan
description: Eine Schnellstartanleitung zum Erstellen einer Kanal- und Gruppenregisterkarte mit dem Yeoman-Generator für Microsoft Teams, einschließlich der Überprüfung des Quellcodes mit Codebeispielen.
ms.localizationpriority: medium
ms.topic: quickstart
ms.author: lajanuar
zone_pivot_groups: teams-app-environment
ms.openlocfilehash: 31da2a8ee267ef42e6c0abd4e3bd695cf69d2f01
ms.sourcegitcommit: 3d6aa10d2f58a63c6a4281a30e8771469dba0d0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/04/2022
ms.locfileid: "64636147"
---
# <a name="channel-or-group-tab"></a>Kanal- oder Gruppenregisterkarte

Kanal-- oder Gruppenregisterkarten übermitteln Inhalte an Kanäle und Gruppenchats und sind eine hervorragende Möglichkeit zum Erstellen von Bereichen für die Zusammenarbeit rund um dedizierte webbasierte Inhalte.

::: zone pivot="node-java-script"

## <a name="create-a-custom-channel-or-group-tab-with-nodejs"></a>Erstellen einer benutzerdefinierten Kanal- oder Gruppenregisterkarte mit Node.js

1. Installieren Sie an der Eingabeaufforderung die [Yeoman](https://yeoman.io/) - und [gulp-cli-Pakete](https://www.npmjs.com/package/gulp-cli) , indem Sie nach der Installation des **Node.js** den folgenden Befehl eingeben:

    ```cmd
    npm install yo gulp-cli --global
    ```

2. Installieren Sie an der Eingabeaufforderung Microsoft Teams App-Generator, indem Sie den folgenden Befehl eingeben:

    ```cmd
    npm install generator-teams --global
    ```

Nachfolgend finden Sie die Schritte zum Erstellen einer Kanal- oder Gruppenregisterkarte:

* [Generieren Der Anwendung mit einer Kanal- oder Gruppenregisterkarte](#generate-your-application-with-a-channel-or-group-tab)
* [Erstellen Ihres App-Pakets](#create-your-app-package)
* [Erstellen und Ausführen der Anwendung](#build-and-run-your-application)
* [Einrichten eines sicheren Tunnels zu Ihrer Registerkarte](#establish-a-secure-tunnel-to-your-tab)
* [Hochladen Der Anwendung Teams](#upload-your-application-to-teams)

### <a name="generate-your-application-with-a-channel-or-group-tab"></a>Generieren Der Anwendung mit einer Kanal- oder Gruppenregisterkarte

1. Erstellen Sie an der Eingabeaufforderung ein neues Verzeichnis für die Kanal- oder Gruppenregisterkarte.

1. Geben Sie den folgenden Befehl in Ihr neues Verzeichnis ein, um den Microsoft Teams App-Generator zu starten:

    ```cmd
    yo teams
    ```

1. Geben Sie Ihre Werte für eine Reihe von Fragen ein, die von Microsoft Teams App-Generator zum Aktualisieren Der **Manifest.json-Datei** aufgefordert werden:

    ![Screenshot zum Öffnen des Generators](/microsoftteams/platform/assets/images/tab-images/teamsTabScreenshot.PNG)

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

        Verwenden Sie die Pfeiltasten, um die **konfigurierbare** Registerkarte auszuwählen.

    * **Welche Bereiche möchten Sie für Ihre Registerkarte verwenden?**

        Sie können ein Team oder einen Gruppenchat auswählen.

    * **Benötigen Sie Microsoft Azure Active Directory (Azure AD) Single Sign-On-Unterstützung für die Registerkarte?**

        Wählen Sie aus, Microsoft Azure Active Directory (Azure AD) Single Sign-On-Unterstützung für die Registerkarte **nicht** einzuschließen. Der Standardwert ist "Ja", geben Sie **"n**" ein.

    * **Soll diese Registerkarte in SharePoint Online verfügbar sein? (J/n)**

        Geben Sie **n** ein

    </details>

> [!IMPORTANT]
> The path component **yourDefaultTabNameTab** is the value that you entered in the generator for **Default Tab Name** plus the word **Tab**.
>
> Beispiel: DefaultTabName ist **MyTab** und **dann /MyTabTab/**

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

    ```bash
    gulp serve
    ```

1. Geben Sie `http://localhost:3007/<yourDefaultAppNameTab>/` in Ihren Browser ein, um die Startseite Ihrer Anwendung anzuzeigen.

    :::image type="content" source="~/assets/images/tab-images/homePage.png" alt-text="Standardregisterkarte" border="true":::

1. Um die Registerkartenkonfigurationsseite anzuzeigen, wechseln Sie zu `http://localhost:3007/<yourDefaultAppNameTab>/config.html`. Es wird Folgendes gezeigt:

    :::image type="content" source="~/assets/images/tab-images/configurationPage.png" alt-text="Registerkartenkonfigurationsseite" border="true":::

### <a name="establish-a-secure-tunnel-to-your-tab"></a>Einrichten eines sicheren Tunnels zu Ihrer Registerkarte

Um einen sicheren Tunnel zu Ihrer Registerkarte einzurichten, beenden Sie den localhost, und geben Sie den folgenden Befehl ein:

```cmd
gulp ngrok-serve
```

> [!IMPORTANT]
> Nachdem Die Registerkarte in Microsoft Teams über **ngrok** hochgeladen und erfolgreich gespeichert wurde, können Sie sie in Teams anzeigen, bis die Tunnelsitzung endet. Wenn Sie Ihre ngrok-Sitzung neu starten, müssen Sie Ihre App mit der neuen URL aktualisieren.

### <a name="upload-your-application-to-teams"></a>Hochladen Der Anwendung Teams

1. Wechseln Sie zu Microsoft Teams, und wählen Sie **Store**&nbsp; :::image type="content" source="~/assets/images/tab-images/store.png" alt-text="Teams Store"::: aus.
1. Wählen Sie **"Apps verwalten" aus**.
1. Wählen Sie **"App veröffentlichen"** und **Hochladen einer benutzerdefinierten App** aus.

    :::image type="content" source="~/assets/images/tab-images/publish-app.png" alt-text="Hochladen benutzerdefinierte App" border="true":::

1. Wechseln Sie zu Ihrem Projektverzeichnis, navigieren Sie zum **Ordner "./package** ", wählen Sie den ZIP-Ordner des App-Pakets aus, und wählen Sie " **Öffnen**" aus.
    
    :::image type="content" source="~/assets/images/tab-images/channeltabadded.png" alt-text="Registerkarte &quot;Hochgeladener Kanal&quot;" border="true":::

1. Wählen Sie im Dialogfeld **"Hinzufügen** " aus. Ihre Registerkarte wird in Teams hochgeladen.
    
    > [!NOTE]
    > Wenn  **"Hinzufügen** " nicht im Dialogfeld angezeigt wird, entfernen Sie den folgenden Code aus dem Manifest des zip-Ordners des hochgeladenen App-Pakets. Zippen Sie den Ordner erneut, und laden Sie ihn in Teams hoch.
    >
    >```Json
    >"staticTabs": [],
    >"bots": [],
    >"connectors": [],
    >"composeExtensions": [],
    >```

1. Befolgen Sie die Anweisungen zum Hinzufügen einer Registerkarte. Es gibt ein benutzerdefiniertes Konfigurationsdialogfeld für Ihre Kanal- oder Gruppenregisterkarte.
1. Wählen Sie **Speichern aus** , und Ihre Registerkarte wird der Registerkartenleiste des Kanals hinzugefügt.

    :::image type="content" source="~/assets/images/tab-images/channeltabuploaded.png" alt-text="Registerkarte &quot;Kanal&quot; hochgeladen" border="true":::
    
    Jetzt haben Sie erfolgreich Ihre Kanal- oder Gruppenregisterkarte in Teams erstellt und hinzugefügt.

::: zone-end

::: zone pivot="razor-csharp"

## <a name="create-a-custom-channel-or-group-tab-with-aspnet-core"></a>Erstellen einer benutzerdefinierten Kanal- oder Gruppenregisterkarte mit ASP.NET Core

1. Erstellen Sie an der Eingabeaufforderung ein neues Verzeichnis für Ihr Registerkartenprojekt.

1. Klonen Sie das Beispiel-Repository mit dem folgenden Befehl in Ihr neues Verzeichnis, oder Sie können den [Quellcode](https://github.com/OfficeDev/Microsoft-Teams-Samples) herunterladen und die Dateien extrahieren:

    ```cmd
    git clone https://github.com/OfficeDev/Microsoft-Teams-Samples.git
    ```

Nachfolgend finden Sie die Schritte zum Erstellen einer Kanal- oder Gruppenregisterkarte:

* [Generieren Der Anwendung mit einer Kanal- oder Gruppenregisterkarte](#generate-your-application-with-a-channel-or-group-tab-1)
* [Einrichten eines sicheren Tunnels zu Ihrer Registerkarte](#establish-a-secure-tunnel-to-your-tab-1)
* [Aktualisieren Der Anwendung](#update-your-application)
* [Erstellen und Ausführen der Anwendung](#build-and-run-your-application-1)
* [Aktualisieren Des App-Pakets mit dem Entwicklerportal](#update-your-app-package-with-developer-portal)
* [Anzeigen einer Vorschau Ihrer App in Teams](#preview-your-app-in-teams)

### <a name="generate-your-application-with-a-channel-or-group-tab"></a>Generieren Der Anwendung mit einer Kanal- oder Gruppenregisterkarte

1. Öffnen Sie Visual Studio, und wählen Sie **"Projekt oder Projektmappe öffnen**" aus.

1. Wechseln Sie zum Ordner "Microsoft-Teams-Samplessamplestab-channel-grouprazor-csharp >  >  > ", und öffnen Sie **"channelGroupTab.sln"**.

1. Wählen Sie in Visual Studio **F5** aus, oder wählen Sie im **Menü "Debuggen**" der Anwendung die Option **"Debuggen starten**" aus, um zu überprüfen, ob die Anwendung ordnungsgemäß geladen wurde. Wechseln Sie in einem Browser zu den folgenden URLs:

    * https://localhost:3978/
    * https://localhost:3978/privacy
    * https://localhost:3978/tou

<details>
<summary><b>Überprüfen des Quellcodes</b></summary>

#### <a name="startupcs"></a>Startup.cs

Dieses Projekt wurde aus einer leeren Vorlage ASP.NET Core 3.1-Webanwendung erstellt, wobei das Kontrollkästchen **Erweitert * Für HTTPS** konfigurieren beim Setup aktiviert ist. Die MVC-Dienste werden durch die Methode des Abhängigkeitsinjektionsframeworks `ConfigureServices()` registriert. Darüber hinaus ermöglicht die leere Vorlage nicht standardmäßig die Bereitstellung statischer Inhalte, sodass die Middleware für statische Dateien der Methode mit dem folgenden Code hinzugefügt `Configure()` wird:

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

#### <a name="tabcs"></a>Tab.cs

Diese C#-Datei enthält eine Methode, die während der Konfiguration von **Tab.cshtml** aufgerufen wird.

#### <a name="appmanifest-folder"></a>AppManifest-Ordner

Dieser Ordner enthält die folgenden erforderlichen App-Paketdateien:

* Ein **Vollfarbsymbol** mit einer Auflösung von 192 x 192 Pixeln.
* Ein **transparentes Gliederungssymbol** mit einer Auflösung von 32 x 32 Pixeln.
* Eine **Manifest.json-Datei** , die die Attribute Ihrer App angibt.

Diese Dateien müssen in einem App-Paket gezippt werden, um Ihre Registerkarte in Teams hochzuladen. Wenn ein Benutzer die Registerkarte hinzufügt oder aktualisiert, lädt Microsoft Teams das `configurationUrl` angegebene Element in Ihrem Manifest, einbettet es in einen IFrame und rendert es auf der Registerkarte.

#### <a name="csproj"></a>CSPROJ

Klicken Sie im fenster Visual Studio Projektmappen-Explorer mit der rechten Maustaste auf das Projekt, und wählen Sie **"Project Datei bearbeiten**" aus. Am Ende der Datei wird der folgende Code angezeigt, der Ihren ZIP-Ordner erstellt und aktualisiert, wenn die Anwendung erstellt wird:

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

### <a name="establish-a-secure-tunnel-to-your-tab"></a>Einrichten eines sicheren Tunnels zu Ihrer Registerkarte

Führen Sie an der Eingabeaufforderung im Stammverzeichnis des Projekts den folgenden Befehl aus, um einen sicheren Tunnel zu Ihrer Registerkarte einzurichten:

```cmd
ngrok http 3978 --host-header=localhost
```

Stellen Sie sicher, dass die Eingabeaufforderung mit ngrok ausgeführt wird, und notieren Sie sich die URL.

### <a name="update-your-application"></a>Aktualisieren Der Anwendung

1. Öffnen Sie Visual Studio Projektmappen-Explorer, wechseln Sie zum Ordner **"****PagesShared** > ", öffnen **Sie _Layout.cshtml**, und fügen Sie Folgendes zum <head> Tags-Abschnitt:

    ```html
    <script src="https://ajax.aspnetcdn.com/ajax/jQuery/jquery-3.4.1.min.js"></script>
    <script src="https://statics.teams.cdn.office.net/sdk/v1.6.0/js/MicrosoftTeams.min.js"></script>
    ```
    
    > [!IMPORTANT]
    > Kopieren Sie die `<script src="...">` URLs von dieser Seite nicht, und fügen Sie sie nicht ein, da sie nicht die neueste Version darstellen. Um die neueste Version des SDK zu erhalten, wechseln Sie immer zu [Microsoft Teams JavaScript-API](https://www.npmjs.com/package/@microsoft/teams-js).
    
1. Fügen Sie einen Aufruf `microsoftTeams.initialize();` in das `script` Tag ein.

1. Wechseln Sie in Visual Studio Projektmappen-Explorer zum Ordner **"Seiten**", und öffnen **Sie "Tab.cshtml".**

    Innerhalb von **Tab.cshtml** zeigt die Anwendung dem Benutzer zwei Optionsschaltflächen zum Anzeigen der Registerkarte mit einem roten oder grauen Symbol an. Durch Auswählen der Schaltfläche "**Grau auswählen**" oder "**Rot auswählen**" wird die Schaltfläche "**Speichern**" auf der Konfigurationsseite festgelegt `saveGray()` bzw`saveRed()`. aktiviert`settings.setValidityState(true)`. Dieser Code teilt Teams mit, dass Sie die Konfigurationsanforderungen erfüllt haben und die Installation fortgesetzt werden kann. Die Parameter von `settings.setSettings` sind festgelegt. Schließlich wird aufgerufen, `saveEvent.notifySuccess()` um anzugeben, dass die Inhalts-URL erfolgreich aufgelöst wurde.

1. Aktualisieren Sie die `websiteUrl` Werte in `contentUrl` jeder Funktion mit der HTTPS-ngrok-URL auf Ihre Registerkarte.

    Ihr Code sollte nun Folgendes enthalten, wobei **y8rCgT2b** durch Ihre ngrok-URL ersetzt wird:

    ```javascript
        
        let saveGray = () => {
            microsoftTeams.settings.registerOnSaveHandler(function (saveEvent) {
                microsoftTeams.settings.setSettings({
                    websiteUrl: `https://y8rCgT2b.ngrok.io`,
                    contentUrl: `https://y8rCgT2b.ngrok.io/gray/`,
                    entityId: "grayIconTab",
                    suggestedDisplayName: "MyNewTab"
                });
                saveEvent.notifySuccess();
            });
        }

        let saveRed = () => {
            microsoftTeams.settings.registerOnSaveHandler(function (saveEvent) {
                microsoftTeams.settings.setSettings({
                    websiteUrl: `https://y8rCgT2b.ngrok.io`,
                    contentUrl: `https://y8rCgT2b.ngrok.io/red/`,
                    entityId: "redIconTab",
                    suggestedDisplayName: "MyNewTab"
                });
                saveEvent.notifySuccess();
        });
        }
    ```

1. Speichern Sie die aktualisierte **Datei Tab.cshtml**.

### <a name="build-and-run-your-application"></a>Erstellen und Ausführen der Anwendung

1. Wählen Sie in Visual Studio **F5** aus, oder wählen Sie im Menü "**Debuggen**" die Option **"Debuggen starten**" aus.

1. Stellen Sie sicher, dass **ngrok** ausgeführt wird und ordnungsgemäß funktioniert, indem Sie Ihren Browser öffnen und über die ngrok-HTTPS-URL, die im Eingabeaufforderungsfenster bereitgestellt wurde, zur Inhaltsseite wechseln.

    > [!TIP]
    > Sie müssen ihre Anwendung sowohl in Visual Studio als auch in ngrok ausführen, um die in diesem Artikel beschriebenen Schritte auszuführen. Wenn Sie die Ausführung Der Anwendung in Visual Studio beenden müssen, um daran zu arbeiten, **lassen Sie ngrok ausgeführt**. Beim Neustart der Anwendung in Visual Studio wird die Weiterleitung der Anwendung überwacht und fortgesetzt. Wenn Sie den ngrok-Dienst neu starten müssen, wird eine neue URL zurückgegeben, und Sie müssen Ihre Anwendung mit der neuen URL aktualisieren.

### <a name="update-your-app-package-with-developer-portal"></a>Aktualisieren Des App-Pakets mit dem Entwicklerportal

1. Wechseln Sie zu Microsoft Teams. Wenn Sie die [webbasierte Version](https://teams.microsoft.com) verwenden, können Sie Ihren Front-End-Code mithilfe der [Entwicklertools](~/tabs/how-to/developer-tools.md) Ihres Browsers überprüfen.

1. Wechseln Sie zum [**Entwicklerportal**](https://dev.teams.microsoft.com/home).

1. Öffnen Sie **Apps** , und wählen Sie **"App importieren**" aus.

1. Der Name Ihres App-Pakets lautet **tab.zip**. Es ist im folgenden Pfad verfügbar:

    ```bash
    /bin/Debug/netcoreapp3.1/tab.zip
    ```

1. Wählen Sie **tab.zip** aus, und öffnen Sie es im Entwicklerportal.

1. Im Abschnitt "**Grundlegende Informationen**" wird eine **Standard-App-ID** erstellt und ausgefüllt.

1. Fügen Sie die Kurz- und Langbeschreibung für Ihre App in **"Beschreibungen" hinzu**.

1. Fügen Sie in den **Entwicklerinformationen** die erforderlichen Details hinzu, und geben Sie ihrer ngrok **HTTPS-URL auf der Website (muss eine gültige HTTPS-URL sein).**

1. Aktualisieren Sie in **App-URLs** die Datenschutzrichtlinie `https://<yourngrokurl>/privacy` und die Nutzungsbedingungen, `https://<yourngrokurl>/tou` und speichern Sie sie.

1. Wählen Sie in **den App-Features** "Gruppe" und "Kanal-App" aus. Aktualisieren Sie die **Konfigurations-URL** , `https://<yourngrokurl>/tab` und wählen Sie Ihre Registerkarte " **Bereich" aus**.

1. Klicken Sie auf **Speichern**.

1. Im Abschnitt "Domänen" müssen Domänen von Ihren Registerkarten Ihre ngrok-URL ohne das HTTPS-Präfix `<yourngrokurl>.ngrok.io`enthalten.

### <a name="preview-your-app-in-teams"></a>Anzeigen einer Vorschau Ihrer App in Teams

1. Wählen Sie **in Teams** auf der Symbolleiste des Entwicklerportals die Vorschau aus. Entwicklerportal informiert Sie darüber, dass Ihre App erfolgreich quergeladen wurde. Die Seite **"Hinzufügen**" wird für Ihre App in Teams angezeigt.

1. Wählen Sie **"Zu Team hinzufügen** " aus, um die Registerkarte in einem Team einzurichten. Konfigurieren Sie Ihre Registerkarte, und wählen Sie **"Speichern**" aus. Ihre Registerkarte ist jetzt in Teams verfügbar.

    :::image type="content" source="~/assets/images/tab-images/channeltabaspnetuploaded.png" alt-text="Kanalregisterkarte ASPNET hochgeladen" border="true":::
    
    Jetzt haben Sie erfolgreich Ihre Kanal- oder Gruppenregisterkarte in Teams erstellt und hinzugefügt.

::: zone-end

::: zone pivot="mvc-csharp"

## <a name="create-a-custom-channel-or-group-tab-with-aspnet-core-mvc"></a>Erstellen einer benutzerdefinierten Kanal- oder Gruppenregisterkarte mit ASP.NET Core MVC

1. Erstellen Sie an der Eingabeaufforderung ein neues Verzeichnis für Ihr Registerkartenprojekt.

1. Klonen Sie das Beispiel-Repository mit dem folgenden Befehl in Ihr neues Verzeichnis, oder Sie können den [Quellcode](https://github.com/OfficeDev/Microsoft-Teams-Samples) herunterladen und die Dateien extrahieren:

    ```cmd
    git clone https://github.com/OfficeDev/Microsoft-Teams-Samples.git
    ```

Nachfolgend finden Sie die Schritte zum Erstellen einer Kanal- oder Gruppenregisterkarte:

* [Generieren Der Anwendung mit einer Kanal- oder Gruppenregisterkarte](#generate-your-application-with-a-channel-or-group-tab-2)
* [Einrichten eines sicheren Tunnels zu Ihrer Registerkarte](#establish-a-secure-tunnel-to-your-tab-2)
* [Aktualisieren Der Anwendung](#update-your-application-1)
* [Erstellen und Ausführen der Anwendung](#build-and-run-your-application-2)
* [Aktualisieren Des App-Pakets mit dem Entwicklerportal](#update-your-app-package-with-developer-portal-1)
* [Anzeigen einer Vorschau Ihrer App in Teams](#preview-your-app-in-teams-1)

### <a name="generate-your-application-with-a-channel-or-group-tab"></a>Generieren Der Anwendung mit einer Kanal- oder Gruppenregisterkarte

1. Öffnen Sie Visual Studio, und wählen Sie **"Projekt oder Projektmappe öffnen**" aus.

1. Wechseln Sie zum Ordner "Microsoft-Teams-Samplessamplestab-channel-groupmvc-csharp >  >  > ", und öffnen Sie **"ChannelGroupTabMVC.sln"**.

1. Wählen Sie in Visual Studio **F5** aus, oder wählen Sie im **Menü "Debuggen**" der Anwendung die Option **"Debuggen starten**" aus, um zu überprüfen, ob die Anwendung ordnungsgemäß geladen wurde. Wechseln Sie in einem Browser zu den folgenden URLs:

    * https://localhost:3978/
    * https://localhost:3978/privacy
    * https://localhost:3978/tou

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

#### <a name="appmanifest-folder"></a>AppManifest-Ordner

Dieser Ordner enthält die folgenden erforderlichen App-Paketdateien:

* Ein **Vollfarbsymbol** mit einer Auflösung von 192 x 192 Pixeln.
* Ein **transparentes Gliederungssymbol** mit einer Auflösung von 32 x 32 Pixeln.
* Eine **Manifest.json-Datei** , die die Attribute Ihrer App angibt.

Diese Dateien müssen in einem App-Paket gezippt werden, um Ihre Registerkarte in Teams hochzuladen.

#### <a name="csproj"></a>CSPROJ

Klicken Sie im fenster Visual Studio Projektmappen-Explorer mit der rechten Maustaste auf das Projekt, und wählen Sie **"Project Datei bearbeiten**" aus. Am Ende der Datei wird der folgende Code angezeigt, der Ihren ZIP-Ordner erstellt und aktualisiert, wenn die Anwendung erstellt wird:

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

#### <a name="models"></a>Modelle

**ChannelGroup.cs** stellt ein Message-Objekt und Methoden vor, die während der Konfiguration von den Controllern aufgerufen werden.

#### <a name="views"></a>Ansichten

Dies sind die verschiedenen Ansichten in ASP.NET Core MVC:

* Start: ASP.NET Core behandelt Dateien mit dem Namen **Index** als Standard- oder Startseite für die Website. Wenn Ihre Browser-URL auf den Stamm der Website zeigt, wird **Index.cshtml** als Startseite für Ihre Anwendung angezeigt.

* Freigegeben: Das Partielle Ansichtsmarkup **_Layout.cshtml** enthält die allgemeine Seitenstruktur der Anwendung und freigegebene visuelle Elemente. Außerdem wird auf die Teams Bibliothek verwiesen.

#### <a name="controllers"></a>Controller

Die Controller verwenden die `ViewBag` Eigenschaft, um Werte dynamisch in die Ansichten zu übertragen.

</details>

### <a name="establish-a-secure-tunnel-to-your-tab"></a>Einrichten eines sicheren Tunnels zu Ihrer Registerkarte

Führen Sie an der Eingabeaufforderung im Stammverzeichnis des Projekts den folgenden Befehl aus, um einen sicheren Tunnel zu Ihrer Registerkarte einzurichten:

```cmd
ngrok http 3978 --host-header=localhost
```

Stellen Sie sicher, dass die Eingabeaufforderung mit ngrok ausgeführt wird, und notieren Sie sich die URL.

### <a name="update-your-application"></a>Aktualisieren Der Anwendung

1. Öffnen Sie Visual Studio Projektmappen-Explorer, wechseln Sie zum Ordner **"****ViewsShared** > ", öffnen **Sie _Layout.cshtml**, und fügen Sie Folgendes zum <head> Tags-Abschnitt:

    ```html
    <script src="https://ajax.aspnetcdn.com/ajax/jQuery/jquery-3.4.1.min.js"></script>
    <script src="https://statics.teams.cdn.office.net/sdk/v1.6.0/js/MicrosoftTeams.min.js"></script>
    ```
    
    > [!IMPORTANT]
    > Kopieren Sie die `<script src="...">` URLs von dieser Seite nicht, und fügen Sie sie nicht ein, da sie nicht die neueste Version darstellen. Um die neueste Version des SDK zu erhalten, wechseln Sie immer zu [Microsoft Teams JavaScript-API](https://www.npmjs.com/package/@microsoft/teams-js).
    
1. Fügen Sie einen Aufruf `microsoftTeams.initialize();` in das `script` Tag ein.

1. Wechseln Sie in Visual Studio Projektmappen-Explorer zum Ordner **"Tab"**, und öffnen **Sie "Tab.cshtml".**

    Innerhalb von **Tab.cshtml** zeigt die Anwendung dem Benutzer zwei Optionsschaltflächen zum Anzeigen der Registerkarte mit einem roten oder grauen Symbol an. Durch Auswählen der Schaltfläche "**Grau auswählen**" oder "**Rot auswählen**" wird die Schaltfläche "**Speichern**" auf der Konfigurationsseite festgelegt `saveGray()` bzw`saveRed()`. aktiviert`settings.setValidityState(true)`. Dieser Code teilt Teams mit, dass Sie die Konfigurationsanforderungen erfüllt haben und die Installation fortgesetzt werden kann. Die Parameter von `settings.setSettings` sind festgelegt. Schließlich wird aufgerufen, `saveEvent.notifySuccess()` um anzugeben, dass die Inhalts-URL erfolgreich aufgelöst wurde. 

1. Aktualisieren Sie die `websiteUrl` Werte in `contentUrl` jeder Funktion mit der HTTPS-ngrok-URL auf Ihre Registerkarte.

    Ihr Code sollte nun Folgendes enthalten, wobei **y8rCgT2b** durch Ihre ngrok-URL ersetzt wird:

    ```javascript

        let saveGray = () => {
            microsoftTeams.settings.registerOnSaveHandler(function (saveEvent) {
                microsoftTeams.settings.setSettings({
                    websiteUrl: `https://y8rCgT2b.ngrok.io`,
                    contentUrl: `https://y8rCgT2b.ngrok.io/gray/`,
                    entityId: "grayIconTab",
                    suggestedDisplayName: "MyNewTab"
                });
                saveEvent.notifySuccess();
            });
        }
    
        let saveRed = () => {
            microsoftTeams.settings.registerOnSaveHandler(function (saveEvent) {
                microsoftTeams.settings.setSettings({
                    websiteUrl: `https://y8rCgT2b.ngrok.io`,
                    contentUrl: `https://y8rCgT2b.ngrok.io/red/`,
                    entityId: "redIconTab",
                    suggestedDisplayName: "MyNewTab"
                });
                saveEvent.notifySuccess();
            });
        }
    ```

1. Speichern Sie unbedingt die aktualisierte Datei **Tab.cshtml**.

### <a name="build-and-run-your-application"></a>Erstellen und Ausführen der Anwendung

1. Wählen Sie in Visual Studio **F5** aus, oder wählen Sie im Menü "**Debuggen**" die Option **"Debuggen starten**" aus.

1. Stellen Sie sicher, dass **ngrok** ausgeführt wird und ordnungsgemäß funktioniert, indem Sie Ihren Browser öffnen und über die ngrok-HTTPS-URL, die im Eingabeaufforderungsfenster bereitgestellt wurde, zur Inhaltsseite wechseln.

    > [!TIP]
    > Sie müssen ihre Anwendung sowohl in Visual Studio als auch in ngrok ausführen, um die in diesem Artikel beschriebenen Schritte auszuführen. Wenn Sie die Ausführung Der Anwendung in Visual Studio beenden müssen, um daran zu arbeiten, **lassen Sie ngrok ausgeführt**. Beim Neustart der Anwendung in Visual Studio wird die Weiterleitung der Anwendung überwacht und fortgesetzt. Wenn Sie den ngrok-Dienst neu starten müssen, wird eine neue URL zurückgegeben, und Sie müssen Ihre Anwendung mit der neuen URL aktualisieren.

### <a name="update-your-app-package-with-developer-portal"></a>Aktualisieren Des App-Pakets mit dem Entwicklerportal

1. Wechseln Sie zu Microsoft Teams. Wenn Sie die [webbasierte Version](https://teams.microsoft.com) verwenden, können Sie Ihren Front-End-Code mithilfe der [Entwicklertools](~/tabs/how-to/developer-tools.md) Ihres Browsers überprüfen.

1. Wechseln Sie zum [**Entwicklerportal**](https://dev.teams.microsoft.com/home).

1. Öffnen Sie **Apps** , und wählen Sie **"App importieren**" aus.

1. Der Name Ihres App-Pakets lautet **tab.zip**. Es ist im folgenden Pfad verfügbar:

    ```bash
    /bin/Debug/netcoreapp3.1/tab.zip
    ```

1. Wählen Sie **tab.zip** aus, und öffnen Sie es im Entwicklerportal.

1. Im Abschnitt "**Grundlegende Informationen**" wird eine **Standard-App-ID** erstellt und ausgefüllt.

1. Fügen Sie die Kurz- und Langbeschreibung für Ihre App in **"Beschreibungen" hinzu**.

1. Fügen Sie in den **Entwicklerinformationen** die erforderlichen Details hinzu, und geben Sie ihrer ngrok **HTTPS-URL auf der Website (muss eine gültige HTTPS-URL sein).**

1. Aktualisieren Sie in **App-URLs** die Datenschutzrichtlinie `https://<yourngrokurl>/privacy` und die Nutzungsbedingungen, `https://<yourngrokurl>/tou` und speichern Sie sie.

1. Wählen Sie in **den App-Features** "Gruppe" und "Kanal-App" aus. Aktualisieren Sie die **Konfigurations-URL** , `https://<yourngrokurl>/tab` und wählen Sie Ihre Registerkarte " **Bereich" aus**.

1. Klicken Sie auf **Speichern**.

1. Im Abschnitt "Domänen" müssen Domänen von Ihren Registerkarten Ihre ngrok-URL ohne das HTTPS-Präfix `<yourngrokurl>.ngrok.io`enthalten.

### <a name="preview-your-app-in-teams"></a>Anzeigen einer Vorschau Ihrer App in Teams

1. Wählen Sie **in Teams** auf der Symbolleiste des Entwicklerportals die Vorschau aus. Entwicklerportal informiert Sie darüber, dass Ihre App erfolgreich quergeladen wurde. Die Seite **"Hinzufügen**" wird für Ihre App in Teams angezeigt.

1. Wählen Sie **"Zu Team hinzufügen** " aus, um die Registerkarte in einem Team einzurichten. Konfigurieren Sie Ihre Registerkarte, und wählen Sie **"Speichern**" aus. Ihre Registerkarte ist jetzt in Teams verfügbar.

    :::image type="content" source="~/assets/images/tab-images/channeltabaspnetuploaded.png" alt-text="Kanalregisterkarte ASPNET MVC hochgeladen" border="true":::
    
    Jetzt haben Sie erfolgreich Ihre Kanal- oder Gruppenregisterkarte in Teams erstellt und hinzugefügt.

::: zone-end

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Erstellen einer Inhaltsseite](~/tabs/how-to/create-tab-pages/content-page.md)

## <a name="see-also"></a>Siehe auch

* [registerkarten Teams](~/tabs/what-are-tabs.md)
* [Erstellen einer persönlichen Registerkarte](~/tabs/how-to/create-personal-tab.md)
* [Registerkarten auf mobilen Geräten](~/tabs/design/tabs-mobile.md)
* [Erstellen von Registerkarten mit adaptiven Karten](~/tabs/how-to/build-adaptive-card-tabs.md)
* [Erstellen einer Seite zum Entfernen](~/tabs/how-to/create-tab-pages/removal-page.md)
