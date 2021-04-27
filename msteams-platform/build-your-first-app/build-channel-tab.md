---
title: Erste Schritte – Erstellen einer Kanal- und Gruppenregisterkarte
author: heath-hamilton
description: Erstellen Sie mithilfe des Microsoft Teams Toolkits schnell einen Microsoft Teams-Kanal und eine Gruppenregisterkarte.
ms.author: lajanuar
localization_priority: Normal
ms.date: 10/09/2020
ms.topic: tutorial
ms.openlocfilehash: aadab4b6826b026eadd5ed564b6e5de5c29b4b1d
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020877"
---
# <a name="build-a-channel-and-group-tab-for-microsoft-teams"></a><span data-ttu-id="32dc8-103">Erstellen einer Kanal- und Gruppenregisterkarte für Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="32dc8-103">Build a channel and group tab for Microsoft Teams</span></span>

<span data-ttu-id="32dc8-104">In diesem Lernprogramm erstellen Sie eine einfache Kanalregisterkarte *(auch* als Gruppenregisterkarte *bezeichnet),* die eine Vollbildseite für einen Teamkanal oder Chat ist.</span><span class="sxs-lookup"><span data-stu-id="32dc8-104">In this tutorial, you'll build a basic *channel tab* (also known as a *group tab*), which is a full-screen page for a team channel or chat.</span></span> <span data-ttu-id="32dc8-105">Im Gegensatz zu einer persönlichen Registerkarte können Benutzer einige Aspekte dieser Art von Registerkarte konfigurieren (z. B. die Registerkarte umbenennen, sodass sie für ihren Kanal sinnvoll ist).</span><span class="sxs-lookup"><span data-stu-id="32dc8-105">Unlike a personal tab, users can configure some aspects of this kind of tab (for example, rename the tab so it's meaningful to their channel).</span></span>

## <a name="your-assignment"></a><span data-ttu-id="32dc8-106">Ihre Zuordnung</span><span class="sxs-lookup"><span data-stu-id="32dc8-106">Your assignment</span></span>

<span data-ttu-id="32dc8-107">Vor nicht langer Zeit hat Ihre Organisation eine Teams-App erstellt, die eine Registerkarte zum Anzeigen wichtiger Kontaktinformationen (Helpdesk, Personalwesen usw.) verwendet.</span><span class="sxs-lookup"><span data-stu-id="32dc8-107">Not long ago, your organization created a Teams app that uses a tab to display important contact information (help desk, HR, etc.).</span></span> <span data-ttu-id="32dc8-108">Da es sich jedoch um eine persönliche Registerkarte handelt, muss jeder Benutzer die Registerkarte installieren, um sie zu sehen, und die Akzeptanz ist niedriger als erwartet.</span><span class="sxs-lookup"><span data-stu-id="32dc8-108">However, since it's a personal tab, each user must install the tab to see it and adoption is lower than expected.</span></span> <span data-ttu-id="32dc8-109">Anders ausgedrückt: Zu viele Mitarbeiter wissen noch nicht, wie sie den Helpdesk erreichen.</span><span class="sxs-lookup"><span data-stu-id="32dc8-109">In other words, too many workers still don't know how to reach the help desk.</span></span>

<span data-ttu-id="32dc8-110">Sie können diese Informationen leichter finden, indem Sie eine Kanalregisterkarte erstellen. Dadurch wird der Aufwand für die Installation einer App durch alle Benutzer beseitigt.</span><span class="sxs-lookup"><span data-stu-id="32dc8-110">You can make this information easier to find by building a channel tab, which will remove the burden of requiring everyone to install an app.</span></span> <span data-ttu-id="32dc8-111">Stattdessen kann ein Benutzer die Registerkarte in einem Kanal oder Chat zum Vorteil einer gesamten Gruppe hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="32dc8-111">Instead, one user can add the tab in a channel or chat for the benefit of an entire group.</span></span>

## <a name="what-youll-learn"></a><span data-ttu-id="32dc8-112">Was Sie lernen werden</span><span class="sxs-lookup"><span data-stu-id="32dc8-112">What you'll learn</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="32dc8-113">Erstellen eines App-Projekts mithilfe des Microsoft Teams Toolkits für Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="32dc8-113">Create an app project using the Microsoft Teams Toolkit for Visual Studio Code</span></span>
> * <span data-ttu-id="32dc8-114">Identifizieren einiger der für Kanalregisterkarten relevanten App-Konfigurationen und Gerüste</span><span class="sxs-lookup"><span data-stu-id="32dc8-114">Identify some of the app configurations and scaffolding relevant to channel tabs</span></span>
> * <span data-ttu-id="32dc8-115">Erstellen von Registerkarteninhalten</span><span class="sxs-lookup"><span data-stu-id="32dc8-115">Create tab content</span></span>
> * <span data-ttu-id="32dc8-116">Erstellen von Inhalten für die Konfigurationsseite einer Registerkarte</span><span class="sxs-lookup"><span data-stu-id="32dc8-116">Create content for a tab's configuration page</span></span>
> * <span data-ttu-id="32dc8-117">Bereitstellen eines vorgeschlagenen Registerkartennamens</span><span class="sxs-lookup"><span data-stu-id="32dc8-117">Provide a suggested tab name</span></span>
> * <span data-ttu-id="32dc8-118">Erstellen und Ausführen Ihrer App lokal</span><span class="sxs-lookup"><span data-stu-id="32dc8-118">Build and run your app locally</span></span>
> * <span data-ttu-id="32dc8-119">Querladen Ihrer App in Teams zu Testzwecken</span><span class="sxs-lookup"><span data-stu-id="32dc8-119">Sideload your app in Teams for testing</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="32dc8-120">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="32dc8-120">Before you begin</span></span>

<span data-ttu-id="32dc8-121">Falls noch nicht, stellen Sie sicher, dass Sie die Voraussetzungen für die [Teams-Entwicklung verstehen und installieren.](build-first-app-overview.md#get-prerequisites)</span><span class="sxs-lookup"><span data-stu-id="32dc8-121">If you haven't yet, make sure you [understand and install the Teams development prerequisites](build-first-app-overview.md#get-prerequisites).</span></span>

## <a name="1-create-your-app-project"></a><span data-ttu-id="32dc8-122">1. Erstellen Ihres App-Projekts</span><span class="sxs-lookup"><span data-stu-id="32dc8-122">1. Create your app project</span></span>

<span data-ttu-id="32dc8-123">Mit dem Microsoft Teams Toolkit können Sie Ihre App konfigurieren und ein Gerüst einrichten, das für Kanal- und Gruppenregisterkarten relevant ist, einschließlich einer grundlegenden Konfigurationsseite und einer Inhaltsseite, auf der "Hello, World!" angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="32dc8-123">The Microsoft Teams Toolkit helps configure your app and set up scaffolding relevant to channel and group tabs, including a basic configuration page and content page that displays a "Hello, World!"</span></span> <span data-ttu-id="32dc8-124">Nachricht.</span><span class="sxs-lookup"><span data-stu-id="32dc8-124">message.</span></span>

> [!TIP]
> <span data-ttu-id="32dc8-125">Wenn Sie noch kein Teams-App-Projekt erstellt haben, ist [](../build-your-first-app/build-and-run.md) es möglicherweise hilfreich, diese Anweisungen zu befolgen, die Projekte ausführlicher erläutern.</span><span class="sxs-lookup"><span data-stu-id="32dc8-125">If you haven't created a Teams app project before, you might find it helpful to follow [these instructions](../build-your-first-app/build-and-run.md) that explain projects in more detail.</span></span>

1. Wählen Visual Studio Code auf der linken Aktivitätsleiste **Microsoft Teams** :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: aus, und wählen Sie Erstellen einer neuen **Teams-App aus.**
1. <span data-ttu-id="32dc8-127">Melden Sie sich bei Aufforderung mit Ihrem Microsoft 365-Entwicklungskonto an.</span><span class="sxs-lookup"><span data-stu-id="32dc8-127">When prompted, sign in with your Microsoft 365 development account.</span></span>
1. <span data-ttu-id="32dc8-128">Wählen Sie **auf dem** Bildschirm Funktionen hinzufügen die Option **Tab** und dann **Weiter aus.**</span><span class="sxs-lookup"><span data-stu-id="32dc8-128">On the **Add capabilities** screen, select **Tab** then **Next**.</span></span>
1. <span data-ttu-id="32dc8-129">Geben Sie einen Namen für Ihre Teams-App ein.</span><span class="sxs-lookup"><span data-stu-id="32dc8-129">Enter a name for your Teams app.</span></span> <span data-ttu-id="32dc8-130">(Dies ist der Standardname für Ihre App und auch der Name des App-Projektverzeichnisses auf Ihrem lokalen Computer.) Wählen **Sie Die Registerkarte Gruppen- oder Teams-Kanal aus.**</span><span class="sxs-lookup"><span data-stu-id="32dc8-130">(This is the default name for your app and also the name of the app project directory on your local machine.) Select **Group or Teams channel tab**.</span></span>
1. <span data-ttu-id="32dc8-131">Wählen **Sie unten** auf dem Bildschirm Fertig stellen aus, um Ihr Projekt zu konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="32dc8-131">Select **Finish** at the bottom of the screen to configure your project.</span></span>  

## <a name="2-identify-relevant-app-project-components"></a><span data-ttu-id="32dc8-132">2. Identifizieren relevanter App-Projektkomponenten</span><span class="sxs-lookup"><span data-stu-id="32dc8-132">2. Identify relevant app project components</span></span>

<span data-ttu-id="32dc8-133">Viele der App-Konfigurationen und Gerüste werden automatisch eingerichtet, wenn Sie Ihr Projekt mit dem Toolkit erstellen.</span><span class="sxs-lookup"><span data-stu-id="32dc8-133">Much of the app configurations and scaffolding are set up automatically when you create your project with the toolkit.</span></span> <span data-ttu-id="32dc8-134">Sehen wir uns die Hauptkomponenten zum Erstellen einer Kanalregisterkarte an.</span><span class="sxs-lookup"><span data-stu-id="32dc8-134">Let's look at the main components for building a channel tab.</span></span>

### <a name="app-configurations"></a><span data-ttu-id="32dc8-135">App-Konfigurationen</span><span class="sxs-lookup"><span data-stu-id="32dc8-135">App configurations</span></span>

<span data-ttu-id="32dc8-136">Wechseln Sie im Toolkit zu **App Studio,** um Ihre App-Konfigurationen zu sehen und zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="32dc8-136">In the toolkit, go to **App Studio** to view and update your app configurations.</span></span>

### <a name="app-scaffolding"></a><span data-ttu-id="32dc8-137">App-Gerüst</span><span class="sxs-lookup"><span data-stu-id="32dc8-137">App scaffolding</span></span>

<span data-ttu-id="32dc8-138">Das App-Gerüst stellt die Komponenten zum Rendern Ihrer Kanalregisterkarte in Teams zur Seite.</span><span class="sxs-lookup"><span data-stu-id="32dc8-138">The app scaffolding provides the components for rendering your channel tab in Teams.</span></span> <span data-ttu-id="32dc8-139">Es gibt eine Menge, mit der Sie arbeiten können, aber derzeit müssen Sie sich nur auf Folgendes konzentrieren:</span><span class="sxs-lookup"><span data-stu-id="32dc8-139">There's a lot you can work with, but for now you only need to focus on the following:</span></span>

* <span data-ttu-id="32dc8-140">Zwei Dateien im `src/components` Verzeichnis Ihres Projekts:</span><span class="sxs-lookup"><span data-stu-id="32dc8-140">Two files located in the `src/components` directory of your project:</span></span>
  * <span data-ttu-id="32dc8-141">`Tab.js` zum Rendern der Inhaltsseite Ihrer Registerkarte.</span><span class="sxs-lookup"><span data-stu-id="32dc8-141">`Tab.js` for rendering your tab's content page.</span></span>
  * <span data-ttu-id="32dc8-142">`TabConfig.js` zum Rendern der Konfigurationsseite Ihrer Registerkarte.</span><span class="sxs-lookup"><span data-stu-id="32dc8-142">`TabConfig.js` for rendering your tab's configuration page.</span></span>
* <span data-ttu-id="32dc8-143">Microsoft Teams JavaScript-Client-SDK, das in den Front-End-Komponenten Ihres Projekts vorinstalliert ist.</span><span class="sxs-lookup"><span data-stu-id="32dc8-143">Microsoft Teams JavaScript client SDK, which comes pre-loaded in your project's front-end components.</span></span>

## <a name="3-customize-your-tab-content-page"></a><span data-ttu-id="32dc8-144">3. Anpassen der Registerkarteninhaltsseite</span><span class="sxs-lookup"><span data-stu-id="32dc8-144">3. Customize your tab content page</span></span>

<span data-ttu-id="32dc8-145">Kopieren und aktualisieren Sie den folgenden Codeausschnitt mit Informationen, die für Ihre Organisation relevant sind, oder verwenden Sie den Code aus Zeitgründen wie folgt.</span><span class="sxs-lookup"><span data-stu-id="32dc8-145">Copy and update the following snippet with information that's relevant to your organization or, for the sake of time, use the code as is.</span></span>

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

<span data-ttu-id="32dc8-146">Wechseln Sie zum `src/components` Verzeichnis, und öffnen Sie `Tab.js` .</span><span class="sxs-lookup"><span data-stu-id="32dc8-146">Go to the `src/components` directory and open `Tab.js`.</span></span> <span data-ttu-id="32dc8-147">Suchen Sie die `render()` Funktion, und fügen Sie Den Inhalt ein `return()` (wie dargestellt).</span><span class="sxs-lookup"><span data-stu-id="32dc8-147">Locate the `render()` function and paste your content inside `return()` (as shown).</span></span>

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

<span data-ttu-id="32dc8-148">Fügen Sie die folgende Regel zu hinzu (ebenfalls in ), damit die E-Mail-Links unabhängig vom verwendeten `App.css` Design leichter zu lesen `src/components` sind.</span><span class="sxs-lookup"><span data-stu-id="32dc8-148">Add the following rule to `App.css` (also located in `src/components`) so the email links are easier to read no matter which theme is used.</span></span>

```CSS
a {
  color: inherit;
}
```

## <a name="4-customize-your-tab-configuration-page"></a><span data-ttu-id="32dc8-149">4. Anpassen der Registerkartenkonfigurationsseite</span><span class="sxs-lookup"><span data-stu-id="32dc8-149">4. Customize your tab configuration page</span></span>

<span data-ttu-id="32dc8-150">Jede Registerkarte in einem Kanal oder Chat verfügt über eine Konfigurationsseite, eine modale Mit mindestens einer Setupoption, die angezeigt wird, wenn Benutzer Ihre App hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="32dc8-150">Every tab in a channel or chat has a configuration page, a modal with at least one setup option that displays when users add your app.</span></span> <span data-ttu-id="32dc8-151">Auf der Konfigurationsseite werden Benutzer standardmäßig gefragt, ob sie den Kanal oder Chat benachrichtigen möchten, wenn die Registerkarte installiert ist.</span><span class="sxs-lookup"><span data-stu-id="32dc8-151">The configuration page by default asks users if they want to notify the channel or chat when the tab is installed.</span></span>

<span data-ttu-id="32dc8-152">Fügen Sie ihrer Konfigurationsseite benutzerdefinierte Inhalte hinzu.</span><span class="sxs-lookup"><span data-stu-id="32dc8-152">Add some custom content to your configuration page.</span></span> <span data-ttu-id="32dc8-153">Wechseln Sie zum Verzeichnis Ihres Projekts, öffnen Sie , und aktualisieren Sie den Platzhalterinhalt `src/components` `TabConfig.js` darin `return()` (wie im folgenden Beispiel gezeigt).</span><span class="sxs-lookup"><span data-stu-id="32dc8-153">Go to your project's `src/components` directory, open `TabConfig.js`, and update the placeholder content inside `return()` (as shown in the following example).</span></span>

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
> <span data-ttu-id="32dc8-154">Geben Sie zumindest einige kurze Informationen zu Ihrer App auf dieser Seite an, da dies das erste Mal sein kann, dass Benutzer davon lernen.</span><span class="sxs-lookup"><span data-stu-id="32dc8-154">At minimum, provide some brief information about your app on this page since this may be the first time users are learning about it.</span></span> <span data-ttu-id="32dc8-155">Sie können auch benutzerdefinierte Konfigurationsoptionen oder einen [Authentifizierungsworkflow](../tabs/how-to/authentication/auth-aad-sso.md)hinzufügen, der auf Registerkartenkonfigurationsseiten üblich ist.</span><span class="sxs-lookup"><span data-stu-id="32dc8-155">You also could include custom configuration options or an [authentication workflow](../tabs/how-to/authentication/auth-aad-sso.md), which is common on tab configuration pages.</span></span>

## <a name="5-provide-a-suggested-tab-name"></a><span data-ttu-id="32dc8-156">5. Geben Sie einen vorgeschlagenen Registerkartennamen an.</span><span class="sxs-lookup"><span data-stu-id="32dc8-156">5. Provide a suggested tab name</span></span>

<span data-ttu-id="32dc8-157">Wenn Sie eine Kanalregisterkarte hinzufügen, wird standardmäßig der App-Name angezeigt (z. B. **First-App**).</span><span class="sxs-lookup"><span data-stu-id="32dc8-157">When you add a channel tab, by default the app name displays (for example, **first-app**).</span></span>

<span data-ttu-id="32dc8-158">Dies kann in Abhängigkeit von dem, was Sie Ihre App aufrufen, in Ordnung sein, aber Sie möchten möglicherweise einen Namen bereitstellen, der im Kontext der Gruppenzusammenarbeit sinnvoller ist (z. B. **Teamkontakte**).</span><span class="sxs-lookup"><span data-stu-id="32dc8-158">This may be fine depending on what you call your app, but you may want to provide a name that makes more sense in the context of group collaboration (for example, **Team Contacts**).</span></span>

1. <span data-ttu-id="32dc8-159">Wechseln `TabConfig.js` Sie in zu `microsoftTeams.settings.setSettings` .</span><span class="sxs-lookup"><span data-stu-id="32dc8-159">In `TabConfig.js`, go to `microsoftTeams.settings.setSettings`.</span></span>
2. <span data-ttu-id="32dc8-160">Fügen Sie `suggestedDisplayName` die Eigenschaft mit dem Registerkartennamen hinzu, den Sie standardmäßig anzeigen möchten.</span><span class="sxs-lookup"><span data-stu-id="32dc8-160">Add the `suggestedDisplayName` property with the tab name you want to display by default.</span></span> 
3. <span data-ttu-id="32dc8-161">Verwenden Sie den im folgenden Beispiel angegebenen Namen, oder geben Sie Ihren Namen ein.</span><span class="sxs-lookup"><span data-stu-id="32dc8-161">Use the name provided in the following example or type your name.</span></span> <span data-ttu-id="32dc8-162">(Standardmäßig können Benutzer den Namen ändern.)</span><span class="sxs-lookup"><span data-stu-id="32dc8-162">(By default, users can change the name.)</span></span>

```JavaScript
microsoftTeams.settings.setSettings({
  "contentUrl": "https://localhost:3000/tab",
  "suggestedDisplayName": "Team Contacts"
});
```

## <a name="6-build-and-run-your-app"></a><span data-ttu-id="32dc8-163">6. Erstellen und Ausführen Ihrer App</span><span class="sxs-lookup"><span data-stu-id="32dc8-163">6. Build and run your app</span></span>

<span data-ttu-id="32dc8-164">Im Interesse der Zeit erstellen und führen Sie Ihre App lokal aus.</span><span class="sxs-lookup"><span data-stu-id="32dc8-164">In the interest of time, you'll build and run your app locally.</span></span>

<span data-ttu-id="32dc8-165">(Diese Informationen sind auch im Toolkit `README` verfügbar.)</span><span class="sxs-lookup"><span data-stu-id="32dc8-165">(This information is also available in the toolkit `README`.)</span></span>

1. <span data-ttu-id="32dc8-166">Wechseln Sie in einem Terminal zum Stammverzeichnis Ihres App-Projekts, und führen Sie `npm install` aus.</span><span class="sxs-lookup"><span data-stu-id="32dc8-166">In a terminal, go to the root directory of your app project and run `npm install`.</span></span>
1. <span data-ttu-id="32dc8-167">Führen Sie `npm start` aus.</span><span class="sxs-lookup"><span data-stu-id="32dc8-167">Run `npm start`.</span></span>

<span data-ttu-id="32dc8-168">Sobald sie abgeschlossen sind, wird ein **Kompiliert erfolgreich erstellt!**</span><span class="sxs-lookup"><span data-stu-id="32dc8-168">Once complete, there's a **Compiled successfully!**</span></span> <span data-ttu-id="32dc8-169">-Nachricht im Terminal.</span><span class="sxs-lookup"><span data-stu-id="32dc8-169">message in the terminal.</span></span> <span data-ttu-id="32dc8-170">Ihre App wird auf `https://localhost:3000` ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="32dc8-170">Your app is running on `https://localhost:3000`.</span></span>

## <a name="7-sideload-your-app-in-teams"></a><span data-ttu-id="32dc8-171">7. Querladen Ihrer App in Teams</span><span class="sxs-lookup"><span data-stu-id="32dc8-171">7. Sideload your app in Teams</span></span>

<span data-ttu-id="32dc8-172">Ihre App kann in Teams testen.</span><span class="sxs-lookup"><span data-stu-id="32dc8-172">Your app is ready to test in Teams.</span></span> <span data-ttu-id="32dc8-173">Dazu müssen Sie über ein Konto verfügen, das das Querladen von Apps zulässt.</span><span class="sxs-lookup"><span data-stu-id="32dc8-173">To do this, you must have an account that allows app sideloading.</span></span> <span data-ttu-id="32dc8-174">(Wenn Sie nicht sicher sind, dass Sie dies haben, erfahren Sie mehr über das Abrufen eines [Teams-Entwicklungskontos.)](../build-your-first-app/build-first-app-overview.md#set-up-your-development-account)</span><span class="sxs-lookup"><span data-stu-id="32dc8-174">(If you aren't sure you have that, learn about getting a [Teams development account](../build-your-first-app/build-first-app-overview.md#set-up-your-development-account).)</span></span>

1. <span data-ttu-id="32dc8-175">Drücken Visual Studio Code die **F5-TASTE,** um einen Teams-Webclient zu starten.</span><span class="sxs-lookup"><span data-stu-id="32dc8-175">In Visual Studio Code, press the **F5** key to launch a Teams web client.</span></span>
1. <span data-ttu-id="32dc8-176">Um Ihre App-Inhalte in Teams anzuzeigen, geben Sie an, wo Ihre App ausgeführt wird ( `localhost` ) vertrauenswürdig ist:</span><span class="sxs-lookup"><span data-stu-id="32dc8-176">To display your app content in Teams, specify that where your app is running (`localhost`) is trustworthy:</span></span>
   1. <span data-ttu-id="32dc8-177">Öffnen Sie eine neue Registerkarte im gleichen Browserfenster (Standardmäßig Google Chrome), das nach dem Drücken von **F5 geöffnet wurde.**</span><span class="sxs-lookup"><span data-stu-id="32dc8-177">Open a new tab in the same browser window (Google Chrome by default) which opened after pressing **F5**.</span></span>
   1. <span data-ttu-id="32dc8-178">Wechseln Sie `https://localhost:3000/tab` zu und fahren Sie mit der Seite fort.</span><span class="sxs-lookup"><span data-stu-id="32dc8-178">Go to `https://localhost:3000/tab` and proceed to the page.</span></span>
1. <span data-ttu-id="32dc8-179">Wechseln Sie zurück zu Teams.</span><span class="sxs-lookup"><span data-stu-id="32dc8-179">Go back to Teams.</span></span> <span data-ttu-id="32dc8-180">Wählen Sie im modalen Modus **Hinzufügen zu einem** Team oder **Zu** einem Chat hinzufügen aus, und suchen Sie nach einem Kanal oder Chat, den Sie zum Testen verwenden können.</span><span class="sxs-lookup"><span data-stu-id="32dc8-180">In the modal, select **Add to a team** or **Add to a chat** and locate a channel or chat you can use for testing.</span></span>
1. <span data-ttu-id="32dc8-181">Wählen **Sie Tab einrichten aus.** Die Konfigurationsseite wird modal angezeigt.</span><span class="sxs-lookup"><span data-stu-id="32dc8-181">Select **Set up a tab**. The configuration page displays in a modal.</span></span><br/>
   :::image type="content" source="../assets/images/tabs/channel-tab-tutorial-content.png" alt-text="Screenshot einer Kanalregisterkartenkonfigurationsseite.":::
1. <span data-ttu-id="32dc8-183">Wählen **Sie Speichern** aus, um die Registerkarte zu konfigurieren. Die Inhaltsseite wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="32dc8-183">Select **Save** to configure the tab. The content page displays.</span></span><br/>
   :::image type="content" source="../assets/images/tabs/channel-tab-tutorial-content-installed.png" alt-text="Screenshot einer Kanalregisterkarte mit statischer Inhaltsansicht.":::

## <a name="well-done"></a><span data-ttu-id="32dc8-185">Gut gemacht</span><span class="sxs-lookup"><span data-stu-id="32dc8-185">Well done</span></span>

<span data-ttu-id="32dc8-186">Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="32dc8-186">Congratulations!</span></span> <span data-ttu-id="32dc8-187">Sie verfügen über eine Teams-App mit einer Registerkarte zum Anzeigen nützlicher Inhalte in Kanälen und Chats.</span><span class="sxs-lookup"><span data-stu-id="32dc8-187">You have a Teams app with a tab for displaying useful content in channels and chats.</span></span>

## <a name="learn-more"></a><span data-ttu-id="32dc8-188">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="32dc8-188">Learn more</span></span>

* <span data-ttu-id="32dc8-189">Befolgen Sie [unsere Entwurfsrichtlinien,](../tabs/design/tabs.md) und erstellen Sie mit [produktionsbereiten](../concepts/design/design-teams-app-ui-templates.md) Benutzeroberflächenvorlagen, um eine nahtlose Oberfläche zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="32dc8-189">Follow our [design guidelines](../tabs/design/tabs.md) and build with [production-ready UI templates](../concepts/design/design-teams-app-ui-templates.md) to create a seamless experience.</span></span>
* <span data-ttu-id="32dc8-190">Informationen [zu mobilen Überlegungen](../tabs/design/tabs-mobile.md) für Registerkarten.</span><span class="sxs-lookup"><span data-stu-id="32dc8-190">Understand [mobile considerations](../tabs/design/tabs-mobile.md) for tabs.</span></span>
* <span data-ttu-id="32dc8-191">[Fügen Sie ihrer Registerkarte die SSO-Authentifizierung hinzu.](../tabs/how-to/authentication/auth-aad-sso.md)</span><span class="sxs-lookup"><span data-stu-id="32dc8-191">[Add SSO authentication to your tab](../tabs/how-to/authentication/auth-aad-sso.md).</span></span>
* <span data-ttu-id="32dc8-192">Verwenden von Teams-Daten [mit Microsoft Graph](https://docs.microsoft.com/graph/teams-concept-overview).</span><span class="sxs-lookup"><span data-stu-id="32dc8-192">Utilize Teams data with [Microsoft Graph](https://docs.microsoft.com/graph/teams-concept-overview).</span></span>
* [<span data-ttu-id="32dc8-193">Erstellen einer Registerkarte ohne toolkit</span><span class="sxs-lookup"><span data-stu-id="32dc8-193">Create a tab without the toolkit</span></span>](../tabs/quickstarts/create-channel-group-tab-node-yeoman.md)

## <a name="next-lesson"></a><span data-ttu-id="32dc8-194">Nächste Lektion</span><span class="sxs-lookup"><span data-stu-id="32dc8-194">Next lesson</span></span>

<span data-ttu-id="32dc8-195">Sie wissen, wie Sie eine Registerkarte für die Zusammenarbeit erstellen.</span><span class="sxs-lookup"><span data-stu-id="32dc8-195">You know how to build a tab for collaboration.</span></span> <span data-ttu-id="32dc8-196">Möchten Sie versuchen, eine andere Art von Teams-App zu erstellen?</span><span class="sxs-lookup"><span data-stu-id="32dc8-196">Want to try building a different kind of Teams app?</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="32dc8-197">Erstellen eines Bots</span><span class="sxs-lookup"><span data-stu-id="32dc8-197">Build a bot</span></span>](../build-your-first-app/build-bot.md)
