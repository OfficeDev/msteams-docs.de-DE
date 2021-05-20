---
title: 'Schnellstart: Erstellen Sie eine benutzerdefinierte persönliche Registerkarte mit Node.js und dem Yeoman Generator für Microsoft Teams'
author: laujan
description: Eine Schnellstartanleitung zum Erstellen einer persönlichen Registerkarte mit dem Yeoman Generator für Microsoft Teams.
localization_priority: Normal
ms.topic: quickstart
ms.author: lajanuar
ms.openlocfilehash: 88ad05aacaed69d695bc918e3e8a44ec18e560ae
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566606"
---
# <a name="create-a-custom-personal-tab-using-nodejs-and-the-yeoman-generator-for-microsoft-teams"></a>Erstellen Sie eine benutzerdefinierte persönliche Registerkarte mit Node.js und dem Yeoman Generator für Microsoft Teams

>[!NOTE]
>Diese Schnellstartanleitung folgt den Schritten, die im [App-Wiki "Build Your First Microsoft Teams"](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App) im Microsoft OfficeDev-GitHub-Repository beschrieben sind.

In diesem Schnellstart werden wir durch gehen, um eine benutzerdefinierte persönliche Registerkarte mit dem [Teams Yeoman Generator zu](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App)erstellen. Wir laden die Anwendung auch in Team hoch.

[!INCLUDE [node-js-yeoman-prereq](~/includes/tabs/node-js-yeoman-prereq.md)]

**Erstellen einer konfigurierbaren oder statischen Registerkarte**

Verwenden Sie die Pfeiltasten, um die statische Registerkarte auszuwählen.

>[!IMPORTANT]
>Die Pfadkomponente *yourDefaultTabNameTab*, auf die in dieser Schnellstartanleitung verwiesen wird, ist der Wert, den Sie im Generator für *den Standard-Tabnamen* plus das Wort *Tab* eingegeben haben.
>
>Beispiel: DefaultTabName: *MyTab*  =>  */MyTabTab/*

## <a name="create-your-personal-tab"></a>Erstellen Sie Ihre persönliche Registerkarte

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

- Speichern Sie **personal.html** im **Webordner** Ihrer Anwendung:

    ```bash
    ./src/app/web/<yourDefaultTabNameTab>/personal.html
    ```

- Öffnen Sie **manifest.js** im Code-Editor:

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

Denken Sie daran, die **Pfadkomponente "contentURL"** **yourDefaultTabNameTab** mit Ihrem tatsächlichen Tabnamen zu aktualisieren.

- Speichern Sie die aktualisierte **manifest.jsauf**.

- Ihre Inhaltsseite muss in einem IFrame bereitgestellt werden. Öffnen Sie **Tab.ts** im Code-Editor:

    ```bash
    ./src/app/<yourDefaultTabNameTab>/<yourDefaultTabNameTab>.ts
    ```

- Fügen Sie der Liste der IFrame-Dekoratoren Folgendes hinzu:

    ```typescript
     @PreventIframe("/<yourDefaultAppName>TabNameTab>/personal.html")
    ```

- Stellen Sie sicher, dass Sie die aktualisierte **Tab.ts-Datei** speichern. Der Tab-Code ist vollständig.

## <a name="build-and-run-your-application"></a>Erstellen und Ausführen Ihrer Anwendung

Öffnen Sie eine Eingabeaufforderung in Ihrem Projektverzeichnis, um die nächsten Aufgaben auszuführen.

[!INCLUDE [node-js-yeoman-gulp-tasks](~/includes/tabs/node-js-yeoman-gulp-tasks.md)]

Um Ihre persönliche Registerkarte anzuzeigen, gehen Sie zu `http://localhost:3007/<yourDefaultAppNameTab>/personal.html`

>![Persönlicher Tab-Screenshot](/microsoftteams/platform/assets/images/tab-images/personalTab.PNG)

## <a name="establish-a-secure-tunnel-to-your-tab"></a>Erstellen eines sicheren Tunnels zu Ihrer Registerkarte

Microsoft Teams ist ein vollständig cloudbasiertes Produkt und erfordert, dass Ihre Tab-Inhalte über HTTPS-Endpunkte in der Cloud verfügbar sind. Teams lokales Hosting nicht zulässt, müssen Sie daher entweder Ihre Registerkarte unter einer öffentlichen URL veröffentlichen oder einen Proxy verwenden, der Ihren lokalen Port für eine URL mit Internetverfügbarer verfügbar macht.

Um Ihre Tab-Erweiterung zu testen, verwenden Sie [ngrok](https://ngrok.com/docs), das in diese Anwendung integriert ist. Ngrok ist ein Reverse-Proxy-Softwaretool, das einen Tunnel zu den öffentlich verfügbaren HTTPS-Endpunkten des lokal ausgeführten Webservers erstellt. Die Webendpunkte Ihres Servers sind während der aktuellen Sitzung auf dem lokalen Computer verfügbar. Wenn die Maschine heruntergefahren wird oder in den Ruhezustand geht, ist der Dienst nicht mehr verfügbar.

Verlassen Sie localhost in Ihrer Eingabeaufforderung und geben Sie Folgendes ein:

```bash
gulp ngrok-serve
```

> [!IMPORTANT]
> Nachdem Ihre Registerkarte über **ngrok** in Microsoft-Teams hochgeladen und erfolgreich gespeichert wurde, können Sie sie in Teams anzeigen, bis die Tunnelsitzung beendet ist.

## <a name="upload-your-application-to-teams"></a>Hochladen Ihre Anwendung auf Teams

- Öffnen Sie den Microsoft Teams Client. Wenn Sie die [webbasierte Version](https://teams.microsoft.com) verwenden, können Sie Ihren Front-End-Code mit den [Entwicklertools](~/tabs/how-to/developer-tools.md)Ihres Browsers überprüfen.
- Wählen Sie im Bedienfeld **"YourTeams"** auf der linken Seite das Menü neben dem Team aus, das `...` Sie zum Testen Ihrer Registerkarte verwenden, und wählen Sie Team **verwalten** aus.
- Wählen Sie im Hauptfenster **Apps** aus der Registerkartenleiste aus und wählen Sie **Hochladen eine benutzerdefinierte App** in der unteren rechten Ecke der Seite aus.
- Öffnen Sie Ihr Projektverzeichnis, navigieren Sie zum **Ordner ./package,** wählen Sie den ZIP-Ordner aus, klicken Sie mit der rechten Maustaste, und wählen Sie **Öffnen** aus. Ihre Registerkarte wird in Teams hochgeladen.

## <a name="view-your-personal-tabs"></a>Anzeigen Ihrer persönlichen Registerkarten

Wählen Sie in der Navigationsleiste ganz links vom Teams-Client das `...` Menü aus, und wählen Sie Ihre App aus der Liste aus.

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Erstellen einer persönlichen Registerkarte mit ASP.NETCore](~/tabs/quickstarts/create-personal-tab-dotnet-core.md)
