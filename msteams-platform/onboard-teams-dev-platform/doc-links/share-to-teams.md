---
title: Hinzufügen einer Freigabe zur Schaltfläche "Teams" zu Ihrer Website
description: Vorgehensweise hinzufügen der Schaltfläche "Share to Teams Embedded" auf Ihrer Website
keywords: Freigeben von Teams in Microsoft Teams
ms.openlocfilehash: 0ebd47af068bf523f27c19241b85d2137af3ada6
ms.sourcegitcommit: 9fbc701a9a039ecdc360aefbe86df52b9c3593f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/12/2020
ms.locfileid: "46652016"
---
# <a name="adding-a-share-to-teams-button-to-your-website"></a><span data-ttu-id="eb4f6-104">Hinzufügen einer Freigabe zur Schaltfläche "Teams" zu Ihrer Website</span><span class="sxs-lookup"><span data-stu-id="eb4f6-104">Adding a Share to Teams button to your website</span></span>

>[!NOTE]
> * <span data-ttu-id="eb4f6-105">Nur die Desktop Versionen von Edge und Chrome werden unterstützt.</span><span class="sxs-lookup"><span data-stu-id="eb4f6-105">Only the desktop versions of Edge and Chrome are supported.</span></span>
> * <span data-ttu-id="eb4f6-106">Die Verwendung von Freemium-oder Gastkonten wird nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="eb4f6-106">Use of Freemium or guest accounts is not supported.</span></span>

<span data-ttu-id="eb4f6-107">Drittanbieterwebsites können das Startprogramm Skript verwenden, um Share to Teams-Schaltflächen auf Ihren Webseiten einzubetten, wodurch die Benutzeroberfläche für Teams in einem Popupfenster gestartet wird, wenn darauf geklickt wird.</span><span class="sxs-lookup"><span data-stu-id="eb4f6-107">Third-party websites can use the launcher script to embed Share to Teams buttons on their webpages which will launch the Share to Teams experience in a popup window when clicked.</span></span> <span data-ttu-id="eb4f6-108">Auf diese Weise können Sie einen Link direkt für einen beliebigen Benutzer oder Microsoft Teams-Kanal freigeben, ohne Kontext zu wechseln.</span><span class="sxs-lookup"><span data-stu-id="eb4f6-108">This will allow you to share a link directly to any person or Microsoft Teams channel without switching context.</span></span>

![Popup "an Teams freigeben"](~/assets/images/share-to-teams-popup.png)

## <a name="how-to-embed-a-share-to-teams-button"></a><span data-ttu-id="eb4f6-110">Vorgehensweise Einbetten einer Share to Teams-Schaltfläche</span><span class="sxs-lookup"><span data-stu-id="eb4f6-110">How to embed a Share to Teams button</span></span>

<span data-ttu-id="eb4f6-111">Zunächst müssen Sie das `launcher.js` Skript auf Ihrer Webseite hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="eb4f6-111">First, you'll need to add the `launcher.js` script on your webpage.</span></span>

```html
<script async defer src="https://teams.microsoft.com/share/launcher.js"></script>
```

<span data-ttu-id="eb4f6-112">Fügen Sie als nächstes ein HTML-Element auf Ihrer Webseite mit dem `teams-share-button` Class-Attribut und dem Link hinzu, der in dem Attribut freigegeben werden soll `data-href` .</span><span class="sxs-lookup"><span data-stu-id="eb4f6-112">Next, add an HTML element on your webpage with the `teams-share-button` class attribute and the link to share in the `data-href` attribute.</span></span>

```html
<div
  class="teams-share-button"
  data-href="https://<link-to-be-shared>">
</div>
```

<span data-ttu-id="eb4f6-113">Dadurch wird das Microsoft Teams-Symbol zu Ihrer Website hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="eb4f6-113">This will add the Microsoft Teams icon to your website.</span></span>

![Symbol "an Teams freigeben"](~/assets/icons/share-to-teams-icon.png)

<span data-ttu-id="eb4f6-115">Wenn Sie eine andere Symbolgröße für die Schaltfläche Freigeben für Teams verwenden möchten, verwenden Sie optional das- `data-icon-px-size` Attribut.</span><span class="sxs-lookup"><span data-stu-id="eb4f6-115">Optionally, if you want a different icon size for the Share to Teams button, use the `data-icon-px-size` attribute.</span></span>

```html
<div
  class="teams-share-button"
  data-href="https://<link-to-be-shared>"
  data-icon-px-size="64">
</div>
```

<span data-ttu-id="eb4f6-116">Wenn Sie wissen, dass die URL-Vorschau von Ihrem Link freigegeben wird, in Microsoft Teams nicht gut gerendert wird (beispielsweise würde die Verknüpfung Benutzerauthentifizierung erfordern), können Sie die URL-Vorschau deaktivieren, indem Sie das `data-preview` auf festgelegte Attribut hinzufügen `false` .</span><span class="sxs-lookup"><span data-stu-id="eb4f6-116">If you know that the URL preview from your link to be shared won't render well in Teams (for example the link would require user authentication) you can disable the URL preview by adding the `data-preview` attribute set to `false`.</span></span>

```html
<div
  class="teams-share-button"
  data-href="https://<link-to-be-shared>"
  data-preview="false">
</div>
```

<span data-ttu-id="eb4f6-117">Wenn die Seite Inhalt dynamisch rendert, können Sie die `shareToMicrosoftTeams.renderButtons()` -Methode verwenden, um zu erzwingen, dass die Schaltfläche **Freigeben** an der entsprechenden Stelle in der Pipeline gerendert wird.</span><span class="sxs-lookup"><span data-stu-id="eb4f6-117">If your page dynamically renders content, you can use the the `shareToMicrosoftTeams.renderButtons()` method to force the **Share** button to render at the appropriate place in the pipeline.</span></span>

## <a name="crafting-your-website-preview"></a><span data-ttu-id="eb4f6-118">Fertigen Ihrer Website Vorschau</span><span class="sxs-lookup"><span data-stu-id="eb4f6-118">Crafting your website preview</span></span>

<span data-ttu-id="eb4f6-119">Wenn Ihre Website für Teams freigegeben wird, enthält die Karte, die in den ausgewählten Kanal eingefügt wird, eine Vorschau Ihrer Website.</span><span class="sxs-lookup"><span data-stu-id="eb4f6-119">When your website is shared to Teams, the card that is inserted into the selected channel will contain a preview of your website.</span></span> <span data-ttu-id="eb4f6-120">Sie können das Verhalten dieser Vorschau steuern, indem Sie sicherstellen, dass der freigegebenen Website (der URL) die entsprechenden Metadaten hinzugefügt werden `data-href` .</span><span class="sxs-lookup"><span data-stu-id="eb4f6-120">You can control the behavior of this preview by ensuring the appropriate meta-data is added to the website being shared (the `data-href` URL).</span></span> <span data-ttu-id="eb4f6-121">In der folgenden Tabelle werden die erforderlichen Tags dargestellt.</span><span class="sxs-lookup"><span data-stu-id="eb4f6-121">The table below outlines the necessary tags.</span></span> <span data-ttu-id="eb4f6-122">Sie können entweder die HTML-Standardversionen oder die Open Graph-Version verwenden.</span><span class="sxs-lookup"><span data-stu-id="eb4f6-122">You can use either the html default versions, or the Open Graph version.</span></span>

<span data-ttu-id="eb4f6-123">Damit die Vorschau angezeigt wird, müssen Sie Folgendes tun:</span><span class="sxs-lookup"><span data-stu-id="eb4f6-123">In order for the preview to be displayed you must:</span></span>

* <span data-ttu-id="eb4f6-124">Fügen Sie entweder ein Miniaturbild oder sowohl einen Titel als auch eine Beschreibung ein (um optimale Ergebnisse zu erzielen, schließen Sie alle drei ein).</span><span class="sxs-lookup"><span data-stu-id="eb4f6-124">Include either a Thumbnail image, or both a Title and Description (for best results, include all three).</span></span>
* <span data-ttu-id="eb4f6-125">Für die freigegebene URL kann keine Authentifizierung erforderlich sein.</span><span class="sxs-lookup"><span data-stu-id="eb4f6-125">The URL being shared cannot require authentication.</span></span> <span data-ttu-id="eb4f6-126">Wenn dies der Fall ist, können Sie ihn trotzdem freigeben, die Vorschau wird jedoch nicht erstellt.</span><span class="sxs-lookup"><span data-stu-id="eb4f6-126">If it does you can still share it, but the preview will not be created.</span></span>

|<span data-ttu-id="eb4f6-127">Wert</span><span class="sxs-lookup"><span data-stu-id="eb4f6-127">Value</span></span>|<span data-ttu-id="eb4f6-128">Metatag</span><span class="sxs-lookup"><span data-stu-id="eb4f6-128">Meta tag</span></span>| <span data-ttu-id="eb4f6-129">Diagramm öffnen</span><span class="sxs-lookup"><span data-stu-id="eb4f6-129">Open Graph</span></span>|
|----|----|----|
|<span data-ttu-id="eb4f6-130">Title</span><span class="sxs-lookup"><span data-stu-id="eb4f6-130">Title</span></span>|`<meta name="title" content="Example Page Title">`|`<meta property="og:title" content="Example Page Title">`|
|<span data-ttu-id="eb4f6-131">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="eb4f6-131">Description</span></span>|`<meta name="description" content="Example Page Description">`|`<meta property="og:description" content="Example Page Description">`|
|<span data-ttu-id="eb4f6-132">Miniaturbild</span><span class="sxs-lookup"><span data-stu-id="eb4f6-132">Thumbnail Image</span></span>| <span data-ttu-id="eb4f6-133">keine</span><span class="sxs-lookup"><span data-stu-id="eb4f6-133">none</span></span> |`<meta property="og:image" content="http://example.com/image.jpg">`|

## <a name="share-to-teams-for-education"></a><span data-ttu-id="eb4f6-134">Freigeben für Teams für Bildungseinrichtungen</span><span class="sxs-lookup"><span data-stu-id="eb4f6-134">Share to Teams for Education</span></span>

<span data-ttu-id="eb4f6-135">Für Lehrer, die die Schaltfläche "für Teams freigeben" verwenden, erhalten Sie eine zusätzliche Option für `Create an Assignment` .</span><span class="sxs-lookup"><span data-stu-id="eb4f6-135">For teachers using the Share to Teams button you'll be given an additional option to `Create an Assignment`.</span></span> <span data-ttu-id="eb4f6-136">Auf diese Weise können Sie schnell eine Zuordnung im ausgewählten Team basierend auf dem freigegebenen Link erstellen.</span><span class="sxs-lookup"><span data-stu-id="eb4f6-136">This enables you to quickly create an assignment in the chosen Team based on the shared link.</span></span>

![Popup "an Teams freigeben"](~/assets/images/share-to-teams-popup-edu.png)

## <a name="full-launcherjs-definition"></a><span data-ttu-id="eb4f6-138">Vollständige launcher.js Definition</span><span class="sxs-lookup"><span data-stu-id="eb4f6-138">Full launcher.js definition</span></span>

| <span data-ttu-id="eb4f6-139">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="eb4f6-139">Property</span></span> | <span data-ttu-id="eb4f6-140">HTML-Attribut</span><span class="sxs-lookup"><span data-stu-id="eb4f6-140">HTML attribute</span></span> | <span data-ttu-id="eb4f6-141">Typ</span><span class="sxs-lookup"><span data-stu-id="eb4f6-141">Type</span></span> | <span data-ttu-id="eb4f6-142">Standard</span><span class="sxs-lookup"><span data-stu-id="eb4f6-142">Default</span></span> | <span data-ttu-id="eb4f6-143">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="eb4f6-143">Description</span></span> |
| -------------- | ---------------------- | --------------------- | ------- | ---------------------------------------------------------------------- |
| <span data-ttu-id="eb4f6-144">href</span><span class="sxs-lookup"><span data-stu-id="eb4f6-144">href</span></span> | `data-href` | <span data-ttu-id="eb4f6-145">string</span><span class="sxs-lookup"><span data-stu-id="eb4f6-145">string</span></span> | <span data-ttu-id="eb4f6-146">n/v</span><span class="sxs-lookup"><span data-stu-id="eb4f6-146">n/a</span></span> | <span data-ttu-id="eb4f6-147">Die href des freizugebenden Inhalts.</span><span class="sxs-lookup"><span data-stu-id="eb4f6-147">The href of the content to share.</span></span> |
| <span data-ttu-id="eb4f6-148">Vorschau</span><span class="sxs-lookup"><span data-stu-id="eb4f6-148">preview</span></span> | `data-preview` | <span data-ttu-id="eb4f6-149">Boolean (als Zeichenfolge)</span><span class="sxs-lookup"><span data-stu-id="eb4f6-149">boolean (as a string)</span></span> | `true` | <span data-ttu-id="eb4f6-150">Gibt an, ob eine Vorschau des freizugebenden Inhalts angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="eb4f6-150">Whether or not to show a preview of the content to share.</span></span> |
| <span data-ttu-id="eb4f6-151">iconPxSize</span><span class="sxs-lookup"><span data-stu-id="eb4f6-151">iconPxSize</span></span> | `data-icon-px-size` | <span data-ttu-id="eb4f6-152">Zahl (als Zeichenfolge)</span><span class="sxs-lookup"><span data-stu-id="eb4f6-152">number (as a string)</span></span> | `32` | <span data-ttu-id="eb4f6-153">Die Größe der zu rendernden Schaltfläche "Share-to-Teams" in Pixel.</span><span class="sxs-lookup"><span data-stu-id="eb4f6-153">The size in pixels of the Share-to-Teams button to render.</span></span> |
| <span data-ttu-id="eb4f6-154">msgText</span><span class="sxs-lookup"><span data-stu-id="eb4f6-154">msgText</span></span> | `data-msg-text` | <span data-ttu-id="eb4f6-155">string</span><span class="sxs-lookup"><span data-stu-id="eb4f6-155">string</span></span> | <span data-ttu-id="eb4f6-156">n/v</span><span class="sxs-lookup"><span data-stu-id="eb4f6-156">n/a</span></span> | <span data-ttu-id="eb4f6-157">Standard Text, der vor dem Link im Feld Nachricht erstellen eingefügt werden soll (Grenzwert für 200 Zeichen)</span><span class="sxs-lookup"><span data-stu-id="eb4f6-157">Default Text to be inserted before the link in the message compose box (200 character limit)</span></span> |
| <span data-ttu-id="eb4f6-158">assignInstr</span><span class="sxs-lookup"><span data-stu-id="eb4f6-158">assignInstr</span></span> | `data-assign-instr` | <span data-ttu-id="eb4f6-159">string</span><span class="sxs-lookup"><span data-stu-id="eb4f6-159">string</span></span> | <span data-ttu-id="eb4f6-160">n/v</span><span class="sxs-lookup"><span data-stu-id="eb4f6-160">n/a</span></span> | <span data-ttu-id="eb4f6-161">Standard Text, der in das Feldzuweisungen "Instructions" eingefügt werden soll (Grenzwert für 200 Zeichen)</span><span class="sxs-lookup"><span data-stu-id="eb4f6-161">Default Text to be inserted in the assignments "Instructions" field (200 character limit)</span></span> |
| <span data-ttu-id="eb4f6-162">assignTitle</span><span class="sxs-lookup"><span data-stu-id="eb4f6-162">assignTitle</span></span> | `data-assign-title` | <span data-ttu-id="eb4f6-163">string</span><span class="sxs-lookup"><span data-stu-id="eb4f6-163">string</span></span> | <span data-ttu-id="eb4f6-164">n/v</span><span class="sxs-lookup"><span data-stu-id="eb4f6-164">n/a</span></span> | <span data-ttu-id="eb4f6-165">Standard Text, der in das Feldzuweisungen "Title" eingefügt werden soll (Grenzwert für 50 Zeichen)</span><span class="sxs-lookup"><span data-stu-id="eb4f6-165">Default Text to be inserted in the assignments "Title" field (50 character limit)</span></span> |

### <a name="methods"></a><span data-ttu-id="eb4f6-166">Methoden</span><span class="sxs-lookup"><span data-stu-id="eb4f6-166">Methods</span></span>

**`shareToMicrosoftTeams.renderButtons(options)`**

<span data-ttu-id="eb4f6-167">`options` (optional): `{ elements?: HTMLElement[] }`</span><span class="sxs-lookup"><span data-stu-id="eb4f6-167">`options` (optional): `{ elements?: HTMLElement[] }`</span></span>

<span data-ttu-id="eb4f6-168">Rendert alle derzeit auf der Seite befindlichen Freigabe Schaltflächen.</span><span class="sxs-lookup"><span data-stu-id="eb4f6-168">Renders all share buttons currently on the page.</span></span> <span data-ttu-id="eb4f6-169">Wenn ein optionales `options` Objekt mit einer Liste von Elementen angegeben wird, werden diese Elemente in Freigabe Schaltflächen gerendert.</span><span class="sxs-lookup"><span data-stu-id="eb4f6-169">If an optional `options` object is supplied with a list of elements, those elements will be rendered into share buttons.</span></span>

### <a name="setting-default-form-values"></a><span data-ttu-id="eb4f6-170">Festlegen von Standardformular Werten</span><span class="sxs-lookup"><span data-stu-id="eb4f6-170">Setting default form values</span></span>

<span data-ttu-id="eb4f6-171">Optional können Sie die Standardwerte für die folgenden Felder im Formular "freigeben für Teams" festlegen:</span><span class="sxs-lookup"><span data-stu-id="eb4f6-171">Optionally, you can choose to set default values for the following fields on the Share to Teams form:</span></span>

* <span data-ttu-id="eb4f6-172">Sagen Sie etwas zu diesem ( `msgText` )</span><span class="sxs-lookup"><span data-stu-id="eb4f6-172">Say something about this (`msgText`)</span></span>
* <span data-ttu-id="eb4f6-173">Zuordnungsanweisungen ( `assignInstr` )</span><span class="sxs-lookup"><span data-stu-id="eb4f6-173">Assignment Instructions (`assignInstr`)</span></span>
* <span data-ttu-id="eb4f6-174">Zuordnungs Titel ( `assignTitle` )</span><span class="sxs-lookup"><span data-stu-id="eb4f6-174">Assignment Title (`assignTitle`)</span></span>

#### <a name="example-default-form-values"></a><span data-ttu-id="eb4f6-175">Beispiel: Standardformular Werte</span><span class="sxs-lookup"><span data-stu-id="eb4f6-175">Example: Default form values</span></span>

```html
<span
    class="teams-share-button"
    data-href="https://www.microsoft.com/education/products/teams"
    data-msg-text="Default Message"
    data-assign-title="Default Assignment Title"
    data-assign-instr="Default Assignment Instructions"
></span>
```
