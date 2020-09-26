---
title: Apps für Microsoft Teams-Besprechungen
author: laujan
description: Übersicht über apps in Microsoft Teams-Besprechungen basierend auf der Rolle des Teilnehmers und Benutzers
ms.topic: overview
ms.author: lajanuar
keywords: Teams-apps-Besprechungen Benutzer Teilnehmer-Rollen-API
ms.openlocfilehash: b5e649f1630ff6c4a120c4b7aefbac1f5f6df06f
ms.sourcegitcommit: b51a4982842948336cfabedb63bdf8f72703585e
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/25/2020
ms.locfileid: "48279715"
---
# <a name="apps-in-teams-meetings-preview"></a>Apps in Teams-Besprechungen (Vorschau)

>[!IMPORTANT]
> In der Vorschau von Microsoft Teams enthaltene Features werden nur für frühere Zugriffs-, Test-und Feedback Zwecke bereitgestellt. Sie werden möglicherweise geändert, bevor Sie in der öffentlichen Version verfügbar werden und sollten nicht in Produktionsanwendungen verwendet werden.

Besprechungen sind der Schlüssel zur Produktivität in Microsoft Teams. Sie ermöglichen Zusammenarbeit, Partnerschaft, informierte Kommunikation und gemeinsames Feedback in einem integrativen und aktiven Forum. Als Entwickler können Sie [konfigurierbare Registerkarten](../tabs/what-are-tabs.md#how-do-tabs-work)-, [bot](../bots/what-are-bots.md)-und [Nachrichten Erweiterungs](../messaging-extensions/what-are-messaging-extensions.md) Anwendungen erstellen, um die Besprechungs Erfahrung von Teams zu verbessern und zu bereichern. Besprechungs Benutzer können über den Tab-Katalog auf apps zugreifen, um relevante Szenarien wie das vorab Staging einer Kanban-Karte, das Starten eines in-Meeting-Aktions fähigen Dialogs oder das Erstellen einer Umfrage nach der Besprechung zu ermöglichen. Ihre Besprechungs-App kann eine Benutzeroberfläche für jede Phase des Besprechungs Lebenszyklus basierend auf dem Teilnehmerstatus bereitstellen.

Die Erweiterungs Center für die Besprechungs-App für Teams werden auf drei Konzepte umstellen:

✔ **Besprechungs Lebenszyklus** – vor, während und nach dem Besprechungszeit Rahmen.  
✔ **Teilnehmerrolle** : Besprechungsorganisator, Referent oder Teilnehmer.  
✔ **Benutzertyp** – Benutzer im Mandanten, im Gast, im Verbund oder im anonymen Team.

<!-- markdownlint-disable MD001 -->
### <a name="meeting-lifecycle-scenarios"></a>Besprechungs Lebenszyklus-Szenarien

## <a name="tabs"></a>Registerkarten

> [!IMPORTANT]
> Wie bei allen Registerkarten Anwendungen muss Ihre APP dem [SSO-Authentifizierungs Fluss](../tabs/how-to/authentication/auth-aad-sso.md) für Teams für Registerkarten entsprechen.

### <a name="pre-meeting-app-experience"></a>App-Erfahrung vor der Besprechung

**Erfahrung vor der Besprechung:**

![Erfahrung vor der Besprechung](../assets/images/apps-in-meetings/PreMeeting.png)

**Registerkarte "Pre-Meeting":**

![Registerkartenansicht vor der Besprechung](../assets/images/apps-in-meetings/PreMeetingTab.png)

✔ Berechtigte Benutzer können über den Tab-Katalog auf zwei Arten apps zu einer Besprechung hinzufügen:

&emsp;&emsp;&#9679; über die Registerkarte **Details** im Planungsformular für Teams.

&emsp;&emsp;&#9679; über die Registerkarte Besprechungs **Chat** in einer vorhandenen Besprechung.</br> </br>

Auf ✔ Registerkarten-Apps können in Besprechungs **Details** und **Chats** -Seiten mithilfe einer Plus-Symbolschaltfläche (➕) zugegriffen werden. |

### <a name="in-meeting-app-experience"></a>In-Meeting-App-Erfahrung

✔ Besprechungs-apps werden in der oberen oberen Leiste des Chatfensters und als in-Meeting-Registerkarten Darstellung über die Registerkarte "in-Meeting" gehostet. Wenn Benutzer eine Registerkarte zu einer Besprechung über den Registerkarten Katalog hinzufügen, werden apps, die **während der Besprechungs** Erfahrung sind, angezeigt.

✔ Berechtigte Benutzer können während der Besprechung apps hinzufügen.

✔, Wenn Sie im Kontext einer Besprechung geladen werden, können apps das Microsoft Teams-Client-SDK nutzen, um auf die `meetingId` `userMri` zu zugreifen und `frameContext` die Benutzeroberfläche entsprechend zu rendern.

✔ Für eine APP können in einer Teams-Besprechung in zwei Bereichen angezeigt werden:

&emsp;&emsp;&#9679; **Seitenbereich**. </br>

> [!NOTE]
> Wenn Ihr _App-Manifest_ angibt, dass Ihre Registerkarte [für den Seitenbereich optimiert](create-apps-for-teams-meetings.md#in-meeting)ist, wird Sie angezeigt. Es kann auch Teil einer Erfahrung mit Freigabe Schacht sein, die bestimmten Entwurfsrichtlinien unterliegt.

&emsp;&emsp;&#9679; **in-Meeting-Dialog**. Verwenden Sie das in-Meeting-Dialogfeld, um Aktions Inhalte für Besprechungsteilnehmer zu präsentieren. *Siehe* [Erstellen von Apps für Microsoft Teams-Besprechungen](create-apps-for-teams-meetings.md).

**Besprechungs Erfahrung:**

![Besprechungs Erfahrung](../assets/images/apps-in-meetings/in-meeting-experience.png)

![In-Meeting-Dialog Ansicht](../assets/images/apps-in-meetings/in-meeting-dialog.png)

**In-Meeting-Aktion-Dialogfeld für Benutzer:**

![Dialog Ansicht](../assets/images/apps-in-meetings/in-meeting-dialog-view.png)

### <a name="post-meeting-app-experience"></a>App-Erfahrung nach der Besprechung

**Erfahrung nach der Besprechung:**

![Post-Besprechungs Ansicht](../assets/images/apps-in-meetings/PostMeeting.png)

Das Post-Meeting-App-Szenario ähnelt der aktuellen Post-Meeting-Erfahrung mit dem zusätzlichen Vorteil, dass Registerkarten auf der Oberfläche vorhanden sind. Benutzer mit Berechtigungen können Apps aus dem Registerkarten Katalog einer Besprechung über die Registerkarte **Details** im Planungsformular für Teams und die Registerkarte Besprechungs **Chat** in einer vorhandenen Besprechung hinzufügen.

### <a name="bots"></a>Bots

Informationen zur bot-Implementierung finden Sie in der Dokumentation zu den [Bots in Microsoft Teams-Besprechungen](../bots/how-to/create-a-bot-for-teams.md#bots-in-teams-meetings) .

### <a name="messaging-extensions"></a>Messaging-Erweiterungen

Informationen zur Implementierung von Messaging Erweiterungen finden Sie in der Dokumentation zu Microsoft [Teams-Besprechungen unter Messaging Extensions](../messaging-extensions/how-to/create-messaging-extension.md#messaging-extensions-in-teams-meetings) .

## <a name="participant-roles-and-user-types-in-a-meeting"></a>Teilnehmerrollen und Benutzertypen in einer Besprechung

![Teilnehmer an einer Besprechung](../assets/images/apps-in-meetings/participant-roles.png)

### <a name="participant-roles"></a>Teilnehmerrollen

Sie können Ihre APP mit Teilnehmer spezifischer Autorisierung entwerfen. Beispielsweise kann nur ein Organisator und/oder Referent eine Umfrage in Besprechungen erstellen. Obwohl die Standardteilnehmer Einstellungen vom IT-Administrator einer Organisation festgelegt werden, kann es sein, dass ein Besprechungsorganisator die Einstellungen für eine bestimmte Besprechung ändern möchte. Organisatoren können diese Änderungen auf der Webseite mit den Besprechungsoptionen vornehmen.

1. **Organisator**. Der Organisator plant eine Besprechung, legt die Besprechungsoptionen fest, ordnet besprechungsrollen zu und startet die Besprechung. Nur Benutzer mit einem M365-Konto (besitzen eine Microsoft Teams-Lizenz) können Organisatoren sein und Berechtigungen für Teilnehmer steuern.
1. **Referent**. Referenten haben fast die gleichen Funktionen wie Organisatoren; ein Referent kann einen Organisator jedoch nicht aus der Sitzung entfernen oder Besprechungsoptionen für die Sitzung ändern. Standardmäßig haben Teilnehmer, die einer Besprechung beitreten, die Referenten Rolle.
1. **Teilnehmer**. Ein Teilnehmer ist ein Benutzer, der zur Teilnahme an einer Besprechung eingeladen wurde, aber nicht berechtigt ist, als Referent zu fungieren. Teilnehmer können mit anderen Besprechungs Mitgliedern interagieren, jedoch keine Besprechungseinstellungen verwalten oder Inhalte freigeben.

_Anzeigen_ [ **von Rollen in einer Microsoft Teams-Besprechung**](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019)

Sie können wie folgt auf die Seite  **Besprechungsoptionen** zugreifen:

Wechseln Sie &#11200; in Microsoft Teams zu **Kalender** ![ Kalender Logo ](../assets/images/apps-in-meetings/calendar-logo.png) , wählen Sie eine Besprechung und dann **Besprechungsoptionen**aus.

Wählen Sie &#11200; in einer Besprechungseinladung die Option **Besprechungsoptionen**aus.

&#11200; wählen Sie während einer Besprechung **Show participants** ![ ](../assets/images/apps-in-meetings/show-participants.png) in den Besprechungs Steuerelementen das Symbol Teilnehmer anzeigen aus. Wählen Sie dann oberhalb der Teilnehmerliste die Option **Berechtigungen verwalten**aus.

### <a name="user-types"></a>Benutzertypen

> [!NOTE]
> Benutzertypen können an Besprechungen teilnehmen und eine der oben beschriebenen Teilnehmerrollen annehmen. Der Benutzertyp wird nicht als Teil der **getParticipantRole** -API verfügbar gemacht.

1. **Im Mandanten**. Diese Benutzer gehören zur Organisation und verfügen über Anmeldeinformationen in Azure Active Directory für den Mandanten. Dabei handelt es sich normalerweise um Vollzeitmitarbeiter, vor-Ort-oder Remotemitarbeiter.
1. **Gast**. Ein Gast ist ein Teilnehmer einer anderen Organisation, der eingeladen wurde, auf Teams oder andere Ressourcen im Mandanten Ihrer Organisation zuzugreifen. Gäste werden dem Active Directory Ihrer Organisation hinzugefügt und können nahezu alle Teams-Funktionen wie ein systemeigenes Teammitglied mit Vollzugriff auf Team Chats, Besprechungen und Dateien erhalten. _Siehe_ [Gastzugriff in Microsoft Teams](/microsoftteams/guest-access)
1. **Verbund/extern**. Ein Verbundbenutzer ist ein externer Teams-Benutzer in einer anderen Organisation, der zur Teilnahme an einer Besprechung eingeladen wurde. Da diese Benutzer gültige Anmeldeinformationen für Verbundpartner haben, werden Sie von Microsoft Teams authentifiziert, haben aber keinen Zugriff auf Ihre Teams oder andere freigegebene Ressourcen von Ihrer Organisation. Wenn Sie möchten, dass externe Benutzer Zugriff auf Teams und Kanäle haben, ist der Gastzugriff möglicherweise eine bessere Option. _Siehe_ [Verwalten von externem Zugriff in Microsoft Teams](/microsoftteams/manage-external-access)
1. **Anonym**. Anonyme Benutzer verfügen nicht über eine Active Directory Identität und sind nicht Verbund mit einem Mandanten. Der anonyme Teilnehmer ist wie ein externer Benutzer, aber seine Identität wird nicht in die Besprechung projiziert. Anonyme Benutzer können nicht auf apps in einem Besprechungsfenster zugreifen.

## <a name="next-steps"></a>Nächste Schritte

> [!div class="nextstepaction"]
> [Erstellen von Apps für Microsoft Teams-Besprechungen](create-apps-for-teams-meetings.md)
