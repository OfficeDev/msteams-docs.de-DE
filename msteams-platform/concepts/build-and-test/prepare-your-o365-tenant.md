---
title: Vorbereiten Ihres Microsoft 365-Mandanten
description: Erste Schritte mit Teams in Microsoft 365
ms.topic: how-to
ms.localizationpriority: medium
keywords: Konfigurieren Microsoft 365 Mandanten Teams Hochladens
ms.openlocfilehash: c1f6a3009a3622c9ba46f2f03024ab696d03d979
ms.sourcegitcommit: 1431dfe08d5a19a63dbf1542a2e6c661e4dd7fc1
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/12/2021
ms.locfileid: "60949033"
---
# <a name="prepare-your-microsoft-365-tenant"></a>Vorbereiten Ihres Microsoft 365-Mandanten

Microsoft 365 Abonnenten können Apps für Microsoft Teams mit einem der folgenden Pläne entwickeln:

* Standard
* Standard
* Enterprise E1, E3 und E5
* Entwickler
* Education, Education Plus und Education E5

> [!NOTE]
> * Weitere Informationen zu Microsoft 365 Abonnements finden Sie unter ["Pläne".](https://products.office.com/business/compare-more-office-365-for-business-plans)
> * Teams ist auch für Kunden verfügbar, die E4 vor der [Einstellung](https://support.office.com//article/important-information-for-office-365-enterprise-e4-customers-f9572348-43a2-43fa-a3d8-3b6c9c042147)abonniert haben.

## <a name="create-your-development-environment"></a>Erstellen der Entwicklungsumgebung

Wenn Sie nicht über ein Microsoft 365 Konto verfügen, müssen Sie sich für ein [Microsoft 365 Entwicklerprogramm-Abonnement](https://developer.microsoft.com/microsoft-365/dev-program) registrieren. Das Abonnement ist 90 Tage lang kostenlos und wird weiterhin verlängert, solange Sie es für Entwicklungsaktivitäten verwenden. Wenn Sie über ein Visual Studio Enterprise- oder Professional-Abonnement verfügen, enthalten beide Programme ein kostenloses Microsoft 365 [Entwicklerabonnement.](https://aka.ms/MyVisualStudioBenefits) Es ist aktiv, solange Ihr Visual Studio Abonnement aktiv ist. Weitere Informationen finden Sie unter [Einrichten eines Microsoft 365 Entwicklerabonnements.](/office/developer-program/office-365-developer-program-get-started)

## <a name="enable-teams-for-your-organization"></a>Aktivieren Teams für Ihre Organisation

Aktivieren Sie Teams für Ihre Organisation, und weitere Informationen finden Sie unter [Aktivieren Teams für Ihre Organisation.](/microsoftteams/enable-features-office-365)

## <a name="enable-custom-teams-apps-and-turn-on-custom-app-uploading"></a>Aktivieren von benutzerdefinierten Teams-Apps und Aktivieren des hochladens benutzerdefinierter Apps

**So aktivieren Sie das hochladen oder Querladen der benutzerdefinierten App für Ihren Entwicklermandanten**

1. Melden Sie sich mit Ihren Administratoranmeldeinformationen bei [Microsoft 365 Admin Center](https://admin.microsoft.com/Adminportal/Home?source=applauncher#/homepage#/) an.

2. Wählen Sie **"Alle** Teams anzeigen"  >  aus.

    ![Admin Center-Menü](~/assets/images/prepare-test-tenant/admin-center.png)

    > [!Note]
    > Es kann bis zu 24 Stunden dauern, bis die **Option Teams** angezeigt wird. Sie können [Ihre benutzerdefinierte App in eine Teams Umgebung hochladen, um](/microsoftteams/upload-custom-apps#validate) sie zu testen und zu überprüfen.

3. Navigieren Sie zu **Teams App**  >  **Setup Policies**  >  **Global**.

   ![Aktivieren der Sideload-Ansicht](~/assets/images/prepare-test-tenant/turn-on-sideload.png)

4. Umschalten **Hochladen benutzerdefinierter Apps** auf **die** Ein-Position.

5. Klicken Sie auf **Speichern**. Ihr Testmandant kann das benutzerdefinierte Querladen von Apps zulassen.

    > [!Note]
    > Es kann bis zu 24 Stunden dauern, bis das Querladen aktiv ist. In der Zwischenzeit können Sie **Upload \<your tenant>** verwenden, um Ihre App zu testen. Informationen zum Hochladen der .zip-Paketdatei der App finden Sie unter ["Hochladen benutzerdefinierter Apps".](/microsoftteams/upload-custom-apps#upload)

    ![Hochladen App-Ansicht](~/assets/images/prepare-test-tenant/upload-for-contoso.png)

Vollständige Informationen zur Interaktion dieser Einstellungen finden Sie unter [Verwalten von benutzerdefinierten App-Richtlinien und -Einstellungen in Teams](/microsoftteams/teams-custom-app-policies-and-settings) und Verwalten von [App-Setuprichtlinien in Teams.](/microsoftteams/teams-app-setup-policies)

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"] 
> [Auswählen eines Test-Setups](~/concepts/build-and-test/debug.md)

## <a name="see-also"></a>Siehe auch

[Hinzufügen von Testdaten zu Ihrem Microsoft 365 Testmandanten](~/concepts/build-and-test/test-data.md)
