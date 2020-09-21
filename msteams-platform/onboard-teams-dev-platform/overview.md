---
title: Microsoft Teams-Entwicklerplattform
author: clearab
description: Übersicht darüber, wie Entwickler Microsoft Teams-Funktionen mithilfe der Teams-Plattform erweitern und anpassen können.
ms.topic: overview
ms.author: anclear
ms.openlocfilehash: 73cbd4f68d8878872147bd412972495de1b5de6e
ms.sourcegitcommit: d3bb4bbcdff9545c9869647dcdbe563a2db868be
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/18/2020
ms.locfileid: "47964571"
---
# <a name="building-for-microsoft-teams"></a>Erstellen für Microsoft Teams

Microsoft Teams-apps bringen wichtige Informationen, gemeinsame Tools und vertrauenswürdige Prozesse dazu, wo Personen zunehmend sammeln, lernen und arbeiten.

Mit apps erweitern Sie Teams entsprechend Ihren Anforderungen. Erstellen Sie etwas ganz neues für Teams oder integrieren Sie eine vorhandene app.

## <a name="what-are-teams-apps"></a>Was sind Microsoft Teams-apps?

Personen ermitteln und verwenden Teams-Apps über eine Reihe von Platt Form [Funktionen](capabilities-overview.md).

Einige apps sind einfach (Benachrichtigungen senden), andere sind komplex (Patientendatensätze anzeigen). Beachten Sie bei der Planung Ihrer APP, dass Teams ein Hub für die Zusammenarbeit sind. Die besten Teams-Apps helfen Benutzern, sich selbst auszudrücken und besser zusammenzuarbeiten.

:::row:::
   :::column span="":::

### <a name="tabs"></a>Registerkarten

**Erhalten Sie Informationen bequemer**: manchmal müssen Sie einfach nur die Suche vereinfachen. Zeigt eine wichtige Webseite auf einer [Registerkarte](../tabs/what-are-tabs.md)an, die eine Vollbildansicht für statischen und dynamischen Inhalt in Microsoft Teams bietet.

:::image type="content" source="doc-links/images/overview-tabs.png" alt-text="Konzeptionelle Darstellung dessen, was Registerkarten im Microsoft Teams-Client aussehen." border="false":::

   :::column-end:::
   :::column span="":::

### <a name="messaging-extensions"></a>Messaging-Erweiterungen

**Vereinfachung des Multitaskings**: mit [Messaging-Erweiterungen](../messaging-extensions/what-are-messaging-extensions.md)können Sie in einer Unterhaltung externe Informationen schnell freigeben. Sie können auch auf eine Nachricht reagieren, beispielsweise das Erstellen eines Hilfe Tickets basierend auf dem Inhalt eines Kanal Beitrags.

:::image type="content" source="doc-links/images/overview-messaging.png" alt-text="Konzeptionelle Darstellung, wie Messaging-Erweiterungen im Teams-Client aussehen." border="false":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::

### <a name="bots"></a>Bots

**Wörter in Aktionen umwandeln**: Unterhaltungen führen häufig dazu, dass Sie etwas tun müssen (Generieren einer Bestellung, Überprüfen des Codes, Überprüfen des Ticket Status usw.). Ein [bot](../bots/what-are-bots.md) kann diese Art von Workflows direkt innerhalb von Teams abstoßen.

:::image type="content" source="doc-links/images/overview-bots.png" alt-text="Konzeptionelle Darstellung dessen, was Bots im Microsoft Teams-Client aussieht." border="false":::

   :::column-end:::
   :::column span="":::

### <a name="webhooks"></a>Webhooks

**Kommunikation mit externen apps**: [eingehende webhooks](../webhooks-and-connectors/what-are-webhooks-and-connectors.md#incoming-webhooks) stellen eine einfache Möglichkeit zum automatischen Senden von Benachrichtigungen von einer anderen APP an einen Teams-Kanal dar. Mit [ausgehenden webhooks](../webhooks-and-connectors/what-are-webhooks-and-connectors.md#outgoing-webhooks)senden Sie Ihrem Webdienst eine Nachricht mit einem @mention.

:::image type="content" source="doc-links/images/overview-connectors.png" alt-text="Konzeptionelle Darstellung dessen, was Konnektoren im Teams-Client aussieht." border="false":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::

### <a name="microsoft-graph-for-teams"></a>Microsoft Graph für Teams

**Verwenden von Teams-Daten**: die [Microsoft Graph-Rest-API für Teams](https://docs.microsoft.com/graph/teams-concept-overview) bietet Zugriff auf Informationen zu Teams, Kanälen, Benutzern und Nachrichten, die Sie beim Erstellen oder Erweitern von Features für Ihre APP unterstützen können.

:::image type="content" source="doc-links/images/overview-graph.png" alt-text="Konzeptionelle Darstellung der Microsoft Graph-Rest-API für Teams." border="false":::

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

## <a name="get-started"></a>Erste Schritte

Wechseln Sie direkt mit unseren ersten App-Lernprogrammen, erfahren Sie, wie Sie vorhandene apps integrieren und importieren, oder nehmen Sie sich Zeit, um mehr über den Lebenszyklus der Teams-App-Entwicklung zu erfahren.

:::row:::
   :::column span="2":::

### <a name="start-building"></a>Erstellen beginnen

   Machen Sie sich schnell mit der Erstellung für Microsoft Teams vertraut, indem Sie eine einfache APP erstellen und einige häufig verwendete Funktionen hinzufügen.

   > [!div class="nextstepaction"]
   > [Erstellen Sie jetzt Ihre erste app.](build-your-first-app/building-real-world-app.md)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

### <a name="integrate-with-teams"></a>Integration in Microsoft Teams

   Verschmelzen Sie die Features, die Benutzer lieben, über eine vorhandene Webanwendung, einen Dienst oder ein System mit den kollaborativen Features von Microsoft Teams.

   > [!div class="nextstepaction"]
   > [Integrieren einer vorhandenen APP](migrating-web-apps.md)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

### <a name="a-little-code-goes-a-long-way"></a>Ein kleiner Code geht ein langer Weg

   Sie müssen kein Experte Programmierer sein, um eine großartige Teams-APP zu erstellen. Versuchen Sie eine von mehreren Lösungen mit niedrigem Code.

   > [!div class="nextstepaction"]
   > [Erstellen einer Low-Code-APP](low-code-solutions.md)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

### <a name="trust-the-process"></a>Dem Prozess Vertrauen

   Erfahren Sie mehr über den gesamten Entwicklungsprozess für Teams-Plattformen, um eine APP für Ihre Organisation oder andere effektiv zu planen, zu entwerfen, zu erstellen und zu veröffentlichen.

   > [!div class="nextstepaction"]
   > [Starten der Planung Ihrer APP](../concepts/extensibility-points.md)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

## <a name="resources"></a>Ressourcen

* [Hinzufügen einer Freigabe zur Schaltfläche "Teams" zu Ihrer Website](../concepts/build-and-test/share-to-teams.md)
* [Fluent-Entwurfs System](https://fluentsite.z22.web.core.windows.net/)
* [Microsoft Teams-JavaScript-SDK](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/?view=msteams-client-js-latest&preserve-view=true)
* [Bot Framework SDK für JavaScript](https://github.com/Microsoft/botbuilder-js) und [bot Framework SDK für .net](https://github.com/Microsoft/botbuilder-dotnet/)
* [Veröffentlichen Ihrer APP in einer Organisation oder AppSource](../concepts/deploy-and-publish/overview.md)
