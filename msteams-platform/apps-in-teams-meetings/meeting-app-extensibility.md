---
title: Erweiterbarkeit der Besprechungs-App
author: laujan
description: Verstehen der Erweiterbarkeit der Besprechungs-App
ms.topic: conceptual
ms.openlocfilehash: 575952555bda288d791862140f7b40ce1792c868
ms.sourcegitcommit: 45c66faef8145abb903ef7118b9fa914c12aba2a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/03/2021
ms.locfileid: "52736754"
---
# <a name="meeting-app-extensibility"></a>Erweiterbarkeit der Besprechungs-App

Die Erweiterbarkeit der Besprechungs-App von Teams basiert auf den folgenden Konzepten:

* Der Besprechungslebenszyklus umfasst verschiedene Phasen, z. B. vor der Besprechung, in der Besprechung und nach der Besprechung.  
* Es gibt drei unterschiedliche Teilnehmerrollen in einer Besprechung: Organisator, Referent und Teilnehmer. Weitere Informationen finden Sie [unter Rollen in einer Teams Besprechung.](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019)  
* Es gibt verschiedene [Benutzertypen](/microsoftteams/non-standard-users#:~:text=An%20anonymous%20user%20is%20a,their%20Microsoft%20or%20organization's%20account.) in einer Besprechung: Mandanten-, [Gast-,](/microsoftteams/guest-access) [Verbund-](/microsoftteams/manage-external-access)und anonyme Benutzer.

In diesem Artikel werden Informationen zum Besprechungslebenszyklus und zum Integrieren von Registerkarten, Bots und Messaging-Erweiterungen in die Besprechung behandelt. Es enthält Informationen zum Identifizieren verschiedener Teilnehmerrollen und verschiedener Benutzertypen zum Ausführen von Aufgaben.

## <a name="meeting-lifecycle"></a>Besprechungslebenszyklus

Der Besprechungslebenszyklus besteht aus der App-Erfahrung vor der Besprechung, in der Besprechung und nach der Besprechung. Sie können Registerkarten, Bots und Messaging-Erweiterungen in jeder Phase des Besprechungslebenszyklus integrieren.

### <a name="integrate-tabs-into-the-meeting-lifecycle"></a>Integrieren von Registerkarten in den Besprechungslebenszyklus

Registerkarten ermöglichen Teammitgliedern den Zugriff auf Dienste und Inhalte in einem bestimmten Raum innerhalb einer Besprechung. Das Team arbeitet direkt mit Registerkarten und hat Unterhaltungen über die Tools und Daten, die auf Registerkarten verfügbar sind. In Teams Besprechung können Benutzer eine Registerkarte hinzufügen, indem sie <img src="~/assets/images/apps-in-meetings/plusbutton.png" alt="Plus button" width="30"/>, und wählen Sie die App aus, die sie installieren möchten.

> [!IMPORTANT]
> Wenn Sie eine Registerkarte in Ihre Besprechung integriert haben, muss Ihre App den Teams [SSO-Authentifizierungsfluss (Single Sign-On) für Registerkarten](../tabs/how-to/authentication/auth-aad-sso.md)befolgen.

> [!NOTE]
> * Mobile Clients unterstützen Registerkarten nur in Vor- und Nachbesprechungsphasen. Die In-Meeting-Umgebungen, die sich im Besprechungsdialogfeld und -panel befinden, sind derzeit nicht auf mobilen Geräten verfügbar.
> * Apps werden nur in privaten geplanten Besprechungen unterstützt.

#### <a name="pre-meeting-app-experience"></a>App-Erfahrung vor der Besprechung

Mit der App-Erfahrung vor der Besprechung können Sie Besprechungs-Apps suchen und hinzufügen und Aufgaben vor der Besprechung ausführen, z. B. die Entwicklung einer Umfrage für Besprechungsteilnehmer.

**So fügen Sie einer vorhandenen Besprechung Registerkarten hinzu**

1. Wählen Sie in Ihrem Kalender eine Besprechung aus, der Sie eine Registerkarte hinzufügen möchten.
1. Wählen Sie die Registerkarte **"Details"** aus, und wählen Sie <img src="~/assets/images/apps-in-meetings/plusbutton.png" alt="Plus button" width="30"/>. Der Registerkartenkatalog wird angezeigt.

    ![Pre-Meeting-Erfahrung](../assets/images/apps-in-meetings/PreMeeting.png)

1. Wählen Sie im Registerkartenkatalog die App aus, die Sie hinzufügen möchten, und führen Sie die erforderlichen Schritte aus. Die App wird als Registerkarte installiert.

    ![Registerkartenansicht vor der Besprechung](../assets/images/apps-in-meetings/PreMeetingTab.png)

    > [!NOTE]
    > * Sie können eine Registerkarte auch mithilfe der Registerkarte **"Besprechungschat"** in einer vorhandenen Besprechung hinzufügen.
    > * Das Registerkartenlayout muss sich in einem organisierten Zustand befinden, wenn mehr als zehn Umfragen oder Umfragen vorhanden sind.

#### <a name="in-meeting-app-experience"></a>App-Erfahrung in Besprechungen

Mit der App-Erfahrung in besprechungsinternen Besprechungen können Sie Teilnehmer während der Besprechung mithilfe von Apps und dem Dialogfeld in der Besprechung einbeziehen. Besprechungs-Apps werden in der oberen Leiste des Besprechungsfensters als Registerkarte in einer Besprechung gehostet. Verwenden Sie das Dialogfeld in der Besprechung, um Aktionen erfordernde Inhalte für Besprechungsteilnehmer anzuzeigen. Weitere Informationen finden Sie unter [Erstellen von Apps für Teams Besprechungen.](create-apps-for-teams-meetings.md)

**So verwenden Sie Registerkarten während einer Besprechung**

1. Wählen Sie nach der Teilnahme an der Besprechung in der oberen Leiste des Chatfensters die App aus, die Sie verwenden möchten. Eine App ist in einer Teams Besprechung im Seitenbereich oder im Dialogfeld in der Besprechung sichtbar.
1. Geben Sie im Dialogfeld in der Besprechung Ihre Antwort als Feedback ein.

    ![Dialogfeldansicht](../assets/images/apps-in-meetings/in-meeting-dialog-view.png)

    > [!NOTE]
    > * Apps können das Teams Client SDK nutzen, um auf das Client-SDK zuzugreifen `meetingId` und die Oberfläche entsprechend zu `userMri` `frameContext` rendern.
    > * Wenn das Dialogfeld in der Besprechung erfolgreich gerendert wird, werden Sie benachrichtigt, dass die Ergebnisse erfolgreich heruntergeladen wurden.
    > * Ihr App-Manifest gibt die Stellen an, an denen sie angezeigt werden sollen. Das Kontextfeld wird zu diesem Zweck verwendet. Es kann auch Teil einer Freigabe-Tray-Erfahrung sein, die den angegebenen Entwurfsrichtlinien unterliegt.

    Die folgende Abbildung veranschaulicht den besprechungsinternen Bereich:

    ![Besprechungsseitiger Bereich](../assets/images/apps-in-meetings/in-meeting-dialog.png)

#### <a name="post-meeting-app-experience"></a>App-Erfahrung nach der Besprechung

Mit der App-Erfahrung nach der Besprechung können Sie die Ergebnisse der Besprechung anzeigen, z. B. Umfrageergebnisse oder Feedback. Auswählen <img src="~/assets/images/apps-in-meetings/plusbutton.png" alt="Plus button" width="30"/> um eine Registerkarte hinzuzufügen und Besprechungsnotizen und -ergebnisse abzurufen, auf die Organisatoren und Teilnehmer maßnahmen ergreifen müssen.

In der folgenden Abbildung wird die Registerkarte **"Contoso"** mit den Ergebnissen der Umfrage und des Feedbacks von Besprechungsteilnehmern angezeigt:

![Ansicht "Besprechung posten"](../assets/images/apps-in-meetings/PostMeeting.png)

> [!NOTE]
> Das Registerkartenlayout muss organisiert werden, wenn mehr als zehn Umfragen oder Umfragen vorhanden sind.

### <a name="integrate-bots-into-the-meeting-lifecycle"></a>Integrieren von Bots in den Besprechungslebenszyklus

Bots, die im Gruppenchatbereich aktiviert sind, funktionieren in Besprechungen. Um Bots zu implementieren, beginnen Sie mit dem [Erstellen eines Bots,](../build-your-first-app/build-bot.md) und fahren Sie dann mit dem Erstellen von [Apps für Teams Besprechungen](../apps-in-teams-meetings/create-apps-for-teams-meetings.md#meeting-apps-api-references)fort.

### <a name="integrate-messaging-extensions-into-the-meeting-lifecycle"></a>Integrieren von Messaging-Erweiterungen in den Besprechungslebenszyklus

Um Messaging-Erweiterungen zu implementieren, beginnen Sie mit dem [Erstellen einer Messaging-Erweiterung,](../messaging-extensions/how-to/create-messaging-extension.md) und fahren Sie dann mit dem [Erstellen von Apps für Teams Besprechungen](../apps-in-teams-meetings/create-apps-for-teams-meetings.md#meeting-apps-api-references)fort.

Die Erweiterbarkeit der Teams Besprechungs-App ermöglicht es Ihnen, Ihre App basierend auf den Teilnehmerrollen in einer Besprechung zu entwerfen.

## <a name="participant-roles-in-a-meeting"></a>Teilnehmerrollen in einer Besprechung

![Teilnehmer an einer Besprechung](../assets/images/apps-in-meetings/participant-roles.png)

Die Standardeinstellungen für Teilnehmer werden vom IT-Administrator einer Organisation bestimmt. Es folgen die Teilnehmerrollen in einer Besprechung:

* **Organisator:** Der Organisator plant eine Besprechung, legt die Besprechungsoptionen fest, weist Besprechungsrollen zu und startet die Besprechung. Nur Benutzer mit M365-Konto und Teams-Lizenz können Organisatoren sein und Teilnehmerberechtigungen steuern. Ein Besprechungsorganisator kann die Einstellungen für eine bestimmte Besprechung ändern. Organisatoren können diese Änderungen auf der **Besprechungsoptionen-Webseite** vornehmen.
* **Referent:** Referenten verfügen über die gleichen Funktionen von Organisatoren mit Ausschlüssen. Ein Referent kann einen Organisator nicht aus der Sitzung entfernen oder Besprechungsoptionen für die Sitzung ändern. Standardmäßig haben Teilnehmer, die an einer Besprechung teilnehmen, die Rolle des Referenten.
* **Teilnehmer:** Ein Teilnehmer ist ein Benutzer, der zur Teilnahme an einer Besprechung eingeladen wurde, aber nicht berechtigt ist, als Referent zu fungieren. Teilnehmer können mit anderen Besprechungsmitgliedern interagieren, aber keine besprechungseinstellungen verwalten oder Inhalte freigeben.

> [!NOTE]
> Nur ein Organisator oder Referent kann Apps hinzufügen, entfernen oder deinstallieren.

Weitere Informationen finden Sie [unter Rollen in einer Teams Besprechung.](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019)

Nachdem Sie Ihre App basierend auf den Teilnehmerrollen in einer Besprechung entwerfen, können Sie jeden Benutzertyp für Besprechungen identifizieren und auswählen, auf was er zugreifen kann.

## <a name="user-types-in-a-meeting"></a>Benutzertypen in einer Besprechung

> [!NOTE]
> Der Benutzertyp ist nicht in der **getParticipantRole-API** enthalten.

Benutzertypen, z. B. Organisator, Referent oder Teilnehmer in einer Besprechung, können eine der [Teilnehmerrollen in einer Besprechung](#participant-roles-in-a-meeting)ausführen.

In der folgenden Liste werden die verschiedenen Benutzertypen zusammen mit ihrer Barrierefreiheit und Leistung beschrieben:

* **Mandanteninterne** Benutzer: Mandanteninterne Benutzer gehören zur Organisation und verfügen über Anmeldeinformationen in Azure Active Directory (AAD) für den Mandanten. Sie sind in der Regel Vollzeit-, Vor-Ort- oder Remotemitarbeiter. Ein mandanteninterner Benutzer kann ein Organisator, Referent oder Teilnehmer sein.
* **Gast:** Ein Gast ist ein Teilnehmer aus einer anderen Organisation, der eingeladen ist, auf Teams oder andere Ressourcen im Mandanten der Organisation zuzugreifen. Gäste werden dem AAD der Organisation hinzugefügt und verfügen über dieselben Teams Funktionen wie ein systemeigenes Teammitglied mit Zugriff auf Teamchats, Besprechungen und Dateien. Ein Gastbenutzer kann ein Organisator, Referent oder Teilnehmer sein. Weitere Informationen finden Sie unter [Gastzugriff in Teams.](/microsoftteams/guest-access)
* **Partner oder extern:** Ein Verbundbenutzer ist ein externer Teams Benutzer in einer anderen Organisation, der zur Teilnahme an einer Besprechung eingeladen wurde. Verbundbenutzer verfügen über gültige Anmeldeinformationen bei Verbundpartnern und sind von Teams autorisiert. Sie haben keinen Zugriff auf Ihre Teams oder andere freigegebene Ressourcen aus Ihrer Organisation. Der Gastzugriff ist eine bessere Option für externe Benutzer, um Zugriff auf Teams und Kanäle zu haben. Weitere Informationen finden Sie unter [Verwalten des externen Zugriffs in Teams.](/microsoftteams/manage-external-access)

    > [!NOTE]
    > Ihre Teams Benutzer können Apps hinzufügen, wenn sie Besprechungen oder Chats mit anderen Organisationen hosten. Die Benutzer können Apps verwenden, die von externen Benutzern freigegeben wurden, wenn Ihre Benutzer an Besprechungen oder Chats teilnehmen, die von anderen Organisationen gehostet werden. Die Datenrichtlinien der Organisation des hostenden Benutzers sowie die Datenfreigabepraktiken der Drittanbieter-Apps, die von der Organisation dieses Benutzers freigegeben werden, werden wirksam.

* **Anonym:** Anonyme Benutzer haben keine AAD-Identität und sind nicht mit einem Mandanten verbunden. Die anonymen Teilnehmer sind wie externe Benutzer, ihre Identität wird jedoch nicht in der Besprechung projiziert. Anonyme Benutzer können in einem Besprechungsfenster nicht auf Apps zugreifen. Ein anonymer Benutzer kann kein Organisator, aber ein Referent oder Teilnehmer sein.

    > [!NOTE]
    > Anonyme Benutzer erben die globale App-Berechtigungsrichtlinie auf Benutzerebene. Weitere Informationen finden Sie unter [Verwalten von Apps.](/microsoftteams/non-standard-users#anonymous-user-in-meetings-access)

Ein Gast oder anonymer Benutzer kann keine Apps hinzufügen, entfernen oder deinstallieren.

Die folgende Tabelle enthält die Benutzertypen und die Features, auf die jeder Benutzer zugreifen kann:

| Benutzertyp | Registerkarten | Bots | Messaging-Erweiterungen | Adaptive Karten | Aufgabenmodule | Dialogfeld "Besprechung" |
| :-- | :-- | :-- | :-- | :-- | :-- | :-- |
| Anonymer Benutzer | Nicht verfügbar | Nicht verfügbar | Nicht verfügbar | Interaktionen im Besprechungschat sind zulässig. | Interaktionen im Besprechungschat von einer adaptiven Karte sind zulässig. | Nicht verfügbar |
| Gast, der Teil des Mandanten-AAD ist | Interaktion ist zulässig. Das Erstellen, Aktualisieren und Löschen ist nicht zulässig. | Nicht verfügbar | Nicht verfügbar | Interaktionen im Besprechungschat sind zulässig. | Interaktionen im Besprechungschat von einer adaptiven Karte sind zulässig. | Available |
| Verbundbenutzer. Weitere Informationen finden Sie unter [nicht standardmäßige Benutzer.](/microsoftteams/non-standard-users) | Interaktion ist zulässig. Das Erstellen, Aktualisieren und Löschen ist nicht zulässig. | Interaktion ist zulässig. Das Abrufen, Aktualisieren und Löschen ist nicht zulässig. | Nicht verfügbar | Interaktionen im Besprechungschat sind zulässig. | Interaktionen im Besprechungschat von einer adaptiven Karte sind zulässig. | Nicht verfügbar |

## <a name="see-also"></a>Mehr dazu

* [Tab](../tabs/what-are-tabs.md#understand-how-tabs-work)
* [Bot](../bots/what-are-bots.md)
* [Messaging-Erweiterung](../messaging-extensions/what-are-messaging-extensions.md)
* [Entwerfen Ihrer App](../apps-in-teams-meetings/design/designing-apps-in-meetings.md)

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Voraussetzungen und API-Verweise für Apps in Teams-Besprechungen](create-apps-for-teams-meetings.md)