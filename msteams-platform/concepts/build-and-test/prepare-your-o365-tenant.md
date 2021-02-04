---
title: Vorbereiten des Microsoft 365-Mandanten
description: Erste Schritte mit Teams in Microsoft 365
ms.topic: how-to
keywords: Konfigurieren des Hochladens von Microsoft 365-Mandantenteams
ms.openlocfilehash: 50765271b93edd380d1c23672289b618baf1d346
ms.sourcegitcommit: 55a4246e62d69d631a63bdd33de34f1b62cc0132
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2021
ms.locfileid: "50093943"
---
# <a name="prepare-your-microsoft-365-tenant"></a>Vorbereiten des Microsoft 365-Mandanten

Als Microsoft 365-Abonnent können Sie Apps für Microsoft Teams mit einem der folgenden Pläne [entwickeln:](https://products.office.com/business/compare-more-office-365-for-business-plans)

* Standard
* Standard
* Enterprise E1, E3 und E5
* Developer
* Education, Education Plus und Education E5

Microsoft Teams steht auch Kunden zur Verfügung, die E4 vor der Dehierung [abonniert haben.](https://support.office.com//article/important-information-for-office-365-enterprise-e4-customers-f9572348-43a2-43fa-a3d8-3b6c9c042147)

## <a name="just-need-a-development-environment"></a>Benötigen Sie nur eine Entwicklungsumgebung?

Wenn Sie derzeit kein Microsoft 365-Konto haben, können Sie sich für ein Abonnement des [Microsoft 365-Entwicklerprogramms](https://developer.microsoft.com/microsoft-365/dev-program) registrieren. Es ist *90* Tage lang kostenlos und wird kontinuierlich verlängert, solange Sie es für Entwicklungsaktivitäten verwenden. Wenn Sie über ein Visual Studio  *Enterprise-* oder Professional-Abonnement verfügen, enthalten beide Programme ein kostenloses Microsoft 365-Entwicklerabonnement, das für die Lebensdauer Ihres Visual Studio ist. [](https://aka.ms/MyVisualStudioBenefits) *Weitere Informationen* finden Sie unter Einrichten [eines Microsoft 365-Entwicklerabonnements.](https://docs.microsoft.com/office/developer-program/office-365-developer-program-get-started)

## <a name="enable-microsoft-teams-for-your-organization"></a>Aktivieren von Microsoft Teams für Ihre Organisation 

Wenn Microsoft Teams für Ihre Organisation nicht aktiviert wurde, müssen Sie dies zuerst tun. Sehen Sie sich unsere detaillierten Anleitungen zum Aktivieren [von Teams für Ihre Organisation an.](/microsoftteams/enable-features-office-365)

## <a name="enable-custom-teams-apps-and-turn-on-custom-app-uploading"></a>Aktivieren von benutzerdefinierten Teams-Apps und Aktivieren des Hochladens benutzerdefinierter Apps

Aktivieren Sie das Sideloading von benutzerdefinierten Apps für Ihren Entwickler-Mandanten wie folgt:

1. Melden Sie [sich mit Ihren Administratoranmeldeinformationen beim Microsoft 365](https://admin.microsoft.com/Adminportal/Home?source=applauncher#/homepage#/) Admin Center an. 

2. Wählen **Sie "Alle Teams**  -->  **anzeigen" aus.** 

![Abbildung des Admin Center-Menüs](~/assets/images/prepare-test-tenant/admin-center.png)

> [!Note] 
> Es kann bis zu 24 Stunden dauern, bis die Option "Teams" angezeigt wird. In der Zwischenzeit können Sie Ihre benutzerdefinierte App [zu Test-](/microsoftteams/upload-custom-apps#validate) und Validierungszwecken in eine Teams-Umgebung hochladen.

3. Navigieren Sie zu **"Setuprichtlinien**  -->  **für**  -->  **Teams-Apps" global (organisationsweite Standardeinstellung)**  

![Aktivieren der Querladenansicht](~/assets/images/prepare-test-tenant/turn-on-sideload.png)

4. **Umschalten des Hochladens benutzerdefinierter Apps** in die **On-Position.**

5. Wählen Sie **"Speichern"** aus, um die Änderungen zu speichern.

Das ist alles. Ihr Test mandant lässt jetzt das Querladen benutzerdefinierter Apps zu.

> [!Note] 
> Es kann bis zu 24 Stunden dauern, bis das Querladen aktiviert ist. In der Zwischenzeit können Sie den **Upload \<your tenant> für verwenden,** um Ihre App zu testen.

![Updload-App-Ansicht](~/assets/images/prepare-test-tenant/upload-for-contoso.png)

Vollständige Informationen zur Interaktion dieser Einstellungen finden Sie unter *,* Verwalten von benutzerdefinierten Richtlinien und Einstellungen für Apps in [Microsoft Teams](https://docs.microsoft.com/microsoftteams/teams-custom-app-policies-and-settings) und Verwalten von Setuprichtlinien für Apps in [Microsoft Teams.](https://docs.microsoft.com/microsoftteams/teams-app-setup-policies)
