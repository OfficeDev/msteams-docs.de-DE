---
title: Einstiegspunkte für Microsoft Teams-apps
author: heath-hamilton
description: Beschreibt, wie und wo Personen Ihre APP in Microsoft Teams verwenden.
ms.topic: conceptual
ms.author: lajanuar
ms.date: 09/22/2020
ms.openlocfilehash: 1c68467177fc440993f059133f049f18785374b7
ms.sourcegitcommit: 1aa0b172931d0f81db346452788c41dc4a6717b9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/22/2020
ms.locfileid: "48209781"
---
# <a name="entry-points-for-teams-apps"></a>Einstiegspunkte für Microsoft Teams-apps

Die Teams-Plattform bietet eine flexible Reihe von Einstiegspunkten, mit denen Benutzer Ihre APP ermitteln und verwenden können. Ihre APP kann so einfach sein wie das Einbetten einer vorhandenen Website in eine persönliche Registerkarte oder eine vielschichtige APP, mit der Benutzer über mehrere Einstiegspunkte interagieren.

Die erfolgreichsten apps fühlen sich in Microsoft Teams heimisch, daher ist es wichtig, die Einstiegspunkte Ihrer APP sorgfältig zu planen.

## <a name="teams-channels-and-group-chats"></a>Teams, Kanäle und Gruppenchats

In Teams, Kanälen und Gruppenchats handelt es sich um Bereiche für die Zusammenarbeit. Apps, die diese Einstiegspunkte verwenden, stehen für alle Mitglieder zur Verfügung und konzentrieren sich in der Regel auf zusätzliche Workflows oder das Entsperren neuer Interaktionen für soziale Netzwerke.

Hier erfahren Sie, wie Microsoft Teams-App-Funktionen häufig in kollaborativen Kontexten verwendet werden:

* [**Registerkarten**](~/tabs/what-are-tabs.md) bieten eine eingebettete Weberfahrung im Vollbildmodus, die für das Team, den Kanal oder den Gruppenchat konfiguriert ist. Alle Mitglieder interagieren mit dem gleichen webbasierten Inhalt, sodass eine Status lose Einzelseiten-App-Erfahrung typisch ist.

* [**Messaging Erweiterungen**](~/messaging-extensions/what-are-messaging-extensions.md) sind Verknüpfungen zum Einfügen externer Inhalte in eine Unterhaltung oder zum Ausführen von Aktionen für Nachrichten, ohne Teams zu verlassen. Durch das Aufteilen von Hyperlinks werden umfangreiche Inhalte bereitgestellt, wenn Inhalte aus einer gemeinsamen URL freigegeben werden.

* [**Bots**](~/bots/what-are-bots.md) interagieren mit Mitgliedern der Unterhaltung durch Chat und reagieren auf Ereignisse (wie das Hinzufügen eines neuen Members oder das Umbenennen eines Kanals). Unterhaltungen mit einem bot in diesen Kontexten sind für alle Mitglieder des Teams, des Kanals oder der Gruppe sichtbar, sodass bot-Unterhaltungen für alle relevant sein sollten.

* [**Webhooks und Connectors**](~/webhooks-and-connectors/what-are-webhooks-and-connectors.md) ermöglichen einem externen Dienst das Veröffentlichen von Nachrichten in einer Unterhaltung und Benutzern zum Senden von Nachrichten an einen Dienst.

* [**Microsoft Graph-Rest-API**](https://docs.microsoft.com/graph/teams-concept-overview) zum erhalten von Daten zu Teams, Kanälen und Gruppenchats zur Unterstützung der Automatisierung und Verwaltung von Teams-Prozessen.

## <a name="personal-apps"></a>Persönliche Apps

[Persönliche apps](~/concepts/design/personal-apps.md) konzentrieren sich auf Interaktionen mit einem einzelnen Benutzer. Die Erfahrung in diesem Kontext ist für jeden Benutzer eindeutig. Benutzer können persönliche apps an der linken Navigationsleiste für einen schnellen Zugriff anheften.

Hier erfahren Sie, wie Microsoft Teams-Funktionen häufig in persönlichen Kontexten verwendet werden:

* [**Bots**](~/bots/what-are-bots.md) haben eins-zu-eins-Gespräche mit einem Benutzer. Bots, die mehrstufige Unterhaltungen erfordern oder nur für einen bestimmten Benutzer relevante Benachrichtigungen bereitstellen, eignen sich am besten für persönliche Kontexte.

* [**Registerkarten**](~/tabs/what-are-tabs.md) bieten eine eingebettete Weberfahrung im Vollbildmodus, die für einzelne Benutzer sinnvoll ist.

## <a name="ui-components"></a>Benutzeroberflächenkomponenten

Apps weisen in der Regel eine oder mehrere standardmäßige Teams-Benutzeroberflächenkomponenten auf. Das Erstellen Ihrer App mithilfe dieser Komponenten führt zu umfangreichen Erfahrungen, die für Benutzer in Microsoft Teams systemeigen sind.

### <a name="cards"></a>Karten

[Karten](~/task-modules-and-cards/what-are-cards.md) sind von JSON definierte Benutzeroberflächencontainer, die formatierten Text, Medien, Steuerelemente (wie Dropdowns und Optionsfelder) und Schaltflächen enthalten können, die eine Aktion auslösen.

Kartenaktionen können Nutzlasten zur API Ihrer App senden, einen Link öffnen, Authentifizierungsabläufe initiieren oder Nachrichten an Unterhaltungen senden. Die Teams-Plattform unterstützt mehrere Karten, darunter Adaptive Karten, Hero Cards, Thumbnail-Karten und vieles mehr. Sie können Kartensammlungen kombinieren und in einer Liste oder einem Karussell anzeigen.

### <a name="task-modules"></a>Aufgabenmodule

[Aufgaben Module](~/task-modules-and-cards/what-are-task-modules.md) bieten modale Erfahrungen in Microsoft Teams. Sie sind besonders nützlich für das Initiieren von Workflows, das Sammeln von Benutzereingaben oder das Anzeigen von umfangreichen Informationen wie Videos oder Power BI-Dashboards. In Aufgaben Modulen können Sie benutzerdefinierten Front-End-Code ausführen, ein `<iframe>` Widget anzeigen oder eine Adaptive Karte anzeigen.

Wenn Sie sich überlegen, wie Sie Ihre APP erstellen möchten, denken Sie daran, dass modals natürlich sind, damit Benutzerinformationen eingeben oder Aufgaben im Vergleich zu einer Registerkarte oder einer Unterhaltungs basierten bot-Erfahrung ausführen können.

### <a name="deep-links"></a>Deep-Links

Ihre APP kann [URL-Deep-Links](~/concepts/build-and-test/deep-links.md) erstellen, um den Benutzer über Ihre APP und den Teams-Client zu navigieren. Sie können eine Tiefe Verknüpfung für die meisten Entitäten in Microsoft Teams erstellen, und einige (wie eine neue Besprechungsanfrage) ermöglichen Ihnen, Informationen mithilfe von Abfragezeichenfolgen in der URL vorab aufzufüllen.

Beispielsweise könnte Ihr Gesprächs-bot eine Nachricht an einen Kanal mit einer tiefen Verknüpfung zu einem Aufgabenmodul senden, die dazu führt, dass eine Karte als 1:1-Nachricht an einen Benutzer gesendet wird, die wiederum einen tiefen Link zum Erstellen einer neuen Besprechung mit einem bestimmten Benutzer zu einem bestimmten Zeitpunkt enthält. Verwenden Sie Deep-Links, um Verbindungen mit den verschiedenen Erweiterungspunkten herzustellen, die für Ihre App verfügbar sind, damit sich Ihr Benutzer stets im richtigen Kontext befindet.

### <a name="web-based-content"></a>Webbasierter Inhalt

[Webbasierter Inhalt](~/tabs/how-to/create-tab-pages/content-page.md) ist eine von Ihnen gehostete Webseite, die in ein Tab-oder Aufgabenmodul eingebettet werden kann.
