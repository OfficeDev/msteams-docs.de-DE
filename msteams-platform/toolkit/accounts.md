---
title: Vorbereiten von Konten zum Erstellen Teams Apps
author: zyxiaoyuer
description: Vorbereiten von Konten zum Erstellen Teams Apps
ms.author: zhany
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: 6a215922ff4b89c4afdce187be9b03479e6a54e6
ms.sourcegitcommit: f1e6f90fb6f7f5825e55a6d18ccf004d0091fb6d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/30/2021
ms.locfileid: "61228047"
---
# <a name="prepare-accounts-to-build-teams-apps"></a>Vorbereiten von Konten zum Erstellen Teams Apps

Zum Entwickeln einer Teams App ist mindestens ein Microsoft 365 Konto mit einem gültigen Abonnement erforderlich. Wenn Sie Ihre Back-End-Ressourcen in Azure hosten möchten, ist auch ein Azure-Konto erforderlich. Das Azure-Konto ist optional, wenn Ihre vorhandene Anwendung auf einem anderen Cloudanbieter gehostet wird und Sie die vorhandene Anwendung in Teams Plattform integrieren möchten.

## <a name="microsoft-365-account"></a>Microsoft 365-Konto

Wenn Sie über kein vorhandenes Microsoft 365 Konto mit einem gültigen Abonnement verfügen, können Sie ein Konto erstellen, indem Sie dem [Microsoft 365 Entwicklerprogramm](https://developer.microsoft.com/microsoft-365/dev-program)beitreten. Das Microsoft 365-Entwicklerprogramm umfasst ein Microsoft 365 E5-Entwicklerabonnement, mit dem Sie einen eigenen Sandkasten erstellen und Lösungen unabhängig von Ihrer Produktionsumgebung entwickeln können.

## <a name="azure-account"></a>Azure-Konto

Wenn Sie Ihre App-bezogenen Ressourcen hosten oder auf Ressourcen **in Azure** zugreifen möchten, müssen Sie über ein Azure-Abonnement verfügen. Sie können [ein kostenloses Konto erstellen,](https://azure.microsoft.com/free/) bevor Sie beginnen.

## <a name="join-microsoft-365-developer-program"></a>Teilnehmen am Microsoft 365-Entwicklerprogramm 

Wenn Sie über kein Microsoft 365 Konto verfügen, müssen Sie sich für ein [Microsoft 365 Entwicklerprogramm-Abonnement](https://developer.microsoft.com/microsoft-365/dev-program) registrieren. Das Abonnement ist 90 Tage lang kostenlos und wird weiterhin verlängert, solange Sie es für Entwicklungsaktivitäten verwenden. Wenn Sie über ein Visual Studio Enterprise- oder Professional-Abonnement verfügen, enthalten beide Programme ein kostenloses Microsoft 365 [Entwicklerabonnement.](https://aka.ms/MyVisualStudioBenefits) Es ist aktiv, solange Ihr Visual Studio Abonnement aktiv ist. Weitere Informationen finden Sie unter [Einrichten eines Microsoft 365 Entwicklerabonnements.](https://developer.microsoft.com/microsoft-365/dev-program)

1. Wechseln Sie zum [Microsoft 365-Entwicklerprogramm.](https://developer.microsoft.com/microsoft-365/dev-program)
2. Wählen Sie **"Jetzt beitreten"** aus, und folgen Sie den Anweisungen auf dem Bildschirm.
3. Wählen Sie auf der Willkommensseite **"E5-Abonnement einrichten"** aus.
4. Richten Sie Ihr Administratorkonto ein. Nach Abschluss des Vorgangs sollte der folgende Bildschirm angezeigt werden:

:::image type="content" source="./images/m365-developer-program.png" alt-text="Diagramm, das das Microsoft m365-Programm zeigt":::

## <a name="accounts-for-microsoft-365-developer-program"></a>Konten für Microsoft 365-Entwicklerprogramm

Sie können sich mit einem der folgenden Kontotypen für das Entwicklerprogramm registrieren:

- **Microsoft-Konto** 

Sie können zur persönlichen Verwendung erstellen– Bietet Zugriff auf alle verbraucherorientierten Microsoft-Produkte und Clouddienste, z. B. Outlook, Messenger, OneDrive, MSN, Xbox Live oder Microsoft 365. Durch Registrieren für ein Outlook.com-Postfach wird automatisch ein Microsoft-Konto erstellt. Nachdem ein Microsoft-Konto erstellt wurde, kann es verwendet werden, um auf Microsoft Cloud-Dienste oder Azure für Verbraucher zuzugreifen.

- **Geschäftskonto**

 Ein Administrator kann für die Geschäftsverwendung ein Problem erstellen– bietet Zugriff auf alle microsoft-Clouddienste auf Unternehmensebene, z. B. Azure, Microsoft Intune oder Microsoft 365. Wenn Sie für einen dieser Dienste als Organisation registrieren, wird automatisch ein cloudbasiertes Verzeichnis in Azure Active Directory zur Darstellung bereitgestellt, das für Ihre Organisation steht.

- **Visual Studio-ID**

Sie können für Ihre Visual Studio Professional oder Enterprise Abonnements erstellen . Es wird empfohlen, dass Sie diese Option verwenden, um am Entwicklerprogramm aus dem Visual Studio Katalog teilzunehmen, um die vorteile als Visual Studio-Abonnent in vollem Umfang zu nutzen.

## <a name="teams-customer-app-uploading-sideloading-permission-check"></a>Teams Überprüfung des Hochladens von Kunden-Apps (Querladen der Berechtigung)

> [!IMPORTANT]
> Während der Entwicklung müssen Sie Ihre App innerhalb Ihrer Teams laden, ohne sie zu verteilen. Dies wird als **Querladen** bezeichnet.

Eine der Möglichkeiten, um zu überprüfen, ob Sie über ein Teams Konto verfügen, überprüfen Sie, ob Sie Apps in Teams querladen können:

1. Wählen Sie im Teams Client in der linken Leiste **"Apps"** aus.
2. Wählen Sie **"Apps verwalten"** aus.
3. Überprüfen Sie, ob die Option **Hochladen einer benutzerdefinierten App** angezeigt wird, wie in der Abbildung dargestellt:

:::image type="content" source="./images/sideload-check.png" alt-text="Diagramm, das das Hochladen einer benutzerdefinierten App zeigt":::

Wenn Hochladen **einer benutzerdefinierten App-Option** nicht angezeigt wird, bedeutet dies, dass Sie nicht über die Berechtigung zum Querladen verfügen. Ohne Querladen-Berechtigung können Sie kein lokales/Remotedebugging ausführen. Daher ist es sehr wichtig, die Querladen-Berechtigung für Ihr Konto zu erhalten, bevor Sie ein Debuggen für Ihre Teams-App durchführen. Wenn Sie Administrator für Ihren Mandanten sind, können Sie die Einstellung für das Querladen für Ihren Mandanten/Ihre Organisation öffnen. Wenn Sie jedoch kein Administrator sind, wenden Sie sich an Ihren Mandantenadministrator, um die Berechtigung zu erhalten.

## <a name="enable-custom-app-uploading-sideloading--for-your-organization"></a>Aktivieren des benutzerdefinierten App-Uploads (Querladen) für Ihre Organisation

> [!IMPORTANT]
> Um das hochladen oder Querladen der benutzerdefinierten App für Ihren Entwicklermandanten zu aktivieren, müssen Sie der Administrator für Ihren Mandanten sein.

1. Melden Sie sich mit Ihren Administratoranmeldeinformationen bei [Microsoft 365 Admin Center](https://admin.microsoft.com/Adminportal/Home?source=applauncher#/homepage#/) an.

2. Wählen Sie **"Alle** Teams anzeigen"  >  aus.

:::image type="content" source="./images/admin-center-teams.png" alt-text="Diagramm, das Teams Admin Center zeigt":::

> [!NOTE]
> Es kann **bis zu 24 Stunden** dauern, bis die option **Teams** angezeigt wird. Sie können [Ihre benutzerdefinierte App in eine Teams Umgebung hochladen, um](/microsoftteams/upload-custom-apps) sie zu testen und zu überprüfen.

3. Navigieren Sie zu **Teams App**  >  **Setup Policies**  >  **Global**.

:::image type="content" source="./images/teams-setup-policy.png" alt-text="Diagramm, das die Einrichtungsrichtlinie für Teams":::

4. Umschalten Hochladen benutzerdefinierten Apps auf **die** Ein-Position.

:::image type="content" source="./images/turn-on-sideload.png" alt-text="Diagramm zum Aktivieren des Querladens":::

5. Wählen Sie **Speichern**. Ihr Testmandant kann das benutzerdefinierte Querladen von Apps zulassen.

:::image type="content" source="./images/save-sideload.png" alt-text="Diagramm, das die Speicheroption zeigt":::

> [!Note]
> Es kann bis zu 24 Stunden dauern, bis das Querladen aktiv ist. In der Zwischenzeit können Sie **[für Ihren Mandanten hochladen]** verwenden, um Ihre App zu testen. Informationen zum Hochladen der .zip-Paketdatei der App finden Sie unter ["Hochladen benutzerdefinierter Apps".](/microsoftteams/teams-app-setup-policies)

Weitere Informationen finden Sie unter [Verwalten von benutzerdefinierten App-Richtlinien und -Einstellungen in Teams](/microsoftteams/teams-custom-app-policies-and-settings) und Verwalten von [App-Setuprichtlinien in Teams.](/microsoftteams/teams-app-setup-policies)

## <a name="see-also"></a>Siehe auch

> [!div class="nextstepaction"]
> [Erstellen eines neuen Teams Projekts](create-new-project.md)

> [!div class="nextstepaction"]
> [Bereitstellen von Cloudressourcen](provision.md)
