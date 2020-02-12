---
title: Vorbereiten des Office 365 Mandanten
description: Erste Schritte mit Microsoft Teams in Office 365
keywords: Konfigurieren des Uploads von Office 365 Mandanten Teams
ms.openlocfilehash: 634392ea3f0228aef69ff920d3b369eb49dd3965
ms.sourcegitcommit: 060b486c38b72a3e6b63b4d617b759174082a508
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/12/2020
ms.locfileid: "41953495"
---
# <a name="prepare-your-office-365-tenant"></a>Vorbereiten des Office 365 Mandanten

Wenn Sie ein Office 365 Abonnent sind, können Sie Apps für Microsoft Teams mit einem der folgenden [Pläne](https://products.office.com/business/compare-more-office-365-for-business-plans)entwickeln:

* Business Essentials
* Business Premium
* Enterprise E1, E3 und E5
* Developer
* Education, Education Plus und Education E5

Microsoft Teams steht auch Kunden, die E4 abonniert haben, vor dem [Ruhestand](https://support.office.com//article/important-information-for-office-365-enterprise-e4-customers-f9572348-43a2-43fa-a3d8-3b6c9c042147)zur Verfügung.

## <a name="just-need-a-development-environment"></a>Sie benötigen lediglich eine Entwicklungsumgebung?

Wenn Sie derzeit kein Office 365 Konto haben, können Sie sich für ein Abonnement für ein [Office 365 Entwicklerprogramm](https://dev.office.com/devprogram) registrieren. Es ist für 90 Tage *kostenlos* und wird ständig erneuert, solange Sie es für Entwicklungsaktivitäten verwenden. Wenn Sie über ein Visual Studio *Enterprise* -oder *Professional* -Abonnement verfügen, enthalten beide Programme ein kostenloses Office 365 [Entwickler Abonnement](https://aka.ms/MyVisualStudioBenefits), das für die Dauer Ihres Visual Studio Abonnements aktiv ist. *Weitere Informationen finden Sie unter* [Einrichten eines Microsoft 365 Developer-Abonnements](https://docs.microsoft.com/office/developer-program/office-365-developer-program-get-started).

## <a name="enable-microsoft-teams-for-your-organization"></a>Aktivieren von Microsoft Teams für Ihre Organisation

Wenn Microsoft Teams nicht für Ihre Organisation aktiviert wurde, müssen Sie dies zunächst tun. Werfen Sie einen Blick auf unsere detaillierten Anleitungen für [die Aktivierung von Teams für Ihre Organisation](https://docs.microsoft.com/microsoftteams/enable-features-office-365).

## <a name="enable-custom-teams-apps-and-turn-on-custom-app-uploading"></a>Aktivieren benutzerdefinierter Teams-apps und Aktivieren des benutzerdefinierten App-Uploads

> [!Note] 
> Wenn Sie die Office 365-Entwicklerplattform zum Erstellen Ihrer APP verwenden, sollten diese Einstellungen bereits so konfiguriert sein, dass Sie Ihre APP erstellen, hochladen und testen können.

Es gibt drei Einstellungen, die für die Aktivierung benutzerdefinierter apps und benutzerdefinierter App-Uploads relevant sind:

* **Die organisationsweite benutzerdefinierte app-Einstellung** => ermöglicht die**Interaktion mit benutzerdefinierten apps** => **unter – mit** dieser Einstellung können benutzerdefinierte Apps für Ihre Organisation aktiviert oder deaktiviert werden. Es muss eingeschaltet sein. 
* **Einstellung** => für die benutzerdefinierte Team-APP**ermöglicht Mitgliedern das Hochladen benutzerdefinierter apps** => **an/aus** – diese Einstellung gilt für jedes einzelne Team in Microsoft Teams. Wenn Sie Ihre APP für ein bestimmtes Team installieren möchten, muss diese für dieses Team eingeschaltet sein.
* **Benutzer benutzerdefinierte App-Richtlinie** => **Benutzer kann benutzerdefinierte apps** => Hochladen ein **/aus** -diese Einstellung steuert die Berechtigungen für einen einzelnen Benutzer. Sie müssen dies für Personen aktivieren, die benutzerdefinierte apps hochladen dürfen.

Umfassende Informationen zur Interaktion dieser Einstellungen *finden Sie unter* [Verwalten benutzerdefinierter App-Richtlinien und-Einstellungen in Microsoft Teams](https://docs.microsoft.com/microsoftteams/teams-custom-app-policies-and-settings) und [Verwalten von App-Setup Richtlinien in Microsoft Teams](https://docs.microsoft.com/microsoftteams/teams-app-setup-policies).
