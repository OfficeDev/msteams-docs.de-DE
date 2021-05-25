---
title: Entwerfen adaptiver Karten für Ihre App
description: Erfahren Sie, wie Sie adaptive Karten für Teams entwerfen und das Microsoft Teams UI Kit erhalten.
localization_priority: Normal
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: b4d5f43268c7bd5afecb56d26eb0d49ed6c9002b
ms.sourcegitcommit: e1fe46c574cec378319814f8213209ad3063b2c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2021
ms.locfileid: "52630282"
---
# <a name="designing-adaptive-cards-for-your-microsoft-teams-app"></a>Entwerfen adaptiver Karten für Ihre Microsoft Teams App

Eine adaptive Karte enthält einen Freihandformtext mit Kartenelementen und optionalen Aktionen. Adaptive Karten sind aktionenfähige Codeausschnitte von Inhalten, die Sie einer Unterhaltung über einen Bot oder eine Messagingerweiterung hinzufügen können. Mithilfe von Text, Grafiken und Schaltflächen bieten diese Karten eine umfassende Kommunikation für Ihre Zielgruppe.

Das Adaptive Card-Framework wird in vielen Microsoft-Produkten verwendet, einschließlich Teams. Sie können Karten innerhalb von Nachrichten über Bots oder Messagingerweiterungen an Benutzer senden. Benutzer können auch Aktionen auf Karten ausführen, wenn vorhanden.

:::image type="content" source="../../assets/images/adaptive-cards/adaptive-card-overview.png" alt-text="Übersichtsbeispiel einer adaptiven Karte." border="false":::

## <a name="microsoft-teams-ui-kit"></a>Microsoft Teams-UI-Kit

Umfassendere Entwurfsrichtlinien für adaptive Karten finden Sie in Teams, einschließlich Elementen, die Sie bei Bedarf packen und ändern können, im Microsoft Teams UI Kit. Das Benutzeroberflächenkit behandelt auch wichtige Themen wie Design, Barrierefreiheit und reaktionsschnelle Größenanpassung.

> [!div class="nextstepaction"]
> [Holen Sie sich das Microsoft Teams-UI-Kit (Figma)](https://www.figma.com/community/file/916836509871353159)

## <a name="adaptive-cards-designer"></a>Designer für adaptive Karten

Sie können ihre adaptiven Karten auch direkt im Browser entwerfen.

> [!div class="nextstepaction"]
> [Testen des Designers für adaptive Karten](https://adaptivecards.io/designer/)

## <a name="types-of-adaptive-cards"></a>Typen adaptiver Karten

### <a name="hero"></a>Hero

Unsere größte Karte. Wird für die Freigabe von Artikeln oder Szenarien verwendet, in denen ein Bild den größten Teil der Geschichte beschreibt.

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/adaptive-cards/hero-card.png" alt-text="Beispiel zeigt eine Adaptive Card Hero Card." border="false":::

# <a name="mobile"></a>[Mobil](#tab/mobile)

:::image type="content" source="../../assets/images/adaptive-cards/mobile-hero-card.png" alt-text="Beispiel zeigt eine Adaptive Card Hero Card auf Mobilgeräten." border="false":::

---

### <a name="thumbnail"></a>Miniaturansicht

Verwenden Sie diese Methode zum Senden einer einfachen Nachricht mit Aktionen.

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/adaptive-cards/thumbnail-card.png" alt-text="Beispiel zeigt eine Miniaturansichtskarte für adaptive Karten." border="false":::

# <a name="mobile"></a>[Mobil](#tab/mobile)

:::image type="content" source="../../assets/images/adaptive-cards/mobile-thumbnail-card.png" alt-text="Beispiel zeigt eine Miniaturansichtskarte für adaptive Karten auf Mobilgeräten." border="false":::

---

### <a name="list"></a>Liste

Wird in Szenarien verwendet, in denen der Benutzer ein Element aus einer Liste auswählen soll, die Elemente jedoch nicht viel Erläuterung benötigen.

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/adaptive-cards/list-card.png" alt-text="Beispiel zeigt eine Listenkarte für adaptive Karten." border="false":::

# <a name="mobile"></a>[Mobil](#tab/mobile)

:::image type="content" source="../../assets/images/adaptive-cards/mobile-list-card.png" alt-text="Beispiel zeigt eine Listenkarte für adaptive Karten auf Mobilgeräten." border="false":::

---
Use for news digests and round-up posts. Note: We recommend the thumbnail card for a single update or news item.
':::image type="content" source="../../assets/images/adaptive-cards/digest-card.png" alt-text="Example shows an Adaptive Card digest card." border="false"::': null
':::image type="content" source="../../assets/images/adaptive-cards/mobile-digest-card.png" alt-text="Example shows an Adaptive Card digest card on mobile." border="false"::': null
---

### <a name="media"></a>Medien

Verwenden Sie, wenn Sie Text und Medien, z. B. Audio oder Video, kombinieren möchten.

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/adaptive-cards/media-card.png" alt-text="Beispiel zeigt eine Medienkarte für adaptive Karten." border="false":::

# <a name="mobile"></a>[Mobil](#tab/mobile)

:::image type="content" source="../../assets/images/adaptive-cards/mobile-media-card.png" alt-text="Beispiel zeigt eine Medienkarte für adaptive Karten auf Mobilgeräten." border="false":::

---

### <a name="people"></a>Personen

Am besten, wenn Sie effizient vermitteln, wer an einer Aufgabe beteiligt ist.

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/adaptive-cards/people-card.png" alt-text="Beispiel zeigt eine Adaptive Card-Personenkarte." border="false":::

# <a name="mobile"></a>[Mobil](#tab/mobile)

:::image type="content" source="../../assets/images/adaptive-cards/mobile-people-card.png" alt-text="Beispiel zeigt eine Adaptive Card-Personenkarte auf Mobilgeräten." border="false":::

---

### <a name="request-ticket"></a>Ticket anfordern

Verwenden Sie, um schnelle Eingaben von einem Benutzer zu erhalten, um automatisch eine Aufgabe oder ein Ticket zu erstellen.

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/adaptive-cards/request-ticket-card.png" alt-text="Beispiel zeigt eine Ticketkarte für adaptive Kartenanforderung." border="false":::

# <a name="mobile"></a>[Mobil](#tab/mobile)

:::image type="content" source="../../assets/images/adaptive-cards/mobile-request-ticket-card.png" alt-text="Beispiel zeigt eine Adaptive Card-Anforderungsticketkarte auf Mobilgeräten." border="false":::

---

### <a name="image-set"></a>Bildsatz

Verwenden Sie zum Senden mehrerer Bildminiaturansichten.

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/adaptive-cards/image-set-card.png" alt-text="Beispiel zeigt eine Adaptive Card-Bildsatzkarte." border="false":::

# <a name="mobile"></a>[Mobil](#tab/mobile)

:::image type="content" source="../../assets/images/adaptive-cards/mobile-image-set-card.png" alt-text="Beispiel zeigt eine Adaptive Card-Bildsatzkarte auf Mobilgeräten." border="false":::

---

### <a name="action-set"></a>Aktionssatz

Verwenden Sie diese Option, wenn der Benutzer eine Schaltfläche auswählen und dann die Benutzereingaben von derselben Karte erfassen soll.

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/adaptive-cards/action-set-card.png" alt-text="Beispiel zeigt eine Aktionssatzkarte für adaptive Karten." border="false":::

# <a name="mobile"></a>[Mobil](#tab/mobile)

:::image type="content" source="../../assets/images/adaptive-cards/mobile-action-set-card.png" alt-text="Beispiel zeigt eine Aktionssatzkarte für adaptive Karten auf Mobilgeräten." border="false":::

---

### <a name="choice-set"></a>Auswahlsatz

Verwenden Sie, um mehrere Eingaben vom Benutzer zu erfassen.

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/adaptive-cards/choice-set-card.png" alt-text="Beispiel zeigt eine Auswahlkarte für adaptive Karten." border="false":::

# <a name="mobile"></a>[Mobil](#tab/mobile)

:::image type="content" source="../../assets/images/adaptive-cards/mobile-choice-set-card.png" alt-text="Beispiel zeigt eine Auswahlkarte für adaptive Karten auf Mobilgeräten." border="false":::

---

## <a name="anatomy"></a>Anatomie

Adaptive Karten haben eine menge Flexibilität. Es wird jedoch dringend empfohlen, die folgenden Komponenten auf jeder Karte zu verwenden.

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/adaptive-cards/anatomy.png" alt-text="EExample zeigt adaptive Kartenanatomie." border="false":::

# <a name="mobile"></a>[Mobil](#tab/mobile)

:::image type="content" source="../../assets/images/adaptive-cards/mobile-anatomy.png" alt-text="Beispiel zeigt adaptive Kartenanatomie auf Mobilgeräten." border="false":::

---

|Leistungsindikator|Beschreibung|
|----------|-----------|
|A|**Header**: Machen Sie Ihre Kopfzeilen klar und präzise.|
|B|**Textkörperkopie:** Übermitteln Sie Details, die entweder zu lang oder nicht wichtig genug sind, um in die Kopfzeile zu enthalten.|
|C|**Primäre Aktionen:** Als bewährte Methode werden 1-3 primäre Aktionen bezeichnet. Sie können bis zu sechs Personen haben.|

## <a name="best-practices"></a>Bewährte Methoden

Verwenden Sie diese Empfehlungen, um eine hochwertige App-Erfahrung zu erstellen.

### <a name="primary-and-secondary-actions"></a>Primäre und sekundäre Aktionen

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/adaptive-cards/actions-do.png" alt-text="Bewährte Methode, wie Sie nur einen kleinen Satz von Aktionen auf einer adaptiven Karte verwenden sollten." border="false":::

#### <a name="do-use-up-to-six-primary-actions"></a>Do: Verwenden von bis zu sechs primären Aktionen

Adaptive Karten können zwar sechs primäre Aktionen unterstützen, die meisten Karten benötigen dies jedoch nicht. Die Aktionen sollten klar, präzise und direkt sein. Weniger ist mehr.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/adaptive-cards/actions-dont.png" alt-text="Bewährte Methode, um Benutzer nicht mit zu vielen Aktionen auf einer adaptiven Karte zu überfordern." border="false":::

#### <a name="dont-use-more-than-six-primary-actions"></a>Don't: Verwenden von mehr als sechs primären Aktionen

Adaptive Karten sollten schnell aktionenfähige Inhalte enthalten. Zu viele Aktionen können einen Benutzer überfordern.

   :::column-end:::
:::row-end:::

### <a name="frequency"></a>Häufigkeit

:::image type="content" source="../../assets/images/adaptive-cards/frequency-do.png" alt-text="Bewährte Methode zur Häufigkeit adaptiver Karten." border="false":::

#### <a name="do-be-concise"></a>Do: Kurz sein

Es ist einfach, mehrere Karten in eine Unterhaltung zu senden, aber sobald Karten nicht mehr angezeigt werden, werden sie weniger nützlich. Versuchen Sie, sich auf das Wesentliche zu beschränken. Dies gilt insbesondere in einem Kanal, in dem Benutzer weniger Toleranz für das haben, was sie als "Rauschen" wahrnehmen.
