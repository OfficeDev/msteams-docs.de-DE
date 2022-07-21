---
title: Entwerfen von Aktivitätsfeed-Benachrichtigungen
author: heath-hamilton
description: 'Erfahren Sie, wie Sie Aktivitätsfeedbenachrichtigungen für Ihre Teams-App entwerfen und das Teams UI Kit erhalten. Entwickeln von Benachrichtigungen aus dem Teams-Kanal in Visual Studio C #'
ms.localizationpriority: medium
ms.author: surbhigupta
ms.topic: reference
ms.openlocfilehash: 9a17027f7dd68993a118f24bb23cfff0a56651e1
ms.sourcegitcommit: 4ba6392eced76ba6baeb6d6dd9ba426ebf4ab24f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/21/2022
ms.locfileid: "66919767"
---
# <a name="designing-activity-feed-notifications-for-your-microsoft-teams-app"></a>Entwerfen von Aktivitätsfeedbenachrichtigungen für Ihre Microsoft Teams-App

Der Aktivitätsfeed ist eine Oberfläche, auf die Benutzer in Microsoft Teams auf ihre Benachrichtigungen zugreifen können. Der Feed behält Benachrichtigungen aus den letzten vier Wochen bei.

# <a name="mobile"></a>[Mobil](#tab/mobile)

:::image type="content" source="../../assets/images/activity-feed/mobile-overview.png" alt-text="Das Beispiel zeigt eine App-Benachrichtigung, die im Teams-Aktivitätsfeed auf mobilgeräten angezeigt wird.":::

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/activity-feed/desktop-overview.png" alt-text="Das Beispiel zeigt eine App-Benachrichtigung, die im Teams-Aktivitätsfeed angezeigt wird.":::

---

## <a name="anatomy"></a>Anatomie

:::image type="content" source="../../assets/images/activity-feed/activity-feed-card-anatomy.png" alt-text="Entwerfen Sie die Anatomie der Teams-Aktivitätsfeedbenachrichtigung.":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|1|**Avatar**: Zeigt, wer die Aktivität initiiert hat.|
|2|**Aktivitätstyp-/App-Symbol**: Zeigt den Aktivitätstyp an. Bei App-Benachrichtigungen wird das Liniensymbol durch ein App-Symbol ersetzt.|
|3|**Titel (erste Zeile): Akteur + Grund**: *Akteur*: Name des Benutzers oder der App, der die Aktivität initiiert hat. *Grund*: Beschreibt die Aktivität.|
|4|**Zeitstempel**: Zeigt an, wann die Aktivität stattgefunden hat.|
|5|**Ort (zweite Zeile):** Zeigt an, wo die Aktivität in Teams stattgefunden hat.|
|6|**Textvorschau (dritte Zeile):** Zeigt eine abgeschnittene Zeile vom Anfang der Benachrichtigung an.|

## <a name="types-of-activity-feed-notification-cards"></a>Arten von Aktivitätsfeed-Benachrichtigungskarten

Die folgenden Varianten zeigen die Arten von Aktivitätsfeedbenachrichtigungskarten, die Sie anzeigen können. Das App-Logo ersetzt den Benutzer-Avatar für von der App generierte Benachrichtigungen.

:::image type="content" source="../../assets/images/activity-feed/activity-feed-card-types.png" alt-text="Varianten von Teams-Aktivitätsfeedkarten.":::

## <a name="manage-activity-feed-notifications"></a>Verwalten von Aktivitätsfeedbenachrichtigungen

Benutzer können Benachrichtigungen verwalten, die von Ihrer App auf der Seite "Teams-Einstellungen" gesendet werden.

## <a name="related-system-notifications"></a>Verwandte Systembenachrichtigungen

Jede Aktivität generiert eine Systembenachrichtigung. Was angezeigt wird, hängt davon ab, was der Benutzer in den Benachrichtigungseinstellungen konfiguriert. Benutzer können auch einen Benachrichtigungsstil basierend auf ihrem Betriebssystem auswählen.

# <a name="mobile"></a>[Mobil](#tab/mobile)

:::image type="content" source="../../assets/images/activity-feed/mobile-related-system-notifications.png" alt-text="Varianten von Teams-Aktivitätsfeedkarten unter Android und iOS.":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|1|Android|
|2|iOS|

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/activity-feed/related-system-notifications.png" alt-text="Varianten von Teams-Aktivitätskarten unter verschiedenen Betriebssystemen.":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|1|Teams benutzerdefiniert|
|2|Windows|
|3|Mac|

---

## <a name="step-by-step-guide"></a>Schrittweise Anleitung

Befolgen Sie die [schrittweise Anleitung zum Senden von Aktivitätsfeedbenachrichtigungen](../../sbs-graphactivity-feedbroadcast.yml) in Teams.

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Implementieren von Aktivitätsfeedbenachrichtigungen](/graph/teams-send-activityfeednotifications)
