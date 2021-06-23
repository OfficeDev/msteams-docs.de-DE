---
title: 'Schnellstart: Erstellen einer benutzerdefinierten persönlichen Registerkarte mit Node.js und dem Yeoman-Generator für Microsoft Teams'
author: surbhigupta
description: Eine Schnellstartanleitung zum Erstellen einer persönlichen Registerkarte mit dem Yeoman-Generator für Microsoft Teams.
localization_priority: Normal
ms.topic: quickstart
ms.author: lajanuar
ms.openlocfilehash: 220d1018f174fc935a10311723a730ebc74ccc33
ms.sourcegitcommit: 623d81eb079d1842813265746a5fe0fe6311b196
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/22/2021
ms.locfileid: "53069202"
---
# <a name="create-a-custom-personal-tab-using-nodejs-and-the-yeoman-generator-for-microsoft-teams"></a><span data-ttu-id="0b11e-103">Erstellen einer benutzerdefinierten persönlichen Registerkarte mit Node.js und dem Yeoman-Generator für Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="0b11e-103">Create a custom personal tab using Node.js and the Yeoman Generator for Microsoft Teams</span></span>

>[!NOTE]
><span data-ttu-id="0b11e-104">Dieser Schnellstart folgt den Schritten, die im Wiki ["Erstellen Ihrer ersten Microsoft Teams App"](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App) im Microsoft OfficeDev-GitHub-Repository beschrieben sind.</span><span class="sxs-lookup"><span data-stu-id="0b11e-104">This quickstart follows the steps outlined in the [Build Your First Microsoft Teams App](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App) Wiki found in the Microsoft OfficeDev GitHub repository.</span></span>

<span data-ttu-id="0b11e-105">In dieser Schnellstartanleitung werden wir schrittweise durch das Erstellen einer benutzerdefinierten persönlichen Registerkarte mithilfe des [Teams Yeoman-Generators geführt.](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App)</span><span class="sxs-lookup"><span data-stu-id="0b11e-105">In this quickstart we'll walk-through creating a custom personal tab using the [Teams Yeoman generator](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App).</span></span> <span data-ttu-id="0b11e-106">Wir werden die Anwendung auch in Team hochladen.</span><span class="sxs-lookup"><span data-stu-id="0b11e-106">We'll also upload the application to Team.</span></span>

[!INCLUDE [node-js-yeoman-prereq](~/includes/tabs/node-js-yeoman-prereq.md)]

<span data-ttu-id="0b11e-107">**Erstellen einer konfigurierbaren oder statischen Registerkarte**</span><span class="sxs-lookup"><span data-stu-id="0b11e-107">**Create a configurable or static tab**</span></span>

<span data-ttu-id="0b11e-108">Verwenden Sie die Pfeiltasten, um die statische Registerkarte auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="0b11e-108">Use the arrow keys to select static tab.</span></span>

>[!IMPORTANT]
><span data-ttu-id="0b11e-109">The path component *yourDefaultTabNameTab*, referenced in this quickstart, is the value that you entered in the generator for *Default Tab Name* plus the word *Tab*.</span><span class="sxs-lookup"><span data-stu-id="0b11e-109">The path component *yourDefaultTabNameTab*, referenced in this quickstart, is the value that you entered in the generator for *Default Tab Name* plus the word *Tab*.</span></span>
>
><span data-ttu-id="0b11e-110">Beispiel: DefaultTabName: *MyTab*  =>  */MyTabTab/*</span><span class="sxs-lookup"><span data-stu-id="0b11e-110">For example: DefaultTabName: *MyTab* => */MyTabTab/*</span></span>

## <a name="create-your-personal-tab"></a><span data-ttu-id="0b11e-111">Erstellen Ihrer persönlichen Registerkarte</span><span class="sxs-lookup"><span data-stu-id="0b11e-111">Create your personal tab</span></span>

<span data-ttu-id="0b11e-112">Um dieser Anwendung eine persönliche Registerkarte hinzuzufügen, erstellen Sie eine Inhaltsseite und aktualisieren vorhandene Dateien:</span><span class="sxs-lookup"><span data-stu-id="0b11e-112">To add a personal tab to this application you'll create a content page and update existing files:</span></span>

- <span data-ttu-id="0b11e-113">Erstellen Sie in Ihrem Code-Editor eine neue HTML-Datei, **personal.html,** und fügen Sie das folgende Markup hinzu:</span><span class="sxs-lookup"><span data-stu-id="0b11e-113">In your code editor, create a new HTML file, **personal.html** and add the following markup:</span></span>

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

- <span data-ttu-id="0b11e-114">Speichern Sie **personal.html** im **Webordner** Ihrer Anwendung:</span><span class="sxs-lookup"><span data-stu-id="0b11e-114">Save **personal.html** in your application's **web** folder:</span></span>

    ```bash
    ./src/app/web/<yourDefaultTabNameTab>/personal.html
    ```

- <span data-ttu-id="0b11e-115">Öffnen **Siemanifest.js** im Code-Editor:</span><span class="sxs-lookup"><span data-stu-id="0b11e-115">Open **manifest.json** in your code editor:</span></span>

    ```bash
    ./src/manifest/manifest.json/
    ```

<span data-ttu-id="0b11e-116">Fügen Sie dem leeren Array ( ) Folgendes `staticTabs` `staticTabs":[]` hinzu, und fügen Sie das folgende JSON-Objekt hinzu:</span><span class="sxs-lookup"><span data-stu-id="0b11e-116">Add the following to the empty `staticTabs` array (`staticTabs":[]`) and add the following JSON object:</span></span>

```json
{
    "entityId": "personalTab",
    "name": "Personal Tab ",
    "contentUrl": "https://{{HOSTNAME}}/<yourDefaultTabNameTab>/personal.html",
    "websiteUrl": "https://{{HOSTNAME}}",
    "scopes": ["personal"]
}

```

<span data-ttu-id="0b11e-117">Denken Sie daran, die **"contentURL"-Pfadkomponente** **"yourDefaultTabNameTab"** mit ihrem tatsächlichen Registerkartennamen zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="0b11e-117">Remember to update the **"contentURL"** path component **yourDefaultTabNameTab** with your actual tab name.</span></span>

- <span data-ttu-id="0b11e-118">Speichern Sie die aktualisierte **manifest.jsunter**.</span><span class="sxs-lookup"><span data-stu-id="0b11e-118">Save the updated **manifest.json**.</span></span>

- <span data-ttu-id="0b11e-119">Ihre Inhaltsseite muss in einem IFrame bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="0b11e-119">Your content page must be served in an IFrame.</span></span> <span data-ttu-id="0b11e-120">Öffnen Sie **Tab.ts** im Code-Editor:</span><span class="sxs-lookup"><span data-stu-id="0b11e-120">Open **Tab.ts** in your code editor:</span></span>

    ```bash
    ./src/app/<yourDefaultTabNameTab>/<yourDefaultTabNameTab>.ts
    ```

- <span data-ttu-id="0b11e-121">Fügen Sie der Liste der IFrame-Decoratoren Folgendes hinzu:</span><span class="sxs-lookup"><span data-stu-id="0b11e-121">Add the following to the list of IFrame decorators:</span></span>

    ```typescript
     @PreventIframe("/<yourDefaultAppName>TabNameTab>/personal.html")
    ```

- <span data-ttu-id="0b11e-122">Speichern Sie unbedingt die aktualisierte Datei **Tab.ts .**</span><span class="sxs-lookup"><span data-stu-id="0b11e-122">Make sure to save the updated **Tab.ts** file.</span></span> <span data-ttu-id="0b11e-123">Der Registerkartencode ist vollständig.</span><span class="sxs-lookup"><span data-stu-id="0b11e-123">Your tab code is complete.</span></span>

## <a name="build-and-run-your-application"></a><span data-ttu-id="0b11e-124">Erstellen und Ausführen ihrer Anwendung</span><span class="sxs-lookup"><span data-stu-id="0b11e-124">Build and Run Your Application</span></span>

<span data-ttu-id="0b11e-125">Öffnen Sie eine Eingabeaufforderung in Ihrem Projektverzeichnis, um die nächsten Aufgaben auszuführen.</span><span class="sxs-lookup"><span data-stu-id="0b11e-125">Open a command prompt in your project directory to complete the next tasks.</span></span>

[!INCLUDE [node-js-yeoman-gulp-tasks](~/includes/tabs/node-js-yeoman-gulp-tasks.md)]

<span data-ttu-id="0b11e-126">Um Ihre persönliche Registerkarte anzuzeigen, wechseln Sie zu `http://localhost:3007/<yourDefaultAppNameTab>/personal.html`</span><span class="sxs-lookup"><span data-stu-id="0b11e-126">To view your personal tab, go to `http://localhost:3007/<yourDefaultAppNameTab>/personal.html`</span></span>

>![Screenshot der persönlichen Registerkarte](/microsoftteams/platform/assets/images/tab-images/personalTab.PNG)

## <a name="establish-a-secure-tunnel-to-your-tab"></a><span data-ttu-id="0b11e-128">Einrichten eines sicheren Tunnels zu Ihrer Registerkarte</span><span class="sxs-lookup"><span data-stu-id="0b11e-128">Establish a secure tunnel to your tab</span></span>

<span data-ttu-id="0b11e-129">Microsoft Teams ist ein vollständig cloudbasiertes Produkt und erfordert, dass Ihre Registerkarteninhalte über HTTPS-Endpunkte aus der Cloud verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="0b11e-129">Microsoft Teams is an entirely cloud-based product and requires that your tab content be available from the cloud using HTTPS endpoints.</span></span> <span data-ttu-id="0b11e-130">Teams lokales Hosting nicht zulässt, müssen Sie daher Ihre Registerkarte entweder über eine öffentliche URL veröffentlichen oder einen Proxy verwenden, der Ihren lokalen Port für eine mit dem Internet verbundene URL verfügbar macht.</span><span class="sxs-lookup"><span data-stu-id="0b11e-130">Teams doesn't allow local hosting, therefore, you need to either publish your tab to a public URL or use a proxy that will expose your local port to an internet-facing URL.</span></span>

<span data-ttu-id="0b11e-131">Zum Testen der Registerkartenerweiterung verwenden Sie [ngrok,](https://ngrok.com/docs)das in diese Anwendung integriert ist.</span><span class="sxs-lookup"><span data-stu-id="0b11e-131">To test your tab extension, you'll use [ngrok](https://ngrok.com/docs), which is built into this application.</span></span> <span data-ttu-id="0b11e-132">Ngrok ist ein Reverseproxysoftwaretool, das einen Tunnel zu den öffentlich verfügbaren HTTPS-Endpunkten Ihres lokal ausgeführten Webservers erstellt.</span><span class="sxs-lookup"><span data-stu-id="0b11e-132">Ngrok is a reverse proxy software tool that will create a tunnel to your locally running web server's publicly-available HTTPS endpoints.</span></span> <span data-ttu-id="0b11e-133">Die Webendpunkte Ihres Servers sind während der aktuellen Sitzung auf Ihrem lokalen Computer verfügbar.</span><span class="sxs-lookup"><span data-stu-id="0b11e-133">Your server's web endpoints will be available during the current session on your local machine.</span></span> <span data-ttu-id="0b11e-134">Wenn der Computer heruntergefahren wird oder in den Ruhezustand wechselt, ist der Dienst nicht mehr verfügbar.</span><span class="sxs-lookup"><span data-stu-id="0b11e-134">When the machine is shut down or goes to sleep the service will no longer be available.</span></span>

<span data-ttu-id="0b11e-135">Beenden Sie an der Eingabeaufforderung "localhost", und geben Sie Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="0b11e-135">In your command prompt, exit localhost and enter the following:</span></span>

```bash
gulp ngrok-serve
```

> [!IMPORTANT]
> <span data-ttu-id="0b11e-136">Nachdem Ihre Registerkarte über **ngrok** in Microsoft Teams hochgeladen und erfolgreich gespeichert wurde, können Sie sie in Teams anzeigen, bis Ihre Tunnelsitzung endet.</span><span class="sxs-lookup"><span data-stu-id="0b11e-136">After your tab has been uploaded to Microsoft teams, via **ngrok**, and successfully saved, you can view it in Teams until your tunnel session ends.</span></span>

## <a name="upload-your-application-to-teams"></a><span data-ttu-id="0b11e-137">Hochladen Der Anwendung Teams</span><span class="sxs-lookup"><span data-stu-id="0b11e-137">Upload your application to Teams</span></span>

- <span data-ttu-id="0b11e-138">Öffnen Sie den Microsoft Teams Client.</span><span class="sxs-lookup"><span data-stu-id="0b11e-138">Open the Microsoft Teams client.</span></span> <span data-ttu-id="0b11e-139">Wenn Sie die [webbasierte Version](https://teams.microsoft.com) verwenden, können Sie Ihren Front-End-Code mithilfe der [Entwicklertools](~/tabs/how-to/developer-tools.md)Ihres Browsers überprüfen.</span><span class="sxs-lookup"><span data-stu-id="0b11e-139">If you use the [web based version](https://teams.microsoft.com) you can inspect your front-end code using your browser's [developer tools](~/tabs/how-to/developer-tools.md).</span></span>
- <span data-ttu-id="0b11e-140">Wählen Sie im Bereich **"YourTeams"** auf der linken Seite das Menü neben dem Team aus, `...` mit dem Sie Ihre Registerkarte testen, und wählen Sie **"Team verwalten"** aus.</span><span class="sxs-lookup"><span data-stu-id="0b11e-140">In the **YourTeams** panel on the left, select the `...` menu next to the team that you're using to test your tab and choose **Manage team**.</span></span>
- <span data-ttu-id="0b11e-141">Wählen Sie in der Registerkartenleiste im Hauptbereich **Apps** aus, und wählen Sie **Hochladen eine benutzerdefinierte App** in der unteren rechten Ecke der Seite aus.</span><span class="sxs-lookup"><span data-stu-id="0b11e-141">In the main panel select **Apps** from the tab bar and choose **Upload a custom app** located in the lower right-hand corner of the page.</span></span>
- <span data-ttu-id="0b11e-142">Öffnen Sie Ihr Projektverzeichnis, navigieren Sie zum **Ordner "./package",** wählen Sie den ZIP-Ordner aus, klicken Sie mit der rechten Maustaste, und wählen Sie **"Öffnen"** aus.</span><span class="sxs-lookup"><span data-stu-id="0b11e-142">Open your project directory, browse to the **./package** folder, select the zip folder, right-click, and choose **Open**.</span></span> <span data-ttu-id="0b11e-143">Ihre Registerkarte wird in Teams hochgeladen.</span><span class="sxs-lookup"><span data-stu-id="0b11e-143">Your tab will upload into Teams.</span></span>

## <a name="view-your-personal-tabs"></a><span data-ttu-id="0b11e-144">Anzeigen Ihrer persönlichen Registerkarten</span><span class="sxs-lookup"><span data-stu-id="0b11e-144">View your personal tabs</span></span>

<span data-ttu-id="0b11e-145">Wählen Sie in der Navigationsleiste ganz links vom Teams Client das `...` Menü aus, und wählen Sie Ihre App aus der Liste aus.</span><span class="sxs-lookup"><span data-stu-id="0b11e-145">In the navbar located at the far-left of the Teams client, select the `...` menu and choose your app from the list.</span></span>

## <a name="next-step"></a><span data-ttu-id="0b11e-146">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="0b11e-146">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0b11e-147">Erstellen einer persönlichen Registerkarte mit ASP.NETCore</span><span class="sxs-lookup"><span data-stu-id="0b11e-147">Create a personal tab using ASP.NETCore</span></span>](~/tabs/quickstarts/create-personal-tab-dotnet-core.md)
