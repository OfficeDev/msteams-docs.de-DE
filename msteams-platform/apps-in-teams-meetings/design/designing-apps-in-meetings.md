---
title: Entwerfen der Besprechungserweiterung
author: heath-hamilton
description: Erfahren Sie, wie Sie Apps in Teams entwerfen und das Microsoft Teams UI Kit erhalten.
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
# <a name="designing-your-microsoft-teams-meeting-extension"></a>Entwerfen ihrer Microsoft Teams Besprechungserweiterung

Sie können Apps erstellen, um Besprechungen produktiver zu gestalten. Bitten Sie z. B. Personen, während eines Anrufs eine Umfrage zu führen, oder senden Sie eine kurze Erinnerung, die den Ablauf der Besprechung nicht unterbricht.

## <a name="microsoft-teams-ui-kit"></a>Microsoft Teams-UI-Kit

Umfassendere Entwurfsrichtlinien, einschließlich Elemente, die Sie bei Bedarf packen und ändern können, finden Sie im Microsoft Teams UI Kit.

> [!div class="nextstepaction"]
> [Holen Sie sich das Microsoft Teams-UI-Kit (Figma)](https://www.figma.com/community/file/916836509871353159)

## <a name="add-a-meeting-extension"></a>Hinzufügen einer Besprechungserweiterung

Sie können eine Besprechungserweiterung vor und während Besprechungen hinzufügen. Sie können auch eine App für eine bestimmte Besprechung direkt aus dem Teams (AppSource) hinzufügen.

### <a name="add-before-a-meeting"></a>Hinzufügen vor einer Besprechung

Wählen Sie in den Besprechungsdetails **Registerkarte hinzufügen +** aus, um das App-Flyout zu öffnen und apps zu finden, die für Besprechungen optimiert sind.

:::image type="content" source="../../assets/images/apps-in-meetings/add-before-meeting.png" alt-text="Beispiel zeigt, wie Sie eine Besprechungserweiterung vor einer Besprechung hinzufügen." border="false":::

### <a name="add-during-a-meeting"></a>Hinzufügen während einer Besprechung

Wählen Sie in einer Besprechung **weitere App** :::image type="icon" source="../../assets/icons/teams-client-more.png":::  >  **hinzufügen aus,** und wählen Sie die app aus, die Sie möchten.

:::image type="content" source="../../assets/images/apps-in-meetings/add-during-meeting.png" alt-text="Beispiel zeigt, wie Sie während einer Besprechung eine Besprechungserweiterung hinzufügen." border="false":::

## <a name="before-a-meeting"></a>Vor einer Besprechung

Vor Ihrer Besprechung können Sie Inhalte auf der Registerkarte hinzufügen. Das folgende Beispiel zeigt eine Entwurfsfrage, die während des Anrufs beantwortet wird.

:::image type="content" source="../../assets/images/apps-in-meetings/before-meeting-tab.png" alt-text="Beispiel zeigt, wie Inhalte in den Besprechungsdetails vor einem Anruf app-App." border="false":::

### <a name="anatomy-meeting-tab-before-and-after-meetings"></a>Anatomie: Registerkarte Besprechung (vor und nach Besprechungen)

:::image type="content" source="../../assets/images/apps-in-meetings/meeting-details-tab-anatomy.png" alt-text="Beispiel zeigt die Strukturanatomie einer Besprechungsregisterkarte vor und nach einer Besprechung." border="false":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|1|**Registerkartenname:** Navigationsbezeichnung für Ihre Registerkarte.|
|2|**Registerkartenüberlauf**: Öffnet Registerkartenaktionen, z. B. Umbenennen und Entfernen.|
|3|**iframe**: Zeigt Ihre App-Inhalte an.|

### <a name="designing-with-ui-templates"></a>Entwerfen mit Benutzeroberflächenvorlagen

Verwenden Sie eine der folgenden Teams-UI-Vorlagen, um Die Besprechungsregisterkarte zu entwerfen:

* [Liste](../../concepts/design/design-teams-app-ui-templates.md#list): Listen können verwandte Elemente in einem scannierbaren Format anzeigen und Benutzern das Ausführen von Aktionen für eine gesamte Liste oder einzelne Elemente ermöglichen.
* [Task board:](../../concepts/design/design-teams-app-ui-templates.md#task-board)Ein Task Board, manchmal auch als Kanbanboard oder Schwimmstreifen bezeichnet, ist eine Sammlung von Karten, die häufig zum Nachverfolgen des Status von Arbeitselementen oder Tickets verwendet werden.
* [Dashboard:](../../concepts/design/design-teams-app-ui-templates.md#dashboard)Ein Dashboard ist ein Canvas mit mehreren Karten, die eine Übersicht über Daten oder Inhalte bieten.
* [Formular](../../concepts/design/design-teams-app-ui-templates.md#form): Formulare sind für die strukturierte Erfassung, Validierung und Übermittlung von Benutzereingaben.
* [Leerer](../../concepts/design/design-teams-app-ui-templates.md#empty-state)Zustand: Die Vorlage für den leeren Zustand kann für viele Szenarien verwendet werden, z. B. für die Anmeldung, die Erstlauferfahrung, Fehlermeldungen und vieles mehr.
* [Linkes](../../concepts/design/design-teams-app-ui-templates.md#left-nav)Navigationsmenü: Die linke Navigationsvorlage kann hilfreich sein, wenn Ihre Registerkarte eine Navigation erfordert. Im Allgemeinen sollten Sie die Registerkartennavigation auf ein Minimum beschränken.

## <a name="use-an-in-meeting-tab"></a>Verwenden einer Registerkarte in Besprechungen

Die Registerkarte "In-Meeting" ist ein Zeichenbereich für die Erweiterung der Zusammenarbeit in Besprechungen. Teilnehmer können app-Inhalte in einem dedizierten Bereich außerhalb der Besprechungsphase über freigegebene oder rollenbasierte Ansichten anzeigen und mit ihnen interagieren.

### <a name="use-cases"></a>Anwendungsfälle

Personen können die Registerkarte "In-Meeting" verwenden, um:

* Geben Sie ausführliches Feedback. Bewerten Sie beispielsweise einen Stellenkandidaten.
* Erstellen Sie eine Umfrage, eine Umfrage oder ein Aufgabenelement für die Besprechungsteilnehmer.
* Anzeigen von Notizen, die für die Besprechung relevant sind. Beispielsweise Informationen zu einem Vertriebsleiter.

:::image type="content" source="../../assets/images/apps-in-meetings/use-in-meeting-tab.png" alt-text="Ein Beispiel zeigt, wie Sie Umfrageinhalte auf einer Registerkarte in besprechungen präsentieren können." border="false":::

### <a name="anatomy-in-meeting-tab"></a>Anatomie: Registerkarte "In-Meeting"

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-anatomy.png" alt-text="Beispiel zeigt die Strukturanatomie einer Registerkarte in Besprechungen." border="false":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|1|**App-Symbol (ausgewählt):** 16 Pixel transparentes App-Logo.|
|2|**App-Name**|
|3|**Header**: Enthält Ihren App-Namen.|
|4 |**Schaltfläche Schließen**: Schließt die Registerkarte. Verwenden Sie immer das schließende Symbol oben rechts anstelle einer Aktion in der Fußzeile.|
|5 |**Benachrichtigungsleiste**: Fehlerwarnungen werden direkt unterhalb der Kopfzeile angezeigt, und der iframe-Inhalt wird um 20 Pixel nach unten geschoben.|
|6 |**iframe**: Zeigt Ihre App-Inhalte an.|

### <a name="spacing"></a>Abstand

Optimieren Sie ihre Registerkarte in Besprechungen so, dass sie in den 280 Pixel breiten iframe-Bereich passt. Es gibt 20 Pixel Abstand auf der linken und rechten Seite des iframes und zwischen der Registerkartenkopfzeile. Der iframe wird bis zum unteren Rand der Registerkarte vollständig ausblutet.

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-spacing.png" alt-text="Beispiel zeigt Die Größe der Registerkartenabstände in Besprechungen." border="false":::

### <a name="scrolling"></a>Bildlauf

Der Iframeinhalt sollte vertikal gescrollt werden. Sie können nur den Inhalt sehen, zu dem Sie einen Bildlauf durchgeführt haben (nichts oben oder unten). Die Bildlaufleiste ist Teil des iframe-Inhalts.

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-scrolling.png" alt-text="Beispiel zeigt, wie die Registerkarte in Besprechungen scrollt." border="false":::

### <a name="navigation"></a>Navigation

Für Szenarien mit Navigationsebenen oder hohen Inhalten wird empfohlen, benutzern die Navigation zu einer sekundären Ebene zu ermöglichen. Benutzer müssen wieder zur vorherigen Ebene wechseln können.

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav.png" alt-text="Beispiel zeigt die Navigation in Besprechungen." border="false":::

## <a name="use-an-in-meeting-dialog"></a>Verwenden eines Besprechungsdialogfelds

Besprechungsdialogfelder werden in der Teams angezeigt. Sie erfordern die Aufmerksamkeit, Bestätigung oder Interaktion eines Benutzers, sind jedoch subtil und unterbrechen die Besprechung nicht. Sie sollten diese sparsam und für Szenarien verwenden, die leicht und aufgabenorientiert sind.

### <a name="use-cases"></a>Anwendungsfälle

Dialoge in Besprechungen werden von einem Benutzer (z. B. dem Besprechungsorganisator) ausgelöst, der die Teilnehmer möglicherweise wie folgt verwenden möchte:

* Kurzes Feedback
* Eine kurze Umfrage oder Umfrage
* Übermitteln von Genehmigungen
* Erinnerungen erhalten

:::image type="content" source="../../assets/images/apps-in-meetings/use-in-meeting-dialog.png" alt-text="Beispiel zeigt, wie Sie ein Besprechungsdialogfeld verwenden können." border="false":::

### <a name="anatomy-in-meeting-dialog"></a>Anatomie: Dialogfeld "In-Meeting"

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-anatomy.png" alt-text="Beispiel zeigt die Strukturanatomie eines Besprechungsdialogfelds." border="false":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|1|**Header**: Enthält App-Symbol, Name, Aktionszeichenfolge und Schließen-Symbol.|
|2|**iframe**: Zeigt Ihre App-Inhalte an.|

### <a name="anatomy-in-meeting-dialog-header"></a>Anatomie: In-Meeting-Dialogkopfzeile

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-header-anatomy.png" alt-text="Beispiel zeigt die Strukturanatomie eines Besprechungsdialogkopfs." border="false":::

Es gibt zwei Kopfzeilenvarianten. Verwenden Sie nach Möglichkeit die Variante mit dem Avatar, um zu verstärken, dass das Dialogfeld von einer Person kommt.

|Leistungsindikator|Beschreibung|
|----------|-----------|
|1|**Avatar**: Person, die das Dialogfeld in der Besprechung initiiert.|
|2|**App-Symbol**|
|3|**App-Name**|
|4 |**Schaltfläche Schließen**: Schließt das Dialogfeld.|
|5 |**Aktionszeichenfolge**: In der Regel wird beschrieben, wer das Dialogfeld initiiert hat.|

### <a name="responsive-behavior"></a>Dynamisches Verhalten

Besprechungsdialogfelder können in der Größe variieren, um unterschiedliche Szenarien zu berücksichtigen. Achten Sie darauf, abstands- und komponentengrößen zu erhalten.

* **Width**: Sie können die Breite des iframe des Dialogfelds an einer beliebigen Stelle innerhalb des unterstützten Größenbereichs angeben.
* **Height**: Sie können die Höhe des iframe des Dialogfelds an einer beliebigen Stelle innerhalb des unterstützten Größenbereichs angeben. Sie können Benutzern auch erlauben, vertikal zu scrollen, wenn Ihre App-Inhalte die maximale Höhe überschreitet.

Geben Sie zum Implementieren die Breite und Höhe mithilfe des Schlüssels [`externalResourceUrl`](~/apps-in-teams-meetings/create-apps-for-teams-meetings.md#notificationsignal-api) an.

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-responsive.png" alt-text="Beispiel zeigt das Dialogfeld in der Besprechung. Breite: Min--280 Pixel (248 Pixel iframe). Max.-460 Pixel (428 Pixel iframe). Höhe: 300 Pixel (iframe)." border="false":::

## <a name="after-a-meeting"></a>Nach einer Besprechung

Sie können nach dem Ende zu einer Besprechung wechseln und App-Inhalte anzeigen. In diesem Beispiel kann der Besprechungsorganisator die Umfrageergebnisse auf der Registerkarte **Contoso** anzeigen. (Hinweis: Aus Entwurfs sicht gibt es keinen Unterschied zwischen der Registerkartenerfahrung vor und nach der Besprechung.)

:::image type="content" source="../../assets/images/apps-in-meetings/post-meeting-experience.png" alt-text="Die Beispielillustration zeigt eine Registerkarte nach der Besprechung." border="false":::

## <a name="best-practices"></a>Bewährte Methoden

Verwenden Sie diese Empfehlungen, um eine hochwertige App-Erfahrung zu erstellen.

### <a name="interactions"></a>Interaktionen

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/interaction-do.png" alt-text="Beispiel zum Einschränken der Anzahl von Interaktionen." border="false":::

#### <a name="do-limit-the-number-of-interactions"></a>Do: Beschränken der Anzahl von Interaktionen

Entfernen Sie in Besprechungsdialogfeldern unnötige Inhalte, die Benutzern nicht helfen, schnell etwas zu erreichen.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/interaction-dont.png" alt-text="Beispiel, in dem gezeigt wird, wie sie keine unnötigen Elemente einführen." border="false":::

#### <a name="dont-introduce-unnecessary-elements"></a>Don't: Einführung unnötiger Elemente

Ein einzelnes Besprechungsdialogfeld mit mehreren Interaktionen kann vom Anruf ablenken.

   :::column-end:::
:::row-end:::

### <a name="layout"></a>Layout

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-layout-do.png" alt-text="Beispiel für die Verwendung eines Einspaltendialogfelds." border="false":::

#### <a name="do-use-a-single-column-dialog-layout"></a>Do: Verwenden eines einspaltig geöffneten Dialogfeldlayouts

Da die Dialoge im Mittelpunkt der Besprechungsphase stehen, sollte der Aufgabenabschluss schnell und einfach sein, um Frust der Benutzer zu vermeiden.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-layout-dont.png" alt-text="Beispiel: Sie sollten den Raum einer Besprechungserweiterung nicht überladen." border="false":::

#### <a name="dont-clutter-the-space"></a>Don't: Clutter the space

Dichte oder überstrukturierte Inhalte können ablenkend und überwältigend sein, insbesondere während einer Besprechung.

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-layout-do.png" alt-text="Beispiel für ein Einspaltenregisterkartenlayout." border="false":::

#### <a name="do-use-a-single-column-tab-layout"></a>Do: Verwenden eines einspaltig geöffneten Registerkartenlayouts

Aufgrund des schmalen Charakters der Registerkarte in der Besprechung wird dringend empfohlen, den Inhalt in einer einzelnen Spalte anzuzeigen.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-layout-dont.png" alt-text="Beispiel für eine Registerkarte mit mehreren Spalten." border="false":::

#### <a name="dont-use-multiple-columns"></a>Don't: Verwenden mehrerer Spalten

Aufgrund des begrenzten Speicherplatzes der Registerkarte "Besprechung" werden Layouts mit mehr als einer Spalte nicht empfohlen.

   :::column-end:::
:::row-end:::

### <a name="controls"></a>Steuerelemente

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-controls-do.png" alt-text="Beispiel, in dem gezeigt wird, wie primäre Steuerelemente rechts ausgerichtet werden." border="false":::

#### <a name="do-right-align-the-primary-action"></a>Do: Rechte Ausrichtung der primären Aktion

Es wird empfohlen, die visuell schwerste Aktion am rechten Ort zu positionieren.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-controls-dont.png" alt-text="Beispiel, in dem gezeigt wird, wie Sie primäre Steuerelemente nicht ausrichten sollten." border="false":::

#### <a name="dont-left-or-center-align-actions"></a>Don't: Aktionen links oder zentriert ausrichten

Dies weicht vom Standardmuster Teams für die Platzierung von Steuerelementen in einem Dialogfeld ab und kann mit einem Dialogfeld hinter dem oberen Dialogfeld in Konflikt stehen.

   :::column-end:::
:::row-end:::

### <a name="scroll"></a>Bildlauf

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-scroll-do.png" alt-text="Beispiel für vertikalen Bildlauf auf einer Registerkarte in Besprechungen." border="false":::

#### <a name="do-scroll-vertically"></a>Do: Vertikal scrollen

Benutzer erwarten vertikalen Bildlauf in Teams (und an anderer Stelle).

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-scroll-dont.png" alt-text="Beispiel für einen horizontalen Bildlauf auf einer Registerkarte in Besprechungen." border="false":::

#### <a name="dont-scroll-horizontally"></a>Don't: Horizontal scrollen

Horizontaler Bildlauf ist kein erwartetes Verhalten in Teams. Andere Canvases in der Besprechungsumgebung scrollen vertikal.

   :::column-end:::
:::row-end:::

### <a name="workflows"></a>Workflows

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-workflow-do.png" alt-text="Beispiel für ein komplexes Szenario auf einer Registerkarte in Besprechungen." border="false":::

#### <a name="do-surface-complex-scenarios-in-the-in-meeting-tab"></a>Do: Komplexe Szenarien auf der Registerkarte Besprechungsoberfläche

Wenn Ihre App mehrere Aufgaben umfasst, wird dringend empfohlen, eine Registerkarte in Besprechungen mit einem Layout mit einer einzelnen Spalte zu verwenden.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-workflow-dont.png" alt-text="Beispiel für komplexe Szenarien in einem Besprechungsdialogfeld." border="false":::

#### <a name="dont-make-in-meeting-dialogs-complex"></a>Don't: In-Meeting-Dialoge komplex machen

Besprechungsdialogfelder sind für kurze Interaktionen vorgesehen.

   :::column-end:::
:::row-end:::

### <a name="theming"></a>Designs

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-theming-do.png" alt-text="Beispiel für eine Besprechungserweiterung mit dem dunklen Design." border="false":::

#### <a name="do-use-teams-color-tokens"></a>Do: Verwenden Teams Farbtoken

Teams Besprechungen sind für den dunklen Modus optimiert, um visuelles und kognitives Rauschen zu reduzieren, damit benutzer sich auf die Diskussion und freigegebene Inhalte konzentrieren können. Erfahren Sie mehr <a href="https://fluentsite.z22.web.core.windows.net/0.51.3/colors#color-scheme" target="_blank">über die Verwendung von Farbtoken (Fluent UI).</a>

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-theming-dont.png" alt-text="Beispiel für eine Besprechungserweiterung mit einem (hellen) Standarddesign." border="false":::

#### <a name="dont-hard-code-hex-values"></a>Don't: Hexwerte für Hartcode

Wenn Sie keine Teams verwenden, sind Ihre Designs weniger skalierbar und nehmen sich mehr Zeit für die Verwaltung.

   :::column-end:::
:::row-end:::

### <a name="navigation"></a>Navigation

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav-do.png" alt-text="Beispiel für eine Besprechungserweiterung mit einer Schaltfläche &quot;Zurück&quot;." border="false":::

#### <a name="do-have-a-back-button"></a>Do: Have a back button

Wenn sie mehr als eine Navigationsebene auf einer Registerkarte in Besprechungen haben, müssen Benutzer wieder zu ihren vorherigen Ansichten wechseln können.

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
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav-caution.png" alt-text="Beispiel für modale (oder Aufgabenmodule) innerhalb einer Registerkarte in Besprechungen." border="false":::

#### <a name="caution-avoid-modals-within-the-in-meeting-tab"></a>Vorsicht: Vermeiden von Modalen auf der Registerkarte "Besprechung"

Modale (auch als Aufgabenmodule bezeichnet) auf der bereits schmalen Registerkarte in Besprechungen können den Inhalt umschließen und verhüllen.

   :::column-end:::
:::row-end:::
