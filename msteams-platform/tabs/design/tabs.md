---
title: Entwurfsrichtlinien für Registerkarten
description: Beschreibt die Richtlinien zum Erstellen von Registerkarten für Inhalt und Zusammenarbeit.
keywords: Teams-Entwurfsrichtlinien Referenz-Framework-Registerkartenkonfiguration
ms.openlocfilehash: b6394b164c5d57adfa4c796c89339f1586241396
ms.sourcegitcommit: e8dfcb167274e996395b77d65999991a18f2051a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/15/2020
ms.locfileid: "47819039"
---
# <a name="content-and-conversations-all-at-once-using-tabs"></a><span data-ttu-id="13a29-104">Inhalte und Unterhaltungen auf einmal mithilfe von Registerkarten</span><span class="sxs-lookup"><span data-stu-id="13a29-104">Content and conversations, all at once using tabs</span></span>

> [!Important]
> <span data-ttu-id="13a29-105">**Registerkarten auf mobilen Clients**</span><span class="sxs-lookup"><span data-stu-id="13a29-105">**Tabs on Mobile Clients**</span></span>
>
> <span data-ttu-id="13a29-106">Befolgten Sie die [Anleitungen für Registerkarten auf mobilen Geräten](./tabs-mobile.md) , wenn Sie Ihre Registerkarten erstellen.</span><span class="sxs-lookup"><span data-stu-id="13a29-106">Follow the [guidance for tabs on mobile](./tabs-mobile.md) when creating your tabs.</span></span> <span data-ttu-id="13a29-107">Wenn Ihre Registerkarte die Authentifizierung verwendet, müssen Sie Ihr Microsoft Teams-JavaScript-SDK auf Version 1.4.1 oder höher aktualisieren, oder die Authentifizierung schlägt fehl.</span><span class="sxs-lookup"><span data-stu-id="13a29-107">If your tab uses authentication, you must upgrade your Teams JavaScript SDK to version 1.4.1 or later, or authentication will fail.</span></span>
>
> <span data-ttu-id="13a29-108">**Registerkarten für Kanal/Gruppe (konfigurierbar) auf mobilen Geräten:**</span><span class="sxs-lookup"><span data-stu-id="13a29-108">**Channel/group (configurable) tabs on mobile:**</span></span>
>
> * <span data-ttu-id="13a29-109">Mobile Clients zeigen nur konfigurierbare Registerkarten mit einem Wert für an `websiteUrl` .</span><span class="sxs-lookup"><span data-stu-id="13a29-109">Mobile clients only show configurable tabs that have a value for `websiteUrl`.</span></span> <span data-ttu-id="13a29-110">Wenn die Registerkarte auf den mobilen Teams-Clients angezeigt werden soll, müssen Sie den Wert von festlegen `websiteUrl` .</span><span class="sxs-lookup"><span data-stu-id="13a29-110">If you want your tab to appear on the Teams mobile clients, you must set the value of `websiteUrl`.</span></span>
> * <span data-ttu-id="13a29-111">Das standardmäßig geöffnete Verhalten auf mobilen Geräten ist das Öffnen außerhalb von Browser mithilfe von `websiteUrl` .</span><span class="sxs-lookup"><span data-stu-id="13a29-111">Default open behavior on mobile is to open outside in browser using the `websiteUrl`.</span></span> <span data-ttu-id="13a29-112">Wenn Sie für apps, die im öffentlichen APP-Speicher veröffentlicht werden, die Kanal Registerkarte standardmäßig in Microsoft Teams öffnen möchten, befolgten Sie die [Anleitungen für Registerkarten auf mobilen Geräten](~/tabs/design/tabs-mobile.md), und wenden Sie sich an Ihren Supportmitarbeiter, um eine weiße Liste zu fordern.</span><span class="sxs-lookup"><span data-stu-id="13a29-112">For apps published to the public App Store, if you want your channel tab to open inside teams by default, follow the [guidance for tabs on mobile](~/tabs/design/tabs-mobile.md), and reach out to your support rep to request to be whitelisted.</span></span>

<span data-ttu-id="13a29-113">Registerkarten sind Ansichtsbilder, die Sie zum Freigeben von Inhalten, halten von Unterhaltungen und Hosten von Drittanbieterdiensten verwenden können, die alle innerhalb des organischen Workflows eines Teams liegen.</span><span class="sxs-lookup"><span data-stu-id="13a29-113">Tabs are canvases that you can use to share content, hold conversations, and host third-party services, all within a team’s organic workflow.</span></span> <span data-ttu-id="13a29-114">Wenn Sie eine Registerkarte in Microsoft Teams erstellen, wird Ihre Webanwendungs-Front-und-Mitte platziert, wo Sie leicht von wichtigen Unterhaltungen aus zugänglich ist.</span><span class="sxs-lookup"><span data-stu-id="13a29-114">When you build a tab in Microsoft Teams, it puts your web app front and center where it’s easily accessible from key conversations.</span></span>

## <a name="guidelines"></a><span data-ttu-id="13a29-115">Anleitungen</span><span class="sxs-lookup"><span data-stu-id="13a29-115">Guidelines</span></span>

<span data-ttu-id="13a29-116">Auf einer Registerkarte "gut" sollten die folgenden Merkmale angezeigt werden:</span><span class="sxs-lookup"><span data-stu-id="13a29-116">A good tab should display the following characteristics:</span></span>

### <a name="focused-functionality"></a><span data-ttu-id="13a29-117">Fokussierte Funktionalität</span><span class="sxs-lookup"><span data-stu-id="13a29-117">Focused functionality</span></span>

<span data-ttu-id="13a29-118">Registerkarten funktionieren am besten, wenn Sie erstellt werden, um eine bestimmte Anforderung zu erfüllen.</span><span class="sxs-lookup"><span data-stu-id="13a29-118">Tabs work best when they’re built to address a specific need.</span></span> <span data-ttu-id="13a29-119">Konzentrieren Sie sich auf eine kleine Gruppe von Aufgaben oder eine Teilmenge der Daten, die für den Kanal relevant ist, in dem sich die Registerkarte befindet.</span><span class="sxs-lookup"><span data-stu-id="13a29-119">Focus on a small set of tasks or a subset of data that’s relevant to the channel the tab is in.</span></span>

### <a name="reduced-chrome"></a><span data-ttu-id="13a29-120">Einfach halten</span><span class="sxs-lookup"><span data-stu-id="13a29-120">Reduced chrome</span></span>

<span data-ttu-id="13a29-121">Vermeiden Sie es, auf einer Registerkarte mehrere Panels zu erstellen, Navigationsebenen hinzuzufügen oder zu fordern, dass Benutzer auf einer Registerkarte sowohl vertikal als auch horizontal scrollen. Versuchen Sie also, keine Registerkarten auf Ihrer Registerkarte zu haben.</span><span class="sxs-lookup"><span data-stu-id="13a29-121">Avoid creating multiple panels in a tab, adding layers of navigation, or requiring users to scroll both vertically and horizontally in one tab. In other words, try not to have tabs in your tab.</span></span>

### <a name="integration"></a><span data-ttu-id="13a29-122">Integration</span><span class="sxs-lookup"><span data-stu-id="13a29-122">Integration</span></span>

<span data-ttu-id="13a29-123">Hier finden Sie Möglichkeiten, Benutzer über die Tab-Aktivität zu informieren, indem Sie einer Unterhaltung [Adaptive Karten](../../task-modules-and-cards/what-are-cards.md#adaptive-cards) senden.</span><span class="sxs-lookup"><span data-stu-id="13a29-123">Find ways to notify users about tab activity by posting [adaptive cards](../../task-modules-and-cards/what-are-cards.md#adaptive-cards) to a conversation.</span></span>

### <a name="conversational"></a><span data-ttu-id="13a29-124">Unterhaltung</span><span class="sxs-lookup"><span data-stu-id="13a29-124">Conversational</span></span>

<span data-ttu-id="13a29-125">Finden Sie eine Möglichkeit, um eine Unterhaltung um eine Registerkarte zu erleichtern. Dadurch wird sichergestellt, dass Unterhaltungen auf dem Inhalt, den Daten oder dem Prozess zur Hand stehen.</span><span class="sxs-lookup"><span data-stu-id="13a29-125">Find a way to facilitate conversation around a tab. This ensures that conversations center on the content, data, or process at hand.</span></span>

### <a name="streamlined-access"></a><span data-ttu-id="13a29-126">Optimierter Zugriff</span><span class="sxs-lookup"><span data-stu-id="13a29-126">Streamlined access</span></span>

<span data-ttu-id="13a29-127">Stellen Sie sicher, dass Sie den richtigen Personen zum richtigen Zeitpunkt Zugriff gewähren.</span><span class="sxs-lookup"><span data-stu-id="13a29-127">Make sure you’re granting access to the right people at the right time.</span></span> <span data-ttu-id="13a29-128">Wenn Sie Ihren Anmeldeprozess einfach halten, können Sie keine Barrieren für Beiträge und Zusammenarbeit schaffen.</span><span class="sxs-lookup"><span data-stu-id="13a29-128">Keeping your sign-in process simple will avoid creating barriers to contribution and collaboration.</span></span>

### <a name="responsiveness-to-window-sizing"></a><span data-ttu-id="13a29-129">Reaktionsfähigkeit auf Fenstergröße</span><span class="sxs-lookup"><span data-stu-id="13a29-129">Responsiveness to window sizing</span></span>

<span data-ttu-id="13a29-130">Teams können in Fenstergrößen so klein wie 720px verwendet werden, damit sichergestellt ist, dass eine Registerkarte in einem kleinen Fenster nutzbar ist, ist genauso wichtig wie die Benutzerfreundlichkeit bei sehr hohen Auflösungen.</span><span class="sxs-lookup"><span data-stu-id="13a29-130">Teams can be used in window sizes as small as 720px, so making sure that a tab is usable in a small window is just as important as usability at very high resolutions.</span></span>

### <a name="flat-navigation"></a><span data-ttu-id="13a29-131">Flache Navigation</span><span class="sxs-lookup"><span data-stu-id="13a29-131">Flat navigation</span></span>

<span data-ttu-id="13a29-132">Wir bitten Entwickler nicht, Ihr gesamtes Portal einer Registerkarte hinzuzufügen. Die relativ flache Navigation hilft dabei, ein einfacheres Unterhaltungs Modell beizubehalten.</span><span class="sxs-lookup"><span data-stu-id="13a29-132">We ask developers not to add their entire portal to a tab. Keeping the navigation relatively flat helps maintain a simpler conversational model.</span></span> <span data-ttu-id="13a29-133">In anderen Worten handelt es sich bei der Unterhaltung um eine Liste von Dingen, wie beispielsweise Arbeitsaufgaben mit drei abgelagerten Elementen oder um eine einzelne Sache wie eine spec.</span><span class="sxs-lookup"><span data-stu-id="13a29-133">In other words, the conversation is about a list of things, such as triaged work items, or a single thing, like a spec.</span></span>

<span data-ttu-id="13a29-134">Es gibt inhärente Navigationsprobleme mit der Hierarchie der tiefen Navigation in Thread-Unterhaltungen.</span><span class="sxs-lookup"><span data-stu-id="13a29-134">There are inherent navigational challenges with deep navigation hierarchy, within threaded conversations.</span></span> <span data-ttu-id="13a29-135">Für eine optimale Benutzerfreundlichkeit sollte die Registerkartennavigation auf ein Minimum reduziert und wie folgt gestaltet werden:</span><span class="sxs-lookup"><span data-stu-id="13a29-135">For the best user experience, your tab navigation should be kept to a minimum and be designed as follows:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="13a29-136">**Öffnet ein Aufgabenmodul wie eine einzelne Arbeitsaufgabe oder Entität**.</span><span class="sxs-lookup"><span data-stu-id="13a29-136">**Opens a task module such as an individual work item or entity**.</span></span> <span data-ttu-id="13a29-137">Dies schließt einen vollständigen Chat aus und ist die beste Option, um den Chat speziell für die Registerkarte und nicht für die unter Entitäten oder Bearbeitungs Erfahrungen zu halten.</span><span class="sxs-lookup"><span data-stu-id="13a29-137">This precludes chat entirely and is the best option to keep chat specifically about the tab and not the sub-entities or editing experiences.</span></span>
>* <span data-ttu-id="13a29-138">**Öffnet ein Pseudo Dialogfeld in einem IFRAME**.</span><span class="sxs-lookup"><span data-stu-id="13a29-138">**Opens a pseudo dialog in an iframe**.</span></span> <span data-ttu-id="13a29-139">Wenn Sie mit einem geschirmten Hintergrund verwendet wird, empfiehlt es sich, die hellere Farbe anstelle der Dunkelheit zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="13a29-139">If used with a screened background we recommend using the lighter color rather than the dark.</span></span> <span data-ttu-id="13a29-140">Die `app-gray-10 at 30%` Transparenz funktioniert gut.</span><span class="sxs-lookup"><span data-stu-id="13a29-140">The `app-gray-10 at 30%` transparency works well.</span></span>
>* <span data-ttu-id="13a29-141">**Öffnet eine Browser Seite**.</span><span class="sxs-lookup"><span data-stu-id="13a29-141">**Opens a browser page**.</span></span>

### <a name="personality"></a><span data-ttu-id="13a29-142">Persönlichkeit</span><span class="sxs-lookup"><span data-stu-id="13a29-142">Personality</span></span>

<span data-ttu-id="13a29-143">Ihr Tab-Canvas bietet eine großartige Gelegenheit, Ihre Benutzeroberfläche zu Branden.</span><span class="sxs-lookup"><span data-stu-id="13a29-143">Your tab canvas presents a great opportunity to brand your experience.</span></span> <span data-ttu-id="13a29-144">Ihr Logo ist ein wichtiger Bestandteil ihrer Identität und ihrer Verbindung mit ihren Benutzern., stellen Sie daher sicher, dass Sie es einschließen:</span><span class="sxs-lookup"><span data-stu-id="13a29-144">Your logo is an important part of your identity and connection with your users., so be sure to include it:</span></span>

> [!div class="checklist"]
>
>* <span data-ttu-id="13a29-145">Platzieren Sie Ihr Logo in der linken oder rechten Ecke oder am unteren Rand</span><span class="sxs-lookup"><span data-stu-id="13a29-145">Place your logo in the left or right corner or along the bottom edge</span></span>
> * <span data-ttu-id="13a29-146">Halten Sie Ihr Logo klein und unaufdringlich</span><span class="sxs-lookup"><span data-stu-id="13a29-146">Keep your logo small and unobtrusive</span></span>

<span data-ttu-id="13a29-147">Unter Einbeziehung ihrer eigenen Farben und Layouts Twill auch Hilfe bei der Kommunikation Persönlichkeit.</span><span class="sxs-lookup"><span data-stu-id="13a29-147">Incorporating your own colors and layouts twill also aid in communicating personality.</span></span>

> [!TIP]
> <span data-ttu-id="13a29-148">Arbeiten Sie mit unserem visuellen Stil, damit Ihr Dienst sich wie ein Teil von Microsoft Teams anfühlt.</span><span class="sxs-lookup"><span data-stu-id="13a29-148">Please work with our visual style so your service feels like a part of Teams.</span></span> <span data-ttu-id="13a29-149">*Siehe*zum Beispiel Microsoft [Teams-Farben](../../concepts/design/components/color.md)</span><span class="sxs-lookup"><span data-stu-id="13a29-149">*See*, for example [Teams Colors](../../concepts/design/components/color.md)</span></span>

---

## <a name="tab-layouts"></a><span data-ttu-id="13a29-150">Registerkarten Layouts</span><span class="sxs-lookup"><span data-stu-id="13a29-150">Tab layouts</span></span>

[!INCLUDE [Tab layouts](../../includes/design/tab-layouts.html)]

---

## <a name="types-of-tabs"></a><span data-ttu-id="13a29-151">Typen von Registerkarten</span><span class="sxs-lookup"><span data-stu-id="13a29-151">Types of tabs</span></span>

[!INCLUDE [Tab types](../../includes/design/tab-types.html)]

---

## <a name="configuration-page-height"></a><span data-ttu-id="13a29-152">Höhe der Konfigurationsseiten</span><span class="sxs-lookup"><span data-stu-id="13a29-152">Configuration page height</span></span>

>[!IMPORTANT]
><span data-ttu-id="13a29-153">Im September 2018 wurde die Höhe für die Registerkarten- [Konfigurationsseite](~/tabs/how-to/create-tab-pages/configuration-page.md) erhöht, während die Breite unverändert blieb.</span><span class="sxs-lookup"><span data-stu-id="13a29-153">In September 2018, the height for the tab [configuration page](~/tabs/how-to/create-tab-pages/configuration-page.md) was increased while the width remained unchanged.</span></span> <span data-ttu-id="13a29-154">Wenn Ihre APP für die ältere Größe ausgelegt ist, hat Ihre Registerkarten-Konfigurationsseite sehr viele vertikale Leerzeichen.</span><span class="sxs-lookup"><span data-stu-id="13a29-154">If your app is designed for the older size your tab configuration page will have a great deal of vertical whitespace.</span></span> <span data-ttu-id="13a29-155">Ältere Store-Apps, die von dieser Änderung ausgenommen sind, müssen sich nach der Aktualisierung an Microsoft wenden, um die neuen Dimensionen zu erfüllen.</span><span class="sxs-lookup"><span data-stu-id="13a29-155">Legacy store apps exempted from this change will need to contact Microsoft after updating to accommodate the new dimensions.</span></span>

<span data-ttu-id="13a29-156">Die Abmessungen der Registerkarten-Konfigurationsseite:</span><span class="sxs-lookup"><span data-stu-id="13a29-156">The dimensions of the tab configuration page:</span></span>


<img width="450px" title="Größen für Konfigurationsregisterkarten" src="~/assets/images/tabs/config-dialog-Contoso2.png" alt="sizes for config tabs" />


### <a name="guidelines-for-tab-configuration-page-format"></a><span data-ttu-id="13a29-158">Richtlinien für das Seitenformat der Registerkartenkonfiguration</span><span class="sxs-lookup"><span data-stu-id="13a29-158">Guidelines for tab configuration page format</span></span>

* <span data-ttu-id="13a29-159">Stützen Sie die minimale Höhe Ihres Inhaltsbereichs auf der Registerkarte Konfigurationsseite auf Grafikelementen mit fester Höhe.</span><span class="sxs-lookup"><span data-stu-id="13a29-159">Base the minimum height of your content area of your tab configuration page on fixed-height graphic elements.</span></span>
* <span data-ttu-id="13a29-160">Berechnen Sie den verfügbaren vertikalen Raum (die Höhe des Inhaltsbereichs auf der Konfigurationsseite) mithilfe von `window.innerHeight` .</span><span class="sxs-lookup"><span data-stu-id="13a29-160">Calculate available vertical space (the height of the content area in the configuration page) using `window.innerHeight`.</span></span> <span data-ttu-id="13a29-161">Dadurch wird die Größe der, in der sich die `<iframe>` Konfigurationsseite befindet, zurückgegeben, die sich in zukünftigen Versionen ändern kann.</span><span class="sxs-lookup"><span data-stu-id="13a29-161">This returns the size of the `<iframe>` in which your configuration page resides, which may change in future releases.</span></span> <span data-ttu-id="13a29-162">Wenn Sie diesen Wert verwenden, wird der Inhalt automatisch an zukünftige Änderungen angepasst.</span><span class="sxs-lookup"><span data-stu-id="13a29-162">By using this value your content will adjust automatically to future changes.</span></span>
* <span data-ttu-id="13a29-163">Zuweisen von vertikalem Abstand zu den Elementen der Variablen Höhe minus was für die Elemente mit fester Höhe benötigt wird.</span><span class="sxs-lookup"><span data-stu-id="13a29-163">Allocate vertical space to the variable-height elements minus what's needed for the fixed-height elements.</span></span>
* <span data-ttu-id="13a29-164">Für den *Anmelde* Status vertikal und horizontal zentrieren Sie den Inhalt.</span><span class="sxs-lookup"><span data-stu-id="13a29-164">For the *login* state, vertically and horizontally center the content.</span></span>
* <span data-ttu-id="13a29-165">Wenn Sie ein Hintergrundbild wünschen, benötigen Sie ein neues Bild, das an den Bereich angepasst wird (bevorzugt), oder Sie können das gleiche Bild beibehalten und zwischen folgenden Themen wählen:</span><span class="sxs-lookup"><span data-stu-id="13a29-165">If you want a background image, you need either a new image, sized to fit the area (preferred), or you can keep the same image and choose between:</span></span>
  * <span data-ttu-id="13a29-166">Ausrichtung an der oberen linken Ecke.</span><span class="sxs-lookup"><span data-stu-id="13a29-166">aligning to the upper left hand corner.</span></span>
  * <span data-ttu-id="13a29-167">Skalieren des Bilds an die Größe</span><span class="sxs-lookup"><span data-stu-id="13a29-167">scaling the image to fit.</span></span>

<span data-ttu-id="13a29-168">Bei ordnungsgemäßer Größe sollte Ihre Registerkarten-Konfigurationsseite wie folgt aussehen:</span><span class="sxs-lookup"><span data-stu-id="13a29-168">When properly sized, your tab configuration page should look similar to this:</span></span>

<img width="450px" title="Neue Registerkarte "Konfiguration"" src="~/assets/images/tabs/config-dialog-Contoso.png" alt="new config tab"/>

## <a name="best-practices"></a><span data-ttu-id="13a29-170">Bewährte Methoden</span><span class="sxs-lookup"><span data-stu-id="13a29-170">Best practices</span></span>

### <a name="always-include-a-default-state"></a><span data-ttu-id="13a29-171">Immer einen Standardzustand einschließen</span><span class="sxs-lookup"><span data-stu-id="13a29-171">Always include a default state</span></span>

<span data-ttu-id="13a29-172">Schließen Sie einen Standardzustand ein, um das Einrichten von Registerkarten zu vereinfachen, auch wenn die Registerkarte konfigurierbar ist.</span><span class="sxs-lookup"><span data-stu-id="13a29-172">Include a default state to make tabs easy to set up even if your tab is configurable.</span></span>

### <a name="deep-linking"></a><span data-ttu-id="13a29-173">Deep-Verknüpfung</span><span class="sxs-lookup"><span data-stu-id="13a29-173">Deep linking</span></span>

<span data-ttu-id="13a29-174">Wann immer möglich, sollten Karten und Bots einen tiefen Link zu umfangreicheren Daten in einer gehosteten RegisterkarteErstellen. Beispielsweise kann eine Karte eine Zusammenfassung der Fehlerdaten anzeigen, aber durch Klicken darauf kann der gesamte Fehler in einer Registerkarte angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="13a29-174">Whenever possible, cards and bots should deep link to richer data in a hosted tab. For example, a card may show a summary of bug data, but clicking it can shows the entire bug in a tab.</span></span>

### <a name="naming"></a><span data-ttu-id="13a29-175">Benennungs</span><span class="sxs-lookup"><span data-stu-id="13a29-175">Naming</span></span>

<span data-ttu-id="13a29-176">In vielen Fällen wird der Name Ihrer APP zu einem großen Registerkartennamen.</span><span class="sxs-lookup"><span data-stu-id="13a29-176">In many cases, the name of your app will make a great tab name.</span></span> <span data-ttu-id="13a29-177">Sie sollten Ihre Registerkarten jedoch auch entsprechend der von Ihnen bereitgestellten Funktionen benennen.</span><span class="sxs-lookup"><span data-stu-id="13a29-177">But, also consider naming your tabs according to the functionality they provide.</span></span>

## <a name="notifications-for-tabs"></a><span data-ttu-id="13a29-178">Benachrichtigungen für Registerkarten</span><span class="sxs-lookup"><span data-stu-id="13a29-178">Notifications for tabs</span></span>

<span data-ttu-id="13a29-179">Es gibt zwei Benachrichtigungs Modi für Änderungen an Registerkarten Inhalten:</span><span class="sxs-lookup"><span data-stu-id="13a29-179">There are two modes of notification for tab content changes:</span></span>

> [!div class="checklist"]
>
> * <span data-ttu-id="13a29-180">**Verwenden Sie die APP-API, um Benutzer über Änderungen zu informieren**.</span><span class="sxs-lookup"><span data-stu-id="13a29-180">**Use the app api to notify users of changes**.</span></span> <span data-ttu-id="13a29-181">Diese Meldung wird im Aktivitätsfeed des Benutzers und im Deep-Link zur Registerkarte angezeigt. *Weitere Informationen finden Sie unter*  [Erstellen von Deep Links zu Inhalten und Features in Microsoft Teams](../../concepts/build-and-test/deep-links.md?view=msteams-client-js-latest&preserve-view=true )</span><span class="sxs-lookup"><span data-stu-id="13a29-181">This message will show up in the user’s activity feed and deep link to the tab. *See*  [Create deep links to content and features in Microsoft Teams](../../concepts/build-and-test/deep-links.md?view=msteams-client-js-latest&preserve-view=true )</span></span>
> * <span data-ttu-id="13a29-182">**Verwenden Sie einen bot**.</span><span class="sxs-lookup"><span data-stu-id="13a29-182">**Use a bot**.</span></span> <span data-ttu-id="13a29-183">Diese Methode wird vor allem bevorzugt, wenn der Tab-Thread gezielt ist.</span><span class="sxs-lookup"><span data-stu-id="13a29-183">This method is preferred especially if the Tab thread is targeted.</span></span> <span data-ttu-id="13a29-184">Das Ergebnis ist, dass die Thread-Unterhaltung der Registerkarte als kürzlich aktiviert in die Ansicht verschoben wird.</span><span class="sxs-lookup"><span data-stu-id="13a29-184">The result will be that the tab’s threaded conversation will be moved into view as recently active.</span></span> <span data-ttu-id="13a29-185">Diese Methode ermöglicht auch eine gewisse Raffinesse in der Art und Weise, wie die Benachrichtigung gesendet wird.</span><span class="sxs-lookup"><span data-stu-id="13a29-185">This method also allows for some sophistication in how the notification is sent.</span></span>

  <span data-ttu-id="13a29-186">Durch das Senden einer Nachricht an einen Tab-Thread wird das Bewusstsein der Aktivität für alle Benutzer erhöht, ohne dass alle Personen explizit benachrichtigt werden.</span><span class="sxs-lookup"><span data-stu-id="13a29-186">Sending a message to a tab thread increases the awareness of activity to all users without explicitly notifying everyone.</span></span> <span data-ttu-id="13a29-187">Dies ist die Sensibilisierung ohne Rauschen.</span><span class="sxs-lookup"><span data-stu-id="13a29-187">This is awareness without noise.</span></span> <span data-ttu-id="13a29-188">Darüber hinaus `@mention`  wird bei bestimmten Benutzern die gleiche Benachrichtigung in Ihren Feed eingefügt, indem Sie Sie direkt mit dem Tab-Thread verbindet.</span><span class="sxs-lookup"><span data-stu-id="13a29-188">In addition, when you `@mention`  specific users the same notification will be placed in their feed, deep linking them to the tab thread directly.</span></span>
