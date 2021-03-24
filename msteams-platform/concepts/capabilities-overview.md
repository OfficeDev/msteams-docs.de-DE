---
title: Grundlegendes zu den Funktionen von Teams-Apps
author: heath-hamilton
description: Erläuterte Funktionen der Teams-App
ms.topic: conceptual
ms.author: lajanuar
ms.date: 09/22/2020
ms.openlocfilehash: 5336b36b52cf81be414f18ccaaf9e235c079e626
ms.sourcegitcommit: 49d1ecda14042bf3f368b14c1971618fe979b914
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/23/2021
ms.locfileid: "51034705"
---
# <a name="understanding-teams-app-capabilities"></a>Grundlegendes zu den Funktionen von Teams-Apps

*Funktionen* sind die Erweiterungspunkte für das Erstellen von Apps auf der Microsoft Teams-Plattform.

Es gibt mehrere Möglichkeiten, Teams zu erweitern, sodass jede App einzigartig ist: Einige haben nur eine Funktion (z. B. einen Webhook), während andere über einige Möglichkeiten verfügen, benutzern Optionen zu geben. Beispielsweise könnte Ihre App Daten an einem zentralen Ort (Registerkarte) anzeigen und dieselben Informationen über eine Unterhaltungsschnittstelle (Bot) präsentieren.

Ihre Teams-App verfügt über eine oder alle der folgenden Kernfunktionen:

* [Registerkarten](../tabs/what-are-tabs.md)
* [Messaging-Erweiterungen](../messaging-extensions/what-are-messaging-extensions.md)
* [Bots](../bots/what-are-bots.md)
* [Webhooks und Connectors](../webhooks-and-connectors/what-are-webhooks-and-connectors.md)

Ihre App kann auch erweiterte Funktionen nutzen, z. B. die [Microsoft Graph-API für Teams.](https://docs.microsoft.com/graph/teams-concept-overview)

In der folgenden Abbildung finden Sie eine Vorstellung davon, welche Funktionen die features bereitstellen würden, die Sie in Ihrer App wünschen.

:::image type="content" source="../assets/images/capabilities-overview.png" alt-text="Mindmap, die zeigt, welche Teams-App-Funktionen es gibt.":::

## <a name="doing-whats-best-for-your-users"></a>Tun, was für Ihre Benutzer am besten ist

Wenn Sie sich mit der Entwicklung von Teams-Apps vertraut machen, beginnen Sie, ihre Feinheiten zu verstehen. Es gibt mehr als eine Möglichkeit, bestimmte Features zu erstellen (z. B. das Sammeln von Benutzereingaben). Beispielsweise können Sie ein webbasiertes Formular mithilfe einer in eine Registerkarte `<iframe>` einbetten. Sie können dies auch auf einer Registerkarte mithilfe eines Aufgabenmoduls, einer Teams-UI-Konvention, tun, um eine systemeigenere Oberfläche zu erhalten, die Ihren Benutzern vielleicht lieber ist.

Die Auswahl der richtigen Funktionen und des richtigen Designs kommt dazu, zunächst die Verwendungsfälle [Ihrer Zielgruppe zu verstehen.](../concepts/design/understand-use-cases.md)
