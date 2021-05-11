---
title: Erste Schritte – Erstellen einer persönlichen Registerkarte
author: girliemac
description: Erstellen Sie schnell Microsoft Teams persönliche Registerkarte mit dem Microsoft Teams Toolkit.
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
# <a name="build-a-basic-personal-tab-for-microsoft-teams"></a><span data-ttu-id="8f370-103">Erstellen einer einfachen persönlichen Registerkarte für Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="8f370-103">Build a basic personal tab for Microsoft Teams</span></span>

<span data-ttu-id="8f370-104">In diesem Lernprogramm lernen Sie, eine grundlegende persönliche Registerkarte in Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="8f370-104">This tutorial teaches you to build a basic personal tab in Microsoft Teams.</span></span> <span data-ttu-id="8f370-105">Registerkarten sind eine einfache Möglichkeit, Informationen in Ihrer App anzuzeigen, indem Sie Webinhalte in einer Teams.</span><span class="sxs-lookup"><span data-stu-id="8f370-105">Tabs are a simple way to surface information in your app by hosting web content in Teams.</span></span> <span data-ttu-id="8f370-106">Registerkarten sind ein gängiges Feature von persönlichen Apps, die einen privaten Arbeitsbereich für einzelne Benutzer bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="8f370-106">Tabs are a common feature of personal apps that provide a private workspace for individual users.</span></span> <span data-ttu-id="8f370-107">Persönliche Registerkarten sind die am nächsten zu einer herkömmlichen Weberfahrung in Teams.</span><span class="sxs-lookup"><span data-stu-id="8f370-107">Personal tabs are the closest thing to a traditional web experience in Teams.</span></span> 

## <a name="what-youll-learn"></a><span data-ttu-id="8f370-108">Was Sie lernen werden</span><span class="sxs-lookup"><span data-stu-id="8f370-108">What you'll learn</span></span>

* <span data-ttu-id="8f370-109">Verstehen der App-Konfigurationen und des Gerüsts, die für persönliche Registerkarten relevant sind.</span><span class="sxs-lookup"><span data-stu-id="8f370-109">Understand the app configurations and scaffolding relevant to personal tabs.</span></span>
* <span data-ttu-id="8f370-110">Erstellen Sie einen Registerkarteninhalt mit einer Kontaktliste Ihrer Organisation.</span><span class="sxs-lookup"><span data-stu-id="8f370-110">Create a tab content with a contact list of your organization.</span></span>
* <span data-ttu-id="8f370-111">Aktualisieren sie das Farbdesign einer Registerkarte basierend auf den Benutzereinstellungen.</span><span class="sxs-lookup"><span data-stu-id="8f370-111">Update a tab's color theme based on user preference.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8f370-112">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="8f370-112">Prerequisites</span></span>

<span data-ttu-id="8f370-113">Stellen Sie sicher, dass Sie verstehen, wie Sie eine einfache App Teams erstellen.</span><span class="sxs-lookup"><span data-stu-id="8f370-113">Make sure that you understand how to set up and build a simple Teams app.</span></span> <span data-ttu-id="8f370-114">Weitere Informationen finden Sie unter [Create your first Microsoft Teams "Hello, World!" app](../build-your-first-app/build-and-run.md).</span><span class="sxs-lookup"><span data-stu-id="8f370-114">For more information, see [create your first Microsoft Teams "Hello, World!" app](../build-your-first-app/build-and-run.md).</span></span>

## <a name="1-understand-your-app-project-components"></a><span data-ttu-id="8f370-115">1. Verstehen ihrer App-Projektkomponenten</span><span class="sxs-lookup"><span data-stu-id="8f370-115">1. Understand your app project components</span></span>

<span data-ttu-id="8f370-116">Nachdem Sie eine einfache persönliche Registerkarte erstellt haben, stellt das generierte App-Gerüst die Komponenten zum Rendern Ihrer persönlichen Registerkarte in Teams.</span><span class="sxs-lookup"><span data-stu-id="8f370-116">After you have created a basic personal tab, the generated app scaffold provides the components for rendering your personal tab in Teams.</span></span> <span data-ttu-id="8f370-117">Es gibt eine Menge, mit der Sie arbeiten können, aber lassen Sie uns uns jetzt auf Folgendes konzentrieren:</span><span class="sxs-lookup"><span data-stu-id="8f370-117">There's a lot you can work with, but for now let us focus on the following:</span></span> 

* <span data-ttu-id="8f370-118">`Tab.js` datei im `src/components` Verzeichnis Ihres Projekts.</span><span class="sxs-lookup"><span data-stu-id="8f370-118">`Tab.js` file in the `src/components` directory of your project.</span></span> <span data-ttu-id="8f370-119">Dies ist für das Rendern der Registerkarteninhaltsseite.</span><span class="sxs-lookup"><span data-stu-id="8f370-119">This is for rendering your tab content page.</span></span>
* <span data-ttu-id="8f370-120">Microsoft Teams JavaScript-Client-SDK, das in den Front-End-Komponenten Ihres Projekts vorinstalliert ist.</span><span class="sxs-lookup"><span data-stu-id="8f370-120">Microsoft Teams JavaScript client SDK, which is pre-loaded in your project's front-end components.</span></span>

<span data-ttu-id="8f370-121">Wie Sie im Abschnitt oben in der Datei feststellen können, verwendet der Beispielcode React , eine `import` `Tabs.js` Open-Source-JavaScript-Bibliothek zum Erstellen von Benutzeroberflächen. [](https://reactjs.org/)</span><span class="sxs-lookup"><span data-stu-id="8f370-121">As you may notice from the `import` section at the top of `Tabs.js` file, the sample code uses [React](https://reactjs.org/), an open-source JavaScript library for building user-interface.</span></span> 

> [!NOTE]
> <span data-ttu-id="8f370-122">Obwohl die React _für die_ Teams nicht erforderlich ist, werden Sie in diesem Lernprogramm React.</span><span class="sxs-lookup"><span data-stu-id="8f370-122">Although using React is _not_ required for Teams development, this tutorial teaches you with React.</span></span>

## <a name="2-customize-your-tab-content-page"></a><span data-ttu-id="8f370-123">2. Anpassen der Registerkarteninhaltsseite</span><span class="sxs-lookup"><span data-stu-id="8f370-123">2. Customize your tab content page</span></span>

<span data-ttu-id="8f370-124">Sie können Ihre Registerkarteninhaltsseite anpassen, um eine Liste wichtiger Kontakte in Ihrer Organisation zu rendern.</span><span class="sxs-lookup"><span data-stu-id="8f370-124">You can customize your tab content page to render a list of important contacts in your organization.</span></span> 

<span data-ttu-id="8f370-125">**So passen Sie ihre Registerkarteninhaltsseite an**</span><span class="sxs-lookup"><span data-stu-id="8f370-125">**To customize your tab content page**</span></span>

1. <span data-ttu-id="8f370-126">Kopieren und ändern Sie das folgende Codebeispiel mit Informationen, die für Sie relevant sind.</span><span class="sxs-lookup"><span data-stu-id="8f370-126">Copy and modify the following code sample with information that's relevant to you.</span></span> <span data-ttu-id="8f370-127">Sie können den Code auch wie folgt verwenden:</span><span class="sxs-lookup"><span data-stu-id="8f370-127">You can also use the code as is:</span></span> 
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
1. <span data-ttu-id="8f370-128">Zum `src/components` Verzeichnis, und öffnen Sie die `Tab.js` Datei.</span><span class="sxs-lookup"><span data-stu-id="8f370-128">Got to the `src/components` directory and open the `Tab.js` file.</span></span> 
1. <span data-ttu-id="8f370-129">Wechseln Sie zu, und ersetzen Sie den Vorlagencode durch den darin geänderten `render()` `return()` Code, wie im folgenden Beispiel gezeigt:</span><span class="sxs-lookup"><span data-stu-id="8f370-129">Go to `render()` and replace the template code with the modified code inside `return()` as shown in the following example:</span></span>
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
1. <span data-ttu-id="8f370-130">Wechseln Sie zum Verzeichnis, und ändern Sie die Datei mit dem folgenden Code, um die E-Mail-Links mit jedem verwendeten Design `src/components` `App.css` leichter zu lesen:</span><span class="sxs-lookup"><span data-stu-id="8f370-130">Go to the `src/components` directory and modify the `App.css` file with the following code to make the email links easier to read with any theme that is used:</span></span>
    ```CSS
    a {
      color: inherit;
    }
    ```
1. <span data-ttu-id="8f370-131">Speichern Sie Ihre Änderungen.</span><span class="sxs-lookup"><span data-stu-id="8f370-131">Save your changes.</span></span> 

   <span data-ttu-id="8f370-132">Sie können den neuen Inhalt auf der Registerkarte Ihrer App in der Teams.</span><span class="sxs-lookup"><span data-stu-id="8f370-132">You can view the new content in your app's tab in Teams.</span></span>

   :::image type="content" source="../assets/images/build-your-first-app/personal-tab-tutorial-content.png" alt-text="Screenshot einer persönlichen Registerkarte mit statischem Inhalt.":::

## <a name="3-update-your-tab-theme"></a><span data-ttu-id="8f370-134">3. Aktualisieren Des Registerkartendesigns</span><span class="sxs-lookup"><span data-stu-id="8f370-134">3. Update your tab theme</span></span>

<span data-ttu-id="8f370-135">Es ist wichtig, dass Ihre Registerkarte ein Design hat, das sich für die Teams.</span><span class="sxs-lookup"><span data-stu-id="8f370-135">It is important for your tab to have a theme that feels native to Teams.</span></span> <span data-ttu-id="8f370-136">Sie müssen Ihre Registerkarte mit dem Teams mischen.</span><span class="sxs-lookup"><span data-stu-id="8f370-136">You must blend your tab with the Teams theme.</span></span> <span data-ttu-id="8f370-137">Ihre Benutzer bevorzugen in der Regel Standard-Designs (hell), dunkel oder mit hohem Kontrast.</span><span class="sxs-lookup"><span data-stu-id="8f370-137">Your users generally prefer default (light), dark, or high contrast themes.</span></span> <span data-ttu-id="8f370-138">Wie Sie vielleicht im letzten Screenshot bemerkt haben, hat Ihre Registerkarte immer noch einen hellen Hintergrund, wenn Ihr Benutzer das dunkle Design verwendet.</span><span class="sxs-lookup"><span data-stu-id="8f370-138">As you might have noticed in the last screenshot, your tab still has a light background when your user is using the dark theme.</span></span> <span data-ttu-id="8f370-139">Dies ist keine empfohlene Benutzeroberfläche.</span><span class="sxs-lookup"><span data-stu-id="8f370-139">This is not a recommended user experience.</span></span>

<span data-ttu-id="8f370-140">Das Teams JavaScript-Client-SDK kann Ihre App auf Designänderungen im Client aufmerksam machen und darauf reagieren.</span><span class="sxs-lookup"><span data-stu-id="8f370-140">The Teams JavaScript client SDK can make your app aware of and react to theme changes in the client.</span></span> <span data-ttu-id="8f370-141">Gehen Sie dazu wie folgt vor:</span><span class="sxs-lookup"><span data-stu-id="8f370-141">To do this, follow these steps:</span></span>

1. <span data-ttu-id="8f370-142">**Get context about the configured Teams client theme** Der Aufruf in Ihrer Datei bietet einen Kontext zum konfigurierten Clientdesign (z. B. `microsoftTeams.getContext()` `Tab.js` dunkles Design).</span><span class="sxs-lookup"><span data-stu-id="8f370-142">**Get context about the configured Teams client theme** The `microsoftTeams.getContext()` call in your `Tab.js` file, provides some context about the configured client theme (such as dark theme).</span></span> <span data-ttu-id="8f370-143">Der folgende Code zugrifft `context` auf die Schnittstelle und ihre Eigenschaften:</span><span class="sxs-lookup"><span data-stu-id="8f370-143">The following code accesses the `context` interface and its properties:</span></span>

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
1. <span data-ttu-id="8f370-144">**Erstellen eines Designänderungshandlers** Mit den eigenschaften in der Hand hat Ihre App ein solides Verständnis der Vorgänge um sie `context` herum in Teams.</span><span class="sxs-lookup"><span data-stu-id="8f370-144">**Create a theme change handler** With the `context` properties in hand, your app has a solid understanding of what's happening around it in Teams.</span></span> <span data-ttu-id="8f370-145">Die App hat jedoch immer noch keine Darstellung, die das Design wiederspiegelt, wenn ein Benutzer sie aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="8f370-145">However, the app still doesn't have an appearance reflecting the theme when a user updates it.</span></span>

   <span data-ttu-id="8f370-146">Sie benötigen einen Handler, um den Zustand Ihrer App mit dem Design zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="8f370-146">You need a handler to update your app's state with the theme.</span></span> <span data-ttu-id="8f370-147">Um einen Handler zu erstellen, fügen Sie den folgenden Designänderungshandler unmittelbar nach dem Aufruf `microsoftTeams.getContext()` ein:</span><span class="sxs-lookup"><span data-stu-id="8f370-147">To create a handler, insert the following theme change handler immediately after the `microsoftTeams.getContext()` call:</span></span>

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
1. <span data-ttu-id="8f370-148">**Übereinstimmung mit den Designformatvorlagen** Ihr Designänderungshandler ist eingerichtet, Sie müssen jedoch weiterhin auf Änderungen reagieren und die Farben Ihrer Registerkarte am aktuellen Design ausrichten.</span><span class="sxs-lookup"><span data-stu-id="8f370-148">**Match the theme styles** Your theme change handler is in place, however, you still have to respond to changes and align your tab's colors with the current theme.</span></span>

   <span data-ttu-id="8f370-149">Speichern Sie in der Funktion den vom Designänderungshandler bereitgestellten Status `render()` in `isTheme` :</span><span class="sxs-lookup"><span data-stu-id="8f370-149">In the `render()` function, store the state provided by the theme change handler in `isTheme`:</span></span>

    ```JavaScript
      const isTheme = this.state.context.theme
    ```
    
    > [!NOTE]
    > <span data-ttu-id="8f370-150">Dieses Beispiel ist nur eine Möglichkeit, Formatvorlagen auf Ihre Registerkarte anzuwenden. Verwenden Sie den Code wie folgt, erweitern Sie ihn, oder schreiben Sie Eigenes.</span><span class="sxs-lookup"><span data-stu-id="8f370-150">This example is just one way you might apply styles to your tab. Use the code as is, expand on it, or write your own.</span></span>

    <span data-ttu-id="8f370-151">Nachdem Sie den vom Designänderungshandler bereitgestellten Status gespeichert haben, stellen Sie die bedingte Logik bereit, um die Formatvorlagen Ihrer Registerkarte basierend auf dem aktuellen Design zu rendern.</span><span class="sxs-lookup"><span data-stu-id="8f370-151">After storing the state provided by the theme change handler, provide the conditional logic to render your tab's styles based on the current theme.</span></span> <span data-ttu-id="8f370-152">Das folgende Beispiel zeigt eine grundlegende Möglichkeit dazu:</span><span class="sxs-lookup"><span data-stu-id="8f370-152">The following example shows a basic way to do this:</span></span>

    1. <span data-ttu-id="8f370-153">Wechseln Sie `render()` zu, und überprüfen Sie das aktuelle Design in `isTheme` .</span><span class="sxs-lookup"><span data-stu-id="8f370-153">Go to `render()` and check the current theme in `isTheme`.</span></span>
    1. <span data-ttu-id="8f370-154">Erstellen Sie `newTheme` ein Objekt mit CSS-Eigenschaften, die für das aktuelle Design relevant sind.</span><span class="sxs-lookup"><span data-stu-id="8f370-154">Create a `newTheme` object with CSS properties relevant to the current theme.</span></span>
    1. <span data-ttu-id="8f370-155">Wenden Sie das folgende CSS auf das Stamm-HTML-Element Ihres Registerkarteninhalts an ( `<div style={newTheme}>` ):</span><span class="sxs-lookup"><span data-stu-id="8f370-155">Apply the following CSS to your tab content's root HTML element (`<div style={newTheme}>`):</span></span>

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

       <span data-ttu-id="8f370-156">Überprüfen Sie ihre Registerkarte in Teams.</span><span class="sxs-lookup"><span data-stu-id="8f370-156">Check your tab in Teams.</span></span> <span data-ttu-id="8f370-157">Das Erscheinungsbild entspricht nun eng mit dem dunklen Design.</span><span class="sxs-lookup"><span data-stu-id="8f370-157">The appearance now closely matches the dark theme.</span></span>

       :::image type="content" source="../assets/images/build-your-first-app/personal-tab-tutorial-updated-theme.png" alt-text="Screenshot einer persönlichen Registerkarte mit statischer Inhaltsansicht.":::

## <a name="see-also"></a><span data-ttu-id="8f370-159">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="8f370-159">See also</span></span>

* [<span data-ttu-id="8f370-160">Microsoft Teams JavaScript-Client-SDK</span><span class="sxs-lookup"><span data-stu-id="8f370-160">Teams JavaScript client SDK</span></span>](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/?view=msteams-client-js-latest&preserve-view=true)
* [<span data-ttu-id="8f370-161">Entwerfen Ihrer Registerkarte für Microsoft Teams Desktop und Web</span><span class="sxs-lookup"><span data-stu-id="8f370-161">Designing your tab for Microsoft Teams desktop and web</span></span>](../tabs/design/tabs.md) 
* [<span data-ttu-id="8f370-162">Kontextschnittstelle</span><span class="sxs-lookup"><span data-stu-id="8f370-162">Context interface</span></span>](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/context?view=msteams-client-js-latest&preserve-view=true)
* [<span data-ttu-id="8f370-163">Entwerfen Ihrer Microsoft Teams-App mit Benutzeroberflächenvorlagen</span><span class="sxs-lookup"><span data-stu-id="8f370-163">Designing your Microsoft Teams app with UI templates</span></span>](../concepts/design/design-teams-app-ui-templates.md) 
* [<span data-ttu-id="8f370-164">Registerkarten auf mobilen Geräten</span><span class="sxs-lookup"><span data-stu-id="8f370-164">Tabs on mobile</span></span>](../tabs/design/tabs-mobile.md)
* [<span data-ttu-id="8f370-165">Unterstützung für einmaliges Anmelden (Single Sign-On, SSO) für Registerkarten</span><span class="sxs-lookup"><span data-stu-id="8f370-165">Single sign-on (SSO) support for tabs</span></span>](../tabs/how-to/authentication/auth-aad-sso.md)
* [<span data-ttu-id="8f370-166">Übersicht über Microsoft Teams-APIs</span><span class="sxs-lookup"><span data-stu-id="8f370-166">Microsoft Teams API overview</span></span>](https://docs.microsoft.com/graph/teams-concept-overview)
* [<span data-ttu-id="8f370-167">Erstellen Sie eine benutzerdefinierte persönliche Registerkarte mit Node.js und dem Yeoman Generator für Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="8f370-167">Create a custom personal tab with Node.js and the Yeoman Generator for Microsoft Teams</span></span>](../tabs/quickstarts/create-personal-tab-node-yeoman.md)

## <a name="next-step"></a><span data-ttu-id="8f370-168">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="8f370-168">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="8f370-169">Erstellen einer Kanalregisterkarte</span><span class="sxs-lookup"><span data-stu-id="8f370-169">Build a channel tab</span></span>](../build-your-first-app/build-channel-tab.md)