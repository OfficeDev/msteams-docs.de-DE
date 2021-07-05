---
title: 'Lernprogramm – Erstellen Ihrer ersten App mit C #'
description: Erfahren Sie, wie Sie mit C# oder .NET mit dem Erstellen Microsoft Teams Apps beginnen.
keywords: Erste Schritte .net c# csharp
ms.custom: scenarios:getting-started; languages:ASP.NET,C#
localization_priority: Normal
ms.topic: tutorial
ms.date: 11/09/2018
ms.openlocfilehash: f63e729400fa74f1675faddbe0b5f8fa101c8824
ms.sourcegitcommit: 9d63611974ba8a7e7f19ceea35e50189a2e90434
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/02/2021
ms.locfileid: "53254344"
---
# <a name="build-your-first-teams-app-using-c"></a>Erstellen Ihrer ersten Teams-App mit C #

In diesem Lernprogramm erfahren Sie, wie Sie Ihre erste Microsoft Teams-App mit .NET oder C# erstellen. Außerdem werden Sie durch die folgenden Schritte geführt:

1. [Vorbereiten der Umgebung](#prepare-your-environment)
1. [Voraussetzungen abrufen](#GetPrerequisites)
1. [Beispiel herunterladen](#DownloadSample)
1. [Erstellen und Ausführen des Beispiels](#BuildRun)
1. [Hosten der Beispiel-App](#hostsample)
1. [Aktualisieren der Anmeldeinformationen für Ihre gehostete App](#updatecredentials)
1. [Konfigurieren der Registerkarte "App"](#configureapptab)

<a name="prepare-your-environment"></a>
[!include [prepare your environment](~/includes/prepare-environment.md)]

<a name="GetPrerequisites"></a>

## <a name="get-prerequisites"></a>Voraussetzungen abrufen

Um dieses Lernprogramm abzuschließen, müssen Sie die folgenden Tools installieren:

- [Installieren von Git](https://git-scm.com/downloads)
- [Installieren von Visual Studio](https://www.visualstudio.com/downloads/)

Sie können die kostenlose Community-Edition von Visual Studio installieren. Wenn es während der Installation eine Option zum Hinzufügen `git` zum Pfad gibt, wählen Sie ihn aus. Führen Sie in einem Terminalfenster den folgenden Befehl aus, um die Installation zu `git` überprüfen:

```bash
$ git --version
git version 2.17.1.windows.2

```

> [!NOTE]
> Verwenden Sie ein geeignetes Terminalfenster auf Ihrer Plattform. Diese Beispiele verwenden Git Bash, können aber auf den meisten Plattformen ausgeführt werden.

Öffnen Sie die neueste Version von Visual Studio, und installieren Sie alle Updates.

Sie können dasselbe Terminalfenster verwenden, um die Befehle in diesem Lernprogramm auszuführen.

<a name="DownloadSample"></a>

## <a name="download-the-sample"></a>Beispiel herunterladen

Sie können mit einem einfachen [Hello, World beginnen!](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-hello-world/csharp) Beispiel in C#. Führen Sie in einem Terminalfenster den folgenden Befehl aus, um das Beispiel-Repository auf Ihrem Computer zu klonen:

```bash
git clone https://github.com/OfficeDev/Microsoft-Teams-Samples.git
```

> [!TIP]
> Sie können dieses [Repository verzweigen,](https://github.com/OfficeDev/Microsoft-Teams-Samples) um Ihre Änderungen zu ändern und in GitHub zu speichern. [](https://help.github.com/articles/fork-a-repo/)

<a name="BuildRun"></a>

## <a name="build-and-run-the-sample"></a>Erstellen und Ausführen des Beispiels

Sie können das Geklonte erstellen und ausführen. 

**So erstellen Sie das geklonte Beispiel und führen es aus**

1. Öffnen Sie die Projektmappendatei **"Microsoft.Teams". Samples.HelloWorld.sln** aus dem **Microsoft-Teams-Samples/samples/app-hello-world/csharp-Verzeichnis** des Beispiels.
1. Wählen Sie im Menü "Erstellen" die Option **"Projektmappe** **erstellen"** aus.
1. Wählen Sie **F5** aus, oder wählen Sie im Menü **"Debuggen"** die Option **"Debuggen starten"** aus, um das Beispiel auszuführen.

    Wenn die App gestartet wird, wird ein Browserfenster geöffnet, in dem der Stamm der App gestartet wird. Sie können die folgenden URLs aufrufen, um zu überprüfen, ob alle App-URLs geladen werden:

    - `https://localhost:44327/`
    - `https://localhost:44327/hello`
    - `https://localhost:44327/first`
    - `https://localhost:44327/second`

    > [!Note]
    > Wenn ein Fehler angezeigt wird, aktualisieren Sie `Could not find a part of the path … bin\roslyn\csc.exe` das Paket mit dem Befehl `Update-Package Microsoft.CodeDom.Providers.DotNetCompilerPlatform -r` . Weitere Informationen finden Sie in [dieser Frage auf Stack Overflow](https://stackoverflow.com/questions/32780315).

    <a name="hostsample"></a>
    ## <a name="deploy-your-sample-app"></a>Bereitstellen Ihrer Beispiel-App

    Apps in Microsoft Teams sind Webanwendungen, die eine oder mehrere Funktionen bereitstellen. Damit die Teams Plattform Ihre App laden kann, muss Ihre App im Internet verfügbar sein. Dazu müssen Sie Ihre App hosten. Sie können es entweder kostenlos in Microsoft Azure hosten oder mithilfe von `ngrok` . Notieren Sie sich nach dem Hosten der App die Stamm-URL, z. `https://yourteamsapp.ngrok.io` B. oder `https://yourteamsapp.azurewebsites.net` .

### <a name="tunnel-using-ngrok"></a>Tunnel mit ngrok

Für schnelle Tests können Sie die App auf Ihrem Computer ausführen und einen Tunnel über einen Webendpunkt erstellen. [`ngrok`](https://ngrok.com) ist ein kostenloses Tool, mit dem Sie eine Webadresse abrufen können, `https://d0ac14a5.ngrok.io` z. B. . Sie können ngrok [herunterladen und installieren](https://ngrok.com/download) und zu einem Speicherort in Ihrer `PATH` hinzufügen.

Öffnen Sie nach der Installation `ngrok` ein neues Terminalfenster, und führen Sie den folgenden Befehl aus, um einen Tunnel zu erstellen:

```bash
ngrok http 44327 -host-header=localhost:44327
```

`Ngrok` antwortet auf Anforderungen aus dem Internet und leitet sie an Ihre App weiter, die an Port 44327 ausgeführt wird. 

**So überprüfen Sie die Antwort**

1. Öffnen Sie Ihren Browser, und navigieren Sie zu `https://d0ac14a5.ngrok.io/hello`. Dadurch wird die Hello-Seite Ihrer App geladen.
1. Verwenden Sie anstelle der in Schritt 1 erwähnten URL die Weiterleitungsadresse, die `ngrok` in Ihrer Konsolensitzung angezeigt wird.
    > [!NOTE]
    > Wenn Sie im [Build- und Ausführungsschritt](#build-and-run-the-sample) einen anderen Port verwendet haben, stellen Sie sicher, dass Sie die gleiche Portnummer zum Einrichten des `ngrok` Tunnels verwenden.
    > [!TIP]
    > Es empfiehlt sich, in einem anderen Terminalfenster ausgeführt zu `ngrok` werden. Dies geschieht, um die `ngrok` Ausführung ohne Beeinträchtigung der App aufzuhalten. Sie müssen die App beenden, neu erstellen und erneut ausführen. Die `ngrok` Sitzung enthält nützliche Debuginformationen in diesem Fenster.

    Die App ist nur während der aktuellen Sitzung auf Ihrem Computer verfügbar. Wenn der Computer heruntergefahren wird oder in den Ruhezustand wechselt, ist der Dienst nicht mehr verfügbar. Denken Sie daran, wenn Sie die App zu Testzwecken für andere Benutzer freigeben. Wenn Sie den Dienst neu starten müssen, gibt die App eine neue Adresse zurück, und Sie müssen jeden Speicherort aktualisieren, der diese Adresse verwendet. Für die kostenpflichtige Version von `ngrok` gilt diese Einschränkung nicht.

### <a name="host-in-azure"></a>Hosten in Azure

Microsoft Azure hostet Ihre .NET-Anwendung auf einer kostenlosen Ebene mithilfe der freigegebenen Infrastruktur. Dies reicht aus, um das `Hello World` Beispiel auszuführen. Weitere Informationen finden Sie unter [Erstellen eines neuen kostenlosen Azure-Kontos.](https://azure.microsoft.com/free/)

Visual Studio bietet integrierte Unterstützung für die App-Bereitstellung für verschiedene Anbieter, einschließlich Azure:

<img width="530px" alt="Visual Studio" src="~/assets/images/get-started/publishtoazure1.png"/>

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

    Sie können Ihre App über das Teams Entwicklerportal konfigurieren. Das Manifest befindet sich unter "Verteilen". Sie können das Manifest verwenden, um Funktionen, erforderliche Ressourcen und andere wichtige Attribute für Ihre App zu konfigurieren. Weitere Informationen zum Konfigurieren Ihrer App mithilfe des Entwicklerportals finden Sie unter [Teams Developer Portal.](../concepts/build-and-test/teams-developer-portal.md)

    <img width="430px" alt="Screenshot of configure tdp" src="~/assets/images/Screen4.png"/>
---

<a name="updatecredentials"></a>
## <a name="update-the-credentials-for-your-hosted-app"></a>Aktualisieren der Anmeldeinformationen für Ihre gehostete App

Die Beispiel-App erfordert, dass die Umgebungsvariablen auf die Werte festgelegt werden, die Sie in der Textdatei gespeichert haben.

**So aktualisieren Sie die Anmeldeinformationen für Ihre gehostete App**

1. die Datei `appsettings.json` öffnen. 
1. Aktualisieren Sie den **MicrosoftAppId-Wert** mit Ihrer Bot-ID, die Sie in der Textdatei gespeichert haben. 
1. Aktualisieren Sie das **MicrosoftAppPassword** mit dem Bot-Kennwort, das Sie gespeichert haben.

    <img width="560px" alt="Setting the keys" src="~/assets/images/get-started/get-started-net-azure-add-keys.png"/>

    Nachdem diese Änderungen vorgenommen wurden, erstellen Sie die App neu. Wenn Sie ngrok verwenden, führen Sie die App lokal aus, und wenn Sie in Azure hosten, stellen Sie die App erneut bereit.

<a name="configureapptab"></a>
## <a name="configure-the-app-tab"></a>Konfigurieren der Registerkarte "App"

Nachdem Sie die App in Teams installiert haben, müssen Sie sie so konfigurieren, dass der Inhalt angezeigt wird. 

**So konfigurieren Sie die Registerkarte "App"**

1. Wechseln Sie zu einem Kanal im Team, in dem Sie die Beispiel-App installiert haben, und wählen Sie die Schaltfläche **"+"** aus, um eine neue Registerkarte hinzuzufügen.
1. Wählen Sie **"Hello World"** aus der **Registerkartenliste hinzufügen** aus. Es wird ein Konfigurationsdialogfeld angezeigt, in dem Sie die Registerkarte auswählen können, die in diesem Kanal angezeigt werden soll. 
1. Wählen Sie **Speichern** aus. Die `Hello World` Registerkarte wird mit der Registerkarte geladen.

    <img width="530px" alt="Screenshot of configure" src="~/assets/images/samples-hello-world-tab-configure.png" />

### <a name="test-your-bot-in-teams"></a>Testen Ihres Bots in Teams

Sie können den Bot jetzt in Teams testen. 

**So testen Sie Ihren Bot**

* Wählen Sie einen Kanal im Team aus, in dem Sie Ihre App registriert haben, und geben Sie `@your-bot-name` diesen ein. Dies wird als **\@ Erwähnung bezeichnet.** Der Bot antwortet auf eine beliebige Nachricht, die Sie senden.

    <img width="450px" alt="Bot responses" src="~/assets/images/samples-hello-world-bot.png" />

### <a name="test-your-messaging-extension"></a>Testen Der Messaging-Erweiterung

**So testen Sie Ihre Messaging-Erweiterung**
1. Wählen Sie **...** unterhalb des Eingabefelds in der Unterhaltungsansicht aus. Ein Menü mit der **App "Hello World"** wird angezeigt. 
1. Wählen Sie das Menü aus, es wird eine Reihe zufälliger Texte angezeigt. Sie können einen beliebigen Text auswählen, der in Ihre Unterhaltung eingefügt wird.

    <img width="530px" alt="Messaging extension menu" src="~/assets/images/samples-hello-world-messaging-extensions-menu1.png" />

    <img width="530px" alt="Messaging extension result" src="~/assets/images/samples-hello-world-messaging-extensions-result1.png" />

1. Wählen Sie einen beliebigen Text aus. Eine Karte, die mit Ihrer eigenen Nachricht formatiert und zum Senden bereit ist, wird angezeigt.

    <img width="530px" alt="Messaging extension send" src="~/assets/images/samples-hello-world-messaging-extensions-send.png" />

## <a name="see-also"></a>Weitere Informationen:

* [Übersicht über Lernprogramme](code-samples.md)
* [Erstellen einer Unterhaltungs-Bot-App](first-app-bot.md)
* [Erstellen einer Messaging-Erweiterung](first-message-extension.md)
* [Codebeispiele](https://github.com/OfficeDev/Microsoft-Teams-Samples)