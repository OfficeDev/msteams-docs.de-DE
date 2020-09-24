---
author: heath-hamilton
description: Hier erfahren Sie, wie Sie eine Kanal-und Gruppen-Registerkarte für Ihre erste Microsoft Teams-app erstellen.
ms.author: lajanuar
ms.date: 09/22/2020
ms.topic: tutorial
title: Erstellen eines Teams-Kanals und einer Gruppenregisterkarte
ms.openlocfilehash: d97d8c13404077bff999db48b24b773aa4bc04ca
ms.sourcegitcommit: f9a2f5cedc9d30ef7a9cf78a47d01cfd277e150d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2020
ms.locfileid: "48237811"
---
# <a name="build-a-teams-channel-and-group-tab"></a><span data-ttu-id="af08c-103">Erstellen eines Teams-Kanals und einer Gruppenregisterkarte</span><span class="sxs-lookup"><span data-stu-id="af08c-103">Build a Teams channel and group tab</span></span>

<span data-ttu-id="af08c-104">In diesem Lernprogramm erstellen Sie eine einfache *Kanal Registerkarte* (auch als *Gruppe Registerkarte*bezeichnet), bei der es sich um eine voll Bild Seite für einen Teamkanal oder Chat handelt.</span><span class="sxs-lookup"><span data-stu-id="af08c-104">In this tutorial, you'll build a basic *channel tab* (also known as a *group tab*), which is a full-screen page for a team channel or chat.</span></span> <span data-ttu-id="af08c-105">Im Gegensatz zu einer persönlichen Registerkarte können Benutzer einige Aspekte dieser Registerkarte konfigurieren (beispielsweise benennen Sie die Registerkarte so um, dass Sie für Ihren Kanal sinnvoll ist).</span><span class="sxs-lookup"><span data-stu-id="af08c-105">Unlike a personal tab, users can configure some aspects of this kind of tab (for example, rename the tab so it's meaningful to their channel).</span></span>

## <a name="your-assignment"></a><span data-ttu-id="af08c-106">Ihre Zuordnung</span><span class="sxs-lookup"><span data-stu-id="af08c-106">Your assignment</span></span>

<span data-ttu-id="af08c-107">Vor kurzem hat Ihre Organisation eine Registerkarte "Teams" mit Informationen zur Kontaktaufnahme mit wichtigen Funktionen (Help Desk, HR usw.) erstellt.</span><span class="sxs-lookup"><span data-stu-id="af08c-107">Not long ago, your organization created a Teams tab with information on how to contact important functions (help desk, HR, etc.).</span></span> <span data-ttu-id="af08c-108">Da die Registerkarte jedoch nur für den persönlichen Gebrauch verwendet wurde, muss jeder Benutzer die Registerkarte installieren, um ihn anzuzeigen, und die Annahme ist niedriger als erwartet.</span><span class="sxs-lookup"><span data-stu-id="af08c-108">However, since the tab was scoped only for personal use, each user must install the tab to see it and adoption is lower than expected.</span></span> <span data-ttu-id="af08c-109">In anderen Worten: zu viele Arbeitskräfte wissen immer noch nicht, wie Sie zum Helpdesk gelangen.</span><span class="sxs-lookup"><span data-stu-id="af08c-109">In other words, too many workers still don't know how to reach the help desk.</span></span>

<span data-ttu-id="af08c-110">Sie können diese Informationen leichter finden, indem Sie eine Kanal RegisterkarteErstellen, wodurch die Belastung der Installation einer APP durch alle Benutzer beseitigt wird.</span><span class="sxs-lookup"><span data-stu-id="af08c-110">You can make this information easier to find by building a channel tab, which will remove the burden of requiring everyone to install an app.</span></span> <span data-ttu-id="af08c-111">Stattdessen kann ein Benutzer die Registerkarte in einem Kanal oder Chat zum Nutzen einer ganzen Gruppe installieren.</span><span class="sxs-lookup"><span data-stu-id="af08c-111">Instead, one user can install the tab in a channel or chat for the benefit of an entire group.</span></span>

## <a name="what-youll-learn"></a><span data-ttu-id="af08c-112">Was Sie lernen</span><span class="sxs-lookup"><span data-stu-id="af08c-112">What you'll learn</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="af08c-113">Erstellen eines App-Projekts mithilfe des Microsoft Teams-Toolkits für Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="af08c-113">Create an app project using the Microsoft Teams Toolkit for Visual Studio Code</span></span>
> * <span data-ttu-id="af08c-114">Identifizieren einiger der Eigenschaften des App-Manifests und der für Kanal-und Gruppenregisterkarten relevanten Gerüste</span><span class="sxs-lookup"><span data-stu-id="af08c-114">Identify some of the app manifest properties and scaffolding relevant to channel and group tabs</span></span>
> * <span data-ttu-id="af08c-115">Lokal Hosten einer APP</span><span class="sxs-lookup"><span data-stu-id="af08c-115">Host an app locally</span></span>
> * <span data-ttu-id="af08c-116">Erstellen von Registerkarten Inhalten</span><span class="sxs-lookup"><span data-stu-id="af08c-116">Create tab content</span></span>
> * <span data-ttu-id="af08c-117">Erstellen von Inhalten für die Konfigurationsseite einer Registerkarte</span><span class="sxs-lookup"><span data-stu-id="af08c-117">Create content for a tab's configuration page</span></span>
> * <span data-ttu-id="af08c-118">Zulassen der Konfiguration und Installation einer Registerkarte</span><span class="sxs-lookup"><span data-stu-id="af08c-118">Allow a tab to be configured and installed</span></span>
> * <span data-ttu-id="af08c-119">Angeben eines vorgeschlagenen Registerkarten namens</span><span class="sxs-lookup"><span data-stu-id="af08c-119">Provide a suggested tab name</span></span>

## <a name="1-create-your-app-project"></a><span data-ttu-id="af08c-120">1. Erstellen des App-Projekts</span><span class="sxs-lookup"><span data-stu-id="af08c-120">1. Create your app project</span></span>

<span data-ttu-id="af08c-121">Das Microsoft Teams-Toolkit hilft Ihnen beim Einrichten des App-Manifests und der für Kanal-und Gruppenregisterkarten relevanten Gerüste, einschließlich einer grundlegenden Konfigurationsseite und einer Inhaltsseite, auf der ein "Hello, World!" angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="af08c-121">The Microsoft Teams Toolkit helps you set up the app manifest and scaffolding relevant to channel and group tabs, including a basic configuration page and content page that displays a "Hello, World!"</span></span> <span data-ttu-id="af08c-122">Nachricht.</span><span class="sxs-lookup"><span data-stu-id="af08c-122">message.</span></span>

> [!TIP]
> <span data-ttu-id="af08c-123">Wenn Sie noch kein Teams-App-Projekt erstellt haben, ist es möglicherweise hilfreich, [diese Anweisungen](../build-your-first-app/build-and-run.md) zu befolgen, mit denen Projekte detaillierter erläutert werden.</span><span class="sxs-lookup"><span data-stu-id="af08c-123">If you haven't created a Teams app project before, you might find it helpful to follow [these instructions](../build-your-first-app/build-and-run.md) that explain projects in more detail.</span></span>

1. Wählen Sie in Visual Studio Code **Microsoft Teams** in :::image type="icon" source="../assets/icons/vsc-toolkit.png"::: der linken Aktivitäts Leiste aus, und wählen Sie **neue Teams-app erstellen**aus.
1. <span data-ttu-id="af08c-125">Geben Sie einen Namen für Ihre Teams-App ein.</span><span class="sxs-lookup"><span data-stu-id="af08c-125">Enter a name for your Teams app.</span></span> <span data-ttu-id="af08c-126">(Dies ist der Standardname für Ihre APP und auch der Name des App-Projektverzeichnisses auf Ihrem lokalen Computer.)</span><span class="sxs-lookup"><span data-stu-id="af08c-126">(This is the default name for your app and also the name of the app project directory on your local machine.)</span></span>
1. <span data-ttu-id="af08c-127">Wählen Sie auf dem Bildschirm **Funktionen hinzufügen** die Register **Karte** dann **Gruppe oder Teams Kanal Registerkarte**.</span><span class="sxs-lookup"><span data-stu-id="af08c-127">On the **Add capabilities** screen, select **Tab** then **Group or Teams channel tab**.</span></span>
1. <span data-ttu-id="af08c-128">Klicken Sie unten auf dem Bildschirm auf **Fertig stellen** , um Ihr Projekt zu konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="af08c-128">Select **Finish** at the bottom of the screen to configure your project.</span></span>  

## <a name="2-identify-relevant-app-project-components"></a><span data-ttu-id="af08c-129">2. Identifizieren der relevanten App-Projektkomponenten</span><span class="sxs-lookup"><span data-stu-id="af08c-129">2. Identify relevant app project components</span></span>

<span data-ttu-id="af08c-130">Ein Großteil des App-Manifests und Gerüste werden automatisch eingerichtet, wenn Sie Ihr Projekt mit dem Teams-Toolkit erstellen.</span><span class="sxs-lookup"><span data-stu-id="af08c-130">Much of the app manifest and scaffolding are set up automatically when you create your project with the Teams Toolkit.</span></span> <span data-ttu-id="af08c-131">Lassen Sie uns die Hauptkomponenten zum Erstellen einer Kanal-und Gruppenregisterkarte betrachten.</span><span class="sxs-lookup"><span data-stu-id="af08c-131">Let's look at the main components for building a channel and group tab.</span></span>

### <a name="app-manifest"></a><span data-ttu-id="af08c-132">App-Manifest</span><span class="sxs-lookup"><span data-stu-id="af08c-132">App manifest</span></span>

<span data-ttu-id="af08c-133">Der folgende Ausschnitt aus dem App-Manifest zeigt [`configurableTabs`](../resources/schema/manifest-schema.md#configurabletabs) , der die Eigenschaften und Standardwerte für Kanal-und Gruppenregisterkarten enthält.</span><span class="sxs-lookup"><span data-stu-id="af08c-133">The following snippet from the app manifest shows [`configurableTabs`](../resources/schema/manifest-schema.md#configurabletabs), which includes the properties and default values relevant to channel and group tabs.</span></span>

```JSON
"configurableTabs": [
    {
        "configurationUrl": "{baseUrl0}/config",
        "canUpdateConfiguration": true,
        "scopes": [
            "team",
            "groupchat"
        ]
    }
],
```

* <span data-ttu-id="af08c-134">`configurationUrl`: Die Host-URL für Ihre Registerkarten-Konfigurationsseite (muss https sein).</span><span class="sxs-lookup"><span data-stu-id="af08c-134">`configurationUrl`: The host URL for your tab configuration page (must be HTTPS).</span></span>
* <span data-ttu-id="af08c-135">`canUpdateConfiguration`: Wenn Sie auf festgelegt `true` ist, können Benutzer die Registerkarteneinstellungen ändern, die Registerkarte umbenennen oder aus einem Kanal oder Chat entfernen.</span><span class="sxs-lookup"><span data-stu-id="af08c-135">`canUpdateConfiguration`: If set to `true`, users can change tab settings, rename the tab, or remove it from a channel or chat.</span></span>
* <span data-ttu-id="af08c-136">`scopes`: Gibt an, ob Benutzer die app in Kanälen ( `team` ) und Chats installieren können ( `groupchat` ).</span><span class="sxs-lookup"><span data-stu-id="af08c-136">`scopes`: Specifies if users can install the app in channels (`team`) and chats (`groupchat`).</span></span> <span data-ttu-id="af08c-137">Mindestens ein Wert ist erforderlich.</span><span class="sxs-lookup"><span data-stu-id="af08c-137">At least one value is required.</span></span>

### <a name="app-scaffolding"></a><span data-ttu-id="af08c-138">App-Gerüste</span><span class="sxs-lookup"><span data-stu-id="af08c-138">App scaffolding</span></span>

<span data-ttu-id="af08c-139">Das App-Gerüst stellt eine `TabConfig.js` Datei bereit, die sich im `src/components` Verzeichnis des Projekts befindet, um die Konfigurationsseite der Registerkarte zu rendern (Weitere Informationen dazu in Kürze).</span><span class="sxs-lookup"><span data-stu-id="af08c-139">The app scaffolding provides a `TabConfig.js` file, located in the `src/components` directory of your project, for rendering your tab's configuration page (more on this soon).</span></span>

## <a name="3-run-your-app"></a><span data-ttu-id="af08c-140">3. führen Sie Ihre APP aus.</span><span class="sxs-lookup"><span data-stu-id="af08c-140">3. Run your app</span></span>

<span data-ttu-id="af08c-141">Im Interesse der Zeit erstellen und führen Sie Ihre APP lokal aus.</span><span class="sxs-lookup"><span data-stu-id="af08c-141">In the interest of time, you'll build and run your app locally.</span></span>

1. <span data-ttu-id="af08c-142">Wechseln Sie in einem Terminal zum Stammverzeichnis des App-Projekts, und führen Sie es aus `npm install` .</span><span class="sxs-lookup"><span data-stu-id="af08c-142">In a terminal, go to the root directory of your app project and run `npm install`.</span></span>
1. <span data-ttu-id="af08c-143">Ausführen `npm start` .</span><span class="sxs-lookup"><span data-stu-id="af08c-143">Run `npm start`.</span></span>

<span data-ttu-id="af08c-144">Nach Abschluss des Vorgangs wird ein **erfolgreiches kompiliert!**</span><span class="sxs-lookup"><span data-stu-id="af08c-144">Once complete, there's a **Compiled successfully!**</span></span> <span data-ttu-id="af08c-145">Nachricht im Terminal.</span><span class="sxs-lookup"><span data-stu-id="af08c-145">message in the terminal.</span></span>

## <a name="4-set-up-a-secure-tunnel-to-your-app"></a><span data-ttu-id="af08c-146">4. Einrichten eines sicheren Tunnels für Ihre APP</span><span class="sxs-lookup"><span data-stu-id="af08c-146">4. Set up a secure tunnel to your app</span></span>

<span data-ttu-id="af08c-147">Für Testzwecke hosten wir die Registerkarte auf einem lokalen Webserver (Port 3000).</span><span class="sxs-lookup"><span data-stu-id="af08c-147">For testing purposes, let's host your tab on a local web server (port 3000).</span></span>

1. <span data-ttu-id="af08c-148">Führen Sie in einem Terminal aus `ngrok http 3000` .</span><span class="sxs-lookup"><span data-stu-id="af08c-148">In a terminal, run `ngrok http 3000`.</span></span>
1. <span data-ttu-id="af08c-149">Kopieren Sie die HTTPS-URL, die Sie bereitgestellt haben.</span><span class="sxs-lookup"><span data-stu-id="af08c-149">Copy the HTTPS URL you're provided.</span></span>
1. <span data-ttu-id="af08c-150">Öffnen Sie in Ihrem `.publish` Verzeichnis `Development.env` .</span><span class="sxs-lookup"><span data-stu-id="af08c-150">In your `.publish` directory, open `Development.env`.</span></span>
1. <span data-ttu-id="af08c-151">Ersetzen Sie den `baseUrl0` Wert durch die kopierte URL.</span><span class="sxs-lookup"><span data-stu-id="af08c-151">Replace the `baseUrl0` value with the copied URL.</span></span> <span data-ttu-id="af08c-152">(Ändern Sie beispielsweise `baseUrl0=http://localhost:3000` in `baseUrl0=https://85528b2b3ca5.ngrok.io` .)</span><span class="sxs-lookup"><span data-stu-id="af08c-152">(For example, change `baseUrl0=http://localhost:3000` to `baseUrl0=https://85528b2b3ca5.ngrok.io`.)</span></span>

<span data-ttu-id="af08c-153">Ihr App-Manifest zeigt auf die Stelle, an der Sie die Registerkarte hosten.</span><span class="sxs-lookup"><span data-stu-id="af08c-153">Your app manifest is pointing to where you're hosting the tab.</span></span>

## <a name="5-customize-your-tab-content-page"></a><span data-ttu-id="af08c-154">5. Anpassen der Inhaltsseite für Registerkarten</span><span class="sxs-lookup"><span data-stu-id="af08c-154">5. Customize your tab content page</span></span>

<span data-ttu-id="af08c-155">Öffnen Sie das App-Manifest ( `manifest.json` ) im `.publish` Verzeichnis, und legen Sie die folgenden Eigenschaften in fest [`staticTabs`](../resources/schema/manifest-schema.md#statictabs) , die die Inhaltsseite ihrer Registerkarte definiert.</span><span class="sxs-lookup"><span data-stu-id="af08c-155">Open the app manifest (`manifest.json`) in the `.publish` directory and set the following properties in [`staticTabs`](../resources/schema/manifest-schema.md#statictabs), which defines your tab's content page.</span></span>

```JSON
"staticTabs": [
    {
        "entityId": "index",
        "name": "My Contacts",
        "contentUrl": "{baseUrl0}/tab",
        "scopes": [ "personal" ]
    }
],
```

<span data-ttu-id="af08c-156">Kopieren Sie den folgenden Codeausschnitt, und aktualisieren Sie ihn mit Informationen, die für Ihre Organisation relevant sind, oder verwenden Sie, um der Zeit Willen, den Code wie es ist.</span><span class="sxs-lookup"><span data-stu-id="af08c-156">Copy and update the following snippet with information that's relevant to your organization or, for the sake of time, use the code as is.</span></span>

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

<span data-ttu-id="af08c-157">Wechseln Sie zum `src/components` Verzeichnis, und öffnen Sie `Tab.js` .</span><span class="sxs-lookup"><span data-stu-id="af08c-157">Go to the `src/components` directory and open `Tab.js`.</span></span> <span data-ttu-id="af08c-158">Suchen `render()` Sie die-Funktion, und fügen Sie den Inhalt in das Bild ein `return()` (siehe Abbildung).</span><span class="sxs-lookup"><span data-stu-id="af08c-158">Locate the `render()` function and paste your content inside `return()` (as shown).</span></span>

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

<span data-ttu-id="af08c-159">Fügen Sie die folgende Regel hinzu, `App.css` damit die e-Mail-Links leichter lesbar sind, unabhängig davon, welches Design verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="af08c-159">Add the following rule to `App.css` so the email links are easier to read no matter which theme is used.</span></span>

```CSS
a {
  color: inherit;
}
```

## <a name="6-create-your-tab-configuration-page"></a><span data-ttu-id="af08c-160">6. Erstellen Ihrer Registerkarten-Konfigurationsseite</span><span class="sxs-lookup"><span data-stu-id="af08c-160">6. Create your tab configuration page</span></span>

<span data-ttu-id="af08c-161">Jede Registerkarte in einem Kanal oder Chat verfügt über eine Konfigurationsseite, eine modale mit mindestens einer Setup Option, die angezeigt wird, wenn Benutzer ihre App installieren.</span><span class="sxs-lookup"><span data-stu-id="af08c-161">Every tab in a channel or chat has a configuration page, a modal with at least one setup option that displays when users install your app.</span></span> <span data-ttu-id="af08c-162">Auf der Konfigurationsseite werden Benutzer standardmäßig gefragt, ob Sie den Kanal oder den Chat benachrichtigen möchten, wenn die Registerkarte installiert ist.</span><span class="sxs-lookup"><span data-stu-id="af08c-162">The configuration page by default asks users if they want to notify the channel or chat when the tab is installed.</span></span>

<span data-ttu-id="af08c-163">Fügen Sie der Konfigurationsseite einige Inhalte hinzu.</span><span class="sxs-lookup"><span data-stu-id="af08c-163">Add some content to your configuration page.</span></span> <span data-ttu-id="af08c-164">Wechseln Sie zum Verzeichnis Ihres Projekts `src/components` , öffnen Sie `TabConfig.js` und fügen Sie einige Inhalte in ein `return()` (siehe Abbildung).</span><span class="sxs-lookup"><span data-stu-id="af08c-164">Go to your project's `src/components` directory, open `TabConfig.js`, and insert some content inside `return()` (as shown).</span></span>

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
> <span data-ttu-id="af08c-165">Geben Sie mindestens einige kurze Informationen zu Ihrer APP auf dieser Seite, da dies das erste Mal sein kann, dass Benutzer davon erfahren.</span><span class="sxs-lookup"><span data-stu-id="af08c-165">At minimum, provide some brief information about your app on this page since this may be the first time users are learning about it.</span></span> <span data-ttu-id="af08c-166">Sie können auch benutzerdefinierte Konfigurationsoptionen oder einen [Authentifizierungs Workflow](../tabs/how-to/authentication/auth-aad-sso.md)einschließen, was bei Registerkarten-Konfigurationsseiten üblich ist.</span><span class="sxs-lookup"><span data-stu-id="af08c-166">You also could include custom configuration options or an [authentication workflow](../tabs/how-to/authentication/auth-aad-sso.md), which is common on tab configuration pages.</span></span>

## <a name="7-allow-the-tab-to-be-configured-and-installed"></a><span data-ttu-id="af08c-167">7. zulassen, dass die Registerkarte konfiguriert und installiert wird</span><span class="sxs-lookup"><span data-stu-id="af08c-167">7. Allow the tab to be configured and installed</span></span>

<span data-ttu-id="af08c-168">Damit Benutzer die Registerkarte erfolgreich konfigurieren und installieren können, müssen Sie die [sichere Host-URL](#4-set-up-a-secure-tunnel-to-your-app) hinzufügen, die Sie der Konfigurationsseiten Komponente eingerichtet haben.</span><span class="sxs-lookup"><span data-stu-id="af08c-168">For users to successfully configure and install the tab, you must add the [secure host URL you set up](#4-set-up-a-secure-tunnel-to-your-app) to the configuration page component.</span></span>

<span data-ttu-id="af08c-169">Wechseln Sie zu `TabConfig.js` und suchen Sie `microsoftTeams.settings.setSettings` .</span><span class="sxs-lookup"><span data-stu-id="af08c-169">Go to `TabConfig.js` and locate `microsoftTeams.settings.setSettings`.</span></span> <span data-ttu-id="af08c-170">`"contentUrl"`Ersetzen Sie dabei den `localhost:3000` Teil der URL durch die Domäne, in der Sie den Registerkarteninhalt hosten (siehe Abbildung).</span><span class="sxs-lookup"><span data-stu-id="af08c-170">For `"contentUrl"`, replace the `localhost:3000` part of the URL with the domain where you're hosting the tab content (as shown).</span></span>

```JavaScript
microsoftTeams.settings.setSettings({
  "contentUrl": "https://<MY_HOST_DOMAIN>/tab"
});
```

<span data-ttu-id="af08c-171">Stellen Sie außerdem sicher, dass `microsoftTeams.settings.setValidityState(true);` .</span><span class="sxs-lookup"><span data-stu-id="af08c-171">Also, make sure that `microsoftTeams.settings.setValidityState(true);`.</span></span> <span data-ttu-id="af08c-172">Standardmäßig ist `false` die Schaltfläche **Speichern** auf der Konfigurationsseite jedoch deaktiviert, wenn Sie auf festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="af08c-172">It is by default, but if set to `false`, the **Save** button is disabled on the configuration page.</span></span>

## <a name="8-provide-a-suggested-tab-name"></a><span data-ttu-id="af08c-173">8. Angeben eines vorgeschlagenen Registerkarten namens</span><span class="sxs-lookup"><span data-stu-id="af08c-173">8. Provide a suggested tab name</span></span>

<span data-ttu-id="af08c-174">Wenn Sie eine Registerkarte zur persönlichen Verwendung installieren, ist der Anzeigename die `name` Eigenschaft im `staticTabs` Teil des App-Manifests (beispielsweise " **meine Kontakte**").</span><span class="sxs-lookup"><span data-stu-id="af08c-174">When you install a tab for personal use, the display name is the `name` property in the `staticTabs` portion of the app manifest (for example, **My Contacts**).</span></span> <span data-ttu-id="af08c-175">Wenn Sie eine Kanal Registerkarte installieren, wird standardmäßig der App-Name angezeigt (beispielsweise **First-App**).</span><span class="sxs-lookup"><span data-stu-id="af08c-175">When you install a channel tab, by default the app name displays (for example, **first-app**).</span></span>

<span data-ttu-id="af08c-176">Dies ist möglicherweise in Ordnung, je nachdem, was Sie Ihre APP aufrufen, aber Sie möchten möglicherweise einen Namen angeben, der im Kontext der Gruppenzusammenarbeit sinnvoller ist (beispielsweise **Team Kontakte**).</span><span class="sxs-lookup"><span data-stu-id="af08c-176">This may be fine depending on what you call your app, but you may want to provide a name that makes more sense in the context of group collaboration (for example, **Team Contacts**).</span></span>

<span data-ttu-id="af08c-177">`TabConfig.js`Wechseln Sie in zu zurück zu `microsoftTeams.settings.setSettings` .</span><span class="sxs-lookup"><span data-stu-id="af08c-177">In `TabConfig.js`, go back to `microsoftTeams.settings.setSettings`.</span></span> <span data-ttu-id="af08c-178">Fügen `suggestedDisplayName` Sie die Eigenschaft mit dem Registerkartennamen hinzu, den Sie standardmäßig anzeigen möchten (siehe Abbildung).</span><span class="sxs-lookup"><span data-stu-id="af08c-178">Add the `suggestedDisplayName` property with the tab name you want to display by default (as shown).</span></span> <span data-ttu-id="af08c-179">Verwenden Sie den angegebenen Namen, oder erstellen Sie einen eigenen.</span><span class="sxs-lookup"><span data-stu-id="af08c-179">Use the provided name or create your own.</span></span> <span data-ttu-id="af08c-180">Denken Sie daran, dass Sie in dem Manifest Benutzern erlauben, den Namen zu ändern, wenn Sie möchten.</span><span class="sxs-lookup"><span data-stu-id="af08c-180">Remember, in the manifest you're allowing users to change the name if they want.</span></span>

```JavaScript
microsoftTeams.settings.setSettings({
  "contentUrl": "https://<MY_HOST_DOMAIN>/tab",
  "suggestedDisplayName": "Team Contacts"
});
```

## <a name="9-view-the-tab"></a><span data-ttu-id="af08c-181">9. Anzeigen der Registerkarte</span><span class="sxs-lookup"><span data-stu-id="af08c-181">9. View the tab</span></span>

<span data-ttu-id="af08c-182">Um die Konfigurations-und Inhaltsseiten ihrer Registerkarte anzuzeigen, müssen Sie Sie in einem Kanal oder Chat installieren.</span><span class="sxs-lookup"><span data-stu-id="af08c-182">To see your tab's configuration and content pages, you must install it in a channel or chat.</span></span>

1. <span data-ttu-id="af08c-183">Wählen Sie im Microsoft Teams-Client **apps**aus.</span><span class="sxs-lookup"><span data-stu-id="af08c-183">In the Teams client, select **Apps**.</span></span>
1. <span data-ttu-id="af08c-184">Wählen Sie **Upload a custom app** aus, und wählen Sie Ihre apps aus `Development.zip` .</span><span class="sxs-lookup"><span data-stu-id="af08c-184">Select **Upload a custom app** and choose your app's `Development.zip`.</span></span>
1. <span data-ttu-id="af08c-185">Wählen Sie **zu einem Team hinzufügen** oder **zu einem Chat hinzufügen** aus, und suchen Sie nach einem Kanal oder Chat, den Sie zum Testen verwenden können.</span><span class="sxs-lookup"><span data-stu-id="af08c-185">Choose **Add to a team** or **Add to a chat** and locate a channel or chat you can use for testing.</span></span>
1. <span data-ttu-id="af08c-186">Wählen Sie **Einrichten einer Registerkarte**aus. Die Konfigurationsseite wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="af08c-186">Select **Set up a tab**. The configuration page displays.</span></span><br/>
   :::image type="content" source="../assets/images/tabs/channel-tab-tutorial-content.png" alt-text="Screenshot einer Kanal Registerkarten-Konfigurationsseite.":::
1. <span data-ttu-id="af08c-188">Wählen Sie **Speichern** aus, um die Registerkarte zu konfigurieren. Der Inhalt wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="af08c-188">Select **Save** to configure the tab. The content displays.</span></span><br/>
   :::image type="content" source="../assets/images/tabs/channel-tab-tutorial-content-installed.png" alt-text="Screenshot einer Kanal Registerkarte mit statischer Inhaltsansicht.":::

## <a name="well-done"></a><span data-ttu-id="af08c-190">Gut gemacht</span><span class="sxs-lookup"><span data-stu-id="af08c-190">Well done</span></span>

<span data-ttu-id="af08c-191">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="af08c-191">Congratulations!</span></span> <span data-ttu-id="af08c-192">Sie verfügen über eine Teams-App mit einer Registerkarte, in der Sie nützliche Inhalte in Kanälen und Chats anzeigen können.</span><span class="sxs-lookup"><span data-stu-id="af08c-192">You have a Teams app with a tab for displaying useful content in channels and chats.</span></span>

## <a name="learn-more"></a><span data-ttu-id="af08c-193">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="af08c-193">Learn more</span></span>

* <span data-ttu-id="af08c-194">[Authentifizieren von Registerkarten Benutzern mit SSO](../tabs/how-to/authentication/auth-aad-sso.md): Wenn Sie nur autorisierte Benutzer Ihrer Registerkarte anzeigen möchten, richten Sie einmaliges Anmelden (Single Sign-on, SSO) über Azure Active Directory (AD) ein.</span><span class="sxs-lookup"><span data-stu-id="af08c-194">[Authenticate tab users with SSO](../tabs/how-to/authentication/auth-aad-sso.md): If you only want authorized users viewing your tab, set up single sign-on (SSO) through Azure Active Directory (AD).</span></span>
* <span data-ttu-id="af08c-195">[Einbetten von Inhalten aus einer vorhandenen Web-App oder Webseite](../tabs/how-to/add-tab.md#tab-requirements): Wir haben gezeigt, wie Sie neue Inhalte für eine persönliche RegisterkarteErstellen, aber Sie können auch Inhalte aus einer externen URL laden.</span><span class="sxs-lookup"><span data-stu-id="af08c-195">[Embed content from an existing web app or webpage](../tabs/how-to/add-tab.md#tab-requirements): We showed you how to create new content for a personal tab, but you can also load content from an external URL.</span></span>
* <span data-ttu-id="af08c-196">[Erstellen Sie eine nahtlose Benutzeroberfläche für Ihre Registerkarte](../tabs/design/tabs.md): Lesen Sie die empfohlenen Richtlinien für das Entwerfen von Microsoft Teams-Registerkarten.</span><span class="sxs-lookup"><span data-stu-id="af08c-196">[Create a seamless experience for your tab](../tabs/design/tabs.md): See the recommended guidelines for designing Teams tabs.</span></span>
* <span data-ttu-id="af08c-197">[Erstellen von Registerkarten für Mobilgeräte](../tabs/design/tabs-mobile.md): Hier erfahren Sie, wie Sie Registerkarten für Telefone und Tablets entwickeln.</span><span class="sxs-lookup"><span data-stu-id="af08c-197">[Build tabs for mobile](../tabs/design/tabs-mobile.md): Understand how to develop tabs for phones and tablets.</span></span>
* [<span data-ttu-id="af08c-198">Erstellen einer Registerkarte ohne Toolkit</span><span class="sxs-lookup"><span data-stu-id="af08c-198">Create a tab without the toolkit</span></span>](../tabs/how-to/add-tab.md)

## <a name="next-lesson"></a><span data-ttu-id="af08c-199">Nächste Lektion</span><span class="sxs-lookup"><span data-stu-id="af08c-199">Next lesson</span></span>

<span data-ttu-id="af08c-200">Sie wissen, wie Sie eine Registerkarte für die Zusammenarbeit erstellen.</span><span class="sxs-lookup"><span data-stu-id="af08c-200">You know how to build a tab for collaboration.</span></span> <span data-ttu-id="af08c-201">Möchten Sie versuchen, eine andere Art von Teams-APP zu erstellen?</span><span class="sxs-lookup"><span data-stu-id="af08c-201">Want to try building a different kind of Teams app?</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="af08c-202">Erstellen eines bot</span><span class="sxs-lookup"><span data-stu-id="af08c-202">Build a bot</span></span>](../build-your-first-app/build-bot.md)
