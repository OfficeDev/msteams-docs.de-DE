---
title: Erstellen von Apps für die Microsoft Teams-Plattform
author: heath-hamilton
description: Verschaffen Sie sich einen Überblick darüber, wie Entwickler Microsoft Teams Funktionen mit benutzerdefinierten Apps erweitern können.
ms.topic: overview
localization_priority: Normal
ms.author: lajanuar
ms.date: 09/22/2020
ms.openlocfilehash: 8724b669476b11aa8cb1aca6d9586fc7ea42587d
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566509"
---
# <a name="build-apps-for-microsoft-teams"></a>Apps für Microsoft Teams erstellen

Microsoft Teams-Apps bringen wichtige Informationen, gemeinsame Tools und vertrauenswürdige Prozesse dort, wo sich Die Menschen zunehmend sammeln, lernen und arbeiten.

Apps sind, wie Sie Teams erweitern, um Ihre Bedürfnisse zu erfüllen. Erstellen Sie etwas brandneues für Teams oder integrieren Sie eine vorhandene App.

> [!div class="nextstepaction"]
> [Beginnen Sie hier](build-your-first-app/build-first-app-overview.md)

## <a name="what-are-teams-apps"></a>Was sind Teams Apps?

Teams-Apps sind eine Kombination aus [Funktionen](concepts/capabilities-overview.md) und [Einstiegspunkten](concepts/extensibility-points.md). Beispielsweise können Personen mit dem *Bot* (Fähigkeit) Ihrer App in einem *Kanal* (Einstiegspunkt) chatten.

Einige Apps sind einfach (Benachrichtigungen senden), während andere komplex sind (Patientendatensätze verwalten). Denken Sie bei der Planung Ihrer App daran, dass Teams ein Collaboration Hub ist. Die besten Teams Apps helfen Menschen, sich auszudrücken und besser zusammenzuarbeiten.

:::row:::
   :::column span="":::

### <a name="tabs"></a>Registerkarten

**Erhalten Sie Informationen bequemer**: Manchmal müssen Sie nur die Dinge einfacher zu finden. Zeigen Sie eine wichtige Webseite in einer [Registerkarte](tabs/what-are-tabs.md)an, die ein Vollbild-Weberlebnis für statische und dynamische Inhalte in Teams bietet.

:::image type="content" source="assets/images/overview-tabs.png" alt-text="Konzeptionelle Darstellung, wie Registerkarten im Teams Client aussehen." border="false":::

   :::column-end:::

   :::column span="":::

### <a name="bots"></a>Bots

**Wörter in Aktionen umwandeln:** Unterhaltungen führen oft dazu, dass sie etwas tun müssen (Erstellen einer Bestellung, Überprüfen meines Codes, Überprüfen des Ticketstatus usw.). Ein [Bot](bots/what-are-bots.md) kann diese Art von Workflows direkt in Teams starten.

:::image type="content" source="assets/images/overview-bots.png" alt-text="Konzeptuelle Darstellung dessen, wie Bots im Teams Client aussehen." border="false":::

   :::column-end:::

:::row-end:::

:::row:::

   :::column span="":::

### <a name="messaging-extensions"></a>Messaging-Erweiterungen

**Machen Sie es einfacher Multitasking**: Mit [Messaging-Erweiterungen](messaging-extensions/what-are-messaging-extensions.md)können Sie schnell externe Informationen in einer Unterhaltung teilen. Sie können auch auf eine Nachricht reagieren, z. B. ein Hilfeticket basierend auf dem Inhalt eines Kanalbeitrags erstellen.

:::image type="content" source="assets\images\overview-messaging.png" alt-text="Konzeptionelle Darstellung, wie Messagingerweiterungen im Teams Client aussehen." border="false":::

   :::column-end:::

   :::column span="":::

### <a name="webhooks"></a>Webhooks

**Kommunizieren mit externen Apps**: [Eingehende Webhooks](webhooks-and-connectors/what-are-webhooks-and-connectors.md#incoming-webhooks) sind eine einfache Möglichkeit, Benachrichtigungen von einer anderen App automatisch an einen Teams Kanal zu senden. Mit [ausgehenden Webhooks](webhooks-and-connectors/what-are-webhooks-and-connectors.md#outgoing-webhooks), Nachricht An Ihren Webdienst mit einem @mention.

:::image type="content" source="assets/images/overview-connectors.png" alt-text="Konzeptionelle Darstellung, wie Connectors im Teams Client aussehen." border="false":::

   :::column-end:::
:::row-end:::

:::row:::

   :::column span="":::

### <a name="microsoft-graph-for-teams"></a>Microsoft Graph für Teams

**Verwenden Teams Daten:** Die [Microsoft Graph-API für Teams](/graph/teams-concept-overview) bietet Zugriff auf Informationen zu Teams, Kanälen, Benutzern und Nachrichten, mit denen Sie Funktionen für Ihre App erstellen oder verbessern können.

:::image type="content" source="assets/images/overview-graph.png" alt-text="Konzeptionelle Darstellung der Microsoft Graph-API für Teams." border="false":::

   :::column-end:::

   :::column span="":::
   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

## <a name="start-building"></a>Beginnen Sie mit dem Bau

Machen Sie sich schnell mit dem Erstellen für Teams vertraut, indem Sie Ihre Umgebung einrichten und eine einfache App erstellen.

> [!div class="nextstepaction"]
> [Die erste App erstellen](build-your-first-app/build-first-app-overview.md)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

## <a name="integrate-with-teams"></a>Integration in Microsoft Teams

Verschmelzen Sie die Funktionen, die Benutzer an einer vorhandenen Web-App, einem Dienst oder einem Vorhandenen System lieben, mit den kollaborativen Funktionen von Teams.

> [!div class="nextstepaction"]
> [Integrieren einer vorhandenen App](samples/integrating-web-apps.md)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

## <a name="a-little-code-goes-a-long-way"></a>Ein kleiner Code geht einen langen Weg

Sie müssen kein erfahrener Programmierer sein, um eine großartige Teams-App zu erstellen. Probieren Sie eine der verschiedenen Low-Code-Lösungen aus.

> [!div class="nextstepaction"]
> [Erstellen einer Low-Code-App](samples/teams-low-code-solutions.md)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

## <a name="get-ideas-for-your-app"></a>Holen Sie sich Ideen für Ihre App

Suchen Sie nach Inspiration für die App-Entwicklung? Durchsuchen Sie unsere Liste der realen Szenarien und Branchenlösungen mit High-Fidelity-Konzept-Mocks, um zu verstehen, wie Teams Apps Ihren Benutzern helfen können.

> [!div class="nextstepaction"]
> [Siehe App-Szenarien](https://adoption.microsoft.com/extensibility-look-book/scenarios/)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

## <a name="see-also"></a>Siehe auch

* [Hinzufügen einer Schaltfläche "Share-to-Teams" zu Ihrer Website](concepts/build-and-test/share-to-teams.md)
* [Entwerfen Sie Ihre Teams-App](concepts/design/design-teams-app-overview.md)
* [Microsoft Teams JavaScript-Client-SDK](/javascript/api/@microsoft/teams-js/?view=msteams-client-js-latest&preserve-view=true)
* Bot Framework SDK für [JavaScript](https://github.com/Microsoft/botbuilder-js) und [.NET](https://github.com/Microsoft/botbuilder-dotnet/)
* [Verteilen Sie Ihre Teams-App](concepts/deploy-and-publish/apps-publish-overview.md)
