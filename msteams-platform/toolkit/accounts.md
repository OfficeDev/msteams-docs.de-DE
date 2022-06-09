---
title: Vorbereiten von Konten zum Erstellen von Teams-Apps
author: zyxiaoyuer
description: Vorbereiten von Konten zum Erstellen von Teams-Apps
ms.author: surbhigupta
ms.localizationpriority: high
ms.topic: overview
ms.date: 03/14/2022
ms.openlocfilehash: 7e9ccfe5fd533f9502ea2de176efa8a46712524d
ms.sourcegitcommit: ff31cbe4840191f004d8fc61dd4fd93d35fcaecb
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/07/2022
ms.locfileid: "65938907"
---
# <a name="prepare-accounts-to-build-teams-apps"></a>Vorbereiten von Konten zum Erstellen von Teams-Apps

Um eine Teams-App zu erstellen und hochzuladen, müssen Sie die folgenden Konten vorbereiten:

* [Microsoft 365-Konto mit gültigem Abonnement](accounts.md#microsoft-365-account)
* [Azure-Konto zum Hosten der Back-End-Ressourcen in Azure](accounts.md#azure-account-to-host-backend-resources)

## <a name="microsoft-365-account"></a>Microsoft 365 Konto

Um ein Microsoft 365-Konto zu erstellen, registrieren Sie sich für ein Microsoft 365-Entwicklerprogramm-Abonnement. Das Abonnement ist 90 Tage lang kostenlos und wird weiterhin verlängert, solange Sie es für Entwicklungsaktivitäten verwenden.

Wenn Sie über ein Visual Studio Enterprise- oder Professional-Abonnement verfügen, enthalten beide Programme ein kostenloses Microsoft 365-[Entwicklerabonnement](https://aka.ms/MyVisualStudioBenefits). Es ist aktiv, solange Ihr Visual Studio Abonnement aktiv ist. Weitere Informationen finden Sie unter [Einrichten eines Microsoft 365 Developer-Abonnements](https://developer.microsoft.com/microsoft-365/dev-program).

### <a name="microsoft-365-developer-program"></a>Microsoft 365-Entwicklerprogramm

Um ein kostenloses Teams-Entwicklerkonto zu erhalten, treten Sie dem Microsoft 365-Entwicklerprogramm bei und führen Sie die folgenden Schritte aus:

1. Gehen Sie zu [Microsoft 365-Entwicklerprogramm](https://developer.microsoft.com/microsoft-365/dev-program).
2. Wählen Sie **Jetzt beitreten** aus.
3. Wählen Sie **E5-Abonnement einrichten** aus.
4. Einrichten Ihres Administratorkontos.

   Nach Abschluss des Abonnements wird die folgende Abbildung angezeigt:

    :::image type="content" source="./images/m365-developer-program.png" alt-text="Diagramm, das das Microsoft 365-Programm zeigt":::

### <a name="microsoft-365-developer-account-types"></a>Microsoft 365 Entwicklerkontotypen

Sie können sich für das Entwicklerprogramm registrieren, indem Sie einen der folgenden Kontotypen verwenden:

* **Microsoft-Konto für die persönliche Verwendung**

    Das Konto bietet Zugriff auf Microsoft-Produkte und Clouddienste wie Outlook, Messenger, OneDrive, MSN, Xbox Live oder Microsoft 365. Sie können sich für ein Outlook.com-Postfach registrieren, um ein Microsoft-Konto zu erstellen, das für den Zugriff auf verbraucherbezogene Microsoft-Clouddienste oder Azure verwendet werden kann.

* **Microsoft-Geschäftskonto für Unternehmen**

     Das Konto bietet Zugang zu allen Microsoft Cloud-Diensten für kleine, mittlere und große Unternehmen, wie Azure, Microsoft Intune oder Microsoft 365. Wenn Sie sich bei einem dieser Dienste als Organisation registrieren, wird automatisch ein cloudbasiertes Verzeichnis in Azure AD bereitgestellt, um Ihre Organisation darzustellen.

* **Visual Studio-Benutzer-ID**

    Die Benutzer-ID für das Visual Studio Professional- oder Enterprise-Abonnement kann verwendet werden, um dem Entwicklerprogramm innerhalb der Visual Studio Gallery beizutreten und alle Vorteile eines Visual Studio-Abonnenten zu nutzen.

## <a name="azure-account-to-host-backend-resources"></a>Azure-Konto zum Hosten von Back-End-Ressourcen

Das Azure-Konto ist optional, wenn Ihre vorhandene Anwendung auf einem anderen Cloudanbieter gehostet wird und Sie die vorhandene Anwendung auf der Teams-Plattform integrieren möchten.

**Visual Studio-ID**

Wenn Sie Ihre anwendungsbezogenen Ressourcen hosten oder auf Ressourcen in Azure zugreifen möchten, können Sie [ein kostenloses Konto erstellen](https://azure.microsoft.com/free/), bevor Sie beginnen. Alternativ können Sie Ihre Backend-Ressourcen auch bei einem anderen Cloud-Anbieter oder auf Ihren eigenen Servern hosten, wenn diese öffentlich zugänglich sind.

## <a name="upload-custom-app"></a>Hochladen einer benutzerdefinierten App

> [!IMPORTANT]
> Nachdem Sie die App erstellt haben, müssen Sie Ihre App in Teams laden, ohne sie zu verteilen. Dieser Vorgang wird als **Sideloading** bezeichnet.

   Sie können überprüfen, ob die Berechtigung zum Querladen entweder mit Visual Studio Code oder Teams Client aktiviert ist.

* **Überprüfen der Berechtigung zum Querladen mithilfe von Visual Studio Code**

    1. Öffnen Sie **Visual Studio Code**.
    2. Wählen Sie im linken Bereich **Teams Toolkit** aus. Wenn Sie die Option nicht sehen können, stellen Sie sicher, dass Sie die Teams Toolkit-Erweiterung installiert haben.
    3. Wählen Sie **Konten** aus, und melden Sie sich bei Ihrem Microsoft 365 Konto an.
    4. Überprüfen Sie, ob Sie die Option **Querladen aktiviert** anzeigen können, wie in der folgenden Abbildung dargestellt:

       :::image type="content" source="../assets/images/teams-toolkit-v2/sideloading.png" alt-text="Querladen aktivieren" border="true":::

* **Überprüfen der Berechtigung zum Querladen mithilfe von Teams Client**

    1. Öffnen Sie **Microsoft Teams**.
    2. Wählen Sie **Apps** im linken Bereich aus.
    3. Wählen Sie **In App veröffentlichen** aus.

       :::image type="content" source="../assets/images/teams-toolkit-v2/publish2.png" alt-text="Einer App veröffentlichen" border="true":::

    4. Überprüfen Sie, ob die Option **Hochladen einer benutzerdefinierten App** angezeigt wird, wie in der folgenden Abbildung dargestellt:

       :::image type="content" source="../assets/images/teams-toolkit-v2/upload2.png" alt-text="Benutzerdefinierte App hochladen" border="true":::

        Wenn Sie die Option **Benutzerdefinierte App hochladen** nicht anzeigen können, bedeutet dies, dass Sie nicht über die erforderliche Berechtigung zum Querladen verfügen.

        * Aktivieren Sie für einen Mandantenadministrator die Einstellung für das Querladen Ihres Mandanten oder Ihrer Organisation im Teams Admin Center.
        * Wenn Sie kein Mandantenadministrator sind, müssen Sie sich an Ihren Mandantenadministrator wenden, um das Querladen zu aktivieren.

* **Hochladen einer benutzerdefinierten App mithilfe des Admin Centers**

  > [!IMPORTANT]
  > Um das hochladen oder Querladen benutzerdefinierter Apps für Ihren Entwicklermandanten zu aktivieren, müssen Sie der Administrator für Ihren Mandanten sein.

  Führen Sie die folgenden Schritte aus, um die benutzerdefinierte App hochzuladen:

  1. Melden Sie sich beim [Microsoft 365 Admin Center](https://admin.microsoft.com/Adminportal/Home?source=applauncher#/homepage#/) mit Ihren Admin-Zugangsdaten an.

  2. Wählen Sie **Alle anzeigen** > **Teams** aus.

     :::image type="content" source="../assets/images/teams-toolkit-v2/5.png" alt-text="Alle anzeigen" border="true":::

     > [!Note]
     > Es kann **bis zu 24 Stunden dauern,** bis die Option **Teams** angezeigt wird. Sie können [Ihre benutzerdefinierte App zu Test- und Validierungszwecken in eine Teams-Umgebung](/microsoftteams/upload-custom-apps) hochladen.

  3. Wechseln Sie zu **Teams-Apps** > **Setuprichtlinien**.

     :::image type="content" source="../assets/images/teams-toolkit-v2/3.png" alt-text="Festlegen von Richtlinien":::

  4. Stellen Sie die Umschaltfläche **Benutzerdefinierte Apps hochladen** auf die Position **Ein**.

     :::image type="content" source="../assets/images/teams-toolkit-v2/4.png" alt-text="Umschaltfläche":::

  5. Wählen Sie **Speichern**.

     > [!Note]
     > Es kann bis zu 24 Stunden dauern, bis das Querladen aktiv wird. In der Zwischenzeit können Sie **Upload für Ihren Mandanten** verwenden, um Ihre App zu testen. Informationen zum Hochladen der .zip-Paketdatei der App finden Sie unter [Hochladen benutzerdefinierten Apps](/microsoftteams/teams-app-setup-policies).

Weitere Informationen finden Sie unter [Verwalten von benutzerdefinierten App-Richtlinien und -Einstellungen in Teams](/microsoftteams/teams-custom-app-policies-and-settings) und [Verwalten von App-Setuprichtlinien in Teams](/microsoftteams/teams-app-setup-policies).

## <a name="see-also"></a>Siehe auch

* [Erstellen einer neuen Teams-App mit Teams Toolkit](create-new-project.md)
* [Bereitstellen von Cloudressourcen](provision.md)
* [Bereitstellen der Teams-App in der Cloud](deploy.md)
* [Veröffentlichen Ihrer Teams-App](../concepts/deploy-and-publish/appsource/publish.md)
* [Verwalten mehrerer Umgebungen](TeamsFx-multi-env.md)
