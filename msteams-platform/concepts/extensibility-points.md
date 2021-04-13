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
# <a name="entry-points-for-teams-apps"></a>Einstiegspunkte für Microsoft Teams-Apps

Die Microsoft Teams-Plattform bietet eine flexible Reihe von Einstiegspunkten, an denen Personen Ihre App finden und verwenden können. Ihre App kann etwas so Einfachem dienen wie dem Einbetten von vorhandenem Webinhalt in eine Registerkarte, oder eine komplexe Lösung sein, mit der Benutzer in verschiedenen Kontexten interagieren.

Die erfolgreichsten Anwendungen fühlen sich wie systemeigene Microsoft Teams-Apps an, daher ist es wichtig, die Einstiegspunkte für Ihre App sorgfältig zu planen.

## <a name="teams-channels-and-chats"></a>Teams, Kanäle und Gruppenchats

Bei Teams, Kanälen und Chats handelt es sich um Orte für die Zusammenarbeit. Apps in diesen Kontexten stehen allen an diesem Ort zur Verfügung, und sind in der Regel auf zusätzliche Workflows oder die Ermöglichung neuer sozialer Interaktionen ausgerichtet.

Die App-Funktionen von Microsoft Teams werden in Kontexten für die Zusammenarbeit in der Regel folgendermaßen verwendet:

* [**Registerkarten**](~/tabs/what-are-tabs.md) bieten ein eingebettetes Web-Erlebnis im Vollbildmodus, das für das jeweilige Team bzw. den Kanal oder Gruppenchat konfiguriert ist. Alle Mitglieder interagieren mit denselben webbasierten Inhalten, daher ist eine zustandslose Einzelseiten-App üblich.

* [**Messaging-Erweiterungen**](~/messaging-extensions/what-are-messaging-extensions.md) sind Verknüpfungen zum Einfügen externer Inhalte in eine Unterhaltung oder zum Ausführen von Aktionen für Nachrichten, ohne Microsoft Teams verlassen zu müssen. Die Linkausweitung bietet reichhaltige Inhalte, wenn Inhalte über eine herkömmliche URL geteilt werden.

* [**Bots**](~/bots/what-are-bots.md) interagieren mit Teilnehmern der Unterhaltung über einen Chat und reagieren auf Ereignisse (wie das Hinzufügen eines neuen Mitglieds oder das Umbenennen eines Kanals). Unterhaltungen mit einem Bot in diesen Kontexten sind für alle Mitglieder des Teams, Kanals oder der Gruppe sichtbar, daher sollten Bot-Unterhaltungen für alle relevant sein.

* [**Webhooks und Connectors**](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md) ermöglichen einem externen Dienst das Posten von Nachrichten in einer Unterhaltung und Benutzern wiederum das Senden von Nachrichten an einen Dienst.

* [**Die Microsoft Graph REST-API**](https://docs.microsoft.com/graph/teams-concept-overview) zum Abrufen von Daten zu Teams, Kanälen und Gruppenchats hilft dabei, die Automatisierung und Verwaltung von Microsoft Teams-Abläufen zu vereinfachen.

## <a name="personal-apps"></a>Persönliche Apps

[Persönliche Apps](~/concepts/design/personal-apps.md) sind auf Interaktionen mit einem einzelnen Benutzer ausgerichtet. Die Benutzererfahrung ist in diesem Kontext für jeden Benutzer einmalig.

So werden Microsoft Teams-Funktionen häufig in persönlichen Kontexten verwendet:

* [**Bots**](~/bots/what-are-bots.md) führen persönliche Unterhaltungen mit Benutzern. Bots, die mehrstufige Unterhaltungen erfordern oder Benachrichtigungen bereitstellen, die nur für einen bestimmten Benutzer relevant sind, eignen sich am besten für persönliche Apps.

* [**Registerkarten**](~/tabs/what-are-tabs.md) bieten eine eingebettete Weberfahrung im Vollbildmodus, die für den Benutzer, der sie betrachtet, sinnvoll ist.

## <a name="examples"></a>Beispiele

Die Designrichtlinien für Microsoft Teams-Apps enthalten detaillierte visuelle Darstellungen, die zeigen, wo Benutzer Microsoft Teams-Apps finden und verwenden können.

> [!div class="nextstepaction"]
> [Designrichtlinien für Microsoft Teams-Apps ansehen](../concepts/design/design-teams-app-overview.md)
