---
title: Erstellen einer persönlichen Registerkarte für Teams
author: heath-hamilton
description: Erfahren Sie, wie Sie eine persönliche Registerkarte in ihrer ersten Microsoft Teams-app erstellen.
ms.topic: tutorial
ms.openlocfilehash: 1c782adce2201550d30d658907d507dc6a1337f3
ms.sourcegitcommit: 9fbc701a9a039ecdc360aefbe86df52b9c3593f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/12/2020
ms.locfileid: "46652046"
---
# <a name="create-a-personal-tab-for-teams"></a><span data-ttu-id="7878c-103">Erstellen einer persönlichen Registerkarte für Teams</span><span class="sxs-lookup"><span data-stu-id="7878c-103">Create a personal tab for Teams</span></span>

<span data-ttu-id="7878c-104">Registerkarten stellen eine einfache Möglichkeit dar, Inhalte in Ihrer APP zu Oberflächen, indem eine Webseite im Wesentlichen in Microsoft Teams eingebettet wird.</span><span class="sxs-lookup"><span data-stu-id="7878c-104">Tabs are a simple way to surface content in your app by essentially embedding a webpage in Teams.</span></span>

<span data-ttu-id="7878c-105">Es gibt zwei Arten von Registerkarten in Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="7878c-105">There are two types of tabs in Teams.</span></span> <span data-ttu-id="7878c-106">In diesem Lernprogramm erstellen Sie grundlegende eine *persönliche Registerkarte*, eine voll Bildinhalts Seite für einzelne Benutzer.</span><span class="sxs-lookup"><span data-stu-id="7878c-106">In this tutorial, you'll build basic a *personal tab*, a full-screen content page for individual users.</span></span> <span data-ttu-id="7878c-107">(Persönliche Registerkarten sind die nächste Sache einer herkömmlichen Website Erfahrung in Microsoft Teams.)</span><span class="sxs-lookup"><span data-stu-id="7878c-107">(Personal tabs are the closest thing to a traditional website experience in Teams.)</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="7878c-108">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="7878c-108">Before you begin</span></span>

<span data-ttu-id="7878c-109">Sie benötigen eine grundlegende ausgeführte App für den Einstieg.</span><span class="sxs-lookup"><span data-stu-id="7878c-109">You need a basic running app to get started.</span></span> <span data-ttu-id="7878c-110">Wenn Sie noch keinen haben, lesen Sie [Erstellen und Ausführen ihrer ersten Teams-App](build-and-run-with-toolkit.md).</span><span class="sxs-lookup"><span data-stu-id="7878c-110">If you don't have one, see [build and run your first Teams app](build-and-run-with-toolkit.md).</span></span>

## <a name="your-assignment"></a><span data-ttu-id="7878c-111">Ihre Zuordnung</span><span class="sxs-lookup"><span data-stu-id="7878c-111">Your assignment</span></span>

<span data-ttu-id="7878c-112">Personen in Ihrer Organisation haben Probleme bei der Suche nach grundlegenden Kontaktinformationen für wichtige Funktionen (Helpdesk, HR usw.).</span><span class="sxs-lookup"><span data-stu-id="7878c-112">People in your organization have trouble finding basic contact information for important functions (help desk, HR, etc.).</span></span> <span data-ttu-id="7878c-113">Sie müssen sicherstellen, dass diese Informationen schnell an einer Stelle gefunden werden können.</span><span class="sxs-lookup"><span data-stu-id="7878c-113">You're in charge of making sure they can quickly find this information in one place.</span></span> <span data-ttu-id="7878c-114">Wie würden Sie das tun?</span><span class="sxs-lookup"><span data-stu-id="7878c-114">How would you do that?</span></span> <span data-ttu-id="7878c-115">Eine persönliche Registerkarte Teams, natürlich.</span><span class="sxs-lookup"><span data-stu-id="7878c-115">A Teams personal tab, of course.</span></span>

## <a name="what-youll-learn"></a><span data-ttu-id="7878c-116">Was Sie lernen</span><span class="sxs-lookup"><span data-stu-id="7878c-116">What you'll learn</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="7878c-117">Identifizieren der für persönliche Registerkarten relevanten App-Manifest-Eigenschaften und-Gerüste</span><span class="sxs-lookup"><span data-stu-id="7878c-117">Identify the app manifest properties and scaffolding relevant to personal tabs</span></span>
> * <span data-ttu-id="7878c-118">Erstellen von Inhalten für die Registerkarte</span><span class="sxs-lookup"><span data-stu-id="7878c-118">Create content for your tab</span></span>
> * <span data-ttu-id="7878c-119">Aktualisieren des Farbdesigns ihrer Registerkarte basierend auf der Benutzereinstellung</span><span class="sxs-lookup"><span data-stu-id="7878c-119">Update your tab's color theme based on user preference</span></span>

## <a name="identify-relevant-app-manifest-and-scaffolding-components"></a><span data-ttu-id="7878c-120">Identifizieren relevanter App-Manifest-und Gerüstbau-Komponenten</span><span class="sxs-lookup"><span data-stu-id="7878c-120">Identify relevant app manifest and scaffolding components</span></span>

<span data-ttu-id="7878c-121">Ein Großteil der persönlichen Registerkarten-App-Gerüste und Manifeste wird automatisch eingerichtet, wenn Sie Ihr Projekt mit dem Teams-Toolkit erstellen.</span><span class="sxs-lookup"><span data-stu-id="7878c-121">Much of the personal tab app scaffolding and manifest is set up automatically when you create your project with the Teams Toolkit.</span></span> <span data-ttu-id="7878c-122">Lassen Sie uns die Hauptkomponenten für die Erstellung einer persönlichen Registerkarte betrachten.</span><span class="sxs-lookup"><span data-stu-id="7878c-122">Let's look at the main components for building a personal tab.</span></span>

### <a name="app-manifest"></a><span data-ttu-id="7878c-123">App-Manifest</span><span class="sxs-lookup"><span data-stu-id="7878c-123">App manifest</span></span>

<span data-ttu-id="7878c-124">Der folgende Ausschnitt aus dem App-Manifest (die `manifest.json` Datei im Verzeichnis des Projekts `.publish` ) zeigt an [`staticTabs`](../../resources/schema/manifest-schema.md#statictabs) , welche Eigenschaften und Standardwerte für persönliche Registerkarten relevant sind.</span><span class="sxs-lookup"><span data-stu-id="7878c-124">The following snippet from the app manifest (the `manifest.json` file in your project's `.publish` directory) shows [`staticTabs`](../../resources/schema/manifest-schema.md#statictabs), which includes properties and default values relevant to personal tabs.</span></span>

```JSON
    "staticTabs": [
        {
            "entityId": "index",
            "name": "Personal Tab",
            "contentUrl": "{baseUrl0}/tab",
            "scopes": [ "personal" ]
        }
    ],
```

* <span data-ttu-id="7878c-125">`entityId`: Ein eindeutiger Bezeichner für die Seite, die von der Registerkarte angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="7878c-125">`entityId`: A unique identifier for the page displayed by the tab.</span></span>
* <span data-ttu-id="7878c-126">`name`: Der Anzeigename der Registerkarte (beispielsweise "meine Kontakte").</span><span class="sxs-lookup"><span data-stu-id="7878c-126">`name`: The tab's display name (for example, "My Contacts").</span></span>
* <span data-ttu-id="7878c-127">`contentUrl`: Die Host-URL die Registerkarteninhalts Seite (muss https sein).</span><span class="sxs-lookup"><span data-stu-id="7878c-127">`contentUrl`: The host URL the tab content page (must be HTTPS).</span></span>
* <span data-ttu-id="7878c-128">`scopes`: Gibt an, dass die Registerkarte nur zur persönlichen Verwendung verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="7878c-128">`scopes`: Specifies the tab is for personal use only.</span></span>

### <a name="app-scaffolding"></a><span data-ttu-id="7878c-129">App-Gerüste</span><span class="sxs-lookup"><span data-stu-id="7878c-129">App scaffolding</span></span>

<span data-ttu-id="7878c-130">Das App-Gerüst stellt die Komponenten zum Rendern Ihrer Registerkarte in Microsoft Teams bereit.</span><span class="sxs-lookup"><span data-stu-id="7878c-130">The app scaffolding provides the components for rendering your tab in Teams.</span></span> <span data-ttu-id="7878c-131">Es gibt eine Menge, mit der Sie arbeiten können, aber im Moment müssen Sie sich nur auf Folgendes konzentrieren:</span><span class="sxs-lookup"><span data-stu-id="7878c-131">There's a lot you can work with, but for now you only need to focus on the following:</span></span>

* <span data-ttu-id="7878c-132">`Tab.js` Datei im `src/components` Verzeichnis des Projekts</span><span class="sxs-lookup"><span data-stu-id="7878c-132">`Tab.js` file in the `src/components` directory of your project</span></span>
* <span data-ttu-id="7878c-133">Microsoft Teams JavaScript-Client-SDK, das in den Front-End-Komponenten Ihres Projekts vorinstalliert ist</span><span class="sxs-lookup"><span data-stu-id="7878c-133">Microsoft Teams JavaScript client SDK, which comes pre-loaded in your project's front-end components</span></span>

## <a name="create-your-tab-content"></a><span data-ttu-id="7878c-134">Erstellen des Registerkarteninhalts</span><span class="sxs-lookup"><span data-stu-id="7878c-134">Create your tab content</span></span>

<span data-ttu-id="7878c-135">Kompilieren Sie eine Liste wichtiger Kontakte in Ihrer Organisation.</span><span class="sxs-lookup"><span data-stu-id="7878c-135">Compile a list of important contacts in your organization.</span></span> <span data-ttu-id="7878c-136">Kopieren Sie den folgenden Codeausschnitt, und aktualisieren Sie ihn mit Informationen, die für Sie relevant sind, oder verwenden Sie, um der Zeit Willen, den Code wie es ist.</span><span class="sxs-lookup"><span data-stu-id="7878c-136">Copy and update the following snippet with information that's relevant to you or, for the sake of time, use the code as is.</span></span>

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

<span data-ttu-id="7878c-137">Wechseln Sie zum `src/components` Verzeichnis, und öffnen Sie `Tab.js` .</span><span class="sxs-lookup"><span data-stu-id="7878c-137">Go to the `src/components` directory and open `Tab.js`.</span></span> <span data-ttu-id="7878c-138">Suchen `render()` Sie die-Funktion, und fügen Sie den Inhalt in das Bild ein `return()` (siehe Abbildung).</span><span class="sxs-lookup"><span data-stu-id="7878c-138">Locate the `render()` function and paste your content inside `return()` (as shown).</span></span>

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

<span data-ttu-id="7878c-139">Fügen Sie die folgende Regel hinzu, `App.css` damit die e-Mail-Links leichter lesbar sind, unabhängig davon, welches Design verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="7878c-139">Add the following rule to `App.css` so the email links are easier to read no matter which theme is used.</span></span>

```CSS
  a {
    color: inherit;
  }
```

<span data-ttu-id="7878c-140">Speichern Sie Ihre Änderungen.</span><span class="sxs-lookup"><span data-stu-id="7878c-140">Save your changes.</span></span> <span data-ttu-id="7878c-141">Wechseln Sie zur Registerkarte ihrer app in Microsoft Teams, um den neuen Inhalt anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="7878c-141">Go to your app's tab in Teams to view the new content.</span></span>

![Beispiel Screenshot einer persönlichen Registerkarte mit statischem Inhalt](../doc-links/images/personal-tab-tutorial-content.png)

## <a name="update-the-tab-theme"></a><span data-ttu-id="7878c-143">Aktualisieren des Registerkarten Designs</span><span class="sxs-lookup"><span data-stu-id="7878c-143">Update the tab theme</span></span>

<span data-ttu-id="7878c-144">Gute apps fühlen sich nativ für Teams, daher ist es wichtig, dass Ihre Registerkarte mit dem Microsoft Teams-Design kombiniert wird, das Ihre Benutzer bevorzugen: Standard (hell), dunkel oder hoher Kontrast.</span><span class="sxs-lookup"><span data-stu-id="7878c-144">Good apps feel native to Teams, so it's important your tab blends with the Teams theme your users prefer: default (light), dark, or high contrast.</span></span> <span data-ttu-id="7878c-145">Wie Sie vielleicht schon im letzten Screenshot bemerkt haben, hat ihre Registerkarte immer noch einen hellen Hintergrund, wenn der Client das dunkle Design verwendet.</span><span class="sxs-lookup"><span data-stu-id="7878c-145">As you might have noticed in the last screenshot, your tab still has a light background when the client's using the dark theme.</span></span> <span data-ttu-id="7878c-146">Dies ist keine empfohlene Benutzeroberfläche.</span><span class="sxs-lookup"><span data-stu-id="7878c-146">This is not a recommended user experience.</span></span>

<span data-ttu-id="7878c-147">Das Microsoft [Teams-JavaScript-Client-SDK](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/?view=msteams-client-js-latest) kann Ihre APP auf Designänderungen im Client aufmerksam machen und darauf reagieren.</span><span class="sxs-lookup"><span data-stu-id="7878c-147">The [Teams JavaScript client SDK](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/?view=msteams-client-js-latest) can make your app aware of and react to theme changes in the client.</span></span> <span data-ttu-id="7878c-148">Lassen Sie uns die Vorgehensweise durchgehen.</span><span class="sxs-lookup"><span data-stu-id="7878c-148">Let's walk through how to do this.</span></span>

### <a name="get-context-about-the-teams-client"></a><span data-ttu-id="7878c-149">Abrufen des Kontexts zum Microsoft Teams-Client</span><span class="sxs-lookup"><span data-stu-id="7878c-149">Get context about the Teams client</span></span>

<span data-ttu-id="7878c-150">In Ihrer `Tab.js` Datei gibt es einen `microsoftTeams.getContext()` Anruf, [`context`](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/microsoftteams.context?view=msteams-client-js-latest) der einige Informationen zu dem konfigurierten Client Design enthält, unter anderem.</span><span class="sxs-lookup"><span data-stu-id="7878c-150">In your `Tab.js` file, there's a `microsoftTeams.getContext()` call that provides some [`context`](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/microsoftteams.context?view=msteams-client-js-latest) about, among other details, the configured client theme.</span></span> <span data-ttu-id="7878c-151">Dank des App-Gerüsts verwenden Sie diesen Code wie für den Zugriff auf die `context` Schnittstelle und ihre Eigenschaften.</span><span class="sxs-lookup"><span data-stu-id="7878c-151">Thanks to the app scaffolding, use this code as is to access the `context` interface and its properties.</span></span>

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

### <a name="create-a-theme-change-handler"></a><span data-ttu-id="7878c-152">Erstellen eines Handlers für die Designänderung</span><span class="sxs-lookup"><span data-stu-id="7878c-152">Create a theme change handler</span></span>

<span data-ttu-id="7878c-153">Mit den `context` Eigenschaften in der Hand hat Ihre APP ein fundiertes Verständnis dessen, was in Microsoft Teams geschieht.</span><span class="sxs-lookup"><span data-stu-id="7878c-153">With the `context` properties in hand, your app has a solid understanding of what's happening around it in Teams.</span></span> <span data-ttu-id="7878c-154">Die APP weiß jedoch noch nicht, dass Ihr Aussehen das Design reflektieren sollte, das ein Benutzer auswählt.</span><span class="sxs-lookup"><span data-stu-id="7878c-154">But the app still doesn't know its appearance should reflect whatever theme a user chooses.</span></span>

<span data-ttu-id="7878c-155">Sie benötigen einen Handler, damit sich der Zustand Ihrer APP mit dem Design ändert.</span><span class="sxs-lookup"><span data-stu-id="7878c-155">You need a handler so that your app's state changes with the theme.</span></span> <span data-ttu-id="7878c-156">Fügen Sie den folgenden Design änderungshandler unmittelbar nach dem `microsoftTeams.getContext()` Aufruf ein.</span><span class="sxs-lookup"><span data-stu-id="7878c-156">Insert the following theme change handler immediately after the `microsoftTeams.getContext()` call.</span></span>

```JavaScript
  microsoftTeams.registerOnThemeChangeHandler(theme => {
    if (theme !== this.state.theme) {
      this.setState({ theme });  
    }
  });
```

### <a name="match-theme-styles"></a><span data-ttu-id="7878c-157">Zuordnen von Designstilen</span><span class="sxs-lookup"><span data-stu-id="7878c-157">Match theme styles</span></span>

<span data-ttu-id="7878c-158">Ihr Design änderungshandler ist vorhanden, aber Sie benötigen Code, der auf diese Änderungen reagiert und die Farben ihrer Registerkarten mit dem aktuellen Design ausrichtet.</span><span class="sxs-lookup"><span data-stu-id="7878c-158">Your theme change handler is in place, but you need some code that responds to those changes and aligns your tab's colors with the current theme.</span></span>

> [!NOTE]
> <span data-ttu-id="7878c-159">Das folgende Beispiel ist nur eine Möglichkeit, wie Sie Formatvorlagen auf die Registerkarte anwenden können. verwenden Sie den Code wie folgt, erweitern Sie ihn, oder schreiben Sie einen eigenen.</span><span class="sxs-lookup"><span data-stu-id="7878c-159">The following example is just one way you might apply styles to your tab. Use the code as is, expand on it, or write your own.</span></span>

<span data-ttu-id="7878c-160">Speichern Sie den vom Design änderungshandler in bereitgestellten Zustand `isTheme` .</span><span class="sxs-lookup"><span data-stu-id="7878c-160">Store the state provided by the theme change handler in `isTheme`.</span></span>

```JavaScript
  const isTheme = this.state.theme
```

<span data-ttu-id="7878c-161">Bereitstelleneiner bedingten Logik zum Rendern der Formatvorlagen ihrer Registerkarten basierend auf dem aktuellen Design.</span><span class="sxs-lookup"><span data-stu-id="7878c-161">Provide some conditional logic to render your tab's styles based on the current theme.</span></span> <span data-ttu-id="7878c-162">Das folgende Beispiel zeigt eine einfache Möglichkeit, dies zu tun, indem 1) das aktuelle Design in `isTheme` , 2) das Erstellen eines `newTheme` Objekts mit CSS-Eigenschaften, die für das aktuelle Design relevant sind, und 3) Überprüfen des CSS auf das HTML-Stammelement Ihres Registerkarteninhalts ( `<div>` ).</span><span class="sxs-lookup"><span data-stu-id="7878c-162">The following example shows a basic way to do this by 1) checking the current theme in `isTheme`, 2) creating a `newTheme` object with CSS properties relevant to the current theme, and 3) applying the CSS to your tab content's root HTML element (`<div>`).</span></span>

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

<span data-ttu-id="7878c-163">Überprüfen Sie Ihre Registerkarte in Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="7878c-163">Check your tab in Teams.</span></span> <span data-ttu-id="7878c-164">Die Darstellung sollte eng mit dem dunklen Design übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="7878c-164">The appearance should closely match the dark theme.</span></span>

![Beispiel Screenshot einer persönlichen Registerkarte mit statischem Inhalt](../doc-links/images/personal-tab-tutorial-updated-theme.png)

## <a name="well-done"></a><span data-ttu-id="7878c-166">Gut gemacht</span><span class="sxs-lookup"><span data-stu-id="7878c-166">Well done</span></span>

<span data-ttu-id="7878c-167">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="7878c-167">Congratulations!</span></span> <span data-ttu-id="7878c-168">Sie verfügen über eine Teams-App mit einer persönlichen Registerkarte, die es einfacher macht, wichtige Kontakte in Ihrer Organisation zu finden.</span><span class="sxs-lookup"><span data-stu-id="7878c-168">You have a Teams app with a personal tab that makes it easier to find important contacts in your organization.</span></span>

## <a name="next-step"></a><span data-ttu-id="7878c-169">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="7878c-169">Next step</span></span>

<span data-ttu-id="7878c-170">Sie wissen, wie Sie eine Registerkarte zur persönlichen Verwendung erstellen.</span><span class="sxs-lookup"><span data-stu-id="7878c-170">You know how to build a tab for personal use.</span></span> <span data-ttu-id="7878c-171">Schauen wir uns an, was es braucht, um eine Registerkarte für Team Kanäle und Chats zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="7878c-171">Let's look at what it takes to build a tab for team channels and chats.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7878c-172">Erstellen einer Kanal Registerkarte</span><span class="sxs-lookup"><span data-stu-id="7878c-172">Build a channel tab</span></span>](add-channel-tab.md)

## <a name="learn-more"></a><span data-ttu-id="7878c-173">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="7878c-173">Learn more</span></span>

* <span data-ttu-id="7878c-174">[Authentifizieren von Registerkarten Benutzern mit SSO](../../tabs/how-to/authentication/auth-aad-sso.md): Wenn Sie nur autorisierte Benutzer Ihrer Registerkarte anzeigen möchten, richten Sie einmaliges Anmelden (Single Sign-on, SSO) über Azure Active Directory (AD) ein.</span><span class="sxs-lookup"><span data-stu-id="7878c-174">[Authenticate tab users with SSO](../../tabs/how-to/authentication/auth-aad-sso.md): If you only want authorized users viewing your tab, set up single sign-on (SSO) through Azure Active Directory (AD).</span></span>
* <span data-ttu-id="7878c-175">[Einbetten von Inhalten aus einer vorhandenen Web-App oder Webseite](../../tabs/how-to/add-tab.md#tab-requirements): Wir haben gezeigt, wie Sie neue Inhalte für eine persönliche RegisterkarteErstellen, aber Sie können auch Inhalte aus einer externen URL laden.</span><span class="sxs-lookup"><span data-stu-id="7878c-175">[Embed content from an existing web app or webpage](../../tabs/how-to/add-tab.md#tab-requirements): We showed you how to create new content for a personal tab, but you can also load content from an external URL.</span></span>
* <span data-ttu-id="7878c-176">[Erstellen Sie eine nahtlose Benutzeroberfläche für Ihre Registerkarte](../../tabs/design/tabs.md): Lesen Sie die empfohlenen Richtlinien für das Entwerfen von Microsoft Teams-Registerkarten.</span><span class="sxs-lookup"><span data-stu-id="7878c-176">[Create a seamless experience for your tab](../../tabs/design/tabs.md): See the recommended guidelines for designing Teams tabs.</span></span>
* <span data-ttu-id="7878c-177">[Erstellen von Registerkarten für Mobilgeräte](../../tabs/design/tabs-mobile.md): Hier erfahren Sie, wie Sie Registerkarten für Smartphones und Tablets entwickeln.</span><span class="sxs-lookup"><span data-stu-id="7878c-177">[Build tabs for mobile](../../tabs/design/tabs-mobile.md): Understand how to develop tabs for smartphones and tablets.</span></span>

