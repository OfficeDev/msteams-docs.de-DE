---
title: Voraussetzungen für das Erstellen Ihrer Teams-App mit Visual Studio Code
author: zyxiaoyuer
description: In diesem Modul lernen Sie die Voraussetzungen kennen, die für Tools und SDK erforderlich sind.
ms.author: surbhigupta
ms.localizationpriority: high
ms.topic: overview
ms.date: 03/14/2022
ms.openlocfilehash: 412b7bfedb6ba39f1d38f42aac56cc793ea385b1
ms.sourcegitcommit: ed7488415f814d0f60faa15ee8ec3d64ee336380
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/07/2022
ms.locfileid: "67617152"
---
# <a name="prerequisites-for-creating-your-teams-app"></a>Voraussetzungen für das Erstellen Ihrer Teams-App

Stellen Sie sicher, dass die folgenden Voraussetzungen erfüllt sind, bevor Sie mit dem Erstellen Ihrer Teams-App beginnen:

* [Grundlegende Anforderungen zum Erstellen Ihrer Teams-App](#basic-requirements-to-build-your-teams-app)
* [Vorbereiten von Konten zum Erstellen Ihrer Teams-App](#accounts-to-build-your-teams-app)
* [Querladen-Berechtigung](#sideloading-permission)

## <a name="basic-requirements-to-build-your-teams-app"></a>Grundlegende Anforderungen zum Erstellen Ihrer Teams-App

Stellen Sie sicher, dass die folgenden Anforderungen erfüllt sind, bevor Sie mit dem Erstellen Ihrer Teams-App beginnen:

| &nbsp; | Grundlegende Anforderungen | Für die Verwendung| Für Den Umgebungstyp|
   | --- | --- | --- |
   | **Erforderlich** | &nbsp; | &nbsp; | &nbsp; |
   | &nbsp; | Teams Toolkit| Eine Microsoft Visual Studio Code-Erweiterung, die ein Projektgerüst für Ihre App erstellt. Verwenden Sie die neueste Version. | JavaScript und SPFx|
   | &nbsp; | [Microsoft Teams](https://www.microsoft.com/microsoft-teams/download-app) | Arbeiten Sie mit allen Personen zusammen, mit denen Sie über Apps für Chats, Besprechungen und Anrufe zusammenarbeiten – alles an einem zentralen Ort.| JavaScript und SPFx|
   | &nbsp; | [Node.js](https://nodejs.org/en/download/) | Back-End-JavaScript-Laufzeitumgebung. Verwenden Sie die neueste Version von v16 LTS.| JavaScript und SPFx|
   | &nbsp; |[Node Package Manager (NPM)](https://www.npmjs.com/package/@microsoft/teamsfx) | Installieren und verwalten Sie Pakete für die Verwendung in Node.js- und ASP.NET Core-Anwendungen.| JavaScript und SPFx|
   | &nbsp; | [Microsoft&nbsp; Edge](https://www.microsoft.com/edge) (empfohlen) oder [Google Chrome](https://www.google.com/chrome/) | Ein Browser mit Entwicklertools. | JavaScript und SPFx|
   | &nbsp; | [Visual Studio Code](https://code.visualstudio.com/download) | Build-Umgebungen für JavaScript, TypeScript oder SharePoint Framework (SPFx). Verwenden Sie Version 1.55 oder höher. | JavaScript und SPFx|
   | **Optional** | &nbsp; | &nbsp; | &nbsp; |
   | &nbsp; | [Azure-Tools für Visual Studio Code](https://marketplace.visualstudio.com/items?itemName=ms-vscode.vscode-node-azure-pack) und [Azure CLI](/cli/azure/install-azure-cli) | Greifen Sie auf gespeicherte Daten zu, oder stellen Sie ein cloudbasiertes Back-End für Ihre Teams-App in Azure bereit. | JavaScript|
   | &nbsp; | [React Developer Tools für Chrome](https://chrome.google.com/webstore/detail/react-developer-tools/fmkadmapgofadopljbjfkapdkoienihi) ODER [React Developer Tools für Microsoft&nbsp;Edge](https://microsoftedge.microsoft.com/addons/detail/react-developer-tools/gpphkfbcpidddadnkolkpfckpihlkkil) | Eine Browser-DevTools-Erweiterung für die Open Source-React JavaScript-Bibliothek. | JavaScript|
   | &nbsp; | [Microsoft Graph-Tester](https://developer.microsoft.com/graph/graph-explorer) | Ein browserbasiertes Tool, mit dem Sie eine Abfrage aus Microsoft Graph-Daten ausführen können. | JavaScript und SPFx|
   | &nbsp; | [Entwicklerportal für Teams](https://dev.teams.microsoft.com/) | Webbasiertes Portal zum Konfigurieren, Verwalten und Verteilen Ihrer Teams-App, einschließlich an Ihre Organisation oder den Teams-Store.| JavaScript und SPFx|

   > [!NOTE]
   >
   > * Das Dokument wird mit Teams Toolkit Version 4.0.0 und Nodejs Version 16 getestet.
   > * Erstellen Sie ein Lesezeichen für den Microsoft Graph-Explorer, um mehr über Microsoft Graph-Dienste zu erfahren. Mit diesem browserbasierten Tool können Sie Microsoft Graph außerhalb einer App abfragen und darauf zugreifen.

## <a name="accounts-to-build-your-teams-app"></a>Konten zum Erstellen Ihrer Teams-App

Stellen Sie sicher, dass Sie über die folgenden Konten verfügen, bevor Sie mit dem Erstellen Ihrer Teams-App beginnen:

| Konten | Für die Verwendung| Für Den Umgebungstyp|
| --- | --- |
|[Microsoft 365-Konto mit gültigem Abonnement](#microsoft-365-developer-program)|Teams-Entwicklerkonto beim Entwickeln einer App.| JavaScript und SPFx|
|[Azure-Konto](accounts.md#azure-account-to-host-backend-resources)|Back-End-Ressourcen in Azure.| JavaScript und SPFx|
|[Administratorkonto der SharePoint-Sammlungswebsite](#sharepoint-collection-site-administrator-account) |Bereitstellung für Hosting.| SPFx|

### <a name="microsoft-365-developer-program"></a>Microsoft 365-Entwicklerprogramm

Um ein Microsoft 365-Konto zu erstellen, registrieren Sie sich für ein Microsoft 365-Entwicklerprogramm-Abonnement. Das Abonnement ist 90 Tage lang kostenlos und wird weiterhin verlängert, solange Sie es für Entwicklungsaktivitäten verwenden.

Wenn Sie über ein Visual Studio Enterprise- oder Professional-Abonnement verfügen, enthalten beide Programme ein kostenloses Microsoft 365-[Entwicklerabonnement](https://aka.ms/MyVisualStudioBenefits). Es ist aktiv, solange Ihr Visual Studio Abonnement aktiv ist. Weitere Informationen finden Sie unter [Einrichten eines Microsoft 365 Developer-Abonnements](https://developer.microsoft.com/microsoft-365/dev-program).

Sie können sich für das Entwicklerprogramm registrieren, indem Sie einen der folgenden Kontotypen verwenden:

* **Microsoft-Konto für die persönliche Verwendung**

  :::row:::

    :::column span="3":::

       Das Konto bietet Zugriff auf Microsoft-Produkte und Clouddienste wie Outlook, Messenger, OneDrive, MSN, Xbox Live oder Microsoft 365. 

       Sie können sich für ein Outlook.com-Postfach registrieren, um ein Microsoft-Konto zu erstellen, das für den Zugriff auf verbraucherbezogene Microsoft-Clouddienste oder Azure verwendet werden kann.

    :::column-end:::
    :::column span="1":::
             :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/personal-account-icon.png" alt-text="persönliches Konto.":::
   :::column-end:::

  :::row-end:::

* **Microsoft-Geschäftskonto für Unternehmen**

  :::row:::

    :::column span="3":::

       Das Konto bietet Zugriff auf alle kleinen, mittleren und unternehmensspezifischen Microsoft-Clouddienste. Zu den Diensten gehören Azure, Microsoft Intune oder Microsoft 365. 

       Wenn Sie sich bei einem dieser Dienste als Organisation registrieren, wird automatisch ein cloudbasiertes Verzeichnis in Azure AD bereitgestellt, um Ihre Organisation darzustellen.

    :::column-end:::
    :::column span="1":::
             :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/work-account-icon.png" alt-text="Geschäftskonto.":::
    :::column-end:::

  :::row-end:::

#### <a name="create-a-free-microsoft-365-developer-account"></a>Erstellen eines kostenlosen Microsoft 365-Entwicklerkontos

Um ein kostenloses Microsoft 365-Entwicklerkonto zu erstellen, treten Sie dem Microsoft 365-Entwicklerprogramm bei, und führen Sie das folgende Konto aus:

1. Gehen Sie zu [Microsoft 365-Entwicklerprogramm](https://developer.microsoft.com/microsoft-365/dev-program).
1. Wählen Sie **Jetzt beitreten** aus.
1. Einrichten Ihres Administratorkontos.

   Nach Abschluss des Abonnements wird die folgende Abbildung angezeigt:

    :::image type="content" source="../assets/images/teams-toolkit-v2/m365-account.png" alt-text="M365-Konto":::

### <a name="azure-account"></a>Azure-Konto

Sie benötigen ein Azure-Konto zum Hosten einer Teams-App oder der Back-End-Ressourcen für Ihre Teams-App mithilfe des Teams-Toolkits in Visual Studio Code. In den folgenden Szenarien müssen Sie ein Azure-Abonnement benötigen:

* Wenn Sie bereits über eine App auf einem anderen Cloudanbieter als Azure verfügen und die App auf der Teams-Plattform integrieren möchten, müssen Sie über ein Azure-Abonnement verfügen.
* Sie können ein Azure-Abonnement auswählen, um Ihre Back-End-Ressourcen mit einem anderen Cloudanbieter oder auf Ihren eigenen Servern zu hosten, wenn sie über die öffentliche Domäne verfügbar sind.

> [!NOTE]
> Sie müssen [ein kostenloses Konto erstellen](https://azure.microsoft.com/free/) , bevor Sie beginnen.

### <a name="sharepoint-collection-site-administrator-account"></a>Administratorkonto der SharePoint-Sammlungswebsite

Beim Erstellen von Teams-Apps mithilfe der SPFx-Umgebung benötigen Sie das SharePoint-Websiteadministratorkonto bei der Bereitstellung für das Hosting. Wenn Sie einen Mandanten für ein Microsoft 365-Entwicklerprogramm verwenden, können Sie das Administratorkonto verwenden, das Sie zu diesem Zeitpunkt erstellt haben.

## <a name="sideloading-permission"></a>Querladen-Berechtigung

Nachdem Sie die App erstellt haben, müssen Sie ihre App in Teams laden, ohne sie zu verteilen. Dieser Vorgang wird als Querladen bezeichnet. Melden Sie sich bei Ihrem Microsoft 365-Konto an, um diese Option anzuzeigen.

Sie können überprüfen, ob die Berechtigung zum Querladen entweder mit Visual Studio Code oder Teams Client aktiviert ist.

<br>
<details>
<summary><b>Überprüfen der Berechtigung zum Querladen mithilfe von Visual Studio Code</b></summary>

1. Öffnen Sie **Visual Studio Code**.
1. Wählen Sie das Symbol "Teams-Toolkit :::image type="icon" source="../assets/images/teams-toolkit-v2/teams-toolkit-sidebar-icon.PNG"::: " auf der Symbolleiste des Teams-Toolkits aus.

   > [!NOTE]
   > Wenn die Option nicht angezeigt werden kann, lesen [Sie "Installieren des Teams-Toolkits](install-Teams-Toolkit.md) ", um die Erweiterung des Teams-Toolkits in Visual Studio Code zu installieren.
1. Wählen Sie " **Bei M365** anmelden" unter **"KONTEN"** aus, und melden Sie sich bei Ihrem Microsoft 365-Konto an.

    :::image type="content" source="../assets/images/teams-toolkit-v2/accounts.png" alt-text="Kontodetails":::

1. Überprüfen Sie, ob Sie die Option **Querladen aktiviert** anzeigen können, wie in der folgenden Abbildung dargestellt:

    :::image type="content" source="../assets/images/teams-toolkit-v2/sideloading.png" alt-text="Querladen aktivieren":::

</details>
<br>
<details>
<summary><b>Überprüfen der Berechtigung zum Querladen mithilfe von Teams Client</b></summary>

1. Wählen Sie im Teams-Client **"Apps**" aus.
1. Wählen Sie **"App verwalten"** aus.
1. Wählen Sie **"App hochladen**" aus.

    :::image type="content" source="../assets/images/teams-toolkit-v2/upload-app.png" alt-text="Einer App veröffentlichen":::

4. Überprüfen Sie, ob die Option **Hochladen einer benutzerdefinierten App** angezeigt wird, wie in der folgenden Abbildung dargestellt:

    :::image type="content" source="../assets/images/teams-toolkit-v2/upload-custom-app1.png" alt-text="Benutzerdefinierte App hochladen":::

</details>

### <a name="enable-sideloading-using-admin-center"></a>Aktivieren des Querladens mithilfe des Admin Centers

Wenn Sie die Option " **Benutzerdefinierte App hochladen** " nicht anzeigen können, wird angezeigt, dass Sie nicht über die erforderliche Berechtigung zum Querladen verfügen.

* Aktivieren Sie für einen Mandantenadministrator die Einstellung für das Querladen Ihres Mandanten oder Ihrer Organisation im Teams Admin Center.
* Wenn Sie kein Mandantenadministrator sind, müssen Sie sich an Ihren Mandantenadministrator wenden, um das Querladen zu aktivieren.

Wenn Sie über Administratorrechte verfügen, führen Sie die folgenden Schritte aus, um die benutzerdefinierte App mithilfe des Admin Centers hochzuladen:

  1. Melden Sie sich beim [Microsoft 365 Admin Center](https://admin.microsoft.com/Adminportal/Home?source=applauncher#/homepage#/) mit Ihren Admin-Zugangsdaten an.

  1. Wählen Sie das :::image type="icon" source="../assets/images/teams-toolkit-v2/showall icon.PNG"::: Symbol > **Teams** aus.

       :::image type="content" source="../assets/images/teams-toolkit-v2/m365-admin-center.png" alt-text="Microsoft 365 Admin Mitte":::

     > [!Note]
     > Es kann **bis zu 24 Stunden dauern,** bis die Option **Teams** angezeigt wird. Sie können [Ihre benutzerdefinierte App zu Test- und Validierungszwecken in eine Teams-Umgebung](/microsoftteams/upload-custom-apps) hochladen.

  1. Melden Sie sich mit Ihren Administratoranmeldeinformationen beim Microsoft Teams Admin Center an.
  1. Wählen Sie das :::image type="icon" source="../assets/images/teams-toolkit-v2/showall icon.PNG"::: Symbol >**Setuprichtlinien** für **Teams-Apps** >  aus.

     :::image type="content" source="../assets/images/teams-toolkit-v2/m365-admin-center1.png" alt-text="Microsoft 365 Admin Mitte1":::

  1. **Global auswählen (organisationsweite Standardeinstellung)**

     :::image type="content" source="../assets/images/teams-toolkit-v2/select-manage-policies.png" alt-text="Wählen Sie &quot;Richtlinien verwalten&quot; aus.":::

  1. Stellen Sie die Umschaltfläche **Benutzerdefinierte Apps hochladen** auf die Position **Ein**.

     :::image type="content" source="../assets/images/teams-toolkit-v2/Upload-custom-apps.png" alt-text="Benutzerdefinierte Apps hochladen":::

  5. Wählen Sie **Speichern**.

     > [!Note]
     > Es kann bis zu 24 Stunden dauern, bis das Querladen aktiv wird. In der Zwischenzeit können Sie **Upload für Ihren Mandanten** verwenden, um Ihre App zu testen. Informationen zum Hochladen der .zip-Paketdatei der App finden Sie unter [Hochladen benutzerdefinierten Apps](/microsoftteams/teams-app-setup-policies).

     Stellen Sie sicher, dass Sie jetzt über die Querladen-Berechtigung verfügen, indem Sie die in der [Überprüfung der Querladenberechtigung mit Visual Studio Code oder dem Teams-Client erwähnten Schritte verwenden.](#sideloading-permission)

</details>

## <a name="see-also"></a>Siehe auch

* [Verwalten von benutzerdefinierten App-Richtlinien und Einstellungen in Teams](/microsoftteams/teams-custom-app-policies-and-settings)
* [Verwalten von App-Setuprichtlinien in Teams](/microsoftteams/teams-app-setup-policies)
* [Hochladen benutzerdefinierter Apps](/microsoftteams/teams-app-setup-policies)
* [Bereitstellen von Cloudressourcen mithilfe des Teams-Toolkits](provision.md)
* [Bereitstellen der Teams-App in der Cloud](deploy.md)
