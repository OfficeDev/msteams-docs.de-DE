---
title: Verwenden der Steuerelementbibliothek
description: Verwenden der von Microsoft Teams App Studio bereitgestellten Steuerelementbibliothek
keywords: Teams-App-Studio-Steuerelementbibliothek
ms.openlocfilehash: d817f55bd75216f77375b7848c5c32cbd29304c2
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674202"
---
# <a name="using-the-control-library-in-app-studio"></a>Verwenden der Steuerelementbibliothek in App Studio

[Microsoft Teams App Studio](~/get-started/get-started-app-studio.md) bietet Ihnen eine Reihe von Steuerelementen, die Sie in ihren eigenen Apps verwenden können. Diese Steuerelemente werden auf der Registerkarte *Steuerelementbibliothek* von App Studio bereitgestellt.

Diese Steuerelemente wurden von den Microsoft Teams-Designern erstellt, um Ihre eigenen Workflows zu rationalisieren, das Steuerungsverhalten zu standardisieren und die Standarddesigns des Support Teams zu standardisieren. Sie können diese Bibliothek in ihren eigenen Apps verwenden, um ein einheitliches Aussehen und Verhalten zu erzielen.

Zu den Steuerelementen gehören:

* Schaltflächen
* DropDowns
* Kontrollkästchen
* Optionsfelder
* Schaltet
* Test Bereiche
* Links
* Registerkarten
* Tabellen
* Symbole

## <a name="optionally-use-react-controls"></a>Optionales Verwenden von Reaktions Steuerelementen

Die vollständige Teams-Steuerelementbibliothek verwendet das [Reaktions JavaScript-UI-Framework](https://reactjs.org/) , wird jedoch so erstellt, dass Sie nicht an ein bestimmtes UI-Framework gebunden ist. Es gibt vier verschiedene NPM-Pakete:

* **msteams-UI-Styles-Core** Die wichtigsten CSS-Formatvorlagen von Benutzeroberflächenkomponenten. Es ist unabhängig von einem UI-Framework.
* **msteams-UI-Icons-Core** Die Hauptgruppen Symbole.
* **msteams-UI-Components-reagiere** Die Bindungs Bibliothek reagieren. Es hängt von msteams-UI-Styles-Core ab.
* **msteams-UI-Icons-reagiere** Die Reaktions Bindungs Bibliothek für die Gruppe von Teams-Symbolen. Es hängt von msteams-UI-Icons-Core ab.

Diese Bibliotheken sind alle Open Source, und Sie können msteams-UI-Styles-Core und msteams-UI-Icons-Core ohne Reaktion verwenden.

## <a name="adding-the-control-library"></a>Hinzufügen der Steuerelementbibliothek

Installieren der Steuerelementbibliothek und ihrer Peer `typestyle`Abhängigkeit:

```terminal
npm install --save typestyle && npm install --save msteams-ui-components-react
```

*Optional:* Installieren Sie die Teams-Symbole.

```terminal
npm install --save msteams-ui-icons-react
```

Suchen und öffnen `src/App.js` und ersetzen Sie den Inhalt durch den folgenden Code:

```javascript
import React, { Component } from ‘react’;
import { TeamsComponentContext, ThemeStyle, PrimaryButton } from ‘msteams-ui-components-react’

class App extends Component {
   render() {
      // Sets up the top-level context for the library. It accepts global
      // configurations such as font size and theme. fontSize is your page’s
      // default font size. We made it a parameter so that you could use this
      // library with CSS frameworks such as Bootstrap. Some CSS frameworks
      // set the default font size for the page; retrieve it and use it
      // instead of {16} in the block.
      // This library uses the power of CSS to do most of the work for you.
      // Instead of passing themes as a parameter to every UI component,
      // we set it on a parent HTML element. All HTML elements nested within
      // that parent will inherit these properties.

      return (
        <TeamsComponentContext
            fontSize={16}
            theme={ThemeStyle.Light}
        />
      );
   }
}
export default App;
```

Ausführen der App

```terminal
npm run start
```

Wenn Sie zu http://localhost:3000navigieren, sollte der folgende Bildschirm angezeigt werden:

<img width="530px" src="~/assets/images/get-started/control-library-button.png" title="Schaltfläche "Steuerelementbibliothek""/>

## <a name="dynamically-handling-theme-changes"></a>Dynamisches behandeln von Designänderungen

Ihre APP muss Designs behandeln, wenn:

* Die Registerkarte wird anfänglich geladen.
* Ein Benutzer ändert das Design, nachdem die Registerkarte bereits geladen wurde.

Das Design ist im [Kontext](/javascript/api/@microsoft/teams-js/context&view=msteams-client-js-latest)einer Registerkarte enthalten, die abgerufen werden kann, bevor die Registerkarte über URL-Platzhalterwerte geladen wird, oder jederzeit mithilfe des [Microsoft Teams-JavaScript-Client-SDK](/javascript/api/%40microsoft/teams-js/context).

Hier wird erläutert, wie das aktuelle Design abgerufen wird und wie auf Designänderungen geantwortet wird: [Kontext für Ihre Microsoft Teams-Registerkarte abrufen](~/concepts/tabs/tabs-context.md).

In diesem Beispielcode wird gezeigt, wie dies geschieht.

```js
componentWillMount() {
    // If you are deploying your site as a MS Teams static or configurable tab,
    // you should add “?theme={theme}” to your tabs URL in the manifest.
    // That way you will get the current theme before it’s loaded; getContext()
    // is called only after the tab is loaded, which will cause the tab to flash
    // if the current theme is different than the default.
    this.updateTheme(this.getQueryVariable('theme'));
    this.setState({
        fontSize: this.pageFontSize(),
    });

    // If you are not using the MS Teams Javascript SDK, you can remove this entire
    // if block, but if you want theme changes in the MS Teams client to propagate
    // to the tab, leave it here.
    microsoftTeams.initialize();
    microsoftTeams.registerOnThemeChangeHandler(this.updateTheme);
}
```

## <a name="connect-your-own-component-to-the-teamscomponentcontext"></a>Verbinden Ihrer eigenen Komponente mit dem TeamsComponentContext

Wenn Sie Ihren eigenen CSS-Code verwenden möchten, können Sie weiterhin auf Designänderungen reagieren und die von Microsoft Teams definierten Farben verwenden. TeamsComponentContext ermöglicht es Ihnen, dies zu tun.

Bearbeiten Sie die Datei erneut `src/App.js` , und ersetzen Sie den Inhalt durch den folgenden Code:

```javascript
import React, { Component } from ‘react’;
import { TeamsComponentContext, ThemeStyle, ConnectedComponent } from ‘msteams-ui-components-react’

class App extends Component {
    render() {
        return (
            <TeamsComponentContext
                fontSize={16}
                theme={ThemeStyle.HighContrast}>
                <MyComponent />
            </TeamsComponentContext>
        );
    }
}

class MyComponent extends Component {
    render() {
        return (
            <ConnectedComponent render={(props) => {
                const context = props.context;

                switch (context.style) {
                case ThemeStyle.Dark:
                    return <div style={{ color: context.colors.dark.brand00 }}>Dark theme!</div>;
                case ThemeStyle.HighContrast:
                    return <div style={{ color: context.colors.highContrast.black }}>High Contrast theme!</div>;
                case ThemeStyle.Light:
                    return <div style={{ color: context.colors.light.brand00 }}>Light theme!</div>;
                }
            }} />
        );
    }
}

export default App;
```

In diesem Code wird eine neue Komponente als MyComponent definiert. Anschließend wird eine spezielle Komponente aus der Steuerelementbibliothek namens ConnectedComponent hinzugefügt. ConnectedComponent verfügt über eine Eigenschaft `render` mit dem Namen, die eine Funktion als Parameter verwendet. Zum Zeitpunkt des Renderns wird diese Funktion mit dem entsprechenden Kontext für die Registerkarte aufgerufen. Der Kontext enthält das Design, in dem die Seite gerendert wird, sowie das globale Color-Objekt, das Sie verwenden können, um Microsoft Teams-Farben auf die Registerkarte anzuwenden. Wie Sie in der `switch` Anweisung sehen können, wird basierend `<div>` auf dem Design das entsprechende ausgewählt.

Um Designs zu ändern, müssen wir die TeamsComponentContext auf Stammebene mit einem anderen Design übergeben. Wenn sich ein Design ändert, werden alle untergeordneten Elemente, die in ConnectedComponent umbrochen werden, erneut gerendert. Siehe vorheriger Abschnitt "dynamisches behandeln von Designänderungen".

Es gibt andere Möglichkeiten, um Ihre Komponente mit TeamsComponentContext zu verbinden. Wenn Sie mit [redux](https://redux.js.org/basics/usage-with-react)vertraut sind, bevorzugen Sie möglicherweise das folgende Muster:

```js
import React, { Component } from ‘react’;
import { TeamsComponentContext, ThemeStyle, connectTeamsComponent } from ‘msteams-ui-components-react’

class App extends Component {
    render() {
        return (
            <TeamsComponentContext
                fontSize={16}
                theme={ThemeStyle.HighContrast}>
                <MyComponent />
            </TeamsComponentContext>
        );
    }
}

class MyComponentInner extends Component {
    render() {
        const context = this.props.context;
        switch (context.style) {
            case ThemeStyle.Dark:
                return <div style={{ color: context.colors.dark.brand00 }}>Dark theme!</div>;
            case ThemeStyle.HighContrast:
                return <div style={{ color: context.colors.highContrast.black }}>High Contrast theme!</div>;
            case ThemeStyle.Light:
                return <div style={{ color: context.colors.light.brand00 }}>Light theme!</div>;
        }
    }
}

const MyComponent = connectTeamsComponent(MyComponentInner);

export default App;
```

Verwenden Sie in dieser Methode anstelle von ConnectedComponent die connectTeamsComponent-Funktion. Die connectTeamsComponent-Funktion verwendet Ihre aktuelle Komponente und gibt eine neue Komponente zurück, wobei das Context-Objekt injiziert wird.

## <a name="next-steps"></a>Weitere Schritte

Wechseln Sie zu Teams App Studio, und schauen Sie sich alle Steuerelemente an, die wir anbieten, und Beispielcode für deren Verwendung. Vergessen Sie nicht, diese in verschiedenen Designs zu erkunden.