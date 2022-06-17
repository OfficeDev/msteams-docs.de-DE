---
title: Entwickeln von Nachrichtenerweiterungen
description: In diesem Modul erfahren Sie, wie Sie mit Nachrichtenerweiterungen in Microsoft Teams
ms.topic: overview
ms.localizationpriority: medium
ms.openlocfilehash: c81df30b71bbdba19842e45f06b4c9bb930e4c0d
ms.sourcegitcommit: ca84b5fe5d3b97f377ce5cca41c48afa95496e28
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2022
ms.locfileid: "66143977"
---
# <a name="develop-message-extensions-for-microsoft-teams"></a>Entwickeln von Nachrichtenerweiterungen für Microsoft Teams

[!include[v3-to-v4-SDK-pointer](~/includes/v3-to-v4-pointer-me.md)]

Nachrichtenerweiterungen sind eine leistungsstarke Möglichkeit für Benutzer, über Microsoft Teams mit Ihrer App in Kontakt zu treten. Mit dieser Funktion können Benutzer Informationen in Ihrem Dienst abfragen oder posten und diese Informationen in Form von Karten direkt in einer Nachricht posten.

![Beispiel für eine Nachrichtenerweiterungskarte](~/assets/images/compose-extensions/ceexample.png)

Nachrichtenerweiterungen werden am unteren Rand des Felds zum Verfassen angezeigt. Einige sind integriert, z. B. Emoji, GIF und Aufkleber. Wählen Sie die Schaltfläche " **Weitere Optionen** (**&#8943;**) aus, um andere Nachrichtenerweiterungen anzuzeigen, einschließlich derer, die Sie aus dem App-Katalog hinzufügen oder sich selbst hochladen.

Wie würden Sie Nachrichtenerweiterungen verwenden? Hier sind einige Möglichkeiten:

* Arbeitselemente und Fehler.
* Kundensupporttickets.
* Verwendungsdiagramme und Berichte.
* Bilder und Medieninhalte.
* Verkaufschancen und Leads.

## <a name="types-of-message-extensions"></a>Arten von Nachrichtenerweiterungen

Es gibt in erster Linie zwei Arten von Nachrichtenerweiterungen, die Sie heute für Teams erstellen können. Die folgenden Themen führen Sie durch den Erstellungsprozess:

* [Suchbasierte Nachrichtenerweiterungen](~/resources/messaging-extension-v3/search-extensions.md): Fragen Sie Ihren Dienst nach Informationen ab, und fügen Sie diese in eine Nachricht ein. Beispiel: Nachschlagen eines Arbeitselements
* [Aktionsbasierte Nachrichtenerweiterungen](~/resources/messaging-extension-v3/create-extensions.md): Sammeln Sie Informationen vom Benutzer, und posten Sie sie bei einem Drittanbieterdienst. Beispiel: Erstellen eines Arbeitselements
