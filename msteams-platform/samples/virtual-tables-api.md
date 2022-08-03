---
title: Web-API für virtuelle Tabellen
author: surbhigupta
description: In diesem Modul erfahren Sie mehr über die Web-API für virtuelle Tabellen für die Steuerelement-App für die Zusammenarbeit, die Sortierung virtueller Tabellen und das Filtern in Microsoft Teams.
ms.localizationpriority: medium
ms.author: v-npaladugu
ms.topic: conceptual
ms.openlocfilehash: 31784cfabccdfa861044e74be533c00f134ea851
ms.sourcegitcommit: 0bb822b30739e4a532a36764dad2dbf35a81ba29
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2022
ms.locfileid: "67179093"
---
# <a name="virtual-tables-web-api"></a>Web-API für virtuelle Tabellen

Wenn Sie die Dataverse-Web-API verwenden, um mehrere Datensätze aus einer virtuellen Tabelle abzurufen, können zusätzliche Abfrageparameter einbezogen werden, um Sortierung, Filterung und Paginierung zu unterstützen. Diese Features werden in den virtuellen Tabellen der Zusammenarbeitssteuerelemente nicht einheitlich unterstützt, da sie auf der Unterstützung durch die Microsoft Graph-API basieren. In der Entitätsreferenz für virtuelle Tabellen finden Sie Details dazu, was jede virtuelle Tabelle unterstützt.

> [!NOTE]
> Derzeit sind Die Steuerelemente für die Zusammenarbeit nur in der [öffentlichen Entwicklervorschau](~/resources/dev-preview/developer-preview-intro.md) verfügbar.

## <a name="virtual-table-sorting"></a>Sortieren virtueller Tabellen

Mit den virtuellen Tabellen können Sie den OData-$orderby Abfrageparameter verwenden, um Kriterien für die Sortierung des Resultsets festzulegen. Verwenden Sie das Asc- oder Desc-Suffix, um die aufsteigende bzw. absteigende Reihenfolge anzugeben. Der Standardwert ist aufsteigend, wenn das Suffix nicht angewendet wird.  

**Unterstützte Tabellen**: Jede virtuelle Tabelle unterstützt die gleiche Sortierfunktion wie die jeweilige Graph-Ressource. Die virtuellen Tabellen, die die Sortierung unterstützen, sind:  

* Graph-Laufwerkelement
* Graph-Ereignis

> [!NOTE]
> Das Sortieren wird nicht für alle Attribute der jeweiligen Graph-Ressourcen unterstützt. Wenn ein Benutzer versucht, nach einer virtuellen Tabelle mit einem nicht unterstützten Attribut zu sortieren, hat dieses Resultset seine Standardreihenfolge. Dies entspricht dem Verhalten der Dataverse-Web-API für Spalten, die keine Sortierung unterstützen.

Beispiele:

* GET [Organization URI]/api/data/v9.2/m365_graphdriveitems?$filter=m365_collaborationrootid eq '00000000-0000-0000-0000-00000-000000000000'&$orderby=m365_name desc
* GET [Organisations-URI]/api/data/v9.2/m365_graphevents?$filter=m365_groupid eq '00000000-0000-0000-0000-0000000000000000000000000000-$orderby m365_subject asc

## <a name="virtual-table-filtering"></a>Filtern virtueller Tabellen

Mit den virtuellen Tabellen können Sie den OData-$filter Abfrageparameter verwenden, um Kriterien festzulegen, für die Zeilen zurückgegeben werden. Die virtuellen Tabellen werden mit den gleichen OData-Operatoren abgefragt, die von der Dataverse-Web-API unterstützt werden.

* **Vergleichsoperatoren**

  |Operator|Beschreibung|Beispiel|
  |----|----|----|
  |eq|Equal|$filter=m365_name eq 'Contoso'|
  |ne|Nicht gleich|$filter=m365_name ne 'Contoso'|
  |gt|Größer als|$filter=m365_price gt 50,0|
  |ge|Größer als oder gleich|$filter=m365_price ge 50,0|
  |lt|Kleiner als|$filter=m365_price lt 50.0|
  |le|Kleiner als oder gleich|$filter=m365_price le 50,0|

* **Logische Operatoren**

  |Operator|Beschreibung|Beispiel|
  |----|----|----|
  |und|Logisches UND |$filter=m365_name Eq 'Contoso' und m365_price eq 50.0|
  |oder|Logisches ODER |$filter=m365_name ne 'Contoso' oder m365_price eq 50.0|
  |not|Logische Aushandlung |$filter=nicht enthält(m365_name;'Contoso')|

* **Gruppierungsoperatoren**

  |Operator|Beschreibung|Beispiel|
  |----|----|----|
  |( )|Rangfolgengruppierung |$filter=(m365_name eq 'Contoso' und m365_price eq 50.0) oder contains(m365_subject;'Team Sync')|

* **Abfragefunktionen**

  |Funktion |Beispiel |
  |----|----|
  |contains|$filter=contains(m365_name;'Contoso')|
  |endswith|$filter=endswith(m365_name;'Contoso')|
  |startswith|$filter=startswith(m365_name;'Contoso')|

**Unterstützte Tabellen**: Jede virtuelle Tabelle unterstützt die gleiche Filterfunktion wie die jeweilige Graph-Ressource. Die virtuellen Tabellen, die Filterung unterstützen, sind:

* Graph-Buchungstermin
* Graph-Laufwerkelement
* Graph-Ereignis

> [!Note]
> Das Filtern wird nicht für alle Attribute der jeweiligen Graph-Ressourcen unterstützt. Wenn ein Benutzer versucht, nach einer virtuellen Tabelle mit einem nicht unterstützten Attribut zu filtern, wird dieser Filter ignoriert. Dies ist dasselbe Verhalten wie die Dataverse-Web-API für Spalten, die keine Filterung unterstützen.

Beispiele:

* GET [Organisations-URI]/api/data/v9.2/m365_graphbookingappointments?$filter=m365_bookingbusinessid eq 'ContosoBank@Contoso.onmicrosoft.com' und m365_price eq 100.0
* GET [Organisations-URI]/api/data/v9.2/m365_graphdriveitems?$filter=m365_collaborationrootid eq '00000000-0000-0000-0000-0000000000000000000- und m365_name eq 'Meeting Notes.docx'
* GET [Organisations-URI]/api/data/v9.2/m365_graphevents?$filter=m365_groupid eq '00000000-0000-0000-0000-00000000000000' und m365_subject eq 'Monthly Sync'

## <a name="virtual-table-pagination"></a>Paginierung virtueller Tabellen

Paginierung ist eine nützliche Ressource zum Abrufen einer großen Gruppe von Datensätzen. Die Paginierung virtueller Tabellen kann auf drei verschiedene Arten erreicht werden.

Sie können die Seitengröße mithilfe des `odata.maxpagesize` Einstellungswerts im Anforderungsheader angeben. Wenn das Resultset mehrere Seiten umfasst, enthält die Antwort die `@odata.nextLink` Eigenschaft. Beispielanforderung und Antwort lauten wie folgt:

# <a name="request"></a>[Anforderung](#tab/request)

```http
  GET [Organization URI]/api/data/v9.2/m365_graphdriveitems 
  Accept: application/json 
  Prefer: odata.maxpagesize=2 
```

# <a name="response"></a>[Antwort](#tab/response)

```json
{ 

  "@odata.context": "[Organization URI]/api/data/v9.0/$metadata#m365_graphdriveitems", 
  "value": [ 
   { 
      "@odata.etag": "W/\"{FA93AF7C-1F45-4714-85A5-BB95EB86E1E5}\"", 
      "m365_name": "Review.doc", 
      "m365_graphdriveitemid": "f50aae23-6644-3d35-66d7-e3c5a979dad3", 
      …
      },
      {
      "@odata.etag": "W/\"{3938D549-1AEF-46A5-BF3C-38472AD934C2}\"", 
      "m365_name": "Review.doc", 
      "m365_graphdriveitemid": "3d59a7e2-ec83-d0b3-270e-8ad676622027", 
      … 
      } 
      ],
      "@odata.nextLink": "[Organization URI]/api/data/v9.0/m365_graphdriveitems &$skiptoken=%3Ccookie%20pagenumber=%222%22%20pagingcookie=%22UGFnZWQ9VFJVRSZwX1NvcnRCZWhhdmlvcj0xJnBfRmlsZUxlYWZSZWY9dGVzdCZwX0lEPTI5%22%20istracking=%22False%22%20/%3E" 
} 
```

---

Derzeit unterstützen die folgenden virtuellen Tabellen die `odata.maxpagesize` Einstellung:

* Graph-Buchungstermin
* Graph-Kalenderereignis
* Graph-Laufwerk
* Graph-Laufwerkelement

Sie können die Anzahl der zurückzugebenden Datensätze angeben, indem Sie die `$top` Option in der URL übergeben. Wenn Sie auch die Seitenzahl angeben müssen, können Sie dies tun, indem Sie ein Auslagerungscookie als XML-codierte Zeichenfolge als `$skiptoken` Option übergeben. Um eine bestimmte Seitenzahl abzurufen, können Sie das Paging-Cookie im folgenden Format übergeben:

  `<cookie pagenumber=3 />`

# <a name="request"></a>[Anforderung](#tab/request1)

```http
     GET [Organization URL]/api/data/v9.2/m365_graphevents?$top=2&$skiptoken=<cookie pagenumber='3' /> 
```

# <a name="response"></a>[Antwort](#tab/response1)

```json

{
  "@odata.context": "[Organization URI]/api/data/v9.0/$metadata#m365_graphevents", 
  "value": [
   { 
      "@odata.etag": "W/\"{FA93AF7C-1F45-4714-85A5-BB95EB86E1E5}\"", 
      "m365_graphdeventid": "3d59a7e2-ec83-d0b3-270e-8ad676622027", 
      "m365_subject": "Important meeting", 
      …
    }, 
    {
      "@odata.etag": "W/\"{3938D549-1AEF-46A5-BF3C-38472AD934C2}\"", 
      "m365_graphdeventid": "f50aae23-6644-3d35-66d7-e3c5a979dad3", 
      "m365_subject": "Another important meeting", 
      …
    } 
  ] 
}

```

---

> [!Note]
> Die Antwort enthält nicht die `@nextLink` Eigenschaft. Wenn für Ihren Anwendungsfall der Link zur nächsten Seite zurückgegeben werden muss, können Sie den in Abschnitt 1 beschriebenen Einstellungsheader "odata.maxpagesize" verwenden, anstatt den URI-Parameter $top zu übergeben.

Derzeit unterstützen die folgenden virtuellen Tabellen das Abrufen einer bestimmten Seite:

* Graph-Buchungstermin
* Graph-Kalenderereignis

Sie können ein Abruf-XML als XML-codierte Zeichenfolge übergeben. Mit der XML-Abrufoption können Sie mehrere Abfrageeinstellungen angeben. Die paginierungsspezifischen Optionen sind Seite (Seitenzahl) und Anzahl (Seitengröße). Der folgende XML-Code gibt die Seitenzahl und -größe an:

  `<fetch version="1.0" mapping="logical" returntotalrecordcount="true" page="<Page Number>" count="<Page Size>"></fetch>`

# <a name="request"></a>[Anforderung](#tab/request2)

```http
GET [Organization URL]/api/data/v9.2/m365_graphevents?$fetchXml=<fetch version="1.0" mapping="logical" returntotalrecordcount="true" page="3" count="2"></fetch> 

```

# <a name="response"></a>[Antwort](#tab/response2)

```json
{ 

    "@odata.context": "[Organization URI]/api/data/v9.0/$metadata#m365_graphdevents", 
    "@Microsoft.Dynamics.CRM.fetchxmlpagingcookie": "<cookie pagenumber=\"3\" pagingcookie=\"\" istracking=\"False\" />", 
    "value": [ 
        { 
            "@odata.etag": "W/\"{FA93AF7C-1F45-4714-85A5-BB95EB86E1E5}\"", 
            "m365_graphdeventid": "3d59a7e2-ec83-d0b3-270e-8ad676622027", 
            "m365_subject": "Important meeting", 
            …
        }, 
        { 
            "@odata.etag": "W/\"{3938D549-1AEF-46A5-BF3C-38472AD934C2}\"", 
            "m365_graphdeventid": "f50aae23-6644-3d35-66d7-e3c5a979dad3", 
            "m365_subject": "Another important meeting", 
            …
        } 
    ] 
} 

```

---

Die folgenden virtuellen Tabellen unterstützen die count-Eigenschaft, die als Teil der fetchXml-Option übergeben werden soll:

* Graph-Laufwerk
* Graph-Laufwerkelement

Die folgenden virtuellen Tabellen unterstützen die Seiteneigenschaft als Teil der fetchXml-Option:

* Graph-Buchungstermin
* Graph-Kalenderereignis
