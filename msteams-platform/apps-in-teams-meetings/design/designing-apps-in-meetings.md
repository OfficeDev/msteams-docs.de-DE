---
title: Entwerfen Ihrer Besprechungs Erweiterung
author: heath-hamilton
description: Hier erfahren Sie, wie Sie apps in Microsoft Teams-Besprechungen entwerfen und das Microsoft Teams UI Kit abrufen.
ms.author: lajanuar
ms.topic: conceptual
ms.openlocfilehash: 3d18895626d5f2846d10e7145a622834d82b2e98
ms.sourcegitcommit: c102da958759c13aa9e0f81bde1cffb34a8bef34
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/09/2020
ms.locfileid: "49606132"
---
# <a name="designing-your-microsoft-teams-meeting-extension"></a>Entwerfen Ihrer Microsoft Teams-Besprechungs Erweiterung

Sie können Apps erstellen, um Besprechungen produktiver zu gestalten. Bitten Sie beispielsweise die Personen, während eines Anrufs eine Umfrage abzuschließen oder eine schnell Erinnerung zu senden, die den Ablauf der Besprechung nicht unterbricht.

## <a name="microsoft-teams-ui-kit"></a>Microsoft Teams-UI-Kit

Ausführlichere Entwurfsrichtlinien, einschließlich der Elemente, die Sie nach Bedarf abrufen und ändern können, finden Sie im Microsoft Teams UI Kit.

> [!div class="nextstepaction"]
> [Abrufen des Microsoft Teams UI Kit (Figma)](https://www.figma.com/community/file/916836509871353159)

## <a name="add-a-meeting-extension"></a>Hinzufügen einer Besprechungs Erweiterung

Sie können vor und während Besprechungen eine Besprechungs Erweiterung hinzufügen. Sie können auch eine APP für eine bestimmte Besprechung direkt aus dem Microsoft Teams Store (AppSource).

### <a name="add-before-a-meeting"></a>Vor einer Besprechung hinzufügen

Wählen Sie vor einer Besprechung die Option **Add a Tab +** aus, um das App-Flyout zu öffnen und für Besprechungen optimierte apps zu finden.

:::image type="content" source="../../assets/images/apps-in-meetings/add-before-meeting.png" alt-text="Beispiel zeigt, wie eine Besprechungs Erweiterung vor einer Besprechung hinzugefügt wird." border="false":::

### <a name="add-during-a-meeting"></a>Während einer Besprechung hinzufügen

Wählen Sie in einer Besprechung **Weitere** :::image type="icon" source="../../assets/icons/teams-client-more.png":::  >  **app hinzufügen** aus, und wählen Sie die gewünschte App aus.

:::image type="content" source="../../assets/images/apps-in-meetings/add-during-meeting.png" alt-text="In diesem Beispiel wird gezeigt, wie während einer Besprechung eine Besprechungs Erweiterung hinzugefügt wird." border="false":::

## <a name="before-a-meeting"></a>Vor einer Besprechung

Sie können vor Ihrer Besprechung Inhalte auf der Registerkarte hinzufügen. Das folgende Beispiel zeigt eine Entwurfs Frage für Umfragen, die von Personen während des Anrufs beantwortet werden.

:::image type="content" source="../../assets/images/apps-in-meetings/before-meeting-tab.png" alt-text="Beispiel zeigt, wie der Inhalt der Besprechungsdetails vor einem Anruf App-Inhalte enthält." border="false":::

### <a name="anatomy-meeting-tab-before-and-after-meetings"></a>Anatomie: Registerkarte "Besprechung" (vor und nach Besprechungen)

:::image type="content" source="../../assets/images/apps-in-meetings/meeting-details-tab-anatomy.png" alt-text="Beispiel zeigt die strukturelle Anatomie einer Besprechungs Registerkarte vor und nach einer Besprechung." border="false":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|1|**Tab Name**: Navigations Bezeichnung für die Registerkarte.|
|2 |**Registerkarten Überlauf**: Öffnet Registerkarten Aktionen wie umbenennen und entfernen.|
|3 |**iframe**: zeigt den App-Inhalt an.|

### <a name="designing-with-ui-templates"></a>Entwerfen mit Benutzeroberflächenvorlagen

Verwenden Sie eine der folgenden Teams-Benutzeroberflächenvorlagen, um die Gestaltung ihrer Besprechungs Registerkarte zu unterstützen:

* [List](../../concepts/design/design-teams-app-ui-templates.md#list): Listen können verwandte Elemente in einem scannable-Format anzeigen und Benutzern das Ausführen von Aktionen für eine gesamte Liste oder einzelne Elemente gestatten.
* [Task Board](../../concepts/design/design-teams-app-ui-templates.md#task-board): ein Aufgaben Gremium, das manchmal als Kanban-Board oder als Swim Lanes bezeichnet wird, ist eine Sammlung von Karten, die häufig zum Nachverfolgen des Status von Arbeitsaufgaben oder Tickets verwendet werden.
* [Dashboard](../../concepts/design/design-teams-app-ui-templates.md#dashboard): ein Dashboard ist eine Leinwand mit mehreren Karten, die eine Übersicht über Daten oder Inhalte bieten.
* [Formular](../../concepts/design/design-teams-app-ui-templates.md#form): Formulare dienen zum Sammeln, validieren und Übermitteln von Benutzereingaben in strukturierter Form.
* [Leer State](../../concepts/design/design-teams-app-ui-templates.md#empty-state): die leere Statusvorlage kann für viele Szenarien verwendet werden, einschließlich Anmeldung, Erstausführung, Fehlermeldungen und mehr.
* [Linker NAV](../../concepts/design/design-teams-app-ui-templates.md#left-nav): die linke Navigationsvorlage kann hilfreich sein, wenn Ihre Registerkarte eine Navigation erfordert. Im Allgemeinen sollten Sie die Registerkartennavigation auf ein Minimum beschränken.

## <a name="use-an-in-meeting-tab"></a>Verwenden einer in-Meeting-Registerkarte

Die Registerkarte in-Meeting ist eine Arbeitsfläche zum Erweitern der Zusammenarbeit während Besprechungen. Teilnehmer können App-Inhalte in einem dedizierten Bereich außerhalb der Besprechungs Phase über freigegebene oder rollenbasierte Ansichten anzeigen und mit ihnen interagieren.

### <a name="use-cases"></a>Anwendungsfälle

Die Registerkarte "in-Meeting" wird von den Benutzern möglicherweise verwendet:

* Bereitstellen eines detaillierten Feedbacks (zum Beispiel Auswerten eines Bewerbers)
* Schnelles Erstellen einer Umfrage, Umfrage oder eines Aufgabenelements für die Besprechungsteilnehmer
* Anzeigen von Notizen, die für die Besprechung relevant sind (beispielsweise Informationen zu einem Verkaufsleiter)

:::image type="content" source="../../assets/images/apps-in-meetings/use-in-meeting-tab.png" alt-text="Beispiel zeigt, wie Sie Abstimmungs Inhalte auf einer Registerkarte in der Besprechung präsentieren können." border="false":::

### <a name="anatomy-in-meeting-tab"></a>Anatomie: Registerkarte "in der Besprechung"

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-anatomy.png" alt-text="Beispiel zeigt die strukturelle Anatomie einer in-Meeting-Registerkarte." border="false":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|1|**App-Symbol (ausgewählt)**: transparentes 16-Pixel-App-Logo.|
|2 |**App-Name**|
|3 |**Kopfzeile**: enthält Ihren APP-Namen.|
|4 |**Schließen (Schaltfläche**): die Registerkarte wird verworfen. Verwenden Sie immer das obere rechte Schließsymbol anstelle einer Aktion in der Fußzeile.|
|5 |**Benachrichtigungsleiste**: Fehlermeldungen werden direkt unterhalb der Kopfzeile angezeigt, und der iframe-Inhalt wird um 20 Pixel nach unten verschoben.|
|6 |**iframe**: zeigt den App-Inhalt an.|

### <a name="spacing"></a>Abstand

Optimieren Sie Ihre in-Meeting-Registerkarte, um Edge-to-Edge im Bereich von 280 Pixel breitem IFRAME anzupassen. Es gibt 20 Pixel Textabstand auf der linken und rechten Seite des IFRAME und zwischen dem Registerkarten Kopf. Der iframe ist vollständig am unteren Rand der Registerkarte angefüllt.

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-spacing.png" alt-text="In diesem Beispiel werden Bemaßungen im Abstands Abstand im Besprechungs Register dargestellt." border="false":::

### <a name="scrolling"></a>Scrollen

Iframe-Inhalte sollten vertikal scrollen. Sie können nur den Inhalt sehen, zu dem Sie einen Bildlauf durchgeführt haben (nichts oberhalb oder unterhalb). Die ScrollBar ist Teil des IFRAME-Inhalts.

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-scrolling.png" alt-text="Beispiel zeigt, wie die in-Meeting-Registerkarte einen Bildlauf durchführt." border="false":::

### <a name="navigation"></a>Navigation

Für Szenarien mit Navigationsebenen oder schweren Inhalten empfehlen wir, Benutzern das Navigieren zu einer sekundären Ebene zu ermöglichen. Benutzer müssen in der Lage sein, zur vorherigen Ebene zurückzukehren.

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav.png" alt-text="Beispiel zeigt die in-Meeting-Navigation." border="false":::

## <a name="use-an-in-meeting-dialog"></a>Verwenden eines in-Meeting-Dialogs

In-Meeting-Dialoge werden in der Teams-Besprechungs Phase angezeigt. Sie benötigen Aufmerksamkeit, Bestätigung oder Interaktion eines Benutzers, sind jedoch subtil und unterbrechen die Besprechung nicht. Sie sollten diese sparsam und für Szenarien verwenden, die leicht und aufgabenorientiert sind.

### <a name="use-cases"></a>Anwendungsfälle

In-Meeting-Dialogfelder werden von einem Benutzer (wie dem Besprechungsorganisator) ausgelöst, der den Teilnehmern möglicherweise Folgendes wünscht:

* Kurzes Feedback geben
* Eine kurze Umfrage oder Umfrage durchführen
* Übermitteln von Genehmigungen
* Erinnerungen abrufen

:::image type="content" source="../../assets/images/apps-in-meetings/use-in-meeting-dialog.png" alt-text="Beispiel zeigt, wie Sie ein in-Meeting-Dialogfeldverwenden können." border="false":::

### <a name="anatomy-in-meeting-dialog"></a>Anatomie: Dialogfeld "in der Besprechung"

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-anatomy.png" alt-text="Beispiel zeigt die strukturelle Anatomie eines in-Meeting-Dialogs." border="false":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|1|**Kopfzeile**: schließt das App-Symbol, den Namen, die Aktionszeichenfolge und das Schließsymbol ein.|
|2 |**iframe**: zeigt den App-Inhalt an.|

### <a name="anatomy-in-meeting-dialog-header"></a>Anatomie: in-Meeting-Dialogfeld Kopfzeile

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-header-anatomy.png" alt-text="Beispiel zeigt die strukturelle Anatomie einer in-Meeting-Dialogfeld Kopfzeile." border="false":::

Es gibt zwei Header Varianten. Verwenden Sie nach Möglichkeit die Variante mit dem Avatar, um zu verstärken, dass das Dialogfeld von einer Person kommt.

|Leistungsindikator|Beschreibung|
|----------|-----------|
|1|**Avatar**: Person, die den in-Meeting-Dialog initiiert.|
|2 |**App-Symbol**|
|3 |**App-Name**|
|4 |**Schaltfläche Schließen**: das Dialogfeld wird geschlossen.|
|5 |**Aktionszeichenfolge**: beschreibt normalerweise, wer das Dialogfeld initiiert hat.|

### <a name="responsive-behavior"></a>Dynamisches Verhalten

In-Meeting-Dialogfelder können in der Größe variieren, um verschiedene Szenarien zu berücksichtigen. Stellen Sie sicher, dass der Abstand und die Komponentengrößen beibehalten werden.

* **Width**: die iframe-Breite ist ein absoluter Wert innerhalb des angegebenen Bereichs.
* **Height**: die Höhe des Dialogs wird durch den Inhalt im IFRAME bestimmt. Der vertikale Bildlauf übernimmt den Inhalt, der die maximale Höhe überschreitet.

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-responsive.png" alt-text="Beispiel wird das in-Meeting-Dialogfeld angezeigt. Breite: min--280 Pixel (248 Pixel IFRAME). Max--460 Pixel (428 Pixel IFRAME). Höhe: 300 Pixel (IFRAME)." border="false":::

## <a name="after-a-meeting"></a>Nach einer Besprechung

Sie können nach dem Beenden zu einer Besprechung zurückkehren und App-Inhalte anzeigen. In diesem Beispiel kann der Besprechungsorganisator die Umfrageergebnisse auf der Registerkarte " **contoso** " anzeigen. (Hinweis: aus Entwurfssicht gibt es keinen Unterschied zwischen der Benutzeroberfläche vor und nach der Besprechung.)

:::image type="content" source="../../assets/images/apps-in-meetings/post-meeting-experience.png" alt-text="Beispiel zeigt eine Registerkarte Nachbesprechung." border="false":::

## <a name="best-practices"></a>Bewährte Methoden

### <a name="interactions"></a>Interaktionen

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/interaction-do.png" alt-text="Beispiel für eine bewährte Methode für die Besprechungs Erweiterung." border="false":::

#### <a name="do-limit-the-number-of-interactions"></a>Do: Begrenzen der Anzahl von Interaktionen

Entfernen Sie für in-Meeting-Dialogfelder unnötige Inhalte, die nicht dazu beitragen, dass Benutzer schnell etwas erreichen.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/interaction-dont.png" alt-text="Beispiel für eine bewährte Methode für die Besprechungs Erweiterung." border="false":::

#### <a name="dont-introduce-unnecessary-elements"></a>Nicht: Einführung unnötiger Elemente

Ein einzelnes in-Meeting-Dialogfeld mit mehreren Interaktionen kann vom Anruf ablenken.

   :::column-end:::
:::row-end:::

### <a name="layout"></a>Layout

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-layout-do.png" alt-text="Beispiel für eine bewährte Methode für die Besprechungs Erweiterung." border="false":::

#### <a name="do-use-single-column-layouts"></a>Do: Verwenden von Einzel Spaltenlayouts

Da sich die Dialogfelder in der Mitte der Besprechungs Phase befinden, sollte die Aufgaben Vervollständigung schnell und einfach sein, um Benutzer Frustration zu vermeiden.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-layout-dont.png" alt-text="Beispiel für eine bewährte Methode für die Besprechungs Erweiterung." border="false":::

#### <a name="dont-clutter-the-space"></a>Nicht: Übersichtlichkeit des Speicherplatzes

Dichte oder übermäßig strukturierte Inhalte können störend und überwältigend sein, vor allem während einer Besprechung.

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-layout-do.png" alt-text="Beispiel für eine bewährte Methode für die Besprechungs Erweiterung." border="false":::

#### <a name="do-use-single-columns"></a>Do: einzelne Spalten verwenden

Angesichts der engen Natur in der Besprechungs Registerkarte wird dringend empfohlen, den Inhalt in einer einzelnen Spalte anzuzeigen.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-layout-dont.png" alt-text="Beispiel für eine bewährte Methode für die Besprechungs Erweiterung." border="false":::

#### <a name="dont-use-multiple-columns"></a>Nicht: mehrere Spalten verwenden

Aufgrund des begrenzten Speicherplatzes der in-Meeting-Registerkarte werden Layouts mit mehr als einer Spalte nicht empfohlen.

   :::column-end:::
:::row-end:::

### <a name="controls"></a>Steuerelemente

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-controls-do.png" alt-text="Beispiel für eine bewährte Methode für die Besprechungs Erweiterung." border="false":::

#### <a name="do-right-align-the-primary-action"></a>Do: Rechtsbündiges Ausrichten der primären Aktion

Es wird empfohlen, die positioiningste Aktion am am weitesten rechts gelegenen Ort zu übersichtlich.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-controls-dont.png" alt-text="Beispiel für eine bewährte Methode für die Besprechungs Erweiterung." border="false":::

#### <a name="dont-left-or-center-align-actions"></a>Nicht: Links oder zentrierte Ausrichtungs Aktionen

Dies weicht vom standardmäßigen Teams-Muster für die Platzierung von Steuerelementen in einem Dialogfeld ab und kann mit einem Dialogfeld hinter dem oberen Rand in Konflikt stehen.

   :::column-end:::
:::row-end:::

### <a name="scroll"></a>Bildlauf

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-scroll-do.png" alt-text="Beispiel für eine bewährte Methode für die Besprechungs Erweiterung." border="false":::

#### <a name="do-scroll-vertically"></a>Do: vertikal scrollen

Es wird empfohlen, die visuell intensivste Aktion an der am weitesten rechts gelegenen Stelle zu positionieren.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-scroll-dont.png" alt-text="Beispiel für eine bewährte Methode für die Besprechungs Erweiterung." border="false":::

#### <a name="dont-scroll-horizontally"></a>Nicht: horizontal scrollen

Ein horizontaler Bildlauf ist kein erwartetes Verhalten in Microsoft Teams. Andere Canvases in der Besprechungs Umgebung Scrollen vertikal.

   :::column-end:::
:::row-end:::

### <a name="workflows"></a>Workflows

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-workflow-do.png" alt-text="Beispiel für eine bewährte Methode für die Besprechungs Erweiterung." border="false":::

#### <a name="do-surface-complex-scenarios-in-the-in-meeting-tab"></a>Do: Oberflächen komplexe Szenarien auf der Registerkarte "in-Meeting"

Wenn Ihre APP mehrere Aufgaben umfasst, wird ein Layout mit einer einzelnen Spalte auf einer Registerkarte in der Besprechung dringend empfohlen.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-workflow-dont.png" alt-text="Beispiel für eine bewährte Methode für die Besprechungs Erweiterung." border="false":::

#### <a name="dont-package-complex-scenarios-in-the-in-meeting-dialog"></a>Nicht: Verpacken komplexer Szenarien im Dialogfeld "in-Meeting"

In-Meeting-Dialoge sind für kurze Interaktionen vorgesehen.

   :::column-end:::
:::row-end:::

### <a name="theming"></a>Designs

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-theming-do.png" alt-text="Beispiel für eine bewährte Methode für die Besprechungs Erweiterung." border="false":::

#### <a name="do-use-teams-color-tokens"></a>Do: Verwenden von Microsoft Teams-Farb Token

Microsoft Teams-Besprechungen sind für den dunklen Modus optimiert, um visuelles und kognitives Rauschen zu reduzieren, sodass sich Benutzer auf die Diskussion und den freigegebenen Inhalt konzentrieren können. Erfahren Sie mehr über die Verwendung von <a href="https://fluentsite.z22.web.core.windows.net/0.51.3/colors#color-scheme" target="_blank">Farb Token (Fluent UI)</a>.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-theming-dont.png" alt-text="Beispiel für eine bewährte Methode für die Besprechungs Erweiterung." border="false":::

#### <a name="dont-include-another-dismiss-button"></a>Nicht: andere Schaltfläche "Schließen" einschließen

Das Bereitstelleneiner Option zum Schließen von Inhalten in Besprechungs Registerkarten kann Probleme verursachen, da bereits eine Schaltfläche in der Kopfzeile vorhanden ist, um die in-Meeting-Registerkarte selbst zu schließen.

   :::column-end:::
:::row-end:::

### <a name="navigation"></a>Navigation

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav-do.png" alt-text="Beispiel für eine bewährte Methode für die Besprechungs Erweiterung." border="false":::

#### <a name="do-have-a-back-button"></a>Do: verfügen über eine Schaltfläche "zurück"

Wenn auf einer Registerkarte in der Besprechung mehr als eine Navigationsebene vorhanden ist, müssen die Benutzer in der Lage sein, zu ihren vorherigen Ansichten zurückzukehren.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav-dont.png" alt-text="Beispiel für eine bewährte Methode für die Besprechungs Erweiterung." border="false":::

#### <a name="dont-include-another-dismiss-button"></a>Nicht: andere Schaltfläche "Schließen" einschließen

Das Bereitstelleneiner Option zum Schließen von Inhalten in Besprechungs Registerkarten kann Probleme verursachen, da bereits eine Schaltfläche in der Kopfzeile vorhanden ist, um die in-Meeting-Registerkarte selbst zu schließen.

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav-caution.png" alt-text="Beispiel für eine bewährte Methode für die Besprechungs Erweiterung." border="false":::

#### <a name="caution-avoid-modals-within-the-in-meeting-tab"></a>Vorsicht: Vermeiden von modaldaten auf der Registerkarte "in-Meeting"

Modals (auch als Vorgangs Module bezeichnet) in der ohnehin engen Registerkarte "in-Meeting" kann den Inhalt Umbrechen und verdecken.

   :::column-end:::
:::row-end:::

## <a name="validate-your-design"></a>Überprüfen des Designs

Wenn Sie Ihre APP in AppSource veröffentlichen möchten, sollten Sie sich mit den Entwurfsproblemen vertraut machen, die häufig dazu führen, dass apps während der Übermittlung fehlschlagen.

> [!div class="nextstepaction"]
> [Überprüfen der Entwurfs Validierungsrichtlinien](../../concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md#validation-guidelines--most-failed-test-cases)
