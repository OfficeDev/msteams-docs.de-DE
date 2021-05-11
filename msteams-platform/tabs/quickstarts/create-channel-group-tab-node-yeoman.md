---
title: Erstellen Sie einen benutzerdefinierten Kanal und eine gruppe Registerkarte mit Node.js und dem Yeoman Generator für Microsoft Teams
author: laujan
description: Eine Schnellstartanleitung zum Erstellen eines Kanals und einer Gruppenregisterkarte mit dem Yeoman Generator für Microsoft Teams.
localization_priority: Normal
ms.topic: quickstart
ms.author: lajanuar
ms.openlocfilehash: 962a558014a3bc84010860082df6891bb48c7715
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020303"
---
# <a name="create-a-custom-channel-and-group-tab-with-nodejs-and-the-yeoman-generator-for-microsoft-teams"></a>Erstellen Sie einen benutzerdefinierten Kanal und eine Node.js mit Microsoft Teams

>[!NOTE]
>Dieser Schnellstart folgt den Schritten, die im Wiki zum Erstellen der ersten [Microsoft Teams-App](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App) im Microsoft OfficeDev-Repository GitHub sind.

In dieser Schnellstartanleitung wird das Erstellen eines benutzerdefinierten Kanals und einer Registerkarte für Gruppen mithilfe des Teams [Yeoman-Generators durchgef?llt.](https://github.com/OfficeDev/generator-teams/)

[!INCLUDE [node-js-yeoman-prereq](~/includes/tabs/node-js-yeoman-prereq.md)]

**Möchten Sie eine konfigurierbare oder statische Registerkarte erstellen?**

Verwenden Sie die Pfeiltasten, um die konfigurierbare Registerkarte auszuwählen.

**Welche Bereiche möchten Sie für Ihre Registerkarte verwenden?**

Sie können einen Team- und/oder Gruppenchat auswählen

**Möchten Sie, dass diese Registerkarte in SharePoint Online verfügbar ist? (Y/n)** 

Wählen **Sie n** aus.

>[!IMPORTANT]
>Die Pfadkomponente **yourDefaultTabNameTab**, auf die in diesem Schnellstart verwiesen wird, ist der Wert, den Sie im Generator für **Standardregisterkartenname** plus das Wort **Tab eingegeben haben.**
>
>Beispiel: DefaultTabName: **MyTab**  =>  **/MyTabTab/**

Navigieren Sie in Ihrem Projektverzeichnis zu folgendem:

```bash
./src/app/scripts/<yourDefaultTabNameTab>/<yourDefaultTabNameTab>.tsx
```

Hier finden Sie Ihre Registerkartenlogik. Suchen Sie die Methode, und fügen Sie dem Containercode das folgende Tag und `render()` `<div>` den folgenden Inhalt `<PanelBody>` hinzu:

```html
    <PanelBody>
        <div style={styles.section}>
            Hello World! Yo Teams rocks!
        </div>
    </PanelBody>
```

Stellen Sie sicher, dass die aktualisierte Datei gespeichert wird.

## <a name="build-and-run-your-application"></a>Erstellen und Ausführen Der Anwendung

Öffnen Sie eine Eingabeaufforderung in Ihrem Projektverzeichnis, um die nächsten Aufgaben auszuführen.

[!INCLUDE [node-js-yeoman-gulp-tasks](~/includes/tabs/node-js-yeoman-gulp-tasks.md)]

Wechseln Sie zum Anzeigen der Registerkartenkonfigurationsseite zu `https://localhost:3007/<yourDefaultAppNameTab>/config.html` . Folgendes sollte angezeigt werden:

![Screenshot der Konfigurationsseite](~/assets/images/tab-images/configurationPage.png)

## <a name="establish-a-secure-tunnel-to-your-tab"></a>Einrichten eines sicheren Tunnels für Ihre Registerkarte

Microsoft Teams ist ein vollständig cloudbasiertes Produkt und erfordert, dass Ihre Registerkarteninhalte über HTTPS-Endpunkte in der Cloud verfügbar sind. Teams lokales Hosting ist nicht zulässig, daher müssen Sie Ihre Registerkarte entweder in einer öffentlichen URL veröffentlichen oder einen Proxy verwenden, der Ihren lokalen Port für eine mit dem Internet zugängliche URL verfügbar macht.

Zum Testen der Tabulatorerweiterung verwenden Sie [ngrok](https://ngrok.com/docs), das in diese Anwendung integrierte. Ngrok ist ein Reverseproxy-Softwaretool, das einen Tunnel zu den öffentlich verfügbaren HTTPS-Endpunkten Ihres lokal ausgeführten Webservers erstellt. Die Webendpunkte Ihres Servers stehen während der aktuellen Sitzung auf Dem lokalen Computer zur Verfügung. Wenn der Computer heruntergefahren wird oder in den Ruhezustand geht, ist der Dienst nicht mehr verfügbar.

Beenden Sie localhost in der Eingabeaufforderung, und geben Sie Folgendes ein:

```bash
gulp ngrok-serve
```

> [!IMPORTANT]
> Nachdem Ihre Registerkarte in Microsoft Teams hochgeladen und erfolgreich gespeichert wurde, können Sie sie im Registerkartenkatalog anzeigen, der Registerkartenleiste hinzufügen und mit ihr interagieren, bis Ihre ngrok-Tunnelsitzung endet. Wenn Sie Ihre ngrok-Sitzung neu starten, müssen Sie Ihre App mit der neuen URL aktualisieren.

## <a name="upload-your-application-to-teams"></a>Hochladen Ihre Anwendung zu Teams

- Öffnen Sie den Microsoft Teams Client. Wenn Sie die [webbasierte Version verwenden,](https://teams.microsoft.com) können Sie Ihren Front-End-Code mithilfe der Entwicklertools Ihres Browsers [überprüfen.](~/tabs/how-to/developer-tools.md)
- Wählen Sie *im Bereich YourTeams* auf der linken Seite das Menü neben dem Team aus, das Sie zum Testen Ihrer Registerkarte verwenden, und `...` wählen Sie Team verwalten **aus.**
- Wählen Sie im Hauptbereich **apps** aus der Registerkartenleiste aus, und wählen **Hochladen** eine benutzerdefinierte App in der unteren rechten Ecke der Seite aus.
- Öffnen Sie Ihr Projektverzeichnis, navigieren Sie zum **Ordner ./package,** wählen Sie den Ordner app package zip aus, und wählen Sie **Öffnen aus.** Ihre Registerkarte wird in Teams.
- Kehren Sie zu Ihrem Team zurück, wählen Sie den Kanal aus, in dem Sie die Registerkarte anzeigen möchten, wählen ➕ in der Registerkartenleiste aus, und wählen Sie ihre Registerkarte aus dem Katalog aus.
- Befolgen Sie die Anweisungen zum Hinzufügen einer Registerkarte. Beachten Sie, dass es ein benutzerdefiniertes Konfigurationsdialogfeld für Die Registerkarte Kanal/Gruppe gibt.
- Wählen **Sie Speichern** aus, und Ihre Registerkarte wird der Registerkartenleiste des Kanals hinzugefügt.
