---
title: Entwerfen eines Besprechungs Dialogfelds in Microsoft Teams
author: heath-hamilton
description: Anleitungen und bewährte Methoden für das Entwerfen eines in-Meeting-Dialogs für Microsoft Teams.
ms.author: lajanuar
ms.topic: conceptual
ms.openlocfilehash: 89e532e6dbd83e54269606f6e051fa377de68f62
ms.sourcegitcommit: f9a2f5cedc9d30ef7a9cf78a47d01cfd277e150d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2020
ms.locfileid: "48243327"
---
# <a name="design-an-in-meeting-dialog"></a>Besprechungs-Dialogfeld entwerfen

In-Meeting-Dialoge werden in der Teams-Besprechungs Phase angezeigt. Sie benötigen Aufmerksamkeit, Bestätigung oder Interaktion eines Benutzers, sind jedoch subtil und unterbrechen die Besprechung nicht.

## <a name="use-cases"></a>Anwendungsfälle

In-Meeting-Dialogfelder werden von einem Benutzer (wie dem Besprechungsorganisator) ausgelöst, der den Teilnehmern möglicherweise Folgendes wünscht:

* Kurzes Feedback geben
* Eine kurze Umfrage oder Umfrage durchführen
* Übermitteln von Genehmigungen
* Erinnerungen abrufen

## <a name="example"></a>Beispiel

Im folgenden Beispiel wird gezeigt, wie der in-Meeting-Dialog aus der Perspektive eines Besprechungsteilnehmers aussehen könnte. Wie Sie sehen können, sind der Inhalt und die Aufgabe leicht.

:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-dialog-participant-view.png" alt-text="Beispiel zeigt, wie der in-Meeting-Dialog aus der Perspektive eines Besprechungsteilnehmers aussehen könnte.":::

<a href="https://www.figma.com/community/file/888593778835180533" target="_blank">Das vollständige Szenario anzeigen (Figma)</a>

<a href="https://www.figma.com/community/file/888593778835180533" target="_blank">Siehe andere Beispiele für Anwendungsfälle (Figma)</a>

## <a name="anatomy"></a>Anatomie

:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-dialog-anatomy.png" alt-text="UI-Anatomie einer in-Meeting-Dialogfeldansicht." border="false":::

1. **App-Symbol**
1. **App-Name**
1. **Aktionszeichenfolge**
1. **Symbol schließen:** Schließt ein einzelnes Dialogfeld. Verwenden Sie immer das obere rechte Schließsymbol anstelle einer Aktion in der Fußzeile.
1. **WebView**: zeigt alle Inhalte und Schaltflächen von Drittanbieter-apps an (Standard-Teams-Schaltflächen werden empfohlen).

### <a name="sizing"></a>Dimensionierung

In-Meeting-Dialogfelder können in der Größe variieren, um verschiedene Anwendungsfälle zu berücksichtigen, aber Sie müssen stets Abstand und Komponentengröße beibehalten.

* **Height**: die Höhe des Dialogs wird durch den Inhalt in der WebView bestimmt. Der vertikale Bildlauf übernimmt den Inhalt, der die von Ihnen angegebene maximale Höhe überschreitet.
* **Width**: die Breite der WebView ist ein absoluter Wert innerhalb des angegebenen Bereichs.

:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-dialog-sizing.png" alt-text="Abbildung mit den möglichen Dimensionen eines in-Meeting-Dialogs. Height: die Höhe des Dialogs wird durch den Inhalt in der WebView bestimmt. Der vertikale Bildlauf übernimmt den Inhalt, der die von Ihnen definierte maximale Höhe überschreitet. Min: keine. Max: 400 Pixel (320 Pixel WebView). Width: die Breite der WebView ist ein absoluter Wert innerhalb des angegebenen Bereichs. Min.: 288 Pixel (256 Pixel WebView). Max: 468 Pixel (436 Pixel WebView)." border="false":::

## <a name="behavior"></a>Verhalten

Weitere Informationen finden Sie unter Allgemeines in-Meeting-Dialog Verhalten wie Rest, laden und vieles mehr in <a href="https://www.figma.com/community/file/888593778835180533" target="_blank">Figma</a>.

### <a name="position"></a>Position

In-Meeting-Dialogfelder werden in der Mitte der Besprechungs Phase ausgerichtet. Sie können nicht gezogen werden und arbeiten im Rahmen von Microsoft Teams-Benachrichtigungen auf Systemebene.

:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-dialog-position.png" alt-text="Abbildung der UI-Anatomie eines in-Meeting-Dialogs." border="false":::

### <a name="aggregation"></a>Aggregation

Es wird jeweils nur ein Dialogfeld angezeigt, wobei das Stapel Ranking von zuletzt bis zuletzt an den unteren Rand gesendet wurde. Sobald ein Dialogfeld aufgelöst oder entlassen wurde, nimmt der nächste an seiner Stelle an.

<a href="https://www.figma.com/community/file/888593778835180533" target="_blank">Siehe ein Beispiel (Figma)</a>

### <a name="scrolling"></a>Scrollen

Der Bildlauf erfolgt im WebView-Teil eines in-Meeting-Dialogs. Beachten Sie beim Scrollen Folgendes:

* Sie sollten nur vertikal scrollen können.
* Sie können nur den Inhalt sehen, zu dem Sie einen Bildlauf durchgeführt haben (nichts oberhalb oder unterhalb).

:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-dialog-scroll.png" alt-text="Abbildung zeigt, wie der Bildlauf im WebView-Inhalt im in-Meeting-Dialog funktioniert." border="false":::

### <a name="buttons"></a>Schaltflächen

In-Meeting-Dialogfelder sind Teil der WebView ([Siehe einige Beispiele](#best-practices)).

Im Gegensatz zu ähnlichen Komponenten werden Besprechungs Dialogfelder geschlossen, nachdem ein Benutzer eine Schaltfläche ausgewählt hat.

## <a name="components"></a>Komponenten

In-Meeting-Dialoge werden in erster Linie mit den folgenden <a href="https://www.figma.com/community/file/888593778835180533" target="_blank">UI-Komponenten (Figma)</a>erstellt, die auf dem <a href="https://fluentsite.z22.web.core.windows.net/" target="_blank">Fluent-Entwurfs System</a>basieren.

Komponente | Anleitungen | Beispiel
 - | - | -
Schaltfläche | Primäre und sekundäre Schaltflächen können Mittel oder klein sein | Senden einer Antwort
Input | Feld für eine kurze Benutzereingabe. Bezeichnungstext kann ein Symbol enthalten  | Feedback eingeben
Dropdown | Wählen Sie eine oder mehrere Optionen aus einer Liste aus. Kann Such-und Mehrfachauswahl Funktionen umfassen | Auswählen einer Sprache
Auswahlsteuerelemente | Verwenden Sie Kontrollkästchen für mehrere Auswahlmöglichkeiten oder Optionsfelder, und schalten Sie Sie für einzelne Optionen ein. Für detailliertere Auswahlen verwenden Sie einen Schieberegler | Abstimmung in einer Umfrage
Warnungen | Unabhängig davon, ob eine dringende Nachricht, ein Fehlerstatus oder eine Warnung angezeigt wird, die Nachricht sollte kurz sein und die aktuelle Aufgabe des Benutzers nicht unterbrechen. | Anzeigeproblem beim Senden einer Antwort

## <a name="theming"></a>Designs

### <a name="colors"></a>Farben

Verwenden Sie das <a href="https://www.figma.com/community/file/888593778835180533" target="_blank">Empfohlene Farbschema (Figma)</a> für Hintergründe, vordergrunde und förderzustände.

### <a name="typography"></a>Typografie

Verwenden Sie die <a href="https://www.figma.com/community/file/888593778835180533" target="_blank">empfohlenen Schriftgrößen und-Gewichtungen (Figma)</a> für Titel, Textkörper und metadatentext.

## <a name="best-practices"></a>Bewährte Methoden

Während in-Meeting-Dialoge Anrufe effektiver gestalten können, können Sie auch Anrufe entgleisen, wenn Sie zu auffällig sind. Im Allgemeinen verwenden Sie die Dialogfelder sparsam, und befolgen Sie diese bewährten Methoden.

### <a name="navigation"></a>Navigation

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-dialog-steps-do.png" alt-text="Abbildung, die zeigt, wie der Inhalt von Besprechungs Dialogen auf einen einzelnen Bildschirm beschränkt wird, damit sich Benutzer auf die Besprechung konzentrieren können." border="false":::

#### <a name="do-keep-it-contained"></a>Do: enthalten bleiben

Beschränken Sie den Inhalt von Besprechungs Dialogen auf einen einzelnen Bildschirm, damit sich Benutzer auf die Besprechung konzentrieren können.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-dialog-steps-dont.png" alt-text="Abbildung zeigt, wie in-Meeting-Dialogfeldern nicht erforderlich ist, dass Benutzer durch Inhalte navigieren." border="false":::

#### <a name="dont-include-multiple-steps"></a>Nicht: mehrere Schritte einschließen

In-Besprechungs Dialogfelder sollten Benutzer nicht durch Inhalte navigieren müssen.

   :::column-end:::
:::row-end:::

### <a name="interactions"></a>Interaktionen

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-dialog-interactions-do.png" alt-text="Abbildung, die zeigt, warum Sie unnötige Inhalte entfernen sollten, die Benutzern nicht dabei helfen, schnell etwas zu erreichen." border="false":::

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-dialog-interactions-dont.png" alt-text="Eine weitere Abbildung zeigt, warum Sie unnötige Inhalte entfernen sollten, die nicht dazu beitragen, dass Benutzer schnell etwas erreichen." border="false":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-dialog-tab-do.png" alt-text="Abbildung zeigt, dass Sie, wenn Sie komplexe Interaktionen benötigen, stattdessen eine einzelne Spalte im rechten Bereich der Besprechung verwenden sollten." border="false":::

#### <a name="do-limit-number-of-interactions"></a>Do: Begrenzen der Anzahl von Interaktionen

Entfernen Sie unnötige Inhalte, die nicht dazu beitragen, dass Benutzer schnell etwas erreichen. Wenn Sie komplexe Interaktionen benötigen, wird dringend empfohlen, ihre Inhalte stattdessen in einer einzelnen Spalte auf der Registerkarte "in-Meeting" anzuzeigen.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-dialog-tab-dont.png" alt-text="Abbildung zeigt, dass zu viele Interaktionen im Dialogfeld "in-Meeting" von der Besprechung ablenken." border="false":::

#### <a name="dont-introduce-unnecessary-elements"></a>Nicht: Einführung unnötiger Elemente

Sie können möglicherweise ein einzelnes Besprechungs Dialogfeld mit mehreren Interaktionen entwerfen, aber zu viele können von der Besprechung ablenken.

   :::column-end:::
:::row-end:::

### <a name="layout"></a>Layout

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-dialog-layout-do.png" alt-text="Abbildung mit einem idealen Layout für in-Meeting-Dialoge." border="false":::

#### <a name="do-use-single-column-layouts"></a>Do: Verwenden von Einzel Spaltenlayouts

Da sich die Dialogfelder in der Mitte der Besprechungs Phase befinden, sollte die Aufgaben Vervollständigung schnell und einfach sein, um Benutzer Frustration zu vermeiden.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-dialog-layout-dont.png" alt-text="Abbildung mit Layout für in-Besprechungs Dialogfelder, die nicht empfohlen werden." border="false":::

#### <a name="dont-clutter-the-space"></a>Nicht: Übersichtlichkeit des Speicherplatzes

Dichte oder übermäßig strukturierte Inhalte können störend und überwältigend sein, vor allem während einer Besprechung.

   :::column-end:::
:::row-end:::

### <a name="size"></a>Größe

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-dialog-size-do.png" alt-text="Abbildung, die zeigt, wie die Größe des Dialogfelds in der Besprechung immer identisch sein sollte." border="false":::

#### <a name="do-keep-it-consistent"></a>Vorgehensweise: konsistent halten

Dies ist wichtig, da in-Meeting-Dialogfelder immer am gleichen Speicherort angezeigt werden.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-dialog-size-dont.png" alt-text="Abbildung zeigt, wie Sie nicht unterschiedliche Dialog Größen verwenden sollten." border="false":::

#### <a name="dont-always-fit-to-the-content"></a>Nicht: immer an den Inhalt anpassen

Möglicherweise versuchen Sie, einen horizontalen Bildlauf zu vermeiden, aber mehrere in-Meeting-Dialog Größen innerhalb derselben App stellen eine inkonsistente Erfahrung dar.

   :::column-end:::
:::row-end:::

### <a name="controls"></a>Steuerelemente

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-dialog-controls-do.png" alt-text="Illustration, in der die Schaltflächen im Dialogfeld "in-Meeting" platziert werden." border="false":::

#### <a name="do-right-align-the-primary-action"></a>Do: Rechtsbündiges Ausrichten der primären Aktion

Es wird empfohlen, die visuell intensivste Aktion an der am weitesten rechts gelegenen Stelle zu positionieren.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-dialog-controls-dont.png" alt-text="Illustration, in der die Schaltflächen im Dialogfeld "in-Meeting" nicht platziert werden." border="false":::

#### <a name="dont-left-or-center-align-actions"></a>Nicht: Links oder zentrierte Ausrichtungs Aktionen

Dies weicht vom standardmäßigen Teams-Muster für die Platzierung von Steuerelementen in einem Dialogfeld ab und kann mit einem Dialogfeld hinter dem oberen Rand in Konflikt stehen.

   :::column-end:::
:::row-end:::

## <a name="accessibility"></a>Barrierefreiheit

Informationen zur Barrierefreiheit finden Sie unter <a href="https://www.figma.com/community/file/888593778835180533" target="_blank">Figma</a>.

## <a name="resources"></a>Ressourcen

* <a href="https://www.figma.com/community/file/888593778835180533" target="_blank">Figma-Datei für Microsoft Teams-Besprechungs Erweiterungen</a>

## <a name="validate-your-design"></a>Überprüfen des Designs

Wenn Sie Ihre APP in AppSource veröffentlichen möchten, sollten Sie sich mit den Entwurfsproblemen vertraut machen, die häufig dazu führen, dass apps während der Übermittlung fehlschlagen.

> [!div class="nextstepaction"]
> [Überprüfen der Entwurfs Validierungsrichtlinien](../../concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md#validation-guidelines)
