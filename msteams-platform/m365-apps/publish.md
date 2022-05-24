---
title: Veröffentlichen von Microsoft Teams-Apps für Microsoft 365
description: Machen Sie Ihre Microsoft 365-fähigen Teams-Apps für Benutzer in Teams, Outlook und Office
ms.date: 05/24/2022
ms.topic: conceptual
ms.custom: m365apps
ms.localizationpriority: medium
ms.openlocfilehash: b256eb75f871425d855c0f12359015134870efc0
ms.sourcegitcommit: 1e77573e47fad51a19545949fdac1241b13052e2
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2022
ms.locfileid: "65656079"
---
# <a name="publish-teams-apps-for-microsoft-365"></a>Veröffentlichen von Microsoft Teams-Apps für Microsoft 365

Microsoft 365-aktivierte Teams-Apps werden für die Produktionsverwendung in Microsoft Teams unterstützt. Sie können diese Apps für die Vorschau von Zielgruppen verteilen, die die *Targeted Release-Versionen* von outlook.com und office.com sowie den *Betakanalbuild* von Outlook für Windows Desktop verwenden. Verteilungsoptionen und -prozesse für Microsoft 365-aktivierte Teams-Apps sind identisch mit herkömmlichen Teams-Apps.

Nach der Veröffentlichung kann Ihre App zusätzlich zum Teams Store als installierbare App aus dem Outlook- und Office-App Store ermittelt werden. Ihre App verwendet die in Teams definierten Berechtigungen für Outlook und Office. Teams Administratoren können den [Zugriff auf Teams Apps Microsoft 365](/MicrosoftTeams/manage-third-party-teams-apps) für Benutzer in ihrer Organisation verwalten.

:::image type="content" source="images/outlook-office-app-store.png" alt-text="Outlook und Office.com installieren Bildschirme für die Apps SurveyMonkey und MURAL Teams":::

## <a name="single-tenant-distribution"></a>Verteilung an einen einzelnen Mandanten

Outlook-fähigen Nachrichtenerweiterungen können auf verschiedene Weise an Test- und Produktionsmandanten verteilt werden:

### <a name="teams-client"></a>Teams-Client

Wählen Sie im Menü *"Apps*" die Option "*Apps* >  verwalten *" aus. Veröffentlichen Sie eine appSubmit* >  **an Ihre Organisation**. Dies erfordert die Genehmigung Ihres IT-Administrators.

### <a name="teams-developer-portal"></a>Teams Developer Portal

Verwenden Sie das [Teams Developer Portal](https://dev.teams.microsoft.com/), um eine App in Ihre Organisation hochzuladen und zu veröffentlichen. Dies erfordert die Genehmigung Ihres IT-Administrators. Weitere Informationen finden Sie unter [Verwalten Ihrer Apps mit dem Entwicklerportal für Microsoft Teams](../concepts/build-and-test/teams-developer-portal.md).

### <a name="microsoft-teams-admin-center"></a>‎Microsoft Teams Admin Center

Als Teams-Administrator können Sie das App-Paket für den Mandanten Ihrer Organisation aus [Teams Admin Center](https://admin.teams.microsoft.com/) hochladen und vorinstallieren. Weitere Informationen finden Sie [unter Hochladen Ihrer benutzerdefinierten Apps im Microsoft Teams Admin Center](/MicrosoftTeams/upload-custom-apps).

### <a name="microsoft-admin-center"></a>Microsoft Admin Center

Als globaler Administrator können Sie das App-Paket vom [Microsoft-Administrator](https://admin.microsoft.com/) hochladen und vorinstalliert installieren. Weitere Informationen finden Sie [unter Testen und Bereitstellen von Microsoft 365 Apps durch Partner im Portal für integrierte Apps](/microsoft-365/admin/manage/test-and-deploy-microsoft-365-apps).

## <a name="multitenant-distribution"></a>Verteilung an mehrere Mandanten

Der Übermittlungsprozess von [Microsoft AppSource](https://appsource.microsoft.com/) (Microsoft Commercial Marketplace) für Teams Apps, die für Outlook und Office aktiviert sind, entspricht herkömmlichen Teams-Apps. Der einzige Unterschied besteht darin, dass Sie Teams [App-Manifestversion 1.13](../tabs/how-to/using-teams-client-sdk.md) in Ihrem App-Paket verwenden müssen, das Unterstützung für Teams Apps bietet, die über Microsoft 365 ausgeführt werden.

> [!TIP]
> Verwenden Sie Teams Developer Portal, um [Ihr App-Paket zu überprüfen](https://dev.teams.microsoft.com/validation), um Fehler oder Warnungen zu beheben, bevor Sie es an den Teams Store (über [das Microsoft Partner Network](https://partner.microsoft.com/)) übermitteln.

Informationen zu den ersten Schritte finden [Sie unter Verteilen Ihrer Microsoft Teams-App](../concepts/deploy-and-publish/apps-publish-overview.md).
