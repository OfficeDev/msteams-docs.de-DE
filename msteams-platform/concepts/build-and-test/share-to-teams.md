---
title: Schaltfläche "Share-to-Teams erstellen"
description: Hinzufügen der eingebetteten Schaltfläche "Zu Teams freigeben" auf Ihrer Website
ms.topic: reference
localization_priority: Normal
keywords: Freigeben von Teams-Share-to-Teams
ms.openlocfilehash: c8bbb371e2d68bf063c3aa5e02c7cf3ec911c0b8
ms.sourcegitcommit: a732789190f59ec1f3699e8ad2f06387e8fe1458
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2021
ms.locfileid: "52058474"
---
# <a name="create-share-to-teams-button"></a><span data-ttu-id="3befc-104">Schaltfläche "Share-to-Teams erstellen"</span><span class="sxs-lookup"><span data-stu-id="3befc-104">Create Share-to-Teams button</span></span>

<span data-ttu-id="3befc-105">Websites von Drittanbietern können das Startstartskript verwenden, um Share-to-Teams-Schaltflächen auf ihren Webseiten einzubetten.</span><span class="sxs-lookup"><span data-stu-id="3befc-105">Third-party websites can use the launcher script to embed Share-to-Teams buttons on their webpages.</span></span> <span data-ttu-id="3befc-106">Wenn Sie diese Option auswählen, wird die Share-to-Teams-Erfahrung in einem Popupfenster gestartet.</span><span class="sxs-lookup"><span data-stu-id="3befc-106">When you select, it launches the Share-to-Teams experience in a pop-up window.</span></span> <span data-ttu-id="3befc-107">Auf diese Weise können Sie einen Link direkt mit jeder Person oder einem Microsoft Teams-Kanal teilen, ohne den Kontext zu wechseln.</span><span class="sxs-lookup"><span data-stu-id="3befc-107">This allows you to share a link directly to any person or Microsoft Teams channel without switching the context.</span></span> <span data-ttu-id="3befc-108">In diesem Dokument erfahren Sie, wie Sie eine Share-to-Teams-Schaltfläche für Ihre Website erstellen und einbetten, ihre Websitevorschau erstellen und Share-to-Teams for Education erweitern.</span><span class="sxs-lookup"><span data-stu-id="3befc-108">This document guides you on how to create, and embed a Share-to-Teams button for your website, craft your website preview, and extend Share-to-Teams for Education.</span></span>

> [!NOTE]
> * <span data-ttu-id="3befc-109">Nur die Desktopversionen von Edge und Chrome werden unterstützt.</span><span class="sxs-lookup"><span data-stu-id="3befc-109">Only the desktop versions of Edge and Chrome are supported.</span></span>
> * <span data-ttu-id="3befc-110">Die Verwendung von Freemium- oder Gastkonten wird nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="3befc-110">Use of Freemium or guest accounts is not supported.</span></span>  

<span data-ttu-id="3befc-111">In der folgenden Abbildung wird die Popuperfahrung "Share-to-Teams" angezeigt:</span><span class="sxs-lookup"><span data-stu-id="3befc-111">The following image displays the Share-to-Teams pop-up experience:</span></span>

![Share-to-Teams-Popup](~/assets/images/share-to-teams-popup.png)

## <a name="embed-a-share-to-teams-button"></a><span data-ttu-id="3befc-113">Einbetten einer Schaltfläche Für Teams freigeben</span><span class="sxs-lookup"><span data-stu-id="3befc-113">Embed a Share to Teams button</span></span>

1. <span data-ttu-id="3befc-114">Fügen Sie `launcher.js` das Skript auf Ihrer Webseite hinzu.</span><span class="sxs-lookup"><span data-stu-id="3befc-114">Add the `launcher.js` script on your webpage.</span></span>

    ```html
    <script async defer src="https://teams.microsoft.com/share/launcher.js"></script>
    ```

1. <span data-ttu-id="3befc-115">Fügen Sie ein HTML-Element auf Ihrer Webseite mit dem Klassenattribut und dem Link hinzu, `teams-share-button` der im Attribut gemeinsam verwendet werden `data-href` soll.</span><span class="sxs-lookup"><span data-stu-id="3befc-115">Add a HTML element on your webpage with the `teams-share-button` class attribute and the link to share in the `data-href` attribute.</span></span>

    ```html
    <div
      class="teams-share-button"
      data-href="https://<link-to-be-shared>">
    </div>
    ```

    <span data-ttu-id="3befc-116">Nachdem Sie dies abgeschlossen haben, wird das Microsoft Teams-Symbol zu Ihrer Website hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="3befc-116">After completing this, the Microsoft Teams icon gets added to your website.</span></span> <span data-ttu-id="3befc-117">Die folgende Abbildung zeigt das Share-to-Teams-Symbol:</span><span class="sxs-lookup"><span data-stu-id="3befc-117">The following image shows Share-to-Teams icon:</span></span>

    ![Symbol "Für Teams freigeben"](~/assets/icons/share-to-teams-icon.png)

1. <span data-ttu-id="3befc-119">Wenn Sie eine andere Symbolgröße für die Schaltfläche Für Teams freigeben möchten, verwenden Sie alternativ das `data-icon-px-size` Attribut.</span><span class="sxs-lookup"><span data-stu-id="3befc-119">Alternatively, if you want a different icon size for the Share-to Teams button, use the `data-icon-px-size` attribute.</span></span>

    ```html
    <div
      class="teams-share-button"
      data-href="https://<link-to-be-shared>"
      data-icon-px-size="64">
    </div>
    ```
1. <span data-ttu-id="3befc-120">Wenn für den freigegebenen Link die Benutzerauthentifizierung erforderlich ist und die URL-Vorschau ihres links, der freigegeben werden soll, in Teams nicht gut gerendert wird, können Sie die URL-Vorschau deaktivieren, indem Sie das Attribut hinzufügen, das auf `data-preview` festgelegt `false` ist.</span><span class="sxs-lookup"><span data-stu-id="3befc-120">If the shared link requires user authentication, and the URL preview from your link to be shared does not render well in Teams then, you can disable the URL preview by adding the `data-preview` attribute set to `false`.</span></span>

    ```html
    <div
      class="teams-share-button"
      data-href="https://<link-to-be-shared>"
      data-preview="false">
    </div>
    ```

1. <span data-ttu-id="3befc-121">Wenn Ihre Seite Inhalte dynamisch rendert, können Sie mit der -Methode erzwingen, dass die Schaltfläche Freigeben an der entsprechenden Stelle `shareToMicrosoftTeams.renderButtons()` in der Pipeline gerendert wird. </span><span class="sxs-lookup"><span data-stu-id="3befc-121">If your page dynamically renders content, you can use the the `shareToMicrosoftTeams.renderButtons()` method to force the **Share** button to render at the appropriate place in the pipeline.</span></span>

## <a name="craft-your-website-preview"></a><span data-ttu-id="3befc-122">Erstellen der Websitevorschau</span><span class="sxs-lookup"><span data-stu-id="3befc-122">Craft your website preview</span></span>

<span data-ttu-id="3befc-123">Wenn Ihre Website für Teams freigegeben wird, enthält die Karte, die in den ausgewählten Kanal eingefügt wird, eine Vorschau Ihrer Website.</span><span class="sxs-lookup"><span data-stu-id="3befc-123">When your website is shared to Teams, the card that is inserted into the selected channel contains a preview of your website.</span></span> <span data-ttu-id="3befc-124">Sie können das Verhalten dieser Vorschau steuern, indem Sie sicherstellen, dass der freigegebenen Website die entsprechenden Metadaten hinzugefügt werden, z. B. die `data-href` URL.</span><span class="sxs-lookup"><span data-stu-id="3befc-124">You can control the behavior of this preview by ensuring the appropriate meta-data is added to the website being shared, such as the `data-href` URL.</span></span>  

<span data-ttu-id="3befc-125">**So zeigen Sie die Vorschau an**</span><span class="sxs-lookup"><span data-stu-id="3befc-125">**To display the preview**</span></span>

* <span data-ttu-id="3befc-126">Sie müssen entweder ein **Miniaturansichtsbild** oder einen **Titel und** eine **Beschreibung enthalten.**</span><span class="sxs-lookup"><span data-stu-id="3befc-126">You must include either a **Thumbnail image**, or both a **Title** and **Description**.</span></span> <span data-ttu-id="3befc-127">Um die besten Ergebnisse zu erzielen, schließen Sie alle drei ein.</span><span class="sxs-lookup"><span data-stu-id="3befc-127">For best results, include all three.</span></span>
* <span data-ttu-id="3befc-128">Die freigegebene URL erfordert keine Authentifizierung.</span><span class="sxs-lookup"><span data-stu-id="3befc-128">The shared URL does not require authentication.</span></span> <span data-ttu-id="3befc-129">Wenn die Authentifizierung erforderlich ist, können Sie sie freigeben, aber die Vorschau wird nicht erstellt.</span><span class="sxs-lookup"><span data-stu-id="3befc-129">If it requires authentication, you can share it, but the preview is not created.</span></span>

<span data-ttu-id="3befc-130">In der folgenden Tabelle sind die erforderlichen Tags aufgeführt:</span><span class="sxs-lookup"><span data-stu-id="3befc-130">The following table outlines the necessary tags:</span></span>

|<span data-ttu-id="3befc-131">Wert</span><span class="sxs-lookup"><span data-stu-id="3befc-131">Value</span></span>|<span data-ttu-id="3befc-132">Metatag</span><span class="sxs-lookup"><span data-stu-id="3befc-132">Meta tag</span></span>| <span data-ttu-id="3befc-133">Öffnen von Graph</span><span class="sxs-lookup"><span data-stu-id="3befc-133">Open Graph</span></span>|
|----|----|----|
|<span data-ttu-id="3befc-134">Titel</span><span class="sxs-lookup"><span data-stu-id="3befc-134">Title</span></span>|`<meta name="title" content="Example Page Title">`|`<meta property="og:title" content="Example Page Title">`|
|<span data-ttu-id="3befc-135">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="3befc-135">Description</span></span>|`<meta name="description" content="Example Page Description">`|`<meta property="og:description" content="Example Page Description">`|
|<span data-ttu-id="3befc-136">Miniaturansicht</span><span class="sxs-lookup"><span data-stu-id="3befc-136">Thumbnail Image</span></span>| <span data-ttu-id="3befc-137">none.</span><span class="sxs-lookup"><span data-stu-id="3befc-137">none.</span></span> |`<meta property="og:image" content="http://example.com/image.jpg">`|

<span data-ttu-id="3befc-138">Sie können entweder die Html-Standardversionen oder die Open Graph-Version verwenden.</span><span class="sxs-lookup"><span data-stu-id="3befc-138">You can use either the html default versions, or the Open Graph version.</span></span>

## <a name="share-to-teams-for-education"></a><span data-ttu-id="3befc-139">Freigeben für Teams for Education</span><span class="sxs-lookup"><span data-stu-id="3befc-139">Share to Teams for Education</span></span>

<span data-ttu-id="3befc-140">Für Lehrkräfte, die die Schaltfläche Für Teams freigeben verwenden, gibt es eine zusätzliche Option zu `Create an Assignment` .</span><span class="sxs-lookup"><span data-stu-id="3befc-140">For teachers using the Share to Teams button, there is an additional option to `Create an Assignment`.</span></span> <span data-ttu-id="3befc-141">Auf diese Weise können Sie schnell eine Zuordnung im ausgewählten Team basierend auf dem freigegebenen Link erstellen.</span><span class="sxs-lookup"><span data-stu-id="3befc-141">This enables you to quickly create an assignment in the chosen Team, based on the shared link.</span></span> <span data-ttu-id="3befc-142">Die folgende Abbildung zeigt Share-to-Teams für Bildungseinrichtungen:</span><span class="sxs-lookup"><span data-stu-id="3befc-142">The following image displays Share-to-Teams for education:</span></span> 

![Freigeben für Teams-Popup-Bildungseinrichtungen](~/assets/images/share-to-teams-popup-edu.png)

## <a name="full-launcherjs-definition"></a><span data-ttu-id="3befc-144">Vollständige launcher.js Definition</span><span class="sxs-lookup"><span data-stu-id="3befc-144">Full launcher.js definition</span></span>

| <span data-ttu-id="3befc-145">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="3befc-145">Property</span></span> | <span data-ttu-id="3befc-146">HTML-Attribut</span><span class="sxs-lookup"><span data-stu-id="3befc-146">HTML attribute</span></span> | <span data-ttu-id="3befc-147">Typ</span><span class="sxs-lookup"><span data-stu-id="3befc-147">Type</span></span> | <span data-ttu-id="3befc-148">Standard</span><span class="sxs-lookup"><span data-stu-id="3befc-148">Default</span></span> | <span data-ttu-id="3befc-149">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="3befc-149">Description</span></span> |
| -------------- | ---------------------- | --------------------- | ------- | ---------------------------------------------------------------------- |
| <span data-ttu-id="3befc-150">href</span><span class="sxs-lookup"><span data-stu-id="3befc-150">href</span></span> | `data-href` | <span data-ttu-id="3befc-151">string</span><span class="sxs-lookup"><span data-stu-id="3befc-151">string</span></span> | <span data-ttu-id="3befc-152">n/v</span><span class="sxs-lookup"><span data-stu-id="3befc-152">n/a</span></span> | <span data-ttu-id="3befc-153">Der Href des inhalts, der gemeinsam verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="3befc-153">The href of the content to share.</span></span> |
| <span data-ttu-id="3befc-154">Vorschau</span><span class="sxs-lookup"><span data-stu-id="3befc-154">preview</span></span> | `data-preview` | <span data-ttu-id="3befc-155">boolean (als Zeichenfolge)</span><span class="sxs-lookup"><span data-stu-id="3befc-155">boolean (as a string)</span></span> | `true` | <span data-ttu-id="3befc-156">Gibt an, ob eine Vorschau des zu teilende Inhalts angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="3befc-156">Whether or not to show a preview of the content to share.</span></span> |
| <span data-ttu-id="3befc-157">iconPxSize</span><span class="sxs-lookup"><span data-stu-id="3befc-157">iconPxSize</span></span> | `data-icon-px-size` | <span data-ttu-id="3befc-158">Zahl (als Zeichenfolge)</span><span class="sxs-lookup"><span data-stu-id="3befc-158">number (as a string)</span></span> | `32` | <span data-ttu-id="3befc-159">Die Größe der zu rendernde Schaltfläche "Share-to-Teams" in Pixeln.</span><span class="sxs-lookup"><span data-stu-id="3befc-159">The size in pixels of the Share-to-Teams button to render.</span></span> |
| <span data-ttu-id="3befc-160">msgText</span><span class="sxs-lookup"><span data-stu-id="3befc-160">msgText</span></span> | `data-msg-text` | <span data-ttu-id="3befc-161">string</span><span class="sxs-lookup"><span data-stu-id="3befc-161">string</span></span> | <span data-ttu-id="3befc-162">n/v</span><span class="sxs-lookup"><span data-stu-id="3befc-162">n/a</span></span> | <span data-ttu-id="3befc-163">Standardtext, der vor dem Link im Feld Zum Verfassen von Nachrichten eingefügt werden soll.</span><span class="sxs-lookup"><span data-stu-id="3befc-163">Default Text to be inserted before the link in the message compose box.</span></span> <span data-ttu-id="3befc-164">Die maximale Anzahl von Zeichen beträgt 200.</span><span class="sxs-lookup"><span data-stu-id="3befc-164">Maximum number of characters is 200.</span></span> |
| <span data-ttu-id="3befc-165">assignInstr</span><span class="sxs-lookup"><span data-stu-id="3befc-165">assignInstr</span></span> | `data-assign-instr` | <span data-ttu-id="3befc-166">string</span><span class="sxs-lookup"><span data-stu-id="3befc-166">string</span></span> | <span data-ttu-id="3befc-167">n/v</span><span class="sxs-lookup"><span data-stu-id="3befc-167">n/a</span></span> | <span data-ttu-id="3befc-168">Standardtext, der in das Feld "Anweisungen" eingefügt werden soll.</span><span class="sxs-lookup"><span data-stu-id="3befc-168">Default Text to be inserted in the assignments "Instructions" field.</span></span> <span data-ttu-id="3befc-169">Die maximale Anzahl von Zeichen beträgt 200.</span><span class="sxs-lookup"><span data-stu-id="3befc-169">Maximum number of characters is 200.</span></span> |
| <span data-ttu-id="3befc-170">assignTitle</span><span class="sxs-lookup"><span data-stu-id="3befc-170">assignTitle</span></span> | `data-assign-title` | <span data-ttu-id="3befc-171">string</span><span class="sxs-lookup"><span data-stu-id="3befc-171">string</span></span> | <span data-ttu-id="3befc-172">n/v</span><span class="sxs-lookup"><span data-stu-id="3befc-172">n/a</span></span> | <span data-ttu-id="3befc-173">Standardtext, der in das Feld Zuordnungen "Titel" eingefügt werden soll.</span><span class="sxs-lookup"><span data-stu-id="3befc-173">Default Text to be inserted in the assignments "Title" field.</span></span> <span data-ttu-id="3befc-174">Die maximale Anzahl von Zeichen ist 50.</span><span class="sxs-lookup"><span data-stu-id="3befc-174">Maximum number of characters is 50.</span></span> |

### <a name="methods"></a><span data-ttu-id="3befc-175">Methoden</span><span class="sxs-lookup"><span data-stu-id="3befc-175">Methods</span></span>

**`shareToMicrosoftTeams.renderButtons(options)`**

<span data-ttu-id="3befc-176">`options` (optional): `{ elements?: HTMLElement[] }`</span><span class="sxs-lookup"><span data-stu-id="3befc-176">`options` (optional): `{ elements?: HTMLElement[] }`</span></span>

<span data-ttu-id="3befc-177">Derzeit werden alle Freigabeschaltflächen auf der Seite gerendert.</span><span class="sxs-lookup"><span data-stu-id="3befc-177">Currently, all share buttons are rendered on the page.</span></span> <span data-ttu-id="3befc-178">Wenn ein optionales Objekt mit einer Liste von Elementen bereitgestellt wird, werden diese Elemente `options` in Freigabeschaltflächen gerendert.</span><span class="sxs-lookup"><span data-stu-id="3befc-178">If an optional `options` object is supplied with a list of elements, those elements are rendered into share buttons.</span></span>

### <a name="set-default-form-values"></a><span data-ttu-id="3befc-179">Festlegen von Standardformularwerten</span><span class="sxs-lookup"><span data-stu-id="3befc-179">Set default form values</span></span>

<span data-ttu-id="3befc-180">Sie können die Standardwerte für die folgenden Felder im Formular Für Teams freigeben festlegen:</span><span class="sxs-lookup"><span data-stu-id="3befc-180">You can select to set default values for the following fields on the Share to Teams form:</span></span>

* <span data-ttu-id="3befc-181">Sagen Sie dazu etwas: `msgText`</span><span class="sxs-lookup"><span data-stu-id="3befc-181">Say something about this: `msgText`</span></span>
* <span data-ttu-id="3befc-182">Zuweisungsanweisungen: `assignInstr`</span><span class="sxs-lookup"><span data-stu-id="3befc-182">Assignment Instructions: `assignInstr`</span></span>
* <span data-ttu-id="3befc-183">Zuordnungstitel: `assignTitle`</span><span class="sxs-lookup"><span data-stu-id="3befc-183">Assignment Title: `assignTitle`</span></span>

#### <a name="example"></a><span data-ttu-id="3befc-184">Beispiel</span><span class="sxs-lookup"><span data-stu-id="3befc-184">Example</span></span>

 <span data-ttu-id="3befc-185">Standardformularwerte werden im folgenden Beispiel angegeben:</span><span class="sxs-lookup"><span data-stu-id="3befc-185">Default form values are given in the following example:</span></span>

```html
<span
    class="teams-share-button"
    data-href="https://www.microsoft.com/education/products/teams"
    data-msg-text="Default Message"
    data-assign-title="Default Assignment Title"
    data-assign-instr="Default Assignment Instructions"
></span>
```

## <a name="see-also"></a><span data-ttu-id="3befc-186">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="3befc-186">See also</span></span>

- [<span data-ttu-id="3befc-187">Integrieren von Web-Apps</span><span class="sxs-lookup"><span data-stu-id="3befc-187">Integrate web apps</span></span>](~/samples/integrate-web-apps-overview.md)
