---
title: Erste Schritte - Erstellen eines Kanals und einer Gruppenregisterkarte
author: girliemac
description: Erstellen Sie schnell eine Microsoft Teams Kanal- und Gruppenregisterkarte mit dem Microsoft Teams Toolkit.
ms.author: timura
ms.date: 03/22/2020
ms.topic: tutorial
ms.openlocfilehash: ff9cfbfb7d099db52966f119add4ce8729929aa1
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566068"
---
# <a name="build-your-first-channel-and-group-tab-for-microsoft-teams"></a>Erstellen Sie Ihre erste Kanal- und Gruppenregisterkarte für Microsoft Teams

In diesem Tutorial lernen Sie an, eine grundlegende *Kanalregisterkarte* zu erstellen, die auch als *Gruppenregisterkarte* bezeichnet wird, die eine Vollbildseite für einen Teamkanal oder Chat ist. Sie können auch einige Aspekte dieser Art von Registerkarte konfigurieren, z. B. die Registerkarte umbenennen, sodass sie für ihren Kanal sinnvoll ist, was Sie in einer persönlichen Registerkarte nicht tun können.

## <a name="what-youll-learn"></a>Was Sie lernen werden

* Erstellen Sie ein App-Projekt mit dem Microsoft Teams Toolkit für Visual Studio Code.
* Verstehen Sie die App-Konfigurationen und Gerüste, die für Kanalregisterkarten relevant sind.
* Erstellen Sie Dentabinhalt und die Registerkartenkonfiguration.
* Erstellen und führen Sie Ihre App in Teams zum Testen aus.

## <a name="prerequisites"></a>Voraussetzungen

Stellen Sie sicher, dass Sie verstehen, wie Sie eine einfache Teams-App einrichten und erstellen. Weitere Informationen finden Sie [unter Erstellen Ihrer ersten Microsoft Teams "Hello, World!"-App](../build-your-first-app/build-and-run.md).

## <a name="1-create-your-app-project"></a>1. Erstellen Sie Ihr App-Projekt

Das Microsoft Teams Toolkit hilft Ihnen, Ihre App zu konfigurieren und das Gerüst einzurichten, das für Kanal- und Gruppenregisterkarten relevant ist. Es enthält auch eine grundlegende Konfigurationsseite und Inhaltsseite, die ein "Hallo, Welt!" anzeigt. Nachricht.

**So erstellen Sie Ihr App-Projekt**

1. Wechseln Sie zu Visual Studio Code und wählen Sie **Microsoft Teams** :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: auf der linken Aktivitätsleiste aus.
1. Melden Sie sich mit Ihrem Microsoft 365-Entwicklungskonto an, wenn Sie dazu aufgefordert werden.
1. Wählen Sie auf dem Bildschirm **Projekt** auswählen **JS** (JavaScript) unter **Kanal- und Gruppen-App** aus.
1. Geben Sie einen Namen für Ihre Teams App ein. 

    > [!NOTE]
    > Dies ist der Standardname für Ihre App und auch der Name des App-Projektverzeichnisses auf Ihrem lokalen Computer.

1. Wählen Sie **Gruppe oder Teams Kanalregisterkarte**.
1. Wählen Sie am unteren Bildschirmrand **fertig** aus, um das Projekt zu konfigurieren und das Projekt auf dem lokalen Computer zu speichern.  

## <a name="2-understand-your-app-project-components"></a>2. Verstehen Ihrer App-Projektkomponenten

Ein Großteil der App-Konfigurationen und Gerüste wird automatisch eingerichtet, wenn Sie Ihr Projekt mit dem Toolkit erstellen. Sehen wir uns die Hauptkomponenten zum Erstellen einer Kanalregisterkarte an.

* **App-Konfigurationen**: Öffnen Sie **App Studio** im Toolkit, um Ihre App-Konfigurationen anzuzeigen und zu aktualisieren.
* **App-Gerüst:** Das App-Gerüst stellt die Komponenten bereit, die zum Rendern der Kanalregisterkarte in Teams erforderlich sind. Es gibt eine Menge, mit dem Sie arbeiten können, aber jetzt konzentrieren wir uns auf Folgendes:
  * Die Dateien im `src/components` Verzeichnis Ihres Projekts:
    * `Tab.js` zum Rendern der Inhaltsseite Ihrer Registerkarte.
    * `TabConfig.js` zum Rendern der Konfigurationsseite Ihrer Registerkarte.
  * Microsoft Teams JavaScript Client SDK, das in den Front-End-Komponenten Ihres Projekts vorinstalliert ist.

## <a name="3-customize-your-tab-content-page"></a>3. Passen Sie Ihre Registerkarte Inhalt Seite

1. Kopieren und ändern Sie das folgende Codebeispiel mit Informationen, die für Ihre Organisation relevant sind. Sie können den Ausschnitt auch so verwenden, wie er ist:
    ```JSX
    <div>
      <h1>Important Contacts</h1>
        <ul>
          <li>Help Desk: <a href="mailto:support@company.com">support@company.com</a></li>
          <li>Human Resources: <a href="mailto:hr@company.com">hr@company.com</a></li>
          <li>Facilities: <a href="mailto:facilities@company.com">facilities@company.com</a></li>
        </ul>
    </div>
    ```
    
1. Wechseln Sie zum `src/components` Verzeichnis, und öffnen Sie die `Tab.js` Datei. Suchen Sie die `render()` Funktion, und fügen Sie den Code ein, `return()` wie im folgenden Beispiel gezeigt:
    ```JavaScript
    render() {

        let userName = Object.keys(this.state.context).length > 0 ? this.state.context['upn'] : "";

        return (
        <div>
          <h1>Important Contacts</h1>
            <ul>
              <li>Help Desk: <a href="mailto:support@company.com">support@company.com</a></li>
              <li>Human Resources: <a href="mailto:hr@company.com">hr@company.com</a></li>
              <li>Facilities: <a href="mailto:facilities@company.com">facilities@company.com</a></li>
            </ul>
        </div>
        );
    }
    ```
    
1. Wechseln Sie zum `src/components` Verzeichnis und aktualisieren Sie die Datei mit dem folgenden `App.css` Code, um die E-Mail-Links in jedem verwendeten Design leichter lesbar zu machen:
    ```CSS
    a {
      color: inherit;
    }
    ```

## <a name="4-customize-your-tab-configuration-page"></a>4. Passen Sie Ihre Registerkarte Konfigurationsseite an

Jede Registerkarte in einem Kanal oder Chat verfügt über eine Konfigurationsseite, ein Modal mit mindestens einer Setupoption, die angezeigt wird, wenn Benutzer Ihre App hinzufügen. Die Konfigurationsseite fragt Benutzer standardmäßig, ob sie den Kanal oder Chat benachrichtigen möchten, wenn die Registerkarte installiert ist. Sie können die Konfigurationsseite anpassen, indem Sie benutzerdefinierte Inhalte hinzufügen.

Um benutzerdefinierte Inhalte hinzuzufügen, öffnen Sie `TabConfig.js` die Datei aus dem `src/components` Verzeichnis, und aktualisieren Sie den Platzhalterinhalt innerhalb, `return()` wie im folgenden Beispiel gezeigt:

  ```JavaScript
  return (
      <div>
        <h1>Add My Contoso Contacts</h1>
        <div>
          Select <b>Save</b> to add our organization's important contacts to this workspace.
        </div>
      </div>
  );
  ```
 
> [!TIP]
> Geben Sie auf dieser Seite einen kurzen Überblick über Ihre App, da dies das erste Mal wäre, dass Benutzer darüber lesen. Sie können auch benutzerdefinierte Konfigurationsoptionen oder einen [Authentifizierungsworkflow](../tabs/how-to/authentication/auth-aad-sso.md)einschließen, der auf Registerkarten mit der Konfiguration der Registerkarten üblich ist.

## <a name="5-customize-your-tab-name"></a>5. Passen Sie Ihren Tab-Namen an

Wenn Sie eine Kanalregisterkarte hinzufügen, wird der App-Name standardmäßig angezeigt, z. **B. First-App**. Sie können auch einen Namen angeben, der im Kontext der Gruppenzusammenarbeit sinnvoller ist, z. B. **Teamkontakte:**

1. Wechseln Sie zum `src/components` Verzeichnis, und öffnen Sie die `TabConfig.js` Datei.
1. Fügen Sie die `suggestedDisplayName` Eigenschaft mit dem Tabnamen hinzu, den Sie standardmäßig unter anzeigen möchten, `microsoftTeams.settings.setSettings` wie im folgenden Beispiel gezeigt:

    ```JavaScript
        microsoftTeams.settings.setSettings({
        "contentUrl": "https://localhost:3000/tab",
        "suggestedDisplayName": "Team Contacts"
      });
      ```

## <a name="6-build-and-run-your-app"></a>6. Erstellen und Ausführen Ihrer App

In diesem Tutorial lernen Sie, Ihre App lokal zu erstellen und auszuführen. 

1. Wechseln Sie zum Stammverzeichnis Ihres App-Projekts in Terminal.
1. Führen Sie `npm install` aus.
1. Führen Sie `npm start` aus.

Diese Informationen finden Sie auch im `README` Abschnitt des Toolkits.
Ihre App wird `https://localhost:3000` nach dem **Kompilierten erfolgreich ausgeführt!** Meldung wird im Terminal angezeigt. 

## <a name="7-sideload-your-app-in-teams"></a>7. Sideload Ihre App in Teams

Ihre App kann in Teams getestet werden. Dazu benötigen Sie ein Konto, das das Sideloading von Apps ermöglicht. 

1. Öffnen Sie einen Teams Webclient in Visual Studio Code mit der **Taste F5.**
1. Fügen Sie ( ) als vertrauenswürdig hinzu, indem Sie `localhost` die folgenden Schritte ausführen, damit Ihre App-Inhalte in Teams angezeigt werden können:

   1. Öffnen Sie eine neue Registerkarte im gleichen Browserfenster (standardmäßig Google Chrome), die mit der **Taste F5** geöffnet wurde.
   1. Öffnen `https://localhost:3000/tab` Sie die Seite, und fahren Sie mit der Seite fort.

1. Wählen Sie **Hinzufügen zu einem Team** oder Hinzufügen zu einem **Chat** und Suchen eines Kanals oder Chats, den Sie zum Testen vom Modal in Teams verwenden können.
1. Wählen **Sie Registerkarte einrichten** aus. Die Konfigurationsseite wird in einem Modal angezeigt.

   :::image type="content" source="../assets/images/tabs/channel-tab-tutorial-content.png" alt-text="Screenshot einer Kanalregisterkartenkonfigurationsseite.":::

1. Wählen Sie **Speichern** aus, um die Registerkarte zu konfigurieren. Die folgende Inhaltsseite wird angezeigt:

   :::image type="content" source="../assets/images/tabs/channel-tab-tutorial-content-installed.png" alt-text="Screenshot einer Kanalregisterkarte mit statischer Inhaltsansicht.":::

## <a name="see-also"></a>Siehe auch

* [Erstellen und Ausführen Ihrer ersten Microsoft Teams-App](../build-your-first-app/build-and-run.md) 
* [Microsoft Teams JavaScript-Client-SDK](/javascript/api/@microsoft/teams-js/?view=msteams-client-js-latest&preserve-view=true)
* [Entwerfen der Registerkarte für Microsoft Teams Desktop und Web](../tabs/design/tabs.md) 
* [Entwerfen Ihrer Microsoft Teams-App mit UI-Vorlagen](../concepts/design/design-teams-app-ui-templates.md) 
* [Registerkarten auf mobilen Geräten](../tabs/design/tabs-mobile.md)
* [SSO-Unterstützung (Single Sign-On) für Registerkarten](../tabs/how-to/authentication/auth-aad-sso.md)
* [Übersicht über Microsoft Teams-APIs](/graph/teams-concept-overview)
* [Erstellen Sie eine benutzerdefinierte persönliche Registerkarte mit Node.js und dem Yeoman Generator für Microsoft Teams](../tabs/quickstarts/create-personal-tab-node-yeoman.md)

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Erstellen eines Bots](../build-your-first-app/build-bot.md)

> [!div class="nextstepaction"]
> [Erstellen einer Messaging-Erweiterung](../build-your-first-app/build-messaging-extension.md)
