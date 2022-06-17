---
title: Veröffentlichen von Teams-Apps mithilfe von Teams-Toolkits
author: zyxiaoyuer
description: In diesem Modul erfahren Sie, wie Sie Teams Apps mit Teams Toolkit veröffentlichen und in einzelnen Bereichen oder Querladen-Berechtigungen veröffentlichen.
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: 0ae6ab1f128eccae6df4fff20364f590106ab146
ms.sourcegitcommit: ca84b5fe5d3b97f377ce5cca41c48afa95496e28
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2022
ms.locfileid: "66142605"
---
# <a name="publish-teams-apps-using-teams-toolkit"></a>Veröffentlichen von Teams-Apps mithilfe von Teams-Toolkits

Nachdem Sie Ihre App erstellt haben, können Sie diese an verschiedene Bereiche verteilen, z. B. Einzelpersonen, Teams, Organisationen oder an alle. Die Verteilung hängt von mehreren Faktoren ab, einschließlich Bedürfnissen, geschäftlichen und technischen Anforderungen und Ihrem Ziel für die App. Die Verteilung in einen unterschiedlichen Bereich erfordert möglicherweise einen anderen Überprüfungsprozess. Im Allgemeinen gilt: Je größer der Bereich ist, desto mehr Überprüfungen muss die App aus Sicherheits- und Compliancegründen durchlaufen.

## <a name="prerequisite"></a>Voraussetzungen

* [Installieren des Teams-Toolkits](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension) Version v3.0.0+.

> [!TIP]
> Stellen Sie sicher, dass Sie über ein Teams-App-Projekt in VS Code verfügen.

## <a name="publish-to-individual-scope-or-sideload-permission"></a>Veröffentlichen in einen einzelnen Bereich oder Querladenberechtigung

Die Benutzer können eine benutzerdefinierte App zu Teams hinzufügen, indem sie ein App-Paket in einer ZIP-Datei direkt in ein Team oder in den persönlichen Kontext hochladen. Das Hinzufügen einer benutzerdefinierten App durch Hochladen eines App-Pakets wird als Querladen bezeichnet und ermöglicht es Ihnen, die App während der Entwicklung zu testen, bevor die App wie in den folgenden Szenarien erwähnt für eine breite Verteilung bereit ist:

* Testen und debuggen Sie eine App lokal.
* Erstellen Sie eine App für sich selbst, z. B. zum Automatisieren eines Workflows.
* Erstellen Sie eine App für eine kleine Gruppe von Benutzern, z. B. Ihre Arbeitsgruppe.

Sie können eine App nur für die interne Verwendung erstellen und für Ihr Team freigeben, ohne sie an den Teams-Appkatalog im Teams-App Store zu übermitteln.

**So kompilieren Sie Ihre App in eine *ZIP-App-Paketdatei**

Sie können das App-Paket kompilieren, indem Sie `Zip Teams metadata package` aus **BEREITSTELLUNG** in der Strukturansicht des Teams-Toolkits auswählen. Sie müssen zuerst `Provision in the cloud` ausführen. Das generierte App-Paket wird sich in `{your project folder}/build/appPackage/appPackage.{env}.zip` befinden.

Führen Sie die folgenden Schritte aus, um das App-Paket hochzuladen:

1. Wählen Sie im Teams-Client **Apps** in der linken Leiste aus.
2. Wählen Sie **Verwalten Ihrer Apps** aus.
3. Wählen Sie **App veröffentlichen** aus.

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/pub.png" alt-text="publish":::

4. Wählen Sie **Benutzerdefinierte App hochladen** aus:

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/uplo.png" alt-text="Hochladen":::

## <a name="publish-to-your-organization"></a>In Ihrer Organisation veröffentlichen

Wenn die App für die Verwendung in der Produktion bereit ist, können Sie die App mithilfe der Teams-App-Übermittlungs-API übermitteln, die von Graph-API aufgerufen wird, einer integrierten Entwicklungsumgebung (Integrated Development Environment, IDE), z. B. Microsoft Visual Studio Code, die mit dem Teams-Toolkit installiert ist. Sie können entweder **In Teams veröffentlichen** aus **BEREITSTELLUNG** in der Strukturansicht des Teams-Toolkit auswählen, oder lösen Sie **Teams: Veröffentlichen in Teams** über die Befehlspalette aus. Wählen Sie dann **Für Ihre Organisation installieren** aus:

![Für Ihre Organisation installieren](./images/installforyourorganization.png)

Die App ist im Bereich **Apps verwalten** des Microsoft Teams Admin Centers verfügbar, wo Sie und der Administrator sie überprüfen und genehmigen können.

Für Sie als Administrator ist **Apps verwalten** im [Microsoft Teams Admin Center](https://admin.teams.microsoft.com/policies/manage-apps) der Bereich, in dem Sie alle Teams-Apps für Ihre Organisation anzeigen und verwalten können. Sie können den Status und die Eigenschaften von Apps auf Organisationsebene sehen, neue benutzerdefinierte Apps im App Store Ihrer Organisation genehmigen oder hochladen, Apps auf Organisationsebene blockieren oder zulassen, Apps zu Teams hinzufügen, Dienste für Drittanbieter-Apps kaufen, von Apps angeforderte Berechtigungen anzeigen, Administratorzustimmung für Apps erteilen und [organisationsweite App-Einstellungen verwalten](https://admin.teams.microsoft.com/policies/manage-apps).

Das Teams-Toolkit für Visual Studio Code ist auf der Microsoft Teams-App-Übermittlungs-API aufbaut und ermöglicht es Ihnen, den Prozess „Übermittlung für Genehmigung“ für benutzerdefinierte Apps in Teams zu automatisieren.

> [!NOTE]
> Die App wird noch nicht im App Store Ihrer Organisation veröffentlicht. Mit diesem Schritt wird die App an das Microsoft Teams Admin Center übermittelt, wo Sie diese für die Veröffentlichung im App Store Ihrer Organisation genehmigen können.

## <a name="admin-approval-for-teams-apps"></a>Administratorgenehmigung für Teams-Apps

Der Administrator Ihres Teams-Mandanten kann dann zum Bereich **Apps verwalten** im Microsoft Teams Admin Center navigieren, er wechselt dazu im linken Navigationsbereich zu Teams-Apps > Apps verwalten. Sie können alle Teams-Apps für Ihre Organisation anzeigen. Im Widget „Ausstehende Genehmigung“ oben auf der Seite erfahren Sie, wann eine benutzerdefinierte App zur Genehmigung übermittelt wird.
In der Tabelle veröffentlicht eine neu übermittelte App automatisch den Status übermittelter und blockierter Apps. Sie können die Spalte mit dem Veröffentlichungsstatus in absteigender Reihenfolge sortieren, um die App zu finden:

 :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/admin-approval-for-teams-app-1.png" alt-text="Genehmigung":::

Wählen Sie den App-Namen aus, um zur Seite „App-Details“ zu wechseln. Auf der Registerkarte „Info“ können Sie Details zur App anzeigen, einschließlich Beschreibung, Status und App-ID:

 :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/about-submitted-app-1.png" alt-text="Übermittelte App":::

Führen Sie die folgenden Schritte aus, um die App zu veröffentlichen:

1. Wechseln Sie in der linken Navigationsleiste des Microsoft Teams Admin Centers zu Teams-Apps > **Apps verwalten**.
2. Wählen Sie den App-Namen aus, um zur Seite mit den App-Details zu wechseln, und wählen Sie dann im Statusfeld **Veröffentlichen** aus.
Nachdem Sie die App veröffentlicht haben, ändert sich der Veröffentlichungsstatus in „veröffentlicht“ und der Status wird automatisch in zulässig geändert.

## <a name="publish-to-microsoft-store"></a>Veröffentlichen im Microsoft Store

Sie können Ihre App direkt an den Store in Microsoft Teams verteilen und Millionen von Benutzern auf der ganzen Welt erreichen. Wenn Ihre App auch im Store vorgestellt wird, können Sie potenzielle Kunden sofort erreichen. Die Apps, die im Teams-Store veröffentlicht werden, werden auch automatisch auf Microsoft AppSource gelistet, dem offiziellen Marketplace für Microsoft 365-Apps und -Lösungen.

Weitere Informationen finden Sie unter ([Veröffentlichen Ihrer App im Microsoft Teams Store](../concepts/deploy-and-publish/appsource/publish.md#publish-your-app-to-the-microsoft-teams-store)).

## <a name="see-also"></a>Siehe auch

* [Verwalten mehrerer Umgebungen](TeamsFx-multi-env.md)
* [Zusammenarbeit mit anderen Entwicklern am Teams-Projekt](TeamsFx-collaboration.md)
