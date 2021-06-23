---
title: Erstellen eines benutzerdefinierten Kanals und einer gruppenspezifischen Registerkarte mit Node.js und dem Yeoman-Generator für Microsoft Teams
author: surbhigupta
description: Eine Schnellstartanleitung zum Erstellen einer Kanal- und Gruppenregisterkarte mit dem Yeoman-Generator für Microsoft Teams.
localization_priority: Normal
ms.topic: quickstart
ms.author: lajanuar
ms.openlocfilehash: 6b3b5e513f91afae47364c37eb2b037a13438d35
ms.sourcegitcommit: 623d81eb079d1842813265746a5fe0fe6311b196
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/22/2021
ms.locfileid: "53069107"
---
# <a name="create-a-custom-channel-and-group-tab-using-nodejs-and-the-yeoman-generator-for-microsoft-teams"></a>Erstellen einer benutzerdefinierten Kanal- und Gruppenregisterkarte mit Node.js und dem Yeoman-Generator für Microsoft Teams

>[!NOTE]
>Diese Schnellstartanleitung folgt den Schritten, die im Wiki ["Erstellen Ihrer ersten Microsoft Teams App"](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App) im Microsoft OfficeDev-GitHub-Repository beschrieben sind.

In dieser Schnellstartanleitung werden wir schrittweise durch das Erstellen eines benutzerdefinierten Kanals und einer Gruppenregisterkarte mithilfe des [Teams Yeoman-Generators geführt.](https://github.com/OfficeDev/generator-teams/)

[!INCLUDE [node-js-yeoman-prereq](~/includes/tabs/node-js-yeoman-prereq.md)]

**Möchten Sie eine konfigurierbare oder statische Registerkarte erstellen?**

Verwenden Sie die Pfeiltasten, um die konfigurierbare Registerkarte auszuwählen.

**Welche Bereiche möchten Sie für Ihre Registerkarte verwenden?**

Sie können ein Team und/oder einen Gruppenchat auswählen

**Soll diese Registerkarte in SharePoint Online verfügbar sein? (J/n)** 

Wählen Sie **n** aus.

>[!IMPORTANT]
>The path component **yourDefaultTabNameTab**, referenced in this quickstart, is the value that you entered in the generator for **Default Tab Name** plus the word **Tab**.
>
>Beispiel: DefaultTabName: **MyTab**  =>  **/MyTabTab/**

Navigieren Sie in Ihrem Projektverzeichnis zu Folgendem:

```bash
./src/app/scripts/<yourDefaultTabNameTab>/<yourDefaultTabNameTab>.tsx
```

Hier finden Sie Ihre Registerkartenlogik. Suchen Sie die Methode, und fügen Sie oben im `render()` Containercode das folgende Tag und den folgenden `<div>` Inhalt `<PanelBody>` hinzu:

```html
    <PanelBody>
        <div style={styles.section}>
            Hello World! Yo Teams rocks!
        </div>
    </PanelBody>
```

Stellen Sie sicher, dass Sie die aktualisierte Datei speichern.

## <a name="build-and-run-your-application"></a>Erstellen und Ausführen ihrer Anwendung

Öffnen Sie eine Eingabeaufforderung in Ihrem Projektverzeichnis, um die nächsten Aufgaben auszuführen.

[!INCLUDE [node-js-yeoman-gulp-tasks](~/includes/tabs/node-js-yeoman-gulp-tasks.md)]

Wechseln Sie zum Anzeigen der Registerkartenkonfigurationsseite zu `https://localhost:3007/<yourDefaultAppNameTab>/config.html` . Folgendes sollte angezeigt werden:

![Screenshot der Konfigurationsseite](~/assets/images/tab-images/configurationPage.png)

## <a name="establish-a-secure-tunnel-to-your-tab"></a>Einrichten eines sicheren Tunnels zu Ihrer Registerkarte

Microsoft Teams ist ein vollständig cloudbasiertes Produkt und erfordert, dass Ihre Registerkarteninhalte über HTTPS-Endpunkte aus der Cloud verfügbar sind. Teams lokales Hosting nicht zulässt, müssen Sie daher Ihre Registerkarte entweder über eine öffentliche URL veröffentlichen oder einen Proxy verwenden, der Ihren lokalen Port für eine internetbasierte URL verfügbar macht.

Zum Testen der Registerkartenerweiterung verwenden Sie [ngrok,](https://ngrok.com/docs)das in diese Anwendung integriert ist. Ngrok ist ein Reverseproxysoftwaretool, das einen Tunnel zu den öffentlich verfügbaren HTTPS-Endpunkten Ihres lokal ausgeführten Webservers erstellt. Die Webendpunkte Ihres Servers sind während der aktuellen Sitzung auf Ihrem lokalen Computer verfügbar. Wenn der Computer heruntergefahren wird oder in den Ruhezustand wechselt, ist der Dienst nicht mehr verfügbar.

Beenden Sie an der Eingabeaufforderung "localhost", und geben Sie Folgendes ein:

```bash
gulp ngrok-serve
```

> [!IMPORTANT]
> Nachdem Ihre Registerkarte in Microsoft Teams hochgeladen und erfolgreich gespeichert wurde, können Sie sie im Registerkartenkatalog anzeigen, sie der Registerkartenleiste hinzufügen und damit interagieren, bis Ihre ngrok-Tunnelsitzung endet. Wenn Sie Ihre ngrok-Sitzung neu starten, müssen Sie Ihre App mit der neuen URL aktualisieren.

## <a name="upload-your-application-to-teams"></a>Hochladen Der Anwendung Teams

- Öffnen Sie den Microsoft Teams Client. Wenn Sie die [webbasierte Version](https://teams.microsoft.com) verwenden, können Sie Ihren Front-End-Code mithilfe der [Entwicklertools](~/tabs/how-to/developer-tools.md)Ihres Browsers überprüfen.
- Wählen Sie im Bereich *"YourTeams"* auf der linken Seite das Menü neben dem Team aus, `...` mit dem Sie Ihre Registerkarte testen, und wählen Sie **"Team verwalten"** aus.
- Wählen Sie in der Registerkartenleiste im Hauptbereich **Apps** aus, und wählen Sie **Hochladen eine benutzerdefinierte App** in der unteren rechten Ecke der Seite aus.
- Öffnen Sie Ihr Projektverzeichnis, navigieren Sie zum **Ordner "./package",** wählen Sie den ZIP-Ordner des App-Pakets aus, und wählen Sie **"Öffnen"** aus. Ihre Registerkarte wird in Teams hochgeladen.
- Kehren Sie zu Ihrem Team zurück, wählen Sie den Kanal aus, in dem Sie die Registerkarte anzeigen möchten, wählen Sie ➕ aus der Registerkartenleiste aus, und wählen Sie Ihre Registerkarte im Katalog aus.
- Befolgen Sie die Anweisungen zum Hinzufügen einer Registerkarte. Beachten Sie, dass ein benutzerdefiniertes Konfigurationsdialogfeld für ihre Kanal-/Gruppenregisterkarte vorhanden ist.
- Wählen Sie **"Speichern"** aus, und Ihre Registerkarte wird der Registerkartenleiste des Kanals hinzugefügt.

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Erstellen eines benutzerdefinierten Kanals und einer Gruppenregisterkarte mit ASP.NETCore](~/tabs/quickstarts/create-channel-group-tab-dotnet-core.md)
