---
title: Entwerfen von Aufgaben Modulen
author: heath-hamilton
description: Hier erfahren Sie, wie Sie Aufgaben Module für Teams-apps entwerfen und das Microsoft Teams UI Kit abrufen.
ms.author: lajanuar
ms.topic: reference
ms.openlocfilehash: 41584ecf58ca7718290e58e5845549e4579dac64
ms.sourcegitcommit: c102da958759c13aa9e0f81bde1cffb34a8bef34
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/09/2020
ms.locfileid: "49606199"
---
# <a name="designing-task-modules-for-your-microsoft-teams-app"></a>Entwerfen von Aufgaben Modulen für Ihre Microsoft Teams-App

Sie können modale Popup-Erlebnisse in Ihrer Teams-App mit Aufgaben Modulen erstellen. Verwenden Sie diese Funktion, um Rich-Medien und-Informationen anzuzeigen oder eine komplexe Aufgabe abzuschließen.

:::image type="content" source="../../assets/images/task-module/task-module-overview.png" alt-text="Beispiel zeigt ein Aufgabenmodul." border="false":::

## <a name="microsoft-teams-ui-kit"></a>Microsoft Teams-UI-Kit

Ausführlichere Entwurfsrichtlinien für Aufgaben Module, einschließlich der Elemente, die Sie nach Bedarf erfassen und ändern können, finden Sie im Microsoft Teams UI Kit.

> [!div class="nextstepaction"]
> [Abrufen des Microsoft Teams UI Kit (Figma)](https://www.figma.com/community/file/916836509871353159)

## <a name="open-a-task-module"></a>Öffnen eines Aufgabenmoduls

Aufgaben Module können von fast überall in Ihrer APP gestartet werden.

* **Tab**: ein Aufgabenmodul kann von einem beliebigen Link innerhalb einer Registerkarte oder eines IFRAME gestartet werden. Verwenden Sie in Szenarien, in denen der Benutzer sich auf eine Interaktion konzentrieren soll.
* **Bot**: ein Aufgabenmodul kann über einen Link in einer bot-Nachricht gestartet werden.
* **Adaptive Karte**: ein Aufgabenmodul kann von einer adaptiven Karte gestartet werden (mit einer Messaging Erweiterung oder einem bot gesendet), wenn ein Benutzer eine Schaltfläche auswählt.
* **Messaging-Erweiterung (Aktionsbefehle)**: mit Messaging Erweiterungen können Sie eine bestimmte Aktion für Nachrichteninhalte durchführen. Durch Auswählen einer Aktion wird ein Aufgabenmodul geöffnet.
* **Messaging Erweiterung (Kontext des verfassen-Felds)**: im Feld Verfassen können Sie eine Messaging Erweiterung entwerfen, um anstelle des typischen Flyouts ein Aufgabenmodul zu öffnen. Reservieren Sie Aufgaben Module für komplexe Interaktionen, beispielsweise das Ausfüllen eines Formulars.

## <a name="anatomy"></a>Anatomie

:::image type="content" source="../../assets/images/task-module/task-module-anatomy.png" alt-text="Illustration, die die Benutzeroberflächen Anatomie eines Aufgabenmoduls veranschaulicht." border="false":::

Aufgaben Module sind sehr flexible Oberflächen. Sie können mit iframes erstellt werden, indem Sie andere Benutzeroberflächenvorlagen einziehen, um von Partnern erstellte Erfahrungen zu hosten. Dies wird für die meiste polierte Erfahrung bevorzugt.

Sie können auch mit dem [Adaptive Card](../../task-modules-and-cards/cards/design-effective-cards.md) -Framework erstellt werden, was eine einfachere und schnellere Möglichkeit zur Ausführung häufig auftretender Szenarien (beispielsweise Formulare) darstellen kann.

|Leistungsindikator|Beschreibung|
|----------|-----------|
|1|**App-Symbol**|
|2 |**App-Name**: vollständiger Name Ihrer APP.|
|3 |**Kopfzeile**: machen Sie Kopfzeilen klar und prägnant. Beschreiben Sie die Aufgabe, die die Benutzer ausführen sollen.
|4 |**Schaltfläche Schließen**: ermöglicht Benutzern das Auffinden von App-Inhalten, die Sie einfügen möchten.|
|5 |**iframe**: reaktionsfähiger Speicherplatz, der Ihre APP-Inhalte hostet.|
|6 |**Aktionen (optional)**: Schaltflächen im Zusammenhang mit Ihrem App-Inhalt.|

## <a name="designing-with-ui-templates"></a>Entwerfen mit Benutzeroberflächenvorlagen

Sie sollten Vorlagen für allgemeine Layouts in ihren Aufgaben Modulen verwenden. Jeder besteht aus kleineren Komponenten, um ein elegantes, reaktionsfähiges Design zu erstellen, das aus dem Karton oder für Ihr Szenario oder ihr Marken-Erscheinungsbild verwendet werden kann.

* [List](../../concepts/design/design-teams-app-ui-templates.md#list): Listen können verwandte Elemente in einem scannable-Format anzeigen und Benutzern das Ausführen von Aktionen für eine gesamte Liste oder einzelne Elemente gestatten.
* [Formular](../../concepts/design/design-teams-app-ui-templates.md#form): Formulare dienen zum Sammeln, validieren und Übermitteln von Benutzereingaben in strukturierter Form.
* [Leer State](../../concepts/design/design-teams-app-ui-templates.md#empty-state): die leere Statusvorlage kann für viele Szenarien verwendet werden, einschließlich Anmeldung, Erstausführung, Fehlermeldungen und mehr.

## <a name="examples"></a>Beispiele

### <a name="list"></a>List

Listen funktionieren in einem Aufgabenmodul gut, da Sie einfach zu überprüfen sind.

:::image type="content" source="../../assets/images/task-module/list.png" alt-text="Beispielliste in einem Aufgabenmodul." border="false":::

### <a name="form"></a>Formular

Aufgaben Module eignen sich hervorragend zum Aufstellen von Formularen mit sequenziellen Benutzereingaben und Inline Überprüfung. Sie können Adaptive Karten als Möglichkeit zum Einbetten von Formularelementen nutzen.

:::image type="content" source="../../assets/images/task-module/form.png" alt-text="Beispielformular in einem Aufgabenmodul." border="false":::

### <a name="sign-in"></a>Anmelden

Erstellen Sie einen fokussierten Anmelde-oder Registrierungs Fluss mit einer Reihe von Aufgaben Modulen, sodass Benutzer problemlos durch sequenzielle Schritte navigieren können.

:::image type="content" source="../../assets/images/task-module/sign-in.png" alt-text="Beispiel für ein anmeldeerlebnis in einem Aufgabenmodul." border="false":::

### <a name="media"></a>Medien

Einbetten von Medieninhalten in einen Aufgabenmodul für eine fokussierte Anzeigeoberfläche.

:::image type="content" source="../../assets/images/task-module/media.png" alt-text="Beispiel Medieninhalte in einem Aufgabenmodul." border="false":::

### <a name="empty-state"></a>Leerer Zustand

Verwenden Sie für Willkommens-, Fehler-und Erfolgsmeldungen.

:::image type="content" source="../../assets/images/task-module/empty-state.png" alt-text="Beispiel für einen leeren Zustand in einem Aufgabenmodul." border="false":::

### <a name="image-gallery"></a>Bildergalerie

Einbetten eines Galerie Karussells in einen iframe.

:::image type="content" source="../../assets/images/task-module/image-gallery.png" alt-text="Beispielbild Galerie in einem Aufgabenmodul." border="false":::

### <a name="poll"></a>Umfrage

In diesem Beispiel werden Umfrageergebnisse angezeigt, die von einer adaptiven Karte gestartet wurden.

:::image type="content" source="../../assets/images/task-module/poll.png" alt-text="Beispielabfrage in einem Aufgabenmodul." border="false":::

## <a name="best-practices"></a>Bewährte Methoden

### <a name="usability"></a>Benutzerfreundlichkeit

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/usability-do.png" alt-text="Beispiel mit einem Aufgabenmodul bewährte Methode." border="false":::

#### <a name="do-use-one-task-module-at-a-time"></a>Do: Gleichzeitiges verwenden eines Aufgabenmoduls

Das Ziel besteht darin, den Benutzer darauf zu konzentrieren, eine Aufgabe abzuschließen.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/usability-dont.png" alt-text="Beispiel mit einem Aufgabenmodul bewährte Methode." border="false":::

#### <a name="dont-pop-a-dialog-on-top-of-a-task-module"></a>Nicht: Pop ein Dialogfeld oberhalb eines Aufgabenmoduls

Dadurch entsteht eine unfokussierte, verwirrende Benutzeroberfläche.

   :::column-end:::
:::row-end:::

### <a name="responsive"></a>Reaktionsfähig

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/responsive-do.png" alt-text="Beispiel mit einem Aufgabenmodul bewährte Methode." border="false":::

#### <a name="do-make-sure-the-content-is-responsive"></a>Do: sicherstellen, dass der Inhalt reagiert

Während Adaptive Karten, die in einem Aufgabenmodul gehostet werden, auf mobilen Geräten gut gerendert werden, sollten Sie, wenn Sie einen IFRAME zum Hosten von App-Inhalten auswählen, sicherstellen, dass die Benutzeroberfläche reagiert und auf allen Geräten gut funktioniert.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/responsive-dont.png" alt-text="Beispiel mit einem Aufgabenmodul bewährte Methode." border="false":::

#### <a name="dont-use-horizontal-scrollbars"></a>Nicht: horizontale Bildlaufleisten verwenden

Es ist eine bewährte Methode, Inhalte konzentriert und nicht zu lang zu halten. Wenn ein Bildlauf erforderlich ist, Scrollen Sie vertikal und nicht horizontal.

   :::column-end:::
:::row-end:::

### <a name="simplicity"></a>Einfachheit

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/simplicity-do.png" alt-text="Beispiel mit einem Aufgabenmodul bewährte Methode." border="false":::

#### <a name="do-keep-it-short"></a>Do: kurz halten

Sie können ganz einfach einen mehrstufigen Assistenten erstellen, aber das bedeutet nicht unbedingt, dass Sie dies sollten! Ein Aufgabenmodul mit mehreren Bildschirmen kann problematisch sein, da eingehende Nachrichten ablenken und Benutzer zum Beenden verleiten. Wenn Ihre Aufgabe wirklich involviert ist, gehen Sie zu einer vollständigen Webseite anstelle eines Aufgabenmoduls.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/simplicity-dont.png" alt-text="Beispiel mit einem Aufgabenmodul bewährte Methode." border="false":::

#### <a name="dont-do-long-interactions"></a>Nicht: lange Interaktionen ausführen

Versuchen Sie, ihre Interaktionen kurz und auf den neuesten Stand zu bringen.

   :::column-end:::
:::row-end:::

### <a name="error-messages"></a>Fehlermeldungen

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/error-messages-do.png" alt-text="Beispiel mit einem Aufgabenmodul bewährte Methode." border="false":::

#### <a name="do-use-inline-error-messages"></a>Do: Verwenden von Inline Fehlermeldungen

Anleitungen zur Inline Fehlerbehandlung finden Sie in der Forms-Benutzeroberflächen Vorlage.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/error-messages-dont.png" alt-text="Beispiel mit einem Aufgabenmodul bewährte Methode." border="false":::

#### <a name="dont-put-error-messages-in-dialogs"></a>Nicht: Put-Fehlermeldungen in Dialogfeldern

Keine Fehlermeldung in einem Dialogfeld oberhalb eines Aufgabenmoduls Pop. Dadurch wird eine verwirrende Benutzeroberfläche erstellt.

   :::column-end:::
:::row-end:::
