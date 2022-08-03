---
title: Rest-API-Referenzen zur Zusammenarbeitssteuerung und Einstellungen
author: surbhigupta
description: In diesem Modul erfahren Sie mehr über die Rest-API-Referenz zur Steuerung der Zusammenarbeit und einstellungen zum Verwalten von Einstellungen, Starten, Zuordnen und Abrufen von Zusammenarbeitsaktivitäten.
ms.localizationpriority: medium
ms.author: v-npaladugu
ms.topic: conceptual
ms.openlocfilehash: bc0a5e6834077e199c1dff26568ef2acfeb72745
ms.sourcegitcommit: 0bb822b30739e4a532a36764dad2dbf35a81ba29
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/03/2022
ms.locfileid: "67178980"
---
# <a name="collaboration-control-and-settings-rest-api-reference"></a>Rest-API-Referenz zur Zusammenarbeitssteuerung und Einstellungen

Entwickler können das Zusammenarbeitssteuerelement und die Rest-API für Einstellungen verwenden, um Einstellungen zu verwalten, Aktivitäten zur Zusammenarbeit mit ihren eigenen Geschäftsmodellentitäten zu starten, zuzuordnen und abzurufen.

> [!NOTE]
> Derzeit sind Die Steuerelemente für die Zusammenarbeit nur in der [öffentlichen Entwicklervorschau](~/resources/dev-preview/developer-preview-intro.md) verfügbar.

Dieser Artikel enthält Eine Referenz für die REST-API für die Zusammenarbeitssteuerungslösung.

## <a name="rest-operations-collaboration---custom-api"></a>REST-Vorgänge: Zusammenarbeit – Benutzerdefinierte API

|Vorgang|Beschreibung|
|---------|-----------|
|[Zuordnen einer Zuordnung zur Zusammenarbeit](/rest/api/industry/collaboration-toolkit/collaboration-custom-ap-is/associate-collaboration-map)|Ordnet eine Entität für die Zusammenarbeit einer Zusammenarbeitssitzung zu.|
|[Zusammenarbeitssitzung starten](/rest/api/industry/collaboration-toolkit/collaboration-custom-ap-is/begin-collaboration-session)|Erstellt einen Datensatz für die Zusammenarbeitssitzung, der mit einer Geschäftsentität, einem Anwendungskontext und optionalen Metadaten verknüpft ist.|
|[Zuordnung zur Zusammenarbeitskarte trennen](/rest/api/industry/collaboration-toolkit/collaboration-custom-ap-is/disassociate-collaboration-map-custom-api)|Die Zuordnung einer zugeordneten Entität zu der angegebenen Zusammenarbeitssitzung wird aufgehoben.|
|[Abrufen von Karten für die Zusammenarbeit](/rest/api/industry/collaboration-toolkit/collaboration-custom-ap-is/retrieve-collaboration-maps-custom-api)|Ruft eine Liste der Karten für die Zusammenarbeit für eine Sitzung eines bestimmten Entitätstyps ab.|
|[Abrufen der Zusammenarbeitssitzung](/rest/api/industry/collaboration-toolkit/collaboration-custom-ap-is/retrieve-collaboration-session-custom-api)|Ruft einen Datensatz für die Zusammenarbeitssitzung basierend auf den bereitgestellten Parametern ab.|
|[Aktualisieren der Zuordnung zur Zusammenarbeit](/rest/api/industry/collaboration-toolkit/collaboration-custom-ap-is/update-collaboration-map-custom-api)|Aktualisierungen einen Zuordnungsdatensatz für die Zusammenarbeit und deren Metadaten, sofern angegeben.|
|[Zusammenarbeitssitzung aktualisieren](/rest/api/industry/collaboration-toolkit/collaboration-custom-ap-is/update-collaboration-session)|Aktualisierungen einen Sitzungsdatensatz für die Zusammenarbeit und optional dessen Metadaten.|

## <a name="rest-operations-collaboration---standard-odata-apis"></a>REST-Vorgänge: Zusammenarbeit – Standard-OData-APIs

|Vorgang|Beschreibung|
|---------|-----------|
|[Abrufen der Zuordnung zur Zusammenarbeit nach ID](/rest/api/industry/collaboration-toolkit/collaboration-standard-o-data-ap-is/get-collaboration-map-by-id)|Ruft die Details aus einem Kartendatensatz für die Zusammenarbeit ab.|
|[Abrufen von Zusammenarbeitsmetadaten](/rest/api/industry/collaboration-toolkit/collaboration-standard-o-data-ap-is/get-collaboration-metadata)|Ruft eine Liste der Metadatendatensätze für die Zusammenarbeit für eine bestimmte Zuordnung zur Zusammenarbeit oder einen Namen der Stammentität für die Zusammenarbeit ab.|
|[Abrufen von Collaboration Root](/rest/api/industry/collaboration-toolkit/collaboration-standard-o-data-ap-is/get-collaboration-root)|Listet alle erstellten Zusammenarbeitssitzungen auf.|

## <a name="rest-operations-settings---custom-apis"></a>REST-Vorgänge: Einstellungen – Benutzerdefinierte APIs

|Vorgang|Beschreibung|
|---------|-----------|
|[Erstellen und Aktualisieren von Einstellungen](/rest/api/industry/collaboration-toolkit/settings-custom-ap-is/create-update-setting-custom-api)|Erstellt oder aktualisiert eine Einstellung, die sowohl dem Gruppenpfad als auch dem Namen der Einstellungsdefinition entspricht.|
|[Nulleinstellungen abrufen](/rest/api/industry/collaboration-toolkit/settings-custom-ap-is/retrieve-null-settings-custom-api)|Gibt eine Liste der Einstellungsdefinitionen zurück, die keinen Wert haben.|
|[Einstellungen abrufen](/rest/api/industry/collaboration-toolkit/settings-custom-ap-is/retrieve-settings-custom-api)|Gibt eine Liste bestimmter Einstellungen oder Einstellungen in Gruppen zurück.|

## <a name="rest-operations-settings---standard-odata-apis"></a>REST-Vorgänge: Einstellungen – Standard-OData-APIs

|Vorgang|Beschreibung|
|---------|-----------|
|[Einstellungsdefinition löschen](/rest/api/industry/collaboration-toolkit/settings-standard-o-data-ap-is/delete-settings-definition)|Löscht eine Einstellungsdefinition.|
|[Gruppe "Einstellungen löschen"](/rest/api/industry/collaboration-toolkit/settings-standard-o-data-ap-is/delete-settings-group)|Löscht eine Einstellungsgruppe.|
|[Einstellungstyp löschen](/rest/api/industry/collaboration-toolkit/settings-standard-o-data-ap-is/delete-settings-type)|Löschen sie einen Einstellungstyp.|
|[Einstellungswert löschen](/rest/api/industry/collaboration-toolkit/settings-standard-o-data-ap-is/delete-settings-value)|Löscht einen Einstellungswert.|
|[Abrufen von Einstellungsdefinitionen](/rest/api/industry/collaboration-toolkit/settings-standard-o-data-ap-is/get-settings-definitions)|Listet Einstellungsdefinitionen auf.|
|[Abrufen von Einstellungsgruppen](/rest/api/industry/collaboration-toolkit/settings-standard-o-data-ap-is/get-settings-groups)|Listet Einstellungsgruppen auf.|
|[Einstellungstypen abrufen](/rest/api/industry/collaboration-toolkit/settings-standard-o-data-ap-is/get-settings-types)|Listet Einstellungstypen auf.|
|[Einstellungswert abrufen](/rest/api/industry/collaboration-toolkit/settings-standard-o-data-ap-is/get-settings-value)|Listet Einstellungswerte auf.|
|[Patcheinstellungendefinition](/rest/api/industry/collaboration-toolkit/settings-standard-o-data-ap-is/patch-settings-definition)|Aktualisierungen einer Einstellungsdefinition.|
|[Patcheinstellungsgruppe](/rest/api/industry/collaboration-toolkit/settings-standard-o-data-ap-is/patch-settings-group)|Aktualisierungen einer Einstellungsgruppe.|
|[Patcheinstellungstyp](/rest/api/industry/collaboration-toolkit/settings-standard-o-data-ap-is/patch-settings-type)|Aktualisierungen einen Einstellungstyp.|
|[Wert für Patcheinstellungen](/rest/api/industry/collaboration-toolkit/settings-standard-o-data-ap-is/patch-settings-value)|Aktualisierungen einen Einstellungswert.|
|[Definition der Beitragseinstellungen](/rest/api/industry/collaboration-toolkit/settings-standard-o-data-ap-is/post-settings-definition)|Erstellt eine neue Einstellungsdefinition.|
|[Gruppe "Posteinstellungen"](/rest/api/industry/collaboration-toolkit/settings-standard-o-data-ap-is/post-settings-group)|Erstellt eine neue Einstellungsgruppe.|
|[Typ der Posteinstellungen](/rest/api/industry/collaboration-toolkit/settings-standard-o-data-ap-is/post-settings-type)|Erstellt einen neuen Einstellungstyp.|
|[Post Settings Value](/rest/api/industry/collaboration-toolkit/settings-standard-o-data-ap-is/post-settings-value)|Erstellt einen neuen Einstellungswert.|
