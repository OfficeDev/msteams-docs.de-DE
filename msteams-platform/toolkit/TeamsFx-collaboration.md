---
title: Zusammenarbeiten an TeamsFx Project mit Teams Toolkit
author: yanjiang
description: In diesem Artikel erfahren Sie, wie Sie mit Teams Toolkit an TeamsFx Project zusammenarbeiten und mit anderen Entwicklern zusammenarbeiten.
ms.author: rentu
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: 0f81990603b3e0275a057c489d7fac44ee0127cc
ms.sourcegitcommit: ca84b5fe5d3b97f377ce5cca41c48afa95496e28
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2022
ms.locfileid: "66142059"
---
# <a name="collaborate-on-teams-project-using-teams-toolkit"></a>Zusammenarbeiten an Teams-Projekten mit dem Teams-Toolkit

Mehrere Entwickler können zusammenarbeiten, um das gleiche TeamsFx-Projekt zu debuggen, bereitzustellen und bereitzustellen. Es ist jedoch erforderlich, die richtigen Berechtigungen für Teams App und Microsoft Azure Active Directory (Azure AD)-App manuell festzulegen. Teams Toolkit unterstützt die Zusammenarbeitsfunktion, damit Entwickler und Projektbesitzer andere Entwickler oder Mitarbeiter zum TeamsFx-Projekt einladen können, um dasselbe TeamsFx-Projekt zu debuggen, bereitzustellen und bereitzustellen.

## <a name="prerequisites"></a>Voraussetzungen

* Microsoft 365-Abonnement
* Azure mit gültigem Abonnement
  
  Weitere Informationen zu verschiedenen Konten finden Sie unter [Vorbereiten von Konten zum Erstellen Teams App](accounts.md).

* [Installieren von Teams Toolkit](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension) Version v3.0.0+

> [!TIP]
> Stellen Sie sicher, dass ein Teams App-Projekt in Visual Studio Code geöffnet ist.

## <a name="collaborate-with-other-developers"></a>Zusammenarbeit mit anderen Entwicklern

Die folgenden Listen führen uns, um den Zusammenarbeitsprozess und dessen Einschränkung zu verstehen:

* Als Projektbesitzer

  > [!NOTE]
  > Bevor Projektmitarbeiter für eine Umgebung hinzugefügt werden, muss der Projektbesitzer das Projekt zuerst [bereitstellen](provision.md) .

  1. Wählen Sie im Abschnitt **"UMGEBUNG**" auf Teams Toolkit **Mitarbeiter aus**. Es zeigt die Optionen **"App Microsoft 365 Teams hinzufügen" (mit Azure AD-App) "Besitzer"** und "**Liste Microsoft 365 Teams App"-Besitzer (mit Azure AD-App) an,** wie in den folgenden Bildern dargestellt:

     :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/add collaborators.png" alt-text="Mitarbeiter":::

  2. Wählen Sie **Microsoft 365 Teams "App hinzufügen" (mit Azure AD-App) "Besitzer"** aus, und fügen Sie andere Microsoft 365 Konto-E-Mail-Adresse als Mitarbeiter hinzu. Das hinzuzufügende Konto muss sich für das Remotedebuggen auf demselben Mandanten wie der Projektbesitzer befinden, wie in der Abbildung gezeigt:

     :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/manifest preview-1.png" alt-text="envi hinzufügen":::

  3. Wenn Sie Mitarbeiter in der aktuellen Umgebung anzeigen möchten, wählen Sie "**Liste Microsoft 365 Teams App"-Besitzer (mit Azure AD-App)** aus. Mitarbeiter werden dann im Ausgabekanal aufgelistet, wie in der folgenden Abbildung dargestellt:

     :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/list of collaborators.png" alt-text="list":::

  4. Pushen des Projekts auf GitHub

     > [!NOTE]
     > Die neu hinzugefügten Mitarbeiter erhalten keine Benachrichtigung. Der Project Besitzer muss den Mitarbeiter benachrichtigen.

* Als Projektmitarbeiter

  1. Klonen Sie das Projekt von GitHub.
  2. Melden Sie sich bei Microsoft 365 Konto an.
  3. Melden Sie sich beim Azure-Konto an, es verfügt über die Berechtigung "Mitwirkender" für alle Azure-Ressourcen, die im Projekt verwendet werden.
  4. Um eine Vorschau Ihrer Teams-App anzuzeigen, stellen Sie das Projekt remote bereit.
  5. Starten Sie remote, um eine Vorschau der Teams-App zu erhalten.

     > [!NOTE]
     > Mitarbeiter müssen sich mit dem Konto anmelden, das der Projektbesitzer unter demselben Mandanten mit dem Projektbesitzer hinzufügt. Weitere Informationen finden Sie [unter Erstellen und Ausführen Ihrer Teams-App in einer Remoteumgebung](/microsoftteams/platform/sbs-gs-javascript?tabs=vscode%2Cvsc%2Cviscode%2Cvcode&tutorial-step=3&branch).

### <a name="limitations"></a>Einschränkungen

Wenn Sie Mitarbeiter aus Teams Toolkit-Erweiterung entfernen möchten, müssen Sie sie manuell entfernen, da Sie sie nicht direkt entfernen können. Führen Sie die folgenden Schritte aus, um Mitarbeiter manuell zu entfernen:

* Verwenden des Entwicklerportals

  * Wechseln Sie zu [Teams Entwicklerportal](https://dev.teams.microsoft.com/home), und wählen Sie Ihre Teams App nach Name oder App-ID aus.
  * Wählen Sie **"Besitzer** " im linken Bereich aus.
  * Wählen Sie den Mitarbeiter aus, und entfernen Sie den Mitarbeiter.

* Verwenden von Azure Active Directory

  * Wechseln Sie zu [Azure Active Directory](https://ms.portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/RegisteredApps), wählen Sie im linken Bereich **die App-Registrierung** aus, und suchen Sie Ihre Azure AD-App.
  * Wählen Sie **"Besitzer**" im linken Bereich auf Azure AD-App Verwaltungsseite aus.
  * Wählen Sie den Mitarbeiter aus, und entfernen Sie den Mitarbeiter.

   > [!NOTE]
   >
   > * Mitarbeiter, die Ihrem Projekt hinzugefügt wurden, erhalten keine Benachrichtigung. Project Besitzer muss Mitarbeiter offline benachrichtigen.
   > * Azure-bezogene Berechtigungen müssen vom Azure-Abonnementadministrator auf Azure-Portal manuell festgelegt werden. Das Azure-Konto muss über eine Mitwirkenderolle für das Abonnement verfügen, damit Entwickler zusammenarbeiten können, um TeamsFx-Projekt bereitzustellen und bereitzustellen.

## <a name="see-also"></a>Siehe auch

* [Bereitstellen von Cloudressourcen](provision.md)
* [Bereitstellen der Teams-App in der Cloud](deploy.md)
* [Verwalten mehrerer Umgebungen](TeamsFx-multi-env.md)
