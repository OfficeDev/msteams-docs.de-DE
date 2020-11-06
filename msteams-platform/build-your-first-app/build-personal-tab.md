---
title: Erste Schritte – Erstellen einer persönlichen Registerkarte
author: heath-hamilton
description: Erstellen Sie mit dem Microsoft Teams-Toolkit schnell eine persönliche Registerkarte von Microsoft Teams.
ms.author: lajanuar
ms.date: 11/03/2020
ms.topic: tutorial
ms.openlocfilehash: 17153b9b7cd7e6dd9052fc40073fec60a4d51f81
ms.sourcegitcommit: 99c35de7e2c604bd8bce392242c2c2fa709cd50b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/06/2020
ms.locfileid: "48931729"
---
# <a name="build-a-personal-tab-for-microsoft-teams"></a>Erstellen einer persönlichen Registerkarte für Microsoft Teams

Registerkarten stellen eine einfache Möglichkeit dar, Inhalte in Ihrer APP zu Oberflächen, indem eine Webseite im Wesentlichen in Microsoft Teams eingebettet wird.

Es gibt zwei Arten von Registerkarten in Microsoft Teams. In diesem Lernprogramm erstellen Sie grundlegende eine *persönliche Registerkarte* , eine voll Bildinhalts Seite für einzelne Benutzer. (Persönliche Registerkarten sind die nächste Sache einer herkömmlichen Website Erfahrung in Microsoft Teams.)

## <a name="before-you-begin"></a>Bevor Sie beginnen

Für die ersten Schritte benötigen Sie eine grundlegende ausgeführte persönliche Registerkarte. Wenn Sie noch keinen haben, lesen Sie [Erstellen und Ausführen ihrer ersten Teams-App](../build-your-first-app/build-and-run.md).

## <a name="your-assignment"></a>Ihre Zuordnung

Personen in Ihrer Organisation haben Probleme bei der Suche nach grundlegenden Kontaktinformationen für wichtige Funktionen (Helpdesk, HR usw.). Sie müssen sicherstellen, dass diese Informationen schnell an einer Stelle gefunden werden können. Wie würden Sie das tun? Eine persönliche Registerkarte Teams, natürlich.

## <a name="what-youll-learn"></a>Was Sie lernen

> [!div class="checklist"]
>
> * Identifizieren einiger der für persönliche Registerkarten relevanten App-Konfigurationen und Gerüste
> * Erstellen von Registerkarten Inhalten
> * Aktualisieren des Farbdesigns einer Registerkarte basierend auf der Benutzereinstellung

## <a name="1-identify-relevant-app-project-components"></a>1. Identifizieren der relevanten App-Projektkomponenten

Viele der APP-Konfigurationen und Gerüste werden automatisch eingerichtet, wenn Sie Ihr Projekt mit dem Teams-Toolkit erstellen. Lassen Sie uns die Hauptkomponenten für die Erstellung einer persönlichen Registerkarte betrachten.

### <a name="app-configurations"></a>App-Konfigurationen

Sie können Ihre APP-Konfigurationen mithilfe von App Studio anzeigen und aktualisieren, die im Toolkit enthalten ist.

Während des Setups hat das Toolkit zunächst die Inhaltsseite für Registerkarten konfiguriert, auf der Sie Ihren primären Inhalt anzeigen können. Wechseln Sie im Toolkit zu **App Studio** , und wählen Sie **Registerkarten** aus, um die Konfiguration anzuzeigen.

### <a name="app-scaffolding"></a>App-Gerüste

Das App-Gerüst stellt die Komponenten zum Rendern Ihrer persönlichen Registerkarte in Microsoft Teams bereit. Es gibt eine Menge, mit der Sie arbeiten können, aber im Moment müssen Sie sich nur auf Folgendes konzentrieren:

* `Tab.js` Datei im `src/components` Verzeichnis des Projekts. Dies dient zum Rendern Ihrer Registerkarteninhalts Seite.
* Microsoft Teams JavaScript-Client-SDK, das in den Front-End-Komponenten Ihres Projekts vorinstalliert ist.

## <a name="2-customize-your-tab-content-page"></a>2. Anpassen der Inhaltsseite der Registerkarte

Kompilieren Sie eine Liste wichtiger Kontakte in Ihrer Organisation. Kopieren Sie den folgenden Codeausschnitt, und aktualisieren Sie ihn mit Informationen, die für Sie relevant sind, oder verwenden Sie, um der Zeit Willen, den Code wie es ist.

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

Wechseln Sie zum `src/components` Verzeichnis, und öffnen Sie `Tab.js` . Suchen `render()` Sie die-Funktion, und fügen Sie den Inhalt in das Bild ein `return()` (siehe Abbildung).

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

Fügen Sie die folgende Regel hinzu, `App.css` damit die e-Mail-Links leichter lesbar sind, unabhängig davon, welches Design verwendet wird.

```CSS
a {
  color: inherit;
}
```

Speichern Sie Ihre Änderungen. Wechseln Sie zur Registerkarte ihrer app in Microsoft Teams, um den neuen Inhalt anzuzeigen.

:::image type="content" source="../assets/images/tabs/personal-tab-tutorial-content.png" alt-text="Screenshot einer persönlichen Registerkarte mit statischem Inhalt.":::

## <a name="3-update-the-tab-theme"></a>3. Aktualisieren des Registerkarten Designs

Gute apps fühlen sich nativ für Teams, daher ist es wichtig, dass Ihre Registerkarte mit dem Microsoft Teams-Design kombiniert wird, das Ihre Benutzer bevorzugen: Standard (hell), dunkel oder hoher Kontrast. Wie Sie vielleicht schon im letzten Screenshot bemerkt haben, hat ihre Registerkarte immer noch einen hellen Hintergrund, wenn der Client das dunkle Design verwendet. Dies ist keine empfohlene Benutzeroberfläche.

Das Microsoft [Teams-JavaScript-Client-SDK](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/?view=msteams-client-js-latest&preserve-view=true) kann Ihre APP auf Designänderungen im Client aufmerksam machen und darauf reagieren. Lassen Sie uns die Vorgehensweise durchgehen.

### <a name="get-context-about-the-teams-client"></a>Abrufen des Kontexts zum Microsoft Teams-Client

In Ihrer `Tab.js` Datei gibt es einen `microsoftTeams.getContext()` Anruf, [`context`](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/microsoftteams.context?view=msteams-client-js-latest&preserve-view=true) der einige Informationen zu dem konfigurierten Client Design enthält, unter anderem. Dank des App-Gerüsts verwenden Sie diesen Code wie für den Zugriff auf die `context` Schnittstelle und ihre Eigenschaften.

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

### <a name="create-a-theme-change-handler"></a>Erstellen eines Handlers für die Designänderung

Mit den `context` Eigenschaften in der Hand hat Ihre APP ein fundiertes Verständnis dessen, was in Microsoft Teams geschieht. Die APP weiß jedoch noch nicht, dass Ihr Aussehen das Design reflektieren sollte, das ein Benutzer auswählt.

Sie benötigen einen Handler, damit sich der Zustand Ihrer APP mit dem Design ändert. Fügen Sie den folgenden Design änderungshandler unmittelbar nach dem `microsoftTeams.getContext()` Aufruf ein.

```JavaScript
  microsoftTeams.registerOnThemeChangeHandler(theme => {
    if (theme !== this.state.theme) {
      this.setState({ theme });  
    }
  });
```

### <a name="match-theme-styles"></a>Zuordnen von Designstilen

Ihr Design änderungshandler ist vorhanden, aber Sie benötigen Code, der auf diese Änderungen reagiert und die Farben ihrer Registerkarten mit dem aktuellen Design ausrichtet.

> [!NOTE]
> Das folgende Beispiel ist nur eine Möglichkeit, wie Sie Formatvorlagen auf die Registerkarte anwenden können. Verwenden Sie den Code wie folgt, erweitern Sie ihn, oder schreiben Sie einen eigenen.

Speichern Sie den vom Design änderungshandler in bereitgestellten Zustand `isTheme` .

```JavaScript
  const isTheme = this.state.theme
```

Bereitstelleneiner bedingten Logik zum Rendern der Formatvorlagen ihrer Registerkarten basierend auf dem aktuellen Design. Das folgende Beispiel zeigt eine einfache Möglichkeit, dies zu tun, indem 1) das aktuelle Design in `isTheme` , 2) das Erstellen eines `newTheme` Objekts mit CSS-Eigenschaften, die für das aktuelle Design relevant sind, und 3) Überprüfen des CSS auf das HTML-Stammelement Ihres Registerkarteninhalts ( `<div>` ).

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

Überprüfen Sie Ihre Registerkarte in Microsoft Teams. Die Darstellung sollte eng mit dem dunklen Design übereinstimmen.

:::image type="content" source="../assets/images/tabs/personal-tab-tutorial-updated-theme.png" alt-text="Screenshot einer persönlichen Registerkarte mit statischer Inhaltsansicht.":::

## <a name="well-done"></a>Gut gemacht

Herzlichen Glückwunsch! Sie verfügen über eine Teams-App mit einer persönlichen Registerkarte, die es einfacher macht, wichtige Kontakte in Ihrer Organisation zu finden.

## <a name="learn-more"></a>Mehr erfahren

* [Authentifizieren von Registerkarten Benutzern mit SSO](../tabs/how-to/authentication/auth-aad-sso.md): Wenn Sie nur autorisierte Benutzer Ihrer Registerkarte anzeigen möchten, richten Sie einmaliges Anmelden (Single Sign-on, SSO) über Azure Active Directory (AD) ein.
* [Einbetten von Inhalten aus einer vorhandenen Web-App oder Webseite](../tabs/how-to/add-tab.md#tab-requirements): Wir haben gezeigt, wie Sie neue Inhalte für eine persönliche RegisterkarteErstellen, aber Sie können auch Inhalte aus einer externen URL laden.
* [Erstellen Sie eine nahtlose Benutzeroberfläche für Ihre Registerkarte](../tabs/design/tabs.md): Lesen Sie die empfohlenen Richtlinien für das Entwerfen von Microsoft Teams-Registerkarten.
* [Erstellen von Registerkarten für Mobilgeräte](../tabs/design/tabs-mobile.md): Hier erfahren Sie, wie Sie Registerkarten für Telefone und Tablets entwickeln.
* [Verwenden von Teams-Daten mit der Microsoft Graph-API](https://docs.microsoft.com/graph/teams-concept-overview)
* [Erstellen einer Registerkarte ohne Toolkit](../tabs/how-to/add-tab.md)

## <a name="next-lesson"></a>Nächste Lektion

Sie wissen, wie Sie eine Registerkarte zur persönlichen Verwendung erstellen. Schauen wir uns an, was es braucht, um eine Registerkarte für Team Kanäle und Chats zu erstellen.

> [!div class="nextstepaction"]
> [Erstellen einer Kanalregisterkarte](../build-your-first-app/build-channel-tab.md)
