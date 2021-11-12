---
title: Einstiegspunkte für Microsoft Teams-Apps
author: heath-hamilton
description: Beschreibt Einstiegspunkte für Ihre App, z. B. Team, Kanal und Chat in der persönlichen und freigegebenen App-Erfahrung.
ms.topic: conceptual
ms.localizationpriority: medium
ms.author: lajanuar
ms.openlocfilehash: 2dd2670787c3da9140b5798db3e7d28b30271f70
ms.sourcegitcommit: 781f34af2a95952bf437d0b7236ae995f4e14a08
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/12/2021
ms.locfileid: "60948418"
---
# <a name="entry-points-for-teams-apps"></a>Einstiegspunkte für Microsoft Teams-Apps

Die Teams-Plattform bietet eine flexible Gruppe von Einstiegspunkten, z. B. Team, Kanal und Chat, an denen Benutzer Ihre App entdecken und verwenden können. Ihre App kann etwas so Einfachem dienen wie dem Einbetten von vorhandenem Webinhalt in eine Registerkarte, oder eine komplexe Lösung sein, mit der Benutzer in verschiedenen Kontexten interagieren.
Die erfolgreichsten Apps sind systemeigen für Teams. Wählen Sie daher die Einstiegspunkte Ihrer App sorgfältig aus.

## <a name="shared-app-experiences"></a>Freigegebene App-Erfahrungen

Team, Kanal und Chat sind Räume für die Zusammenarbeit. Apps in diesem Kontext sind für jeden in diesem Bereich verfügbar. Zusammenarbeitsräume konzentrieren sich in der Regel auf zusätzliche Workflows oder das Entsperren neuer sozialer Interaktionen.

Die folgende Liste zeigt, wie Teams App-Funktionen häufig in Zusammenarbeitskontexten verwendet werden:

* [**Registerkarten**](~/tabs/what-are-tabs.md) bieten ein eingebettetes Web-Erlebnis im Vollbildmodus, das für das jeweilige Team bzw. den Kanal oder Gruppenchat konfiguriert ist. Alle Mitglieder interagieren mit demselben webbasierten Inhalt, sodass eine zustandslose Einzelseiten-App-Erfahrung typisch ist.

* [**Messaging-Erweiterungen**](~/messaging-extensions/what-are-messaging-extensions.md) sind Verknüpfungen zum Einfügen externer Inhalte in eine Unterhaltung oder zum Ausführen von Aktionen für Nachrichten, ohne Microsoft Teams verlassen zu müssen. [Die Verbreitung von Links](~/messaging-extensions/how-to/link-unfurling.md) stellt umfangreiche Inhalte bereit, wenn Inhalte über eine gemeinsame URL freigegeben werden.

* [**Bots**](~/bots/what-are-bots.md) interagieren mit Mitgliedern der Unterhaltung über chatten und auf Ereignisse reagieren, z. B. ein neues Mitglied hinzufügen oder einen Kanal umbenennen. 
   > [!NOTE]
   > Unterhaltungen mit einem Bot in diesem Kontext sind für alle Mitglieder des Teams, Kanals oder der Gruppe sichtbar, daher müssen Bot-Unterhaltungen für alle relevant sein.

* [**Webhooks und Connectors**](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md) ermöglichen einem externen Dienst das Posten von Nachrichten in einer Unterhaltung und Benutzern wiederum das Senden von Nachrichten an einen Dienst.

* [**Die Microsoft Graph REST-API**](/graph/teams-concept-overview) zum Abrufen von Daten zu Teams, Kanälen und Gruppenchats hilft dabei, die Automatisierung und Verwaltung von Microsoft Teams-Abläufen zu vereinfachen.

## <a name="personal-app-experiences"></a>Persönliche App-Umgebungen

[Persönliche Apps](../concepts/design/personal-apps.md) sind auf Interaktionen mit einem einzelnen Benutzer ausgerichtet. Die Benutzererfahrung ist in diesem Kontext für jeden Benutzer einmalig.

Die folgende Liste zeigt, wie Teams Funktionen in persönlichen Kontexten häufig verwendet werden:

* [**Bots**](~/bots/what-are-bots.md) führen persönliche Unterhaltungen mit Benutzern. Bots, die mehrstufige Unterhaltungen erfordern oder Benachrichtigungen bereitstellen, die nur für einen bestimmten Benutzer relevant sind, eignen sich am besten für persönliche Apps.

* [**Registerkarten**](~/tabs/what-are-tabs.md) bieten eine eingebettete Weboberfläche im Vollbildmodus, die für den Benutzer von Bedeutung ist.

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Grundlegendes zu Anwendungsfällen](../concepts/design/understand-use-cases.md)

## <a name="see-also"></a>Siehe auch

* [Entwurfsrichtlinien für Teams-Apps](../concepts/design/design-teams-app-overview.md) <br>
* [Erstellen Ihrer ersten Microsoft Teams-App](../build-your-first-app/build-first-app-overview.md)