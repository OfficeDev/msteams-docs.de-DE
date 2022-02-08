---
title: Veröffentlichen von Teams-Apps mithilfe von Teams-Toolkits
author: zyxiaoyuer
description: Veröffentlichen Teams Apps
ms.author: yanjiang
ms.localizationpriority: medium
ms.topic: overview
ms.date: 11/29/2021
ms.openlocfilehash: d232ac1d0ac96d46aa5f265f3fedd7b65afb3a86
ms.sourcegitcommit: c66da76fb766df6270095265e1da8c49a3afd195
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/07/2022
ms.locfileid: "62435761"
---
# <a name="publish-teams-apps-using-teams-toolkit"></a>Veröffentlichen von Teams-Apps mithilfe von Teams-Toolkits

Nach dem Erstellen der App können Sie Ihre App auf einen anderen Bereich verteilen, z. B. einzeln, team, organisation oder jeder. Die Verteilung hängt von mehreren Faktoren ab, einschließlich Anforderungen, geschäftlichen und technischen Anforderungen und Ihrem Ziel für die App. Die Verteilung auf einen anderen Bereich erfordert möglicherweise einen anderen Überprüfungsprozess. Im Allgemeinen gilt: Je größer der Bereich, desto mehr Überprüfungen muss die App im Hinblick auf Sicherheits- und Compliancebedenken durchlaufen.

## <a name="prerequisite"></a>Voraussetzungen

* [Installieren Sie Teams Toolkit](https://marketplace.visualstudio.com/items?itemName=TeamsDevApp.ms-teams-vscode-extension) Version v3.0.0+.

> [!TIP]
> Stellen Sie sicher, dass Sie über Teams App-Projekt im VS-Code verfügen.

## <a name="publish-to-individual-scope-or-sideload-permission"></a>Veröffentlichen in einzelnem Bereich oder Querladen der Berechtigung

Die Benutzer können Teams benutzerdefinierte Apps hinzufügen, indem sie ein App-Paket in einer *.zip-Datei direkt in ein Team oder in einen persönlichen Kontext hochladen. Das Hinzufügen einer benutzerdefinierten App durch Hochladen eines App-Pakets wird als Querladen bezeichnet und ermöglicht es Ihnen, die App während der Entwicklung zu testen, bevor die App wie in den folgenden Szenarien erwähnt umfassend verteilt werden kann:

* Testen und debuggen Sie eine App lokal.
* Erstellen Sie eine App für sich selbst, z. B. zum Automatisieren eines Workflows.
* Erstellen Sie eine App für kleine Benutzer, z. B. Ihre Arbeitsgruppe.

Sie können eine App nur für die interne Verwendung erstellen und für Ihr Team freigeben, ohne sie an den Teams App-Katalog im Teams App Store zu übermitteln.

**So erstellen Sie Ihre App auf *.zip App-Paketdatei**

Sie können das App-Paket erstellen, indem Sie in der Strukturansicht von Teams Toolkit die Option **"BEREITSTELLUNG**" auswählen`Zip Teams metadata package`. Sie müssen zuerst ausführen `Provision in the cloud` . Das generierte App-Paket befindet sich in `{your project folder}/build/appPackage/appPackage.{env}.zip`.

Führen Sie die folgenden Schritte aus, um das App-Paket hochzuladen:

1. Wählen Sie im Teams Client in der linken Leiste **"Apps**" aus.
2. Wählen Sie **"Apps verwalten" aus**.
3. Auswählen **der Veröffentlichung einer App**

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/pub.png" alt-text="publish":::

4. Wählen Sie **Hochladen einer benutzerdefinierten App** aus:

   :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/uplo.png" alt-text="Hochladen":::

## <a name="publish-to-your-organization"></a>In Ihrer Organisation veröffentlichen 

Wenn die App für die Verwendung in der Produktion bereit ist, können Sie die App mithilfe der Teams App-Übermittlungs-API übermitteln, die von Graph API aufgerufen wird, einer integrierten Entwicklungsumgebung (Integrated Development Environment, IDE), z. B. Microsoft Visual Studio Code, der mit Teams Toolkit installiert ist. Sie können entweder in **der Strukturansicht** von Teams Toolkit die Option "**Veröffentlichen in Teams**" auswählen oder **Teams auslösen: Veröffentlichen in Teams** über die Befehlspalette. Wählen Sie dann **"Installieren" für Ihre Organisation** aus:

![Installieren für Ihre Organisation](./images/installforyourorganization.png)

Die App ist im **Manage apps** of Microsoft Teams Admin Center verfügbar, in dem Sie und der Administrator sie überprüfen und genehmigen können.

Als Administrator können Sie im [Microsoft Teams Admin Center](https://admin.teams.microsoft.com/policies/manage-apps) **Apps verwalten**, in denen Sie alle Teams-Apps für Ihre Organisation anzeigen und verwalten können. Sie können den Status und die Eigenschaften von Apps auf Organisationsebene anzeigen, neue benutzerdefinierte Apps im App Store Ihrer Organisation genehmigen oder hochladen, Apps auf Organisationsebene blockieren oder zulassen, Apps zu Teams hinzufügen, Dienste für Drittanbieter-Apps kaufen, von Apps angeforderte Berechtigungen anzeigen, Apps Administratorzustimmung erteilen und [organisationsweite App-Einstellungen verwalten](https://admin.teams.microsoft.com/policies/manage-apps).

Teams Toolkit für Visual Studio Code auf der Teams App-Übermittlungs-API aufbauen und ermöglicht es Ihnen, den Übermittlungs-zu-Genehmigungsprozess für benutzerdefinierte Apps auf Teams zu automatisieren.

> [!NOTE]
> Die App wird noch nicht im App Store Ihrer Organisation veröffentlicht. Der Schritt sendet die App an das Microsoft Teams Admin Center, wo Sie sie für die Veröffentlichung im App Store Ihrer Organisation genehmigen können.

## <a name="admin-approval-for-teams-apps"></a>Administratorgenehmigung für Teams-Apps

Der Administrator Ihres Teams Mandanten kann dann im Microsoft Teams Admin Center zu "**Apps verwalten**" wechseln. Wechseln Sie in der linken Navigationsleiste zu Teams Apps > Verwalten von Apps. Sie können alle Teams-Apps für Ihre Organisation anzeigen. Im Widget "Genehmigung ausstehend" oben auf der Seite erfahren Sie, wann eine benutzerdefinierte App zur Genehmigung übermittelt wird.
In der Tabelle veröffentlicht eine neu übermittelte App automatisch den Status übermittelter und blockierter Apps. Sie können die Veröffentlichungsstatusspalte in absteigender Reihenfolge sortieren, um die App zu finden:

 :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/admin-approval-for-teams-app-1.png" alt-text="Genehmigung":::

Wählen Sie den App-Namen aus, um zur Seite "App-Details" zu wechseln. Auf der Registerkarte "Info" können Sie Details zur App anzeigen, einschließlich Beschreibung, Status und App-ID:

 :::image type="content" source="../assets/images/teams-toolkit-v2/teams toolkit fundamentals/about-submitted-app-1.png" alt-text="übermittelte App":::

Führen Sie die folgenden Schritte aus, um die App zu veröffentlichen:

1. Wechseln Sie in der linken Navigationsleiste des Microsoft Teams Admin Centers zu Teams Apps > **Verwalten von Apps**.
2. Wählen Sie den App-Namen aus, um zur Seite "App-Details" zu wechseln, und wählen Sie dann im Statusfeld " **Veröffentlichen**" aus.
Nachdem Sie die App veröffentlicht haben, ändert sich der Veröffentlichungsstatus in "Veröffentlicht", und der Status wird automatisch in "Zulässig" geändert.

## <a name="publish-to-microsoft-store"></a>Veröffentlichen im Microsoft Store

Sie können Ihre App direkt an den Store innerhalb Microsoft Teams verteilen und Millionen von Benutzern auf der ganzen Welt erreichen. Wenn Ihre App auch im Store enthalten ist, können Sie potenzielle Kunden sofort erreichen. Die im Teams Store veröffentlichten Apps werden auch automatisch in Microsoft AppSource aufgeführt, dem offiziellen Marketplace für Microsoft 365 Apps und Lösungen.

Weitere Informationen finden Sie unter ["Veröffentlichen im Microsoft Teams Store]([Publish your app to the Microsoft Teams store](../concepts/deploy-and-publish/appsource/publish.md#publish-your-app-to-the-microsoft-teams-store))"

## <a name="see-also"></a>Siehe auch

* [Verwalten mehrerer Umgebungen](TeamsFx-multi-env.md)
* [Zusammenarbeit mit anderen Entwicklern an Teams Projekt](TeamsFx-collaboration.md)