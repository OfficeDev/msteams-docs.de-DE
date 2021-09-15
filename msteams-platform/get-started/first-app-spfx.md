---
title: Erste Schritte – Erstellen Ihrer ersten Teams-App mit SPFx
author: zhenyasav
description: Erfahren Sie, wie Sie eine benutzerdefinierte Registerkarte mit dem SharePoint-Framework
ms.author: zhenyasa
ms.date: 05/19/2021
ms.topic: quickstart
ms.localizationpriority: none
ms.openlocfilehash: 36aa779db0c45ab3724673cb0030a97cceef6a78
ms.sourcegitcommit: 72de146d11e81fd9777374dd3915ad290fd07d82
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/15/2021
ms.locfileid: "59360812"
---
# <a name="build-and-run-your-first-microsoft-teams-app-with-sharepoint-framework-spfx"></a>Erstellen und Ausführen Ihrer ersten Microsoft Teams-App mit SharePoint-Framework (SPFx)

In diesem Lernprogramm erfahren Sie, wie Sie eine neue Microsoft Teams-App in SharePoint-Framework SPFx erstellen, die eine einfache persönliche App implementiert. Beispielsweise enthält eine *persönliche App* eine Reihe von Registerkarten für die individuelle Verwendung. Während des Lernprogramms erfahren Sie mehr über die Struktur einer Teams-App, wie Sie eine App lokal ausführen und wie Sie die App für SharePoint bereitstellen.

## <a name="before-you-begin"></a>Bevor Sie beginnen

Stellen Sie sicher, dass Ihre Entwicklungsumgebung eingerichtet ist, indem Sie die erforderlichen Komponenten installieren.

> [!div class="nextstepaction"]
> [Erforderliche Komponenten installieren](prerequisites.md)

## <a name="get-organized"></a>Besser organisiert sein

Zusätzlich zu den Voraussetzungen müssen Sie auch Administrator für eine SharePoint-Websitesammlung sein.  Hier stellen Sie Ihre App für das Hosting bereit.  Wenn Sie einen Mandanten des M365-Entwicklerprogramms verwenden, verwenden Sie das Administratorkonto, das Sie bei der Registrierung für das Programm eingerichtet haben.  

## <a name="create-your-project"></a>Erstellen Ihres Projekts

Verwenden Sie zum Erstellen Ihres ersten Projekts das Microsoft Teams-Toolkit:

# <a name="visual-studio-code"></a>[Visual Studio Code](#tab/vscode)

1. Öffnen Sie Visual Studio Code.
1. Wählen Sie das symbol Teams in der Randleiste aus, um das Teams Toolkit zu öffnen.

    :::image type="content" source="../assets/images/teams-toolkit-v2/sidebar-icon.png" alt-text="Das Microsoft Teams-Symbol in der Visual Studio Code-Randleiste.":::

1. Klicken Sie auf **Neues Projekt erstellen**.

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project.png" alt-text="Ort des Links „Neues Projekt erstellen“ in der Randleiste des Microsoft Teams-Toolkits.":::

1. Wählen Sie **Neue Microsoft Teams-App erstellen** aus.

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-new-project-intro.png" alt-text="Starten des Assistenten für „Neues Projekt erstellen“":::

1. Wählen Sie im Abschnitt **"Funktionen auswählen"** die Option **"Registerkarte"** und dann **"OK"** aus.

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project-capabilities.png" alt-text="Screenshot, der zeigt, wie Ihrer neuen App Funktionen hinzufügt werden können.":::

1. Wählen Sie im Abschnitt zum **Frontend-Hostingtyp** **SharePoint-Framework (SPFx)** aus.

   :::image type="content" source="../assets/images/teams-toolkit-v2/create-project-hosting.png" alt-text="Screenshot, der zeigt, wie das Hosting für Ihre neue App ausgewählt wird.":::

1. Wählen Sie im Abschnitt **"Framework"** **React** aus.

   :::image type="content" source="../assets/images/teams-toolkit-v2/spfx-which-framework.png" alt-text="Auswählen des Frameworks":::

1. Wenn Sie nach einem **Webpartnamen** gefragt werden, drücken Sie die **EINGABETASTE,** um die Standardeinstellung zu übernehmen.

1. Wenn Sie nach der **Webpartbeschreibung** gefragt werden, drücken Sie die **EINGABETASTE,** um die Standardeinstellung zu übernehmen.

1. Wenn Sie nach der **Programmiersprache** gefragt werden, drücken Sie die **EINGABETASTE,** um die Standardeinstellung zu übernehmen.

1. Wählen Sie einen Arbeitsbereichsordner aus.  Innerhalb Ihres Arbeitsbereichsordners wird für das von Ihnen erstellte Projekt ein Ordner erstellt.

1. Geben Sie einen passenden Namen für Ihre App ein, wie z. B. `helloworld`.  Der Name der App darf nur aus alphanumerischen Zeichen bestehen.  Drücken Sie die **EINGABETASTE**, um fortzufahren.

   Ihre Microsoft Teams-App wird innerhalb weniger Sekunden erstellt.

# <a name="command-line"></a>[Befehlszeile](#tab/cli)

Verwenden Sie die `teamsfx`-CLI zum Erstellen Ihres ersten Projekts.  Beginnen Sie in dem Ordner, in dem Sie den Projektordner erstellen möchten.

``` bash
teamsfx new
```

Die CLI führt durch einige Fragen zum Erstellen des Projekts.  Bei jeder Frage wird angegeben, wie Sie sie beantworten können (z. B. mithilfe von Pfeiltasten, um eine Option auszuwählen).  Wenn Sie eine Frage beantwortet haben, bestätigen Sie Ihre Auswahl, indem Sie die **EINGABETASTE** drücken.

1. Wählen Sie **Neue Microsoft Teams-App erstellen** aus.
1. Registerkarte **auswählen.**
1. Wählen Sie **SharePoint-Framework (SPFx)** Front-End-Hosting aus.
1. Wählen Sie **React** Framework aus.
1. Drücken Sie die **EINGABETASTE** für den **Webpartnamen.**
1. Drücken Sie die **EINGABETASTE** für die **Webpartbeschreibung.**
1. Drücken Sie die **EINGABETASTE** für die **Programmiersprache.**
1. Drücken Sie die **EINGABETASTE**, um den Standardordner des Arbeitsbereichs auszuwählen.
1. Geben Sie einen passenden Namen für Ihre App ein, wie z. B. `helloworld`.  Der Name der App darf nur aus alphanumerischen Zeichen bestehen.

   Nachdem alle Fragen beantwortet wurden, wird Ihr Projekt erstellt.

---

- [Weitere Informationen zur Entwicklung für SharePoint-Framework](/sharepoint/dev/spfx/sharepoint-framework-overview)

## <a name="take-a-tour-of-the-source-code"></a>Machen Sie einen Rundgang durch den Quellcode

Wenn Sie diesen Abschnitt vorerst überspringen möchten, können Sie [Ihre App lokal ausführen](#run-your-app-locally).

Nachdem das Teams Toolkit Ihr Projekt konfiguriert hat, verfügen Sie über die Komponenten zum Erstellen einer einfachen persönlichen App für Teams, die in der SharePoint-Framework gehostet wird.  Die Projektverzeichnisse und -dateien werden im Explorer-Bereich von Visual Studio Code angezeigt.

:::image type="content" source="../assets/images/teams-toolkit-v2/app-project-files-spfx.png" alt-text="Screenshot der App-Projektdateien für eine persönliche App in Visual Studio Code":::

Das Toolkit erstellt im Projektverzeichnis automatisch Ordner basierend auf den Funktionen, die Sie während des Setups hinzugefügt haben. Das Microsoft Teams Toolkit behält seinen Status für Ihre App im `.fx`-Verzeichnis bei. 

- Die Einstellungen, die Sie beim Erstellen des Projekts ausgewählt haben, werden in `.fx/settings.json` gespeichert.
- Der Status Ihres Projekts wird in `.fx/env.*.json` gespeichert.

Und die Teams App-Informationen werden im `appPackage` Verzeichnis gespeichert.

- Die App-Symbole werden als PNG-Dateien in `appPackage/color.png` und `appPackage/outline.png` gespeichert.
- Das App-Manifest für die Veröffentlichung im Entwicklerportal für Teams wird in `appPackage/manifest.source.json` gespeichert.


Da Sie ein SPFx Webpart-Projekt ausgewählt haben, sind die folgenden Dateien für Ihre Benutzeroberfläche relevant:

- Der Ordner `SPFx/src/webparts/{webpart}` enthält Ihr SPFx-Webpart.
- Die Datei `.vscode/launch.json` beschreibt die Debugkonfigurationen, die in der Debugpalette verfügbar sind.

Weitere Informationen zu SharePoint Webparts für Teams [finden Sie in der SharePoint Dokumentation.](/sharepoint/dev/spfx/build-for-teams-overview)

## <a name="run-your-app-locally"></a>Lokales Ausführen Ihrer App

Teams Mit dem Toolkit können Sie Ihre App lokal hosten und über die [SharePoint-Framework Workbench](/sharepoint/dev/spfx/debug-in-vscode)ausführen.

### <a name="build-and-run-your-app-locally-in-visual-studio-code"></a>Erstellen und lokales Ausführen der App in Visual Studio Code

So erstellen Sie Ihre App und führen sie lokal aus:

1. Drücken Sie von Visual Studio Code die **F5-TASTE.**

   :::image type="content" source="../assets/images/teams-toolkit-v2/spfx-debug-local.png" alt-text="Screenshot, der zeigt, wie sie eine SPFx-App in einer lokalen Workbench starten.":::

   > [!NOTE]
   > Wenn Sie die App zum ersten Mal ausführen, werden alle Abhängigkeiten heruntergeladen und die App wird erstellt.  Ein Browserfenster wird automatisch geöffnet und die SharePoint Workbench geladen, wenn der Build abgeschlossen ist.  Dies kann 3 bis 5 Minuten dauern.

   Nachdem die SharePoint Workbench geladen wurde.

   >[!NOTE]
   > Sie werden vom Toolkit aufgefordert, bei Bedarf ein lokales Zertifikat zu installieren. Mit diesem Zertifikat kann Microsoft Teams Ihre Anwendung von `https://localhost` laden. Wählen Sie "Ja" aus, wenn das folgende Dialogfenster angezeigt wird:

   :::image type="content" source="../assets/images/teams-toolkit-v2/ssl-prompt.png" alt-text="Screenshot mit Dialogfenster zum Installieren eines SSL-Zertifikats, damit Microsoft Teams Ihre Anwendung von localhost laden kann.":::

1. Wählen Sie **"Webpart hinzufügen+** Symbole" aus, um das Webpart hinzuzufügen.

   :::image type="content" source="../assets/images/teams-toolkit-v2/spfx-workbench-addpart.png" alt-text="Screenshot der SPFx Workbench, die mit dem Popup ausgeführt wird, um ein Webpart hinzuzufügen.":::

1. Wählen Sie ihr Webpart aus dem Menü aus.

   :::image type="content" source="../assets/images/teams-toolkit-v2/spfx-workbench-addpart2.png" alt-text="Screenshot der SPFx Workbench, die mit dem Popup ausgeführt wird, um eine Webpartauswahl hinzuzufügen.":::

   Ihre App sollte jetzt ausgeführt werden.  Sie können normale Debugaktivitäten ausführen, als ob dies ein anderes SPFx-Webpart wäre (z. B. das Festlegen von Haltepunkten).

   > [!TIP]
   > Versuchen Sie, Haltepunkte in der Rendermethode des Browserfensters zu platzieren `SPFx/src/webparts/{webpart}/{webpart}.ts` und neu zu laden. VS Code wird an Haltepunkten im Code beendet.

## <a name="deploy-your-app-to-sharepoint"></a>Bereitstellen Ihrer App für SharePoint

Stellen Sie sicher, dass in Ihrer Bereitstellung ein SharePoint App-Katalog vorhanden ist.  Wenn eine nicht vorhanden ist, [erstellen Sie eine](/sharepoint/use-app-catalog).  Es kann bis zu 15 Minuten dauern, bis der App-Katalog vollständig erstellt wurde.

# <a name="visual-studio-code"></a>[Visual Studio Code](#tab/vscode)

1. Öffnen Sie Visual Studio Code.
1. Wählen Sie in der Seitenleiste das Teams Toolkit aus, indem Sie das Symbol Teams auswählen.
1. Wählen Sie **"Bereitstellung in der Cloud" aus.**

   :::image type="content" source="../assets/images/teams-toolkit-v2/provisioning-commands.png" alt-text="Screenshot der Bereitstellungsbefehle":::

   Sie können den Fortschritt überwachen, indem Sie sich die Dialogfelder in der unteren rechten Ecke ansehen.  Nach ein paar Sekunden wird der folgende Hinweis angezeigt:

   :::image type="content" source="../assets/images/teams-toolkit-v2/provision-complete.png" alt-text="Screenshot des Dialogfelds &quot;Bereitstellung abgeschlossen&quot;.":::

1. Wählen Sie nach Abschluss der Bereitstellung die Option **"In der Cloud bereitstellen"** aus.

1. Derzeit ist keine automatisierte Bereitstellung verfügbar.  Ein Dialogfeld wird angezeigt, in dem Sie aufgefordert werden, manuell zu erstellen und bereitzustellen. Wählen Sie **Build SharePoint Package** aus.

   :::image type="content" source="../assets/images/teams-toolkit-v2/build-sharepoint-package.png" alt-text="Screenshot des Dialogfelds &quot;Sharepoint-Paket erstellen&quot;":::

# <a name="command-line"></a>[Befehlszeile](#tab/cli)

In Ihrem Terminalfenster:

1. Führen Sie `teamsfx provision` aus.

   ``` bash
   teamsfx provision
   ```

   Möglicherweise werden Sie aufgefordert, sich bei Ihrem Azure-Abonnement anzumelden.  Bei Bedarf werden Sie aufgefordert, ein Azure-Abonnement auszuwählen, das für die Azure-Ressourcen verwendet werden soll.

   > [!NOTE]
   > Es werden immer einige Azure-Ressourcen zum Hosten Ihrer App verwendet.

1. Führen Sie `teamsfx deploy` aus.

   ``` bash
   teamsfx deploy
   ```

1. Wenn Sie dazu aufgefordert werden, wählen Sie **"Build SharePoint Package"** aus.

---

Das SharePoint-Paket befindet sich in `SPFx/sharepoint/solution` Ihrem Projekt.  Hochladen das Paket zu SharePoint:

1. Melden Sie sich bei der M365 Admin Console an, und navigieren Sie dann zum SharePoint App-Katalog.

   1. Öffnen `https://admin.microsoft.com/AdminPortal/Home` Sie .
   1. Wählen Sie unter **Admin Center** das **SharePoint** Admin Center aus.
   1. Wählen Sie im Randleistenmenü **weitere Features** aus.
   1. Drücken Sie **"Öffnen"** unter **"Apps".**
   1. Wählen Sie **App-Katalog** aus.

1. Wählen Sie **"Apps für SharePoint verteilen"** aus.

    :::image type="content" source="../assets/images/teams-toolkit-v2/spfx-distribute-apps.png" alt-text="Verteilen von Apps für SharePoint.":::

1. Wählen Sie **Hochladen** aus.

1. Wählen Sie **"Datei auswählen"** aus.

1. Suchen Sie Ihre `{project}.sppkg` Datei im Ordner in Ihrem `SPFx/sharepoint/solution` Projekt. Klicken Sie auf **Öffnen**.

1. Wählen Sie **OK** aus.

1. Der SharePoint Bereitstellungsprozess wird automatisch gestartet. Stellen Sie sicher, dass **diese Lösung für alle Websites in der Organisation verfügbar** ist. Wählen Sie dann **Bereitstellen aus.**

1. Wählen Sie die Registerkarte **"DATEIEN" aus.**

    :::image type="content" source="../assets/images/teams-toolkit-v2/spfx-appcatalog-filestab.png" alt-text="Wählen Sie die Registerkarte &quot;Dateien&quot; im SharePoint App-Katalog aus.":::

1. wählen Sie das bereitgestellte Paket aus, und wählen Sie dann in der oberen rechten Ecke die Option **"Synchronisieren" aus, um Teams.**

    > [!Note]
    > Der Vorgang "Mit Teams synchronisieren" kann einige Minuten dauern.  Auf der rechten Seite des Browsers wird eine Meldung angezeigt, die angibt, dass die App erfolgreich mit Teams synchronisiert wurde.

   Öffnen Sie die Teams Anwendung (oder melden Sie sich bei `https://teams.microsoft.com` ) an.  Drücken Sie den dreistelligen Punkt auf der Seitenleiste, und wählen Sie dann **alle Apps** aus.  Die App wird in der Kategorie "Apps" platziert, die **für Ihre Organisationskategorie erstellt wurden.**  Sie können die App von dort hinzufügen.

   :::image type="content" source="../assets/images/teams-toolkit-v2/spfx-app-in-teams.png" alt-text="Screenshot der App in Teams":::

## <a name="see-also"></a>Siehe auch

* [Übersicht über Lernprogramme](code-samples.md)
* [Erstellen einer Unterhaltungs-Bot-App](first-app-bot.md)
* [Erstellen einer Messaging-Erweiterung](first-message-extension.md)
* [Codebeispiele](https://github.com/OfficeDev/Microsoft-Teams-Samples)
