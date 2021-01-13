---
title: Erstellen von Apps für die Microsoft Teams-Plattform
author: heath-hamilton
description: Erhalten Sie eine Übersicht darüber, wie Entwickler Microsoft Teams-Features mit benutzerdefinierten Apps erweitern können.
ms.topic: overview
ms.author: lajanuar
ms.date: 09/22/2020
ms.openlocfilehash: 45be2dd7d0e421ac331cfc02703f0b81eab3dfe5
ms.sourcegitcommit: 4539479289b43812eaae07a1c0f878bed815d2d2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/12/2021
ms.locfileid: "49797771"
---
# <a name="build-apps-for-microsoft-teams"></a><span data-ttu-id="2f1b3-103">Apps für Microsoft Teams erstellen</span><span class="sxs-lookup"><span data-stu-id="2f1b3-103">Build apps for Microsoft Teams</span></span>

<span data-ttu-id="2f1b3-104">Microsoft Teams-Apps bieten wichtige Informationen, allgemeine Tools und vertrauenswürdige Prozesse, in denen Benutzer zunehmend sammeln, lernen und arbeiten.</span><span class="sxs-lookup"><span data-stu-id="2f1b3-104">Microsoft Teams apps bring key information, common tools, and trusted processes to where people increasingly gather, learn, and work.</span></span>

<span data-ttu-id="2f1b3-105">Apps erweitern Teams so, dass sie Ihren Anforderungen entsprechen.</span><span class="sxs-lookup"><span data-stu-id="2f1b3-105">Apps are how you extend Teams to fit your needs.</span></span> <span data-ttu-id="2f1b3-106">Erstellen Sie etwas ganz Neues für Teams, oder integrieren Sie eine vorhandene App.</span><span class="sxs-lookup"><span data-stu-id="2f1b3-106">Create something brand new for Teams or integrate an existing app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="2f1b3-107">Beginnen Sie hier</span><span class="sxs-lookup"><span data-stu-id="2f1b3-107">Start here</span></span>](build-your-first-app/build-first-app-overview.md)

## <a name="what-are-teams-apps"></a><span data-ttu-id="2f1b3-108">Was sind Teams-Apps?</span><span class="sxs-lookup"><span data-stu-id="2f1b3-108">What are Teams apps?</span></span>

<span data-ttu-id="2f1b3-109">Teams Apps sind eine Kombination aus [Funktionen und](concepts/capabilities-overview.md) [Einstiegspunkten.](concepts/extensibility-points.md)</span><span class="sxs-lookup"><span data-stu-id="2f1b3-109">Teams apps are a combination of [capabilities](concepts/capabilities-overview.md) and [entry points](concepts/extensibility-points.md).</span></span> <span data-ttu-id="2f1b3-110">Beispielsweise können Benutzer mit dem Bot *(Funktion)* Ihrer App in einem *Kanal* (Einstiegspunkt) chatten.</span><span class="sxs-lookup"><span data-stu-id="2f1b3-110">For example, people can chat with your app's *bot* (capability) in a *channel* (entry point).</span></span>

<span data-ttu-id="2f1b3-111">Einige Apps sind einfach (Benachrichtigungen senden), während andere komplex sind (Patientendatensätze verwalten).</span><span class="sxs-lookup"><span data-stu-id="2f1b3-111">Some apps are simple (send notifications), while others are complex (manage patient records).</span></span> <span data-ttu-id="2f1b3-112">Denken Sie beim Planen Ihrer App daran, dass Teams ein Hub für die Zusammenarbeit ist.</span><span class="sxs-lookup"><span data-stu-id="2f1b3-112">When planning your app, remember that Teams is a collaboration hub.</span></span> <span data-ttu-id="2f1b3-113">Die besten Teams-Apps helfen, sich selbst zu ausdrücken und besser zusammen zu arbeiten.</span><span class="sxs-lookup"><span data-stu-id="2f1b3-113">The best Teams apps help people express themselves and work better together.</span></span>

:::row:::
   :::column span="":::

### <a name="tabs"></a><span data-ttu-id="2f1b3-114">Registerkarten</span><span class="sxs-lookup"><span data-stu-id="2f1b3-114">Tabs</span></span>

<span data-ttu-id="2f1b3-115">**Einfachere Informationen:** Manchmal müssen Sie die Suche vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="2f1b3-115">**Get information more conveniently**: Sometimes you just need to make things easier to find.</span></span> <span data-ttu-id="2f1b3-116">Zeigen Sie eine wichtige Webseite auf einer [Registerkarte](tabs/what-are-tabs.md)an, die eine Vollbildweberfahrung für statische und dynamische Inhalte in Teams bietet.</span><span class="sxs-lookup"><span data-stu-id="2f1b3-116">Display an important webpage in a [tab](tabs/what-are-tabs.md), which provides a full-screen web experience for static and dynamic content in Teams.</span></span>

:::image type="content" source="assets/images/overview-tabs.png" alt-text="Konzeptionelle Darstellung, wie Registerkarten im Teams-Client aussehen." border="false":::

   :::column-end:::

   :::column span="":::

### <a name="bots"></a><span data-ttu-id="2f1b3-118">Bots</span><span class="sxs-lookup"><span data-stu-id="2f1b3-118">Bots</span></span>

<span data-ttu-id="2f1b3-119">**Machen Sie Wörter in Aktionen:** Unterhaltungen führen häufig dazu, dass sie eine Aktion ausführen müssen (Eine Bestellung generieren, meinen Code überprüfen, den Ticketstatus überprüfen usw.).</span><span class="sxs-lookup"><span data-stu-id="2f1b3-119">**Turn words into actions**: Conversations often result in the need to do something (generate an order, review my code, check ticket status, etc.).</span></span> <span data-ttu-id="2f1b3-120">Ein [Bot](bots/what-are-bots.md) kann diese Arten von Workflows direkt in Teams starten.</span><span class="sxs-lookup"><span data-stu-id="2f1b3-120">A [bot](bots/what-are-bots.md) can kick off these kinds of workflows right inside Teams.</span></span>

:::image type="content" source="assets/images/overview-bots.png" alt-text="Konzeptionelle Darstellung, wie Bots im Teams-Client aussehen." border="false":::

   :::column-end:::

:::row-end:::

:::row:::

   :::column span="":::

### <a name="messaging-extensions"></a><span data-ttu-id="2f1b3-122">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="2f1b3-122">Messaging extensions</span></span>

<span data-ttu-id="2f1b3-123">**Einfacheres Multitask:** [Mit](messaging-extensions/what-are-messaging-extensions.md)Messagingerweiterungen können Sie externe Informationen in einer Unterhaltung schnell freigeben.</span><span class="sxs-lookup"><span data-stu-id="2f1b3-123">**Make it easier to multitask**: With [messaging extensions](messaging-extensions/what-are-messaging-extensions.md), you can quickly share external information in a conversation.</span></span> <span data-ttu-id="2f1b3-124">Sie können auch auf eine Nachricht ein, z. B. das Erstellen eines Hilfetickets basierend auf dem Inhalt eines Kanalbeitrags.</span><span class="sxs-lookup"><span data-stu-id="2f1b3-124">You also can act on a message, such as creating a help ticket based on the content of a channel post.</span></span>

:::image type="content" source="assets\images\overview-messaging.png" alt-text="Konzeptionelle Darstellung, wie Messagingerweiterungen im Teams-Client aussehen." border="false":::

   :::column-end:::

   :::column span="":::

### <a name="webhooks"></a><span data-ttu-id="2f1b3-126">Webhooks</span><span class="sxs-lookup"><span data-stu-id="2f1b3-126">Webhooks</span></span>

<span data-ttu-id="2f1b3-127">**Kommunikation mit externen Apps:** [Eingehende Webhooks](webhooks-and-connectors/what-are-webhooks-and-connectors.md#incoming-webhooks) sind eine einfache Möglichkeit zum automatischen Senden von Benachrichtigungen von einer anderen App an einen Teams-Kanal.</span><span class="sxs-lookup"><span data-stu-id="2f1b3-127">**Communicate with external apps**: [Incoming webhooks](webhooks-and-connectors/what-are-webhooks-and-connectors.md#incoming-webhooks) are a simple way to automatically send notifications from another app to a Teams channel.</span></span> <span data-ttu-id="2f1b3-128">Nachricht [bei ausgehenden Webhooks](webhooks-and-connectors/what-are-webhooks-and-connectors.md#outgoing-webhooks)an Ihren Webdienst mit @mention.</span><span class="sxs-lookup"><span data-stu-id="2f1b3-128">With [outgoing webhooks](webhooks-and-connectors/what-are-webhooks-and-connectors.md#outgoing-webhooks), message your web service with an @mention.</span></span>

:::image type="content" source="assets/images/overview-connectors.png" alt-text="Konzeptionelle Darstellung, wie Connectors im Teams-Client aussehen." border="false":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::

### <a name="microsoft-graph-for-teams"></a><span data-ttu-id="2f1b3-130">Microsoft Graph für Teams</span><span class="sxs-lookup"><span data-stu-id="2f1b3-130">Microsoft Graph for Teams</span></span>

<span data-ttu-id="2f1b3-131">**Nutzen von Teams-Daten:** Die [Microsoft Graph-API](https://docs.microsoft.com/graph/teams-concept-overview) für Teams bietet Zugriff auf Informationen zu Teams, Kanälen, Benutzern und Nachrichten, mit deren Hilfe Sie Features für Ihre App erstellen oder verbessern können.</span><span class="sxs-lookup"><span data-stu-id="2f1b3-131">**Utilize Teams data**: The [Microsoft Graph API for Teams](https://docs.microsoft.com/graph/teams-concept-overview) provides access to information about teams, channels, users, and messages that can help you create or enhance features for your app.</span></span>

:::image type="content" source="assets/images/overview-graph.png" alt-text="Konzeptionelle Darstellung der Microsoft Graph-API für Teams." border="false":::

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

## <a name="start-building"></a><span data-ttu-id="2f1b3-133">Mit dem Erstellen beginnen</span><span class="sxs-lookup"><span data-stu-id="2f1b3-133">Start building</span></span>

   <span data-ttu-id="2f1b3-134">Machen Sie sich schnell mit dem Erstellen für Teams vertraut, indem Sie eine einfache App erstellen und einige häufig verwendete Funktionen hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="2f1b3-134">Quickly familiarize yourself with building for Teams by creating a simple app and adding some commonly used capabilities.</span></span>

   > [!div class="nextstepaction"]
   > [<span data-ttu-id="2f1b3-135">Erstellen Ihrer ersten App jetzt</span><span class="sxs-lookup"><span data-stu-id="2f1b3-135">Build your first app now</span></span>](build-your-first-app/build-first-app-overview.md)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

## <a name="integrate-with-teams"></a><span data-ttu-id="2f1b3-136">Integration in Teams</span><span class="sxs-lookup"><span data-stu-id="2f1b3-136">Integrate with Teams</span></span>

   <span data-ttu-id="2f1b3-137">Vermischen Sie die Features, die Benutzer über eine vorhandene Web-App, einen Dienst oder ein System mit den Features für die Zusammenarbeit von Teams haben.</span><span class="sxs-lookup"><span data-stu-id="2f1b3-137">Blend the features users love about an existing web app, service, or system with the collaborative features of Teams.</span></span>

   > [!div class="nextstepaction"]
   > [<span data-ttu-id="2f1b3-138">Integrieren einer vorhandenen App</span><span class="sxs-lookup"><span data-stu-id="2f1b3-138">Integrate an existing app</span></span>](samples/integrating-web-apps.md)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

## <a name="a-little-code-goes-a-long-way"></a><span data-ttu-id="2f1b3-139">Ein wenig Code ist ein langer Weg</span><span class="sxs-lookup"><span data-stu-id="2f1b3-139">A little code goes a long way</span></span>

   <span data-ttu-id="2f1b3-140">Sie müssen kein erfahrener Programmierer sein, um eine großartige Teams-App zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="2f1b3-140">You don't need to be an expert programmer to build a great Teams app.</span></span> <span data-ttu-id="2f1b3-141">Probieren Sie eine von mehreren Low-Code-Lösungen aus.</span><span class="sxs-lookup"><span data-stu-id="2f1b3-141">Try one of several low-code solutions.</span></span>

   > [!div class="nextstepaction"]
   > [<span data-ttu-id="2f1b3-142">Erstellen einer App mit geringem Code</span><span class="sxs-lookup"><span data-stu-id="2f1b3-142">Create a low-code app</span></span>](samples/teams-low-code-solutions.md)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

## <a name="resources"></a><span data-ttu-id="2f1b3-143">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="2f1b3-143">Resources</span></span>

* [<span data-ttu-id="2f1b3-144">Hinzufügen einer Share-to-Teams-Schaltfläche zu Ihrer Website</span><span class="sxs-lookup"><span data-stu-id="2f1b3-144">Add a Share-to-Teams button to your website</span></span>](concepts/build-and-test/share-to-teams.md)
* <span data-ttu-id="2f1b3-145"><a href="https://fluentsite.z22.web.core.windows.net/" target="_blank">Fluent-Benutzeroberfläche</a></span><span class="sxs-lookup"><span data-stu-id="2f1b3-145"><a href="https://fluentsite.z22.web.core.windows.net/" target="_blank">Fluent UI</a></span></span>
* [<span data-ttu-id="2f1b3-146">Microsoft Teams JavaScript client SDK</span><span class="sxs-lookup"><span data-stu-id="2f1b3-146">Microsoft Teams JavaScript client SDK</span></span>](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/?view=msteams-client-js-latest&preserve-view=true)
* <span data-ttu-id="2f1b3-147">[Bot Framework SDK für JavaScript](https://github.com/Microsoft/botbuilder-js) und [Bot Framework SDK für .NET](https://github.com/Microsoft/botbuilder-dotnet/)</span><span class="sxs-lookup"><span data-stu-id="2f1b3-147">[Bot Framework SDK for JavaScript](https://github.com/Microsoft/botbuilder-js) and [Bot Framework SDK for .NET](https://github.com/Microsoft/botbuilder-dotnet/)</span></span>
* [<span data-ttu-id="2f1b3-148">Veröffentlichen Ihrer App in einer Organisation oder AppSource</span><span class="sxs-lookup"><span data-stu-id="2f1b3-148">Publish your app to an organization or AppSource</span></span>](concepts/deploy-and-publish/overview.md)
