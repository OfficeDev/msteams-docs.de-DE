---
title: Erstellen einer Schaltfläche zum Teilen in Microsoft Teams
description: So fügen Sie die eingebettete Schaltfläche "Zu Teams freigeben" auf Ihrer Website hinzu
ms.topic: reference
keywords: Share Teams Share-to-Teams
ms.openlocfilehash: 46091c957137cc871095ca6a57c0d61fa79d9458
ms.sourcegitcommit: 976e870cc925f61b76c3830ec04ba6e4bdfde32f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/27/2021
ms.locfileid: "50014334"
---
# <a name="create-a-share-to-teams-button-for-your-website"></a><span data-ttu-id="a9154-104">Erstellen einer Schaltfläche zum Teilen in Teams für Ihre Website</span><span class="sxs-lookup"><span data-stu-id="a9154-104">Create a Share-to-Teams button for your website</span></span>

>[!NOTE]
> * <span data-ttu-id="a9154-105">Nur die Desktopversionen von Edge und Chrome werden unterstützt.</span><span class="sxs-lookup"><span data-stu-id="a9154-105">Only the desktop versions of Edge and Chrome are supported.</span></span>
> * <span data-ttu-id="a9154-106">Die Verwendung von Freemium- oder Gastkonten wird nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="a9154-106">Use of Freemium or guest accounts is not supported.</span></span>

<span data-ttu-id="a9154-107">Drittanbieterwebsites können das Startskript verwenden, um Schaltflächen "In Teams freigeben" auf ihren Webseiten einzubetten, wodurch die Freigabe für Teams in einem Popupfenster gestartet wird, wenn darauf geklickt wird.</span><span class="sxs-lookup"><span data-stu-id="a9154-107">Third-party websites can use the launcher script to embed Share to Teams buttons on their webpages which will launch the Share to Teams experience in a popup window when clicked.</span></span> <span data-ttu-id="a9154-108">Dadurch können Sie einen Link direkt für eine beliebige Person oder einen Microsoft Teams-Kanal freigeben, ohne den Kontext zu wechseln.</span><span class="sxs-lookup"><span data-stu-id="a9154-108">This will allow you to share a link directly to any person or Microsoft Teams channel without switching context.</span></span>

![Popup "Für Teams freigeben"](~/assets/images/share-to-teams-popup.png)

## <a name="how-to-embed-a-share-to-teams-button"></a><span data-ttu-id="a9154-110">So betten Sie eine Schaltfläche "In Teams freigeben" ein</span><span class="sxs-lookup"><span data-stu-id="a9154-110">How to embed a Share to Teams button</span></span>

<span data-ttu-id="a9154-111">Zunächst müssen Sie das Skript auf Ihrer `launcher.js` Webseite hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="a9154-111">First, you'll need to add the `launcher.js` script on your webpage.</span></span>

```html
<script async defer src="https://teams.microsoft.com/share/launcher.js"></script>
```

<span data-ttu-id="a9154-112">Fügen Sie als Nächstes ein HTML-Element auf Ihrer Webseite mit dem Klassenattribut und dem Link zum Freigeben `teams-share-button` im Attribut `data-href` hinzu.</span><span class="sxs-lookup"><span data-stu-id="a9154-112">Next, add an HTML element on your webpage with the `teams-share-button` class attribute and the link to share in the `data-href` attribute.</span></span>

```html
<div
  class="teams-share-button"
  data-href="https://<link-to-be-shared>">
</div>
```

<span data-ttu-id="a9154-113">Dadurch wird das Microsoft Teams-Symbol zu Ihrer Website hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="a9154-113">This will add the Microsoft Teams icon to your website.</span></span>

![Symbol "Für Teams freigeben"](~/assets/icons/share-to-teams-icon.png)

<span data-ttu-id="a9154-115">Wenn Sie für die Schaltfläche "In Teams freigeben" eine andere Symbolgröße wünschen, verwenden Sie optional das `data-icon-px-size` Attribut.</span><span class="sxs-lookup"><span data-stu-id="a9154-115">Optionally, if you want a different icon size for the Share to Teams button, use the `data-icon-px-size` attribute.</span></span>

```html
<div
  class="teams-share-button"
  data-href="https://<link-to-be-shared>"
  data-icon-px-size="64">
</div>
```

<span data-ttu-id="a9154-116">Wenn Sie wissen, dass die URL-Vorschau von Ihrem Link, der freigegeben werden soll, in Teams nicht gut gerendert wird (z. B. wäre für den Link eine Benutzerauthentifizierung erforderlich), können Sie die URL-Vorschau deaktivieren, indem Sie das Attribut hinzufügen, das auf festgelegt `data-preview` `false` ist.</span><span class="sxs-lookup"><span data-stu-id="a9154-116">If you know that the URL preview from your link to be shared won't render well in Teams (for example the link would require user authentication) you can disable the URL preview by adding the `data-preview` attribute set to `false`.</span></span>

```html
<div
  class="teams-share-button"
  data-href="https://<link-to-be-shared>"
  data-preview="false">
</div>
```

<span data-ttu-id="a9154-117">Wenn Ihre Seite Inhalte dynamisch rendert, können Sie die Methode verwenden, um zu erzwingen, dass die Schaltfläche "Freigeben" an der entsprechenden Stelle `shareToMicrosoftTeams.renderButtons()` in der Pipeline gerendert wird. </span><span class="sxs-lookup"><span data-stu-id="a9154-117">If your page dynamically renders content, you can use the the `shareToMicrosoftTeams.renderButtons()` method to force the **Share** button to render at the appropriate place in the pipeline.</span></span>

## <a name="crafting-your-website-preview"></a><span data-ttu-id="a9154-118">Erstellen der Websitevorschau</span><span class="sxs-lookup"><span data-stu-id="a9154-118">Crafting your website preview</span></span>

<span data-ttu-id="a9154-119">Wenn Ihre Website für Teams freigegeben ist, enthält die Karte, die in den ausgewählten Kanal eingefügt wird, eine Vorschau Ihrer Website.</span><span class="sxs-lookup"><span data-stu-id="a9154-119">When your website is shared to Teams, the card that is inserted into the selected channel will contain a preview of your website.</span></span> <span data-ttu-id="a9154-120">Sie können das Verhalten dieser Vorschau steuern, indem Sie sicherstellen, dass der freigegebenen Website (der URL) die entsprechenden `data-href` Metadaten hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="a9154-120">You can control the behavior of this preview by ensuring the appropriate meta-data is added to the website being shared (the `data-href` URL).</span></span> <span data-ttu-id="a9154-121">In der folgenden Tabelle sind die erforderlichen Tags aufgeführt.</span><span class="sxs-lookup"><span data-stu-id="a9154-121">The table below outlines the necessary tags.</span></span> <span data-ttu-id="a9154-122">Sie können entweder die Html-Standardversionen oder die Open Graph-Version verwenden.</span><span class="sxs-lookup"><span data-stu-id="a9154-122">You can use either the html default versions, or the Open Graph version.</span></span>

<span data-ttu-id="a9154-123">Damit die Vorschau angezeigt wird, müssen Sie:</span><span class="sxs-lookup"><span data-stu-id="a9154-123">In order for the preview to be displayed you must:</span></span>

* <span data-ttu-id="a9154-124">Schließen Sie entweder ein Miniaturbild oder einen Titel und eine Beschreibung ein (um optimale Ergebnisse zu erzielen, schließen Sie alle drei ein).</span><span class="sxs-lookup"><span data-stu-id="a9154-124">Include either a Thumbnail image, or both a Title and Description (for best results, include all three).</span></span>
* <span data-ttu-id="a9154-125">Die freigegebene URL kann keine Authentifizierung erfordern.</span><span class="sxs-lookup"><span data-stu-id="a9154-125">The URL being shared cannot require authentication.</span></span> <span data-ttu-id="a9154-126">Wenn dies möglich ist, können Sie sie weiterhin freigeben, aber die Vorschau wird nicht erstellt.</span><span class="sxs-lookup"><span data-stu-id="a9154-126">If it does you can still share it, but the preview will not be created.</span></span>

|<span data-ttu-id="a9154-127">Wert</span><span class="sxs-lookup"><span data-stu-id="a9154-127">Value</span></span>|<span data-ttu-id="a9154-128">Metatag</span><span class="sxs-lookup"><span data-stu-id="a9154-128">Meta tag</span></span>| <span data-ttu-id="a9154-129">Open Graph</span><span class="sxs-lookup"><span data-stu-id="a9154-129">Open Graph</span></span>|
|----|----|----|
|<span data-ttu-id="a9154-130">Titel</span><span class="sxs-lookup"><span data-stu-id="a9154-130">Title</span></span>|`<meta name="title" content="Example Page Title">`|`<meta property="og:title" content="Example Page Title">`|
|<span data-ttu-id="a9154-131">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="a9154-131">Description</span></span>|`<meta name="description" content="Example Page Description">`|`<meta property="og:description" content="Example Page Description">`|
|<span data-ttu-id="a9154-132">Miniaturansicht</span><span class="sxs-lookup"><span data-stu-id="a9154-132">Thumbnail Image</span></span>| <span data-ttu-id="a9154-133">n/v</span><span class="sxs-lookup"><span data-stu-id="a9154-133">none</span></span> |`<meta property="og:image" content="http://example.com/image.jpg">`|

## <a name="share-to-teams-for-education"></a><span data-ttu-id="a9154-134">Freigeben für Teams für Bildungseinrichtungen</span><span class="sxs-lookup"><span data-stu-id="a9154-134">Share to Teams for Education</span></span>

<span data-ttu-id="a9154-135">Für Lehrer, die die Schaltfläche "In Teams freigeben" verwenden, erhalten Sie eine zusätzliche Option für `Create an Assignment` .</span><span class="sxs-lookup"><span data-stu-id="a9154-135">For teachers using the Share to Teams button you'll be given an additional option to `Create an Assignment`.</span></span> <span data-ttu-id="a9154-136">Auf diese Weise können Sie schnell eine Zuweisung im ausgewählten Team basierend auf dem freigegebenen Link erstellen.</span><span class="sxs-lookup"><span data-stu-id="a9154-136">This enables you to quickly create an assignment in the chosen Team based on the shared link.</span></span>

![Popup "In Teams freigeben"](~/assets/images/share-to-teams-popup-edu.png)

## <a name="full-launcherjs-definition"></a><span data-ttu-id="a9154-138">Vollständige launcher.js Definition</span><span class="sxs-lookup"><span data-stu-id="a9154-138">Full launcher.js definition</span></span>

| <span data-ttu-id="a9154-139">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="a9154-139">Property</span></span> | <span data-ttu-id="a9154-140">HTML-Attribut</span><span class="sxs-lookup"><span data-stu-id="a9154-140">HTML attribute</span></span> | <span data-ttu-id="a9154-141">Typ</span><span class="sxs-lookup"><span data-stu-id="a9154-141">Type</span></span> | <span data-ttu-id="a9154-142">Standard</span><span class="sxs-lookup"><span data-stu-id="a9154-142">Default</span></span> | <span data-ttu-id="a9154-143">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="a9154-143">Description</span></span> |
| -------------- | ---------------------- | --------------------- | ------- | ---------------------------------------------------------------------- |
| <span data-ttu-id="a9154-144">href</span><span class="sxs-lookup"><span data-stu-id="a9154-144">href</span></span> | `data-href` | <span data-ttu-id="a9154-145">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="a9154-145">string</span></span> | <span data-ttu-id="a9154-146">n/v</span><span class="sxs-lookup"><span data-stu-id="a9154-146">n/a</span></span> | <span data-ttu-id="a9154-147">Der Href des zu teilende Inhalts.</span><span class="sxs-lookup"><span data-stu-id="a9154-147">The href of the content to share.</span></span> |
| <span data-ttu-id="a9154-148">Vorschau</span><span class="sxs-lookup"><span data-stu-id="a9154-148">preview</span></span> | `data-preview` | <span data-ttu-id="a9154-149">boolean (als Zeichenfolge)</span><span class="sxs-lookup"><span data-stu-id="a9154-149">boolean (as a string)</span></span> | `true` | <span data-ttu-id="a9154-150">Gibt an, ob eine Vorschau des zu teilende Inhalts angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="a9154-150">Whether or not to show a preview of the content to share.</span></span> |
| <span data-ttu-id="a9154-151">iconPxSize</span><span class="sxs-lookup"><span data-stu-id="a9154-151">iconPxSize</span></span> | `data-icon-px-size` | <span data-ttu-id="a9154-152">Zahl (als Zeichenfolge)</span><span class="sxs-lookup"><span data-stu-id="a9154-152">number (as a string)</span></span> | `32` | <span data-ttu-id="a9154-153">Die Größe der zu rendernde Schaltfläche "Share-to-Teams" in Pixeln.</span><span class="sxs-lookup"><span data-stu-id="a9154-153">The size in pixels of the Share-to-Teams button to render.</span></span> |
| <span data-ttu-id="a9154-154">msgText</span><span class="sxs-lookup"><span data-stu-id="a9154-154">msgText</span></span> | `data-msg-text` | <span data-ttu-id="a9154-155">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="a9154-155">string</span></span> | <span data-ttu-id="a9154-156">n/v</span><span class="sxs-lookup"><span data-stu-id="a9154-156">n/a</span></span> | <span data-ttu-id="a9154-157">Standardtext, der vor dem Link in das Feld zum Verfassen von Nachrichten eingefügt werden soll (Grenzwert von 200 Zeichen)</span><span class="sxs-lookup"><span data-stu-id="a9154-157">Default Text to be inserted before the link in the message compose box (200 character limit)</span></span> |
| <span data-ttu-id="a9154-158">assignInstr</span><span class="sxs-lookup"><span data-stu-id="a9154-158">assignInstr</span></span> | `data-assign-instr` | <span data-ttu-id="a9154-159">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="a9154-159">string</span></span> | <span data-ttu-id="a9154-160">n/v</span><span class="sxs-lookup"><span data-stu-id="a9154-160">n/a</span></span> | <span data-ttu-id="a9154-161">Standardtext, der in das Feld "Anweisungen" eingefügt werden soll (Grenzwert von 200 Zeichen)</span><span class="sxs-lookup"><span data-stu-id="a9154-161">Default Text to be inserted in the assignments "Instructions" field (200 character limit)</span></span> |
| <span data-ttu-id="a9154-162">assignTitle</span><span class="sxs-lookup"><span data-stu-id="a9154-162">assignTitle</span></span> | `data-assign-title` | <span data-ttu-id="a9154-163">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="a9154-163">string</span></span> | <span data-ttu-id="a9154-164">n/v</span><span class="sxs-lookup"><span data-stu-id="a9154-164">n/a</span></span> | <span data-ttu-id="a9154-165">Standardtext, der in das Zuordnungsfeld "Titel" eingefügt werden soll (Grenzwert von 50 Zeichen)</span><span class="sxs-lookup"><span data-stu-id="a9154-165">Default Text to be inserted in the assignments "Title" field (50 character limit)</span></span> |

### <a name="methods"></a><span data-ttu-id="a9154-166">Methoden</span><span class="sxs-lookup"><span data-stu-id="a9154-166">Methods</span></span>

**`shareToMicrosoftTeams.renderButtons(options)`**

<span data-ttu-id="a9154-167">`options` (optional): `{ elements?: HTMLElement[] }`</span><span class="sxs-lookup"><span data-stu-id="a9154-167">`options` (optional): `{ elements?: HTMLElement[] }`</span></span>

<span data-ttu-id="a9154-168">Rendert alle Freigabeschaltflächen, die sich derzeit auf der Seite befindet.</span><span class="sxs-lookup"><span data-stu-id="a9154-168">Renders all share buttons currently on the page.</span></span> <span data-ttu-id="a9154-169">Wenn ein optionales Objekt mit einer Liste von Elementen bereitgestellt wird, werden diese Elemente `options` in Freigabeschaltflächen gerendert.</span><span class="sxs-lookup"><span data-stu-id="a9154-169">If an optional `options` object is supplied with a list of elements, those elements will be rendered into share buttons.</span></span>

### <a name="setting-default-form-values"></a><span data-ttu-id="a9154-170">Festlegen von Standardformularwerten</span><span class="sxs-lookup"><span data-stu-id="a9154-170">Setting default form values</span></span>

<span data-ttu-id="a9154-171">Optional können Sie standardwerte für die folgenden Felder im Formular "In Teams freigeben" festlegen:</span><span class="sxs-lookup"><span data-stu-id="a9154-171">Optionally, you can choose to set default values for the following fields on the Share to Teams form:</span></span>

* <span data-ttu-id="a9154-172">Etwas dazu sagen ( `msgText` )</span><span class="sxs-lookup"><span data-stu-id="a9154-172">Say something about this (`msgText`)</span></span>
* <span data-ttu-id="a9154-173">Zuweisungsanweisungen ( `assignInstr` )</span><span class="sxs-lookup"><span data-stu-id="a9154-173">Assignment Instructions (`assignInstr`)</span></span>
* <span data-ttu-id="a9154-174">Zuweisungstitel ( `assignTitle` )</span><span class="sxs-lookup"><span data-stu-id="a9154-174">Assignment Title (`assignTitle`)</span></span>

#### <a name="example-default-form-values"></a><span data-ttu-id="a9154-175">Beispiel: Standardformularwerte</span><span class="sxs-lookup"><span data-stu-id="a9154-175">Example: Default form values</span></span>

```html
<span
    class="teams-share-button"
    data-href="https://www.microsoft.com/education/products/teams"
    data-msg-text="Default Message"
    data-assign-title="Default Assignment Title"
    data-assign-instr="Default Assignment Instructions"
></span>
```
