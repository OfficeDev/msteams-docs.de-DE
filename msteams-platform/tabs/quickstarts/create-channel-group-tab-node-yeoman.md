---
title: Erstellen einer benutzerdefinierten Kanal-und Gruppenregisterkarte mit Node.js und dem Erzeuger Generator für Microsoft Teams
author: laujan
description: Eine Schnellstartanleitung zum Erstellen einer Kanal-und Gruppenregisterkarte mit dem Landarbeits Generator für Microsoft Teams.
ms.topic: quickstart
ms.author: lajanuar
ms.openlocfilehash: 77081f83c753f812032ccfebe2accd3cb8859f99
ms.sourcegitcommit: e8dfcb167274e996395b77d65999991a18f2051a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/15/2020
ms.locfileid: "47818934"
---
# <a name="create-a-custom-channel-and-group-tab-with-nodejs-and-the-yeoman-generator-for-microsoft-teams"></a>Erstellen einer benutzerdefinierten Kanal-und Gruppenregisterkarte mit Node.js und dem Erzeuger Generator für Microsoft Teams

>[!NOTE]
>Diese Schnellstartleiste folgt den Schritten im Artikel [Erstellen des ersten Microsoft Teams-App](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App) -Wikis, die im Microsoft officedev GitHub-Repository gefunden wurden.

In diesem Schnellstart werden Sie durch das Erstellen einer benutzerdefinierten Kanal-und Gruppenregisterkarte mithilfe des Teams-Landarbeits [Generators](https://github.com/OfficeDev/generator-teams/)durchlaufen.

[!INCLUDE [node-js-yeoman-prereq](~/includes/tabs/node-js-yeoman-prereq.md)]

**Möchten Sie eine konfigurierbare oder statische RegisterkarteErstellen?**

Verwenden Sie die Pfeiltasten, um die Registerkarte konfigurierbar auszuwählen.

**Welche Bereiche möchten Sie für Ihre Registerkarte verwenden?**

Sie können ein Team und/oder einen Gruppenchat auswählen.

**Soll diese Registerkarte in SharePoint Online verfügbar sein? (J/n)** 

Wählen Sie **n**aus.

>[!IMPORTANT]
>In der Pfadkomponente **yourDefaultTabNameTab**, auf die in diesem Schnellstart verwiesen wird, handelt es sich um den Wert, den Sie im Generator für den **standardmäßigen Registerkartennamen** sowie die **Register**Karte Word eingegeben haben.
>
>Beispiel: DefaultTabName: **mytab**  =>  **/MyTabTab/**

Navigieren Sie in Ihrem Projektverzeichnis zu folgendem:

```bash
./src/app/scripts/<yourDefaultTabNameTab>/<yourDefaultTabNameTab>.tsx
```

Hier finden Sie Ihre Tab-Logik. Suchen `render()` Sie die-Methode, und fügen Sie das folgende `<div>` Tag und den Inhalt oben im `<PanelBody>` Container Code hinzu:

```html
    <PanelBody>
        <div style={styles.section}>
            Hello World! Yo Teams rocks!
        </div>
    </PanelBody>
```

Stellen Sie sicher, dass Sie die aktualisierte Datei speichern.

## <a name="build-and-run-your-application"></a>Erstellen und Ausführen der Anwendung

Öffnen Sie im Projektverzeichnis eine Eingabeaufforderung, um die nächsten Aufgaben abzuschließen.

[!INCLUDE [node-js-yeoman-gulp-tasks](~/includes/tabs/node-js-yeoman-gulp-tasks.md)]

Um Ihre Registerkarten-Konfigurationsseite anzuzeigen, wechseln Sie zu `https://localhost:3007/<yourDefaultAppNameTab>/config.html` . Folgendes sollte angezeigt werden:

![Screenshot der Konfigurationsseite](~/assets/images/tab-images/configurationPage.png)

## <a name="establish-a-secure-tunnel-to-your-tab"></a>Einrichten eines sicheren Tunnels für die Registerkarte

Microsoft Teams ist ein vollständig Cloud-basiertes Produkt und erfordert, dass Ihre Registerkarteninhalte über HTTPS-Endpunkte in der Cloud verfügbar sind. Teams nicht zulassen lokales Hosting daher müssen Sie entweder Ihre Registerkarte in einer öffentlichen URL veröffentlichen oder einen Proxy verwenden, der den lokalen Port einer URL mit Internetverbindung verfügbar macht.

Um Ihre Tab-Erweiterung zu testen, verwenden Sie [ngrok](https://ngrok.com/docs), das in diese Anwendung integriert ist. Ngrok ist ein Reverse-Proxy-Software Tool, mit dem ein Tunnel zu den öffentlich verfügbaren HTTPS-Endpunkten des lokal ausgeführten Webservers erstellt wird. Die Webendpunkte Ihres Servers sind während der aktuellen Sitzung auf Ihrem lokalen Computer verfügbar. Wenn der Computer heruntergefahren wird oder in den Standbymodus wechselt, steht der Dienst nicht mehr zur Verfügung.

Beenden Sie in der Eingabeaufforderung localhost, und geben Sie Folgendes ein:

```bash
gulp ngrok-serve
```

> [!IMPORTANT]
> Nachdem die Registerkarte in Microsoft Teams hochgeladen und erfolgreich gespeichert wurde, können Sie Sie im Registerkarten Katalog anzeigen, der Registerkartenleiste hinzufügen und mit ihr interagieren, bis die ngrok-Tunnelsitzung endet. Wenn Sie die ngrok-Sitzung neu starten, müssen Sie Ihre APP mit der neuen URL aktualisieren.

## <a name="upload-your-application-to-teams"></a>Hochladen Ihrer Anwendung in Microsoft Teams

- Öffnen Sie den Microsoft Teams-Client. Wenn Sie die [webbasierte Version](https://teams.microsoft.com) verwenden, können Sie den Front-End-Code mithilfe der [Entwicklertools](~/tabs/how-to/developer-tools.md)Ihres Browsers überprüfen.
- Wählen Sie im *YourTeams* -Bereich auf der linken Seite das `...` Menü neben dem Team aus, das Sie zum Testen der Registerkarte verwenden, und wählen Sie **Team verwalten**aus.
- Wählen Sie im Hauptbereich **apps** in der Registerkartenleiste aus, und wählen Sie **eine benutzerdefinierte App hochladen** , die sich in der unteren rechten Ecke der Seite befindet.
- Öffnen Sie Ihr Projektverzeichnis, navigieren Sie zum Ordner **./Paket** , wählen Sie den ZIP-Ordner für das App-Paket aus, und wählen Sie **Öffnen**aus. Ihre Registerkarte wird in Teams hochgeladen.
- Kehren Sie zu Ihrem Team zurück, wählen Sie den Kanal aus, in dem Sie die Registerkarte anzeigen möchten, wählen Sie in der Registerkartenleiste ➕ aus, und wählen Sie im Katalog die Registerkarte aus.
- Befolgen Sie die Anweisungen zum Hinzufügen einer Registerkarte. Beachten Sie, dass für die Registerkarte Kanal/Gruppe ein benutzerdefiniertes Konfigurationsdialogfeld vorhanden ist.
- Wählen Sie **Speichern** aus, und ihre Registerkarte wird der Registerkartenleiste des Kanals hinzugefügt.
