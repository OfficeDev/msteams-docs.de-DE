---
title: Lokalisierung für Ihre App
description: Beschreibt Überlegungen zum Lokalisieren Ihrer Microsoft Teams-App.
ms.topic: conceptual
localization_priority: Normal
keywords: Teams veröffentlichen Store Office Publishing AppSource-Lokalisierungssprache
ms.date: 05/15/2018
ms.openlocfilehash: a55b8af97e5306843858e5844a017dd402ab3516
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566047"
---
# <a name="localization-for-microsoft-teams-apps"></a>Lokalisierung für Microsoft Teams Apps

Beim Lokalisieren Ihrer Microsoft Teams-App müssen Sie Folgendes berücksichtigen:

1. Ihr Teams-Shop-Eintrag (falls zutreffend).
1. Die Endbenutzerzeichenfolgen in Ihrem App-Manifest. Zum Beispiel Bot-Befehle.
1. Reagieren auf lokalisierten Text, der von Ihren Benutzern gesendet wurde.

## <a name="localizing-your-appsource-listing"></a>Lokalisieren Ihres AppSource-Eintrags

Wenn Sie im Store veröffentlichen, müssen Sie sich bewusst sein, dass die Lokalisierung Ihres AppSource-Eintrags noch nicht unterstützt wird. In Vorbereitung auf die Unterstützung für lokalisierte Angebote im App Store können Sie Ihrem Eintrag jedoch weitere Sprachen hinzufügen. Derzeit werden nur die Standard-Sprachinformationen (Englisch), die Sie im [Partner Center](/office/dev/store/submit-to-appsource-via-partner-center) für Ihren Eintrag bereitstellen, im [AppSource-Websiteeintrag](https://appsource.microsoft.com/marketplace/apps?product=office%3Bteams&page=1) für Ihre App angezeigt.

### <a name="example-of-configuring-localization"></a>Beispiel für die Konfiguration der Lokalisierung

Um eine zusätzliche Sprache für Ihre App zu konfigurieren, wählen Sie im [Partner Center](/office/dev/store/submit-to-appsource-via-partner-center)sowohl Englisch als auch die zusätzliche Sprache der App aus. In diesem Beispiel wird Französisch verwendet:

1. Englische Sprache hinzufügen
    * Geben Sie den App-Namen ein.
    * Füllen Sie eine kurze Beschreibung der App in englischer Sprache aus.
    * Füllen Sie die lange Beschreibung der App in englischer Sprache aus.
    * In der langen Beschreibung fügen Sie bitte auch die Zeile "Diese App ist in "Französisch" verfügbar.
    * Hochladen die Bilder Ihrer App-Benutzeroberfläche (in englischer Sprache).
2. Französisch hinzufügen
    * Geben Sie den App-Namen ein.
    * Füllen Sie eine kurze Beschreibung der App auf Französisch aus.
    * Füllen Sie die lange Beschreibung der App auf Französisch aus.
    * Hochladen die Bilder Ihrer App-Benutzeroberfläche (auf Französisch).

Die Bilder, die Sie mit der englischen Sprache hochladen, werden in AppSource verwendet.

## <a name="localizing-the-strings-in-your-app-manifest"></a>Lokalisieren der Zeichenfolgen in Ihrem App-Manifest

Sie müssen das Microsoft Teams App-Schema v1.5+ verwenden, um Ihre App ordnungsgemäß zu lokalisieren. Sie können dies tun, indem Sie das `$schema` Attribut in Ihrem manifest.jsin der Datei auf ' ' setzen und die https://developer.microsoft.com/en-us/json-schemas/teams/v1.8/MicrosoftTeams.Localization.schema.json 'manifestVersion'-Eigenschaft auf '1.7' aktualisieren.

### <a name="example-manifestjson-change"></a>Beispiel manifest.jszur Änderung

```json
{
  "$schema": "https://developer.microsoft.com/en-us/json-schemas/teams/v1.8/MicrosoftTeams.Localization.schema.json",
  "manifestVersion": "1.5",
  ...
}
```

Sie sollten dann die Eigenschaft 'localizationInfo' mit der Standardsprache hinzufügen, die Ihre Anwendung unterstützt. Die Standardsprache wird als letzte Fallbacksprache verwendet, wenn die Clienteinstellungen des Benutzers nicht mit einer Ihrer zusätzlichen Sprachen übereinstimmen.

### <a name="example-manifestjson-change"></a>Beispiel manifest.jszur Änderung

```json
{
  ...
  "localizationInfo": {
    "defaultLanguageTag": "en"
  }
  ...
}
```

Sie können zusätzliche JSon-Dateien mit Übersetzungen aller Benutzerzeichenfolgen in Ihrem Manifest bereitstellen. Diese Dateien müssen dem [JSON-Schema der Lokalisierungsdatei](../../resources/schema/localization-schema.md) entsprechen und der "localizationInfo"-Eigenschaft Ihres Manifests hinzugefügt werden. Jede Datei korreliert mit einem Sprachtag, das der Teams-Client verwendet, um die entsprechenden Zeichenfolgen auszuwählen. Das Sprach-Tag hat die Form <language> - <region> von, aber es wird empfohlen, den <region> Teil wegzulassen, um alle Regionen anzusprechen, die die gewünschte Sprache unterstützen.

Der Teams-Client wendet die Zeichenfolgen in dieser Reihenfolge an: Standard-Sprachzeichenfolgen -> Sprache des Benutzers nur Zeichenfolgen -> Sprache + Die Regionszeichenfolgen des Benutzers.

Sie geben z. B. eine Standardsprache von 'fr' (Französisch, alle Regionen) und zusätzliche Sprachdateien für 'en' (Englisch, alle Regionen) und 'en-gb' (Englisch, Großbritannien) an. Wenn die Sprache des Benutzers auf 'en-gb' gesetzt ist:

1. Der Teams-Client übernimmt die 'fr'-Zeichenfolgen, die sie mit den 'en'-Zeichenfolgen überschreiben.
2. Überschreiben Sie diejenigen mit den Zeichenfolgen 'en-gb'.

Wenn die Sprache des Benutzers auf 'en-ca' gesetzt ist: 

1. Der Teams-Client übernimmt die 'fr'-Zeichenfolgen, die sie mit den 'en'-Zeichenfolgen überschreiben.
2. Da keine "en-ca"-Lokalisierung bereitgestellt wird, werden die "en"-Lokalisierungen verwendet.

Wenn die Sprache des Benutzers auf 'es-es' gesetzt ist, nimmt der Teams Client die 'fr'-Zeichenfolgen und überschreibt sie nicht mit einer der Sprachdateien.

Daher wird dringend empfohlen, Übersetzungen auf oberster Ebene, nur für Die Sprache, in Ihrem Manifest bereitzustellen ('en' statt 'en-us') und nur Überschreibungen auf Regionsebene für die wenigen Zeichenfolgen bereitzustellen, die sie benötigen.

### <a name="example-manifestjson-change"></a>Beispiel manifest.jszur Änderung

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

### <a name="example-localization-json-file"></a>Beispiellokalisierung .json-Datei

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

Wenn Sie lokalisierte Versionen Ihrer Anwendung bereitstellen, ist es sehr wahrscheinlich, dass Ihre Benutzer mit derselben Sprache antworten. Teams übersetzt die Benutzerübermittlungen nicht zurück in die Standardsprache, daher muss Ihre App dies verarbeiten. Wenn Sie z. B. einen lokalisierten befehlsgebundenen Befehl angeben, `commandList` sind die Antworten auf Ihren Bot der lokalisierte Text des Befehls und nicht die Standardsprache. Ihre App muss entsprechend reagieren.

## <a name="code-sample"></a>Codebeispiel

| Beispielname | Beschreibung | .NET |
|-------------|-------------|------|
| App-Lokalisierung | Microsoft Teams App-Lokalisierung mit Bot und Tab. | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-localization/csharp) |


