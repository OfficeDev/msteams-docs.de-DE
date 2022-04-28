---
title: Einrichten Ihrer Entwicklungsumgebung zum Erweitern Teams Apps über Microsoft 365
description: Hier sind die Voraussetzungen für die Erweiterung Ihrer Teams-Apps über Microsoft 365
ms.date: 02/11/2022
ms.openlocfilehash: 094da29fdb871ef4af091e32e123e2d644b7445f
ms.sourcegitcommit: 0117c4e750a388a37cc189bba8fc0deafc3fd230
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2022
ms.locfileid: "65104070"
---
# <a name="set-up-your-dev-environment-for-extending-teams-apps-across-microsoft-365"></a>Einrichten Ihrer Entwicklungsumgebung zum Erweitern Teams Apps über Microsoft 365

> [!NOTE]
> Die Teams-App über Microsoft 365 ist derzeit nur in [der öffentlichen Entwicklervorschau](~/resources/dev-preview/developer-preview-intro.md) verfügbar.

Die Entwicklungsumgebung zum Erweitern Teams Apps über Microsoft 365 hinweg ähnelt Microsoft Teams Entwicklung. In diesem Artikel werden spezifische Konfigurationen erläutert, die zum Ausführen von Vorschaubuilds von Microsoft Teams- und Microsoft Office-Anwendungen erforderlich sind, um eine Vorschau Teams Apps anzuzeigen, die in Outlook und Office ausgeführt werden.

So richten Sie die Entwicklungsumgebung ein:

> [!div class="checklist"]
>
> * [Abrufen Microsoft 365 Entwicklermandanten (Sandkastenmandant) und Aktivieren des Querladens](#prepare-a-developer-tenant-for-testing)
> * [Registrieren Ihres Microsoft 365 Mandanten in *Office 365 Targeted Releases*](#enroll-your-developer-tenant-for-office-365-targeted-releases)
> * [Konfigurieren Ihres Kontos für den Zugriff auf Vorschauversionen von Outlook und Office](#install-office-apps-in-your-test-environment)
> * [Wechseln zur Developer Preview-Version von Teams](#switch-to-the-developer-preview-version-of-teams)
> * [*Optional*] [Installieren Teams Toolkit-Erweiterung für Microsoft Visual Studio Code](#install-visual-studio-code-and-teams-toolkit-preview-extension)

## <a name="prepare-a-developer-tenant-for-testing"></a>Vorbereiten eines Entwicklermandanten für Tests

Sie benötigen einen Sandkastenmandanten für Microsoft 365 Entwicklerabonnements, um Ihre Entwicklungsumgebung einzurichten. Wenn Sie noch keinen haben, erstellen Sie einen [Sandkastenmandanten](/office/developer-program/microsoft-365-developer-program-get-started) , oder rufen Sie einen Testmandanten über Ihre Organisation ab.

Nachdem Sie einen Mandanten haben, müssen Sie das Querladen für Ihren Mandanten aktivieren. Weitere Informationen finden Sie [unter Aktivieren des Querladens](/microsoftteams/platform/concepts/build-and-test/prepare-your-o365-tenant#enable-custom-teams-apps-and-turn-on-custom-app-uploading). Um zu überprüfen, ob das Querladen aktiviert ist, melden Sie sich bei Teams an, wählen Sie **Apps** aus, und suchen Sie dann **nach Hochladen einer benutzerdefinierten App-Option**.

:::image type="content" source="images/teams-sideloading-enabled.png" alt-text="Hochladen einer benutzerdefinierten App-Option":::

## <a name="enroll-your-developer-tenant-for-office-365-targeted-releases"></a>Registrieren Ihres Entwicklermandanten für Office 365 Targeted Releases

> [!IMPORTANT]
> Lesen Sie die neuesten Updates auf [Microsoft Teams – Microsoft 365 Developer Blog](https://devblogs.microsoft.com/microsoft365dev/), um zu überprüfen, ob Outlook.com- und Office.com-Unterstützung für Teams-Apps für Ihren Testmandanten verfügbar ist.

So registrieren Sie Ihren Testmandanten für Office 365 zielorientierte Versionen:

1. Melden Sie sich bei [Microsoft 365 Admin Center](https://admin.microsoft.com) mit Ihren Anmeldeinformationen für den Testmandanten an.
1. Wechseln Sie zum **Profil "Einstellungen** >  **Org Einstellungen** >  **Organization"**.
1. Wählen Sie **"Veröffentlichungseinstellungen"** aus.
1. Wählen Sie eine *beliebige Einstellung für gezielte Veröffentlichungen* aus:
    1. **Zielversion für alle Benutzer**
    1. **Zielversion für ausgewählte Benutzer**

    :::image type="content" source="images/m365-admin-center-targeted-releases.png" alt-text="Microsoft 365 Admin Center Menü &quot;Veröffentlichungseinstellungen&quot; mit ausgewählter Option &quot;Targeted Release&quot;":::

1. Wählen Sie **Speichern**.

Weitere Informationen zu Office 365 Veröffentlichungsoptionen finden [Sie unter Einrichten der Standard- oder Targeted Release-Optionen](/microsoft-365/admin/manage/release-options-in-office-365?view=o365-worldwide&preserve-view=true#targeted-release) in *Microsoft 365 Admin Center Hilfe*.

## <a name="install-office-apps-in-your-test-environment"></a>Installieren Office Apps in Ihrer Testumgebung

> [!IMPORTANT]
> Lesen Sie die neuesten Updates für [Microsoft Teams – Microsoft 365 Entwicklerblog](https://devblogs.microsoft.com/microsoft365dev/), um zu überprüfen, ob Outlook für Windows Desktopunterstützung für Teams Nachrichtenerweiterungen für Ihren Testmandanten verfügbar ist.

Sie können eine Vorschau Teams Apps anzeigen, die in Outlook auf Windows Desktop ausgeführt werden, indem Sie einen aktuellen *Betakanalbuild verwenden*. Überprüfen Sie, ob Sie [den Microsoft 365 Apps Updatekanal](/deployoffice/change-update-channels?WT.mc_id=M365-MVP-5002016) für Ihren Testmandanten ändern müssen, um einen Office 365 Betakanalbuild zu installieren.

So installieren Sie Office 365 Betakanalanwendungen in Ihrer Testumgebung:

1. Melden Sie sich mit Ihren Anmeldeinformationen für den Testmandanten bei Ihrer Testumgebung an.
1. Laden Sie das [Office-Bereitstellungstool](https://www.microsoft.com/download/details.aspx?id=49117) herunter, und extrahieren Sie es in einen lokalen Ordner.
1. Wechseln Sie zum lokalen Ordner, und öffnen Sie *configuration-Office365-x86.xml* (oder **x64.xml*, je nach Ihrer Umgebung) in einem Text-Editor, und aktualisieren Sie den *Kanalwert* auf `BetaChannel`.
1. Öffnen Sie die Eingabeaufforderung, und navigieren Sie zum Pfad des lokalen Ordners.
1. Führen Sie `setup.exe /configure configuration-Office365-x86.xml` die **-x64.xml-Datei* aus (oder verwenden Sie sie, je nach Setup).
1. Öffnen Sie Outlook (Desktopclient), und richten Sie das E-Mail-Konto mit Ihren Testmandantenanmeldeinformationen ein.
1. Öffnen **Sie Outlook "File** >  **Office** **AccountAbout** > ".  
   Wenn die Buildnummer **14416** oder höher ist und der Kanal *Betakanal* ist, führen Sie Microsoft 365 Betakanalbuild aus.
1. Aktivieren Sie in der oberen rechten Ecke den Umschalter " **In Kürze verfügbar** ".

    :::image type="content" source="images/outlook-coming-soon.png" alt-text="Umschaltoption &quot;In Kürze verfügbar&quot; in Outlook":::

> [!NOTE]
> Möglicherweise müssen Sie Outlook schließen und ihren Computer neu starten, damit die Schaltfläche "*In Kürze* verfügbar" angezeigt wird.

Sie können die Unterstützung von Testmandanten für Ihr Mandantenkonto überprüfen:

* Melden Sie sich bei Teams persönlichen Registerkarten, die auf office.com, outlook.com und Outlook für Windows Desktop ausgeführt werden, mit Ihren Anmeldeinformationen für den Testmandanten an, und suchen Sie auf der linken Randleiste von Office oder Outlook nach Auslassungszeichen (**...**).

    :::image type="content" source="images/outlook-desktop-ellipses.png" alt-text="Option &quot;Auslassungszeichen&quot; ('...') auf der linken Randleiste von Outlook":::

* Wenn Nachrichtenerweiterungen in outlook.com und Outlook für Windows angezeigt werden, suchen Sie unten im Bereich zum Outlook Verfassen von Nachrichten nach der Option "**Weitere Apps**".

    :::image type="content" source="images/outlook-web-compose-more-apps.png" alt-text="Option &quot;Weitere Apps&quot; im Bereich &quot;Nachricht Outlook verfassen&quot;":::

> [!NOTE]
> Wenn Sie sich für Betakanalversionen angemeldet haben, aber diese Auslassungszeichenoptionen nicht angezeigt werden, ist es wahrscheinlich, dass die Vorschaufeatures für Ihren Mandanten bereitgestellt werden. Die neuesten Updates finden Sie [im Microsoft Teams Developer Blog](https://devblogs.microsoft.com/microsoft365dev/).

## <a name="switch-to-the-developer-preview-version-of-teams"></a>Wechseln zur Developer Preview-Version von Teams

Stellen Sie sicher, dass Sie von Ihrem Microsoft Teams-Client zur [öffentlichen Entwicklervorschau](../resources/dev-preview/developer-preview-intro.md) wechseln.

1. Melden Sie sich bei Teams mit Ihren Sandkastenmandantenanmeldeinformationen an.
1. Wählen Sie im Menü mit den Auslassungspunkten (**...**) neben Ihrem Benutzerprofil die Option **"****InfoEntwicklungsvorschau** > " aus. Ein Dialogfeld wird angezeigt, und wählen Sie **"Zur Entwicklervorschau wechseln"** aus.
1. Nachdem die Teams App neu gestartet wurde, wechseln Sie zum Menü mit den Auslassungspunkten (**...**) neben Ihrem Benutzerprofil, und überprüfen Sie, ob **die Entwicklervorschau** ausgewählt ist.

    :::image type="content" source="images/teams-dev-preview.png" alt-text="Vorschauoption für öffentliche Entwickler in Teams":::

## <a name="install-visual-studio-code-and-teams-toolkit-preview-extension"></a>Installieren Visual Studio Code und Teams Toolkit Preview-Erweiterung

Optional können Sie [Visual Studio Code](https://code.visualstudio.com/) verwenden, um Teams Apps in Office und Outlook zu erweitern.

Die Erweiterung [Teams Toolkit für Visual Studio Code](https://aka.ms/teams-toolkit) (`v2.10.0`oder höher) bietet Befehle, mit denen Sie Ihren vorhandenen Teams Code so ändern können, dass er mit Outlook und Office kompatibel ist. Weitere Informationen finden Sie unter [Aktivieren Teams persönlichen Registerkarte für Office und Outlook](extend-m365-teams-personal-tab.md).

## <a name="next-steps"></a>Nächste Schritte

* [Aktivieren einer persönlichen Teams-Registerkarte für Office und Outlook](extend-m365-teams-personal-tab.md)
* [Aktivieren einer Teams-Nachrichtenerweiterung für Outlook](extend-m365-teams-message-extension.md)
