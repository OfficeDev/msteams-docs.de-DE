---
title: Vorbereiten Ihres Office 365-Mandanten
description: Erste Schritte mit Microsoft Teams in Office 365
keywords: Konfigurieren des Uploads von Office 365 Mandanten Teams
ms.openlocfilehash: a246b13ae3a12a486a06ff9d98d37d4d147e4ed4
ms.sourcegitcommit: 52732714105fac07c331cd31e370a9685f45d3e1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/25/2020
ms.locfileid: "46874863"
---
# <a name="prepare-your-office-365-tenant"></a>Vorbereiten Ihres Office 365-Mandanten

Wenn Sie ein Office 365 Abonnent sind, können Sie Apps für Microsoft Teams mit einem der folgenden [Pläne](https://products.office.com/business/compare-more-office-365-for-business-plans)entwickeln:

* Business Essentials
* Business Premium
* Enterprise E1, E3 und E5
* Developer
* Education, Education Plus und Education E5

Microsoft Teams steht auch Kunden, die E4 abonniert haben, vor dem [Ruhestand](https://support.office.com//article/important-information-for-office-365-enterprise-e4-customers-f9572348-43a2-43fa-a3d8-3b6c9c042147)zur Verfügung.

## <a name="just-need-a-development-environment"></a>Sie benötigen lediglich eine Entwicklungsumgebung?

Wenn Sie derzeit kein Office 365 Konto haben, können Sie sich für ein [Microsoft 365-Entwicklerprogramm](https://developer.microsoft.com/microsoft-365/dev-program) Abonnement anmelden. Es ist für 90 Tage *kostenlos* und wird ständig erneuert, solange Sie es für Entwicklungsaktivitäten verwenden. Wenn Sie über ein Visual Studio *Enterprise* -oder *Professional* -Abonnement verfügen, enthalten beide Programme ein kostenloses Microsoft 365- [Entwickler Abonnement](https://aka.ms/MyVisualStudioBenefits), das für die Dauer Ihres Visual Studio Abonnements aktiv ist. *Weitere Informationen finden Sie unter* [Einrichten eines Microsoft 365 Developer-Abonnements](https://docs.microsoft.com/office/developer-program/office-365-developer-program-get-started).

## <a name="enable-microsoft-teams-for-your-organization"></a>Aktivieren von Microsoft Teams für Ihre Organisation 

Wenn Microsoft Teams nicht für Ihre Organisation aktiviert wurde, müssen Sie dies zunächst tun. Werfen Sie einen Blick auf unsere detaillierten Anleitungen für [die Aktivierung von Teams für Ihre Organisation](/microsoftteams/enable-features-office-365).

## <a name="enable-custom-teams-apps-and-turn-on-custom-app-uploading"></a>Aktivieren benutzerdefinierter Teams-apps und Aktivieren des benutzerdefinierten App-Uploads

Aktivieren Sie wie folgt benutzerdefinierte App-Sideloading für den Entwickler Mandanten:

1. Melden Sie sich bei [Microsoft 365 Admin Center](https://admin.microsoft.com/Adminportal/Home?source=applauncher#/homepage#/) mit Ihren Administratoranmeldeinformationen an. 

2. Wählen Sie **alle**  -->  **Teams**anzeigen aus. 

![Bild des Admin Center-Menüs](~/assets/images/prepare-test-tenant/admin-center.png)

> [!Note] 
> Es kann bis zu 24 Stunden dauern, bis die Option "Teams" angezeigt wird. Während der Zwischenzeit können Sie [Ihre benutzerdefinierte app in eine Teams-Umgebung hochladen](/microsoftteams/upload-custom-apps#validate) , um Sie zu testen und zu validieren.

3. Navigieren Sie zu **Teams**  -->  -**Setup Richtlinien**für apps  -->  **Global (organisationsweit Standard)**  

![Aktivieren der querladen-Ansicht](~/assets/images/prepare-test-tenant/turn-on-sideload.png)

4. Schalten Sie **benutzerdefinierte apps** in die Position **on** hoch.

Das ist alles. Der Testmandant lässt jetzt benutzerdefinierte App-Sideloading.

> [!Note] 
> Es kann bis zu 24 Stunden dauern, bis Sideloading aktiviert ist. Während der Zwischenzeit können Sie **Upload for \<your tenant> ** verwenden, um Ihre APP zu testen.

![Updload-App-Ansicht](~/assets/images/prepare-test-tenant/upload-for-contoso.png)

Umfassende Informationen zur Interaktion dieser Einstellungen *finden Sie unter* [Verwalten benutzerdefinierter App-Richtlinien und-Einstellungen in Microsoft Teams](https://docs.microsoft.com/microsoftteams/teams-custom-app-policies-and-settings) und [Verwalten von App-Setup Richtlinien in Microsoft Teams](https://docs.microsoft.com/microsoftteams/teams-app-setup-policies).
