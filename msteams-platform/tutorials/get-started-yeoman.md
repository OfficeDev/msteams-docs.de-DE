---
title: Tutorial - Erstellen Sie Ihre erste App mit dem Yeoman Generator
description: Erfahren Sie, wie Sie mit dem Erstellen Microsoft Teams Apps mit dem Yeoman-Generator beginnen.
keywords: erste Schritte node.js nodejs yeoman
localization_priority: Normal
ms.topic: tutorial
ms.custom: scenarios:getting-started
ms.openlocfilehash: 96a4f64d487e1d16bf25abd978759fedeac1061c
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566824"
---
# <a name="create-your-first-microsoft-teams-app-using-the-yeoman-generator"></a>Erstellen Sie Ihre erste Microsoft Teams-App mit dem Yeoman-Generator

> [!Note]
> Dieses Tutorial kommt vom [Yeoman Generator für Teams Wiki](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App).

In diesem Tutorial werden wir durch die Erstellung Ihrer allerersten Microsoft Teams App mit dem Microsoft Teams Yeoman Generator gehen. Es führt Sie auch durch den Prozess der Aktualisierung Ihrer Teams mit dem Yeoman-Generator. Voraussetzung für den Einstieg in dieses Tutorial ist, dass Sie über ein Teams Konto verfügen, das das [Sideloading](~/concepts/build-and-test/prepare-your-o365-tenant.md)von Apps ermöglicht.

![yeoman generator git](~/assets/yeoman-demo.gif)

## <a name="setup-and-prepare-your-machine"></a>Einrichten und Vorbereiten Ihrer Maschine

Sie müssen Folgendes auf Ihrem Computer installieren, bevor Sie mit der Verwendung des Yeoman-Generators beginnen.

### <a name="install-nodejs"></a>Installieren von Node.js

Sie müssen Node.js auf Ihrem Computer installiert haben. Sie sollten die neueste [LTS-Version](https://nodejs.org)verwenden.

### <a name="install-a-code-editor"></a>Installieren eines Code-Editors

Sie benötigen einen Code-Editor. Die meisten dieser Dokumentationen und Bilder beziehen sich auf die Verwendung [von Visual Studio Code](https://code.visualstudio.com). Sie können jedoch den gewünschten Texteditor verwenden.

### <a name="install-yeoman-and-gulp-cli"></a>Installieren von Yeoman und Gulp CLI

Um Gerüstprojekte mit dem Generator zu erstellen, müssen Sie das Yeoman-Tool und den Gulp CLI-Task-Manager installieren.

Öffnen Sie eine Eingabeaufforderung, und geben Sie Folgendes ein:

```bash
npm install yo gulp-cli --global
```

## <a name="install-the-generator"></a>Installieren des Generators

Installieren Sie den Teams Yeoman-Generator mit dem folgenden Befehl:

```bash
npm install generator-teams --global
```

Installieren Sie die Vorschauversion des Generators mit dem folgenden Befehl:

```bash
npm install generator-teams@preview --global
```

## <a name="generate-your-project"></a>Generieren Sie Ihr Projekt

In diesem Abschnitt werden die Schritte zum Generieren des Projekts erläutert.

**So generieren Sie Ihr Projekt**

1. Öffnen Sie eine Eingabeaufforderung, und erstellen Sie ein neues Verzeichnis, in dem Sie Ihr Projekt erstellen möchten, und führen Sie in diesem Verzeichnis den Befehl `yo teams` aus. Der Generator startet.
1. Beantworten Sie den Satz von Fragen, die vom Generator gestellt werden:

   ![yo-Teams](~/assets/yeoman-images/teams-first-app-1.png)

   1. Die erste Frage betrifft Ihren Projektnamen, Sie können ihn wie folgt belassen, indem Sie die Eingabetaste drücken.
   1. Die nächste Frage fragt Sie, ob Sie ein neues Verzeichnis erstellen oder das aktuelle verwenden möchten. Da Sie sich bereits in dem gewünschten Verzeichnis befinden, drücken Sie einfach die Eingabetaste.
   1. Geben Sie in der nächsten Frage den Titel Ihres Projekts ein. Dieser Titel wird im Manifest und in der Beschreibung Ihrer App verwendet. 
   1. Als Nächstes werden Sie nach einem Firmennamen gefragt, der auch im Manifest verwendet wird.
   1. In der fünften Frage werden Sie gefragt, welche Version des Manifests Sie verwenden möchten. Wählen Sie für dieses Tutorial `v1.5` aus, welches das aktuelle allgemeine verfügbare Schema ist.
   1. Als Nächstes fragt der Generator Sie nach den Elementen, die Sie Ihrem Projekt hinzufügen möchten. Sie können eine einzelne oder eine beliebige Kombination von Elementen auswählen. Wählen Sie für diese Tutorials einfach *eine Registerkarte* aus:

    ![Artikelauswahl](~/assets/yeoman-images/teams-first-app-2.png)

1. Antworten Sie auf den nächsten Satz von Folgefragen, die basierend auf den in Schritt 2 ausgewählten Elementen angezeigt werden.
1. Geben Sie eine URL ein, unter der Sie Ihre Lösung hosten möchten. 

   > [!NOTE]
   > Die URL kann eine beliebige URL sein, aber standardmäßig schlägt der Generator eine Azure-Website-URL vor.

1. Bestätigen Sie in der nächsten Frage, ob Sie Komponententests für Ihre Lösung einschließen möchten. Die Standardantwort lautet *yes*. Wenn Sie Komponententests einschließen, verfügt das generierte Projekt über ein Komponententestframework und einige Standardkomponententests für die verschiedenen Elemente, die auf Gerüsten erstellt werden. 
   > [!NOTE]
   > * Für dieses Tutorial sollten Sie kein Testframework enthalten.
   > * Der Generator hat viele integrierte erweiterte Funktionen, die Sie opt-in oder Opt-out können.

1. Um die Anmeldung für Sie zu vereinfachen, werden Sie auch gefragt, ob Sie Azure Application Insights für die Anmeldung verwenden möchten. Wenn Sie *Ja* wählen, müssen Sie einen Azure Application Insights-Schlüssel angeben. 

   > [!NOTE]
   > Für dieses Tutorial Opt-out der Verwendung von Application Insights.

Der nächste Fragensatz basiert auf den zuvor ausgewählten Elementen. Für eine Registerkarte müssen Sie nur einen Namen angeben und optional auswählen, ob Sie diese App als SharePoint Online-Webpart verwenden möchten. Nachdem Sie den Namen angeben, generiert der Generator das Projekt und installiert alle Abhängigkeiten. Dies dauert ein oder zwei Minuten.

## <a name="add-some-code-to-your-tab"></a>Hinzufügen von Code zu Ihrer Registerkarte

Nachdem der Generator fertig ist, können Sie die Lösung in Ihrem Lieblings-Code-Editor öffnen. Nehmen Sie sich ein oder zwei Minuten Zeit und machen Sie sich mit der Organisation des Codes vertraut. Weitere Informationen finden Sie in [Project Strukturdokumentation.](https://github.com/OfficeDev/generator-teams/wiki/Project-Structure)

Ihre Registerkarte befindet sich in der `./src/app/scripts/myFirstAppTab/MyFirstAppTab.tsx` Datei. Dies ist die TypeScript React-basierte Klasse für Ihre Registerkarte. Suchen Sie die `render()` Methode, und fügen Sie eine Codezeile innerhalb des Steuerelements hinzu, `<PanelBody>` damit sie wie folgt aussieht:

``` TypeScript
<PanelBody>
    <div style={styles.section}>
    Hello World! Yo Teams rocks!
    </div>
</PanelBody>
```

Speichern Sie die Datei, und kehren Sie zur Eingabeaufforderung zurück.

## <a name="build-your-app"></a>Erstellen Sie Ihre Anwendung

Sie können nun Ihr Projekt erstellen. Dies geschieht in zwei Schritten (oder in einem Schritt, siehe unten).

Zuerst müssen Sie die Teams App-Manifestdatei erstellen, die Sie in Microsoft Teams hochladen/sideloaden. Dies geschieht durch die Gulp-Aufgabe `gulp manifest` . Dadurch wird das Manifest überprüft und eine ZIP-Datei im `./package` Verzeichnis erstellt.

Zum Erstellen der Lösung verwenden Sie den `gulp build` Befehl. Dadurch wird Ihre Lösung in den `./dist` Ordner übertragen. 

## <a name="run-your-app"></a>Ausführen Ihrer App

Zum Ausführen Ihrer App verwenden Sie den `gulp serve` Befehl. Dadurch wird ein lokaler Webserver erstellt und gestartet, auf dem Sie Ihre App testen können. Der Befehl erstellt die Anwendung auch neu, wenn Sie eine Datei in Ihrem Projekt speichern. 

Sie sollten nun in der Lage `http://localhost:3007/myFirstAppTab/` sein, zu navigieren, um sicherzustellen, dass Ihre Registerkarte gerendert wird. Allerdings noch nicht in Microsoft Teams:

![Anzeigen Ihrer Website in einem Browser](~/assets/yeoman-images/teams-first-app-3.png)

## <a name="run-your-app-in-microsoft-teams"></a>Führen Sie Ihre App in Microsoft Teams

Microsoft Teams ermöglicht es Ihnen nicht, Ihre App auf localhost gehostet zu haben, daher müssen Sie sie entweder auf einer öffentlichen URL veröffentlichen oder einen Proxy wie ngrok verwenden.

Eine gute Nachricht ist, dass das Gerüstprojekt diese eingebaute hat. Wenn Sie `gulp ngrok-serve` den ngrok-Dienst ausführen, wird er im Hintergrund mit einem eindeutigen und öffentlichen DNS-Eintrag gestartet, und er wird auch das Manifest mit dieser eindeutigen URL verpacken und dann genau dasselbe wie `gulp serve` ausführen.

Erstellen Sie nach dem Ausführen ein neues Microsoft Teams Team, und klicken Sie `gulp ngrok-serve` bei der Erstellung auf den Teamnamen, um zu den Teameinstellungen zu wechseln, und wählen Sie dann *Apps* aus. In der unteren rechten Ecke sollten Sie einen Link *Hochladen einer benutzerdefinierten App* sehen, wählen Sie sie aus, und navigieren Sie dann zu Ihrem Projektordner und dem Unterordner mit dem Namen `package` . Wählen Sie die ZIP-Datei in diesem Ordner aus, und wählen Sie Öffnen aus. Ihre App wird jetzt in Microsoft Teams:

![Sideloaded-App](~/assets/yeoman-images/teams-first-app-4.png)

Kehren Sie zum *Allgemeinen* Kanal zurück und wählen Sie *+* eine neue Registerkarte hinzu. Sie sollten Ihre Registerkarte in der Liste der Registerkarten sehen:

![Registerkarte konfigurieren](~/assets/yeoman-images/teams-first-app-5.png)

Wählen Sie Ihre Registerkarte und folgen Sie den Anweisungen, um sie hinzuzufügen. Beachten Sie, dass Sie über ein benutzerdefiniertes Konfigurationsdialogfeld verfügen, für das Sie die Quelle bearbeiten können. Wählen Sie *Speichern* aus, um die Registerkarte zum Kanal hinzuzufügen. Sobald Sie fertig sind, sollte Ihre Registerkarte in Microsoft Teams geladen werden!

![Ausführen der Registerkarte in Teams](~/assets/yeoman-images/teams-first-app-6.png)

## <a name="upgrade-microsoft-teams"></a>Upgrade-Microsoft Teams

Sie können Auch Ihre aktuelle Microsoft Teams Version auf die neueste Version aktualisieren, indem Sie den Microsoft Teams Yeoman-Generator verwenden.

**So aktualisieren Sie Microsoft Teams**

1. Aktuelle Version von Teams mit dem folgenden Befehl abrufen:

   ```PowerShell
    yo teams --version
   ```
2. Verwenden Sie den folgenden Befehl, um Ihren Generator aktualisieren auszuwählen:

   ```PowerShell
    yo
   ```
3. Verwenden Sie die Pfeiltasten, um **Aktualisieren Sie Ihre Generatoren**:

   ![Bild von YoSelectUpdatGen](~/assets/images/Update-Teams/YoSelectUpdateGen.png)

4. Wählen Sie den gewünschten Generator aus der Liste der Generatoren aus:
   > [!NOTE]
   > Verwenden Sie die Leertaste, um eine ausgewählte Teams Version aus den verfügbaren Optionen auszuwählen oder zu löschen.

    ![Bild von UseSpaceToSelectGenerators](~/assets/images/Update-Teams/UseSpaceToSelectGenerators.png)
    

   > [!NOTE]
   > Es dauert einige Sekunden bis Minuten, bis Teams Installation abgeschlossen ist.

5. Nachdem die Installation abgeschlossen ist, verwenden Sie den folgenden Befehl, um die installierte Version zu überprüfen:

   ```PowerShell
    yo teams --version
   ```
   
**Congrats! Sie haben Ihre erste Microsoft Teams-App erstellt und bereitgestellt. Sie haben auch Microsoft Teams aktualisiert.**
