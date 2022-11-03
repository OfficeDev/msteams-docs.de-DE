---
title: Veröffentlichen von Teams-Apps mithilfe von Teams-Toolkits
author: zyxiaoyuer
description: In diesem Modul erfahren Sie, wie Sie Teams-Apps mithilfe des Teams-Toolkits veröffentlichen und in einem einzelnen Bereich oder einer Berechtigung zum Querladen veröffentlichen.
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: d6333afb6d62fc832310c165c30970254998e91e
ms.sourcegitcommit: c3601696cced9aadc764f1e734646ee7711f154c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/03/2022
ms.locfileid: "68833156"
---
# <a name="publish-teams-apps-using-teams-toolkit"></a>Veröffentlichen von Teams-Apps mithilfe von Teams-Toolkits

Nachdem Sie Ihre App erstellt haben, können Sie diese an verschiedene Bereiche verteilen, z. B. Einzelpersonen, Teams, Organisationen oder an alle. Die Verteilung hängt von mehreren Faktoren ab, z. B. anforderungen, geschäftlichen und technischen Anforderungen und Ihrem Ziel für die App. Die Verteilung in einen unterschiedlichen Bereich erfordert möglicherweise einen anderen Überprüfungsprozess. Im Allgemeinen gilt: Je größer der Bereich ist, desto mehr Überprüfungen muss die App aus Sicherheits- und Compliancegründen durchlaufen.

:::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/publish-flow.png" alt-text="Veröffentlichungsflow":::

Hier erfahren Sie, was Sie in diesem Abschnitt lernen:

* [Veröffentlichen in einen einzelnen Bereich oder Querladenberechtigung](#publish-to-individual-scope-or-sideload-permission)
* [In Ihrer Organisation veröffentlichen](#publish-to-your-organization)
* [Veröffentlichen im Microsoft Teams Store](#publish-to-microsoft-teams-store)

## <a name="prerequisites"></a>Voraussetzungen

* Erstellen Sie Ihr [App-Paket](~/concepts/build-and-test/apps-package.md) und [überprüfen Sie es](https://dev.teams.microsoft.com/appvalidation.html) auf Fehler.
* Aktivieren Sie das [Hochladen einer benutzerdefinierter App](~/concepts/build-and-test/prepare-your-o365-tenant.md#enable-custom-teams-apps-and-turn-on-custom-app-uploading) in Teams.
* Stellen Sie sicher, dass Ihre App ausgeführt wird und über HTTPs zugänglich ist.
* Stellen Sie sicher, dass Sie eine Reihe von Richtlinien in der Veröffentlichung Ihrer App im Microsoft Teams Store befolgt haben, um Ihre App zu veröffentlichen.

## <a name="publish-to-individual-scope-or-sideload-permission"></a>Veröffentlichen in einen einzelnen Bereich oder Querladenberechtigung

Sie können Teams eine benutzerdefinierte App hinzufügen, indem Sie ein [App-Paket](../concepts/build-and-test/apps-package.md) in einer *.zip-Datei direkt in ein Team oder im persönlichen Kontext hochladen. Das Hinzufügen einer benutzerdefinierten App durch Hochladen eines App-Pakets wird als Querladen bezeichnet. Es ermöglicht Ihnen, die App zu testen, während sie in Teams hochgeladen wird. Sie können Eine App in den folgenden Szenarien erstellen und testen:

* Testen und debuggen Sie eine App lokal.
* Erstellen Sie eine App für sich selbst, z. B. zum Automatisieren eines Workflows.
* Erstellen Sie eine App für eine kleine Gruppe von Benutzern, z. B. Ihre Arbeitsgruppe.

Sie können eine App nur für die interne Verwendung erstellen und für Ihr Team freigeben, ohne sie an den Teams-Appkatalog im Teams-App Store zu übermitteln. Weitere Informationen finden Sie unter [Hochladen Ihrer App in Teams](../concepts/deploy-and-publish/apps-upload.md).

### <a name="to-build-your-app-to-zip-app-package-file"></a>So erstellen Sie Ihre App als ZIP-App-Paketdatei

Sie müssen zuerst ausführen `Provision in the cloud` , bevor Sie das App-Paket erstellen. Die folgenden Schritte helfen Ihnen beim Erstellen des App-Pakets.

* Wählen Sie unter **BEREITSTELLUNG** die Option **Teams-Metadatenpaket zippen** aus.<br>
    Das generierte App-Paket wird sich in `{your project folder}/build/appPackage/appPackage.{env}.zip` befinden.

### <a name="to-upload-app-package"></a>So laden Sie ein App-Paket hoch

Führen Sie die folgenden Schritte aus, um das App-Paket hochzuladen:

1. Wählen Sie im Teams-Client **Apps** > **Verwalten Ihrer Apps** > **eine App hochladen aus**.

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/publish1.png" alt-text="Veröffentlichen einer App":::

   **Das Fenster "App hochladen** " wird angezeigt.

2. Wählen Sie **Benutzerdefinierte App hochladen** aus.

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/upload.png" alt-text="Hochladen einer App":::

   Jetzt wird die App quer in den Teams-Client geladen, und Sie können sie hinzufügen und anzeigen.

## <a name="publish-to-your-organization"></a>In Ihrer Organisation veröffentlichen

Wenn die App für die Verwendung in der Produktion bereit ist, können Sie die App mithilfe der Teams-App-Übermittlungs-API übermitteln, die von Graph-API aufgerufen wird. Die Teams-App-Übermittlungs-API ist eine integrierte Entwicklungsumgebung (IDE), z. B. Microsoft Visual Studio Code, die mit dem Teams-Toolkit installiert ist. Die folgenden Schritte helfen Ihnen beim Veröffentlichen der App in Ihrer Organisation:

* [Veröffentlichen aus dem Teams-Toolkit](#publish-from-teams-toolkit)
* [Genehmigen im Admin Center](#approve-on-admin-center)

### <a name="publish-from-teams-toolkit"></a>Veröffentlichen aus dem Teams-Toolkit

Die folgenden Schritte helfen Ihnen beim Veröffentlichen der App aus dem Teams Toolkit:

1. Sie können Ihre Teams-App auf eine der folgenden Arten veröffentlichen:
     * Wählen Sie in der Strukturansicht des Teams-Toolkits unter **BEREITSTELLUNG** die Option **In Teams veröffentlichen** aus.
     * Geben Sie trigger **Teams: Veröffentlichen in Teams** aus der Befehlspalette ein.

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/select-publish.png" alt-text="Wählen Sie Veröffentlichen aus.":::

1. Wählen Sie **Installieren für Ihre Organisation** aus.

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/installforyourorganization.png" alt-text="Für Ihre Organisation installieren":::

   Nun wurde die App erfolgreich im Verwaltungsportal veröffentlicht, und der folgende Hinweis wird angezeigt:

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/confirm-publish.png" alt-text="Bestätigen der Veröffentlichung":::

Jetzt ist die App im Microsoft Teams Admin Center zum **Verwalten von Apps** verfügbar, wo Sie und der Administrator sie überprüfen und genehmigen können.

> [!NOTE]
> Die App wird noch nicht im App Store Ihrer Organisation veröffentlicht. Mit diesem Schritt wird die App an das Microsoft Teams Admin Center übermittelt, wo Sie diese für die Veröffentlichung im App Store Ihrer Organisation genehmigen können.

### <a name="approve-on-admin-center"></a>Genehmigen im Admin Center

Das Teams-Toolkit für Visual Studio Code basiert auf der Teams-App-Übermittlungs-API und ermöglicht es Ihnen, den Genehmigungsprozess für benutzerdefinierte Apps in Teams zu automatisieren.

  > [!NOTE]
  > Stellen Sie sicher, dass Sie über ein Teams-App-Projekt in VS Code verfügen. Für Sie als Administrator ist **Apps verwalten** im [Microsoft Teams Admin Center](https://admin.teams.microsoft.com/policies/manage-apps) der Bereich, in dem Sie alle Teams-Apps für Ihre Organisation anzeigen und verwalten können. Sie können die folgenden Aktivitäten im Admin Center ausführen:
  >
  > * Sehen Sie sich den Status und die Eigenschaften von Apps auf Organisationsebene an.
  > * Genehmigen Sie neue benutzerdefinierte Apps, oder laden Sie sie in den App Store Ihrer Organisation hoch.
  > * Blockieren oder Zulassen von Apps auf Organisationsebene.
  > * Fügen Sie Apps zu Teams hinzu.
  > * Erwerben sie Dienste für Drittanbieter-Apps.
  > * Anzeigen von Berechtigungen, die von Apps angefordert werden.
  > * Erteilen Sie Apps die Administratoreinwilligung.
  > * [Organisationsweite App-Einstellungen verwalten](https://admin.teams.microsoft.com/policies/manage-apps).

Die folgenden Schritte helfen Ihnen bei der Genehmigung über Admin Center:

1. Wählen Sie **Zum Verwaltungsportal wechseln** aus.

1. Wählen Sie das :::image type="icon" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/Showall.PNG"::: Symbol > **Teams-App** > **Apps verwalten** aus.

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/select-manage-apps.png" alt-text="Wählen Sie Apps verwalten aus.":::

   Sie können alle Teams-Apps für Ihre Organisation anzeigen.

   Im Widget „Ausstehende Genehmigung“ oben auf der Seite erfahren Sie, wann eine benutzerdefinierte App zur Genehmigung übermittelt wird. In der Tabelle veröffentlicht eine neu übermittelte App automatisch den Status der übermittelten und blockierten Apps. Sie können die Spalte für den Veröffentlichungsstatus in absteigender Reihenfolge sortieren, um die App zu finden.

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/admin-approval-for-teams-app-1.png" alt-text="Genehmigung":::

1. Wählen Sie den App-Namen aus, um zur Seite „App-Details“ zu wechseln. Auf der Registerkarte **Info** können Sie Details zur App anzeigen, einschließlich Beschreibung, Status und App-ID.

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/about-submitted-app-1.png" alt-text="Übermittelte App":::

1. Wählen Sie die Dropdownliste Status aus, und ändern Sie von **Übermittelt** in **Veröffentlichen**.

   Nachdem Sie die App veröffentlicht haben, ändert sich der Veröffentlichungsstatus in „veröffentlicht“ und der Status wird automatisch in zulässig geändert.

   Weitere Informationen finden Sie unter [Veröffentlichen in Ihrer Organisation](/MicrosoftTeams/manage-apps?toc=%2Fmicrosoftteams%2Fplatform%2Ftoc.json&bc=%2Fmicrosoftteams%2Fplatform%2Fbreadcrumb%2Ftoc.json).

## <a name="publish-to-microsoft-teams-store"></a>Veröffentlichen im Microsoft Teams Store

Sie können Ihre App direkt an den Store in Microsoft Teams verteilen und Millionen von Benutzern auf der ganzen Welt erreichen. Wenn Ihre App auch im Store vorgestellt wird, können Sie potenzielle Kunden sofort erreichen. Die Apps, die im Teams-Store veröffentlicht werden, werden auch automatisch auf Microsoft AppSource gelistet, dem offiziellen Marketplace für Microsoft 365-Apps und -Lösungen.

Weitere Informationen finden Sie unter [Veröffentlichen Ihrer App im Microsoft Teams Store](../concepts/deploy-and-publish/appsource/publish.md#publish-your-app-to-the-microsoft-teams-store).

## <a name="see-also"></a>Siehe auch

* [Verteilen Ihrer Microsoft Teams-App](../concepts/deploy-and-publish/apps-publish-overview.md)
* [Teams-App-Paket erstellen](../concepts/build-and-test/apps-package.md)
* [Vorbereiten Ihres Microsoft 365-Mandanten](../concepts/build-and-test/prepare-your-o365-tenant.md)
* [Veröffentlichen Sie Ihre App im Microsoft Teams Store](../concepts/deploy-and-publish/appsource/publish.md)
* [Hochladen Ihrer App in Teams](../concepts/deploy-and-publish/apps-upload.md)
* [Verwalten der Teams-App im Microsoft Teams Admin Center](/MicrosoftTeams/manage-apps?toc=%2Fmicrosoftteams%2Fplatform%2Ftoc.json&bc=%2Fmicrosoftteams%2Fplatform%2Fbreadcrumb%2Ftoc.json)
