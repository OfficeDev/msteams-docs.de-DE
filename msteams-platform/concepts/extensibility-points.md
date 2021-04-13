---
title: Einstiegspunkte für Microsoft Teams-Apps
author: heath-hamilton
description: Hier wird beschrieben, wo Benutzer Ihre App in Microsoft Teams finden und verwenden können.
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: f61e5b5c05855c0a3a766920095cf46f699f08a6
ms.sourcegitcommit: 9404c2e3a30887b9e17e0c89b12dd26fd9b8033e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/09/2021
ms.locfileid: "51654356"
---
# <a name="entry-points-for-teams-apps"></a>Einstiegspunkte für Microsoft Teams-Apps

Die Teams-Plattform bietet eine flexible Reihe von Einstiegspunkten, z. B. Team, Kanal und Chat, in denen Benutzer Ihre App entdecken und verwenden können. Ihre App kann etwas so Einfachem dienen wie dem Einbetten von vorhandenem Webinhalt in eine Registerkarte, oder eine komplexe Lösung sein, mit der Benutzer in verschiedenen Kontexten interagieren.
Die erfolgreichsten Apps sind in Teams nativ, wählen Sie daher die Einstiegspunkte Ihrer App sorgfältig aus.

## <a name="shared-app-experiences"></a>Freigegebene App-Erfahrungen

Team, Kanal und Chat sind Räume für die Zusammenarbeit. Apps in diesen Kontexten stehen allen in diesem Bereich zur Verfügung. Bereiche für die Zusammenarbeit konzentrieren sich in der Regel auf zusätzliche Workflows oder das Entsperren neuer Interaktionen mit sozialen Netzwerken.

Die folgende Liste zeigt, wie Funktionen von Teams-Apps häufig in kontextbezogenen Kontexten verwendet werden:

* [**Registerkarten**](~/tabs/what-are-tabs.md) bieten ein eingebettetes Web-Erlebnis im Vollbildmodus, das für das jeweilige Team bzw. den Kanal oder Gruppenchat konfiguriert ist. Alle Mitglieder interagieren mit demselben webbasierten Inhalt, daher ist eine zustandslose Einseiten-App typisch.

* [**Messaging-Erweiterungen**](~/messaging-extensions/what-are-messaging-extensions.md) sind Verknüpfungen zum Einfügen externer Inhalte in eine Unterhaltung oder zum Ausführen von Aktionen für Nachrichten, ohne Microsoft Teams verlassen zu müssen. [Die Verknüpfungsentfurling](~/messaging-extensions/how-to/link-unfurling.md) bietet umfangreiche Inhalte beim Freigeben von Inhalten von einer gemeinsamen URL.

* [**Bots**](~/bots/what-are-bots.md) interagieren über Chat mit Mitgliedern der Unterhaltung und reagieren auf Ereignisse, z. B. das Hinzufügen eines neuen Mitglieds oder das Umbenennen eines Kanals. 
   > [!NOTE]
   > Unterhaltungen mit einem Bot in diesen Kontexten sind für alle Mitglieder des Teams, Kanals oder der Gruppe sichtbar, sodass Botunterhaltungen für alle relevant sein müssen.

* [**Webhooks und Connectors**](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md) ermöglichen einem externen Dienst das Posten von Nachrichten in einer Unterhaltung und Benutzern wiederum das Senden von Nachrichten an einen Dienst.

* [**Die Microsoft Graph REST-API**](https://docs.microsoft.com/graph/teams-concept-overview) zum Abrufen von Daten zu Teams, Kanälen und Gruppenchats hilft dabei, die Automatisierung und Verwaltung von Microsoft Teams-Abläufen zu vereinfachen.

## <a name="personal-app-experiences"></a>Persönliche App-Erfahrungen

[Persönliche Apps](../concepts/design/personal-apps.md) sind auf Interaktionen mit einem einzelnen Benutzer ausgerichtet. Die Benutzererfahrung ist in diesem Kontext für jeden Benutzer einmalig.

Die folgende Liste zeigt, wie Teams-Funktionen häufig in persönlichen Kontexten verwendet werden:

* [**Bots**](~/bots/what-are-bots.md) führen persönliche Unterhaltungen mit Benutzern. Bots, die mehrstufige Unterhaltungen erfordern oder Benachrichtigungen bereitstellen, die nur für einen bestimmten Benutzer relevant sind, eignen sich am besten für persönliche Apps.

* [**Registerkarten**](~/tabs/what-are-tabs.md) bieten eine eingebettete Weberfahrung im Vollbildmodus, die für den Benutzer, der sie betrachtet, von Bedeutung ist.

## <a name="see-also"></a>Siehe auch

> [!div class="nextstepaction"]
> [Richtlinien zum Entwerfen von Teams-Apps](../concepts/design/design-teams-app-overview.md)

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Verstehen von Verwendungsfällen](../concepts/design/understand-use-cases.md)
