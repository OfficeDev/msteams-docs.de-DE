---
title: Erstellen einer benutzerdefinierten Kanal-und Gruppenregisterkarte mit Node. js und dem Generator für Microsoft Teams
author: laujan
description: Eine Schnellstartanleitung zum Erstellen einer Kanal-und Gruppenregisterkarte mit dem Landarbeits Generator für Microsoft Teams.
ms.topic: quickstart
ms.author: laujan
ms.openlocfilehash: c5e028dcc117d729f2bf366923d03568b7f557a4
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674290"
---
# <a name="create-a-custom-channel-and-group-tab-with-nodejs-and-the-yeoman-generator-for-microsoft-teams"></a><span data-ttu-id="4919b-103">Erstellen einer benutzerdefinierten Kanal-und Gruppenregisterkarte mit Node. js und dem Generator für Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="4919b-103">Create a custom channel and group tab with Node.js and the Yeoman Generator for Microsoft Teams</span></span>

>[!NOTE]
><span data-ttu-id="4919b-104">Diese Schnellstartleiste folgt den Schritten im Artikel [Erstellen des ersten Microsoft Teams-App](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App) -Wikis, die im Microsoft officedev GitHub-Repository gefunden wurden.</span><span class="sxs-lookup"><span data-stu-id="4919b-104">This quickstart follows the steps outlined in the [Build Your First Microsoft Teams App](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App) Wiki found in the Microsoft OfficeDev GitHub repository.</span></span>

<span data-ttu-id="4919b-105">In diesem Schnellstart werden Sie durch das Erstellen einer benutzerdefinierten Kanal-und Gruppenregisterkarte mithilfe des Teams-Landarbeits [Generators](https://github.com/OfficeDev/generator-teams/)durchlaufen.</span><span class="sxs-lookup"><span data-stu-id="4919b-105">In this quickstart we'll walk-through creating a custom channel and group tab using the [Teams Yeoman generator](https://github.com/OfficeDev/generator-teams/).</span></span>

[!INCLUDE [node-js-yeoman-prereq](~/includes/tabs/node-js-yeoman-prereq.md)]

<span data-ttu-id="4919b-106">**Möchten Sie eine konfigurierbare oder statische RegisterkarteErstellen?**</span><span class="sxs-lookup"><span data-stu-id="4919b-106">**Do you want to create a configurable or static tab?**</span></span>

<span data-ttu-id="4919b-107">Verwenden Sie die Pfeiltasten, um die Registerkarte konfigurierbar auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="4919b-107">Use the arrow keys to select configurable tab.</span></span>

<span data-ttu-id="4919b-108">**Welche Bereiche möchten Sie für Ihre Registerkarte verwenden?**</span><span class="sxs-lookup"><span data-stu-id="4919b-108">**What scopes do you intend to use for your Tab?**</span></span>

<span data-ttu-id="4919b-109">Sie können ein Team und/oder einen Gruppenchat auswählen.</span><span class="sxs-lookup"><span data-stu-id="4919b-109">You can select a Team and/or a group chat</span></span>

<span data-ttu-id="4919b-110">**Soll diese Registerkarte in SharePoint Online verfügbar sein? (J/n)**</span><span class="sxs-lookup"><span data-stu-id="4919b-110">**Do you want this tab to be available in SharePoint Online? (Y/n)**</span></span> 

<span data-ttu-id="4919b-111">Wählen Sie **n**aus.</span><span class="sxs-lookup"><span data-stu-id="4919b-111">Select **n**.</span></span>

>[!IMPORTANT]
><span data-ttu-id="4919b-112">In der Pfadkomponente **yourDefaultTabNameTab**, auf die in diesem Schnellstart verwiesen wird, handelt es sich um den Wert, den Sie im Generator für den **standardmäßigen Registerkartennamen** sowie die **Register**Karte Word eingegeben haben.</span><span class="sxs-lookup"><span data-stu-id="4919b-112">The path component **yourDefaultTabNameTab**, referenced in this quickstart, is the value that you entered in the generator for **Default Tab Name** plus the word **Tab**.</span></span>
>
><span data-ttu-id="4919b-113">Beispiel: DefaultTabName: **mytab** => **/MyTabTab/**</span><span class="sxs-lookup"><span data-stu-id="4919b-113">For example: DefaultTabName: **MyTab** => **/MyTabTab/**</span></span>

<span data-ttu-id="4919b-114">Navigieren Sie in Ihrem Projektverzeichnis zu folgendem:</span><span class="sxs-lookup"><span data-stu-id="4919b-114">In your project directory, navigate to the following:</span></span>

```bash
./src/app/scripts/<yourDefaultTabNameTab>/<yourDefaultTabNameTab>.tsx
```

<span data-ttu-id="4919b-115">Hier finden Sie Ihre Tab-Logik.</span><span class="sxs-lookup"><span data-stu-id="4919b-115">That is where you'll find your tab logic.</span></span> <span data-ttu-id="4919b-116">Suchen Sie `render()` die-Methode, und `<div>` fügen Sie das folgende Tag und den Inhalt `<PanelBody>` oben im Container Code hinzu:</span><span class="sxs-lookup"><span data-stu-id="4919b-116">Locate the `render()` method and add the following `<div>` tag and content to the top of the `<PanelBody>` container code:</span></span>

```html
    <PanelBody>
        <div style={styles.section}>
            Hello World! Yo Teams rocks!
        </div>
    </PanelBody>
```

<span data-ttu-id="4919b-117">Stellen Sie sicher, dass Sie die aktualisierte Datei speichern.</span><span class="sxs-lookup"><span data-stu-id="4919b-117">Make sure to save the updated file.</span></span>

## <a name="build-and-run-your-application"></a><span data-ttu-id="4919b-118">Erstellen und Ausführen der Anwendung</span><span class="sxs-lookup"><span data-stu-id="4919b-118">Build and Run Your Application</span></span>

<span data-ttu-id="4919b-119">Öffnen Sie im Projektverzeichnis eine Eingabeaufforderung, um die nächsten Aufgaben abzuschließen.</span><span class="sxs-lookup"><span data-stu-id="4919b-119">Open a command prompt in your project directory to complete the next tasks.</span></span>

[!INCLUDE [node-js-yeoman-gulp-tasks](~/includes/tabs/node-js-yeoman-gulp-tasks.md)]

<span data-ttu-id="4919b-120">Um Ihre Registerkarten-Konfigurationsseite anzuzeigen `https://localhost:3007/<yourDefaultAppNameTab>/config.html`, wechseln Sie zu.</span><span class="sxs-lookup"><span data-stu-id="4919b-120">To view your tab configuration page go to `https://localhost:3007/<yourDefaultAppNameTab>/config.html`.</span></span> <span data-ttu-id="4919b-121">Folgendes sollte angezeigt werden:</span><span class="sxs-lookup"><span data-stu-id="4919b-121">You should see the following:</span></span>

![Screenshot der Konfigurationsseite](~/assets/images/tab-images/configurationPage.png)

## <a name="establish-a-secure-tunnel-to-your-tab"></a><span data-ttu-id="4919b-123">Einrichten eines sicheren Tunnels für die Registerkarte</span><span class="sxs-lookup"><span data-stu-id="4919b-123">Establish a secure tunnel to your tab</span></span>

<span data-ttu-id="4919b-124">Microsoft Teams ist ein vollständig Cloud-basiertes Produkt und erfordert, dass Ihre Registerkarteninhalte über HTTPS-Endpunkte in der Cloud verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="4919b-124">Microsoft Teams is an entirely cloud-based product and requires that your tab content be available from the cloud using HTTPS endpoints.</span></span> <span data-ttu-id="4919b-125">Teams nicht zulassen lokales Hosting daher müssen Sie entweder Ihre Registerkarte in einer öffentlichen URL veröffentlichen oder einen Proxy verwenden, der den lokalen Port einer URL mit Internetverbindung verfügbar macht.</span><span class="sxs-lookup"><span data-stu-id="4919b-125">Teams doesn't allow local hosting, therefore, you need to either publish your tab to a public URL or use a proxy that will expose your local port to an internet-facing URL.</span></span>

<span data-ttu-id="4919b-126">Um Ihre Tab-Erweiterung zu testen, verwenden Sie [ngrok](https://ngrok.com/docs), das in diese Anwendung integriert ist.</span><span class="sxs-lookup"><span data-stu-id="4919b-126">To test your tab extension, you'll use [ngrok](https://ngrok.com/docs), which is built into this application.</span></span> <span data-ttu-id="4919b-127">Ngrok ist ein Reverse-Proxy-Software Tool, mit dem ein Tunnel zu den öffentlich verfügbaren HTTPS-Endpunkten des lokal ausgeführten Webservers erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="4919b-127">Ngrok is a reverse proxy software tool that will create a tunnel to your locally running web server's publicly-available HTTPS endpoints.</span></span> <span data-ttu-id="4919b-128">Die Webendpunkte Ihres Servers sind während der aktuellen Sitzung auf Ihrem lokalen Computer verfügbar.</span><span class="sxs-lookup"><span data-stu-id="4919b-128">Your server's web endpoints will be available during the current session on your local machine.</span></span> <span data-ttu-id="4919b-129">Wenn der Computer heruntergefahren wird oder in den Standbymodus wechselt, steht der Dienst nicht mehr zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="4919b-129">When the machine is shut down or goes to sleep the service will no longer be available.</span></span>

<span data-ttu-id="4919b-130">Beenden Sie in der Eingabeaufforderung localhost, und geben Sie Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="4919b-130">In your command prompt, exit localhost and enter the following:</span></span>

```bash
gulp ngrok-serve
```

> [!IMPORTANT]
> <span data-ttu-id="4919b-131">Nachdem die Registerkarte in Microsoft Teams hochgeladen und erfolgreich gespeichert wurde, können Sie Sie im Registerkarten Katalog anzeigen, der Registerkartenleiste hinzufügen und mit ihr interagieren, bis die ngrok-Tunnelsitzung endet.</span><span class="sxs-lookup"><span data-stu-id="4919b-131">After your tab has been uploaded to Microsoft teams and successfully saved, you can view it in the tabs gallery, add it to the tabs bar, and interact with it until your ngrok tunnel session ends.</span></span> <span data-ttu-id="4919b-132">Wenn Sie die ngrok-Sitzung neu starten, müssen Sie Ihre APP mit der neuen URL aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="4919b-132">If you restart your ngrok session, you'll need to update your app with the new URL.</span></span>

## <a name="upload-your-application-to-teams"></a><span data-ttu-id="4919b-133">Hochladen Ihrer Anwendung in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="4919b-133">Upload your application to Teams</span></span>

- <span data-ttu-id="4919b-134">Öffnen Sie den Microsoft Teams-Client.</span><span class="sxs-lookup"><span data-stu-id="4919b-134">Open the Microsoft Teams client.</span></span> <span data-ttu-id="4919b-135">Wenn Sie die [webbasierte Version](https://teams.microsoft.com) verwenden, können Sie den Front-End-Code mithilfe der [Entwicklertools](~/tabs/how-to/developer-tools.md)Ihres Browsers überprüfen.</span><span class="sxs-lookup"><span data-stu-id="4919b-135">If you use the [web based version](https://teams.microsoft.com) you can inspect your front-end code using your browser's [developer tools](~/tabs/how-to/developer-tools.md).</span></span>
- <span data-ttu-id="4919b-136">Wählen Sie im *YourTeams* -Bereich auf der linken Seite `...` das Menü neben dem Team aus, das Sie zum Testen der Registerkarte verwenden, und wählen Sie **Team verwalten**aus.</span><span class="sxs-lookup"><span data-stu-id="4919b-136">In the *YourTeams* panel on the left, select the `...` menu next to the team that you're using to test your tab and choose **Manage team**.</span></span>
- <span data-ttu-id="4919b-137">Wählen Sie im Hauptbereich **apps** in der Registerkartenleiste aus, und wählen Sie **eine benutzerdefinierte App hochladen** , die sich in der unteren rechten Ecke der Seite befindet.</span><span class="sxs-lookup"><span data-stu-id="4919b-137">In the main panel select **Apps** from the tab bar and choose **Upload a custom app** located in the lower right-hand corner of the page.</span></span>
- <span data-ttu-id="4919b-138">Öffnen Sie Ihr Projektverzeichnis, navigieren Sie zum Ordner **./Paket** , wählen Sie den ZIP-Ordner für das App-Paket aus, und wählen Sie **Öffnen**aus.</span><span class="sxs-lookup"><span data-stu-id="4919b-138">Open your project directory, browse to the **./package** folder, select the app package zip folder and choose **Open**.</span></span> <span data-ttu-id="4919b-139">Ihre Registerkarte wird in Teams hochgeladen.</span><span class="sxs-lookup"><span data-stu-id="4919b-139">Your tab will upload into Teams.</span></span>
- <span data-ttu-id="4919b-140">Kehren Sie zu Ihrem Team zurück, wählen Sie den Kanal aus, in dem Sie die Registerkarte anzeigen möchten, wählen Sie in der Registerkartenleiste ➕ aus, und wählen Sie im Katalog die Registerkarte aus.</span><span class="sxs-lookup"><span data-stu-id="4919b-140">Return to your team, choose the channel where you would like to display the tab, select ➕ from the tab bar, and choose your tab from the gallery.</span></span>
- <span data-ttu-id="4919b-141">Befolgen Sie die Anweisungen zum Hinzufügen einer Registerkarte. Beachten Sie, dass es ein benutzerdefiniertes Konfigurationsdialogfeld für die Registerkarte Kanal/Gruppe gibt.</span><span class="sxs-lookup"><span data-stu-id="4919b-141">Follow the directions for adding a tab. Note that there's a custom configuration dialog for your channel/group tab.</span></span>
- <span data-ttu-id="4919b-142">Wählen Sie **Speichern** aus, und ihre Registerkarte wird der Registerkartenleiste des Kanals hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="4919b-142">Select **Save** and your tab will be added to the channel's tab bar.</span></span>
