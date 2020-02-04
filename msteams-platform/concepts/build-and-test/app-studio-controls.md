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
# <a name="using-the-control-library-in-app-studio"></a><span data-ttu-id="e5e95-104">Verwenden der Steuerelementbibliothek in App Studio</span><span class="sxs-lookup"><span data-stu-id="e5e95-104">Using the control library in App Studio</span></span>

<span data-ttu-id="e5e95-105">[Microsoft Teams App Studio](~/get-started/get-started-app-studio.md) bietet Ihnen eine Reihe von Steuerelementen, die Sie in ihren eigenen Apps verwenden können.</span><span class="sxs-lookup"><span data-stu-id="e5e95-105">[Microsoft Teams App Studio](~/get-started/get-started-app-studio.md) provides you with a set of controls that you can use in your own apps.</span></span> <span data-ttu-id="e5e95-106">Diese Steuerelemente werden auf der Registerkarte *Steuerelementbibliothek* von App Studio bereitgestellt.</span><span class="sxs-lookup"><span data-stu-id="e5e95-106">These controls are provided in the *Control Library* tab of App Studio.</span></span>

<span data-ttu-id="e5e95-107">Diese Steuerelemente wurden von den Microsoft Teams-Designern erstellt, um Ihre eigenen Workflows zu rationalisieren, das Steuerungsverhalten zu standardisieren und die Standarddesigns des Support Teams zu standardisieren.</span><span class="sxs-lookup"><span data-stu-id="e5e95-107">These controls were created by the Microsoft Teams designers to streamline their own workflows, standardize control behavior and support Team's default themes.</span></span> <span data-ttu-id="e5e95-108">Sie können diese Bibliothek in ihren eigenen Apps verwenden, um ein einheitliches Aussehen und Verhalten zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="e5e95-108">You can use this library in your own apps to achieve a unified look and feel.</span></span>

<span data-ttu-id="e5e95-109">Zu den Steuerelementen gehören:</span><span class="sxs-lookup"><span data-stu-id="e5e95-109">Controls include:</span></span>

* <span data-ttu-id="e5e95-110">Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="e5e95-110">Buttons</span></span>
* <span data-ttu-id="e5e95-111">DropDowns</span><span class="sxs-lookup"><span data-stu-id="e5e95-111">Dropdowns</span></span>
* <span data-ttu-id="e5e95-112">Kontrollkästchen</span><span class="sxs-lookup"><span data-stu-id="e5e95-112">Checkboxes</span></span>
* <span data-ttu-id="e5e95-113">Optionsfelder</span><span class="sxs-lookup"><span data-stu-id="e5e95-113">Radio Buttons</span></span>
* <span data-ttu-id="e5e95-114">Schaltet</span><span class="sxs-lookup"><span data-stu-id="e5e95-114">Toggles</span></span>
* <span data-ttu-id="e5e95-115">Test Bereiche</span><span class="sxs-lookup"><span data-stu-id="e5e95-115">Test Areas</span></span>
* <span data-ttu-id="e5e95-116">Links</span><span class="sxs-lookup"><span data-stu-id="e5e95-116">Links</span></span>
* <span data-ttu-id="e5e95-117">Registerkarten</span><span class="sxs-lookup"><span data-stu-id="e5e95-117">Tabs</span></span>
* <span data-ttu-id="e5e95-118">Tabellen</span><span class="sxs-lookup"><span data-stu-id="e5e95-118">Tables</span></span>
* <span data-ttu-id="e5e95-119">Symbole</span><span class="sxs-lookup"><span data-stu-id="e5e95-119">Icons</span></span>

## <a name="optionally-use-react-controls"></a><span data-ttu-id="e5e95-120">Optionales Verwenden von Reaktions Steuerelementen</span><span class="sxs-lookup"><span data-stu-id="e5e95-120">Optionally use React controls</span></span>

<span data-ttu-id="e5e95-121">Die vollständige Teams-Steuerelementbibliothek verwendet das [Reaktions JavaScript-UI-Framework](https://reactjs.org/) , wird jedoch so erstellt, dass Sie nicht an ein bestimmtes UI-Framework gebunden ist.</span><span class="sxs-lookup"><span data-stu-id="e5e95-121">The full Teams control library uses the [React JavaScript UI framework](https://reactjs.org/) however it is built so that it is not tied to a specific UI framework.</span></span> <span data-ttu-id="e5e95-122">Es gibt vier verschiedene NPM-Pakete:</span><span class="sxs-lookup"><span data-stu-id="e5e95-122">There are four different npm packages:</span></span>

* <span data-ttu-id="e5e95-123">**msteams-UI-Styles-Core** Die wichtigsten CSS-Formatvorlagen von Benutzeroberflächenkomponenten.</span><span class="sxs-lookup"><span data-stu-id="e5e95-123">**msteams-ui-styles-core** The core CSS styles of UI components.</span></span> <span data-ttu-id="e5e95-124">Es ist unabhängig von einem UI-Framework.</span><span class="sxs-lookup"><span data-stu-id="e5e95-124">It’s independent of any UI framework.</span></span>
* <span data-ttu-id="e5e95-125">**msteams-UI-Icons-Core** Die Hauptgruppen Symbole.</span><span class="sxs-lookup"><span data-stu-id="e5e95-125">**msteams-ui-icons-core** The core set of Teams icons.</span></span>
* <span data-ttu-id="e5e95-126">**msteams-UI-Components-reagiere** Die Bindungs Bibliothek reagieren.</span><span class="sxs-lookup"><span data-stu-id="e5e95-126">**msteams-ui-components-react** The React binding library.</span></span> <span data-ttu-id="e5e95-127">Es hängt von msteams-UI-Styles-Core ab.</span><span class="sxs-lookup"><span data-stu-id="e5e95-127">It depends on msteams-ui-styles-core.</span></span>
* <span data-ttu-id="e5e95-128">**msteams-UI-Icons-reagiere** Die Reaktions Bindungs Bibliothek für die Gruppe von Teams-Symbolen.</span><span class="sxs-lookup"><span data-stu-id="e5e95-128">**msteams-ui-icons-react** The React binding library for the set of Teams icons.</span></span> <span data-ttu-id="e5e95-129">Es hängt von msteams-UI-Icons-Core ab.</span><span class="sxs-lookup"><span data-stu-id="e5e95-129">It depends on msteams-ui-icons-core.</span></span>

<span data-ttu-id="e5e95-130">Diese Bibliotheken sind alle Open Source, und Sie können msteams-UI-Styles-Core und msteams-UI-Icons-Core ohne Reaktion verwenden.</span><span class="sxs-lookup"><span data-stu-id="e5e95-130">These libraries are all open source, and you can use msteams-ui-styles-core and msteams-ui-icons-core without React.</span></span>

## <a name="adding-the-control-library"></a><span data-ttu-id="e5e95-131">Hinzufügen der Steuerelementbibliothek</span><span class="sxs-lookup"><span data-stu-id="e5e95-131">Adding the control library</span></span>

<span data-ttu-id="e5e95-132">Installieren der Steuerelementbibliothek und ihrer Peer `typestyle`Abhängigkeit:</span><span class="sxs-lookup"><span data-stu-id="e5e95-132">Install the control library and its peer dependency `typestyle`:</span></span>

```terminal
npm install --save typestyle && npm install --save msteams-ui-components-react
```

<span data-ttu-id="e5e95-133">*Optional:* Installieren Sie die Teams-Symbole.</span><span class="sxs-lookup"><span data-stu-id="e5e95-133">*Optional:* Install the Teams icons.</span></span>

```terminal
npm install --save msteams-ui-icons-react
```

<span data-ttu-id="e5e95-134">Suchen und öffnen `src/App.js` und ersetzen Sie den Inhalt durch den folgenden Code:</span><span class="sxs-lookup"><span data-stu-id="e5e95-134">Find and open `src/App.js` and replace its content with following code:</span></span>

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

<span data-ttu-id="e5e95-135">Ausführen der App</span><span class="sxs-lookup"><span data-stu-id="e5e95-135">Run the app</span></span>

```terminal
npm run start
```

<span data-ttu-id="e5e95-136">Wenn Sie zu http://localhost:3000navigieren, sollte der folgende Bildschirm angezeigt werden:</span><span class="sxs-lookup"><span data-stu-id="e5e95-136">When you navigate to http://localhost:3000, you should see the following screen:</span></span>

<img width="530px" src="~/assets/images/get-started/control-library-button.png" title="Schaltfläche "Steuerelementbibliothek""/>

## <a name="dynamically-handling-theme-changes"></a><span data-ttu-id="e5e95-138">Dynamisches behandeln von Designänderungen</span><span class="sxs-lookup"><span data-stu-id="e5e95-138">Dynamically handling theme changes</span></span>

<span data-ttu-id="e5e95-139">Ihre APP muss Designs behandeln, wenn:</span><span class="sxs-lookup"><span data-stu-id="e5e95-139">Your app needs to handle themes when:</span></span>

* <span data-ttu-id="e5e95-140">Die Registerkarte wird anfänglich geladen.</span><span class="sxs-lookup"><span data-stu-id="e5e95-140">The tab is initially loaded</span></span>
* <span data-ttu-id="e5e95-141">Ein Benutzer ändert das Design, nachdem die Registerkarte bereits geladen wurde.</span><span class="sxs-lookup"><span data-stu-id="e5e95-141">A user changes the theme after the tab is already loaded</span></span>

<span data-ttu-id="e5e95-142">Das Design ist im [Kontext](/javascript/api/@microsoft/teams-js/context&view=msteams-client-js-latest)einer Registerkarte enthalten, die abgerufen werden kann, bevor die Registerkarte über URL-Platzhalterwerte geladen wird, oder jederzeit mithilfe des [Microsoft Teams-JavaScript-Client-SDK](/javascript/api/%40microsoft/teams-js/context).</span><span class="sxs-lookup"><span data-stu-id="e5e95-142">The theme is included in a tab’s [Context](/javascript/api/@microsoft/teams-js/context&view=msteams-client-js-latest), which can be retrieved before the tab is loaded via URL placeholder values, or at any time by using the [Microsoft Teams JavaScript client SDK](/javascript/api/%40microsoft/teams-js/context).</span></span>

<span data-ttu-id="e5e95-143">Hier wird erläutert, wie das aktuelle Design abgerufen wird und wie auf Designänderungen geantwortet wird: [Kontext für Ihre Microsoft Teams-Registerkarte abrufen](~/concepts/tabs/tabs-context.md).</span><span class="sxs-lookup"><span data-stu-id="e5e95-143">How the current theme is retrieved and how to respond to theme changes is discussed here: [Get context for your Microsoft Teams tab](~/concepts/tabs/tabs-context.md).</span></span>

<span data-ttu-id="e5e95-144">In diesem Beispielcode wird gezeigt, wie dies geschieht.</span><span class="sxs-lookup"><span data-stu-id="e5e95-144">This sample code shows how this is done.</span></span>

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

## <a name="connect-your-own-component-to-the-teamscomponentcontext"></a><span data-ttu-id="e5e95-145">Verbinden Ihrer eigenen Komponente mit dem TeamsComponentContext</span><span class="sxs-lookup"><span data-stu-id="e5e95-145">Connect your own component to the TeamsComponentContext</span></span>

<span data-ttu-id="e5e95-146">Wenn Sie Ihren eigenen CSS-Code verwenden möchten, können Sie weiterhin auf Designänderungen reagieren und die von Microsoft Teams definierten Farben verwenden.</span><span class="sxs-lookup"><span data-stu-id="e5e95-146">If you want to use your own CSS code you can still respond to theme changes and use colors defined by teams.</span></span> <span data-ttu-id="e5e95-147">TeamsComponentContext ermöglicht es Ihnen, dies zu tun.</span><span class="sxs-lookup"><span data-stu-id="e5e95-147">TeamsComponentContext allows you to do this.</span></span>

<span data-ttu-id="e5e95-148">Bearbeiten Sie die Datei erneut `src/App.js` , und ersetzen Sie den Inhalt durch den folgenden Code:</span><span class="sxs-lookup"><span data-stu-id="e5e95-148">Once again, edit your `src/App.js` file and replace its content with following code:</span></span>

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

<span data-ttu-id="e5e95-149">In diesem Code wird eine neue Komponente als MyComponent definiert.</span><span class="sxs-lookup"><span data-stu-id="e5e95-149">In this code, a new component is defined called MyComponent.</span></span> <span data-ttu-id="e5e95-150">Anschließend wird eine spezielle Komponente aus der Steuerelementbibliothek namens ConnectedComponent hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="e5e95-150">Then a special component from the control library called ConnectedComponent is added.</span></span> <span data-ttu-id="e5e95-151">ConnectedComponent verfügt über eine Eigenschaft `render` mit dem Namen, die eine Funktion als Parameter verwendet.</span><span class="sxs-lookup"><span data-stu-id="e5e95-151">ConnectedComponent has a property called `render` which takes a function as a parameter.</span></span> <span data-ttu-id="e5e95-152">Zum Zeitpunkt des Renderns wird diese Funktion mit dem entsprechenden Kontext für die Registerkarte aufgerufen. Der Kontext enthält das Design, in dem die Seite gerendert wird, sowie das globale Color-Objekt, das Sie verwenden können, um Microsoft Teams-Farben auf die Registerkarte anzuwenden. Wie Sie in der `switch` Anweisung sehen können, wird basierend `<div>` auf dem Design das entsprechende ausgewählt.</span><span class="sxs-lookup"><span data-stu-id="e5e95-152">At render time this function will be called with the appropriate context for your tab. The context includes the theme that the page is being rendered in as well as the global color object that you can use to apply Teams colors to your tab. As you can see in the `switch` statement, the appropriate `<div>` is chosen based on the theme.</span></span>

<span data-ttu-id="e5e95-153">Um Designs zu ändern, müssen wir die TeamsComponentContext auf Stammebene mit einem anderen Design übergeben.</span><span class="sxs-lookup"><span data-stu-id="e5e95-153">To change themes, we need to pass the root-level TeamsComponentContext a different theme.</span></span> <span data-ttu-id="e5e95-154">Wenn sich ein Design ändert, werden alle untergeordneten Elemente, die in ConnectedComponent umbrochen werden, erneut gerendert.</span><span class="sxs-lookup"><span data-stu-id="e5e95-154">When a theme changes, all the child elements wrapped in ConnectedComponent will be re-rendered.</span></span> <span data-ttu-id="e5e95-155">Siehe vorheriger Abschnitt "dynamisches behandeln von Designänderungen".</span><span class="sxs-lookup"><span data-stu-id="e5e95-155">See previous section “Dynamically Handle Theme Changes.”</span></span>

<span data-ttu-id="e5e95-156">Es gibt andere Möglichkeiten, um Ihre Komponente mit TeamsComponentContext zu verbinden.</span><span class="sxs-lookup"><span data-stu-id="e5e95-156">There are other ways to connect your component to TeamsComponentContext.</span></span> <span data-ttu-id="e5e95-157">Wenn Sie mit [redux](https://redux.js.org/basics/usage-with-react)vertraut sind, bevorzugen Sie möglicherweise das folgende Muster:</span><span class="sxs-lookup"><span data-stu-id="e5e95-157">If you’re familiar with [Redux](https://redux.js.org/basics/usage-with-react), you may prefer the following pattern:</span></span>

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

<span data-ttu-id="e5e95-158">Verwenden Sie in dieser Methode anstelle von ConnectedComponent die connectTeamsComponent-Funktion.</span><span class="sxs-lookup"><span data-stu-id="e5e95-158">In this method, instead of using ConnectedComponent, you use the connectTeamsComponent function.</span></span> <span data-ttu-id="e5e95-159">Die connectTeamsComponent-Funktion verwendet Ihre aktuelle Komponente und gibt eine neue Komponente zurück, wobei das Context-Objekt injiziert wird.</span><span class="sxs-lookup"><span data-stu-id="e5e95-159">The connectTeamsComponent function takes your current component and returns a new component with the context object injected.</span></span>

## <a name="next-steps"></a><span data-ttu-id="e5e95-160">Weitere Schritte</span><span class="sxs-lookup"><span data-stu-id="e5e95-160">Next steps</span></span>

<span data-ttu-id="e5e95-161">Wechseln Sie zu Teams App Studio, und schauen Sie sich alle Steuerelemente an, die wir anbieten, und Beispielcode für deren Verwendung.</span><span class="sxs-lookup"><span data-stu-id="e5e95-161">Head to Teams App Studio and check out all the controls we offer and sample code of how to use them.</span></span> <span data-ttu-id="e5e95-162">Vergessen Sie nicht, diese in verschiedenen Designs zu erkunden.</span><span class="sxs-lookup"><span data-stu-id="e5e95-162">Don’t forget to explore them in different themes.</span></span>