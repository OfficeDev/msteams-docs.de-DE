---
title: Erste Schritte - Erstellen eines Kanals und einer Gruppenregisterkarte
author: girliemac
description: Erstellen Sie schnell eine Microsoft Teams Kanal- und Gruppenregisterkarte mit dem Microsoft Teams Toolkit.
ms.author: timura
ms.date: 03/22/2020
ms.topic: tutorial
ms.openlocfilehash: ff9cfbfb7d099db52966f119add4ce8729929aa1
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566068"
---
# <a name="build-your-first-channel-and-group-tab-for-microsoft-teams"></a><span data-ttu-id="63ab8-103">Erstellen Sie Ihre erste Kanal- und Gruppenregisterkarte für Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="63ab8-103">Build your first channel and group tab for Microsoft Teams</span></span>

<span data-ttu-id="63ab8-104">In diesem Tutorial lernen Sie an, eine grundlegende *Kanalregisterkarte* zu erstellen, die auch als *Gruppenregisterkarte* bezeichnet wird, die eine Vollbildseite für einen Teamkanal oder Chat ist.</span><span class="sxs-lookup"><span data-stu-id="63ab8-104">This tutorial teaches you to build a basic *channel tab* also known as a *group tab*, which is a full-screen page for a team channel or chat.</span></span> <span data-ttu-id="63ab8-105">Sie können auch einige Aspekte dieser Art von Registerkarte konfigurieren, z. B. die Registerkarte umbenennen, sodass sie für ihren Kanal sinnvoll ist, was Sie in einer persönlichen Registerkarte nicht tun können.</span><span class="sxs-lookup"><span data-stu-id="63ab8-105">You can also configure some aspects of this kind of tab, for example, rename the tab so it's meaningful to their channel, which you cannot do in a Personal Tab.</span></span>

## <a name="what-youll-learn"></a><span data-ttu-id="63ab8-106">Was Sie lernen werden</span><span class="sxs-lookup"><span data-stu-id="63ab8-106">What you'll learn</span></span>

* <span data-ttu-id="63ab8-107">Erstellen Sie ein App-Projekt mit dem Microsoft Teams Toolkit für Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="63ab8-107">Create an app project using the Microsoft Teams Toolkit for Visual Studio Code.</span></span>
* <span data-ttu-id="63ab8-108">Verstehen Sie die App-Konfigurationen und Gerüste, die für Kanalregisterkarten relevant sind.</span><span class="sxs-lookup"><span data-stu-id="63ab8-108">Understand the app configurations and scaffolding relevant to channel tabs.</span></span>
* <span data-ttu-id="63ab8-109">Erstellen Sie Dentabinhalt und die Registerkartenkonfiguration.</span><span class="sxs-lookup"><span data-stu-id="63ab8-109">Create tab content and tab configuration.</span></span>
* <span data-ttu-id="63ab8-110">Erstellen und führen Sie Ihre App in Teams zum Testen aus.</span><span class="sxs-lookup"><span data-stu-id="63ab8-110">Build and run your app in teams for testing.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="63ab8-111">Voraussetzungen</span><span class="sxs-lookup"><span data-stu-id="63ab8-111">Prerequisites</span></span>

<span data-ttu-id="63ab8-112">Stellen Sie sicher, dass Sie verstehen, wie Sie eine einfache Teams-App einrichten und erstellen.</span><span class="sxs-lookup"><span data-stu-id="63ab8-112">Make sure that you understand how to set up and build a simple Teams app.</span></span> <span data-ttu-id="63ab8-113">Weitere Informationen finden Sie [unter Erstellen Ihrer ersten Microsoft Teams "Hello, World!"-App](../build-your-first-app/build-and-run.md).</span><span class="sxs-lookup"><span data-stu-id="63ab8-113">For more information, see [create your first Microsoft Teams "Hello, World!" app](../build-your-first-app/build-and-run.md).</span></span>

## <a name="1-create-your-app-project"></a><span data-ttu-id="63ab8-114">1. Erstellen Sie Ihr App-Projekt</span><span class="sxs-lookup"><span data-stu-id="63ab8-114">1. Create your app project</span></span>

<span data-ttu-id="63ab8-115">Das Microsoft Teams Toolkit hilft Ihnen, Ihre App zu konfigurieren und das Gerüst einzurichten, das für Kanal- und Gruppenregisterkarten relevant ist.</span><span class="sxs-lookup"><span data-stu-id="63ab8-115">The Microsoft Teams Toolkit helps you to configure your app and set up the scaffolding relevant to channel and group tabs.</span></span> <span data-ttu-id="63ab8-116">Es enthält auch eine grundlegende Konfigurationsseite und Inhaltsseite, die ein "Hallo, Welt!" anzeigt.</span><span class="sxs-lookup"><span data-stu-id="63ab8-116">It also contains a basic configuration page and content page that displays a "Hello, World!"</span></span> <span data-ttu-id="63ab8-117">Nachricht.</span><span class="sxs-lookup"><span data-stu-id="63ab8-117">message.</span></span>

<span data-ttu-id="63ab8-118">**So erstellen Sie Ihr App-Projekt**</span><span class="sxs-lookup"><span data-stu-id="63ab8-118">**To create your app project**</span></span>

1. Wechseln Sie zu Visual Studio Code und wählen Sie **Microsoft Teams** :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: auf der linken Aktivitätsleiste aus.
1. <span data-ttu-id="63ab8-120">Melden Sie sich mit Ihrem Microsoft 365-Entwicklungskonto an, wenn Sie dazu aufgefordert werden.</span><span class="sxs-lookup"><span data-stu-id="63ab8-120">Sign in with your Microsoft 365 development account when prompted to do so.</span></span>
1. <span data-ttu-id="63ab8-121">Wählen Sie auf dem Bildschirm **Projekt** auswählen **JS** (JavaScript) unter **Kanal- und Gruppen-App** aus.</span><span class="sxs-lookup"><span data-stu-id="63ab8-121">On the **Select project** screen, select **JS** (JavaScript) under **Channel and group app**.</span></span>
1. <span data-ttu-id="63ab8-122">Geben Sie einen Namen für Ihre Teams App ein.</span><span class="sxs-lookup"><span data-stu-id="63ab8-122">Enter a name for your Teams app.</span></span> 

    > [!NOTE]
    > <span data-ttu-id="63ab8-123">Dies ist der Standardname für Ihre App und auch der Name des App-Projektverzeichnisses auf Ihrem lokalen Computer.</span><span class="sxs-lookup"><span data-stu-id="63ab8-123">This is the default name for your app and also the name of the app project directory on your local machine.</span></span>

1. <span data-ttu-id="63ab8-124">Wählen Sie **Gruppe oder Teams Kanalregisterkarte**.</span><span class="sxs-lookup"><span data-stu-id="63ab8-124">Select **Group or Teams channel tab**.</span></span>
1. <span data-ttu-id="63ab8-125">Wählen Sie am unteren Bildschirmrand **fertig** aus, um das Projekt zu konfigurieren und das Projekt auf dem lokalen Computer zu speichern.</span><span class="sxs-lookup"><span data-stu-id="63ab8-125">Select **Finish** at the bottom of the screen to configure your project and save your project on your local machine.</span></span>  

## <a name="2-understand-your-app-project-components"></a><span data-ttu-id="63ab8-126">2. Verstehen Ihrer App-Projektkomponenten</span><span class="sxs-lookup"><span data-stu-id="63ab8-126">2. Understand your app project components</span></span>

<span data-ttu-id="63ab8-127">Ein Großteil der App-Konfigurationen und Gerüste wird automatisch eingerichtet, wenn Sie Ihr Projekt mit dem Toolkit erstellen.</span><span class="sxs-lookup"><span data-stu-id="63ab8-127">Much of the app configurations and scaffolding are set up automatically when you create your project with the toolkit.</span></span> <span data-ttu-id="63ab8-128">Sehen wir uns die Hauptkomponenten zum Erstellen einer Kanalregisterkarte an.</span><span class="sxs-lookup"><span data-stu-id="63ab8-128">Let's look at the main components for building a channel tab.</span></span>

* <span data-ttu-id="63ab8-129">**App-Konfigurationen**: Öffnen Sie **App Studio** im Toolkit, um Ihre App-Konfigurationen anzuzeigen und zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="63ab8-129">**App configurations**: Open **App Studio** in the toolkit to view and update your app configurations.</span></span>
* <span data-ttu-id="63ab8-130">**App-Gerüst:** Das App-Gerüst stellt die Komponenten bereit, die zum Rendern der Kanalregisterkarte in Teams erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="63ab8-130">**App scaffolding**: The app scaffolding provides the components needed for rendering your channel tab in Teams.</span></span> <span data-ttu-id="63ab8-131">Es gibt eine Menge, mit dem Sie arbeiten können, aber jetzt konzentrieren wir uns auf Folgendes:</span><span class="sxs-lookup"><span data-stu-id="63ab8-131">There's a lot you can work with, however, for now let's focus on the following:</span></span>
  * <span data-ttu-id="63ab8-132">Die Dateien im `src/components` Verzeichnis Ihres Projekts:</span><span class="sxs-lookup"><span data-stu-id="63ab8-132">The files located in the `src/components` directory of your project:</span></span>
    * <span data-ttu-id="63ab8-133">`Tab.js` zum Rendern der Inhaltsseite Ihrer Registerkarte.</span><span class="sxs-lookup"><span data-stu-id="63ab8-133">`Tab.js` for rendering your tab's content page.</span></span>
    * <span data-ttu-id="63ab8-134">`TabConfig.js` zum Rendern der Konfigurationsseite Ihrer Registerkarte.</span><span class="sxs-lookup"><span data-stu-id="63ab8-134">`TabConfig.js` for rendering your tab's configuration page.</span></span>
  * <span data-ttu-id="63ab8-135">Microsoft Teams JavaScript Client SDK, das in den Front-End-Komponenten Ihres Projekts vorinstalliert ist.</span><span class="sxs-lookup"><span data-stu-id="63ab8-135">Microsoft Teams JavaScript client SDK, which comes pre-loaded in your project's front-end components.</span></span>

## <a name="3-customize-your-tab-content-page"></a><span data-ttu-id="63ab8-136">3. Passen Sie Ihre Registerkarte Inhalt Seite</span><span class="sxs-lookup"><span data-stu-id="63ab8-136">3. Customize your tab content page</span></span>

1. <span data-ttu-id="63ab8-137">Kopieren und ändern Sie das folgende Codebeispiel mit Informationen, die für Ihre Organisation relevant sind.</span><span class="sxs-lookup"><span data-stu-id="63ab8-137">Copy and modify the following code sample with information that's relevant to your organization.</span></span> <span data-ttu-id="63ab8-138">Sie können den Ausschnitt auch so verwenden, wie er ist:</span><span class="sxs-lookup"><span data-stu-id="63ab8-138">You can also use the snippet as it is:</span></span>
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
    
1. <span data-ttu-id="63ab8-139">Wechseln Sie zum `src/components` Verzeichnis, und öffnen Sie die `Tab.js` Datei.</span><span class="sxs-lookup"><span data-stu-id="63ab8-139">Go to the `src/components` directory and open the `Tab.js` file.</span></span> <span data-ttu-id="63ab8-140">Suchen Sie die `render()` Funktion, und fügen Sie den Code ein, `return()` wie im folgenden Beispiel gezeigt:</span><span class="sxs-lookup"><span data-stu-id="63ab8-140">Locate the `render()` function and paste your code inside `return()` as shown in the following example:</span></span>
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
    
1. <span data-ttu-id="63ab8-141">Wechseln Sie zum `src/components` Verzeichnis und aktualisieren Sie die Datei mit dem folgenden `App.css` Code, um die E-Mail-Links in jedem verwendeten Design leichter lesbar zu machen:</span><span class="sxs-lookup"><span data-stu-id="63ab8-141">Go to the `src/components` directory and update the `App.css` file with the following code to make the email links easier to read in any theme that is used:</span></span>
    ```CSS
    a {
      color: inherit;
    }
    ```

## <a name="4-customize-your-tab-configuration-page"></a><span data-ttu-id="63ab8-142">4. Passen Sie Ihre Registerkarte Konfigurationsseite an</span><span class="sxs-lookup"><span data-stu-id="63ab8-142">4. Customize your tab configuration page</span></span>

<span data-ttu-id="63ab8-143">Jede Registerkarte in einem Kanal oder Chat verfügt über eine Konfigurationsseite, ein Modal mit mindestens einer Setupoption, die angezeigt wird, wenn Benutzer Ihre App hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="63ab8-143">Every tab in a channel or chat has a configuration page, a modal with at least one setup option that displays when users add your app.</span></span> <span data-ttu-id="63ab8-144">Die Konfigurationsseite fragt Benutzer standardmäßig, ob sie den Kanal oder Chat benachrichtigen möchten, wenn die Registerkarte installiert ist.</span><span class="sxs-lookup"><span data-stu-id="63ab8-144">The configuration page by default asks users if they want to notify the channel or chat when the tab is installed.</span></span> <span data-ttu-id="63ab8-145">Sie können die Konfigurationsseite anpassen, indem Sie benutzerdefinierte Inhalte hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="63ab8-145">You can customize the configuration page by adding custom content.</span></span>

<span data-ttu-id="63ab8-146">Um benutzerdefinierte Inhalte hinzuzufügen, öffnen Sie `TabConfig.js` die Datei aus dem `src/components` Verzeichnis, und aktualisieren Sie den Platzhalterinhalt innerhalb, `return()` wie im folgenden Beispiel gezeigt:</span><span class="sxs-lookup"><span data-stu-id="63ab8-146">To add custom content, open `TabConfig.js` file from the `src/components` directory and update the placeholder content inside `return()` as shown in the following example:</span></span>

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
> <span data-ttu-id="63ab8-147">Geben Sie auf dieser Seite einen kurzen Überblick über Ihre App, da dies das erste Mal wäre, dass Benutzer darüber lesen.</span><span class="sxs-lookup"><span data-stu-id="63ab8-147">Give a brief information about your app on this page since this would be the first time users are reading about it.</span></span> <span data-ttu-id="63ab8-148">Sie können auch benutzerdefinierte Konfigurationsoptionen oder einen [Authentifizierungsworkflow](../tabs/how-to/authentication/auth-aad-sso.md)einschließen, der auf Registerkarten mit der Konfiguration der Registerkarten üblich ist.</span><span class="sxs-lookup"><span data-stu-id="63ab8-148">You can also include custom configuration options or an [authentication workflow](../tabs/how-to/authentication/auth-aad-sso.md), which is common on tab configuration pages.</span></span>

## <a name="5-customize-your-tab-name"></a><span data-ttu-id="63ab8-149">5. Passen Sie Ihren Tab-Namen an</span><span class="sxs-lookup"><span data-stu-id="63ab8-149">5. Customize your tab name</span></span>

<span data-ttu-id="63ab8-150">Wenn Sie eine Kanalregisterkarte hinzufügen, wird der App-Name standardmäßig angezeigt, z. **B. First-App**.</span><span class="sxs-lookup"><span data-stu-id="63ab8-150">When you add a channel tab, the app name displays by default, for example, **first-app**.</span></span> <span data-ttu-id="63ab8-151">Sie können auch einen Namen angeben, der im Kontext der Gruppenzusammenarbeit sinnvoller ist, z. B. **Teamkontakte:**</span><span class="sxs-lookup"><span data-stu-id="63ab8-151">You can also provide a name that makes more sense in the context of group collaboration, for example, **Team Contacts**:</span></span>

1. <span data-ttu-id="63ab8-152">Wechseln Sie zum `src/components` Verzeichnis, und öffnen Sie die `TabConfig.js` Datei.</span><span class="sxs-lookup"><span data-stu-id="63ab8-152">Go to the `src/components` directory and open the `TabConfig.js` file.</span></span>
1. <span data-ttu-id="63ab8-153">Fügen Sie die `suggestedDisplayName` Eigenschaft mit dem Tabnamen hinzu, den Sie standardmäßig unter anzeigen möchten, `microsoftTeams.settings.setSettings` wie im folgenden Beispiel gezeigt:</span><span class="sxs-lookup"><span data-stu-id="63ab8-153">Add the `suggestedDisplayName` property with the tab name you want to display by default under `microsoftTeams.settings.setSettings` as shown in the following example:</span></span>

    ```JavaScript
        microsoftTeams.settings.setSettings({
        "contentUrl": "https://localhost:3000/tab",
        "suggestedDisplayName": "Team Contacts"
      });
      ```

## <a name="6-build-and-run-your-app"></a><span data-ttu-id="63ab8-154">6. Erstellen und Ausführen Ihrer App</span><span class="sxs-lookup"><span data-stu-id="63ab8-154">6. Build and run your app</span></span>

<span data-ttu-id="63ab8-155">In diesem Tutorial lernen Sie, Ihre App lokal zu erstellen und auszuführen.</span><span class="sxs-lookup"><span data-stu-id="63ab8-155">This tutorial teaches you to build and run your app locally.</span></span> 

1. <span data-ttu-id="63ab8-156">Wechseln Sie zum Stammverzeichnis Ihres App-Projekts in Terminal.</span><span class="sxs-lookup"><span data-stu-id="63ab8-156">Go to the root directory of your app project in Terminal.</span></span>
1. <span data-ttu-id="63ab8-157">Führen Sie `npm install` aus.</span><span class="sxs-lookup"><span data-stu-id="63ab8-157">Run `npm install`.</span></span>
1. <span data-ttu-id="63ab8-158">Führen Sie `npm start` aus.</span><span class="sxs-lookup"><span data-stu-id="63ab8-158">Run `npm start`.</span></span>

<span data-ttu-id="63ab8-159">Diese Informationen finden Sie auch im `README` Abschnitt des Toolkits.</span><span class="sxs-lookup"><span data-stu-id="63ab8-159">This information is also present in the `README` section of the toolkit.</span></span>
<span data-ttu-id="63ab8-160">Ihre App wird `https://localhost:3000` nach dem **Kompilierten erfolgreich ausgeführt!**</span><span class="sxs-lookup"><span data-stu-id="63ab8-160">Your app is running on `https://localhost:3000` after the **Compiled successfully!**</span></span> <span data-ttu-id="63ab8-161">Meldung wird im Terminal angezeigt.</span><span class="sxs-lookup"><span data-stu-id="63ab8-161">message appears in the terminal.</span></span> 

## <a name="7-sideload-your-app-in-teams"></a><span data-ttu-id="63ab8-162">7. Sideload Ihre App in Teams</span><span class="sxs-lookup"><span data-stu-id="63ab8-162">7. Sideload your app in Teams</span></span>

<span data-ttu-id="63ab8-163">Ihre App kann in Teams getestet werden.</span><span class="sxs-lookup"><span data-stu-id="63ab8-163">Your app is ready to test in Teams.</span></span> <span data-ttu-id="63ab8-164">Dazu benötigen Sie ein Konto, das das Sideloading von Apps ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="63ab8-164">To do this, you must have an account that allows app sideloading.</span></span> 

1. <span data-ttu-id="63ab8-165">Öffnen Sie einen Teams Webclient in Visual Studio Code mit der **Taste F5.**</span><span class="sxs-lookup"><span data-stu-id="63ab8-165">Open a Teams web client in Visual Studio Code with the **F5** key.</span></span>
1. <span data-ttu-id="63ab8-166">Fügen Sie ( ) als vertrauenswürdig hinzu, indem Sie `localhost` die folgenden Schritte ausführen, damit Ihre App-Inhalte in Teams angezeigt werden können:</span><span class="sxs-lookup"><span data-stu-id="63ab8-166">Add (`localhost`) as trustworthy by following these steps to enable your app content to display in Teams:</span></span>

   1. <span data-ttu-id="63ab8-167">Öffnen Sie eine neue Registerkarte im gleichen Browserfenster (standardmäßig Google Chrome), die mit der **Taste F5** geöffnet wurde.</span><span class="sxs-lookup"><span data-stu-id="63ab8-167">Open a new tab in the same browser window (Google Chrome by default) which opened with the **F5** key.</span></span>
   1. <span data-ttu-id="63ab8-168">Öffnen `https://localhost:3000/tab` Sie die Seite, und fahren Sie mit der Seite fort.</span><span class="sxs-lookup"><span data-stu-id="63ab8-168">Open `https://localhost:3000/tab` and proceed to the page.</span></span>

1. <span data-ttu-id="63ab8-169">Wählen Sie **Hinzufügen zu einem Team** oder Hinzufügen zu einem **Chat** und Suchen eines Kanals oder Chats, den Sie zum Testen vom Modal in Teams verwenden können.</span><span class="sxs-lookup"><span data-stu-id="63ab8-169">Select **Add to a team** or **Add to a chat** and locate a channel or chat you can use for testing from the modal in Teams.</span></span>
1. <span data-ttu-id="63ab8-170">Wählen **Sie Registerkarte einrichten** aus. Die Konfigurationsseite wird in einem Modal angezeigt.</span><span class="sxs-lookup"><span data-stu-id="63ab8-170">Select **Set up a tab**. The configuration page displays in a modal.</span></span>

   :::image type="content" source="../assets/images/tabs/channel-tab-tutorial-content.png" alt-text="Screenshot einer Kanalregisterkartenkonfigurationsseite.":::

1. <span data-ttu-id="63ab8-172">Wählen Sie **Speichern** aus, um die Registerkarte zu konfigurieren. Die folgende Inhaltsseite wird angezeigt:</span><span class="sxs-lookup"><span data-stu-id="63ab8-172">Select **Save** to configure the tab. The following content page appears:</span></span>

   :::image type="content" source="../assets/images/tabs/channel-tab-tutorial-content-installed.png" alt-text="Screenshot einer Kanalregisterkarte mit statischer Inhaltsansicht.":::

## <a name="see-also"></a><span data-ttu-id="63ab8-174">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="63ab8-174">See also</span></span>

* [<span data-ttu-id="63ab8-175">Erstellen und Ausführen Ihrer ersten Microsoft Teams-App</span><span class="sxs-lookup"><span data-stu-id="63ab8-175">Build and run your first Microsoft Teams app</span></span>](../build-your-first-app/build-and-run.md) 
* [<span data-ttu-id="63ab8-176">Microsoft Teams JavaScript-Client-SDK</span><span class="sxs-lookup"><span data-stu-id="63ab8-176">Teams JavaScript client SDK</span></span>](/javascript/api/@microsoft/teams-js/?view=msteams-client-js-latest&preserve-view=true)
* [<span data-ttu-id="63ab8-177">Entwerfen der Registerkarte für Microsoft Teams Desktop und Web</span><span class="sxs-lookup"><span data-stu-id="63ab8-177">Designing your tab for Microsoft Teams desktop and web</span></span>](../tabs/design/tabs.md) 
* [<span data-ttu-id="63ab8-178">Entwerfen Ihrer Microsoft Teams-App mit UI-Vorlagen</span><span class="sxs-lookup"><span data-stu-id="63ab8-178">Designing your Microsoft Teams app with UI templates</span></span>](../concepts/design/design-teams-app-ui-templates.md) 
* [<span data-ttu-id="63ab8-179">Registerkarten auf mobilen Geräten</span><span class="sxs-lookup"><span data-stu-id="63ab8-179">Tabs on mobile</span></span>](../tabs/design/tabs-mobile.md)
* [<span data-ttu-id="63ab8-180">SSO-Unterstützung (Single Sign-On) für Registerkarten</span><span class="sxs-lookup"><span data-stu-id="63ab8-180">Single sign-on (SSO) support for tabs</span></span>](../tabs/how-to/authentication/auth-aad-sso.md)
* [<span data-ttu-id="63ab8-181">Übersicht über Microsoft Teams-APIs</span><span class="sxs-lookup"><span data-stu-id="63ab8-181">Microsoft Teams API overview</span></span>](/graph/teams-concept-overview)
* [<span data-ttu-id="63ab8-182">Erstellen Sie eine benutzerdefinierte persönliche Registerkarte mit Node.js und dem Yeoman Generator für Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="63ab8-182">Create a custom personal tab with Node.js and the Yeoman Generator for Microsoft Teams</span></span>](../tabs/quickstarts/create-personal-tab-node-yeoman.md)

## <a name="next-step"></a><span data-ttu-id="63ab8-183">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="63ab8-183">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="63ab8-184">Erstellen eines Bots</span><span class="sxs-lookup"><span data-stu-id="63ab8-184">Build a bot</span></span>](../build-your-first-app/build-bot.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="63ab8-185">Erstellen einer Messaging-Erweiterung</span><span class="sxs-lookup"><span data-stu-id="63ab8-185">Build a messaging extension</span></span>](../build-your-first-app/build-messaging-extension.md)
