---
title: Entwerfen von Aufgabenmodulen
author: heath-hamilton
description: Erfahren Sie, wie Sie Aufgabenmodule für Teams-Apps entwerfen und den Microsoft Teams-Benutzeroberflächenbausatz abrufen.
ms.localizationpriority: high
ms.author: lajanuar
ms.topic: reference
ms.openlocfilehash: 1cf22c8ff94e5d1a6132bd382395067d3623b4bf
ms.sourcegitcommit: 8feddafb51b2a1a85d04e37568b2861287f982d3
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/22/2021
ms.locfileid: "59475636"
---
# <a name="designing-task-modules-for-your-microsoft-teams-app"></a>Entwerfen von Aufgabenmodulen für Ihre Microsoft Teams-App

Sie können modale Popup-Erfahrungen in Ihrer Teams-App mit Aufgabenmodulen erstellen. Verwenden Sie diese Funktion, um Rich-Media und Informationen anzuzeigen, oder eine komplexe Aufgabe abzuschließen.

:::image type="content" source="../../assets/images/task-module/task-module-overview.png" alt-text="Beispiel zeigt ein Aufgabenmodul an." border="false":::

## <a name="microsoft-teams-ui-kit"></a>Microsoft Teams-Benutzeroberflächenbausatz

Umfassendere Anleitungen für das Aufgabenmoduldesign, einschließlich Elemente, die Sie nach Bedarf abrufen und ändern können, finden Sie im Microsoft Teams-Benutzeroberflächenbausatz.

> [!div class="nextstepaction"]
> [Holen Sie sich den Microsoft Teams-Benutzeroberflächenbausatz (Figma)](https://www.figma.com/community/file/916836509871353159)

## <a name="open-a-task-module"></a>Öffnen eines Aufgabenmoduls

Aufgabenmodule können von fast überall in Ihrer App gestartet werden.

* **Registerkarte**: Ein Aufgabenmodul kann über einen beliebigen Link innerhalb einer Registerkarte gestartet werden. Verwenden Sie dies in Szenarien, in denen sich der Benutzer auf eine Interaktion konzentrieren soll.
* **Bot**: Ein Aufgabenmodul kann über einen Link innerhalb einer Botnachricht gestartet werden.
* **Adaptive Karte**: Ein Aufgabenmodul kann über eine adaptive Karte gestartet werden (gesendet mit einer Messaging-Erweiterung oder von einem Bot), wenn ein Benutzer eine Schaltfläche auswählt.
* **Messaging-Erweiterung (Aktionsbefehle)**: Messaging-Erweiterungen ermöglichen es Ihnen, eine bestimmte Aktion für Nachrichteninhalte auszuführen. Wenn Sie eine Aktion auswählen, wird ein Aufgabenmodul geöffnet.
* **Messaging-Erweiterung (Feldkontext verfassen)**: Im Feld „verfassen“ können Sie eine Messaging-Erweiterung entwerfen, um ein Aufgabenmodul zu öffnen anstelle des typischen Flyout. Reservieren Sie Aufgabenmodule für komplexe Interaktionen, z. B. das Ausfüllen eines Formulars.

## <a name="anatomy"></a>Anatomie

Aufgabenmodule bieten eine flexible Oberfläche für gehostete App-Erfahrungen. Sie werden mithilfe eines iFrame (Desktop) oder einer WebView (Mobilgerät) erstellt, sodass Sie Aufgabenmodule mit unseren Benutzeroberflächenvorlagen (empfohlen) oder von Grund auf neu entwerfen können.

Sie können auch mit dem Framework für [Adaptive Karten](../../task-modules-and-cards/cards/design-effective-cards.md) erstellt werden. Dies kann eine einfachere und schnellere Möglichkeit sein, häufige Szenarien (z. B. Formulare) zu vereinfachen.

### <a name="mobile"></a>Mobilgeräte

:::image type="content" source="../../assets/images/task-module/mobile-task-module-anatomy.png" alt-text="Abbildung zeigt die Benutzeroberflächenanatomie eines Aufgabenmoduls auf Mobilgeräten." border="false":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|1|**Kopfzeile**: Erstellen Sie Ihre Kopfzeilen klar und präzise. Beschreiben Sie die Aufgabe, die Benutzer ausführen sollen.
|2|**App-Name**: Vollständiger Name Ihrer App.|
|3|**Schaltfläche „Schließen“**: Schließt das Aufgabenmodul. Wendet keine ungespeicherten Änderungen in App-Inhalten an.|
|4|**WebView**: Reaktionsfähiger Bereich, der Ihre App-Inhalte hostet.|
|5|**Aktionen (optional)**: Schaltflächen im Zusammenhang mit Ihren App-Inhalten.|

### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/task-module/task-module-anatomy.png" alt-text="Abbildung zeigt die Benutzeroberflächenanatomie eines Aufgabenmoduls." border="false":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|1|**App-Symbol**|
|2|**App-Name**: Vollständiger Name Ihrer App.|
|3|**Kopfzeile**: Erstellen Sie Ihre Kopfzeilen klar und präzise. Beschreiben Sie die Aufgabe, die Benutzer ausführen sollen.
|4|**Schaltfläche „Schließen“**: Schließt das Aufgabenmodul. Wendet keine ungespeicherten Änderungen in App-Inhalten an.|
|5|**iFrame**: Reaktionsfähiger Bereich, der Ihre App-Inhalte hostet.|
|6|**Aktionen (optional)**: Schaltflächen im Zusammenhang mit Ihren App-Inhalten.|

## <a name="designing-with-ui-templates"></a>Entwerfen mit Benutzeroberflächenvorlagen

Erwägen Sie die Verwendung von Vorlagen für allgemeine Layouts innerhalb Ihrer Aufgabenmodule. Jede besteht aus kleineren Komponenten, um ein elegantes, reaktionsfähiges Design zu erstellen, das sofort verwendet oder für Ihr Szenario oder das Look & Feel Ihrer Marke angepasst werden kann.

* [Liste](../../concepts/design/design-teams-app-ui-templates.md#list): Listen können verwandte Elemente in einem durchsuchbaren Format anzeigen und es Benutzern ermöglichen, Aktionen für eine ganze Liste oder einzelne Elemente auszuführen.
* [Formular](../../concepts/design/design-teams-app-ui-templates.md#form): Formulare dienen zum Sammeln, Überprüfen und Übermitteln von Benutzereingaben auf strukturierte Weise.
* [Leerer Status](../../concepts/design/design-teams-app-ui-templates.md#empty-state): Die Vorlage „leerer Status“ kann für viele Szenarien verwendet werden, z. B. für die Anmeldung, die Erfahrung beim ersten Ausführen, Fehlermeldungen und vieles mehr.

## <a name="examples"></a>Beispiele

### <a name="list"></a>Liste

Listen funktionieren gut in einem Aufgabenmodul, da sie einfach zu durchsuchen sind.

#### <a name="mobile"></a>Mobilgeräte

:::image type="content" source="../../assets/images/task-module/mobile-list.png" alt-text="Beispielliste in einem Aufgabenmodul auf einem Mobilgerät." border="false":::

#### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/task-module/list.png" alt-text="Beispielliste in einem Aufgabenmodul." border="false":::

### <a name="form"></a>Formular

Aufgabenmodule eignen sich hervorragend zum Anzeigen von Formularen mit sequenziellen Benutzereingaben und Inline-Validierung. Sie können adaptive Karten als Möglichkeit zum Einbetten von Formularelementen nutzen.

#### <a name="mobile"></a>Mobilgeräte

:::image type="content" source="../../assets/images/task-module/mobile-form.png" alt-text="Beispielformular in einem Aufgabenmodul auf Mobilgeräten." border="false":::

#### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/task-module/form.png" alt-text="Beispielformular in einem Aufgabenmodul." border="false":::

### <a name="sign-in"></a>Anmelden

Erstellen Sie einen fokussierten Anmelde- oder Registrierungsfluss mit einer Reihe von Aufgabenmodulen, sodass Benutzer problemlos sequenzielle Schritte durchlaufen können.

#### <a name="mobile"></a>Mobilgeräte

:::image type="content" source="../../assets/images/task-module/mobile-sign-in.png" alt-text="Beispiel für die Anmeldeerfahrung in einem Aufgabenmodul auf Mobilgeräten." border="false":::

#### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/task-module/sign-in.png" alt-text="Beispiel für die Anmeldeerfahrung in einem Aufgabenmodul." border="false":::

### <a name="media"></a>Medien

Einbetten von Medieninhalten in ein Aufgabenmodul für eine fokussierte Anzeigeerfahrung.

#### <a name="mobile"></a>Mobilgeräte

:::image type="content" source="../../assets/images/task-module/mobile-media.png" alt-text="Beispiel für Medieninhalte in einem Aufgabenmodul auf Mobilgeräten." border="false":::

#### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/task-module/media.png" alt-text="Beispiel für Medieninhalte in einem Aufgabenmodul." border="false":::

### <a name="empty-state"></a>Leerer Zustand

Wird für Begrüßungs-, Fehler- und Erfolgsmeldungen verwendet.

#### <a name="mobile"></a>Mobilgeräte

:::image type="content" source="../../assets/images/task-module/mobile-empty-state.png" alt-text="Beispiel für leeren Zustand in einem Aufgabenmodul auf Mobilgeräten." border="false":::

#### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/task-module/empty-state.png" alt-text="Beispiel für leeren Zustand in einem Aufgabenmodul." border="false":::

### <a name="image-gallery"></a>Bildergalerie

Einbetten eines Katalogkarussells in ein iFrame (Desktop) oder eine WebView (Mobilgerät).

##### <a name="mobile"></a>Mobilgeräte

:::image type="content" source="../../assets/images/task-module/mobile-image-gallery.png" alt-text="Beispiel eines Bildkatalogs in einem Aufgabenmodul auf Mobilgeräten." border="false":::

##### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/task-module/image-gallery.png" alt-text="Beispiel eines Bildkatalogs in einem Aufgabenmodul." border="false":::

### <a name="poll"></a>Umfrage

Dieses Beispiel zeigt Ergebnisse einer Umfrage, die von einer adaptiven Karte gestartet wurde. Die Umfrage kann auch in ein Aufgabenmodul platziert werden.

#### <a name="mobile"></a>Mobilgeräte

:::image type="content" source="../../assets/images/task-module/mobile-poll.png" alt-text="Beispielumfrage in einem Aufgabenmodul auf Mobilgeräten." border="false":::

#### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/task-module/poll.png" alt-text="Beispielumfrage in einem Aufgabenmodul." border="false":::

## <a name="best-practices"></a>Bewährte Methoden

Verwenden Sie diese Empfehlungen, um eine hochwertige App-Erfahrung zu erstellen.

### <a name="usability"></a>Benutzerfreundlichkeit

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/usability-do.png" alt-text="Beispiel zeigt eine bewährte Methode für ein Aufgabenmodul (ein Aufgabenmodul nach dem anderen)." border="false":::

#### <a name="do-use-one-task-module-at-a-time"></a>Tun: Verwenden Sie jeweils ein Aufgabenmodul nach dem anderen.

Das Ziel besteht darin, dass sich der Benutzer auf das Erledigen einer Aufgabe konzentriert.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/usability-dont.png" alt-text="Beispiel zeigt eine bewährte Methode für ein Aufgabenmodul (ein Dialogfeld über einem Aufgabenmodul einblenden)." border="false":::

#### <a name="dont-pop-a-dialog-on-top-of-a-task-module"></a>Nicht tun: Einblenden eines Dialogfelds über einem Aufgabenmodul

Dies führt zu einer unscharfen, verwirrenden Benutzererfahrung.

   :::column-end:::
:::row-end:::

### <a name="responsive"></a>Reaktionsfähig

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/responsive-do.png" alt-text="Beispiel zeigt eine bewährte Methode für ein Aufgabenmodul (sicherstellen, dass die Inhalte reaktionsfähig sind)." border="false":::

#### <a name="do-make-sure-the-content-is-responsive"></a>Tun: Sicherstellen, dass die Inhalte reaktionsfähig sind

Während adaptive Karten, die in einem Aufgabenmodul gehostet werden, gut auf mobilen Geräten gerendert werden, müssen Sie bei Verwendung eines iFrames zum Hosten von App-Inhalten sicherstellen, dass die Benutzeroberfläche reaktionsfähig ist und geräteübergreifend gut funktioniert.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/responsive-dont.png" alt-text="Beispiel zeigt eine bewährte Methode für ein Aufgabenmodul (verwenden Sie keine horizontalen Bildlaufleisten)." border="false":::

#### <a name="dont-use-horizontal-scroll-bars"></a>Nicht tun: Horizontale Bildlaufleisten verwenden

Es ist eine bewährte Methode, Inhalte fokussiert und nicht zu lang zu halten. Wenn ein Bildlauf erforderlich ist, scrollen Sie vertikal und nicht horizontal.

   :::column-end:::
:::row-end:::

### <a name="simplicity"></a>Einfachheit

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/simplicity-do.png" alt-text="Beispiel zeigt eine bewährte Methode für ein Aufgabenmodul (halten Sie es kurz)." border="false":::

#### <a name="do-keep-it-short"></a>Tun: Halten Sie Ihren Beitrag kurz.

Sie können ganz einfach einen Assistenten mit mehreren Schritten erstellen, aber das bedeutet nicht unbedingt, dass Sie es sollten! Ein Aufgabenmodul mit mehreren Bildschirmen kann problematisch sein, da eingehende Nachrichten ablenkend sind und Benutzer zum Beenden verleiten. Wenn Ihre Aufgabe sehr umfangreich ist, sollten Sie statt eines Aufgabenmoduls eine ganze Webseite öffnen.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/simplicity-dont.png" alt-text="Beispiel zeigt eine bewährte Methode für ein Aufgabenmodul (keine langen Interaktionen)." border="false":::

#### <a name="dont-have-long-interactions"></a>Nicht tun: Lange Interaktionen erstellen

Versuchen Sie, Ihre Interaktionen kurz zu halten und auf den Punkt zu bringen.

   :::column-end:::
:::row-end:::

### <a name="error-messages"></a>Fehlermeldungen

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/error-messages-do.png" alt-text="Beispiel zeigt eine bewährte Methode für ein Aufgabenmodul (Inline-Fehlermeldungen verwenden)." border="false":::

#### <a name="do-use-inline-error-messages"></a>Tun: Verwenden von Inline-Fehlermeldungen

Anleitungen zur Inline-Fehlerbehandlung finden Sie in den Formularen zur Benutzeroberflächenvorlage.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/task-module/error-messages-dont.png" alt-text="Beispiel zeigt eine bewährte Methode für ein Aufgabenmodul (Fehlermeldungen in Dialogfelder einfügen)." border="false":::

#### <a name="dont-put-error-messages-in-dialogs"></a>Nicht tun: Fehlermeldungen in Dialogfelder einfügen

Blenden Sie keine Fehlermeldung in einem Dialogfeld über einem Aufgabenmodul ein. Dies führt zu einer verwirrenden Benutzererfahrung.

   :::column-end:::
:::row-end:::
