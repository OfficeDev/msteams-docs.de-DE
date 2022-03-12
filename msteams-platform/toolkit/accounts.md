---
title: Vorbereiten von Konten zum Erstellen Teams Apps
author: zyxiaoyuer
description: Vorbereiten von Konten zum Erstellen Teams Apps
ms.author: zhany
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: 9dbfa97b892f2234b53eb42b5d5764b8f6fd6e93
ms.sourcegitcommit: 8a0ffd21c800eecfcd6d1b5c4abd8c107fcf3d33
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2022
ms.locfileid: "63452571"
---
# <a name="prepare-accounts-to-build-teams-apps"></a>Vorbereiten von Konten zum Erstellen Teams Apps

Zum Entwickeln Teams App benötigen Sie mindestens ein Microsoft 365 Konto mit gültigem Abonnement. Wenn Sie Ihre Back-End-Ressourcen in Azure hosten möchten, benötigen Sie ein Azure-Konto. Das Azure-Konto ist optional, wenn Ihre vorhandene Anwendung auf einem anderen Cloudanbieter gehostet wird und Sie die vorhandene Anwendung in Teams Plattform integrieren möchten.

## <a name="microsoft-365-account"></a>Microsoft 365 Konto

Wenn Sie über kein vorhandenes Microsoft 365 Konto mit einem gültigen Abonnement verfügen, können Sie ein Konto erstellen, indem Sie dem [Microsoft 365 Entwicklerprogramm](https://developer.microsoft.com/microsoft-365/dev-program) beitreten. Das Microsoft 365-Entwicklerprogramm enthält ein Microsoft 365 E5 Entwicklerabonnement, mit dem Sie Ihre eigene Sandbox erstellen und unabhängig von Ihrer Produktionsumgebung Lösungen entwickeln können.

## <a name="azure-account"></a>Azure-Konto

Wenn Sie Ihre App-bezogenen Ressourcen hosten oder auf Ressourcen in Azure zugreifen möchten, benötigen Sie ein Azure-Abonnement. Sie können [ein kostenloses Konto erstellen](https://azure.microsoft.com/free/) , bevor Sie beginnen.

## <a name="join-microsoft-365-developer-program"></a>Teilnehmen am Microsoft 365-Entwicklerprogramm

Wenn Sie über kein Microsoft 365 Konto verfügen, müssen Sie sich für ein [Abonnement für ein Microsoft 365 Entwicklerprogramm](https://developer.microsoft.com/microsoft-365/dev-program) registrieren. Das Abonnement ist 90 Tage lang kostenlos und wird weiterhin verlängert, solange Sie es für Entwicklungsaktivitäten verwenden. Wenn Sie über ein Visual Studio Enterprise- oder Professional-Abonnement verfügen, enthalten beide Programme ein kostenloses Microsoft 365 [Entwicklerabonnement](https://aka.ms/MyVisualStudioBenefits). Es ist aktiv, solange Ihr Visual Studio Abonnement aktiv ist. Weitere Informationen finden Sie unter [Einrichten eines Microsoft 365 Entwicklerabonnements](https://developer.microsoft.com/microsoft-365/dev-program).

1. Wechseln Sie zum [Microsoft 365-Entwicklerprogramm](https://developer.microsoft.com/microsoft-365/dev-program).
2. Wählen Sie **"Jetzt beitreten" aus**.
3. Wählen Sie **"E5-Abonnement einrichten**" aus.
4. Richten Sie Ihr Administratorkonto ein. Nach Abschluss des Vorgangs sollte der folgende Bildschirm angezeigt werden:

:::image type="content" source="./images/m365-developer-program.png" alt-text="Diagramm, das Microsoft 365-Programm zeigt":::

## <a name="accounts-for-microsoft-365-developer-program"></a>Konten für Microsoft 365-Entwicklerprogramm

Sie können sich mit einem der folgenden Kontotypen für das Entwicklerprogramm registrieren:

* **Microsoft-Konto für die persönliche Verwendung**

  Bietet Zugriff auf alle verbraucherorientierten Microsoft-Produkte und Clouddienste, z. B. Outlook, Messenger, OneDrive, MSN, Xbox Live oder Microsoft 365. Durch Registrieren für ein Outlook.com-Postfach wird automatisch ein Microsoft-Konto erstellt. Nachdem ein Microsoft-Konto erstellt wurde, kann es verwendet werden, um auf Microsoft Cloud-Dienste oder Azure für Verbraucher zuzugreifen.

* **Geschäftskonto**

  Bietet Zugriff auf alle kleinen, mittleren und geschäftlichen Microsoft-Clouddienste auf Unternehmensebene, z. B. Azure, Microsoft Intune oder Microsoft 365. Wenn Sie sich bei einem dieser Dienste als Organisation registrieren, wird automatisch ein cloudbasiertes Verzeichnis in Microsoft Azure Active Directory (Azure AD) bereitgestellt, um Ihre Organisation darzustellen.

* **Visual Studio-ID**

  Sie können für Ihre Visual Studio Professional oder Enterprise Abonnements erstellen . Es wird empfohlen, dass Sie diese Option verwenden, um am Entwicklerprogramm aus dem Visual Studio Katalog teilzunehmen, um die vorteile als Visual Studio-Abonnent in vollem Umfang zu nutzen.

## <a name="teams-customer-app-upload-or-sideload-permission"></a>Teams Berechtigung zum Hochladen oder Querladen von Kunden-Apps

> [!IMPORTANT]
> Während der Entwicklung müssen Sie Ihre App innerhalb Ihrer Teams laden, ohne sie zu verteilen. Dies wird als **Querladen** bezeichnet.

Die folgende Liste enthält Schritte, um zu überprüfen, ob das Querladen der App-Berechtigung aktiviert ist. Es gibt zwei verschiedene Möglichkeiten:

* **So verwenden Sie Microsoft Visual Studio-Code**

    1. Öffnen **Sie Visual Studio Code**.
    1. Wählen Sie im linken Bereich **Teams Toolkit** aus.
    1. Wählen Sie **"Konten"** aus, und melden Sie sich bei Ihrem Microsoft 365 Konto an.
    1. Überprüfen Sie, ob die Option **"Querladen" wie** in der Abbildung dargestellt aktiviert angezeigt wird:

       :::image type="content" source="../assets/images/teams-toolkit-v2/sideloading.png" alt-text="Aktivieren des Querladens":::

* **So verwenden Sie Teams Konto**

    1. Öffnen **Sie Microsoft Teams**.
    2. Wählen Sie **"Apps"** in der linken Leiste aus.
    3. Wählen Sie **"App veröffentlichen" aus**.

       :::image type="content" source="../assets/images/teams-toolkit-v2/publish.png" alt-text="Einer App veröffentlichen":::

    4. Überprüfen Sie, ob die Option **Hochladen einer benutzerdefinierten App** angezeigt wird, wie in der Abbildung dargestellt:

       :::image type="content" source="../assets/images/teams-toolkit-v2/upload.png" alt-text="Hochladen einer benutzerdefinierten App":::

Wenn **Hochladen einer benutzerdefinierten App-Option** nicht angezeigt wird, bedeutet dies, dass Sie nicht über die Berechtigung zum Querladen verfügen. Ohne Querladen-Berechtigung können Sie kein lokales oder Remotedebugging ausführen. Daher ist es sehr wichtig, die Querladen-Berechtigung für Ihr Konto zu erhalten, bevor Sie ein Debuggen für Ihre Teams-App durchführen. Wenn Sie Administrator für Ihren Mandanten sind, können Sie die Einstellung für das Querladen für Ihren Mandanten oder Ihre Organisation öffnen. Wenn Sie kein Administrator sind, wenden Sie sich an Ihren Mandantenadministrator, um die Berechtigung zu erhalten.

## <a name="enable-custom-app-uploading-for-your-organization"></a>Aktivieren des hochladens von benutzerdefinierten Apps für Ihre Organisation

> [!IMPORTANT]
> Um das hochladen oder Querladen der benutzerdefinierten App für Ihren Entwicklermandanten zu aktivieren, müssen Sie der Administrator für Ihren Mandanten sein.

1. Melden Sie sich mit Ihren Administratoranmeldeinformationen bei [Microsoft 365 Admin Center](https://admin.microsoft.com/Adminportal/Home?source=applauncher#/homepage#/) an.

2. Wählen Sie **"Alle** >  anzeigen **Teams** aus.

   :::image type="content" source="../assets/images/teams-toolkit-v2/5.png" alt-text="Alle anzeigen":::

> [!NOTE]
> Es kann **bis zu 24 Stunden** dauern, bis die **Option Teams** angezeigt wird. Sie können [Ihre benutzerdefinierte App in eine Teams Umgebung hochladen, um](/microsoftteams/upload-custom-apps) sie zu testen und zu überprüfen.

3. Navigieren Sie zu **Teams appsSetup** >  **PoliciesGlobal** > .

   :::image type="content" source="../assets/images/teams-toolkit-v2/3.png" alt-text="Festlegen von Olicies":::

4. Umschalten Hochladen benutzerdefinierten Apps **auf die** Ein-Position.

   :::image type="content" source="../assets/images/teams-toolkit-v2/4.png" alt-text="Umschalten":::

5. Wählen Sie **Speichern**.

> [!Note]
> Es kann bis zu 24 Stunden dauern, bis das Querladen aktiv ist. In der Zwischenzeit können Sie **upload für Ihren Mandanten** verwenden, um Ihre App zu testen. Informationen zum Hochladen der .zip-Paketdatei der App finden Sie unter ["Hochladen benutzerdefinierter Apps"](/microsoftteams/teams-app-setup-policies).

Weitere Informationen finden Sie unter [Verwalten von benutzerdefinierten App-Richtlinien und -Einstellungen in Teams](/microsoftteams/teams-custom-app-policies-and-settings) und [Verwalten von App-Setuprichtlinien in Teams](/microsoftteams/teams-app-setup-policies).

## <a name="see-also"></a>Siehe auch

* [Erstellen eines neuen Teams Projekts](create-new-project.md)
* [Bereitstellen von Cloudressourcen](provision.md)
