---
title: Erste Schritte – Erstellen eines Kanals und einer Gruppenregisterkarte
author: heath-hamilton
description: Erstellen Sie mithilfe des Microsoft Teams Toolkits schnell einen Microsoft Teams-Kanal und eine Gruppenregisterkarte.
ms.author: lajanuar
ms.date: 10/09/2020
ms.topic: tutorial
ms.openlocfilehash: 0692d28653063c2f886db9a03e7136379edde9c3
ms.sourcegitcommit: 00c657e3bf57d3b92aca7da941cde47a2eeff4d0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/20/2021
ms.locfileid: "49911877"
---
# <a name="build-a-channel-and-group-tab-for-microsoft-teams"></a><span data-ttu-id="551bd-103">Erstellen eines Kanals und einer Gruppenregisterkarte für Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="551bd-103">Build a channel and group tab for Microsoft Teams</span></span>

<span data-ttu-id="551bd-104">In diesem Lernprogramm erstellen Sie eine einfache Kanalregisterkarte *(auch* als Gruppenregisterkarte *bezeichnet),* die eine Vollbildseite für einen Teamkanal oder Chat ist.</span><span class="sxs-lookup"><span data-stu-id="551bd-104">In this tutorial, you'll build a basic *channel tab* (also known as a *group tab*), which is a full-screen page for a team channel or chat.</span></span> <span data-ttu-id="551bd-105">Im Gegensatz zu einer persönlichen Registerkarte können Benutzer einige Aspekte dieser Art von Registerkarte konfigurieren (benennen Sie die Registerkarte beispielsweise so um, dass sie für ihren Kanal von Bedeutung ist).</span><span class="sxs-lookup"><span data-stu-id="551bd-105">Unlike a personal tab, users can configure some aspects of this kind of tab (for example, rename the tab so it's meaningful to their channel).</span></span>

## <a name="your-assignment"></a><span data-ttu-id="551bd-106">Ihre Zuordnung</span><span class="sxs-lookup"><span data-stu-id="551bd-106">Your assignment</span></span>

<span data-ttu-id="551bd-107">Vor nicht langer Zeit hat Ihre Organisation eine Teams-App erstellt, die eine Registerkarte zum Anzeigen wichtiger Kontaktinformationen (Helpdesk, Personalabteilung usw.) verwendet.</span><span class="sxs-lookup"><span data-stu-id="551bd-107">Not long ago, your organization created a Teams app that uses a tab to display important contact information (help desk, HR, etc.).</span></span> <span data-ttu-id="551bd-108">Da es sich jedoch um eine persönliche Registerkarte handelt, muss jeder Benutzer die Registerkarte installieren, um sie zu sehen, und die Akzeptanz ist geringer als erwartet.</span><span class="sxs-lookup"><span data-stu-id="551bd-108">However, since it's a personal tab, each user must install the tab to see it and adoption is lower than expected.</span></span> <span data-ttu-id="551bd-109">Mit anderen Worten: Zu viele Mitarbeiter wissen immer noch nicht, wie sie zum Helpdesk gelangen.</span><span class="sxs-lookup"><span data-stu-id="551bd-109">In other words, too many workers still don't know how to reach the help desk.</span></span>

<span data-ttu-id="551bd-110">Sie können diese Informationen leichter finden, indem Sie eine Kanalregisterkarte erstellen. Dadurch entlasten Sie jeden, eine App zu installieren.</span><span class="sxs-lookup"><span data-stu-id="551bd-110">You can make this information easier to find by building a channel tab, which will remove the burden of requiring everyone to install an app.</span></span> <span data-ttu-id="551bd-111">Stattdessen kann ein Benutzer die Registerkarte in einem Kanal hinzufügen oder zum Vorteil einer ganzen Gruppe chatten.</span><span class="sxs-lookup"><span data-stu-id="551bd-111">Instead, one user can add the tab in a channel or chat for the benefit of an entire group.</span></span>

## <a name="what-youll-learn"></a><span data-ttu-id="551bd-112">Was Sie lernen werden</span><span class="sxs-lookup"><span data-stu-id="551bd-112">What you'll learn</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="551bd-113">Erstellen eines App-Projekts mithilfe des Microsoft Teams Toolkit for Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="551bd-113">Create an app project using the Microsoft Teams Toolkit for Visual Studio Code</span></span>
> * <span data-ttu-id="551bd-114">Identifizieren einiger der für Kanalregisterkarten relevanten App-Konfigurationen und Gerüste</span><span class="sxs-lookup"><span data-stu-id="551bd-114">Identify some of the app configurations and scaffolding relevant to channel tabs</span></span>
> * <span data-ttu-id="551bd-115">Erstellen von Registerkarteninhalten</span><span class="sxs-lookup"><span data-stu-id="551bd-115">Create tab content</span></span>
> * <span data-ttu-id="551bd-116">Erstellen von Inhalten für die Konfigurationsseite einer Registerkarte</span><span class="sxs-lookup"><span data-stu-id="551bd-116">Create content for a tab's configuration page</span></span>
> * <span data-ttu-id="551bd-117">Bereitstellen eines vorgeschlagenen Registerkartennamens</span><span class="sxs-lookup"><span data-stu-id="551bd-117">Provide a suggested tab name</span></span>
> * <span data-ttu-id="551bd-118">Erstellen und Lokales Ausführen Ihrer App</span><span class="sxs-lookup"><span data-stu-id="551bd-118">Build and run your app locally</span></span>
> * <span data-ttu-id="551bd-119">Querladen Ihrer App in Teams zu Testzwecken</span><span class="sxs-lookup"><span data-stu-id="551bd-119">Sideload your app in Teams for testing</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="551bd-120">Vorabinformationen</span><span class="sxs-lookup"><span data-stu-id="551bd-120">Before you begin</span></span>

<span data-ttu-id="551bd-121">Falls noch nicht, stellen Sie sicher, dass Sie die Voraussetzungen für die Entwicklung von Teams verstehen und [installieren.](build-first-app-overview.md#get-prerequisites)</span><span class="sxs-lookup"><span data-stu-id="551bd-121">If you haven't yet, make sure you [understand and install the Teams development prerequisites](build-first-app-overview.md#get-prerequisites).</span></span>

## <a name="1-create-your-app-project"></a><span data-ttu-id="551bd-122">1. Erstellen Ihres App-Projekts</span><span class="sxs-lookup"><span data-stu-id="551bd-122">1. Create your app project</span></span>

<span data-ttu-id="551bd-123">Mit dem Microsoft Teams Toolkit können Sie Ihre App konfigurieren und ein Gerüst einrichten, das für Kanal- und Gruppenregisterkarten relevant ist, einschließlich einer einfachen Konfigurationsseite und einer Inhaltsseite mit dem Titel "Hello, World!"</span><span class="sxs-lookup"><span data-stu-id="551bd-123">The Microsoft Teams Toolkit helps configure your app and set up scaffolding relevant to channel and group tabs, including a basic configuration page and content page that displays a "Hello, World!"</span></span> <span data-ttu-id="551bd-124">Nachricht.</span><span class="sxs-lookup"><span data-stu-id="551bd-124">message.</span></span>

> [!TIP]
> <span data-ttu-id="551bd-125">Wenn Sie noch kein Teams-App-Projekt erstellt haben, ist [](../build-your-first-app/build-and-run.md) es möglicherweise hilfreich, diese Anweisungen zu befolgen, in der Projekte ausführlicher erläutert werden.</span><span class="sxs-lookup"><span data-stu-id="551bd-125">If you haven't created a Teams app project before, you might find it helpful to follow [these instructions](../build-your-first-app/build-and-run.md) that explain projects in more detail.</span></span>

1. Wählen Visual Studio Code auf der linken Aktivitätsleiste **Microsoft Teams** aus, und wählen :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: Sie **"Neue Teams-App erstellen" aus.**
1. <span data-ttu-id="551bd-127">Wenn Sie dazu aufgefordert werden, melden Sie sich mit Ihrem Microsoft 365-Entwicklungskonto an.</span><span class="sxs-lookup"><span data-stu-id="551bd-127">When prompted, sign in with your Microsoft 365 development account.</span></span>
1. <span data-ttu-id="551bd-128">Wählen Sie **auf dem Bildschirm** "Funktionen hinzufügen" die Option **"Tab"** und dann **"Weiter" aus.**</span><span class="sxs-lookup"><span data-stu-id="551bd-128">On the **Add capabilities** screen, select **Tab** then **Next**.</span></span>
1. <span data-ttu-id="551bd-129">Geben Sie einen Namen für Ihre Teams-App ein.</span><span class="sxs-lookup"><span data-stu-id="551bd-129">Enter a name for your Teams app.</span></span> <span data-ttu-id="551bd-130">(Dies ist der Standardname für Ihre App und auch der Name des App-Projektverzeichnisses auf dem lokalen Computer.) Wählen Sie **die Registerkarte "Gruppen- oder Teams-Kanal" aus.**</span><span class="sxs-lookup"><span data-stu-id="551bd-130">(This is the default name for your app and also the name of the app project directory on your local machine.) Select **Group or Teams channel tab**.</span></span>
1. <span data-ttu-id="551bd-131">Wählen **Sie "Fertig** stellen" am unteren Rand des Bildschirms aus, um das Projekt zu konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="551bd-131">Select **Finish** at the bottom of the screen to configure your project.</span></span>  

## <a name="2-identify-relevant-app-project-components"></a><span data-ttu-id="551bd-132">2. Identifizieren relevanter Komponenten des App-Projekts</span><span class="sxs-lookup"><span data-stu-id="551bd-132">2. Identify relevant app project components</span></span>

<span data-ttu-id="551bd-133">Ein Teil der App-Konfigurationen und -Gerüste werden automatisch eingerichtet, wenn Sie Ihr Projekt mit dem Toolkit erstellen.</span><span class="sxs-lookup"><span data-stu-id="551bd-133">Much of the app configurations and scaffolding are set up automatically when you create your project with the toolkit.</span></span> <span data-ttu-id="551bd-134">Sehen wir uns die Hauptkomponenten zum Erstellen einer Kanalregisterkarte an.</span><span class="sxs-lookup"><span data-stu-id="551bd-134">Let's look at the main components for building a channel tab.</span></span>

### <a name="app-configurations"></a><span data-ttu-id="551bd-135">App-Konfigurationen</span><span class="sxs-lookup"><span data-stu-id="551bd-135">App configurations</span></span>

<span data-ttu-id="551bd-136">Wechseln Sie im Toolkit zu **App Studio,** um Ihre App-Konfigurationen zu sehen und zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="551bd-136">In the toolkit, go to **App Studio** to view and update your app configurations.</span></span>

### <a name="app-scaffolding"></a><span data-ttu-id="551bd-137">App-Gerüst</span><span class="sxs-lookup"><span data-stu-id="551bd-137">App scaffolding</span></span>

<span data-ttu-id="551bd-138">Das App-Gerüst stellt die Komponenten zum Rendern Ihrer Kanalregisterkarte in Teams zur Seite.</span><span class="sxs-lookup"><span data-stu-id="551bd-138">The app scaffolding provides the components for rendering your channel tab in Teams.</span></span> <span data-ttu-id="551bd-139">Es gibt eine Menge, mit der Sie arbeiten können, aber derzeit müssen Sie sich nur auf Folgendes konzentrieren:</span><span class="sxs-lookup"><span data-stu-id="551bd-139">There's a lot you can work with, but for now you only need to focus on the following:</span></span>

* <span data-ttu-id="551bd-140">Zwei Dateien im Verzeichnis `src/components` Ihres Projekts:</span><span class="sxs-lookup"><span data-stu-id="551bd-140">Two files located in the `src/components` directory of your project:</span></span>
  * <span data-ttu-id="551bd-141">`Tab.js` zum Rendern der Inhaltsseite Ihrer Registerkarte.</span><span class="sxs-lookup"><span data-stu-id="551bd-141">`Tab.js` for rendering your tab's content page.</span></span>
  * <span data-ttu-id="551bd-142">`TabConfig.js` zum Rendern der Konfigurationsseite Ihrer Registerkarte.</span><span class="sxs-lookup"><span data-stu-id="551bd-142">`TabConfig.js` for rendering your tab's configuration page.</span></span>
* <span data-ttu-id="551bd-143">Microsoft Teams JavaScript-Client-SDK, das vorab in den Front-End-Komponenten Ihres Projekts geladen wird.</span><span class="sxs-lookup"><span data-stu-id="551bd-143">Microsoft Teams JavaScript client SDK, which comes pre-loaded in your project's front-end components.</span></span>

## <a name="3-customize-your-tab-content-page"></a><span data-ttu-id="551bd-144">3. Anpassen der Registerkarteninhaltsseite</span><span class="sxs-lookup"><span data-stu-id="551bd-144">3. Customize your tab content page</span></span>

<span data-ttu-id="551bd-145">Kopieren und aktualisieren Sie den folgenden Codeausschnitt mit Informationen, die für Ihre Organisation relevant sind, oder verwenden Sie den Code der Zeit nach belieben.</span><span class="sxs-lookup"><span data-stu-id="551bd-145">Copy and update the following snippet with information that's relevant to your organization or, for the sake of time, use the code as is.</span></span>

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

<span data-ttu-id="551bd-146">Wechseln Sie zum `src/components` Verzeichnis, und öffnen Sie `Tab.js` .</span><span class="sxs-lookup"><span data-stu-id="551bd-146">Go to the `src/components` directory and open `Tab.js`.</span></span> <span data-ttu-id="551bd-147">Suchen Sie die `render()` Funktion, und fügen Sie Ihren Inhalt `return()` ein (wie dargestellt).</span><span class="sxs-lookup"><span data-stu-id="551bd-147">Locate the `render()` function and paste your content inside `return()` (as shown).</span></span>

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

<span data-ttu-id="551bd-148">Fügen Sie die folgende Regel zu (auch in ) hinzu, damit die E-Mail-Links unabhängig vom verwendeten `App.css` Design leichter zu lesen `src/components` sind.</span><span class="sxs-lookup"><span data-stu-id="551bd-148">Add the following rule to `App.css` (also located in `src/components`) so the email links are easier to read no matter which theme is used.</span></span>

```CSS
a {
  color: inherit;
}
```

## <a name="4-customize-your-tab-configuration-page"></a><span data-ttu-id="551bd-149">4. Anpassen der Registerkartenkonfigurationsseite</span><span class="sxs-lookup"><span data-stu-id="551bd-149">4. Customize your tab configuration page</span></span>

<span data-ttu-id="551bd-150">Jede Registerkarte in einem Kanal oder Chat verfügt über eine Konfigurationsseite, eine modale Mit mindestens einer Setupoption, die angezeigt wird, wenn Benutzer Ihre App hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="551bd-150">Every tab in a channel or chat has a configuration page, a modal with at least one setup option that displays when users add your app.</span></span> <span data-ttu-id="551bd-151">Auf der Konfigurationsseite werden Benutzer standardmäßig gefragt, ob sie den Kanal oder chatten möchten, wenn die Registerkarte installiert ist.</span><span class="sxs-lookup"><span data-stu-id="551bd-151">The configuration page by default asks users if they want to notify the channel or chat when the tab is installed.</span></span>

<span data-ttu-id="551bd-152">Fügen Sie Ihrer Konfigurationsseite benutzerdefinierte Inhalte hinzu.</span><span class="sxs-lookup"><span data-stu-id="551bd-152">Add some custom content to your configuration page.</span></span> <span data-ttu-id="551bd-153">Wechseln Sie zum Verzeichnis Ihres Projekts, öffnen Sie das Verzeichnis, und aktualisieren Sie den Platzhalterinhalt (wie im `src/components` `TabConfig.js` folgenden Beispiel `return()` gezeigt).</span><span class="sxs-lookup"><span data-stu-id="551bd-153">Go to your project's `src/components` directory, open `TabConfig.js`, and update the placeholder content inside `return()` (as shown in the following example).</span></span>

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
> <span data-ttu-id="551bd-154">Stellen Sie auf dieser Seite mindestens einige kurze Informationen zu Ihrer App zur Verfügung, da dies das erste Mal sein kann, dass Benutzer mehr darüber wissen.</span><span class="sxs-lookup"><span data-stu-id="551bd-154">At minimum, provide some brief information about your app on this page since this may be the first time users are learning about it.</span></span> <span data-ttu-id="551bd-155">Sie können auch benutzerdefinierte Konfigurationsoptionen oder einen [Authentifizierungsworkflow](../tabs/how-to/authentication/auth-aad-sso.md)verwenden, der auf Registerkartenkonfigurationsseiten häufig verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="551bd-155">You also could include custom configuration options or an [authentication workflow](../tabs/how-to/authentication/auth-aad-sso.md), which is common on tab configuration pages.</span></span>

## <a name="5-provide-a-suggested-tab-name"></a><span data-ttu-id="551bd-156">5. Geben Sie einen vorgeschlagenen Registerkartennamen an.</span><span class="sxs-lookup"><span data-stu-id="551bd-156">5. Provide a suggested tab name</span></span>

<span data-ttu-id="551bd-157">Wenn Sie eine Kanalregisterkarte hinzufügen, wird standardmäßig der Name der App angezeigt (z. B. **First-App).**</span><span class="sxs-lookup"><span data-stu-id="551bd-157">When you add a channel tab, by default the app name displays (for example, **first-app**).</span></span>

<span data-ttu-id="551bd-158">Dies kann in Abhängigkeit von dem, was Sie Ihre App aufrufen, in Ordnung sein, Aber Sie möchten möglicherweise einen Namen bereitstellen, der im Kontext der Gruppenzusammenarbeit sinnvoller ist (z. B. **Teamkontakte).**</span><span class="sxs-lookup"><span data-stu-id="551bd-158">This may be fine depending on what you call your app, but you may want to provide a name that makes more sense in the context of group collaboration (for example, **Team Contacts**).</span></span>

1. <span data-ttu-id="551bd-159">Wechseln `TabConfig.js` Sie in zu `microsoftTeams.settings.setSettings` .</span><span class="sxs-lookup"><span data-stu-id="551bd-159">In `TabConfig.js`, go to `microsoftTeams.settings.setSettings`.</span></span>
2. <span data-ttu-id="551bd-160">Fügen Sie `suggestedDisplayName` die Eigenschaft mit dem Registerkartennamen hinzu, der standardmäßig angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="551bd-160">Add the `suggestedDisplayName` property with the tab name you want to display by default.</span></span> 
3. <span data-ttu-id="551bd-161">Verwenden Sie den im folgenden Beispiel angegebenen Namen, oder geben Sie Ihren Namen ein.</span><span class="sxs-lookup"><span data-stu-id="551bd-161">Use the name provided in the following example or type your name.</span></span> <span data-ttu-id="551bd-162">(Standardmäßig können Benutzer den Namen ändern.)</span><span class="sxs-lookup"><span data-stu-id="551bd-162">(By default, users can change the name.)</span></span>

```JavaScript
microsoftTeams.settings.setSettings({
  "contentUrl": "https://localhost:3000/tab",
  "suggestedDisplayName": "Team Contacts"
});
```

## <a name="6-build-and-run-your-app"></a><span data-ttu-id="551bd-163">6. Erstellen und Ausführen Ihrer App</span><span class="sxs-lookup"><span data-stu-id="551bd-163">6. Build and run your app</span></span>

<span data-ttu-id="551bd-164">Im Interesse der Zeit erstellen und führen Sie Ihre App lokal aus.</span><span class="sxs-lookup"><span data-stu-id="551bd-164">In the interest of time, you'll build and run your app locally.</span></span>

<span data-ttu-id="551bd-165">(Diese Informationen sind auch im Toolkit `README` verfügbar.)</span><span class="sxs-lookup"><span data-stu-id="551bd-165">(This information is also available in the toolkit `README`.)</span></span>

1. <span data-ttu-id="551bd-166">Wechseln Sie in einem Terminal zum Stammverzeichnis Ihres App-Projekts, und führen Sie es `npm install` aus.</span><span class="sxs-lookup"><span data-stu-id="551bd-166">In a terminal, go to the root directory of your app project and run `npm install`.</span></span>
1. <span data-ttu-id="551bd-167">Führen Sie `npm start` .</span><span class="sxs-lookup"><span data-stu-id="551bd-167">Run `npm start`.</span></span>

<span data-ttu-id="551bd-168">Nach Abschluss des Vorgangs wird erfolgreich **kompiliert!**</span><span class="sxs-lookup"><span data-stu-id="551bd-168">Once complete, there's a **Compiled successfully!**</span></span> <span data-ttu-id="551bd-169">im Terminal zu senden.</span><span class="sxs-lookup"><span data-stu-id="551bd-169">message in the terminal.</span></span> <span data-ttu-id="551bd-170">Ihre App wird unter `https://localhost:3000` ausgeführt.</span><span class="sxs-lookup"><span data-stu-id="551bd-170">Your app is running on `https://localhost:3000`.</span></span>

## <a name="7-sideload-your-app-in-teams"></a><span data-ttu-id="551bd-171">7. Querladen Ihrer App in Teams</span><span class="sxs-lookup"><span data-stu-id="551bd-171">7. Sideload your app in Teams</span></span>

<span data-ttu-id="551bd-172">Ihre App kann in Teams testen.</span><span class="sxs-lookup"><span data-stu-id="551bd-172">Your app is ready to test in Teams.</span></span> <span data-ttu-id="551bd-173">Dazu müssen Sie über ein Konto verfügen, das das Querladen von Apps ermöglicht.</span><span class="sxs-lookup"><span data-stu-id="551bd-173">To do this, you must have an account that allows app sideloading.</span></span> <span data-ttu-id="551bd-174">(Wenn Sie nicht sicher sind, ob Sie dies haben, erfahren Sie mehr über das Abrufen eines [Teams-Entwicklungskontos.)](../build-your-first-app/build-first-app-overview.md#set-up-your-development-account)</span><span class="sxs-lookup"><span data-stu-id="551bd-174">(If you aren't sure you have that, learn about getting a [Teams development account](../build-your-first-app/build-first-app-overview.md#set-up-your-development-account).)</span></span>

1. <span data-ttu-id="551bd-175">Drücken Visual Studio Code die **F5-TASTE,** um einen Teams-Webclient zu starten.</span><span class="sxs-lookup"><span data-stu-id="551bd-175">In Visual Studio Code, press the **F5** key to launch a Teams web client.</span></span>
1. <span data-ttu-id="551bd-176">Um Ihre App-Inhalte in Teams anzuzeigen, geben Sie an, dass der Ort, an dem Ihre App ausgeführt wird ( `localhost` ) vertrauenswürdig ist:</span><span class="sxs-lookup"><span data-stu-id="551bd-176">To display your app content in Teams, specify that where your app is running (`localhost`) is trustworthy:</span></span>
   1. <span data-ttu-id="551bd-177">Öffnen Sie eine neue Registerkarte im selben Browserfenster (standardmäßig Google Chrome), das nach drücken von **F5 geöffnet wurde.**</span><span class="sxs-lookup"><span data-stu-id="551bd-177">Open a new tab in the same browser window (Google Chrome by default) which opened after pressing **F5**.</span></span>
   1. <span data-ttu-id="551bd-178">Wechseln Sie `https://localhost:3000/tab` zu der Seite, und fahren Sie mit der Seite fort.</span><span class="sxs-lookup"><span data-stu-id="551bd-178">Go to `https://localhost:3000/tab` and proceed to the page.</span></span>
1. <span data-ttu-id="551bd-179">Wechseln Sie zurück zu Teams.</span><span class="sxs-lookup"><span data-stu-id="551bd-179">Go back to Teams.</span></span> <span data-ttu-id="551bd-180">Wählen Sie im modalen Modus "Zu einem Team **hinzufügen"** oder "Zu einem Chat **hinzufügen"** aus, und suchen Sie nach einem Kanal oder Chat, den Sie zu Testzwecken verwenden können.</span><span class="sxs-lookup"><span data-stu-id="551bd-180">In the modal, select **Add to a team** or **Add to a chat** and locate a channel or chat you can use for testing.</span></span>
1. <span data-ttu-id="551bd-181">Wählen **Sie "Registerkarte einrichten" aus.** Die Konfigurationsseite wird modal angezeigt.</span><span class="sxs-lookup"><span data-stu-id="551bd-181">Select **Set up a tab**. The configuration page displays in a modal.</span></span><br/>
   :::image type="content" source="../assets/images/tabs/channel-tab-tutorial-content.png" alt-text="Screenshot einer Konfigurationsseite für Kanalregisterkarten.":::
1. <span data-ttu-id="551bd-183">Wählen **Sie "Speichern"** aus, um die Registerkarte zu konfigurieren. Die Inhaltsseite wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="551bd-183">Select **Save** to configure the tab. The content page displays.</span></span><br/>
   :::image type="content" source="../assets/images/tabs/channel-tab-tutorial-content-installed.png" alt-text="Screenshot einer Kanalregisterkarte mit statischer Inhaltsansicht.":::

## <a name="well-done"></a><span data-ttu-id="551bd-185">Gut gemacht</span><span class="sxs-lookup"><span data-stu-id="551bd-185">Well done</span></span>

<span data-ttu-id="551bd-186">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="551bd-186">Congratulations!</span></span> <span data-ttu-id="551bd-187">Sie verfügen über eine Teams-App mit einer Registerkarte zum Anzeigen nützlicher Inhalte in Kanälen und Chats.</span><span class="sxs-lookup"><span data-stu-id="551bd-187">You have a Teams app with a tab for displaying useful content in channels and chats.</span></span>

## <a name="learn-more"></a><span data-ttu-id="551bd-188">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="551bd-188">Learn more</span></span>

* <span data-ttu-id="551bd-189">Folgen Sie [unseren Entwurfsrichtlinien,](../tabs/design/tabs.md) und erstellen Sie mit [produktionsbereiten](../concepts/design/design-teams-app-ui-templates.md) Benutzeroberflächenvorlagen, um eine nahtlose Benutzeroberfläche zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="551bd-189">Follow our [design guidelines](../tabs/design/tabs.md) and build with [production-ready UI templates](../concepts/design/design-teams-app-ui-templates.md) to create a seamless experience.</span></span>
* <span data-ttu-id="551bd-190">Informationen [zu mobilen Überlegungen](../tabs/design/tabs-mobile.md) für Registerkarten.</span><span class="sxs-lookup"><span data-stu-id="551bd-190">Understand [mobile considerations](../tabs/design/tabs-mobile.md) for tabs.</span></span>
* <span data-ttu-id="551bd-191">[Fügen Sie ihrer Registerkarte die SSO-Authentifizierung hinzu.](../tabs/how-to/authentication/auth-aad-sso.md)</span><span class="sxs-lookup"><span data-stu-id="551bd-191">[Add SSO authentication to your tab](../tabs/how-to/authentication/auth-aad-sso.md).</span></span>
* <span data-ttu-id="551bd-192">Nutzen von Microsoft Teams-Daten [mit Microsoft Graph](https://docs.microsoft.com/graph/teams-concept-overview).</span><span class="sxs-lookup"><span data-stu-id="551bd-192">Utilize Teams data with [Microsoft Graph](https://docs.microsoft.com/graph/teams-concept-overview).</span></span>
* [<span data-ttu-id="551bd-193">Erstellen einer Registerkarte ohne toolkit</span><span class="sxs-lookup"><span data-stu-id="551bd-193">Create a tab without the toolkit</span></span>](../tabs/quickstarts/create-channel-group-tab-node-yeoman.md)

## <a name="next-lesson"></a><span data-ttu-id="551bd-194">Nächste Lektion</span><span class="sxs-lookup"><span data-stu-id="551bd-194">Next lesson</span></span>

<span data-ttu-id="551bd-195">Sie wissen, wie Sie eine Registerkarte für die Zusammenarbeit erstellen.</span><span class="sxs-lookup"><span data-stu-id="551bd-195">You know how to build a tab for collaboration.</span></span> <span data-ttu-id="551bd-196">Möchten Sie versuchen, eine andere Art von Teams-App zu erstellen?</span><span class="sxs-lookup"><span data-stu-id="551bd-196">Want to try building a different kind of Teams app?</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="551bd-197">Erstellen eines Bots</span><span class="sxs-lookup"><span data-stu-id="551bd-197">Build a bot</span></span>](../build-your-first-app/build-bot.md)
