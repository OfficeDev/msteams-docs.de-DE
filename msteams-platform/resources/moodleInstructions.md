---
title: Installieren von Moodle LMS
description: Installieren und Konfigurieren der Moodle-Integrations-App für Microsoft Teams
keywords: Teams Integrations-Plug-Ins für die Moodle-App
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
> Um IT-Administratoren bei der einfachen Einrichtung von Moodle und Teams zu helfen, werden Open-Source-Microsoft 365 Von Moodle-Plug-Ins für folgendes aktualisiert:
>
> * Automatische Registrierung Ihres Moodle-Servers [mit Azure Active Directory (Azure AD)](https://azure.microsoft.com/services/active-directory/).
>
> * Bereitstellung Ihres Moodle-Assistenten-Bots mit einem Klick in Azure.
>
> * Automatische Bereitstellung von Teams und automatische Synchronisierung von Teamregistrierungen für alle oder Auswählen von Moodle-Kursen.
>
> * Automatische Installation der Registerkarte "Moodle" und des "Moodle-Assistenten"-Bots in jedem synchronisierten Team.
>
> Weitere Informationen zu den Funktionen, die diese Integration bietet, finden Sie [unter Microsoft Teams und Moodle](https://education.microsoft.com/resource/3dffb3a8).

## <a name="prerequisites"></a>Voraussetzungen

Es folgen die Voraussetzungen für die Installation von Moodle:

* Anmeldeinformationen für den Administrator von "Moodle".

* Azure AD-Administratoranmeldeinformationen.

* Ein Azure-Abonnement, in dem Sie neue Ressourcen erstellen können.

## <a name="1-install-the-microsoft-365-moodle-plugins"></a>1. Installieren der Microsoft 365 Von Moodle-Plug-Ins

Die Integration von Moodle in Microsoft Teams wird durch die Open [Source-Microsoft 365 von Moodle-Plug-Ins unterstützt.](https://github.com/Microsoft/o365-moodle)

### <a name="requisite-applications-and-plugins"></a>Erforderliche Anwendungen und Plug-Ins

Stellen Sie sicher, dass Sie Folgendes installieren und herunterladen, bevor Sie mit der Installation der Microsoft 365 von Moodle-Plug-Ins fortfahren:

1. Stellen Sie sicher, [dass Sie eine aktuelle stabile Version von Moodle installieren.](https://download.moodle.org/releases/latest/)

1. Laden Sie die Moodle [OpenID-Verbinden](https://moodle.org/plugins/auth_oidc) und die Microsoft 365 Integrations-Plug-Ins auf Ihrem lokalen Computer herunter, und speichern Sie sie. [](https://moodle.org/plugins/local_o365)

    > [!NOTE]
    > Die Installation der OpenID-Verbinden und Microsoft 365 Integrations-Plug-Ins sind für die Integration Teams erforderlich.
    >
    > Darüber hinaus werden die [Microsoft 365 Teams Design-Plug-Ins](https://moodle.org/plugins/theme_boost_o365teams) dringend empfohlen.

### <a name="microsoft-365-moodle-plugins"></a>Microsoft 365 Moodle-Plug-Ins

1. Melden Sie sich als Administrator bei  Ihrem Moodle-Server an, und wählen Sie im Einstellungen im linken Navigationsbereich die Option Websiteverwaltung aus. [](https://docs.moodle.org/22/en/Settings_block)

1. Wählen Sie die **Registerkarte Plug-Ins** aus, und wählen Sie dann **Plug-Ins installieren aus.**

1. Wählen Sie **im Abschnitt Plug-Ins aus ZIP-Datei** installieren die Option Datei auswählen **aus.**

1. Wählen **Hochladen im** linken Navigationsbereich eine Dateioption aus, suchen Sie nach der heruntergeladenen Datei, und wählen Sie Hochladen datei **aus.**

1. Wählen **Sie websiteverwaltung** im linken Navigationsbereich aus, um zum Administratordashboard zurückzukehren. Scrollen Sie nach unten zu **den lokalen Plug-Ins,** und wählen **Sie den Link Microsoft 365 Integration** aus.

    > [!IMPORTANT]
    >
    > * Lassen Sie Microsoft 365 Die Konfigurationsseite von Moodle-Plug-Ins auf einer separaten Browserregisterkarte geöffnet, da Sie während des gesamten Prozesses zu diesem Seitensatz zurückkehren müssen.  
    >
    > * Wenn Sie über keine vorhandene Moodle-Website verfügen, wechseln Sie zum [Repository "Moodle on Azure",](https://github.com/azure/moodle) stellen Sie schnell eine Moodle-Instanz bereit, und passen Sie sie an Ihre Anforderungen an.

## <a name="2-configure-the-connection-between-the-microsoft-365-plugins-and-azure-active-directory-azure-ad"></a>2. Konfigurieren der Verbindung zwischen den Microsoft 365-Plug-Ins und Azure Active Directory (Azure AD)

Sie müssen die Verbindung zwischen den Microsoft 365 und Azure AD konfigurieren.

### <a name="requisites"></a>Requisiten

Registrieren Sie Moodle als Anwendung in Azure AD mithilfe des PowerShell-Skripts. Das Powershell-Skript enthält Folgendes:

* Eine neue Azure AD-Anwendung für Microsoft 365 Mandanten, die von den Microsoft 365 Verwendet wird.
* Die App für Microsoft 365 Mandanten, richten Sie die erforderlichen Antwort-URLs und Berechtigungen für die bereitgestellte App ein, und gibt `AppID` die und `Key` zurück.

Verwenden Sie die `AppID` generierte und in Microsoft 365 Setupseite von Moodle-Plug-Ins, um Ihre `Key` Moodle-Serverwebsite mit Azure AD zu konfigurieren.

> [!IMPORTANT]
>
> * Das PowerShell-Skript wird nicht mit den neuesten Konfigurationselementen aktualisiert. Daher müssen Sie die Konfiguration manuell nach den Schritten ausführen, die auf den Releaseseiten von Moodle [3.8.0.4 und 3.9.1](https://docs.moodle.org/39/en/Office365#3.8.0.4_and_3.9.1_release) und [3.8.0.5 und 3.9.2](https://docs.moodle.org/39/en/Office365#3.8.0.5_and_3.9.2_release) beschrieben sind.
>
> * Weitere Informationen zum manuellen Registrieren Ihrer Moodle-Instanz finden Sie unter [Registrieren Ihrer Moodle-Instanz als Anwendung.](https://docs.moodle.org/34/en/Office365#Register_your_Moodle_instance_as_an_Application)

### <a name="the-moodle-tab-for-microsoft-teams-information-flow"></a>Registerkarte "Moodle" für Microsoft Teams Informationsfluss

<img width="530px" src="../assets/images/MoodleTabInformationFlow.png" alt="Moodle tab for Microsoft Teams information flow" />

1. Wählen Sie auf Microsoft 365 Seite Integrations-Plug-Ins die **Registerkarte Setup** aus.

1. Wählen Sie **die Schaltfläche PowerShell-Skript herunterladen** aus, und speichern Sie sie als ZIP-Ordner auf Ihrem lokalen Computer.

1. Bereiten Sie das PowerShell-Skript aus der ZIP-Datei wie folgt vor: 

    1. Laden Sie die Datei herunter, und `Moodle-AzureAD-Powershell.zip` extrahieren Sie sie.
    1. Öffnen Sie den extrahierten Ordner.
    1. Klicken Sie mit der rechten Maustaste `Moodle-AzureAD-Script.ps1` auf die Datei, und wählen Sie **Eigenschaften aus.**
    1. Aktivieren Sie **unter der Registerkarte** Allgemein des Fensters Eigenschaften das Kontrollkästchen neben dem `Unblock` **Security-Attribut** am unteren Rand des Fensters.
    1. Klicken Sie auf **OK**.
    1. Kopieren Sie den Verzeichnispfad in den extrahierten Ordner.

1. Führen Sie PowerShell als Administrator aus:

    1. Klicken Sie auf Starten.
    1. Geben Sie PowerShell ein.
    1. Klicken Sie mit der rechten Maustaste **auf Windows PowerShell**.
    1. Wählen **Sie Als Administrator ausführen aus.**

1. Navigieren Sie zum entzippten Verzeichnis, indem Sie `cd .../.../Moodle-AzureAD-Powershell` eingeben, `.../...` wo sich der Pfad zum Verzeichnis befindet.

1. Führen Sie das PowerShell-Skript aus:

    1. Geben Sie `Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser` ein.
    1. Geben Sie `./Moodle-AzureAD-Script.ps1` ein.
    1. Melden Sie sich bei Microsoft 365 Administratorkonto im Popupfenster an.
    1. Geben Sie den Namen der Azure AD-Anwendung ein, z. B. "Moodle" oder "Moodle"-Plug-Ins.
    1. Geben Sie die URL für Ihren Moodle-Server ein.
    1. Kopieren Sie die vom Skript generierte **Anwendungs-ID ( `AppID` )** und den **Anwendungsschlüssel( `Key` ),** und speichern Sie sie.

1. Als Nächstes müssen Sie das `AppID` und zum Microsoft 365 Hinzufügen von `Key` Moodle-Plug-Ins hinzufügen. Kehren Sie zur Seite "Plug-Ins-Verwaltung", Websiteverwaltung > Plugins > Microsoft 365 Integration zurück.

1. Fügen Sie **auf der Registerkarte** Setup das -Element hinzu, das Sie zuvor kopiert `AppID` `Key` haben, und wählen Sie dann Änderungen **speichern aus.** Nach dem Aktualisieren der Seite wird ein neuer Abschnitt Verbindungsmethode **auswählen angezeigt.**

1. Aktivieren Sie **in der Methode Verbindung auswählen** das Kontrollkästchen Default , und wählen Sie dann Änderungen **erneut** speichern aus. 

1. Nach der Aktualisierung der Seite sehen Sie einen weiteren neuen Abschnitt **Administrator-Zustimmung & zusätzliche Informationen**.
    1. Wählen **Sie Link Administratorzuwilligung** bereitstellen aus, geben Microsoft 365 Anmeldeinformationen des globalen Administrators ein, und akzeptieren Sie **dann,** um die Berechtigungen zu erteilen.
    1. Wählen Sie neben dem **Feld Azure AD Tenant** die Schaltfläche **Erkennen** aus.
    1. Wählen Sie neben **OneDrive for Business URL** die Schaltfläche **Erkennen** aus.
    1. Nachdem die Felder auffüllt sind, wählen Sie erneut die Schaltfläche **Änderungen** speichern aus.

1. Wählen Sie die **Schaltfläche Aktualisieren** aus, um die Installation zu überprüfen, und wählen Sie dann Änderungen **speichern aus.**

1. Synchronisieren Sie Benutzer zwischen Ihrem Moodle-Server und Azure AD. Erste Schritte:

    > [!NOTE]
    > Je nach Umgebung können Sie während dieser Phase verschiedene Optionen auswählen.

1. Synchronisieren Sie Benutzer zwischen Ihrem Moodle-Server und Azure AD. Je nach Umgebung können Sie während dieser Phase verschiedene Optionen auswählen. Erste Schritte:
    1. Wechseln Sie zur **Registerkarte Einstellungen Synchronisieren.**

    1. Aktivieren Sie **im Abschnitt Benutzer mit Azure AD** synchronisieren die Kontrollkästchen, die für Ihre Umgebung gelten. Sie müssen Folgendes auswählen:  

        ✔ Erstellen von Konten in Moodle für Benutzer in Azure AD.

        ✔ Aktualisieren aller Konten in Moodle für Benutzer in Azure AD.

    1. Im Abschnitt **Einschränkung der** Benutzererstellung können Sie einen Filter einrichten, um die Azure AD-Benutzer zu beschränken, die mit Moodle synchronisiert sind.
    1. Im **Abschnitt Benutzerfeldzuordnung** können Sie die Azure AD an die Zuordnung von Moodle-Benutzerprofilen anpassen.
    1. Im Abschnitt **Teams Synchronisierung** können Sie auswählen, dass automatisch Gruppen erstellt werden, z. B. Teams für einige oder alle Ihrer vorhandenen Moodle-Kurse.

13. Wählen Sie zum Überprüfen [von Aufträgen](https://docs.moodle.org/310/en/Cron) und zum  manuellen Ausführen dieser Aufträge für die erste Ausführung den Link Verwaltung geplanter Aufgaben im Abschnitt Synchronisieren von Benutzern **mit Azure AD** aus. Dadurch gelangen Sie zur **Seite Geplante Vorgänge.**

    1. Scrollen Sie nach unten, und suchen Sie den **Auftrag Benutzer mit Azure AD** synchronisieren, und wählen Sie Jetzt ausführen **aus.**
    1. Wenn Sie Gruppen basierend auf vorhandenen Kursen erstellen möchten, können Sie auch das Erstellen von Benutzergruppen **in einem Microsoft 365** ausführen.

    > [!NOTE]
    >
    > Der [Moodle-Cron wird](https://docs.moodle.org/310/en/Cron) gemäß dem Vorgangszeitplan ausgeführt. Der Standardzeitplan ist einmal pro Tag. Der cron muss jedoch häufiger ausgeführt werden, um alles synchron zu halten.

1. Kehren Sie zur Seite "Plug-Ins"-Verwaltung, **Websiteverwaltung > Plugins > Microsoft 365 Integration** zurück, und wählen Sie die Seite **Teams Einstellungen** aus.

1. Konfigurieren Sie **auf Teams Einstellungen** Seite die erforderlichen Einstellungen, um die Integration der Teams zu ermöglichen.

    1. Um **OpenID Verbinden** zu aktivieren,  wählen Sie den Link Authentifizierung verwalten aus, und wählen Sie das Augensymbol in der **Zeile OpenId Verbinden** aus, wenn es ausgegraut ist.
    1. Um die Frameeinbettung zu aktivieren, wählen Sie den **Link HTTP-Sicherheit** aus, und aktivieren Sie dann das Kontrollkästchen neben **Frameeinbettung zulassen.**
    1. Um Webdienste zu aktivieren, die die Funktionen der Moodle-API aktivieren, wählen Sie den Link **Erweiterte Features** aus, und stellen Sie dann sicher, dass das Kontrollkästchen neben Webdienste **aktivieren** aktiviert ist.
    1. Um die externen Dienste für Microsoft 365 zu aktivieren, wählen Sie den Link **Externe** Dienste aus, und wählen Sie dann:  

        ✔ Wählen Sie **bearbeiten** in der Zeile **"Moodle Microsoft 365 Webservices"** aus.

        ✔ Aktivieren Sie das Kontrollkästchen neben **Aktiviert,** und wählen Sie **dann Änderungen speichern aus.**

    1. Bearbeiten Sie ihre authentifizierten Benutzerberechtigungen, damit sie Webdiensttoken erstellen können.

        ✔ Wählen Sie den **Link Bearbeitungsrolle Authentifizierter Benutzer** aus.

        ✔ Scrollen Sie nach unten, und suchen Sie die Funktion **Webdiensttoken** erstellen, und aktivieren Sie das **Kontrollkästchen Zulassen.**

## <a name="3-deploy-the-moodle-assistant-bot-to-azure"></a>3. Bereitstellen des "Moodle Assistant Bot" in Azure

Der kostenlose Moodle-Assistent-Bot für Microsoft Teams hilft Lehrern und Schülern, Fragen zu ihren Kursen, Aufgaben, Noten und anderen Informationen in Moodle zu beantworten. Der Bot sendet auch Moodle-Benachrichtigungen an Schüler und Lehrer innerhalb Teams. Der Bot ist ein von Microsoft verwaltetes Open-Source-Projekt, das unter [GitHub.](https://github.com/microsoft/Moodle-Teams-Bot)

> [!NOTE]
>
> * Stellen Sie Ressourcen für Ihr Azure-Abonnement bereit. Alle Ressourcen wurden mithilfe der kostenlosen **Ebene** konfiguriert. Je nach Verwendung Ihres Bots müssen Sie diese Ressourcen möglicherweise skalieren.
>
> * Um die Registerkarte "Moodle" ohne den Bot zu verwenden, fahren Sie mit [4 aus.](#4-deploy-your-microsoft-teams-app)

### <a name="moodle-bot-information-flow"></a>Informationen zum Moodle-Bot

<img width="530px" src="../assets/images/MoodleBotInformationFlow.png" alt="Moodle bot for Microsoft Teams information flow" />

Zum Installieren des Bots müssen Sie ihn auf der [Microsoft Identity Platform registrieren.](https://identity.microsoft.com/Landing) Auf diese Weise kann sich Ihr Bot bei Ihren Microsoft-Endpunkten authentifizieren. 

**So registrieren Sie Ihren Bot**

1. Wechseln Sie zur Verwaltungsseite der Plugins, und wählen Sie dann **Plug-Ins aus.** Wählen **Microsoft 365 Integration** die Registerkarte **Teams Einstellungen** aus.

1. Wählen Sie den **Link Microsoft Application Registration Portal** aus, und melden Sie sich mit Ihrer Microsoft-ID an.

1. Geben Sie einen Namen für Ihre App ein, z. B. "MoodleBot", und wählen Sie die **Schaltfläche Erstellen** aus.

1. Kopieren Sie **die Anwendungs-ID,** und fügen Sie sie auf der Seite **Teamanwendungs-ID Einstellungen** ein. 

1. Wählen Sie die **Schaltfläche Neues Kennwort generieren** aus. Kopieren Sie das generierte Kennwort, und fügen Sie es in das Feld **Botanwendungskennwort** auf der **Einstellungen** ein.

1. Scrollen Sie zum unteren Rand des Formulars, und wählen **Sie Änderungen speichern aus.**

Nachdem Sie Ihre Anwendungs-ID und Ihr Kennwort generiert haben, stellen Sie Ihren Bot in Azure bereit:

> [!div class="checklist"]
> * Wählen **Sie Bereitstellen in Azure** aus, und füllen Sie das Formular mit den erforderlichen Informationen aus, z. B. der Botanwendungs-ID, dem Botanwendungskennwort und dem geheimen "Moodle"-Teams Einstellungen Seite.  Die Azure-Informationen finden Sie auf der **Seite Setup.** 
> * Aktivieren Sie nach Dem Ausfüllen des Formulars das Kontrollkästchen, um den Allgemeinen Geschäftsbedingungen zu zustimmen.
> * Wählen Sie **Kaufen aus.** Alle Azure-Ressourcen werden auf der kostenlosen Ebene bereitgestellt.

Nachdem die Bereitstellung der Ressourcen in Azure abgeschlossen ist, müssen Sie die Microsoft 365 von Moodle mit einem Messagingendpunkt konfigurieren. Sie müssen den Endpunkt von Ihrem Bot in Azure erhalten:

1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.

1. Wählen Sie im linken Bereich **Ressourcengruppen aus,** und wählen Sie die Ressourcengruppe aus, die Sie beim Bereitstellen des Bots verwendet oder erstellt haben.

1. Wählen Sie **die WebApp Bot-Ressource** aus der Liste der Ressourcen in der Gruppe aus.

1. Kopieren Sie **den Messagingendpunkt** aus dem **Abschnitt** Übersicht.

1. Öffnen Sie in Moodle die **Seite Team Einstellungen** Ihrer Microsoft 365-Plug-Ins.

1. Fügen Sie **im Feld BotEndpunkt** die URL ein, die Sie gerade kopiert haben, und ändern Sie das Wort *Nachrichten* in *Webhook*. Die URL muss wie folgt angezeigt werden: `https://botname.azurewebsites.net/api/webhook`

1. Wählen **Sie Änderungen speichern aus.**

1. Wechseln Sie nach dem Speichern der Änderungen zur Registerkarte  Team Einstellungen, wählen Sie die Schaltfläche Manifestdatei herunterladen aus, und speichern Sie das **App-Manifestpaket** zur weiteren Verwendung auf Ihrem Computer.

## <a name="4-deploy-your-microsoft-teams-app"></a>4. Bereitstellen ihrer Microsoft Teams App

Nachdem Ihr Bot in Azure bereitgestellt und für das Sprechen mit Ihrem Moodle-Server konfiguriert wurde, müssen Sie Ihre Microsoft Teams bereitstellen. Dazu müssen Sie die App-Manifestdatei laden, die Sie im vorherigen Schritt von der Microsoft 365 -Seite des Moodle-Plug-Ins-Einstellungen heruntergeladen haben.

Bevor Sie die App installieren, müssen Sie sicherstellen, dass externe Apps aktiviert und Apps hochgeladen werden. Weitere Informationen finden Sie unter [Prepare your Microsoft 365 tenant](../concepts/build-and-test/prepare-your-o365-tenant.md). 

**So stellen Sie Ihre App zur Bereitstellung** 

1. Öffnen **Microsoft Teams**. 

1. Wählen Sie **im** unteren linken Bereich der Navigationsleiste das Symbol App aus.

1. Wählen Sie **Hochladen einen benutzerdefinierten App-Link** aus der Liste der Optionen aus.

   > [!NOTE]
   > Wenn Sie als globaler Administrator angemeldet sind, müssen Sie die Möglichkeit haben, die App in den App-Katalog Ihrer Organisation hochzuladen, andernfalls können Sie die App nur für ein Team laden, in dem Sie Mitglied sind.

4. Wählen Sie das `manifest.zip` paket aus, das Sie zuvor heruntergeladen haben, und wählen Sie **Speichern aus.** Wenn Sie das App-Manifestpaket nicht heruntergeladen haben, können Sie auf der Registerkarte **Team Einstellungen** der Konfigurationsseite für Plug-Ins in Moodle herunterladen.

Nachdem Sie die App installiert haben, können Sie die Registerkarte zu jedem Kanal hinzufügen, auf den Sie Zugriff haben. Navigieren Sie dazu zum Kanal, wählen Sie das **Plussymbol** (➕) aus, und wählen Sie Ihre App aus der Liste aus. Folgen Sie den Eingabeaufforderungen, um das Hinzufügen Ihrer Registerkarte "Moodle-Kurs" zu einem Kanal zu beenden.

## <a name="5-allow-automatic-creation-of-moodle-tabs-in-microsoft-teams"></a>5. Automatisches Erstellen von Registerkarten von "Moodle" in Microsoft Teams

Obwohl die Registerkarten "Moodle" manuell in Microsoft Teams erstellt werden, können Sie sie automatisch erstellen, wenn Teams aus der Kurssynchronisierung erstellt werden. Dazu müssen Sie die ID der hochgeladenen app Microsoft Teams in Moodle konfigurieren.

**So ermöglichen Sie die automatische Erstellung von Registerkarten für "Moodle"**

1. Öffnen Sie Microsoft Teams.

1. Wählen Sie im unteren linken Bereich der Navigationsleiste das Symbol Apps aus.

1. Suchen Sie die hochgeladene **Moodle->** wählen **Sie** das Optionssymbol aus, > Link **kopieren auswählen.**

1. Fügen Sie in einem Texteditor den kopierten Inhalt ein. Sie muss eine URL wie ht-&#8203;tps://teams.microsoft.com/l/app/00112233-4455-6677-8899-aabbccddeeff. Kopieren Sie den letzten Teil der URL, z. B. , der die `00112233-4455-6677-8899-aabbccddeeff` ID der Microsoft Teams ist.

1. Öffnen Sie in Moodle die **Registerkarte Teams Der App-Microsoft 365** von Moodle-Plug-Ins.

1. Fügen Sie die ID der Microsoft Teams in das Feld App-ID von Moodle ein, und speichern Sie Änderungen.

Wenn ein Moodle-Kurs synchronisiert wird, installiert Microsoft Teams automatisch die Moodle-App im Team, erstellt eine Registerkarte "Moodle" im Kanal Allgemein von Teams und konfiguriert sie so, dass sie die Kursseite für den Kurs "Moodle" enthält, von dem aus er synchronisiert wird. Sie können jetzt direkt von der Website aus mit Ihren Moodle-Kursen Microsoft Teams.

> [!NOTE]
> Wenn Sie Featureanforderungen oder Feedback an uns senden möchten, besuchen Sie unsere [User Voice-Seite](https://microsoftteams.uservoice.com/forums/916759-moodle).

## <a name="see-also"></a>Siehe auch

- [Integrieren von Web-Apps](~/samples/integrate-web-apps-overview.md)
- [Moodle](https://moodle.org/)
- [Dokumentation zu "Moodle".](https://docs.moodle.org/34/en/Installing_plugins)

