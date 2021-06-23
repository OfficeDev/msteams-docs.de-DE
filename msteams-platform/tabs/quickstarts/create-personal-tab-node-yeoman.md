---
title: 'Schnellstart: Erstellen einer benutzerdefinierten persönlichen Registerkarte mit Node.js und dem Yeoman-Generator für Microsoft Teams'
author: surbhigupta
description: Eine Schnellstartanleitung zum Erstellen einer persönlichen Registerkarte mit dem Yeoman-Generator für Microsoft Teams.
localization_priority: Normal
ms.topic: quickstart
ms.author: lajanuar
ms.openlocfilehash: 220d1018f174fc935a10311723a730ebc74ccc33
ms.sourcegitcommit: 623d81eb079d1842813265746a5fe0fe6311b196
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/22/2021
ms.locfileid: "53069202"
---
# <a name="create-a-custom-personal-tab-using-nodejs-and-the-yeoman-generator-for-microsoft-teams"></a>Erstellen einer benutzerdefinierten persönlichen Registerkarte mit Node.js und dem Yeoman-Generator für Microsoft Teams

>[!NOTE]
>Dieser Schnellstart folgt den Schritten, die im Wiki ["Erstellen Ihrer ersten Microsoft Teams App"](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App) im Microsoft OfficeDev-GitHub-Repository beschrieben sind.

In dieser Schnellstartanleitung werden wir schrittweise durch das Erstellen einer benutzerdefinierten persönlichen Registerkarte mithilfe des [Teams Yeoman-Generators geführt.](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App) Wir werden die Anwendung auch in Team hochladen.

[!INCLUDE [node-js-yeoman-prereq](~/includes/tabs/node-js-yeoman-prereq.md)]

**Erstellen einer konfigurierbaren oder statischen Registerkarte**

Verwenden Sie die Pfeiltasten, um die statische Registerkarte auszuwählen.

>[!IMPORTANT]
>The path component *yourDefaultTabNameTab*, referenced in this quickstart, is the value that you entered in the generator for *Default Tab Name* plus the word *Tab*.
>
>Beispiel: DefaultTabName: *MyTab*  =>  */MyTabTab/*

## <a name="create-your-personal-tab"></a>Erstellen Ihrer persönlichen Registerkarte

Um dieser Anwendung eine persönliche Registerkarte hinzuzufügen, erstellen Sie eine Inhaltsseite und aktualisieren vorhandene Dateien:

- Erstellen Sie in Ihrem Code-Editor eine neue HTML-Datei, **personal.html,** und fügen Sie das folgende Markup hinzu:

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

- Speichern Sie **personal.html** im **Webordner** Ihrer Anwendung:

    ```bash
    ./src/app/web/<yourDefaultTabNameTab>/personal.html
    ```

- Öffnen **Siemanifest.js** im Code-Editor:

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

Denken Sie daran, die **"contentURL"-Pfadkomponente** **"yourDefaultTabNameTab"** mit ihrem tatsächlichen Registerkartennamen zu aktualisieren.

- Speichern Sie die aktualisierte **manifest.jsunter**.

- Ihre Inhaltsseite muss in einem IFrame bereitgestellt werden. Öffnen Sie **Tab.ts** im Code-Editor:

    ```bash
    ./src/app/<yourDefaultTabNameTab>/<yourDefaultTabNameTab>.ts
    ```

- Fügen Sie der Liste der IFrame-Decoratoren Folgendes hinzu:

    ```typescript
     @PreventIframe("/<yourDefaultAppName>TabNameTab>/personal.html")
    ```

- Speichern Sie unbedingt die aktualisierte Datei **Tab.ts .** Der Registerkartencode ist vollständig.

## <a name="build-and-run-your-application"></a>Erstellen und Ausführen ihrer Anwendung

Öffnen Sie eine Eingabeaufforderung in Ihrem Projektverzeichnis, um die nächsten Aufgaben auszuführen.

[!INCLUDE [node-js-yeoman-gulp-tasks](~/includes/tabs/node-js-yeoman-gulp-tasks.md)]

Um Ihre persönliche Registerkarte anzuzeigen, wechseln Sie zu `http://localhost:3007/<yourDefaultAppNameTab>/personal.html`

>![Screenshot der persönlichen Registerkarte](/microsoftteams/platform/assets/images/tab-images/personalTab.PNG)

## <a name="establish-a-secure-tunnel-to-your-tab"></a>Einrichten eines sicheren Tunnels zu Ihrer Registerkarte

Microsoft Teams ist ein vollständig cloudbasiertes Produkt und erfordert, dass Ihre Registerkarteninhalte über HTTPS-Endpunkte aus der Cloud verfügbar sind. Teams lokales Hosting nicht zulässt, müssen Sie daher Ihre Registerkarte entweder über eine öffentliche URL veröffentlichen oder einen Proxy verwenden, der Ihren lokalen Port für eine mit dem Internet verbundene URL verfügbar macht.

Zum Testen der Registerkartenerweiterung verwenden Sie [ngrok,](https://ngrok.com/docs)das in diese Anwendung integriert ist. Ngrok ist ein Reverseproxysoftwaretool, das einen Tunnel zu den öffentlich verfügbaren HTTPS-Endpunkten Ihres lokal ausgeführten Webservers erstellt. Die Webendpunkte Ihres Servers sind während der aktuellen Sitzung auf Ihrem lokalen Computer verfügbar. Wenn der Computer heruntergefahren wird oder in den Ruhezustand wechselt, ist der Dienst nicht mehr verfügbar.

Beenden Sie an der Eingabeaufforderung "localhost", und geben Sie Folgendes ein:

```bash
gulp ngrok-serve
```

> [!IMPORTANT]
> Nachdem Ihre Registerkarte über **ngrok** in Microsoft Teams hochgeladen und erfolgreich gespeichert wurde, können Sie sie in Teams anzeigen, bis Ihre Tunnelsitzung endet.

## <a name="upload-your-application-to-teams"></a>Hochladen Der Anwendung Teams

- Öffnen Sie den Microsoft Teams Client. Wenn Sie die [webbasierte Version](https://teams.microsoft.com) verwenden, können Sie Ihren Front-End-Code mithilfe der [Entwicklertools](~/tabs/how-to/developer-tools.md)Ihres Browsers überprüfen.
- Wählen Sie im Bereich **"YourTeams"** auf der linken Seite das Menü neben dem Team aus, `...` mit dem Sie Ihre Registerkarte testen, und wählen Sie **"Team verwalten"** aus.
- Wählen Sie in der Registerkartenleiste im Hauptbereich **Apps** aus, und wählen Sie **Hochladen eine benutzerdefinierte App** in der unteren rechten Ecke der Seite aus.
- Öffnen Sie Ihr Projektverzeichnis, navigieren Sie zum **Ordner "./package",** wählen Sie den ZIP-Ordner aus, klicken Sie mit der rechten Maustaste, und wählen Sie **"Öffnen"** aus. Ihre Registerkarte wird in Teams hochgeladen.

## <a name="view-your-personal-tabs"></a>Anzeigen Ihrer persönlichen Registerkarten

Wählen Sie in der Navigationsleiste ganz links vom Teams Client das `...` Menü aus, und wählen Sie Ihre App aus der Liste aus.

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Erstellen einer persönlichen Registerkarte mit ASP.NETCore](~/tabs/quickstarts/create-personal-tab-dotnet-core.md)
