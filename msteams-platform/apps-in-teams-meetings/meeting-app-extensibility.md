---
title: Einheitliche Besprechungs-Apps
author: surbhigupta
description: 'Erfahren Sie mehr über Teams Besprechungslebenszyklus und die Besprechungserfahrung des Benutzers in der Desktop- und mobilen Umgebung, die Rollen und Typen von Teilnehmern und Benutzern, die Integration von Bots und Messaging-Erweiterungen in den Besprechungslebenszyklus.'
ms.topic: conceptual
ms.localizationpriority: none
---

# <a name="unified-meetings-apps"></a>Einheitliche Besprechungs-Apps

Teams einheitlichen Besprechungs-Apps basieren auf den folgenden Konzepten:

* Der Besprechungslebenszyklus besteht aus verschiedenen Phasen mit entsprechenden Freigabefenstern: vor der Besprechung, in der Besprechung und nach der Besprechung.  
* Es gibt drei verschiedene Teilnehmerrollen in einer Besprechung: Organisator, Referent und Teilnehmer. Weitere Informationen finden Sie [unter Rollen in einer Teams-Besprechung](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019).  
* Es gibt verschiedene [Benutzertypen](/microsoftteams/non-standard-users#:~:text=An%20anonymous%20user%20is%20a,their%20Microsoft%20or%20organization's%20account.) in einer Besprechung: Mandanten-, [Gast](/microsoftteams/guest-access)-, [Verbund](/microsoftteams/manage-external-access)- und anonyme Benutzer.

Dieser Artikel behandelt die Informationen zum Besprechungslebenszyklus und zum Integrieren von Registerkarten, Bots und Messaging-Erweiterungen. Es identifiziert verschiedene Teilnehmerrollen und Benutzertypen.

## <a name="meeting-lifecycle"></a>Der Besprechungslebenszyklus

Den Phasen des Besprechungslebenszyklus entsprechen in der App drei Umgebungen: vor der Besprechung, in der Besprechung und nach der Besprechung. Sie können Registerkarten, Bots und Messaging-Erweiterungen in jedes der Freigabefenster des Besprechungslebenszyklus integrieren.

> [!NOTE]
> Besprechungserweiterungen wie Bots, Karten, Nachrichtenerweiterungen und Nachrichtenaktionen werden im Webclient unterstützt. Gehostete Erfahrungen wie Registerkarten, Inhaltsbubblasen und freigabeweise Freigaben werden derzeit jedoch nicht vollständig unterstützt.

### <a name="integrate-tabs-into-the-meeting-lifecycle"></a>Integrieren von Registerkarten in den Besprechungslebenszyklus

Registerkarten ermöglichen es Teammitgliedern, auf Dienste und Inhalte in einem bestimmten Bereich innerhalb einer Besprechung zuzugreifen. Das Team arbeitet direkt mit Registerkarten und unterhält sich über die Tools und Daten, die auf den Registerkarten verfügbar sind. In Teams Besprechung können Sie eine Registerkarte hinzufügen, indem Sie <img src="~/assets/images/apps-in-meetings/plusbutton.png" alt="Plus button" width="30"/>und wählen Sie die App aus, die Sie installieren möchten.

> [!IMPORTANT]
> Wenn Sie eine Registerkarte in Ihre Besprechung integriert haben, muss Ihre App den Teams [SSO-Authentifizierungsfluss (Single Sign-On) für Registerkarten](../tabs/how-to/authentication/auth-aad-sso.md) befolgen.

> [!NOTE]
>
> * Die privaten geplanten Besprechungen unterstützen nur Apps.
> * Die Option "App hinzufügen" für Teams Registerkarte "Besprechungserweiterung" wird in Teams Webclient nicht unterstützt.

#### <a name="pre-meeting-app-experience"></a>Pre-Meeting-App-Umgebung

Über die Pre-Meeting-App-Umgebung können Sie Besprechungs-Apps suchen und hinzufügen. Sie können auch im Vorfeld der Besprechung Dinge erledigen wie z. B. eine Umfrage erstellen, um die Besprechungsteilnehmer über etwas zu befragen.

So fügen Sie einer vorhandenen Besprechung Registerkarten hinzu:

1. Wählen Sie in Ihrem Kalender eine Besprechung aus, der Sie eine Registerkarte hinzufügen möchten.
1. Wählen Sie die Registerkarte **"Details** " aus, und wählen Sie <img src="~/assets/images/apps-in-meetings/plusbutton.png" alt="Plus button" width="30"/>. Der Registerkartenkatalog wird angezeigt.

    :::image type="content" source="~/assets/images/apps-in-meetings/Pre-Meeting-002.png" alt-text="Pre-Meeting-App-Umgebung":::

1. Wählen Sie im Registerkartenkatalog die App aus, die Sie hinzufügen möchten, und führen Sie die erforderlichen Schritte aus. Die App wird als Registerkarte installiert.

   > [!NOTE]
   >
   > * Sie können einer vorhandenen Besprechung auch über die Registerkarte " **Besprechungschat** " eine Registerkarte hinzufügen.
   > * Das Registerkartenlayout muss sich in einem organisierten Zustand befinden, wenn mehr als 10 Umfragen oder Umfragen vorhanden sind.

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="~/assets/images/apps-in-meetings/PreMeetingTab.png" alt-text="Registerkarten während einer Besprechung":::

# <a name="mobile"></a>[Mobil](#tab/mobile)

Nachdem Sie die Registerkarten zu einer vorhandenen Besprechung auf mobilen Geräten hinzugefügt haben, können Sie die gleichen Apps in der Umgebung vor der Besprechung unter **"Weitere** Informationen" der Besprechungsdetails sehen.

<img src="../assets/images/apps-in-meetings/mobilePostMeeting.png" alt="Mobile pre-meeting experience" width="200"/>  

---

#### <a name="in-meeting-app-experience"></a>In-Meeting-App-Umgebung

Über die In-Meeting-App-Umgebung können Sie während der Besprechung mithilfe von Apps und dem Dialogfeld die Teilnehmer einbeziehen. Die Besprechungs-Apps werden auf der Symbolleiste des Besprechungsfensters als Registerkarten in der Besprechung gehostet. Im Dialogfeld in der Besprechung können Aktionen erfordernde Inhalte für Besprechungsteilnehmer angezeigt werden. Weitere Informationen finden Sie unter [Aktivieren und Konfigurieren Ihrer Apps für Teams Besprechungen](enable-and-configure-your-app-for-teams-meetings.md).

Für mobile Geräte sind Besprechungs-Apps über **Apps** > auslassungspunkte &#x25CF;&#x25CF;&#x25CF; in der Besprechung verfügbar. Wählen Sie **"Apps"** aus, um alle in der Besprechung verfügbaren Apps anzuzeigen.

So verwenden Sie Registerkarten während einer Besprechung:

1. Wechseln Sie zu Teams.
1. Wählen Sie in Ihrem Kalender eine Besprechung aus, in der Sie eine Registerkarte verwenden möchten.
1. Wählen Sie nach der Teilnahme an der Besprechung auf der Symbolleiste des Chatfensters die erforderliche App aus.
    Eine App ist in einer Teams Besprechung im Seitenbereich oder im Dialogfeld in der Besprechung sichtbar.
1. Geben Sie im Dialogfeld in der Besprechung Ihre Antwort als Feedback ein.

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="~/assets/images/apps-in-meetings/desktop-in-meeting-dialog-view.png" alt-text="Desktopansicht":::


# <a name="mobile"></a>[Mobil](#tab/mobile)

Nachdem Sie die Besprechung eingegeben und die App über den Desktop oder das Web hinzugefügt haben, ist die App in mobilen Teams Besprechung im Abschnitt **"Apps"** sichtbar. Wählen Sie **"Apps"** aus, um die Liste der Apps anzuzeigen. Der Benutzer kann jede der Apps als besprechungsseitigen Bereich der App starten.

Das Dialogfeld in der Besprechung wird angezeigt, in dem Sie Ihre Antwort als Feedback eingeben können.

<img src="../assets/images/apps-in-meetings/mobile-in-meeting-dialog-view.png" alt="Mobile dialog box view" width="200"/>

> [!NOTE]
> Sie müssen das App-Manifest nicht ändern, damit die Apps auf mobilen Geräten funktionieren.

---

> [!NOTE]
>
> * Apps können das Teams Client SDK nutzen, `userMri`um auf das `meetingId`Client-SDK zuzugreifen und `frameContext` die Oberfläche entsprechend zu rendern.
> * Wenn das Dialogfeld in der Besprechung erfolgreich gerendert wird, wird eine Benachrichtigung gesendet, dass die Ergebnisse erfolgreich heruntergeladen wurden.
> * Ihr App-Manifest gibt die Stellen an, an denen die Apps angezeigt werden sollen. Dies kann durch Angeben des Kontextfelds im Manifest erfolgen. Sie ist auch Teil einer Gemeinsamen Besprechungsphase, die den angegebenen [Entwurfsrichtlinien](~\apps-in-teams-meetings\design\designing-apps-in-meetings.md) unterliegt.

Die folgende Abbildung veranschaulicht den besprechungsinternen Bereich:

# <a name="desktop"></a>[Desktop](#tab/desktop)

![Besprechungsseitiger Bereich](../assets/images/in-meeting-dialog.png)

# <a name="mobile"></a>[Mobil](#tab/mobile)

<img src="../assets/images/apps-in-meetings/sidepanelmobile.png" alt="In-meeting side panel mobile" width="300"/>

---

In der folgenden Tabelle wird das Verhalten der App beschrieben, wenn sie überprüft und nicht überprüft wird:

|App-Funktion | App wird überprüft | App wird nicht überprüft |
|---|---|---|
| Erweiterbarkeit von Besprechungen | Die App wird in Besprechungen angezeigt. | Die App wird nicht in Besprechungen für die mobilen Clients angezeigt. |

Weitere Informationen finden Sie in den [Richtlinien für die Speichervalidierung](../concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md).

#### <a name="post-meeting-app-experience"></a>App-Erfahrung nach der Besprechung

Mit der App-Erfahrung nach der Besprechung können Sie die Ergebnisse der Besprechung anzeigen, z. B. Umfrageergebnisse oder Feedback. Auswählen <img src="~/assets/images/apps-in-meetings/plusbutton.png" alt="Plus button" width="30"/> um eine Registerkarte hinzuzufügen, Besprechungsnotizen abzurufen und die Ergebnisse anzuzeigen, in denen Organisatoren und Teilnehmer maßnahmen ergreifen müssen.

In der folgenden Abbildung wird die Registerkarte **"Contoso** " mit den Ergebnissen der Umfrage und des Feedbacks von Besprechungsteilnehmern angezeigt:

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="~/assets/images/apps-in-meetings/post.png" alt-text="Contoso-Registerkarte mit Ergebnissen":::

# <a name="mobile"></a>[Mobil](#tab/mobile)

:::image type="content" source="~/assets/images/apps-in-meetings/mobilepremeeting.png" alt-text="App-Erfahrung nach besprechungsbesprechung":::

---

> [!NOTE]
> Das Registerkartenlayout muss organisiert werden, wenn mehr als 10 Umfragen oder Umfragen vorhanden sind.

### <a name="integrate-bots-into-the-meeting-lifecycle"></a>Integrieren von Bots in den Besprechungslebenszyklus

Bots, die im Gruppenchatbereich aktiviert sind, funktionieren in Besprechungen. Um Bots zu implementieren, beginnen Sie mit dem [Erstellen eines Bots](../build-your-first-app/build-bot.md), und fahren Sie dann mit dem [Erstellen von Apps für Teams Besprechungen](../apps-in-teams-meetings/API-references.md#meeting-apps-api-references) fort.

### <a name="integrate-messaging-extensions-into-the-meeting-lifecycle"></a>Integrieren von Messaging-Erweiterungen in den Besprechungslebenszyklus

Um die Messaging-Erweiterung zu implementieren, beginnen Sie mit dem [Erstellen einer Messaging-Erweiterung](../messaging-extensions/how-to/create-messaging-extension.md), und fahren Sie dann mit dem [Erstellen von Apps für Teams Besprechungen](../apps-in-teams-meetings/API-references.md#meeting-apps-api-references) fort.

Mit den Teams einheitlichen Besprechungs-Apps können Sie Ihre App basierend auf den Teilnehmerrollen in einer Besprechung entwerfen.

## <a name="participant-roles-in-a-meeting"></a>Teilnehmerrollen in einer Besprechung

:::image type="content" source="~/assets/images/apps-in-meetings/participant-roles.png" alt-text="Teilnehmerrollen in einer Besprechung":::

Die Standardeinstellungen für Teilnehmer werden vom IT-Administrator einer Organisation bestimmt. Es folgen die Teilnehmerrollen in einer Besprechung:

* **Organisator**: Der Organisator plant eine Besprechung, legt die Besprechungsoptionen fest, weist Besprechungsrollen zu und startet die Besprechung. Die Benutzer mit Microsoft 365 Konto und Teams Lizenz können nur die Organisatoren sein und die Teilnehmerberechtigungen steuern. Ein Besprechungsorganisator kann die Einstellungen für eine bestimmte Besprechung ändern. Organisatoren können diese Änderungen auf der **Besprechungsoptionen-Webseite** vornehmen.

* **Referent**: Die Referenten verfügen über die gleichen Funktionen der Organisatoren mit Ausschlüssen. Ein Referent kann einen Organisator nicht aus der Sitzung entfernen oder Besprechungsoptionen für die Sitzung ändern. Standardmäßig haben Teilnehmer, die an einer Besprechung teilnehmen, die Rolle des Referenten.

* **Teilnehmer**: Ein Teilnehmer ist ein Benutzer, der zur Teilnahme an der Besprechung eingeladen wird. Teilnehmer verfügen während der Besprechung über eingeschränkte Funktionen, z. B.:
  * Sie können mit anderen Besprechungsmitgliedern interagieren, aber keine der Besprechungseinstellungen verwalten oder den Inhalt freigeben.  
  * Sie können die Registerkarten-App in der Besprechungsphase anzeigen oder mit ihr interagieren, ohne die App zu installieren oder ohne App-Berechtigungen.
  * Sie können die App im Seitenbereich ohne App-Berechtigungen nicht anzeigen oder mit ihr interagieren.
  * Sie sind nicht berechtigt, als Referent zu fungieren.

> [!NOTE]
> Nur ein Organisator oder Referent kann Apps hinzufügen, entfernen oder deinstallieren.

Weitere Informationen finden Sie [unter Rollen in einer Teams-Besprechung](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019).

Nachdem Sie Ihre App basierend auf den Teilnehmerrollen in einer Besprechung entwerfen, können Sie jeden Benutzertyp für Besprechungen identifizieren und auswählen, auf was er zugreifen kann.

## <a name="user-types-in-a-meeting"></a>Benutzertypen in einer Besprechung

Benutzertypen, z. B. Organisator, Referent oder Teilnehmer an einer Besprechung, können eine der [Teilnehmerrollen in einer Besprechung](#participant-roles-in-a-meeting) ausführen.

> [!NOTE]
> Der Benutzertyp ist nicht in der **getParticipantRole-API** enthalten.

In der folgenden Liste werden die verschiedenen Benutzertypen zusammen mit ihrer Barrierefreiheit und Leistung aufgeführt:

* **Mandanteninterne** Benutzer gehören zur Organisation und verfügen über Anmeldeinformationen in Microsoft Azure Active Directory (Azure AD) für den Mandanten. Es handelt sich um Vollzeit-, Vor-Ort- oder Remotemitarbeiter. Ein mandanteninterner Benutzer kann ein Organisator, Referent oder Teilnehmer sein.
* **Gast**: Ein Gast ist ein Teilnehmer aus einer anderen Organisation, der eingeladen ist, auf Teams oder andere Ressourcen im Mandanten der Organisation zuzugreifen. Gäste werden den Azure AD der Organisation hinzugefügt und verfügen über dieselben Teams Funktionen wie ein systemeigenes Teammitglied. Sie haben Zugriff auf Teamchats, Besprechungen und Dateien. Ein Gast kann ein Organisator, Referent oder Teilnehmer sein. Weitere Informationen finden Sie unter [Gastzugriff in Teams](/microsoftteams/guest-access).
* **Verbunden oder extern**: Ein Verbundbenutzer ist ein externer Teams Benutzer in einer anderen Organisation, der zur Teilnahme an einer Besprechung eingeladen wurde. Verbundbenutzer verfügen über gültige Anmeldeinformationen bei Verbundpartnern und werden von Teams autorisiert. Sie haben keinen Zugriff auf Ihre Teams oder andere freigegebene Ressourcen aus Ihrer Organisation. Der Gastzugriff ist eine bessere Option für externe Benutzer, um Zugriff auf Teams und Kanäle zu haben. Weitere Informationen finden Sie unter [Verwalten des externen Zugriffs in Teams](/microsoftteams/manage-external-access).

    > [!NOTE]
    > Ihre Teams Benutzer können Apps hinzufügen, wenn sie Besprechungen oder Chats mit anderen Organisationen hosten. Die Benutzer können Apps verwenden, die von externen Benutzern freigegeben wurden, wenn Ihre Benutzer an Besprechungen oder Chats teilnehmen, die von anderen Organisationen gehostet werden. Die Datenrichtlinien der Organisation des hostenden Benutzers sowie die Datenfreigabepraktiken der Drittanbieter-Apps, die von der Organisation dieses Benutzers freigegeben werden, werden wirksam.

    > [!IMPORTANT]
    > Derzeit sind Apps von Drittanbietern in Government Community Cloud (GCC) verfügbar, aber nicht für GCC-High und das Verteidigungsministerium (Department of Defense, DOD). Drittanbieter-Apps sind für GCC standardmäßig deaktiviert. Informationen zum Aktivieren von Drittanbieter-Apps für GCC finden Sie unter [Verwalten von App-Berechtigungsrichtlinien](/microsoftteams/teams-app-permission-policies) und [Verwalten von Apps](/microsoftteams/manage-apps).

* **Anonym**: Anonyme Benutzer haben keine Azure AD Identität und sind nicht mit einem Mandanten verbunden. Die anonymen Teilnehmer sind wie externe Benutzer, aber ihre Identität wird in der Besprechung nicht angezeigt. Anonyme Benutzer können in einem Besprechungsfenster nicht auf Apps zugreifen. Ein anonymer Benutzer kann kein Organisator, aber ein Referent oder Teilnehmer sein.

    > [!NOTE]
    > Anonyme Benutzer erben die globale App-Berechtigungsrichtlinie auf Benutzerebene. Weitere Informationen finden Sie unter [Verwalten von Apps](/microsoftteams/non-standard-users#anonymous-user-in-meetings-access).

Ein Gast oder anonymer Benutzer kann keine Apps hinzufügen, entfernen oder deinstallieren.

Die folgende Tabelle enthält die Benutzertypen und listet die Features auf, auf die jeder Benutzer zugreifen kann:

| Benutzertyp | Registerkarten | Bots | Messaging-Erweiterungen | Adaptive Karten | Aufgabenmodule | Dialogfeld "Besprechung" | Besprechungsphase | Inhaltsblase |
| :-- | :-- | :-- | :-- | :-- | :-- | :-- | :-- | :-- |
| Anonymer Benutzer | Nicht verfügbar | Nicht verfügbar | Nicht verfügbar | Interaktionen im Besprechungschat sind zulässig. | Interaktionen im Besprechungschat von einer adaptiven Karte sind zulässig. | Nicht verfügbar | Kann die App in der Besprechungsphase anzeigen und mit ihr interagieren | Nicht verfügbar |
| Gast, Teil des Mandanten-Azure AD | Interaktion ist zulässig. Erstellen, Aktualisieren und Löschen sind nicht zulässig. | Nicht verfügbar | Nicht verfügbar | Interaktionen im Besprechungschat sind zulässig. | Interaktionen im Besprechungschat von einer adaptiven Karte sind zulässig. | Verfügbar | Kann die App in der Besprechungsphase starten, anzeigen und mit ihr interagieren | Verfügbar |
| Partnerbenutzer finden weitere Informationen unter [nicht standardmäßige Benutzer](/microsoftteams/non-standard-users). | Interaktion ist zulässig. Erstellen, Aktualisieren und Löschen sind nicht zulässig. | Interaktion ist zulässig. Das Abrufen, Aktualisieren und Löschen ist nicht zulässig. | Nicht verfügbar | Interaktionen im Besprechungschat sind zulässig. | Interaktionen im Besprechungschat von einer adaptiven Karte sind zulässig. | Nicht verfügbar | Kann die App in der Besprechungsphase starten, anzeigen und mit ihr interagieren | Nicht verfügbar |

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Aktivieren und Konfigurieren Ihrer Apps für Teams Besprechungen](enable-and-configure-your-app-for-teams-meetings.md)

## <a name="see-also"></a>Siehe auch

* [Tab](../tabs/what-are-tabs.md#understand-how-tabs-work)
* [Bot](../bots/what-are-bots.md):
* [Messaging-Erweiterung](../messaging-extensions/what-are-messaging-extensions.md)
* [Entwerfen Ihrer App](../apps-in-teams-meetings/design/designing-apps-in-meetings.md)
