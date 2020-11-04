---
title: Besprechungs-Registerkarte entwerfen
author: heath-hamilton
description: Hier erfahren Sie, wie Sie eine in-Meeting-Registerkarte für Microsoft Teams effektiv entwerfen.
ms.author: lajanuar
ms.topic: conceptual
ms.openlocfilehash: 402d25e543494636af287bcc2e8a308765b4cea9
ms.sourcegitcommit: df9448681d2a81f1029aad5a5e1989cd438d1ae0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/03/2020
ms.locfileid: "48877029"
---
# <a name="design-an-in-meeting-tab"></a>Besprechungs-Registerkarte entwerfen

Die Registerkarte in-Meeting ist eine Arbeitsfläche zum Erweitern der Zusammenarbeit während Besprechungen. Basierend auf den registerkartenfunktionen von Teams können Teilnehmer App-Inhalte in einem dedizierten Raum außerhalb der Besprechungs Phase über freigegebene oder rollenbasierte Ansichten anzeigen und interagieren.

## <a name="use-cases"></a>Anwendungsfälle

Die Registerkarte "in-Meeting" wird von den Benutzern möglicherweise verwendet:

* Bereitstellen eines detaillierten Feedbacks (zum Beispiel Auswerten eines Bewerbers)
* Schnelles Erstellen einer Umfrage, Umfrage oder eines Aufgabenelements für die Besprechungsteilnehmer
* Anzeigen von Notizen, die für die Besprechung relevant sind (beispielsweise Informationen zu einem Verkaufsleiter)

## <a name="example"></a>Beispiel

Das folgende Beispiel zeigt die Registerkarte in der Besprechung, in der Umfrage-App-Inhalte angezeigt werden.

:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-tab-organizer-view.png" alt-text="Das Beispiel zeigt, wie die Registerkarte Besprechung in der Besprechung aus der Perspektive eines Besprechungsorganisators aussehen könnte.":::

<a href="https://www.figma.com/community/file/888593778835180533" target="_blank">Das vollständige Szenario anzeigen (Figma)</a>

<a href="https://www.figma.com/community/file/888593778835180533" target="_blank">Siehe andere Beispiele für Anwendungsfälle (Figma)</a>

## <a name="anatomy"></a>Anatomie

Auf der Registerkarte in-Meeting werden Ihre APP-Inhalte mit den folgenden Dimensionen angezeigt:

* **Breite** : 280 Pixel für den WebView-Bereich. Auf der linken und rechten Seite des Webviews befinden sich 20 Pixel Textabstand.
* **Höhe** : vollständiges Anfärben am unteren Rand der Registerkarte. Zwischen dem WebView-Bereich und der Registerkartenüberschrift befinden sich 20 Pixelabstand.

:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-tab-anatomy.png" alt-text="Abbildung der UI-Anatomie einer Besprechungs Erweiterung in der Besprechungs Registerkarte." border="false":::

1. **App-Symbol** : der Einstiegspunkt zur Registerkarte in der Besprechung.
1. **Kopfzeile** : schließt den Registerkartennamen ein.
1. **Name** : der Name der Registerkarten Instanz.
1. **Entlassen** : die Registerkarte wird geschlossen. Verwenden Sie immer das obere rechte Schließsymbol anstelle einer Aktion in der Fußzeile.
1. **WebView** : zeigt alle Inhalte von Drittanbieter-apps an.

## <a name="behavior"></a>Verhalten

### <a name="scale"></a>Skalierung

Derzeit ist die Breite der in-Meeting-Registerkarte festgelegt.

### <a name="scrolling"></a>Scrollen

Hier erfahren Sie, was Sie über das Scrollen auf der Registerkarte "in-Meeting" wissen:

* Sie sollten nur vertikal scrollen können.
* Sie können nur den Inhalt sehen, zu dem Sie einen Bildlauf durchgeführt haben (nichts oberhalb oder unterhalb).
* Die ScrollBar ist Teil des WebView-Inhalts.

:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-tab-scroll.png" alt-text="Abbildung zeigt, wie der Bildlauf in der WebView-Inhalt auf der Registerkarte in-Meeting funktioniert." border="false":::

### <a name="navigation"></a>Navigation

Für Szenarien mit Navigationsebenen oder schweren Inhalten empfehlen wir, Benutzern das Navigieren zu einer sekundären Ebene zu ermöglichen. Benutzer müssen in der Lage sein, zur vorherigen Ebene zurückzukehren.

:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-tab-nav.png" alt-text="Abbildung, die zeigt, wie die Navigation zu einer sekundären Ebene auf der in-Meeting-Registerkarte funktioniert." border="false":::

## <a name="components"></a>Komponenten

In-Meeting-Registerkarten werden in erster Linie mit den folgenden <a href="https://www.figma.com/community/file/888593778835180533" target="_blank">UI-Komponenten (Figma)</a>erstellt, die auf dem <a href="https://fluentsite.z22.web.core.windows.net/" target="_blank">Fluent-Entwurfs System</a>basieren.

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

### <a name="responsiveness"></a>Suchen

In-Meeting-Registerkarten Layouts sollten in der Lage sein, verschiedene Größen zu skalieren. Berücksichtigen Sie, wie die Registerkarte skaliert wird und wie Sie Form vor, während und nach der Besprechung nimmt.

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-tab-before-meeting.png" alt-text="Abbildung zeigt, dass der Inhalt der Besprechungs Registerkarte vor und nach einer Besprechung wie eine voll Bild Registerkarte aussieht." border="false":::

#### <a name="before-the-meeting"></a>Vor der Besprechung

Stellen Sie sicher, dass sich das registerkartenlayout an ein rechts-oder links Layout für unterschiedliche Sprachen anpassen kann und dass Steuerelemente an die richtigen Stellen verschoben werden. (Vorab-Besprechungs Layouts können auch auf Post-Meeting-Layouts angewendet werden.)

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-tab-during-meeting.png" alt-text="Abbildung, die zeigt, wie der Inhalt der Registerkarte &quot;Pre-Meeting&quot; auf die Registerkarte &quot;in-Meeting&quot; während einer Besprechung verkürzt wird." border="false":::

#### <a name="during-the-meeting"></a>Während der Besprechung

Der Inhalt der Registerkarte wird an das Layout und die Position in der Besprechungs Registerkarte angepasst.

   :::column-end:::
:::row-end:::

### <a name="theming"></a>Designs

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-tab-theming-do.png" alt-text="Illustration, die zeigt, wie Sie die in-Meeting-Registerkarte für das dunkle Design entwerfen, das in Microsoft Teams-Besprechungen verwendet wird." border="false":::

#### <a name="do-design-for-a-dark-theme"></a>Do: Design für ein dunkles Design

Microsoft Teams-Besprechungen sind für den dunklen Modus optimiert, um visuelles und kognitives Rauschen zu reduzieren, sodass sich Benutzer auf die Diskussion und den freigegebenen Inhalt konzentrieren können.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-tab-theming-dont.png" alt-text="Abbildung zeigt, dass Sie keine Farben verwenden sollten, die dem dunklen Design von Teams nicht förderlich sind." border="false":::

#### <a name="dont-use-unfamiliar-colors"></a>Nicht: Unbekannte Farben verwenden

Farben, die mit der Besprechungs Umgebung kollidieren, sind möglicherweise störend und werden in Microsoft Teams eher als systemeigen dargestellt.

   :::column-end:::
:::row-end:::

### <a name="scrolling"></a>Scrollen

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-tab-scroll-do.png" alt-text="Die Abbildung zeigt, dass Sie auf der Registerkarte &quot;in-Meeting&quot; nur den vertikalen Bildlauf zulassen sollten." border="false":::

#### <a name="do-scroll-vertically"></a>Do: vertikal scrollen

Benutzer erwarten vertikales Scrollen in Microsoft Teams (und anderswo).

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-tab-scroll-dont.png" alt-text="Die Abbildung zeigt, dass auf der Registerkarte &quot;in-Meeting&quot; kein horizontaler Bildlauf zulässig ist." border="false":::

#### <a name="dont-scroll-horizontally"></a>Nicht: horizontal scrollen

Ein horizontaler Bildlauf ist kein erwartetes Verhalten in Microsoft Teams. Andere Canvases in der Besprechungs Umgebung Scrollen vertikal.

   :::column-end:::
:::row-end:::

### <a name="layout"></a>Layout

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-tab-layout-do.png" alt-text="Abbildung mit dem empfohlenen Layout mit einer einzelnen Spalte auf der Registerkarte &quot;in-Meeting&quot;." border="false":::

#### <a name="do-single-columns"></a>Do: einzelne Spalten

Angesichts der engen Natur in der Besprechungs Registerkarte wird dringend empfohlen, den Inhalt in einer einzelnen Spalte anzuzeigen.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-tab-layout-dont.png" alt-text="Abbildung zeigt, wie ein zweispaltiges Layout auf der Registerkarte &quot;in-Meeting&quot; nicht ideal ist." border="false":::

#### <a name="dont-multiple-columns"></a>Nicht: mehrere Spalten

Aufgrund des begrenzten Speicherplatzes der in-Meeting-Registerkarte werden Layouts mit mehr als einer Spalte nicht empfohlen.

   :::column-end:::
:::row-end:::

### <a name="navigation"></a>Navigation

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-tab-nav-do.png" alt-text="Abbildung zeigt, dass Sie immer eine Schaltfläche &quot;zurück&quot; bereitstellen sollten, wenn Ihre in-Meeting-Registerkarten-app mehr als eine Navigationsebene aufweist." border="false":::

#### <a name="do-have-a-back-button"></a>Do: verfügen über eine Schaltfläche "zurück"

Wenn Sie mehr als eine Navigations Schicht haben, müssen die Benutzer in der Lage sein, zur vorherigen Ansicht zurückzukehren.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-tab-nav-dont.png" alt-text="Abbildung zeigt, dass das Hinzufügen einer weiteren Schaltfläche Schließen auf der Registerkarte in-Meeting für die Navigation redundant ist und Probleme verursachen könnte." border="false":::

#### <a name="dont-include-another-close-button"></a>Nicht: Einschließen einer weiteren schließen-Schaltfläche

Das Bereitstelleneiner Option zum Schließen von Inhalten in Besprechungs Registerkarten kann Probleme verursachen, da bereits eine Schaltfläche zum Schließen in der Kopfzeile vorhanden ist, um die in-Meeting-Registerkarte selbst zu schließen.

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/calls-and-meetings/in-meeting-tab-nav-caution.png" alt-text="Abbildung zeigt, dass Sie bei der Verwendung von modals (also Aufgaben Modulen) auf der Registerkarte &quot;in-Meeting&quot; mit dem begrenzten Platz Vorsicht walten lassen müssen." border="false":::

#### <a name="caution-using-dialogs-in-a-narrow-space"></a>Vorsicht: Verwenden von Dialogfeldern auf engstem Raum

Dialogfelder, beispielsweise Vorgangs Module, können den Inhalt in der bereits engen Registerkarte in Besprechungen Umbrechen und verdecken.

   :::column-end:::
:::row-end:::

## <a name="accessibility"></a>Barrierefreiheit

Informationen zur Barrierefreiheit finden Sie unter <a href="https://www.figma.com/community/file/888593778835180533" target="_blank">Figma</a>.

## <a name="resources"></a>Ressourcen

* <a href="https://www.figma.com/community/file/888593778835180533" target="_blank">Figma-Datei für Microsoft Teams-Besprechungs Erweiterungen</a>
* [Entwurfsrichtlinien für Registerkarten](../../tabs/design/tabs.md)
* [Entwurfsrichtlinien für Tabs für mobile Geräte](../../tabs/design/tabs-mobile.md)

## <a name="validate-your-design"></a>Überprüfen des Designs

Wenn Sie Ihre APP in AppSource veröffentlichen möchten, sollten Sie sich mit den Entwurfsproblemen vertraut machen, die häufig dazu führen, dass apps während der Übermittlung fehlschlagen.

> [!div class="nextstepaction"]
> [Überprüfen der Entwurfs Validierungsrichtlinien](../../concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md#validation-guidelines--most-failed-test-cases)
