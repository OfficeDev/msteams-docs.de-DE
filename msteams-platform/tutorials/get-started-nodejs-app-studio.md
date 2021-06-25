---
title: Lernprogramm – Erstellen Ihrer ersten App mit Node.js
description: Erfahren Sie, wie Sie mit Microsoft Teams-Apps mit Node.js beginnen.
keywords: Erste Schritte node.js nodejs App Studio
ms.topic: tutorial
localization_priority: Normal
ms.custom: scenarios:getting-started; languages:JavaScript,Node.js
ms.openlocfilehash: bbb2e50592eaa8a69a2cd9abda6a17ba2aa0e6bc
ms.sourcegitcommit: 6e4d2c8e99426125f7b72b9640ee4a4b4f374401
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/24/2021
ms.locfileid: "53114471"
---
# <a name="build-your-first-microsoft-teams-app-using-nodejs"></a>Erstellen Ihrer ersten Microsoft Teams-App mit Node.js

In diesem Lernprogramm erfahren Sie, wie Sie Ihre erste Microsoft Teams-App mit Node.js erstellen. Außerdem werden Sie durch die folgenden Schritte geführt: 

1. [Vorbereiten der Umgebung](#prepare-environment)
1. [Voraussetzungen abrufen](#GetPrerequisites)
1. [Beispiel herunterladen](#DownloadSample)
1. [Erstellen und Ausführen des Beispiels](#BuildRun)
1. [Hosten der Beispiel-App](#HostSample)
1. [Aktualisieren der Anmeldeinformationen für Ihre gehostete App](#updatecredentials)
1. [Konfigurieren der Registerkarte "App"](#ConfigureTheAppTab)

<a name="prepare-environment"></a>

[!include [prepare your environment](~/includes/prepare-environment.md)]

<a name="GetPrerequisites"></a>

### <a name="download-and-host-your-app"></a>Herunterladen und Hosten Ihrer App

Führen Sie die folgenden Schritte aus, um eine einfache "Hello World"-App in Teams herunterzuladen und zu hosten.

<a name="GetPrerequisites"></a>

## <a name="get-prerequisites"></a>Voraussetzungen abrufen

Zum Abschließen dieses Lernprogramms benötigen Sie die folgenden Tools. Wenn sie noch nicht vorhanden sind, können Sie sie über diese Links installieren.

- [Git](https://git-scm.com/downloads)
- [Node.js und NPM](https://nodejs.org/)
- Rufen Sie einen beliebigen Text-Editor oder eine beliebige IDE ab. Sie können [Visual Studio Code](https://code.visualstudio.com/download) kostenlos installieren und verwenden.

Wenn während der Installation Optionen zum Hinzufügen , und zum PFAD angezeigt `git` `node` `npm` `code` werden, wählen Sie die Optionen aus. 

Stellen Sie sicher, dass die Tools verfügbar sind, indem Sie Folgendes in einem Terminalfenster ausführen:

> [!NOTE]
> Verwenden Sie das Terminalfenster, mit dem Sie auf Ihrer Plattform am besten vertraut sind. Diese Beispiele verwenden Bash (das in Git enthalten ist), aber diese Skripts werden auf den meisten Plattformen ausgeführt.

```bash
$ git --version
git version 2.19.0.windows.1

$ node -v
v8.9.3

$ npm -v
5.5.1

$ gulp -v
CLI version 2.3.0
Local version 4.0.2
```

Möglicherweise haben Sie eine andere Version dieser Anwendungen. Dies sollte kein Problem sein, mit Ausnahme von gulp. Für gulp müssen Sie Version 4.0.0 oder höher verwenden.

Wenn Sie gulp nicht installiert haben (oder die falsche Version installiert haben), führen Sie dies jetzt `npm install gulp` in Ihrem Terminalfenster aus.

Wenn Sie Visual Studio Code installiert haben, können Sie die Installation überprüfen, indem Sie Folgendes ausführen:

```bash
code --version
1.28.2
929bacba01ef658b873545e26034d1a8067445e9
```

Sie können dieses Terminalfenster weiterhin verwenden, um die befehle auszuführen, die in diesem Lernprogramm folgen.

<a name="DownloadSample"></a>

## <a name="download-the-sample"></a>Beispiel herunterladen

Wir haben ein einfaches [Hello, World bereitgestellt!](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-hello-world/nodejs) Beispiel für die ersten Schritte. Führen Sie in einem Terminalfenster den folgenden Befehl aus, um das Beispiel-Repository auf Ihrem lokalen Computer zu klonen:

```bash
git clone https://github.com/OfficeDev/Microsoft-Teams-Samples.git
```

> [!TIP]
> Sie können dieses [Repository verzweigen,](https://github.com/OfficeDev/Microsoft-Teams-Samples) wenn Sie Ihre Änderungen an Ihrem GitHub-Repository für zukünftige Verweise ändern und einchecken möchten. [](https://help.github.com/articles/fork-a-repo/)

<a name="BuildRun"></a>

## <a name="build-and-run-the-sample"></a>Erstellen und Ausführen des Beispiels

Führen Sie nach dem Klonen des Repositorys den Befehl "Verzeichnis ändern" im Terminal aus, um das Verzeichnis in das Beispiel zu ändern:

```bash
cd Microsoft-Teams-Samples/samples/app-hello-world/nodejs/
```

Zum Erstellen des Beispiels müssen Sie alle Abhängigkeiten installieren. Führen Sie dazu den folgenden Befehl aus:

```bash
npm install
```

Es sollte eine Reihe von Abhängigkeiten angezeigt werden, die installiert werden. Nach der Installation können Sie die App mit dem folgenden Befehl ausführen:

```bash
npm start
```

Wenn die Hello-World-App gestartet wird, wird sie `App started listening on port 3333` im Terminalfenster angezeigt.

> [!NOTE]
> Wenn in der obigen Meldung eine andere Portnummer angezeigt wird, liegt dies daran, dass Sie eine PORT-Umgebungsvariable festgelegt haben. Sie können diesen Port weiterhin verwenden oder Ihre Umgebungsvariable auf 3333 ändern.

An diesem Punkt können Sie ein Browserfenster öffnen und zu den folgenden URLs navigieren, um zu überprüfen, ob alle App-URLs geladen werden:

- `http://localhost:3333`
- `http://localhost:3333/hello`
- `http://localhost:3333/first`
- `http://localhost:3333/second`

<a name="HostSample"></a>

## <a name="deploy-your-sample-app"></a>Bereitstellen Ihrer Beispiel-App

Denken Sie daran, dass Apps in Microsoft Teams Webanwendungen sind, die eine oder mehrere Funktionen verfügbar machen. Damit die Teams Plattform Ihre App laden kann, muss Ihre App über das Internet erreichbar sein. Damit Ihre App über das Internet erreichbar ist, müssen Sie ihre App *hosten.*

Für lokale Tests können Sie die App auf Ihrem lokalen Computer ausführen und einen Tunnel mit einem Webendpunkt erstellen. [ngrok](https://ngrok.com) ist ein kostenloses Tool, mit dem Sie genau das tun können. Mit *ngrok* können Sie eine Webadresse wie `https://d0ac14a5.ngrok.io` (diese URL ist nur ein Beispiel) abrufen. Sie können *ngrok* für Ihre Umgebung [herunterladen und installieren.](https://ngrok.com/download) Stellen Sie sicher, dass Sie es einem Speicherort in Ihrer `PATH` hinzufügen.

Nach der Installation können Sie ein neues Terminalfenster öffnen und den folgenden Befehl ausführen, um einen Tunnel zu erstellen. Im Beispiel wird Port 3333 verwendet. Achten Sie daher darauf, ihn hier anzugeben:

```bash
ngrok http 3333 -host-header=localhost:3333
```

*Ngrok* lauscht auf Anforderungen aus dem Internet und leitet sie an Ihre App weiter, die an Port 3333 ausgeführt wird. Sie können dies überprüfen, indem Sie Ihren Browser öffnen und `https://d0ac14a5.ngrok.io/hello` die Hello-Seite Ihrer App laden. Verwenden Sie unbedingt die Von *ngrok* in Ihrer Konsolensitzung angezeigte Weiterleitungsadresse anstelle dieser URL.

> [!NOTE]
> Wenn Sie im [obigen Build](#build-and-run-the-sample) einen anderen Port verwendet und ausgeführt haben, stellen Sie sicher, dass Sie die gleiche Portnummer verwenden, um den *ngrok-Tunnel* einzurichten.
> [!TIP]
> Es empfiehlt sich, *ngrok* in einem anderen Terminalfenster auszuführen, damit es ohne Beeinträchtigung der Knoten-App ausgeführt wird, die Sie später möglicherweise beenden, neu erstellen und erneut ausführen müssen. Die *ngrok-Sitzung* gibt nützliche Debuginformationen in diesem Fenster zurück.

Es gibt eine kostenpflichtige Version von *ngrok,* die persistente Namen zulässt. Wenn Sie die kostenlose Version verwenden, ist Ihre App nur während der aktuellen Sitzung auf Ihrem Entwicklungscomputer verfügbar. Wenn der Computer heruntergefahren wird oder in den Ruhezustand wechselt, ist der Dienst nicht mehr verfügbar. Denken Sie daran, wenn Sie die App für Tests durch andere Benutzer freigeben. Wenn Sie den Dienst neu starten müssen, wird eine neue Adresse zurückgegeben, und Sie müssen jeden Ort aktualisieren, der diese Adresse verwendet.

Notieren Sie sich die URL Ihrer App. Sie benötigen dies später, wenn Sie die App bei Teams über App Studio oder das Entwicklerportal registrieren.

<a name="DeployToTeams"></a>

## <a name="deploy-your-app-to-microsoft-teams"></a>Bereitstellen Ihrer App für Microsoft Teams

An diesem Punkt wird eine App im Internet gehostet, aber Sie haben noch keine Möglichkeit, Teams zu sagen, wo sie gesucht werden soll oder sogar wie Ihre App heißt. Dazu müssen Sie jetzt ein App-Paket erstellen. Dies ist nur eine Textdatei, die das App-Manifest und einige Symbole enthält, die der Teams-Client zum ordnungsgemäßen Anzeigen und Branding Ihrer App verwendet. Sie können dieses App-Paket manuell erstellen oder App Studio oder das Entwicklerportal verwenden, Tools, die in Teams ausgeführt werden, wodurch die Registrierung der App vereinfacht wird. App Studio und das Entwicklerportal sind die empfohlenen Methoden zum Erstellen und Aktualisieren des App-Pakets.

Für beide Methoden benötigen Sie Folgendes:

- Die URL, unter der Ihre App im Internet zu finden ist.
- Symbole, die Teams zum Branding Ihrer App verwenden. Das Beispiel enthält Platzhaltersymbole in "src\static\images". App Studio stellt bei Bedarf auch Standardsymbole bereit.

**Aktualisieren des App-Pakets**

# <a name="app-studio"></a>[App-Studio](#tab/AS)

[!include [Use App Studio to configure the app package](~/includes/get-started/get-started-use-app-studio.md)]

# <a name="developer-portal"></a>[Entwicklerportal](#tab/DP)

**So installieren Sie das Entwicklerportal (Vorschau) in Teams**

1. Wählen Sie unten in der linken Leiste das Symbol **"Apps"** aus, und suchen Sie nach **dem Entwicklerportal.**

    <img width="430px" alt="Screenshot of TDP" src="~/assets/images/Screen1.png"/>

1. Wählen Sie **"Entwicklerportal"** aus, und wählen Sie **"Öffnen"** aus.

    <img width="430px" alt="Screenshot of TDP Open" src="~/assets/images/screen2.png"/>

1. Wählen Sie die Registerkarte "Apps" aus, und wählen Sie **"Vorhandene App importieren"** aus.

    <img width="430px" alt="Screenshot of import app in tdp" src="~/assets/images/screen3.png"/>

1. Wählen Sie **"Hello World"** aus, und wählen Sie **"Importieren"** aus. Die **Hello World-App** wird im Entwicklerportal importiert. 

    Sie können Ihre App über das Teams Entwicklerportal konfigurieren. Das Manifest befindet sich unter "Verteilen". Sie können das Manifest verwenden, um Funktionen, erforderliche Ressourcen und andere wichtige Attribute für Ihre App zu konfigurieren. Weitere Informationen zum Konfigurieren Ihrer App mithilfe des Entwicklerportals finden Sie [unter Teams Developer Portal.](../concepts/build-and-test/teams-developer-portal.md)

    <img width="430px" alt="Screenshot of configure tdp" src="~/assets/images/Screen4.png"/>

---
<a name="updatecredentials"></a>

## <a name="update-the-credentials-for-your-hosted-app"></a>Aktualisieren der Anmeldeinformationen für Ihre gehostete App

Für die Beispiel-App müssen die folgenden Umgebungsvariablen auf die Werte festgelegt werden, die Sie zuvor notieren:

```
MICROSOFT_APP_ID=<YOUR BOT'S APP ID>
MICROSOFT_APP_PASSWORD=<YOUR BOT'S PASSWORD>
WEBSITE_NODE_DEFAULT_VERSION=8.9.4
```

Wie Sie dies tun, hängt davon ab, wie Sie Ihre App gehostet haben. Wichtig bei der Verwendung von Umgebungsvariablen ist, dass diese Werte Teil Ihrer Umgebung sind. Sie können über den Code für Ihre App aufgerufen werden, werden jedoch nicht für Dritte verfügbar gemacht, die möglicherweise die Dateien untersuchen, aus denen Ihre Website besteht.

Wenn Sie die App mit ngrok ausführen, müssen Sie einige lokale Umgebungsvariablen einrichten. Es gibt viele Möglichkeiten, dies zu tun. Wenn Sie jedoch Visual Studio Code verwenden, ist es am einfachsten, eine [Startkonfiguration](https://code.visualstudio.com/Docs/editor/debugging#_launch-configurations)hinzuzufügen:

``` 
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

MICROSOFT_APP_ID und MICROSOFT_APP_PASSWORD ist die ID bzw. das Kennwort für Ihren Bot.
NODE_DEBUG zeigen Ihnen, was in Ihrem Bot in der Visual Studio Code Debugkonsole passiert.
NODE_CONFIG_DIR verweist auf das Verzeichnis im Stammverzeichnis des Repositorys (wenn die App lokal ausgeführt wird, wird sie standardmäßig im Ordner "src" nach ihr gesucht).

> [!Note]
> Wenn Sie npm nicht weiter oben im Lernprogramm beendet haben, müssen Sie diese ausführen, `npm stop` damit Visual Studio Code die Startkonfigurationsvariablen korrekt abrufen können.

<a name="ConfigureTheAppTab"></a>

## <a name="configure-the-app-tab"></a>Konfigurieren der Registerkarte "App"

Nachdem Sie die App in einem Team installiert haben, müssen Sie sie so konfigurieren, dass Inhalte angezeigt werden. Wechseln Sie zu einem Kanal im Team, und klicken Sie auf die Schaltfläche **"+",** um eine neue Registerkarte hinzuzufügen. Sie können dann `Hello World` aus der **Registerkartenliste hinzufügen** auswählen. Anschließend wird ihnen ein Konfigurationsdialogfeld angezeigt. In diesem Dialogfeld können Sie auswählen, welche Registerkarte in diesem Kanal angezeigt werden soll. Nachdem Sie die Registerkarte ausgewählt und auf **"Speichern"** geklickt haben, wird die `Hello World` Registerkarte angezeigt, die mit der ausgewählten Registerkarte geladen wurde:

<img width="430px" alt="Screenshot of configure" src="~/assets/images/samples-hello-world-tab-configure.png"/>

### <a name="test-your-bot-in-teams"></a>Testen Ihres Bots in Teams

Sie können jetzt mit dem Bot in Teams interagieren. Wählen Sie einen Kanal im Team aus, in dem Sie Ihre App registriert haben, und geben Sie `@your-bot-name` dann Ihre Nachricht ein. Dies wird als **\@ Erwähnung bezeichnet.** Jede Nachricht, die Sie an den Bot senden, wird als Antwort an Sie gesendet:

<img width="450px" alt="Bot responses" src="~/assets/images/samples-hello-world-bot.png"/>

<a name="ComposeRichMessages"></a>

### <a name="test-your-messaging-extension"></a>Testen Der Messaging-Erweiterung

Um Ihre Messaging-Erweiterung zu testen, können Sie auf die drei Punkte unterhalb des Eingabefelds in der Unterhaltungsansicht klicken. Ein Menü wird mit der **App "Hello World"** angezeigt. Wenn Sie darauf klicken, wird eine Reihe zufälliger Texte angezeigt. Sie können einen beliebigen auswählen, und er wird in Ihre Unterhaltung eingefügt:

<img width="430px" alt="Messaging extension menu" src="~/assets/images/samples-hello-world-messaging-extensions-menu1.png" />

<img width="430px" alt="Messaging extension result" src="~/assets/images/samples-hello-world-messaging-extensions-result1.png" />

Wählen Sie einen der zufälligen Texte aus, und unten sehen Sie eine Karte, die formatiert und zum Senden mit Ihrer eigenen Nachricht bereit ist:

<img width="430px" alt="Messaging extension send" src="~/assets/images/samples-hello-world-messaging-extensions-send.png" />

 ## <a name="see-also"></a>Siehe auch

* [Übersicht über Lernprogramme](code-samples.md)
* [Codebeispiele](https://github.com/OfficeDev/Microsoft-Teams-Samples)