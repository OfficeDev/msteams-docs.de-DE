---
title: Richten Sie Ihre Entwicklungsumgebung für die Erweiterung von Teams-Apps auf Microsoft 365 ein
description: Hier sind die Voraussetzungen für die Erweiterung Ihrer Teams-Apps auf Microsoft 365
ms.date: 02/11/2022
ms.localizationpriority: high
ms.openlocfilehash: 483ae6982dd51a16573655ed14dc93577642ba4b
ms.sourcegitcommit: f15bd0e90eafb00e00cf11183b129038de8354af
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/28/2022
ms.locfileid: "65111500"
---
# <a name="set-up-your-dev-environment-for-extending-teams-apps-across-microsoft-365"></a>Richten Sie Ihre Entwicklungsumgebung für die Erweiterung von Teams-Apps auf Microsoft 365 ein

> [!NOTE]
> Die Extend Teams-App für Microsoft 365 ist derzeit nur in der [öffentlichen Entwicklervorschau verfügbar](~/resources/dev-preview/developer-preview-intro.md).

Die Entwicklungsumgebung zum Erweitern von Teams-Apps auf Microsoft 365 ähnelt der Microsoft Teams-Entwicklung. In diesem Artikel werden bestimmte Konfigurationen erläutert, die zum Ausführen von Vorschau-Builds von Microsoft Teams- und Microsoft Office-Anwendungen erforderlich sind, um eine Vorschau von Teams-Apps anzuzeigen, die in Outlook und Office ausgeführt werden.

So richten Sie die Entwicklungsumgebung ein:

> [!div class="checklist"]
>
> * [Holen Sie sich Microsoft 365 Developer (Sandbox) Tenant und aktivieren Sie das Querladen](#prepare-a-developer-tenant-for-testing)
> * [Registrieren Sie Ihren Microsoft 365-Mandanten in *Office 365 Targeted Releases*](#enroll-your-developer-tenant-for-office-365-targeted-releases)
> * [Konfigurieren Sie Ihr Konto für den Zugriff auf Vorschauversionen von Outlook und Office](#install-office-apps-in-your-test-environment)
> * [Wechseln Sie zur Developer Preview-Version von Teams](#switch-to-the-developer-preview-version-of-teams)
> * [*Optional*] [Installieren Sie die Team Toolkit-Erweiterung für Microsoft Visual Studio Code](#install-visual-studio-code-and-teams-toolkit-preview-extension)

## <a name="prepare-a-developer-tenant-for-testing"></a>Bereiten Sie einen Entwicklermandanten zum Testen vor

Sie benötigen einen Sandbox-Mandanten für Microsoft 365-Entwicklerabonnements, um Ihre Entwicklungsumgebung einzurichten. Wenn Sie noch keinen haben, erstellen Sie einen [Sandbox-Mandanten](/office/developer-program/microsoft-365-developer-program-get-started) oder erhalten Sie einen Testmandanten über Ihre Organisation.

Nachdem Sie einen Mandanten haben, müssen Sie Sideloading für Ihren Mandanten [aktivieren, siehe Sideloading aktivieren](/microsoftteams/platform/concepts/build-and-test/prepare-your-o365-tenant#enable-custom-teams-apps-and-turn-on-custom-app-uploading). Um zu überprüfen, ob das Querladen aktiviert ist, melden Sie sich bei Teams an, wählen Sie **Apps** aus, und aktivieren Sie dann die Option zum **Hochladen einer** benutzerdefinierten App.

:::image type="content" source="images/teams-sideloading-enabled.png" alt-text="Laden Sie eine benutzerdefinierte App-Option hoch":::

## <a name="enroll-your-developer-tenant-for-office-365-targeted-releases"></a>Registrieren Sie Ihren Entwicklermandanten für gezielte Versionen von Office 365

> [!IMPORTANT]
> Sehen Sie sich die neuesten Updates auf [Microsoft Teams – Microsoft 365 Developer Blog](https://devblogs.microsoft.com/microsoft365dev/) an, um zu überprüfen, ob Outlook.com- und Office.com-Support für Teams-Apps für Ihren Testmandanten verfügbar ist.

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

> [!IMPORTANT]
> Sehen Sie sich die neuesten Updates auf [Microsoft Teams – Microsoft 365 Developer Blog](https://devblogs.microsoft.com/microsoft365dev/) an, um zu überprüfen, ob Outlook für Windows-Desktopunterstützung für Teams-Nachrichtenerweiterungen für Ihren Testmandanten verfügbar ist.

Sie können eine Vorschau von Teams-Apps anzeigen, die in Outlook auf dem Windows-Desktop ausgeführt werden, indem Sie einen aktuellen *Betakanal-Build verwenden*. Überprüfen Sie, ob Sie den [Updatekanal](/deployoffice/change-update-channels?WT.mc_id=M365-MVP-5002016) für Microsoft 365-Apps für Ihren Testmandanten ändern müssen, um einen Office 365-Betakanal-Build zu installieren.

So installieren Sie Office 365 Beta Channel-Anwendungen in Ihrer Testumgebung:

1. Melden Sie sich mit Ihren Testmandanten-Anmeldeinformationen bei Ihrer Testumgebung an.
1. Laden Sie das [Office-Bereitstellungstool](https://www.microsoft.com/download/details.aspx?id=49117) herunter und extrahieren Sie es in einen lokalen Ordner.
1. Gehen Sie zum lokalen Ordner und öffnen Sie *configuration-Office365-x86.xml* (oder **x64.xml*, abhängig von Ihrer Umgebung) in einem *Texteditor* und aktualisieren Sie den Kanalwert auf `BetaChannel`.
1. Öffnen Sie die Eingabeaufforderung und navigieren Sie zum lokalen Ordnerpfad.
1. Ausführen `setup.exe /configure configuration-Office365-x86.xml` (oder verwenden Sie die **x64.xml* Datei, abhängig von Ihrer Einrichtung).
1. Öffnen Sie Outlook (Desktop-Client) und richten Sie das E-Mail-Konto mit Ihren Testmandanten-Anmeldeinformationen ein.
1. Öffnen Sie das **File** > **Office-Konto** > **über Outlook**.  
   Wenn die Buildnummer **14416** oder höher ist und der Kanal *Betakanal ist*, führen Sie den Microsoft 365-Betakanal-Build aus.
1. Aktivieren Sie in der oberen rechten Ecke den **Umschalter** Demnächst.

    :::image type="content" source="images/outlook-coming-soon.png" alt-text="Umschaltoption „Demnächst verfügbar“ in Outlook":::

> [!NOTE]
> Möglicherweise müssen Sie Outlook schließen und Ihren Computer neu starten, damit die *Schaltfläche* In Kürze angezeigt wird.

Sie können die Testmandantenunterstützung für Ihr Mandantenkonto überprüfen:

* Melden Sie sich für persönliche Registerkarten von Teams, die auf office.com, outlook.com und Outlook für Windows-Desktop ausgeführt werden, mit Ihren Anmeldeinformationen für den Testmandanten an, und überprüfen Sie die Option mit Auslassungspunkten (**...**) in der linken Seitenleiste von Office oder Outlook.

    :::image type="content" source="images/outlook-desktop-ellipses.png" alt-text="Auslassungspunkte ('...') Option in der linken Seitenleiste von Outlook":::

* Suchen Sie für Nachrichtenerweiterungen in outlook.com und Outlook für Windows nach der Option **Weitere Apps** unten im Bereich zum Verfassen von Nachrichten in Outlook.

    :::image type="content" source="images/outlook-web-compose-more-apps.png" alt-text="Option „Weitere Apps“ im Bereich zum Verfassen von Nachrichten in Outlook":::

> [!NOTE]
> Wenn Sie sich für Betakanalversionen angemeldet haben, diese Auslassungspunkte jedoch nicht angezeigt werden, ist es wahrscheinlich, dass die Unterstützung der Vorschaufunktion für Ihren Mandanten gerade eingeführt wird. Die neuesten Updates finden Sie im [Microsoft Teams Developer Blog](https://devblogs.microsoft.com/microsoft365dev/).

## <a name="switch-to-the-developer-preview-version-of-teams"></a>Wechseln Sie zur Developer Preview-Version von Teams

Stellen Sie sicher, dass Sie von Ihrem Microsoft Teams-Client zur [öffentlichen Entwicklervorschau](../resources/dev-preview/developer-preview-intro.md) wechseln.

1. Melden Sie sich mit Ihren Sandbox-Mandantenanmeldeinformationen bei Teams an.
1. Wählen Sie im Menü mit den Auslassungspunkten (**...**) neben Ihrem Benutzerprofil die Option **Über** > **Entwicklervorschau aus**. Ein Dialogfeld wird angezeigt **Wählen Sie Zur Entwicklervorschau wechseln aus**.
1. Wechseln Sie nach dem Neustart der Teams-App zum Menü mit den Auslassungspunkten (**...**) neben Ihrem Benutzerprofil, und überprüfen Sie, ob **Entwicklervorschau ausgewählt** ist.

    :::image type="content" source="images/teams-dev-preview.png" alt-text="Vorschauoption für öffentliche Entwickler in Teams":::

## <a name="install-visual-studio-code-and-teams-toolkit-preview-extension"></a>Installieren Sie Visual Studio Code and Teams Toolkit Preview-Erweiterung

Optional können Sie [Visual Studio Code](https://code.visualstudio.com/) verwenden, um Teams-Apps in Office und Outlook zu erweitern.

Die Erweiterung [Teams Toolkit für Visual Studio Code](https://aka.ms/teams-toolkit) (`v2.10.0` oder höher) stellt Befehle bereit, mit denen Sie Ihren vorhandenen Teams-Code so ändern können, dass er mit Outlook und Office kompatibel ist. Weitere Informationen finden Sie unter Persönliche [Registerkarte „Teams“ für Office und Outlook aktivieren](extend-m365-teams-personal-tab.md).

## <a name="next-steps"></a>Nächste Schritte

* [Aktivieren einer persönlichen Teams-Registerkarte für Office und Outlook](extend-m365-teams-personal-tab.md)
* [Aktivieren einer Teams-Messaging-Erweiterung für Outlook](extend-m365-teams-message-extension.md)
