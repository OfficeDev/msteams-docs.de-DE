---
title: Erstellen von Apps für die Microsoft Teams-Plattform
author: heath-hamilton
description: Erhalten Sie eine Übersicht darüber, wie Entwickler Microsoft Teams-Features mit benutzerdefinierten Apps erweitern können.
ms.topic: overview
ms.author: lajanuar
ms.date: 09/22/2020
ms.openlocfilehash: 45be2dd7d0e421ac331cfc02703f0b81eab3dfe5
ms.sourcegitcommit: 4539479289b43812eaae07a1c0f878bed815d2d2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/12/2021
ms.locfileid: "49797771"
---
# <a name="build-apps-for-microsoft-teams"></a>Apps für Microsoft Teams erstellen

Microsoft Teams-Apps bieten wichtige Informationen, allgemeine Tools und vertrauenswürdige Prozesse, in denen Benutzer zunehmend sammeln, lernen und arbeiten.

Apps erweitern Teams so, dass sie Ihren Anforderungen entsprechen. Erstellen Sie etwas ganz Neues für Teams, oder integrieren Sie eine vorhandene App.

> [!div class="nextstepaction"]
> [Beginnen Sie hier](build-your-first-app/build-first-app-overview.md)

## <a name="what-are-teams-apps"></a>Was sind Teams-Apps?

Teams Apps sind eine Kombination aus [Funktionen und](concepts/capabilities-overview.md) [Einstiegspunkten.](concepts/extensibility-points.md) Beispielsweise können Benutzer mit dem Bot *(Funktion)* Ihrer App in einem *Kanal* (Einstiegspunkt) chatten.

Einige Apps sind einfach (Benachrichtigungen senden), während andere komplex sind (Patientendatensätze verwalten). Denken Sie beim Planen Ihrer App daran, dass Teams ein Hub für die Zusammenarbeit ist. Die besten Teams-Apps helfen, sich selbst zu ausdrücken und besser zusammen zu arbeiten.

:::row:::
   :::column span="":::

### <a name="tabs"></a>Registerkarten

**Einfachere Informationen:** Manchmal müssen Sie die Suche vereinfachen. Zeigen Sie eine wichtige Webseite auf einer [Registerkarte](tabs/what-are-tabs.md)an, die eine Vollbildweberfahrung für statische und dynamische Inhalte in Teams bietet.

:::image type="content" source="assets/images/overview-tabs.png" alt-text="Konzeptionelle Darstellung, wie Registerkarten im Teams-Client aussehen." border="false":::

   :::column-end:::

   :::column span="":::

### <a name="bots"></a>Bots

**Machen Sie Wörter in Aktionen:** Unterhaltungen führen häufig dazu, dass sie eine Aktion ausführen müssen (Eine Bestellung generieren, meinen Code überprüfen, den Ticketstatus überprüfen usw.). Ein [Bot](bots/what-are-bots.md) kann diese Arten von Workflows direkt in Teams starten.

:::image type="content" source="assets/images/overview-bots.png" alt-text="Konzeptionelle Darstellung, wie Bots im Teams-Client aussehen." border="false":::

   :::column-end:::

:::row-end:::

:::row:::

   :::column span="":::

### <a name="messaging-extensions"></a>Messaging-Erweiterungen

**Einfacheres Multitask:** [Mit](messaging-extensions/what-are-messaging-extensions.md)Messagingerweiterungen können Sie externe Informationen in einer Unterhaltung schnell freigeben. Sie können auch auf eine Nachricht ein, z. B. das Erstellen eines Hilfetickets basierend auf dem Inhalt eines Kanalbeitrags.

:::image type="content" source="assets\images\overview-messaging.png" alt-text="Konzeptionelle Darstellung, wie Messagingerweiterungen im Teams-Client aussehen." border="false":::

   :::column-end:::

   :::column span="":::

### <a name="webhooks"></a>Webhooks

**Kommunikation mit externen Apps:** [Eingehende Webhooks](webhooks-and-connectors/what-are-webhooks-and-connectors.md#incoming-webhooks) sind eine einfache Möglichkeit zum automatischen Senden von Benachrichtigungen von einer anderen App an einen Teams-Kanal. Nachricht [bei ausgehenden Webhooks](webhooks-and-connectors/what-are-webhooks-and-connectors.md#outgoing-webhooks)an Ihren Webdienst mit @mention.

:::image type="content" source="assets/images/overview-connectors.png" alt-text="Konzeptionelle Darstellung, wie Connectors im Teams-Client aussehen." border="false":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::

### <a name="microsoft-graph-for-teams"></a>Microsoft Graph für Teams

**Nutzen von Teams-Daten:** Die [Microsoft Graph-API](https://docs.microsoft.com/graph/teams-concept-overview) für Teams bietet Zugriff auf Informationen zu Teams, Kanälen, Benutzern und Nachrichten, mit deren Hilfe Sie Features für Ihre App erstellen oder verbessern können.

:::image type="content" source="assets/images/overview-graph.png" alt-text="Konzeptionelle Darstellung der Microsoft Graph-API für Teams." border="false":::

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

## <a name="start-building"></a>Mit dem Erstellen beginnen

   Machen Sie sich schnell mit dem Erstellen für Teams vertraut, indem Sie eine einfache App erstellen und einige häufig verwendete Funktionen hinzufügen.

   > [!div class="nextstepaction"]
   > [Erstellen Ihrer ersten App jetzt](build-your-first-app/build-first-app-overview.md)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

## <a name="integrate-with-teams"></a>Integration in Teams

   Vermischen Sie die Features, die Benutzer über eine vorhandene Web-App, einen Dienst oder ein System mit den Features für die Zusammenarbeit von Teams haben.

   > [!div class="nextstepaction"]
   > [Integrieren einer vorhandenen App](samples/integrating-web-apps.md)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

## <a name="a-little-code-goes-a-long-way"></a>Ein wenig Code ist ein langer Weg

   Sie müssen kein erfahrener Programmierer sein, um eine großartige Teams-App zu erstellen. Probieren Sie eine von mehreren Low-Code-Lösungen aus.

   > [!div class="nextstepaction"]
   > [Erstellen einer App mit geringem Code](samples/teams-low-code-solutions.md)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

## <a name="resources"></a>Ressourcen

* [Hinzufügen einer Share-to-Teams-Schaltfläche zu Ihrer Website](concepts/build-and-test/share-to-teams.md)
* <a href="https://fluentsite.z22.web.core.windows.net/" target="_blank">Fluent-Benutzeroberfläche</a>
* [Microsoft Teams JavaScript client SDK](https://docs.microsoft.com/javascript/api/@microsoft/teams-js/?view=msteams-client-js-latest&preserve-view=true)
* [Bot Framework SDK für JavaScript](https://github.com/Microsoft/botbuilder-js) und [Bot Framework SDK für .NET](https://github.com/Microsoft/botbuilder-dotnet/)
* [Veröffentlichen Ihrer App in einer Organisation oder AppSource](concepts/deploy-and-publish/overview.md)
