---
title: Zusammenarbeiten an TeamsFx Project mithilfe des Teams-Toolkits
author: surbhigupta
description: In diesem Artikel erfahren Sie, wie Sie mithilfe des Teams-Toolkits an TeamsFx Project zusammenarbeiten und mit anderen Entwicklern zusammenarbeiten.
ms.author: v-amprasad
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: 90ccd073e45649f715751e81835747bfb95d7806
ms.sourcegitcommit: ed7488415f814d0f60faa15ee8ec3d64ee336380
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/07/2022
ms.locfileid: "67616854"
---
# <a name="collaborate-on-teams-project-using-microsoft-teams-toolkit"></a>Zusammenarbeiten am Teams-Projekt mithilfe des Microsoft Teams-Toolkits

Mehrere Entwickler können zusammenarbeiten, um das gleiche TeamsFx-Projekt zu debuggen, bereitzustellen und bereitzustellen. Es ist jedoch erforderlich, die richtigen Berechtigungen für Die Teams-App und Microsoft Azure Active Directory (Azure AD) manuell festzulegen. Das Teams-Toolkit unterstützt die Zusammenarbeitsfunktion, damit Entwickler und Projektbesitzer andere Entwickler oder Mitarbeiter zum TeamsFx-Projekt einladen können, um dasselbe TeamsFx-Projekt zu debuggen, bereitzustellen und bereitzustellen.

## <a name="collaborate-with-other-developers"></a>Zusammenarbeit mit anderen Entwicklern

Die folgenden Abschnitte führen uns, um den Zusammenarbeitsprozess als Projektbesitzer oder Projektmitarbeiter zu verstehen:

### <a name="as-project-owner"></a>Als Projektbesitzer

  > [!NOTE]
  > Bevor Projektmitarbeiter für eine Umgebung hinzugefügt werden, muss der Projektbesitzer das Projekt zuerst [bereitstellen](provision.md) .

  1. Wählen Sie in der Aktivitätsleiste das **Teams-Toolkit** aus.
  
     :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/select-teams-toolkit.png" alt-text="Auswählen des Teams-Toolkits in der Aktivitätsleiste":::

  1. Wählen Sie im Abschnitt **"UMGEBUNG** " Mitarbeiter aus, die als Option **1** " **Microsoft 365 Teams-App hinzufügen" (mit Azure AD-App)-Besitzern** und **2** " **Microsoft 365 Teams-App-Besitzer " (mit Azure AD-App) auflisten,** wie in der folgenden Abbildung dargestellt:

     :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/add collaborators.png" alt-text="Mitarbeiter":::

  2. Wählen Sie **"Microsoft 365 Teams-App (mit Azure AD-App)-Besitzern hinzufügen** " aus, und fügen Sie andere E-Mail-Adressen des Microsoft 365-Kontos als Mitarbeiter hinzu. Das hinzuzufügende Konto muss sich für das Remotedebuggen auf demselben Mandanten wie der Projektbesitzer befinden, wie in der Abbildung gezeigt:

     :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/add-owner.png" alt-text="Projektbesitzer hinzufügen":::

  3. Wenn Sie Mitarbeiter in der aktuellen Umgebung anzeigen möchten, wählen Sie **"Microsoft 365 Teams-App-Besitzer auflisten" (mit Azure AD-App)** aus. Dann können Sie Mitarbeiter sehen, die im Ausgabekanal aufgelistet sind, wie in der folgenden Abbildung dargestellt:

     :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/list of collaborators.png" alt-text="list":::

  4. Verschieben Sie das Projekt auf GitHub.

     > [!NOTE]
     > Die neu hinzugefügten Mitarbeiter erhalten keine Benachrichtigung. Der Projektbesitzer muss den Mitarbeiter benachrichtigen.

### <a name="as-project-collaborator"></a>Als Projektmitarbeiter

  1. Klonen Sie das Projekt von GitHub.
  2. Melden Sie sich beim Microsoft 365-Konto an.
  3. Melden Sie sich beim Azure-Konto an, es verfügt über die Berechtigung "Mitwirkender" für alle Azure-Ressourcen, die im Projekt verwendet werden.
  4. Um eine Vorschau Ihrer Teams-App anzuzeigen, stellen Sie das Projekt remote bereit.
  5. Starten Sie remote, um eine Vorschau der Teams-App zu erhalten.

     > [!NOTE]
     > Mitarbeiter müssen sich mit dem Konto anmelden, das der Projektbesitzer unter demselben Mandanten mit dem Projektbesitzer hinzufügt. Weitere Informationen finden Sie [unter Erstellen und Ausführen Ihrer Teams-App in einer Remoteumgebung](/microsoftteams/platform/sbs-gs-javascript?tabs=vscode%2Cvsc%2Cviscode%2Cvcode&tutorial-step=3&branch).

## <a name="remove-collaborators"></a>Mitarbeiter entfernen

Wenn Sie Mitarbeiter aus der Erweiterung des Teams-Toolkits entfernen möchten, müssen Sie sie manuell entfernen, da Sie sie nicht direkt entfernen können. Führen Sie die folgenden Schritte aus, um Mitarbeiter manuell zu entfernen:

* Verwenden des Entwicklerportals

  * Wechseln Sie zum [Teams-Entwicklerportal](https://dev.teams.microsoft.com/home) , und wählen Sie Ihre Teams-App nach Name oder App-ID aus.
  * Wählen Sie **"Besitzer** " im linken Bereich aus.
  * Wählen Sie den Mitarbeiter aus, und entfernen Sie den Mitarbeiter.

* Verwenden von Azure Active Directory

  * Wechseln Sie zu [Azure Active Directory](https://ms.portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/RegisteredApps), wählen Sie im linken Bereich **die App-Registrierung** aus, und suchen Sie Ihre Azure AD-App.
  * Wählen Sie **"Besitzer** " im linken Bereich auf der Verwaltungsseite der Azure AD-App aus.
  * Wählen Sie den Mitarbeiter aus, und entfernen Sie den Mitarbeiter.

    > [!NOTE]
    >
    > * Mitarbeiter, die Ihrem Projekt hinzugefügt wurden, erhalten keine Benachrichtigung. Projektbesitzer muss Mitarbeiter offline benachrichtigen.
    > * Azure-bezogene Berechtigungen müssen vom Azure-Abonnementadministrator auf Azure-Portal manuell festgelegt werden.
    > * Das Azure-Konto muss über eine Mitwirkenderolle für das Abonnement verfügen, damit Entwickler zusammenarbeiten können, um TeamsFx-Projekt bereitzustellen und bereitzustellen.

## <a name="see-also"></a>Siehe auch

* [Bereitstellen von Cloudressourcen](provision.md)
* [Bereitstellen der Teams-App in der Cloud](deploy.md)
* [Verwalten mehrerer Umgebungen](TeamsFx-multi-env.md)
