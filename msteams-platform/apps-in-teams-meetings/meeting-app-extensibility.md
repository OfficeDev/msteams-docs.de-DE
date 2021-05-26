---
title: Erweiterbarkeit der Besprechungs-App
author: laujan
description: Verstehen der Erweiterbarkeit der Besprechungs-App
ms.topic: conceptual
ms.openlocfilehash: 96770a6a06d7a4478d8a00a7928c74b38d7b4b2c
ms.sourcegitcommit: 999f5c607671e088ea8a461fa7dbb63f8d61c39b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/25/2021
ms.locfileid: "52649843"
---
# <a name="meeting-app-extensibility"></a>Erweiterbarkeit der Besprechungs-App

Teams der Erweiterung der Besprechungs-App basiert auf den folgenden Konzepten:

* Der Besprechungslebenszyklus hat unterschiedliche Phasen, z. B. vor der Besprechung, in der Besprechung und nach der Besprechung.  
* In einer Besprechung gibt es drei unterschiedliche Teilnehmerrollen: Organisator, Organisator und Teilnehmer. Weitere Informationen finden Sie unter [Rollen in einer Teams Besprechung](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019).  
* Es gibt verschiedene [Benutzertypen](/microsoftteams/non-standard-users#:~:text=An%20anonymous%20user%20is%20a,their%20Microsoft%20or%20organization's%20account.) in einer Besprechung: [Mandanten-,](/microsoftteams/guest-access)Gast-, [Verbund-](/microsoftteams/manage-external-access)und anonyme Benutzer.

Dieser Artikel behandelt Informationen zum Besprechungslebenszyklus und zur Integration von Registerkarten, Bots und Messagingerweiterungen in die Besprechung. Es enthält Informationen zum Identifizieren unterschiedlicher Teilnehmerrollen und unterschiedlicher Benutzertypen zum Ausführen von Aufgaben.

## <a name="meeting-lifecycle"></a>Besprechungslebenszyklus

Der Besprechungslebenszyklus besteht aus app-Erfahrung vor der Besprechung, in der Besprechung und nach der Besprechung. Sie können Registerkarten, Bots und Messagingerweiterungen in jeder Phase des Besprechungslebenszyklus integrieren.

### <a name="integrate-tabs-into-the-meeting-lifecycle"></a>Integrieren von Registerkarten in den Besprechungslebenszyklus

Registerkarten ermöglichen Teammitgliedern den Zugriff auf Dienste und Inhalte in einem bestimmten Bereich innerhalb einer Besprechung. Das Team arbeitet direkt mit Registerkarten und verfügt über Unterhaltungen zu den Tools und Daten, die in Registerkarten verfügbar sind. In Teams können Benutzer eine Registerkarte hinzufügen, indem sie <img src="~/assets/images/apps-in-meetings/plusbutton.png" alt="Plus button" width="30"/>und die App auswählen, die sie installieren möchten.

> [!IMPORTANT]
> Wenn Sie eine Registerkarte in Ihre Besprechung integriert haben, muss Ihre App dem Authentifizierungsfluss Teams einmaliges Anmelden [(Single Sign-On, SSO) für Registerkarten folgen.](../tabs/how-to/authentication/auth-aad-sso.md)

> [!NOTE]
> * Mobile Clients unterstützen Registerkarten nur in Vor- und Nachbesprechungsphasen. Die Besprechungserfahrungen, die im Besprechungsdialogfeld und -panel vorhanden sind, sind derzeit nicht auf Mobilgeräten verfügbar.
> * Apps werden nur in privaten geplanten Besprechungen unterstützt.

#### <a name="pre-meeting-app-experience"></a>App-Erfahrung vor besprechung

Mit der App vor der Besprechung können Sie Besprechungs-Apps finden und hinzufügen und Aufgaben vor der Besprechung ausführen, z. B. das Entwickeln einer Umfrage für Besprechungsteilnehmer.

**So fügen Sie einer vorhandenen Besprechung Registerkarten hinzu**

1. Wählen Sie in Ihrem Kalender eine Besprechung aus, der Sie eine Registerkarte hinzufügen möchten.
1. Wählen Sie die **Registerkarte Details** aus, und wählen Sie <img src="~/assets/images/apps-in-meetings/plusbutton.png" alt="Plus button" width="30"/>. Der Registerkartenkatalog wird angezeigt.

    ![Pre-Meeting-Erfahrung](../assets/images/apps-in-meetings/PreMeeting.png)

1. Wählen Sie im Registerkartenkatalog die App aus, die Sie hinzufügen möchten, und führen Sie die erforderlichen Schritte aus. Die App wird als Registerkarte installiert.

    ![Registerkartenansicht vor der Besprechung](../assets/images/apps-in-meetings/PreMeetingTab.png)

    > [!NOTE]
    > * Sie können auch eine Registerkarte mithilfe der Registerkarte **Besprechungschat** in einer vorhandenen Besprechung hinzufügen.
    > * Das Registerkartenlayout muss sich in einem organisierten Zustand befinden, wenn mehr als zehn Umfragen oder Umfragen durchgeführt werden.

#### <a name="in-meeting-app-experience"></a>In-Meeting-App-Erfahrung

Mit der In-Meeting-App können Sie Die Teilnehmer während der Besprechung mithilfe von Apps und dem Dialogfeld in der Besprechung engagieren. Besprechungs-Apps werden in der oberen Leiste des Besprechungsfensters als Registerkarte in Besprechungen gehostet. Verwenden Sie das Dialogfeld in der Besprechung, um aktionenfähige Inhalte für Besprechungsteilnehmer anzuzeigen. Weitere Informationen finden Sie unter [Erstellen von Apps für Teams Besprechungen.](create-apps-for-teams-meetings.md)

**So verwenden Sie Registerkarten während einer Besprechung**

1. Nachdem Sie die Besprechung betreten haben, wählen Sie in der oberen Leiste des Chatfensters die App aus, die Sie verwenden möchten. Eine App ist in einer Teams im Seitenbereich oder im Dialogfeld in der Besprechung sichtbar.
1. Geben Sie im Dialogfeld In-Meeting Ihre Antwort als Feedback ein.

    ![Dialogfeldansicht](../assets/images/apps-in-meetings/in-meeting-dialog-view.png)

    > [!NOTE]
    > * Apps können das Teams Client SDK nutzen, um auf das , zu zugreifen und die `meetingId` `userMri` `frameContext` Benutzererfahrung entsprechend zu rendern.
    > * Wenn das Dialogfeld in der Besprechung erfolgreich gerendert wird, werden Sie benachrichtigt, dass die Ergebnisse erfolgreich heruntergeladen wurden.
    > * Ihr App-Manifest gibt die Orte an, an denen sie angezeigt werden sollen. Das Kontextfeld wird zu diesem Zweck verwendet. Sie kann auch Teil einer Share-Tray-Erfahrung sein, die den angegebenen Entwurfsrichtlinien unterliegt.

    Die folgende Abbildung veranschaulicht den seitenseitigen Bereich der Besprechung:

    ![Besprechungsseitiger Bereich](../assets/images/apps-in-meetings/in-meeting-dialog.png)

#### <a name="post-meeting-app-experience"></a>App-Erfahrung nach der Besprechung

Mit der App nach der Besprechung können Sie die Ergebnisse der Besprechung anzeigen, z. B. Umfrageergebnisse oder Feedback. Auswählen <img src="~/assets/images/apps-in-meetings/plusbutton.png" alt="Plus button" width="30"/> , um eine Registerkarte hinzuzufügen und Besprechungsnotizen und Ergebnisse zu erhalten, für die Organisatoren und Teilnehmer Maßnahmen ergreifen müssen.

In der folgenden Abbildung wird die **Registerkarte Contoso** mit den Ergebnissen von Umfragen und Feedback angezeigt, die von Besprechungsteilnehmern empfangen wurden:

![Besprechungsansicht veröffentlichen](../assets/images/apps-in-meetings/PostMeeting.png)

> [!NOTE]
> Das Registerkartenlayout muss organisiert sein, wenn mehr als zehn Umfragen oder Umfragen durchgeführt werden.

### <a name="integrate-bots-into-the-meeting-lifecycle"></a>Integrieren von Bots in den Besprechungslebenszyklus

Bots, die im Gruppenchatbereich aktiviert sind, funktionieren in Besprechungen. Um Bots zu implementieren, beginnen Sie mit dem Erstellen [eines Bots](../build-your-first-app/build-bot.md) und dann mit dem Erstellen von [Apps für Teams Besprechungen.](../apps-in-teams-meetings/create-apps-for-teams-meetings.md#meeting-apps-api-references)

### <a name="integrate-messaging-extensions-into-the-meeting-lifecycle"></a>Integrieren von Messagingerweiterungen in den Besprechungslebenszyklus

Um Messagingerweiterungen zu implementieren, beginnen Sie mit dem Erstellen einer [Messagingerweiterung](../messaging-extensions/how-to/create-messaging-extension.md) und dann mit dem Erstellen von Apps [für Teams Besprechungen.](../apps-in-teams-meetings/create-apps-for-teams-meetings.md#meeting-apps-api-references)

Mit Teams der Besprechungs-App können Sie Ihre App basierend auf den Teilnehmerrollen in einer Besprechung entwerfen.

## <a name="participant-roles-in-a-meeting"></a>Teilnehmerrollen in einer Besprechung

![Teilnehmer an einer Besprechung](../assets/images/apps-in-meetings/participant-roles.png)

Die Standardeinstellungen für Teilnehmer werden vom IT-Administrator einer Organisation bestimmt. Es folgen die Teilnehmerrollen in einer Besprechung:

* **Organisator**: Der Organisator plant eine Besprechung, legt die Besprechungsoptionen fest, weist Besprechungsrollen zu und startet die Besprechung. Nur Benutzer mit dem M365-Konto und Teams können Organisator sein und die Teilnehmerberechtigungen steuern. Ein Besprechungsorganisator kann die Einstellungen für eine bestimmte Besprechung ändern. Organisatoren können diese Änderungen auf der Webseite **"Besprechungsoptionen"** vornehmen.
* **Organisator**: Organisatoren verfügen über dieselben Funktionen wie Organisatoren mit Ausschlüssen. Ein Organisator kann keinen Organisator aus der Sitzung entfernen oder Besprechungsoptionen für die Sitzung ändern. Standardmäßig haben Teilnehmer, die an einer Besprechung teilnahmen, die Rolle des Moderators.
* **Teilnehmer**: Ein Teilnehmer ist ein Benutzer, der zur Teilnahme an einer Besprechung eingeladen wurde, aber nicht autorisiert ist, als Moderator zu fungieren. Teilnehmer können mit anderen Besprechungsmitgliedern interagieren, aber keine Besprechungseinstellungen verwalten oder Inhalte freigeben.

> [!NOTE]
> Nur ein Organisator oder Organisator kann Apps hinzufügen, entfernen oder deinstallieren.

Weitere Informationen finden Sie unter [Rollen in einer Teams Besprechung](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019).

Nachdem Sie Ihre App basierend auf Teilnehmerrollen in einer Besprechung entwerfen, können Sie jeden Benutzertyp für Besprechungen identifizieren und auswählen, auf welchen Benutzer sie zugreifen können.

## <a name="user-types-in-a-meeting"></a>Benutzertypen in einer Besprechung

> [!NOTE]
> Der Benutzertyp ist nicht in der **getParticipantRole-API** enthalten.

Benutzertypen, z. B. Organisator, Organisator oder Teilnehmer einer Besprechung, können eine der [Teilnehmerrollen in einer Besprechung ausführen.](#participant-roles-in-a-meeting)

In der folgenden Liste werden die verschiedenen Benutzertypen sowie deren Barrierefreiheit und Leistung aufgeführt:

* **In-tenant:** Mandantenbenutzer gehören der Organisation an und verfügen über Anmeldeinformationen in Azure Active Directory (AAD) für den Mandanten. Es handelt sich in der Regel um Vollzeit-, Standort- oder Remotemitarbeiter. Ein Mandantenbenutzer kann ein Organisator, Organisator oder Teilnehmer sein.
* **Gast**: Ein Gast ist ein Teilnehmer aus einer anderen Organisation, der eingeladen ist, auf Teams oder andere Ressourcen im Mandanten der Organisation zu zugreifen. Gäste werden zum AAD der Organisation hinzugefügt und verfügen über dieselben Teams wie ein systemeigenes Teammitglied mit Zugriff auf Teamchats, Besprechungen und Dateien. Ein Gastbenutzer kann ein Organisator, Organisator oder Teilnehmer sein. Weitere Informationen finden Sie unter [Gastzugriff in Teams](/microsoftteams/guest-access).
* **Partner oder extern:** Ein Verbundbenutzer ist ein externer Teams benutzer in einer anderen Organisation, der zur Teilnahme an einer Besprechung eingeladen wurde. Verbundbenutzer verfügen über gültige Anmeldeinformationen bei Verbundpartnern und sind von Teams. Sie haben keinen Zugriff auf Ihre Teams oder andere freigegebene Ressourcen aus Ihrer Organisation. Der Gastzugriff ist eine bessere Option für externe Benutzer, um Zugriff auf Teams und Kanäle zu haben. Weitere Informationen finden Sie unter [Verwalten des externen Zugriffs in Teams](/microsoftteams/manage-external-access).

    > [!NOTE]
    > Ihre Teams können Apps hinzufügen, wenn sie Besprechungen oder Chats mit anderen Organisationen hosten. Die Benutzer können Apps verwenden, die von externen Benutzern freigegeben werden, wenn Ihre Benutzer an Besprechungen oder Chats teilnehmen, die von anderen Organisationen gehostet werden. Die Datenrichtlinien der Organisation des hostingden Benutzers sowie die Datenfreigabepraktiken der von der Organisation dieses Benutzers gemeinsam genutzten Drittanbieter-Apps werden wirksam.

* **Anonym:** Anonyme Benutzer verfügen nicht über eine AAD-Identität und sind nicht mit einem Mandanten in Verbindung. Die anonymen Teilnehmer sind wie externe Benutzer, ihre Identität wird jedoch nicht in der Besprechung projiziert. Anonyme Benutzer können in einem Besprechungsfenster nicht auf Apps zugreifen. Ein anonymer Benutzer kann kein Organisator sein, aber ein Organisator oder Teilnehmer sein.

    > [!NOTE]
    > Anonyme Benutzer erben die globale Standardmäßige App-Berechtigungsrichtlinie auf Benutzerebene. Weitere Informationen finden Sie unter [Verwalten von Apps](/microsoftteams/non-standard-users#anonymous-user-in-meetings-access).

Ein Gast oder anonymer Benutzer kann keine Apps hinzufügen, entfernen oder deinstallieren.

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
> [Voraussetzungen und API-Verweise für Apps in Teams Besprechungen](create-apps-for-teams-meetings.md)