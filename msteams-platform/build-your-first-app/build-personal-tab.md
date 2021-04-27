---
title: Erste Schritte – Erstellen einer persönlichen Registerkarte
author: heath-hamilton
description: Erstellen Sie schnell eine persönliche Microsoft Teams-Registerkarte mithilfe des Microsoft Teams Toolkits.
ms.author: lajanuar
localization_priority: Normal
ms.date: 11/03/2020
ms.topic: tutorial
ms.openlocfilehash: dabe427142dd3e6a1d2f01f83601cbffd4a20dbd
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2021
ms.locfileid: "52019979"
---
# <a name="build-a-personal-tab-for-microsoft-teams"></a>Erstellen einer persönlichen Registerkarte für Microsoft Teams

Registerkarten sind eine einfache Möglichkeit, Inhalte in Ihrer App anzuzeigen, indem sie im Wesentlichen eine Webseite in Teams einbetten.

Es gibt zwei Arten von Registerkarten in Teams. In diesem Lernprogramm erstellen Sie eine einfache persönliche *Registerkarte*, eine Vollbildinhaltsseite für einzelne Benutzer. (Persönliche Registerkarten sind der herkömmlichen Websiteerfahrung in Teams am nächsten.)

## <a name="before-you-begin"></a>Bevor Sie beginnen

Für die ersten Schritte benötigen Sie eine einfache, ausgeführte persönliche Registerkarte. Wenn Sie nicht über eine verfügen, lesen Sie [Erstellen und Ausführen Ihrer ersten Teams-App](../build-your-first-app/build-and-run.md).

## <a name="your-assignment"></a>Ihre Zuordnung

Personen in Ihrer Organisation haben Probleme, grundlegende Kontaktinformationen für wichtige Funktionen (Helpdesk, Personalwesen usw.) zu finden. Sie sind dafür verantwortlich, sicherzustellen, dass diese Informationen schnell an einem Ort gefunden werden können. Wie würden Sie das tun? Natürlich eine persönliche Registerkarte für Teams.

## <a name="what-youll-learn"></a>Was Sie lernen werden

> [!div class="checklist"]
>
> * Identifizieren einiger der für persönliche Registerkarten relevanten App-Konfigurationen und Gerüste
> * Erstellen von Registerkarteninhalten
> * Aktualisieren des Farbdesigns einer Registerkarte basierend auf den Benutzereinstellungen

## <a name="1-identify-relevant-app-project-components"></a>1. Identifizieren relevanter App-Projektkomponenten

Viele der App-Konfigurationen und Gerüste werden automatisch eingerichtet, wenn Sie Ihr Projekt mit dem Teams Toolkit erstellen. Sehen wir uns die Hauptkomponenten zum Erstellen einer persönlichen Registerkarte an.

### <a name="app-configurations"></a>App-Konfigurationen

Wechseln Sie im Toolkit zu **App Studio,** um Ihre App-Konfigurationen zu sehen und zu aktualisieren.

### <a name="app-scaffolding"></a>App-Gerüst

Das App-Gerüst bietet die Komponenten zum Rendern Ihrer persönlichen Registerkarte in Teams. Es gibt eine Menge, mit der Sie arbeiten können, aber derzeit müssen Sie sich nur auf Folgendes konzentrieren:

* `Tab.js` datei im `src/components` Verzeichnis Ihres Projekts. Dies ist für das Rendern der Registerkarteninhaltsseite.
* Microsoft Teams JavaScript-Client-SDK, das in den Front-End-Komponenten Ihres Projekts vorinstalliert ist.

## <a name="2-customize-your-tab-content-page"></a>2. Anpassen der Registerkarteninhaltsseite

Kompilieren Sie eine Liste wichtiger Kontakte in Ihrer Organisation. Kopieren und aktualisieren Sie den folgenden Codeausschnitt mit Informationen, die für Sie relevant sind, oder verwenden Sie den Code aus Zeitgründen wie folgt.

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

Wechseln Sie zum `src/components` Verzeichnis, und öffnen Sie `Tab.js` . Suchen Sie die `render()` Funktion, und fügen Sie Den Inhalt ein `return()` (wie dargestellt).

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

Fügen Sie die folgende Regel hinzu, damit die E-Mail-Links unabhängig vom `App.css` verwendeten Design leichter zu lesen sind.

```CSS
a {
  color: inherit;
}
```

Speichern Sie Ihre Änderungen. Wechseln Sie zur Registerkarte Ihrer App in Teams, um die neuen Inhalte anzuzeigen.

:::image type="content" source="../assets/images/tabs/personal-tab-tutorial-content.png" alt-text="Screenshot einer persönlichen Registerkarte mit statischem Inhalt.":::

## <a name="3-update-the-tab-theme"></a>3. Aktualisieren des Registerkartendesigns

Gute Apps sind für Teams nativ. Daher ist es wichtig, dass Ihre Registerkarte mit dem von Ihren Benutzern bevorzugten Teams-Design kombiniert wird: Standard (hell), dunkel oder hoher Kontrast. Wie Sie vielleicht im letzten Screenshot bemerkt haben, hat Ihre Registerkarte immer noch einen hellen Hintergrund, wenn der Client das dunkle Design verwendet. Dies ist keine empfohlene Benutzeroberfläche.

Das [JavaScript-Client-SDK](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/?view=msteams-client-js-latest&preserve-view=true) von Teams kann Ihre App auf Designänderungen im Client aufmerksam machen und darauf reagieren. Gehen wir nun durch die Funktionsweise.

### <a name="get-context-about-the-teams-client"></a>Kontext zum Teams-Client erhalten

In Ihrer Datei gibt es einen Aufruf, der einige Informationen unter anderem zum konfigurierten `Tab.js` `microsoftTeams.getContext()` [`context`](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/context?view=msteams-client-js-latest&preserve-view=true) Clientdesign enthält. Verwenden Sie diesen Code dank des App-Gerüsts so, wie er für den Zugriff auf `context` die Schnittstelle und ihre Eigenschaften ist.

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

Mit den eigenschaften in der Hand hat Ihre App ein solides Verständnis davon, was um sie `context` herum in Teams passiert. Aber die App weiß immer noch nicht, dass ihre Darstellung das design widerspiegeln soll, das ein Benutzer wählt.

Sie benötigen einen Handler, damit sich der Zustand Ihrer App mit dem Design ändert. Fügen Sie den folgenden Designänderungshandler unmittelbar nach dem Aufruf `microsoftTeams.getContext()` ein.

```JavaScript
  microsoftTeams.registerOnThemeChangeHandler(theme => {
    if (theme !== this.state.theme) {
      this.setState({ theme });  
    }
  });
```

### <a name="match-theme-styles"></a>Übereinstimmung von Designformatvorlagen

Ihr Designänderungshandler ist eingerichtet, Sie benötigen jedoch Code, der auf diese Änderungen reagiert und die Farben Ihrer Registerkarte am aktuellen Design ausgerichtet.

> [!NOTE]
> Das folgende Beispiel ist nur eine Möglichkeit, Formatvorlagen auf Ihre Registerkarte anzuwenden. Verwenden Sie den Code wie folgt, erweitern Sie ihn, oder schreiben Sie Eigenes.

Speichern Sie `render()` in der Funktion den vom Designänderungshandler bereitgestellten Status in `isTheme` .

```JavaScript
  const isTheme = this.state.theme
```

Nachdem Sie den vom Designänderungshandler bereitgestellten Status gespeichert haben, stellen Sie eine bedingte Logik bereit, um die Formatvorlagen Ihrer Registerkarte basierend auf dem aktuellen Design zu rendern. Das folgende Beispiel zeigt eine grundlegende Möglichkeit dazu:
1. Überprüfen Sie das aktuelle Design in `isTheme` .
2. Erstellen Sie `newTheme` ein Objekt mit CSS-Eigenschaften, die für das aktuelle Design relevant sind.
3. Wenden Sie das CSS auf das Stamm-HTML-Element Ihres Registerkarteninhalts an ( `<div style={newTheme}>` ).

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

Glückwunsch! Sie verfügen über eine Teams-App mit einer persönlichen Registerkarte, die die Suche nach wichtigen Kontakten in Ihrer Organisation erleichtert.

## <a name="learn-more"></a>Weitere Informationen

* Befolgen Sie [unsere Entwurfsrichtlinien,](../tabs/design/tabs.md) und erstellen Sie mit [produktionsbereiten](../concepts/design/design-teams-app-ui-templates.md) Benutzeroberflächenvorlagen, um eine nahtlose Oberfläche zu erstellen.
* Informationen [zu mobilen Überlegungen](../tabs/design/tabs-mobile.md) für Registerkarten.
* [Fügen Sie ihrer Registerkarte die SSO-Authentifizierung hinzu.](../tabs/how-to/authentication/auth-aad-sso.md)
* Verwenden von Teams-Daten [mit Microsoft Graph](https://docs.microsoft.com/graph/teams-concept-overview).
* [Erstellen Sie eine Registerkarte ohne das Toolkit](../tabs/quickstarts/create-personal-tab-node-yeoman.md).

## <a name="next-lesson"></a>Nächste Lektion

Sie wissen, wie Sie eine Registerkarte für die persönliche Verwendung erstellen. Sehen wir uns an, was zum Erstellen einer Registerkarte für Teamkanäle und Chats benötigt wird.

> [!div class="nextstepaction"]
> [Erstellen einer Kanalregisterkarte](../build-your-first-app/build-channel-tab.md)
