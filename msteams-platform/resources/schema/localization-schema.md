---
title: JSON-Schemareferenz für Lokalisierungsdatei
description: Beschreibt das von der Lokalisierungsdatei für Microsoft Teams unterstützte Lokalisierungs Schema.
keywords: Schema Lokalisierung für Teams-Manifestdatei
ms.date: 05/20/2019
ms.openlocfilehash: 061729ecb5110c99d8f85f144796f1a78b266c3d
ms.sourcegitcommit: bac0226d9048c363d96bbaf6f5395388c5f5c45a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/06/2020
ms.locfileid: "45039279"
---
# <a name="reference-localization-file-json-schema"></a>Referenz: JSON-Schema der Lokalisierungsdatei

In der Microsoft Teams-Lokalisierungsdatei werden Sprachübersetzungen beschrieben, die basierend auf den Clientspracheinstellungen bedient werden. Die Datei muss dem Schema entsprechen, das unter gehostet wird [`https://developer.microsoft.com/en-us/json-schemas/teams/v1.7/MicrosoftTeams.Localization.schema.json`](https://developer.microsoft.com/en-us/json-schemas/teams/v1.7/MicrosoftTeams.Localization.schema.json) . Weitere Informationen finden Sie unter [App-Lokalisierung](~/concepts/build-and-test/apps-localization.md).

## <a name="sample"></a>Beispiel

```json
{
  "$schema": "https://developer.microsoft.com/json-schemas/teams/v1.7/MicrosoftTeams.schema.json",
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
> Geben Sie das Schema am Anfang des Manifests an, um IntelliSense oder ähnliche Unterstützung aus Ihrem Code-Editor zu aktivieren:`"$schema": "https://developer.microsoft.com/json-schemas/teams/v1.7/MicrosoftTeams.schema.json",`

## <a name="nameshort"></a>Name. Short

**Zeichenfolge, maximale Länge 30**

Ersetzt die entsprechende Zeichenfolge aus dem App-Manifest durch den hier angegebenen Wert.

## <a name="namefull"></a>Name. Full

**Zeichenfolge, maximale Länge 100**

Ersetzt die entsprechende Zeichenfolge aus dem App-Manifest durch den hier angegebenen Wert.

## <a name="descriptionshort"></a>Description. Short

**Zeichenfolge, maximale Länge 80**

Ersetzt die entsprechende Zeichenfolge aus dem App-Manifest durch den hier angegebenen Wert.

## <a name="descriptionfull"></a>Description. Full

**Zeichenfolge, maximale Länge 4000**

Ersetzt die entsprechende Zeichenfolge aus dem App-Manifest durch den hier angegebenen Wert.

## <a name="statictabs0-910-5name"></a>staticTabs \\ [([0-9] | 1 [0-5]) \\ ] \\ . Name

**Zeichenfolge, maximale Länge 128**

Ersetzt die entsprechenden Zeichenfolgen (en) aus dem App-Manifest durch den hier angegebenen Wert.

## <a name="bots0commandlists0-2commands0-9title"></a>Bots \\ [0 \\ ] \\ . commandLists \\ [[0-2] \\ ] \\ . Commands \\ [[0-9] \\ ] \\ . Title

**Zeichenfolge, maximale Länge 32**

Ersetzt die entsprechenden Zeichenfolgen (en) aus dem App-Manifest durch den hier angegebenen Wert.

## <a name="bots0commandlists0-2commands0-9description"></a>Bots \\ [0 \\ ] \\ . commandLists \\ [[0-2] \\ ] \\ . Commands \\ [[0-9] \\ ] \\ . Description

**Zeichenfolge, maximale Länge 128**

Ersetzt die entsprechenden Zeichenfolgen (en) aus dem App-Manifest durch den hier angegebenen Wert.

## <a name="composeextensions0commands0-9title"></a>composeExtensions \\ [0 \\ ] \\ . Commands \\ [[0-9] \\ ] \\ . Title

**Zeichenfolge, maximale Länge 32**

Ersetzt die entsprechenden Zeichenfolgen (en) aus dem App-Manifest durch den hier angegebenen Wert.

## <a name="composeextensions0commands0-9description"></a>composeExtensions \\ [0 \\ ] \\ . Commands \\ [[0-9] \\ ] \\ . Description

**Zeichenfolge, maximale Länge 128**

Ersetzt die entsprechenden Zeichenfolgen (en) aus dem App-Manifest durch den hier angegebenen Wert.

## <a name="composeextensions0commands0-9parameters0-4title"></a>composeExtensions \\ [0 \\ ] \\ . Commands \\ [[0-9] \\ ] \\ . Parameters \\ [[0-4] \\ ] \\ . Title

**Zeichenfolge, maximale Länge 32**

Ersetzt die entsprechenden Zeichenfolgen (en) aus dem App-Manifest durch den hier angegebenen Wert.

## <a name="composeextensions0commands0-9parameters0-4description"></a>composeExtensions \\ [0 \\ ] \\ . Commands \\ [[0-9] \\ ] \\ . Parameters \\ [[0-4] \\ ] \\ . Description

**Zeichenfolge, maximale Länge 128**

Ersetzt die entsprechenden Zeichenfolgen (en) aus dem App-Manifest durch den hier angegebenen Wert.

## <a name="composeextensions0commands0-9parameters0-4value"></a>composeExtensions \\ [0 \\ ] \\ . Commands \\ [[0-9] \\ ] \\ . Parameters \\ [[0-4] \\ ] \\ . Value

**Zeichenfolge, maximale Länge 512**

Ersetzt die entsprechenden Zeichenfolgen (en) aus dem App-Manifest durch den hier angegebenen Wert.

## <a name="composeextensions0commands0-9parameters0-4choices0-9title"></a>composeExtensions \\ [0 \\ ] \\ . Commands \\ [[0-9] \\ ] \\ . Parameters \\ [[0-4] \\ ] \\ . Choices \\ [[0-9] \\ ] \\ . Title

**Zeichenfolge, maximale Länge 128**

Ersetzt die entsprechenden Zeichenfolgen (en) aus dem App-Manifest durch den hier angegebenen Wert.

## <a name="composeextensions0commands0-9taskinfotitle"></a>composeExtensions \\ [0 \\ ] \\ . Commands \\ [[0-9] \\ ] \\ . taskInfo \\ . Title

**Zeichenfolge, maximale Länge 64**

Ersetzt die entsprechenden Zeichenfolgen (en) aus dem App-Manifest durch den hier angegebenen Wert.
