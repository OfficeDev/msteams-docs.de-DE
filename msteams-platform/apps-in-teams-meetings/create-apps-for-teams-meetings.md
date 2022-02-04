---
title: Voraussetzungen für Apps in Teams-Besprechungen
author: surbhigupta
description: Identifizieren von Voraussetzungen mit Apps für Teams Besprechungen
ms.topic: conceptual
ms.author: lajanuar
ms.localizationpriority: medium
keywords: Teams-Apps – Benutzerteilnehmer-Rollen-API für Besprechungen
ms.openlocfilehash: 4c42a66f7891691b8c53d61d1ce637d57048eae8
ms.sourcegitcommit: 54f6690b559beedc330b971618e574d33d69e8a8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2022
ms.locfileid: "62362739"
---
# <a name="prerequisites-for-apps-in-teams-meetings"></a>Voraussetzungen für Apps in Teams-Besprechungen

Mit Apps für Teams Besprechungen können Sie die Funktionen Ihrer Apps über den gesamten Besprechungslebenszyklus erweitern. Bevor Sie mit Apps für Teams Besprechungen arbeiten, müssen Sie die folgenden Voraussetzungen erfüllen:

* Erfahren Sie, wie Sie Teams-Apps entwickeln. Weitere Informationen zum Entwickeln Teams App finden Sie unter [Teams App-Entwicklung](../overview.md).

* Aktualisieren Sie das Teams App-Manifest, um anzugeben, dass die App für Besprechungen verfügbar ist. Weitere Informationen finden Sie unter [App-Manifest](enable-and-configure-your-app-for-teams-meetings.md#update-your-app-manifest).

* Verwenden Sie Ihre App, die konfigurierbare Registerkarten im Gruppenchatbereich unterstützt. Weitere Informationen finden Sie unter [Gruppenchatbereich](../resources/schema/manifest-schema.md#configurabletabs) und [Erstellen einer Gruppenregisterkarte](../build-your-first-app/build-channel-tab.md).

* Halten Sie sich an allgemeine Teams Entwurfsrichtlinien für Registerkarten für Szenarien vor und nach der Besprechung. Informationen zu Erfahrungen während Besprechungen finden Sie auf der Registerkarte "Besprechung" und in den Entwurfsrichtlinien des Dialogfelds "In-Meeting". Weitere Informationen finden Sie unter [Teams Entwurfsrichtlinien für Registerkarten](../tabs/design/tabs.md), [Entwurfsrichtlinien für Registerkarten in Besprechungen](../apps-in-teams-meetings/design/designing-apps-in-meetings.md#use-an-in-meeting-tab) und [Entwurfsrichtlinien für Dialogfelder in Besprechungen](../apps-in-teams-meetings/design/designing-apps-in-meetings.md#use-an-in-meeting-dialog).

* Unterstützen Sie den `groupchat` Bereich, um Ihre App in Chats vor und nach der Besprechung zu aktivieren. Mit der App-Erfahrung vor der Besprechung können Sie Besprechungs-Apps suchen und hinzufügen und die Aufgaben vor der Besprechung ausführen. Mit der App-Erfahrung nach der Besprechung können Sie die Ergebnisse der Besprechung anzeigen, z. B. Umfrageergebnisse oder Gebühren.
* Die URL-Parameter der Besprechungs-API müssen `meetingId`über , `userId`und `tenantId`verfügen. Die Parameter sind als Teil der Teams Client SDK- und Bot-Aktivität verfügbar. Sie können auch zuverlässige Informationen zu Benutzer-ID und Mandanten-ID mithilfe der [SSO-Authentifizierung der Registerkarte](../tabs/how-to/authentication/auth-aad-sso.md) abrufen.

* Die `GetParticipant` API muss über eine Bot-Registrierung und -ID verfügen, um Authentifizierungstoken zu generieren. Weitere Informationen finden Sie unter [Bot-Registrierung und -ID](../build-your-first-app/build-bot.md).

* Damit Ihre App in Echtzeit aktualisiert werden kann, muss sie basierend auf den Ereignisaktivitäten in der Besprechung auf dem neuesten Stand sein. Diese Ereignisse können sich innerhalb des Besprechungsdialogfelds und in anderen Phasen des Besprechungslebenszyklus befinden. Das Dialogfeld in besprechungsinternen Besprechungen finden Sie unter Abschlussparameter `bot Id` in der `NotificationSignal` API.

* Die `Meeting Details` API muss über eine Bot-Registrierung und Bot-ID verfügen. Es erfordert Bot SDK, um .`TurnContext` Um die Besprechungsdetails-API zu verwenden, müssen Sie unterschiedliche RSC-Berechtigungen basierend auf dem Umfang einer Besprechung abrufen, z. B. private Besprechungen oder Kanalbesprechung.

* Bei Echtzeitbesprechungsereignissen müssen Sie mit dem objekt vertraut sein, das `TurnContext` über das Bot SDK verfügbar ist. Das `Activity` Objekt enthält `TurnContext` die Nutzlast mit der tatsächlichen Start- und Endzeit. Echtzeitbesprechungsereignisse erfordern eine registrierte Bot-ID von der Teams-Plattform. Der Bot kann das Start- oder Endereignis der Besprechung automatisch empfangen, indem er es im Manifest hinzufügt `ChannelMeeting.ReadBasic.Group` .

* `meetingId``userId`Parameter haben und `tenantId` in besprechungs-API-URL. Die Parameter sind als Teil der Teams Client SDK- und Bot-Aktivität verfügbar. Sie können auch zuverlässige Informationen zu Benutzer-ID und Mandanten-ID mithilfe der [SSO-Authentifizierung der Registerkarte](../tabs/how-to/authentication/auth-aad-sso.md) abrufen.

* Besitzen Sie eine Bot-Registrierung und -ID in der `GetParticipant` API, um Authentifizierungstoken zu generieren. Weitere Informationen finden Sie unter [Bot-Registrierung und -ID](../build-your-first-app/build-bot.md).

* Halten Sie Ihre App basierend auf Denkaktivitäten in der Besprechung auf dem neuesten Stand. Diese Ereignisse können sich innerhalb des Besprechungsdialogfelds und in anderen Phasen des Besprechungslebenszyklus befinden. Aktivieren Sie für das Dialogfeld in der Besprechung den Abschlussparameter `bot Id` in `NotificationSignal` der API.

* Besitzen Sie eine Bot-Registrierung und Bot-ID in der `MeetingDetails` API. Es erfordert Bot SDK, um .`TurnContext`

* Machen Sie sich mit dem `TurnContext` über das Bot SDK verfügbaren Objekt vertraut. Das `Activity` Objekt enthält `TurnContext` die Nutzlast mit der tatsächlichen Start- und Endzeit. Echtzeitbesprechungsereignisse erfordern eine registrierte Bot-ID von der Teams-Plattform.

Nachdem Sie die Voraussetzungen erfüllt haben, können Sie die API-Referenzen `GetUserContext``GetParticipant``NotificationSignal`für Besprechungs-Apps verwenden, die `Meeting Details` Ihnen den Zugriff auf Informationen mithilfe von Attributen und das Anzeigen relevanter Inhalte ermöglichen.

> [!NOTE]
> Teams JavaScript SDK (_Version_: 1.10 und höher) für SSO, um im Besprechungsseitigen Bereich zu arbeiten.

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Aktivieren und Konfigurieren Ihrer Apps für Teams Besprechungen](enable-and-configure-your-app-for-teams-meetings.md)

## <a name="see-also"></a>Siehe auch

* [Entwurfsrichtlinien für Besprechungsdialoge](design/designing-apps-in-meetings.md#use-an-in-meeting-dialog)
* [Teams Authentifizierungsfluss für Registerkarten](../tabs/how-to/authentication/auth-flow-tab.md)
* [Apps für Teams-Besprechungen](teams-apps-in-meetings.md)
* [Teams Bot-API-Änderungen zum Abrufen von Team- oder Chatmitgliedern](~/resources/team-chat-member-api-changes.md)
