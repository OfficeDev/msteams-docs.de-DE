---
title: Erste Schritte – Erstellen einer Kanal-und Gruppenregisterkarte
author: heath-hamilton
description: Erstellen Sie mit dem Microsoft Teams-Toolkit schnell eine Microsoft Teams-Kanal-und-Gruppen-Registerkarte.
ms.author: lajanuar
ms.date: 10/09/2020
ms.topic: tutorial
ms.openlocfilehash: bb87d34974469057287cf63725e7722125c57c34
ms.sourcegitcommit: c102da958759c13aa9e0f81bde1cffb34a8bef34
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/09/2020
ms.locfileid: "49605245"
---
# <a name="build-a-channel-and-group-tab-for-microsoft-teams"></a><span data-ttu-id="bce57-103">Erstellen einer Kanal-und Gruppenregisterkarte für Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="bce57-103">Build a channel and group tab for Microsoft Teams</span></span>

<span data-ttu-id="bce57-104">In diesem Lernprogramm erstellen Sie eine einfache *Kanal Registerkarte* (auch als *Gruppe Registerkarte* bezeichnet), bei der es sich um eine voll Bild Seite für einen Teamkanal oder Chat handelt.</span><span class="sxs-lookup"><span data-stu-id="bce57-104">In this tutorial, you'll build a basic *channel tab* (also known as a *group tab*), which is a full-screen page for a team channel or chat.</span></span> <span data-ttu-id="bce57-105">Im Gegensatz zu einer persönlichen Registerkarte können Benutzer einige Aspekte dieser Registerkarte konfigurieren (beispielsweise benennen Sie die Registerkarte so um, dass Sie für Ihren Kanal sinnvoll ist).</span><span class="sxs-lookup"><span data-stu-id="bce57-105">Unlike a personal tab, users can configure some aspects of this kind of tab (for example, rename the tab so it's meaningful to their channel).</span></span>

## <a name="your-assignment"></a><span data-ttu-id="bce57-106">Ihre Zuordnung</span><span class="sxs-lookup"><span data-stu-id="bce57-106">Your assignment</span></span>

<span data-ttu-id="bce57-107">Vor kurzem hat Ihre Organisation eine Teams-App erstellt, die eine Registerkarte zum Anzeigen wichtiger Kontaktinformationen (Helpdesk, HR usw.) verwendet.</span><span class="sxs-lookup"><span data-stu-id="bce57-107">Not long ago, your organization created a Teams app that uses a tab to display important contact information (help desk, HR, etc.).</span></span> <span data-ttu-id="bce57-108">Da es sich jedoch um eine persönliche Registerkarte handelt, muss jeder Benutzer die Registerkarte installieren, um es anzuzeigen, und die Annahme ist niedriger als erwartet.</span><span class="sxs-lookup"><span data-stu-id="bce57-108">However, since it's a personal tab, each user must install the tab to see it and adoption is lower than expected.</span></span> <span data-ttu-id="bce57-109">In anderen Worten: zu viele Arbeitskräfte wissen immer noch nicht, wie Sie zum Helpdesk gelangen.</span><span class="sxs-lookup"><span data-stu-id="bce57-109">In other words, too many workers still don't know how to reach the help desk.</span></span>

<span data-ttu-id="bce57-110">Sie können diese Informationen leichter finden, indem Sie eine Kanal RegisterkarteErstellen, wodurch die Belastung der Installation einer APP durch alle Benutzer beseitigt wird.</span><span class="sxs-lookup"><span data-stu-id="bce57-110">You can make this information easier to find by building a channel tab, which will remove the burden of requiring everyone to install an app.</span></span> <span data-ttu-id="bce57-111">Stattdessen kann ein Benutzer die Registerkarte in einem Kanal oder Chat zum Nutzen einer ganzen Gruppe hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="bce57-111">Instead, one user can add the tab in a channel or chat for the benefit of an entire group.</span></span>

## <a name="what-youll-learn"></a><span data-ttu-id="bce57-112">Was Sie lernen</span><span class="sxs-lookup"><span data-stu-id="bce57-112">What you'll learn</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="bce57-113">Erstellen eines App-Projekts mithilfe des Microsoft Teams-Toolkits für Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="bce57-113">Create an app project using the Microsoft Teams Toolkit for Visual Studio Code</span></span>
> * <span data-ttu-id="bce57-114">Identifizieren einiger der für Kanal-und Gruppenregisterkarten relevanten App-Konfigurationen und Gerüste</span><span class="sxs-lookup"><span data-stu-id="bce57-114">Identify some of the app configurations and scaffolding relevant to channel and group tabs</span></span>
> * <span data-ttu-id="bce57-115">Erstellen von Registerkarten Inhalten</span><span class="sxs-lookup"><span data-stu-id="bce57-115">Create tab content</span></span>
> * <span data-ttu-id="bce57-116">Erstellen von Inhalten für die Konfigurationsseite einer Registerkarte</span><span class="sxs-lookup"><span data-stu-id="bce57-116">Create content for a tab's configuration page</span></span>
> * <span data-ttu-id="bce57-117">Angeben eines vorgeschlagenen Registerkarten namens</span><span class="sxs-lookup"><span data-stu-id="bce57-117">Provide a suggested tab name</span></span>
> * <span data-ttu-id="bce57-118">Lokales erstellen und Ausführen der APP</span><span class="sxs-lookup"><span data-stu-id="bce57-118">Build and run your app locally</span></span>
> * <span data-ttu-id="bce57-119">Querladen ihrer app in Teams zum Testen</span><span class="sxs-lookup"><span data-stu-id="bce57-119">Sideload your app in Teams for testing</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="bce57-120">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="bce57-120">Before you begin</span></span>

<span data-ttu-id="bce57-121">Wenn Sie noch nicht vorhanden sind, stellen Sie sicher, dass Sie [die Entwicklungsvoraussetzungen für Teams kennen und installieren](build-first-app-overview.md#get-prerequisites).</span><span class="sxs-lookup"><span data-stu-id="bce57-121">If you haven't yet, make sure you [understand and install the Teams development prerequisites](build-first-app-overview.md#get-prerequisites).</span></span>

## <a name="1-create-your-app-project"></a><span data-ttu-id="bce57-122">1. Erstellen des App-Projekts</span><span class="sxs-lookup"><span data-stu-id="bce57-122">1. Create your app project</span></span>

<span data-ttu-id="bce57-123">Das Microsoft Teams-Toolkit unterstützt die Konfiguration Ihrer APP und das Einrichten von für Kanal-und Gruppenregisterkarten relevanten Gerüsten, einschließlich einer grundlegenden Konfigurationsseite und einer Inhaltsseite, auf der ein "Hello, World!" angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="bce57-123">The Microsoft Teams Toolkit helps configure your app and set up scaffolding relevant to channel and group tabs, including a basic configuration page and content page that displays a "Hello, World!"</span></span> <span data-ttu-id="bce57-124">Nachricht.</span><span class="sxs-lookup"><span data-stu-id="bce57-124">message.</span></span>

> [!TIP]
> <span data-ttu-id="bce57-125">Wenn Sie noch kein Teams-App-Projekt erstellt haben, ist es möglicherweise hilfreich, [diese Anweisungen](../build-your-first-app/build-and-run.md) zu befolgen, mit denen Projekte detaillierter erläutert werden.</span><span class="sxs-lookup"><span data-stu-id="bce57-125">If you haven't created a Teams app project before, you might find it helpful to follow [these instructions](../build-your-first-app/build-and-run.md) that explain projects in more detail.</span></span>

1. Wählen Sie in Visual Studio Code **Microsoft Teams** in :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: der linken Aktivitäts Leiste aus, und wählen Sie **neue Teams-app erstellen** aus.
1. <span data-ttu-id="bce57-127">Wenn Sie dazu aufgefordert werden, melden Sie sich mit Ihrem Microsoft 365-entwicklungskonto an.</span><span class="sxs-lookup"><span data-stu-id="bce57-127">When prompted, sign in with your Microsoft 365 development account.</span></span>
1. <span data-ttu-id="bce57-128">Wählen Sie auf dem Bildschirm **Funktionen hinzufügen** die Option **Tab** und dann dann **weiter** aus.</span><span class="sxs-lookup"><span data-stu-id="bce57-128">On the **Add capabilities** screen, select **Tab** then **Next**.</span></span>
1. <span data-ttu-id="bce57-129">Geben Sie einen Namen für Ihre Teams-App ein.</span><span class="sxs-lookup"><span data-stu-id="bce57-129">Enter a name for your Teams app.</span></span> <span data-ttu-id="bce57-130">(Dies ist der Standardname für Ihre APP und auch der Name des App-Projektverzeichnisses auf Ihrem lokalen Computer.)</span><span class="sxs-lookup"><span data-stu-id="bce57-130">(This is the default name for your app and also the name of the app project directory on your local machine.)</span></span>
1. <span data-ttu-id="bce57-131">Überprüfen Sie die Optionen auf der Registerkarte **persönliche** und **Gruppen-oder Teams-Kanäle** .</span><span class="sxs-lookup"><span data-stu-id="bce57-131">Check the **Personal tab** and **Group or Teams channel tab** options.</span></span> <span data-ttu-id="bce57-132">(In Kürze erfahren Sie, warum Sie beide Arten von Registerkarten benötigen.)</span><span class="sxs-lookup"><span data-stu-id="bce57-132">(You'll soon learn why you need both types of tabs.)</span></span>
1. <span data-ttu-id="bce57-133">Klicken Sie unten auf dem Bildschirm auf **Fertig stellen** , um Ihr Projekt zu konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="bce57-133">Select **Finish** at the bottom of the screen to configure your project.</span></span>  

## <a name="2-identify-relevant-app-project-components"></a><span data-ttu-id="bce57-134">2. Identifizieren der relevanten App-Projektkomponenten</span><span class="sxs-lookup"><span data-stu-id="bce57-134">2. Identify relevant app project components</span></span>

<span data-ttu-id="bce57-135">Viele der APP-Konfigurationen und Gerüste werden automatisch eingerichtet, wenn Sie Ihr Projekt mit dem Teams-Toolkit erstellen.</span><span class="sxs-lookup"><span data-stu-id="bce57-135">Much of the app configurations and scaffolding are set up automatically when you create your project with the Teams Toolkit.</span></span> <span data-ttu-id="bce57-136">Lassen Sie uns die Hauptkomponenten zum Erstellen einer Kanal-und Gruppenregisterkarte betrachten.</span><span class="sxs-lookup"><span data-stu-id="bce57-136">Let's look at the main components for building a channel and group tab.</span></span>

### <a name="app-configurations"></a><span data-ttu-id="bce57-137">App-Konfigurationen</span><span class="sxs-lookup"><span data-stu-id="bce57-137">App configurations</span></span>

<span data-ttu-id="bce57-138">Sie können Ihre APP-Konfigurationen mithilfe von App Studio anzeigen und aktualisieren, die im Toolkit enthalten ist.</span><span class="sxs-lookup"><span data-stu-id="bce57-138">You can view and update your app configurations using App Studio, which is included in the toolkit.</span></span>

<span data-ttu-id="bce57-139">Während des Setups hat das Toolkit zunächst zwei wesentliche Komponenten von Kanal-und Gruppenregisterkarten konfiguriert:</span><span class="sxs-lookup"><span data-stu-id="bce57-139">During setup, the toolkit initially configured two essential components of channel and group tabs:</span></span>

* <span data-ttu-id="bce57-140">**Konfigurationsseite**: das modale zum Hinzufügen einer Registerkarte zu einem Kanal oder Chat.</span><span class="sxs-lookup"><span data-stu-id="bce57-140">**Configuration page**: The modal for adding a tab to a channel or chat.</span></span> <span data-ttu-id="bce57-141">(In App Studio können Sie diese Seite finden, indem Sie auf **Tabs > Registerkarte "Team"** wechseln.)</span><span class="sxs-lookup"><span data-stu-id="bce57-141">(In App Studio, you can find this page by going to **Tabs > Team tab**.)</span></span>
* <span data-ttu-id="bce57-142">**Inhaltsseite**: dort, wo Sie Ihren primären Inhalt anzeigen.</span><span class="sxs-lookup"><span data-stu-id="bce57-142">**Content page**: Where you display your primary content.</span></span> <span data-ttu-id="bce57-143">(In App Studio können Sie diese Seite finden, indem Sie zu **Registerkarten wechseln > eine persönliche Registerkarte hinzufügen**.)</span><span class="sxs-lookup"><span data-stu-id="bce57-143">(In App Studio, you can find this page by going to **Tabs > Add a personal tab**.)</span></span>

### <a name="app-scaffolding"></a><span data-ttu-id="bce57-144">App-Gerüste</span><span class="sxs-lookup"><span data-stu-id="bce57-144">App scaffolding</span></span>

<span data-ttu-id="bce57-145">Das App-Gerüst stellt die Komponenten zum Rendern Ihrer persönlichen Registerkarte in Microsoft Teams bereit.</span><span class="sxs-lookup"><span data-stu-id="bce57-145">The app scaffolding provides the components for rendering your personal tab in Teams.</span></span> <span data-ttu-id="bce57-146">Es gibt eine Menge, mit der Sie arbeiten können, aber im Moment müssen Sie sich nur auf Folgendes konzentrieren:</span><span class="sxs-lookup"><span data-stu-id="bce57-146">There's a lot you can work with, but for now you only need to focus on the following:</span></span>

* <span data-ttu-id="bce57-147">Zwei Dateien, die sich im `src/components` Verzeichnis des Projekts befinden:</span><span class="sxs-lookup"><span data-stu-id="bce57-147">Two files located in the `src/components` directory of your project:</span></span>
  * <span data-ttu-id="bce57-148">`Tab.js` zum Rendern der Inhaltsseite der Registerkarte.</span><span class="sxs-lookup"><span data-stu-id="bce57-148">`Tab.js` for rendering your tab's content page.</span></span>
  * <span data-ttu-id="bce57-149">`TabConfig.js` zum Rendern der Konfigurationsseite der Registerkarte.</span><span class="sxs-lookup"><span data-stu-id="bce57-149">`TabConfig.js` for rendering your tab's configuration page.</span></span>
* <span data-ttu-id="bce57-150">Microsoft Teams JavaScript-Client-SDK, das in den Front-End-Komponenten Ihres Projekts vorinstalliert ist.</span><span class="sxs-lookup"><span data-stu-id="bce57-150">Microsoft Teams JavaScript client SDK, which comes pre-loaded in your project's front-end components.</span></span>

## <a name="3-customize-your-tab-content-page"></a><span data-ttu-id="bce57-151">3. Anpassen der Inhaltsseite der Registerkarte</span><span class="sxs-lookup"><span data-stu-id="bce57-151">3. Customize your tab content page</span></span>

<span data-ttu-id="bce57-152">Kopieren Sie den folgenden Codeausschnitt, und aktualisieren Sie ihn mit Informationen, die für Ihre Organisation relevant sind, oder verwenden Sie, um der Zeit Willen, den Code wie es ist.</span><span class="sxs-lookup"><span data-stu-id="bce57-152">Copy and update the following snippet with information that's relevant to your organization or, for the sake of time, use the code as is.</span></span>

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

<span data-ttu-id="bce57-153">Wechseln Sie zum `src/components` Verzeichnis, und öffnen Sie `Tab.js` .</span><span class="sxs-lookup"><span data-stu-id="bce57-153">Go to the `src/components` directory and open `Tab.js`.</span></span> <span data-ttu-id="bce57-154">Suchen `render()` Sie die-Funktion, und fügen Sie den Inhalt in das Bild ein `return()` (siehe Abbildung).</span><span class="sxs-lookup"><span data-stu-id="bce57-154">Locate the `render()` function and paste your content inside `return()` (as shown).</span></span>

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

<span data-ttu-id="bce57-155">Fügen Sie die folgende Regel zu hinzu `App.css` (befindet sich auch in `src/components` ), sodass die e-Mail-Links leichter lesbar sind, unabhängig davon, welches Design verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="bce57-155">Add the following rule to `App.css` (also located in `src/components`) so the email links are easier to read no matter which theme is used.</span></span>

```CSS
a {
  color: inherit;
}
```

## <a name="4-customize-your-tab-configuration-page"></a><span data-ttu-id="bce57-156">4. Anpassen Ihrer Registerkarten-Konfigurationsseite</span><span class="sxs-lookup"><span data-stu-id="bce57-156">4. Customize your tab configuration page</span></span>

<span data-ttu-id="bce57-157">Jede Registerkarte in einem Kanal oder Chat verfügt über eine Konfigurationsseite, eine modale mit mindestens einer Setup Option, die angezeigt wird, wenn Benutzer Ihre APP hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="bce57-157">Every tab in a channel or chat has a configuration page, a modal with at least one setup option that displays when users add your app.</span></span> <span data-ttu-id="bce57-158">Auf der Konfigurationsseite werden Benutzer standardmäßig gefragt, ob Sie den Kanal oder den Chat benachrichtigen möchten, wenn die Registerkarte installiert ist.</span><span class="sxs-lookup"><span data-stu-id="bce57-158">The configuration page by default asks users if they want to notify the channel or chat when the tab is installed.</span></span>

<span data-ttu-id="bce57-159">Fügen Sie der Konfigurationsseite einige benutzerdefinierte Inhalte hinzu.</span><span class="sxs-lookup"><span data-stu-id="bce57-159">Add some custom content to your configuration page.</span></span> <span data-ttu-id="bce57-160">Wechseln Sie zum Verzeichnis des Projekts `src/components` , öffnen Sie `TabConfig.js` , und aktualisieren Sie den Platzhalterinhalt in `return()` (wie im folgenden Beispiel dargestellt).</span><span class="sxs-lookup"><span data-stu-id="bce57-160">Go to your project's `src/components` directory, open `TabConfig.js`, and update the placeholder content inside `return()` (as shown in the following example).</span></span>

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
> <span data-ttu-id="bce57-161">Geben Sie mindestens einige kurze Informationen zu Ihrer APP auf dieser Seite, da dies das erste Mal sein kann, dass Benutzer davon erfahren.</span><span class="sxs-lookup"><span data-stu-id="bce57-161">At minimum, provide some brief information about your app on this page since this may be the first time users are learning about it.</span></span> <span data-ttu-id="bce57-162">Sie können auch benutzerdefinierte Konfigurationsoptionen oder einen [Authentifizierungs Workflow](../tabs/how-to/authentication/auth-aad-sso.md)einschließen, was bei Registerkarten-Konfigurationsseiten üblich ist.</span><span class="sxs-lookup"><span data-stu-id="bce57-162">You also could include custom configuration options or an [authentication workflow](../tabs/how-to/authentication/auth-aad-sso.md), which is common on tab configuration pages.</span></span>

## <a name="5-provide-a-suggested-tab-name"></a><span data-ttu-id="bce57-163">5. Angeben eines vorgeschlagenen Registerkarten namens</span><span class="sxs-lookup"><span data-stu-id="bce57-163">5. Provide a suggested tab name</span></span>

<span data-ttu-id="bce57-164">Wenn Sie eine Kanal-oder Gruppenregisterkarte hinzufügen, wird standardmäßig der App-Name angezeigt (beispielsweise **First-App**).</span><span class="sxs-lookup"><span data-stu-id="bce57-164">When you add a channel or group tab, by default the app name displays (for example, **first-app**).</span></span>

<span data-ttu-id="bce57-165">Dies ist möglicherweise in Ordnung, je nachdem, was Sie Ihre APP aufrufen, aber Sie möchten möglicherweise einen Namen angeben, der im Kontext der Gruppenzusammenarbeit sinnvoller ist (beispielsweise **Team Kontakte**).</span><span class="sxs-lookup"><span data-stu-id="bce57-165">This may be fine depending on what you call your app, but you may want to provide a name that makes more sense in the context of group collaboration (for example, **Team Contacts**).</span></span>

<span data-ttu-id="bce57-166">`TabConfig.js`Wechseln Sie in zu `microsoftTeams.settings.setSettings` .</span><span class="sxs-lookup"><span data-stu-id="bce57-166">In `TabConfig.js`, go to `microsoftTeams.settings.setSettings`.</span></span> <span data-ttu-id="bce57-167">Fügen `suggestedDisplayName` Sie die Eigenschaft mit dem Registerkartennamen hinzu, den Sie standardmäßig anzeigen möchten (siehe Abbildung).</span><span class="sxs-lookup"><span data-stu-id="bce57-167">Add the `suggestedDisplayName` property with the tab name you want to display by default (as shown).</span></span> <span data-ttu-id="bce57-168">Verwenden Sie den angegebenen Namen, oder erstellen Sie einen eigenen.</span><span class="sxs-lookup"><span data-stu-id="bce57-168">Use the provided name or create your own.</span></span> <span data-ttu-id="bce57-169">(Standardmäßig können Benutzer den Namen ändern, falls gewünscht.)</span><span class="sxs-lookup"><span data-stu-id="bce57-169">(By default, users to change the name if they want.)</span></span>

```JavaScript
microsoftTeams.settings.setSettings({
  "contentUrl": "https://localhost:3000/tab",
  "suggestedDisplayName": "Team Contacts"
});
```

## <a name="6-build-and-run-your-app"></a><span data-ttu-id="bce57-170">6. erstellen und Ausführen der APP</span><span class="sxs-lookup"><span data-stu-id="bce57-170">6. Build and run your app</span></span>

<span data-ttu-id="bce57-171">Im Interesse der Zeit erstellen und führen Sie Ihre APP lokal aus.</span><span class="sxs-lookup"><span data-stu-id="bce57-171">In the interest of time, you'll build and run your app locally.</span></span>

<span data-ttu-id="bce57-172">(Diese Informationen sind auch im Toolkit verfügbar `README` .)</span><span class="sxs-lookup"><span data-stu-id="bce57-172">(This information is also available in the toolkit `README`.)</span></span>

1. <span data-ttu-id="bce57-173">Wechseln Sie in einem Terminal zum Stammverzeichnis des App-Projekts, und führen Sie es aus `npm install` .</span><span class="sxs-lookup"><span data-stu-id="bce57-173">In a terminal, go to the root directory of your app project and run `npm install`.</span></span>
1. <span data-ttu-id="bce57-174">Ausführen `npm start` .</span><span class="sxs-lookup"><span data-stu-id="bce57-174">Run `npm start`.</span></span>

<span data-ttu-id="bce57-175">Nach Abschluss des Vorgangs wird ein **erfolgreiches kompiliert!**</span><span class="sxs-lookup"><span data-stu-id="bce57-175">Once complete, there's a **Compiled successfully!**</span></span> <span data-ttu-id="bce57-176">Nachricht im Terminal.</span><span class="sxs-lookup"><span data-stu-id="bce57-176">message in the terminal.</span></span> <span data-ttu-id="bce57-177">Ihre APP wird gestartet `https://localhost:3000` .</span><span class="sxs-lookup"><span data-stu-id="bce57-177">Your app is running on `https://localhost:3000`.</span></span>

## <a name="7-sideload-your-app-in-teams"></a><span data-ttu-id="bce57-178">7. querladen ihrer app in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="bce57-178">7. Sideload your app in Teams</span></span>

<span data-ttu-id="bce57-179">Ihre APP ist zum Testen in Microsoft Teams verfügbar.</span><span class="sxs-lookup"><span data-stu-id="bce57-179">Your app is ready to test in Teams.</span></span> <span data-ttu-id="bce57-180">Hierzu benötigen Sie ein Konto, das App-Sideloading zulässt.</span><span class="sxs-lookup"><span data-stu-id="bce57-180">To do this, you must have an account that allows app sideloading.</span></span> <span data-ttu-id="bce57-181">(Wenn Sie nicht sicher sind, dass dies der Fall ist, erfahren Sie mehr über das [Einrichten eines Teams-entwicklungskontos](../build-your-first-app/build-first-app-overview.md#set-up-your-development-account).)</span><span class="sxs-lookup"><span data-stu-id="bce57-181">(If you aren't sure you have that, learn about getting a [Teams development account](../build-your-first-app/build-first-app-overview.md#set-up-your-development-account).)</span></span>

1. <span data-ttu-id="bce57-182">Drücken Sie in Visual Studio Code die **F5** -Taste, um einen Microsoft Teams-WebClient zu starten.</span><span class="sxs-lookup"><span data-stu-id="bce57-182">In Visual Studio Code, press the **F5** key to launch a Teams web client.</span></span>
1. <span data-ttu-id="bce57-183">Um Ihre APP-Inhalte in Microsoft Teams anzuzeigen, geben Sie an, wo Ihre APP aktiv ist ( `localhost` ) vertrauenswürdig ist:</span><span class="sxs-lookup"><span data-stu-id="bce57-183">To display your app content in Teams, specify that where your app is running (`localhost`) is trustworthy:</span></span>
   1. <span data-ttu-id="bce57-184">Öffnen Sie eine neue Registerkarte in demselben Browserfenster (standardmäßig Google Chrome), die nach Drücken von **F5** geöffnet wurde.</span><span class="sxs-lookup"><span data-stu-id="bce57-184">Open a new tab in the same browser window (Google Chrome by default) which opened after pressing **F5**.</span></span>
   1. <span data-ttu-id="bce57-185">Wechseln Sie zu `https://localhost:3000/tab` der Seite, und fahren Sie fort.</span><span class="sxs-lookup"><span data-stu-id="bce57-185">Go to `https://localhost:3000/tab` and proceed to the page.</span></span>
1. <span data-ttu-id="bce57-186">Wechseln Sie zurück zu Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="bce57-186">Go back to Teams.</span></span> <span data-ttu-id="bce57-187">Wählen Sie im modalen Modus **zu einem Team hinzufügen** oder **zu einem Chat hinzufügen** aus, und suchen Sie nach einem Kanal oder Chat, den Sie zum Testen verwenden können.</span><span class="sxs-lookup"><span data-stu-id="bce57-187">In the modal, select **Add to a team** or **Add to a chat** and locate a channel or chat you can use for testing.</span></span>
1. <span data-ttu-id="bce57-188">Wählen Sie **Einrichten einer Registerkarte** aus. Die Konfigurationsseite wird in einem modalen angezeigt.</span><span class="sxs-lookup"><span data-stu-id="bce57-188">Select **Set up a tab**. The configuration page displays in a modal.</span></span><br/>
   :::image type="content" source="../assets/images/tabs/channel-tab-tutorial-content.png" alt-text="Screenshot einer Kanal Registerkarten-Konfigurationsseite.":::
1. <span data-ttu-id="bce57-190">Wählen Sie **Speichern** aus, um die Registerkarte zu konfigurieren. Die Inhaltsseite wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="bce57-190">Select **Save** to configure the tab. The content page displays.</span></span><br/>
   :::image type="content" source="../assets/images/tabs/channel-tab-tutorial-content-installed.png" alt-text="Screenshot einer Kanal Registerkarte mit statischer Inhaltsansicht.":::

## <a name="well-done"></a><span data-ttu-id="bce57-192">Gut gemacht</span><span class="sxs-lookup"><span data-stu-id="bce57-192">Well done</span></span>

<span data-ttu-id="bce57-193">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="bce57-193">Congratulations!</span></span> <span data-ttu-id="bce57-194">Sie verfügen über eine Teams-App mit einer Registerkarte, in der Sie nützliche Inhalte in Kanälen und Chats anzeigen können.</span><span class="sxs-lookup"><span data-stu-id="bce57-194">You have a Teams app with a tab for displaying useful content in channels and chats.</span></span>

## <a name="learn-more"></a><span data-ttu-id="bce57-195">Mehr erfahren</span><span class="sxs-lookup"><span data-stu-id="bce57-195">Learn more</span></span>

* <span data-ttu-id="bce57-196">[Authentifizieren von Registerkarten Benutzern mit SSO](../tabs/how-to/authentication/auth-aad-sso.md): Wenn Sie nur autorisierte Benutzer Ihrer Registerkarte anzeigen möchten, richten Sie einmaliges Anmelden (Single Sign-on, SSO) über Azure Active Directory (AD) ein.</span><span class="sxs-lookup"><span data-stu-id="bce57-196">[Authenticate tab users with SSO](../tabs/how-to/authentication/auth-aad-sso.md): If you only want authorized users viewing your tab, set up single sign-on (SSO) through Azure Active Directory (AD).</span></span>
* <span data-ttu-id="bce57-197">[Einbetten von Inhalten aus einer vorhandenen Web-App oder Webseite](../tabs/how-to/add-tab.md#tab-requirements): Wir haben gezeigt, wie Sie neue Inhalte für eine persönliche RegisterkarteErstellen, aber Sie können auch Inhalte aus einer externen URL laden.</span><span class="sxs-lookup"><span data-stu-id="bce57-197">[Embed content from an existing web app or webpage](../tabs/how-to/add-tab.md#tab-requirements): We showed you how to create new content for a personal tab, but you can also load content from an external URL.</span></span>
* <span data-ttu-id="bce57-198">[Erstellen Sie eine nahtlose Benutzeroberfläche für Ihre Registerkarte](../tabs/design/tabs.md): Lesen Sie die empfohlenen Richtlinien für das Entwerfen von Microsoft Teams-Registerkarten.</span><span class="sxs-lookup"><span data-stu-id="bce57-198">[Create a seamless experience for your tab](../tabs/design/tabs.md): See the recommended guidelines for designing Teams tabs.</span></span>
* <span data-ttu-id="bce57-199">[Erstellen von Registerkarten für Mobilgeräte](../tabs/design/tabs-mobile.md): Hier erfahren Sie, wie Sie Registerkarten für Telefone und Tablets entwickeln.</span><span class="sxs-lookup"><span data-stu-id="bce57-199">[Build tabs for mobile](../tabs/design/tabs-mobile.md): Understand how to develop tabs for phones and tablets.</span></span>
* [<span data-ttu-id="bce57-200">Verwenden von Teams-Daten mit der Microsoft Graph-API</span><span class="sxs-lookup"><span data-stu-id="bce57-200">Utilize Teams data with the Microsoft Graph API</span></span>](https://docs.microsoft.com/graph/teams-concept-overview)
* [<span data-ttu-id="bce57-201">Erstellen einer Registerkarte ohne Toolkit</span><span class="sxs-lookup"><span data-stu-id="bce57-201">Create a tab without the toolkit</span></span>](../tabs/how-to/add-tab.md)

## <a name="next-lesson"></a><span data-ttu-id="bce57-202">Nächste Lektion</span><span class="sxs-lookup"><span data-stu-id="bce57-202">Next lesson</span></span>

<span data-ttu-id="bce57-203">Sie wissen, wie Sie eine Registerkarte für die Zusammenarbeit erstellen.</span><span class="sxs-lookup"><span data-stu-id="bce57-203">You know how to build a tab for collaboration.</span></span> <span data-ttu-id="bce57-204">Möchten Sie versuchen, eine andere Art von Teams-APP zu erstellen?</span><span class="sxs-lookup"><span data-stu-id="bce57-204">Want to try building a different kind of Teams app?</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="bce57-205">Erstellen eines Bots</span><span class="sxs-lookup"><span data-stu-id="bce57-205">Build a bot</span></span>](../build-your-first-app/build-bot.md)
