---
title: Erstellen einer neuen Teams-App mit dem Teams-Toolkit
author: zyxiaoyuer
description: Erstellen einer neuen Teams-App mithilfe des Teams-Toolkits
ms.author: surbhigupta
ms.localizationpriority: high
ms.topic: overview
ms.date: 03/14/2022
ms.openlocfilehash: 5da4a0ada6e116a22957a6f1f1b1f2f281501e2a
ms.sourcegitcommit: 80edf3c964bb47a2ee13f9eda4334ad19e21f331
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2022
ms.locfileid: "65654475"
---
# <a name="create-a-new-teams-app-using-teams-toolkit"></a>Erstellen einer neuen Teams-App mit dem Teams-Toolkit

Um eine neue Teams-App mithilfe des Teams-Toolkits zu erstellen, können Sie eine der folgenden Optionen auswählen:

* [Erstellen einer neuen Teams-App](create-new-project.md#create-a-new-teams-app)
* [Anzeigebeispiele](create-new-project.md#create-a-new-teams-app-using-view-samples)

### <a name="create-a-new-teams-app"></a>Erstellen einer neuen Teams-App

1. Öffnen Sie Visual Studio Code.
1. Wählen Sie das Teams-Toolkit-Symbol :::image type="icon" source="../assets/images/teams-toolkit-v2/teams-toolkit-sidebar-icon.PNG" border="true"::: in der Visual Studio Code-Randleiste aus.
1. Wählen Sie **Neue Microsoft Teams-App erstellen** aus.

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams-toolkit-sidebar.png" alt-text="Teams Toolkit-Randleiste":::

1. Sie können **Eine neue Teams-App erstellen** oder **Aus einem Beispiel starten** auswählen.
   
   :::image type="content" source="../assets/images/teams-toolkit-v2/select-create-app.png" alt-text="App erstellen":::
   
1. Wenn Sie **Eine neue Teams-App erstellen** auswählen, wird die folgende Abbildung mit Vorlagen aus drei Kategorien angezeigt: Szenariobasierte Teams-App, einfache Teams-App und erweiterte Teams-Apps in Microsoft 365: 

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams-capabilities.png" alt-text="Funktionen für Teams-App":::

1. Wählen Sie mindestens eine Option aus, um mit dem Erstellen der Teams-App zu beginnen.


### <a name="create-a-new-teams-app-using-view-samples"></a>Erstellen einer neuen Teams-App mithilfe von Anzeigebeispielen

Sie können eine neue App erstellen, indem Sie **Anzeigebeispiele** erkunden und ein vorhandenes Beispiel auswählen. Das ausgewählte Beispiel verfügt möglicherweise bereits über einige Funktionen, z. B. eine Aufgabenliste mit einem Azure-Back-End oder eine Integration in das Microsoft Graph-Toolkit.

 1. Öffnen Sie das **Teams-Toolkit** aus Microsoft Visual Studio Code.
 1. Wählen Sie den Abschnitt **ENTWICKLUNG** in der Baumansicht aus.
 1. Wählen Sie **Anzeigebeispiele** aus. 

    :::image type="content" source="../assets/images/teams-toolkit-v2/view-samples.png" alt-text="Anzeigebeispiele":::

    Der Beispielkatalog wird wie in der folgenden Abbildung dargestellt angezeigt:
   
    :::image type="content" source="../assets/images/teams-toolkit-v2/sample-gallery.png" alt-text="Beispielkatalog":::

  Sie können den Beispielkatalog wie folgt erkunden:

  1. Wählen Sie ein Beispiel aus, um detaillierte Informationen zu durchsuchen.
  1. Wählen Sie auf der Informationsseite jedes Beispiels **Erstellen** aus, um es herunterzuladen. 
  1. Führen Sie Ihre App lokal oder remote aus, um eine Vorschau im Teams-Webclient anzuzeigen, indem Sie die Anweisungen befolgen, die nach dem Herunterladen des Beispiels automatisch geöffnet werden.
  1. Wenn Sie die Beispiele nicht herunterladen möchten, können Sie **Auf GitHub anzeigen** auswählen, um das Beispiel im GitHub-Beispielrepository zu öffnen und den Quellcode durchzusuchen.

## <a name="step-by-step-guides-using-teams-toolkit"></a>Schritt-für-Schritt-Anleitungen mithilfe des Teams-Toolkits

* [Erstellen einer Teams-App mit Blazor](../sbs-gs-blazorupdate.yml)
* [Erstellen einer Teams-App mit JavaScript, mithilfe von React](../sbs-gs-javascript.yml)
* [Erstellen einer Teams-App mit SPFx](../sbs-gs-spfx.yml)
* [Erstellen einer Teams-App mit C# oder .NET](../sbs-gs-csharp.yml)
* Benachrichtigung an Teams senden 
* Befehlsbot erstellen

## <a name="see-also"></a>Siehe auch

* [Bereitstellen von Cloudressourcen](provision.md)
* [Bereitstellen der Teams-App in der Cloud](deploy.md)
* [Veröffentlichen Ihrer Teams-App](../concepts/deploy-and-publish/appsource/publish.md)
* [Verwalten mehrerer Umgebungen](TeamsFx-multi-env.md)
* [Zusammenarbeit mit anderen Entwicklern am Teams-Projekt](TeamsFx-collaboration.md)