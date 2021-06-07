---
title: Übersicht über universelle Aktionen für adaptive Karten
description: Eine kurze Übersicht über universelle Aktionen für adaptive Karten.
ms.topic: overview
localization_priority: Normal
ms.openlocfilehash: f8980743954c4dff2ced464bc599439c7519cefe
ms.sourcegitcommit: d1d1143e285cac5f23590ccba5389616d08f94b3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/05/2021
ms.locfileid: "52781618"
---
# <a name="universal-actions-for-adaptive-cards"></a>Universal-Aktionen für adaptive Karten

Universelle Aktionen für adaptive Karten haben sich aus dem Feedback von Entwicklern entwickelt, dass das Layout und Rendering für adaptive Karten zwar universell war, die Aktionsbehandlung jedoch nicht war. Auch wenn ein Entwickler dieselbe Karte an verschiedene Orte senden möchte, müssen aktionen unterschiedlich behandelt werden.

Universelle Aktionen für adaptive Karten stellt den Bot als allgemeines Back-End für die Behandlung von Aktionen bereit und führt einen neuen Aktionstyp ein, `Action.Execute` der appsübergreifend funktioniert, z. B. Teams und Outlook.

Dieses Dokument hilft Ihnen zu verstehen, wie Sie das Modell für universelle Aktionen verwenden können, um die Benutzerfreundlichkeit der Interaktion mit adaptiven Karten plattform- und anwendungsübergreifend zu verbessern.

> [!NOTE]
> Unterstützung für universelle Aktionen für adaptive Karten ist nur für Vom Bot gesendete Karten verfügbar. Unterstützung für Karten, die über das Feld zum Verfassen gesendet werden, und die Verbreitung von Karten für Links wird in Kürze verfügbar sein.

## <a name="enhance-user-experiences-with-universal-actions-for-adaptive-cards"></a>Verbessern der Benutzererfahrung mit universellen Aktionen für adaptive Karten

Universelle Aktionen für adaptive Karten verbessern die Benutzererfahrung, indem die folgenden Szenarien aktiviert werden:

* [Universelle Aktionen](#universal-actions)
* [Benutzerspezifische Ansichten](#user-specific-views)
* [Sequenzielle Workflowunterstützung](#sequential-workflow-support)
* [Aktuelle Ansichten](#up-to-date-views)

### <a name="universal-actions"></a>Universelle Aktionen

Vor den universellen Aktionen für adaptive Karten haben verschiedene Hosts wie folgt unterschiedliche Aktionsmodelle bereitgestellt:

* Teams oder bots verwendet `Action.Submit` , ein Ansatz, der das tatsächliche Kommunikationsmodell auf den zugrunde liegenden Kanal zurücksetzt.
* Outlook `Action.Http` für die Kommunikation mit dem Back-End-Dienst verwendet, der explizit in der Nutzlast der adaptiven Karte angegeben ist.

Die folgende Abbildung zeigt das aktuelle inkonsistente Aktionsmodell:

:::image type="content" source="~/assets/images/adaptive-cards/current-teams-outlook-action-model.png" alt-text="Inkonsistentes Aktionsmodell":::

Mit den universellen Aktionen für adaptive Karten können Sie `Action.Execute` die Aktionsbehandlung auf verschiedenen Plattformen verwenden. `Action.Execute`funktioniert über Hubs hinweg, einschließlich Teams und Outlook. Darüber hinaus kann eine adaptive Karte als Antwort auf eine `Action.Execute` ausgelöste Aufrufanforderung zurückgegeben werden.

Die folgende Abbildung zeigt das neue Modell für universelle Aktionen:

:::image type="content" source="~/assets/images/adaptive-cards/universal-action-model.png" alt-text="Neue universelle Aktionen für adaptive Karten":::

Sie können jetzt die gleiche Karte an beide senden, Teams und Outlook, und sie mithilfe des zugrunde liegenden Bots miteinander synchronisieren. Alle Aktionen, die auf beiden Plattformen ausgeführt werden, werden mit diesem Build einmal auf die andere Plattform übernommen *und stellen ein beliebiges* Modell (Universelle Aktionen für adaptive Karten) bereit.

Die folgende Abbildung zeigt die universellen Aktionen für adaptive Karten für Teams und Outlook:

# <a name="mobile"></a>[Mobil](#tab/mobile)

:::image type="content" source="~/assets/images/adaptive-cards/mobile-universal-bots-teams-outlook.jpg" alt-text="Mobile Karte für Teams und Outlook":::

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="~/assets/images/adaptive-cards/universal-bots-teams-outlook.png" alt-text="Dieselbe Karte wie Teams und Outlook":::

* * *

### <a name="user-specific-views"></a>Benutzerspezifische Ansichten

Heute sieht jeder Benutzer im Teams Chat oder Kanal genau die gleichen Ansichts- und Schaltflächenaktionen auf der adaptiven Karte. In bestimmten Szenarien ist es jedoch erforderlich, dass bestimmte Benutzer unterschiedlich handeln und Zugriff auf unterschiedliche Informationen innerhalb desselben Chats oder Kanals haben.

Wenn Sie beispielsweise eine Karte für die Schadensberichterstattung in einem Chat oder Kanal senden, muss nur dem Benutzer, dem der Vorfall zugewiesen ist, eine Schaltfläche **"Auflösen"** angezeigt werden. Andererseits muss dem Ersteller des Vorfalls eine Schaltfläche **"Bearbeiten"** angezeigt werden, und alle anderen Benutzer dürfen nur Details des Vorfalls anzeigen können. Dies wird durch benutzerspezifische Ansichten ermöglicht, die von der Eigenschaft aktiviert `refresh` werden.

Die folgende Abbildung zeigt ein Beispiel für eine Ticketing Messaging Extension (ME), bei der verschiedene Benutzer im Chat basierend auf der Anforderung unterschiedliche Aktionen angezeigt werden:

# <a name="mobile"></a>[Mobil](#tab/mobile)

:::image type="content" source="~/assets/images/adaptive-cards/mobile-universal-bots-incident-management.jpg" alt-text="Benutzerspezifische Ansichten mobiler Benutzer":::

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="~/assets/images/adaptive-cards/universal-bots-incident-management.png" alt-text="Benutzerspezifische Ansichten":::

* * *

Weitere Informationen finden Sie im [Beispiel für benutzerspezifische Ansichten.](User-Specific-Views.md)

### <a name="sequential-workflow-support"></a>Sequenzielle Workflowunterstützung

Mit sequenzieller Workflowunterstützung können Benutzer eine Reihe von Workflows durchlaufen, ohne separate Karten zu senden. Dies wird durch die Möglichkeit `Action.Execute` ermöglicht, eine adaptive Karte als Reaktion auf eine Aktion zurückzugeben. Außerdem kann jeder Benutzer im Chat oder Kanal den Workflow durchlaufen, ohne die Karte für andere Benutzer im Chat zu ändern.

Die folgende Abbildung zeigt ein Beispiel für einen Bot zur Sortierung von Essen: <br/>

<img src="~/assets/images/bots/sequentialWorkflow.gif" alt="Sequential Workflow" width="400"/>

Die folgende Abbildung zeigt die verschiedenen Zustände für verschiedene Benutzer im Chat oder Kanal:

:::image type="content" source="~/assets/images/adaptive-cards/universal-bots-catering-bot.png" alt-text="Zustände des Bots &quot;Auffüllen&quot;":::

Weitere Informationen finden Sie im [Beispiel für sequenziellen Workflow.](Sequential-Workflows.md)

### <a name="up-to-date-views"></a>Aktuelle Ansichten

Sie können adaptive Karten erstellen, die automatisch aktualisiert werden. Dies kann z. B. eine Genehmigungsanforderung sein, die von einem Benutzer gesendet wurde. Nach der Genehmigung muss die Karte automatisch Details zur Genehmigungszeit der Anforderung und zur Person anzeigen, die die Anforderung genehmigt hat. Mit dem Aktualisierungsmodell können Sie so aktuelle Ansichten bereitstellen. Die folgende Abbildung zeigt einen mehrstufigen Genehmigungsfluss und wie die Ansichten für verschiedene Benutzer angezeigt werden.

:::image type="content" source="~/assets/images/adaptive-cards/universal-bots-up-to-date-views.png" alt-text="Aktuelle benutzerspezifische Ansichten":::

Weitere Informationen finden Sie im [Beispiel für aktuelle Ansichten.](Up-To-Date-Views.md)

Jetzt können Sie verstehen, wie adaptive Karten mit dem neuen Modell für universelle Aktionen transformiert werden können, um eine einzigartige und verbesserte Benutzererfahrung bereitzustellen.

## <a name="adaptive-cards-and-the-new-universal-actions-model"></a>Adaptive Karten und das neue Modell für universelle Aktionen

Adaptive Karten sind eine Kombination aus Inhalten, z. B. Text und Grafiken, und Aktionen, die von einem Benutzer ausgeführt werden können. Weitere Informationen finden Sie unter [Adaptive Karten.](http://adaptivecards.io/) Die neuen universellen Aktionen für adaptive Karten ermöglichen eine allgemeine Behandlung der Aktionen adaptiver Karten über Plattformen und Anwendungen hinweg. Weitere Informationen finden Sie unter ["Universelles Aktionsmodell".](/adaptive-cards/authoring-cards/universal-action-model)

Sie können loslegen, indem Sie Szenarien mithilfe der [Schnellstartanleitung](Work-with-universal-actions-for-adaptive-cards.md) aktualisieren und universelle Aktionen nutzen.

## <a name="see-also"></a>Siehe auch

* [Was sind Bots?](~/bots/what-are-bots.md)
* [Übersicht über adaptive Karten](~/task-modules-and-cards/what-are-cards.md)
* [Adaptive Karten @ Microsoft Build 2020](https://youtu.be/hEBhwB72Qn4?t=1393)
* [Adaptive Karten @ Ignite 2020](https://techcommunity.microsoft.com/t5/video-hub/elevate-user-experiences-with-teams-and-adaptive-cards/m-p/1689460)

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Mit Universal-Aktionen für adaptive Karten arbeiten](Work-with-universal-actions-for-adaptive-cards.md)
