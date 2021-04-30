---
title: Arbeiten mit universellen Aktionen für adaptive Karten
description: Arbeiten Sie mit den universellen Aktionen für adaptive Karten.
ms.topic: conceptual
localization_priority: Normal
ms.openlocfilehash: 8c260a4893d38ad365cbb3bdd5a7613a1b42654f
ms.sourcegitcommit: 1256639fa424e3833b44207ce847a245824d48e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/29/2021
ms.locfileid: "52088838"
---
# <a name="work-with-universal-actions-for-adaptive-cards"></a><span data-ttu-id="f8a43-103">Arbeiten mit universellen Aktionen für adaptive Karten</span><span class="sxs-lookup"><span data-stu-id="f8a43-103">Work with Universal Actions for Adaptive Cards</span></span>

<span data-ttu-id="f8a43-104">Universelle Aktionen für adaptive Karten bieten eine Möglichkeit, adaptive Kartenszenarien sowohl für Teams als auch für Outlook.</span><span class="sxs-lookup"><span data-stu-id="f8a43-104">Universal Actions for Adaptive Cards provides a way to implement Adaptive Card based scenarios for both, Teams and Outlook.</span></span> <span data-ttu-id="f8a43-105">Dieses Dokument behandelt Folgendes:</span><span class="sxs-lookup"><span data-stu-id="f8a43-105">This document covers the following:</span></span>

* [<span data-ttu-id="f8a43-106">Schema für universelle Aktionen für adaptive Karten</span><span class="sxs-lookup"><span data-stu-id="f8a43-106">Schema used for Universal Actions for Adaptive Cards</span></span>](#schema-for-universal-actions-for-adaptive-cards)
* [<span data-ttu-id="f8a43-107">Aktualisierungsmodell</span><span class="sxs-lookup"><span data-stu-id="f8a43-107">Refresh model</span></span>](#refresh-model)
* [<span data-ttu-id="f8a43-108">`adaptiveCard/action` Aufrufen der Aktivität</span><span class="sxs-lookup"><span data-stu-id="f8a43-108">`adaptiveCard/action` invoke activity</span></span>](#adaptivecardaction-invoke-activity)
* [<span data-ttu-id="f8a43-109">Abwärtskompatibilität</span><span class="sxs-lookup"><span data-stu-id="f8a43-109">Backward compatibility</span></span>](#backward-compatibility)

## <a name="quick-start-guide-to-leverage-universal-actions-for-adaptive-cards-in-teams"></a><span data-ttu-id="f8a43-110">Schnellstartanleitung zur Nutzung universeller Aktionen für adaptive Karten in Teams</span><span class="sxs-lookup"><span data-stu-id="f8a43-110">Quick start guide to leverage Universal Actions for Adaptive Cards in Teams</span></span>

1. <span data-ttu-id="f8a43-111">Ersetzen Sie alle Instanzen `Action.Submit` von `Action.Execute` durch, um ein vorhandenes Szenario auf Teams.</span><span class="sxs-lookup"><span data-stu-id="f8a43-111">Replace all instances of `Action.Submit` with `Action.Execute` to update an existing scenario on Teams.</span></span>
2. <span data-ttu-id="f8a43-112">Fügen Sie Ihrer adaptiven Karte eine Klausel hinzu, wenn Sie das automatische Aktualisierungsmodell nutzen möchten oder wenn für Ihr Szenario `refresh` benutzerspezifische Ansichten erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="f8a43-112">Add a `refresh` clause to your Adaptive Card, if you want to leverage the automatic refresh model or if your scenario requires User Specific Views.</span></span>

    >[!NOTE]
    > <span data-ttu-id="f8a43-113">Geben Sie die `userIds` zu identifizierende Eigenschaft an, welche Benutzer automatische Updates erhalten.</span><span class="sxs-lookup"><span data-stu-id="f8a43-113">Specify the `userIds` property to identify, which users get automatic updates.</span></span>

3. <span data-ttu-id="f8a43-114">Behandeln `adaptiveCard/action` sie Aufrufanforderungen in Ihrem Bot.</span><span class="sxs-lookup"><span data-stu-id="f8a43-114">Handle `adaptiveCard/action` invoke requests in your bot.</span></span>
4. <span data-ttu-id="f8a43-115">Verwenden Sie den Kontext der Aufrufanforderung, um mit Karten zurück zu antworten, die speziell für einen Benutzer erstellt wurden.</span><span class="sxs-lookup"><span data-stu-id="f8a43-115">Use the invoke request's context to respond back with cards that are specifically created for a user.</span></span>

    > [!NOTE]
    > <span data-ttu-id="f8a43-116">Wenn Ihr Bot eine neue Karte als Ergebnis der Verarbeitung einer zurückgibt, muss die Antwort `Action.Execute` dem Antwortformat entsprechen.</span><span class="sxs-lookup"><span data-stu-id="f8a43-116">Whenever your bot returns a new card as a result of processing an `Action.Execute`, the response must conform to the response format.</span></span>

## <a name="schema-for-universal-actions-for-adaptive-cards"></a><span data-ttu-id="f8a43-117">Schema für universelle Aktionen für adaptive Karten</span><span class="sxs-lookup"><span data-stu-id="f8a43-117">Schema for Universal Actions for Adaptive Cards</span></span>

<span data-ttu-id="f8a43-118">Universelle Aktionen für adaptive Karten werden im Schema adaptiver Karten, Version 1.4, eingeführt.</span><span class="sxs-lookup"><span data-stu-id="f8a43-118">Universal Actions for Adaptive Cards is introduced in the Adaptive Cards schema version 1.4.</span></span> <span data-ttu-id="f8a43-119">Um adaptive Karte effektiv zu verwenden, muss die Eigenschaft Ihrer adaptiven Karte `version` auf 1,4 festgelegt sein.</span><span class="sxs-lookup"><span data-stu-id="f8a43-119">To use Adaptive Card effectively, the `version` property of your Adaptive Card must be set to 1.4.</span></span>

> [!NOTE]
> <span data-ttu-id="f8a43-120">Wenn Sie die Eigenschaft auf 1,4 festlegen, ist Ihre adaptive Karte mit älteren Clients der Plattformen oder Anwendungen wie Outlook und Teams nicht kompatibel, da sie die universellen Aktionen für adaptive Karten nicht `version` unterstützen.</span><span class="sxs-lookup"><span data-stu-id="f8a43-120">Setting the `version` property to 1.4 makes your Adaptive Card incompatible with older clients of the platforms or applications, such as Outlook and Teams, as they do not support the Universal Actions for Adaptive Cards.</span></span>

<span data-ttu-id="f8a43-121">Wenn Sie die Kartenversion auf kleiner als 1.4 festlegen und entweder oder beides, Eigenschaft und verwenden, geschieht `refresh` `Action.Execute` Folgendes:</span><span class="sxs-lookup"><span data-stu-id="f8a43-121">If you set the card version to less than 1.4 and use either or both, `refresh` property and `Action.Execute`, the following happens:</span></span>

| <span data-ttu-id="f8a43-122">Client</span><span class="sxs-lookup"><span data-stu-id="f8a43-122">Client</span></span> | <span data-ttu-id="f8a43-123">Verhalten</span><span class="sxs-lookup"><span data-stu-id="f8a43-123">Behavior</span></span> |
| :-- | :-- |
| <span data-ttu-id="f8a43-124">Teams</span><span class="sxs-lookup"><span data-stu-id="f8a43-124">Teams</span></span> | <span data-ttu-id="f8a43-125">Ihre Karte funktioniert nicht mehr.</span><span class="sxs-lookup"><span data-stu-id="f8a43-125">Your card stops working.</span></span> <span data-ttu-id="f8a43-126">Die Karte wird nicht aktualisiert und wird in Abhängigkeit von der Version des Teams `Action.Execute` gerendert.</span><span class="sxs-lookup"><span data-stu-id="f8a43-126">Card is not refreshed and `Action.Execute` does not render depending on the version of the Teams client.</span></span> <span data-ttu-id="f8a43-127">Um maximale Kompatibilität in Teams zu gewährleisten, definieren `Action.Execute` Sie mit einer in der `Action.Submit` Fallback-Eigenschaft.</span><span class="sxs-lookup"><span data-stu-id="f8a43-127">To ensure maximum compatibility in Teams, define `Action.Execute` with an `Action.Submit` in the fallback property.</span></span> |

<span data-ttu-id="f8a43-128">Weitere Informationen zur Unterstützung älterer Clients finden Sie unter [Abwärtskompatibilität](#backward-compatibility).</span><span class="sxs-lookup"><span data-stu-id="f8a43-128">For more information on how to support older clients, see [backward compatibility](#backward-compatibility).</span></span>

### <a name="actionexecute"></a><span data-ttu-id="f8a43-129">Action.Execute</span><span class="sxs-lookup"><span data-stu-id="f8a43-129">Action.Execute</span></span>

<span data-ttu-id="f8a43-130">Ersetzen Sie beim Erstellen adaptiver Karten `Action.Submit` und `Action.Http` durch `Action.Execute` .</span><span class="sxs-lookup"><span data-stu-id="f8a43-130">When authoring Adaptive Cards, replace `Action.Submit` and `Action.Http` with `Action.Execute`.</span></span> <span data-ttu-id="f8a43-131">Das Schema für `Action.Execute` ähnelt dem von `Action.Submit` .</span><span class="sxs-lookup"><span data-stu-id="f8a43-131">The schema for `Action.Execute` is similar to that of `Action.Submit`.</span></span>

<span data-ttu-id="f8a43-132">Weitere Informationen finden Sie unter [Action.Exeschema and properties](https://docs.microsoft.com/adaptive-cards/authoring-cards/universal-action-model#actionexecute).</span><span class="sxs-lookup"><span data-stu-id="f8a43-132">For more information, see [Action.Execute schema and properties](https://docs.microsoft.com/adaptive-cards/authoring-cards/universal-action-model#actionexecute).</span></span>

<span data-ttu-id="f8a43-133">Jetzt können Sie das Aktualisierungsmodell verwenden, damit adaptive Karten automatisch aktualisiert werden können.</span><span class="sxs-lookup"><span data-stu-id="f8a43-133">Now, you can use the refresh model to allow Adaptive Cards to update automatically.</span></span>

## <a name="refresh-model"></a><span data-ttu-id="f8a43-134">Aktualisierungsmodell</span><span class="sxs-lookup"><span data-stu-id="f8a43-134">Refresh model</span></span>

<span data-ttu-id="f8a43-135">Um Ihre adaptive Karte automatisch zu aktualisieren, definieren Sie ihre Eigenschaft, die eine Aktion vom Typ und `refresh` `Action.Execute` ein Array `userIds` einbettet.</span><span class="sxs-lookup"><span data-stu-id="f8a43-135">To automatically refresh your Adaptive Card, define its `refresh` property, which embeds an action of type `Action.Execute` and an `userIds` array.</span></span>

<span data-ttu-id="f8a43-136">Weitere Informationen finden Sie unter [Aktualisierungsschema und Eigenschaften](https://docs.microsoft.com/adaptive-cards/authoring-cards/universal-action-model#refresh-mechanism).</span><span class="sxs-lookup"><span data-stu-id="f8a43-136">For more information, see [refresh schema and properties](https://docs.microsoft.com/adaptive-cards/authoring-cards/universal-action-model#refresh-mechanism).</span></span>

## <a name="user-ids-in-refresh"></a><span data-ttu-id="f8a43-137">Benutzer-IDs in der Aktualisierung</span><span class="sxs-lookup"><span data-stu-id="f8a43-137">User IDs in refresh</span></span>

<span data-ttu-id="f8a43-138">Im Folgenden sind die Features von UserIds in refresh zu finden:</span><span class="sxs-lookup"><span data-stu-id="f8a43-138">The following are the features of UserIds in refresh:</span></span>

* <span data-ttu-id="f8a43-139">UserIds ist ein Array von MrI des Benutzers, das Teil der `refresh` Eigenschaft in Adaptive Karten ist.</span><span class="sxs-lookup"><span data-stu-id="f8a43-139">UserIds is an array of user MRI's which is part of the `refresh` property in Adaptive Cards.</span></span>

* <span data-ttu-id="f8a43-140">Wenn die List-Eigenschaft wie im Abschnitt "Aktualisieren" der Karte angegeben ist, wird die Karte `userIds` `userIds: []` nicht automatisch aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="f8a43-140">If the `userIds` list property is specified as `userIds: []` in the refresh section of the card, the card is not automatically refreshed.</span></span> <span data-ttu-id="f8a43-141">Stattdessen wird  dem Benutzer eine Option Karte aktualisieren im Dreipunktmenü im Web oder Desktop und im kontextbezogenen Long-Press-Menü in Mobile angezeigt, d. h. Android oder iOS, um die Karte manuell zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="f8a43-141">Instead, a **Refresh Card** option is displayed to the user in the triple dot menu in web or desktop and in the long press context menu in mobile, that is, Android or iOS to manually refresh the card.</span></span>

* <span data-ttu-id="f8a43-142">Die UserIds-Eigenschaft wird hinzugefügt, da Kanäle in Teams eine große Anzahl von Mitgliedern enthalten können.</span><span class="sxs-lookup"><span data-stu-id="f8a43-142">UserIds property is added because channels in Teams can include a large number of members.</span></span> <span data-ttu-id="f8a43-143">Wenn alle Mitglieder den Kanal gleichzeitig anzeigen, führt eine bedingungslose automatische Aktualisierung zu vielen gleichzeitigen Aufrufen des Bots.</span><span class="sxs-lookup"><span data-stu-id="f8a43-143">If all members are viewing the channel at the same time, an unconditional automatic refresh results in many concurrent calls to the bot.</span></span> <span data-ttu-id="f8a43-144">Um dies zu vermeiden, muss die Eigenschaft immer enthalten sein, um zu ermitteln, welche Benutzer eine automatische Aktualisierung mit maximal `userIds` *60 (60) Benutzer-MRIs erhalten müssen.*</span><span class="sxs-lookup"><span data-stu-id="f8a43-144">To avoid this, the `userIds` property must always be included to identify which users must get an automatic refresh with a maximum of *60 (sixty) user MRIs*.</span></span>

* <span data-ttu-id="f8a43-145">Weitere Informationen zum Abrufen Teams Benutzer-MRIs des Unterhaltungsmitglieds zum Hinzufügen in die UserIds-Liste im Abschnitt Aktualisierung von Adaptive Karte finden Sie unter [Fetch roster or user profile](https://docs.microsoft.com/microsoftteams/platform/bots/how-to/get-teams-context?tabs=dotnet#fetch-the-roster-or-user-profile).</span><span class="sxs-lookup"><span data-stu-id="f8a43-145">For more information on how you can fetch Teams conversation member's user MRIs to add in userIds list in refresh section of Adaptive Card, see [fetch roster or user profile](https://docs.microsoft.com/microsoftteams/platform/bots/how-to/get-teams-context?tabs=dotnet#fetch-the-roster-or-user-profile).</span></span>

* <span data-ttu-id="f8a43-146">Beispiel für Teams benutzer-MRI ist`29:1bSnHZ7Js2STWrgk6ScEErLk1Lp2zQuD5H2qQ960rtvstKp8tKLl-3r8b6DoW0QxZimuTxk_kupZ1DBMpvIQQUAZL-PNj0EORDvRZXy8kvWk`</span><span class="sxs-lookup"><span data-stu-id="f8a43-146">Sample Teams user MRI is `29:1bSnHZ7Js2STWrgk6ScEErLk1Lp2zQuD5H2qQ960rtvstKp8tKLl-3r8b6DoW0QxZimuTxk_kupZ1DBMpvIQQUAZL-PNj0EORDvRZXy8kvWk`</span></span>

> [!NOTE]
> <span data-ttu-id="f8a43-147">Die `userIds` Eigenschaft wird in Outlook ignoriert, und die Eigenschaft wird immer automatisch `refresh` aktiviert.</span><span class="sxs-lookup"><span data-stu-id="f8a43-147">The `userIds` property is ignored in Outlook, and the `refresh` property is always automatically activated.</span></span> <span data-ttu-id="f8a43-148">Es gibt kein Skalierungsproblem in Outlook, da Benutzer die Karte zu unterschiedlichen Zeiten anzeigen.</span><span class="sxs-lookup"><span data-stu-id="f8a43-148">There is no scale issue in Outlook because users view the card at different times.</span></span>

<span data-ttu-id="f8a43-149">Im nächsten Schritt verwenden Sie die Aufrufaktivität, um zu verstehen, welche Anforderung nach der `adaptiveCard/action` Ausführung gestellt werden `Action.Execute` muss.</span><span class="sxs-lookup"><span data-stu-id="f8a43-149">Next step is to use the `adaptiveCard/action` invoke activity to understand what request must be made after `Action.Execute` is executed.</span></span>

## <a name="adaptivecardaction-invoke-activity"></a><span data-ttu-id="f8a43-150">`adaptiveCard/action` Aufrufen der Aktivität</span><span class="sxs-lookup"><span data-stu-id="f8a43-150">`adaptiveCard/action` invoke activity</span></span>

<span data-ttu-id="f8a43-151">Wenn sie im Client ausgeführt wird, wird ihrem Bot eine neue `Action.Execute` Art von `adaptiveCard/action` Invoke-Aktivität vorgenommen.</span><span class="sxs-lookup"><span data-stu-id="f8a43-151">When `Action.Execute` is executed in the client, a new type of Invoke activity `adaptiveCard/action` is made to your bot.</span></span>

<span data-ttu-id="f8a43-152">Weitere Informationen finden Sie unter [Anforderungsformat und Eigenschaften für eine typische `adaptiveCard/action` Aufrufaktivität](https://docs.microsoft.com/adaptive-cards/authoring-cards/universal-action-model#request-format).</span><span class="sxs-lookup"><span data-stu-id="f8a43-152">For more information, see [request format and properties for a typical `adaptiveCard/action` invoke activity](https://docs.microsoft.com/adaptive-cards/authoring-cards/universal-action-model#request-format).</span></span>

<span data-ttu-id="f8a43-153">Weitere Informationen finden Sie unter [Antwortformat und Eigenschaften für eine typische `adaptiveCard/action` Aufrufaktivität mit unterstützten Antworttypen](https://docs.microsoft.com/adaptive-cards/authoring-cards/universal-action-model#response-format).</span><span class="sxs-lookup"><span data-stu-id="f8a43-153">For more information, see [response format and properties for a typical `adaptiveCard/action` invoke activity with supported response types](https://docs.microsoft.com/adaptive-cards/authoring-cards/universal-action-model#response-format).</span></span>

<span data-ttu-id="f8a43-154">Als Nächstes können Sie die Abwärtskompatibilität auf ältere Clients über verschiedene Plattformen hinweg anwenden und Ihre adaptive Karte kompatibel machen.</span><span class="sxs-lookup"><span data-stu-id="f8a43-154">Next, you can apply backward compatibility to older clients across different platforms and make your Adaptive Card compatible.</span></span>

## <a name="backward-compatibility"></a><span data-ttu-id="f8a43-155">Abwärtskompatibilität</span><span class="sxs-lookup"><span data-stu-id="f8a43-155">Backward compatibility</span></span>

<span data-ttu-id="f8a43-156">Mit universellen Aktionen für adaptive Karten können Sie Eigenschaften festlegen, die die Abwärtskompatibilität mit älteren Versionen von Outlook und Teams.</span><span class="sxs-lookup"><span data-stu-id="f8a43-156">Universal Actions for Adaptive Cards allows you to set properties that enable backward compatibility with older versions of Outlook and Teams.</span></span>

### <a name="teams"></a><span data-ttu-id="f8a43-157">Teams</span><span class="sxs-lookup"><span data-stu-id="f8a43-157">Teams</span></span>

<span data-ttu-id="f8a43-158">Um die Abwärtskompatibilität Ihrer adaptiven Karten mit älteren Versionen von Teams sicherzustellen, müssen Sie die Eigenschaft enthalten und `fallback` den Wert auf `Action.Submit` festlegen.</span><span class="sxs-lookup"><span data-stu-id="f8a43-158">To ensure backward compatibility of your Adaptive Cards with older versions of Teams, you must include the `fallback` property and set its value to `Action.Submit`.</span></span> <span data-ttu-id="f8a43-159">Außerdem muss Ihr Botcode sowohl als auch `Action.Execute` `Action.Submit` verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="f8a43-159">Also, your bot code must process both `Action.Execute` and `Action.Submit`.</span></span>

<span data-ttu-id="f8a43-160">Weitere Informationen finden Sie unter [Abwärtskompatibilität auf Teams](https://docs.microsoft.com/adaptive-cards/authoring-cards/universal-action-model#teams).</span><span class="sxs-lookup"><span data-stu-id="f8a43-160">For more information, see [backward compatibility on Teams](https://docs.microsoft.com/adaptive-cards/authoring-cards/universal-action-model#teams).</span></span>

## <a name="see-also"></a><span data-ttu-id="f8a43-161">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="f8a43-161">See also</span></span>

* [<span data-ttu-id="f8a43-162">Adaptive Kartenaktionen in Teams</span><span class="sxs-lookup"><span data-stu-id="f8a43-162">Adaptive Card actions in Teams</span></span>](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions)
* [<span data-ttu-id="f8a43-163">Wie Bots funktionieren</span><span class="sxs-lookup"><span data-stu-id="f8a43-163">How bots work</span></span>](/azure/bot-service/bot-builder-basics?view=azure-bot-service-4.0&preserve-view=true)
