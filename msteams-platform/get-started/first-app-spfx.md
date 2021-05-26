---
title: Erste Schritte – Erstellen Sie Ihre erste Teams-App mit SPFx
author: zhenyasav
description: Erfahren Sie, wie Sie eine benutzerdefinierte Registerkarte mit dem SharePoint-Framework
ms.author: zhenyasa
ms.date: 05/19/2021
ms.topic: quickstart
ms.openlocfilehash: 54886b47bbe70fed5dd1f010517e6c91d8d5a50d
ms.sourcegitcommit: 9cabeaed9baf96c8caeb1497f0bc37abdb787d22
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/25/2021
ms.locfileid: "52646770"
---
# <a name="build-and-run-your-first-microsoft-teams-app-with-sharepoint-framework-spfx"></a>Erstellen und Ausführen der ersten Microsoft Teams app mit SharePoint-Framework (SPFx)

In diesem Lernprogramm erstellen Sie eine neue Microsoft Teams-App in SharePoint-Framework (SPFx), die eine einfache persönliche App implementiert. (Eine *persönliche App* enthält eine Reihe von Registerkarten, die für die individuelle Verwendung festgelegt sind.) Während des Lernprogramms erfahren Sie mehr über die Struktur einer Teams-App, über das lokale Ausführen der App und über die Bereitstellung der App SharePoint.

## <a name="before-you-begin"></a>Bevor Sie beginnen:

Stellen Sie sicher, dass Ihre Entwicklungsumgebung eingerichtet ist, indem Sie die [erforderlichen Komponenten installieren.](prerequisites.md)

> [!div class="nextstepaction"]
> [Installieren der erforderlichen Komponenten](prerequisites.md)

## <a name="get-organized"></a>Besser organisiert sein

Zusätzlich zu den Voraussetzungen müssen Sie auch Administrator für eine websitesammlung SharePoint sein.  Hier stellen Sie Ihre App für das Hosting zur Bereitstellung.  Wenn Sie einen Mandanten des M365-Entwicklerprogramms verwenden, verwenden Sie das Administratorkonto, das Sie bei der Registrierung für das Programm eingerichtet haben.  

## <a name="create-your-project"></a>Erstellen Ihres Projekts

Verwenden Sie das Teams Toolkit, um Ihr erstes Projekt zu erstellen:

# <a name="visual-studio-code"></a>[Visual Studio Code](#tab/vscode)

1. Öffnen Visual Studio Code.
1. Öffnen Sie Teams Toolkit, indem Sie Teams in der Seitenleiste auswählen:

    :::image type="content" source="../assets/images/teams-toolkit-v2/sidebar-icon.png" alt-text="Das Teams Symbol in der Visual Studio Code Seitenleiste.":::

1. Wählen **Sie Neue Project** aus.

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project.png" alt-text="Speicherort des Links Neue Project erstellen in der Teams Toolkit-Seitenleiste.":::

1. Wählen **Sie Create a new Teams app aus.**

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-new-project-intro.png" alt-text="Assistentenstart für Neue Project":::

1. Im Schritt **Funktionen auswählen** wird die **Tab-Funktion** bereits ausgewählt.  Drücken Sie **OK**.

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project-capabilities.png" alt-text="Screenshot, der zeigt, wie Sie Ihrer neuen App Funktionen hinzufügen.":::

1. Wählen Sie **im Schritt Frontend-Hostingtyp** **SharePoint-Framework (SPFx) aus.**

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project-hosting.png" alt-text="Screenshot, der zeigt, wie Sie das Hosting für Ihre neue App auswählen.":::

1. Wählen Sie **im Schritt Framework** die Option **React** aus.

   :::image type="content" source="../assets/images/teams-toolkit-v2/spfx-which-framework.png" alt-text="Select Framework":::

1. Wenn Sie nach einem **Webpartnamen gefragt werden,** drücken Sie **die EINGABETASTE,** um die Standardeinstellung zu akzeptieren.

1. Wenn Sie nach der **Webpartbeschreibung gefragt werden,** drücken Sie **die EINGABETASTE,** um die Standardeinstellung zu akzeptieren.

1. Wenn Sie nach der **Programmiersprache gefragt werden,** drücken Sie **die EINGABETASTE,** um die Standardeinstellung zu akzeptieren.

1. Wählen Sie einen Arbeitsbereichsordner aus.  In Ihrem Arbeitsbereichsordner wird ein Ordner für das Projekt erstellt, das Sie erstellen.

1. Geben Sie einen geeigneten Namen für Ihre App ein, z. `helloworld` B. .  Der Name der App darf nur aus alphanumerischen Zeichen bestehen.  Drücken **Sie die EINGABETASTE,** um fortzufahren.

Ihre Teams-App wird innerhalb weniger Sekunden erstellt.

# <a name="command-line"></a>[Befehlszeile](#tab/cli)

Verwenden Sie die `teamsfx` CLI, um Ihr erstes Projekt zu erstellen.  Beginnen Sie mit dem Ordner, in dem Sie den Projektordner erstellen möchten.

``` bash
teamsfx new
```

Die CLI führt einige Fragen durch, um das Projekt zu erstellen.  Jede Frage wird Ihnen mitteilen, wie sie beantwortet werden soll (z. B. verwenden Sie Pfeiltasten, um eine Option auszuwählen).  Wenn Sie die Frage beantwortet haben, bestätigen Sie Ihre Auswahl, indem Sie die **EINGABETASTE drücken.**

1. Wählen **Sie Create a new Teams app aus.**
1. Wählen Sie die **Tab-Funktion** aus.
1. Wählen **SharePoint-Framework (SPFx)** Frontendhosting aus.
1. Wählen **React** Framework aus.
1. Drücken **Sie die EINGABETASTE** für den **Webpartnamen**.
1. Drücken **Sie die EINGABETASTE** für **die Webpartbeschreibung**.
1. Drücken **Sie die EINGABETASTE** für **die Programmiersprache**.
1. Drücken **Sie die EINGABETASTE,** um den Standardarbeitsbereichsordner auszuwählen.
1. Geben Sie einen geeigneten Namen für Ihre App ein, z. `helloworld` B. .  Der Name der App darf nur aus alphanumerischen Zeichen bestehen.

Nachdem alle Fragen beantwortet wurden, wird Ihr Projekt erstellt.

---

- [Erfahren Sie mehr über die Entwicklung für SharePoint-Framework](/sharepoint/dev/spfx/sharepoint-framework-overview)

## <a name="take-a-tour-of-the-source-code"></a>Machen Sie einen Rundgang durch den Quellcode

Wenn Sie diesen Abschnitt vorerst überspringen möchten, können Sie [Ihre App lokal ausführen.](#run-your-app-locally)

Sobald Teams Toolkit Ihr Projekt konfiguriert hat, verfügen Sie über die Komponenten zum Erstellen einer einfachen persönlichen App für Teams, die innerhalb des SharePoint-Framework.  Die Projektverzeichnissen und -dateien werden im Explorer-Bereich von Visual Studio Code.

:::image type="content" source="../assets/images/teams-toolkit-v2/app-project-files-spfx.png" alt-text="Screenshot mit App-Projektdateien für eine persönliche App in Visual Studio Code.":::

Das Toolkit erstellt automatisch ein Gerüst für Sie im Projektverzeichnis basierend auf den Funktionen, die Sie während des Setups hinzugefügt haben. Das Teams Toolkit behält seinen Status für Ihre App im Verzeichnis `.fx` bei.  Unter anderen Elementen in diesem Verzeichnis:

- Die App-Symbole werden als PNG-Dateien in `color.png` und `outline.png` gespeichert.
- Das App-Manifest für die Veröffentlichung im Entwicklerportal für Teams wird in `manifest.source.json` gespeichert.
- Die Einstellungen, die Sie beim Erstellen des Projekts ausgewählt haben, werden in `settings.json` gespeichert.

Da Sie ein SPFx Webpartprojekt ausgewählt haben, sind die folgenden Dateien für Die Benutzeroberfläche relevant:

- Der Ordner `SPFx/src/webparts/{webpart}` enthält SPFx Webpart.
- In der `.vscode/launch.json` Datei werden die Debugkonfigurationen beschrieben, die in der Debugpalette verfügbar sind.

Weitere Informationen zu SharePoint Webparts für Teams finden Sie in der [SharePoint Dokumentation](/sharepoint/dev/spfx/build-for-teams-overview).

## <a name="run-your-app-locally"></a>Lokales Ausführen der App

Teams Toolkit ermöglicht Es Ihnen, Ihre App lokal zu hosten und sie über die [SharePoint-Framework Workbench ausführen.](/sharepoint/dev/spfx/debug-in-vscode)

### <a name="build-and-run-your-app-locally-in-visual-studio-code"></a>Erstellen und ausführen Sie Ihre App lokal in Visual Studio Code

So erstellen und führen Sie Ihre App lokal aus:

1. Drücken Visual Studio Code **F5**.

   :::image type="content" source="../assets/images/teams-toolkit-v2/spfx-debug-local.png" alt-text="Screenshot, der zeigt, wie sie SPFx in einer lokalen Workbench starten.":::

   > [!NOTE]
   > Wenn Sie die App zum ersten Mal ausführen, werden alle Abhängigkeiten heruntergeladen und die App erstellt.  Ein Browserfenster wird automatisch geöffnet und lädt die SharePoint Workbench, wenn der Build abgeschlossen ist.  Dies kann 3 bis 5 Minuten dauern.

   Sobald SharePoint Workbench geladen wurde.

   >[!NOTE]
   > Das Toolkit fordert Sie auf, bei Bedarf ein lokales Zertifikat zu installieren. Dieses Zertifikat ermöglicht Teams, ihre Anwendung aus zu `https://localhost` laden. Wählen Sie Ja aus, wenn das folgende Dialogfeld angezeigt wird:

   :::image type="content" source="../assets/images/teams-toolkit-v2/ssl-prompt.png" alt-text="Screenshot, der zeigt, wie die Aufforderung zum Installieren eines SSL-Zertifikats angezeigt wird, Teams die Anwendung von localhost laden zu können.":::

1. Drücken Sie eines der **Symbole Webpart hinzufügen** (+), um Ihr Webpart hinzuzufügen.

   :::image type="content" source="../assets/images/teams-toolkit-v2/spfx-workbench-addpart.png" alt-text="Screenshot der SPFx workbench, die mit dem Popup ausgeführt wird, um ein Webpart hinzuzufügen, das angezeigt wird.":::

1. Wählen Sie ihr Webpart aus dem Menü aus.

   :::image type="content" source="../assets/images/teams-toolkit-v2/spfx-workbench-addpart2.png" alt-text="Screenshot der SPFx Workbench, die mit dem Popup ausgeführt wird, um eine Webpartauswahl hinzuzufügen.":::

Ihre App sollte jetzt ausgeführt werden.  Sie können normale Debugaktivitäten so tun, als wäre dies eine andere SPFx Webpart (z. B. Festlegen von Haltepunkten).

> [!TIP]
> Versuchen Sie, Haltepunkte in der Rendermethode von zu platzieren `SPFx/src/webparts/{webpart}/{webpart}.ts` und das Browserfenster neu zu laden. VS Code wird an Haltepunkten in Ihrem Code beendet.

## <a name="deploy-your-app-to-sharepoint"></a>Bereitstellen Ihrer App für SharePoint

Stellen Sie sicher, SharePoint App-Katalog in Ihrer Bereitstellung vorhanden ist.  Wenn sie nicht vorhanden ist, [erstellen Sie eine](/sharepoint/use-app-catalog).  Es kann bis zu 15 Minuten dauern, bis der App-Katalog vollständig erstellt ist.

# <a name="visual-studio-code"></a>[Visual Studio Code](#tab/vscode)

1. Öffnen Sie Visual Studio Code.
1. Wählen Sie Teams Toolkit aus der Seitenleiste aus, indem Sie das Symbol Teams auswählen.
1. Wählen **Sie Bereitstellung in der Cloud aus.**

   :::image type="content" source="../assets/images/teams-toolkit-v2/provisioning-commands.png" alt-text="Screenshot der Bereitstellungsbefehle":::

1. Sie können den Fortschritt überwachen, indem Sie die Dialogfelder in der unteren rechten Ecke ansehen.  Nach einigen Sekunden wird der folgende Hinweis angezeigt:

   :::image type="content" source="../assets/images/teams-toolkit-v2/provision-complete.png" alt-text="Screenshot des Dialogfelds &quot;Bereitstellung abgeschlossen&quot;.":::

1. Nachdem die Bereitstellung abgeschlossen ist, wählen **Sie Bereitstellen in der Cloud aus.**

1. Derzeit ist die automatisierte Bereitstellung nicht verfügbar.  Es wird ein Dialogfeld angezeigt, in dem Sie aufgefordert werden, manuell zu erstellen und zu bereitstellen. Drücken **Sie build SharePoint Package**.

   :::image type="content" source="../assets/images/teams-toolkit-v2/build-sharepoint-package.png" alt-text="Screenshot für das Dialogfeld Sharepoint-Paket erstellen":::

# <a name="command-line"></a>[Befehlszeile](#tab/cli)

Im Terminalfenster:

1. Führen Sie `teamsfx provision` aus.

   ``` bash
   teamsfx provision
   ```

   Möglicherweise werden Sie aufgefordert, sich bei Ihrem Azure-Abonnement zu melden.  Bei Bedarf werden Sie aufgefordert, ein Azure-Abonnement auszuwählen, das für die Azure-Ressourcen verwendet werden soll.

   > [!NOTE]
   > Es gibt immer einige Azure-Ressourcen, die für das Hosten Ihrer App verwendet werden.

1. Führen Sie `teamsfx deploy` aus.

   ``` bash
   teamsfx deploy
   ```

1. Wenn Sie dazu aufgefordert werden, wählen **Sie Build SharePoint Package aus.**

---

Das SharePoint befindet sich in `SPFx/sharepoint/solution` Ihrem Projekt.  Hochladen paket, das sie SharePoint:

1. Melden Sie sich bei der M365 Admin Console an, und navigieren Sie dann zum SharePoint App-Katalog.

   - Öffnen `https://admin.microsoft.com/AdminPortal/Home` Sie .
   - Wählen **Sie unter Admin Center** das **SharePoint** Admin Center aus.
   - Wählen **Sie im** Menü Nebenleiste weitere Features aus.
   - Drücken **Sie öffnen** unter **Apps**.
   - Wählen Sie **App-Katalog aus.**

1. Wählen **Sie Verteilen von Apps für SharePoint** aus.

    :::image type="content" source="../assets/images/teams-toolkit-v2/spfx-distribute-apps.png" alt-text="Verteilen von Apps für SharePoint.":::

1. Wählen **Sie Hochladen** aus.

1. Drücken **Sie Datei auswählen.**

1. Suchen Sie `{project}.sppkg` die Datei im Ordner in Ihrem `SPFx/sharepoint/solution` Projekt.  Drücken **Sie öffnen**.

1. Drücken Sie **OK**.

1. Der SharePoint wird automatisch gestartet.  Stellen **Sie sicher, dass diese Lösung für alle Websites in der** Organisation verfügbar ist aktiviert ist, und drücken Sie dann die Deploy **-Taste.**

1. Wählen Sie die **Registerkarte DATEIEN** aus.

    :::image type="content" source="../assets/images/teams-toolkit-v2/spfx-appcatalog-filestab.png" alt-text="Wählen Sie die Registerkarte Dateien im SharePoint App-Katalog aus.":::

1. Wählen Sie das bereitgestellte Paket aus, und drücken Sie dann die Teams **im** Menüband.

    > [!Note]
    > Die Synchronisierung mit Teams kann einige Minuten dauern.  Auf der rechten Seite des Browsers wird eine Meldung angezeigt, die angibt, dass die App erfolgreich mit Teams.

Öffnen Sie Teams -Anwendung (oder melden Sie sich unter `https://teams.microsoft.com` ) an.  Drücken Sie den Dreipunkt auf der Seitenleiste, und wählen Sie **Dann Alle Apps aus.**  Die App wird in der Kategorie **Apps platziert, die für Ihre Organisationskategorie erstellt** wurden.  Sie können die App von dort hinzufügen.

:::image type="content" source="../assets/images/teams-toolkit-v2/spfx-app-in-teams.png" alt-text="Screenshot der App innerhalb Teams":::

## <a name="next-steps"></a>Nächste Schritte

Erfahren Sie mehr über andere Methoden zum Erstellen Teams Apps:

- [Erstellen einer Teams App mit React](first-app-react.md)
- [Erstellen einer Teams App mit Blazor](first-app-blazor.md)
- [Erstellen einer Unterhaltungsbot-App](first-app-bot.md)
- [Erstellen einer Messaging-Erweiterung](first-message-extension.md)
