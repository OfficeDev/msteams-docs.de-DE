---
title: Lokalisierung für Ihre App
description: Beschreibt Überlegungen zum Lokalisieren Ihrer Microsoft Teams-App.
ms.topic: conceptual
localization_priority: Normal
keywords: Teams veröffentlichen Store Office Publishing AppSource-Lokalisierungssprache
ms.date: 05/15/2018
ms.openlocfilehash: 8490230ad0b268d402a9ad7deb5f8b1e3f420f9d
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2021
ms.locfileid: "52020849"
---
# <a name="localization-for-microsoft-teams-apps"></a>Lokalisierung für Microsoft Teams-Apps

Beim Lokalisieren Ihrer Microsoft Teams-App müssen Sie drei wichtige Bereiche berücksichtigen.

1. Ihr AppSource-Eintrag (wenn Sie im App Store veröffentlichen).
1. Die Zeichenfolgen, die dem Endbenutzer im App-Manifest angezeigt werden (z. B. Botbefehle).
1. Reagieren auf lokalisierten Text, der von Ihren Benutzern übermittelt wurde.

## <a name="localizing-your-appsource-listing"></a>Lokalisieren Ihres AppSource-Eintrags

Wenn Sie im App Store veröffentlichen, müssen Sie beachten, dass das Lokalisieren Ihres AppSource-Eintrags noch nicht unterstützt wird. In Vorbereitung auf die Unterstützung lokalisierter Einträge im App Store können Sie ihrem Eintrag jedoch weitere Sprachen hinzufügen. Derzeit werden nur die standardmäßigen (englischen) Sprachinformationen, die Sie im [Partner Center](/office/dev/store/submit-to-appsource-via-partner-center) für Ihren Eintrag bereitstellen, im [AppSource-Websiteeintrag](https://appsource.microsoft.com/marketplace/apps?product=office%3Bteams&page=1) für Ihre App angezeigt.

Um eine zusätzliche Sprache für Ihre App zu konfigurieren, wählen Sie im [Partner Center](/office/dev/store/submit-to-appsource-via-partner-center)sowohl Englisch als auch die zusätzliche Sprache der App aus. In diesem Beispiel wird Französisch verwendet.

1. Hinzufügen von Englisch
    * Geben Sie den Namen der App ein.
    * Geben Sie eine kurze Beschreibung der App in Englisch ein.
    * Füllen Sie die lange Beschreibung der App in Englisch aus.
    * Fügen Sie in der langen Beschreibung auch die Zeile "Diese App ist in "Französisch" verfügbar.
    * Laden Sie die Bilder ihrer App-UI hoch (in Englisch).
2. Hinzufügen von Französisch
    * Geben Sie den Namen der App ein.
    * Geben Sie eine kurze Beschreibung der App auf Französisch ein.
    * Füllen Sie die lange Beschreibung der App auf Französisch aus.
    * Laden Sie die Bilder ihrer App-UI hoch (auf Französisch).

Die Bilder, die Sie mit der englischen Sprache hochladen, werden in AppSource verwendet.

## <a name="localizing-the-strings-in-your-app-manifest"></a>Lokalisieren der Zeichenfolgen im App-Manifest

Sie müssen das Microsoft Teams-App-Schema v1.5+ verwenden, um Ihre App ordnungsgemäß zu lokalisieren. Dazu können Sie das Attribut in Ihrer manifest.json-Datei auf ' ' festlegen und die Eigenschaft `$schema` https://developer.microsoft.com/en-us/json-schemas/teams/v1.8/MicrosoftTeams.Localization.schema.json "manifestVersion" auf "1.7" aktualisieren.

### <a name="example-manifestjson-change"></a>Beispiel manifest.jsbei Änderung

```json
{
  "$schema": "https://developer.microsoft.com/en-us/json-schemas/teams/v1.8/MicrosoftTeams.Localization.schema.json",
  "manifestVersion": "1.5",
  ...
}
```

Anschließend möchten Sie die Eigenschaft "localizationInfo" mit der Standardsprache hinzufügen, die ihre Anwendung unterstützt. Die Standardsprache wird als endgültige Fallbacksprache verwendet, wenn die Clienteinstellungen des Benutzers keinem Ihrer zusätzlichen Sprachen entsprechen.

### <a name="example-manifestjson-change"></a>Beispiel manifest.jsbei Änderung

```json
{
  ...
  "localizationInfo": {
    "defaultLanguageTag": "en"
  }
  ...
}
```

Sie können zusätzliche .json-Dateien mit Übersetzungen aller zeichenfolgen angezeigten Benutzer in Ihrem Manifest bereitstellen. Diese Dateien müssen dem [JSON-Schema](../../resources/schema/localization-schema.md) der Lokalisierungsdatei entsprechen und der Eigenschaft "localizationInfo" Ihres Manifests hinzugefügt werden. Jede Datei korreliert mit einem Sprachtag, das der Teams-Client zum Auswählen der entsprechenden Zeichenfolgen verwendet. Das Sprachtag hat die Form, es wird jedoch empfohlen, den Teil weglassen, um alle Regionen zu verwenden, die <language> - <region> die gewünschte <region> Sprache unterstützen.

Der Teams-Client verwendet die Zeichenfolgen in dieser Reihenfolge: Standardsprachenzeichenfolgen -> Sprache des Benutzers nur Zeichenfolgen -> Sprache des Benutzers + Regionenzeichenfolgen des Benutzers.

Sie stellen z. B. die Standardsprache "fr" (Französisch, alle Regionen) und zusätzliche Sprachdateien für "en" (Englisch, alle Regionen) und "en-gb" (Englisch, Großbritannien) zur Verfügung. Wenn die Sprache des Benutzers auf "en-gb" festgelegt ist:

1. Der Teams-Client überschreibt die Zeichenfolgen "fr" mit den Zeichenfolgen "en".
2. Überschreiben Sie diese mit den Zeichenfolgen "en-gb".

Wenn die Sprache des Benutzers auf "en-ca" festgelegt ist: 

1. Der Teams-Client überschreibt die Zeichenfolgen "fr" mit den Zeichenfolgen "en".
2. Da keine "en-ca"-Lokalisierung bereitgestellt wird, werden die "en"-Lokalisierungen verwendet.

Wenn die Sprache des Benutzers auf "es-es" festgelegt ist, überschreibt der Teams-Client die "fr"-Zeichenfolgen und überschreibt sie nicht mit einer der Sprachdateien.

Daher wird dringend empfohlen, nur Übersetzungen auf oberster Ebene in Ihrem Manifest ('en' statt 'en-us') zur Verfügung zu stellen und nur Überschreibungen auf Regionsebene für die wenigen Zeichenfolgen zur Verfügung zu stellen, die sie benötigen.

### <a name="example-manifestjson-change"></a>Beispiel manifest.jsbei Änderung

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

### <a name="example-localization-json-file"></a>Beispiel für lokalisierungs-Json-Datei

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

## <a name="handling-localized-text-submissions-from-your-users"></a>Behandeln lokalisierter Textübermittlungen von Benutzern

Wenn Sie lokalisierte Versionen Ihrer Anwendung bereitstellen, ist es sehr wahrscheinlich, dass Ihre Benutzer mit derselben Sprache antworten. Teams übersetzt die Benutzerübermittlungen nicht zurück in die Standardsprache, daher muss Ihre App dies behandeln. Wenn Sie z. B. einen lokalisierten Bereitstellen, sind die Antworten auf Ihren Bot der lokalisierte Text des Befehls, nicht `commandList` die Standardsprache. Ihre App muss entsprechend reagieren.
