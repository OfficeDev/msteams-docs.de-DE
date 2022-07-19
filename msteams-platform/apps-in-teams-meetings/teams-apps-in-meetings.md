---
title: Apps für Teams-Besprechungen
author: surbhigupta
description: In diesem Artikel erfahren Sie, wie Apps in Microsoft Teams-Besprechungen basierend auf Teilnehmer- und Benutzerrolle und App-Erweiterbarkeit funktionieren.
ms.topic: overview
ms.author: lajanuar
ms.localizationpriority: medium
ms.date: 04/07/2022
ms.openlocfilehash: 97dcb7076797531b510b323e5d7671a8afed0961
ms.sourcegitcommit: 79d525c0be309200e930cdd942bc2c753d0b718c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/19/2022
ms.locfileid: "66841890"
---
# <a name="apps-for-teams-meetings-and-calls"></a>Apps für Teams-Besprechungen und -Anrufe

Besprechungen ermöglichen Zusammenarbeit, Partnerschaft, informierte Kommunikation und geteiltes Feedback. Die Besprechungs-App kann eine Benutzererfahrung für jede Phase des Besprechungslebenszyklus bereitstellen. Der Besprechungslebenszyklus umfasst die App-Erfahrung vor der Besprechung, während der Besprechung und nach der Besprechung, abhängig vom Status des Teilnehmers.

> [!Note]
>
> Apps für Sofortbesprechungen, Einzel- und Gruppenanrufe sind derzeit nur in der [öffentlichen Entwicklervorschau](~/resources/dev-preview/developer-preview-intro.md) verfügbar.

Teams unterstützt den Zugriff auf Apps während der Besprechung für die folgenden Besprechungstypen:

* [**Geplante Besprechungen**](https://support.microsoft.com/office/schedule-a-meeting-in-teams-943507a9-8583-4c58-b5d2-8ec8265e04e5#ID0EFBD=Desktop): Besprechungen, die über den Teams-Kalender geplant sind.
* [**Einzelanrufe**](https://support.microsoft.com/office/start-a-call-from-a-chat-in-teams-f5138c9d-df4c-43d8-9cf6-53400c1a7798): Anrufe, die in einem Einzelchat initiiert wurden.
* [**Gruppenanrufe**](https://support.microsoft.com/office/start-a-call-from-a-chat-in-teams-f5138c9d-df4c-43d8-9cf6-53400c1a7798): Anrufe, die im Gruppenchat initiiert wurden.
* [**Sofortbesprechungen: Besprechungen**](https://support.microsoft.com/office/start-an-instant-meeting-in-teams-ff95e53f-8231-4739-87fa-00b9723f4ef5), die über die Schaltfläche " **Jetzt besprechen** " im Teams-Kalender initiiert wurden.

Benutzer können der Besprechung Apps hinzufügen, indem sie die **+** Option aus ihrem Teams-Besprechungsfenster verwenden.

:::image type="content" source="../assets/images/apps-in-meetings/add-app.png" alt-text="Hinzufügen einer App in einer Besprechung" border="true":::

Besuchen Sie den [Teams-Store](https://go.microsoft.com/fwlink/p/?LinkID=2183121) , und erkunden Sie Apps, die speziell für Besprechungen entwickelt wurden.

> [!Note]
>
> * Derzeit wird das Hinzufügen einer App auf Mobilgeräten nicht unterstützt. Ein Benutzer kann die App jedoch anzeigen und die App von mobilgeräten aus für die Stufe freigeben.
>
> * Wenn derzeit eine dritte Person zu einem 1:1-Anruf hinzugefügt wird, wird der Anruf zu einem Gruppenanruf erhöht, was bedeutet, dass eine neue Sitzung gestartet wird. Apps, die dem 1:1-Anruf hinzugefügt wurden, sind im Gruppenanruf nicht verfügbar. Sie können jedoch erneut hinzugefügt werden.
>
> * Derzeit werden App-Oberflächen in Teams-Kanalbesprechungen (sowohl geplante Besprechungen als auch Sofortbesprechungen) nicht unterstützt.

Die folgende Abbildung vermittelt eine Vorstellung von den Erweiterungsmöglichkeiten der Besprechungs-App:

![Erweiterbarkeit der Besprechungs-App](../assets/images/apps-in-meetings/meetingappextensibility.png)

Dieser Artikel bietet eine Übersicht über die Erweiterungsmöglichkeiten der Besprechungs-App, API-Verweise, das Aktivieren und Konfigurieren von Apps für Besprechungen und benutzerdefinierte Zusammen-Modus-Szenen in Microsoft Teams.

Verbessern Sie Ihre Besprechungserfahrung mithilfe des Features zur Besprechungserweiterung. Mit diesem Feature können Sie Ihre Apps in Besprechungen integrieren. Es umfasst auch verschiedene Freigabefenster eines Besprechungslebenszyklus, in denen Sie Registerkarten, Bots und Messaging-Erweiterungen integrieren können. Sie können verschiedene Teilnehmerrollen und Benutzertypen angeben, Besprechungsereignisse abrufen und In-Meeting-Dialogfenster generieren.

Um Microsoft Teams mit Apps für Besprechungen anzupassen, aktivieren Sie Ihre Apps für Microsoft Teams-Besprechungen, indem Sie das App-Manifest aktualisieren und die Apps auch für Besprechungsszenarien konfigurieren.

Mit dem neuen benutzerdefinierten Feature "Zusammen-Modus-Szenen" können Benutzer an einer Besprechung mit ihrem Team an einem zentralen Ort zusammenarbeiten.

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Einheitliche Besprechungs-Apps](meeting-app-extensibility.md)

## <a name="see-also"></a>Siehe auch

* [Entwerfen eigener Microsoft Teams-Messaging-Erweiterungen](~/apps-in-teams-meetings/design/designing-apps-in-meetings.md)
* [API-Referenzen für Besprechungs-Apps – Microsoft Teams](~/apps-in-teams-meetings/api-references.md)
* [Benutzerdefinierte Zusammen-Modus-Szenen](~/apps-in-teams-meetings/teams-together-mode.md)
* [Aktivieren und Konfigurieren Ihrer Apps für Microsoft Teams-Besprechungen](~/apps-in-teams-meetings/enable-and-configure-your-app-for-teams-meetings.md)
* [Der Besprechungslebenszyklus](meeting-app-extensibility.md#meeting-lifecycle)
* [Verbesserte Zusammenarbeit mit Live Share SDK](teams-live-share-overview.md)
