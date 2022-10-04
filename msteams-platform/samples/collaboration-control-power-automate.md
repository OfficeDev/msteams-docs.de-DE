---
title: Power Automate in der Steuerelement-App für die Zusammenarbeit
author: surbhigupta
description: In diesem Modul erfahren Sie mehr über Power Automate in der Steuerelement-App für die Zusammenarbeit in Microsoft Teams und wie Sie eine Azure-App erstellen.
ms.localizationpriority: medium
ms.author: v-npaladugu
ms.topic: conceptual
ms.openlocfilehash: 975d5fdd923d96ae1daa649795259a05904b6921
ms.sourcegitcommit: f2ac771cbd608e872604e9ac8ffec2d08f55ee1a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/04/2022
ms.locfileid: "68373052"
---
# <a name="power-automate"></a>Power Automate

Power Automate kann verwendet werden, um Workflows in Ihrer Collaboration Manager Anwendung zu automatisieren. Erstellen Sie beispielsweise automatisch Aufgaben, wenn ein neuer Datensatz erstellt wird.

Der Connector für die Zusammenarbeitssteuerung ermöglicht Entwicklern den Zugriff auf Steuerelement-APIs für die Zusammenarbeit durch Trigger oder Aktionen in automatisierten Workflows in Microsoft Power Automate-, Microsoft Power Apps- und Azure Logic-Apps.

> [!NOTE]
> Derzeit sind Die Steuerelemente für die Zusammenarbeit nur in der [öffentlichen Entwicklervorschau](~/resources/dev-preview/developer-preview-intro.md) verfügbar.

In dieser Version ermöglicht der Connector Herstellern das Einrichten von Triggern:

1. Wenn eine Zusammenarbeitssitzung erstellt wird.
1. Wenn eine Planner-Aufgabe erstellt oder geändert wird.

Es enthält auch eine Reihe von APIs und Aufgaben für die Zusammenarbeitssteuerelemente, die mit einem Fluss aufgerufen werden können. Die Connectoraktionen finden Sie in der Workflowschrittauswahl. Der Connector selbst befindet sich auf benutzerdefinierten Connectors mit konfigurierbaren Optionen. Um den Connector in Ihrer Lösung zu verwenden, muss ein Azure-App erstellt werden, dem Ihre Umgebung vertraut, um die Flüsse auszuführen.

## <a name="create-an-azure-app"></a>Erstellen eines Azure-App

Melden Sie sich im [Azure-Portal](https://ms.portal.azure.com/#home) für die Azure Active Directory-Verwaltung mit den folgenden Schritten bei Ihrem Konto mit den entsprechenden Berechtigungen an, um Ihrer Umgebung eine Benutzeranwendung hinzuzufügen:

1. Wählen Sie auf der Startseite von Azure-Portal **Azure Active Directory** aus. Wählen Sie in Azure Active Directory die Dropdownliste für **"Hinzufügen"** und dann " **App-Registrierung**" aus.

   :::image type="content" source="../assets/images/collaboration-control/azure-active-directory-home-portal.png" alt-text="Screenshot ist ein Beispiel, das zeigt, wie Sie eine neue App-Registrierung hinzufügen.":::

   :::image type="content" source="../assets/images/collaboration-control/new-app-registration.png" alt-text="Screenshot ist ein Beispiel, das zeigt, wie Sie eine neue App-Registrierung hinzufügen.":::

1. Legen Sie in der App-Registrierung Ihren Anwendungsnamen fest, und fügen Sie den Webumleitungs-URI hinzu `https://global.consent.azure-apim.net/redirect`.

   :::image type="content" source="../assets/images/collaboration-control/register-an-application.png" alt-text="Screenshot ist ein Beispiel, das zeigt, wie eine Anwendung registriert wird.":::

1. Wählen Sie im Abschnitt "Implizite Gewährung und Hybridflüsse" sowohl Zugriffstoken als auch ID-Token aus.

   :::image type="content" source="../assets/images/collaboration-control/authorisation-endpoint-tokens.png" alt-text="Screenshot ist ein Beispiel für die Token und ID-Token.":::

1. Wählen Sie im linken Bereich "API-Berechtigung" und dann **"Berechtigung hinzufügen"** aus, und suchen Sie dann nach der **Berechtigung "Dynamisches CRM** ".

   :::image type="content" source="../assets/images/collaboration-control/dynamic-crm.png" alt-text="Screenshot ist ein Beispiel, das zeigt, wie Sie eine Berechtigung hinzufügen.":::

1. Stellen Sie sicher, **dass Sie nach** dem Auswählen von Dynamics CRM user_impersonation in "Berechtigungen" auswählen.

   :::image type="content" source="../assets/images/collaboration-control/admin-consent-required.png" alt-text="Screenshot ist ein Beispiel zum Aktivieren des Kontrollkästchens user_impersonation.":::

1. Fügen Sie auf der Seite "Zertifikate & Geheime Schlüssel" einen **neuen geheimen Clientschlüssel** hinzu, und speichern Sie den Wert zur späteren Verwendung beim Einrichten der Connectorsicherheit.

   :::image type="content" source="../assets/images/collaboration-control/copy-new-secret-value.png" alt-text="Screenshot ist ein Beispiel zum Kopieren eines neuen geheimen Werts.":::

1. Kopieren Sie auf der Seite "Anwendungsübersicht **" die Anwendungs-ID (Client-ID),** und speichern Sie sie zur späteren Verwendung, während Sie die Connectorsicherheit einrichten.

   :::image type="content" source="../assets/images/collaboration-control/application-client-ID.png" alt-text="Screenshot ist ein Beispiel zum Speichern der Client-ID":::

Jetzt ist Ihre Azure-App festgelegt, und Sie müssen sie als Benutzeranwendung in Ihrer Umgebung hinzufügen.

## <a name="add-azure-app-to-power-automate-environment"></a>Hinzufügen einer Azure-App zur Power Automate-Umgebung

1. Öffnen Sie das Power Apps-Portal, wählen Sie in der oberen rechten Ecke **einstellungen** aus, und öffnen **Sie Admin Mitte**.

   :::image type="content" source="../assets/images/collaboration-control/power-apps-interface.png" alt-text="Screenshot ist ein Beispiel für die Power Apps-Schnittstelle.":::

1. Wählen Sie im Admin Center im linken Bereich die Option **"Umgebung** " aus, und wählen Sie Ihre Umgebung in der Liste aus, der Sie die Connector-App hinzufügen möchten.

   :::image type="content" source="../assets/images/collaboration-control/power-platform-admin-center.png" alt-text="Screenshot ist ein Beispiel, das zeigt, wie Sie eine Connector-App hinzufügen.":::

1. Wählen Sie auf der Seite "Umgebungsdetails" **die Option "Einstellungen"** aus.

   :::image type="content" source="../assets/images/collaboration-control/settings-environment.png" alt-text="Screenshot ist ein Beispiel, das zeigt, wie Einstellungen ausgewählt werden.":::

1. Wählen Sie auf der Einstellungsdetailseite **den Abschnitt "Benutzer + Berechtigungen** " und dann **"Anwendungsbenutzer"** aus.

   :::image type="content" source="../assets/images/collaboration-control/users-link.png" alt-text="Screenshot ist ein Beispiel für den Anwendungsbenutzerlink.":::

1. Wählen Sie auf der Seite "App-Benutzer" die Option **"+ Neuer App-Benutzer**" aus. **Ein neues App-Benutzerfenster** erstellen wird angezeigt.

   :::image type="content" source="../assets/images/collaboration-control/new-app-user.png" alt-text="Screenshot ist ein Beispiel für den neuen App-Benutzer.":::

1. Wählen Sie **eine App aus, und fügen Sie sie hinzu**.

   :::image type="content" source="../assets/images/collaboration-control/create-new-app-user.png" alt-text="Screenshot ist ein Beispiel zum Erstellen eines neuen App-Benutzers.":::

1. Wählen Sie Ihre App im Suchfeld aus, und wählen Sie erneut "Hinzufügen" aus.

   :::image type="content" source="../assets/images/collaboration-control/add-app-aad.png" alt-text="Screenshot ist ein Beispiel, das zeigt, wie Sie eine App aus Azure Active Directory hinzufügen.":::

Nachdem die App hinzugefügt wurde, legen Sie die **Geschäftseinheit** und **die Sicherheitsrollen** auf Ihre Connectoranwendung fest. Wählen Sie **"Erstellen"** aus, und Ihre App befindet sich in der Liste. Wenn der App-Benutzer in der Umgebung festgelegt ist, können wir mit der benutzerdefinierten Connectorkonfiguration fortfahren.

## <a name="custom-connector-configuration"></a>Benutzerdefinierte Connectorkonfiguration

1. Öffnen Sie PowerApps oder Power Automate, und wählen Sie das Menü **"Benutzerdefinierte Connectors** " aus. Wählen Sie **"Bearbeiten"** für den Connector für die Zusammenarbeit aus.

   :::image type="content" source="../assets/images/collaboration-control/collaboration-connector.png" alt-text="Der Screenshot zeigt, wie Sie das Menü &quot;Bearbeiten für benutzerdefinierten Connector&quot; auswählen.":::
1. Geben Sie auf der Registerkarte "Allgemeine Informationen" den Host mit der Adresse der Dynamic 365-Instanzdomäne (ohne https://) ein.

   :::image type="content" source="../assets/images/collaboration-control/general-information.png" alt-text="Screenshot ist ein Beispiel, das die allgemeinen Informationen zeigt.":::

1. Geben Sie auf der Registerkarte "Sicherheit" die folgenden Eingaben ein:

   * Geheimer Clientschlüssel: Verwenden Sie den gespeicherten Wert für den geheimen App-Schlüssel in der Eingabe.
   * Client-ID: Ihre Azure-App (Client-ID).
   * Ressourcen-URL: Die URL Ihrer Dynamic 365-Instanz (`https://org.crm.dynamics.com/`).
   * Bereich: Identisch mit oben mit. Standardsuffix (`https://org.crm.dynamics.com/.default`).

   :::image type="content" source="../assets/images/collaboration-control/dynamic-365-instance.png" alt-text="Screenshot ist ein Beispiel für die Dynamic 365-Instanz.":::

1. Wählen Sie **"Connector aktualisieren"** aus, um die Änderungen zu speichern und dem Fluss das Herstellen von Verbindungen zu ermöglichen.

   :::image type="content" source="../assets/images/collaboration-control/custom-connector.png" alt-text="Screenshot ist ein Beispiel für den benutzerdefinierten Connector.":::

## <a name="how-to-invoke-the-connector"></a>So wird's gemacht: Aufrufen des Connectors  

Trigger und Aktionen sind mit konfigurierbarer Eingabe und Ausgabe als Workflowschritt vordefiniert. Hinzufügen des Workflowschritts zur richtigen Workflowposition mit korrekter Eingabe- und Ausgabekonfiguration, um zu definieren, wann der Trigger oder die Aktion aufgerufen werden soll.

  :::image type="content" source="../assets/images/collaboration-control/invoke-the-connector.png" alt-text="Screenshot ist ein Beispiel, das zeigt, wie der Connector aufgerufen wird.":::

### <a name="triggers-and-actions-supported-with-connector"></a>Trigger und Aktionen, die vom Connector unterstützt werden

Die folgenden Trigger und Aktionen werden in einem Fluss unterstützt:

* **Trigger**

  1. Wenn eine Zusammenarbeitssitzung erstellt wird.

      :::image type="content" source="../assets/images/collaboration-control/colab-session-created-preview.png" alt-text="Screenshot der erstellten Zusammenarbeitssitzung.":::

      **Umfang:** Ein Bereich, der begrenzt werden soll, welche Zeilen den Fluss auslösen können.

      **Ausführen als:** Der ausführenden Benutzer für Schritte, in denen Aufruferverbindungen verwendet werden.

  1. Wenn eine Aufgabe erstellt oder geändert wird

      :::image type="content" source="../assets/images/collaboration-control/task-created.png" alt-text="Screenshot ist ein Beispiel, das zeigt, dass die Aufgabe erstellt oder geändert wurde.":::

      Standardmäßig ist die Auslöser-Planner-Aufgabe deaktiviert und wird nicht ausgelöst. Um es zu aktivieren, muss der Mandantenadministrator die folgenden Schritte ausführen:

      1. Erstellen Sie ein Supportticket unter dem Pfad Power Apps/Zusammenarbeitssteuerelemente/Einstellungen.
      1. Fordern Sie an, dass Ihre Umgebung für den Connector für die Zusammenarbeit aktiviert ist und stellt Ihre Umgebungs-URL (bevorzugt) oder Organisations-ID bereit.  
      1. Sie können der Supportanfrage den folgenden Beispieltext hinzufügen: "Umgebungs-URL aktivieren: `url` für den Connector für die Zusammenarbeit".
      1. Informationen zum Öffnen eines Supporttickets finden [Sie unter "Hilfe + Support abrufen](/power-platform/admin/get-help-support)"

* **Aktionen**

  1. Zusammenarbeitssitzung starten

      :::image type="content" source="../assets/images/collaboration-control/begin-collab-session.png" alt-text="Screenshot ist ein Beispiel, das zeigt, wie Sie mit der Zusammenarbeitssitzung beginnen.":::

     Diese Schrittaktion erstellt eine neue Zusammenarbeitssitzung für Ihre dataverse-Geschäftsentität:

      * **Anwendungsname:** Der Name der zugeordneten Anwendung könnte beispielsweise "Collaboration Manager für Darlehen" oder "Collaboration Manager für die Abschlussprüfung" sein.
      * **Name der Zusammenarbeitsstammentität:** Der Typ des Anwendungsdatensatzes (Tabellenname) könnte z. B. "msfi_loanapplication" für eine Collaboration Manager für die Kreditanwendung sein.
      * **Stammentitäts-ID der Zusammenarbeit:** Die ID des zugeordneten Anwendungsdatensatzes, z. B. die ID eines Kreditantragsdatensatzes.  

      ***Erweiterte Optionen***

      **Metadaten (erweitert):** Fügt Metadaten für eine Zusammenarbeitssitzung hinzu.

        * **OData-Typ:** Dieses Feld muss angegeben werden, wenn der andere Schlüssel/Wert festgelegt ist und genau #Microsoft.Dynamics.CRM.m365_collaborationmetadata übereinstimmen muss.
        * **Schlüssel:** Schlüssel, der dem Metadatenattribut zugeordnet ist.
        * **Wert:** Wert, der dem Metadatenattribut zugeordnet ist.

  1. Abrufen der Zusammenarbeitssitzung

      ::image type="content" source=".. /assets/images/collaboration-control/retrieve-collab-session.png" alt-text="Screenshot ist ein Beispiel, das zeigt, wie die Zusammenarbeitssitzung abgerufen wird.":::

     Diese Schrittaktion gibt die Zusammenarbeitssitzung zurück, die den bereitgestellten Eingaben entspricht:

     * **Anwendungsname:** Der Anwendungsnamenkontext für die Zusammenarbeitssitzung.
     * **Stammentitäts-ID der Zusammenarbeit:** Die Geschäftsentitäts-ID für die Zusammenarbeitssitzung.  
     * **Name der Zusammenarbeitsstammentität:** Der Unternehmensentitätstyp für die Zusammenarbeitssitzung.

  1. Zusammenarbeitssitzung aktualisieren

      :::image type="content" source="../assets/images/collaboration-control/update-collab-session.png" alt-text="Screenshot ist ein Beispiel, das zeigt, wie Sie die Zusammenarbeitssitzung aktualisieren.":::

     Diese Schrittaktion aktualisiert eine vorhandene Zusammenarbeitssitzung:

     * **Stamm-ID der Zusammenarbeit:** Die GUID für die Zielzusammenarbeitssitzung/den Stammdatensatz.
     * **Stammentitäts-ID der Zusammenarbeit:** Die Geschäftsentitäts-ID, auf die sich die Zusammenarbeitssitzung bezieht.
     * **Name der Zusammenarbeitsstammentität:** Der Name des Unternehmensentitätstyps, auf den sich die Zusammenarbeitssitzung bezieht.

     ***Erweiterte Optionen:***

      **Metadaten erstellen (erweitert):** Fügt einem Datensatz einer Zusammenarbeitssitzung weitere Metadaten hinzu.

      * **OData-Typ:** Dieses Feld muss angegeben werden, wenn der andere Schlüssel/Wert festgelegt ist und genau #Microsoft.Dynamics.CRM.m365_collaborationmetadata übereinstimmen muss.
      * **Schlüssel:** Schlüssel, der dem Metadatenattribut zugeordnet ist.
      * **Wert:** Wert, der dem Metadatenattribut zugeordnet ist.

      **Aktualisieren von Metadaten (erweitert):** Aktualisierungen vorhandenen Metadaten in einem Sitzungsdatensatz für die Zusammenarbeit.

      * **OData-Typ:** Dieses Feld muss angegeben werden, wenn der andere Schlüssel/Wert festgelegt ist und genau #Microsoft.Dynamics.CRM.m365_collaborationmetadata übereinstimmen muss.
      * **Schlüssel:** Schlüssel, der dem zu aktualisierenden Metadatenattribut zugeordnet ist.
      * **Wert:** Wert, der dem Metadatenattribut zugeordnet ist.

      **Metadaten löschen (erweitert):** Entfernt alle vorhandenen Metadaten in einem Datensatz einer Zusammenarbeitssitzung.

      * **OData-Typ:** Dieses Feld muss angegeben werden, wenn der andere Schlüssel/Wert festgelegt ist und genau #Microsoft.Dynamics.CRM.m365_collaborationmetadata übereinstimmen muss.
      * **Schlüssel:** Schlüssel, der dem zu entfernenden Metadatenattribut zugeordnet ist.

  1. Zuordnen einer Zuordnung zur Zusammenarbeit (extern)

      :::image type="content" source="../assets/images/collaboration-control/associate-collab-map.png" alt-text="Screenshot ist ein Beispiel, das zeigt, wie Sie eine Zuordnung zur Zusammenarbeitszuordnung erstellen.":::

     Diese Schrittaktion erstellt eine Zuordnung einer externen Zusammenarbeitsentität (außerhalb von Dataverse) mit Ihrer Zusammenarbeitssitzung:

     * **Stamm-ID der Zusammenarbeit:** Der eindeutige Bezeichner der Zusammenarbeitssitzung, der einer Entität für die Zusammenarbeit zugeordnet werden soll.
     * **Externe ID der Zusammenarbeitstabelle:** Die externe Ressourcen-ID für die Zusammenarbeit, die zugeordnet werden soll.
     * **Name der Zusammenarbeitszuordnungsentität:** Der Name des externen Entitätstyps für die Zusammenarbeit, der zugeordnet werden soll.

     ***Erweiterte Optionen:***

     **Metadaten:** Fügen Sie Metadaten für eine Zuordnung zur Zusammenarbeit hinzu.
     * **OData-Typ:** Dieses Feld muss angegeben werden, wenn der andere Schlüssel/Wert festgelegt ist und genau #Microsoft.Dynamics.CRM.m365_collaborationmetadata übereinstimmen muss.
     * **Schlüssel:** Schlüssel, der dem Metadatenattribut zugeordnet ist.
     * **Wert:** Wert, der dem Metadatenattribut zugeordnet ist.

  1. Zuordnen der Zuordnung zur Zusammenarbeit (intern)

      :::image type="content" source="../assets/images/collaboration-control/associate-collab-map-internal.png" alt-text="Screenshot ist ein Beispiel, das zeigt, wie sie eine interne Zuordnung zur Zusammenarbeit zuordnen.":::

     Diese Schrittaktion erstellt eine Zuordnung einer Zusammenarbeitsentität (Dataverse-Tabelle) mit Ihrer Zusammenarbeitssitzung. Intern sind nur zum Erstellen von Zuordnungen zwischen internen Dataverse-Entitäten/-Tabellen vorgesehen.

     * **Stamm-ID der Zusammenarbeit:** Der eindeutige Bezeichner der Zusammenarbeitssitzung, der einer Entität für die Zusammenarbeit zugeordnet werden soll.
     * **Entitäts-ID der Zusammenarbeitstabelle:** Die datenverse-Entitäts-ID für die Zusammenarbeit, die zugeordnet werden soll.
     * **Name der Zusammenarbeitszuordnungsentität:** Der Name des zu zuordnenden Datenverse-Entitätstyps für die Zusammenarbeit.

     ***Erweiterte Optionen:***

     **Metadaten (erweitert)** Fügen Sie Metadaten für eine Zuordnung zur Zusammenarbeit hinzu.

     * **OData-Typ:** Dieses Feld muss angegeben werden, wenn der andere Schlüssel/Wert festgelegt ist und genau #Microsoft.Dynamics.CRM.m365_collaborationmetadata übereinstimmen muss.
     * **Schlüssel:** Schlüssel, der dem Metadatenattribut zugeordnet ist
     * **Wert:** Wert, der dem Metadatenattribut zugeordnet ist

  1. Aktualisieren der Zuordnung zur Zusammenarbeit

      :::image type="content" source="../assets/images/collaboration-control/update-collab-map.png" alt-text="Screenshot ist ein Beispiel, das zeigt, wie Die Zuordnung zur Zusammenarbeit aktualisiert wird.":::

     Mit dieser Schrittaktion wird eine vorhandene Zuordnung zur Zusammenarbeit aktualisiert:

     * **Karten-ID für die Zusammenarbeit:** Der zu aktualisierenden eindeutigen Bezeichner für die Zusammenarbeitszuordnung.
     * **Entitäts-ID der Zusammenarbeitstabelle:** Die zuzuordnenden Entitäts-ID für die Zusammenarbeit. Dieser Wert muss leer sein, wenn die externe ID bereitgestellt wird.
     * **Name der Zusammenarbeitszuordnungsentität**
     * **Externe ID der Zusammenarbeitstabelle:** Die externe Ressourcen-ID für die Zusammenarbeit, die zugeordnet werden soll. Dieser Wert muss leer sein, wenn die Entitäts-ID angegeben wird.  

     ***Erweiterte Optionen:***

     **Metadaten erstellen:** Fügt einem Datensatz für die Zusammenarbeitszuordnung weitere Metadaten hinzu.

     * **OData-Typ:** Dieses Feld muss angegeben werden, wenn der andere Schlüssel/Wert festgelegt ist und genau #Microsoft.Dynamics.CRM.m365_collaborationmetadata übereinstimmen muss.
     * **Schlüssel:** Schlüssel, der dem Metadatenattribut zugeordnet ist.
     * **Wert:** Wert, der dem Metadatenattribut zugeordnet ist.

     **Metadaten aktualisieren:** Aktualisierungen vorhandenen Metadaten in einem Datensatz für die Zusammenarbeitskarte.

     * **OData-Typ:** Dieses Feld muss angegeben werden, wenn der andere Schlüssel/Wert festgelegt ist und genau #Microsoft.Dynamics.CRM.m365_collaborationmetadata übereinstimmen muss.
     * **Schlüssel:** Schlüssel, der dem zu aktualisierenden Metadatenattribut zugeordnet ist
     * **Wert:** Wert, der dem Metadatenattribut zugeordnet ist

     **Metadaten löschen:** Entfernt alle vorhandenen Metadaten in einem Zuordnungsdatensatz für die Zusammenarbeit.

     * **OData-Typ:** Dieses Feld muss angegeben werden, wenn der andere Schlüssel/Wert festgelegt ist und genau #Microsoft.Dynamics.CRM.m365_collaborationmetadata übereinstimmen muss.
     * **Schlüssel:** Schlüssel, der dem zu entfernenden Metadatenattribut zugeordnet ist.

  1. Abrufen von Zusammenarbeitsmetadaten

      :::image type="content" source="../assets/images/collaboration-control/get-collab-metadata.png" alt-text="Screenshot ist ein Beispiel, das zeigt, wie Metadaten für die Zusammenarbeit abgerufen werden.":::

     In dieser Schrittaktion werden alle Metadaten aufgelistet, die mit dem angegebenen Filter übereinstimmen.

     **Filter:** Ein Filter, der auf die Metadatenabfrage angewendet werden soll.
     Beispiel zum Abrufen aller Metadaten im Zusammenhang mit einer Entitäts-ID für die Zusammenarbeitszuordnung  
     m365_entityname eq 'm365_collaborationmap' und m365_entityid eq 'GUID'

  1. Planner-Aufgabe erstellen

      :::image type="content" source="../assets/images/collaboration-control/create-planner-task.png" alt-text="Screenshot ist ein Beispiel zum Erstellen einer Planner-Aufgabe.":::

     Mit dieser Schrittaktion wird eine Graph-Planner-Aufgabe mithilfe der virtuellen Planner-Aufgabentabelle "Zusammenarbeitssteuerelemente" erstellt:

     * **Stamm-ID der Zusammenarbeit (erforderlich):** Eindeutiger Bezeichner der Zusammenarbeitssitzung
     * **Plan-ID (erforderlich):** Plan-ID, zu der die Aufgabe gehört
     * **Titel (erforderlich):** Titel der Aufgabe
     * **Zuordnungen:** Ein json-formatiertes Objekt, das alle Zuweisungen eines Vorgangs darstellt. Siehe [plannerAssignments-Ressourcentyp](/graph/api/resources/plannerassignments)
     * **Bucket-ID:** Bucket-ID, zu der die Aufgaben gehören.
     * **Priorität:** Priorität des Vorgangs. 0 und 10 (einschließlich) erhöhen den Wert und haben eine niedrigere Priorität.

     ***Erweiterte Optionen:***

     * **Anzahl der aktiven Prüflistenelemente** (Erweitert): Anzahl der Prüflistenelemente, deren Wert auf "false" festgelegt ist, der unvollständige Elemente darstellt.
     * **Angewendete Kategorien:** Ein JSON-Formatiererobjekt, das alle Kategorien darstellt, die für die Aufgabe angewendet werden sollen. Siehe [plannerAppliedCategories-Ressourcentyp](/graph/api/resources/plannerappliedcategories).
     * **Priorität zuweisen:** Zeichenfolgenwerthinweise, die verwendet werden, um Elemente dieses Typs in einer Listenansicht zu sortieren. Anzeigen [, Verwenden von Bestellhinweisen in Planner](/graph/api/resources/planner-order-hint-format)
     * **Anzahl der Prüflistenelemente:** Anzahl der Prüflistenelemente, die für die Aufgabe vorhanden sind.
     * **Abgeschlossen von:** Ein json-formatiertes Objekt, das die Identität des Benutzers darstellt, der die Aufgabe abgeschlossen hat. Siehe [IdentitySet-Ressourcentyp](/graph/api/resources/identityset)
     * **Unterhaltungsthread-ID:** Thread-ID der Unterhaltung für die Aufgabe. Dies ist die ID des Unterhaltungsthreadobjekts, das in der Gruppe erstellt wurde.
     * **Erstellt von:** Ein json-formatiertes Objekt, das die Identität des Benutzers darstellt, der die Aufgabe erstellt hat. Siehe [IdentitySet-Ressourcentyp](/graph/api/resources/identityset)
     * **Fälligkeitsdatum:** Datum und Uhrzeit, zu dem der Vorgang fällig ist. Der Timestamp-Typ stellt die Datums- und Uhrzeitinformationen mithilfe des ISO 8601-Formats dar und wird immer in UTC-Zeit angegeben. Mitternacht UTC-Zeit am 1. Januar 2014 ist beispielsweise 2014-01-01T00:00:00Z.
     * **Bestellhinweis:** Hinweis, der zum Bestellen von Elementen dieses Typs in einer Listenansicht verwendet wird. Das Format wird [mithilfe von Reihenfolgenhinweisen in Planner](/graph/api/resources/planner-order-hint-format) definiert.
     * **Prozent abgeschlossen:** Prozentsatz des Vorgangsabschlusses (0-100)
     * **Vorschautyp:** Dadurch wird der Vorschautyp festgelegt, der für die Aufgabe angezeigt wird. Die möglichen Werte sind: automatic, noPreview, checklist, description, reference.
     * **Referenzanzahl:** Anzahl der externen Verweise, die für den Vorgang vorhanden sind.
     * **Startdatum:** Datum und Uhrzeit, zu dem die Aufgabe beginnt. Der Timestamp-Typ stellt die Datums- und Uhrzeitinformationen mithilfe des ISO 8601-Formats dar und wird immer in UTC-Zeit angegeben. Mitternacht UTC-Zeit am 01. Januar 2014 ist beispielsweise der 01.01.2014.01.000:00Z.

  1. Planner-Aufgabe abrufen

      :::image type="content" source="../assets/images/collaboration-control/get-planner-task.png" alt-text="Screenshot ist ein Beispiel für die Aufgabe &quot;Planer abrufen&quot;.":::

     Diese Schrittaktion gibt eine Planner-Vorgangsdaten mithilfe von Steuerelementen für die Zusammenarbeit in der virtuellen Planner-Aufgabentabelle zurück:

     **Vorgangs-ID (erforderlich):** Eindeutiger Vorgangsbezeichner

  1. Planner-Aufgabe aktualisieren

      :::image type="content" source="../assets/images/collaboration-control/update-planner-task-preview.png" alt-text="Screenshot der Aufgabe &quot;Planer aktualisieren&quot;.":::

     Mit dieser Schrittaktion wird ein Planner-Aufgabendatensatz mithilfe der virtuellen Planner-Aufgabentabelle für Steuerelemente für die Zusammenarbeit aktualisiert.

     * **Vorgangs-ID (erforderlich):** Eindeutiger Bezeichner der Aufgabe.
     * **Zuordnungen:** Ein json-formatiertes Objekt, das alle Zuweisungen eines Vorgangs darstellt. Siehe plannerAssignments-Ressourcentyp – Microsoft Graph v1.0 | Microsoft-Dokumentation.  
     * **Bucket-ID:** Bucket-ID, zu der die Aufgabe gehört.  
     * **Planner-Aufgabendetails:** Stellt die zusätzlichen Informationen zu einer Aufgabe dar.
     * **Fälligkeitsdatum:** Datum und Uhrzeit, zu dem der Vorgang fällig ist. Der Timestamp-Typ stellt die Datums- und Uhrzeitinformationen mithilfe des ISO 8601-Formats dar und wird immer in UTC-Zeit angegeben. Mitternacht UTC-Zeit am 01. Januar 2014 ist beispielsweise 2014-01-01T00:00:00Z.
     * **Priorität:** Priorität des Vorgangs. 0 und 10 (einschließlich) erhöhen den Wert und haben eine niedrigere Priorität.  
     * **Prozent abgeschlossen:** Prozentsatz des Vorgangsabschlusses (0-100).
     * **Titel:** Titel der Aufgabe.

     ***Erweiterte Optionen:***

     * **Angewendete Kategorien:** Ein json-formatiertes Objekt, das alle Kategorien darstellt, die für die Aufgabe angewendet werden sollen. Siehe [plannerAppliedCategories-Ressourcentyp](/graph/api/resources/plannerappliedcategories).
     * **Priorität zuweisen:** Zeichenfolgenwerthinweise, die verwendet werden, um Elemente dieses Typs in einer Listenansicht zu sortieren. Informationen finden Sie [unter Verwendung von Orderhinweisen in Planner](/graph/api/resources/planner-order-hint-format).
     * **Unterhaltungsthread-ID:** Thread-ID der Unterhaltung für die Aufgabe. Dies ist die ID des Unterhaltungsthreadobjekts, das in der Gruppe erstellt wurde.
     * **Stamm-ID der Zusammenarbeit:** Eindeutiger Bezeichner der Zusammenarbeitssitzung.
     * **Bestellhinweis:** Hinweis, der zum Bestellen von Elementen dieses Typs in einer Listenansicht verwendet wird. Das Format wird hier als Gliederung definiert.
     * **Startdatum:** Datum und Uhrzeit, zu dem die Aufgabe beginnt. Der Timestamp-Typ stellt die Datums- und Uhrzeitinformationen mithilfe des ISO 8601-Formats dar und wird immer in UTC-Zeit angegeben. Mitternacht UTC-Zeit am 1. Januar 2014 ist beispielsweise 2014-01-01T00:00:00Z.

**Beispielflussszenario**

Im Folgenden sind Beispiele für Flüsse aufgeführt:

1. Abrufen einer Antwort aus Microsoft-Formularen, Erstellen einer Zusammenarbeitssitzung und einer zugeordneten Aufgabe.

   :::image type="content" source="../assets/images/collaboration-control/response-submitted.png" alt-text="Screenshot ist ein Beispiel, das zeigt, wie Eine neue Antwort übermittelt wird.":::

1. Jedes Mal, wenn eine Zusammenarbeitssitzung erstellt wird, erfassen Sie die Details, und senden Sie eine E-Mail-Benachrichtigung.

   :::image type="content" source="../assets/images/collaboration-control/colab-session-created-preview.png" alt-text="Screenshot ist ein Beispiel für die erstellte Zusammenarbeitssitzung.":::

> [!NOTE]
> Auf diese Weise können mehrere Flüsse ausgelöst werden, um unterschiedliche Aktionen auszuführen, wobei Daten aus der Antwort der Erstellung der Zusammenarbeitssitzung verwendet werden.
