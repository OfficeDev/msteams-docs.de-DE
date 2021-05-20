---
title: Installieren von Moodle LMS
description: So installieren und konfigurieren Sie die Moodle-Integrations-App für Microsoft Teams
keywords: Teams Moodle App-Integrations-Plugins
ms.topic: how-to
localization_priority: Normal
ms.author: lajanuar
author: laujan
ms.openlocfilehash: d7fddad80ca08fd4ca8dee352cdcbc46e8e97dcd
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566719"
---
# <a name="install-moodle-lms"></a>Installieren von Moodle LMS

In diesem Artikel erfahren Sie, wie Sie das Moodle LMS installieren.

> [!NOTE]
> Um IT-Administratoren bei der einfachen Einrichtung von Moodle und Teams-Integration zu unterstützen, werden Open-Source-Microsoft 365 Moodle Plugins für Folgendes aktualisiert:
>
> * Automatische Registrierung Ihres Moodle-Servers mit [Azure Active Directory (Azure AD)](https://azure.microsoft.com/services/active-directory/).
>
> * Ein-Klick-Bereitstellung Ihres Moodle Assistant-Bots in Azure.
>
> * Automatische Bereitstellung von Teams und automatische Synchronisierung von Teamregistrierungen für alle oder ausgewählte Moodle-Kurse.
>
> * Automatische Installation der Moodle-Registerkarte und des Moodle-Assistenten-Bots in jedes synchronisierte Team.
>
> Weitere Informationen zu den Funktionen dieser Integration finden Sie unter [Microsoft Teams und Moodle](https://education.microsoft.com/resource/3dffb3a8).

## <a name="prerequisites"></a>Voraussetzungen

Im Folgenden sind die Voraussetzungen für die Installation von Moodle:

* Moodle-Administratoranmeldeinformationen.

* Azure AD-Administratoranmeldeinformationen.

* Ein Azure-Abonnement, in dem Sie neue Ressourcen erstellen können.

## <a name="1-install-the-microsoft-365-moodle-plugins"></a>1. Installieren Sie die Microsoft 365 Moodle Plugins

Moodle Integration in Microsoft Teams wird durch die Open-Source-Microsoft 365 [Moodle Plugins gesetzt](https://github.com/Microsoft/o365-moodle)angetrieben.

### <a name="requisite-applications-and-plugins"></a>Erforderliche Anwendungen und Plugins

Stellen Sie sicher, dass Sie Folgendes installieren und herunterladen, bevor Sie mit der Installation der Microsoft 365 Moodle-Plugins fortfahren:

1. Stellen Sie sicher, dass Sie eine [aktuelle stabile Version von Moodle](https://download.moodle.org/releases/latest/)installieren.

1. Laden Sie die Moodle [OpenID Verbinden](https://moodle.org/plugins/auth_oidc) und die [Microsoft 365 Integration](https://moodle.org/plugins/local_o365) Plugins auf Ihren lokalen Computer herunter und speichern Sie sie.

    > [!NOTE]
    > Für die Teams-Integration sind die Installation der OpenID-Verbinden und Microsoft 365 Integration-Plugins erforderlich.
    >
    > Darüber hinaus ist die [Microsoft 365 Teams Theme](https://moodle.org/plugins/theme_boost_o365teams) Plugins sehr zu empfehlen.

### <a name="microsoft-365-moodle-plugins"></a>Microsoft 365 Moodle Plugins

1. Melden Sie sich bei Ihrem Moodle-Server als Administrator an, und wählen Sie **Siteadministration** aus dem [Einstellungen-Block](https://docs.moodle.org/22/en/Settings_block) im linken Navigationsbereich aus.

1. Wählen Sie die Registerkarte **Plugins** aus, und wählen Sie dann **Plugins installieren**.

1. Wählen Sie im Abschnitt Installieren von **Plugins aus ZIP-Dateien** **eine Datei auswählen** aus.

1. Wählen Sie **Hochladen Dateioption** aus dem linken Navigationsbereich aus, suchen Sie nach der heruntergeladenen Datei, und wählen Sie **Hochladen diese Datei** aus.

1. Wählen Sie **Siteadministration** im linken Navigationsbereich aus, um zu Ihrem Admin-Dashboard zurückzukehren. Scrollen Sie nach unten zu den **lokalen Plugins** und wählen Sie den **Link Microsoft 365 Integration** aus.

    > [!IMPORTANT]
    >
    > * Halten Sie Ihre Microsoft 365 Moodle Plugins Konfigurationsseite in einer separaten Browser-Registerkarte geöffnet, wie Sie zu diesem Satz von Seiten während des gesamten Prozesses zurückkehren müssen.  
    >
    > * Wenn Sie nicht über eine vorhandene Moodle-Site verfügen, wechseln Sie zum [Moodle on](https://github.com/azure/moodle) Azure-Repository, und stellen Sie schnell eine Moodle-Instanz bereit, und passen Sie sie an Ihre Anforderungen an.

## <a name="2-configure-the-connection-between-the-microsoft-365-plugins-and-azure-active-directory-azure-ad"></a>2. Konfigurieren der Verbindung zwischen den Microsoft 365-Plugins und Azure Active Directory (Azure AD)

Sie müssen die Verbindung zwischen den Microsoft 365-Plugins und Azure AD konfigurieren.

### <a name="requisites"></a>Voraussetzungen

Registrieren Sie Moodle mithilfe des PowerShell-Skripts als Anwendung in Azure AD. Das Powershell-Skript sieht Folgendes vor:

* Eine neue Azure AD-Anwendung für Ihren Microsoft 365-Mandanten, der von den Microsoft 365 Moodle-Plugins verwendet wird.
* Die App für Ihren Microsoft 365 Mandanten, richten Sie die erforderlichen Antwort-URLs und Berechtigungen für die bereitgestellte App ein, und gibt die `AppID` und `Key` zurück.

Verwenden Sie die generierte `AppID` und auf Ihrer Microsoft 365 `Key` Moodle Plugins-Setupseite, um Ihre Moodle-Serversite mit Azure AD zu konfigurieren.

> [!IMPORTANT]
>
> * Das PowerShell-Skript wird nicht mit den neuesten Konfigurationselementen aktualisiert, daher müssen Sie die Konfiguration manuell nach den Schritten in den Releaseseiten Moodle [3.8.0.4 und 3.9.1](https://docs.moodle.org/39/en/Office365#3.8.0.4_and_3.9.1_release) und [3.8.0.5 und 3.9.2](https://docs.moodle.org/39/en/Office365#3.8.0.5_and_3.9.2_release) ausführen.
>
> * Weitere Informationen zum manuellen Registrieren Ihrer Moodle-Instance finden Sie unter [Registrieren Ihrer Moodle-Instance als Anwendung](https://docs.moodle.org/34/en/Office365#Register_your_Moodle_instance_as_an_Application).

### <a name="the-moodle-tab-for-microsoft-teams-information-flow"></a>Die Registerkarte Moodle für Microsoft Teams Informationsfluss

<img width="530px" src="../assets/images/MoodleTabInformationFlow.png" alt="Moodle tab for Microsoft Teams information flow" />

1. Wählen Sie auf der Seite Microsoft 365 Integration-Plugins die Registerkarte **Setup** aus.

1. Wählen Sie die Schaltfläche **PowerShell-Skript herunterladen** aus, und speichern Sie sie als ZIP-Ordner auf Ihrem lokalen Computer.

1. Bereiten Sie das PowerShell-Skript aus der ZIP-Datei wie folgt vor: 

    1. Laden Sie die Datei herunter und extrahieren Sie `Moodle-AzureAD-Powershell.zip` sie.
    1. Öffnen Sie den extrahierten Ordner.
    1. Klicken Sie mit der rechten Maustaste auf die `Moodle-AzureAD-Script.ps1` Datei und wählen Sie **Eigenschaften** aus.
    1. Aktivieren Sie unter der Registerkarte **Allgemein** im Fenster Eigenschaften das `Unblock` Kontrollkästchen neben dem **Sicherheitsattribut** am unteren Rand des Fensters.
    1. Klicken Sie auf **OK**.
    1. Kopieren Sie den Verzeichnispfad in den extrahierten Ordner.

1. Führen Sie PowerShell als Administrator aus:

    1. Klicken Sie auf Starten.
    1. Geben Sie PowerShell ein.
    1. Rechtsklick auf **Windows PowerShell**.
    1. Wählen Sie **Ausführen als Administrator** aus.

1. Navigieren Sie zum entpackten Verzeichnis, indem Sie `cd .../.../Moodle-AzureAD-Powershell` eingeben, wo `.../...` sich der Pfad zum Verzeichnis befindet.

1. Führen Sie das PowerShell-Skript aus:

    1. Geben Sie `Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser` ein.
    1. Geben Sie `./Moodle-AzureAD-Script.ps1` ein.
    1. Melden Sie sich im Popup-Fenster bei Ihrem Microsoft 365-Administratorkonto an.
    1. Geben Sie den Namen der Azure AD-Anwendung ein, z. B. Moodle- oder Moodle-Plugins.
    1. Geben Sie die URL für Ihren Moodle-Server ein.
    1. Kopieren Sie die vom Skript generierte **Anwendungs-ID ( `AppID` )** und **den Anwendungsschlüssel ( `Key` ),** und speichern Sie sie.

1. Als nächstes müssen Sie die `AppID` und `Key` zum Microsoft 365 Moodle Plugins hinzufügen. Zurück zur Plugins-Verwaltungsseite, Website-Verwaltung > Plugins > Microsoft 365 Integration.

1. Fügen Sie auf der Registerkarte **Setup** die `AppID` und sie zuvor kopiert `Key` hinzu, und wählen Sie dann Änderungen **speichern** aus. Nach der Seitenaktualisierung wird ein neuer Abschnitt **Verbindungsmethode auswählen** angezeigt.

1. Aktivieren Sie in der **Verbindungsmethode "Verbindung auswählen"** das Kontrollkästchen **Standard**, und wählen Sie dann erneut **Änderungen speichern** aus.

1. Nachdem die Seite aktualisiert wurde, können Sie einen weiteren neuen Abschnitt **Admin Zustimmung & zusätzlichen Informationen** sehen.
    1. Wählen Sie Link **Admin Consent bereitstellen** aus, geben Sie Ihre Microsoft 365 Globalen Administratoranmeldeinformationen ein, und **akzeptieren** Sie dann, um die Berechtigungen zu erteilen.
    1. Wählen Sie neben dem Feld **Azure AD Tenant** die Schaltfläche **Erkennen** aus.
    1. Wählen Sie neben der **OneDrive for Business URL** die Schaltfläche **Erkennen** aus.
    1. Nachdem die Felder aufgepopt wurden, wählen Sie die Schaltfläche **Änderungen speichern** erneut aus.

1. Wählen Sie die Schaltfläche **Aktualisieren** aus, um die Installation zu überprüfen, und wählen Sie dann **Änderungen speichern** aus.

1. Synchronisieren Sie Benutzer zwischen Ihrem Moodle-Server und Azure AD. Erste Schritte:

    > [!NOTE]
    > Je nach Umgebung können Sie in dieser Phase verschiedene Optionen auswählen.

1. Synchronisieren Sie Benutzer zwischen Ihrem Moodle-Server und Azure AD. Je nach Umgebung können Sie in dieser Phase verschiedene Optionen auswählen. Erste Schritte:
    1. Wechseln Sie zur **Registerkarte Synchronisieren Einstellungen**.

    1. Aktivieren Sie im Abschnitt **Benutzer mit Azure AD** synchronisieren die Kontrollkästchen, die für Ihre Umgebung gelten. Sie müssen Folgendes auswählen:  

        ✔ Erstellen von Konten in Moodle für Benutzer in Azure AD.

        ✔ Alle Konten in Moodle für Benutzer in Azure AD aktualisieren.

    1. Im Abschnitt **Benutzererstellungseinschränkung** können Sie einen Filter einrichten, um die Azure AD-Benutzer einzuschränken, die mit Moodle synchronisiert werden.
    1. Im Abschnitt **Benutzerfeldzuordnung** können Sie die Feldzuordnung von Azure AD zu Moodle-Benutzerprofil anpassen.
    1. Im Abschnitt **Teams Sync** können Sie auswählen, dass automatisch Gruppen erstellt werden sollen, z. B. Teams für einige oder alle vorhandenen Moodle-Kurse.

13. Um [Cron-Aufträge](https://docs.moodle.org/310/en/Cron) zu überprüfen und manuell für die erste Ausführung auszuführen, wählen Sie im Abschnitt **Benutzer mit Azure AD** synchronisieren den Link zur Verwaltung **geplanter Aufgaben** aus. Dadurch gelangen Sie zur Seite **Geplante Aufgaben.**

    1. Scrollen Sie nach unten, und suchen Sie den **Azure AD-Auftrag synchronisieren,** und wählen Sie **Jetzt ausführen** aus.
    1. Wenn Sie Gruppen basierend auf vorhandenen Kursen erstellen möchten, können Sie auch die **Benutzergruppen erstellen in Microsoft 365** ausführen.

    > [!NOTE]
    >
    > Der Moodle [Cron](https://docs.moodle.org/310/en/Cron) läuft nach dem Aufgabenplan. Der Standardzeitplan ist einmal täglich. Der Cron muss jedoch häufiger ausgeführt werden, um alles synchron zu halten.

1. Kehren Sie zur Plugin-Verwaltungsseite, **zur Websiteverwaltung > Plugins > Microsoft 365 Integration** zurück, und wählen Sie die Seite **Teams Einstellungen** aus.

1. Konfigurieren Sie auf der **Seite Teams Einstellungen** die erforderlichen Einstellungen, um die Teams App-Integration zu aktivieren.

    1. Um **OpenID Verbinden** zu aktivieren, wählen Sie den Link **Authentifizierung verwalten** aus, und wählen Sie das Augensymbol in der **OpenId-Verbinden-Zeile** aus, wenn es ausgegraut ist.
    1. Um die Einbettung von Frames zu aktivieren, wählen Sie die **HTTP-Sicherheitsverknüpfung** aus, und aktivieren Sie dann das Kontrollkästchen neben **Frameeinbettung zulassen**.
    1. Um Webdienste zu aktivieren, die die Moodle-API-Funktionen aktivieren, wählen Sie den Link **Erweiterte Funktionen** aus, und stellen Sie dann sicher, dass das Kontrollkästchen neben **Webdienste aktivieren** aktiviert ist.
    1. Um die externen Dienste für Microsoft 365 zu aktivieren, wählen Sie die Verknüpfung **Externe Dienste** aus, und dann:  

        ✔ Wählen Sie **Bearbeiten** in der **Zeile Moodle Microsoft 365 Webservices** aus.

        ✔ Aktivieren Sie das Kontrollkästchen neben **Aktiviert**, und wählen Sie dann **Änderungen speichern** aus.

    1. Bearbeiten Sie Ihre authentifizierten Benutzerberechtigungen, damit diese Webdiensttoken erstellen können.

        ✔ Wählen Sie die **Bearbeitungsrolle Authentifizierter Benutzerlink** aus.

        ✔ Scrollen Sie nach unten und suchen Sie die Funktion **Webdiensttoken erstellen,** und aktivieren Sie das Kontrollkästchen **Zulassen.**

## <a name="3-deploy-the-moodle-assistant-bot-to-azure"></a>3. Stellen Sie den Moodle Assistant Bot in Azure bereit

Der kostenlose Moodle-Assistents-Bot für Microsoft Teams hilft Lehrern und Schülern, Fragen zu ihren Kursen, Aufgaben, Noten und anderen Informationen in Moodle zu beantworten. Der Bot sendet auch Moodle-Benachrichtigungen an Schüler und Lehrer innerhalb Teams. Der Bot ist ein Open-Source-Projekt, das von Microsoft verwaltet wird und auf [GitHub](https://github.com/microsoft/Moodle-Teams-Bot)verfügbar ist.

> [!NOTE]
>
> * Stellen Sie Ressourcen für Ihr Azure-Abonnement bereit. Alle Ressourcen wurden mit dem **kostenlosen** Kontingent konfiguriert. Abhängig von der Nutzung Ihres Bots müssen Sie diese Ressourcen möglicherweise skalieren.
>
> * Um die Moodle-Registerkarte ohne den Bot zu verwenden, springen Sie zu [4](#4-deploy-your-microsoft-teams-app).

### <a name="moodle-bot-information-flow"></a>Moodle Bot-Informationsfluss

<img width="530px" src="../assets/images/MoodleBotInformationFlow.png" alt="Moodle bot for Microsoft Teams information flow" />

Um den Bot zu installieren, müssen Sie ihn auf der [Microsoft Identity Platform](https://identity.microsoft.com/Landing)registrieren. Auf diese Weise kann sich Ihr Bot bei Ihren Microsoft-Endpunkten authentifizieren. 

**So registrieren Sie Ihren Bot**

1. Gehen Sie zur Plugins-Verwaltungsseite, und wählen Sie dann **Plugins** aus. Wählen Sie unter **Microsoft 365 Integration** die Registerkarte **Teams Einstellungen** aus.

1. Wählen Sie den Link **Microsoft Application Registration Portal** aus, und melden Sie sich mit Ihrer Microsoft ID an.

1. Geben Sie einen Namen für Ihre App ein, z. B. MoodleBot, und wählen Sie die Schaltfläche **Erstellen** aus.

1. Kopieren Sie die **Anwendungs-ID,** und fügen Sie sie in das Feld **Bot-Anwendungs-ID** auf der **Seite Team Einstellungen** ein.

1. Wählen Sie die Schaltfläche **Neues Kennwort generieren** aus. Kopieren Sie das generierte Kennwort, und fügen Sie es in das Feld **Bot-Anwendungskennwort** auf der **Seite Team Einstellungen** ein.

1. Scrollen Sie zum unteren Rand des Formulars, und wählen Sie **Änderungen speichern** aus.

Nachdem Sie Ihre Anwendungs-ID und Ihr Kennwort generiert haben, stellen Sie Ihren Bot in Azure bereit:

> [!div class="checklist"]
> * Wählen Sie **Bereitstellen in Azure** aus, und füllen Sie das Formular mit den erforderlichen Informationen aus, z. B. der Bot-Anwendungs-ID, dem Bot-Anwendungskennwort und dem Moodle Secret auf der **Teams Einstellungen-Seite.** Die Azure-Informationen befinden sich auf der **Seite Setup.** 
> * Aktivieren Sie nach dem Ausfüllen des Formulars das Kontrollkästchen, um den Geschäftsbedingungen zuzustimmen.
> * Wählen Sie **Kauf**. Alle Azure-Ressourcen werden im kostenlosen Kontingent bereitgestellt.

Nachdem die Bereitstellung der Ressourcen in Azure abgeschlossen wurde, müssen Sie die Microsoft 365 Moodle-Plugins mit einem Messagingendpunkt konfigurieren. Sie müssen den Endpunkt von Ihrem Bot in Azure abrufen:

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.

1. Wählen Sie im linken Bereich **Ressourcengruppen** aus, und wählen Sie die Ressourcengruppe aus, die Sie verwendet oder erstellt haben, während Sie ihren Bot bereitstellen.

1. Wählen Sie die **WebApp Bot-Ressource** aus der Liste der Ressourcen in der Gruppe aus.

1. Kopieren Sie den **Messaging-Endpunkt** aus dem Abschnitt **Übersicht.**

1. Öffnen Sie in Moodle die **Team-Einstellungen-Seite** Ihres Microsoft 365 Moodle Plugins.

1. Fügen Sie im Feld **Bot Endpoint** die URL ein, die Sie gerade kopiert haben, und ändern Sie das Wort *Nachrichten* in *webhook*. Die URL muss wie folgt angezeigt werden: `https://botname.azurewebsites.net/api/webhook`

1. Wählen Sie **Änderungen speichern** aus.

1. Nachdem Sie die Änderungen gespeichert haben, kehren Sie zur Registerkarte **Team Einstellungen** zurück, wählen Sie die Schaltfläche **Manifestdatei herunterladen** aus, und speichern Sie das App-Manifestpaket zur weiteren Verwendung auf Ihrem Computer.

## <a name="4-deploy-your-microsoft-teams-app"></a>4. Stellen Sie Ihre Microsoft Teams-App bereit

Nachdem Ihr Bot in Azure bereitgestellt und für die Weiterbereitung mit Ihrem Moodle-Server konfiguriert wurde, müssen Sie Ihre Microsoft Teams-App bereitstellen. Dazu müssen Sie die App-Manifestdatei laden, die Sie im vorherigen Schritt von der Seite Microsoft 365 Moodle Plugins Team Einstellungen heruntergeladen haben.

Bevor Sie die App installieren, müssen Sie sicherstellen, dass externe Apps aktiviert und Apps hochgeladen werden. Weitere Informationen finden Sie unter [Vorbereiten des Microsoft 365 Mandanten](../concepts/build-and-test/prepare-your-o365-tenant.md). 

**So stellen Sie Ihre App bereit** 

1. Öffnen **Sie Microsoft Teams**. 

1. Wählen Sie das **App-Symbol** im unteren linken Bereich der Navigationsleiste aus.

1. Wählen Sie die **Hochladen einen benutzerdefinierten App-Link** aus der Liste der Optionen aus.

   > [!NOTE]
   > Wenn Sie als globaler Administrator angemeldet sind, müssen Sie die Möglichkeit haben, die App in den App-Katalog Ihrer Organisation hochzuladen, andernfalls können Sie die App nur für ein Team laden, in dem Sie Mitglied sind.

4. Wählen Sie das Paket aus, `manifest.zip` das Sie zuvor heruntergeladen haben, und wählen Sie **Speichern** aus. Wenn Sie das App-Manifestpaket nicht heruntergeladen haben, können Sie es von der Registerkarte **Team Einstellungen** der Plugins-Konfigurationsseite in Moodle herunterladen.

Nachdem Sie die App installiert haben, können Sie die Registerkarte jedem Kanal hinzufügen, auf den Sie Zugriff haben. Navigieren Sie dazu zum Kanal, wählen Sie das **Plussymbol** (➕) und wählen Sie Ihre App aus der Liste aus. Folgen Sie den Anweisungen, um das Hinzufügen der Moodle-Kursregisterkarte zu einem Kanal abzuschließen.

## <a name="5-allow-automatic-creation-of-moodle-tabs-in-microsoft-teams"></a>5. Erlauben Sie die automatische Erstellung von Moodle-Tabs in Microsoft Teams

Obwohl die Moodle-Registerkarten manuell in Microsoft Teams erstellt werden, können Sie sie automatisch erstellen, wenn Teams aus der Kurssynchronisierung erstellt werden. Dazu müssen Sie die ID der hochgeladenen Microsoft Teams-App in Moodle konfigurieren.

**So ermöglichen Sie die automatische Erstellung von Moodle-Registerkarten**

1. Öffnen Sie Microsoft Teams.

1. Wählen Sie das Apps-Symbol im unteren linken Bereich der Navigationsleiste aus.

1. Suchen Sie die hochgeladene **Moodle-App** > das **Optionssymbol** auswählen > **Den Link kopieren** auswählen.

1. Fügen Sie in einem Texteditor den kopierten Inhalt ein. Sie muss eine URL wie ht&#8203;tps://teams.microsoft.com/l/app/00112233-4455-6677-8899-aabbccddeeff enthalten. Kopieren Sie den letzten Teil der URL, z. B. `00112233-4455-6677-8899-aabbccddeeff` , der die ID der Microsoft Teams-App ist.

1. Öffnen Sie in Moodle die **Teams Moodle-App-Registerkarte** von Ihrer Konfigurationsseite Microsoft 365 Moodle Plugins.

1. Fügen Sie die ID der Microsoft Teams-App in das Feld Moodle-App-ID ein, und speichern Sie Änderungen.

Wenn ein Moodle-Kurs synchronisiert wird, installiert Microsoft Teams automatisch die Moodle-App im Team, erstellt eine Moodle-Registerkarte im allgemeinen Kanal von Teams und konfiguriert sie so, dass sie die Kursseite für den Moodle-Kurs enthält, von dem aus er synchronisiert wird. Sie können jetzt direkt von Microsoft Teams aus mit der Arbeit mit Ihren Moodle-Kursen beginnen.

> [!NOTE]
> Um Feature-Anfragen oder Feedback mit uns zu teilen, besuchen Sie unsere [User Voice-Seite](https://microsoftteams.uservoice.com/forums/916759-moodle).

## <a name="see-also"></a>Siehe auch

- [Integrieren von Web-Apps](~/samples/integrate-web-apps-overview.md)
- [Moodle](https://moodle.org/)
- [Moodle-Dokumentation](https://docs.moodle.org/34/en/Installing_plugins).

