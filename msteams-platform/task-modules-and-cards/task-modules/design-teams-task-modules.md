---
title: Entwerfen von Aufgabenmodulen
author: heath-hamilton
description: Erfahren Sie, wie Sie Aufgabenmodule für Teams entwerfen und das Microsoft Teams UI Kit erhalten.
localization_priority: Normal
ms.author: lajanuar
ms.topic: reference
ms.openlocfilehash: 48e47a6c0bde0f0a3fefb8fcbfb362687ce58947
ms.sourcegitcommit: e1fe46c574cec378319814f8213209ad3063b2c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2021
ms.locfileid: "52629921"
---
# <a name="designing-task-modules-for-your-microsoft-teams-app"></a>Entwerfen von Aufgabenmodulen für Microsoft Teams App

Sie können modale Popuperfahrungen in Ihrer Teams mit Aufgabenmodulen erstellen. Verwenden Sie diese Funktion zum Anzeigen von Rich Media und Informationen oder zum Abschließen einer komplexen Aufgabe.

:::image type="content" source="../../assets/images/task-module/task-module-overview.png" alt-text="Beispiel zeigt ein Aufgabenmodul." border="false":::

## <a name="microsoft-teams-ui-kit"></a>Microsoft Teams-UI-Kit

Umfassendere Entwurfsrichtlinien für Aufgabenmodule, einschließlich Elemente, die Sie bei Bedarf packen und ändern können, finden Sie im Microsoft Teams UI Kit.

> [!div class="nextstepaction"]
> [Holen Sie sich das Microsoft Teams-UI-Kit (Figma)](https://www.figma.com/community/file/916836509871353159)

## <a name="open-a-task-module"></a>Öffnen eines Aufgabenmoduls

Aufgabenmodule können von fast überall in Ihrer App gestartet werden.

* **Registerkarte**: Ein Aufgabenmodul kann über einen beliebigen Link innerhalb einer Registerkarte gestartet werden. Wird in Szenarien verwendet, in denen der Benutzer sich auf eine Interaktion konzentrieren soll.
* **Bot**: Ein Aufgabenmodul kann über einen Link innerhalb einer Botnachricht gestartet werden.
* **Adaptive Karte:** Ein Aufgabenmodul kann von einer adaptiven Karte (gesendet mit einer Messagingerweiterung oder von einem Bot) gestartet werden, wenn ein Benutzer eine Schaltfläche auswählt.
* **Messagingerweiterung (Aktionsbefehle):** Mit Messagingerweiterungen können Sie eine bestimmte Aktion für Nachrichteninhalte ausführen. Wenn Sie eine Aktion auswählen, wird ein Aufgabenmodul geöffnet.
* **Messagingerweiterung (Kontext des Verfassenfelds):** Im Verfassenfeld können Sie eine Messagingerweiterung entwerfen, um ein Aufgabenmodul anstelle des typischen Flyouts zu öffnen. Reservieren Sie Aufgabenmodule für komplexe Interaktionen, z. B. das Ausfüllen eines Formulars.

## <a name="anatomy"></a>Anatomie

Aufgabenmodule bieten eine flexible Oberfläche für gehostete App-Oberflächen. Sie werden mit einem iframe (Desktop) oder webview (mobil) erstellt, sodass Sie Aufgabenmodule mit unseren Benutzeroberflächenvorlagen (empfohlen) oder von Grund auf neu entwerfen können.

Sie können auch mit dem [Adaptive Cards-Framework](../../task-modules-and-cards/cards/design-effective-cards.md) erstellt werden. Dies kann eine einfachere und schnellere Möglichkeit sein, gängige Szenarien (z. B. Formulare) zu erleichtern.

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/task-module/task-module-anatomy.png" alt-text="Abbildung der Ui-Anatomie eines Aufgabenmoduls." border="false":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|1|**App-Symbol**|
|2|**App-Name**: Vollständiger Name Ihrer App.|
|3|**Kopfzeile**: Kopfzeilen klar und prägnant machen. Beschreiben Sie die Aufgabe, die Benutzer abschließen möchten.
|4 |**Schaltfläche Schließen**: Schließt das Aufgabenmodul. Nicht gespeicherte Änderungen werden nicht in den App-Inhalten angewendet.|
|5 |**iframe**: Responsive space that hosts your app content.|
|6 |**Aktionen (optional):** Schaltflächen im Zusammenhang mit Ihrem App-Inhalt.|

# <a name="mobile"></a>[Mobil](#tab/mobile)

:::image type="content" source="../../assets/images/task-module/mobile-task-module-anatomy.png" alt-text="Abbildung der Benutzeroberflächenanatomie eines Aufgabenmoduls auf mobilen Geräten." border="false":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|1|**Kopfzeile**: Kopfzeilen klar und prägnant machen. Beschreiben Sie die Aufgabe, die Benutzer abschließen möchten.
|2|**App-Name**: Vollständiger Name Ihrer App.|
|3|**Schaltfläche Schließen**: Schließt das Aufgabenmodul. Nicht gespeicherte Änderungen werden nicht in den App-Inhalten angewendet.|
|4 |**webview**: Responsive space that hosts your app content.|
|5 |**Aktionen (optional):** Schaltflächen im Zusammenhang mit Ihrem App-Inhalt.|

---

## <a name="designing-with-ui-templates"></a>Entwerfen mit Benutzeroberflächenvorlagen

Erwägen Sie die Verwendung von Vorlagen für allgemeine Layouts in Ihren Aufgabenmodulen. Jede besteht aus kleineren Komponenten, um ein elegantes, ansprechendes Design zu erstellen, das von vorn oder für Ihr Szenario oder Ihr Markendesign angepasst werden kann.

* [Liste](../../concepts/design/design-teams-app-ui-templates.md#list): Listen können verwandte Elemente in einem scannierbaren Format anzeigen und Benutzern das Ausführen von Aktionen für eine gesamte Liste oder einzelne Elemente ermöglichen.
* [Formular](../../concepts/design/design-teams-app-ui-templates.md#form): Formulare sind für die strukturierte Erfassung, Validierung und Übermittlung von Benutzereingaben.
* [Leerer](../../concepts/design/design-teams-app-ui-templates.md#empty-state)Zustand: Die Vorlage für den leeren Zustand kann für viele Szenarien verwendet werden, z. B. für die Anmeldung, die Erstlauferfahrung, Fehlermeldungen und vieles mehr.

## <a name="examples"></a>Beispiele

### <a name="list"></a>Liste

Listen funktionieren in einem Aufgabenmodul gut, da sie einfach zu scannen sind.

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/task-module/list.png" alt-text="Beispielliste in einem Aufgabenmodul." border="false":::

# <a name="mobile"></a>[Mobil](#tab/mobile)

:::image type="content" source="../../assets/images/task-module/mobile-list.png" alt-text="Beispielliste in einem Aufgabenmodul auf Mobilgeräten." border="false":::

---

### <a name="form"></a>Formular

Aufgabenmodule sind ein hervorragender Ort, um Formulare mit sequenziellen Benutzereingaben und Inlineüberprüfungen zu benutzeroberflächen. Sie können adaptive Karten als Möglichkeit zum Einbetten von Formularelementen verwenden.

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/task-module/form.png" alt-text="Beispielformular in einem Aufgabenmodul." border="false":::

# <a name="mobile"></a>[Mobil](#tab/mobile)

:::image type="content" source="../../assets/images/task-module/mobile-form.png" alt-text="Beispielformular in einem Aufgabenmodul auf mobilen Geräten." border="false":::

---

### <a name="sign-in"></a>Anmelden

Erstellen Sie einen fokussierten Anmelde- oder Anmeldefluss mit einer Reihe von Aufgabenmodulen, mit der benutzer sich problemlos durch sequenzielle Schritte bewegen können.

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/task-module/sign-in.png" alt-text="Beispiel für die Anmeldeerfahrung in einem Aufgabenmodul." border="false":::

# <a name="mobile"></a>[Mobil](#tab/mobile)

:::image type="content" source="../../assets/images/task-module/mobile-sign-in.png" alt-text="Beispiel für die Anmeldeerfahrung in einem Aufgabenmodul auf Mobilgeräten." border="false":::

---

### <a name="media"></a>Medien

Einbetten von Medieninhalten in ein Aufgabenmodul für eine fokussierte Anzeige.

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/task-module/media.png" alt-text="Beispiel für Medieninhalte in einem Aufgabenmodul." border="false":::

# <a name="mobile"></a>[Mobil](#tab/mobile)

:::image type="content" source="../../assets/images/task-module/mobile-media.png" alt-text="Beispiel für Medieninhalte in einem Aufgabenmodul auf Mobilgeräten." border="false":::

---

### <a name="empty-state"></a>Leerer Status

Wird für Willkommens-, Fehler- und Erfolgsmeldungen verwendet.

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/task-module/empty-state.png" alt-text="Beispiel leerer Zustand in einem Aufgabenmodul." border="false":::

# <a name="mobile"></a>[Mobil](#tab/mobile)

:::image type="content" source="../../assets/images/task-module/mobile-empty-state.png" alt-text="Beispiel leerer Zustand in einem Aufgabenmodul auf mobilen Geräten." border="false":::

---

### <a name="image-gallery"></a>Bildergalerie

Ein Katalog karussell in einen iframe (Desktop) oder webview (mobil) einbetten.

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/task-module/image-gallery.png" alt-text="Beispielbildkatalog in einem Aufgabenmodul." border="false":::

# <a name="mobile"></a>[Mobil](#tab/mobile)

:::image type="content" source="../../assets/images/task-module/mobile-image-gallery.png" alt-text="Beispielbildkatalog in einem Aufgabenmodul auf Mobilgeräten." border="false":::

---

### <a name="poll"></a>Umfrage

In diesem Beispiel werden Umfrageergebnisse gezeigt, die von einer adaptiven Karte gestartet wurden. Die Abfrage kann auch in einem Aufgabenmodul platziert werden.

# <a name="desktop"></a>[Desktop](#tab/desktop)

:::image type="content" source="../../assets/images/task-module/poll.png" alt-text="Beispielumfrage in einem Aufgabenmodul." border="false":::

# <a name="mobile"></a>[Mobil](#tab/mobile)

:::image type="content" source="../../assets/images/task-module/mobile-poll.png" alt-text="Beispielumfrage in einem Aufgabenmodul auf Mobilgeräten." border="false":::

---

## <a name="best-practices"></a>Bewährte Methoden

Verwenden Sie diese Empfehlungen, um eine hochwertige App-Erfahrung zu erstellen.

### <a name="usability"></a>Benutzerfreundlichkeit

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/usability-do.png" alt-text="Beispiel für eine bewährte Methode für ein Aufgabenmodul (ein Aufgabenmodul nach dem anderen)." border="false":::

#### <a name="do-use-one-task-module-at-a-time"></a>Do: Verwenden eines Aufgabenmoduls gleichzeitig

Ziel ist es, den Benutzer auf das Abschließen einer Aufgabe zu konzentrieren.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/usability-dont.png" alt-text="Beispiel für eine bewährte Methode für ein Aufgabenmodul (Öffnen eines Dialogfelds über einem Aufgabenmodul)." border="false":::

#### <a name="dont-pop-a-dialog-on-top-of-a-task-module"></a>Don't: Pop a dialog on top of a task module

Dies führt zu einer unkonzentrierten, verwirrenden Benutzeroberfläche.

   :::column-end:::
:::row-end:::

### <a name="responsive"></a>Reaktionsfähig

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/responsive-do.png" alt-text="Beispiel für eine bewährte Methode für ein Aufgabenmodul (Stellen Sie sicher, dass der Inhalt reaktionsfähig ist)." border="false":::

#### <a name="do-make-sure-the-content-is-responsive"></a>Do: Stellen Sie sicher, dass der Inhalt reaktionsfähig ist

Während adaptive Karten, die in einem Aufgabenmodul gehostet werden, auf mobilen Geräten gut gerendert werden, stellen Sie sicher, dass die Benutzeroberfläche reaktionsfähig ist und geräteübergreifend gut funktioniert, wenn Sie einen iframe zum Hosten von App-Inhalten verwenden möchten.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/responsive-dont.png" alt-text="Beispiel für eine bewährte Methode für ein Aufgabenmodul (verwenden Sie keine horizontalen Bildlaufleisten)." border="false":::

#### <a name="dont-use-horizontal-scroll-bars"></a>Don't: Verwenden horizontaler Bildlaufleisten

Es ist eine bewährte Methode, inhalte fokussiert und nicht zu langwierig zu halten. Wenn ein Bildlauf erforderlich ist, scrollen Sie vertikal und nicht horizontal.

   :::column-end:::
:::row-end:::

### <a name="simplicity"></a>Einfachheit

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/simplicity-do.png" alt-text="Beispiel für eine bewährte Methode für ein Aufgabenmodul (kurz)." border="false":::

#### <a name="do-keep-it-short"></a>Do: Keep it short

Sie können ganz einfach einen mehrstufigen Assistenten erstellen, aber das bedeutet nicht unbedingt, dass Sie es sollten! Ein Aufgabenmodul mit mehreren Bildschirmen kann problematisch sein, da eingehende Nachrichten abgelenkt werden und Benutzer zum Beenden verleiten. Wenn Ihre Aufgabe wirklich beteiligt ist, wird anstelle eines Aufgabenmoduls eine vollständige Webseite angezeigt.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/simplicity-dont.png" alt-text="Beispiel für bewährte Vorgehensweise für ein Aufgabenmodul (keine langen Interaktionen)." border="false":::

#### <a name="dont-have-long-interactions"></a>Don't: Have long interactions

Versuchen Sie, Ihre Interaktionen kurz und auf den Punkt zu halten.

   :::column-end:::
:::row-end:::

### <a name="error-messages"></a>Fehlermeldungen

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/error-messages-do.png" alt-text="Beispiel für eine bewährte Methode für ein Aufgabenmodul (Verwenden von Inlinefehlermeldungen)." border="false":::

#### <a name="do-use-inline-error-messages"></a>Do: Verwenden von Inlinefehlermeldungen

Richtlinien zur Inlinefehlerbehandlung finden Sie in der Formularbenutzeroberflächenvorlage.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/error-messages-dont.png" alt-text="Beispiel für eine bewährte Methode für ein Aufgabenmodul (Setzen Sie Fehlermeldungen in Dialogfelder ein)." border="false":::

#### <a name="dont-put-error-messages-in-dialogs"></a>Don't: Setzen von Fehlermeldungen in Dialogfelder

Geben Sie in einem Dialogfeld über einem Aufgabenmodul keine Fehlermeldung ein. Dadurch wird eine verwirrende Benutzeroberfläche erstellt.

   :::column-end:::
:::row-end:::
