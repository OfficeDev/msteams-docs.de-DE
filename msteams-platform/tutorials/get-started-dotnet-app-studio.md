---
title: 'Lernprogramm – Erstellen Ihrer ersten App mit C #'
description: 'Erfahren Sie, wie Sie mit dem Erstellen von Microsoft #A0 mit C#/.NET beginnen.'
keywords: Erste Schritte .net c# csharp
ms.custom: scenarios:getting-started; languages:ASP.NET,C#
ms.topic: tutorial
ms.date: 11/09/2018
ms.openlocfilehash: c28c4d00c375b8e37f82c343eec2c5405ae0c1c8
ms.sourcegitcommit: fa64b83c0b534bf7a89f256880d5b5ca193e4b04
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/28/2021
ms.locfileid: "50037039"
---
# <a name="create-your-first-microsoft-teams-app-using-c"></a>Erstellen Ihrer ersten Microsoft #A0 mit C #

Dieses Lernprogramm hilft Ihnen, mit dem Erstellen einer Microsoft #A0 mit C# auf .NET zu beginnen.

[!include [prepare your environment](~/includes/prepare-environment.md)]

<a name="GetPrerequisites"></a>

## <a name="get-prerequisites"></a>Voraussetzungen erhalten

Um dieses Lernprogramm abschließen zu können, benötigen Sie die folgenden Tools:

- [Installieren von Git](https://git-scm.com/downloads)
- [Installieren Visual Studio](https://www.visualstudio.com/downloads/). Sie können die kostenlose Community Edition installieren.

Wenn während der Installation eine Option zum Hinzufügen zum PFAD angezeigt wird, wählen Sie `git` dies aus. Es ist praktisch.

Überprüfen Sie `git` die Installation, indem Sie folgendes in einem Terminalfenster ausführen:
> [!NOTE]
> Verwenden Sie das Terminalfenster, mit dem Sie sich auf Ihrer Plattform am besten aus sind. Diese Beispiele verwenden Bash, werden aber auf den meisten Plattformen ausgeführt.

```bash
$ git --version
git version 2.17.1.windows.2

```

Stellen Sie sicher, dass Sie die neueste Version von Visual Studio installieren und alle Updates installieren, wenn sie angezeigt werden.

Sie können weiterhin dieses Terminalfenster verwenden, um die Befehle auszuführen, die in diesem Lernprogramm folgen.

<a name="DownloadSample"></a>

## <a name="download-the-sample"></a>Herunterladen des Beispiels

Wir haben ein einfaches [Hello, World! bereitgestellt.](https://github.com/OfficeDev/msteams-samples-hello-world-csharp) Beispiel in C#, um Sie zu beginnen. Führen Sie in einem Terminalfenster den folgenden Befehl aus, um das Beispielrepository auf Ihrem lokalen Computer zu klonen:

```bash
git clone https://github.com/OfficeDev/msteams-samples-hello-world-csharp.git
```

> [!TIP]
> Sie können [dieses Repository ver forken,](https://help.github.com/articles/fork-a-repo/) [](https://github.com/OfficeDev/msteams-samples-hello-world-csharp) wenn Sie Ihre Änderungen an GitHub ändern und zur zukünftigen Referenz einchecken möchten.

<a name="BuildRun"></a>

## <a name="build-and-run-the-sample"></a>Erstellen und Ausführen des Beispiels

Nachdem das Repository geklont wurde, Visual Studio Sie die Lösungsdatei aus dem Stammverzeichnis des Beispiels öffnen und im `Microsoft.Teams.Samples.HelloWorld.sln` `Build Solution` Menü `Build` klicken. Sie können das Beispiel ausführen, indem Sie das Menü drücken `F5` `Start Debugging` oder `Debug` auswählen.

Wenn die App gestartet wird, wird ein Browserfenster mit dem Stamm der gestarteten App geöffnet. Sie können zu den folgenden URLs navigieren, um zu überprüfen, ob alle URLs geladen werden:

- [http://localhost:3333](http://localhost:3333)
- [http://localhost:3333/hello](http://localhost:3333/hello)
- [http://localhost:3333/first](http://localhost:3333/first)
- [http://localhost:3333/second](http://localhost:3333/second)

<a name="HostSample"></a>

> [!Note]
> Wenn sie eine Fehlermeldung wie `Could not find a part of the path … bin\roslyn\csc.exe` erhalten, versuchen Sie, das Paket mit dem Befehl zu `Update-Package Microsoft.CodeDom.Providers.DotNetCompilerPlatform -r` aktualisieren. Weitere Informationen finden Sie in dieser Frage auf [StackOverflow.](https://stackoverflow.com/questions/32780315)

## <a name="host-the-sample-app"></a>Hosten der Beispiel-App

Denken Sie daran, dass Apps in Microsoft Teams Webanwendungen sind, die eine oder mehrere Funktionen verfügbar machen. Damit die Plattform Teams Ihre App laden kann, muss Ihre App über das Internet erreichbar sein. Damit Ihre App über das Internet erreichbar ist, müssen Sie Ihre App hosten. Sie können sie entweder kostenlos in Microsoft Azure hosten oder einen Tunnel für den lokalen Prozess auf Ihrem Entwicklungscomputer `ngrok` erstellen. Wenn Sie mit dem Hosten Ihrer App fertig sind, notieren Sie sich die Stamm-URL. Sie sieht in etwa wie: `https://yourteamsapp.ngrok.io` oder `https://yourteamsapp.azurewebsites.net` aus.

### <a name="tunnel-using-ngrok"></a>Tunnel mit ngrok

Für schnelle Tests können Sie die App auf Ihrem lokalen Computer ausführen und einen Tunnel über einen Webendpunkt erstellen. [ngrok](https://ngrok.com) ist ein kostenloses Tool, mit dem Sie genau das tun können. Mit ngrok können Sie eine Webadresse wie z. B. `https://d0ac14a5.ngrok.io` (diese URL ist nur ein Beispiel) erhalten. Sie können [ngrok](https://ngrok.com/download) für Ihre Umgebung herunterladen und installieren. Stellen Sie sicher, dass Sie es einem Speicherort in Ihrer `PATH` hinzufügen.

Nach der Installation können Sie ein neues Terminalfenster öffnen und den folgenden Befehl ausführen, um einen Tunnel zu erstellen. Im Beispiel wird Port 3333 verwendet. Geben Sie ihn daher unbedingt hier an.

```bash
ngrok http 3333 -host-header=localhost:3333
```

Ngrok hört Anforderungen aus dem Internet ab und führt sie an Ihre App weiter, die an Port 3333 ausgeführt wird. Sie können dies überprüfen, indem Sie Ihren Browser öffnen und die `https://d0ac14a5.ngrok.io/hello` Hello-Seite Ihrer App laden. Verwenden Sie anstatt dieser URL unbedingt die Weiterleitungsadresse, die ngrok in Ihrer Konsolensitzung angezeigt hat.

> [!NOTE]
> Wenn Sie im Build einen [](#build-and-run-the-sample) anderen Port verwendet haben, und führen Sie den obigen Schritt aus, stellen Sie sicher, dass Sie zum Einrichten des Tunnels dieselbe Portnummer `ngrok` verwenden.
> [!TIP]
> Es ist eine gute Idee, in einem anderen Terminalfenster ausgeführt zu werden, damit sie ausgeführt wird, ohne die App zu stören, die Sie später möglicherweise beenden, neu erstellen und `ngrok` erneut ausführen müssen. Die `ngrok` Sitzung gibt nützliche Debuginformationen in diesem Fenster zurück.

Die App ist nur während der aktuellen Sitzung auf Ihrem Entwicklungscomputer verfügbar. Wenn der Computer heruntergefahren wird oder in den Ruhezustand geht, ist der Dienst nicht mehr verfügbar. Denken Sie daran, wenn Sie die App für Tests durch andere Benutzer freigeben. Wenn Sie den Dienst neu starten müssen, wird eine neue Adresse zurückgeben, und Sie müssen jeden Ort aktualisieren, der diese Adresse verwendet. Für die kostenpflichtige Version von Ngrok gilt diese Einschränkung nicht.

### <a name="host-in-azure"></a>Host in Azure

Mit Microsoft Azure können Sie Ihre .NET-Anwendung mithilfe einer gemeinsam genutzten Infrastruktur auf einer kostenlosen Ebene hosten. Dies reicht aus, um dieses Beispiel ausführen zu `Hello World` können. Weitere [Informationen finden Sie unter Erstellen eines neuen kostenlosen](https://azure.microsoft.com/free/) Kontos.

Visual Studio bietet integrierte Unterstützung für die Bereitstellung von Apps für verschiedene Anbieter, einschließlich Azure.

<img width="530px" alt="Visual Studio" src="~/assets/images/get-started/publishtoazure1.png"/>

[!include [Use App Studio to configure the app package](~/includes/get-started/get-started-use-app-studio.md)]

## <a name="update-the-credentials-for-your-hosted-app"></a>Aktualisieren der Anmeldeinformationen für Ihre gehostete App

Die Beispiel-App erfordert, dass die folgenden Umgebungsvariablen auf die Werte festgelegt werden, die Sie zuvor notieren.

Öffnen Sie die appsettings.jsOn-Datei. Aktualisieren Sie *den Wert "MicrosoftAppId"* mit Ihrer Bot-ID, die Sie zuvor gespeichert haben. Aktualisieren Sie *MicrosoftAppPassword* mit dem Bot-Kennwort, das Sie zuvor gespeichert haben.

<img width="560px" alt="Setting the keys" src="~/assets/images/get-started/get-started-net-azure-add-keys.png"/>

Nachdem diese Änderungen vorgenommen wurden, erstellen Sie die App neu. Wenn Sie ngrok verwenden, führen Sie die App lokal aus, und wenn Sie die App in Azure hosten, stellen Sie sie erneut bereit.

## <a name="configure-the-app-tab"></a>Konfigurieren der Registerkarte "App"

Nachdem Sie die App in einem Team installiert haben, müssen Sie sie so konfigurieren, dass Inhalte angezeigt werden. Wechseln Sie zu einem Kanal im Team, in dem Sie die Beispiel-App installiert haben, und klicken Sie auf die Schaltfläche **"+",** um eine neue Registerkarte hinzuzufügen. Sie können dann aus der `Hello World` Registerkartenliste **"Hinzufügen"** auswählen. Anschließend wird ein Konfigurationsdialogfeld angezeigt. In diesem Dialogfeld können Sie auswählen, welche Registerkarte in diesem Kanal angezeigt werden soll. Nachdem Sie die Registerkarte ausgewählt und auf diese geklickt haben, wird die Registerkarte mit der ausgewählten `Save` `Hello World` Registerkarte geladen.

<img width="530px" alt="Screenshot of configure" src="~/assets/images/samples-hello-world-tab-configure.png" />

### <a name="test-your-bot-in-teams"></a>Testen Ihres Bots in Teams

Sie können jetzt mit dem Bot in Teams interagieren. Wählen Sie einen Kanal im Team aus, in dem Sie Ihre App registriert haben, und geben Sie `@your-bot-name` ein. Dies wird als Erwähnung **\@ bezeichnet.** Welche Nachricht Sie an den Bot senden, wird als Antwort an Sie zurückgeschickt.

<img width="450px" alt="Bot responses" src="~/assets/images/samples-hello-world-bot.png" />

### <a name="test-your-messaging-extension"></a>Testen der Messagingerweiterung

Zum Testen Ihrer Messagingerweiterung können Sie auf die drei Punkte unter dem Eingabefeld in der Unterhaltungsansicht klicken. Ein Menü wird mit der **"Hello World"-App** angezeigt. Wenn Sie darauf klicken, wird eine Reihe zufälliger Texte angezeigt. Sie können eine davon auswählen und in Ihre Unterhaltung einfügen.

<img width="530px" alt="Messaging extension menu" src="~/assets/images/samples-hello-world-messaging-extensions-menu.png" />

<img width="530px" alt="Messaging extension result" src="~/assets/images/samples-hello-world-messaging-extensions-result.png" />

Wählen Sie einen der zufälligen Texte aus, und unten wird eine Karte formatiert und bereit zum Senden mit Ihrer eigenen Nachricht angezeigt.

<img width="530px" alt="Messaging extension send" src="~/assets/images/samples-hello-world-messaging-extensions-send.png" />
