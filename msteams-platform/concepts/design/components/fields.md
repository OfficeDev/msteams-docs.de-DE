---
title: Referenz zu Entwurfsrichtlinien
description: Beschreibt die Richtlinien für die Verwendung von Feldern und Flyouts in ihren apps.
keywords: Teams-Entwurfsrichtlinien Referenzkomponenten Felder und Flyouts
ms.openlocfilehash: 0f62d38bf961ae79b05c599638cefb3c76f46ed4
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674511"
---
# <a name="fields-and-flyouts"></a>Felder und Flyouts

---

## <a name="fields"></a>Felder

Felder sind Bereiche, in denen Benutzer Text eingeben können.

### <a name="padding-and-size"></a>Textabstand und Größe

Einzeilige Textfelder sind eine feste Höhe von Bund, die der Höhe anderer Komponenten entspricht. Einige Textfelder wie Beschreibungsfelder sind möglicherweise vertikal höher, sodass mehr Text zulässig ist.
[!include[Padding and size](~/includes/design/fields-image-padding.html)]

### <a name="states"></a>Staaten

Dies sind die Zustände unserer Textfelder. Text Felder sind in unterschiedlichen Zuständen vorhanden. Wir haben spezielle Designs für neun mögliche Szenarien, einschließlich (von oben nach unten): resting-Textfeld, Tastatur im Fokus und Cursor innerhalb des Felds, Tastatur im Fokus mit eingegebenem Text, Fehlerbehandlung erfolgreich, Fehlerbehandlung ist fehlgeschlagen, Klartext Feld (einschließlich eines X-Symbols), Suchfeld (einschließlich eines suchsymbols), eines Lade Felds und eines deaktivierten Felds.
[!include[Field states](~/includes/design/fields-image-states.html)]

### <a name="formatting-help-text-and-labels"></a>Formatieren von Hilfe Text und Beschriftungen

Felder können Platzhaltertext enthalten, um ein Beispiel für die Art der erforderlichen Informationen anzugeben. Sie können auch Bezeichnungen enthalten, die dem Benutzer mehr Kontext geben. Innerhalb eines Felds sollte Ihr Text immer linksbündig ausgerichtet sein. Wir verwenden auch hier in der Satz Verkleidung.

Wir verwenden Segoe UI Regular bei 12 pt (Caption) und $App-Gray-02 für Bezeichnungen. Für Hilfetext verwenden wir Segoe UI Regular bei 14 pt (Base) und $App-Gray-02.
[!include[Fields typography](~/includes/design/fields-image-typography.html)]

---

## <a name="flyouts"></a>Flyouts

Flyouts sind leichter als Dialogfelder und können schnell abgewiesen werden. Sie können Schaltflächen, Felder und andere Komponenten enthalten.
[!include[Flyouts](~/includes/design/flyouts-image.html)]

### <a name="sizing-and-padding"></a>Größenanpassung und Auffüllung

Links und rechts neben dem Inhalt wird ein 16px-Abstand empfohlen.
[!include[Flyouts size and padding](~/includes/design/flyouts-image-sizepadding.html)]

### <a name="placement"></a>Platzierung

Flyouts sind kontextbezogen und sollten oberhalb, unterhalb oder neben dem Element platziert werden, das es ausgelöst hat.

### <a name="scrolling"></a>Scrollen

Der Header bleibt an der richtigen Stelle, um dem Inhalt, in dem ein Bildlauf durchgeführt wird, Kontext zu geben.
[!include[Flyouts scrolling](~/includes/design/flyouts-image-scrolling.html)]

## <a name="mobile"></a>Mobil

Felder sind Texteingabefelder, die Eingaben von Benutzern annehmen. Flyout-Menüs sind horizontale Popupfenster, die im oberen Bereich angezeigt werden und zum Anzeigen detaillierter Informationen zu einem Element verwendet werden können.

### <a name="field-controls"></a>Feldsteuerelemente

[!include[Mobile fields](~/includes/design/fields-mobile-image.html)]

### <a name="flyout-menu-list-controls"></a>Flyout-Menü Listensteuerelemente

[!include[Mobile flyout menu controls](~/includes/design/flyout-menu-mobile-image.html)]
