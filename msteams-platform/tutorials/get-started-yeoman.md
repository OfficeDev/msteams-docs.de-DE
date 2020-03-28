---
title: Erste Schritte mit dem Landarbeits Generator für Microsoft Teams
description: Erste Schritte beim Erstellen von tollen apps mit dem Landwirtschafts Generator für Microsoft Teams
keywords: Erste Schritte Node. js nodejs
ms.topic: tutorial
ms.custom: scenarios:getting-started
ms.openlocfilehash: 217c0900e067a61e083e7ffb0b121afdaa51c49f
ms.sourcegitcommit: b13b38a104946c32cd5245a7af706070e534927d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/28/2020
ms.locfileid: "43034043"
---
# <a name="build-your-first-microsoft-teams-app"></a>Erstellen Ihrer ersten Microsoft Teams-App

>[!Note]
>Dieses Lernprogramm stammt aus dem wiki "landkraft- [Generator für Microsoft Teams](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App) "

In diesem Tutorial werden wir durch das Erstellen Ihrer ersten Microsoft Teams-App mithilfe des Microsoft Teams-Landarbeits-Generators gehen. Es wird davon ausgegangen, dass Sie das [Laden von Microsoft Teams-apps aktiviert](~/concepts/build-and-test/prepare-your-o365-tenant.md)haben.

![git-Generator](~/assets/yeoman-demo.gif)

## <a name="setup-and-prepare-your-machine"></a>Einrichten und Vorbereiten des Computers

Sie müssen Folgendes auf Ihrem Computer installieren, bevor Sie mit der Verwendung des Teams-Generators beginnen.

### <a name="install-node"></a>Installations Knoten

Sie müssen NodeJS auf Ihrem Computer installiert haben. Sie sollten die neueste [LTS-Version](https://nodejs.org/dist/latest-v8.x/)verwenden.

### <a name="install-a-code-editor"></a>Installieren eines Code-Editors

Sie benötigen auch einen Code-Editor, können jederzeit den von Ihnen bevorzugten Texteditor verwenden. Die meisten dieser Dokumentationen und Screenshots bezieht sich jedoch auf die Verwendung [Visual Studios Codes](https://code.visualstudio.com).

### <a name="install-yeoman-and-gulp-cli"></a>Installieren von "Autobauer" und "Schluck" CLI

Um ein Gerüst von Projekten mit dem Teams-Generator erstellen zu können, müssen Sie das Tool "Tools" sowie den "Schluck CLI-Task-Manager" installieren.

Öffnen Sie eine Eingabeaufforderung, und geben Sie Folgendes ein:

```bash
npm install yo gulp-cli --global
```

## <a name="install-the-microsoft-teams-apps-generator---yo-teams"></a>Installieren der Microsoft Teams-apps-Generator-Yo-Teams

Der Befehl "landkraft-Generator für Microsoft Teams-Apps" wird mit dem folgenden Befehl installiert:

```bash
npm install generator-teams --global
```

#### <a name="install-preview-versions"></a>Installieren von Vorschauversionen

Wenn Sie mit dem folgenden Befehl Vorschauversionen des Teams-Generators installieren möchten:

```bash
npm install generator-teams@preview --global
```

## <a name="generate-your-project"></a>Erstellen des Projekts

Öffnen Sie eine Eingabeaufforderung, und erstellen Sie ein neues Verzeichnis, in dem Sie Ihr Projekt erstellen möchten, und geben Sie `yo teams`in diesem Verzeichnis den Befehl ein. Dadurch wird der Microsoft Teams-apps-Generator gestartet, und Sie werden eine Reihe von Fragen gestellt.

![Yo Teams](~/assets/yeoman-images/teams-first-app-1.png)

Bei der ersten Frage geht es um Ihren Projektnamen, und Sie können ihn unverändert lassen, indem Sie die EINGABETASTE drücken. In der nächsten Frage werden Sie gefragt, ob Sie ein neues Verzeichnis erstellen oder die aktuelle verwenden möchten. Da wir uns bereits im gewünschten Verzeichnis befinden, drücken Sie einfach die EINGABETASTE.

Im folgenden Schritt wird nach einem Titel Ihres Projekts gefragt, dieser Titel wird im Manifest und in der Beschreibung Ihrer APP verwendet. Anschließend werden Sie nach einem Firmennamen gefragt, der auch im Manifest verwendet wird.

In der fünften Frage werden Sie gefragt, welche Version des Manifests Sie verwenden möchten. Wählen Sie `v1.5`für dieses Lernprogramm das aktuelle allgemein verfügbare Schema aus.

Anschließend werden Sie vom Generator gefragt, welche Elemente dem Projekt hinzugefügt werden sollen. Sie können eine einzelne oder eine beliebige Kombination von Elementen auswählen. Wählen Sie im Moment einfach *eine Registerkarte*aus.

![Elementauswahl](~/assets/yeoman-images/teams-first-app-2.png)

Basierend auf den ausgewählten Elementen werden Sie aufgefordert, eine Reihe von weiteren Fragen zu beantworten.

Jetzt müssen Sie eine URL eingeben, von der aus Sie Ihre Lösung hosten werden. Hierbei kann es sich um eine beliebige URL handeln, standardmäßig schlägt der Generator jedoch eine Azure-Websites-URL vor.

Der Generator verfügt über eine Vielzahl integrierter erweiterter Funktionen, die Sie aktivieren oder deaktivieren können. Nach der URL-Frage werden Sie gefragt, ob Sie Komponententests für Ihre Lösung einschließen möchten, Standard ist ja. Wenn Sie dies auswählen, verfügt das generierte Projekt über ein Komponententestframework und einige Standardkomponenten Tests für die unterschiedlichen Elemente, die als Gerüstbau verwendet werden. Wählen Sie für dieses Lernprogramm nicht ein Test Framework einschließen aus.

Um die Protokollierung für Sie zu vereinfachen, werden Sie auch gefragt, ob Sie Azure-Anwendungs Einblicke für die Protokollierung verwenden möchten. Wenn Sie Ja auswählen, müssen Sie einen Azure Application Insights-Schlüssel bereitstellen. Für dieses Lernprogramm Opt-out der Verwendung von Application Insights.

Die nächste Gruppe von Fragen basiert auf Ihrer Auswahl von Elementen, die zuvor verwendet wurden. Für eine Registerkarte müssen Sie nur einen Namen angeben und optional auswählen, ob Sie diese APP als SharePoint Online Webpart verwenden können möchten. Nachdem Sie diesen Namen angegeben haben, wird der Generator das Projekt generieren und alle Abhängigkeiten installieren. Dies dauert ein oder zwei Minuten.

## <a name="add-some-code-to-your-tab"></a>Hinzufügen von Code zu ihrer Registerkarte

Sobald der Generator fertig ist, können Sie die Lösung in Ihrem bevorzugten Code-Editor öffnen. Nehmen Sie sich ein oder zwei Minuten und machen Sie sich mit der Organisation des Codes vertraut – Sie können mehr darüber in der Dokumentation zur [Projektstruktur](https://github.com/OfficeDev/generator-teams/wiki/Project-Structure) lesen.

Die Registerkarte befindet sich in der `./src/app/scripts/myFirstAppTab/MyFirstAppTab.tsx` Datei. Dies ist die auf der Registerkarte basierende Reaktions basierte Klasse. suchen `render()` Sie die-Methode, und fügen Sie eine `<PanelBody>` Codezeile innerhalb des Steuerelements, sodass es wie folgt aussieht:

``` TypeScript
<PanelBody>
    <div style={styles.section}>
    Hello World! Yo Teams rocks!
    </div>
</PanelBody>
```

Speichern Sie die Datei, und kehren Sie zur Eingabeaufforderung zurück.

## <a name="build-your-app"></a>Erstellen Sie Ihre Anwendung

Sie können nun Ihr Projekt erstellen. Dies erfolgt in zwei Schritten (oder einem Schritt, siehe unten).

Zunächst müssen Sie die Teams-App-Manifestdatei erstellen, die Sie in Microsoft Teams hochladen/querladen. Dies erfolgt durch die Aufgabe `gulp manifest`"schlucken". Dadurch wird das Manifest überprüft und eine ZIP-Datei im `./package` Verzeichnis erstellt.

Verwenden Sie zum Erstellen der Lösung den `gulp build` Befehl. Dadurch wird die Lösung in den `./dist` Ordner transstapeln. 

## <a name="run-your-app"></a>Ausführen der APP

Zum Ausführen der App verwenden Sie den `gulp serve` Befehl. Dadurch wird ein lokaler Webserver erstellt und gestartet, damit Sie Ihre APP testen können. Mit dem Befehl wird die Anwendung auch dann neu erstellt, wenn Sie eine Datei im Projekt speichern. 

Sie sollten jetzt in der Lage sein, `http://localhost:3007/myFirstAppTab/` zu navigieren, um sicherzustellen, dass Ihre Registerkarte gerendert wird. Jedoch noch nicht in Microsoft Teams.

![Anzeigen Ihrer Website in einem Browser](~/assets/yeoman-images/teams-first-app-3.png)

## <a name="run-your-app-in-microsoft-teams"></a>Ausführen ihrer app in Microsoft Teams

Microsoft Teams lässt nicht zu, dass Ihre APP auf localhost gehostet wird, daher müssen Sie Sie entweder in einer öffentlichen URL veröffentlichen oder einen Proxy wie ngrok verwenden.

Eine gute Nachricht ist, dass das Gerüst Projekt diese integrierte ist. Wenn Sie den `gulp ngrok-serve` ngrok-Dienst ausführen, wird im Hintergrund mit einem eindeutigen und öffentlichen DNS-Eintrag gestartet, und es wird auch das Manifest mit dieser eindeutigen URL Verpacken und dann genau dasselbe tun wie `gulp serve`.

Erstellen Sie `gulp ngrok-serve`nach dem Starten ein neues Microsoft Teams-Team, und klicken Sie bei der Erstellung auf den Namen des Teams, um zu den Teams-Einstellungen zu wechseln, und wählen Sie dann *apps*aus. In der unteren rechten Ecke sehen Sie einen Link zum *Hochladen einer benutzerdefinierten App*, wählen Sie Sie aus, und navigieren Sie dann zu Ihrem Projekt `package`Ordner und dem Unterordner mit dem Namen. Wählen Sie die ZIP-Datei in diesem Ordner aus, und wählen Sie öffnen aus. Ihre APP wird nun in Microsoft Teams quer geladene.

![quer geladene-App](~/assets/yeoman-images/teams-first-app-4.png)

Wechseln Sie zurück zum Kanal *Allgemein* , und *+* wählen Sie aus, um eine neue Registerkarte hinzuzufügen. Die Registerkarte sollte in der Liste der Registerkarten angezeigt werden.

![Registerkarte "Konfigurieren"](~/assets/yeoman-images/teams-first-app-5.png)

Klicken Sie auf die Registerkarte, und folgen Sie den Anweisungen zum Hinzufügen. Beachten Sie, dass Sie über ein benutzerdefiniertes Konfigurationsdialogfeld verfügen, in dem Sie die Quelle bearbeiten können. Wählen Sie *Speichern* aus, um die Registerkarte dem Kanal hinzuzufügen. Wenn die Registerkarte fertig ist, sollte Sie in Microsoft Teams geladen werden!

![Registerkarte "Running" in Microsoft Teams](~/assets/yeoman-images/teams-first-app-6.png)

**Congrats! Sie haben ihre erste Microsoft Teams-App erstellt und bereitgestellt.**
