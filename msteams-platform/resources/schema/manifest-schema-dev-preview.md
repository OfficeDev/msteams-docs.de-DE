---
title: Referenz zum Entwicklervorschaumanifestschema
description: Beschreibt das vom Manifest unterstützte Schema für Microsoft Teams
ms.topic: reference
keywords: Teams-Manifestschema – Entwicklervorschau
localization_priority: Normal
ms.date: 05/20/2019
ms.openlocfilehash: c2009038341a22664b0f055fa9756a9d1eba87b9
ms.sourcegitcommit: 64c1cf2a268ef101a519bc31d171618d0f6cd12a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/13/2021
ms.locfileid: "52915090"
---
# <a name="developer-preview-manifest-schema-for-microsoft-teams"></a>Entwicklervorschau-Manifestschema für Microsoft Teams

Informationen zum Aktivieren der Entwicklervorschau finden Sie in der [öffentlichen Entwicklervorschau für Microsoft Teams.](~/resources/dev-preview/developer-preview-intro.md)

> [!NOTE]
> * Wenn Sie keine Vorschaufeatures für Entwickler verwenden, verwenden Sie stattdessen das [App-Manifest für GA-Features.](~/resources/schema/manifest-schema.md)

Das Microsoft Teams Manifest beschreibt, wie die App in das Microsoft Teams Produkt integriert wird. Ihr Manifest muss dem schema gehosteten [`https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json`](https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json) entsprechen.

Weitere Informationen zu den verfügbaren Features finden Sie [unter: Features in der Public Developer Preview für Microsoft Teams](~/resources/dev-preview/developer-preview-features.md).

## <a name="sample-full-manifest"></a>Vollständiges Beispielmanifest

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
      "contentBotId": "Specifies to the app that tab is an Adaptive Card Tab. You can either provide the contentBotId or contentUrl.",
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
  ],
  "webApplicationInfo": {
    "id": "AAD App ID",
    "resource": "Resource URL for acquiring auth token for SSO",
    "applicationPermissions": [
      "TeamSettings.Read.Group",
      "ChannelSettings.Read.Group",
      "ChannelSettings.Edit.Group",
      "Channel.Create.Group",
      "Channel.Delete.Group",
      "ChannelMessage.Read.Group",
      "TeamsApp.Read.Group",
      "TeamsTab.Read.Group",
      "TeamsTab.Create.Group",
      "TeamsTab.Edit.Group",
      "TeamsTab.Delete.Group",
      "Member.Read.Group",
      "Owner.Read.Group",
      "Member.ReadWrite.Group",
      "Owner.ReadWrite.Group"
    ],
  },
   "configurableProperties": [
     "name",
     "shortDescription",
     "longDescription",
     "smallImageUrl", 
     "largeImageUrl", 
     "accentColor",
     "developerUrl",
     "privacyUrl",
     "termsOfUseUrl"        
  ],
  "defaultInstallScope": "meetings",
  "defaultGroupCapability": {
    "meetings": "tab", 
    "team": "bot", 
    "groupchat": "bot"
  }
}
```

Das Schema definiert die folgenden Eigenschaften:

## <a name="schema"></a>$schema

*Optional, aber empfohlen* &ndash; Schnur

Die https://-URL, die auf das JSON-Schema für das Manifest verweist.

## <a name="manifestversion"></a>manifestVersion

**Erforderlich** &ndash; Schnur

Die Version des Manifestschemas, das dieses Manifest verwendet. Es sollte "devPreview" sein.

## <a name="version"></a>Version

**Erforderlich** &ndash; Schnur

Die Version der spezifischen App. Wenn Sie etwas in Ihrem Manifest aktualisieren, muss auch die Version erhöht werden. Auf diese Weise wird bei der Installation des neuen Manifests das vorhandene überschrieben, und der Benutzer erhält die neue Funktionalität. Wenn diese App an den Store übermittelt wurde, muss das neue Manifest erneut übermittelt und erneut überprüft werden. Anschließend erhalten Benutzer dieser App das neue aktualisierte Manifest automatisch in einigen Stunden, nachdem es genehmigt wurde.

Wenn sich die von der App angeforderten Berechtigungen ändern, werden die Benutzer aufgefordert, ein Upgrade durchzuführen und der App erneut zuzustimmen.

Diese Versionszeichenfolge muss dem [Semverstandard](http://semver.org/) (MAJOR. kleiner. PATCH).

## <a name="id"></a>id

**Erforderlich** &ndash; Microsoft-App-ID

Der eindeutige von Microsoft generierte Bezeichner für diese App. Wenn Sie einen Bot über die Microsoft Bot Framework registriert haben oder sich die Web-App Ihrer Registerkarte bereits bei Microsoft anmeldet, sollten Sie bereits über eine ID verfügen und sie hier eingeben. Andernfalls sollten Sie eine neue ID im Microsoft-Anwendungsregistrierungsportal[(Meine Anwendungen)](https://apps.dev.microsoft.com)generieren, sie hier eingeben und dann wiederverwenden, wenn Sie [einen Bot hinzufügen.](~/bots/how-to/create-a-bot-for-teams.md)

## <a name="packagename"></a>Packagename

**Erforderlich** &ndash; Schnur

Ein eindeutiger Bezeichner für diese App in umgekehrter Domänenschreibweise; z. B. com.example.myapp.

## <a name="developer"></a>developer

**Required**

Gibt Informationen zu Ihrem Unternehmen an. Bei An AppSource übermittelten Apps (früher Office Store) müssen diese Werte mit den Informationen in Ihrem AppSource-Eintrag übereinstimmen.

|Name| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|
|`name`|32 Zeichen|✔|Der Anzeigename für den Entwickler.|
|`websiteUrl`|2048 Zeichen|✔|Die https:// URL zur Website des Entwicklers. Dieser Link sollte Benutzer zu Ihrem Unternehmen oder zu einer produktspezifischen Angebotsseite führen.|
|`privacyUrl`|2048 Zeichen|✔|Die https:// URL zur Datenschutzrichtlinie des Entwicklers.|
|`termsOfUseUrl`|2048 Zeichen|✔|Die https:// URL zu den Nutzungsbedingungen des Entwicklers.|
|`mpnId`|10 Zeichen|✔|**Optional** Die Microsoft Partner Network-ID, die die Partnerorganisation identifiziert, die die App erstellt.|

## <a name="localizationinfo"></a>localizationInfo

**Optional**

Ermöglicht die Angabe einer Standardsprache sowie Zeiger auf zusätzliche Sprachdateien. Siehe [Lokalisierung](~/concepts/build-and-test/apps-localization.md).

|Name| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|
|`defaultLanguageTag`|4 Zeichen|✔|Das Sprachtag der Zeichenfolgen in dieser Manifestdatei auf oberster Ebene.|

### <a name="localizationinfoadditionallanguages"></a>localizationInfo.additionalLanguages

Ein Array von Objekten, die zusätzliche Sprachübersetzungen angeben.

|Name| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|
|`languageTag`|4 Zeichen|✔|Das Sprachtag der Zeichenfolgen in der bereitgestellten Datei.|
|`file`|4 Zeichen|✔|Ein relativer Dateipfad zu einer JSON-Datei, die die übersetzten Zeichenfolgen enthält.|

## <a name="name"></a>name

**Required**

Der Name Ihrer App-Erfahrung, der Benutzern in der Teams angezeigt wird. Für an AppSource übermittelte Apps müssen diese Werte mit den Informationen in Ihrem AppSource-Eintrag übereinstimmen. Die Werte von `short` und sollten nicht identisch `full` sein.

|Name| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|
|`short`|30 Zeichen|✔|Der kurze Anzeigename für die App.|
|`full`|100 Zeichen||Der vollständige Name der App, der verwendet wird, wenn der vollständige App-Name 30 Zeichen überschreitet.|

## <a name="description"></a>description

**Required**

Beschreibt Ihre App für Benutzer. Für an AppSource übermittelte Apps müssen diese Werte mit den Informationen in Ihrem AppSource-Eintrag übereinstimmen.

Stellen Sie sicher, dass Ihre Beschreibung Ihre Erfahrung genau beschreibt und Informationen bereitstellt, die potenziellen Kunden helfen, zu verstehen, was Ihre Erfahrung bewirkt. Beachten Sie in der vollständigen Beschreibung auch, ob für die Verwendung ein externes Konto erforderlich ist. Die Werte von `short` und sollten nicht identisch `full` sein.  Ihre kurze Beschreibung darf nicht innerhalb der langen Beschreibung wiederholt werden und darf keinen anderen App-Namen enthalten.

|Name| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|
|`short`|80 Zeichen|✔|Eine kurze Beschreibung der App-Erfahrung, die verwendet wird, wenn der Platz begrenzt ist.|
|`full`|4000 Zeichen|✔|Die vollständige Beschreibung Ihrer App.|

## <a name="icons"></a>Symbole

**Required**

Symbole, die in der Teams-App verwendet werden. Die Symboldateien müssen als Teil des Uploadpakets enthalten sein.

|Name| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|
|`outline`|2048 Zeichen|✔|Ein relativer Dateipfad zu einem transparenten 32 x 32 PNG-Gliederungssymbol.|
|`color`|2048 Zeichen|✔|Ein relativer Dateipfad zu einem farbigen PNG-Symbol mit 192 x 192.|

## <a name="accentcolor"></a>accentColor

**Erforderlich** &ndash; Schnur

Eine Farbe, die in Verbindung mit und als Hintergrund für Ihre Gliederungssymbole verwendet werden soll.

Der Wert muss ein gültiger HTML-Farbcode sein, der mit "#" beginnt, z. `#4464ee` B. .

## <a name="configurabletabs"></a>configurableTabs

**Optional**

Wird verwendet, wenn Ihre App-Erfahrung über eine Registerkartenoberfläche im Teamkanal verfügt, die eine zusätzliche Konfiguration erfordert, bevor sie hinzugefügt wird. Konfigurierbare Registerkarten werden nur im Teams-Bereich unterstützt, und derzeit wird nur eine Registerkarte pro App unterstützt.

Das Objekt ist ein Array mit allen Elementen des Typs `object` . Dieser Block ist nur für Lösungen erforderlich, die eine konfigurierbare Kanalregisterkartenlösung bereitstellen.

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`configurationUrl`|Zeichenfolge|2048 Zeichen|✔|Die https:// URL, die beim Konfigurieren der Registerkarte verwendet werden soll.|
|`canUpdateConfiguration`|Boolesch|||Ein Wert, der angibt, ob eine Instanz der Konfiguration der Registerkarte vom Benutzer nach der Erstellung aktualisiert werden kann. Standard: `true`|
|`scopes`|Array von Enumerationen|1|✔|Derzeit unterstützen konfigurierbare Registerkarten nur die `team` Bereiche und `groupchat` Bereiche. |
|`sharePointPreviewImage`|Zeichenfolge|2048||Ein relativer Dateipfad zu einem Registerkartenvorschaubild zur Verwendung in SharePoint. Größe 1024 x 768. |
|`supportedSharePointHosts`|Array von Enumerationen|1||Definiert, wie Ihre Registerkarte in SharePoint zur Verfügung gestellt wird. Optionen sind `sharePointFullPage` und `sharePointWebPart` |

## <a name="statictabs"></a>staticTabs

**Optional**

Definiert eine Gruppe von Registerkarten, die standardmäßig "angeheftet" werden können, ohne dass der Benutzer sie manuell hinzufügt. Im Bereich deklarierte statische `personal` Registerkarten werden immer an die persönliche Benutzeroberfläche der App angeheftet. Statische Registerkarten, die im Bereich deklariert `team` sind, werden derzeit nicht unterstützt.

Rendern sie Registerkarten mit adaptiven Karten, indem Sie `contentBotId` sie anstelle `contentUrl` des **staticTabs-Blocks** angeben.

Das Objekt ist ein Array (maximal 16 Elemente) mit allen Elementen des `object` Typs. Dieser Block ist nur für Lösungen erforderlich, die eine statische Registerkartenlösung bereitstellen.


|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`entityId`|String|64 Zeichen|✔|Ein eindeutiger Bezeichner für die Entität, die auf der Registerkarte angezeigt wird.|
|`name`|Zeichenfolge|128 Zeichen|✔|Der Anzeigename der Registerkarte in der Kanalschnittstelle.|
|`contentUrl`|Zeichenfolge|2048 Zeichen|✔|Die https:// URL, die auf die Entitäts-UI verweist, die im Teams Canvas angezeigt werden soll.|
|`contentBotId`|   | | | Die Microsoft Teams App-ID, die für den Bot im Bot Framework-Portal angegeben ist. |
|`websiteUrl`|Zeichenfolge|2048 Zeichen||Die https:// URL, um darauf hinzuweisen, ob sich ein Benutzer für die Anzeige in einem Browser entscheidet.|
|`scopes`|Array von Enumerationen|1|✔|Derzeit unterstützen statische Registerkarten nur den `personal` Bereich, was bedeutet, dass sie nur als Teil der persönlichen Benutzeroberfläche bereitgestellt werden können.|

## <a name="bots"></a>Bots

**Optional**

Definiert eine Bot-Lösung zusammen mit optionalen Informationen wie Standardbefehlseigenschaften.

Das Objekt ist ein Array (maximal 1 Element &mdash; ist derzeit nur ein Bot pro App zulässig) mit allen Elementen des `object` Typs. Dieser Block ist nur für Lösungen erforderlich, die eine Bot-Erfahrung bieten.

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`botId`|String|64 Zeichen|✔|Die eindeutige Microsoft-App-ID für den Bot, wie bei Bot Framework registriert. Dies kann durchaus mit der gesamten [App-ID](#id)übereinstimmen.|
|`needsChannelSelector`|Boolesch|||Beschreibt, ob der Bot einen Benutzerhinweis verwendet, um den Bot einem bestimmten Kanal hinzuzufügen. Standard: `false`|
|`isNotificationOnly`|Boolesch|||Gibt an, ob ein Bot ein unidirektionaler Bot ausschließlich für Benachrichtigungen ist (im Gegensatz zu einem dialogorientierten Bot). Standard: `false`|
|`supportsFiles`|Boolesch|||Gibt an, ob der Bot die Möglichkeit zum Hochladen/Herunterladen von Dateien in persönliche Chats unterstützt. Standard: `false`|
|`scopes`|Array von Enumerationen|3|✔|Gibt an, ob der Bot eine Umgebung im Kontext eines Kanals in einem `team` oder Gruppenchat (`groupchat`) ist, oder aber eine Umgebung einzig für einen bestimmten Benutzer (`personal`). Diese Optionen sind nicht exklusiv.|

### <a name="botscommandlists"></a>bots.commandLists

Eine optionale Liste von Befehlen, die Ihr Bot Benutzern empfehlen kann. Das Objekt ist ein Array (maximal 2 Elemente) mit allen Elementen des `object` Typs. Sie müssen eine separate Befehlsliste für jeden Bereich definieren, den Ihr Bot unterstützt. Weitere Informationen finden Sie unter [Bot-Menüs.](~/bots/how-to/create-a-bot-commands-menu.md)

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`items.scopes`|Array von Enumerationen|3|✔|Gibt den Bereich an, für den die Befehlsliste gültig ist. Mögliche Optionen sind `team`, `personal` und `groupchat`.|
|`items.commands`|Array von Objekten|10|✔|Ein Array von Befehlen, die der Bot unterstützt:<br>`title`: der Bot-Befehlsname (Zeichenfolge, 32).<br>`description`: eine einfache Beschreibung oder ein Beispiel für die Befehlssyntax und ihr Argument (Zeichenfolge, 128).|

## <a name="connectors"></a>Steckverbinder

**Optional**

Der `connectors` Block definiert einen Office 365 Connector für die App.

Das Objekt ist ein Array (maximal 1 Element) mit allen Elementen des Typs `object` . Dieser Block ist nur für Lösungen erforderlich, die einen Connector bereitstellen.

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`configurationUrl`|Zeichenfolge|2048 Zeichen|✔|Die https:// URL, die beim Konfigurieren des Connectors verwendet werden soll.|
|`connectorId`|String|64 Zeichen|✔|Ein eindeutiger Bezeichner für den Connector, der seiner ID im [Connectors Developer Dashboard](https://aka.ms/connectorsdashboard)entspricht.|
|`scopes`|Array von Enumerationen|1|✔|Gibt an, ob der Connector eine Erfahrung im Kontext eines Kanals in einem oder `team` eine Benutzeroberfläche bietet, die auf einen einzelnen Benutzer beschränkt ist ( `personal` ). Derzeit wird nur der `team` Bereich unterstützt.|

## <a name="composeextensions"></a>composeExtensions

**Optional**

Definiert eine Messaging-Erweiterung für die App.

> [!NOTE]
> Der Name des Features wurde im November 2017 von "Erstellerweiterung" in "Messaging-Erweiterung" geändert, aber der Manifestname bleibt unverändert, sodass vorhandene Erweiterungen weiterhin funktionieren.

Das Objekt ist ein Array (maximal 1 Element) mit allen Elementen des Typs `object` . Dieser Block ist nur für Lösungen erforderlich, die eine Messaging-Erweiterung bereitstellen.

|Name| Typ | Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`botId`|Zeichenfolge|64|✔|Die eindeutige Microsoft-App-ID für den Bot, der die Messaging-Erweiterung unterstützt, wie beim Bot Framework registriert. Dies kann durchaus mit der gesamten [App-ID](#id)übereinstimmen.|
|`canUpdateConfiguration`|Boolesch|||Ein Wert, der angibt, ob die Konfiguration einer Messaging-Erweiterung vom Benutzer aktualisiert werden kann. Der Standardwert lautet `false`.|
|`commands`|Array des Objekts|10|✔|Array von Befehlen, die von der Messaging-Erweiterung unterstützt werden|

### <a name="composeextensionscommands"></a>composeExtensions.commands

Ihre Messaging-Erweiterung sollte einen oder mehrere Befehle deklarieren. Jeder Befehl wird in Microsoft Teams als potenzielle Interaktion vom UI-basierten Einstiegspunkt angezeigt. Es gibt maximal 10 Befehle.

Jedes Befehlselement ist ein Objekt mit der folgenden Struktur:

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`id`|String|64 Zeichen|✔|Die ID für den Befehl.|
|`type`|String|64 Zeichen||Typ des Befehls. Eine von `query` oder `action` . Standard: `query`|
|`title`|Zeichenfolge|32 Zeichen|✔|Der benutzerfreundliche Befehlsname.|
|`description`|Zeichenfolge|128 Zeichen||Die Beschreibung, die Benutzern angezeigt wird, um den Zweck dieses Befehls anzugeben.|
|`initialRun`|Boolesch|||Ein boolescher Wert, der angibt, ob der Befehl anfänglich ohne Parameter ausgeführt werden soll. Standard: `false`|
|`context`|Array von Zeichenfolgen|3||Definiert, von wo aus die Nachrichtenerweiterung aufgerufen werden kann. Eine beliebige Kombination von `compose` , `commandBox` , `message` . Der Standardwert ist `["compose", "commandBox"]`|
|`fetchTask`|Boolesch|||Ein boolescher Wert, der angibt, ob das Aufgabenmodul dynamisch abgerufen werden soll.|
|`taskInfo`|Objekt|||Geben Sie das Aufgabenmodul an, das vorab geladen werden soll, wenn Sie einen Messaging-Erweiterungsbefehl verwenden.|
|`taskInfo.title`|Zeichenfolge|64||Titel des ersten Dialogfelds.|
|`taskInfo.width`|Zeichenfolge|||Dialogbreite – entweder eine Zahl in Pixeln oder ein Standardlayout, z. B. "groß", "mittel" oder "klein".|
|`taskInfo.height`|Zeichenfolge|||Dialoghöhe – entweder eine Zahl in Pixeln oder ein Standardlayout, z. B. "groß", "mittel" oder "klein".|
|`taskInfo.url`|Zeichenfolge|||Ursprüngliche Webansichts-URL.|
|`messageHandlers`|Array von Objekten|5 ||Eine Liste von Handlern, mit denen Apps aufgerufen werden können, wenn bestimmte Bedingungen erfüllt sind. Domänen müssen auch in aufgeführt `validDomains` werden.|
|`messageHandlers.type`|Zeichenfolge|||Der Typ des Nachrichtenhandlers. Muss `"link"` sein.|
|`messageHandlers.value.domains`|Array von Zeichenfolgen|||Array von Domänen, für die sich der Linknachrichtenhandler registrieren kann.|
|`parameters`|Array des Objekts|5 |✔|Die Liste der Parameter, die der Befehl verwendet. Minimum: 1; Maximum: 5|
|`parameter.name`|String|64 Zeichen|✔|Der Name des Parameters, wie er im Client angezeigt wird. Dies ist in der Benutzeranforderung enthalten.|
|`parameter.title`|Zeichenfolge|32 Zeichen|✔|Benutzerfreundlicher Titel für den Parameter.|
|`parameter.description`|Zeichenfolge|128 Zeichen||Benutzerfreundliche Zeichenfolge, die den Zweck dieses Parameters beschreibt.|
|`parameter.inputType`|Zeichenfolge|128 Zeichen||Definiert den Typ des Steuerelements, das in einem Aufgabenmodul für angezeigt `fetchTask: true` wird. Einer von `text` , , , , , , `textarea` `number` `date` `time` `toggle` `choiceset` .|
|`parameter.choices`|Array von Objekten|10||Die Auswahloptionen für die `choiceset` . Wird nur verwendet, wenn `parameter.inputType` `choiceset` .|
|`parameter.choices.title`|Zeichenfolge|128||Titel der Wahl.|
|`parameter.choices.value`|Zeichenfolge|512||Value of the choice.|

## <a name="permissions"></a>Berechtigungen

**Optional**

Ein `string` Array, das angibt, welche Berechtigungen die App anfordert, wodurch Endbenutzer wissen, wie die Erweiterung ausgeführt wird. Die folgenden Optionen sind nicht exklusiv:

* `identity`&emsp;Erfordert Benutzeridentitätsinformationen.
* `messageTeamMembers`&emsp;Erfordert die Berechtigung, direkte Nachrichten an Teammitglieder zu senden.

Wenn Sie diese Berechtigungen beim Aktualisieren Ihrer App ändern, wiederholen Ihre Benutzer den Zustimmungsprozess bei der ersten Ausführung der aktualisierten App.

## <a name="devicepermissions"></a>devicePermissions

**Optional** Array von Zeichenfolgen

Gibt die systemeigenen Features auf dem Gerät eines Benutzers an, auf die Ihre App Zugriff anfordern kann. Mögliche Optionen sind:

* `geolocation`
* `media`
* `notifications`
* `midi`
* `openExternal`

## <a name="validdomains"></a>validDomains

**Optional,** außer **erforderlich,** sofern angegeben

Eine Liste der gültigen Domänen, von denen die App erwartet, dass inhalte geladen werden. Domäneneinträge können Platzhalter enthalten, `*.example.com` z. B. . Dies entspricht genau einem Segment der Domäne. wenn Sie übereinstimmen `a.b.example.com` müssen, verwenden Sie `*.*.example.com` . Wenn Ihre Registerkartenkonfiguration oder Inhalts-UI zu einer anderen Domäne als der für die Registerkartenkonfiguration verwendeten navigieren muss, muss diese Domäne hier angegeben werden.

Es ist jedoch **nicht** erforderlich, die Domänen von Identitätsanbietern, die Sie unterstützen möchten, in Ihre App einzuschließen. Um sich beispielsweise mithilfe einer Google-ID zu authentifizieren, ist es erforderlich, zu accounts.google.com umzuleiten, sie sollten jedoch keine accounts.google.com in `validDomains[]` einschließen.

> [!IMPORTANT]
> Fügen Sie keine Domänen hinzu, die sich außerhalb Ihres Steuerelements befinden, entweder direkt oder über Platzhalter. Ist z. `yourapp.onmicrosoft.com` B. gültig, aber `*.onmicrosoft.com` nicht gültig.

Das Objekt ist ein Array mit allen Elementen des Typs `string` .

## <a name="webapplicationinfo"></a>webApplicationInfo

**Optional**

Geben Sie Ihre AAD-App-ID und Graph Informationen an, damit sich Benutzer nahtlos bei Ihrer AAD-App anmelden können.

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`id`|Zeichenfolge|36 Zeichen|✔|AAD-Anwendungs-ID der App. Diese ID muss eine GUID sein.|
|`resource`|Zeichenfolge|2048 Zeichen|✔|Ressourcen-URL der App zum Abrufen des Authentifizierungstokens für SSO.|
|`applicationPermissions`|Array|Maximal 100 Elemente|✔|Ressourcenberechtigungen für die Anwendung.|

## <a name="configurableproperties"></a>configurableProperties

**Optional** – Array

Der `configurableProperties` Block definiert die App-Eigenschaften, die Teams Administratoren anpassen können. Weitere Informationen finden Sie unter Aktivieren der [App-Anpassung.](~/concepts/design/enable-app-customization.md)

> [!NOTE]
> Es muss mindestens eine Eigenschaft definiert werden. Sie können maximal neun Eigenschaften in diesem Block definieren.

Sie können eine der folgenden Eigenschaften definieren:

* `name`: Der Anzeigename der App.
* `shortDescription`: Die kurze Beschreibung der App.
* `longDescription`: Die ausführliche Beschreibung der App.
* `smallImageUrl`: Das Gliederungssymbol der App.
* `largeImageUrl`: Das Farbsymbol der App.
* `accentColor`: Die Farbe, die in Verbindung mit und als Hintergrund für Ihre Gliederungssymbole verwendet werden soll.
* `developerUrl`: Die HTTPS-URL der Website des Entwicklers.
* `privacyUrl`: Die HTTPS-URL der Datenschutzrichtlinie des Entwicklers.
* `termsOfUseUrl`: Die HTTPS-URL der Nutzungsbedingungen des Entwicklers.

## <a name="defaultinstallscope"></a>defaultInstallScope

**Optional** – Zeichenfolge

Gibt den standardmäßig für diese App definierten Installationsumfang an. Der definierte Bereich ist die Option, die auf der Schaltfläche angezeigt wird, wenn ein Benutzer versucht, die App hinzuzufügen. Mögliche Optionen sind:
* `personal`
* `team`
* `groupchat`
* `meetings`

## <a name="defaultgroupcapability"></a>defaultGroupCapability

**Optional** – Objekt

Wenn ein Gruppeninstallationsbereich ausgewählt ist, wird die Standardfunktion definiert, wenn der Benutzer die App installiert. Mögliche Optionen sind:
* `team`
* `groupchat`
* `meetings`
 
|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`team`|string|||Wenn der ausgewählte Installationsbereich ausgewählt `team` ist, gibt dieses Feld die verfügbare Standardfunktion an. Optionen: `tab` `bot` oder `connector` .|
|`groupchat`|Zeichenfolge|||Wenn der ausgewählte Installationsbereich ausgewählt `groupchat` ist, gibt dieses Feld die verfügbare Standardfunktion an. Optionen: `tab` `bot` oder `connector` .|
|`meetings`|Zeichenfolge|||Wenn der ausgewählte Installationsbereich ausgewählt `meetings` ist, gibt dieses Feld die verfügbare Standardfunktion an. Optionen: `tab` `bot` oder `connector` .|
