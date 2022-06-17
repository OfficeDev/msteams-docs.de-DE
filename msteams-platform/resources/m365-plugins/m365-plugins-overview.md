---
title: Microsoft 365-Plugins
description: In diesem Artikel erhalten Sie Informationen zu Microsoft 365-Plugins, Plug-In-Liste und -Bezeichnungen, Microsoft 365 und One Note-Interaktion und vielem mehr.
ms.topic: Microsoft 365 plugins
ms.localizationpriority: high
ms.author: Surbhigupta
ms.openlocfilehash: 5228803be99d77e24f5cd1731c826b1a28509097
ms.sourcegitcommit: 5070746e736edb4ae77cd3efcb2ab8bb2e5819a0
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/16/2022
ms.locfileid: "66124046"
---
# <a name="microsoft-365-plugins"></a>Microsoft 365-Plugins

Microsoft 365 Plugins ermöglichen die Integration zwischen der Moodle-Website und Teams. Diese Plugins erleichtern es Benutzern, den Kursinhalt zu planen, bereitzustellen und zusammenzuarbeiten. Die Plugins können unabhängig oder in Partnerschaft gemäß den Anforderungen verwendet werden.

## <a name="plugin-list-and-labels"></a>Plugin-Liste und Bezeichnungen

In der folgenden Tabelle sind die Plugins und GitHub-Bezeichnungen aufgeführt, die basierend auf den Anforderungen verwendet werden sollen.

<!--Old content of the table updated and revamped |Plugins to install |Description |GitHub label(s)|
|-----|-----|----|
|[**OpenID Connect**](#openid-connect)|Enable SSO for users who work using both Moodle and Microsoft Teams|auth_oidc|
|• [**OpenID Connect**](#openid-connect) </br> • [**Microsoft 365 integration**](#microsoft-365-integration) |Create Teams instances for each course in Moodle, and sync faculty as owners, and students as team members|• auth_oidc </br> • local_o365|
|• [**OpenID Connect**](#openid-connect) </br> • [**Microsoft 365 integration**](#microsoft-365-integration) </br> • [**Teams Theme**](#microsoft-365-teams-theme)| Remove Moodle blocks and extra chrome within the Moodle iframes for Teams, which applies while mapping courses to Teams instances | • auth_oidc </br> • local_o365 </br> • themeboost_o365teams |
|• [**OpenID Connect**](#openid-connect) </br> • [**Microsoft 365 integration**](#microsoft-365-integration) </br> • [**Microsoft 365 Repository**](#microsoft-365-repository) |Leverage Microsoft 365 OneDrive content for file repositories to reduce storage needs in Moodle | • auth_oidc </br> * local_o365 </br> • repository_office 365|
|• [**OpenID Connect**](#openid-connect) </br> • [**OneNote**](#onenote-integration) </br> • [**OneNote Submissions**](#onenote-integration) </br> • [**OneNote Feedback**](#onenote-integration) | Enable OneNote to be used for assignment, submission and feedback |• auth_oidc </br> • local_onenote </br> • assignsubmission_onenote </br> • assignfeedback_onenote |  
|• [**OpenID Connect**](#openid-connect) </br> • [**Microsoft 365 integration**](#microsoft-365-integration) • [**Microsoft 365 Repository**](#microsoft-365-repository) </br> • [**Microsoft Block**](#microsoft-365-repository) | Enable 365 quick access blocks within Moodle with links to Microsoft 365 collaboration services and install links for Microsoft Office | • auth_oidc </br> • local_o365 </br> • repository_office365 </br> • block_microsoft |
|[**Teams Meeting**](#teams-meetings) | Enable Atto editor in Moodle to create Teams meeting links |atto_teamsmeeting |
|[**oEmbed Filter**](#oembed-filter) | Enable video links in Moodle | Filter_oembed| -->

|Zu installierende Plugins |Beschreibung |GitHub-Bezeichnungen|
|-----|-----|----|
|[**OpenID Connect**](#openid-connect)|Aktiviert SSO für Benutzer, die sowohl Moodle als auch Teams verwenden.|auth_oidc|
|[**Microsoft 365-Integration**](#microsoft-365-integration)|Erstellen Sie Teams-Instanzen für jeden Kurs in Moodle, und synchronisieren Sie Lehrpersonal als Eigentümer und Studierende als Teammitglieder.|local_o365|
|[**Microsoft 365 Repository**](#microsoft-365-repository) |Unterstützt Microsoft 365 OneDrive-Inhalte für Dateiablagen, um den Speicherbedarf in Moodle zu reduzieren.| repository_office 365|
|[**Teams-Besprechung**](#teams-meetings) |Ermöglicht dem Atto-Editor in Moodle das Erstellen von Teams-Besprechungslinks.|atto_teamsmeeting |
|[**Teams-Design**](#microsoft-365-teams-theme)| Entfernen Sie Moodle-Blöcke und zusätzliches Chrom in den Moodle-Iframes für Teams, die beim Zuordnen von Kursen zu Teams-Instanzen gelten.| themeboost_o365teams |
|[**OneNote**](#onenote-integration)| Aktivieren Sie die Verwendung von OneNote für Zuweisung, Übermittlung und Feedback.|local_onenote, assignsubmission_onenote und assignfeedback_onenote </br>|  
|[**Microsoft Block**](#microsoft-block) | Aktiviert Microsoft 365 Schnellzugriffsblöcke in Moodle mit Links zu Microsoft 365-Zusammenarbeitsdiensten und Installationslinks für Microsoft Office.|block_microsoft |
|[**oEmbed-Filter**](#oembed-filter) | Aktivieren Sie Videolinks in Moodle.|Filter_oembed|

Moodle LMS unterstützt die folgenden Plugins:

## <a name="openid-connect"></a>OpenID Connect

Mit dem Open ID Connect-Plug-In können Benutzer alle Websites oder Tools authentifizieren, die die erforderliche Spezifikation unterstützen, und SSO (Single Sign-On-Unterstützung) mit Microsoft Office 365 bereitstellen. Das OpenID Connect-Plugin bietet Institutionen die folgenden Anmeldeoptionen, um ihre spezifischen Anforderungen zu erfüllen:

* Benutzer können ihre Office 365-Anmeldedaten wie E-Mail und Passwort eingeben, um sich direkt anzumelden, oder sich mit den Moodle-Benutzernamen- und Passwortfeldern anmelden, ohne sich bei Office 365 anzumelden.
* Benutzer können den Link auswählen, um sich über Office 365 oder den OpenID Connect-Anbieter auf der Moodle-Seite anzumelden.

Die folgende Abbildung zeigt die OpenID Connect-Anmeldeseite:

:::image type="content" source="../../assets/images/MoodleInstructions/openid-connect.png" alt-text="Anmelden bei open-id connect" border="true":::

## <a name="microsoft-365-integration"></a>Microsoft 365-Integration

Die Microsoft 365-Integration besteht aus mehreren Apps mit mehreren Funktionen, sodass Benutzer in Verbindung bleiben und je nach Bedarf verschiedene Aktionen ausführen können. Mit dem Plugin können Administratoren Folgendes überprüfen:

* Überprüfen Sie die entsprechenden Integrationsfunktionen.
* Synchronisieren Sie Benutzer zwischen Office 365 und Moodle.
* Konfigurieren Sie die erforderlichen Berechtigungen für Benutzer.
* Richten Sie die SharePoint-Website für die Kursdateien ein.

In der folgenden Abbildung wird die Setupseite für die Microsoft 365-Integration angezeigt:

:::image type="content" source="../../assets/images/MoodleInstructions/365-integration.png" alt-text="Microsoft 365-Integration" border="true":::

### <a name="user-functions"></a>Benutzerfunktionen

Die Benutzer können die folgenden Aktionen mit Microsoft 365 Integration ausführen:

* Überprüfen Sie die allgemeine Funktion aller Microsoft 365 Plugin-Integrationen.
* Hochladen einer CSV-Datei, die Moodle mit Office 365-Benutzern vergleicht.
* Überprüfen Sie die Konfigurationen auf Azure AD-Berechtigungen.

## <a name="microsoft-365-repository"></a>Microsoft 365 Repository

Mit dem Microsoft 365 Repository-Plugin können Benutzer Kursdateien in OneDrive speichern. Dozenten können Dateien aus dem Kursdateienbereich von OneDrive oder aus ihrem eigenen persönlichen Bereich zum Repository hinzufügen.

Das Microsoft 365 Repository ermöglicht es dem Benutzer, es als Dateispeicher für eine Institution zu verwenden und gleichzeitig die Datenstruktur von Moodle einfach zu halten. Das Microsoft 365 Repository-Plugin stellt die folgenden Dienste bereit:

* Die Lehrpersonal kann die Kursdateien in OneDrive speichern. Jeder Kurs verfügt über einen eigenen Ordner, der in OneDrive erstellt wurde, sodass Lehrkräfte Dateien entweder aus dem Bereich „Kursdateien“ von OneDrive oder aus ihrem eigenen persönlichen Bereich hinzufügen können.  
* So fügen Sie Moodle-Dateien als Kopie hinzu oder erstellen einen Link zu der Datei. Die verknüpfte Datei wird in einem neuen Anwendungsfenster angezeigt oder auf der Webseite eingebettet.
* So laden Sie Dateien mithilfe der Moodle-Dateiauswahl auf OneDrive oder SharePoint hoch.

In der folgenden Abbildung wird das Microsoft 365 Datei-Repository angezeigt:

:::image type="content" source="../../assets/images/MoodleInstructions/microsoft-365- repository.png" alt-text="M365 Repository"  border="true":::

## <a name="teams-meetings"></a>Teams-Besprechungen

Das Teams-Besprechungs-Plugin ermöglicht Benutzern das Erstellen von Besprechungsanfragen in Kalendern, Aufgaben, Forenbeiträgen und auch im Atto-Editor gemäß Verfügbarkeit.

Nachdem das Plugin installiert wurde, können Lehrpersonal und Schüler/Studenten mit Moodle eine Audio- oder Videobesprechung erstellen, die Microsoft 365 Konto- und Moodle-Berechtigungen erfordert.

>[!NOTE]
>Teams-Besprechungen werden nicht in Outlook- oder Teams-Kalendern angezeigt, jedoch können der Einladung einzelne Kursteilnehmernamen hinzugefügt werden.

In der folgenden Abbildung wird die Anmeldeseite für Teams-Besprechungen angezeigt:

:::image type="content" source="../../assets/images/MoodleInstructions/teams-meeting.png" alt-text="Anmelden bei der Teams-Besprechung" border="true":::

## <a name="microsoft-365-teams-theme"></a>Microsoft 365 Teams Design

Das Microsoft 365 Teams-Design-Plugin bietet Benutzern eine benutzerdefinierte Ansicht der Startseite des Moodle-Kurses und kann angezeigt werden, wenn Benutzer auf ihre Moodle-Kurse in Teams zugreifen.

Das Design-Plugin bietet Benutzern eine einheitliche erweiterte Benutzeroberfläche mit den folgenden Features:

* Passt sich an Microsoft Teams-Designänderungen an, z. B. Standard, dunkel und hoher Kontrast.
* Ermöglicht die Konzentration auf die Kursaktivitäten.
* Entfernt Moodle-Blöcke, Navigation, Kopf- und Fußzeile.
* Stellt Microsoft Team User Interface (UI)-Elemente zur Verfügung.

Das folgende Bild zeigt das vom Benutzer eingerichtete Teams-Design:

:::image type="content" source="../../assets/images/MoodleInstructions/teams-theme.png" alt-text="Microsoft Teams-Design" border="true":::

## <a name="onenote-integration"></a>OneNote-Integration

Das OneNote-Integrations-Plugin bietet Nutzern die Möglichkeit, Notizbücher, Abschnitte und Seiten zu durchsuchen, in denen Aufgaben eingereicht werden, und Lehrkräfte geben das notwendige Feedback zu den entsprechenden Aufgaben in OneNote. OneNote verbessert auch die Benutzerfreundlichkeit, indem es über Tests und Links hinausgehende Funktionen hinzufügt und die Möglichkeiten für die mobile Nutzung von digitalen Stiften, Foto- oder Videomedien und das gemeinsame Schreiben mit Gruppen erweitert.

Die OneNote-Integration unterstützt Sie beim Zugriff auf Texte, Grafiken und Audiodateien. Das Plugin bietet die folgenden Vorteile:

* Fügen Sie das Durchsuchen von Notizbüchern, Abschnitten und Seiten hinzu, in denen die Schüler an Aufgaben arbeiten, und geben Sie Feedback zu diesen Aufgaben in OneNote.
* Kombinieren Sie digitale Ordner für Notizen, Aufgaben und Feedback zum Nachschlagen und Überprüfen.
* Erweitern Sie die Entwurfsmöglichkeiten über Text und Links hinaus, und erweitern Sie die mobile Nutzung mit digitalen Stiften, Foto- oder Videomedien und gemeinsamer Dokumenterstellung mit Gruppen.
* Fügen Sie die Einreichungs- und Feedback-Seite für jede Aufgabe unter dem Konto des Lehrpersonals hinzu. Wenn eine solche Datei in Moodle gespeichert wird, werden eine Kopie der HTML-Datei und alle zugehörigen Bilder in eine Zip-Datei gepackt.

> [!NOTE]
> Die Übermittlungs- oder Feedbackereignisse lösen die OneNote-Erstellung mit einem Abschnitt für jeden Kurs aus, für den sich der Kursteilnehmer angemeldet hat.

## <a name="microsoft-block"></a>Microsoft-Block

Das Microsoft-Block-Plugin ermöglicht dem Benutzer den Zugriff auf den Speicherort der SharePoint-Kursdateien und die Anzeige des Kurses im OneNote-Notizbuch für die Einreichung von Beiträgen, zusammen mit der Option, die Einstellungen für die Office 365-Integration zu ändern. Die Administratoren können den Block so konfigurieren, dass er auf allen Kursseiten angezeigt wird.

Der Microsoft-Block verbessert die Benutzerfreundlichkeit, indem er eine Benutzerschnittstelle zum Ändern der Microsoft 365-Integrationsfunktionen und zum Zugriff auf die zahlreichen Ressourcen bereitstellt. Die Administratoren können den Block so konfigurieren, dass die vorgenommenen Änderungen auf jeder Kursseite angezeigt werden. Der Block ermöglicht es dem Benutzer, die folgenden Aktivitäten auszuführen:

* Greifen Sie auf den Speicherort der SharePoint-Kursdatei und das OneNote-Notizbuch zu.
* Sehen Sie sich den Kurs im OneNote-Notizbuch für die Einreichung an.
* Konfigurieren Sie die Outlook-Kalendersynchronisierung.
* Verwaltet die Verbindung mit Office 365.
* Passen Sie persönliche Office 365-Integrationseinstellungen an.

Die folgende Abbildung zeigt die Microsoft-Block-Benutzeroberfläche:

:::image type="content" source="../../assets/images/MoodleInstructions/microsoft-block-1.png" alt-text="Microsoft-Block" border="true":::

## <a name="oembed-filter"></a>oEmbed-Filter

Das oEmbed-Filter-Plugin vereinfacht und verbessert die Benutzerfreundlichkeit, indem es die Einbindung von externen HTML-Inhalten in Moodle vereinfacht. Im Folgenden sind die Vorteile des oEmbed-Filters aufgeführt.

* Reduziert die Zeit zum Einbetten von Videos in eine HTML-Seite.
* Ermöglicht das Einbetten mehrerer Videoinhaltsanbieter.
* Stellt eine schnellere Methode zum Kopieren und Einbetten von Code aus einem der unterstützten Dienste sicher.
* Ermöglicht das Einbetten von Videos ohne API-Schlüssel.

Die folgende Abbildung zeigt die Aufnahme externer HTML-Inhalte in Moodle:

:::image type="content" source="../../assets/images/MoodleInstructions/oEmbed-filter.png" alt-text="oEmbed-Filterseite" border="true":::

## <a name="see-also"></a>Siehe auch

* [Partner-Apps für Moodle](../partner-apps-for-moodle.md)
* [Moodle – häufig gestellte Fragen](../faqs.md)
