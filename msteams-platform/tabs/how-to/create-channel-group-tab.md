---
title: Erstellen einer Kanalregisterkarte oder Gruppenregisterkarte
author: laujan
description: Erstellen Sie einen benutzerdefinierten Kanal, die Registerkarte "Gruppierung" mit Node.js, ASP.NET Core ASP.NET Core MVC. App generieren, Paket erstellen, App erstellen und ausführen, Geheimnistunnel, Hochladen in Teams
ms.localizationpriority: high
ms.topic: quickstart
ms.author: lajanuar
zone_pivot_groups: teams-app-environment
ms.openlocfilehash: 2ad44d0c43df7193106474fc3b6534d9ddde5bfc
ms.sourcegitcommit: 84747a9e3c561c2ca046eda0b52ada18da04521d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2022
ms.locfileid: "68791664"
---
# <a name="create-a-channel-tab-or-group-tab"></a>Erstellen einer Kanalregisterkarte oder Gruppenregisterkarte

Kanal- oder Gruppenregisterkarten stellen Inhalte an Kanäle und Gruppenchats bereit, was dazu beiträgt, Räume für die Zusammenarbeit um dedizierte webbasierte Inhalte zu erstellen.

Stellen Sie sicher, dass Sie über alle [Voraussetzungen](~/tabs/how-to/tab-requirements.md) verfügen, um Ihre Kanal- oder Gruppenregisterkarte zu erstellen.

[!INCLUDE [sdk-include](~/includes/sdk-include.md)]

::: zone pivot="node-java-script"

## <a name="create-a-custom-channel-or-group-tab-with-nodejs"></a>Erstellen einer benutzerdefinierten Kanal- oder Gruppenregisterkarte mit Node.js

1. Installieren Sie an der Eingabeaufforderung die Pakete [Yeoman](https://yeoman.io/) und [gulp-cli](https://www.npmjs.com/package/gulp-cli), indem Sie nach der Installation von **Node.js** den folgenden Befehl eingeben:

    ```cmd
    npm install yo gulp-cli --global
    ```

2. Installieren Sie an der Eingabeaufforderung den Microsoft Teams-App-Generator, indem Sie den folgenden Befehl eingeben:

    ```cmd
    npm install generator-teams --global
    ```

Im Folgenden sind die Schritte zum Erstellen einer Kanal- oder Gruppenregisterkarte aufgeführt:

* [Generieren einer Anwendung mit einer Kanal- oder Gruppenregisterkarte](#generate-your-application-with-a-channel-or-group-tab)
* [Erstellen Ihres App-Pakets](#create-your-app-package)
* [Erstellen und Ausführen Ihrer Anwendung](#build-and-run-your-application)
* [Einrichten eines sicheren Tunnels zu Ihrer Registerkarte](#establish-a-secure-tunnel-to-your-tab)
* [Hochladen Ihrer Anwendung in Microsoft Teams](#upload-your-application-to-teams)

### <a name="generate-your-application-with-a-channel-or-group-tab"></a>Generieren einer Anwendung mit einer Kanal- oder Gruppenregisterkarte

1. Erstellen Sie an der Eingabeaufforderung ein neues Verzeichnis für Ihre Kanal- oder Gruppenregisterkarte.

1. Geben Sie den folgenden Befehl in Ihr neues Verzeichnis ein, um den Microsoft Teams-App-Generator zu starten:

    ```cmd
    yo teams
    ```

1. Stellen Sie Ihre Werte für eine Reihe von Fragen bereit, die vom Microsoft Teams-App-Generator zum Aktualisieren Ihrer `manifest.json` Datei aufgefordert werden:

    ![Screenshot zum Öffnen des Generators](/microsoftteams/platform/assets/images/tab-images/teamsTabScreenshot.PNG)

    <details>
    <summary><b>Reihe von Fragen zum Aktualisieren der Datei "manifest.json"</b></summary>

    * **Wie lautet der Name Ihrer Lösung?**

        Der Lösungsname ist Ihr Projektname. Sie können den vorgeschlagenen Namen annehmen, indem Sie die **EINGABETASTE** drücken.

    * **Wohin möchten Sie die Daten verschieben?**

        Sie befinden sich derzeit in Ihrem Projektverzeichnis. Drücken Sie die **EINGABETASTE**.

    * **Titel Ihres Microsoft Teams App-Projektes?**

        Der Titel ist der Name Ihres App-Pakets und wird im App-Manifest und in der Beschreibung verwendet. Geben Sie einen Titel ein, oder drücken Sie die **EINGABETASTE**, um den Standardnamen zu übernehmen.

    * **Ihr (Firmen)name? (max. 32 Zeichen)**

        Ihr Firmenname kann im App-Manifest verwendet werden. Geben Sie einen Firmennamen ein, oder drücken **Sie die EINGABETASTE**, um den Standardnamen zu übernehmen.

    * **Welche Manifestversion möchten Sie verwenden?**

        Wählen Sie das Standardschema aus.

    * **Schnelle Gerüsterstellung? (J/n)**

        Der Standardwert ist "ja". geben Sie **n** ein, um Ihre Microsoft Partner-ID einzugeben.

    * **Geben Sie Ihre Microsoft Partner-ID ein, sofern Sie über eine verfügen (zum Überspringen leer lassen).**

        Dieses Feld ist nicht erforderlich und darf nur verwendet werden, wenn Sie bereits Teil des [Microsoft Partner-Netzwerks](https://partner.microsoft.com) sind.

    * **Was möchten Sie zu Ihrem Projekt hinzufügen?**

        Wählen Sie **( &ast; ) Eine Registerkarte** aus.

    * **Die URL zum Hosten dieser Lösung?**

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

        Verwenden Sie die Pfeiltasten, um für die Registerkarte **Konfigurierbar** auszuwählen.

    * **Welche Bereiche sollen für Ihre Registerkarte verwendet werden?**

        Zur Auswahl stehen Team oder Gruppenchat.

    * **Benötigen Sie Microsoft Azure Active Directory (Azure AD) SSO-Unterstützung für die Registerkarte?**

        Legen Sie fest, **keine** Microsoft Azure Active Directory (Azure AD)SSO-Unterstützung für die Registerkarte einzuschließen. Der Standardwert ist "ja", geben Sie "**n**" ein.

    * **Soll diese Registerkarte in SharePoint Online zur Verfügung stehen? (Y/n)**

        Geben Sie "**n**" ein.

    </details>

> [!IMPORTANT]
> Die Pfadkomponente **yourDefaultTabNameTab** ist der Wert, den Sie im Generator für **Standardregisterkartenname** eingegeben haben, plus das Wort **Tab**. Beispiel: `DefaultTabName` ist zuerst **MyTab**, dann **/MyTabTab/**.

<!--- TBD: this info seems removed from the main branch.
* A **full color icon** measuring 192 x 192 pixels.
* A **transparent outline icon** measuring 32 x 32 pixels.
* A `manifest.json` file that specifies the attributes of your app.
--->

### <a name="create-your-app-package"></a>Erstellen Ihres App-Pakets

Sie benötigen ein App-Paket, um Ihre Anwendung in Microsoft Teams erstellen und ausführen zu können. Das App-Paket wird über eine gulp-Aufgabe erstellt, welche die `manifest.json`-Datei überprüft und den ZIP-Ordner im Verzeichnis `./package` generiert. Geben Sie an der Eingabeaufforderung den folgenden Befehl ein:

```cmd
gulp manifest
```

### <a name="build-and-run-your-application"></a>Erstellen und Ausführen Ihrer Anwendung

#### <a name="build-your-application"></a>Erstellen Ihrer Anwendung

Geben Sie an der Eingabeaufforderung den folgenden Befehl ein, um Ihre Lösung in den Ordner `./dist` zu transpilieren (transkompilieren):

```cmd
gulp build
```

#### <a name="run-your-application"></a>Ausführen Ihrer Anwendung

1. Geben Sie an der Eingabeaufforderung den folgenden Befehl ein, um einen lokalen Webserver zu starten:

    ```bash
    gulp serve
    ```

1. Geben Sie `http://localhost:3007/<yourDefaultAppNameTab>/` in Ihren Browser ein, um die Startseite Ihrer Anwendung anzuzeigen.

    :::image type="content" source="~/assets/images/tab-images/homePage.png" alt-text="Standardregisterkarte":::

1. Um die Registerkartenkonfigurationsseite anzuzeigen, wechseln Sie zu `http://localhost:3007/<yourDefaultAppNameTab>/config.html`.

    :::image type="content" source="~/assets/images/tab-images/configurationPage.png" alt-text="Konfigurationsseite für Registerkarten":::

### <a name="establish-a-secure-tunnel-to-your-tab"></a>Einrichten eines sicheren Tunnels zu Ihrer Registerkarte

Um einen sicheren Tunnel zu Ihrer Registerkarte einzurichten, beenden Sie den localhost, und geben Sie den folgenden Befehl ein:

```cmd
gulp ngrok-serve
```

> [!IMPORTANT]
> Nachdem Ihre Registerkarte über **ngrok** in Microsoft Teams hochgeladen und erfolgreich gespeichert wurde, können Sie diese in Microsoft Teams anzeigen, bis Ihre Tunnelsitzung endet. Wenn Sie die ngrok-Sitzung neu starten, müssen Sie Ihre App mit der neuen URL aktualisieren.

### <a name="upload-your-application-to-teams"></a>Hochladen Ihrer Anwendung in Teams

1. Wechseln Sie zu Teams, und wählen Sie **Apps**&nbsp;:::image type="content" source="~/assets/images/tab-images/store.png" alt-text="Teams Store"::: aus.
1. Wählen **Sie Apps verwalten** > **App** >  hochladen **Benutzerdefinierte App hochladen** aus.
1. Wechseln Sie zu Ihrem Projektverzeichnis, navigieren Sie zum Ordner **./package**, wählen Sie den ZIP-Ordner des App-Pakets und dann **Öffnen** aus.

    :::image type="content" source="~/assets/images/tab-images/channeltabadded.png" alt-text="Hochgeladene Kanalregisterkarte":::

1. Wählen Sie im Dialogfeld **Hinzufügen** aus. Ihre Registerkarte wird in Microsoft Teams hochgeladen.

    > [!NOTE]
    > Wenn im Dialogfeld **Hinzufügen** nicht angezeigt wird, entfernen Sie den folgenden Code aus dem Manifest des hochgeladenen ZIP-Ordners des App-Pakets. Zippen Sie den Ordner erneut, und laden Sie ihn in Microsoft Teams hoch.
    >
    >```Json
    >"staticTabs": [],
    >"bots": [],
    >"connectors": [],
    >"composeExtensions": [],
    >```

1. Befolgen Sie die Anweisungen zum Hinzufügen einer Registerkarte. Es gibt ein benutzerdefiniertes Konfigurationsdialogfeld für Ihre Kanal- oder Gruppenregisterkarte.
1. Klicken Sie auf **Speichern**, und Ihre Registerkarte wird der Registerkartenleiste des Kanals hinzugefügt.

    :::image type="content" source="~/assets/images/tab-images/channeltabuploaded.png" alt-text="Die hochgeladene Kanalregisterkarte":::

    Nun haben Sie erfolgreich Ihre Kanal- oder Gruppenregisterkarte in Teams erstellt und hinzugefügt.

::: zone-end

::: zone pivot="razor-csharp"

## <a name="create-a-custom-channel-or-group-tab-with-aspnet-core"></a>Erstellen einer benutzerdefinierten Kanal- oder Gruppenregisterkarte mit ASP.NET Core

1. Erstellen Sie an der Eingabeaufforderung ein neues Verzeichnis für Ihr Registerkartenprojekt.

1. Klonen Sie das Beispielrepository mit dem folgenden Befehl in Ihr neues Verzeichnis, oder laden Sie den [Quellcode](https://github.com/OfficeDev/Microsoft-Teams-Samples) herunter, und extrahieren Sie die Dateien:

    ```cmd
    git clone https://github.com/OfficeDev/Microsoft-Teams-Samples.git
    ```

Im Folgenden sind die Schritte zum Erstellen einer Kanal- oder Gruppenregisterkarte aufgeführt:

* [Generieren einer Anwendung mit einer Kanal- oder Gruppenregisterkarte](#generate-your-application-with-a-channel-or-group-tab-1)
* [Einrichten eines sicheren Tunnels zu Ihrer Registerkarte](#establish-a-secure-tunnel-to-your-tab-1)
* [Aktualisieren Ihrer Anwendung](#update-your-application)
* [Erstellen und Ausführen Ihrer Anwendung](#build-and-run-your-application-1)
* [Aktualisieren Ihres App-Pakets über das Entwicklerportal](#update-your-app-package-with-developer-portal)
* [Vorschau ihrer App in Microsoft Teams](#preview-your-app-in-teams)

### <a name="generate-your-application-with-a-channel-or-group-tab"></a>Generieren einer Anwendung mit einer Kanal- oder Gruppenregisterkarte

1. Öffnen Sie Visual Studio, und wählen Sie **Projekt oder Lösung öffnen** aus.

1. Wechseln Sie zum Ordner **Microsoft_Teams-Samples** > **samples** > **tab-channel-group** > **razor-csharp**, und öffnen Sie **channelGroupTab.sln**.

1. Wählen Sie in Visual Studio **F5** oder **Debuggen starten** im Menü **Debuggen** Ihrer Anwendung aus, um zu überprüfen, ob die Anwendung ordnungsgemäß geladen wurde. Wechseln Sie in einem Browser zu den folgenden URLs:

    * `https://localhost:3978/`
    * `https://localhost:3978/privacy`
    * `https://localhost:3978/tou`

<details>
<summary><b>Überprüfen des Quellcodes</b></summary>

#### <a name="startupcs"></a>Startup.cs

Dieses Projekt wurde aus einer leeren Vorlage für ASP.NET Core 3.1-Webanwendungen erstellt, wobei das Kontrollkästchen **Erweitert * Für HTTPS konfigurieren** beim Setup aktiviert ist. Die MVC-Dienste werden von der `ConfigureServices()`-Methode des Frameworks für die Abhängigkeitsinjektion registriert. Außerdem ermöglicht die leere Vorlage nicht die standardmäßige Bereitstellung statischer Inhalte, sodass die Middleware für statische Dateien der Methode `Configure()` mit dem folgenden Code hinzugefügt wird:

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMvc(options => options.EnableEndpointRouting = false);
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

ASP.NET Core behandelt Dateien namens **Index** als Standard- oder Startseite für die Website. Wenn Ihre Browser-URL auf das Stammverzeichnis der Website verweist, wird **Index.cshtml** als Startseite für Ihre Anwendung angezeigt.

#### <a name="tabcs"></a>Tab.cs

Diese C#-Datei enthält eine Methode, die während der Konfiguration von **Tab.cshtml** aufgerufen wird.

#### <a name="appmanifest-folder"></a>AppManifest-Ordner

Dieser Ordner enthält die folgenden erforderlichen App-Paketdateien:

* Ein **Vollfarbsymbol** mit einer Größe von 192 x 192 Pixeln.
* Ein **transparentes Kontursymbol** mit einer Größe von 32 x 32 Pixeln.
* Eine `manifest.json`-Datei, welche die Attribute Ihrer App angibt.

Diese Dateien müssen in einem App-Paket gezippt werden, damit sie beim Hochladen Ihrer Registerkarte in Microsoft Teams verwendet werden können. Wenn ein Benutzer ihre Registerkarte hinzufügen oder aktualisieren möchte, lädt Teams die `configurationUrl` in Ihrem Manifest angegebene, bettet sie in einen IFrame ein und rendert sie auf Ihrer Registerkarte.

#### <a name="csproj"></a>.csproj

Klicken Sie im Visual Studio-Projektmappen-Explorerfenster mit der rechten Maustaste auf das Projekt, und wählen Sie **Projektdatei bearbeiten** aus. Am Ende der Datei sehen Sie den folgenden Code, der Ihren ZIP-Ordner erstellt und aktualisiert, wenn die Anwendung erstellt wird:

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

Führen Sie an der Eingabeaufforderung im Stammverzeichnis Ihres Projektverzeichnisses den folgenden Befehl aus, um einen sicheren Tunnel zu Ihrer Registerkarte einzurichten:

```cmd
ngrok http 3978 --host-header=localhost
```

Stellen Sie sicher, dass die Eingabeaufforderung bei aktivem ngrok ausgeführt wird, und notieren Sie sich die URL.

### <a name="update-your-application"></a>Aktualisieren Ihrer Anwendung

1. Öffnen Sie den Visual Studio-Projektmappen-Explorer, und wechseln Sie zum Ordner **Pages** > **Shared**, öffnen Sie **_Layout.cshtml**, und fügen Sie Folgendes zum <head> Tags-Abschnitt hinzu:

    ```html
    <script src="https://ajax.aspnetcdn.com/ajax/jQuery/jquery-3.4.1.min.js"></script>
    <script src="https://res.cdn.office.net/teams-js/2.2.0/js/MicrosoftTeams.min.js" 
      integrity="sha384yBjE++eHeBPzIg+IKl9OHFqMbSdrzY2S/LW3qeitc5vqXewEYRWegByWzBN/chRh" 
      crossorigin="anonymous" >
    </script>
    ```

    > [!IMPORTANT]
    > Kopieren Sie nicht die `<script src="...">`-URLs von dieser Seite, und fügen Sie sie nicht ein, da sie nicht die neueste Version darstellen. Um die neueste Version des SDK zu erhalten, wechseln Sie immer zu [Microsoft Teams JavaScript-API](https://www.npmjs.com/package/@microsoft/teams-js).

1. Fügen Sie einen Aufruf von `microsoftTeams.app.initialize();` in das `script`-Tag ein.

1. Wechseln Sie in Visual Studio Projektmappen-Explorer zum Ordner **Pages**, und öffnen Sie **Tab.cshtml.**

    In **Tab.cshtml** bietet die Anwendung dem Benutzer zwei Optionen zum Anzeigen der Registerkarte mit einem roten oder grauen Symbol. Die Schaltfläche **Grau auswählen** oder **Rot auswählen** löst `saveGray()` bzw `saveRed()` . legt fest `pages.config.setValidityState(true)`, und aktiviert **Speichern** auf der Konfigurationsseite. Dieser Code teilt Teams mit, dass Sie die Konfiguration der Anforderungen abgeschlossen haben und mit der Installation fortfahren können. Die Parameter von `pages.config.setConfig` sind festgelegt. Schließlich wird `saveEvent.notifySuccess()` aufgerufen, um anzugeben, dass die Inhalts-URL erfolgreich aufgelöst wurde.

1. Aktualisieren Sie die Werte `websiteUrl` und `contentUrl` jeder Funktion mit der HTTPS-ngrok-URL zu Ihrer Registerkarte.

    Ihr Code sollte jetzt Folgendes enthalten, wobei **y8rCgT2b** durch Ihre ngrok-URL ersetzt wurde:

    ```javascript
        
        let saveGray = () => {
            microsoftTeams.pages.config.registerOnSaveHandler((saveEvent) => {
                microsoftTeams.pages.config.setConfig({
                    websiteUrl: `https://y8rCgT2b.ngrok.io`,
                    contentUrl: `https://y8rCgT2b.ngrok.io/gray/`,
                    entityId: "grayIconTab",
                    suggestedDisplayName: "MyNewTab",
                    removeUrl: ""
                });
                saveEvent.notifySuccess();
            });
        }

        let saveRed = () => {
            microsoftTeams.pages.config.registerOnSaveHandler((saveEvent) => {
                microsoftTeams.pages.config.setConfig({
                    websiteUrl: `https://y8rCgT2b.ngrok.io`,
                    contentUrl: `https://y8rCgT2b.ngrok.io/red/`,
                    entityId: "redIconTab",
                    suggestedDisplayName: "MyNewTab",
                    removeUrl: ""
                });
                saveEvent.notifySuccess();
            });
        }
    ```

1. Speichern Sie das aktualisierte **Tab.cshtml**.

### <a name="build-and-run-your-application"></a>Erstellen und Ausführen Ihrer Anwendung

1. Wählen Sie in Visual Studio **F5** oder **Debuggen starten** im Menü **Debuggen** aus.

1. Stellen Sie sicher, dass **ngrok** ordnungsgemäß ausgeführt wird und funktioniert, indem Sie Ihren Browser öffnen und über die ngrok-HTTPS-URL, die in Ihrem Eingabeaufforderungsfenster bereitgestellt wurde, zu Ihrer Inhaltsseite wechseln.

    > [!TIP]
    > Es müssen sowohl Ihre Anwendung in Visual Studio als auch ngrok ausgeführt werden, um die in diesem Artikel beschriebenen Schritte auszuführen. Wenn Sie die Ausführung Ihrer Anwendung in Visual Studio beenden müssen, um daran zu arbeiten, lassen Sie **ngrok** weiterhin aktiv. Sie überwacht das Routing der Anforderung Ihrer Anwendung und setzt es fort, wenn sie in Visual Studio neu gestartet wird. Wenn Sie den ngrok-Dienst neu starten müssen, wird eine neue URL zurückgegeben, und Sie müssen Ihre Anwendung mit der neuen URL aktualisieren.

<!--- TBD: This note seems to be removed from main. Commenting it for now.
> [!NOTE]
> App Studio can be used to edit your `manifest.json` file and upload the completed package to Teams. You can also manually edit the `manifest.json` file. If you do, ensure that you build the solution again to create the `tab.zip` file to upload.
--->

### <a name="update-your-app-package-with-developer-portal"></a>Aktualisieren Ihres App-Pakets über das Entwicklerportal

1. Wechseln Sie zu Teams. Wenn Sie die [webbasierte Version](https://teams.microsoft.com) verwenden, können Sie Ihren Front-End-Code mithilfe der [Entwicklertools](~/tabs/how-to/developer-tools.md) Ihres Browsers überprüfen.

1. Wechseln Sie zum [**Entwicklerportal**](https://dev.teams.microsoft.com/home).

1. Öffnen Sie **Apps**, und wählen Sie **App importieren** aus.

   <!--- TBD: This steps seems to be removed from main now so commenting it for now.

   Select **Import an existing app** in the **Manifest editor** to begin updating the app package for your tab. The source code comes with its own partially complete manifest. The name of your app package is `tab.zip`. It is available from the following path:
   --->

1. Der Name Ihres App-Pakets lautet `tab.zip`. Es ist im folgenden Pfad verfügbar:

    ```bash
    /bin/Debug/netcoreapp3.1/tab.zip
    ```

1. Wählen Sie `tab.zip` aus, und öffnen Sie es im Entwicklerportal.

1. Eine Standard-**App-ID** wird erstellt und im Abschnitt **Allgemeine Informationen** aufgefüllt.

1. Fügen Sie die Kurz- und Langbeschreibung für Ihre App unter **Beschreibungen** hinzu.

1. Fügen Sie in **Entwicklerinformationen** die erforderlichen Details hinzu, und geben Sie unter **Website (muss eine gültige HTTPS-URL sein)** Ihre ngrok-HTTPS-URL ein.

1. Aktualisieren Sie in **App-URLs** die Datenschutzrichtlinie auf `https://<yourngrokurl>/privacy` und die Nutzungsbedingungen auf `https://<yourngrokurl>/tou`, und speichern Sie.

1. Wählen Sie unter **App-Features** **die Option Gruppierungs- und Kanal-App** aus. Aktualisieren Sie die **Konfigurations-URL** mit `https://<yourngrokurl>/tab`, und wählen Sie den **Bereich** Ihrer Registerkarte aus.

1. Wählen Sie **Speichern**.

1. Im Abschnitt "Domänen" müssen Domänen auf Ihren Registerkarten Ihre ngrok-URL ohne das HTTPS-Präfix `<yourngrokurl>.ngrok.io` enthalten.

### <a name="preview-your-app-in-teams"></a>Anzeigen einer Vorschau Ihrer App in Teams

1. Wählen Sie auf der Entwicklerportal-Symbolleiste **Vorschau in Microsoft Teams** aus; das Entwicklerportal informiert Sie, dass Ihre App erfolgreich quergeladen wurde. Die Seite **Hinzufügen** wird für Ihre App in Microsoft Teams angezeigt.

1. Wählen Sie **Zu Team hinzufügen** aus, um die Registerkarte in einem Team einzurichten. Konfigurieren Sie Ihre Registerkarte, und klicken Sie auf **Speichern**. Ihre Registerkarte ist jetzt in Microsoft Teams verfügbar.

    :::image type="content" source="~/assets/images/tab-images/channeltabaspnetuploaded.png" alt-text="Kanalregisterkarte-ASPNET hochgeladen":::

    Nun haben Sie erfolgreich Ihre Kanal- oder Gruppenregisterkarte in Teams erstellt und hinzugefügt.

::: zone-end

::: zone pivot="mvc-csharp"

## <a name="create-a-custom-channel-or-group-tab-with-aspnet-core-mvc"></a>Erstellen einer benutzerdefinierten Kanal- oder Gruppenregisterkarte mit ASP.NET Core MVC

1. Erstellen Sie an der Eingabeaufforderung ein neues Verzeichnis für Ihr Registerkartenprojekt.

1. Klonen Sie das Beispielrepository mit dem folgenden Befehl in Ihr neues Verzeichnis, oder laden Sie den [Quellcode](https://github.com/OfficeDev/Microsoft-Teams-Samples) herunter, und extrahieren Sie die Dateien:

    ```cmd
    git clone https://github.com/OfficeDev/Microsoft-Teams-Samples.git
    ```

Im Folgenden sind die Schritte zum Erstellen einer Kanal- oder Gruppenregisterkarte aufgeführt:

* [Generieren einer Anwendung mit einer Kanal- oder Gruppenregisterkarte](#generate-your-application-with-a-channel-or-group-tab-2)
* [Einrichten eines sicheren Tunnels zu Ihrer Registerkarte](#establish-a-secure-tunnel-to-your-tab-2)
* [Aktualisieren Ihrer Anwendung](#update-your-application-1)
* [Erstellen und Ausführen Ihrer Anwendung](#build-and-run-your-application-2)
* [Aktualisieren Ihres App-Pakets über das Entwicklerportal](#update-your-app-package-with-developer-portal-1)
* [Vorschau ihrer App in Microsoft Teams](#preview-your-app-in-teams-1)

### <a name="generate-your-application-with-a-channel-or-group-tab"></a>Generieren einer Anwendung mit einer Kanal- oder Gruppenregisterkarte

1. Öffnen Sie Visual Studio, und wählen Sie **Projekt oder Lösung öffnen** aus.

1. Wechseln Sie zum Ordner **Microsoft-Teams-Samples** > **samples** > **tab-channel-group** > **mvc-csharp**, und öffnen Sie **ChannelGroupTabMVC.sln**.

1. Wählen Sie in Visual Studio **F5** oder **Debuggen starten** im Menü **Debuggen** Ihrer Anwendung aus, um zu überprüfen, ob die Anwendung ordnungsgemäß geladen wurde. Wechseln Sie in einem Browser zu den folgenden URLs:

    * `https://localhost:3978/`
    * `https://localhost:3978/privacy`
    * `https://localhost:3978/tou`

<details>
<summary><b>Überprüfen des Quellcodes</b></summary>

#### <a name="startupcs"></a>Startup.cs

Dieses Projekt wurde aus einer leeren Vorlage für ASP.NET Core 3.1-Webanwendungen erstellt, wobei das Kontrollkästchen **Erweitert – Für HTTPS konfigurieren** beim Setup aktiviert ist. Die MVC-Dienste werden von der `ConfigureServices()`-Methode des Frameworks für die Abhängigkeitsinjektion registriert. Außerdem ermöglicht die leere Vorlage nicht die standardmäßige Bereitstellung statischer Inhalte, sodass die Middleware für statische Dateien der Methode `Configure()` mit dem folgenden Code hinzugefügt wird:

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMvc(options => options.EnableEndpointRouting = false);
}

public void Configure(IApplicationBuilder app)
{
    app.UseStaticFiles();
    app.UseMvc();
}
```

#### <a name="wwwroot-folder"></a>Webstammordner

In ASP.NET Core sucht die Anwendung im Webstammordner nach statischen Dateien.

#### <a name="appmanifest-folder"></a>Ordner „AppManifest“

Dieser Ordner enthält die folgenden erforderlichen App-Paketdateien:

* Ein **Vollfarbsymbol** mit einer Größe von 192 x 192 Pixeln.
* Ein **transparentes Kontursymbol** mit einer Größe von 32 x 32 Pixeln.
* Eine `manifest.json`-Datei, welche die Attribute Ihrer App angibt.

Diese Dateien müssen in einem App-Paket gezippt werden, damit sie beim Hochladen Ihrer Registerkarte in Microsoft Teams verwendet werden können.

#### <a name="csproj"></a>.csproj

Klicken Sie im Visual Studio-Projektmappen-Explorerfenster mit der rechten Maustaste auf das Projekt, und wählen Sie **Projektdatei bearbeiten** aus. Am Ende der Datei sehen Sie den folgenden Code, der Ihren ZIP-Ordner erstellt und aktualisiert, wenn die Anwendung erstellt wird:

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

**ChannelGroup.cs** stellt ein Nachrichtenobjekt und Methoden dar, die während der Konfiguration von den Controllern aufgerufen werden können.

#### <a name="views"></a>Ansichten

Dies sind die verschiedenen Ansichten in ASP.NET Core MVC:

* Startseite: ASP.NET Core behandelt Dateien namens **Index** als die Standard- oder Startseite für die Website. Wenn ihre Browser-URL auf das Stammverzeichnis der Website verweist, kann **Index.cshtml** als Startseite für Ihre Anwendung angezeigt werden.

* Freigegeben: Das Teilansichtsmarkup **_Layout.cshtml** enthält die gesamte Seitenstruktur der Anwendung und freigegebene visuelle Elemente, die ebenfalls auf die Teams-Bibliothek verweisen.

#### <a name="controllers"></a>Controller

Die Controller verwenden die `ViewBag`-Eigenschaft, um Werte dynamisch in die Ansichten zu übertragen.

</details>

### <a name="establish-a-secure-tunnel-to-your-tab"></a>Einrichten eines sicheren Tunnels zu Ihrer Registerkarte

Führen Sie an der Eingabeaufforderung im Stammverzeichnis Ihres Projektverzeichnisses den folgenden Befehl aus, um einen sicheren Tunnel zu Ihrer Registerkarte einzurichten:

```cmd
ngrok http 3978 --host-header=localhost
```

Stellen Sie sicher, dass die Eingabeaufforderung bei aktivem ngrok ausgeführt wird, und notieren Sie sich die URL.

### <a name="update-your-application"></a>Aktualisieren Ihrer Anwendung

1. Öffnen Sie den Visual Studio-Projektmappen-Explorer, und wechseln Sie zum Ordner **Views** > **Shared**, öffnen Sie **_Layout.cshtml**, und fügen Sie Folgendes zum <head> Tags-Abschnitt hinzu:

    ```html
    <script src="https://ajax.aspnetcdn.com/ajax/jQuery/jquery-3.4.1.min.js"></script>
    <script src="https://res.cdn.office.net/teams-js/2.2.0/js/MicrosoftTeams.min.js" 
      integrity="sha384yBjE++eHeBPzIg+IKl9OHFqMbSdrzY2S/LW3qeitc5vqXewEYRWegByWzBN/chRh" 
      crossorigin="anonymous" >
    </script>
    ```

    > [!IMPORTANT]
    > Kopieren Sie nicht die `<script src="...">`-URLs von dieser Seite, und fügen Sie sie nicht ein, da sie nicht die neueste Version darstellen. Um die neueste Version des SDK zu erhalten, wechseln Sie immer zu [Microsoft Teams JavaScript-API](https://www.npmjs.com/package/@microsoft/teams-js).

1. Fügen Sie einen Aufruf von `microsoftTeams.app.initialize();` in das `script`-Tag ein.

1. Wechseln Sie in Visual Studio Projektmappen-Explorer zum Ordner **Tab**, und öffnen Sie **Tab.cshtml.**

    In **Tab.cshtml** bietet die Anwendung dem Benutzer zwei Optionen zum Anzeigen der Registerkarte mit einem roten oder grauen Symbol. Die Schaltfläche **Grau auswählen** oder **Rot auswählen** löst `saveGray()` bzw `saveRed()` . legt fest `pages.config.setValidityState(true)`, und aktiviert **Speichern** auf der Konfigurationsseite. Dieser Code teilt Teams mit, dass Sie die Konfiguration der Anforderungen abgeschlossen haben und mit der Installation fortfahren können. Die Parameter von `pages.config.setConfig` sind festgelegt. Schließlich wird `saveEvent.notifySuccess()` aufgerufen, um anzugeben, dass die Inhalts-URL erfolgreich aufgelöst wurde.

1. Aktualisieren Sie die Werte `websiteUrl` und `contentUrl` jeder Funktion mit der HTTPS-ngrok-URL zu Ihrer Registerkarte.

    Ihr Code sollte jetzt Folgendes enthalten, wobei **y8rCgT2b** durch Ihre ngrok-URL ersetzt wurde:

    ```javascript

        let saveGray = () => {
            microsoftTeams.pages.config.registerOnSaveHandler((saveEvent) => {
                microsoftTeams.pages.config.setConfig({
                    websiteUrl: `https://y8rCgT2b.ngrok.io`,
                    contentUrl: `https://y8rCgT2b.ngrok.io/gray/`,
                    entityId: "grayIconTab",
                    suggestedDisplayName: "MyNewTab",
                    removeUrl:""
                });
                saveEvent.notifySuccess();
            });
        }
    
        let saveRed = () => {
            microsoftTeams.pages.config.registerOnSaveHandler((saveEvent) => {
                microsoftTeams.pages.config.setConfig({
                    websiteUrl: `https://y8rCgT2b.ngrok.io`,
                    contentUrl: `https://y8rCgT2b.ngrok.io/red/`,
                    entityId: "redIconTab",
                    suggestedDisplayName: "MyNewTab",
                    removeUrl:""
                });
                saveEvent.notifySuccess();
            });
        }
    ```

1. Stellen Sie sicher, dass Sie die aktualisierte Datei **Tab.cshtml** speichern.

### <a name="build-and-run-your-application"></a>Erstellen und Ausführen Ihrer Anwendung

1. Wählen Sie in Visual Studio **F5** oder **Debuggen starten** im Menü **Debuggen** aus.

1. Stellen Sie sicher, dass **ngrok** ordnungsgemäß ausgeführt wird und funktioniert, indem Sie Ihren Browser öffnen und über die ngrok-HTTPS-URL, die in Ihrem Eingabeaufforderungsfenster bereitgestellt wurde, zu Ihrer Inhaltsseite wechseln.

    > [!TIP]
    > Es müssen sowohl Ihre Anwendung in Visual Studio als auch ngrok ausgeführt werden, um die in diesem Artikel beschriebenen Schritte auszuführen. Wenn Sie die Ausführung Ihrer Anwendung in Visual Studio beenden müssen, um daran zu arbeiten, lassen Sie **ngrok** weiterhin aktiv. Sie überwacht das Routing der Anforderung Ihrer Anwendung und setzt es fort, wenn sie in Visual Studio neu gestartet wird. Wenn Sie den ngrok-Dienst neu starten müssen, wird eine neue URL zurückgegeben, und Sie müssen Ihre Anwendung mit der neuen URL aktualisieren.

### <a name="update-your-app-package-with-developer-portal"></a>Aktualisieren Ihres App-Pakets über das Entwicklerportal

1. Wechseln Sie zu Teams. Wenn Sie die [webbasierte Version](https://teams.microsoft.com) verwenden, können Sie Ihren Front-End-Code mithilfe der [Entwicklertools](~/tabs/how-to/developer-tools.md) Ihres Browsers überprüfen.

1. Wechseln Sie zum [**Entwicklerportal**](https://dev.teams.microsoft.com/home).

1. Öffnen Sie **Apps**, und wählen Sie **App importieren** aus.

1. Der Name Ihres App-Pakets lautet **tab.zip**. Es ist im folgenden Pfad verfügbar:

    ```bash
    /bin/Debug/netcoreapp3.1/tab.zip
    ```

1. Wählen Sie **tab.zip** aus, und öffnen Sie es im Entwicklerportal.

1. Eine Standard-**App-ID** wird erstellt und im Abschnitt **Allgemeine Informationen** aufgefüllt.

1. Fügen Sie die Kurz- und Langbeschreibung für Ihre App in **Beschreibungen** hinzu.

1. Fügen Sie in **Entwicklerinformationen** die erforderlichen Details hinzu, und geben Sie unter **Website (muss eine gültige HTTPS-URL sein)** Ihre ngrok-HTTPS-URL ein.

1. Aktualisieren Sie in **App-URLs** die Datenschutzrichtlinie auf `https://<yourngrokurl>/privacy` und die Nutzungsbedingungen auf `https://<yourngrokurl>/tou`, und speichern Sie.

1. Wählen Sie unter **App-Features** **die Option Gruppierungs- und Kanal-App** aus. Aktualisieren Sie die **Konfigurations-URL** mit `https://<yourngrokurl>/tab`, und wählen Sie den **Bereich** Ihrer Registerkarte aus.

1. Wählen Sie **Speichern**.

1. Im Abschnitt "Domänen" müssen Domänen auf Ihren Registerkarten Ihre ngrok-URL ohne das HTTPS-Präfix `<yourngrokurl>.ngrok.io` enthalten.

### <a name="preview-your-app-in-teams"></a>Anzeigen einer Vorschau Ihrer App in Teams

1. Wählen Sie auf der Entwicklerportal-Symbolleiste **Vorschau in Microsoft Teams** aus; das Entwicklerportal informiert Sie, dass Ihre App erfolgreich quergeladen wurde. Die Seite **Hinzufügen** wird für Ihre App in Microsoft Teams angezeigt.

1. Wählen Sie **Zu Team hinzufügen** aus, um die Registerkarte in einem Team einzurichten. Konfigurieren Sie Ihre Registerkarte, und klicken Sie auf **Speichern**. Ihre Registerkarte ist jetzt in Microsoft Teams verfügbar.

    :::image type="content" source="~/assets/images/tab-images/channeltabaspnetuploaded.png" alt-text="Kanalregisterkarte-ASPNET MVC hochgeladen":::

    Nun haben Sie erfolgreich Ihre Kanal- oder Gruppenregisterkarte in Teams erstellt und hinzugefügt.

::: zone-end

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Erstellen einer Inhaltsseite](~/tabs/how-to/create-tab-pages/content-page.md)

## <a name="see-also"></a>Siehe auch

* [Microsoft Teams-Registerkarten](~/tabs/what-are-tabs.md)
* [Erstellen einer persönlichen Registerkarte](~/tabs/how-to/create-personal-tab.md)
* [Registerkarten auf mobilen Geräten](~/tabs/design/tabs-mobile.md)
* [Erstellen von Registerkarten mit adaptiven Karten](~/tabs/how-to/build-adaptive-card-tabs.md)
* [Erstellen einer Seite zum Entfernen](~/tabs/how-to/create-tab-pages/removal-page.md)
* [Hinzufügen einer SharePoint-Seite als Registerkarte in Teams](https://support.microsoft.com/en-us/office/add-a-sharepoint-page-list-or-document-library-as-a-tab-in-teams-131edef1-455f-4c67-a8ce-efa2ebf25f0b)
