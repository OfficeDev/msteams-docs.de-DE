---
title: Hinzufügen einer Microsoft Teams-Registerkarte in SharePoint als SPFx-Webpart
author: laujan
description: Vorgehensweise zum Bereitstellen Ihrer vorhandenen Teams-Registerkarte in SharePoint als SharePoint-Framework-WebPart.
keywords: Teams-Registerkarten SharePoint Framework-Entwicklung
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: d7f617f0967743eab84423cd31f78d4700db1c1c
ms.sourcegitcommit: e92408e751a8f51028908ab7e2415a8051a536c0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/01/2020
ms.locfileid: "48326347"
---
# <a name="adding-a-microsoft-teams-tab-in-sharepoint-as-an-spfx-web-part"></a><span data-ttu-id="f0fc1-104">Hinzufügen einer Microsoft Teams-Registerkarte in SharePoint als SPFx-Webpart</span><span class="sxs-lookup"><span data-stu-id="f0fc1-104">Adding a Microsoft Teams tab in SharePoint as an SPFx web part</span></span>

## <a name="rich-integration-between-teams-and-sharepoint"></a><span data-ttu-id="f0fc1-105">Umfassende Integration zwischen Microsoft Teams und SharePoint</span><span class="sxs-lookup"><span data-stu-id="f0fc1-105">Rich integration between Teams and SharePoint</span></span>

<span data-ttu-id="f0fc1-106">Mit der November-Version von Microsoft Teams und SharePoint Framework v.</span><span class="sxs-lookup"><span data-stu-id="f0fc1-106">With the November release of Teams and SharePoint Framework v.</span></span> <span data-ttu-id="f0fc1-107">1,7 haben Entwickler zwei leistungsstarke Funktionen:</span><span class="sxs-lookup"><span data-stu-id="f0fc1-107">1.7, developers have two powerful capabilities:</span></span>

<ul  class="panelContent cardsC">
<li>
    <a href="#introduction">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage bgdAccent1">
                            <img src="~/assets/images/tabs/tabs-in-sharepoint/image084.png" alt="tab-in-sharepoint view"/>
                        </div>
                    </div>
                    <div class="cardText">
                        <h3><span data-ttu-id="f0fc1-108">Teams-Registerkarten in SharePoint</span><span class="sxs-lookup"><span data-stu-id="f0fc1-108">Teams Tabs in SharePoint</span></span></h3>
                        <p><span data-ttu-id="f0fc1-109">Erstellen Sie reichhaltige App-Erlebnisse in SharePoint, indem Sie Ihre Teams-app in SharePoint (diesen Artikel) einbringen.</span><span class="sxs-lookup"><span data-stu-id="f0fc1-109">Create rich app experiences in SharePoint by bringing your Teams app into Sharepoint (this article).</span></span></p>
                    </div>
                </div>
            </div>
        </div>
    </a>
</li>
<li>
    <a href="https://docs.microsoft.com/sharepoint/dev/spfx/web-parts/get-started/using-web-part-as-ms-teams-tab">
        <div class="cardSize">
            <div class="cardPadding">
                <div class="card">
                    <div class="cardImageOuter">
                        <div class="cardImage bgdAccent1">
                            <img src="~/assets/images/tabs/tabs-in-sharepoint/SharePoint-web-part-exposed-as-a-Tab-in-Microsoft-Teams.png" alt="web-part-exposed-as-a-tab" />
                        </div>
                    </div>
                    <div class="cardText">
                        <h3><span data-ttu-id="f0fc1-110">SharePoint-Framework in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="f0fc1-110">SharePoint Framework in Teams</span></span></h3>
                        <p><span data-ttu-id="f0fc1-111">Bringen Sie Ihre SharePoint-Webparts in Microsoft Teams, und lassen Sie SharePoint das Hosting für Sie verwalten.</span><span class="sxs-lookup"><span data-stu-id="f0fc1-111">Bring your SharePoint web parts to Teams and let SharePoint manage the hosting for you.</span></span></p>
                    </div>
                </div>
            </div>
        </div>
    </a>
</li>
</ul>

### <a name="teams-tabs-in-sharepoint"></a><span data-ttu-id="f0fc1-112">Teams-Registerkarten in SharePoint</span><span class="sxs-lookup"><span data-stu-id="f0fc1-112">Teams tabs in SharePoint</span></span>

<span data-ttu-id="f0fc1-113">Mit SharePoint Framework v. 1.7 unterstützen wir nun die Möglichkeit für Entwickler, ihre Teams-Registerkarten zu nehmen und in SharePoint zu hosten.</span><span class="sxs-lookup"><span data-stu-id="f0fc1-113">With SharePoint Framework v.1.7, we’re now supporting the ability for developers to take their Teams tabs and host it in SharePoint.</span></span> <span data-ttu-id="f0fc1-114">Wenn Tabs in SharePoint gehostet werden, erhalten Sie eine ähnliche "ganzseitige" Oberfläche, wobei Sie alle Funktionen von Teams-Registerkarten unter Beibehaltung des Kontexts und der Vertrautheit einer SharePoint-Website verfügbar machen.</span><span class="sxs-lookup"><span data-stu-id="f0fc1-114">As Tabs hosted in SharePoint get a similar "full page" experience, exposing the all the features of Teams tabs while retaining the context and familiarity of a SharePoint site.</span></span>

### <a name="sharepoint-framework-in-teams"></a><span data-ttu-id="f0fc1-115">SharePoint-Framework in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="f0fc1-115">SharePoint Framework in Teams</span></span>

<span data-ttu-id="f0fc1-116">Sie können auch Ihre Microsoft Teams-Registerkarten mit SharePoint Framework implementieren.</span><span class="sxs-lookup"><span data-stu-id="f0fc1-116">You can also implement your Microsoft Teams tabs using SharePoint Framework.</span></span> <span data-ttu-id="f0fc1-117">Für SharePoint-Entwickler wird dadurch der Entwicklungsprozess für Teams-Registerkarten erheblich vereinfacht, da SharePoint-Framework-Webparts in SharePoint gehostet werden, ohne dass externe Dienste wie Azure erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="f0fc1-117">For SharePoint developers, this significantly simplifies the development process for Teams tabs because SharePoint Framework web parts are hosted within SharePoint without any need for external services such as Azure.</span></span> [<span data-ttu-id="f0fc1-118">Erfahren Sie mehr über die Verwendung des SharePoint-Frameworks in Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="f0fc1-118">Learn more about using the SharePoint Framework in Teams.</span></span>](/sharepoint/dev/spfx/web-parts/get-started/using-web-part-as-ms-teams-tab)

## <a name="introduction"></a><span data-ttu-id="f0fc1-119">Einführung</span><span class="sxs-lookup"><span data-stu-id="f0fc1-119">Introduction</span></span>

<span data-ttu-id="f0fc1-120">In diesen Anweisungen wird erklärt, wie Sie eine Registerkarte aus einer Microsoft Teams-Beispiel-app erstellen und in SharePoint verwenden können.</span><span class="sxs-lookup"><span data-stu-id="f0fc1-120">These instructions will explain how you can take a tab from a Microsoft Teams sample app and use it in SharePoint.</span></span> <span data-ttu-id="f0fc1-121">Wir verwenden eine Registerkarte, die bereits auf Azure gehostet wird, um sich auf die erforderliche Integrationsarbeit zu konzentrieren.</span><span class="sxs-lookup"><span data-stu-id="f0fc1-121">We will be using a tab that's already hosted on Azure in order to focus on the required integration work.</span></span>

<span data-ttu-id="f0fc1-122">Die Beispiel-APP, die wir verwenden, ist eine Talent Verwaltungsanwendung.</span><span class="sxs-lookup"><span data-stu-id="f0fc1-122">The sample app we're using is a Talent Management application.</span></span> <span data-ttu-id="f0fc1-123">Es verwaltet den Einstellungsprozess von Kandidaten für offene Positionen in einem Team.</span><span class="sxs-lookup"><span data-stu-id="f0fc1-123">It manages the hiring process of candidates for open positions in a team.</span></span> <span data-ttu-id="f0fc1-124">(Die APP selbst, während Sie nett aussieht, tut tatsächlich nichts.</span><span class="sxs-lookup"><span data-stu-id="f0fc1-124">(The app itself, while it looks nice, doesn't actually do anything.</span></span> <span data-ttu-id="f0fc1-125">Wir möchten uns darauf konzentrieren, eine Teams-APP zu erstellen und Sie in Teams zu laden, ohne eine echte Talent Verwaltungsanwendung zu erstellen.)</span><span class="sxs-lookup"><span data-stu-id="f0fc1-125">We want to focus on building a Teams app and loading it into Teams, not create a real talent management application.)</span></span>

### <a name="benefits-of-this-approach"></a><span data-ttu-id="f0fc1-126">Vorteile dieses Ansatzes</span><span class="sxs-lookup"><span data-stu-id="f0fc1-126">Benefits of this approach</span></span>

- <span data-ttu-id="f0fc1-127">Erreichen von SharePoint-Benutzern mit der Registerkarte "vorhandene Teams"</span><span class="sxs-lookup"><span data-stu-id="f0fc1-127">Reach SharePoint users with your existing Teams tab</span></span>
- <span data-ttu-id="f0fc1-128">Laden Sie Ihr App-Manifest direkt in Ihren SharePoint-App-Katalog hoch.</span><span class="sxs-lookup"><span data-stu-id="f0fc1-128">Upload your app manifest directly to your SharePoint app catalog.</span></span> <span data-ttu-id="f0fc1-129">Microsoft [Teams-Anwendungspakete](~/concepts/build-and-test/apps-package.md) werden jetzt von SharePoint unterstützt</span><span class="sxs-lookup"><span data-stu-id="f0fc1-129">[Teams application packages](~/concepts/build-and-test/apps-package.md) are now supported by SharePoint</span></span>
- <span data-ttu-id="f0fc1-130">Endbenutzer konfigurieren die Registerkarte auf einer Seite genauso wie alle anderen SharePoint-Webparts</span><span class="sxs-lookup"><span data-stu-id="f0fc1-130">End users configure the tab on a page just like any other SharePoint web part</span></span>
- <span data-ttu-id="f0fc1-131">Ihre Registerkarte kann auf Ihren [Kontext](~/tabs/how-to/access-teams-context.md) zugreifen, genauso wie Sie es kann, wenn Sie innerhalb von Teams läuft</span><span class="sxs-lookup"><span data-stu-id="f0fc1-131">Your tab can access its [context](~/tabs/how-to/access-teams-context.md) just as it can when running inside Teams</span></span>

## <a name="step-1-testing-the-sample-app"></a><span data-ttu-id="f0fc1-132">Schritt 1: Testen der Beispiel-App</span><span class="sxs-lookup"><span data-stu-id="f0fc1-132">Step 1: Testing the sample app</span></span>

<span data-ttu-id="f0fc1-133">Laden Sie das Beispiel-App-Manifest von [**hier**](https://github.com/MicrosoftDocs/msteams-docs/raw/master/msteams-platform/assets/downloads/TalentMgmt-Azure.zip)herunter.</span><span class="sxs-lookup"><span data-stu-id="f0fc1-133">Download the sample app manifest from [**here**](https://github.com/MicrosoftDocs/msteams-docs/raw/master/msteams-platform/assets/downloads/TalentMgmt-Azure.zip).</span></span>

<span data-ttu-id="f0fc1-134">Klicken Sie in Microsoft Teams auf das Store-Symbol unten links und dann auf "benutzerdefinierte App hochladen" unten links.</span><span class="sxs-lookup"><span data-stu-id="f0fc1-134">In Microsoft Teams, click on the Store icon at the lower left and then "Upload a custom app" at the lower left.</span></span> <span data-ttu-id="f0fc1-135">Die Datei, die hochgeladen werden soll, befindet sich im Ordner "Downloads"; Es heißt TalentMgmt-Azure.zip.</span><span class="sxs-lookup"><span data-stu-id="f0fc1-135">The file to upload will be located in your Downloads folder; it's called TalentMgmt-Azure.zip.</span></span> <span data-ttu-id="f0fc1-136">Wenn alles gut geht, sehen Sie den Bildschirm "Installation/Zustimmung" für die Talent Management-APP.</span><span class="sxs-lookup"><span data-stu-id="f0fc1-136">If all goes well, you'll see the install/consent screen for the talent management app.</span></span> <span data-ttu-id="f0fc1-137">Wählen Sie das Team aus, das Sie installieren möchten, und klicken Sie auf die Schaltfläche installieren.</span><span class="sxs-lookup"><span data-stu-id="f0fc1-137">Choose the team you want to install to and click the Install button.</span></span> <span data-ttu-id="f0fc1-138">Sie können jetzt mit der APP experimentieren.</span><span class="sxs-lookup"><span data-stu-id="f0fc1-138">You're now free to experiment with the app.</span></span>

## <a name="step-2-using-the-teams-tab-in-sharepoint"></a><span data-ttu-id="f0fc1-139">Schritt 2: Verwenden der Registerkarte "Teams" in SharePoint</span><span class="sxs-lookup"><span data-stu-id="f0fc1-139">Step 2: Using the Teams tab in SharePoint</span></span>

<span data-ttu-id="f0fc1-140">Laden Sie Ihr Teams-App-Paket in Ihren SharePoint-App-Katalog hoch, indem Sie beispielsweise einen Besuch durchsuchen. `https://YOUR_TENANT_NAME.sharepoint.com/sites/apps/AppCatalog/Forms/AllItems.aspx` `https://contoso.sharepoint.com/sites/apps/AppCatalog/Forms/AllItems.aspx`</span><span class="sxs-lookup"><span data-stu-id="f0fc1-140">Upload and deploy your Teams app package to your SharePoint App Catalog by visiting `https://YOUR_TENANT_NAME.sharepoint.com/sites/apps/AppCatalog/Forms/AllItems.aspx`, e.g. `https://contoso.sharepoint.com/sites/apps/AppCatalog/Forms/AllItems.aspx`.</span></span>

<span data-ttu-id="f0fc1-141">Wenn Sie dazu aufgefordert werden, aktivieren Sie die Option "Diese Lösung für alle Websites in der Organisation verfügbar machen":</span><span class="sxs-lookup"><span data-stu-id="f0fc1-141">When prompted, enable "Make this solution available to all sites in the organization":</span></span>

![Registerkarten in der SharePoint-Ansicht](~/assets/images/tabs/tabs-in-sharepoint/image065.png)

<span data-ttu-id="f0fc1-143">Erstellen Sie in Ihrer Website eine neue Seite, indem Sie auf die Schaltfläche Gear oben rechts und dann auf "Seite hinzufügen" klicken:</span><span class="sxs-lookup"><span data-stu-id="f0fc1-143">In your site, create a new page by clicking in the gear button at the upper right and then "Add a page":</span></span>

![SharePoint-Ansicht](~/assets/images/tabs/tabs-in-sharepoint/image066.png)

<span data-ttu-id="f0fc1-145">Die Erstellungsumgebung für SharePoint-Seiten wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="f0fc1-145">You'll see the SharePoint Pages authoring experience.</span></span> <span data-ttu-id="f0fc1-146">Nennen Sie Ihre Seite "meine Teams-Registerkarte".</span><span class="sxs-lookup"><span data-stu-id="f0fc1-146">Name your page "My Teams Tab".</span></span>

<span data-ttu-id="f0fc1-147">Öffnen Sie die Webpart-Toolbox durch Drücken der +-Schaltfläche, und wählen Sie Ihre Teams-Registerkarte ("Contoso HR" genannt) aus.</span><span class="sxs-lookup"><span data-stu-id="f0fc1-147">Open the web part toolbox by pressing the + button, and select your Teams Tab (named "Contoso HR").</span></span> <span data-ttu-id="f0fc1-148">Webparts werden alphabetisch sortiert; Wenn es sich um eine lange Liste handelt, können Sie die Suchleiste verwenden, um Sie zu finden.</span><span class="sxs-lookup"><span data-stu-id="f0fc1-148">Web parts are sorted alphabetically; if it's a long list, you can use the search bar to find it.</span></span> <span data-ttu-id="f0fc1-149">Dadurch wird ein Webpart im Canvas-Bereich erstellt, der die Registerkarte Teams enthält:</span><span class="sxs-lookup"><span data-stu-id="f0fc1-149">This will create a web part in the canvas that contains your Teams tab:</span></span>

![Registerkartenansicht](~/assets/images/tabs/tabs-in-sharepoint/image071.png)

<span data-ttu-id="f0fc1-151">Drücken Sie die Schaltfläche "veröffentlichen", wenn Sie die Bearbeitung abgeschlossen haben.</span><span class="sxs-lookup"><span data-stu-id="f0fc1-151">Press the "Publish" button when you are finished editing.</span></span>

<span data-ttu-id="f0fc1-152">Möglicherweise möchten Sie auf "Seite zur Navigation hinzufügen" klicken, um in der linken Navigationsleiste eine Kurzübersicht zu Ihrer Seite zu haben:</span><span class="sxs-lookup"><span data-stu-id="f0fc1-152">You may want to click "Add page to navigation" to have a quick reference to your page in the left navigation bar:</span></span>

![Registerkarte in SharePoint-Bild](~/assets/images/tabs/tabs-in-sharepoint/image073.png)

## <a name="step-3-explore-app-pages-in-sharepoint"></a><span data-ttu-id="f0fc1-154">Schritt 3: Durchsuchen von App-Seiten in SharePoint</span><span class="sxs-lookup"><span data-stu-id="f0fc1-154">Step 3: Explore App Pages in SharePoint</span></span>

<span data-ttu-id="f0fc1-155">Nachdem Sie Ihre Seite veröffentlicht haben, können Sie [Ihre Teams-app in eine umfassendere Erfahrung in SharePoint umwandeln](/sharepoint/dev/spfx/web-parts/single-part-app-pages).</span><span class="sxs-lookup"><span data-stu-id="f0fc1-155">Once your page is published, you can explore [turning your Teams app into a more complete experience inside SharePoint](/sharepoint/dev/spfx/web-parts/single-part-app-pages).</span></span> <span data-ttu-id="f0fc1-156">Dadurch wird die aktuelle Seite in eine APP-Seite umgewandelt, die das normale SharePoint-Seitenlayout mit einer ganzseitigen Oberfläche für die Registerkarte "Teams" zeigt:</span><span class="sxs-lookup"><span data-stu-id="f0fc1-156">This converts the current page into an App Page, showing the normal SharePoint page layout with a full-page experience for the Teams tab:</span></span>

![Bild von Registerkarten in SharePoint](~/assets/images/tabs/tabs-in-sharepoint/image085.png)

## <a name="more-information"></a><span data-ttu-id="f0fc1-158">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="f0fc1-158">More information</span></span>

- [<span data-ttu-id="f0fc1-159">Erstellen von Microsoft Teams-Registerkarten mit SharePoint Framework – Lernprogramm</span><span class="sxs-lookup"><span data-stu-id="f0fc1-159">Building Microsoft Teams tab using SharePoint Framework - Tutorial</span></span>](/sharepoint/dev/spfx/web-parts/get-started/using-web-part-as-ms-teams-tab)
- [<span data-ttu-id="f0fc1-160">Verwenden von App-Seiten mit einem einzelne Part in SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="f0fc1-160">Using single part app pages in SharePoint Online</span></span>](/sharepoint/dev/spfx/web-parts/single-part-app-pages)
