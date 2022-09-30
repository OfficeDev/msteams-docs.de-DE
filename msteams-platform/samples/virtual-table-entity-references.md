---
title: Entitätsverweise für virtuelle Tabellen
author: surbhigupta
description: In diesem Modul erfahren Sie mehr über die Entitätsreferenz für virtuelle Tabellen und deren Attribute in Microsoft Teams.
ms.localizationpriority: medium
ms.author: v-npaladugu
ms.topic: conceptual
ms.openlocfilehash: 98e9ee6a2bc565c35a9b46c2990a7c548dab2e31
ms.sourcegitcommit: edfe85e312c73e34aa795922c4b7eb0647528d48
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/30/2022
ms.locfileid: "68243052"
---
# <a name="virtual-tables-entity-reference"></a>Entitätsverweis für virtuelle Tabellen

Die Zusammenarbeit steuert virtuelle Entitäten und deren Attribute verfügen über eine 1:1-Zuordnung mit einem bestimmten Microsoft Graph-Ressourcentyp. Beispielsweise werden die Diagrammplaner-Vorgangsentitäten dem [Ressourcentyp "Microsoft Graph Planner-Vorgang"](/graph/api/resources/plannertask) zugeordnet. Die virtuelle Entität hat dieselben Attribute wie der Ressourcentyp.

> [!NOTE]
> Derzeit sind Die Steuerelemente für die Zusammenarbeit nur in der [öffentlichen Entwicklervorschau](~/resources/dev-preview/developer-preview-intro.md) verfügbar.

## <a name="collaboration-controls-virtual-entities"></a>Zusammenarbeit steuert virtuelle Entitäten

| Name | Beschreibung |
|---|---|
| Graph Planner-Aufgabe | Die Graph Planner-Aufgabentabelle stellt eine Planner-Aufgabe in Microsoft 365 dar. |
| Diagrammplanerplan | Die Tabelle "Diagrammplanplan" stellt einen Planner-Plan in Microsoft 365 dar. |
| Graph-Ereignis | Die Graph-Ereignistabelle stellt ein Ereignis in einem Benutzerkalender oder den Standardkalender einer Microsoft 365-Gruppe dar. |
| Graph-Buchungstermin | Die Tabelle "Graph-Buchungstermin" stellt einen Kundentermin für einen Buchungsdienst dar, der von einer Gruppe von Mitarbeitern ausgeführt wird, die von einem Microsoft Bookings Unternehmen hervorgehoben wurde. |
| Graph-Laufwerk | Die Tabelle "Graph-Laufwerk" stellt das Objekt der obersten Ebene dar, das oneDrive eines Benutzers oder eine Dokumentbibliothek in SharePoint darstellt. |
| Graph-Laufwerkelement | Die Tabelle "Graph-Laufwerkelement" stellt eine Datei, einen Ordner oder ein anderes Element dar, das auf einem Laufwerk gespeichert ist. |

## <a name="graph-planner-task"></a>Graph Planner-Aufgabe

* Entitätsname: m365_graphplannertask.
* Graph-Ressource: [plannerTask-Ressourcentyp](/graph/api/resources/plannertask)
* Das Sortieren wird nicht unterstützt.
* Das Filtern wird nicht unterstützt.
* Die servergesteuerte Paginierung wird unterstützt, wobei die maximale Seitengröße 400 beträgt.

### <a name="attributes-for-graph-planner-task"></a>Attribute für Graph Planner-Aufgabe

| Spalte  | Dataverse Type | Details |
|---|---|---|
| `m365_collaborationrootid` | Zeichenfolge | Die Stamm-ID der Zusammenarbeitssitzung ist mehreren Zusammenarbeitssitzungen zugeordnet. Dies wird als durch Kommas getrennte Zeichenfolge zurückgegeben. Beachten Sie, dass dieses Attribut beim Abrufen mehrerer Datensätze nicht zurückgegeben wird. |
| `m365_activechecklistitemcount` | Int32 | Anzahl der Prüflistenelemente, deren Wert auf "false" festgelegt ist, was unvollständige Elemente darstellt. |
| `m365_graphplannertaskId` | Guid | Eindeutiger Bezeichner der Diagrammplaneraufgabe. |
| `m365_appliedcategories` | Zeichenfolge | Anzahl der Prüflistenelemente, deren Wert auf "false" festgelegt ist, was unvollständige Elemente darstellt. |
| `m365_appliedcategories` | Zeichenfolge | Die Kategorien, auf die die Aufgabe angewendet wurde. Dieses Attribut ist eine JSON-codierte Zeichenfolge, z. B. "{ \"category1\": true, \"category6\": true, \"category9\": true }" |
| `m365_assigneepriority` | Zeichenfolge | Hinweis, der zum Bestellen von Elementen dieses Typs in einer Listenansicht verwendet wird. Das Format wird [mithilfe von Reihenfolgenhinweisen in Planner](/graph/api/resources/planner-order-hint-format) definiert. |
| `m365_assignments` | Zeichenfolge | Die Gruppe der Zugewiesenen, der die Aufgabe zugewiesen ist. Dieses Attribut ist eine JSON-codierte Zeichenfolge, z. B. "{\" 7be...\": {\"assignedBy\": {\"user\": {\"displayName\", \"email\", \"ID\":\" 7be...\"}, \"group\": null, \"application\": null \"device\": null}" |
| `m365_bucketid` | String | Bucket-ID, zu der die Aufgabe gehört. Der Bucket muss in dem Plan enthalten sein, in dem sich die Aufgabe befindet. Es ist 28 Zeichen lang, wobei die Groß-/Kleinschreibung beachtet wird. Für den Dienst wird eine [Formatüberprüfung](/graph/api/resources/planner-identifiers-disclaimer) durchgeführt. |
| `m365_checklistitemcount` | Int32 | Anzahl der Prüflistenelemente, die für die Aufgabe vorhanden sind. |
| `m365_completedby` | Zeichenfolge | Die Identität des Benutzers, der die Aufgabe abgeschlossen hat. Dieses Attribut ist eine JSON-codierte Zeichenfolge, z. B. {\"user: {\"displayName,ID\"\"\":\"d55...\"}}\" |
| `m365_completeddatetime` | DateTime | Schreibgeschützt. Datum und Uhrzeit, zu dem das "percentComplete" des Vorgangs auf "100" festgelegt ist. Der Timestamp-Typ stellt die Datums- und Uhrzeitinformationen mithilfe des ISO 8601-Formats dar und wird immer in UTC-Zeit angegeben. Mitternacht UTC-Zeit am 1. Januar 2014 ist beispielsweise der 01.01.2014. |
| `m365_conversationthreadid` |Zeichenfolge | Thread-ID der Unterhaltung für die Aufgabe. Dies ist die ID des Unterhaltungsthreadobjekts, das in der Gruppe erstellt wurde. |
| `m365_createdby` | Zeichenfolge | Die Identität des Benutzers, der die Aufgabe erstellt hat. Dieses Attribut ist eine JSON-codierte Zeichenfolge, z. B. {\"user: {\"displayName,ID\"\"\":\"d55...\"}}\" |
| `m365_createddatetime` | DateTime | Schreibgeschützt. Datum und Uhrzeit der Erstellung der Aufgabe. Der Timestamp-Typ stellt die Datums- und Uhrzeitinformationen mithilfe des ISO 8601-Formats dar und wird immer in UTC-Zeit angegeben. Mitternacht UTC-Zeit am 1. Januar 2014 ist beispielsweise der 01.01.2014. |
| `m365_duedatetime` | DateTime | Datum und Uhrzeit der Fälligkeit der Aufgabe. Der Timestamp-Typ stellt die Datums- und Uhrzeitinformationen mithilfe des ISO 8601-Formats dar und wird immer in UTC-Zeit angegeben. Mitternacht UTC-Zeit am 1. Januar 2014 ist beispielsweise der 01.01.2014. |
| `m365_hasdescription` | Boolesch | Schreibgeschützt. Der Wert ist "true", wenn das Detailobjekt der Aufgabe eine nicht leere Beschreibung aufweist, andernfalls "false". |
| `m365_id` | Zeichenfolge | Schreibgeschützt. ID der Aufgabe. Es ist 28 Zeichen lang, wobei die Groß-/Kleinschreibung beachtet wird. Für den Dienst wird eine [Formatüberprüfung](/graph/api/resources/planner-identifiers-disclaimer) durchgeführt.|
| `m365_orderhint` | Zeichenfolge | Hinweis, der zum Bestellen von Elementen dieses Typs in einer Listenansicht verwendet wird. Das Format wird [mithilfe von Reihenfolgenhinweisen in Planner](/graph/api/resources/planner-order-hint-format) definiert. |
| `m365_percentcomplete` | Int32 | Prozentsatz des Vorgangsabschlusses. Wenn der Wert auf 100 festgelegt ist, gilt die Aufgabe als abgeschlossen. |
| `m365_priority` | Int32 | Priorität der Aufgabe. Der gültige Wertebereich liegt zwischen 0 und 10, wobei der zunehmende Wert eine niedrigere Priorität hat (0 hat die höchste Priorität und 10 die niedrigste Priorität). Derzeit interpretiert Planner die Werte 0 und 1 als "dringend", 2, 3 und 4 als "wichtig", 5, 6 und 7 als "mittel" und 8, 9 und 10 als "niedrig". Darüber hinaus legt Planner den Wert 1 für "dringend", 3 für "wichtig", 5 für "mittel" und 9 für "niedrig" fest. |
| `m365_planid` | String | Plan-ID, zu der die Aufgabe gehört. |
| `m365_previewtype` | Zeichenfolge | Hierdurch wird der Typ der Vorschau festgelegt, die für die Aufgabe angezeigt wird. Die möglichen Werte sind: automatic, noPreview, checklist, description, reference. |
| `m365_referencecount` | Int32 | Anzahl externer Bezüge, die für die Aufgabe vorhanden sind.|
| `m365_startdatetime` | DateTime | Datum und Uhrzeit des Aufgabenbeginns. Der Timestamp-Typ stellt die Datums- und Uhrzeitinformationen mithilfe des ISO 8601-Formats dar und wird immer in UTC-Zeit angegeben. Mitternacht UTC-Zeit am 1. Januar 2014 ist beispielsweise der 01.01.2014. |
| `m365_title` | String |Titel der Aufgabe. Primäre Nachschlagespalte |

## <a name="graph-planner-plan"></a>Diagrammplanerplan

* Entitätsname: m365_graphplannerplan.
* Graph-Ressource: [plannerPlan-Ressourcentyp](/graph/api/resources/plannerplan).
* Das Sortieren wird nicht unterstützt.
* Das Filtern wird nicht unterstützt.
* Die servergesteuerte Paginierung wird unterstützt, wobei die maximale Seitengröße 400 beträgt.

### <a name="attributes-for-graph-planner-plan"></a>Attribute für den Diagrammplanplan

| Spalte  | Dataverse Type | Details |
|---|---|---|
| `m365_collaborationrootid` | Zeichenfolge | Die Stamm-ID der Zusammenarbeitssitzung, der der Datensatz zugeordnet ist. Wenn der Datensatz mehreren Zusammenarbeitssitzungen zugeordnet ist, wird dies als durch Kommas getrennte Zeichenfolge zurückgegeben. Beachten Sie, dass dieses Attribut beim Abrufen mehrerer Datensätze nicht zurückgegeben wird.|
| `m365_graphplannerplanid` |Guid |Eindeutiger Bezeichner des Diagrammplanplans.|
| `m365_createdby` | Zeichenfolge | Die Identität des Benutzers, der die Aufgabe erstellt hat. Dieses Attribut ist eine JSON-codierte Zeichenfolge, z. B. {\"user: {\"displayName,ID\"\"\":\"d55...\"}}\" |
| `m365_createddatetime` | DateTime | Schreibgeschützt. Datum und Uhrzeit der Erstellung der Aufgabe. Der Timestamp-Typ stellt die Datums- und Uhrzeitinformationen mithilfe des ISO 8601-Formats dar und wird immer in UTC-Zeit angegeben. Mitternacht UTC-Zeit am 1. Januar 2014 ist beispielsweise der 01.01.2014. |
| `m365_id` | Zeichenfolge | Schreibgeschützt. ID des Plans. Es ist 28 Zeichen lang, wobei die Groß-/Kleinschreibung beachtet wird. Für den Dienst wird eine [Formatüberprüfung](/graph/api/resources/planner-identifiers-disclaimer) durchgeführt.|
| `m365_owner` | Zeichenfolge | ID der [Gruppe](/graph/api/resources/group), die den Plan besitzt. Nachdem sie festgelegt wurde, kann diese Eigenschaft nicht mehr aktualisiert werden.|
| `m365_title` | Zeichenfolge | Der Titel des Plans. Primäre Nachschlagespalte |

## <a name="graph-event"></a>Graph-Ereignis

* Entitätsname: m365_graphevent
* Graph-Ressource: [Ereignisressourcentyp](/graph/api/resources/event)
* Die Sortierung wird für die folgenden Spalten unterstützt:
  * m365_lastmodifieddatetime
  * m365_createddatetime
  * m365_hasattachments
  * m365_importance
  * m365_responserequested
  * m365_sensitivity
  * m365_showas
  * m365_subject
* Das Filtern wird für die folgenden Spalten unterstützt:
  * m365_allownewtimeproposals
  * m365_lastmodifieddatetime
  * m365_createddatetime
  * m365_icaluID
  * m365_importance
  * m365_isallday
  * m365_iscancelled
  * m365_isdraft
  * m365_responserequested
  * m365_sensitivity
  * m365_showas
  * m365_subject
  * m365_type
* Die servergesteuerte Paginierung wird unterstützt.

### <a name="attributes-for-graph-event"></a>Attribute für Graph-Ereignis

| Spalte |Dataverse Type |Details |
|---|---|---|
|`m365_collaborationrootid` |Zeichenfolge |Collaboration root of the collaboration session the record is associated with. Wenn der Datensatz mehreren Zusammenarbeitssitzungen zugeordnet ist, wird dies als durch Kommas getrennte Zeichenfolge zurückgegeben. Beachten Sie, dass dieses Attribut beim Abrufen mehrerer Datensätze nicht zurückgegeben wird. |
|`m365_allownewtimeproposals` |Boolesch |True, wenn der Besprechungsorganisator eingeladenen Benutzern erlaubt, eine neue Uhrzeit vorzuschlagen, wenn sie antworten. Andernfalls "false", was optional ist. Der Standardwert ist „true“. |
|`m365_attendees` |Zeichenfolge |Die Sammlung der Teilnehmer des Ereignisses. Dieses Attribut ist eine JSON-codierte Zeichenfolge mit maximal 15000 Länge. Beispiel: [{{type:required,status\"\"\":{{\"response\":\"none,time\"\"\":\"0001-01-01T00:00:00Z\"}},\"emailAddress\":\"test@contoso.com\"}}]\"\"\" |
|`m365_body` |Zeichenfolge |Der Text der Nachricht, die mit diesem Ereignis verknüpft ist. Er kann im HTML- oder Textformat vorliegen. Dieses Attribut ist eine JSON-codierte Zeichenfolge mit maximal 15000 Länge. Beispiel: {\"contentType\":\"html,content\"\"\":\"html/html\"} |
|`m365_bodypreview` |Zeichenfolge |Die Vorschau der Nachricht, die dem Ereignis zugeordnet ist Liegt im Textformat vor. |
|`m365_categories` |String |Die Kategorien, die mit dem Ereignis verknüpft sind. Jeder Kategorie entspricht der displayName-Eigenschaft einer für den Benutzer definierten outlookCategory. Beispiel: [\"string\"] |
|`m365_changekey` |Zeichenfolge |Identifies the version of the event object. Every time the event is changed, ChangeKey changes as well. This allows Exchange to apply changes to the correct version of the object. |
|`m365_createddatetime` |DateTime |Der Timestamp-Typ stellt die Datums- und Uhrzeitinformationen mithilfe des ISO 8601-Formats dar und wird immer in UTC-Zeit angegeben. Mitternacht UTC-Zeit am 1. Januar 2014 ist beispielsweise der 01.01.2014. |
|`m365_start` |DateTime |Startdatum, Uhrzeit und Zeitzone des Ereignisses. Dieses Attribut ist eine JSON-codierte Zeichenfolge mit maximal 100 Längen. Beispiel: {\"dateTime\":\"2022-01-19T11:00:00+00:00,timeZone\"\"\":\"UTC}\"|
|`m365_end` |DateTime |Datum, Uhrzeit und Zeitzone für das Ende des Ereignisses. Dieses Attribut ist eine JSON-codierte Zeichenfolge mit maximal 100 Längen. Beispiel: {\"dateTime\":\"2022-01-19T11:00:00+00:00,timeZone\"\"\":\"UTC}\" |
|`m365_hasattachments` |Boolean |„true“, wenn das Ereignis Anlagen hat |
|`m365_hideattendees` |Boolesch |Bei Festlegung auf "true" sieht sich jeder Teilnehmer nur in der Liste der Besprechungsanfragen und der Besprechungsnachverfolgung. Der Standardwert ist „false“. |
|`m365_icaluid` |String |Ein eindeutiger Bezeichner für ein Ereignis in mehreren Kalendern. Diese ID ist für jedes Vorkommen in einer wiederkehrenden Serie unterschiedlich. Schreibgeschützt. |
|`m365_isallday`|Boolesch |Set to true if the event lasts all day. If true, regardless of whether it's a single-day or multi-day event, start and end time must be set to midnight and be in the same time zone. |
|`m365_iscancelled` |Boolean |„true“, wenn das Ereignis abgesagt wurde |
|`m365_id`| Zeichenfolge |Schreibgeschützt. ID des Ereignisses. |
|`m365_isdraft` |Boolesch |Auf "true" festgelegt, wenn der Benutzer die Besprechung in Outlook aktualisiert, die Updates aber nicht an die Teilnehmer gesendet hat. "false", wenn alle Änderungen gesendet wurden oder wenn es sich bei dem Ereignis um einen Termin ohne Teilnehmer handelt.|
|`m365_isonlinemeeting`|Boolesch|True, wenn dieses Ereignis Informationen zu Onlinebesprechungen enthält (d. h. onlineMeeting verweist auf eine onlineMeetingInfo-Ressource), andernfalls false. Der Standardwert ist "false" (onlineMeeting ist null). Optional. Nachdem Sie "isOnlineMeeting" auf "true" festgelegt haben, initialisiert Microsoft Graph onlineMeeting. Später ignoriert Outlook alle weiteren Änderungen an isOnlineMeeting, und die Besprechung bleibt online verfügbar.|
|`m365_isorganizer`|Boolesch|Legen Sie den Wert auf "true" fest, wenn der Kalenderbesitzer (durch die Eigenschaft Besitzer des Kalenders) der Organisator des Ereignisses ist (angegeben durch die Eigenschaft Organisator des Ereignisses). Dies gilt auch, wenn eine Stellvertretung das Ereignis im Namen des Besitzers organisiert hat.|
|`m365_isremindero`n|Boolean|„true“, wenn eingestellt ist, dass der Benutzer an das Ereignis erinnert werden soll|
|`m365_lastmodifieddatetime`|DateTime|Der Timestamp-Typ stellt die Datums- und Uhrzeitinformationen mithilfe des ISO 8601-Formats dar und wird immer in UTC-Zeit angegeben. Mitternacht UTC-Zeit am 1. Januar 2014 ist beispielsweise der 01.01.2014.|
|`m365_location`|Zeichenfolge|Der Ort des Ereignisses. JSON-codierte Zeichenfolge mit maximal 4000 Länge. Beispiel: [{\"address\":null,coordinates\"\":null,displayName\"\":\"Harry\'s Bar,locationEmailAddress\"\"\":null,locationType\"\":\"default,locationUri\"\"\":null,uniqueId\"\":\"Harry\'s Bar,uniqueIdType\"\"\":\"private}\"|
|`m365_locations`|Zeichenfolge|Die Orte, an denen die Veranstaltung stattfindet. Die Eigenschaften location und locations entsprechen sich immer gegenseitig. Wenn Sie die location-Eigenschaft aktualisieren, werden alle früheren Orte in der locations-Sammlung entfernt und durch den neuen location-Wert ersetzt. JSON-codierte Zeichenfolge, max. 4000 länge.for example[{\"address\":null,coordinates\"\":null,displayName\"\":\"Harry\'s Bar,locationEmailAddress\"\"\":null,locationType\"\":\"default,locationUri\"\"\":null,uniqueId\"\":\"Harry\'s Bar,uniqueIdType\"\"\":\"private\"}]|
|`m365_onlinemeeting`|Zeichenfolge|Details für einen Teilnehmer, um online an der Besprechung teilzunehmen. Der Standardwert ist null. Read-only.After you set the isOnlineMeeting and onlineMeetingProvider properties to enable a meeting online, Microsoft Graph initializes onlineMeeting. Wenn diese Einstellung festgelegt ist, bleibt die Besprechung online verfügbar, und Sie können die Eigenschaften "isOnlineMeeting", "onlineMeetingProvider" und "onlneMeeting" nicht erneut ändern. JSON-codierte Zeichenfolge, max. 4000 länge.for example{\"conferenceId\": \"String,joinUrl\"\"\": \"String,phones\"\"\": [{\"@odata.type\": \"microsoft.graph.phone\"}],\"quickDial\": \"String,tollFreeNumbers\"\"\": [\"String\"],\"tollNumber\": \"String}\"|
|`m365_onlinemeetingprovider`|Zeichenfolge|Details für einen Teilnehmer, um online an der Besprechung teilzunehmen. Der Standardwert ist null. Schreibgeschützt. Nachdem Sie isOnlineMeeting und `onlineMeetingProvider` die Eigenschaften festgelegt haben, um eine Besprechung online zu aktivieren, initialisiert Microsoft Graph onlineMeeting. Wenn diese Einstellung festgelegt ist, bleibt die Besprechung online verfügbar, und Sie können die Eigenschaften "isOnlineMeeting `onlineMeetingProvider`" und "onlneMeeting" nicht erneut ändern.|
|`m365_onlinemeetingurl`|String|Eine URL für eine Onlinebesprechung. Die Eigenschaft wird nur festgelegt, wenn ein Veranstalter in Outlook angibt, dass es sich bei einer Veranstaltung um eine Onlinebesprechung wie Skype handelt. Schreibgeschützt. Um auf die URL für die Teilnahme an einer Onlinebesprechung zuzugreifen, verwenden Sie `joinUrl`, die über die `onlineMeeting` Eigenschaft des Ereignisses verfügbar gemacht wird. Die `onlineMeetingUrl` Eigenschaft wird in Zukunft nicht mehr unterstützt.|
|`m365_organizer`|Zeichenfolge|Der Organisator der Veranstaltung. JSON-codierte Zeichenfolge mit maximal 4000 Länge. {\"emailAddress\":{\"@odata.type\":\"microsoft.graph.emailAddress\"}}|
|`m365_originalendtimezone`|String|Die Zeitzone, die bei der Erstellung des Ereignisses für das Ereignisende festgelegt wurde. Der Wert tzone://Microsoft/Custom gibt an, dass eine ältere benutzerdefinierte Zeitzone in Outlook-Desktop festgelegt wurde.|
|`m365_originalstart`|DateTime|Stellt die Startzeit eines Ereignisses dar, wenn es anfänglich als Vorkommen oder Ausnahme in einer Terminserie erstellt wird. Diese Eigenschaft wird nicht für Ereignisse zurückgegeben, die einzelne Instanzen sind. Seine Datums- und Uhrzeitinformationen werden im ISO 8601-Format ausgedrückt und immer in UTC angegeben. Mitternacht UTC-Zeit am 1. Januar 2014 ist beispielsweise der 01.01.2014.|
|`m365_originalstarttimezone`|Zeichenfolge|Die Zeitzone, die bei der Erstellung des Ereignisses für den Ereignisbeginn festgelegt wurde. Der Wert tzone://Microsoft/Custom gibt an, dass eine ältere benutzerdefinierte Zeitzone in Outlook-Desktop festgelegt wurde.|
|`m365_recurrence`|Zeichenfolge|Das Serienmuster für das Ereignis. JSON-codierte Zeichenfolge, max. 4000 länge.for example{\"pattern\":{\"dayOfMonth\":0,daysOfWeek\"\":[\"monday,wednesday,friday\"\"\"\"\"],\"firstDayOfWeek\":\"sunday,index\"\"\":\"first,interval\"\"\":1,month\"\":0,type\"\":\"weekly\"},\"range\":{\"startDate\":\"2017-08-14,endDate\"\"\":\"2018-08-14,\"\" numberOfOccurrences\":0,recurrenceTimeZone\"\":\"Eastern Standard Time,type\"\"\":\"endDate\"}}|
|`m365_reminderminutesbeforestart`|Int32|Festlegung, wie viele Minuten vor Beginn des Ereignisses die Erinnerung angezeigt werden soll|
|`m365_responserequested`|Boolesch|Der Standardwert ist "true", was bedeutet, dass der Organisator von eingeladenen Personen eine Antwort auf die Veranstaltung wünscht.|
|`m365_responsestatus`|Zeichenfolge|Typ der Antwort, die als Antwort auf eine Ereignisnachricht gesendet wurde. JSON-codierte Zeichenfolge mit maximal 4000 Länge. {\"response\": \"String,time\"\"\": \"String (timestamp)\"}|
|`m365_sensitivity`|Zeichenfolge|Mögliche Werte sind: normal, persönlich, privat, vertraulich.|
|`m365_seriesmasterid`|String|Die ID für das Terminserien-Masterelement, wenn das Ereignis zu einer Terminserie gehört.|
|`m365_showas`|Zeichenfolge|Der anzuzeigende Status. Mögliche Werte sind: frei, mit Vorbehalt, beschäftigt, oof, workingElsewhere, unbekannt.|
|`m365_subject`|String|Der Text der Betreffzeile des Ereignisses Primäre Nachschlagespalte|
|`m365_transactionid`|Zeichenfolge|Ein benutzerdefinierter Bezeichner, der von einer Client-App für den Server angegeben wird, um redundante POST-Vorgänge zu vermeiden, wenn der Client erneut versucht, dasselbe Ereignis zu erstellen. Dies ist nützlich, wenn geringe Netzwerkkonnektivität dazu führt, dass der Client eine Zeitüberschreitung ausgibt, bevor eine Antwort vom Server für die Anforderung des Clients vor der Ereigniserstellung eingeht. Nachdem Sie beim Erstellen eines Ereignisses festgelegt `transactionId` haben, können Sie transactionId in einer nachfolgenden Aktualisierung nicht mehr ändern. Diese Eigenschaft wird nur bei einer Antwortnutzlast zurückgegeben, wenn sie von einer App festgelegt wurde. Optional.|
|`m365_type`|Zeichenfolge|Der Ereignistyp. Mögliche Werte sind: singleInstance, occurrence, exception, seriesMaster. Schreibgeschützt|
|`m365_weblink`|Zeichenfolge|Die URL zum Öfnen des Ereignisses in Outlook im Web. Outlook im Web öffnet das Ereignis im Browser, wenn Sie bei Ihrem Postfach angemeldet sind. Andernfalls werden Sie von Outlook im Web aufgefordert, sich anzumelden. Auf diese URL kann in einem iFrame nicht zugegriffen werden.|
|`m365_grapheventid`|Guid|Eindeutiger Bezeichner des Diagrammereignisses.|
|`m365_groupid`|Zeichenfolge|Gruppen-ID, zu der das Ereignis gehört.|

## <a name="graph-booking-appointment"></a>Graph-Buchungstermin

* Entitätsname: m365_graphbookingappointment
* Graph-Ressource: [bookingAppointment-Ressourcentyp](/graph/api/resources/bookingappointment)
* Das Sortieren wird nicht unterstützt.
* Das Filtern wird für die folgenden Spalten unterstützt:
  * m365_bookingbusinessID
  * m365_collaborationrootID
  * m365_customertimezone
  * m365_optoutofcustomeremail
  * m365_price
  * m365_pricetype
  * m365_serviceID
  * m365_servicename
* Paginierung wird nicht unterstützt.

### <a name="attributes-for-graph-booking-appointment"></a>Attribute für Graph Booking Appointment

| Spalte  | Dataverse Type | Details |
|---|---|---|
| `m365_collaborationrootid`| Zeichenfolge| Die Stamm-ID der Zusammenarbeitssitzung, der der Datensatz zugeordnet ist. Wenn der Datensatz mehreren Zusammenarbeitssitzungen zugeordnet ist, wird dies als durch Kommas getrennte Zeichenfolge zurückgegeben. Beachten Sie, dass dieses Attribut beim Abrufen mehrerer Datensätze nicht zurückgegeben wird.|
| `m365_graphbookingappointmentid` | Guid | Eindeutiger Bezeichner des Diagrammbuchungstermins.|
| `m365_bookingbusinessid` | Zeichenfolge | Der eindeutige Bezeichner des Buchungsgeschäfts, unter dem der Termin geplant ist.|
| `m365_additionalinformation` | Zeichenfolge | Zusätzliche Informationen, die an den Kunden gesendet werden, wenn ein Termin bestätigt wird.|
| `m365_customers` | Zeichenfolge| Es listet die Kundeneigenschaften für einen Termin auf. Der Termin enthält eine Liste der Kundeninformationen, und jede Einheit gibt die Eigenschaften eines Kunden an, der Teil dieses Termins ist. Optional[{\"customerID\":\"d243c77b-f1ff-4615-a01f-1660b5cb0e79,customQuestionAnswers\"\"\":[],\"emailAddress\":\"jordanm@contoso.com,location\"\"\":{\"address\":{\"city\":\"\",\"countryOrRegion\":\"\",\"postalCode\":\"\",\"postOfficeBox,state\"\"\":\"\",\"street\":\"\",\"type\" },\"coordinates\":{\" Genauigkeit,Höhe,altitudeAccuracy,latitude,longitude\"\"\"\"\"\"\"\"\" },\"displayName\":\"\",\"locationEmailAddress,locationType,locationUri\"\"\"\"\":\"\",\"uniqueID,uniqueIDType\"\"\" },\"name\":\"Jordan Miller,notes,phone,timeZone\"\"\"\"\"\"\",\"@odata.type:\"\" #microsoft.graph.bookingCustomerInformation\"}] |
| `m365_customertimezone` | Zeichenfolge | Die Zeitzone des Kunden. Eine Liste der möglichen Werte finden Sie unter ["dateTimeTimeZone"-Ressourcentyp](/graph/api/resources/datetimetimezone). |
| `m365_duration` | Zeichenfolge | Die Länge des Termins im ISO8601-Format.|
| `m365_enddatetime` | DateTime | Das Datum, die Uhrzeit und die Zeitzone, mit der der Termin endet.|
| `m365_filledattendeescount` | Int32 | Die aktuelle Anzahl der Kunden im Termin.|
| `m365_id` | Zeichenfolge | Die ID des bookingAppointment.The ID of the bookingAppointment. Schreibgeschützt.|
| `m365_islocationonline` | Boolesch | True gibt an, dass der Termin online abgehalten wird. Standardwert ist "false".|
| `m365_joinweburl` | Zeichenfolge | Die URL der Onlinebesprechung für den Termin.|
| `m365_maximumattendeescount` | Int32 | Die maximale Anzahl von Kunden, die in einem Termin zulässig sind.|
| `m365_optoutofcustomeremail` | Boolesch | True gibt an, dass der bookingCustomer für diesen Termin keine Bestätigung für diesen Termin erhalten möchte.|
| `m365_postbuffer` | Zeichenfolge | Die Zeitdauer, die nach Ablauf des Termins für die Bereinigung reserviert werden muss, als Beispiel. Der Wert wird im ISO8601-Format ausgedrückt.|
| `m365_prebuffer` | Zeichenfolge | Der Zeitraum, der reserviert werden muss, bevor der Termin beginnt, als Beispiel für die Vorbereitung. Der Wert wird im ISO8601-Format ausgedrückt.|
| `m365_price` | Decimaltype.fromobject | Der reguläre Preis für einen Termin für den angegebenen bookingService.|
| `m365_pricetype` | Zeichenfolge | Eine Einstellung, die Flexibilität für die Preisstruktur von Diensten bietet. Mögliche Werte sind: undefined, fixedPrice, startingAt, stündlich, kostenlos, priceVaries, callUs, notSet.|
| `m365_reminders` | Zeichenfolge | Die Sammlung von Kundenerinnerungen, die für diesen Termin gesendet wurden. Der Wert dieser Eigenschaft ist nur verfügbar, wenn dieser bookingAppointment anhand seiner ID gelesen wird. [{\"message\":\"We forward to seeing you!\",\"offset\":\"P1D,recipients\"\"\":\"customer\"},{\"message\":\"Reminder that you have an appointment!\",\"offset\":\"P1D,recipients\"\"\":\"staff\"}] |
| `m365_selfserviceappointmentid` | Zeichenfolge | Eine weitere Tracking-ID für den Termin, wenn der Termin direkt vom Kunden auf der Terminplanungsseite erstellt wurde, im Gegensatz zu einem Mitarbeiter im Auftrag des Kunden.|
| `m365_serviceid` | Zeichenfolge | Die ID des bookingService, der diesem Termin zugeordnet ist.|
| `m365_servicelocation` | Zeichenfolge | Der Ort, an dem der Dienst bereitgestellt wird. {\"address\":{\"city\":\"\",\"countryOrRegion\":\"\",\"postalCode\":\"\",\"postOfficeBox,state\"\"\":\"\",\"street\":\"\",\"type\" },\"coordinates\":{\"accuracy,altitude,altitudeAccuracy,latitude,longitude\"\"\"\"\"\"\"\"\" },\"displayName\":\"Our office address,locationEmailAddress\"\" \",\"locationType,locationUri\"\"\":\"\",\"uniqueID,uniqueIDType\"\"\" } |
| `m365_servicename` | Zeichenfolge | Der Name des bookingService, der diesem Termin zugeordnet ist. Diese Eigenschaft ist optional beim Erstellen eines neuen Termins. Wenn nicht angegeben, wird es aus dem Dienst berechnet, der dem Termin durch die serviceID-Eigenschaft zugeordnet ist. |
| `m365_servicenotes` |Zeichenfolge | Notizen von einem bookingStaffMember. Der Wert dieser Eigenschaft ist nur verfügbar, wenn dieser bookingAppointment anhand seiner ID gelesen wird.|
| `m365_smsnotificationsenabled` | Boolesch | "True" gibt an, dass SMS-Benachrichtigungen für den Termin an die Kunden gesendet werden. Standardwert ist "false".|
| `m365_staffmemberids` | Zeichenfolge | Die ID jedes bookingStaffMembers, der in diesem Termin geplant ist. Wird als durch Kommas getrennte Zeichenfolge gespeichert. [\"string\"] |
| `m365_startdatetime` | DateTime | Das Datum, die Uhrzeit und die Zeitzone, mit der der Termin beginnt.|

## <a name="graph-drive"></a>Graph-Laufwerk

* Entitätsname: m365_graphdrive
* Graph-Ressource: [Laufwerksressourcentyp](/graph/api/resources/drive)
* Das Sortieren wird nicht unterstützt.
* Das Filtern wird nicht unterstützt.
* Die servergesteuerte Paginierung wird unterstützt.

### <a name="attributes-for-graph-drive"></a>Attribute für Graph Drive

|Spalte |Dataverse Type |Details |
|---|---|---|
|`m365_collaborationrootid` |Zeichenfolge | Die Stamm-ID der Zusammenarbeitssitzung, der der Datensatz zugeordnet ist. Wenn der Datensatz mehreren Zusammenarbeitssitzungen zugeordnet ist, wird dies als durch Kommas getrennte Zeichenfolge zurückgegeben. Beachten Sie, dass dieses Attribut beim Abrufen mehrerer Datensätze nicht zurückgegeben wird. |
|`m365_createdby` |Zeichenfolge |Die Identität des Benutzers, Geräts oder der Anwendung, die das Element erstellt hat. Schreibgeschützt. Dieses Attribut ist eine JSON-codierte Zeichenfolge, z. B. { "user": { "displayName": "System Account" } } |
|`m365_createddatetime` |DateTime |Datum und Uhrzeit der Elementerstellung. Schreibgeschützt. |
|`m365_description` |Zeichenfolge |Stellt eine für den Benutzer sichtbare Beschreibung des Laufwerks bereit. Schreibgeschützt. |
|`m365_drivetype` |Zeichenfolge |Beschreibt den Typ des Laufwerks, der durch diese Ressource dargestellt wird. Persönliche OneDrive-Laufwerke geben persönliche Laufwerke zurück. OneDrive for Business wird das Geschäft zurückgeben. SharePoint-Dokumentbibliotheken geben documentLibrary zurück. Schreibgeschützt. |
|`m365_graphdriveid` |Guid |Eindeutiger Bezeichner des Diagrammlaufwerks. |
|`m365_id` |Zeichenfolge |Der eindeutige Bezeichner des Laufwerks. Schreibgeschützt. |
|`m365_lastmodifiedby` | Zeichenfolge |Die Identität des Benutzers, des Geräts und der Anwendung, durch die das Element zuletzt geändert wurde. Schreibgeschützt. Dieses Attribut ist eine JSON-codierte Zeichenfolge, z. B. { "user": { "email": "user@contoso.com", "ID": "61de164e-21ff-4b1c-8cbd-77ac440894f8", "displayName": "User Name" } } |
|`m365_lastmodifieddatetime` |DateTime |Datum und Uhrzeit der letzten Änderung des Elements. Schreibgeschützt.|
|`m365_name` |Zeichenfolge |Der Name des Elements. Schreibgeschützt. |
|`m365_owner` |Zeichenfolge |Optional. Das Benutzerkonto, das das Laufwerk besitzt. Schreibgeschützt. Dieses Attribut ist eine JSON-codierte Zeichenfolge. Beispiel: { "group": { "ID": "76c7286f-8645-4ba8-bc0f-c65a16424aaa", "displayName": "Group Name" }} |
|`m365_quota` |Zeichenfolge |Optional. Informationen zum Speicherkontingent des Laufwerks. Schreibgeschützt. Dieses Attribut ist eine JSON-codierte Zeichenfolge. Beispiel: { "deleted": 482586, "remaining": 27487788645969, "state": "normal", "total": 27487790694400, "used": 1565845 } |
|`m365_sharepointids` |Zeichenfolge |Gibt Bezeichner zurück, die für die SharePoint REST-Kompatibilität nützlich sind. Schreibgeschützt. Diese Eigenschaft wird nicht standardmäßig zurückgegeben und muss mithilfe des $select Abfrageparameters ausgewählt werden. Dieses Attribut ist eine JSON-codierte Zeichenfolge. Beispiel: "sharePointIDs": { "listID": "29d8457a-8e26-4291-9901-09718a388aaa", "siteID": "93618739-b3ca-4107-a77c-fba278c48aaa", "siteUrl": "<https://contoso.sharepoint.com>", "tenantID": "53986071-de92-43ad-a41f-f3c4adb2beef", "webID": "a0d0e9ec-e547-4338-92d9-4c2c62e5beef" } |
| `m365_siteid` |Zeichenfolge |Der Bezeichner für die Website, die die Dokumentbibliothek enthält.
|`m365_system` |Zeichenfolge |Falls vorhanden, gibt an, dass es sich um ein vom System verwaltetes Laufwerk handelt. Schreibgeschützt.
|`m365_weburl` |Zeichenfolge |URL, über die die Ressource im Browser angezeigt werden kann. Schreibgeschützt.

### <a name="graph-drive-item"></a>Graph-Laufwerkelement

* Entitätsname: m365_graphdriveitem
* Graph-Ressource: [driveItem-Ressourcentyp](/graph/api/resources/driveitem)
* Die Sortierung wird für die folgende Spalte unterstützt:
  * m365_name
* Das Filtern wird in der folgenden Spalte unterstützt:
  * m365_name
* Die servergesteuerte Paginierung wird unterstützt.

### <a name="attributes-for-graph-drive-item"></a>Attribute für Das Graph-Laufwerkelement

|Spalte |Dataverse Type |Details |
|---|---|---|
|`m365_audio` |Zeichenfolge |Audiometadaten, wenn das Element eine Audiodatei ist. Schreibgeschützt. Nur auf OneDrive Personal. Dieses Attribut ist eine JSON-codierte Zeichenfolge. { "album": "string", "albumArtist": "string", artist": "string", bitrate": 128, "composers": "string", copyright": "string", "disc": 0, "discCount": 0, "duration": 567, "genre": "string", "hasDrm": false, "isVariableBitrate": false, "title": "string", "track": 1, "trackCount": 16, "year": 2014 }|
|`M365_bundle` |Zeichenfolge |Bündelmetadaten, wenn das Element ein Bündel ist. Schreibgeschützt. Dieses Attribut ist eine JSON-codierte Zeichenfolge. Beispiel: { "childCount": 3, "album": { "@odata.type": "microsoft.graph.album" }, } |
|`m365_collaborationrootid` |Zeichenfolge |Die Stamm-ID der Zusammenarbeitssitzung, der der Datensatz zugeordnet ist. Wenn der Datensatz mehreren Zusammenarbeitssitzungen zugeordnet ist, wird dies als durch Kommas getrennte Zeichenfolge zurückgegeben. Beachten Sie, dass dieses Attribut beim Abrufen mehrerer Datensätze nicht zurückgegeben wird. |
|`m365_copy` |Zeichenfolge |Wenn die Anforderung vorhanden ist, wird ein Kopiervorgang ausgeführt. |
|`m365_createdby` |Zeichenfolge |Die Identität des Benutzers, des Geräts und der Anwendung, die das Element erstellt haben. Schreibgeschützt. Dieses Attribut ist eine JSON-codierte Zeichenfolge. Beispiel: {"user":{"displayName":"User Name","email":"alias@contoso.com","ID":"a298b975-3493-4d9e-b2d4-3cad78f00000"},"group": null,"application","device" } |
|`m365_createddatetime` |DateTime |Datum und Uhrzeit der Elementerstellung. Schreibgeschützt. |
|`m365_ctag` |Zeichenfolge |Ein ETag für den Inhalt des Elements. Dieses eTag wird nicht geändert, wenn nur die Metadaten geändert werden. Hinweis. Diese Eigenschaft wird nicht zurückgegeben, wenn es sich bei dem Element um einen Ordner handelt. Schreibgeschützt. |
|`m365_deleted` |Zeichenfolge |Informationen zum „gelöscht“-Zustand des Elements. Schreibgeschützt. Dieses Attribut ist eine JSON-codierte Zeichenfolge. Beispiel: { "state": "string" } |
|`m365_description` |Zeichenfolge |Stellt eine für den Benutzer sichtbare Beschreibung des Elements bereit. Lese-/Schreibzugriff. Nur auf OneDrive Personal. |
|`m365_driveid` |Zeichenfolge |Der Bezeichner für das Laufwerk, das das Laufwerkelement enthält.|
|`m365_etag` |Zeichenfolge |ETag des gesamten Elements (Metadaten + Inhalt). Schreibgeschützt. |
| `m365_file` |Zeichenfolge |Dateimetadaten, wenn das Element eine Datei ist. Schreibgeschützt. Dieses Attribut ist eine JSON-codierte Zeichenfolge. Beispiel: {"hashes":{"crc32Hash","quickXorHash":"Biuzvwdu+Tmu6yRefayD27hD9vD=","sha1Hash","sha256Hash" },"mimeType":"application/vnd.openxmlformats-officedocument.wordprocessingml.document","processingMetadata" } |
| `m365_filesysteminfo` |Zeichenfolge |Informationen zum Dateisystem des Clients. Dieses Attribut ist eine JSON-codierte Zeichenfolge. Beispiel: {"createdDateTime":"2022-07-21T15:02:47+00:00","lastAccessedDateTime","lastModifiedDateTime":"2022-07-21T15:02:55+00:00"} |
|`m365_folder` |Zeichenfolge | Ordnermetadaten, wenn das Element ein Ordner ist. Schreibgeschützt. Dieses Attribut ist eine JSON-codierte Zeichenfolge. Beispiel: {"childCount":0,"view" } |
|`m365_graphdriveitemid` |Guid |Eindeutiger Bezeichner des Diagrammlaufwerkelements. |
|`m365_id` |Zeichenfolge |Der eindeutige Bezeichner des Elements im Laufwerk. Schreibgeschützt. |
|`m365_image` |Zeichenfolge |Bildmetadaten, wenn das Element ein Bild ist. Schreibgeschützt. Dieses Attribut ist eine JSON-codierte Zeichenfolge. Beispiel: {"height","width" } |
|`m365_lastmodifiedby` |Zeichenfolge |Die Identität des Benutzers, des Geräts und der Anwendung, durch die das Element zuletzt geändert wurde. Schreibgeschützt. Dieses Attribut ist eine JSON-codierte Zeichenfolge. Beispiel: {"user":{"displayName":"User Name","email":"alias@contoso.com","ID":"a298b975-3493-4d9e-b2d4-3cad78f9a00e"},"group","application","device" } |
|`m365_lastmodifieddatetime` |DateTime |Datum und Uhrzeit der letzten Änderung des Elements. Schreibgeschützt. |
|`m365_location` |Zeichenfolge |Standortmetadaten, sofern das Element Standortdaten aufweist. Schreibgeschützt. Dieses Attribut ist eine JSON-codierte Zeichenfolge. Beispiel: "location": { "altitude": 1.0, "latitude": 1.0, "longitude": 1.0 } |
|`m365_malware` |Zeichenfolge |Schadsoftware-Metadaten, wenn entdeckt wurde, dass das Element Schadsoftware enthält. Schreibgeschützt. Dieses Attribut ist eine JSON-codierte Zeichenfolge. Beispiel: { "description": "string" } |
|`m365_name` |Zeichenfolge |Der Name des Elements (Dateiname und Erweiterung). Lese-/Schreibzugriff. |
|`m365_package` |Zeichenfolge |Zeigt wenn vorhanden an, dass das Element ein Paket ist statt eines Ordners oder einer Datei. Pakete werden in einigen Kontexten wie Dateien, in anderen Kontexten wie Ordner behandelt. Schreibgeschützt. Dieses Attribut ist eine JSON-codierte Zeichenfolge. Beispiel: { "type": "oneNote" } |
|`m365_parentreference` |Zeichenfolge |Informationen zum übergeordneten Element, wenn das Element ein übergeordnetes Element hat. Dieses Attribut ist eine JSON-codierte Zeichenfolge. Beispiel: {"driveID":"b!qgK-8nOzX0qISvfGCiC2Smbv0m0RlNhDvNQDZsCMpbSnchFAhWAaQoiTLZcSo1gq","driveType":"documentLibrary","ID ":"01EYDCV4YHV77FE3EDDFHIVD6WJ2ETT3PP","name","path":"/drives/b!qgK-8nOzX0qISvfGCiC2Smbv0m0RlNhDvNQDZsCMpbSnchFAhWAaQoiTLZcSo1no/root: /folder name","shareID","sharepointIDs":{"listID":"401172a8-6085-421a-8893-2d9712a35c3c","listItemID","listItemUniqueID":"52feaf12-836c-4e19-8a8f-d64e8939ee52","siteID":" f34e02aa-b373-4a5f-884a-f7c60a20b64a","siteUrl":"https://contoso.sharepoint.com/sites/Contoso,"tenantID","webID":"6dd2ef66-9411-43d8-bcd4-0366c08ccabd"},"siteID" } |
|`m365_parentreferenceid` |Zeichenfolge |Der Bezeichner für das Laufwerkelement, das das übergeordnete Element des Laufwerkelements ist. |
|`m365_pendingoperations` |Zeichenfolge |Gibt, falls vorhanden, an, dass mindestens ein Vorgang, der sich auf den Status von driveItem auswirken kann, noch aussteht. Schreibgeschützt. Dieses Attribut ist eine JSON-codierte Zeichenfolge. Beispiel: { "pendingContentUpdate": {"@odata.type": "microsoft.graph.pendingContentUpdate"} } |
|`m365_photo` |Zeichenfolge |Fotometadaten, wenn das Element ein Foto ist. Schreibgeschützt. Dieses Attribut ist eine JSON-codierte Zeichenfolge. Beispiel: { "cameraMake": "Camera Make", "cameraModel": "Camera Model", "exposureDenominator": 1000000, "exposureNumerator": 41671, "focalLength": 4.38, "fNumber": 1.73, "iso": 70, "orientation": 6, "takenDateTime": "2020-04-29T14:17:39Z" } |
|`m365_publication` |Zeichenfolge |Stellt Informationen über den veröffentlichten oder ausgecheckten Status eines Elements an Stellen bereit, die solche Aktionen unterstützen. Diese Eigenschaft wird nicht standardmäßig zurückgegeben. Schreibgeschützt. Dieses Attribut ist eine JSON-codierte Zeichenfolge. Beispiel: {"level":"published","versionID":"2.0"} |
|`m365_remoteitem` |Zeichenfolge |Daten zum Remoteelement, wenn das Element von einem anderen Laufwerk freigegeben ist als dem, auf das zugegriffen wird. Schreibgeschützt. Dieses Attribut ist eine JSON-codierte Zeichenfolge. Beispiel: { "ID": "string", "createdBy": { "@odata.type": "microsoft.graph.IdentitySet" }, "createdDateTime": "timestamp", "file": { "@odata.type": "microsoft.graph.file" }, "fileSystemInfo": { "@odata.type": "microsoft.graph.fileSystemInfo" }, "folder": { "@odata.type": "microsoft.graph.folder" }, "image": { "@odata.type": "microsoft.graph.image" }, "lastModifiedBy": { "@odata.type": "microsoft.graph.IdentitySet" }, "lastModifiedDateTime": "timestamp", "name": "string", "package": { " @odata.type": "microsoft.graph.package" }, "parentReference": { "@odata.type": "microsoft.graph.itemReference" }, "shared": { "@odata.type": "microsoft.graph.shared" }, "sharepointIDs": { "@odata.type": "microsoft.graph.sharepointIDs" }, "specialFolder": { "@odata.type": "microsoft.graph.specialFolder" }, "size": 1024, "video": { "@odata.type": "microsoft.graph.video" }, "webDavUrl": "url", "webUrl": "url" } |
|`m365_root` |Zeichenfolge |Wenn diese Eigenschaft nicht Null ist, bedeutet dies, dass es sich bei der driveItem-Ressource um die oberste driveItem-Ressource auf dem Laufwerk handelt. |
|`m365_searchresult` |Zeichenfolge |Suchmetadaten, wenn das Element aus einem Suchergebnis stammt. Schreibgeschützt. Dieses Attribut ist eine JSON-codierte Zeichenfolge. Beispiel: { "onClickTelemetryUrl": "url" } |
|`m365_shared` |Zeichenfolge |Gibt an, dass das Element für andere freigegeben wurde, und enthält den „freigegeben“-Status des Elements. Schreibgeschützt. Dieses Attribut ist eine JSON-codierte Zeichenfolge. Beispiel: { "scope": "users", "owner": { "user": { "displayName": "User Name", "ID": "bbbb6fa48aaaaaaa" } } } |
|`m365_sharepointids` |Zeichenfolge |Gibt Bezeichner zurück, die für die SharePoint REST-Kompatibilität nützlich sind. Schreibgeschützt. Dieses Attribut ist eine JSON-codierte Zeichenfolge. z. B. {"listID":"401172a7-6085-421a-8893-2d9712a35aba","listItemID":"338","listItemUniqueID":"0edc89e5-24ea-4c6b-a019-dc51f45eeccc","siteID":"f2be02aa-b373-4a5f-884a-f7c60a20bddd","siteUrl":"https://contoso.sharepoint.com/sites/Contoso","tenantID":"1c137272-0581-487f-b195-aeeb93cc4ccc","webID":"6dd2ef66-9411-43d8-bcd4-0366c08caaaa"} |
|`m365_siteid` |Zeichenfolge |Der Bezeichner für die Website, die die Dokumentbibliothek enthält. |
|`m365_size` |IntType |Größe des Elements in Byte. Schreibgeschützt. |
|`m365_specialfolder` |Zeichenfolge |Facet, das zurückgegeben wird, wenn das aktuelle Element auch als spezieller Ordner verfügbar ist. Schreibgeschützt. Dieses Attribut ist eine JSON-codierte Zeichenfolge. Beispiel: { "name": "documents" } |
|`m365_thumbnail` |Zeichenfolge |Wenn die Anforderung vorhanden ist, werden die Miniaturansichten des Laufwerkelements abgerufen. |
|`m365_video` |Zeichenfolge |Facet, das zurückgegeben wird, wenn das aktuelle Element auch als spezieller Ordner verfügbar ist. Schreibgeschützt. Dieses Attribut ist eine JSON-codierte Zeichenfolge. Beispiel: {"bitrate": 10646968, "duration": 1050683, "height": 720, "width": 1280, "audioBitsPerSample": 16, "audioChannels": 1, "audioFormat": "PCM", "audioSamplesPerSecond": 32000, "fourCC": "H264", "frameRate": 60} |
|`m365_webdavurl` |String | WebDAV-kompatible URL für das Element. |
|`m365_weburl` |Zeichenfolge |URL, über die die Ressource im Browser angezeigt werden kann. Schreibgeschützt. |
