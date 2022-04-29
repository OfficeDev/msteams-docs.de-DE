---
title: Erweitern Sie Teams-Apps auf Microsoft 365 (Vorschau)
description: Erweitern Sie Ihre Teams-App-Erfahrungen auf andere häufig genutzte Bereiche von Microsoft 365
ms.date: 02/11/2022
ms.topic: overview
ms.custom: m365apps
ms.localizationpriority: high
ms.openlocfilehash: 66ba17a638fc57b47febef34bea769e39cdea7e3
ms.sourcegitcommit: f15bd0e90eafb00e00cf11183b129038de8354af
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/28/2022
ms.locfileid: "65111948"
---
# <a name="extend-teams-apps-across-microsoft-365"></a>Erweitern von Teams-Apps auf Microsoft 365

> [!NOTE]
> Diese frühe Entwicklervorschau soll Teams-Entwicklern mit vorhandenen Anwendungen die Möglichkeit geben, die neue Funktionalität auszuprobieren [und Feedback](/microsoftteams/platform/feedback) zu dieser Erweiterung der Teams-Entwicklerplattform in andere stark genutzte Bereiche des Microsoft 365-Ökosystems zu geben.

Sie können Ihre in Microsoft Office und Outlook ausgeführten Teams-Apps testen, indem Sie Ihren Code so aktualisieren, dass er das neue [Microsoft Teams JavaScript Client SDK v2 Preview](using-teams-client-sdk-preview.md) und das Microsoft Teams [Developer Preview Manifest verwendet](../resources/schema/manifest-schema-dev-preview.md).

Mit dieser Vorschau können Sie:

- Erweitern Sie vorhandene [persönliche Registerkarten von Teams auf](/microsoftteams/platform/tabs/how-to/create-personal-tab) Outlook für den Desktop und im Web sowie Office im Web (office.com).
- Erweitern Sie vorhandene [suchbasierte Nachrichtenerweiterungen von Teams](/microsoftteams/platform/messaging-extensions/how-to/search-commands/define-search-command) auf Outlook für den Desktop und im Web.

Verwenden Sie für Feedback und Probleme weiterhin die relevanten Community-Kanäle für [Microsoft Teams-Entwickler](/microsoftteams/platform/feedback).

## <a name="teams-personal-tabs-in-office-and-outlook"></a>Persönliche Registerkarten für Teams in Office und Outlook

Mit dieser Vorschau können Sie eine Anwendung für persönliche Registerkarten von Teams so erweitern, dass sie sowohl in Outlook auf dem Windows-Desktop und im Web als auch in Office im Web ausgeführt werden kann.

Nach dem Querladen in Teams wird Ihre persönliche Registerkarte als eine Ihrer installierten Apps in Outlook und Office angezeigt.

:::image type="content" source="images/outlook-office-teams-personal-tab.png" alt-text="Persönliche Registerkarte, die in Outlook, Office und Teams ausgeführt wird":::

## <a name="teams-message-extensions-in-outlook"></a>Teams-Nachrichtenerweiterungen in Outlook

Mit dieser Vorschau können Sie Ihre suchbasierten Teams-Nachrichtenerweiterungen auf Outlook im Web und Windows-Desktop erweitern, sodass Kunden zusätzlich zu Microsoft Teams-Clients Ergebnisse über den Bereich zum Verfassen von Nachrichten in Outlook suchen und freigeben können.

Nach dem Querladen in Teams wird Ihre Nachrichtenerweiterung als eine Ihrer installierten Apps im Outlook-Bereich zum Verfassen von Nachrichten angezeigt.

:::image type="content" source="images/outlook-teams-messaging-ext.png" alt-text="Nachrichtenerweiterung, die in Outlook und Teams ausgeführt wird":::

## <a name="next-steps"></a>Nächste Schritte

Richten Sie Ihre Entwicklungsumgebung zum Erweitern von Teams-Apps auf Microsoft 365 ein:

> [!div class="nextstepaction"]
> [Erforderliche Komponenten installieren](prerequisites.md)
