---
title: Anwendung mit Steuerelementen für die Zusammenarbeit
author: surbhigupta
description: In diesem Modul erfahren Sie, wie Sie eine modellgesteuerte App mit Steuerelementen für die Zusammenarbeit für Teams erstellen und der App Steuerelemente für die Zusammenarbeit hinzufügen.
ms.localizationpriority: medium
ms.author: v-npaladugu
ms.topic: conceptual
ms.openlocfilehash: 119e02f6cc31d8642447e4e7406d461faff3a731
ms.sourcegitcommit: edfe85e312c73e34aa795922c4b7eb0647528d48
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/30/2022
ms.locfileid: "68243059"
---
# <a name="create-a-new-model-driven-app-with-collaboration-controls-for-teams"></a>Erstellen einer neuen modellgesteuerten App mit Steuerelementen für die Zusammenarbeit für Teams

Steuerelemente für die Zusammenarbeit sind für [modellgesteuerte Anwendungen](/power-apps/maker/model-driven-apps/model-driven-app-overview) konzipiert. Im folgenden Abschnitt wird beschrieben, wie Sie eine modellgesteuerte App erstellen.

> [!NOTE]
> Derzeit sind Die Steuerelemente für die Zusammenarbeit nur in der [öffentlichen Entwicklervorschau](~/resources/dev-preview/developer-preview-intro.md) verfügbar.

## <a name="create-a-model-driven-application"></a>Erstellen einer modellgesteuerten Anwendung

1. Öffnen [Siehttps://make.powerapps.com .](https://make.powerapps.com/) oder [https://make.preview.powerapps.com.](https://make.preview.powerapps.com/)

1. Wählen Sie im linken Bereich **"Lösungen** " aus.

1. Wählen Sie **"Neue Lösung**" aus, damit Sie allen Ihren zukünftigen Anpassungen ein Zuhause bieten können.

   :::image type="content" source="../assets/images/collaboration-control/new-solution.png" alt-text="Der Screenshot ist ein Beispiel für die neue Lösung.":::

1. Geben Sie den Namen und Herausgeber Ihrer neuen Lösung an. Diese Lösung wird Ihre benutzerdefinierte Collaboration Manager enthalten.

   :::image type="content" source="../assets/images/collaboration-control/collaboration-manager.png" alt-text="Der Screenshot ist ein Beispiel für den Zusammenarbeits-Manager.":::

1. Wählen Sie **Erstellen** aus

1. Nachdem die Lösung erstellt wurde, wird sie in Ihrer Lösungsliste angezeigt. Wählen Sie Ihre Lösung aus, um sie zu öffnen.

1. Erstellen Sie vor dem Erstellen Ihrer App ein Zuhause für Ihre Daten. wählen Sie **"Neue** > **Tabelle"** aus, um zu beginnen.

     :::image type="content" source="../assets/images/collaboration-control/create-table.png" alt-text="Der Screenshot beschreibt, wie Sie eine neue Tabelle erstellen.":::

1. Geben Sie Ihrer Tabelle einen Namen. Wählen Sie unter **"Erweiterte Optionen****" die Option "Neue Aktivität erstellen"** aus.

   :::image type="content" source="../assets/images/collaboration-control/new-activity.png" alt-text="Der Screenshot beschreibt, wie Sie eine neue Aktivität erstellen.":::

1. Wählen Sie **Speichern** aus.

1. Nachdem Sie ihre Tabelle erstellt haben, können Sie sie anpassen, indem Sie zusätzliche Spalten, Beziehungen und vieles mehr hinzufügen (optional).

1. Jetzt können Sie eine neue modellgesteuerte App erstellen, indem Sie "**Neue** > **appmodellgesteuerte** >  App" auswählen.

   :::image type="content" source="../assets/images/collaboration-control/model-driven-app.png" alt-text="Der Screenshot ist ein Beispiel für die neue modellgesteuerte App.":::

1. Wählen Sie den neuen **Modernen App-Designer (Vorschau)** aus, um die neue App zu öffnen.

   :::image type="content" source="../assets/images/collaboration-control/model-driven-app-blank.png" alt-text="Der Screenshot ist ein Beispiel, in dem die neue modellgesteuerte App leer ist.":::

1. Wählen Sie **"Erstellen" aus.**

1. Geben Sie Ihrer App einen Namen, und wählen Sie **"Erstellen" aus.**

   :::image type="content" source="../assets/images/collaboration-control/collaboration-manager-for-inspection.png" alt-text="Der Screenshot ist ein Beispiel für den Zusammenarbeits-Manager für die Überprüfung.":::

1. Wählen Sie **"Seite hinzufügen" aus.**

1. Wählen Sie **"Tabellenbasierte Ansicht und Formular" aus.**

   :::image type="content" source="../assets/images/collaboration-control/table-based.png" alt-text="Der Screenshot ist ein Beispiel für die tabellenbasierte Ansicht und das Formular.":::

1. Wählen Sie **"Weiter" aus.**

1. Suchen Sie die Tabelle, die Sie zuvor erstellt haben, und wählen Sie sie aus.

   :::image type="content" source="../assets/images/collaboration-control/table-view-form-pages.png" alt-text="Der Screenshot ist ein Beispiel für die Formularseiten der Tabellenansicht.":::

1. Wählen Sie **"Hinzufügen" aus.**

1. Wählen Sie **"Veröffentlichen"** aus, um Ihre App zu speichern und zu veröffentlichen.

1. Wählen Sie **"Wiedergeben** " aus, um Ihre neue App zu testen.

Jetzt haben Sie erfolgreich eine modellgesteuerte App erstellt.

## <a name="add-collaboration-controls-to-your-application"></a>Hinzufügen von Steuerelementen für die Zusammenarbeit zu Ihrer Anwendung

Im Folgenden werden die Schritte zum Hinzufügen von Steuerelementfunktionen für die Zusammenarbeit wie Aufgaben, Besprechungen, Dateien und Notizen zur erstellten App aufgeführt:

1. Um die Registerkarten "Aufgaben", "Besprechungen" und "Notizen" einzuschließen, müssen Sie das Hauptinformationsformular bearbeiten. Kehren Sie zunächst zum Explorer zurück, und wählen Sie Ihre Lösung aus.

1. Wählen Sie die Tabelle aus, die Sie in ["Erstellen einer neuen modellgesteuerten App für Teams](#create-a-new-model-driven-app-with-collaboration-controls-for-teams)" erstellt haben.

1. Wechseln Sie zur Registerkarte "Formulare" für Ihre Tabelle.

     :::image type="content" source="../assets/images/collaboration-control/forms-tab.png" alt-text="Der Screenshot ist ein Beispiel für die Registerkarte &quot;Formulare&quot; für Ihre Tabelle.":::

1. Wählen Sie das Informationsformular des Formulartyps **"Main** " aus, um es im Formular-Designer zu öffnen.

1. Sobald Sie sich im Formular-Designer befinden, drücken und ziehen Sie eine **einspaltige Registerkarte** aus dem Abschnitt **"Komponenten** ".

     :::image type="content" source="../assets/images/collaboration-control/components.png" alt-text="Der Screenshot ist ein Beispiel für die Komponenten von Power-Apps.":::

1. Nachdem Sie die Registerkarte ausgewählt haben, benennen Sie die Registerkarte im Eigenschaftenbereich in "Aufgaben" um.

1. Wählen Sie den Namen der Registerkarte aus, um den vollständigen Abschnitt auszuwählen, und wählen Sie im Eigenschaftenbereich die **Option "Erste Komponente bis zur vollständigen Registerkarte erweitern** " aus. Dies ist erforderlich, da die Steuerelemente für die Zusammenarbeit am besten in vollständigen Registerkartenansichten angezeigt werden.

    :::image type="content" source="../assets/images/collaboration-control/tasks-pane.png" alt-text=" Der Screenshot beschreibt, wie Sie die erste Komponente zur vollständigen Registerkarte auswählen.":::

     :::image type="content" source="../assets/images/collaboration-control/expand-first-component.png" alt-text=" Im Screenshot wird beschrieben, wie Sie die erste Komponente auf die vollständige Registerkarte erweitern.":::

1. Erweitern Sie die Kategorie "Zusammenarbeit (Vorschau)" in der Steuerelementschublade, und ziehen Sie das Steuerelement "Aufgaben" (Vorschau) auf den Abschnitt im Formular "Aufgaben".

     :::image type="content" source="../assets/images/collaboration-control/collab-preview.png" alt-text="Vorschau des Steuerelements auf dem Abschnitt im Aufgabenformular":::

3. Legen Sie die Tabelle auf "Aktivitäten" fest, & wählen Sie "Fertig" aus.

     :::image type="content" source="../assets/images/collaboration-control/select-table-activities.png" alt-text="Wählen Sie die Tabelle für Aktivitäten aus.":::

5. Wählen Sie in den Eigenschaften "Bezeichnung ausblenden" aus.

     :::image type="content" source="../assets/images/collaboration-control/hide-label-properties.png" alt-text="Bezeichnung ausblenden auswählen":::

1. Das Aufgabensteuerelement wird jetzt angezeigt.

     :::image type="content" source="../assets/images/collaboration-control/new-collab-control.png" alt-text="Anzeige des Aufgabensteuerelements":::

1. Wiederholen Sie die Aufgabenschritte, um Ihrer App Genehmigungen, Dateien, Besprechungen und Notizensteuerelemente hinzuzufügen.
1. Nachdem alle Steuerelemente hinzugefügt wurden, werden die unten im Formular-Designer gerenderten Steuerelemente angezeigt. Wenn ein Steuerelement nicht im Formular-Designer gerendert wird, z. B. ein leeres Formular angezeigt wird, führen Sie Ihre App in Power Apps aus, und das Vorhandensein einer "Configure"-Seite oder eines "leeren Zustands" bedeutet, dass das Steuerelement erfolgreich hinzugefügt wurde.

     :::image type="content" source="../assets/images/collaboration-control/new-collab-approval.png" alt-text="Steuerelemente-Formular-Designer":::

1. Sie können Ihre Power-App jetzt in Power Apps ausführen, indem Sie sie auswählen.

     :::image type="content" source="../assets/images/collaboration-control/collaboration-manager-for-inspections-power-apps.png" alt-text="Zusammenarbeits-Manager für Inspektionen":::

1. Erstellen Sie einen neuen Datensatz, indem Sie **"+Neu** " auswählen und dann den Datensatz öffnen.

     :::image type="content" source="../assets/images/collaboration-control/power-apps-open-the-record.png" alt-text="Der Screenshot ist ein Beispiel für die Power-Apps, die den Datensatz öffnen.":::

1. Jetzt können Sie Ansichten für jede Registerkarte sehen, die der folgenden Abbildung ähnlich aussehen:

     :::image type="content" source="../assets/images/collaboration-control/tabs.png" alt-text="Der Screenshot ist ein Beispiel für die Aufgaben.":::

     > [!TIP]
     > Die Steuerelemente sind erst sichtbar, nachdem ein Datensatz in der Anwendung gespeichert wurde. Wenn die Steuerelementregisterkarten in Ihrem Datensatz nicht angezeigt werden, versuchen Sie, Ihren Browser zu aktualisieren oder die App über Power Apps erneut zu veröffentlichen.

Jetzt haben Sie der Anwendung erfolgreich die Steuerelemente für die Zusammenarbeit hinzugefügt. Sie können Ihre Anwendung jetzt in Power Apps ausführen und die Steuerelemente starten. Da die Einstellungen noch nicht konfiguriert wurden, können Sie erst Dann Entitäten wie Aufgaben oder Besprechungen erstellen.

## <a name="define-settings-for-your-collaboration"></a>Definieren von Einstellungen für Ihre Zusammenarbeit

Sie können Einstellungen für Steuerelemente für die Zusammenarbeit für die Unternehmensentität definieren, z. B. die Tabelle, die in [einer neuen modellgesteuerten App](#create-a-new-model-driven-app-with-collaboration-controls-for-teams) erstellt wurde.

Sie können folgende Einstellungen anwenden:

|Einstellungen|Verwendet von|
|---|---|
|Gruppen-ID|Aufgaben, interne Besprechungen, Genehmigungen.|
|Bookings-Geschäfts-ID|Externe Besprechungen mit Bookings |
|Website-ID|SharePoint-Dateien |
|Laufwerk-ID|SharePoint-Dateien|

> [!NOTE]
> Einstellungen sind crtical, um Ihre App zu starten, also stellen Sie sicher, dass Sie die Schritte wie vorgeschlagen ausführen. Wenn Beim Starten und Speichern der Steuerelemente Probleme auftreten, überprüfen Sie die Werte erneut.

Sie können die Gruppen-ID abrufen, indem Sie ein neues Team erstellen oder ein vorhandenes Team in Microsoft Teams verwenden, um Ihre Anwendung zu hosten und Einstellungsvariablen zu erstellen.

Informationen zum Erstellen eines neuen Teams finden [Sie unter "Von Grund auf neu erstellen"](https://support.microsoft.com/en-us/office/create-a-team-from-scratch-174adf5f-846b-4780-b765-de1a0a737e2b).

Verwenden Sie die folgenden Anweisungen, um die Gruppen-ID Ihres Teams-Teams für Genehmigungen, Aufgaben und interne Besprechungen abzurufen:

1. Suchen Sie Ihr Team in Ihrer Teamliste.

1. Wählen Sie die Ellipse **...** und dann **"Link zum Team** abrufen" aus.

     :::image type="content" source="../assets/images/collaboration-control/get-link.png" alt-text="Der Screenshot beschreibt, wie Die Verknüpfung mit dem Team abgerufen wird.":::

1. Kopieren Sie den Link, und notieren Sie den Wert von `groupId` der URL. Sie verwenden diesen Wert zu einem späteren Zeitpunkt, während Sie die Einstellungen Ihrer Lösung definieren.

     `https://teams.microsoft.com/l/team/19%3akk_TuKhjXu92yJvg4TZ10S6rouLSCgvHIb5NOOTfRjg1%40thread.tacv2/conversations?groupId=4310f270-1aa5-4089-99f3-47eb3b4d69ad&tenantId=b699419b-e0df-47e3-9909-24076fdcf68b`

Verwenden Sie die folgenden Anweisungen, um die SharePoint-Website-ID und Laufwerk-ID für Dateien abzurufen:

1. Um das Steuerelement "Dateien" zu verwenden, müssen Sie eine vorhandene SharePoint-Website konfigurieren oder eine neue SharePoint-Website erstellen. Informationen zum Erstellen einer neuen Website finden [Sie unter Erstellen einer Website](/sharepoint/create-site-collection).

1. Rufen Sie nun die Einstellungswerte von Website-ID und Laufwerk-ID ab, die mithilfe der Details auf Ihrer SharePoint-Website aufgerufen werden können.

     1. **Website-ID**: Melden Sie sich mit [dem Graph-Explorer](https://developer.microsoft.com/graph/graph-explorer) an, und erteilen Sie Berechtigungen für Directory.ReadWrite.All und User.ReadWrite.All

         :::image type="content" source="../assets/images/collaboration-control/graph-permissions.png" alt-text="Der Screenshot ist ein Beispiel für den Graph-Explorer.":::

     1. Stellen Sie sicher, dass Sie den Hostnamen durch Ihren Hostnamen und den relativen Pfad zum Websitepfad ersetzen, und führen Sie einen Graph-Aufruf an `https://graph.microsoft.com/v1.0/sites/{hostname}:/{relative-path-to-site}`. Es folgt ein Beispiel:
         1. Wenn Ihre Website-URL = `https://myhostname.sharepoint.com/sites/MySiteName`
         1. Hostname = `myhostname.sharepoint.com`
         1. Relativer Pfad zur Website = `sites/MySiteName`

              :::image type="content" source="../assets/images/collaboration-control/graph-call.png" alt-text="Der Screenshot ist ein Beispiel für den Graph-Aufruf.":::

            Graph-Aufruf wäre, `https://graph.microsoft.com/v1.0/sites/myhostname.sharepoint.com:/sites/MySiteName`.

     1. Die empfangene Antwort ist ein JSON-Objekt, das die Website darstellt, z. B. Die Website-ID wäre `abcdef.sharepoint.com,0abe7394-6fce-4dcc-9884-7eaceb48cd41,8cb86762-16cd-495e-87cb-893cfdf94054`.

     1. Speichern Sie den Wertparameter für die Website-ID.

     1. **Laufwerk-ID**: Melden Sie sich mit dem [Graph-Explorer](https://developer.microsoft.com/graph/graph-explorer) an, und führen Sie den Graph-Aufruf `https://graph.microsoft.com/v1.0/sites/{site-id}/drives` mit dem Wert der Zuvor gespeicherten Website-ID aus.

     1. Eine JSON-Antwort wird mit einem Parameterwert vom Typ Array oder Liste von Laufwerksobjekten zurückgegeben. Suchen Sie im Json-Objekt nach dem Json-Objekt, dessen Name-Parameter dem Namen Ihrer Dokumentbibliothek entspricht. Speichern Sie den Wert des Laufwerks-ID-Parameters.

Um Besprechungen mit Benutzern außerhalb Ihrer Organisation zu erstellen, z. B. Kunden, und um virtuelle Besuchsfeatures in Ihrer App zu verwenden, müssen Sie ein Bookings-Unternehmen bereitstellen. Weitere Informationen finden Sie [unter Microsoft Bookings](/microsoft-365/bookings/bookings-overview?view=o365-worldwide&preserve-view=true).

## <a name="add-settings-to-your-collaboration-manager-app"></a>Hinzufügen von Einstellungen zu Ihrer Collaboration Manager-App

Um Einstellungen anzuwenden und die Features für die Zusammenarbeit Ihrer App in Power Apps zu erkunden, öffnen Sie die Anwendung, die Sie zuvor erstellt haben. Es wird eine Ansichtsseite angezeigt, auf der Sie die vorhandenen Datensätze auswählen oder einen neuen Datensatz erstellen können. So beginnen Sie mit dem Öffnen oder Erstellen eines Datensatzes.

Sie müssen die Einstellungs-IDs hinzufügen, die Sie zuvor für Ihre Anwendung gespeichert haben.

|Einstellungen|Verwendet von|
|---|---|
|Gruppen-ID|Aufgaben, interne Besprechungen, Genehmigungen.|
|Bookings-Geschäfts-ID|Externe Besprechungen mit Bookings |
|Website-ID|SharePoint-Dateien |
|Laufwerk-ID|SharePoint-Dateien|

### <a name="add-settings-for-tasks-meetings-and-files"></a>Hinzufügen von Einstellungen für Aufgaben, Besprechungen und Dateien

1. Starten Sie ein Steuerelement, und Sie können ein Fenster wie folgt anzeigen:

     :::image type="content" source="../assets/images/collaboration-control/launch-window.png" alt-text="Der Screenshot ist ein Beispiel für das Steuerelementfenster.":::

1. Wählen Sie **"Konfigurieren"** aus, und wechseln Sie zur Registerkarte "Allgemein", um die Gruppen-ID hinzuzufügen.

     :::image type="content" source="../assets/images/collaboration-control/groupid-general.png" alt-text="Der Screenshot beschreibt, wie Die Gruppen-ID auf der Registerkarte &quot;Allgemein&quot; hinzugefügt wird.":::

1. Öffnen Sie die Registerkarte "Dateien", um die Website-ID und laufwerks-ID hinzuzufügen.

     :::image type="content" source="../assets/images/collaboration-control/files-tab.png" alt-text="Der Screenshot beschreibt, wie Sie die Website-ID und Laufwerk-ID auf der Registerkarte &quot;Dateien&quot; hinzufügen.":::

Für das Notizensteuerelement ist kein Einstellungswert erforderlich. Jetzt können Sie Entitäten wie Aufgaben und Besprechungen in Ihrer Anwendung erstellen. Wenn Beim Starten und Speichern der Steuerelemente Probleme auftreten, überprüfen Sie die Einstellungswerte erneut.

## <a name="explore-your-new-collaboration-manager-app"></a>Entdecken Sie Ihre neue Collaboration Manager-App

In den folgenden Abschnitten erfahren Sie, wie Sie die Steuerelemente "Aufgabe", "Notizen", "Besprechungen", "Dateien" und "Genehmigungen" verwenden.

### <a name="create-tasks"></a>Aufgaben erstellen

Erkunden Sie die Zusammenarbeit auf der Registerkarte "Aufgaben", indem Sie die Registerkarte "Aufgaben" auswählen, auf der eine leere Seite geöffnet wird, auf der Benutzer alle relevanten Aufgaben hinzufügen können, die sie ausführen müssen.

1. Um eine neue Aufgabe für das Team zu erstellen, wählen Sie **"Aufgabe hinzufügen"** aus. Es wird ein Dialogfeld geöffnet, in dem Sie Einzelheiten zu der Aufgabe angeben und sie den relevanten Personen im Team zuweisen und "Speichern" auswählen können.

     :::image type="content" source="../assets/images/collaboration-control/add-task.png" alt-text="Der Screenshot beschreibt, wie Sie eine Aufgabe hinzufügen.":::

1. Der gespeicherte Vorgang wird in der Aufgabenliste angezeigt.

1. Da alle Aufgaben von Microsoft Planner unterstützt werden. Benutzer können die Aufgaben-App in Microsoft Teams verwenden, um alle zugewiesenen Aufgaben anzuzeigen. Um zu beginnen, wählen Sie Auslassungszeichen **aus...** im linken Bereich von Teams. Suchen sie Aufgaben nach Planner und Aufgaben, und wählen Sie sie aus.

     :::image type="content" source="../assets/images/collaboration-control/tasks-planner.png" alt-text="Der Screenshot ist ein Beispiel für die Aufgaben von Planner und To Do.":::

1. Nach dem Öffnen der App "Aufgaben nach Planner" und "Aufgaben" können Benutzer alle Aufgaben, die in Ihrer App erstellt wurden, im Abschnitt **"Mir zugewiesen"** der App anzeigen. Benutzer können auch die Details einer Aufgabe anzeigen, Anlagen hinzufügen und als erledigt markieren.

### <a name="create-notes"></a>Erstellen von Notizen

Um eine Notiz zu erstellen, wählen Sie die Registerkarte **"Notizen** " aus Ihrer App aus, die zu einem leeren Bildschirm umleitet, auf dem Benutzer alle relevanten Informationen bereitstellen können. Um eine neue Notiz hinzuzufügen, wählen Sie **"Neue Notiz" aus**.
Nachdem Sie relevante Details in den Notizen hinzugefügt haben, wählen Sie **"Speichern"** aus.

### <a name="create-meetings"></a>Besprechungen erstellen

Wählen Sie die Registerkarte " **Besprechungen** " in einem Datensatz aus, um sowohl interne als auch externe Besprechungen zu planen.

Um eine interne Besprechung zu planen, wählen Sie die Dropdownliste neben der Schaltfläche " **Neue Besprechung** " und dann " **Interne Besprechung"** aus.

:::image type="content" source="../assets/images/collaboration-control/new-meeting-tab.png" alt-text="Der Screenshot beschreibt, wie Sie interne Besprechungen planen.":::

> [!NOTE]
>
> Kundenbuchung ist aktiviert, wenn Sie Microsoft Booking mit einer gültigen Einstellung für Ihre App konfiguriert haben.

Im Dialogfeld **"Neue Besprechung** " können Benutzer relevante Informationen zur Besprechung bereitstellen und **"Speichern"** auswählen. Die Besprechung wird in der Besprechungsliste angezeigt.

:::image type="content" source="../assets/images/collaboration-control/new-meeting.png" alt-text="Der Screenshot beschreibt, wie Sie eine neue Besprechung planen.":::

Um eine externe Besprechung mit dem Kunden zu planen, wählen Sie die Dropdownliste neben der Schaltfläche " **Neue Besprechung** " und dann **"Kundenbuchung**" aus. Wenn die Option **"Kundenbuchung**" in der Dropdownliste "**Neue Besprechung**" nicht verfügbar ist, vergewissern Sie sich, dass die App in den Einstellungen für Microsoft Bookings konfiguriert ist und der Benutzer über die Rolle "Bookings-Administrator" verfügt. Weitere Informationen finden Sie unter ["Hinzufügen von Mitarbeitern zu Bookings](/microsoft-365/bookings/add-staff?view=o365-worldwide&preserve-view=true)". Sie können zusätzliche Buchungstypen hinzufügen, indem Sie zusätzliche Dienste in Ihrem Bookings-Unternehmen hinzufügen.

:::image type="content" source="../assets/images/collaboration-control/customer-booking.png" alt-text="Der Screenshot beschreibt, wie Sie Kundenbuchungen planen.":::

Benutzer können sowohl interne Besprechungen als auch Kundenbuchungen in ihrer Besprechungsliste sehen. Nachdem die Besprechung gestartet wurde, können Benutzer teilnehmen, indem sie die Schaltfläche " **Teilnehmen** " auswählen, die die Besprechung direkt in Microsoft Teams öffnet.

Da die Besprechungen von Outlook unterstützt werden, können Benutzer entweder zu Bookings oder Outlook-Kalender wechseln, um alle Besprechungen in einem einzigen Kalender anzuzeigen. Interne Besprechungen werden im freigegebenen Kalender aufgelistet.

Es folgen die Schritte zum Hinzufügen eines freigegebenen Kalenders zu Outlook (optional):

1. Wählen Sie im Menüband auf der Registerkarte "Start" im Abschnitt "Kalender verwalten" die Option "Kalender öffnen" > "Freigegebenen Kalender öffnen" aus.

1. Geben Sie im Dialogfeld "Freigegebenen Kalender öffnen" den Namen der Person ein. Wählen Sie die gesuchte Person und dann OK aus.

Im linken Bereich sollte unter "Freigegebene Kalender" nun ein zusätzlicher Kalender mit dem Namen der Person angezeigt werden.

:::image type="content" source="../assets/images/collaboration-control/customer-booking.png" alt-text="Der Screenshot beschreibt, wie Sie Kundenbuchungen planen.":::

### <a name="add-files"></a>Dateien hinzufügen

Öffnen Sie die Registerkarte "**Dateien**" in Ihrer Anwendung, und wählen Sie "**Hochladen**" aus, um Dateien von OneDrive for Business oder von Ihrem Computer hochzuladen. Wenn eine Datei erfolgreich hochgeladen wurde, wird die Hauptlistenansicht automatisch aktualisiert, um die Dateien in der Liste anzuzeigen.

:::image type="content" source="../assets/images/collaboration-control/meeting-calendar.png" alt-text="Der Screenshot beschreibt das Öffnen des freigegebenen Kalenders.":::

### <a name="approvals"></a>Genehmigungen

Mit Genehmigungen können Benutzer die Abmeldung von anderen Personen anfordern, wenn sie in einem Datensatz arbeiten. Fordern Sie beispielsweise eine Genehmigung an, um eine Aufgabe auszuführen oder einen Datensatz zu schließen.

1. Wechseln Sie zur Registerkarte **"Genehmigungen** " der Anwendung.

1. Wenn keine Genehmigungsanforderungen vorhanden sind, wird den Benutzern der folgende Bildschirm angezeigt.

      :::image type="content" source="../assets/images/collaboration-control/no-approvals.png" alt-text="Der Screenshot ist ein Beispiel, in dem keine Genehmigungsanforderungen angezeigt werden.":::

1. Wählen Sie die **Neue Genehmigungsanforderung** aus, um das Genehmigungsanforderungsformular zu öffnen.

      :::image type="content" source="../assets/images/collaboration-control/approval-request-form.png" alt-text="Der Screenshot ist ein Beispiel für das neue Genehmigungsanforderungsformular.":::

1. Füllen Sie im Genehmigungsanforderungsformular die erforderlichen Felder aus, und wählen Sie **"Senden**" aus, wodurch eine Anforderung erstellt und der Liste hinzugefügt wird.

      :::image type="content" source="../assets/images/collaboration-control/approvals-list.png" alt-text="Der Screenshot ist ein Beispiel für die Liste der Genehmigungen.":::

1. Wählen Sie die Genehmigung aus, um die Details anzuzeigen.

Weitere Informationen zu Genehmigungen finden Sie unter [Erstellen einer Genehmigung](https://support.microsoft.com/en-us/office/create-an-approval-6548a338-f837-4e3c-ad02-8214fc165c84).
