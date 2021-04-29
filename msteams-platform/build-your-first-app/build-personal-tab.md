---
title: Erste Schritte – Erstellen einer persönlichen Registerkarte
author: girliemac
description: Erstellen Sie schnell eine persönliche Microsoft Teams-Registerkarte mithilfe des Microsoft Teams Toolkits.
ms.author: timura
ms.date: 03/16/2020
ms.topic: tutorial
ms.openlocfilehash: 05ef9913e338a54c7e6ebc301825b27d4bec9705
ms.sourcegitcommit: 303fc214aa04757779a171337f31a6539f47fd03
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/28/2021
ms.locfileid: "52068583"
---
# <a name="build-a-basic-personal-tab-for-microsoft-teams"></a>Erstellen einer einfachen persönlichen Registerkarte für Microsoft Teams

In diesem Lernprogramm lernen Sie, eine grundlegende persönliche Registerkarte in Microsoft Teams zu erstellen. Registerkarten sind eine einfache Möglichkeit, Informationen in Ihrer App durch Hosten von Webinhalten in Teams anzuzeigen. Registerkarten sind ein gängiges Feature von persönlichen Apps, die einen privaten Arbeitsbereich für einzelne Benutzer bereitstellen. Persönliche Registerkarten sind der herkömmlichen Weberfahrung in Teams am nächsten. 

## <a name="what-youll-learn"></a>Was Sie lernen werden

* Verstehen der App-Konfigurationen und des Gerüsts, die für persönliche Registerkarten relevant sind.
* Erstellen Sie einen Registerkarteninhalt mit einer Kontaktliste Ihrer Organisation.
* Aktualisieren sie das Farbdesign einer Registerkarte basierend auf den Benutzereinstellungen.

## <a name="prerequisites"></a>Voraussetzungen

Stellen Sie sicher, dass Sie wissen, wie Sie eine einfache Teams-App einrichten und erstellen. Weitere Informationen finden Sie unter [Erstellen Ihrer ersten Microsoft Teams "Hello, World!"-App.](../build-your-first-app/build-and-run.md)

## <a name="1-understand-your-app-project-components"></a>1. Verstehen ihrer App-Projektkomponenten

Nachdem Sie eine einfache persönliche Registerkarte erstellt haben, stellt das generierte App-Gerüst die Komponenten zum Rendern Ihrer persönlichen Registerkarte in Teams zur Seite. Es gibt eine Menge, mit der Sie arbeiten können, aber lassen Sie uns uns jetzt auf Folgendes konzentrieren: 

* `Tab.js` datei im `src/components` Verzeichnis Ihres Projekts. Dies ist für das Rendern der Registerkarteninhaltsseite.
* Microsoft Teams JavaScript-Client-SDK, das in den Front-End-Komponenten Ihres Projekts vorinstalliert ist.

Wie Sie im Abschnitt oben in der Datei feststellen können, verwendet der Beispielcode React , eine `import` `Tabs.js` Open-Source-JavaScript-Bibliothek [](https://reactjs.org/)zum Erstellen der Benutzeroberfläche. 

> [!NOTE]
> Obwohl die Verwendung von React _für_ die Teams-Entwicklung nicht erforderlich ist, werden Sie in diesem Lernprogramm mit React unterrichtet.

## <a name="2-customize-your-tab-content-page"></a>2. Anpassen der Registerkarteninhaltsseite

Sie können Ihre Registerkarteninhaltsseite anpassen, um eine Liste wichtiger Kontakte in Ihrer Organisation zu rendern. 

**So passen Sie ihre Registerkarteninhaltsseite an**

1. Kopieren und ändern Sie das folgende Codebeispiel mit Informationen, die für Sie relevant sind. Sie können den Code auch wie folgt verwenden: 
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
1. Zum `src/components` Verzeichnis, und öffnen Sie die `Tab.js` Datei. 
1. Wechseln Sie zu, und ersetzen Sie den Vorlagencode durch den darin geänderten `render()` `return()` Code, wie im folgenden Beispiel gezeigt:
    ```JavaScript
    render() {
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
1. Wechseln Sie zum Verzeichnis, und ändern Sie die Datei mit dem folgenden Code, um die E-Mail-Links mit jedem verwendeten Design `src/components` `App.css` leichter zu lesen:
    ```CSS
    a {
      color: inherit;
    }
    ```
1. Speichern Sie Ihre Änderungen. 

   Sie können die neuen Inhalte auf der Registerkarte Ihrer App in Teams anzeigen.

   :::image type="content" source="../assets/images/build-your-first-app/personal-tab-tutorial-content.png" alt-text="Screenshot einer persönlichen Registerkarte mit statischem Inhalt.":::

## <a name="3-update-your-tab-theme"></a>3. Aktualisieren Des Registerkartendesigns

Es ist wichtig, dass Ihre Registerkarte ein Design hat, das sich für Teams nativ anfühlt. Sie müssen Ihre Registerkarte mit dem Teams-Design vermischen. Ihre Benutzer bevorzugen in der Regel Standard-Designs (hell), dunkel oder mit hohem Kontrast. Wie Sie vielleicht im letzten Screenshot bemerkt haben, hat Ihre Registerkarte immer noch einen hellen Hintergrund, wenn Ihr Benutzer das dunkle Design verwendet. Dies ist keine empfohlene Benutzeroberfläche.

Das JavaScript-Client-SDK von Teams kann Ihre App auf Designänderungen im Client aufmerksam machen und darauf reagieren. Gehen Sie dazu wie folgt vor:

1. **Kontext zum konfigurierten Teams-Clientdesign erhalten** Der Aufruf in Ihrer Datei bietet einen Kontext zum konfigurierten Clientdesign (z. B. `microsoftTeams.getContext()` `Tab.js` dunkles Design). Der folgende Code zugrifft `context` auf die Schnittstelle und ihre Eigenschaften:

    ```JavaScript
    componentDidMount(){
      // Get the user context from Teams and set it in the state
      microsoftTeams.getContext((context, error) => {
        this.setState({
          context: context,
          theme: context.theme
        });
      });
    }
    ```
1. **Erstellen eines Designänderungshandlers** Mit den eigenschaften in der Hand hat Ihre App ein solides Verständnis davon, was um sie `context` herum in Teams passiert. Die App hat jedoch immer noch keine Darstellung, die das Design wiederspiegelt, wenn ein Benutzer sie aktualisiert.

   Sie benötigen einen Handler, um den Zustand Ihrer App mit dem Design zu aktualisieren. Um einen Handler zu erstellen, fügen Sie den folgenden Designänderungshandler unmittelbar nach dem Aufruf `microsoftTeams.getContext()` ein:

    ```JavaScript
    microsoftTeams.registerOnThemeChangeHandler(theme => {
    if (theme !== this.state.context.theme) {
    this.setState({
      context: {
      ...this.state.context,
      theme
      }
      })   
      }
    });
      ```
1. **Übereinstimmung mit den Designformatvorlagen** Ihr Designänderungshandler ist eingerichtet, Sie müssen jedoch weiterhin auf Änderungen reagieren und die Farben Ihrer Registerkarte am aktuellen Design ausrichten.

   Speichern Sie in der Funktion den vom Designänderungshandler bereitgestellten Status `render()` in `isTheme` :

    ```JavaScript
      const isTheme = this.state.context.theme
    ```
    
    > [!NOTE]
    > Dieses Beispiel ist nur eine Möglichkeit, Formatvorlagen auf Ihre Registerkarte anzuwenden. Verwenden Sie den Code wie folgt, erweitern Sie ihn, oder schreiben Sie Eigenes.

    Nachdem Sie den vom Designänderungshandler bereitgestellten Status gespeichert haben, stellen Sie die bedingte Logik bereit, um die Formatvorlagen Ihrer Registerkarte basierend auf dem aktuellen Design zu rendern. Das folgende Beispiel zeigt eine grundlegende Möglichkeit dazu:

    1. Wechseln Sie `render()` zu, und überprüfen Sie das aktuelle Design in `isTheme` .
    1. Erstellen Sie `newTheme` ein Objekt mit CSS-Eigenschaften, die für das aktuelle Design relevant sind.
    1. Wenden Sie das folgende CSS auf das Stamm-HTML-Element Ihres Registerkarteninhalts an ( `<div style={newTheme}>` ):

        ```JavaScript
         let newTheme
          if (isTheme === "default") {
            newTheme = {
              backgroundColor: "#EEF1F5",
              color: "#16233A"
            };
          } else {
            newTheme = {
              backgroundColor: "#2B2B30",
              color: "#FFFFFF"
            };
          }
        ```

       Überprüfen Sie Ihre Registerkarte in Teams. Das Erscheinungsbild entspricht nun eng mit dem dunklen Design.

       :::image type="content" source="../assets/images/build-your-first-app/personal-tab-tutorial-updated-theme.png" alt-text="Screenshot einer persönlichen Registerkarte mit statischer Inhaltsansicht.":::

## <a name="see-also"></a>Siehe auch

* [Microsoft Teams JavaScript-Client-SDK](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/?view=msteams-client-js-latest&preserve-view=true)
* [Entwerfen Ihrer Registerkarte für Microsoft Teams Desktop und Web](../tabs/design/tabs.md) 
* [Kontextschnittstelle](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/context?view=msteams-client-js-latest&preserve-view=true)
* [Entwerfen Ihrer Microsoft Teams-App mit Benutzeroberflächenvorlagen](../concepts/design/design-teams-app-ui-templates.md) 
* [Registerkarten auf mobilen Geräten](../tabs/design/tabs-mobile.md)
* [Unterstützung für einmaliges Anmelden (Single Sign-On, SSO) für Registerkarten](../tabs/how-to/authentication/auth-aad-sso.md)
* [Übersicht über Microsoft Teams-APIs](https://docs.microsoft.com/graph/teams-concept-overview)
* [Erstellen einer benutzerdefinierten persönlichen Registerkarte mit Node.js und dem Yeoman-Generator für Microsoft Teams](../tabs/quickstarts/create-personal-tab-node-yeoman.md)

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Erstellen einer Kanalregisterkarte](../build-your-first-app/build-channel-tab.md)