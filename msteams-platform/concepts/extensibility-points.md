---
title: Einstiegspunkte für Microsoft Teams-Apps
author: heath-hamilton
description: Hier wird beschrieben, wo Benutzer Ihre App in Microsoft Teams finden und verwenden können.
ms.topic: conceptual
localization_priority: Normal
ms.author: lajanuar
ms.openlocfilehash: f2bdb35c76bdb7487e66a0e6b9ad01c6da9e04f8
ms.sourcegitcommit: a732789190f59ec1f3699e8ad2f06387e8fe1458
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2021
ms.locfileid: "52058320"
---
# <a name="entry-points-for-teams-apps"></a><span data-ttu-id="da99d-103">Einstiegspunkte für Microsoft Teams-Apps</span><span class="sxs-lookup"><span data-stu-id="da99d-103">Entry points for Teams apps</span></span>

<span data-ttu-id="da99d-104">Die Teams-Plattform bietet eine flexible Reihe von Einstiegspunkten, z. B. Team, Kanal und Chat, in denen Benutzer Ihre App entdecken und verwenden können.</span><span class="sxs-lookup"><span data-stu-id="da99d-104">The Teams platform provides a flexible set of entry points, such as team, channel, and chat where people can discover and use your app.</span></span> <span data-ttu-id="da99d-105">Ihre App kann etwas so Einfachem dienen wie dem Einbetten von vorhandenem Webinhalt in eine Registerkarte, oder eine komplexe Lösung sein, mit der Benutzer in verschiedenen Kontexten interagieren.</span><span class="sxs-lookup"><span data-stu-id="da99d-105">Your app can be as simple as embedding existing web content in a tab or a multi-faceted app that users interact with across several contexts.</span></span>
<span data-ttu-id="da99d-106">Die erfolgreichsten Apps sind in Teams nativ, wählen Sie daher die Einstiegspunkte Ihrer App sorgfältig aus.</span><span class="sxs-lookup"><span data-stu-id="da99d-106">The most successful apps are native to Teams, so choose your app's entry points carefully.</span></span>

## <a name="shared-app-experiences"></a><span data-ttu-id="da99d-107">Freigegebene App-Erfahrungen</span><span class="sxs-lookup"><span data-stu-id="da99d-107">Shared app experiences</span></span>

<span data-ttu-id="da99d-108">Team, Kanal und Chat sind Räume für die Zusammenarbeit.</span><span class="sxs-lookup"><span data-stu-id="da99d-108">Team, channel, and chat are collaboration spaces.</span></span> <span data-ttu-id="da99d-109">Apps in diesen Kontexten stehen allen in diesem Bereich zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="da99d-109">Apps in these contexts are available to everyone in that space.</span></span> <span data-ttu-id="da99d-110">Bereiche für die Zusammenarbeit konzentrieren sich in der Regel auf zusätzliche Workflows oder das Entsperren neuer Interaktionen mit sozialen Netzwerken.</span><span class="sxs-lookup"><span data-stu-id="da99d-110">Collaboration spaces typically focus on additional workflows or unlocking new social interactions.</span></span>

<span data-ttu-id="da99d-111">Die folgende Liste zeigt, wie Funktionen von Teams-Apps häufig in kontextbezogenen Kontexten verwendet werden:</span><span class="sxs-lookup"><span data-stu-id="da99d-111">The following list shows how Teams app capabilities are commonly used in collaborative contexts:</span></span>

* <span data-ttu-id="da99d-112">[**Registerkarten**](~/tabs/what-are-tabs.md) bieten ein eingebettetes Web-Erlebnis im Vollbildmodus, das für das jeweilige Team bzw. den Kanal oder Gruppenchat konfiguriert ist.</span><span class="sxs-lookup"><span data-stu-id="da99d-112">[**Tabs**](~/tabs/what-are-tabs.md) provide a full-screen embedded web experience configured for the team, channel, or group chat.</span></span> <span data-ttu-id="da99d-113">Alle Mitglieder interagieren mit demselben webbasierten Inhalt, daher ist eine zustandslose Einseiten-App typisch.</span><span class="sxs-lookup"><span data-stu-id="da99d-113">All members interact with the same web-based content, so a stateless single-page app experience is typical.</span></span>

* <span data-ttu-id="da99d-114">[**Messaging-Erweiterungen**](~/messaging-extensions/what-are-messaging-extensions.md) sind Verknüpfungen zum Einfügen externer Inhalte in eine Unterhaltung oder zum Ausführen von Aktionen für Nachrichten, ohne Microsoft Teams verlassen zu müssen.</span><span class="sxs-lookup"><span data-stu-id="da99d-114">[**Messaging extensions**](~/messaging-extensions/what-are-messaging-extensions.md) are shortcuts for inserting external content into a conversation or taking action on messages without leaving Teams.</span></span> <span data-ttu-id="da99d-115">[Die Verknüpfungsentfurling](~/messaging-extensions/how-to/link-unfurling.md) bietet umfangreiche Inhalte beim Freigeben von Inhalten von einer gemeinsamen URL.</span><span class="sxs-lookup"><span data-stu-id="da99d-115">[Link unfurling](~/messaging-extensions/how-to/link-unfurling.md) provides rich content when sharing content from a common URL.</span></span>

* <span data-ttu-id="da99d-116">[**Bots**](~/bots/what-are-bots.md) interagieren über Chat mit Mitgliedern der Unterhaltung und reagieren auf Ereignisse, z. B. das Hinzufügen eines neuen Mitglieds oder das Umbenennen eines Kanals.</span><span class="sxs-lookup"><span data-stu-id="da99d-116">[**Bots**](~/bots/what-are-bots.md) interact with members of the conversation through chat and responding to events, such as adding a new member or renaming a channel.</span></span> 
   > [!NOTE]
   > <span data-ttu-id="da99d-117">Unterhaltungen mit einem Bot in diesen Kontexten sind für alle Mitglieder des Teams, Kanals oder der Gruppe sichtbar, sodass Botunterhaltungen für alle relevant sein müssen.</span><span class="sxs-lookup"><span data-stu-id="da99d-117">Conversations with a bot in these contexts are visible to all members of the team, channel, or group, so bot conversations must be relevant to everyone.</span></span>

* <span data-ttu-id="da99d-118">[**Webhooks und Connectors**](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md) ermöglichen einem externen Dienst das Posten von Nachrichten in einer Unterhaltung und Benutzern wiederum das Senden von Nachrichten an einen Dienst.</span><span class="sxs-lookup"><span data-stu-id="da99d-118">[**Webhooks and connectors**](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md) allow an external service to post messages into a conversation and users to send messages to a service.</span></span>

* <span data-ttu-id="da99d-119">[**Die Microsoft Graph REST-API**](https://docs.microsoft.com/graph/teams-concept-overview) zum Abrufen von Daten zu Teams, Kanälen und Gruppenchats hilft dabei, die Automatisierung und Verwaltung von Microsoft Teams-Abläufen zu vereinfachen.</span><span class="sxs-lookup"><span data-stu-id="da99d-119">[**Microsoft Graph REST API**](https://docs.microsoft.com/graph/teams-concept-overview) for getting data about teams, channels, and group chats to help automate and manage Teams processes.</span></span>

## <a name="personal-app-experiences"></a><span data-ttu-id="da99d-120">Persönliche App-Erfahrungen</span><span class="sxs-lookup"><span data-stu-id="da99d-120">Personal app experiences</span></span>

<span data-ttu-id="da99d-121">[Persönliche Apps](../concepts/design/personal-apps.md) sind auf Interaktionen mit einem einzelnen Benutzer ausgerichtet.</span><span class="sxs-lookup"><span data-stu-id="da99d-121">[Personal apps](../concepts/design/personal-apps.md) focus on interactions with a single user.</span></span> <span data-ttu-id="da99d-122">Die Benutzererfahrung ist in diesem Kontext für jeden Benutzer einmalig.</span><span class="sxs-lookup"><span data-stu-id="da99d-122">The experience in this context is unique to each user.</span></span>

<span data-ttu-id="da99d-123">Die folgende Liste zeigt, wie Teams-Funktionen häufig in persönlichen Kontexten verwendet werden:</span><span class="sxs-lookup"><span data-stu-id="da99d-123">The following list shows how Teams capabilities are commonly used in personal contexts:</span></span>

* <span data-ttu-id="da99d-124">[**Bots**](~/bots/what-are-bots.md) führen persönliche Unterhaltungen mit Benutzern.</span><span class="sxs-lookup"><span data-stu-id="da99d-124">[**Bots**](~/bots/what-are-bots.md) have one-on-one conversations with a user.</span></span> <span data-ttu-id="da99d-125">Bots, die mehrstufige Unterhaltungen erfordern oder Benachrichtigungen bereitstellen, die nur für einen bestimmten Benutzer relevant sind, eignen sich am besten für persönliche Apps.</span><span class="sxs-lookup"><span data-stu-id="da99d-125">Bots that require multi-turn conversations or provide notifications relevant only to a specific user are best suited in personal apps.</span></span>

* <span data-ttu-id="da99d-126">[**Registerkarten**](~/tabs/what-are-tabs.md) bieten eine eingebettete Weberfahrung im Vollbildmodus, die für den Benutzer, der sie betrachtet, von Bedeutung ist.</span><span class="sxs-lookup"><span data-stu-id="da99d-126">[**Tabs**](~/tabs/what-are-tabs.md) provide a full-screen embedded web experience that is meaningful to the user looking at it.</span></span>

## <a name="see-also"></a><span data-ttu-id="da99d-127">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="da99d-127">See also</span></span>

- [<span data-ttu-id="da99d-128">Richtlinien zum Entwerfen von Teams-Apps</span><span class="sxs-lookup"><span data-stu-id="da99d-128">Teams app design guidelines</span></span>](../concepts/design/design-teams-app-overview.md)

## <a name="next-step"></a><span data-ttu-id="da99d-129">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="da99d-129">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="da99d-130">Verstehen von Verwendungsfällen</span><span class="sxs-lookup"><span data-stu-id="da99d-130">Understand use cases</span></span>](../concepts/design/understand-use-cases.md)
