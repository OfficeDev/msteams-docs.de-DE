---
title: Bestimmen ihrer Teams-App-Kontexte
author: heath-hamilton
description: Bei der Planung Ihrer Teams-App müssen Sie entscheiden, ob die app in kollaborativen Räumen, in persönlichen Räumen oder in beiden verwendet werden soll.
ms.openlocfilehash: 05c92aa8b199cbdb58e477fb4a64467c150edbfd
ms.sourcegitcommit: 9fbc701a9a039ecdc360aefbe86df52b9c3593f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/12/2020
ms.locfileid: "46652014"
---
# <a name="getting-to-know-teams-ui-conventions"></a>Kennenlernen von Microsoft Teams-Benutzeroberflächen Konventionen

Apps weisen in der Regel eine oder mehrere standardmäßige Teams-Benutzeroberflächen Konventionen auf. Das Erstellen der Funktionen Ihrer App mithilfe dieser Konventionen führt zu umfangreichen Erfahrungen, die für Microsoft Teams systemeigen sind.

## <a name="cards"></a>Karten

[Karten](~/task-modules-and-cards/what-are-cards.md) sind Benutzeroberflächencontainer, die von schematisierten JSON definiert werden und mehrere Eigenschaften und Anlagen enthalten können. Sie können formatierten Text, Medien, Steuerelemente (wie Dropdown Boxen und Optionsfelder) und Schaltflächen enthalten, die Karten Aktionen auslösen.

Kartenaktionen können Nutzlasten zur API Ihrer App senden, einen Link öffnen, Authentifizierungsabläufe initiieren oder Nachrichten an Unterhaltungen senden. Die Teams-Plattform unterstützt mehrere Arten von Karten, einschließlich Adaptive Karten, Hero Cards, Thumbnail-Karten und vieles mehr. Sie können Kartensammlungen kombinieren und in einer Liste oder einem Karussell anzeigen.

## <a name="task-modules"></a>Aufgabenmodule

[Aufgaben Module](~/task-modules-and-cards/what-are-task-modules.md) bieten modale Popup-Erlebnisse in Microsoft Teams. Sie sind besonders nützlich für das Initiieren von Workflows, das Sammeln von Benutzereingaben oder das Anzeigen von umfangreichen Informationen wie Videos oder Power BI-Dashboards. In Aufgaben Modulen können Sie benutzerdefinierten Front-End-Code ausführen, ein `<iframe>` Widget anzeigen oder eine Adaptive Karte anzeigen.

Wenn Sie sich überlegen, wie Sie Ihre APP erstellen möchten, denken Sie daran, dass modals natürlich sind, damit Benutzerinformationen eingeben oder Aufgaben im Vergleich zu einer Registerkarte oder einer Unterhaltungs basierten bot-Erfahrung ausführen können.

## <a name="deep-links"></a>Deep-Links

Ihre APP kann [URL-Deep-Links](~/concepts/build-and-test/deep-links.md) erstellen, um den Benutzer über Ihre APP und den Teams-Client zu navigieren. Sie können für die meisten Entitäten innerhalb von Teams Deep-Links erstellen, von denen einige (ähnlich einer neuen Besprechungsanfrage) Ihnen ermöglichen, Informationen mithilfe von Abfragezeichenfolgen in der URL im Voraus auszufüllen. 

So könnte beispielsweise Ihr Unterhaltungs-Bot eine Nachricht an einen Kanal mit einem Deep-Link für ein Aufgabenmodul senden, was dazu führt, dass eine Karte als 1:1-Nachricht an einen Benutzer gesendet wird, die wiederum einen Deep-Link für das Erstellen einer neuen Besprechung mit einem bestimmten Benutzer zu einem bestimmten Datum/einer bestimmten Uhrzeit beinhaltet. Verwenden Sie Deep-Links, um Verbindungen mit den verschiedenen Erweiterungspunkten herzustellen, die für Ihre App verfügbar sind, damit sich Ihr Benutzer stets im richtigen Kontext befindet.

## <a name="web-based-content"></a>Webbasierter Inhalt

[Webbasierter Inhalt](~/tabs/how-to/create-tab-pages/content-page.md) ist eine von Ihnen gehostete Webseite, die in ein Tab-oder Aufgabenmodul eingebettet werden kann. Um Ihre Webseite in den Teams-Client einzubetten, müssen Sie Folgendes tun:

* `HTTPS`In die URL einschließen.
* In eine eingebettet werden `<iframe>` .
* Schließen Sie das Microsoft Teams JavaScript Client SDK ein, und rufen Sie die SDK `initialize()` -Methode beim Laden der Seite auf.

## <a name="next-steps"></a>Nächste Schritte

* [Entwerfen Ihrer APP](../../tabs/design/tabs.md)
