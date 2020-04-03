---
title: Installieren der Moodle-Integration in Microsoft Teams
description: Installieren und Konfigurieren der Moodle-Integrations-App für Microsoft Teams
keywords: Teams-Plugin für die Moodle-App-Integration
ms.date: 01/31/2019
ms.openlocfilehash: 2b48cfb0bbef9a531e69ae5620c11a8258acdc64
ms.sourcegitcommit: 058b7bbd817af5f513e0e018f2ef562dc3086a84
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/03/2020
ms.locfileid: "43120297"
---
# <a name="installing-the-moodle-integration-with-microsoft-teams"></a>Installieren der Moodle-Integration in Microsoft Teams

> [!VIDEO https://www.youtube.com/embed/OHlPt22nKoE]

[Moodle](https://moodle.org/), das beliebteste und Open-Source Learning Management System (LMS) weltweit, ist jetzt in Microsoft Teams integriert! Diese Integration hilft Pädagogen und Lehrern bei der Zusammenarbeit in Moodle-Kursen, stellen Sie Fragen zu Ihren Noten und Aufgaben und bleiben Sie mit Benachrichtigungen aktualisiert – direkt in Microsoft Teams!

Damit IT-Administratoren diese Integration einfach einrichten können, haben wir unser Open-Source-Office 365-Moodle-Plugin mit den folgenden Funktionen aktualisiert:

* Automatische Registrierung Ihres Moodle-Servers mit Azure AD.
* Bereitstellung mit einem Mausklick für Ihren Moodle Assistant-bot in Azure.
* Automatische Bereitstellung von Teams und automatische Synchronisierung von Team Einschreibungen für alle oder ausgewählte Moodle-Kurse.
* Automatische Installation der Registerkarte "Moodle" und des Moodle Assistant-bot in jedem synchronisierten Team. (Bald verfügbar)
* 1-Klick-Veröffentlichung der Moodle-app in Ihrem privaten Teams-App-Store. (Bald verfügbar)

Weitere Informationen zu den Funktionen, die diese Integration bietet, finden Sie [hier](https://education.microsoft.com/resource/3dffb3a8).

## <a name="prerequisites"></a>Voraussetzungen

Um diese Anwendung zu installieren und zu konfigurieren, benötigen Sie Folgendes:

1. Administratoranmeldeinformationen für Moodle
2. Anmeldeinformationen für Azure AD Administrator
3. Ein Azure-Abonnement, in dem Sie neue Ressourcen in erstellen können

## <a name="step-1-install-the-office-365-moodle-plugin"></a>Schritt 1: Installieren des Office 365 Moodle-Plugins

> [!VIDEO https://www.youtube.com/embed/SETEC5nzMgk]

Die Moodle-Integration in Microsoft Teams wird über das Open Source [Office 365 Moodle-Plugin-Paket](https://github.com/Microsoft/o365-moodle)gesteuert. So installieren Sie das Plugin auf Ihrem Moodle-Server:

1. Laden Sie zuerst das [Office 365-Plug](https://moodle.org/plugins/pluginversions.php?plugin=local_o365) -in-Paket herunter, und speichern Sie es auf Ihrem lokalen Computer. Sie müssen die Version 3,5 oder höher verwenden.
    * Wenn Sie das local_o365-Plugin installieren, werden auch die [auth_oidc](https://moodle.org/plugins/auth_oidc) -und [boost_o365Teams](https://moodle.org/plugins/pluginversions.php?plugin=theme_boost_o365teams) -Plugins installiert.
1. Melden Sie sich als Administrator bei Ihrem Moodle-Server an, und wählen Sie im linken Navigationsbereich die Option **Websiteverwaltung** aus.
1. Wählen Sie die Registerkarte **Plugins** aus, und klicken Sie dann auf **Plugins installieren**.
1. Klicken Sie im Abschnitt **Plugin von ZIP-Datei installieren** auf die Schaltfläche **Datei auswählen** .
1. Wählen Sie die Option **Datei hochladen** im linken Navigationsbereich aus, suchen Sie nach der Datei, die Sie oben heruntergeladen haben, und klicken Sie dann auf **Diese Datei hochladen**.
1. Wählen Sie erneut im linken Navigationsbereich die Option **Websiteverwaltung** aus, um zu Ihrem Administrator Dashboard zurückzukehren. Scrollen Sie nach unten zu den **lokalen Plugins** , und klicken Sie auf den Link **Microsoft Office 365 Integration** . Lassen Sie diese Konfigurationsseite in einer separaten Browserregister Karte geöffnet, wie Sie Sie während des restlichen Prozesses verwenden werden.

Weitere Informationen zum Installieren von Moodle-Plugins finden Sie in der [Moodle-Dokumentation](https://docs.moodle.org/34/en/Installing_plugins).

**Wichtiger Hinweis:** Halten Sie Ihre Office 365 Moodle-Plugin-Konfigurationsseite in einer separaten Browserregister Karte geöffnet, da Sie während dieses Prozesses zu dieser Gruppe von Seiten zurückkehren werden.

*Sie haben noch keine Moodle-Website?* Vielleicht möchten Sie sich unsere Moodle auf Azure [Repo](https://github.com/azure/moodle) ansehen, wo Sie schnell eine Moodle-Instanz in Azure bereitstellen und an Ihre Bedürfnisse anpassen können.

## <a name="step-2-configure-the-connection-between-the-office-365-plugin-and-azure-active-directory"></a>Schritt 2: Konfigurieren der Verbindung zwischen dem Office 365-Plug-in und Azure-Active Directory

> [!VIDEO https://www.youtube.com/embed/FpGEezaJ3SA]

Als nächstes müssen Sie Moodle als Anwendung in ihrer Azure-Active Directory registrieren. Wir haben ein PowerShell-Skript bereitgestellt, das Sie bei der Ausführung dieses Prozesses unterstützt. Das PowerShell-Skript stellt eine neue Azure AD Anwendung für Ihren Office 365-Mandanten bereit, der vom Office 365 Moodle-Plugin verwendet wird. Das Skript stellt die APP für Ihren O365-Mandanten zur Verfügung, richtet alle erforderlichen Antwort-URLs und Berechtigungen für die Bereitstellungs-App ein und gibt die Anwendungs-ID und den Schlüssel zurück. Sie können die generierte Anwendungs-ID und den Schlüssel auf Ihrer O365-Setup Seite für Moodle-Plug-Ins verwenden, um Ihren Moodle-Server mit Azure AD zu konfigurieren. Wenn Sie die detaillierten manuellen Schritte anzeigen möchten, die das PowerShell-Skript automatisiert, finden Sie diese in der vollständigen [Dokumentation für das Plugin](https://docs.moodle.org/34/en/Office365#Register_your_Moodle_instance_as_an_Application).

### <a name="moodle-tab-for-microsoft-teams-information-flow"></a>Registerkarte "Moodle" für Microsoft Teams-Informationsfluss

<img width="530px" src="~/assets/images/MoodleTabInformationFlow.png" title="Registerkarte "Moodle" für Microsoft Teams-Informationsfluss" />

1. Klicken Sie auf der Seite Microsoft Office 365 Integration Plugin auf die Registerkarte **Setup** .
1. Klicken Sie auf die Schaltfläche **PowerShell-Skript herunterladen** und speichern Sie Sie auf Ihrem lokalen Computer.
1. Sie müssen das PowerShell-Skript aus der ZIP-Datei vorbereiten. Gehen Sie hierzu folgendermaßen vor:
    * Laden Sie die `Moodle-AzureAD-Powershell.zip` Datei herunter, und extrahieren Sie Sie.
    * Öffnen Sie den extrahierten Ordner.
    * Klicken Sie mit der rechten `Moodle-AzureAD-Script.ps1` Maustaste auf die Datei, und wählen Sie **Eigenschaften**aus.
    * Aktivieren Sie im Fenster Eigenschaften auf der Registerkarte **Allgemein** das `Unblock` Kontrollkästchen neben dem Attribut **Sicherheit** unten.
    * Klicken Sie auf **OK**.
    * Kopieren Sie den Verzeichnispfad des extrahierten Ordners.
1. Als nächstes führen Sie PowerShell als Administrator aus:
    * Klicken Sie auf Start.
    * Geben Sie PowerShell ein.
    * Klicken Sie mit der rechten Maustaste auf Windows PowerShell.
    * Klicken Sie auf "als Administrator ausführen".
1. Navigieren Sie zum entpackten Verzeichnis, `cd ...\...\Moodle-AzureAD-Powershell` indem `...\...` Sie WHERE als Pfad zum Verzeichnis eingeben.
1. Ausführen des PowerShell-Skripts nach:
    * Geben `Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser`Sie ein.
    * Geben `.\Moodle-AzureAD-Script.ps1`Sie ein.
    * Melden Sie sich im Popupfenster bei Ihrem O365-Administrator Konto an.
    * Geben Sie den Namen der Azure AD Anwendung ein (ex. Moodle/Moodle-Plugin).
    * Geben Sie die URL Ihres Moodle-Servers ein.
    * Kopieren Sie die vom Skript generierte **Anwendungs-ID** und den **Anwendungsschlüssel** , und speichern Sie Sie.
1. Als nächstes müssen Sie die ID und den Schlüssel zum Office 365 Moodle-Plugin hinzufügen. Kehren Sie zur Seite "Plugin-Verwaltung" (Websiteverwaltung > Plugins > Microsoft Office 365-Integration) zurück.
1. Fügen Sie auf der Registerkarte **Setup** die zuvor kopierte **Anwendungs-ID** und den **Anwendungsschlüssel** hinzu, und klicken Sie dann auf **Änderungen speichern**.
1. Nachdem die Seite aktualisiert wurde, sollte nun ein neuer Abschnitt **Verbindungsmethode auswählen**angezeigt werden. Klicken Sie auf das Kontrollkästchen **Standard** , und klicken Sie dann auf **Änderungen speichern** .
1. Nachdem die Seite aktualisiert wurde, wird ein weiterer neuer Abschnitt " **Administrator Zustimmung" & zusätzliche Informationen**angezeigt.
    * Klicken Sie auf den Link **Administrator Zustimmung bereitstellen** , geben Sie Ihre Office3 365 globalen Administrator Anmeldeinformationen ein, und **akzeptieren** Sie dann die Berechtigung, um die Berechtigungen zu erteilen.
    * Klicken Sie neben dem Feld **Azure AD Mandanten** auf die Schaltfläche **erkennen** .
    * Klicken Sie neben der **OneDrive für Unternehmen-URL** auf die Schaltfläche **erkennen** .
    * Nachdem die Felder aufgefüllt wurden, klicken Sie erneut auf die Schaltfläche **Änderungen speichern** .
1. Klicken Sie auf die Schaltfläche **Aktualisieren** , um die Installation zu überprüfen, und speichern Sie dann die **Änderungen**.
1. Als nächstes müssen Sie die Benutzer zwischen Ihrem Moodle-Server und Azure Active Directory synchronisieren. Je nach Umgebung können Sie während dieser Phase unterschiedliche Optionen auswählen. Beachten Sie, dass die hier festgelegte Konfiguration mit jedem Moodle-cron-Run (in der Regel einmal pro Tag) ausgeführt wird, um alles synchron zu halten. Erste Schritte:
    * Wechseln zur **Registerkarte Synchronisierungseinstellungen**
    * Wählen Sie im Abschnitt **Benutzer mit Azure AD synchronisieren** die Kontrollkästchen aus, die für Ihre Umgebung gelten. Normalerweise würden Sie mindestens Folgendes auswählen:
        * Erstellen von Konten in Moodle für Benutzer in Azure AD
        * Aktualisieren aller Konten in Moodle für Benutzer in Azure AD
    * Im Abschnitt zur **Einschränkung der Benutzererstellung** können Sie einen Filter einrichten, um die Azure AD Benutzer zu begrenzen, die mit Moodle synchronisiert werden.
    * Im Abschnitt **Benutzerfeld Zuordnung** können Sie die Azure AD auf die Zuordnung von Moodle-Benutzerprofil Feldern anpassen.
    * Im Abschnitt **Teams-Synchronisierung** können Sie festlegen, dass Gruppen (also Teams) für einige oder alle Ihrer vorhandenen Moodle-Kurse automatisch erstellt werden.
1. Um die cron-Aufträge zu validieren (und Sie manuell auszuführen, wenn Sie für die erste Ausführung möchten), klicken Sie auf den Link **geplante Aufgaben-Verwaltungsseite** im Abschnitt **Benutzer mit Azure AD synchronisieren** . Dadurch gelangen Sie zur Seite **geplante Vorgänge** .
    * Scrollen Sie nach unten, und suchen Sie den Auftrag **Sync users with Azure AD** Job, und klicken Sie auf **jetzt ausführen**.
    * Wenn Sie Gruppen basierend auf vorhandenen Kursen erstellen möchten, können Sie auch die **Benutzergruppen erstellen in Office 365** Auftrag ausführen.
1. Kehren Sie zur Seite "Plugin-Verwaltung" (Websiteverwaltung > Plugins > Microsoft Office 365-Integration) zurück, und wählen Sie die Seite " **Teams-Einstellungen** " aus. Sie müssen einige Sicherheitseinstellungen konfigurieren, um die Integration der Teams-APP zu ermöglichen.
    * Um OpenID Connect zu aktivieren, klicken Sie auf den Link **Authentifizierung verwalten** , und klicken Sie auf das Augensymbol in der **OpenID Connect** -Leitung, wenn es abgeblendet ist.
    * Als nächstes müssen Sie die Frame Einbettung aktivieren. Klicken Sie auf den Link **http-Sicherheit** , und klicken Sie dann auf das Kontrollkästchen neben **Frame Einbettung zulassen**.
    * Der nächste Schritt ist die Aktivierung von Webdiensten, die die Moodle-API-Funktionen aktivieren. Klicken Sie auf den Link **Erweiterte Funktionen** , und stellen Sie sicher, dass das Kontrollkästchen neben **Webdienste aktivieren** aktiviert ist.
    * Schließlich müssen Sie die externen Dienste für Office 365 aktiviert haben. Klicken Sie dann auf den Link **externe Dienste** :
        * Klicken Sie in der Zeile **Moodle Office 365 Webservices** auf **Bearbeiten** .
        * Markieren Sie das Kontrollkästchen neben **aktiviert**, und klicken Sie dann auf **Änderungen speichern** .
    * Als nächstes müssen Sie die Berechtigungen für authentifizierte Benutzer bearbeiten, damit diese Webdienst Tokens erstellen können. Klicken Sie auf den Link **"authentifizierter Benutzer" der Bearbeitungs Rolle** . Scrollen Sie nach unten, und suchen Sie die **tokenfunktion Create a-Webdienst** , und markieren Sie das Kontrollkästchen **zulassen** .

## <a name="step-3-deploy-the-moodle-assistant-bot-to-azure"></a>Schritt 3: Bereitstellen des Moodle Assistant-bot in Azure

> [!VIDEO https://www.youtube.com/embed/gbkJxf8FlfY]

Der ﻿kostenlose Moodle Assistant bot für Microsoft Teams unterstützt Lehrer und Schüler bei der Beantwortung von Fragen zu ihren Kursen, Aufgaben, Noten und anderen Informationen in Moodle. Der bot sendet auch Moodle-Benachrichtigungen an Schüler und Lehrer direkt in Microsoft Teams. Dieser Bot ist ein Open-Source-Projekt, das von Microsoft verwaltet wird, und ist [auf GitHub verfügbar](https://github.com/microsoft/Moodle-Teams-Bot).

> [!NOTE]
> In diesem Abschnitt werden Sie Ressourcen für Ihr Azure-Abonnement bereitstellen, und alle Ressourcen werden mit der **freien** Ebene konfiguriert. Je nach Verwendung Ihres bot müssen Sie möglicherweise diese Ressourcen skalieren.
> Wenn Sie nur die Registerkarte "Moodle" ohne den bot verwenden möchten, fahren Sie mit [Schritt 4 fort](#step-4-deploy-your-microsoft-teams-app).

### <a name="moodle-bot-information-flow"></a>Informationsfluss zu Moodle-bot

<img width="530px" src="~/assets/images/MoodleBotInformationFlow.png" title="Informationsfluss zu Moodle bot for Microsoft Teams" />

Um den bot zu installieren, müssen Sie ihn zunächst auf der [Microsoft Identity-Plattform](https://identity.microsoft.com/Landing)registrieren. Dies ermöglicht es Ihrem bot, sich gegenüber ihren Microsoft-Endpunkten zu authentifizieren. So registrieren Sie Ihren bot:

1. Kehren Sie zur Seite "Plugin-Verwaltung" (Websiteverwaltung > Plugins > Microsoft Office 365-Integration) zurück, und wählen Sie die Registerkarte " **Teams-Einstellungen** " aus.
1. Klicken Sie auf den Link **Microsoft-Anwendungs Registrierungs Portal** , und melden Sie sich mit Ihrer Microsoft-ID an.
1. Geben Sie einen Namen für Ihre APP ein (zB. MoodleBot), und klicken Sie auf die Schaltfläche **Erstellen** .
1. Kopieren Sie die **Anwendungs-ID** , und fügen Sie Sie in das Feld **bot-Anwendungs-ID** auf der Seite **Team Einstellungen** ein.
1. Klicken Sie auf die Schaltfläche **Neues Kennwort generieren** . Kopieren Sie das generierte Kennwort, und fügen Sie es auf der Seite **Team Einstellungen** in das Feld **bot-Anwendungs Kennwort ein** .
1. Scrollen Sie zum unteren Rand des Formulars, und klicken Sie auf **Änderungen speichern**.

Nachdem Sie nun Ihre Anwendungs-ID und Ihr Kennwort generiert haben, ist es an der Zeit, ihren bot in Azure bereitzustellen. Klicken Sie auf die Schaltfläche **in Azure bereitstellen** , und füllen Sie das Formular mit den erforderlichen Informationen aus (die bot-Anwendungs-ID, das Kennwort für die bot-Anwendung und das Moodle-Geheimnis befinden sich auf der Seite **Team Einstellungen** , und die Azure-Informationen befinden sich auf der Seite **Setup** ). Wenn Sie das Formular ausgefüllt haben, klicken Sie auf das Kontrollkästchen, um den Bedingungen zuzustimmen, und klicken Sie dann auf die Schaltfläche **Einkauf** (alle Azure-Ressourcen werden in der freien Ebene bereitgestellt).

Sobald die Bereitstellung von Ressourcen in Azure abgeschlossen ist, müssen Sie das Office 365 Moodle-Plugin mit dem Messaging-Endpunkt konfigurieren. Zunächst müssen Sie den Endpunkt von Ihrem bot in Azure abrufen. Gehen Sie dazu wie folgt vor:

1. Wenn Sie noch nicht angemeldet sind, melden Sie sich im [Azure-Portal](https://portal.azure.com)an.
2. Wählen Sie im linken Bereich **Ressourcengruppen**aus.
3. Wählen Sie in der Liste die Ressourcengruppe aus, die Sie bei der Bereitstellung Ihres bot gerade verwendet (oder erstellt) haben.
4. Wählen Sie die **WebBot** -Ressource aus der Liste der Ressourcen in der Gruppe aus.
5. Kopieren Sie den **Messaging-Endpunkt** aus dem Abschnitt **Overview** .
6. Öffnen Sie in Moodle die Seite **Team Einstellungen** in Ihrem Office 365 Moodle-Plugin.
7. Fügen Sie im Feld **bot-Endpunkt** die URL ein, die Sie soeben kopiert haben, und ändern Sie die Word- *Nachrichten* in *webhook*. Die URL sollte jetzt wie folgt aussehen.`https://botname.azurewebsites.net/api/webhook`
8. Klicken Sie auf **Änderungen speichern** .
9. Wechseln Sie nach dem Speichern der Änderungen zur Registerkarte **Team Einstellungen** , klicken Sie auf die Schaltfläche **Manifestdatei herunterladen** , und speichern Sie das Manifest-Paket auf Ihrem Computer (im nächsten Abschnitt verwenden Sie es).

## <a name="step-4-deploy-your-microsoft-teams-app"></a>Schritt 4: Bereitstellen Ihrer Microsoft Teams-App

> [!VIDEO https://www.youtube.com/embed/2rMb7gtM_ZM]

Nachdem Sie nun ihren bot in Azure bereitgestellt und für die Kommunikation mit Ihrem Moodle-Server konfiguriert haben, ist es an der Zeit, Ihre Microsoft Teams-App bereitzustellen. Dazu laden Sie die Manifestdatei, die Sie auf der Seite Office 365 Moodle Plugin-Team Einstellungen heruntergeladen haben, im vorherigen Schritt.

Bevor Sie die APP installieren können, müssen Sie sicherstellen, dass externe apps und das Hochladen von apps aktiviert ist. Dazu können Sie [die folgenden Schritte](https://docs.microsoft.com/microsoftteams/platform/get-started/get-started-tenant)ausführen. Nachdem Sie sichergestellt haben, dass externe apps aktiviert sind, können Sie die folgenden Schritte ausführen, um Ihre APP bereitzustellen.

1. Öffnen Sie Microsoft Teams.
2. Klicken Sie auf das **Store** -Symbol in der linken oberen Ecke der Navigationsleiste.
3. Klicken Sie in der Liste der Optionen auf den Link **benutzerdefinierte App hochladen** . *Hinweis:* Wenn Sie als globales Verwaltungsprogramm angemeldet sind, haben Sie die Möglichkeit, die app in den App-Store Ihrer Organisation hochzuladen, andernfalls können Sie die app nur für ein Team laden, von dem Sie Mitglied sind.
4. Wählen Sie `manifest.zip` das zuvor heruntergeladene Paket aus, und klicken Sie auf **Speichern**. Wenn Sie das Manifest-Paket noch nicht heruntergeladen haben, können Sie dies auf der Registerkarte " **Team Einstellungen** " der Plugin-Konfigurationsseite in Moodle tun.

Nachdem Sie die APP installiert haben, können Sie die Registerkarte jedem Kanal hinzufügen, auf den Sie Zugriff haben. Navigieren Sie dazu zum Kanal, klicken Sie auf das **+** Symbol, und wählen Sie Ihre APP aus der Liste aus. Befolgten Sie die Anweisungen, um das Hinzufügen Ihrer Moodle-Kurs Registerkarte zu einem Kanal abzuschließen.

Das ist alles. Sie und Ihr Team können jetzt direkt in Microsoft Teams mit ihren Moodle-Kursen arbeiten.

Wenn Sie ein Feature oder Feedback mit uns teilen möchten, besuchen Sie unsere [Benutzer-VoIP-Seite](https://microsoftteams.uservoice.com/forums/916759-moodle).
