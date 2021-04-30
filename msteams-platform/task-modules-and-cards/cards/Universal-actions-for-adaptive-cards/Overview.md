---
title: Übersicht über universelle Aktionen für adaptive Karten
description: Eine kurze Übersicht über universelle Aktionen für adaptive Karten.
ms.topic: overview
localization_priority: Normal
ms.openlocfilehash: f0adf3d1a01262ff9cbdf14128c9ffe088ae8072
ms.sourcegitcommit: 1256639fa424e3833b44207ce847a245824d48e6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/29/2021
ms.locfileid: "52088915"
---
# <a name="universal-actions-for-adaptive-cards"></a>Universelle Aktionen für adaptive Karten

Universelle Aktionen für adaptive Karten entwickelten sich aus entwicklerfeedback, dass das Layout und Rendering für adaptive Karten zwar universell war, die Aktionsbehandlung jedoch nicht war. Auch wenn ein Entwickler dieselbe Karte an verschiedene Orte senden wollte, muss er die Aktionen anders behandeln.

Universelle Aktionen für adaptive Karten bietet den Bot als allgemeines Back-End für die Behandlung von Aktionen und führt einen neuen Aktionstyp ein, der appsübergreifend funktioniert, z. B. `Action.Execute` Teams und Outlook.

Dieses Dokument hilft Ihnen zu verstehen, wie Sie das Modell für universelle Aktionen verwenden können, um die Benutzererfahrung bei der Interaktion mit adaptiven Karten über Plattformen und Anwendungen hinweg zu verbessern.

> [!NOTE]
> Unterstützung für universelle Aktionen für adaptive Karten ist nur für Karten verfügbar, die vom Bot gesendet werden. Unterstützung für Karten, die über das Verfassenfeld gesendet werden, und link-Entf?ndungskarten werden in Kürze verfügbar sein.

## <a name="enhance-user-experiences-with-universal-actions-for-adaptive-cards"></a>Verbessern der Benutzererfahrung mit universellen Aktionen für adaptive Karten

Universelle Aktionen für adaptive Karten verbessern die Benutzerfreundlichkeit, indem die folgenden Szenarien aktiviert werden:

* [Universelle Aktionen](#universal-actions)
* [Benutzerspezifische Ansichten](#user-specific-views)
* [Sequenzielle Workflowunterstützung](#sequential-workflow-support)
* [Aktuelle Ansichten](#up-to-date-views)

### <a name="universal-actions"></a>Universelle Aktionen

Vor den universellen Aktionen für adaptive Karten haben verschiedene Hosts unterschiedliche Aktionsmodelle bereitgestellt:

* Teams oder Bots verwendet , ein Ansatz, der das tatsächliche Kommunikationsmodell auf `Action.Submit` den zugrunde liegenden Kanal ausdebt.
* Outlook `Action.Http` verwendet, um mit dem Back-End-Dienst zu kommunizieren, der explizit in der Nutzlast der adaptiven Karte angegeben ist.

Die folgende Abbildung zeigt das aktuelle inkonsistente Aktionsmodell:

:::image type="content" source="~/assets/images/adaptive-cards/current-teams-outlook-action-model.png" alt-text="Inkonsistentes Aktionsmodell":::

Mit den universellen Aktionen für adaptive Karten können Sie aktionen für `Action.Execute` verschiedene Plattformen verwenden. `Action.Execute`funktioniert über Hubs hinweg, Teams und Outlook. Darüber hinaus kann eine adaptive Karte als Antwort für eine `Action.Execute` ausgelöste Aufrufanforderung zurückgegeben werden.

Die folgende Abbildung zeigt das neue Universelle Aktionsmodell:

:::image type="content" source="~/assets/images/adaptive-cards/universal-action-model.png" alt-text="Neue universelle Aktionen für adaptive Karten":::

Sie können nun dieselbe Karte sowohl an Teams als auch Outlook senden und sie mithilfe des zugrunde liegenden Bots synchron halten. Jede Aktion, die auf beiden Plattformen ergriffen wird, wird mit diesem Build einmal für die andere *übernommen,* und das Modell wird an beliebiger Stelle (Universelle Aktionen für adaptive Karten) bereitgestellt.

Die folgende Abbildung zeigt die universellen Aktionen für adaptive Karten für Teams und Outlook:

:::image type="content" source="~/assets/images/adaptive-cards/universal-bots-teams-outlook.png" alt-text="Gleiche Karte für Teams und Outlook":::

### <a name="user-specific-views"></a>Benutzerspezifische Ansichten

Heute sieht jeder Benutzer im Teams oder Kanal genau die gleichen Ansichts- und Schaltflächenaktionen auf der adaptiven Karte. In bestimmten Szenarien ist es jedoch erforderlich, dass bestimmte Benutzer unterschiedlich handeln und zugriff auf unterschiedliche Informationen innerhalb desselben Chats oder Kanals haben.

Wenn Sie beispielsweise eine Vorfallberichtskarte in einem Chat oder Kanal senden, muss nur dem Benutzer, dem der Vorfall zugewiesen ist, eine **Schaltfläche Auflösen angezeigt** werden. Andererseits muss dem Ersteller des  Vorfalls eine Schaltfläche Bearbeiten angezeigt werden, und alle anderen Benutzer dürfen nur Details des Vorfalls anzeigen. Dies wird durch benutzerspezifische Ansichten ermöglicht, die von der Eigenschaft aktiviert `refresh` werden.

Die folgende Abbildung zeigt ein Beispiel für eine Ticketing Messaging Extension (ME), bei der verschiedenen Benutzern im Chat basierend auf der Anforderung unterschiedliche Aktionen angezeigt werden:

:::image type="content" source="~/assets/images/adaptive-cards/universal-bots-incident-management.png" alt-text="Benutzerspezifische Ansichten":::

Weitere Informationen finden Sie [unter Beispiel für benutzerspezifische Ansichten](User-Specific-Views.md).

### <a name="sequential-workflow-support"></a>Sequenzielle Workflowunterstützung

Mithilfe der Sequenziellen Workflowunterstützung können Benutzer eine Reihe von Workflows ohne separates Senden unterschiedlicher Karten nutzen. Dies wird durch die Möglichkeit `Action.Execute` ermöglicht, eine adaptive Karte als Reaktion auf eine Aktion zurück zu geben. Darüber hinaus kann jeder Benutzer im Chat oder Kanal über seinen Workflow weiterkommen, ohne die Karte für andere Benutzer im Chat zu ändern.

Die folgende Abbildung zeigt ein Beispiel für einen Bot für die Essensbestellung: <br/>

<img src="~/assets/images/bots/sequentialWorkflow.gif" alt="Sequential Workflow" width="400"/>

Die folgende Abbildung zeigt die verschiedenen Zustände für verschiedene Benutzer im Chat oder Kanal:

:::image type="content" source="~/assets/images/adaptive-cards/universal-bots-catering-bot.png" alt-text="Zustände des Cateringbots":::

Weitere Informationen finden Sie unter [Beispiel für Sequenzieller Workflow](Sequential-Workflows.md).

### <a name="up-to-date-views"></a>Aktuelle Ansichten

Sie können adaptive Karten erstellen, die automatisch aktualisiert werden. Dies kann z. B. eine Genehmigungsanforderung sein, die von einem Benutzer gesendet wurde. Nach der Genehmigung muss die Karte automatisch Details zur Genehmigungszeit der Anforderung und zur Genehmigung der Anforderung anzeigen. Mit dem Aktualisierungsmodell können Sie solche aktuellen Ansichten bereitstellen. Die folgende Abbildung zeigt einen mehrstufigen Genehmigungsfluss und wie die Ansichten für verschiedene Benutzer angezeigt werden.

:::image type="content" source="~/assets/images/adaptive-cards/universal-bots-up-to-date-views.png" alt-text="Aktuelle benutzerspezifische Ansichten":::

Weitere Informationen finden Sie [unter Beispiel für aktuelle Ansichten](Up-To-Date-Views.md).

Jetzt können Sie verstehen, wie adaptive Karten mit dem neuen Modell für universelle Aktionen transformiert werden können, um eine eindeutige und verbesserte Benutzeroberfläche zu bieten.

## <a name="adaptive-cards-and-the-new-universal-actions-model"></a>Adaptive Karten und das neue Modell für universelle Aktionen

Adaptive Karten sind eine Kombination aus Inhalten, z. B. Text und Grafiken, und Aktionen, die von einem Benutzer ausgeführt werden können. Weitere Informationen finden Sie unter [Adaptive Karten](http://adaptivecards.io/). Die neuen universellen Aktionen für adaptive Karten ermöglichen eine allgemeine Behandlung der adaptiven Kartenaktionen über Plattformen und Anwendungen hinweg. Weitere Informationen finden Sie unter [Universelles Aktionsmodell](https://docs.microsoft.com/adaptive-cards/authoring-cards/universal-action-model).

[Das Dokument "Arbeiten mit universellen](Work-with-universal-actions-for-adaptive-cards.md) Aktionen für adaptive Karten" führt Sie durch die Schritte, um die Funktionen von Universelle Aktionen für adaptive Karten für Ihre Lösung zu nutzen.

## <a name="see-also"></a>Siehe auch

* [Was sind Bots?](~/bots/what-are-bots.md)
* [Übersicht über adaptive Karten](~/task-modules-and-cards/what-are-cards.md)
* [Adaptive Karten @ Microsoft Build 2020](https://youtu.be/hEBhwB72Qn4?t=1393)
* [Adaptive Karten @ Ignite 2020](https://techcommunity.microsoft.com/t5/video-hub/elevate-user-experiences-with-teams-and-adaptive-cards/m-p/1689460)

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Arbeiten mit universellen Aktionen für adaptive Karten](Work-with-universal-actions-for-adaptive-cards.md)
