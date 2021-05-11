---
title: 'Schnellstart: Erstellen einer benutzerdefinierten persönlichen Registerkarte mit Node.js und dem Yeoman-Generator für Microsoft Teams'
author: laujan
description: Eine Schnellstartanleitung zum Erstellen einer persönlichen Registerkarte mit dem Yeoman-Generator für Microsoft Teams.
localization_priority: Normal
ms.topic: quickstart
ms.author: lajanuar
ms.openlocfilehash: 30143fa3c84a68ae6c34176b252badaa4cef9613
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2021
ms.locfileid: "52019552"
---
# <a name="quickstart-create-a-custom-personal-tab-with-nodejs-and-the-yeoman-generator-for-microsoft-teams"></a>Schnellstart: Erstellen einer benutzerdefinierten persönlichen Registerkarte mit Node.js und dem Yeoman-Generator für Microsoft Teams

>[!NOTE]
>Dieser Schnellstart folgt den Schritten, die im Wiki zum Erstellen der ersten [Microsoft Teams-App](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App) im Microsoft OfficeDev-Repository GitHub sind.

In dieser Schnellstartanleitung werden wir durch das Erstellen einer benutzerdefinierten persönlichen Registerkarte mithilfe des Teams [Yeoman-Generators gehen.](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App) Wir laden die Anwendung auch in Team hoch.

[!INCLUDE [node-js-yeoman-prereq](~/includes/tabs/node-js-yeoman-prereq.md)]

**Möchten Sie eine konfigurierbare oder statische Registerkarte erstellen?**

Verwenden Sie die Pfeiltasten, um die statische Registerkarte auszuwählen.

>[!IMPORTANT]
>Die Pfadkomponente *yourDefaultTabNameTab*, auf die in diesem Schnellstart verwiesen wird, ist der Wert, den Sie im Generator für *Standardregisterkartenname* plus das Wort *Tab eingegeben haben.*
>
>Beispiel: DefaultTabName: *MyTab*  =>  */MyTabTab/*

## <a name="create-your-personal-tab"></a>Erstellen Ihrer persönlichen Registerkarte

Um dieser Anwendung eine persönliche Registerkarte hinzuzufügen, erstellen Sie eine Inhaltsseite und aktualisieren vorhandene Dateien:

- Erstellen Sie im Code-Editor eine neue HTML-Datei, **personal.html,** und fügen Sie das folgende Markup hinzu:

```html
<!DOCTYPE html>
<html>
    <head>
        <meta charset="UTF-8">
        <title>
            <!-- Todo: add your a title here -->
        </title>
        <meta name="viewport" content="width=device-width, initial-scale=1.0">
        <!-- inject:css -->
        <!-- endinject -->
    </head>
        <body>
            <h1>Personal Tab</h1>
            <p><img src="/assets/icon.png"></p>
            <p>This is your personal tab!</p>
        </body>
</html>
```

- Speichern **personal.html** im Webordner Ihrer **Anwendung:**

```bash
./src/app/web/<yourDefaultTabNameTab>/personal.html
```

- Öffnen **manifest.jsim** Code-Editor:

```bash
./src/manifest/manifest.json/
```

Fügen Sie dem leeren Array ( ) Folgendes `staticTabs` `staticTabs":[]` hinzu, und fügen Sie das folgende JSON-Objekt hinzu:

```json
{
    "entityId": "personalTab",
    "name": "Personal Tab ",
    "contentUrl": "https://{{HOSTNAME}}/<yourDefaultTabNameTab>/personal.html",
    "websiteUrl": "https://{{HOSTNAME}}",
    "scopes": ["personal"]
}

```

Denken Sie daran, die **Pfadkomponente "contentURL"** **yourDefaultTabNameTab** mit ihrem tatsächlichen Registerkartennamen zu aktualisieren.

- Speichern Sie die **aktualisiertemanifest.jsunter**.

- Ihre Inhaltsseite muss in einem IFrame bedient werden. Öffnen **Sie Tab.ts** im Code-Editor:

 ```bash
./src/app/<yourDefaultTabNameTab>/<yourDefaultTabNameTab>.ts
```

- Fügen Sie der Liste der IFrame-Verzierer Folgendes hinzu:

```typescript
 @PreventIframe("/<yourDefaultAppName>TabNameTab>/personal.html")
```

- Stellen Sie sicher, dass Sie die aktualisierte **Tab.ts-Datei** speichern. Der Registerkartencode ist vollständig.

## <a name="build-and-run-your-application"></a>Erstellen und Ausführen Der Anwendung

Öffnen Sie eine Eingabeaufforderung in Ihrem Projektverzeichnis, um die nächsten Aufgaben auszuführen.

[!INCLUDE [node-js-yeoman-gulp-tasks](~/includes/tabs/node-js-yeoman-gulp-tasks.md)]

Um Ihre persönliche Registerkarte zu sehen, wechseln Sie zu `http://localhost:3007/<yourDefaultAppNameTab>/personal.html`

>![Screenshot der persönlichen Registerkarte](/microsoftteams/platform/assets/images/tab-images/personalTab.PNG)

## <a name="establish-a-secure-tunnel-to-your-tab"></a>Einrichten eines sicheren Tunnels für Ihre Registerkarte

Microsoft Teams ist ein vollständig cloudbasiertes Produkt und erfordert, dass Ihre Registerkarteninhalte über HTTPS-Endpunkte in der Cloud verfügbar sind. Teams lokales Hosting ist nicht zulässig, daher müssen Sie Ihre Registerkarte entweder in einer öffentlichen URL veröffentlichen oder einen Proxy verwenden, der Ihren lokalen Port für eine mit dem Internet zugängliche URL verfügbar macht.

Zum Testen der Tabulatorerweiterung verwenden Sie [ngrok](https://ngrok.com/docs), das in diese Anwendung integrierte. Ngrok ist ein Reverseproxy-Softwaretool, das einen Tunnel zu den öffentlich verfügbaren HTTPS-Endpunkten Ihres lokal ausgeführten Webservers erstellt. Die Webendpunkte Ihres Servers stehen während der aktuellen Sitzung auf Dem lokalen Computer zur Verfügung. Wenn der Computer heruntergefahren wird oder in den Ruhezustand geht, ist der Dienst nicht mehr verfügbar.

Beenden Sie localhost in der Eingabeaufforderung, und geben Sie Folgendes ein:

```bash
gulp ngrok-serve
```

> [!IMPORTANT]
> Nachdem Ihre Registerkarte in Microsoft Teams hochgeladen, über *ngrok* und erfolgreich gespeichert wurde, können Sie sie in der Teams, bis Ihre Tunnelsitzung endet.

## <a name="upload-your-application-to-teams"></a>Hochladen Ihre Anwendung zu Teams

- Öffnen Sie den Microsoft Teams Client. Wenn Sie die [webbasierte Version verwenden,](https://teams.microsoft.com) können Sie Ihren Front-End-Code mithilfe der Entwicklertools Ihres Browsers [überprüfen.](~/tabs/how-to/developer-tools.md)
- Wählen Sie *im Bereich YourTeams* auf der linken Seite das Menü neben dem Team aus, das Sie zum Testen Ihrer Registerkarte verwenden, und `...` wählen Sie Team verwalten **aus.**
- Wählen Sie im Hauptbereich **apps** aus der Registerkartenleiste aus, und wählen **Hochladen** eine benutzerdefinierte App in der unteren rechten Ecke der Seite aus.
- Öffnen Sie Ihr Projektverzeichnis, navigieren Sie zum **Ordner ./package,** wählen Sie den Ordner "ZIP" aus, klicken Sie mit der rechten Maustaste, und wählen Sie **Öffnen aus.** Ihre Registerkarte wird in Teams.

## <a name="view-your-personal-tabs"></a>Anzeigen Ihrer persönlichen Registerkarten

Wählen Sie in der Navigationsleiste ganz links neben dem client Teams das Menü aus, und wählen Sie ihre `...` App aus der Liste aus.
