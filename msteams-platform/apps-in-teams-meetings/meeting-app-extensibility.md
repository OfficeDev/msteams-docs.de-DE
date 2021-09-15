---
title: Einheitliche Besprechungs-Apps
author: surbhigupta
description: Verstehen von einheitlichen Besprechungs-Apps
ms.topic: conceptual
ms.localizationpriority: none
ms.openlocfilehash: d77187543dd5e4ab774341f30a8a05a41c6a49f2
ms.sourcegitcommit: 72de146d11e81fd9777374dd3915ad290fd07d82
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/15/2021
ms.locfileid: "59360496"
---
# <a name="unified-meetings-apps"></a>Einheitliche Besprechungs-Apps

Teams einheitlichen Besprechungs-Apps basieren auf den folgenden Konzepten:

* Der Besprechungslebenszyklus hat verschiedene Phasen: vor der Besprechung, in der Besprechung und nach der Besprechung.  
* Es gibt drei unterschiedliche Teilnehmerrollen in einer Besprechung: Organisator, Referent und Teilnehmer. Weitere Informationen finden Sie [unter Rollen in einer Teams Besprechung.](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019)  
* Es gibt verschiedene [Benutzertypen](/microsoftteams/non-standard-users#:~:text=An%20anonymous%20user%20is%20a,their%20Microsoft%20or%20organization's%20account.) in einer Besprechung: Mandanten-, [Gast-,](/microsoftteams/guest-access) [Verbund-](/microsoftteams/manage-external-access)und anonyme Benutzer.

> [!VIDEO https://www.youtube-nocookie.com/embed/rrNpFJbxqrg]

Dieser Artikel behandelt die Informationen zum Besprechungslebenszyklus und zum Integrieren von Registerkarten, Bots und Messaging-Erweiterungen. Es identifiziert verschiedene Teilnehmerrollen und Benutzertypen.

## <a name="meeting-lifecycle"></a>Besprechungslebenszyklus

Ein Besprechungslebenszyklus besteht aus der App-Erfahrung vor der Besprechung, in der Besprechung und nach der Besprechung. Sie können Registerkarten, Bots und Messaging-Erweiterungen in jeder Phase des Besprechungslebenszyklus integrieren.

### <a name="integrate-tabs-into-the-meeting-lifecycle"></a>Integrieren von Registerkarten in den Besprechungslebenszyklus

Registerkarten ermöglichen es Teammitgliedern, auf Dienste und Inhalte in einem bestimmten Raum innerhalb einer Besprechung zuzugreifen. Das Team arbeitet direkt mit Registerkarten und hat Unterhaltungen über die Tools und Daten, die auf Registerkarten verfügbar sind. In Teams Besprechung können Sie eine Registerkarte hinzufügen, indem Sie <img src="~/assets/images/apps-in-meetings/plusbutton.png" alt="Plus button" width="30"/>und wählen Sie die App aus, die Sie installieren möchten.

> [!IMPORTANT]
> Wenn Sie eine Registerkarte in Ihre Besprechung integriert haben, muss Ihre App dem Teams [SSO-Authentifizierungsfluss (Single Sign-On) für Registerkarten](../tabs/how-to/authentication/auth-aad-sso.md)folgen.

> [!NOTE]
> * Die privaten geplanten Besprechungen unterstützen nur Apps.
> * Die Option "App hinzufügen" für Teams Registerkarte "Besprechungserweiterung" wird in Teams Webclient nicht unterstützt.

#### <a name="pre-meeting-app-experience"></a>App-Erfahrung vor der Besprechung

Mit der App-Erfahrung vor der Besprechung können Sie Besprechungs-Apps suchen und hinzufügen. Sie können auch Aufgaben vor der Besprechung ausführen, z. B. die Entwicklung einer Umfrage, um die Besprechungsteilnehmer zu befragen.

**So fügen Sie einer vorhandenen Besprechung Registerkarten hinzu**

1. Wählen Sie in Ihrem Kalender eine Besprechung aus, der Sie eine Registerkarte hinzufügen möchten.
1. Wählen Sie die Registerkarte **"Details"** aus, und wählen Sie <img src="~/assets/images/apps-in-meetings/plusbutton.png" alt="Plus button" width="30"/>. Der Registerkartenkatalog wird angezeigt.

    <img src="../assets/images/apps-in-meetings/PreMeeting.png" alt="Pre-meeting experience" width="900"/>

1. Wählen Sie im Registerkartenkatalog die App aus, die Sie hinzufügen möchten, und führen Sie die erforderlichen Schritte aus. Die App wird als Registerkarte installiert.

   > [!NOTE]
   > * Sie können einer vorhandenen Besprechung auch über die Registerkarte **"Besprechungschat"** eine Registerkarte hinzufügen.
   > * Das Registerkartenlayout muss sich in einem organisierten Zustand befinden, wenn mehr als 10 Umfragen oder Umfragen vorhanden sind.

# <a name="desktop"></a>[Desktop](#tab/desktop)

![Registerkartenansicht vor der Besprechung](../assets/images/apps-in-meetings/PreMeetingTab.png)

# <a name="mobile"></a>[Mobil](#tab/mobile)

Nachdem Sie die Registerkarten zu einer vorhandenen Besprechung auf mobilen Geräten hinzugefügt haben, können Sie die gleichen Apps in der Umgebung vor der Besprechung unter **"Weitere** Informationen" der Besprechungsdetails sehen.

<img src="../assets/images/apps-in-meetings/mobilepremeeting.png" alt="Mobile pre-meeting experience" width="200"/>  

---

#### <a name="in-meeting-app-experience"></a>App-Erfahrung in Besprechungen

Mit der App-Erfahrung in besprechungsinternen Besprechungen können Sie Teilnehmer während der Besprechung mithilfe von Apps und dem Dialogfeld in der Besprechung einbeziehen. Besprechungs-Apps werden auf der Symbolleiste des Besprechungsfensters als Registerkarte in der Besprechung gehostet. Verwenden Sie das Dialogfeld in der Besprechung, um Aktionen erfordernde Inhalte für Besprechungsteilnehmer anzuzeigen. Weitere Informationen finden Sie unter [Erstellen von Apps für Teams Besprechungen.](create-apps-for-teams-meetings.md)

Für Mobilgeräte sind Besprechungs-Apps über **Apps** > Auslassungspunkte &#x25CF;&#x25CF;&#x25CF; in der Besprechung verfügbar. Wählen Sie **"Apps"** aus, um alle in der Besprechung verfügbaren Apps anzuzeigen.

**So verwenden Sie Registerkarten während einer Besprechung**

1. Wechseln Sie zu Teams.
1. Wählen Sie in Ihrem Kalender eine Besprechung aus, in der Sie eine Registerkarte verwenden möchten.
1. Wählen Sie nach der Teilnahme an der Besprechung auf der Symbolleiste des Chatfensters die erforderliche App aus.
    Eine App ist in einer Teams Besprechung im Seitenbereich oder im Dialogfeld in der Besprechung sichtbar.
1. Geben Sie im Dialogfeld in der Besprechung Ihre Antwort als Feedback ein.

# <a name="desktop"></a>[Desktop](#tab/desktop)

![Dialogfeldansicht](../assets/images/apps-in-meetings/in-meeting-dialog-view.png)

# <a name="mobile"></a>[Mobil](#tab/mobile)

Nachdem Sie die Besprechung betreten und die App über den Desktop oder das Web hinzugefügt haben, ist die App in mobilen Teams Besprechung im Abschnitt **"Apps"** sichtbar. Wählen Sie **"Apps"** aus, um die Liste der Apps anzuzeigen. Der Benutzer kann jede der Apps als besprechungsseitigen Bereich der App starten.

Das Dialogfeld in der Besprechung wird angezeigt, in dem Sie Ihre Antwort als Feedback eingeben können.

<img src="../assets/images/apps-in-meetings/mobile-in-meeting-dialog-view.png" alt="Mobile dialog box view" width="200"/>

> [!NOTE]
> Sie müssen das App-Manifest nicht ändern, damit die Apps auf mobilen Geräten funktionieren.

---

> [!NOTE]
> * Apps können das Teams Client SDK nutzen, um auf das Client-SDK zuzugreifen `meetingId` und die Oberfläche entsprechend zu `userMri` `frameContext` rendern.
> * Wenn das Dialogfeld in der Besprechung erfolgreich gerendert wird, wird eine Benachrichtigung gesendet, dass die Ergebnisse erfolgreich heruntergeladen wurden.
> * Ihr App-Manifest gibt die Stellen an, an denen die Apps angezeigt werden sollen. Das Kontextfeld wird zu diesem Zweck verwendet. Es ist auch Teil einer Freigabe-Tray-Erfahrung, die den angegebenen Entwurfsrichtlinien unterliegt.

Die folgende Abbildung veranschaulicht den besprechungsinternen Bereich:

# <a name="desktop"></a>[Desktop](#tab/desktop)

![Besprechungsseitiger Bereich](../assets/images/apps-in-meetings/in-meeting-dialog.png)

# <a name="mobile"></a>[Mobil](#tab/mobile)

<img src="../assets/images/apps-in-meetings/sidepanelmobile.png" alt="In-meeting side panel mobile" width="300"/>

---

In der folgenden Tabelle wird das Verhalten der App beschrieben, wenn sie genehmigt und nicht genehmigt wird:

|App-Funktion | App ist genehmigt | App wurde nicht genehmigt |
|---|---|---|
| Erweiterbarkeit von Besprechungen | Die App wird in Besprechungen angezeigt. | Die App wird nicht in Besprechungen für die mobilen Clients angezeigt. |

#### <a name="post-meeting-app-experience"></a>App-Erfahrung nach der Besprechung

Mit der App-Erfahrung nach der Besprechung können Sie die Ergebnisse der Besprechung anzeigen, z. B. Umfrageergebnisse oder Feedback. Auswählen <img src="~/assets/images/apps-in-meetings/plusbutton.png" alt="Plus button" width="30"/> um eine Registerkarte hinzuzufügen, Besprechungsnotizen abzurufen und die Ergebnisse anzuzeigen, in denen Organisatoren und Teilnehmer maßnahmen ergreifen müssen.

In der folgenden Abbildung wird die Registerkarte **"Contoso"** mit den Ergebnissen der Umfrage und des Feedbacks von Besprechungsteilnehmern angezeigt:

# <a name="desktop"></a>[Desktop](#tab/desktop)

![Ansicht "Besprechung posten"](../assets/images/apps-in-meetings/PostMeeting.png)

# <a name="mobile"></a>[Mobil](#tab/mobile)

<img src="../assets/images/apps-in-meetings/mobilePostMeeting.png" alt="Mobile post meeting view" width="200"/>

---

> [!NOTE]
> Das Registerkartenlayout muss organisiert werden, wenn mehr als 10 Umfragen oder Umfragen vorhanden sind.

### <a name="integrate-bots-into-the-meeting-lifecycle"></a>Integrieren von Bots in den Besprechungslebenszyklus

Bots, die im Gruppenchatbereich aktiviert sind, funktionieren in Besprechungen. Um Bots zu implementieren, beginnen Sie mit dem [Erstellen eines Bots,](../build-your-first-app/build-bot.md) und fahren Sie dann mit dem [Erstellen von Apps für Teams Besprechungen](../apps-in-teams-meetings/API-references.md#meeting-apps-api-references)fort.

### <a name="integrate-messaging-extensions-into-the-meeting-lifecycle"></a>Integrieren von Messaging-Erweiterungen in den Besprechungslebenszyklus

Um die Messaging-Erweiterung zu implementieren, beginnen Sie mit dem [Erstellen einer Messaging-Erweiterung,](../messaging-extensions/how-to/create-messaging-extension.md) und fahren Sie dann mit dem Erstellen von [Apps für Teams Besprechungen](../apps-in-teams-meetings/API-references.md#meeting-apps-api-references)fort.

Die Teams einheitlichen Besprechungs-Apps ermöglichen es Ihnen, Ihre App basierend auf den Teilnehmerrollen in einer Besprechung zu entwerfen.

## <a name="participant-roles-in-a-meeting"></a>Teilnehmerrollen in einer Besprechung

![Teilnehmer an einer Besprechung](../assets/images/apps-in-meetings/participant-roles.png)

Die Standardeinstellungen für Teilnehmer werden vom IT-Administrator einer Organisation bestimmt. Es folgen die Teilnehmerrollen in einer Besprechung:

* **Organisator:** Der Organisator plant eine Besprechung, legt die Besprechungsoptionen fest, weist Besprechungsrollen zu und startet die Besprechung. Die Benutzer mit Microsoft 365 Konto und Teams Lizenz können nur die Organisatoren sein und die Teilnehmerberechtigungen steuern. Ein Besprechungsorganisator kann die Einstellungen für eine bestimmte Besprechung ändern. Organisatoren können diese Änderungen auf der **Besprechungsoptionen-Webseite** vornehmen.
* **Referent:** Die Referenten verfügen über die gleichen Funktionen der Organisatoren mit Ausschlüssen. Ein Referent kann einen Organisator nicht aus der Sitzung entfernen oder Besprechungsoptionen für die Sitzung ändern. Standardmäßig haben Teilnehmer, die an einer Besprechung teilnehmen, die Rolle des Referenten.
* **Teilnehmer:** Ein Teilnehmer ist ein Benutzer, der zur Teilnahme an einer Besprechung eingeladen wurde. Die Teilnehmer sind jedoch nicht berechtigt, als Referent zu fungieren. Teilnehmer können mit anderen Besprechungsmitgliedern interagieren, aber keine der Besprechungseinstellungen verwalten oder den Inhalt freigeben.

> [!NOTE]
> Nur ein Organisator oder Referent kann Apps hinzufügen, entfernen oder deinstallieren.

Weitere Informationen finden Sie [unter Rollen in einer Teams Besprechung.](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019)

Nachdem Sie Ihre App basierend auf den Teilnehmerrollen in einer Besprechung entwerfen, können Sie jeden Benutzertyp für Besprechungen identifizieren und auswählen, auf was er zugreifen kann.

## <a name="user-types-in-a-meeting"></a>Benutzertypen in einer Besprechung

Benutzertypen wie Organisator, Referent oder Teilnehmer in einer Besprechung können eine der [Teilnehmerrollen in einer Besprechung](#participant-roles-in-a-meeting)ausführen.

> [!NOTE]
> Der Benutzertyp ist nicht in der **getParticipantRole-API** enthalten.

In der folgenden Liste werden die verschiedenen Benutzertypen zusammen mit ihrer Barrierefreiheit und Leistung aufgeführt:

* **Mandanteninterne** Benutzer gehören zur Organisation und verfügen über Anmeldeinformationen in Azure Active Directory (AAD) für den Mandanten. Es handelt sich um Vollzeit-, Vor-Ort- oder Remotemitarbeiter. Ein mandanteninterner Benutzer kann ein Organisator, Referent oder Teilnehmer sein.
* **Gast:** Ein Gast ist ein Teilnehmer aus einer anderen Organisation, der eingeladen ist, auf Teams oder andere Ressourcen im Mandanten der Organisation zuzugreifen. Gäste werden dem AAD der Organisation hinzugefügt und verfügen über dieselben Teams Funktionen wie ein systemeigenes Teammitglied. Sie haben Zugriff auf Teamchats, Besprechungen und Dateien. Ein Gast kann ein Organisator, Referent oder Teilnehmer sein. Weitere Informationen finden Sie unter [Gastzugriff in Teams.](/microsoftteams/guest-access)
* **Partner oder extern:** Ein Verbundbenutzer ist ein externer Teams Benutzer in einer anderen Organisation, der zur Teilnahme an einer Besprechung eingeladen wurde. Verbundbenutzer verfügen über gültige Anmeldeinformationen bei Verbundpartnern und sind von Teams autorisiert. Sie haben keinen Zugriff auf Ihre Teams oder andere freigegebene Ressourcen aus Ihrer Organisation. Der Gastzugriff ist eine bessere Option für externe Benutzer, um Zugriff auf Teams und Kanäle zu haben. Weitere Informationen finden Sie unter [Verwalten des externen Zugriffs in Teams.](/microsoftteams/manage-external-access)

    > [!NOTE]
    > Ihre Teams Benutzer können Apps hinzufügen, wenn sie Besprechungen oder Chats mit anderen Organisationen hosten. Die Benutzer können Apps verwenden, die von externen Benutzern freigegeben wurden, wenn Ihre Benutzer an Besprechungen oder Chats teilnehmen, die von anderen Organisationen gehostet werden. Die Datenrichtlinien der Organisation des hostenden Benutzers sowie die Datenfreigabepraktiken der Drittanbieter-Apps, die von der Organisation dieses Benutzers freigegeben werden, werden wirksam.

    > [!IMPORTANT]
    > Derzeit sind Apps von Drittanbietern in Government Community Cloud (GCC) verfügbar, aber nicht für GCC-High und das Verteidigungsministerium (Department of Defense, DOD). Drittanbieter-Apps sind für GCC standardmäßig deaktiviert. Informationen zum Aktivieren von Drittanbieter-Apps für GCC finden Sie unter [Verwalten von App-Berechtigungsrichtlinien](/microsoftteams/teams-app-permission-policies) und [Verwalten von Apps.](/microsoftteams/manage-apps)

* **Anonym:** Anonyme Benutzer haben keine AAD-Identität und sind nicht mit einem Mandanten verbunden. Die anonymen Teilnehmer sind wie externe Benutzer, aber ihre Identität wird in der Besprechung nicht angezeigt. Anonyme Benutzer können in einem Besprechungsfenster nicht auf Apps zugreifen. Ein anonymer Benutzer kann kein Organisator, aber ein Referent oder Teilnehmer sein.

    > [!NOTE]
    > Anonyme Benutzer erben die globale App-Berechtigungsrichtlinie auf Benutzerebene. Weitere Informationen finden Sie unter [Verwalten von Apps.](/microsoftteams/non-standard-users#anonymous-user-in-meetings-access)

Ein Gast oder anonymer Benutzer kann keine Apps hinzufügen, entfernen oder deinstallieren.

Die folgende Tabelle enthält die Benutzertypen und listet die Features auf, auf die jeder Benutzer zugreifen kann:

| Benutzertyp | Registerkarten | Bots | Messaging-Erweiterungen | Adaptive Karten | Aufgabenmodule | Dialogfeld "Besprechung" | Besprechungsphase | 
| :-- | :-- | :-- | :-- | :-- | :-- | :-- | :-- |
| Anonymer Benutzer | Nicht verfügbar | Nicht verfügbar | Nicht verfügbar | Interaktionen im Besprechungschat sind zulässig. | Interaktionen im Besprechungschat von einer adaptiven Karte sind zulässig. | Nicht verfügbar | Kann in der Besprechungsphase nicht anzeigen, aber mit der App interagieren |
| Gast, der Teil des Mandanten-AAD ist | Interaktion ist zulässig. Erstellen, Aktualisieren und Löschen sind nicht zulässig. | Nicht verfügbar | Nicht verfügbar | Interaktionen im Besprechungschat sind zulässig. | Interaktionen im Besprechungschat von einer adaptiven Karte sind zulässig. | Available | Kann die App in der Besprechungsphase anzeigen und mit ihr interagieren |
| Verbundbenutzer. Weitere Informationen finden Sie unter [nicht standardmäßige Benutzer.](/microsoftteams/non-standard-users) | Interaktion ist zulässig. Erstellen, Aktualisieren und Löschen sind nicht zulässig. | Interaktion ist zulässig. Das Abrufen, Aktualisieren und Löschen ist nicht zulässig. | Nicht verfügbar | Interaktionen im Besprechungschat sind zulässig. | Interaktionen im Besprechungschat von einer adaptiven Karte sind zulässig. | Nicht verfügbar | Kann die App in der Besprechungsphase anzeigen und mit ihr interagieren |

## <a name="see-also"></a>Siehe auch

* [Tab](../tabs/what-are-tabs.md#understand-how-tabs-work)
* [Bot](../bots/what-are-bots.md)
* [Messaging-Erweiterung](../messaging-extensions/what-are-messaging-extensions.md)
* [Entwerfen Ihrer App](../apps-in-teams-meetings/design/designing-apps-in-meetings.md)

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Voraussetzungen und API-Verweise für Apps in Teams-Besprechungen](create-apps-for-teams-meetings.md)
