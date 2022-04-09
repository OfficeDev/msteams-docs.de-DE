---
title: Bereitstellen Ihrer ersten App mithilfe von Node.js in App Studio
description: Erfahren Sie, wie Sie Microsoft Teams Apps mit Node.js in App Studio bereitstellen.
keywords: Erste Schritte node.js App Studio
ms.custom: scenarios:getting-started; languages:ASP,Node.js
ms.localizationpriority: medium
ms.topic: tutorial
ms.date: 11/09/2018
ms.openlocfilehash: 7f423cfd33fdca9d40f2adfe32b59ace26d39adc
ms.sourcegitcommit: 61003a14e8a179e1268bbdbd9cf5e904c5259566
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2022
ms.locfileid: "64737223"
---
# <a name="update-nodejs-app-package-in-app-studio"></a>Aktualisieren Node.js App-Pakets in App Studio

> [!TIP]
> **Testen Sie das Entwicklerportal**: App Studio hat sich weiterentwickelt. Konfigurieren, verteilen und verwalten Sie Ihre Teams-Apps mit dem neuen [Entwicklerportal](https://dev.teams.microsoft.com/).

App Studio ist eine Teams App, die Sie aus dem Teams Store installieren können. Es vereinfacht die Erstellung und Registrierung einer App.

Führen Sie die folgenden Schritte aus, um das App-Paket zu aktualisieren:

1. Um App Studio in Teams zu installieren, wählen Sie unten in der linken Leiste das **Symbol "Apps**" aus, und suchen Sie nach **App Studio**:

    <img  width="450px" alt="Finding App Studio in the Store View" src="~/assets/images/get-started/searchforAppStudio.png"/>

1. Wählen Sie die **App Studio-Kachel** und dann **"Installieren**" aus. Das App Studio ist installiert:

    <img  width="450px" alt="Installing App Studio" src="~/assets/images/get-started/InstallingAppStudio.png"/>

1. Um das App-Paket für Ihre Teams-App zu erstellen, wählen Sie die Registerkarte "**Manifest-Editor**" in **App Studio** aus:

    <img  width="450px" alt="App Studio" src="~/assets/images/get-started/AppStudio.png"/>

    Das Beispiel enthält ein eigenes Manifest und ist so konzipiert, dass beim Erstellen des Projekts ein App-Paket erstellt wird. Auf Node.js erfolgt dies durch Eingabe `gulp` an der Befehlszeile im Stammverzeichnis des Projekts.

    Sie können das App-Paket auf Node.js erstellen, indem Sie in der Befehlszeile im Stammverzeichnis des Projekts eingeben `gulp` .

    ```bash
    $ gulp
    [13:39:27] Using gulpfile ~\documents\github\msteams-samples-hello-world-nodejs\gulpfile.js
    [13:39:27] Starting 'clean'...
    [13:39:27] Starting 'generate-manifest'...
    [13:39:27] Finished 'generate-manifest' after 11 ms
    [13:39:27] Finished 'clean' after 21 ms
    [13:39:27] Starting 'default'...
    Build completed. Output in manifest folder
    [13:39:27] Finished 'default' after 62 μs
    ```

    Der Name des generierten App-Pakets lautet `helloworldapp.zip`. Sie können nach dieser Datei suchen, wenn der Speicherort in dem von Ihnen verwendeten Tool nicht eindeutig ist.

1. Um dieses App-Paket zu ändern, wählen Sie im **Manifest-Editor** "**Vorhandene App importieren**" aus:

    <img  width="450px" alt="Importing an existing app" src="~/assets/images/get-started/Importinganapp.png"/>

1. Wählen Sie die **kachel Hallo Welt** für Ihre neu importierte App aus:

    <img  width="450px" alt="Newly imported app view" src="~/assets/images/get-started/HelloWorldappdetails.png"/>

    Die folgende Abbildung zeigt das importierte App-Paket in App Studio:

    <img  width="450px" alt="Importing the app package" src="~/assets/images/get-started/Importinganapp2.png"/>

    Auf der linken Seite des Manifest-Editors befindet sich eine Liste der Schritte. Auf der rechten Seite befindet sich eine Liste der Eigenschaften, die für jeden Schritt ausgefüllt werden müssen. Während Sie mit einer Beispiel-App begonnen haben, sind viele der Informationen bereits abgeschlossen. Mit den nächsten Schritten können Sie die Eigenschaften der Hallo Welt-App aktualisieren.

## <a name="app-details"></a>App-Details

Wählen Sie unter **"Details**" **die App-Details** aus. Wählen Sie die Schaltfläche **"Generieren** " aus, um eine neue App-ID zu erstellen.

Ihre neue App-ID ähnelt `2322041b-72bf-459d-b107-f4f335bc35bd`.

Durchlaufen Sie die App-Details im rechten Bereich, einschließlich **Entwicklerinformationen** und **Brandingdetails** . Diese Details sind wichtig, wenn Sie eine neue App für die Verteilung schreiben.

## <a name="tabs"></a>Registerkarten

Es ist einfach, einer Teams App Registerkarten hinzuzufügen. Die Beispiel-App unterstützt bereits mehrere Registerkarten, die Sie aktivieren können.

### <a name="team-tab"></a>Registerkarte "Team"

Ihre App kann nur eine Teamregisterkarte haben:

<img  width="450px" alt="Adding a Teams tab" src="~/assets/images/get-started/TeamTab.png"/>

In diesem Beispiel wird die Konfigurationsseite auf der Registerkarte "Team" angezeigt. Wählen Sie das **Symbol ...** der **Registerkartenkonfigurations-URL** und dann im Dropdownmenü " **Bearbeiten** " aus. Ändern Sie die URL so `https://yourteamsapp.ngrok.io/configure` , dass `yourteamsapp.ngrok.io` sie durch die URL ersetzt werden muss, die Sie beim Hosten Ihrer App verwendet haben.

### <a name="personal-tabs"></a>Persönliche Registerkarten

Ihre App kann bis zu 16 Registerkarten haben, einschließlich der Registerkarte "Team".

Persönliche Registerkarten unterscheiden sich von der Registerkarte "Team". **Die Registerkarte "Hello"** ist bereits in der Liste der persönlichen Registerkarten mit einem Platzhalterwert `com.contoso.helloworld.hellotab`aufgeführt. Wählen Sie das **Symbol ...** der **Registerkartenkonfigurations-URL** und dann im Dropdownmenü " **Bearbeiten** " aus. Das folgende Dialogfeld wird angezeigt:

<img  width="450px" alt="Adding a personal tab dialog" src="~/assets/images/get-started/PersonalTab.png"/>

Aktualisieren Sie die folgenden Felder mit Ihrer App-URL:

* Ändern des **Felds "Inhalts-URL** " in `https://yourteamsapp.ngrok.io/hello`
* Ändern des **Felds "Website-URL** " in `https://yourteamsapp.ngrok.io/hello`

Ersetzen Sie `yourteamsapp.ngrok.io` sie durch die URL, die Sie beim Hosten Ihrer App verwendet haben.

#### <a name="bots"></a>Bots

Das Hinzufügen der Bots-Funktionalität zu Ihrer App ist ganz einfach. Die  Hallo Welt-Beispiel-App enthält bereits einen Bot als Teil des Beispiels, Sie müssen ihn jedoch bei Microsoft registrieren:

<img  width="450px" alt="Adding a bot" src="~/assets/images/get-started/Bots.png"/>

Dem Bot, der aus dem Beispiel importiert wurde, ist keine App-ID zugeordnet. Sie müssen einen neuen Bot erstellen, damit App Studio eine neue App-ID erstellen und bei Microsoft registrieren kann.

> [!NOTE]
> Die von App Studio für den Bot erstellte App-ID unterscheidet sich von der für die App erstellten App-ID. Jeder Bot in einer App benötigt eine eigene App-ID.

Führen Sie die folgenden Schritte aus, um Ihren Bot einzurichten:

1. Wählen Sie " **Löschen"** neben dem importierten Bot in der Botliste aus. Jetzt gibt es keine Bots mehr, die angezeigt werden können.
1. Wählen Sie **"Einrichten** " aus, um das Dialogfeld " **Bot einrichten** " anzuzeigen.

    <img  width="450px" alt="Adding a bot dialog" src="~/assets/images/get-started/Setupbot.png"/>

1. Fügen Sie den Botnamen **"Contoso Bot** " hinzu, und aktivieren Sie alle drei Kontrollkästchen unter **"Bereich"**.
1. Wählen Sie **"Speichern"** aus, um das Dialogfeld zu beenden. App Studio registriert Ihren Bot bei Microsoft und zeigt Ihren neuen Bot in der Botliste an.
1. Öffnen Sie nun eine Textdatei im Editor, und kopieren Sie ihre neue Bot-ID, und fügen Sie sie ein.
1. Klicken Sie auf **"Neues Kennwort generieren"**, und notieren Sie sich das Kennwort in derselben Textdatei, die Sie ihrer Bot-App-ID notiert haben.
1. Aktualisieren Sie die **Bot-Endpunktadresse** auf `https://yourteamsapp.ngrok.io/api/messages`und ersetzen `yourteamsapp.ngrok.io` Sie sie durch die URL, die Sie beim Hosten Ihrer App verwendet haben.
1. Speichern Sie nun Ihre Textdatei, da Sie die Informationen aus der Datei zu Ihrer gehosteten App hinzufügen müssen, um eine sichere Kommunikation mit Ihrem Bot zu ermöglichen.

#### <a name="messaging-extensions"></a>Messaging-Erweiterungen

MitHilfe von Messaging-Erweiterungen können Benutzer Informationen von Ihrem Dienst anfordern und diese Informationen veröffentlichen. Die Informationen werden in Form von Karten in die Kanalunterhaltung gepostet. Messaging-Erweiterungen werden am unteren Rand des Felds zum Verfassen angezeigt.

Führen Sie die folgenden Schritte aus, um Ihre Messaging-Erweiterung einzurichten:

1. Wählen Sie im linken Bereich von App Studio unter **"Funktionen**" die Option "**Messaging-Erweiterungen**" aus, um die Messaging-Erweiterung zu konfigurieren:

    <img  width="450px" alt="Adding a messaging extension" src="~/assets/images/get-started/Messagingextensions.png"/>

    Die Beispiel-Messaging-Erweiterung ist im Bereich " **Messaging-Erweiterungen** " aufgeführt.

1. Wählen Sie **"Löschen"** aus, um die Messaging-Erweiterung zu entfernen, wählen Sie **"Einrichten**" aus, und führen Sie die gleichen Schritte aus, die für [Bots](#bots) verwendet werden. Das Dialogfeld " **Messaging-Erweiterung** " wird angezeigt.
1. Wählen Sie die Registerkarte **"Vorhandenen Bot verwenden** " und **dann "Aus einem meiner vorhandenen Bots auswählen" aus**.
1. Wählen Sie den Bot aus, den Sie im Dropdownmenü erstellt haben. Fügen Sie einen **Bot-Namen** hinzu, und wählen Sie **"Speichern"** aus, um das Dialogfeld zu schließen.
1. Wählen Sie im Abschnitt **"Befehl** " die Option **"Hinzufügen"** aus. Um einen suchbasierten Befehl hinzuzufügen, wählen Sie die Option **"Benutzern erlauben, Ihren Dienst nach Informationen abzufragen" aus, und fügen Sie diese in eine Nachrichtenoption ein** .
1. Geben Sie im Dialogfeld " **Neuer Befehl** " die folgenden Werte ein:

    Unter **"Neu" befehl**:

    * **Befehls-ID**: Geben Sie zufälligen Text ein.
    * **Titel**: Geben Sie einen zufälligen Titel ein.
    * **Beschreibung**: Geben Sie eine zufällige Beschreibung ein.

    Unter **Parameter**:

    * **Name**: Geben Sie den Parameternamen ein.
    * **Titel**: Geben Sie den Kartentitel ein.
    * **Beschreibung**: Geben Sie die Kartenbeschreibung ein.

1. Nachdem Sie die Informationen eingegeben haben, wählen Sie **"Speichern"** aus, um das Dialogfeld zu schließen.

#### <a name="register-your-app-in-teams"></a>Registrieren Der App in Teams

Nachdem Sie die Details Ihrer App eingegeben haben, führen Sie die folgenden Schritte aus, um Ihre App in Teams zu registrieren:

1. Verwenden Sie **"Testen und Verteilen** von App Studio", um Ihre App in Teams zu installieren.
1. Aktualisieren Sie Ihre gehostete Anwendung mit der App-ID und dem Kennwort für Ihren Bot. Verwenden Sie für die Beispiel-App die gleiche App-ID und dasselbe Kennwort für Bot- und Messaging-Erweiterungen.
1. Wählen Sie " **Testen" aus, und verteilen**  Sie sie unter **"Fertig stellen** " im linken Bereich von App Studio:

    <img  width="450px" alt="Testing your app" src="~/assets/images/get-started/Testanddistribute.png"/>

1. Um Ihre App in Teams hochzuladen, wählen Sie unter **"Testen und Verteilen**" die Schaltfläche "**Installieren**" aus:

    <img  width="450px" alt="Adding a messaging extension dialog" src="~/assets/images/get-started/InstallingHelloWorld.png"/>

    > [!NOTE]
    > Wenn Sie die App nicht querladen können, überprüfen Sie, ob Sie das [Hochladen benutzerdefinierter Apps aktiviert](../get-started/get-started-dotnet-app-studio.md#enable-sideloading-option) haben.

1. Wählen Sie im Abschnitt **"Zu einem Team hinzufügen"** das **Suchfeld** aus, und wählen Sie ein Team aus, um die Beispiel-App hinzuzufügen. Sie können ein spezielles Team für Tests einrichten.
1. Wählen Sie unten im Dialogfeld die Schaltfläche " **Installieren** " aus.

    Ihre App ist jetzt in Teams verfügbar. Der Bot und die Messaging-Erweiterung funktionieren jedoch erst, wenn Sie die Umgebung der gehosteten Anwendungen mit den App-IDs und Kennwörtern aktualisieren.

    <img  width="450px" alt="The finished app" src="~/assets/images/get-started/Finishedhelloworld.png"/>

## <a name="update-the-credentials-for-your-hosted-app"></a>Aktualisieren der Anmeldeinformationen für Ihre gehostete App

Für die Beispiel-App müssen die folgenden Umgebungsvariablen auf die Werte festgelegt werden, die Sie zuvor notieren:

```
MICROSOFT_APP_ID=<YOUR BOT'S APP ID>
MICROSOFT_APP_PASSWORD=<YOUR BOT'S PASSWORD>
WEBSITE_NODE_DEFAULT_VERSION=8.9.4
```

Die Umgebungsvariablen sind Teil Ihrer Umgebung. Nur der Code Ihrer App kann darauf zugreifen. Sie sind keinem Dritten offengelegt.

Wenn Sie die App mit ngrok ausführen, müssen Sie lokale Umgebungsvariablen einrichten. Sie können Visual Studio Code verwenden, um eine [Startkonfiguration](https://code.visualstudio.com/Docs/editor/debugging#_launch-configurations) hinzuzufügen:

```json
{
    "type": "node",
    "request": "launch",
    "name": "Launch - Teams Debug",
    "program": "${workspaceRoot}/src/app.js",
    "cwd": "${workspaceFolder}/src",
    "env": {
        "BASE_URI": "https://yourNgrokURL.ngrok.io",
        "MICROSOFT_APP_ID": "00000000-0000-0000-0000-000000000000",
        "MICROSOFT_APP_PASSWORD": "yourBotAppPassword",
        "NODE_DEBUG": "botbuilder",
        "SUPPRESS_NO_CONFIG_WARNING": "y",
        "NODE_CONFIG_DIR": "../config"
    }
}
```

Dabei gilt:

* Die Autorisierungsanmeldeinformationen für Ihren Bot lauten wie folgt:
  * MICROSOFT_APP_ID ist ID
  * MICROSOFT_APP_PASSWORD ist ein Kennwort
* NODE_DEBUG zeigen, was in Ihrem Bot in der Visual Studio Code Debugkonsole geschieht
* NODE_CONFIG_DIR verweist auf das Verzeichnis im Stammverzeichnis des Repositorys (standardmäßig wird bei lokaler Ausführung der App nach dem Stammverzeichnis im `src` Ordner gesucht).

> [!Note]
> Wenn Sie npm nicht von oben im Lernprogramm beendet haben, müssen Sie ausgeführt `npm stop` werden, damit Visual Studio Code ihre Startkonfigurationsvariablen ordnungsgemäß abholen können.

<a name="ConfigureTheAppTab"></a>

## <a name="test-the-app-capabilities-in-teams"></a>Testen der App-Funktionen in Teams

Nachdem Sie die App in Teams installiert haben, müssen Sie sie so konfigurieren, dass Inhalte angezeigt werden.

### <a name="test-your-tab-in-teams"></a>Testen Der Registerkarte in Teams

1. Wechseln Sie zu einem Kanal in Teams, und wählen Sie die Schaltfläche **"+"** aus, um eine neue Registerkarte hinzuzufügen.
1. Sie können dann aus der **Registerkartenliste "Hinzufügen"** auswählen`Hello World`.
1. Wählen Sie im Konfigurationsdialogfeld die Registerkarte aus, die im Kanal angezeigt werden soll. Wählen Sie dann **"Speichern"** aus.

Sie können die Registerkarte sehen, die `Hello World` mit der ausgewählten Registerkarte geladen wurde:

<img width="430px" alt="Screenshot of configure" src="~/assets/images/samples-hello-world-tab-configure.png"/>

### <a name="test-your-bot-in-teams"></a>Testen Ihres Bots in Teams

Sie können jetzt mit dem Bot in Teams interagieren. Wählen Sie einen Kanal im Team aus, in dem Sie Ihre App registriert haben, und geben `@your-bot-name`Sie , gefolgt von Ihrer Nachricht, ein. Diese Art von Nachricht wird als Erwähnung bezeichnet **\@**. Jede Nachricht, die Sie an den Bot senden, wird als Antwort zurück an Sie gesendet:

<img width="450px" alt="Bot responses" src="~/assets/images/samples-hello-world-bot.png"/>

<a name="ComposeRichMessages"></a>

### <a name="test-your-messaging-extension"></a>Testen Ihrer Messaging-Erweiterung

So testen Sie Ihre Messaging-Erweiterung:

1. Wählen Sie die drei Punkte unterhalb des Eingabefelds in der Unterhaltungsansicht aus. Ein Menü mit der **App "Hallo Welt"** wird angezeigt.
1. Wählen Sie das Menü aus. Eine Reihe zufälliger Texte wird angezeigt. Sie können einen der zufälligen Texte auswählen, der in Ihre Unterhaltung eingefügt wird.

    <img width="430px" alt="Messaging extension menu" src="~/assets/images/samples-hello-world-messaging-extensions-menu1.png" />

    <img width="430px" alt="Messaging extension result" src="~/assets/images/samples-hello-world-messaging-extensions-result1.png" />

1. Wählen Sie einen der zufälligen Texte aus. Die formatierte Karte erscheint bereit zum Senden mit Ihrer eigenen Nachricht, die unten enthalten ist:

    <img width="430px" alt="Messaging extension send" src="~/assets/images/samples-hello-world-messaging-extensions-send.png" />

| &nbsp; | &nbsp; |
|:--- | ---:|
|[Back](get-started-overview.md) | &nbsp; |
|
