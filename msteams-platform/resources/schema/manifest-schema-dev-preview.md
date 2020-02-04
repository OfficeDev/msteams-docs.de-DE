---
title: Manifest-Schemareferenz für Entwicklervorschau
description: Beschreibt das vom Manifest für Microsoft Teams unterstützte Schema.
keywords: Entwicklervorschau für Teams-Manifest-Schema
ms.date: 05/20/2019
ms.openlocfilehash: b99e1ae99b7fd1edd4c695f43f3ac25270f0c710
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674104"
---
# <a name="developer-preview-manifest-schema-for-microsoft-teams"></a>Manifest-Schema für Entwicklervorschau für Microsoft Teams

> [!NOTE]
> Informationen zum Programm und dazu, wie Sie teilnehmen können, finden Sie unter [Developer Preview](~/resources/dev-preview/developer-preview-intro.md) .
> Wenn Sie die Entwicklervorschau nicht verwenden, sollten Sie diese Version des Manifests nicht verwenden. Siehe [Referenz: Manifest-Schema für Microsoft Teams](~/resources/schema/manifest-schema.md) für die öffentliche Version des Manifests.

Das Microsoft Teams-Manifest beschreibt, wie die app in das Microsoft Teams-Produkt integriert wird. Das Manifest muss dem Schema entsprechen, das unter [`https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json`](https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json)gehostet wird.

Weitere Informationen zu den verfügbaren Features finden Sie unter: [Features in der Public Developer Preview für Microsoft Teams](~/resources/dev-preview/developer-preview-features.md).

## <a name="sample-full-manifest"></a>Vollständiges Beispiel Manifest

```json
{
  "$schema": "https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json",
  "manifestVersion": "devPreview",
  "version": "1.0.0",
  "id": "%MICROSOFT-APP-ID%",
  "packageName": "com.example.myapp",
  "devicePermissions" : [ "geolocation", "media" ],
  "developer": {
    "name": "Publisher Name",
    "websiteUrl": "https://website.com/",
    "privacyUrl": "https://website.com/privacy",
    "termsOfUseUrl": "https://website.com/app-tos",
    "mpnId": "1234567890"
  },
  "localizationInfo": {
    "defaultLanguageTag": "es-es",
    "additionalLanguages": [
      {
        "languageTag": "en-us",
        "file": "en-us.json"
      }
    ]
  },
  "name": {
    "short": "Name of your app (<=30 chars)",
    "full": "Full name of app, if longer than 30 characters"
  },
  "description": {
    "short": "Short description of your app",
    "full": "Full description of your app"
  },
  "icons": {
    "outline": "%FILENAME-32x32px%",
    "color": "%FILENAME-192x192px"
  },
  "accentColor": "%HEX-COLOR%",
  "configurableTabs": [
    {
      "configurationUrl": "https://contoso.com/teamstab/configure",
      "canUpdateConfiguration": true,
      "scopes": [ "team", "groupchat" ]
    }
  ],
  "staticTabs": [
    {
      "entityId": "idForPage",
      "name": "Display name of tab",
      "contentUrl": "https://contoso.com/content?host=msteams",
      "websiteUrl": "https://contoso.com/content",
      "scopes": [ "personal" ]
    }
  ],
  "bots": [
    {
      "botId": "%MICROSOFT-APP-ID-REGISTERED-WITH-BOT-FRAMEWORK%",
      "needsChannelSelector": false,
      "isNotificationOnly": false,
      "scopes": [ "team", "personal", "groupchat" ],
      "supportsFiles": true,
      "commandLists": [
        {
          "scopes": [ "team", "groupchat" ],
          "commands": [
            {
              "title": "Command 1",
              "description": "Description of Command 1"
            },
            {
              "title": "Command N",
              "description": "Description of Command N"
            }
          ]
        },
        {
          "scopes": [ "personal", "groupchat" ],
          "commands": [
            {
              "title": "Personal command 1",
              "description": "Description of Personal command 1"
            },
            {
              "title": "Personal command N",
              "description": "Description of Personal command N"
            }
          ]
        }
      ]
    }
  ],
  "connectors": [
    {
      "connectorId": "GUID-FROM-CONNECTOR-DEV-PORTAL%",
      "configurationUrl": "https://contoso.com/teamsconnector/configure",
      "scopes": [ "team"]
    }
  ],
  "composeExtensions": [
    {
      "botId": "%MICROSOFT-APP-ID-REGISTERED-WITH-BOT-FRAMEWORK%",
      "canUpdateConfiguration": true,
      "commands": [
        {
          "id": "exampleCmd1",
          "title": "Example Command",
          "description": "Command Description; e.g., Search on the web",
          "initialRun": true,
          "type" : "search",
          "context" : ["compose", "commandBox"],
          "parameters": [
            {
              "name": "keyword",
              "title": "Search keywords",
              "description": "Enter the keywords to search for"
            }
          ]
        },
        {
          "id": "exampleCmd2",
          "title": "Example Command 2",
          "description": "Command Description; e.g., Search for a customer",
          "initialRun": true,
          "type" : "action",
          "fetchTask" : true,
          "context" : ["message"],
          "parameters": [
            {
              "name": "custinfo",
              "title": "Customer name",
              "description": "Enter a customer name",
              "inputType" : "text"
            }
          ]
        },
        {
          "id": "exampleMessageHandler",
          "title": "Message Handler",
          "description": "Domains that will create a preview when pasted into the compose box",
          "messageHandlers": [
            {
              "type" : "link",
              "value" : {
                "domains" : [
                  "mysite.someplace.com",
                  "othersite.someplace.com"
                ]
              }
            }
          ]
        }
      ]
    }
  ],
  "permissions": [
    "identity",
    "messageTeamMembers",
  ],
  "validDomains": [
     "contoso.com",
     "mysite.someplace.com",
     "othersite.someplace.com"
  ]
}
```

Das Schema definiert die folgenden Eigenschaften:

## <a name="schema"></a>$schema

*Optionale, aber empfohlene* &ndash; Zeichenfolge

Die https://-URL, die auf das JSON-Schema für das Manifest verweist.

## <a name="manifestversion"></a>manifestVersion

**Erforderliche** &ndash; Zeichenfolge

Die Version des manifest-Schemas, die dieses Manifest verwendet. Es sollte "devPreview" sein.

## <a name="version"></a>Version

**Erforderliche** &ndash; Zeichenfolge

Die Version der jeweiligen App. Wenn Sie etwas in ihrem Manifest aktualisieren, muss die Version ebenfalls inkrementiert werden. Auf diese Weise wird bei der Installation des neuen Manifests das vorhandene überschrieben, und der Benutzer erhält die neue Funktionalität. Wenn diese APP an den Store übermittelt wurde, muss das neue Manifest erneut übermittelt und erneut validiert werden. Dann erhalten Benutzer dieser APP das neue aktualisierte Manifest automatisch in ein paar Stunden, nachdem es genehmigt wurde.

Wenn sich die angeforderte APP geändert hat, werden die Benutzer aufgefordert, die APP zu aktualisieren und erneut zu genehmigen.

Diese Versionszeichenfolge muss dem [semver](http://semver.org/) -Standard (Major) entsprechen. Moll. Patch).

## <a name="id"></a>id

**Erforderliche** &ndash; Microsoft-App-ID

Der eindeutige von Microsoft generierte Bezeichner für diese APP. Wenn Sie einen bot über das Microsoft bot-Framework registriert haben oder sich die Webanwendung Ihrer Registerkarte bereits bei Microsoft anmeldet, sollten Sie bereits über eine ID verfügen und diese hier eingeben. Andernfalls sollten Sie eine neue ID im Microsoft-Anwendungs Registrierungs Portal ([meine Anwendungen](https://apps.dev.microsoft.com)) generieren, Sie hier eingeben und dann wieder verwenden, wenn Sie [einen bot hinzufügen](~/bots/how-to/create-a-bot-for-teams.md).

## <a name="packagename"></a>PackageName

**Erforderliche** &ndash; Zeichenfolge

Ein eindeutiger Bezeichner für diese APP in umgekehrter Domänen Notation; Beispiel: com. Beispiel. MyApp.

## <a name="developer"></a>developer

**Required**

Gibt Informationen zu Ihrem Unternehmen an. Für an AppSource übermittelte Apps (ehemals Office Store) müssen diese Werte mit den Informationen in Ihrem AppSource-Eintrag übereinstimmen.

|Name| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|
|`name`|32 Zeichen|✔|Der Anzeigename für den Entwickler.|
|`websiteUrl`|2048 Zeichen|✔|Die https://-URL zur Website des Entwicklers. Dieser Link sollte Benutzer zu Ihrer Firma oder produktspezifischen Zielseite führen.|
|`privacyUrl`|2048 Zeichen|✔|Die https://-URL zur Datenschutzrichtlinie des Entwicklers.|
|`termsOfUseUrl`|2048 Zeichen|✔|Die https://-URL zu den Nutzungsbedingungen des Entwicklers.|
|`mpnId`|10 Zeichen|✔|**Optional** Die Microsoft Partner-Netzwerk-ID, die die Partnerorganisation identifiziert, die die APP aufbaut.|

## <a name="localizationinfo"></a>localizationInfo

**Optional**

Ermöglicht die Angabe einer Standardsprache sowie Zeiger auf zusätzliche Sprachdateien. Siehe [Lokalisierung](~/concepts/build-and-test/apps-localization.md).

|Name| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|
|`defaultLanguageTag`|4 Zeichen|✔|Das Language-Tag der Zeichenfolgen in dieser Manifestdatei der obersten Ebene.|

### <a name="localizationinfoadditionallanguages"></a>localizationInfo.additionalLanguages

Ein Array von Objekten, das zusätzliche Sprachübersetzungen angibt.

|Name| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|
|`languageTag`|4 Zeichen|✔|Das Language-Tag der Zeichenfolgen in der bereitgestellten Datei.|
|`file`|4 Zeichen|✔|Ein relativer Dateipfad zu einer JSON-Datei, die die übersetzten Zeichenfolgen enthält.|

## <a name="name"></a>Name

**Required**

Der Name der APP-Erfahrung, der Benutzern in der Microsoft Teams-Benutzeroberfläche angezeigt wird. Für apps, die an AppSource übermittelt werden, müssen diese Werte mit den Informationen in Ihrem AppSource-Eintrag übereinstimmen. Die Werte von `short` und `full` sollten nicht identisch sein.

|Name| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|
|`short`|30 Zeichen|✔|Der kurze Anzeigename für die app.|
|`full`|100 Zeichen||Der vollständige Name der APP, der verwendet wird, wenn der vollständige App-Name 30 Zeichen überschreitet.|

## <a name="description"></a>description

**Required**

Beschreibt die APP für Benutzer. Für apps, die an AppSource übermittelt werden, müssen diese Werte mit den Informationen in Ihrem AppSource-Eintrag übereinstimmen.

Stellen Sie sicher, dass Ihre Beschreibung ihre Erfahrung genau beschreibt und Informationen bereitstellt, um potenziellen Kunden zu helfen, ihre Erfahrungen zu verstehen. Beachten Sie auch, dass in der vollständigen Beschreibung ein externes Konto zur Verwendung benötigt wird. Die Werte von `short` und `full` sollten nicht identisch sein.  Ihre Kurzbeschreibung darf nicht innerhalb der langen Beschreibung wiederholt werden und darf keinen anderen APP-Namen enthalten.

|Name| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|
|`short`|80 Zeichen|✔|Eine kurze Beschreibung Ihrer APP-Erfahrung, die verwendet wird, wenn der Speicherplatz limitiert ist.|
|`full`|4000 Zeichen|✔|Die vollständige Beschreibung Ihrer APP.|

## <a name="icons"></a>Symbole

**Required**

Symbole, die in der Teams-App verwendet werden. Die Symboldateien müssen als Teil des Upload-Pakets enthalten sein.

|Name| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|
|`outline`|2048 Zeichen|✔|Ein relativer Dateipfad zu einem transparenten 32x32 PNG-Gliederungssymbol.|
|`color`|2048 Zeichen|✔|Ein relativer Dateipfad zu einem vollfarbigen 192x192 PNG-Symbol.|

## <a name="accentcolor"></a>accentColor

**Erforderliche** &ndash; Zeichenfolge

Eine Farbe, die in Verbindung mit und als Hintergrund für die Gliederungssymbole verwendet werden soll.

Der Wert muss ein gültiger HTML-Farb Code sein, der mit "#" beginnt `#4464ee`, beispielsweise.

## <a name="configurabletabs"></a>configurableTabs

**Optional**

Wird verwendet, wenn Ihre APP-Erfahrung eine Team Kanal-registerkartenoberfläche aufweist, die eine zusätzliche Konfiguration erfordert, bevor Sie hinzugefügt wird. Konfigurierbare Registerkarten werden nur im Bereich Teams unterstützt, und derzeit wird nur eine Registerkarte pro App unterstützt.

Das Objekt ist ein Array mit allen Elementen des Typs `object`. Dieser Block ist nur für Lösungen erforderlich, die eine konfigurierbare Kanal Registerkarten Lösung bieten.

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`configurationUrl`|Zeichenfolge|2048 Zeichen|✔|Die https://-URL, die beim Konfigurieren der Registerkarte verwendet werden soll.|
|`canUpdateConfiguration`|Boolesch|||Ein Wert, der angibt, ob eine Instanz der Konfiguration der Registerkarte nach der Erstellung vom Benutzer aktualisiert werden kann. Standard`true`|
|`scopes`|Array von Enum|1 |✔|Derzeit unterstützen konfigurierbare Registerkarten `team` nur `groupchat` die Bereiche und. |
|`sharePointPreviewImage`|Zeichenfolge|2048||Ein relativer Dateipfad zu einem Vorschaubild für die Registerkarte für die Verwendung in SharePoint. Größe 1024x768. |
|`supportedSharePointHosts`|Array von Enum|1 ||Definiert, wie die Registerkarte in SharePoint zur Verfügung gestellt wird. Optionen sind `sharePointFullPage` und`sharePointWebPart` |

## <a name="statictabs"></a>staticTabs

**Optional**

Definiert eine Gruppe von Registerkarten, die standardmäßig "fixiert" werden können, ohne dass der Benutzer Sie manuell hinzufügt. Im `personal` Bereich deklarierte statische Registerkarten werden immer an die persönliche Benutzeroberfläche der APP angeheftet. Im `team` Bereich deklarierte statische Registerkarten werden derzeit nicht unterstützt.

Bei dem Objekt handelt es sich um ein Array (maximal 16 Elemente) mit allen Elementen `object`des Typs. Dieser Block ist nur für Lösungen erforderlich, die eine statische Registerkarten Lösung bereitstellen.

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`entityId`|Zeichenfolge|64 Zeichen|✔|Ein eindeutiger Bezeichner für die Entität, die auf der Registerkarte angezeigt wird.|
|`name`|Zeichenfolge|128 Zeichen|✔|Der Anzeigename der Registerkarte in der Kanalschnittstelle.|
|`contentUrl`|Zeichenfolge|2048 Zeichen|✔|Die https://-URL, die auf die Benutzeroberfläche der Entität zeigt, die im Canvas "Teams" angezeigt werden soll.|
|`websiteUrl`|Zeichenfolge|2048 Zeichen||Die https://-URL, auf die verwiesen wird, wenn ein Benutzer sich für die Anzeige in einem Browser entscheidet.|
|`scopes`|Array von Enum|1 |✔|Derzeit unterstützen statische Registerkarten nur `personal` den Bereich, was bedeutet, dass Sie nur als Teil der persönlichen Benutzeroberfläche vorgesehen werden kann.|

## <a name="bots"></a>Bots

**Optional**

Definiert eine bot-Lösung zusammen mit optionalen Informationen wie Standardbefehls Eigenschaften.

Das Objekt ist ein Array (Maximum von nur 1 Element&mdash;, das derzeit nur ein bot pro App zulässig ist) mit allen Elementen des `object`Typs. Dieser Block ist nur für Lösungen erforderlich, die eine bot-Erfahrung bieten.

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`botId`|Zeichenfolge|64 Zeichen|✔|Die eindeutige Microsoft-App-ID für den bot, die im bot-Framework registriert ist. Dies kann auch die gesamte [App-ID](#id)entsprechen.|
|`needsChannelSelector`|Boolesch|||Beschreibt, ob der bot einen Benutzerhinweis verwendet, um den bot einem bestimmten Kanal hinzuzufügen. Standard`false`|
|`isNotificationOnly`|Boolesch|||Gibt an, ob ein bot ein unidirektionaler, nur für Benachrichtigungen gestellter bot ist, im Gegensatz zu einem Unterhaltungs bot. Standard`false`|
|`supportsFiles`|Boolesch|||Gibt an, ob der bot die Möglichkeit unterstützt, Dateien im persönlichen Chat hoch-/herunterzuladen. Standard`false`|
|`scopes`|Array von Enum|3 |✔|Gibt an, ob der bot eine Erfahrung im Kontext eines Kanals in a `team`, in einem Gruppenchat (`groupchat`) oder eine Erfahrung bietet, die auf einen einzelnen Benutzer allein beschränkt`personal`ist (). Diese Optionen sind nicht exklusiv.|

### <a name="botscommandlists"></a>Bots. commandLists

Eine optionale Liste von Befehlen, die ihr bot Benutzern empfehlen kann. Das Objekt ist ein Array (Maximum von 2 Elementen) mit allen Elementen des Typs `object`; Sie müssen für jeden Bereich, den Ihr bot unterstützt, eine separate Befehlsliste definieren. Weitere Informationen finden Sie unter [bot-Menüs](~/bots/how-to/create-a-bot-commands-menu.md) .

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`items.scopes`|Array von Enum|3 |✔|Gibt den Bereich an, für den die Befehlsliste gültig ist. Optionen sind `team`, `personal`und `groupchat`.|
|`items.commands`|Array von Objekten|10  |✔|Ein Array von Befehlen, die der bot unterstützt:<br>`title`: der Name des bot-Befehls (String, 32)<br>`description`: eine einfache Beschreibung oder ein Beispiel für die Befehlssyntax und das zugehörige Argument (String, 128)|

## <a name="connectors"></a>Connectors

**Optional**

Der `connectors` Block definiert einen Office 365-Konnektor für die app.

Das Objekt ist ein Array (Maximum of 1-Element) mit allen Elementen des `object`Typs. Dieser Block ist nur für Lösungen erforderlich, die einen Connector bereitstellen.

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`configurationUrl`|Zeichenfolge|2048 Zeichen|✔|Die https://-URL, die beim Konfigurieren des Connectors verwendet werden soll.|
|`connectorId`|Zeichenfolge|64 Zeichen|✔|Ein eindeutiger Bezeichner für den Connector, der seiner ID im [Entwickler Dashboard für Connectors](https://aka.ms/connectorsdashboard)entspricht.|
|`scopes`|Array von Enum|1 |✔|Gibt an, ob der Connector eine Erfahrung im Kontext eines Kanals in a `team`bietet oder ein Erlebnis, das allein auf einen einzelnen Benutzer beschränkt`personal`ist (). Derzeit wird nur der `team` Bereich unterstützt.|

## <a name="composeextensions"></a>composeExtensions

**Optional**

Definiert eine Messaging Erweiterung für die app.

> [!NOTE]
> Der Name des Features wurde von "Erstell Erweiterung" in "Messaging Extension" im November 2017 geändert, aber der Manifestname bleibt unverändert, sodass vorhandene Erweiterungen weiterhin funktionieren.

Das Objekt ist ein Array (Maximum of 1-Element) mit allen Elementen des `object`Typs. Dieser Block ist nur für Lösungen erforderlich, die eine Messaging Erweiterung bereitstellen.

|Name| Typ | Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`botId`|Zeichenfolge|64|✔|Die eindeutige Microsoft-App-ID für den bot, der die Messaging Erweiterung unterstützt, wie Sie mit dem bot-Framework registriert wurde. Dies kann auch die gesamte [App-ID](#id)entsprechen.|
|`canUpdateConfiguration`|Boolesch|||Ein Wert, der angibt, ob die Konfiguration einer Messaging Erweiterung vom Benutzer aktualisiert werden kann. Der Standardwert `false`ist.|
|`commands`|Array von Object|10  |✔|Array von Befehlen, die von der Messaging-Erweiterung unterstützt werden|

### <a name="composeextensionscommands"></a>composeExtensions. Commands

Ihre Messaging Erweiterung sollte einen oder mehrere Befehle deklarieren. Jeder Befehl wird in Microsoft Teams als potenzielle Interaktion aus dem Benutzeroberflächen basierten Einstiegspfad angezeigt. Es gibt maximal 10 Befehle.

Jedes Command-Element ist ein Objekt mit der folgenden Struktur:

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`id`|Zeichenfolge|64 Zeichen|✔|Die ID für den Befehl|
|`type`|Zeichenfolge|64 Zeichen||Der Typ des Befehls. Einer von `query` oder `action`. Standard`query`|
|`title`|Zeichenfolge|32 Zeichen|✔|Der benutzerfreundliche Befehlsname|
|`description`|Zeichenfolge|128 Zeichen||Die Beschreibung, die den Benutzern angezeigt wird, um den Zweck dieses Befehls anzugeben|
|`initialRun`|Boolesch|||Ein boolescher Wert, der angibt, ob der Befehl anfänglich ohne Parameter ausgeführt werden soll. Standard`false`|
|`context`|Array von Zeichenfolgen|3 ||Definiert, woher die Nachrichten Erweiterung aufgerufen werden kann. Eine beliebige Kombi `compose`Nation `commandBox`von `message`,,. Der Standardwert ist`["compose", "commandBox"]`|
|`fetchTask`|Boolesch|||Ein boolescher Wert, der angibt, ob das Aufgabenmodul dynamisch abgerufen werden soll.|
|`taskInfo`|Object|||Angeben des Aufgabenmoduls, das beim Verwenden eines Messaging Erweiterungs Befehls geladen werden soll|
|`taskInfo.title`|Zeichenfolge|64||Ursprünglicher Dialogtitel|
|`taskInfo.width`|Zeichenfolge|||Dialog Breite-entweder eine Zahl in Pixel oder ein Standardlayout wie "groß", "Mittel" oder "klein"|
|`taskInfo.height`|Zeichenfolge|||Dialog Feld Höhe-entweder eine Zahl in Pixel oder ein Standardlayout wie "groß", "Mittel" oder "klein"|
|`taskInfo.url`|Zeichenfolge|||Anfängliche WebView-URL|
|`messageHandlers`|Array von Objekten|5 ||Eine Liste von Handlern, mit denen apps aufgerufen werden können, wenn bestimmte Bedingungen erfüllt sind. Domänen müssen ebenfalls in aufgeführt sein.`validDomains`|
|`messageHandlers.type`|Zeichenfolge|||Der Typ des Nachrichten Handlers. Muss `"link"` sein.|
|`messageHandlers.value.domains`|Array von Zeichenfolgen|||Array von Domänen, für die der Link Nachrichtenhandler registriert werden kann.|
|`parameters`|Array von Object|5 |✔|Die Liste der Parameter, die der Befehl benötigt. Minimum: 1; Maximum: 5|
|`parameter.name`|Zeichenfolge|64 Zeichen|✔|Der Name des Parameters, wie er im Client angezeigt wird. Dies ist in der Benutzeranforderung enthalten.|
|`parameter.title`|Zeichenfolge|32 Zeichen|✔|Benutzerfreundlicher Titel für den Parameter.|
|`parameter.description`|Zeichenfolge|128 Zeichen||Benutzerfreundliche Zeichenfolge, die den Zweck dieses Parameters beschreibt.|
|`parameter.inputType`|Zeichenfolge|128 Zeichen||Definiert den Typ des Steuerelements, das in einem Aufgaben `fetchTask: true`Modul für angezeigt wird. Eine von `text`, `textarea`, `number`, `date`, `time`, `toggle`,`choiceset`|
|`parameter.choices`|Array von Objekten|10  ||Die Auswahloptionen für `choiceset`. Nur verwenden, `parameter.inputType` wenn`choiceset`|
|`parameter.choices.title`|Zeichenfolge|128||Titel der Auswahl|
|`parameter.choices.value`|Zeichenfolge|512||Wert der Auswahl|

## <a name="permissions"></a>Berechtigungen

**Optional**

Ein Array `string` , das angibt, welche Berechtigungen die APP anfordert, sodass Endbenutzer wissen, wie die Erweiterung ausgeführt wird. Die folgenden Optionen sind nicht exklusiv:

* `identity`&emsp; Erfordert Benutzeridentitätsinformationen
* `messageTeamMembers`&emsp; Erfordert die Berechtigung zum Senden von direkten Nachrichten an Teammitglieder.

Wenn Sie diese Berechtigungen beim Aktualisieren Ihrer APP ändern, werden die Benutzer beim ersten Ausführen der aktualisierten App den Zustimmungsprozess wiederholen.

## <a name="devicepermissions"></a>devicePermissions

**Optional** Array von Zeichenfolgen

Gibt die systemeigenen Funktionen auf dem Gerät eines Benutzers an, für die Ihre APP möglicherweise Zugriff anfordern kann. Die Optionen lauten wie folgt:

* `geolocation`
* `media`
* `notifications`
* `midi`
* `openExternal`

## <a name="validdomains"></a>validDomains

**Optional**, sofern angegeben, außer **erforderlich**

Eine Liste gültiger Domänen, von denen die APP erwartet, dass Sie Inhalte lädt. Domänen Auflistungen können beispielsweise `*.example.com`Platzhalterzeichen enthalten. Dies entspricht genau einem Segment der Domäne. Wenn Sie eine Übereinstimmung `a.b.example.com` benötigen, `*.*.example.com`verwenden Sie. Wenn Ihre Registerkartenkonfiguration oder Inhalts-UI neben einer Verwendung für die Registerkartenkonfiguration zu einer anderen Domäne navigieren muss, muss diese Domäne hier angegeben werden.

Es ist jedoch **nicht** erforderlich, die Domänen von Identitätsanbietern einzubeziehen, die Sie in Ihrer APP unterstützen möchten. Um beispielsweise mit einer Google-ID zu authentifizieren, müssen Sie zu Accounts.Google.com umgeleitet werden, aber Sie sollten Accounts.Google.com nicht in `validDomains[]`einschließen.

> [!IMPORTANT]
> Fügen Sie keine Domänen hinzu, die sich außerhalb des Steuerelements befinden, entweder direkt oder über Platzhalter. Beispielsweise `yourapp.onmicrosoft.com` ist gültig, jedoch `*.onmicrosoft.com` ungültig.

Das Objekt ist ein Array mit allen Elementen des Typs `string`.

## <a name="webapplicationinfo"></a>webApplicationInfo

**Optional**

Geben Sie Ihre Aad-APP-ID und Diagramm Informationen an, damit Benutzer sich nahtlos bei ihrer Aad-App anmelden können.

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`id`|Zeichenfolge|36 Zeichen|✔|Aad-Anwendungs-ID der app. Diese ID muss eine GUID sein.|
|`resource`|Zeichenfolge|2048 Zeichen|✔|Ressourcen-URL der APP zum Abrufen des Authentifizierungstokens für SSO.|