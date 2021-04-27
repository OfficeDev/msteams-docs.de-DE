---
title: Entwerfen adaptiver Karten für Ihre App
description: Erfahren Sie, wie Sie adaptive Karten für Teams entwerfen und das Microsoft Teams UI Kit erhalten.
localization_priority: Normal
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 67a2882a0a687d5ccb48759419ecefcdf9396fc3
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020282"
---
# <a name="designing-adaptive-cards-for-your-microsoft-teams-app"></a>Entwerfen adaptiver Karten für Ihre Microsoft Teams-App

Eine adaptive Karte enthält einen Freihandformtext mit Kartenelementen und optionalen Aktionen. Adaptive Karten sind aktionenfähige Codeausschnitte von Inhalten, die Sie einer Unterhaltung über einen Bot oder eine Messagingerweiterung hinzufügen können. Mithilfe von Text, Grafiken und Schaltflächen bieten diese Karten eine umfassende Kommunikation für Ihre Zielgruppe.

Das Adaptive Card-Framework wird in vielen Microsoft-Produkten verwendet, einschließlich Teams. Sie können Karten innerhalb von Nachrichten über Bots oder Messagingerweiterungen an Benutzer senden. Benutzer können aktionen auf Karten ausführen, wenn vorhanden.

:::image type="content" source="../../assets/images/adaptive-cards/adaptive-card-overview.png" alt-text="Beispiel zeigt eine adaptive Karte." border="false":::

## <a name="microsoft-teams-ui-kit"></a>Microsoft Teams-UI-Kit

Umfassendere Entwurfsrichtlinien für adaptive Karten in Teams, einschließlich Elemente, die Sie bei Bedarf packen und ändern können, finden Sie im Microsoft Teams UI Kit. Das Benutzeroberflächenkit behandelt auch wichtige Themen wie Design, Barrierefreiheit und reaktionsschnelle Größenanpassung.

> [!div class="nextstepaction"]
> [Holen Sie sich das Microsoft Teams-UI-Kit (Figma)](https://www.figma.com/community/file/916836509871353159)

## <a name="adaptive-cards-designer"></a>Designer für adaptive Karten

Sie können ihre adaptiven Karten auch direkt im Browser entwerfen.

> [!div class="nextstepaction"]
> [Testen des Designers für adaptive Karten](https://adaptivecards.io/designer/)

## <a name="types-of-adaptive-cards"></a>Typen adaptiver Karten

### <a name="hero"></a>Hero

Unsere größte Karte. Wird für die Freigabe von Artikeln oder Szenarien verwendet, in denen ein Bild den größten Teil der Geschichte beschreibt.

:::image type="content" source="../../assets/images/adaptive-cards/hero-card.png" alt-text="Beispiel zeigt adaptive Karte." border="false":::

### <a name="thumbnail"></a>Miniaturansicht

Verwenden Sie diese Methode zum Senden einer einfachen Nachricht mit Aktionen.

:::image type="content" source="../../assets/images/adaptive-cards/thumbnail-card.png" alt-text="Beispiel für eine adaptive Karte." border="false":::

### <a name="list"></a>Liste

Wird in Szenarien verwendet, in denen der Benutzer ein Element aus einer Liste auswählen soll, die Elemente jedoch nicht viel Erläuterung benötigen.

:::image type="content" source="../../assets/images/adaptive-cards/list-card.png" alt-text="Beispiel für adaptive Karte." border="false":::

### <a name="digest"></a>Digest

Wird für News digests und Round-up-Beiträge verwendet. Hinweis: Wir empfehlen die Miniaturansichtskarte für ein einzelnes Update oder Newselement.

:::image type="content" source="../../assets/images/adaptive-cards/digest-card.png" alt-text="Abbildung zeigt eine adaptive Karte." border="false":::

### <a name="media"></a>Medien

Verwenden Sie, wenn Sie Text und Medien, z. B. Audio oder Video, kombinieren möchten.

:::image type="content" source="../../assets/images/adaptive-cards/media-card.png" alt-text="Abbildung zeigt adaptive Karte." border="false":::

### <a name="people"></a>Personen

Am besten, wenn Sie effizient vermitteln, wer an einer Aufgabe beteiligt ist.

:::image type="content" source="../../assets/images/adaptive-cards/people-card.png" alt-text="Abbildung einer adaptiven Karte." border="false":::

### <a name="request-ticket"></a>Ticket anfordern

Verwenden Sie, um schnelle Eingaben von einem Benutzer zu erhalten, um automatisch eine Aufgabe oder ein Ticket zu erstellen.

:::image type="content" source="../../assets/images/adaptive-cards/request-ticket-card.png" alt-text="Abbildung der adaptiven Karte." border="false":::

### <a name="imageset"></a>ImageSet

Verwenden Sie zum Senden mehrerer Bildminiaturansichten.

:::image type="content" source="../../assets/images/adaptive-cards/image-set-card.png" alt-text="Beispiel einer adaptiven Karte." border="false":::

### <a name="actionset"></a>ActionSet

Verwenden Sie diese Option, wenn der Benutzer eine Schaltfläche auswählen und dann die Benutzereingaben von derselben Karte erfassen soll.

:::image type="content" source="../../assets/images/adaptive-cards/action-set-card.png" alt-text="Beispiel zeigt eine adaptive Karte." border="false":::

### <a name="choiceset"></a>ChoiceSet

Verwenden Sie, um mehrere Eingaben vom Benutzer zu erfassen.

:::image type="content" source="../../assets/images/adaptive-cards/choice-set-card.png" alt-text="Beispiel zeigt eine adaptive Karte an." border="false":::

## <a name="anatomy"></a>Anatomie

:::image type="content" source="../../assets/images/adaptive-cards/anatomy.png" alt-text="Abbildung der Ui-Anatomie einer adaptiven Karte." border="false":::

Adaptive Karten haben eine menge Flexibilität. Es wird jedoch dringend empfohlen, die folgenden Komponenten auf jeder Karte zu verwenden:

|Leistungsindikator|Beschreibung|
|----------|-----------|
|A|**Header**: Machen Sie Kopfzeilen klar und prägnant, aber beschreibend.|
|B|**Textkörperkopie:** Verwenden Sie, um Details zu vermitteln, die entweder zu lang oder nicht wichtig genug sind, um sie in die Kopfzeile zu einfügen.|
|C|**Primäre Aktionen:** Als bewährte Methode werden 1-3 primäre Aktionen bezeichnet. Maximal sechs sind zulässig.|

## <a name="best-practices"></a>Bewährte Methoden

### <a name="primary-and-secondary-actions"></a>Primäre und sekundäre Aktionen

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/adaptive-cards/actions-do.png" alt-text="Beispiel für eine bewährte Methode für adaptive Karten." border="false":::

#### <a name="do-use-up-to-six-primary-actions"></a>Do: Verwenden von bis zu sechs primären Aktionen

Adaptive Karten können zwar sechs primäre Aktionen unterstützen, die meisten Karten benötigen dies jedoch nicht. Die Aktionen sollten klar, präzise und direkt sein. Weniger ist mehr.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/adaptive-cards/actions-dont.png" alt-text="Beispiel zeigt eine bewährte Methode für adaptive Karten." border="false":::

#### <a name="dont-use-more-than-six-primary-actions"></a>Don't: Verwenden von mehr als sechs primären Aktionen

Adaptive Karten sollten schnell aktionenfähige Inhalte enthalten. Zu viele Aktionen können einen Benutzer überfordern.

   :::column-end:::
:::row-end:::

### <a name="frequency"></a>Häufigkeit

:::image type="content" source="../../assets/images/adaptive-cards/frequency-do.png" alt-text="Abbildung, in der eine bewährte Methode für adaptive Karten angezeigt wird." border="false":::

#### <a name="do-be-concise"></a>Do: Kurz sein

Es ist einfach, mehrere Karten in eine Unterhaltung zu senden, aber sobald Karten nicht mehr angezeigt werden, werden sie weniger nützlich. Versuchen Sie, sich auf das Wesentliche zu beschränken. Dies gilt insbesondere in einem Kanal, in dem Benutzer weniger Toleranz für das haben, was sie als "Rauschen" wahrnehmen.
