---
title: Erweitern Teams Apps über Microsoft 365 hinweg (Vorschau)
description: Erweitern der Teams App-Umgebungen auf andere bereiche mit hoher Microsoft 365
ms.date: 02/11/2022
ms.topic: overview
ms.custom: m365apps
ms.localizationpriority: medium
ms.openlocfilehash: 013bb773897965d51daaa485459eec78478292b3
ms.sourcegitcommit: 0117c4e750a388a37cc189bba8fc0deafc3fd230
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2022
ms.locfileid: "65104343"
---
# <a name="extend-teams-apps-across-microsoft-365"></a>Erweitern von Teams-Apps auf Microsoft 365

> [!NOTE]
> Diese frühe Entwicklervorschau soll Teams Entwicklern mit vorhandenen Anwendungen die Möglichkeit bieten, die neue Funktionalität auszuprobieren und Feedback zu dieser Erweiterung der Teams-Entwicklerplattform in andere bereiche mit hoher Nutzung des Microsoft 365-Ökosystems [zu geben](/microsoftteams/platform/feedback).

Sie können Ihre Teams-Apps testen, die in Microsoft Office und Outlook ausgeführt werden, indem Sie Ihren Code aktualisieren, um das neue [Microsoft Teams javaScript-Client-SDK v2 Preview](using-teams-client-sdk-preview.md) und Microsoft Teams [Developer Preview-Manifest](../resources/schema/manifest-schema-dev-preview.md) zu verwenden.

Mit dieser Vorschau können Sie:

- Erweitern vorhandener Teams [persönlichen Registerkarten](/microsoftteams/platform/tabs/how-to/create-personal-tab) auf Outlook für Desktop und im Web sowie Office im Web (office.com).
- Erweitern Sie vorhandene Teams [suchbasierte Nachrichtenerweiterungen](/microsoftteams/platform/messaging-extensions/how-to/search-commands/define-search-command) auf Outlook für Desktop und im Web.

Verwenden Sie für Feedback und Probleme weiterhin die relevanten [Microsoft Teams Entwickler-Communitykanäle](/microsoftteams/platform/feedback).

## <a name="teams-personal-tabs-in-office-and-outlook"></a>Teams persönliche Registerkarten in Office und Outlook

Mit dieser Vorschau können Sie eine Teams persönliche Registerkartenanwendung so erweitern, dass sie sowohl in Outlook auf Windows Desktop und im Web als auch Office im Web ausgeführt wird.

Nach dem Querladen in Teams wird Ihre persönliche Registerkarte als eine Ihrer installierten Apps in Outlook und Office angezeigt.

:::image type="content" source="images/outlook-office-teams-personal-tab.png" alt-text="Persönliche Registerkarte, die in Outlook, Office und Teams ausgeführt wird":::

## <a name="teams-message-extensions-in-outlook"></a>Teams von Nachrichtenerweiterungen in Outlook

Mit dieser Vorschau können Sie Ihre suchbasierten Teams-Nachrichtenerweiterungen auf Outlook im Web und Windows Desktop erweitern, sodass Kunden neben Microsoft Teams Clients auch Ergebnisse über den Nachrichtenbereich "Verfassen" von Outlook durchsuchen und freigeben können.

Nach dem Querladen in Teams wird Ihre Nachrichtenerweiterung als eine Ihrer installierten Apps im Outlook Nachrichtenbereich zum Verfassen angezeigt.

:::image type="content" source="images/outlook-teams-messaging-ext.png" alt-text="Nachrichtenerweiterung, die in Outlook und Teams ausgeführt wird":::

## <a name="next-steps"></a>Nächste Schritte

Richten Sie Ihre Entwicklungsumgebung ein, um Teams Apps auf Microsoft 365 zu erweitern:

> [!div class="nextstepaction"]
> [Erforderliche Komponenten installieren](prerequisites.md)
