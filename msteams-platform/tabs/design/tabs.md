---
title: Entwurfsrichtlinien für Registerkarten
description: Beschreibt die Richtlinien zum Erstellen von Registerkarten für Inhalt und Zusammenarbeit.
keywords: Teams-Entwurfsrichtlinien Referenz-Framework-Registerkartenkonfiguration
ms.openlocfilehash: adf86678a42e2267af00734e1ef85efced882488
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674060"
---
# <a name="content-and-conversations-all-at-once-using-tabs"></a><span data-ttu-id="85e81-104">Inhalte und Unterhaltungen auf einmal mithilfe von Registerkarten</span><span class="sxs-lookup"><span data-stu-id="85e81-104">Content and conversations, all at once using tabs</span></span>

> [!Important]
> <span data-ttu-id="85e81-105">**Registerkarten auf mobilen Clients**</span><span class="sxs-lookup"><span data-stu-id="85e81-105">**Tabs on Mobile Clients**</span></span>
>
> <span data-ttu-id="85e81-106">Befolgten Sie die [Anleitungen für Registerkarten auf mobilen Geräten](~/tabs/design/tabs-mobile.md) , wenn Sie Ihre Registerkarten erstellen.</span><span class="sxs-lookup"><span data-stu-id="85e81-106">Follow the [guidance for tabs on mobile](~/tabs/design/tabs-mobile.md) when creating your tabs.</span></span> <span data-ttu-id="85e81-107">Wenn Ihre Registerkarte die Authentifizierung verwendet, müssen Sie Ihr Microsoft Teams-JavaScript-SDK auf Version 1.4.1 oder höher aktualisieren, oder die Authentifizierung schlägt fehl.</span><span class="sxs-lookup"><span data-stu-id="85e81-107">If your tab uses authentication, you must upgrade your Teams JavaScript SDK to version 1.4.1 or later, or authentication will fail.</span></span>
>
> <span data-ttu-id="85e81-108">**Persönliche Registerkarten (statisch) auf mobilen Geräten:**</span><span class="sxs-lookup"><span data-stu-id="85e81-108">**Personal (static) tabs on mobile:**</span></span>
>
> * <span data-ttu-id="85e81-109">Statische Registerkarten (persönliche APP) stehen in der [Entwicklervorschau](~/resources/dev-preview/developer-preview-intro.md)zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="85e81-109">Static tabs (personal app) are available in [developer preview](~/resources/dev-preview/developer-preview-intro.md).</span></span>
> * <span data-ttu-id="85e81-110">Stellen Sie beim Erstellen der statischen Registerkarten sicher, dass Sie den [Anweisungen für Tabs auf mobilen](~/tabs/design/tabs-mobile.md)</span><span class="sxs-lookup"><span data-stu-id="85e81-110">While building your static tabs, ensure to follow the [guidance for tabs on mobile](~/tabs/design/tabs-mobile.md)</span></span>
>
> <span data-ttu-id="85e81-111">**Registerkarten für Kanal/Gruppe (konfigurierbar) auf mobilen Geräten:**</span><span class="sxs-lookup"><span data-stu-id="85e81-111">**Channel/group (configurable) tabs on mobile:**</span></span>
>
> * <span data-ttu-id="85e81-112">Mobile Clients zeigen nur Registerkarten mit einem Wert für `websiteUrl`an.</span><span class="sxs-lookup"><span data-stu-id="85e81-112">Mobile clients only show tabs that have a value for `websiteUrl`.</span></span> <span data-ttu-id="85e81-113">Wenn die Registerkarte auf den mobilen Teams-Clients angezeigt werden soll, müssen Sie den Wert von `websiteUrl`festlegen.</span><span class="sxs-lookup"><span data-stu-id="85e81-113">If you want your tab to appear on the Teams mobile clients, you must set the value of `websiteUrl`.</span></span>
> * <span data-ttu-id="85e81-114">Das standardmäßig geöffnete Verhalten auf mobilen Geräten ist das `websiteUrl`öffnen außerhalb von Browser mithilfe von.</span><span class="sxs-lookup"><span data-stu-id="85e81-114">Default open behavior on mobile is to open outside in browser using the `websiteUrl`.</span></span> <span data-ttu-id="85e81-115">Wenn Sie für apps, die im öffentlichen APP-Speicher veröffentlicht werden, die Kanal Registerkarte standardmäßig in Microsoft Teams öffnen möchten, befolgten Sie die [Anleitungen für Registerkarten auf mobilen Geräten](~/tabs/design/tabs-mobile.md), und wenden Sie sich an Ihren Supportmitarbeiter, um eine weiße Liste zu fordern.</span><span class="sxs-lookup"><span data-stu-id="85e81-115">For apps published to the public App Store, if you want your channel tab to open inside teams by default, follow the [guidance for tabs on mobile](~/tabs/design/tabs-mobile.md), and reach out to your support rep to request to be whitelisted.</span></span>

<span data-ttu-id="85e81-116">Registerkarten sind Ansichtsbilder, die Sie zum Freigeben von Inhalten, halten von Unterhaltungen und Hosten von Drittanbieterdiensten verwenden können, die alle innerhalb des organischen Workflows eines Teams liegen.</span><span class="sxs-lookup"><span data-stu-id="85e81-116">Tabs are canvases that you can use to share content, hold conversations, and host third-party services, all within a team’s organic workflow.</span></span> <span data-ttu-id="85e81-117">Wenn Sie eine Registerkarte in Microsoft Teams erstellen, wird Ihre Webanwendungs-Front-und-Mitte platziert, wo Sie leicht von wichtigen Unterhaltungen aus zugänglich ist.</span><span class="sxs-lookup"><span data-stu-id="85e81-117">When you build a tab in Microsoft Teams, it puts your web app front and center where it’s easily accessible from key conversations.</span></span>

## <a name="guidelines"></a><span data-ttu-id="85e81-118">Anleitungen</span><span class="sxs-lookup"><span data-stu-id="85e81-118">Guidelines</span></span>

<span data-ttu-id="85e81-119">Auf einer Registerkarte "gut" sollten die folgenden Merkmale angezeigt werden:</span><span class="sxs-lookup"><span data-stu-id="85e81-119">A good tab should display the following characteristics:</span></span>

### <a name="focused-functionality"></a><span data-ttu-id="85e81-120">Fokussierte Funktionalität</span><span class="sxs-lookup"><span data-stu-id="85e81-120">Focused functionality</span></span>

<span data-ttu-id="85e81-121">Registerkarten funktionieren am besten, wenn Sie erstellt werden, um eine bestimmte Anforderung zu erfüllen.</span><span class="sxs-lookup"><span data-stu-id="85e81-121">Tabs work best when they’re built to address a specific need.</span></span> <span data-ttu-id="85e81-122">Konzentrieren Sie sich auf eine kleine Gruppe von Aufgaben oder eine Teilmenge der Daten, die für den Kanal relevant ist, in dem sich die Registerkarte befindet.</span><span class="sxs-lookup"><span data-stu-id="85e81-122">Focus on a small set of tasks or a subset of data that’s relevant to the channel the tab is in.</span></span>

### <a name="reduced-chrome"></a><span data-ttu-id="85e81-123">Reduziertes Chrom</span><span class="sxs-lookup"><span data-stu-id="85e81-123">Reduced chrome</span></span>

<span data-ttu-id="85e81-124">Vermeiden Sie es, mehrere Bereiche auf einer Registerkarte zu erstellen, Navigationsebenen hinzuzufügen oder Benutzer zu verpflichten, sowohl vertikal als auch horizontal in einer Registerkarte zu scrollen. In anderen Worten: versuchen Sie nicht, Registerkarten auf Ihrer Registerkarte zu haben.</span><span class="sxs-lookup"><span data-stu-id="85e81-124">Avoid creating multiple panels in a tab, adding layers of navigation, or requiring users to scroll both vertically and horizontally in one tab. In other words, try not to have tabs in your tab.</span></span>

> [!TIP]
> <span data-ttu-id="85e81-125">Vermeiden Sie es, mehrere Bereiche auf einer Registerkarte zu erstellen, Navigationsebenen hinzuzufügen oder Benutzer zu verpflichten, sowohl vertikal als auch horizontal in einer Registerkarte zu scrollen.</span><span class="sxs-lookup"><span data-stu-id="85e81-125">Avoid creating multiple panels in a tab, adding layers of navigation, or requiring users to scroll both vertically and horizontally in one tab.</span></span>

### <a name="integration"></a><span data-ttu-id="85e81-126">Integration</span><span class="sxs-lookup"><span data-stu-id="85e81-126">Integration</span></span>

<span data-ttu-id="85e81-127">Hier finden Sie Möglichkeiten, Benutzer über die Tab-Aktivität zu informieren, indem Sie beispielsweise Karten für eine Unterhaltung veröffentlichen.</span><span class="sxs-lookup"><span data-stu-id="85e81-127">Find ways to notify users about tab activity by posting cards to a conversation, for example.</span></span>

### <a name="conversational"></a><span data-ttu-id="85e81-128">Gesprächs</span><span class="sxs-lookup"><span data-stu-id="85e81-128">Conversational</span></span>

<span data-ttu-id="85e81-129">Finden Sie eine Möglichkeit, um eine Unterhaltung um eine Registerkarte zu erleichtern. Dadurch wird sichergestellt, dass Unterhaltungen auf dem Inhalt, den Daten oder dem Prozess zur Hand stehen.</span><span class="sxs-lookup"><span data-stu-id="85e81-129">Find a way to facilitate conversation around a tab. This ensures that conversations center on the content, data, or process at hand.</span></span>

### <a name="streamlined-access"></a><span data-ttu-id="85e81-130">Optimierter Zugriff</span><span class="sxs-lookup"><span data-stu-id="85e81-130">Streamlined access</span></span>

<span data-ttu-id="85e81-131">Stellen Sie sicher, dass Sie den richtigen Personen zum richtigen Zeitpunkt Zugriff gewähren.</span><span class="sxs-lookup"><span data-stu-id="85e81-131">Make sure you’re granting access to the right people at the right time.</span></span> <span data-ttu-id="85e81-132">Wenn Sie Ihren Anmeldeprozess einfach halten, können Sie keine Barrieren für Beiträge und Zusammenarbeit schaffen.</span><span class="sxs-lookup"><span data-stu-id="85e81-132">Keeping your sign-in process simple will avoid creating barriers to contribution and collaboration.</span></span>

### <a name="personality"></a><span data-ttu-id="85e81-133">Persönlichkeit</span><span class="sxs-lookup"><span data-stu-id="85e81-133">Personality</span></span>

<span data-ttu-id="85e81-134">Ihr Tab-Canvas bietet eine gute Gelegenheit, Ihre Benutzeroberfläche zu Branden.</span><span class="sxs-lookup"><span data-stu-id="85e81-134">Your tab canvas presents a good opportunity to brand your experience.</span></span> <span data-ttu-id="85e81-135">Integrieren Sie Ihre eigenen Logos, Farben und Layouts, um Persönlichkeit zu vermitteln.</span><span class="sxs-lookup"><span data-stu-id="85e81-135">Incorporate your own logos, colors, and layouts to communicate personality.</span></span>

<span data-ttu-id="85e81-136">Ihr Logo ist ein wichtiger Bestandteil ihrer Identität und eine Verbindung mit ihren Benutzern.</span><span class="sxs-lookup"><span data-stu-id="85e81-136">Your logo is an important part of your identity and a connection with your users.</span></span> <span data-ttu-id="85e81-137">Achten Sie darauf, Sie einzubeziehen.</span><span class="sxs-lookup"><span data-stu-id="85e81-137">So be sure to include it.</span></span>

* <span data-ttu-id="85e81-138">Platzieren Sie Ihr Logo in der linken oder rechten Ecke oder am unteren Rand</span><span class="sxs-lookup"><span data-stu-id="85e81-138">Place your logo in the left or right corner or along the bottom edge</span></span>
* <span data-ttu-id="85e81-139">Halten Sie Ihr Logo klein und unaufdringlich</span><span class="sxs-lookup"><span data-stu-id="85e81-139">Keep your logo small and unobtrusive</span></span>

> [!TIP]
> <span data-ttu-id="85e81-140">Arbeiten Sie mit unserem visuellen Stil, damit Ihr Dienst sich wie ein Teil von Microsoft Teams anfühlt.</span><span class="sxs-lookup"><span data-stu-id="85e81-140">Please work with our visual style so your service feels like a part of Teams.</span></span>

---

## <a name="tab-layouts"></a><span data-ttu-id="85e81-141">Registerkarten Layouts</span><span class="sxs-lookup"><span data-stu-id="85e81-141">Tab layouts</span></span>

[!include[Tab layouts](~/includes/design/tab-layouts.html)]

---

## <a name="types-of-tabs"></a><span data-ttu-id="85e81-142">Typen von Registerkarten</span><span class="sxs-lookup"><span data-stu-id="85e81-142">Types of tabs</span></span>

[!include[Tab types](~/includes/design/tab-types.html)]

---

## <a name="configuration-page-height"></a><span data-ttu-id="85e81-143">Höhe der Konfigurationsseiten</span><span class="sxs-lookup"><span data-stu-id="85e81-143">Configuration page height</span></span>

>[!NOTE]
><span data-ttu-id="85e81-144">Im September 2018 wurde die Höhe für die Registerkarten- [Konfigurationsseite](~/tabs/how-to/create-tab-pages/configuration-page.md) erhöht, während die Breite unverändert blieb.</span><span class="sxs-lookup"><span data-stu-id="85e81-144">In September 2018, the height for the tab [configuration page](~/tabs/how-to/create-tab-pages/configuration-page.md) was increased while the width remained unchanged.</span></span> <span data-ttu-id="85e81-145">Wenn Ihre APP für die ältere Größe ausgelegt ist, hat Ihre Registerkarten-Konfigurationsseite sehr viele vertikale Leerzeichen.</span><span class="sxs-lookup"><span data-stu-id="85e81-145">If your app is designed for the older size your tab configuration page will have a great deal of vertical whitespace.</span></span> <span data-ttu-id="85e81-146">Ältere Store-Apps, die von dieser Änderung ausgenommen sind, müssen sich nach der Aktualisierung an Microsoft wenden, um die neuen Dimensionen zu erfüllen.</span><span class="sxs-lookup"><span data-stu-id="85e81-146">Legacy store apps exempted from this change will need to contact Microsoft after updating to accommodate the new dimensions.</span></span>

<span data-ttu-id="85e81-147">Die Abmessungen der Registerkarten-Konfigurationsseite:</span><span class="sxs-lookup"><span data-stu-id="85e81-147">The dimensions of the tab configuration page:</span></span>

<img width="450px" title="Größen für Konfigurationsregisterkarten" src="~/assets/images/tabs/config-dialog-Contoso2.png" />

### <a name="guidelines-for-tab-configuration-page-format"></a><span data-ttu-id="85e81-149">Richtlinien für das Seitenformat der Registerkartenkonfiguration</span><span class="sxs-lookup"><span data-stu-id="85e81-149">Guidelines for tab configuration page format</span></span>

* <span data-ttu-id="85e81-150">Stützen Sie die minimale Höhe Ihres Inhaltsbereichs auf der Registerkarte Konfigurationsseite auf Grafikelementen mit fester Höhe.</span><span class="sxs-lookup"><span data-stu-id="85e81-150">Base the minimum height of your content area of your tab configuration page on fixed-height graphic elements.</span></span>
* <span data-ttu-id="85e81-151">Berechnen Sie den verfügbaren vertikalen Raum (die Höhe des Inhaltsbereichs auf der Konfigurations `window.innerHeight`Seite) mithilfe von.</span><span class="sxs-lookup"><span data-stu-id="85e81-151">Calculate available vertical space (the height of the content area in the configuration page) using `window.innerHeight`.</span></span> <span data-ttu-id="85e81-152">Dadurch wird die Größe der, `<iframe>` in der sich die Konfigurationsseite befindet, zurückgegeben, die sich in zukünftigen Versionen ändern kann.</span><span class="sxs-lookup"><span data-stu-id="85e81-152">This returns the size of the `<iframe>` in which your configuration page resides, which may change in future releases.</span></span> <span data-ttu-id="85e81-153">Wenn Sie diesen Wert verwenden, wird der Inhalt automatisch an zukünftige Änderungen angepasst.</span><span class="sxs-lookup"><span data-stu-id="85e81-153">By using this value your content will adjust automatically to future changes.</span></span>
* <span data-ttu-id="85e81-154">Zuweisen von vertikalem Abstand zu den Elementen der Variablen Höhe minus was für die Elemente mit fester Höhe benötigt wird.</span><span class="sxs-lookup"><span data-stu-id="85e81-154">Allocate vertical space to the variable-height elements minus what's needed for the fixed-height elements.</span></span>
* <span data-ttu-id="85e81-155">Für den *Anmelde* Status vertikal und horizontal zentrieren Sie den Inhalt.</span><span class="sxs-lookup"><span data-stu-id="85e81-155">For the *login* state, vertically and horizontally center the content.</span></span>
* <span data-ttu-id="85e81-156">Wenn Sie ein Hintergrundbild wünschen, benötigen Sie ein neues Bild, das an den Bereich angepasst wird (bevorzugt), oder Sie können das gleiche Bild beibehalten und zwischen folgenden Themen wählen:</span><span class="sxs-lookup"><span data-stu-id="85e81-156">If you want a background image, you need either a new image, sized to fit the area (preferred), or you can keep the same image and choose between:</span></span>
  * <span data-ttu-id="85e81-157">Ausrichtung an der oberen linken Ecke.</span><span class="sxs-lookup"><span data-stu-id="85e81-157">aligning to the upper left hand corner.</span></span>
  * <span data-ttu-id="85e81-158">Skalieren des Bilds an die Größe</span><span class="sxs-lookup"><span data-stu-id="85e81-158">scaling the image to fit.</span></span>

<span data-ttu-id="85e81-159">Bei ordnungsgemäßer Größe sollte Ihre Registerkarten-Konfigurationsseite wie folgt aussehen:</span><span class="sxs-lookup"><span data-stu-id="85e81-159">When properly sized, your tab configuration page should look similar to this:</span></span>

<img width="450px" title="Neue Registerkarte "Konfiguration"" src="~/assets/images/tabs/config-dialog-Contoso.png" />

## <a name="best-practices"></a><span data-ttu-id="85e81-161">Bewährte Methoden</span><span class="sxs-lookup"><span data-stu-id="85e81-161">Best practices</span></span>

### <a name="always-include-a-default-state"></a><span data-ttu-id="85e81-162">Immer einen Standardzustand einschließen</span><span class="sxs-lookup"><span data-stu-id="85e81-162">Always include a default state</span></span>

<span data-ttu-id="85e81-163">Schließen Sie einen Standardzustand ein, um das Einrichten von Registerkarten zu vereinfachen, auch wenn die Registerkarte konfigurierbar ist.</span><span class="sxs-lookup"><span data-stu-id="85e81-163">Include a default state to make tabs easy to set up even if your tab is configurable.</span></span>

### <a name="deep-linking"></a><span data-ttu-id="85e81-164">Deep-Verknüpfung</span><span class="sxs-lookup"><span data-stu-id="85e81-164">Deep linking</span></span>

<span data-ttu-id="85e81-165">Wann immer möglich, sollten Karten und Bots einen tiefen Link zu umfangreicheren Daten in einer gehosteten RegisterkarteErstellen. Beispielsweise kann eine Karte eine Zusammenfassung der Fehlerdaten anzeigen, aber durch Klicken darauf kann der gesamte Fehler in einer Registerkarte angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="85e81-165">Whenever possible, cards and bots should deep link to richer data in a hosted tab. For example, a card may show a summary of bug data, but clicking it can shows the entire bug in a tab.</span></span>

### <a name="naming"></a><span data-ttu-id="85e81-166">Benennungs</span><span class="sxs-lookup"><span data-stu-id="85e81-166">Naming</span></span>

<span data-ttu-id="85e81-167">In vielen Fällen kann der Name Ihrer APP einen großen Namen für die Registerkarte bilden.</span><span class="sxs-lookup"><span data-stu-id="85e81-167">In many cases, the name of your app may make a great tab name.</span></span> <span data-ttu-id="85e81-168">Sie sollten Ihre Registerkarten jedoch entsprechend der von Ihnen bereitgestellten Funktionen benennen.</span><span class="sxs-lookup"><span data-stu-id="85e81-168">But consider naming your tabs according to the functionality they provide.</span></span>
