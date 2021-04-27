---
title: JSON-Schemareferenz für Lokalisierungsdatei
description: Beschreibt das lokalisierungsschema, das von der Lokalisierungsdatei für Microsoft Teams unterstützt wird.
ms.topic: reference
localization_priority: Normal
keywords: Manifestschemalokalisierung von Teams
ms.date: 05/20/2019
ms.openlocfilehash: 3e4207fb3e862eac18c80ffc49e7c5648ae05c28
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2021
ms.locfileid: "52019706"
---
# <a name="reference-localization-file-json-schema"></a>Referenz: JSON-Schema der Lokalisierungsdatei

In der Microsoft Teams-Lokalisierungsdatei werden Sprachübersetzungen beschrieben, die basierend auf den Clientspracheneinstellungen bedient werden. Ihre Datei muss dem schema entsprechen, das unter gehostet [`https://developer.microsoft.com/en-us/json-schemas/teams/v1.8/MicrosoftTeams.Localization.schema.json`](https://developer.microsoft.com/en-us/json-schemas/teams/v1.8/MicrosoftTeams.Localization.schema.json) wird. Weitere Informationen finden Sie unter [App-Lokalisierung](~/concepts/build-and-test/apps-localization.md).

## <a name="sample"></a>Beispiel

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

## <a name="schema"></a>$schema

**uri**

Die https://-URL, die auf das JSON-Schema für das Manifest verweist.

> [!TIP]
> Geben Sie das Schema am Anfang des Manifests an, um IntelliSense oder ähnliche Unterstützung von Ihrem Code-Editor zu aktivieren: `"$schema": "https://developer.microsoft.com/json-schemas/teams/v1.8/MicrosoftTeams.schema.json",`

## <a name="nameshort"></a>name.short

**Zeichenfolge, Max. Länge 30**

Ersetzt die entsprechende Zeichenfolge aus dem App-Manifest durch den hier angegebenen Wert.

## <a name="namefull"></a>name.full

**Zeichenfolge, Max. Länge 100**

Ersetzt die entsprechende Zeichenfolge aus dem App-Manifest durch den hier angegebenen Wert.

## <a name="descriptionshort"></a>description.short

**Zeichenfolge, Max. Länge 80**

Ersetzt die entsprechende Zeichenfolge aus dem App-Manifest durch den hier angegebenen Wert.

## <a name="descriptionfull"></a>description.full

**Zeichenfolge, Max. Länge 4000**

Ersetzt die entsprechende Zeichenfolge aus dem App-Manifest durch den hier angegebenen Wert.

## <a name="statictabs0-910-5name"></a>staticTabs \\ [([0-9]|1[0-5]) \\ ] \\ .name

**Zeichenfolge, Max. Länge 128**

Ersetzt die entsprechenden Zeichenfolgen aus dem App-Manifest durch den hier angegebenen Wert.

## <a name="bots0commandlists0-2commands0-9title"></a>bots \\ [0 \\ ] \\ .commandLists \\ [[0-2] \\ ] \\ .commands \\ [[0-9] \\ ] \\ .title

**Zeichenfolge, Max. Länge 32**

Ersetzt die entsprechenden Zeichenfolgen aus dem App-Manifest durch den hier angegebenen Wert.

## <a name="bots0commandlists0-2commands0-9description"></a>bots \\ [0 \\ ] \\ .commandLists \\ [[0-2] \\ ] \\ .commands \\ [[0-9] \\ ] \\ .description

**Zeichenfolge, Max. Länge 128**

Ersetzt die entsprechenden Zeichenfolgen aus dem App-Manifest durch den hier angegebenen Wert.

## <a name="composeextensions0commands0-9title"></a>composeExtensions \\ [0 \\ ] \\ .commands \\ [[0-9] \\ ] \\ .title

**Zeichenfolge, Max. Länge 32**

Ersetzt die entsprechenden Zeichenfolgen aus dem App-Manifest durch den hier angegebenen Wert.

## <a name="composeextensions0commands0-9description"></a>composeExtensions \\ [0 \\ ] \\ .commands \\ [[0-9] \\ ] \\ .description

**Zeichenfolge, Max. Länge 128**

Ersetzt die entsprechenden Zeichenfolgen aus dem App-Manifest durch den hier angegebenen Wert.

## <a name="composeextensions0commands0-9parameters0-4title"></a>composeExtensions \\ [0 \\ ] \\ .commands \\ [[0-9] \\ ] \\ .parameters \\ [[0-4] \\ ] \\ .title

**Zeichenfolge, Max. Länge 32**

Ersetzt die entsprechenden Zeichenfolgen aus dem App-Manifest durch den hier angegebenen Wert.

## <a name="composeextensions0commands0-9parameters0-4description"></a>composeExtensions \\ [0 \\ ] \\ .commands \\ [[0-9] \\ ] \\ .parameters \\ [[0-4] \\ ] \\ .description

**Zeichenfolge, Max. Länge 128**

Ersetzt die entsprechenden Zeichenfolgen aus dem App-Manifest durch den hier angegebenen Wert.

## <a name="composeextensions0commands0-9parameters0-4value"></a>composeExtensions \\ [0 \\ ] \\ .commands \\ [[0-9] \\ ] \\ .parameters \\ [[0-4] \\ ] \\ .value

**Zeichenfolge, Max. Länge 512**

Ersetzt die entsprechenden Zeichenfolgen aus dem App-Manifest durch den hier angegebenen Wert.

## <a name="composeextensions0commands0-9parameters0-4choices0-9title"></a>composeExtensions \\ [0 \\ ] \\ .commands \\ [[0-9] \\ ] \\ .parameters \\ [[0-4] \\ ] \\ .choices \\ [[0-9] \\ ] \\ .title

**Zeichenfolge, Max. Länge 128**

Ersetzt die entsprechenden Zeichenfolgen aus dem App-Manifest durch den hier angegebenen Wert.

## <a name="composeextensions0commands0-9taskinfotitle"></a>composeExtensions \\ [0 \\ ] \\ .commands \\ [[0-9] \\ ] \\ .taskInfo \\ .title

**Zeichenfolge, Max. Länge 64**

Ersetzt die entsprechenden Zeichenfolgen aus dem App-Manifest durch den hier angegebenen Wert.
