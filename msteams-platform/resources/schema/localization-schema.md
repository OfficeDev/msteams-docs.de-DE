---
title: Json-Schemareferenz lokalisieren
description: Beschreibt das Lokalisierungsschema, das von der Lokalisierungsdatei für Microsoft Teams mithilfe eines Beispielschemas unterstützt wird.
ms.topic: reference
ms.localizationpriority: medium
ms.date: 05/20/2019
ms.openlocfilehash: 23d02e845e4fcdc1c2fc76d8e9c376479fe1fa1f
ms.sourcegitcommit: ca84b5fe5d3b97f377ce5cca41c48afa95496e28
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2022
ms.locfileid: "66144276"
---
# <a name="localize-json-schema-reference"></a>Json-Schemareferenz lokalisieren

Die Microsoft Teams Lokalisierungsdatei beschreibt Sprachübersetzungen, die basierend auf den Clientspracheneinstellungen bereitgestellt werden. Ihre Datei muss dem Schema entsprechen, das unter gehostet wird [`https://developer.microsoft.com/en-us/json-schemas/teams/v1.8/MicrosoftTeams.Localization.schema.json`](https://developer.microsoft.com/en-us/json-schemas/teams/v1.8/MicrosoftTeams.Localization.schema.json).

> [!TIP]
> Geben Sie das Schema am Anfang des Manifests an, um die Unterstützung von Code-Editoren zu aktivieren oder eine ähnliche Unterstützung zu erhalten `IntelliSense` : `"$schema": "https://developer.microsoft.com/json-schemas/teams/v1.8/MicrosoftTeams.schema.json",`

## <a name="example"></a>Beispiel

Beispiel für das JSON-Lokalisierungsschema:

```json
{
  "$schema": "https://developer.microsoft.com/json-schemas/teams/v1.8/MicrosoftTeams.schema.json",
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
|`$schema`|URI|–|Die https://-URL, die auf das JSON-Schema für das Manifest verweist.|
|`name.short`|Zeichenfolge|30|Ersetzt die entsprechende Zeichenfolge aus dem App-Manifest durch den hier angegebenen Wert.|
|`name.full`|Zeichenfolge|100|Ersetzt die entsprechende Zeichenfolge aus dem App-Manifest durch den hier angegebenen Wert.|
|`description.short`|Zeichenfolge|80|Ersetzt die entsprechende Zeichenfolge aus dem App-Manifest durch den hier angegebenen Wert.|
|`description.full`|Zeichenfolge|4000|Ersetzt die entsprechende Zeichenfolge aus dem App-Manifest durch den hier angegebenen Wert.|
|`staticTabs\\[([0-9]|1[0-5])\\]\\.name`|Zeichenfolge|128|Ersetzt die entsprechenden Zeichenfolgen aus dem App-Manifest durch den hier angegebenen Wert.|
|`bots\\[0\\]\\.commandLists\\[[0-2]\\]\\.commands\\[[0-9]\\]\\.title`|Zeichenfolge|32|Ersetzt die entsprechenden Zeichenfolgen aus dem App-Manifest durch den hier angegebenen Wert.|
|`bots\\[0\\]\\.commandLists\\[[0-2]\\]\\.commands\\[[0-9]\\]\\.description`|Zeichenfolge|128|Ersetzt die entsprechenden Zeichenfolgen aus dem App-Manifest durch den hier angegebenen Wert.|
|`composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.title`|Zeichenfolge|32|Ersetzt die entsprechenden Zeichenfolgen aus dem App-Manifest durch den hier angegebenen Wert.|
|`composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.description`|Zeichenfolge|128|Ersetzt die entsprechenden Zeichenfolgen aus dem App-Manifest durch den hier angegebenen Wert.|
|`composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.title`|Zeichenfolge|32|Ersetzt die entsprechende Zeichenfolge aus dem App-Manifest durch den hier angegebenen Wert.|
|`composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.description`|Zeichenfolge|128|Ersetzt die entsprechenden Zeichenfolgen aus dem App-Manifest durch den hier angegebenen Wert.|
|`composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.value`|Zeichenfolge|512|Ersetzt die entsprechende Zeichenfolge aus dem App-Manifest durch den hier angegebenen Wert.|
|`composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.choices\\[[0-9]\\]\\.title`|Zeichenfolge|128|Ersetzt die entsprechenden Zeichenfolgen aus dem App-Manifest durch den hier angegebenen Wert.|
|`composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.taskInfo\\.title`|Zeichenfolge|64|Ersetzt die entsprechenden Zeichenfolgen aus dem App-Manifest durch den hier angegebenen Wert.|
|`activities.activityTypes\\[\\b([0-9]|[1-8][0-9]|9[0-9]|1[01][0-9]|12[0-7])\\b]\\.description`|Zeichenfolge|128|Eine kurze Beschreibung der Benachrichtigung|
|`activities.activityTypes\\[\\b([0-9]|[1-8][0-9]|9[0-9]|1[01][0-9]|12[0-7])\\b]\\.templateText`|Zeichenfolge|128|Beispiel: "{actor} hat die Aufgabe {taskId} für Sie erstellt."|

## <a name="see-also"></a>Siehe auch

[Lokalisieren IhrerApp](~/concepts/build-and-test/apps-localization.md)
