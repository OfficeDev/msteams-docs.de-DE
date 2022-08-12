---
title: Json-Schemareferenz lokalisieren
description: Beschreibt das Lokalisierungsschema, das von der Lokalisierungsdatei für Microsoft Teams unter Verwendung eines Beispielschemas unterstützt wird.
ms.topic: reference
ms.localizationpriority: medium
ms.date: 05/20/2019
ms.openlocfilehash: f4ffd9a4b722ccc414f70b19e3020ab39d1ce779
ms.sourcegitcommit: 69a45722c5c09477bbff3ba1520e6c81d2d2d997
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/11/2022
ms.locfileid: "67311946"
---
# <a name="localize-json-schema-reference"></a>Json-Schemareferenz lokalisieren

Die Microsoft Teams-Lokalisierungsdatei beschreibt Sprachübersetzungen, die basierend auf den Clientspracheneinstellungen bereitgestellt werden. Ihre Datei muss dem Schema entsprechen, das unter gehostet wird [`https://developer.microsoft.com/en-us/json-schemas/teams/v1.8/MicrosoftTeams.Localization.schema.json`](https://developer.microsoft.com/en-us/json-schemas/teams/v1.8/MicrosoftTeams.Localization.schema.json).

> [!TIP]
> Geben Sie das Schema am Anfang des Manifests an, um die Unterstützung von Code-Editoren zu aktivieren oder eine ähnliche Unterstützung zu erhalten `IntelliSense` : `"$schema": "https://developer.microsoft.com/json-schemas/teams/v1.8/MicrosoftTeams.schema.json",`

## <a name="example"></a>Beispiel

Beispiel für das JSON-Lokalisierungsschema:

```json
{
    "$schema": "https://developer.microsoft.com/en-us/json-schemas/teams/v1.9/MicrosoftTeams.Localization.schema.json",
    "name.short": "Portail de Développement",
    "name.full": "Portail des développeurs",
    "description.short": "Configurer, distribuer et gérer vos applications Microsoft Teams",
    "description.full": "Anciennement App Studio, le portail des développeurs peut vous aider où que vous soyez dans votre parcours de développement d’applications Microsoft Teams.1. Configurez une nouvelle application ou importez une application existante.2. Configurez les fonctionnalités de votre application et d’autres métadonnées importantes.3. Obtenez des ressources pour vous aider à créer une application de haute qualité.3. Testez votre application directement dans Teams.4. Distribuez votre application dans votre organisation ou dans le Store Teams.5. Analysez l’utilisation, l’engagement et d’autres informations sur votre application. Le portail inclut également des outils pour concevoir des scènes virtuelles personnalisées, des cartes adaptatives et l’intégration à la Plateforme d’identités Microsoft.",
    "staticTabs[0].name": "Accueil",
    "staticTabs[1].name": "Applications",
    "staticTabs[2].name": "Outils",
    "staticTabs[3].name": "Developer Portal",
    "bots[0].commandLists[0].commands[0].title": "Rechercher",
    "bots[0].commandLists[0].commands[0].description": "Rechercher la documentation Teams appropriée"
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
