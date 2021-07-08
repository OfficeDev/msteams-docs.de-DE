---
title: Kartentypen
description: Beschreibt alle Karten und Kartenaktionen, die Bots in Teams
localization_priority: Normal
keywords: Referenz zu Bots-Karten
ms.topic: reference
ms.openlocfilehash: d3b84344eccee7c2595b0e978c72d7e331b198cb
ms.sourcegitcommit: b1f9162a0bbcd276064ae9e4f1e8bccc06cb7035
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/07/2021
ms.locfileid: "53328072"
---
# <a name="types-of-cards"></a><span data-ttu-id="270d7-104">Kartentypen</span><span class="sxs-lookup"><span data-stu-id="270d7-104">Types of cards</span></span>

<span data-ttu-id="270d7-105">Adaptive, Hero-, List-, Office 365 Connector-, Beleg-, Anmelde- und Miniaturansichtskarten und Kartensammlungen werden in Bots für Microsoft Teams unterstützt.</span><span class="sxs-lookup"><span data-stu-id="270d7-105">Adaptive, hero, list, Office 365 Connector, receipt, signin, and thumbnail cards and card collections are supported in bots for Microsoft Teams.</span></span> <span data-ttu-id="270d7-106">Sie basieren auf Vom Bot Framework definierten Karten, aber Teams unterstützt nicht alle Bot Framework-Karten und hat einige eigene hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="270d7-106">They are based on cards defined by the Bot Framework, but Teams does not support all Bot Framework cards and has added some of its own.</span></span>

<span data-ttu-id="270d7-107">Bevor Sie die verschiedenen Kartentypen identifizieren, sollten Sie wissen, wie Sie eine Favoritenkarte, Miniaturansichtskarte oder adaptive Karte erstellen.</span><span class="sxs-lookup"><span data-stu-id="270d7-107">Before you identify the different card types, understand how to create a a hero card, thumbnail card, or Adaptive Card.</span></span>

## <a name="create-a-hero-card-thumbnail-card-or-adaptive-card"></a><span data-ttu-id="270d7-108">Erstellen einer Favoritenkarte, Miniaturansichtskarte oder adaptiven Karte</span><span class="sxs-lookup"><span data-stu-id="270d7-108">Create a hero card, thumbnail card, or Adaptive Card</span></span>

<span data-ttu-id="270d7-109">**So erstellen Sie eine Favoritenkarte, Miniaturansichtskarte oder adaptive Karte aus App Studio**</span><span class="sxs-lookup"><span data-stu-id="270d7-109">**To create a hero card, thumbnail card, or Adaptive Card from App Studio**</span></span>

1. <span data-ttu-id="270d7-110">Wechseln Sie von Teams zu **App Studio.**</span><span class="sxs-lookup"><span data-stu-id="270d7-110">Go to **App Studio** from Teams.</span></span>
1. <span data-ttu-id="270d7-111">Wählen Sie **den Karten-Editor** aus.</span><span class="sxs-lookup"><span data-stu-id="270d7-111">Select **Card editor**.</span></span>
1. <span data-ttu-id="270d7-112">Wählen Sie **"Neue Karte erstellen"** aus.</span><span class="sxs-lookup"><span data-stu-id="270d7-112">Select **Create a new card**.</span></span>
1. <span data-ttu-id="270d7-113">Wählen Sie **"Erstellen"** für eine der Karten aus **Hero-Karte,** **Miniaturansichtskarte** oder **adaptiver Karte** aus.</span><span class="sxs-lookup"><span data-stu-id="270d7-113">Select **Create** for one of the cards from **Hero Card**, **Thumbnail Card**, or **Adaptive Card**.</span></span> <span data-ttu-id="270d7-114">Die Metadatendetails, Schaltflächen und JSON-, Csharp- und Knotencodebeispiele werden für diese Karte gezeigt.</span><span class="sxs-lookup"><span data-stu-id="270d7-114">The metadata details, buttons, and json, csharp, and node code examples are shown for that card.</span></span>

    ![Favoritenkartendetails](~/assets/images/Cards/Herocarddetails.png)

1. <span data-ttu-id="270d7-116">Wählen Sie **"Diese Karte senden" aus.**</span><span class="sxs-lookup"><span data-stu-id="270d7-116">Select **Send me this card**.</span></span> <span data-ttu-id="270d7-117">Die Karte wird als Chatnachricht an Sie gesendet.</span><span class="sxs-lookup"><span data-stu-id="270d7-117">The card is sent to you as a chat message.</span></span>

## <a name="card-examples"></a><span data-ttu-id="270d7-118">Kartenbeispiele</span><span class="sxs-lookup"><span data-stu-id="270d7-118">Card examples</span></span>

<span data-ttu-id="270d7-119">Weitere Informationen zur Verwendung von Karten finden Sie in der Dokumentation für das Bot Builder SDK v3.</span><span class="sxs-lookup"><span data-stu-id="270d7-119">You can find additional information on how to use cards in the documentation for the Bot Builder SDK v3.</span></span> <span data-ttu-id="270d7-120">Codebeispiele sind auch im **Microsoft/BotBuilder-Samples-Repository** auf GitHub verfügbar.</span><span class="sxs-lookup"><span data-stu-id="270d7-120">Code samples are also available in the **Microsoft/BotBuilder-Samples** repository on GitHub.</span></span> <span data-ttu-id="270d7-121">Es folgen einige Kartenbeispiele:</span><span class="sxs-lookup"><span data-stu-id="270d7-121">Following are a few card examples:</span></span>

* <span data-ttu-id="270d7-122">.NET</span><span class="sxs-lookup"><span data-stu-id="270d7-122">.NET</span></span>
  * <span data-ttu-id="270d7-123">[Fügen Sie Nachrichten Karten als Anlagen hinzu.](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-an-adaptive-card&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="270d7-123">[Add cards as attachments to messages](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-an-adaptive-card&preserve-view=true).</span></span>
  * <span data-ttu-id="270d7-124">[Karten-Beispielcode Bot Builder v4](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/06.using-cards).</span><span class="sxs-lookup"><span data-stu-id="270d7-124">[Cards sample code Bot Builder v4](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/06.using-cards).</span></span>

* <span data-ttu-id="270d7-125">Node.js</span><span class="sxs-lookup"><span data-stu-id="270d7-125">Node.js</span></span>
  * <span data-ttu-id="270d7-126">[Fügen Sie Nachrichten Karten als Anlagen hinzu.](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=javascript#send-an-adaptive-card&preserve-view=true)</span><span class="sxs-lookup"><span data-stu-id="270d7-126">[Add cards as attachments to messages](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=javascript#send-an-adaptive-card&preserve-view=true).</span></span>
  * <span data-ttu-id="270d7-127">[Karten-Beispielcode Bot Builder v4](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/06.using-cards).</span><span class="sxs-lookup"><span data-stu-id="270d7-127">[Cards sample code Bot Builder v4](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/javascript_nodejs/06.using-cards).</span></span>

## <a name="card-types"></a><span data-ttu-id="270d7-128">Kartentypen</span><span class="sxs-lookup"><span data-stu-id="270d7-128">Card types</span></span>

<span data-ttu-id="270d7-129">Sie können unterschiedliche Kartentypen basierend auf Ihren Anwendungsanforderungen identifizieren und verwenden.</span><span class="sxs-lookup"><span data-stu-id="270d7-129">You can identify and use different types of cards based on your application requirements.</span></span> <span data-ttu-id="270d7-130">In der folgenden Tabelle sind die Kartentypen aufgeführt, die Ihnen zur Verfügung stehen:</span><span class="sxs-lookup"><span data-stu-id="270d7-130">The following table shows the types of cards available to you:</span></span>

| <span data-ttu-id="270d7-131">Kartentyp</span><span class="sxs-lookup"><span data-stu-id="270d7-131">Card type</span></span> | <span data-ttu-id="270d7-132">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="270d7-132">Description</span></span> |
| --- | --- |
| [<span data-ttu-id="270d7-133">Adaptive Karte</span><span class="sxs-lookup"><span data-stu-id="270d7-133">Adaptive Card</span></span>](#adaptive-card) | <span data-ttu-id="270d7-134">Diese Karte ist in hohem Maße anpassbar und kann eine beliebige Kombination aus Text, Sprache, Bildern, Schaltflächen und Eingabefeldern enthalten.</span><span class="sxs-lookup"><span data-stu-id="270d7-134">This card is highly customizable and can contain any combination of text, speech, images, buttons, and input fields.</span></span> |
| [<span data-ttu-id="270d7-135">Hero-Karte</span><span class="sxs-lookup"><span data-stu-id="270d7-135">Hero card</span></span>](#hero-card) | <span data-ttu-id="270d7-136">Diese Karte enthält in der Regel ein einzelnes großes Bild, eine oder mehrere Schaltflächen und eine kleine Textmenge.</span><span class="sxs-lookup"><span data-stu-id="270d7-136">This card typically contains a single large image, one or more buttons, and a small amount of text.</span></span> |
| [<span data-ttu-id="270d7-137">Karte auflisten</span><span class="sxs-lookup"><span data-stu-id="270d7-137">List card</span></span>](#list-card) | <span data-ttu-id="270d7-138">Diese Karte enthält eine Bildlaufliste von Elementen.</span><span class="sxs-lookup"><span data-stu-id="270d7-138">This card contains a scrolling list of items.</span></span> |
| [<span data-ttu-id="270d7-139">Office 365 Connectorkarte</span><span class="sxs-lookup"><span data-stu-id="270d7-139">Office 365 Connector card</span></span>](#office-365-connector-card) | <span data-ttu-id="270d7-140">Diese Karte verfügt über ein flexibles Layout mit mehreren Abschnitten, Feldern, Bildern und Aktionen.</span><span class="sxs-lookup"><span data-stu-id="270d7-140">This card has a flexible layout with multiple sections, fields, images, and actions.</span></span> |
| [<span data-ttu-id="270d7-141">Belegkarte</span><span class="sxs-lookup"><span data-stu-id="270d7-141">Receipt card</span></span>](#receipt-card) | <span data-ttu-id="270d7-142">Diese Karte stellt dem Benutzer einen Beleg bereit.</span><span class="sxs-lookup"><span data-stu-id="270d7-142">This card provides a receipt to the user.</span></span> |
| [<span data-ttu-id="270d7-143">Anmeldekarte</span><span class="sxs-lookup"><span data-stu-id="270d7-143">Signin card</span></span>](#signin-card) | <span data-ttu-id="270d7-144">Mit dieser Karte kann ein Bot anfordern, dass sich ein Benutzer anmeldet.</span><span class="sxs-lookup"><span data-stu-id="270d7-144">This card enables a bot to request that a user signs in.</span></span> |
| [<span data-ttu-id="270d7-145">Miniaturansichtskarte</span><span class="sxs-lookup"><span data-stu-id="270d7-145">Thumbnail card</span></span>](#thumbnail-card) | <span data-ttu-id="270d7-146">Diese Karte enthält in der Regel ein einzelnes Miniaturbild, kurzen Text und eine oder mehrere Schaltflächen.</span><span class="sxs-lookup"><span data-stu-id="270d7-146">This card typically contains a single thumbnail image, some short text, and one or more buttons.</span></span> |
| [<span data-ttu-id="270d7-147">Kartensammlungen</span><span class="sxs-lookup"><span data-stu-id="270d7-147">Card collections</span></span>](#card-collections) | <span data-ttu-id="270d7-148">Diese Kartensammlung wird verwendet, um mehrere Elemente in einer einzigen Antwort zurückzugeben.</span><span class="sxs-lookup"><span data-stu-id="270d7-148">This card collection is used to return multiple items in a single response.</span></span> |

## <a name="features-that-support-different-card-types"></a><span data-ttu-id="270d7-149">Features, die unterschiedliche Kartentypen unterstützen</span><span class="sxs-lookup"><span data-stu-id="270d7-149">Features that support different card types</span></span>

| <span data-ttu-id="270d7-150">Kartentyp</span><span class="sxs-lookup"><span data-stu-id="270d7-150">Card type</span></span> | <span data-ttu-id="270d7-151">Bots</span><span class="sxs-lookup"><span data-stu-id="270d7-151">Bots</span></span> | <span data-ttu-id="270d7-152">Vorschau der Nachrichtenerweiterung</span><span class="sxs-lookup"><span data-stu-id="270d7-152">Message extension previews</span></span> | <span data-ttu-id="270d7-153">Ergebnisse der Nachrichtenerweiterung</span><span class="sxs-lookup"><span data-stu-id="270d7-153">Message extension results</span></span> | <span data-ttu-id="270d7-154">Aufgabenmodule</span><span class="sxs-lookup"><span data-stu-id="270d7-154">Task modules</span></span> | <span data-ttu-id="270d7-155">Ausgehende Webhooks</span><span class="sxs-lookup"><span data-stu-id="270d7-155">Outgoing Webhooks</span></span> | <span data-ttu-id="270d7-156">Eingehende Webhooks</span><span class="sxs-lookup"><span data-stu-id="270d7-156">Incoming Webhooks</span></span> | <span data-ttu-id="270d7-157">O365-Connectors</span><span class="sxs-lookup"><span data-stu-id="270d7-157">O365 Connectors</span></span> |
| --- | --- | --- | --- | --- | --- | --- | --- |
| <span data-ttu-id="270d7-158">Adaptive Karte</span><span class="sxs-lookup"><span data-stu-id="270d7-158">Adaptive Card</span></span> | <span data-ttu-id="270d7-159">✔</span><span class="sxs-lookup"><span data-stu-id="270d7-159">✔</span></span> | <span data-ttu-id="270d7-160">✖</span><span class="sxs-lookup"><span data-stu-id="270d7-160">✖</span></span> | <span data-ttu-id="270d7-161">✔</span><span class="sxs-lookup"><span data-stu-id="270d7-161">✔</span></span> | <span data-ttu-id="270d7-162">✔</span><span class="sxs-lookup"><span data-stu-id="270d7-162">✔</span></span> | <span data-ttu-id="270d7-163">✔</span><span class="sxs-lookup"><span data-stu-id="270d7-163">✔</span></span> | <span data-ttu-id="270d7-164">✔</span><span class="sxs-lookup"><span data-stu-id="270d7-164">✔</span></span> | <span data-ttu-id="270d7-165">✖</span><span class="sxs-lookup"><span data-stu-id="270d7-165">✖</span></span> |
| <span data-ttu-id="270d7-166">O365-Connectorkarte</span><span class="sxs-lookup"><span data-stu-id="270d7-166">O365 Connector card</span></span> | <span data-ttu-id="270d7-167">✔</span><span class="sxs-lookup"><span data-stu-id="270d7-167">✔</span></span> | <span data-ttu-id="270d7-168">✖</span><span class="sxs-lookup"><span data-stu-id="270d7-168">✖</span></span> | <span data-ttu-id="270d7-169">✔</span><span class="sxs-lookup"><span data-stu-id="270d7-169">✔</span></span> | <span data-ttu-id="270d7-170">✖</span><span class="sxs-lookup"><span data-stu-id="270d7-170">✖</span></span> | <span data-ttu-id="270d7-171">✔</span><span class="sxs-lookup"><span data-stu-id="270d7-171">✔</span></span> | <span data-ttu-id="270d7-172">✔</span><span class="sxs-lookup"><span data-stu-id="270d7-172">✔</span></span> | <span data-ttu-id="270d7-173">✔</span><span class="sxs-lookup"><span data-stu-id="270d7-173">✔</span></span> |
| <span data-ttu-id="270d7-174">Hero-Karte</span><span class="sxs-lookup"><span data-stu-id="270d7-174">Hero card</span></span> | <span data-ttu-id="270d7-175">✔</span><span class="sxs-lookup"><span data-stu-id="270d7-175">✔</span></span> | <span data-ttu-id="270d7-176">✔</span><span class="sxs-lookup"><span data-stu-id="270d7-176">✔</span></span> | <span data-ttu-id="270d7-177">✔</span><span class="sxs-lookup"><span data-stu-id="270d7-177">✔</span></span> | <span data-ttu-id="270d7-178">✖</span><span class="sxs-lookup"><span data-stu-id="270d7-178">✖</span></span> | <span data-ttu-id="270d7-179">✔</span><span class="sxs-lookup"><span data-stu-id="270d7-179">✔</span></span> | <span data-ttu-id="270d7-180">✔</span><span class="sxs-lookup"><span data-stu-id="270d7-180">✔</span></span> | <span data-ttu-id="270d7-181">✖</span><span class="sxs-lookup"><span data-stu-id="270d7-181">✖</span></span> |
| <span data-ttu-id="270d7-182">Miniaturansichtskarte</span><span class="sxs-lookup"><span data-stu-id="270d7-182">Thumbnail card</span></span> | <span data-ttu-id="270d7-183">✔</span><span class="sxs-lookup"><span data-stu-id="270d7-183">✔</span></span> | <span data-ttu-id="270d7-184">✔</span><span class="sxs-lookup"><span data-stu-id="270d7-184">✔</span></span> | <span data-ttu-id="270d7-185">✔</span><span class="sxs-lookup"><span data-stu-id="270d7-185">✔</span></span> | <span data-ttu-id="270d7-186">✖</span><span class="sxs-lookup"><span data-stu-id="270d7-186">✖</span></span> | <span data-ttu-id="270d7-187">✔</span><span class="sxs-lookup"><span data-stu-id="270d7-187">✔</span></span> | <span data-ttu-id="270d7-188">✔</span><span class="sxs-lookup"><span data-stu-id="270d7-188">✔</span></span> | <span data-ttu-id="270d7-189">✖</span><span class="sxs-lookup"><span data-stu-id="270d7-189">✖</span></span> |
| <span data-ttu-id="270d7-190">Karte auflisten</span><span class="sxs-lookup"><span data-stu-id="270d7-190">List card</span></span> | <span data-ttu-id="270d7-191">✔</span><span class="sxs-lookup"><span data-stu-id="270d7-191">✔</span></span> | <span data-ttu-id="270d7-192">✖</span><span class="sxs-lookup"><span data-stu-id="270d7-192">✖</span></span> | <span data-ttu-id="270d7-193">✖</span><span class="sxs-lookup"><span data-stu-id="270d7-193">✖</span></span> | <span data-ttu-id="270d7-194">✖</span><span class="sxs-lookup"><span data-stu-id="270d7-194">✖</span></span> | <span data-ttu-id="270d7-195">✔</span><span class="sxs-lookup"><span data-stu-id="270d7-195">✔</span></span> | <span data-ttu-id="270d7-196">✔</span><span class="sxs-lookup"><span data-stu-id="270d7-196">✔</span></span> | <span data-ttu-id="270d7-197">✖</span><span class="sxs-lookup"><span data-stu-id="270d7-197">✖</span></span> |
| <span data-ttu-id="270d7-198">Belegkarte</span><span class="sxs-lookup"><span data-stu-id="270d7-198">Receipt card</span></span> | <span data-ttu-id="270d7-199">✔</span><span class="sxs-lookup"><span data-stu-id="270d7-199">✔</span></span> | <span data-ttu-id="270d7-200">✖</span><span class="sxs-lookup"><span data-stu-id="270d7-200">✖</span></span> | <span data-ttu-id="270d7-201">✖</span><span class="sxs-lookup"><span data-stu-id="270d7-201">✖</span></span> | <span data-ttu-id="270d7-202">✖</span><span class="sxs-lookup"><span data-stu-id="270d7-202">✖</span></span> | <span data-ttu-id="270d7-203">✖</span><span class="sxs-lookup"><span data-stu-id="270d7-203">✖</span></span> | <span data-ttu-id="270d7-204">✔</span><span class="sxs-lookup"><span data-stu-id="270d7-204">✔</span></span> | <span data-ttu-id="270d7-205">✖</span><span class="sxs-lookup"><span data-stu-id="270d7-205">✖</span></span> |
| <span data-ttu-id="270d7-206">Anmeldekarte</span><span class="sxs-lookup"><span data-stu-id="270d7-206">Signin card</span></span> | <span data-ttu-id="270d7-207">✔</span><span class="sxs-lookup"><span data-stu-id="270d7-207">✔</span></span> | <span data-ttu-id="270d7-208">✖</span><span class="sxs-lookup"><span data-stu-id="270d7-208">✖</span></span> | <span data-ttu-id="270d7-209">✖</span><span class="sxs-lookup"><span data-stu-id="270d7-209">✖</span></span> | <span data-ttu-id="270d7-210">✖</span><span class="sxs-lookup"><span data-stu-id="270d7-210">✖</span></span> | <span data-ttu-id="270d7-211">✖</span><span class="sxs-lookup"><span data-stu-id="270d7-211">✖</span></span> | <span data-ttu-id="270d7-212">✖</span><span class="sxs-lookup"><span data-stu-id="270d7-212">✖</span></span> | <span data-ttu-id="270d7-213">✖</span><span class="sxs-lookup"><span data-stu-id="270d7-213">✖</span></span> |

> [!NOTE]
> <span data-ttu-id="270d7-214">Bei adaptiven Karten in eingehenden Webhooks werden alle systemeigenen Schemaelemente adaptiver Karten, mit Ausnahme `Action.Submit` von , vollständig unterstützt.</span><span class="sxs-lookup"><span data-stu-id="270d7-214">For Adaptive Cards in Incoming Webhooks, all native Adaptive Card schema elements, except `Action.Submit`, are fully supported.</span></span> <span data-ttu-id="270d7-215">Die unterstützten Aktionen sind [**Action.OpenURL**](https://adaptivecards.io/explorer/Action.OpenUrl.html), [**Action.ShowCard**](https://adaptivecards.io/explorer/Action.ShowCard.html), [**Action.ToggleVisibility**](https://adaptivecards.io/explorer/Action.ToggleVisibility.html)und [**Action.Execute**](/adaptive-cards/authoring-cards/universal-action-model#actionexecute).</span><span class="sxs-lookup"><span data-stu-id="270d7-215">The supported actions are [**Action.OpenURL**](https://adaptivecards.io/explorer/Action.OpenUrl.html), [**Action.ShowCard**](https://adaptivecards.io/explorer/Action.ShowCard.html), [**Action.ToggleVisibility**](https://adaptivecards.io/explorer/Action.ToggleVisibility.html), and [**Action.Execute**](/adaptive-cards/authoring-cards/universal-action-model#actionexecute).</span></span>

## <a name="common-properties-for-all-cards"></a><span data-ttu-id="270d7-216">Allgemeine Eigenschaften für alle Karten</span><span class="sxs-lookup"><span data-stu-id="270d7-216">Common properties for all cards</span></span>

<span data-ttu-id="270d7-217">Sie können einige allgemeine Eigenschaften durchgehen, die für alle Karten gelten.</span><span class="sxs-lookup"><span data-stu-id="270d7-217">You can go through some common properties that are applicable to all cards.</span></span>

### <a name="inline-card-images"></a><span data-ttu-id="270d7-218">Inlinekartenbilder</span><span class="sxs-lookup"><span data-stu-id="270d7-218">Inline card images</span></span>

<span data-ttu-id="270d7-219">Die Karte kann ein Inlinebild enthalten, indem ein Link zum öffentlich verfügbaren Bild eingeschlossen wird.</span><span class="sxs-lookup"><span data-stu-id="270d7-219">The card can contain an inline image by including a link to the publicly available image.</span></span> <span data-ttu-id="270d7-220">Aus Leistungsgründen wird dringend empfohlen, das Image auf einem öffentlichen Content Delivery Network (CDN) zu hosten.</span><span class="sxs-lookup"><span data-stu-id="270d7-220">For performance purposes, it is highly recommended you host the image on a public Content Delivery Network (CDN).</span></span>

<span data-ttu-id="270d7-221">Bilder werden nach oben oder unten skaliert, um das Seitenverhältnis für die Abdeckung des Bildbereichs beizubehalten.</span><span class="sxs-lookup"><span data-stu-id="270d7-221">Images are scaled up or down in size to maintain the aspect ratio for covering the image area.</span></span> <span data-ttu-id="270d7-222">Bilder werden dann von der Mitte zugeschnitten, um das entsprechende Seitenverhältnis für die Karte zu erzielen.</span><span class="sxs-lookup"><span data-stu-id="270d7-222">Images are then cropped from center to achieve the appropriate aspect ratio for the card.</span></span>

<span data-ttu-id="270d7-223">Bilder müssen höchstens 1024×1024 und im PNG-, JPEG- oder GIF-Format vorliegen.</span><span class="sxs-lookup"><span data-stu-id="270d7-223">Images must be at most 1024×1024 and in PNG, JPEG, or GIF format.</span></span> <span data-ttu-id="270d7-224">Animierte GIF-Dateien werden nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="270d7-224">Animated GIF is not supported.</span></span>

<span data-ttu-id="270d7-225">Die folgende Tabelle enthält die Eigenschaften von Inlinekartenbildern:</span><span class="sxs-lookup"><span data-stu-id="270d7-225">The following table provides the properties of inline card images:</span></span>

| <span data-ttu-id="270d7-226">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="270d7-226">Property</span></span> | <span data-ttu-id="270d7-227">Typ</span><span class="sxs-lookup"><span data-stu-id="270d7-227">Type</span></span>  | <span data-ttu-id="270d7-228">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="270d7-228">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="270d7-229">url</span><span class="sxs-lookup"><span data-stu-id="270d7-229">url</span></span> | <span data-ttu-id="270d7-230">URL</span><span class="sxs-lookup"><span data-stu-id="270d7-230">URL</span></span> | <span data-ttu-id="270d7-231">HTTPS-URL zum Bild.</span><span class="sxs-lookup"><span data-stu-id="270d7-231">HTTPS URL to the image.</span></span> |
| <span data-ttu-id="270d7-232">alt</span><span class="sxs-lookup"><span data-stu-id="270d7-232">alt</span></span> | <span data-ttu-id="270d7-233">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="270d7-233">String</span></span> | <span data-ttu-id="270d7-234">Beschreibung des Bilds, auf das zugegriffen werden kann.</span><span class="sxs-lookup"><span data-stu-id="270d7-234">Accessible description of the image.</span></span> |

> [!NOTE]
> <span data-ttu-id="270d7-235">Wenn eine Karte eine Bild-URL enthält, die vor dem endgültigen Bild umgeleitet wird, wird die Umleitung in der Bild-URL nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="270d7-235">If a card includes an image URL that is redirected before the final image, the redirect in image URL is not supported.</span></span> <span data-ttu-id="270d7-236">Dies geschieht für Bilder, die in der öffentlichen Cloud freigegeben sind.</span><span class="sxs-lookup"><span data-stu-id="270d7-236">This occurs for images shared on the public cloud.</span></span>

### <a name="buttons"></a><span data-ttu-id="270d7-237">Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="270d7-237">Buttons</span></span>

<span data-ttu-id="270d7-238">Schaltflächen werden am unteren Rand der Karte gestapelt angezeigt.</span><span class="sxs-lookup"><span data-stu-id="270d7-238">Buttons are shown stacked at the bottom of the card.</span></span> <span data-ttu-id="270d7-239">Schaltflächentext befindet sich immer in einer zeile und wird abgeschnitten, wenn der Text die Breite der Schaltfläche überschreitet.</span><span class="sxs-lookup"><span data-stu-id="270d7-239">Button text is always on a single line and is truncated if the text exceeds the button width.</span></span> <span data-ttu-id="270d7-240">Zusätzliche Schaltflächen, die über die von der Karte maximal unterstützte Anzahl hinausgehen, werden nicht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="270d7-240">Any additional buttons beyond the maximum number supported by the card are not shown.</span></span>

<span data-ttu-id="270d7-241">Weitere Informationen finden Sie unter [Kartenaktionen.](~/task-modules-and-cards/cards/cards-actions.md)</span><span class="sxs-lookup"><span data-stu-id="270d7-241">For more information, see [card actions](~/task-modules-and-cards/cards/cards-actions.md).</span></span>

### <a name="card-formatting"></a><span data-ttu-id="270d7-242">Kartenformatierung</span><span class="sxs-lookup"><span data-stu-id="270d7-242">Card formatting</span></span>

<span data-ttu-id="270d7-243">Weitere Informationen zur Textformatierung in Karten finden Sie unter [Kartenformatierung.](~/task-modules-and-cards/cards/cards-format.md)</span><span class="sxs-lookup"><span data-stu-id="270d7-243">For more information on text formatting in cards, see [card formatting](~/task-modules-and-cards/cards/cards-format.md).</span></span>

<span data-ttu-id="270d7-244">Nachdem Sie die allgemeinen Eigenschaften für alle Karten identifiziert haben, können Sie jetzt mit adaptiven Karten arbeiten, die Ihnen helfen, das Engagement und die Effizienz zu steigern, indem Sie Ihre Aktionen erfordernden Inhalte direkt zu den von Ihnen verwendeten Apps hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="270d7-244">After identifying the common properties for all cards, you can now work with Adaptive Cards, which help you increase engagement and efficiency by adding your actionable content directly into the apps you use.</span></span>

## <a name="adaptive-card"></a><span data-ttu-id="270d7-245">Adaptive Karte</span><span class="sxs-lookup"><span data-stu-id="270d7-245">Adaptive Card</span></span>

> [!VIDEO https://www.youtube-nocookie.com/embed/J12lKt717Ws]

<span data-ttu-id="270d7-246">Eine adaptive Karte ist eine anpassbare Karte, die eine beliebige Kombination aus Text, Sprache, Bildern, Schaltflächen und Eingabefeldern enthalten kann.</span><span class="sxs-lookup"><span data-stu-id="270d7-246">An Adaptive Card is a customizable card that can contain any combination of text, speech, images, buttons, and input fields.</span></span> <span data-ttu-id="270d7-247">Weitere Informationen finden Sie unter [Adaptive Karten v1.2.0.](https://github.com/microsoft/AdaptiveCards/releases/tag/v1.2.0)</span><span class="sxs-lookup"><span data-stu-id="270d7-247">For more information, see [Adaptive Cards v1.2.0](https://github.com/microsoft/AdaptiveCards/releases/tag/v1.2.0).</span></span>

### <a name="support-for-adaptive-cards"></a><span data-ttu-id="270d7-248">Unterstützung für adaptive Karten</span><span class="sxs-lookup"><span data-stu-id="270d7-248">Support for Adaptive Cards</span></span>

<span data-ttu-id="270d7-249">Die folgende Tabelle enthält die Features, die adaptive Karten unterstützen:</span><span class="sxs-lookup"><span data-stu-id="270d7-249">The following table provides the features that support Adaptive Cards:</span></span>

| <span data-ttu-id="270d7-250">Bots in Teams</span><span class="sxs-lookup"><span data-stu-id="270d7-250">Bots in Teams</span></span> | <span data-ttu-id="270d7-251">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="270d7-251">Messaging extensions</span></span>  | <span data-ttu-id="270d7-252">Connectors</span><span class="sxs-lookup"><span data-stu-id="270d7-252">Connectors</span></span> | <span data-ttu-id="270d7-253">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="270d7-253">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="270d7-254">✔</span><span class="sxs-lookup"><span data-stu-id="270d7-254">✔</span></span> | <span data-ttu-id="270d7-255">✔</span><span class="sxs-lookup"><span data-stu-id="270d7-255">✔</span></span> | <span data-ttu-id="270d7-256">✖</span><span class="sxs-lookup"><span data-stu-id="270d7-256">✖</span></span> | <span data-ttu-id="270d7-257">✔</span><span class="sxs-lookup"><span data-stu-id="270d7-257">✔</span></span> |

> [!NOTE]
> * <span data-ttu-id="270d7-258">Teams Plattform unterstützt v1.2 oder eine frühere Version von Features für adaptive Karten.</span><span class="sxs-lookup"><span data-stu-id="270d7-258">Teams platform supports v1.2 or earlier of Adaptive Card features.</span></span>
> * <span data-ttu-id="270d7-259">Das Formatieren positiver oder destruktiver Aktionen wird in adaptiven Karten auf der Teams Plattform nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="270d7-259">Positive or destructive action styling is not supported in Adaptive Cards on the Teams platform.</span></span>
> * <span data-ttu-id="270d7-260">Medienelemente werden derzeit in adaptiver Karte auf der Teams-Plattform nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="270d7-260">Media elements are currently not supported in Adaptive Card on the Teams platform.</span></span>

### <a name="example-of-adaptive-card"></a><span data-ttu-id="270d7-261">Beispiel für adaptive Karte</span><span class="sxs-lookup"><span data-stu-id="270d7-261">Example of Adaptive Card</span></span>

![Beispiel für eine adaptive Karte](~/assets/images/cards/adaptivecard.png)

<span data-ttu-id="270d7-263">Der folgende Code zeigt ein Beispiel für eine adaptive Karte:</span><span class="sxs-lookup"><span data-stu-id="270d7-263">The following code shows an example of an Adaptive Card:</span></span>

```json
{
  "contentType": "application/vnd.microsoft.card.adaptive",
  "content": {
    "$schema": "http://adaptivecards.io/schemas/adaptive-card.json",
    "type": "AdaptiveCard",
    "version": "1.0",
    "body": [
      {
        "type": "Container",
        "items": [
          {
            "type": "TextBlock",
            "text": "Publish Adaptive Card schema",
            "weight": "bolder",
            "size": "medium"
          },
          {
            "type": "ColumnSet",
            "columns": [
              {
                "type": "Column",
                "width": "auto",
                "items": [
                  {
                    "type": "Image",
                    "url": "https://pbs.twimg.com/profile_images/3647943215/d7f12830b3c17a5a9e4afcc370e3a37e_400x400.jpeg",
                    "size": "small",
                    "style": "person"
                  }
                ]
              },
              {
                "type": "Column",
                "width": "stretch",
                "items": [
                  {
                    "type": "TextBlock",
                    "text": "Matt Hidinger",
                    "weight": "bolder",
                    "wrap": true
                  },
                  {
                    "type": "TextBlock",
                    "spacing": "none",
                    "text": "Created {{DATE(2017-02-14T06:08:39Z, SHORT)}}",
                    "isSubtle": true,
                    "wrap": true
                  }
                ]
              }
            ]
          }
        ]
      },
      {
        "type": "Container",
        "items": [
          {
            "type": "TextBlock",
            "text": "Now that we have defined the main rules and features of the format, we need to produce a schema and publish it to GitHub. The schema will be the starting point of our reference documentation.",
            "wrap": true
          },
          {
            "type": "FactSet",
            "facts": [
              {
                "title": "Board:",
                "value": "Adaptive Card"
              },
              {
                "title": "List:",
                "value": "Backlog"
              },
              {
                "title": "Assigned to:",
                "value": "Matt Hidinger"
              },
              {
                "title": "Due date:",
                "value": "Not set"
              }
            ]
          }
        ]
      }
    ],
    "actions": [
      {
        "type": "Action.ShowCard",
        "title": "Set due date",
        "card": {
          "type": "AdaptiveCard",
          "body": [
            {
              "type": "Input.Date",
              "id": "dueDate"
            }
          ],
          "actions": [
            {
              "type": "Action.Submit",
              "title": "OK"
            }
          ]
        }
      },
      {
        "type": "Action.ShowCard",
        "title": "Comment",
        "card": {
          "type": "AdaptiveCard",
          "body": [
            {
              "type": "Input.Text",
              "id": "comment",
              "isMultiline": true,
              "placeholder": "Enter your comment"
            }
          ],
          "actions": [
            {
              "type": "Action.Submit",
              "title": "OK"
            }
          ]
        }
      }
    ]
  }  
}
```

#### <a name="additional-information-on-adaptive-cards"></a><span data-ttu-id="270d7-264">Zusätzliche Informationen zu adaptiven Karten</span><span class="sxs-lookup"><span data-stu-id="270d7-264">Additional information on Adaptive Cards</span></span>

<span data-ttu-id="270d7-265">Bot Framework-Referenz:</span><span class="sxs-lookup"><span data-stu-id="270d7-265">Bot Framework reference:</span></span>

* [<span data-ttu-id="270d7-266">Knoten "Adaptive Karten"</span><span class="sxs-lookup"><span data-stu-id="270d7-266">Adaptive Cards Node</span></span>](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=javascript#send-an-adaptive-card&preserve-view=true)
* [<span data-ttu-id="270d7-267">Adaptive Karte C #</span><span class="sxs-lookup"><span data-stu-id="270d7-267">Adaptive Card C#</span></span>](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-an-adaptive-card&preserve-view=true)

<span data-ttu-id="270d7-268">Sie können jetzt mit einer Hero-Karte arbeiten, bei der es sich um eine Mehrzweckkarte handelt, die verwendet wird, um eine potenzielle Benutzerauswahl visuell hervorzuheben.</span><span class="sxs-lookup"><span data-stu-id="270d7-268">You can now work with a hero card, which is a multipurpose card used to visually highlight a potential user selection.</span></span>

## <a name="hero-card"></a><span data-ttu-id="270d7-269">Hero-Karte</span><span class="sxs-lookup"><span data-stu-id="270d7-269">Hero card</span></span>

<span data-ttu-id="270d7-270">Eine Karte, die in der Regel ein einzelnes großes Bild, eine oder mehrere Schaltflächen und Text enthält.</span><span class="sxs-lookup"><span data-stu-id="270d7-270">A card that typically contains a single large image, one or more buttons, and text.</span></span>

### <a name="support-for-hero-cards"></a><span data-ttu-id="270d7-271">Unterstützung für Favoritenkarten</span><span class="sxs-lookup"><span data-stu-id="270d7-271">Support for hero cards</span></span>

<span data-ttu-id="270d7-272">Die folgende Tabelle enthält die Features, die Hero-Karten unterstützen:</span><span class="sxs-lookup"><span data-stu-id="270d7-272">The following table provides the features that support hero cards:</span></span>

| <span data-ttu-id="270d7-273">Bots in Teams</span><span class="sxs-lookup"><span data-stu-id="270d7-273">Bots in Teams</span></span> | <span data-ttu-id="270d7-274">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="270d7-274">Messaging extensions</span></span>  | <span data-ttu-id="270d7-275">Connectors</span><span class="sxs-lookup"><span data-stu-id="270d7-275">Connectors</span></span> | <span data-ttu-id="270d7-276">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="270d7-276">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="270d7-277">✔</span><span class="sxs-lookup"><span data-stu-id="270d7-277">✔</span></span> | <span data-ttu-id="270d7-278">✔</span><span class="sxs-lookup"><span data-stu-id="270d7-278">✔</span></span> | <span data-ttu-id="270d7-279">✖</span><span class="sxs-lookup"><span data-stu-id="270d7-279">✖</span></span> | <span data-ttu-id="270d7-280">✔</span><span class="sxs-lookup"><span data-stu-id="270d7-280">✔</span></span> |

### <a name="properties-of-a-hero-card"></a><span data-ttu-id="270d7-281">Eigenschaften einer Favoritenkarte</span><span class="sxs-lookup"><span data-stu-id="270d7-281">Properties of a hero card</span></span>

<span data-ttu-id="270d7-282">Die folgende Tabelle enthält die Eigenschaften einer Hero-Karte:</span><span class="sxs-lookup"><span data-stu-id="270d7-282">The following table provides the properties of a hero card:</span></span>

| <span data-ttu-id="270d7-283">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="270d7-283">Property</span></span> | <span data-ttu-id="270d7-284">Typ</span><span class="sxs-lookup"><span data-stu-id="270d7-284">Type</span></span>  | <span data-ttu-id="270d7-285">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="270d7-285">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="270d7-286">title</span><span class="sxs-lookup"><span data-stu-id="270d7-286">title</span></span> | <span data-ttu-id="270d7-287">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="270d7-287">Rich text</span></span> | <span data-ttu-id="270d7-288">Titel der Karte.</span><span class="sxs-lookup"><span data-stu-id="270d7-288">Title of the card.</span></span> <span data-ttu-id="270d7-289">Maximal zwei Zeilen.</span><span class="sxs-lookup"><span data-stu-id="270d7-289">Maximum two lines.</span></span> |
| <span data-ttu-id="270d7-290">Untertitel</span><span class="sxs-lookup"><span data-stu-id="270d7-290">subtitle</span></span> | <span data-ttu-id="270d7-291">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="270d7-291">Rich text</span></span> | <span data-ttu-id="270d7-292">Untertitel der Karte.</span><span class="sxs-lookup"><span data-stu-id="270d7-292">Subtitle of the card.</span></span> <span data-ttu-id="270d7-293">Maximal zwei Zeilen.</span><span class="sxs-lookup"><span data-stu-id="270d7-293">Maximum two lines.</span></span>|
| <span data-ttu-id="270d7-294">text</span><span class="sxs-lookup"><span data-stu-id="270d7-294">text</span></span> | <span data-ttu-id="270d7-295">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="270d7-295">Rich text</span></span> | <span data-ttu-id="270d7-296">Text wird unter dem Untertitel angezeigt.</span><span class="sxs-lookup"><span data-stu-id="270d7-296">Text appears under the subtitle.</span></span> <span data-ttu-id="270d7-297">Formatierungsoptionen finden Sie unter [Kartenformatierung.](~/task-modules-and-cards/cards/cards-format.md)</span><span class="sxs-lookup"><span data-stu-id="270d7-297">For formatting options, see [card formatting](~/task-modules-and-cards/cards/cards-format.md).</span></span> |
| <span data-ttu-id="270d7-298">Bilder</span><span class="sxs-lookup"><span data-stu-id="270d7-298">images</span></span> | <span data-ttu-id="270d7-299">Array von Bildern</span><span class="sxs-lookup"><span data-stu-id="270d7-299">Array of images</span></span> | <span data-ttu-id="270d7-300">Bild, das oben auf der Karte angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="270d7-300">Image displayed at the top of the card.</span></span> <span data-ttu-id="270d7-301">Seitenverhältnis 16:9.</span><span class="sxs-lookup"><span data-stu-id="270d7-301">Aspect ratio 16:9.</span></span> |
| <span data-ttu-id="270d7-302">Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="270d7-302">buttons</span></span> | <span data-ttu-id="270d7-303">Array von Aktionsobjekten</span><span class="sxs-lookup"><span data-stu-id="270d7-303">Array of action objects</span></span> | <span data-ttu-id="270d7-304">Aktionssatz, der für die aktuelle Karte gilt.</span><span class="sxs-lookup"><span data-stu-id="270d7-304">Set of actions applicable to the current card.</span></span> <span data-ttu-id="270d7-305">Maximal sechs.</span><span class="sxs-lookup"><span data-stu-id="270d7-305">Maximum six.</span></span> |
| <span data-ttu-id="270d7-306">Tippen</span><span class="sxs-lookup"><span data-stu-id="270d7-306">tap</span></span> | <span data-ttu-id="270d7-307">Action-Objekt</span><span class="sxs-lookup"><span data-stu-id="270d7-307">Action object</span></span> | <span data-ttu-id="270d7-308">Wird aktiviert, wenn der Benutzer auf die Karte selbst tippt.</span><span class="sxs-lookup"><span data-stu-id="270d7-308">Activated when the user taps on the card itself.</span></span> |

### <a name="example-of-a-hero-card"></a><span data-ttu-id="270d7-309">Beispiel für eine Hero-Karte</span><span class="sxs-lookup"><span data-stu-id="270d7-309">Example of a hero card</span></span>

![Beispiel für eine Hero-Karte](~/assets/images/cards/hero.png)

<span data-ttu-id="270d7-311">Der folgende Code zeigt ein Beispiel für eine Hero-Karte:</span><span class="sxs-lookup"><span data-stu-id="270d7-311">The following code shows an example of a hero card:</span></span>

```json
{
   "contentType": "application/vnd.microsoft.card.hero",
   "content": {
     "title": "Seattle Center Monorail",
     "subtitle": "Seattle Center Monorail",
     "text": "The Seattle Center Monorail is an elevated train line between Seattle Center (near the Space Needle) and downtown Seattle. It was built for the 1962 World's Fair. Its original two trains, completed in 1961, are still in service.",
     "images": [
       {
         "url":"https://upload.wikimedia.org/wikipedia/commons/thumb/4/49/Seattle_monorail01_2008-02-25.jpg/1024px-Seattle_monorail01_2008-02-25.jpg"
       }
     ],
    "buttons": [
      {
         "type": "openUrl",
         "title": "Official website",
         "value": "https://www.seattlemonorail.com"
       },
      {
        "type": "openUrl",
        "title": "Wikipeda page",
        "value": "https://en.wikipedia.org/wiki/Seattle_Center_Monorail"
       }
     ]
   }
}

```

### <a name="additional-information-on-hero-cards"></a><span data-ttu-id="270d7-312">Zusätzliche Informationen zu Favoritenkarten</span><span class="sxs-lookup"><span data-stu-id="270d7-312">Additional information on hero cards</span></span>

<span data-ttu-id="270d7-313">Bot Framework-Referenz:</span><span class="sxs-lookup"><span data-stu-id="270d7-313">Bot Framework reference:</span></span>

* [<span data-ttu-id="270d7-314">Hero-Karte Node.js</span><span class="sxs-lookup"><span data-stu-id="270d7-314">Hero card Node.js</span></span>](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=javascript#send-a-hero-card&preserve-view=true)
* [<span data-ttu-id="270d7-315">Hero-Karte C #</span><span class="sxs-lookup"><span data-stu-id="270d7-315">Hero card C#</span></span>](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-a-hero-card&preserve-view=true)

## <a name="list-card"></a><span data-ttu-id="270d7-316">Karte auflisten</span><span class="sxs-lookup"><span data-stu-id="270d7-316">List card</span></span>

<span data-ttu-id="270d7-317">Die Listenkarte wurde von Teams hinzugefügt, um Funktionen bereitzustellen, die über das hinausgeht, was die Listensammlung bereitstellen kann.</span><span class="sxs-lookup"><span data-stu-id="270d7-317">The list card has been added by Teams to provide functions beyond what the list collection can provide.</span></span> <span data-ttu-id="270d7-318">Die Listenkarte enthält eine Bildlaufliste mit Elementen.</span><span class="sxs-lookup"><span data-stu-id="270d7-318">The list card provides a scrolling list of items.</span></span>

### <a name="support-for-list-cards"></a><span data-ttu-id="270d7-319">Unterstützung für Listenkarten</span><span class="sxs-lookup"><span data-stu-id="270d7-319">Support for list cards</span></span>

<span data-ttu-id="270d7-320">Die folgende Tabelle enthält die Features, die Listenkarten unterstützen:</span><span class="sxs-lookup"><span data-stu-id="270d7-320">The following table provides the features that support list cards:</span></span>

| <span data-ttu-id="270d7-321">Bots in Teams</span><span class="sxs-lookup"><span data-stu-id="270d7-321">Bots in Teams</span></span> | <span data-ttu-id="270d7-322">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="270d7-322">Messaging extensions</span></span>  | <span data-ttu-id="270d7-323">Connectors</span><span class="sxs-lookup"><span data-stu-id="270d7-323">Connectors</span></span> | <span data-ttu-id="270d7-324">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="270d7-324">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="270d7-325">✔</span><span class="sxs-lookup"><span data-stu-id="270d7-325">✔</span></span> | <span data-ttu-id="270d7-326">✖</span><span class="sxs-lookup"><span data-stu-id="270d7-326">✖</span></span> | <span data-ttu-id="270d7-327">✖</span><span class="sxs-lookup"><span data-stu-id="270d7-327">✖</span></span> |<span data-ttu-id="270d7-328">✔</span><span class="sxs-lookup"><span data-stu-id="270d7-328">✔</span></span> |

### <a name="properties-of-a-list-card"></a><span data-ttu-id="270d7-329">Eigenschaften einer Listenkarte</span><span class="sxs-lookup"><span data-stu-id="270d7-329">Properties of a list card</span></span>

<span data-ttu-id="270d7-330">Die folgende Tabelle enthält die Eigenschaften einer Listenkarte:</span><span class="sxs-lookup"><span data-stu-id="270d7-330">The following table provides the properties of a list card:</span></span>

| <span data-ttu-id="270d7-331">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="270d7-331">Property</span></span> | <span data-ttu-id="270d7-332">Typ</span><span class="sxs-lookup"><span data-stu-id="270d7-332">Type</span></span>  | <span data-ttu-id="270d7-333">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="270d7-333">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="270d7-334">title</span><span class="sxs-lookup"><span data-stu-id="270d7-334">title</span></span> | <span data-ttu-id="270d7-335">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="270d7-335">Rich text</span></span> | <span data-ttu-id="270d7-336">Titel der Karte.</span><span class="sxs-lookup"><span data-stu-id="270d7-336">Title of the card.</span></span> <span data-ttu-id="270d7-337">Maximal 2 Zeilen.</span><span class="sxs-lookup"><span data-stu-id="270d7-337">Maximum 2 lines.</span></span>|
| <span data-ttu-id="270d7-338">Elemente</span><span class="sxs-lookup"><span data-stu-id="270d7-338">items</span></span> | <span data-ttu-id="270d7-339">Array von Listenelementen</span><span class="sxs-lookup"><span data-stu-id="270d7-339">Array of list items</span></span> | <span data-ttu-id="270d7-340">Satz von Elementen, die auf die Karte anwendbar sind.</span><span class="sxs-lookup"><span data-stu-id="270d7-340">Set of items applicable to the card.</span></span>|
| <span data-ttu-id="270d7-341">Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="270d7-341">buttons</span></span> | <span data-ttu-id="270d7-342">Array von Aktionsobjekten</span><span class="sxs-lookup"><span data-stu-id="270d7-342">Array of action objects</span></span> | <span data-ttu-id="270d7-343">Aktionssatz, der für die aktuelle Karte gilt.</span><span class="sxs-lookup"><span data-stu-id="270d7-343">Set of actions applicable to the current card.</span></span> <span data-ttu-id="270d7-344">Maximal 6.</span><span class="sxs-lookup"><span data-stu-id="270d7-344">Maximum 6.</span></span> |

### <a name="example-of-a-list-card"></a><span data-ttu-id="270d7-345">Beispiel für eine Listenkarte</span><span class="sxs-lookup"><span data-stu-id="270d7-345">Example of a list card</span></span>

<span data-ttu-id="270d7-346">Der folgende Code zeigt ein Beispiel für eine Listenkarte:</span><span class="sxs-lookup"><span data-stu-id="270d7-346">The following code shows an example of a list card:</span></span>

```json
{
  "contentType": "application/vnd.microsoft.teams.card.list",
  "content": {
    "title": "Card title",
    "items": [
      {
        "type": "file",
        "id": "https://contoso.sharepoint.com/teams/new/Shared%20Documents/Report.xlsx",
        "title": "Report",
        "subtitle": "teams > new > design",
        "tap": {
          "type": "imBack",
          "value": "editOnline https://contoso.sharepoint.com/teams/new/Shared%20Documents/Report.xlsx"
        }
      },
      {
        "type": "resultItem",
        "icon": "https://cdn2.iconfinder.com/data/icons/social-icons-33/128/Trello-128.png",
        "title": "Trello title",
        "subtitle": "A Trello subtitle",
        "tap": {
          "type": "openUrl",
          "value": "http://trello.com"
        }
      },
      {
        "type": "section",
        "title": "Manager"
      },
      {
        "type": "person",
        "id": "JohnDoe@contoso.com",
        "title": "John Doe",
        "subtitle": "Manager",
        "tap": {
          "type": "imBack",
          "value": "whois JohnDoe@contoso.com"
        }
      }
    ],
    "buttons": [
      {
        "type": "imBack",
        "title": "Select",
        "value": "whois"
      }
    ]
  }
}
```

## <a name="office-365-connector-card"></a><span data-ttu-id="270d7-347">Office 365-Connectorkarte</span><span class="sxs-lookup"><span data-stu-id="270d7-347">Office 365 connector card</span></span>

<span data-ttu-id="270d7-348">Sie können mit einer Office 365 Connector-Karte arbeiten, die ein flexibles Layout bietet und eine hervorragende Möglichkeit darstellt, nützliche Informationen zu erhalten.</span><span class="sxs-lookup"><span data-stu-id="270d7-348">You can work with an Office 365 Connector card that provides a flexible layout and is a great way to get useful information.</span></span> <span data-ttu-id="270d7-349">Die Office 365 Connectorkarte wird in Teams und nicht im Bot Framework unterstützt.</span><span class="sxs-lookup"><span data-stu-id="270d7-349">The Office 365 connector card is supported in Teams, not in Bot Framework.</span></span> <span data-ttu-id="270d7-350">Diese Karte bietet ein flexibles Layout mit mehreren Abschnitten, Feldern, Bildern und Aktionen.</span><span class="sxs-lookup"><span data-stu-id="270d7-350">This card provides a flexible layout with multiple sections, fields, images, and actions.</span></span> <span data-ttu-id="270d7-351">Diese Karte enthält eine Connectorkarte, sodass sie von Bots verwendet werden kann.</span><span class="sxs-lookup"><span data-stu-id="270d7-351">This card contains a connector card so that it can be used by bots.</span></span> <span data-ttu-id="270d7-352">Informationen zu den Unterschieden zwischen Connectorkarten und der Office 365 Connector-Karte finden Sie unter [zusätzliche Informationen auf der Office 365 Connector-Karte.](#additional-information-on-the-office-365-connector-card)</span><span class="sxs-lookup"><span data-stu-id="270d7-352">For differences between connector cards and the Office 365 Connector card, see [Additional information on the Office 365 Connector card](#additional-information-on-the-office-365-connector-card).</span></span>

### <a name="support-for-office-365-connector-cards"></a><span data-ttu-id="270d7-353">Unterstützung für Office 365 Connectorkarten</span><span class="sxs-lookup"><span data-stu-id="270d7-353">Support for Office 365 Connector cards</span></span>

<span data-ttu-id="270d7-354">Die folgende Tabelle enthält die Features, die Office 365 Connectorkarten unterstützen:</span><span class="sxs-lookup"><span data-stu-id="270d7-354">The following table provides the features that support Office 365 Connector cards:</span></span>

| <span data-ttu-id="270d7-355">Bots in Teams</span><span class="sxs-lookup"><span data-stu-id="270d7-355">Bots in Teams</span></span> | <span data-ttu-id="270d7-356">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="270d7-356">Messaging extensions</span></span>  | <span data-ttu-id="270d7-357">Connectors</span><span class="sxs-lookup"><span data-stu-id="270d7-357">Connectors</span></span> | <span data-ttu-id="270d7-358">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="270d7-358">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="270d7-359">✔</span><span class="sxs-lookup"><span data-stu-id="270d7-359">✔</span></span> | <span data-ttu-id="270d7-360">✔</span><span class="sxs-lookup"><span data-stu-id="270d7-360">✔</span></span> | <span data-ttu-id="270d7-361">✔</span><span class="sxs-lookup"><span data-stu-id="270d7-361">✔</span></span> | <span data-ttu-id="270d7-362">✖</span><span class="sxs-lookup"><span data-stu-id="270d7-362">✖</span></span> |

### <a name="properties-of-the-office-365-connector-card"></a><span data-ttu-id="270d7-363">Eigenschaften der Office 365-Connectorkarte</span><span class="sxs-lookup"><span data-stu-id="270d7-363">Properties of the Office 365 Connector card</span></span>

<span data-ttu-id="270d7-364">Die folgende Tabelle enthält die Eigenschaften der Office 365-Connectorkarte:</span><span class="sxs-lookup"><span data-stu-id="270d7-364">The following table provides the properties of the Office 365 connector card:</span></span>

| <span data-ttu-id="270d7-365">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="270d7-365">Property</span></span> | <span data-ttu-id="270d7-366">Typ</span><span class="sxs-lookup"><span data-stu-id="270d7-366">Type</span></span>  | <span data-ttu-id="270d7-367">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="270d7-367">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="270d7-368">title</span><span class="sxs-lookup"><span data-stu-id="270d7-368">title</span></span> | <span data-ttu-id="270d7-369">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="270d7-369">Rich text</span></span> | <span data-ttu-id="270d7-370">Titel der Karte.</span><span class="sxs-lookup"><span data-stu-id="270d7-370">Title of the card.</span></span> <span data-ttu-id="270d7-371">Maximal zwei Zeilen.</span><span class="sxs-lookup"><span data-stu-id="270d7-371">Maximum two lines.</span></span> |
| <span data-ttu-id="270d7-372">Zusammenfassung</span><span class="sxs-lookup"><span data-stu-id="270d7-372">summary</span></span> | <span data-ttu-id="270d7-373">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="270d7-373">Rich text</span></span> | <span data-ttu-id="270d7-374">Zusammenfassung der Karte.</span><span class="sxs-lookup"><span data-stu-id="270d7-374">Summary of the card.</span></span> <span data-ttu-id="270d7-375">Maximal zwei Zeilen.</span><span class="sxs-lookup"><span data-stu-id="270d7-375">Maximum two lines.</span></span> |
| <span data-ttu-id="270d7-376">text</span><span class="sxs-lookup"><span data-stu-id="270d7-376">text</span></span> | <span data-ttu-id="270d7-377">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="270d7-377">Rich text</span></span> | <span data-ttu-id="270d7-378">Text wird unter dem Untertitel angezeigt.</span><span class="sxs-lookup"><span data-stu-id="270d7-378">Text appears under the subtitle.</span></span> <span data-ttu-id="270d7-379">Formatierungsoptionen finden Sie unter [Kartenformatierung.](~/task-modules-and-cards/cards/cards-format.md)</span><span class="sxs-lookup"><span data-stu-id="270d7-379">For formatting options, see [card formatting](~/task-modules-and-cards/cards/cards-format.md).</span></span> |
| <span data-ttu-id="270d7-380">themeColor</span><span class="sxs-lookup"><span data-stu-id="270d7-380">themeColor</span></span> | <span data-ttu-id="270d7-381">HEX-Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="270d7-381">HEX string</span></span> | <span data-ttu-id="270d7-382">Farbe, die die `accentColor` aus dem Anwendungsmanifest bereitgestellte Überschreibung überschreibt.</span><span class="sxs-lookup"><span data-stu-id="270d7-382">Color that overrides the `accentColor` provided from the application manifest.</span></span> |

### <a name="additional-information-on-the-office-365-connector-card"></a><span data-ttu-id="270d7-383">Zusätzliche Informationen auf der Office 365 Connectorkarte</span><span class="sxs-lookup"><span data-stu-id="270d7-383">Additional information on the Office 365 Connector card</span></span>

<span data-ttu-id="270d7-384">Office 365 Connectorkarten funktionieren ordnungsgemäß in Microsoft Teams, einschließlich [ `ActionCard` Aktionen.](/outlook/actionable-messages/card-reference#actioncard-action)</span><span class="sxs-lookup"><span data-stu-id="270d7-384">Office 365 Connector cards function properly in Microsoft Teams, including [`ActionCard` actions](/outlook/actionable-messages/card-reference#actioncard-action).</span></span>

<span data-ttu-id="270d7-385">Der wichtige Unterschied zwischen der Verwendung von Connectorkarten aus einem Connector und der Verwendung von Connectorkarten in Ihrem Bot besteht in der Behandlung von Kartenaktionen.</span><span class="sxs-lookup"><span data-stu-id="270d7-385">The important difference between using connector cards from a connector and using connector cards in your bot is the handling of card actions.</span></span> <span data-ttu-id="270d7-386">In der folgenden Tabelle sind die Unterschiede aufgeführt:</span><span class="sxs-lookup"><span data-stu-id="270d7-386">The following table lists the difference:</span></span>

| <span data-ttu-id="270d7-387">Connector</span><span class="sxs-lookup"><span data-stu-id="270d7-387">Connector</span></span> | <span data-ttu-id="270d7-388">Bot</span><span class="sxs-lookup"><span data-stu-id="270d7-388">Bot</span></span> |
| --- | --- |
| <span data-ttu-id="270d7-389">Der Endpunkt empfängt die Kartennutzlast über HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="270d7-389">The endpoint receives the card payload through HTTP POST.</span></span> | <span data-ttu-id="270d7-390">Die `HttpPOST` Aktion löst eine Aktivität `invoke` aus, die nur die Aktions-ID und den Textkörper an den Bot sendet.</span><span class="sxs-lookup"><span data-stu-id="270d7-390">The `HttpPOST` action triggers an `invoke` activity that sends only the action ID and body to the bot.</span></span>|

<span data-ttu-id="270d7-391">Jede Connectorkarte kann maximal zehn Abschnitte anzeigen, und jeder Abschnitt kann maximal fünf Bilder und fünf Aktionen enthalten.</span><span class="sxs-lookup"><span data-stu-id="270d7-391">Each connector card can display a maximum of ten sections, and each section can contain a maximum of five images and five actions.</span></span>

> [!NOTE]
> <span data-ttu-id="270d7-392">Alle zusätzlichen Abschnitte, Bilder oder Aktionen in einer Nachricht werden nicht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="270d7-392">Any additional sections, images, or actions in a message do not appear.</span></span>

<span data-ttu-id="270d7-393">Alle Textfelder unterstützen Markdown und HTML.</span><span class="sxs-lookup"><span data-stu-id="270d7-393">All text fields support Markdown and HTML.</span></span> <span data-ttu-id="270d7-394">Sie können steuern, welche Abschnitte Markdown oder HTML verwenden, indem Sie die `markdown` Eigenschaft in einer Nachricht festlegen.</span><span class="sxs-lookup"><span data-stu-id="270d7-394">You can control which sections use Markdown or HTML by setting the `markdown` property in a message.</span></span> <span data-ttu-id="270d7-395">Standardmäßig `markdown` ist auf `true` .</span><span class="sxs-lookup"><span data-stu-id="270d7-395">By default, `markdown` is set to `true`.</span></span> <span data-ttu-id="270d7-396">Wenn Sie stattdessen HTML verwenden möchten, legen Sie `markdown` dies auf `false` fest.</span><span class="sxs-lookup"><span data-stu-id="270d7-396">If you want to use HTML instead, set `markdown` to `false`.</span></span>

<span data-ttu-id="270d7-397">Wenn Sie die `themeColor` Eigenschaft angeben, überschreibt sie die `accentColor` Eigenschaft im App-Manifest.</span><span class="sxs-lookup"><span data-stu-id="270d7-397">If you specify the `themeColor` property, it overrides the `accentColor` property in the app manifest.</span></span>

<span data-ttu-id="270d7-398">Um den Renderingstil für `activityImage` anzugeben, können Sie `activityImageType` wie in der folgenden Tabelle dargestellt festlegen:</span><span class="sxs-lookup"><span data-stu-id="270d7-398">To specify the rendering style for `activityImage`, you can set `activityImageType` as shown in the following table:</span></span>

| <span data-ttu-id="270d7-399">Wert</span><span class="sxs-lookup"><span data-stu-id="270d7-399">Value</span></span> | <span data-ttu-id="270d7-400">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="270d7-400">Description</span></span> |
| --- | --- |
| `avatar` | <span data-ttu-id="270d7-401">Standard, `activityImage` wird als Kreis zugeschnitten.</span><span class="sxs-lookup"><span data-stu-id="270d7-401">Default, `activityImage` is cropped as a circle.</span></span> |
| `article` | <span data-ttu-id="270d7-402">`activityImage` wird als Rechteck angezeigt und behält das Seitenverhältnis bei.</span><span class="sxs-lookup"><span data-stu-id="270d7-402">`activityImage` is displayed as a rectangle and retains its aspect ratio.</span></span> |

<span data-ttu-id="270d7-403">Weitere Informationen zu den Eigenschaften der Connectorkarte finden Sie unter [Referenz zu Nachrichtenkarten](/outlook/actionable-messages/card-reference)mit Aktionen.</span><span class="sxs-lookup"><span data-stu-id="270d7-403">For all other details about connector card properties, see [actionable message card reference](/outlook/actionable-messages/card-reference).</span></span> <span data-ttu-id="270d7-404">Die einzigen Connectorkarteneigenschaften, die Teams derzeit nicht unterstützen, sind:</span><span class="sxs-lookup"><span data-stu-id="270d7-404">The only connector card properties that Teams does not currently support are as follows:</span></span>

* `heroImage`
* `hideOriginalBody`
* <span data-ttu-id="270d7-405">`startGroup`immer wie in Teams behandelt `true`</span><span class="sxs-lookup"><span data-stu-id="270d7-405">`startGroup` always treated as `true` in Teams</span></span>
* `originator`
* `correlationId`

### <a name="example-of-an-office-365-connector-card"></a><span data-ttu-id="270d7-406">Beispiel für eine Office 365-Connectorkarte</span><span class="sxs-lookup"><span data-stu-id="270d7-406">Example of an Office 365 Connector card</span></span>

<span data-ttu-id="270d7-407">Der folgende Code zeigt ein Beispiel für eine Office 365 Connectorkarte:</span><span class="sxs-lookup"><span data-stu-id="270d7-407">The following code shows an example of an Office 365 Connector card:</span></span>

```json
{
  "contentType": "application/vnd.microsoft.teams.card.o365connector",
  "content": {
    "@type": "MessageCard",
    "@context": "http://schema.org/extensions",
    "summary": "John Doe commented on Trello",
    "title": "Project Tango",
    "sections": [
        {
            "activityTitle": "John Doe commented",
            "activitySubtitle": "On Project Tango",
            "activityText": "\"Here are the designs\"",
            "activityImage": "http://connectorsdemo.azurewebsites.net/images/MSC12_Oscar_002.jpg"
        },
        {
            "title": "Details",
            "facts": [
                {
                    "name": "Labels",
                    "value": "Designs, redlines"
                },
                {
                    "name": "Due date",
                    "value": "Dec 7, 2016"
                },
                {
                    "name": "Attachments",
                    "value": "[final.jpg](http://connectorsdemo.azurewebsites.net/images/WIN14_Jan_04.jpg)"
                }
            ]
        },
        {
            "title": "Images",
            "images": [
                {
                    "image":"http://connectorsdemo.azurewebsites.net/images/MicrosoftSurface_024_Cafe_OH-06315_VS_R1c.jpg"
                },
                {
                    "image":"http://connectorsdemo.azurewebsites.net/images/WIN12_Scene_01.jpg"
                },
                {
                    "image":"http://connectorsdemo.azurewebsites.net/images/WIN12_Anthony_02.jpg"
                }
            ]
        }
    ],
    "potentialAction": [
        {
            "@context": "http://schema.org",
            "@type": "ViewAction",
            "name": "View in Trello",
            "target": [
                "https://trello.com/c/1101/"
            ]
        }
    ]
  }
}
```

## <a name="receipt-card"></a><span data-ttu-id="270d7-408">Belegkarte</span><span class="sxs-lookup"><span data-stu-id="270d7-408">Receipt card</span></span>

<span data-ttu-id="270d7-409">Teams unterstützt die Belegkarte.</span><span class="sxs-lookup"><span data-stu-id="270d7-409">Teams supports receipt card.</span></span> <span data-ttu-id="270d7-410">Es handelt sich um eine Karte, die es einem Bot ermöglicht, dem Benutzer einen Beleg bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="270d7-410">It is a card that enables a bot to provide a receipt to the user.</span></span> <span data-ttu-id="270d7-411">Es enthält in der Regel die Liste der Elemente, die in den Beleg aufgenommen werden sollen, z. B. Steuer- und Gesamtinformationen.</span><span class="sxs-lookup"><span data-stu-id="270d7-411">It typically contains the list of items to include on the receipt, such as tax and total information.</span></span>

### <a name="support-for-receipt-cards"></a><span data-ttu-id="270d7-412">Unterstützung für Belegkarten</span><span class="sxs-lookup"><span data-stu-id="270d7-412">Support for receipt cards</span></span>

<span data-ttu-id="270d7-413">Die folgende Tabelle enthält die Features, die Belegkarten unterstützen:</span><span class="sxs-lookup"><span data-stu-id="270d7-413">The following table provides the features that support receipt cards:</span></span>

| <span data-ttu-id="270d7-414">Bots in Teams</span><span class="sxs-lookup"><span data-stu-id="270d7-414">Bots in Teams</span></span> | <span data-ttu-id="270d7-415">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="270d7-415">Messaging extensions</span></span>  | <span data-ttu-id="270d7-416">Connectors</span><span class="sxs-lookup"><span data-stu-id="270d7-416">Connectors</span></span> | <span data-ttu-id="270d7-417">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="270d7-417">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="270d7-418">✔</span><span class="sxs-lookup"><span data-stu-id="270d7-418">✔</span></span> | <span data-ttu-id="270d7-419">✔</span><span class="sxs-lookup"><span data-stu-id="270d7-419">✔</span></span> | <span data-ttu-id="270d7-420">✖</span><span class="sxs-lookup"><span data-stu-id="270d7-420">✖</span></span> | <span data-ttu-id="270d7-421">✔</span><span class="sxs-lookup"><span data-stu-id="270d7-421">✔</span></span> |

### <a name="example-of-a-receipt-card"></a><span data-ttu-id="270d7-422">Beispiel für eine Belegkarte</span><span class="sxs-lookup"><span data-stu-id="270d7-422">Example of a receipt card</span></span>

![Beispiel für eine Belegkarte](~/assets/images/cards/receipt.png)

<span data-ttu-id="270d7-424">Der folgende Code zeigt ein Beispiel für eine Belegkarte:</span><span class="sxs-lookup"><span data-stu-id="270d7-424">The following code shows an example of a receipt card:</span></span>

```json
{
  "contentType": "application/vnd.microsoft.card.receipt",
  "content": {
    "title": "John Doe",
    "facts": [
      {
        "key": "Order Number",
        "value": "1234"
      },
      {
        "key": "Payment Method",
        "value": "VISA 5555-****"
      }
    ],
    "items": [
      {
        "title": "Data Transfer",
        "image": {
          "url": "https://github.com/amido/azure-vector-icons/raw/master/renders/traffic-manager.png"
        },
        "price": "$ 38.45",
        "quantity": "368"
      },
      {
        "title": "App Service",
        "image": {
          "url": "https://github.com/amido/azure-vector-icons/raw/master/renders/cloud-service.png"
        },
        "price": "$ 45.00",
        "quantity": "720"
      }
    ],
    "total": "$ 90.95",
    "tax": "$ 7.50",
    "buttons": [
      {
        "type": "openUrl",
        "title": "More information",
        "image": "https://account.windowsazure.com/content/6.10.1.38-.8225.160809-1618/aux-pre/images/offer-icon-freetrial.png",
        "value": "https://azure.microsoft.com/en-us/pricing/"
      }
    ]
  }
}
```

### <a name="additional-information-on-receipt-cards"></a><span data-ttu-id="270d7-425">Zusätzliche Informationen zu Belegkarten</span><span class="sxs-lookup"><span data-stu-id="270d7-425">Additional information on receipt cards</span></span>

<span data-ttu-id="270d7-426">Bot Framework-Referenz:</span><span class="sxs-lookup"><span data-stu-id="270d7-426">Bot Framework reference:</span></span>

* [<span data-ttu-id="270d7-427">Belegkarte Node.js</span><span class="sxs-lookup"><span data-stu-id="270d7-427">Receipt card Node.js</span></span>](/javascript/api/botframework-schema/receiptcard?view=botbuilder-ts-latest&preserve-view=true)
* [<span data-ttu-id="270d7-428">Belegkarte C #</span><span class="sxs-lookup"><span data-stu-id="270d7-428">Receipt card C#</span></span>](/dotnet/api/microsoft.bot.schema.receiptcard?view=botbuilder-dotnet-stable&preserve-view=true)

## <a name="signin-card"></a><span data-ttu-id="270d7-429">Anmeldekarte</span><span class="sxs-lookup"><span data-stu-id="270d7-429">Signin card</span></span>

<span data-ttu-id="270d7-430">Die Anmeldekarte in Teams ähnelt der Anmeldekarte im Bot Framework, mit der Ausnahme, dass die Anmeldekarte in Teams nur zwei Aktionen `signin` unterstützt und `openUrl` .</span><span class="sxs-lookup"><span data-stu-id="270d7-430">The signin card in Teams is similar to the signin card in the Bot Framework except that the signin card in Teams only supports two actions `signin` and `openUrl`.</span></span>

<span data-ttu-id="270d7-431">Die Anmeldeaktion kann von einer beliebigen Karte in Teams verwendet werden, nicht nur von der Anmeldekarte.</span><span class="sxs-lookup"><span data-stu-id="270d7-431">The signin action can be used from any card in Teams, not just the signin card.</span></span> <span data-ttu-id="270d7-432">Weitere Informationen finden Sie unter [Teams Authentifizierungsfluss für Bots.](~/bots/how-to/authentication/auth-flow-bot.md)</span><span class="sxs-lookup"><span data-stu-id="270d7-432">For more information, see [Teams authentication flow for bots](~/bots/how-to/authentication/auth-flow-bot.md).</span></span>

### <a name="support-for-signin-cards"></a><span data-ttu-id="270d7-433">Unterstützung für Anmeldekarten</span><span class="sxs-lookup"><span data-stu-id="270d7-433">Support for signin cards</span></span>

<span data-ttu-id="270d7-434">Die folgende Tabelle enthält die Features, die Anmeldekarten unterstützen:</span><span class="sxs-lookup"><span data-stu-id="270d7-434">The following table provides the features that support signin cards:</span></span>

| <span data-ttu-id="270d7-435">Bots in Teams</span><span class="sxs-lookup"><span data-stu-id="270d7-435">Bots in Teams</span></span> | <span data-ttu-id="270d7-436">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="270d7-436">Messaging extensions</span></span>  | <span data-ttu-id="270d7-437">Connectors</span><span class="sxs-lookup"><span data-stu-id="270d7-437">Connectors</span></span> | <span data-ttu-id="270d7-438">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="270d7-438">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="270d7-439">✔</span><span class="sxs-lookup"><span data-stu-id="270d7-439">✔</span></span> | <span data-ttu-id="270d7-440">✖</span><span class="sxs-lookup"><span data-stu-id="270d7-440">✖</span></span> | <span data-ttu-id="270d7-441">✖</span><span class="sxs-lookup"><span data-stu-id="270d7-441">✖</span></span> | <span data-ttu-id="270d7-442">✔</span><span class="sxs-lookup"><span data-stu-id="270d7-442">✔</span></span> |

### <a name="additional-information-on-signin-cards"></a><span data-ttu-id="270d7-443">Zusätzliche Informationen zu Anmeldekarten</span><span class="sxs-lookup"><span data-stu-id="270d7-443">Additional information on signin cards</span></span>

<span data-ttu-id="270d7-444">Bot Framework-Referenz:</span><span class="sxs-lookup"><span data-stu-id="270d7-444">Bot Framework reference:</span></span>

* [<span data-ttu-id="270d7-445">Anmeldekarten-Node.js</span><span class="sxs-lookup"><span data-stu-id="270d7-445">Signin card Node.js</span></span>](/javascript/api/botframework-schema/signincard?view=botbuilder-ts-latest&preserve-view=true)
* [<span data-ttu-id="270d7-446">Anmeldekarte C #</span><span class="sxs-lookup"><span data-stu-id="270d7-446">Signin card C#</span></span>](/dotnet/api/microsoft.bot.schema.signincard?view=botbuilder-dotnet-stable&preserve-view=true)

## <a name="thumbnail-card"></a><span data-ttu-id="270d7-447">Miniaturansichtskarte</span><span class="sxs-lookup"><span data-stu-id="270d7-447">Thumbnail card</span></span>

<span data-ttu-id="270d7-448">Sie können mit einer Miniaturansichtskarte arbeiten, die zum Senden einer einfachen Nachricht mit Aktionen verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="270d7-448">You can work with a thumbnail card that is used for sending a simple actionable message.</span></span> <span data-ttu-id="270d7-449">Eine Karte, die in der Regel ein einzelnes Miniaturbild, eine oder mehrere Schaltflächen und Text enthält.</span><span class="sxs-lookup"><span data-stu-id="270d7-449">A card that typically contains a single thumbnail image, one or more buttons, and text.</span></span>

### <a name="support-for-thumbnail-cards"></a><span data-ttu-id="270d7-450">Unterstützung für Miniaturansichtskarten</span><span class="sxs-lookup"><span data-stu-id="270d7-450">Support for thumbnail cards</span></span>

<span data-ttu-id="270d7-451">Die folgende Tabelle enthält die Features, die Miniaturansichtskarten unterstützen:</span><span class="sxs-lookup"><span data-stu-id="270d7-451">The following table provides the features that support thumbnail cards:</span></span>

| <span data-ttu-id="270d7-452">Bots in Teams</span><span class="sxs-lookup"><span data-stu-id="270d7-452">Bots in Teams</span></span> | <span data-ttu-id="270d7-453">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="270d7-453">Messaging extensions</span></span>  | <span data-ttu-id="270d7-454">Connectors</span><span class="sxs-lookup"><span data-stu-id="270d7-454">Connectors</span></span> | <span data-ttu-id="270d7-455">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="270d7-455">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="270d7-456">✔</span><span class="sxs-lookup"><span data-stu-id="270d7-456">✔</span></span> | <span data-ttu-id="270d7-457">✔</span><span class="sxs-lookup"><span data-stu-id="270d7-457">✔</span></span> | <span data-ttu-id="270d7-458">✖</span><span class="sxs-lookup"><span data-stu-id="270d7-458">✖</span></span> | <span data-ttu-id="270d7-459">✔</span><span class="sxs-lookup"><span data-stu-id="270d7-459">✔</span></span> |

![Beispiel für eine Miniaturansichtskarte](~/assets/images/cards/thumbnail.png)

### <a name="properties-of-a-thumbnail-card"></a><span data-ttu-id="270d7-461">Eigenschaften einer Miniaturansichtskarte</span><span class="sxs-lookup"><span data-stu-id="270d7-461">Properties of a thumbnail card</span></span>

<span data-ttu-id="270d7-462">Die folgende Tabelle enthält die Eigenschaften einer Miniaturansichtskarte:</span><span class="sxs-lookup"><span data-stu-id="270d7-462">The following table provides the properties of a thumbnail card:</span></span>

| <span data-ttu-id="270d7-463">Eigenschaft</span><span class="sxs-lookup"><span data-stu-id="270d7-463">Property</span></span> | <span data-ttu-id="270d7-464">Typ</span><span class="sxs-lookup"><span data-stu-id="270d7-464">Type</span></span>  | <span data-ttu-id="270d7-465">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="270d7-465">Description</span></span> |
| --- | --- | --- |
| <span data-ttu-id="270d7-466">title</span><span class="sxs-lookup"><span data-stu-id="270d7-466">title</span></span> | <span data-ttu-id="270d7-467">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="270d7-467">Rich text</span></span> | <span data-ttu-id="270d7-468">Titel der Karte.</span><span class="sxs-lookup"><span data-stu-id="270d7-468">Title of the card.</span></span> <span data-ttu-id="270d7-469">Maximal 2 Zeilen.</span><span class="sxs-lookup"><span data-stu-id="270d7-469">Maximum 2 lines.</span></span>|
| <span data-ttu-id="270d7-470">Untertitel</span><span class="sxs-lookup"><span data-stu-id="270d7-470">subtitle</span></span> | <span data-ttu-id="270d7-471">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="270d7-471">Rich text</span></span> | <span data-ttu-id="270d7-472">Untertitel der Karte.</span><span class="sxs-lookup"><span data-stu-id="270d7-472">Subtitle of the card.</span></span> <span data-ttu-id="270d7-473">Maximal 2 Zeilen.</span><span class="sxs-lookup"><span data-stu-id="270d7-473">Maximum 2 lines.</span></span>|
| <span data-ttu-id="270d7-474">text</span><span class="sxs-lookup"><span data-stu-id="270d7-474">text</span></span> | <span data-ttu-id="270d7-475">Rich-Text </span><span class="sxs-lookup"><span data-stu-id="270d7-475">Rich text</span></span> | <span data-ttu-id="270d7-476">Text wird unter dem Untertitel angezeigt.</span><span class="sxs-lookup"><span data-stu-id="270d7-476">Text appears under the subtitle.</span></span> <span data-ttu-id="270d7-477">Formatierungsoptionen finden Sie unter [Kartenformatierung.](~/task-modules-and-cards/cards/cards-format.md)</span><span class="sxs-lookup"><span data-stu-id="270d7-477">For formatting options, see [card formatting](~/task-modules-and-cards/cards/cards-format.md).</span></span> |
| <span data-ttu-id="270d7-478">Bilder</span><span class="sxs-lookup"><span data-stu-id="270d7-478">images</span></span> | <span data-ttu-id="270d7-479">Array von Bildern</span><span class="sxs-lookup"><span data-stu-id="270d7-479">Array of images</span></span> | <span data-ttu-id="270d7-480">Bild, das oben auf der Karte angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="270d7-480">Image displayed at the top of the card.</span></span> <span data-ttu-id="270d7-481">Seitenverhältnis 1:1 Quadrat.</span><span class="sxs-lookup"><span data-stu-id="270d7-481">Aspect ratio 1:1 square.</span></span> |
| <span data-ttu-id="270d7-482">Schaltflächen</span><span class="sxs-lookup"><span data-stu-id="270d7-482">buttons</span></span> | <span data-ttu-id="270d7-483">Array von Aktionsobjekten</span><span class="sxs-lookup"><span data-stu-id="270d7-483">Array of action objects</span></span> | <span data-ttu-id="270d7-484">Aktionssatz, der für die aktuelle Karte gilt.</span><span class="sxs-lookup"><span data-stu-id="270d7-484">Set of actions applicable to the current card.</span></span> <span data-ttu-id="270d7-485">Maximal 6.</span><span class="sxs-lookup"><span data-stu-id="270d7-485">Maximum 6.</span></span> |
| <span data-ttu-id="270d7-486">Tippen</span><span class="sxs-lookup"><span data-stu-id="270d7-486">tap</span></span> | <span data-ttu-id="270d7-487">Action-Objekt</span><span class="sxs-lookup"><span data-stu-id="270d7-487">Action object</span></span> | <span data-ttu-id="270d7-488">Wird aktiviert, wenn der Benutzer auf die Karte selbst tippt.</span><span class="sxs-lookup"><span data-stu-id="270d7-488">Activated when the user taps on the card itself.</span></span> |

### <a name="example-of-a-thumbnail-card"></a><span data-ttu-id="270d7-489">Beispiel für eine Miniaturansichtskarte</span><span class="sxs-lookup"><span data-stu-id="270d7-489">Example of a thumbnail card</span></span>

<span data-ttu-id="270d7-490">Der folgende Code zeigt ein Beispiel für eine Miniaturansichtskarte:</span><span class="sxs-lookup"><span data-stu-id="270d7-490">The following code shows an example of a thumbnail card:</span></span>

```json
{
  "contentType": "application/vnd.microsoft.card.thumbnail",
  "content": {
    "title": "Bender",
    "subtitle": "tale of a robot who dared to love",
    "text": "Bender Bending Rodríguez is a main character in the animated television series Futurama. He was created by series creators Matt Groening and David X. Cohen, and is voiced by John DiMaggio",
    "images": [
      {
        "url": "https://upload.wikimedia.org/wikipedia/en/a/a6/Bender_Rodriguez.png",
        "alt": "Bender Rodríguez"
      }
    ],
    "buttons": [
      {
        "type": "imBack",
        "title": "Thumbs Up",
        "image": "http://moopz.com/assets_c/2012/06/emoji-thumbs-up-150-thumb-autox125-140616.jpg",
        "value": "I like it"
      },
      {
        "type": "imBack",
        "title": "Thumbs Down",
        "image": "http://yourfaceisstupid.com/wp-content/uploads/2014/08/thumbs-down.png",
        "value": "I don't like it"
      },
      {
        "type": "openUrl",
        "title": "I feel lucky",
        "image": "http://thumb9.shutterstock.com/photos/thumb_large/683806/148441982.jpg",
        "value": "https://www.bing.com/images/search?q=bender&qpvt=bender&qpvt=bender&qpvt=bender&FORM=IGRE"
      }
    ],
    "tap": {
      "type": "imBack",
      "value": "Tapped it!"
    }
  }
}
```

### <a name="additional-information"></a><span data-ttu-id="270d7-491">Weitere Informationen</span><span class="sxs-lookup"><span data-stu-id="270d7-491">Additional information</span></span>

<span data-ttu-id="270d7-492">Bot Framework-Referenz:</span><span class="sxs-lookup"><span data-stu-id="270d7-492">Bot Framework reference:</span></span>

* [<span data-ttu-id="270d7-493">Miniaturansichtskarte Node.js</span><span class="sxs-lookup"><span data-stu-id="270d7-493">Thumbnail card Node.js</span></span>](/javascript/api/botframework-schema/thumbnailcard?view=botbuilder-ts-latest&preserve-view=true)
* [<span data-ttu-id="270d7-494">Miniaturansichtskarte C #</span><span class="sxs-lookup"><span data-stu-id="270d7-494">Thumbnail card C#</span></span>](/dotnet/api/microsoft.bot.schema.thumbnailcard?view=botbuilder-dotnet-stable&preserve-view=true)

## <a name="card-collections"></a><span data-ttu-id="270d7-495">Kartensammlungen</span><span class="sxs-lookup"><span data-stu-id="270d7-495">Card collections</span></span>

<span data-ttu-id="270d7-496">Sie können mit Kartensammlungen arbeiten, die Karussell- und Listensammlungen enthalten.</span><span class="sxs-lookup"><span data-stu-id="270d7-496">You can work with card collections that include carousel and list collections.</span></span> <span data-ttu-id="270d7-497">Teams unterstützt Kartensammlungen.</span><span class="sxs-lookup"><span data-stu-id="270d7-497">Teams supports card collections.</span></span> <span data-ttu-id="270d7-498">Kartensammlungen enthalten `builder.AttachmentLayout.carousel` und `builder.AttachmentLayout.list` .</span><span class="sxs-lookup"><span data-stu-id="270d7-498">Card collections include `builder.AttachmentLayout.carousel` and `builder.AttachmentLayout.list`.</span></span> <span data-ttu-id="270d7-499">Diese Sammlungen enthalten adaptive, Hero- oder Miniaturansichtskarten.</span><span class="sxs-lookup"><span data-stu-id="270d7-499">These collections contain Adaptive, hero, or thumbnail cards.</span></span>

### <a name="carousel-collection"></a><span data-ttu-id="270d7-500">Karussellsammlung</span><span class="sxs-lookup"><span data-stu-id="270d7-500">Carousel collection</span></span>

<span data-ttu-id="270d7-501">Das [Karusselllayout](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-a-carousel-of-cards&preserve-view=true) zeigt ein Karussell mit Karten, optional mit zugehörigen Aktionsschaltflächen.</span><span class="sxs-lookup"><span data-stu-id="270d7-501">The [carousel layout](/azure/bot-service/bot-builder-howto-add-media-attachments?view=azure-bot-service-4.0&tabs=csharp#send-a-carousel-of-cards&preserve-view=true) shows a carousel of cards, optionally with associated action buttons.</span></span>

#### <a name="support-for-carousel-collections"></a><span data-ttu-id="270d7-502">Unterstützung für Karussellsammlungen</span><span class="sxs-lookup"><span data-stu-id="270d7-502">Support for carousel collections</span></span>

<span data-ttu-id="270d7-503">Die folgende Tabelle enthält die Features, die Karussellsammlungen unterstützen:</span><span class="sxs-lookup"><span data-stu-id="270d7-503">The following table provides the features that support carousel collections:</span></span>

| <span data-ttu-id="270d7-504">Bots in Teams</span><span class="sxs-lookup"><span data-stu-id="270d7-504">Bots in Teams</span></span> | <span data-ttu-id="270d7-505">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="270d7-505">Messaging extensions</span></span>  | <span data-ttu-id="270d7-506">Connectors</span><span class="sxs-lookup"><span data-stu-id="270d7-506">Connectors</span></span> | <span data-ttu-id="270d7-507">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="270d7-507">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="270d7-508">✔</span><span class="sxs-lookup"><span data-stu-id="270d7-508">✔</span></span> | <span data-ttu-id="270d7-509">✖</span><span class="sxs-lookup"><span data-stu-id="270d7-509">✖</span></span> | <span data-ttu-id="270d7-510">✖</span><span class="sxs-lookup"><span data-stu-id="270d7-510">✖</span></span> | <span data-ttu-id="270d7-511">✔</span><span class="sxs-lookup"><span data-stu-id="270d7-511">✔</span></span> |

> [!NOTE]
> <span data-ttu-id="270d7-512">Ein Karussell kann maximal zehn Karten pro Nachricht anzeigen.</span><span class="sxs-lookup"><span data-stu-id="270d7-512">A carousel can display a maximum of ten cards per message.</span></span>

#### <a name="properties-of-a-carousel-card"></a><span data-ttu-id="270d7-513">Eigenschaften einer Karussellkarte</span><span class="sxs-lookup"><span data-stu-id="270d7-513">Properties of a carousel card</span></span>

<span data-ttu-id="270d7-514">Die Eigenschaften einer Karussellkarte sind identisch mit den Favoriten- und Miniaturansichtskarten.</span><span class="sxs-lookup"><span data-stu-id="270d7-514">Properties of a carousel card are same as the hero and thumbnail cards.</span></span>

#### <a name="example-of-a-carousel-collection"></a><span data-ttu-id="270d7-515">Beispiel für eine Karussellsammlung</span><span class="sxs-lookup"><span data-stu-id="270d7-515">Example of a carousel collection</span></span>

![Beispiel für ein Karussell von Karten](~/assets/images/cards/carousel.png)

<span data-ttu-id="270d7-517">Der folgende Code zeigt ein Beispiel für eine Karussellsammlung:</span><span class="sxs-lookup"><span data-stu-id="270d7-517">The following code shows an example of a carousel collection:</span></span>

```json
{
 "attachmentLayout": "carousel",
 "attachments":[
    {
      "contentType": "application/vnd.microsoft.card.adaptive",
      "content": {
        "type": "AdaptiveCard",
        "version": "1.0",
        "body": [
          {
            "type": "Container",
            "items": [
              {
                "type": "TextBlock",
                "size": "extraLarge",
                "weight": "bolder",
                "text": "Welcome to Employee Connect",
                "height": "stretch"
              },
              {
                "type": "TextBlock",
                "size": "medium",
                "weight": "bolder",
                "text": "Add events to your calendar",
                "height": "stretch"
              },
              {
                "type": "TextBlock",
                "weight": "bolder",
                "text": "The bot can send \r\rnotification to remind \r\ryou about the latest \r\revents and trainings.",
                "wrap": true,
                "height": "stretch"
              },
              {
                "type": "ColumnSet",
                "columns": [
                  {
                    "type": "Column",
                    "items": [],
                    "height": "stretch"
                  }
                ]
              },
              {
                "type": "ColumnSet",
                "columns": [
                  {
                    "type": "Column",
                    "items": [],
                    "height": "stretch"
                  }
                ]
              }
            ]
          }
        ],
        "actions": [
          {
            "type": "Action.Submit",
            "title": "Let's get started"
          }
        ]
      }
    },
    {
      "contentType": "application/vnd.microsoft.card.adaptive",
      "content": {
        "type": "AdaptiveCard",
        "version": "1.2",
        "body": [
          {
            "type": "Container",
            "items": [
              {
                "type": "TextBlock",
                "size": "large",
                "weight": "bolder",
                "text": "Employee connect"
              },
              {
                "type": "TextBlock",
                "text": "The bot can send notifications \r\rto remind you about the latest \r\r events and trainings",
                "wrap": true,
                "maxWidth": 2
              },
              {
                "type": "ColumnSet",
                "columns": [
                  {
                    "type": "Column",
                    "items": [],
                    "height": "stretch"
                  }
                ]
              },
              {
                "type": "ColumnSet",
                "columns": [
                  {
                    "type": "Column",
                    "items": [],
                    "height": "stretch"
                  }
                ]
              }
            ]
          }
        ],
        "actions": [
          {
            "type": "Action.Submit",
            "title": "Let's get started"
          }
        ]
      }
    },
    {
      "contentType": "application/vnd.microsoft.card.adaptive",
      "content": {
        "type": "AdaptiveCard",
        "version": "1.0",
        "body": [
          {
            "type": "Container",
            "items": [
              {
                "type": "TextBlock",
                "size": "large",
                "weight": "bolder",
                "text": "Employee Connect final"
              },
              {
                "type": "TextBlock",
                "weight": "bolder",
                "text": "Create and manage your tasks",
                "wrap": true
              },
              {
                "type": "TextBlock",
                "text": "The app identifies all your pending tasks \r\r and helps you manage everything at \r\r one place.",
                "wrap": true
              },
              {
                "type": "TextBlock",
                "weight": "bolder",
                "text": "Try these commands \r\r- Pending Submissions \r\r- Pending Approvals- My Tools",
                "wrap": true,
                "height": "stretch"
              }
            ]
          }
        ],
        "actions": [
          {
            "type": "Action.Submit",
            "title": "Let's get started"
          }
        ]
      }
    }
  ]
}
```

#### <a name="syntax-for-carousel-collections"></a><span data-ttu-id="270d7-518">Syntax für Karussellsammlungen</span><span class="sxs-lookup"><span data-stu-id="270d7-518">Syntax for carousel collections</span></span>

<span data-ttu-id="270d7-519">`builder.AttachmentLayoutTypes.Carousel` ist die Syntax für Karussellsammlungen.</span><span class="sxs-lookup"><span data-stu-id="270d7-519">`builder.AttachmentLayoutTypes.Carousel` is the syntax for carousel collections.</span></span>

### <a name="list-collection"></a><span data-ttu-id="270d7-520">Sammlung auflisten</span><span class="sxs-lookup"><span data-stu-id="270d7-520">List collection</span></span>

<span data-ttu-id="270d7-521">Das Listenlayout zeigt eine vertikal gestapelte Liste von Karten, optional mit zugehörigen Aktionsschaltflächen.</span><span class="sxs-lookup"><span data-stu-id="270d7-521">The list layout shows a vertically stacked list of cards, optionally with associated action buttons.</span></span>

#### <a name="support-for-list-collections"></a><span data-ttu-id="270d7-522">Unterstützung für Listensammlungen</span><span class="sxs-lookup"><span data-stu-id="270d7-522">Support for list collections</span></span>

<span data-ttu-id="270d7-523">Die folgende Tabelle enthält die Features, die Listensammlungen unterstützen:</span><span class="sxs-lookup"><span data-stu-id="270d7-523">The following table provides the features that support list collections:</span></span>

| <span data-ttu-id="270d7-524">Bots in Teams</span><span class="sxs-lookup"><span data-stu-id="270d7-524">Bots in Teams</span></span> | <span data-ttu-id="270d7-525">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="270d7-525">Messaging extensions</span></span>  | <span data-ttu-id="270d7-526">Connectors</span><span class="sxs-lookup"><span data-stu-id="270d7-526">Connectors</span></span> | <span data-ttu-id="270d7-527">Bot Framework</span><span class="sxs-lookup"><span data-stu-id="270d7-527">Bot Framework</span></span> |
| --- | --- | --- | --- |
| <span data-ttu-id="270d7-528">✔</span><span class="sxs-lookup"><span data-stu-id="270d7-528">✔</span></span> | <span data-ttu-id="270d7-529">✔</span><span class="sxs-lookup"><span data-stu-id="270d7-529">✔</span></span> | <span data-ttu-id="270d7-530">✖</span><span class="sxs-lookup"><span data-stu-id="270d7-530">✖</span></span> | <span data-ttu-id="270d7-531">✔</span><span class="sxs-lookup"><span data-stu-id="270d7-531">✔</span></span> |

#### <a name="example-of-a-list-collection"></a><span data-ttu-id="270d7-532">Beispiel für eine Listensammlung</span><span class="sxs-lookup"><span data-stu-id="270d7-532">Example of a list collection</span></span>

![Beispiel für eine Liste von Karten](~/assets/images/cards/list.png)

<span data-ttu-id="270d7-534">Die Eigenschaften von Listensammlungen sind identisch mit den Favoriten- oder Miniaturansichtskarten.</span><span class="sxs-lookup"><span data-stu-id="270d7-534">Properties of list collections are same as the hero or thumbnail cards.</span></span>

<span data-ttu-id="270d7-535">Eine Liste kann maximal zehn Karten pro Nachricht anzeigen.</span><span class="sxs-lookup"><span data-stu-id="270d7-535">A list can display a maximum of ten cards per message.</span></span>

> [!NOTE]
> <span data-ttu-id="270d7-536">Einige Kombinationen von Listenkarten werden unter iOS und Android noch nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="270d7-536">Some combinations of list cards are not yet supported on iOS and Android.</span></span>

#### <a name="syntax-for-list-collections"></a><span data-ttu-id="270d7-537">Syntax für Listensammlungen</span><span class="sxs-lookup"><span data-stu-id="270d7-537">Syntax for list collections</span></span>

<span data-ttu-id="270d7-538">`builder.AttachmentLayout.list` ist die Syntax für Listensammlungen.</span><span class="sxs-lookup"><span data-stu-id="270d7-538">`builder.AttachmentLayout.list` is the syntax for list collections.</span></span>

## <a name="cards-not-supported-in-teams"></a><span data-ttu-id="270d7-539">Karten werden in Teams nicht unterstützt</span><span class="sxs-lookup"><span data-stu-id="270d7-539">Cards not supported in Teams</span></span>

<span data-ttu-id="270d7-540">Die folgenden Karten werden vom Bot Framework implementiert, aber nicht von Teams unterstützt:</span><span class="sxs-lookup"><span data-stu-id="270d7-540">The following cards are implemented by the Bot Framework, but are not supported by Teams:</span></span>

* <span data-ttu-id="270d7-541">Animationskarten</span><span class="sxs-lookup"><span data-stu-id="270d7-541">Animation cards</span></span>
* <span data-ttu-id="270d7-542">Audiokarten</span><span class="sxs-lookup"><span data-stu-id="270d7-542">Audio cards</span></span>
* <span data-ttu-id="270d7-543">Grafikkarten</span><span class="sxs-lookup"><span data-stu-id="270d7-543">Video cards</span></span>

## <a name="see-also"></a><span data-ttu-id="270d7-544">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="270d7-544">See also</span></span>

* [<span data-ttu-id="270d7-545">Aufgabenmodule</span><span class="sxs-lookup"><span data-stu-id="270d7-545">Task modules</span></span>](~/task-modules-and-cards/what-are-task-modules.md)
* [<span data-ttu-id="270d7-546">Formatieren von Karten</span><span class="sxs-lookup"><span data-stu-id="270d7-546">Format cards</span></span>](~/task-modules-and-cards/cards/cards-format.md)
