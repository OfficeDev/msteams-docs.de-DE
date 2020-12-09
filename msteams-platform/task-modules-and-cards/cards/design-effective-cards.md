---
title: Entwerfen von adaptiven Karten für Ihre APP
description: Hier erfahren Sie, wie Sie Adaptive Karten für Teams entwerfen und das Microsoft Teams UI Kit erhalten.
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: bd48846284620415cc8cadabc59f2ab7b61d5189
ms.sourcegitcommit: c102da958759c13aa9e0f81bde1cffb34a8bef34
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/09/2020
ms.locfileid: "49604522"
---
# <a name="designing-adaptive-cards-for-your-microsoft-teams-app"></a>Entwerfen von adaptiven Karten für Ihre Microsoft Teams-App

Eine Adaptive Karte enthält einen Freihandform Körper mit Kartenelementen und optionalen Aktionen. Adaptive Karten sind Aktions fähige Snippets von Inhalten, die Sie einer Unterhaltung über eine bot-oder Messaging-Erweiterung hinzufügen können. Mithilfe von Text, Grafiken und Schaltflächen bieten diese Karten eine umfassende Kommunikation mit Ihrem Publikum.

Das Adaptive Karten Framework wird in vielen Microsoft-Produkten, einschließlich Teams, verwendet. Sie können Karten innerhalb von Nachrichten an Benutzer über Bots oder Messaging-Erweiterungen senden. Benutzer können Aktionen auf Karten durchführen, wenn diese vorhanden sind.

:::image type="content" source="../../assets/images/adaptive-cards/adaptive-card-overview.png" alt-text="Beispiel zeigt eine Adaptive Karte." border="false":::

## <a name="microsoft-teams-ui-kit"></a>Microsoft Teams-UI-Kit

Ausführlichere Entwurfsrichtlinien für Adaptive Karten in Microsoft Teams, einschließlich der Elemente, die Sie nach Bedarf abrufen und ändern können, finden Sie im Microsoft Teams UI Kit. Das UI-Kit umfasst auch wichtige Themen wie Design, Barrierefreiheit und reaktionsschnelle Größenanpassung.

> [!div class="nextstepaction"]
> [Abrufen des Microsoft Teams UI Kit (Figma)](https://www.figma.com/community/file/916836509871353159)

## <a name="adaptive-cards-designer"></a>Adaptive Cards-Designer

Sie können auch mit dem Entwerfen Ihrer adaptiven Karten direkt im Browser beginnen.

> [!div class="nextstepaction"]
> [Testen des Adaptive Cards-Designers](https://adaptivecards.io/designer/)

## <a name="types-of-adaptive-cards"></a>Arten von adaptiven Karten

### <a name="hero"></a>Hero

Unsere größte Karte. Verwenden Sie für die Freigabe von Artikeln oder Szenarien, in denen ein Bild die meiste Geschichte erzählt.

:::image type="content" source="../../assets/images/adaptive-cards/hero-card.png" alt-text="Beispiel zeigt eine Adaptive Karte." border="false":::

### <a name="thumbnail"></a>Minaturansicht

Verwenden Sie zum Senden einer einfachen Aktion-Nachricht.

:::image type="content" source="../../assets/images/adaptive-cards/thumbnail-card.png" alt-text="Beispiel zeigt eine Adaptive Karte." border="false":::

### <a name="list"></a>List

Verwenden Sie in Szenarien, in denen der Benutzer ein Element aus einer Liste auswählen soll, aber für die Elemente keine große Erklärung erforderlich ist.

:::image type="content" source="../../assets/images/adaptive-cards/list-card.png" alt-text="Beispiel zeigt eine Adaptive Karte." border="false":::

### <a name="digest"></a>Digest

Verwenden Sie für Nachrichtenübersichten und Round-up-Beiträge. Hinweis: Wir empfehlen die thumbnailkarte für ein einzelnes Update oder ein neues Element.

:::image type="content" source="../../assets/images/adaptive-cards/digest-card.png" alt-text="Beispiel zeigt eine Adaptive Karte." border="false":::

### <a name="media"></a>Medien

Verwenden Sie diese Funktion, wenn Sie Text und Medien wie Audio oder Video kombinieren möchten.

:::image type="content" source="../../assets/images/adaptive-cards/media-card.png" alt-text="Beispiel zeigt eine Adaptive Karte." border="false":::

### <a name="people"></a>Personen

Am besten geeignet, wenn Sie effizient vermitteln möchten, wer eine Aufgabe eingeht.

:::image type="content" source="../../assets/images/adaptive-cards/people-card.png" alt-text="Beispiel zeigt eine Adaptive Karte." border="false":::

### <a name="request-ticket"></a>Ticket anfordern

Wird verwendet, um schnelle Eingaben eines Benutzers zu erhalten, um automatisch eine Aufgabe oder ein Ticket zu erstellen.

:::image type="content" source="../../assets/images/adaptive-cards/request-ticket-card.png" alt-text="Beispiel zeigt eine Adaptive Karte." border="false":::

### <a name="imageset"></a>ImageSet

Verwenden Sie, um mehrere Bildminiaturansichten zu senden.

:::image type="content" source="../../assets/images/adaptive-cards/image-set-card.png" alt-text="Beispiel zeigt eine Adaptive Karte." border="false":::

### <a name="actionset"></a>Für actionset

Verwenden Sie diese Option, wenn Sie möchten, dass der Benutzer eine Schaltfläche wählt und dann zusätzlich Benutzereingaben von derselben Karte sammelt.

:::image type="content" source="../../assets/images/adaptive-cards/action-set-card.png" alt-text="Beispiel zeigt eine Adaptive Karte." border="false":::

### <a name="choiceset"></a>Choiceset

Verwenden Sie, um mehrere Eingaben des Benutzers zu erfassen.

:::image type="content" source="../../assets/images/adaptive-cards/choice-set-card.png" alt-text="Beispiel zeigt eine Adaptive Karte." border="false":::

## <a name="anatomy"></a>Anatomie

:::image type="content" source="../../assets/images/adaptive-cards/anatomy.png" alt-text="Illustration mit der UI-Anatomie einer adaptiven Karte." border="false":::

Adaptive Karten haben eine große Flexibilität. Es wird jedoch dringend empfohlen, die folgenden Komponenten auf jeder Karte einzubinden:

|Leistungsindikator|Beschreibung|
|----------|-----------|
|A|**Kopfzeile**: transparente und prägnante Kopfzeilen, aber dennoch aussagekräftig.|
|B|**Body Copy**: Verwenden Sie, um Details zu übermitteln, die entweder zu lang oder nicht wichtig genug sind, um in die Kopfzeile einzubeziehen.|
|C|**Primäre Aktionen**: Fügen Sie als bewährte Methode 1-3 primäre Aktionen hinzu. Es sind maximal sechs zulässig.|

## <a name="best-practices"></a>Bewährte Methoden

### <a name="primary-and-secondary-actions"></a>Primäre und sekundäre Aktionen

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/adaptive-cards/actions-do.png" alt-text="Beispiel mit einer bewährten Methode für Adaptive Karten." border="false":::

#### <a name="do-use-up-to-six-primary-actions"></a>Do: Verwenden Sie bis zu sechs primäre Aktionen.

Während Adaptive Karten sechs primäre Aktionen unterstützen können, benötigen die meisten Karten dies nicht. Aktionen sollten klar, prägnant und geradlinig sein. Weniger ist mehr.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/adaptive-cards/actions-dont.png" alt-text="Beispiel mit einer bewährten Methode für Adaptive Karten." border="false":::

#### <a name="dont-use-more-than-six-primary-actions"></a>Nicht: mehr als sechs primäre Aktionen verwenden

Adaptive Karten sollten schnelle, umsetzbare Inhalte darstellen. Zu viele Aktionen können einen Benutzer überwältigen.

   :::column-end:::
:::row-end:::

### <a name="frequency"></a>Häufigkeit

:::image type="content" source="../../assets/images/adaptive-cards/frequency-do.png" alt-text="Beispiel mit einer bewährten Methode für Adaptive Karten." border="false":::

#### <a name="do-be-concise"></a>Do: prägnant sein

Es ist ganz einfach, mehrere Karten in eine Unterhaltung zu senden, aber sobald die Karten aus dem Blickfeld geraten, werden Sie nicht mehr so nützlich. Versuchen Sie, sich auf das Wesentliche zu beschränken. Dies gilt insbesondere für einen Kanal, in dem Benutzer eine geringere Toleranz für das als "Rauschen" wahrgenommene haben.
