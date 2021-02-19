---
title: 'Lernprogramm – Erstellen Ihrer ersten App mithilfe von C #'
description: 'Erfahren Sie, wie Sie mit dem Erstellen von Microsoft #A0 mit C# oder .NET beginnen.'
keywords: Erste Schritte .net c# csharp
ms.custom: scenarios:getting-started; languages:ASP.NET,C#
ms.topic: tutorial
ms.date: 11/09/2018
ms.openlocfilehash: 29cc4e0f434bf9ece9c6073af84627acc048b628
ms.sourcegitcommit: 6ff8d1244ac386641ebf9401804b8df3854b02dc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/18/2021
ms.locfileid: "50294754"
---
# <a name="create-your-first-teams-app-using-c-or-net"></a>Erstellen Ihrer ersten #A0 mithilfe von C# oder .NET

Dieses Lernprogramm hilft Ihnen beim Erstellen einer Microsoft #A0 mit C# oder .NET.

[!include [prepare your environment](~/includes/prepare-environment.md)]

<a name="GetPrerequisites"></a>

## <a name="get-prerequisites"></a>Erforderliche Komponenten erhalten

Zum Abschließen dieses Lernprogramms müssen Sie die folgenden Tools erhalten:

- [Installieren von Git](https://git-scm.com/downloads)
- [Installieren Visual Studio](https://www.visualstudio.com/downloads/). Sie können die kostenlose Community edition installieren.

Wenn während der Installation eine Option zum PATH hinzugefügt werden `git` kann, wählen Sie sie aus.

Führen Sie in einem Terminalfenster den folgenden Befehl aus, um die Installation zu `git` überprüfen:

```bash
$ git --version
git version 2.17.1.windows.2

```

> [!NOTE]
> Verwenden Sie ein geeignetes Terminalfenster auf Ihrer Plattform. In diesen Beispielen wird Bash verwendet, aber auf den meisten Plattformen ausgeführt.

Stellen Sie sicher, dass Sie die neueste Version von Visual Studio starten und Updates installieren.

Sie können dasselbe Terminalfenster verwenden, um die Befehle in diesem Lernprogramm auszuführen.

<a name="DownloadSample"></a>

## <a name="download-the-sample"></a>Herunterladen des Beispiels

Sie können mit einem einfachen [Hello, World! beginnen.](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-hello-world/csharp) Beispiel in C#. Führen Sie in einem Terminalfenster den folgenden Befehl aus, um das Beispielrepository auf ihren lokalen Computer zu klonen:

```bash
git clone https://github.com/OfficeDev/Microsoft-Teams-Samples.git
```

> [!TIP]
> Sie können [dieses Repository forken,](https://help.github.com/articles/fork-a-repo/) [um](https://github.com/OfficeDev/Microsoft-Teams-Samples) Ihre Änderungen an GitHub zu ändern und zu speichern.

<a name="BuildRun"></a>

## <a name="build-and-run-the-sample"></a>Erstellen und Ausführen des Beispiels

Nachdem das Repository geklont wurde, öffnen Sie mithilfe Visual Studio die Lösungsdatei aus dem `Microsoft.Teams.Samples.HelloWorld.sln` **Verzeichnis Microsoft-Teams-Samples/samples/app-hello-world/csharp** des Beispiels, und wählen Sie aus dem Menü `Build Solution` `Build` aus. Zum Ausführen des Beispiels drücken `F5` Oder wählen Sie aus dem Menü `Start Debugging` `Debug` aus.

Wenn die App gestartet wird, wird ein Browserfenster geöffnet, in dem der Stamm der App gestartet wird. Sie können zu den folgenden URLs navigieren, um zu überprüfen, ob alle App-URLs geladen werden:

- [https://localhost:44327/](https://localhost:44327/)
- [https://localhost:44327/hello](https://localhost:44327/hello)
- [https://localhost:44327/first](https://localhost:44327/first)
- [https://localhost:44327/second]https://localhost:44327/second)

<a name="HostSample"></a>

> [!Note]
> Wenn sie einen Fehler `Could not find a part of the path … bin\roslyn\csc.exe` erhalten, aktualisieren Sie das Paket mit dem Befehl `Update-Package Microsoft.CodeDom.Providers.DotNetCompilerPlatform -r` . Weitere Informationen finden Sie in [dieser Frage unter StackOverflow](https://stackoverflow.com/questions/32780315).

## <a name="host-the-sample-app"></a>Hosten der Beispiel-App

Apps in Microsoft Teams sind Webanwendungen, die eine oder mehrere Funktionen bereitstellen. Damit die Teams-Plattform Ihre App laden kann, muss Ihre App über das Internet erreichbar sein. Damit Ihre App über das Internet erreichbar ist, müssen Sie Ihre App hosten. Sie können sie entweder kostenlos in Microsoft Azure hosten oder einen Tunnel für den lokalen Prozess auf Ihrem Entwicklungscomputer mit `ngrok` erstellen. Wenn Sie mit dem Hosten Ihrer App fertig sind, notieren Sie sich die Stamm-URL. Beispiel: `https://yourteamsapp.ngrok.io` oder `https://yourteamsapp.azurewebsites.net` .

### <a name="tunnel-using-ngrok"></a>Tunnel mit ngrok

Für schnelle Tests können Sie die App auf Ihrem lokalen Computer ausführen und über einen Webendpunkt einen Tunnel dafür erstellen. [ngrok](https://ngrok.com) ist ein kostenloses Tool, mit dem Sie eine Webadresse wie erhalten `https://d0ac14a5.ngrok.io` können. Sie können [ngrok](https://ngrok.com/download) herunterladen und installieren. Stellen Sie sicher, dass Sie es einem Speicherort in Ihrer `PATH` hinzufügen.

Öffnen Sie nach der Installation von ngrok ein neues Terminalfenster, und führen Sie den folgenden Befehl aus, um einen Tunnel zu erstellen:

```bash
ngrok http 44327 -host-header=localhost:44327
```

Im Beispiel wird Port 44327 verwendet, um ihn anzugeben.

Ngrok lauscht Anforderungen aus dem Internet und leitet sie an Ihre App weiter, die unter Port 44327 ausgeführt wird. Um dies zu überprüfen, öffnen Sie Ihren Browser, und `https://d0ac14a5.ngrok.io/hello` wechseln Sie zu, um die Hello-Seite Ihrer App zu laden. Verwenden Sie anstelle dieser URL die Weiterleitungsadresse, die von ngrok in Ihrer Konsolensitzung angezeigt wird.

> [!NOTE]
> Wenn Sie im Build- [](#build-and-run-the-sample) und Ausführungsschritt einen anderen Port verwendet haben, stellen Sie sicher, dass Sie zum Einrichten des Tunnels dieselbe Portnummer `ngrok` verwenden.

> [!TIP]
> Es ist eine gute Idee, in einem `ngrok` anderen Terminalfenster ausgeführt zu werden. Dies geschieht, um zu verhindern, dass ngrok ausgeführt wird, ohne die App zu stören, die Sie beenden, neu erstellen und erneut ausführen müssen. Die `ngrok` Sitzung enthält nützliche Debugginginformationen in diesem Fenster.

Die App ist nur während der aktuellen Sitzung auf Ihrem Entwicklungscomputer verfügbar. Wenn der Computer heruntergefahren wird oder in den Ruhezustand geht, ist der Dienst nicht mehr verfügbar. Denken Sie daran, wenn Sie die App für Tests für andere Benutzer freigeben. Wenn Sie den Dienst neu starten müssen, gibt die App eine neue Adresse zurück, und Sie müssen jeden Speicherort aktualisieren, der diese Adresse verwendet. Die kostenpflichtige Version von ngrok hat diese Einschränkung nicht.

### <a name="host-in-azure"></a>Host in Azure

Microsoft Azure hostet Ihre .NET-Anwendung auf einer kostenlosen Ebene mithilfe der freigegebenen Infrastruktur. Dies ist ausreichend, um das Beispiel ausführen zu `Hello World` können. Weitere Informationen finden Sie unter [Erstellen eines neuen kostenlosen Kontos](https://azure.microsoft.com/free/).

Visual Studio bietet integrierte Unterstützung für die App-Bereitstellung für verschiedene Anbieter, einschließlich Azure.

<img width="530px" alt="Visual Studio" src="~/assets/images/get-started/publishtoazure1.png"/>

[!include [Use App Studio to configure the app package](~/includes/get-started/get-started-use-app-studio.md)]

## <a name="update-the-credentials-for-your-hosted-app"></a>Aktualisieren der Anmeldeinformationen für Ihre gehostete App

Die Beispiel-App erfordert, dass die folgenden Umgebungsvariablen auf die Werte festgelegt werden, die Sie zuvor notieren.

Öffnen Sie die appsettings.json-Datei. Aktualisieren Sie *den MicrosoftAppId-Wert* mit Ihrer Bot-ID, die Sie zuvor gespeichert haben. Aktualisieren Sie *microsoftAppPassword* mit dem bot-Kennwort, das Sie zuvor gespeichert haben.

<img width="560px" alt="Setting the keys" src="~/assets/images/get-started/get-started-net-azure-add-keys.png"/>

Nachdem diese Änderungen vorgenommen wurden, erstellen Sie die App neu. Wenn Sie ngrok verwenden, führen Sie die App lokal aus, und wenn Sie in Azure hosten, stellen Sie die App erneut bereit.

## <a name="configure-the-app-tab"></a>Konfigurieren der Registerkarte "App"

Nachdem Sie die App in einem Team installiert haben, müssen Sie sie so konfigurieren, dass Inhalte angezeigt werden. Wechseln Sie zu einem Kanal im Team, in dem Sie die Beispiel-App installiert haben, und klicken Sie auf die Schaltfläche **"+",** um eine neue Registerkarte hinzuzufügen. Sie können dann aus `Hello World` der Registerkartenliste **Hinzufügen** auswählen. Anschließend wird ihnen ein Konfigurationsdialogfeld angezeigt. In diesem Dialogfeld können Sie auswählen, welche Registerkarte in diesem Kanal angezeigt werden soll. Sobald Sie die Registerkarte ausgewählt haben und auf klicken, wird die Registerkarte mit der von Ihnen ausgewählten `Save` `Hello World` Registerkarte geladen.

<img width="530px" alt="Screenshot of configure" src="~/assets/images/samples-hello-world-tab-configure.png" />

### <a name="test-your-bot-in-teams"></a>Testen Des Bots in Teams

Sie können jetzt mit dem Bot in Teams interagieren. Wählen Sie einen Kanal im Team aus, in dem Sie Ihre App registriert haben, und geben Sie `@your-bot-name` ein. Dies wird als Erwähnung **\@ bezeichnet.** Alle Nachrichten, die Sie an den Bot senden, werden als Antwort an Sie zurückgeschickt.

<img width="450px" alt="Bot responses" src="~/assets/images/samples-hello-world-bot.png" />

### <a name="test-your-messaging-extension"></a>Testen Der Messagingerweiterung

Um Ihre Messagingerweiterung zu testen, können Sie auf die drei Punkte unter dem Eingabefeld in der Unterhaltungsansicht klicken. Ein Menü wird mit der **"Hello World"-App** angezeigt. Wenn Sie darauf klicken, wird eine Reihe zufälliger Texte angezeigt. Sie können einen beliebigen auswählen, und er wird in Ihre Unterhaltung eingefügt.

<img width="530px" alt="Messaging extension menu" src="~/assets/images/samples-hello-world-messaging-extensions-menu.png" />

<img width="530px" alt="Messaging extension result" src="~/assets/images/samples-hello-world-messaging-extensions-result.png" />

Wählen Sie einen der zufälligen Texte aus, und unten wird eine Karte formatiert und kann mit Ihrer eigenen Nachricht gesendet werden.

<img width="530px" alt="Messaging extension send" src="~/assets/images/samples-hello-world-messaging-extensions-send.png" />
