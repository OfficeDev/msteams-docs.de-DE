---
title: Erste Schritte – Erstellen einer persönlichen Registerkarte
author: heath-hamilton
description: Erstellen Sie mithilfe des Microsoft Teams Toolkits schnell eine persönliche Microsoft Teams-Registerkarte.
ms.author: lajanuar
ms.date: 11/03/2020
ms.topic: tutorial
ms.openlocfilehash: 17263303207ffb5bee333f1ec0e655096b1062ee
ms.sourcegitcommit: 00c657e3bf57d3b92aca7da941cde47a2eeff4d0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/20/2021
ms.locfileid: "49911912"
---
# <a name="build-a-personal-tab-for-microsoft-teams"></a><span data-ttu-id="aa462-103">Erstellen einer persönlichen Registerkarte für Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="aa462-103">Build a personal tab for Microsoft Teams</span></span>

<span data-ttu-id="aa462-104">Registerkarten sind eine einfache Möglichkeit, Inhalte in Ihrer App anzuzeigen, indem Sie im Wesentlichen eine Webseite in Teams einbetten.</span><span class="sxs-lookup"><span data-stu-id="aa462-104">Tabs are a simple way to surface content in your app by essentially embedding a webpage in Teams.</span></span>

<span data-ttu-id="aa462-105">Es gibt zwei Arten von Registerkarten in Teams.</span><span class="sxs-lookup"><span data-stu-id="aa462-105">There are two types of tabs in Teams.</span></span> <span data-ttu-id="aa462-106">In diesem Lernprogramm erstellen Sie eine einfache persönliche *Registerkarte,* eine Vollbildinhaltsseite für einzelne Benutzer.</span><span class="sxs-lookup"><span data-stu-id="aa462-106">In this tutorial, you'll build basic a *personal tab*, a full-screen content page for individual users.</span></span> <span data-ttu-id="aa462-107">(Persönliche Registerkarten sind der traditionellen Websiteerfahrung in Teams am nächsten.)</span><span class="sxs-lookup"><span data-stu-id="aa462-107">(Personal tabs are the closest thing to a traditional website experience in Teams.)</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="aa462-108">Vorabinformationen</span><span class="sxs-lookup"><span data-stu-id="aa462-108">Before you begin</span></span>

<span data-ttu-id="aa462-109">Für die ersten Schritte benötigen Sie eine einfache, ausgeführte persönliche Registerkarte.</span><span class="sxs-lookup"><span data-stu-id="aa462-109">You need a basic running personal tab to get started.</span></span> <span data-ttu-id="aa462-110">Wenn Sie nicht über eine verfügen, lesen Sie die Informationen zum [Erstellen und Ausführen Ihrer ersten Teams-App.](../build-your-first-app/build-and-run.md)</span><span class="sxs-lookup"><span data-stu-id="aa462-110">If you don't have one, see [build and run your first Teams app](../build-your-first-app/build-and-run.md).</span></span>

## <a name="your-assignment"></a><span data-ttu-id="aa462-111">Ihre Zuordnung</span><span class="sxs-lookup"><span data-stu-id="aa462-111">Your assignment</span></span>

<span data-ttu-id="aa462-112">Personen in Ihrer Organisation haben Probleme bei der Suche nach grundlegenden Kontaktinformationen für wichtige Funktionen (Helpdesk, Personalwesen usw.).</span><span class="sxs-lookup"><span data-stu-id="aa462-112">People in your organization have trouble finding basic contact information for important functions (help desk, HR, etc.).</span></span> <span data-ttu-id="aa462-113">Sie sind dafür verantwortlich, sicherzustellen, dass sie diese Informationen schnell an einem Ort finden können.</span><span class="sxs-lookup"><span data-stu-id="aa462-113">You're in charge of making sure they can quickly find this information in one place.</span></span> <span data-ttu-id="aa462-114">Wie würden Sie das tun?</span><span class="sxs-lookup"><span data-stu-id="aa462-114">How would you do that?</span></span> <span data-ttu-id="aa462-115">Natürlich eine persönliche Registerkarte für Teams.</span><span class="sxs-lookup"><span data-stu-id="aa462-115">A Teams personal tab, of course.</span></span>

## <a name="what-youll-learn"></a><span data-ttu-id="aa462-116">Was Sie lernen werden</span><span class="sxs-lookup"><span data-stu-id="aa462-116">What you'll learn</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="aa462-117">Identifizieren einiger der für persönliche Registerkarten relevanten App-Konfigurationen und Gerüste</span><span class="sxs-lookup"><span data-stu-id="aa462-117">Identify some of the app configurations and scaffolding relevant to personal tabs</span></span>
> * <span data-ttu-id="aa462-118">Erstellen von Registerkarteninhalten</span><span class="sxs-lookup"><span data-stu-id="aa462-118">Create tab content</span></span>
> * <span data-ttu-id="aa462-119">Aktualisieren des Farbdesigns einer Registerkarte basierend auf den Benutzereinstellungen</span><span class="sxs-lookup"><span data-stu-id="aa462-119">Update a tab's color theme based on user preference</span></span>

## <a name="1-identify-relevant-app-project-components"></a><span data-ttu-id="aa462-120">1. Identifizieren relevanter Komponenten des App-Projekts</span><span class="sxs-lookup"><span data-stu-id="aa462-120">1. Identify relevant app project components</span></span>

<span data-ttu-id="aa462-121">Ein Teil der App-Konfigurationen und -Gerüste werden automatisch eingerichtet, wenn Sie Ihr Projekt mit dem Teams Toolkit erstellen.</span><span class="sxs-lookup"><span data-stu-id="aa462-121">Much of the app configurations and scaffolding are set up automatically when you create your project with the Teams Toolkit.</span></span> <span data-ttu-id="aa462-122">Sehen wir uns die Hauptkomponenten zum Erstellen einer persönlichen Registerkarte an.</span><span class="sxs-lookup"><span data-stu-id="aa462-122">Let's look at the main components for building a personal tab.</span></span>

### <a name="app-configurations"></a><span data-ttu-id="aa462-123">App-Konfigurationen</span><span class="sxs-lookup"><span data-stu-id="aa462-123">App configurations</span></span>

<span data-ttu-id="aa462-124">Wechseln Sie im Toolkit zu **App Studio,** um Ihre App-Konfigurationen zu sehen und zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="aa462-124">In the toolkit, go to **App Studio** to view and update your app configurations.</span></span>

### <a name="app-scaffolding"></a><span data-ttu-id="aa462-125">App-Gerüst</span><span class="sxs-lookup"><span data-stu-id="aa462-125">App scaffolding</span></span>

<span data-ttu-id="aa462-126">Das Gerüst der App enthält die Komponenten zum Rendern Ihrer persönlichen Registerkarte in Teams.</span><span class="sxs-lookup"><span data-stu-id="aa462-126">The app scaffolding provides the components for rendering your personal tab in Teams.</span></span> <span data-ttu-id="aa462-127">Es gibt eine Menge, mit der Sie arbeiten können, aber derzeit müssen Sie sich nur auf Folgendes konzentrieren:</span><span class="sxs-lookup"><span data-stu-id="aa462-127">There's a lot you can work with, but for now you only need to focus on the following:</span></span>

* <span data-ttu-id="aa462-128">`Tab.js` im Verzeichnis `src/components` Ihres Projekts.</span><span class="sxs-lookup"><span data-stu-id="aa462-128">`Tab.js` file in the `src/components` directory of your project.</span></span> <span data-ttu-id="aa462-129">Dies ist für das Rendern der Registerkarteninhaltsseite.</span><span class="sxs-lookup"><span data-stu-id="aa462-129">This is for rendering your tab content page.</span></span>
* <span data-ttu-id="aa462-130">Microsoft Teams JavaScript-Client-SDK, das vorab in den Front-End-Komponenten Ihres Projekts geladen wird.</span><span class="sxs-lookup"><span data-stu-id="aa462-130">Microsoft Teams JavaScript client SDK, which comes pre-loaded in your project's front-end components.</span></span>

## <a name="2-customize-your-tab-content-page"></a><span data-ttu-id="aa462-131">2. Anpassen der Registerkarteninhaltsseite</span><span class="sxs-lookup"><span data-stu-id="aa462-131">2. Customize your tab content page</span></span>

<span data-ttu-id="aa462-132">Kompilieren Sie eine Liste wichtiger Kontakte in Ihrer Organisation.</span><span class="sxs-lookup"><span data-stu-id="aa462-132">Compile a list of important contacts in your organization.</span></span> <span data-ttu-id="aa462-133">Kopieren und aktualisieren Sie den folgenden Codeausschnitt mit Informationen, die für Sie relevant sind, oder verwenden Sie den Code der Zeit nach belieben.</span><span class="sxs-lookup"><span data-stu-id="aa462-133">Copy and update the following snippet with information that's relevant to you or, for the sake of time, use the code as is.</span></span>

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

<span data-ttu-id="aa462-134">Wechseln Sie zum `src/components` Verzeichnis, und öffnen Sie `Tab.js` .</span><span class="sxs-lookup"><span data-stu-id="aa462-134">Go to the `src/components` directory and open `Tab.js`.</span></span> <span data-ttu-id="aa462-135">Suchen Sie die `render()` Funktion, und fügen Sie Ihren Inhalt `return()` ein (wie dargestellt).</span><span class="sxs-lookup"><span data-stu-id="aa462-135">Locate the `render()` function and paste your content inside `return()` (as shown).</span></span>

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

<span data-ttu-id="aa462-136">Fügen Sie die folgende Regel hinzu, damit die E-Mail-Links unabhängig vom verwendeten `App.css` Design leichter zu lesen sind.</span><span class="sxs-lookup"><span data-stu-id="aa462-136">Add the following rule to `App.css` so the email links are easier to read no matter which theme is used.</span></span>

```CSS
a {
  color: inherit;
}
```

<span data-ttu-id="aa462-137">Speichern Sie Ihre Änderungen.</span><span class="sxs-lookup"><span data-stu-id="aa462-137">Save your changes.</span></span> <span data-ttu-id="aa462-138">Wechseln Sie zur Registerkarte Ihrer App in Teams, um die neuen Inhalte anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="aa462-138">Go to your app's tab in Teams to view the new content.</span></span>

:::image type="content" source="../assets/images/tabs/personal-tab-tutorial-content.png" alt-text="Screenshot einer persönlichen Registerkarte mit statischem Inhalt.":::

## <a name="3-update-the-tab-theme"></a><span data-ttu-id="aa462-140">3. Aktualisieren des Registerkartendesigns</span><span class="sxs-lookup"><span data-stu-id="aa462-140">3. Update the tab theme</span></span>

<span data-ttu-id="aa462-141">Gute Apps sind für Teams nativ. Daher ist es wichtig, dass Ihre Registerkarte mit dem von Ihren Benutzern bevorzugten Teams-Design kombiniert wird: Standard (hell), dunkel oder hoher Kontrast.</span><span class="sxs-lookup"><span data-stu-id="aa462-141">Good apps feel native to Teams, so it's important your tab blends with the Teams theme your users prefer: default (light), dark, or high contrast.</span></span> <span data-ttu-id="aa462-142">Wie Sie vielleicht im letzten Screenshot bemerkt haben, hat Ihre Registerkarte immer noch einen hellen Hintergrund, wenn der Client das dunkle Design verwendet.</span><span class="sxs-lookup"><span data-stu-id="aa462-142">As you might have noticed in the last screenshot, your tab still has a light background when the client's using the dark theme.</span></span> <span data-ttu-id="aa462-143">Dies ist keine empfohlene Benutzeroberfläche.</span><span class="sxs-lookup"><span data-stu-id="aa462-143">This is not a recommended user experience.</span></span>

<span data-ttu-id="aa462-144">Das [JavaScript-Client-SDK](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/?view=msteams-client-js-latest&preserve-view=true) für Teams kann Ihre App auf Designänderungen im Client aufmerksam machen und darauf reagieren.</span><span class="sxs-lookup"><span data-stu-id="aa462-144">The [Teams JavaScript client SDK](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/?view=msteams-client-js-latest&preserve-view=true) can make your app aware of and react to theme changes in the client.</span></span> <span data-ttu-id="aa462-145">Hier erfahren Sie, wie Sie dies tun.</span><span class="sxs-lookup"><span data-stu-id="aa462-145">Let's walk through how to do this.</span></span>

### <a name="get-context-about-the-teams-client"></a><span data-ttu-id="aa462-146">Kontext zum Client "Teams" erhalten</span><span class="sxs-lookup"><span data-stu-id="aa462-146">Get context about the Teams client</span></span>

<span data-ttu-id="aa462-147">In Ihrer Datei gibt es einen Aufruf, der einige Informationen zum konfigurierten `Tab.js` `microsoftTeams.getContext()` [`context`](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/context?view=msteams-client-js-latest&preserve-view=true) Clientdesign enthält.</span><span class="sxs-lookup"><span data-stu-id="aa462-147">In your `Tab.js` file, there's a `microsoftTeams.getContext()` call that provides some [`context`](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/context?view=msteams-client-js-latest&preserve-view=true) about, among other details, the configured client theme.</span></span> <span data-ttu-id="aa462-148">Verwenden Sie diesen Code dank des App-Gerüsts, um auf die `context` Benutzeroberfläche und deren Eigenschaften zu zugreifen.</span><span class="sxs-lookup"><span data-stu-id="aa462-148">Thanks to the app scaffolding, use this code as is to access the `context` interface and its properties.</span></span>

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

### <a name="create-a-theme-change-handler"></a><span data-ttu-id="aa462-149">Erstellen eines Designänderungshandlers</span><span class="sxs-lookup"><span data-stu-id="aa462-149">Create a theme change handler</span></span>

<span data-ttu-id="aa462-150">Mit den Eigenschaften in der Hand hat Ihre App ein solides Verständnis dafür, was in `context` Teams um sie herum passiert.</span><span class="sxs-lookup"><span data-stu-id="aa462-150">With the `context` properties in hand, your app has a solid understanding of what's happening around it in Teams.</span></span> <span data-ttu-id="aa462-151">Aber die App weiß immer noch nicht, dass ihre Darstellung das Design widerspiegeln sollte, das ein Benutzer aus wählt.</span><span class="sxs-lookup"><span data-stu-id="aa462-151">But the app still doesn't know its appearance should reflect whatever theme a user chooses.</span></span>

<span data-ttu-id="aa462-152">Sie benötigen einen Handler, damit sich der Zustand Ihrer App mit dem Design ändert.</span><span class="sxs-lookup"><span data-stu-id="aa462-152">You need a handler so that your app's state changes with the theme.</span></span> <span data-ttu-id="aa462-153">Fügen Sie den folgenden Designänderungshandler unmittelbar nach dem Aufruf `microsoftTeams.getContext()` ein.</span><span class="sxs-lookup"><span data-stu-id="aa462-153">Insert the following theme change handler immediately after the `microsoftTeams.getContext()` call.</span></span>

```JavaScript
  microsoftTeams.registerOnThemeChangeHandler(theme => {
    if (theme !== this.state.theme) {
      this.setState({ theme });  
    }
  });
```

### <a name="match-theme-styles"></a><span data-ttu-id="aa462-154">Übereinstimmung mit Designstilen</span><span class="sxs-lookup"><span data-stu-id="aa462-154">Match theme styles</span></span>

<span data-ttu-id="aa462-155">Ihr Designänderungshandler ist eingerichtet, Aber Sie benötigen Code, der auf diese Änderungen reagiert und die Farben Ihrer Registerkarte am aktuellen Design ausgerichtet.</span><span class="sxs-lookup"><span data-stu-id="aa462-155">Your theme change handler is in place, but you need some code that responds to those changes and aligns your tab's colors with the current theme.</span></span>

> [!NOTE]
> <span data-ttu-id="aa462-156">Das folgende Beispiel ist nur eine Möglichkeit, Formatvorlagen auf Ihre Registerkarte anzuwenden. Verwenden Sie den Code so, wie er ist, erweitern Sie ihn, oder schreiben Sie Ihren eigenen Code.</span><span class="sxs-lookup"><span data-stu-id="aa462-156">The following example is just one way you might apply styles to your tab. Use the code as is, expand on it, or write your own.</span></span>

<span data-ttu-id="aa462-157">Speichern Sie in der Funktion den Zustand, der `render()` vom Designänderungshandler bereitgestellt wird, in `isTheme` .</span><span class="sxs-lookup"><span data-stu-id="aa462-157">In the `render()` function, store the state provided by the theme change handler in `isTheme`.</span></span>

```JavaScript
  const isTheme = this.state.theme
```

<span data-ttu-id="aa462-158">Nachdem Sie den vom Designänderungshandler bereitgestellten Status gespeichert haben, stellen Sie eine bedingte Logik bereit, um die Formatvorlagen Ihrer Registerkarte basierend auf dem aktuellen Design zu rendern.</span><span class="sxs-lookup"><span data-stu-id="aa462-158">After storing the state provided by the theme change handler, provide some conditional logic to render your tab's styles based on the current theme.</span></span> <span data-ttu-id="aa462-159">Das folgende Beispiel zeigt eine grundlegende Möglichkeit dazu:</span><span class="sxs-lookup"><span data-stu-id="aa462-159">The following example shows a basic way to do this:</span></span>
1. <span data-ttu-id="aa462-160">Überprüfen Sie das aktuelle Design in `isTheme` .</span><span class="sxs-lookup"><span data-stu-id="aa462-160">Check the current theme in `isTheme`.</span></span>
2. <span data-ttu-id="aa462-161">Erstellen Sie `newTheme` ein Objekt mit CSS-Eigenschaften, die für das aktuelle Design relevant sind.</span><span class="sxs-lookup"><span data-stu-id="aa462-161">Create a `newTheme` object with CSS properties relevant to the current theme.</span></span>
3. <span data-ttu-id="aa462-162">Wenden Sie das CSS auf das Stamm-HTML-Element ( ) des Registerkarteninhalts an. `<div>`</span><span class="sxs-lookup"><span data-stu-id="aa462-162">Apply the CSS to your tab content's root HTML element (`<div>`).</span></span>

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

<span data-ttu-id="aa462-163">Überprüfen Sie Ihre Registerkarte in Teams.</span><span class="sxs-lookup"><span data-stu-id="aa462-163">Check your tab in Teams.</span></span> <span data-ttu-id="aa462-164">Das Erscheinungsbild sollte eng mit dem dunklen Design übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="aa462-164">The appearance should closely match the dark theme.</span></span>

:::image type="content" source="../assets/images/tabs/personal-tab-tutorial-updated-theme.png" alt-text="Screenshot einer persönlichen Registerkarte mit statischer Inhaltsansicht.":::

## <a name="well-done"></a><span data-ttu-id="aa462-166">Gut gemacht</span><span class="sxs-lookup"><span data-stu-id="aa462-166">Well done</span></span>

<span data-ttu-id="aa462-167">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="aa462-167">Congratulations!</span></span> <span data-ttu-id="aa462-168">Sie verfügen über eine Teams-App mit einer persönlichen Registerkarte, die die Suche nach wichtigen Kontakten in Ihrer Organisation erleichtert.</span><span class="sxs-lookup"><span data-stu-id="aa462-168">You have a Teams app with a personal tab that makes it easier to find important contacts in your organization.</span></span>

## <a name="learn-more"></a><span data-ttu-id="aa462-169">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="aa462-169">Learn more</span></span>

* <span data-ttu-id="aa462-170">Folgen Sie [unseren Entwurfsrichtlinien,](../tabs/design/tabs.md) und erstellen Sie mit [produktionsbereiten](../concepts/design/design-teams-app-ui-templates.md) Benutzeroberflächenvorlagen, um eine nahtlose Benutzeroberfläche zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="aa462-170">Follow our [design guidelines](../tabs/design/tabs.md) and build with [production-ready UI templates](../concepts/design/design-teams-app-ui-templates.md) to create a seamless experience.</span></span>
* <span data-ttu-id="aa462-171">Informationen [zu mobilen Überlegungen](../tabs/design/tabs-mobile.md) für Registerkarten.</span><span class="sxs-lookup"><span data-stu-id="aa462-171">Understand [mobile considerations](../tabs/design/tabs-mobile.md) for tabs.</span></span>
* <span data-ttu-id="aa462-172">[Fügen Sie ihrer Registerkarte die SSO-Authentifizierung hinzu.](../tabs/how-to/authentication/auth-aad-sso.md)</span><span class="sxs-lookup"><span data-stu-id="aa462-172">[Add SSO authentication to your tab](../tabs/how-to/authentication/auth-aad-sso.md).</span></span>
* <span data-ttu-id="aa462-173">Nutzen von Microsoft Teams-Daten [mit Microsoft Graph](https://docs.microsoft.com/graph/teams-concept-overview).</span><span class="sxs-lookup"><span data-stu-id="aa462-173">Utilize Teams data with [Microsoft Graph](https://docs.microsoft.com/graph/teams-concept-overview).</span></span>
* <span data-ttu-id="aa462-174">[Erstellen Sie eine Registerkarte ohne das Toolkit.](../tabs/quickstarts/create-personal-tab-node-yeoman.md)</span><span class="sxs-lookup"><span data-stu-id="aa462-174">[Create a tab without the toolkit](../tabs/quickstarts/create-personal-tab-node-yeoman.md).</span></span>

## <a name="next-lesson"></a><span data-ttu-id="aa462-175">Nächste Lektion</span><span class="sxs-lookup"><span data-stu-id="aa462-175">Next lesson</span></span>

<span data-ttu-id="aa462-176">Sie wissen, wie Sie eine Registerkarte für die persönliche Verwendung erstellen.</span><span class="sxs-lookup"><span data-stu-id="aa462-176">You know how to build a tab for personal use.</span></span> <span data-ttu-id="aa462-177">Sehen wir uns an, was zum Erstellen einer Registerkarte für Teamkanäle und Chats benötigt wird.</span><span class="sxs-lookup"><span data-stu-id="aa462-177">Let's look at what it takes to build a tab for team channels and chats.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="aa462-178">Erstellen einer Kanalregisterkarte</span><span class="sxs-lookup"><span data-stu-id="aa462-178">Build a channel tab</span></span>](../build-your-first-app/build-channel-tab.md)
