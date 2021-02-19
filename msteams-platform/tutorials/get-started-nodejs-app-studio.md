---
title: Lernprogramm – Erstellen Ihrer ersten App mithilfe Node.js
description: Erfahren Sie, wie Sie mit dem Erstellen von Microsoft Teams-Apps mit Node.js.
keywords: Erste Schritte node.js nodejs App Studio
ms.topic: tutorial
ms.custom: scenarios:getting-started; languages:JavaScript,Node.js
ms.openlocfilehash: 61be1056a07952c6cf166dbe183fa257ceaf7227
ms.sourcegitcommit: 6ff8d1244ac386641ebf9401804b8df3854b02dc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/18/2021
ms.locfileid: "50294761"
---
# <a name="create-your-first-microsoft-teams-app-using-nodejs"></a>Erstellen Sie Ihre erste Microsoft Teams-App mithilfe Node.js

Dieses Lernprogramm hilft Ihnen, mit dem Erstellen einer Microsoft Teams-App mithilfe von Node.js.

[!include [prepare your environment](~/includes/prepare-environment.md)]

<a name="DownloadAndHost"></a>

## <a name="download-and-host-your-app"></a>Herunterladen und Hosten Ihrer App

Führen Sie die folgenden Schritte aus, um eine einfache "Hello World"-App in Teams herunterzuladen und zu hosten.

<a name="GetPrerequisites"></a>

### <a name="get-prerequisites"></a>Erforderliche Komponenten erhalten

Zum Abschließen dieses Lernprogramms benötigen Sie die folgenden Tools. Wenn sie noch nicht vorhanden sind, können Sie sie über diese Links installieren.

- [Git](https://git-scm.com/downloads)
- [Node.js und NPM](https://nodejs.org/)
- Get any text editor or IDE. Sie können den Code Visual Studio [kostenlos](https://code.visualstudio.com/download) installieren und verwenden.

Wenn während der Installation Optionen zum Hinzufügen von , , , und zum PFAD angezeigt werden, wählen Sie `git` `node` `npm` `code` dies aus. Es ist praktisch.

Stellen Sie sicher, dass die Tools verfügbar sind, indem Sie folgendes in einem Terminalfenster ausführen:

> [!NOTE]
> Verwenden Sie das Terminalfenster, mit dem Sie auf Ihrer Plattform am bequemsten sind. Diese Beispiele verwenden Bash (das in Git enthalten ist), diese Skripts werden jedoch auf den meisten Plattformen ausgeführt.

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

Wenn Sie gulp nicht installiert haben (oder die falsche Version installiert haben), verwenden Sie dies jetzt, indem Sie `npm install gulp` im Terminalfenster ausführen.

Wenn Sie Visual Studio Code installiert haben, können Sie die Installation überprüfen, indem Sie:

```bash
code --version
1.28.2
929bacba01ef658b873545e26034d1a8067445e9
```

Sie können dieses Terminalfenster weiterhin verwenden, um die Befehle auszuführen, die in diesem Lernprogramm ausgeführt werden.

<a name="DownloadSample"></a>

### <a name="download-the-sample"></a>Herunterladen des Beispiels

Wir haben ein einfaches [Hello, World! bereitgestellt.](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-hello-world/nodejs) Beispiel für die ersten Schritte. Führen Sie in einem Terminalfenster den folgenden Befehl aus, um das Beispielrepository auf ihren lokalen Computer zu klonen:

```bash
git clone https://github.com/OfficeDev/Microsoft-Teams-Samples.git
```

> [!TIP]
> Sie können dieses [](https://github.com/OfficeDev/Microsoft-Teams-Samples) Repository [forken,](https://help.github.com/articles/fork-a-repo/) wenn Sie Ihre Änderungen an Ihrem GitHub-Repository ändern und einchecken möchten, um eine zukünftige Referenz zu erhalten.

<a name="BuildRun"></a>

### <a name="build-and-run-the-sample"></a>Erstellen und Ausführen des Beispiels

Nachdem das Repository geklont wurde, wechseln Sie zu dem Verzeichnis, das das Beispiel enthält:

```bash
cd Microsoft-Teams-Samples/samples/app-hello-world/nodejs/
```

Zum Erstellen des Beispiels müssen Sie alle abhängigkeiten installieren. Führen Sie dazu den folgenden Befehl aus:

```bash
npm install
```

Es sollte eine Reihe von Abhängigkeiten installiert werden. Sobald sie fertig sind, können Sie die App ausführen:

```bash
npm start
```

Wenn die Hello-World-App gestartet wird, wird sie `App started listening on port 3333` im Terminalfenster angezeigt.

> [!NOTE]
> Wenn in der obigen Meldung eine andere Portnummer angezeigt wird, liegt dies daran, dass eine PORT-Umgebungsvariable festgelegt ist. Sie können diesen Port weiterhin verwenden oder Die Umgebungsvariable in 3333 ändern.

An diesem Punkt können Sie ein Browserfenster öffnen und zu den folgenden URLs navigieren, um zu überprüfen, ob alle App-URLs geladen werden:

- [http://localhost:3333](http://localhost:3333)
- [http://localhost:3333/hello](http://localhost:3333/hello)
- [http://localhost:3333/first](http://localhost:3333/first)
- [http://localhost:3333/second](http://localhost:3333/second)

<a name="HostSample"></a>

### <a name="host-the-sample-app"></a>Hosten der Beispiel-App

Denken Sie daran, dass Apps in Microsoft Teams Webanwendungen sind, die eine oder mehrere Funktionen verfügbar machen. Damit die Teams-Plattform Ihre App laden kann, muss Ihre App über das Internet erreichbar sein. Damit Ihre App über das Internet erreichbar ist, müssen Sie *Ihre App* hosten.

Für lokale Tests können Sie die App auf Ihrem lokalen Computer ausführen und einen Tunnel mit einem Webendpunkt erstellen. [ngrok](https://ngrok.com) ist ein kostenloses Tool, mit dem Sie genau dies tun können. Mit *ngrok* können Sie eine Webadresse wie z. B. `https://d0ac14a5.ngrok.io` erhalten (diese URL ist nur ein Beispiel). Sie können *ngrok* [für](https://ngrok.com/download) Ihre Umgebung herunterladen und installieren. Stellen Sie sicher, dass Sie es einem Speicherort in Ihrer `PATH` hinzufügen.

Nach der Installation können Sie ein neues Terminalfenster öffnen und den folgenden Befehl ausführen, um einen Tunnel zu erstellen. Das Beispiel verwendet Port 3333, stellen Sie daher sicher, dass Sie ihn hier angeben.

```bash
ngrok http 3333 -host-header=localhost:3333
```

*Ngrok* lauscht Anfragen aus dem Internet und führt sie an Ihre App weiter, die an Port 3333 ausgeführt wird. Sie können dies überprüfen, indem Sie Ihren Browser öffnen und die `https://d0ac14a5.ngrok.io/hello` Hello-Seite Ihrer App laden. Verwenden Sie unbedingt die Weiterleitungsadresse, die *von ngrok* in Ihrer Konsolensitzung angezeigt wird, anstelle dieser URL.

> [!NOTE]
> Wenn Sie im obigen [](#build-and-run-the-sample) Build- und Ausführungsschritt einen anderen Port verwendet haben, stellen Sie sicher, dass Sie zum Einrichten des *ngrok-Tunnels* dieselbe Portnummer verwenden.
> [!TIP]
> Es ist eine gute Idee, *ngrok* in einem anderen Terminalfenster ausführen, um die Ausführung zu verhindern, ohne die Knoten-App zu stören, die Sie später möglicherweise beenden, neu erstellen und erneut ausführen müssen. Die *ngrok-Sitzung* gibt nützliche Debuginformationen in diesem Fenster zurück.

Es gibt eine kostenpflichtige Version von *ngrok,* die dauerhafte Namen zulässt. Wenn Sie die kostenlose Version verwenden, ist Ihre App nur während der aktuellen Sitzung auf Ihrem Entwicklungscomputer verfügbar. Wenn der Computer heruntergefahren wird oder in den Ruhezustand geht, ist der Dienst nicht mehr verfügbar. Denken Sie daran, wenn Sie die App für Tests durch andere Benutzer freigeben. Wenn Sie den Dienst neu starten müssen, gibt er eine neue Adresse zurück, und Sie müssen jeden Ort aktualisieren, der diese Adresse verwendet.

Notieren Sie sich die URL Ihrer App, da Sie dies später benötigen, wenn Sie die App mit App Studio bei Teams registrieren. Editor funktioniert zu diesem Zweck gut.

<a name="DeployToTeams"></a>

## <a name="deploy-your-app-to-microsoft-teams"></a>Bereitstellen Ihrer App in Microsoft Teams

An diesem Punkt haben Sie eine App im Internet gehostet, aber Sie haben noch keine Möglichkeit, Teams mitzuteilen, wo sie suchen soll, oder auch nicht, wie Ihre App heißt. Dazu müssen Sie jetzt ein App-Paket erstellen. Dies ist wenig mehr als eine Textdatei, die das App-Manifest und einige Symbole enthält, die der Teams-Client zum ordnungsgemäßen Anzeigen und Branden Ihrer App verwendet. Sie können dieses App-Paket manuell erstellen oder App Studio verwenden, ein Tool, das in Teams ausgeführt wird, das das Registrieren der App vereinfacht. App Studio ist die empfohlene Methode zum Erstellen und Aktualisieren des App-Pakets.

Für beide Methoden benötigen Sie Folgendes:

- Die URL, unter der Ihre App im Internet gefunden werden kann.
- Symbole, die Teams zum Branden Ihrer App verwendet. Das Beispiel enthält Platzhaltersymbole in "src\static\images". App Studio stellt bei Bedarf auch Standardsymbole zur Verfügung.

[!include[Use App Studio to configure the app package](~/includes/get-started/get-started-use-app-studio.md)]

## <a name="update-your-hosted-app"></a>Aktualisieren Ihrer gehosteten App

Die Beispiel-App erfordert, dass die folgenden Umgebungsvariablen auf die Werte festgelegt werden, die Sie zuvor notieren.

```
MICROSOFT_APP_ID=<YOUR BOT'S APP ID>
MICROSOFT_APP_PASSWORD=<YOUR BOT'S PASSWORD>
WEBSITE_NODE_DEFAULT_VERSION=8.9.4
```

Wie Sie dies tun, hängt davon ab, wie Sie Ihre App gehostet haben. Das Wichtige bei der Verwendung von Umgebungsvariablen ist, dass diese Werte Teil Ihrer Umgebung sind – sie können über den Code für Ihre App zugegriffen werden, aber sie werden nicht für Dritte verfügbar gemacht, die die Dateien untersuchen, aus denen Ihre Website besteht.

Wenn Sie die App mit ngrok ausführen, müssen Sie einige lokale Umgebungsvariablen einrichten. Es gibt viele Möglichkeiten, dies zu tun, aber am einfachsten ist es, wenn Sie Visual Studio Code verwenden, eine [Startkonfiguration hinzuzufügen:](https://code.visualstudio.com/Docs/editor/debugging#_launch-configurations)

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

Dabei gilt Folgendes:

MICROSOFT_APP_ID und MICROSOFT_APP_PASSWORD ist die ID bzw. das Kennwort für Ihren Bot.
NODE_DEBUG zeigt Ihnen, was in Ihrem Bot geschieht, in der Visual Studio Codedebuggerkonsole.
NODE_CONFIG_DIR auf das Verzeichnis im Stammverzeichnis des Repositorys (standardmäßig wird die App lokal ausgeführt, wird sie im Ordner src nach ihr sucht).

> [!Note]
> Wenn Sie npm weiter oben im Lernprogramm nicht beendet haben, müssen Sie ausführen, damit Visual Studio Code ihre Startkonfigurationsvariablen `npm stop` richtig anfordert.

<a name="ConfigureTheAppTab"></a>

## <a name="configure-the-app-tab"></a>Konfigurieren der Registerkarte "App"

Nachdem Sie die App in einem Team installiert haben, müssen Sie sie so konfigurieren, dass Inhalte angezeigt werden. Wechseln Sie zu einem Kanal im Team, und klicken Sie auf die Schaltfläche **"+",** um eine neue Registerkarte hinzuzufügen. Sie können dann aus `Hello World` der Registerkartenliste **Hinzufügen** auswählen. Anschließend wird ihnen ein Konfigurationsdialogfeld angezeigt. In diesem Dialogfeld können Sie auswählen, welche Registerkarte in diesem Kanal angezeigt werden soll. Sobald Sie die Registerkarte ausgewählt haben und auf klicken, wird die Registerkarte mit der von Ihnen ausgewählten `Save` `Hello World` Registerkarte geladen.

<img width="430px" alt="Screenshot of configure" src="~/assets/images/samples-hello-world-tab-configure.png"/>

### <a name="test-your-bot-in-teams"></a>Testen Des Bots in Teams

Sie können jetzt mit dem Bot in Teams interagieren. Wählen Sie einen Kanal im Team aus, in dem Sie Ihre App registriert haben, und geben Sie `@your-bot-name` ein, gefolgt von Ihrer Nachricht. Dies wird als Erwähnung **\@ bezeichnet.** Alle Nachrichten, die Sie an den Bot senden, werden als Antwort an Sie zurückgeschickt.

<img width="450px" alt="Bot responses" src="~/assets/images/samples-hello-world-bot.png"/>

<a name="ComposeRichMessages"></a>

### <a name="test-your-messaging-extension"></a>Testen Der Messagingerweiterung

Um Ihre Messagingerweiterung zu testen, können Sie auf die drei Punkte unter dem Eingabefeld in der Unterhaltungsansicht klicken. Ein Menü wird mit der **"Hello World"-App** angezeigt. Wenn Sie darauf klicken, werden eine Reihe zufälliger Texte zu sehen sein. Sie können einen beliebigen auswählen und ihn in Ihre Unterhaltung einfügen.

<img width="430px" alt="Messaging extension menu" src="~/assets/images/samples-hello-world-messaging-extensions-menu.png" />

<img width="430px" alt="Messaging extension result" src="~/assets/images/samples-hello-world-messaging-extensions-result.png" />

Wählen Sie einen der zufälligen Texte aus, und unten wird eine Karte formatiert und kann mit Ihrer eigenen Nachricht gesendet werden.

<img width="430px" alt="Messaging extension send" src="~/assets/images/samples-hello-world-messaging-extensions-send.png" />
