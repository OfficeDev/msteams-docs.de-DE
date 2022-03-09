---
title: Lokalisieren IhrerApp
description: Beschreibt Überlegungen zum Lokalisieren Ihrer Microsoft Teams-App.
ms.topic: conceptual
ms.localizationpriority: medium
keywords: Teams veröffentlichen die AppSource-Lokalisierungssprache für Store-Veröffentlichungen
ms.date: 05/15/2018
ms.openlocfilehash: ec734017a807f744a4b44d7d3594638a5ec72b32
ms.sourcegitcommit: 2fdca6fb0ade3f6b460eb9a4dfea0a8e2ab8d3b9
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/08/2022
ms.locfileid: "63355524"
---
# <a name="localize-your-app"></a>Lokalisieren IhrerApp

Berücksichtigen Sie die folgenden Faktoren, um Ihre Microsoft Teams App zu lokalisieren:

1. [Lokalisieren Sie Ihren AppSource-Eintrag](#localize-your-appsource-listing).
1. [Lokalisieren Sie Zeichenfolgen in Ihrem App-Manifest](#localize-strings-in-your-app-manifest). 
1. [Behandeln sie lokalisierte Textübermittlungen von Ihren Benutzern](#handle-localized-text-submissions-from-your-users).

## <a name="localize-your-appsource-listing"></a>Lokalisieren Ihres AppSource-Eintrags

Wenn Sie die App im Store veröffentlichen, geben Sie Metadaten (Beschreibungen, Screenshots, Name) in den Sprachen an, in denen Ihre App aufgeführt werden soll, und geben Sie diese Sprachen explizit auf der **Marketplace-Eintragsseite** im Partner Center an. Weitere Informationen finden Sie unter [lokalisierte Microsoft AppSource-Fronts](/office/dev/store/prepare-localized-solutions#localized-microsoft-appsource-fronts). Um lokalisierte Einträge im App Store zu unterstützen, können Sie Ihrem Eintrag zusätzliche Sprachen hinzufügen. Die Standardspracheninformationen, die Sie im [Partner Center](/office/dev/store/submit-to-appsource-via-partner-center) für Ihren Eintrag angeben, werden im [AppSource-Websiteeintrag](https://appsource.microsoft.com/marketplace/apps?product=office%3Bteams&page=1 "AppSource ist ein Ort für alle Anforderungen Ihres Teams. Bringen Sie alles zusammen, einschließlich Chats, Besprechungen, Anrufen, Dateien und Tools, um eine produktivere Teamarbeit zu ermöglichen.") für Ihre App angezeigt. Derzeit lautet die Standardsprache Englisch.

### <a name="configure-localization"></a>Konfigurieren der Lokalisierung

Um eine zusätzliche Sprache für Ihre App zu konfigurieren, wählen Sie im [Partner Center](/office/dev/store/submit-to-appsource-via-partner-center) sowohl Englisch als auch die zusätzliche Sprache der App aus. Französisch wird im folgenden Beispiel als zusätzliche Sprache verwendet:

1. Hinzufügen von Englisch
    * Geben Sie den App-Namen ein.
    * Geben Sie eine kurze Beschreibung der App in Englisch ein.
    * Geben Sie die lange Beschreibung der App in Englisch ein.
    * Geben Sie in der langen Beschreibung ein: **Diese App ist auf Französisch verfügbar**.
    * Hochladen die Bilder Der App-UI (in Englisch).
2. Hinzufügen der Sprache Französisch
    * Geben Sie den App-Namen ein.
    * Geben Sie eine kurze Beschreibung der App auf Französisch ein.
    * Geben Sie die lange Beschreibung der App auf Französisch ein.
    * Hochladen die Bilder Der App-UI (auf Französisch).

Die Bilder, die Sie mit der englischen Sprache hochladen, werden in AppSource verwendet.

## <a name="localize-strings-in-your-app-manifest"></a>Lokalisieren von Zeichenfolgen im App-Manifest

Sie müssen das Microsoft Teams-App-Schema `v1.5` und höher verwenden, um Ihre App zu lokalisieren. Sie können dies tun, indem Sie das `$schema` Attribut in der Datei "manifest.json" auf **https://developer.microsoft.com/en-us/json-schemas/teams/v1.5/MicrosoftTeams.schema.json** oder höher festlegen und die Eigenschaft auf `$schema` version `manifestVersion` (`1.5`in diesem Fall) aktualisieren. 

Sie müssen die `localizationInfo` Eigenschaft mit der von der Anwendung unterstützten Standardsprache hinzufügen. Die Standardsprache wird als endgültige Fallbacksprache verwendet, wenn die Clienteinstellungen des Benutzers mit keiner ihrer zusätzlichen Sprachen übereinstimmen.

### <a name="example-manifestjson-change"></a>Beispiel für eine Änderung von "manifest.json"

Die folgende Datei manifest.json hilft Beim Hinzufügen der `localizationInfo` Eigenschaft mit der Standardsprache, die Ihre Anwendung unterstützt, zusammen mit `additionalLanguages`:

```json
{
  "$schema": "https://developer.microsoft.com/en-us/json-schemas/teams/v1.5/MicrosoftTeams.schema.json",
  "manifestVersion": "1.5",
  "localizationInfo": {
        "defaultLanguageTag": "en",
        "additionalLanguages": [
            {
                "languageTag": "es-mx",
                "file": "es-mx.json"
            }
        ]
    }
  ...
}
```

### <a name="example-localization-json-change"></a>Beispiel für eine Json-Lokalisierungsänderung

Es folgt ein Beispiel für die Lokalisierung von JSON:

```json
{
  "$schema": "https://developer.microsoft.com/en-us/json-schemas/teams/v1.5/MicrosoftTeams.Localization.schema.json",
  "manifestVersion": "1.5",
  "name.short": "Localización",
  "name.full": "Aplicación de localización",
  ...
}
```


Sie können zusätzliche JSON-Dateien mit Übersetzungen aller benutzerorientierten Zeichenfolgen in Ihrem Manifest bereitstellen. Diese Dateien müssen dem [JSON-Schema der Lokalisierungsdatei](../../resources/schema/localization-schema.md) entsprechen und der Eigenschaft Ihres Manifests hinzugefügt `localizationInfo` werden. Jede Datei korreliert mit einem Sprachtag, das der Teams Client verwendet, um die entsprechenden Zeichenfolgen auszuwählen. Das Sprachtag hat die Form, `<language>-<region>` aber Sie können den `<region>` Teil weglassen, um auf alle Regionen abzuzielen, die die gewünschte Sprache unterstützen.

Der Teams Client wendet die Zeichenfolgen in der folgenden Reihenfolge an: Standardsprachenzeichenfolgen – > Sprache des Benutzers nur Zeichenfolgen – > Sprache des Benutzers + Regionszeichenfolgen des Benutzers.

Sie geben beispielsweise die Standardsprache "fr" (Französisch, alle Regionen) und zusätzliche Sprachdateien für "en" (Englisch, alle Regionen) und "en-gb" (Englisch, großes Großbritannien) an. Die Sprache des Benutzers ist auf "en-gb" festgelegt. Die folgenden Änderungen erfolgen basierend auf der Sprachauswahl:

1. Der Teams Client übernimmt die Zeichenfolgen "fr" und überschreibt sie mit den Zeichenfolgen "en".
1. Überschreiben Sie die Zeichenfolgen "en" mit den Zeichenfolgen "en-gb".

Wenn die Sprache des Benutzers auf "en-ca" festgelegt ist, werden die folgenden Änderungen basierend auf der Sprachauswahl vorgenommen: 

1. Der Teams Client übernimmt die Zeichenfolgen "fr" und überschreibt sie mit den Zeichenfolgen "en".
1. Da keine Lokalisierung "en-ca" angegeben wird, werden die "en"-Lokalisierungen verwendet.

Wenn die Sprache des Benutzers auf "es-es" festgelegt ist, verwendet der Teams Client die Zeichenfolge "fr". Der Teams Client überschreibt die Zeichenfolgen nicht mit einer der Sprachdateien, da keine Übersetzung von "es" oder "es-es" bereitgestellt wird.

Daher müssen Sie nur Übersetzungen auf oberster Ebene in Ihrem Manifest bereitstellen. Beispiel: "en" anstelle von "en-us". Sie müssen Außerkraftsetzungen auf Regionsebene nur für die wenigen Zeichenfolgen bereitstellen, die sie benötigen. 

### <a name="example-manifestjson-change"></a>Beispiel für eine Änderung von "manifest.json"

Die manifest.json-Änderung wird im folgenden Beispiel gezeigt:

```json
{
  ...
  "localizationInfo": {
    "defaultLanguageTag": "en",
    "additionalLanguages": [
      {
        "languageTag": "en-gb",
        "file": "en-gb.json"
      },
      {
        "languageTag": "fr",
        "file": "fr.json"
      },
      {
        "languageTag": "pl",
        "file": "pl.json"
      }
    ]
  }
  ...
}
```

### <a name="example-localization-json-file"></a>Beispiel für die Lokalisierung der JSON-Datei

 Die Änderung "localization.json" wird im folgenden Beispiel gezeigt:

```json
{
  "$schema": "https://developer.microsoft.com/en-us/json-schemas/teams/v1.8/MicrosoftTeams.Localization.schema.json",
  "name.short": "Le App",
  "name.full": "App pour Microsoft Teams",
  "description.short": "Créez d'excellentes applications pour Microsoft Teams avec App.",
  "description.full": "Créez de nouvelles applications Microsoft Teams, concevez et prévisualisez des cartes bot, et explorez la documentation avec App.",
  "staticTabs[0].name": "Editeur de manifest",
  "staticTabs[1].name": "Editeur de cartes",
  "staticTabs[2].name": "Bibliothèque de contrôles",
  "bots[0].commandLists[0].commands[0].title": "chercher",
  "bots[0].commandLists[0].commands[0].description": "Rechercher la documentation Teams pertinente"
}
```

## <a name="handle-localized-text-submissions-from-your-users"></a>Behandeln lokalisierter Textübermittlungen von Benutzern

Wenn Sie lokalisierte Versionen Ihrer Anwendung bereitstellen, antworten die Benutzer mit derselben Sprache. Da Teams die Benutzerübermittlungen nicht zurück in die Standardsprache übersetzt, muss Ihre App die lokalisierten Sprachantworten verarbeiten. Wenn Sie beispielsweise einen lokalisierten `commandList`Befehl bereitstellen, sind die Antworten auf Ihren Bot der lokalisierte Text des Befehls und nicht die Standardsprache. Ihre App muss entsprechend reagieren.

## <a name="code-sample"></a>Codebeispiel

| Beispielname | Beschreibung | .NET | Node.js |
|-------------|-------------|------|------|
| App-Lokalisierung | Microsoft Teams App-Lokalisierung mit bot und tab. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-localization/csharp) |[Anzeigen](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-localization/nodejs) |

## <a name="see-also"></a>Siehe auch

[Json-Schemareferenz lokalisieren](~/resources/schema/localization-schema.md)
