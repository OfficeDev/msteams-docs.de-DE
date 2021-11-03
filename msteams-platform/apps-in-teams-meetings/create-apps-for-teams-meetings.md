---
title: Voraussetzungen für Apps in Teams-Besprechungen
author: surbhigupta
description: Identifizieren von Voraussetzungen mit Apps für Teams Besprechungen
ms.topic: conceptual
ms.author: lajanuar
ms.localizationpriority: medium
keywords: Teams-Apps – Benutzerteilnehmer-Rollen-API für Besprechungen
ms.openlocfilehash: 9ac6e87a8f85d0e8d73c6bf58dd705a55f887f43
ms.sourcegitcommit: 22c9e44437720d30c992a4a3626a2a9f745983c1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/03/2021
ms.locfileid: "60720232"
---
# <a name="prerequisites-for-apps-in-teams-meetings"></a>Voraussetzungen für Apps in Teams-Besprechungen

Mit Apps für Teams Besprechungen können Sie die Funktionen Ihrer Apps über den gesamten Besprechungslebenszyklus erweitern. Bevor Sie mit Apps für Teams Besprechungen arbeiten, müssen Sie die folgenden Voraussetzungen erfüllen:

* Erfahren Sie, wie Sie Teams-Apps entwickeln. Weitere Informationen zum Entwickeln Teams App finden Sie unter [Teams App-Entwicklung.](../overview.md)

* Aktualisieren Sie das Teams App-Manifest, um anzugeben, dass die App für Besprechungen verfügbar ist. Weitere Informationen finden Sie unter [App-Manifest.](enable-and-configure-your-app-for-teams-meetings.md#update-your-app-manifest)

* Verwenden Sie Ihre App, die konfigurierbare Registerkarten im Gruppenchatbereich unterstützt. Weitere Informationen finden Sie unter [Gruppenchatbereich](../resources/schema/manifest-schema.md#configurabletabs) und [Erstellen einer Gruppenregisterkarte.](../build-your-first-app/build-channel-tab.md)

* Halten Sie sich an allgemeine Teams Entwurfsrichtlinien für Registerkarten für Szenarien vor und nach der Besprechung. Informationen zu Erfahrungen während Besprechungen finden Sie auf der Registerkarte "Besprechung" und in den Entwurfsrichtlinien des Dialogfelds "In-Meeting". Weitere Informationen finden Sie unter [Teams Entwurfsrichtlinien für Registerkarten,](../tabs/design/tabs.md) [Entwurfsrichtlinien für Registerkarten in Besprechungen](../apps-in-teams-meetings/design/designing-apps-in-meetings.md#use-an-in-meeting-tab)und Entwurfsrichtlinien für [Dialogfelder in Besprechungen.](../apps-in-teams-meetings/design/designing-apps-in-meetings.md#use-an-in-meeting-dialog)

* Unterstützen Sie den `groupchat` Bereich, um Ihre App in Chats vor und nach der Besprechung zu aktivieren. Mit der App-Erfahrung vor der Besprechung können Sie Besprechungs-Apps suchen und hinzufügen und die Aufgaben vor der Besprechung ausführen. Mit der App-Erfahrung nach der Besprechung können Sie die Ergebnisse der Besprechung anzeigen, z. B. Umfrageergebnisse oder Gebühren.
* Die URL-Parameter der Besprechungs-API müssen `meetingId` über `userId` , und `tenantId` verfügen. Die Parameter sind als Teil der Teams Client SDK- und Bot-Aktivität verfügbar. Sie können auch zuverlässige Informationen zu Benutzer-ID und Mandanten-ID mithilfe der [SSO-Authentifizierung](../tabs/how-to/authentication/auth-aad-sso.md)der Registerkarte abrufen.

* Die `GetParticipant` API muss über eine Bot-Registrierung und -ID verfügen, um Authentifizierungstoken zu generieren. Weitere Informationen finden Sie unter [Bot-Registrierung und -ID.](../build-your-first-app/build-bot.md)

* Damit Ihre App in Echtzeit aktualisiert werden kann, muss sie basierend auf den Ereignisaktivitäten in der Besprechung auf dem neuesten Stand sein. Diese Ereignisse können sich innerhalb des Besprechungsdialogfelds und in anderen Phasen des Besprechungslebenszyklus befinden. Das Dialogfeld in besprechungsinternen Besprechungen finden Sie unter `bot Id` Abschlussparameter in `NotificationSignal` der API.

* Die `Meeting Details` API muss über eine Bot-Registrierung und Bot-ID verfügen. Es erfordert Bot SDK, um `TurnContext` .

* Bei Echtzeitbesprechungsereignissen müssen Sie mit dem objekt vertraut sein, `TurnContext` das über das Bot SDK verfügbar ist. Das `Activity` Objekt enthält die Nutzlast mit der `TurnContext` tatsächlichen Start- und Endzeit. Besprechungsereignisse in Echtzeit erfordern eine registrierte Bot-ID von der Teams-Plattform.

* Parameter haben `meetingId` `userId` und in `tenantId` besprechungs-API-URL. Die Parameter sind als Teil der Teams Client SDK- und Bot-Aktivität verfügbar. Sie können auch zuverlässige Informationen zu Benutzer-ID und Mandanten-ID mithilfe der [SSO-Authentifizierung](../tabs/how-to/authentication/auth-aad-sso.md)der Registerkarte abrufen.

* Besitzen Sie eine Bot-Registrierung und -ID in der `GetParticipant` API, um Authentifizierungstoken zu generieren. Weitere Informationen finden Sie unter [Bot-Registrierung und -ID.](../build-your-first-app/build-bot.md)

* Halten Sie Ihre App basierend auf Denkaktivitäten in der Besprechung auf dem neuesten Stand. Diese Ereignisse können sich innerhalb des Besprechungsdialogfelds und in anderen Phasen des Besprechungslebenszyklus befinden. Aktivieren Sie für das Dialogfeld in der Besprechung den Abschlussparameter in der `bot Id` `NotificationSignal` API.

* Besitzen Sie eine Bot-Registrierung und Bot-ID in der `MeetingDetails` API. Es erfordert Bot SDK, um `TurnContext` .

* Machen Sie sich mit dem `TurnContext` über das Bot SDK verfügbaren Objekt vertraut. Das `Activity` Objekt enthält die Nutzlast mit der `TurnContext` tatsächlichen Start- und Endzeit. Besprechungsereignisse in Echtzeit erfordern eine registrierte Bot-ID von der Teams-Plattform.

Nachdem Sie die Voraussetzungen erfüllt haben, können Sie die API-Referenzen für Besprechungs-Apps `GetUserContext` `GetParticipant` `NotificationSignal` verwenden, die `Meeting Details` Ihnen den Zugriff auf Informationen mithilfe von Attributen und das Anzeigen relevanter Inhalte ermöglichen.

> [!NOTE]
> Teams JavaScript SDK (_Version:_ 1.10 und höher) für SSO, um im Besprechungsseitenbereich zu arbeiten.

## <a name="see-also"></a>Siehe auch

* [Entwurfsrichtlinien für Besprechungsdialoge](design/designing-apps-in-meetings.md#use-an-in-meeting-dialog)
* [Teams Authentifizierungsfluss für Registerkarten](../tabs/how-to/authentication/auth-flow-tab.md)
* [Apps für Teams Besprechungen](teams-apps-in-meetings.md)

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [API-Referenzen für Besprechungs-Apps](API-references.md)
