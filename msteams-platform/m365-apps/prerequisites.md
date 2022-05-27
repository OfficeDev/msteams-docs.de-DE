---
title: Richten Sie Ihre Entwicklungsumgebung für die Erweiterung von Teams-Apps auf Microsoft 365 ein
description: Hier sind die Voraussetzungen für die Erweiterung Ihrer Teams-Apps auf Microsoft 365
ms.date: 05/24/2022
ms.custom: m365apps
ms.localizationpriority: high
ms.openlocfilehash: fc96d8883f0ad09ebd321a392481e75d92ae8641
ms.sourcegitcommit: c197fe4c721822b6195dfc5c7d8e9ccd47f142fe
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/25/2022
ms.locfileid: "65668025"
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

Außerdem müssen Sie das Sideloading für Ihren Mandanten aktivieren:

1. Melden Sie sich beim Microsoft 365 Admin Center an (https://admin.microsoft.com) mit den Anmeldeinformationen für Ihren Testmandanten), und wählen Sie im Seitenbereich **Microsoft Teams** aus, um das *Microsoft Teams Admin Center* zu öffnen.
1. Auswählen: Microsoft Teams-Apps > Apps verwalten > **Organisationsweite App-Einstellungen**.
1. Aktivieren Sie unter **Benutzerdefinierte Apps** die Option *Interaktion mit benutzerdefinierten Apps*.

    :::image type="content" source="images/teams-admin-enable-sideloading.png" alt-text="Aktivieren Sie das Sideloading für benutzerdefinierte Apps über das Teams-Administrationszentrum":::

## <a name="enroll-your-developer-tenant-for-office-365-targeted-releases"></a>Registrieren Sie Ihren Entwicklermandanten für gezielte Versionen von Office 365

> [!Important]
> Es kann bis zu fünf Tage nach dem Erstellen eines [Microsoft 365 Entwickler-Sandkastenmandanten](/office/developer-program/microsoft-365-developer-program-get-started) und der Registrierung in [Office 365 Targeted-Versionen](#enroll-your-developer-tenant-for-office-365-targeted-releases) für quergeladene Teams-Apps dauern, die in Outlook und Office angezeigt werden.

So registrieren Sie Ihren Testmandanten für gezielte Versionen von Office 365:

1. Melden Sie sich mit Ihren Anmeldeinformationen für den Testmandanten beim [Microsoft 365 Admin Center](https://admin.microsoft.com) an.
1. Gehen Sie zu **Einstellungen** > **Organisationseinstellungen** > **Organisationsprofil**.
1. Wählen Sie **Release-Einstellungen aus**.
1. Wählen Sie eine beliebige Einstellung für die *gezielte Veröffentlichung* aus:
    1. **Zielfreigabe für alle**
    1. **Zielversion für ausgewählte Benutzer**

    :::image type="content" source="images/m365-admin-center-targeted-releases.png" alt-text="Microsoft 365 Admin Center-Menü „Release-Einstellungen“ mit ausgewählter Option „Targeted Release“":::

1. Wählen Sie **Speichern**.

Weitere Informationen zu den Veröffentlichungsoptionen von Office 365 finden [Sie unter Einrichten der Standard- oder zielgerichteten Veröffentlichungsoptionen](/microsoft-365/admin/manage/release-options-in-office-365?view=o365-worldwide&preserve-view=true#targeted-release) in der *Microsoft 365 Admin Center-Hilfe*.

## <a name="install-office-apps-in-your-test-environment"></a>Installieren Sie Office-Apps in Ihrer Testumgebung

Sie können eine Vorschau von Teams-Apps anzeigen, die in Outlook auf dem Windows-Desktop ausgeführt werden, indem Sie einen aktuellen *Betakanal-Build verwenden*. Überprüfen Sie, ob Sie den [Updatekanal](/deployoffice/change-update-channels?WT.mc_id=M365-MVP-5002016) für Microsoft 365-Apps für Ihren Testmandanten ändern müssen, um einen Office 365-Betakanal-Build zu installieren.

So installieren Sie Office 365 Beta Channel-Anwendungen in Ihrer Testumgebung:

1. Melden Sie sich mit Ihren Testmandanten-Anmeldeinformationen bei Ihrer Testumgebung an.
1. Laden Sie das [Office-Bereitstellungstool](https://www.microsoft.com/download/details.aspx?id=49117) herunter und extrahieren Sie es in einen lokalen Ordner.
1. Gehen Sie zum lokalen Ordner und öffnen Sie *configuration-Office365-x86.xml* (oder **x64.xml*, abhängig von Ihrer Umgebung) in einem *Texteditor* und aktualisieren Sie den Kanalwert auf `BetaChannel`.
1. Öffnen Sie die Eingabeaufforderung und navigieren Sie zum lokalen Ordnerpfad.
1. Ausführen `setup.exe /configure configuration-Office365-x86.xml` (oder verwenden Sie die **x64.xml* Datei, abhängig von Ihrer Einrichtung).
1. Öffnen Sie Outlook (Desktop-Client) und richten Sie das E-Mail-Konto mit Ihren Testmandanten-Anmeldeinformationen ein.
1. Öffnen Sie **Datei** > **Office-Konto** > **Informationen zu Outlook** um zu bestätigen, dass Sie einen Microsoft 365 *Beta-Kanal* Build von Outlook ausführen.

    :::image type="content" source="images/outlook-about-beta-channel.png" alt-text="Gehen Sie in Ihrem Office-Konto zu &quot;Über Outlook&quot;, um zu überprüfen, ob Sie ein Beta-Channel-Build ausführen.":::

1. Stellen Sie sicher, dass *Microsoft Edge WebView2 Runtime* installiert ist. Öffnen Sie Windows **Start** > **Apps & Features** und suchen Sie nach **Webansicht**:

    :::image type="content" source="images/windows-addremove-webview2.png" alt-text="Suchen Sie in Ihrem Windows Einstellungen unter &quot;Apps und Features&quot; nach &quot;Webview&quot;":::

    Wenn es nicht aufgeführt ist, installieren Sie [Microsoft Edge WebView2](https://developer.microsoft.com/microsoft-edge/webview2/) in Ihrer Testumgebung.

## <a name="switch-to-the-developer-preview-version-of-teams"></a>Wechseln Sie zur Developer Preview-Version von Teams

Stellen Sie sicher, dass Sie von Ihrem Microsoft Teams-Client zur [öffentlichen Entwicklervorschau](../resources/dev-preview/developer-preview-intro.md) wechseln.

1. Melden Sie sich mit Ihren Sandbox-Mandantenanmeldeinformationen bei Teams an.
1. Wählen Sie im Menü mit den Auslassungspunkten (**...**) neben Ihrem Benutzerprofil die Option **Über** > **Entwicklervorschau aus**. Ein Dialogfeld wird angezeigt **Wählen Sie Zur Entwicklervorschau wechseln aus**.
1. Wechseln Sie nach dem Neustart der Teams-App zum Menü mit den Auslassungspunkten (**...**) neben Ihrem Benutzerprofil, und überprüfen Sie, ob **Entwicklervorschau ausgewählt** ist.

    :::image type="content" source="images/teams-dev-preview.png" alt-text="Vorschauoption für öffentliche Entwickler in Teams":::

## <a name="install-visual-studio-code-and-teams-toolkit-extension"></a>Install Visual Studio Code and Teams Toolkit extension

Optional können Sie [Visual Studio Code](https://code.visualstudio.com/) verwenden, um Teams-Apps in Office und Outlook zu erweitern.

Die Erweiterung [Teams Toolkit für Visual Studio Code](https://aka.ms/teams-toolkit) (`v2.10.0`oder höher) bietet Befehle, mit denen Sie Ihren vorhandenen Teams-Code so ändern können, dass er mit Outlook und Office kompatibel ist. Weitere Informationen finden Sie unter [Aktivieren der persönlichen Registerkarte von Teams für Office und Outlook](extend-m365-teams-personal-tab.md).

## <a name="next-step"></a>Nächster Schritt

Erstellen oder aktualisieren Sie eine Teams-App für die Ausführung über Microsoft 365:

> [!div class="nextstepaction"]
> [Aktivieren einer persönlichen Teams-Registerkarte für Office und Outlook](extend-m365-teams-personal-tab.md)
> [!div class="nextstepaction"]
> [Aktivieren einer Teams-Messaging-Erweiterung für Outlook](extend-m365-teams-message-extension.md)
