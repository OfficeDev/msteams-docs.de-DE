---
title: Erste Schritte – Erstellen einer Kanal- und Gruppenregisterkarte
author: girliemac
description: Erstellen Sie schnell Microsoft Teams kanal- und gruppenregisterkarten mithilfe des Microsoft Teams Toolkits.
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

In diesem Lernprogramm lernen  Sie, eine einfache Kanalregisterkarte zu erstellen, die auch als Gruppenregisterkarte bezeichnet *wird.* Dabei handelt es sich um eine Vollbildseite für einen Teamkanal oder Chat. Sie können auch einige Aspekte dieser Art von Registerkarte konfigurieren, z. B. die Registerkarte umbenennen, damit sie für ihren Kanal sinnvoll ist, was sie in einer persönlichen Registerkarte nicht tun kann.

## <a name="what-youll-learn"></a>Was Sie lernen werden

* Erstellen Sie ein App-Projekt mit dem Microsoft Teams Toolkit für Visual Studio Code.
* Verstehen der App-Konfigurationen und des Gerüsts, die für Kanalregisterkarten relevant sind.
* Erstellen der Registerkarteninhalts- und Registerkartenkonfiguration.
* Erstellen und ausführen Sie Ihre App zu Testzwecken in Teams.

## <a name="prerequisites"></a>Voraussetzungen

Stellen Sie sicher, dass Sie verstehen, wie Sie eine einfache App Teams erstellen. Weitere Informationen finden Sie unter [Create your first Microsoft Teams "Hello, World!" app](../build-your-first-app/build-and-run.md).

## <a name="1-create-your-app-project"></a>1. Erstellen Ihres App-Projekts

Mit Microsoft Teams Toolkit können Sie Ihre App konfigurieren und das Gerüst einrichten, das für Kanal- und Gruppenregisterkarten relevant ist. Sie enthält auch eine grundlegende Konfigurationsseite und Inhaltsseite, auf der ein "Hello, World!" angezeigt wird. Nachricht.

**So erstellen Sie Ihr App-Projekt**

1. Wechseln Sie zu Visual Studio Code, und **wählen Microsoft Teams** auf der :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: linken Aktivitätsleiste aus.
1. Melden Sie sich mit Microsoft 365 Entwicklungskonto an, wenn Sie dazu aufgefordert werden.
1. Wählen Sie **auf dem Bildschirm** Projekt auswählen **JS** (JavaScript) unter **Kanal und Gruppen-App aus.**
1. Geben Sie einen Namen für Ihre Teams ein. 

    > [!NOTE]
    > Dies ist der Standardname für Ihre App und auch der Name des App-Projektverzeichnisses auf Ihrem lokalen Computer.

1. Wählen **Sie Gruppe oder Teams Kanalregisterkarte aus.**
1. Wählen **Sie unten** auf dem Bildschirm Fertig stellen aus, um Ihr Projekt zu konfigurieren und das Projekt auf dem lokalen Computer zu speichern.  

## <a name="2-understand-your-app-project-components"></a>2. Verstehen Ihrer App-Projektkomponenten

Viele der App-Konfigurationen und Gerüste werden automatisch eingerichtet, wenn Sie Ihr Projekt mit dem Toolkit erstellen. Sehen wir uns die Hauptkomponenten zum Erstellen einer Kanalregisterkarte an.

* **App-Konfigurationen:** Öffnen **Sie App Studio** im Toolkit, um Ihre App-Konfigurationen anzeigen und aktualisieren zu können.
* **App-Gerüst:** Das App-Gerüst stellt die Komponenten zum Rendern Ihrer Kanalregisterkarte in Teams. Es gibt eine Menge, mit der Sie arbeiten können, aber jetzt konzentrieren wir uns auf Folgendes:
  * Die Dateien im `src/components` Verzeichnis Ihres Projekts:
    * `Tab.js` zum Rendern der Inhaltsseite Ihrer Registerkarte.
    * `TabConfig.js` zum Rendern der Konfigurationsseite Ihrer Registerkarte.
  * Microsoft Teams JavaScript-Client-SDK, das in den Front-End-Komponenten Ihres Projekts vorinstalliert ist.

## <a name="3-customize-your-tab-content-page"></a>3. Anpassen der Registerkarteninhaltsseite

1. Kopieren und ändern Sie das folgende Codebeispiel mit Informationen, die für Ihre Organisation relevant sind. Sie können den Codeausschnitt auch wie folgt verwenden:
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
    
1. Wechseln Sie zum `src/components` Verzeichnis, und öffnen Sie die `Tab.js` Datei. Suchen Sie `render()` die Funktion, und fügen Sie Den Code `return()` ein, wie im folgenden Beispiel gezeigt:
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
    
1. Wechseln Sie zum Verzeichnis, und aktualisieren Sie die Datei mit dem folgenden Code, um die E-Mail-Links in allen verwendeten `src/components` `App.css` Designs leichter zu lesen:
    ```CSS
    a {
      color: inherit;
    }
    ```

## <a name="4-customize-your-tab-configuration-page"></a>4. Anpassen der Registerkartenkonfigurationsseite

Jede Registerkarte in einem Kanal oder Chat verfügt über eine Konfigurationsseite, eine modale Mit mindestens einer Setupoption, die angezeigt wird, wenn Benutzer Ihre App hinzufügen. Auf der Konfigurationsseite werden Benutzer standardmäßig gefragt, ob sie den Kanal oder Chat benachrichtigen möchten, wenn die Registerkarte installiert ist. Sie können die Konfigurationsseite anpassen, indem Sie benutzerdefinierten Inhalt hinzufügen.

Um benutzerdefinierten Inhalt hinzuzufügen, öffnen Sie die Datei aus dem Verzeichnis, und aktualisieren Sie den Platzhalterinhalt darin, wie `TabConfig.js` `src/components` im folgenden Beispiel `return()` gezeigt:

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
> Geben Sie auf dieser Seite eine kurze Information zu Ihrer App, da dies das erste Mal ist, dass Benutzer darüber lesen. Sie können auch benutzerdefinierte Konfigurationsoptionen oder einen [Authentifizierungsworkflow](../tabs/how-to/authentication/auth-aad-sso.md)hinzufügen, der auf Registerkartenkonfigurationsseiten üblich ist.

## <a name="5-customize-your-tab-name"></a>5. Anpassen des Registerkartennamens

Wenn Sie eine Kanalregisterkarte hinzufügen, wird der App-Name standardmäßig angezeigt, z. B. **first-app**. Sie können auch einen Namen bereitstellen, der im Kontext der Gruppenzusammenarbeit sinnvoller ist, z. B. **Teamkontakte**:

1. Wechseln Sie zum `src/components` Verzeichnis, und öffnen Sie die `TabConfig.js` Datei.
1. Fügen Sie die Eigenschaft mit dem Registerkartennamen hinzu, den Sie standardmäßig unter anzeigen `suggestedDisplayName` `microsoftTeams.settings.setSettings` möchten, wie im folgenden Beispiel gezeigt:

    ```JavaScript
        microsoftTeams.settings.setSettings({
        "contentUrl": "https://localhost:3000/tab",
        "suggestedDisplayName": "Team Contacts"
      });
      ```

## <a name="6-build-and-run-your-app"></a>6. Erstellen und Ausführen Ihrer App

In diesem Lernprogramm erfahren Sie, wie Sie Ihre App lokal erstellen und ausführen können. 

1. Wechseln Sie zum Stammverzeichnis Ihres App-Projekts im Terminal.
1. Führen Sie `npm install` aus.
1. Führen Sie `npm start` aus.

Diese Informationen finden Sie auch im `README` Abschnitt des Toolkits.
Ihre App wird nach `https://localhost:3000` dem erfolgreichen **Kompilierten ausgeführt!** wird im Terminal angezeigt. 

## <a name="7-sideload-your-app-in-teams"></a>7. Querladen Ihrer App in Teams

Ihre App ist bereit zum Testen in Teams. Dazu müssen Sie über ein Konto verfügen, das das Querladen von Apps zulässt. 

1. Öffnen Sie Teams web client in Visual Studio Code mit der **F5-Taste.**
1. Fügen Sie ( ) als vertrauenswürdig hinzu, indem Sie die folgenden Schritte ausführen, um die Anzeige von App-Inhalten `localhost` in Teams:

   1. Öffnen Sie eine neue Registerkarte im gleichen Browserfenster (Standardmäßig Google Chrome), das mit der **F5-Taste geöffnet** wurde.
   1. Öffnen `https://localhost:3000/tab` Sie die Seite, und fahren Sie mit der Seite fort.

1. Wählen **Sie Zu einem Team hinzufügen oder** **zu** einem Chat hinzufügen aus, und suchen Sie einen Kanal oder Chat, den Sie zum Testen über das modale In-Teams.
1. Wählen **Sie Tab einrichten aus.** Die Konfigurationsseite wird modal angezeigt.

   :::image type="content" source="../assets/images/tabs/channel-tab-tutorial-content.png" alt-text="Screenshot einer Kanalregisterkartenkonfigurationsseite.":::

1. Wählen **Sie Speichern** aus, um die Registerkarte zu konfigurieren. Die folgende Inhaltsseite wird angezeigt:

   :::image type="content" source="../assets/images/tabs/channel-tab-tutorial-content-installed.png" alt-text="Screenshot einer Kanalregisterkarte mit statischer Inhaltsansicht.":::

## <a name="see-also"></a>Siehe auch

* [Erstellen und Ausführen der ersten Microsoft Teams App](../build-your-first-app/build-and-run.md) 
* [Microsoft Teams JavaScript-Client-SDK](/javascript/api/@microsoft/teams-js/?view=msteams-client-js-latest&preserve-view=true)
* [Entwerfen Ihrer Registerkarte für Microsoft Teams Desktop und Web](../tabs/design/tabs.md) 
* [Entwerfen Ihrer Microsoft Teams-App mit Benutzeroberflächenvorlagen](../concepts/design/design-teams-app-ui-templates.md) 
* [Registerkarten auf mobilen Geräten](../tabs/design/tabs-mobile.md)
* [Unterstützung für einmaliges Anmelden (Single Sign-On, SSO) für Registerkarten](../tabs/how-to/authentication/auth-aad-sso.md)
* [Übersicht über Microsoft Teams-APIs](/graph/teams-concept-overview)
* [Erstellen Sie eine benutzerdefinierte persönliche Registerkarte mit Node.js und dem Yeoman Generator für Microsoft Teams](../tabs/quickstarts/create-personal-tab-node-yeoman.md)

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Erstellen eines Bots](../build-your-first-app/build-bot.md)

> [!div class="nextstepaction"]
> [Erstellen einer Messaging-Erweiterung](../build-your-first-app/build-messaging-extension.md)
