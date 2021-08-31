---
title: Entwerfen adaptiver Karten für Ihre App
description: Erfahren Sie, wie Sie adaptive Karten für Teams entwerfen und das Microsoft Teams UI Kit erhalten.
localization_priority: Priority
ms.topic: conceptual
ms.author: lajanuar
ms.openlocfilehash: 28a6b794b9ebae88f8895013f945cbf3b4a91e87
ms.sourcegitcommit: 306b6e8cb3aac8bfda10ef3999467a797d64539d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 08/20/2021
ms.locfileid: "58408657"
---
# <a name="designing-adaptive-cards-for-your-microsoft-teams-app"></a>Entwerfen adaptiver Karten für Ihre Microsoft Teams-App

Eine adaptive Karte enthält einen Freihandform-Textkörper mit Kartenelementen und optionalen Aktionen. Adaptive Karten sind Aktionen erfordernde Inhaltsausschnitte, die Sie einer Unterhaltung über einen Bot oder eine Messagingerweiterung hinzufügen können. Mithilfe von Text, Grafiken und Schaltflächen ermöglichen diese Karten eine umfassende Kommunikation mit Ihrer Zielgruppe.

Das Framework für adaptive Karten wird in vielen Microsoft-Produkten verwendet, einschließlich Microsoft Teams. Sie können Karten in Nachrichten über Bots oder Messagingerweiterungen an Benutzer senden. Benutzer können auch Aktionen auf Karten durchführen, wenn diese bereitgestellt werden.

:::image type="content" source="../../assets/images/adaptive-cards/adaptive-card-overview.png" alt-text="Übersichtsbeispiel für eine adaptive Karte." border="false":::

## <a name="microsoft-teams-ui-kit"></a>Microsoft Teams-UI-Kit

Umfassendere Entwurfsrichtlinien für adaptive Karten, einschließlich Elemente, die Sie nach Bedarf abrufen und ändern können, finden Sie im Microsoft Teams-UI-Kit. Das UI-Kit deckt auch wesentliche Themen wie Designs, Barrierefreiheit und dynamische Größenanpassung ab.

> [!div class="nextstepaction"]
> [Holen Sie sich das Microsoft Teams-UI-Kit (Figma)](https://www.figma.com/community/file/916836509871353159)

## <a name="adaptive-cards-designer"></a>Designer für adaptive Karten

Sie können ihre adaptiven Karten auch direkt im Browser entwerfen.

> [!div class="nextstepaction"]
> [Designer für adaptive Karten testen](https://adaptivecards.io/designer/)

## <a name="types-of-adaptive-cards"></a>Typen von adaptiven Karten

### <a name="hero"></a>Hero

Unsere größte Karte. Wird für die Freigabe von Artikeln oder Szenarien verwendet, in denen ein Bild den größten Teil der Geschichte erzählt.

#### <a name="mobile"></a>Mobil

:::image type="content" source="../../assets/images/adaptive-cards/mobile-hero-card.png" alt-text="Beispiel einer adaptiven Hero-Karte auf einem Mobilgerät." border="false":::

#### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/adaptive-cards/hero-card.png" alt-text="Beispiel einer adaptiven Hero-Karte." border="false":::

### <a name="thumbnail"></a>Miniaturansicht

Wird zum Senden einer einfachen, Aktionen erfordernden Nachricht verwendet.

#### <a name="mobile"></a>Mobil

:::image type="content" source="../../assets/images/adaptive-cards/mobile-thumbnail-card.png" alt-text="Beispiel einer adaptiven Miniaturansichtskarte auf einem Mobilgerät." border="false":::

#### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/adaptive-cards/thumbnail-card.png" alt-text="Beispiel einer adaptiven Miniaturansichtskarte." border="false":::

### <a name="list"></a>Liste

Wird in Szenarien verwendet, in denen der Benutzer ein Element aus einer Liste auswählen soll, die Elemente jedoch nicht viel Erklärung benötigen.

#### <a name="mobile"></a>Mobil

:::image type="content" source="../../assets/images/adaptive-cards/mobile-list-card.png" alt-text="Beispiel einer adaptiven Listenkarte auf einem Mobilgerät." border="false":::

#### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/adaptive-cards/list-card.png" alt-text="Beispiel einer adaptiven Listenkarte." border="false":::

### <a name="digest"></a>Digest

Wird für News-Digests und Round-Up-Beiträge verwendet. Hinweis: Wir empfehlen ein einzelnes Update oder Newselement der Miniaturansichtskarte.

#### <a name="mobile"></a>Mobil

:::image type="content" source="../../assets/images/adaptive-cards/mobile-digest-card.png" alt-text="Beispiel einer adaptiven Digestkarte auf einem Mobilgerät." border="false":::

#### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/adaptive-cards/digest-card.png" alt-text="Beispiel einer adaptiven Digestkarte." border="false":::

### <a name="media"></a>Medien

Wird verwendet, wenn Sie Text und Medien kombinieren möchten, z. B. Audio oder Video.

#### <a name="mobile"></a>Mobil

:::image type="content" source="../../assets/images/adaptive-cards/mobile-media-card.png" alt-text="Beispiel einer adaptiven Medienkarte auf einem Mobilgerät." border="false":::

#### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/adaptive-cards/media-card.png" alt-text="Beispiel einer adaptiven Medienkarte." border="false":::

### <a name="people"></a>Personen

Am besten geeignet, wenn Sie effizient vermitteln möchten, wer an einer Aufgabe beteiligt ist.

#### <a name="mobile"></a>Mobil

:::image type="content" source="../../assets/images/adaptive-cards/mobile-people-card.png" alt-text="Beispiel einer adaptiven Personenkarte auf einem Mobilgerät." border="false":::

#### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/adaptive-cards/people-card.png" alt-text="Beispiel einer adaptiven Personenkarte." border="false":::

### <a name="request-ticket"></a>Anforderungsticket

Wird verwendet, um von einem Benutzer schnelle Eingaben zum automatischen Erstellen einer Aufgabe oder eines Tickets zu erhalten.

#### <a name="mobile"></a>Mobil

:::image type="content" source="../../assets/images/adaptive-cards/mobile-request-ticket-card.png" alt-text="Beispiel einer adaptiven Anforderungsticketkarte auf einem Mobilgerät." border="false":::

#### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/adaptive-cards/request-ticket-card.png" alt-text="Beispiel einer adaptiven Anforderungsticketkarte." border="false":::

### <a name="image-set"></a>Bildergruppe

Wird verwendet, um mehrere Miniaturansichten von Bildern zu senden.

#### <a name="mobile"></a>Mobil

:::image type="content" source="../../assets/images/adaptive-cards/mobile-image-set-card.png" alt-text="Beispiel einer adaptiven Bildergruppenkarte auf einem Mobilgerät." border="false":::

#### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/adaptive-cards/image-set-card.png" alt-text="Beispiel einer adaptiven Bildergruppenkarte." border="false":::

### <a name="action-set"></a>Aktionsgruppe

Wird verwendet, wenn der Benutzer eine Schaltfläche auswählen soll, und Sie dann zusätzliche Benutzereingaben über dieselbe Karte erfassen möchten.

#### <a name="mobile"></a>Mobil

:::image type="content" source="../../assets/images/adaptive-cards/mobile-action-set-card.png" alt-text="Beispiel einer adaptiven Aktionsgruppenkarte auf einem Mobilgerät." border="false":::

#### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/adaptive-cards/action-set-card.png" alt-text="Beispiel einer adaptiven Aktionsgruppenkarte." border="false":::

### <a name="choice-set"></a>Auswahlgruppe

Wird verwendet, um mehrere Eingaben vom Benutzer zu erfassen.

#### <a name="mobile"></a>Mobil

:::image type="content" source="../../assets/images/adaptive-cards/mobile-choice-set-card.png" alt-text="Beispiel einer adaptiven Auswahlgruppenkarte auf einem Mobilgerät." border="false":::

#### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/adaptive-cards/choice-set-card.png" alt-text="Beispiel einer adaptiven Auswahlgruppenkarte." border="false":::

## <a name="anatomy"></a>Anatomie

Adaptive Karten sind sehr flexibel. Es wird jedoch dringend empfohlen, mindestens die folgenden Komponenten auf jeder Karte zu verwenden.

#### <a name="mobile"></a>Mobil

:::image type="content" source="../../assets/images/adaptive-cards/mobile-anatomy.png" alt-text="Beispiel der Anatomie adaptiver Karten auf einem Mobilgerät." border="false":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|A|**Kopfzeile**: Sorgen Sie dafür, dass Ihre Kopfzeilen klar und präzise sind.|
|B|**Textkörper**: Übermitteln Sie hier Details, die entweder zu lang oder nicht wichtig genug sind, um sie in die Kopfzeile aufzunehmen.|
|C|**Primäre Aktionen**: Schließen Sie als bewährte Methode 1 bis 3 primäre Aktionen ein. Es können bis zu sechs eingefügt werden.|

#### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/adaptive-cards/anatomy.png" alt-text="Beispiel der Anatomie adaptiver Karten." border="false":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|A|**Kopfzeile**: Sorgen Sie dafür, dass Ihre Kopfzeilen klar und präzise sind.|
|B|**Textkörper**: Übermitteln Sie hier Details, die entweder zu lang oder nicht wichtig genug sind, um sie in die Kopfzeile aufzunehmen.|
|C|**Primäre Aktionen**: Schließen Sie als bewährte Methode 1 bis 3 primäre Aktionen ein. Es können bis zu sechs eingefügt werden.|

## <a name="best-practices"></a>Bewährte Methoden

Verwenden Sie diese Empfehlungen, um eine hochwertige App-Erfahrung zu erstellen.

### <a name="primary-and-secondary-actions"></a>Primäre und sekundäre Aktionen

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/adaptive-cards/actions-do.png" alt-text="Bewährte Methode: Eine adaptive Karte sollte nur eine kleine Gruppe von Aktionen enthalten." border="false":::

#### <a name="do-use-up-to-six-primary-actions"></a>Was Sie tun sollten: bis zu sechs primäre Aktionen verwenden

Adaptive Karten unterstützen zwar bis zu sechs primäre Aktionen, auf den meisten Karten werden diese jedoch nicht benötigt. Aktionen sollten klar, präzise und unkompliziert sein. Weniger ist mehr.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/adaptive-cards/actions-dont.png" alt-text="Bewährte Methode: Benutzer sollten nicht mit zu vielen Aktionen auf einer adaptiven Karte überfordert werden." border="false":::

#### <a name="dont-use-more-than-six-primary-actions"></a>Was Sie nicht tun sollten: mehr als sechs primäre Aktionen verwenden

Adaptive Karten sollten schnelle, handlungsrelevante Inhalte präsentieren. Zu viele Aktionen können einen Benutzer überfordern.

   :::column-end:::
:::row-end:::

### <a name="frequency"></a>Häufigkeit

:::image type="content" source="../../assets/images/adaptive-cards/frequency-do.png" alt-text="Bewährte Methode bezüglich der Häufigkeit adaptiver Karten." border="false":::

#### <a name="do-be-concise"></a>Was Sie tun sollten: Präzise sein

Es ist einfach, mehrere Karten in eine Unterhaltung zu senden, aber sobald Karten aus der Ansicht scrollen, werden sie weniger nützlich. Versuchen Sie, sich auf das Wesentliche zu beschränken. Dies gilt insbesondere in einem Kanal, in dem Benutzer weniger Toleranz für das haben, was sie als „Rauschen“ wahrnehmen.
