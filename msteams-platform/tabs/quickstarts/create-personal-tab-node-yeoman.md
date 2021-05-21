---
title: 'Schnellstart: Erstellen einer benutzerdefinierten persönlichen Registerkarte mit Node.js und dem Yeoman-Generator für Microsoft Teams'
author: laujan
description: Eine Schnellstartanleitung zum Erstellen einer persönlichen Registerkarte mit dem Yeoman-Generator für Microsoft Teams.
localization_priority: Normal
ms.topic: quickstart
ms.author: lajanuar
ms.openlocfilehash: 88ad05aacaed69d695bc918e3e8a44ec18e560ae
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566606"
---
# <a name="create-a-custom-personal-tab-using-nodejs-and-the-yeoman-generator-for-microsoft-teams"></a><span data-ttu-id="1037c-103">Erstellen Sie eine benutzerdefinierte persönliche Registerkarte mit Node.js und dem Yeoman-Generator für Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="1037c-103">Create a custom personal tab using Node.js and the Yeoman Generator for Microsoft Teams</span></span>

>[!NOTE]
><span data-ttu-id="1037c-104">Dieser Schnellstart folgt den Schritten, die im Wiki zum Erstellen der ersten [Microsoft Teams-App](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App) im Microsoft OfficeDev-Repository GitHub sind.</span><span class="sxs-lookup"><span data-stu-id="1037c-104">This quickstart follows the steps outlined in the [Build Your First Microsoft Teams App](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App) Wiki found in the Microsoft OfficeDev GitHub repository.</span></span>

<span data-ttu-id="1037c-105">In dieser Schnellstartanleitung werden wir durch das Erstellen einer benutzerdefinierten persönlichen Registerkarte mithilfe des Teams [Yeoman-Generators gehen.](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App)</span><span class="sxs-lookup"><span data-stu-id="1037c-105">In this quickstart we'll walk-through creating a custom personal tab using the [Teams Yeoman generator](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App).</span></span> <span data-ttu-id="1037c-106">Wir laden die Anwendung auch in Team hoch.</span><span class="sxs-lookup"><span data-stu-id="1037c-106">We'll also upload the application to Team.</span></span>

[!INCLUDE [node-js-yeoman-prereq](~/includes/tabs/node-js-yeoman-prereq.md)]

<span data-ttu-id="1037c-107">**Erstellen einer konfigurierbaren oder statischen Registerkarte**</span><span class="sxs-lookup"><span data-stu-id="1037c-107">**Create a configurable or static tab**</span></span>

<span data-ttu-id="1037c-108">Verwenden Sie die Pfeiltasten, um die statische Registerkarte auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="1037c-108">Use the arrow keys to select static tab.</span></span>

>[!IMPORTANT]
><span data-ttu-id="1037c-109">Die Pfadkomponente *yourDefaultTabNameTab*, auf die in diesem Schnellstart verwiesen wird, ist der Wert, den Sie im Generator für *Standardregisterkartenname* plus das Wort *Tab eingegeben haben.*</span><span class="sxs-lookup"><span data-stu-id="1037c-109">The path component *yourDefaultTabNameTab*, referenced in this quickstart, is the value that you entered in the generator for *Default Tab Name* plus the word *Tab*.</span></span>
>
><span data-ttu-id="1037c-110">Beispiel: DefaultTabName: *MyTab*  =>  */MyTabTab/*</span><span class="sxs-lookup"><span data-stu-id="1037c-110">For example: DefaultTabName: *MyTab* => */MyTabTab/*</span></span>

## <a name="create-your-personal-tab"></a><span data-ttu-id="1037c-111">Erstellen Ihrer persönlichen Registerkarte</span><span class="sxs-lookup"><span data-stu-id="1037c-111">Create your personal tab</span></span>

<span data-ttu-id="1037c-112">Um dieser Anwendung eine persönliche Registerkarte hinzuzufügen, erstellen Sie eine Inhaltsseite und aktualisieren vorhandene Dateien:</span><span class="sxs-lookup"><span data-stu-id="1037c-112">To add a personal tab to this application you'll create a content page and update existing files:</span></span>

- <span data-ttu-id="1037c-113">Erstellen Sie im Code-Editor eine neue HTML-Datei, **personal.html,** und fügen Sie das folgende Markup hinzu:</span><span class="sxs-lookup"><span data-stu-id="1037c-113">In your code editor, create a new HTML file, **personal.html** and add the following markup:</span></span>

    ```html
    <!DOCTYPE html>
    <html>
        <head>
            <meta charset="UTF-8">
            <title>
                <!-- Todo: add your a title here -->
            </title>
            <meta name="viewport" content="width=device-width, initial-scale=1.0">
            <!-- inject:css -->
            <!-- endinject -->
        </head>
            <body>
                <h1>Personal Tab</h1>
                <p><img src="/assets/icon.png"></p>
                <p>This is your personal tab!</p>
            </body>
    </html>
    ```

- <span data-ttu-id="1037c-114">Speichern **personal.html** im Webordner Ihrer **Anwendung:**</span><span class="sxs-lookup"><span data-stu-id="1037c-114">Save **personal.html** in your application's **web** folder:</span></span>

    ```bash
    ./src/app/web/<yourDefaultTabNameTab>/personal.html
    ```

- <span data-ttu-id="1037c-115">Öffnen **manifest.jsim** Code-Editor:</span><span class="sxs-lookup"><span data-stu-id="1037c-115">Open **manifest.json** in your code editor:</span></span>

    ```bash
    ./src/manifest/manifest.json/
    ```

<span data-ttu-id="1037c-116">Fügen Sie dem leeren Array ( ) Folgendes `staticTabs` `staticTabs":[]` hinzu, und fügen Sie das folgende JSON-Objekt hinzu:</span><span class="sxs-lookup"><span data-stu-id="1037c-116">Add the following to the empty `staticTabs` array (`staticTabs":[]`) and add the following JSON object:</span></span>

```json
{
    "entityId": "personalTab",
    "name": "Personal Tab ",
    "contentUrl": "https://{{HOSTNAME}}/<yourDefaultTabNameTab>/personal.html",
    "websiteUrl": "https://{{HOSTNAME}}",
    "scopes": ["personal"]
}

```

<span data-ttu-id="1037c-117">Denken Sie daran, die **Pfadkomponente "contentURL"** **yourDefaultTabNameTab** mit ihrem tatsächlichen Registerkartennamen zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="1037c-117">Remember to update the **"contentURL"** path component **yourDefaultTabNameTab** with your actual tab name.</span></span>

- <span data-ttu-id="1037c-118">Speichern Sie die **aktualisiertemanifest.jsunter**.</span><span class="sxs-lookup"><span data-stu-id="1037c-118">Save the updated **manifest.json**.</span></span>

- <span data-ttu-id="1037c-119">Ihre Inhaltsseite muss in einem IFrame bedient werden.</span><span class="sxs-lookup"><span data-stu-id="1037c-119">Your content page must be served in an IFrame.</span></span> <span data-ttu-id="1037c-120">Öffnen **Sie Tab.ts** im Code-Editor:</span><span class="sxs-lookup"><span data-stu-id="1037c-120">Open **Tab.ts** in your code editor:</span></span>

    ```bash
    ./src/app/<yourDefaultTabNameTab>/<yourDefaultTabNameTab>.ts
    ```

- <span data-ttu-id="1037c-121">Fügen Sie der Liste der IFrame-Verzierer Folgendes hinzu:</span><span class="sxs-lookup"><span data-stu-id="1037c-121">Add the following to the list of IFrame decorators:</span></span>

    ```typescript
     @PreventIframe("/<yourDefaultAppName>TabNameTab>/personal.html")
    ```

- <span data-ttu-id="1037c-122">Stellen Sie sicher, dass Sie die aktualisierte **Tab.ts-Datei** speichern.</span><span class="sxs-lookup"><span data-stu-id="1037c-122">Make sure to save the updated **Tab.ts** file.</span></span> <span data-ttu-id="1037c-123">Der Registerkartencode ist vollständig.</span><span class="sxs-lookup"><span data-stu-id="1037c-123">Your tab code is complete.</span></span>

## <a name="build-and-run-your-application"></a><span data-ttu-id="1037c-124">Erstellen und Ausführen Der Anwendung</span><span class="sxs-lookup"><span data-stu-id="1037c-124">Build and Run Your Application</span></span>

<span data-ttu-id="1037c-125">Öffnen Sie eine Eingabeaufforderung in Ihrem Projektverzeichnis, um die nächsten Aufgaben auszuführen.</span><span class="sxs-lookup"><span data-stu-id="1037c-125">Open a command prompt in your project directory to complete the next tasks.</span></span>

[!INCLUDE [node-js-yeoman-gulp-tasks](~/includes/tabs/node-js-yeoman-gulp-tasks.md)]

<span data-ttu-id="1037c-126">Um Ihre persönliche Registerkarte zu sehen, wechseln Sie zu `http://localhost:3007/<yourDefaultAppNameTab>/personal.html`</span><span class="sxs-lookup"><span data-stu-id="1037c-126">To view your personal tab, go to `http://localhost:3007/<yourDefaultAppNameTab>/personal.html`</span></span>

>![Screenshot der persönlichen Registerkarte](/microsoftteams/platform/assets/images/tab-images/personalTab.PNG)

## <a name="establish-a-secure-tunnel-to-your-tab"></a><span data-ttu-id="1037c-128">Einrichten eines sicheren Tunnels für Ihre Registerkarte</span><span class="sxs-lookup"><span data-stu-id="1037c-128">Establish a secure tunnel to your tab</span></span>

<span data-ttu-id="1037c-129">Microsoft Teams ist ein vollständig cloudbasiertes Produkt und erfordert, dass Ihre Registerkarteninhalte über HTTPS-Endpunkte in der Cloud verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="1037c-129">Microsoft Teams is an entirely cloud-based product and requires that your tab content be available from the cloud using HTTPS endpoints.</span></span> <span data-ttu-id="1037c-130">Teams lokales Hosting ist nicht zulässig, daher müssen Sie Ihre Registerkarte entweder in einer öffentlichen URL veröffentlichen oder einen Proxy verwenden, der Ihren lokalen Port für eine mit dem Internet zugängliche URL verfügbar macht.</span><span class="sxs-lookup"><span data-stu-id="1037c-130">Teams doesn't allow local hosting, therefore, you need to either publish your tab to a public URL or use a proxy that will expose your local port to an internet-facing URL.</span></span>

<span data-ttu-id="1037c-131">Zum Testen der Tabulatorerweiterung verwenden Sie [ngrok](https://ngrok.com/docs), das in diese Anwendung integrierte.</span><span class="sxs-lookup"><span data-stu-id="1037c-131">To test your tab extension, you'll use [ngrok](https://ngrok.com/docs), which is built into this application.</span></span> <span data-ttu-id="1037c-132">Ngrok ist ein Reverseproxy-Softwaretool, das einen Tunnel zu den öffentlich verfügbaren HTTPS-Endpunkten Ihres lokal ausgeführten Webservers erstellt.</span><span class="sxs-lookup"><span data-stu-id="1037c-132">Ngrok is a reverse proxy software tool that will create a tunnel to your locally running web server's publicly-available HTTPS endpoints.</span></span> <span data-ttu-id="1037c-133">Die Webendpunkte Ihres Servers stehen während der aktuellen Sitzung auf Dem lokalen Computer zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="1037c-133">Your server's web endpoints will be available during the current session on your local machine.</span></span> <span data-ttu-id="1037c-134">Wenn der Computer heruntergefahren wird oder in den Ruhezustand geht, ist der Dienst nicht mehr verfügbar.</span><span class="sxs-lookup"><span data-stu-id="1037c-134">When the machine is shut down or goes to sleep the service will no longer be available.</span></span>

<span data-ttu-id="1037c-135">Beenden Sie localhost in der Eingabeaufforderung, und geben Sie Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="1037c-135">In your command prompt, exit localhost and enter the following:</span></span>

```bash
gulp ngrok-serve
```

> [!IMPORTANT]
> <span data-ttu-id="1037c-136">Nachdem Ihre Registerkarte in Microsoft Teams hochgeladen, über **ngrok** und erfolgreich gespeichert wurde, können Sie sie in der Teams, bis Ihre Tunnelsitzung endet.</span><span class="sxs-lookup"><span data-stu-id="1037c-136">After your tab has been uploaded to Microsoft teams, via **ngrok**, and successfully saved, you can view it in Teams until your tunnel session ends.</span></span>

## <a name="upload-your-application-to-teams"></a><span data-ttu-id="1037c-137">Hochladen Ihre Anwendung zu Teams</span><span class="sxs-lookup"><span data-stu-id="1037c-137">Upload your application to Teams</span></span>

- <span data-ttu-id="1037c-138">Öffnen Sie den Microsoft Teams Client.</span><span class="sxs-lookup"><span data-stu-id="1037c-138">Open the Microsoft Teams client.</span></span> <span data-ttu-id="1037c-139">Wenn Sie die [webbasierte Version verwenden,](https://teams.microsoft.com) können Sie Ihren Front-End-Code mithilfe der Entwicklertools Ihres Browsers [überprüfen.](~/tabs/how-to/developer-tools.md)</span><span class="sxs-lookup"><span data-stu-id="1037c-139">If you use the [web based version](https://teams.microsoft.com) you can inspect your front-end code using your browser's [developer tools](~/tabs/how-to/developer-tools.md).</span></span>
- <span data-ttu-id="1037c-140">Wählen Sie **im Bereich YourTeams** auf der linken Seite das Menü neben dem Team aus, das Sie zum Testen Ihrer Registerkarte verwenden, und `...` wählen Sie Team verwalten **aus.**</span><span class="sxs-lookup"><span data-stu-id="1037c-140">In the **YourTeams** panel on the left, select the `...` menu next to the team that you're using to test your tab and choose **Manage team**.</span></span>
- <span data-ttu-id="1037c-141">Wählen Sie im Hauptbereich **apps** aus der Registerkartenleiste aus, und wählen **Hochladen** eine benutzerdefinierte App in der unteren rechten Ecke der Seite aus.</span><span class="sxs-lookup"><span data-stu-id="1037c-141">In the main panel select **Apps** from the tab bar and choose **Upload a custom app** located in the lower right-hand corner of the page.</span></span>
- <span data-ttu-id="1037c-142">Öffnen Sie Ihr Projektverzeichnis, navigieren Sie zum **Ordner ./package,** wählen Sie den Ordner "ZIP" aus, klicken Sie mit der rechten Maustaste, und wählen Sie **Öffnen aus.**</span><span class="sxs-lookup"><span data-stu-id="1037c-142">Open your project directory, browse to the **./package** folder, select the zip folder, right-click, and choose **Open**.</span></span> <span data-ttu-id="1037c-143">Ihre Registerkarte wird in Teams.</span><span class="sxs-lookup"><span data-stu-id="1037c-143">Your tab will upload into Teams.</span></span>

## <a name="view-your-personal-tabs"></a><span data-ttu-id="1037c-144">Anzeigen Ihrer persönlichen Registerkarten</span><span class="sxs-lookup"><span data-stu-id="1037c-144">View your personal tabs</span></span>

<span data-ttu-id="1037c-145">Wählen Sie in der Navigationsleiste ganz links neben dem client Teams das Menü aus, und wählen Sie ihre `...` App aus der Liste aus.</span><span class="sxs-lookup"><span data-stu-id="1037c-145">In the navbar located at the far-left of the Teams client, select the `...` menu and choose your app from the list.</span></span>

## <a name="next-step"></a><span data-ttu-id="1037c-146">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="1037c-146">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="1037c-147">Erstellen einer persönlichen Registerkarte mithilfe von ASP.NETCore</span><span class="sxs-lookup"><span data-stu-id="1037c-147">Create a personal tab using ASP.NETCore</span></span>](~/tabs/quickstarts/create-personal-tab-dotnet-core.md)
