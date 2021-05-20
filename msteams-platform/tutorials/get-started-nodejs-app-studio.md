---
title: Tutorial - Erstellen Sie Ihre erste App mit Node.js
description: Erfahren Sie, wie Sie mit dem Erstellen Microsoft Teams Apps mit Node.js beginnen.
keywords: Erste Schritte node.js nodejs App Studio
ms.topic: tutorial
localization_priority: Normal
ms.custom: scenarios:getting-started; languages:JavaScript,Node.js
ms.openlocfilehash: 46272671443e07432513b667af424b5c5be05f2e
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566540"
---
# <a name="create-your-first-microsoft-teams-app-using-nodejs"></a>Erstellen Sie Ihre erste Microsoft Teams-App mit Node.js

In diesem Tutorial können Sie mit dem Erstellen einer Microsoft Teams-App mit Node.js beginnen.

[!include [prepare your environment](~/includes/prepare-environment.md)]

<a name="DownloadAndHost"></a>

## <a name="download-and-host-your-app"></a>Herunterladen und Hosten Ihrer App

Führen Sie die folgenden Schritte aus, um eine einfache "Hallo-Welt"-App in Teams herunterzuladen und zu hosten.

<a name="GetPrerequisites"></a>

### <a name="get-prerequisites"></a>Voraussetzungen abrufen

Um dieses Tutorial abzuschließen, benötigen Sie die folgenden Tools. Wenn Sie sie noch nicht haben, können Sie sie über diese Links installieren.

- [Git](https://git-scm.com/downloads)
- [Node.js und NPM](https://nodejs.org/)
- Holen Sie sich einen beliebigen Texteditor oder eine IDE. Sie können [Visual Studio Code](https://code.visualstudio.com/download) kostenlos installieren und verwenden.

Wenn Während der Installation Optionen zum Hinzufügen von , , und zum PATH angezeigt werden, wählen Sie dies `git` `node` `npm` `code` aus. Es wird praktisch sein.

Stellen Sie sicher, dass die Tools verfügbar sind, indem Sie folgendes in einem Terminalfenster ausführen:

> [!NOTE]
> Verwenden Sie das Terminalfenster, mit dem Sie sich auf Ihrer Plattform am wohlsten fühlen. Diese Beispiele verwenden Bash (das in Git enthalten ist), aber diese Skripte werden auf den meisten Plattformen ausgeführt.

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

Möglicherweise verfügen Sie über eine andere Version dieser Anwendungen. Dies sollte kein Problem sein, außer gulp. Für gulp müssen Sie Version 4.0.0 oder höher verwenden.

Wenn Sie gulp nicht installiert haben (oder die falsche Version installiert haben), führen Sie dies jetzt `npm install gulp` in Ihrem Terminalfenster aus.

Wenn Sie Visual Studio Code installiert haben, können Sie die Installation überprüfen, indem Sie:

```bash
code --version
1.28.2
929bacba01ef658b873545e26034d1a8067445e9
```

Sie können dieses Terminalfenster weiterhin verwenden, um die folgenden Befehle in diesem Tutorial auszuführen.

<a name="DownloadSample"></a>

### <a name="download-the-sample"></a>Laden Sie das Beispiel herunter

Wir haben ein einfaches [Hallo, Welt](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-hello-world/nodejs) zur Verfügung gestellt! Beispiel, um Ihnen den Einstieg zu erleichtern. Führen Sie in einem Terminalfenster den folgenden Befehl aus, um das Beispiel-Repository auf Ihren lokalen Computer zu klonen:

```bash
git clone https://github.com/OfficeDev/Microsoft-Teams-Samples.git
```

> [!TIP]
> Sie können dieses [Repository](https://github.com/OfficeDev/Microsoft-Teams-Samples) [verkleben,](https://help.github.com/articles/fork-a-repo/) wenn Sie Ihre Änderungen an Ihrem GitHub Repository für zukünftige Referenzen ändern und einchecken möchten.

<a name="BuildRun"></a>

### <a name="build-and-run-the-sample"></a>Erstellen und Ausführen des Beispiels

Nachdem das Repository geklont wurde, wechseln Sie in das Verzeichnis, in dem sich das Beispiel befindet:

```bash
cd Microsoft-Teams-Samples/samples/app-hello-world/nodejs/
```

Um das Beispiel zu erstellen, müssen Sie alle abhängigkeiten installieren. Führen Sie dazu den folgenden Befehl aus:

```bash
npm install
```

Es sollte angezeigt werden, dass eine Reihe von Abhängigkeiten installiert werden. Sobald sie fertig sind, können Sie die App ausführen:

```bash
npm start
```

Wenn die hello-world-App gestartet wird, wird sie `App started listening on port 3333` im Terminalfenster angezeigt.

> [!NOTE]
> Wenn in der obigen Meldung eine andere Portnummer angezeigt wird, liegt dies daran, dass sie eine PORT-Umgebungsvariable festgelegt haben. Sie können diesen Port weiterhin verwenden oder Ihre Umgebungsvariable in 3333 ändern.

An dieser Stelle können Sie ein Browserfenster öffnen und zu den folgenden URLs navigieren, um zu überprüfen, ob alle App-URLs geladen werden:

- `http://localhost:3333`
- `http://localhost:3333/hello`
- `http://localhost:3333/first`
- `http://localhost:3333/second`

<a name="HostSample"></a>

### <a name="host-the-sample-app"></a>Hosten der Beispiel-App

Denken Sie daran, dass Apps in Microsoft Teams Webanwendungen sind, die eine oder mehrere Funktionen verfügbar machen. Damit die Teams Plattform Ihre App lädt, muss Ihre App über das Internet erreichbar sein. Damit Ihre App über das Internet erreichbar ist, müssen Sie Ihre App *hosten.*

Für lokale Tests können Sie die App auf Ihrem lokalen Computer ausführen und einen Tunnel zu diesem Mitmachen mit einem Webendpunkt erstellen. [ngrok](https://ngrok.com) ist ein kostenloses Tool, mit dem Sie genau das tun können. Mit *ngrok* können Sie eine Webadresse wie `https://d0ac14a5.ngrok.io` (diese URL ist nur ein Beispiel) erhalten. Sie können *ngrok* für Ihre Umgebung [herunterladen und installieren.](https://ngrok.com/download) Stellen Sie sicher, dass Sie es an einem Speicherort in Ihrem `PATH` hinzufügen.

Nachdem Sie es installiert haben, können Sie ein neues Terminalfenster öffnen und den folgenden Befehl ausführen, um einen Tunnel zu erstellen. Das Beispiel verwendet Port 3333, also stellen Sie sicher, dass Sie ihn hier angeben:

```bash
ngrok http 3333 -host-header=localhost:3333
```

*Ngrok* hört Anfragen aus dem Internet ab und leitet sie an Ihre App weiter, die auf Port 3333 ausgeführt wird. Sie können dies überprüfen, indem Sie Ihren Browser öffnen und die `https://d0ac14a5.ngrok.io/hello` Hallo-Seite Ihrer App laden. Bitte verwenden Sie die Weiterleitungsadresse, die von *ngrok* in Ihrer Konsolensitzung anstelle dieser URL angezeigt wird.

> [!NOTE]
> Wenn Sie einen anderen Port im Build verwendet haben und schritt oben [ausgeführt](#build-and-run-the-sample) werden, stellen Sie sicher, dass Sie dieselbe Portnummer verwenden, um den *ngrok-Tunnel* einzurichten.
> [!TIP]
> Es ist eine gute Idee, *ngrok* in einem anderen Terminalfenster auszuführen, um es laufen zu lassen, ohne die Knoten-App zu stören, die Sie später möglicherweise anhalten, neu erstellen und erneut ausführen müssen. Die *ngrok-Sitzung* gibt in diesem Fenster nützliche Debuginformationen zurück.

Es gibt eine kostenpflichtige Version von *ngrok,* die persistente Namen zulässt. Wenn Sie die kostenlose Version verwenden, ist Ihre App nur während der aktuellen Sitzung auf Ihrem Entwicklungscomputer verfügbar. Wenn die Maschine heruntergefahren wird oder in den Ruhezustand geht, ist der Dienst nicht mehr verfügbar. Denken Sie daran, wenn Sie die App zum Testen durch andere Benutzer freigeben. Wenn Sie den Dienst neu starten müssen, wird eine neue Adresse zurückgegeben, und Sie müssen jeden Ort aktualisieren, der diese Adresse verwendet.

Denken Sie daran, notieren Sie sich die URL Ihrer App, da Sie dies später benötigen, wenn Sie die App mit Teams app studio registrieren. Editor funktioniert dafür gut.

<a name="DeployToTeams"></a>

## <a name="deploy-your-app-to-microsoft-teams"></a>Stellen Sie Ihre App zum Microsoft Teams bereit

Zu diesem Zeitpunkt haben Sie eine App im Internet gehostet, aber Sie haben noch keine Möglichkeit, Teams zu sagen, wo sie zu suchen, oder sogar, was Ihre App genannt wird. Dazu müssen Sie nun ein App-Paket erstellen. Dies ist nicht viel mehr als eine Textdatei, die das App-Manifest und einige Symbole enthält, die der Teams-Client verwendet, um Ihre App ordnungsgemäß anzuzeigen und zu brandmarken. Sie können dieses App-Paket manuell erstellen oder App Studio verwenden, ein Tool, das in Teams ausgeführt wird, das den Prozess der Registrierung der App vereinfacht. App Studio ist die empfohlene Methode zum Erstellen und Aktualisieren des App-Pakets.

Für eine der beiden Methoden benötigen Sie Folgendes:

- Die URL, unter der Sich Ihre App im Internet befindet.
- Symbole, die Teams verwenden, um Ihre App zu brandmarken. Das Beispiel enthält Platzhaltersymbole, die sich in "src-static-images" befinden. App Studio stellt bei Bedarf auch Standardsymbole bereit.

[!include[Use App Studio to configure the app package](~/includes/get-started/get-started-use-app-studio.md)]

## <a name="update-your-hosted-app"></a>Aktualisieren Ihrer gehosteten App

Für die Beispiel-App müssen die folgenden Umgebungsvariablen auf die Werte festgelegt werden, die Sie zuvor notieren:

```
MICROSOFT_APP_ID=<YOUR BOT'S APP ID>
MICROSOFT_APP_PASSWORD=<YOUR BOT'S PASSWORD>
WEBSITE_NODE_DEFAULT_VERSION=8.9.4
```

Wie Sie dies tun, hängt davon ab, wie Sie Ihre App gehostet haben. Das Wichtige an der Verwendung von Umgebungsvariablen ist, dass diese Werte Teil Ihrer Umgebung sind - sie können durch den Code für Ihre App zugegriffen werden, aber sie sind nicht für Dritte verfügbar, die die Dateien untersuchen könnten, aus denen Ihre Website besteht.

Wenn Sie die App mit ngrok ausführen, müssen Sie einige lokale Umgebungsvariablen einrichten. Es gibt viele Möglichkeiten, dies zu tun, aber die einfachste, wenn Sie Visual Studio Code verwenden, ist es, eine [Startkonfiguration](https://code.visualstudio.com/Docs/editor/debugging#_launch-configurations)hinzuzufügen:

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

MICROSOFT_APP_ID und MICROSOFT_APP_PASSWORD ist die ID bzw. das Passwort für Ihren Bot.
NODE_DEBUG zeigt Ihnen, was in Ihrem Bot in der Visual Studio Code-Debug-Konsole passiert.
NODE_CONFIG_DIR zeigt auf das Verzeichnis im Stammverzeichnis des Repositorys (standardmäßig sucht die App, wenn sie lokal ausgeführt wird, im Ordner src nach).

> [!Note]
> Wenn Sie npm nicht von früher im Tutorial gestoppt haben, müssen Sie ausführen, `npm stop` damit Visual Studio Code Ihre Startkonfigurationsvariablen korrekt abrufen können.

<a name="ConfigureTheAppTab"></a>

## <a name="configure-the-app-tab"></a>Konfigurieren der App-Registerkarte

Nachdem Sie die App in einem Team installiert haben, müssen Sie sie so konfigurieren, dass Inhalte angezeigt werden. Gehen Sie zu einem Kanal im Team und klicken Sie auf die Schaltfläche **"+",** um eine neue Registerkarte hinzuzufügen. Sie können dann `Hello World` aus der Liste Registerkarte **hinzufügen** auswählen. Anschließend wird Ihnen ein Konfigurationsdialog angezeigt. In diesem Dialogfeld können Sie auswählen, welche Registerkarte in diesem Kanal angezeigt werden soll. Sobald Sie die Registerkarte ausgewählt und klicken Sie auf `Save` Sie können die Registerkarte mit der Registerkarte geladen sehen Sie `Hello World` gewählt:

<img width="430px" alt="Screenshot of configure" src="~/assets/images/samples-hello-world-tab-configure.png"/>

### <a name="test-your-bot-in-teams"></a>Testen Sie Ihren Bot in Teams

Sie können jetzt mit dem Bot in Teams interagieren. Wählen Sie einen Kanal im Team aus, in dem Sie Ihre App registriert haben, und geben Sie `@your-bot-name` ein, gefolgt von Ihrer Nachricht. Dies wird als **\@ Erwähnung** bezeichnet. Welche Nachricht Sie an den Bot senden, wird Ihnen als Antwort zurückgesendet:

<img width="450px" alt="Bot responses" src="~/assets/images/samples-hello-world-bot.png"/>

<a name="ComposeRichMessages"></a>

### <a name="test-your-messaging-extension"></a>Testen Sie Ihre Messaging-Erweiterung

Um Ihre Messaging-Erweiterung zu testen, können Sie auf die drei Punkte unter dem Eingabefeld in Ihrer Unterhaltungsansicht klicken. Ein Menü erscheint mit der **"Hello World"-App.** Wenn Sie darauf klicken, sehen Sie eine Reihe von zufälligen Texten. Sie können einen von ihnen auswählen und es wird in Ihre Unterhaltung eingefügt:

<img width="430px" alt="Messaging extension menu" src="~/assets/images/samples-hello-world-messaging-extensions-menu.png" />

<img width="430px" alt="Messaging extension result" src="~/assets/images/samples-hello-world-messaging-extensions-result.png" />

Wählen Sie einen der zufälligen Texte, und Sie sehen eine Karte formatiert und bereit, mit Ihrer eigenen Nachricht am unteren Rand zu senden:

<img width="430px" alt="Messaging extension send" src="~/assets/images/samples-hello-world-messaging-extensions-send.png" />
