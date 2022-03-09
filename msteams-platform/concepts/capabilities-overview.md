---
title: Grundlegendes zu App-Features
author: heath-hamilton
description: Beschreibung der Funktionen von Teams-Apps, z. B. Registerkarten, Bots, Messagingerweiterungen und Webhooks und Connectors; App-Bereich, z. B. persönliche und freigegebene Apps
ms.topic: conceptual
ms.localizationpriority: high
ms.author: lajanuar
ms.date: 09/22/2020
keywords: Registerkarten Bots Messaging-Erweiterungen Webhooks Connectors
ms.openlocfilehash: ecc7ddc9ff1a80aa4eb5b37c55088f5fa5721b37
ms.sourcegitcommit: 2fdca6fb0ade3f6b460eb9a4dfea0a8e2ab8d3b9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/08/2022
ms.locfileid: "63355545"
---
# <a name="understand-microsoft-teams-app-features"></a>Grundlegendes zu Microsoft Teams-App-Features

Es gibt mehrere Möglichkeiten, Teams zu erweitern, sodass jede App einzigartig ist. Eine Teams-App kann sich für einen Benutzer auf unterschiedliche Weise bemerkbar machen. Zu den Features einer Teams-App gehören:

- App-Funktionen
- App-Bereich

Beispielsweise kann ein Benutzer mit einer App auf einer Canvas-Registerkarte interagieren, um eine Aktivität auszuführen, oder er kann sich dafür entscheiden, dies mithilfe eines Konversationsbots zu tun. Sie können nur eine Funktion verwenden, z. B. einen Webhook, während andere über mehrere Funktionen verfügen, um Benutzern verschiedene Optionen zu bieten.

Diese Funktionen können in verschiedenen Bereichen vorhanden sein. Ihre App kann z. B. Daten an einem zentralen freigegebenen Ort anzeigen, d. h. auf der Registerkarte, und dieselben Informationen über eine persönliche Konversationsschnittstelle, d. h. den Bot, darstellen.

## <a name="app-capabilities"></a>App-Funktionen

Um Ihre App erweitern zu können, müssen Sie alle Kernfunktionen und Einstiegspunkte verstehen, die in einem Gemeinsamen Bereich funktionieren. Sie können mit den Erweiterungspunkten zum Erstellen Ihrer Apps experimentieren. Wichtige App-Projektkomponenten helfen Ihnen, Ihre App-Seite ordnungsgemäß zu konfigurieren.

Ihre Teams-Apps verfügen über eine oder alle der folgenden Kernfunktionen:

:::row:::
   :::column span="":::
### <a name="personal-apps"></a>Persönliche Apps

Eine [persönliche App](../concepts/design/personal-apps.md) ist ein dedizierter Bereich oder Bot, der Nutzern hilft, sich auf ihre eigenen Aufgaben zu konzentrieren oder für sie wichtige Aktivitäten anzuzeigen.

   :::column-end:::

   :::column span="":::

:::image type="content" source="../assets/images/overview-personal-apps-2021.png" alt-text="Konzeptionelle Darstellung, wie persönliche Apps im Teams-Client aussehen." border="false":::

   :::column-end:::

:::row-end:::

:::row:::
   :::column span="":::

### <a name="tabs"></a>Registerkarten

Zeigen Sie Ihre webbasierten Inhalte auf einer [Registerkarte](../tabs/what-are-tabs.md) an, auf der Personen darüber diskutieren und gemeinsam daran arbeiten können.

   :::column-end:::

   :::column span="":::

:::image type="content" source="../assets/images/overview-channel-chat-apps-2021.png" alt-text="Konzeptionelle Darstellung, wie Registerkarten im Teams-Client aussehen." border="false":::

   :::column-end:::

:::row-end:::

:::row:::
   :::column span="":::

### <a name="bots"></a>Bots

Unterhaltungen führen häufig dazu, etwas tun müssen (eine Bestellung generieren, meinen Code überprüfen, den Ticketstatus überprüfen usw.). Ein [Bot](../bots/what-are-bots.md) kann diese Arten von Workflows direkt in Teams starten.

   :::column-end:::

   :::column span="":::

:::image type="content" source="../assets/images/overview-bots-2021.png" alt-text="Konzeptionelle Darstellung, wie Bots im Teams-Client aussehen." border="false":::

   :::column-end:::

:::row-end:::

:::row:::

   :::column span="":::

### <a name="messaging-extensions"></a>Messaging-Erweiterungen

Mit [Messagingerweiterungen](../messaging-extensions/what-are-messaging-extensions.md)können Sie schnell externe Informationen in einer Unterhaltung freigeben. Sie können auch auf eine Nachricht reagieren, z. B. durch das Erstellen eines Hilfetickets basierend auf dem Inhalt eines Kanalbeitrags.

   :::column-end:::

   :::column span="":::

:::image type="content" source="../assets/images/overview-messaging-extensions-2021.png" alt-text="Konzeptionelle Darstellung, wie Messaging-Erweiterungen im Teams-Client aussehen." border="false":::

   :::column-end:::
:::row-end:::

:::row:::

   :::column span="":::

### <a name="meeting-extensions"></a>Besprechungserweiterungen

Es gibt einige Möglichkeiten,[Ihre App in die Teams-Anrufe einzubinden](../apps-in-teams-meetings/design/designing-apps-in-meetings.md).

   :::column-end:::

   :::column span="":::

:::image type="content" source="../assets/images/overview-meeting-extensions-2021.png" alt-text="Konzeptionelle Darstellung, wie Besprechungserweiterungen im Teams-Client aussehen." border="false":::

   :::column-end:::
:::row-end:::

:::row:::

   :::column span="":::

### <a name="webhooks-and-connectors"></a>Webhooks und Connectors

[Eingehende Webhooks](../webhooks-and-connectors/what-are-webhooks-and-connectors.md#incoming-webhooks) sind eine einfache Möglichkeit, automatisch Benachrichtigungen von einer anderen App an einen Teams-Kanal zu senden. Mit [ausgehenden Webhooks](../webhooks-and-connectors/what-are-webhooks-and-connectors.md#outgoing-webhooks) senden Sie eine Nachricht mit einem @mention an Ihren Webdienst.

   :::column-end:::

   :::column span="":::

:::image type="content" source="../assets/images/overview-connectors.png" alt-text="Konzeptionelle Darstellung, wie Connectors im Teams-Client aussehen." border="false":::

   :::column-end:::
:::row-end:::

:::row:::

   :::column span="":::

### <a name="microsoft-graph-for-teams"></a>Microsoft Graph für Teams

Die [Microsoft Graph-API für Teams](/graph/teams-concept-overview) bietet Zugriff auf Informationen zu Teams, Kanälen, Nutzern und Nachrichten, die Ihnen helfen können, Features für Ihre App zu erstellen oder zu verbessern (z. B. Rich Notifications).

   :::column-end:::

   :::column span="":::

:::image type="content" source="../assets/images/overview-graph.png" alt-text="Konzeptionelle Darstellung der Microsoft Graph-API für Teams." border="false":::

   :::column-end:::
:::row-end:::

> [!NOTE]
> Der Teams Store hat sich weiterentwickelt: Zuvor wurden die branchenspezifischen Apps aktualisiert, indem die Auslassungspunkte auf der Kachel ausgewählt wurden. Mit der aktualisierten Teams Store-Oberfläche können Sie jetzt die branchenspezifischen Apps aktualisieren, indem Sie sich beim [Teams Admin Center](https://admin.teams.microsoft.com)anmelden.

## <a name="choose-the-correct-scope-for-your-app"></a>Wählen Sie den richtigen Bereich für Ihre App aus.

Sie können den App-Bereich wie folgt auswählen:

- Persönliche App-Erfahrung: Eine persönliche App ist ein dedizierter Bereich oder Bot, der Nutzern hilft, sich auf ihre eigenen Aufgaben zu konzentrieren oder für sie wichtige Aktivitäten anzuzeigen.
- Freigegebene App-Erfahrung: Team, Kanal und Chat sind Bereiche für die Zusammenarbeit. Apps in diesen Kontexten sind für alle Nutzer in diesem Bereich verfügbar. Zusammenarbeitsbereiche konzentrieren sich in der Regel auf Workflows für die Interaktionen Ihrer App oder die Erschließung neuer sozialer Interaktionen.

## <a name="see-also"></a>Siehe auch

* [Erstellen von Apps für Teams](../overview.md)
* [Erstellen Ihrer ersten Microsoft Teams-App](../build-your-first-app/build-first-app-overview.md)