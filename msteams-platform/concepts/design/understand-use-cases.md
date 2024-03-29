---
title: Grundlegendes zu Anwendungsfällen und Teams-Features Ihrer App
author: heath-hamilton
description: Erfahren Sie mehr über Microsoft Teams-App-Funktionen wie Registerkarten, Bots, Besprechungserweiterungen, Nachrichtenerweiterungen, Webhookconnectors, persönliche App-Erfahrungen und freigegebene App-Erfahrungen.
ms.topic: conceptual
ms.localizationpriority: high
ms.author: anclear
ms.openlocfilehash: 296f6d2e8fe5088c480490cc0dbcc035f9f659ec
ms.sourcegitcommit: 0e4fcbc5efff4bfa1dbfba1e5467bbfaa6638705
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/28/2022
ms.locfileid: "68773513"
---
# <a name="understand-your-use-cases"></a>Grundlegendes zu Ihren Anwendungsfällen

Im gemeinsamen sozialen Rahmen von Teams gibt es eine Vielzahl von Nutzeranforderungen, die Sie mit einer Teams-App lösen können. Zum Beispiel ist eine App, die eine Lücke in der effektiven Zusammenarbeit überbrückt, eine hervorragende Lösung.

Der App-Benutzer und die Anforderungen an seine App sind die grundlegenden Richtlinien, die alle App-Auswahlen bestimmen, die Sie treffen werden. Das Design der App, die Auswahl der Funktionen, die Festlegung der Build- und Testumgebung und die Vermarktung der App richten sich nach den Anforderungen des Benutzers an die App.

Wenn Sie die Benutzeranforderungen mit Ihrer App erfüllen sollen, müssen Sie diese zunächst verstehen.

* **Grundlegendes zum Benutzer**:
  * Erkennen sie Nutzerprobleme und identifizieren Sie die Lösungen für einige häufige Probleme, mit denen die Nutzer konfrontiert sind.
  * Erstellen Sie Ihre Teams-App, indem Sie die richtige Kombination von Teams-Features finden, um die Anforderungen Ihrer Nutzer zu erfüllen.
  * Verstehen Sie Anwendungsfälle, um zu erkennen, wie ein Endbenutzer mit Ihrer Anwendung interagiert.
  * Es wird empfohlen, das Lean-Modul zum [Veröffentlichen Ihrer App im Teams App Store](/training/modules/microsoft-teams-publish-app-to-store/) durchzugehen, um Ihre App beim Bestehen des Microsoft Teams Store-Übermittlungsprozesses zu unterstützen.

* **Verstehen des Problems**: Ermitteln Sie das Kernproblem, das Ihre App lösen muss.

* **Berücksichtigen Sie die Integration**: Identifizieren Sie die Anwendungen und Dienste, die Ihre App benötigt, wie Authentifizierung, Microsoft Graph oder Webanwendungen.

## <a name="microsoft-teams-app-features"></a>Microsoft Teams-App-Features

There are multiple ways to extend Teams so every app is unique. Teams app features offer:

* [App-Funktionen](#app-capabilities)
* [App-Bereich](#app-scope)

### <a name="app-capabilities"></a>App-Funktionen

Fähigkeiten sind die Kernfunktionen, die Sie in Ihre App einbauen können. Sie werden auch als Einstiegs- oder Erweiterungspunkte bezeichnet, da sie Integration und Interaktion ermöglichen.

Ihre Teams-Apps verfügen über eine oder alle der folgenden Kernfunktionen:

:::row:::
   :::column span="":::

#### <a name="personal-apps"></a>Persönliche Apps

Eine [persönliche App](../../concepts/design/personal-apps.md) ist ein bestimmter Bereich oder Bot, der Nutzern hilft, sich auf ihre eigenen Aufgaben zu konzentrieren oder relevante Aktivitäten anzuzeigen.

   :::column-end:::

   :::column span="":::

:::image type="content" source="../../assets/images/overview-personal-apps-2021.png" alt-text="Konzeptionelle Darstellung, wie persönliche Apps im Teams-Client aussehen.":::

   :::column-end:::

:::row-end:::

:::row:::
   :::column span="":::

#### <a name="tabs"></a>Registerkarten

Zeigen Sie Ihre webbasierten Inhalte auf einer [Registerkarte](../../tabs/what-are-tabs.md) an, auf der Personen darüber diskutieren und gemeinsam daran arbeiten können.

   :::column-end:::

   :::column span="":::

:::image type="content" source="../../assets/images/overview-channel-chat-apps-2021.png" alt-text="Konzeptionelle Darstellung, wie Registerkarten im Teams-Client aussehen.":::

   :::column-end:::

:::row-end:::

:::row:::
   :::column span="":::

#### <a name="bots"></a>Bots

Gespräche führen oft zu der Notwendigkeit, etwas zu tun (eine Bestellung zu erstellen, Code zu überprüfen, den Ticketstatus zu kontrollieren usw.). Ein [Bot](../../bots/what-are-bots.md) kann diese Arten von Workflows direkt in Teams starten.

   :::column-end:::

   :::column span="":::

:::image type="content" source="../../assets/images/overview-bots-2021.png" alt-text="Konzeptionelle Darstellung, wie Bots im Teams-Client aussehen.":::

   :::column-end:::

:::row-end:::

:::row:::

   :::column span="":::

#### <a name="message-extensions"></a>Nachrichtenerweiterungen

Mit [Nachrichtenerweiterungen](../../messaging-extensions/what-are-messaging-extensions.md) können Sie externe Informationen durchsuchen und freigeben. Sie können auch auf eine Nachricht reagieren, z. B. durch das Erstellen eines Hilfetickets basierend auf dem Inhalt eines Kanalbeitrags.

   :::column-end:::

   :::column span="":::

:::image type="content" source="../../assets/images/overview-messaging-extensions-2021.png" alt-text="Konzeptionelle Darstellung, wie Nachrichtenerweiterungen im Teams-Client aussehen.":::

   :::column-end:::
:::row-end:::

:::row:::

   :::column span="":::

#### <a name="meeting-extensions"></a>Besprechungserweiterungen

Es gibt einige Möglichkeiten,[Ihre App in die Teams-Anrufe einzubinden](../../apps-in-teams-meetings/design/designing-apps-in-meetings.md).

   :::column-end:::

   :::column span="":::

:::image type="content" source="../../assets/images/overview-meeting-extensions-2021.png" alt-text="Konzeptionelle Darstellung, wie Besprechungserweiterungen im Teams-Client aussehen.":::

   :::column-end:::
:::row-end:::

:::row:::

   :::column span="":::

#### <a name="webhooks-and-connectors"></a>Webhooks und Connectors

[Eingehende Webhooks](../../webhooks-and-connectors/what-are-webhooks-and-connectors.md#incoming-webhooks) sind eine einfache Möglichkeit, automatisch Benachrichtigungen von einer anderen App an einen Teams-Kanal zu senden. Mit [ausgehenden Webhooks](../../webhooks-and-connectors/what-are-webhooks-and-connectors.md#outgoing-webhooks)können Sie Ihrem Webdienst eine Nachricht mit einem @mention senden.

   :::column-end:::

   :::column span="":::

:::image type="content" source="../../assets/images/overview-connectors.png" alt-text="Konzeptionelle Darstellung, wie Connectors im Teams-Client aussehen.":::

   :::column-end:::
:::row-end:::

:::row:::

   :::column span="":::

#### <a name="microsoft-graph-for-teams"></a>Microsoft Graph für Teams

Der [Microsoft Graph-API für Teams](/graph/teams-concept-overview) bietet Zugriff auf Informationen zu Teams, Kanälen, Benutzern und Nachrichten, die Ihnen helfen, Features für Ihre App zu erstellen oder zu verbessern.

   :::column-end:::

   :::column span="":::

:::image type="content" source="../../assets/images/overview-graph.png" alt-text="Konzeptionelle Darstellung der Microsoft Graph-API für Teams.":::

   :::column-end:::
:::row-end:::

> [!NOTE]
> Teams Store hat sich weiterentwickelt:
>
> Zuvor wurden die BRANCHEN-Apps durch Auswahl der Ellipsen auf der Kachel aktualisiert. Mit der aktualisierten Teams Store-Oberfläche können Sie jetzt die branchenspezifischen Apps aktualisieren, indem Sie sich beim [Teams Admin Center](https://admin.teams.microsoft.com)anmelden.

### <a name="app-scope"></a>App-Bereich

Ihre App kann einen der folgenden Bereiche aufweisen:

* **Persönliche App-Benutzeroberfläche**: Eine persönliche App ist ein bestimmter Bereich oder Bot, der Nutzern hilft, sich auf ihre eigenen Aufgaben zu konzentrieren oder für sie wichtige Aktivitäten anzuzeigen.
* **Gemeinsame App-Erfahrung**: Team, Kanal und Chat sind Bereiche für die Zusammenarbeit. Apps in diesen Kontexten sind für alle Nutzer in diesem Bereich verfügbar. Zusammenarbeitsbereiche konzentrieren sich in der Regel auf Workflows für die Interaktionen Ihrer App oder das Freischalten neuer sozialer Interaktionen.

Eine App kann über verschiedene Bereiche hinweg vorhanden sein. Beispiel:

* Ihre App kann Daten an einem zentralen freigegebenen Speicherort anzeigen, d. h. auf einer Registerkarte.
* Sie kann dieselben Informationen auch über eine persönliche Konversationsschnittstelle, d. h. einen Bot, darstellen.

Ein Nutzer kann mit einer App auf einer Canvas-Registerkarte interagieren, um eine Aktivität auszuführen, oder er kann dies mithilfe eines Konversationsbots tun.

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Zuordnen Ihrer Anwendungsfälle](../../concepts/design/map-use-cases.md)

## <a name="see-also"></a>Siehe auch

[Integrieren von Gerätefunktionen](~/concepts/device-capabilities/device-capabilities-overview.md)
