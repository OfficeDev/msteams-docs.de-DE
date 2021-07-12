---
title: Mit Universal-Aktionen für adaptive Karten arbeiten
description: Mit Universal-Aktionen für adaptive Karten arbeiten.
ms.topic: conceptual
localization_priority: Normal
ms.openlocfilehash: 4361f1c7774837b728c6382df4e62e00ea912e35
ms.sourcegitcommit: 999f5c607671e088ea8a461fa7dbb63f8d61c39b
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/25/2021
ms.locfileid: "52649699"
---
# <a name="work-with-universal-actions-for-adaptive-cards"></a><span data-ttu-id="27704-103">Mit Universal-Aktionen für adaptive Karten arbeiten</span><span class="sxs-lookup"><span data-stu-id="27704-103">Work with Universal Actions for Adaptive Cards</span></span>

<span data-ttu-id="27704-104">Universal-Aktionen für adaptive Karten bieten eine Möglichkeit zum Implementieren adaptiver Kartenszenarien für Teams und Outlook.</span><span class="sxs-lookup"><span data-stu-id="27704-104">Universal Actions for Adaptive Cards provides a way to implement Adaptive Card based scenarios for both, Teams and Outlook.</span></span> <span data-ttu-id="27704-105">In diesem Dokument wird Folgendes behandelt:</span><span class="sxs-lookup"><span data-stu-id="27704-105">This document covers the following:</span></span>

* [<span data-ttu-id="27704-106">Schema, das für Universal-Aktionen für adaptive Karten verwendet wird</span><span class="sxs-lookup"><span data-stu-id="27704-106">Schema used for Universal Actions for Adaptive Cards</span></span>](#schema-for-universal-actions-for-adaptive-cards)
* [<span data-ttu-id="27704-107">Aktualisierungsmodell</span><span class="sxs-lookup"><span data-stu-id="27704-107">Refresh model</span></span>](#refresh-model)
* [<span data-ttu-id="27704-108">`adaptiveCard/action` Aufrufaktivität</span><span class="sxs-lookup"><span data-stu-id="27704-108">`adaptiveCard/action` invoke activity</span></span>](#adaptivecardaction-invoke-activity)
* [<span data-ttu-id="27704-109">Abwärtskompatibilität</span><span class="sxs-lookup"><span data-stu-id="27704-109">Backward compatibility</span></span>](#backward-compatibility)

## <a name="quick-start-guide-to-leverage-universal-actions-for-adaptive-cards-in-teams"></a><span data-ttu-id="27704-110">Schnellstarthandbuch zur Nutzung von Universal-Aktionen für adaptive Karten in Teams</span><span class="sxs-lookup"><span data-stu-id="27704-110">Quick start guide to leverage Universal Actions for Adaptive Cards in Teams</span></span>

1. <span data-ttu-id="27704-111">Ersetzen Sie alle Instanzen von `Action.Submit` durch `Action.Execute`, um ein vorhandenes Szenario in Teams zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="27704-111">Replace all instances of `Action.Submit` with `Action.Execute` to update an existing scenario on Teams.</span></span>
2. <span data-ttu-id="27704-112">Fügen Sie Ihrer adaptiven Karte eine `refresh`-Klausel hinzu, wenn Sie das Modell für die automatische Aktualisierung nutzen möchten oder wenn Ihr Szenario benutzerspezifische Ansichten erfordert.</span><span class="sxs-lookup"><span data-stu-id="27704-112">Add a `refresh` clause to your Adaptive Card, if you want to leverage the automatic refresh model or if your scenario requires User Specific Views.</span></span>

    >[!NOTE]
    > <span data-ttu-id="27704-113">Geben Sie die `userIds`-Eigenschaft an, die identifiziert werden soll, welche Benutzer automatische Updates erhalten.</span><span class="sxs-lookup"><span data-stu-id="27704-113">Specify the `userIds` property to identify, which users get automatic updates.</span></span>

3. <span data-ttu-id="27704-114">Verarbeiten Sie `adaptiveCard/action` Aufrufanforderungen in Ihrem Bot.</span><span class="sxs-lookup"><span data-stu-id="27704-114">Handle `adaptiveCard/action` invoke requests in your bot.</span></span>
4. <span data-ttu-id="27704-115">Verwenden Sie den Kontext der Aufrufanforderung, um mit Karten zu antworten, die speziell für einen Benutzer erstellt wurden.</span><span class="sxs-lookup"><span data-stu-id="27704-115">Use the invoke request's context to respond back with cards that are specifically created for a user.</span></span>

    > [!NOTE]
    > <span data-ttu-id="27704-116">Wenn Ihr Bot als Ergebnis der Verarbeitung eines `Action.Execute` eine neue Karte zurückgibt, muss die Antwort dem Antwortformat entsprechen.</span><span class="sxs-lookup"><span data-stu-id="27704-116">Whenever your bot returns a new card as a result of processing an `Action.Execute`, the response must conform to the response format.</span></span>

## <a name="schema-for-universal-actions-for-adaptive-cards"></a><span data-ttu-id="27704-117">Schema für Universal-Aktionen für adaptive Karten</span><span class="sxs-lookup"><span data-stu-id="27704-117">Schema for Universal Actions for Adaptive Cards</span></span>

<span data-ttu-id="27704-118">Universal-Aktionen für adaptive Karten wird in der Adaptive Karten-Schemaversion 1.4 eingeführt.</span><span class="sxs-lookup"><span data-stu-id="27704-118">Universal Actions for Adaptive Cards is introduced in the Adaptive Cards schema version 1.4.</span></span> <span data-ttu-id="27704-119">Um adaptive Karten effektiv verwenden zu können, muss die `version`-Eigenschaft Ihrer adaptiven Karte auf 1.4 festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="27704-119">To use Adaptive Card effectively, the `version` property of your Adaptive Card must be set to 1.4.</span></span>

> [!NOTE]
> <span data-ttu-id="27704-120">Wenn Sie die `version`-Eigenschaft auf 1.4 festlegen, ist Ihre adaptive Karte nicht mit älteren Clients der Plattformen oder Anwendungen wie Outlook und Teams kompatibel, da sie die Universal-Aktionen für adaptive Karten nicht unterstützen.</span><span class="sxs-lookup"><span data-stu-id="27704-120">Setting the `version` property to 1.4 makes your Adaptive Card incompatible with older clients of the platforms or applications, such as Outlook and Teams, as they do not support the Universal Actions for Adaptive Cards.</span></span>

<span data-ttu-id="27704-121">Wenn Sie die Kartenversion auf eine niedrigere Version als 1.4 festlegen und entweder die `refresh`-Eigenschaft oder `Action.Execute` verwenden, geschieht Folgendes:</span><span class="sxs-lookup"><span data-stu-id="27704-121">If you set the card version to less than 1.4 and use either or both, `refresh` property and `Action.Execute`, the following happens:</span></span>

| <span data-ttu-id="27704-122">Client</span><span class="sxs-lookup"><span data-stu-id="27704-122">Client</span></span> | <span data-ttu-id="27704-123">Verhalten</span><span class="sxs-lookup"><span data-stu-id="27704-123">Behavior</span></span> |
| :-- | :-- |
| <span data-ttu-id="27704-124">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="27704-124">Teams</span></span> | <span data-ttu-id="27704-125">Ihre Karte funktioniert nicht mehr.</span><span class="sxs-lookup"><span data-stu-id="27704-125">Your card stops working.</span></span> <span data-ttu-id="27704-126">Die Karte wird nicht aktualisiert, und `Action.Execute` wird nicht abhängig von der Version des Teams-Clients gerendert.</span><span class="sxs-lookup"><span data-stu-id="27704-126">Card is not refreshed and `Action.Execute` does not render depending on the version of the Teams client.</span></span> <span data-ttu-id="27704-127">Um maximale Kompatibilität in Teams sicherzustellen, definieren Sie `Action.Execute` mit einem `Action.Submit` in der Fallbackeigenschaft.</span><span class="sxs-lookup"><span data-stu-id="27704-127">To ensure maximum compatibility in Teams, define `Action.Execute` with an `Action.Submit` in the fallback property.</span></span> |

<span data-ttu-id="27704-128">Weitere Informationen zur Unterstützung älterer Clients finden Sie unter [Abwärtskompatibilität](#backward-compatibility).</span><span class="sxs-lookup"><span data-stu-id="27704-128">For more information on how to support older clients, see [backward compatibility](#backward-compatibility).</span></span>

### <a name="actionexecute"></a><span data-ttu-id="27704-129">Action.Execute</span><span class="sxs-lookup"><span data-stu-id="27704-129">Action.Execute</span></span>

<span data-ttu-id="27704-130">Ersetzen Sie beim Erstellen von adaptive Karten `Action.Submit` und `Action.Http` durch `Action.Execute`.</span><span class="sxs-lookup"><span data-stu-id="27704-130">When authoring Adaptive Cards, replace `Action.Submit` and `Action.Http` with `Action.Execute`.</span></span> <span data-ttu-id="27704-131">Das Schema für `Action.Execute` ähnelt dem von `Action.Submit`.</span><span class="sxs-lookup"><span data-stu-id="27704-131">The schema for `Action.Execute` is similar to that of `Action.Submit`.</span></span>

<span data-ttu-id="27704-132">Weitere Informationen finden Sie unter [Action.Execute-Schema und -Eigenschaften](/adaptive-cards/authoring-cards/universal-action-model#actionexecute).</span><span class="sxs-lookup"><span data-stu-id="27704-132">For more information, see [Action.Execute schema and properties](/adaptive-cards/authoring-cards/universal-action-model#actionexecute).</span></span>

<span data-ttu-id="27704-133">Jetzt können Sie das Aktualisierungsmodell verwenden, damit Adaptive Karten automatisch aktualisiert werden können.</span><span class="sxs-lookup"><span data-stu-id="27704-133">Now, you can use the refresh model to allow Adaptive Cards to update automatically.</span></span>

## <a name="refresh-model"></a><span data-ttu-id="27704-134">Aktualisierungsmodell</span><span class="sxs-lookup"><span data-stu-id="27704-134">Refresh model</span></span>

<span data-ttu-id="27704-135">Um Ihre adaptive Karte automatisch zu aktualisieren, definieren Sie ihre `refresh`-Eigenschaft, die eine Aktion vom Typ `Action.Execute` und ein `userIds`-Array einbettet.</span><span class="sxs-lookup"><span data-stu-id="27704-135">To automatically refresh your Adaptive Card, define its `refresh` property, which embeds an action of type `Action.Execute` and an `userIds` array.</span></span>

<span data-ttu-id="27704-136">Weitere Informationen finden Sie unter [Aktualisieren von Schemas und Eigenschaften](/adaptive-cards/authoring-cards/universal-action-model#refresh-mechanism).</span><span class="sxs-lookup"><span data-stu-id="27704-136">For more information, see [refresh schema and properties](/adaptive-cards/authoring-cards/universal-action-model#refresh-mechanism).</span></span>

## <a name="user-ids-in-refresh"></a><span data-ttu-id="27704-137">Benutzer-IDs, die aktualisiert werden</span><span class="sxs-lookup"><span data-stu-id="27704-137">User IDs in refresh</span></span>

<span data-ttu-id="27704-138">Im Folgenden sind die Features von UserIds aufgeführt, die aktualisiert werden:</span><span class="sxs-lookup"><span data-stu-id="27704-138">The following are the features of UserIds in refresh:</span></span>

* <span data-ttu-id="27704-139">UserIds ist ein Array von Benutzer-MRIs, das Teil der `refresh`-Eigenschaft in Adaptive Karten ist.</span><span class="sxs-lookup"><span data-stu-id="27704-139">UserIds is an array of user MRI's which is part of the `refresh` property in Adaptive Cards.</span></span>

* <span data-ttu-id="27704-140">Wenn die `userIds`-Listeneigenschaft als `userIds: []` im Aktualisierungsabschnitt der Karte angegeben ist, wird die Karte nicht automatisch aktualisiert.</span><span class="sxs-lookup"><span data-stu-id="27704-140">If the `userIds` list property is specified as `userIds: []` in the refresh section of the card, the card is not automatically refreshed.</span></span> <span data-ttu-id="27704-141">Stattdessen wird dem Benutzer eine Option **Karte aktualisieren** im Dreifachpunktmenü im Web oder auf dem Desktop und im Kontextmenü mit langem Tastendruck auf Mobilgeräten, d. h. Android oder iOS, angezeigt, um die Karte manuell zu aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="27704-141">Instead, a **Refresh Card** option is displayed to the user in the triple dot menu in web or desktop and in the long press context menu in mobile, that is, Android or iOS to manually refresh the card.</span></span>

* <span data-ttu-id="27704-142">Die UserIds-Eigenschaft wird hinzugefügt, da Kanäle in Teams eine große Anzahl von Mitgliedern enthalten können.</span><span class="sxs-lookup"><span data-stu-id="27704-142">UserIds property is added because channels in Teams can include a large number of members.</span></span> <span data-ttu-id="27704-143">Wenn alle Mitglieder den Kanal gleichzeitig anzeigen, führt eine bedingungslose automatische Aktualisierung zu vielen gleichzeitigen Aufrufen des Bots.</span><span class="sxs-lookup"><span data-stu-id="27704-143">If all members are viewing the channel at the same time, an unconditional automatic refresh results in many concurrent calls to the bot.</span></span> <span data-ttu-id="27704-144">Um dies zu vermeiden, muss die `userIds`-Eigenschaft immer eingeschlossen werden, um zu identifizieren, welche Benutzer eine automatische Aktualisierung mit maximal *60 (sechszig) Benutzer-MRIs* erhalten müssen.</span><span class="sxs-lookup"><span data-stu-id="27704-144">To avoid this, the `userIds` property must always be included to identify which users must get an automatic refresh with a maximum of *60 (sixty) user MRIs*.</span></span>

* <span data-ttu-id="27704-145">Weitere Informationen dazu, wie Sie die Benutzer-MRIs eines Teams-Unterhaltungsmitglieds abrufen können, um sie in der Liste "userIds" im Aktualisierungsabschnitt der adaptiven Karte hinzuzufügen, finden Sie unter [Abrufen der Liste oder des Benutzerprofils](/microsoftteams/platform/bots/how-to/get-teams-context?tabs=dotnet#fetch-the-roster-or-user-profile).</span><span class="sxs-lookup"><span data-stu-id="27704-145">For more information on how you can fetch Teams conversation member's user MRIs to add in userIds list in refresh section of Adaptive Card, see [fetch roster or user profile](/microsoftteams/platform/bots/how-to/get-teams-context?tabs=dotnet#fetch-the-roster-or-user-profile).</span></span>

* <span data-ttu-id="27704-146">MRI des Teams-Beispielbenutzers ist `29:1bSnHZ7Js2STWrgk6ScEErLk1Lp2zQuD5H2qQ960rtvstKp8tKLl-3r8b6DoW0QxZimuTxk_kupZ1DBMpvIQQUAZL-PNj0EORDvRZXy8kvWk`</span><span class="sxs-lookup"><span data-stu-id="27704-146">Sample Teams user MRI is `29:1bSnHZ7Js2STWrgk6ScEErLk1Lp2zQuD5H2qQ960rtvstKp8tKLl-3r8b6DoW0QxZimuTxk_kupZ1DBMpvIQQUAZL-PNj0EORDvRZXy8kvWk`</span></span>

> [!NOTE]
> <span data-ttu-id="27704-147">Die `userIds`-Eigenschaft wird in Outlook ignoriert, und die `refresh`-Eigenschaft wird immer automatisch aktiviert.</span><span class="sxs-lookup"><span data-stu-id="27704-147">The `userIds` property is ignored in Outlook, and the `refresh` property is always automatically activated.</span></span> <span data-ttu-id="27704-148">Es gibt kein Skalierungsproblem in Outlook, da Benutzer die Karte zu unterschiedlichen Zeiten anzeigen.</span><span class="sxs-lookup"><span data-stu-id="27704-148">There is no scale issue in Outlook because users view the card at different times.</span></span>

<span data-ttu-id="27704-149">Der nächste Schritt besteht darin, die `adaptiveCard/action`-Aufrufaktivität zu verwenden, um zu verstehen, welche Anforderung ausgeführt werden muss, nachdem `Action.Execute` ausgeführt wurde.</span><span class="sxs-lookup"><span data-stu-id="27704-149">Next step is to use the `adaptiveCard/action` invoke activity to understand what request must be made after `Action.Execute` is executed.</span></span>

## <a name="adaptivecardaction-invoke-activity"></a><span data-ttu-id="27704-150">`adaptiveCard/action` Aufrufaktivität</span><span class="sxs-lookup"><span data-stu-id="27704-150">`adaptiveCard/action` invoke activity</span></span>

<span data-ttu-id="27704-151">Wenn `Action.Execute` im Client ausgeführt wird, wird ein neuer Typ von Aufrufaktivität `adaptiveCard/action` für Ihren Bot erstellt.</span><span class="sxs-lookup"><span data-stu-id="27704-151">When `Action.Execute` is executed in the client, a new type of Invoke activity `adaptiveCard/action` is made to your bot.</span></span>

<span data-ttu-id="27704-152">Weitere Informationen finden Sie unter [Anforderungsformat und -eigenschaften für eine typische `adaptiveCard/action`-Aufrufaktivität](/adaptive-cards/authoring-cards/universal-action-model#request-format).</span><span class="sxs-lookup"><span data-stu-id="27704-152">For more information, see [request format and properties for a typical `adaptiveCard/action` invoke activity](/adaptive-cards/authoring-cards/universal-action-model#request-format).</span></span>

<span data-ttu-id="27704-153">Weitere Informationen finden Sie unter [Antwortformat und -eigenschaften für eine typische `adaptiveCard/action`-Aufrufaktivität mit unterstützten Antworttypen](/adaptive-cards/authoring-cards/universal-action-model#response-format).</span><span class="sxs-lookup"><span data-stu-id="27704-153">For more information, see [response format and properties for a typical `adaptiveCard/action` invoke activity with supported response types](/adaptive-cards/authoring-cards/universal-action-model#response-format).</span></span>

<span data-ttu-id="27704-154">Als Nächstes können Sie Abwärtskompatibilität auf ältere Clients auf verschiedenen Plattformen anwenden und Ihre adaptive Karte kompatibel machen.</span><span class="sxs-lookup"><span data-stu-id="27704-154">Next, you can apply backward compatibility to older clients across different platforms and make your Adaptive Card compatible.</span></span>

## <a name="backward-compatibility"></a><span data-ttu-id="27704-155">Abwärtskompatibilität</span><span class="sxs-lookup"><span data-stu-id="27704-155">Backward compatibility</span></span>

<span data-ttu-id="27704-156">Mit Universal-Aktionen für adaptive Karten können Sie Eigenschaften festlegen, die Abwärtskompatibilität mit älteren Versionen von Outlook und Teams ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="27704-156">Universal Actions for Adaptive Cards allows you to set properties that enable backward compatibility with older versions of Outlook and Teams.</span></span>

### <a name="teams"></a><span data-ttu-id="27704-157">Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="27704-157">Teams</span></span>

<span data-ttu-id="27704-158">Um die Abwärtskompatibilität Ihrer adaptiven Karten mit älteren Versionen von Teams sicherzustellen, müssen Sie die `fallback`-Eigenschaft einschließen und ihren Wert auf `Action.Submit`festlegen.</span><span class="sxs-lookup"><span data-stu-id="27704-158">To ensure backward compatibility of your Adaptive Cards with older versions of Teams, you must include the `fallback` property and set its value to `Action.Submit`.</span></span> <span data-ttu-id="27704-159">Außerdem muss Ihr Botcode sowohl `Action.Execute` als auch `Action.Submit`verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="27704-159">Also, your bot code must process both `Action.Execute` and `Action.Submit`.</span></span>

<span data-ttu-id="27704-160">Weitere Informationen finden Sie unter [Abwärtskompatibilität in Teams](/adaptive-cards/authoring-cards/universal-action-model#teams).</span><span class="sxs-lookup"><span data-stu-id="27704-160">For more information, see [backward compatibility on Teams](/adaptive-cards/authoring-cards/universal-action-model#teams).</span></span>

## <a name="code-sample"></a><span data-ttu-id="27704-161">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="27704-161">Code sample</span></span>

|<span data-ttu-id="27704-162">Beispielname</span><span class="sxs-lookup"><span data-stu-id="27704-162">Sample name</span></span> | <span data-ttu-id="27704-163">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="27704-163">Description</span></span> | <span data-ttu-id="27704-164">.NETCore</span><span class="sxs-lookup"><span data-stu-id="27704-164">.NETCore</span></span> |
|----------------|-----------------|--------------|
| <span data-ttu-id="27704-165">Teams-Catering-Bot</span><span class="sxs-lookup"><span data-stu-id="27704-165">Teams catering bot</span></span> | <span data-ttu-id="27704-166">Erstellen Sie einen einfachen Bot, der mit adaptiven Karten eine Bestellung annimmt.</span><span class="sxs-lookup"><span data-stu-id="27704-166">Create a simple bot that accepts food order using Adaptive Cards.</span></span> |[<span data-ttu-id="27704-167">Anzeigen</span><span class="sxs-lookup"><span data-stu-id="27704-167">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/bot-teams-catering/csharp)|

## <a name="see-also"></a><span data-ttu-id="27704-168">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="27704-168">See also</span></span>

* [<span data-ttu-id="27704-169">Adaptive Kartenaktionen in Teams</span><span class="sxs-lookup"><span data-stu-id="27704-169">Adaptive Card actions in Teams</span></span>](~/task-modules-and-cards/cards/cards-actions.md#adaptive-cards-actions)
* [<span data-ttu-id="27704-170">Wie Bots funktionieren</span><span class="sxs-lookup"><span data-stu-id="27704-170">How bots work</span></span>](/azure/bot-service/bot-builder-basics?view=azure-bot-service-4.0&preserve-view=true)
