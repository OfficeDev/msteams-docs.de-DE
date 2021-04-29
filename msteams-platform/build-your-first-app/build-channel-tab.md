---
title: Erste Schritte – Erstellen einer Kanal- und Gruppenregisterkarte
author: girliemac
description: Erstellen Sie mithilfe des Microsoft Teams Toolkits schnell einen Microsoft Teams-Kanal und eine Gruppenregisterkarte.
ms.author: timura
ms.date: 03/22/2020
ms.topic: tutorial
ms.openlocfilehash: 868a471499bf2015196b7b741e340d070d0ed458
ms.sourcegitcommit: 303fc214aa04757779a171337f31a6539f47fd03
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/28/2021
ms.locfileid: "52068746"
---
# <a name="build-your-first-channel-and-group-tab-for-microsoft-teams"></a><span data-ttu-id="92384-103">Erstellen Ihrer ersten Kanal- und Gruppenregisterkarte für Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="92384-103">Build your first channel and group tab for Microsoft Teams</span></span>

<span data-ttu-id="92384-104">In diesem Lernprogramm lernen  Sie, eine einfache Kanalregisterkarte zu erstellen, die auch als Gruppenregisterkarte bezeichnet *wird.* Dabei handelt es sich um eine Vollbildseite für einen Teamkanal oder Chat.</span><span class="sxs-lookup"><span data-stu-id="92384-104">This tutorial teaches you to build a basic *channel tab* also known as a *group tab*, which is a full-screen page for a team channel or chat.</span></span> <span data-ttu-id="92384-105">Sie können auch einige Aspekte dieser Art von Registerkarte konfigurieren, z. B. die Registerkarte umbenennen, damit sie für ihren Kanal sinnvoll ist, was sie in einer persönlichen Registerkarte nicht tun kann.</span><span class="sxs-lookup"><span data-stu-id="92384-105">You can also configure some aspects of this kind of tab, for example, rename the tab so it's meaningful to their channel, which you cannot do in a Personal Tab.</span></span>

## <a name="what-youll-learn"></a><span data-ttu-id="92384-106">Was Sie lernen werden</span><span class="sxs-lookup"><span data-stu-id="92384-106">What you'll learn</span></span>

* <span data-ttu-id="92384-107">Erstellen Sie ein App-Projekt mit dem Microsoft Teams Toolkit für Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="92384-107">Create an app project using the Microsoft Teams Toolkit for Visual Studio Code.</span></span>
* <span data-ttu-id="92384-108">Verstehen der App-Konfigurationen und des Gerüsts, die für Kanalregisterkarten relevant sind.</span><span class="sxs-lookup"><span data-stu-id="92384-108">Understand the app configurations and scaffolding relevant to channel tabs.</span></span>
* <span data-ttu-id="92384-109">Erstellen der Registerkarteninhalts- und Registerkartenkonfiguration.</span><span class="sxs-lookup"><span data-stu-id="92384-109">Create tab content and tab configuration.</span></span>
* <span data-ttu-id="92384-110">Erstellen und ausführen Sie Ihre App zu Testzwecken in Teams.</span><span class="sxs-lookup"><span data-stu-id="92384-110">Build and run your app in teams for testing.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="92384-111">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="92384-111">Prerequisites</span></span>

<span data-ttu-id="92384-112">Stellen Sie sicher, dass Sie wissen, wie Sie eine einfache Teams-App einrichten und erstellen.</span><span class="sxs-lookup"><span data-stu-id="92384-112">Make sure that you understand how to set up and build a simple Teams app.</span></span> <span data-ttu-id="92384-113">Weitere Informationen finden Sie unter [Erstellen Ihrer ersten Microsoft Teams "Hello, World!"-App.](../build-your-first-app/build-and-run.md)</span><span class="sxs-lookup"><span data-stu-id="92384-113">For more information, see [create your first Microsoft Teams "Hello, World!" app](../build-your-first-app/build-and-run.md).</span></span>

## <a name="1-create-your-app-project"></a><span data-ttu-id="92384-114">1. Erstellen Ihres App-Projekts</span><span class="sxs-lookup"><span data-stu-id="92384-114">1. Create your app project</span></span>

<span data-ttu-id="92384-115">Mit dem Microsoft Teams Toolkit können Sie Ihre App konfigurieren und das Gerüst einrichten, das für Kanal- und Gruppenregisterkarten relevant ist.</span><span class="sxs-lookup"><span data-stu-id="92384-115">The Microsoft Teams Toolkit helps you to configure your app and set up the scaffolding relevant to channel and group tabs.</span></span> <span data-ttu-id="92384-116">Sie enthält auch eine grundlegende Konfigurationsseite und Inhaltsseite, auf der ein "Hello, World!" angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="92384-116">It also contains a basic configuration page and content page that displays a "Hello, World!"</span></span> <span data-ttu-id="92384-117">Nachricht.</span><span class="sxs-lookup"><span data-stu-id="92384-117">message.</span></span>

<span data-ttu-id="92384-118">**So erstellen Sie Ihr App-Projekt**</span><span class="sxs-lookup"><span data-stu-id="92384-118">**To create your app project**</span></span>

1. Wechseln Sie zu Visual Studio Code, und wählen **Sie Microsoft Teams** auf der linken :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: Aktivitätsleiste aus.
1. <span data-ttu-id="92384-120">Melden Sie sich mit Ihrem Microsoft 365-Entwicklungskonto an, wenn Sie dazu aufgefordert werden.</span><span class="sxs-lookup"><span data-stu-id="92384-120">Sign in with your Microsoft 365 development account when prompted to do so.</span></span>
1. <span data-ttu-id="92384-121">Wählen Sie **auf dem Bildschirm** Projekt auswählen **JS** (JavaScript) unter **Kanal und Gruppen-App aus.**</span><span class="sxs-lookup"><span data-stu-id="92384-121">On the **Select project** screen, select **JS** (JavaScript) under **Channel and group app**.</span></span>
1. <span data-ttu-id="92384-122">Geben Sie einen Namen für Ihre Teams-App ein.</span><span class="sxs-lookup"><span data-stu-id="92384-122">Enter a name for your Teams app.</span></span> 

    > [!NOTE]
    > <span data-ttu-id="92384-123">Dies ist der Standardname für Ihre App und auch der Name des App-Projektverzeichnisses auf Ihrem lokalen Computer.</span><span class="sxs-lookup"><span data-stu-id="92384-123">This is the default name for your app and also the name of the app project directory on your local machine.</span></span>

1. <span data-ttu-id="92384-124">Wählen **Sie Die Registerkarte Gruppen- oder Teams-Kanal aus.**</span><span class="sxs-lookup"><span data-stu-id="92384-124">Select **Group or Teams channel tab**.</span></span>
1. <span data-ttu-id="92384-125">Wählen **Sie unten** auf dem Bildschirm Fertig stellen aus, um Ihr Projekt zu konfigurieren und das Projekt auf dem lokalen Computer zu speichern.</span><span class="sxs-lookup"><span data-stu-id="92384-125">Select **Finish** at the bottom of the screen to configure your project and save your project on your local machine.</span></span>  

## <a name="2-understand-your-app-project-components"></a><span data-ttu-id="92384-126">2. Verstehen Ihrer App-Projektkomponenten</span><span class="sxs-lookup"><span data-stu-id="92384-126">2. Understand your app project components</span></span>

<span data-ttu-id="92384-127">Viele der App-Konfigurationen und Gerüste werden automatisch eingerichtet, wenn Sie Ihr Projekt mit dem Toolkit erstellen.</span><span class="sxs-lookup"><span data-stu-id="92384-127">Much of the app configurations and scaffolding are set up automatically when you create your project with the toolkit.</span></span> <span data-ttu-id="92384-128">Sehen wir uns die Hauptkomponenten zum Erstellen einer Kanalregisterkarte an.</span><span class="sxs-lookup"><span data-stu-id="92384-128">Let's look at the main components for building a channel tab.</span></span>

* <span data-ttu-id="92384-129">**App-Konfigurationen:** Öffnen **Sie App Studio** im Toolkit, um Ihre App-Konfigurationen anzeigen und aktualisieren zu können.</span><span class="sxs-lookup"><span data-stu-id="92384-129">**App configurations**: Open **App Studio** in the toolkit to view and update your app configurations.</span></span>
* <span data-ttu-id="92384-130">**App-Gerüst:** Das App-Gerüst bietet die Komponenten, die zum Rendern Ihrer Kanalregisterkarte in Teams erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="92384-130">**App scaffolding**: The app scaffolding provides the components needed for rendering your channel tab in Teams.</span></span> <span data-ttu-id="92384-131">Es gibt eine Menge, mit der Sie arbeiten können, aber jetzt konzentrieren wir uns auf Folgendes:</span><span class="sxs-lookup"><span data-stu-id="92384-131">There's a lot you can work with, however, for now let's focus on the following:</span></span>
  * <span data-ttu-id="92384-132">Die Dateien im `src/components` Verzeichnis Ihres Projekts:</span><span class="sxs-lookup"><span data-stu-id="92384-132">The files located in the `src/components` directory of your project:</span></span>
    * <span data-ttu-id="92384-133">`Tab.js` zum Rendern der Inhaltsseite Ihrer Registerkarte.</span><span class="sxs-lookup"><span data-stu-id="92384-133">`Tab.js` for rendering your tab's content page.</span></span>
    * <span data-ttu-id="92384-134">`TabConfig.js` zum Rendern der Konfigurationsseite Ihrer Registerkarte.</span><span class="sxs-lookup"><span data-stu-id="92384-134">`TabConfig.js` for rendering your tab's configuration page.</span></span>
  * <span data-ttu-id="92384-135">Microsoft Teams JavaScript-Client-SDK, das in den Front-End-Komponenten Ihres Projekts vorinstalliert ist.</span><span class="sxs-lookup"><span data-stu-id="92384-135">Microsoft Teams JavaScript client SDK, which comes pre-loaded in your project's front-end components.</span></span>

## <a name="3-customize-your-tab-content-page"></a><span data-ttu-id="92384-136">3. Anpassen der Registerkarteninhaltsseite</span><span class="sxs-lookup"><span data-stu-id="92384-136">3. Customize your tab content page</span></span>

1. <span data-ttu-id="92384-137">Kopieren und ändern Sie das folgende Codebeispiel mit Informationen, die für Ihre Organisation relevant sind.</span><span class="sxs-lookup"><span data-stu-id="92384-137">Copy and modify the following code sample with information that's relevant to your organization.</span></span> <span data-ttu-id="92384-138">Sie können den Codeausschnitt auch wie folgt verwenden:</span><span class="sxs-lookup"><span data-stu-id="92384-138">You can also use the snippet as it is:</span></span>
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
1. <span data-ttu-id="92384-139">Wechseln Sie zum `src/components` Verzeichnis, und öffnen Sie die `Tab.js` Datei.</span><span class="sxs-lookup"><span data-stu-id="92384-139">Go to the `src/components` directory and open the `Tab.js` file.</span></span> <span data-ttu-id="92384-140">Suchen Sie `render()` die Funktion, und fügen Sie Den Code `return()` ein, wie im folgenden Beispiel gezeigt:</span><span class="sxs-lookup"><span data-stu-id="92384-140">Locate the `render()` function and paste your code inside `return()` as shown in the following example:</span></span>
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
1. <span data-ttu-id="92384-141">Wechseln Sie zum Verzeichnis, und aktualisieren Sie die Datei mit dem folgenden Code, um die E-Mail-Links in allen verwendeten `src/components` `App.css` Designs leichter zu lesen:</span><span class="sxs-lookup"><span data-stu-id="92384-141">Go to the `src/components` directory and update the `App.css` file with the following code to make the email links easier to read in any theme that is used:</span></span>
    ```CSS
    a {
      color: inherit;
    }
    ```

## <a name="4-customize-your-tab-configuration-page"></a><span data-ttu-id="92384-142">4. Anpassen der Registerkartenkonfigurationsseite</span><span class="sxs-lookup"><span data-stu-id="92384-142">4. Customize your tab configuration page</span></span>

<span data-ttu-id="92384-143">Jede Registerkarte in einem Kanal oder Chat verfügt über eine Konfigurationsseite, eine modale Mit mindestens einer Setupoption, die angezeigt wird, wenn Benutzer Ihre App hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="92384-143">Every tab in a channel or chat has a configuration page, a modal with at least one setup option that displays when users add your app.</span></span> <span data-ttu-id="92384-144">Auf der Konfigurationsseite werden Benutzer standardmäßig gefragt, ob sie den Kanal oder Chat benachrichtigen möchten, wenn die Registerkarte installiert ist.</span><span class="sxs-lookup"><span data-stu-id="92384-144">The configuration page by default asks users if they want to notify the channel or chat when the tab is installed.</span></span> <span data-ttu-id="92384-145">Sie können die Konfigurationsseite anpassen, indem Sie benutzerdefinierten Inhalt hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="92384-145">You can customize the configuration page by adding custom content.</span></span>

<span data-ttu-id="92384-146">Um benutzerdefinierten Inhalt hinzuzufügen, öffnen Sie die Datei aus dem Verzeichnis, und aktualisieren Sie den Platzhalterinhalt darin, wie `TabConfig.js` `src/components` im folgenden Beispiel `return()` gezeigt:</span><span class="sxs-lookup"><span data-stu-id="92384-146">To add custom content, open `TabConfig.js` file from the `src/components` directory and update the placeholder content inside `return()` as shown in the following example:</span></span>

  ```JavaScript
  return (
      <div>
        <h1>Add My Contoso Contacts</h1>
        <div>
          Select <b>Save</b> to add our organization's important contacts to this workspace.
        </div>
      </div>
  );
  ```
 
> [!TIP]
> <span data-ttu-id="92384-147">Geben Sie auf dieser Seite eine kurze Information zu Ihrer App, da dies das erste Mal ist, dass Benutzer darüber lesen.</span><span class="sxs-lookup"><span data-stu-id="92384-147">Give a brief information about your app on this page since this would be the first time users are reading about it.</span></span> <span data-ttu-id="92384-148">Sie können auch benutzerdefinierte Konfigurationsoptionen oder einen [Authentifizierungsworkflow](../tabs/how-to/authentication/auth-aad-sso.md)hinzufügen, der auf Registerkartenkonfigurationsseiten üblich ist.</span><span class="sxs-lookup"><span data-stu-id="92384-148">You can also include custom configuration options or an [authentication workflow](../tabs/how-to/authentication/auth-aad-sso.md), which is common on tab configuration pages.</span></span>

## <a name="5-customize-your-tab-name"></a><span data-ttu-id="92384-149">5. Anpassen des Registerkartennamens</span><span class="sxs-lookup"><span data-stu-id="92384-149">5. Customize your tab name</span></span>

<span data-ttu-id="92384-150">Wenn Sie eine Kanalregisterkarte hinzufügen, wird der App-Name standardmäßig angezeigt, z. B. **first-app**.</span><span class="sxs-lookup"><span data-stu-id="92384-150">When you add a channel tab, the app name displays by default, for example, **first-app**.</span></span> <span data-ttu-id="92384-151">Sie können auch einen Namen bereitstellen, der im Kontext der Gruppenzusammenarbeit sinnvoller ist, z. B. **Teamkontakte**:</span><span class="sxs-lookup"><span data-stu-id="92384-151">You can also provide a name that makes more sense in the context of group collaboration, for example, **Team Contacts**:</span></span>

1. <span data-ttu-id="92384-152">Wechseln Sie zum `src/components` Verzeichnis, und öffnen Sie die `TabConfig.js` Datei.</span><span class="sxs-lookup"><span data-stu-id="92384-152">Go to the `src/components` directory and open the `TabConfig.js` file.</span></span>
1. <span data-ttu-id="92384-153">Fügen Sie die Eigenschaft mit dem Registerkartennamen hinzu, den Sie standardmäßig unter anzeigen `suggestedDisplayName` `microsoftTeams.settings.setSettings` möchten, wie im folgenden Beispiel gezeigt:</span><span class="sxs-lookup"><span data-stu-id="92384-153">Add the `suggestedDisplayName` property with the tab name you want to display by default under `microsoftTeams.settings.setSettings` as shown in the following example:</span></span>

  ```JavaScript
    microsoftTeams.settings.setSettings({
    "contentUrl": "https://localhost:3000/tab",
    "suggestedDisplayName": "Team Contacts"
  });
  ```

## <a name="6-build-and-run-your-app"></a><span data-ttu-id="92384-154">6. Erstellen und Ausführen Ihrer App</span><span class="sxs-lookup"><span data-stu-id="92384-154">6. Build and run your app</span></span>

<span data-ttu-id="92384-155">In diesem Lernprogramm erfahren Sie, wie Sie Ihre App lokal erstellen und ausführen können.</span><span class="sxs-lookup"><span data-stu-id="92384-155">This tutorial teaches you to build and run your app locally.</span></span> 

1. <span data-ttu-id="92384-156">Wechseln Sie zum Stammverzeichnis Ihres App-Projekts im Terminal.</span><span class="sxs-lookup"><span data-stu-id="92384-156">Go to the root directory of your app project in Terminal.</span></span>
1. <span data-ttu-id="92384-157">Führen Sie `npm install` aus.</span><span class="sxs-lookup"><span data-stu-id="92384-157">Run `npm install`.</span></span>
1. <span data-ttu-id="92384-158">Führen Sie `npm start` aus.</span><span class="sxs-lookup"><span data-stu-id="92384-158">Run `npm start`.</span></span>

<span data-ttu-id="92384-159">Diese Informationen finden Sie auch im `README` Abschnitt des Toolkits.</span><span class="sxs-lookup"><span data-stu-id="92384-159">This information is also present in the `README` section of the toolkit.</span></span>
<span data-ttu-id="92384-160">Ihre App wird nach `https://localhost:3000` dem erfolgreichen **Kompilierten ausgeführt!**</span><span class="sxs-lookup"><span data-stu-id="92384-160">Your app is running on `https://localhost:3000` after the **Compiled successfully!**</span></span> <span data-ttu-id="92384-161">wird im Terminal angezeigt.</span><span class="sxs-lookup"><span data-stu-id="92384-161">message appears in the terminal.</span></span> 

## <a name="7-sideload-your-app-in-teams"></a><span data-ttu-id="92384-162">7. Querladen Ihrer App in Teams</span><span class="sxs-lookup"><span data-stu-id="92384-162">7. Sideload your app in Teams</span></span>

<span data-ttu-id="92384-163">Ihre App kann in Teams testen.</span><span class="sxs-lookup"><span data-stu-id="92384-163">Your app is ready to test in Teams.</span></span> <span data-ttu-id="92384-164">Dazu müssen Sie über ein Konto verfügen, das das Querladen von Apps zulässt.</span><span class="sxs-lookup"><span data-stu-id="92384-164">To do this, you must have an account that allows app sideloading.</span></span> 

1. <span data-ttu-id="92384-165">Öffnen Sie einen Teams-Webclient in Visual Studio Code mit der **F5-Taste.**</span><span class="sxs-lookup"><span data-stu-id="92384-165">Open a Teams web client in Visual Studio Code with the **F5** key.</span></span>
1. <span data-ttu-id="92384-166">Fügen Sie ( ) als vertrauenswürdig hinzu, indem Sie die folgenden Schritte ausführen, um die Anzeige von App-Inhalten `localhost` in Teams zu ermöglichen:</span><span class="sxs-lookup"><span data-stu-id="92384-166">Add (`localhost`) as trustworthy by following these steps to enable your app content to display in Teams:</span></span>

   1. <span data-ttu-id="92384-167">Öffnen Sie eine neue Registerkarte im gleichen Browserfenster (Standardmäßig Google Chrome), das mit der **F5-Taste geöffnet** wurde.</span><span class="sxs-lookup"><span data-stu-id="92384-167">Open a new tab in the same browser window (Google Chrome by default) which opened with the **F5** key.</span></span>
   1. <span data-ttu-id="92384-168">Öffnen `https://localhost:3000/tab` Sie die Seite, und fahren Sie mit der Seite fort.</span><span class="sxs-lookup"><span data-stu-id="92384-168">Open `https://localhost:3000/tab` and proceed to the page.</span></span>

1. <span data-ttu-id="92384-169">Wählen **Sie Zu einem Team hinzufügen oder** zu einem Chat **hinzufügen** aus, und suchen Sie einen Kanal oder Chat, den Sie für Tests über den modalen Modus in Teams verwenden können.</span><span class="sxs-lookup"><span data-stu-id="92384-169">Select **Add to a team** or **Add to a chat** and locate a channel or chat you can use for testing from the modal in Teams.</span></span>
1. <span data-ttu-id="92384-170">Wählen **Sie Tab einrichten aus.** Die Konfigurationsseite wird modal angezeigt.</span><span class="sxs-lookup"><span data-stu-id="92384-170">Select **Set up a tab**. The configuration page displays in a modal.</span></span>

   :::image type="content" source="../assets/images/tabs/channel-tab-tutorial-content.png" alt-text="Screenshot einer Kanalregisterkartenkonfigurationsseite.":::

1. <span data-ttu-id="92384-172">Wählen **Sie Speichern** aus, um die Registerkarte zu konfigurieren. Die folgende Inhaltsseite wird angezeigt:</span><span class="sxs-lookup"><span data-stu-id="92384-172">Select **Save** to configure the tab. The following content page appears:</span></span>

   :::image type="content" source="../assets/images/tabs/channel-tab-tutorial-content-installed.png" alt-text="Screenshot einer Kanalregisterkarte mit statischer Inhaltsansicht.":::

## <a name="see-also"></a><span data-ttu-id="92384-174">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="92384-174">See also</span></span>

* [<span data-ttu-id="92384-175">Erstellen und Ausführen Ihrer ersten Microsoft Teams-App</span><span class="sxs-lookup"><span data-stu-id="92384-175">Build and run your first Microsoft Teams app</span></span>](../build-your-first-app/build-and-run.md) 
* [<span data-ttu-id="92384-176">Microsoft Teams JavaScript-Client-SDK</span><span class="sxs-lookup"><span data-stu-id="92384-176">Teams JavaScript client SDK</span></span>](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/?view=msteams-client-js-latest&preserve-view=true)
* [<span data-ttu-id="92384-177">Entwerfen Ihrer Registerkarte für Microsoft Teams Desktop und Web</span><span class="sxs-lookup"><span data-stu-id="92384-177">Designing your tab for Microsoft Teams desktop and web</span></span>](../tabs/design/tabs.md) 
* [<span data-ttu-id="92384-178">Entwerfen Ihrer Microsoft Teams-App mit Benutzeroberflächenvorlagen</span><span class="sxs-lookup"><span data-stu-id="92384-178">Designing your Microsoft Teams app with UI templates</span></span>](../concepts/design/design-teams-app-ui-templates.md) 
* [<span data-ttu-id="92384-179">Registerkarten auf mobilen Geräten</span><span class="sxs-lookup"><span data-stu-id="92384-179">Tabs on mobile</span></span>](../tabs/design/tabs-mobile.md)
* [<span data-ttu-id="92384-180">Unterstützung für einmaliges Anmelden (Single Sign-On, SSO) für Registerkarten</span><span class="sxs-lookup"><span data-stu-id="92384-180">Single sign-on (SSO) support for tabs</span></span>](../tabs/how-to/authentication/auth-aad-sso.md)
* [<span data-ttu-id="92384-181">Übersicht über Microsoft Teams-APIs</span><span class="sxs-lookup"><span data-stu-id="92384-181">Microsoft Teams API overview</span></span>](https://docs.microsoft.com/graph/teams-concept-overview)
* [<span data-ttu-id="92384-182">Erstellen einer benutzerdefinierten persönlichen Registerkarte mit Node.js und dem Yeoman-Generator für Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="92384-182">Create a custom personal tab with Node.js and the Yeoman Generator for Microsoft Teams</span></span>](../tabs/quickstarts/create-personal-tab-node-yeoman.md)

## <a name="next-step"></a><span data-ttu-id="92384-183">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="92384-183">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="92384-184">Erstellen eines Bots</span><span class="sxs-lookup"><span data-stu-id="92384-184">Build a bot</span></span>](../build-your-first-app/build-bot.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="92384-185">Erstellen einer Messaging-Erweiterung</span><span class="sxs-lookup"><span data-stu-id="92384-185">Build a messaging extension</span></span>](../build-your-first-app/build-messaging-extension.md)