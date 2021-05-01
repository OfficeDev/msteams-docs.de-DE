---
title: Vorbereiten der Store-Übermittlung
description: Beschreibt die letzten Schritte vor dem Übermitteln Microsoft Teams App, die im Store aufgeführt werden soll.
ms.topic: how-to
localization_priority: Normal
author: heath-hamilton
ms.author: surbhigupta
ms.openlocfilehash: d46d21c3d984b5688c00857e485210b0f0fcf2c7
ms.sourcegitcommit: 25c9ad27f99682caaa7347840578b118c63b8f69
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2021
ms.locfileid: "52101681"
---
# <a name="prepare-your-microsoft-teams-store-submission"></a><span data-ttu-id="7bc6a-103">Vorbereiten der Microsoft Teams Speicherübermittlung</span><span class="sxs-lookup"><span data-stu-id="7bc6a-103">Prepare your Microsoft Teams store submission</span></span>

<span data-ttu-id="7bc6a-104">Sie haben Ihre App entworfen, erstellt und Microsoft Teams getestet.</span><span class="sxs-lookup"><span data-stu-id="7bc6a-104">You've designed, built, and tested your Microsoft Teams app.</span></span> <span data-ttu-id="7bc6a-105">Jetzt können Sie sie auflisten, damit Die Benutzer Ihre App entdecken und mit der Verwendung beginnen können.</span><span class="sxs-lookup"><span data-stu-id="7bc6a-105">Now you're ready to list it so people can discover and start using your app.</span></span>

<span data-ttu-id="7bc6a-106">Bevor Sie Ihre App an [Partner Center übermitteln,](/office/dev/store/use-partner-center-to-submit-to-appsource)stellen Sie sicher, dass Sie folgendes getan haben.</span><span class="sxs-lookup"><span data-stu-id="7bc6a-106">Before you submit your app to [Partner Center](/office/dev/store/use-partner-center-to-submit-to-appsource), make sure you've done the following.</span></span>

## <a name="validate-your-app-package"></a><span data-ttu-id="7bc6a-107">Überprüfen Des App-Pakets</span><span class="sxs-lookup"><span data-stu-id="7bc6a-107">Validate your app package</span></span>

<span data-ttu-id="7bc6a-108">Während Ihre App möglicherweise in einer Testumgebung funktioniert, sollten Sie Ihr App-Paket überprüfen, um zu vermeiden, dass während des Übermittlungsprozesses Probleme auftreten.</span><span class="sxs-lookup"><span data-stu-id="7bc6a-108">While your app may be working in a test environment, you should check your app package to avoid running into issues during the submission process.</span></span>

<span data-ttu-id="7bc6a-109">Das Microsoft Teams-App-Validierungstool hilft Ihnen, Probleme zu identifizieren und zu beheben, bevor Sie sie an Partner Center übermitteln.</span><span class="sxs-lookup"><span data-stu-id="7bc6a-109">The Microsoft Teams app validation tool helps you identify and fix issues before submitting to Partner Center.</span></span> <span data-ttu-id="7bc6a-110">Das Tool überprüft die Konfigurationen Ihrer App automatisch mit den gleichen Testfällen, die während der Speicherüberprüfung verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="7bc6a-110">The tool automatically checks your app's configurations against the same test cases used during store validation.</span></span>

1. <span data-ttu-id="7bc6a-111">Wechseln Sie zum [Microsoft Teams App-Überprüfungstool](https://dev.teams.microsoft.com/appvalidation.html).</span><span class="sxs-lookup"><span data-stu-id="7bc6a-111">Go to the [Microsoft Teams app validation tool](https://dev.teams.microsoft.com/appvalidation.html).</span></span> <span data-ttu-id="7bc6a-112">(Hinweis: Das Tool ist auch in [App Studio verfügbar.)](../../../build-and-test/app-studio-overview.md)</span><span class="sxs-lookup"><span data-stu-id="7bc6a-112">(Note: The tool is also available in [App Studio](../../../build-and-test/app-studio-overview.md).)</span></span>
1. <span data-ttu-id="7bc6a-113">Hochladen App-Paket, um die automatisierten Tests durchzuführen.</span><span class="sxs-lookup"><span data-stu-id="7bc6a-113">Upload your app package to run the automated tests.</span></span>
1. <span data-ttu-id="7bc6a-114">Wechseln Sie zur **Vorläufigen Prüfliste,** und überprüfen Sie die Testfälle, die schwer zu automatisieren sind.</span><span class="sxs-lookup"><span data-stu-id="7bc6a-114">Go to the **Preliminary checklist** and review the test cases that are difficult to automate.</span></span>
1. <span data-ttu-id="7bc6a-115">[Beheben Sie Probleme mit Ihren Konfigurationen](~/resources/schema/manifest-schema.md) oder Apps im Allgemeinen, wenn die automatisierten Tests Fehler verursachen oder Sie nicht alle Kriterien in der Prüfliste erfüllt haben.</span><span class="sxs-lookup"><span data-stu-id="7bc6a-115">[Fix issues with your configurations](~/resources/schema/manifest-schema.md) or app in general if the automated tests give you errors or you haven't met all the criteria in the checklist.</span></span>

## <a name="compile-testing-instructions"></a><span data-ttu-id="7bc6a-116">Kompilieren von Testanweisungen</span><span class="sxs-lookup"><span data-stu-id="7bc6a-116">Compile testing instructions</span></span>

<span data-ttu-id="7bc6a-117">Stellen Sie Anweisungen und Ressourcen zur Verfügung, mit denen die Prüfer Ihre App testen können, einschließlich Testkonten, Anmeldeinformationen und Lizenzschlüsseln.</span><span class="sxs-lookup"><span data-stu-id="7bc6a-117">Provide instructions and resources to help the reviewers test your app, including test accounts, credentials, and license keys.</span></span> <span data-ttu-id="7bc6a-118">Sie können Anweisungen im Partner Center hinzufügen oder sie an einen öffentlich verfügbaren Speicherort in SharePoint.</span><span class="sxs-lookup"><span data-stu-id="7bc6a-118">You can add instructions in Partner Center or upload them to a publicly available location on SharePoint.</span></span>

### <a name="feature-list"></a><span data-ttu-id="7bc6a-119">Featureliste</span><span class="sxs-lookup"><span data-stu-id="7bc6a-119">Feature list</span></span>

<span data-ttu-id="7bc6a-120">Geben Sie Details zu den Funktionen Ihrer App in Teams und Schritte zum Testen der einzelnen Apps an.</span><span class="sxs-lookup"><span data-stu-id="7bc6a-120">Provide details about your app's capabilities in Teams and steps for testing each one.</span></span>

### <a name="accounts"></a><span data-ttu-id="7bc6a-121">Konten</span><span class="sxs-lookup"><span data-stu-id="7bc6a-121">Accounts</span></span>

<span data-ttu-id="7bc6a-122">Sie müssen Testkonten bereitstellen, wenn Ihre App eine Lizenz- oder Back-End-Safelisting erfordert.</span><span class="sxs-lookup"><span data-stu-id="7bc6a-122">You must provide test accounts if your app requires a license or backend safelisting.</span></span> <span data-ttu-id="7bc6a-123">Alle konten, die Sie bereitstellen, müssen vorab ausgefüllte Daten enthalten, um tests zu erleichtern.</span><span class="sxs-lookup"><span data-stu-id="7bc6a-123">All accounts you provide must include pre-populated data to facilitate testing.</span></span>

<span data-ttu-id="7bc6a-124">Je nach den Features Ihrer App müssen Sie möglicherweise folgendes bereitstellen:</span><span class="sxs-lookup"><span data-stu-id="7bc6a-124">Depending on your app's features, you may need to provide all of the following:</span></span>

* <span data-ttu-id="7bc6a-125">Administratorkonto (erforderlich)</span><span class="sxs-lookup"><span data-stu-id="7bc6a-125">Admin account (required)</span></span>
* <span data-ttu-id="7bc6a-126">Nicht-Administrator-Konto (erforderlich)</span><span class="sxs-lookup"><span data-stu-id="7bc6a-126">Non-admin account (required)</span></span>
* <span data-ttu-id="7bc6a-127">Ein Konto, das nicht vorkonfiguriert ist, um die Anmeldeerfahrung bei der ersten Ausführung ordnungsgemäß zu testen (erforderlich)</span><span class="sxs-lookup"><span data-stu-id="7bc6a-127">An account that isn't pre-configured in order to properly test the first-run sign-in experience (required)</span></span>
* <span data-ttu-id="7bc6a-128">Ein Konto mit Zugriff auf Premium- oder Upgradefeatures (sofern zutreffend)</span><span class="sxs-lookup"><span data-stu-id="7bc6a-128">An account with access to premium or upgraded features (if applicable)</span></span>
* <span data-ttu-id="7bc6a-129">Zwei Konten im gleichen Mandanten, um die Zusammenarbeit für Apps zu testen, die in freigegebenen Kontexten funktionieren (sofern zutreffend)</span><span class="sxs-lookup"><span data-stu-id="7bc6a-129">Two accounts in the same tenant to test the collaboration experience for apps that work in shared contexts (if applicable)</span></span>

### <a name="tenant-configurations"></a><span data-ttu-id="7bc6a-130">Mandantenkonfigurationen</span><span class="sxs-lookup"><span data-stu-id="7bc6a-130">Tenant configurations</span></span>

<span data-ttu-id="7bc6a-131">Wenn Sie einen mandanten Teams für die Verwendung Ihrer App konfigurieren müssen, fügen Sie diese Anweisungen sowie Administrator- und Nicht-Admin-Konten zur Überprüfung ein.</span><span class="sxs-lookup"><span data-stu-id="7bc6a-131">If you must configure a Teams tenant to use your app, include those instructions and admin and non-admin accounts for validation.</span></span>

### <a name="video-optional"></a><span data-ttu-id="7bc6a-132">Video (optional)</span><span class="sxs-lookup"><span data-stu-id="7bc6a-132">Video (optional)</span></span>

<span data-ttu-id="7bc6a-133">Stellen Sie eine Aufzeichnung Ihrer App bereit, damit Microsoft seine Funktionalität vollständig verstehen kann.</span><span class="sxs-lookup"><span data-stu-id="7bc6a-133">Provide a recording of your app so that Microsoft can fully understand its functionality.</span></span>

## <a name="create-your-store-listing-details"></a><span data-ttu-id="7bc6a-134">Erstellen von Details zum Storeeintrag</span><span class="sxs-lookup"><span data-stu-id="7bc6a-134">Create your store listing details</span></span>

<span data-ttu-id="7bc6a-135">Die informationen, die Sie an [Partner Center](https://partner.microsoft.com)&#8212;einschließlich Ihres Namens, Beschreibungen, Symbole und Bilder&#8212;wird der Teams-Store und Microsoft AppSource-Eintrag für Ihre App.</span><span class="sxs-lookup"><span data-stu-id="7bc6a-135">The information that you submit to [Partner Center](https://partner.microsoft.com)&#8212;including your name, descriptions, icons, and images&#8212;becomes the Teams store and Microsoft AppSource listing for your app.</span></span>

<span data-ttu-id="7bc6a-136">Ein Storeeintrag kann der erste Eindruck ihrer App sein.</span><span class="sxs-lookup"><span data-stu-id="7bc6a-136">A store listing may be someone's first impression of your app.</span></span> <span data-ttu-id="7bc6a-137">Erhöhen Sie Installationen mit einem Eintrag, der die Vorteile, Funktionalität und Marke Ihrer App effektiv vermittelt.</span><span class="sxs-lookup"><span data-stu-id="7bc6a-137">Increase installations with a listing that effectively conveys your app's benefits, functionality, and brand.</span></span>

### <a name="specify-a-short-name"></a><span data-ttu-id="7bc6a-138">Angeben eines kurzen Namens</span><span class="sxs-lookup"><span data-stu-id="7bc6a-138">Specify a short name</span></span>

<span data-ttu-id="7bc6a-139">Der Name Ihrer App (insbesondere der kurz bezeichnete [*Name)*](~/resources/schema/manifest-schema.md#name)spielt eine entscheidende Rolle bei der Benutzerentkung im Store.</span><span class="sxs-lookup"><span data-stu-id="7bc6a-139">Your app's name (specifically, its [*short name*](~/resources/schema/manifest-schema.md#name)) plays a crucial role in how users discover it in the store.</span></span>

:::row:::

   :::column span="3":::
      :::image type="content" source="../../../../assets/images/store-detail-page/AppName-02.png" alt-text="Beispiel screenshot highlights where an app's short name displays in a store listing.":::
   :::column-end:::
   :::column span="1":::
   :::column-end:::

:::row-end:::

<span data-ttu-id="7bc6a-141">Stellen Sie sicher, dass Ihr kurzer Name den Richtlinien für [die Speicherüberprüfung entspricht.](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md#11-app-name)</span><span class="sxs-lookup"><span data-stu-id="7bc6a-141">Make sure your short name adheres to the [store validation guidelines](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md#11-app-name).</span></span>

### <a name="write-descriptions"></a><span data-ttu-id="7bc6a-142">Schreibbeschreibungen</span><span class="sxs-lookup"><span data-stu-id="7bc6a-142">Write descriptions</span></span>

<span data-ttu-id="7bc6a-143">Sie müssen eine kurze und lange Beschreibung Ihrer App haben.</span><span class="sxs-lookup"><span data-stu-id="7bc6a-143">You must have a short and long description of your app.</span></span>

#### <a name="short-description"></a><span data-ttu-id="7bc6a-144">Kurzbeschreibung</span><span class="sxs-lookup"><span data-stu-id="7bc6a-144">Short description</span></span>

<span data-ttu-id="7bc6a-145">Eine kurze Zusammenfassung Ihrer App, die ursprünglich, mitreißend und an Ihre Zielgruppe gerichtet sein sollte.</span><span class="sxs-lookup"><span data-stu-id="7bc6a-145">A concise summary of your app that should be original, engaging, and directed at your target audience.</span></span> <span data-ttu-id="7bc6a-146">Behalten Sie die kurz beschriebene Beschreibung auf einen Satz bei.</span><span class="sxs-lookup"><span data-stu-id="7bc6a-146">Keep the short description to one sentence.</span></span>

:::row:::

   :::column span="3":::
      :::image type="content" source="~/assets/images/store-detail-page/ShortDescription-02.png" alt-text="Beispiel screenshot highlights where an app's short description displays in a store listing.":::
   :::column-end:::
   :::column span="1":::
   :::column-end:::

:::row-end:::

<span data-ttu-id="7bc6a-148">Stellen Sie sicher, dass Ihre kurze Beschreibung den Richtlinien für die [Speicherüberprüfung entspricht.](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md#431-short-description)</span><span class="sxs-lookup"><span data-stu-id="7bc6a-148">Make sure your short description adheres to the [store validation guidelines](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md#431-short-description).</span></span>

#### <a name="long-description"></a><span data-ttu-id="7bc6a-149">Lange Beschreibung</span><span class="sxs-lookup"><span data-stu-id="7bc6a-149">Long description</span></span>

<span data-ttu-id="7bc6a-150">Die lange Beschreibung kann eine Erzählung enthalten, die die Wichtigsten Features Ihrer App, die probleme, die sie löst, und ihre Zielgruppe hervorhebt.</span><span class="sxs-lookup"><span data-stu-id="7bc6a-150">The long description can provide a narrative that highlights your app's main features, the problems it solves, and its target audience.</span></span> <span data-ttu-id="7bc6a-151">Während diese Beschreibung bis zu 4.000 Zeichen umfassen kann, lesen die meisten Benutzer nur zwischen 300 und 500 Wörter.</span><span class="sxs-lookup"><span data-stu-id="7bc6a-151">While this description can be as long as 4,000 characters, most users will only read between 300-500 words.</span></span>

:::row:::

   :::column span="3":::
      :::image type="content" source="~/assets/images/store-detail-page/LongDescription-02.png" alt-text="Beispiel screenshot highlights where an app's long description displays in a store listing.":::
   :::column-end:::
   :::column span="1":::
   :::column-end:::

:::row-end:::

<span data-ttu-id="7bc6a-153">Stellen Sie sicher, dass ihre lange Beschreibung den Richtlinien für die [Speicherüberprüfung entspricht.](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md#432-long-description)</span><span class="sxs-lookup"><span data-stu-id="7bc6a-153">Make sure your long description adheres to the [store validation guidelines](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md#432-long-description).</span></span>

### <a name="adhere-to-icon-design-guidelines"></a><span data-ttu-id="7bc6a-154">Einhalten von Richtlinien für das Symboldesign</span><span class="sxs-lookup"><span data-stu-id="7bc6a-154">Adhere to icon design guidelines</span></span>

<span data-ttu-id="7bc6a-155">Symbole sind eines der Wichtigsten Elemente, die Benutzern beim Durchsuchen des Informationsspeichers angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="7bc6a-155">Icons are one of the main elements users see when browsing the store.</span></span> <span data-ttu-id="7bc6a-156">Ihre Symbole sollten die Marke und den Zweck Ihrer App kommunizieren und gleichzeitig Teams erfüllen.</span><span class="sxs-lookup"><span data-stu-id="7bc6a-156">Your icons should communicate your app's brand and purpose while also adhering to Teams requirements.</span></span>

<span data-ttu-id="7bc6a-157">Weitere Informationen finden Sie unter [Anleitungen zum Erstellen Teams App-Symbole](~/concepts/build-and-test/apps-package.md#app-icons).</span><span class="sxs-lookup"><span data-stu-id="7bc6a-157">For more information, see [guidance on creating Teams app icons](~/concepts/build-and-test/apps-package.md#app-icons).</span></span>

### <a name="capture-screenshots"></a><span data-ttu-id="7bc6a-158">Screenshots erfassen</span><span class="sxs-lookup"><span data-stu-id="7bc6a-158">Capture screenshots</span></span>

<span data-ttu-id="7bc6a-159">Screenshots bieten eine prominente visuelle Vorschau Ihrer App, um Ihren App-Namen, Ihr Symbol und Ihre Beschreibungen zu ergänzen.</span><span class="sxs-lookup"><span data-stu-id="7bc6a-159">Screenshots provide a prominent visual preview of your app to complement your app name, icon, and descriptions.</span></span>

:::row:::

   :::column span="3":::
      :::image type="content" source="~/assets/images/store-detail-page/Screenshot-01.png" alt-text="Beispiel screenshot highlights where app screenshots display in a store listing.":::
   :::column-end:::
   :::column span="1":::
   :::column-end:::

:::row-end:::

<span data-ttu-id="7bc6a-161">Beachten Sie Folgendes zu Screenshots:</span><span class="sxs-lookup"><span data-stu-id="7bc6a-161">Remember the following about screenshots:</span></span>

* <span data-ttu-id="7bc6a-162">Sie können bis zu fünf Screenshots pro Eintrag haben.</span><span class="sxs-lookup"><span data-stu-id="7bc6a-162">You can have up to five screenshots per listing.</span></span>
* <span data-ttu-id="7bc6a-163">Unterstützte Dateitypen sind PNG, JPEG und GIF.</span><span class="sxs-lookup"><span data-stu-id="7bc6a-163">Supported file types include PNG, JPEG, and GIF.</span></span>
* <span data-ttu-id="7bc6a-164">Die Abmessungen sollten 1366 x 768 Pixel betragen.</span><span class="sxs-lookup"><span data-stu-id="7bc6a-164">Dimensions should be 1366x768 pixels.</span></span>
* <span data-ttu-id="7bc6a-165">Maximale Größe von 1.024 KB.</span><span class="sxs-lookup"><span data-stu-id="7bc6a-165">Maximum size of 1,024 KB.</span></span>

<span data-ttu-id="7bc6a-166">Bewährte Methoden finden Sie in den folgenden Ressourcen:</span><span class="sxs-lookup"><span data-stu-id="7bc6a-166">For best practices, see the following resources:</span></span>

* [<span data-ttu-id="7bc6a-167">Teams richtlinien für die Speicherüberprüfung</span><span class="sxs-lookup"><span data-stu-id="7bc6a-167">Teams store validation guidelines</span></span>](~/concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md#44-screenshots)
* [<span data-ttu-id="7bc6a-168">Erstellen effektiver Bilder für Microsoft-App-Stores</span><span class="sxs-lookup"><span data-stu-id="7bc6a-168">Craft effective images for Microsoft app stores</span></span>](/office/dev/store/craft-effective-appsource-store-images)

### <a name="create-a-video"></a><span data-ttu-id="7bc6a-169">Erstellen eines Videos</span><span class="sxs-lookup"><span data-stu-id="7bc6a-169">Create a video</span></span>

<span data-ttu-id="7bc6a-170">Ein Video in Ihrem Eintrag kann die effektivste Möglichkeit sein, um zu kommunizieren, warum Personen Ihre App verwenden sollten.</span><span class="sxs-lookup"><span data-stu-id="7bc6a-170">A video in your listing can be the most effective way to communicate why people should use your app.</span></span> <span data-ttu-id="7bc6a-171">Sie sollten die folgenden Fragen in einem Video beantworten:</span><span class="sxs-lookup"><span data-stu-id="7bc6a-171">You should address the following questions in a video:</span></span>

* <span data-ttu-id="7bc6a-172">Wer ist Ihre App für?</span><span class="sxs-lookup"><span data-stu-id="7bc6a-172">Who is your app for?</span></span>
* <span data-ttu-id="7bc6a-173">Welche Probleme kann Ihre App lösen?</span><span class="sxs-lookup"><span data-stu-id="7bc6a-173">What problems can your app solve?</span></span>
* <span data-ttu-id="7bc6a-174">Wie funktioniert Ihre App?</span><span class="sxs-lookup"><span data-stu-id="7bc6a-174">How does your app work?</span></span>
* <span data-ttu-id="7bc6a-175">Welche weiteren Vorteile bietet ihnen die Verwendung Ihrer App?</span><span class="sxs-lookup"><span data-stu-id="7bc6a-175">What other benefits do you get from using your app?</span></span>

#### <a name="best-practices-for-videos"></a><span data-ttu-id="7bc6a-176">Bewährte Methoden für Videos</span><span class="sxs-lookup"><span data-stu-id="7bc6a-176">Best practices for videos</span></span>

* <span data-ttu-id="7bc6a-177">Halten Sie Ihr Video zwischen 30 und 90 Sekunden.</span><span class="sxs-lookup"><span data-stu-id="7bc6a-177">Keep your video between 30-90 seconds.</span></span>
* <span data-ttu-id="7bc6a-178">Zielen Sie auf Qualität ab.</span><span class="sxs-lookup"><span data-stu-id="7bc6a-178">Aim for quality.</span></span> <span data-ttu-id="7bc6a-179">In einem Eintrag sehen Benutzer Ihr Video vor Screenshots.</span><span class="sxs-lookup"><span data-stu-id="7bc6a-179">In a listing, users will see your video before screenshots.</span></span>

### <a name="select-a-category-for-your-app"></a><span data-ttu-id="7bc6a-180">Auswählen einer Kategorie für Ihre App</span><span class="sxs-lookup"><span data-stu-id="7bc6a-180">Select a category for your app</span></span>

<span data-ttu-id="7bc6a-181">Während der Übermittlung werden Sie aufgefordert, Ihre App zu kategorisieren.</span><span class="sxs-lookup"><span data-stu-id="7bc6a-181">During submission, you're asked to categorize your app.</span></span> <span data-ttu-id="7bc6a-182">In der folgenden Tabelle werden Teams Den kategorien zugeordnet, die im [Partner Center aufgeführt sind.](https://aka.ms/PartnerCenterHomePage)</span><span class="sxs-lookup"><span data-stu-id="7bc6a-182">The following table maps Teams store categories to the categories listed in [Partner Center](https://aka.ms/PartnerCenterHomePage).</span></span>

| <span data-ttu-id="7bc6a-183">Teams Kategorien</span><span class="sxs-lookup"><span data-stu-id="7bc6a-183">Teams categories</span></span>       | <span data-ttu-id="7bc6a-184">Partner Center-Kategorien</span><span class="sxs-lookup"><span data-stu-id="7bc6a-184">Partner Center categories</span></span>  |
|:---------------------|:---------------|
| <span data-ttu-id="7bc6a-185">Analytics und BI</span><span class="sxs-lookup"><span data-stu-id="7bc6a-185">Analytics and BI</span></span> | <span data-ttu-id="7bc6a-186">Analyse, Datenvisualisierung und BI</span><span class="sxs-lookup"><span data-stu-id="7bc6a-186">Analytics, Data Visualization and BI</span></span> |
| <span data-ttu-id="7bc6a-187">Entwickler und IT</span><span class="sxs-lookup"><span data-stu-id="7bc6a-187">Developer and IT</span></span> | <span data-ttu-id="7bc6a-188">Entwicklertools, IT-Administrator</span><span class="sxs-lookup"><span data-stu-id="7bc6a-188">Developer Tools, IT Admin</span></span> |
| <span data-ttu-id="7bc6a-189">Schulung und Weiterbildung</span><span class="sxs-lookup"><span data-stu-id="7bc6a-189">Education</span></span> | <span data-ttu-id="7bc6a-190">Schulung und Weiterbildung</span><span class="sxs-lookup"><span data-stu-id="7bc6a-190">Education</span></span> |
| <span data-ttu-id="7bc6a-191">Personalwesen</span><span class="sxs-lookup"><span data-stu-id="7bc6a-191">Human resources</span></span> | <span data-ttu-id="7bc6a-192">Personalwesen und Personalwerbung</span><span class="sxs-lookup"><span data-stu-id="7bc6a-192">Human Resources and Recruiting</span></span> |
| <span data-ttu-id="7bc6a-193">Produktivität</span><span class="sxs-lookup"><span data-stu-id="7bc6a-193">Productivity</span></span> | <span data-ttu-id="7bc6a-194">Inhaltsverwaltung, Dateien und Dokumente, Produktivität, Schulungen und Lernprogramme und Dienstprogramme</span><span class="sxs-lookup"><span data-stu-id="7bc6a-194">Content Management, Files and documents, Productivity, Training and Tutorials, and Utilities</span></span> |
| <span data-ttu-id="7bc6a-195">Projektmanagement</span><span class="sxs-lookup"><span data-stu-id="7bc6a-195">Project management</span></span> | <span data-ttu-id="7bc6a-196">Kommunikation, Project, Workflow und Unternehmensverwaltung</span><span class="sxs-lookup"><span data-stu-id="7bc6a-196">Communication, Project Management, Workflow, and Business Management</span></span> |
| <span data-ttu-id="7bc6a-197">Vertrieb und Support</span><span class="sxs-lookup"><span data-stu-id="7bc6a-197">Sales and support</span></span> | <span data-ttu-id="7bc6a-198">Kunden- und Kontaktverwaltung, Kundensupport, Finanzverwaltung, Vertrieb und Marketing</span><span class="sxs-lookup"><span data-stu-id="7bc6a-198">Customer and Contact Management, Customer Support, Financial Management, Sales and Marketing</span></span> |
| <span data-ttu-id="7bc6a-199">Soziales und Spaß</span><span class="sxs-lookup"><span data-stu-id="7bc6a-199">Social and fun</span></span> | <span data-ttu-id="7bc6a-200">Bilder- und Videogalerien, Lifestyle, Nachrichten und Wetter, Soziales, Reisen und Navigation</span><span class="sxs-lookup"><span data-stu-id="7bc6a-200">Image and Video Galleries, Lifestyle, News and Weather, Social, Travel, and Navigation</span></span> |

### <a name="localize-your-store-listing"></a><span data-ttu-id="7bc6a-201">Lokalisieren Des Store-Eintrags</span><span class="sxs-lookup"><span data-stu-id="7bc6a-201">Localize your store listing</span></span>

<span data-ttu-id="7bc6a-202">Partner Center unterstützt [lokalisierte Store-Einträge](https://docs.microsoft.com/office/dev/store/prepare-localized-solutions).</span><span class="sxs-lookup"><span data-stu-id="7bc6a-202">Partner Center supports [localized store listings](https://docs.microsoft.com/office/dev/store/prepare-localized-solutions).</span></span> <span data-ttu-id="7bc6a-203">Weitere Informationen finden Sie unter [Localize your Teams app listing](../../../../concepts/build-and-test/apps-localization.md).</span><span class="sxs-lookup"><span data-stu-id="7bc6a-203">For more information, see [how to localize your Teams app listing](../../../../concepts/build-and-test/apps-localization.md).</span></span>

## <a name="complete-publisher-verification"></a><span data-ttu-id="7bc6a-204">Abschließen Publisher Überprüfung</span><span class="sxs-lookup"><span data-stu-id="7bc6a-204">Complete Publisher Verification</span></span>

<span data-ttu-id="7bc6a-205">[Publisher überprüfung](/azure/active-directory/develop/publisher-verification-overview) ist für Teams im Store aufgeführten Apps erforderlich. Weitere Informationen finden Sie unter [häufig gestellte Fragen](/azure/active-directory/develop/publisher-verification-overview#frequently-asked-questions), wie Sie Ihre [App](/azure/active-directory/develop/mark-app-as-publisher-verified)als herausgeberverifiziert markieren und die Herausgeberüberprüfung [beheben.](/azure/active-directory/develop/troubleshoot-publisher-verification)</span><span class="sxs-lookup"><span data-stu-id="7bc6a-205">[Publisher Verification](/azure/active-directory/develop/publisher-verification-overview) is required for Teams apps listed in the store.For more information, see [frequently asked questions](/azure/active-directory/develop/publisher-verification-overview#frequently-asked-questions), [how to mark your app as publisher verified](/azure/active-directory/develop/mark-app-as-publisher-verified), and [troubleshoot publisher verification](/azure/active-directory/develop/troubleshoot-publisher-verification).</span></span>

## <a name="complete-publisher-attestation"></a><span data-ttu-id="7bc6a-206">Complete Publisher Attestation</span><span class="sxs-lookup"><span data-stu-id="7bc6a-206">Complete Publisher Attestation</span></span>

<span data-ttu-id="7bc6a-207">[Publisher Bescheinigung](/microsoft-365-app-certification/docs/attestation) ist auch für Teams im Store aufgeführten Apps erforderlich.</span><span class="sxs-lookup"><span data-stu-id="7bc6a-207">[Publisher Attestation](/microsoft-365-app-certification/docs/attestation) is also required for Teams apps listed in the store.</span></span> <span data-ttu-id="7bc6a-208">Der Prozess umfasst das Abschließen einer Selbstbewertung der Sicherheits-, Datenverarbeitungs- und Compliancepraktiken Ihrer App, die potenziellen Kunden dabei helfen können, fundierte Entscheidungen über die Verwendung Ihrer App zu treffen.</span><span class="sxs-lookup"><span data-stu-id="7bc6a-208">The process includes completing a self-assessment of your app's security, data handling, and compliance practices that can help potential customers make informed decisions about using your app.</span></span>

> [!NOTE]
> <span data-ttu-id="7bc6a-209">Wenn Sie eine neue App übermitteln, können Sie die Publisher-Bestätigung erst dann offiziell abschließen, wenn Ihre App im Teams ist.</span><span class="sxs-lookup"><span data-stu-id="7bc6a-209">If you're submitting a new app, you can't officially complete Publisher Attestation until your app is listed on the Teams store.</span></span> <span data-ttu-id="7bc6a-210">Wenn Sie eine aufgelistete App aktualisieren, füllen Sie Publisher Aus, bevor Sie die neueste Version der App zur Überprüfung übermitteln.</span><span class="sxs-lookup"><span data-stu-id="7bc6a-210">If you're updating a listed app, complete Publisher Attestation before you submit the latest version of the app for validation.</span></span>

## <a name="next-step"></a><span data-ttu-id="7bc6a-211">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="7bc6a-211">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7bc6a-212">Übermitteln Ihrer App</span><span class="sxs-lookup"><span data-stu-id="7bc6a-212">Submit your app</span></span>](https://docs.microsoft.com/office/dev/store/add-in-submission-guide)
