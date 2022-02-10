---
title: Zusammenarbeit an TeamsFx-Project mit Teams Toolkit
author: yanjiang
description: Zusammenarbeit an TeamsFx-Project mit Teams Toolkit
ms.author: rentu
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: af96227df93bb2c236607791e3870b1882d2da5f
ms.sourcegitcommit: 90587b1ec04bf20d716ed6feb8ccca4313e87f8c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/10/2022
ms.locfileid: "62518373"
---
# <a name="collaborate-on-teams-project-using-teams-toolkit"></a>Zusammenarbeit an Teams Projekt mit Teams Toolkit

Mehrere Entwickler können zusammenarbeiten, um dasselbe TeamsFx-Projekt zu debuggen, bereitzustellen und bereitzustellen. Es muss jedoch manuell die richtigen Berechtigungen für Teams App und Microsoft Azure Active Directory (Azure AD) App.Teams  Das Toolkit unterstützt die Zusammenarbeitsfunktion, damit Entwickler und Projektbesitzer andere Entwickler oder Mitarbeiter zum TeamsFx-Projekt einladen können, dasselbe TeamsFx-Projekt zu debuggen, bereitzustellen und bereitzustellen.

## <a name="prerequisites"></a>Voraussetzungen

* Kontovoraussetzungen

    Um Cloudressourcen bereitzustellen, benötigen Sie die folgenden Konten. Weitere Informationen finden Sie unter ["Vorbereiten von Konten zum Erstellen Teams App](accounts.md)".

  * Microsoft 365-Abonnement
  * Azure mit gültigem Abonnement

* [Installieren Sie Teams Toolkit](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension) Version v3.0.0+.

> [!TIP]
> Stellen Sie sicher, dass in Microsoft Visual Studio Code ein Teams App-Projekt geöffnet ist.

## <a name="collaborate-with-other-developers"></a>Zusammenarbeit mit anderen Entwicklern

Die folgende Liste führt uns dazu, den Zusammenarbeitsprozess und dessen Einschränkung zu verstehen:

### <a name="as-project-owner"></a>Als Projektbesitzer

> [!NOTE]
> Bevor Mitarbeiter für eine Umgebung hinzugefügt werden, muss der Projektbesitzer das Projekt zuerst [bereitstellen](provision.md) .

* Wählen Sie im Abschnitt **"UMGEBUNG**" auf Teams Toolkit **Mitarbeiter aus**. Es zeigt die Optionen **"Add Microsoft 365 Teams App (with Microsoft Azure Active Directory (Azure AD) App) Owners**" und **"List Microsoft 365 Teams App" (mit Azure AD App) an. Besitzer** wie in den folgenden Bildern dargestellt:

  :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/add collaborators.png" alt-text="Mitarbeiter":::

* Wählen Sie **"Add Microsoft 365 Teams App (with Microsoft Azure Active Directory (Azure AD) App)"-Besitzer aus**, und fügen Sie als Mitarbeiter andere Microsoft 365 Konto-E-Mail-Adresse hinzu. Das hinzuzufügende Konto muss sich auf demselben Mandanten wie der Projektbesitzer für Remotedebugger befinden, wie in der Abbildung dargestellt:

  :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/manifest preview-1.png" alt-text="envi hinzufügen":::

* Wählen Sie zum Anzeigen von Mitarbeitern in der aktuellen Umgebung **"List Microsoft 365 Teams App (with Microsoft Azure Active Directory (Azure AD) App)"-Besitzer** aus, und die Mitarbeiter werden dann im Ausgabekanal aufgeführt, wie in der folgenden Abbildung dargestellt:

  :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/list of collaborators.png" alt-text="list":::

* Verschieben Sie das Projekt an GitHub.

> [!NOTE]
> Der neu hinzugefügte Mitarbeiter erhält keine Benachrichtigung. Project Besitzer muss den Mitarbeiter benachrichtigen.

### <a name="as-project-collaborator"></a>Als Projektmitarbeiter

* Klonen Sie das Projekt aus GitHub.
* Melden Sie sich bei Microsoft 365 Konto an.
* Melden Sie sich bei einem Azure-Konto an, das über die Berechtigung "Mitwirkender" für alle Azure-Ressourcen verfügt, die in diesem Projekt verwendet werden.
* Stellen Sie das Projekt remote bereit, um eine Vorschau Ihrer Teams-App anzuzeigen.
* Starten Sie die Remote-App, um eine Vorschau der Teams-App zu erhalten.

Weitere Informationen finden Sie unter [Erstellen und Ausführen Ihrer Teams-App in einer Remoteumgebung](/microsoftteams/platform/sbs-gs-javascript?tabs=vscode%2Cvsc%2Cviscode%2Cvcode&tutorial-step=3&branch).

> [!NOTE]
> Mitarbeiter müssen sich mithilfe des vom Projektbesitzer hinzugefügten Kontos anmelden, das sich unter demselben Mandanten mit dem Projektbesitzer befindet.

### <a name="limitation"></a>Einschränkung

Mitarbeiter können nicht direkt aus Teams Toolkit-Erweiterung entfernt werden. Führen Sie die folgenden Schritte aus, um Mitarbeiter manuell zu entfernen:

  1. Wechseln Sie zu Teams Entwicklerportal, und wählen Sie Ihre Teams App anhand des Namens oder der App-ID aus.
  2. Wählen Sie **"Besitzer"** aus dem linken Bereich aus.
  3. Wählen Sie den Mitarbeiter aus, und entfernen Sie den Mitarbeiter.
  4. Wechseln Sie zu [Azure Active Directory](https://ms.portal.azure.com/#blade/Microsoft_AAD_IAM/ActiveDirectoryMenuBlade/RegisteredApps), wählen Sie **die App-Registrierung** im linken Bereich aus, und suchen Sie Ihre Microsoft Azure Active Directory -App (Azure AD).
  5. Wählen Sie **"Besitzer**" im linken Bereich auf Microsoft Azure Active Directory (Azure AD) App-Verwaltungsseite aus.
  6. Wählen Sie den Mitarbeiter aus, und entfernen Sie den Mitarbeiter.

> [!NOTE]
> * Mitarbeiter, die Ihrem Projekt hinzugefügt wurden, erhalten keine Benachrichtigung. Project Besitzer muss Mitarbeiter offline benachrichtigen.
> * Azure-bezogene Berechtigungen müssen vom Azure-Abonnementadministrator auf Microsoft Azure Portal manuell festgelegt werden. Das Azure-Konto muss über eine Mitwirkenderolle für das Abonnement verfügen, damit Entwickler an der Bereitstellung und Bereitstellung des TeamsFx-Projekts zusammenarbeiten können.

## <a name="see-also"></a>Weitere Artikel

* [Bereitstellen von Cloudressourcen](provision.md)
* [Bereitstellen der Teams-App in der Cloud](deploy.md)
* [Verwalten mehrerer Umgebungen](TeamsFx-multi-env.md)
