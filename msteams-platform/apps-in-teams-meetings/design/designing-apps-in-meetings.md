---
title: Entwerfen Der Besprechungserweiterung
author: heath-hamilton
description: Erfahren Sie, wie Sie die Entwurfsrichtlinien implementieren und die Benutzeroberflächenvorlagen verwenden, um eine Besprechungserweiterung für Teams zu entwerfen.
ms.author: lajanuar
ms.localizationpriority: medium
ms.topic: conceptual
ms.date: 04/07/2022
ms.openlocfilehash: d0d994a7966f3ee172b29e6f9a6f1d4d4a2edff0
ms.sourcegitcommit: 2d2a08f671c3d19381403ba1af5dff1f06bb4dd6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/15/2022
ms.locfileid: "67338851"
---
# <a name="designing-your-microsoft-teams-meeting-extension"></a>Entwerfen eigener Microsoft Teams-Messaging-Erweiterungen

Sie können Apps erstellen, um Besprechungen produktiver zu gestalten. Bitten Sie z. B. personen, während einer Besprechung eine Umfrage abzuschließen oder eine schnelle Erinnerung zu senden, die den Ablauf der Besprechung nicht unterbricht.

## <a name="microsoft-teams-ui-kit"></a>Microsoft Teams-UI-Kit

Umfassendere Entwurfsrichtlinien, einschließlich Elemente, die Sie bei Bedarf abrufen und ändern können, finden Sie im Microsoft Teams UI Kit.

> [!div class="nextstepaction"]
> [Holen Sie sich das Microsoft Teams-UI-Kit (Figma)](https://www.figma.com/community/file/916836509871353159)

## <a name="add-a-meeting-extension"></a>Hinzufügen einer Besprechungserweiterung

Benutzer können eine Besprechungserweiterung vor und während Besprechungen hinzufügen. Sie können auch eine App für eine bestimmte Besprechung direkt aus dem Teams-Store hinzufügen.

### <a name="add-before-a-meeting"></a>Vor einer Besprechung hinzufügen

In den Besprechungsdetails können Benutzer **"Registerkarte hinzufügen+** " auswählen, um das App-Flyout zu öffnen und apps zu finden, die für Besprechungen optimiert sind.

:::image type="content" source="../../assets/images/apps-in-meetings/add-before-meeting.png" alt-text="Das Beispiel zeigt, wie Eine Besprechungserweiterung vor einer Besprechung hinzugefügt wird.":::

### <a name="add-during-a-meeting"></a>Während einer Besprechung hinzufügen

#### <a name="mobile"></a>Mobil

Nachdem die App hinzugefügt wurde (z. B. auf dem Desktop), können Benutzer auf die App in einer Besprechung zugreifen, indem sie **"Mehr**:::image type="icon" source="../../assets/icons/teams-client-more.png":::" auswählen.

:::image type="content" source="../../assets/images/apps-in-meetings/mobile-add-during-meeting.png" alt-text="Das Beispiel zeigt, wie Sie eine Besprechungserweiterung während einer Besprechung auf mobilgeräten hinzufügen.":::

#### <a name="desktop"></a>Desktop

In einer Besprechung können Benutzer **"Weitere** :::image type="icon" source="../../assets/icons/teams-client-more.png"::: > **Hinzufügen"** und dann die gewünschte App auswählen.

:::image type="content" source="../../assets/images/apps-in-meetings/add-during-meeting.png" alt-text="Das Beispiel zeigt, wie Sie während einer Besprechung eine Besprechungserweiterung hinzufügen.":::

## <a name="before-a-meeting"></a>Vor einer Besprechung

Vor einer Besprechung ist Ihre App für Benutzer auf einer Registerkarte verfügbar. Das folgende Beispiel zeigt einen Entwurf einer Umfragefrage, die während der Besprechung beantwortet wird.

:::image type="content" source="../../assets/images/apps-in-meetings/before-meeting-tab.png" alt-text="Das Beispiel zeigt, wie Sie Inhalte in den Besprechungsdetails vor einem Anruf anzeigen.":::

### <a name="anatomy-meeting-tab-before-and-after-meetings"></a>Anatomie: Registerkarte "Besprechung" (vor und nach Besprechungen)

:::image type="content" source="../../assets/images/apps-in-meetings/meeting-details-tab-anatomy.png" alt-text="Das Beispiel zeigt die strukturelle Anatomie einer Besprechungsregisterkarte vor und nach einer Besprechung.":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|1|**Registerkartenname**:Navigationsbezeichnung für Ihre Registerkarte.|
|2|**Registerkartenüberlauf**: Öffnet Registerkartenaktionen, z. B. Umbenennen und Entfernen.|
|3|**iframe**: Zeigt Ihre App-Inhalte an.|

### <a name="design-with-ui-templates"></a>Entwerfen mit Benutzeroberflächenvorlagen

Verwenden Sie eine der folgenden Teams-Benutzeroberflächenvorlagen, um ihre Besprechungsregisterkarte zu entwerfen:

* [Liste](../../concepts/design/design-teams-app-ui-templates.md#list): Listen können verwandte Elemente in einem übersichtlichen Format anzeigen und Benutzern ermöglichen, Aktionen für eine gesamte Liste oder einzelne Elemente auszuführen.
* [Task Board](../../concepts/design/design-teams-app-ui-templates.md#task-board): Ein Task Board, manchmal auch als „Kanban-Board“ oder „Organisationsprozessdarstellungen“ bezeichnet, ist eine Sammlung von Karten, die häufig verwendet werden, um den Status von Arbeitselementen oder Tickets nachzuverfolgen.
* [Dashboard](../../concepts/design/design-teams-app-ui-templates.md#dashboard): Ein Dashboard ist ein Zeichenbereich mit mehreren Karten, die eine Übersicht über Daten oder Inhalte bieten.
* [Formular](../../concepts/design/design-teams-app-ui-templates.md#form): Formulare dienen zum strukturierten Sammeln, Überprüfen und Übermitteln von Benutzereingaben.
* [Leerer Zustand](../../concepts/design/design-teams-app-ui-templates.md#empty-state): Die leere Statusvorlage kann für viele Szenarien verwendet werden, einschließlich der Anmeldung, der ersten Ausführung, der Fehlermeldungen und vieles mehr.
* [Linke Navigation](../../concepts/design/design-teams-app-advanced-ui-components.md#left-nav): Die linke Navigationskomponente kann hilfreich sein, wenn ihre Registerkarte eine Navigation erfordert. Im Allgemeinen sollten Sie die Navigation auf ein Minimum beschränken.

## <a name="use-an-in-meeting-tab"></a>Verwenden einer Registerkarte in der Besprechung

Die Registerkarte "In der Besprechung" ist ein Zeichenbereich zum Erweitern der Zusammenarbeit während Besprechungen. Teilnehmer können App-Inhalte in einem dedizierten Bereich außerhalb der Besprechungsphase über freigegebene oder rollenbasierte Ansichten anzeigen und mit ihnen interagieren.

### <a name="use-cases"></a>Anwendungsfälle

Personen können die Registerkarte "In Besprechung" verwenden, um Folgendes zu erreichen:

* Geben Sie detailliertes Feedback. Bewerten Sie z. B. einen Kandidaten.
* Erstellen Sie eine Umfrage, eine Umfrage oder ein Aufgabenelement für die Besprechungsteilnehmer.
* Zeigen Sie für die Besprechung relevante Notizen an. Beispielsweise Informationen zu einem Vertriebsleiter.

#### <a name="mobile"></a>Mobil

:::image type="content" source="../../assets/images/apps-in-meetings/mobile-use-in-meeting-tab.png" alt-text="Das Beispiel zeigt, wie Sie Umfrageinhalte auf einer Registerkarte in einer Besprechung auf mobilgeräten präsentieren können.":::

#### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/apps-in-meetings/use-in-meeting-tab.png" alt-text="Das Beispiel zeigt, wie Sie Umfrageinhalte auf einer Registerkarte in einer Besprechung präsentieren können.":::

### <a name="anatomy-in-meeting-tab"></a>Anatomie: Registerkarte "In Besprechung"

:::image type="content" source="../../assets/in-meeting-tab-anatomy.png" alt-text="Das Beispiel zeigt die strukturelle Anatomie einer Registerkarte in einer Besprechung.":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|1|**App-Symbol (ausgewählt)**: transparentes App-Logo mit 16 Pixeln.|
|2|**App-Name**|
|3|**Kopfzeile**: Enthält ihren App-Namen.|
|4 |**Schaltfläche "Schließen"**: Schließt die Registerkarte. Verwenden Sie immer das Symbol für das schließende Symbol oben rechts anstelle einer Aktion in der Fußzeile.|
|5 |**Benachrichtigungsleiste**: Fehlerwarnungen werden direkt unterhalb der Kopfzeile angezeigt und verschieben den rest des iframe-Inhalts um 20 Pixel nach unten.|
|6 |**iframe**: Zeigt Ihre App-Inhalte an.|

### <a name="spacing"></a>Abstand

Optimieren Sie Ihre Registerkarte in der Besprechung so, dass sie edge-to-edge innerhalb des iFrame-Bereichs von 280 Pixeln passt. Es gibt 20 Pixel Abstand auf der linken und rechten Seite des iFrames und zwischen der Registerkartenüberschrift. Der iframe ist vollständig beschnitten am unteren Rand der Registerkarte.

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-spacing.png" alt-text="Das Beispiel zeigt die Abmessungen des Tababstands in der Besprechung.":::

### <a name="scrolling"></a>Scrollen

Beachten Sie Folgendes, wenn Sie das Scrollen zulassen:

* Inhalte im iframe-Inhalt sollten nur vertikal scrollen.
* Benutzern sollte nur der Inhalt angezeigt werden, zu dem sie gescrollt haben (nichts darüber oder darunter).
* Die Bildlaufleiste ist Teil des iframe-Inhalts.

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-scrolling.png" alt-text="Das Beispiel zeigt, wie die Registerkarte in der Besprechung scrollt.":::

### <a name="navigation"></a>Navigation

Für Szenarien mit Navigationsebenen oder umfangreichen Inhalten wird empfohlen, Benutzern die Navigation zu einer sekundären Ebene zu ermöglichen. Benutzer müssen zur vorherigen Ebene zurückkehren können.

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav.png" alt-text="Das Beispiel zeigt die Navigation in der Besprechung.":::

## <a name="use-an-in-meeting-dialog"></a>Verwenden eines Besprechungsdialogfelds

Besprechungsdialogfelder werden auf der Teams-Besprechungsphase angezeigt. Sie erfordern die Aufmerksamkeit, Bestätigung oder Interaktion eines Benutzers, sind aber subtil und unterbrechen die Besprechung nicht. Sie sollten diese sparsam und für Szenarien verwenden, die leicht und aufgabenorientiert sind.

### <a name="use-cases"></a>Anwendungsfälle

In-Besprechungsdialogfelder werden von einem Benutzer (z. B. dem Besprechungsorganisator) ausgelöst, der folgende Aktionen ausführen soll:

* Geben Sie kurzes Feedback.
* Nehmen Sie an einer kurzen Umfrage oder Umfrage teil.
* Genehmigungen übermitteln.
* Abrufen von Erinnerungen.

### <a name="mobile"></a>Mobil

:::image type="content" source="../../assets/images/apps-in-meetings/mobile-use-in-meeting-dialog.png" alt-text="Das Beispiel zeigt, wie Sie ein Dialogfeld in einer Besprechung auf mobilgeräten verwenden können.":::

### <a name="desktop"></a>Desktop

:::image type="content" source="../../assets/images/apps-in-meetings/use-in-meeting-dialog.png" alt-text="Beispiel zeigt, wie Sie ein besprechungsinternes Dialogfeld verwenden können.":::

### <a name="anatomy-in-meeting-dialog"></a>Anatomie: Dialogfeld "In Besprechung"

:::image type="content" source="../../assets/in-meeting-dialog-anatomy.png" alt-text="Beispiel zeigt die strukturelle Anatomie eines Besprechungsdialogfelds.":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|1|**Kopfzeile**: Enthält Das App-Symbol, den Namen, die Aktionszeichenfolge und das Symbol "Schließen".|
|2|**iframe**: Zeigt Ihre App-Inhalte an.|

### <a name="anatomy-in-meeting-dialog-header"></a>Anatomie: Kopfzeile des Dialogfelds "In Besprechung"

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-header-anatomy.png" alt-text="Das Beispiel zeigt die strukturelle Anatomie eines Besprechungsdialogkopfs.":::

Es gibt zwei Kopfzeilenvarianten. Verwenden Sie nach Möglichkeit die Variante mit dem Avatar, um zu verstärken, dass das Dialogfeld von einer Person stammt.

|Leistungsindikator|Beschreibung|
|----------|-----------|
|1|**Avatar**: Person, die das Dialogfeld in der Besprechung initiiert.|
|2|**App-Symbol**|
|3|**App-Name**|
|4 |**Schaltfläche "Schließen"**: Schließt das Dialogfeld.|
|5 |**Aktionszeichenfolge**: Beschreibt in der Regel, wer das Dialogfeld initiiert hat.|

### <a name="responsive-behavior-in-meeting-dialogs"></a>Reaktionsfähiges Verhalten: Dialogfelder in Besprechungen

In Besprechungsdialogfeldern kann die Größe variieren, um unterschiedliche Szenarien zu berücksichtigen. Achten Sie darauf, die Auffüllung und Komponentengrößen beizubehalten.

* **Breite**: Sie können die Breite des iFrames des Dialogfelds an einer beliebigen Stelle innerhalb des unterstützten Größenbereichs angeben.
* **Höhe**: Sie können die Höhe des iFrames des Dialogfelds an einer beliebigen Stelle innerhalb des unterstützten Größenbereichs angeben. Sie können Benutzern auch erlauben, vertikal zu scrollen, wenn der App-Inhalt die maximale Höhe überschreitet.

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-responsive.png" alt-text="Das Beispiel zeigt das Dialogfeld in der Besprechung. Breite: Min--280 Pixel (248 Pixel iFrame). Max. 460 Pixel (428 Pixel iFrame). Höhe: 300 Pixel (iframe).":::

## <a name="use-the-shared-meeting-stage"></a>Verwenden der freigegebenen Besprechungsphase

Sie können Benutzern die Freigabe und Interaktion mit einigen oder allen App-Inhalten auf der Besprechungsphase ermöglichen. Hier sind Beispiele dafür, wie Personen dieses Feature während einer Besprechung verwenden können:

* Bearbeiten eines Dokuments.
* Whiteboarding
* Überprüfen eines Dashboards.
* Schauen Sie sich ein Video an.
* Spielen eines Spiels.

Für die Besprechung freigegebene Apps belegen denselben Platz wie ein freigegebener Bildschirm. Die Phase wird auch für alle Besprechungsteilnehmer auf die gleiche Weise neu festgelegt.

> [!NOTE]
> Derzeit können mobile Benutzer Keine App-Inhalte für die Besprechungsphase freigeben. Sie können jedoch Inhalte sehen, die vom Desktop freigegeben wurden.

### <a name="use-cases"></a>Anwendungsfälle

In der gemeinsamen Besprechungsphase geht es um Zusammenarbeit und Teilnahme. Hier sind einige Beispielszenarien, die Ihnen den Einstieg erleichtern.

:::row:::
   :::column span="1":::

**Bearbeiten und überprüfen**: Tauchen Sie in Dashboards ein und planen Sie mit allen Teilnehmern der Besprechung.

   :::column-end:::
   :::column span="3":::

:::image type="content" source="~/assets/images/apps-in-meetings/shared-meeting-stage-edit-review.png" alt-text="Beispiel zeigt ein Dashboard, das in der freigegebenen Besprechungsphase überprüft wird.":::

:::image type="content" source="~/assets/images/apps-in-meetings/shared-meeting-stage-edit-review-component.png" alt-text="Das Beispiel zeigt eine Dashboardkomponente, die in der freigegebenen Besprechungsphase überprüft wird.":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="1":::

**Whiteboard**: Zeichnen und ideenieren Sie gemeinsam auf einem freigegebenen Zeichenbereich.

   :::column-end:::
   :::column span="3":::

:::image type="content" source="~/assets/images/apps-in-meetings/shared-meeting-stage-whiteboard.png" alt-text="Das Beispiel zeigt ein Whiteboard auf der freigegebenen Besprechungsphase.":::

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="1":::

**Quiz**: Testen Sie Wissen und gewinnen Sie Einblicke mit interaktiven Materialien.

   :::column-end:::
   :::column span="3":::

:::image type="content" source="~/assets/images/apps-in-meetings/shared-meeting-stage-quiz.png" alt-text="Das Beispiel zeigt eine Prüfung auf der freigegebenen Besprechungsphase.":::

   :::column-end:::
:::row-end:::

### <a name="anatomy-share-all-app-content-to-a-meeting"></a>Anatomie: Teilen aller App-Inhalte für eine Besprechung

:::image type="content" source="~/assets/images/apps-in-meetings/shared-meeting-stage-anatomy.png" alt-text="Die Abbildung zeigt die Design-Anatomie der freigegebenen Besprechungsphase, wenn alle App-Inhalte freigegeben werden.":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|1|**App-Symbol**: Das hervorgehobene Symbol gibt an, dass die Registerkarte der App in der Besprechung geöffnet ist.|
|2|**Schaltfläche "Für Besprechung freigeben"**: Der Einstiegspunkt zum Freigeben der App für die Besprechung. Zeigt an, ob Sie Ihre App für die Verwendung der freigegebenen Besprechungsphase konfigurieren.|
|3|**Referentenzuordnung**: Zeigt den Namen des Teilnehmers an, der die App freigegeben hat.|
|4 |**iframe**: Zeigt Ihre App-Inhalte an.|
|5 |**Schaltfläche "Freigabe beenden"**: Beendet die Freigabe der App für die Besprechungsphase. Wird nur für den Teilnehmer angezeigt, der die Freigabe gestartet hat.|

### <a name="anatomy-share-specific-app-content-to-a-meeting"></a>Anatomie: Freigeben bestimmter App-Inhalte für eine Besprechung

:::image type="content" source="~/assets/images/apps-in-meetings/shared-meeting-stage-anatomy-component.png" alt-text="Die Abbildung zeigt die Design-Anatomie der freigegebenen Besprechungsphase, wenn nur bestimmte App-Inhalte freigegeben werden.":::

|Leistungsindikator|Beschreibung|
|----------|-----------|
|1|**App-Symbol**: Das hervorgehobene Symbol gibt an, dass die Registerkarte der App in der Besprechung geöffnet ist.|
|2|**Schaltfläche "Für Besprechung freigeben"**: Der Einstiegspunkt zum Freigeben der App für die Besprechung. Verwenden Sie für eine konsistente Benutzererfahrung immer das standardmäßige Teams-Freigabesymbol. **"Für Besprechung freigeben** " ist der empfohlene Standardtext, aber Sie können ihn auch für Ihre Anwendungsfälle anpassen. Beispiel: **Gemeinsames Wiedergeben** für eine Spiele-App oder **Gemeinsames Ansehen** für eine Video-App. Stellen Sie in beiden Fällen klar, dass die Aktion eine freigegebene, interaktive Erfahrung für alle Teilnehmer der Besprechung schafft.|
|3|**Referentenzuordnung**: Zeigt den Namen des Teilnehmers an, der die App freigegeben hat.|
|4 |**iframe**: Zeigt Ihre App-Inhalte an.|
|5 |**Schaltfläche "Freigabe beenden"**: Beendet die Freigabe der App für die Besprechungsphase. Wird nur für den Teilnehmer angezeigt, der die Freigabe gestartet hat.|

### <a name="responsive-behavior-shared-meeting-stage"></a>Reaktionsfähiges Verhalten: Freigegebene Besprechungsphase

Apps, die für die Besprechungsphase freigegeben wurden, variieren je nach Status der Besprechung und der Größe des Benutzers. Behalten Sie abstand und das dynamische Layout der Navigation und Steuerelemente wie in einem Browser bei.

* **Seitenbereich**: Ein Benutzer kann den Seitenbereich während einer Besprechung jederzeit öffnen lassen, um zu chatten, die Teilnehmerliste anzuzeigen oder eine App (z. B. Die Registerkarte "In der Besprechung") zu verwenden. Die Phase wird dynamisch neu angeordnet, wenn das Panel geöffnet ist.
* **Video- und Audioraster**: Das Video- und Audioraster ist immer sichtbar, um Besprechungsteilnehmer anzuzeigen. Wenn ein Benutzer jemanden in der Besprechung spotlights oder anheftt, erhöht dies die Höhe oder Breite des Teilnehmerrasters je nach Ausrichtung.

#### <a name="meeting-stage-without-side-panel"></a>Besprechungsphase (ohne Seitenbereich)

Wenn der Seitenbereich nicht geöffnet ist, beträgt die Besprechungsphase standardmäßig 994 x 678 Pixel und kann mindestens 792 x 382 Pixel betragen.

:::image type="content" source="~/assets/images/apps-in-meetings/meeting-stage-no-side-panel.png" alt-text="Abbildung der Reaktionsfähigkeit der freigegebenen Besprechungsphase mit geschlossenem Seitenbereich.":::

#### <a name="meeting-stage-with-side-panel"></a>Besprechungsphase (mit Seitenbereich)

Wenn der Seitenbereich geöffnet ist, beträgt die Besprechungsphase standardmäßig 918 x 540 Pixel und kann mindestens 472 x 382 Pixel betragen.

:::image type="content" source="~/assets/images/apps-in-meetings/meeting-stage-with-side-panel.png" alt-text="Abbildung der Reaktionsfähigkeit der freigegebenen Besprechungsphase mit geöffnetem Seitenbereich.":::

## <a name="after-a-meeting"></a>Nach einer Besprechung

Sie können zu einer Besprechung zurückkehren, nachdem sie beendet wurde, und App-Inhalte anzeigen. In diesem Beispiel kann sich der Besprechungsorganisator die Umfrageergebnisse auf der Registerkarte **"Contoso** " ansehen. (Hinweis: Aus Entwurfssicht gibt es keinen Unterschied zwischen der Registerkartenoberfläche vor und nach der Besprechung.)

:::image type="content" source="../../assets/images/apps-in-meetings/post-meeting-experience.png" alt-text="Die Beispielabbildung zeigt eine Registerkarte nach der Besprechung.":::

## <a name="best-practices"></a>Bewährte Methoden

Verwenden Sie diese Empfehlungen, um eine hochwertige App-Erfahrung zu erstellen.

### <a name="interactions"></a>Interaktionen

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/interaction-do.png" alt-text="Beispiel, das zeigt, wie die Anzahl der Interaktionen eingeschränkt wird.":::

#### <a name="do-limit-the-number-of-interactions"></a>Do: Limit the number of interactions

Entfernen Sie bei Besprechungsdialogfeldern unnötige Inhalte, die Benutzern nicht helfen, schnell etwas zu erreichen.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/interaction-dont.png" alt-text="Beispiel, das zeigt, wie sie keine unnötigen Elemente einführen.":::

#### <a name="dont-introduce-unnecessary-elements"></a>Don't: Einführung unnötiger Elemente

Ein einzelnes Dialogfeld in der Besprechung mit mehreren Interaktionen kann von der Besprechung ablenken.

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/interaction-shared-stage-do.png" alt-text="Beispiel, das zeigt, wie eine fokussierte Umgebung erstellt wird.":::

#### <a name="do-create-a-focused-environment"></a>Do: Erstellen einer fokussierten Umgebung

Wir empfehlen, die App-Erfahrung nur auf die Besprechungsphase zu beschränken. Sie können eine Registerkarte in der Besprechung im Seitenbereich als sekundäre, private Ansicht für bestimmte Szenarien verwenden.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/interaction-shared-stage-dont.png" alt-text="Beispiel, das zeigt, wie konkurrierende Oberflächen während Besprechungen nicht einbezogen werden.":::

#### <a name="dont-include-competing-surfaces"></a>Nicht verwenden: Konkurrierende Oberflächen einschließen

Ihre App sollte die Benutzer nur bitten, sich auf eine einzelne Oberfläche zu konzentrieren, unabhängig davon, ob sie auf der Bühne zusammenarbeitet oder auf ein Dialogfeld in der Besprechung reagiert. (Hinweis: Sie können nicht beibehalten, dass Dialogfelder von anderen Apps ausgelöst werden, während sich Ihre App auf der Bühne befindet.)

   :::column-end:::
:::row-end:::

### <a name="layout"></a>Layout

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-layout-do.png" alt-text="Beispiel, das zeigt, wie Sie ein einspaltiges Dialogfeldlayout verwenden sollten.":::

#### <a name="do-use-a-one-column-dialog"></a>Do: Use a one-column dialog

Da sich die Dialogfelder im Zentrum der Besprechungsphase befinden, sollte die Aufgabenerledigung schnell und einfach sein, um Frustrationen der Benutzer zu vermeiden.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-layout-dont.png" alt-text="Beispiel, das zeigt, dass Sie den Platz einer Besprechungserweiterung nicht überladen sollten.":::

#### <a name="dont-clutter-the-space"></a>Don't: Clutter the space

Dichte oder überstrukturierte Inhalte können ablenkend und überwältigend sein, insbesondere während einer Besprechung.

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-theming-do.png" alt-text="Beispiel für ein einspaltiges Registerkartenlayout.":::

#### <a name="do-use-a-one-column-tab"></a>Do: Verwenden einer einspaltigen Registerkarte

Angesichts der schmalen Beschaffenheit der Registerkarte in der Besprechung wird dringend empfohlen, den Inhalt in einer einzigen Spalte anzuzeigen.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-layout-dont.png" alt-text="Beispiel für eine Registerkarte mit mehreren Spalten.":::

#### <a name="dont-use-multiple-columns"></a>Nicht empfohlen: Verwenden mehrerer Spalten

Aufgrund des begrenzten Platzes auf der Registerkarte "Besprechung" werden Layouts mit mehr als einer Spalte nicht empfohlen.

   :::column-end:::
:::row-end:::

### <a name="controls"></a>Steuerelemente

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-controls-do.png" alt-text="Beispiel, das zeigt, wie primäre Steuerelemente rechtsbündig ausgerichtet werden.":::

#### <a name="do-right-align-the-primary-action"></a>Do: Right align the primary action

Wir empfehlen, die visuell schwerste Aktion an der richtigen Position zu positionieren.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-controls-dont.png" alt-text="Beispiel, das zeigt, wie Sie primäre Steuerelemente nicht linksbündig ausrichten sollten.":::

#### <a name="dont-left-or-center-align-actions"></a>Nicht empfohlen: Linksbündige oder zentrierte Ausrichtungsaktionen

Dies weicht vom standardmäßigen Teams-Muster für die Platzierung von Steuerelementen in einem Dialogfeld ab und kann mit einem Dialogfeld hinter dem oberen Dialogfeld in Konflikt kommen.

   :::column-end:::
:::row-end:::

### <a name="scrolling"></a>Scrollen

:::row:::
   :::column span="":::

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-scroll-do.png" alt-text="Beispiel für vertikalen Bildlauf auf einer Registerkarte in der Besprechung.":::

:::image type="content" source="../../assets/images/apps-in-meetings/shared-meeting-stage-scroll-do.png" alt-text="Beispiel für vertikalen Bildlauf in der freigegebenen Besprechungsphase.":::

#### <a name="do-scroll-vertically"></a>Do: Scrollen vertikal

Benutzer erwarten einen vertikalen Bildlauf in Teams (und an anderer Stelle). Dies gilt möglicherweise nicht, wenn Sie über eine kreative Canvas verfügen, z. B. ein Whiteboard, das Benutzer über die X- und Y-Achse schwenken können.

   :::column-end:::
   :::column span="":::

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-scroll-dont.png" alt-text="Beispiel für einen horizontalen Bildlauf auf einer Registerkarte in der Besprechung.":::

:::image type="content" source="../../assets/images/apps-in-meetings/shared-meeting-stage-scroll-dont.png" alt-text="Beispiel für horizontalen Bildlauf in der freigegebenen Besprechungsphase.":::

#### <a name="dont-scroll-horizontally"></a>Nicht empfohlen: Horizontaler Bildlauf

Horizontales Scrollen ist in Teams (einschließlich der Besprechungsumgebung) kein erwartetes Verhalten.

   :::column-end:::
:::row-end:::

### <a name="workflows"></a>Workflows

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-workflow-do.png" alt-text="Beispiel für ein komplexes Szenario auf einer Registerkarte in der Besprechung.":::

#### <a name="do-surface-complex-scenarios-in-the-in-meeting-tab"></a>Do: Surface complex scenarios in the in-meeting tab

Wenn Ihre App mehrere Aufgaben enthält, wird dringend empfohlen, eine Besprechungsregisterkarte mit einem einspaltigen Layout zu verwenden.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-dialog-workflow-dont.png" alt-text="Beispiel für komplexe Szenarien in einem Dialogfeld in einer Besprechung.":::

#### <a name="dont-make-in-meeting-dialogs-complex"></a>Nicht empfohlen: Gestalten Von Besprechungsdialogfeldern zu komplex

In Besprechungsdialogfeldern sind für kurze Interaktionen vorgesehen.

   :::column-end:::
:::row-end:::

### <a name="theming"></a>Design

:::row:::
   :::column span="":::

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-theming-do.png" alt-text="Beispiel für eine Besprechungserweiterung mit dem dunklen Design.":::

:::image type="content" source="../../assets/images/apps-in-meetings/shared-meeting-stage-theming-do.png" alt-text="Ein weiteres Beispiel, das die Besprechungserweiterung mit dem dunklen Design zeigt.":::

#### <a name="do-focus-on-dark-theme"></a>Do: Fokus auf dunkles Design

Teams-Besprechungen sind für dunkle Designs optimiert, um visuelle und kognitive Geräusche zu reduzieren, damit sich Benutzer auf die Diskussion und freigegebene Inhalte konzentrieren können. Beachten Sie, dass bestimmte Arten von Apps (z. B. Whiteboarding und Dokumentbearbeitung) keinen dunklen Zeichenbereich benötigen.

   :::column-end:::
   :::column span="":::

:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-theming-dont.png" alt-text="Beispiel für eine Besprechungserweiterung mit Farben, die nicht mit dem Besprechungsdesign übereinstimmen.":::

:::image type="content" source="../../assets/images/apps-in-meetings/shared-meeting-stage-theming-dont.png" alt-text="Ein weiteres Beispiel, das eine Besprechungserweiterung mit Farben zeigt, die nicht mit dem Besprechungsdesign übereinstimmen.":::

#### <a name="dont-use-unfamiliar-colors"></a>Nicht: Verwenden Sie unbekannte Farben

Farben, die mit der Besprechungsumgebung kollidieren, können ablenken und in Teams weniger nativ erscheinen. Erfahren Sie mehr über die [Teams-Farbhierarchie](https://developer.microsoft.com/fluentui#/styles/web/colors/products), einschließlich neutraler Anrufdesigns.

   :::column-end:::
:::row-end:::

### <a name="navigation"></a>Navigation

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav-do.png" alt-text="Beispiel für eine Besprechungserweiterung mit einer Zurück-Schaltfläche.":::

#### <a name="do-have-a-back-button"></a>Do: Have a Back button

Wenn auf einer Registerkarte in der Besprechung mehrere Navigationsebenen vorhanden sind, müssen Benutzer zu ihren vorherigen Ansichten zurückkehren können.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav-dont.png" alt-text="Beispiel für eine Besprechungserweiterung mit zwei Schaltflächen zum Schließen.":::

#### <a name="dont-include-another-dismiss-button"></a>Don't: Include another dismiss button

Das Bereitstellen einer Option zum Schließen von Registerkarteninhalten in Besprechungen kann zu Problemen führen, da bereits eine Schaltfläche in der Kopfzeile vorhanden ist, um die Registerkarte in der Besprechung selbst zu schließen.

   :::column-end:::
:::row-end:::

:::row:::
   :::column span="":::
   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/in-meeting-tab-nav-caution.png" alt-text="Beispiel mit Modaldaten (oder Aufgabenmodulen) auf einer Registerkarte in der Besprechung.":::

#### <a name="caution-avoid-modals-within-the-in-meeting-tab"></a>Achtung: Vermeiden von Modalien auf der Registerkarte "Besprechung"

Modale Elemente (auch als Aufgabenmodule bezeichnet) auf der bereits schmalen Registerkarte in der Besprechung können den Inhalt umbrechen und verdecken.

   :::column-end:::
:::row-end:::

### <a name="responsive-behavior"></a>Dynamisches Verhalten

:::row:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/shared-meeting-stage-responsiveness-do.png" alt-text="Beispiel, das zeigt, wie die Größe einer Besprechungserweiterung ordnungsgemäß geändert wird.":::

#### <a name="do-resize-and-scale-your-app-responsively"></a>Do: Ändern der Größe und Skalierung Ihrer App

App-Inhalte sollten in kleineren Fenstern dynamisch angepasst und verkleinert werden. Lassen Sie die Hauptnavigation Ihrer App und alle unverankerten Steuerelemente sichtbar.

   :::column-end:::
   :::column span="":::
:::image type="content" source="../../assets/images/apps-in-meetings/shared-meeting-stage-responsiveness-dont.png" alt-text="Beispiel, das zeigt, wie die Größe einer Besprechungserweiterung nicht ordnungsgemäß geändert wird.":::

#### <a name="dont-crop-or-clip-primary-ui-components"></a>Don't: Crop or clip primary UI components

Eine unverankerte Navigation und Steuerelemente außerhalb des Bildschirms und das Erfordern eines Bildlaufs können für Benutzer verwirrend sein. Der App-Inhalt sollte nicht horizontal scrollen, wenn er nicht in den iFrame passen kann.

   :::column-end:::
:::row-end:::

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Konfigurieren Ihrer App für Besprechungen](~/apps-in-teams-meetings/enable-and-configure-your-app-for-teams-meetings.md)
