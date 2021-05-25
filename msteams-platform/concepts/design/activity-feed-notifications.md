---
title: Entwerfen von Aktivitätsfeedbenachrichtigungen
author: heath-hamilton
description: Erfahren Sie, wie Sie Aktivitätsfeedbenachrichtigungen für Ihre Teams entwerfen und das Microsoft Teams UI Kit erhalten.
localization_priority: Normal
ms.author: surbhigupta
ms.topic: reference
ms.openlocfilehash: 61a2a6da2a5ed0cb3126b9798094b06c575c9b6c
ms.sourcegitcommit: e1fe46c574cec378319814f8213209ad3063b2c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2021
ms.locfileid: "52631290"
---
# <a name="designing-activity-feed-notifications-for-your-microsoft-teams-app"></a>Entwerfen von Aktivitätsfeedbenachrichtigungen für Microsoft Teams App

Der Aktivitätsfeed ist eine Oberfläche, auf die Benutzer auf ihre Benachrichtigungen in Microsoft Teams. Der Feed behält Benachrichtigungen aus den letzten vier Wochen bei.

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/activity-feed/desktop-overview.png" alt-text="Beispiel zeigt eine App-Benachrichtigung, die im Teams angezeigt wird." border="false":::

# <a name="mobile"></a>[Mobil](#tab/mobile)

:::image type="content" source="../../assets/images/activity-feed/mobile-overview.png" alt-text="Beispiel zeigt eine App-Benachrichtigung, die im Teams-Aktivitätsfeed auf Mobilgeräten angezeigt wird." border="false":::

---

## <a name="anatomy"></a>Anatomie

:::image type="content" source="../../assets/images/activity-feed/activity-feed-card-anatomy.png" alt-text="Designanatomie der Teams Aktivitätsfeedbenachrichtigung." border="false":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|1|**Avatar**: Zeigt an, wer die Aktivität initiiert hat.|
|2|**Aktivitätstyp/App-Symbol**: Zeigt den Aktivitätstyp an. Bei App-Benachrichtigungen wird das Liniensymbol durch ein App-Symbol ersetzt.|
|3|**Titel (erste Zeile): Actor + Grund**: *Actor*: Name des Benutzers oder der App, der die Aktivität initiiert hat. *Grund*: Beschreibt die Aktivität.|
|4 |**Zeitstempel**: Zeigt an, wann die Aktivität passiert ist.|
|5 |**Position (zweite Zeile):** Zeigt an, wo die Aktivität in der Teams.|
|6 |**Tertiäre Informationen (dritte Zeile):** Optional. Zeigt Vorschautext oder zusätzliche Informationen an.|

## <a name="types-of-activity-feed-notification-cards"></a>Typen von Aktivitätsfeedbenachrichtigungskarten

Die folgenden Varianten zeigen die Arten von Aktivitätsfeedbenachrichtigungskarten, die Sie anzeigen können. Das App-Logo ersetzt den Benutzer-Avatar für app-generierte Benachrichtigungen.

:::image type="content" source="../../assets/images/activity-feed/activity-feed-card-types.png" alt-text="Varianten Teams Aktivitätsfeedkarten." border="false":::

## <a name="manage-activity-feed-notifications"></a>Verwalten von Aktivitätsfeedbenachrichtigungen

Benutzer können Benachrichtigungen, die von Ihrer App gesendet werden, auf der Seite Teams verwalten.

## <a name="related-system-notifications"></a>Verwandte Systembenachrichtigungen

Jede Aktivität generiert eine Systembenachrichtigung. Was angezeigt wird, hängt davon ab, was der Benutzer in seinen Benachrichtigungseinstellungen konfiguriert. Benutzer können auch eine Benachrichtigungsart basierend auf ihrem Betriebssystem auswählen.

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/activity-feed/related-system-notifications.png" alt-text="Varianten von Teams Aktivitätskarten auf verschiedenen Betriebssystemen." border="false":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|1|Teams benutzerdefinierte|
|2|Windows|
|3|Mac|

# <a name="mobile"></a>[Mobil](#tab/mobile)

:::image type="content" source="../../assets/images/activity-feed/mobile-related-system-notifications.png" alt-text="Varianten Teams Aktivitätsfeedkarten unter Android und iOS." border="false":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|1|Android|
|2|iOS|

---

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Implementieren von Aktivitätsfeedbenachrichtigungen](/graph/teams-send-activityfeednotifications)
