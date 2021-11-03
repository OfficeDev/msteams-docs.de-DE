---
title: Erstellen von Apps für die Microsoft Teams-Plattform
author: heath-hamilton
description: Hier erhalten Sie einen Überblick, wie Entwickler Microsoft Teams Features mit benutzerdefinierten Apps erweitern können.
ms.topic: overview
ms.localizationpriority: medium
ms.author: lajanuar
ms.date: 05/24/2021
ms.openlocfilehash: fcec0e01f6f9d635896ef14eb4efee5e56f9e761
ms.sourcegitcommit: 22c9e44437720d30c992a4a3626a2a9f745983c1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/03/2021
ms.locfileid: "60720113"
---
# <a name="build-apps-for-microsoft-teams"></a>Apps für Microsoft Teams erstellen

Microsoft Teams Apps bieten wichtige Informationen, allgemeine Tools und vertrauenswürdige Prozesse, in denen sich Menschen zunehmend sammeln, lernen und arbeiten.

Apps erweitern Teams entsprechend Ihren Anforderungen. Erstellen Sie etwas ganz Neues für Teams oder integrieren Sie eine vorhandene App.

> [!div class="nextstepaction"]
> [Beginnen Sie hier](get-started/get-started-overview.md)

## <a name="what-are-teams-apps"></a>Was sind Teams Apps?

Teams Apps sind eine Kombination von [Funktionen.](concepts/capabilities-overview.md) Einige Apps sind einfach (Benachrichtigungen senden), während andere komplex sind (Patientendatensätze verwalten). Denken Sie bei der Planung Ihrer App daran, dass Teams ein Hub für die Zusammenarbeit ist. Die besten Teams Apps helfen Menschen, sich auszudrücken und besser zusammenzuarbeiten.

### <a name="personal-apps"></a>Persönliche Apps

:::row:::
   :::column span="1":::

**Helfen Sie den Benutzern, sich zu konzentrieren:** Eine [persönliche App](concepts/design/personal-apps.md) ist ein dedizierter Bereich oder Bot, der benutzern dabei hilft, sich auf ihre eigenen Aufgaben zu konzentrieren oder ihnen wichtige Aktivitäten anzuzeigen.

   :::column-end:::

   :::column span="3":::

:::image type="content" source="assets/images/overview-personal-apps-2021.png" alt-text="Konzeptionelle Darstellung, wie persönliche Apps im Teams-Client aussehen." border="false":::

   :::column-end:::

:::row-end:::

### <a name="tabs"></a>Registerkarten

:::row:::
   :::column span="1":::

**Einfachere Zusammenarbeit:** Zeigen Sie Ihre webbasierten Inhalte auf einer [Registerkarte](tabs/what-are-tabs.md) an, auf der Benutzer diese gemeinsam besprechen und bearbeiten können.

   :::column-end:::

   :::column span="3":::

:::image type="content" source="assets/images/overview-channel-chat-apps-2021.png" alt-text="Konzeptionelle Darstellung, wie Registerkarten im Teams-Client aussehen." border="false":::

   :::column-end:::

:::row-end:::

### <a name="bots"></a>Bots

:::row:::
   :::column span="1":::

**Verwandeln Sie Wörter in Aktionen:** Unterhaltungen führen häufig dazu, dass sie etwas tun müssen (eine Bestellung generieren, meinen Code überprüfen, den Ticketstatus überprüfen usw.). Ein [Bot](bots/what-are-bots.md) kann diese Arten von Workflows direkt in Teams starten.

   :::column-end:::

   :::column span="3":::

:::image type="content" source="assets/images/overview-bots-2021.png" alt-text="Konzeptionelle Darstellung, wie Bots im Teams-Client aussehen." border="false":::

   :::column-end:::

:::row-end:::

### <a name="messaging-extensions"></a>Messaging-Erweiterungen

:::row:::

   :::column span="1":::

**Vereinfachen Sie das Multitasking:** Mit [Messaging-Erweiterungen](messaging-extensions/what-are-messaging-extensions.md)können Sie schnell externe Informationen in einer Unterhaltung freigeben. Sie können auch auf eine Nachricht reagieren, z. B. das Erstellen eines Hilfetickets basierend auf dem Inhalt eines Kanalbeitrags.

   :::column-end:::

   :::column span="3":::

:::image type="content" source="assets/images/overview-messaging-extensions-2021.png" alt-text="Konzeptionelle Darstellung, wie Messaging-Erweiterungen im Teams-Client aussehen." border="false":::

   :::column-end:::
:::row-end:::

### <a name="meeting-extensions"></a>Besprechungserweiterungen

:::row:::

   :::column span="1":::

**Erstellen von Apps für Besprechungen:** Es gibt einige Optionen zum [Integrieren Ihrer App in die Teams Anruferfahrung.](apps-in-teams-meetings/design/designing-apps-in-meetings.md)

   :::column-end:::

   :::column span="3":::

:::image type="content" source="assets/images/overview-meeting-extensions-2021.png" alt-text="Konzeptionelle Darstellung, wie Besprechungserweiterungen im Teams-Client aussehen." border="false":::

   :::column-end:::
:::row-end:::

### <a name="webhooks-and-connectors"></a>Webhooks und Connectors

:::row:::

   :::column span="":::

**Kommunikation mit externen Apps:** [Eingehende Webhooks](webhooks-and-connectors/what-are-webhooks-and-connectors.md#incoming-webhooks) sind eine einfache Möglichkeit, automatisch Benachrichtigungen von einer anderen App an einen Teams Kanal zu senden. Senden Sie bei [ausgehenden Webhooks](webhooks-and-connectors/what-are-webhooks-and-connectors.md#outgoing-webhooks)eine Nachricht an Ihren Webdienst mit einem @mention.

   :::column-end:::

   :::column span="":::

:::image type="content" source="assets/images/overview-connectors.png" alt-text="Konzeptionelle Darstellung, wie Connectors im Teams-Client aussehen." border="false":::

   :::column-end:::
:::row-end:::

### <a name="microsoft-graph-for-teams"></a>Microsoft Graph für Teams

:::row:::

   :::column span="":::

**Nutzen sie Teams Daten:** Die [Microsoft Graph-API für Teams](/graph/teams-concept-overview) bietet Zugriff auf Informationen zu Teams, Kanälen, Benutzern und Nachrichten, die Ihnen helfen können, Features für Ihre App zu erstellen oder zu verbessern (z. B. umfangreiche Benachrichtigungen).

   :::column-end:::

   :::column span="":::

:::image type="content" source="assets/images/overview-graph.png" alt-text="Konzeptionelle Darstellung der Microsoft Graph-API für Teams." border="false":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

## <a name="start-building"></a>Beginnen Sie mit dem Erstellen

Machen Sie sich schnell mit der Erstellung für Teams vertraut, indem Sie Ihre Umgebung einrichten und eine einfache App erstellen.

> [!div class="nextstepaction"]
> [Die erste App erstellen](get-started/get-started-overview.md)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

## <a name="integrate-with-teams"></a>Integration in Microsoft Teams

Kombinieren Sie die Features, die Benutzer an einer vorhandenen Web-App, einem Dienst oder System schätzen, mit den Features für die Zusammenarbeit von Teams.

> [!div class="nextstepaction"]
> [Integrieren einer vorhandenen App](samples/integrating-web-apps.md)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

## <a name="a-little-code-goes-a-long-way"></a>Ein kleiner Code ist ein langer Weg

Sie müssen kein erfahrener Programmierer sein, um eine großartige Teams-App zu erstellen. Probieren Sie eine von mehreren Lösungen mit geringem Code aus.

> [!div class="nextstepaction"]
> [Erstellen einer App mit wenig Code](samples/teams-low-code-solutions.md)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

## <a name="get-ideas-for-your-app"></a>Holen Sie sich Ideen für Ihre App

Sie möchten sich für die App-Entwicklung inspirieren? Durchsuchen Sie unsere Liste der realen Szenarien und Branchenlösungen mit High-Fidelity-Konzeptmodellen, um die verschiedenen Möglichkeiten zu verstehen, wie Teams Apps Ihren Benutzern helfen können.

> [!div class="nextstepaction"]
> [Anzeigen von App-Szenarien](https://adoption.microsoft.com/extensibility-look-book/scenarios/)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

## <a name="see-also"></a>Siehe auch

* [Hinzufügen einer Schaltfläche "Freigeben für Teams" zu Ihrer Website](concepts/build-and-test/share-to-teams.md)
* [Entwerfen Ihrer Teams-App](concepts/design/design-teams-app-overview.md)
* [Microsoft Teams JavaScript-Client-SDK](/javascript/api/@microsoft/teams-js/?view=msteams-client-js-latest&preserve-view=true)
* Bot Framework SDK für [JavaScript](https://github.com/Microsoft/botbuilder-js) und [.NET](https://github.com/Microsoft/botbuilder-dotnet/)
* [Verteilen Ihrer Teams-App](concepts/deploy-and-publish/apps-publish-overview.md)
