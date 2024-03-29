---
title: Installieren von Moodle LMS
description: In diesem Artikel erfahren Sie, wie Sie die Moodle-Integrations-App für Microsoft Teams installieren und konfigurieren.
ms.topic: how-to
ms.localizationpriority: medium
ms.author: lajanuar
author: surbhigupta
ms.openlocfilehash: c2276c720ca4d7014b3317365411a9c3d7fe6a73
ms.sourcegitcommit: edfe85e312c73e34aa795922c4b7eb0647528d48
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/30/2022
ms.locfileid: "68243178"
---
# <a name="install-moodle-lms"></a>Installieren von Moodle LMS

In diesem Artikel erfahren Sie, wie Sie das Moodle LMS installieren.

> [!NOTE]
> Um IT-Administratoren bei der einfachen Einrichtung der Moodle- und Teams-Integration zu unterstützen, werden Open-Source-Microsoft 365 Moodle-Plug-Ins für Folgendes aktualisiert:
>
> * Automatische Registrierung Ihres Moodle-Servers mit [Microsoft Azure Active Directory (Azure AD)](https://azure.microsoft.com/services/active-directory/).
>
> * Bereitstellung Ihres Moodle Assistant-Bots in Azure mit einem Klick.
>
> * Automatische Bereitstellung von Teams und automatische Synchronisierung von Teamregistrierungen für alle oder ausgewählte Moodle-Kurse.
>
> * Automatische Installation der Registerkarte "Moodle" und des Moodle-Assistenten-Bots in jedem synchronisierten Team.
>
> Weitere Informationen zu den Funktionen, die diese Integration bietet, finden Sie unter [Microsoft Teams und Moodle](https://education.microsoft.com/resource/3dffb3a8).

## <a name="prerequisites"></a>Voraussetzungen

Es folgen die Voraussetzungen für die Installation von Moodle:

* Moodle-Administratoranmeldeinformationen.

* Azure AD-Administratoranmeldeinformationen.

* Ein Azure-Abonnement, in dem Sie neue Ressourcen erstellen können.

## <a name="1-install-the-microsoft-365-moodle-plugins"></a>1. Installieren der Microsoft 365 Moodle Plugins

Die Moodle-Integration in Microsoft Teams wird durch das Open Source [Microsoft 365 Moodle-Plug-Ins unterstützt](https://moodle.org/plugins/browse.php?list=set&id=72).

### <a name="requisite-applications-and-plugins"></a>Erforderliche Anwendungen und Plug-Ins

Stellen Sie sicher, dass Sie Folgendes installieren und herunterladen, bevor Sie mit der Installation der Microsoft 365 Moodle-Plug-Ins fortfahren:

1. Stellen Sie sicher, dass Sie eine [aktuelle stabile Version von Moodle](https://download.moodle.org/releases/latest/) installieren.

1. Laden Sie die Moodle [OpenID Connect](https://moodle.org/plugins/auth_oidc) und die [Microsoft 365 Integration-Plug-Ins](https://moodle.org/plugins/local_o365) herunter, und speichern Sie sie auf Ihrem lokalen Computer.

    > [!NOTE]
    > Die Installation der OpenID Connect- und Microsoft 365-Integrations-Plug-Ins ist für die Teams-Integration erforderlich.
    >
    > Darüber hinaus wird das [Microsoft 365 Teams-Design-Plug-In](https://moodle.org/plugins/theme_boost_o365teams) dringend empfohlen.

### <a name="microsoft-365-moodle-plugins"></a>Microsoft 365 Moodle Plugins

1. Laden Sie die Plug-Ins herunter, extrahieren Sie sie, und laden Sie sie in ihre entsprechenden Ordner hoch. Extrahieren Sie beispielsweise das OpenID Connect-Plug-In (auth_oidc) in einen Ordner namens **oidc**, und laden Sie es in den **Authentifizierungsordner** Ihres Moodle-Dokumentstamms hoch. 

1. Melden Sie sich als Administrator bei Ihrem Moodle-Server an, und wählen Sie **"Websiteverwaltung**" aus.

1. Nach der Erkennung neuer Plug-Ins, die installiert werden sollen, sollte Moodle Sie zur Seite "Neue Plugins installieren" umleiten. Wenn dies nicht der Fall ist, wählen Sie auf der Seite "**Websiteverwaltung**" auf der Registerkarte "**Allgemein**" die Option **"Benachrichtigungen**" aus. Dies sollte die Installation der Plug-Ins auslösen.

1. Nachdem die Plug-Ins installiert wurden, wechseln Sie auf der Seite "**Websiteadministrator**" zur Registerkarte **"Plug-Ins**", wählen Sie den Link zum Abschnitt **"Authentifizierung**" aus, und aktivieren Sie **OpenID Connect**. Es ist in Ordnung, die Plug-In-Konfiguration leer zu lassen – sie werden später ausgefüllt.

1. Scrollen Sie auf der Seite **"Websiteadministrator** " nach unten zum Abschnitt " **Lokale Plug-Ins** ", und wählen Sie den Link **"Microsoft 365-Integration** " aus.

    > [!IMPORTANT]
    >
    > * Lassen Sie Ihre Konfigurationsseite für Microsoft 365 Moodle-Plug-Ins auf einer separaten Browserregisterkarte geöffnet, da Sie während des gesamten Prozesses zu dieser Gruppe von Seiten zurückkehren müssen.  
    >
    > * Wenn Sie nicht über eine vorhandene Moodle-Website verfügen, wechseln Sie zum [Moodle on Azure-Repository](https://github.com/azure/moodle) , stellen Sie schnell eine Moodle-Instanz bereit, und passen Sie sie an Ihre Anforderungen an.

## <a name="2-configure-the-connection-between-the-microsoft-365-plugins-and-azure-ad"></a>2. Konfigurieren der Verbindung zwischen den Microsoft 365-Plug-Ins und Azure AD

Sie müssen die Verbindung zwischen den Microsoft 365-Plug-Ins und Azure AD konfigurieren.

### <a name="requisites"></a>Voraussetzungen

Registrieren Sie Moodle mithilfe des PowerShell-Skripts als Anwendung in Azure AD. Das Skript stellt Folgendes bereit:

* Eine neue Azure AD-Anwendung für Ihren Microsoft 365-Mandanten, die von den Microsoft 365 Moodle-Plug-Ins verwendet wird.
* Die App für Ihren Microsoft 365-Mandanten, richtet die erforderlichen Antwort-URLs und Berechtigungen für die bereitgestellte App ein und gibt die `AppID` `Key`und zurück.

Verwenden Sie die generierte `AppID` und `Key` in Ihrer Microsoft 365 Moodle Plugins Setup-Seite, um Ihre Moodle-Serverwebsite mit Azure AD zu konfigurieren.

> [!IMPORTANT]
>
> * Weitere Informationen zum manuellen Registrieren Ihrer Moodle-Instanz finden [Sie unter Registrieren Ihrer Moodle-Instanz als Anwendung](https://docs.moodle.org/400/en/Microsoft_365#Azure_App_Creation_and_Configuration).

### <a name="the-moodle-tab-for-microsoft-teams-information-flow"></a>Die Registerkarte "Moodle" für den Informationsfluss in Microsoft Teams

<img width="530px" src="../assets/images/MoodleTabInformationFlow.png" alt="Moodle tab for Microsoft Teams information flow" />

1. Wählen Sie auf der Seite "Microsoft 365-Integrations-Plug-Ins" die Registerkarte " **Setup** " aus.

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

1. Wechseln Sie zum entzippten Verzeichnis, indem Sie `cd .../.../Moodle-AzureAD-Powershell` eingeben, wo `.../...` sich der Pfad zum Verzeichnis befindet.

1. Führen Sie das PowerShell-Skript aus:

    1. `Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser` eingeben.
    1. `./Moodle-AzureAD-Script.ps1` eingeben.
    1. Melden Sie sich im Popupfenster bei Ihrem Microsoft 365-Administratorkonto an.
    1. Geben Sie den Namen der Azure AD-Anwendung ein, z. B. Moodle- oder Moodle-Plug-Ins.
    1. Geben Sie die URL für Ihren Moodle-Server ein.
    1. Kopieren Sie die vom Skript generierte **Anwendungs-ID (`AppID`)** und den **Anwendungsschlüssel(`Key`),** und speichern Sie sie.

1. Als Nächstes müssen Sie die `AppID` Und `Key` zu den Microsoft 365 Moodle Plugins hinzufügen. Kehren Sie zur Verwaltungsseite für Plug-Ins, Websiteverwaltung > Plugins > Microsoft 365-Integration zurück.

1. Fügen Sie auf der Registerkarte **"Setup** " die `AppID` `Key` zuvor kopierte Datei hinzu, und wählen Sie dann " **Änderungen speichern"** aus. Nachdem die Seite aktualisiert wurde, wird ein neuer Abschnitt **"Verbindungsmethode auswählen" angezeigt**.

1. **Aktivieren Sie in der Choose-Verbindungsmethode** das Kontrollkästchen **"Standard**", und wählen Sie dann erneut **"Änderungen speichern"** aus.

1. Nachdem die Seite aktualisiert wurde, können Sie einen weiteren neuen Abschnitt **Admin Zustimmung & zusätzlichen Informationen** sehen.
    1. Wählen Sie **"Admin Zustimmungslink bereitstellen**" aus, geben Sie Ihre Anmeldeinformationen für den globalen Microsoft 365-Administrator ein, und **stimmen Sie** dann zu, um die Berechtigungen zu erteilen.
    1. Wählen Sie neben dem **Azure AD-Mandantenfeld** die Schaltfläche " **Erkennen** " aus.
    1. Wählen Sie neben der **OneDrive for Business-URL** die Schaltfläche "**Erkennen**" aus.
    1. Nachdem die Felder ausgefüllt wurden, wählen Sie die Schaltfläche **"Änderungen speichern** " erneut aus.

1. Wählen Sie die Schaltfläche " **Aktualisieren** " aus, um die Installation zu überprüfen, und wählen Sie dann " **Änderungen speichern"** aus.

1. Synchronisieren Sie Benutzer zwischen Ihrem Moodle-Server und Azure AD. Erste Schritte:

    > [!NOTE]
    > Je nach Umgebung können Sie während dieser Phase verschiedene Optionen auswählen.

    1. Wechseln Sie zur **Registerkarte "Synchronisierungseinstellungen"**.

    1. Aktivieren Sie im Abschnitt **"Benutzer mit Azure AD synchronisieren** " die Kontrollkästchen, die für Ihre Umgebung gelten. Sie müssen Folgendes auswählen:  

        ✔ Erstellen Sie Konten in Moodle für Benutzer in Azure AD.

        ✔ Aktualisieren Sie alle Konten in Moodle für Benutzer in Azure AD.

    1. Im Abschnitt **"Einschränkung der Benutzererstellung** " können Sie einen Filter einrichten, um die Azure AD-Benutzer einzuschränken, die mit Moodle synchronisiert werden.

1. Um [Cron-Aufträge](https://docs.moodle.org/400/en/Cron) zu überprüfen und für die erste Ausführung manuell auszuführen, wählen Sie den Link zur **Verwaltungsseite für geplante Aufgaben** im Abschnitt **"Benutzer mit Azure AD synchronisieren** " aus. Dadurch gelangen Sie zur Seite **"Geplante Vorgänge** ".

    1. Scrollen Sie nach unten, suchen Sie die **Synchronisierungsbenutzer mit dem Azure AD-Auftrag** , und wählen Sie **"Jetzt ausführen"** aus.
    1. Wenn Sie Gruppen basierend auf vorhandenen Kursen erstellen möchten, können Sie auch die Aufgabe **"Benutzergruppen erstellen" in Microsoft 365** ausführen.

    > [!NOTE]
    >
    > Der Moodle [Cron](https://docs.moodle.org/310/en/Cron) wird gemäß dem Aufgabenplan ausgeführt. Der Standardzeitplan ist einmal täglich. Der Cron muss jedoch häufiger ausgeführt werden, um alles synchron zu halten.

1. Kehren Sie zur Verwaltungsseite für Plug-Ins, **websiteverwaltung > Plugins > Microsoft 365-Integration** zurück, und wählen Sie die Seite **"Teams-Einstellungen"** aus.

1. Konfigurieren Sie auf der Seite " **Teams-Einstellungen"** die erforderlichen Einstellungen, um die Integration der Teams-App zu aktivieren, indem Sie auf den Link " **Moodle-Einstellungen überprüfen** " klicken, werden alle erforderlichen Konfigurationen aktualisiert, damit die Teams-Integration funktioniert. 

## <a name="3-deploy-the-moodle-assistant-bot-to-azure"></a>3. Bereitstellen des Moodle Assistant Bot in Azure

Der kostenlose Moodle-Assistenten-Bot für Microsoft Teams hilft Lehrern und Schülern bei der Beantwortung von Fragen zu ihren Kursen, Aufgaben, Noten und anderen Informationen in Moodle. Der Bot sendet außerdem Moodle-Benachrichtigungen an Kursteilnehmer und Lehrer in Teams. Der Bot ist ein Open-Source-Projekt, das von Microsoft verwaltet wird und auf [GitHub](https://github.com/microsoft/Moodle-Teams-Bot) verfügbar ist.

> [!NOTE]
>
> * Stellen Sie Ressourcen in Ihrem Azure-Abonnement bereit. Alle Ressourcen wurden mithilfe der **kostenlosen** Ebene konfiguriert. Je nach Verwendung Ihres Bots müssen Sie diese Ressourcen möglicherweise skalieren.
>
> * Um die Registerkarte Moodle ohne den Bot zu verwenden, fahren Sie mit [4](#4-deploy-your-microsoft-teams-app) fort.

### <a name="moodle-bot-information-flow"></a>Moodle-Bot-Informationsfluss

<img width="530px" src="../assets/images/MoodleBotInformationFlow.png" alt="Moodle bot for Microsoft Teams information flow" />

Um den Bot zu installieren, müssen Sie ihn auf der [Microsoft Identity Platform](https://identity.microsoft.com/Landing) registrieren. Auf diese Weise kann sich Ihr Bot bei Ihren Microsoft-Endpunkten authentifizieren.

So registrieren Sie Ihren Bot:

1. Wechseln Sie zur Verwaltungsseite für Plug-Ins, und wählen Sie dann **Plugins** aus. Wählen Sie unter **"Microsoft 365-Integration**" die Registerkarte " **Teams-Einstellungen"** aus.

1. Wählen Sie den Link zum **Microsoft-Anwendungsregistrierungsportal** aus, und melden Sie sich mit Ihrer Microsoft-ID an.

1. Geben Sie einen Namen für Ihre App ein, z. B. MoodleBot, und wählen Sie die Schaltfläche " **Erstellen** " aus.

1. Kopieren Sie die **Anwendungs-ID** , und fügen Sie sie in das Feld **"Bot-Anwendungs-ID** " auf der Seite **"Teameinstellungen"** ein.

1. Wählen Sie die Schaltfläche " **Neues Kennwort generieren** " aus. Kopieren Sie das generierte Kennwort, und fügen Sie es in das Feld " **Bot-Anwendungskennwort** " auf der Seite **"Teameinstellungen"** ein.

1. Scrollen Sie zum Ende des Formulars, und wählen Sie **"Änderungen speichern"** aus.

Nachdem Sie Ihre Anwendungs-ID und Ihr Kennwort generiert haben, stellen Sie Ihren Bot in Azure bereit:

> [!div class="checklist"]
>
> * Wählen Sie **"In Azure bereitstellen** " aus, und füllen Sie das Formular mit den erforderlichen Informationen aus, z. B. botanwendungs-ID, Bot-Anwendungskennwort und Moodle Secret auf der Seite **"Teams-Einstellungen"** . Die Azure-Informationen befinden sich auf der **Setupseite** .
> * Aktivieren Sie nach Dem Ausfüllen des Formulars das Kontrollkästchen, um den Allgemeinen Geschäftsbedingungen zuzustimmen.
> * Wählen Sie **"Kaufen**" aus. Alle Azure-Ressourcen werden auf der kostenlosen Ebene bereitgestellt.

Nachdem die Ressourcen die Bereitstellung in Azure abgeschlossen haben, müssen Sie die Microsoft 365 Moodle-Plug-Ins mit einem Messaging-Endpunkt konfigurieren. Sie müssen den Endpunkt von Ihrem Bot in Azure abrufen:

1. Melden Sie sich im [Microsoft Azure-Portal](https://portal.azure.com) an.

1. Wählen Sie im linken Bereich **"Ressourcengruppen** " aus, und wählen Sie die Ressourcengruppe aus, die Sie während der Bereitstellung Ihres Bots verwendet oder erstellt haben.

1. Wählen Sie die **WebApp Bot-Ressource** aus der Liste der Ressourcen in der Gruppe aus.

1. Kopieren Sie den **Messaging-Endpunkt** aus dem Abschnitt **"Übersicht** ".

1. Öffnen Sie in Moodle die Seite **"Teameinstellungen"** Ihrer Microsoft 365 Moodle-Plug-Ins.

1. Fügen Sie im Feld **Bot-Endpunkt** die kopierte URL ein, und ändern Sie die *Wortnachrichten* in *Webhook*. Die URL muss wie folgt angezeigt werden: `https://botname.azurewebsites.net/api/webhook`

1. Klicken Sie auf **Änderungen speichern**.

1. Nachdem Sie die Änderungen gespeichert haben, wechseln Sie zurück zur Registerkarte " **Teameinstellungen** ", wählen Sie die Schaltfläche " **Manifestdatei herunterladen** " aus, und speichern Sie das App-Manifestpaket zur weiteren Verwendung auf Ihrem Computer.

## <a name="4-deploy-your-microsoft-teams-app"></a>4. Bereitstellen Ihrer Microsoft Teams-App

Nachdem Ihr Bot in Azure bereitgestellt und für die Kommunikation mit Ihrem Moodle-Server konfiguriert wurde, müssen Sie Ihre Microsoft Teams-App bereitstellen. Dazu müssen Sie die App-Manifestdatei laden, die Sie im vorherigen Schritt von der Microsoft 365 Moodle Plugins Team Settings-Seite heruntergeladen haben.

Bevor Sie die App installieren, müssen Sie sicherstellen, dass externe Apps aktiviert und Apps hochgeladen werden. Weitere Informationen finden [Sie unter "Vorbereiten Ihres Microsoft 365-Mandanten](../concepts/build-and-test/prepare-your-o365-tenant.md)".

So stellen Sie Ihre App bereit:

1. Öffnen Sie **Microsoft Teams**.

1. Wählen Sie das **Symbol "Apps** " im unteren linken Bereich der Navigationsleiste aus.

1. Wählen Sie im Navigationsmenü den Link " **Apps verwalten** " aus.

1. Klicken Sie auf **"App veröffentlichen** ", und wählen Sie " **App in den App-Katalog Ihrer Organisation hochladen" aus**.

   > [!NOTE]
   > Wenn Sie als globaler Administrator angemeldet sind, müssen Sie die Möglichkeit haben, die App in den App-Katalog Ihrer Organisation hochzuladen. Andernfalls können Sie die App nur für ein Team laden, in dem Sie Mitglied sind.

4. Wählen Sie das Paket aus, das `manifest.zip` Sie zuvor heruntergeladen haben, und wählen Sie **"Speichern"** aus. Wenn Sie das App-Manifestpaket nicht heruntergeladen haben, können Sie es von der Registerkarte " **Teameinstellungen** " der Plug-In-Konfigurationsseite in Moodle herunterladen.

Nachdem Sie die App installiert haben, können Sie die Registerkarte jedem Kanal hinzufügen, auf den Sie Zugriff haben. Wechseln Sie dazu zum Kanal, wählen Sie das **Pluszeichen** (➕) aus, und wählen Sie Ihre App aus der Liste aus. Folgen Sie den Anweisungen, um das Hinzufügen Ihrer Moodle-Kursregisterkarte zu einem Kanal abzuschließen.

## <a name="5-allow-automatic-creation-of-moodle-tabs-in-microsoft-teams"></a>5. Zulassen der automatischen Erstellung von Moodle-Registerkarten in Microsoft Teams

Obwohl die Moodle-Registerkarten manuell in Microsoft Teams erstellt werden, können Sie entscheiden, sie automatisch zu erstellen, wenn Teams anhand der Kurssynchronisierung erstellt werden. Dazu müssen Sie die ID der hochgeladenen Microsoft Teams-App in Moodle konfigurieren.

So ermöglichen Sie die automatische Erstellung von Moodle-Registerkarten:

1. Öffnen Sie in Moodle die Registerkarte " **Teams Moodle-App** " auf ihrer Konfigurationsseite für Microsoft 365 Moodle-Plug-Ins.

1. Wenn die Azure-App über die empfohlene Berechtigung für die **Einstellung "Moodle-App-ID** " verfügt, sollte ein **automatisch erkannter Wert angezeigt werden**. Kopieren Sie diesen Wert in die Einstellung.

1. Wenn der automatisch erkannte Wert nicht vorhanden ist, folgen Sie der Anweisung auf der Seite, um die Moodle-App-ID zu finden und die Einstellung auszufüllen.

Wenn ein Moodle-Kurs synchronisiert wird, installiert Teams automatisch die Moodle-App im Team, erstellt eine Moodle-Registerkarte im Kanal "Allgemein" von Teams und konfiguriert sie so, dass sie die Kursseite für den Moodle-Kurs enthält, aus dem er synchronisiert wird. Sie können jetzt direkt in Teams mit Ihren Moodle-Kursen arbeiten.

> [!NOTE]
> Besuchen Sie unsere [User Voice-Seite](https://support.microsoft.com/en-us/office/uservoice-pages-430e1a78-e016-472a-a10f-dc2a3df3450a), um Featureanfragen oder Feedback mit uns zu teilen.

## <a name="see-also"></a>Siehe auch

* [Integrieren von Web-Apps](~/samples/integrate-web-apps-overview.md)
* [Moodle](https://moodle.org/)
* [Moodle-Dokumentation](https://docs.moodle.org/400/en/Installing_plugins)
* [Microsoft 365- und Moodle-Integrationsseite auf Moodle Docs](https://docs.moodle.org/400/en/Microsoft_365)
