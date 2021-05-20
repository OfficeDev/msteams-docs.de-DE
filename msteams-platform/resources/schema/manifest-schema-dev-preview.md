---
title: Entwicklervorschau-Manifestschemareferenz
description: Beschreibt das Schema, das vom Manifest für Microsoft Teams unterstützt wird
ms.topic: reference
keywords: Teams-Manifestschema Entwicklervorschau
localization_priority: Normal
ms.date: 05/20/2019
ms.openlocfilehash: b52d52f96312dc2978844b07a0f7ebb1d817166d
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566705"
---
# <a name="developer-preview-manifest-schema-for-microsoft-teams"></a>Entwicklervorschaumanifestschema für Microsoft Teams

> [!NOTE]
> Informationen zum Programm und zur Teilnahme an dem Programm finden Sie in [der Entwicklervorschau.](~/resources/dev-preview/developer-preview-intro.md)
> Wenn Sie die Entwicklervorschau nicht verwenden, sollten Sie diese Version des Manifests nicht verwenden. Siehe [Referenz: Manifestschema für Microsoft Teams](~/resources/schema/manifest-schema.md) für die öffentliche Version des Manifests.

Das Microsoft Teams-Manifest beschreibt, wie sich die App in das Microsoft Teams Produkt integriert. Das Manifest muss dem Schema entsprechen, das unter gehostet [`https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json`](https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json) wird.

Weitere Informationen zu den verfügbaren Funktionen finden Sie unter: [Funktionen in der Öffentlichen Entwicklervorschau für Microsoft Teams](~/resources/dev-preview/developer-preview-features.md).

## <a name="sample-full-manifest"></a>Beispiel-Vollmanifest

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
  ],
   "configurableProperties": [
     "name",
     "shortDescription",
     "longDescription",
     "smallImageUrl", 
     "largeImageUrl", 
     "accentColor",
     "websiteUrl",
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

Die https:// URL, die auf das JSON-Schema für das Manifest verweist.

## <a name="manifestversion"></a>manifestVersion

**Erforderlich** &ndash; Schnur

Die Version des Manifestschemas, das dieses Manifest verwendet. Es sollte "devPreview" sein.

## <a name="version"></a>Version

**Erforderlich** &ndash; Schnur

Die Version der jeweiligen App. Wenn Sie etwas in Ihrem Manifest aktualisieren, muss die Version ebenfalls erhöht werden. Auf diese Weise wird bei der Installation des neuen Manifests das vorhandene überschrieben, und der Benutzer erhält die neue Funktionalität. Wenn diese App an den Store übermittelt wurde, muss das neue Manifest erneut übermittelt und erneut überprüft werden. Dann erhalten Benutzer dieser App das neue aktualisierte Manifest automatisch in wenigen Stunden, nachdem es genehmigt wurde.

Wenn sich die angeforderten Berechtigungen der App ändern, werden Benutzer aufgefordert, ein Upgrade durchzuführen und die App erneut zuzustimmen.

Diese Versionszeichenfolge muss dem [Semver-Standard](http://semver.org/) (MAJOR. kleiner. PATCH).

## <a name="id"></a>id

**Erforderlich** &ndash; Microsoft-App-ID

Der eindeutige von Microsoft generierte Bezeichner für diese App. Wenn Sie einen Bot über die Microsoft Bot Framework registriert haben oder sich die Web-App Ihres Tabs bereits bei Microsoft anmeldet, sollten Sie bereits über eine ID verfügen und diese hier eingeben. Andernfalls sollten Sie eine neue ID im Microsoft Application Registration Portal ([Meine Anwendungen](https://apps.dev.microsoft.com)) generieren, hier eingeben und dann wiederverwenden, wenn Sie einen [Bot hinzufügen.](~/bots/how-to/create-a-bot-for-teams.md)

## <a name="packagename"></a>Packagename

**Erforderlich** &ndash; Schnur

Ein eindeutiger Bezeichner für diese App in umgekehrter Domänennotation; z. B. com.example.myapp.

## <a name="developer"></a>developer

**Required**

Gibt Informationen zu Ihrem Unternehmen an. Bei Apps, die an AppSource übermittelt werden (früher Office Store), müssen diese Werte mit den Informationen in Ihrem AppSource-Eintrag übereinstimmen.

|Name| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|
|`name`|32 Zeichen|✔|Der Anzeigename für den Entwickler.|
|`websiteUrl`|2048 Zeichen|✔|Die https:// URL auf die Website des Entwicklers. Dieser Link sollte Benutzer zu Ihrem Unternehmen oder Ihrer produktspezifischen Zielseite führen.|
|`privacyUrl`|2048 Zeichen|✔|Die https:// URL zur Datenschutzrichtlinie des Entwicklers.|
|`termsOfUseUrl`|2048 Zeichen|✔|Die https:// URL zu den Nutzungsbedingungen des Entwicklers.|
|`mpnId`|10 Zeichen|✔|**Optional** Die Microsoft Partner Network ID, die die Partnerorganisation identifiziert, die die App erstellen.|

## <a name="localizationinfo"></a>lokalisierungInfo

**Optional**

Ermöglicht die Angabe einer Standardsprache sowie Zeiger auf zusätzliche Sprachdateien. Siehe [Lokalisierung](~/concepts/build-and-test/apps-localization.md).

|Name| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|
|`defaultLanguageTag`|4 Zeichen|✔|Das Sprachtag der Zeichenfolgen in dieser Manifestdatei der obersten Ebene.|

### <a name="localizationinfoadditionallanguages"></a>lokalisierungInfo.additionalSprachen

Ein Array von Objekten, die zusätzliche Sprachübersetzungen angeben.

|Name| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|
|`languageTag`|4 Zeichen|✔|Das Sprachtag der Zeichenfolgen in der bereitgestellten Datei.|
|`file`|4 Zeichen|✔|Ein relativer Dateipfad zu einer JSon-Datei, die die übersetzten Zeichenfolgen enthält.|

## <a name="name"></a>name

**Required**

Der Name Ihrer App-Erfahrung, der Benutzern im Teams angezeigt wird. Bei Apps, die an AppSource gesendet werden, müssen diese Werte mit den Informationen in Ihrem AppSource-Eintrag übereinstimmen. Die Werte von `short` und sollten nicht die gleichen `full` sein.

|Name| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|
|`short`|30 Zeichen|✔|Der kurze Anzeigename für die App.|
|`full`|100 Zeichen||Der vollständige Name der App, der verwendet wird, wenn der vollständige App-Name 30 Zeichen überschreitet.|

## <a name="description"></a>description

**Required**

Beschreibt Ihre App für Benutzer. Bei Apps, die an AppSource gesendet werden, müssen diese Werte mit den Informationen in Ihrem AppSource-Eintrag übereinstimmen.

Stellen Sie sicher, dass Ihre Beschreibung Ihre Erfahrung genau beschreibt und Informationen bereitstellt, die potenziellen Kunden helfen, ihre Erfahrung zu verstehen. Sie sollten auch in der vollständigen Beschreibung notieren, ob ein externes Konto für die Verwendung erforderlich ist. Die Werte von `short` und sollten nicht die gleichen `full` sein.  Ihre Kurzbeschreibung darf nicht innerhalb der langen Beschreibung wiederholt werden und darf keinen anderen App-Namen enthalten.

|Name| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|
|`short`|80 Zeichen|✔|Eine kurze Beschreibung Ihrer App-Erfahrung, die verwendet wird, wenn der Speicherplatz begrenzt ist.|
|`full`|4000 Zeichen|✔|Die vollständige Beschreibung Ihrer App.|

## <a name="icons"></a>Symbole

**Required**

Symbole, die in der Teams-App verwendet werden. Die Symboldateien müssen als Teil des Upload-Pakets enthalten sein.

|Name| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|
|`outline`|2048 Zeichen|✔|Ein relativer Dateipfad zu einem transparenten 32x32 PNG-Umrisssymbol.|
|`color`|2048 Zeichen|✔|Ein relativer Dateipfad zu einem 192x192 PNG-Symbol in voller Farbe.|

## <a name="accentcolor"></a>accentFarbe

**Erforderlich** &ndash; Schnur

Eine Farbe, die in Verbindung mit und als Hintergrund für Ihre Gliederungssymbole verwendet werden soll.

Der Wert muss ein gültiger HTML-Farbcode sein, der z. B. mit ''' `#4464ee` beginnt.

## <a name="configurabletabs"></a>konfigurierbareTabs

**Optional**

Wird verwendet, wenn Ihre App-Erfahrung über eine Teamkanal-Registerkarte verfügt, die eine zusätzliche Konfiguration erfordert, bevor sie hinzugefügt wird. Konfigurierbare Registerkarten werden nur im Teamsbereich unterstützt, und derzeit wird nur eine Registerkarte pro App unterstützt.

Das Objekt ist ein Array mit allen Elementen des Typs `object` . Dieser Block ist nur für Lösungen erforderlich, die eine konfigurierbare Kanalregisterkartenlösung bereitstellen.

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`configurationUrl`|Zeichenfolge|2048 Zeichen|✔|Die https:// URL, die beim Konfigurieren der Registerkarte verwendet werden soll.|
|`canUpdateConfiguration`|Boolesch|||Ein Wert, der angibt, ob eine Instanz der Registerkartenkonfiguration vom Benutzer nach der Erstellung aktualisiert werden kann. Standard: `true`|
|`scopes`|Array von Enumerationen|1|✔|Derzeit unterstützen konfigurierbare Registerkarten nur die `team` `groupchat` und-Bereiche. |
|`sharePointPreviewImage`|Zeichenfolge|2048||Ein relativer Dateipfad zu einem Registerkartenvorschaubild zur Verwendung in SharePoint. Größe 1024x768. |
|`supportedSharePointHosts`|Array von Enumerationen|1||Definiert, wie Ihre Registerkarte in SharePoint zur Verfügung gestellt wird. Optionen sind `sharePointFullPage` und `sharePointWebPart` |

## <a name="statictabs"></a>staticTabs

**Optional**

Definiert eine Reihe von Registerkarten, die standardmäßig "angeheftet" werden können, ohne dass der Benutzer sie manuell hinzufügt. Statische Registerkarten, die im `personal` Gültigkeitsbereich deklariert sind, werden immer an die persönliche Erfahrung der App angeheftet. Statische Registerkarten, die im Bereich deklariert `team` sind, werden derzeit nicht unterstützt.

Das Objekt ist ein Array (maximal 16 Elemente) mit allen Elementen des Typs `object` . Dieser Block ist nur für Lösungen erforderlich, die eine statische Registerkartenlösung bereitstellen.

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`entityId`|String|64 Zeichen|✔|Ein eindeutiger Bezeichner für die Entität, die auf der Registerkarte angezeigt wird.|
|`name`|Zeichenfolge|128 Zeichen|✔|Der Anzeigename der Registerkarte in der Kanalschnittstelle.|
|`contentUrl`|Zeichenfolge|2048 Zeichen|✔|Die https:// URL, die auf die Entitätsbenutzeroberfläche verweist, die im Teams-Canvas angezeigt werden soll.|
|`websiteUrl`|Zeichenfolge|2048 Zeichen||Die https:// URL, auf die sie zeigen sollen, wenn ein Benutzer sich für die Anzeige in einem Browser entscheidet.|
|`scopes`|Array von Enumerationen|1|✔|Derzeit unterstützen statische Registerkarten nur den `personal` Bereich, d. h., er kann nur als Teil der persönlichen Erfahrung bereitgestellt werden.|

## <a name="bots"></a>Bots

**Optional**

Definiert eine Bot-Lösung zusammen mit optionalen Informationen wie Standardbefehlseigenschaften.

Das Objekt ist ein Array (maximal nur 1 Element &mdash; ist derzeit nur ein Bot pro App erlaubt) mit allen Elementen des Typs `object` . Dieser Block ist nur für Lösungen erforderlich, die ein Bot-Erlebnis bieten.

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`botId`|String|64 Zeichen|✔|Die eindeutige Microsoft-App-ID für den Bot, wie bei Bot Framework registriert. Dies kann durchaus mit der gesamten [App-ID](#id)identisch sein.|
|`needsChannelSelector`|Boolesch|||Beschreibt, ob der Bot einen Benutzerhinweis verwendet, um den Bot einem bestimmten Kanal hinzuzufügen. Standard: `false`|
|`isNotificationOnly`|Boolesch|||Gibt an, ob ein Bot ein unidirektionaler Bot ausschließlich für Benachrichtigungen ist (im Gegensatz zu einem dialogorientierten Bot). Standard: `false`|
|`supportsFiles`|Boolesch|||Gibt an, ob der Bot die Möglichkeit zum Hochladen/Herunterladen von Dateien in persönliche Chats unterstützt. Standard: `false`|
|`scopes`|Array von Enumerationen|3|✔|Gibt an, ob der Bot eine Umgebung im Kontext eines Kanals in einem `team` oder Gruppenchat (`groupchat`) ist, oder aber eine Umgebung einzig für einen bestimmten Benutzer (`personal`). Diese Optionen sind nicht exklusiv.|

### <a name="botscommandlists"></a>bots.commandListen

Eine optionale Liste von Befehlen, die Ihr Bot Benutzern empfehlen kann. Das Objekt ist ein Array (maximal 2 Elemente) mit allen Elementen des `object` Typs; Sie müssen eine separate Befehlsliste für jeden Bereich definieren, den Ihr Bot unterstützt. Weitere Informationen finden Sie unter [Bot-Menüs](~/bots/how-to/create-a-bot-commands-menu.md).

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
|`connectorId`|String|64 Zeichen|✔|Ein eindeutiger Bezeichner für den Connector, der mit seiner ID im [Connectors Developer Dashboard](https://aka.ms/connectorsdashboard)übereinstimmt.|
|`scopes`|Array von Enumerationen|1|✔|Gibt an, ob der Connector eine Erfahrung im Kontext eines Kanals in einem bietet, oder eine Erfahrung, die nur für einen einzelnen Benutzer ( ) `team` gilt. `personal` Derzeit wird nur der `team` Bereich unterstützt.|

## <a name="composeextensions"></a>composeExtensions

**Optional**

Definiert eine Messagingerweiterung für die App.

> [!NOTE]
> Der Name des Features wurde im November 2017 von "Komponenerweiterung" in "Messaging-Erweiterung" geändert, aber der Manifestname bleibt derselbe, sodass vorhandene Erweiterungen weiterhin funktionieren.

Das Objekt ist ein Array (maximal 1 Element) mit allen Elementen des Typs `object` . Dieser Block ist nur für Lösungen erforderlich, die eine Messagingerweiterung bereitstellen.

|Name| Typ | Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`botId`|Zeichenfolge|64|✔|Die eindeutige Microsoft-App-ID für den Bot, die die Messagingerweiterung unterstützt, wie sie im Bot Framework registriert ist. Dies kann durchaus mit der gesamten [App-ID](#id)identisch sein.|
|`canUpdateConfiguration`|Boolesch|||Ein Wert, der angibt, ob die Konfiguration einer Messagingerweiterung vom Benutzer aktualisiert werden kann. Der Standardwert lautet `false`.|
|`commands`|Array des Objekts|10|✔|Array von Befehlen, die von der Messagingerweiterung unterstützt werden|

### <a name="composeextensionscommands"></a>composeExtensions.commands

Ihre Messagingerweiterung sollte einen oder mehrere Befehle deklarieren. Jeder Befehl wird in Microsoft Teams als potenzielle Interaktion vom UI-basierten Einstiegspunkt angezeigt. Es gibt maximal 10 Befehle.

Jedes Befehlselement ist ein Objekt mit der folgenden Struktur:

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`id`|String|64 Zeichen|✔|Die ID für den Befehl.|
|`type`|String|64 Zeichen||Typ des Befehls. Einer von `query` oder `action` . Standard: `query`|
|`title`|Zeichenfolge|32 Zeichen|✔|Der benutzerfreundliche Befehlsname.|
|`description`|Zeichenfolge|128 Zeichen||Die Beschreibung, die Benutzern angezeigt wird, um den Zweck dieses Befehls anzugeben.|
|`initialRun`|Boolesch|||Ein boolescher Wert, der angibt, ob der Befehl zunächst ohne Parameter ausgeführt werden soll. Standard: `false`|
|`context`|Array von Strings|3||Definiert, von wo aus die Nachrichtenerweiterung aufgerufen werden kann. Jede Beliebige Kombination von `compose` , `commandBox` . `message` Standard ist `["compose", "commandBox"]`|
|`fetchTask`|Boolesch|||Ein boolescher Wert, der angibt, ob das Taskmodul dynamisch abgerufen werden soll.|
|`taskInfo`|Object|||Geben Sie den Taskmodul an, der vorab geladen werden soll, wenn ein Messagingerweiterungsbefehl verwendet wird.|
|`taskInfo.title`|Zeichenfolge|64||Erster Dialogtitel.|
|`taskInfo.width`|Zeichenfolge|||Dialogbreite - entweder eine Zahl in Pixel oder ein Standardlayout wie 'large', 'medium' oder 'small'.|
|`taskInfo.height`|Zeichenfolge|||Dialoghöhe - entweder eine Zahl in Pixel oder ein Standardlayout wie 'large', 'medium' oder 'small'.|
|`taskInfo.url`|Zeichenfolge|||Erste Webview-URL.|
|`messageHandlers`|Array von Objekten|5 ||Eine Liste von Handlern, mit denen Apps aufgerufen werden können, wenn bestimmte Bedingungen erfüllt sind. Domänen müssen auch in aufgeführt `validDomains` werden.|
|`messageHandlers.type`|Zeichenfolge|||Der Typ des Nachrichtenhandlers. Muss `"link"` sein.|
|`messageHandlers.value.domains`|Array von Strings|||Array von Domänen, für die der Linknachrichtenhandler registrieren kann.|
|`parameters`|Array des Objekts|5 |✔|Die Liste der Parameter, die der Befehl verwendet. Minimum: 1; maximal: 5|
|`parameter.name`|String|64 Zeichen|✔|Der Name des Parameters, wie er im Client angezeigt wird. Dies ist in der Benutzeranforderung enthalten.|
|`parameter.title`|Zeichenfolge|32 Zeichen|✔|Benutzerfreundlicher Titel für den Parameter.|
|`parameter.description`|Zeichenfolge|128 Zeichen||Benutzerfreundliche Zeichenfolge, die den Zweck dieses Parameters beschreibt.|
|`parameter.inputType`|Zeichenfolge|128 Zeichen||Definiert den Typ des Steuerelements, das in einem Taskmodul für angezeigt `fetchTask: true` wird. Einer von `text` , , , , , , `textarea` `number` `date` `time` `toggle` `choiceset` .|
|`parameter.choices`|Array von Objekten|10||Die Auswahloptionen für die `choiceset` . Nur verwenden, wenn `parameter.inputType` es sich um `choiceset` .|
|`parameter.choices.title`|Zeichenfolge|128||Titel der Wahl.|
|`parameter.choices.value`|Zeichenfolge|512||Value of the choice.|

## <a name="permissions"></a>Berechtigungen

**Optional**

Ein Array, dessen `string` Berechtigung die App anfordert, sodass Endbenutzer wissen, wie die Erweiterung ausgeführt wird. Die folgenden Optionen sind nicht exklusiv:

* `identity`&emsp;Erfordert Benutzeridentitätsinformationen.
* `messageTeamMembers`&emsp;Erfordert die Berechtigung zum Senden direkter Nachrichten an Teammitglieder.

Wenn Sie diese Berechtigungen beim Aktualisieren Ihrer App ändern, werden die Benutzer den Zustimmungsprozess beim ersten Ausführen der aktualisierten App wiederholen.

## <a name="devicepermissions"></a>devicePermissions

**Optional** Array von Strings

Gibt die systemeigenen Features auf dem Gerät eines Benutzers an, auf die Ihre App möglicherweise Zugriff anfordert. Mögliche Optionen sind:

* `geolocation`
* `media`
* `notifications`
* `midi`
* `openExternal`

## <a name="validdomains"></a>validDomains

**Optional**, außer **Erforderlich,** sofern angegeben

Eine Liste gültiger Domänen, von denen die App erwartet, dass Inhalte geladen werden. Domänenlisten können Platzhalter enthalten, z. `*.example.com` B. . Dies entspricht genau einem Segment der Domäne; wenn Sie übereinstimmen müssen, `a.b.example.com` verwenden Sie `*.*.example.com` . Wenn Ihre Registerkartenkonfiguration oder Inhaltsbenutzeroberfläche zu einer anderen Domäne als der für die Registerkartenkonfiguration verwendenden Domäne navigieren muss, muss diese Domäne hier angegeben werden.

Es ist jedoch **nicht** erforderlich, die Domänen von Identitätsanbietern, die Sie unterstützen möchten, in Ihre App aufzunehmen. Um sich beispielsweise mit einer Google-ID zu authentifizieren, ist es erforderlich, zu accounts.google.com umzuleiten, aber Sie sollten accounts.google.com nicht in `validDomains[]` .

> [!IMPORTANT]
> Fügen Sie keine Domänen hinzu, die sich außerhalb Ihrer Kontrolle befinden, weder direkt noch über Platzhalter. Zum Beispiel `yourapp.onmicrosoft.com` ist gültig, aber `*.onmicrosoft.com` nicht gültig.

Das Objekt ist ein Array mit allen Elementen des Typs `string` .

## <a name="webapplicationinfo"></a>webApplicationInfo

**Optional**

Geben Sie Ihre AAD-App-ID und Graph Informationen an, damit sich Benutzer nahtlos bei Ihrer AAD-App anmelden können.

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`id`|Zeichenfolge|36 Zeichen|✔|AAD-Anwendungs-ID der App. Diese ID muss eine GUID sein.|
|`resource`|Zeichenfolge|2048 Zeichen|✔|Ressourcen-URL der App zum Abrufen von Authentifizierungstoken für SSO.|

## <a name="configurableproperties"></a>konfigurierbareEigenschaften

**Optional** - Array

Der `configurableProperties` Block definiert die App-Eigenschaften, die Teams Administrator anpassen kann. Weitere Informationen finden Sie unter [Anpassen von Apps in Microsoft Teams](/MicrosoftTeams/customize-apps).

> [!NOTE]
> Es muss mindestens eine Eigenschaft definiert werden. Sie können maximal neun Eigenschaften in diesem Block definieren.
> Als bewährte Methode müssen Sie Anpassungsrichtlinien für App-Benutzer und -Kunden bereitstellen, die Sie beim Anpassen Ihrer App befolgen müssen. 

Sie können eine der folgenden Eigenschaften definieren:
* `name`: Ermöglicht es Administratoren, den Anzeigenamen der App zu ändern.
* `shortDescription`: Ermöglicht es Admin, die Kurzbeschreibung der App zu ändern.
* `longDescription`: Ermöglicht es Administratoren, die detaillierte Beschreibung der App zu ändern.
* `smallImageUrl`: Es ist die `outline` Eigenschaft im Block des `icons` Manifests.
* `largeImageUrl`: Es ist die `color` Eigenschaft im Block des `icons` Manifests.
* `accentColor`: Es ist die Farbe, die in Verbindung mit und als Hintergrund für Ihre Gliederungssymbole verwendet werden soll.
* `websiteUrl`: Es ist die https:// URL auf der Website des Entwicklers.
* `privacyUrl`: Es ist die https:// URL zur Datenschutzrichtlinie des Entwicklers.
* `termsOfUseUrl`: Es ist die https:// URL zu den Nutzungsbedingungen des Entwicklers.

## <a name="defaultinstallscope"></a>defaultInstallScope

**Optional** - String

Gibt den standardmäßig für diese App definierten Installationsbereich an. Der definierte Bereich ist die Option, die auf der Schaltfläche angezeigt wird, wenn ein Benutzer versucht, die App hinzuzufügen. Mögliche Optionen sind:
* `personal`
* `team`
* `groupchat`
* `meetings`

## <a name="defaultgroupcapability"></a>defaultGroupCapability

**Optional** - Objekt

Wenn ein Gruppeninstallationsbereich ausgewählt ist, definiert er die Standardfunktion, wenn der Benutzer die App installiert. Mögliche Optionen sind:
* `team`
* `groupchat`
* `meetings`
 
|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`team`|string|||Wenn der ausgewählte Installationsbereich `team` ist , gibt dieses Feld die verfügbare Standardfunktion an. Optionen: `tab` `bot` , , oder `connector` .|
|`groupchat`|Zeichenfolge|||Wenn der ausgewählte Installationsbereich `groupchat` ist , gibt dieses Feld die verfügbare Standardfunktion an. Optionen: `tab` `bot` , , oder `connector` .|
|`meetings`|Zeichenfolge|||Wenn der ausgewählte Installationsbereich `meetings` ist , gibt dieses Feld die verfügbare Standardfunktion an. Optionen: `tab` `bot` , , oder `connector` .|

