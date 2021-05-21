---
title: Apps in Teams Besprechungen
author: laujan
description: Übersicht über Apps in Teams Besprechungen basierend auf der Teilnehmer- und Benutzerrolle
ms.topic: overview
ms.author: lajanuar
localization_priority: Normal
keywords: Rollen-API für Teams-Apps-Besprechungen für Benutzerteilnehmer
ms.openlocfilehash: c1f7ef6b03b9f9c51d591fac7484a29492d81b41
ms.sourcegitcommit: 20764037458026e5870ee3975b966404103af650
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/20/2021
ms.locfileid: "52583743"
---
# <a name="apps-in-teams-meetings"></a>Apps in Teams Besprechungen

Besprechungen ermöglichen Zusammenarbeit, Partnerschaft, informierte Kommunikation und geteiltes Feedback in einem inklusiven und aktiven Forum. Die Besprechungs-App kann je nach Status des Teilnehmers eine Benutzeroberfläche für jede Phase des Besprechungslebenszyklus bereitstellen, einschließlich der Vorbetreff-, Besprechungs- und Post-Meeting-App-Erfahrung.

Teams Endbenutzer können während Besprechungen über den Registerkartenkatalog auf Apps zugreifen, z. B.:

* Vorabphase eines Kanban-Board
* Starten eines Dialogfelds mit Aktionen in Besprechungen
* Erstellen einer Umfrage nach der Besprechung

Teams der Erweiterung der Besprechungs-App basiert auf den folgenden Konzepten:

✔ besprechungslebenszyklus hat Phasen wie vor, während und nach besprechung Zeitrahmen.  
✔ teilnehmerrollen in einer Besprechung, z. B. Besprechungsorganisator, Organisator oder Teilnehmer.  
✔ Benutzertypen in einer Besprechung wie mandanten-, gast-, verbund- oder anonyme Benutzertypen Teams werden.

Dieser Artikel behandelt Informationen zum Besprechungslebenszyklus und zur Integration von Registerkarten, Bots und Messagingerweiterungen in Ihre Besprechung. Außerdem können Sie Teilnehmerrollen identifizieren und auch verschiedene Benutzertypen verwenden, um Aufgaben auszuführen.

> [!NOTE]
> Zum Arbeiten mit den Erweiterungsfeatures der Besprechungs-App müssen Sie über die entsprechenden Berechtigungen verfügen.

### <a name="meeting-lifecycle"></a>Besprechungslebenszyklus

Der Besprechungslebenszyklus besteht aus app-Erfahrung vor der Besprechung, in der Besprechung und nach der Besprechung. Sie können Registerkarten, Bots und Messagingerweiterungen in jeder Phase des Besprechungslebenszyklus integrieren.

## <a name="integrate-tabs-into-the-meeting-lifecycle"></a>Integrieren von Registerkarten in den Besprechungslebenszyklus

Registerkarten ermöglichen Teammitgliedern den Zugriff auf Dienste und Inhalte in einem bestimmten Bereich innerhalb eines Kanals oder Chats. Auf diese Weise kann das Team direkt mit Registerkarten arbeiten und Unterhaltungen über die Tools und Daten führen, die in Registerkarten verfügbar sind. In Teams Können Benutzer eine Registerkarte hinzufügen, indem sie plus auswählen <img src="~/assets/images/apps-in-meetings/plusbutton.png" alt="Plus button" width="30"/>und die App auswählen, die sie als Registerkarte installieren möchten.

> [!IMPORTANT]
> Wenn Sie eine Registerkarte in Ihre Besprechung integriert haben, muss Ihre App dem Authentifizierungsfluss Teams einmaliges Anmelden [(Single Sign-On, SSO)](../tabs/how-to/authentication/auth-aad-sso.md) für Registerkarten folgen.

> [!NOTE]
> * Mobile Clients unterstützen Registerkarten nur in Vor- und Nachbesprechungsphasen. Die Besprechungserfahrungen, die im Besprechungsdialogfeld und -panel vorhanden sind, sind derzeit nicht auf Mobilgeräten verfügbar.
> * Apps werden nur in privaten geplanten Besprechungen unterstützt.

### <a name="pre-meeting-app-experience"></a>App-Erfahrung vor besprechung

**Vorbetreff:**

![Pre-Meeting-Erfahrung](../assets/images/apps-in-meetings/PreMeeting.png)

**Registerkarte "Pre-Meeting":**

![Registerkartenansicht vor der Besprechung](../assets/images/apps-in-meetings/PreMeetingTab.png)

✔ benutzer sind Benutzer, die apps zu einer Besprechung in verschiedenen Phasen des Besprechungslebenszyklus hinzufügen können. Diese Benutzer können apps zu einer Besprechung über den Registerkartenkatalog auf zwei Arten hinzufügen:

   * Verwenden der **Registerkarte Details** im Teams Zeitplanungsformular.

   * Verwenden der Registerkarte **Besprechungschat** in einer vorhandenen Besprechung.

✔ Tab-Apps sind in **Besprechungsdetails** und **Chats-Seiten** über eine Plus-➕ zugänglich.

✔ Registerkartenlayout muss sich in einem organisierten Zustand befinden, wenn mehrere (mehr als zehn) Umfragen oder Umfragen durchgeführt werden.

### <a name="in-meeting-app-experience"></a>In-Meeting-App-Erfahrung

✔ Besprechungs-Apps werden in der oberen Leiste des Chatfensters und als Registerkartenerfahrung in Besprechungen mithilfe der Registerkarte "In-Meeting" gehostet. Wenn Benutzer einer Besprechung über den Registerkartenkatalog eine Registerkarte hinzufügen, werden Apps angezeigt, die sich während **der Besprechungserfahrung** befinden.

✔ Berechtigte Benutzer können Apps während der Besprechung hinzufügen.

✔ Wenn sie im Kontext einer Besprechung geladen werden, können Apps das Teams-Client-SDK nutzen, um auf das , zu zugreifen und die Benutzererfahrung entsprechend zu `meetingId` `userMri` `frameContext` rendern.

✔ Exportieren eines Ergebnisses einer Umfrage oder Umfrage benachrichtigt die Benutzer, dass die Ergebnisse erfolgreich heruntergeladen wurden.

✔ Eine App wird in einer Teams im Seitenbereich oder im Dialogfeld in der Besprechung angezeigt. Verwenden Sie das Dialogfeld in der Besprechung, um aktionenfähige Inhalte für Besprechungsteilnehmer anzuzeigen. Weitere Informationen finden Sie unter [Erstellen von Apps für Teams Besprechungen.](create-apps-for-teams-meetings.md)

   > [!NOTE]
   > Ihr App-Manifest gibt an, dass Ihre Registerkarte [für den Seitenbereich](create-apps-for-teams-meetings.md#during-a-meeting)optimiert ist, d. h. an der Stelle, an der sie angezeigt wird. Sie kann auch Teil einer Share-Tray-Erfahrung sein, die den angegebenen Entwurfsrichtlinien unterliegt.

In den folgenden Bildern wird die App als Besprechungsdialogfeld und als separater Seitenbereich angezeigt:

![In-Meeting-Erfahrung](../assets/images/apps-in-meetings/in-meeting-experience.png)

![In-Meeting-Dialog-Ansicht](../assets/images/apps-in-meetings/in-meeting-dialog.png)

#### <a name="in-meeting-actionable-dialog-for-users"></a>In-Meeting-Dialogfeld mit Aktionen für Benutzer

![Dialogansicht](../assets/images/apps-in-meetings/in-meeting-dialog-view.png)

### <a name="post-meeting-app-experience"></a>App-Erfahrung nach der Besprechung

![Besprechungsansicht veröffentlichen](../assets/images/apps-in-meetings/PostMeeting.png)

✔ Das App-Szenario nach der Besprechung ähnelt der aktuellen Nachbesprechung mit dem zusätzlichen Vorteil, dass Registerkarten auf der Oberfläche vorhanden sind.

✔ Berechtigte Benutzer können Apps aus dem Registerkartenkatalog zu einer Besprechung mithilfe der Registerkarte **Details** im Teams-Planungsformular und der Registerkarte Besprechungschat in einer vorhandenen Besprechung hinzufügen. 

✔ Registerkartenlayout muss organisiert sein, wenn mehr als zehn Umfragen oder Umfragen durchgeführt werden.

### <a name="integrate-bots-into-the-meeting-lifecycle"></a>Integrieren von Bots in den Besprechungslebenszyklus

Beginnen Sie bei der Botimplementierung mit [dem Erstellen eines Bots,](../build-your-first-app/build-bot.md) und fahren Sie dann mit dem Erstellen von Apps für [Teams fort.](../apps-in-teams-meetings/create-apps-for-teams-meetings.md#meeting-apps-api-reference)

### <a name="integrate-messaging-extensions-into-the-meeting-lifecycle"></a>Integrieren von Messagingerweiterungen in den Besprechungslebenszyklus

Beginnen Sie bei der Implementierung von Messagingerweiterungen mit dem Erstellen einer [Messagingerweiterung,](../messaging-extensions/how-to/create-messaging-extension.md) und fahren Sie dann mit dem Erstellen von [Apps für Teams fort.](../apps-in-teams-meetings/create-apps-for-teams-meetings.md#meeting-apps-api-reference)

## <a name="participant-roles-and-user-types-in-a-meeting"></a>Teilnehmerrollen und Benutzertypen in einer Besprechung

![Teilnehmer an einer Besprechung](../assets/images/apps-in-meetings/participant-roles.png)

### <a name="participant-roles"></a>Teilnehmerrollen

Die Standardeinstellungen für Teilnehmer werden vom IT-Administrator einer Organisation bestimmt. Es folgen die Teilnehmerrollen in einer Besprechung:

* **Organisator**: Der Organisator plant eine Besprechung, legt die Besprechungsoptionen fest, weist Besprechungsrollen zu und startet die Besprechung. Nur Benutzer mit einem M365-Konto mit Teams können Organisatore sein und Die Teilnehmerberechtigungen steuern. Ein Besprechungsorganisator kann die Einstellungen für eine bestimmte Besprechung ändern. Organisatoren können diese Änderungen auf der Webseite **"Besprechungsoptionen"** vornehmen.
* **Organisator**: Organisator hat dieselben Funktionen wie Organisator. Ein Organisator kann jedoch keinen Organisator aus der Sitzung entfernen oder Besprechungsoptionen für die Sitzung ändern. Standardmäßig haben Teilnehmer, die an einer Besprechung teilnahmen, die Rolle des Moderators.
* **Teilnehmer**: Ein Teilnehmer ist ein Benutzer, der zur Teilnahme an einer Besprechung eingeladen wurde, der jedoch nicht autorisiert ist, als Moderator zu fungieren. Teilnehmer können mit anderen Besprechungsmitgliedern interagieren, aber keine Besprechungseinstellungen verwalten oder Inhalte freigeben.

Nur ein Organisator oder Organisator kann Apps hinzufügen, entfernen oder deinstallieren. Nur Organisator oder Organisator können Umfragen in einer Besprechung erstellen.

Weitere Informationen finden Sie unter [Rollen in einer Teams Besprechung](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019).

Sie können wie folgt auf  **die Seite Besprechungsoptionen** zugreifen:

* Wechseln Teams zu **Kalenderlogo** ![ ](../assets/images/apps-in-meetings/calendar-logo.png) Kalender, wählen Sie eine Besprechung und dann **Besprechungsoptionen aus.**

* Wählen Sie in einer Besprechungseinladung **Besprechungsoptionen aus.**

* Wählen Sie während einer Besprechung das Symbol Teilnehmer **anzeigen** ![ in den ](../assets/images/apps-in-meetings/show-participants.png) Besprechungssteuerelementen anzeigen aus. Wählen Sie dann oberhalb der Liste der Teilnehmer Berechtigungen **verwalten aus.**

### <a name="user-types"></a>Benutzertypen

> [!NOTE]
> Benutzer, denen bestimmte Benutzertypen zugewiesen sind, können an Besprechungen teilnehmen und eine der in den [Teilnehmerrollen beschriebenen Teilnehmerrollen übernehmen.](#participant-roles) Der Benutzertyp ist nicht in der **getParticipantRole-API** enthalten.

Die folgenden Benutzertypen bestimmen, was jeder Benutzer tun kann und worauf er zugreifen kann:

* **In-tenant:** Mandantenbenutzer gehören der Organisation an und verfügen über Anmeldeinformationen in Azure Active Directory (AAD) für den Mandanten. Es handelt sich in der Regel um Vollzeit-, Standort- oder Remotemitarbeiter. Ein Mandantenbenutzer kann ein Organisator, Organisator oder Teilnehmer sein.
* **Gast**: Ein Gast ist ein Teilnehmer aus einer anderen Organisation, der eingeladen ist, auf Teams oder andere Ressourcen im Mandanten der Organisation zu zugreifen. Gäste werden zum AAD Ihrer Organisation hinzugefügt und verfügen über die gleichen Teams funktionen wie ein systemeigenes Teammitglied mit Zugriff auf Teamchats, Besprechungen und Dateien. Ein Gastbenutzer kann ein Organisator, Organisator oder Teilnehmer sein. Weitere Informationen finden Sie unter [Gastzugriff in Teams](/microsoftteams/guest-access).
* **Partner oder extern:** Ein Verbundbenutzer ist ein externer Teams benutzer in einer anderen Organisation, der zur Teilnahme an einer Besprechung eingeladen wurde. Diese Benutzer verfügen über gültige Anmeldeinformationen bei Verbundpartnern und sind von Teams. Sie haben keinen Zugriff auf Ihre Teams oder andere freigegebene Ressourcen aus Ihrer Organisation. Der Gastzugriff ist eine bessere Option für externe Benutzer, um Zugriff auf Teams und Kanäle zu haben. Weitere Informationen finden Sie unter [Verwalten des externen Zugriffs in Teams](/microsoftteams/manage-external-access).
* **Anonym:** Anonyme Benutzer verfügen nicht über eine AAD-Identität und sind nicht mit einem Mandanten in Verbindung. Der anonyme Teilnehmer ist wie ein externer Benutzer, aber seine Identität wird in der Besprechung nicht projiziert. Ein anonymer Benutzer kann kein Organisator sein, aber ein Organisator oder Ein Teilnehmer sein.

> [!NOTE]
> Anonyme Benutzer erben die globale Standardmäßige App-Berechtigungsrichtlinie auf Benutzerebene. Weitere Informationen finden Sie unter [Manage Apps](/microsoftteams/non-standard-users#anonymous-user-in-meetings-access).

Die folgende Tabelle enthält die Benutzertypen und die Features, auf die jeder Benutzer zugreifen kann:

| Benutzertyp | Registerkarten | Bots | Messaging-Erweiterungen | Adaptive Karten | Aufgabenmodule | Dialogfeld "Besprechung" |
| :-- | :-- | :-- | :-- | :-- | :-- | :-- |
| Anonymer Benutzer | Nicht verfügbar | Nicht verfügbar | Nicht verfügbar | Interaktionen im Besprechungschat sind zulässig. | Interaktionen im Besprechungschat von einer adaptiven Karte sind zulässig. | Nicht verfügbar |
| Gast, der Teil des Mandanten-AAD ist | Interaktion ist zulässig. Erstellen, Aktualisieren und Löschen sind nicht zulässig. | Nicht verfügbar | Nicht verfügbar | Interaktionen im Besprechungschat sind zulässig. | Interaktionen im Besprechungschat von einer adaptiven Karte sind zulässig. | Available |
| Verbund | Nicht verfügbar | Nicht verfügbar | Nicht verfügbar | Nicht verfügbar | Nicht verfügbar | Nicht verfügbar |

## <a name="see-also"></a>Siehe auch

* [Tab](../tabs/what-are-tabs.md#understand-how-tabs-work)
* [Bot](../bots/what-are-bots.md)
* [Messaging-Erweiterung](../messaging-extensions/what-are-messaging-extensions.md)
* [Entwerfen Ihrer App](../apps-in-teams-meetings/design/designing-apps-in-meetings.md)

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Erstellen Sie Ihre Anwendung](create-apps-for-teams-meetings.md)
