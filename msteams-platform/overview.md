---
title: Erstellen von Apps für die Microsoft Teams-Plattform
author: heath-hamilton
description: Hier erhalten Sie einen Überblick darüber, wie Entwickler Microsoft Teams Features mit benutzerdefinierten Apps erweitern können.
ms.topic: overview
ms.localizationpriority: high
ms.author: lajanuar
ms.date: 05/24/2021
ms.openlocfilehash: 1a7957c8ea6d889ffe5ab7e40c8a5bb1377b6ca5
ms.sourcegitcommit: 9e448dcdfd78f4278e9600808228e8158d830ef7
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/17/2022
ms.locfileid: "62059623"
---
# <a name="build-apps-for-microsoft-teams"></a>Apps für Microsoft Teams erstellen

Microsoft Teams Apps bieten wichtige Informationen, allgemeine Tools und vertrauenswürdige Prozesse in einen Bereich, in dem sich immer mehr Menschen treffen, lernen und arbeiten.

Mit Apps können Sie Teams erweitern und so an Ihre Anforderungen anpassen. Erstellen Sie etwas völlig Neues für Teams oder integrieren Sie eine vorhandene App.

> [!div class="nextstepaction"]
> [Beginnen Sie hier](get-started/get-started-overview.md)

## <a name="what-are-teams-apps"></a>Was sind Teams Apps?

Teams Apps sind eine Kombination von [Funktionen](concepts/capabilities-overview.md). Einige Apps dienen nur einer einfachen Funktion (Senden von Benachrichtigungen), während andere komplex sind (Verwalten von Patientendatensätzen). Denken Sie bei der Planung Ihrer App daran, dass Teams ein Hub für die Zusammenarbeit ist. Die besten Teams Apps helfen den Menschen, sich auszudrücken und besser zusammenzuarbeiten.

### <a name="personal-apps"></a>Persönliche Apps

:::row:::
   :::column span="1":::

**Helfen Sie den Benutzern, sich zu konzentrieren:** Eine [persönliche App](concepts/design/personal-apps.md) ist ein dedizierter Bereich oder Bot, der Benutzern dabei hilft, sich auf ihre eigenen Aufgaben zu konzentrieren oder ihnen Aktivitäten anzuzeigen, die ihnen wichtig sind.

   :::column-end:::

   :::column span="3":::

:::image type="content" source="assets/images/overview-personal-apps-2021.png" alt-text="Konzeptionelle Darstellung, wie persönliche Apps im Teams-Client aussehen." border="false":::

   :::column-end:::

:::row-end:::

### <a name="tabs"></a>Registerkarten

:::row:::
   :::column span="1":::

**Einfachere Zusammenarbeit**: Zeigen Sie Ihre webbasierten Inhalte auf einer [Registerkarte](tabs/what-are-tabs.md) an, auf der die Benutzer diese gemeinsam besprechen und bearbeiten können.

   :::column-end:::

   :::column span="3":::

:::image type="content" source="assets/images/overview-channel-chat-apps-2021.png" alt-text="Konzeptionelle Darstellung, wie Registerkarten im Teams-Client aussehen." border="false":::

   :::column-end:::

:::row-end:::

### <a name="bots"></a>Bots

:::row:::
   :::column span="1":::

**Umwandeln von Wörtern in Aktionen**: Unterhaltungen führen häufig dazu, dass eine Aktion erforderlich ist (eine Bestellung muss generiert werden, mein Code oder der Ticketstatus müssen überprüfen werden usw.). Ein [Bot](bots/what-are-bots.md) kann diese Arten von Workflows direkt in Teams starten.

   :::column-end:::

   :::column span="3":::

:::image type="content" source="assets/images/overview-bots-2021.png" alt-text="Konzeptionelle Darstellung, wie Bots im Teams-Client aussehen." border="false":::

   :::column-end:::

:::row-end:::

### <a name="messaging-extensions"></a>Messaging-Erweiterungen

:::row:::

   :::column span="1":::

**Vereinfachen Sie das Multitasking**: Mit [Messaging-Erweiterungen](messaging-extensions/what-are-messaging-extensions.md)können Sie schnell externe Informationen in einer Unterhaltung freigeben. Sie können auch auf eine Nachricht reagieren, z. B. durch das Erstellen eines Hilfetickets basierend auf dem Inhalt eines Kanalbeitrags.

   :::column-end:::

   :::column span="3":::

:::image type="content" source="assets/images/overview-messaging-extensions-2021.png" alt-text="Konzeptionelle Darstellung, wie Messaging-Erweiterungen im Teams-Client aussehen." border="false":::

   :::column-end:::
:::row-end:::

### <a name="meeting-extensions"></a>Besprechungserweiterungen

:::row:::

   :::column span="1":::

**Erstellen von Apps für Besprechungen**: Es gibt einige Optionen zum [Integrieren Ihrer App in die Teams Anruferfahrung](apps-in-teams-meetings/design/designing-apps-in-meetings.md).

   :::column-end:::

   :::column span="3":::

:::image type="content" source="assets/images/overview-meeting-extensions-2021.png" alt-text="Konzeptionelle Darstellung, wie Besprechungserweiterungen im Teams-Client aussehen." border="false":::

   :::column-end:::
:::row-end:::

### <a name="webhooks-and-connectors"></a>Webhooks und Connectors

:::row:::

   :::column span="":::

**Kommunikation mit externen Apps**: [Eingehende Webhooks](webhooks-and-connectors/what-are-webhooks-and-connectors.md#incoming-webhooks) sind eine einfache Möglichkeit, automatisch Benachrichtigungen von einer anderen App an einen Teams Kanal zu senden. Mit [ausgehenden Webhooks](webhooks-and-connectors/what-are-webhooks-and-connectors.md#outgoing-webhooks) senden Sie eine Nachricht mit einem @mention an Ihren Webdienst.

   :::column-end:::

   :::column span="":::

:::image type="content" source="assets/images/overview-connectors.png" alt-text="Konzeptionelle Darstellung, wie Connectors im Teams-Client aussehen." border="false":::

   :::column-end:::
:::row-end:::

### <a name="microsoft-graph-for-teams"></a>Microsoft Graph für Teams

:::row:::

   :::column span="":::

**Nutzen von Teams-Daten**: Die [Microsoft Graph-API für Teams](/graph/teams-concept-overview) bietet Zugriff auf Informationen zu Teams, Kanälen, Benutzern und Nachrichten, mit denen Sie Features für Ihre App erstellen oder verbessern können (z. B. umfangreiche Benachrichtigungen).

   :::column-end:::

   :::column span="":::

:::image type="content" source="assets/images/overview-graph.png" alt-text="Konzeptionelle Darstellung der Microsoft Graph-API für Teams." border="false":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

## <a name="start-building"></a>Mit dem Erstellen beginnen

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

## <a name="a-little-code-goes-a-long-way"></a>Selbst ein kleiner Code kann viel bewirken

Sie müssen kein erfahrener Programmierer sein, um eine großartige Teams-App zu erstellen. Probieren Sie eine von mehreren Lösungen mit nur wenig Code aus.

> [!div class="nextstepaction"]
> [Erstellen einer App mit wenig Code](samples/teams-low-code-solutions.md)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="2":::

## <a name="get-ideas-for-your-app"></a>Inspirierende Ideen für Ihre App erhalten

Sie möchten sich für die App-Entwicklung inspirieren lassen? Durchsuchen Sie unsere Liste der realen Szenarien und Branchenlösungen mit High-Fidelity-Konzeptmodellen, um die verschiedenen Möglichkeiten zu verstehen, wie Teams Apps Ihren Benutzern helfen können.

> [!div class="nextstepaction"]
> [Anzeigen von App-Szenarien](https://adoption.microsoft.com/extensibility-look-book/scenarios/)

   :::column-end:::
   :::column span="":::

   :::column-end:::
:::row-end:::

## <a name="test-your-app-running-across-microsoft-365"></a>Testen Ihrer App, die über Microsoft 365 ausgeführt wird

Mit Microsoft Teams JavaScript-Client-SDK v2 Preview können Sie eine Vorschau Ihrer Teams Apps anzeigen, die in anderen stark frequentierten Microsoft 365-Umgebungen ausgeführt werden.

> [!div class="nextstepaction"]
> [Erweitern Ihrer App](m365-apps/overview.md)

## <a name="see-also"></a>Siehe auch

* [App-Grundlagen](~/concepts/app-fundamentals-overview.md)
* [Entwerfen Ihrer Teams-App](~/concepts/design/design-teams-app-process.md)
* [Zuordnen von Anwendungsfällen zu Teams App-Funktionen](~/concepts/design/map-use-cases.md)
