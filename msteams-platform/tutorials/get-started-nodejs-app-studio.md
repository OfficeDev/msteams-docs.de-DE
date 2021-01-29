---
title: Lernprogramm – Erstellen Sie Ihre erste App mithilfe Node.js
description: Erfahren Sie, wie Sie mit dem Erstellen von Microsoft Teams-Apps mit Node.js.
keywords: Erste Schritte node.js nodejs App Studio
ms.topic: tutorial
ms.custom: scenarios:getting-started; languages:JavaScript,Node.js
ms.openlocfilehash: 03dcf79a46266321e54c7e99bf01cdd2a87075fa
ms.sourcegitcommit: fa64b83c0b534bf7a89f256880d5b5ca193e4b04
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/28/2021
ms.locfileid: "50037046"
---
# <a name="create-your-first-microsoft-teams-app-using-nodejs"></a>Erstellen Sie Ihre erste Microsoft Teams-App mithilfe Node.js

Dieses Lernprogramm hilft Ihnen bei den ersten Schritte beim Erstellen einer Microsoft Teams-App Node.js.

[!include [prepare your environment](~/includes/prepare-environment.md)]

<a name="DownloadAndHost"></a>

## <a name="download-and-host-your-app"></a>Herunterladen und Hosten Ihrer App

Führen Sie die folgenden Schritte aus, um eine einfache "Hello World"-App in Teams herunterzuladen und zu hosten.

<a name="GetPrerequisites"></a>

### <a name="get-prerequisites"></a>Voraussetzungen erhalten

Zum Abschließen dieses Lernprogramms benötigen Sie die folgenden Tools. Wenn sie noch nicht vorhanden sind, können Sie sie über diese Links installieren.

- [Git](https://git-scm.com/downloads)
- [Node.js und NPM](https://nodejs.org/)
- Erhalten Sie einen beliebigen Texteditor oder eine IDE. Sie können Visual Studio [Code kostenlos](https://code.visualstudio.com/download) installieren und verwenden.

Wenn während der Installation Optionen zum Hinzufügen , , und zum PFAD angezeigt werden, wählen Sie `git` `node` `npm` `code` dies aus. Es ist praktisch.

Stellen Sie sicher, dass die Tools verfügbar sind, indem Sie folgendes in einem Terminalfenster ausführen:

> [!NOTE]
> Verwenden Sie das Terminalfenster, mit dem Sie sich auf Ihrer Plattform am besten aus sind. In diesen Beispielen wird Bash (in Git enthalten) verwendet, aber diese Skripts werden auf den meisten Plattformen ausgeführt.

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

Wenn Sie gulp nicht installiert haben (oder die falsche Version installiert haben), tun Sie dies jetzt, indem Sie `npm install gulp` in Ihrem Terminalfenster ausführen.

Wenn Sie Visual Studio Code installiert haben, können Sie die Installation überprüfen, indem Sie dies ausführen:

```bash
code --version
1.28.2
929bacba01ef658b873545e26034d1a8067445e9
```

Sie können weiterhin dieses Terminalfenster verwenden, um die Befehle auszuführen, die in diesem Lernprogramm folgen.

<a name="DownloadSample"></a>

### <a name="download-the-sample"></a>Herunterladen des Beispiels

Wir haben ein einfaches [Hello, World! bereitgestellt.](https://github.com/OfficeDev/msteams-samples-hello-world-nodejs) Beispiel für die ersten Schritte. Führen Sie in einem Terminalfenster den folgenden Befehl aus, um das Beispielrepository auf Ihrem lokalen Computer zu klonen:

```bash
git clone https://github.com/OfficeDev/msteams-samples-hello-world-nodejs.git
```

> [!TIP]
> Sie können [dieses Repository ver forken,](https://help.github.com/articles/fork-a-repo/) [](https://github.com/OfficeDev/msteams-samples-hello-world-nodejs) wenn Sie Ihre Änderungen an Ihrem GitHub-Repository ändern und einchecken möchten, um eine zukünftige Referenz zu erhalten.

<a name="BuildRun"></a>

### <a name="build-and-run-the-sample"></a>Erstellen und Ausführen des Beispiels

Nachdem das Repository geklont wurde, wechseln Sie zu dem Verzeichnis, in dem sich das Beispiel befindet:

```bash
cd msteams-samples-hello-world-nodejs
```

Zum Erstellen des Beispiels müssen Sie alle Abhängigkeiten installieren. Führen Sie dazu den folgenden Befehl aus:

```bash
npm install
```

Es sollte eine Reihe von Abhängigkeiten angezeigt werden, die installiert werden. Sobald sie fertig sind, können Sie die App ausführen:

```bash
npm start
```

Wenn die Hello-World-App gestartet wird, wird sie `App started listening on port 3333` im Terminalfenster angezeigt.

> [!NOTE]
> Wenn in der obigen Meldung eine andere Portnummer angezeigt wird, ist eine Portumgebungsvariable festgelegt. Sie können diesen Port weiterhin verwenden oder die Umgebungsvariable in 3333 ändern.

An diesem Punkt können Sie ein Browserfenster öffnen und zu den folgenden URLs navigieren, um zu überprüfen, ob alle URLs geladen werden:

- [http://localhost:3333](http://localhost:3333)
- [http://localhost:3333/hello](http://localhost:3333/hello)
- [http://localhost:3333/first](http://localhost:3333/first)
- [http://localhost:3333/second](http://localhost:3333/second)

<a name="HostSample"></a>

### <a name="host-the-sample-app"></a>Hosten der Beispiel-App

Denken Sie daran, dass Apps in Microsoft Teams Webanwendungen sind, die eine oder mehrere Funktionen verfügbar machen. Damit die Plattform Teams Ihre App laden kann, muss Ihre App über das Internet erreichbar sein. Damit Ihre App über das Internet erreichbar ist, müssen Sie *Ihre App* hosten.

Für lokale Tests können Sie die App auf Ihrem lokalen Computer ausführen und einen Tunnel mit einem Webendpunkt erstellen. [ngrok](https://ngrok.com) ist ein kostenloses Tool, mit dem Sie genau das tun können. Mit *ngrok* können Sie eine Webadresse wie z. B. `https://d0ac14a5.ngrok.io` (diese URL ist nur ein Beispiel) erhalten. Sie können *ngrok für* Ihre Umgebung herunterladen und installieren. [](https://ngrok.com/download) Stellen Sie sicher, dass Sie es einem Speicherort in Ihrer `PATH` hinzufügen.

Nach der Installation können Sie ein neues Terminalfenster öffnen und den folgenden Befehl ausführen, um einen Tunnel zu erstellen. Im Beispiel wird Port 3333 verwendet. Geben Sie ihn daher hier an.

```bash
ngrok http 3333 -host-header=localhost:3333
```

*Ngrok* hört Anforderungen aus dem Internet ab und führt sie an Ihre App weiter, die an Port 3333 ausgeführt wird. Sie können dies überprüfen, indem Sie Ihren Browser öffnen und die `https://d0ac14a5.ngrok.io/hello` Hello-Seite Ihrer App laden. Verwenden Sie anstatt dieser URL unbedingt die Weiterleitungsadresse, die *ngrok* in Ihrer Konsolensitzung angezeigt hat.

> [!NOTE]
> Wenn Sie im Build einen [](#build-and-run-the-sample) anderen Port verwendet haben und den obigen Schritt ausführen, stellen Sie sicher, dass Sie zum Einrichten des *ngrok-Tunnels* dieselbe Portnummer verwenden.
> [!TIP]
> Es ist eine gute Idee, *ngrok* in einem anderen Terminalfenster ausführen, damit es ausgeführt wird, ohne die Knoten-App zu stören, die Sie später möglicherweise beenden, neu erstellen und erneut ausführen müssen. Die *ngrok-Sitzung* gibt nützliche Debuginformationen in diesem Fenster zurück.

Es gibt eine kostenpflichtige Version von *ngrok,* die beständige Namen zulässt. Wenn Sie die kostenlose Version verwenden, ist Ihre App nur während der aktuellen Sitzung auf Ihrem Entwicklungscomputer verfügbar. Wenn der Computer heruntergefahren wird oder in den Ruhezustand geht, ist der Dienst nicht mehr verfügbar. Denken Sie daran, wenn Sie die App für Tests durch andere Benutzer freigeben. Wenn Sie den Dienst neu starten müssen, wird eine neue Adresse zurückgeben, und Sie müssen jeden Ort aktualisieren, der diese Adresse verwendet.

Notieren Sie sich die URL Ihrer App, da Sie diese später benötigen, wenn Sie die App mit App Studio bei Teams registrieren. Editor funktioniert zu diesem Zweck gut.

<a name="DeployToTeams"></a>

## <a name="deploy-your-app-to-microsoft-teams"></a>Bereitstellen Ihrer App in Microsoft Teams

An diesem Punkt haben Sie eine App, die im Internet gehostet wird, Aber Sie haben noch keine Möglichkeit, Teams mitzuteilen, wo sie suchen soll oder auch nicht, wie Ihre App heißt. Dazu müssen Sie nun ein App-Paket erstellen. Dies ist wenig mehr als eine Textdatei, die das App-Manifest und einige Symbole enthält, die der Teams-Client verwendet, um Ihre App ordnungsgemäß zu anzeigen und zu brandmarken. Sie können dieses App-Paket manuell erstellen oder App Studio verwenden, ein Tool, das in Teams ausgeführt wird und das Registrieren der App vereinfacht. App Studio ist die empfohlene Methode zum Erstellen und Aktualisieren des App-Pakets.

Für beide Methoden benötigen Sie Folgendes:

- Die URL, unter der Ihre App im Internet zu finden ist.
- Symbole, die Teams zum Branden Ihrer App verwendet. Das Beispiel enthält Platzhaltersymbole in "src\static\images". App Studio stellt bei Bedarf auch Standardsymbole zur Verfügung.

[!include[Use App Studio to configure the app package](~/includes/get-started/get-started-use-app-studio.md)]

## <a name="update-your-hosted-app"></a>Aktualisieren Ihrer gehosteten App

Die Beispiel-App erfordert, dass die folgenden Umgebungsvariablen auf die Werte festgelegt werden, die Sie zuvor notieren.

```
MICROSOFT_APP_ID=<YOUR BOT'S APP ID>
MICROSOFT_APP_PASSWORD=<YOUR BOT'S PASSWORD>
WEBSITE_NODE_DEFAULT_VERSION=8.9.4
```

Wie Sie dies tun, hängt davon ab, wie Sie Ihre App gehostet haben. Der wichtige Punkt bei der Verwendung von Umgebungsvariablen ist, dass diese Werte Teil Ihrer Umgebung sind. Sie können über den Code für Ihre App darauf zugreifen, werden jedoch nicht für Dritte verfügbar gemacht, die die Dateien untersuchen, aus denen Ihre Website besteht.

Wenn Sie die App mit ngrok ausführen, müssen Sie einige lokale Umgebungsvariablen einrichten. Es gibt viele Möglichkeiten, dies zu tun, aber die einfachste Möglichkeit, wenn Sie Visual Studio Code verwenden, ist das Hinzufügen einer [Startkonfiguration:](https://code.visualstudio.com/Docs/editor/debugging#_launch-configurations)

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
NODE_DEBUG zeigt Ihnen, was in Ihrem Bot geschieht, in der Visual Studio Code-Debugkonsole.
NODE_CONFIG_DIR verweist auf das Verzeichnis im Stammverzeichnis des Repositorys (wenn die App lokal ausgeführt wird, sucht sie standardmäßig im Ordner "src").

> [!Note]
> Wenn Sie npm weiter oben im Lernprogramm nicht beendet haben, müssen Sie die Ausführung ausführen, damit Visual Studio Code ihre Startkonfigurationsvariablen `npm stop` richtig anfordert.

<a name="ConfigureTheAppTab"></a>

## <a name="configure-the-app-tab"></a>Konfigurieren der Registerkarte "App"

Nachdem Sie die App in einem Team installiert haben, müssen Sie sie so konfigurieren, dass Inhalte angezeigt werden. Wechseln Sie zu einem Kanal im Team, und klicken Sie auf die Schaltfläche **"+",** um eine neue Registerkarte hinzuzufügen. Sie können dann aus der `Hello World` Registerkartenliste **"Hinzufügen"** auswählen. Anschließend wird ein Konfigurationsdialogfeld angezeigt. In diesem Dialogfeld können Sie auswählen, welche Registerkarte in diesem Kanal angezeigt werden soll. Nachdem Sie die Registerkarte ausgewählt und darauf geklickt haben, wird die Registerkarte mit der ausgewählten `Save` `Hello World` Registerkarte geladen.

<img width="430px" src="~/assets/images/samples-hello-world-tab-configure.png" alt-text="Screenshot of configure" />

### <a name="test-your-bot-in-teams"></a>Testen Ihres Bots in Teams

Sie können jetzt mit dem Bot in Teams interagieren. Wählen Sie einen Kanal im Team aus, in dem Sie Ihre App registriert haben, und geben Sie `@your-bot-name` , gefolgt von Ihrer Nachricht, ein. Dies wird als Erwähnung **\@ bezeichnet.** Welche Nachricht Sie an den Bot senden, wird als Antwort an Sie zurückgeschickt.

<img width="450px" alt-text="Bot responses" src="~/assets/images/samples-hello-world-bot.png" />

<a name="ComposeRichMessages"></a>

### <a name="test-your-messaging-extension"></a>Testen der Messagingerweiterung

Zum Testen Ihrer Messagingerweiterung können Sie auf die drei Punkte unter dem Eingabefeld in der Unterhaltungsansicht klicken. Ein Menü mit der **"Hello World"-App** wird angezeigt. Wenn Sie darauf klicken, wird eine Reihe zufälliger Texte zu sehen sein. Sie können eine davon auswählen und in Ihre Unterhaltung einfügen.

<img width="430px" alt-text="Messaging extension menu" src="~/assets/images/samples-hello-world-messaging-extensions-menu.png" />

<img width="430px" alt-text="Messaging extension result" src="~/assets/images/samples-hello-world-messaging-extensions-result.png" />

Wählen Sie einen der zufälligen Texte aus, und unten wird eine Karte formatiert und bereit zum Senden mit Ihrer eigenen Nachricht angezeigt.

<img width="430px" alt-text="Messaging extension send" src="~/assets/images/samples-hello-world-messaging-extensions-send.png" />
