---
title: Erstellen von Apps für die Microsoft Teams Plattform
author: heath-hamilton
description: Erhalten Sie eine Übersicht darüber, wie Entwickler Microsoft Teams features mit benutzerdefinierten Apps erweitern können.
ms.topic: overview
localization_priority: Normal
ms.author: lajanuar
ms.date: 09/22/2020
ms.openlocfilehash: 69c36cf5f925bdb9802e7ec081a7765187a06128
ms.sourcegitcommit: 25c9ad27f99682caaa7347840578b118c63b8f69
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2021
ms.locfileid: "52101842"
---
# <a name="build-apps-for-microsoft-teams"></a><span data-ttu-id="2e032-103">Apps für Microsoft Teams erstellen</span><span class="sxs-lookup"><span data-stu-id="2e032-103">Build apps for Microsoft Teams</span></span>

<span data-ttu-id="2e032-104">Microsoft Teams apps bringen wichtige Informationen, allgemeine Tools und vertrauenswürdige Prozesse an die Stelle, an der Die Menschen zunehmend sammeln, lernen und arbeiten.</span><span class="sxs-lookup"><span data-stu-id="2e032-104">Microsoft Teams apps bring key information, common tools, and trusted processes to where people increasingly gather, learn, and work.</span></span>

<span data-ttu-id="2e032-105">Apps sind die Art und Weise, Teams Ihre Anforderungen erfüllen.</span><span class="sxs-lookup"><span data-stu-id="2e032-105">Apps are how you extend Teams to fit your needs.</span></span> <span data-ttu-id="2e032-106">Erstellen Sie etwas neues für Teams oder integrieren Sie eine vorhandene App.</span><span class="sxs-lookup"><span data-stu-id="2e032-106">Create something brand new for Teams or integrate an existing app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2e032-107">Beginnen Sie hier</span><span class="sxs-lookup"><span data-stu-id="2e032-107">Start here</span></span>](build-your-first-app/build-first-app-overview.md)

## <a name="what-are-teams-apps"></a><span data-ttu-id="2e032-108">Was sind Teams Apps?</span><span class="sxs-lookup"><span data-stu-id="2e032-108">What are Teams apps?</span></span>

<span data-ttu-id="2e032-109">Teams Apps sind eine Kombination aus [Funktionen und](concepts/capabilities-overview.md) [Einstiegspunkten.](concepts/extensibility-points.md)</span><span class="sxs-lookup"><span data-stu-id="2e032-109">Teams apps are a combination of [capabilities](concepts/capabilities-overview.md) and [entry points](concepts/extensibility-points.md).</span></span> <span data-ttu-id="2e032-110">Beispielsweise können Benutzer mit dem Bot *(Funktion)* Ihrer App in einem *Kanal* (Einstiegspunkt) chatten.</span><span class="sxs-lookup"><span data-stu-id="2e032-110">For example, people can chat with your app's *bot* (capability) in a *channel* (entry point).</span></span>

<span data-ttu-id="2e032-111">Einige Apps sind einfach (Benachrichtigungen senden), während andere komplex sind (Patientendatensätze verwalten).</span><span class="sxs-lookup"><span data-stu-id="2e032-111">Some apps are simple (send notifications), while others are complex (manage patient records).</span></span> <span data-ttu-id="2e032-112">Beachten Sie beim Planen Ihrer App, dass Teams ein Hub für die Zusammenarbeit ist.</span><span class="sxs-lookup"><span data-stu-id="2e032-112">When planning your app, remember that Teams is a collaboration hub.</span></span> <span data-ttu-id="2e032-113">Die besten Teams helfen, sich selbst zu ausdrücken und besser zusammen zu arbeiten.</span><span class="sxs-lookup"><span data-stu-id="2e032-113">The best Teams apps help people express themselves and work better together.</span></span>

:::row:::
   :::column span="":::

### <a name="tabs"></a><span data-ttu-id="2e032-114">Registerkarten</span><span class="sxs-lookup"><span data-stu-id="2e032-114">Tabs</span></span>

<span data-ttu-id="2e032-115">**Einfachere Informationen:** Manchmal müssen Sie die Suche vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="2e032-115">**Get information more conveniently**: Sometimes you just need to make things easier to find.</span></span> <span data-ttu-id="2e032-116">Zeigen Sie eine wichtige Webseite auf einer [Registerkarte an,](tabs/what-are-tabs.md)die eine Vollbildweberfahrung für statische und dynamische Inhalte in Teams.</span><span class="sxs-lookup"><span data-stu-id="2e032-116">Display an important webpage in a [tab](tabs/what-are-tabs.md), which provides a full-screen web experience for static and dynamic content in Teams.</span></span>

:::image type="content" source="assets/images/overview-tabs.png" alt-text="Konzeptionelle Darstellung des Aussehens von Registerkarten im Teams Client." border="false":::

   :::column-end:::

   :::column span="":::

### <a name="bots"></a><span data-ttu-id="2e032-118">Bots</span><span class="sxs-lookup"><span data-stu-id="2e032-118">Bots</span></span>

<span data-ttu-id="2e032-119">**Wörter in Aktionen verwandeln:** Unterhaltungen führen häufig dazu, dass sie etwas tun müssen (Eine Bestellung generieren, meinen Code überprüfen, ticketstatus überprüfen und so weiter).</span><span class="sxs-lookup"><span data-stu-id="2e032-119">**Turn words into actions**: Conversations often result in the need to do something (generate an order, review my code, check ticket status, and so on).</span></span> <span data-ttu-id="2e032-120">Ein [Bot](bots/what-are-bots.md) kann diese Arten von Workflows direkt innerhalb der Teams.</span><span class="sxs-lookup"><span data-stu-id="2e032-120">A [bot](bots/what-are-bots.md) can kick off these kinds of workflows right inside Teams.</span></span>

:::image type="content" source="assets/images/overview-bots.png" alt-text="Konzeptionelle Darstellung des Aussehens von Bots im Teams Client." border="false":::

   :::column-end:::

:::row-end:::

:::row:::

   :::column span="":::

### <a name="messaging-extensions"></a><span data-ttu-id="2e032-122">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="2e032-122">Messaging extensions</span></span>

<span data-ttu-id="2e032-123">**Vereinfachen Sie multitask:** Mit [Messagingerweiterungen](messaging-extensions/what-are-messaging-extensions.md)können Sie externe Informationen in einer Unterhaltung schnell freigeben.</span><span class="sxs-lookup"><span data-stu-id="2e032-123">**Make it easier to multitask**: With [messaging extensions](messaging-extensions/what-are-messaging-extensions.md), you can quickly share external information in a conversation.</span></span> <span data-ttu-id="2e032-124">Sie können auch eine Nachricht verwenden, z. B. das Erstellen eines Hilfetickets basierend auf dem Inhalt eines Kanalbeitrags.</span><span class="sxs-lookup"><span data-stu-id="2e032-124">You also can act on a message, such as creating a help ticket based on the content of a channel post.</span></span>

:::image type="content" source="assets\images\overview-messaging.png" alt-text="Konzeptionelle Darstellung des Aussehens von Messagingerweiterungen im Teams Client." border="false":::

   :::column-end:::

   :::column span="":::

### <a name="webhooks"></a><span data-ttu-id="2e032-126">Webhooks</span><span class="sxs-lookup"><span data-stu-id="2e032-126">Webhooks</span></span>

<span data-ttu-id="2e032-127">**Kommunikation mit externen Apps:** [Eingehende Webhooks](webhooks-and-connectors/what-are-webhooks-and-connectors.md#incoming-webhooks) sind eine einfache Möglichkeit, Benachrichtigungen von einer anderen App automatisch an einen Teams senden.</span><span class="sxs-lookup"><span data-stu-id="2e032-127">**Communicate with external apps**: [Incoming webhooks](webhooks-and-connectors/what-are-webhooks-and-connectors.md#incoming-webhooks) are a simple way to automatically send notifications from another app to a Teams channel.</span></span> <span data-ttu-id="2e032-128">Mit [ausgehenden Webhooks](webhooks-and-connectors/what-are-webhooks-and-connectors.md#outgoing-webhooks)wird der Webdienst mit einem @mention.</span><span class="sxs-lookup"><span data-stu-id="2e032-128">With [outgoing webhooks](webhooks-and-connectors/what-are-webhooks-and-connectors.md#outgoing-webhooks), message your web service with an @mention.</span></span>

:::image type="content" source="assets/images/overview-connectors.png" alt-text="Konzeptionelle Darstellung des Aussehens von Connectors im Teams Client." border="false":::

   :::column-end:::
:::row-end:::

:::row:::

   :::column span="":::

### <a name="microsoft-graph-for-teams"></a><span data-ttu-id="2e032-130">Microsoft Graph für Teams</span><span class="sxs-lookup"><span data-stu-id="2e032-130">Microsoft Graph for Teams</span></span>

<span data-ttu-id="2e032-131">**Nutzen Teams** Daten: Die [Microsoft Graph-API für Teams](https://docs.microsoft.com/graph/teams-concept-overview) bietet Zugriff auf Informationen zu Teams, Kanälen, Benutzern und Nachrichten, mit deren Hilfe Sie Features für Ihre App erstellen oder verbessern können.</span><span class="sxs-lookup"><span data-stu-id="2e032-131">**Utilize Teams data**: The [Microsoft Graph API for Teams](https://docs.microsoft.com/graph/teams-concept-overview) provides access to information about teams, channels, users, and messages that can help you create or enhance features for your app.</span></span>

:::image type="content" source="assets/images/overview-graph.png" alt-text="Konzeptionelle Darstellung der Microsoft Graph-API für Teams." border="false":::

   :::column-end:::

   :::column span="":::
   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

## <a name="start-building"></a><span data-ttu-id="2e032-133">Erstellen beginnen</span><span class="sxs-lookup"><span data-stu-id="2e032-133">Start building</span></span>

<span data-ttu-id="2e032-134">Machen Sie sich schnell mit dem Erstellen von Teams vertraut, indem Sie Ihre Umgebung einrichten und eine einfache App erstellen.</span><span class="sxs-lookup"><span data-stu-id="2e032-134">Quickly familiarize yourself with building for Teams by setting up your environment and creating a simple app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2e032-135">Die erste App erstellen</span><span class="sxs-lookup"><span data-stu-id="2e032-135">Build your first app</span></span>](build-your-first-app/build-first-app-overview.md)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

## <a name="integrate-with-teams"></a><span data-ttu-id="2e032-136">Integration in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="2e032-136">Integrate with Teams</span></span>

<span data-ttu-id="2e032-137">Vermischen Sie die Features, die Benutzer an einer vorhandenen Web-App, einem Dienst oder system lieben, mit den features für die Zusammenarbeit Teams.</span><span class="sxs-lookup"><span data-stu-id="2e032-137">Blend the features users love about an existing web app, service, or system with the collaborative features of Teams.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2e032-138">Integrieren einer vorhandenen App</span><span class="sxs-lookup"><span data-stu-id="2e032-138">Integrate an existing app</span></span>](samples/integrating-web-apps.md)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

## <a name="a-little-code-goes-a-long-way"></a><span data-ttu-id="2e032-139">Ein wenig Code geht weit</span><span class="sxs-lookup"><span data-stu-id="2e032-139">A little code goes a long way</span></span>

<span data-ttu-id="2e032-140">Sie müssen kein erfahrener Programmierer sein, um eine großartige app Teams erstellen.</span><span class="sxs-lookup"><span data-stu-id="2e032-140">You don't need to be an expert programmer to build a great Teams app.</span></span> <span data-ttu-id="2e032-141">Testen Sie eine von mehreren Low-Code-Lösungen.</span><span class="sxs-lookup"><span data-stu-id="2e032-141">Try one of several low-code solutions.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2e032-142">Erstellen einer Low-Code-App</span><span class="sxs-lookup"><span data-stu-id="2e032-142">Create a low-code app</span></span>](samples/teams-low-code-solutions.md)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

## <a name="get-ideas-for-your-app"></a><span data-ttu-id="2e032-143">Ideen für Ihre App erhalten</span><span class="sxs-lookup"><span data-stu-id="2e032-143">Get ideas for your app</span></span>

<span data-ttu-id="2e032-144">Suchen Sie nach Inspiration für die App-Entwicklung?</span><span class="sxs-lookup"><span data-stu-id="2e032-144">Looking for app development inspiration?</span></span> <span data-ttu-id="2e032-145">Durchsuchen Sie unsere Liste mit realen Szenarien und Branchenlösungen mit Konzepten mit hoher Genauigkeit, um die verschiedenen Möglichkeiten zu verstehen, Teams Apps Ihren Benutzern helfen können.</span><span class="sxs-lookup"><span data-stu-id="2e032-145">Browse our list of real-world scenarios and industry solutions with high fidelity concept mocks to understand the various ways Teams apps can help your users.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2e032-146">Siehe App-Szenarien</span><span class="sxs-lookup"><span data-stu-id="2e032-146">See app scenarios</span></span>](https://adoption.microsoft.com/extensibility-look-book/scenarios/)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

## <a name="see-also"></a><span data-ttu-id="2e032-147">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="2e032-147">See also</span></span>

* [<span data-ttu-id="2e032-148">Hinzufügen einer Share-to-Teams-Schaltfläche zu Ihrer Website</span><span class="sxs-lookup"><span data-stu-id="2e032-148">Add a Share-to-Teams button to your website</span></span>](concepts/build-and-test/share-to-teams.md)
* [<span data-ttu-id="2e032-149">Entwerfen Ihrer Teams App</span><span class="sxs-lookup"><span data-stu-id="2e032-149">Design your Teams app</span></span>](concepts/design/design-teams-app-overview.md)
* [<span data-ttu-id="2e032-150">Microsoft Teams JavaScript-Client-SDK</span><span class="sxs-lookup"><span data-stu-id="2e032-150">Microsoft Teams JavaScript client SDK</span></span>](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/?view=msteams-client-js-latest&preserve-view=true)
* <span data-ttu-id="2e032-151">Bot Framework SDK für [JavaScript](https://github.com/Microsoft/botbuilder-js) und [.NET](https://github.com/Microsoft/botbuilder-dotnet/)</span><span class="sxs-lookup"><span data-stu-id="2e032-151">Bot Framework SDK for [JavaScript](https://github.com/Microsoft/botbuilder-js) and [.NET](https://github.com/Microsoft/botbuilder-dotnet/)</span></span>
* [<span data-ttu-id="2e032-152">Verteilen Ihrer Teams App</span><span class="sxs-lookup"><span data-stu-id="2e032-152">Distribute your Teams app</span></span>](concepts/deploy-and-publish/apps-publish-overview.md)
