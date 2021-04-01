---
title: Erstellen von Apps für die Microsoft Teams-Plattform
author: heath-hamilton
description: Erhalten Sie eine Übersicht darüber, wie Entwickler Microsoft Teams-Features mit benutzerdefinierten Apps erweitern können.
ms.topic: overview
ms.author: lajanuar
ms.date: 09/22/2020
ms.openlocfilehash: e40d2b0d8b0d12e6275b97f79d103310d22f9720
ms.sourcegitcommit: 3bd2627b7a334568f61ccc606395e3d89aa521d9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/31/2021
ms.locfileid: "51475928"
---
# <a name="build-apps-for-microsoft-teams"></a><span data-ttu-id="c1356-103">Apps für Microsoft Teams erstellen</span><span class="sxs-lookup"><span data-stu-id="c1356-103">Build apps for Microsoft Teams</span></span>

<span data-ttu-id="c1356-104">Microsoft Teams-Apps bringen wichtige Informationen, allgemeine Tools und vertrauenswürdige Prozesse an die Stelle, an der Personen zunehmend sammeln, lernen und arbeiten.</span><span class="sxs-lookup"><span data-stu-id="c1356-104">Microsoft Teams apps bring key information, common tools, and trusted processes to where people increasingly gather, learn, and work.</span></span>

<span data-ttu-id="c1356-105">Apps sind die Art und Weise, wie Sie Teams an Ihre Anforderungen anpassen.</span><span class="sxs-lookup"><span data-stu-id="c1356-105">Apps are how you extend Teams to fit your needs.</span></span> <span data-ttu-id="c1356-106">Erstellen Sie etwas ganz Neues für Teams, oder integrieren Sie eine vorhandene App.</span><span class="sxs-lookup"><span data-stu-id="c1356-106">Create something brand new for Teams or integrate an existing app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c1356-107">Beginnen Sie hier</span><span class="sxs-lookup"><span data-stu-id="c1356-107">Start here</span></span>](build-your-first-app/build-first-app-overview.md)

## <a name="what-are-teams-apps"></a><span data-ttu-id="c1356-108">Was sind Teams-Apps?</span><span class="sxs-lookup"><span data-stu-id="c1356-108">What are Teams apps?</span></span>

<span data-ttu-id="c1356-109">Teams-Apps sind eine Kombination aus [Funktionen und](concepts/capabilities-overview.md) [Einstiegspunkten.](concepts/extensibility-points.md)</span><span class="sxs-lookup"><span data-stu-id="c1356-109">Teams apps are a combination of [capabilities](concepts/capabilities-overview.md) and [entry points](concepts/extensibility-points.md).</span></span> <span data-ttu-id="c1356-110">Beispielsweise können Benutzer mit dem Bot *(Funktion)* Ihrer App in einem *Kanal* (Einstiegspunkt) chatten.</span><span class="sxs-lookup"><span data-stu-id="c1356-110">For example, people can chat with your app's *bot* (capability) in a *channel* (entry point).</span></span>

<span data-ttu-id="c1356-111">Einige Apps sind einfach (Benachrichtigungen senden), während andere komplex sind (Patientendatensätze verwalten).</span><span class="sxs-lookup"><span data-stu-id="c1356-111">Some apps are simple (send notifications), while others are complex (manage patient records).</span></span> <span data-ttu-id="c1356-112">Denken Sie bei der Planung Ihrer App daran, dass Teams ein Hub für die Zusammenarbeit ist.</span><span class="sxs-lookup"><span data-stu-id="c1356-112">When planning your app, remember that Teams is a collaboration hub.</span></span> <span data-ttu-id="c1356-113">Die besten Teams-Apps helfen, sich selbst zu ausdrücken und besser zusammen zu arbeiten.</span><span class="sxs-lookup"><span data-stu-id="c1356-113">The best Teams apps help people express themselves and work better together.</span></span>

:::row:::
   :::column span="":::

### <a name="tabs"></a><span data-ttu-id="c1356-114">Registerkarten</span><span class="sxs-lookup"><span data-stu-id="c1356-114">Tabs</span></span>

<span data-ttu-id="c1356-115">**Einfachere Informationen:** Manchmal müssen Sie die Suche vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="c1356-115">**Get information more conveniently**: Sometimes you just need to make things easier to find.</span></span> <span data-ttu-id="c1356-116">Zeigen Sie eine wichtige Webseite auf einer [Registerkarte an,](tabs/what-are-tabs.md)die eine Vollbildweberfahrung für statische und dynamische Inhalte in Teams bietet.</span><span class="sxs-lookup"><span data-stu-id="c1356-116">Display an important webpage in a [tab](tabs/what-are-tabs.md), which provides a full-screen web experience for static and dynamic content in Teams.</span></span>

:::image type="content" source="assets/images/overview-tabs.png" alt-text="Konzeptionelle Darstellung, wie Registerkarten im Teams-Client aussehen." border="false":::

   :::column-end:::

   :::column span="":::

### <a name="bots"></a><span data-ttu-id="c1356-118">Bots</span><span class="sxs-lookup"><span data-stu-id="c1356-118">Bots</span></span>

<span data-ttu-id="c1356-119">**Machen Sie Wörter in Aktionen:** Unterhaltungen führen häufig zu der Notwendigkeit, etwas zu tun (Eine Bestellung generieren, meinen Code überprüfen, Ticketstatus überprüfen usw.).</span><span class="sxs-lookup"><span data-stu-id="c1356-119">**Turn words into actions**: Conversations often result in the need to do something (generate an order, review my code, check ticket status, etc.).</span></span> <span data-ttu-id="c1356-120">Ein [Bot](bots/what-are-bots.md) kann diese Arten von Workflows direkt in Teams starten.</span><span class="sxs-lookup"><span data-stu-id="c1356-120">A [bot](bots/what-are-bots.md) can kick off these kinds of workflows right inside Teams.</span></span>

:::image type="content" source="assets/images/overview-bots.png" alt-text="Konzeptionelle Darstellung, wie Bots im Teams-Client aussehen." border="false":::

   :::column-end:::

:::row-end:::

:::row:::

   :::column span="":::

### <a name="messaging-extensions"></a><span data-ttu-id="c1356-122">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="c1356-122">Messaging extensions</span></span>

<span data-ttu-id="c1356-123">**Vereinfachen Sie multitask:** Mit [Messagingerweiterungen](messaging-extensions/what-are-messaging-extensions.md)können Sie externe Informationen in einer Unterhaltung schnell freigeben.</span><span class="sxs-lookup"><span data-stu-id="c1356-123">**Make it easier to multitask**: With [messaging extensions](messaging-extensions/what-are-messaging-extensions.md), you can quickly share external information in a conversation.</span></span> <span data-ttu-id="c1356-124">Sie können auch eine Nachricht verwenden, z. B. das Erstellen eines Hilfetickets basierend auf dem Inhalt eines Kanalbeitrags.</span><span class="sxs-lookup"><span data-stu-id="c1356-124">You also can act on a message, such as creating a help ticket based on the content of a channel post.</span></span>

:::image type="content" source="assets\images\overview-messaging.png" alt-text="Konzeptionelle Darstellung, wie Messagingerweiterungen im Teams-Client aussehen." border="false":::

   :::column-end:::

   :::column span="":::

### <a name="webhooks"></a><span data-ttu-id="c1356-126">Webhooks</span><span class="sxs-lookup"><span data-stu-id="c1356-126">Webhooks</span></span>

<span data-ttu-id="c1356-127">**Kommunikation mit externen Apps:** [Eingehende Webhooks](webhooks-and-connectors/what-are-webhooks-and-connectors.md#incoming-webhooks) sind eine einfache Möglichkeit, Benachrichtigungen von einer anderen App automatisch an einen Teams-Kanal zu senden.</span><span class="sxs-lookup"><span data-stu-id="c1356-127">**Communicate with external apps**: [Incoming webhooks](webhooks-and-connectors/what-are-webhooks-and-connectors.md#incoming-webhooks) are a simple way to automatically send notifications from another app to a Teams channel.</span></span> <span data-ttu-id="c1356-128">Mit [ausgehenden Webhooks](webhooks-and-connectors/what-are-webhooks-and-connectors.md#outgoing-webhooks)wird der Webdienst mit einem @mention.</span><span class="sxs-lookup"><span data-stu-id="c1356-128">With [outgoing webhooks](webhooks-and-connectors/what-are-webhooks-and-connectors.md#outgoing-webhooks), message your web service with an @mention.</span></span>

:::image type="content" source="assets/images/overview-connectors.png" alt-text="Konzeptionelle Darstellung, wie Connectors im Teams-Client aussehen." border="false":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
   :::column-end:::
:::row-end:::

### <a name="microsoft-graph-for-teams"></a><span data-ttu-id="c1356-130">Microsoft Graph für Teams</span><span class="sxs-lookup"><span data-stu-id="c1356-130">Microsoft Graph for Teams</span></span>

<span data-ttu-id="c1356-131">**Nutzen von Teams-Daten:** Die [Microsoft Graph-API für Teams](https://docs.microsoft.com/graph/teams-concept-overview) bietet Zugriff auf Informationen zu Teams, Kanälen, Benutzern und Nachrichten, mit deren Hilfe Sie Features für Ihre App erstellen oder verbessern können.</span><span class="sxs-lookup"><span data-stu-id="c1356-131">**Utilize Teams data**: The [Microsoft Graph API for Teams](https://docs.microsoft.com/graph/teams-concept-overview) provides access to information about teams, channels, users, and messages that can help you create or enhance features for your app.</span></span>

:::image type="content" source="assets/images/overview-graph.png" alt-text="Konzeptionelle Darstellung der Microsoft Graph-API für Teams." border="false":::

   :::column-end:::
   :::column span="":::

:::row:::
   :::column span="2":::
   :::column-end:::
:::row-end:::

## <a name="build-solutions-for-microsoft-teams-apps"></a><span data-ttu-id="c1356-133">Erstellen von Lösungen für Microsoft Teams-Apps</span><span class="sxs-lookup"><span data-stu-id="c1356-133">Build solutions for Microsoft Teams apps</span></span>
 
<span data-ttu-id="c1356-134">Microsoft bietet ein Erweiterbarkeits-Look-Buch, eine Szenariobibliothek für Teams-Apps, die nach Branche organisiert sind.</span><span class="sxs-lookup"><span data-stu-id="c1356-134">Microsoft offers an extensibility look book, a scenario library for Teams apps organized by industry.</span></span> <span data-ttu-id="c1356-135">Dieses Buch hilft Ihnen, Apps auf der Teams-Plattform zu erstellen und verschiedene mögliche Szenarien mit verschiedenen Funktionen der Teams-Plattform zu verstehen.</span><span class="sxs-lookup"><span data-stu-id="c1356-135">This book helps you build apps on the Teams platform and understand different possible scenarios using various Teams platform capabilities.</span></span> <span data-ttu-id="c1356-136">Die Look Book-Szenarien beginnen mit einem Geschäftsproblem, den beteiligten Personen und ihren Herausforderungen und enden mit einer Teams-App-Lösung, die die Geschäftlichen Anforderungen erfüllt.</span><span class="sxs-lookup"><span data-stu-id="c1356-136">The look book scenarios start with a business problem, the personas involved along with their challenges, and end with a Teams app solution addressing the business needs.</span></span>

<span data-ttu-id="c1356-137">Jedes Szenario in dieser Bibliothek wird von einer Reihe von Designkonzepten mit hoher Genauigkeit begleitet, die als Inspiration für das Entwerfen Ihrer Apps und die Verbesserung der Benutzerfreundlichkeit dienen können.</span><span class="sxs-lookup"><span data-stu-id="c1356-137">Each scenario in this library is accompanied by a set of high-fidelity design concept mocks, which can serve as an inspiration for designing your apps and enhancing user experience.</span></span> <span data-ttu-id="c1356-138">Darüber hinaus werden im Look Book die bewährten Methoden für Design und Architektur hervorgehoben, die beim Erstellen der einzelnen Apps befolgt werden.</span><span class="sxs-lookup"><span data-stu-id="c1356-138">In addition, the look book highlights the design and architecture best practices followed in building each app.</span></span> <span data-ttu-id="c1356-139">Weitere Informationen finden Sie im Erweiterungs-Look-Buch.</span><span class="sxs-lookup"><span data-stu-id="c1356-139">For more information, see the extensibility look book.</span></span> <span data-ttu-id="c1356-140">Weitere Informationen finden Sie unter [Extensibility Look Book](https://adoption.microsoft.com/extensibility-look-book/scenarios/).</span><span class="sxs-lookup"><span data-stu-id="c1356-140">For more information, see [extensibility look book](https://adoption.microsoft.com/extensibility-look-book/scenarios/).</span></span> 

## <a name="start-building"></a><span data-ttu-id="c1356-141">Erstellen beginnen</span><span class="sxs-lookup"><span data-stu-id="c1356-141">Start building</span></span>

<span data-ttu-id="c1356-142">Machen Sie sich schnell mit dem Erstellen von Teams vertraut, indem Sie eine einfache App erstellen und einige häufig verwendete Funktionen hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="c1356-142">Quickly familiarize yourself with building for Teams by creating a simple app and adding some commonly used capabilities.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c1356-143">Erstellen Ihrer ersten App jetzt</span><span class="sxs-lookup"><span data-stu-id="c1356-143">Build your first app now</span></span>](build-your-first-app/build-first-app-overview.md)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

## <a name="integrate-with-teams"></a><span data-ttu-id="c1356-144">Integration in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="c1356-144">Integrate with Teams</span></span>

<span data-ttu-id="c1356-145">Vermischen Sie die Features, die Benutzer an einer vorhandenen Web-App, einem Dienst oder system lieben, mit den gemeinsamen Features von Teams.</span><span class="sxs-lookup"><span data-stu-id="c1356-145">Blend the features users love about an existing web app, service, or system with the collaborative features of Teams.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c1356-146">Integrieren einer vorhandenen App</span><span class="sxs-lookup"><span data-stu-id="c1356-146">Integrate an existing app</span></span>](samples/integrating-web-apps.md)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

## <a name="a-little-code-goes-a-long-way"></a><span data-ttu-id="c1356-147">Ein wenig Code geht weit</span><span class="sxs-lookup"><span data-stu-id="c1356-147">A little code goes a long way</span></span>

<span data-ttu-id="c1356-148">Sie müssen kein erfahrener Programmierer sein, um eine großartige Teams-App zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="c1356-148">You don't need to be an expert programmer to build a great Teams app.</span></span> <span data-ttu-id="c1356-149">Testen Sie eine von mehreren Low-Code-Lösungen.</span><span class="sxs-lookup"><span data-stu-id="c1356-149">Try one of several low-code solutions.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c1356-150">Erstellen einer Low-Code-App</span><span class="sxs-lookup"><span data-stu-id="c1356-150">Create a low-code app</span></span>](samples/teams-low-code-solutions.md)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

## <a name="resources"></a><span data-ttu-id="c1356-151">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="c1356-151">Resources</span></span>

* [<span data-ttu-id="c1356-152">Hinzufügen einer Share-to-Teams-Schaltfläche zu Ihrer Website</span><span class="sxs-lookup"><span data-stu-id="c1356-152">Add a Share-to-Teams button to your website</span></span>](concepts/build-and-test/share-to-teams.md)
* [<span data-ttu-id="c1356-153">Entwerfen Ihrer Teams-App</span><span class="sxs-lookup"><span data-stu-id="c1356-153">Design your Teams app</span></span>](concepts/design/design-teams-app-overview.md)
* [<span data-ttu-id="c1356-154">Microsoft Teams JavaScript client SDK</span><span class="sxs-lookup"><span data-stu-id="c1356-154">Microsoft Teams JavaScript client SDK</span></span>](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/?view=msteams-client-js-latest&preserve-view=true)
* <span data-ttu-id="c1356-155">Bot Framework SDK für [JavaScript](https://github.com/Microsoft/botbuilder-js) und [.NET](https://github.com/Microsoft/botbuilder-dotnet/)</span><span class="sxs-lookup"><span data-stu-id="c1356-155">Bot Framework SDK for [JavaScript](https://github.com/Microsoft/botbuilder-js) and [.NET](https://github.com/Microsoft/botbuilder-dotnet/)</span></span>
* [<span data-ttu-id="c1356-156">Veröffentlichen Ihrer Teams-App</span><span class="sxs-lookup"><span data-stu-id="c1356-156">Publish your Teams app</span></span>](concepts/deploy-and-publish/overview.md)
