---
title: Grundlegendes zu Teams-App-Funktionen
author: heath-hamilton
description: ''
ms.topic: overview
ms.author: heath-hamilton
ms.openlocfilehash: 580d75b648bde1caf0e85647c89635804c91fb70
ms.sourcegitcommit: 9fbc701a9a039ecdc360aefbe86df52b9c3593f3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/12/2020
ms.locfileid: "46652031"
---
# <a name="understanding-teams-app-capabilities"></a>Grundlegendes zu Teams-App-Funktionen

*Funktionen* sind die Erweiterungspunkte für das Erstellen von apps auf der Microsoft Teams-Plattform.

Es gibt mehrere Möglichkeiten, den Microsoft Teams-Client zu erweitern, sodass jede APP eindeutig ist: einige haben nur eine Funktion (beispielsweise einen webhook), während andere einige Benutzeroptionen haben. Beispielsweise könnte Ihre APP Daten an einem zentralen Ort (Tab) anzeigen und diese Informationen über eine Konversations Schnittstelle (bot) präsentieren.

Ihre Teams-App kann eine oder alle der folgenden Hauptfunktionen haben:

* [Tabs](../tabs/what-are-tabs.md)
* [Messaging-Erweiterungen](../messaging-extensions/what-are-messaging-extensions.md)
* [Webhooks und Connectors](../webhooks-and-connectors/what-are-webhooks-and-connectors.md)
* [Bots](../bots/what-are-bots.md)

Ihre APP kann auch erweiterte Funktionen nutzen, beispielsweise die [Microsoft Graph-Rest-API](../graph-api/rsc/resource-specific-consent.md).

In der folgenden Abbildung erfahren Sie, welche Funktionen die gewünschten Features in Ihrer APP bereitstellen.

![Mind Map veranschaulicht, welche Teams-App-Funktionen](doc-links/images/capabilities-overview.png)

## <a name="doing-whats-best-for-your-users"></a>Ausführen des am besten geeigneten für Ihre Benutzer

Wenn Sie sich mit der APP-Entwicklung von Teams vertraut machen, verstehen Sie die Feinheiten. Es gibt mehrere Möglichkeiten zum Erstellen bestimmter Features (beispielsweise das Sammeln von Benutzereingaben). Beispielsweise können Sie ein webbasiertes Formular in einer Registerkarte mit einem einbetten `<iframe>` . Sie können dies auch auf einer Registerkarte mithilfe eines Aufgabenmoduls, einer Benutzeroberflächen Konvention für Teams, für eine mehr systemeigene Benutzeroberfläche tun, die Ihren Benutzern möglicherweise lieber ist.

Bei der Auswahl der richtigen Kombination von Funktionen und Benutzeroberflächen Konventionen, Steuerelementen und Elementen wird zunächst die [Anwendungsfälle der Benutzergruppen verstanden](../concepts/design/understand-use-cases.md).

## <a name="learn-more"></a>Weitere Informationen

* [Starten der Planung Ihrer APP](../concepts/extensibility-points.md)
