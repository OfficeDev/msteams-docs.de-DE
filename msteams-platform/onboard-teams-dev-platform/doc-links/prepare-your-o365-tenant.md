---
title: Vorbereiten der Entwicklungsumgebung für Teams
description: Einrichten der Umgebung für die Entwicklung von Apps für Teams
keywords: Konfigurieren von Office 365 Mandanten Teams hochladen der Umgebungs Entwicklung
ms.openlocfilehash: 701c6c110026007cf1670e783348bbdbe1aff498
ms.sourcegitcommit: 9fbc701a9a039ecdc360aefbe86df52b9c3593f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/12/2020
ms.locfileid: "46652018"
---
# <a name="prepare-your-development-environment"></a>Vorbereiten Ihrer Entwicklungsumgebung

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

Wenn Microsoft Teams nicht für Ihre Organisation aktiviert wurde, müssen Sie dies zunächst tun. Werfen Sie einen Blick auf unsere detaillierten Anleitungen für [die Aktivierung von Teams für Ihre Organisation](https://docs.microsoft.com/microsoftteams/enable-features-office-365).

## <a name="enable-custom-teams-apps-and-turn-on-custom-app-uploading"></a>Aktivieren benutzerdefinierter Teams-apps und Aktivieren des benutzerdefinierten App-Uploads

Aktivieren Sie wie folgt benutzerdefinierte App-Sideloading für den Entwickler Mandanten:

1. Melden Sie sich bei [Microsoft 365 Admin Center](https://admin.microsoft.com/Adminportal/Home?source=applauncher#/homepage#/) mit Ihren Administratoranmeldeinformationen an. 

2. Wählen Sie **alle**  -->  **Teams**anzeigen aus. 

![Bild des Menüs "App-Überlauf"](~/assets/images/prepare-test-tenant/admin-center.png)

3. Navigieren Sie zu **Teams**  -->  -**Setup Richtlinien**für apps  -->  **Global (organisationsweit Standard)**  

![Bild des Menüs "App-Überlauf"](~/assets/images/prepare-test-tenant/turn-on-sideload.png)

4. Schalten Sie **benutzerdefinierte apps** in die Position **on** hoch.

Das ist alles. Der Testmandant lässt jetzt benutzerdefinierte App-Sideloading.

> [!Note] 
> Es kann bis zu 24 Stunden dauern, bis Sideloading aktiviert ist. Während der Zwischenzeit können Sie **Upload for \<your tenant> ** verwenden, um Ihre APP zu testen.

![Bild des Menüs "App-Überlauf"](~/assets/images/prepare-test-tenant/upload-for-contoso.png)

Umfassende Informationen zur Interaktion dieser Einstellungen *finden Sie unter* [Verwalten benutzerdefinierter App-Richtlinien und-Einstellungen in Microsoft Teams](https://docs.microsoft.com/microsoftteams/teams-custom-app-policies-and-settings) und [Verwalten von App-Setup Richtlinien in Microsoft Teams](https://docs.microsoft.com/microsoftteams/teams-app-setup-policies).