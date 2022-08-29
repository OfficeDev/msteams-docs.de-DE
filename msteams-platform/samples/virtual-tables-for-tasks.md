---
title: Steuerelement-App für virtuelle Tabellen für Aufgaben, Besprechungen und Dateien in der Steuerelement-App für die Zusammenarbeit
author: surbhigupta
description: In diesem Modul erfahren Sie mehr über virtuelle Tabellen für Aufgaben, Besprechungen und Dateien in der Steuerelement-App für die Zusammenarbeit in Microsoft Teams.
ms.localizationpriority: medium
ms.author: v-npaladugu
ms.topic: conceptual
ms.openlocfilehash: 1913b379e9f24d36948a05190a4ae1804a8ec728
ms.sourcegitcommit: 442d2c8e80a2605b6d0215c973557471f18f8121
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/11/2022
ms.locfileid: "67314595"
---
# <a name="virtual-tables-for-tasks-meetings-files"></a>Virtuelle Tabellen für Aufgaben, Besprechungen, Dateien

Eine neue Funktion mit dieser Version ist eine Reihe virtueller Tabellen. Diese ermöglichen Entwicklern die Interaktion mit Graph über OData-APIs.

Die Kernlösung für die Zusammenarbeitssteuerung umfasst eine Reihe [virtueller Tabellen](/power-apps/developer/data-platform/virtual-entities/get-started-ve), die für den programmgesteuerten Zugriff auf die Daten verwendet werden können, die von den Steuerelementen für die Zusammenarbeit erstellt wurden.

> [!NOTE]
> Derzeit sind Die Steuerelemente für die Zusammenarbeit nur in der [öffentlichen Entwicklervorschau](~/resources/dev-preview/developer-preview-intro.md) verfügbar.

> [!TIP]
> [Virtuelle Tabellen](/power-apps/developer/data-platform/virtual-entities/get-started-ve) , auch als virtuelle Entitäten bezeichnet, ermöglichen die Integration von Daten, die sich in externen Systemen befinden, indem diese Daten nahtlos als Tabellen in Microsoft Dataverse dargestellt werden, ohne Replikation von Daten und häufig ohne benutzerdefinierte Codierung.

Das externe System, das von den Steuerelementen für die Zusammenarbeit verwendet wird, ist Microsoft Graph. Es gibt virtuelle Tabellen für Gruppenkalenderereignisse, Das Buchen von Terminen, Planerplänen oder Aufgaben und SharePoint-Laufwerken, Ordnern und Dateien.

Dieser Artikel enthält Beispiele, die zeigen, wie Sie mithilfe der Dataverse REST-API auf die virtuellen Tabellen zugreifen, um CRUD-Vorgänge (Erstellen, Lesen, Aktualisieren und Löschen) auszuführen.

> [!TIP]
> Weitere Informationen zur Dataverse-REST-API finden [Sie unter Verwenden der Microsoft Dataverse-Web-API](/power-apps/developer/data-platform/webapi/overview).

* Virtuelle Tabellen verwenden die standardmäßige Dataverse-Web-API, die die Verwendung der virtuellen Tabellen zum Auffüllen von Daten in Ihrer Anwendung erleichtert.
* Virtuelle Tabellen implementieren komplexe Workflows, die zur Unterstützung von Steuerelementen für die Zusammenarbeit erforderlich sind, und diese werden in Microsoft-Rechenzentren ausgeführt, um eine optimale Leistung zu erzielen.  
* Virtuelle Tabellen verwenden die standardmäßigen Dataverse-Protokollierungs- und -Überwachungsfunktionen.

Nachdem Sie die Steuerelemente für die Zusammenarbeit installiert haben, können die virtuellen Tabellen als ein anderer Dienst für Ihre Anwendung behandelt werden, von dem abhängig sein kann.

:::image type="content" source="~/assets/images/collaboration-control/vt-overview.png" alt-text="Übersicht über virtuelle Tabellen":::

**Voraussetzungen**

Um diesem Artikel zu folgen, benötigen Sie Folgendes:

1. Eine Dataverse-Umgebung, in der die Steuerelemente für die Zusammenarbeit installiert wurden.
1. Ein Benutzerkonto in der Dataverse-Umgebung, dem die **Benutzerrolle "Zusammenarbeit"** zugewiesen ist.
1. Ein Drittanbietertool, z. B.: Post man oder einen benutzerdefinierten C#-Code, mit dem Sie sich bei Microsoft Dataverse-Instanzen authentifizieren und Web-API-Anforderungen verfassen und senden und Antworten anzeigen können.  

> [!TIP]
> Microsoft stellt Informationen zum Konfigurieren einer Postman-Umgebung bereit, die eine Verbindung mit Ihrer Dataverse-Instanz herstellt und Postman zum Ausführen von Vorgängen mit der Web-API verwendet. Siehe [Verwenden von Postman mit Microsoft Dataverse-Web-API](/power-apps/developer/data-platform/webapi/use-postman-web-api).

## <a name="virtual-tables-sample-scenario"></a>Beispielszenario für virtuelle Tabellen

Das in diesem Leitfaden beschriebene Szenario verwendet die virtuellen Tabellen "Planner Plan" und "Task". Das beschriebene Szenario ist das gleiche, das vom Steuerelement für die Zusammenarbeit von Aufgaben verwendet wird. Aus Benutzersicht zeigt das Szenario, wie ein Planner-Plan und mehrere Aufgaben erstellt und einem bestimmten Geschäftsdatensatz zugeordnet werden. In diesem Szenario wird gezeigt, wie Sie die dem Geschäftsdatensatz zugeordneten Aufgaben abrufen und wie Sie eine bestimmte Planner-Aufgabe lesen, aktualisieren und löschen.

Im folgenden Sequenzdiagramm wird die Interaktion zwischen dem Client erläutert, z. B. das Steuerelement für die Aufgabenzusammenarbeit, die [Zusammenarbeits-API](/rest/api/industry/collaboration-controls/) und die virtuellen Tabellen "Plan für Planner" und "Aufgaben".

:::image type="content" source="~/assets/images/collaboration-control/vt-sequence.png" alt-text="Sequenzdiagramm für virtuelle Tabellen":::

## <a name="virtual-tables-basic-operations"></a>Grundlegende Vorgänge für virtuelle Tabellen

In diesem Abschnitt werden die HTTP-Anforderungen und -Antworten für jeden Schritt im Beispielszenario beschrieben.

**Aufgabe 1: Abrufen der Gruppen-ID**

Rufen Sie die Gruppen-ID ab, die in [den Einstellungen für Ihre Zusammenarbeit](~/samples/app-with-collaboration-controls.md#define-settings-for-your-collaboration) verwendet wird.

> [!NOTE]
> Der Benutzer, den Sie zum Erstellen des Plans in den nachfolgenden Aufgaben verwenden, muss Mitglied dieser Gruppe sein. Andernfalls erhalten Sie die Antwort "403 Forbidden".

**Aufgabe 2: Starten einer Zusammenarbeitssitzung**

Eine Zusammenarbeitssitzung ist ein Datensatz in der Stammtabelle für die Zusammenarbeit, mit dem Sie mehrere Zusammenarbeiten zuordnen können, z. B. Aufgaben, Ereignisse, Termine mit einem Geschäftsdatensatz.

Mithilfe einer Zusammenarbeitssitzung können Sie Vorgänge ausführen, z. B. eine Liste der Kalenderereignisse, die einem Geschäftsdatensatz zugeordnet sind, z. B. eine Inspektionsanwendung.

# <a name="request"></a>[Anforderung](#tab/request)

```http
    HTTP/1.1 POST https://[Organization URI]/api/data/v9.0/m365_begincollaborationsession  
```

```json
{
    "applicationName": "{{applicationName}}", 
    "collaborationRootEntityId": "{{collaborationRootEntityId}}", 
    "collaborationRootEntityName": "{{entityName}}" 
}
```

* `applicationName`: Eindeutiger Name für die Anwendung
* `collaborationRootEntityName`: Name der Unternehmensdatensatzentität  
* `collaborationRootEntityId`: Primärschlüssel (ID) des spezifischen Geschäftsdatensatzes

# <a name="response"></a>[Antwort](#tab/response)

```http
    HTTP/1.1 200 OK 
```

```json
{ 
    "@odata.context": "https:// [Organization URI]/api/data/v9.0/$metadata#Microsoft.Dynamics.CRM.m365_begincollaborationsessionResponse", 
    "collaborationRootId": "72fc6b52-39d5-ec11-a7b6-0022481bfe8f" 
}
```

---

Behalten Sie den `collaborationRootId` Überblick, wie er in nachfolgenden Anforderungen benötigt wird.

**Aufgabe 3: Erstellen eines Planner-Plans**

Erstellen Sie einen Planner-Plan, und ordnen Sie ihn der oben erstellten Zusammenarbeitssitzung zu `Group ID` und `collaborationRootId`.

# <a name="request"></a>[Anforderung](#tab/request1)

```http
    HTTP/1.1 POST https://[Organization URI]/api/data/v9.0/m365_graphplannerplans  
```

```json

{ 
    "m365_collaborationrootid": "{{collaborationRootId}}", 
    "m365_owner": "{{groupId}}", 
    "m365_title": "{{planTitle}}" 
}

```

* `collaborationRootId`: Identifiziert die Zusammenarbeitssitzung, der wir diesen Plan zuordnen möchten, und verwendet den Wert aus Aufgabe 2.

* `groupId`: Identifiziert die Gruppe, der dieser Plan gehören soll. Verwenden Sie den Wert aus Schritt 1.

* `planTitle`: Titel des Plans

# <a name="response"></a>[Antwort](#tab/response1)

```http
    HTTP/1.1 201 Created 
```

```json

{ 
    "@odata.context": "https:// [Organization URI]/api/data/v9.0/$metadata#m365_graphplannerplans/$entity", 
    "@odata.etag": "W/\"JzEtUGxhbiAgQEBAQEBAQEBAQEBAQEBARCc=\"", 
    "m365_createdby": "{\"user\":{\"displayName\":null,\"email\":null,\"id\":\"be330617-0e2b-48e9-8bf7-429a09c78e65\"},\"group\":null}", 
    "m365_createddatetime": "2022-05-16T16:58:33.1833561Z", 
    "m365_owner": "03614cef-8f5b-4265-9944-080d013c55d6", 
    "m365_title": "Multi-byte plan", 
    "m365_id": "8I6fu1kNS0elsbTxd67bi2UADnJu", 
    "m365_collaborationrootid": "72fc6b52-39d5-ec11-a7b6-0022481bfe8f", 
    "m365_graphplannerplanid": "5c9c3ecf-f157-0f67-dcd9-733a77ad593e", 
    "m365_details": null 
} 

```

---

Behalten Sie den`m365_id` Überblick, wie er in nachfolgenden Anforderungen benötigt wird.

**Aufgabe 4: Erstellen einer Planner-Aufgabe**

Erstellen einer Planner-Aufgabe mit `PlanId` und `collaborationRootId`. Sie können mehrere Planner-Aufgaben erstellen und sie der zuvor erstellten Zusammenarbeitssitzung zuordnen.

# <a name="request"></a>[Anforderung](#tab/request2)

```http
    HTTP/1.1 POST https://[Organization URI]/api/data/v9.0/m365_graphplannertasks  
```

```json
{ 
    "m365_collaborationrootid": "{{collaborationRootId}}", 
    "m365_planid": "{{planId}}", 
    "m365_title": "{{taskTitle}}", 
    "m365_duedatetime": "2022-05-04T08:00:00Z", 
    "m365_assignments": "{\"me\":{\"orderHint\":\" !\",\"@odata.type\":\"#microsoft.graph.plannerAssignment\"}}" 
} 

```

* `collaborationRootId`: Identifiziert die Zusammenarbeitssitzung, der wir diesen Plan zuordnen möchten, uns den Wert aus Aufgabe 2.
* `planId`: Identifiziert den Plan, dem diese Aufgabe zugewiesen wird, verwenden Sie den Wert aus dem vorherigen Schritt.
* `taskTitle`: Titel der Aufgabe

# <a name="response"></a>[Antwort](#tab/response2)

```http
    HTTP/1.1 201 Created 
```

```json

{ 
    "@odata.context": "https://mwtmarkwallaceunmanaged.crm10.dynamics.com/api/data/v9.0/$metadata#m365_graphplannertasks/$entity", 
    "@odata.etag": "W/\"JzEtVGFzayAgQEBAQEBAQEBAQEBAQEBARCc=\"", 
    "m365_activechecklistitemcount": 0, 
    "m365_appliedcategories": "{}", 
    "m365_assigneepriority": "8585488865579062167", 
    "m365_assignments": "{\"be330617-0e2b-48e9-8bf7-429a09c78e65\":{\"assignedBy\":{\"user\":{\"displayName\":null,\"email\":null,\"id\":\"be330617-0e2b-48e9-8bf7-429a09c78e65\"},\"group\":null},\"assignedDateTime\":\"2022-05-16T16:58:47.571364+00:00\",\"orderHint\":\"8585488866179218449P`\",\"@odata.type\":\"#microsoft.graph.plannerAssignment\"}}", 
    "m365_checklistitemcount": 0, 
    "m365_createdby": "{\"user\":{\"displayName\":null,\"email\":null,\"id\":\"be330617-0e2b-48e9-8bf7-429a09c78e65\"},\"group\":null}", 
    "m365_createddatetime": "2022-05-16T16:58:47Z", 
    "m365_duedatetime": "2022-05-04T08:00:00Z", 
    "m365_hasdescription": false, 
    "m365_orderhint": "8585488865579062167", 
    "m365_percentcomplete": 0, 
    "m365_priority": 5, 
    "m365_planid": "8I6fu1kNS0elsbTxd67bi2UADnJu", 
    "m365_previewtype": "automatic", 
    "m365_referencecount": 0, 
    "m365_title": "Team-oriented discrete time-frame", 
    "m365_id": "8WSKWaEqAU-aZV4h9VUn0GUALXbH", 
    "m365_collaborationrootid": "72fc6b52-39d5-ec11-a7b6-0022481bfe8f", 
    "m365_graphplannertaskid": "0a2115b9-8b03-90ee-b450-42005d906ce8", 
    "m365_completedby": null, 
    "m365_details": null, 
    "m365_completeddatetime": null, 
    "m365_conversationthreadid": null, 
    "m365_bucketid": null, 
    "m365_startdatetime": null 
} 

```

---

Behalten Sie den `m365_graphplannertaskid` Überblick, wie er in nachfolgenden Anforderungen benötigt wird.

> [!NOTE]
> Dies `m365_graphplannertaskid` ist der Primärschlüssel des Datensatzes in der virtuellen Tabelle "Planner-Aufgabe". Alle nachfolgenden Anforderungen an die virtuelle Tabelle zur Interaktion mit diesem Datensatz müssen diesen Primärschlüssel verwenden. Dies wird als in den `plannerTaskId` nachfolgenden Schritten in diesem Dokument bezeichnet.

Wiederholen Sie diesen Schritt, um mehrere Aufgaben im Plan zu erstellen.

**Aufgabe 5: Abrufen zugeordneter Planner-Aufgaben**

Rufen Sie zugeordnete Planner-Aufgaben ab, `collaborationRootId` die der zuvor erstellten Zusammenarbeitssitzung zugeordnet sind.

# <a name="request"></a>[Anforderung](#tab/request3)

```http
    HTTP/1.1 GET https://[Organization URI]/api/data/v9.0/ m365_graphplannertasks?$filter=m365_collaborationrootid eq '{{collaborationRootId}}'&$select=m365_graphplannertaskid,m365_title,m365_createddatetime  
```

* `$filter`: Verwenden Sie die $filter Systemabfrage, um Datensätze anzufordern, die der Zusammenarbeitssitzung zugeordnet sind (indem Sie die ID des Stammdatensatzes für die Zusammenarbeit angeben).
* `$select`: Verwenden Sie die $select Systemabfrageoption, um bestimmte Eigenschaften anzufordern.

# <a name="response"></a>[Antwort](#tab/response3)

```http
    HTTP/1.1 200 OK 
```

```json

{ 

    "@odata.context": "https://mwtmarkwallaceunmanaged.crm10.dynamics.com/api/data/v9.0/$metadata#m365_graphplannertasks(m365_graphplannertaskid,m365_title,m365_createddatetime)", 
    "value": [ 
        { 
            "@odata.etag": "W/\"JzEtVGFzayAgQEBAQEBAQEBAQEBAQEBARCc=\"", 
            "m365_graphplannertaskid": "8537731e-9414-1091-8d7d-ce5b74fc2477", 
            "m365_title": "Diverse executive core", 
            "m365_createddatetime": "2022-05-16T16:58:45Z", 
            "m365_id": "N_A2qmo3j0uvZZY1yd6V_GUADDEg", 
            "m365_collaborationrootid": "72fc6b52-39d5-ec11-a7b6-0022481bfe8f" 
        }, 
        { 
            "@odata.etag": "W/\"JzEtVGFzayAgQEBAQEBAQEBAQEBAQEBARCc=\"", 
            "m365_graphplannertaskid": "4a89895a-050e-9165-a6e4-19c3850f22ec", 
            "m365_title": "Cloned didactic open architecture", 
            "m365_createddatetime": "2022-05-16T16:58:41Z", 
            "m365_id": "--U0zbgsO0us084C0yCyEWUALbWw", 
            "m365_collaborationrootid": "72fc6b52-39d5-ec11-a7b6-0022481bfe8f" 
        }, 
        { 
            "@odata.etag": "W/\"JzEtVGFzayAgQEBAQEBAQEBAQEBAQEBARCc=\"", 
            "m365_graphplannertaskid": "20a08b8c-394b-b3fb-f9d1-47496df7a67b", 
            "m365_title": "Synergized zero defect interface", 
            "m365_createddatetime": "2022-05-16T16:58:43Z", 
            "m365_id": "AMn3RtbmV0m6cvkp5HKDCWUAKI0_", 
            "m365_collaborationrootid": "72fc6b52-39d5-ec11-a7b6-0022481bfe8f" 
        } 
    ] 
} 

```

---

Verfolgen Sie, `m365_id‘s` wie IDs in nachfolgenden Anforderungen benötigt werden.

**Aufgabe 6: Abrufen einer Planner-Aufgabe**

Dient zum Abrufen einer Planner-Aufgabe `PlannerTaskID` zum Ausführen eines Lesevorgangs für eine der zuvor erstellten Planner-Aufgaben.

# <a name="request"></a>[Anforderung](#tab/request4)

```http
    HTTP/1.1 GET https://[Organization URI]/api/data/v9.0/m365_graphplannertasks({{plannerTaskId}})  
```

* `plannerTaskId`: Der Primärschlüssel für den Planner-Aufgabendatensatz ist die `m365_graphplannertaskid` Eigenschaft.

# <a name="response"></a>[Antwort](#tab/response4)

```http
    HTTP/1.1 200 OK 
```

```json
{ 
    "@odata.context": "https://mwtmarkwallaceunmanaged.crm10.dynamics.com/api/data/v9.0/$metadata#m365_graphplannertasks/$entity", 
    "@odata.etag": "W/\"JzEtVGFzayAgQEBAQEBAQEBAQEBAQEBARCc=\"", 
    "m365_activechecklistitemcount": 0, 
    "m365_appliedcategories": "{}", 
    "m365_assigneepriority": "8585488204334528131", 
    "m365_assignments": "{\"be330617-0e2b-48e9-8bf7-429a09c78e65\":{\"assignedBy\":{\"user\":{\"displayName\":null,\"email\":null,\"id\":\"be330617-0e2b-48e9-8bf7-429a09c78e65\"},\"group\":null},\"assignedDateTime\":\"2022-05-17T11:20:52.0247676+00:00\",\"orderHint\":\"8585488204934840644P2\",\"@odata.type\":\"#microsoft.graph.plannerAssignment\"}}", 
    "m365_checklistitemcount": 0, 
    "m365_createdby": "{\"user\":{\"displayName\":null,\"email\":null,\"id\":\"be330617-0e2b-48e9-8bf7-429a09c78e65\"},\"group\":null}", 
    "m365_createddatetime": "2022-05-17T11:20:52Z", 
    "m365_duedatetime": "2022-05-04T08:00:00Z", 
    "m365_orderhint": "8585488204334528131", 
    "m365_percentcomplete": 0, 
    "m365_priority": 5, 
    "m365_planid": "8I6fu1kNS0elsbTxd67bi2UADnJu", 
    "m365_previewtype": "automatic", 
    "m365_referencecount": 0, 
    "m365_title": "Secured content-based customer loyalty", 
    "m365_id": "SXmz1hxiOk-E3MKJUyhj0mUABvix", 
    "m365_details": "{\"@odata.context\":\"https://graph.microsoft.com/beta/$metadata#planner/tasks('SXmz1hxiOk-E3MKJUyhj0mUABvix')/details/$entity\",\"@odata.etag\":\"W/\\\"JzEtVGFza0RldGFpbHMgQEBAQEBAQEBAQEBAQEBARCc=\\\"\",\"description\":null,\"previewType\":\"automatic\",\"id\":\"SXmz1hxiOk-E3MKJUyhj0mUABvix\",\"references\":{},\"checklist\":{}}", 
    "m365_graphplannertaskid": "1b326015-bb43-945c-85bc-9b2a4ed16c73", 
    "m365_completedby": null, 
    "m365_hasdescription": null, 
    "m365_collaborationrootid": null, 
    "m365_completeddatetime": null, 
    "m365_conversationthreadid": null, 
    "m365_bucketid": null, 
    "m365_startdatetime": null 
}

```

---

Verfolgen Sie die `@odata.etag` Eigenschaft und die`m365_graphplannertaskid` Eigenschaft, da diese zum Ausführen von Aktualisierungs- oder Löschvorgängen erforderlich sind.

**Aufgabe 7: Aktualisieren einer Planner-Aufgabe**

Aktualisieren Sie eine Planner-Aufgabe, `PlannerTask ID` um einen Aktualisierungsvorgang für eine der im vorherigen Schritt erstellten Planner-Aufgaben auszuführen. Führen Sie die folgende Anforderung aus, um eine Planner-Aufgabe zu aktualisieren:

# <a name="request"></a>[Anforderung](#tab/request5)

```http
    HTTP/1.1 PATCH https://[Organization URI]/api/data/v9.0/m365_graphplannertasks({{plannerTaskId}})
```

* Header: If-Match: {{@odata.etag}}

```json

{
    "m365_title": "{{$planTitle}}" 
}   

```

* `@odata.etag`: Beim Etag für die Aufgabe müssen Sie einen Lesevorgang ausführen, um die aktuellste Version abzurufen.

* `planTitle`: Aktualisierter Titel für die Aufgabe

# <a name="response"></a>[Antwort](#tab/response5)

```http
    HTTP/1.1 204 No Content 
```

---

**Aufgabe 8: Löschen einer Planner-Aufgabe**

Löschen Sie eine Planner-Aufgabe, um `PlannerTask ID` einen Löschvorgang für eine der im vorherigen Schritt erstellten Planner-Aufgaben auszuführen. Führen Sie die folgende Anforderung aus, um eine Planner-Aufgabe zu löschen:

# <a name="request"></a>[Anforderung](#tab/request6)

```http
    HTTP/1.1 DELETE https://[Organization URI]/api/data/v9.0/m365_graphplannertasks({{plannerTaskId}})
```

* `@odata.etag`: Beim Etag für die Aufgabe müssen Sie einen Lesevorgang ausführen, um die aktuellste Version abzurufen.

# <a name="response"></a>[Antwort](#tab/response6)

```http
    HTTP/1.1 204 No Content
```

---

**Aufgabe 9: Aktualisieren von Planner-Aufgabendetails**

Aktualisieren Sie eine Planner-Aufgabe, `PlannerTask ID` um einen Aktualisierungsvorgang für eine der im vorherigen Schritt erstellten Planner-Aufgaben auszuführen.

# <a name="request"></a>[Anforderung](#tab/request7)

```http
    HTTP/1.1 PATCH https://[Organization URI]/api/data/v9.0/m365_graphplannertasks({{plannerTaskId}})
```

Header: If-Match: {{@odata.etag}}

```json

{ 

    "m365_title": "{{$planTitle}}", 
    "m365_details": "{\"@odata.etag\":\"{{details.etag}}\",\"description\":\"Updated Task Description\"}" 

}   
```

* `@odata.etag`: Beim Etag für die Aufgabe müssen Sie einen Lesevorgang ausführen, um die aktuellste Version abzurufen.
* `planTitle`: Der Titel für die Aufgabe wurde aktualisiert.
* `@details.etag`: Für die Aufgabendetails müssen Sie einen Lesevorgang mithilfe des Abfrageparameters $select ausführen, um die `m365_details` Spalte einzuschließen, um die aktuellste Version abzurufen. Dieser Wert wird in die `m365_details` Spalte der Antwort eingeschlossen. Dieser Wert ist nicht identisch mit dem `@odata.etag` , da im Planner-Back-End die Aufgabe und ihre Details separat gespeichert werden.

# <a name="response"></a>[Antwort](#tab/response7)

```http
HTTP/1.1 204 No Content 
```

---

> [!NOTE]
> Sie können die `If-Match` Kopfzeile auf "*" festlegen, und dann müssen Sie keine etag-Werte angeben, aber Ihre Änderungen überschreiben die Aufgabe und ihre Details immer.

## <a name="virtual-tables-authorization"></a>Autorisierung virtueller Tabellen

Im Folgenden sind die Autorisierungsschritte aufgeführt, die erforderlich sind, um HTTP-Anforderungen mithilfe der virtuellen Tabellen in der Lösung für Steuerelemente für die Zusammenarbeit zu stellen.

### <a name="azure-app-registration"></a>Azure-App-Registrierung

Zum Abrufen des richtigen Bearertokens ist eine App-Registrierung in Azure erforderlich. Weitere Informationen zu App-Registrierungen finden Sie unter [Registrieren einer App](/azure/active-directory/develop/quickstart-register-app).

1. Erstellen Sie eine App-Registrierung im Azure-Portal zur Authentifizierung.
1. Navigieren Sie zu **Zertifikaten & geheimen Schlüsseln**.
1. Erstellen Sie einen neuen geheimen Clientschlüssel.

     > [!IMPORTANT]
     > Achten Sie darauf, den geheimen Wert zu kopieren und zur späteren Verwendung zu speichern. Sie können nach dem Verlassen der aktuellen Seite nicht mehr darauf zugreifen.

1. Navigieren Sie zu **API-Berechtigungen**.
1. Fügen Sie die **user_impersonation** delegierte Berechtigung von Dynamics CRM hinzu.
1. Erteilen Sie die Administratorzustimmung für diese Berechtigung.

     :::image type="content" source="../assets/images/collaboration-control/power-automate-api-permission.png" alt-text="Der Screenshot ist ein Beispiel für die Power Automate-API-Berechtigung":::

1. Navigieren Sie zum **Manifest**.
1. Legen Sie den Wert der folgenden Attribute auf "true" fest:

   * oauth2AllowIdTokenImplicitFlow
   * oauth2AllowImplicitFlow

1. Wählen Sie "Speichern" aus.

     :::image type="content" source="../assets/images/collaboration-control/power-automate-manifest.png" alt-text="Der Screenshot ist ein Beispiel für das Power Automate-Manifest":::

### <a name="powerapps-environment-permissions"></a>PowerApps-Umgebungsberechtigungen

Nachdem die App-Registrierung eingerichtet wurde, müssen Sie einen Anwendungsbenutzer in der PowerApps-Umgebung einrichten. Auf diese Weise können Sie sich mit den richtigen Dynamics-Bereichen authentifizieren, die zuvor konfiguriert wurden.

1. Öffnen Sie das [Power Platform Admin Center](https://admin.powerplatform.microsoft.com/).
1. Navigieren Sie zu **Umgebungen** > **Your_Environment** > **Benutzer-App-Benutzerliste** > .
1. Wählen Sie **"Neuer App-Benutzer** " und dann Ihre Azure-App-Registrierung aus.
1. Wählen Sie **"Sicherheitsrollen bearbeiten"** aus, und weisen Sie dem App-Benutzer die Rolle " **Systemadministrator** " zu.

   1. Die **Rolle "Systemadministrator"** wird angewendet, um die Authentifizierung für alle Benutzer zuzulassen, die über eine niedrigere Sicherheitsrolle verfügen. Beispielsweise **steuert die Zusammenarbeit den Benutzer**.
   1. Dies kann durch Anwenden einer niedrigeren Rolle auf die Anwendung eingeschränkt werden. Beispielsweise **steuert die Zusammenarbeit den Administrator**.

     :::image type="content" source="../assets/images/collaboration-control/power-automate-admin-center.png" alt-text="Der Screenshot ist ein Beispiel für das Power Automate Admin Center":::

### <a name="getting-the-bearer-token"></a>Abrufen des Bearertokens

Senden Sie nach Abschluss der Azure-App-Registrierung und der PowerApps-Umgebungsberechtigungen die folgende HTTP-Anforderung, um das Bearer-Token abzurufen.

```http
POST https://login.microsoftonline.com/<AZURE_APP_TENANT_ID>/oauth2/token
```

* **Content-Type**: application/x-www-form-urlencoded
* **client_id**: <AZURE_APP_CLIENT_ID>
* **&client_secret**: <AZURE_APP_CLIENT_ID>
* **&Ressource**: https://\<RESOURCEURL\>/
* **&Benutzername**: \<USERNAME\>
* **&Kennwort**: \<PASSWORD\>
* **&grant_type**: Kennwort

> [!IMPORTANT]
> Achten Sie darauf, den nachfolgenden Schrägstrich in den Ressourcenparameter einzuschließen. Andernfalls erhalten Sie beim Aufrufen der virtuellen Tabelle einen Fehler im Zusammenhang mit Graph-Bereichen.

Kopieren Sie aus der Antwortnutzlast den Wert der **access_token** Eigenschaft. Sie können dieses Bearertoken dann als Teil des Autorisierungsheaders übergeben, wenn Sie Anforderungen an die virtuellen Tabellen stellen.

:::image type="content" source="../assets/images/collaboration-control/power-automate-authorization.png" alt-text="Der Screenshot ist ein Beispiel für die Power Automate-Autorisierung":::

## <a name="virtual-tables-error-handling"></a>Fehlerbehandlung bei virtuellen Tabellen

Die Fehlerbehandlung in virtuellen Tabellen beschreibt häufige Fehlerszenarien und die Reaktion der virtuellen Tabellen.

### <a name="attempt-to-create-a-virtual-record-without-a-collaboration-session"></a>Erstellen eines virtuellen Datensatzes ohne Zusammenarbeitssitzung

Für jede Anforderung zum Erstellen eines virtuellen Datensatzes ist eine gültige Zusammenarbeitssitzung erforderlich.  Wenn ein virtueller Datensatz erstellt wird, erstellt die virtuelle Tabelle einen Datensatz für die Zusammenarbeitszuordnung, der den primären Schlüssel des virtuellen Datensatzes, den Entitätsnamen und die externe ID, d. h. die Graph-Ressourcen-ID, enthält. Diese Zuordnung zur Zusammenarbeit ist einer Zusammenarbeitssitzung zugeordnet, und auf diese Weise verfolgen die Steuerelemente für die Zusammenarbeit die Mitarbeitszusammenarbeit, die einem Geschäftsdatensatz zugeordnet ist.

# <a name="request"></a>[Anforderung](#tab/request8)

```http
    HTTP/1.1 POST https://[Organization URI]/api/data/v9.0/m365_graphplannertasks  
```

```json

{ 
    "m365_planid": "{{planId}}", 
    "m365_title": "{{taskTitle}}", 
    "m365_duedatetime": "2022-05-04T08:00:00Z", 
    "m365_assignments": "{\"me\":{\"orderHint\":\" !\",\"@odata.type\":\"#microsoft.graph.plannerAssignment\"}}" 
}

```

Die `collaborationRootId` Eigenschaft fehlt in der Anforderung.

# <a name="response"></a>[Antwort](#tab/response8)

```http
    HTTP/1.1 400 Bad Request 
```

```json

{ 
    "error": { 
        "code": "0x80048d0b", 
        "message": "Parameter 'm365_collaborationrootid' is null, empty, or white-space." 
    } 
} 

```

---

Um dieses Problem zu beheben, müssen Sie beim Erstellen eines virtuellen Datensatzes immer eine gültige `collaborationRootId` Eigenschaft angeben.

### <a name="attempt-to-read-a-virtual-record-without-a-collaboration-map"></a>Versuch, einen virtuellen Datensatz ohne Eine Zuordnung zur Zusammenarbeit zu lesen

Mit virtuellen Tabellen können Sie Anforderungen ausführen, die Sammlungen virtueller Datensätze zurückgeben. Wir haben dies weiter oben in diesem Dokument gesehen, in dem wir alle Planeraufgaben angefordert haben, die einer bestimmten Zusammenarbeitssitzung zugeordnet sind. Es ist auch möglich, alle planner-Aufgaben, die einem bestimmten Planerplan zugeordnet sind, mithilfe einer $filter Systemabfrage wie folgt anzufordern: $filter=m365_planid eq`{{planId}}`. Ein Problem, das bei Verwendung einer solchen Abfrage auftritt, besteht darin, dass Datensätze für Planner-Aufgaben zurückgegeben werden, die keiner Zusammenarbeitssitzung zugeordnet sind, d. h. Planner-Aufgaben, die mit einer anderen Methode als der Verwendung eines Steuerelements für die Zusammenarbeit erstellt wurden. Wenn Sie versuchen, einen solchen Datensatz zu lesen, zu aktualisieren oder zu löschen, schlägt die Anforderung fehl, da die virtuelle Tabelle die zugeordnete Zuordnung zur Zusammenarbeit nicht finden kann.  

# <a name="request"></a>[Anforderung](#tab/request9)

```http
    HTTP/1.1 GET https://[Organization URI]/api/data/v9.0/m365_graphplannertasks({{plannerTaskId}})
```

Die `plannerTaskId` Eigenschaft ist einer Planner-Aufgabe zugeordnet, die mithilfe der Planner-Weboberfläche erstellt wurde und daher keinen Datensatz für die Zusammenarbeitskarte enthält.

# <a name="response"></a>[Antwort](#tab/response9)

```http
    HTTP/1.1 404 Not Found 
```

```json
{ 
    "error": { 
        "code": "0x80048d02", 
        "message": "A record with the specified key values does not exist in m365_collaborationmap entity" 
    }
} 
```

---

Um dieses Problem zu beheben, müssen Sie die Fehlermeldung in der Antwort überprüfen, und wenn sie auf die oben gezeigte Nachricht festgelegt ist, bedeutet dies, dass der virtuelle Datensatz nicht zugeordnet ist. Um eine Zuordnung für diesen Datensatz zu erstellen, müssen Sie ["Zuordnungszusammenarbeitszuordnung – REST-API](/rest/api/industry/collaboration-controls/collaboration-custom-ap-is/associate-collaboration-map)" aufrufen.

### <a name="attempt-to-read-a-virtual-record-and-the-graph-resource-has-been-deleted"></a>Versuch, einen virtuellen Datensatz zu lesen, und die Graph-Ressource wurde gelöscht

Im Zusammenhang mit dem vorherigen Fehler müssen Sie den Fall behandeln, in dem eine Graph-Ressource gelöscht wurde, der Client jedoch weiterhin einen Verweis auf den gelöschten virtuellen Datensatz hat. Dies kann passieren, wenn ein anderer Benutzer den Datensatz gelöscht hat. Wenn Sie versuchen, einen solchen Datensatz zu lesen, zu aktualisieren oder zu löschen, schlägt die Anforderung fehl, da die virtuelle Tabelle die Ressource nicht aus Graph abrufen kann.

# <a name="request"></a>[Anforderung](#tab/request10)

```http
    HTTP/1.1 GET https://[Organization URI]/api/data/v9.0/m365_graphplannertasks({{plannerTaskId}})
```

Die `plannerTaskId` Eigenschaft ist einer Planner-Aufgabe zugeordnet, die gelöscht wurde.

# <a name="response"></a>[Antwort](#tab/response10)

```http
    HTTP/1.1 404 Not Found 
```

```json
{ 
    "error": { 
        "code": "0x80048d02", 
        "message": "REST call failed because: Reason - NotFound, Full error - {\"error\":{\"code\":\"\",\"message\":\"The requested item is not found.\",\"innerError\":{\"date\":\"2022-05-17T16:30:51\",\"request-id\":\"b692a31a-312d-490c-8dce-d258459a0211\",\"client-request-id\":\"b692a31a-312d-490c-8dce-d258459a0211\"}}}." 
    } 
} 
```

---

Dieser Fall muss von jedem Clientcode behandelt werden, der virtuelle Datensätze abruft, da ein anderer Benutzer die zugeordnete Graph-Ressource jederzeit löschen kann.

### <a name="attempt-to-update-a-virtual-record-with-an-invalid-odataetag"></a>Versuchen Sie, einen virtuellen Datensatz mit einem ungültigen @odata.etag zu aktualisieren.

Die `@odata.etag` Eigenschaft wird für die Parallelität von Daten verwendet und um das Überschreiben desselben Datensatzes zu verhindern, wenn er von einem anderen Benutzer aktualisiert wurde. Wenn ein Datensatz gelesen wird, wird das aktuelle Etag zurückgegeben und bleibt gültig, bis der Datensatz geändert wird. Das etag sollte in jeder Updateanforderung enthalten sein und wird vor Abschluss des Vorgangs überprüft. Wenn der Datensatz von einem anderen Benutzer geändert wurde, da der aktuelle Benutzer den Datensatz gelesen hat, schlägt die Aktualisierungsanforderung des aktuellen Benutzers fehl.

Wenn Sie zwei Aktualisierungsanforderungen mit demselben @odata.etag ausführen, schlägt die zweite Anforderung fehl:

# <a name="request"></a>[Anforderung](#tab/request11)

```http
    HTTP/1.1 PATCH https://[Organization URI]/api/data/v9.0/m365_graphplannertasks({{plannerTaskId}})
```

Header: If-Match: {{@odata.etag}}

```json
{
    "m365_title": "{{$planTitle}}" 
}

```

# <a name="response"></a>[Antwort](#tab/response11)

```http
    HTTP/1.1 409 Conflict 
```

```json
{ 
    "error": { 
        "code": "0x80048d08", 
        "message": "REST call failed because: Reason - Conflict, Full error - {\"error\":{\"code\":\"\",\"message\":\"The attempted changes conflicted with already accepted changes. Read the latest state and resolve differences.\",\"innerError\":{\"date\":\"2022-05-18T06:54:55\",\"request-id\":\"dc6cd2b7-1509-4e81-91ff-22cf35b86e18\",\"client-request-id\":\"dc6cd2b7-1509-4e81-91ff-22cf35b86e18\"}}}." 
    }
} 
```

---

### <a name="querying-for-associated-virtual-records"></a>Abfragen zugeordneter virtueller Datensätze

In Aufgabe 5 von oben wird beschrieben, wie zugeordnete Planner-Aufgaben abgerufen werden. Dieser Vorgang wird für alle virtuellen Tabellen unterstützt. Beim Ausführen dieser Anforderung müssen Sie eine `$filter` Abfrage einschließen, die die Stamm-ID für die Zusammenarbeit wie unten dargestellt angibt:

# <a name="request"></a>[Anforderung](#tab/request12)

```http
    HTTP/1.1 GET https://[Organization URI]/api/data/v9.0/ m365_graphplannertasks?$filter=m365_collaborationrootid eq '{{collaborationRootId}}'&$select=m365_graphplannertaskid,m365_title,m365_createddatetime  
```

---

* Andere Filteroptionen können nicht mit dieser `$filter` Abfrage kombiniert werden und werden ignoriert.
* Andere Filter müssen direkt in der Antwort der Anforderung ausgeführt werden.

### <a name="querying-for-virtual-records-with-required-key-attributes"></a>Abfragen von virtuellen Datensätzen mit erforderlichen Schlüsselattributen

Wenn die Dataverse-Web-API aufgerufen wird, um mehrere Datensätze aus den folgenden virtuellen Tabellen abzurufen, ist ein obligatorisches Schlüsselattribut erforderlich. Graph Booking Appointments erfordert, dass ein gültiger `m365_bookingbusinessid` Wert in der Abfrage enthalten ist. Wenn das Schlüsselattribut nicht bereitgestellt wird, schlägt die Anforderung wie folgt fehl:

# <a name="response"></a>[Antwort](#tab/response13)

```http
    HTTP/1.1 400 Bad Request 
```

```json

{ 
  "error": { 
    "code": "0x80048d0b", 
    "message": "Key attribute is missing: 'm365_bookingbusinessid'.", 
    ….
  } 
} 

```

---

Um dieses Problem zu beheben, ändern Sie die Anforderung in das folgende Format:

# <a name="request"></a>[Anforderung](#tab/request14)

```http
    HTTP/1.1 GET https://[Organization URI]/api/data/v9.0/ m365_graphbookingappointments?$filter=m365_bookingbusinessid eq '{{bookingBusinessId}}'
```

---

### <a name="creating-virtual-records-and-graph-access-control"></a>Erstellen virtueller Datensätze und Graph-Zugriffssteuerung

Die virtuellen Tabellen berücksichtigen die für Microsoft Graph angegebene Zugriffssteuerung. Die virtuellen Tabellen lassen keine Vorgänge zu, die der Benutzer mithilfe der Microsoft Graph-API nicht ausführen konnte. Wenn der Benutzer, den Sie zum Erstellen des Plans verwenden, beispielsweise Aufgabe 3 ist und kein Mitglied der von Ihnen verwendeten Gruppe ist, erhalten Sie 403 unzulässige Antworten.
