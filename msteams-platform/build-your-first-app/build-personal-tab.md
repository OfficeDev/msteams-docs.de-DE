---
title: Erste Schritte – Erstellen einer persönlichen Registerkarte
author: heath-hamilton
description: Erstellen Sie mit dem Microsoft Teams-Toolkit schnell eine persönliche Registerkarte von Microsoft Teams.
ms.author: lajanuar
ms.date: 11/03/2020
ms.topic: tutorial
ms.openlocfilehash: a82d3dcfd9529d88160c4193d27105c3468fe654
ms.sourcegitcommit: 64acd30eee8af5fe151e9866c13226ed3f337c72
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/18/2020
ms.locfileid: "49346805"
---
# <a name="build-a-personal-tab-for-microsoft-teams"></a><span data-ttu-id="3ebe6-103">Erstellen einer persönlichen Registerkarte für Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="3ebe6-103">Build a personal tab for Microsoft Teams</span></span>

<span data-ttu-id="3ebe6-104">Registerkarten stellen eine einfache Möglichkeit dar, Inhalte in Ihrer APP zu Oberflächen, indem eine Webseite im Wesentlichen in Microsoft Teams eingebettet wird.</span><span class="sxs-lookup"><span data-stu-id="3ebe6-104">Tabs are a simple way to surface content in your app by essentially embedding a webpage in Teams.</span></span>

<span data-ttu-id="3ebe6-105">Es gibt zwei Arten von Registerkarten in Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="3ebe6-105">There are two types of tabs in Teams.</span></span> <span data-ttu-id="3ebe6-106">In diesem Lernprogramm erstellen Sie grundlegende eine *persönliche Registerkarte*, eine voll Bildinhalts Seite für einzelne Benutzer.</span><span class="sxs-lookup"><span data-stu-id="3ebe6-106">In this tutorial, you'll build basic a *personal tab*, a full-screen content page for individual users.</span></span> <span data-ttu-id="3ebe6-107">(Persönliche Registerkarten sind die nächste Sache einer herkömmlichen Website Erfahrung in Microsoft Teams.)</span><span class="sxs-lookup"><span data-stu-id="3ebe6-107">(Personal tabs are the closest thing to a traditional website experience in Teams.)</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="3ebe6-108">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="3ebe6-108">Before you begin</span></span>

<span data-ttu-id="3ebe6-109">Für die ersten Schritte benötigen Sie eine grundlegende ausgeführte persönliche Registerkarte.</span><span class="sxs-lookup"><span data-stu-id="3ebe6-109">You need a basic running personal tab to get started.</span></span> <span data-ttu-id="3ebe6-110">Wenn Sie noch keinen haben, lesen Sie [Erstellen und Ausführen ihrer ersten Teams-App](../build-your-first-app/build-and-run.md).</span><span class="sxs-lookup"><span data-stu-id="3ebe6-110">If you don't have one, see [build and run your first Teams app](../build-your-first-app/build-and-run.md).</span></span>

## <a name="your-assignment"></a><span data-ttu-id="3ebe6-111">Ihre Zuordnung</span><span class="sxs-lookup"><span data-stu-id="3ebe6-111">Your assignment</span></span>

<span data-ttu-id="3ebe6-112">Personen in Ihrer Organisation haben Probleme bei der Suche nach grundlegenden Kontaktinformationen für wichtige Funktionen (Helpdesk, HR usw.).</span><span class="sxs-lookup"><span data-stu-id="3ebe6-112">People in your organization have trouble finding basic contact information for important functions (help desk, HR, etc.).</span></span> <span data-ttu-id="3ebe6-113">Sie müssen sicherstellen, dass diese Informationen schnell an einer Stelle gefunden werden können.</span><span class="sxs-lookup"><span data-stu-id="3ebe6-113">You're in charge of making sure they can quickly find this information in one place.</span></span> <span data-ttu-id="3ebe6-114">Wie würden Sie das tun?</span><span class="sxs-lookup"><span data-stu-id="3ebe6-114">How would you do that?</span></span> <span data-ttu-id="3ebe6-115">Eine persönliche Registerkarte Teams, natürlich.</span><span class="sxs-lookup"><span data-stu-id="3ebe6-115">A Teams personal tab, of course.</span></span>

## <a name="what-youll-learn"></a><span data-ttu-id="3ebe6-116">Was Sie lernen</span><span class="sxs-lookup"><span data-stu-id="3ebe6-116">What you'll learn</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="3ebe6-117">Identifizieren einiger der für persönliche Registerkarten relevanten App-Konfigurationen und Gerüste</span><span class="sxs-lookup"><span data-stu-id="3ebe6-117">Identify some of the app configurations and scaffolding relevant to personal tabs</span></span>
> * <span data-ttu-id="3ebe6-118">Erstellen von Registerkarten Inhalten</span><span class="sxs-lookup"><span data-stu-id="3ebe6-118">Create tab content</span></span>
> * <span data-ttu-id="3ebe6-119">Aktualisieren des Farbdesigns einer Registerkarte basierend auf der Benutzereinstellung</span><span class="sxs-lookup"><span data-stu-id="3ebe6-119">Update a tab's color theme based on user preference</span></span>

## <a name="1-identify-relevant-app-project-components"></a><span data-ttu-id="3ebe6-120">1. Identifizieren der relevanten App-Projektkomponenten</span><span class="sxs-lookup"><span data-stu-id="3ebe6-120">1. Identify relevant app project components</span></span>

<span data-ttu-id="3ebe6-121">Viele der APP-Konfigurationen und Gerüste werden automatisch eingerichtet, wenn Sie Ihr Projekt mit dem Teams-Toolkit erstellen.</span><span class="sxs-lookup"><span data-stu-id="3ebe6-121">Much of the app configurations and scaffolding are set up automatically when you create your project with the Teams Toolkit.</span></span> <span data-ttu-id="3ebe6-122">Lassen Sie uns die Hauptkomponenten für die Erstellung einer persönlichen Registerkarte betrachten.</span><span class="sxs-lookup"><span data-stu-id="3ebe6-122">Let's look at the main components for building a personal tab.</span></span>

### <a name="app-configurations"></a><span data-ttu-id="3ebe6-123">App-Konfigurationen</span><span class="sxs-lookup"><span data-stu-id="3ebe6-123">App configurations</span></span>

<span data-ttu-id="3ebe6-124">Sie können Ihre APP-Konfigurationen mithilfe von App Studio anzeigen und aktualisieren, die im Toolkit enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="3ebe6-124">You can view and update your app configurations using App Studio, which is included in the toolkit.</span></span>

<span data-ttu-id="3ebe6-125">Während des Setups hat das Toolkit zunächst die Inhaltsseite für Registerkarten konfiguriert, auf der Sie Ihren primären Inhalt anzeigen können.</span><span class="sxs-lookup"><span data-stu-id="3ebe6-125">During setup, the toolkit initially configured your tab content page, which is where you display your primary content.</span></span> <span data-ttu-id="3ebe6-126">Wechseln Sie im Toolkit zu **App Studio** , und wählen Sie **Registerkarten** aus, um die Konfiguration anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="3ebe6-126">In the toolkit, go to **App Studio** and select **Tabs** to see the configuration.</span></span>

### <a name="app-scaffolding"></a><span data-ttu-id="3ebe6-127">App-Gerüste</span><span class="sxs-lookup"><span data-stu-id="3ebe6-127">App scaffolding</span></span>

<span data-ttu-id="3ebe6-128">Das App-Gerüst stellt die Komponenten zum Rendern Ihrer persönlichen Registerkarte in Microsoft Teams bereit.</span><span class="sxs-lookup"><span data-stu-id="3ebe6-128">The app scaffolding provides the components for rendering your personal tab in Teams.</span></span> <span data-ttu-id="3ebe6-129">Es gibt eine Menge, mit der Sie arbeiten können, aber im Moment müssen Sie sich nur auf Folgendes konzentrieren:</span><span class="sxs-lookup"><span data-stu-id="3ebe6-129">There's a lot you can work with, but for now you only need to focus on the following:</span></span>

* <span data-ttu-id="3ebe6-130">`Tab.js` Datei im `src/components` Verzeichnis des Projekts.</span><span class="sxs-lookup"><span data-stu-id="3ebe6-130">`Tab.js` file in the `src/components` directory of your project.</span></span> <span data-ttu-id="3ebe6-131">Dies dient zum Rendern Ihrer Registerkarteninhalts Seite.</span><span class="sxs-lookup"><span data-stu-id="3ebe6-131">This is for for rendering your tab content page.</span></span>
* <span data-ttu-id="3ebe6-132">Microsoft Teams JavaScript-Client-SDK, das in den Front-End-Komponenten Ihres Projekts vorinstalliert ist.</span><span class="sxs-lookup"><span data-stu-id="3ebe6-132">Microsoft Teams JavaScript client SDK, which comes pre-loaded in your project's front-end components.</span></span>

## <a name="2-customize-your-tab-content-page"></a><span data-ttu-id="3ebe6-133">2. Anpassen der Inhaltsseite der Registerkarte</span><span class="sxs-lookup"><span data-stu-id="3ebe6-133">2. Customize your tab content page</span></span>

<span data-ttu-id="3ebe6-134">Kompilieren Sie eine Liste wichtiger Kontakte in Ihrer Organisation.</span><span class="sxs-lookup"><span data-stu-id="3ebe6-134">Compile a list of important contacts in your organization.</span></span> <span data-ttu-id="3ebe6-135">Kopieren Sie den folgenden Codeausschnitt, und aktualisieren Sie ihn mit Informationen, die für Sie relevant sind, oder verwenden Sie, um der Zeit Willen, den Code wie es ist.</span><span class="sxs-lookup"><span data-stu-id="3ebe6-135">Copy and update the following snippet with information that's relevant to you or, for the sake of time, use the code as is.</span></span>

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

<span data-ttu-id="3ebe6-136">Wechseln Sie zum `src/components` Verzeichnis, und öffnen Sie `Tab.js` .</span><span class="sxs-lookup"><span data-stu-id="3ebe6-136">Go to the `src/components` directory and open `Tab.js`.</span></span> <span data-ttu-id="3ebe6-137">Suchen `render()` Sie die-Funktion, und fügen Sie den Inhalt in das Bild ein `return()` (siehe Abbildung).</span><span class="sxs-lookup"><span data-stu-id="3ebe6-137">Locate the `render()` function and paste your content inside `return()` (as shown).</span></span>

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

<span data-ttu-id="3ebe6-138">Fügen Sie die folgende Regel hinzu, `App.css` damit die e-Mail-Links leichter lesbar sind, unabhängig davon, welches Design verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="3ebe6-138">Add the following rule to `App.css` so the email links are easier to read no matter which theme is used.</span></span>

```CSS
a {
  color: inherit;
}
```

<span data-ttu-id="3ebe6-139">Speichern Sie Ihre Änderungen.</span><span class="sxs-lookup"><span data-stu-id="3ebe6-139">Save your changes.</span></span> <span data-ttu-id="3ebe6-140">Wechseln Sie zur Registerkarte ihrer app in Microsoft Teams, um den neuen Inhalt anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="3ebe6-140">Go to your app's tab in Teams to view the new content.</span></span>

:::image type="content" source="../assets/images/tabs/personal-tab-tutorial-content.png" alt-text="Screenshot einer persönlichen Registerkarte mit statischem Inhalt.":::

## <a name="3-update-the-tab-theme"></a><span data-ttu-id="3ebe6-142">3. Aktualisieren des Registerkarten Designs</span><span class="sxs-lookup"><span data-stu-id="3ebe6-142">3. Update the tab theme</span></span>

<span data-ttu-id="3ebe6-143">Gute apps fühlen sich nativ für Teams, daher ist es wichtig, dass Ihre Registerkarte mit dem Microsoft Teams-Design kombiniert wird, das Ihre Benutzer bevorzugen: Standard (hell), dunkel oder hoher Kontrast.</span><span class="sxs-lookup"><span data-stu-id="3ebe6-143">Good apps feel native to Teams, so it's important your tab blends with the Teams theme your users prefer: default (light), dark, or high contrast.</span></span> <span data-ttu-id="3ebe6-144">Wie Sie vielleicht schon im letzten Screenshot bemerkt haben, hat ihre Registerkarte immer noch einen hellen Hintergrund, wenn der Client das dunkle Design verwendet.</span><span class="sxs-lookup"><span data-stu-id="3ebe6-144">As you might have noticed in the last screenshot, your tab still has a light background when the client's using the dark theme.</span></span> <span data-ttu-id="3ebe6-145">Dies ist keine empfohlene Benutzeroberfläche.</span><span class="sxs-lookup"><span data-stu-id="3ebe6-145">This is not a recommended user experience.</span></span>

<span data-ttu-id="3ebe6-146">Das Microsoft [Teams-JavaScript-Client-SDK](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/?view=msteams-client-js-latest&preserve-view=true) kann Ihre APP auf Designänderungen im Client aufmerksam machen und darauf reagieren.</span><span class="sxs-lookup"><span data-stu-id="3ebe6-146">The [Teams JavaScript client SDK](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/?view=msteams-client-js-latest&preserve-view=true) can make your app aware of and react to theme changes in the client.</span></span> <span data-ttu-id="3ebe6-147">Lassen Sie uns die Vorgehensweise durchgehen.</span><span class="sxs-lookup"><span data-stu-id="3ebe6-147">Let's walk through how to do this.</span></span>

### <a name="get-context-about-the-teams-client"></a><span data-ttu-id="3ebe6-148">Abrufen des Kontexts zum Microsoft Teams-Client</span><span class="sxs-lookup"><span data-stu-id="3ebe6-148">Get context about the Teams client</span></span>

<span data-ttu-id="3ebe6-149">In Ihrer `Tab.js` Datei gibt es einen `microsoftTeams.getContext()` Anruf, [`context`](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/context?view=msteams-client-js-latest&preserve-view=true) der einige Informationen zu dem konfigurierten Client Design enthält, unter anderem.</span><span class="sxs-lookup"><span data-stu-id="3ebe6-149">In your `Tab.js` file, there's a `microsoftTeams.getContext()` call that provides some [`context`](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/context?view=msteams-client-js-latest&preserve-view=true) about, among other details, the configured client theme.</span></span> <span data-ttu-id="3ebe6-150">Dank des App-Gerüsts verwenden Sie diesen Code wie für den Zugriff auf die `context` Schnittstelle und ihre Eigenschaften.</span><span class="sxs-lookup"><span data-stu-id="3ebe6-150">Thanks to the app scaffolding, use this code as is to access the `context` interface and its properties.</span></span>

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

### <a name="create-a-theme-change-handler"></a><span data-ttu-id="3ebe6-151">Erstellen eines Handlers für die Designänderung</span><span class="sxs-lookup"><span data-stu-id="3ebe6-151">Create a theme change handler</span></span>

<span data-ttu-id="3ebe6-152">Mit den `context` Eigenschaften in der Hand hat Ihre APP ein fundiertes Verständnis dessen, was in Microsoft Teams geschieht.</span><span class="sxs-lookup"><span data-stu-id="3ebe6-152">With the `context` properties in hand, your app has a solid understanding of what's happening around it in Teams.</span></span> <span data-ttu-id="3ebe6-153">Die APP weiß jedoch noch nicht, dass Ihr Aussehen das Design reflektieren sollte, das ein Benutzer auswählt.</span><span class="sxs-lookup"><span data-stu-id="3ebe6-153">But the app still doesn't know its appearance should reflect whatever theme a user chooses.</span></span>

<span data-ttu-id="3ebe6-154">Sie benötigen einen Handler, damit sich der Zustand Ihrer APP mit dem Design ändert.</span><span class="sxs-lookup"><span data-stu-id="3ebe6-154">You need a handler so that your app's state changes with the theme.</span></span> <span data-ttu-id="3ebe6-155">Fügen Sie den folgenden Design änderungshandler unmittelbar nach dem `microsoftTeams.getContext()` Aufruf ein.</span><span class="sxs-lookup"><span data-stu-id="3ebe6-155">Insert the following theme change handler immediately after the `microsoftTeams.getContext()` call.</span></span>

```JavaScript
  microsoftTeams.registerOnThemeChangeHandler(theme => {
    if (theme !== this.state.theme) {
      this.setState({ theme });  
    }
  });
```

### <a name="match-theme-styles"></a><span data-ttu-id="3ebe6-156">Zuordnen von Designstilen</span><span class="sxs-lookup"><span data-stu-id="3ebe6-156">Match theme styles</span></span>

<span data-ttu-id="3ebe6-157">Ihr Design änderungshandler ist vorhanden, aber Sie benötigen Code, der auf diese Änderungen reagiert und die Farben ihrer Registerkarten mit dem aktuellen Design ausrichtet.</span><span class="sxs-lookup"><span data-stu-id="3ebe6-157">Your theme change handler is in place, but you need some code that responds to those changes and aligns your tab's colors with the current theme.</span></span>

> [!NOTE]
> <span data-ttu-id="3ebe6-158">Das folgende Beispiel ist nur eine Möglichkeit, wie Sie Formatvorlagen auf die Registerkarte anwenden können. Verwenden Sie den Code wie folgt, erweitern Sie ihn, oder schreiben Sie einen eigenen.</span><span class="sxs-lookup"><span data-stu-id="3ebe6-158">The following example is just one way you might apply styles to your tab. Use the code as is, expand on it, or write your own.</span></span>

<span data-ttu-id="3ebe6-159">Speichern Sie den vom Design änderungshandler in bereitgestellten Zustand `isTheme` .</span><span class="sxs-lookup"><span data-stu-id="3ebe6-159">Store the state provided by the theme change handler in `isTheme`.</span></span>

```JavaScript
  const isTheme = this.state.theme
```

<span data-ttu-id="3ebe6-160">Bereitstelleneiner bedingten Logik zum Rendern der Formatvorlagen ihrer Registerkarten basierend auf dem aktuellen Design.</span><span class="sxs-lookup"><span data-stu-id="3ebe6-160">Provide some conditional logic to render your tab's styles based on the current theme.</span></span> <span data-ttu-id="3ebe6-161">Das folgende Beispiel zeigt eine einfache Möglichkeit, dies zu tun, indem 1) das aktuelle Design in `isTheme` , 2) das Erstellen eines `newTheme` Objekts mit CSS-Eigenschaften, die für das aktuelle Design relevant sind, und 3) Überprüfen des CSS auf das HTML-Stammelement Ihres Registerkarteninhalts ( `<div>` ).</span><span class="sxs-lookup"><span data-stu-id="3ebe6-161">The following example shows a basic way to do this by 1) checking the current theme in `isTheme`, 2) creating a `newTheme` object with CSS properties relevant to the current theme, and 3) applying the CSS to your tab content's root HTML element (`<div>`).</span></span>

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

<span data-ttu-id="3ebe6-162">Überprüfen Sie Ihre Registerkarte in Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="3ebe6-162">Check your tab in Teams.</span></span> <span data-ttu-id="3ebe6-163">Die Darstellung sollte eng mit dem dunklen Design übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="3ebe6-163">The appearance should closely match the dark theme.</span></span>

:::image type="content" source="../assets/images/tabs/personal-tab-tutorial-updated-theme.png" alt-text="Screenshot einer persönlichen Registerkarte mit statischer Inhaltsansicht.":::

## <a name="well-done"></a><span data-ttu-id="3ebe6-165">Gut gemacht</span><span class="sxs-lookup"><span data-stu-id="3ebe6-165">Well done</span></span>

<span data-ttu-id="3ebe6-166">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="3ebe6-166">Congratulations!</span></span> <span data-ttu-id="3ebe6-167">Sie verfügen über eine Teams-App mit einer persönlichen Registerkarte, die es einfacher macht, wichtige Kontakte in Ihrer Organisation zu finden.</span><span class="sxs-lookup"><span data-stu-id="3ebe6-167">You have a Teams app with a personal tab that makes it easier to find important contacts in your organization.</span></span>

## <a name="learn-more"></a><span data-ttu-id="3ebe6-168">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="3ebe6-168">Learn more</span></span>

* <span data-ttu-id="3ebe6-169">[Authentifizieren von Registerkarten Benutzern mit SSO](../tabs/how-to/authentication/auth-aad-sso.md): Wenn Sie nur autorisierte Benutzer Ihrer Registerkarte anzeigen möchten, richten Sie einmaliges Anmelden (Single Sign-on, SSO) über Azure Active Directory (AD) ein.</span><span class="sxs-lookup"><span data-stu-id="3ebe6-169">[Authenticate tab users with SSO](../tabs/how-to/authentication/auth-aad-sso.md): If you only want authorized users viewing your tab, set up single sign-on (SSO) through Azure Active Directory (AD).</span></span>
* <span data-ttu-id="3ebe6-170">[Einbetten von Inhalten aus einer vorhandenen Web-App oder Webseite](../tabs/how-to/add-tab.md#tab-requirements): Wir haben gezeigt, wie Sie neue Inhalte für eine persönliche RegisterkarteErstellen, aber Sie können auch Inhalte aus einer externen URL laden.</span><span class="sxs-lookup"><span data-stu-id="3ebe6-170">[Embed content from an existing web app or webpage](../tabs/how-to/add-tab.md#tab-requirements): We showed you how to create new content for a personal tab, but you can also load content from an external URL.</span></span>
* <span data-ttu-id="3ebe6-171">[Erstellen Sie eine nahtlose Benutzeroberfläche für Ihre Registerkarte](../tabs/design/tabs.md): Lesen Sie die empfohlenen Richtlinien für das Entwerfen von Microsoft Teams-Registerkarten.</span><span class="sxs-lookup"><span data-stu-id="3ebe6-171">[Create a seamless experience for your tab](../tabs/design/tabs.md): See the recommended guidelines for designing Teams tabs.</span></span>
* <span data-ttu-id="3ebe6-172">[Erstellen von Registerkarten für Mobilgeräte](../tabs/design/tabs-mobile.md): Hier erfahren Sie, wie Sie Registerkarten für Telefone und Tablets entwickeln.</span><span class="sxs-lookup"><span data-stu-id="3ebe6-172">[Build tabs for mobile](../tabs/design/tabs-mobile.md): Understand how to develop tabs for phones and tablets.</span></span>
* [<span data-ttu-id="3ebe6-173">Verwenden von Teams-Daten mit der Microsoft Graph-API</span><span class="sxs-lookup"><span data-stu-id="3ebe6-173">Utilize Teams data with the Microsoft Graph API</span></span>](https://docs.microsoft.com/graph/teams-concept-overview)
* [<span data-ttu-id="3ebe6-174">Erstellen einer Registerkarte ohne Toolkit</span><span class="sxs-lookup"><span data-stu-id="3ebe6-174">Create a tab without the toolkit</span></span>](../tabs/how-to/add-tab.md)

## <a name="next-lesson"></a><span data-ttu-id="3ebe6-175">Nächste Lektion</span><span class="sxs-lookup"><span data-stu-id="3ebe6-175">Next lesson</span></span>

<span data-ttu-id="3ebe6-176">Sie wissen, wie Sie eine Registerkarte zur persönlichen Verwendung erstellen.</span><span class="sxs-lookup"><span data-stu-id="3ebe6-176">You know how to build a tab for personal use.</span></span> <span data-ttu-id="3ebe6-177">Schauen wir uns an, was es braucht, um eine Registerkarte für Team Kanäle und Chats zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="3ebe6-177">Let's look at what it takes to build a tab for team channels and chats.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="3ebe6-178">Erstellen einer Kanalregisterkarte</span><span class="sxs-lookup"><span data-stu-id="3ebe6-178">Build a channel tab</span></span>](../build-your-first-app/build-channel-tab.md)
