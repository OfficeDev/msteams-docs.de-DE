---
title: Entwerfen effektiver Karten
description: Beschreibt die Entwurfsrichtlinien zum Erstellen von Karten.
keywords: Teams-Entwurfsrichtlinien Referenz-Framework-Karten anpassungsfähiges Leichtgewicht
ms.openlocfilehash: 33ee0b59a3a5a1490d6e2106f8532094ed852598
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674522"
---
# <a name="designing-effective-cards"></a><span data-ttu-id="db7c1-104">Entwerfen effektiver Karten</span><span class="sxs-lookup"><span data-stu-id="db7c1-104">Designing effective cards</span></span>

<span data-ttu-id="db7c1-105">Karten sind Aktionen-Snippets von Inhalten, die Sie einer Unterhaltung über einen bot, einen Konnektor oder eine APP hinzufügen können.</span><span class="sxs-lookup"><span data-stu-id="db7c1-105">Cards are actionable snippets of content that you can add to a conversation through a bot, a connector, or app.</span></span> <span data-ttu-id="db7c1-106">Mithilfe von Text, Grafiken und Schaltflächen können Sie mit Karten mit einer Zielgruppe kommunizieren.</span><span class="sxs-lookup"><span data-stu-id="db7c1-106">Using text, graphics, and buttons, cards allow you to communicate with an audience.</span></span>

<span data-ttu-id="db7c1-107">Mit unserem Karten Framework entfällt die Last des Designs einer voll funktionsfähigen UX.</span><span class="sxs-lookup"><span data-stu-id="db7c1-107">Our card framework eliminates the burden of designing a fully functional UX.</span></span> <span data-ttu-id="db7c1-108">Wir haben verschiedene standardmäßige Kartentypen entwickelt, die jeweils in unsere unterstützten Plattformen passen.</span><span class="sxs-lookup"><span data-stu-id="db7c1-108">We developed several standard card types and each one fits within our supported platforms.</span></span> <span data-ttu-id="db7c1-109">Dies bedeutet, dass für das Layout vollständig gesorgt ist, und Sie müssen keine unterschiedlichen Karten Iterationen auf Plattformen entwickeln.</span><span class="sxs-lookup"><span data-stu-id="db7c1-109">This means layout is completely taken care of, and you won’t need to develop different card iterations across platforms.</span></span> <span data-ttu-id="db7c1-110">Stattdessen können Sie sich auf das Einwählen von Inhalten konzentrieren.</span><span class="sxs-lookup"><span data-stu-id="db7c1-110">Instead, you can focus on dialing in your content.</span></span>

---

## <a name="guidelines"></a><span data-ttu-id="db7c1-111">Anleitungen</span><span class="sxs-lookup"><span data-stu-id="db7c1-111">Guidelines</span></span>

<span data-ttu-id="db7c1-112">Denken Sie an eine Karte als Antwort auf eine Benutzerfrage oder eine Einstellung.</span><span class="sxs-lookup"><span data-stu-id="db7c1-112">Think of a card as a response to a user question or a setting.</span></span> <span data-ttu-id="db7c1-113">Eine Karte kann auf eine direkte Frage (beispielsweise "wie viele geöffnete Fehler ich habe?") oder auf eine Bedingung (wie "eine Liste mit meinen geöffneten Fehlern an 9 Uhr täglich senden") Antworten.</span><span class="sxs-lookup"><span data-stu-id="db7c1-113">A card can respond to a direct question (like, “How many open bugs do I have?”) or to a condition (like, “Send a list of my open bugs at 9 am every day”).</span></span>

> [!TIP]
> <span data-ttu-id="db7c1-114">Die Verwendung eines unserer Standardkarten Typen bedeutet, dass Sie bereits wissen, dass alle Ihre Antworten auf jeder unterstützten Plattform gut gerendert werden.</span><span class="sxs-lookup"><span data-stu-id="db7c1-114">Using one of our standard card types means you’ll already know that all your responses will render nicely across each supported platform.</span></span>

<span data-ttu-id="db7c1-115">Eine Karte kann eines der folgenden Elemente enthalten:</span><span class="sxs-lookup"><span data-stu-id="db7c1-115">A card could include any of the following elements:</span></span><br />

[!include[Card anatomy](~/includes/design/card-image-anatomy.html)]

1. <span data-ttu-id="db7c1-116">**Umschlagtext**: am besten für Chatnachrichten verwendet.</span><span class="sxs-lookup"><span data-stu-id="db7c1-116">**Envelope text**: Best used for chat messages.</span></span> <span data-ttu-id="db7c1-117">Wenn Sie beispielsweise einen bot sagen möchten: "hier ist, was ich gefunden habe!"</span><span class="sxs-lookup"><span data-stu-id="db7c1-117">For example, if you want a bot to say: “Here’s what I found!”</span></span> <span data-ttu-id="db7c1-118">oder "time for your 1:00 News Digest" ist, wird diese Nachricht am besten im Umschlagtext angezeigt.</span><span class="sxs-lookup"><span data-stu-id="db7c1-118">or “Time for your 1:00 news digest”, that message is best displayed in envelope text.</span></span>

   <span data-ttu-id="db7c1-119">Briefumschlag Text ist eine großartige Möglichkeit, um eine kleine Persönlichkeit in ihren Dienst einzufügen – denken Sie daran, Sie relativ kurz zu halten.</span><span class="sxs-lookup"><span data-stu-id="db7c1-119">Envelope text is a great way to inject a little personality into your service—just remember to keep it relatively short.</span></span>

2. <span data-ttu-id="db7c1-120">**Title**: Ihr Titel ist immer der größte Text auf Ihrer Karte.</span><span class="sxs-lookup"><span data-stu-id="db7c1-120">**Title**: Your title will always be the largest text in your card.</span></span> <span data-ttu-id="db7c1-121">Es dient auch als "Hook", also versuchen Sie, den Titel kurz zu halten, einprägsam und einfach zu scannen.</span><span class="sxs-lookup"><span data-stu-id="db7c1-121">It also serves as your “hook”, so try to keep the title short, memorable, and easy to scan.</span></span>

3. <span data-ttu-id="db7c1-122">Unter **Titel**: am besten für Attribution, Slogans oder als sekundäre Direktive verwendet.</span><span class="sxs-lookup"><span data-stu-id="db7c1-122">**Subtitle**: Best used for attribution, taglines, or as a secondary directive.</span></span> <span data-ttu-id="db7c1-123">Diese Komponente wird direkt unter Ihrem Titel angezeigt.</span><span class="sxs-lookup"><span data-stu-id="db7c1-123">This component appears just below your title.</span></span>

4. <span data-ttu-id="db7c1-124">**Bild**: Bilder skalieren, um ihren Container anzupassen.</span><span class="sxs-lookup"><span data-stu-id="db7c1-124">**Image**: Images scale to fit their container.</span></span> <span data-ttu-id="db7c1-125">Hero Cards haben eine maximale Breite von 420px, Miniaturansichten haben eine maximale Breite von 100px, und Listenansichten ermöglichen nur Bund im Desktopmodus.</span><span class="sxs-lookup"><span data-stu-id="db7c1-125">Hero cards have a max width of 420px, thumbnails have a max width of 100px, and list views only allow for 32px in desktop mode.</span></span>

5. <span data-ttu-id="db7c1-126">**Text**: am besten für nur-Text im Textkörper Ihrer Karte verwendet.</span><span class="sxs-lookup"><span data-stu-id="db7c1-126">**Text**: Best used for plain text in the body of your card.</span></span> <span data-ttu-id="db7c1-127">Die maximale Länge hängt vom ausgewählten Kartentyp ab.</span><span class="sxs-lookup"><span data-stu-id="db7c1-127">Your max length depends on the card type you’ve selected.</span></span>

6. <span data-ttu-id="db7c1-128">**Schaltflächen**: wird am besten zum Öffnen von Webseiten, Registerkarten oder zusätzlichen Chat Inhalten verwendet.</span><span class="sxs-lookup"><span data-stu-id="db7c1-128">**Buttons**: Best used to open web pages, tabs, or additional chat content.</span></span> <span data-ttu-id="db7c1-129">Achten Sie darauf, den Text der Schaltfläche kurz zu halten.</span><span class="sxs-lookup"><span data-stu-id="db7c1-129">Make sure to keep your button text short and to the point.</span></span>

   <span data-ttu-id="db7c1-130">Sie können bis zu 6 Schaltflächen pro Karte einbeziehen, aber wir empfehlen Ihnen hier eine "Less is more"-Philosophie.</span><span class="sxs-lookup"><span data-stu-id="db7c1-130">You can include up to 6 buttons per card, but we’d recommend following a ‘less is more’ philosophy here.</span></span>

7. <span data-ttu-id="db7c1-131">**Tippen**Sie auf Region: Dies ist der klickable Bereich Ihrer Karte.</span><span class="sxs-lookup"><span data-stu-id="db7c1-131">**Tap region**: This is the clickable region of your card.</span></span> <span data-ttu-id="db7c1-132">Die meisten Benutzer möchten automatisch auf Bilder klicken, damit Sie wissen, wo Sie tippen oder klicken sollten.</span><span class="sxs-lookup"><span data-stu-id="db7c1-132">Most users will want to click on images automatically, so try and craft your text so they know where they should tap or click.</span></span>

> [!TIP]
> <span data-ttu-id="db7c1-133">Es ist nicht erforderlich, jedes Element in jede von Ihnen erstellte Karte einzubeziehen.</span><span class="sxs-lookup"><span data-stu-id="db7c1-133">There’s no need to include every element in each card you create.</span></span> <span data-ttu-id="db7c1-134">Lassen Sie Ihre Inhalte ihre Elemente diktieren.</span><span class="sxs-lookup"><span data-stu-id="db7c1-134">Let your content dictate your elements.</span></span>

---

## <a name="types-of-cards"></a><span data-ttu-id="db7c1-135">Kartentypen</span><span class="sxs-lookup"><span data-stu-id="db7c1-135">Types of cards</span></span>

### <a name="hero"></a><span data-ttu-id="db7c1-136">Hero</span><span class="sxs-lookup"><span data-stu-id="db7c1-136">Hero</span></span>

<span data-ttu-id="db7c1-137">Unsere größte Karte.</span><span class="sxs-lookup"><span data-stu-id="db7c1-137">Our largest card.</span></span> <span data-ttu-id="db7c1-138">Eignet sich am besten für Artikel, lange Beschreibungen oder Szenarien, in denen das Bild den größten Teil der Geschichte erzählt.</span><span class="sxs-lookup"><span data-stu-id="db7c1-138">Best used for articles, long descriptions, or scenarios where your image is telling most of the story.</span></span>

[!include[Card anatomy](~/includes/design/card-image-hero.html)]

### <a name="thumbnail"></a><span data-ttu-id="db7c1-139">Minaturansicht</span><span class="sxs-lookup"><span data-stu-id="db7c1-139">Thumbnail</span></span>

<span data-ttu-id="db7c1-140">Kurz und bündig.</span><span class="sxs-lookup"><span data-stu-id="db7c1-140">Short and sweet.</span></span> <span data-ttu-id="db7c1-141">Diese Karten sind ideal für kurze Antworten, oder wenn Sie mehrere Karten gleichzeitig zurückgeben möchten, sodass der Benutzer aus einer Reihe von Optionen auswählen kann.</span><span class="sxs-lookup"><span data-stu-id="db7c1-141">These cards are ideal for short answers, or if you want to return several cards at once so the user can choose from a bunch of options.</span></span> <span data-ttu-id="db7c1-142">Wir glauben, dass dies eine großartige Möglichkeit zum Deep Link zu einer anderen Registerkarte oder einem Webdienst ist.</span><span class="sxs-lookup"><span data-stu-id="db7c1-142">We think these are a great way to deep link to another tab or a web service.</span></span>

[!include[Card anatomy](~/includes/design/card-image-thumbnail.html)]

### <a name="sign-in"></a><span data-ttu-id="db7c1-143">Anmelden</span><span class="sxs-lookup"><span data-stu-id="db7c1-143">Sign in</span></span>

<span data-ttu-id="db7c1-144">Bei einigen Diensten müssen sich Benutzer unabhängig von unserer Authentifizierung anmelden.</span><span class="sxs-lookup"><span data-stu-id="db7c1-144">Some services require users to sign in independently of our authentication.</span></span> <span data-ttu-id="db7c1-145">In diesem Fall würden Sie eine Anmeldekarte vorlegen, bevor der Benutzer eine Verbindung mit Ihrem Dienst herstellen kann.</span><span class="sxs-lookup"><span data-stu-id="db7c1-145">In that event, you would present a sign-in card before the user can connect to your service.</span></span>

[!include[Card anatomy](~/includes/design/card-image-signin.html)]

> [!TIP]
> <span data-ttu-id="db7c1-146">Begrenzen Sie das Vorkommen einer zusätzlichen Anmeldekarte, da Sie eine erhebliche Geschwindigkeits Beule für neue Benutzer darstellen.</span><span class="sxs-lookup"><span data-stu-id="db7c1-146">Limit the occurrences of an additional sign-in card since they pose a significant speed bump for new users.</span></span>

---

## <a name="card-collections"></a><span data-ttu-id="db7c1-147">Kartensammlungen</span><span class="sxs-lookup"><span data-stu-id="db7c1-147">Card collections</span></span>

<span data-ttu-id="db7c1-148">Wir haben auch standardmäßige Kartentypen, die am besten verwendet werden, wenn Sie mehrere Teile des inhaltsgleich zeitig oder in schneller Folge präsentieren möchten.</span><span class="sxs-lookup"><span data-stu-id="db7c1-148">We also have standard card types that are best used when you want to present several pieces of content at once or in quick succession.</span></span> <span data-ttu-id="db7c1-149">Zu diesem Zweck haben wir ein Karussell, einen Digest, eine Liste und eine "Bubble Merge".</span><span class="sxs-lookup"><span data-stu-id="db7c1-149">For that purpose, we have a carousel, a digest, a list, and what we call a ‘bubble merge’.</span></span>

### <a name="carousel"></a><span data-ttu-id="db7c1-150">Karussell</span><span class="sxs-lookup"><span data-stu-id="db7c1-150">Carousel</span></span>

<span data-ttu-id="db7c1-151">Am besten geeignet für Artikel, Shopping und Browsen durch Karten.</span><span class="sxs-lookup"><span data-stu-id="db7c1-151">Best used for articles, shopping, and browsing through cards.</span></span>

[!include[Card anatomy](~/includes/design/card-image-carousel.html)]

> [!TIP]
> <span data-ttu-id="db7c1-152">Das Karussell ist die maximale Höhe der größten Karte.</span><span class="sxs-lookup"><span data-stu-id="db7c1-152">The carousel will be the max height of your largest card.</span></span> <span data-ttu-id="db7c1-153">Es wird empfohlen, die gleichen Kartentypen und Inhaltsfelder zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="db7c1-153">We recommend using the same card type and content fields throughout.</span></span>

### <a name="digest"></a><span data-ttu-id="db7c1-154">Digest</span><span class="sxs-lookup"><span data-stu-id="db7c1-154">Digest</span></span>

<span data-ttu-id="db7c1-155">Eignet sich am besten für Nachrichten, Digests und immer dann, wenn der Benutzer mehrere Karten gleichzeitig anzeigen soll.</span><span class="sxs-lookup"><span data-stu-id="db7c1-155">Best used for news, digests, and whenever you want the user to view multiple cards at once.</span></span> <span data-ttu-id="db7c1-156">Wir empfehlen die Verwendung von Miniatur Ansichtskarten für Digest.</span><span class="sxs-lookup"><span data-stu-id="db7c1-156">We recommend using thumbnail cards for digests.</span></span>

[!include[Card anatomy](~/includes/design/card-image-digest.html)]

### <a name="lists"></a><span data-ttu-id="db7c1-157">Listen</span><span class="sxs-lookup"><span data-stu-id="db7c1-157">Lists</span></span>

<span data-ttu-id="db7c1-158">Listen stellen eine hervorragende Möglichkeit dar, einen scannable-Objektsatz in einem der folgenden Szenarien darzustellen.</span><span class="sxs-lookup"><span data-stu-id="db7c1-158">Lists are a great way to present a scannable set of objects in a “pick one of these” scenario.</span></span> <span data-ttu-id="db7c1-159">Listen werden am besten für Elemente verwendet, die nicht viele Erklärungen benötigen.</span><span class="sxs-lookup"><span data-stu-id="db7c1-159">Lists are best used for items that don’t need a lot of explanation.</span></span>

[!include[Card anatomy](~/includes/design/card-image-list.html)]

### <a name="bubble-merge"></a><span data-ttu-id="db7c1-160">Blasen Zusammenführung</span><span class="sxs-lookup"><span data-stu-id="db7c1-160">Bubble merge</span></span>

<span data-ttu-id="db7c1-161">Einige interessante Effekte können erzielt werden, indem ein Held und mehrere Miniaturansichten schnell hintereinander gesendet werden.</span><span class="sxs-lookup"><span data-stu-id="db7c1-161">Some interesting effects can be achieved by sending one hero and several thumbnails in quick succession.</span></span> <span data-ttu-id="db7c1-162">Diese Vorgehensweise wird empfohlen, wenn Sie ein Hauptergebnis bereitstellen möchten, aber einige weitere verwandte Elemente enthalten sollen.</span><span class="sxs-lookup"><span data-stu-id="db7c1-162">We recommend this approach when you want to serve a main result but include a few more related items.</span></span>

[!include[Card anatomy](~/includes/design/card-image-bubble-merge.html)]

---

## <a name="best-practices"></a><span data-ttu-id="db7c1-163">Bewährte Methoden</span><span class="sxs-lookup"><span data-stu-id="db7c1-163">Best practices</span></span>

### <a name="keep-the-noise-down"></a><span data-ttu-id="db7c1-164">Rauschen nach unten aufbewahren</span><span class="sxs-lookup"><span data-stu-id="db7c1-164">Keep the noise down</span></span>

<span data-ttu-id="db7c1-165">Es ist ganz einfach, mehrere Karten in eine Unterhaltung zu senden, aber sobald die Karten aus dem Blickfeld geraten, werden Sie nicht mehr so nützlich.</span><span class="sxs-lookup"><span data-stu-id="db7c1-165">It’s easy to send multiple cards into a conversation, but once cards scroll out of view, they become less useful.</span></span> <span data-ttu-id="db7c1-166">Versuchen Sie, sich auf das Wesentliche zu beschränken.</span><span class="sxs-lookup"><span data-stu-id="db7c1-166">Try to limit yourself to the essentials.</span></span> <span data-ttu-id="db7c1-167">Dies gilt insbesondere für einen Kanal, in dem Benutzer eine geringere Toleranz für das als "Rauschen" wahrgenommene haben.</span><span class="sxs-lookup"><span data-stu-id="db7c1-167">This is especially true in a channel where users have less tolerance for what they perceive as “noise”.</span></span>

### <a name="test-on-mobile"></a><span data-ttu-id="db7c1-168">Test auf mobilen Geräten</span><span class="sxs-lookup"><span data-stu-id="db7c1-168">Test on mobile</span></span>

<span data-ttu-id="db7c1-169">Mobile Umgebungen sind Platz-und Bandbreitenabhängig, daher sollten Sie vorsichtig sein, wenn Sie überdimensionierte Bilder und große Datensätze in Listen und Karussells einschließen.</span><span class="sxs-lookup"><span data-stu-id="db7c1-169">Mobile environments are space- and bandwidth-constrained, so be cautious about including oversized images and large data sets in lists and carousels.</span></span> <span data-ttu-id="db7c1-170">Außerdem werden Titel breiten und Textlängen auf dem Mobiltelefon abgeschnitten, sodass dies eine andere Sache ist, die Sie im Auge behalten.</span><span class="sxs-lookup"><span data-stu-id="db7c1-170">Also, title widths and text lengths will truncate on mobile, so that’s another thing to keep an eye on.</span></span>

### <a name="check-your-graphics"></a><span data-ttu-id="db7c1-171">Überprüfen der Grafiken</span><span class="sxs-lookup"><span data-stu-id="db7c1-171">Check your graphics</span></span>

<span data-ttu-id="db7c1-172">Grafiken werden skaliert, daher sollten Sie Sie auf allen Plattformen in einer Vorschau anzeigen.</span><span class="sxs-lookup"><span data-stu-id="db7c1-172">Graphics are going to scale, so be sure to preview them on all platforms.</span></span>

### <a name="avoid-including-text-in-a-graphic"></a><span data-ttu-id="db7c1-173">Vermeiden des Einbindens von Text in eine Grafik</span><span class="sxs-lookup"><span data-stu-id="db7c1-173">Avoid including text in a graphic</span></span>

<span data-ttu-id="db7c1-174">Alle Elemente, die von einem Benutzer gelesen werden müssen, sollten in ein Textfeld eingeschlossen werden.</span><span class="sxs-lookup"><span data-stu-id="db7c1-174">Anything that needs to be read by a user should be included in a text field.</span></span> <span data-ttu-id="db7c1-175">Wenn ein Bild dynamisch skaliert wird, kann jeder Text, den Sie einer Grafik hinzufügen, nicht mehr verständlich sein.</span><span class="sxs-lookup"><span data-stu-id="db7c1-175">Once an image is dynamically scaled, any text you add to a graphic may become unintelligible.</span></span>

### <a name="use-mentions-if-you-want-the-attention-of-specific-users"></a><span data-ttu-id="db7c1-176">Verwenden von Erwähnungen, wenn Sie die Aufmerksamkeit bestimmter Benutzer wünschen</span><span class="sxs-lookup"><span data-stu-id="db7c1-176">Use mentions if you want the attention of specific users</span></span>

> [!NOTE]
> <span data-ttu-id="db7c1-177">Die Erwähnung der Unterstützung in Cards wird derzeit nur in der [Entwicklervorschau](~/resources/dev-preview/developer-preview-intro.md) unterstützt.</span><span class="sxs-lookup"><span data-stu-id="db7c1-177">Mention support in cards is currently supported in [Developer Preview](~/resources/dev-preview/developer-preview-intro.md) only.</span></span>

<span data-ttu-id="db7c1-178">Erwähnungen sind eine hervorragende Möglichkeit, bestimmte Benutzer in einem Team-oder Gruppenchat zu benachrichtigen.</span><span class="sxs-lookup"><span data-stu-id="db7c1-178">Mentions are a great way to notify specific users in a Team or group chat.</span></span> <span data-ttu-id="db7c1-179">Sie können eine Erwähnung in der Karte in Szenarien wie, eine Aufgabe, die einem Benutzer zugewiesen ist oder Lob an einen Teamkollegen hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="db7c1-179">You can include a mention in card in scenarios like, a task thats assigned to a user or giving Kudos to a teammate.</span></span> <span data-ttu-id="db7c1-180">Hier erfahren Sie, wie Sie in Karten auf der [Seite Kartenformatierung](~/task-modules-and-cards/cards/cards-format.md)Erwähnungen hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="db7c1-180">Learn how to include mentions in cards in the [card formatting page](~/task-modules-and-cards/cards/cards-format.md).</span></span> 
