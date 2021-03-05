---
title: 'Lernprogramm – Erstellen Ihrer ersten App mithilfe von C #'
description: Erfahren Sie, wie Sie mit dem Erstellen von Microsoft Teams-Apps mit C# oder .NET beginnen.
keywords: Erste Schritte .net c# csharp
ms.custom: scenarios:getting-started; languages:ASP.NET,C#
ms.topic: tutorial
ms.date: 11/09/2018
ms.openlocfilehash: ededd0800c7f789469e79e2a475c125b7fc37795
ms.sourcegitcommit: 5cb3453e918bec1173899e7591b48a48113cf8f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/04/2021
ms.locfileid: "50449355"
---
# <a name="create-your-first-teams-app-using-c-or-net"></a>Erstellen Ihrer ersten Teams-App mithilfe C# oder .NET

Dieses Lernprogramm hilft Ihnen beim Erstellen einer Microsoft Teams-App mit C# oder .NET. Dazu müssen Sie Folgendes tun:

* Vorbereiten der Umgebung
* Erforderliche Komponenten erhalten
* Herunterladen des Beispiels
* Erstellen und Ausführen des Beispiels
* Hosten der Beispiel-App
* Aktualisieren der Anmeldeinformationen für Ihre gehostete App
* Konfigurieren der Registerkarte "App"

[!include [prepare your environment](~/includes/prepare-environment.md)]

<a name="GetPrerequisites"></a>

## <a name="get-prerequisites"></a>Erforderliche Komponenten erhalten

Zum Abschließen dieses Lernprogramms müssen Sie die folgenden Tools installieren:

- [Installieren von Git](https://git-scm.com/downloads)
- [Installieren von Visual Studio](https://www.visualstudio.com/downloads/)

Sie können die kostenlose Community edition von Visual Studio. Wenn es während der Installation eine Option gibt, die dem Pfad `git` hinzugefügt werden kann, wählen Sie ihn aus. Führen Sie in einem Terminalfenster den folgenden Befehl aus, um die Installation zu `git` überprüfen:

```bash
$ git --version
git version 2.17.1.windows.2

```

> [!NOTE]
> Verwenden Sie ein geeignetes Terminalfenster auf Ihrer Plattform. Diese Beispiele verwenden Git Bash, können jedoch auf den meisten Plattformen ausgeführt werden.

Öffnen Sie die neueste Version von Visual Studio, und installieren Sie alle Updates.

Sie können dasselbe Terminalfenster verwenden, um die Befehle in diesem Lernprogramm auszuführen.

<a name="DownloadSample"></a>

## <a name="download-the-sample"></a>Herunterladen des Beispiels

Sie können mit einem einfachen [Hello, World! beginnen.](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-hello-world/csharp) Beispiel in C#. Führen Sie in einem Terminalfenster den folgenden Befehl aus, um das Beispielrepository auf Ihren Computer zu klonen:

```bash
git clone https://github.com/OfficeDev/Microsoft-Teams-Samples.git
```

> [!TIP]
> Sie können dieses [](https://github.com/OfficeDev/Microsoft-Teams-Samples) Repository [forken,](https://help.github.com/articles/fork-a-repo/) um Ihre Änderungen an GitHub zu ändern und zu speichern.

<a name="BuildRun"></a>

## <a name="build-and-run-the-sample"></a>Erstellen und Ausführen des Beispiels

Nachdem das Repository geklont wurde, öffnen Sie mithilfe von Visual Studio die Lösungsdatei **Microsoft.Teams.Samples.HelloWorld.sln** aus dem **Microsoft-Teams-Samples/samples/app-hello-world/csharp-Verzeichnis** des Beispiels. Wählen Sie dann **im Menü Build** die Option Lösung erstellen aus.  Drücken Sie zum Ausführen des Beispiels **F5,** oder wählen Sie **Debuggen starten** im Menü **Debuggen** aus.

Wenn die App gestartet wird, wird ein Browserfenster geöffnet, in dem der Stamm der App gestartet wird. Sie können zu den folgenden URLs wechseln, um zu überprüfen, ob alle App-URLs geladen werden:

- [https://localhost:44327/](https://localhost:44327/)
- [https://localhost:44327/hello](https://localhost:44327/hello)
- [https://localhost:44327/first](https://localhost:44327/first)
- [https://localhost:44327/second]https://localhost:44327/second)

<a name="HostSample"></a>

> [!Note]
> Wenn sie einen Fehler `Could not find a part of the path … bin\roslyn\csc.exe` erhalten, aktualisieren Sie das Paket mit dem Befehl `Update-Package Microsoft.CodeDom.Providers.DotNetCompilerPlatform -r` . Weitere Informationen finden Sie in [dieser Frage unter Stack Overflow](https://stackoverflow.com/questions/32780315).

## <a name="host-the-sample-app"></a>Hosten der Beispiel-App

Apps in Microsoft Teams sind Webanwendungen, die eine oder mehrere Funktionen bereitstellen. Damit die Teams-Plattform Ihre App laden kann, muss Ihre App im Internet verfügbar sein. Dazu müssen Sie Ihre App hosten. Sie können sie entweder kostenlos in Microsoft Azure hosten oder mithilfe von einen Tunnel für den lokalen Prozess auf Ihrem Computer `ngrok` erstellen. Notieren Sie sich nach dem Hosten Ihrer App die Stamm-URL, z. B. `https://yourteamsapp.ngrok.io` oder `https://yourteamsapp.azurewebsites.net` .

### <a name="tunnel-using-ngrok"></a>Tunnel mit ngrok

Für schnelle Tests können Sie die App auf Ihrem Computer ausführen und über einen Webendpunkt einen Tunnel dafür erstellen. [`ngrok`](https://ngrok.com) ist ein kostenloses Tool, mit dem Sie eine Webadresse erhalten können, z. B. `https://d0ac14a5.ngrok.io` . Sie können [ngrok herunterladen und](https://ngrok.com/download) installieren und an einem Speicherort in Ihrer `PATH` hinzufügen.

Öffnen Sie nach `ngrok` der Installation ein neues Terminalfenster, und führen Sie den folgenden Befehl aus, um einen Tunnel zu erstellen:

```bash
ngrok http 44327 -host-header=localhost:44327
```

`Ngrok` lauscht Anfragen aus dem Internet und leitet sie an Ihre App weiter, die an Port 44327 ausgeführt wird. Um dies zu überprüfen, öffnen Sie Ihren Browser, und `https://d0ac14a5.ngrok.io/hello` wechseln Sie zu, um die Hello-Seite Ihrer App zu laden. Verwenden Sie anstelle dieser URL die Weiterleitungsadresse, die `ngrok` in Der Konsolensitzung angezeigt wird.

> [!NOTE]
> Wenn Sie im Build- [](#build-and-run-the-sample) und Ausführungsschritt einen anderen Port verwendet haben, stellen Sie sicher, dass Sie zum Einrichten des Tunnels dieselbe Portnummer `ngrok` verwenden.

> [!TIP]
> Es ist eine gute Idee, in einem `ngrok` anderen Terminalfenster ausgeführt zu werden. Dies geschieht, um `ngrok` die Ausführung zu unterlaufen, ohne die App zu stören. Sie müssen die App beenden, neu erstellen und erneut ausführen. Die `ngrok` Sitzung enthält nützliche Debugginginformationen in diesem Fenster.

Die App ist nur während der aktuellen Sitzung auf Ihrem Computer verfügbar. Wenn der Computer heruntergefahren wird oder in den Ruhezustand geht, ist der Dienst nicht mehr verfügbar. Denken Sie daran, wenn Sie die App für Tests für andere Benutzer freigeben. Wenn Sie den Dienst neu starten müssen, gibt die App eine neue Adresse zurück, und Sie müssen jeden Speicherort aktualisieren, der diese Adresse verwendet. Die kostenpflichtige Version von `ngrok` hat diese Einschränkung nicht.

### <a name="host-in-azure"></a>Host in Azure

Microsoft Azure hostet Ihre .NET-Anwendung auf einer kostenlosen Ebene mithilfe der freigegebenen Infrastruktur. Dies ist ausreichend, um das Beispiel ausführen zu `Hello World` können. Weitere Informationen finden Sie unter [Erstellen eines neuen kostenlosen Azure-Kontos](https://azure.microsoft.com/free/).

Visual Studio bietet integrierte Unterstützung für die App-Bereitstellung für verschiedene Anbieter, einschließlich Azure.

<img width="530px" alt="Visual Studio" src="~/assets/images/get-started/publishtoazure1.png"/>

[!include [Use App Studio to configure the app package](~/includes/get-started/get-started-use-app-studio.md)]

## <a name="update-the-credentials-for-your-hosted-app"></a>Aktualisieren der Anmeldeinformationen für Ihre gehostete App

Für die Beispiel-App müssen die Umgebungsvariablen auf die Werte festgelegt werden, die Sie in der [Textdatei gespeichert haben.](~/includes/get-started/get-started-use-app-studio.md#bots)

Öffnen Sie appsettings.jsOn-Datei. Aktualisieren Sie **den MicrosoftAppId-Wert** mit Ihrer Bot-ID, die Sie in der Textdatei gespeichert haben. Aktualisieren Sie **microsoftAppPassword** mit dem von Ihnen gespeicherten Botkennwort.

<img width="560px" alt="Setting the keys" src="~/assets/images/get-started/get-started-net-azure-add-keys.png"/>

Nachdem diese Änderungen vorgenommen wurden, erstellen Sie die App neu. Wenn Sie ngrok verwenden, führen Sie die App lokal aus, und wenn Sie in Azure hosten, stellen Sie die App erneut bereit.

## <a name="configure-the-app-tab"></a>Konfigurieren der Registerkarte "App"

Nachdem Sie die App in einem Team installiert haben, müssen Sie sie so konfigurieren, dass Inhalte angezeigt werden. Wechseln Sie zu einem Kanal im Team, in dem Sie die Beispiel-App installiert haben, und wählen Sie die Schaltfläche **"+"** aus, um eine neue Registerkarte hinzuzufügen. Wählen **Sie Hello World** in der **Registerkartenliste** Hinzufügen aus. Es wird ein Konfigurationsdialogfeld angezeigt, mit dem Sie die Registerkarte auswählen können, die in diesem Kanal angezeigt werden soll. Nachdem Sie die Registerkarte ausgewählt und die Option **Speichern** ausgewählt haben, wird die Registerkarte `Hello World` mit der Registerkarte geladen.

<img width="530px" alt="Screenshot of configure" src="~/assets/images/samples-hello-world-tab-configure.png" />

### <a name="test-your-bot-in-teams"></a>Testen Des Bots in Teams

Jetzt können Sie den Bot in Teams testen. Wählen Sie einen Kanal im Team aus, in dem Sie Ihre App registriert haben, und geben Sie `@your-bot-name` ein. Dies wird als Erwähnung **\@ bezeichnet.** Der Bot antwortet auf jede nachricht, die Sie senden.

<img width="450px" alt="Bot responses" src="~/assets/images/samples-hello-world-bot.png" />

### <a name="test-your-messaging-extension"></a>Testen Der Messagingerweiterung

Zum Testen Ihrer Messagingerweiterung können Sie **... unter** dem Eingabefeld in der Unterhaltungsansicht auswählen. Ein Menü mit der **App "Hello World"** wird angezeigt. Wenn Sie sie auswählen, wird eine Reihe zufälliger Texte angezeigt. Sie können einen zufälligen Text auswählen, der in Ihre Unterhaltung eingefügt wird.

<img width="530px" alt="Messaging extension menu" src="~/assets/images/samples-hello-world-messaging-extensions-menu.png" />

<img width="530px" alt="Messaging extension result" src="~/assets/images/samples-hello-world-messaging-extensions-result.png" />

Wählen Sie einen der zufälligen Text aus. Es wird eine Karte angezeigt, die mit Ihrer eigenen Nachricht formatiert und zum Senden bereit ist.

<img width="530px" alt="Messaging extension send" src="~/assets/images/samples-hello-world-messaging-extensions-send.png" />
