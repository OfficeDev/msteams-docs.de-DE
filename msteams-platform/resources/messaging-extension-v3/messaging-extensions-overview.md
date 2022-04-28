---
title: Entwickeln von Nachrichtenerweiterungen
description: Beschreibt die ersten Schritte mit Nachrichtenerweiterungen in Microsoft Teams
ms.topic: overview
ms.localizationpriority: medium
keywords: Messaging-Erweiterungen für Teams-Messaging-Erweiterungen
ms.openlocfilehash: 8d44ea8ffe3c265a5c65ae2e842fe4f55f950e58
ms.sourcegitcommit: f15bd0e90eafb00e00cf11183b129038de8354af
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/28/2022
ms.locfileid: "65111920"
---
# <a name="develop-message-extensions-for-microsoft-teams"></a>Entwickeln von Nachrichtenerweiterungen für Microsoft Teams

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-me.md)]

Nachrichtenerweiterungen sind eine leistungsstarke Möglichkeit für Benutzer, über Microsoft Teams mit Ihrer App in Kontakt zu treten. Mit dieser Funktion können Benutzer Informationen in Ihrem Dienst abfragen oder posten und diese Informationen in Form von Karten direkt in einer Nachricht posten.

![Beispiel für eine Nachrichtenerweiterungskarte](~/assets/images/compose-extensions/ceexample.png)

Nachrichtenerweiterungen werden am unteren Rand des Felds zum Verfassen angezeigt. Einige sind integriert, z. B. Emoji, Giphy und Aufkleber. Wählen Sie die Schaltfläche " **Weitere Optionen** (**&#8943;**) aus, um andere Nachrichtenerweiterungen anzuzeigen, einschließlich derer, die Sie aus dem App-Katalog hinzufügen oder sich selbst hochladen.

Wie würden Sie Nachrichtenerweiterungen verwenden? Hier sind einige Möglichkeiten:

* Arbeitselemente und Fehler
* Kundensupporttickets
* Verwendungsdiagramme und Berichte
* Bilder und Medieninhalte
* Verkaufschancen und Leads

## <a name="types-of-message-extensions"></a>Typen von Nachrichtenerweiterungen

Es gibt in erster Linie zwei Arten von Nachrichtenerweiterungen, die Sie heute für Teams erstellen können. Die folgenden Themen führen Sie durch den Erstellungsprozess:

* [Suchbasierte Nachrichtenerweiterungen](~/resources/messaging-extension-v3/search-extensions.md): Fragen Sie Ihren Dienst nach Informationen ab, und fügen Sie diese in eine Nachricht ein. Beispiel: Nachschlagen eines Arbeitselements
* [Aktionsbasierte Nachrichtenerweiterungen](~/resources/messaging-extension-v3/create-extensions.md): Sammeln Sie Informationen vom Benutzer, und posten Sie sie bei einem Drittanbieterdienst. Beispiel: Erstellen eines Arbeitselements
