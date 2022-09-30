---
title: Einschränkungen und bekannte Probleme in der Zusammenarbeitssteuerungs-App
author: surbhigupta
description: In diesem Modul erfahren Sie mehr über Einschränkungen und bekannte Probleme in der App für Steuerelemente für die Zusammenarbeit für Microsoft Teams.
ms.localizationpriority: medium
ms.author: v-npaladugu
ms.topic: conceptual
ms.openlocfilehash: fe403c566b47be6509ff0d11113c34a8fc667cc9
ms.sourcegitcommit: edfe85e312c73e34aa795922c4b7eb0647528d48
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/30/2022
ms.locfileid: "68243388"
---
# <a name="limitations-and-known-issues"></a>Einschränkungen und bekannte Probleme

> [!NOTE]
> Derzeit sind Die Steuerelemente für die Zusammenarbeit nur in der [öffentlichen Entwicklervorschau](~/resources/dev-preview/developer-preview-intro.md) verfügbar.

Es folgen die Einschränkungen für Steuerelemente für die Zusammenarbeit:

* Komponenten können in Canvas-Apps nicht verwendet werden.
* Komponenten unterstützen nur vollständige Registerkartenansichten.

     :::image type="content" source="../assets/images/collaboration-control/tasks-tab.png" alt-text="Der Screenshot zeigt die Aufgaben." border="true":::

* Die ausgewählte Untergitteransicht wird nicht berücksichtigt. Alle Aufgaben, Besprechungen oder Notizen für den Datensatz für die Zusammenarbeit werden angezeigt.

     :::image type="content" source="../assets/images/collaboration-control/subgrid-view.png" alt-text="Der Screenshot zeigt die Subgrid-Ansicht der Aufgaben." border= "true":::

* Aktivitäten, die dem Zeitachsensteuerelement hinzugefügt wurden, werden nicht in den Komponenten, Aufgaben, Besprechungen und Notizen angezeigt, die in den Komponenten erstellt wurden, nicht im Zeitachsensteuerelement enthalten.
* Neue Datensätze müssen vor dem Zugriff auf die Komponenten gespeichert werden, andernfalls wird ein leerer Bildschirm angezeigt.
* Die Komponenten erben keine Designelemente von dem Formular oder der App, dem sie hinzugefügt werden.
* Lokalisierung ist nur verfügbar, wenn die App in Microsoft Teams ausgeführt wird.
* Der strenge Modus von Microsoft Edge wird nicht unterstützt, und websiteübergreifende Cookies sind erforderlich.

**Admin Center wird nicht aktualisiert, wenn die Installation oder das Upgrade abgeschlossen ist**

Wenn Sie die Installationsschritte bei der [Installation der Steuerelemente für die Zusammenarbeit ausführen](~/samples/install-collaboration-control.md), werden Sie zum Power Platform Admin Center umgeleitet. Ein Banner wird angezeigt, wenn die Installation gestartet wird, aber es wird nicht aktualisiert, wenn die Installation abgeschlossen ist. Der Status wird während der Installation aufgelistet, und wenn er abgeschlossen ist, ist er möglicherweise nicht in der Liste verfügbar. Sie können die Lösungsliste anzeigen, um [https://make.powerapps.com/](https://make.preview.powerapps.com/) zu bestätigen, dass die Installation abgeschlossen ist.

**Ansicht während der Installation:** :::image type="content" source="../assets/images/collaboration-control/view-during-installation.png" alt-text="Der Screenshot zeigt den Prozess während der Installation." border="true":::

**Ansicht nach der Installation:** :::image type="content" source="../assets/images/collaboration-control/view-after-installation.png" alt-text="Der Screenshot zeigt den Abschluss der Installation." border="true":::

Beim Upgrade der Steuerelemente auf eine höhere Version wird das banner für die gleiche installation gestartet angezeigt, aber der Status des Steuerelements bleibt auch nach Abschluss des Upgrades installiert. Sie können bestätigen, dass das Upgrade abgeschlossen ist, indem Sie die Lösungsliste unter [https://make.powerapps.com/](https://make.preview.powerapps.com/)überprüfen, es muss ungefähr 15 Minuten dauern.

Sie können auch im Verlauf für bestimmte Lösungen sehen, dass die spätere Version installiert und dann die vorherige Version entfernt wurde: :::image type="content" source="../assets/images/collaboration-control/history.png" alt-text="Der Screenshot zeigt den Verlauf für bestimmte Lösungen der Versionen, die installiert und entfernt werden." border="true":::

## <a name="bookings-meetings"></a>Bookings-Besprechungen

Das Steuerelement "Besprechungen" unterstützt eine Besprechung auf einmal, wenn Sie Bookings verwenden, um mit Benutzern außerhalb Ihrer Organisation in Kontakt zu treten. Ein bis viele Besprechungen werden derzeit nicht mithilfe von Steuerelementen für die Zusammenarbeit unterstützt.

**Der Status des Besprechungsteilnehmers ist falsch.**

Wenn ein Teilnehmer eine Besprechung mit rsvpst, wird sein Antwortstatus in der Agendaansicht und in den Besprechungsdetails möglicherweise nicht ordnungsgemäß angezeigt. Wenn Sie die Schaltfläche "Ablehnen" auswählen, wird möglicherweise eine Fehlermeldung auf dem Bildschirm zurückgegeben.

## <a name="tasks"></a>Aufgaben

**Aufgaben: Filtertext "klar" wird nicht übersetzt**

Der Text auf der Schaltfläche "Löschen", der im Aufgabenfilter angezeigt wird, wird nicht übersetzt.

**Aufgaben: Rasterkontextmenü wird zugeschnitten angezeigt**

Wenn das Raster "Aufgaben" mit einer geringen Anzahl von Vorgängen aufgefüllt wird, wird das Rasterkontextmenü möglicherweise abgeschnitten angezeigt und erfordert die Verwendung von Bildlaufleisten.

**Aufgaben: Stichwortsuchfilter verwenden den Operator "BeginsWith" für "Gast"-Aufgaben**

Wenn Sie Aufgaben mithilfe des Schlüsselworttextfilters durchsuchen, werden "Gast"-Aufgaben mithilfe des Operators "BeginsWith" zurückgegeben. "Member"-Aufgaben werden mithilfe des Operators "Contains" zurückgegeben.

## <a name="files"></a>Dateien

Beim Navigieren in den Archivordner nach dem Archivieren von Dateien können Benutzern doppelte Archivordner angezeigt werden.  Das Navigieren von den Archivordnern zur Hauptansicht der Dateien behebt das Problem, und archivierte Dateien werden nicht entfernt.

## <a name="controls"></a>Steuerelemente

**Steuerelemente können nicht gespeichert werden**

Wenn ein Steuerelement eine Aufgabe oder Besprechung nicht speichern kann, ist die ursache wahrscheinlich eine falsch konfigurierte Gruppen-ID oder Kanal-ID.  

Lösung 1: Stellen Sie sicher, dass die IDs korrekt sind und die Einstellungen gemäß der Einstellungsübung angewendet werden.  

Lösung 2: Stellen Sie sicher, dass sich die Power Apps-Umgebung und die Teams-Umgebung auf demselben Mandanten befinden.  

**Steuerelemente können nicht geladen werden oder zeigen einen Fehler an**

Wenn die Steuerelemente nicht geladen werden können oder ein Fehler angezeigt wird, kann es sich um ein vorübergehendes Problem handeln.

Beispiel:

:::image type="content" source="../assets/images/collaboration-control/sync-fail.png" alt-text="Der Screenshot zeigt, dass die Steuerelementsynchronisierung fehlschlägt.":::

Dies würde im Konsolenprotokoll wie folgt gerendert:

:::image type="content" source="../assets/images/collaboration-control/control-fail.png" alt-text="Screenshot ist ein Beispiel für ein Steuerelementfehler im Consol-Protokoll." border="true":::

Lösung: Aktualisieren Sie Ihren Browser, oder laden Sie die Registerkarte in der Teams-App neu.

Wenn Sie den App-Namen, das Symbol oder die Beschreibung nach dem Hochladen in Teams ändern möchten, sehen Sie sich das [Anpassen der Darstellung von Apps](/MicrosoftTeams/customize-apps#customize-details-of-an-app) an.

## <a name="error-logging"></a>Fehlerprotokollierung

Die Steuerelemente stellen die folgenden Methoden zum Debuggen Ihrer Anwendung bereit.

1. **Ablaufverfolgungsprotokollierung** von Plug-In-Ereignissen, wenn eine API aufgerufen wird. Diese Informationen werden in Ihrer Dataverse-Umgebung gespeichert.

    1. Um die Ablaufverfolgungsprotokollierung zu aktivieren, führen Sie die folgenden Schritte in [der Protokollierung und Ablaufverfolgung aus](/power-apps/developer/data-platform/logging-tracing?WT.mc_id=email).

1. **Browserprotokollierung** für UI-Steuerelemente. Dies ist die standardmäßige Konsolenprotokollierung.

    1. Es wird unterstützt, wenn Sie einen Browser verwenden, um die Collaboration Manager-App über Power Platform und Teams-Web auszuführen.
    1. Auf der Registerkarte "Konsole" können Sie mithilfe der Fehlermeldung "Collaboration Manager" nach Fehlern suchen oder nach Collaboration Manager Steuerelementnamen wie "Aufgaben" suchen.

> [!TIP]
> Wenn in einem Teams-Desktopclient ein Fehler auftritt, versuchen Sie, es im Teams-Web zu replizieren, um das Fehlerprotokoll zu erfassen.

## <a name="faq"></a>Häufig gestellte Fragen

<br>

<details>

<summary><b>Was sind die Steuerelemente für die Zusammenarbeit (Vorschau)?</b></summary>

Mithilfe von Steuerelementen für die Zusammenarbeit (Vorschau) können Sie Microsoft 365-Funktionen zu Ihren benutzerdefinierten Power Apps-Anwendungen hinzufügen, um Benutzerworkflows bei der Zusammenarbeit an Geschäftsprozessen in Teams oder Power Apps zu vereinfachen.

<br>

</details>

<br>

<details>

<summary><b>Was ist der Vorteil der Steuerelemente für die Zusammenarbeit (Vorschau) für Hersteller?</b></summary>

Mit diesen neuen Steuerelementen können Sie als Hersteller Drag-and-Drop-Steuerelemente verwenden, die Microsoft 365-Zusammenarbeit für Ihre App ermöglichen.

<br>

</details>

<br>

<details>

<summary><b>Was ist der Vorteil der Steuerelemente für die Zusammenarbeit (Vorschau) für Benutzer?</b></summary>

Ihre Benutzer können Produktivitätsgewinne erzielen und in ihrem Fluss bleiben, indem sie an Genehmigungen, Dateien, Besprechungen, Notizen und Aufgaben zusammenarbeiten, ohne den Kontext Ihrer App zu verlassen.

<br>

</details>

<br>

<details>

<summary><b>Gewusst wie Zugriff auf die Steuerelemente für die Zusammenarbeit erhalten (Vorschau)?</b></summary>

Bitten Sie Ihren Power Platform-Administrator, die Steuerelemente aus AppSource in Ihrer Power Apps-Umgebung zu installieren.

<br>

</details>

<br>

<details>

<summary><b>Gewusst wie die Steuerelemente einer modellgesteuerten App hinzufügen?</b></summary>

Wechseln Sie zum Formular-Designer, und ziehen Sie die Steuerelemente aus dem Komponentenbereich auf ein Formular.

<br>

</details>
