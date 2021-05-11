---
title: Erstellen Sie einen benutzerdefinierten Kanal und eine gruppe Registerkarte mit Node.js und dem Yeoman Generator für Microsoft Teams
author: laujan
description: Eine Schnellstartanleitung zum Erstellen eines Kanals und einer Gruppenregisterkarte mit dem Yeoman Generator für Microsoft Teams.
localization_priority: Normal
ms.topic: quickstart
ms.author: lajanuar
ms.openlocfilehash: 962a558014a3bc84010860082df6891bb48c7715
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020303"
---
# <a name="create-a-custom-channel-and-group-tab-with-nodejs-and-the-yeoman-generator-for-microsoft-teams"></a><span data-ttu-id="d880e-103">Erstellen Sie einen benutzerdefinierten Kanal und eine Node.js mit Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="d880e-103">Create a custom channel and group tab with Node.js and the Yeoman Generator for Microsoft Teams</span></span>

>[!NOTE]
><span data-ttu-id="d880e-104">Dieser Schnellstart folgt den Schritten, die im Wiki zum Erstellen der ersten [Microsoft Teams-App](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App) im Microsoft OfficeDev-Repository GitHub sind.</span><span class="sxs-lookup"><span data-stu-id="d880e-104">This quickstart follows the steps outlined in the [Build Your First Microsoft Teams App](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App) Wiki found in the Microsoft OfficeDev GitHub repository.</span></span>

<span data-ttu-id="d880e-105">In dieser Schnellstartanleitung wird das Erstellen eines benutzerdefinierten Kanals und einer Registerkarte für Gruppen mithilfe des Teams [Yeoman-Generators durchgef?llt.](https://github.com/OfficeDev/generator-teams/)</span><span class="sxs-lookup"><span data-stu-id="d880e-105">In this quickstart we'll walk-through creating a custom channel and group tab using the [Teams Yeoman generator](https://github.com/OfficeDev/generator-teams/).</span></span>

[!INCLUDE [node-js-yeoman-prereq](~/includes/tabs/node-js-yeoman-prereq.md)]

<span data-ttu-id="d880e-106">**Möchten Sie eine konfigurierbare oder statische Registerkarte erstellen?**</span><span class="sxs-lookup"><span data-stu-id="d880e-106">**Do you want to create a configurable or static tab?**</span></span>

<span data-ttu-id="d880e-107">Verwenden Sie die Pfeiltasten, um die konfigurierbare Registerkarte auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="d880e-107">Use the arrow keys to select configurable tab.</span></span>

<span data-ttu-id="d880e-108">**Welche Bereiche möchten Sie für Ihre Registerkarte verwenden?**</span><span class="sxs-lookup"><span data-stu-id="d880e-108">**What scopes do you intend to use for your Tab?**</span></span>

<span data-ttu-id="d880e-109">Sie können einen Team- und/oder Gruppenchat auswählen</span><span class="sxs-lookup"><span data-stu-id="d880e-109">You can select a Team and/or a group chat</span></span>

<span data-ttu-id="d880e-110">**Möchten Sie, dass diese Registerkarte in SharePoint Online verfügbar ist? (Y/n)**</span><span class="sxs-lookup"><span data-stu-id="d880e-110">**Do you want this tab to be available in SharePoint Online? (Y/n)**</span></span> 

<span data-ttu-id="d880e-111">Wählen **Sie n** aus.</span><span class="sxs-lookup"><span data-stu-id="d880e-111">Select **n**.</span></span>

>[!IMPORTANT]
><span data-ttu-id="d880e-112">Die Pfadkomponente **yourDefaultTabNameTab**, auf die in diesem Schnellstart verwiesen wird, ist der Wert, den Sie im Generator für **Standardregisterkartenname** plus das Wort **Tab eingegeben haben.**</span><span class="sxs-lookup"><span data-stu-id="d880e-112">The path component **yourDefaultTabNameTab**, referenced in this quickstart, is the value that you entered in the generator for **Default Tab Name** plus the word **Tab**.</span></span>
>
><span data-ttu-id="d880e-113">Beispiel: DefaultTabName: **MyTab**  =>  **/MyTabTab/**</span><span class="sxs-lookup"><span data-stu-id="d880e-113">For example: DefaultTabName: **MyTab** => **/MyTabTab/**</span></span>

<span data-ttu-id="d880e-114">Navigieren Sie in Ihrem Projektverzeichnis zu folgendem:</span><span class="sxs-lookup"><span data-stu-id="d880e-114">In your project directory, navigate to the following:</span></span>

```bash
./src/app/scripts/<yourDefaultTabNameTab>/<yourDefaultTabNameTab>.tsx
```

<span data-ttu-id="d880e-115">Hier finden Sie Ihre Registerkartenlogik.</span><span class="sxs-lookup"><span data-stu-id="d880e-115">That is where you'll find your tab logic.</span></span> <span data-ttu-id="d880e-116">Suchen Sie die Methode, und fügen Sie dem Containercode das folgende Tag und `render()` `<div>` den folgenden Inhalt `<PanelBody>` hinzu:</span><span class="sxs-lookup"><span data-stu-id="d880e-116">Locate the `render()` method and add the following `<div>` tag and content to the top of the `<PanelBody>` container code:</span></span>

```html
    <PanelBody>
        <div style={styles.section}>
            Hello World! Yo Teams rocks!
        </div>
    </PanelBody>
```

<span data-ttu-id="d880e-117">Stellen Sie sicher, dass die aktualisierte Datei gespeichert wird.</span><span class="sxs-lookup"><span data-stu-id="d880e-117">Make sure to save the updated file.</span></span>

## <a name="build-and-run-your-application"></a><span data-ttu-id="d880e-118">Erstellen und Ausführen Der Anwendung</span><span class="sxs-lookup"><span data-stu-id="d880e-118">Build and Run Your Application</span></span>

<span data-ttu-id="d880e-119">Öffnen Sie eine Eingabeaufforderung in Ihrem Projektverzeichnis, um die nächsten Aufgaben auszuführen.</span><span class="sxs-lookup"><span data-stu-id="d880e-119">Open a command prompt in your project directory to complete the next tasks.</span></span>

[!INCLUDE [node-js-yeoman-gulp-tasks](~/includes/tabs/node-js-yeoman-gulp-tasks.md)]

<span data-ttu-id="d880e-120">Wechseln Sie zum Anzeigen der Registerkartenkonfigurationsseite zu `https://localhost:3007/<yourDefaultAppNameTab>/config.html` .</span><span class="sxs-lookup"><span data-stu-id="d880e-120">To view your tab configuration page go to `https://localhost:3007/<yourDefaultAppNameTab>/config.html`.</span></span> <span data-ttu-id="d880e-121">Folgendes sollte angezeigt werden:</span><span class="sxs-lookup"><span data-stu-id="d880e-121">You should see the following:</span></span>

![Screenshot der Konfigurationsseite](~/assets/images/tab-images/configurationPage.png)

## <a name="establish-a-secure-tunnel-to-your-tab"></a><span data-ttu-id="d880e-123">Einrichten eines sicheren Tunnels für Ihre Registerkarte</span><span class="sxs-lookup"><span data-stu-id="d880e-123">Establish a secure tunnel to your tab</span></span>

<span data-ttu-id="d880e-124">Microsoft Teams ist ein vollständig cloudbasiertes Produkt und erfordert, dass Ihre Registerkarteninhalte über HTTPS-Endpunkte in der Cloud verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="d880e-124">Microsoft Teams is an entirely cloud-based product and requires that your tab content be available from the cloud using HTTPS endpoints.</span></span> <span data-ttu-id="d880e-125">Teams lokales Hosting ist nicht zulässig, daher müssen Sie Ihre Registerkarte entweder in einer öffentlichen URL veröffentlichen oder einen Proxy verwenden, der Ihren lokalen Port für eine mit dem Internet zugängliche URL verfügbar macht.</span><span class="sxs-lookup"><span data-stu-id="d880e-125">Teams doesn't allow local hosting, therefore, you need to either publish your tab to a public URL or use a proxy that will expose your local port to an internet-facing URL.</span></span>

<span data-ttu-id="d880e-126">Zum Testen der Tabulatorerweiterung verwenden Sie [ngrok](https://ngrok.com/docs), das in diese Anwendung integrierte.</span><span class="sxs-lookup"><span data-stu-id="d880e-126">To test your tab extension, you'll use [ngrok](https://ngrok.com/docs), which is built into this application.</span></span> <span data-ttu-id="d880e-127">Ngrok ist ein Reverseproxy-Softwaretool, das einen Tunnel zu den öffentlich verfügbaren HTTPS-Endpunkten Ihres lokal ausgeführten Webservers erstellt.</span><span class="sxs-lookup"><span data-stu-id="d880e-127">Ngrok is a reverse proxy software tool that will create a tunnel to your locally running web server's publicly-available HTTPS endpoints.</span></span> <span data-ttu-id="d880e-128">Die Webendpunkte Ihres Servers stehen während der aktuellen Sitzung auf Dem lokalen Computer zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="d880e-128">Your server's web endpoints will be available during the current session on your local machine.</span></span> <span data-ttu-id="d880e-129">Wenn der Computer heruntergefahren wird oder in den Ruhezustand geht, ist der Dienst nicht mehr verfügbar.</span><span class="sxs-lookup"><span data-stu-id="d880e-129">When the machine is shut down or goes to sleep the service will no longer be available.</span></span>

<span data-ttu-id="d880e-130">Beenden Sie localhost in der Eingabeaufforderung, und geben Sie Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="d880e-130">In your command prompt, exit localhost and enter the following:</span></span>

```bash
gulp ngrok-serve
```

> [!IMPORTANT]
> <span data-ttu-id="d880e-131">Nachdem Ihre Registerkarte in Microsoft Teams hochgeladen und erfolgreich gespeichert wurde, können Sie sie im Registerkartenkatalog anzeigen, der Registerkartenleiste hinzufügen und mit ihr interagieren, bis Ihre ngrok-Tunnelsitzung endet.</span><span class="sxs-lookup"><span data-stu-id="d880e-131">After your tab has been uploaded to Microsoft teams and successfully saved, you can view it in the tabs gallery, add it to the tabs bar, and interact with it until your ngrok tunnel session ends.</span></span> <span data-ttu-id="d880e-132">Wenn Sie Ihre ngrok-Sitzung neu starten, müssen Sie Ihre App mit der neuen URL aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="d880e-132">If you restart your ngrok session, you'll need to update your app with the new URL.</span></span>

## <a name="upload-your-application-to-teams"></a><span data-ttu-id="d880e-133">Hochladen Ihre Anwendung zu Teams</span><span class="sxs-lookup"><span data-stu-id="d880e-133">Upload your application to Teams</span></span>

- <span data-ttu-id="d880e-134">Öffnen Sie den Microsoft Teams Client.</span><span class="sxs-lookup"><span data-stu-id="d880e-134">Open the Microsoft Teams client.</span></span> <span data-ttu-id="d880e-135">Wenn Sie die [webbasierte Version verwenden,](https://teams.microsoft.com) können Sie Ihren Front-End-Code mithilfe der Entwicklertools Ihres Browsers [überprüfen.](~/tabs/how-to/developer-tools.md)</span><span class="sxs-lookup"><span data-stu-id="d880e-135">If you use the [web based version](https://teams.microsoft.com) you can inspect your front-end code using your browser's [developer tools](~/tabs/how-to/developer-tools.md).</span></span>
- <span data-ttu-id="d880e-136">Wählen Sie *im Bereich YourTeams* auf der linken Seite das Menü neben dem Team aus, das Sie zum Testen Ihrer Registerkarte verwenden, und `...` wählen Sie Team verwalten **aus.**</span><span class="sxs-lookup"><span data-stu-id="d880e-136">In the *YourTeams* panel on the left, select the `...` menu next to the team that you're using to test your tab and choose **Manage team**.</span></span>
- <span data-ttu-id="d880e-137">Wählen Sie im Hauptbereich **apps** aus der Registerkartenleiste aus, und wählen **Hochladen** eine benutzerdefinierte App in der unteren rechten Ecke der Seite aus.</span><span class="sxs-lookup"><span data-stu-id="d880e-137">In the main panel select **Apps** from the tab bar and choose **Upload a custom app** located in the lower right-hand corner of the page.</span></span>
- <span data-ttu-id="d880e-138">Öffnen Sie Ihr Projektverzeichnis, navigieren Sie zum **Ordner ./package,** wählen Sie den Ordner app package zip aus, und wählen Sie **Öffnen aus.**</span><span class="sxs-lookup"><span data-stu-id="d880e-138">Open your project directory, browse to the **./package** folder, select the app package zip folder and choose **Open**.</span></span> <span data-ttu-id="d880e-139">Ihre Registerkarte wird in Teams.</span><span class="sxs-lookup"><span data-stu-id="d880e-139">Your tab will upload into Teams.</span></span>
- <span data-ttu-id="d880e-140">Kehren Sie zu Ihrem Team zurück, wählen Sie den Kanal aus, in dem Sie die Registerkarte anzeigen möchten, wählen ➕ in der Registerkartenleiste aus, und wählen Sie ihre Registerkarte aus dem Katalog aus.</span><span class="sxs-lookup"><span data-stu-id="d880e-140">Return to your team, choose the channel where you would like to display the tab, select ➕ from the tab bar, and choose your tab from the gallery.</span></span>
- <span data-ttu-id="d880e-141">Befolgen Sie die Anweisungen zum Hinzufügen einer Registerkarte. Beachten Sie, dass es ein benutzerdefiniertes Konfigurationsdialogfeld für Die Registerkarte Kanal/Gruppe gibt.</span><span class="sxs-lookup"><span data-stu-id="d880e-141">Follow the directions for adding a tab. Note that there's a custom configuration dialog for your channel/group tab.</span></span>
- <span data-ttu-id="d880e-142">Wählen **Sie Speichern** aus, und Ihre Registerkarte wird der Registerkartenleiste des Kanals hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="d880e-142">Select **Save** and your tab will be added to the channel's tab bar.</span></span>
