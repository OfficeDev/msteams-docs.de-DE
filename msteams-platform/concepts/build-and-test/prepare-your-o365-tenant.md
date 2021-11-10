---
title: Vorbereiten Ihres Microsoft 365-Mandanten
description: Erste Schritte mit Teams in Microsoft 365
ms.topic: how-to
ms.localizationpriority: medium
keywords: Konfigurieren Microsoft 365 Mandanten Teams Hochladens
ms.openlocfilehash: 2b7da66460df12efd1e3c5bd45a9dfa6572e4b4c
ms.sourcegitcommit: af1d0a4041ce215e7863ac12c71b6f1fa3e3ba81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/10/2021
ms.locfileid: "60888153"
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

Wenn Sie nicht über ein Microsoft 365 Konto verfügen, müssen Sie sich für ein [Abonnement für Microsoft 365 Entwicklerprogramm](https://developer.microsoft.com/microsoft-365/dev-program) registrieren. Das Abonnement ist 90 Tage lang kostenlos und wird weiterhin verlängert, solange Sie es für Entwicklungsaktivitäten verwenden. Wenn Sie über ein Visual Studio Enterprise- oder Professional-Abonnement verfügen, enthalten beide Programme ein kostenloses Microsoft 365 [Entwicklerabonnement.](https://aka.ms/MyVisualStudioBenefits) Es ist aktiv, solange Ihr Visual Studio Abonnement aktiv ist. Weitere Informationen finden Sie unter [Einrichten eines Microsoft 365 Entwicklerabonnements.](/office/developer-program/office-365-developer-program-get-started)

## <a name="enable-teams-for-your-organization"></a>Aktivieren Teams für Ihre Organisation

Aktivieren Sie Teams für Ihre Organisation, und weitere Informationen finden Sie unter [Aktivieren Teams für Ihre Organisation.](/microsoftteams/enable-features-office-365)

## <a name="enable-custom-teams-apps-and-turn-on-custom-app-uploading"></a>Aktivieren von benutzerdefinierten Teams-Apps und Aktivieren des benutzerdefinierten App-Uploads

**So aktivieren Sie das hochladen oder Querladen der benutzerdefinierten App für Ihren Entwicklermandanten**

1. Melden Sie sich mit Ihren Administratoranmeldeinformationen bei [Microsoft 365 Admin Center](https://admin.microsoft.com/Adminportal/Home?source=applauncher#/homepage#/) an.

2. Wählen Sie **"Alle** Teams anzeigen"  >  aus.

    ![Admin Center-Menü](~/assets/images/prepare-test-tenant/admin-center.png)

    > [!Note]
    > Es kann bis zu 24 Stunden dauern, bis die **Option Teams** angezeigt wird. Sie können [Ihre benutzerdefinierte App zu diesem](/microsoftteams/upload-custom-apps#validate) Zeitpunkt zum Testen und Überprüfen in eine Teams Umgebung hochladen.

3. Navigieren Sie zu **Teams App**  >  **Setup Policies**  >  **Global**.

   ![Aktivieren der Sideload-Ansicht](~/assets/images/prepare-test-tenant/turn-on-sideload.png)

4. Umschalten **Hochladen benutzerdefinierten Apps** auf **die** Ein-Position.

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
