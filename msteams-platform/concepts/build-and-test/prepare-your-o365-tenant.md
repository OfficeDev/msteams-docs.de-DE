---
title: Vorbereiten Ihres Microsoft 365-Mandanten
description: Erste Schritte mit Teams in Microsoft 365
ms.topic: how-to
localization_priority: Normal
keywords: Konfigurieren Microsoft 365 mandanten Teams Hochladens
ms.openlocfilehash: 45d6dfb57fd2faa5bb303aac1dff86be142d0dc2
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2021
ms.locfileid: "52019944"
---
# <a name="prepare-your-microsoft-365-tenant"></a>Vorbereiten Ihres Microsoft 365-Mandanten

Microsoft 365 Abonnenten können Apps für Microsoft Teams mit einem der folgenden Pläne entwickeln:

* Standard
* Standard
* Enterprise E1, E3 und E5
* Developer
* Education, Education Plus, and Education E5

> [!NOTE]
> * Weitere Informationen zu Microsoft 365 Abonnements finden Sie unter [Pläne](https://products.office.com/business/compare-more-office-365-for-business-plans).
> * Teams ist auch für Kunden verfügbar, die E4 vor der Rente abonniert [haben.](https://support.office.com//article/important-information-for-office-365-enterprise-e4-customers-f9572348-43a2-43fa-a3d8-3b6c9c042147)

## <a name="create-your-development-environment"></a>Erstellen Ihrer Entwicklungsumgebung

Wenn Sie nicht über ein Microsoft 365 verfügen, müssen Sie sich für ein Microsoft 365 [Developer Program-Abonnement](https://developer.microsoft.com/microsoft-365/dev-program) registrieren. Das Abonnement ist für 90 Tage kostenlos und wird weiterhin verlängert, solange Sie es für Entwicklungsaktivitäten verwenden. Wenn Sie über ein Visual Studio Enterprise oder Professional verfügen, enthalten beide Programme ein kostenloses Microsoft 365 [Entwicklerabonnement](https://aka.ms/MyVisualStudioBenefits). Sie ist aktiv, solange Visual Studio Abonnement aktiv ist. Weitere Informationen finden Sie unter [Einrichten eines Microsoft 365 Entwicklerabonnements](https://docs.microsoft.com/office/developer-program/office-365-developer-program-get-started).

## <a name="enable-teams-for-your-organization"></a>Aktivieren Teams für Ihre Organisation

Aktivieren Teams für Ihre Organisation und weitere Informationen finden Sie unter [Enable Teams for your organization](/microsoftteams/enable-features-office-365).

## <a name="enable-custom-teams-apps-and-turn-on-custom-app-uploading"></a>Aktivieren von Teams Apps und Aktivieren des Hochladens benutzerdefinierter Apps

**So aktivieren Sie das Hochladen oder Querladen der benutzerdefinierten App für Ihren Entwickler-Mandanten**

1. Melden Sie sich [bei Microsoft 365 Admin Center mit](https://admin.microsoft.com/Adminportal/Home?source=applauncher#/homepage#/) Ihren Administratoranmeldeinformationen an.

2. Wählen **Sie Alle Teams**  >  aus.

    ![Admin Center-Menü](~/assets/images/prepare-test-tenant/admin-center.png)

    > [!Note]
    > Es kann bis zu 24 Stunden dauern, bis **die Teams** angezeigt wird. Sie können [Ihre benutzerdefinierte App in eine Teams für](/microsoftteams/upload-custom-apps#validate) Tests und Überprüfungen in dieser Zeit hochladen.

3. Navigieren Sie **zu Teams apps** Setup  >  **Policies**  >  **Global**.

   ![Aktivieren der Querladenansicht](~/assets/images/prepare-test-tenant/turn-on-sideload.png)

4. **Umschalten Hochladen benutzerdefinierten Apps auf** die **Ein-Position.**

5. Wählen Sie **Speichern** aus. Ihr Test-Mandant kann das Querladen benutzerdefinierter Apps zulassen.

    > [!Note]
    > Es kann bis zu 24 Stunden dauern, bis das Querladen aktiv ist. In der Zwischenzeit können Sie upload **\<your tenant> für verwenden,** um Ihre App zu testen. Informationen zum Hochladen der .zip der App finden Sie unter [Hochladen benutzerdefinierter Apps](/microsoftteams/upload-custom-apps#upload).

    ![Hochladen-App-Ansicht](~/assets/images/prepare-test-tenant/upload-for-contoso.png)

Vollständige Informationen zur Interaktion dieser Einstellungen finden Sie unter [Manage custom app policies and settings in Teams](https://docs.microsoft.com/microsoftteams/teams-custom-app-policies-and-settings) and manage app setup policies in [Teams](https://docs.microsoft.com/microsoftteams/teams-app-setup-policies).

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"] 
> [Auswählen eines Test-Setups](~/concepts/build-and-test/debug.md)

