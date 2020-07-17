---
title: Entwurfsrichtlinien für Messaging Erweiterungen
description: Beschreibt die Richtlinien zum Erstellen von Messaging Erweiterungen.
keywords: Design Guidelines für Teams Referenz Tipps für Messaging-Erweiterungen bewährte Methode
author: EmilyyC
ms.author: qinch
ms.openlocfilehash: 5d62646c5757f93cc4f6ae6e089ef3a0918f9eea
ms.sourcegitcommit: 81ac2a1070d16e20ae0e4cb6137dce09b31914af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/16/2020
ms.locfileid: "45152686"
---
# <a name="start-sharing-with-powerful-messaging-extensions"></a>Starten der Freigabe mit leistungsstarken Messaging Erweiterungen

Messaging Erweiterungen sind für die Freigabe von Inhalten mit Aktionen konzipiert. Dieses Feature stellt den höchsten ROI (Return on Investment) in unserem Stack dar. Messaging-Erweiterungen funktionieren in Chat und Kanälen, unterstützen mehrere Abfrage Endpunkte, ermöglichen die Erstellung neuer Entitäten und arbeiten mit dem Aufteilen von Links, um eine benutzerdefinierte Verknüpfungs Vorschau zu erstellen. Die Herausforderung besteht darin, dass das Feature zwar leistungsfähig und äußerst nützlich ist, es aber nicht leicht auffindbar ist. Dieses Handbuch hilft Ihnen beim Erstellen von Messaging Erweiterungen, die von mehr Benutzern bereitgestellt und verwendet werden.

## <a name="design-guidelines"></a>Richtlinien für den Entwurf

### <a name="show-content-as-a-user-type"></a>Anzeigen von Inhalten als Benutzertyp

Messaging-Erweiterungen stellen eine einzigartige Möglichkeit zur Verwendung von Stichwort suchen zur Suche nach Aktionen zur Verfügung, die für einen oder mehrere Benutzer freigegeben werden können. Mit dieser bevorzugten Interaktion können Benutzer Suchbegriffe mit einer verzögerten automatischen Abfrage als Benutzertyp eingeben. Dieses Modell macht eine gute Aufgabe, vorgeschlagene Ergebnisse zu simulieren, und erfordert, dass Benutzer minimal Zeichen eingeben.

> [!TIP]
>Es ist möglich, aber nicht wünschenswert, dass Benutzer auswählen `enter` oder `search` vor dem Senden von Abfragen müssen. Es gibt zwar weniger Stress im Back-End-Dienst, aber dieses Modell ist nicht die Norm und kann die Benutzer verwirren.

### <a name="consider-zero-term-queries"></a>Prüfen von NULL Termin Abfragen

NULL-Term-Abfragen werden direkt durch eine Benutzeraktion ausgelöst, statt indem der Benutzer Ausdrücke in ein Suchfeld schreibt. Alle Messaging-Erweiterungen profitieren von NULL-Term-Abfragen, in der Regel basierend auf dem, was der Benutzer zuletzt im Dienst gesehen hat. Der Vorteil besteht darin, dass die Wahrscheinlichkeit, dass der Benutzer die zuletzt gesehenen Teile teilen möchte, recht hoch ist. Andere NULL-Term-Abfragen basieren möglicherweise auf dem Dienst. Beispiels `news` Weise kann kürzlich gepostete News-Erweiterungen von aktuellen und bevorstehenden Ereignissen angezeigt werden.

<img width="450px" title="Neue Registerkarte "Konfiguration"" src="../../assets/images/messaging-extension/zero-term-query.png" />

### <a name="include-link-unfurling"></a>Link-Entfaltung einschließen

Eine der am häufigsten verwendeten Methoden zum Freigeben von Inhalten in Microsoft Teams ist die über einen Hyperlink, unabhängig davon, ob es sich um eine Aufgabe handelt, an der Sie gerade gearbeitet haben, oder um ein Video, das Sie witzig gefunden haben. Wenn ein Benutzer einen Link in Microsoft Teams freigibt, wird eine Vorschau mit Bild, Titel oder Beschreibung angezeigt. Wenn Sie einen [Link aufrollen](../how-to/link-unfurling.md) , können Sie diese Vorschau jetzt anpassen. Außerdem werden Benutzer aufgefordert, Ihre APP zu installieren, nachdem Sie sich für die Verwendung Ihrer Vorschau entschieden haben. Durch das Hinzufügen von Funktionen zur Aufrollung von Links zu Ihrer APP kann Ihre APP-Auffindbarkeit erheblich gesteigert werden.

### <a name="highlight-your-messaging-extension"></a>Markieren Ihrer Messaging Erweiterung

Messaging Erweiterungen sind nicht immer leicht zu finden. Fügen Sie App-Screenshots in die APP-Detailseite und Ihre Hilfedokumentation ein, um Ihre Messaging Erweiterung zu kennzeichnen. Sie können auch die *Anleitungs* Dokumentation für Ihre Messaging Erweiterung in bot Tours einschließen, um die gesamte App jenseits der bot-Interaktionen hervorzuheben.

### <a name="add-actions-on-card"></a>Hinzufügen von Aktionen auf der Karte

Zeigen Sie Benutzern nicht nur Text an. Haben Sie etwas, mit dem Sie interagieren und die nächste Aktion durchführen können. Beispielsweise fügt die places-APP nicht nur eine Karte auf der Karte ein, sondern verfügt auch über eine Schaltfläche, die, wenn Sie ausgewählt ist, Wegbeschreibungen zum Speicherort anzeigt. Benutzer können mehr Aufgaben ausführen, nachdem Sie die Karte erhalten haben.

<img width="450px" title="Neue Registerkarte "Konfiguration"" src="../../assets/images/messaging-extension/action-on-card.png" />

### <a name="keep-users-in-the-app-context"></a>Benutzer im App-Kontext behalten

Wenn eine Karte nicht ausreicht und Sie einen Link für weitere Informationen benötigen, können Sie eine Registerkarte öffnen, anstatt einen Browser zu öffnen, um eine bessere Benutzerfreundlichkeit zu erzielen. *Weitere Informationen finden Sie unter* [Erweitern Ihrer Teams-App mit einer benutzerdefinierten Registerkarte](../../tabs/how-to/add-tab.md)
