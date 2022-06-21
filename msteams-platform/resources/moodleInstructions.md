---
title: Installieren von Moodle LMS
description: In diesem Artikel erfahren Sie, wie Sie die Moodle-Integrations-App für Microsoft Teams
ms.topic: how-to
ms.localizationpriority: medium
ms.author: lajanuar
author: surbhigupta
ms.openlocfilehash: 0c19d8bc4e3919fe49f6594c8ec738bafc1c76d3
ms.sourcegitcommit: 7bbb7caf729a00b267ceb8af7defffc91903d945
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/21/2022
ms.locfileid: "66189637"
---
# <a name="install-moodle-lms"></a>Installieren von Moodle LMS

In diesem Artikel erfahren Sie, wie Sie das Moodle LMS installieren.

> [!NOTE]
> Um IT-Administratoren bei der einfachen Einrichtung von Moodle und Teams Integration zu unterstützen, wird Open Source Microsoft 365 Moodle Plugins für Folgendes aktualisiert:
>
> * Automatische Registrierung Ihres Moodle-Servers mit [Microsoft Azure Active Directory (Azure AD)](https://azure.microsoft.com/services/active-directory/).
>
> * Bereitstellung Ihres Moodle Assistant-Bots in Azure mit einem Klick.
>
> * Automatische Bereitstellung von Teams und automatische Synchronisierung von Teamregistrierungen für alle oder ausgewählte Moodle-Kurse.
>
> * Automatische Installation der Registerkarte "Moodle" und des Moodle-Assistenten-Bots in jedem synchronisierten Team.
>
> Weitere Informationen zu den Funktionen, die diese Integration bietet, finden Sie [unter Microsoft Teams und Moodle](https://education.microsoft.com/resource/3dffb3a8).

## <a name="prerequisites"></a>Voraussetzungen

Es folgen die Voraussetzungen für die Installation von Moodle:

* Moodle-Administratoranmeldeinformationen.

* Azure AD-Administratoranmeldeinformationen.

* Ein Azure-Abonnement, in dem Sie neue Ressourcen erstellen können.

## <a name="1-install-the-microsoft-365-moodle-plugins"></a>1. Installieren Sie die Microsoft 365 Moodle Plugins

Die Moodle-Integration in Microsoft Teams wird durch das Open Source [Microsoft 365 Moodle Plug-Ins-Set](https://github.com/Microsoft/o365-moodle) unterstützt.

### <a name="requisite-applications-and-plugins"></a>Erforderliche Anwendungen und Plug-Ins

Stellen Sie sicher, dass Sie Folgendes installieren und herunterladen, bevor Sie mit der Installation der Microsoft 365 Moodle-Plug-Ins fortfahren:

1. Stellen Sie sicher, dass Sie eine [aktuelle stabile Version von Moodle](https://download.moodle.org/releases/latest/) installieren.

1. Laden Sie die Moodle [OpenID-Verbinden](https://moodle.org/plugins/auth_oidc) und die [Microsoft 365 Integration-Plugins](https://moodle.org/plugins/local_o365) herunter und speichern Sie sie auf Ihrem lokalen Computer.

    > [!NOTE]
    > Die Installation der OpenID-Verbinden- und Microsoft 365 Integrations-Plug-Ins ist für die Teams Integration erforderlich.
    >
    > Darüber hinaus wird das [Microsoft 365 Teams Theme](https://moodle.org/plugins/theme_boost_o365teams) Plugins dringend empfohlen.

### <a name="microsoft-365-moodle-plugins"></a>Microsoft 365 Moodle Plugins

1. Melden Sie sich als Administrator bei Ihrem Moodle-Server an, und wählen Sie "**Websiteverwaltung**" aus dem [Einstellungen Block](https://docs.moodle.org/22/en/Settings_block) im linken Navigationsbereich aus.

1. Wählen Sie die Registerkarte **"Plug-Ins** " und dann **"Plug-Ins installieren**" aus.

1. Wählen Sie im Abschnitt **"Plug-Ins aus ZIP-Datei installieren** " die **Option "Datei auswählen"** aus.

1. Wählen Sie im linken Navigationsbereich **Hochladen Dateioption** aus, suchen Sie nach der heruntergeladenen Datei, und wählen Sie **Hochladen diese Datei** aus.

1. Wählen Sie im linken Navigationsbereich die **Websiteverwaltung** aus, um zu Ihrem Administratordashboard zurückzukehren. Scrollen Sie nach unten zu den **lokalen Plug-Ins**, und wählen Sie den Link **Microsoft 365 Integration** aus.

    > [!IMPORTANT]
    >
    > * Lassen Sie Ihre Microsoft 365 Moodle Plugins-Konfigurationsseite auf einer separaten Browserregisterkarte geöffnet, da Sie während des gesamten Prozesses zu dieser Gruppe von Seiten zurückkehren müssen.  
    >
    > * Wenn Sie nicht über eine vorhandene Moodle-Website verfügen, wechseln Sie zum [Moodle on Azure-Repository](https://github.com/azure/moodle) , stellen Sie schnell eine Moodle-Instanz bereit, und passen Sie sie an Ihre Anforderungen an.

## <a name="2-configure-the-connection-between-the-microsoft-365-plugins-and-azure-ad"></a>2. Konfigurieren der Verbindung zwischen den Microsoft 365-Plug-Ins und Azure AD

Sie müssen die Verbindung zwischen den Microsoft 365-Plug-Ins und Azure AD konfigurieren.

### <a name="requisites"></a>Voraussetzungen

Registrieren Sie Moodle mithilfe des PowerShell-Skripts als Anwendung in Azure AD. Das Skript stellt Folgendes bereit:

* Eine neue Azure AD-Anwendung für Ihren Microsoft 365 Mandanten, die von den Microsoft 365 Moodle Plugins verwendet wird.
* Die App für Ihren Microsoft 365 Mandanten, richtet die erforderlichen Antwort-URLs und Berechtigungen für die bereitgestellte App ein und gibt die `AppID` `Key`und zurück.

Verwenden Sie die generierte `AppID` und `Key` in Ihrer Microsoft 365 Moodle Plugins-Setupseite, um Ihre Moodle-Serverwebsite mit Azure AD zu konfigurieren.

> [!IMPORTANT]
>
> * Das PowerShell-Skript wird nicht mit den neuesten Konfigurationselementen aktualisiert. Daher müssen Sie die Konfiguration manuell gemäß den Schritten ausführen, die auf den Moodle [3.8.0.4- und 3.9.1](https://docs.moodle.org/39/en/Office365#3.8.0.4_and_3.9.1_release) - und [3.8.0.5- und 3.9.2-Versionsseiten](https://docs.moodle.org/39/en/Office365#3.8.0.5_and_3.9.2_release) beschrieben sind.
>
> * Weitere Informationen zum manuellen Registrieren Ihrer Moodle-Instanz finden [Sie unter Registrieren Ihrer Moodle-Instanz als Anwendung](https://docs.moodle.org/34/en/Office365#Register_your_Moodle_instance_as_an_Application).

### <a name="the-moodle-tab-for-microsoft-teams-information-flow"></a>Registerkarte "Moodle" für Microsoft Teams Informationsfluss

<img width="530px" src="../assets/images/MoodleTabInformationFlow.png" alt="Moodle tab for Microsoft Teams information flow" />

1. Wählen Sie auf der Seite Microsoft 365 Integrations-Plug-Ins die Registerkarte **"Setup**" aus.

1. Wählen Sie die Schaltfläche **"PowerShell-Skript herunterladen** " aus, und speichern Sie sie als ZIP-Ordner auf Ihrem lokalen Computer.

1. Bereiten Sie das PowerShell-Skript aus der ZIP-Datei wie folgt vor:

    1. Laden Sie die Datei herunter, und extrahieren Sie sie `Moodle-AzureAD-Powershell.zip` .
    1. Öffnen Sie den extrahierten Ordner.
    1. Klicken Sie mit der rechten Maustaste auf die `Moodle-AzureAD-Script.ps1` Datei, und wählen Sie **"Eigenschaften"** aus.
    1. Aktivieren Sie auf der Registerkarte "**Allgemein**" des Eigenschaftenfenster das `Unblock` Kontrollkästchen neben dem **Sicherheitsattribut** am unteren Rand des Fensters.
    1. Wählen Sie **OK** aus.
    1. Kopieren Sie den Verzeichnispfad in den extrahierten Ordner.

1. Führen Sie PowerShell als Administrator aus:

    1. Klicken Sie auf Starten.
    1. Geben Sie PowerShell ein.
    1. Klicken Sie mit der rechten Maustaste auf **Windows PowerShell**.
    1. Wählen Sie **"Als Administrator ausführen" aus**.

1. Navigieren Sie zum entpackten Verzeichnis, indem Sie eingeben `cd .../.../Moodle-AzureAD-Powershell` , wo `.../...` sich der Pfad zum Verzeichnis befindet.

1. Führen Sie das PowerShell-Skript aus:

    1. `Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser` eingeben.
    1. `./Moodle-AzureAD-Script.ps1` eingeben.
    1. Melden Sie sich im Popupfenster bei Ihrem Microsoft 365 Administratorkonto an.
    1. Geben Sie den Namen der Azure AD-Anwendung ein, z. B. Moodle- oder Moodle-Plug-Ins.
    1. Geben Sie die URL für Ihren Moodle-Server ein.
    1. Kopieren Sie die vom Skript generierte **Anwendungs-ID (`AppID`)** und den **Anwendungsschlüssel(`Key`),** und speichern Sie sie.

1. Als Nächstes müssen Sie das `AppID` und `Key` dem Microsoft 365 Moodle Plugins hinzufügen. Kehren Sie zur Seite "Plugins-Verwaltung", "Websiteverwaltung > Plugins > Microsoft 365 Integration" zurück.

1. Fügen Sie auf der Registerkarte **"Setup** " die `AppID` `Key` zuvor kopierte Datei hinzu, und wählen Sie dann " **Änderungen speichern"** aus. Nachdem die Seite aktualisiert wurde, wird ein neuer Abschnitt **"Verbindungsmethode auswählen" angezeigt**.

1. **Aktivieren Sie in der Choose-Verbindungsmethode** das Kontrollkästchen **"Standard**", und wählen Sie dann erneut **"Änderungen speichern"** aus.

1. Nachdem die Seite aktualisiert wurde, können Sie einen weiteren neuen Abschnitt **Admin Zustimmung & zusätzlichen Informationen** sehen.
    1. Wählen Sie **"Admin Zustimmungslink bereitstellen**" aus, geben Sie Ihre Microsoft 365 Anmeldeinformationen für den globalen Administrator ein, und **stimmen Sie** dann zu, um die Berechtigungen zu erteilen.
    1. Wählen Sie neben dem **Azure AD-Mandantenfeld** die Schaltfläche " **Erkennen** " aus.
    1. Wählen Sie neben der **OneDrive for Business-URL** die Schaltfläche "**Erkennen**" aus.
    1. Nachdem die Felder ausgefüllt wurden, wählen Sie die Schaltfläche **"Änderungen speichern** " erneut aus.

1. Wählen Sie die Schaltfläche " **Aktualisieren** " aus, um die Installation zu überprüfen, und wählen Sie dann " **Änderungen speichern"** aus.

1. Synchronisieren Sie Benutzer zwischen Ihrem Moodle-Server und Azure AD. Erste Schritte:

    > [!NOTE]
    > Je nach Umgebung können Sie während dieser Phase verschiedene Optionen auswählen.

1. Synchronisieren Sie Benutzer zwischen Ihrem Moodle-Server und Azure AD. Je nach Umgebung können Sie während dieser Phase verschiedene Optionen auswählen. Erste Schritte:
    1. Wechseln Sie zur **Registerkarte "Einstellungen synchronisieren"**.

    1. Aktivieren Sie im Abschnitt **"Benutzer mit Azure AD synchronisieren** " die Kontrollkästchen, die für Ihre Umgebung gelten. Sie müssen Folgendes auswählen:  

        ✔ Erstellen Sie Konten in Moodle für Benutzer in Azure AD.

        ✔ Aktualisieren Sie alle Konten in Moodle für Benutzer in Azure AD.

    1. Im Abschnitt **"Einschränkung der Benutzererstellung** " können Sie einen Filter einrichten, um die Azure AD-Benutzer einzuschränken, die mit Moodle synchronisiert werden.
    1. Im Abschnitt **"Benutzerfeldzuordnung** " können Sie die Azure AD-Feldzuordnung an die Moodle-Benutzerprofil-Feldzuordnung anpassen.
    1. Im Abschnitt **Teams Synchronisieren** können Sie auswählen, dass Gruppen automatisch erstellt werden sollen, z. B. Teams für einige oder alle Ihrer vorhandenen Moodle-Kurse.

13. Um [Cron-Aufträge](https://docs.moodle.org/310/en/Cron) zu überprüfen und für die erste Ausführung manuell auszuführen, wählen Sie den Link zur **Verwaltungsseite für geplante Aufgaben** im Abschnitt **"Benutzer mit Azure AD synchronisieren** " aus. Dadurch gelangen Sie zur Seite **"Geplante Vorgänge** ".

    1. Scrollen Sie nach unten, suchen Sie die **Synchronisierungsbenutzer mit dem Azure AD-Auftrag** , und wählen Sie **"Jetzt ausführen"** aus.
    1. Wenn Sie Gruppen basierend auf vorhandenen Kursen erstellen möchten, können Sie die Aufgabe "Benutzergruppen erstellen" auch **in Microsoft 365** Auftrag ausführen.

    > [!NOTE]
    >
    > Der Moodle [Cron](https://docs.moodle.org/310/en/Cron) wird gemäß dem Aufgabenplan ausgeführt. Der Standardzeitplan ist einmal täglich. Der Cron muss jedoch häufiger ausgeführt werden, um alles synchron zu halten.

1. Kehren Sie zur Seite "Plugins-Verwaltung", **"Websiteverwaltung > Plugins > Microsoft 365 Integration**" zurück, und wählen Sie die **Teams Einstellungen** Seite aus.

1. Konfigurieren Sie **auf** der Seite Teams Einstellungen die erforderlichen Einstellungen, um die Teams App-Integration zu aktivieren.

    1. Um **OpenID Verbinden** zu aktivieren, wählen Sie den Link **"Authentifizierung verwalten**" aus, und wählen Sie das Augensymbol in der **Zeile "OpenId" Verbinden** aus, wenn es nicht verfügbar ist.
    1. Um die Frameeinbettung zu aktivieren, wählen Sie den **Link "HTTP-Sicherheit** " und dann das Kontrollkästchen neben **"Frameeinbettung zulassen**" aus.
    1. Um Webdienste zu aktivieren, die die Moodle-API-Features aktivieren, wählen Sie den Link **"Erweiterte Features"** aus, und stellen Sie dann sicher, dass das Kontrollkästchen neben **"Webdienste aktivieren"** aktiviert ist.
    1. Um die externen Dienste für Microsoft 365 zu aktivieren, wählen Sie den Link **"Externe Dienste**" aus, und gehen Sie dann wie folgt vor:  

        ✔ Wählen Sie in der Zeile **"Moodle Microsoft 365 Webservices**" die Option **"Bearbeiten"** aus.

        ✔ Aktivieren Sie das Kontrollkästchen neben **"Aktiviert"** und dann "**Änderungen speichern"**.

    1. Bearbeiten Sie ihre authentifizierten Benutzerberechtigungen, um ihnen das Erstellen von Webdiensttoken zu ermöglichen.

        ✔ Wählen Sie den Link **"Bearbeitungsrolle authentifizierter Benutzer** " aus.

        ✔ Scrollen Sie nach unten, suchen Sie die Funktion **zum Erstellen eines Webdiensttokens** , und aktivieren Sie das Kontrollkästchen **"Zulassen** ".

## <a name="3-deploy-the-moodle-assistant-bot-to-azure"></a>3. Bereitstellen des Moodle Assistant Bot in Azure

Der kostenlose Moodle Assistant Bot für Microsoft Teams hilft Lehrern und Schülern, Fragen zu ihren Kursen, Aufgaben, Noten und anderen Informationen in Moodle zu beantworten. Der Bot sendet außerdem Moodle-Benachrichtigungen an Schüler und Lehrer innerhalb Teams. Der Bot ist ein Open Source-Projekt, das von Microsoft verwaltet wird und auf [GitHub](https://github.com/microsoft/Moodle-Teams-Bot) verfügbar ist.

> [!NOTE]
>
> * Stellen Sie Ressourcen in Ihrem Azure-Abonnement bereit. Alle Ressourcen wurden mithilfe der **kostenlosen** Ebene konfiguriert. Je nach Verwendung Ihres Bots müssen Sie diese Ressourcen möglicherweise skalieren.
>
> * Um die Registerkarte Moodle ohne den Bot zu verwenden, fahren Sie mit [4](#4-deploy-your-microsoft-teams-app) fort.

### <a name="moodle-bot-information-flow"></a>Moodle-Bot-Informationsfluss

<img width="530px" src="../assets/images/MoodleBotInformationFlow.png" alt="Moodle bot for Microsoft Teams information flow" />

Um den Bot zu installieren, müssen Sie ihn auf der [Microsoft Identity Platform](https://identity.microsoft.com/Landing) registrieren. Auf diese Weise kann sich Ihr Bot bei Ihren Microsoft-Endpunkten authentifizieren.

So registrieren Sie Ihren Bot:

1. Wechseln Sie zur Verwaltungsseite für Plug-Ins, und wählen Sie dann **Plugins** aus. Wählen Sie unter **Microsoft 365 Integration** die Registerkarte **Teams Einstellungen** aus.

1. Wählen Sie den Link zum **Microsoft-Anwendungsregistrierungsportal** aus, und melden Sie sich mit Ihrer Microsoft-ID an.

1. Geben Sie einen Namen für Ihre App ein, z. B. MoodleBot, und wählen Sie die Schaltfläche " **Erstellen** " aus.

1. Kopieren Sie die **Anwendungs-ID**, und fügen Sie sie in das Feld **"Bot-Anwendungs-ID**" auf der Seite **"Team Einstellungen**" ein.

1. Wählen Sie die Schaltfläche " **Neues Kennwort generieren** " aus. Kopieren Sie das generierte Kennwort, und fügen Sie es in das Feld "**Bot-Anwendungskennwort**" auf der Seite **"Team Einstellungen**" ein.

1. Scrollen Sie zum Ende des Formulars, und wählen Sie **"Änderungen speichern"** aus.

Nachdem Sie Ihre Anwendungs-ID und Ihr Kennwort generiert haben, stellen Sie Ihren Bot in Azure bereit:

> [!div class="checklist"]
>
> * Wählen Sie **"In Azure bereitstellen**" aus, und füllen Sie das Formular mit den erforderlichen Informationen aus, z. B. botanwendungs-ID, Bot-Anwendungskennwort und Moodle Secret auf der **seite Teams Einstellungen**. Die Azure-Informationen befinden sich auf der **Setupseite** .
> * Aktivieren Sie nach Dem Ausfüllen des Formulars das Kontrollkästchen, um den Allgemeinen Geschäftsbedingungen zuzustimmen.
> * Wählen Sie **"Kaufen**" aus. Alle Azure-Ressourcen werden auf der kostenlosen Ebene bereitgestellt.

Nachdem die Ressourcen die Bereitstellung in Azure abgeschlossen haben, müssen Sie die Microsoft 365 Moodle-Plug-Ins mit einem Messaging-Endpunkt konfigurieren. Sie müssen den Endpunkt von Ihrem Bot in Azure abrufen:

1. Melden Sie sich im [Microsoft Azure-Portal](https://portal.azure.com) an.

1. Wählen Sie im linken Bereich **"Ressourcengruppen** " aus, und wählen Sie die Ressourcengruppe aus, die Sie während der Bereitstellung Ihres Bots verwendet oder erstellt haben.

1. Wählen Sie die **WebApp Bot-Ressource** aus der Liste der Ressourcen in der Gruppe aus.

1. Kopieren Sie den **Messaging-Endpunkt** aus dem Abschnitt **"Übersicht** ".

1. Öffnen Sie in Moodle die **Team Einstellungen** Seite Ihrer Microsoft 365 Moodle Plugins.

1. Fügen Sie im Feld **Bot-Endpunkt** die kopierte URL ein, und ändern Sie die *Wortnachrichten* in *Webhook*. Die URL muss wie folgt angezeigt werden: `https://botname.azurewebsites.net/api/webhook`

1. Klicken Sie auf **Änderungen speichern**.

1. Nachdem Sie die Änderungen gespeichert haben, wechseln Sie zurück zur Registerkarte "**Team Einstellungen**", wählen Sie die Schaltfläche "**Manifestdatei herunterladen**" aus, und speichern Sie das App-Manifestpaket zur weiteren Verwendung auf Ihrem Computer.

## <a name="4-deploy-your-microsoft-teams-app"></a>4. Bereitstellen Ihrer Microsoft Teams-App

Nachdem Ihr Bot in Azure bereitgestellt und für die Kommunikation mit Ihrem Moodle-Server konfiguriert wurde, müssen Sie Ihre Microsoft Teams-App bereitstellen. Dazu müssen Sie die App-Manifestdatei laden, die Sie im vorherigen Schritt von der Seite Microsoft 365 Moodle Plugins Team Einstellungen heruntergeladen haben.

Bevor Sie die App installieren, müssen Sie sicherstellen, dass externe Apps aktiviert und Apps hochgeladen werden. Weitere Informationen finden [Sie unter "Vorbereiten Ihres Microsoft 365 Mandanten](../concepts/build-and-test/prepare-your-o365-tenant.md)".

So stellen Sie Ihre App bereit:

1. Öffnen Sie **Microsoft Teams**.

1. Wählen Sie das **App-Symbol** im unteren linken Bereich der Navigationsleiste aus.

1. Wählen Sie die **Hochladen einen benutzerdefinierten App-Link** aus der Liste der Optionen aus.

   > [!NOTE]
   > Wenn Sie als globaler Administrator angemeldet sind, müssen Sie die Möglichkeit haben, die App in den App-Katalog Ihrer Organisation hochzuladen. Andernfalls können Sie die App nur für ein Team laden, in dem Sie Mitglied sind.

4. Wählen Sie das Paket aus, das `manifest.zip` Sie zuvor heruntergeladen haben, und wählen Sie **"Speichern"** aus. Wenn Sie das App-Manifestpaket nicht heruntergeladen haben, können Sie es von der Registerkarte **"Team" Einstellungen** der Plug-In-Konfigurationsseite in Moodle herunterladen.

Nachdem Sie die App installiert haben, können Sie die Registerkarte jedem Kanal hinzufügen, auf den Sie Zugriff haben. Navigieren Sie dazu zum Kanal, wählen Sie das **Pluszeichen** (➕) aus, und wählen Sie Ihre App aus der Liste aus. Folgen Sie den Anweisungen, um das Hinzufügen Ihrer Moodle-Kursregisterkarte zu einem Kanal abzuschließen.

## <a name="5-allow-automatic-creation-of-moodle-tabs-in-microsoft-teams"></a>5. Zulassen der automatischen Erstellung von Moodle-Registerkarten in Microsoft Teams

Obwohl die Moodle-Registerkarten manuell in Microsoft Teams erstellt werden, können Sie entscheiden, sie automatisch zu erstellen, wenn Teams anhand der Kurssynchronisierung erstellt werden. Dazu müssen Sie die ID der hochgeladenen Microsoft Teams-App in Moodle konfigurieren.

So ermöglichen Sie die automatische Erstellung von Moodle-Registerkarten:

1. Öffnen Sie Microsoft Teams.

1. Wählen Sie im unteren linken Bereich das Symbol "Apps" aus.

1. Suchen Sie die hochgeladene **Moodle-App** , > wählen Sie das **Optionssymbol** > Link **kopieren** aus.

1. Fügen Sie den kopierten Inhalt in einen Text-Editor ein. Es muss eine URL wie `https://teams.microsoft.com/l/app/00112233-4455-6677-8899-aabbccddeeff`enthalten. Kopieren Sie den letzten Teil der URL, z`00112233-4455-6677-8899-aabbccddeeff`. B. die ID der Microsoft Teams-App.

1. Öffnen Sie in Moodle die Registerkarte **Teams Moodle-App** auf der Konfigurationsseite für Microsoft 365 Moodle-Plug-Ins.

1. Fügen Sie die ID der Microsoft Teams-App in das Feld "Moodle-App-ID" ein, und speichern Sie die Änderungen.

Wenn ein Moodle-Kurs synchronisiert wird, installiert Teams automatisch die Moodle-App im Team, erstellt eine Moodle-Registerkarte im Kanal "Allgemein" von Teams und konfiguriert sie so, dass sie die Kursseite für den Moodle-Kurs enthält, aus dem er synchronisiert wird. Sie können jetzt direkt von Teams aus mit Ihren Moodle-Kursen arbeiten.

> [!NOTE]
> Besuchen Sie unsere [User Voice-Seite](https://support.microsoft.com/en-us/office/uservoice-pages-430e1a78-e016-472a-a10f-dc2a3df3450a), um Featureanfragen oder Feedback mit uns zu teilen.

## <a name="see-also"></a>Siehe auch

* [Integrieren von Web-Apps](~/samples/integrate-web-apps-overview.md)
* [Moodle](https://moodle.org/)
* [Moodle-Dokumentation](https://docs.moodle.org/34/en/Installing_plugins).
