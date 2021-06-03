---
title: Erstellen von Apps mit dem Microsoft Teams Toolkit und Visual Studio Code
description: Erste Schritte beim Erstellen großartiger benutzerdefinierter Apps direkt Visual Studio Code mit dem Microsoft Teams Toolkit
keywords: Teams Visual Studio Code Toolkit
localization_priority: Normal
ms.topic: overview
ms.author: lajanuar
ms.openlocfilehash: bc97a78df5618c87dfc66fae179145acd749ad1f
ms.sourcegitcommit: 33a43c61f27ae750776616b2cf90159455d8ba6c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/02/2021
ms.locfileid: "52721822"
---
# <a name="build-apps-with-the-teams-toolkit-and-visual-studio-code"></a>Erstellen von Apps mit dem Teams Toolkit und Visual Studio Code

Das Teams Toolkit für Visual Studio Code unterstützt Entwickler beim Erstellen und Bereitstellen von Teams-Apps mit integrierter Identität, Zugriff auf Cloudspeicher, Daten von Microsoft Graph und anderen Diensten in Azure und M365 mit einem Ansatz der Nullkonfiguration für die Entwicklererfahrung.  

Sie können das Toolkit auch mit Visual Studio oder als CLI `teamsfx` (genannt) verwenden.

## <a name="install-the-teams-toolkit-for-visual-studio-code"></a>Installieren des Teams Toolkits für Visual Studio Code

1. Öffnen Sie Visual Studio Code.
1. Wählen Sie die Ansicht Erweiterungen (**STRG+Umschalt+X**  /  **.⇧-X** oder **Ansicht > Erweiterungen ).**
1. Geben Sie im Suchfeld Teams _Toolkit ein._
1. Wählen Sie auf der grünen Installationsschaltfläche neben dem Teams Toolkit aus.

Sie finden auch das Teams Toolkit im [Visual Studio Code Marketplace](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension).

Die folgenden Tools werden von der erweiterung Visual Studio Code installiert, wenn sie benötigt werden.  Wenn sie bereits installiert ist, wird stattdessen die installierte Version verwendet.  Wenn Sie Linux (einschließlich WSL) verwenden, müssen Sie diese Tools vor der Verwendung installieren:

- [Azure Functions Core Tools](/azure/azure-functions/functions-run-local)

    Azure Functions Core Tools wird verwendet, um alle Back-End-Komponenten während einer lokalen Debug ausgeführt, einschließlich der Authentifizierungshilfen, die beim Ausführen Ihrer Dienste in Azure erforderlich sind.  Es wird im Projektverzeichnis installiert (mit npm `devDependencies` ).

- [.NET SDK](/dotnet/core/install/)

    Das .NET SDK wird verwendet, um angepasste Bindungen für lokale Debugging- und Azure Functions-App-Bereitstellungen zu installieren.  Wenn Sie das .NET 3.1 (oder höher) SDK nicht global installiert haben, wird die portable Version installiert.

- [ngrok](https://ngrok.com/download)

    Einige Teams (Unterhaltungsbots, Messagingerweiterungen und eingehende Webhooks) erfordern eingehende Verbindungen.  Sie müssen Ihr Entwicklungssystem für die Teams Tunnel verfügbar machen.  Für Apps, die nur Registerkarten enthalten, ist kein Tunnel erforderlich.  Dieses Paket wird im Projektverzeichnis installiert (mithilfe von npm `devDependencies` ).

## <a name="use-the-teams-toolkit-for-visual-studio-code"></a>Verwenden sie Teams Toolkit für Visual Studio Code

- [Einrichten eines neuen Projekts](#set-up-a-new-teams-project)
- [Konfigurieren Sie die App](#configure-your-app)
- [Lokales Ausführen Ihrer App](#install-and-run-your-app-locally)
- [Veröffentlichen eigener Apps](#publish-your-app-to-teams)

## <a name="set-up-a-new-teams-project"></a>Einrichten eines neuen Teams Projekt

Das Teams Toolkit kann React Apps erstellen, die in Azure gehostet werden, oder SPFx Webparts, die in Ihrer M365-Umgebung SharePoint werden.  So erstellen Sie eine React app, die in Azure gehostet werden soll:

1. Öffnen Sie Visual Studio Code.
1. Öffnen Sie das Microsoft Teams-Toolkit, indem Sie auf das Microsoft Teams-Symbol in der Randleiste klicken:

    :::image type="content" source="../assets/images/teams-toolkit-v2/sidebar-icon.png" alt-text="Das Microsoft Teams-Symbol in der Visual Studio Code-Randleiste.":::

1. Klicken Sie auf **Neues Projekt erstellen**.

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project.png" alt-text="Ort des Links „Neues Projekt erstellen“ in der Randleiste des Microsoft Teams-Toolkits.":::

1. Wählen Sie **Neue Microsoft Teams-App erstellen** aus.

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-new-project-intro.png" alt-text="Starten des Assistenten für „Neues Projekt erstellen“":::

1. Im Schritt **Funktionen auswählen** ist die Funktion **Registerkarten** bereits ausgewählt.  Optional können Sie auch **Bot** und **Messaging Extension auswählen.**  Drücken Sie **OK**.

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project-capabilities.png" alt-text="Screenshot, der zeigt, wie Ihrer neuen App Funktionen hinzufügt werden können.":::

1. Wählen Sie im Schritt **Frontend-Hostingtyp** die Option **Azure** aus.

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project-hosting.png" alt-text="Screenshot, der zeigt, wie das Hosting für Ihre neue App ausgewählt wird.":::

1. (Optional) Wählen Sie **im Schritt Cloudressourcen** die Von Ihrer Anwendung verwendeten Cloudressourcen aus.  Sie können den CRUD-Zugriff (erstellen, lesen, aktualisieren, löschen) auf eine SQL oder eine API auswählen:

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project-cloud-resources.png" alt-text="Screenshot, der zeigt, wie Cloudressourcen für Ihre neue App hinzugefügt werden.":::

1. Im Schritt **Programmiersprache** können Sie **JavaScript** oder **TypeScript auswählen:**

    :::image type="content" source="../assets/images/teams-toolkit-v2/create-project-programming-languages.png" alt-text="Screenshot, der zeigt, wie die Programmiersprache ausgewählt wird.":::

1. Wählen Sie einen Arbeitsbereichsordner aus.  Innerhalb Ihres Arbeitsbereichsordners wird für das von Ihnen erstellte Projekt ein Ordner erstellt.

1. Geben Sie einen passenden Namen für Ihre App ein, wie z. B. `helloworld`.  Der Name der App darf nur aus alphanumerischen Zeichen bestehen.  Drücken Sie die **EINGABETASTE**, um fortzufahren.

Ihre Microsoft Teams-App wird innerhalb weniger Sekunden erstellt.  Die Gerüst-App enthält Code zum Verarbeiten der einmaligen Anmeldung mit Azure Active Directory und Zugriff auf die Microsoft-Graph.  Wenn Sie Azure-Ressourcen ausgewählt haben, ist auch der Code für diese Ressourcen verfügbar.

Eine Einführung in den Erstellungs- SPFx Veröffentlichungsprozess finden Sie im [SPFx Lernprogramm](../get-started/first-app-spfx.md).

## <a name="configure-your-app"></a>Konfigurieren Sie die App

Im Kern umfasst die Teams drei Komponenten:

  1. Der Microsoft Teams (Web, Desktop oder Mobile), auf dem Benutzer mit Ihrer App interagieren.
  1. Ein Server, der auf Anforderungen nach Inhalten reagiert, die in der Teams. Beispiel: HTML-Registerkarteninhalt oder eine adaptive Botkarte.
  1. Ein Teams-App-Paket besteht aus drei Dateien:

      > [!div class="checklist"]
      >
      > - Die manifest.jsein.
      > - Ein [Farbsymbol](../resources/schema/manifest-schema.md#icons) für Ihre App, das im öffentlichen Oder Organisations-App-Katalog angezeigt werden soll.
      > - Ein [Gliederungssymbol](../resources/schema/manifest-schema.md#icons) für die Anzeige Teams Aktivitätsleiste.

Das Manifest und die Symbole werden im Ordner Ihres Projekts gespeichert, bevor sie in das `.fx` Teams. Wenn eine App installiert ist, analysiert Teams-Client die Manifestdatei, um die erforderlichen Informationen wie den Namen Ihrer App und die URL zu ermitteln, in der sich die Dienste befinden.

1. Um Ihre App zu konfigurieren, navigieren Sie zur **Registerkarte Teams Toolkit** in Visual Studio Code.
1. Wählen **Sie im Abschnitt Project Manifest-Editor** aus. 

Durch Bearbeiten der Felder auf der Seite App-Details werden die Inhalte der datei manifest.jsaktualisiert, die letztendlich als Teil des App-Pakets versandt werden.

## <a name="install-and-run-your-app-locally"></a>Installieren und Ausführen der App lokal

So erstellen Sie Ihre App und führen sie lokal aus:

1. Drücken Sie in Visual Studio Code **F5**, um die Anwendung im Debugmodus auszuführen.

   > Wenn Sie die App zum ersten Mal ausführen, werden alle Abhängigkeiten heruntergeladen und die App wird erstellt.  Wenn die Erstellung abgeschlossen ist, wird automatisch ein Browserfenster geöffnet.  Dies kann 3 bis 5 Minuten dauern.

   Das Toolkit fordert Sie auf, bei Bedarf ein lokales Zertifikat zu installieren. Mit diesem Zertifikat kann Microsoft Teams Ihre Anwendung von `https://localhost` laden. Wählen Sie "Ja" aus, wenn das folgende Dialogfenster angezeigt wird:

   :::image type="content" source="../assets/images/teams-toolkit-v2/ssl-prompt.png" alt-text="Screenshot mit Dialogfenster zum Installieren eines SSL-Zertifikats, damit Microsoft Teams Ihre Anwendung von localhost laden kann.":::

1. Ihr Webbrowser wird gestartet, um die Anwendung auszuführen. Wenn Sie zum Öffnen von Microsoft Teams aufgefordert werden, wählen Sie „Abbrechen“ aus, um im Browser zu verbleiben. Möglicherweise werden Sie auch aufgefordert, zu anderen Teams zu wechseln. Wählen Sie in diesem Fall die Web-App aus.

   :::image type="content" source="../assets/images/teams-toolkit-v2/launch-web-browser-and-pick-webapp.png" alt-text="Screenshot, der zeigt, wie die Web-Version von Microsoft Teams beim Start ausgewählt wird.":::

1. Möglicherweise werden Sie aufgefordert, sich anzumelden.  Melden Sie sich in diesem Fall mit Ihrem M365-Konto an.
1. Wenn Sie aufgefordert werden, die App in Microsoft Teams zu installieren, drücken Sie **Hinzufügen**.

Sowohl das Back-End als auch das Frontend sind in den debugger Visual Studio Code integriert.  Auf diese Weise können Sie Haltepunkte an einer beliebigen Stelle im Code festlegen und den Zustand überprüfen.  Sie können auch alle Frontend-Debugtools (z. B. React Entwicklertools) im Browser verwenden.  Weitere Informationen zum Debuggen in Visual Studio Code finden Sie [in der Dokumentation](https://code.visualstudio.com/Docs/editor/debugging).

## <a name="publish-your-app-to-teams"></a>Veröffentlichen Ihrer App in Teams

Bevor sie von anderen Personen verwendet werden kann, müssen Sie Ihre App im Entwicklerportal veröffentlichen, um Teams.

1. Um Ihre App zu veröffentlichen, navigieren Sie zur **Registerkarte Teams Toolkit** in Visual Studio Code.
1. Wählen **Sie im Abschnitt Teams** veröffentlichen **Project** aus.

Wenn Sie Das Azure-Hosting verwenden, müssen Sie in der Cloud bereitgestellt und bereitgestellt haben. Eine Einführung in den Veröffentlichungsprozess SPFx finden Sie im [SPFx Lernprogramm](../get-started/first-app-spfx.md).

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Verwalten und Unterstützen Ihrer veröffentlichten App](../concepts/deploy-and-publish/appsource/post-publish/overview.md)
