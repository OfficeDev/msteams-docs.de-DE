---
title: Erste Schritte mit C#/.net
description: Erste Schritte beim Erstellen von tollen apps in Microsoft Teams mit C#-/.net
keywords: Erste Schritte mit .net c# CSharp
ms.date: 11/09/2018
ms.openlocfilehash: de133894042baaba897a9f046d613cd5dbb94eee
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674273"
---
# <a name="get-started-on-the-microsoft-teams-platform-with-cnet-and-app-studio"></a>Erste Schritte mit der Microsoft Teams-Plattform mit C#/.net und App Studio

Die [Microsoft Teams](/microsoftteams/) -Entwicklerplattform erleichtert Ihnen das Erweitern von Teams und die nahtlose Integration ihrer eigenen Anwendungen und Dienste in den Arbeitsbereich "Teams". Diese Apps können dann an Ihr Unternehmen oder für Teams auf der ganzen Welt verteilt werden.

Um Microsoft Teams zu erweitern, müssen Sie eine Microsoft Teams-app erstellen. Eine Microsoft Teams-APP ist eine Webanwendung, die Sie hosten. Diese APP kann dann in Microsoft Teams in den Arbeitsbereich des Benutzers integriert werden.

In diesem Lernprogramm erfahren Sie, wie Sie mit dem Erstellen einer Microsoft Teams-App mithilfe von C# in .net beginnen können. Sie können die APP testen, indem Sie Sie in ein Team laden, für das Sie Berechtigungen haben, oder in einen Testmandanten, der mit dem Office-Entwicklerprogramm erstellt wurde.

[!include [prepare your environment](~/includes/prepare-environment.md)]

<a name="GetPrerequisites"></a>

## <a name="get-prerequisites"></a>Abrufen von Voraussetzungen

Um dieses Lernprogramm abzuschließen, müssen Sie die folgenden Tools abrufen:

- [Installieren von git](https://git-scm.com/downloads)
- [Installieren Sie Visual Studio 2017](https://www.visualstudio.com/downloads/). Sie können die ﻿kostenlose Community Edition installieren.

Wenn Sie während der Installation eine Option `git` zum Hinzufügen des Pfads sehen, wählen Sie aus. Das ist praktisch.

Überprüfen `git` Sie Ihre Installation, indem Sie Folgendes in einem Terminalfenster ausführen:
> [!NOTE]
> Verwenden Sie das Terminal-Fenster, mit dem Sie sich am besten auf Ihrer Plattform vertraut machen. In diesen Beispielen wird bash verwendet, wird jedoch auf den meisten Plattformen ausgeführt.

```bash
$ git --version
git version 2.17.1.windows.2

```

Stellen Sie sicher, dass Sie Visual Studio 2017 starten und alle Updates installieren, falls dies angezeigt wird.

Sie können weiterhin dieses Terminalfenster verwenden, um die Befehle auszuführen, die in diesem Lernprogramm folgen.

<a name="DownloadSample"></a>

## <a name="download-the-sample"></a>Herunterladen des Beispiels

Wir haben ein einfaches [Hello, World](https://github.com/OfficeDev/msteams-samples-hello-world-csharp) bereitgestellt! Beispiel in C#, um den Einstieg zu erhalten. Führen Sie in einem Terminalfenster den folgenden Befehl aus, um das Beispiel-Repository auf Ihren lokalen Computer zu klonen:

```bash
git clone https://github.com/OfficeDev/msteams-samples-hello-world-csharp.git
```

> [!TIP]
> Sie können dieses [Repo](https://github.com/OfficeDev/msteams-samples-hello-world-csharp) [abzweigen](https://help.github.com/articles/fork-a-repo/) , wenn Sie die Änderungen an GitHub zur späteren Referenz ändern und einchecken möchten.

<a name="BuildRun"></a>

## <a name="build-and-run-the-sample"></a>Erstellen und Ausführen des Beispiels

Nachdem das Repository geklont wurde, verwenden Sie Visual Studio, um die Lösungsdatei `Microsoft.Teams.Samples.HelloWorld.sln` aus dem Stammverzeichnis des Beispiels zu öffnen und `Build Solution` im `Build` Menü zu klicken. Sie können das Beispiel durch Drücken `F5` oder auswählen `Start Debugging` im `Debug` Menü ausführen.

Wenn die APP gestartet wird, wird ein Browserfenster geöffnet, in dem der Stamm der APP gestartet ist. Sie können zu den folgenden URLs navigieren, um sicherzustellen, dass alle App-URLs geladen werden:

- [http://localhost:3333](http://localhost:3333)
- [http://localhost:3333/hello](http://localhost:3333/hello)
- [http://localhost:3333/first](http://localhost:3333/first)
- [http://localhost:3333/second](http://localhost:3333/second)

<a name="HostSample"></a>

> [!Note]
> Wenn Sie eine Fehlermeldung wie `Could not find a part of the path … bin\roslyn\csc.exe`erhalten, versuchen Sie, das Paket mit `Update-Package Microsoft.CodeDom.Providers.DotNetCompilerPlatform -r`dem Befehl zu aktualisieren. Weitere Informationen finden Sie [in dieser Frage auf StackOverflow](https://stackoverflow.com/questions/32780315) .

## <a name="host-the-sample-app"></a>Hosten der Beispiel-App

Beachten Sie, dass apps in Microsoft Teams Webanwendungen sind, die eine oder mehrere Funktionen verfügbar machen. Damit die Microsoft Teams-Plattform Ihre APP lädt, muss Ihre APP über das Internet erreichbar sein. Damit Ihre APP über das Internet erreichbar ist, müssen Sie Ihre APP hosten. Sie können es entweder in Microsoft Azure kostenlos hosten oder einen Tunnel für den lokalen Prozess auf dem Entwicklungscomputer mit `ngrok`erstellen. Wenn Sie das Hosten Ihrer APP abgeschlossen haben, notieren Sie sich die Stamm-URL. Es sieht etwa wie folgt aus `https://yourteamsapp.ngrok.io` : `https://yourteamsapp.azurewebsites.net`oder.

### <a name="tunnel-using-ngrok"></a>Tunnel mit ngrok

Für schnelle Tests können Sie die APP auf Ihrem lokalen Computer ausführen und einen Tunnel über einen Webendpunkt erstellen. [ngrok](https://ngrok.com) ist ein kostenloses Tool, mit dem Sie genau dies tun können. Mit ngrok können Sie eine Webadresse wie `https://d0ac14a5.ngrok.io` (diese URL ist nur ein Beispiel) erhalten. Sie können ngrok für Ihre Umgebung [herunterladen und installieren](https://ngrok.com/download) . Stellen Sie sicher, dass Sie Sie an einen Speicherort `PATH`in Ihrem hinzufügen.

Nachdem Sie es installiert haben, können Sie ein neues Terminalfenster öffnen und den folgenden Befehl ausführen, um einen Tunnel zu erstellen. Im Beispiel wird Port 3333 verwendet, stellen Sie daher sicher, dass Sie es hier angeben.

```bash
ngrok http 3333 -host-header=localhost:3333
```

Ngrok wird Anfragen aus dem Internet abhören und diese an Ihre APP weiterleiten, die auf Port 3333 läuft. Sie können überprüfen, ob Sie Ihren Browser öffnen `https://d0ac14a5.ngrok.io/hello` und die Hello-Seite Ihrer App laden. Achten Sie darauf, dass Sie die von ngrok in ihrer Konsolensitzung angezeigte Weiterleitungsadresse anstelle dieser URL verwenden.

> [!NOTE]
> Wenn Sie einen anderen Port im Schritt " [Build" und "ausführen](#build-and-run-the-sample) " verwendet haben, stellen Sie sicher, dass Sie die gleiche Port `ngrok` Nummer zum Einrichten des Tunnels verwenden.
> [!TIP]
> Es empfiehlt sich, `ngrok` in einem anderen Terminalfenster ausgeführt zu werden, damit es ausgeführt wird, ohne dass die APP beeinträchtigt wird, die Sie später möglicherweise beenden, neu erstellen und erneut ausführen müssen. Die `ngrok` Sitzung gibt nützliche Debuginformationen in diesem Fenster zurück.

Die APP ist nur während der aktuellen Sitzung auf dem Entwicklungscomputer verfügbar. Wenn der Computer heruntergefahren wird oder in den Standbymodus wechselt, steht der Dienst nicht mehr zur Verfügung. Denken Sie daran, wenn Sie die APP für Tests von anderen Benutzern freigeben. Wenn Sie den Dienst neu starten müssen, wird eine neue Adresse zurückgegeben, und Sie müssen jeden Ort aktualisieren, an dem diese Adresse verwendet wird. Die kostenpflichtige Version von Ngrok hat diese Einschränkung nicht.

### <a name="host-in-azure"></a>Host in Azure

Microsoft Azure können Sie Ihre .NET-Anwendung auf einer freien Ebene mit der freigegebenen Infrastruktur hosten. Dies reicht aus, um dieses `Hello World` Beispiel ausführen zu können. Weitere Informationen finden Sie unter [Erstellen eines neuen kostenlosen Kontos](https://azure.microsoft.com/free/) .

Visual Studio bietet integrierte Unterstützung für die APP-Bereitstellung für unterschiedliche Anbieter, einschließlich Azure.

<img width="530px" src="~/assets/images/get-started/publishtoazure1.png" title="Visual Studio"/>

[!include[Use App Studio to configure the app package](~/includes/get-started/get-started-use-app-studio.md)]

## <a name="update-the-credentials-for-your-hosted-app"></a>Aktualisieren der Anmeldeinformationen für die gehostete App

Für die Beispiel-App müssen die folgenden Umgebungsvariablen auf die Werte festgelegt werden, auf die Sie zuvor hingewiesen haben.

Öffnen Sie die Datei "Internet. config", und suchen Sie nach dem Abschnitt *appSettings* . Aktualisieren Sie den *MicrosoftAppId* -Wert mit ihrer bot-ID, die Sie zuvor gespeichert haben. Aktualisieren Sie das *MicrosoftAppPassword* mit dem zuvor gespeicherten bot-Kennwort.

<img width="560px" src="~/assets/images/get-started/get-started-net-azure-add-keys.png" title="Festlegen der Schlüssel"/>

Nachdem diese Änderungen vorgenommen wurden, erstellen Sie die APP neu. Wenn Sie ngrok verwenden, führen Sie die APP lokal aus, und wenn Sie in Azure hosten, müssen Sie die APP erneut bereitstellen.

## <a name="configure-the-app-tab"></a>Konfigurieren der Registerkarte "App"

Nachdem Sie die app in einem Team installiert haben, müssen Sie Sie so konfigurieren, dass Inhalte angezeigt werden. Wechseln Sie zu einem Kanal im Team, in dem Sie die Beispiel-App installiert haben, und klicken Sie auf die Schaltfläche **"+"** , um eine neue Registerkarte hinzuzufügen. Sie können dann in `Hello World` der Liste **Registerkarte hinzufügen** auswählen. Anschließend wird ein Konfigurationsdialogfeld angezeigt. In diesem Dialogfeld können Sie auswählen, welche Registerkarte in diesem Kanal angezeigt werden soll. Nachdem Sie die Registerkarte ausgewählt haben und `Save` klicken Sie auf dann können `Hello World` Sie die Registerkarte mit der ausgewählten Registerkarte geladen sehen.

<img width="530px" src="~/assets/images/samples-hello-world-tab-configure.png" title="Screenshot von configure" />

### <a name="test-your-bot-in-teams"></a>Testen Sie Ihren bot in Microsoft Teams

Sie können nun mit dem bot in Microsoft Teams interagieren. Wählen Sie einen Kanal in dem Team aus, in dem Sie Ihre APP `@your-bot-name`registriert haben, und geben Sie ein. Dies wird als ** \@Erwähnung**bezeichnet. Jede Nachricht, die Sie an den bot senden, wird als Antwort an Sie zurückgesendet.

<img width="450px" title="Bot-Antworten" src="~/assets/images/samples-hello-world-bot.png" />

### <a name="test-your-messaging-extension"></a>Testen der Messaging Erweiterung

Um Ihre Messaging Erweiterung zu testen, können Sie auf die drei Punkte unter dem Eingabefeld in ihrer Unterhaltungsansicht klicken. Ein Menü wird mit der **"Hello World"-** app in diesem Popup angezeigt. Wenn Sie darauf klicken, sehen Sie eine Reihe von zufälligen Texten, die angezeigt werden. Sie können eine von Ihnen auswählen, und Sie wird in Ihre Unterhaltung eingefügt.

<img width="530px" title="Menü "Messaging Erweiterung"" src="~/assets/images/samples-hello-world-messaging-extensions-menu.png" />

<img width="530px" title="Ergebnis der Messaging-Erweiterung" src="~/assets/images/samples-hello-world-messaging-extensions-result.png" />

Wählen Sie einen der zufälligen Texte aus, und Sie sehen eine Karte, die formatiert und mit ihrer eigenen Nachricht am unteren Rand gesendet werden kann.

<img width="530px" title="Messaging-Durchwahl senden" src="~/assets/images/samples-hello-world-messaging-extensions-send.png" />
