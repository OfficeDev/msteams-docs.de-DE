---
title: Apps in Teams-Besprechungen
author: laujan
description: Übersicht über Apps in Teams-Besprechungen basierend auf Teilnehmer- und Benutzerrolle
ms.topic: overview
ms.author: lajanuar
keywords: Rollen-API für Teams-Apps-Besprechungen für Benutzerteilnehmer
ms.openlocfilehash: 51fe2e0ebdaa56197bbebd1e5dbcf90698fb1f92
ms.sourcegitcommit: 23ed7edf145df10dcfba15c43978eae9e0d451a8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2021
ms.locfileid: "50753553"
---
# <a name="apps-in-teams-meetings"></a>Apps in Teams-Besprechungen

Besprechungen sind für die Produktivität in Teams entscheidend. Sie ermöglichen Zusammenarbeit, Partnerschaft, informierte Kommunikation und geteiltes Feedback in einem inklusiven und aktiven Forum. Als Entwickler können Sie konfigurierbare Tab-, [](../messaging-extensions/what-are-messaging-extensions.md) [](../tabs/what-are-tabs.md#how-do-tabs-work) [Bot-](../bots/what-are-bots.md)und Nachrichtenerweiterungsanwendungen erstellen, um eine Teams-Besprechungserfahrung zu verbessern und zu bereichern. Besprechungsbenutzer können über den Registerkartenkatalog auf Apps zugreifen, um relevante Szenarien wie die Vorabbereitstellung eines Kanban-Board, das Starten eines Dialogfelds mit Aktionen in Besprechungen oder das Erstellen einer Umfrage nach der Besprechung zu ermöglichen. Ihre Besprechungs-App kann eine Benutzeroberfläche für jede Phase des Besprechungslebenszyklus basierend auf dem Teilnehmerstatus bereitstellen.

Die Erweiterbarkeit der Besprechungs-App von Teams zentriert sich auf drei Konzepte:

✔ **Besprechungslebenszyklus** – vor, während und nach dem Besprechungszeitrahmen.  
✔ **Teilnehmerrolle** – Besprechungsorganisator, Organisator oder Teilnehmer.  
✔ **Benutzertyp** – Mandanten-, Gast-, Verbund- oder anonymer Teams-Benutzer.

<!-- markdownlint-disable MD001 -->
### <a name="meeting-lifecycle-scenarios"></a>Besprechungslebenszyklusszenarien

## <a name="tabs"></a>Registerkarten

> [!IMPORTANT]
> Wie bei allen Registerkartenanwendungen muss Ihre App den Teams [-SSO-Authentifizierungsfluss](../tabs/how-to/authentication/auth-aad-sso.md) für Registerkarten befolgen.

> [!NOTE]
> * Mobile Clients unterstützen Registerkarten nur in Oberflächen vor besprechungen und nach Besprechungen. Die Besprechungserfahrungen, z. B. das Dialogfeld in besprechungen und das Panel auf Mobilgeräten, werden in Kürze verfügbar sein.
> * Apps werden nur in privaten geplanten Besprechungen unterstützt.

### <a name="pre-meeting-app-experience"></a>App-Erfahrung vor besprechung

**Vorbetreff:**

![Pre-Meeting-Erfahrung](../assets/images/apps-in-meetings/PreMeeting.png)

**Registerkarte "Pre-Meeting":**

![Registerkartenansicht vor der Besprechung](../assets/images/apps-in-meetings/PreMeetingTab.png)

✔ Benutzer mit Berechtigungen können apps zu einer Besprechung über den Registerkartenkatalog auf zwei Arten hinzufügen:

&emsp;&emsp;&#9679; Über die **Registerkarte Details** im Teams-Planungsformular.

&emsp;&emsp;&#9679; Über die Registerkarte **Besprechungschat** in einer vorhandenen Besprechung.</br> </br>

✔ Tab-Apps sind in  **Besprechungsdetails und Chats-Seiten** über eine Plussymbolschaltfläche (➕) zugänglich.|

✔ Tablayout sollte sich in einem organisierten Zustand befinden, wenn mehr als zehn Umfragen oder Umfragen durchgeführt werden.

### <a name="in-meeting-app-experience"></a>In-Meeting-App-Erfahrung

✔ Besprechungs-Apps werden in der oberen Leiste des Chatfensters und als Registerkartenerfahrung in Besprechungen über die Registerkarte In-Meeting gehostet. Wenn Benutzer einer Besprechung über den Registerkartenkatalog eine Registerkarte hinzufügen, werden Apps angezeigt, die sich während der **Besprechungserfahrung** befinden.

✔ Berechtigte Benutzer können Apps während der Besprechung hinzufügen.

✔ Wenn apps im Kontext einer Besprechung geladen werden, können sie das Teams Client SDK nutzen, um auf das zu zugreifen und die Erfahrung entsprechend `meetingId` `userMri` zu `frameContext` rendern.

✔ Exportieren eines Ergebnisses einer Umfrage oder Umfrage sollte die Benutzer mit der Meldung "Ergebnisse erfolgreich heruntergeladen" benachrichtigen.

✔ Damit eine App in einer Teams-Besprechung in zwei Bereichen sichtbar ist:

&emsp;&emsp;&#9679; **Seitenbereich .** </br>

> [!NOTE]
> Wenn Ihr _App-Manifest_ angibt, dass Ihre Registerkarte [für](create-apps-for-teams-meetings.md#during-a-meeting)den Seitenbereich optimiert ist, wird sie dort angezeigt. Sie kann auch Teil einer Share-Tray-Erfahrung sein, die den angegebenen Entwurfsrichtlinien unterliegt.

&emsp;&emsp;&#9679; **In-Meeting-Dialogfeld .** Verwenden Sie das Dialogfeld in der Besprechung, um Inhalte mit Aktionen für Besprechungsteilnehmer anzuzeigen. *Weitere Informationen* [finden Sie unter Erstellen von Apps für Teams-Besprechungen.](create-apps-for-teams-meetings.md)

**In-Meeting-Erfahrung:**

![In-Meeting-Erfahrung](../assets/images/apps-in-meetings/in-meeting-experience.png)

![In-Meeting-Dialog-Ansicht](../assets/images/apps-in-meetings/in-meeting-dialog.png)

**In-Meeting-Dialogfeld mit Aktionen für Benutzer:**

![Dialogansicht](../assets/images/apps-in-meetings/in-meeting-dialog-view.png)

### <a name="post-meeting-app-experience"></a>App-Erfahrung nach der Besprechung

**Nach der Besprechung:**

![Nach besprechungsansicht](../assets/images/apps-in-meetings/PostMeeting.png)

✔ Das App-Szenario nach der Besprechung ähnelt der aktuellen Nachbesprechung mit dem zusätzlichen Vorteil, dass Registerkarten auf der Oberfläche vorhanden sind. 

✔ Berechtigte Benutzer können Apps aus dem Registerkartenkatalog zu einer Besprechung über die  Registerkarte **Details** im Teams-Planungsformular und die Registerkarte Besprechungschat in einer vorhandenen Besprechung hinzufügen.

✔ Tablayout sollte sich in einem organisierten Zustand befinden, wenn mehr als zehn Umfragen oder Umfragen durchgeführt werden.

### <a name="bots"></a>Bots

Beginnen Sie bei der Botimplementierung mit [dem Erstellen eines Bots,](../build-your-first-app/build-bot.md) und fahren Sie dann mit dem Erstellen von Apps [für Teams-Besprechungen fort.](../apps-in-teams-meetings/create-apps-for-teams-meetings.md#meeting-apps-api-reference)

### <a name="messaging-extensions"></a>Messaging-Erweiterungen

Beginnen Sie bei der Implementierung von Messagingerweiterungen mit dem Erstellen einer [Messagingerweiterung,](../messaging-extensions/how-to/create-messaging-extension.md) und fahren Sie dann mit dem Erstellen von [Apps für Teams-Besprechungen fort.](../apps-in-teams-meetings/create-apps-for-teams-meetings.md#meeting-apps-api-reference)

## <a name="participant-roles-and-user-types-in-a-meeting"></a>Teilnehmerrollen und Benutzertypen in einer Besprechung

![Teilnehmer an einer Besprechung](../assets/images/apps-in-meetings/participant-roles.png)

### <a name="participant-roles"></a>Teilnehmerrollen

Sie können Ihre App mit teilnehmerspezifischer Autorisierung entwerfen. Beispielsweise kann nur ein Organisator und/oder Organisator eine Umfrage in Besprechungen erstellen. Obwohl die Standardeinstellungen für Teilnehmer vom IT-Administrator einer Organisation bestimmt werden, kann es sein, dass ein Besprechungsorganisator die Einstellungen für eine bestimmte Besprechung ändern möchte. Organisatoren können diese Änderungen auf der Webseite "Besprechungsoptionen" vornehmen.

1. **Organizer**. Der Organisator plant eine Besprechung, legt die Besprechungsoptionen fest, weist Besprechungsrollen zu und startet die Besprechung. Nur Benutzer mit einem M365-Konto (im Besitz einer Teams-Lizenz) können Organisator sein und Die Teilnehmerberechtigungen steuern.
1. **Presenter**. Organisator haben nahezu dieselben Funktionen wie Organisator. Ein Organisator kann jedoch keinen Organisator aus der Sitzung entfernen oder Besprechungsoptionen für die Sitzung ändern. Standardmäßig haben Teilnehmer, die an einer Besprechung teilnahmen, die Rolle des Moderators.
1. **Attendee**. Ein Teilnehmer ist ein Benutzer, der zur Teilnahme an einer Besprechung eingeladen wurde, der jedoch nicht autorisiert ist, als Moderator zu fungieren. Teilnehmer können mit anderen Besprechungsmitgliedern interagieren, aber keine Besprechungseinstellungen verwalten oder Inhalte freigeben.

_Siehe_ [ **Rollen in einer Teams-Besprechung**](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019)

Sie können wie folgt auf  **die Seite Besprechungsoptionen** zugreifen:

&#11200; In Teams wechseln Sie zu **Kalenderkalenderlogo,** wählen Sie eine Besprechung ![ und dann ](../assets/images/apps-in-meetings/calendar-logo.png) **Besprechungsoptionen aus.**

&#11200; Wählen Sie in einer Besprechungseinladung **Besprechungsoptionen aus.**

&#11200; Wählen Sie während einer Besprechung **das** Symbol Teilnehmer anzeigen ![ in den ](../assets/images/apps-in-meetings/show-participants.png) Besprechungssteuerelementen anzeigen aus. Wählen Sie dann oberhalb der Liste der Teilnehmer Berechtigungen **verwalten aus.**

### <a name="user-types"></a>Benutzertypen

> [!NOTE]
> Benutzertypen können an Besprechungen teilnehmen und eine der oben beschriebenen Teilnehmerrollen annehmen. Der Benutzertyp wird nicht als Teil der **getParticipantRole-API verfügbar** gemacht.

1. **Mandantenindant**. Diese Benutzer gehören zur Organisation und verfügen über Anmeldeinformationen in Azure Active Directory für den Mandanten. Es handelt sich in der Regel um Vollzeit-, Standort- oder Remotemitarbeiter.
1. **Gast**. Ein Gast ist ein Teilnehmer aus einer anderen Organisation, der eingeladen wurde, auf Teams oder andere Ressourcen im Mandanten Ihrer Organisation zu zugreifen. Gäste werden zum Active Directory Ihrer Organisation hinzugefügt und können nahezu dieselben Teams-Funktionen wie ein systemeigenes Teammitglied mit Vollzugriff auf Teamchats, Besprechungen und Dateien erhalten. _Siehe_ [Gastzugriff in Microsoft Teams](/microsoftteams/guest-access)
1. **Federated/External**. Ein Verbundbenutzer ist ein externer Teams-Benutzer in einer anderen Organisation, der zur Teilnahme an einer Besprechung eingeladen wurde. Da diese Benutzer über gültige Anmeldeinformationen bei Verbundpartnern verfügen, werden sie von Teams als authentifiziert behandelt, haben jedoch keinen Zugriff auf Ihre Teams oder andere freigegebene Ressourcen aus Ihrer Organisation. Wenn externe Benutzer Zugriff auf Teams und Kanäle haben sollen, ist der Gastzugriff möglicherweise eine bessere Option. _Weitere Informationen_ [finden Sie unter Verwalten des externen Zugriffs in Microsoft Teams](/microsoftteams/manage-external-access)
1. **Anonym**. Anonyme Benutzer verfügen nicht über eine Active Directory-Identität und sind nicht mit einem Mandanten partnerisiert. Der anonyme Teilnehmer ist wie ein externer Benutzer, seine Identität wird jedoch nicht in die Besprechung projiziert. Anonyme Benutzer können in einem Besprechungsfenster nicht auf Apps zugreifen.

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Entwerfen Ihrer App](../apps-in-teams-meetings/design/designing-apps-in-meetings.md)
> [!div class="nextstepaction"]
> [Erstellen Sie Ihre Anwendung](create-apps-for-teams-meetings.md)
