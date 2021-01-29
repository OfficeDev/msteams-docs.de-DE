---
title: Lernprogramm – Erstellen Ihrer ersten App mithilfe des Yeoman-Generators
description: Erfahren Sie, wie Sie mit dem Erstellen von Microsoft Teams-Apps mit dem Yeoman-Generator beginnen.
keywords: Erste Schritte node.js nodejs yeoman
ms.topic: tutorial
ms.custom: scenarios:getting-started
ms.openlocfilehash: f7f0fb3ba1be28dfa7d343be3af9d122b4ad090d
ms.sourcegitcommit: fa64b83c0b534bf7a89f256880d5b5ca193e4b04
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/28/2021
ms.locfileid: "50037004"
---
# <a name="create-your-first-microsoft-teams-app-using-the-yeoman-generator"></a>Erstellen Ihrer ersten Microsoft Teams-App mithilfe des Yeoman-Generators

>[!Note]
>Dieses Lernprogramm stammt aus dem [Yeoman-Generator für Teams-Wiki.](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App)

In diesem Lernprogramm werden wir durch die Erstellung Ihrer ersten Microsoft Teams-App mithilfe des Microsoft Teams-Yeoman-Generators gehen. Es wird davon ausgegangen, dass Sie über ein Teams-Konto verfügen, das das [Querladen von](~/concepts/build-and-test/prepare-your-o365-tenant.md)Apps ermöglicht.

![Yeoman-Generator-Git](~/assets/yeoman-demo.gif)

## <a name="setup-and-prepare-your-machine"></a>Einrichten und Vorbereiten des Computers

Sie müssen Folgendes auf Ihrem Computer installieren, bevor Sie mit der Verwendung des Yeoman-Generators beginnen.

### <a name="install-nodejs"></a>Installieren von Node.js

Sie müssen die Node.js auf Ihrem Computer installiert haben. Sie sollten die neueste [LTS-Version verwenden.](https://nodejs.org)

### <a name="install-a-code-editor"></a>Installieren eines Code-Editors

Sie benötigen auch einen Code-Editor, und sie können den von Ihnen bevorzugten Texteditor verwenden. Die meisten dieser Dokumentationen und Screenshots beziehen sich jedoch auf die Verwendung [Visual Studio Code .](https://code.visualstudio.com)

### <a name="install-yeoman-and-gulp-cli"></a>Installieren von Yeoman und Gulp CLI

Um mithilfe des Teams-Generators ein Gerüst für Projekte erstellen zu können, müssen Sie das Tool Yeoman sowie den Gulp CLI-Task-Manager installieren.

Öffnen Sie eine Eingabeaufforderung, und geben Sie Folgendes ein:

```bash
npm install yo gulp-cli --global
```

## <a name="install-the-generator"></a>Installieren des Generators

Installieren Sie den Teams-Yeoman-Generator mit dem folgenden Befehl:

```bash
npm install generator-teams --global
```

Führen Sie den folgenden Befehl aus, um Vorschauversionen des Generators zu installieren:

```bash
npm install generator-teams@preview --global
```

## <a name="generate-your-project"></a>Generieren Des Projekts

Öffnen Sie eine Eingabeaufforderung, und erstellen Sie ein neues Verzeichnis, in dem Sie Ihr Projekt erstellen möchten, und führen Sie in diesem Verzeichnis den Befehl `yo teams` aus.

Dadurch wird der Generator gestartet, der Sie mit einer Reihe von Fragen anfordert.

![yo teams](~/assets/yeoman-images/teams-first-app-1.png)

Die erste Frage ist der Projektname. Sie können ihn durch Drücken der EINGABETASTE so be lassen, wie er ist. Die nächste Frage stellt Ihnen die Frage, ob Sie ein neues Verzeichnis erstellen oder das aktuelle Verzeichnis verwenden möchten. Da wir uns bereits in dem Verzeichnis befinden, das wir verwenden möchten, drücken wir einfach die EINGABETASTE.

Im folgenden Schritt wird nach einem Titel Ihres Projekts gefragt. Dieser Titel wird im Manifest und in der Beschreibung Ihrer App verwendet. Anschließend werden Sie nach einem Firmennamen gefragt, der auch im Manifest verwendet wird.

In der fünften Frage werden Sie gefragt, welche Version des Manifests Sie verwenden möchten. Wählen Sie für dieses `v1.5` Lernprogramm das aktuelle allgemein verfügbare Schema aus.

Danach fragt der Generator Sie nach den Elementen, die Sie Ihrem Projekt hinzufügen möchten. Sie können ein einzelnes oder eine beliebige Kombination von Elementen auswählen. For now, just select *a Tab*.

![Elementauswahl](~/assets/yeoman-images/teams-first-app-2.png)

Basierend auf den ausgewählten Elementen werden Ihnen eine Reihe von Nachschlagefragen gestellt.

Jetzt müssen Sie eine URL eingeben, unter der Sie Ihre Lösung hosten. Dies kann eine beliebige URL sein, der Generator schlägt jedoch standardmäßig eine Azure-Website-URL vor.

Der Generator verfügt über viele integrierte erweiterte Features, für die Sie sich entscheiden oder abmelden können. Nach der URL-Frage, die Sie fragen, ob Sie Komponententests für Ihre Lösung hinzufügen möchten, ist der Standardwert "Ja". Wenn Sie dies auswählen, verfügt das generierte Projekt über ein Komponententestframework und einige Standardeinheitstests für die verschiedenen Elemente, die Gerüste erstellt werden. In diesem Lernprogramm wird kein Testframework verwendet.

Um Die Protokollierung für Sie einfach zu machen, werden Sie auch gefragt, ob Sie Azure Application Insights für die Protokollierung verwenden möchten. Wenn Sie "Ja" auswählen, müssen Sie einen Azure Application Insights-Schlüssel bereitstellen. In diesem Lernprogramm können Sie die Verwendung von Application Insights abmelden.

Die nächsten Fragen basieren auf der zuvor von Ihnen getroffenen Auswahl von Elementen. Für eine Registerkarte müssen Sie nur einen Namen eingeben und optional auswählen, ob Sie diese App als SharePoint Online-Web part verwenden möchten. Nachdem Sie diesen Namen angegeben haben, generiert der Generator das Projekt und installiert alle Abhängigkeiten. Dies dauert ein oder zwei Minuten.

## <a name="add-some-code-to-your-tab"></a>Hinzufügen von Code zu Ihrer Registerkarte

Sobald der Generator fertig ist, können Sie die Lösung in Ihrem bevorzugten Codeeditor öffnen. Nehmen Sie sich ein oder zwei Minuten Zeit und machen Sie sich mit der Struktur des Codes vertraut . Weitere Informationen dazu finden Sie in der [Dokumentation zur Projektstruktur.](https://github.com/OfficeDev/generator-teams/wiki/Project-Structure)

Die Registerkarte befindet sich in der `./src/app/scripts/myFirstAppTab/MyFirstAppTab.tsx` Datei. Dies ist die TypeScript React-basierte Klasse für Ihre Registerkarte. Suchen Sie die Methode, und fügen Sie eine Codezeile innerhalb des Steuerelements hinzu, `render()` damit sie wie hier `<PanelBody>` aussieht:

``` TypeScript
<PanelBody>
    <div style={styles.section}>
    Hello World! Yo Teams rocks!
    </div>
</PanelBody>
```

Speichern Sie die Datei, und kehren Sie zur Eingabeaufforderung zurück.

## <a name="build-your-app"></a>Erstellen Sie Ihre Anwendung

Sie können nun Ihr Projekt erstellen. Dies erfolgt in zwei Schritten (oder in einem Schritt, siehe unten).

Zuerst müssen Sie die Teams-App-Manifestdatei erstellen, die Sie in Microsoft Teams hochladen/querladen. Dies erfolgt durch die Gulp-Aufgabe. `gulp manifest` Dadurch wird das Manifest überprüft und eine ZIP-Datei im Verzeichnis `./package` erstellt.

Um Ihre Lösung zu erstellen, verwenden Sie den `gulp build` Befehl. Dadurch wird Ihre Lösung in den Ordner `./dist` transpiliert. 

## <a name="run-your-app"></a>Ausführen Ihrer App

Um Ihre App auszuführen, verwenden Sie den `gulp serve` Befehl. Dadurch erstellen und starten Sie einen lokalen Webserver, auf dem Sie Ihre App testen können. Der Befehl erstellt die Anwendung auch neu, wenn Sie eine Datei in Ihrem Projekt speichern. 

Sie sollten nun in der Lage sein, zu navigieren, `http://localhost:3007/myFirstAppTab/` um sicherzustellen, dass die Registerkarte gerendert wird. Allerdings noch nicht in Microsoft Teams.

![Anzeigen Ihrer Website in einem Browser](~/assets/yeoman-images/teams-first-app-3.png)

## <a name="run-your-app-in-microsoft-teams"></a>Ausführen Ihrer App in Microsoft Teams

Microsoft Teams lässt nicht zu, dass Ihre App auf localhost gehostet wird. Daher müssen Sie sie entweder unter einer öffentlichen URL veröffentlichen oder einen Proxy wie ngrok verwenden.

Eine gute Nachricht ist, dass das Gerüstprojekt über dieses integrierte Projekt verfügt. Wenn Sie den ngrok-Dienst ausführen, wird er im Hintergrund mit einem eindeutigen und öffentlichen DNS-Eintrag gestartet. Außerdem wird das Manifest mit dieser eindeutigen URL gepackt und dann genau dasselbe wie `gulp ngrok-serve` `gulp serve` ausgeführt.

Erstellen Sie nach der Ausführung ein neues Microsoft Teams-Team, und klicken Sie bei seiner Erstellung auf den Teamnamen, um zu den Teameinstellungen zu wechseln und dann `gulp ngrok-serve` *Apps auszuwählen.* In der unteren rechten Ecke sollte ein Link zum *Hochladen* einer benutzerdefinierten App angezeigt werden. Wählen Sie ihn aus, und navigieren Sie dann zu Ihrem Projektordner und dem aufgerufenen `package` Unterordner. Wählen Sie die ZIP-Datei in diesem Ordner aus, und wählen Sie "Öffnen" aus. Ihre App wird nun in Microsoft Teams sideloaded.

![Sideloaded app](~/assets/yeoman-images/teams-first-app-4.png)

Wechseln Sie zurück zum Kanal *"Allgemein",* und wählen *+* Sie aus, um eine neue Registerkarte hinzuzufügen. Ihre Registerkarte sollte in der Liste der Registerkarten angezeigt werden.

![Registerkarte konfigurieren](~/assets/yeoman-images/teams-first-app-5.png)

Wählen Sie Ihre Registerkarte aus, und folgen Sie den Anweisungen, um sie hinzuzufügen. Beachten Sie, dass Sie über ein benutzerdefiniertes Konfigurationsdialogfeld verfügen, für das Sie die Quelle bearbeiten können. Wählen *Sie "Speichern"* aus, um ihre Registerkarte zum Kanal hinzuzufügen. Sobald Sie fertig sind, sollte Ihre Registerkarte in Microsoft Teams geladen werden!

![Ausführen der Registerkarte in Teams](~/assets/yeoman-images/teams-first-app-6.png)

**Cong kongenial! Sie haben Ihre erste Microsoft Teams-App erstellt und bereitgestellt.**
