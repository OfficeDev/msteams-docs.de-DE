---
title: Vorbereiten der Übermittlung an den Store
description: Beschreibt die letzten Schritte vor dem Senden Ihrer Microsoft Teams-App, die im Store aufgeführt werden soll.
ms.topic: how-to
localization_priority: Normal
author: heath-hamilton
ms.author: surbhigupta
ms.openlocfilehash: 975d3ef8fc8bdc8d6d7c336cf3a61a3a42ef5315
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566033"
---
# <a name="prepare-your-microsoft-teams-store-submission"></a><span data-ttu-id="1a198-103">Vorbereiten Der Microsoft Teams-Shop-Übermittlung</span><span class="sxs-lookup"><span data-stu-id="1a198-103">Prepare your Microsoft Teams store submission</span></span>

<span data-ttu-id="1a198-104">Sie haben Ihre Microsoft Teams-App entworfen, erstellt und getestet.</span><span class="sxs-lookup"><span data-stu-id="1a198-104">You've designed, built, and tested your Microsoft Teams app.</span></span> <span data-ttu-id="1a198-105">Jetzt können Sie es auflisten, damit die Leute Ihre App entdecken und verwenden können.</span><span class="sxs-lookup"><span data-stu-id="1a198-105">Now you're ready to list it so people can discover and start using your app.</span></span>

<span data-ttu-id="1a198-106">Bevor Sie Ihre App an [das Partner Center](/office/dev/store/use-partner-center-to-submit-to-appsource)übermitteln, stellen Sie sicher, dass Sie Folgendes getan haben.</span><span class="sxs-lookup"><span data-stu-id="1a198-106">Before you submit your app to [Partner Center](/office/dev/store/use-partner-center-to-submit-to-appsource), make sure you've done the following.</span></span>

## <a name="validate-your-app-package"></a><span data-ttu-id="1a198-107">Überprüfen Ihres App-Pakets</span><span class="sxs-lookup"><span data-stu-id="1a198-107">Validate your app package</span></span>

<span data-ttu-id="1a198-108">Während Ihre App möglicherweise in einer Testumgebung funktioniert, sollten Sie Ihr App-Paket überprüfen, um Probleme während des Übermittlungsprozesses zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="1a198-108">While your app may be working in a test environment, you should check your app package to avoid running into issues during the submission process.</span></span>

<span data-ttu-id="1a198-109">Das Microsoft Teams App-Validierungstool hilft Ihnen, Probleme zu identifizieren und zu beheben, bevor Sie an das Partner Center senden.</span><span class="sxs-lookup"><span data-stu-id="1a198-109">The Microsoft Teams app validation tool helps you identify and fix issues before submitting to Partner Center.</span></span> <span data-ttu-id="1a198-110">Das Tool überprüft automatisch die Konfigurationen Ihrer App mit den gleichen Testfällen, die während der Speicherüberprüfung verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="1a198-110">The tool automatically checks your app's configurations against the same test cases used during store validation.</span></span>

1. <span data-ttu-id="1a198-111">Wechseln Sie zum [Microsoft Teams-App-Validierungstool](https://dev.teams.microsoft.com/appvalidation.html).</span><span class="sxs-lookup"><span data-stu-id="1a198-111">Go to the [Microsoft Teams app validation tool](https://dev.teams.microsoft.com/appvalidation.html).</span></span> <span data-ttu-id="1a198-112">(Hinweis: Das Tool ist auch in [App Studio](../../../build-and-test/app-studio-overview.md)verfügbar.)</span><span class="sxs-lookup"><span data-stu-id="1a198-112">(Note: The tool is also available in [App Studio](../../../build-and-test/app-studio-overview.md).)</span></span>
1. <span data-ttu-id="1a198-113">Hochladen Ihr App-Paket, um die automatisierten Tests auszuführen.</span><span class="sxs-lookup"><span data-stu-id="1a198-113">Upload your app package to run the automated tests.</span></span>
1. <span data-ttu-id="1a198-114">Wechseln Sie zur **vorläufigen Checkliste,** und überprüfen Sie die schwer zu automatisierenden Testfälle.</span><span class="sxs-lookup"><span data-stu-id="1a198-114">Go to the **Preliminary checklist** and review the test cases that are difficult to automate.</span></span>
1. <span data-ttu-id="1a198-115">[Beheben Sie Probleme mit Ihren Konfigurationen](~/resources/schema/manifest-schema.md) oder Ihrer App im Allgemeinen, wenn die automatisierten Tests Ihnen Fehler beschwichtigen oder Sie nicht alle Kriterien in der Checkliste erfüllt haben.</span><span class="sxs-lookup"><span data-stu-id="1a198-115">[Fix issues with your configurations](~/resources/schema/manifest-schema.md) or app in general if the automated tests give you errors or you haven't met all the criteria in the checklist.</span></span>

## <a name="compile-testing-instructions"></a><span data-ttu-id="1a198-116">Erstellen von Testanweisungen</span><span class="sxs-lookup"><span data-stu-id="1a198-116">Compile testing instructions</span></span>

<span data-ttu-id="1a198-117">Geben Sie Anweisungen und Ressourcen an, mit denen die Prüfer Ihre App testen können, einschließlich Testkonten, Anmeldeinformationen und Lizenzschlüssel.</span><span class="sxs-lookup"><span data-stu-id="1a198-117">Provide instructions and resources to help the reviewers test your app, including test accounts, credentials, and license keys.</span></span> <span data-ttu-id="1a198-118">Sie können Anweisungen im Partner Center hinzufügen oder an einen öffentlich zugänglichen Speicherort auf SharePoint hochladen.</span><span class="sxs-lookup"><span data-stu-id="1a198-118">You can add instructions in Partner Center or upload them to a publicly available location on SharePoint.</span></span>

### <a name="feature-list"></a><span data-ttu-id="1a198-119">Feature-Liste</span><span class="sxs-lookup"><span data-stu-id="1a198-119">Feature list</span></span>

<span data-ttu-id="1a198-120">Geben Sie Details zu den Funktionen Ihrer App in Teams und Schritte zum Testen der einzelnen Apps an.</span><span class="sxs-lookup"><span data-stu-id="1a198-120">Provide details about your app's capabilities in Teams and steps for testing each one.</span></span>

### <a name="accounts"></a><span data-ttu-id="1a198-121">Konten</span><span class="sxs-lookup"><span data-stu-id="1a198-121">Accounts</span></span>

<span data-ttu-id="1a198-122">Sie müssen Testkonten bereitstellen, wenn Ihre App eine Lizenz oder ein Backend-Safelisting erfordert.</span><span class="sxs-lookup"><span data-stu-id="1a198-122">You must provide test accounts if your app requires a license or backend safelisting.</span></span> <span data-ttu-id="1a198-123">Alle von Ihnen zur Verfügung stellenkonten müssen vorab ausgefüllte Daten enthalten, um das Testen zu erleichtern.</span><span class="sxs-lookup"><span data-stu-id="1a198-123">All accounts you provide must include pre-populated data to facilitate testing.</span></span>

<span data-ttu-id="1a198-124">Abhängig von den Funktionen Ihrer App müssen Sie möglicherweise alle folgenden Optionen bereitstellen:</span><span class="sxs-lookup"><span data-stu-id="1a198-124">Depending on your app's features, you may need to provide all of the following:</span></span>

* <span data-ttu-id="1a198-125">Admin-Konto (erforderlich)</span><span class="sxs-lookup"><span data-stu-id="1a198-125">Admin account (required)</span></span>
* <span data-ttu-id="1a198-126">Nicht-Admin-Konto (erforderlich)</span><span class="sxs-lookup"><span data-stu-id="1a198-126">Non-admin account (required)</span></span>
* <span data-ttu-id="1a198-127">Ein Konto, das nicht vorkonfiguriert ist, um die Anmeldeerfahrung für die erste Ausführung ordnungsgemäß zu testen (erforderlich)</span><span class="sxs-lookup"><span data-stu-id="1a198-127">An account that isn't pre-configured in order to properly test the first-run sign-in experience (required)</span></span>
* <span data-ttu-id="1a198-128">Ein Konto mit Zugriff auf Premium- oder Upgrade-Funktionen (falls zutreffend)</span><span class="sxs-lookup"><span data-stu-id="1a198-128">An account with access to premium or upgraded features (if applicable)</span></span>
* <span data-ttu-id="1a198-129">Zwei Konten im selben Mandanten, um die Zusammenarbeit für Apps zu testen, die in freigegebenen Kontexten funktionieren (falls zutreffend)</span><span class="sxs-lookup"><span data-stu-id="1a198-129">Two accounts in the same tenant to test the collaboration experience for apps that work in shared contexts (if applicable)</span></span>

### <a name="tenant-configurations"></a><span data-ttu-id="1a198-130">Mandantenkonfigurationen</span><span class="sxs-lookup"><span data-stu-id="1a198-130">Tenant configurations</span></span>

<span data-ttu-id="1a198-131">Wenn Sie einen Teams Mandanten für die Verwendung Ihrer App konfigurieren müssen, fügen Sie diese Anweisungen sowie Administrator- und Nicht-Admin-Konten zur Validierung hinzu.</span><span class="sxs-lookup"><span data-stu-id="1a198-131">If you must configure a Teams tenant to use your app, include those instructions and admin and non-admin accounts for validation.</span></span>

### <a name="video-optional"></a><span data-ttu-id="1a198-132">Video (optional)</span><span class="sxs-lookup"><span data-stu-id="1a198-132">Video (optional)</span></span>

<span data-ttu-id="1a198-133">Stellen Sie eine Aufzeichnung Ihrer App bereit, damit Microsoft die Funktionalität vollständig verstehen kann.</span><span class="sxs-lookup"><span data-stu-id="1a198-133">Provide a recording of your app so that Microsoft can fully understand its functionality.</span></span>

## <a name="create-your-store-listing-details"></a><span data-ttu-id="1a198-134">Erstellen Sie Ihre Shop-Eintragsdetails</span><span class="sxs-lookup"><span data-stu-id="1a198-134">Create your store listing details</span></span>

<span data-ttu-id="1a198-135">Die Informationen, die Sie an [das Partner Center](https://partner.microsoft.com) übermitteln,&#8212;einschließlich Ihres Namens, Ihrer Beschreibungen, Symbole und Bilder&#8212;wird zum Teams-Store und Microsoft AppSource-Eintrag für Ihre App.</span><span class="sxs-lookup"><span data-stu-id="1a198-135">The information that you submit to [Partner Center](https://partner.microsoft.com)&#8212;including your name, descriptions, icons, and images&#8212;becomes the Teams store and Microsoft AppSource listing for your app.</span></span>

<span data-ttu-id="1a198-136">Ein Store-Eintrag kann der erste Eindruck Ihrer App sein.</span><span class="sxs-lookup"><span data-stu-id="1a198-136">A store listing may be someone's first impression of your app.</span></span> <span data-ttu-id="1a198-137">Erhöhen Sie die Installationen mit einem Eintrag, der die Vorteile, Funktionen und Marken Ihrer App effektiv vermittelt.</span><span class="sxs-lookup"><span data-stu-id="1a198-137">Increase installations with a listing that effectively conveys your app's benefits, functionality, and brand.</span></span>

### <a name="specify-a-short-name"></a><span data-ttu-id="1a198-138">Angeben eines kurzen Namens</span><span class="sxs-lookup"><span data-stu-id="1a198-138">Specify a short name</span></span>

<span data-ttu-id="1a198-139">Der Name Ihrer App (insbesondere der [*kurzbeinige Name)*](~/resources/schema/manifest-schema.md#name)spielt eine entscheidende Rolle, wie Benutzer sie im Store entdecken.</span><span class="sxs-lookup"><span data-stu-id="1a198-139">Your app's name (specifically, its [*short name*](~/resources/schema/manifest-schema.md#name)) plays a crucial role in how users discover it in the store.</span></span>

:::row:::

   :::column span="3":::
      :::image type="content" source="../../../../assets/images/store-detail-page/AppName-02.png" alt-text="Beispiel-Screenshot zeigt, wo der Kurzname einer App in einem Store-Eintrag angezeigt wird.":::
   :::column-end:::
   :::column span="1":::
   :::column-end:::

:::row-end:::

<span data-ttu-id="1a198-141">Stellen Sie sicher, dass Ihr Kurzname den Richtlinien für die [Speichervalidierung](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md#11-app-name)entspricht.</span><span class="sxs-lookup"><span data-stu-id="1a198-141">Make sure your short name adheres to the [store validation guidelines](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md#11-app-name).</span></span>

### <a name="write-descriptions"></a><span data-ttu-id="1a198-142">Schreiben von Beschreibungen</span><span class="sxs-lookup"><span data-stu-id="1a198-142">Write descriptions</span></span>

<span data-ttu-id="1a198-143">Sie müssen eine kurze und lange Beschreibung Ihrer App haben.</span><span class="sxs-lookup"><span data-stu-id="1a198-143">You must have a short and long description of your app.</span></span>

#### <a name="short-description"></a><span data-ttu-id="1a198-144">Kurzbeschreibung</span><span class="sxs-lookup"><span data-stu-id="1a198-144">Short description</span></span>

<span data-ttu-id="1a198-145">Eine kurze Zusammenfassung Ihrer App, die originell, ansprechend und an Ihre Zielgruppe gerichtet sein sollte.</span><span class="sxs-lookup"><span data-stu-id="1a198-145">A concise summary of your app that should be original, engaging, and directed at your target audience.</span></span> <span data-ttu-id="1a198-146">Halten Sie die Kurzbeschreibung auf einen Satz.</span><span class="sxs-lookup"><span data-stu-id="1a198-146">Keep the short description to one sentence.</span></span>

:::row:::

   :::column span="3":::
      :::image type="content" source="~/assets/images/store-detail-page/ShortDescription-02.png" alt-text="Beispiel-Screenshot zeigt, wo die Kurzbeschreibung einer App in einem Store-Eintrag angezeigt wird.":::
   :::column-end:::
   :::column span="1":::
   :::column-end:::

:::row-end:::

<span data-ttu-id="1a198-148">Stellen Sie sicher, dass Ihre Kurzbeschreibung den Richtlinien für die [Speichervalidierung](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md#431-short-description)entspricht.</span><span class="sxs-lookup"><span data-stu-id="1a198-148">Make sure your short description adheres to the [store validation guidelines](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md#431-short-description).</span></span>

#### <a name="long-description"></a><span data-ttu-id="1a198-149">Lange Beschreibung</span><span class="sxs-lookup"><span data-stu-id="1a198-149">Long description</span></span>

<span data-ttu-id="1a198-150">Die lange Beschreibung kann eine Erzählung bereitstellen, die die Hauptfunktionen Ihrer App, die probleme, die sie löst, und ihre Zielgruppe hervorhebt.</span><span class="sxs-lookup"><span data-stu-id="1a198-150">The long description can provide a narrative that highlights your app's main features, the problems it solves, and its target audience.</span></span> <span data-ttu-id="1a198-151">Während diese Beschreibung bis zu 4.000 Zeichen lang sein kann, lesen die meisten Benutzer nur zwischen 300-500 Wörtern.</span><span class="sxs-lookup"><span data-stu-id="1a198-151">While this description can be as long as 4,000 characters, most users will only read between 300-500 words.</span></span>

:::row:::

   :::column span="3":::
      :::image type="content" source="~/assets/images/store-detail-page/LongDescription-02.png" alt-text="Beispiel-Screenshot zeigt, wo die lange Beschreibung einer App in einem Store-Eintrag angezeigt wird.":::
   :::column-end:::
   :::column span="1":::
   :::column-end:::

:::row-end:::

<span data-ttu-id="1a198-153">Stellen Sie sicher, dass Ihre lange Beschreibung den Richtlinien für die [Speichervalidierung](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md#432-long-description)entspricht.</span><span class="sxs-lookup"><span data-stu-id="1a198-153">Make sure your long description adheres to the [store validation guidelines](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md#432-long-description).</span></span>

### <a name="adhere-to-icon-design-guidelines"></a><span data-ttu-id="1a198-154">Einhaltung der Richtlinien für das Icon-Design</span><span class="sxs-lookup"><span data-stu-id="1a198-154">Adhere to icon design guidelines</span></span>

<span data-ttu-id="1a198-155">Symbole sind eines der Wichtigsten Elemente, die Benutzer beim Durchsuchen des Shops sehen.</span><span class="sxs-lookup"><span data-stu-id="1a198-155">Icons are one of the main elements users see when browsing the store.</span></span> <span data-ttu-id="1a198-156">Ihre Symbole sollten die Marke und den Zweck Ihrer App kommunizieren und gleichzeitig Teams Anforderungen einhalten.</span><span class="sxs-lookup"><span data-stu-id="1a198-156">Your icons should communicate your app's brand and purpose while also adhering to Teams requirements.</span></span>

<span data-ttu-id="1a198-157">Weitere Informationen finden Sie unter [Anleitung zum Erstellen Teams App-Symbole](~/concepts/build-and-test/apps-package.md#app-icons).</span><span class="sxs-lookup"><span data-stu-id="1a198-157">For more information, see [guidance on creating Teams app icons](~/concepts/build-and-test/apps-package.md#app-icons).</span></span>

### <a name="capture-screenshots"></a><span data-ttu-id="1a198-158">Screenshots erfassen</span><span class="sxs-lookup"><span data-stu-id="1a198-158">Capture screenshots</span></span>

<span data-ttu-id="1a198-159">Screenshots bieten eine prominente visuelle Vorschau Ihrer App, um Ihren App-Namen, Ihr Symbol und Ihre Beschreibungen zu ergänzen.</span><span class="sxs-lookup"><span data-stu-id="1a198-159">Screenshots provide a prominent visual preview of your app to complement your app name, icon, and descriptions.</span></span>

:::row:::

   :::column span="3":::
      :::image type="content" source="~/assets/images/store-detail-page/Screenshot-01.png" alt-text="Beispiel-Screenshots, bei denen App-Screenshots in einem Store-Eintrag angezeigt werden.":::
   :::column-end:::
   :::column span="1":::
   :::column-end:::

:::row-end:::

<span data-ttu-id="1a198-161">Erinnern Sie sich an die folgenden Screenshots:</span><span class="sxs-lookup"><span data-stu-id="1a198-161">Remember the following about screenshots:</span></span>

* <span data-ttu-id="1a198-162">Sie können bis zu fünf Screenshots pro Liste haben.</span><span class="sxs-lookup"><span data-stu-id="1a198-162">You can have up to five screenshots per listing.</span></span>
* <span data-ttu-id="1a198-163">Zu den unterstützten Dateitypen gehören PNG, JPEG und GIF.</span><span class="sxs-lookup"><span data-stu-id="1a198-163">Supported file types include PNG, JPEG, and GIF.</span></span>
* <span data-ttu-id="1a198-164">Die Abmessungen sollten 1366x768 Pixel betragen.</span><span class="sxs-lookup"><span data-stu-id="1a198-164">Dimensions should be 1366x768 pixels.</span></span>
* <span data-ttu-id="1a198-165">Maximale Größe von 1.024 KB.</span><span class="sxs-lookup"><span data-stu-id="1a198-165">Maximum size of 1,024 KB.</span></span>

<span data-ttu-id="1a198-166">Bewährte Methoden finden Sie in den folgenden Ressourcen:</span><span class="sxs-lookup"><span data-stu-id="1a198-166">For best practices, see the following resources:</span></span>

* [<span data-ttu-id="1a198-167">Teams-Shop-Validierungsrichtlinien</span><span class="sxs-lookup"><span data-stu-id="1a198-167">Teams store validation guidelines</span></span>](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md#44-screenshots)
* [<span data-ttu-id="1a198-168">Erstellen effektiver Bilder für Microsoft App Stores</span><span class="sxs-lookup"><span data-stu-id="1a198-168">Craft effective images for Microsoft app stores</span></span>](/office/dev/store/craft-effective-appsource-store-images)

### <a name="create-a-video"></a><span data-ttu-id="1a198-169">Erstellen eines Videos</span><span class="sxs-lookup"><span data-stu-id="1a198-169">Create a video</span></span>

<span data-ttu-id="1a198-170">Ein Video in Ihrem Eintrag kann die effektivste Möglichkeit sein, zu kommunizieren, warum Benutzer Ihre App verwenden sollten.</span><span class="sxs-lookup"><span data-stu-id="1a198-170">A video in your listing can be the most effective way to communicate why people should use your app.</span></span> <span data-ttu-id="1a198-171">Die folgenden Fragen sollten Sie in einem Video beantworten:</span><span class="sxs-lookup"><span data-stu-id="1a198-171">You should address the following questions in a video:</span></span>

* <span data-ttu-id="1a198-172">Wer ist Ihre App?</span><span class="sxs-lookup"><span data-stu-id="1a198-172">Who is your app for?</span></span>
* <span data-ttu-id="1a198-173">Welche Probleme kann Ihre App lösen?</span><span class="sxs-lookup"><span data-stu-id="1a198-173">What problems can your app solve?</span></span>
* <span data-ttu-id="1a198-174">Wie funktioniert Ihre App?</span><span class="sxs-lookup"><span data-stu-id="1a198-174">How does your app work?</span></span>
* <span data-ttu-id="1a198-175">Welche weiteren Vorteile haben Sie bei der Nutzung Ihrer App?</span><span class="sxs-lookup"><span data-stu-id="1a198-175">What other benefits do you get from using your app?</span></span>

#### <a name="best-practices-for-videos"></a><span data-ttu-id="1a198-176">Bewährte Methoden für Videos</span><span class="sxs-lookup"><span data-stu-id="1a198-176">Best practices for videos</span></span>

* <span data-ttu-id="1a198-177">Halten Sie Ihr Video zwischen 30-90 Sekunden.</span><span class="sxs-lookup"><span data-stu-id="1a198-177">Keep your video between 30-90 seconds.</span></span>
* <span data-ttu-id="1a198-178">Ziel für Qualität.</span><span class="sxs-lookup"><span data-stu-id="1a198-178">Aim for quality.</span></span> <span data-ttu-id="1a198-179">In einem Eintrag sehen Benutzer Ihr Video vor Screenshots.</span><span class="sxs-lookup"><span data-stu-id="1a198-179">In a listing, users will see your video before screenshots.</span></span>

### <a name="select-a-category-for-your-app"></a><span data-ttu-id="1a198-180">Auswählen einer Kategorie für Ihre App</span><span class="sxs-lookup"><span data-stu-id="1a198-180">Select a category for your app</span></span>

<span data-ttu-id="1a198-181">Während der Übermittlung werden Sie aufgefordert, Ihre App zu kategorisieren.</span><span class="sxs-lookup"><span data-stu-id="1a198-181">During submission, you're asked to categorize your app.</span></span> <span data-ttu-id="1a198-182">In der folgenden Tabelle werden Teams Shopkategorien den im [Partner Center](https://aka.ms/PartnerCenterHomePage)aufgeführten Kategorien zugeordnet.</span><span class="sxs-lookup"><span data-stu-id="1a198-182">The following table maps Teams store categories to the categories listed in [Partner Center](https://aka.ms/PartnerCenterHomePage).</span></span>

| <span data-ttu-id="1a198-183">Teams Kategorien</span><span class="sxs-lookup"><span data-stu-id="1a198-183">Teams categories</span></span>       | <span data-ttu-id="1a198-184">Partner Center-Kategorien</span><span class="sxs-lookup"><span data-stu-id="1a198-184">Partner Center categories</span></span>  |
|:---------------------|:---------------|
| <span data-ttu-id="1a198-185">Analytics und BI</span><span class="sxs-lookup"><span data-stu-id="1a198-185">Analytics and BI</span></span> | <span data-ttu-id="1a198-186">Analytics, Datenvisualisierung und BI</span><span class="sxs-lookup"><span data-stu-id="1a198-186">Analytics, Data Visualization and BI</span></span> |
| <span data-ttu-id="1a198-187">Entwickler und IT</span><span class="sxs-lookup"><span data-stu-id="1a198-187">Developer and IT</span></span> | <span data-ttu-id="1a198-188">Entwicklertools, IT-Administrator</span><span class="sxs-lookup"><span data-stu-id="1a198-188">Developer Tools, IT Admin</span></span> |
| <span data-ttu-id="1a198-189">Schulung und Weiterbildung</span><span class="sxs-lookup"><span data-stu-id="1a198-189">Education</span></span> | <span data-ttu-id="1a198-190">Schulung und Weiterbildung</span><span class="sxs-lookup"><span data-stu-id="1a198-190">Education</span></span> |
| <span data-ttu-id="1a198-191">Personalwesen</span><span class="sxs-lookup"><span data-stu-id="1a198-191">Human resources</span></span> | <span data-ttu-id="1a198-192">Personal wesenund Personal und Recruiting</span><span class="sxs-lookup"><span data-stu-id="1a198-192">Human Resources and Recruiting</span></span> |
| <span data-ttu-id="1a198-193">Produktivität</span><span class="sxs-lookup"><span data-stu-id="1a198-193">Productivity</span></span> | <span data-ttu-id="1a198-194">Content Management, Dateien und Dokumente, Produktivität, Schulung und Tutorials und Dienstprogramme</span><span class="sxs-lookup"><span data-stu-id="1a198-194">Content Management, Files and documents, Productivity, Training and Tutorials, and Utilities</span></span> |
| <span data-ttu-id="1a198-195">Projektmanagement</span><span class="sxs-lookup"><span data-stu-id="1a198-195">Project management</span></span> | <span data-ttu-id="1a198-196">Kommunikation, Project Management, Workflow und Business Management</span><span class="sxs-lookup"><span data-stu-id="1a198-196">Communication, Project Management, Workflow, and Business Management</span></span> |
| <span data-ttu-id="1a198-197">Vertrieb und Support</span><span class="sxs-lookup"><span data-stu-id="1a198-197">Sales and support</span></span> | <span data-ttu-id="1a198-198">Kunden- und Kontaktmanagement, Kundensupport, Finanzmanagement, Vertrieb und Marketing</span><span class="sxs-lookup"><span data-stu-id="1a198-198">Customer and Contact Management, Customer Support, Financial Management, Sales and Marketing</span></span> |
| <span data-ttu-id="1a198-199">Sozial und Spaß</span><span class="sxs-lookup"><span data-stu-id="1a198-199">Social and fun</span></span> | <span data-ttu-id="1a198-200">Bild- und Videogalerien, Lebensstil, Nachrichten und Wetter, Soziales, Reisen und Navigation</span><span class="sxs-lookup"><span data-stu-id="1a198-200">Image and Video Galleries, Lifestyle, News and Weather, Social, Travel, and Navigation</span></span> |

### <a name="localize-your-store-listing"></a><span data-ttu-id="1a198-201">Lokalisieren Sie Ihren Shop-Eintrag</span><span class="sxs-lookup"><span data-stu-id="1a198-201">Localize your store listing</span></span>

<span data-ttu-id="1a198-202">Partner Center unterstützt [lokalisierte Shop-Einträge](/office/dev/store/prepare-localized-solutions).</span><span class="sxs-lookup"><span data-stu-id="1a198-202">Partner Center supports [localized store listings](/office/dev/store/prepare-localized-solutions).</span></span> <span data-ttu-id="1a198-203">Weitere Informationen finden Sie unter [Lokalisierung Ihrer Teams App-Liste](../../../../concepts/build-and-test/apps-localization.md).</span><span class="sxs-lookup"><span data-stu-id="1a198-203">For more information, see [how to localize your Teams app listing](../../../../concepts/build-and-test/apps-localization.md).</span></span>

## <a name="complete-publisher-verification"></a><span data-ttu-id="1a198-204">Vollständige Publisher-Überprüfung</span><span class="sxs-lookup"><span data-stu-id="1a198-204">Complete Publisher Verification</span></span>

<span data-ttu-id="1a198-205">[Publisher Überprüfung](/azure/active-directory/develop/publisher-verification-overview) ist für Teams im Store aufgeführten Apps erforderlich.</span><span class="sxs-lookup"><span data-stu-id="1a198-205">[Publisher Verification](/azure/active-directory/develop/publisher-verification-overview) is required for Teams apps listed in the store.</span></span> <span data-ttu-id="1a198-206">Weitere Informationen finden Sie unter [Häufig gestellte Fragen](/azure/active-directory/develop/publisher-verification-overview#frequently-asked-questions), [wie Sie Ihre App als verifizierten Herausgeber markieren](/azure/active-directory/develop/mark-app-as-publisher-verified)und die [Herausgeberüberprüfung beheben](/azure/active-directory/develop/troubleshoot-publisher-verification).</span><span class="sxs-lookup"><span data-stu-id="1a198-206">For more information, see [frequently asked questions](/azure/active-directory/develop/publisher-verification-overview#frequently-asked-questions), [how to mark your app as publisher verified](/azure/active-directory/develop/mark-app-as-publisher-verified), and [troubleshoot publisher verification](/azure/active-directory/develop/troubleshoot-publisher-verification).</span></span>

## <a name="complete-publisher-attestation"></a><span data-ttu-id="1a198-207">Vollständige Publisher-Bescheinigung</span><span class="sxs-lookup"><span data-stu-id="1a198-207">Complete Publisher Attestation</span></span>

<span data-ttu-id="1a198-208">[Publisher Attestation](/microsoft-365-app-certification/docs/attestation) ist auch für Teams apps erforderlich, die im Store aufgelistet sind.</span><span class="sxs-lookup"><span data-stu-id="1a198-208">[Publisher Attestation](/microsoft-365-app-certification/docs/attestation) is also required for Teams apps listed in the store.</span></span> <span data-ttu-id="1a198-209">Der Prozess umfasst die Durchführung einer Selbstbewertung der Sicherheits-, Datenverarbeitungs- und Compliance-Praktiken Ihrer App, die potenziellen Kunden helfen kann, fundierte Entscheidungen über die Verwendung Ihrer App zu treffen.</span><span class="sxs-lookup"><span data-stu-id="1a198-209">The process includes completing a self-assessment of your app's security, data handling, and compliance practices that can help potential customers make informed decisions about using your app.</span></span>

> [!NOTE]
> <span data-ttu-id="1a198-210">Wenn Sie eine neue App einreichen, können Sie Publisher Attestation erst dann offiziell abschließen, wenn Ihre App im Teams Store aufgeführt ist.</span><span class="sxs-lookup"><span data-stu-id="1a198-210">If you're submitting a new app, you can't officially complete Publisher Attestation until your app is listed on the Teams store.</span></span> <span data-ttu-id="1a198-211">Wenn Sie eine aufgelistete App aktualisieren, schließen Sie Publisher Bescheinigung ab, bevor Sie die neueste Version der App zur Validierung einreichen.</span><span class="sxs-lookup"><span data-stu-id="1a198-211">If you're updating a listed app, complete Publisher Attestation before you submit the latest version of the app for validation.</span></span>

## <a name="next-step"></a><span data-ttu-id="1a198-212">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="1a198-212">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="1a198-213">Übermitteln Ihrer App</span><span class="sxs-lookup"><span data-stu-id="1a198-213">Submit your app</span></span>](/office/dev/store/add-in-submission-guide)
