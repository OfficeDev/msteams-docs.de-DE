---
title: Erstellen einer Kanal- oder Gruppenregisterkarte
author: laujan
description: Eine Schnellstartanleitung zum Erstellen einer Kanal- und Gruppenregisterkarte mit dem Yeoman-Generator für Microsoft Teams, einschließlich der Überprüfung des Quellcodes mit Codebeispielen.
ms.localizationpriority: medium
ms.topic: quickstart
ms.author: lajanuar
zone_pivot_groups: teams-app-environment
ms.openlocfilehash: 736b8821a7d0f9e1eda35377bc4937e68c035c75
ms.sourcegitcommit: b2f6599e44a418b4cce92f28843b7e013fd6e86d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/06/2022
ms.locfileid: "64686676"
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

Im Folgenden sind die Schritte zum Erstellen einer Kanal- oder Gruppenregisterkarte aufgeführt:

* [Generieren Ihrer Anwendung mit einer Kanal- oder Gruppenregisterkarte](#generate-your-application-with-a-channel-or-group-tab)
* [Erstellen Ihres App-Pakets](#create-your-app-package)
* [Erstellen und Ausführen der Anwendung](#build-and-run-your-application)
* [Einrichten eines sicheren Tunnels auf Ihrer Registerkarte](#establish-a-secure-tunnel-to-your-tab)
* [Hochladen Der Anwendung Teams](#upload-your-application-to-teams)

### <a name="generate-your-application-with-a-channel-or-group-tab"></a>Generieren Ihrer Anwendung mit einer Kanal- oder Gruppenregisterkarte

1. Erstellen Sie an der Eingabeaufforderung ein neues Verzeichnis für Ihre Kanal- oder Gruppenregisterkarte.

1. Geben Sie den folgenden Befehl in Ihr neues Verzeichnis ein, um den Microsoft Teams App-Generator zu starten:

    ```cmd
    yo teams
    ```

1. Stellen Sie Ihre Werte für eine Reihe von Fragen bereit, die von Microsoft Teams App-Generator aufgefordert werden, ihre **Datei manifest.json** zu aktualisieren:

    ![Screenshot zum Öffnen des Generators](/microsoftteams/platform/assets/images/tab-images/teamsTabScreenshot.PNG)

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

        Verwenden Sie die Pfeiltasten, um die Registerkarte **"Konfigurierbar** " auszuwählen.

    * **Welche Bereiche möchten Sie für Ihre Registerkarte verwenden?**

        Sie können ein Team oder einen Gruppenchat auswählen.

    * **Benötigen Sie Microsoft Azure Active Directory (Azure AD) Single Sign-On-Unterstützung für die Registerkarte?**

        Wählen Sie aus, Microsoft Azure Active Directory (Azure AD) Single-Sign-On-Unterstützung für die Registerkarte **nicht** einzuschließen. Der Standardwert ist "Ja", geben Sie **"n**" ein.

    * **Soll diese Registerkarte in SharePoint Online verfügbar sein? (Y/n)**

        Geben Sie **"n**" ein.

    </details>

> [!IMPORTANT]
> Die Pfadkomponente **"yourDefaultTabNameTab** " ist der Wert, den Sie im Generator für den **Standardregisterkartennamen** plus das Wort **Tab** eingegeben haben.
>
> Beispiel: "DefaultTabName" ist **"MyTab"** und " **/MyTabTab/"**

### <a name="create-your-app-package"></a>Erstellen Ihres App-Pakets

Sie müssen über ein App-Paket verfügen, um Ihre Anwendung in Teams erstellen und ausführen zu können. Das App-Paket wird mithilfe einer gulp-Aufgabe erstellt, die die Datei **manifest.json** überprüft und den ZIP-Ordner im Verzeichnis **"./package** " generiert. Geben Sie an der Eingabeaufforderung den folgenden Befehl ein:

```cmd
gulp manifest
```

### <a name="build-and-run-your-application"></a>Erstellen und Ausführen der Anwendung

#### <a name="build-your-application"></a>Erstellen Ihrer Anwendung

Geben Sie an der Eingabeaufforderung den folgenden Befehl ein, um die Lösung in den Ordner **"./dist** " zu transpilieren:

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

### <a name="establish-a-secure-tunnel-to-your-tab"></a>Einrichten eines sicheren Tunnels auf Ihrer Registerkarte

Um einen sicheren Tunnel zu Ihrer Registerkarte einzurichten, beenden Sie den localhost, und geben Sie den folgenden Befehl ein:

```cmd
gulp ngrok-serve
```

> [!IMPORTANT]
> Nachdem Ihre Registerkarte über **ngrok** in Microsoft Teams hochgeladen und erfolgreich gespeichert wurde, können Sie sie in Teams anzeigen, bis Ihre Tunnelsitzung endet. Wenn Sie die ngrok-Sitzung neu starten, müssen Sie Ihre App mit der neuen URL aktualisieren.

### <a name="upload-your-application-to-teams"></a>Hochladen Der Anwendung Teams

1. Wechseln Sie zu Microsoft Teams, und wählen Sie **"Apps**&nbsp; :::image type="content" source="~/assets/images/tab-images/store.png" alt-text="Teams Store&quot; aus":::.
1. Wählen Sie **"Apps verwalten"** und **Hochladen einer benutzerdefinierten App** aus.
1. Wechseln Sie zu Ihrem Projektverzeichnis, navigieren Sie zum Ordner **"./package** ", wählen Sie den ZIP-Ordner des App-Pakets aus, und wählen Sie **"Öffnen**" aus.
    
    :::image type="content" source="~/assets/images/tab-images/channeltabadded.png" alt-text="Registerkarte &quot;Hochgeladener Kanal&quot;" border="true":::

1. Wählen Sie im Dialogfeld **"Hinzufügen"** aus. Ihre Registerkarte wird in Teams hochgeladen.
    
    > [!NOTE]
    > Wenn  **"Hinzufügen"** nicht im Dialogfeld angezeigt wird, entfernen Sie den folgenden Code aus dem Manifest des hochgeladenen Postfachordners des App-Pakets. Zippen Sie den Ordner erneut, und laden Sie ihn in Teams hoch.
    >
    >```Json
    >"staticTabs": [],
    >"bots": [],
    >"connectors": [],
    >"composeExtensions": [],
    >```

1. Folgen Sie den Anweisungen zum Hinzufügen einer Registerkarte. Es gibt ein benutzerdefiniertes Konfigurationsdialogfeld für Ihre Kanal- oder Gruppenregisterkarte.
1. Wählen Sie **"Speichern"** aus, und Ihre Registerkarte wird der Registerkartenleiste des Kanals hinzugefügt.

    :::image type="content" source="~/assets/images/tab-images/channeltabuploaded.png" alt-text="Kanalregisterkarte hochgeladen" border="true":::
    
    Jetzt haben Sie erfolgreich Ihre Kanal- oder Gruppenregisterkarte in Teams erstellt und hinzugefügt.

::: zone-end

::: zone pivot="razor-csharp"

## <a name="create-a-custom-channel-or-group-tab-with-aspnet-core"></a>Erstellen einer benutzerdefinierten Kanal- oder Gruppenregisterkarte mit ASP.NET Core

1. Erstellen Sie an der Eingabeaufforderung ein neues Verzeichnis für Ihr Registerkartenprojekt.

1. Klonen Sie das Beispielrepository mithilfe des folgenden Befehls in Ihr neues Verzeichnis, oder Laden Sie den [Quellcode](https://github.com/OfficeDev/Microsoft-Teams-Samples) herunter, und extrahieren Sie die Dateien:

    ```cmd
    git clone https://github.com/OfficeDev/Microsoft-Teams-Samples.git
    ```

Im Folgenden sind die Schritte zum Erstellen einer Kanal- oder Gruppenregisterkarte aufgeführt:

* [Generieren Ihrer Anwendung mit einer Kanal- oder Gruppenregisterkarte](#generate-your-application-with-a-channel-or-group-tab-1)
* [Einrichten eines sicheren Tunnels auf Ihrer Registerkarte](#establish-a-secure-tunnel-to-your-tab-1)
* [Aktualisieren Ihrer Anwendung](#update-your-application)
* [Erstellen und Ausführen der Anwendung](#build-and-run-your-application-1)
* [Aktualisieren Ihres App-Pakets mit dem Entwicklerportal](#update-your-app-package-with-developer-portal)
* [Vorschau ihrer App in Teams](#preview-your-app-in-teams)

### <a name="generate-your-application-with-a-channel-or-group-tab"></a>Generieren Ihrer Anwendung mit einer Kanal- oder Gruppenregisterkarte

1. Öffnen Sie Visual Studio, und wählen Sie **"Projekt oder Lösung öffnen" aus**.

1. Wechseln Sie zum Ordner "Microsoft-Teams-Samplessamplestab-channel-grouprazor-csharp >  >  > ", und öffnen Sie **"channelGroupTab.sln**".

1. Wählen Sie in Visual Studio **F5** aus, oder wählen Sie im Menü **"Debuggen**" der Anwendung die Option **"Debuggen starten**" aus, um zu überprüfen, ob die Anwendung ordnungsgemäß geladen wurde. Wechseln Sie in einem Browser zu den folgenden URLs:

    * https://localhost:3978/
    * https://localhost:3978/privacy
    * https://localhost:3978/tou

<details>
<summary><b>Überprüfen des Quellcodes</b></summary>

#### <a name="startupcs"></a>Startup.cs

Dieses Projekt wurde aus einer leeren ASP.NET Core 3.1-Webanwendungsvorlage erstellt, bei der das Kontrollkästchen **"Erweitert * Für HTTPS konfigurieren**" beim Setup aktiviert ist. Die MVC-Dienste werden von der Methode des Abhängigkeitsinjektionsframeworks `ConfigureServices()` registriert. Darüber hinaus wird die Bereitstellung statischer Inhalte durch die leere Vorlage nicht standardmäßig aktiviert, sodass die Middleware für statische Dateien der `Configure()` Methode mit dem folgenden Code hinzugefügt wird:

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

#### <a name="tabcs"></a>Tab.cs

Diese C#-Datei enthält eine Methode, die während der Konfiguration von **Tab.cshtml** aufgerufen wird.

#### <a name="appmanifest-folder"></a>AppManifest-Ordner

Dieser Ordner enthält die folgenden erforderlichen App-Paketdateien:

* Ein **Vollfarbsymbol** mit einer Abmessung von 192 x 192 Pixeln.
* Ein **transparentes Gliederungssymbol** mit einer Abmessung von 32 x 32 Pixeln.
* Eine **manifest.json-Datei** , die die Attribute Ihrer App angibt.

Diese Dateien müssen in einem App-Paket gezippt werden, damit Sie Ihre Registerkarte in Teams hochladen können. Wenn ein Benutzer ihre Registerkarte hinzufügen oder aktualisieren möchte, lädt Microsoft Teams die `configurationUrl` in Ihrem Manifest angegebene Datei, bettet sie in einen IFrame ein und rendert sie auf Ihrer Registerkarte.

#### <a name="csproj"></a>.csproj

Klicken Sie im fenster Visual Studio Projektmappen-Explorer mit der rechten Maustaste auf das Projekt, und wählen **Sie "Project Datei bearbeiten**" aus. Am Ende der Datei wird der folgende Code angezeigt, der Ihren ZIP-Ordner erstellt und aktualisiert, wenn die Anwendung erstellt wird:

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

### <a name="establish-a-secure-tunnel-to-your-tab"></a>Einrichten eines sicheren Tunnels auf Ihrer Registerkarte

Führen Sie an der Eingabeaufforderung im Stammverzeichnis ihres Projektverzeichnisses den folgenden Befehl aus, um einen sicheren Tunnel auf Ihrer Registerkarte einzurichten:

```cmd
ngrok http 3978 --host-header=localhost
```

Stellen Sie sicher, dass die Eingabeaufforderung mit ngrok ausgeführt wird, und notieren Sie sich die URL.

### <a name="update-your-application"></a>Aktualisieren Ihrer Anwendung

1. Öffnen Sie Visual Studio Projektmappen-Explorer, wechseln Sie zum Ordner **"****PagesShared** > ", öffnen Sie **_Layout.cshtml**, und fügen Sie Folgendes hinzu: <head> Tags-Abschnitt:

    ```html
    <script src="https://ajax.aspnetcdn.com/ajax/jQuery/jquery-3.4.1.min.js"></script>
    <script src="https://statics.teams.cdn.office.net/sdk/v1.6.0/js/MicrosoftTeams.min.js"></script>
    ```
    
    > [!IMPORTANT]
    > Kopieren Sie die `<script src="...">` URLs von dieser Seite nicht, und fügen Sie sie nicht ein, da sie nicht die neueste Version darstellen. Um die neueste Version des SDK zu erhalten, wechseln Sie immer zu [Microsoft Teams JavaScript-API](https://www.npmjs.com/package/@microsoft/teams-js).
    
1. Fügen Sie einen Aufruf in `microsoftTeams.initialize();` das `script` Tag ein.

1. Wechseln Sie in Visual Studio Projektmappen-Explorer zum Ordner **"Pages**", und öffnen **Sie Tab.cshtml**

    In **Tab.cshtml** stellt die Anwendung dem Benutzer zwei Optionsfelder zum Anzeigen der Registerkarte mit einem roten oder grauen Symbol bereit. Wenn Sie die Schaltfläche "**Grau auswählen**" oder "**Rot auswählen**" auswählen, wird die Schaltfläche "**Speichern**" auf der Konfigurationsseite ausgelöst `saveGray()` bzw`saveRed()`. festgelegt`settings.setValidityState(true)`. Dieser Code teilt Teams mit, dass Sie die Konfigurationsanforderungen erfüllt haben und die Installation fortgesetzt werden kann. Die Parameter von `settings.setSettings` sind festgelegt. Schließlich wird aufgerufen, um anzugeben, `saveEvent.notifySuccess()` dass die Inhalts-URL erfolgreich aufgelöst wurde.

1. Aktualisieren Sie die `websiteUrl` Werte in `contentUrl` jeder Funktion mit der HTTPS-ngrok-URL auf Ihre Registerkarte.

    Ihr Code sollte jetzt Folgendes enthalten **, wobei y8rCgT2b** durch Ihre ngrok-URL ersetzt wird:

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

1. Speichern Sie das aktualisierte **Tab.cshtml**.

### <a name="build-and-run-your-application"></a>Erstellen und Ausführen der Anwendung

1. Wählen Sie in Visual Studio **F5** aus, oder wählen Sie im Menü **"Debuggen**" die Option **"Debuggen starten**" aus.

1. Stellen Sie sicher, dass **ngrok** ordnungsgemäß ausgeführt wird und funktioniert, indem Sie Ihren Browser öffnen und über die ngrok HTTPS-URL zu Ihrer Inhaltsseite wechseln, die in Ihrem Eingabeaufforderungsfenster bereitgestellt wurde.

    > [!TIP]
    > Sie müssen sowohl Ihre Anwendung in Visual Studio als auch ngrok ausführen, um die in diesem Artikel beschriebenen Schritte auszuführen. Wenn Sie die Ausführung Ihrer Anwendung in Visual Studio beenden müssen, um daran zu arbeiten, führen Sie **ngrok weiter** aus. Beim Neustart in Visual Studio wird die Anforderung der Anwendung überwacht und fortgesetzt. Wenn Sie den ngrok-Dienst neu starten müssen, wird eine neue URL zurückgegeben, und Sie müssen Ihre Anwendung mit der neuen URL aktualisieren.

### <a name="update-your-app-package-with-developer-portal"></a>Aktualisieren Ihres App-Pakets mit dem Entwicklerportal

1. Wechseln Sie zu Microsoft Teams. Wenn Sie die [webbasierte Version](https://teams.microsoft.com) verwenden, können Sie Ihren Front-End-Code mithilfe der [Entwicklertools](~/tabs/how-to/developer-tools.md) Ihres Browsers überprüfen.

1. Wechseln Sie zum [**Entwicklerportal**](https://dev.teams.microsoft.com/home).

1. Öffnen Sie **Apps** , und wählen Sie **"App importieren**" aus.

1. Der Name Des App-Pakets ist **tab.zip**. Es ist im folgenden Pfad verfügbar:

    ```bash
    /bin/Debug/netcoreapp3.1/tab.zip
    ```

1. Wählen Sie **tab.zip** aus, und öffnen Sie es im Entwicklerportal.

1. Eine **Standard-App-ID** wird im Abschnitt **"Grundlegende Informationen** " erstellt und aufgefüllt.

1. Fügen Sie die kurz- und lange Beschreibung für Ihre App in **"Beschreibungen" hinzu**.

1. Fügen Sie in **den Entwicklerinformationen** die erforderlichen Details hinzu, und geben Sie auf der **Website (muss eine gültige HTTPS-URL sein)** Ihre ngrok HTTPS-URL an.

1. Aktualisieren Sie in **App-URLs** die Datenschutzrichtlinie und `https://<yourngrokurl>/privacy` die Nutzungsbedingungen, um sie zu `https://<yourngrokurl>/tou` speichern.

1. Wählen Sie **in den App-Features** "Gruppen- und Kanal-App" aus. Aktualisieren Sie die **Konfigurations-URL** mit `https://<yourngrokurl>/tab` der Registerkarte " **Bereich**", und wählen Sie sie aus.

1. Klicken Sie auf **Speichern**.

1. Im Abschnitt "Domänen" müssen Domänen von Ihren Registerkarten Ihre ngrok-URL ohne das HTTPS-Präfix `<yourngrokurl>.ngrok.io`enthalten.

### <a name="preview-your-app-in-teams"></a>Vorschau ihrer App in Teams

1. Wählen Sie **"Vorschau" in Teams** auf der Symbolleiste des Entwicklerportals aus. Das Entwicklerportal informiert Sie darüber, dass Ihre App erfolgreich quergeladen wurde. Die Seite **"Hinzufügen"** wird für Ihre App in Teams angezeigt.

1. Wählen Sie **"Zu Team hinzufügen"** aus, um die Registerkarte in einem Team einzurichten. Konfigurieren Sie Ihre Registerkarte, und wählen Sie **"Speichern" aus**. Ihre Registerkarte ist jetzt in Teams verfügbar.

    :::image type="content" source="~/assets/images/tab-images/channeltabaspnetuploaded.png" alt-text="Kanalregisterkarte ASPNET hochgeladen" border="true":::
    
    Jetzt haben Sie erfolgreich Ihre Kanal- oder Gruppenregisterkarte in Teams erstellt und hinzugefügt.

::: zone-end

::: zone pivot="mvc-csharp"

## <a name="create-a-custom-channel-or-group-tab-with-aspnet-core-mvc"></a>Erstellen einer benutzerdefinierten Kanal- oder Gruppenregisterkarte mit ASP.NET Core MVC

1. Erstellen Sie an der Eingabeaufforderung ein neues Verzeichnis für Ihr Registerkartenprojekt.

1. Klonen Sie das Beispielrepository mithilfe des folgenden Befehls in Ihr neues Verzeichnis, oder Laden Sie den [Quellcode](https://github.com/OfficeDev/Microsoft-Teams-Samples) herunter, und extrahieren Sie die Dateien:

    ```cmd
    git clone https://github.com/OfficeDev/Microsoft-Teams-Samples.git
    ```

Im Folgenden sind die Schritte zum Erstellen einer Kanal- oder Gruppenregisterkarte aufgeführt:

* [Generieren Ihrer Anwendung mit einer Kanal- oder Gruppenregisterkarte](#generate-your-application-with-a-channel-or-group-tab-2)
* [Einrichten eines sicheren Tunnels auf Ihrer Registerkarte](#establish-a-secure-tunnel-to-your-tab-2)
* [Aktualisieren Ihrer Anwendung](#update-your-application-1)
* [Erstellen und Ausführen der Anwendung](#build-and-run-your-application-2)
* [Aktualisieren Ihres App-Pakets mit dem Entwicklerportal](#update-your-app-package-with-developer-portal-1)
* [Vorschau ihrer App in Teams](#preview-your-app-in-teams-1)

### <a name="generate-your-application-with-a-channel-or-group-tab"></a>Generieren Ihrer Anwendung mit einer Kanal- oder Gruppenregisterkarte

1. Öffnen Sie Visual Studio, und wählen Sie **"Projekt oder Lösung öffnen" aus**.

1. Wechseln Sie zum Ordner "Microsoft-Teams-Samplessamplestab-channel-groupmvc-csharp >  >  > ", und öffnen Sie **"ChannelGroupTabMVC.sln**".

1. Wählen Sie in Visual Studio **F5** aus, oder wählen Sie im Menü **"Debuggen**" der Anwendung die Option **"Debuggen starten**" aus, um zu überprüfen, ob die Anwendung ordnungsgemäß geladen wurde. Wechseln Sie in einem Browser zu den folgenden URLs:

    * https://localhost:3978/
    * https://localhost:3978/privacy
    * https://localhost:3978/tou

<details>
<summary><b>Überprüfen des Quellcodes</b></summary>

#### <a name="startupcs"></a>Startup.cs

Dieses Projekt wurde aus einer leeren Vorlage für ASP.NET Core 3.1-Webanwendung erstellt, wobei das Kontrollkästchen **"Erweitert – Für HTTPS konfigurieren**" beim Setup aktiviert ist. Die MVC-Dienste werden von der Methode des Abhängigkeitsinjektionsframeworks `ConfigureServices()` registriert. Darüber hinaus wird die Bereitstellung statischer Inhalte durch die leere Vorlage nicht standardmäßig aktiviert, sodass die Middleware für statische Dateien der `Configure()` Methode mit dem folgenden Code hinzugefügt wird:

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

#### <a name="appmanifest-folder"></a>AppManifest-Ordner

Dieser Ordner enthält die folgenden erforderlichen App-Paketdateien:

* Ein **Vollfarbsymbol** mit einer Abmessung von 192 x 192 Pixeln.
* Ein **transparentes Gliederungssymbol** mit einer Abmessung von 32 x 32 Pixeln.
* Eine **manifest.json-Datei** , die die Attribute Ihrer App angibt.

Diese Dateien müssen in einem App-Paket gezippt werden, damit Sie Ihre Registerkarte in Teams hochladen können.

#### <a name="csproj"></a>.csproj

Klicken Sie im fenster Visual Studio Projektmappen-Explorer mit der rechten Maustaste auf das Projekt, und wählen **Sie "Project Datei bearbeiten**" aus. Am Ende der Datei sehen Sie den folgenden Code, der Ihren ZIP-Ordner erstellt und aktualisiert, wenn die Anwendung erstellt wird:

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

**ChannelGroup.cs** stellt ein Message-Objekt und Methoden dar, die während der Konfiguration von den Controllern aufgerufen werden.

#### <a name="views"></a>Ansichten

Dies sind die verschiedenen Ansichten in ASP.NET Core MVC:

* Startseite: ASP.NET Core behandelt Dateien, die als **Index** bezeichnet werden, als Standard- oder Homepage für die Website. Wenn Ihre Browser-URL auf den Stamm der Website verweist, wird **Index.cshtml** als Startseite für Ihre Anwendung angezeigt.

* Freigegeben: Das Partielle Ansichtsmarkup **_Layout.cshtml** enthält die gesamte Seitenstruktur der Anwendung und freigegebene visuelle Elemente. Sie verweist auch auf die Teams Library.

#### <a name="controllers"></a>Controller

Die Controller verwenden die `ViewBag` Eigenschaft, um Werte dynamisch in die Ansichten zu übertragen.

</details>

### <a name="establish-a-secure-tunnel-to-your-tab"></a>Einrichten eines sicheren Tunnels auf Ihrer Registerkarte

Führen Sie an der Eingabeaufforderung im Stammverzeichnis ihres Projektverzeichnisses den folgenden Befehl aus, um einen sicheren Tunnel auf Ihrer Registerkarte einzurichten:

```cmd
ngrok http 3978 --host-header=localhost
```

Stellen Sie sicher, dass die Eingabeaufforderung mit ngrok ausgeführt wird, und notieren Sie sich die URL.

### <a name="update-your-application"></a>Aktualisieren Ihrer Anwendung

1. Öffnen Sie Visual Studio Projektmappen-Explorer, wechseln Sie zum Ordner **"****ViewsShared** > ", öffnen Sie **_Layout.cshtml**, und fügen Sie Folgendes hinzu: <head> Tags-Abschnitt:

    ```html
    <script src="https://ajax.aspnetcdn.com/ajax/jQuery/jquery-3.4.1.min.js"></script>
    <script src="https://statics.teams.cdn.office.net/sdk/v1.6.0/js/MicrosoftTeams.min.js"></script>
    ```
    
    > [!IMPORTANT]
    > Kopieren Sie die `<script src="...">` URLs von dieser Seite nicht, und fügen Sie sie nicht ein, da sie nicht die neueste Version darstellen. Um die neueste Version des SDK zu erhalten, wechseln Sie immer zu [Microsoft Teams JavaScript-API](https://www.npmjs.com/package/@microsoft/teams-js).
    
1. Fügen Sie einen Aufruf in `microsoftTeams.initialize();` das `script` Tag ein.

1. Wechseln Sie in Visual Studio Projektmappen-Explorer zum Ordner **"Tab"**, und öffnen **Sie "Tab.cshtml"**.

    In **Tab.cshtml** stellt die Anwendung dem Benutzer zwei Optionsfelder zum Anzeigen der Registerkarte mit einem roten oder grauen Symbol bereit. Wenn Sie die Schaltfläche "**Grau auswählen**" oder "**Rot auswählen**" auswählen, wird die Schaltfläche "**Speichern**" auf der Konfigurationsseite ausgelöst `saveGray()` bzw`saveRed()`. festgelegt`settings.setValidityState(true)`. Dieser Code teilt Teams mit, dass Sie die Konfigurationsanforderungen erfüllt haben und die Installation fortgesetzt werden kann. Die Parameter von `settings.setSettings` sind festgelegt. Schließlich wird aufgerufen, um anzugeben, `saveEvent.notifySuccess()` dass die Inhalts-URL erfolgreich aufgelöst wurde. 

1. Aktualisieren Sie die `websiteUrl` Werte in `contentUrl` jeder Funktion mit der HTTPS-ngrok-URL auf Ihre Registerkarte.

    Ihr Code sollte jetzt Folgendes enthalten **, wobei y8rCgT2b** durch Ihre ngrok-URL ersetzt wird:

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

1. Stellen Sie sicher, dass Sie die aktualisierte **Datei "Tab.cshtml"** speichern.

### <a name="build-and-run-your-application"></a>Erstellen und Ausführen der Anwendung

1. Wählen Sie in Visual Studio **F5** aus, oder wählen Sie im Menü **"Debuggen**" die Option **"Debuggen starten**" aus.

1. Stellen Sie sicher, dass **ngrok** ordnungsgemäß ausgeführt wird und funktioniert, indem Sie Ihren Browser öffnen und über die ngrok HTTPS-URL zu Ihrer Inhaltsseite wechseln, die in Ihrem Eingabeaufforderungsfenster bereitgestellt wurde.

    > [!TIP]
    > Sie müssen sowohl Ihre Anwendung in Visual Studio als auch ngrok ausführen, um die in diesem Artikel beschriebenen Schritte auszuführen. Wenn Sie die Ausführung Ihrer Anwendung in Visual Studio beenden müssen, um daran zu arbeiten, führen Sie **ngrok weiter** aus. Beim Neustart in Visual Studio wird die Anforderung der Anwendung überwacht und fortgesetzt. Wenn Sie den ngrok-Dienst neu starten müssen, wird eine neue URL zurückgegeben, und Sie müssen Ihre Anwendung mit der neuen URL aktualisieren.

### <a name="update-your-app-package-with-developer-portal"></a>Aktualisieren Ihres App-Pakets mit dem Entwicklerportal

1. Wechseln Sie zu Microsoft Teams. Wenn Sie die [webbasierte Version](https://teams.microsoft.com) verwenden, können Sie Ihren Front-End-Code mithilfe der [Entwicklertools](~/tabs/how-to/developer-tools.md) Ihres Browsers überprüfen.

1. Wechseln Sie zum [**Entwicklerportal**](https://dev.teams.microsoft.com/home).

1. Öffnen Sie **Apps** , und wählen Sie **"App importieren**" aus.

1. Der Name Des App-Pakets ist **tab.zip**. Es ist im folgenden Pfad verfügbar:

    ```bash
    /bin/Debug/netcoreapp3.1/tab.zip
    ```

1. Wählen Sie **tab.zip** aus, und öffnen Sie es im Entwicklerportal.

1. Eine **Standard-App-ID** wird im Abschnitt **"Grundlegende Informationen** " erstellt und aufgefüllt.

1. Fügen Sie die kurz- und lange Beschreibung für Ihre App in **"Beschreibungen" hinzu**.

1. Fügen Sie in **den Entwicklerinformationen** die erforderlichen Details hinzu, und geben Sie auf der **Website (muss eine gültige HTTPS-URL sein)** Ihre ngrok HTTPS-URL an.

1. Aktualisieren Sie in **App-URLs** die Datenschutzrichtlinie und `https://<yourngrokurl>/privacy` die Nutzungsbedingungen, um sie zu `https://<yourngrokurl>/tou` speichern.

1. Wählen Sie **in den App-Features** "Gruppen- und Kanal-App" aus. Aktualisieren Sie die **Konfigurations-URL** mit `https://<yourngrokurl>/tab` der Registerkarte " **Bereich**", und wählen Sie sie aus.

1. Klicken Sie auf **Speichern**.

1. Im Abschnitt "Domänen" müssen Domänen von Ihren Registerkarten Ihre ngrok-URL ohne das HTTPS-Präfix `<yourngrokurl>.ngrok.io`enthalten.

### <a name="preview-your-app-in-teams"></a>Vorschau ihrer App in Teams

1. Wählen Sie **"Vorschau" in Teams** auf der Symbolleiste des Entwicklerportals aus. Das Entwicklerportal informiert Sie darüber, dass Ihre App erfolgreich quergeladen wurde. Die Seite **"Hinzufügen"** wird für Ihre App in Teams angezeigt.

1. Wählen Sie **"Zu Team hinzufügen"** aus, um die Registerkarte in einem Team einzurichten. Konfigurieren Sie Ihre Registerkarte, und wählen Sie **"Speichern" aus**. Ihre Registerkarte ist jetzt in Teams verfügbar.

    :::image type="content" source="~/assets/images/tab-images/channeltabaspnetuploaded.png" alt-text="Kanalregisterkarte ASPNET MVC hochgeladen" border="true":::
    
    Jetzt haben Sie erfolgreich Ihre Kanal- oder Gruppenregisterkarte in Teams erstellt und hinzugefügt.

::: zone-end

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Erstellen einer Inhaltsseite](~/tabs/how-to/create-tab-pages/content-page.md)

## <a name="see-also"></a>Siehe auch

* [Teams Registerkarten](~/tabs/what-are-tabs.md)
* [Erstellen einer persönlichen Registerkarte](~/tabs/how-to/create-personal-tab.md)
* [Registerkarten auf mobilen Geräten](~/tabs/design/tabs-mobile.md)
* [Erstellen von Registerkarten mit adaptiven Karten](~/tabs/how-to/build-adaptive-card-tabs.md)
* [Erstellen einer Seite zum Entfernen](~/tabs/how-to/create-tab-pages/removal-page.md)
