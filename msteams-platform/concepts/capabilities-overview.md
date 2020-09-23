---
title: Grundlegendes zu Teams-App-Funktionen
author: heath-hamilton
description: Erläuterte Teams-App-Funktionen
ms.topic: conceptual
ms.author: lajanuar
ms.date: 09/22/2020
ms.openlocfilehash: e7a6fe61fa5c74547ce20cc895afdd044f35e512
ms.sourcegitcommit: 1aa0b172931d0f81db346452788c41dc4a6717b9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/22/2020
ms.locfileid: "48210275"
---
# <a name="understanding-teams-app-capabilities"></a>Grundlegendes zu Teams-App-Funktionen

*Funktionen* sind die Erweiterungspunkte für das Erstellen von apps auf der Microsoft Teams-Plattform.

Es gibt mehrere Möglichkeiten zum Erweitern von Teams, sodass jede APP eindeutig ist: einige verfügen nur über eine Funktion (beispielsweise einen webhook), während andere einige Benutzeroptionen zur Verfügung stellen. Beispielsweise könnte Ihre APP Daten an einem zentralen Ort (Tab) anzeigen und diese Informationen über eine Konversations Schnittstelle (bot) präsentieren.

Ihre Teams-App kann eine oder alle der folgenden Hauptfunktionen haben:

* [Tabs](../tabs/what-are-tabs.md)
* [Messaging-Erweiterungen](../messaging-extensions/what-are-messaging-extensions.md)
* [Bots](../bots/what-are-bots.md)
* [Webhooks und Connectors](../webhooks-and-connectors/what-are-webhooks-and-connectors.md)

Ihre APP kann auch erweiterte Funktionen nutzen, beispielsweise die [Microsoft Graph-API für Teams](https://docs.microsoft.com/graph/teams-concept-overview).

In der folgenden Abbildung erfahren Sie, welche Funktionen die gewünschten Features in Ihrer APP bereitstellen.

:::image type="content" source="../assets/images/capabilities-overview.png" alt-text="Mind Map illustriert, was Teams-App-Funktionen sind.":::

## <a name="doing-whats-best-for-your-users"></a>Ausführen des am besten geeigneten für Ihre Benutzer

Wenn Sie sich mit der APP-Entwicklung von Teams vertraut machen, verstehen Sie die Feinheiten. Es gibt mehrere Möglichkeiten zum Erstellen bestimmter Features (beispielsweise das Sammeln von Benutzereingaben). Beispielsweise können Sie ein webbasiertes Formular in einer Registerkarte mit einem einbetten `<iframe>` . Sie können dies auch auf einer Registerkarte mithilfe eines Aufgabenmoduls, einer Benutzeroberflächen Konvention für Teams, für eine mehr systemeigene Benutzeroberfläche tun, die Ihren Benutzern möglicherweise lieber ist.

Wenn Sie die richtigen Funktionen und das richtige Design auswählen, müssen Sie sich zunächst [mit den Anwendungsfällen Ihres Publikums vertraut](../concepts/design/understand-use-cases.md)machen.
