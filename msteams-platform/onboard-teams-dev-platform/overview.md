---
title: Microsoft Teams-Entwicklerplattform
author: clearab
description: Übersicht darüber, wie Entwickler Microsoft Teams-Funktionen mithilfe der Teams-Plattform erweitern und anpassen können.
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: 73cbd4f68d8878872147bd412972495de1b5de6e
ms.sourcegitcommit: d3bb4bbcdff9545c9869647dcdbe563a2db868be
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/18/2020
ms.locfileid: "47964571"
---
# <a name="building-for-microsoft-teams"></a><span data-ttu-id="70f88-103">Erstellen für Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="70f88-103">Building for Microsoft Teams</span></span>

<span data-ttu-id="70f88-104">Microsoft Teams-apps bringen wichtige Informationen, gemeinsame Tools und vertrauenswürdige Prozesse dazu, wo Personen zunehmend sammeln, lernen und arbeiten.</span><span class="sxs-lookup"><span data-stu-id="70f88-104">Microsoft Teams apps bring key information, common tools, and trusted processes to where people increasingly gather, learn, and work.</span></span>

<span data-ttu-id="70f88-105">Mit apps erweitern Sie Teams entsprechend Ihren Anforderungen.</span><span class="sxs-lookup"><span data-stu-id="70f88-105">Apps are how you extend Teams to fit your needs.</span></span> <span data-ttu-id="70f88-106">Erstellen Sie etwas ganz neues für Teams oder integrieren Sie eine vorhandene app.</span><span class="sxs-lookup"><span data-stu-id="70f88-106">Create something brand new for Teams or integrate an existing app.</span></span>

## <a name="what-are-teams-apps"></a><span data-ttu-id="70f88-107">Was sind Microsoft Teams-apps?</span><span class="sxs-lookup"><span data-stu-id="70f88-107">What are Teams apps?</span></span>

<span data-ttu-id="70f88-108">Personen ermitteln und verwenden Teams-Apps über eine Reihe von Platt Form [Funktionen](capabilities-overview.md).</span><span class="sxs-lookup"><span data-stu-id="70f88-108">People discover and use Teams apps through a set of platform [capabilities](capabilities-overview.md).</span></span>

<span data-ttu-id="70f88-109">Einige apps sind einfach (Benachrichtigungen senden), andere sind komplex (Patientendatensätze anzeigen).</span><span class="sxs-lookup"><span data-stu-id="70f88-109">Some apps are simple (send notifications), while others are complex (view patient records).</span></span> <span data-ttu-id="70f88-110">Beachten Sie bei der Planung Ihrer APP, dass Teams ein Hub für die Zusammenarbeit sind.</span><span class="sxs-lookup"><span data-stu-id="70f88-110">When planning your app, remember that Teams is a collaboration hub.</span></span> <span data-ttu-id="70f88-111">Die besten Teams-Apps helfen Benutzern, sich selbst auszudrücken und besser zusammenzuarbeiten.</span><span class="sxs-lookup"><span data-stu-id="70f88-111">The best Teams apps help people express themselves and work better together.</span></span>

:::row:::
   :::column span="":::

### <a name="tabs"></a><span data-ttu-id="70f88-112">Registerkarten</span><span class="sxs-lookup"><span data-stu-id="70f88-112">Tabs</span></span>

<span data-ttu-id="70f88-113">**Erhalten Sie Informationen bequemer**: manchmal müssen Sie einfach nur die Suche vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="70f88-113">**Get information more conveniently**: Sometimes you just need to make things easier to find.</span></span> <span data-ttu-id="70f88-114">Zeigt eine wichtige Webseite auf einer [Registerkarte](../tabs/what-are-tabs.md)an, die eine Vollbildansicht für statischen und dynamischen Inhalt in Microsoft Teams bietet.</span><span class="sxs-lookup"><span data-stu-id="70f88-114">Display an important webpage in a [tab](../tabs/what-are-tabs.md), which provides a full-screen web experience for static and dynamic content in Teams.</span></span>

:::image type="content" source="doc-links/images/overview-tabs.png" alt-text="Konzeptionelle Darstellung dessen, was Registerkarten im Microsoft Teams-Client aussehen." border="false":::

   :::column-end:::
   :::column span="":::

### <a name="messaging-extensions"></a><span data-ttu-id="70f88-116">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="70f88-116">Messaging extensions</span></span>

<span data-ttu-id="70f88-117">**Vereinfachung des Multitaskings**: mit [Messaging-Erweiterungen](../messaging-extensions/what-are-messaging-extensions.md)können Sie in einer Unterhaltung externe Informationen schnell freigeben.</span><span class="sxs-lookup"><span data-stu-id="70f88-117">**Make it easier to multitask**: With [messaging extensions](../messaging-extensions/what-are-messaging-extensions.md), you can quickly share external information in a conversation.</span></span> <span data-ttu-id="70f88-118">Sie können auch auf eine Nachricht reagieren, beispielsweise das Erstellen eines Hilfe Tickets basierend auf dem Inhalt eines Kanal Beitrags.</span><span class="sxs-lookup"><span data-stu-id="70f88-118">You also can act on a message, such as creating a help ticket based on the content of a channel post.</span></span>

:::image type="content" source="doc-links/images/overview-messaging.png" alt-text="Konzeptionelle Darstellung, wie Messaging-Erweiterungen im Teams-Client aussehen." border="false":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::

### <a name="bots"></a><span data-ttu-id="70f88-120">Bots</span><span class="sxs-lookup"><span data-stu-id="70f88-120">Bots</span></span>

<span data-ttu-id="70f88-121">**Wörter in Aktionen umwandeln**: Unterhaltungen führen häufig dazu, dass Sie etwas tun müssen (Generieren einer Bestellung, Überprüfen des Codes, Überprüfen des Ticket Status usw.).</span><span class="sxs-lookup"><span data-stu-id="70f88-121">**Turn words into actions**: Conversations often result in the need to do something (generate an order, review my code, check ticket status, etc.).</span></span> <span data-ttu-id="70f88-122">Ein [bot](../bots/what-are-bots.md) kann diese Art von Workflows direkt innerhalb von Teams abstoßen.</span><span class="sxs-lookup"><span data-stu-id="70f88-122">A [bot](../bots/what-are-bots.md) can kick off these kinds of workflows right inside Teams.</span></span>

:::image type="content" source="doc-links/images/overview-bots.png" alt-text="Konzeptionelle Darstellung dessen, was Bots im Microsoft Teams-Client aussieht." border="false":::

   :::column-end:::
   :::column span="":::

### <a name="webhooks"></a><span data-ttu-id="70f88-124">Webhooks</span><span class="sxs-lookup"><span data-stu-id="70f88-124">Webhooks</span></span>

<span data-ttu-id="70f88-125">**Kommunikation mit externen apps**: [eingehende webhooks](../webhooks-and-connectors/what-are-webhooks-and-connectors.md#incoming-webhooks) stellen eine einfache Möglichkeit zum automatischen Senden von Benachrichtigungen von einer anderen APP an einen Teams-Kanal dar.</span><span class="sxs-lookup"><span data-stu-id="70f88-125">**Communicate with external apps**: [Incoming webhooks](../webhooks-and-connectors/what-are-webhooks-and-connectors.md#incoming-webhooks) are a simple way to automatically send notifications from another app to a Teams channel.</span></span> <span data-ttu-id="70f88-126">Mit [ausgehenden webhooks](../webhooks-and-connectors/what-are-webhooks-and-connectors.md#outgoing-webhooks)senden Sie Ihrem Webdienst eine Nachricht mit einem @mention.</span><span class="sxs-lookup"><span data-stu-id="70f88-126">With [outgoing webhooks](../webhooks-and-connectors/what-are-webhooks-and-connectors.md#outgoing-webhooks), message your web service with an @mention.</span></span>

:::image type="content" source="doc-links/images/overview-connectors.png" alt-text="Konzeptionelle Darstellung dessen, was Konnektoren im Teams-Client aussieht." border="false":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::

### <a name="microsoft-graph-for-teams"></a><span data-ttu-id="70f88-128">Microsoft Graph für Teams</span><span class="sxs-lookup"><span data-stu-id="70f88-128">Microsoft Graph for Teams</span></span>

<span data-ttu-id="70f88-129">**Verwenden von Teams-Daten**: die [Microsoft Graph-Rest-API für Teams](https://docs.microsoft.com/graph/teams-concept-overview) bietet Zugriff auf Informationen zu Teams, Kanälen, Benutzern und Nachrichten, die Sie beim Erstellen oder Erweitern von Features für Ihre APP unterstützen können.</span><span class="sxs-lookup"><span data-stu-id="70f88-129">**Utilize Teams data**: The [Microsoft Graph REST API for Teams](https://docs.microsoft.com/graph/teams-concept-overview) provides access to information about teams, channels, users, and messages that can help you create or enhance features for your app.</span></span>

:::image type="content" source="doc-links/images/overview-graph.png" alt-text="Konzeptionelle Darstellung der Microsoft Graph-Rest-API für Teams." border="false":::

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

## <a name="get-started"></a><span data-ttu-id="70f88-131">Erste Schritte</span><span class="sxs-lookup"><span data-stu-id="70f88-131">Get started</span></span>

<span data-ttu-id="70f88-132">Wechseln Sie direkt mit unseren ersten App-Lernprogrammen, erfahren Sie, wie Sie vorhandene apps integrieren und importieren, oder nehmen Sie sich Zeit, um mehr über den Lebenszyklus der Teams-App-Entwicklung zu erfahren.</span><span class="sxs-lookup"><span data-stu-id="70f88-132">Jump right in with our first app tutorials, find out how to integrate and import existing apps, or take your time to learn about the Teams app development lifecycle.</span></span>

:::row:::
   :::column span="2":::

### <a name="start-building"></a><span data-ttu-id="70f88-133">Erstellen beginnen</span><span class="sxs-lookup"><span data-stu-id="70f88-133">Start building</span></span>

   <span data-ttu-id="70f88-134">Machen Sie sich schnell mit der Erstellung für Microsoft Teams vertraut, indem Sie eine einfache APP erstellen und einige häufig verwendete Funktionen hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="70f88-134">Quickly familiarize yourself with building for Teams by creating a simple app and adding some commonly used capabilities.</span></span>

   > [!div class="nextstepaction"]
   > [<span data-ttu-id="70f88-135">Erstellen Sie jetzt Ihre erste app.</span><span class="sxs-lookup"><span data-stu-id="70f88-135">Build your first app now</span></span>](build-your-first-app/building-real-world-app.md)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

### <a name="integrate-with-teams"></a><span data-ttu-id="70f88-136">Integration in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="70f88-136">Integrate with Teams</span></span>

   <span data-ttu-id="70f88-137">Verschmelzen Sie die Features, die Benutzer lieben, über eine vorhandene Webanwendung, einen Dienst oder ein System mit den kollaborativen Features von Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="70f88-137">Blend the features users love about an existing web app, service, or system with the collaborative features of Teams.</span></span>

   > [!div class="nextstepaction"]
   > [<span data-ttu-id="70f88-138">Integrieren einer vorhandenen APP</span><span class="sxs-lookup"><span data-stu-id="70f88-138">Integrate an existing app</span></span>](migrating-web-apps.md)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

### <a name="a-little-code-goes-a-long-way"></a><span data-ttu-id="70f88-139">Ein kleiner Code geht ein langer Weg</span><span class="sxs-lookup"><span data-stu-id="70f88-139">A little code goes a long way</span></span>

   <span data-ttu-id="70f88-140">Sie müssen kein Experte Programmierer sein, um eine großartige Teams-APP zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="70f88-140">You don't need to be an expert programmer to build a great Teams app.</span></span> <span data-ttu-id="70f88-141">Versuchen Sie eine von mehreren Lösungen mit niedrigem Code.</span><span class="sxs-lookup"><span data-stu-id="70f88-141">Try one of several low-code solutions.</span></span>

   > [!div class="nextstepaction"]
   > [<span data-ttu-id="70f88-142">Erstellen einer Low-Code-APP</span><span class="sxs-lookup"><span data-stu-id="70f88-142">Create a low-code app</span></span>](low-code-solutions.md)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

### <a name="trust-the-process"></a><span data-ttu-id="70f88-143">Dem Prozess Vertrauen</span><span class="sxs-lookup"><span data-stu-id="70f88-143">Trust the process</span></span>

   <span data-ttu-id="70f88-144">Erfahren Sie mehr über den gesamten Entwicklungsprozess für Teams-Plattformen, um eine APP für Ihre Organisation oder andere effektiv zu planen, zu entwerfen, zu erstellen und zu veröffentlichen.</span><span class="sxs-lookup"><span data-stu-id="70f88-144">Learn the entire Teams platform development process to effectively plan, design, build, and publish an app for your organization or anyone.</span></span>

   > [!div class="nextstepaction"]
   > [<span data-ttu-id="70f88-145">Starten der Planung Ihrer APP</span><span class="sxs-lookup"><span data-stu-id="70f88-145">Start planning your app</span></span>](../concepts/extensibility-points.md)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

## <a name="resources"></a><span data-ttu-id="70f88-146">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="70f88-146">Resources</span></span>

* [<span data-ttu-id="70f88-147">Hinzufügen einer Freigabe zur Schaltfläche "Teams" zu Ihrer Website</span><span class="sxs-lookup"><span data-stu-id="70f88-147">Add a Share to Teams button to your website</span></span>](../concepts/build-and-test/share-to-teams.md)
* [<span data-ttu-id="70f88-148">Fluent-Entwurfs System</span><span class="sxs-lookup"><span data-stu-id="70f88-148">Fluent Design System</span></span>](https://fluentsite.z22.web.core.windows.net/)
* [<span data-ttu-id="70f88-149">Microsoft Teams-JavaScript-SDK</span><span class="sxs-lookup"><span data-stu-id="70f88-149">Microsoft Teams JavaScript SDK</span></span>](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/?view=msteams-client-js-latest&preserve-view=true)
* <span data-ttu-id="70f88-150">[Bot Framework SDK für JavaScript](https://github.com/Microsoft/botbuilder-js) und [bot Framework SDK für .net](https://github.com/Microsoft/botbuilder-dotnet/)</span><span class="sxs-lookup"><span data-stu-id="70f88-150">[Bot Framework SDK for JavaScript](https://github.com/Microsoft/botbuilder-js) and [Bot Framework SDK for .NET](https://github.com/Microsoft/botbuilder-dotnet/)</span></span>
* [<span data-ttu-id="70f88-151">Veröffentlichen Ihrer APP in einer Organisation oder AppSource</span><span class="sxs-lookup"><span data-stu-id="70f88-151">Publish your app to an organization or AppSource</span></span>](../concepts/deploy-and-publish/overview.md)
