---
title: Installieren von Moodle LMS
description: Installieren und Konfigurieren der Moodle-Integrations-App für Microsoft Teams
keywords: Teams Moodle-App-Integrations-Plug-In
ms.topic: how-to
localization_priority: Normal
ms.author: lajanuar
author: laujan
ms.openlocfilehash: 091192054c5add7cfbdc1e7baabc86e34cef7631
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020592"
---
# <a name="install-moodle-lms"></a>Installieren von Moodle LMS

Moodle ist ein beliebtes Open-Source Learning Management System (LMS). Es ist jetzt in Microsoft Teams integriert. Diese Integration hilft Lehrkräften und Lehrkräften bei der Zusammenarbeit an Kursen von Moodle, beim Stellen von Fragen zu Noten und Aufgaben und bei der Aktualisierung von Benachrichtigungen direkt in Teams.

Damit IT-Administratoren diese Integration problemlos einrichten können, wird das Open-Source-Microsoft 365-Moodle-Plug-In mit den folgenden Funktionen aktualisiert:

* Automatische Registrierung Ihres Moodle-Servers mit [Azure Active Directory](https://azure.microsoft.com/services/active-directory/) (Azure AD).
* Bereitstellung Ihres Moodle-Assistenten-Bots mit einem Klick in Azure.
* Automatische Bereitstellung von Teams und automatische Synchronisierung von Teamregistrierungen für alle oder Auswählen von Moodle-Kursen.
* Automatische Installation der Registerkarte "Moodle" und des "Moodle-Assistenten"-Bots in jedem synchronisierten Team.

Weitere Informationen zu den Funktionen, die diese Integration bietet, finden Sie unter [Microsoft Teams und Moodle](https://education.microsoft.com/resource/3dffb3a8).

## <a name="prerequisites"></a>Voraussetzungen

Im Folgenden sind die Voraussetzungen für die Installation und Konfiguration der Moodle-Anwendung zu finden: 

1. Anmeldeinformationen für den Administrator von "Moodle".

1. Azure AD-Administratoranmeldeinformationen.

1. Ein Azure-Abonnement, in dem Sie neue Ressourcen erstellen können.

**So installieren und konfigurieren Sie die Moodle-Anwendung** 

Führen Sie die folgenden Schritte aus, um die Moodle-Anwendung zu installieren und zu konfigurieren: 

## <a name="1-install-the-microsoft-365-moodle-plugins"></a>1. Installieren der Microsoft 365-Moodle-Plug-Ins

Die Integration von Moodle in Microsoft Teams wird vom Open Source [Microsoft 365 Moodle-Plug-In-Set unterstützt.](https://github.com/Microsoft/o365-moodle) Zum Installieren des Plug-Ins auf Ihrem Moodle-Server müssen die folgenden Anwendungen installiert sein:

1. Eine [aktuelle stabile Version von Moodle](https://download.moodle.org/releases/latest/).

1. Die Moodle [OpenID Connect](https://moodle.org/plugins/auth_oidc) und [die Microsoft 365](https://moodle.org/plugins/local_o365) Integration-Plug-Ins heruntergeladen und auf Ihrem lokalen Computer gespeichert.

   > [!NOTE]
   > Die Installation der OpenID Connect- und Microsoft 365-Integrations-Plug-Ins ist für die Microsoft Teams-Integration erforderlich. Darüber hinaus wird [das Microsoft 365 Teams](https://moodle.org/plugins/theme_boost_o365teams) Design-Plug-In dringend empfohlen.

1. Melden Sie sich als Administrator bei  Ihrem Moodle-Server an, und wählen Sie im Block [Einstellungen](https://docs.moodle.org/22/en/Settings_block) im linken Navigationsbereich die Option Websiteverwaltung aus.

1. Wählen Sie die **Registerkarte Plug-Ins** aus, und wählen Sie dann **Plug-Ins installieren aus.**

1. Wählen Sie **im Abschnitt Plug-In aus ZIP-Datei installieren** die Schaltfläche Datei **auswählen** aus.

1. Wählen **Sie im linken Navigationsbereich** die Option Datei hochladen aus, suchen Sie nach der heruntergeladenen Datei, und wählen Sie Diese Datei hochladen **aus.**

1. Wählen Sie **die Websiteverwaltung** im linken Navigationsbereich aus, um zum Administratordashboard zurückzukehren. Scrollen Sie nach unten zu **den lokalen Plug-Ins,** und wählen Sie den **Microsoft 365-Integrationslink** aus. 

> [!IMPORTANT]
>
> * Lassen Sie Ihre Microsoft 365-Moodle-Plugin-Konfigurationsseite auf einer separaten Browserregisterkarte geöffnet, da Sie während des gesamten Prozesses zu diesem Seitensatz zurückkehren müssen.  <br/><br/>
> * Wenn Sie nicht über eine vorhandene Moodle-Website verfügen, [](https://github.com/azure/moodle) können Sie das Moodle on Azure-Repository besuchen, in dem Sie eine Moodle-Instanz schnell bereitstellen und an Ihre Anforderungen anpassen können.

## <a name="2-configure-the-connection-between-the-microsoft-365-plugin-and-azure-active-directory-azure-ad"></a>2. Konfigurieren der Verbindung zwischen dem Microsoft 365-Plug-In und Azure Active Directory (Azure AD)

Sie müssen Moodle als Anwendung in Azure AD registrieren. Verwenden Sie das PowerShell-Skript, um diesen Prozess auszuführen. Das PowerShell-Skript stellt eine neue Azure AD-Anwendung für Ihren Microsoft 365-Mandanten bereit, die vom Microsoft 365-Moodle-Plug-In verwendet wird. Das Skript stellt die App für Ihren Microsoft 365-Mandanten, die erforderlichen Antwort-URLs und Berechtigungen für die bereitgestellte App ein, und gibt `AppID` die und `Key` zurück. Sie können die generierte und auf Ihrer `AppID` `Key` Microsoft 365-Setupseite für das Moodle-Plug-In verwenden, um Ihre Moodle-Serverwebsite mit Azure AD zu konfigurieren.

> [!IMPORTANT]
> * Das PowerShell-Skript wird nicht mit den neuesten Konfigurationselementen aktualisiert, daher müssen Sie die Konfiguration manuell nach den Schritten ausführen, die auf den Releaseseiten von Moodle [3.8.0.4 und 3.9.1](https://docs.moodle.org/39/en/Office365#3.8.0.4_and_3.9.1_release) und [3.8.0.5 und 3.9.2](https://docs.moodle.org/39/en/Office365#3.8.0.5_and_3.9.2_release) beschrieben sind. </br></br>
> * Informationen zu den manuellen Schritten, die das PowerShell-Skript automatisiert, finden Sie unter [Registrieren Ihrer Moodle-Instanz als Anwendung.](https://docs.moodle.org/34/en/Office365#Register_your_Moodle_instance_as_an_Application)

### <a name="the-moodle-tab-for-microsoft-teams-information-flow"></a>Informationen über die Registerkarte "Moodle" für Microsoft Teams

<img width="530px" src="../assets/images/MoodleTabInformationFlow.png" alt="Moodle tab for Microsoft Teams information flow" />

1. Wählen Sie auf der Seite Microsoft 365-Integrations-Plug-In die **Registerkarte Setup** aus.

1. Wählen Sie **die Schaltfläche PowerShell-Skript herunterladen** aus, und speichern Sie sie auf Ihrem lokalen Computer.

1. Sie müssen das PowerShell-Skript aus der ZIP-Datei vorbereiten. Führen Sie die folgenden Schritte aus, um das PowerShell-Skript aus der ZIP-Datei vorzubereiten:

    1. Laden Sie die Datei herunter, und `Moodle-AzureAD-Powershell.zip` extrahieren Sie sie.
    1. Öffnen Sie den extrahierten Ordner.
    1. Klicken Sie mit der rechten Maustaste `Moodle-AzureAD-Script.ps1` auf die Datei, und wählen Sie **Eigenschaften aus.**
    1. Aktivieren Sie **unter der Registerkarte** Allgemein des Fensters Eigenschaften das Kontrollkästchen neben dem `Unblock` **Security-Attribut** am unteren Rand des Fensters.
    1. Wählen Sie **OK** aus.
    1. Kopieren Sie den Verzeichnispfad in den extrahierten Ordner.

1. Führen Sie PowerShell als Administrator aus:

    1. Klicken Sie auf Starten.
    1. Geben Sie PowerShell ein.
    1. Klicken Sie mit der rechten Windows PowerShell.
    1. Wählen **Sie Als Administrator ausführen aus.**

1. Navigieren Sie zum entzippten Verzeichnis, indem Sie `cd .../.../Moodle-AzureAD-Powershell` eingeben, `.../...` wo sich der Pfad zum Verzeichnis befindet.

1. Führen Sie das PowerShell-Skript aus:

    1. Geben Sie `Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser` ein.
    1. Geben Sie `./Moodle-AzureAD-Script.ps1` ein.
    1. Melden Sie sich im Popupfenster bei Ihrem Microsoft 365-Administratorkonto an.
    1. Geben Sie den Namen der Azure AD-Anwendung ein (z. B. Das Moodle/Moodle-Plug-In).
    1. Geben Sie die URL für Ihren Moodle-Server ein.
    1. Kopieren Sie die vom Skript **generierte** **Anwendungs-ID** und den Anwendungsschlüssel, und speichern Sie sie.

1. Als Nächstes müssen Sie das `AppID` und `Key` zum Microsoft 365-Moodle-Plug-In hinzufügen. Kehren Sie zur Seite für die Verwaltung des Plug-Ins zurück. Der Ablauf ist: Websiteverwaltung ➡ Plugins ➡ Microsoft 365-Integration.

1. Fügen Sie **auf der Registerkarte Setup** die **Anwendungs-ID** und den **Anwendungsschlüssel** hinzu, die Sie zuvor kopiert haben, und wählen Sie **Dann Änderungen speichern aus.**

1. Nach dem Aktualisieren der Seite wird ein neuer Abschnitt Verbindungsmethode **auswählen angezeigt.** Aktivieren Sie das Kontrollkästchen **Standard,** und wählen Sie dann **Änderungen erneut** speichern aus.

1. Nach der Aktualisierung der Seite sehen Sie einen weiteren neuen Abschnitt **Administrator-Zustimmung & zusätzliche Informationen**.
    1. Wählen **Sie Link Administratorzuwilligung** bereitstellen aus, geben Sie Ihre Microsoft 365-Anmeldeinformationen für den globalen Administrator ein, und akzeptieren Sie **dann,** um die Berechtigungen zu erteilen.
    1. Wählen Sie neben dem **Feld Azure AD Tenant** die Schaltfläche **Erkennen** aus.
    1. Wählen Sie neben **der OneDrive for #A0** die Schaltfläche **Erkennen** aus.
    1. Nachdem die Felder auffüllt sind, wählen Sie erneut die Schaltfläche **Änderungen** speichern aus.

1. Wählen Sie die **Schaltfläche Aktualisieren** aus, um die Installation zu überprüfen, und speichern Sie **dann Änderungen**.

1. Synchronisieren Sie Benutzer zwischen Ihrem Moodle-Server und Azure AD. Je nach Umgebung können Sie während dieser Phase verschiedene Optionen auswählen. Erste Schritte:
    1. Wechseln zur Registerkarte **Synchronisierungseinstellungen**
    1. Aktivieren Sie **im Abschnitt Benutzer mit Azure AD** synchronisieren die Kontrollkästchen, die für Ihre Umgebung gelten. Sie müssen Folgendes auswählen:  

        ✔ Erstellen von Konten in Moodle für Benutzer in Azure AD . 
        ✔ Aktualisieren aller Konten in Moodle für Benutzer in Azure AD.  

    1. Im Abschnitt **Einschränkung der** Benutzererstellung können Sie einen Filter einrichten, um die Azure AD-Benutzer zu beschränken, die mit Moodle synchronisiert sind.
    1. Im **Abschnitt Benutzerfeldzuordnung** können Sie die Azure AD an die Zuordnung von Moodle-Benutzerprofilen anpassen.
    1. Im Abschnitt **Teams Sync** können Sie auswählen, dass automatisch Gruppen erstellt werden, z. B. Teams für einige oder alle Ihrer vorhandenen Moodle-Kurse.

> [!NOTE]
> Der [Moodle-Cron wird](https://docs.moodle.org/310/en/Cron) gemäß dem Vorgangszeitplan ausgeführt. Der Standardzeitplan ist einmal pro Tag. Der cron muss jedoch häufiger ausgeführt werden, um alles synchron zu halten.

13. Wählen Sie zum Überprüfen [von Aufträgen](https://docs.moodle.org/310/en/Cron) und zum  manuellen Ausführen dieser Aufträge für die erste Ausführung den Link Verwaltung geplanter Aufgaben im Abschnitt Synchronisieren von Benutzern **mit Azure AD** aus. Dadurch gelangen Sie zur **Seite Geplante Vorgänge.**

    1. Scrollen Sie nach unten, und suchen Sie den **Auftrag Benutzer mit Azure AD** synchronisieren, und wählen Sie Jetzt ausführen **aus.**
    1. Wenn Sie Gruppen basierend auf vorhandenen Kursen erstellen möchten, können Sie auch den Auftrag Benutzergruppen **in Microsoft 365 erstellen** ausführen.

1. Kehren Sie zur Seite für die Verwaltung des Plug-Ins zurück. Der Navigationsfluss ist: Websiteverwaltung ➡ Plugins ➡ Microsoft 365 Integratio. Wählen Sie dann die Seite **Teams-Einstellungen** aus. Sie müssen einige Einstellungen konfigurieren, um die Integration der Teams-App zu aktivieren.

    1. Um **OpenID Connect zu aktivieren,** wählen Sie den Link Authentifizierung verwalten aus, und wählen Sie das Augensymbol in der **OpenId Connect-Zeile** aus, wenn es ausgegraut ist. 
    1. Aktivieren sie die Frameeinbettung. Wählen Sie **den Link HTTP-Sicherheit** und dann das Kontrollkästchen neben **Frameeinbettung zulassen aus.**
    1. Aktivieren Sie Webdienste, die die Funktionen der Moodle-API aktivieren. Wählen Sie **den Link Erweiterte Features** aus, und stellen Sie sicher, dass das Kontrollkästchen neben **Webdienste** aktivieren aktiviert ist.
    1. Aktivieren Sie die externen Dienste für Microsoft 365. Wählen Sie **dann den** Link Externe Dienste aus:  

        ✔ Wählen Sie **Bearbeiten** in der **Zeile Moodle Microsoft 365 Webservices** aus.  
        ✔ Aktivieren Sie das Kontrollkästchen neben **Aktiviert,** und wählen Sie **dann Änderungen speichern aus.**

    1. Bearbeiten Sie ihre authentifizierten Benutzerberechtigungen, damit sie Webdiensttoken erstellen können. Wählen Sie **den Link Bearbeitungsrolle "Authentifizierter Benutzer"** aus. Scrollen Sie nach unten, und suchen Sie die **Funktion Webdiensttoken** erstellen, und aktivieren Sie das **Kontrollkästchen Zulassen.**

## <a name="3-deploy-the-moodle-assistant-bot-to-azure"></a>3. Bereitstellen des "Moodle Assistant Bot" in Azure

Der kostenlose Moodle-Assistent-Bot für Microsoft Teams hilft Lehrern und Schülern, Fragen zu ihren Kursen, Aufgaben, Noten und anderen Informationen in Moodle zu beantworten. Der Bot sendet auch Moodle-Benachrichtigungen an Schüler und Lehrer in Teams. Der Bot ist ein open-source-Projekt, das von Microsoft verwaltet wird und auf [GitHub verfügbar ist.](https://github.com/microsoft/Moodle-Teams-Bot)

> [!NOTE]
> * In diesem Abschnitt müssen Sie Ressourcen für Ihr Azure-Abonnement bereitstellen. Alle Ressourcen werden mithilfe der kostenlosen **Ebene** konfiguriert. Je nach Verwendung Ihres Bots können Sie diese Ressourcen skalieren.
> * Um die Registerkarte "Moodle" ohne den Bot zu verwenden, fahren Sie mit [4 aus.](#4-deploy-your-microsoft-teams-app)

### <a name="moodle-bot-information-flow"></a>Informationen zum Moodle-Bot

<img width="530px" src="../assets/images/MoodleBotInformationFlow.png" alt="Moodle bot for Microsoft Teams information flow" />

Zum Installieren des Bots müssen Sie ihn auf der [Microsoft Identity Platform registrieren.](https://identity.microsoft.com/Landing) Auf diese Weise kann sich Ihr Bot bei Ihren Microsoft-Endpunkten authentifizieren. 

**So registrieren Sie Ihren Bot:**

1. Wechseln Sie zur Seite für die Verwaltung des Plug-Ins. Wechseln Sie zu **Plugins**. Wählen **Sie unter Microsoft 365-Integration** die Registerkarte **Teams-Einstellungen** aus.

1. Wählen Sie den **Link Microsoft Application Registration Portal** aus, und melden Sie sich mit Ihrer Microsoft-ID an.

1. Geben Sie einen Namen für Ihre App ein, z. B. "MoodleBot", und wählen Sie die **Schaltfläche Erstellen** aus.

1. Kopieren Sie **die Anwendungs-ID,** und fügen Sie sie in das **Feld Botanwendungs-ID** auf der **Seite Teameinstellungen** ein.

1. Wählen Sie die **Schaltfläche Neues Kennwort generieren** aus. Kopieren Sie das generierte Kennwort, und fügen Sie es in das Feld **Bot-Anwendungskennwort** auf der Seite **Teameinstellungen** ein.

1. Scrollen Sie zum unteren Rand des Formulars, und wählen **Sie Änderungen speichern aus.**

Während Sie Ihre Anwendungs-ID und Ihr Kennwort generiert haben, besteht der nächste Schritt in der Bereitstellung Ihres Bots in Azure:

> [!div class="checklist"]
> * Wählen Sie **die Schaltfläche Bereitstellen in Azure** aus, und füllen Sie das Formular mit den erforderlichen Informationen aus, z. B. die Bot-Anwendungs-ID, das Kennwort der Botanwendung und das Geheime Kennwort für Die Geheime Einstellung von Moodle befinden sich auf der Seite **Teameinstellungen.** Die Azure-Informationen finden Sie auf der **Seite Setup).** 
> * Aktivieren Sie nach Dem Ausfüllen des Formulars das Kontrollkästchen, um den Allgemeinen Geschäftsbedingungen zu zustimmen.
> * Wählen Sie die **Schaltfläche Kaufen** aus. Alle Azure-Ressourcen werden auf der kostenlosen Ebene bereitgestellt.

Nachdem die Bereitstellung der Ressourcen in Azure abgeschlossen ist, müssen Sie das Microsoft 365-Moodle-Plug-In mit einem Messagingendpunkt konfigurieren. Sie müssen den Endpunkt von Ihrem Bot in Azure erhalten:

**Konfigurieren des Microsoft 365-Moodle-Plug-Ins mit einem Messagingendpunkt**  
1. Melden Sie sich beim [Azure-Portal](https://portal.azure.com) an.

1. Wählen Sie im linken Bereich **Ressourcengruppen aus,** und wählen Sie die Ressourcengruppe aus, die Sie beim Bereitstellen des Bots verwendet oder erstellt haben.

1. Wählen Sie **die WebApp Bot-Ressource** aus der Liste der Ressourcen in der Gruppe aus.

1. Kopieren Sie **den Messagingendpunkt** aus dem **Abschnitt** Übersicht.

1. Öffnen Sie in Moodle die **Seite Teameinstellungen** Ihres Microsoft 365-Moodle-Plug-Ins.

1. Fügen Sie **im Feld BotEndpunkt** die URL ein, die Sie gerade kopiert haben, und ändern Sie das Wort *Nachrichten* in *Webhook*. Die URL sollte nun wie folgt angezeigt werden: `https://botname.azurewebsites.net/api/webhook`

1. Wählen **Sie Änderungen speichern aus.**

1. Wechseln Sie nach dem Speichern  der Änderungen zur  Registerkarte Teameinstellungen, wählen Sie die Schaltfläche Manifestdatei herunterladen aus, und speichern Sie das App-Manifestpaket zur weiteren Verwendung auf Ihrem Computer.

## <a name="4-deploy-your-microsoft-teams-app"></a>4. Bereitstellen Ihrer Microsoft Teams-App

Nachdem Ihr Bot in Azure bereitgestellt und für das Sprechen mit Ihrem Moodle-Server konfiguriert wurde, müssen Sie Ihre Microsoft Teams-App bereitstellen. Dazu müssen Sie die App-Manifestdatei laden, die Sie im vorherigen Schritt von der Seite Microsoft 365 Moodle-Plugin-Teameinstellungen heruntergeladen haben.

Bevor Sie die App installieren, müssen Sie sicherstellen, dass externe Apps aktiviert und Apps hochgeladen werden. Dazu können Sie die Schritte in der Dokumentation zu Microsoft [365-Mandanten](../concepts/build-and-test/prepare-your-o365-tenant.md) vorbereiten von Teams ausführen. Sie können die folgenden Schritte ausführen, um Ihre App zu bereitstellen: 

**So stellen Sie Ihre App zur Bereitstellung**

1. Öffnen **Sie Microsoft Teams**. 

1. Wählen Sie **im** unteren linken Bereich der Navigationsleiste das Symbol App aus.

1. Wählen Sie **in der Liste** der Optionen den Link Benutzerdefinierte App hochladen aus.

   > [!NOTE]
   > Wenn Sie als globaler Administrator angemeldet sind, müssen Sie die Möglichkeit haben, die App in den App-Katalog Ihrer Organisation hochzuladen, andernfalls können Sie die App nur für ein Team laden, in dem Sie Mitglied sind.

4. Wählen Sie das `manifest.zip` paket aus, das Sie zuvor heruntergeladen haben, und wählen Sie **Speichern aus.** Wenn Sie das App-Manifestpaket nicht heruntergeladen haben, können Sie auf der Registerkarte **Teameinstellungen** auf der Seite "Plug-In-Konfiguration" in Moodle herunterladen.

Nachdem Sie die App installiert haben, können Sie die Registerkarte zu jedem Kanal hinzufügen, auf den Sie Zugriff haben. Navigieren Sie dazu zum Kanal, wählen Sie das **Plussymbol** (➕) aus, und wählen Sie Ihre App aus der Liste aus. Folgen Sie den Eingabeaufforderungen, um das Hinzufügen Ihrer Registerkarte "Moodle-Kurs" zu einem Kanal zu beenden.

## <a name="5-allow-automatic-creation-of-moodle-tabs-in-microsoft-teams"></a>5. Automatisches Erstellen von Registerkarten für "Moodle" in Microsoft Teams zulassen

Obwohl die Registerkarten "Moodle" manuell in Microsoft Teams erstellt werden, können Sie festlegen, dass sie automatisch erstellt werden, wenn Teams aus der Kurssynchronisierung erstellt werden. Dazu müssen Sie die ID der hochgeladenen Microsoft Teams-App in Moodle konfigurieren:

1. Öffnen Sie Microsoft Teams.

1. Wählen Sie im unteren linken Bereich der Navigationsleiste das Symbol Apps aus.

1. Suchen Sie die hochgeladene **Moodle-App➡** Wählen **Sie** das Optionssymbol aus, ➡ Link **kopieren auswählen.**

1. Fügen Sie in einem Texteditor den kopierten Inhalt ein. Sie muss eine URL wie ht-&#8203;tps://teams.microsoft.com/l/app/00112233-4455-6677-8899-aabbccddeeff. Kopieren Sie den letzten Teil der URL, z. B.  `00112233-4455-6677-8899-aabbccddeeff` , der die ID der Microsoft Teams-App ist.

1. Öffnen Sie in Moodle die **Registerkarte Teams Moodle-App** auf ihrer Microsoft 365-Konfigurationsseite für das Moodle-Plug-In.

1. Fügen Sie die ID der Microsoft Teams-App in das Feld App-ID von Moodle ein, und speichern Sie Änderungen.

Wenn ein Moodle-Kurs synchronisiert wird, installiert Microsoft Teams automatisch die Moodle-App im Team, erstellt eine Registerkarte "Moodle" im Allgemeinen Kanal von Teams und konfiguriert sie so, dass sie die Kursseite für den Kurs "Moodle" enthält, von dem er synchronisiert wird. Sie können jetzt direkt von Microsoft Teams aus mit Ihren Moodle-Kursen arbeiten.

Wenn Sie Featureanforderungen oder Feedback an uns senden möchten, besuchen Sie unsere [User Voice-Seite](https://microsoftteams.uservoice.com/forums/916759-moodle).

## <a name="see-also"></a>Siehe auch

> [!div class="nextstepaction"]
> [Integrieren von Web-Apps](~/samples/integrate-web-apps-overview.md)

> [!div class="nextstepaction"]
> [Moodle](https://moodle.org/)

> [!div class="nextstepaction"]
> [Dokumentation zu "Moodle".](https://docs.moodle.org/34/en/Installing_plugins)
