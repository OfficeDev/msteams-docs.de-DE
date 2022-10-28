---
title: Apps für Teams-Besprechungen
author: surbhigupta
description: In diesem Artikel erfahren Sie, wie Apps in Microsoft Teams-Besprechungen basierend auf der Rolle "Teilnehmer", "Benutzer" und "App-Erweiterbarkeit" funktionieren.
ms.topic: overview
ms.author: lajanuar
ms.localizationpriority: medium
ms.date: 04/07/2022
ms.openlocfilehash: f253a4ca3d09e48f99df36fdcb77bdd740fab5ff
ms.sourcegitcommit: bb15ce26cd65bec90991b703069424ab4b4e1a61
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/28/2022
ms.locfileid: "68772272"
---
# <a name="apps-for-teams-meetings-and-calls"></a>Apps für Teams-Besprechungen und -Anrufe

Besprechungen ermöglichen Zusammenarbeit, Partnerschaft, informierte Kommunikation und geteiltes Feedback. Der Besprechungsbereich kann eine Benutzererfahrung für jede Phase des Besprechungslebenszyklus bereitstellen. Die folgende Abbildung vermittelt eine Vorstellung von den Erweiterungsmöglichkeiten der Besprechungs-App:

:::image type="content" source="../assets/images/apps-in-meetings/meetingappextensibility.png" alt-text="Der Screenshot zeigt, wie die Erweiterbarkeit von Besprechungs-Apps funktioniert.":::

Sie müssen mit den folgenden Produktkonzepten vertraut sein, um benutzerdefinierte Besprechungserfahrungen mit Apps in Microsoft Teams zu erstellen.

## <a name="supported-meeting-types-in-teams"></a>Unterstützte Besprechungstypen in Teams

Teams unterstützt den Zugriff auf Apps während der Besprechung für die folgenden Besprechungstypen:

* [**Geplante Besprechungen**](https://support.microsoft.com/office/schedule-a-meeting-in-teams-943507a9-8583-4c58-b5d2-8ec8265e04e5#ID0EFBD=Desktop): Besprechungen, die über den Teams-Kalender geplant sind.
* [**Geplante Kanalbesprechungen**](https://support.microsoft.com/office/schedule-a-meeting-in-teams-943507a9-8583-4c58-b5d2-8ec8265e04e5#ID0EFBD=Desktop): Besprechungen, die über öffentliche Teams-Kanäle geplant werden.
* [**Einzelanrufe**](https://support.microsoft.com/office/start-a-call-from-a-chat-in-teams-f5138c9d-df4c-43d8-9cf6-53400c1a7798): Anrufe, die im Einzelchat initiiert werden.
* [**Gruppenanrufe**](https://support.microsoft.com/office/start-a-call-from-a-chat-in-teams-f5138c9d-df4c-43d8-9cf6-53400c1a7798): Im Gruppenchat initiierte Anrufe.
* [**Sofortbesprechungen**](https://support.microsoft.com/office/start-an-instant-meeting-in-teams-ff95e53f-8231-4739-87fa-00b9723f4ef5): Besprechungen, die über die Schaltfläche **"Jetzt besprechen** " im Teams-Kalender initiiert wurden.
* [**Webinar**](https://support.microsoft.com/office/get-started-with-teams-webinars-42f3f874-22dc-4289-b53f-bbc1a69013e3): Webinar initiiert über die Schaltfläche **"Webinar** " in der Dropdownliste **"Neue Besprechung** ".

Erfahren Sie mehr über [Teams-Besprechungen, Ablauf- und Richtlinien](/MicrosoftTeams/meeting-expiration) und [Besprechungen, Webinare und Liveereignisse](/microsoftteams/quick-start-meetings-live-events).
> [!NOTE]
>
> * Apps für geplante Besprechungen im öffentlichen Kanal sind derzeit nur in der [öffentlichen Entwicklervorschau](../resources/dev-preview/developer-preview-intro.md) verfügbar.
> * Apps werden in den folgenden Artikeln nicht unterstützt:
>   * [PstN-Teams-Anrufe (Public Switched Telephone Network)](/microsoftteams/cloud-voice-landing-page#public-switched-telephone-network-connectivity-options)
>   * [End-to-End-verschlüsselte Teams-Anrufe](https://support.microsoft.com/office/use-end-to-end-encryption-for-teams-calls-1274b4d2-b5c5-4b24-a376-606fa6728a90)
>   * [Sofortkanalbesprechungen](https://support.microsoft.com/office/start-an-instant-meeting-in-teams-ff95e53f-8231-4739-87fa-00b9723f4ef5)
>   * Besprechungen im [freigegebenen Kanal](https://support.microsoft.com/office/what-is-a-shared-channel-in-teams-e70a8c22-fee4-4d6e-986f-9e0781d7d11d)

## <a name="meeting-lifecycle"></a>Der Besprechungslebenszyklus

Ein Besprechungslebenszyklus umfasst die App-Erfahrung vor, in der Besprechung und nach der Besprechung, abhängig vom Benutzertyp und der Rolle des Benutzers in einer Teams-Besprechung.

## <a name="user-types-in-teams"></a>Benutzertypen in Teams

Teams unterstützt Benutzertypen wie mandanteninterne, Gastbenutzer, Verbundbenutzer oder externe Benutzer in einer Teams-Besprechung. Jeder Benutzertyp kann über eine der [Benutzerrollen in der Teams-Besprechung verfügen](#user-roles-in-teams-meeting).

> [!NOTE]
>
> Wenn derzeit eine dritte Person zu einem 1:1-Anruf hinzugefügt wird, wird der Anruf auf einen Gruppenanruf erhöht, was bedeutet, dass eine neue Sitzung beginnt. Apps, die dem Einzelanruf hinzugefügt wurden, sind im Gruppenanruf nicht verfügbar. Sie können jedoch erneut hinzugefügt werden.

In der folgenden Liste sind die verschiedenen Benutzertypen sowie deren Barrierefreiheit aufgeführt:

* **Mandantenintern**: Mandanteninterne Benutzer gehören zur Organisation und verfügen über Anmeldeinformationen in Azure Active Directory (AAD) für den Mandanten. Sie sind Vollzeit-, Vor-Ort- oder Remotemitarbeiter. Ein mandanteninterner Benutzer kann Organisator, Referent oder Teilnehmer sein.
* **Gast**: Ein Gast ist ein Teilnehmer einer anderen Organisation, die zum Zugriff auf Teams oder andere Ressourcen im Mandanten der Organisation eingeladen wird. Gäste werden dem Azure AD der Organisation hinzugefügt und verfügen über dieselben Teams-Funktionen wie ein natives Teammitglied. Sie haben Zugriff auf Teamchats, Besprechungen und Dateien. Ein Gast kann Organisator, Referent oder Teilnehmer sein. Weitere Informationen finden Sie unter [Gastzugriff in Teams](/microsoftteams/guest-access).
* **Verbund oder extern**: Ein Verbundbenutzer oder ein externer Benutzer ist ein Teams-Benutzer aus einer anderen Organisation, der zur Teilnahme an einer Besprechung eingeladen wurde. Verbundbenutzer verfügen über gültige Anmeldeinformationen bei Verbundpartnern und werden von Teams autorisiert. Sie haben keinen Zugriff auf Ihre Teams oder andere freigegebene Ressourcen aus Ihrer Organisation. Der Gastzugriff ist eine bessere Option für externe Benutzer, um Zugriff auf Teams und Kanäle zu haben. Weitere Informationen finden Sie unter [Verwalten des externen Zugriffs in Teams](/microsoftteams/manage-external-access).

    > [!NOTE]
    > Teams-Benutzer können Apps hinzufügen, wenn sie Besprechungen oder Chats mit anderen Organisationen hosten. Wenn ein externer Benutzer Apps für die Besprechung freigeben, kann der gesamte Benutzer auf die App zugreifen. Die Datenrichtlinien und Datenfreigabepraktiken der Hostorganisation der Drittanbieter-Apps, die von der Organisation dieses Benutzers freigegeben werden, werden wirksam.

* **Anonym**: Anonyme Benutzer verfügen nicht über eine Azure AD-Identität und sind nicht mit einem Mandanten verbunden. Die anonymen Teilnehmer sind wie externe Benutzer, aber ihre Identität wird in der Besprechung nicht angezeigt. Anonyme Benutzer können in einem Besprechungsfenster nicht auf Apps zugreifen. Ein anonymer Benutzer kann das Botlogo im Besprechungschat nicht anzeigen. Ein anonymer Benutzer kann ein Referent oder ein Teilnehmer, aber kein Organisator sein.

    > [!NOTE]
    > Anonyme Benutzer erben die globale Standard-App-Berechtigungsrichtlinie auf Benutzerebene. Weitere Informationen finden Sie unter [Verwalten von Apps](/microsoftteams/non-standard-users#anonymous-user-in-meetings-access).

## <a name="user-roles-in-teams-meeting"></a>Benutzerrollen in Teams-Besprechungen

Im Folgenden sind die Benutzerrollen in einer Teams-Besprechung aufgeführt:

* **Organisator**: Der Organisator plant eine Besprechung, legt die Besprechungsoptionen fest, weist Besprechungsrollen zu, steuert Teilnehmerberechtigungen und startet die Besprechung. Nur Benutzer mit einem Microsoft 365-Konto und einer Teams-Lizenz können der Organisator sein. Ein Besprechungsorganisator kann die Einstellungen für eine bestimmte Besprechung auf der [Seite **Besprechungsoptionen**](https://support.microsoft.com/en-us/office/change-participant-settings-for-a-teams-meeting-53261366-dbd5-45f9-aae9-a70e6354f88e) ändern.

* **Referenten**: Referenten in einer Besprechung verfügen über ähnliche Funktionen wie der Organisator, mit der Ausnahme, dass sie einen Organisator aus der Sitzung entfernen und Besprechungsoptionen für die Sitzung ändern.

* **Teilnehmer**: Ein Teilnehmer ist ein Benutzer, der zur Teilnahme an der Besprechung eingeladen wird. Teilnehmer haben während der Besprechung eingeschränkte Möglichkeiten.

> [!NOTE]
> Nur ein Organisator oder Referent kann Apps hinzufügen, entfernen oder deinstallieren.

Weitere Informationen finden Sie unter [Rollen in einer Teams-Besprechung](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019).

> [!TIP]
>
> * Die [Standardmäßigen Teilnehmereinstellungen](/microsoftteams/meeting-policies-participants-and-guests) werden vom IT-Administrator einer Organisation festgelegt.Gemäß den Standardeinstellungen haben Teilnehmer, die an einer Besprechung teilnehmen, die Referentrolle.
> * Die Referentenrolle ist in Einzelanrufen nicht verfügbar.
> * Ein Benutzer, der den Gruppenanruf über einen Chat startet, gilt als Organisator.

> [!IMPORTANT]
>
> * Derzeit sind Apps von Drittanbietern in Government Community Cloud (GCC) verfügbar, aber nicht für GCC-High- und DOD-Mandanten (Department of Defense).
> * Drittanbieter-Apps sind für GCC standardmäßig deaktiviert. Informationen zum Aktivieren von Drittanbieter-Apps für GCC finden Sie unter [Verwalten von App-Berechtigungsrichtlinien](/microsoftteams/teams-app-permission-policies) und [Verwalten von Apps](/microsoftteams/manage-apps).

## <a name="see-also"></a>Siehe auch

* [Entwerfen eigener Microsoft Teams-Messaging-Erweiterungen](~/apps-in-teams-meetings/design/designing-apps-in-meetings.md)
* [Registerkarten erstellen für Besprechungen](~/apps-in-teams-meetings/build-tabs-for-meeting.md)
* [Erstellen von Apps für die Teams-Besprechungsphase](build-apps-for-teams-meeting-stage.md)
* [Erstellen einer erweiterbaren Unterhaltung für Besprechungschats](build-extensible-conversation-for-meeting-chat.md)
* [Erstellen von Apps für anonyme Benutzer](build-apps-for-anonymous-user.md)
* [Besprechungs-Apps-APIs](meeting-apps-apis.md)
* [Verbesserte Zusammenarbeit mit Live Share SDK](teams-live-share-overview.md)
* [Benutzerdefinierte Zusammen-Modus-Szenen](~/apps-in-teams-meetings/teams-together-mode.md)
