---
title: Apps für Teams-Besprechungen
author: surbhigupta
description: In diesem Artikel erfahren Sie, wie Apps in Microsoft Teams-Besprechungen basierend auf Teilnehmer- und Benutzerrolle und App-Erweiterbarkeit funktionieren.
ms.topic: overview
ms.author: lajanuar
ms.localizationpriority: medium
ms.date: 04/07/2022
ms.openlocfilehash: 86cccc05a2c22cd337ae696d232c09c52728523c
ms.sourcegitcommit: 20070f1708422d800d7b1d84b85cbce264616ead
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2022
ms.locfileid: "68537528"
---
# <a name="apps-for-teams-meetings-and-calls"></a>Apps für Teams-Besprechungen und -Anrufe

Besprechungen ermöglichen Zusammenarbeit, Partnerschaft, informierte Kommunikation und geteiltes Feedback. Die Besprechungs-App kann eine Benutzererfahrung für jede Phase des Besprechungslebenszyklus bereitstellen. Der Besprechungslebenszyklus umfasst die App-Erfahrung vor der Besprechung, während der Besprechung und nach der Besprechung, abhängig vom Status des Teilnehmers.

> [!NOTE]
>
> Apps für Sofortbesprechungen, geplante Besprechungen im öffentlichen Kanal, Einzel- und Gruppenanrufe sind derzeit nur in der [öffentlichen Entwicklervorschau](../resources/dev-preview/developer-preview-intro.md) verfügbar.

Teams unterstützt den Zugriff auf Apps während der Besprechung für die folgenden Besprechungstypen:

* [**Geplante Besprechungen**](https://support.microsoft.com/office/schedule-a-meeting-in-teams-943507a9-8583-4c58-b5d2-8ec8265e04e5#ID0EFBD=Desktop): Besprechungen, die über den Teams-Kalender geplant sind.
* [**Geplante Kanalbesprechungen: Besprechungen**](https://support.microsoft.com/office/schedule-a-meeting-in-teams-943507a9-8583-4c58-b5d2-8ec8265e04e5#ID0EFBD=Desktop), die über öffentliche Teams-Kanäle geplant sind.
* [**Einzelanrufe**](https://support.microsoft.com/office/start-a-call-from-a-chat-in-teams-f5138c9d-df4c-43d8-9cf6-53400c1a7798): Anrufe, die in einem Einzelchat initiiert wurden.
* [**Gruppenanrufe**](https://support.microsoft.com/office/start-a-call-from-a-chat-in-teams-f5138c9d-df4c-43d8-9cf6-53400c1a7798): Anrufe, die im Gruppenchat initiiert wurden.
* [**Sofortbesprechungen: Besprechungen**](https://support.microsoft.com/office/start-an-instant-meeting-in-teams-ff95e53f-8231-4739-87fa-00b9723f4ef5), die über die Schaltfläche " **Jetzt besprechen** " im Teams-Kalender initiiert wurden.

Benutzer können der Besprechung Apps hinzufügen, indem sie die **+** Option aus ihrem Teams-Besprechungsfenster verwenden.

:::image type="content" source="../assets/images/apps-in-meetings/add-app.png" alt-text="Hinzufügen einer App in einer Besprechung" border="true":::

Besuchen Sie den [Teams-Store](https://go.microsoft.com/fwlink/p/?LinkID=2183121) , und erkunden Sie Apps, die speziell für Besprechungen entwickelt wurden.

> [!NOTE]
>
> * Wenn derzeit eine dritte Person zu einem 1:1-Anruf hinzugefügt wird, wird der Anruf zu einem Gruppenanruf erhöht, was bedeutet, dass eine neue Sitzung gestartet wird. Apps, die dem 1:1-Anruf hinzugefügt wurden, sind im Gruppenanruf nicht verfügbar. Sie können jedoch erneut hinzugefügt werden.
>
> * Derzeit werden App-Erfahrungen in Teams-Sofortkanalbesprechungen nicht unterstützt.

Die folgende Abbildung vermittelt eine Vorstellung von den Erweiterungsmöglichkeiten der Besprechungs-App:

![Erweiterbarkeit der Besprechungs-App](../assets/images/apps-in-meetings/meetingappextensibility.png)

Dieser Artikel bietet eine Übersicht über die Erweiterungsmöglichkeiten der Besprechungs-App, API-Verweise, das Aktivieren und Konfigurieren von Apps für Besprechungen und benutzerdefinierte Zusammen-Modus-Szenen in Microsoft Teams.

> [!NOTE]
>
> Besprechungs-Apps (Randbereich, Besprechungsphase) werden im Teams-Desktopclient unterstützt. Wo wie im Teams-Webclient wird es nur unterstützt, wenn die Entwicklervorschau aktiviert ist.

* **Erweitern der Besprechungs-App**: Verbessern Sie Ihre Besprechungserfahrung mithilfe der Besprechungserweiterungsfunktion. Mit diesem Feature können Sie Ihre Apps in Besprechungen integrieren. Es umfasst auch verschiedene Freigabefenster eines Besprechungslebenszyklus, in denen Sie Registerkarten, Bots und Messaging-Erweiterungen integrieren können. Sie können verschiedene Teilnehmerrollen und Benutzertypen angeben, Besprechungsereignisse abrufen und In-Meeting-Dialogfenster generieren.
* **Konfigurieren von Apps für Besprechungen**: Um Teams mit Apps für Besprechungen anzupassen, aktivieren Sie Ihre Apps für Teams-Besprechungen, indem Sie das App-Manifest aktualisieren und die Apps auch für Besprechungsszenarien konfigurieren.
* **Anpassen mit Zusammen-Modus-Szenen**: Das neue benutzerdefinierte Feature "Zusammen-Modus-Szenen" ermöglicht Benutzern die Zusammenarbeit an einer Besprechung mit ihrem Team an einer zentralen Stelle.
* **Anpassen der App-Berechtigung im freigegebenen Kanal**: Wenn Ihre App wichtige Informationen im freigegebenen Kanal freigibt, können Sie die App-Berechtigung für externe Mitglieder anpassen. App-Berechtigungen in [freigegebenen Kanälen](../concepts/build-and-test/Shared-channels.md) folgen der App-Liste des Hostteams und der App-Richtlinie des Hostmandanten.
* **Abrufen von Besprechungsaufzeichnungen**: Sie können in einem Szenario nach der Besprechung auf Besprechungstranskripte zugreifen und diese abrufen. Konfigurieren Sie Ihre App so, dass Transkriptionen automatisch für eine geplante Besprechung abgerufen werden, und verwenden Sie sie für Einblicke, intelligente Analysen und vieles mehr.
* **Generieren Sie einen Deep-Link, um Inhalte für die Phase in Besprechungen freizugeben**: Sie können einen Deep-Link generieren, um die App für das Bereitstellen und Starten oder Teilnehmen an einer Besprechung freizugeben.

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
