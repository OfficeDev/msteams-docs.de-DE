---
title: Entwerfen von Aufgabenmodulen
author: heath-hamilton
description: Erfahren Sie, wie Sie Aufgabenmodule für Teams Apps entwerfen und das Microsoft Teams UI Kit erhalten.
localization_priority: Normal
ms.author: lajanuar
ms.topic: reference
ms.openlocfilehash: 9248fba30726511d025e71957c0d9f2bac4c9866
ms.sourcegitcommit: 306b6e8cb3aac8bfda10ef3999467a797d64539d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/20/2021
ms.locfileid: "58408615"
---
# <a name="designing-task-modules-for-your-microsoft-teams-app"></a>Entwerfen von Aufgabenmodulen für Ihre Microsoft Teams-App

Sie können modale Popupfunktionen in Ihrer Teams-App mit Aufgabenmodulen erstellen. Verwenden Sie diese Funktion, um umfangreiche Medien und Informationen anzuzeigen oder eine komplexe Aufgabe auszuführen.

:::image type="content" source="../../assets/images/task-module/task-module-overview.png" alt-text="Beispiel zeigt ein Aufgabenmodul." border="false":::

## <a name="microsoft-teams-ui-kit"></a>Microsoft Teams-UI-Kit

Umfassendere Entwurfsrichtlinien für Aufgabenmodule, einschließlich Elementen, die Sie nach Bedarf abrufen und ändern können, finden Sie im Microsoft Teams UI Kit.

> [!div class="nextstepaction"]
> [Holen Sie sich das Microsoft Teams-UI-Kit (Figma)](https://www.figma.com/community/file/916836509871353159)

## <a name="open-a-task-module"></a>Öffnen eines Aufgabenmoduls

Aufgabenmodule können von fast überall in Ihrer App gestartet werden.

* **Registerkarte:** Ein Aufgabenmodul kann über einen beliebigen Link innerhalb einer Registerkarte gestartet werden. Wird in Szenarien verwendet, in denen der Benutzer sich auf eine Interaktion konzentrieren soll.
* **Bot:** Ein Aufgabenmodul kann über einen Link innerhalb einer Bot-Nachricht gestartet werden.
* **Adaptive Karte:** Ein Aufgabenmodul kann von einer adaptiven Karte (gesendet mit einer Messaging-Erweiterung oder von einem Bot) gestartet werden, wenn ein Benutzer eine Schaltfläche auswählt.
* **Messaging-Erweiterung (Aktionsbefehle):** Messaging-Erweiterungen ermöglichen Es Ihnen, eine bestimmte Aktion für Nachrichteninhalte auszuführen. Wenn Sie eine Aktion auswählen, wird ein Aufgabenmodul geöffnet.
* **Messaging-Erweiterung (Verfassenfeldkontext):** Im Feld "Verfassen" können Sie eine Messaging-Erweiterung so entwerfen, dass anstelle des typischen Flyouts ein Aufgabenmodul geöffnet wird. Reservieren Sie Aufgabenmodule für komplexe Interaktionen, z. B. das Ausfüllen eines Formulars.

## <a name="anatomy"></a>Anatomie

Aufgabenmodule bieten eine flexible Oberfläche für gehostete App-Umgebungen. Sie werden mit einem iframe (Desktop) oder einer Webansicht (mobil) erstellt, sodass Sie Aufgabenmodule mit unseren Benutzeroberflächenvorlagen (empfohlen) oder von Grund auf neu entwerfen können.

Sie können auch mit dem Framework für [adaptive Karten](../../task-modules-and-cards/cards/design-effective-cards.md) erstellt werden, was eine einfachere und schnellere Möglichkeit sein kann, allgemeine Szenarien (z. B. Formulare) zu vereinfachen.

### <a name="mobile"></a>Mobilgeräte

:::image type="content" source="../../assets/images/task-module/mobile-task-module-anatomy.png" alt-text="Abbildung der UI-Anatomie eines Aufgabenmoduls auf mobilgeräten." border="false":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|1|**Kopfzeile:** Kopfzeilen klar und prägnant gestalten. Beschreiben Sie die Aufgabe, die Benutzer ausführen sollen.
|2|**App-Name**: Vollständiger Name Ihrer App.|
|3|**Schaltfläche "Schließen":** Schließt das Aufgabenmodul. Es werden keine nicht gespeicherten Änderungen im App-Inhalt angewendet.|
|4 |**Webview:** Reaktionsfähiger Speicherplatz, in dem Ihre App-Inhalte gehostet werden.|
|5 |**Aktionen (optional):** Schaltflächen im Zusammenhang mit Ihrem App-Inhalt.|

### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/task-module/task-module-anatomy.png" alt-text="Abbildung der Ui-Anatomie eines Aufgabenmoduls." border="false":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|1|**App-Symbol**|
|2|**App-Name**: Vollständiger Name Ihrer App.|
|3|**Kopfzeile:** Kopfzeilen klar und prägnant gestalten. Beschreiben Sie die Aufgabe, die Benutzer ausführen sollen.
|4 |**Schaltfläche "Schließen":** Schließt das Aufgabenmodul. Es werden keine nicht gespeicherten Änderungen im App-Inhalt angewendet.|
|5 |**iframe:** Dynamischer Speicherplatz, in dem Ihre App-Inhalte gehostet werden.|
|6 |**Aktionen (optional):** Schaltflächen im Zusammenhang mit Ihrem App-Inhalt.|

## <a name="designing-with-ui-templates"></a>Entwerfen mit UI-Vorlagen

Erwägen Sie die Verwendung von Vorlagen für allgemeine Layouts in Ihren Aufgabenmodulen. Jede besteht aus kleineren Komponenten, um ein ansprechendes, reaktionsfähiges Design zu erstellen, das sofort verwendet oder für Ihr Szenario oder ihr Markenerscheinungsbild angepasst werden kann.

* [Liste:](../../concepts/design/design-teams-app-ui-templates.md#list)Listen können verwandte Elemente in einem scannbaren Format anzeigen und Benutzern ermöglichen, Aktionen für eine gesamte Liste oder einzelne Elemente auszuführen.
* [Formular:](../../concepts/design/design-teams-app-ui-templates.md#form)Formulare dienen zum strukturierten Sammeln, Überprüfen und Übermitteln von Benutzereingaben.
* [Leerer Zustand:](../../concepts/design/design-teams-app-ui-templates.md#empty-state)Die leere Statusvorlage kann für viele Szenarien verwendet werden, einschließlich Anmeldung, Erste Ausführung, Fehlermeldungen und vieles mehr.

## <a name="examples"></a>Beispiele

### <a name="list"></a>Liste

Listen funktionieren gut in einem Aufgabenmodul, da sie einfach zu scannen sind.

#### <a name="mobile"></a>Mobilgeräte

:::image type="content" source="../../assets/images/task-module/mobile-list.png" alt-text="Beispielliste in einem Aufgabenmodul auf mobilen Geräten." border="false":::

#### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/task-module/list.png" alt-text="Beispielliste in einem Aufgabenmodul." border="false":::

### <a name="form"></a>Formular

Aufgabenmodule eignen sich hervorragend zum Anzeigen von Formularen mit sequenziellen Benutzereingaben und Inlineüberprüfungen. Sie können adaptive Karten zum Einbetten von Formularelementen verwenden.

#### <a name="mobile"></a>Mobilgeräte

:::image type="content" source="../../assets/images/task-module/mobile-form.png" alt-text="Beispielformular in einem Aufgabenmodul auf mobilen Geräten." border="false":::

#### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/task-module/form.png" alt-text="Beispielformular in einem Aufgabenmodul." border="false":::

### <a name="sign-in"></a>Anmelden

Erstellen Sie einen fokussierten Anmelde- oder Registrierungsfluss mit einer Reihe von Aufgabenmodulen, sodass Benutzer problemlos sequenzielle Schritte durchlaufen können.

#### <a name="mobile"></a>Mobilgeräte

:::image type="content" source="../../assets/images/task-module/mobile-sign-in.png" alt-text="Beispiel für die Anmeldung in einem Aufgabenmodul auf mobilen Geräten." border="false":::

#### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/task-module/sign-in.png" alt-text="Beispiel für die Anmeldung in einem Aufgabenmodul." border="false":::

### <a name="media"></a>Medien

Einbetten von Medieninhalten in ein Aufgabenmodul für eine fokussierte Anzeige.

#### <a name="mobile"></a>Mobilgeräte

:::image type="content" source="../../assets/images/task-module/mobile-media.png" alt-text="Beispiel für Medieninhalte in einem Aufgabenmodul auf mobilen Geräten." border="false":::

#### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/task-module/media.png" alt-text="Beispiel für Medieninhalte in einem Aufgabenmodul." border="false":::

### <a name="empty-state"></a>Leerer Zustand

Wird für Begrüßungs-, Fehler- und Erfolgsmeldungen verwendet.

#### <a name="mobile"></a>Mobilgeräte

:::image type="content" source="../../assets/images/task-module/mobile-empty-state.png" alt-text="Beispiel für einen leeren Zustand in einem Aufgabenmodul auf mobilen Geräten." border="false":::

#### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/task-module/empty-state.png" alt-text="Beispiel für einen leeren Zustand in einem Aufgabenmodul." border="false":::

### <a name="image-gallery"></a>Bildergalerie

Einbetten eines Katalog-Karussells in einen iframe (Desktop) oder eine Webansicht (mobil).

##### <a name="mobile"></a>Mobilgeräte

:::image type="content" source="../../assets/images/task-module/mobile-image-gallery.png" alt-text="Beispielbildgalerie in einem Aufgabenmodul auf mobilen Geräten." border="false":::

##### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/task-module/image-gallery.png" alt-text="Beispielbildgalerie in einem Aufgabenmodul." border="false":::

### <a name="poll"></a>Umfrage

In diesem Beispiel werden die Von einer adaptiven Karte gestarteten Umfrageergebnisse gezeigt. Die Abfrage kann auch in einem Aufgabenmodul platziert werden.

#### <a name="mobile"></a>Mobilgeräte

:::image type="content" source="../../assets/images/task-module/mobile-poll.png" alt-text="Beispielumfrage in einem Aufgabenmodul auf mobilen Geräten." border="false":::

#### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/task-module/poll.png" alt-text="Beispielumfrage in einem Aufgabenmodul." border="false":::

## <a name="best-practices"></a>Bewährte Methoden

Verwenden Sie diese Empfehlungen, um eine hochwertige App-Erfahrung zu erstellen.

### <a name="usability"></a>Usability

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/usability-do.png" alt-text="Beispiel für eine bewährte Methode für ein Aufgabenmodul (jeweils ein Aufgabenmodul)." border="false":::

#### <a name="do-use-one-task-module-at-a-time"></a>Do: Jeweils ein Aufgabenmodul verwenden

Das Ziel besteht darin, den Benutzer auf die Erledigung einer Aufgabe zu konzentrieren.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/usability-dont.png" alt-text="Beispiel für eine bewährte Methode für ein Aufgabenmodul (Popup eines Dialogfelds über einem Aufgabenmodul)." border="false":::

#### <a name="dont-pop-a-dialog-on-top-of-a-task-module"></a>Don't: Popup eines Dialogfelds über einem Aufgabenmodul

Dadurch entsteht eine unfokussierte, verwirrende Benutzererfahrung.

   :::column-end:::
:::row-end:::

### <a name="responsive"></a>Reaktionsfähig

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/responsive-do.png" alt-text="Beispiel für eine bewährte Methode für ein Aufgabenmodul (sicherstellen, dass der Inhalt reaktionsfähig ist)." border="false":::

#### <a name="do-make-sure-the-content-is-responsive"></a>Do: Stellen Sie sicher, dass der Inhalt reaktionsfähig ist

Während adaptive Karten, die in einem Aufgabenmodul gehostet werden, gut auf mobilen Geräten gerendert werden, stellen Sie sicher, dass die Benutzeroberfläche reaktionsfähig und geräteübergreifend gut funktioniert, wenn Sie einen iFrame zum Hosten von App-Inhalten verwenden.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/responsive-dont.png" alt-text="Beispiel für eine bewährte Methode für ein Aufgabenmodul (verwenden Sie keine horizontalen Bildlaufleisten)." border="false":::

#### <a name="dont-use-horizontal-scroll-bars"></a>Nicht empfohlen: Verwenden horizontaler Bildlaufleisten

Es ist eine bewährte Methode, Inhalte konzentriert und nicht zu lang zu halten. Wenn ein Bildlauf erforderlich ist, scrollen Sie vertikal und nicht horizontal.

   :::column-end:::
:::row-end:::

### <a name="simplicity"></a>Einfachheit

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/simplicity-do.png" alt-text="Beispiel für eine bewährte Methode für ein Aufgabenmodul (kurz halten)." border="false":::

#### <a name="do-keep-it-short"></a>Do: Keep it short

Sie können ganz einfach einen Assistenten mit mehreren Schritten erstellen, aber das bedeutet nicht unbedingt, dass Sie dies tun sollten. Ein Aufgabenmodul mit mehreren Bildschirmen kann problematisch sein, da eingehende Nachrichten ablenken und Benutzer zum Beenden verlocken. Wenn Ihre Aufgabe wirklich beteiligt ist, öffnen Sie eine vollständige Webseite anstelle eines Aufgabenmoduls.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/simplicity-dont.png" alt-text="Beispiel für eine bewährte Methode für ein Aufgabenmodul (keine langen Interaktionen)." border="false":::

#### <a name="dont-have-long-interactions"></a>Don't: Have long interactions

Versuchen Sie, Ihre Interaktionen kurz und auf den Punkt zu halten.

   :::column-end:::
:::row-end:::

### <a name="error-messages"></a>Fehlermeldungen

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/error-messages-do.png" alt-text="Beispiel für eine bewährte Methode für ein Aufgabenmodul (Verwenden von Inline-Fehlermeldungen)." border="false":::

#### <a name="do-use-inline-error-messages"></a>Do: Verwenden von Inlinefehlermeldungen

Richtlinien zur Inlinefehlerbehandlung finden Sie in der Formular-UI-Vorlage.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/error-messages-dont.png" alt-text="Beispiel für eine bewährte Methode für ein Aufgabenmodul (Fehlermeldungen in Dialogfeldern platzieren)." border="false":::

#### <a name="dont-put-error-messages-in-dialogs"></a>Don't: Platzieren von Fehlermeldungen in Dialogfeldern

Zeigen Sie keine Fehlermeldung in einem Dialogfeld auf einem Aufgabenmodul an. Dies führt zu einer verwirrenden Benutzererfahrung.

   :::column-end:::
:::row-end:::
