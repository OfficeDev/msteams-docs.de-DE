---
title: Erstellen von Apps für die Microsoft Teams Plattform
author: heath-hamilton
description: Erhalten Sie eine Übersicht darüber, wie Entwickler Microsoft Teams features mit benutzerdefinierten Apps erweitern können.
ms.topic: overview
localization_priority: Normal
ms.author: lajanuar
ms.date: 09/22/2020
ms.openlocfilehash: 645b8087b367dd3cc9f5efdd53c53974307ce65e
ms.sourcegitcommit: e1fe46c574cec378319814f8213209ad3063b2c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2021
ms.locfileid: "52630494"
---
# <a name="build-apps-for-microsoft-teams"></a><span data-ttu-id="c284f-103">Apps für Microsoft Teams erstellen</span><span class="sxs-lookup"><span data-stu-id="c284f-103">Build apps for Microsoft Teams</span></span>

<span data-ttu-id="c284f-104">Microsoft Teams apps bringen wichtige Informationen, allgemeine Tools und vertrauenswürdige Prozesse an die Stelle, an der Die Menschen zunehmend sammeln, lernen und arbeiten.</span><span class="sxs-lookup"><span data-stu-id="c284f-104">Microsoft Teams apps bring key information, common tools, and trusted processes to where people increasingly gather, learn, and work.</span></span>

<span data-ttu-id="c284f-105">Apps sind die Art und Weise, Teams Ihre Anforderungen erfüllen.</span><span class="sxs-lookup"><span data-stu-id="c284f-105">Apps are how you extend Teams to fit your needs.</span></span> <span data-ttu-id="c284f-106">Erstellen Sie etwas neues für Teams oder integrieren Sie eine vorhandene App.</span><span class="sxs-lookup"><span data-stu-id="c284f-106">Create something brand new for Teams or integrate an existing app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c284f-107">Beginnen Sie hier</span><span class="sxs-lookup"><span data-stu-id="c284f-107">Start here</span></span>](build-your-first-app/build-first-app-overview.md)

## <a name="what-are-teams-apps"></a><span data-ttu-id="c284f-108">Was sind Teams Apps?</span><span class="sxs-lookup"><span data-stu-id="c284f-108">What are Teams apps?</span></span>

<span data-ttu-id="c284f-109">Teams Apps sind eine Kombination von [Funktionen](concepts/capabilities-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c284f-109">Teams apps are a combination of [capabilities](concepts/capabilities-overview.md).</span></span> <span data-ttu-id="c284f-110">Einige Apps sind einfach (Benachrichtigungen senden), während andere komplex sind (Patientendatensätze verwalten).</span><span class="sxs-lookup"><span data-stu-id="c284f-110">Some apps are simple (send notifications), while others are complex (manage patient records).</span></span> <span data-ttu-id="c284f-111">Beachten Sie beim Planen Ihrer App, dass Teams ein Hub für die Zusammenarbeit ist.</span><span class="sxs-lookup"><span data-stu-id="c284f-111">When planning your app, remember that Teams is a collaboration hub.</span></span> <span data-ttu-id="c284f-112">Die besten Teams helfen, sich selbst zu ausdrücken und besser zusammen zu arbeiten.</span><span class="sxs-lookup"><span data-stu-id="c284f-112">The best Teams apps help people express themselves and work better together.</span></span>

### <a name="personal-apps"></a><span data-ttu-id="c284f-113">Persönliche Apps</span><span class="sxs-lookup"><span data-stu-id="c284f-113">Personal apps</span></span>

:::row:::
   :::column span="1":::

<span data-ttu-id="c284f-114">**Hilfe bei der Fokussierung** von Personen: Eine [persönliche App](concepts/design/personal-apps.md) ist ein dedizierter Raum oder Bot, der Benutzern hilft, sich auf ihre eigenen Aufgaben zu konzentrieren oder wichtige Aktivitäten zu sehen.</span><span class="sxs-lookup"><span data-stu-id="c284f-114">**Help people focus**: A [personal app](concepts/design/personal-apps.md) is a dedicated space or bot to help users focus on their own tasks or view activities important to them.</span></span>

   :::column-end:::

   :::column span="3":::

:::image type="content" source="assets/images/overview-personal-apps-2021.png" alt-text="Konzeptionelle Darstellung des Aussehens von persönlichen Apps im Teams Client." border="false":::

   :::column-end:::

:::row-end:::

### <a name="tabs"></a><span data-ttu-id="c284f-116">Registerkarten</span><span class="sxs-lookup"><span data-stu-id="c284f-116">Tabs</span></span>

:::row:::
   :::column span="1":::

<span data-ttu-id="c284f-117">**Einfacher zusammenarbeiten:** Zeigen Sie Ihre webbasierten Inhalte auf einer [Registerkarte an,](tabs/what-are-tabs.md) auf der Die Benutzer diese gemeinsam besprechen und bearbeiten können.</span><span class="sxs-lookup"><span data-stu-id="c284f-117">**Collaborate more conveniently**: Display your web-based content in a [tab](tabs/what-are-tabs.md) where people can discuss and work on it together.</span></span>

   :::column-end:::

   :::column span="3":::

:::image type="content" source="assets/images/overview-channel-chat-apps-2021.png" alt-text="Konzeptionelle Darstellung des Aussehens von Registerkarten im Teams Client." border="false":::

   :::column-end:::

:::row-end:::

### <a name="bots"></a><span data-ttu-id="c284f-119">Bots</span><span class="sxs-lookup"><span data-stu-id="c284f-119">Bots</span></span>

:::row:::
   :::column span="1":::

<span data-ttu-id="c284f-120">**Wörter in Aktionen verwandeln:** Unterhaltungen führen häufig dazu, dass sie etwas tun müssen (Eine Bestellung generieren, meinen Code überprüfen, ticketstatus überprüfen und so weiter).</span><span class="sxs-lookup"><span data-stu-id="c284f-120">**Turn words into actions**: Conversations often result in the need to do something (generate an order, review my code, check ticket status, and so on).</span></span> <span data-ttu-id="c284f-121">Ein [Bot](bots/what-are-bots.md) kann diese Arten von Workflows direkt innerhalb der Teams.</span><span class="sxs-lookup"><span data-stu-id="c284f-121">A [bot](bots/what-are-bots.md) can kick off these kinds of workflows right inside Teams.</span></span>

   :::column-end:::

   :::column span="3":::

:::image type="content" source="assets/images/overview-bots-2021.png" alt-text="Konzeptionelle Darstellung des Aussehens von Bots im Teams Client." border="false":::

   :::column-end:::

:::row-end:::

### <a name="messaging-extensions"></a><span data-ttu-id="c284f-123">Messaging-Erweiterungen</span><span class="sxs-lookup"><span data-stu-id="c284f-123">Messaging extensions</span></span>

:::row:::

   :::column span="1":::

<span data-ttu-id="c284f-124">**Vereinfachen Sie multitask:** Mit [Messagingerweiterungen](messaging-extensions/what-are-messaging-extensions.md)können Sie externe Informationen in einer Unterhaltung schnell freigeben.</span><span class="sxs-lookup"><span data-stu-id="c284f-124">**Make it easier to multitask**: With [messaging extensions](messaging-extensions/what-are-messaging-extensions.md), you can quickly share external information in a conversation.</span></span> <span data-ttu-id="c284f-125">Sie können auch eine Nachricht verwenden, z. B. das Erstellen eines Hilfetickets basierend auf dem Inhalt eines Kanalbeitrags.</span><span class="sxs-lookup"><span data-stu-id="c284f-125">You also can act on a message, such as creating a help ticket based on the content of a channel post.</span></span>

   :::column-end:::

   :::column span="3":::

:::image type="content" source="assets/images/overview-messaging-extensions-2021.png" alt-text="Konzeptionelle Darstellung des Aussehens von Messagingerweiterungen im Teams Client." border="false":::

   :::column-end:::
:::row-end:::

### <a name="meeting-extensions"></a><span data-ttu-id="c284f-127">Besprechungserweiterungen</span><span class="sxs-lookup"><span data-stu-id="c284f-127">Meeting extensions</span></span>

:::row:::

   :::column span="1":::

<span data-ttu-id="c284f-128">**Erstellen von Apps für Besprechungen:** Es gibt einige Optionen zum Integrieren Ihrer App in die [Teams Anruferfahrung.](apps-in-teams-meetings/design/designing-apps-in-meetings.md)</span><span class="sxs-lookup"><span data-stu-id="c284f-128">**Create apps for meetings**: There are a few options for [incorporating your app into the Teams calling experience](apps-in-teams-meetings/design/designing-apps-in-meetings.md).</span></span>

   :::column-end:::

   :::column span="3":::

:::image type="content" source="assets/images/overview-meeting-extensions-2021.png" alt-text="Konzeptionelle Darstellung, wie Besprechungserweiterungen im Teams aussehen." border="false":::

   :::column-end:::
:::row-end:::

### <a name="webhooks-and-connectors"></a><span data-ttu-id="c284f-130">Webhooks und Connectors</span><span class="sxs-lookup"><span data-stu-id="c284f-130">Webhooks and connectors</span></span>

:::row:::

   :::column span="":::

<span data-ttu-id="c284f-131">**Kommunikation mit externen Apps:** [Eingehende Webhooks](webhooks-and-connectors/what-are-webhooks-and-connectors.md#incoming-webhooks) sind eine einfache Möglichkeit, Benachrichtigungen von einer anderen App automatisch an einen Teams senden.</span><span class="sxs-lookup"><span data-stu-id="c284f-131">**Communicate with external apps**: [Incoming webhooks](webhooks-and-connectors/what-are-webhooks-and-connectors.md#incoming-webhooks) are a simple way to automatically send notifications from another app to a Teams channel.</span></span> <span data-ttu-id="c284f-132">Mit [ausgehenden Webhooks](webhooks-and-connectors/what-are-webhooks-and-connectors.md#outgoing-webhooks)wird der Webdienst mit einem @mention.</span><span class="sxs-lookup"><span data-stu-id="c284f-132">With [outgoing webhooks](webhooks-and-connectors/what-are-webhooks-and-connectors.md#outgoing-webhooks), message your web service with an @mention.</span></span>

   :::column-end:::

   :::column span="":::

:::image type="content" source="assets/images/overview-connectors.png" alt-text="Konzeptionelle Darstellung des Aussehens von Connectors im Teams Client." border="false":::

   :::column-end:::
:::row-end:::

### <a name="microsoft-graph-for-teams"></a><span data-ttu-id="c284f-134">Microsoft Graph für Teams</span><span class="sxs-lookup"><span data-stu-id="c284f-134">Microsoft Graph for Teams</span></span>

:::row:::

   :::column span="":::

<span data-ttu-id="c284f-135">Nutzen **Teams** Daten: Die [Microsoft Graph-API für Teams](/graph/teams-concept-overview) bietet Zugriff auf Informationen zu Teams, Kanälen, Benutzern und Nachrichten, mit deren Hilfe Sie Features für Ihre App erstellen oder verbessern können (z. B. umfangreiche Benachrichtigungen).</span><span class="sxs-lookup"><span data-stu-id="c284f-135">**Utilize Teams data**: The [Microsoft Graph API for Teams](/graph/teams-concept-overview) provides access to information about teams, channels, users, and messages that can help you create or enhance features for your app (such as rich notifications).</span></span>

   :::column-end:::

   :::column span="":::

:::image type="content" source="assets/images/overview-graph.png" alt-text="Konzeptionelle Darstellung der Microsoft Graph-API für Teams." border="false":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

## <a name="start-building"></a><span data-ttu-id="c284f-137">Erstellen beginnen</span><span class="sxs-lookup"><span data-stu-id="c284f-137">Start building</span></span>

<span data-ttu-id="c284f-138">Machen Sie sich schnell mit dem Erstellen von Teams vertraut, indem Sie Ihre Umgebung einrichten und eine einfache App erstellen.</span><span class="sxs-lookup"><span data-stu-id="c284f-138">Quickly familiarize yourself with building for Teams by setting up your environment and creating a simple app.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c284f-139">Die erste App erstellen</span><span class="sxs-lookup"><span data-stu-id="c284f-139">Build your first app</span></span>](build-your-first-app/build-first-app-overview.md)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

## <a name="integrate-with-teams"></a><span data-ttu-id="c284f-140">Integration in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="c284f-140">Integrate with Teams</span></span>

<span data-ttu-id="c284f-141">Vermischen Sie die Features, die Benutzer an einer vorhandenen Web-App, einem Dienst oder system lieben, mit den features für die Zusammenarbeit Teams.</span><span class="sxs-lookup"><span data-stu-id="c284f-141">Blend the features users love about an existing web app, service, or system with the collaborative features of Teams.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c284f-142">Integrieren einer vorhandenen App</span><span class="sxs-lookup"><span data-stu-id="c284f-142">Integrate an existing app</span></span>](samples/integrating-web-apps.md)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

## <a name="a-little-code-goes-a-long-way"></a><span data-ttu-id="c284f-143">Ein wenig Code geht weit</span><span class="sxs-lookup"><span data-stu-id="c284f-143">A little code goes a long way</span></span>

<span data-ttu-id="c284f-144">Sie müssen kein erfahrener Programmierer sein, um eine großartige app Teams erstellen.</span><span class="sxs-lookup"><span data-stu-id="c284f-144">You don't need to be an expert programmer to build a great Teams app.</span></span> <span data-ttu-id="c284f-145">Testen Sie eine von mehreren Low-Code-Lösungen.</span><span class="sxs-lookup"><span data-stu-id="c284f-145">Try one of several low-code solutions.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c284f-146">Erstellen einer Low-Code-App</span><span class="sxs-lookup"><span data-stu-id="c284f-146">Create a low-code app</span></span>](samples/teams-low-code-solutions.md)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

## <a name="get-ideas-for-your-app"></a><span data-ttu-id="c284f-147">Ideen für Ihre App erhalten</span><span class="sxs-lookup"><span data-stu-id="c284f-147">Get ideas for your app</span></span>

<span data-ttu-id="c284f-148">Suchen Sie nach Inspiration für die App-Entwicklung?</span><span class="sxs-lookup"><span data-stu-id="c284f-148">Looking for app development inspiration?</span></span> <span data-ttu-id="c284f-149">Durchsuchen Sie unsere Liste mit realen Szenarien und Branchenlösungen mit Konzepten mit hoher Genauigkeit, um die verschiedenen Möglichkeiten zu verstehen, Teams Apps Ihren Benutzern helfen können.</span><span class="sxs-lookup"><span data-stu-id="c284f-149">Browse our list of real-world scenarios and industry solutions with high fidelity concept mocks to understand the various ways Teams apps can help your users.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="c284f-150">Siehe App-Szenarien</span><span class="sxs-lookup"><span data-stu-id="c284f-150">See app scenarios</span></span>](https://adoption.microsoft.com/extensibility-look-book/scenarios/)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

## <a name="see-also"></a><span data-ttu-id="c284f-151">Sehen Sie ebenfalls</span><span class="sxs-lookup"><span data-stu-id="c284f-151">See also</span></span>

* [<span data-ttu-id="c284f-152">Hinzufügen einer Share-to-Teams-Schaltfläche zu Ihrer Website</span><span class="sxs-lookup"><span data-stu-id="c284f-152">Add a Share-to-Teams button to your website</span></span>](concepts/build-and-test/share-to-teams.md)
* [<span data-ttu-id="c284f-153">Entwerfen Ihrer Teams App</span><span class="sxs-lookup"><span data-stu-id="c284f-153">Design your Teams app</span></span>](concepts/design/design-teams-app-overview.md)
* [<span data-ttu-id="c284f-154">Microsoft Teams JavaScript-Client-SDK</span><span class="sxs-lookup"><span data-stu-id="c284f-154">Microsoft Teams JavaScript client SDK</span></span>](/javascript/api/@microsoft/teams-js/?view=msteams-client-js-latest&preserve-view=true)
* <span data-ttu-id="c284f-155">Bot Framework SDK für [JavaScript](https://github.com/Microsoft/botbuilder-js) und [.NET](https://github.com/Microsoft/botbuilder-dotnet/)</span><span class="sxs-lookup"><span data-stu-id="c284f-155">Bot Framework SDK for [JavaScript](https://github.com/Microsoft/botbuilder-js) and [.NET](https://github.com/Microsoft/botbuilder-dotnet/)</span></span>
* [<span data-ttu-id="c284f-156">Verteilen Ihrer Teams App</span><span class="sxs-lookup"><span data-stu-id="c284f-156">Distribute your Teams app</span></span>](concepts/deploy-and-publish/apps-publish-overview.md)
