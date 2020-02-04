---
title: Entwurfsrichtlinien für Bots
description: Beschreibt die Richtlinien zum Erstellen von Bots
keywords: Teams-Entwurfsrichtlinien Referenz Framework-Bots im Gespräch
ms.openlocfilehash: f59a1e9c280f27567692b4d10341db79d05c3464
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674497"
---
# <a name="start-talking-with-bots"></a><span data-ttu-id="18136-104">Gespräch mit Bots beginnen</span><span class="sxs-lookup"><span data-stu-id="18136-104">Start talking with bots</span></span>

<span data-ttu-id="18136-105">Bots sind Unterhaltungs-apps, die eine enge oder bestimmte Gruppe von Aufgaben ausführen.</span><span class="sxs-lookup"><span data-stu-id="18136-105">Bots are conversational apps that perform a narrow or specific set of tasks.</span></span> <span data-ttu-id="18136-106">Sie bieten Ihnen die Möglichkeit, mit Benutzern zu kommunizieren, auf Ihre Fragen zu Antworten und Sie proaktiv über Änderungen zu informieren.</span><span class="sxs-lookup"><span data-stu-id="18136-106">They give you an opportunity to communicate with users, respond to their questions, and proactively notify them about changes.</span></span> <span data-ttu-id="18136-107">Sie sind eine großartige Möglichkeit, um Sie zu erreichen.</span><span class="sxs-lookup"><span data-stu-id="18136-107">They’re a great way to reach out.</span></span>

---

## <a name="guidelines"></a><span data-ttu-id="18136-108">Anleitungen</span><span class="sxs-lookup"><span data-stu-id="18136-108">Guidelines</span></span>

### <a name="avatars"></a><span data-ttu-id="18136-109">Avatars</span><span class="sxs-lookup"><span data-stu-id="18136-109">Avatars</span></span>

<span data-ttu-id="18136-110">Bot-Avatare in Teams sind wie Sechsecke geformt, sodass die Benutzer schnell erkennen können, dass Sie mit einem bot anstatt mit einer Person sprechen.</span><span class="sxs-lookup"><span data-stu-id="18136-110">Bot avatars in Teams are shaped like hexagons so people can quickly tell that they’re talking to a bot instead of a person.</span></span> <span data-ttu-id="18136-111">Sie übermitteln Ihren Avatar als Quadrat, und wir beschneiden ihn für Sie.</span><span class="sxs-lookup"><span data-stu-id="18136-111">You’ll submit your avatar as a square and we’ll crop it for you.</span></span> <span data-ttu-id="18136-112">Wenn es um Avatare geht, empfehlen wir Ihnen, ihre Lesbarkeit von 2 m entfernt und einen höheren Kontrast zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="18136-112">When it comes to avatars, we recommend making yours legible from 2 feet away and using a higher contrast.</span></span>

[!include[Avatar image](~/includes/design/bot-avatar-image.html)]

### <a name="buttons"></a><span data-ttu-id="18136-113">Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="18136-113">Buttons</span></span>

<span data-ttu-id="18136-114">Wir unterstützen bis zu sechs Schaltflächen pro Karte.</span><span class="sxs-lookup"><span data-stu-id="18136-114">We support up to six buttons per card.</span></span> <span data-ttu-id="18136-115">Seien Sie beim Schreiben von Schaltflächentext prägnant, und denken Sie daran, dass die meisten Schaltflächen nur die Aufgabe behandeln sollten, die Ihnen zur Verfügung steht.</span><span class="sxs-lookup"><span data-stu-id="18136-115">Be concise when writing button text, and keep in mind that most buttons should only address the task at hand.</span></span>

### <a name="graphics"></a><span data-ttu-id="18136-116">Grafik</span><span class="sxs-lookup"><span data-stu-id="18136-116">Graphics</span></span>

<span data-ttu-id="18136-117">Grafiken sind eine gute Möglichkeit, eine Geschichte zu erzählen, aber nicht alle bot-Unterhaltungen benötigen Grafiken, also verwenden Sie Sie für maximale Auswirkung.</span><span class="sxs-lookup"><span data-stu-id="18136-117">Graphics are a good way to tell a story, but not all bot conversations require graphics, so use them for maximum impact.</span></span>

### <a name="responding-to-users-and-failing-gracefully"></a><span data-ttu-id="18136-118">Reagieren auf Benutzer und fehlgeschlagene ordnungsgemäße</span><span class="sxs-lookup"><span data-stu-id="18136-118">Responding to users and failing gracefully</span></span>

<span data-ttu-id="18136-119">Ihr bot sollte auch auf Dinge wie "Hi", "Help" und "Thanks" reagieren können, während häufige Rechtschreibfehler und Colloquialisms berücksichtigt werden.</span><span class="sxs-lookup"><span data-stu-id="18136-119">Your bot should also be able to respond to things like 'Hi', 'Help', and 'Thanks' while taking common misspellings and colloquialisms into account.</span></span> <span data-ttu-id="18136-120">Zum Beispiel:</span><span class="sxs-lookup"><span data-stu-id="18136-120">For example:</span></span>

#### <a name="x2713-hello"></a><span data-ttu-id="18136-121">&#x2713; Hallo</span><span class="sxs-lookup"><span data-stu-id="18136-121">&#x2713; Hello</span></span>

<span data-ttu-id="18136-122">`Hi` `how are you` `howdy`</span><span class="sxs-lookup"><span data-stu-id="18136-122">`Hi` `how are you` `howdy`</span></span>

#### <a name="x2713-help"></a><span data-ttu-id="18136-123">&#x2713; Hilfe</span><span class="sxs-lookup"><span data-stu-id="18136-123">&#x2713; Help</span></span>

<span data-ttu-id="18136-124">`What do you do?` `How does this work?` `What the heck?`</span><span class="sxs-lookup"><span data-stu-id="18136-124">`What do you do?` `How does this work?` `What the heck?`</span></span>

#### <a name="x2713-thanks"></a><span data-ttu-id="18136-125">&#x2713; Dank</span><span class="sxs-lookup"><span data-stu-id="18136-125">&#x2713; Thanks</span></span>

<span data-ttu-id="18136-126">`Thank you` `thankyou` `thx`</span><span class="sxs-lookup"><span data-stu-id="18136-126">`Thank you` `thankyou` `thx`</span></span>

<span data-ttu-id="18136-127">Ihr bot sollte in der Lage sein, die folgenden Arten von Abfragen und Eingaben zu verarbeiten:</span><span class="sxs-lookup"><span data-stu-id="18136-127">Your bot should be able to handle the following types of queries and inputs:</span></span>

* <span data-ttu-id="18136-128">**Erkannte Fragen**: Dies sind die "Best Case"-Fragen, die Sie von Benutzern erwarten.</span><span class="sxs-lookup"><span data-stu-id="18136-128">**Recognized questions**: These are the “best case scenario” questions you’d anticipate from users.</span></span>
* <span data-ttu-id="18136-129">**Erkannte nicht-Fragen**: Abfragen über nicht unterstützte Funktionen, zufällige Informationen oder wenn jemand bei Ihrem bot fluchen möchte.</span><span class="sxs-lookup"><span data-stu-id="18136-129">**Recognized non-questions**: Queries about unsupported functionality, random pieces of information, or when someone wants to curse at your bot.</span></span>
* <span data-ttu-id="18136-130">**Unbekannte Fragen**: unverständliche Eingaben (d. h., Kauderwelsch).</span><span class="sxs-lookup"><span data-stu-id="18136-130">**Unrecognized questions**: Unintelligible inputs (i.e., gibberish).</span></span>

<span data-ttu-id="18136-131">Beispiele für bot-Persönlichkeits-und-Antworttypen:</span><span class="sxs-lookup"><span data-stu-id="18136-131">Examples of bot personality and response types:</span></span>

[!include[Bot responses](~/includes/design/bot-responses-table.html)]

> [!TIP]
> <span data-ttu-id="18136-132">Wenn Sie Ihr bot-Skript schreiben, Fragen Sie sich selbst: "wird mein Unternehmen beschämt, wenn eine Antwort auf dem Bildschirm aufgezeichnet und freigegeben wird?"</span><span class="sxs-lookup"><span data-stu-id="18136-132">When writing your bot script, ask yourself: “Will my company be embarrassed if a response is screen captured and shared?”</span></span>

### <a name="understanding-what-users-are-trying-to-say"></a><span data-ttu-id="18136-133">Verstehen, was Benutzer zu sagen versuchen</span><span class="sxs-lookup"><span data-stu-id="18136-133">Understanding what users are trying to say</span></span>

#### <a name="use-a-thesaurus-for-synonyms"></a><span data-ttu-id="18136-134">Verwenden eines Thesaurus für Synonyme</span><span class="sxs-lookup"><span data-stu-id="18136-134">Use a thesaurus for synonyms</span></span>

<span data-ttu-id="18136-135">Verwenden Sie bei Brainstorming-Varianten einen Thesaurus, und rufen Sie Personen aus so vielen verschiedenen Hintergründen ab, die Sie bei der Generierung unterschiedlicher Interpretationen der einzelnen Abfragen unterstützen.</span><span class="sxs-lookup"><span data-stu-id="18136-135">When brainstorming variants, use a thesaurus and get people from as many different backgrounds as possible to help you generate different interpretations of each query.</span></span>

#### <a name="make-use-of-telemetry-and-interviews"></a><span data-ttu-id="18136-136">Nutzen von Telemetrie und Interviews</span><span class="sxs-lookup"><span data-stu-id="18136-136">Make use of telemetry and interviews</span></span>

<span data-ttu-id="18136-137">Finden Sie heraus, was Benutzer sagen und was ihre Absicht war, als Sie Ihren bot Abfragen.</span><span class="sxs-lookup"><span data-stu-id="18136-137">Find out what users are saying and what was their intent when querying your bot.</span></span> <span data-ttu-id="18136-138">Dies wird ein fortlaufender Prozess, wenn Sie Benutzer an unterschiedlichen Standorten und Unternehmenstypen erhalten.</span><span class="sxs-lookup"><span data-stu-id="18136-138">This will be an ongoing process as you get users in different locations and types of companies.</span></span> <span data-ttu-id="18136-139">Sie können die Spracherkennung und die beabsichtigte Zuordnung mit dem Sprachverständnis Intelligent Service ([Luis](/azure/cognitive-services/luis/what-is-luis)) optimieren.</span><span class="sxs-lookup"><span data-stu-id="18136-139">You can fine-tune language recognition and intent mapping with Language Understanding Intelligent Service ([LUIS](/azure/cognitive-services/luis/what-is-luis)).</span></span>

### <a name="how-often-should-you-use-your-bot-to-reach-out-to-a-user"></a><span data-ttu-id="18136-140">Wie oft sollten Sie Ihren bot verwenden, um einen Benutzer zu erreichen?</span><span class="sxs-lookup"><span data-stu-id="18136-140">How often should you use your bot to reach out to a user?</span></span>

#### <a name="x2713-when-a-state-has-changed"></a><span data-ttu-id="18136-141">&#x2713;, wenn sich ein Status geändert hat</span><span class="sxs-lookup"><span data-stu-id="18136-141">&#x2713; When a state has changed</span></span>

<span data-ttu-id="18136-142">Beispiel: Wenn eine Zuordnung als abgeschlossen markiert ist, wenn sich ein Fehler ändert, wenn neue soziale Medien verfügbar sind oder wenn eine Umfrage abgeschlossen wurde.</span><span class="sxs-lookup"><span data-stu-id="18136-142">For example, if an assignment is marked as complete, when a bug changes, when new social media is available, or when a poll has been completed.</span></span>

#### <a name="x2713-when-the-timing-is-right"></a><span data-ttu-id="18136-143">&#x2713;, wenn das Timing stimmt</span><span class="sxs-lookup"><span data-stu-id="18136-143">&#x2713; When the timing is right</span></span>

<span data-ttu-id="18136-144">Ihr Bot kann wie eine tägliche Zusammenfassung handeln und eine Benachrichtigung an den Benutzer oder Kanal mit einer bestimmten Frequenz senden.</span><span class="sxs-lookup"><span data-stu-id="18136-144">Your bot can act like a daily digest, sending a notification to the user or channel at a specific frequency.</span></span>

<span data-ttu-id="18136-145">Lassen Sie den Benutzer im Steuerelement.</span><span class="sxs-lookup"><span data-stu-id="18136-145">Leave the user in control.</span></span> <span data-ttu-id="18136-146">Stellen Sie Benachrichtigungseinstellungen bereit, die Häufigkeit und Priorität umfassen.</span><span class="sxs-lookup"><span data-stu-id="18136-146">Provide notification settings that include frequency and priority.</span></span>

[!include[Bot notification](~/includes/design/bot-notification-image.html)]

---

## <a name="using-tabs"></a><span data-ttu-id="18136-147">Verwenden von Registerkarten</span><span class="sxs-lookup"><span data-stu-id="18136-147">Using tabs</span></span>

<span data-ttu-id="18136-148">Tabs machen Ihren bot viel funktionaler.</span><span class="sxs-lookup"><span data-stu-id="18136-148">Tabs make your bot much more functional.</span></span> <span data-ttu-id="18136-149">Mit Registerkarten können Sie Folgendes erstellen:</span><span class="sxs-lookup"><span data-stu-id="18136-149">With tabs, you can create the following:</span></span>

### <a name="x2713-a-place-to-host-standing-queries"></a><span data-ttu-id="18136-150">&#x2713; einer Stelle zum Hosten von ständigen Abfragen</span><span class="sxs-lookup"><span data-stu-id="18136-150">&#x2713; A place to host standing queries</span></span>

<span data-ttu-id="18136-151">In persönlichen Gesprächen zwischen einem bot und einer einzelnen Person können benutzerspezifische Informationen und Listen in Registerkarten untergebracht werden.</span><span class="sxs-lookup"><span data-stu-id="18136-151">In personal conversations between a bot and a single person, tabs can house user-specific information and lists.</span></span> <span data-ttu-id="18136-152">Sie sind auch ein guter Ort, um bot-Antworten auf häufig gestellte Fragen (FAQs) zu verwalten, sodass Benutzer nicht weiter gefragt werden müssen.</span><span class="sxs-lookup"><span data-stu-id="18136-152">They’re also a good place to maintain bot responses to frequently-asked questions (FAQs) — so users don’t need to keep asking.</span></span>

### <a name="x2713-a-place-to-finish-a-conversation"></a><span data-ttu-id="18136-153">&#x2713; eine Stelle zum Abschließen einer Unterhaltung</span><span class="sxs-lookup"><span data-stu-id="18136-153">&#x2713; A place to finish a conversation</span></span>

<span data-ttu-id="18136-154">Sie können eine Verknüpfung mit einer Registerkarte von einer Karte herstellen.</span><span class="sxs-lookup"><span data-stu-id="18136-154">You can link to a tab from a card.</span></span> <span data-ttu-id="18136-155">Wenn Ihr bot eine Antwort bereitstellt, die einige weitere Schritte erfordert, kann er eine Verknüpfung mit einer Registerkarte herstellen, um die Aufgabe oder den Ablauf abzuschließen.</span><span class="sxs-lookup"><span data-stu-id="18136-155">If your bot provides an answer that requires a few more steps, it can link to a tab to complete the task or flow.</span></span>

### <a name="x2713-a-place-to-provide-some-help"></a><span data-ttu-id="18136-156">&#x2713; ein Ort, um Hilfe zu leisten</span><span class="sxs-lookup"><span data-stu-id="18136-156">&#x2713; A place to provide some help</span></span>

<span data-ttu-id="18136-157">Fügen Sie eine Registerkarte hinzu, mit der Benutzer über die Kommunikation mit Ihrem bot informieren.</span><span class="sxs-lookup"><span data-stu-id="18136-157">Add a tab that educates users about how to communicate with your bot.</span></span> <span data-ttu-id="18136-158">Sie können einen Kontext für die Funktionen oder FAQs bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="18136-158">You can provide some context for what it does or FAQs.</span></span>

![Bereitstellen von Hilfe](~/assets/images/framework/framework_bots_tbot-help.png)

> [!TIP]
> <span data-ttu-id="18136-160">Durch das Einbetten von Teilen Ihrer Website auf eine Registerkarte kann ein Benutzer den Kontext einer Unterhaltung beibehalten, während dieser den Dienst verwendet.</span><span class="sxs-lookup"><span data-stu-id="18136-160">Embedding parts of your site in a tab will help someone maintain the context of a conversation as they use your service.</span></span> <span data-ttu-id="18136-161">Es entfällt die Notwendigkeit, ihren Dienst in einem Browser zu starten und zwischen apps hin und her zu wechseln.</span><span class="sxs-lookup"><span data-stu-id="18136-161">It removes the need to launch your service in a browser and switch back and forth between apps.</span></span>

---

## <a name="best-practices"></a><span data-ttu-id="18136-162">Bewährte Methoden</span><span class="sxs-lookup"><span data-stu-id="18136-162">Best practices</span></span>

### <a name="x2713-bots-arent-assistants"></a><span data-ttu-id="18136-163">&#x2713; Bots sind keine Assistenten</span><span class="sxs-lookup"><span data-stu-id="18136-163">&#x2713; Bots aren’t assistants</span></span>

<span data-ttu-id="18136-164">Im Gegensatz zu Agents, beispielsweise Cortana, fungieren Bots als Spezialisten.</span><span class="sxs-lookup"><span data-stu-id="18136-164">Unlike agents, e.g., Cortana, bots act as specialists.</span></span>

### <a name="x2713-discourage-chitchat"></a><span data-ttu-id="18136-165">&#x2713; abschrecken von Geplauder</span><span class="sxs-lookup"><span data-stu-id="18136-165">&#x2713; Discourage chitchat</span></span>

<span data-ttu-id="18136-166">Wenn Ihr bot nicht für Unterhaltungen entwickelt wurde, finden Sie Möglichkeiten, um das Geplauder in Richtung Aufgaben Abschluss umzuleiten.</span><span class="sxs-lookup"><span data-stu-id="18136-166">Unless your bot is built for conversation, find ways to redirect chitchat toward task completion.</span></span>

### <a name="x2713-introduce-some-personality"></a><span data-ttu-id="18136-167">&#x2713; Einführung einer Persönlichkeit</span><span class="sxs-lookup"><span data-stu-id="18136-167">&#x2713; Introduce some personality</span></span>

<span data-ttu-id="18136-168">Halten Sie Ihre bot-Persönlichkeit konsistent mit der Stimme Ihres Produkts.</span><span class="sxs-lookup"><span data-stu-id="18136-168">Keep your bot personality consistent with the voice of your product.</span></span> <span data-ttu-id="18136-169">Denken Sie an Ihren bot als sprechen für Ihr Unternehmen.</span><span class="sxs-lookup"><span data-stu-id="18136-169">Think of your bot as speaking for your company.</span></span>

### <a name="x2713-maintain-tone"></a><span data-ttu-id="18136-170">&#x2713; Ton beibehalten</span><span class="sxs-lookup"><span data-stu-id="18136-170">&#x2713; Maintain tone</span></span>

<span data-ttu-id="18136-171">Bestimmen Sie, ob Ihr Ton freundlich und leicht sein soll, "nur die Fakten" oder Super schrullig.</span><span class="sxs-lookup"><span data-stu-id="18136-171">Determine whether you want your tone to be friendly and light, “just the facts”, or super quirky.</span></span>

### <a name="x2713-encourage-easy-task-flow"></a><span data-ttu-id="18136-172">&#x2713; einfache Aufgaben Übermittlung fördern</span><span class="sxs-lookup"><span data-stu-id="18136-172">&#x2713; Encourage easy task flow</span></span>

<span data-ttu-id="18136-173">Unterstützung von Multi-Turn-Interaktionen, während immer noch vollständig geformte Fragen zulässt</span><span class="sxs-lookup"><span data-stu-id="18136-173">Support multi-turn interactions while still allowing for fully formed questions.</span></span> <span data-ttu-id="18136-174">Das antizipieren des nächsten Schritts erleichtert Benutzern das Durchlaufen von Aufgaben Abläufen erheblich.</span><span class="sxs-lookup"><span data-stu-id="18136-174">Anticipating the next step will help users get through task flows much easier.</span></span>

<span data-ttu-id="18136-175">Wenn ein Benutzer mehrere Schritte zum Ausführen einer Aufgabe ausführt, lassen Sie den bot diesen Schritt durchführen, aber beenden Sie ihn, indem Sie einen schnelleren Pfad vorschlagen.</span><span class="sxs-lookup"><span data-stu-id="18136-175">If a user takes several steps to complete a task, allow your bot to take them through each step, but finish by having it suggest a quicker path.</span></span> <span data-ttu-id="18136-176">Wenn ein Benutzer beispielsweise mehrere Konversations Schritte durchgeführt hat, um eine Besprechung festzulegen (indem er zuerst eine Besprechung angibt, dann identifiziert, mit wem, dann die Uhrzeit angibt und dann den Tag angibt), beenden Sie die Unterhaltung mit dem folgenden Vorschlag: Fragen Sie das nächste Mal, ob Sie kann eine Besprechung mit Bob um 1:00 Morgen planen.</span><span class="sxs-lookup"><span data-stu-id="18136-176">For example, if a user has taken several conversational turns to set a meeting (by first specifying a meeting, then identifying with whom, then stating the time, then stating the day), finish the conversation with the following suggestion: Next time, try asking if you can ‘schedule a meeting with Bob at 1:00 tomorrow’.</span></span>