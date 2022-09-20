---
title: Einheitliche Besprechungs-Apps
author: surbhigupta
description: Erfahren Sie mehr über den Besprechungslebenszyklus, die Erstellung der Besprechungserfahrung des Benutzers während des gesamten Besprechungslebenszyklus in der Desktop- und mobilen Umgebung, Teilnehmerrollen und Benutzertypen. Darüber hinaus erfahren Sie mehr über die Integration von Bots und Nachrichtenerweiterungen in den Besprechungslebenszyklus.
ms.topic: conceptual
ms.localizationpriority: none
ms.author: surbhigupta
ms.date: 04/07/2022
ms.openlocfilehash: 4807b85ed1b520b84701bcd727fda88cf77808eb
ms.sourcegitcommit: 08bd7f1b9c654b95d3639ca88052c9ca9a8c3f67
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/20/2022
ms.locfileid: "67833673"
---
# <a name="unified-meetings-apps"></a>Einheitliche Besprechungs-Apps

Teams-Apps für einheitliche Besprechungen basieren auf den folgenden Konzepten:

* Der Besprechungslebenszyklus besteht aus verschiedenen Phasen mit entsprechenden Freigabefenstern: vor der Besprechung, in der Besprechung und nach der Besprechung.  
* Es gibt drei verschiedene Teilnehmerrollen in einer Besprechung: Organisator, Referent und Teilnehmer. Weitere Informationen finden Sie unter [Rollen in einer Teams-Besprechung](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019).  
* Es gibt verschiedene [Benutzertypen](/microsoftteams/non-standard-users#:~:text=An%20anonymous%20user%20is%20a,their%20Microsoft%20or%20organization's%20account.) in einer Besprechung: Mandantenspezifische, [Gast](/microsoftteams/guest-access)-, [Verbund](/microsoftteams/manage-external-access)- und anonyme Benutzer.

In diesem Artikel werden die Informationen zum Lebenszyklus von Besprechungen und zum Integrieren von Registerkarten, Bots und Nachrichtenerweiterungen behandelt. Es identifiziert verschiedene Teilnehmerrollen und Benutzertypen.

## <a name="meeting-lifecycle"></a>Der Besprechungslebenszyklus

Den Phasen des Besprechungslebenszyklus entsprechen in der App drei Umgebungen: vor der Besprechung, in der Besprechung und nach der Besprechung. Sie können Registerkarten, Bots und Nachrichtenerweiterungen in jeder Phase des Besprechungslebenszyklus integrieren.

> [!NOTE]
>
> * Apps für Sofortbesprechungen, geplante Besprechungen im öffentlichen Kanal, Einzel- und Gruppenanrufe sind derzeit nur in der [öffentlichen Entwicklervorschau](../resources/dev-preview/developer-preview-intro.md) verfügbar.
>
> * Besprechungserweiterungen wie Bots, Karten, Nachrichtenerweiterungen und Nachrichtenaktionen werden im Webclient unterstützt. Gehostete Benutzeroberflächen wie Registerkarten, Inhaltsblasen und Freigabe für Die Stufe werden derzeit jedoch nicht vollständig unterstützt.

### <a name="integrate-tabs-into-the-meeting-lifecycle"></a>Integrieren von Registerkarten in den Besprechungslebenszyklus

Registerkarten ermöglichen es Teammitgliedern, auf Dienste und Inhalte in einem bestimmten Bereich innerhalb einer Besprechung zuzugreifen. Das Team arbeitet direkt mit Registerkarten und unterhält sich über die Tools und Daten, die auf den Registerkarten verfügbar sind. In Teams-Besprechungen können Sie eine Registerkarte hinzufügen, indem Sie <img src="~/assets/images/apps-in-meetings/plusbutton.png" alt="Plus button" width="30"/>aus, und wählen Sie die App aus, die Sie installieren möchten.

> [!IMPORTANT]
> Wir empfehlen Ihnen, den [SSO-Authentifizierungsfluss (Single Sign-On, Einmaliges Anmelden) von Teams für Registerkarten](../tabs/how-to/authentication/tab-sso-overview.md) zu befolgen, wenn Sie eine Registerkarten-App in Ihre Besprechung integriert haben.

> [!NOTE]
> Die Option "App hinzufügen" für die Registerkarten-App der Teams-Besprechungserweiterung wird im Teams-Webclient nicht unterstützt.

#### <a name="pre-meeting-app-experience"></a>Pre-Meeting-App-Umgebung

Über die Pre-Meeting-App-Umgebung können Sie Besprechungs-Apps suchen und hinzufügen. Sie können auch im Vorfeld der Besprechung Dinge erledigen wie z. B. eine Umfrage erstellen, um die Besprechungsteilnehmer über etwas zu befragen.

#### <a name="to-add-tabs-to-an-existing-meeting"></a>So fügen Sie einer vorhandenen Besprechung Registerkarten hinzu

1. Wählen Sie in Ihrem Kalender eine Besprechung aus, der Sie eine Registerkarte hinzufügen möchten.
1. Wählen Sie die Registerkarte **Details** aus, und wählen Sie <img src="~/assets/images/apps-in-meetings/plusbutton.png" alt="Plus button" width="30"/>. Der Registerkartenkatalog wird angezeigt.

    :::image type="content" source="~/assets/images/apps-in-meetings/PreMeeting.png" alt-text="App-Erfahrung vor der Besprechung.":::

1. Wählen Sie im Registerkartenkatalog die App aus, die Sie hinzufügen möchten, und führen Sie die erforderlichen Schritte aus. Die App wird als Registerkarte installiert.

   > [!NOTE]
   > Sie können einer vorhandenen Besprechung auch eine Registerkarte hinzufügen, indem Sie die Registerkarte " **Besprechungschat** " verwenden.

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="~/assets/images/apps-in-meetings/PreMeetingTab.png" alt-text="Registerkarten während einer Besprechung.":::

# <a name="mobile"></a>[Mobil](#tab/mobile)

Nachdem Sie die Registerkarten zu einer vorhandenen Besprechung auf mobilgeräten hinzugefügt haben, können Sie dieselben Apps in der Pre-Meeting-Erfahrung unter **"Weitere** " der Besprechungsdetails sehen.

:::image type="content" source="~/assets/images/apps-in-meetings/mobilepremeeting.png" alt-text="Mobiles Vorbesprechungserlebnis":::

---

#### <a name="in-meeting-app-experience"></a>In-Meeting-App-Umgebung

Über die In-Meeting-App-Umgebung können Sie während der Besprechung mithilfe von Apps und dem Dialogfeld die Teilnehmer einbeziehen. Die Besprechungs-Apps werden auf der Symbolleiste des Besprechungsfensters als Registerkarten in der Besprechung gehostet. Im Dialogfeld in der Besprechung können Aktionen erfordernde Inhalte für Besprechungsteilnehmer angezeigt werden. Weitere Informationen finden Sie unter ["Erstellen von Apps für Teams-Besprechungen](create-apps-for-teams-meetings.md)".

Für mobile Apps sind Besprechungs-Apps über **Apps** > Auslassungszeichen &#x25CF;&#x25CF;&#x25CF; in der Besprechung verfügbar. Wählen Sie **"Apps** " aus, um alle in der Besprechung verfügbaren Apps anzuzeigen.

Für Desktops können Sie Apps während einer Besprechung mithilfe **der Option "App** :::image type="icon" source="../assets/icons/add-icon.png" border="false"::: hinzufügen" aus dem Besprechungsfenster hinzufügen.

So verwenden Sie Registerkarten während einer Besprechung:

1. Wechseln Sie zu Teams.
1. Wählen Sie in Ihrem Kalender eine Besprechung aus, in der Sie eine Registerkarte verwenden möchten.
1. Nachdem Sie die Besprechung betreten haben, wählen Sie auf der Symbolleiste des Chatfensters die erforderliche App aus.
    Eine App ist in einer Teams-Besprechung im Seitlichen Bereich oder im Dialogfeld "In-Besprechung" sichtbar.
1. Geben Sie im Dialogfeld "Besprechung" Ihre Antwort als Feedback ein.

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="~/assets/images/apps-in-meetings/desktop-in-meeting-dialog-view.png" alt-text="Desktop in der Besprechungsansicht.":::

# <a name="mobile"></a>[Mobil](#tab/mobile)

Nachdem Sie die Besprechung betreten und die App über den Desktop oder das Web hinzugefügt haben, ist die App in der mobilen Teams-Besprechung unter dem Abschnitt **"Apps** " sichtbar. Wählen Sie **"Apps** " aus, um die Liste der Apps anzuzeigen. Benutzer können jede der Apps als Besprechungsseite der App starten.

Das Dialogfeld "In der Besprechung" wird angezeigt, in dem Sie Ihre Antwort als Feedback eingeben können.

:::image type="content" source="~/assets/images/apps-in-meetings/mobile-in-meeting-dialog-view.png" alt-text="Mobile Dialogfeldansicht":::

> [!NOTE]
> Sie müssen das App-Manifest nicht ändern, damit die Apps auf mobilgeräten funktionieren.

---

> [!NOTE]
>
> * Apps können das Teams-Client-SDK nutzen, um auf die `meetingId``userMri`App zuzugreifen und `frameContext` die Umgebung entsprechend zu rendern.
> * Wenn das Dialogfeld in der Besprechung erfolgreich gerendert wird, wird eine Benachrichtigung gesendet, dass die Ergebnisse erfolgreich heruntergeladen wurden.
> * Ihr App-Manifest gibt die Orte an, an denen die Apps angezeigt werden sollen. Dies kann durch Angeben des Kontextfelds im Manifest erfolgen. Sie ist auch Teil einer Freigabe-Besprechungsphase, die den [angegebenen Entwurfsrichtlinien](~\apps-in-teams-meetings\design\designing-apps-in-meetings.md) unterliegt.

Die folgende Abbildung veranschaulicht den Besprechungsseitenbereich:

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="~/assets/images/apps-in-meetings/in-meeting-dialog1.png" alt-text="Besprechungsseitiger Bereich":::

# <a name="mobile"></a>[Mobil](#tab/mobile)

:::image type="content" source="~/assets/images/apps-in-meetings/sidepanelmobile.png" alt-text="In-Meeting Side Panel mobilel":::

---

In der folgenden Tabelle wird das Verhalten der App beschrieben, wenn sie überprüft und nicht überprüft wird:

|App-Funktion | Die App wird überprüft. | Die App wurde nicht überprüft. |
|---|---|---|
| Erweiterbarkeit von Besprechungen | Die App wird in Besprechungen angezeigt. | Die App wird nicht in Besprechungen für die mobilen Clients angezeigt. |

Weitere Informationen finden Sie in den [Richtlinien für die Speicherüberprüfung](../concepts/deploy-and-publish/appsource/prepare/teams-store-validation-guidelines.md).

#### <a name="post-meeting-app-experience"></a>App-Erfahrung nach der Besprechung

Mit der App-Erfahrung nach der Besprechung können Sie die Ergebnisse der Besprechung anzeigen, z. B. Umfrageergebnisse oder Feedback. Auswählen <img src="~/assets/images/apps-in-meetings/plusbutton.png" alt="Plus button" width="30"/> um eine Registerkarte hinzuzufügen, Besprechungsnotizen abzurufen und die Ergebnisse anzuzeigen, in denen Organisatoren und Teilnehmer Maßnahmen ergreifen müssen.

In der folgenden Abbildung wird die Registerkarte **"Contoso** " mit Ergebnissen der Umfrage und des Feedbacks angezeigt, die von den Besprechungsteilnehmern empfangen wurden:

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="~/assets/images/apps-in-meetings/post.png" alt-text="Registerkarte &quot;Contoso&quot; mit Ergebnissen.":::

# <a name="mobile"></a>[Mobil](#tab/mobile)

:::image type="content" source="~/assets/images/apps-in-meetings/mobilepremeeting.png" alt-text="App-Erfahrung nach der Besprechung.":::

---

#### <a name="apps-in-channel-meeting"></a>Apps in Kanalbesprechungen

Eine öffentliche geplante Kanalbesprechung verfügt über die gleiche Liste von Apps wie das übergeordnete Team. Durch das Installieren einer App in einer Kanalbesprechung wird sie auch im übergeordneten Team zur Verfügung gestellt und umgekehrt.

Die Registerkarteninstanzen in einer Kanalbesprechung sind jedoch von den Registerkarten im Kanal selbst getrennt. Angenommen, ein "Entwicklungskanal" verfügt über eine Registerkarte "Polly". Wenn Sie eine "Standup"-Besprechung in diesem Kanal erstellen, würde diese Besprechung keine "Polly"-Registerkarte haben, bis Sie [die Registerkarte explizit zur Besprechung hinzufügen](#to-add-tabs-to-an-existing-meeting).

In öffentlichen geplanten Kanalbesprechungen kann nach dem Hinzufügen einer Besprechungsregisterkarte über die Seite "Besprechungsdetails" durch Auswählen des Besprechungsobjekts darauf zugegriffen werden. Sehen Sie sich das folgende Beispiel an:

:::image type="content" source="~/assets/images/apps-in-meetings/after-a-meeting1.png" alt-text="Nach einer Besprechung":::

### <a name="integrate-bots-into-the-meeting-lifecycle"></a>Integrieren von Bots in den Besprechungslebenszyklus

Bots, die im `groupchat` Bereich aktiviert sind, funktionieren in Besprechungen. Um Bots zu implementieren, beginnen Sie mit [dem Erstellen eines Bots](../build-your-first-app/build-bot.md) , und fahren Sie dann mit dem [Erstellen von Apps für Teams-Besprechungen](../apps-in-teams-meetings/API-references.md#meeting-apps-api-references) fort.

### <a name="integrate-message-extensions-into-the-meeting-lifecycle"></a>Integrieren von Nachrichtenerweiterungen in den Besprechungslebenszyklus

Um die Nachrichtenerweiterung zu implementieren, beginnen [Sie mit dem Erstellen einer Nachrichtenerweiterung](../messaging-extensions/how-to/create-messaging-extension.md), und fahren Sie dann mit dem [Erstellen von Apps für Teams-Besprechungen](../apps-in-teams-meetings/API-references.md#meeting-apps-api-references) fort.

Die Teams-Apps für einheitliche Besprechungen ermöglichen es Ihnen, Ihre App basierend auf Teilnehmerrollen in einer Besprechung zu entwerfen.

## <a name="participant-roles-in-a-meeting"></a>Teilnehmerrollen in einer Besprechung

:::image type="content" source="~/assets/images/apps-in-meetings/participant-roles.png" alt-text="Teilnehmerrollen in einer Besprechung.":::

Die Standardeinstellungen für Teilnehmer werden vom IT-Administrator einer Organisation bestimmt. Im Folgenden sind die Teilnehmerrollen in einer Besprechung aufgeführt:

* **Organisator: Der** Organisator plant eine Besprechung, legt die Besprechungsoptionen fest, weist Besprechungsrollen zu und startet die Besprechung. Nur Benutzer mit Microsoft 365-Konto und Teams-Lizenz können Organisatoren sein und die Teilnehmerberechtigungen steuern. Ein Besprechungsorganisator kann die Einstellungen für eine bestimmte Besprechung ändern. Organisatoren können diese Änderungen auf der Webseite " **Besprechungsoptionen"** vornehmen.
* **Referent**: Referenten verfügen über dieselben Funktionen von Organisatoren mit Ausschlüssen. Ein Referent kann einen Organisator nicht aus der Sitzung entfernen oder Besprechungsoptionen für die Sitzung ändern. Standardmäßig haben Teilnehmer, die an einer Besprechung teilnehmen, die Referentenrolle.
* **Teilnehmer**: Ein Teilnehmer wird zur Teilnahme an einer Besprechung eingeladen, kann aber nicht als Referent fungieren. Teilnehmer können mit anderen Besprechungsmitgliedern interagieren, aber keine der Besprechungseinstellungen verwalten oder den Inhalt freigeben.

> [!NOTE]
> Nur ein Organisator oder Referent kann Apps hinzufügen, entfernen oder deinstallieren.

Weitere Informationen finden Sie unter [Rollen in einer Teams-Besprechung](https://support.microsoft.com/office/roles-in-a-teams-meeting-c16fa7d0-1666-4dde-8686-0a0bfe16e019).

Nachdem Sie Ihre App basierend auf Teilnehmerrollen in einer Besprechung erstellt haben, können Sie jeden Benutzertyp für Besprechungen identifizieren und auswählen, worauf er zugreifen kann.

## <a name="user-types-in-a-meeting"></a>Benutzertypen in einer Besprechung

Benutzertypen wie Mandanten-, Gast-, Verbund- oder externe Benutzer in einer Besprechung können eine der [Teilnehmerrollen in einer Besprechung](#participant-roles-in-a-meeting) ausführen.

> [!NOTE]
> Der Benutzertyp ist nicht in der **getParticipantRole-API** enthalten.

Benutzertypen, z. B. Organisator, Referent oder Teilnehmer an einer Besprechung, können [teilnehmer an einer Besprechung](#participant-roles-in-a-meeting) sein.

In der folgenden Liste werden die verschiedenen Benutzertypen zusammen mit ihrer Barrierefreiheit und Leistung beschrieben:

* **Mandantenindanten**: Mandantenspezifische Benutzer gehören zur Organisation und verfügen über Anmeldeinformationen in Azure Active Directory (AAD) für den Mandanten. Sie sind Vollzeit-, Vor-Ort- oder Remotemitarbeiter. Ein Mandantenbenutzer kann ein Organisator, Referent oder Teilnehmer sein.
* **Gast**: Ein Gast ist ein Teilnehmer aus einer anderen Organisation, der eingeladen wurde, auf Teams oder andere Ressourcen im Mandanten der Organisation zuzugreifen. Gäste werden dem Azure AD der Organisation hinzugefügt und verfügen über dieselben Teams-Funktionen wie ein natives Teammitglied. Sie haben Zugriff auf Teamchats, Besprechungen und Dateien. Ein Gast kann ein Organisator, Referent oder Teilnehmer sein. Weitere Informationen finden Sie [unter Gastzugriff in Teams](/microsoftteams/guest-access).
* **Verbund oder extern**: Ein Verbundbenutzer ist ein externer Teams-Benutzer in einer anderen Organisation, der zur Teilnahme an einer Besprechung eingeladen wurde. Verbundbenutzer verfügen über gültige Anmeldeinformationen bei Verbundpartnern und werden von Teams autorisiert. Sie haben keinen Zugriff auf Ihre Teams oder andere freigegebene Ressourcen aus Ihrer Organisation. Der Gastzugriff ist eine bessere Option für externe Benutzer, um Zugriff auf Teams und Kanäle zu haben. Weitere Informationen finden Sie unter [Verwalten des externen Zugriffs in Teams](/microsoftteams/manage-external-access).

    > [!NOTE]
    > Ihre Teams-Benutzer können Apps hinzufügen, wenn sie Besprechungen oder Chats mit anderen Organisationen hosten. Die Benutzer können Apps verwenden, die von externen Benutzern geteilt werden, wenn Ihre Benutzer an Besprechungen oder Chats teilnehmen, die von anderen Organisationen gehostet werden. Die Datenrichtlinien der Organisation des hostenden Benutzers sowie die Datenfreigabepraktiken der Drittanbieter-Apps, die von der Organisation dieses Benutzers gemeinsam genutzt werden, werden wirksam.

    > [!IMPORTANT]
    > Derzeit sind Drittanbieter-Apps in Government Community Cloud (GCC) verfügbar, aber nicht für GCC-High und Department of Defense (DOD). Drittanbieter-Apps sind für GCC standardmäßig deaktiviert. Informationen zum Aktivieren von Drittanbieter-Apps für GCC finden Sie unter [Verwalten von App-Berechtigungsrichtlinien](/microsoftteams/teams-app-permission-policies) und [Verwalten von Apps](/microsoftteams/manage-apps).

* **Anonym**: Anonyme Benutzer haben keine Azure AD-Identität und sind nicht mit einem Mandanten verbunden. Die anonymen Teilnehmer sind wie externe Benutzer, aber ihre Identität wird in der Besprechung nicht angezeigt. Anonyme Benutzer können in einem Besprechungsfenster nicht auf Apps zugreifen. Ein anonymer Benutzer kann kein Organisator, aber Referent oder Teilnehmer sein.

    > [!NOTE]
    > Anonyme Benutzer erben die globale Standard-App-Berechtigungsrichtlinie auf Benutzerebene. Weitere Informationen finden Sie [unter "Apps verwalten](/microsoftteams/non-standard-users#anonymous-user-in-meetings-access)".

Die folgende Tabelle enthält die Benutzertypen und listet die Features auf, auf die jeder Benutzer in Besprechungen zugreifen kann:

| Benutzertyp | Registerkarten | Bots | Nachrichtenerweiterungen | Adaptive Karten | Aufgabenmodule | Dialogfeld "Besprechung" | Besprechungsphase |
| :-- | :-- | :-- | :-- | :-- | :-- | :-- | :-- |
| Anonymer Benutzer | Nicht verfügbar | Nicht verfügbar | Nicht verfügbar | Interaktionen im Besprechungschat sind zulässig. | Nicht verfügbar | Nicht verfügbar | Nicht verfügbar |
| Gast, Teil des Mandanten Azure AD | Interaktion ist zulässig. Erstellen, Aktualisieren und Löschen sind nicht zulässig. | Nicht verfügbar | Nicht verfügbar | Interaktionen im Besprechungschat sind zulässig. | Interaktionen im Besprechungschat über die adaptive Karte sind zulässig. | Available | Kann die App nur auf dem Teams-Desktopclient und auf mobilen Teams-Geräten starten, anzeigen und mit der App in der Besprechungsphase interagieren. |
| Verbundbenutzer finden weitere Informationen unter [nicht standardmäßigen Benutzern](/microsoftteams/non-standard-users). | Interaktion ist in geplanten Besprechungen zulässig. Erstellen, Aktualisieren und Löschen sind nicht zulässig. | Interaktion ist zulässig. Abrufen, Aktualisieren und Löschen sind nicht zulässig. | Nicht verfügbar | Interaktionen im Besprechungschat sind zulässig. | Interaktionen im Besprechungschat über die adaptive Karte sind zulässig. | Nicht verfügbar | Kann die App nur auf dem Teams-Desktopclient und auf mobilen Teams-Geräten starten, anzeigen und mit der App in der Besprechungsphase interagieren. |

> [!NOTE]
>
> Das Verhalten der verschiedenen Benutzertypen für Apps in Anrufen ist mit dem Verhalten in geplanten Besprechungen identisch, mit Ausnahme der folgenden:
>
> * Verbundbenutzer können in Anrufen nicht mit Registerkarten-Apps interagieren.
> * Wenn Verbundbenutzer einem vorhandenen Anruf mit Mandanten- oder Gastbenutzern hinzugefügt werden, verlieren alle Teilnehmer die Möglichkeit, Apps hinzuzufügen, zu aktualisieren oder zu entfernen. Allerdings können nur die vorhandenen Mandanten- oder Gastbenutzer weiterhin mit den Apps interagieren, die hinzugefügt wurden, bevor Verbundbenutzer zum Anruf eingeladen werden.
> * Auf mobilen Geräten können anonyme Benutzer nicht auf Apps in geplanten Besprechungen im öffentlichen Kanal zugreifen.

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Voraussetzungen und API-Verweise für Apps in Teams-Besprechungen](create-apps-for-teams-meetings.md)

## <a name="see-also"></a>Siehe auch

* [Tab](../tabs/what-are-tabs.md#understand-how-tabs-work)
* [Bot](../bots/what-are-bots.md):
* [Nachrichtenerweiterung](../messaging-extensions/what-are-messaging-extensions.md)
* [Entwerfen Ihrer App](../apps-in-teams-meetings/design/designing-apps-in-meetings.md)
* [Microsoft Teams-Besuchsberichte zu einer Besprechung](/microsoftteams/teams-analytics-and-reports/meeting-attendance-report)
* [Einrichten der Option zur Besprechungsaufzeichnung für OneDrive for Business und SharePoint](/MicrosoftTeams/tmr-meeting-recording-change#set-up-the-meeting-recording-option-for-onedrive-for-business-and-sharepoint)
