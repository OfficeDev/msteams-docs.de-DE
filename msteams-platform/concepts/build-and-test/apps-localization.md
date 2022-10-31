---
title: Lokalisieren IhrerApp
description: Hier erfahren Sie, wie Sie Ihre Microsoft Teams-App lokalisieren und Zeichenfolgen in Ihrem App-Manifest lokalisieren.
ms.topic: conceptual
ms.localizationpriority: medium
ms.date: 05/15/2018
ms.openlocfilehash: bd8b579178598b1d485e908f80e9590b27652101
ms.sourcegitcommit: 10debe0f01574a21aab54bfac692a4c8373263a8
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/31/2022
ms.locfileid: "68789870"
---
# <a name="localize-your-app"></a>Lokalisieren IhrerApp

Berücksichtigen Sie die folgenden Faktoren, um Ihre Microsoft Teams-App zu lokalisieren:

1. [Lokalisieren Sie Ihren AppSource-Eintrag](#localize-your-appsource-listing).
1. [Lokalisieren Sie Zeichenfolgen in Ihrem App-Manifest](#localize-strings-in-your-app-manifest).
1. [Behandeln Sie lokalisierte Textübermittlungen von Ihren Benutzern](#handle-localized-text-submissions-from-your-users).

## <a name="localize-your-appsource-listing"></a>Lokalisieren Ihres AppSource-Eintrags

Wenn Sie die App im Store veröffentlichen, geben Sie Metadaten (Beschreibungen, Screenshots, Name) in den Sprachen an, in denen Ihre App aufgeführt werden soll, und geben Sie diese Sprachen explizit auf der **Seite Marketplace-Einträge** im Partner Center an. Weitere Informationen finden Sie unter [Lokalisierte Microsoft AppSource-Fronts](/office/dev/store/prepare-localized-solutions#localized-microsoft-appsource-fronts). Um lokalisierte Einträge im App Store zu unterstützen, können Sie Ihrem Eintrag zusätzliche Sprachen hinzufügen. Die Standardsprachinformationen, die Sie im [Partner Center](/office/dev/store/submit-to-appsource-via-partner-center) für Ihren Eintrag angeben, werden im [AppSource-Websiteeintrag](https://appsource.microsoft.com/marketplace/apps?product=office%3Bteams&page=1 "AppSource ist ein Ort für alle Anforderungen Ihres Teams. Bringen Sie alles zusammen, einschließlich Chats, Besprechungen, Anrufe, Dateien und Tools, um eine produktivere Teamarbeit zu ermöglichen.") für Ihre App angezeigt. Derzeit ist Englisch die Standardsprache.

### <a name="configure-localization"></a>Konfigurieren der Lokalisierung

Um eine zusätzliche Sprache für Ihre App zu konfigurieren, wählen Sie im [Partner Center](/office/dev/store/submit-to-appsource-via-partner-center) sowohl Englisch als auch die zusätzliche Sprache der App aus. Französisch wird im folgenden Beispiel als zusätzliche Sprache verwendet:

1. Hinzufügen der Englischen Sprache
    * Geben Sie den App-Namen ein.
    * Geben Sie eine kurze Beschreibung der App in englischer Sprache ein.
    * Geben Sie die lange Beschreibung der App auf Englisch ein.
    * Geben Sie in der langen Beschreibung Folgendes ein: **Diese App ist in Französisch verfügbar**.
    * Laden Sie die Bilder der App-Benutzeroberfläche hoch (auf Englisch).
2. Hinzufügen von Französisch
    * Geben Sie den App-Namen ein.
    * Geben Sie eine kurze Beschreibung der App auf Französisch ein.
    * Geben Sie die lange Beschreibung der App auf Französisch ein.
    * Laden Sie die Bilder ihrer App-Benutzeroberfläche hoch (auf Französisch).

Die Bilder, die Sie in englischer Sprache hochladen, werden in AppSource verwendet.

## <a name="localize-strings-in-your-app-manifest"></a>Lokalisieren von Zeichenfolgen in Ihrem App-Manifest

Verwenden Sie das Microsoft Teams-App-Schema `v1.5` und höher, um Ihre App zu lokalisieren. Hierzu können Sie das `$schema` Attribut in Ihrer datei manifest.json auf `https://developer.microsoft.com/json-schemas/teams/v1.5/MicrosoftTeams.schema.json` oder höher festlegen und die `manifestVersion` Eigenschaft auf `$schema` version (`1.5` in diesem Fall) aktualisieren.

Fügen Sie die `localizationInfo` -Eigenschaft mit der Standardsprache hinzu, die ihre Anwendung unterstützt. Die Standardsprache wird als endgültige Fallbacksprache verwendet, wenn die Clienteinstellungen des Benutzers mit keiner Ihrer zusätzlichen Sprachen übereinstimmen.

> [!NOTE]
> Die Manifestversion muss für manifest.json- und localization.json-Dateien identisch sein.

### <a name="example-manifestjson-change"></a>Beispiel für eine Manifest.json-Änderung

Im Folgenden `manifest.json` können Sie die -Eigenschaft mit der `localizationInfo` Standardsprache hinzufügen, die Ihre Anwendung zusammen mit `additionalLanguages`unterstützt:

```json
{
  "$schema": "https://developer.microsoft.com/json-schemas/teams/v1.5/MicrosoftTeams.schema.json",
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

### <a name="example-localization-json-change"></a>Änderung der JSON-Beispiellokalisierung

Es folgt ein Beispiel für die Lokalisierung von JSON:

```json
{
  "$schema": "https://developer.microsoft.com/json-schemas/teams/v1.5/MicrosoftTeams.Localization.schema.json",
  "manifestVersion": "1.5",
  "name.short": "Localización",
  "name.full": "Aplicación de localización",
  ...
}
```

Sie können zusätzliche JSON-Dateien mit Übersetzungen aller benutzerseitigen Zeichenfolgen in Ihrem Manifest bereitstellen. Diese Dateien müssen dem [JSON-Schema der Lokalisierungsdatei](../../resources/schema/localization-schema.md) entsprechen und der `localizationInfo` -Eigenschaft Ihres Manifests hinzugefügt werden. Jede Datei korreliert mit einem Sprachtag, das der Teams-Client verwendet, um die entsprechenden Zeichenfolgen auszuwählen. Das Sprachtag hat die Form von, `<language>-<region>` aber Sie können den `<region>` Teil weglassen, um alle Regionen als Ziel zu verwenden, die die gewünschte Sprache unterstützen.

Der Teams-Client wendet die Zeichenfolgen in der folgenden Reihenfolge an: Standardsprachzeichenfolgen -> nur Zeichenfolgen für die Sprache des Benutzers -> Sprache des Benutzers + Regionszeichenfolgen des Benutzers.

Beispielsweise stellen Sie die Standardsprache "fr" (Französisch, alle Regionen) und zusätzliche Sprachdateien für "en" (Englisch, alle Regionen) und "en-gb" (Englisch, Großbritannien) bereit. Die Sprache des Benutzers ist auf "en-gb" festgelegt. Die folgenden Änderungen erfolgen basierend auf der Sprachauswahl:

1. Der Teams-Client akzeptiert die "fr"-Zeichenfolgen und überschreibt sie mit den Zeichenfolgen "en".
1. Überschreiben Sie die Zeichenfolgen "en" mit den Zeichenfolgen "en-gb".

Wenn die Sprache des Benutzers auf "en-ca" festgelegt ist, werden die folgenden Änderungen basierend auf der Sprachauswahl vorgenommen:

1. Der Teams-Client akzeptiert die "fr"-Zeichenfolgen und überschreibt sie mit den Zeichenfolgen "en".
1. Da keine "en-ca"-Lokalisierung angegeben wird, werden die "en"-Lokalisierungen verwendet.

Wenn die Sprache des Benutzers auf "es-es" festgelegt ist, akzeptiert der Teams-Client die Zeichenfolgen "fr". Der Teams-Client überschreibt die Zeichenfolgen nicht mit einer der Sprachdateien, da keine Übersetzung von "es" oder "es-es" bereitgestellt wird.

Daher müssen Sie nur Sprachübersetzungen auf oberster Ebene in Ihrem Manifest bereitstellen. Beispiel: `en` anstelle von `en-us`. Sie müssen Außerkraftsetzungen auf Regionsebene nur für die wenigen Zeichenfolgen bereitstellen, die sie benötigen.

### <a name="example-manifestjson-change"></a>Beispiel für eine Manifest.json-Änderung

Die `manifest.json` Änderung wird im folgenden Beispiel gezeigt:

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

### <a name="example-localization-json-file"></a>JSON-Beispieldatei für die Lokalisierung

 Die `localization.json` Änderung wird im folgenden Beispiel gezeigt:

```json
{
  "$schema": "https://developer.microsoft.com/json-schemas/teams/v1.8/MicrosoftTeams.Localization.schema.json",
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

## <a name="handle-localized-text-submissions-from-your-users"></a>Behandeln von lokalisierten Textübermittlungen von Benutzern

Wenn Sie lokalisierte Versionen Ihrer Anwendung bereitstellen, antworten die Benutzer mit der gleichen Sprache. Da Teams die Benutzerübermittlungen nicht zurück in die Standardsprache übersetzt, muss Ihre App die lokalisierten Sprachantworten verarbeiten. Wenn Sie beispielsweise einen lokalisierten `commandList`angeben, sind die Antworten an Ihren Bot der lokalisierte Text des Befehls und nicht die Standardsprache. Ihre App muss entsprechend reagieren.

## <a name="code-sample"></a>Codebeispiel

| Beispielname | Beschreibung | .NET | Node.js |
|-------------|-------------|------|------|
| App-Lokalisierung | Teams-App-Lokalisierung mithilfe von Bot und Registerkarte. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-localization/csharp) |[Anzeigen](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-localization/nodejs) |

## <a name="see-also"></a>Siehe auch

* [Json-Schemareferenz lokalisieren](~/resources/schema/localization-schema.md)
