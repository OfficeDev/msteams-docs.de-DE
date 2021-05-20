---
title: Erstellen Sie einen benutzerdefinierten Kanal und Gruppen-Tab mit Node.js und dem Yeoman Generator für Microsoft Teams
author: laujan
description: Eine Schnellstartanleitung zum Erstellen eines Kanals und einer Gruppenregisterkarte mit dem Yeoman Generator für Microsoft Teams.
localization_priority: Normal
ms.topic: quickstart
ms.author: lajanuar
ms.openlocfilehash: 559393884e3b8a4aad1787ea4ca8f9f4de54d151
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566645"
---
# <a name="create-a-custom-channel-and-group-tab-using-nodejs-and-the-yeoman-generator-for-microsoft-teams"></a>Erstellen Sie eine benutzerdefinierte Kanal- und Gruppenregisterkarte mit Node.js und dem Yeoman Generator für Microsoft Teams

>[!NOTE]
>Diese Schnellstartanleitung folgt den Schritten, die im [App-Wiki "Build Your First Microsoft Teams"](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App) im Microsoft OfficeDev-GitHub-Repository beschrieben sind.

In dieser Schnellstartanleitung werden wir mit dem [Teams Yeoman-Generator](https://github.com/OfficeDev/generator-teams/)einen benutzerdefinierten Kanal und eine Gruppenregisterkarte erstellen.

[!INCLUDE [node-js-yeoman-prereq](~/includes/tabs/node-js-yeoman-prereq.md)]

**Möchten Sie eine konfigurierbare oder statische Registerkarte erstellen?**

Verwenden Sie die Pfeiltasten, um die konfigurierbare Registerkarte auszuwählen.

**Welche Bereiche beabsichtigen Sie für Ihre Registerkarte zu verwenden?**

Sie können ein Team und/oder einen Gruppenchat auswählen

**Soll diese Registerkarte in SharePoint Online verfügbar sein? (Y/n)** 

Wählen Sie **n**.

>[!IMPORTANT]
>Die Pfadkomponente **yourDefaultTabNameTab**, auf die in dieser Schnellstartanleitung verwiesen wird, ist der Wert, den Sie im Generator für **den Standard-Tabnamen** plus das Wort **Tab** eingegeben haben.
>
>Beispiel: DefaultTabName: **MyTab**  =>  **/MyTabTab/**

Navigieren Sie in Ihrem Projektverzeichnis zu den folgenden Optionen:

```bash
./src/app/scripts/<yourDefaultTabNameTab>/<yourDefaultTabNameTab>.tsx
```

Das ist, wo Sie Ihre Registerkarte Nastonlogik finden. Suchen Sie die `render()` Methode, und fügen Sie das folgende Tag und den folgenden `<div>` Inhalt am oberen Rand des `<PanelBody>` Containercodes hinzu:

```html
    <PanelBody>
        <div style={styles.section}>
            Hello World! Yo Teams rocks!
        </div>
    </PanelBody>
```

Stellen Sie sicher, dass Sie die aktualisierte Datei speichern.

## <a name="build-and-run-your-application"></a>Erstellen und Ausführen Ihrer Anwendung

Öffnen Sie eine Eingabeaufforderung in Ihrem Projektverzeichnis, um die nächsten Aufgaben auszuführen.

[!INCLUDE [node-js-yeoman-gulp-tasks](~/includes/tabs/node-js-yeoman-gulp-tasks.md)]

Um die Registerkartenkonfigurationsseite anzuzeigen, gehen Sie zu `https://localhost:3007/<yourDefaultAppNameTab>/config.html` . Folgendes sollte angezeigt werden:

![Screenshot der Konfigurationsseite](~/assets/images/tab-images/configurationPage.png)

## <a name="establish-a-secure-tunnel-to-your-tab"></a>Erstellen eines sicheren Tunnels zu Ihrer Registerkarte

Microsoft Teams ist ein vollständig cloudbasiertes Produkt und erfordert, dass Ihre Tab-Inhalte über HTTPS-Endpunkte in der Cloud verfügbar sind. Teams lokales Hosting nicht zulässt, müssen Sie daher entweder Ihre Registerkarte unter einer öffentlichen URL veröffentlichen oder einen Proxy verwenden, der Ihren lokalen Port für eine URL mit Internetverfügbarer verfügbar macht.

Um Ihre Tab-Erweiterung zu testen, verwenden Sie [ngrok](https://ngrok.com/docs), das in diese Anwendung integriert ist. Ngrok ist ein Reverse-Proxy-Softwaretool, das einen Tunnel zu den öffentlich verfügbaren HTTPS-Endpunkten des lokal ausgeführten Webservers erstellt. Die Webendpunkte Ihres Servers sind während der aktuellen Sitzung auf dem lokalen Computer verfügbar. Wenn die Maschine heruntergefahren wird oder in den Ruhezustand geht, ist der Dienst nicht mehr verfügbar.

Verlassen Sie localhost in Ihrer Eingabeaufforderung und geben Sie Folgendes ein:

```bash
gulp ngrok-serve
```

> [!IMPORTANT]
> Nachdem Ihre Registerkarte in Microsoft-Teams hochgeladen und erfolgreich gespeichert wurde, können Sie sie im Registerkartenkatalog anzeigen, zur Registerkartenleiste hinzufügen und mit ihr interagieren, bis Ihre ngrok-Tunnelsitzung endet. Wenn Sie Ihre ngrok-Sitzung neu starten, müssen Sie Ihre App mit der neuen URL aktualisieren.

## <a name="upload-your-application-to-teams"></a>Hochladen Ihre Anwendung auf Teams

- Öffnen Sie den Microsoft Teams Client. Wenn Sie die [webbasierte Version](https://teams.microsoft.com) verwenden, können Sie Ihren Front-End-Code mit den [Entwicklertools](~/tabs/how-to/developer-tools.md)Ihres Browsers überprüfen.
- Wählen Sie im Bedienfeld *"YourTeams"* auf der linken Seite das Menü neben dem Team aus, das `...` Sie zum Testen Ihrer Registerkarte verwenden, und wählen Sie Team **verwalten** aus.
- Wählen Sie im Hauptfenster **Apps** aus der Registerkartenleiste aus und wählen Sie **Hochladen eine benutzerdefinierte App** in der unteren rechten Ecke der Seite aus.
- Öffnen Sie Ihr Projektverzeichnis, navigieren Sie zum **Ordner ./package,** wählen Sie den Zip-Ordner des App-Pakets aus und wählen Sie **Öffnen** aus. Ihre Registerkarte wird in Teams hochgeladen.
- Kehren Sie zu Ihrem Team zurück, wählen Sie den Kanal aus, in dem Sie die Registerkarte anzeigen möchten, wählen Sie ➕ aus der Registerkartenleiste aus, und wählen Sie Ihre Registerkarte aus der Galerie aus.
- Folgen Sie den Anweisungen zum Hinzufügen einer Registerkarte. Beachten Sie, dass es ein benutzerdefiniertes Konfigurationsdialogfeld für Ihre Kanal-/Gruppenregisterkarte gibt.
- Wählen Sie **Speichern** aus, und Ihre Registerkarte wird der Registerkartenleiste des Kanals hinzugefügt.

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Erstellen einer benutzerdefinierten Kanal- und Gruppenregisterkarte mit ASP.NETCore](~/tabs/quickstarts/create-channel-group-tab-dotnet-core.md)