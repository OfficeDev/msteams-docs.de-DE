---
title: Verteilen Ihrer App
description: Beschreibt die drei Optionen für die Verteilung Ihrer App.
ms.topic: conceptual
localization_priority: Normal
keywords: teams publish store office distribute AppSource sideload upload app
ms.openlocfilehash: a033b90be436fbf20ef11fe95059d04388cefdf8
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020779"
---
# <a name="distribute-your-microsoft-teams-app"></a>Verteilen Ihrer Microsoft Teams-App

Nachdem Sie Ihre App erstellt haben, gibt es drei Optionen für die Verteilung:

1. [Laden Sie Ihre App direkt hoch.](#upload-your-app-directly)
2. [Veröffentlichen Sie Ihre App im App-Katalog Ihrer Organisation.](#publish-to-your-organizations-app-catalog)
3. [Veröffentlichen Sie Ihre App über AppSource](#publish-to-appsource).

## <a name="enterprise-organizations"></a>Unternehmensorganisationen

### <a name="upload-your-app-directly"></a>Laden Sie Ihre App direkt hoch

Dies ist die einfachste Möglichkeit, Ihre App zu testen und zu verwenden. Wenn Sie der Teambesitzer sind und/oder benutzerdefinierte Apps hochladen aktiviert [ist,](/microsoftteams/admin-settings)können Sie die App direkt hochladen [(oder querladen)](./apps-upload.md) und sofort mit der Verwendung beginnen. Wenn Sie die App jedoch für andere freigeben möchten, müssen Sie ihnen Ihr App-Paket senden und sie bitten, es unabhängig hochzuladen.

Wenn Sie Ihre App breiter verteilen möchten, bietet Teams einen In-App-Katalog für Benutzer, um qualitativ hochwertige Teams-Apps zu finden oder zu entdecken. Damit Ihre Lösung im Katalog verfügbar ist, müssen Sie entweder [im](#publish-to-your-organizations-app-catalog) App-Katalog Ihrer Organisation veröffentlichen oder [in AppSource veröffentlichen.](./appsource/publish.md)

### <a name="publish-to-your-organizations-app-catalog"></a>Veröffentlichen im App-Katalog Ihrer Organisation

Der App-Katalog Ihrer Organisation enthält Apps, die für Ihre Organisation einzigartig sind und vollständig unter der Kontrolle Ihrer Organisation sind. Weitere Informationen finden Sie im Artikel Veröffentlichen von [*Apps im App-Katalog Ihrer Organisation.*](/microsoftteams/tenant-apps-catalog-teams) Dieses Feature kann nur von Teams-Benutzern mit Microsoft Office 365 Mandantenadministratorberechtigungen verwaltet werden.

### <a name="publish-to-appsource"></a>Veröffentlichen in AppSource

AppSource (früher als Office Store bezeichnet) bietet Ihnen einen bequemen Ort zum Verteilen Ihrer Microsoft Teams-App sowie anderer Office 365-Erweiterbarkeitstypen wie Office-Add-Ins und SharePoint-Add-Ins. Befolgen Sie unsere Richtlinien, [um Ihre App an AppSource zu übermitteln.](./appsource/publish.md)

## <a name="government-community-cloud-gcc-organizations"></a>Organisationen der Government Community Cloud (GCC)

### <a name="upload-your-custom-app-directly-to-teams"></a>Hochladen Ihrer benutzerdefinierten App direkt in Teams

 Als GCC-Mandantenadministrator entscheiden Sie, ob Sie eine benutzerdefinierte App in Ihre Mandantenumgebung hochladen und ob sie in Ihrem Mandanten-App-Katalog veröffentlicht werden soll. Microsoft besitzt oder kontrolliert ihre benutzerdefinierten Anwendungen nicht, daher müssen Sie sicherstellen, dass alle Endpunkte den Anforderungen Ihrer Organisation entsprechen. Wenn die App-Lösung außerdem eine Bot- oder Nachrichtenerweiterung enthält, müssen Sie die [Bot Framework-Registrierung](https://dev.botframework.com/) wie folgt abschließen:

1. Wählen Sie auf der Seite Mit **Kanälen** verbinden unter **Hinzufügen eines empfohlenen Kanals** **Teams aus.**
1. Navigieren Sie zur **Seite MSTeams konfigurieren** *(siehe* unten).
1. Wählen **Sie unter Messaging** das **Optionsfeld Microsoft Teams for Government Customers** aus.
1. Wählen Sie in der unteren linken Ecke der Seite Speichern **aus.**  

>[!IMPORTANT]
> Sie können die kommerzielle Konfiguration von Teams nicht zum Hochladen/Querladen Ihrer benutzerdefinierten App in eine GCC-Umgebung verwenden. Sie müssen das Optionsfeld **Microsoft Teams for Government Customers** für eine GCC-kompatible Konfiguration auswählen.

![Seite für die Messagingkonfiguration von Teams](../../assets/images/gcc-configure.png)

> [!NOTE]
>
> * Die oben dargestellten Uploadanweisungen für GCC-Umgebungen gelten für benutzerdefinierte Teams-Apps. </br>
> * Kompatible Microsoft-Apps sind in der GCC-Umgebung standardmäßig in Teams aktiviert.
> * Drittanbieter-Apps sind auf Mandantenebene deaktiviert und sollten über die App-Berechtigungsrichtlinien Ihrer Organisation [verwaltet werden.](/microsoftteams/teams-app-permission-policies) Stellen Sie sicher, dass Sie alle Drittanbieter-Apps überprüfen, um sicherzustellen, dass sie mit den Richtlinien und Verfahren Ihrer Organisation in Einklang stehen.

> [!TIP]
>
> Microsoft 365-Entwicklerpartner stellen Über das [Microsoft 365 App Certification Program](/microsoft-365-app-certification/overview)Sicherheits-, Datenverarbeitungs- und Compliancedetails für ihre Drittanbieter-Teams-Apps zur Verfügung. *Siehe auch* [Microsoft Teams App Certification](/microsoftteams/platform/concepts/deploy-and-publish/appsource/post-publish/application-certification).
</br></br>
