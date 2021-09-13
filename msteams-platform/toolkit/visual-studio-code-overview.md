---
title: Erstellen von Apps mit dem Microsoft Teams Toolkit und Visual Studio Code
description: Erste Schritte beim Erstellen von großartigen benutzerdefinierten Apps direkt in Visual Studio Code mit dem Microsoft Teams Toolkit
keywords: Teams Visual Studio Code Toolkit
ms.localizationpriority: medium
ms.topic: overview
ms.author: lajanuar
ms.openlocfilehash: 4425ea5ac6daa400d33497e031cf37639cd2722a
ms.sourcegitcommit: fc9f906ea1316028d85b41959980b81f2c23ef2f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2021
ms.locfileid: "59156088"
---
# <a name="build-apps-with-the-teams-toolkit-and-visual-studio-code"></a>Erstellen von Apps mit dem Teams Toolkit und Visual Studio Code

Das Teams Toolkit für Visual Studio Code hilft Entwicklern beim Erstellen und Bereitstellen Teams Apps mit integrierter Identität, Zugriff auf Cloudspeicher, Daten von Microsoft Graph und anderen Diensten in Azure und M365 mit einem Nullkonfigurationsansatz für die Entwicklerumgebung.  

Sie können das Toolkit auch mit Visual Studio oder als CLI `teamsfx` (genannt) verwenden.

## <a name="install-the-teams-toolkit-for-visual-studio-code"></a>Installieren des Teams Toolkits für Visual Studio Code

1. Öffnen Sie Visual Studio Code.
1. Wählen Sie die Erweiterungsansicht (**STRG+UMSCHALT+X**  /  **⌘⇧-X** oder **Ansicht > Erweiterungen) aus.**
1. Geben Sie in das Suchfeld _Teams Toolkit_ ein.
1. Klicken Sie auf die grüne Installationsschaltfläche neben dem Teams Toolkit.

Sie finden auch das Teams Toolkit auf dem [Visual Studio Code Marketplace.](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension)

Die folgenden Tools werden von der Visual Studio Code-Erweiterung installiert, wenn sie benötigt werden. Wenn sie bereits installiert ist, wird stattdessen die installierte Version verwendet. Wenn Sie Linux (einschließlich WSL) verwenden, müssen Sie diese Tools vor der Verwendung installieren:

- [Azure Functions Core Tools](/azure/azure-functions/functions-run-local)

    Azure Functions Core Tools wird verwendet, um alle Back-End-Komponenten während einer lokalen Debugausführung lokal auszuführen, einschließlich der Authentifizierungshilfsprogramme, die beim Ausführen Ihrer Dienste in Azure erforderlich sind. Sie wird mithilfe des npm im Projektverzeichnis `devDependencies` installiert.

- [.NET SDK](/dotnet/core/install/)

    Das .NET SDK wird verwendet, um angepasste Bindungen für lokales Debuggen und Azure Functions-App-Bereitstellungen zu installieren. Wenn Sie das .NET 3.1- oder höher-SDK nicht global installiert haben, wird die portierbare Version installiert.

- [ngrok](https://ngrok.com/download)

    Einige Teams App-Features (Unterhaltungs-Bots, Messaging-Erweiterungen und eingehende Webhooks) erfordern eingehende Verbindungen.  Sie müssen Ihr Entwicklungssystem für Teams über einen Tunnel verfügbar machen. Für Apps, die nur Registerkarten enthalten, ist kein Tunnel erforderlich.  Dieses Paket wird im Projektverzeichnis installiert (mit `devDependencies` npm).

## <a name="use-the-teams-toolkit-for-visual-studio-code"></a>Verwenden des Teams-Toolkits für Visual Studio Code

- [Einrichten eines neuen Projekts](#set-up-a-new-teams-project)
- [Konfigurieren Sie die App](#configure-your-app)
- [Lokales Ausführen Ihrer App](#install-and-run-your-app-locally)
- [Veröffentlichen eigener Apps](#publish-your-app-to-teams)

## <a name="set-up-a-new-teams-project"></a>Einrichten eines neuen Teams Projekts

Das Teams Toolkit kann React Apps erstellen, die in Azure gehostet werden, oder SPFx Webparts, die in Ihrer M365 SharePoint-Umgebung gehostet werden. So erstellen Sie eine neue React-App, die in Azure gehostet werden soll:

1. Öffnen Sie Visual Studio Code.
1. Öffnen Sie das Microsoft Teams-Toolkit, indem Sie auf das Microsoft Teams-Symbol in der Randleiste klicken:

    :::image type="content" source="../assets/images/teams-toolkit-v2/sidebar-icon.png" alt-text="Das Microsoft Teams-Symbol in der Visual Studio Code-Randleiste.":::

1. Klicken Sie auf **Neues Projekt erstellen**.

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project.png" alt-text="Ort des Links „Neues Projekt erstellen“ in der Randleiste des Microsoft Teams-Toolkits.":::

1. Wählen Sie **Neue Microsoft Teams-App erstellen** aus.

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-new-project-intro.png" alt-text="Starten des Assistenten für „Neues Projekt erstellen“":::

1. Im Schritt **"Funktionen auswählen"** ist die **Registerkartenfunktion** bereits ausgewählt. Sie können optional auch **Bot-** und **Messaging-Erweiterung** auswählen.  Drücken Sie **OK**.

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project-capabilities.png" alt-text="Screenshot, der zeigt, wie Ihrer neuen App Funktionen hinzufügt werden können.":::

1. Wählen Sie im Schritt **Frontend-Hostingtyp** die Option **Azure** aus.

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project-hosting.png" alt-text="Screenshot, der zeigt, wie das Hosting für Ihre neue App ausgewählt wird.":::

1. Wählen Sie optional im Schritt **"Cloudressourcen"** Cloudressourcen aus, die Ihre Anwendung verwendet. Sie können den CRUD-Zugriff (Erstellen, Lesen, Aktualisieren und Löschen) auf eine SQL Tabelle oder eine API auswählen:

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project-cloud-resources.png" alt-text="Screenshot, der zeigt, wie Cloudressourcen für Ihre neue App hinzugefügt werden.":::

1. Im Schritt **"Programmiersprache"** können Sie **JavaScript** oder **TypeScript** auswählen:

    :::image type="content" source="../assets/images/teams-toolkit-v2/create-project-programming-languages.png" alt-text="Screenshot, der zeigt, wie die Programmiersprache ausgewählt wird.":::

1. Wählen Sie einen Arbeitsbereichsordner aus. Ein Ordner wird in Ihrem Arbeitsbereichsordner für das Projekt erstellt, das Sie erstellen.

1. Geben Sie einen passenden Namen für Ihre App ein, wie z. B. `helloworld`. Der Name der App darf nur aus alphanumerischen Zeichen bestehen.  Drücken Sie die **EINGABETASTE**, um fortzufahren.

Ihre Teams-App wird innerhalb weniger Sekunden erstellt. Die Gerüst-App enthält Code zum Behandeln des einmaligen Anmeldens mit Azure Active Directory und zugriff auf die Microsoft-Graph.  Wenn Sie Azure-Ressourcen ausgewählt haben, ist auch der Code für diese Ressourcen verfügbar.

Eine exemplarische Vorgehensweise zum SPFx Erstellungs- und Veröffentlichungsprozess finden Sie im [SPFx Lernprogramm.](../get-started/first-app-spfx.md)

## <a name="configure-your-app"></a>Konfigurieren Sie die App

Im Kern umfasst die Teams App drei Komponenten:

  1. Der Microsoft Teams Client (Web, Desktop oder Mobil), auf dem Benutzer mit Ihrer App interagieren.
  1. Ein Server, der auf Anforderungen für Inhalte reagiert, die in Teams angezeigt werden. Beispiel: HTML-Registerkarteninhalt oder eine adaptive Bot-Karte.
  1. Ein Teams-App-Paket besteht aus drei Dateien:

      > [!div class="checklist"]
      >
      > - Die manifest.jsaktiviert.
      > - Ein [Farbsymbol](../resources/schema/manifest-schema.md#icons) für Ihre App, das im öffentlichen App- oder Organisations-App-Katalog angezeigt werden soll.
      > - Ein [Gliederungssymbol](../resources/schema/manifest-schema.md#icons) für die Anzeige auf der Teams Aktivitätsleiste.

Das Manifest und die Symbole werden im `.fx` Ordner Ihres Projekts gespeichert, bevor sie in Teams hochgeladen werden. Wenn eine App installiert ist, analysiert der Teams-Client die Manifestdatei, um die erforderlichen Informationen wie den Namen Ihrer App und die URL zu ermitteln, unter der sich die Dienste befinden.

1. Navigieren Sie zum Konfigurieren Ihrer App zur Registerkarte **Teams Toolkit** in Visual Studio Code.
1. Wählen Sie im **Abschnitt Project** den **Manifest-Editor** aus.

Durch das Bearbeiten der Felder auf der Seite "App-Details" wird der Inhalt der manifest.jsin der Datei aktualisiert, die letztendlich als Teil des App-Pakets ausgeliefert wird.

## <a name="install-and-run-your-app-locally"></a>Lokales Installieren und Ausführen der App

So erstellen Sie Ihre App und führen sie lokal aus:

1. Drücken Sie in Visual Studio Code **F5**, um die Anwendung im Debugmodus auszuführen.

   > Wenn Sie die App zum ersten Mal ausführen, werden alle Abhängigkeiten heruntergeladen und die App wird erstellt.  Wenn die Erstellung abgeschlossen ist, wird automatisch ein Browserfenster geöffnet.  Dies kann 3 bis 5 Minuten dauern.

   Das Toolkit fordert Sie auf, bei Bedarf ein lokales Zertifikat zu installieren. Mit diesem Zertifikat kann Microsoft Teams Ihre Anwendung von `https://localhost` laden. Wählen Sie "Ja" aus, wenn das folgende Dialogfenster angezeigt wird:

   :::image type="content" source="../assets/images/teams-toolkit-v2/ssl-prompt.png" alt-text="Screenshot mit Dialogfenster zum Installieren eines SSL-Zertifikats, damit Microsoft Teams Ihre Anwendung von localhost laden kann.":::

1. Ihr Webbrowser wird gestartet, um die Anwendung auszuführen. Wenn Sie zum Öffnen von Microsoft Teams aufgefordert werden, wählen Sie „Abbrechen“ aus, um im Browser zu verbleiben. Möglicherweise werden Sie auch aufgefordert, zu anderen Zeiten zur Teams-Anwendung zu wechseln. Wählen Sie in diesem Fall die Web-App aus.

   :::image type="content" source="../assets/images/teams-toolkit-v2/launch-web-browser-and-pick-webapp.png" alt-text="Screenshot, der zeigt, wie die Web-Version von Microsoft Teams beim Start ausgewählt wird.":::

1. Möglicherweise werden Sie aufgefordert, sich anzumelden. Melden Sie sich in diesem Fall mit Ihrem M365-Konto an.
1. Wenn Sie aufgefordert werden, die App in Microsoft Teams zu installieren, drücken Sie **Hinzufügen**.

Sowohl das Back-End als auch der Frontend sind in den Visual Studio Code Debugger eingebunden.  Auf diese Weise können Sie haltepunkte an einer beliebigen Stelle im Code festlegen und den Status überprüfen.  Sie können auch alle Front-End-Debuggingtools (z. B. die React Developer Tools) im Browser verwenden.  Weitere Informationen zum Debuggen in Visual Studio Code, lesen Sie [die Dokumentation.](https://code.visualstudio.com/Docs/editor/debugging)

## <a name="publish-your-app-to-teams"></a>Veröffentlichen Ihrer App in Teams

Bevor sie von anderen Personen verwendet werden kann, müssen Sie Ihre App für Teams im Entwicklerportal veröffentlichen.

1. Navigieren Sie zum Veröffentlichen Ihrer App zur Registerkarte **Teams Toolkit** in Visual Studio Code.
1. Wählen Sie im Abschnitt **Project** in **Teams veröffentlichen** aus.

Wenn Sie Azure-Hosting verwenden, müssen Sie die Cloud bereitgestellt und bereitgestellt haben. Eine exemplarische Vorgehensweise zum SPFx Veröffentlichungsprozess finden Sie im [SPFx Lernprogramm.](../get-started/first-app-spfx.md)

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Verwalten und Unterstützen Ihrer veröffentlichten App](../concepts/deploy-and-publish/appsource/post-publish/overview.md)
