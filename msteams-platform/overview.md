---
title: Erstellen von Apps für die Microsoft Teams-Plattform
author: heath-hamilton
description: Übersicht darüber, wie Entwickler Microsoft Teams-Features mit benutzerdefinierten apps erweitern und anpassen können.
ms.topic: overview
ms.author: lajanuar
ms.date: 09/22/2020
ms.openlocfilehash: 6f5f3454885320669ef42383529d39fcfcfdfee8
ms.sourcegitcommit: c102da958759c13aa9e0f81bde1cffb34a8bef34
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/09/2020
ms.locfileid: "49604787"
---
# <a name="build-apps-for-microsoft-teams"></a><span data-ttu-id="8a091-103">Apps für Microsoft Teams erstellen</span><span class="sxs-lookup"><span data-stu-id="8a091-103">Build apps for Microsoft Teams</span></span>

<span data-ttu-id="8a091-104">Microsoft Teams-apps bringen wichtige Informationen, gemeinsame Tools und vertrauenswürdige Prozesse dazu, wo Personen zunehmend sammeln, lernen und arbeiten.</span><span class="sxs-lookup"><span data-stu-id="8a091-104">Microsoft Teams apps bring key information, common tools, and trusted processes to where people increasingly gather, learn, and work.</span></span>

<span data-ttu-id="8a091-105">Mit apps erweitern Sie Teams entsprechend Ihren Anforderungen.</span><span class="sxs-lookup"><span data-stu-id="8a091-105">Apps are how you extend Teams to fit your needs.</span></span> <span data-ttu-id="8a091-106">Erstellen Sie etwas ganz neues für Teams oder integrieren Sie eine vorhandene app.</span><span class="sxs-lookup"><span data-stu-id="8a091-106">Create something brand new for Teams or integrate an existing app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="8a091-107">Beginnen Sie hier</span><span class="sxs-lookup"><span data-stu-id="8a091-107">Start here</span></span>](build-your-first-app/build-first-app-overview.md)

## <a name="what-are-teams-apps"></a><span data-ttu-id="8a091-108">Was sind Microsoft Teams-apps?</span><span class="sxs-lookup"><span data-stu-id="8a091-108">What are Teams apps?</span></span>

<span data-ttu-id="8a091-109">Microsoft Teams-apps sind eine Kombination aus [Funktionen](concepts/capabilities-overview.md) und [Einstiegspunkten](concepts/extensibility-points.md).</span><span class="sxs-lookup"><span data-stu-id="8a091-109">Teams apps are a combination of [capabilities](concepts/capabilities-overview.md) and [entry points](concepts/extensibility-points.md).</span></span> <span data-ttu-id="8a091-110">Beispielsweise können Personen mit dem *bot* (Funktion) Ihrer APP in einem *Kanal* (Einstiegspunkte) chatten.</span><span class="sxs-lookup"><span data-stu-id="8a091-110">For example, people can chat with your app's *bot* (capability) in a *channel* (entry point).</span></span>

<span data-ttu-id="8a091-111">Einige apps sind einfach (Benachrichtigungen senden), andere sind komplex (Verwalten von Patientendatensätzen).</span><span class="sxs-lookup"><span data-stu-id="8a091-111">Some apps are simple (send notifications), while others are complex (manage patient records).</span></span> <span data-ttu-id="8a091-112">Beachten Sie bei der Planung Ihrer APP, dass Teams ein Hub für die Zusammenarbeit sind.</span><span class="sxs-lookup"><span data-stu-id="8a091-112">When planning your app, remember that Teams is a collaboration hub.</span></span> <span data-ttu-id="8a091-113">Die besten Teams-Apps helfen Benutzern, sich selbst auszudrücken und besser zusammenzuarbeiten.</span><span class="sxs-lookup"><span data-stu-id="8a091-113">The best Teams apps help people express themselves and work better together.</span></span>

:::row:::
   :::column span="":::

### <a name="tabs"></a><span data-ttu-id="8a091-114">Registerkarten</span><span class="sxs-lookup"><span data-stu-id="8a091-114">Tabs</span></span>

<span data-ttu-id="8a091-115">**Erhalten Sie Informationen bequemer**: manchmal müssen Sie einfach nur die Suche vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="8a091-115">**Get information more conveniently**: Sometimes you just need to make things easier to find.</span></span> <span data-ttu-id="8a091-116">Zeigt eine wichtige Webseite auf einer [Registerkarte](tabs/what-are-tabs.md)an, die eine Vollbildansicht für statischen und dynamischen Inhalt in Microsoft Teams bietet.</span><span class="sxs-lookup"><span data-stu-id="8a091-116">Display an important webpage in a [tab](tabs/what-are-tabs.md), which provides a full-screen web experience for static and dynamic content in Teams.</span></span>

:::image type="content" source="assets/images/overview-tabs.png" alt-text="Konzeptionelle Darstellung dessen, was Registerkarten im Microsoft Teams-Client aussehen." border="false":::

   :::column-end:::
   :::column span="":::

### <a name="messaging-extensions"></a><span data-ttu-id="8a091-118">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="8a091-118">Messaging extensions</span></span>

<span data-ttu-id="8a091-119">**Vereinfachung des Multitaskings**: mit [Messaging-Erweiterungen](messaging-extensions/what-are-messaging-extensions.md)können Sie in einer Unterhaltung externe Informationen schnell freigeben.</span><span class="sxs-lookup"><span data-stu-id="8a091-119">**Make it easier to multitask**: With [messaging extensions](messaging-extensions/what-are-messaging-extensions.md), you can quickly share external information in a conversation.</span></span> <span data-ttu-id="8a091-120">Sie können auch auf eine Nachricht reagieren, beispielsweise das Erstellen eines Hilfe Tickets basierend auf dem Inhalt eines Kanal Beitrags.</span><span class="sxs-lookup"><span data-stu-id="8a091-120">You also can act on a message, such as creating a help ticket based on the content of a channel post.</span></span>

:::image type="content" source="assets\images\overview-messaging.png" alt-text="Konzeptionelle Darstellung, wie Messaging-Erweiterungen im Teams-Client aussehen." border="false":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::

### <a name="bots"></a><span data-ttu-id="8a091-122">Bots</span><span class="sxs-lookup"><span data-stu-id="8a091-122">Bots</span></span>

<span data-ttu-id="8a091-123">**Wörter in Aktionen umwandeln**: Unterhaltungen führen häufig dazu, dass Sie etwas tun müssen (Generieren einer Bestellung, Überprüfen des Codes, Überprüfen des Ticket Status usw.).</span><span class="sxs-lookup"><span data-stu-id="8a091-123">**Turn words into actions**: Conversations often result in the need to do something (generate an order, review my code, check ticket status, etc.).</span></span> <span data-ttu-id="8a091-124">Ein [bot](bots/what-are-bots.md) kann diese Art von Workflows direkt innerhalb von Teams abstoßen.</span><span class="sxs-lookup"><span data-stu-id="8a091-124">A [bot](bots/what-are-bots.md) can kick off these kinds of workflows right inside Teams.</span></span>

:::image type="content" source="assets/images/overview-bots.png" alt-text="Konzeptionelle Darstellung dessen, was Bots im Microsoft Teams-Client aussieht." border="false":::

   :::column-end:::
   :::column span="":::

### <a name="webhooks"></a><span data-ttu-id="8a091-126">Webhooks</span><span class="sxs-lookup"><span data-stu-id="8a091-126">Webhooks</span></span>

<span data-ttu-id="8a091-127">**Kommunikation mit externen apps**: [eingehende webhooks](webhooks-and-connectors/what-are-webhooks-and-connectors.md#incoming-webhooks) stellen eine einfache Möglichkeit zum automatischen Senden von Benachrichtigungen von einer anderen APP an einen Teams-Kanal dar.</span><span class="sxs-lookup"><span data-stu-id="8a091-127">**Communicate with external apps**: [Incoming webhooks](webhooks-and-connectors/what-are-webhooks-and-connectors.md#incoming-webhooks) are a simple way to automatically send notifications from another app to a Teams channel.</span></span> <span data-ttu-id="8a091-128">Mit [ausgehenden webhooks](webhooks-and-connectors/what-are-webhooks-and-connectors.md#outgoing-webhooks)senden Sie Ihrem Webdienst eine Nachricht mit einem @mention.</span><span class="sxs-lookup"><span data-stu-id="8a091-128">With [outgoing webhooks](webhooks-and-connectors/what-are-webhooks-and-connectors.md#outgoing-webhooks), message your web service with an @mention.</span></span>

:::image type="content" source="assets/images/overview-connectors.png" alt-text="Konzeptionelle Darstellung dessen, was Konnektoren im Teams-Client aussieht." border="false":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::

### <a name="microsoft-graph-for-teams"></a><span data-ttu-id="8a091-130">Microsoft Graph für Teams</span><span class="sxs-lookup"><span data-stu-id="8a091-130">Microsoft Graph for Teams</span></span>

<span data-ttu-id="8a091-131">**Verwenden von Teams-Daten**: die [Microsoft Graph-API für Teams](https://docs.microsoft.com/graph/teams-concept-overview) bietet Zugriff auf Informationen zu Teams, Kanälen, Benutzern und Nachrichten, die Sie beim Erstellen oder Erweitern von Features für Ihre APP unterstützen können.</span><span class="sxs-lookup"><span data-stu-id="8a091-131">**Utilize Teams data**: The [Microsoft Graph API for Teams](https://docs.microsoft.com/graph/teams-concept-overview) provides access to information about teams, channels, users, and messages that can help you create or enhance features for your app.</span></span>

:::image type="content" source="assets/images/overview-graph.png" alt-text="Konzeptionelle Darstellung der Microsoft Graph-API für Teams." border="false":::

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

## <a name="get-started"></a><span data-ttu-id="8a091-133">Erste Schritte</span><span class="sxs-lookup"><span data-stu-id="8a091-133">Get started</span></span>

<span data-ttu-id="8a091-134">Wechseln Sie direkt mit unseren ersten App-Lernprogrammen, oder erfahren Sie, wie Sie vorhandene apps integrieren und importieren können.</span><span class="sxs-lookup"><span data-stu-id="8a091-134">Jump right in with our first app tutorials or find out how to integrate and import existing apps.</span></span>

:::row:::
   :::column span="2":::

### <a name="start-building"></a><span data-ttu-id="8a091-135">Erstellen beginnen</span><span class="sxs-lookup"><span data-stu-id="8a091-135">Start building</span></span>

   <span data-ttu-id="8a091-136">Machen Sie sich schnell mit der Erstellung für Microsoft Teams vertraut, indem Sie eine einfache APP erstellen und einige häufig verwendete Funktionen hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="8a091-136">Quickly familiarize yourself with building for Teams by creating a simple app and adding some commonly used capabilities.</span></span>

   > [!div class="nextstepaction"]
   > [<span data-ttu-id="8a091-137">Erstellen Sie jetzt Ihre erste app.</span><span class="sxs-lookup"><span data-stu-id="8a091-137">Build your first app now</span></span>](build-your-first-app/build-first-app-overview.md)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

### <a name="integrate-with-teams"></a><span data-ttu-id="8a091-138">Integration in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="8a091-138">Integrate with Teams</span></span>

   <span data-ttu-id="8a091-139">Verschmelzen Sie die Features, die Benutzer lieben, über eine vorhandene Webanwendung, einen Dienst oder ein System mit den kollaborativen Features von Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="8a091-139">Blend the features users love about an existing web app, service, or system with the collaborative features of Teams.</span></span>

   > [!div class="nextstepaction"]
   > [<span data-ttu-id="8a091-140">Integrieren einer vorhandenen APP</span><span class="sxs-lookup"><span data-stu-id="8a091-140">Integrate an existing app</span></span>](samples/integrating-web-apps.md)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

### <a name="a-little-code-goes-a-long-way"></a><span data-ttu-id="8a091-141">Ein kleiner Code geht ein langer Weg</span><span class="sxs-lookup"><span data-stu-id="8a091-141">A little code goes a long way</span></span>

   <span data-ttu-id="8a091-142">Sie müssen kein Experte Programmierer sein, um eine großartige Teams-APP zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="8a091-142">You don't need to be an expert programmer to build a great Teams app.</span></span> <span data-ttu-id="8a091-143">Versuchen Sie eine von mehreren Lösungen mit niedrigem Code.</span><span class="sxs-lookup"><span data-stu-id="8a091-143">Try one of several low-code solutions.</span></span>

   > [!div class="nextstepaction"]
   > [<span data-ttu-id="8a091-144">Erstellen einer Low-Code-APP</span><span class="sxs-lookup"><span data-stu-id="8a091-144">Create a low-code app</span></span>](samples/teams-low-code-solutions.md)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

## <a name="resources"></a><span data-ttu-id="8a091-145">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="8a091-145">Resources</span></span>

* [<span data-ttu-id="8a091-146">Hinzufügen einer Freigabe zur Schaltfläche "Teams" zu Ihrer Website</span><span class="sxs-lookup"><span data-stu-id="8a091-146">Add a Share to Teams button to your website</span></span>](concepts/build-and-test/share-to-teams.md)
* <span data-ttu-id="8a091-147"><a href="https://fluentsite.z22.web.core.windows.net/" target="_blank">Fluent-Benutzeroberfläche</a></span><span class="sxs-lookup"><span data-stu-id="8a091-147"><a href="https://fluentsite.z22.web.core.windows.net/" target="_blank">Fluent UI</a></span></span>
* [<span data-ttu-id="8a091-148">Microsoft Teams JavaScript-Client-SDK</span><span class="sxs-lookup"><span data-stu-id="8a091-148">Microsoft Teams JavaScript client SDK</span></span>](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/?view=msteams-client-js-latest&preserve-view=true)
* <span data-ttu-id="8a091-149">[Bot Framework SDK für JavaScript](https://github.com/Microsoft/botbuilder-js) und [bot Framework SDK für .net](https://github.com/Microsoft/botbuilder-dotnet/)</span><span class="sxs-lookup"><span data-stu-id="8a091-149">[Bot Framework SDK for JavaScript](https://github.com/Microsoft/botbuilder-js) and [Bot Framework SDK for .NET](https://github.com/Microsoft/botbuilder-dotnet/)</span></span>
* [<span data-ttu-id="8a091-150">Veröffentlichen Ihrer APP in einer Organisation oder AppSource</span><span class="sxs-lookup"><span data-stu-id="8a091-150">Publish your app to an organization or AppSource</span></span>](concepts/deploy-and-publish/overview.md)
