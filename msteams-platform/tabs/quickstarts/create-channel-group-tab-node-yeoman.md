---
title: Erstellen eines benutzerdefinierten Kanals und einer gruppenspezifischen Registerkarte mit Node.js und dem Yeoman-Generator für Microsoft Teams
author: surbhigupta
description: Eine Schnellstartanleitung zum Erstellen einer Kanal- und Gruppenregisterkarte mit dem Yeoman-Generator für Microsoft Teams.
localization_priority: Normal
ms.topic: quickstart
ms.author: lajanuar
ms.openlocfilehash: 6b3b5e513f91afae47364c37eb2b037a13438d35
ms.sourcegitcommit: 623d81eb079d1842813265746a5fe0fe6311b196
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/22/2021
ms.locfileid: "53069107"
---
# <a name="create-a-custom-channel-and-group-tab-using-nodejs-and-the-yeoman-generator-for-microsoft-teams"></a><span data-ttu-id="60ab9-103">Erstellen einer benutzerdefinierten Kanal- und Gruppenregisterkarte mit Node.js und dem Yeoman-Generator für Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="60ab9-103">Create a custom channel and group tab using Node.js and the Yeoman Generator for Microsoft Teams</span></span>

>[!NOTE]
><span data-ttu-id="60ab9-104">Diese Schnellstartanleitung folgt den Schritten, die im Wiki ["Erstellen Ihrer ersten Microsoft Teams App"](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App) im Microsoft OfficeDev-GitHub-Repository beschrieben sind.</span><span class="sxs-lookup"><span data-stu-id="60ab9-104">This quickstart follows the steps outlined in the [Build Your First Microsoft Teams App](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App) Wiki found in the Microsoft OfficeDev GitHub repository.</span></span>

<span data-ttu-id="60ab9-105">In dieser Schnellstartanleitung werden wir schrittweise durch das Erstellen eines benutzerdefinierten Kanals und einer Gruppenregisterkarte mithilfe des [Teams Yeoman-Generators geführt.](https://github.com/OfficeDev/generator-teams/)</span><span class="sxs-lookup"><span data-stu-id="60ab9-105">In this quickstart we'll walk-through creating a custom channel and group tab using the [Teams Yeoman generator](https://github.com/OfficeDev/generator-teams/).</span></span>

[!INCLUDE [node-js-yeoman-prereq](~/includes/tabs/node-js-yeoman-prereq.md)]

<span data-ttu-id="60ab9-106">**Möchten Sie eine konfigurierbare oder statische Registerkarte erstellen?**</span><span class="sxs-lookup"><span data-stu-id="60ab9-106">**Do you want to create a configurable or static tab?**</span></span>

<span data-ttu-id="60ab9-107">Verwenden Sie die Pfeiltasten, um die konfigurierbare Registerkarte auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="60ab9-107">Use the arrow keys to select configurable tab.</span></span>

<span data-ttu-id="60ab9-108">**Welche Bereiche möchten Sie für Ihre Registerkarte verwenden?**</span><span class="sxs-lookup"><span data-stu-id="60ab9-108">**What scopes do you intend to use for your Tab?**</span></span>

<span data-ttu-id="60ab9-109">Sie können ein Team und/oder einen Gruppenchat auswählen</span><span class="sxs-lookup"><span data-stu-id="60ab9-109">You can select a Team and/or a group chat</span></span>

<span data-ttu-id="60ab9-110">**Soll diese Registerkarte in SharePoint Online verfügbar sein? (J/n)**</span><span class="sxs-lookup"><span data-stu-id="60ab9-110">**Do you want this tab to be available in SharePoint Online? (Y/n)**</span></span> 

<span data-ttu-id="60ab9-111">Wählen Sie **n** aus.</span><span class="sxs-lookup"><span data-stu-id="60ab9-111">Select **n**.</span></span>

>[!IMPORTANT]
><span data-ttu-id="60ab9-112">The path component **yourDefaultTabNameTab**, referenced in this quickstart, is the value that you entered in the generator for **Default Tab Name** plus the word **Tab**.</span><span class="sxs-lookup"><span data-stu-id="60ab9-112">The path component **yourDefaultTabNameTab**, referenced in this quickstart, is the value that you entered in the generator for **Default Tab Name** plus the word **Tab**.</span></span>
>
><span data-ttu-id="60ab9-113">Beispiel: DefaultTabName: **MyTab**  =>  **/MyTabTab/**</span><span class="sxs-lookup"><span data-stu-id="60ab9-113">For example: DefaultTabName: **MyTab** => **/MyTabTab/**</span></span>

<span data-ttu-id="60ab9-114">Navigieren Sie in Ihrem Projektverzeichnis zu Folgendem:</span><span class="sxs-lookup"><span data-stu-id="60ab9-114">In your project directory, navigate to the following:</span></span>

```bash
./src/app/scripts/<yourDefaultTabNameTab>/<yourDefaultTabNameTab>.tsx
```

<span data-ttu-id="60ab9-115">Hier finden Sie Ihre Registerkartenlogik.</span><span class="sxs-lookup"><span data-stu-id="60ab9-115">That is where you'll find your tab logic.</span></span> <span data-ttu-id="60ab9-116">Suchen Sie die Methode, und fügen Sie oben im `render()` Containercode das folgende Tag und den folgenden `<div>` Inhalt `<PanelBody>` hinzu:</span><span class="sxs-lookup"><span data-stu-id="60ab9-116">Locate the `render()` method and add the following `<div>` tag and content to the top of the `<PanelBody>` container code:</span></span>

```html
    <PanelBody>
        <div style={styles.section}>
            Hello World! Yo Teams rocks!
        </div>
    </PanelBody>
```

<span data-ttu-id="60ab9-117">Stellen Sie sicher, dass Sie die aktualisierte Datei speichern.</span><span class="sxs-lookup"><span data-stu-id="60ab9-117">Make sure to save the updated file.</span></span>

## <a name="build-and-run-your-application"></a><span data-ttu-id="60ab9-118">Erstellen und Ausführen ihrer Anwendung</span><span class="sxs-lookup"><span data-stu-id="60ab9-118">Build and Run Your Application</span></span>

<span data-ttu-id="60ab9-119">Öffnen Sie eine Eingabeaufforderung in Ihrem Projektverzeichnis, um die nächsten Aufgaben auszuführen.</span><span class="sxs-lookup"><span data-stu-id="60ab9-119">Open a command prompt in your project directory to complete the next tasks.</span></span>

[!INCLUDE [node-js-yeoman-gulp-tasks](~/includes/tabs/node-js-yeoman-gulp-tasks.md)]

<span data-ttu-id="60ab9-120">Wechseln Sie zum Anzeigen der Registerkartenkonfigurationsseite zu `https://localhost:3007/<yourDefaultAppNameTab>/config.html` .</span><span class="sxs-lookup"><span data-stu-id="60ab9-120">To view your tab configuration page go to `https://localhost:3007/<yourDefaultAppNameTab>/config.html`.</span></span> <span data-ttu-id="60ab9-121">Folgendes sollte angezeigt werden:</span><span class="sxs-lookup"><span data-stu-id="60ab9-121">You should see the following:</span></span>

![Screenshot der Konfigurationsseite](~/assets/images/tab-images/configurationPage.png)

## <a name="establish-a-secure-tunnel-to-your-tab"></a><span data-ttu-id="60ab9-123">Einrichten eines sicheren Tunnels zu Ihrer Registerkarte</span><span class="sxs-lookup"><span data-stu-id="60ab9-123">Establish a secure tunnel to your tab</span></span>

<span data-ttu-id="60ab9-124">Microsoft Teams ist ein vollständig cloudbasiertes Produkt und erfordert, dass Ihre Registerkarteninhalte über HTTPS-Endpunkte aus der Cloud verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="60ab9-124">Microsoft Teams is an entirely cloud-based product and requires that your tab content be available from the cloud using HTTPS endpoints.</span></span> <span data-ttu-id="60ab9-125">Teams lokales Hosting nicht zulässt, müssen Sie daher Ihre Registerkarte entweder über eine öffentliche URL veröffentlichen oder einen Proxy verwenden, der Ihren lokalen Port für eine internetbasierte URL verfügbar macht.</span><span class="sxs-lookup"><span data-stu-id="60ab9-125">Teams doesn't allow local hosting, therefore, you need to either publish your tab to a public URL or use a proxy that will expose your local port to an internet-facing URL.</span></span>

<span data-ttu-id="60ab9-126">Zum Testen der Registerkartenerweiterung verwenden Sie [ngrok,](https://ngrok.com/docs)das in diese Anwendung integriert ist.</span><span class="sxs-lookup"><span data-stu-id="60ab9-126">To test your tab extension, you'll use [ngrok](https://ngrok.com/docs), which is built into this application.</span></span> <span data-ttu-id="60ab9-127">Ngrok ist ein Reverseproxysoftwaretool, das einen Tunnel zu den öffentlich verfügbaren HTTPS-Endpunkten Ihres lokal ausgeführten Webservers erstellt.</span><span class="sxs-lookup"><span data-stu-id="60ab9-127">Ngrok is a reverse proxy software tool that will create a tunnel to your locally running web server's publicly-available HTTPS endpoints.</span></span> <span data-ttu-id="60ab9-128">Die Webendpunkte Ihres Servers sind während der aktuellen Sitzung auf Ihrem lokalen Computer verfügbar.</span><span class="sxs-lookup"><span data-stu-id="60ab9-128">Your server's web endpoints will be available during the current session on your local machine.</span></span> <span data-ttu-id="60ab9-129">Wenn der Computer heruntergefahren wird oder in den Ruhezustand wechselt, ist der Dienst nicht mehr verfügbar.</span><span class="sxs-lookup"><span data-stu-id="60ab9-129">When the machine is shut down or goes to sleep the service will no longer be available.</span></span>

<span data-ttu-id="60ab9-130">Beenden Sie an der Eingabeaufforderung "localhost", und geben Sie Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="60ab9-130">In your command prompt, exit localhost and enter the following:</span></span>

```bash
gulp ngrok-serve
```

> [!IMPORTANT]
> <span data-ttu-id="60ab9-131">Nachdem Ihre Registerkarte in Microsoft Teams hochgeladen und erfolgreich gespeichert wurde, können Sie sie im Registerkartenkatalog anzeigen, sie der Registerkartenleiste hinzufügen und damit interagieren, bis Ihre ngrok-Tunnelsitzung endet.</span><span class="sxs-lookup"><span data-stu-id="60ab9-131">After your tab has been uploaded to Microsoft teams and successfully saved, you can view it in the tabs gallery, add it to the tabs bar, and interact with it until your ngrok tunnel session ends.</span></span> <span data-ttu-id="60ab9-132">Wenn Sie Ihre ngrok-Sitzung neu starten, müssen Sie Ihre App mit der neuen URL aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="60ab9-132">If you restart your ngrok session, you'll need to update your app with the new URL.</span></span>

## <a name="upload-your-application-to-teams"></a><span data-ttu-id="60ab9-133">Hochladen Der Anwendung Teams</span><span class="sxs-lookup"><span data-stu-id="60ab9-133">Upload your application to Teams</span></span>

- <span data-ttu-id="60ab9-134">Öffnen Sie den Microsoft Teams Client.</span><span class="sxs-lookup"><span data-stu-id="60ab9-134">Open the Microsoft Teams client.</span></span> <span data-ttu-id="60ab9-135">Wenn Sie die [webbasierte Version](https://teams.microsoft.com) verwenden, können Sie Ihren Front-End-Code mithilfe der [Entwicklertools](~/tabs/how-to/developer-tools.md)Ihres Browsers überprüfen.</span><span class="sxs-lookup"><span data-stu-id="60ab9-135">If you use the [web based version](https://teams.microsoft.com) you can inspect your front-end code using your browser's [developer tools](~/tabs/how-to/developer-tools.md).</span></span>
- <span data-ttu-id="60ab9-136">Wählen Sie im Bereich *"YourTeams"* auf der linken Seite das Menü neben dem Team aus, `...` mit dem Sie Ihre Registerkarte testen, und wählen Sie **"Team verwalten"** aus.</span><span class="sxs-lookup"><span data-stu-id="60ab9-136">In the *YourTeams* panel on the left, select the `...` menu next to the team that you're using to test your tab and choose **Manage team**.</span></span>
- <span data-ttu-id="60ab9-137">Wählen Sie in der Registerkartenleiste im Hauptbereich **Apps** aus, und wählen Sie **Hochladen eine benutzerdefinierte App** in der unteren rechten Ecke der Seite aus.</span><span class="sxs-lookup"><span data-stu-id="60ab9-137">In the main panel select **Apps** from the tab bar and choose **Upload a custom app** located in the lower right-hand corner of the page.</span></span>
- <span data-ttu-id="60ab9-138">Öffnen Sie Ihr Projektverzeichnis, navigieren Sie zum **Ordner "./package",** wählen Sie den ZIP-Ordner des App-Pakets aus, und wählen Sie **"Öffnen"** aus.</span><span class="sxs-lookup"><span data-stu-id="60ab9-138">Open your project directory, browse to the **./package** folder, select the app package zip folder and choose **Open**.</span></span> <span data-ttu-id="60ab9-139">Ihre Registerkarte wird in Teams hochgeladen.</span><span class="sxs-lookup"><span data-stu-id="60ab9-139">Your tab will upload into Teams.</span></span>
- <span data-ttu-id="60ab9-140">Kehren Sie zu Ihrem Team zurück, wählen Sie den Kanal aus, in dem Sie die Registerkarte anzeigen möchten, wählen Sie ➕ aus der Registerkartenleiste aus, und wählen Sie Ihre Registerkarte im Katalog aus.</span><span class="sxs-lookup"><span data-stu-id="60ab9-140">Return to your team, choose the channel where you would like to display the tab, select ➕ from the tab bar, and choose your tab from the gallery.</span></span>
- <span data-ttu-id="60ab9-141">Befolgen Sie die Anweisungen zum Hinzufügen einer Registerkarte. Beachten Sie, dass ein benutzerdefiniertes Konfigurationsdialogfeld für ihre Kanal-/Gruppenregisterkarte vorhanden ist.</span><span class="sxs-lookup"><span data-stu-id="60ab9-141">Follow the directions for adding a tab. Note that there's a custom configuration dialog for your channel/group tab.</span></span>
- <span data-ttu-id="60ab9-142">Wählen Sie **"Speichern"** aus, und Ihre Registerkarte wird der Registerkartenleiste des Kanals hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="60ab9-142">Select **Save** and your tab will be added to the channel's tab bar.</span></span>

## <a name="next-step"></a><span data-ttu-id="60ab9-143">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="60ab9-143">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="60ab9-144">Erstellen eines benutzerdefinierten Kanals und einer Gruppenregisterkarte mit ASP.NETCore</span><span class="sxs-lookup"><span data-stu-id="60ab9-144">Create a Custom Channel and Group Tab with ASP.NETCore</span></span>](~/tabs/quickstarts/create-channel-group-tab-dotnet-core.md)
