---
title: Installieren von Moodle LMS
description: So installieren und konfigurieren Sie die Moodle-Integrations-App für Microsoft Teams
keywords: Teams Moodle-App-Integrations-Plug-Ins
ms.topic: how-to
ms.localizationpriority: medium
ms.author: lajanuar
author: surbhigupta
ms.openlocfilehash: d4a7c150b777702e7724575ac4db04860a281978
ms.sourcegitcommit: 830fdc80556a5fde642850dd6b4d1b7efda3609d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/09/2022
ms.locfileid: "63399205"
---
# <a name="install-moodle-lms"></a>Installieren von Moodle LMS

In diesem Artikel erfahren Sie, wie Sie Moodle LMS installieren.

> [!NOTE]
> Um IT-Administratoren bei der einfachen Einrichtung von Moodle und Teams Integration zu unterstützen, wird Open Source Microsoft 365 Moodle-Plug-Ins für Folgendes aktualisiert:
>
> * Automatische Registrierung Ihres Moodle-Servers mit [Microsoft Azure Active Directory (Azure AD)](https://azure.microsoft.com/services/active-directory/).
>
> * Bereitstellung Ihres Moodle Assistant-Bots in Azure mit einem Klick.
>
> * Automatische Bereitstellung von Teams und automatische Synchronisierung von Teamregistrierungen für alle oder ausgewählte Moodle-Kurse.
>
> * Automatische Installation der Registerkarte "Moodle" und des Moodle-Assistenten-Bots in jedem synchronisierten Team.
>
> Weitere Informationen zu den Funktionen dieser Integration finden Sie unter [Microsoft Teams und Moodle](https://education.microsoft.com/resource/3dffb3a8).

## <a name="prerequisites"></a>Voraussetzungen

Nachfolgend sind die Voraussetzungen für die Installation von Moodle beschrieben:

* Moodle-Administratoranmeldeinformationen.

* Azure AD Administratoranmeldeinformationen.

* Ein Azure-Abonnement, in dem Sie neue Ressourcen erstellen können.

## <a name="1-install-the-microsoft-365-moodle-plugins"></a>1. Installieren Sie die Microsoft 365 Moodle-Plug-Ins

Die Moodle-Integration in Microsoft Teams wird durch die Open [Source-Microsoft 365 Moodle-Plug-Ins unterstützt](https://github.com/Microsoft/o365-moodle).

### <a name="requisite-applications-and-plugins"></a>Erforderliche Anwendungen und Plug-Ins

Stellen Sie sicher, dass Sie Folgendes installieren und herunterladen, bevor Sie mit der Installation der Microsoft 365 Moodle-Plug-Ins fortfahren:

1. Stellen Sie sicher, dass Sie eine [aktuelle stabile Version von Moodle](https://download.moodle.org/releases/latest/) installieren.

1. Laden Sie die Moodle [OpenID-Verbinden](https://moodle.org/plugins/auth_oidc) und die [Microsoft 365](https://moodle.org/plugins/local_o365) Integrations-Plug-Ins auf Ihrem lokalen Computer herunter, und speichern Sie sie.

    > [!NOTE]
    > Die Installation der OpenID-Verbinden und Microsoft 365 Integrations-Plug-Ins ist für die Teams Integration erforderlich.
    >
    > Darüber hinaus wird die [Microsoft 365 Teams](https://moodle.org/plugins/theme_boost_o365teams) Design-Plug-Ins dringend empfohlen.

### <a name="microsoft-365-moodle-plugins"></a>Microsoft 365 Moodle-Plug-Ins

1. Melden Sie sich als Administrator bei Ihrem Moodle-Server an, und wählen Sie die **Websiteverwaltung** aus dem [Einstellungen Block](https://docs.moodle.org/22/en/Settings_block) aus, der sich im linken Navigationsbereich befindet.

1. Wählen Sie die Registerkarte **"Plug-Ins** " und dann " **Plug-Ins installieren"** aus.

1. Wählen Sie im Abschnitt **"Plug-Ins aus ZIP-Datei installieren****" die Option "Datei auswählen"** aus.

1. Wählen Sie im linken Navigationsbereich **Hochladen eine Dateioption** aus, suchen Sie nach der datei, die Sie heruntergeladen haben, und wählen Sie **Hochladen diese Datei** aus.

1. Wählen Sie die **Websiteverwaltung** im linken Navigationsbereich aus, um zu Ihrem Administratordashboard zurückzukehren. Scrollen Sie nach unten zu den **lokalen Plug-Ins**, und wählen Sie den Link **Microsoft 365 Integration** aus.

    > [!IMPORTANT]
    >
    > * Lassen Sie Ihre Microsoft 365 Moodle-Plug-In-Konfigurationsseite auf einer separaten Browserregisterkarte geöffnet, da Sie während des gesamten Prozesses zu dieser Gruppe von Seiten zurückkehren müssen.  
    >
    > * Wenn Sie nicht über eine vorhandene Moodle-Website verfügen, wechseln Sie zum [Moodle on Azure-Repository](https://github.com/azure/moodle) , stellen Sie schnell eine Moodle-Instanz bereit und passen Sie sie an Ihre Anforderungen an.

## <a name="2-configure-the-connection-between-the-microsoft-365-plugins-and-azure-ad"></a>2. Konfigurieren der Verbindung zwischen den Microsoft 365-Plug-Ins und Azure AD

Sie müssen die Verbindung zwischen den Microsoft 365-Plug-Ins und Azure AD konfigurieren.

### <a name="requisites"></a>Voraussetzungen

Registrieren Sie Moodle als Anwendung in Ihrem Azure AD mithilfe des PowerShell-Skripts. Das Skript stellt Folgendes bereit:

* Eine neue Azure AD-Anwendung für Ihren Microsoft 365 Mandanten, die von den Microsoft 365 Moodle-Plug-Ins verwendet wird.
* Die App für Ihren Microsoft 365 Mandanten, richtet die erforderlichen Antwort-URLs und Berechtigungen für die bereitgestellte App ein und gibt die und zurück `AppID` `Key`.

Verwenden Sie die generierte `AppID` und `Key` in Ihrer Microsoft 365 Moodle Plugins-Setupseite, um Ihre Moodle-Serverwebsite mit Azure AD zu konfigurieren.

> [!IMPORTANT]
>
> * Das PowerShell-Skript wird nicht mit den neuesten Konfigurationselementen aktualisiert. Daher müssen Sie die Konfiguration manuell nach den Schritten durchführen, die auf den Versionsseiten Moodle [3.8.0.4 und 3.9.1](https://docs.moodle.org/39/en/Office365#3.8.0.4_and_3.9.1_release) und [3.8.0.5 und 3.9.2](https://docs.moodle.org/39/en/Office365#3.8.0.5_and_3.9.2_release) beschrieben sind.
>
> * Weitere Informationen zum manuellen Registrieren Ihrer Moodle-Instanz finden Sie unter [Registrieren Ihrer Moodle-Instanz als Anwendung](https://docs.moodle.org/34/en/Office365#Register_your_Moodle_instance_as_an_Application).

### <a name="the-moodle-tab-for-microsoft-teams-information-flow"></a>Registerkarte "Moodle" für Microsoft Teams Informationsfluss

<img width="530px" src="../assets/images/MoodleTabInformationFlow.png" alt="Moodle tab for Microsoft Teams information flow" />

1. Wählen Sie auf der Seite Microsoft 365 Integrations-Plug-Ins die Registerkarte **"Setup**" aus.

1. Wählen Sie die Schaltfläche " **PowerShell-Skript herunterladen** " aus, und speichern Sie sie als ZIP-Ordner auf Ihrem lokalen Computer.

1. Bereiten Sie das PowerShell-Skript aus der ZIP-Datei wie folgt vor:

    1. Laden Sie die Datei herunter, und extrahieren Sie sie `Moodle-AzureAD-Powershell.zip` .
    1. Öffnen Sie den extrahierten Ordner.
    1. Klicken Sie mit der rechten Maustaste auf die `Moodle-AzureAD-Script.ps1` Datei, und wählen Sie **"Eigenschaften" aus**.
    1. Aktivieren Sie im Fenster "Eigenschaften" auf der Registerkarte " **Allgemein** " das `Unblock` Kontrollkästchen neben dem **Security-Attribut** am unteren Rand des Fensters.
    1. Wählen Sie **OK** aus.
    1. Kopieren Sie den Verzeichnispfad in den extrahierten Ordner.

1. Führen Sie PowerShell als Administrator aus:

    1. Klicken Sie auf Starten.
    1. Geben Sie PowerShell ein.
    1. Klicken Sie mit der rechten Maustaste auf **Windows PowerShell**.
    1. Wählen Sie **"Als Administrator ausführen**" aus.

1. Navigieren Sie zum entpackten Verzeichnis, indem Sie eingeben `cd .../.../Moodle-AzureAD-Powershell` , wo `.../...` sich der Pfad zum Verzeichnis befindet.

1. Führen Sie das PowerShell-Skript aus:

    1. Geben Sie `Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser`.
    1. Geben Sie `./Moodle-AzureAD-Script.ps1`.
    1. Melden Sie sich im Popupfenster bei Ihrem Microsoft 365 Administratorkonto an.
    1. Geben Sie den Namen der Azure AD-Anwendung ein, z. B. Moodle- oder Moodle-Plug-Ins.
    1. Geben Sie die URL für Ihren Moodle-Server ein.
    1. Kopieren Sie die vom Skript generierte **Anwendungs-ID (`AppID`)** und den **Anwendungsschlüssel(`Key`),** und speichern Sie sie.

1. Als Nächstes müssen Sie das `AppID` und `Key` zum Microsoft 365 Moodle-Plug-Ins hinzufügen. Kehren Sie zur Verwaltungsseite für Plug-Ins zurück, websiteverwaltung > Plugins > Microsoft 365 Integration.

1. Fügen Sie auf der Registerkarte **"Setup** " die `AppID` `Key` zuvor kopierten und kopierten hinzu, und wählen Sie dann **"Änderungen speichern" aus**. Nachdem die Seite aktualisiert wurde, wird ein neuer Abschnitt **"Verbindungsmethode auswählen" angezeigt**.

1. Aktivieren Sie in der **Methode "Verbindung auswählen**" das Kontrollkästchen mit der Bezeichnung **"Standard**", und wählen Sie dann erneut **"Änderungen speichern" aus** .

1. Nachdem die Seite aktualisiert wurde, sehen Sie einen weiteren neuen Abschnitt **zur Administratorzustimmung & zusätzliche Informationen**.
    1. Wählen Sie den Link "**Administratorzustimmung bereitstellen**" aus, geben Sie Ihre Microsoft 365 globalen Administratoranmeldeinformationen ein, und **akzeptieren Sie** dann, um die Berechtigungen zu erteilen.
    1. Wählen Sie neben dem **Feld Azure AD Mandanten** die Schaltfläche "**Erkennen**" aus.
    1. Wählen Sie neben der **OneDrive for Business-URL** die Schaltfläche "**Erkennen**" aus.
    1. Nachdem die Felder aufgefüllt wurden, wählen Sie erneut die Schaltfläche **"Änderungen speichern** " aus.

1. Klicken Sie auf die Schaltfläche " **Aktualisieren** ", um die Installation zu überprüfen, und wählen Sie dann **"Änderungen speichern"** aus.

1. Synchronisieren Sie Benutzer zwischen Ihrem Moodle-Server und Azure AD. Erste Schritte:

    > [!NOTE]
    > Je nach Umgebung können Sie in dieser Phase unterschiedliche Optionen auswählen.

1. Synchronisieren Sie Benutzer zwischen Ihrem Moodle-Server und Azure AD. Je nach Umgebung können Sie in dieser Phase unterschiedliche Optionen auswählen. Erste Schritte:
    1. Wechseln Sie zur **Registerkarte Einstellungen synchronisieren**.

    1. Aktivieren Sie im Abschnitt **"Benutzer mit Azure AD synchronisieren**" die Kontrollkästchen, die für Ihre Umgebung gelten. Sie müssen Folgendes auswählen:  

        ✔ Erstellen Sie Konten in Moodle für Benutzer in Azure AD.

        ✔ Aktualisieren Sie alle Konten in Moodle für Benutzer in Azure AD.

    1. Im Abschnitt "**Einschränkung der Benutzererstellung**" können Sie einen Filter einrichten, um die Azure AD Benutzer einzuschränken, die mit Moodle synchronisiert werden.
    1. Im Abschnitt **"Benutzerfeldzuordnung**" können Sie die Azure AD zur Moodle-Benutzerprofil-Feldzuordnung anpassen.
    1. Im Abschnitt **Teams Synchronisierung** können Sie auswählen, ob Automatisch Gruppen erstellt werden sollen, z. B. Teams für einige oder alle Ihrer vorhandenen Moodle-Kurse.

13. Um [Cron-Aufträge](https://docs.moodle.org/310/en/Cron) zu überprüfen und für die erste Ausführung manuell auszuführen, wählen Sie den Link "**Verwaltung geplanter Aufgaben**" im Abschnitt "**Benutzer mit Azure AD synchronisieren**" aus. Dadurch gelangen Sie zur Seite " **Geplante Aufgaben** ".

    1. Scrollen Sie nach unten, suchen Sie die **Synchronisierungsbenutzer mit Azure AD** Auftrag, und wählen Sie **"Jetzt ausführen" aus**.
    1. Wenn Sie Gruppen basierend auf vorhandenen Kursen erstellen möchten, können Sie auch die **Benutzergruppen in Microsoft 365** Auftrag erstellen ausführen.

    > [!NOTE]
    >
    > Moodle [Cron](https://docs.moodle.org/310/en/Cron) wird gemäß dem Aufgabenplan ausgeführt. Der Standardzeitplan ist einmal täglich. Der Cron muss jedoch häufiger ausgeführt werden, um alles synchron zu halten.

1. Kehren Sie zur Verwaltungsseite für Plug-Ins zurück, **websiteverwaltung > Plugins > Microsoft 365 Integration**, und wählen Sie die **Seite Teams Einstellungen** aus.

1. Konfigurieren Sie auf der **Teams Einstellungen** Seite die erforderlichen Einstellungen, um die Teams App-Integration zu aktivieren.

    1. Um **OpenID Verbinden** zu aktivieren, wählen Sie den Link **"Authentifizierung verwalten**" aus, und wählen Sie das Augensymbol auf der **OpenId Verbinden** Zeile aus, wenn sie abgeblendet ist.
    1. Um die Frameeinbettung zu aktivieren, wählen Sie den Link **HTTP-Sicherheit** aus, und aktivieren Sie dann das Kontrollkästchen neben **"Frameeinbettung zulassen"**.
    1. Um Webdienste zu aktivieren, die die Moodle-API-Features aktivieren, wählen Sie den Link **"Erweiterte Features** " aus, und stellen Sie dann sicher, dass das Kontrollkästchen neben " **Webdienste aktivieren** " aktiviert ist.
    1. Um die externen Dienste für Microsoft 365 zu aktivieren, wählen Sie den Link **"Externe Dienste"** aus, und wählen Sie dann Folgendes aus:  

        ✔ Wählen Sie in der Zeile **"Moodle Microsoft 365 Webservices**" die Option **"Bearbeiten**" aus.

        ✔ Aktivieren Sie das Kontrollkästchen neben **"Aktiviert"**, und wählen Sie dann **"Änderungen speichern" aus**.

    1. Bearbeiten Sie Ihre authentifizierten Benutzerberechtigungen, damit sie Webdiensttoken erstellen können.

        ✔ Wählen Sie den Link " **Authentifizierte Benutzer bearbeiten** " aus.

        ✔ Scrollen Sie nach unten, suchen Sie die Funktion zum **Erstellen eines Webdiensttokens** , und aktivieren Sie das Kontrollkästchen **Zulassen** .

## <a name="3-deploy-the-moodle-assistant-bot-to-azure"></a>3. Bereitstellen des Moodle Assistant Bot in Azure

Der kostenlose Moodle-Assistent-Bot für Microsoft Teams hilft Lehrern und Schülern bei der Beantwortung von Fragen zu ihren Kursen, Aufgaben, Noten und anderen Informationen in Moodle. Der Bot sendet außerdem Moodle-Benachrichtigungen an Schüler und Lehrer innerhalb Teams. Der Bot ist ein Open-Source-Projekt, das von Microsoft verwaltet wird und auf [GitHub](https://github.com/microsoft/Moodle-Teams-Bot) verfügbar ist.

> [!NOTE]
>
> * Stellen Sie Ressourcen für Ihr Azure-Abonnement bereit. Alle Ressourcen wurden mithilfe der **kostenlosen** Ebene konfiguriert. Abhängig von der Verwendung Ihres Bots müssen Sie diese Ressourcen möglicherweise skalieren.
>
> * Um die Moodle-Registerkarte ohne den Bot zu verwenden, fahren Sie mit [4](#4-deploy-your-microsoft-teams-app) um.

### <a name="moodle-bot-information-flow"></a>Moodle-Bot-Informationsfluss

<img width="530px" src="../assets/images/MoodleBotInformationFlow.png" alt="Moodle bot for Microsoft Teams information flow" />

Um den Bot zu installieren, müssen Sie ihn auf der [Microsoft Identity Platform](https://identity.microsoft.com/Landing) registrieren. Dadurch kann sich Ihr Bot bei Ihren Microsoft-Endpunkten authentifizieren.

So registrieren Sie Ihren Bot:

1. Wechseln Sie zur Verwaltungsseite für Plug-Ins, und wählen Sie dann **Plug-Ins** aus. Wählen Sie unter **Microsoft 365 Integration** die Registerkarte **Teams Einstellungen** aus.

1. Wählen Sie den Link **zum Microsoft-Anwendungsregistrierungsportal** aus, und melden Sie sich mit Ihrer Microsoft-ID an.

1. Geben Sie einen Namen für Ihre App ein, z. B. MoodleBot, und wählen Sie die Schaltfläche **"Erstellen** " aus.

1. Kopieren Sie die **Anwendungs-ID**, und fügen Sie sie in das **Feld "Bot-Anwendungs-ID**" auf der Seite **"Team Einstellungen**" ein.

1. Wählen Sie die Schaltfläche **"Neues Kennwort generieren** " aus. Kopieren Sie das generierte Kennwort, und fügen Sie es in das **Feld "Bot-Anwendungskennwort"** auf der Seite **"Team Einstellungen**" ein.

1. Scrollen Sie zum unteren Rand des Formulars, und wählen Sie **"Änderungen speichern" aus**.

Nachdem Sie Ihre Anwendungs-ID und Ihr Kennwort generiert haben, stellen Sie Ihren Bot in Azure bereit:

> [!div class="checklist"]
>
> * Wählen Sie **"Bereitstellen in Azure"** aus, und füllen Sie das Formular mit den erforderlichen Informationen aus, z. B. der Bot-Anwendungs-ID, dem Bot-Anwendungskennwort und dem geheimen Moodle-Schlüssel auf der **Teams Einstellungen** Seite. Die Azure-Informationen befinden sich auf der **Setupseite** .
> * Aktivieren Sie nach dem Ausfüllen des Formulars das Kontrollkästchen, um den Geschäftsbedingungen zuzustimmen.
> * Wählen Sie **"Kaufen" aus**. Alle Azure-Ressourcen werden auf der kostenlosen Ebene bereitgestellt.

Nachdem die Ressourcen in Azure bereitgestellt wurden, müssen Sie die Microsoft 365 Moodle-Plug-Ins mit einem Messaging-Endpunkt konfigurieren. Sie müssen den Endpunkt von Ihrem Bot in Azure abrufen:

1. Melden Sie sich im [Microsoft Azure-Portal](https://portal.azure.com) an.

1. Wählen Sie im linken Bereich **Ressourcengruppen** aus, und wählen Sie die Ressourcengruppe aus, die Sie während der Bereitstellung Ihres Bots verwendet oder erstellt haben.

1. Wählen Sie die **WebApp-Bot-Ressource** aus der Liste der Ressourcen in der Gruppe aus.

1. Kopieren Sie den **Nachrichtenendpunkt** aus dem Abschnitt **"Übersicht** ".

1. Öffnen Sie in Moodle die **Team-Einstellungen-Seite** Ihrer Microsoft 365 Moodle-Plug-Ins.

1. Fügen Sie im **Feld "Bot-Endpunkt** " die URL ein, die Sie gerade kopiert haben, und ändern Sie die *Wortmeldungen* in *Webhook*. Die URL muss wie folgt angezeigt werden: `https://botname.azurewebsites.net/api/webhook`

1. Klicken Sie auf **Änderungen speichern**.

1. Wechseln Sie nach dem Speichern der Änderungen zurück zur Registerkarte "**Team Einstellungen**", wählen Sie die Schaltfläche "**Manifestdatei herunterladen**" aus, und speichern Sie das App-Manifestpaket zur weiteren Verwendung auf Ihrem Computer.

## <a name="4-deploy-your-microsoft-teams-app"></a>4. Bereitstellen ihrer Microsoft Teams-App

Nachdem Ihr Bot in Azure bereitgestellt und für die Kommunikation mit Ihrem Moodle-Server konfiguriert wurde, müssen Sie Ihre Microsoft Teams App bereitstellen. Dazu müssen Sie die App-Manifestdatei laden, die Sie im vorherigen Schritt von der Seite Microsoft 365 Moodle Plugins Team Einstellungen heruntergeladen haben.

Bevor Sie die App installieren, müssen Sie sicherstellen, dass externe Apps aktiviert und Apps hochgeladen werden. Weitere Informationen finden Sie unter [Vorbereiten Ihres Microsoft 365 Mandanten](../concepts/build-and-test/prepare-your-o365-tenant.md).

So stellen Sie Ihre App bereit:

1. Öffnen **Sie Microsoft Teams**.

1. Wählen Sie das **App-Symbol** im unteren linken Bereich der Navigationsleiste aus.

1. Wählen Sie die **Hochladen einen benutzerdefinierten App-Link** aus der Liste der Optionen aus.

   > [!NOTE]
   > Wenn Sie als globaler Administrator angemeldet sind, müssen Sie die Möglichkeit haben, die App in den App-Katalog Ihrer Organisation hochzuladen. Andernfalls können Sie die App nur für ein Team laden, in dem Sie Mitglied sind.

4. Wählen Sie das `manifest.zip` Paket aus, das Sie zuvor heruntergeladen haben, und wählen Sie **"Speichern**" aus. Wenn Sie das App-Manifestpaket nicht heruntergeladen haben, können Sie es auf der Registerkarte "**Team Einstellungen**" der Konfigurationsseite der Plug-Ins in Moodle herunterladen.

Nachdem Sie die App installiert haben, können Sie die Registerkarte zu jedem Kanal hinzufügen, auf den Sie Zugriff haben. Navigieren Sie dazu zum Kanal, wählen Sie das **Pluszeichen** (➕) aus, und wählen Sie Ihre App aus der Liste aus. Folgen Sie den Anweisungen, um das Hinzufügen Ihrer Moodle-Kursregisterkarte zu einem Kanal abzuschließen.

## <a name="5-allow-automatic-creation-of-moodle-tabs-in-microsoft-teams"></a>5. Zulassen der automatischen Erstellung von Moodle-Registerkarten in Microsoft Teams

Obwohl die Moodle-Registerkarten in Microsoft Teams manuell erstellt werden, können Sie sie automatisch erstellen, wenn Teams über die Kurssynchronisierung erstellt werden. Dazu müssen Sie die ID der hochgeladenen Microsoft Teams-App in Moodle konfigurieren.

So ermöglichen Sie die automatische Erstellung von Moodle-Registerkarten:

1. Öffnen Sie Microsoft Teams.

1. Wählen Sie im unteren linken Bereich der Navigationsleiste das Symbol "Apps" aus.

1. Suchen Sie die hochgeladene **Moodle-App** > wählen Sie das **Optionssymbol** aus, > **link kopieren** auswählen.

1. Fügen Sie den kopierten Inhalt in einen Text-Editor ein. Er muss eine URL wie `https://teams.microsoft.com/l/app/00112233-4455-6677-8899-aabbccddeeff`z. B. enthalten. Kopieren Sie den letzten Teil der URL, z`00112233-4455-6677-8899-aabbccddeeff`. B. die ID der Microsoft Teams App.

1. Öffnen Sie in Moodle die Registerkarte **Teams Moodle-App** von Ihrer Konfigurationsseite Microsoft 365 Moodle-Plug-Ins.

1. Fügen Sie die ID der Microsoft Teams-App in das Id-Feld der Moodle-App ein, und speichern Sie die Änderungen.

Wenn ein Moodle-Kurs synchronisiert wird, installiert Microsoft Teams automatisch die Moodle-App im Team, erstellt eine Registerkarte "Moodle" im Kanal "Allgemein" von Teams und konfiguriert sie so, dass sie die Kursseite für den Moodle-Kurs enthält, von dem aus sie synchronisiert wird. Sie können jetzt direkt von Microsoft Teams aus mit Ihren Moodle-Kursen arbeiten.

> [!NOTE]
> Wenn Sie Featureanfragen oder Feedback mit uns teilen möchten, besuchen Sie unsere [User Voice-Seite](https://microsoftteams.uservoice.com/forums/916759-moodle).

## <a name="see-also"></a>Siehe auch

* [Integrieren von Web-Apps](~/samples/integrate-web-apps-overview.md)
* [Moodle](https://moodle.org/)
* [Moodle-Dokumentation](https://docs.moodle.org/34/en/Installing_plugins).
