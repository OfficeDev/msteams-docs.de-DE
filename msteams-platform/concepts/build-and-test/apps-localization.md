---
title: Lokalisieren IhrerApp
description: Erfahren Sie, wie Sie Ihre Microsoft Teams App lokalisieren und Zeichenfolgen in Ihrem App-Manifest lokalisieren.
ms.topic: conceptual
ms.localizationpriority: medium
ms.date: 05/15/2018
ms.openlocfilehash: 5c3d0612f0e7ce0e183d097469165cf2f9c337d0
ms.sourcegitcommit: 9d318eda5589ea8f5519d05cb83e0acf3e13e2f4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/17/2022
ms.locfileid: "66150666"
---
# <a name="localize-your-app"></a>Lokalisieren IhrerApp

Berücksichtigen Sie die folgenden Faktoren, um Ihre Microsoft Teams App zu lokalisieren:

1. [Lokalisieren Sie Ihren AppSource-Eintrag](#localize-your-appsource-listing).
1. [Lokalisieren Sie Zeichenfolgen in Ihrem App-Manifest](#localize-strings-in-your-app-manifest).
1. [Behandeln sie lokalisierte Textübermittlungen von Ihren Benutzern](#handle-localized-text-submissions-from-your-users).

## <a name="localize-your-appsource-listing"></a>Lokalisieren Des AppSource-Eintrags

Wenn Sie die App im Store veröffentlichen, stellen Sie Metadaten (Beschreibungen, Screenshots, Namen) in den Sprachen bereit, in denen Ihre App aufgeführt werden soll, und geben Sie diese Sprachen explizit auf der **Marketplace-Eintragsseite** im Partner Center an. Weitere Informationen finden Sie [unter lokalisierten Microsoft AppSource-Fronts](/office/dev/store/prepare-localized-solutions#localized-microsoft-appsource-fronts). Um lokalisierte Einträge im App Store zu unterstützen, können Sie Ihrem Eintrag weitere Sprachen hinzufügen. Die Standardsprachinformationen, die Sie im [Partner Center](/office/dev/store/submit-to-appsource-via-partner-center) für Ihren Eintrag angeben, werden im [AppSource-Websiteeintrag](https://appsource.microsoft.com/marketplace/apps?product=office%3Bteams&page=1 "AppSource ist ein Ort für alle Anforderungen Ihres Teams. Bringen Sie alles zusammen, einschließlich Chats, Besprechungen, Anrufen, Dateien und Tools, um produktivere Teamarbeit zu ermöglichen.") für Ihre App angezeigt. Derzeit ist Die Standardsprache Englisch.

### <a name="configure-localization"></a>Konfigurieren der Lokalisierung

Um eine zusätzliche Sprache für Ihre App zu konfigurieren, wählen Sie im [Partner Center](/office/dev/store/submit-to-appsource-via-partner-center) sowohl Englisch als auch die zusätzliche Sprache der App aus. Französisch wird im folgenden Beispiel als zusätzliche Sprache verwendet:

1. Hinzufügen von Englisch
    * Geben Sie den App-Namen ein.
    * Geben Sie eine kurze Beschreibung der App in Englisch ein.
    * Geben Sie die lange Beschreibung der App in Englisch ein.
    * Geben Sie in der langen Beschreibung Folgendes ein: **Diese App ist in Französisch verfügbar**.
    * Hochladen die Bilder der App-Benutzeroberfläche (in Englisch).
2. Französisch hinzufügen
    * Geben Sie den App-Namen ein.
    * Geben Sie eine kurze Beschreibung der App in Französisch ein.
    * Geben Sie die lange Beschreibung der App auf Französisch ein.
    * Hochladen die Bilder der App-Benutzeroberfläche (auf Französisch).

Die Bilder, die Sie mit der englischen Sprache hochladen, werden in AppSource verwendet.

## <a name="localize-strings-in-your-app-manifest"></a>Lokalisieren von Zeichenfolgen im App-Manifest

Verwenden Sie das Microsoft Teams App-Schema `v1.5` und höher, um Ihre App zu lokalisieren. Sie können dies tun, indem Sie das `$schema` Attribut in der Datei manifest.json auf `https://developer.microsoft.com/json-schemas/teams/v1.5/MicrosoftTeams.schema.json` oder höher festlegen und die Eigenschaft auf `$schema` version `manifestVersion` aktualisieren (`1.5`in diesem Fall).

Fügen Sie die `localizationInfo` Eigenschaft mit der Standardsprache hinzu, die ihre Anwendung unterstützt. Die Standardsprache wird als letzte Fallbacksprache verwendet, wenn die Clienteinstellungen des Benutzers nicht mit einer Ihrer zusätzlichen Sprachen übereinstimmen.

### <a name="example-manifestjson-change"></a>Beispiel für manifest.json-Änderung

Im Folgenden `manifest.json` wird die Eigenschaft mit der `localizationInfo` Standardsprache hinzugefügt, die ihre Anwendung unterstützt, zusammen mit `additionalLanguages`:

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

### <a name="example-localization-json-change"></a>Json-Änderung für die Beispiellokalisierung

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

Sie können zusätzliche JSON-Dateien mit Übersetzungen aller benutzerorientierten Zeichenfolgen in Ihrem Manifest bereitstellen. Diese Dateien müssen dem [JSON-Schema der Lokalisierungsdatei](../../resources/schema/localization-schema.md) entsprechen und der `localizationInfo` Eigenschaft Ihres Manifests hinzugefügt werden. Jede Datei korreliert mit einem Sprachtag, das der Teams Client verwendet, um die entsprechenden Zeichenfolgen auszuwählen. Das Sprachtag hat die Form, `<language>-<region>` aber Sie können den `<region>` Teil weglassen, um auf alle Regionen abzuzielen, die die gewünschte Sprache unterstützen.

Der Teams-Client wendet die Zeichenfolgen in der folgenden Reihenfolge an: Standardsprachenzeichenfolgen - > nur Zeichenfolgen für die Sprache des Benutzers - > Sprache des Benutzers und Regionszeichenfolgen des Benutzers.

Sie stellen beispielsweise die Standardsprache "fr" (Französisch, alle Regionen) und zusätzliche Sprachdateien für "en" (Englisch, alle Regionen) und "en-gb" (Englisch, Großbritannien) bereit. Die Sprache des Benutzers ist auf "en-gb" festgelegt. Die folgenden Änderungen erfolgen basierend auf der Sprachauswahl:

1. Der Teams-Client überschreibt die Zeichenfolgen "fr" und überschreibt sie mit den "en"-Zeichenfolgen.
1. Überschreiben Sie die "en"-Zeichenfolgen mit den "en-gb"-Zeichenfolgen.

Wenn die Sprache des Benutzers auf "en-ca" festgelegt ist, werden die folgenden Änderungen basierend auf der Sprachauswahl vorgenommen:

1. Der Teams-Client überschreibt die Zeichenfolgen "fr" und überschreibt sie mit den "en"-Zeichenfolgen.
1. Da keine "en-ca"-Lokalisierung bereitgestellt wird, werden die "en"-Lokalisierungen verwendet.

Wenn die Sprache des Benutzers auf "es-es" festgelegt ist, übernimmt der Teams Client die Zeichenfolgen "fr". Der Teams-Client überschreibt die Zeichenfolgen nicht mit einer der Sprachdateien, da keine "es"- oder "es-es"-Übersetzung bereitgestellt wird.

Daher müssen Sie in Ihrem Manifest Nur-Sprachübersetzungen auf oberster Ebene bereitstellen. Beispielsweise `en` anstelle von `en-us`. Außerkraftsetzungen auf Regionsebene müssen nur für die wenigen Zeichenfolgen bereitgestellt werden, die sie benötigen.

### <a name="example-manifestjson-change"></a>Beispiel für manifest.json-Änderung

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

### <a name="example-localization-json-file"></a>Beispiel für die Lokalisierung einer JSON-Datei

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

## <a name="handle-localized-text-submissions-from-your-users"></a>Behandeln lokalisierter Textübermittlungen von Benutzern

Wenn Sie lokalisierte Versionen Ihrer Anwendung bereitstellen, antworten die Benutzer mit derselben Sprache. Da Teams die Benutzerübermittlungen nicht wieder in die Standardsprache übersetzt, muss Ihre App die lokalisierten Sprachantworten verarbeiten. Wenn Sie z. B. einen lokalisierten `commandList`Text angeben, sind die Antworten auf Ihren Bot der lokalisierte Text des Befehls, nicht die Standardsprache. Ihre App muss entsprechend reagieren.

## <a name="code-sample"></a>Codebeispiel

| Beispielname | Beschreibung | .NET | Node.js |
|-------------|-------------|------|------|
| App-Lokalisierung | Teams App-Lokalisierung mithilfe von Bot und Registerkarte. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-localization/csharp) |[Anzeigen](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-localization/nodejs) |

## <a name="see-also"></a>Siehe auch

[Json-Schemareferenz lokalisieren](~/resources/schema/localization-schema.md)
