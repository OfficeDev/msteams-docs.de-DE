---
title: Veröffentlichen von Microsoft Teams-Apps für Microsoft 365
description: Erfahren Sie, wie Sie Ihre Microsoft 365-fähigen Microsoft 365-fähigen Teams-Apps für Benutzer in Teams, Outlook und Office über die Verteilung mit einem einzigen Mandanten und mehreren Mandanten auffindbar machen.
ms.date: 10/10/2022
ms.topic: conceptual
ms.custom: m365apps
ms.localizationpriority: medium
ms.openlocfilehash: b225624970a380679b2b1a508bf3b4d2882de72e
ms.sourcegitcommit: 20070f1708422d800d7b1d84b85cbce264616ead
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/12/2022
ms.locfileid: "68537521"
---
# <a name="publish-teams-apps-for-microsoft-365"></a>Veröffentlichen von Microsoft Teams-Apps für Microsoft 365

Microsoft Teams unterstützt Microsoft 365-fähige Teams-Apps für die Produktion. Sie können diese Apps an Benutzergruppen verteilen, die die *Targeted Release* (Dev Preview)-Versionen von Outlook.com und Office.com, den *Betakanalbuild* von Outlook für Windows Desktop und den Office Current Channel (Dev Preview)-Build der Office-App für Android verwenden. Verteilungsoptionen und -prozesse für Microsoft 365-fähige Teams-Apps sind identisch mit herkömmlichen Teams-Apps.

Nachdem sie veröffentlicht wurde, kann Ihre App zusätzlich zum Teams Store als installierbare App aus den Outlook- und Office-App-Stores auffindbar sein. Ihre App verwendet die in Teams in Outlook und Office definierten Berechtigungen. Teams-Administratoren können [den Zugriff auf Teams-Apps in Microsoft 365](/MicrosoftTeams/manage-third-party-teams-apps) für Benutzer in ihrer Organisation verwalten.

:::image type="content" source="images/outlook-office-app-store.png" alt-text="Der Screenshot ist ein Beispiel für Outlook und Office.com Installationsbildschirme für die Apps SurveyMonkey und MURAL Teams.":::

## <a name="single-tenant-distribution"></a>Verteilung an einen einzelnen Mandanten

Outlook-fähige Nachrichtenerweiterungen können auf verschiedene Arten an Test- und Produktionsmandanten verteilt werden:

### <a name="teams-client"></a>Teams-Client

Wählen Sie im Menü **"Apps**" die Option "**Apps** >  verwalten **" aus. Veröffentlichen Sie eine App** > **Übermitteln Sie eine App an Ihre Organisation**. Dies erfordert die Genehmigung Ihres IT-Administrators.

### <a name="teams-developer-portal"></a>Teams-Entwicklerportal

Verwenden Sie das [Teams-Entwicklerportal](https://dev.teams.microsoft.com/) , um eine App in Ihre Organisation hochzuladen und zu veröffentlichen. Dies erfordert die Genehmigung Ihres IT-Administrators. Weitere Informationen finden Sie unter [Verwalten Ihrer Apps mit dem Entwicklerportal für Microsoft Teams](../concepts/build-and-test/teams-developer-portal.md).

### <a name="microsoft-teams-admin-center"></a>‎Microsoft Teams Admin Center

Als Teams-Administrator können Sie das App-Paket für den Mandanten Ihrer Organisation aus dem [Teams Admin Center](https://admin.teams.microsoft.com/) hochladen und vorinstallieren. Weitere Informationen finden [Sie unter Hochladen Ihrer benutzerdefinierten Apps im Microsoft Teams Admin Center](/MicrosoftTeams/upload-custom-apps).

### <a name="microsoft-admin-center"></a>Microsoft Admin Center

Als globaler Administrator können Sie das App-Paket vom [Microsoft-Administrator](https://admin.microsoft.com/) hochladen und vorinstalliert installieren. Weitere Informationen finden Sie [unter Testen und Bereitstellen von Microsoft 365 Apps durch Partner im Portal für integrierte Apps](/microsoft-365/admin/manage/test-and-deploy-microsoft-365-apps).

## <a name="multitenant-distribution"></a>Verteilung an mehrere Mandanten

Der Übermittlungsprozess des [kommerziellen Microsoft Marketplace](https://appsource.microsoft.com/) (Microsoft AppSource) für Teams-Apps, die für Outlook und Office aktiviert sind, ist identisch mit herkömmlichen Teams-Apps. Der einzige Unterschied besteht darin, dass Sie die Version [1.13](../tabs/how-to/using-teams-client-sdk.md) des Teams-App-Manifests in Ihrem App-Paket verwenden müssen, wodurch Unterstützung für Teams-Apps eingeführt wird, die in Microsoft 365 ausgeführt werden.

> [!TIP]
> Verwenden Sie das Teams-Entwicklerportal, um [Ihr App-Paket zu überprüfen](https://dev.teams.microsoft.com/validation) , um Fehler oder Warnungen vor der Übermittlung an den Teams-Store (über [das Microsoft Partner Network)](https://partner.microsoft.com/) zu beheben.

Informationen zu den ersten Schritte finden Sie unter [Verteilen Ihrer Microsoft Teams-App](../concepts/deploy-and-publish/apps-publish-overview.md).
