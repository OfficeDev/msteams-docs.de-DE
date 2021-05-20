---
title: Apps in Teams Meetings
author: laujan
description: Übersicht über Apps in Teams Meetings basierend auf Teilnehmer- und Benutzerrolle
ms.topic: overview
ms.author: lajanuar
localization_priority: Normal
keywords: Teams Apps Meetings Benutzer Teilnehmer Rolle api
ms.openlocfilehash: c5419565d8defd03a3dcfcc5b05b9517cb4269e2
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52565924"
---
# <a name="apps-in-teams-meetings"></a>Apps in Teams Meetings

Meetings ermöglichen Zusammenarbeit, Partnerschaft, informierte Kommunikation und gemeinsames Feedback in einem inklusiven und aktiven Forum. Die Besprechungs-App kann je nach Status des Teilnehmers eine Benutzererfahrung für jede Phase des Besprechungslebenszyklus bereitstellen, einschließlich Pre-Meeting-, In-Meeting- und Post-Meeting-App-Erfahrung.

Teams Endbenutzer können während Besprechungen über den Tab-Katalog auf Apps zugreifen, z. B.:

* Vorstufe eines Kanban-Boards
* Starten eines in Meeting umsetzbaren Dialogfelds
* Erstellen einer Umfrage nach dem Meeting

Die Erweiterbarkeit der Besprechungs-App für Teams basiert auf den folgenden Konzepten:

✔ Meeting-Lebenszyklus hat Phasen wie vor, während und nach dem Besprechungszeitraum.  
✔ Teilnehmerrollen in einer Besprechung, z. B. Besprechungsorganisator, Moderator oder Teilnehmer.  
✔ Benutzertypen in einer Besprechung, z. B. in-tenant, guest, federated oder anonymous Teams user.

Dieser Artikel behandelt Informationen zum Besprechungslebenszyklus und zum Integrieren von Registerkarten, Bots und Messagingerweiterungen in Ihre Besprechung. Außerdem können Sie Teilnehmerrollen identifizieren und auch verschiedene Benutzertypen zum Ausführen von Aufgaben verwenden.

> [!NOTE]
> Um mit den Erweiterbarkeitsfeatures der Besprechungs-App arbeiten zu können, müssen Sie über die entsprechenden Berechtigungen verfügen.

### <a name="meeting-lifecycle"></a>Besprechungslebenszyklus

Der Besprechungslebenszyklus besteht aus der App-Erfahrung vor Meeting, Besprechung und Nachbesprechung. Sie können Registerkarten, Bots und Messagingerweiterungen in jeder Phase des Besprechungslebenszyklus integrieren.

## <a name="integrate-tabs-into-the-meeting-lifecycle"></a>Integrieren von Registerkarten in den Besprechungslebenszyklus

Registerkarten ermöglichen Teammitgliedern den Zugriff auf Dienste und Inhalte in einem bestimmten Bereich innerhalb eines Kanals oder Chats. Auf diese Weise kann das Team direkt mit Registerkarten arbeiten und Gespräche über die Tools und Daten führen, die in Registerkarten verfügbar sind. In Teams Besprechung können Benutzer eine Registerkarte hinzufügen, indem sie Plus <img src="~/assets/images/apps-in-meetings/plusbutton.png" alt="Plus button" width="30"/>, und wählen Sie die App aus, die sie als Registerkarte installieren möchten.

> [!IMPORTANT]
> Wenn Sie eine Registerkarte in Ihre Besprechung integriert haben, muss Ihre App dem Teams [SSO-Authentifizierungsablauf (Single Sign-On)](../tabs/how-to/authentication/auth-aad-sso.md) für Registerkarten folgen.

> [!NOTE]
> * Mobile Clients unterstützen Registerkarten nur in Pre- und Post-Meeting-Phasen. Die Besprechungserlebnisse, die sich im Besprechungsdialog und im Panel befinden, sind derzeit nicht auf Mobilgeräten verfügbar.
> * Apps werden nur in privaten geplanten Besprechungen unterstützt.

### <a name="pre-meeting-app-experience"></a>Pre-Meeting-App-Erfahrung

**Erfahrung vor dem Meeting:**

![Pre-Meeting-Erfahrung](../assets/images/apps-in-meetings/PreMeeting.png)

**Registerkarte Vor dem Meeting:**

![Registerkartenansicht vor der Besprechung](../assets/images/apps-in-meetings/PreMeetingTab.png)

✔ Berechtigte Benutzer sind Benutzer, die apps zu einer Besprechung in verschiedenen Phasen des Besprechungslebenszyklus hinzufügen können. Diese Benutzer können Apps über die Registerkartengalerie auf zwei Arten zu einer Besprechung hinzufügen:

   * Verwenden der Registerkarte **Details** im Teams Planungsformular.

   * Verwenden der Registerkarte **Besprechungschat** in einer vorhandenen Besprechung.

✔ Tab-Apps sind in Besprechungen **Details-** und **Chat-Seiten** über eine Plus-➕-Schaltfläche zugänglich.

✔ Tab-Layout muss sich in einem organisierten Zustand befinden, wenn mehr als zehn Umfragen oder Umfragen vorliegen.

### <a name="in-meeting-app-experience"></a>In-Meeting-App-Erfahrung

✔ Meeting-Apps werden in der oberen oberen Leiste des Chatfensters gehostet und als In-Meeting-Registerkarte n.V. über die Registerkarte "Besprechung" angezeigt. Wenn Benutzer einer Besprechung über die Registerkartengalerie eine Registerkarte hinzufügen, werden Apps angezeigt, die sich während der **Besprechungserfahrung** befinden.

✔ Berechtigte Benutzer können während der Besprechung Apps hinzufügen.

✔ Beim Laden im Kontext einer Besprechung können Apps das Teams Client-SDK nutzen, um auf die zuzugreifen `meetingId` und die Erfahrung entsprechend zu `userMri` `frameContext` rendern.

✔ Das Exportieren eines Ergebnisses einer Umfrage oder Umfrage benachrichtigt die Benutzer, dass die Ergebnisse erfolgreich heruntergeladen wurden.

✔ Eine App ist in einer Teams Besprechung im Seitenbereich oder im Dialogfeld "Besprechung" sichtbar. Verwenden Sie das Dialogfeld in der Besprechung, um umsetzbare Inhalte für Besprechungsteilnehmer zu präsentieren. Weitere Informationen finden Sie unter [Erstellen von Apps für Teams Besprechungen](create-apps-for-teams-meetings.md).

   > [!NOTE]
   > Ihr App-Manifest gibt an, dass Ihre Registerkarte [für den Seitenbereich optimiert](create-apps-for-teams-meetings.md#during-a-meeting)ist, d. h., wo sie angezeigt wird. Es kann auch Teil eines Share-Tray-Erlebnisses sein, vorbehaltlich bestimmter Entwurfsrichtlinien.

Die folgenden Bilder zeigen die App als Dialogfeld in der Besprechung und als separate Seitengruppe an:

![In-Meeting-Erfahrung](../assets/images/apps-in-meetings/in-meeting-experience.png)

![In-Meeting-Dialog-Ansicht](../assets/images/apps-in-meetings/in-meeting-dialog.png)

#### <a name="in-meeting-actionable-dialog-for-users"></a>In-Meeting-Dialog für Benutzer

![Dialogansicht](../assets/images/apps-in-meetings/in-meeting-dialog-view.png)

### <a name="post-meeting-app-experience"></a>App-Erfahrung nach dem Treffen

![Ansicht nach der Besprechung](../assets/images/apps-in-meetings/PostMeeting.png)

✔ Das App-Szenario nach dem Meeting ähnelt der aktuellen Erfahrung nach dem Meeting mit dem zusätzlichen Vorteil, dass Registerkarten innerhalb der Oberfläche vorhanden sind.

✔ Berechtigte Benutzer können Apps aus dem Registerkartenkatalog zu einer Besprechung hinzufügen, indem Sie die Registerkarte **Details** im Teams Planungsformular und die Registerkarte **Besprechungschat** in einer vorhandenen Besprechung verwenden.

✔ Tab-Layout muss organisiert werden, wenn mehr als zehn Umfragen oder Umfragen vorliegen.

### <a name="integrate-bots-into-the-meeting-lifecycle"></a>Integrieren von Bots in den Meeting-Lebenszyklus

Für die Bot-Implementierung beginnen Sie mit [dem Erstellen eines Bots](../build-your-first-app/build-bot.md) und fahren Sie dann mit der Erstellung von [Apps für Teams Meetings](../apps-in-teams-meetings/create-apps-for-teams-meetings.md#meeting-apps-api-reference)fort.

### <a name="integrate-messaging-extensions-into-the-meeting-lifecycle"></a>Integrieren von Messagingerweiterungen in den Besprechungslebenszyklus

Beginnen Sie für die Implementierung von Messagingerweiterungen mit [dem Erstellen einer Messagingerweiterung,](../messaging-extensions/how-to/create-messaging-extension.md) und fahren Sie dann mit [dem Erstellen von Apps für Teams Besprechungen](../apps-in-teams-meetings/create-apps-for-teams-meetings.md#meeting-apps-api-reference)fort.

## <a name="participant-roles-and-user-types-in-a-meeting"></a>Teilnehmerrollen und Benutzertypen in einer Besprechung

![Teilnehmer an einem Meeting](../assets/images/apps-in-meetings/participant-roles.png)

### <a name="participant-roles"></a>Teilnehmerrollen

Die Standardteilnehmereinstellungen werden vom IT-Administrator einer Organisation festgelegt. Im Folgenden sind die Teilnehmerrollen in einer Besprechung:

* **Organisator**: Der Organisator plant eine Besprechung, legt die Besprechungsoptionen fest, weist Besprechungsrollen zu und startet die Besprechung. Nur Benutzer mit einem M365-Konto mit einer Teams-Lizenz können Organisatoren und Steuerelementberechtigungen für Teilnehmer sein. Ein Besprechungsorganisator kann die Einstellungen für eine bestimmte Besprechung ändern. Organisatoren können diese Änderungen auf der Webseite der **Besprechungsoptionen** vornehmen.
* **Presenter**: Moderatoren haben die gleichen Funktionen wie der Organisator. Ein Moderator kann jedoch keinen Organisator aus der Sitzung entfernen oder Besprechungsoptionen für die Sitzung ändern. Standardmäßig haben Teilnehmer, die an einer Besprechung teilnehmen, die Referentenrolle.
* **Teilnehmer:** Ein Teilnehmer ist ein Benutzer, der zur Teilnahme an einer Besprechung eingeladen wurde, aber nicht berechtigt ist, als Moderator zu fungieren. Teilnehmer können mit anderen Besprechungsmitgliedern interagieren, aber keine der Besprechungseinstellungen verwalten oder Inhalte freigeben.

Nur ein Organisator oder Moderator kann Apps hinzufügen, entfernen oder deinstallieren. Nur Organisator oder Moderator kann Umfragen in einer Besprechung erstellen.

Weitere Informationen finden Sie unter [Rollen in einer besprechung Teams](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019).

Sie können wie folgt auf die Seite  **Besprechungsoptionen** zugreifen:

* Wechseln Sie in  Teams zum ![ Kalenderkalenderlogo ](../assets/images/apps-in-meetings/calendar-logo.png) , wählen Sie eine Besprechung aus, und dann die **Besprechungsoptionen**.

* Wählen Sie in einer **Besprechungseinladung Besprechungsoptionen** aus.

* Wählen Sie während einer Besprechung die Option **Teilnehmer** ![ anzeigen das Symbol in den ](../assets/images/apps-in-meetings/show-participants.png) Besprechungssteuerelementen anzeigen aus. Wählen Sie dann über der Teilnehmerliste **Berechtigungen verwalten** aus.

### <a name="user-types"></a>Benutzertypen

> [!NOTE]
> Benutzer mit bestimmten Benutzertypen, die ihnen zugewiesen sind, können an Besprechungen teilnehmen und eine der teilnehmerrollen übernehmen, die in [Teilnehmerrollen](#participant-roles)beschrieben sind. Der Benutzertyp ist nicht in der **getParticipantRole-API** enthalten.

Die folgenden Benutzertypen identifizieren, was jeder Benutzer tun kann und worauf er zugreifen kann:

* **In-Tenant**: Mandantenbenutzer gehören zur Organisation und verfügen über Anmeldeinformationen in Azure Active Directory (AAD) für den Mandanten. Sie sind in der Regel Vollzeit-, Vor-Ort- oder Remote-Mitarbeiter. Ein mandantist ein Organisator, Moderator oder Teilnehmer kann sein.
* **Gast**: Ein Gast ist ein Teilnehmer einer anderen Organisation, der zum Zugriff auf Teams oder andere Ressourcen im Mandanten der Organisation eingeladen ist. Gäste werden dem AAD Ihrer Organisation hinzugefügt und verfügen über die gleichen Teams Funktionen wie ein natives Teammitglied mit Zugriff auf Teamchats, Besprechungen und Dateien. Ein Gastbenutzer kann ein Organisator, Moderator oder Teilnehmer sein. Weitere Informationen finden Sie [unter Gastzugriff in Teams](/microsoftteams/guest-access).
* **Verbundoder oder extern:** Ein Verbundbenutzer ist ein externer Teams Benutzer in einer anderen Organisation, der zur Teilnahme an einer Besprechung eingeladen wurde. Diese Benutzer verfügen über gültige Anmeldeinformationen bei Verbundpartnern und sind von Teams autorisiert. Sie haben keinen Zugriff auf Ihre Teams oder andere freigegebene Ressourcen aus Ihrer Organisation. Der Gastzugriff ist eine bessere Option für externe Benutzer, um Zugriff auf Teams und Kanäle zu haben. Weitere Informationen finden Sie unter [Verwalten des externen Zugriffs in Teams](/microsoftteams/manage-external-access).
* **Anonym**: Anonyme Benutzer haben keine AAD-Identität und werden nicht mit einem Mandanten verbunden. Der anonyme Teilnehmer ist wie ein externer Benutzer, aber seine Identität wird nicht in der Besprechung projiziert. Ein anonymer Benutzer kann kein Organisator sein, sondern ein Moderator oder Teilnehmer sein.

> [!NOTE]
> Anonyme Benutzer erben die globale Standardrichtlinie für App-Berechtigungsrichtlinien auf Benutzerebene. Weitere Informationen finden Sie unter Verwalten von [Apps](/microsoftteams/non-standard-users#anonymous-user-in-meetings-access).

Die folgende Tabelle enthält die Benutzertypen und die Funktionen, auf die jeder Benutzer zugreifen kann:

| Benutzertyp | Registerkarten | Bots | Messaging-Erweiterungen | Adaptive Karten | Aufgabenmodule | Dialogfeld "Besprechung" |
| :-- | :-- | :-- | :-- | :-- | :-- | :-- |
| Anonymer Benutzer | Nicht verfügbar | Nicht verfügbar | Nicht verfügbar | Interaktionen im Besprechungschat sind zulässig. | Interaktionen im Besprechungschat von einer Adaptive Card sind zulässig. | Nicht verfügbar |
| Gast, der Teil des Mieters AAD ist | Interaktion ist erlaubt. Das Erstellen, Aktualisieren und Löschen ist nicht zulässig. | Nicht verfügbar | Nicht verfügbar | Interaktionen im Besprechungschat sind zulässig. | Interaktionen im Besprechungschat von einer Adaptive Card sind zulässig. | Available |
| Federated | Nicht verfügbar | Nicht verfügbar | Nicht verfügbar | Nicht verfügbar | Nicht verfügbar | Nicht verfügbar |

## <a name="see-also"></a>Siehe auch

* [Tab](../tabs/what-are-tabs.md#understand-how-tabs-work)
* [Bot](../bots/what-are-bots.md)
* [Messaging-Erweiterung](../messaging-extensions/what-are-messaging-extensions.md)
* [Entwerfen Ihrer App](../apps-in-teams-meetings/design/designing-apps-in-meetings.md)

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Erstellen Sie Ihre Anwendung](create-apps-for-teams-meetings.md)
