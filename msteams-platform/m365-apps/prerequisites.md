---
title: Richten Sie Ihre Entwicklungsumgebung für die Erweiterung von Teams-Apps auf Microsoft 365 ein
description: Anforderungen zum Einrichten Ihrer Entwicklungsumgebung für die Erweiterung von Teams-Apps auf Microsoft 365. Kennen Sie konfigurationen, die zum Ausführen von Builds von Microsoft Teams und Microsoft Office-Anwendungen erforderlich sind.
ms.date: 05/24/2022
ms.custom: m365apps
ms.topic: conceptual
ms.localizationpriority: high
ms.openlocfilehash: 99050d8b8db4fac38e9d36c42a6c3efe7f1bf28d
ms.sourcegitcommit: 10debe0f01574a21aab54bfac692a4c8373263a8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2022
ms.locfileid: "68789912"
---
# <a name="set-up-your-dev-environment-for-extending-teams-apps-across-microsoft-365"></a>Richten Sie Ihre Entwicklungsumgebung für die Erweiterung von Teams-Apps auf Microsoft 365 ein

Die Entwicklungsumgebung zum Erweitern von Teams-Apps auf Microsoft 365 ähnelt der Microsoft Teams-Entwicklung. In diesem Artikel werden bestimmte Konfigurationen erläutert, die zum Ausführen von Vorschau-Builds von Microsoft Teams- und Microsoft Office-Anwendungen erforderlich sind, um eine Vorschau von Teams-Apps anzuzeigen, die in Outlook und Office ausgeführt werden.

So richten Sie die Entwicklungsumgebung ein:

> [!div class="checklist"]
>
> * [Holen Sie sich Microsoft 365 Developer (Sandbox) Tenant und aktivieren Sie das Querladen](#prepare-a-developer-tenant-for-testing)
> * [Registrieren Sie Ihren Microsoft 365-Mandanten in *Office 365 Targeted Releases*](#enroll-your-developer-tenant-for-office-365-targeted-releases)
> * [Installieren Sie Beta Channel Builds von Microsoft 365 Apps in Ihrer Testumgebung](#install-office-apps-in-your-test-environment)
> * [Wechseln Sie zur Developer Preview-Version von Teams](#switch-to-the-developer-preview-version-of-teams)
> * [*Optional*] [Installieren Sie die Team Toolkit-Erweiterung für Microsoft Visual Studio Code](#install-visual-studio-code-and-teams-toolkit-extension)

## <a name="prepare-a-developer-tenant-for-testing"></a>Bereiten Sie einen Entwicklermandanten zum Testen vor

Sie benötigen einen Sandbox-Mandanten für Microsoft 365-Entwicklerabonnements, um Ihre Entwicklungsumgebung einzurichten. Wenn Sie noch keinen haben, erstellen Sie einen [Sandbox-Mandanten](/office/developer-program/microsoft-365-developer-program-get-started) oder erhalten Sie einen Testmandanten über Ihre Organisation.

Außerdem müssen Sie das Querladen für Ihren Mandanten aktivieren:

 1. Melden Sie sich mit Ihren Testmandantenanmeldeinformationen beim [Teams Admin Center](https://admin.teams.microsoft.com/dashboard) an.

 1. Wechseln Sie zu **Teams-Apps** > **Apps verwalten**.

 1. Wählen Sie oben rechts **Organisationsweite App-Einstellungen** aus.

 1. Aktivieren Sie unter Benutzerdefinierte Apps die Umschaltfläche **Interaktion mit benutzerdefinierter App** und **Speichern**.

    :::image type="content" source="images/teams-admin-enable-sideloading.png" alt-text="Der Screenshot ist ein Beispiel, das das Querladen für benutzerdefinierte Apps aus dem Teams Admin Center ermöglicht":::

 1. Neben organisationsweiten App-Einstellungen ermöglichen benutzerdefinierte App-Richtlinieneinstellungen benutzern auch das Hochladen benutzerdefinierter Apps in Teams. Weitere Informationen finden Sie unter [Verwalten von benutzerdefinierten App-Richtlinien und -Einstellungen](/microsoftteams/teams-custom-app-policies-and-settings#custom-app-policy-and-settings).

 1. Wechseln Sie im Teams Admin Center zu **Setuprichtlinien** für **Teams-Apps** > , und wählen Sie dann **Globale (organisationsweite Standard)-Richtlinie** aus.

 1. Aktivieren Sie **Benutzerdefinierte Apps hochladen**, und wählen **Sie Speichern** aus.

## <a name="enroll-your-developer-tenant-for-office-365-targeted-releases"></a>Registrieren Sie Ihren Entwicklermandanten für gezielte Versionen von Office 365

> [!IMPORTANT]
> Es kann bis zu fünf Tage nach dem Erstellen eines [Microsoft 365 Entwickler-Sandkastenmandanten](/office/developer-program/microsoft-365-developer-program-get-started) und der Registrierung in [Office 365 Targeted-Versionen](#enroll-your-developer-tenant-for-office-365-targeted-releases) für quergeladene Teams-Apps dauern, die in Outlook und Office angezeigt werden.

So registrieren Sie Ihren Testmandanten für gezielte Versionen von Office 365:

1. Melden Sie sich mit Ihren Anmeldeinformationen für den Testmandanten beim [Microsoft 365 Admin Center](https://admin.microsoft.com) an.
1. Gehen Sie zu **Einstellungen** > **Organisationseinstellungen** > **Organisationsprofil**.
1. Wählen Sie **Release-Einstellungen aus**.
1. Wählen Sie eine beliebige Einstellung für die *gezielte Veröffentlichung* aus:
    1. **Zielfreigabe für alle**
    1. **Zielversion für ausgewählte Benutzer**

    :::image type="content" source="images/m365-admin-center-targeted-releases.png" alt-text="Der Screenshot ist ein Beispiel, das das Menü Microsoft 365 Admin Center &quot;Releaseeinstellungen&quot; mit ausgewählter Option &quot;Zielversion&quot; zeigt.":::

1. Wählen Sie **Speichern** aus.

Weitere Informationen zu Office 365 Releaseoptionen finden [Sie unter Einrichten der Standard- oder Zielversionsoptionen](/microsoft-365/admin/manage/release-options-in-office-365?view=o365-worldwide&preserve-view=true#targeted-release) in *Microsoft 365 Admin Center Hilfe*.

## <a name="install-office-apps-in-your-test-environment"></a>Installieren Sie Office-Apps in Ihrer Testumgebung

### <a name="desktop"></a>Desktop

Sie können eine Vorschau von Teams-Apps anzeigen, die in Outlook auf dem Windows-Desktop ausgeführt werden, indem Sie einen aktuellen *Betakanal-Build verwenden*. Überprüfen Sie, ob Sie [den Microsoft 365 Apps Updatekanal](/deployoffice/change-update-channels?WT.mc_id=M365-MVP-5002016) für Ihren Testmandanten ändern müssen, um einen Office 365 Betakanal-Build zu installieren.

So installieren Sie Office 365 Beta Channel-Anwendungen in Ihrer Testumgebung:

1. Melden Sie sich mit Ihren Testmandanten-Anmeldeinformationen bei Ihrer Testumgebung an.
1. Laden Sie das [Office-Bereitstellungstool](https://www.microsoft.com/download/details.aspx?id=49117) herunter und extrahieren Sie es in einen lokalen Ordner.
1. Gehen Sie zum lokalen Ordner und öffnen Sie *configuration-Office365-x86.xml* (oder **x64.xml*, abhängig von Ihrer Umgebung) in einem *Texteditor* und aktualisieren Sie den Kanalwert auf `BetaChannel`.
1. Öffnen Sie die Eingabeaufforderung, und wechseln Sie zum Pfad des lokalen Ordners.
1. Ausführen `setup.exe /configure configuration-Office365-x86.xml` (oder verwenden Sie die **x64.xml* Datei, abhängig von Ihrer Einrichtung).
1. Öffnen Sie Outlook (Desktop-Client) und richten Sie das E-Mail-Konto mit Ihren Testmandanten-Anmeldeinformationen ein.
1. Öffnen Sie **Datei** > **Office-Konto** > **Informationen zu Outlook** um zu bestätigen, dass Sie einen Microsoft 365 *Beta-Kanal* Build von Outlook ausführen.

    :::image type="content" source="images/outlook-about-beta-channel.png" alt-text="Der Screenshot zeigt ein Beispiel für Outlook, um zu überprüfen, ob Sie einen Betakanalbuild ausführen.":::

1. Stellen Sie sicher, dass *Microsoft Edge WebView2 Runtime* installiert ist. Öffnen Sie Windows **Start** > **Apps & Features** und suchen Sie nach **Webansicht**:

    :::image type="content" source="images/windows-addremove-webview2.png" alt-text="Der Screenshot ist ein Beispiel, das das Suchfeld in Ihren Windows-Einstellungen zeigt.":::

    Wenn es nicht aufgeführt ist, installieren Sie [Microsoft Edge WebView2](https://developer.microsoft.com/microsoft-edge/webview2/) in Ihrer Testumgebung.

### <a name="mobile"></a>Mobil

Sie können eine Vorschau der persönlichen Teams-Registerkarten anzeigen, die in der Office-App für Android ausgeführt werden, indem Sie dem Betaprogramm beitreten.

Um die neueste Betaversion der Office-App zu installieren, erstellen Sie auf Ihrem physischen Android-Gerät oder Android-Emulator:

1. Stellen Sie sicher, dass Sie ein von Google Play [unterstütztes Android-Gerät](https://support.google.com/googleplay/answer/1727131) verwenden.
1. Starten Sie den **Play Store** auf Ihrem Android-Gerät.
1. Suchen Sie nach Office, und wählen Sie **Microsoft Office: Bearbeiten & Share** aus.
1. Wählen Sie die Schaltfläche **Installieren** aus.

    :::image type="content" source="images/office-android-install.png" alt-text="Der Screenshot ist ein Beispiel, das die Schaltfläche &quot;Installieren&quot; für die App &quot;Microsoft Office: Bearbeiten & Teilen&quot; im Google Play Store zeigt.":::

1. Wählen Sie nach Abschluss der Installation im **Abschnitt An Beta** teilnehmen die Option **Beitreten** aus.

    :::image type="content" source="images/office-android-join-beta.png" alt-text="Der Screenshot ist ein Beispiel, das den Bildschirm &quot;An der Beta teilnehmen&quot; zeigt.":::

1. Starten Sie die Office-App, und melden Sie sich mit Ihren Testmandantenanmeldeinformationen an.
1. Öffnen Sie Ihr Profil **(Ich) > Einstellungen** , und scrollen Sie zum Ende des Menüs.
2. Stellen Sie sicher, dass Sie die Office-App-Version 16.0.15726.20000 oder höher für Android verwenden.

## <a name="switch-to-the-developer-preview-version-of-teams"></a>Wechseln Sie zur Developer Preview-Version von Teams

Stellen Sie sicher, dass Sie von Ihrem Microsoft Teams-Client zur [öffentlichen Entwicklervorschau](../resources/dev-preview/developer-preview-intro.md) wechseln.

1. Melden Sie sich mit Ihren Sandbox-Mandantenanmeldeinformationen bei Teams an.
1. Wählen Sie im Menü mit den Auslassungspunkten (**...**) neben Ihrem Benutzerprofil die Option **Über** > **Entwicklervorschau aus**. Ein Dialogfeld wird angezeigt **Wählen Sie Zur Entwicklervorschau wechseln aus**.
1. Wechseln Sie nach dem Neustart der Teams-App zum Menü mit den Auslassungspunkten (**...**) neben Ihrem Benutzerprofil, und überprüfen Sie, ob **Entwicklervorschau ausgewählt** ist.

    :::image type="content" source="images/teams-dev-preview.png" alt-text="Der Screenshot ist ein Beispiel, das die Öffentliche Entwicklervorschauoption in Teams zeigt.":::

## <a name="install-visual-studio-code-and-teams-toolkit-extension"></a>Install Visual Studio Code and Teams Toolkit extension

Optional können Sie [Visual Studio Code](https://code.visualstudio.com/) verwenden, um Teams-Apps in Office und Outlook zu erweitern.

The extension [Teams Toolkit for Visual Studio Code](https://aka.ms/teams-toolkit) (`v2.10.0` or later) provides commands that can help modify your existing Teams code to be compatible with Outlook and Office. For more information, see [enable Teams personal tab for Office and Outlook](extend-m365-teams-personal-tab.md).

## <a name="next-step"></a>Nächster Schritt

Erstellen oder aktualisieren Sie eine Teams-App für die Ausführung über Microsoft 365:

> [!div class="nextstepaction"]
> [Aktivieren einer persönlichen Teams-Registerkarte für Office und Outlook](extend-m365-teams-personal-tab.md)
> [!div class="nextstepaction"]
> [Aktivieren einer Teams-Messaging-Erweiterung für Outlook](extend-m365-teams-message-extension.md)
