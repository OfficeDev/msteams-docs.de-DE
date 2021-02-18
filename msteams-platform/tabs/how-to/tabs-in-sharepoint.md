---
title: Hinzufügen einer Microsoft Teams-Registerkarte in SharePoint als ein SPFx-Web part
author: laujan
description: Bereitstellen Ihrer vorhandenen Registerkarte "Teams" in SharePoint als SharePoint-Framework-Web part.
keywords: Teams-Registerkarten- SharePoint-Framework-Entwicklung
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 2e5d1b01aa5f7566e25c7720d6a0539386226576
ms.sourcegitcommit: 6caf503de5544fb8b9c8c6bef8eff4ff5a46068c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/17/2021
ms.locfileid: "50270791"
---
# <a name="adding-a-microsoft-teams-tab-in-sharepoint-as-an-spfx-web-part"></a><span data-ttu-id="1f4a1-104">Hinzufügen einer Microsoft Teams-Registerkarte in SharePoint als ein SPFx-Web part</span><span class="sxs-lookup"><span data-stu-id="1f4a1-104">Adding a Microsoft Teams tab in SharePoint as an SPFx web part</span></span>

## <a name="rich-integration-between-teams-and-sharepoint"></a><span data-ttu-id="1f4a1-105">Umfassende Integration zwischen Teams und SharePoint</span><span class="sxs-lookup"><span data-stu-id="1f4a1-105">Rich integration between Teams and SharePoint</span></span>

<span data-ttu-id="1f4a1-106">Mit der Novemberversion von Teams und SharePoint Framework v.</span><span class="sxs-lookup"><span data-stu-id="1f4a1-106">With the November release of Teams and SharePoint Framework v.</span></span> <span data-ttu-id="1f4a1-107">1.7, Entwickler verfügen über zwei leistungsstarke Funktionen:</span><span class="sxs-lookup"><span data-stu-id="1f4a1-107">1.7, developers have two powerful capabilities:</span></span>

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
                        <h3><span data-ttu-id="1f4a1-108">Registerkarten für Teams in SharePoint</span><span class="sxs-lookup"><span data-stu-id="1f4a1-108">Teams Tabs in SharePoint</span></span></h3>
                        <p><span data-ttu-id="1f4a1-109">Erstellen Sie umfangreiche App-Erfahrungen in SharePoint, indem Sie Ihre Teams-App in SharePoint (dieser Artikel) bringen.</span><span class="sxs-lookup"><span data-stu-id="1f4a1-109">Create rich app experiences in SharePoint by bringing your Teams app into Sharepoint (this article).</span></span></p>
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
                        <h3><span data-ttu-id="1f4a1-110">SharePoint Framework in Teams</span><span class="sxs-lookup"><span data-stu-id="1f4a1-110">SharePoint Framework in Teams</span></span></h3>
                        <p><span data-ttu-id="1f4a1-111">Bring your SharePoint web parts to Teams and let SharePoint manage the hosting for you.</span><span class="sxs-lookup"><span data-stu-id="1f4a1-111">Bring your SharePoint web parts to Teams and let SharePoint manage the hosting for you.</span></span></p>
                    </div>
                </div>
            </div>
        </div>
    </a>
</li>
</ul>

### <a name="teams-tabs-in-sharepoint"></a><span data-ttu-id="1f4a1-112">Registerkarten "Teams" in SharePoint</span><span class="sxs-lookup"><span data-stu-id="1f4a1-112">Teams tabs in SharePoint</span></span>

<span data-ttu-id="1f4a1-113">Mit SharePoint Framework v.1.7 unterstützen wir entwicklern jetzt die Möglichkeit, ihre Registerkarten in Teams zu verwenden und in SharePoint zu hosten.</span><span class="sxs-lookup"><span data-stu-id="1f4a1-113">With SharePoint Framework v.1.7, we’re now supporting the ability for developers to take their Teams tabs and host it in SharePoint.</span></span> <span data-ttu-id="1f4a1-114">Da in SharePoint gehostete Registerkarten eine ähnliche "ganzseitige" Erfahrung erhalten, werden alle Features von Registerkarten von Teams verfügbar gemacht, während der Kontext und die Vertrautheit einer SharePoint-Website beibehalten werden.</span><span class="sxs-lookup"><span data-stu-id="1f4a1-114">As Tabs hosted in SharePoint get a similar "full page" experience, exposing the all the features of Teams tabs while retaining the context and familiarity of a SharePoint site.</span></span>

### <a name="sharepoint-framework-in-teams"></a><span data-ttu-id="1f4a1-115">SharePoint Framework in Teams</span><span class="sxs-lookup"><span data-stu-id="1f4a1-115">SharePoint Framework in Teams</span></span>

<span data-ttu-id="1f4a1-116">Sie können Ihre Microsoft Teams-Registerkarten auch mithilfe von SharePoint Framework implementieren.</span><span class="sxs-lookup"><span data-stu-id="1f4a1-116">You can also implement your Microsoft Teams tabs using SharePoint Framework.</span></span> <span data-ttu-id="1f4a1-117">Für SharePoint-Entwickler vereinfacht dies den Entwicklungsprozess für Registerkarten von Teams erheblich, da SharePoint-Framework-Webparts in SharePoint gehostet werden, ohne dass externe Dienste wie Azure benötigt werden.</span><span class="sxs-lookup"><span data-stu-id="1f4a1-117">For SharePoint developers, this significantly simplifies the development process for Teams tabs because SharePoint Framework web parts are hosted within SharePoint without any need for external services such as Azure.</span></span> [<span data-ttu-id="1f4a1-118">Erfahren Sie mehr über die Verwendung von SharePoint Framework in Teams.</span><span class="sxs-lookup"><span data-stu-id="1f4a1-118">Learn more about using the SharePoint Framework in Teams.</span></span>](/sharepoint/dev/spfx/web-parts/get-started/using-web-part-as-ms-teams-tab)

## <a name="introduction"></a><span data-ttu-id="1f4a1-119">Einführung</span><span class="sxs-lookup"><span data-stu-id="1f4a1-119">Introduction</span></span>

<span data-ttu-id="1f4a1-120">In diesen Anweisungen wird erläutert, wie Sie eine Registerkarte aus einer Microsoft Teams-Beispiel-App verwenden und in SharePoint verwenden können.</span><span class="sxs-lookup"><span data-stu-id="1f4a1-120">These instructions will explain how you can take a tab from a Microsoft Teams sample app and use it in SharePoint.</span></span> <span data-ttu-id="1f4a1-121">Wir verwenden eine Registerkarte, die bereits in Azure gehostet wird, um uns auf die erforderliche Integrationsarbeit zu konzentrieren.</span><span class="sxs-lookup"><span data-stu-id="1f4a1-121">We will be using a tab that's already hosted on Azure in order to focus on the required integration work.</span></span>

<span data-ttu-id="1f4a1-122">Die von uns verwendeten Beispiel-App ist eine Talentverwaltungsanwendung.</span><span class="sxs-lookup"><span data-stu-id="1f4a1-122">The sample app we're using is a Talent Management application.</span></span> <span data-ttu-id="1f4a1-123">Er verwaltet den Einstellungsprozess von Kandidaten für offene Positionen in einem Team.</span><span class="sxs-lookup"><span data-stu-id="1f4a1-123">It manages the hiring process of candidates for open positions in a team.</span></span> <span data-ttu-id="1f4a1-124">(Die App selbst hat zwar ein gutes Aussehen, aber sie hat eigentlich nichts zu tun.</span><span class="sxs-lookup"><span data-stu-id="1f4a1-124">(The app itself, while it looks nice, doesn't actually do anything.</span></span> <span data-ttu-id="1f4a1-125">Wir möchten uns darauf konzentrieren, eine Teams-App zu erstellen und sie in Teams zu laden, und keine echte Talentverwaltungsanwendung erstellen.)</span><span class="sxs-lookup"><span data-stu-id="1f4a1-125">We want to focus on building a Teams app and loading it into Teams, not create a real talent management application.)</span></span>

### <a name="benefits-of-this-approach"></a><span data-ttu-id="1f4a1-126">Vorteile dieses Ansatzes</span><span class="sxs-lookup"><span data-stu-id="1f4a1-126">Benefits of this approach</span></span>

- <span data-ttu-id="1f4a1-127">Erreichen von SharePoint-Benutzern mit Ihrer vorhandenen Registerkarte "Teams"</span><span class="sxs-lookup"><span data-stu-id="1f4a1-127">Reach SharePoint users with your existing Teams tab</span></span>
- <span data-ttu-id="1f4a1-128">Laden Sie Ihr App-Manifest direkt in Ihren SharePoint-App-Katalog hoch.</span><span class="sxs-lookup"><span data-stu-id="1f4a1-128">Upload your app manifest directly to your SharePoint app catalog.</span></span> <span data-ttu-id="1f4a1-129">[Teams-Anwendungspakete werden](~/concepts/build-and-test/apps-package.md) jetzt von SharePoint unterstützt</span><span class="sxs-lookup"><span data-stu-id="1f4a1-129">[Teams application packages](~/concepts/build-and-test/apps-package.md) are now supported by SharePoint</span></span>
- <span data-ttu-id="1f4a1-130">Endbenutzer konfigurieren die Registerkarte auf einer Seite wie jedes andere SharePoint-Web part</span><span class="sxs-lookup"><span data-stu-id="1f4a1-130">End users configure the tab on a page just like any other SharePoint web part</span></span>
- <span data-ttu-id="1f4a1-131">Ihre Registerkarte kann auf den Kontext [zugreifen,](~/tabs/how-to/access-teams-context.md) so wie es möglich ist, wenn sie in Teams ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="1f4a1-131">Your tab can access its [context](~/tabs/how-to/access-teams-context.md) just as it can when running inside Teams</span></span>

## <a name="step-1-testing-the-sample-app"></a><span data-ttu-id="1f4a1-132">Schritt 1: Testen der Beispiel-App</span><span class="sxs-lookup"><span data-stu-id="1f4a1-132">Step 1: Testing the sample app</span></span>

<span data-ttu-id="1f4a1-133">Laden Sie das Beispiel-App-Manifest hier [**herunter.**](https://github.com/MicrosoftDocs/msteams-docs/raw/master/msteams-platform/assets/downloads/TalentMgmt-Azure.zip)</span><span class="sxs-lookup"><span data-stu-id="1f4a1-133">Download the sample app manifest from [**here**](https://github.com/MicrosoftDocs/msteams-docs/raw/master/msteams-platform/assets/downloads/TalentMgmt-Azure.zip).</span></span>

<span data-ttu-id="1f4a1-134">Klicken Sie in Microsoft Teams unten links auf das Store-Symbol und dann links unten auf "Benutzerdefinierte App hochladen".</span><span class="sxs-lookup"><span data-stu-id="1f4a1-134">In Microsoft Teams, click on the Store icon at the lower left and then "Upload a custom app" at the lower left.</span></span> <span data-ttu-id="1f4a1-135">Die hochzuladende Datei befindet sich in Ihrem Downloadordner. Sie wird als TalentMgmt-Azure.zip.</span><span class="sxs-lookup"><span data-stu-id="1f4a1-135">The file to upload will be located in your Downloads folder; it's called TalentMgmt-Azure.zip.</span></span> <span data-ttu-id="1f4a1-136">Wenn alles gut läuft, wird der Installations-/Zustimmungsbildschirm für die Talentmanagement-App angezeigt.</span><span class="sxs-lookup"><span data-stu-id="1f4a1-136">If all goes well, you'll see the install/consent screen for the talent management app.</span></span> <span data-ttu-id="1f4a1-137">Wählen Sie das Team aus, in dem Sie installieren möchten, und klicken Sie auf die Schaltfläche "Installieren".</span><span class="sxs-lookup"><span data-stu-id="1f4a1-137">Choose the team you want to install to and click the Install button.</span></span> <span data-ttu-id="1f4a1-138">Sie können jetzt mit der App experimentieren.</span><span class="sxs-lookup"><span data-stu-id="1f4a1-138">You're now free to experiment with the app.</span></span>

## <a name="step-2-using-the-teams-tab-in-sharepoint"></a><span data-ttu-id="1f4a1-139">Schritt 2: Verwenden der Registerkarte "Teams" in SharePoint</span><span class="sxs-lookup"><span data-stu-id="1f4a1-139">Step 2: Using the Teams tab in SharePoint</span></span>

<span data-ttu-id="1f4a1-140">Laden Sie Ihr Teams-App-Paket hoch, und stellen Sie es in Ihren SharePoint-App-Katalog ein, indem Sie `https://YOUR_TENANT_NAME.sharepoint.com/sites/apps/AppCatalog/Forms/AllItems.aspx` z. B. . `https://contoso.sharepoint.com/sites/apps/AppCatalog/Forms/AllItems.aspx`</span><span class="sxs-lookup"><span data-stu-id="1f4a1-140">Upload and deploy your Teams app package to your SharePoint App Catalog by visiting `https://YOUR_TENANT_NAME.sharepoint.com/sites/apps/AppCatalog/Forms/AllItems.aspx`, e.g. `https://contoso.sharepoint.com/sites/apps/AppCatalog/Forms/AllItems.aspx`.</span></span>

<span data-ttu-id="1f4a1-141">Wenn Sie dazu aufgefordert werden, aktivieren Sie "Diese Lösung für alle Websites in der Organisation verfügbar machen":</span><span class="sxs-lookup"><span data-stu-id="1f4a1-141">When prompted, enable "Make this solution available to all sites in the organization":</span></span>

![Registerkarten in der SharePoint-Ansicht](~/assets/images/tabs/tabs-in-sharepoint/image065.png)

<span data-ttu-id="1f4a1-143">Erstellen Sie auf Ihrer Website eine neue Seite, indem Sie oben rechts auf die Zahnradschaltfläche und dann auf "Seite hinzufügen" klicken:</span><span class="sxs-lookup"><span data-stu-id="1f4a1-143">In your site, create a new page by clicking in the gear button at the upper right and then "Add a page":</span></span>

![SharePoint-Ansicht](~/assets/images/tabs/tabs-in-sharepoint/image066.png)

<span data-ttu-id="1f4a1-145">Sie sehen die Erstellungserfahrung für SharePoint-Seiten.</span><span class="sxs-lookup"><span data-stu-id="1f4a1-145">You'll see the SharePoint Pages authoring experience.</span></span> <span data-ttu-id="1f4a1-146">Nennen Sie Ihre Seite "Registerkarte "Meine Teams".</span><span class="sxs-lookup"><span data-stu-id="1f4a1-146">Name your page "My Teams Tab".</span></span>

<span data-ttu-id="1f4a1-147">Öffnen Sie die Web part-Toolbox, indem Sie die Schaltfläche +drücken, und wählen Sie Ihre Registerkarte "Teams" (mit dem Namen "Contoso HR") aus.</span><span class="sxs-lookup"><span data-stu-id="1f4a1-147">Open the web part toolbox by pressing the + button, and select your Teams Tab (named "Contoso HR").</span></span> <span data-ttu-id="1f4a1-148">Webparts sind alphabetisch sortiert. Wenn es sich um eine lange Liste gibt, können Sie die Suchleiste verwenden, um sie zu finden.</span><span class="sxs-lookup"><span data-stu-id="1f4a1-148">Web parts are sorted alphabetically; if it's a long list, you can use the search bar to find it.</span></span> <span data-ttu-id="1f4a1-149">Dadurch wird ein Web part in der Canvas erstellt, die Ihre Registerkarte "Teams" enthält:</span><span class="sxs-lookup"><span data-stu-id="1f4a1-149">This will create a web part in the canvas that contains your Teams tab:</span></span>

![Registerkartenansicht](~/assets/images/tabs/tabs-in-sharepoint/image071.png)

<span data-ttu-id="1f4a1-151">Klicken Sie auf die Schaltfläche "Veröffentlichen", wenn Sie die Bearbeitung abgeschlossen haben.</span><span class="sxs-lookup"><span data-stu-id="1f4a1-151">Press the "Publish" button when you are finished editing.</span></span>

<span data-ttu-id="1f4a1-152">Sie können auf "Seite zur Navigation hinzufügen" klicken, um einen Kurzverweis auf Ihre Seite in der linken Navigationsleiste zu erhalten:</span><span class="sxs-lookup"><span data-stu-id="1f4a1-152">You may want to click "Add page to navigation" to have a quick reference to your page in the left navigation bar:</span></span>

![Registerkarte in SharePoint Bild](~/assets/images/tabs/tabs-in-sharepoint/image073.png)

## <a name="step-3-explore-app-pages-in-sharepoint"></a><span data-ttu-id="1f4a1-154">Schritt 3: Erkunden von App-Seiten in SharePoint</span><span class="sxs-lookup"><span data-stu-id="1f4a1-154">Step 3: Explore App Pages in SharePoint</span></span>

<span data-ttu-id="1f4a1-155">Nachdem Ihre Seite veröffentlicht wurde, können Sie erkunden, wie Sie Ihre Teams-App in eine vollständigere Erfahrung [in SharePoint umschließen.](/sharepoint/dev/spfx/web-parts/single-part-app-pages)</span><span class="sxs-lookup"><span data-stu-id="1f4a1-155">Once your page is published, you can explore [turning your Teams app into a more complete experience inside SharePoint](/sharepoint/dev/spfx/web-parts/single-part-app-pages).</span></span> <span data-ttu-id="1f4a1-156">Dadurch wird die aktuelle Seite in eine App-Seite konvertiert, die das normale SharePoint-Seitenlayout mit einer ganzseitigen Besensung für die Registerkarte "Teams" zeigt:</span><span class="sxs-lookup"><span data-stu-id="1f4a1-156">This converts the current page into an App Page, showing the normal SharePoint page layout with a full-page experience for the Teams tab:</span></span>

![Abbildung von Registerkarten in Sharepoint](~/assets/images/tabs/tabs-in-sharepoint/image085.png)

## <a name="code-sample"></a><span data-ttu-id="1f4a1-158">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="1f4a1-158">Code sample</span></span>
| <span data-ttu-id="1f4a1-159">**Beispielname**</span><span class="sxs-lookup"><span data-stu-id="1f4a1-159">**Sample name**</span></span> | <span data-ttu-id="1f4a1-160">**Beschreibung**</span><span class="sxs-lookup"><span data-stu-id="1f4a1-160">**Description**</span></span> | <span data-ttu-id="1f4a1-161">**SPFx**</span><span class="sxs-lookup"><span data-stu-id="1f4a1-161">**SPFx**</span></span> |
|-----------------|-----------------|----------|
| <span data-ttu-id="1f4a1-162">SPFx-Web part</span><span class="sxs-lookup"><span data-stu-id="1f4a1-162">SPFx web part</span></span> | <span data-ttu-id="1f4a1-163">SPFx-Web-Part-Beispiele für Registerkarten, Kanäle und Gruppen.</span><span class="sxs-lookup"><span data-stu-id="1f4a1-163">SPFx web part samples for tabs, channels, and groups.</span></span> | [<span data-ttu-id="1f4a1-164">View</span><span class="sxs-lookup"><span data-stu-id="1f4a1-164">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-channel-group/spfx)

## <a name="more-information"></a><span data-ttu-id="1f4a1-165">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="1f4a1-165">More information</span></span>

- [<span data-ttu-id="1f4a1-166">Erstellen von Microsoft Teams-Registerkarten mit SharePoint Framework – Lernprogramm</span><span class="sxs-lookup"><span data-stu-id="1f4a1-166">Building Microsoft Teams tab using SharePoint Framework - Tutorial</span></span>](/sharepoint/dev/spfx/web-parts/get-started/using-web-part-as-ms-teams-tab)
- [<span data-ttu-id="1f4a1-167">Verwenden von App-Seiten mit einem einzelne Part in SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="1f4a1-167">Using single part app pages in SharePoint Online</span></span>](/sharepoint/dev/spfx/web-parts/single-part-app-pages)
