---
title: Erstellen von Apps für die Microsoft Teams-Plattform
author: heath-hamilton
description: Verschaffen Sie sich einen Überblick darüber, wie Entwickler Microsoft Teams Funktionen mit benutzerdefinierten Apps erweitern können.
ms.topic: overview
localization_priority: Normal
ms.author: lajanuar
ms.date: 09/22/2020
ms.openlocfilehash: 8724b669476b11aa8cb1aca6d9586fc7ea42587d
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566509"
---
# <a name="build-apps-for-microsoft-teams"></a><span data-ttu-id="56dca-103">Apps für Microsoft Teams erstellen</span><span class="sxs-lookup"><span data-stu-id="56dca-103">Build apps for Microsoft Teams</span></span>

<span data-ttu-id="56dca-104">Microsoft Teams-Apps bringen wichtige Informationen, gemeinsame Tools und vertrauenswürdige Prozesse dort, wo sich Die Menschen zunehmend sammeln, lernen und arbeiten.</span><span class="sxs-lookup"><span data-stu-id="56dca-104">Microsoft Teams apps bring key information, common tools, and trusted processes to where people increasingly gather, learn, and work.</span></span>

<span data-ttu-id="56dca-105">Apps sind, wie Sie Teams erweitern, um Ihre Bedürfnisse zu erfüllen.</span><span class="sxs-lookup"><span data-stu-id="56dca-105">Apps are how you extend Teams to fit your needs.</span></span> <span data-ttu-id="56dca-106">Erstellen Sie etwas brandneues für Teams oder integrieren Sie eine vorhandene App.</span><span class="sxs-lookup"><span data-stu-id="56dca-106">Create something brand new for Teams or integrate an existing app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="56dca-107">Beginnen Sie hier</span><span class="sxs-lookup"><span data-stu-id="56dca-107">Start here</span></span>](build-your-first-app/build-first-app-overview.md)

## <a name="what-are-teams-apps"></a><span data-ttu-id="56dca-108">Was sind Teams Apps?</span><span class="sxs-lookup"><span data-stu-id="56dca-108">What are Teams apps?</span></span>

<span data-ttu-id="56dca-109">Teams-Apps sind eine Kombination aus [Funktionen](concepts/capabilities-overview.md) und [Einstiegspunkten](concepts/extensibility-points.md).</span><span class="sxs-lookup"><span data-stu-id="56dca-109">Teams apps are a combination of [capabilities](concepts/capabilities-overview.md) and [entry points](concepts/extensibility-points.md).</span></span> <span data-ttu-id="56dca-110">Beispielsweise können Personen mit dem *Bot* (Fähigkeit) Ihrer App in einem *Kanal* (Einstiegspunkt) chatten.</span><span class="sxs-lookup"><span data-stu-id="56dca-110">For example, people can chat with your app's *bot* (capability) in a *channel* (entry point).</span></span>

<span data-ttu-id="56dca-111">Einige Apps sind einfach (Benachrichtigungen senden), während andere komplex sind (Patientendatensätze verwalten).</span><span class="sxs-lookup"><span data-stu-id="56dca-111">Some apps are simple (send notifications), while others are complex (manage patient records).</span></span> <span data-ttu-id="56dca-112">Denken Sie bei der Planung Ihrer App daran, dass Teams ein Collaboration Hub ist.</span><span class="sxs-lookup"><span data-stu-id="56dca-112">When planning your app, remember that Teams is a collaboration hub.</span></span> <span data-ttu-id="56dca-113">Die besten Teams Apps helfen Menschen, sich auszudrücken und besser zusammenzuarbeiten.</span><span class="sxs-lookup"><span data-stu-id="56dca-113">The best Teams apps help people express themselves and work better together.</span></span>

:::row:::
   :::column span="":::

### <a name="tabs"></a><span data-ttu-id="56dca-114">Registerkarten</span><span class="sxs-lookup"><span data-stu-id="56dca-114">Tabs</span></span>

<span data-ttu-id="56dca-115">**Erhalten Sie Informationen bequemer**: Manchmal müssen Sie nur die Dinge einfacher zu finden.</span><span class="sxs-lookup"><span data-stu-id="56dca-115">**Get information more conveniently**: Sometimes you just need to make things easier to find.</span></span> <span data-ttu-id="56dca-116">Zeigen Sie eine wichtige Webseite in einer [Registerkarte](tabs/what-are-tabs.md)an, die ein Vollbild-Weberlebnis für statische und dynamische Inhalte in Teams bietet.</span><span class="sxs-lookup"><span data-stu-id="56dca-116">Display an important webpage in a [tab](tabs/what-are-tabs.md), which provides a full-screen web experience for static and dynamic content in Teams.</span></span>

:::image type="content" source="assets/images/overview-tabs.png" alt-text="Konzeptionelle Darstellung, wie Registerkarten im Teams Client aussehen." border="false":::

   :::column-end:::

   :::column span="":::

### <a name="bots"></a><span data-ttu-id="56dca-118">Bots</span><span class="sxs-lookup"><span data-stu-id="56dca-118">Bots</span></span>

<span data-ttu-id="56dca-119">**Wörter in Aktionen umwandeln:** Unterhaltungen führen oft dazu, dass sie etwas tun müssen (Erstellen einer Bestellung, Überprüfen meines Codes, Überprüfen des Ticketstatus usw.).</span><span class="sxs-lookup"><span data-stu-id="56dca-119">**Turn words into actions**: Conversations often result in the need to do something (generate an order, review my code, check ticket status, and so on).</span></span> <span data-ttu-id="56dca-120">Ein [Bot](bots/what-are-bots.md) kann diese Art von Workflows direkt in Teams starten.</span><span class="sxs-lookup"><span data-stu-id="56dca-120">A [bot](bots/what-are-bots.md) can kick off these kinds of workflows right inside Teams.</span></span>

:::image type="content" source="assets/images/overview-bots.png" alt-text="Konzeptuelle Darstellung dessen, wie Bots im Teams Client aussehen." border="false":::

   :::column-end:::

:::row-end:::

:::row:::

   :::column span="":::

### <a name="messaging-extensions"></a><span data-ttu-id="56dca-122">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="56dca-122">Messaging extensions</span></span>

<span data-ttu-id="56dca-123">**Machen Sie es einfacher Multitasking**: Mit [Messaging-Erweiterungen](messaging-extensions/what-are-messaging-extensions.md)können Sie schnell externe Informationen in einer Unterhaltung teilen.</span><span class="sxs-lookup"><span data-stu-id="56dca-123">**Make it easier to multitask**: With [messaging extensions](messaging-extensions/what-are-messaging-extensions.md), you can quickly share external information in a conversation.</span></span> <span data-ttu-id="56dca-124">Sie können auch auf eine Nachricht reagieren, z. B. ein Hilfeticket basierend auf dem Inhalt eines Kanalbeitrags erstellen.</span><span class="sxs-lookup"><span data-stu-id="56dca-124">You also can act on a message, such as creating a help ticket based on the content of a channel post.</span></span>

:::image type="content" source="assets\images\overview-messaging.png" alt-text="Konzeptionelle Darstellung, wie Messagingerweiterungen im Teams Client aussehen." border="false":::

   :::column-end:::

   :::column span="":::

### <a name="webhooks"></a><span data-ttu-id="56dca-126">Webhooks</span><span class="sxs-lookup"><span data-stu-id="56dca-126">Webhooks</span></span>

<span data-ttu-id="56dca-127">**Kommunizieren mit externen Apps**: [Eingehende Webhooks](webhooks-and-connectors/what-are-webhooks-and-connectors.md#incoming-webhooks) sind eine einfache Möglichkeit, Benachrichtigungen von einer anderen App automatisch an einen Teams Kanal zu senden.</span><span class="sxs-lookup"><span data-stu-id="56dca-127">**Communicate with external apps**: [Incoming webhooks](webhooks-and-connectors/what-are-webhooks-and-connectors.md#incoming-webhooks) are a simple way to automatically send notifications from another app to a Teams channel.</span></span> <span data-ttu-id="56dca-128">Mit [ausgehenden Webhooks](webhooks-and-connectors/what-are-webhooks-and-connectors.md#outgoing-webhooks), Nachricht An Ihren Webdienst mit einem @mention.</span><span class="sxs-lookup"><span data-stu-id="56dca-128">With [outgoing webhooks](webhooks-and-connectors/what-are-webhooks-and-connectors.md#outgoing-webhooks), message your web service with an @mention.</span></span>

:::image type="content" source="assets/images/overview-connectors.png" alt-text="Konzeptionelle Darstellung, wie Connectors im Teams Client aussehen." border="false":::

   :::column-end:::
:::row-end:::

:::row:::

   :::column span="":::

### <a name="microsoft-graph-for-teams"></a><span data-ttu-id="56dca-130">Microsoft Graph für Teams</span><span class="sxs-lookup"><span data-stu-id="56dca-130">Microsoft Graph for Teams</span></span>

<span data-ttu-id="56dca-131">**Verwenden Teams Daten:** Die [Microsoft Graph-API für Teams](/graph/teams-concept-overview) bietet Zugriff auf Informationen zu Teams, Kanälen, Benutzern und Nachrichten, mit denen Sie Funktionen für Ihre App erstellen oder verbessern können.</span><span class="sxs-lookup"><span data-stu-id="56dca-131">**Utilize Teams data**: The [Microsoft Graph API for Teams](/graph/teams-concept-overview) provides access to information about teams, channels, users, and messages that can help you create or enhance features for your app.</span></span>

:::image type="content" source="assets/images/overview-graph.png" alt-text="Konzeptionelle Darstellung der Microsoft Graph-API für Teams." border="false":::

   :::column-end:::

   :::column span="":::
   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

## <a name="start-building"></a><span data-ttu-id="56dca-133">Beginnen Sie mit dem Bau</span><span class="sxs-lookup"><span data-stu-id="56dca-133">Start building</span></span>

<span data-ttu-id="56dca-134">Machen Sie sich schnell mit dem Erstellen für Teams vertraut, indem Sie Ihre Umgebung einrichten und eine einfache App erstellen.</span><span class="sxs-lookup"><span data-stu-id="56dca-134">Quickly familiarize yourself with building for Teams by setting up your environment and creating a simple app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="56dca-135">Die erste App erstellen</span><span class="sxs-lookup"><span data-stu-id="56dca-135">Build your first app</span></span>](build-your-first-app/build-first-app-overview.md)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

## <a name="integrate-with-teams"></a><span data-ttu-id="56dca-136">Integration in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="56dca-136">Integrate with Teams</span></span>

<span data-ttu-id="56dca-137">Verschmelzen Sie die Funktionen, die Benutzer an einer vorhandenen Web-App, einem Dienst oder einem Vorhandenen System lieben, mit den kollaborativen Funktionen von Teams.</span><span class="sxs-lookup"><span data-stu-id="56dca-137">Blend the features users love about an existing web app, service, or system with the collaborative features of Teams.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="56dca-138">Integrieren einer vorhandenen App</span><span class="sxs-lookup"><span data-stu-id="56dca-138">Integrate an existing app</span></span>](samples/integrating-web-apps.md)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

## <a name="a-little-code-goes-a-long-way"></a><span data-ttu-id="56dca-139">Ein kleiner Code geht einen langen Weg</span><span class="sxs-lookup"><span data-stu-id="56dca-139">A little code goes a long way</span></span>

<span data-ttu-id="56dca-140">Sie müssen kein erfahrener Programmierer sein, um eine großartige Teams-App zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="56dca-140">You don't need to be an expert programmer to build a great Teams app.</span></span> <span data-ttu-id="56dca-141">Probieren Sie eine der verschiedenen Low-Code-Lösungen aus.</span><span class="sxs-lookup"><span data-stu-id="56dca-141">Try one of the several low-code solutions.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="56dca-142">Erstellen einer Low-Code-App</span><span class="sxs-lookup"><span data-stu-id="56dca-142">Create a low-code app</span></span>](samples/teams-low-code-solutions.md)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

## <a name="get-ideas-for-your-app"></a><span data-ttu-id="56dca-143">Holen Sie sich Ideen für Ihre App</span><span class="sxs-lookup"><span data-stu-id="56dca-143">Get ideas for your app</span></span>

<span data-ttu-id="56dca-144">Suchen Sie nach Inspiration für die App-Entwicklung?</span><span class="sxs-lookup"><span data-stu-id="56dca-144">Looking for app development inspiration?</span></span> <span data-ttu-id="56dca-145">Durchsuchen Sie unsere Liste der realen Szenarien und Branchenlösungen mit High-Fidelity-Konzept-Mocks, um zu verstehen, wie Teams Apps Ihren Benutzern helfen können.</span><span class="sxs-lookup"><span data-stu-id="56dca-145">Browse our list of real-world scenarios and industry solutions with high fidelity concept mocks to understand the various ways Teams apps can help your users.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="56dca-146">Siehe App-Szenarien</span><span class="sxs-lookup"><span data-stu-id="56dca-146">See app scenarios</span></span>](https://adoption.microsoft.com/extensibility-look-book/scenarios/)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

## <a name="see-also"></a><span data-ttu-id="56dca-147">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="56dca-147">See also</span></span>

* [<span data-ttu-id="56dca-148">Hinzufügen einer Schaltfläche "Share-to-Teams" zu Ihrer Website</span><span class="sxs-lookup"><span data-stu-id="56dca-148">Add a Share-to-Teams button to your website</span></span>](concepts/build-and-test/share-to-teams.md)
* [<span data-ttu-id="56dca-149">Entwerfen Sie Ihre Teams-App</span><span class="sxs-lookup"><span data-stu-id="56dca-149">Design your Teams app</span></span>](concepts/design/design-teams-app-overview.md)
* [<span data-ttu-id="56dca-150">Microsoft Teams JavaScript-Client-SDK</span><span class="sxs-lookup"><span data-stu-id="56dca-150">Microsoft Teams JavaScript client SDK</span></span>](/javascript/api/@microsoft/teams-js/?view=msteams-client-js-latest&preserve-view=true)
* <span data-ttu-id="56dca-151">Bot Framework SDK für [JavaScript](https://github.com/Microsoft/botbuilder-js) und [.NET](https://github.com/Microsoft/botbuilder-dotnet/)</span><span class="sxs-lookup"><span data-stu-id="56dca-151">Bot Framework SDK for [JavaScript](https://github.com/Microsoft/botbuilder-js) and [.NET](https://github.com/Microsoft/botbuilder-dotnet/)</span></span>
* [<span data-ttu-id="56dca-152">Verteilen Sie Ihre Teams-App</span><span class="sxs-lookup"><span data-stu-id="56dca-152">Distribute your Teams app</span></span>](concepts/deploy-and-publish/apps-publish-overview.md)
