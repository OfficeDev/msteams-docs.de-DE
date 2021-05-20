---
title: 'Tutorial - Erstellen Sie Ihre erste App mit C #'
description: Erfahren Sie, wie Sie mit dem Erstellen Microsoft Teams-Apps mit C- oder .NET beginnen.
keywords: Erste Schritte .net c' csharp
ms.custom: scenarios:getting-started; languages:ASP.NET,C#
localization_priority: Normal
ms.topic: tutorial
ms.date: 11/09/2018
ms.openlocfilehash: eaa37f1ccb7944ee18bb62ae47882dc4a715b165
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566887"
---
# <a name="create-your-first-teams-app-using-c"></a>Erstellen Sie Ihre erste Teams-App mit C #

In diesem Tutorial können Sie eine Microsoft Teams-App mit C-Code erstellen. Dazu müssen Sie Folgendes tun:

* Vorbereiten der Umgebung
* Voraussetzungen abrufen
* Laden Sie das Beispiel herunter
* Erstellen und Ausführen des Beispiels
* Hosten der Beispiel-App
* Aktualisieren der Anmeldeinformationen für Ihre gehostete App
* Konfigurieren der App-Registerkarte

[!include [prepare your environment](~/includes/prepare-environment.md)]

<a name="GetPrerequisites"></a>

## <a name="get-prerequisites"></a>Voraussetzungen abrufen

Um dieses Tutorial abzuschließen, müssen Sie die folgenden Tools installieren:

- [Installieren von Git](https://git-scm.com/downloads)
- [Installieren von Visual Studio](https://www.visualstudio.com/downloads/)

Sie können die kostenlose Community-Edition von Visual Studio installieren. Wenn es während der Installation eine Option zum Hinzufügen `git` zum Pfad gibt, wählen Sie ihn aus. Führen Sie in einem Terminalfenster den folgenden Befehl aus, um Ihre Installation zu `git` überprüfen:

```bash
$ git --version
git version 2.17.1.windows.2

```

> [!NOTE]
> Verwenden Sie ein geeignetes Terminalfenster auf Ihrer Plattform. Diese Beispiele verwenden Git Bash, können aber auf den meisten Plattformen ausgeführt werden.

Öffnen Sie die neueste Version von Visual Studio und installieren Sie alle Updates.

Sie können dasselbe Terminalfenster verwenden, um die Befehle in diesem Tutorial auszuführen.

<a name="DownloadSample"></a>

## <a name="download-the-sample"></a>Laden Sie das Beispiel herunter

Sie können mit einem einfachen [Hallo, Welt beginnen!](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-hello-world/csharp) Beispiel in C.. Führen Sie in einem Terminalfenster den folgenden Befehl aus, um das Beispiel-Repository auf Ihren Computer zu klonen:

```bash
git clone https://github.com/OfficeDev/Microsoft-Teams-Samples.git
```

> [!TIP]
> Sie können dieses [Repository](https://github.com/OfficeDev/Microsoft-Teams-Samples) [verkleben,](https://help.github.com/articles/fork-a-repo/) um Ihre Änderungen zu ändern und in GitHub zu speichern.

<a name="BuildRun"></a>

## <a name="build-and-run-the-sample"></a>Erstellen und Ausführen des Beispiels

Nachdem das Repository geklont wurde, verwenden Sie Visual Studio, um die Lösungsdatei **Microsoft.Teams zu öffnen. Samples.HelloWorld.sln** aus dem **Microsoft-Teams-Samples/samples/app-hello-world/csharp-Verzeichnis** des Beispiels. Wählen Sie dann im Menü **Erstellen** die Option **Lösung erstellen** aus. Um das Beispiel auszuführen, drücken Sie **F5** oder wählen Sie **Debuggen** starten im **Debugmenü** aus.

Wenn die App gestartet wird, wird ein Browserfenster geöffnet, in dem der Stamm der App gestartet wird. Sie können zu den folgenden URLs wechseln, um zu überprüfen, ob alle App-URLs geladen werden:

- `https://localhost:44327/`
- `https://localhost:44327/hello`
- `https://localhost:44327/first`
- `https://localhost:44327/second`

<a name="HostSample"></a>

> [!Note]
> Wenn sie eine Fehlermeldung `Could not find a part of the path … bin\roslyn\csc.exe` erhalten, aktualisieren Sie das Paket mit dem Befehl `Update-Package Microsoft.CodeDom.Providers.DotNetCompilerPlatform -r` . Weitere Informationen finden Sie unter [diese Frage unter Stack Overflow](https://stackoverflow.com/questions/32780315).

## <a name="host-the-sample-app"></a>Hosten der Beispiel-App

Apps in Microsoft Teams sind Webanwendungen, die eine oder mehrere Funktionen bereitstellen. Damit die Teams Plattform Ihre App laden kann, muss Ihre App im Internet verfügbar sein. Dazu müssen Sie Ihre App hosten. Sie können es entweder kostenlos in Microsoft Azure hosten oder einen Tunnel zum lokalen Prozess auf Ihrem Computer erstellen, indem Sie `ngrok` verwenden. Nachdem Sie Ihre App hosten, notieren Sie sich deren Stamm-URL, z. `https://yourteamsapp.ngrok.io` B. oder `https://yourteamsapp.azurewebsites.net` .

### <a name="tunnel-using-ngrok"></a>Tunnel mit ngrok

Zum schnellen Testen können Sie die App auf Ihrem Computer ausführen und einen Tunnel zu diesem Überstand über einen Webendpunkt erstellen. [`ngrok`](https://ngrok.com) ist ein kostenloses Tool, mit dem Sie eine Webadresse erhalten können, z. `https://d0ac14a5.ngrok.io` B. . Sie können ngrok [herunterladen und installieren](https://ngrok.com/download) und es an einem Speicherort in Ihrem `PATH` hinzufügen.

Öffnen Sie nach der Installation `ngrok` ein neues Terminalfenster, und führen Sie den folgenden Befehl aus, um einen Tunnel zu erstellen:

```bash
ngrok http 44327 -host-header=localhost:44327
```

`Ngrok` überwacht Anfragen aus dem Internet und leitet sie an Ihre App weiter, die unter Port 44327 ausgeführt wird. Um dies zu überprüfen, öffnen Sie Ihren Browser, und gehen Sie `https://d0ac14a5.ngrok.io/hello` zu , um die Hallo-Seite Ihrer App zu laden. Verwenden Sie anstelle dieser URL die Weiterleitungsadresse, die in der Konsolensitzung angezeigt `ngrok` wird.

> [!NOTE]
> Wenn Sie im [Build- und Ausführungsschritt](#build-and-run-the-sample) einen anderen Port verwendet haben, stellen Sie sicher, dass Sie dieselbe Portnummer verwenden, um den `ngrok` Tunnel einzurichten.

> [!TIP]
> Es ist eine gute Idee, in einem anderen Terminalfenster zu `ngrok` laufen. Dies geschieht, um zu verhindern, `ngrok` dass die App ausgeführt wird, ohne die App zu stören. Sie müssen die App anhalten, neu erstellen und erneut ausführen. Die `ngrok` Sitzung enthält nützliche Debuginformationen in diesem Fenster.

Die App ist nur während der aktuellen Sitzung auf Ihrem Computer verfügbar. Wenn die Maschine heruntergefahren wird oder in den Ruhezustand geht, ist der Dienst nicht mehr verfügbar. Denken Sie daran, wenn Sie die App zum Testen für andere Benutzer freigeben. Wenn Sie den Dienst neu starten müssen, gibt die App eine neue Adresse zurück, und Sie müssen jeden Speicherort aktualisieren, der diese Adresse verwendet. Die kostenpflichtige Version von `ngrok` hat diese Einschränkung nicht.

### <a name="host-in-azure"></a>Host in Azure

Microsoft Azure Hosthosten Ihrer .NET-Anwendung auf einem freien Kontingent mithilfe einer freigegebenen Infrastruktur. Dies reicht aus, um das `Hello World` Beispiel auszuführen. Weitere Informationen finden Sie unter [Erstellen eines neuen kostenlosen Azure-Kontos](https://azure.microsoft.com/free/).

Visual Studio bietet integrierte Unterstützung für die App-Bereitstellung für verschiedene Anbieter, einschließlich Azure:

<img width="530px" alt="Visual Studio" src="~/assets/images/get-started/publishtoazure1.png"/>

[!include [Use App Studio to configure the app package](~/includes/get-started/get-started-use-app-studio.md)]

## <a name="update-the-credentials-for-your-hosted-app"></a>Aktualisieren der Anmeldeinformationen für Ihre gehostete App

Die Beispiel-App erfordert, dass die Umgebungsvariablen auf die Werte festgelegt werden, die Sie in der Textdatei gespeichert haben.

die Datei `appsettings.json` öffnen. Aktualisieren Sie den **MicrosoftAppId-Wert** mit Ihrer Bot-ID, die Sie in der Textdatei gespeichert haben. Aktualisieren Sie das **MicrosoftAppPassword** mit dem von Ihnen gespeicherten Bot-Passwort.

<img width="560px" alt="Setting the keys" src="~/assets/images/get-started/get-started-net-azure-add-keys.png"/>

Nachdem diese Änderungen vorgenommen wurden, erstellen Sie die App neu. Wenn Sie ngrok verwenden, führen Sie die App lokal aus, und stellen Sie die App erneut bereit, und wenn Sie in Azure hosten, stellen Sie die App erneut bereit.

## <a name="configure-the-app-tab"></a>Konfigurieren der App-Registerkarte

Nachdem Sie die App in einem Team installiert haben, müssen Sie sie so konfigurieren, dass Inhalte angezeigt werden. Wechseln Sie zu einem Kanal im Team, in dem Sie die Beispiel-App installiert haben, und wählen Sie die Schaltfläche **"+",** um eine neue Registerkarte hinzuzufügen. Wählen Sie **Hello World** aus der **RegisterkarteNliste Hinzufügen** aus. Es wird ein Konfigurationsdialogfeld angezeigt, in dem Sie die Registerkarte auswählen können, die in diesem Kanal angezeigt werden soll. Nachdem Sie die Registerkarte ausgewählt und die Option **Speichern** auswählen, wird die `Hello World` Registerkarte mit der Registerkarte geladen.

<img width="530px" alt="Screenshot of configure" src="~/assets/images/samples-hello-world-tab-configure.png" />

### <a name="test-your-bot-in-teams"></a>Testen Sie Ihren Bot in Teams

Jetzt können Sie den Bot in Teams testen. Wählen Sie einen Kanal im Team aus, in dem Sie Ihre App registriert haben, und geben Sie `@your-bot-name` ein. Dies wird als **\@ Erwähnung** bezeichnet. Der Bot antwortet auf jede Nachricht, die Sie senden.

<img width="450px" alt="Bot responses" src="~/assets/images/samples-hello-world-bot.png" />

### <a name="test-your-messaging-extension"></a>Testen Sie Ihre Messaging-Erweiterung

Um Ihre Messaging-Erweiterung zu testen, können Sie **...** unter dem Eingabefeld in Ihrer Unterhaltungsansicht auswählen. Ein Menü mit der **App "Hello World"** wird angezeigt. Wenn Sie es auswählen, wird eine Reihe zufälliger Texte angezeigt. Sie können einen der zufälligen Texte auswählen, der in Ihre Unterhaltung eingefügt wird.

<img width="530px" alt="Messaging extension menu" src="~/assets/images/samples-hello-world-messaging-extensions-menu.png" />

<img width="530px" alt="Messaging extension result" src="~/assets/images/samples-hello-world-messaging-extensions-result.png" />

Wählen Sie einen der zufälligen Texte aus. Eine Karte, die mit Ihrer eigenen Nachricht formatiert und zum Senden bereit ist, wird angezeigt.

<img width="530px" alt="Messaging extension send" src="~/assets/images/samples-hello-world-messaging-extensions-send.png" />
