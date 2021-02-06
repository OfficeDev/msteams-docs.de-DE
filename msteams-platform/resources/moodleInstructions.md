---
title: Installieren der Integration von Moodle in Microsoft Teams
description: So installieren und konfigurieren Sie die Integrations-App "Moodle" für Microsoft Teams
keywords: Integrations-Plug-In für Teams-Moodle-App
ms.topic: how-to
ms.author: lajanuar
author: laujan
ms.openlocfilehash: bb3de6b3897105ff3564ecd332cba28a0db85b0f
ms.sourcegitcommit: a16590b2ccc46e1b6d17cbb367762a3c16ff779c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/05/2021
ms.locfileid: "50115741"
---
# <a name="installing-the-moodle-integration-with-microsoft-teams"></a>Installieren der Integration von Moodle in Microsoft Teams

[Moodle,](https://moodle.org/)ein beliebtes Open-Source Learning Management System (LMS), ist jetzt in Microsoft Teams integriert. Diese Integration hilft Lehrkräften und Lehrkräften bei der Zusammenarbeit an Den -Kursen, stellt Fragen zu Noten und Aufgaben und bleibt mit Benachrichtigungen direkt in Teams auf dem Laufenden.

Um IT-Administratoren das Einrichten dieser Integration zu erleichtern, haben wir unser Open-Source-Microsoft 365-Plug-In für Das Plug-In für Das Plug-In mit den folgenden Funktionen aktualisiert:

* Automatische Registrierung Ihres Servers mit "Moodle" mit [Azure Active Directory](https://azure.microsoft.com/services/active-directory/) (Azure AD).
* Bereitstellung Des Bots für den Moodle-Assistenten in Azure mit nur einem Klick.
* Automatische Bereitstellung von Teams und automatische Synchronisierung von Teamregistrierungen für alle oder ausgewählte Kurse von "Moodle".
* Automatische Installation der Registerkarte "Moodle" und des Bots für den Assistant von "Moodle" in jedem synchronisierten Team.

Weitere Informationen zu den Funktionen, die diese Integration bietet, finden Sie *unter* [Microsoft Teams und Moodle.](https://education.microsoft.com/resource/3dffb3a8)

## <a name="prerequisites"></a>Voraussetzungen

Um diese Anwendung zu installieren und zu konfigurieren, benötigen Sie:

1. Anmeldeinformationen für den Administrator von "Moodle".

1. Azure AD-Administratoranmeldeinformationen.

1. Ein Azure-Abonnement, in dem Sie neue Ressourcen erstellen können.

## <a name="step-1-install-the-microsoft-365-moodle-plugins"></a>Schritt 1: Installieren des Microsoft 365-Plug-Ins für "Moodle"

Die Integration von Moodle in Microsoft Teams wird durch das Open Source [Microsoft 365-Plug-In-Set für Das Plug-In "365" unterstützt.](https://github.com/Microsoft/o365-moodle) Zum Installieren des Plug-Ins auf Ihrem "Moodle"-Server muss Folgendes installiert sein:

1. Eine [aktuelle stabile Version von Moodle](https://download.moodle.org/releases/latest/).

1. The Moodle [OpenID Connect](https://moodle.org/plugins/auth_oidc) and the [Microsoft 365 Integration](https://moodle.org/plugins/local_o365) plugins downloaded and saved to your local computer.

> [!NOTE]
> Die Installation der OpenID Connect- und Microsoft 365-Integrations-Plug-Ins ist für die Integration von Teams erforderlich. Darüber hinaus wird [das Microsoft 365 Teams Theme-Plug-In](https://moodle.org/plugins/theme_boost_o365teams) dringend empfohlen.

3. Melden Sie sich als Administrator bei  Ihrem Moodle-Server an, und wählen Sie im Einstellungsblock im linken Navigationsbereich die Option "Websiteverwaltung" aus. [](https://docs.moodle.org/22/en/Settings_block)

1. Wählen Sie die **Registerkarte "Plug-Ins"** und dann **"Plug-In installieren" aus.**

1. Wählen Sie **im Abschnitt "Plug-In** aus ZIP installieren" die Schaltfläche **"Datei auswählen"** aus.

1. Wählen Sie **im linken Navigationsbereich** die Optionen zum Hochladen einer Datei aus, suchen Sie nach der oben heruntergeladenen Datei, und wählen Sie **"Diese Datei hochladen" aus.**

1. Wählen Sie **die Option "Websiteverwaltung"** im linken Navigationsbereich aus, um zum Administratordashboard zurückzukehren. Scrollen Sie nach unten zu den lokalen Plug-Ins, und wählen Sie den **Microsoft 365-Integrationslink** aus.  **Lassen Sie diese Konfigurationsseite während des installationsvorgangs auf einer separaten Browserregisterkarte geöffnet.**

Weitere Informationen zur Installation von Moodle-Plug-Ins finden Sie in der [Dokumentation zu Moodle.](https://docs.moodle.org/34/en/Installing_plugins)

> [!IMPORTANT]
>
> * Lassen Sie Ihre Konfigurationsseite für Das Microsoft 365-Chrome-Plug-In auf einer separaten Browserregisterkarte geöffnet. Sie kehren während des gesamten Prozesses zu diesem Seitensatz zurück.  <br/><br/>
>* Wenn Sie nicht über eine vorhandene "Moodle"-Website verfügen, können Sie Sich bei "Moodle" im [Azure-Repository](https://github.com/azure/moodle) informieren, wo Sie schnell eine "Moodle"-Instanz bereitstellen und an Ihre Anforderungen anpassen können.

## <a name="step-2-configure-the-connection-between-the-microsoft-365-plugin-and-azure-active-directory-azure-ad"></a>Schritt 2: Konfigurieren der Verbindung zwischen dem Microsoft 365-Plug-In und Azure Active Directory (Azure AD)

Als Nächstes müssen Sie Fürlala als Anwendung in Ihrem Azure AD registrieren. Wir haben ein PowerShell-Skript bereitgestellt, das Sie bei der Ausführung dieses Vorgangs unterstützen soll. Das PowerShell-Skript stellt eine neue Azure AD-Anwendung für Ihren Microsoft 365-Mandanten bereit, die vom Microsoft 365-Plug-In Fürsprecher Fürsprecher verwendet wird. Das Skript stellt die App für Ihren Microsoft 365-Mandanten, die erforderlichen Antwort-URLs und -Berechtigungen für die bereitgestellte App ein, und gibt die und `AppID` `Key` zurück. Sie können die generierte und auf Ihrer Setupseite für `AppID` `Key` Das Microsoft 365-Plug-In-Plug-Ins verwenden, um Ihre Website für den Server mit "Moodle" mit Azure AD zu konfigurieren.

>[!IMPORTANT]
> Das PowerShell-Skript wird nicht mit den neuesten Konfigurationselementen aktualisiert, daher müssen Sie die Konfiguration manuell abschließen, indem Sie die Schritte auf den Releaseseiten von Moodle [3.8.0.4 und 3.9.1](https://docs.moodle.org/39/en/Office365#3.8.0.4_and_3.9.1_release) und [3.8.0.5 und 3.9.2](https://docs.moodle.org/39/en/Office365#3.8.0.5_and_3.9.2_release) ausführen. </br></br>
> Informationen zum Anzeigen der manuellen Schritte, die das PowerShell-Skript *automatisiert,* finden Sie unter [Registrieren Der Instanz von "Moodle" als Anwendung.](https://docs.moodle.org/34/en/Office365#Register_your_Moodle_instance_as_an_Application)

### <a name="the-moodle-tab-for-microsoft-teams-information-flow"></a>Die Registerkarte "Moodle" für den Microsoft Teams-Informationsfluss

<img width="530px" src="../assets/images/MoodleTabInformationFlow.png" alt="Moodle tab for Microsoft Teams information flow" />

1. Wählen Sie auf der Seite "Microsoft 365-Integrations-Plug-In" die **Registerkarte "Setup"** aus.

1. Wählen Sie **die Schaltfläche "PowerShell-Skript herunterladen"** aus, und speichern Sie sie auf Ihrem lokalen Computer.

1. Sie müssen das PowerShell-Skript aus der ZIP-Datei vorbereiten. Gehen Sie hierzu folgendermaßen vor:

    * Laden Sie die Datei herunter, und extrahieren `Moodle-AzureAD-Powershell.zip` Sie sie.
    * Öffnen Sie den extrahierten Ordner.
    * Klicken Sie mit der rechten Maustaste auf die `Moodle-AzureAD-Script.ps1` Datei, und wählen Sie **"Eigenschaften" aus.**
    * Aktivieren Sie **unter der** Registerkarte "Allgemein" des Eigenschaftenfensters das Kontrollkästchen neben dem Sicherheitsattribut am unteren Rand `Unblock` des Fensters. 
    * Wählen Sie **OK** aus.
    * Kopieren Sie den Verzeichnispfad in den extrahierten Ordner.

1. Als Nächstes führen Sie PowerShell als Administrator aus:

    * Wählen Sie "Start" aus.
    * Geben Sie PowerShell ein.
    * Klicken Sie mit der rechten maustaste Windows PowerShell.
    * Wählen Sie "Als Administrator ausführen" aus.

1. Navigieren Sie zum entzippten Verzeichnis, indem Sie eingeben, wo `cd .../.../Moodle-AzureAD-Powershell` sich der Pfad zum Verzeichnis `.../...` befindet.

1. Führen Sie das PowerShell-Skript aus:

    * Geben Sie `Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser` ein .
    * Geben Sie `./Moodle-AzureAD-Script.ps1` ein .
    * Melden Sie sich im Popupfenster bei Ihrem Microsoft 365-Administratorkonto an.
    * Geben Sie den Namen der Azure AD-Anwendung ein (z. B. "Moodle/Moodle"-Plug-In).
    * Geben Sie die URL für Ihren "Moodle"-Server ein.
    * Kopieren Sie die Vom Skript **generierte** **Anwendungs-ID** und den Anwendungsschlüssel, und speichern Sie sie.

1. Als Nächstes müssen Sie das und das ` AppID` `Key` Microsoft 365-Plug-In von Moodle hinzufügen. Kehren Sie zur Seite für die Verwaltung des Plug-Ins zurück (Websiteverwaltung ➡ Plugins ➡ Microsoft 365-Integration).

1. Fügen Sie **auf der Registerkarte "Setup"** die **Anwendungs-ID** und den **Anwendungsschlüssel** hinzu, die Sie zuvor kopiert haben, und wählen Sie dann **"Änderungen speichern" aus.**

1. Sobald die Seite aktualisiert wird, sollte ein neuer Abschnitt **"Verbindungsmethode auswählen" angezeigt werden.** Aktivieren Sie das Kontrollkästchen mit der Bezeichnung **"Standard",** und wählen Sie dann erneut **"Änderungen speichern"** aus.

1. Sobald die Seite aktualisiert wird, wird ein weiterer neuer Abschnitt **"Administrator-Zustimmung"**& zusätzliche Informationen angezeigt.
    * Wählen Sie **den Link "Administratorzuwilligung** bereitstellen" aus, geben  Sie Ihre Anmeldeinformationen für den globalen Microsoft 365-Administrator ein, und akzeptieren Sie die Berechtigungen.
    * Wählen Sie neben dem **Azure AD-Mandantenfeld** die Schaltfläche **"Erkennen"** aus.
    * Wählen Sie neben der **OneDrive for #A0** die Schaltfläche **"Erkennen"** aus.
    * Sobald die Felder auffüllen, wählen Sie erneut die **Schaltfläche "Änderungen** speichern" aus.

1. Wählen Sie die **Schaltfläche "Aktualisieren"** aus, um die Installation zu überprüfen, und speichern **Sie dann die Änderungen.**

1. Als Nächstes müssen Sie Die Benutzer zwischen Ihrem Server mit Moodle und Azure AD synchronisieren. Je nach Umgebung können Sie in dieser Phase unterschiedliche Optionen auswählen. Erste Schritte:
    * Wechseln zur Registerkarte **"Synchronisierungseinstellungen"**
    * Aktivieren Sie **im Abschnitt "Benutzer** mit Azure AD synchronisieren" die Kontrollkästchen, die für Ihre Umgebung gelten. In der Regel würden Sie mindestens Folgendes auswählen:  

        ✔ Erstellen von Konten in Moodle für Benutzer in Azure AD . 
        ✔ Aktualisieren Sie alle Konten in Moodle für Benutzer in Azure AD.  

    * Im Abschnitt **"Benutzererstellungseinschränkung"** können Sie einen Filter einrichten, um die Azure AD-Benutzer zu begrenzen, die mit Moodle synchronisiert werden.
    * Im **Abschnitt "Benutzerfeldzuordnung"** können Sie die Zuordnung der Azure AD-zu-Moodle-Benutzerprofil-Feldzuordnung anpassen.
    * Im Abschnitt **"Teams-Synchronisierung"** können Sie auswählen, dass automatisch Gruppen (d. h. Teams) für einige oder alle Ihrer vorhandenen Kurse für Moodle erstellt werden.

> [!NOTE]
> The Moodle [Vetn](https://docs.moodle.org/310/en/Cron) will run according to the task schedule (once a day by default). Das Gerät sollte jedoch häufiger ausgeführt werden, um alles synchron zu halten.

13. Zum Überprüfen [von Aufträgen](https://docs.moodle.org/310/en/Cron) (und/oder manuellen Ausführen  der Aufträge für die erste Ausführung) wählen Sie den Link zur Verwaltung geplanter Aufgaben im Abschnitt "Benutzer mit **Azure AD** synchronisieren" aus. Dadurch gelangen Sie zur Seite **"Geplante Vorgänge".**

    * Scrollen Sie nach unten, suchen Sie den Auftrag **"Benutzer** mit Azure AD synchronisieren", und wählen **Sie "Jetzt ausführen" aus.**
    * Wenn Sie Gruppen basierend auf vorhandenen Kursen erstellen möchten, können Sie auch den Auftrag zum Erstellen von Benutzergruppen **in Microsoft 365** ausführen.

1. Kehren Sie zur Seite "Plug-In-Verwaltung" (Websiteverwaltung ➡ Plugins ➡ Microsoft 365-Integration) zurück, und wählen Sie die Seite **"Teams-Einstellungen"** aus. Sie müssen einige Einstellungen konfigurieren, um die Integration der Teams-App zu aktivieren.

    * Um **OpenID Connect** zu  aktivieren, wählen Sie den Link "Authentifizierung verwalten" aus, und wählen Sie das Augensymbol in der **OpenId Connect-Zeile** aus, wenn es ausgegraut ist.
    * Als Nächstes müssen Sie die Frameeinbettung aktivieren. Wählen Sie **den Link "HTTP-Sicherheit"** und dann das Kontrollkästchen neben **"Frameeinbettung zulassen" aus.**
    * Der nächste Schritt besteht im Aktivieren von Webdiensten, die die Features der Moodle-API aktivieren. Wählen Sie **den Link "Erweiterte Features"** aus, und stellen Sie dann sicher, dass das Kontrollkästchen **neben** Webdienste aktivieren aktiviert ist.
    * Schließlich müssen Sie die externen Dienste für Microsoft 365 aktivieren. Wählen Sie **dann den Link "Externe** Dienste" aus:  

        ✔ In der Zeile **"Microsoft** **365-Webdienste" von", "Bearbeiten"** auswählen.  
        ✔ Markieren Sie das Kontrollkästchen neben **"Aktiviert",** und wählen Sie dann **"Änderungen speichern" aus.**

    * Als Nächstes müssen Sie Ihre authentifizierten Benutzerberechtigungen bearbeiten, damit diese Webdiensttoken erstellen können. Wählen Sie **den Link "Authentifizierter Benutzer" der Bearbeitungsrolle** aus. Scrollen Sie nach unten, suchen Sie nach der Funktion zum Erstellen eines **Webdiensttokens,** und aktivieren Sie das Kontrollkästchen **"Zulassen".**

## <a name="step-3-deploy-the-moodle-assistant-bot-to-azure"></a>Schritt 3: Bereitstellen des Moodle-Assistenten-Bots in Azure

Der kostenlose Assistant Bot für Moodle für Microsoft Teams hilft Lehrern und Schülern bei der Beantwortung von Fragen zu ihren Kursen, Aufgaben, Noten und anderen Informationen in Moodle. Der Bot sendet auch Benachrichtigungen über DieBezung an Schüler/Studenten und Lehrer in Teams. Der Bot ist ein Open-Source-Projekt, das von Microsoft verwaltet wird, und ist auf [GitHub verfügbar.](https://github.com/microsoft/Moodle-Teams-Bot)

> [!NOTE]
> In diesem Abschnitt stellen Sie Ressourcen für Ihr Azure-Abonnement bereit. Alle Ressourcen werden mithilfe der kostenlosen **Ebene** konfiguriert. Je nach Verwendung Ihres Bots müssen Sie diese Ressourcen möglicherweise skalieren.
> Wenn Sie die Registerkarte "Moodle" ohne den Bot verwenden möchten, fahren Sie mit [Schritt 4 fort.](#step-4-deploy-your-microsoft-teams-app)

### <a name="moodle-bot-information-flow"></a>Informationfluss für den 16-1-Bot

<img width="530px" src="../assets/images/MoodleBotInformationFlow.png" alt="Moodle bot for Microsoft Teams information flow" />

Um den Bot zu installieren, müssen Sie ihn zuerst auf der [Microsoft Identity Platform registrieren.](https://identity.microsoft.com/Landing) Dadurch kann sich Ihr Bot bei Ihren Microsoft-Endpunkten authentifizieren. So registrieren Sie Ihren Bot:

1. Kehren Sie zur Seite "Plug-In-Verwaltung" (Websiteverwaltung ➡ Plugins ➡ Microsoft 365-Integration) zurück, und wählen Sie die Registerkarte **"Teams-Einstellungen"** aus.

1. Wählen Sie den **Link "Microsoft-Anwendungsregistrierungsportal"** aus, und melden Sie sich mit Ihrer Microsoft-ID an.

1. Geben Sie einen Namen für Ihre App ein (z. B. "MoodleBot"), und wählen Sie die Schaltfläche **"Erstellen"** aus.

1. Kopieren Sie **die Anwendungs-ID,** und fügen Sie sie in das **Feld "Bot-Anwendungs-ID"** auf der Seite **"Teameinstellungen"** ein.

1. Wählen Sie die **Schaltfläche "Neues Kennwort generieren"** aus. Kopieren Sie das generierte Kennwort, und fügen Sie es in das Feld **"Botanwendungskennwort"** auf der Seite **"Teameinstellungen"** ein.

1. Scrollen Sie zum Ende des Formulars, und wählen **Sie "Änderungen speichern" aus.**

Nachdem Sie nun Ihre Anwendungs-ID und Ihr Kennwort generiert haben, ist es an der Zeit, Ihren Bot in Azure zu bereitstellen:

> [!div class="checklist"]
> * Wählen Sie **die Schaltfläche "In Azure** bereitstellen" aus, und füllen Sie das Formular mit den erforderlichen Informationen aus (die Bot-Anwendungs-ID, das Botanwendungskennwort und der geheime Schlüssel von "Moodle" befinden sich auf der Seite **"Teameinstellungen".** Die Informationen zu Azure finden Sie auf der **Seite "Setup").** 
> * Sobald Sie das Formular ausgefüllt haben, aktivieren Sie das Kontrollkästchen, um den Geschäftsbedingungen zu zustimmen.
> * Wählen Sie die **Schaltfläche "Kaufen"** aus (alle Azure-Ressourcen werden auf der kostenlosen Ebene bereitgestellt).

Nachdem die Ressourcen die Bereitstellung in Azure abgeschlossen haben, müssen Sie das Microsoft 365-Plug-In "Moodle" mit einem Messagingendpunkt konfigurieren. Sie müssen den Endpunkt von Ihrem Bot in Azure erhalten:

1. Melden Sie sich beim [Azure-Portal an.](https://portal.azure.com)

1. Wählen Sie im linken Bereich **Ressourcengruppen aus,** und wählen Sie die Ressourcengruppe aus, die Sie bei der Bereitstellung Ihres Bots verwendet (oder erstellt) haben.

1. Wählen Sie **die WebApp -Bot-Ressource** aus der Liste der Ressourcen in der Gruppe aus.

1. Kopieren Sie den **Nachrichtenendpunkt** aus dem **Abschnitt "Übersicht".**

1. Öffnen Sie in Moodle die **Seite "Teameinstellungen"** Ihres Microsoft 365-Plug-Ins für Das Plug-In.

1. Fügen Sie **im Feld "Bot-Endpunkt"** die URL ein, die Sie gerade kopiert haben, und ändern Sie das Wort *"Nachrichten"* in *"Webhook".* Die URL sollte jetzt wie folgt aussehen:  `https://botname.azurewebsites.net/api/webhook`

1. Wählen Sie **"Änderungen speichern" aus.**

1. Nachdem Ihre Änderungen gespeichert wurden, wechseln Sie zurück  zur Registerkarte **"Teameinstellungen",** wählen Sie die Schaltfläche "Manifestdatei herunterladen" aus, und speichern Sie das App-Manifestpaket auf Ihrem Computer (Sie verwenden es im nächsten Abschnitt).

## <a name="step-4-deploy-your-microsoft-teams-app"></a>Schritt 4: Bereitstellen Ihrer Microsoft Teams-App

Nachdem Sie Ihren Bot in Azure bereitgestellt und so konfiguriert haben, dass er mit Ihrem Moodle-Server in Verbindung steht, ist es an der Zeit, Ihre Microsoft Teams-App bereitstellen. Laden Sie dazu die App-Manifestdatei, die Sie im vorherigen Schritt von der Seite "Microsoft 365-Teameinstellungen für Das Plug-In-Team" von Microsoft 365 heruntergeladen haben.

Bevor Sie die App installieren können, müssen Sie sicherstellen, dass externe Apps und das Hochladen von Apps aktiviert sind. Dazu können Sie die Schritte in der Microsoft [365-Mandantendokumentation](../concepts/build-and-test/prepare-your-o365-tenant.md) für Microsoft Teams vorbereiten. Nachdem Sie sichergestellt haben, dass externe Apps aktiviert sind, können Sie die folgenden Schritte ausführen, um Ihre App zu bereitstellen:

1. Öffnen **Sie Microsoft Teams.** 

1. Wählen Sie **das Symbol "App"** im linken unteren Bereich der Navigationsleiste aus.

1. Wählen Sie **in der Liste** der Optionen den Link "Benutzerdefinierte App hochladen" aus.

> [!Note]
> Wenn Sie als globaler Administrator angemeldet sind, haben Sie die Möglichkeit, die App in den App-Katalog Ihrer Organisation hochzuladen, andernfalls können Sie die App nur für ein Team laden, in dem Sie Mitglied sind.

4. Wählen Sie das `manifest.zip` Paket aus, das Sie zuvor heruntergeladen haben, und wählen Sie **"Speichern" aus.** Wenn Sie das App-Manifestpaket nicht heruntergeladen haben, können Sie dies auf der Registerkarte **"Teameinstellungen"** auf der Seite "Plug-In-Konfiguration" in Moodle tun.

Nachdem Sie die App installiert haben, können Sie die Registerkarte einem beliebigen Kanal hinzufügen, auf den Sie Zugriff haben. Navigieren Sie dazu zum Kanal, wählen **Sie** das Pluszeichen (➕) aus, und wählen Sie Ihre App aus der Liste aus. Folgen Sie den Eingabeaufforderungen, um das Hinzufügen Ihrer Registerkarte für den Kurs "Moodle" zu einem Kanal zu beenden.

## <a name="step-5-allow-automatic-creation-of-moodle-tabs-in-microsoft-teams"></a>Schritt 5: Zulassen der automatischen Erstellung von Registerkarten von "Moodle" in Microsoft Teams

Obwohl die Registerkarten von "Moodle" manuell in Microsoft Teams erstellt werden können, können Sie diese automatisch erstellen lassen, wenn Teams aus der Kurssynchronisierung erstellt werden. Dazu konfigurieren Sie die ID der hochgeladenen Microsoft Teams-App in Moodle:

1. Öffnen Sie Microsoft Teams.

1. Wählen Sie das Symbol "Apps" im unteren linken Bereich der Navigationsleiste aus.

1. Suchen Sie die **hochgeladene ➡A0** aus, und wählen **Sie** das Optionssymbol ➡ Link **kopieren aus.**

1. Fügen Sie den kopierten Inhalt in einen Texteditor ein. Sie sollte eine URL wie z. B. ht&#8203;tps://teams.microsoft.com/l/app/00112233-4455-6677-8899-aabbccddeeff. Kopieren Sie den letzten Teil der URL, z. B. `00112233-4455-6677-8899-aabbccddeeff` die ID der Microsoft Teams-App.

1. Öffnen Sie in Moodle die **Registerkarte "Teams-Moodle-App"** auf ihrer Konfigurationsseite für Das Microsoft 365-Plug-In für Das Plug-In.

1. Fügen Sie die ID der Microsoft Teams-App in das Feld "Moodle-App-ID" ein, und speichern Sie die Änderungen.

Wenn nun ein Course für Moodle synchronisiert wird, installiert Microsoft Teams automatisch die "Moodle"-App im Team, erstellt eine Registerkarte "Moodle" im Kanal "Allgemein" von Teams und konfiguriert sie so, dass sie die Kursseite für den Kurs von "Moodle" enthält, aus dem sie synchronisiert wird.

### <a name="thats-it-you-and-your-team-can-now-start-working-with-your-moodle-courses-directly-from-microsoft-teams"></a>Das ist alles. Sie und Ihr Team können jetzt direkt von Microsoft Teams aus mit Ihren Kursen für Fürstliche Kurse arbeiten.

Um Featureanfragen oder Feedback mit uns zu teilen, besuchen Sie bitte unsere [Seite "Benutzerstimme".](https://microsoftteams.uservoice.com/forums/916759-moodle)
