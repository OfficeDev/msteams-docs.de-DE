---
title: Übersicht über universelle Aktionen für adaptive Karten
description: Erfahren Sie mehr über universelle Aktionen für adaptive Karten, z. B. benutzerspezifische Ansichten, unterstützung für sequenzielle Workflows und vieles mehr für Desktop- und mobile Umgebungen.
ms.topic: overview
ms.localizationpriority: medium
ms.openlocfilehash: 4ee3210391f3a8aaba4b74d3d07ee6507789afed
ms.sourcegitcommit: c3601696cced9aadc764f1e734646ee7711f154c
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/03/2022
ms.locfileid: "68833058"
---
# <a name="universal-actions-for-adaptive-cards"></a>Universal-Aktionen für adaptive Karten

Universal Actions for Adaptive Cards entwickelte sich aus Dem Entwicklerfeedback, dass Layout und Rendering für adaptive Karten zwar universell waren, dies jedoch nicht der Fall war. Selbst wenn ein Entwickler dieselbe Karte an verschiedene Orte senden möchte, muss er Aktionen unterschiedlich behandeln.

Universelle Aktionen für adaptive Karten verwenden den Bot als gängiges Back-End für die Behandlung von Aktionen und führen einen neuen Aktionstyp ein, `Action.Execute`der appübergreifend funktioniert, z. B. Teams und Outlook.

Dieses Dokument hilft Ihnen zu verstehen, wie Sie das Modell für universelle Aktionen verwenden können, um die Benutzerfreundlichkeit der Interaktion mit adaptiven Karten plattform- und anwendungsübergreifend zu verbessern.

> [!NOTE]
> Die Unterstützung für universelle Aktionen für adaptive Karten v1.4 ist nur für Karten verfügbar, die vom Bot gesendet werden. Unterstützung für Karten, die über das Verfassen von Box- und Link-Unfurling-Karten gesendet werden, ist in Kürze verfügbar.

## <a name="enhance-user-experiences-with-universal-actions-for-adaptive-cards"></a>Verbessern der Benutzerfreundlichkeit mit universellen Aktionen für adaptive Karten

Universelle Aktionen für adaptive Karten verbessern die Benutzerfreundlichkeit, indem die folgenden Szenarien aktiviert werden:

* [Universelle Aktionen](#universal-actions)
* [Benutzerspezifische Ansichten](#user-specific-views)
* [Unterstützung für sequenzielle Workflows](#sequential-workflow-support)
* [Aktuelle Ansichten](#up-to-date-views)

### <a name="universal-actions"></a>Universelle Aktionen

Vor den Universellen Aktionen für adaptive Karten haben verschiedene Hosts verschiedene Aktionsmodelle wie folgt bereitgestellt:

* Teams oder Bots haben verwendet `Action.Submit`, ein Ansatz, der das tatsächliche Kommunikationsmodell auf den zugrunde liegenden Kanal verschiebt.
* Outlook wird verwendet `Action.Http` , um mit dem Back-End-Dienst zu kommunizieren, der explizit in der Nutzlast der adaptiven Karte angegeben ist.

Die folgende Abbildung zeigt das aktuelle inkonsistente Aktionsmodell:

:::image type="content" source="~/assets/images/adaptive-cards/current-teams-outlook-action-model.png" alt-text="Inkonsistentes Aktionsmodell":::

Mit den Universellen Aktionen für adaptive Karten können Sie für die Behandlung von Aktionen auf verschiedenen Plattformen verwenden `Action.Execute` .

`Action.Execute` funktioniert in allen Hubs, einschließlich Teams und Outlook, und ist kein Ersatz von `Action.Submit`. Wenn Sie beispielsweise möchten, dass ein externes System eine Aktion ausführen soll und das Ergebnis der Aktion mithilfe der [Messaging-Erweiterung](../../../messaging-extensions/what-are-messaging-extensions.md) an Ihre Unterhaltung zurückgesendet werden muss, `Action.Execute` wird nicht unterstützt.

Für [Karten zum Entpacken von Links](../../../messaging-extensions/how-to/link-unfurling.md) , z. B. Hero- und Miniaturansichtskarten, müssen Sie aufrufen `Action.Submit`.

Darüber hinaus kann eine adaptive Karte als Antwort für eine `Action.Execute` ausgelöste Aufrufanforderung zurückgegeben werden.

Die folgende Abbildung zeigt das neue Universal Action-Modell:

:::image type="content" source="~/assets/images/adaptive-cards/universal-action-model.png" alt-text="Neue universelle Aktionen für adaptive Karten":::

Sie können jetzt die gleiche Karte an Teams und Outlook senden und sie mithilfe des zugrunde liegenden Bots synchron halten. Jede Aktion, die auf einer der Plattformen ausgeführt wird, wird mit diesem Build einmal für die andere wiedergegeben *und überall (* Universelle Aktionen für adaptive Karten)-Modell bereitgestellt.

Die folgende Abbildung zeigt die Universellen Aktionen für adaptive Karten für Teams und Outlook:

# <a name="mobile"></a>[Mobil](#tab/mobile)

:::image type="content" source="~/assets/images/mobile-universal-bots-teams-outlook.png" alt-text="Dieselbe Mobile-Karte für Teams und Outlook":::

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="~/assets/images/adaptive-cards/universal-bots-teams-outlook.png" alt-text="Gleiche Karte für Teams und Outlook" lightbox="../../../assets/images/adaptive-cards/universal-bots-teams-outlook.png":::

* * *

### <a name="user-specific-views"></a>Benutzerspezifische Ansichten

Heute sieht jeder Benutzer im Teams-Chat oder -Kanal genau die gleichen Ansichts- und Schaltflächenaktionen auf der adaptiven Karte. In bestimmten Szenarien müssen sich bestimmte Benutzer jedoch anders verhalten und zugriff auf unterschiedliche Informationen innerhalb desselben Chats oder Kanals haben.

Wenn Sie z. B. eine Karte zur Meldung von Vorfällen in einem Chat oder Kanal senden, muss nur der Benutzer, dem der Vorfall zugewiesen ist, die Schaltfläche **Auflösen** sehen. Auf der anderen Seite muss der Ersteller des Incidents die Schaltfläche **Bearbeiten** sehen, und alle anderen Benutzer dürfen nur Details des Incidents anzeigen können. Dies wird durch benutzerspezifische Ansichten ermöglicht, die durch die `refresh` -Eigenschaft aktiviert werden.

Die folgende Abbildung zeigt ein Beispiel für eine Ticketing-Nachrichtenerweiterung (ME), bei der verschiedenen Benutzern im Chat je nach Anforderung unterschiedliche Aktionen angezeigt werden:

# <a name="mobile"></a>[Mobil](#tab/mobile)

:::image type="content" source="~/assets/images/adaptive-cards/mobile-universal-bots-incident-management.jpg" alt-text="Mobile Benutzerspezifische Ansichten" lightbox="../../../assets/images/adaptive-cards/mobile-universal-bots-incident-management.jpg":::

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="~/assets/images/adaptive-cards/universal-bots-incident-management.png" alt-text="Benutzerspezifische Ansichten" lightbox="../../../assets/images/adaptive-cards/universal-bots-incident-management.png":::

* * *

Weitere Informationen finden Sie unter [Beispiel für benutzerspezifische Ansichten](User-Specific-Views.md).

### <a name="sequential-workflow-support"></a>Unterstützung für sequenzielle Workflows

Mit der Unterstützung für sequenzielle Workflows können Benutzer eine Reihe von Workflows durchlaufen, ohne verschiedene Karten separat zu senden. Dies wird durch die Fähigkeit von `Action.Execute` ermöglicht, eine adaptive Karte als Reaktion auf eine Aktion zurückzugeben. Außerdem kann jeder Benutzer im Chat oder Kanal seinen Workflow durchlaufen, ohne die Karte für andere Benutzer im Chat zu ändern.

Die folgende Abbildung veranschaulicht ein Beispiel für einen Bot für die Lebensmittelbestellung: <br/>

<img src="~/assets/images/bots/sequentialWorkflow.gif" alt="Sequential Workflow" width="400"/>

Die folgende Abbildung zeigt die verschiedenen Zustände für verschiedene Benutzer im Chat oder Kanal:

:::image type="content" source="~/assets/images/adaptive-cards/universal-bots-catering-bot.png" alt-text="Zustände des Cateringbots" lightbox="../../../assets/images/adaptive-cards/universal-bots-catering-bot.png":::

Weitere Informationen finden Sie unter [Beispiel für sequenzielle Workflows](Sequential-Workflows.md).

### <a name="up-to-date-views"></a>Aktuelle Ansichten

Sie können adaptive Karten erstellen, die automatisch aktualisiert werden. Es kann z. B. eine Genehmigungsanforderung sein, die von einem Benutzer gesendet wird. Nach der Genehmigung muss die Karte automatisch Details zum Zeitpunkt der Anforderungsgenehmigung und zum Genehmigten der Anforderung anzeigen. Mit dem Aktualisierungsmodell können Sie solche aktuellen Ansichten bereitstellen. Die folgende Abbildung zeigt einen mehrstufigen Genehmigungsablauf und die Darstellung der Ansichten für verschiedene Benutzer.

:::image type="content" source="~/assets/images/adaptive-cards/universal-bots-up-to-date-views.png" alt-text="Aktuelle benutzerspezifische Ansichten" lightbox="../../../assets/images/adaptive-cards/universal-bots-up-to-date-views.png":::

Weitere Informationen finden Sie unter [Beispiel für aktuelle Ansichten](Up-To-Date-Views.md).

Jetzt können Sie verstehen, wie adaptive Karten mit dem neuen Universal Actions-Modell transformiert werden können, um eine einzigartige und verbesserte Benutzererfahrung zu bieten.

## <a name="adaptive-cards-and-the-new-universal-actions-model"></a>Adaptive Karten und das neue Modell für universelle Aktionen

Adaptive Karten sind eine Kombination aus Inhalten, z. B. Text und Grafiken, und Aktionen, die von einem Benutzer ausgeführt werden können. Weitere Informationen finden Sie unter [Adaptive Karten](http://adaptivecards.io/). Die neuen Universellen Aktionen für adaptive Karten ermöglichen eine gemeinsame Behandlung der Aktionen für adaptive Karten über Plattformen und Anwendungen hinweg. Weitere Informationen finden Sie unter [Universelles Aktionsmodell](/adaptive-cards/authoring-cards/universal-action-model).

Sie können beginnen, indem Sie Szenarien mithilfe des [Schnellstartleitfadens] aktualisieren. (Work-with-universal-actions-for-adaptive-cards.md) und nutzen Universelle Aktionen.

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Mit Universal-Aktionen für adaptive Karten arbeiten](Work-with-universal-actions-for-adaptive-cards.md)

## <a name="see-also"></a>Siehe auch

* [Was sind Bots?](~/bots/what-are-bots.md)
* [Übersicht über adaptive Karten](~/task-modules-and-cards/what-are-cards.md)
* [Adaptive Karten @ Microsoft Build 2020](https://youtu.be/hEBhwB72Qn4?t=1393)
* [Adaptive Karten @ Ignite 2020](https://techcommunity.microsoft.com/t5/video-hub/elevate-user-experiences-with-teams-and-adaptive-cards/m-p/1689460).
* [Universelle Aktionen für suchbasierte Messagingerweiterungen](../../../messaging-extensions/how-to/search-commands/universal-actions-for-search-based-message-extensions.md)
