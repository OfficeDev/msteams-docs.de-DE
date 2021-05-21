---
title: Lernprogramm – Erstellen Ihrer ersten App mithilfe des Yeoman-Generators
description: Erfahren Sie, wie Sie mit dem Microsoft Teams Erstellen von Apps beginnen.
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
# <a name="create-your-first-microsoft-teams-app-using-the-yeoman-generator"></a>Erstellen Ihrer ersten Microsoft Teams-App mithilfe des Yeoman-Generators

> [!Note]
> Dieses Lernprogramm stammt aus dem [Yeoman-Generator für Teams Wiki.](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App)

In diesem Lernprogramm werden wir durch das Erstellen Ihrer ersten Microsoft Teams-App mithilfe des Microsoft Teams Yeoman-Generators gehen. Außerdem werden Sie durch den Prozess des Upgrades Ihrer Teams mithilfe des Yeoman-Generators führt. Die Voraussetzung für den Einstieg in dieses Lernprogramm ist, dass Sie über ein Teams verfügen, das das Querladen von Apps [zulässt.](~/concepts/build-and-test/prepare-your-o365-tenant.md)

![yeoman generator git](~/assets/yeoman-demo.gif)

## <a name="setup-and-prepare-your-machine"></a>Einrichten und Vorbereiten des Computers

Sie müssen Folgendes auf Ihrem Computer installieren, bevor Sie mit der Verwendung des Yeoman-Generators beginnen.

### <a name="install-nodejs"></a>Installieren von Node.js

Sie müssen Node.js auf Ihrem Computer installiert haben. Sie sollten die neueste [LTS-Version verwenden.](https://nodejs.org)

### <a name="install-a-code-editor"></a>Installieren eines Code-Editors

Sie benötigen einen Code-Editor. Die meisten dieser Dokumentationen und Bilder beziehen sich auf die Verwendung [Visual Studio Code](https://code.visualstudio.com). Sie können jedoch den von Ihnen bevorzugten Texteditor verwenden.

### <a name="install-yeoman-and-gulp-cli"></a>Installieren von Yeoman und Gulp CLI

Zum Gerüsten von Projekten mithilfe des Generators müssen Sie das Yeoman-Tool und den Gulp CLI-Task-Manager installieren.

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

## <a name="generate-your-project"></a>Generieren Ihres Projekts

Dieser Abschnitt führt Sie durch die Schritte zum Generieren Ihres Projekts.

**So generieren Sie Ihr Projekt**

1. Öffnen Sie eine Eingabeaufforderung, und erstellen Sie ein neues Verzeichnis, in dem Sie Ihr Projekt erstellen möchten, und führen Sie in diesem Verzeichnis den Befehl `yo teams` aus. Der Generator wird gestartet.
1. Antworten Sie auf die Fragen, die vom Generator gestellt werden:

   ![yo teams](~/assets/yeoman-images/teams-first-app-1.png)

   1. Die erste Frage ist ihr Projektname. Sie können ihn so be lassen, wie durch Drücken der EINGABETASTE.
   1. In der nächsten Frage werden Sie gefragt, ob Sie ein neues Verzeichnis erstellen oder das aktuelle Verzeichnis verwenden möchten. Drücken Sie einfach die EINGABETASTE, da Sie sich bereits im verzeichnis befinden, das Sie möchten.
   1. Geben Sie in der nächsten Frage den Titel Ihres Projekts ein. Dieser Titel wird im Manifest und in der Beschreibung Ihrer App verwendet. 
   1. Als Nächstes werden Sie nach einem Firmennamen gefragt, der auch im Manifest verwendet wird.
   1. In der fünften Frage werden Sie gefragt, welche Version des Manifests Sie verwenden möchten. Wählen Sie für dieses `v1.5` Lernprogramm die Option aus, die das aktuelle allgemeine verfügbare Schema ist.
   1. Als Nächstes fragt der Generator Sie nach den Elementen, die Sie Ihrem Projekt hinzufügen möchten. Sie können eine einzelne oder eine beliebige Kombination von Elementen auswählen. Wählen Sie für diese Lernprogramme einfach *eine Registerkarte aus:*

    ![Elementauswahl](~/assets/yeoman-images/teams-first-app-2.png)

1. Beantworten Sie die nächsten Folgefragen, die basierend auf den in Schritt 2 ausgewählten Elementen angezeigt werden.
1. Geben Sie eine URL ein, in der Sie Ihre Lösung hosten. 

   > [!NOTE]
   > Die URL kann eine beliebige URL sein, aber standardmäßig schlägt der Generator eine Azure-Website-URL vor.

1. Bestätigen Sie in der nächsten Frage, ob Sie Komponententests für Ihre Lösung enthalten möchten. Die Standardantwort ist *Ja*. Wenn Sie Komponententests verwenden möchten, verfügt das generierte Projekt über ein Komponententestframework und einige Standardeinheitstests für die verschiedenen Elemente, die gerüstet werden. 
   > [!NOTE]
   > * Wählen Sie für dieses Lernprogramm aus, kein Testframework zu enthalten.
   > * Der Generator verfügt über eine Menge integrierter erweiterter Features, für die Sie sich abmelden oder abmelden können.

1. Um die Anmeldung für Sie zu einfach zu machen, werden Sie auch gefragt, ob Sie Azure Application Insights für die Anmeldung verwenden möchten. Wenn Sie Ja *auswählen,* müssen Sie einen Azure Application Insights-Schlüssel bereitstellen. 

   > [!NOTE]
   > Für dieses Lernprogramm wird die Verwendung von Application Insights nicht mehr verwendet.

Der nächste Fragensatz basiert auf den zuvor ausgewählten Elementen. Für eine Registerkarte müssen Sie nur einen Namen eingeben und optional auswählen, ob Sie diese App als SharePoint Online-Web part verwenden möchten. Nachdem Sie den Namen zur Verfügung stellen, generiert der Generator das Projekt und installiert alle Abhängigkeiten. Dies dauert ein bis zwei Minuten.

## <a name="add-some-code-to-your-tab"></a>Hinzufügen von Code zu Ihrer Registerkarte

Nachdem der Generator fertig ist, können Sie die Lösung in Ihrem bevorzugten Code-Editor öffnen. Nehmen Sie sich ein oder zwei Minuten Zeit, und machen Sie sich mit der Organisation des Codes vertraut. Weitere Informationen finden Sie unter [Project Strukturdokumentation.](https://github.com/OfficeDev/generator-teams/wiki/Project-Structure)

Ihre Registerkarte befindet sich in der `./src/app/scripts/myFirstAppTab/MyFirstAppTab.tsx` Datei. Dies ist die typeScript React-basierte Klasse für Ihre Registerkarte. Suchen Sie die Methode, und fügen Sie eine Codezeile innerhalb des Steuerelements `render()` `<PanelBody>` hinzu, sodass sie wie dies aussieht:

``` TypeScript
<PanelBody>
    <div style={styles.section}>
    Hello World! Yo Teams rocks!
    </div>
</PanelBody>
```

Speichern Sie die Datei, und kehren Sie zur Eingabeaufforderung zurück.

## <a name="build-your-app"></a>Erstellen Sie Ihre Anwendung

Sie können jetzt Ihr Projekt erstellen. Dies erfolgt in zwei Schritten (oder in einem Schritt, siehe unten).

Zuerst müssen Sie die Teams-App-Manifestdatei erstellen, die Sie hochladen/querladen in Microsoft Teams. Dies wird von der Gulp-Aufgabe `gulp manifest` ausgeführt. Dadurch wird das Manifest überprüft und eine ZIP-Datei im Verzeichnis `./package` erstellt.

Verwenden Sie den Befehl, um Ihre Lösung zu `gulp build` erstellen. Dadurch wird Die Lösung in den Ordner `./dist` transpiliert. 

## <a name="run-your-app"></a>Ausführen Ihrer App

Verwenden Sie den Befehl, um Ihre App `gulp serve` auszuführen. Dadurch erstellen und starten Sie einen lokalen Webserver, auf dem Sie Ihre App testen können. Der Befehl erstellt die Anwendung auch neu, wenn Sie eine Datei in Ihrem Projekt speichern. 

Sie sollten nun in der Lage sein, zu `http://localhost:3007/myFirstAppTab/` navigieren, um sicherzustellen, dass Ihre Registerkarte gerendert wird. Allerdings noch nicht in Microsoft Teams:

![Anzeigen Ihrer Website in einem Browser](~/assets/yeoman-images/teams-first-app-3.png)

## <a name="run-your-app-in-microsoft-teams"></a>Führen Sie Ihre App in Microsoft Teams

Microsoft Teams sie nicht zulassen, dass Ihre App auf localhost gehostet wird, müssen Sie sie also entweder in einer öffentlichen URL veröffentlichen oder einen Proxy wie ngrok verwenden.

Eine gute Nachricht ist, dass das Gerüstprojekt über dieses integrierte Projekt verfügt. Wenn Sie den ngrok-Dienst ausführen, wird er im Hintergrund gestartet, mit einem eindeutigen und öffentlichen DNS-Eintrag, und er verpackt das Manifest auch mit dieser eindeutigen URL und macht dann genau dasselbe `gulp ngrok-serve` wie `gulp serve` .

Erstellen Sie nach der Ausführung ein neues Microsoft Teams Team, und klicken Sie beim Erstellen auf den Teamnamen, um zu den Teams-Einstellungen zu wechseln und `gulp ngrok-serve` dann *Apps auszuwählen.* In der unteren rechten Ecke sollte ein Link Hochladen einer benutzerdefinierten App angezeigt *werden,* wählen Sie ihn aus, und navigieren Sie dann zu Ihrem Projektordner und dem Unterordner namens `package` . Wählen Sie die ZIP-Datei in diesem Ordner aus, und wählen Sie öffnen aus. Ihre App wird nun in die Microsoft Teams:

![seitegeladene App](~/assets/yeoman-images/teams-first-app-4.png)

Wechseln Sie zurück zum *Kanal Allgemein,* und wählen *+* Sie aus, um eine neue Registerkarte hinzuzufügen. Ihre Registerkarte sollte in der Liste der Registerkarten angezeigt werden:

![Registerkarte konfigurieren](~/assets/yeoman-images/teams-first-app-5.png)

Wählen Sie Ihre Registerkarte aus, und befolgen Sie die Anweisungen, um sie hinzuzufügen. Beachten Sie, dass Sie über ein benutzerdefiniertes Konfigurationsdialogfeld verfügen, für das Sie die Quelle bearbeiten können. Wählen *Sie Speichern* aus, um ihre Registerkarte zum Kanal hinzuzufügen. Sobald Sie fertig sind, sollte Ihre Registerkarte innerhalb des Microsoft Teams!

![Ausführen der Registerkarte in Teams](~/assets/yeoman-images/teams-first-app-6.png)

## <a name="upgrade-microsoft-teams"></a>Upgrade Microsoft Teams

Sie können ihre aktuelle Microsoft Teams auch mithilfe des Microsoft Teams Yeoman-Generators auf die neueste Version aktualisieren.

**So aktualisieren Microsoft Teams**

1. Mit dem folgenden Befehl Teams aktuelle Version der Version des Befehls:

   ```PowerShell
    yo teams --version
   ```
2. Verwenden Sie den folgenden Befehl, um den Generator zu aktualisieren:

   ```PowerShell
    yo
   ```
3. Verwenden Sie die Pfeiltasten, um **Ihre Generatoren aktualisieren zu wählen:**

   ![Bild von YoSelectUpdatGen](~/assets/images/Update-Teams/YoSelectUpdateGen.png)

4. Wählen Sie den generator aus der Liste der Generatoren aus:
   > [!NOTE]
   > Verwenden Sie die Leerraumleiste, um eine ausgewählte Teams aus den verfügbaren Optionen auszuwählen oder zu löschen.

    ![Abbildung von UseSpaceToSelectGenerators](~/assets/images/Update-Teams/UseSpaceToSelectGenerators.png)
    

   > [!NOTE]
   > Es dauert einige Sekunden bis Minuten, Teams installation abgeschlossen ist.

5. Verwenden Sie nach Abschluss der Installation den folgenden Befehl, um die installierte Version zu überprüfen:

   ```PowerShell
    yo teams --version
   ```
   
**Congrat! Sie haben Ihre erste App Microsoft Teams bereitgestellt. Sie haben auch ein Microsoft Teams.**
