---
title: Übersicht über universelle Aktionen für adaptive Karten
description: Informationen zu universellen Aktionen für adaptive Karten, z. B. benutzerspezifische Ansichten, sequenzielle Workflowunterstützung und mehr für Desktop- und mobile Umgebungen
ms.topic: overview
ms.localizationpriority: medium
ms.openlocfilehash: 9c04ed4726840bd3d1637555d1bb021f31bf2e25
ms.sourcegitcommit: 19f3e4e9088d0a07c9b567e76640d498b9d1981f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/16/2022
ms.locfileid: "67786976"
---
# <a name="universal-actions-for-adaptive-cards"></a>Universal-Aktionen für adaptive Karten

Universelle Aktionen für adaptive Karten haben sich aus dem Feedback von Entwicklern entwickelt, dass die Aktionsbehandlung trotz der universellen Darstellung von Layout und Rendering für adaptive Karten nicht möglich war. Auch wenn ein Entwickler die gleiche Karte an verschiedene Orte senden wollte, muss er Aktionen anders behandeln.

Universelle Aktionen für adaptive Karten bringen den Bot als allgemeines Back-End für die Behandlung von Aktionen und führen einen neuen Aktionstyp ein, `Action.Execute`der appsübergreifend funktioniert, z. B. Teams und Outlook.

Dieses Dokument hilft Ihnen zu verstehen, wie Sie das Modell für universelle Aktionen verwenden können, um die Benutzererfahrung bei der Interaktion mit adaptiven Karten über Plattformen und Anwendungen hinweg zu verbessern.

> [!NOTE]
> Unterstützung für universelle Aktionen für adaptive Karten v1.4 ist nur für Karten verfügbar, die vom Bot gesendet werden. Die Unterstützung für Karten, die über das Feld "Verfassen" und die Verbreitung von Links gesendet werden, wird in Kürze verfügbar sein.

## <a name="enhance-user-experiences-with-universal-actions-for-adaptive-cards"></a>Verbessern der Benutzererfahrung mit universellen Aktionen für adaptive Karten

Universelle Aktionen für adaptive Karten verbessern die Benutzerfreundlichkeit, indem die folgenden Szenarien aktiviert werden:

* [Universelle Aktionen](#universal-actions)
* [Benutzerspezifische Ansichten](#user-specific-views)
* [Unterstützung sequenzieller Workflows](#sequential-workflow-support)
* [Aktuelle Ansichten](#up-to-date-views)

### <a name="universal-actions"></a>Universelle Aktionen

Vor den universellen Aktionen für adaptive Karten stellten verschiedene Hosts unterschiedliche Aktionsmodelle wie folgt bereit:

* Teams oder Bots verwendet `Action.Submit`, ein Ansatz, der das tatsächliche Kommunikationsmodell auf den zugrunde liegenden Kanal zurücksetzt.
* Outlook wurde für die Kommunikation mit dem Back-End-Dienst verwendet `Action.Http` , der explizit in der Nutzlast der adaptiven Karte angegeben ist.

Die folgende Abbildung zeigt das aktuelle inkonsistente Aktionsmodell:

:::image type="content" source="~/assets/images/adaptive-cards/current-teams-outlook-action-model.png" alt-text="Inkonsistentes Aktionsmodell":::

Mit den universellen Aktionen für adaptive Karten können Sie die Aktionsbehandlung auf verschiedenen Plattformen verwenden `Action.Execute` . `Action.Execute` funktioniert hubübergreifend, einschließlich Teams und Outlook. Darüber hinaus kann eine adaptive Karte als Antwort für eine `Action.Execute` ausgelöste Aufrufanforderung zurückgegeben werden.

Die folgende Abbildung zeigt das neue Modell für universelle Aktionen:

:::image type="content" source="~/assets/images/adaptive-cards/universal-action-model.png" alt-text="Neue universelle Aktionen für adaptive Karten":::

Sie können jetzt die gleiche Karte an Teams und Outlook senden und mithilfe des zugrunde liegenden Bots miteinander synchronisieren. Alle Auf beiden Plattformen ausgeführten Aktionen werden mit diesem Build einmal für die andere plattform widergespiegelt *. Stellen Sie das Modell an einer beliebigen Stelle* (Universelle Aktionen für adaptive Karten) bereit.

Die folgende Abbildung zeigt die universellen Aktionen für adaptive Karten für Teams und Outlook:

# <a name="mobile"></a>[Mobil](#tab/mobile)

:::image type="content" source="~/assets/images/mobile-universal-bots-teams-outlook.png" alt-text="Mobile gleiche Karte für Teams und Outlook":::

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="~/assets/images/adaptive-cards/universal-bots-teams-outlook.png" alt-text="Gleiche Karte für Teams und Outlook" lightbox="../../../assets/images/adaptive-cards/universal-bots-teams-outlook.png":::

* * *

### <a name="user-specific-views"></a>Benutzerspezifische Ansichten

Heute sieht jeder Benutzer im Teams-Chat oder -Kanal genau die gleichen Ansichts- und Schaltflächenaktionen auf der adaptiven Karte. In bestimmten Szenarien ist es jedoch erforderlich, dass bestimmte Benutzer anders handeln und Zugriff auf unterschiedliche Informationen innerhalb desselben Chats oder Kanals haben.

Wenn Sie z. B. eine Vorfallberichtskarte in einem Chat oder Kanal senden, muss nur dem Benutzer, dem der Vorfall zugewiesen wurde, die Schaltfläche " **Auflösen** " angezeigt werden. Andererseits muss dem Vorfallersteller eine Schaltfläche **"Bearbeiten"** angezeigt werden, und alle anderen Benutzer dürfen nur Details des Vorfalls anzeigen. Dies wird durch benutzerspezifische Ansichten ermöglicht, die von der `refresh` Eigenschaft aktiviert werden.

Die folgende Abbildung zeigt ein Beispiel für eine Erweiterung der Ticketnachricht (ME), bei der verschiedenen Benutzern im Chat basierend auf der Anforderung unterschiedliche Aktionen angezeigt werden:

# <a name="mobile"></a>[Mobil](#tab/mobile)

:::image type="content" source="~/assets/images/adaptive-cards/mobile-universal-bots-incident-management.jpg" alt-text="Mobile benutzerspezifische Ansichten" lightbox="../../../assets/images/adaptive-cards/mobile-universal-bots-incident-management.jpg":::

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="~/assets/images/adaptive-cards/universal-bots-incident-management.png" alt-text="Benutzerspezifische Ansichten" lightbox="../../../assets/images/adaptive-cards/universal-bots-incident-management.png":::

* * *

Weitere Informationen finden Sie im [Beispiel für benutzerspezifische Ansichten](User-Specific-Views.md).

### <a name="sequential-workflow-support"></a>Unterstützung sequenzieller Workflows

Mit der Unterstützung sequenzieller Workflows können Benutzer eine Reihe von Workflows durchlaufen, ohne unterschiedliche Karten separat zu senden. Dies wird durch die Möglichkeit `Action.Execute` ermöglicht, eine adaptive Karte als Reaktion auf eine Aktion zurückzugeben. Außerdem kann jeder Benutzer im Chat oder Kanal den Workflow durchlaufen, ohne die Karte für andere Benutzer im Chat zu ändern.

Die folgende Abbildung zeigt ein Beispiel für einen Bot für die Lebensmittelbestellung: <br/>

<img src="~/assets/images/bots/sequentialWorkflow.gif" alt="Sequential Workflow" width="400"/>

Die folgende Abbildung zeigt die verschiedenen Zustände für verschiedene Benutzer im Chat oder Kanal:

:::image type="content" source="~/assets/images/adaptive-cards/universal-bots-catering-bot.png" alt-text="Catering-Bot-Staaten" lightbox="../../../assets/images/adaptive-cards/universal-bots-catering-bot.png":::

Weitere Informationen finden Sie im [Beispiel für sequenziellen Workflow](Sequential-Workflows.md).

### <a name="up-to-date-views"></a>Aktuelle Ansichten

Sie können adaptive Karten erstellen, die automatisch aktualisiert werden. Dies kann beispielsweise eine Genehmigungsanforderung sein, die von einem Benutzer gesendet wurde. Nach der Genehmigung muss die Karte automatisch Details zum Genehmigungszeitpunkt der Anforderung und zur Person anzeigen, die die Anforderung genehmigt hat. Mit dem Aktualisierungsmodell können Sie solche aktuellen Ansichten bereitstellen. Die folgende Abbildung zeigt einen mehrstufigen Genehmigungsfluss und zeigt, wie die Ansichten für verschiedene Benutzer angezeigt werden.

:::image type="content" source="~/assets/images/adaptive-cards/universal-bots-up-to-date-views.png" alt-text="Aktuelle benutzerspezifische Ansichten" lightbox="../../../assets/images/adaptive-cards/universal-bots-up-to-date-views.png":::

Weitere Informationen finden Sie im [Beispiel für aktuelle Ansichten](Up-To-Date-Views.md).

Jetzt können Sie verstehen, wie adaptive Karten mit dem neuen Modell für universelle Aktionen transformiert werden können, um eine einzigartige und verbesserte Benutzererfahrung zu bieten.

## <a name="adaptive-cards-and-the-new-universal-actions-model"></a>Adaptive Karten und das neue Modell für universelle Aktionen

Adaptive Karten sind eine Kombination aus Inhalten, z. B. Text und Grafiken, und Aktionen, die von einem Benutzer ausgeführt werden können. Weitere Informationen finden Sie unter [Adaptive Karten](http://adaptivecards.io/). Die neuen universellen Aktionen für adaptive Karten ermöglichen eine gemeinsame Behandlung der Aktionen für adaptive Karten über Plattformen und Anwendungen hinweg. Weitere Informationen finden Sie unter ["Universelles Aktionsmodell"](/adaptive-cards/authoring-cards/universal-action-model).

Sie können die ersten Schritte ausführen, indem Sie Szenarien mithilfe der [Schnellstartanleitung] aktualisieren. (Work-with-universal-actions-for-adaptive-cards.md) und universelle Aktionen nutzen.

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Mit Universal-Aktionen für adaptive Karten arbeiten](Work-with-universal-actions-for-adaptive-cards.md)

## <a name="see-also"></a>Siehe auch

* [Was sind Bots?](~/bots/what-are-bots.md)
* [Übersicht über adaptive Karten](~/task-modules-and-cards/what-are-cards.md)
* [Adaptive Karten @ Microsoft Build 2020](https://youtu.be/hEBhwB72Qn4?t=1393)
* [Adaptive Karten @ Ignite 2020](https://techcommunity.microsoft.com/t5/video-hub/elevate-user-experiences-with-teams-and-adaptive-cards/m-p/1689460).
* [Universelle Aktionen für suchbasierte Messaging-Erweiterungen](../../../messaging-extensions/how-to/search-commands/universal-actions-for-search-based-message-extensions.md)
