---
title: Lokalisierung für Team-apps
description: Beschreibt Probleme beim Lokalisieren Ihrer APP.
keywords: Teams veröffentlichen Store Office Publishing AppSource Localization Language
ms.date: 05/15/2018
ms.openlocfilehash: 30e4a2589bf5c1093723406c78cff2258554c486
ms.sourcegitcommit: 6c786434b56cc8c2765a14aa1f6149870245f309
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/06/2020
ms.locfileid: "44590858"
---
# <a name="localization-for-microsoft-teams-apps"></a>Lokalisierung für Microsoft Teams-apps

Beim Lokalisieren Ihrer Microsoft Teams-App gibt es drei wichtige Bereiche, die Sie berücksichtigen müssen.

1. Ihr AppSource-Eintrag (falls Sie im App Store veröffentlicht werden).
1. Die benutzerbezogenen Zeichenfolgen in Ihrem App-Manifest (beispielsweise bot-Befehle).
1. Reagieren auf lokalisierten Text, der von Ihren Benutzern übermittelt wurde.

## <a name="localizing-your-appsource-listing"></a>Lokalisieren Ihres AppSource-Eintrags

Wenn Sie im App Store veröffentlichen, müssen Sie beachten, dass die Lokalisierung Ihres AppSource-Eintrags noch nicht unterstützt wird. In Vorbereitung auf die Unterstützung lokalisierter Auflistungen im App Store können Sie jedoch weitere Sprachen zu Ihrem Angebot hinzufügen. Derzeit werden nur die standardmäßigen (englischsprachigen) Informationen, die Sie im [Partner Center](/dev/store/use-partner-center-to-submit-to-appsource) für Ihr Angebot angeben, im [AppSource-Website](https://appsource.microsoft.com/marketplace/apps?product=office%3Bteams&page=1) Eintrag für Ihre APP angezeigt.

Zum Konfigurieren einer zusätzlichen Sprache für Ihre APP wählen Sie im [Partner Center](/dev/store/use-partner-center-to-submit-to-appsource)sowohl Englisch als auch die zusätzliche Sprache der APP aus. In diesem Beispiel wird Französisch verwendet.

1. Englische Sprache hinzufügen
    * Geben Sie den APP-Namen ein.
    * Geben Sie eine kurze Beschreibung der app in englischer Sprache ein.
    * Geben Sie die lange Beschreibung der app in Englisch ein.
    * In der langen Beschreibung fügen Sie bitte auch die-"diese APP ist in Französisch" zur Verfügung.
    * Laden Sie die Bilder der App-Benutzeroberfläche hoch (in englischer Sprache).
2. Französisch-Sprache hinzufügen
    * Geben Sie den APP-Namen ein.
    * Geben Sie eine kurze Beschreibung der app in Französisch ein.
    * Geben Sie die lange Beschreibung der app in Französisch ein.
    * Laden Sie die Bilder der App-Benutzeroberfläche (in Französisch) hoch.

Die Bilder, die Sie mit der englischen Sprache hochladen, werden in AppSource verwendet.

## <a name="localizing-the-strings-in-your-app-manifest"></a>Lokalisieren der Zeichenfolgen in Ihrem App-Manifest

Sie müssen das Microsoft Teams-App-Schema v 1.5 + verwenden, um Ihre APP ordnungsgemäß zu lokalisieren. Sie können dies tun, indem Sie das `$schema` -Attribut in ihrer Manifest. JSON-Datei auf ' https://developer.microsoft.com/json-schemas/teams/v1.7/MicrosoftTeams.schema.json ' festlegen und die Eigenschaft ' manifestVersion ' auf ' 1,5 ' aktualisieren.

### <a name="example-manifestjson-change"></a>Beispiel für Manifest. JSON-Änderung

```json
{
  "$schema": "https://developer.microsoft.com/json-schemas/teams/v1.7/MicrosoftTeams.schema.json",
  "manifestVersion": "1.5",
  ...
}
```

Anschließend möchten Sie die Eigenschaft "localizationInfo" mit der Standardsprache hinzufügen, die von der Anwendung unterstützt wird. Die Standardsprache wird als endgültige Fallbacksprache verwendet, wenn die Clienteinstellungen des Benutzers nicht mit einer ihrer zusätzlichen Sprachen übereinstimmen.

### <a name="example-manifestjson-change"></a>Beispiel für Manifest. JSON-Änderung

```json
{
  ...
  "localizationInfo": {
    "defaultLanguageTag": "en"
  }
  ...
}
```

Sie können zusätzliche JSON-Dateien mit Übersetzungen aller Benutzerzeichenfolgen in ihrem Manifest bereitstellen. Diese Dateien müssen dem [JSON-Schema der Lokalisierungsdatei](../../resources/schema/localization-schema.md) entsprechen, und Sie müssen der Eigenschaft "localizationInfo" des Manifests hinzugefügt werden. Jede Datei korreliert mit einem Language-Tag, das der Microsoft Teams-Client verwendet, um die entsprechenden Zeichenfolgen auszuwählen. Das sprach-Tag hat die Form, <language> - <region> aber es wird empfohlen, den Teil auszulassen, der <region> auf alle Regionen abzielt, die die gewünschte Sprache unterstützen.

Der Microsoft Teams-Client wendet die Zeichenfolgen in dieser Reihenfolge an: Standardsprachen Zeichenfolgen – > Sprache des Benutzers nur Zeichenfolgen – > Benutzersprache + Benutzer Regions Zeichenfolgen.

Sie geben beispielsweise eine Standardsprache von "fr" (Französisch, alle Regionen) und zusätzliche Sprachdateien für "en" (Englisch, alle Regionen) und "en-GB" (Englisch, Großbritannien) an. Wenn die Sprache des Benutzers auf "en-GB" festgelegt ist:

1. Der Microsoft Teams-Client nimmt die Zeichenfolgen "fr" mit den Zeichenfolgen "en" überschrieben.
2. Überschreiben Sie diese mit den Zeichenfolgen "en-GB".

Wenn die Sprache des Benutzers auf "en-ca" festgelegt ist: 

1. Der Microsoft Teams-Client nimmt die Zeichenfolgen "fr" mit den Zeichenfolgen "en" überschrieben.
2. Da keine "en-ca"-Lokalisierung bereitgestellt wird, werden die "en"-Lokalisierungen verwendet.

Wenn die Sprache des Benutzers auf "es-es" festgelegt ist, übernimmt der Microsoft Teams-Client die Zeichenfolgen "fr" und setzt diese nicht mit einer der Sprachdateien außer Kraft.

Daher wird dringend empfohlen, nur Übersetzungen auf oberster Ebene in ihrem Manifest ("en" anstelle von "en-US") bereitzustellen und nur Überschreibungen auf Regionsebene für die wenigen Zeichenfolgen bereitzustellen, die Sie benötigen.

### <a name="example-manifestjson-change"></a>Beispiel für Manifest. JSON-Änderung

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

### <a name="example-localization-json-file"></a>Beispiel für die Datei "Localization. JSON"

```json
{
  "$schema": "https://developer.microsoft.com/json-schemas/teams/v1.7/MicrosoftTeams.schema.json",
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

## <a name="handling-localized-text-submissions-from-your-users"></a>Behandeln lokalisierter Text Übermittlungen von Benutzern

Wenn Ihre lokalisierten Versionen Ihrer Anwendung bereitstellen, ist es sehr wahrscheinlich, dass Ihre Benutzer mit der gleichen Sprache Antworten werden. Die Benutzereingaben werden von Microsoft Teams nicht wieder in die Standardsprache übersetzt, sodass Ihre APP dies verarbeiten muss. Wenn Sie beispielsweise eine lokalisierte bereitstellen `commandList` , sind die Antworten auf Ihren bot der lokalisierte Text des Befehls und nicht die Standardsprache. Ihre APP muss entsprechend reagiert werden.
