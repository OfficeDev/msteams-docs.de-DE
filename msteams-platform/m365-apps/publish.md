---
title: Veröffentlichen von Microsoft Teams-Apps für Microsoft 365
description: Erfahren Sie, wie Sie Ihre Microsoft 365-fähigen Microsoft 365-fähigen Teams-Apps für Benutzer in Teams, Outlook und Office über eine Einzelmandanten- und mehrinstanzenfähige Verteilung auffindbar machen.
ms.date: 10/10/2022
ms.topic: conceptual
ms.custom: m365apps
ms.localizationpriority: medium
ms.openlocfilehash: cfe650e676252a16c1665f078938adbff0d4c7d7
ms.sourcegitcommit: 10debe0f01574a21aab54bfac692a4c8373263a8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2022
ms.locfileid: "68789884"
---
# <a name="publish-teams-apps-for-microsoft-365"></a>Veröffentlichen von Microsoft Teams-Apps für Microsoft 365

Microsoft Teams unterstützt Microsoft 365-fähige Teams-Apps für die Produktion. Sie können diese Apps an Benutzer verteilen, die die *Targeted Release* (Dev Preview)-Versionen von Outlook.com und Office.com, den *Betakanal-Build* von Outlook für Windows-Desktop und office Current Channel (Dev Preview)-Build der Office-App für Android verwenden. Verteilungsoptionen und -prozesse für Microsoft 365-fähige Teams-Apps sind die gleichen wie für herkömmliche Teams-Apps.

Nach der Veröffentlichung ist Ihre App zusätzlich zum Teams Store als installierbare App aus den Outlook- und Office-App-Stores erkennbar. Ihre App verwendet die in Teams definierten Berechtigungen in Outlook und Office. Teams-Administratoren können [den Zugriff auf Teams-Apps in Microsoft 365](/MicrosoftTeams/manage-third-party-teams-apps) für Benutzer in ihrer Organisation verwalten.

:::image type="content" source="images/outlook-office-app-store.png" alt-text="Der Screenshot ist ein Beispiel, das Outlook und Office.com Installationsbildschirme für die Apps SurveyMonkey und MURAL Teams zeigt.":::

## <a name="single-tenant-distribution"></a>Verteilung an einen einzelnen Mandanten

Outlook-fähige Nachrichtenerweiterungen können auf verschiedene Weise an Test- und Produktionsmandanten verteilt werden:

### <a name="teams-client"></a>Teams-Client

Wählen Sie im Menü **Apps** die Option **Apps** >  verwalten **App veröffentlichen** > **App an Ihre Organisation übermitteln** aus. Zum Übermitteln einer App ist die Genehmigung Ihres IT-Administrators erforderlich.

### <a name="teams-developer-portal"></a>Teams-Entwicklerportal

Verwenden Sie das [Teams-Entwicklerportal](https://dev.teams.microsoft.com/) , um eine App für Ihre Organisation hochzuladen und zu veröffentlichen. Das Hochladen und Veröffentlichen einer App erfordert die Genehmigung Ihres IT-Administrators. Weitere Informationen finden Sie unter [Verwalten Ihrer Apps mit dem Entwicklerportal für Microsoft Teams](../concepts/build-and-test/teams-developer-portal.md).

### <a name="microsoft-teams-admin-center"></a>‎Microsoft Teams Admin Center

Als Teams-Administrator können Sie das App-Paket für den Mandanten Ihrer Organisation aus dem [Teams Admin Center](https://admin.teams.microsoft.com/) hochladen und vorab installieren. Weitere Informationen finden Sie unter [Hochladen Ihrer benutzerdefinierten Apps im Microsoft Teams Admin Center](/MicrosoftTeams/upload-custom-apps).

### <a name="microsoft-admin-center"></a>Microsoft Admin Center

Als globaler Administrator können Sie das App-Paket vom [Microsoft-Administrator](https://admin.microsoft.com/) hochladen und vorinstallieren. Weitere Informationen finden Sie unter [Testen und Bereitstellen von Microsoft 365 Apps von Partnern im Portal für integrierte Apps](/microsoft-365/admin/manage/test-and-deploy-microsoft-365-apps).

## <a name="multitenant-distribution"></a>Verteilung an mehrere Mandanten

Der [Übermittlungsprozess von Microsoft AppSource](https://appsource.microsoft.com/) (Microsoft Commercial Marketplace) für Teams-Apps, die für Outlook und Office aktiviert sind, ist identisch mit herkömmlichen Teams-Apps. Der einzige Unterschied besteht darin, dass Sie version [1.13](../tabs/how-to/using-teams-client-sdk.md) des Teams-App-Manifests in Ihrem App-Paket verwenden müssen, wodurch Unterstützung für Teams-Apps eingeführt wird, die in Microsoft 365 ausgeführt werden.

> [!TIP]
> Verwenden Sie das Teams-Entwicklerportal, um [Ihr App-Paket zu überprüfen](https://dev.teams.microsoft.com/validation) , um Fehler oder Warnungen zu beheben, bevor Sie es an den Teams Store (über [Microsoft Partner Network](https://partner.microsoft.com/)) übermitteln.

Informationen zu den ersten Schritten finden [Sie unter Verteilen Ihrer Microsoft Teams-App](../concepts/deploy-and-publish/apps-publish-overview.md).
