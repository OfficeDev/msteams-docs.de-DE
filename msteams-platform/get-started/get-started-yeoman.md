---
title: Lernprogramm – Erstellen Ihrer ersten App mithilfe des Yeoman-Generators
description: Erfahren Sie, wie Sie mit dem Yeoman-Generator mit dem Erstellen Microsoft Teams Apps beginnen.
keywords: Erste Schritte node.js nodejs yeoman
ms.localizationpriority: medium
ms.topic: tutorial
ms.custom: scenarios:getting-started
ms.openlocfilehash: 90bd997de1e5bbfc92e366d466c156f052cbe3bf
ms.sourcegitcommit: fc9f906ea1316028d85b41959980b81f2c23ef2f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2021
ms.locfileid: "59156530"
---
# <a name="build-your-first-microsoft-teams-app-using-the-yeoman-generator"></a>Erstellen Ihrer ersten Microsoft Teams-App mithilfe des Yeoman-Generators

> [!Note]
> Dieses Lernprogramm stammt aus dem [Yeoman-Generator für Teams Wiki.](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App)

In diesem Lernprogramm erfahren Sie, wie Sie Ihre erste Microsoft Teams-App mit dem Microsoft Teams Yeoman-Generator erstellen. Außerdem werden Sie durch den Prozess des Upgradens Ihrer Teams mithilfe des Yeoman-Generators führt. Bevor Sie beginnen, benötigen Sie ein Teams Konto, das das [Querladen von Apps](~/concepts/build-and-test/prepare-your-o365-tenant.md)ermöglicht.

![Git des Yeoman-Generators](~/assets/yeoman-demo.gif)

[!include [prepare your environment](~/includes/prepare-environment.md)]

<a name="GetPrerequisites"></a>

## <a name="get-prerequisites"></a>Voraussetzungen abrufen

Sie müssen Folgendes auf Ihrem Computer installieren, bevor Sie mit der Verwendung des Yeoman-Generators beginnen:

* Node.js

   Sie müssen Node.js auf Ihrem Computer installiert haben. Sie sollten die neueste [LTS-Version](https://nodejs.org)verwenden.

* Ein Code-Editor

   Sie benötigen einen Code-Editor. Die meisten dieser Dokumentationen und Bilder beziehen sich auf die Verwendung [Visual Studio Code](https://code.visualstudio.com). Sie können jedoch den gewünschten Text-Editor verwenden.

* Yeoman und Gulp CLI

   Zum Erstellen eines Gerüsts für Projekte mithilfe des Generators müssen Sie das Yeoman-Tool und den Gulp CLI-Task-Manager installieren.

   Öffnen Sie eine Eingabeaufforderung, und geben Sie Folgendes ein:

   ```bash
   npm install yo gulp-cli --global
   ```

## <a name="install-the-generator"></a>Installieren des Generators

Installieren Sie den Teams Yeoman-Generator mit dem folgenden Befehl:

```bash
npm init yo teams
```

Installieren Sie die Vorschauversion des Generators mit dem folgenden Befehl:

```bash
npm init yo teams@preview
```

## <a name="generate-your-project"></a>Generieren Ihres Projekts

In diesem Abschnitt werden Sie durch die Schritte zum Generieren Ihres Projekts geführt.

**So generieren Sie Ihr Projekt**

1. Öffnen Sie eine Eingabeaufforderung, und erstellen Sie ein neues Verzeichnis, in dem Sie Ihr Projekt erstellen möchten.
1. Wechseln Sie zum Verzeichnis, und führen Sie den Befehl `yo teams` aus. Der Generator wird gestartet.
1. Antworten Sie auf die Fragen, die vom Generator gestellt werden:

   ![Yo Teams](~/assets/yeoman-images/teams-first-app-1.png)

   1. Geben Sie einen Namen für Ihr Projekt ein. Sie können es wie belassen, indem Sie die EINGABETASTE drücken.
   1. Geben Sie einen Pfad für das neue Verzeichnis ein, wenn Sie ein neues Verzeichnis erstellen möchten. Da Sie sich bereits im gewünschten Verzeichnis befinden, drücken Sie einfach die EINGABETASTE.
   1. Geben Sie den Titel Ihres Projekts ein. Dieser Titel wird im Manifest und in der Beschreibung Ihrer App verwendet. 
   1. Geben Sie einen Firmennamen ein, der auch im Manifest verwendet wird.
   1. Geben Sie die Version des Manifests ein, das Sie verwenden möchten. Wählen Sie für dieses Lernprogramm `v1.5` das aktuelle allgemein verfügbare Schema aus.
   1. Wählen Sie die Elemente aus, die Sie Ihrem Projekt hinzufügen möchten. Sie können eine einzelne oder eine beliebige Kombination von Elementen auswählen. Wählen Sie für dieses Lernprogramm einfach *eine Registerkarte* aus:

    ![Elementauswahl](~/assets/yeoman-images/teams-first-app-2.png)

1. Antworten Sie auf die nächsten Folgefragen, die basierend auf den in Schritt 3 ausgewählten Elementen angezeigt werden.
1. Geben Sie eine URL für den Speicherort ein, an dem Sie Ihre Lösung hosten möchten. 

   > [!NOTE]
   > Die URL kann eine beliebige URL sein, aber standardmäßig schlägt der Generator eine Azure-Website-URL vor.

1. Vergewissern Sie sich, dass Sie Komponententests für Ihre Lösung einschließen möchten. Die Standardantwort lautet **Ja**. Wenn Sie sich dafür entscheiden, Komponententests einzubeziehen, verfügt das generierte Projekt über ein Komponententestframework und einige Standardeinheitstests für die verschiedenen Elemente, die ein Gerüst erstellen. 
   > [!NOTE]
   > * Wählen Sie für dieses Lernprogramm, kein Testframework einzuschließen.
   > * Der Generator verfügt über viele integrierte erweiterte Features, von denen Sie sich anmelden oder abmelden können.

1. Um ihnen die Anmeldung zu erleichtern, werden Sie auch gefragt, ob Sie Azure Application Insights für die Anmeldung verwenden möchten. Wenn Sie **"Ja"** auswählen, müssen Sie einen Azure-Anwendungsschlüssel Insights bereitstellen. 

   > [!NOTE]
   > In diesem Lernprogramm wird die Verwendung von Anwendungs-Insights abgemeldet.

   Die nächsten Fragen basieren auf den zuvor ausgewählten Elementen. Für eine Registerkarte müssen Sie nur einen Namen angeben und optional auswählen, ob Sie diese App als SharePoint Online-Webpart verwenden möchten. Nachdem Sie den Namen angegeben haben, generiert der Generator das Projekt und installiert alle Abhängigkeiten. Dies dauert ein oder zwei Minuten.

## <a name="add-code-to-your-tab"></a>Hinzufügen von Code zu Ihrer Registerkarte

Nach Abschluss des Generators können Sie die Lösung in Ihrem bevorzugten Code-Editor öffnen. Nehmen Sie sich ein oder zwei Minuten Zeit, und machen Sie sich mit der Organisation des Codes vertraut. Weitere Informationen finden Sie in [Project Strukturdokumentation.](https://github.com/OfficeDev/generator-teams/wiki/Project-Structure)

Ihre Registerkarte befindet sich in der `./src/app/scripts/myFirstAppTab/MyFirstAppTab.tsx` Datei. Dies ist die TypeScript-React-basierte Klasse für Ihre Registerkarte. 

1. Suchen Sie die `render()` Methode, und fügen Sie eine Codezeile innerhalb des `<PanelBody>` Steuerelements hinzu, damit sie wie folgt aussieht:

   ``` TypeScript
   <PanelBody>
      <div style={styles.section}>
      Hello World! Yo Teams rocks!
      </div>
   </PanelBody>
   ```
1. Speichern Sie die Datei, und kehren Sie zur Eingabeaufforderung zurück.

## <a name="build-your-app"></a>Erstellen Sie Ihre Anwendung

Sie können nun Ihr Projekt erstellen. Dies erfolgt in zwei Schritten.

1. Erstellen Sie die Teams App-Manifestdatei für die App, die Sie in Microsoft Teams hochgeladen haben. Dies geschieht durch die Gulp-Aufgabe. `gulp manifest` Dadurch wird das Manifest überprüft und eine ZIP-Datei im `./package` Verzeichnis erstellt.
1. Führen Sie den `gulp build` Befehl aus, um die Lösung zu erstellen. Dadurch wird Ihre Lösung in den `./dist` Ordner transpiliert. 

## <a name="run-your-app"></a>Ausführen Ihrer App

Verwenden Sie den Befehl, um Ihre App `gulp serve` auszuführen. Dadurch wird ein lokaler Webserver erstellt und gestartet, auf dem Sie Ihre App testen können. Der Befehl erstellt die Anwendung auch neu, wenn Sie eine Datei in Ihrem Projekt speichern. 

Jetzt sollten Sie zu der Registerkarte wechseln `http://localhost:3007/myFirstAppTab/` und sicherstellen, dass sie gerendert wird. Sie befindet sich jedoch noch nicht in Microsoft Teams. 

**So rendern Sie die Registerkarte in Microsoft Teams**

![Anzeigen Ihrer Website in einem Browser](~/assets/yeoman-images/teams-first-app-3.png)

### <a name="run-your-app-in-microsoft-teams"></a>Ausführen Ihrer App in Microsoft Teams

Microsoft Teams nicht zulässt, dass Ihre App auf localhost gehostet wird. Daher müssen Sie sie entweder unter einer öffentlichen URL veröffentlichen oder einen Proxy wie z. B. ngrok verwenden. Eine gute Nachricht ist, dass das Gerüstprojekt über dieses integrierte Projekt verfügt. 

**So führen Sie Ihre App in Teams**

1. Wird `gulp ngrok-serve` in Terminal ausgeführt. Wenn Sie `gulp ngrok-serve` den ngrok-Dienst ausführen, wird er im Hintergrund mit einem eindeutigen und öffentlichen DNS-Eintrag gestartet. Außerdem wird das Manifest mit dieser eindeutigen URL verpackt und dann genau dasselbe ausgeführt wie `gulp serve` .
1. Erstellen Sie ein neues Microsoft Teams Team.
1. Wählen Sie den Teamnamen > Teams Einstellungen > Apps aus.
1. Wählen Sie in der unteren rechten Ecke **Hochladen einer benutzerdefinierten App** aus.
1. Wechseln Sie zum `package` Ordner unter Ihrem Projektordner. 
1. Wählen Sie die ZIP-Datei in diesem Ordner aus, und wählen Sie "Öffnen" aus. 
   Ihre App wird nun in Microsoft Teams quergeladen:

   ![Quergeladene App](~/assets/yeoman-images/teams-first-app-4.png)
1. Wechseln Sie zurück zum Kanal **"Allgemein",** und wählen Sie **+** aus, um eine neue Registerkarte hinzuzufügen. Die Registerkarte sollte in der Liste der Registerkarten angezeigt werden: ![ Registerkarte konfigurieren](~/assets/yeoman-images/teams-first-app-5.png)
1. Wählen Sie Ihre Registerkarte aus, und folgen Sie den Anweisungen, um sie hinzuzufügen. Beachten Sie, dass Sie über ein benutzerdefiniertes Konfigurationsdialogfeld verfügen, für das Sie die Quelle bearbeiten können. Wählen Sie *"Speichern"* aus, um ihre Registerkarte zum Kanal hinzuzufügen. Ihre Registerkarte wird jetzt in Microsoft Teams geladen!

   ![Registerkarte "Ausführen" in Teams](~/assets/yeoman-images/teams-first-app-6.png)

### <a name="upgrade-microsoft-teams"></a>Upgrade Microsoft Teams

Sie können ihre aktuelle Microsoft Teams Version auch mit dem Microsoft Teams Yeoman-Generator auf die neueste Version aktualisieren.

**So aktualisieren Sie Microsoft Teams**

1. Rufen Sie die aktuelle Version von Teams mit dem folgenden Befehl ab:

   ```PowerShell
    yo teams --version
   ```
2. Verwenden Sie den folgenden Befehl, um ihren Generator auszuwählen und zu aktualisieren:

   ```PowerShell
    yo
   ```
3. Verwenden Sie die Pfeiltasten, um **"Generatoren aktualisieren"** auszuwählen:

   ![Abbildung von YoSelectUpdatGen](~/assets/images/Update-Teams/YoSelectUpdateGen.png)

4. Wählen Sie den gewünschten Generator aus der Liste der Generatoren aus:
   > [!NOTE]
   > Verwenden Sie die Leertaste, um eine ausgewählte Teams Version aus den verfügbaren Optionen auszuwählen oder zu löschen.

    ![Abbildung von UseSpaceToSelectGenerators](~/assets/images/Update-Teams/UseSpaceToSelectGenerators.png)
    

   > [!NOTE]
   > Es dauert einige Sekunden bis Minuten, bis Teams Installation abgeschlossen ist.

5. Verwenden Sie nach Abschluss der Installation den folgenden Befehl, um die installierte Version zu überprüfen:

   ```PowerShell
    yo teams --version
   ```
   Congrats! Sie haben Ihre erste Microsoft Teams App erstellt und bereitgestellt. Sie haben auch Microsoft Teams aktualisiert.

 ## <a name="see-also"></a>Siehe auch

* [Übersicht über Lernprogramme](code-samples.md)
* [Erstellen einer Unterhaltungs-Bot-App](first-app-bot.md)
* [Erstellen einer Messaging-Erweiterung](first-message-extension.md)
* [Codebeispiele](https://github.com/OfficeDev/Microsoft-Teams-Samples)
