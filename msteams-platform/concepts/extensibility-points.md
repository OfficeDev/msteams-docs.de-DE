---
title: Einstiegspunkte für Microsoft Teams-Apps
author: heath-hamilton
description: Hier wird beschrieben, wo Benutzer Ihre App in Microsoft Teams finden und verwenden können.
ms.topic: conceptual
ms.author: lajanuar
ms.date: 09/22/2020
ms.openlocfilehash: 72ce2620160f854bbe458821db01e91d2d9f62cd
ms.sourcegitcommit: 098d38dd947e87e69d289b99e807bea2d95c42f9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/18/2020
ms.locfileid: "49713627"
---
# <a name="entry-points-for-teams-apps"></a><span data-ttu-id="7578c-103">Einstiegspunkte für Microsoft Teams-Apps</span><span class="sxs-lookup"><span data-stu-id="7578c-103">Entry points for Teams apps</span></span>

<span data-ttu-id="7578c-104">Die Microsoft Teams-Plattform bietet eine flexible Reihe von Einstiegspunkten, an denen Personen Ihre App finden und verwenden können.</span><span class="sxs-lookup"><span data-stu-id="7578c-104">The Teams platform provides a flexible set of entry points where people can discover and use your app.</span></span> <span data-ttu-id="7578c-105">Ihre App kann etwas so Einfachem dienen wie dem Einbetten von vorhandenem Webinhalt in eine Registerkarte, oder eine komplexe Lösung sein, mit der Benutzer in verschiedenen Kontexten interagieren.</span><span class="sxs-lookup"><span data-stu-id="7578c-105">Your app can be as simple as embedding existing web content in a tab or a multi-faceted app that users interact with across several contexts.</span></span>

<span data-ttu-id="7578c-106">Die erfolgreichsten Anwendungen fühlen sich wie systemeigene Microsoft Teams-Apps an, daher ist es wichtig, die Einstiegspunkte für Ihre App sorgfältig zu planen.</span><span class="sxs-lookup"><span data-stu-id="7578c-106">The most successful apps feel native to Teams, so it's important to carefully plan your app's entry points.</span></span>

## <a name="teams-channels-and-chats"></a><span data-ttu-id="7578c-107">Teams, Kanäle und Gruppenchats</span><span class="sxs-lookup"><span data-stu-id="7578c-107">Teams, channels, and chats</span></span>

<span data-ttu-id="7578c-108">Bei Teams, Kanälen und Chats handelt es sich um Orte für die Zusammenarbeit.</span><span class="sxs-lookup"><span data-stu-id="7578c-108">Teams, channels, and chats are collaboration spaces.</span></span> <span data-ttu-id="7578c-109">Apps in diesen Kontexten stehen allen an diesem Ort zur Verfügung, und sind in der Regel auf zusätzliche Workflows oder die Ermöglichung neuer sozialer Interaktionen ausgerichtet.</span><span class="sxs-lookup"><span data-stu-id="7578c-109">Apps in these contexts are available to everyone in that space and typically focus on additional workflows or unlocking new social interactions.</span></span>

<span data-ttu-id="7578c-110">Die App-Funktionen von Microsoft Teams werden in Kontexten für die Zusammenarbeit in der Regel folgendermaßen verwendet:</span><span class="sxs-lookup"><span data-stu-id="7578c-110">Here's how Teams app capabilities are commonly used in collaborative contexts:</span></span>

* <span data-ttu-id="7578c-111">[**Registerkarten**](~/tabs/what-are-tabs.md) bieten ein eingebettetes Web-Erlebnis im Vollbildmodus, das für das jeweilige Team bzw. den Kanal oder Gruppenchat konfiguriert ist.</span><span class="sxs-lookup"><span data-stu-id="7578c-111">[**Tabs**](~/tabs/what-are-tabs.md) provide a full-screen embedded web experience configured for the team, channel, or group chat.</span></span> <span data-ttu-id="7578c-112">Alle Mitglieder interagieren mit denselben webbasierten Inhalten, daher ist eine zustandslose Einzelseiten-App üblich.</span><span class="sxs-lookup"><span data-stu-id="7578c-112">All members interact with the same web-based content, so a stateless single page app experience is typical.</span></span>

* <span data-ttu-id="7578c-113">[**Messaging-Erweiterungen**](~/messaging-extensions/what-are-messaging-extensions.md) sind Verknüpfungen zum Einfügen externer Inhalte in eine Unterhaltung oder zum Ausführen von Aktionen für Nachrichten, ohne Microsoft Teams verlassen zu müssen.</span><span class="sxs-lookup"><span data-stu-id="7578c-113">[**Messaging extensions**](~/messaging-extensions/what-are-messaging-extensions.md) are shortcuts for inserting external content into a conversation or taking action on messages without leaving Teams.</span></span> <span data-ttu-id="7578c-114">Die Linkausweitung bietet reichhaltige Inhalte, wenn Inhalte über eine herkömmliche URL geteilt werden.</span><span class="sxs-lookup"><span data-stu-id="7578c-114">Link unfurling provides rich content when sharing content from a common URL.</span></span>

* <span data-ttu-id="7578c-115">[**Bots**](~/bots/what-are-bots.md) interagieren mit Teilnehmern der Unterhaltung über einen Chat und reagieren auf Ereignisse (wie das Hinzufügen eines neuen Mitglieds oder das Umbenennen eines Kanals).</span><span class="sxs-lookup"><span data-stu-id="7578c-115">[**Bots**](~/bots/what-are-bots.md) interact with members of the conversation through chat and responding to events (like adding a new member or renaming a channel).</span></span> <span data-ttu-id="7578c-116">Unterhaltungen mit einem Bot in diesen Kontexten sind für alle Mitglieder des Teams, Kanals oder der Gruppe sichtbar, daher sollten Bot-Unterhaltungen für alle relevant sein.</span><span class="sxs-lookup"><span data-stu-id="7578c-116">Conversations with a bot in these contexts are visible to all members of the team, channel, or group, so bot conversations should be relevant to everyone.</span></span>

* <span data-ttu-id="7578c-117">[**Webhooks und Connectors**](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md) ermöglichen einem externen Dienst das Posten von Nachrichten in einer Unterhaltung und Benutzern wiederum das Senden von Nachrichten an einen Dienst.</span><span class="sxs-lookup"><span data-stu-id="7578c-117">[**Webhooks and connectors**](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md) allow an external service to post messages into a conversation and users to send messages to a service.</span></span>

* <span data-ttu-id="7578c-118">[**Die Microsoft Graph REST-API**](https://docs.microsoft.com/graph/teams-concept-overview) zum Abrufen von Daten zu Teams, Kanälen und Gruppenchats hilft dabei, die Automatisierung und Verwaltung von Microsoft Teams-Abläufen zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="7578c-118">[**Microsoft Graph REST API**](https://docs.microsoft.com/graph/teams-concept-overview) for getting data about teams, channels, and group chats to help automate and manage Teams processes.</span></span>

## <a name="personal-apps"></a><span data-ttu-id="7578c-119">Persönliche Apps</span><span class="sxs-lookup"><span data-stu-id="7578c-119">Personal apps</span></span>

<span data-ttu-id="7578c-120">[Persönliche Apps](~/concepts/design/personal-apps.md) sind auf Interaktionen mit einem einzelnen Benutzer ausgerichtet.</span><span class="sxs-lookup"><span data-stu-id="7578c-120">[Personal apps](~/concepts/design/personal-apps.md) focus on interactions with a single user.</span></span> <span data-ttu-id="7578c-121">Die Benutzererfahrung ist in diesem Kontext für jeden Benutzer einmalig.</span><span class="sxs-lookup"><span data-stu-id="7578c-121">The experience in this context is unique to each user.</span></span>

<span data-ttu-id="7578c-122">So werden Microsoft Teams-Funktionen häufig in persönlichen Kontexten verwendet:</span><span class="sxs-lookup"><span data-stu-id="7578c-122">Here's how Teams capabilities are commonly used in personal contexts:</span></span>

* <span data-ttu-id="7578c-123">[**Bots**](~/bots/what-are-bots.md) führen persönliche Unterhaltungen mit Benutzern.</span><span class="sxs-lookup"><span data-stu-id="7578c-123">[**Bots**](~/bots/what-are-bots.md) have one-on-one conversations with a user.</span></span> <span data-ttu-id="7578c-124">Bots, die mehrstufige Unterhaltungen erfordern oder Benachrichtigungen bereitstellen, die nur für einen bestimmten Benutzer relevant sind, eignen sich am besten für persönliche Apps.</span><span class="sxs-lookup"><span data-stu-id="7578c-124">Bots that require multi-turn conversations or provide notifications relevant only to a specific user are best suited in personal apps.</span></span>

* <span data-ttu-id="7578c-125">[**Registerkarten**](~/tabs/what-are-tabs.md) bieten eine eingebettete Weberfahrung im Vollbildmodus, die für den Benutzer, der sie betrachtet, sinnvoll ist.</span><span class="sxs-lookup"><span data-stu-id="7578c-125">[**Tabs**](~/tabs/what-are-tabs.md) provide a full-screen embedded web experience that's meaningful to the user looking at it.</span></span>

## <a name="examples"></a><span data-ttu-id="7578c-126">Beispiele</span><span class="sxs-lookup"><span data-stu-id="7578c-126">Examples</span></span>

<span data-ttu-id="7578c-127">Die Designrichtlinien für Microsoft Teams-Apps enthalten detaillierte visuelle Darstellungen, die zeigen, wo Benutzer Microsoft Teams-Apps finden und verwenden können.</span><span class="sxs-lookup"><span data-stu-id="7578c-127">The Teams app design guidelines provide detailed visuals showing you where people can find and use Teams apps.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7578c-128">Designrichtlinien für Microsoft Teams-Apps ansehen</span><span class="sxs-lookup"><span data-stu-id="7578c-128">See the Teams app design guidelines</span></span>](../concepts/design/design-teams-app-overview.md)
