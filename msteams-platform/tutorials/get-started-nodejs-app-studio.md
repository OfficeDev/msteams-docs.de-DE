---
title: Erste Schritte mit App Studio und Node. js
description: Erste Schritte beim Erstellen von tollen apps in Microsoft Teams mit Node. js und App Studio
keywords: Erste Schritte Node. js nodejs App Studio
ms.date: 11/09/2018
ms.openlocfilehash: 36da6d7445ad7780f6bbbf52ccce3e558c76be72
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674513"
---
# <a name="get-started-on-the-microsoft-teams-platform-with-nodejs-and-app-studio"></a>Erste Schritte mit der Microsoft Teams-Plattform mit Node. js und App Studio

Die [Microsoft Teams](/microsoftteams/) -Entwicklerplattform erleichtert Ihnen das Erweitern von Teams und die nahtlose Integration ihrer eigenen Anwendungen und Dienste in den Arbeitsbereich "Teams". Diese Apps können dann an Ihr Unternehmen oder für Teams auf der ganzen Welt verteilt werden.

Um Microsoft Teams zu erweitern, müssen Sie eine Microsoft Teams-app erstellen. Eine Microsoft Teams-APP ist eine Webanwendung, die Sie hosten. Diese APP kann dann in Microsoft Teams in den Arbeitsbereich des Benutzers integriert werden.

[!include [prepare your environment](~/includes/prepare-environment.md)]

<a name="DownloadAndHost"></a>

## <a name="download-and-host-your-app"></a>Herunterladen und Hosten Ihrer APP

Führen Sie die folgenden Schritte aus, um eine einfache "Hello World"-app in Microsoft Teams herunterzuladen und zu hosten.

<a name="GetPrerequisites"></a>

### <a name="get-prerequisites"></a>Abrufen von Voraussetzungen

Um dieses Lernprogramm abzuschließen, benötigen Sie die folgenden Tools. Wenn Sie diese nicht bereits haben, können Sie Sie über diese Links installieren.

- [Git](https://git-scm.com/downloads)
- [Node. js und NPM](https://nodejs.org/)
- Abrufen eines beliebigen Text-Editors oder einer IDE. Sie können [Visual Studio-Code](https://code.visualstudio.com/download) kostenlos installieren und verwenden.

Wenn Sie Optionen zum Hinzufügen `git`, `node` `npm`, und `code` dem Pfad während der Installation sehen, wählen Sie, um dies zu tun. Das ist praktisch.

Stellen Sie sicher, dass die Tools verfügbar sind, indem Sie Folgendes in einem Terminalfenster ausführen:

> [!NOTE]
> Verwenden Sie das Terminal-Fenster, mit dem Sie sich am besten auf Ihrer Plattform vertraut machen. In diesen Beispielen wird bash verwendet (in git enthalten), diese Skripts werden jedoch auf den meisten Plattformen ausgeführt.

```bash
$ git --version
git version 2.19.0.windows.1

$ node -v
v8.9.3

$ npm -v
5.5.1

$ gulp -v
CLI version 4.0.2
```

Möglicherweise haben Sie eine andere Version dieser Anwendungen. Dies sollte kein Problem sein, außer für "schlucken". Für Schluck müssen Sie Version 4.0.0 oder höher verwenden.

Wenn Sie keinen Schluck installiert haben (oder die falsche Version installiert haben), tun Sie dies jetzt, `npm install gulp` indem Sie in Ihrem Terminal-Fenster ausführen.

Wenn Sie Visual Studio Code installiert haben, können Sie die Installation überprüfen, indem Sie Folgendes durchführen:

```bash
code --version
1.28.2
929bacba01ef658b873545e26034d1a8067445e9
```

Sie können weiterhin dieses Terminalfenster verwenden, um die Befehle auszuführen, die in diesem Lernprogramm folgen.

<a name="DownloadSample"></a>

### <a name="download-the-sample"></a>Herunterladen des Beispiels

Wir haben ein einfaches [Hello, World](https://github.com/OfficeDev/msteams-samples-hello-world-nodejs) bereitgestellt! Beispiel für die ersten Schritte. Führen Sie in einem Terminalfenster den folgenden Befehl aus, um das Beispiel-Repository auf Ihren lokalen Computer zu klonen:

```bash
git clone https://github.com/OfficeDev/msteams-samples-hello-world-nodejs.git
```

> [!TIP]
> Sie können dieses [Repo](https://github.com/OfficeDev/msteams-samples-hello-world-nodejs) [abzweigen](https://help.github.com/articles/fork-a-repo/) , wenn Sie Ihre Änderungen an Ihrem GitHub-Repo zum späteren Nachschlagen ändern und einchecken möchten.

<a name="BuildRun"></a>

### <a name="build-and-run-the-sample"></a>Erstellen und Ausführen des Beispiels

Nachdem das Repository geklont wurde, wechseln Sie in das Verzeichnis, in dem sich das Beispiel befindet:

```bash
cd msteams-samples-hello-world-nodejs
```

Um das Beispiel zu erstellen, müssen Sie alle Abhängigkeiten installieren. Führen Sie dazu den folgenden Befehl aus:

```bash
npm install
```

Sie sollten eine Reihe von Abhängigkeiten erhalten, die installiert werden. Nachdem Sie fertig sind, können Sie die app ausführen:

```bash
npm start
```

Wenn die Hello-World-App gestartet wird, `App started listening on port 3333` wird Sie im Terminalfenster angezeigt.

> [!NOTE]
> Wenn in der obigen Meldung eine andere Portnummer angezeigt wird, liegt dies daran, dass Sie eine Umgebungsvariable für die Port Umgebung festgelegt haben. Sie können diesen Port weiterhin verwenden oder Ihre Umgebungsvariable in 3333 ändern.

Nun können Sie ein Browserfenster öffnen und zu den folgenden URLs navigieren, um zu überprüfen, ob alle App-URLs geladen werden:

- [http://localhost:3333](http://localhost:3333)
- [http://localhost:3333/hello](http://localhost:3333/hello)
- [http://localhost:3333/first](http://localhost:3333/first)
- [http://localhost:3333/second](http://localhost:3333/second)

<a name="HostSample"></a>

### <a name="host-the-sample-app"></a>Hosten der Beispiel-App

Beachten Sie, dass apps in Microsoft Teams Webanwendungen sind, die eine oder mehrere Funktionen verfügbar machen. Damit die Microsoft Teams-Plattform Ihre APP lädt, muss Ihre APP über das Internet erreichbar sein. Damit Ihre APP über das Internet erreichbar ist, müssen Sie Ihre APP *hosten* .

Für lokale Tests können Sie die APP auf Ihrem lokalen Computer ausführen und einen Tunnel mit einem Webendpunkt erstellen. [ngrok](https://ngrok.com) ist ein kostenloses Tool, mit dem Sie genau dies tun können. Mit *ngrok* können Sie eine Webadresse wie `https://d0ac14a5.ngrok.io` (diese URL ist nur ein Beispiel) erhalten. Sie können *ngrok* für Ihre Umgebung [herunterladen und installieren](https://ngrok.com/download) . Stellen Sie sicher, dass Sie Sie an einen Speicherort `PATH`in Ihrem hinzufügen.

Nachdem Sie es installiert haben, können Sie ein neues Terminalfenster öffnen und den folgenden Befehl ausführen, um einen Tunnel zu erstellen. Im Beispiel wird Port 3333 verwendet, stellen Sie daher sicher, dass Sie es hier angeben.

```bash
ngrok http 3333 -host-header=localhost:3333
```

*Ngrok* wird Anfragen aus dem Internet abhören und diese an Ihre APP weiterleiten, die auf Port 3333 läuft. Sie können überprüfen, ob Sie Ihren Browser öffnen `https://d0ac14a5.ngrok.io/hello` und die Hello-Seite Ihrer App laden. Achten Sie darauf, dass Sie die von *ngrok* in ihrer Konsolensitzung angezeigte Weiterleitungsadresse anstelle dieser URL verwenden.

> [!NOTE]
> Wenn Sie einen anderen Port im Schritt " [Build" und "ausführen](#build-and-run-the-sample) " verwendet haben, stellen Sie sicher, dass Sie die gleiche Portnummer zum Einrichten des *ngrok* -Tunnels verwenden.
> [!TIP]
> Es empfiehlt sich, *ngrok* in einem anderen Terminalfenster auszuführen, damit es ausgeführt wird, ohne dass die Knoten-App gestört wird, die Sie später möglicherweise beenden, neu erstellen und erneut ausführen müssen. In diesem Fenster werden in der *ngrok* -Sitzung nützliche Debuginformationen zurückgegeben.

Es gibt eine kostenpflichtige Version von *ngrok* , die persistente Namen zulässt. Wenn Sie die ﻿kostenlose Version verwenden, ist Ihre APP nur während der aktuellen Sitzung auf dem Entwicklungscomputer verfügbar. Wenn der Computer heruntergefahren wird oder in den Standbymodus wechselt, steht der Dienst nicht mehr zur Verfügung. Denken Sie daran, wenn Sie die APP für Tests von anderen Benutzern freigeben. Wenn Sie den Dienst neu starten müssen, wird eine neue Adresse zurückgegeben, und Sie müssen jeden Ort aktualisieren, an dem diese Adresse verwendet wird.

Notieren Sie sich die URL Ihrer APP, da Sie dies später benötigen, wenn Sie die app in Microsoft Teams mithilfe von App Studio registrieren. Der Editor funktioniert zu diesem Zweck einwandfrei.

<a name="DeployToTeams"></a>

## <a name="deploy-your-app-to-microsoft-teams"></a>Bereitstellen der APP für Microsoft Teams

An diesem Punkt haben Sie eine APP, die im Internet gehostet wird, aber Sie haben keine Möglichkeit, Microsoft Teams mitzuteilen, wo Sie suchen sollen oder sogar, was Ihre APP heißt. Dafür müssen Sie nun ein App-Paket erstellen. Dies ist kaum mehr als eine Textdatei, die das App-Manifest und einige Symbole enthält, die der Microsoft Teams-Client zum ordnungsgemäßen anzeigen und Branding Ihrer APP verwendet. Sie können dieses app-Paket manuell erstellen, oder Sie können APP Studio verwenden, ein Tool, das in Microsoft Teams ausgeführt wird, um den Registrierungsvorgang für die APP zu vereinfachen. App Studio ist die empfohlene Methode zum Erstellen und Aktualisieren des App-Pakets.

Für beide Methoden ist Folgendes erforderlich:

- Die URL, über die Ihre APP im Internet gefunden werden kann.
- Symbole, mit denen Microsoft Teams Ihre APP brandingieren kann. Das Beispiel enthält Platzhaltersymbole, die sich in "src\static\images. Bei Bedarf stellt App Studio auch Standardsymbole bereit.

[!include[Use App Studio to configure the app package](~/includes/get-started/get-started-use-app-studio.md)]

## <a name="update-your-hosted-app"></a>Aktualisieren der gehosteten App

Für die Beispiel-App müssen die folgenden Umgebungsvariablen auf die Werte festgelegt werden, auf die Sie zuvor hingewiesen haben.

```
MICROSOFT_APP_ID=<YOUR BOT'S APP ID>
MICROSOFT_APP_PASSWORD=<YOUR BOT'S PASSWORD>
WEBSITE_NODE_DEFAULT_VERSION=8.9.4
```

Die Vorgehensweise unterscheidet sich je nachdem, wie Sie Ihre APP gehostet haben. Wichtig bei der Verwendung von Umgebungsvariablen ist, dass diese Werte Teil Ihrer Umgebung sind – Sie können über den Code Ihrer APP auf Sie zugreifen, aber Sie werden nicht für Drittanbieter verfügbar gemacht, die die Dateien, aus denen Ihre Website besteht, möglicherweise untersuchen.

Wenn Sie die APP mit ngrok durchführen, müssen Sie einige lokale Umgebungsvariablen einrichten. Es gibt viele Möglichkeiten, dies zu tun, aber am einfachsten ist es, wenn Sie Visual Studio Code verwenden, eine [Startkonfiguration](https://code.visualstudio.com/Docs/editor/debugging#_launch-configurations)hinzuzufügen:

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

MICROSOFT_APP_ID und MICROSOFT_APP_PASSWORD ist jeweils die ID und das Kennwort für Ihren bot.
In NODE_DEBUG erfahren Sie, was in Ihrem bot in der Visual Studio-Code-Debug-Konsole geschieht.
NODE_CONFIG_DIR verweist auf das Verzeichnis im Stammverzeichnis des Repositorys (Standardmäßig wird bei der lokalen Ausführung der APP im Ordner src nach dieser gesucht).

> [!Note]
> Wenn Sie NPM nicht von früher im Lernprogramm angehalten haben, müssen Sie in der `npm stop` Reihenfolge ausgeführt werden, dass Visual Studio Code Ihre Start Konfigurationsvariablen ordnungsgemäß Pickup.

<a name="ConfigureTheAppTab"></a>

## <a name="configure-the-app-tab"></a>Konfigurieren der Registerkarte "App"

Nachdem Sie die app in einem Team installiert haben, müssen Sie Sie so konfigurieren, dass Inhalte angezeigt werden. Wechseln Sie zu einem Kanal im Team, und klicken Sie auf die Schaltfläche **"+"** , um eine neue Registerkarte hinzuzufügen. Sie können dann in `Hello World` der Liste **Registerkarte hinzufügen** auswählen. Anschließend wird ein Konfigurationsdialogfeld angezeigt. In diesem Dialogfeld können Sie auswählen, welche Registerkarte in diesem Kanal angezeigt werden soll. Sobald Sie die Registerkarte ausgewählt haben und `Save` auf klicken, können `Hello World` Sie die Registerkarte anzeigen, die mit der ausgewählten Registerkarte geladen wurde.

<img width="430px" src="~/assets/images/samples-hello-world-tab-configure.png" title="Screenshot von configure" />

### <a name="test-your-bot-in-teams"></a>Testen Sie Ihren bot in Microsoft Teams

Sie können nun mit dem bot in Microsoft Teams interagieren. Wählen Sie einen Kanal im Team aus, in dem Sie Ihre APP registriert `@your-bot-name`haben, und geben Sie gefolgt von Ihrer Nachricht ein. Dies wird als ** \@Erwähnung**bezeichnet. Jede Nachricht, die Sie an den bot senden, wird als Antwort an Sie zurückgesendet.

<img width="450px" title="Bot-Antworten" src="~/assets/images/samples-hello-world-bot.png" />

<a name="ComposeRichMessages"></a>

### <a name="test-your-messaging-extension"></a>Testen der Messaging Erweiterung

Um Ihre Messaging Erweiterung zu testen, können Sie auf die drei Punkte unter dem Eingabefeld in ihrer Unterhaltungsansicht klicken. Ein Menü wird mit der **"Hello World"-** app in diesem Popup angezeigt. Wenn Sie darauf klicken, wird eine Reihe von zufälligen Texten angezeigt. Sie können eine von Ihnen auswählen, und Sie wird in Ihre Unterhaltung eingefügt.

<img width="430px" title="Menü "Messaging Erweiterung"" src="~/assets/images/samples-hello-world-messaging-extensions-menu.png" />

<img width="430px" title="Ergebnis der Messaging-Erweiterung" src="~/assets/images/samples-hello-world-messaging-extensions-result.png" />

Wählen Sie einen der zufälligen Texte aus, und Sie sehen eine Karte, die formatiert und mit ihrer eigenen Nachricht am unteren Rand gesendet werden kann.

<img width="430px" title="Messaging-Durchwahl senden" src="~/assets/images/samples-hello-world-messaging-extensions-send.png" />
