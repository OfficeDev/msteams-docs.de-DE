---
title: Hinzufügen der Registerkarte Teams zu SharePoint
author: laujan
description: So stellen Sie Ihre vorhandene Registerkarte "Teams" in SharePoint als SharePoint-Framework-Web part zur Verfügung.
keywords: Teams registerkarten sharepoint framework development
localization_priority: Normal
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: a2ea6c470f094a9d7b8617a210559e911f5f81c9
ms.sourcegitcommit: a732789190f59ec1f3699e8ad2f06387e8fe1458
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2021
ms.locfileid: "52058481"
---
# <a name="add-teams-tab-to-sharepoint"></a><span data-ttu-id="46da1-104">Hinzufügen der Registerkarte Teams zu SharePoint</span><span class="sxs-lookup"><span data-stu-id="46da1-104">Add Teams tab to SharePoint</span></span> 

<span data-ttu-id="46da1-105">Sie können eine umfassende Integrationserfahrung zwischen Microsoft Teams und SharePoint erhalten, indem Sie eine Microsoft Teams-Registerkarte in SharePoint als SPFx-Web part hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="46da1-105">You can get a rich integration experience between Microsoft Teams and SharePoint by adding a Microsoft Teams tab in SharePoint as an SPFx web part.</span></span> <span data-ttu-id="46da1-106">In diesem Dokument erfahren Sie, wie Sie eine Registerkarte aus einer Microsoft Teams-Beispiel-App nehmen und in SharePoint verwenden.</span><span class="sxs-lookup"><span data-stu-id="46da1-106">This document guides you on how you to take a tab from a Microsoft Teams sample app and use it in SharePoint.</span></span> 

## <a name="rich-integration-between-teams-and-sharepoint"></a><span data-ttu-id="46da1-107">Umfassende Integration zwischen Teams und SharePoint</span><span class="sxs-lookup"><span data-stu-id="46da1-107">Rich integration between Teams and SharePoint</span></span>

<span data-ttu-id="46da1-108">Mit der Novemberversion von Teams und SharePoint Framework v.1.7 verfügen Entwickler über zwei leistungsstarke Funktionen:</span><span class="sxs-lookup"><span data-stu-id="46da1-108">With the November release of Teams and SharePoint Framework v.1.7, developers have two powerful capabilities:</span></span>

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
                        <h3><span data-ttu-id="46da1-109">Registerkarten für Teams in SharePoint</span><span class="sxs-lookup"><span data-stu-id="46da1-109">Teams Tabs in SharePoint</span></span></h3>
                        <p><span data-ttu-id="46da1-110">Erstellen Sie umfangreiche App-Erfahrungen in SharePoint, indem Sie Ihre Teams-App in Sharepoint (in diesem Artikel) verwenden.</span><span class="sxs-lookup"><span data-stu-id="46da1-110">Create rich app experiences in SharePoint by bringing your Teams app into Sharepoint (this article).</span></span></p>
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
                        <h3><span data-ttu-id="46da1-111">SharePoint Framework in Teams</span><span class="sxs-lookup"><span data-stu-id="46da1-111">SharePoint Framework in Teams</span></span></h3>
                        <p><span data-ttu-id="46da1-112">Bring your SharePoint web parts to Teams and let SharePoint manage the hosting for you.</span><span class="sxs-lookup"><span data-stu-id="46da1-112">Bring your SharePoint web parts to Teams and let SharePoint manage the hosting for you.</span></span></p>
                    </div>
                </div>
            </div>
        </div>
    </a>
</li>
</ul>

### <a name="teams-tabs-in-sharepoint"></a><span data-ttu-id="46da1-113">Registerkarten "Teams" in SharePoint</span><span class="sxs-lookup"><span data-stu-id="46da1-113">Teams tabs in SharePoint</span></span>

<span data-ttu-id="46da1-114">Mit SharePoint Framework v.1.7 können Sie Ihre Teams-Registerkarten in SharePoint hosten.</span><span class="sxs-lookup"><span data-stu-id="46da1-114">With SharePoint Framework v.1.7, you can host your Teams tabs in SharePoint.</span></span> <span data-ttu-id="46da1-115">Wenn in SharePoint gehostete  Registerkarten eine ähnliche vollständige Seitenerfahrung erhalten, werden alle Features von Teams-Registerkarten verfügbar gemacht, während der Kontext und die Vertrautheit einer SharePoint-Website beibehalten werden.</span><span class="sxs-lookup"><span data-stu-id="46da1-115">As tabs hosted in SharePoint get a similar **full page** experience, exposing all the features of Teams tabs while retaining the context and familiarity of a SharePoint site.</span></span>

### <a name="sharepoint-framework-in-teams"></a><span data-ttu-id="46da1-116">SharePoint Framework in Teams</span><span class="sxs-lookup"><span data-stu-id="46da1-116">SharePoint Framework in Teams</span></span>

<span data-ttu-id="46da1-117">Sie können Ihre Microsoft Teams-Registerkarten auch mithilfe von SharePoint Framework implementieren.</span><span class="sxs-lookup"><span data-stu-id="46da1-117">You can also implement your Microsoft Teams tabs using SharePoint Framework.</span></span> <span data-ttu-id="46da1-118">SharePoint Framework-Webparts werden in SharePoint gehostet, ohne dass externe Dienste wie Azure benötigt werden.</span><span class="sxs-lookup"><span data-stu-id="46da1-118">SharePoint Framework web parts are hosted within SharePoint without any need for external services, such as Azure.</span></span> <span data-ttu-id="46da1-119">Für SharePoint-Entwickler vereinfacht dies den Entwicklungsprozess für Teams-Registerkarten erheblich.</span><span class="sxs-lookup"><span data-stu-id="46da1-119">For SharePoint developers, this significantly simplifies the development process for Teams tabs.</span></span> <span data-ttu-id="46da1-120">Weitere Informationen zum SharePoint Framework in Teams finden Sie unter Verwenden des [SharePoint Framework in Teams.](/sharepoint/dev/spfx/web-parts/get-started/using-web-part-as-ms-teams-tab)</span><span class="sxs-lookup"><span data-stu-id="46da1-120">For more information on SharePoint Framework in Teams, see [how to use the SharePoint Framework in Teams.](/sharepoint/dev/spfx/web-parts/get-started/using-web-part-as-ms-teams-tab)</span></span>

## <a name="introduction"></a><span data-ttu-id="46da1-121">Einführung</span><span class="sxs-lookup"><span data-stu-id="46da1-121">Introduction</span></span>

<span data-ttu-id="46da1-122">Die hier verwendete Registerkarte wird bereits in Azure gehostet, um sich auf die erforderliche Integrationsarbeit zu konzentrieren.</span><span class="sxs-lookup"><span data-stu-id="46da1-122">The tab used here is already hosted on Azure, to focus on the required integration work.</span></span>

<span data-ttu-id="46da1-123">Die verwendete Beispiel-App ist eine Talentverwaltungsanwendung.</span><span class="sxs-lookup"><span data-stu-id="46da1-123">The sample app that is being used is a Talent Management application.</span></span> <span data-ttu-id="46da1-124">Es verwaltet den Einstellungsprozess von Kandidaten für offene Positionen in einem Team.</span><span class="sxs-lookup"><span data-stu-id="46da1-124">It manages the hiring process of candidates for open positions in a team.</span></span> <span data-ttu-id="46da1-125">Erstellen Sie eine Beispiel-Teams-App, und laden Sie sie in Teams.</span><span class="sxs-lookup"><span data-stu-id="46da1-125">Build a sample Teams app and load it into Teams.</span></span> <span data-ttu-id="46da1-126">Erstellen Sie keine echte Talentverwaltungsanwendung.</span><span class="sxs-lookup"><span data-stu-id="46da1-126">Do not create a real talent management application.</span></span>

### <a name="benefits-of-this-approach"></a><span data-ttu-id="46da1-127">Vorteile dieses Ansatzes</span><span class="sxs-lookup"><span data-stu-id="46da1-127">Benefits of this approach</span></span>

* <span data-ttu-id="46da1-128">Erreichen Sie SharePoint-Benutzer mit Ihrer vorhandenen Registerkarte Teams.</span><span class="sxs-lookup"><span data-stu-id="46da1-128">Reach SharePoint users with your existing Teams tab.</span></span>
* <span data-ttu-id="46da1-129">Laden Sie Ihr App-Manifest direkt in Ihren SharePoint-App-Katalog hoch.</span><span class="sxs-lookup"><span data-stu-id="46da1-129">Upload your app manifest directly to your SharePoint app catalog.</span></span> <span data-ttu-id="46da1-130">[Teams-Anwendungspakete](~/concepts/build-and-test/apps-package.md) werden jetzt von SharePoint unterstützt.</span><span class="sxs-lookup"><span data-stu-id="46da1-130">[Teams application packages](~/concepts/build-and-test/apps-package.md) are now supported by SharePoint.</span></span>
* <span data-ttu-id="46da1-131">Die Benutzer konfigurieren die Registerkarte auf einer Seite wie jedes andere SharePoint-Web part.</span><span class="sxs-lookup"><span data-stu-id="46da1-131">The users configure the tab on a page just like any other SharePoint web part.</span></span>
* <span data-ttu-id="46da1-132">Ihre Registerkarte kann auf ihren [Kontext](~/tabs/how-to/access-teams-context.md) zugreifen, wie er kann, wenn sie in Teams ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="46da1-132">Your tab can access its [context](~/tabs/how-to/access-teams-context.md) sameas it can, when running inside Teams.</span></span>

<span data-ttu-id="46da1-133">**So fügen Sie die Registerkarte Teams zu SharePoint hinzu**</span><span class="sxs-lookup"><span data-stu-id="46da1-133">**To add Teams tab to SharePoint**</span></span>

<span data-ttu-id="46da1-134">Führen Sie die folgenden Schritte aus, um Die Registerkarte Teams zu SharePoint hinzuzufügen:</span><span class="sxs-lookup"><span data-stu-id="46da1-134">Perform the following steps to add Teams tab to SharePoint:</span></span>

## <a name="1-test-the-sample-app"></a><span data-ttu-id="46da1-135">1. Testen der Beispiel-App</span><span class="sxs-lookup"><span data-stu-id="46da1-135">1. Test the sample app</span></span>

<span data-ttu-id="46da1-136">Laden Sie das [Beispiel-App-Manifest herunter.](https://github.com/MicrosoftDocs/msteams-docs/raw/master/msteams-platform/assets/downloads/TalentMgmt-Azure.zip)</span><span class="sxs-lookup"><span data-stu-id="46da1-136">Download the [sample app manifest](https://github.com/MicrosoftDocs/msteams-docs/raw/master/msteams-platform/assets/downloads/TalentMgmt-Azure.zip).</span></span>

1. <span data-ttu-id="46da1-137">Öffnen Sie Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="46da1-137">Open Microsoft Teams.</span></span>
1. <span data-ttu-id="46da1-138">Wählen Sie **das Appstore-Symbol** unten links neben der Registerkarte aus.</span><span class="sxs-lookup"><span data-stu-id="46da1-138">Select the **Appstore** icon at the lower left of side tab.</span></span>
1. <span data-ttu-id="46da1-139">Wählen **Sie unten links Hochladen** einer benutzerdefinierten App aus.</span><span class="sxs-lookup"><span data-stu-id="46da1-139">Select **Upload a custom app** at the lower left.</span></span> <span data-ttu-id="46da1-140">In der folgenden Abbildung wird der entsprechende Bildschirm angezeigt:</span><span class="sxs-lookup"><span data-stu-id="46da1-140">The following image displays the corresponding screen:</span></span>  

    ![Hochladen einer benutzerdefinierten App](~/assets/images/tabs/tabs-in-sharepoint/upload-custom-app.png)

1. <span data-ttu-id="46da1-142">Die datei, die hochgeladen werden soll, befindet sich im **Ordner Downloads.**</span><span class="sxs-lookup"><span data-stu-id="46da1-142">The file to upload is located in your **Downloads** folder.</span></span> <span data-ttu-id="46da1-143">Es wird als TalentMgmt-Azure.zip.</span><span class="sxs-lookup"><span data-stu-id="46da1-143">It is called TalentMgmt-Azure.zip.</span></span> <span data-ttu-id="46da1-144">In der folgenden Abbildung wird der entsprechende Bildschirm angezeigt:</span><span class="sxs-lookup"><span data-stu-id="46da1-144">The following image displays the corresponding screen:</span></span>
 
    ![TalentMgmt in Azure](~/assets/images/tabs/tabs-in-sharepoint/talentmgmt-azure.png)

1. <span data-ttu-id="46da1-146">Sie können den Installations- oder Zustimmungsbildschirm für die Talentverwaltungs-App sehen.</span><span class="sxs-lookup"><span data-stu-id="46da1-146">You can see the install or consent screen for the talent management app.</span></span> <span data-ttu-id="46da1-147">Wählen Sie das Team aus, das Sie installieren möchten.</span><span class="sxs-lookup"><span data-stu-id="46da1-147">Select the team you want to install.</span></span> 
1. <span data-ttu-id="46da1-148">Wählen Sie **installieren** aus, und beginnen Sie mit dem Experimentieren mit der App.</span><span class="sxs-lookup"><span data-stu-id="46da1-148">Select the **Install** and start experimenting with the app.</span></span>

## <a name="2-use-teams-tab-in-sharepoint"></a><span data-ttu-id="46da1-149">2. Verwenden der Registerkarte Teams in SharePoint</span><span class="sxs-lookup"><span data-stu-id="46da1-149">2. Use Teams tab in SharePoint</span></span>

1. <span data-ttu-id="46da1-150">Laden Sie Ihr Teams-App-Paket hoch und stellen Sie es in Ihrem SharePoint-App-Katalog unter `https://YOUR_TENANT_NAME.sharepoint.com/sites/apps/AppCatalog/Forms/AllItems.aspx` .</span><span class="sxs-lookup"><span data-stu-id="46da1-150">Upload and deploy your Teams app package to your SharePoint App Catalog by visiting `https://YOUR_TENANT_NAME.sharepoint.com/sites/apps/AppCatalog/Forms/AllItems.aspx`.</span></span> <span data-ttu-id="46da1-151">Beispiel: `https://contoso.sharepoint.com/sites/apps/AppCatalog/Forms/AllItems.aspx`.</span><span class="sxs-lookup"><span data-stu-id="46da1-151">For example, `https://contoso.sharepoint.com/sites/apps/AppCatalog/Forms/AllItems.aspx`.</span></span>

1. <span data-ttu-id="46da1-152">Wenn Sie dazu aufgefordert werden, aktivieren **Sie Diese Lösung für alle Websites in der Organisation verfügbar machen.**</span><span class="sxs-lookup"><span data-stu-id="46da1-152">When prompted, enable **Make this solution available to all sites in the organization**.</span></span>
<span data-ttu-id="46da1-153">In der folgenden Abbildung wird der entsprechende Bildschirm angezeigt:</span><span class="sxs-lookup"><span data-stu-id="46da1-153">The following image displays the corresponding screen:</span></span>

   ![Registerkarten in der Sharepoint-Ansicht](~/assets/images/tabs/tabs-in-sharepoint/image065.png)

1. <span data-ttu-id="46da1-155">Erstellen Sie auf Ihrer Website eine neue Seite, indem Sie oben rechts die Zahnradschaltfläche auswählen und dann **Seite hinzufügen auswählen.**</span><span class="sxs-lookup"><span data-stu-id="46da1-155">In your site, create a new page by selecting the gear button at the upper right and then  select **Add a page**.</span></span>
<span data-ttu-id="46da1-156">In der folgenden Abbildung wird der entsprechende Bildschirm angezeigt:</span><span class="sxs-lookup"><span data-stu-id="46da1-156">The following image displays the corresponding screen:</span></span>

   ![Sharepoint-Ansicht](~/assets/images/tabs/tabs-in-sharepoint/image066.png)

1. <span data-ttu-id="46da1-158">Sie können die Erstellungserfahrung von SharePoint-Seiten anzeigen.</span><span class="sxs-lookup"><span data-stu-id="46da1-158">You can see the SharePoint pages authoring experience.</span></span> <span data-ttu-id="46da1-159">Benennen Sie Ihre Seite als **Registerkarte "Meine Teams".**</span><span class="sxs-lookup"><span data-stu-id="46da1-159">Name your page as **My Teams Tab**.</span></span>

1. <span data-ttu-id="46da1-160">Öffnen Sie die Web part-Toolbox, indem Sie die Schaltfläche drücken, und wählen Sie Die Registerkarte Teams mit dem Namen `+` **Contoso HR aus.**</span><span class="sxs-lookup"><span data-stu-id="46da1-160">Open the web part toolbox by pressing the `+` button, and select your Teams Tab, named **Contoso HR**.</span></span> <span data-ttu-id="46da1-161">Webparts werden alphabetisch sortiert.</span><span class="sxs-lookup"><span data-stu-id="46da1-161">Web parts are sorted alphabetically.</span></span> <span data-ttu-id="46da1-162">Wenn es sich um eine lange Liste handelt, können Sie die Suchleiste verwenden, um sie zu finden.</span><span class="sxs-lookup"><span data-stu-id="46da1-162">If it is a long list, you can use the search bar to find it.</span></span> <span data-ttu-id="46da1-163">Dadurch wird ein Webteil im Zeichenbereich erstellt, das Ihre Registerkarte Teams enthält. In der folgenden Abbildung wird die Registerkartenansicht angezeigt:</span><span class="sxs-lookup"><span data-stu-id="46da1-163">This creates a web part in the canvas that contains your Teams tab. The following image displays the tab view:</span></span>

   ![Registerkartenansicht](~/assets/images/tabs/tabs-in-sharepoint/image071.png)

1. <span data-ttu-id="46da1-165">Drücken Sie die **Schaltfläche Veröffentlichen,** nachdem Sie die Bearbeitung abgeschlossen haben.</span><span class="sxs-lookup"><span data-stu-id="46da1-165">Press the **Publish** button after you finish  editing.</span></span>

1. <span data-ttu-id="46da1-166">Wählen **Sie Seite zur Navigation hinzufügen aus,** um einen Schnellverweis auf Ihre Seite in der linken Navigationsleiste zu haben.</span><span class="sxs-lookup"><span data-stu-id="46da1-166">Select **Add page to navigation** to have a quick reference to your page in the left navigation bar.</span></span> <span data-ttu-id="46da1-167">In der folgenden Abbildung wird die Registerkarte in Sharepoint angezeigt:</span><span class="sxs-lookup"><span data-stu-id="46da1-167">The following image displays the tab in Sharepoint:</span></span> 

   ![Registerkarte im Sharepoint-Bild](~/assets/images/tabs/tabs-in-sharepoint/image073.png)

## <a name="3-explore-app-pages-in-sharepoint"></a><span data-ttu-id="46da1-169">3. Erkunden von App-Seiten in SharePoint</span><span class="sxs-lookup"><span data-stu-id="46da1-169">3. Explore App Pages in SharePoint</span></span>

<span data-ttu-id="46da1-170">Nachdem Ihre Seite veröffentlicht wurde, können Sie erkunden, wie Sie [Ihre Teams-App](/sharepoint/dev/spfx/web-parts/single-part-app-pages)in sharePoint zu einer vollständigeren Umgebung machen.</span><span class="sxs-lookup"><span data-stu-id="46da1-170">After your page is published, you can explore [turning your Teams app into a more complete experience inside SharePoint](/sharepoint/dev/spfx/web-parts/single-part-app-pages).</span></span> <span data-ttu-id="46da1-171">Dadurch wird die aktuelle Seite in eine App-Seite konvertiert, die das normale SharePoint-Seitenlayout mit einer vollständigen Seitenerfahrung für die Registerkarte Teams zeigt.</span><span class="sxs-lookup"><span data-stu-id="46da1-171">This converts the current page into an App Page, showing the normal SharePoint page layout with a full page experience for the Teams tab.</span></span> 

<span data-ttu-id="46da1-172">Die folgende Abbildung zeigt die vollständige Erfahrung der Teams-App in Sharepoint: ![ Abbildung von Registerkarten in Sharepoint](~/assets/images/tabs/tabs-in-sharepoint/image085.png)</span><span class="sxs-lookup"><span data-stu-id="46da1-172">The following image displays the complete experience of Teams app in Sharepoint: ![Image of Tabs in Sharepoint](~/assets/images/tabs/tabs-in-sharepoint/image085.png)</span></span>

## <a name="code-sample"></a><span data-ttu-id="46da1-173">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="46da1-173">Code sample</span></span>
| <span data-ttu-id="46da1-174">**Beispielname**</span><span class="sxs-lookup"><span data-stu-id="46da1-174">**Sample name**</span></span> | <span data-ttu-id="46da1-175">**Beschreibung**</span><span class="sxs-lookup"><span data-stu-id="46da1-175">**Description**</span></span> | <span data-ttu-id="46da1-176">**SPFx**</span><span class="sxs-lookup"><span data-stu-id="46da1-176">**SPFx**</span></span> |
|-----------------|-----------------|----------|
| <span data-ttu-id="46da1-177">SPFx-Web part</span><span class="sxs-lookup"><span data-stu-id="46da1-177">SPFx web part</span></span> | <span data-ttu-id="46da1-178">SPFx-Webteilbeispiele für Registerkarten, Kanäle und Gruppen.</span><span class="sxs-lookup"><span data-stu-id="46da1-178">SPFx web part samples for tabs, channels, and groups.</span></span> | [<span data-ttu-id="46da1-179">View</span><span class="sxs-lookup"><span data-stu-id="46da1-179">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/tab-channel-group/spfx)

## <a name="see-also"></a><span data-ttu-id="46da1-180">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="46da1-180">See also</span></span>

- [<span data-ttu-id="46da1-181">Erstellen von Microsoft Teams-Registerkarten mit SharePoint Framework – Lernprogramm</span><span class="sxs-lookup"><span data-stu-id="46da1-181">Building Microsoft Teams tab using SharePoint Framework - Tutorial</span></span>](/sharepoint/dev/spfx/web-parts/get-started/using-web-part-as-ms-teams-tab)

- [<span data-ttu-id="46da1-182">Verwenden von App-Seiten mit einem einzelne Part in SharePoint Online</span><span class="sxs-lookup"><span data-stu-id="46da1-182">Using single part app pages in SharePoint Online</span></span>](/sharepoint/dev/spfx/web-parts/single-part-app-pages)

- [<span data-ttu-id="46da1-183">Integrieren von Web-Apps</span><span class="sxs-lookup"><span data-stu-id="46da1-183">Integrate web apps</span></span>](~/samples/integrate-web-apps-overview.md)
