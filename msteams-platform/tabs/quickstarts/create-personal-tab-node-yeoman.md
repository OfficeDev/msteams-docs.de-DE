---
title: 'Schnellstart: Erstellen einer benutzerdefinierten persönlichen Registerkarte mit Node. js und dem Generator für Microsoft Teams'
author: laujan
description: Eine Schnellstartanleitung zum Erstellen einer persönlichen Registerkarte mit dem Landarbeits Generator für Microsoft Teams.
ms.topic: quickstart
ms.author: laujan
ms.openlocfilehash: 2d1b17360b92a161179091c1f6ba06ffa194e958
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674075"
---
# <a name="quickstart-create-a-custom-personal-tab-with-nodejs-and-the-yeoman-generator-for-microsoft-teams"></a><span data-ttu-id="5813a-103">Schnellstart: Erstellen einer benutzerdefinierten persönlichen Registerkarte mit Node. js und dem Generator für Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="5813a-103">Quickstart: Create a custom personal tab with Node.js and the Yeoman Generator for Microsoft Teams</span></span>

>[!NOTE]
><span data-ttu-id="5813a-104">Diese Schnellstartleiste folgt den Schritten im Artikel [Erstellen des ersten Microsoft Teams-App](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App) -Wikis, die im Microsoft officedev GitHub-Repository gefunden wurden.</span><span class="sxs-lookup"><span data-stu-id="5813a-104">This quickstart follows the steps outlined in the [Build Your First Microsoft Teams App](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App) Wiki found in the Microsoft OfficeDev GitHub repository.</span></span>

<span data-ttu-id="5813a-105">In diesem Schnellstart werden Sie durch das Erstellen einer benutzerdefinierten persönlichen Registerkarte mithilfe des Teams-Landarbeits- [Generators](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App)gehen.</span><span class="sxs-lookup"><span data-stu-id="5813a-105">In this quickstart we'll walk-through creating a custom personal tab using the [Teams Yeoman generator](https://github.com/OfficeDev/generator-teams/wiki/Build-Your-First-Microsoft-Teams-App).</span></span> <span data-ttu-id="5813a-106">Wir laden die Anwendung auch in Team hoch.</span><span class="sxs-lookup"><span data-stu-id="5813a-106">We'll also upload the application to Team.</span></span>

[!INCLUDE [node-js-yeoman-prereq](~/includes/tabs/node-js-yeoman-prereq.md)]

<span data-ttu-id="5813a-107">**Möchten Sie eine konfigurierbare oder statische RegisterkarteErstellen?**</span><span class="sxs-lookup"><span data-stu-id="5813a-107">**Do you want to create a configurable or static tab?**</span></span>

<span data-ttu-id="5813a-108">Verwenden Sie die Pfeiltasten, um statische Registerkarte auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="5813a-108">Use the arrow keys to select static tab.</span></span>

>[!IMPORTANT]
><span data-ttu-id="5813a-109">In der Pfadkomponente *yourDefaultTabNameTab*, auf die in diesem Schnellstart verwiesen wird, handelt es sich um den Wert, den Sie im Generator für den *standardmäßigen Registerkartennamen* sowie die *Register*Karte Word eingegeben haben.</span><span class="sxs-lookup"><span data-stu-id="5813a-109">The path component *yourDefaultTabNameTab*, referenced in this quickstart, is the value that you entered in the generator for *Default Tab Name* plus the word *Tab*.</span></span>
>
><span data-ttu-id="5813a-110">Beispiel: DefaultTabName: *mytab* => */MyTabTab/*</span><span class="sxs-lookup"><span data-stu-id="5813a-110">For example: DefaultTabName: *MyTab* => */MyTabTab/*</span></span>

## <a name="create-your-personal-tab"></a><span data-ttu-id="5813a-111">Erstellen Ihrer persönlichen Registerkarte</span><span class="sxs-lookup"><span data-stu-id="5813a-111">Create your personal tab</span></span>

<span data-ttu-id="5813a-112">Zum Hinzufügen einer persönlichen Registerkarte zu dieser Anwendung erstellen Sie eine Inhaltsseite und aktualisieren vorhandene Dateien:</span><span class="sxs-lookup"><span data-stu-id="5813a-112">To add a personal tab to this application you'll create a content page and update existing files:</span></span>

- <span data-ttu-id="5813a-113">Erstellen Sie in Ihrem Code-Editor eine neue HTML-Datei **Personal. html** , und fügen Sie das folgende Markup hinzu:</span><span class="sxs-lookup"><span data-stu-id="5813a-113">In your code editor, create a new HTML file, **personal.html** and add the following markup:</span></span>

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

- <span data-ttu-id="5813a-114">Speichern Sie **Personal. html** im **Webordner ihrer** Anwendung:</span><span class="sxs-lookup"><span data-stu-id="5813a-114">Save **personal.html** in your application's **web** folder:</span></span>

```bash
./src/app/web/<yourDefaultTabNameTab>/personal.html
```

- <span data-ttu-id="5813a-115">Öffnen Sie **Manifest. JSON** in Ihrem Code-Editor:</span><span class="sxs-lookup"><span data-stu-id="5813a-115">Open **manifest.json** in your code editor:</span></span>

```bash
./src/manifest/manifest.json/
```

<span data-ttu-id="5813a-116">Fügen Sie Folgendes zum leeren `staticTabs` Array hinzu (`staticTabs":[]`), und fügen Sie das folgende JSON-Objekt hinzu:</span><span class="sxs-lookup"><span data-stu-id="5813a-116">Add the following to the empty `staticTabs` array (`staticTabs":[]`) and add the following JSON object:</span></span>

```json
{
    "entityId": "personalTab",
    "name": "Personal Tab ",
    "contentUrl": "https://{{HOSTNAME}}/<yourDefaultTabNameTab>/personal.html",
    "websiteUrl": "https://{{HOSTNAME}}",
    "scopes": ["personal"]
}

```

<span data-ttu-id="5813a-117">Denken Sie daran, die **"contentURL"** -Pfadkomponente **yourDefaultTabNameTab** mit Ihrem tatsächlichen Registerkartennamen zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="5813a-117">Remember to update the **"contentURL"** path component **yourDefaultTabNameTab** with your actual tab name.</span></span>

- <span data-ttu-id="5813a-118">Speichern Sie die aktualisierte **Manifest. JSON**.</span><span class="sxs-lookup"><span data-stu-id="5813a-118">Save the updated **manifest.json**.</span></span>

- <span data-ttu-id="5813a-119">Die Inhaltsseite muss in einem IFRAME bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="5813a-119">Your content page must be served in an IFrame.</span></span> <span data-ttu-id="5813a-120">Öffnen Sie **Tab. TS** in Ihrem Code-Editor:</span><span class="sxs-lookup"><span data-stu-id="5813a-120">Open **Tab.ts** in your code editor:</span></span>

 ```bash
./src/app/<yourDefaultTabNameTab>/<yourDefaultTabNameTab>.ts
```

- <span data-ttu-id="5813a-121">Fügen Sie der Liste der iframe-Dekorateure Folgendes hinzu:</span><span class="sxs-lookup"><span data-stu-id="5813a-121">Add the following to the list of IFrame decorators:</span></span>

```typescript
 @PreventIframe("/<yourDefaultAppName>TabNameTab>/personal.html")
```

- <span data-ttu-id="5813a-122">Achten Sie darauf, die aktualisierte **Registerkarte. TS** -Datei zu speichern.</span><span class="sxs-lookup"><span data-stu-id="5813a-122">Make sure to save the updated **Tab.ts** file.</span></span> <span data-ttu-id="5813a-123">Der Tab-Code ist abgeschlossen.</span><span class="sxs-lookup"><span data-stu-id="5813a-123">Your tab code is complete.</span></span>

## <a name="build-and-run-your-application"></a><span data-ttu-id="5813a-124">Erstellen und Ausführen der Anwendung</span><span class="sxs-lookup"><span data-stu-id="5813a-124">Build and Run Your Application</span></span>

<span data-ttu-id="5813a-125">Öffnen Sie im Projektverzeichnis eine Eingabeaufforderung, um die nächsten Aufgaben abzuschließen.</span><span class="sxs-lookup"><span data-stu-id="5813a-125">Open a command prompt in your project directory to complete the next tasks.</span></span>

[!INCLUDE [node-js-yeoman-gulp-tasks](~/includes/tabs/node-js-yeoman-gulp-tasks.md)]

<span data-ttu-id="5813a-126">Um Ihre persönliche Registerkarte anzuzeigen, wechseln Sie zu`http://localhost:3007/<yourDefaultAppNameTab>/personal.html`</span><span class="sxs-lookup"><span data-stu-id="5813a-126">To view your personal tab, go to `http://localhost:3007/<yourDefaultAppNameTab>/personal.html`</span></span>

>![Screenshot der persönlichen Registerkarte](/microsoftteams/platform/assets/images/tab-images/personalTab.PNG)

## <a name="establish-a-secure-tunnel-to-your-tab"></a><span data-ttu-id="5813a-128">Einrichten eines sicheren Tunnels für die Registerkarte</span><span class="sxs-lookup"><span data-stu-id="5813a-128">Establish a secure tunnel to your tab</span></span>

<span data-ttu-id="5813a-129">Microsoft Teams ist ein vollständig Cloud-basiertes Produkt und erfordert, dass Ihre Registerkarteninhalte über HTTPS-Endpunkte in der Cloud verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="5813a-129">Microsoft Teams is an entirely cloud-based product and requires that your tab content be available from the cloud using HTTPS endpoints.</span></span> <span data-ttu-id="5813a-130">Teams nicht zulassen lokales Hosting daher müssen Sie entweder Ihre Registerkarte in einer öffentlichen URL veröffentlichen oder einen Proxy verwenden, der den lokalen Port einer URL mit Internetverbindung verfügbar macht.</span><span class="sxs-lookup"><span data-stu-id="5813a-130">Teams doesn't allow local hosting, therefore, you need to either publish your tab to a public URL or use a proxy that will expose your local port to an internet-facing URL.</span></span>

<span data-ttu-id="5813a-131">Um Ihre Tab-Erweiterung zu testen, verwenden Sie [ngrok](https://ngrok.com/docs), das in diese Anwendung integriert ist.</span><span class="sxs-lookup"><span data-stu-id="5813a-131">To test your tab extension, you'll use [ngrok](https://ngrok.com/docs), which is built into this application.</span></span> <span data-ttu-id="5813a-132">Ngrok ist ein Reverse-Proxy-Software Tool, mit dem ein Tunnel zu den öffentlich verfügbaren HTTPS-Endpunkten des lokal ausgeführten Webservers erstellt wird.</span><span class="sxs-lookup"><span data-stu-id="5813a-132">Ngrok is a reverse proxy software tool that will create a tunnel to your locally running web server's publicly-available HTTPS endpoints.</span></span> <span data-ttu-id="5813a-133">Die Webendpunkte Ihres Servers sind während der aktuellen Sitzung auf Ihrem lokalen Computer verfügbar.</span><span class="sxs-lookup"><span data-stu-id="5813a-133">Your server's web endpoints will be available during the current session on your local machine.</span></span> <span data-ttu-id="5813a-134">Wenn der Computer heruntergefahren wird oder in den Standbymodus wechselt, steht der Dienst nicht mehr zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="5813a-134">When the machine is shut down or goes to sleep the service will no longer be available.</span></span>

<span data-ttu-id="5813a-135">Beenden Sie in der Eingabeaufforderung localhost, und geben Sie Folgendes ein:</span><span class="sxs-lookup"><span data-stu-id="5813a-135">In your command prompt, exit localhost and enter the following:</span></span>

```bash
gulp ngrok-serve
```

> [!IMPORTANT]
> <span data-ttu-id="5813a-136">Nachdem die Registerkarte über *ngrok*in Microsoft Teams hochgeladen und erfolgreich gespeichert wurde, können Sie Sie in Teams anzeigen, bis Ihre Tunnelsitzung endet.</span><span class="sxs-lookup"><span data-stu-id="5813a-136">After your tab has been uploaded to Microsoft teams, via *ngrok*, and successfully saved, you can view it in Teams until your tunnel session ends.</span></span>

## <a name="upload-your-application-to-teams"></a><span data-ttu-id="5813a-137">Hochladen Ihrer Anwendung in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="5813a-137">Upload your application to Teams</span></span>

- <span data-ttu-id="5813a-138">Öffnen Sie den Microsoft Teams-Client.</span><span class="sxs-lookup"><span data-stu-id="5813a-138">Open the Microsoft Teams client.</span></span> <span data-ttu-id="5813a-139">Wenn Sie die [webbasierte Version](https://teams.microsoft.com) verwenden, können Sie den Front-End-Code mithilfe der [Entwicklertools](~/tabs/how-to/developer-tools.md)Ihres Browsers überprüfen.</span><span class="sxs-lookup"><span data-stu-id="5813a-139">If you use the [web based version](https://teams.microsoft.com) you can inspect your front-end code using your browser's [developer tools](~/tabs/how-to/developer-tools.md).</span></span>
- <span data-ttu-id="5813a-140">Wählen Sie im *YourTeams* -Bereich auf der linken Seite `...` das Menü neben dem Team aus, das Sie zum Testen der Registerkarte verwenden, und wählen Sie **Team verwalten**aus.</span><span class="sxs-lookup"><span data-stu-id="5813a-140">In the *YourTeams* panel on the left, select the `...` menu next to the team that you're using to test your tab and choose **Manage team**.</span></span>
- <span data-ttu-id="5813a-141">Wählen Sie im Hauptbereich **apps** in der Registerkartenleiste aus, und wählen Sie **eine benutzerdefinierte App hochladen** , die sich in der unteren rechten Ecke der Seite befindet.</span><span class="sxs-lookup"><span data-stu-id="5813a-141">In the main panel select **Apps** from the tab bar and choose **Upload a custom app** located in the lower right-hand corner of the page.</span></span>
- <span data-ttu-id="5813a-142">Öffnen Sie Ihr Projektverzeichnis, navigieren Sie zum Ordner **./Paket** , wählen Sie den Ordner zip aus, klicken Sie mit der rechten Maustaste, und wählen Sie **Öffnen**aus.</span><span class="sxs-lookup"><span data-stu-id="5813a-142">Open your project directory, browse to the **./package** folder, select the zip folder, right-click, and choose **Open**.</span></span> <span data-ttu-id="5813a-143">Ihre Registerkarte wird in Teams hochgeladen.</span><span class="sxs-lookup"><span data-stu-id="5813a-143">Your tab will upload into Teams.</span></span>

## <a name="view-your-personal-tabs"></a><span data-ttu-id="5813a-144">Anzeigen Ihrer persönlichen Registerkarten</span><span class="sxs-lookup"><span data-stu-id="5813a-144">View your personal tabs</span></span>

<span data-ttu-id="5813a-145">Wählen Sie in der navbar, die sich auf der linken Seite des Teams-Clients `...` befindet, das Menü aus, und wählen Sie Ihre APP aus der Liste aus.</span><span class="sxs-lookup"><span data-stu-id="5813a-145">In the navbar located at the far-left of the Teams client, select the `...` menu and choose your app from the list.</span></span>
