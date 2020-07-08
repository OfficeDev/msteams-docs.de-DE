---
title: Erstellen von apps mit dem Microsoft Teams-Toolkit und Visual Studio
description: Erste Schritte beim Erstellen großartiger benutzerdefinierter apps direkt in Visual Studio mit dem Microsoft Teams-Toolkit
keywords: Teams Visual Studio Toolkit
ms.date: 06/30/2020
ms.openlocfilehash: e5715cf23cfd221b65afe0e6258ce06ff98770aa
ms.sourcegitcommit: 694babb79d379360a20cf928a9d2b88dd6d3bdd0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/07/2020
ms.locfileid: "45051722"
---
# <a name="build-apps-with-the-microsoft-teams-toolkit-and-visual-studio"></a><span data-ttu-id="b6840-104">Erstellen von apps mit dem Microsoft Teams-Toolkit und Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b6840-104">Build apps with the Microsoft Teams Toolkit and Visual Studio</span></span>

<span data-ttu-id="b6840-105">Mit dem Microsoft Teams-Toolkit können Sie benutzerdefinierte Teams-apps direkt in der Visual Studio Umgebung erstellen.</span><span class="sxs-lookup"><span data-stu-id="b6840-105">The Microsoft Teams Toolkit enables you to create custom Teams apps directly within the Visual Studio environment.</span></span> <span data-ttu-id="b6840-106">Das Toolkit führt Sie durch den Prozess und bietet alles, was Sie zum Erstellen, Debuggen und starten ihrer Teams-App benötigen.</span><span class="sxs-lookup"><span data-stu-id="b6840-106">The toolkit guides you through the process and provides everything you need to build, debug, and launch your Teams app.</span></span>

## <a name="installing-the-teams-toolkit"></a><span data-ttu-id="b6840-107">Installieren des Teams-Toolkits</span><span class="sxs-lookup"><span data-stu-id="b6840-107">Installing the Teams Toolkit</span></span>

<span data-ttu-id="b6840-108">Das Microsoft Teams-Toolkit für Visual Studio steht vom [Visual Studio Marketplace](https://aka.ms/teams-toolkit) oder direkt als Erweiterung innerhalb von Visual Studio zum Download bereit.</span><span class="sxs-lookup"><span data-stu-id="b6840-108">The Microsoft Teams Toolkit for Visual Studio is available for download from the [Visual Studio Marketplace](https://aka.ms/teams-toolkit) or directly as an extension within Visual Studio.</span></span>

## <a name="using-the-toolkit"></a><span data-ttu-id="b6840-109">Verwenden des Toolkits</span><span class="sxs-lookup"><span data-stu-id="b6840-109">Using the toolkit</span></span>

- [<span data-ttu-id="b6840-110">Einrichten eines neuen Projekts</span><span class="sxs-lookup"><span data-stu-id="b6840-110">Set up a new project</span></span>](#set-up-a-new-teams-project)
- [<span data-ttu-id="b6840-111">Konfigurieren Sie die App</span><span class="sxs-lookup"><span data-stu-id="b6840-111">Configure your app</span></span>](#configure-your-app)
- [<span data-ttu-id="b6840-112">Verpacken Ihrer APP</span><span class="sxs-lookup"><span data-stu-id="b6840-112">Package your app</span></span>](#package-your-app)
- [<span data-ttu-id="b6840-113">Ausführen ihrer app in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="b6840-113">Run your app in Teams</span></span>](#install-and-run-your-app-locally)
- [<span data-ttu-id="b6840-114">Überprüfen Ihrer APP</span><span class="sxs-lookup"><span data-stu-id="b6840-114">Validate your app</span></span>](#validate-your-app)
- [<span data-ttu-id="b6840-115">Veröffentlichen Ihrer APP</span><span class="sxs-lookup"><span data-stu-id="b6840-115">Publish your app</span></span>](#publish-your-app-to-teams)

## <a name="set-up-a-new-teams-project"></a><span data-ttu-id="b6840-116">Einrichten eines neuen Teams-Projekts</span><span class="sxs-lookup"><span data-stu-id="b6840-116">Set up a new Teams project</span></span>

1. <span data-ttu-id="b6840-117">Erstellen Sie ein neues Projekt, und wählen Sie die Vorlage Microsoft Terams Toolkit aus.</span><span class="sxs-lookup"><span data-stu-id="b6840-117">Create a new project and select the Microsoft Terams Toolkit template.</span></span>
1. <span data-ttu-id="b6840-118">Sie gelangen auf den Bildschirm **Funktionen hinzufügen** Konfigurieren der Eigenschaften für Ihre neue APP.</span><span class="sxs-lookup"><span data-stu-id="b6840-118">You will arrive at the **Add capabilities** screen configure the properties for your new app.</span></span>
1. <span data-ttu-id="b6840-119">Klicken Sie auf die Schaltfläche **Fertig stellen** , um den Konfigurationsprozess abzuschließen.</span><span class="sxs-lookup"><span data-stu-id="b6840-119">Select the **Finish** button to complete the configuration process.</span></span>

## <a name="configure-your-app"></a><span data-ttu-id="b6840-120">Konfigurieren Sie die App</span><span class="sxs-lookup"><span data-stu-id="b6840-120">Configure your app</span></span>

<span data-ttu-id="b6840-121">Im Kern umfasst die Teams-app drei Komponenten:</span><span class="sxs-lookup"><span data-stu-id="b6840-121">At its core, the Teams app embraces three components:</span></span>

  1. <span data-ttu-id="b6840-122">Der Microsoft Teams-Client ("Internet", "Desktop" oder "Mobil"), auf dem Benutzer mit Ihrer APP interagieren.</span><span class="sxs-lookup"><span data-stu-id="b6840-122">The Microsoft Teams client (web, desktop or mobile) where users interact with your app.</span></span>
  1. <span data-ttu-id="b6840-123">Ein Server, der auf Anforderungen für Inhalte reagiert, die in Microsoft Teams angezeigt werden, beispielsweise HTML-Registerkarteninhalte oder eine bot-Adaptive Karte.</span><span class="sxs-lookup"><span data-stu-id="b6840-123">A server that responds to requests for content that will be displayed in Teams, e.g., HTML tab content or a bot adaptive card .</span></span>
  1. <span data-ttu-id="b6840-124">Ein Teams- [App-Paket](/concepts/build-and-test/apps-package.md) , bestehend aus drei Dateien:</span><span class="sxs-lookup"><span data-stu-id="b6840-124">A Teams [app package](/concepts/build-and-test/apps-package.md) consisting of three files:</span></span>

  > [!div class="checklist"]
  >
  > - <span data-ttu-id="b6840-125">Die manifest.jsauf</span><span class="sxs-lookup"><span data-stu-id="b6840-125">The manifest.json</span></span> 
  > - <span data-ttu-id="b6840-126">Ein [Farbsymbol](../resources/schema/manifest-schema.md#icons) für Ihre APP, das im öffentlichen oder im Organisations-App-Katalog angezeigt wird</span><span class="sxs-lookup"><span data-stu-id="b6840-126">A [color icon](../resources/schema/manifest-schema.md#icons) for your app to display in the public or organization app catalog</span></span>
 > - <span data-ttu-id="b6840-127">Ein [Gliederungssymbol](../resources/schema/manifest-schema.md#icons) für die Anzeige in der Microsoft Teams-Aktivitäts Leiste.</span><span class="sxs-lookup"><span data-stu-id="b6840-127">An [outline icon](../resources/schema/manifest-schema.md#icons) for display on the Teams activity bar.</span></span>

<span data-ttu-id="b6840-128">Wenn eine APP installiert ist, analysiert der Microsoft Teams-Client die Manifestdatei, um benötigte Informationen wie den Namen Ihrer APP und die URL zu ermitteln, in der sich die Dienste befinden.</span><span class="sxs-lookup"><span data-stu-id="b6840-128">When an app is installed, the Teams client parses the manifest file to determine needed information like the name of your app and the URL where the services are located.</span></span>

1. <span data-ttu-id="b6840-129">Um Ihre APP zu konfigurieren, navigieren Sie zum **Microsoft Teams Toolkit** -Erweiterungsfenster.</span><span class="sxs-lookup"><span data-stu-id="b6840-129">To configure your app, navigate to the **Microsoft Teams Toolkit** extension window.</span></span>
1. <span data-ttu-id="b6840-130">Wählen Sie **App-Paket bearbeiten** aus, um die Seite **App-Details** anzuzeigen.</span><span class="sxs-lookup"><span data-stu-id="b6840-130">Select **Edit app package** to view the **App details** page.</span></span>
1. <span data-ttu-id="b6840-131">Durch das Bearbeiten der Felder auf der Seite mit den App-Details wird der Inhalt der manifest.jsauf Datei aktualisiert, die letztendlich als Teil des App-Pakets ausgeliefert wird.</span><span class="sxs-lookup"><span data-stu-id="b6840-131">Editing the fields in the App details page updates the contents of the manifest.json file that will ultimately ship as part of the app package.</span></span> [<span data-ttu-id="b6840-132">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="b6840-132">Learn more</span></span>](https://aka.ms/teams-toolkit-manifest)

## <a name="package-your-app"></a><span data-ttu-id="b6840-133">Verpacken Ihrer APP</span><span class="sxs-lookup"><span data-stu-id="b6840-133">Package your app</span></span>

<span data-ttu-id="b6840-134">Wenn Sie die Seite " **App-Details** " ändern oder das **Manifest**oder **. env** -Dateien im Ordner " **. Publish** " Ihrer APP aktualisieren, wird die **Development.zip** Datei automatisch generiert.</span><span class="sxs-lookup"><span data-stu-id="b6840-134">Modifying your the **app details** page or updating the **manifest**, or **.env** files in your app's  **.publish** folder will automatically generate your **Development.zip** file.</span></span> <span data-ttu-id="b6840-135">Sie müssen [zwei Symbole](../concepts/build-and-test/apps-package.md#icons) in den gleichen Ordner einschließen.</span><span class="sxs-lookup"><span data-stu-id="b6840-135">You'll need to include [two icons](../concepts/build-and-test/apps-package.md#icons) in that same folder.</span></span>

## <a name="install-and-run-your-app-locally"></a><span data-ttu-id="b6840-136">Lokal installieren und Ausführen der APP</span><span class="sxs-lookup"><span data-stu-id="b6840-136">Install and run your app locally</span></span>

<span data-ttu-id="b6840-137">Wählen Sie im Dropdownmenü *Lösungs Konfigurationen* die Option *Bereitstellen*aus.</span><span class="sxs-lookup"><span data-stu-id="b6840-137">From the *Solutions Configurations* dropdown menu, select *Deploy*.</span></span> <span data-ttu-id="b6840-138">Drücken Sie die Schaltfläche *ISS Express + Teams* .</span><span class="sxs-lookup"><span data-stu-id="b6840-138">Press the *ISS Express + Teams* button.</span></span> <span data-ttu-id="b6840-139">Microsoft Teams wird gestartet, und der APP-Installationsdialog sollte im Microsoft Teams-Client angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="b6840-139">Teams will launch and the app installation dialogue should appear in the Teams client.</span></span>

## <a name="validate-your-app"></a><span data-ttu-id="b6840-140">Überprüfen Ihrer APP</span><span class="sxs-lookup"><span data-stu-id="b6840-140">Validate your app</span></span>

<span data-ttu-id="b6840-141">Auf der Seite über **prüfen** können Sie Ihr App-Paket überprüfen, bevor Sie Ihre APP an AppSource senden.</span><span class="sxs-lookup"><span data-stu-id="b6840-141">The **Validate** page allows you to check your app package before submitting your app to AppSource.</span></span> <span data-ttu-id="b6840-142">Laden Sie einfach das Manifest-Paket hoch, und das Überprüfungstool überprüft Ihre APP mit allen Manifest-bezogenen Testfällen.</span><span class="sxs-lookup"><span data-stu-id="b6840-142">Simply upload the manifest package and the validation tool will check your app against all manifest related test cases.</span></span> <span data-ttu-id="b6840-143">Bei jedem fehlgeschlagenen Test enthält die Beschreibung einen Link zur Dokumentation, mit dem Sie den Fehler beheben können.</span><span class="sxs-lookup"><span data-stu-id="b6840-143">For each failed tests, the description provides a documentation link to help you fix the error.</span></span> <span data-ttu-id="b6840-144">Bei den Tests, die schwer zu automatisieren sind, werden in der **vorläufigen Prüfliste** 7 der häufigsten fehlgeschlagenen Testfälle sowie Links zu einer vollständigen Übermittlungs Prüfliste aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="b6840-144">For the tests that are hard to automate, the **Preliminary checklist** details 7 of the most common failed test cases as well as link to a complete submission checklist.</span></span>

## <a name="publish-your-app-to-teams"></a><span data-ttu-id="b6840-145">Veröffentlichen Ihrer APP in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="b6840-145">Publish your app to Teams</span></span>

<span data-ttu-id="b6840-146">Auf Ihrer Project-Startseite können Sie Ihre APP in ein Team hochladen, Ihre APP für Benutzer in Ihrer Organisation an den benutzerdefinierten APP-Speicher des Unternehmens übermitteln oder Ihre APP an die APP-Quelle für alle Microsoft Teams-Benutzer senden.</span><span class="sxs-lookup"><span data-stu-id="b6840-146">On your project home page, you can upload your app to a team, submit your app to your company custom app store for users in your organization, or submit your app to App Source for all Teams users.</span></span> <span data-ttu-id="b6840-147">Ihr IT-Administrator prüft diese Übermittlungen.</span><span class="sxs-lookup"><span data-stu-id="b6840-147">Your IT admin will review these submissions.</span></span> <span data-ttu-id="b6840-148">Sie können zur Seite *veröffentlichen* zurückkehren, um den Übermittlungsstatus zu überprüfen und zu erfahren, ob Ihre APP von Ihrem IT-Administrator genehmigt oder abgelehnt wurde. In diesem Fall können Sie auch Aktualisierungen an Ihre APP übermitteln oder derzeit aktive Übermittlungen kündigen.</span><span class="sxs-lookup"><span data-stu-id="b6840-148">You can return to the *Publish* page to check on your submission status and learn if your app was approved or rejected by your IT admin. This is also where you'll come to submit updates to your app or cancel any currently active submissions.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="b6840-149">Nächster Schritt: Verwalten und unterstützen Ihrer veröffentlichten App</span><span class="sxs-lookup"><span data-stu-id="b6840-149">Next step: Maintaining and supporting your published app</span></span>](../concepts/deploy-and-publish/appsource/post-publish/overview.md)
