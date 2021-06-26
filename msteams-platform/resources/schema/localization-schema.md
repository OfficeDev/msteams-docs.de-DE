---
title: Referenz zum Lokalisieren des JSON-Schemas
description: Beschreibt das Lokalisierungsschema, das von der Lokalisierungsdatei für Microsoft Teams
ms.topic: reference
localization_priority: Normal
keywords: Teams-Manifestschemalokalisierung
ms.date: 05/20/2019
ms.openlocfilehash: 6e8f666cc6bfa693d7f2f469fc58fd6ee4860a80
ms.sourcegitcommit: 4d9d1542e04abacfb252511c665a7229d8bb7162
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/25/2021
ms.locfileid: "53140512"
---
# <a name="localize-json-schema-reference"></a>Referenz zum Lokalisieren des JSON-Schemas

Die Microsoft Teams Lokalisierungsdatei beschreibt Sprachübersetzungen, die basierend auf den Clientspracheneinstellungen bereitgestellt werden. Ihre Datei muss dem Schema entsprechen, das unter gehostet [`https://developer.microsoft.com/en-us/json-schemas/teams/v1.5/MicrosoftTeams.Localization.schema.json`](https://developer.microsoft.com/en-us/json-schemas/teams/v1.5/MicrosoftTeams.Localization.schema.json) wird. 

> [!TIP]
> Geben Sie das Schema am Anfang des Manifests an, um die Unterstützung über den Code-Editor zu aktivieren `IntelliSense` oder ähnlich: `"$schema": "https://developer.microsoft.com/json-schemas/teams/v1.5/MicrosoftTeams.schema.json",`

## <a name="example"></a>Beispiel 

Beispiel für das Lokalisierungs-JSON-Schema:

```json
{
  "$schema": "https://developer.microsoft.com/json-schemas/teams/v1.5/MicrosoftTeams.schema.json",
  "name.short": "Le App Studio",
  "name.full": "App Studio pour Microsoft Teams",
  "description.short": "Créez d'excellentes applications pour Microsoft Teams avec App Studio.",
  "description.full": "Créez de nouvelles applications Microsoft Teams, concevez et prévisualisez des cartes bot, et explorez la documentation avec App Studio.",
  "staticTabs[0].name": "Editeur de manifest",
  "staticTabs[1].name": "Editeur de cartes",
  "staticTabs[2].name": "Bibliothèque de contrôles",
  "bots[0].commandLists[0].commands[0].title": "chercher",
  "bots[0].commandLists[0].commands[0].description": "Rechercher la documentation Teams pertinente"
}
```

Das Schema definiert die folgenden Eigenschaften:

|Eigenschaft|Typ|Maximale Länge|Beschreibung|
|---------------|--------|---------|------------------|
|`$schema`|URI|NA|Die https:// URL, die auf das JSON-Schema für das Manifest verweist.|
|`name.short`|Zeichenfolge|30|Ersetzt die entsprechende Zeichenfolge aus dem App-Manifest durch den hier angegebenen Wert.|
|`name.full`|Zeichenfolge|100|Ersetzt die entsprechende Zeichenfolge aus dem App-Manifest durch den hier angegebenen Wert.|
|`description.short`|Zeichenfolge|80|Ersetzt die entsprechende Zeichenfolge aus dem App-Manifest durch den hier angegebenen Wert.|
|`description.full`|Zeichenfolge|4000|Ersetzt die entsprechende Zeichenfolge aus dem App-Manifest durch den hier angegebenen Wert.|
|`staticTabs\\[([0-9]|1[0-5])\\]\\.name`|Zeichenfolge|128|Ersetzt die entsprechenden Zeichenfolgen aus dem App-Manifest durch den hier angegebenen Wert.|
|`bots\\[0\\]\\.commandLists\\[[0-2]\\]\\.commands\\[[0-9]\\]\\.title`|Zeichenfolge|32|Ersetzt die entsprechenden Zeichenfolgen aus dem App-Manifest durch den hier angegebenen Wert.|
|`## bots\\[0\\]\\.commandLists\\[[0-2]\\]\\.commands\\[[0-9]\\]\\.description`|Zeichenfolge|128|Ersetzt die entsprechenden Zeichenfolgen aus dem App-Manifest durch den hier angegebenen Wert.|
|`composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.title`|Zeichenfolge|32|Ersetzt die entsprechenden Zeichenfolgen aus dem App-Manifest durch den hier angegebenen Wert.|
|`composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.description`|Zeichenfolge|128|Ersetzt die entsprechenden Zeichenfolgen aus dem App-Manifest durch den hier angegebenen Wert.|
|`composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.title`|Zeichenfolge|32|Ersetzt die entsprechende Zeichenfolge aus dem App-Manifest durch den hier angegebenen Wert.|
|`composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.description`|Zeichenfolge|128|Ersetzt die entsprechenden Zeichenfolgen aus dem App-Manifest durch den hier angegebenen Wert.|
|`composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.value`|Zeichenfolge|512|Ersetzt die entsprechende Zeichenfolge aus dem App-Manifest durch den hier angegebenen Wert.|
|`composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.choices\\[[0-9]\\]\\.title`|Zeichenfolge|128|Ersetzt die entsprechenden Zeichenfolgen aus dem App-Manifest durch den hier angegebenen Wert.|
|`composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.taskInfo\\.title`|Zeichenfolge|64|Ersetzt die entsprechenden Zeichenfolgen aus dem App-Manifest durch den hier angegebenen Wert.|

## <a name="see-also"></a>Siehe auch

> [Lokalisieren IhrerApp](~/concepts/build-and-test/apps-localization.md)
