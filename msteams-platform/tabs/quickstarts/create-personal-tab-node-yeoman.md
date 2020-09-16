---
title: 'Schnellstart: Erstellen einer benutzerdefinierten persönlichen Registerkarte mit Node.js und dem Generator für Microsoft Teams'
author: laujan
description: Eine Schnellstartanleitung zum Erstellen einer persönlichen Registerkarte mit dem Landarbeits Generator für Microsoft Teams.
ms.topic: quickstart
ms.author: lajanuar
ms.openlocfilehash: e39878d117b0b1b1f8c0e2450021d9238f5b7877
ms.sourcegitcommit: e8dfcb167274e996395b77d65999991a18f2051a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/15/2020
ms.locfileid: "47818885"
---
# <a name="quickstart-create-a-custom-personal-tab-with-nodejs-and-the-yeoman-generator-for-microsoft-teams"></a>Schnellstart: Erstellen einer benutzerdefinierten persönlichen Registerkarte mit Node.js und dem Generator für Microsoft Teams

>[!NOTE]
>Diese Schnellstartleiste folgt den Schritten im Artikel [Erstellen des ersten Microsoft Teams-App](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App) -Wikis, die im Microsoft officedev GitHub-Repository gefunden wurden.

In diesem Schnellstart werden Sie durch das Erstellen einer benutzerdefinierten persönlichen Registerkarte mithilfe des Teams-Landarbeits- [Generators](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App)gehen. Wir laden die Anwendung auch in Team hoch.

[!INCLUDE [node-js-yeoman-prereq](~/includes/tabs/node-js-yeoman-prereq.md)]

**Möchten Sie eine konfigurierbare oder statische RegisterkarteErstellen?**

Verwenden Sie die Pfeiltasten, um statische Registerkarte auszuwählen.

>[!IMPORTANT]
>In der Pfadkomponente *yourDefaultTabNameTab*, auf die in diesem Schnellstart verwiesen wird, handelt es sich um den Wert, den Sie im Generator für den *standardmäßigen Registerkartennamen* sowie die *Register*Karte Word eingegeben haben.
>
>Beispiel: DefaultTabName: *mytab*  =>  */MyTabTab/*

## <a name="create-your-personal-tab"></a>Erstellen Ihrer persönlichen Registerkarte

Zum Hinzufügen einer persönlichen Registerkarte zu dieser Anwendung erstellen Sie eine Inhaltsseite und aktualisieren vorhandene Dateien:

- Erstellen Sie in Ihrem Code-Editor eine neue HTML-Datei **personal.html** , und fügen Sie das folgende Markup hinzu:

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

- Speichern Sie **personal.html** im **Webordner ihrer** Anwendung:

```bash
./src/app/web/<yourDefaultTabNameTab>/personal.html
```

- Öffnen Sie **manifest.js** im Code-Editor:

```bash
./src/manifest/manifest.json/
```

Fügen Sie Folgendes zum leeren `staticTabs` Array hinzu ( `staticTabs":[]` ), und fügen Sie das folgende JSON-Objekt hinzu:

```json
{
    "entityId": "personalTab",
    "name": "Personal Tab ",
    "contentUrl": "https://{{HOSTNAME}}/<yourDefaultTabNameTab>/personal.html",
    "websiteUrl": "https://{{HOSTNAME}}",
    "scopes": ["personal"]
}

```

Denken Sie daran, die **"contentURL"** -Pfadkomponente **yourDefaultTabNameTab** mit Ihrem tatsächlichen Registerkartennamen zu aktualisieren.

- Speichern Sie die aktualisierte **manifest.js**.

- Die Inhaltsseite muss in einem IFRAME bereitgestellt werden. Öffnen Sie **Tab. TS** in Ihrem Code-Editor:

 ```bash
./src/app/<yourDefaultTabNameTab>/<yourDefaultTabNameTab>.ts
```

- Fügen Sie der Liste der iframe-Dekorateure Folgendes hinzu:

```typescript
 @PreventIframe("/<yourDefaultAppName>TabNameTab>/personal.html")
```

- Achten Sie darauf, die aktualisierte **Registerkarte. TS** -Datei zu speichern. Der Tab-Code ist abgeschlossen.

## <a name="build-and-run-your-application"></a>Erstellen und Ausführen der Anwendung

Öffnen Sie im Projektverzeichnis eine Eingabeaufforderung, um die nächsten Aufgaben abzuschließen.

[!INCLUDE [node-js-yeoman-gulp-tasks](~/includes/tabs/node-js-yeoman-gulp-tasks.md)]

Um Ihre persönliche Registerkarte anzuzeigen, wechseln Sie zu `http://localhost:3007/<yourDefaultAppNameTab>/personal.html`

>![Screenshot der persönlichen Registerkarte](/microsoftteams/platform/assets/images/tab-images/personalTab.PNG)

## <a name="establish-a-secure-tunnel-to-your-tab"></a>Einrichten eines sicheren Tunnels für die Registerkarte

Microsoft Teams ist ein vollständig Cloud-basiertes Produkt und erfordert, dass Ihre Registerkarteninhalte über HTTPS-Endpunkte in der Cloud verfügbar sind. Teams nicht zulassen lokales Hosting daher müssen Sie entweder Ihre Registerkarte in einer öffentlichen URL veröffentlichen oder einen Proxy verwenden, der den lokalen Port einer URL mit Internetverbindung verfügbar macht.

Um Ihre Tab-Erweiterung zu testen, verwenden Sie [ngrok](https://ngrok.com/docs), das in diese Anwendung integriert ist. Ngrok ist ein Reverse-Proxy-Software Tool, mit dem ein Tunnel zu den öffentlich verfügbaren HTTPS-Endpunkten des lokal ausgeführten Webservers erstellt wird. Die Webendpunkte Ihres Servers sind während der aktuellen Sitzung auf Ihrem lokalen Computer verfügbar. Wenn der Computer heruntergefahren wird oder in den Standbymodus wechselt, steht der Dienst nicht mehr zur Verfügung.

Beenden Sie in der Eingabeaufforderung localhost, und geben Sie Folgendes ein:

```bash
gulp ngrok-serve
```

> [!IMPORTANT]
> Nachdem die Registerkarte über *ngrok*in Microsoft Teams hochgeladen und erfolgreich gespeichert wurde, können Sie Sie in Teams anzeigen, bis Ihre Tunnelsitzung endet.

## <a name="upload-your-application-to-teams"></a>Hochladen Ihrer Anwendung in Microsoft Teams

- Öffnen Sie den Microsoft Teams-Client. Wenn Sie die [webbasierte Version](https://teams.microsoft.com) verwenden, können Sie den Front-End-Code mithilfe der [Entwicklertools](~/tabs/how-to/developer-tools.md)Ihres Browsers überprüfen.
- Wählen Sie im *YourTeams* -Bereich auf der linken Seite das `...` Menü neben dem Team aus, das Sie zum Testen der Registerkarte verwenden, und wählen Sie **Team verwalten**aus.
- Wählen Sie im Hauptbereich **apps** in der Registerkartenleiste aus, und wählen Sie **eine benutzerdefinierte App hochladen** , die sich in der unteren rechten Ecke der Seite befindet.
- Öffnen Sie Ihr Projektverzeichnis, navigieren Sie zum Ordner **./Paket** , wählen Sie den Ordner zip aus, klicken Sie mit der rechten Maustaste, und wählen Sie **Öffnen**aus. Ihre Registerkarte wird in Teams hochgeladen.

## <a name="view-your-personal-tabs"></a>Anzeigen Ihrer persönlichen Registerkarten

Wählen Sie in der navbar, die sich auf der linken Seite des Teams-Clients befindet, das `...` Menü aus, und wählen Sie Ihre APP aus der Liste aus.
