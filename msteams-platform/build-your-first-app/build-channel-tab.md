---
author: heath-hamilton
description: Hier erfahren Sie, wie Sie eine Kanal Registerkarte für Ihre erste Microsoft Teams-app erstellen.
ms.author: lajanuar
ms.date: 09/22/2020
ms.topic: tutorial
title: Erstellen einer Microsoft Teams-Kanal Registerkarte
ms.openlocfilehash: d0846c3af23fd9df6013f989e9f455f711d05a5f
ms.sourcegitcommit: 1aa0b172931d0f81db346452788c41dc4a6717b9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/22/2020
ms.locfileid: "48210256"
---
# <a name="build-a-teams-channel-tab"></a><span data-ttu-id="d611f-103">Erstellen einer Microsoft Teams-Kanal Registerkarte</span><span class="sxs-lookup"><span data-stu-id="d611f-103">Build a Teams channel tab</span></span>

<span data-ttu-id="d611f-104">In diesem Lernprogramm erstellen Sie eine einfache *Kanal Registerkarte*, eine Vollbildschirm-Inhaltsseite für einen Teamkanal oder Chat.</span><span class="sxs-lookup"><span data-stu-id="d611f-104">In this tutorial, you'll build a basic *channel tab*, a full-screen content page for a team channel or chat.</span></span> <span data-ttu-id="d611f-105">Im Gegensatz zu einer persönlichen Registerkarte können Benutzer einige Aspekte einer Kanal Registerkarte konfigurieren (beispielsweise benennen Sie die Registerkarte so um, dass Sie für Ihren Kanal sinnvoll ist).</span><span class="sxs-lookup"><span data-stu-id="d611f-105">Unlike a personal tab, users can configure some aspects of a channel tab (for example, rename the tab so it's meaningful to their channel).</span></span>

## <a name="before-you-begin"></a><span data-ttu-id="d611f-106">Bevor Sie beginnen</span><span class="sxs-lookup"><span data-stu-id="d611f-106">Before you begin</span></span>

<span data-ttu-id="d611f-107">Sie benötigen eine grundlegende ausgeführte App für den Einstieg.</span><span class="sxs-lookup"><span data-stu-id="d611f-107">You need a basic running app to get started.</span></span> <span data-ttu-id="d611f-108">Wenn Sie noch keinen haben, folgen Sie den [Anweisungen unter Build, und führen Sie Ihre Teams erste APP](../build-your-first-app/build-and-run.md)aus.</span><span class="sxs-lookup"><span data-stu-id="d611f-108">If you don't have one, follow the [build and run your Teams first app instructions](../build-your-first-app/build-and-run.md).</span></span> <span data-ttu-id="d611f-109">Wenn Sie Ihr App-Projekt erstellen, wählen Sie nur die **Kanal Registerkarte "Gruppe" oder "Teams"** aus.</span><span class="sxs-lookup"><span data-stu-id="d611f-109">When you create your app project, choose only the **Group or Teams channel tab** option.</span></span>

## <a name="your-assignment"></a><span data-ttu-id="d611f-110">Ihre Zuordnung</span><span class="sxs-lookup"><span data-stu-id="d611f-110">Your assignment</span></span>

<span data-ttu-id="d611f-111">Vor kurzem hat Ihre Organisation eine Registerkarte "Teams" mit Informationen zur Kontaktaufnahme mit wichtigen Funktionen (Help Desk, HR usw.) erstellt.</span><span class="sxs-lookup"><span data-stu-id="d611f-111">Not long ago, your organization created a Teams tab with information on how to contact important functions (help desk, HR, etc.).</span></span> <span data-ttu-id="d611f-112">Da die Registerkarte jedoch nur für den persönlichen Gebrauch verwendet wurde, muss jeder Benutzer die Registerkarte installieren, um ihn anzuzeigen, und die Annahme ist niedriger als erwartet.</span><span class="sxs-lookup"><span data-stu-id="d611f-112">However, since the tab was scoped only for personal use, each user must install the tab to see it and adoption is lower than expected.</span></span> <span data-ttu-id="d611f-113">In anderen Worten: zu viele Arbeitskräfte wissen immer noch nicht, wie Sie zum Helpdesk gelangen.</span><span class="sxs-lookup"><span data-stu-id="d611f-113">In other words, too many workers still don't know how to reach the help desk.</span></span>

<span data-ttu-id="d611f-114">Sie können diese Informationen leichter finden, indem Sie eine Kanal RegisterkarteErstellen, wodurch die Belastung der Installation einer APP durch alle Benutzer beseitigt wird.</span><span class="sxs-lookup"><span data-stu-id="d611f-114">You can make this information easier to find by building a channel tab, which will remove the burden of requiring everyone to install an app.</span></span> <span data-ttu-id="d611f-115">Stattdessen kann ein Benutzer die Registerkarte in einem Kanal oder Chat zum Nutzen einer ganzen Gruppe installieren.</span><span class="sxs-lookup"><span data-stu-id="d611f-115">Instead, one user can install the tab in a channel or chat for the benefit of an entire group.</span></span>

## <a name="what-youll-learn"></a><span data-ttu-id="d611f-116">Was Sie lernen</span><span class="sxs-lookup"><span data-stu-id="d611f-116">What you'll learn</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="d611f-117">Identifizieren einiger der Eigenschaften des App-Manifests und der für Kanal Registerkarten relevanten Gerüste</span><span class="sxs-lookup"><span data-stu-id="d611f-117">Identify some of the app manifest properties and scaffolding relevant to channel tabs</span></span>
> * <span data-ttu-id="d611f-118">Erstellen von Registerkarten Inhalten</span><span class="sxs-lookup"><span data-stu-id="d611f-118">Create tab content</span></span>
> * <span data-ttu-id="d611f-119">Erstellen von Inhalten für die Konfigurationsseite einer Registerkarte</span><span class="sxs-lookup"><span data-stu-id="d611f-119">Create content for a tab's configuration page</span></span>
> * <span data-ttu-id="d611f-120">Zulassen der Konfiguration und Installation einer Registerkarte</span><span class="sxs-lookup"><span data-stu-id="d611f-120">Allow a tab to be configured and installed</span></span>
> * <span data-ttu-id="d611f-121">Angeben eines vorgeschlagenen Registerkarten namens</span><span class="sxs-lookup"><span data-stu-id="d611f-121">Provide a suggested tab name</span></span>

## <a name="identify-relevant-app-project-components"></a><span data-ttu-id="d611f-122">Identifizieren relevanter App-Projektkomponenten</span><span class="sxs-lookup"><span data-stu-id="d611f-122">Identify relevant app project components</span></span>

<span data-ttu-id="d611f-123">Ein Großteil des App-Manifests und Gerüste werden automatisch eingerichtet, wenn Sie Ihr Projekt mit dem Teams-Toolkit erstellen.</span><span class="sxs-lookup"><span data-stu-id="d611f-123">Much of the app manifest and scaffolding are set up automatically when you create your project with the Teams Toolkit.</span></span> <span data-ttu-id="d611f-124">Lassen Sie uns die Hauptkomponenten zum Erstellen einer Kanal Registerkarte betrachten.</span><span class="sxs-lookup"><span data-stu-id="d611f-124">Let's look at the main components for building a channel tab.</span></span>

### <a name="app-manifest"></a><span data-ttu-id="d611f-125">App-Manifest</span><span class="sxs-lookup"><span data-stu-id="d611f-125">App manifest</span></span>

<span data-ttu-id="d611f-126">Der folgende Ausschnitt aus dem App-Manifest zeigt [`configurableTabs`](../resources/schema/manifest-schema.md#configurabletabs) , der die Eigenschaften und Standardwerte enthält, die für Kanal Registerkarten relevant sind.</span><span class="sxs-lookup"><span data-stu-id="d611f-126">The following snippet from the app manifest shows [`configurableTabs`](../resources/schema/manifest-schema.md#configurabletabs), which includes the properties and default values relevant to channel tabs.</span></span>

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

* <span data-ttu-id="d611f-127">`configurationUrl`: Die Host-URL für Ihre Registerkarten-Konfigurationsseite (muss https sein).</span><span class="sxs-lookup"><span data-stu-id="d611f-127">`configurationUrl`: The host URL for your tab configuration page (must be HTTPS).</span></span>
* <span data-ttu-id="d611f-128">`canUpdateConfiguration`: Wenn Sie auf festgelegt `true` ist, können Benutzer die Registerkarteneinstellungen ändern, die Registerkarte umbenennen oder aus einem Kanal oder Chat entfernen.</span><span class="sxs-lookup"><span data-stu-id="d611f-128">`canUpdateConfiguration`: If set to `true`, users can change tab settings, rename the tab, or remove it from a channel or chat.</span></span>
* <span data-ttu-id="d611f-129">`scopes`: Gibt an, ob Benutzer die app in Kanälen ( `team` ) und Chats installieren können ( `groupchat` ).</span><span class="sxs-lookup"><span data-stu-id="d611f-129">`scopes`: Specifies if users can install the app in channels (`team`) and chats (`groupchat`).</span></span> <span data-ttu-id="d611f-130">Mindestens ein Wert ist erforderlich.</span><span class="sxs-lookup"><span data-stu-id="d611f-130">At least one value is required.</span></span>

### <a name="app-scaffolding"></a><span data-ttu-id="d611f-131">App-Gerüste</span><span class="sxs-lookup"><span data-stu-id="d611f-131">App scaffolding</span></span>

<span data-ttu-id="d611f-132">Das App-Gerüst stellt eine `TabConfig.js` Datei bereit, die sich im `src/components` Verzeichnis des Projekts befindet, um die Konfigurationsseite der Registerkarte zu rendern (Weitere Informationen dazu in Kürze).</span><span class="sxs-lookup"><span data-stu-id="d611f-132">The app scaffolding provides a `TabConfig.js` file, located in the `src/components` directory of your project, for rendering your tab's configuration page (more on this soon).</span></span>

## <a name="create-your-tab-content"></a><span data-ttu-id="d611f-133">Erstellen des Registerkarteninhalts</span><span class="sxs-lookup"><span data-stu-id="d611f-133">Create your tab content</span></span>

<span data-ttu-id="d611f-134">Öffnen Sie das App-Manifest ( `manifest.json` ) im `.publish` Verzeichnis, und legen Sie die folgenden Eigenschaften in fest [`staticTabs`](../resources/schema/manifest-schema.md#statictabs) , die die Inhaltsseite ihrer Registerkarte definiert.</span><span class="sxs-lookup"><span data-stu-id="d611f-134">Open the app manifest (`manifest.json`) in the `.publish` directory and set the following properties in [`staticTabs`](../resources/schema/manifest-schema.md#statictabs), which defines your tab's content page.</span></span>

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

<span data-ttu-id="d611f-135">Kopieren Sie den folgenden Codeausschnitt, und aktualisieren Sie ihn mit Informationen, die für Ihre Organisation relevant sind, oder verwenden Sie, um der Zeit Willen, den Code wie es ist.</span><span class="sxs-lookup"><span data-stu-id="d611f-135">Copy and update the following snippet with information that's relevant to your organization or, for the sake of time, use the code as is.</span></span>

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

<span data-ttu-id="d611f-136">Wechseln Sie zum `src/components` Verzeichnis, und öffnen Sie `Tab.js` .</span><span class="sxs-lookup"><span data-stu-id="d611f-136">Go to the `src/components` directory and open `Tab.js`.</span></span> <span data-ttu-id="d611f-137">Suchen `render()` Sie die-Funktion, und fügen Sie den Inhalt in das Bild ein `return()` (siehe Abbildung).</span><span class="sxs-lookup"><span data-stu-id="d611f-137">Locate the `render()` function and paste your content inside `return()` (as shown).</span></span>

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

<span data-ttu-id="d611f-138">Fügen Sie die folgende Regel hinzu, `App.css` damit die e-Mail-Links leichter lesbar sind, unabhängig davon, welches Design verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="d611f-138">Add the following rule to `App.css` so the email links are easier to read no matter which theme is used.</span></span>

```CSS
a {
  color: inherit;
}
```

## <a name="create-your-tab-configuration-page"></a><span data-ttu-id="d611f-139">Erstellen der Seite für die Registerkartenkonfiguration</span><span class="sxs-lookup"><span data-stu-id="d611f-139">Create your tab configuration page</span></span>

<span data-ttu-id="d611f-140">Jede Kanal Registerkarte verfügt über eine Konfigurationsseite, eine modale mit mindestens einer Setup Option, die bei der Installation der App angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="d611f-140">Every channel tab has a configuration page, a modal with at least one setup option that displays when installing the app.</span></span> <span data-ttu-id="d611f-141">Auf der Konfigurationsseite werden Benutzer standardmäßig gefragt, ob Sie den Kanal oder den Chat benachrichtigen möchten, wenn die Registerkarte installiert ist.</span><span class="sxs-lookup"><span data-stu-id="d611f-141">The configuration page by default asks users if they want to notify the channel or chat when the tab is installed.</span></span>

<span data-ttu-id="d611f-142">Fügen Sie der Konfigurationsseite einige Inhalte hinzu.</span><span class="sxs-lookup"><span data-stu-id="d611f-142">Add some content to your configuration page.</span></span> <span data-ttu-id="d611f-143">Wechseln Sie zum Verzeichnis Ihres Projekts `src/components` , öffnen Sie `TabConfig.js` und fügen Sie einige Inhalte in ein `return()` (siehe Abbildung).</span><span class="sxs-lookup"><span data-stu-id="d611f-143">Go to your project's `src/components` directory, open `TabConfig.js`, and insert some content inside `return()` (as shown).</span></span>

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
> <span data-ttu-id="d611f-144">Geben Sie mindestens einige kurze Informationen zu Ihrer APP auf dieser Seite, da dies das erste Mal sein kann, dass Benutzer davon erfahren.</span><span class="sxs-lookup"><span data-stu-id="d611f-144">At minimum, provide some brief information about your app on this page since this may be the first time users are learning about it.</span></span> <span data-ttu-id="d611f-145">Sie können auch benutzerdefinierte Konfigurationsoptionen oder einen [Authentifizierungs Workflow](../tabs/how-to/authentication/auth-aad-sso.md)einschließen, was bei Registerkarten-Konfigurationsseiten üblich ist.</span><span class="sxs-lookup"><span data-stu-id="d611f-145">You also could include custom configuration options or an [authentication workflow](../tabs/how-to/authentication/auth-aad-sso.md), which is common on tab configuration pages.</span></span>

## <a name="allow-the-tab-to-be-configured-and-installed"></a><span data-ttu-id="d611f-146">Konfigurieren und Installieren der Registerkarte zulassen</span><span class="sxs-lookup"><span data-stu-id="d611f-146">Allow the tab to be configured and installed</span></span>

<span data-ttu-id="d611f-147">Damit Benutzer die Kanal Registerkarte erfolgreich konfigurieren und installieren können, müssen Sie die Host-URL hinzufügen, die Sie beim [Erstellen und durchführen ihrer ersten App](../build-your-first-app/build-and-run.md) für die Komponente "Konfigurationsseite" eingerichtet haben.</span><span class="sxs-lookup"><span data-stu-id="d611f-147">For users to successfully configure and install the channel tab, you must add the host URL you set up when [creating and running your first app](../build-your-first-app/build-and-run.md) to the configuration page component.</span></span>

<span data-ttu-id="d611f-148">Wechseln Sie zu `TabConfig.js` und suchen Sie `microsoftTeams.settings.setSettings` .</span><span class="sxs-lookup"><span data-stu-id="d611f-148">Go to `TabConfig.js` and locate `microsoftTeams.settings.setSettings`.</span></span> <span data-ttu-id="d611f-149">`"contentUrl"`Ersetzen Sie dabei den `localhost:3000` Teil der URL durch die Domäne, in der Sie den Registerkarteninhalt hosten (siehe Abbildung).</span><span class="sxs-lookup"><span data-stu-id="d611f-149">For `"contentUrl"`, replace the `localhost:3000` part of the URL with the domain where you're hosting the tab content (as shown).</span></span>

```JavaScript
microsoftTeams.settings.setSettings({
  "contentUrl": "https://<MY_HOST_DOMAIN>/tab"
});
```

<span data-ttu-id="d611f-150">Stellen Sie außerdem sicher, dass `microsoftTeams.settings.setValidityState(true);` .</span><span class="sxs-lookup"><span data-stu-id="d611f-150">Also, make sure that `microsoftTeams.settings.setValidityState(true);`.</span></span> <span data-ttu-id="d611f-151">Standardmäßig ist `false` die Schaltfläche **Speichern** auf der Konfigurationsseite jedoch deaktiviert, wenn Sie auf festgelegt ist.</span><span class="sxs-lookup"><span data-stu-id="d611f-151">It is by default, but if set to `false`, the **Save** button is disabled on the configuration page.</span></span>

## <a name="provide-a-suggested-tab-name"></a><span data-ttu-id="d611f-152">Angeben eines vorgeschlagenen Registerkarten namens</span><span class="sxs-lookup"><span data-stu-id="d611f-152">Provide a suggested tab name</span></span>

<span data-ttu-id="d611f-153">Wenn Sie eine Registerkarte zur persönlichen Verwendung installieren, ist der Anzeigename die `name` Eigenschaft im `staticTabs` Teil des App-Manifests (beispielsweise " **meine Kontakte**").</span><span class="sxs-lookup"><span data-stu-id="d611f-153">When you install a tab for personal use, the display name is the `name` property in the `staticTabs` portion of of the app manifest (for example, **My Contacts**).</span></span> <span data-ttu-id="d611f-154">Wenn Sie eine Kanal Registerkarte installieren, wird standardmäßig der App-Name angezeigt (beispielsweise **First-App**).</span><span class="sxs-lookup"><span data-stu-id="d611f-154">When you install a channel tab, by default the app name displays (for example, **first-app**).</span></span>

<span data-ttu-id="d611f-155">Dies ist möglicherweise in Ordnung, je nachdem, was Sie Ihre APP aufrufen, aber Sie möchten möglicherweise einen Namen angeben, der im Kontext der Gruppenzusammenarbeit sinnvoller ist (beispielsweise **Team Kontakte**).</span><span class="sxs-lookup"><span data-stu-id="d611f-155">This may be fine depending on what you call your app, but you may want to provide a name that makes more sense in the context of group collaboration (for example, **Team Contacts**).</span></span>

<span data-ttu-id="d611f-156">`TabConfig.js`Wechseln Sie in zu zurück zu `microsoftTeams.settings.setSettings` .</span><span class="sxs-lookup"><span data-stu-id="d611f-156">In `TabConfig.js`, go back to `microsoftTeams.settings.setSettings`.</span></span> <span data-ttu-id="d611f-157">Fügen `suggestedDisplayName` Sie die Eigenschaft mit dem Registerkartennamen hinzu, den Sie standardmäßig anzeigen möchten (siehe Abbildung).</span><span class="sxs-lookup"><span data-stu-id="d611f-157">Add the `suggestedDisplayName` property with the tab name you want to display by default (as shown).</span></span> <span data-ttu-id="d611f-158">Verwenden Sie den angegebenen Namen, oder erstellen Sie einen eigenen.</span><span class="sxs-lookup"><span data-stu-id="d611f-158">Use the provided name or create your own.</span></span> <span data-ttu-id="d611f-159">Denken Sie daran, dass Sie in dem Manifest Benutzern erlauben, den Namen zu ändern, wenn Sie möchten.</span><span class="sxs-lookup"><span data-stu-id="d611f-159">Remember, in the manifest you're allowing users to change the name if they want.</span></span>

```JavaScript
microsoftTeams.settings.setSettings({
  "contentUrl": "https://<MY_HOST_DOMAIN>/tab",
  "suggestedDisplayName": "Team Contacts"
});
```

## <a name="view-the-channel-tab"></a><span data-ttu-id="d611f-160">Anzeigen der Kanal Registerkarte</span><span class="sxs-lookup"><span data-stu-id="d611f-160">View the channel tab</span></span>

<span data-ttu-id="d611f-161">Um die Konfigurations-und Inhaltsseiten Ihrer Kanal Registerkarte anzuzeigen, müssen Sie Sie in einem Kanal oder Chat installieren.</span><span class="sxs-lookup"><span data-stu-id="d611f-161">To see your channel tab's configuration and content pages, you must install it in a channel or chat.</span></span>

1. <span data-ttu-id="d611f-162">Wählen Sie im Microsoft Teams-Client **apps**aus.</span><span class="sxs-lookup"><span data-stu-id="d611f-162">In the Teams client, select **Apps**.</span></span>
1. <span data-ttu-id="d611f-163">Wählen Sie **Upload a custom app** aus, und wählen Sie Ihre apps aus `Development.zip` .</span><span class="sxs-lookup"><span data-stu-id="d611f-163">Select **Upload a custom app** and choose your app's `Development.zip`.</span></span>
1. <span data-ttu-id="d611f-164">Wählen Sie **zu einem Team hinzufügen** oder **zu einem Chat hinzufügen** aus, und suchen Sie nach einem Kanal oder Chat, den Sie zum Testen verwenden können.</span><span class="sxs-lookup"><span data-stu-id="d611f-164">Choose **Add to a team** or **Add to a chat** and locate a channel or chat you can use for testing.</span></span>
1. <span data-ttu-id="d611f-165">Wählen Sie **Einrichten einer Registerkarte**aus. Die Konfigurationsseite wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="d611f-165">Select **Set up a tab**. The configuration page displays.</span></span><br/>
   :::image type="content" source="../assets/images/tabs/channel-tab-tutorial-content.png" alt-text="Screenshot einer Kanal Registerkarten-Konfigurationsseite.":::
1. <span data-ttu-id="d611f-167">Wählen Sie **Speichern** aus, um die Registerkarte zu konfigurieren. Der Inhalt wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="d611f-167">Select **Save** to configure the tab. The content displays.</span></span><br/>
   :::image type="content" source="../assets/images/tabs/channel-tab-tutorial-content-installed.png" alt-text="Screenshot einer Kanal Registerkarte mit statischer Inhaltsansicht.":::

## <a name="well-done"></a><span data-ttu-id="d611f-169">Gut gemacht</span><span class="sxs-lookup"><span data-stu-id="d611f-169">Well done</span></span>

<span data-ttu-id="d611f-170">Herzlichen Glückwunsch!</span><span class="sxs-lookup"><span data-stu-id="d611f-170">Congratulations!</span></span> <span data-ttu-id="d611f-171">Sie verfügen über eine Teams-App mit einer Kanal Registerkarte, um nützliche Inhalte in Kanälen und Chats anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="d611f-171">You have a Teams app with a channel tab for displaying useful content in channels and chats.</span></span>

## <a name="learn-more"></a><span data-ttu-id="d611f-172">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="d611f-172">Learn more</span></span>

* <span data-ttu-id="d611f-173">[Authentifizieren von Registerkarten Benutzern mit SSO](../tabs/how-to/authentication/auth-aad-sso.md): Wenn Sie nur autorisierte Benutzer Ihrer Registerkarte anzeigen möchten, richten Sie einmaliges Anmelden (Single Sign-on, SSO) über Azure Active Directory (AD) ein.</span><span class="sxs-lookup"><span data-stu-id="d611f-173">[Authenticate tab users with SSO](../tabs/how-to/authentication/auth-aad-sso.md): If you only want authorized users viewing your tab, set up single sign-on (SSO) through Azure Active Directory (AD).</span></span>
* <span data-ttu-id="d611f-174">[Einbetten von Inhalten aus einer vorhandenen Web-App oder Webseite](../tabs/how-to/add-tab.md#tab-requirements): Wir haben gezeigt, wie Sie neue Inhalte für eine persönliche RegisterkarteErstellen, aber Sie können auch Inhalte aus einer externen URL laden.</span><span class="sxs-lookup"><span data-stu-id="d611f-174">[Embed content from an existing web app or webpage](../tabs/how-to/add-tab.md#tab-requirements): We showed you how to create new content for a personal tab, but you can also load content from an external URL.</span></span>
* <span data-ttu-id="d611f-175">[Erstellen Sie eine nahtlose Benutzeroberfläche für Ihre Registerkarte](../tabs/design/tabs.md): Lesen Sie die empfohlenen Richtlinien für das Entwerfen von Microsoft Teams-Registerkarten.</span><span class="sxs-lookup"><span data-stu-id="d611f-175">[Create a seamless experience for your tab](../tabs/design/tabs.md): See the recommended guidelines for designing Teams tabs.</span></span>
* <span data-ttu-id="d611f-176">[Erstellen von Registerkarten für Mobilgeräte](../tabs/design/tabs-mobile.md): Hier erfahren Sie, wie Sie Registerkarten für Telefone und Tablets entwickeln.</span><span class="sxs-lookup"><span data-stu-id="d611f-176">[Build tabs for mobile](../tabs/design/tabs-mobile.md): Understand how to develop tabs for phones and tablets.</span></span>
* [<span data-ttu-id="d611f-177">Erstellen einer Registerkarte ohne Toolkit</span><span class="sxs-lookup"><span data-stu-id="d611f-177">Create a tab without the toolkit</span></span>](../tabs/how-to/add-tab.md)

## <a name="next-lesson"></a><span data-ttu-id="d611f-178">Nächste Lektion</span><span class="sxs-lookup"><span data-stu-id="d611f-178">Next lesson</span></span>

<span data-ttu-id="d611f-179">Sie wissen, wie Sie eine Registerkarte für die Zusammenarbeit erstellen.</span><span class="sxs-lookup"><span data-stu-id="d611f-179">You know how to build a tab for collaboration.</span></span> <span data-ttu-id="d611f-180">Möchten Sie versuchen, eine andere Art von Teams-APP zu erstellen?</span><span class="sxs-lookup"><span data-stu-id="d611f-180">Want to try building a different kind of Teams app?</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="d611f-181">Erstellen eines bot</span><span class="sxs-lookup"><span data-stu-id="d611f-181">Build a bot</span></span>](../build-your-first-app/build-bot.md)
