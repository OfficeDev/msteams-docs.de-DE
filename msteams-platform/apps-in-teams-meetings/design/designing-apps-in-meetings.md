---
title: Entwerfen Ihrer Besprechungserweiterung
author: heath-hamilton
description: Erfahren Sie, wie Sie Apps in Teams Besprechungen entwerfen und das Microsoft Teams UI Kit, die Registerkarte für Besprechungen und Anwendungsfälle, das reaktionsfähige Verhalten und die freigegebene Besprechungsphase sowie das Design und die Navigation abrufen.
ms.author: lajanuar
ms.localizationpriority: medium
ms.topic: conceptual
keywords: UI-Kit-Vorlage in besprechungsbasiertem reaktionsfähigem Verhalten – freigegebene Besprechungsphase
ms.openlocfilehash: 39d0ef00d6a012726f2a3645f3d8e2bf00ebaf33
ms.sourcegitcommit: af1d0a4041ce215e7863ac12c71b6f1fa3e3ba81
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/10/2021
ms.locfileid: "60887845"
---
# <a name="designing-your-microsoft-teams-meeting-extension"></a>Entwerfen ihrer Microsoft Teams Besprechungserweiterung

Sie können Apps erstellen, um Besprechungen produktiver zu gestalten. Bitten Sie personen beispielsweise, während einer Besprechung eine Umfrage durchzuführen, oder senden Sie eine kurze Erinnerung, die den Ablauf der Besprechung nicht unterbricht.

## <a name="microsoft-teams-ui-kit"></a>Microsoft Teams-UI-Kit

Umfassendere Entwurfsrichtlinien, einschließlich Elementen, die Sie nach Bedarf abrufen und ändern können, finden Sie im Microsoft Teams UI Kit.

> [!div class="nextstepaction"]
> [Holen Sie sich das Microsoft Teams-UI-Kit (Figma)](https://www.figma.com/community/file/916836509871353159)

## <a name="add-a-meeting-extension"></a>Hinzufügen einer Besprechungserweiterung

Benutzer können vor und während Besprechungen eine Besprechungserweiterung hinzufügen. Sie können eine App für eine bestimmte Besprechung auch direkt aus dem Teams Store hinzufügen.

### <a name="add-before-a-meeting"></a>Hinzufügen vor einer Besprechung

In den Besprechungsdetails können Benutzer **eine Registerkarte hinzufügen +** auswählen, um das App-Flyout zu öffnen und apps zu finden, die für Besprechungen optimiert sind.

:::image type="content" source="../../assets/images/apps-in-meetings/add-before-meeting.png" alt-text="Beispiel zeigt, wie Sie eine Besprechungserweiterung vor einer Besprechung hinzufügen." border="false":::

### <a name="add-during-a-meeting"></a>Während einer Besprechung hinzufügen

#### <a name="mobile"></a>Mobilgeräte

Nachdem die App hinzugefügt wurde (z. B. auf dem Desktop), können Benutzer in einer Besprechung auf die App zugreifen, indem sie **"Mehr"** :::image type="icon" source="../../assets/icons/teams-client-more.png"::: auswählen.

:::image type="content" source="../../assets/images/apps-in-meetings/mobile-add-during-meeting.png" alt-text="Beispiel zeigt, wie sie während einer Besprechung auf mobilen Geräten eine Besprechungserweiterung hinzufügen." border="false":::

#### <a name="desktop"></a>Desktop

In einer Besprechung können Benutzer **weitere** :::image type="icon" source="../../assets/icons/teams-client-more.png":::  >  **Apps hinzufügen** und die gewünschte App auswählen.

:::image type="content" source="../../assets/images/apps-in-meetings/add-during-meeting.png" alt-text="Beispiel zeigt, wie sie während einer Besprechung eine Besprechungserweiterung hinzufügen." border="false":::

## <a name="before-a-meeting"></a>Vor einer Besprechung

Vor einer Besprechung steht Ihre App Benutzern auf einer Registerkarte zur Verfügung. Das folgende Beispiel zeigt einen Entwurf einer Umfragefrage, die während der Besprechung beantwortet wird.

:::image type="content" source="../../assets/images/apps-in-meetings/before-meeting-tab.png" alt-text="Beispiel zeigt, wie Sie Inhalte in den Besprechungsdetails vor einem Anruf appieren." border="false":::

### <a name="anatomy-meeting-tab-before-and-after-meetings"></a>Anatomie: Besprechungsregisterkarte (vor und nach Besprechungen)

:::image type="content" source="../../assets/images/apps-in-meetings/meeting-details-tab-anatomy.png" alt-text="Beispiel zeigt die strukturelle Anatomie einer Besprechungsregisterkarte vor und nach einer Besprechung." border="false":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|1|**Registerkartenname**:Navigationsbezeichnung für Ihre Registerkarte.|
|2|**Registerkartenüberlauf**: Öffnet Registerkartenaktionen, z. B. Umbenennen und Entfernen.|
|3|**iframe**: Zeigt Ihre App-Inhalte an.|

### <a name="design-with-ui-templates"></a>Entwerfen mit Benutzeroberflächenvorlagen

Verwenden Sie eine der folgenden Teams Ui-Vorlagen, um die Besprechungsregisterkarte zu entwerfen:

* [Liste](../../concepts/design/design-teams-app-ui-templates.md#list): Listen können verwandte Elemente in einem übersichtlichen Format anzeigen und Benutzern ermöglichen, Aktionen für eine gesamte Liste oder einzelne Elemente auszuführen.
* [Task Board](../../concepts/design/design-teams-app-ui-templates.md#task-board): Ein Task Board, manchmal auch als „Kanban-Board“ oder „Organisationsprozessdarstellungen“ bezeichnet, ist eine Sammlung von Karten, die häufig verwendet werden, um den Status von Arbeitselementen oder Tickets nachzuverfolgen.
* [Dashboard](../../concepts/design/design-teams-app-ui-templates.md#dashboard): Ein Dashboard ist ein Zeichenbereich mit mehreren Karten, die eine Übersicht über Daten oder Inhalte bieten.
* [Formular](../../concepts/design/design-teams-app-ui-templates.md#form): Formulare dienen zum strukturierten Sammeln, Überprüfen und Übermitteln von Benutzereingaben.
* [Leerer Zustand](../../concepts/design/design-teams-app-ui-templates.md#empty-state): Die leere Statusvorlage kann für viele Szenarien verwendet werden, einschließlich der Anmeldung, der ersten Ausführung, der Fehlermeldungen und vieles mehr.
* [Linke Navigation](../../concepts/design/design-teams-app-advanced-ui-components.md#left-nav): Die linke Navigationskomponente kann hilfreich sein, wenn ihre Registerkarte eine Navigation erfordert. Im Allgemeinen sollten Sie die Navigation auf ein Minimum beschränken.

## <a name="use-an-in-meeting-tab"></a>Verwenden einer Besprechungsregisterkarte

Die Registerkarte "Besprechungsinterne Besprechung" ist ein Zeichenbereich zum Erweitern der Zusammenarbeit während Besprechungen. Teilnehmer können App-Inhalte in einem dedizierten Bereich außerhalb der Besprechungsphase über freigegebene oder rollenbasierte Ansichten anzeigen und mit ihnen interagieren.

### <a name="use-cases"></a>Anwendungsfälle

Personen können die Registerkarte "Besprechungsinterne Besprechung" für Folgendes verwenden:

* Geben Sie ausführliches Feedback. Bewerten Sie beispielsweise einen Stellenkandidaten.
* Erstellen Sie eine Umfrage, eine Umfrage oder ein Aufgabenelement für die Besprechungsteilnehmer.
* Zeigt notizen an, die für die Besprechung relevant sind. Beispielsweise Informationen zu einem Vertriebsleiter.

#### <a name="mobile"></a>Mobilgeräte

:::image type="content" source="../../assets/images/apps-in-meetings/mobile-use-in-meeting-tab.png" alt-text="Beispiel zeigt, wie Sie Umfrageinhalte auf einer Besprechungsregisterkarte auf mobilen Geräten anzeigen können." border="false":::

#### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/apps-in-meetings/use-in-meeting-tab.png" alt-text="Beispiel zeigt, wie Sie Abfrageinhalte auf einer Besprechungsregisterkarte darstellen können." border="false":::

### <a name="anatomy-in-meeting-tab"></a>Anatomie: Registerkarte "In-Meeting"

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-anatomy.png" alt-text="Beispiel zeigt die strukturelle Anatomie einer Besprechungsregisterkarte." border="false":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|1|**App-Symbol (ausgewählt):** 16 Pixel transparentes App-Logo.|
|2|**App-Name**|
|3|**Header:** Enthält ihren App-Namen.|
|4|**Schaltfläche "Schließen":** Schließt die Registerkarte. Verwenden Sie immer das Symbol zum Schließen oben rechts anstelle einer Aktion in der Fußzeile.|
|5|**Benachrichtigungsleiste:** Fehlerwarnungen werden direkt unterhalb der Kopfzeile angezeigt, und der iframe-Inhalt wird um 20 Pixel nach unten verschoben.|
|6 |**iframe**: Zeigt Ihre App-Inhalte an.|

### <a name="spacing"></a>Abstand

Optimieren Sie Ihre Besprechungsregisterkarte so, dass sie in den 280 Pixel breiten iFramebereich passt. Es gibt 20 Pixel Abstand auf der linken und rechten Seite des iframe und zwischen der Registerkartenkopfzeile. Der iframe ist vollständig beschnitten bis zum unteren Rand der Registerkarte.

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-spacing.png" alt-text="Beispiel zeigt die Größe des Tababstands in besprechungsinternen Besprechungen." border="false":::

### <a name="scrolling"></a>Scrollen

Beachten Sie Folgendes, wenn Sie den Bildlauf zulassen:

* Inhalte im iframe-Inhalt sollten nur vertikal scrollen.
* Benutzer sollten nur den Inhalt sehen, zu dem sie einen Bildlauf durchgeführt haben (nichts über oder darunter). 
* Die Bildlaufleiste ist Teil des iframe-Inhalts.

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-scrolling.png" alt-text="Beispiel zeigt, wie die Besprechungsregisterkarte scrollt." border="false":::

### <a name="navigation"></a>Navigation

Für Szenarien mit Navigationsebenen oder umfangreichen Inhalten wird empfohlen, Benutzern das Navigieren zu einer sekundären Ebene zu gestatten. Benutzer müssen in der Lage sein, zur vorherigen Ebene zurückzukehren.

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav.png" alt-text="Beispiel zeigt die Navigation in Besprechungen." border="false":::

## <a name="use-an-in-meeting-dialog"></a>Verwenden eines Besprechungsdialogfelds

Dialogfelder in Besprechungen werden auf der Teams Besprechungsphase angezeigt. Sie erfordern die Aufmerksamkeit, Bestätigung oder Interaktion eines Benutzers, sind aber dezent und unterbrechen die Besprechung nicht. Sie sollten diese sparsam und für Szenarien verwenden, die leicht und aufgabenorientiert sind.

### <a name="use-cases"></a>Anwendungsfälle

In-Meeting-Dialogfelder werden von einem Benutzer (z. B. dem Besprechungsorganisator) ausgelöst, der Teilnehmer möglicherweise folgendes wünschen:

* Geben Sie kurzes Feedback
* Nehmen Sie an einer kurzen Umfrage oder Umfrage teil
* Übermitteln von Genehmigungen
* Abrufen von Erinnerungen

### <a name="mobile"></a>Mobilgeräte

:::image type="content" source="../../assets/images/apps-in-meetings/mobile-use-in-meeting-dialog.png" alt-text="Beispiel zeigt, wie Sie ein Besprechungsdialogfeld auf mobilgeräten verwenden können." border="false":::

### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/apps-in-meetings/use-in-meeting-dialog.png" alt-text="Beispiel zeigt, wie Sie ein Besprechungsdialogfeld verwenden können." border="false":::

### <a name="anatomy-in-meeting-dialog"></a>Anatomie: Besprechungsdialogfeld

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-anatomy.png" alt-text="Beispiel zeigt die strukturelle Anatomie eines Besprechungsdialogfelds." border="false":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|1|**Kopfzeile:** Enthält das App-Symbol, den Namen, die Aktionszeichenfolge und das Schließen-Symbol.|
|2|**iframe**: Zeigt Ihre App-Inhalte an.|

### <a name="anatomy-in-meeting-dialog-header"></a>Anatomie: Kopfzeile des Besprechungsdialogfelds

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-header-anatomy.png" alt-text="Beispiel zeigt die strukturelle Anatomie einer Besprechungsdialogkopfzeile." border="false":::

Es gibt zwei Kopfzeilenvarianten. Verwenden Sie nach Möglichkeit die Variante mit dem Avatar, um zu bestätigen, dass das Dialogfeld von einer Person stammt.

|Leistungsindikator|Beschreibung|
|----------|-----------|
|1|**Avatar**: Person, die das Besprechungsdialogfeld initiiert.|
|2|**App-Symbol**|
|3|**App-Name**|
|4|**Schaltfläche "Schließen":** Schließt das Dialogfeld.|
|5|**Aktionszeichenfolge:** Beschreibt in der Regel, wer das Dialogfeld initiiert hat.|

### <a name="responsive-behavior-in-meeting-dialogs"></a>Reaktionsfähiges Verhalten: Dialogfelder in Besprechungen

Dialogfelder in Besprechungen können je nach Größe variieren, um unterschiedliche Szenarien zu berücksichtigen. Achten Sie darauf, die Auffüllung und Komponentengrößen beizubehalten.

* **Breite:** Sie können die Breite des iframe des Dialogfelds an einer beliebigen Stelle innerhalb des unterstützten Größenbereichs angeben.
* **Höhe:** Sie können die Höhe des iFrames des Dialogfelds an einer beliebigen Stelle innerhalb des unterstützten Größenbereichs angeben. Sie können Benutzern auch den vertikalen Bildlauf ermöglichen, wenn Der App-Inhalt die maximale Höhe überschreitet.

Geben Sie zum Implementieren die Breite und Höhe mithilfe des [`externalResourceUrl`](~/apps-in-teams-meetings/API-references.md#notificationsignal-api) Schlüssels an.

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-responsive.png" alt-text="Beispiel zeigt das Dialogfeld &quot;In-Meeting&quot;. Breite: Min.-280 Pixel (248 Pixel iframe). Max-460 Pixel (428 Pixel iframe). Höhe: 300 Pixel (iframe)." border="false":::

## <a name="use-the-shared-meeting-stage"></a>Verwenden der freigegebenen Besprechungsphase

Die freigegebene Besprechungsphase hilft Besprechungsteilnehmern bei der Interaktion und Zusammenarbeit mit App-Inhalten in Echtzeit. Die Benutzer können sich beispielsweise auf die Bearbeitung eines Dokuments, brainstorming mit einem Whiteboard oder das Überprüfen eines Dashboards konzentrieren.

Für die Besprechungsphase freigegebene Apps belegen den gleichen Platz wie ein freigegebener Bildschirm. Die Phase wird für alle Besprechungsteilnehmer neu ausgerichtet.

> [!NOTE]
> Alle Benutzer in der Besprechung können die App sehen, wenn sie vom Desktop freigegeben werden. Die Funktion zum Freigeben einer App für die Bereitstellung über mobilgeräte ist derzeit jedoch nicht verfügbar.
 
### <a name="use-cases"></a>Anwendungsfälle

In der gemeinsamen Besprechungsphase geht es um Zusammenarbeit und Teilnahme. Hier sind einige Beispielszenarien, die Ihnen bei den ersten Schritten helfen.

:::row:::
   :::column span="1":::

**Bearbeiten und Überprüfen:** Befassen Sie sich mit Dashboards und planen Sie mit allen Personen in der Besprechung.

   :::column-end:::
   :::column span="3":::

:::image type="content" source="~/assets/images/apps-in-meetings/shared-meeting-stage-edit-review.png" alt-text="Beispiel zeigt ein Dashboard, das in der freigegebenen Besprechungsphase überprüft wird." border="false":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="1":::

**Whiteboard:** Zeichnen und Zusammenstellen auf einer freigegebenen Canvas.

   :::column-end:::
   :::column span="3":::

:::image type="content" source="~/assets/images/apps-in-meetings/shared-meeting-stage-whiteboard.png" alt-text="Beispiel zeigt ein Whiteboard in der freigegebenen Besprechungsphase." border="false":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="1":::

**Quiz:** Testen Sie Wissen und gewinnen Sie Einblicke mit interaktiven Materialien.

   :::column-end:::
   :::column span="3":::

:::image type="content" source="~/assets/images/apps-in-meetings/shared-meeting-stage-quiz.png" alt-text="Beispiel zeigt ein Quiz in der phase der freigegebenen Besprechung." border="false":::

   :::column-end:::
:::row-end:::

### <a name="anatomy-shared-meeting-stage"></a>Anatomie: Gemeinsame Besprechungsphase

:::image type="content" source="~/assets/images/apps-in-meetings/shared-meeting-stage-anatomy.png" alt-text="Die Abbildung zeigt die Design-Anatomie der freigegebenen Besprechungsphase." border="false":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|1|**App-Symbol:** Das hervorgehobene Symbol gibt an, dass die Registerkarte "In-Meeting" der App geöffnet ist.|
|2|**Schaltfläche "Für Besprechungsphase freigeben":** Der Einstiegspunkt, an dem die App für die Besprechungsphase freigegeben werden soll. Zeigt an, ob Sie Ihre App für die Verwendung der freigegebenen Besprechungsphase konfigurieren.|
|3|**iframe**: Zeigt Ihre App-Inhalte an.|
|4|**Schaltfläche "Freigabe beenden":** Beendet die Freigabe der App für die Besprechungsphase. Zeigt nur für den Teilnehmer an, der die Freigabe gestartet hat.|
|5|**Zuschreibung** des Referenten: Zeigt den Namen des Teilnehmers an, der die App freigegeben hat.|

### <a name="responsive-behavior-shared-meeting-stage"></a>Reaktionsfähiges Verhalten: Freigegebene Besprechungsphase

Apps, die für die Besprechungsphase freigegeben wurden, variieren je nach Größe des Besprechungsstatus und der Größe des Fensters durch den Benutzer. Verwalten Sie den Abstand und das dynamische Layout von Navigation und Steuerelementen genau wie in einem Browser.

* **Seitenbereich:** Ein Benutzer kann den Seitenbereich jederzeit während einer Besprechung öffnen lassen, um zu chatten, die Teilnehmerliste anzuzeigen oder eine App zu verwenden (z. B. die Registerkarte "In-Meeting"). Die Phase wird dynamisch neu angeordnet, wenn das Panel geöffnet ist.
* **Video- und Audioraster:** Das Video- und Audioraster ist immer sichtbar, um Besprechungsteilnehmer anzuzeigen. Wenn ein Benutzer eine Person in der Besprechung ins Blickfeld rückt oder anheftet, erhöht dies die Höhe oder Breite des Teilnehmerrasters je nach Ausrichtung.

#### <a name="meeting-stage-without-side-panel"></a>Besprechungsphase (ohne Seitenbereich)

Wenn der Seitenbereich nicht geöffnet ist, beträgt die Besprechungsphase standardmäßig 994 x 678 Pixel und kann mindestens 792 x 382 Pixel betragen.

:::image type="content" source="~/assets/images/apps-in-meetings/meeting-stage-no-side-panel.png" alt-text="Abbildung der Reaktionsfähigkeit der freigegebenen Besprechungsphase mit geschlossener Seitenleiste." border="false":::

#### <a name="meeting-stage-with-side-panel"></a>Besprechungsphase (mit Seitenbereich)

Wenn der Seitenbereich geöffnet ist, beträgt die Besprechungsphase standardmäßig 918 x 540 Pixel und kann mindestens 472 x 382 Pixel betragen.

:::image type="content" source="~/assets/images/apps-in-meetings/meeting-stage-with-side-panel.png" alt-text="Abbildung der Reaktionsfähigkeit der freigegebenen Besprechungsphase mit geöffneter Seitenleiste." border="false":::

## <a name="after-a-meeting"></a>Nach einer Besprechung

Sie können zu einer Besprechung zurückkehren, nachdem sie beendet wurde, und App-Inhalte anzeigen. In diesem Beispiel kann sich der Besprechungsorganisator die Umfrageergebnisse auf der Registerkarte **"Contoso"** ansehen. (Hinweis: Aus Entwurfssicht gibt es keinen Unterschied zwischen der Registerkarte "Vor" und "Nach der Besprechung".)

:::image type="content" source="../../assets/images/apps-in-meetings/post-meeting-experience.png" alt-text="Die Beispieldarstellung zeigt eine Registerkarte nach der Besprechung." border="false":::

## <a name="best-practices"></a>Bewährte Methoden

Verwenden Sie diese Empfehlungen, um eine hochwertige App-Erfahrung zu erstellen.

### <a name="interactions"></a>Interaktionen

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/interaction-do.png" alt-text="Beispiel, in dem gezeigt wird, wie die Anzahl der Interaktionen begrenzt wird." border="false":::

#### <a name="do-limit-the-number-of-interactions"></a>Do: Beschränken der Anzahl von Interaktionen

Entfernen Sie für Besprechungsdialogfelder unnötige Inhalte, die Benutzern nicht helfen, schnell etwas zu erreichen.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/interaction-dont.png" alt-text="Beispiel, in dem gezeigt wird, wie keine unnötigen Elemente eingeführt werden." border="false":::

#### <a name="dont-introduce-unnecessary-elements"></a>Nicht empfohlen: Einführen unnötiger Elemente

Ein einzelnes Besprechungsdialogfeld mit mehreren Interaktionen kann von der Besprechung ablenken.

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/interaction-shared-stage-do.png" alt-text="Beispiel für das Erstellen einer fokussierten Umgebung." border="false":::

#### <a name="do-create-a-focused-environment"></a>Do: Erstellen einer fokussierten Umgebung

Es wird empfohlen, die App-Erfahrung nur auf die Besprechungsphase zu beschränken. Sie können eine Besprechungsregisterkarte im Seitenbereich als sekundäre, private Ansicht für bestimmte Szenarien verwenden.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/interaction-shared-stage-dont.png" alt-text="Beispiel, in dem gezeigt wird, wie sie während Besprechungen keine konkurrierten Oberflächen einschließen." border="false":::

#### <a name="dont-include-competing-surfaces"></a>Nicht empfohlen: Einschließen von Oberflächen im Wettbewerb

Ihre App sollte die Benutzer nur auffordern, sich auf eine einzelne Oberfläche zu konzentrieren, unabhängig davon, ob sie auf der Stufe zusammenarbeitet oder auf ein Besprechungsdialogfeld reagiert. (Hinweis: Dialogfelder, die von anderen Apps ausgelöst werden, können nicht beibehalten werden, während Sich Ihre App auf der Stufe befindet.) 

   :::column-end:::
:::row-end:::

### <a name="layout"></a>Layout

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-layout-do.png" alt-text="Beispiel für die Verwendung eines einspaltigen Dialogfeldlayouts." border="false":::

#### <a name="do-use-a-one-column-dialog"></a>Do: Verwenden eines einspaltigen Dialogfelds

Da die Dialogfelder im Mittelpunkt der Besprechungsphase stehen, sollte der Aufgabenabschluss schnell und einfach sein, um Benutzerfrustration zu vermeiden.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-layout-dont.png" alt-text="Beispiel, das zeigt, dass Sie den Raum einer Besprechungserweiterung nicht überladen sollten." border="false":::

#### <a name="dont-clutter-the-space"></a>Don't: Clutter the space

Dichte oder übermäßig strukturierte Inhalte können ablenkend und überwältigend sein, insbesondere während einer Besprechung.

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-layout-do.png" alt-text="Beispiel für ein einspaltiges Registerkartenlayout." border="false":::

#### <a name="do-use-a-one-column-tab"></a>Do: Verwenden einer einspaltigen Registerkarte

Angesichts der schmalen Natur der Besprechungsregisterkarte wird dringend empfohlen, den Inhalt in einer einzelnen Spalte anzuzeigen.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-layout-dont.png" alt-text="Beispiel für eine Registerkarte mit mehreren Spalten." border="false":::

#### <a name="dont-use-multiple-columns"></a>Don't: Use multiple columns

Aufgrund des begrenzten Platzes der Besprechungsregisterkarte werden Layouts mit mehr als einer Spalte nicht empfohlen.

   :::column-end:::
:::row-end:::

### <a name="controls"></a>Steuerelemente

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-controls-do.png" alt-text="Beispiel, das zeigt, wie primäre Steuerelemente rechts ausgerichtet werden." border="false":::

#### <a name="do-right-align-the-primary-action"></a>Do: Rechtsgündige Ausrichtung der primären Aktion

Wir empfehlen, die visuell schwerste Aktion am rechten Ort zu positionieren.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-controls-dont.png" alt-text="Beispiel, das zeigt, wie Sie primäre Steuerelemente nicht linksbündig ausrichten sollten." border="false":::

#### <a name="dont-left-or-center-align-actions"></a>Nicht empfohlen: Aktionen links oder zentr werden ausgerichtet

Dies weicht vom standard Teams Muster für die Platzierung von Steuerelementen in einem Dialogfeld ab und kann mit einem Dialogfeld hinter dem oberen Dialogfeld in Konflikt geraten.

   :::column-end:::
:::row-end:::

### <a name="scrolling"></a>Scrollen

:::row:::
   :::column span="":::

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-scroll-do.png" alt-text="Beispiel für den vertikalen Bildlauf auf einer Besprechungsregisterkarte." border="false":::

:::image type="content" source="../../assets/images/apps-in-meetings/shared-meeting-stage-scroll-do.png" alt-text="Beispiel für den vertikalen Bildlauf in der freigegebenen Besprechungsphase." border="false":::

#### <a name="do-scroll-vertically"></a>Do: Vertikaler Bildlauf

Benutzer erwarten einen vertikalen Bildlauf in Teams (und an anderer Stelle). Dies gilt möglicherweise nicht, wenn Sie über eine kreative Canvas verfügen, z. B. ein Whiteboard, das Benutzer über die X- und Y-Achse schwenken können.

   :::column-end:::
   :::column span="":::

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-scroll-dont.png" alt-text="Beispiel für einen horizontalen Bildlauf auf einer Besprechungsregisterkarte." border="false":::

:::image type="content" source="../../assets/images/apps-in-meetings/shared-meeting-stage-scroll-dont.png" alt-text="Beispiel für den horizontalen Bildlauf in der freigegebenen Besprechungsphase." border="false":::

#### <a name="dont-scroll-horizontally"></a>Nicht ausführen: Horizontaler Bildlauf

Horizontaler Bildlauf ist kein erwartetes Verhalten in Teams (einschließlich der Besprechungsumgebung).

   :::column-end:::
:::row-end:::

### <a name="workflows"></a>Workflows

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-workflow-do.png" alt-text="Beispiel für ein komplexes Szenario auf einer Besprechungsregisterkarte." border="false":::

#### <a name="do-surface-complex-scenarios-in-the-in-meeting-tab"></a>Do: Surface complex scenarios in the in-meeting tab

Wenn Ihre App mehrere Aufgaben enthält, wird dringend empfohlen, eine Besprechungsregisterkarte mit einem einspaltigen Layout zu verwenden.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-workflow-dont.png" alt-text="Beispiel für komplexe Szenarien in einem Besprechungsdialogfeld." border="false":::

#### <a name="dont-make-in-meeting-dialogs-complex"></a>Nicht empfohlen: In-Meeting-Dialogfelder komplex gestalten

Besprechungsdialogfelder sind für kurze Interaktionen vorgesehen.

   :::column-end:::
:::row-end:::

### <a name="theming"></a>Design

:::row:::
   :::column span="":::

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-theming-do.png" alt-text="Beispiel für eine Besprechungserweiterung mit dem dunklen Design." border="false":::

:::image type="content" source="../../assets/images/apps-in-meetings/shared-meeting-stage-theming-do.png" alt-text="Ein weiteres Beispiel für die Besprechungserweiterung mit dem dunklen Design." border="false":::

#### <a name="do-focus-on-dark-theme"></a>Do: Fokus auf dunklem Design

Teams Besprechungen sind für dunkles Design optimiert, um visuelles und kognitives Rauschen zu reduzieren, damit sich Benutzer auf die Diskussion und freigegebene Inhalte konzentrieren können. Beachten Sie, dass bestimmte Arten von Apps (z. B. Whiteboarding und Dokumentbearbeitung) keinen dunklen Zeichenbereich benötigen.

   :::column-end:::
   :::column span="":::

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-theming-dont.png" alt-text="Beispiel für eine Besprechungserweiterung mit Farben, die nicht mit dem Besprechungsdesign übereinstimmen." border="false":::

:::image type="content" source="../../assets/images/apps-in-meetings/shared-meeting-stage-theming-dont.png" alt-text="Ein weiteres Beispiel für eine Besprechungserweiterung mit Farben, die nicht mit dem Besprechungsdesign übereinstimmen." border="false":::

#### <a name="dont-use-unfamiliar-colors"></a>Don't: Verwenden Sie unbekannte Farben

Farben, die mit der Besprechungsumgebung in Konflikt stehen, können ablenkend sein und für Teams weniger nativ erscheinen. Erfahren Sie mehr über die Teams [Farbhierarchie,](https://developer.microsoft.com/fluentui#/styles/web/colors/products)einschließlich Anrufdesign-Neutralen.

   :::column-end:::
:::row-end:::

### <a name="navigation"></a>Navigation

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav-do.png" alt-text="Beispiel für eine Besprechungserweiterung mit einer Schaltfläche &quot;Zurück&quot;." border="false":::

#### <a name="do-have-a-back-button"></a>Do: Have a Back button

Wenn Sie auf einer Besprechungsregisterkarte mehr als eine Navigationsebene haben, müssen Benutzer in der Lage sein, zu ihren vorherigen Ansichten zurückzukehren.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav-dont.png" alt-text="Beispiel für eine Besprechungserweiterung mit zwei Schaltflächen zum Schließen." border="false":::

#### <a name="dont-include-another-dismiss-button"></a>Don't: Include another dismiss button

Das Bereitstellen einer Option zum Schließen von Besprechungsregisterkarteninhalten kann zu Problemen führen, da bereits eine Schaltfläche in der Kopfzeile vorhanden ist, um die Registerkarte in der Besprechung selbst zu schließen.

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav-caution.png" alt-text="Beispiel für modale Elemente (oder Aufgabenmodule) auf einer Besprechungsregisterkarte." border="false":::

#### <a name="caution-avoid-modals-within-the-in-meeting-tab"></a>Vorsicht: Vermeiden Sie modale Elemente auf der Registerkarte "Besprechung".

Modale Elemente (auch als Aufgabenmodule bezeichnet) auf der bereits schmalen Besprechungsregisterkarte können den Inhalt umschließen und verdecken.

   :::column-end:::
:::row-end:::

### <a name="responsive-behavior"></a>Dynamisches Verhalten

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/shared-meeting-stage-responsiveness-do.png" alt-text="Beispiel, das zeigt, wie die Größe einer Besprechungserweiterung ordnungsgemäß angepasst wird." border="false":::

#### <a name="do-resize-and-scale-your-app-responsively"></a>Gehen Sie vor: Anpassen der Größe und dynamisches Skalieren Ihrer App

App-Inhalte sollten in kleineren Fenstern dynamisch angepasst und verkleinert werden. Halten Sie die Hauptnavigation Ihrer App und alle unverankerten Steuerelemente sichtbar.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/shared-meeting-stage-responsiveness-dont.png" alt-text="Beispiel, das zeigt, wie die Größe einer Besprechungserweiterung nicht ordnungsgemäß angepasst wird." border="false":::

#### <a name="dont-crop-or-clip-primary-ui-components"></a>Nicht empfohlen: Zuschneiden oder Beschneiden der primären UI-Komponenten

Die unverankerte Navigation und Steuerelemente außerhalb des Bildschirms und das Suchen eines Bildlaufs können für Benutzer verwirrend sein. Ihre App-Inhalte sollten nicht horizontal scrollen, wenn sie nicht in den iframe passen können.

   :::column-end:::
:::row-end:::

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Konfigurieren Ihrer App für Besprechungen](~/apps-in-teams-meetings/enable-and-configure-your-app-for-teams-meetings.md)
