---
title: Entwerfen ihrer Besprechungserweiterung
author: heath-hamilton
description: Erfahren Sie, wie Sie Apps in Teams Meetings entwerfen und das Microsoft Teams UI Kit abrufen.
ms.author: lajanuar
localization_priority: Normal
ms.topic: conceptual
ms.openlocfilehash: 0a888c333305e9caafcd0bac0e5549bf08ead424
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566026"
---
# <a name="designing-your-microsoft-teams-meeting-extension"></a>Entwerfen der Microsoft Teams Besprechungserweiterung

Sie können Apps erstellen, um Besprechungen produktiver zu gestalten. Bitten Sie beispielsweise Personen, während eines Anrufs eine Umfrage abzuschließen, oder senden Sie eine schnelle Erinnerung, die den Ablauf der Besprechung nicht unterbricht.

## <a name="microsoft-teams-ui-kit"></a>Microsoft Teams-UI-Kit

Umfassendere Entwurfsrichtlinien, einschließlich Elemente, die Sie bei Bedarf greifen und ändern können, finden Sie im Microsoft Teams UI Kit.

> [!div class="nextstepaction"]
> [Holen Sie sich das Microsoft Teams-UI-Kit (Figma)](https://www.figma.com/community/file/916836509871353159)

## <a name="add-a-meeting-extension"></a>Hinzufügen einer Besprechungserweiterung

Sie können eine Besprechungserweiterung vor und während der Besprechungen hinzufügen. Sie können auch eine App für eine bestimmte Besprechung direkt aus dem Teams Store (AppSource) hinzufügen.

### <a name="add-before-a-meeting"></a>Hinzufügen vor einer Besprechung

Wählen Sie in den Besprechungsdetails **eine Registerkarte hinzufügen aus,** um das App-Flyout zu öffnen und für Besprechungen optimierte Apps zu finden.

:::image type="content" source="../../assets/images/apps-in-meetings/add-before-meeting.png" alt-text="Das Beispiel zeigt, wie sie eine Besprechungserweiterung vor einer Besprechung hinzufügen." border="false":::

### <a name="add-during-a-meeting"></a>Hinzufügen während einer Besprechung

Wählen Sie in einer Besprechung **Weitere** :::image type="icon" source="../../assets/icons/teams-client-more.png":::  >  **Informationen zum Hinzufügen einer App** aus, und wählen Sie die gewünschte App aus.

:::image type="content" source="../../assets/images/apps-in-meetings/add-during-meeting.png" alt-text="Das Beispiel zeigt, wie sie während einer Besprechung eine Besprechungserweiterung hinzufügen." border="false":::

## <a name="before-a-meeting"></a>Vor einer Besprechung

Vor Ihrer Besprechung können Sie Inhalte auf der Registerkarte hinzufügen. Das folgende Beispiel zeigt einen Umfrageentwurf, den die Teilnehmer während des Anrufs beantworten.

:::image type="content" source="../../assets/images/apps-in-meetings/before-meeting-tab.png" alt-text="Das Beispiel zeigt, wie Sie Inhalte in den Besprechungsdetails vor einem Anruf anzeigen." border="false":::

### <a name="anatomy-meeting-tab-before-and-after-meetings"></a>Anatomie: Registerkarte Meeting (vor und nach Besprechungen)

:::image type="content" source="../../assets/images/apps-in-meetings/meeting-details-tab-anatomy.png" alt-text="Das Beispiel zeigt die strukturelle Anatomie einer Besprechungsregisterkarte vor und nach einer Besprechung." border="false":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|1|**Tab-Name**: Navigationsbeschriftung für Ihre Registerkarte.|
|2|**Tab-Überlauf**: Öffnet Tabstoppaktionen, z. B. Umbenennen und Entfernen.|
|3|**iframe**: Zeigt Ihre App-Inhalte an.|

### <a name="designing-with-ui-templates"></a>Entwerfen mit UI-Vorlagen

Verwenden Sie eine der folgenden Teams UI-Vorlagen, um die Besprechungsregisterkarte zu entwerfen:

* [Liste](../../concepts/design/design-teams-app-ui-templates.md#list): Listen können verwandte Elemente in einem scannbaren Format anzeigen und Benutzern ermöglichen, Aktionen für eine gesamte Liste oder einzelne Elemente auszuführen.
* [Aufgabentafel](../../concepts/design/design-teams-app-ui-templates.md#task-board): Ein Aufgabenbrett, manchmal auch Kanban-Board oder Schwimmbahnen genannt, ist eine Sammlung von Karten, die oft verwendet werden, um den Status von Arbeitsaufgaben oder Tickets zu verfolgen.
* [Dashboard](../../concepts/design/design-teams-app-ui-templates.md#dashboard): Ein Dashboard ist ein Canvas mit mehreren Karten, die einen Überblick über Daten oder Inhalte bieten.
* [Formular](../../concepts/design/design-teams-app-ui-templates.md#form): Formulare sind zum Sammeln, Validieren und Übermitteln von Benutzereingaben auf strukturierte Weise.
* [Leerer Zustand](../../concepts/design/design-teams-app-ui-templates.md#empty-state): Die leere Statusvorlage kann für viele Szenarien verwendet werden, einschließlich Anmeldung, Erstausführung, Fehlermeldungen und mehr.
* [Linkes Navi](../../concepts/design/design-teams-app-ui-templates.md#left-nav): Die linke Navi-Vorlage kann helfen, wenn Ihre Registerkarte eine Gewisse Navigation erfordert. Im Allgemeinen sollten Sie die Tab-Navigation auf ein Minimum beschränken.

## <a name="use-an-in-meeting-tab"></a>Verwenden einer Registerkarte in Besprechungen

Die Registerkarte "In-Meeting" ist eine Arbeitsfläche zum Erweitern der Zusammenarbeit während Besprechungen. Teilnehmer können App-Inhalte in einem dedizierten Bereich außerhalb der Besprechungsphase durch freigegebene oder rollenbasierte Ansichten anzeigen und mit ihnen interagieren.

### <a name="use-cases"></a>Anwendungsfälle

Personen können die Registerkarte "In-Meeting" verwenden, um:

* Geben Sie detailliertes Feedback. Bewerten Sie beispielsweise einen Stellenbewerber.
* Erstellen Sie eine Umfrage, Umfrage oder ein Aufgabenelement für die Besprechungsteilnehmer.
* Zeigt Notizen an, die für die Besprechung relevant sind. Beispiel: Informationen zu einem Verkaufsleiter.

:::image type="content" source="../../assets/images/apps-in-meetings/use-in-meeting-tab.png" alt-text="Das Beispiel zeigt, wie Sie Umfrageinhalte auf einer Besprechungsregisterkarte darstellen können." border="false":::

### <a name="anatomy-in-meeting-tab"></a>Anatomie: Registerkarte "In-Meeting"

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-anatomy.png" alt-text="Das Beispiel zeigt die strukturelle Anatomie einer Registerkarte in Besprechungen." border="false":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|1|**App-Symbol (ausgewählt):** 16-Pixel-transparentes App-Logo.|
|2|**App-Name**|
|3|**Header**: Enthält Ihren App-Namen.|
|4 |**Schaltfläche Schließen**: Schließt die Registerkarte ab. Verwenden Sie immer das obere rechte Nahsymbol anstelle einer Aktion in der Fußzeile.|
|5 |**Benachrichtigungsleiste**: Fehlerwarnungen werden direkt unter der Kopfzeile angezeigt und drücken den iframe-Inhalt um 20 Pixel nach unten.|
|6 |**iframe**: Zeigt Ihre App-Inhalte an.|

### <a name="spacing"></a>Abstand

Optimieren Sie Ihre Registerkarte in Meetings, um Edge-to-Edge innerhalb des 280 Pixel breiten iframe-Bereichs anzupassen. Auf der linken und rechten Seite des iframes und zwischen dem Tab-Header befinden sich 20 Pixel Auffüllung. Der iframe ist voll bluten bis zum unteren Rand der Registerkarte.

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-spacing.png" alt-text="Das Beispiel zeigt in-Meeting-Tababstanddimensionen." border="false":::

### <a name="scrolling"></a>Scrollen

Iframe-Inhalte sollten vertikal scrollen. Sie können nur den Inhalt sehen, zu dem Sie gescrollt haben (nichts über oder unter). Die Bildlaufleiste ist Teil des iframe-Inhalts.

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-scrolling.png" alt-text="Das Beispiel zeigt, wie die Registerkarte in Besprechung scrollt." border="false":::

### <a name="navigation"></a>Navigation

Für Szenarien mit Navigationsebenen oder schwerem Inhalt wird empfohlen, Benutzern das Navigieren zu einer sekundären Ebene zu ermöglichen. Benutzer müssen in der Lage sein, zur vorherigen Ebene zurückzukehren.

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav.png" alt-text="Beispiel zeigt in Der Besprechungsnavigation." border="false":::

## <a name="use-an-in-meeting-dialog"></a>Verwenden eines Dialogfelds in der Besprechung

In-Meeting-Dialoge werden auf der Teams Besprechungsphase angezeigt. Sie erfordern die Aufmerksamkeit, Bestätigung oder Interaktion eines Benutzers, sind jedoch subtil und unterbrechen die Besprechung nicht. Sie sollten diese sparsam und für Szenarien verwenden, die licht- und aufgabenorientiert sind.

### <a name="use-cases"></a>Anwendungsfälle

In Besprechungsdialogen werden von einem Benutzer (z. B. dem Besprechungsorganisator) ausgelöst, der teilnehmer möglicherweise wie folgt:

* Kurzes Feedback geben
* Nehmen Sie an einer kurzen Umfrage oder Umfrage teil
* Bewillisch einreichen
* Erhalten Sie Erinnerungen

:::image type="content" source="../../assets/images/apps-in-meetings/use-in-meeting-dialog.png" alt-text="Das Beispiel zeigt, wie Sie ein Dialogfeld in der Besprechung verwenden können." border="false":::

### <a name="anatomy-in-meeting-dialog"></a>Anatomie: Dialog im Gespräch

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-anatomy.png" alt-text="Das Beispiel zeigt die strukturelle Anatomie eines Dialogfelds im Besprechungsdialog." border="false":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|1|**Kopfzeile**: Enthält App-Symbol, Name, Aktionszeichenfolge und Schließen-Symbol.|
|2|**iframe**: Zeigt Ihre App-Inhalte an.|

### <a name="anatomy-in-meeting-dialog-header"></a>Anatomie: Dialogkopf im Besprechungsgespräch

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-header-anatomy.png" alt-text="Das Beispiel zeigt die strukturelle Anatomie eines Dialogheaders in Besprechungen." border="false":::

Es gibt zwei Headervarianten. Wenn möglich, verwenden Sie die Variante mit dem Avatar, um zu verstärken, dass der Dialog von einer Person kommt.

|Leistungsindikator|Beschreibung|
|----------|-----------|
|1|**Avatar**: Person, die den Dialog im Besprechungsdialog initiiert.|
|2|**App-Symbol**|
|3|**App-Name**|
|4 |**Schaltfläche Schließen**: Schließt das Dialogfeld ab.|
|5 |**Aktionszeichenfolge**: Beschreibt in der Regel, wer das Dialogfeld initiiert hat.|

### <a name="responsive-behavior"></a>Dynamisches Verhalten

In Besprechungsdialogen kann in der Größe variieren, um verschiedene Szenarien zu berücksichtigen. Achten Sie darauf, die Polsterung und die Komponentengrößen beizubehalten.

* **Breite**: Sie können die Breite des iframes des Dialogfelds an einer beliebigen Stelle innerhalb des unterstützten Größenbereichs angeben.
* **Höhe**: Sie können die Höhe des iframes des Dialogfelds an einer beliebigen Stelle innerhalb des unterstützten Größenbereichs angeben. Sie können Benutzern auch erlauben, vertikal zu scrollen, wenn Ihr App-Inhalt die maximale Höhe überschreitet.

Geben Sie zum Implementieren die Breite und Höhe mithilfe des [`externalResourceUrl`](~/apps-in-teams-meetings/create-apps-for-teams-meetings.md#notificationsignal-api) Schlüssels an.

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-responsive.png" alt-text="Das Beispiel zeigt das Dialogfeld in der Besprechung. Breite: Min--280 Pixel (248 Pixel iframe). Max--460 Pixel (428 Pixel iframe). Höhe: 300 Pixel (iframe)." border="false":::

## <a name="after-a-meeting"></a>Nach einem Meeting

Sie können nach dem Ende zu einer Besprechung zurückkehren und App-Inhalte anzeigen. In diesem Beispiel kann sich der Besprechungsorganisator die Umfrageergebnisse auf der **Registerkarte Contoso** ansehen. (Hinweis: Vom Entwurfsstandpunkt aus gibt es keinen Unterschied zwischen einer Registerkarte vor und nach dem Meeting.)

:::image type="content" source="../../assets/images/apps-in-meetings/post-meeting-experience.png" alt-text="Die Beispielabbildung zeigt eine Registerkarte nach dem Meeting." border="false":::

## <a name="best-practices"></a>Bewährte Methoden

Verwenden Sie diese Empfehlungen, um eine hochwertige App-Erfahrung zu erstellen.

### <a name="interactions"></a>Interaktionen

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/interaction-do.png" alt-text="Beispiel, das zeigt, wie die Anzahl der Interaktionen begrenzt wird." border="false":::

#### <a name="do-limit-the-number-of-interactions"></a>Tun: Beschränken sie die Anzahl der Interaktionen

Entfernen Sie bei Besprechungsdialogen unnötige Inhalte, die Benutzern nicht dabei helfen, schnell etwas zu erreichen.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/interaction-dont.png" alt-text="Beispiel, das zeigt, wie keine unnötigen Elemente eingeführt werden." border="false":::

#### <a name="dont-introduce-unnecessary-elements"></a>Nicht: Unnötige Elemente einführen

Ein einzelner Dialog mit mehreren Interaktionen kann vom Aufruf ablenken.

   :::column-end:::
:::row-end:::

### <a name="layout"></a>Layout

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-layout-do.png" alt-text="Beispiel, das zeigt, wie Sie ein einspaltiges Dialogfeldlayout verwenden sollten." border="false":::

#### <a name="do-use-a-single-column-dialog-layout"></a>Tun: Verwenden eines einspaltigen Dialoglayouts

Da die Dialoge im Mittelpunkt der Besprechungsphase stehen, sollte die Aufgabenvervollständigung schnell und einfach sein, um Benutzerfrustrationen zu vermeiden.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-layout-dont.png" alt-text="Beispiel, das zeigt, dass Sie den Raum einer Besprechungserweiterung nicht überladen sollten." border="false":::

#### <a name="dont-clutter-the-space"></a>Nicht: Den Raum überladen

Dichte oder zu strukturierte Inhalte können ablenkend und überwältigend sein, insbesondere während eines Meetings.

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-layout-do.png" alt-text="Beispiel für ein einspaltiges Registerkartenlayout." border="false":::

#### <a name="do-use-a-single-column-tab-layout"></a>Tun: Verwenden eines einspaltigen Registerkartenlayouts

Angesichts der engen Natur der Registerkarte "In-Meeting" wird dringend empfohlen, den Inhalt in einer einzelnen Spalte anzuzeigen.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-layout-dont.png" alt-text="Beispiel, das eine Registerkarte mit mehreren Spalten anzeigt." border="false":::

#### <a name="dont-use-multiple-columns"></a>Nicht: Verwenden Sie mehrere Spalten

Aufgrund des begrenzten Platzes auf der Registerkarte "In-Meeting" werden Layouts mit mehr als einer Spalte nicht empfohlen.

   :::column-end:::
:::row-end:::

### <a name="controls"></a>Steuerelemente

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-controls-do.png" alt-text="Beispiel, das zeigt, wie primäre Steuerelemente rechts ausgerichtet werden." border="false":::

#### <a name="do-right-align-the-primary-action"></a>Tun: Rechts richten Sie die primäre Aktion aus

Wir empfehlen, die visuell schwerste Aktion an der richtigen Stelle zu positionieren.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-controls-dont.png" alt-text="Beispiel, das zeigt, wie Sie primäre Steuerelemente nicht links ausrichten sollten." border="false":::

#### <a name="dont-left-or-center-align-actions"></a>Nicht: Aktionen nach links oder in der Mitte ausrichten

Dies weicht vom Standardmuster Teams für die Steuerplatzierung in einem Dialog feldieren und kann mit einem Dialog feldieren.

   :::column-end:::
:::row-end:::

### <a name="scroll"></a>Bildlauf

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-scroll-do.png" alt-text="Beispiel für vertikales Scrollen auf einer Besprechungsregisterkarte." border="false":::

#### <a name="do-scroll-vertically"></a>Tun: Vertikal scrollen

Benutzer erwarten vertikales Scrollen in Teams (und anderswo).

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-scroll-dont.png" alt-text="Beispiel für horizontales Scrollen in einer Besprechungsregisterkarte." border="false":::

#### <a name="dont-scroll-horizontally"></a>Nicht: Horizontal scrollen

Horizontales Scrollen ist kein erwartetes Verhalten in Teams. Andere Leinwände in der Besprechungsumgebung scrollen vertikal.

   :::column-end:::
:::row-end:::

### <a name="workflows"></a>Workflows

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-workflow-do.png" alt-text="Beispiel für das Zeigen eines komplexen Szenarios auf einer Registerkarte in Besprechungen." border="false":::

#### <a name="do-surface-complex-scenarios-in-the-in-meeting-tab"></a>Tun: Komplexe Szenarien auf der Registerkarte "In-Meeting" anzeigen

Wenn Ihre App mehrere Aufgaben enthält, wird dringend empfohlen, eine Registerkarte in Besprechungen mit einem einspaltigen Layout zu verwenden.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-workflow-dont.png" alt-text="Beispiel für komplexe Szenarien in einem Besprechungsdialog." border="false":::

#### <a name="dont-make-in-meeting-dialogs-complex"></a>Nicht: In-Meeting-Dialoge komplex machen

In Besprechungsdialogen sind für kurze Interaktionen vorgesehen.

   :::column-end:::
:::row-end:::

### <a name="theming"></a>Designs

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-theming-do.png" alt-text="Beispiel für eine Besprechungserweiterung mit dem dunklen Thema." border="false":::

#### <a name="do-use-teams-color-tokens"></a>Tun: Verwenden Teams Farbtoken

Teams Meetings sind für den dunklen Modus optimiert, um visuelles und kognitives Rauschen zu reduzieren, sodass sich Benutzer auf die Diskussion und freigegebene Inhalte konzentrieren können. Erfahren Sie mehr über die Verwendung von <a href="https://fluentsite.z22.web.core.windows.net/0.51.3/colors#color-scheme" target="_blank">Farbtoken (Fluent UI)</a>.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-theming-dont.png" alt-text="Beispiel für eine Besprechungserweiterung mit einem Standarddesign (Licht)." border="false":::

#### <a name="dont-hard-code-hex-values"></a>Nicht: Hartcode-Hex-Werte

Wenn Sie keine Teams Farbtoken verwenden, sind Ihre Designs weniger skalierbar und nehmen mehr Zeit in Anspruch.

   :::column-end:::
:::row-end:::

### <a name="navigation"></a>Navigation

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav-do.png" alt-text="Beispiel für eine Besprechungserweiterung mit einer Zurück-Schaltfläche." border="false":::

#### <a name="do-have-a-back-button"></a>Do: Haben Sie eine Zurück-Taste

Wenn Sie mehr als eine Navigationsebene auf einer Registerkarte in Besprechungen haben, müssen Benutzer in der Lage sein, zu ihren vorherigen Ansichten zurückzukehren.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav-dont.png" alt-text="Beispiel für eine Besprechungserweiterung mit zwei Abweisungsschaltflächen." border="false":::

#### <a name="dont-include-another-dismiss-button"></a>Nicht: Fügen Sie eine weitere Abweisungsschaltfläche ein

Das Bereitstellen einer Option zum Schließen von Besprechungsregisterkarteninhalten kann Probleme verursachen, da sich bereits eine Schaltfläche im Header befindet, um die Registerkarte in Besprechungen selbst zu schließen.

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav-caution.png" alt-text="Beispiel für Modals (oder Aufgabenmodule) auf einer Registerkarte in Besprechungen." border="false":::

#### <a name="caution-avoid-modals-within-the-in-meeting-tab"></a>Achtung: Vermeiden Sie Modals innerhalb der Registerkarte in Besprechungen

Modals (auch als Taskmodule bezeichnet) auf der bereits schmalen Registerkarte in Besprechungen können den Inhalt umschließen und verschleiern.

   :::column-end:::
:::row-end:::
