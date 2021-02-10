---
title: Erste Schritte – Erstellen einer persönlichen Registerkarte
author: heath-hamilton
description: Erstellen Sie mithilfe des Microsoft Teams Toolkits schnell eine persönliche Microsoft Teams-Registerkarte.
ms.author: lajanuar
ms.date: 11/03/2020
ms.topic: tutorial
ms.openlocfilehash: 083d1425fe43a9b150732aa35bef34e2349c6ea6
ms.sourcegitcommit: b99ed616db734371e4af4594b7e895c5b05737c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/09/2021
ms.locfileid: "50162901"
---
# <a name="build-a-personal-tab-for-microsoft-teams"></a>Erstellen einer persönlichen Registerkarte für Microsoft Teams

Registerkarten sind eine einfache Möglichkeit, Inhalte in Ihrer App anzuzeigen, indem Sie im Wesentlichen eine Webseite in Teams einbetten.

Es gibt zwei Arten von Registerkarten in Teams. In diesem Lernprogramm erstellen Sie eine einfache persönliche *Registerkarte,* eine Vollbildinhaltsseite für einzelne Benutzer. (Persönliche Registerkarten sind der traditionellen Websiteerfahrung in Teams am nächsten.)

## <a name="before-you-begin"></a>Bevor Sie beginnen

Für die ersten Schritte benötigen Sie eine einfache, ausgeführte persönliche Registerkarte. Wenn Sie nicht über eine verfügen, lesen Sie die Informationen zum [Erstellen und Ausführen Ihrer ersten Teams-App.](../build-your-first-app/build-and-run.md)

## <a name="your-assignment"></a>Ihre Zuordnung

Personen in Ihrer Organisation haben Probleme bei der Suche nach grundlegenden Kontaktinformationen für wichtige Funktionen (Helpdesk, Personalwesen usw.). Sie sind dafür verantwortlich, sicherzustellen, dass sie diese Informationen schnell an einem Ort finden können. Wie würden Sie das tun? Natürlich eine persönliche Registerkarte für Teams.

## <a name="what-youll-learn"></a>Was Sie lernen werden

> [!div class="checklist"]
>
> * Identifizieren einiger der für persönliche Registerkarten relevanten App-Konfigurationen und Gerüste
> * Erstellen von Registerkarteninhalten
> * Aktualisieren des Farbdesigns einer Registerkarte basierend auf den Benutzereinstellungen

## <a name="1-identify-relevant-app-project-components"></a>1. Identifizieren relevanter Komponenten des App-Projekts

Ein Teil der App-Konfigurationen und -Gerüste werden automatisch eingerichtet, wenn Sie Ihr Projekt mit dem Teams Toolkit erstellen. Sehen wir uns die Hauptkomponenten zum Erstellen einer persönlichen Registerkarte an.

### <a name="app-configurations"></a>App-Konfigurationen

Wechseln Sie im Toolkit zu **App Studio,** um Ihre App-Konfigurationen zu sehen und zu aktualisieren.

### <a name="app-scaffolding"></a>App-Gerüst

Das Gerüst der App enthält die Komponenten zum Rendern Ihrer persönlichen Registerkarte in Teams. Es gibt eine Menge, mit der Sie arbeiten können, aber derzeit müssen Sie sich nur auf Folgendes konzentrieren:

* `Tab.js` im Verzeichnis `src/components` Ihres Projekts. Dies ist für das Rendern ihrer Registerkarteninhaltsseite.
* Microsoft Teams JavaScript-Client-SDK, das vorab in den Front-End-Komponenten Ihres Projekts geladen wird.

## <a name="2-customize-your-tab-content-page"></a>2. Anpassen der Registerkarteninhaltsseite

Kompilieren Sie eine Liste wichtiger Kontakte in Ihrer Organisation. Kopieren und aktualisieren Sie den folgenden Codeausschnitt mit Informationen, die für Sie relevant sind, oder verwenden Sie den Code der Zeit nach wie vor.

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

Wechseln Sie zum `src/components` Verzeichnis, und öffnen Sie `Tab.js` . Suchen Sie die `render()` Funktion, und fügen Sie Ihren Inhalt `return()` ein (wie dargestellt).

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

Fügen Sie die folgende Regel hinzu, damit die E-Mail-Links unabhängig vom verwendeten `App.css` Design leichter zu lesen sind.

```CSS
a {
  color: inherit;
}
```

Speichern Sie Ihre Änderungen. Wechseln Sie zur Registerkarte Ihrer App in Teams, um die neuen Inhalte anzuzeigen.

:::image type="content" source="../assets/images/tabs/personal-tab-tutorial-content.png" alt-text="Screenshot einer persönlichen Registerkarte mit statischem Inhalt.":::

## <a name="3-update-the-tab-theme"></a>3. Aktualisieren des Registerkartendesigns

Gute Apps sind für Teams nativ. Daher ist es wichtig, dass Ihre Registerkarte mit dem von Ihren Benutzern bevorzugten Teams-Design kombiniert wird: Standard (hell), dunkel oder hoher Kontrast. Wie Sie vielleicht im letzten Screenshot bemerkt haben, hat Ihre Registerkarte immer noch einen hellen Hintergrund, wenn der Client das dunkle Design verwendet. Dies ist keine empfohlene Benutzeroberfläche.

Das [JavaScript-Client-SDK](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/?view=msteams-client-js-latest&preserve-view=true) für Teams kann Ihre App auf Designänderungen im Client aufmerksam machen und darauf reagieren. Hier erfahren Sie, wie Sie dies tun.

### <a name="get-context-about-the-teams-client"></a>Kontext zum Client "Teams" erhalten

In Ihrer Datei gibt es einen Aufruf, der einige Informationen zum konfigurierten `Tab.js` `microsoftTeams.getContext()` [`context`](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/context?view=msteams-client-js-latest&preserve-view=true) Clientdesign enthält. Verwenden Sie dank des Gerüsts der App diesen Code, um auf die `context` Benutzeroberfläche und deren Eigenschaften zu zugreifen.

```JavaScript
componentDidMount(){
  // Get the user context from Teams and set it in the state
  microsoftTeams.getContext((context, error) => {
    this.setState({
      context: context
    });
  });
  // Next steps: Error handling using the error object
}
```

### <a name="create-a-theme-change-handler"></a>Erstellen eines Designänderungshandlers

Mit den Eigenschaften in der Hand hat Ihre App ein solides Verständnis dafür, was in `context` Teams um sie herum passiert. Aber die App weiß immer noch nicht, dass ihre Darstellung das Design widerspiegeln sollte, das ein Benutzer aus wählt.

Sie benötigen einen Handler, damit sich der Zustand Ihrer App mit dem Design ändert. Fügen Sie den folgenden Designänderungshandler unmittelbar nach dem Aufruf `microsoftTeams.getContext()` ein.

```JavaScript
  microsoftTeams.registerOnThemeChangeHandler(theme => {
    if (theme !== this.state.theme) {
      this.setState({ theme });  
    }
  });
```

### <a name="match-theme-styles"></a>Übereinstimmung mit Designstilen

Ihr Designänderungshandler ist eingerichtet, Aber Sie benötigen Code, der auf diese Änderungen reagiert und die Farben Ihrer Registerkarte am aktuellen Design ausgerichtet.

> [!NOTE]
> Das folgende Beispiel ist nur eine Möglichkeit, Formatvorlagen auf Ihre Registerkarte anzuwenden. Verwenden Sie den Code so, wie er ist, erweitern Sie ihn, oder schreiben Sie Einen eigenen.

Speichern Sie in der Funktion den Zustand, der `render()` vom Designänderungshandler bereitgestellt wird, in `isTheme` .

```JavaScript
  const isTheme = this.state.theme
```

Nachdem Sie den vom Designänderungshandler bereitgestellten Status gespeichert haben, stellen Sie eine bedingte Logik bereit, um die Formatvorlagen Ihrer Registerkarte basierend auf dem aktuellen Design zu rendern. Das folgende Beispiel zeigt eine grundlegende Möglichkeit dazu:
1. Überprüfen Sie das aktuelle Design in `isTheme` .
2. Erstellen Sie `newTheme` ein Objekt mit CSS-Eigenschaften, die für das aktuelle Design relevant sind.
3. Wenden Sie das CSS auf das Stamm-HTML-Element ( ) des Registerkarteninhalts an. `<div style={newTheme}>`

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

Überprüfen Sie Ihre Registerkarte in Teams. Das Erscheinungsbild sollte eng mit dem dunklen Design übereinstimmen.

:::image type="content" source="../assets/images/tabs/personal-tab-tutorial-updated-theme.png" alt-text="Screenshot einer persönlichen Registerkarte mit statischer Inhaltsansicht.":::

## <a name="well-done"></a>Gut gemacht

Herzlichen Glückwunsch! Sie verfügen über eine Teams-App mit einer persönlichen Registerkarte, die die Suche nach wichtigen Kontakten in Ihrer Organisation erleichtert.

## <a name="learn-more"></a>Weitere Informationen

* Folgen Sie [unseren Entwurfsrichtlinien,](../tabs/design/tabs.md) und erstellen Sie mit [produktionsbereiten](../concepts/design/design-teams-app-ui-templates.md) Benutzeroberflächenvorlagen, um eine nahtlose Benutzeroberfläche zu erstellen.
* Informationen [zu mobilen Überlegungen](../tabs/design/tabs-mobile.md) für Registerkarten.
* [Fügen Sie ihrer Registerkarte die SSO-Authentifizierung hinzu.](../tabs/how-to/authentication/auth-aad-sso.md)
* Nutzen von Microsoft Teams-Daten [mit Microsoft Graph](https://docs.microsoft.com/graph/teams-concept-overview).
* [Erstellen Sie eine Registerkarte ohne das Toolkit.](../tabs/quickstarts/create-personal-tab-node-yeoman.md)

## <a name="next-lesson"></a>Nächste Lektion

Sie wissen, wie Sie eine Registerkarte für die persönliche Verwendung erstellen. Sehen wir uns an, was zum Erstellen einer Registerkarte für Teamkanäle und Chats benötigt wird.

> [!div class="nextstepaction"]
> [Erstellen einer Kanalregisterkarte](../build-your-first-app/build-channel-tab.md)
