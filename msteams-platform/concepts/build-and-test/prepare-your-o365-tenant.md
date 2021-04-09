---
title: Vorbereiten des Microsoft 365-Mandanten
description: Erste Schritte mit Teams in Microsoft 365
ms.topic: how-to
keywords: Konfigurieren des Hochladens von Microsoft 365-Mandantenteams
ms.openlocfilehash: aa7f994744f8b1c62aa32122a5006cfa0f22d391
ms.sourcegitcommit: 5b3ba227c2e5e6f7a2c629961993f168da6a504d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/08/2021
ms.locfileid: "51634754"
---
# <a name="prepare-your-microsoft-365-tenant"></a>Vorbereiten des Microsoft 365-Mandanten

Microsoft 365-Abonnenten können Apps für Microsoft Teams mit einem der folgenden Pläne entwickeln:

* Standard
* Standard
* Enterprise E1, E3 und E5
* Developer
* Education, Education Plus, and Education E5

> [!NOTE]
> Weitere Informationen zu Microsoft 365-Abonnements finden Sie unter [Pläne](https://products.office.com/business/compare-more-office-365-for-business-plans).
> 
> Microsoft Teams steht auch Kunden zur Verfügung, die E4 vor der Rente [abonniert haben.](https://support.office.com//article/important-information-for-office-365-enterprise-e4-customers-f9572348-43a2-43fa-a3d8-3b6c9c042147)

## <a name="create-your-development-environment"></a>Erstellen Ihrer Entwicklungsumgebung

Wenn Sie kein Microsoft 365-Konto haben, müssen Sie sich für ein [Microsoft 365 Developer Program-Abonnement](https://developer.microsoft.com/microsoft-365/dev-program) registrieren. Das Abonnement ist für 90 Tage kostenlos und wird weiterhin verlängert, solange Sie es für Entwicklungsaktivitäten verwenden. Wenn Sie über ein Visual Studio Enterprise- oder Professional-Abonnement verfügen, enthalten beide Programme ein kostenloses Microsoft [365-Entwicklerabonnement.](https://aka.ms/MyVisualStudioBenefits) Sie ist so lange aktiv, wie Visual Studio Abonnement aktiv ist. Weitere Informationen finden Sie unter [Einrichten eines Microsoft 365-Entwicklerabonnements](https://docs.microsoft.com/office/developer-program/office-365-developer-program-get-started).

## <a name="enable-microsoft-teams-for-your-organization"></a>Aktivieren von Microsoft Teams für Ihre Organisation

Aktivieren Sie Microsoft Teams für Ihre Organisation, und sehen Sie sich unsere detaillierten Anleitungen zum Aktivieren [von Teams für Ihre Organisation an.](/microsoftteams/enable-features-office-365)

## <a name="enable-custom-teams-apps-and-turn-on-custom-app-uploading"></a>Aktivieren benutzerdefinierter Teams-Apps und Aktivieren des Hochladens benutzerdefinierter Apps

**So aktivieren Sie das Hochladen oder Querladen der benutzerdefinierten App für Ihren Entwickler-Mandanten**

1. Melden Sie sich [beim Microsoft 365 Admin Center](https://admin.microsoft.com/Adminportal/Home?source=applauncher#/homepage#/) mit Ihren Administratoranmeldeinformationen an.

2. Wählen **Sie Alle Teams** anzeigen  >  **aus.**

    ![Abbildung des Admin Center-Menüs](~/assets/images/prepare-test-tenant/admin-center.png)

    > [!Note]
    > Es kann bis zu 24 Stunden dauern, bis die **Option Teams** angezeigt wird. Sie können [Ihre benutzerdefinierte App in dieser](/microsoftteams/upload-custom-apps#validate) Zeit zu Test- und Validierungszwecken in eine Teams-Umgebung hochladen.

3. Navigieren Sie zu **Teams apps**  >  **Setup Policies**  >  **Global**.

   ![Aktivieren der Querladenansicht](~/assets/images/prepare-test-tenant/turn-on-sideload.png)

4. **Umschalten Sie benutzerdefinierte Apps hochladen** an die **Ein-Position.**

5. Wählen Sie **Speichern** aus.
   Ihr Test-Mandant kann das Querladen benutzerdefinierter Apps zulassen.

    > [!Note]
    > Es kann bis zu 24 Stunden dauern, bis das Querladen aktiv ist. Zwischenzeit können Sie upload **\<your tenant> für verwenden,** um Ihre App zu testen.

    ![Updload-App-Ansicht](~/assets/images/prepare-test-tenant/upload-for-contoso.png)

Vollständige Informationen zur Interaktion dieser Einstellungen finden Sie unter [Manage custom app policies and settings in Microsoft Teams](https://docs.microsoft.com/microsoftteams/teams-custom-app-policies-and-settings) und Manage app setup policies in Microsoft [Teams](https://docs.microsoft.com/microsoftteams/teams-app-setup-policies).

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"] 
> [Auswählen einer Testeinrichtung](~/concepts/build-and-test/debug.md)
> 


