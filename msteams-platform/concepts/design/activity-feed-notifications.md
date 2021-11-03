---
title: Entwerfen von Aktivitätsfeedbenachrichtigungen
author: heath-hamilton
description: Erfahren Sie, wie Sie Aktivitätsfeedbenachrichtigungen für Ihre Teams-App entwerfen und das Microsoft Teams UI Kit abrufen.
ms.localizationpriority: medium
ms.author: surbhigupta
ms.topic: reference
ms.openlocfilehash: d566def261d6fd1177fed46c31466d248c8e5e3b
ms.sourcegitcommit: 22c9e44437720d30c992a4a3626a2a9f745983c1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/03/2021
ms.locfileid: "60719917"
---
# <a name="designing-activity-feed-notifications-for-your-microsoft-teams-app"></a>Entwerfen von Aktivitätsfeedbenachrichtigungen für Ihre Microsoft Teams-App

Der Aktivitätsfeed ist eine Oberfläche, über die Benutzer auf ihre Benachrichtigungen in Microsoft Teams zugreifen können. Der Feed behält Benachrichtigungen aus den letzten vier Wochen bei.

# <a name="mobile"></a>[Mobil](#tab/mobile)

:::image type="content" source="../../assets/images/activity-feed/mobile-overview.png" alt-text="Beispiel zeigt eine App-Benachrichtigung, die im Teams Aktivitätsfeed auf mobilgeräten angezeigt wird." border="false":::

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/activity-feed/desktop-overview.png" alt-text="Beispiel zeigt eine App-Benachrichtigung, die im Teams-Aktivitätsfeed angezeigt wird." border="false":::

---

## <a name="anatomy"></a>Anatomie

:::image type="content" source="../../assets/images/activity-feed/activity-feed-card-anatomy.png" alt-text="Entwerfen Sie die Anatomie der Teams Aktivitätsfeedbenachrichtigung." border="false":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|1|**Avatar**: Zeigt an, wer die Aktivität initiiert hat.|
|2|**Aktivitätstyp/App-Symbol:** Stellt den Aktivitätstyp dar. Bei App-Benachrichtigungen wird das Liniensymbol durch ein App-Symbol ersetzt.|
|3|**Titel (erste Zeile): Akteur + Grund:** *Akteur:* Name des Benutzers oder der App, der die Aktivität initiiert hat. *Grund:* Beschreibt die Aktivität.|
|4 |**Zeitstempel:** Zeigt an, wann die Aktivität stattgefunden hat.|
|5|**Ort (zweite Zeile):** Zeigt an, wo die Aktivität in Teams stattgefunden hat.|
|6 |**Textvorschau (dritte Zeile):** Zeigt eine abgeschnittene Zeile ab dem Anfang der Benachrichtigung an.|

## <a name="types-of-activity-feed-notification-cards"></a>Arten von Aktivitätsfeed-Benachrichtigungskarten

Die folgenden Varianten zeigen die Arten von Aktivitätsfeed-Benachrichtigungskarten, die Sie anzeigen können. Das App-Logo ersetzt den Benutzer-Avatar für von der App generierte Benachrichtigungen.

:::image type="content" source="../../assets/images/activity-feed/activity-feed-card-types.png" alt-text="Varianten von Teams Aktivitätsfeedkarten." border="false":::

## <a name="manage-activity-feed-notifications"></a>Verwalten von Aktivitätsfeedbenachrichtigungen

Benutzer können Benachrichtigungen, die von Ihrer App gesendet werden, auf der Einstellungsseite Teams verwalten.

## <a name="related-system-notifications"></a>Zugehörige Systembenachrichtigungen

Jede Aktivität generiert eine Systembenachrichtigung. Was angezeigt wird, hängt davon ab, was der Benutzer in den Benachrichtigungseinstellungen konfiguriert. Benutzer können auch ein Benachrichtigungsformat basierend auf ihrem Betriebssystem auswählen.

# <a name="mobile"></a>[Mobil](#tab/mobile)

:::image type="content" source="../../assets/images/activity-feed/mobile-related-system-notifications.png" alt-text="Varianten von Teams Aktivitätsfeedkarten unter Android und iOS." border="false":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|1|Android|
|2|iOS|

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/activity-feed/related-system-notifications.png" alt-text="Varianten von Teams Aktivitätskarten auf verschiedenen Betriebssystemen." border="false":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|1|benutzerdefinierte Teams|
|2|Windows|
|3|Mac|

---

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Implementieren von Aktivitätsfeedbenachrichtigungen](/graph/teams-send-activityfeednotifications)
