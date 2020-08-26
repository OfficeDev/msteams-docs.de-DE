---
title: Entwicklerplattform für Teams
author: clearab
description: Übersicht darüber, wie Entwickler Microsoft Teams-Funktionen mithilfe der Teams-Plattform erweitern und anpassen können.
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: 4af4d34ffa4581be6e69f6233d3eb356aa6a2a08
ms.sourcegitcommit: 52732714105fac07c331cd31e370a9685f45d3e1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "46874884"
---
# <a name="building-for-microsoft-teams"></a><span data-ttu-id="8e0bb-103">Erstellen für Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="8e0bb-103">Building for Microsoft Teams</span></span>

<span data-ttu-id="8e0bb-104">Microsoft Teams-apps bringen wichtige Informationen, gemeinsame Tools und vertrauenswürdige Prozesse dazu, wo Personen zunehmend sammeln, lernen und arbeiten.</span><span class="sxs-lookup"><span data-stu-id="8e0bb-104">Microsoft Teams apps bring key information, common tools, and trusted processes to where people increasingly gather, learn, and work.</span></span>

<span data-ttu-id="8e0bb-105">Mit apps erweitern Sie Teams entsprechend Ihren Anforderungen.</span><span class="sxs-lookup"><span data-stu-id="8e0bb-105">Apps are how you extend Teams to fit your needs.</span></span> <span data-ttu-id="8e0bb-106">Sie können etwas ganz neues für Teams erstellen oder einfach Features in Ihren bevorzugten apps und Diensten integrieren.</span><span class="sxs-lookup"><span data-stu-id="8e0bb-106">You can create something brand new for Teams or simply integrate features in your favorite apps and services.</span></span>

## <a name="what-can-teams-apps-do"></a><span data-ttu-id="8e0bb-107">Was können Teams-apps tun?</span><span class="sxs-lookup"><span data-stu-id="8e0bb-107">What can Teams apps do?</span></span>

<span data-ttu-id="8e0bb-108">Personen ermitteln und verwenden Teams-Apps über eine Reihe von Platt Form [Funktionen](capabilities-overview.md).</span><span class="sxs-lookup"><span data-stu-id="8e0bb-108">People discover and use Teams apps through a set of platform [capabilities](capabilities-overview.md).</span></span>

<span data-ttu-id="8e0bb-109">Einige apps sind einfach (Benachrichtigungen senden), andere sind komplex (Patientendatensätze anzeigen).</span><span class="sxs-lookup"><span data-stu-id="8e0bb-109">Some apps are simple (send notifications), while others are complex (view patient records).</span></span> <span data-ttu-id="8e0bb-110">Beachten Sie bei der Planung Ihrer APP, dass Teams ein Hub für die Zusammenarbeit sind.</span><span class="sxs-lookup"><span data-stu-id="8e0bb-110">When planning your app, remember that Teams is a collaboration hub.</span></span> <span data-ttu-id="8e0bb-111">Die besten Teams-Apps helfen Benutzern, sich selbst auszudrücken und besser zusammenzuarbeiten.</span><span class="sxs-lookup"><span data-stu-id="8e0bb-111">The best Teams apps help people express themselves and work better together.</span></span>

### <a name="get-information-more-conveniently"></a><span data-ttu-id="8e0bb-112">Bequemeres Abrufen von Informationen</span><span class="sxs-lookup"><span data-stu-id="8e0bb-112">Get information more conveniently</span></span>

<span data-ttu-id="8e0bb-113">Manchmal müssen Sie die Dinge einfacher finden.</span><span class="sxs-lookup"><span data-stu-id="8e0bb-113">Sometimes you just need to make things easier to find.</span></span> <span data-ttu-id="8e0bb-114">Zeigt eine wichtige Webseite auf einer [Registerkarte](doc-links/what-are-tabs.md)an, die eine Vollbildansicht für statischen und dynamischen Inhalt in Microsoft Teams bietet.</span><span class="sxs-lookup"><span data-stu-id="8e0bb-114">Display an important webpage in a [tab](doc-links/what-are-tabs.md), which provides a full-screen web experience for static and dynamic content in Teams.</span></span>

![Konzeptionelle Darstellung dessen, was Registerkarten im Microsoft Teams-Client aussehen.](doc-links/images/overview-tabs.png)

### <a name="share-links-without-switching-context"></a><span data-ttu-id="8e0bb-116">Freigeben von Links ohne Kontextwechsel</span><span class="sxs-lookup"><span data-stu-id="8e0bb-116">Share links without switching context</span></span>

<span data-ttu-id="8e0bb-117">Informationen in eine Unterhaltung ziehen und Teams niemals verlassen.</span><span class="sxs-lookup"><span data-stu-id="8e0bb-117">Pull information into a conversation and never leave Teams.</span></span> <span data-ttu-id="8e0bb-118">Mit [Messaging-Erweiterungen](doc-links/what-are-messaging-extensions.md) können Sie beispielsweise umfangreiche, leicht verdauliche Inhalte aus einem externen System mithilfe des Felds zum Verfassen von Nachrichten freigeben.</span><span class="sxs-lookup"><span data-stu-id="8e0bb-118">For example, with [messaging extensions](doc-links/what-are-messaging-extensions.md) you can share rich, easily digestible content from an external system using the message compose box.</span></span>

![Konzeptionelle Darstellung, wie Messaging-Erweiterungen im Teams-Client aussehen](doc-links\images\overview-messaging.png)

### <a name="turn-words-into-actions"></a><span data-ttu-id="8e0bb-120">Umwandeln von Wörtern in Aktionen</span><span class="sxs-lookup"><span data-stu-id="8e0bb-120">Turn words into actions</span></span>

<span data-ttu-id="8e0bb-121">Unterhaltungen führen häufig dazu, dass Sie etwas tun müssen (eine Bestellung erstellen, meinen Code überprüfen usw.).</span><span class="sxs-lookup"><span data-stu-id="8e0bb-121">Conversations often result in the need to do something (create an order, review my code, etc.).</span></span> <span data-ttu-id="8e0bb-122">Ein [bot](doc-links/what-are-bots.md) kann diese Art von Workflows direkt innerhalb von Teams abstoßen.</span><span class="sxs-lookup"><span data-stu-id="8e0bb-122">A [bot](doc-links/what-are-bots.md) can kick off these kinds of workflows right inside Teams.</span></span>

![Konzeptionelle Darstellung dessen, was Bots im Microsoft Teams-Client aussieht](doc-links/images/overview-bots.png)

### <a name="communicate-with-external-apps-and-services"></a><span data-ttu-id="8e0bb-124">Kommunikation mit externen apps und Diensten</span><span class="sxs-lookup"><span data-stu-id="8e0bb-124">Communicate with external apps and services</span></span>

<span data-ttu-id="8e0bb-125">Bei [eingehenden webhooks](doc-links/what-are-webhooks-and-connectors.md#incoming-webhooks) handelt es sich um eine einfache Möglichkeit, Benachrichtigungen automatisch von einer anderen APP an einen Microsoft Teams-Kanal oder Chat zu senden.</span><span class="sxs-lookup"><span data-stu-id="8e0bb-125">[Incoming webhooks](doc-links/what-are-webhooks-and-connectors.md#incoming-webhooks) are a simple way to automatically send alerts from another app to a Teams channel or chat.</span></span> <span data-ttu-id="8e0bb-126">Mit [ausgehenden webhooks](doc-links/what-are-webhooks-and-connectors.md#outgoing-webhooks)können Sie eine Nachricht an den Webdienst mit einem @mention senden.</span><span class="sxs-lookup"><span data-stu-id="8e0bb-126">With [outgoing webhooks](doc-links/what-are-webhooks-and-connectors.md#outgoing-webhooks), you can send a message to your web service with an @mention.</span></span>

![Konzeptionelle Darstellung dessen, was Konnektoren im Teams-Client aussieht.](doc-links/images/overview-connectors.png)

### <a name="utilize-teams-data"></a><span data-ttu-id="8e0bb-128">Verwenden von Microsoft Teams-Daten</span><span class="sxs-lookup"><span data-stu-id="8e0bb-128">Utilize Teams data</span></span>

<span data-ttu-id="8e0bb-129">Die [Microsoft Graph-Rest-API für Teams](https://docs.microsoft.com/graph/teams-concept-overview) bietet Zugriff auf Informationen zu Teams, Kanälen, Benutzern und Nachrichten, die Sie beim Erstellen oder Erweitern von Features für Ihre APP unterstützen können.</span><span class="sxs-lookup"><span data-stu-id="8e0bb-129">The [Microsoft Graph REST API for Teams](https://docs.microsoft.com/graph/teams-concept-overview) provides access to information about teams, channels, users, and messages that can help you create or enhance features for your app.</span></span>

!["Konzeptionelle Darstellung der Microsoft Graph-Rest-API für Teams](doc-links/images/overview-graph.png)
  
## <a name="start-building"></a><span data-ttu-id="8e0bb-131">Erstellen beginnen</span><span class="sxs-lookup"><span data-stu-id="8e0bb-131">Start building</span></span>

   <span data-ttu-id="8e0bb-132">Machen Sie sich schnell mit der Erstellung für Microsoft Teams vertraut, indem Sie eine einfache APP erstellen und ein paar häufig verwendete Funktionen hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="8e0bb-132">Quickly familiarize yourself with building for Teams by creating a simple app and adding a couple commonly used capabilities.</span></span>

   > [!div class="nextstepaction"]
   > [<span data-ttu-id="8e0bb-133">Erstellen Sie jetzt Ihre erste app.</span><span class="sxs-lookup"><span data-stu-id="8e0bb-133">Build your first app now</span></span>](build-your-first-app/build-real-world-app.md)

### <a name="bring-it-all-together"></a><span data-ttu-id="8e0bb-134">Zusammenführen</span><span class="sxs-lookup"><span data-stu-id="8e0bb-134">Bring it all together</span></span>

   <span data-ttu-id="8e0bb-135">Vereinfachen Sie Prozesse und Workflows für Benutzer, indem Sie die bevorzugten Webanwendungen, Dienste und Systeme Ihrer Organisation mit kollaborativen Teams-Features kombinieren.</span><span class="sxs-lookup"><span data-stu-id="8e0bb-135">Simplify processes and workflows for users by blending your organization's favorite web apps, services, and systems with Teams collaborative features.</span></span>

   > [!div class="nextstepaction"]
   > [<span data-ttu-id="8e0bb-136">Integrieren einer vorhandenen APP</span><span class="sxs-lookup"><span data-stu-id="8e0bb-136">Integrate an existing app</span></span>](doc-links/integrating-web-apps.md)

### <a name="trust-the-process"></a><span data-ttu-id="8e0bb-137">Dem Prozess Vertrauen</span><span class="sxs-lookup"><span data-stu-id="8e0bb-137">Trust the process</span></span>

   <span data-ttu-id="8e0bb-138">Verstehen Sie den gesamten Entwicklungsprozess für Teams-Plattformen, um eine APP für Ihre Organisation oder andere Personen effektiv zu planen, zu entwerfen, zu erstellen und zu veröffentlichen.</span><span class="sxs-lookup"><span data-stu-id="8e0bb-138">Understand the entire Teams platform development process to effectively plan, design, build, and publish an app for your organization or anyone.</span></span>

   > [!div class="nextstepaction"]
   > [<span data-ttu-id="8e0bb-139">Starten der Planung Ihrer APP</span><span class="sxs-lookup"><span data-stu-id="8e0bb-139">Start planning your app</span></span>](doc-links/extensibility-points.md)

### <a name="no-code-no-worries"></a><span data-ttu-id="8e0bb-140">Kein Code, keine Sorge</span><span class="sxs-lookup"><span data-stu-id="8e0bb-140">No code, no worries</span></span>

   <span data-ttu-id="8e0bb-141">Sie müssen kein Programmierer sein, um eine großartige APP zu erstellen.</span><span class="sxs-lookup"><span data-stu-id="8e0bb-141">You don't need to be a programmer to build a great app.</span></span> <span data-ttu-id="8e0bb-142">Erstellen Sie eine Teams-App mit wenig bis gar keinen Code mithilfe der Microsoft Power-Plattform.</span><span class="sxs-lookup"><span data-stu-id="8e0bb-142">Create a Teams app with little to no code using the Microsoft Power Platform.</span></span>

   > [!div class="nextstepaction"]
   > [<span data-ttu-id="8e0bb-143">Importieren einer Power Platform-App</span><span class="sxs-lookup"><span data-stu-id="8e0bb-143">Import a Power Platform app</span></span>](doc-links/importing-custom-microsoft-apps.md)

## <a name="resources"></a><span data-ttu-id="8e0bb-144">Ressourcen</span><span class="sxs-lookup"><span data-stu-id="8e0bb-144">Resources</span></span>

* [<span data-ttu-id="8e0bb-145">Hinzufügen einer Freigabe zur Schaltfläche "Teams" zu Ihrer Website</span><span class="sxs-lookup"><span data-stu-id="8e0bb-145">Add a Share to Teams button to your website</span></span>](doc-links/share-to-teams.md)
* [<span data-ttu-id="8e0bb-146">Fluent-Benutzeroberflächen-Entwurfs System</span><span class="sxs-lookup"><span data-stu-id="8e0bb-146">Fluent UI Design System</span></span>](https://fluentsite.z22.web.core.windows.net/)
* [<span data-ttu-id="8e0bb-147">Microsoft Teams JavaScript-Client-SDK</span><span class="sxs-lookup"><span data-stu-id="8e0bb-147">Microsoft Teams JavaScript client SDK</span></span>](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/?view=msteams-client-js-latest)
* <span data-ttu-id="8e0bb-148">[Bot Framework SDK für JavaScript](https://github.com/Microsoft/botbuilder-js) und [bot Framework SDK für .net](https://github.com/Microsoft/botbuilder-dotnet/)</span><span class="sxs-lookup"><span data-stu-id="8e0bb-148">[Bot Framework SDK for JavaScript](https://github.com/Microsoft/botbuilder-js) and [Bot Framework SDK for .NET](https://github.com/Microsoft/botbuilder-dotnet/)</span></span>
