---
title: Erstellen von Apps für die Microsoft Teams-Plattform
author: heath-hamilton
description: Übersicht darüber, wie Entwickler Microsoft Teams-Features mit benutzerdefinierten apps erweitern und anpassen können.
ms.topic: overview
ms.author: lajanuar
ms.date: 09/22/2020
ms.openlocfilehash: 6f5f3454885320669ef42383529d39fcfcfdfee8
ms.sourcegitcommit: c102da958759c13aa9e0f81bde1cffb34a8bef34
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/09/2020
ms.locfileid: "49604787"
---
# <a name="build-apps-for-microsoft-teams"></a>Apps für Microsoft Teams erstellen

Microsoft Teams-apps bringen wichtige Informationen, gemeinsame Tools und vertrauenswürdige Prozesse dazu, wo Personen zunehmend sammeln, lernen und arbeiten.

Mit apps erweitern Sie Teams entsprechend Ihren Anforderungen. Erstellen Sie etwas ganz neues für Teams oder integrieren Sie eine vorhandene app.

> [!div class="nextstepaction"]
> [Beginnen Sie hier](build-your-first-app/build-first-app-overview.md)

## <a name="what-are-teams-apps"></a>Was sind Microsoft Teams-apps?

Microsoft Teams-apps sind eine Kombination aus [Funktionen](concepts/capabilities-overview.md) und [Einstiegspunkten](concepts/extensibility-points.md). Beispielsweise können Personen mit dem *bot* (Funktion) Ihrer APP in einem *Kanal* (Einstiegspunkte) chatten.

Einige apps sind einfach (Benachrichtigungen senden), andere sind komplex (Verwalten von Patientendatensätzen). Beachten Sie bei der Planung Ihrer APP, dass Teams ein Hub für die Zusammenarbeit sind. Die besten Teams-Apps helfen Benutzern, sich selbst auszudrücken und besser zusammenzuarbeiten.

:::row:::
   :::column span="":::

### <a name="tabs"></a>Registerkarten

**Erhalten Sie Informationen bequemer**: manchmal müssen Sie einfach nur die Suche vereinfachen. Zeigt eine wichtige Webseite auf einer [Registerkarte](tabs/what-are-tabs.md)an, die eine Vollbildansicht für statischen und dynamischen Inhalt in Microsoft Teams bietet.

:::image type="content" source="assets/images/overview-tabs.png" alt-text="Konzeptionelle Darstellung dessen, was Registerkarten im Microsoft Teams-Client aussehen." border="false":::

   :::column-end:::
   :::column span="":::

### <a name="messaging-extensions"></a>Messaging-Erweiterungen

**Vereinfachung des Multitaskings**: mit [Messaging-Erweiterungen](messaging-extensions/what-are-messaging-extensions.md)können Sie in einer Unterhaltung externe Informationen schnell freigeben. Sie können auch auf eine Nachricht reagieren, beispielsweise das Erstellen eines Hilfe Tickets basierend auf dem Inhalt eines Kanal Beitrags.

:::image type="content" source="assets\images\overview-messaging.png" alt-text="Konzeptionelle Darstellung, wie Messaging-Erweiterungen im Teams-Client aussehen." border="false":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::

### <a name="bots"></a>Bots

**Wörter in Aktionen umwandeln**: Unterhaltungen führen häufig dazu, dass Sie etwas tun müssen (Generieren einer Bestellung, Überprüfen des Codes, Überprüfen des Ticket Status usw.). Ein [bot](bots/what-are-bots.md) kann diese Art von Workflows direkt innerhalb von Teams abstoßen.

:::image type="content" source="assets/images/overview-bots.png" alt-text="Konzeptionelle Darstellung dessen, was Bots im Microsoft Teams-Client aussieht." border="false":::

   :::column-end:::
   :::column span="":::

### <a name="webhooks"></a>Webhooks

**Kommunikation mit externen apps**: [eingehende webhooks](webhooks-and-connectors/what-are-webhooks-and-connectors.md#incoming-webhooks) stellen eine einfache Möglichkeit zum automatischen Senden von Benachrichtigungen von einer anderen APP an einen Teams-Kanal dar. Mit [ausgehenden webhooks](webhooks-and-connectors/what-are-webhooks-and-connectors.md#outgoing-webhooks)senden Sie Ihrem Webdienst eine Nachricht mit einem @mention.

:::image type="content" source="assets/images/overview-connectors.png" alt-text="Konzeptionelle Darstellung dessen, was Konnektoren im Teams-Client aussieht." border="false":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::

### <a name="microsoft-graph-for-teams"></a>Microsoft Graph für Teams

**Verwenden von Teams-Daten**: die [Microsoft Graph-API für Teams](https://docs.microsoft.com/graph/teams-concept-overview) bietet Zugriff auf Informationen zu Teams, Kanälen, Benutzern und Nachrichten, die Sie beim Erstellen oder Erweitern von Features für Ihre APP unterstützen können.

:::image type="content" source="assets/images/overview-graph.png" alt-text="Konzeptionelle Darstellung der Microsoft Graph-API für Teams." border="false":::

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

## <a name="get-started"></a>Erste Schritte

Wechseln Sie direkt mit unseren ersten App-Lernprogrammen, oder erfahren Sie, wie Sie vorhandene apps integrieren und importieren können.

:::row:::
   :::column span="2":::

### <a name="start-building"></a>Erstellen beginnen

   Machen Sie sich schnell mit der Erstellung für Microsoft Teams vertraut, indem Sie eine einfache APP erstellen und einige häufig verwendete Funktionen hinzufügen.

   > [!div class="nextstepaction"]
   > [Erstellen Sie jetzt Ihre erste app.](build-your-first-app/build-first-app-overview.md)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

### <a name="integrate-with-teams"></a>Integration in Microsoft Teams

   Verschmelzen Sie die Features, die Benutzer lieben, über eine vorhandene Webanwendung, einen Dienst oder ein System mit den kollaborativen Features von Microsoft Teams.

   > [!div class="nextstepaction"]
   > [Integrieren einer vorhandenen APP](samples/integrating-web-apps.md)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

### <a name="a-little-code-goes-a-long-way"></a>Ein kleiner Code geht ein langer Weg

   Sie müssen kein Experte Programmierer sein, um eine großartige Teams-APP zu erstellen. Versuchen Sie eine von mehreren Lösungen mit niedrigem Code.

   > [!div class="nextstepaction"]
   > [Erstellen einer Low-Code-APP](samples/teams-low-code-solutions.md)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

## <a name="resources"></a>Ressourcen

* [Hinzufügen einer Freigabe zur Schaltfläche "Teams" zu Ihrer Website](concepts/build-and-test/share-to-teams.md)
* <a href="https://fluentsite.z22.web.core.windows.net/" target="_blank">Fluent-Benutzeroberfläche</a>
* [Microsoft Teams JavaScript-Client-SDK](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/?view=msteams-client-js-latest&preserve-view=true)
* [Bot Framework SDK für JavaScript](https://github.com/Microsoft/botbuilder-js) und [bot Framework SDK für .net](https://github.com/Microsoft/botbuilder-dotnet/)
* [Veröffentlichen Ihrer APP in einer Organisation oder AppSource](concepts/deploy-and-publish/overview.md)
