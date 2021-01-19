---
title: Entwerfen der Besprechungserweiterung
author: heath-hamilton
description: Erfahren Sie, wie Sie Apps in Teams-Besprechungen entwerfen und das Microsoft Teams UI Kit erhalten.
ms.author: lajanuar
ms.topic: conceptual
ms.openlocfilehash: c6e76356b698da4e32e279b0842ab2cc35254e99
ms.sourcegitcommit: 84f408aa2854aa7a5cefaa66ce9a373b19e0864a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/18/2021
ms.locfileid: "49886758"
---
# <a name="designing-your-microsoft-teams-meeting-extension"></a>Entwerfen Ihrer Microsoft Teams-Besprechungserweiterung

Sie können Apps erstellen, um Besprechungen produktiver zu gestalten. Bitten Sie beispielsweise Personen, während eines Anrufs eine Umfrage zu führen, oder senden Sie eine kurze Erinnerung, die den Ablauf der Besprechung nicht unterbricht.

## <a name="microsoft-teams-ui-kit"></a>Microsoft Teams UI Kit

Umfassendere Designrichtlinien, einschließlich Elemente, die Sie bei Bedarf verwenden und ändern können, finden Sie im Microsoft Teams UI Kit.

> [!div class="nextstepaction"]
> [Microsoft Teams UI Kit (Bissma)](https://www.figma.com/community/file/916836509871353159)

## <a name="add-a-meeting-extension"></a>Hinzufügen einer Besprechungserweiterung

Sie können vor und während Besprechungen eine Besprechungserweiterung hinzufügen. Sie können eine App für eine bestimmte Besprechung auch direkt aus dem Teams Store (AppSource) hinzufügen.

### <a name="add-before-a-meeting"></a>Hinzufügen vor einer Besprechung

Wählen Sie in den Besprechungsdetails "Registerkarte **hinzufügen" aus,** um das App-Flyout zu öffnen und apps zu suchen, die für Besprechungen optimiert sind.

:::image type="content" source="../../assets/images/apps-in-meetings/add-before-meeting.png" alt-text="Im Beispiel wird gezeigt, wie Sie vor einer Besprechung eine Besprechungserweiterung hinzufügen." border="false":::

### <a name="add-during-a-meeting"></a>Hinzufügen während einer Besprechung

Wählen Sie in einer Besprechung **"Weitere** :::image type="icon" source="../../assets/icons/teams-client-more.png":::  >  **Hinzufügen einer App"** aus, und wählen Sie die App aus, die Sie wünschen.

:::image type="content" source="../../assets/images/apps-in-meetings/add-during-meeting.png" alt-text="Beispiel zeigt, wie sie während einer Besprechung eine Besprechungserweiterung hinzufügen." border="false":::

## <a name="before-a-meeting"></a>Vor einer Besprechung

Vor Ihrer Besprechung können Sie Inhalte auf der Registerkarte hinzufügen. Das folgende Beispiel zeigt einen Umfrageentwurf, den Personen während des Anrufs beantworten.

:::image type="content" source="../../assets/images/apps-in-meetings/before-meeting-tab.png" alt-text="Im Beispiel wird gezeigt, wie Inhalte in den Besprechungsdetails vor einem Anruf app-n." border="false":::

### <a name="anatomy-meeting-tab-before-and-after-meetings"></a>Anatomie: Registerkarte "Besprechung" (vor und nach Besprechungen)

:::image type="content" source="../../assets/images/apps-in-meetings/meeting-details-tab-anatomy.png" alt-text="Beispiel zeigt die strukturell angepasste Struktur einer Besprechungsregisterkarte vor und nach einer Besprechung." border="false":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|1|**Registerkartenname:** Navigationsbezeichnung für Ihre Registerkarte.|
|2 |**Registerkartenüberlauf:** Öffnet Registerkartenaktionen, z. B. Umbenennen und Entfernen.|
|3|**iframe**: Zeigt Ihre App-Inhalte an.|

### <a name="designing-with-ui-templates"></a>Entwerfen mit Benutzeroberflächenvorlagen

Verwenden Sie eine der folgenden Teams-UI-Vorlagen, um Ihre Besprechungsregisterkarte zu entwerfen:

* [Liste](../../concepts/design/design-teams-app-ui-templates.md#list): Listen können verwandte Elemente in einem scannierbaren Format anzeigen und Benutzern das Ausführen von Aktionen für eine gesamte Liste oder einzelne Elemente ermöglichen.
* [Task Board:](../../concepts/design/design-teams-app-ui-templates.md#task-board)Ein Task Board, manchmal auch als Kanban Board oder Rettungsweg bezeichnet, ist eine Sammlung von Karten, die häufig verwendet werden, um den Status von Arbeitselementen oder Tickets nachverfolgt.
* [Dashboard:](../../concepts/design/design-teams-app-ui-templates.md#dashboard)Ein Dashboard ist eine Canvas mit mehreren Karten, die eine Übersicht über Daten oder Inhalte bieten.
* [Formular:](../../concepts/design/design-teams-app-ui-templates.md#form)Formulare sind für die strukturierte Erfassung, Validierung und Übermittlung von Benutzereingaben.
* [Leerer](../../concepts/design/design-teams-app-ui-templates.md#empty-state)Zustand: Die Vorlage "Leerer Zustand" kann für viele Szenarien verwendet werden, z. B. anmeldung, Erste Ausführung, Fehlermeldungen und vieles mehr.
* [Linke Navigationsleiste:](../../concepts/design/design-teams-app-ui-templates.md#left-nav)Die linke Navigationsvorlage kann hilfreich sein, wenn ihre Registerkarte eine gewisse Navigation erfordert. Im Allgemeinen sollten Sie die Registerkartennavigation auf ein Minimum beschränken.

## <a name="use-an-in-meeting-tab"></a>Verwenden einer Registerkarte für Besprechungen

Die Registerkarte "Besprechung" ist eine Canvas zum Erweitern der Zusammenarbeit während Besprechungen. Teilnehmer können über freigegebene oder rollenbasierte Ansichten in einem dedizierten Bereich außerhalb der Besprechungsphase mit den Inhalten der App interagieren.

### <a name="use-cases"></a>Anwendungsfälle

Personen können die Registerkarte "Besprechung" verwenden, um:

* Geben Sie detailliertes Feedback (z. B. Bewerten eines Stellenkandidaten)
* Schnelles Erstellen eines Umfrage-, Umfrage- oder Aufgabenelements für die Besprechungsteilnehmer
* Anzeigen von für die Besprechung relevanten Notizen (z. B. Informationen zu einem Vertriebsleiter)

:::image type="content" source="../../assets/images/apps-in-meetings/use-in-meeting-tab.png" alt-text="Ein Beispiel zeigt, wie Sie Umfrageinhalte auf einer Registerkarte für Besprechungen präsentieren können." border="false":::

### <a name="anatomy-in-meeting-tab"></a>Aufbau: Registerkarte "In-Meeting"

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-anatomy.png" alt-text="Beispiel zeigt die strukturell angepasste Struktur einer Registerkarte in Besprechungen." border="false":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|1|**App-Symbol (ausgewählt):** 16 Pixel transparentes App-Logo.|
|2 |**App-Name**|
|3|**Header:** Enthält den App-Namen.|
|4 |**Schaltfläche "Schließen":** Schließt die Registerkarte. Verwenden Sie immer das obere rechte Schließensymbol anstelle einer Aktion in der Fußzeile.|
|5 |**Benachrichtigungsleiste:** Fehlerwarnungen werden direkt unterhalb der Kopfzeile angezeigt, und der iframe-Inhalt wird um 20 Pixel nach unten geschoben.|
|6 |**iframe**: Zeigt Ihre App-Inhalte an.|

### <a name="spacing"></a>Abstand

Optimieren Sie Ihre Registerkarte in Besprechungen so, dass sie in den 280 Pixel breiten iframe-Bereich von Rand zu Rand passt. Es gibt 20 Pixel Abstand auf der linken und rechten Seite des iframe und zwischen der Registerkartenüberschrift. Der iframe ist vollständig beschnitten bis unten auf der Registerkarte.

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-spacing.png" alt-text="Beispiel zeigt die Abmessungen des Abstands von Registerkarten in Besprechungen." border="false":::

### <a name="scrolling"></a>Scrollen

Der Bildlauf von Iframeinhalten sollte vertikal durchgeführt werden. Sie können nur den Inhalt sehen, zu dem Sie einen Bildlauf durchgeführt haben (nichts über oder darunter). Die Bildlaufleiste ist Teil des iframe-Inhalts.

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-scrolling.png" alt-text="Beispiel zeigt, wie die Registerkarte in der Besprechung scrollt." border="false":::

### <a name="navigation"></a>Navigation

Für Szenarien mit Navigationsebenen oder hohen Inhalten wird empfohlen, Benutzern die Navigation zu einer sekundären Ebene zu ermöglichen. Benutzer müssen zur vorherigen Ebene zurück wechseln können.

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav.png" alt-text="Beispiel zeigt die Navigation in Besprechungen." border="false":::

## <a name="use-an-in-meeting-dialog"></a>Verwenden eines Besprechungsdialogfelds

Dialoge in Besprechungen werden auf der Besprechungsphase von Teams angezeigt. Sie erfordern die Aufmerksamkeit, Bestätigung oder Interaktion eines Benutzers, sind aber dezent und unterbrechen die Besprechung nicht. Sie sollten diese sparsam und für Szenarien verwenden, die einfach und aufgabenorientiert sind.

### <a name="use-cases"></a>Anwendungsfälle

Dialogfelder in Besprechungen werden von einem Benutzer (z. B. dem Besprechungsorganisator) ausgelöst, der die Teilnehmer möglicherweise zu den:

* Bereitstellen von kurzem Feedback
* Nehmen Sie eine kurze Umfrage oder Umfrage vor.
* Übermitteln von Genehmigungen
* Erinnerungen erhalten

:::image type="content" source="../../assets/images/apps-in-meetings/use-in-meeting-dialog.png" alt-text="Im Beispiel wird gezeigt, wie Sie ein Dialogfeld in Besprechungen verwenden können." border="false":::

### <a name="anatomy-in-meeting-dialog"></a>Aufbau: Dialogfeld "In-Meeting"

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-anatomy.png" alt-text="Das Beispiel zeigt die strukturell anatomische Struktur eines Dialogfelds in der Besprechung." border="false":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|1|**Header:** Enthält App-Symbol, -Name, Aktionszeichenfolge und Schließen-Symbol.|
|2 |**iframe**: Zeigt Ihre App-Inhalte an.|

### <a name="anatomy-in-meeting-dialog-header"></a>Aufbau: Kopfzeile des Dialogfelds "In-Meeting"

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-header-anatomy.png" alt-text="Das Beispiel zeigt die strukturell angepasste Struktur eines Dialogkopfs in besprechungsind." border="false":::

Es gibt zwei Kopfzeilenvarianten. Verwenden Sie nach Möglichkeit die Variante mit dem Avatar, um zu verstärken, dass das Dialogfeld von einer Person kommt.

|Leistungsindikator|Beschreibung|
|----------|-----------|
|1|**Avatar:** Person, die das Dialogfeld in der Besprechung initiiert.|
|2 |**Symbol "App"**|
|3|**App-Name**|
|4 |**Schaltfläche "Schließen":** Schließt das Dialogfeld.|
|5 |**Aktionszeichenfolge:** In der Regel wird beschrieben, wer das Dialogfeld initiiert hat.|

### <a name="responsive-behavior"></a>Dynamisches Verhalten

Dialoge in Besprechungen können je nach Größe variieren, um unterschiedliche Szenarien zu berücksichtigen. Achten Sie darauf, abstands- und komponentengrößen zu verwalten.

* **Breite:** Die Breite des iframe ist ein absoluter Wert innerhalb des angegebenen Bereichs.
* **Höhe:** Die Höhe des Dialogfelds wird durch den Inhalt im iframe bestimmt. Der vertikale Bildlauf übernimmt den Inhalt, der die maximale Höhe überschreitet.

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-responsive.png" alt-text="Das Beispiel zeigt das Dialogfeld &quot;In-Meeting&quot;. Breite: Min--280 Pixel (248 Pixel iframe). Max- 460 Pixel (428 Pixel iframe). Höhe: 300 Pixel (iframe)." border="false":::

## <a name="after-a-meeting"></a>Nach einer Besprechung

Sie können zu einer Besprechung zurück wechseln, nachdem sie beendet wurde, und den Inhalt der App anzeigen. In diesem Beispiel kann der Besprechungsorganisator die Umfrageergebnisse auf der Registerkarte **"Contoso"** anzeigen. (Hinweis: Aus Entwurfs sicht gibt es keinen Unterschied zwischen der Registerkartenerfahrung vor und nach der Besprechung.)

:::image type="content" source="../../assets/images/apps-in-meetings/post-meeting-experience.png" alt-text="Beispiel zeigt eine Registerkarte nach der Besprechung." border="false":::

## <a name="best-practices"></a>Bewährte Methoden

### <a name="interactions"></a>Interaktionen

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/interaction-do.png" alt-text="Beispiel, in dem gezeigt wird, wie die Anzahl der Interaktionen begrenzt wird." border="false":::

#### <a name="do-limit-the-number-of-interactions"></a>Do: Limit the number of interactions

Entfernen Sie in Besprechungsdialogfeldern nicht benötigte Inhalte, die Benutzern nicht helfen, schnell etwas zu erreichen.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/interaction-dont.png" alt-text="Beispiel, in dem gezeigt wird, wie sie keine unnötigen Elemente einführen." border="false":::

#### <a name="dont-introduce-unnecessary-elements"></a>Nicht erforderlich: Unnötige Elemente einführen

Ein einzelnes Besprechungsdialogfeld mit mehreren Interaktionen kann vom Anruf ablenken.

   :::column-end:::
:::row-end:::

### <a name="layout"></a>Layout

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-layout-do.png" alt-text="Beispiel für die Verwendung eines Einspaltendialogfelds." border="false":::

#### <a name="do-use-a-single-column-dialog-layout"></a>Do: Use a single-column dialog layout

Da die Dialogfelder im Mittelpunkt der Besprechungsphase stehen, sollte der Aufgabenabschluss schnell und einfach sein, um Frustration der Benutzer zu vermeiden.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-layout-dont.png" alt-text="Beispiel, in dem gezeigt wird, dass Sie den Platz einer Besprechungserweiterung nicht überladen sollten." border="false":::

#### <a name="dont-clutter-the-space"></a>Nicht zu vergessen: Überladen des Leerzeichens

Dichte oder zu strukturierte Inhalte können ablenkend und überwältigend sein, insbesondere während einer Besprechung.

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-layout-do.png" alt-text="Beispiel für ein Einspalten-Registerkartenlayout." border="false":::

#### <a name="do-use-a-single-column-tab-layout"></a>Verwenden eines einspaltig angezeigten Registerkartenlayouts

Aufgrund der schmalen Art der Registerkarte in der Besprechung wird dringend empfohlen, den Inhalt in einer einzelnen Spalte anzuzeigen.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-layout-dont.png" alt-text="Beispiel für eine Registerkarte mit mehreren Spalten." border="false":::

#### <a name="dont-use-multiple-columns"></a>Nicht zu verwenden: Verwenden mehrerer Spalten

Aufgrund des begrenzten Speicherplatzes auf der Registerkarte "Besprechung" werden Layouts mit mehr als einer Spalte nicht empfohlen.

   :::column-end:::
:::row-end:::

### <a name="controls"></a>Steuerelemente

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-controls-do.png" alt-text="Beispiel, in dem gezeigt wird, wie primäre Steuerelemente rechts ausgerichtet werden." border="false":::

#### <a name="do-right-align-the-primary-action"></a>Do: Right align the primary action

Es wird empfohlen, die visuell schwierigste Aktion am rechten Ort zu positionieren.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-controls-dont.png" alt-text="Beispiel, in dem gezeigt wird, wie primäre Steuerelemente nicht linksb ausgerichtet werden sollen." border="false":::

#### <a name="dont-left-or-center-align-actions"></a>Nicht zu verwenden: Links- oder zentriert ausgerichtete Aktionen

Dies weicht vom standardmäßigen Teams-Muster für die Steuerelementplatzierung in einem Dialogfeld ab und kann mit einem Dialogfeld hinter dem oberen Dialogfeld in Konflikt stehen.

   :::column-end:::
:::row-end:::

### <a name="scroll"></a>Bildlauf

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-scroll-do.png" alt-text="Beispiel für einen vertikalen Bildlauf auf einer Registerkarte in Besprechungen." border="false":::

#### <a name="do-scroll-vertically"></a>Do: Scroll vertically

Benutzer erwarten vertikales Scrollen in Teams (und an anderer Stelle).

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-scroll-dont.png" alt-text="Beispiel für einen horizontalen Bildlauf auf einer Registerkarte in einer Besprechung." border="false":::

#### <a name="dont-scroll-horizontally"></a>Nicht: Horizontaler Bildlauf

Horizontales Scrollen ist in Teams kein erwartetes Verhalten. Andere Zeichenblätter in der Besprechungsumgebung scrollen vertikal.

   :::column-end:::
:::row-end:::

### <a name="workflows"></a>Workflows

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-workflow-do.png" alt-text="Beispiel für ein komplexes Szenario auf einer Registerkarte in einer Besprechung." border="false":::

#### <a name="do-surface-complex-scenarios-in-the-in-meeting-tab"></a>Do: Surface complex scenarios in the in-meeting tab

Wenn Ihre App mehrere Aufgaben umfasst, wird dringend empfohlen, eine Registerkarte in Besprechungen mit einem layout mit einer Spalte zu verwenden.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-workflow-dont.png" alt-text="Beispiel für komplexe Szenarien in einem Besprechungsdialogfeld." border="false":::

#### <a name="dont-make-in-meeting-dialogs-complex"></a>Nicht zu verwenden: Dialoge in Besprechungen komplex machen

Dialoge in Besprechungen sind für kurze Interaktionen vorgesehen.

   :::column-end:::
:::row-end:::

### <a name="theming"></a>Designs

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-theming-do.png" alt-text="Beispiel für eine Besprechungserweiterung mit dunklem Design." border="false":::

#### <a name="do-use-teams-color-tokens"></a>Verwenden von Teams-Farbtoken

Teams-Besprechungen sind für den dunklen Modus optimiert, um visuelle und kognitive Rauschgeräusche zu reduzieren, damit benutzer sich auf die Diskussion und freigegebene Inhalte konzentrieren können. Erfahren Sie mehr über <a href="https://fluentsite.z22.web.core.windows.net/0.51.3/colors#color-scheme" target="_blank">die Verwendung von Farbtoken (Fluent UI)</a>.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-theming-dont.png" alt-text="Beispiel für eine Besprechungserweiterung mit einem (hellen) Standarddesign." border="false":::

#### <a name="dont-hard-code-hex-values"></a>Nicht zu beachten: Hartcode-Hexadezimalwerte

Wenn Sie keine Farbtoken von Teams verwenden, sind Ihre Designs weniger skalierbar und nehmen mehr Zeit in Die Verwaltung.

   :::column-end:::
:::row-end:::

### <a name="navigation"></a>Navigation

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav-do.png" alt-text="Beispiel für eine Besprechungserweiterung mit einer Schaltfläche &quot;Zurück&quot;." border="false":::

#### <a name="do-have-a-back-button"></a>Do: Have a Back button

Wenn sie auf einer Registerkarte in Besprechungen mehrere Navigationsebenen haben, müssen Benutzer wieder zu ihren vorherigen Ansichten wechseln können.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav-dont.png" alt-text="Beispiel für eine Besprechungserweiterung mit zwei Schaltflächen zum Schließen." border="false":::

#### <a name="dont-include-another-dismiss-button"></a>Don't: Include another dismiss button

Das Bereitstellen einer Option zum Schließen von Registerkarteninhalten in Besprechungen kann Probleme verursachen, da bereits eine Schaltfläche in der Kopfzeile vorhanden ist, um die Registerkarte in der Besprechung selbst zu schließen.

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav-caution.png" alt-text="Beispiel mit modalen Modalitäten (oder Aufgabenmodulen) auf einer Registerkarte für Besprechungen." border="false":::

#### <a name="caution-avoid-modals-within-the-in-meeting-tab"></a>Achtung: Vermeiden Sie Modalitäten auf der Registerkarte "Besprechung".

Modale Modalitäten (auch als Aufgabenmodule bezeichnet) auf der bereits schmalen Registerkarte für Besprechungen können den Inhalt umschließen und verfemen.

   :::column-end:::
:::row-end:::

## <a name="validate-your-design"></a>Überprüfen Des Designs

Wenn Sie Ihre App in AppSource veröffentlichen möchten, sollten Sie die Designprobleme verstehen, die häufig dazu führen, dass Apps während der Übermittlung fehlschlagen.

> [!div class="nextstepaction"]
> [Überprüfen der Entwurfsüberprüfungsrichtlinien](../../concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md#validation-guidelines--most-failed-test-cases)
