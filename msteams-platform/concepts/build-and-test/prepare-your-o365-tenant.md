---
title: Vorbereiten Ihres Microsoft 365-Mandanten
description: Erste Schritte mit Teams in Microsoft 365
ms.topic: how-to
ms.localizationpriority: high
keywords: Konfigurieren Microsoft 365 Mandanten Teams Hochladen
ms.openlocfilehash: 9e9972a41b6b210b99e7a5ac16fc3665132c3757
ms.sourcegitcommit: f15bd0e90eafb00e00cf11183b129038de8354af
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/28/2022
ms.locfileid: "65111395"
---
# <a name="prepare-your-microsoft-365-tenant"></a>Vorbereiten Ihres Microsoft 365-Mandanten

Microsoft 365-Abonnenten können Apps für Microsoft Teams mit einem der folgenden Pläne entwickeln:

* Standard
* Standard
* Enterprise E1, E3 und E5
* Developer
* Education, Education Plus und Education E5

> [!NOTE]
>
> * Weitere Informationen zu Microsoft 365-Abonnements finden Sie unter [Pläne](https://products.office.com/business/compare-more-office-365-for-business-plans).
> * Teams steht auch Kunden zur Verfügung, die E4 vor seiner [Einstellung](https://support.office.com//article/important-information-for-office-365-enterprise-e4-customers-f9572348-43a2-43fa-a3d8-3b6c9c042147) abonniert haben.

## <a name="create-your-development-environment"></a>Vorbereiten der Entwicklungsumgebung

Wenn Sie kein Microsoft 365-Konto haben, können Sie sich für das [Microsoft 365-Entwicklerprogramm](https://developer.microsoft.com/microsoft-365/dev-program)-Abonnement registrieren. Das Abonnement ist 90 Tage lang kostenlos und wird weiterhin verlängert, solange Sie es für Entwicklungsaktivitäten verwenden. Wenn Sie über ein Visual Studio Enterprise- oder Professional-Abonnement verfügen, enthalten beide Programme ein kostenloses Microsoft 365 [Entwicklerabonnement](https://aka.ms/MyVisualStudioBenefits). Es ist aktiv, solange Ihr Visual Studio Abonnement aktiv ist. Weitere Informationen finden Sie unter [Einrichten eines Microsoft 365-Entwicklerabonnements](/office/developer-program/office-365-developer-program-get-started).

## <a name="enable-teams-for-your-organization"></a>Aktivieren von Teams für Ihre Organisation

Aktivieren Sie Teams für Ihre Organisation. Weitere Informationen finden Sie unter [Aktivieren von Teams für Ihre Organisation](/microsoftteams/enable-features-office-365).

## <a name="enable-custom-teams-apps-and-turn-on-custom-app-uploading"></a>Aktivieren von benutzerdefinierten Teams-Apps und Aktivieren des Hochladens benutzerdefinierter Apps

Um das Hochladen oder Querladen benutzerdefinierter Apps für Ihren Entwicklermandanten zu aktivieren:

1. Melden Sie sich mit Ihren Administratoranmeldeinformationen beim [Microsoft 365 Admin Center](https://admin.microsoft.com/Adminportal/Home?source=applauncher#/homepage#/) an.

2. Wählen Sie **Alle anzeigen** > **Teams** aus.

    ![Admin Center-Menü](~/assets/images/prepare-test-tenant/admin-center.png)

    > [!Note]
    > Es kann bis zu 24 Stunden dauern, bis die Option **Teams** angezeigt wird. Sie können in dieser Zeit [Ihre benutzerdefinierte App in eine Teams-Umgebung hochladen](/microsoftteams/upload-custom-apps#validate), um sie zu testen und zu validieren.

3. Navigieren Sie zu **Teams-Apps** > **Setuprichtlinien** > **Global**.

   ![Aktivieren der Querladenansicht](~/assets/images/prepare-test-tenant/turn-on-sideload.png)

4. Schalten Sie **Benutzerdefinierte Apps hochladen** auf die Position **Ein** um.

5. Wählen Sie **Speichern**. Ihr Testmandant kann benutzerdefiniertes Querladen von Apps zulassen.

    > [!Note]
    > Es kann bis zu 24 Stunden dauern, bis das Querladen aktiv wird. In der Zwischenzeit können Sie **Upload für \<your tenant>** verwenden, um Ihre App zu testen. Informationen zum Hochladen der .zip-Paketdatei der App finden Sie unter [Hochladen benutzerdefinierter Apps](/microsoftteams/upload-custom-apps#upload).

    ![Hochladen-App-Ansicht](~/assets/images/prepare-test-tenant/upload-for-contoso.png)

Ausführliche Informationen über das Interagieren dieser Einstellungen finden Sie unter [Verwalten von benutzerdefinierten App-Richtlinien und Einstellungen in Teams](/microsoftteams/teams-custom-app-policies-and-settings) und [Verwalten von App-Setuprichtlinien in Teams](/microsoftteams/teams-app-setup-policies).

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Auswählen eines Test-Setups](~/concepts/build-and-test/debug.md)

## <a name="see-also"></a>Siehe auch

[Hinzufügen von Testdaten zu Ihrem Microsoft 365-Testmandanten](~/concepts/build-and-test/test-data.md)
