---
title: Richten Sie Ihre Entwicklungsumgebung für die Erweiterung Teams Apps über Microsoft 365
description: Hier sind die Voraussetzungen für die Erweiterung Ihrer Teams-Apps über Microsoft 365
ms.date: 11/15/2021
ms.topic: how-to
ms.openlocfilehash: d9e6ecb9e0cdbdb4754de12dff4399c02bf88863
ms.sourcegitcommit: f77750f2e60f63d1e2f66a96c169119683c66950
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/15/2021
ms.locfileid: "60960311"
---
# <a name="set-up-your-dev-environment-for-extending-teams-apps-across-m365-preview"></a>Einrichten der Entwicklungsumgebung für die Erweiterung Teams Apps über M365 hinweg (Vorschau)

Die Entwicklungsumgebung für die Erweiterung Teams Apps über Microsoft 365 hinweg ähnelt der Umgebung, die Sie für Microsoft Teams Entwicklung verwenden. In diesem Artikel werden bestimmte Konfigurationen erläutert, die zum Ausführen von Vorschaubuilds von Microsoft Teams- und Microsoft Office-Anwendungen erforderlich sind, um eine Vorschau Teams Apps anzuzeigen, die in Outlook und Office ausgeführt werden. Um Ihre Entwicklungsumgebung einzurichten, müssen Sie Folgendes tun:

> [!div class="checklist"]
> * [Abrufen eines Mandanten für M365-Entwickler (Sandbox) und Aktivieren des Querladens](#prepare-a-developer-tenant-for-testing)
> * [Registrieren Ihres M365-Mandanten in *Office 365 gezielten Versionen*](#enroll-your-developer-tenant-for-office-365-targeted-releases)
> * [Konfigurieren Ihres Kontos für den Zugriff auf Vorschauversionen von Outlook und Office](#install-beta-office-apps-in-your-test-environment)
> * [Wechseln Sie zur Developer Preview-Version von Teams](#switch-to-the-developer-preview-version-of-teams)
> * [*Optional*] [Installieren Teams Toolkit-Erweiterung für Visual Studio Code](#install-visual-studio-code-and-teams-toolkit-preview-extension)

## <a name="prepare-a-developer-tenant-for-testing"></a>Vorbereiten eines Entwicklermandanten für Tests

Wenn Sie noch nicht über einen verfügen, erstellen Sie einen Sandkastenmandanten [für Microsoft 365 Entwicklerabonnement,](/office/developer-program/microsoft-365-developer-program-get-started) oder rufen Sie einen Testmandanten über Ihre Organisation ab.

Nachdem Sie über einen Mandanten verfügen, müssen Sie das Querladen für Ihren Mandanten [aktivieren,](/microsoftteams/platform/concepts/build-and-test/prepare-your-o365-tenant#enable-custom-teams-apps-and-turn-on-custom-app-uploading) indem Sie sich bei [Microsoft 365 Admin Center](https://admin.microsoft.com) anmelden und zu "Alle > Teams > Teams Apps > Setuprichtlinien > **Global** anzeigen" navigieren.  Umschalten auf **Hochladen benutzerdefinierten Apps** und **Speichern**.

Wenn Sie über einen vorhandenen Mandanten verfügen, überprüfen Sie, ob das Querladen aktiviert ist, indem Sie sich bei Teams anmelden und **Apps** auswählen. Sie sehen die **Hochladen einer benutzerdefinierten** App-Option, wenn das Querladen für Ihren Mandanten aktiviert ist.

:::image type="content" source="images/teams-sideloading-enabled.png" alt-text="Das Querladen ist für Ihren Mandanten aktiviert, wenn die Option &quot;Hochladen einer benutzerdefinierten App&quot; im Bereich Teams &quot;Apps&quot; angezeigt wird.":::

## <a name="enroll-your-developer-tenant-for-office-365-targeted-releases"></a>Registrieren Ihres Entwicklermandanten für Office 365 zielgerichtete Versionen

> [!IMPORTANT]
> Informationen dazu, ob outlook.com und office.com Unterstützung für Teams Apps für Ihren Testmandanten verfügbar ist, finden Sie im neuesten Microsoft Teams – [Microsoft 365 Entwicklerblog.](https://devblogs.microsoft.com/microsoft365dev/category/teams/)

Um eine Vorschau Teams Apps anzuzeigen, die in outlook.com oder office.com ausgeführt werden, aktivieren Sie Ihren Testmandanten, um [gezielte Versionen](/microsoft-365/admin/manage/release-options-in-office-365#targeted-release)zu Office 365.

1. Melden Sie sich bei Microsoft 365 Admin Center mithilfe von Anmeldeinformationen für Ihren Testmandanten an, und navigieren Sie zur Registerkarte ["Organisationsprofil".](https://admin.microsoft.com/AdminPortal/Home?#/Settings/OrganizationProfile) Wählen Sie **"Versionseinstellungen"** aus, und wählen Sie eine der Einstellungen für die *gezielte Veröffentlichung* aus:

:::image type="content" source="images/m365-admin-center-targeted-releases.png" alt-text="Microsoft 365 Admin Center Menü &quot;Versionseinstellungen&quot; mit ausgewählter Option für die gezielte Veröffentlichung":::

Weitere Informationen zu Office 365 Releaseoptionen finden Sie unter ["Einrichten der Standard- oder Targeted Release-Optionen"](/microsoft-365/admin/manage/release-options-in-office-365) in *Microsoft 365 Admin Center Hilfe.*

1. Stellen Sie sicher, dass Ihr Mandant Unterstützung für Teams persönlichen Registerkarten hat, die auf office.com und outlook.com ausgeführt werden, indem Sie sich mit Ihren Testmandantenanmeldeinformationen anmelden. Wenn auf der Seitenleiste eine Ellipse (**...**) angezeigt wird (der Einstiegspunkt für quergeladene Teams persönliche Registerkarten), hat Ihr Mandant Unterstützung.

:::image type="content" source="images/outlook-web-ellipses.png" alt-text="Ellipses '...' Einstiegspunkt für quergeladene Teams Registerkarten-Apps in outlook.com":::

1. Überprüfen Sie die Mandantenunterstützung für Messaging-Erweiterungen in outlook.com, indem Sie im Outlook Nachrichtenbereich zum Verfassen nach der Option **"Weitere Apps"** suchen.
``

> [!NOTE]
> Wenn Sie sich für gezielte Versionen entschieden haben, diese Optionen jedoch nicht angezeigt werden, ist es wahrscheinlich, dass die Vorschaufeatureunterstützung noch in der Einführung für Ihren Mandanten erfolgt. Die neuesten Updates finden Sie [im Microsoft Teams Developer Blog.](https://devblogs.microsoft.com/microsoft365dev/category/teams/)

## <a name="install-beta-office-apps-in-your-test-environment"></a>Installieren von Beta-Office-Apps in Ihrer Testumgebung

> [!IMPORTANT]
> Lesen Sie den neuesten [Microsoft Teams – Microsoft 365 Entwicklerblog,](https://devblogs.microsoft.com/microsoft365dev/category/teams/) um zu überprüfen, ob Outlook für Windows Desktopunterstützung für Teams Nachrichtenerweiterungen für Ihren Testmandanten verfügbar ist.

Sie können eine Vorschau Teams Apps anzeigen, die in Outlook auf Windows Desktop ausgeführt werden, indem Sie einen aktuellen *Betakanalbuild* verwenden. Um einen Outlook Betakanalbuild in Ihrer Testumgebung zu installieren, müssen Sie wahrscheinlich [den Microsoft 365 Apps Updatekanal](/deployoffice/change-update-channels?WT.mc_id=M365-MVP-5002016) für Ihren Testmandanten ändern.

Hier sind die Schritte zum Installieren von Office 365 *Betakanalanwendungen* in Ihrer Testumgebung:

1. Melden Sie sich in Ihrer Testumgebung bei Microsoft 365 Admin Center an ( https://admin.microsoft.com) mit den Anmeldeinformationen, die Sie für Ihren Testmandanten erstellt haben (z. B. *Benutzername* @ *Domäne*.onmicrosoft.com).
1. Wählen Sie im Admin Center die Option **"Installieren Office"** (oder *wechseln Sie zum geführten Setup),* um Desktop-Apps in Ihrer Testumgebung zu installieren. Fügen Sie optional einen Testbenutzer hinzu (nützlich für Tests).
1. Laden Sie das [Office-Bereitstellungstool herunter,](https://www.microsoft.com/download/details.aspx?id=49117) und extrahieren Sie es in einen lokalen Ordner.
1. Öffnen *Sieconfiguration-Office365-x86.xml* (oder das **x64.xml*, je nach Umgebung) in einem Text-Editor, und aktualisieren Sie den *Kanalwert* auf `BetaChannel` .
1. Führen Sie an einer Eingabeaufforderung mit erhöhten Rechten `setup.exe /configure configuration-Office365-x86.xml` je nach Setup die Datei **x64.xml* aus.
1. Öffnen Sie Outlook (Desktopclient), und richten Sie das E-Mail-Konto mit Ihren Testmandantenanmeldeinformationen ein.
1. Öffnen Sie in Outlook **"Datei**  >  **Office Konto** über  >  **Outlook",** und vergewissern Sie sich, dass Sie sich jetzt im *Betakanal* befinden und dass Ihre Buildnummer **14416** oder höher ist.
1. Aktivieren Sie die Schaltfläche **"Bald verfügbar"** in der Ecke ihres Outlook Clientfensters:

   :::image type="content" source="images/outlook-coming-soon.png" alt-text="Schaltfläche &quot;Bald verfügbar&quot; in Outlook Desktop auf &quot;Ein&quot; umgeschaltet":::

Sie können überprüfen, ob Ihr Mandant Teams persönliche Registerkarten unterstützt, die auf Outlook für Windows Desktop ausgeführt werden, indem Sie sich mit Ihren Testmandantenanmeldeinformationen anmelden und in der Seitenleiste nach einer Ellipse **(...**) suchen (der Einstiegspunkt für quergeladene Teams persönliche Registerkarten).

:::image type="content" source="images/outlook-desktop-ellipses.png" alt-text="Ellipses '...' Einstiegspunkt für quergeladene Teams Registerkarten-Apps in Outlook für Desktop":::

Auf ähnliche Weise können Sie die Mandantenunterstützung für Messaging-Erweiterungen in Outlook für Windows Desktop überprüfen, indem Sie im Menüband zum Outlook Verfassen von Nachrichten nach der Option **"Weitere Apps"** suchen.

Wenn Sie sich für gezielte Versionen entschieden haben, aber diese Ellipsenoptionen nicht angezeigt werden, ist es wahrscheinlich, dass die Vorschaufeatureunterstützung noch in der Einführung für Ihren Mandanten erfolgt. Die neuesten Updates finden Sie [im Microsoft Teams Developer Blog.](https://devblogs.microsoft.com/microsoft365dev/category/teams/)

## <a name="switch-to-the-developer-preview-version-of-teams"></a>Wechseln zur Developer Preview-Version von Teams

Stellen Sie sicher, dass Sie sich von Ihrem Microsoft Teams Client für die [*öffentliche Entwicklervorschau*](../resources/dev-preview/developer-preview-intro.md) anmelden.

1. Melden Sie sich mit Ihrem Sandkastenmandantenkonto bei Teams an.
1. Wählen Sie im Menü mit den Auslassungspunkten (**...**) neben Ihrem Benutzerprofil die Option **"Info"** und dann die Option **"Entwicklervorschau"** aus.
1. Nachdem das Dialogfeld angezeigt wurde, wählen Sie **"Zur Entwicklervorschau wechseln"** aus, um Teams neu zu starten, und überprüfen Sie, ob die Entwicklervorschau jetzt aktiviert ist.

:::image type="content" source="images/teams-dev-preview.png" alt-text="Öffnen Sie im Menü Teams Auslassungspunkte &quot;Info&quot;, und überprüfen Sie, ob die Option &quot;Entwicklervorschau&quot; aktiviert ist.":::

## <a name="install-visual-studio-code-and-teams-toolkit-preview-extension"></a>Installieren der Vorschauerweiterung für Visual Studio Code und Teams Toolkit

Optional können Sie [Visual Studio Code](https://code.visualstudio.com/) nutzen, um Teams Apps auf Office und Outlook zu erweitern.

Die Erweiterung [Teams Toolkit für Visual Studio Code](https://aka.ms/teams-toolkit) `v2.10.0` (oder höher) bietet Befehle, mit denen Sie Ihren vorhandenen Teams-Code so ändern können, dass er mit Outlook und Office kompatibel ist. Aktivieren Sie weiterhin [Teams persönliche Registerkarte für Office und Outlook,](extend-m365-teams-personal-tab.md) um mehr zu erfahren.

## <a name="next-steps"></a>Nächste Schritte

- [Aktivieren einer Teams persönlichen Registerkarte für Office und Outlook](extend-m365-teams-personal-tab.md)
- [Aktivieren einer Teams Messaging-Erweiterung für Outlook](extend-m365-teams-message-extension.md)