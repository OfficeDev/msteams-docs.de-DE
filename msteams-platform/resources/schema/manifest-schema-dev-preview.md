---
title: Developer Preview Manifestschemareferenz
description: Beschreibt das schema, das vom Manifest für die Microsoft Teams
ms.topic: reference
keywords: teams manifest schema Developer Preview
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
> Weitere [Developer Preview](~/resources/dev-preview/developer-preview-intro.md) zum Programm und zur Teilnahme finden Sie unter Developer Preview.
> Wenn Sie die Entwicklervorschau nicht verwenden, sollten Sie diese Version des Manifests nicht verwenden. Informationen [zur öffentlichen Version des Manifests finden Microsoft Teams Referenz:](~/resources/schema/manifest-schema.md) Manifestschema.

Das Microsoft Teams-Manifest beschreibt, wie die App in das Microsoft Teams integriert wird. Ihr Manifest muss dem schema entsprechen, das unter gehostet [`https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json`](https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json) wird.

Weitere Informationen zu den verfügbaren Features finden Sie unter Features [in the Public Developer Preview for Microsoft Teams](~/resources/dev-preview/developer-preview-features.md).

## <a name="sample-full-manifest"></a>Beispiel für vollständiges Manifest

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

*Optional, aber empfohlen* &ndash; Zeichenfolge

Die https://-URL, die auf das JSON-Schema für das Manifest verweist.

## <a name="manifestversion"></a>manifestVersion

**Erforderlich** &ndash; Zeichenfolge

Die Version des Manifestschemas, das dieses Manifest verwendet. Es sollte "devPreview" sein.

## <a name="version"></a>Version

**Erforderlich** &ndash; Zeichenfolge

Die Version der spezifischen App. Wenn Sie etwas in Ihrem Manifest aktualisieren, muss auch die Version erhöht werden. Auf diese Weise wird bei der Installation des neuen Manifests das vorhandene überschrieben, und der Benutzer erhält die neue Funktionalität. Wenn diese App an den Store übermittelt wurde, muss das neue Manifest erneut übermittelt und erneut überprüft werden. Anschließend erhalten Benutzer dieser App das neue aktualisierte Manifest automatisch in ein paar Stunden, nachdem es genehmigt wurde.

Wenn sich die Von der App angeforderten Berechtigungen ändern, werden Die Benutzer aufgefordert, ein Upgrade zu starten und der App erneut zu zustimmen.

Diese Versionszeichenfolge muss dem [semver-Standard](http://semver.org/) (MAJOR. MINOR. PATCH).

## <a name="id"></a>id

**Erforderlich** &ndash; Microsoft-App-ID

Der eindeutige von Microsoft generierte Bezeichner für diese App. Wenn Sie einen Bot über das Microsoft Bot Framework registriert haben oder sich die Web-App Ihrer Registerkarte bereits bei Microsoft angemeldet hat, sollten Sie bereits über eine ID verfügen und ihn hier eingeben. Andernfalls sollten Sie eine neue ID im Microsoft Application Registration Portal ([Meine](https://apps.dev.microsoft.com)Anwendungen ) generieren, sie hier eingeben und dann wiederverwenden, wenn Sie [einen Bot hinzufügen.](~/bots/how-to/create-a-bot-for-teams.md)

## <a name="packagename"></a>packageName

**Erforderlich** &ndash; Zeichenfolge

Ein eindeutiger Bezeichner für diese App in umgekehrter Domänen-Notation; z. B. com.example.myapp.

## <a name="developer"></a>developer

**Required**

Gibt Informationen zu Ihrem Unternehmen an. Für apps submitted to AppSource (formerly Office Store), these values must match the information in your AppSource entry.

|Name| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|
|`name`|32 Zeichen|✔|Der Anzeigename für den Entwickler.|
|`websiteUrl`|2048 Zeichen|✔|Die https://-URL zur Website des Entwicklers. Dieser Link sollte Benutzer zu Ihrer unternehmens- oder produktspezifischen Angebotsseite gelangen.|
|`privacyUrl`|2048 Zeichen|✔|Die https:// url to the developer's privacy policy.|
|`termsOfUseUrl`|2048 Zeichen|✔|Die https:// URL zu den Nutzungsbedingungen des Entwicklers.|
|`mpnId`|10 Zeichen|✔|**Optional** Die Microsoft Partner Network ID, die die Partnerorganisation identifiziert, die die App erstellt.|

## <a name="localizationinfo"></a>localizationInfo

**Optional**

Ermöglicht die Angabe einer Standardsprache sowie Zeiger auf zusätzliche Sprachdateien. Weitere [Informationen finden Sie unter Lokalisierung](~/concepts/build-and-test/apps-localization.md).

|Name| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|
|`defaultLanguageTag`|4 Zeichen|✔|Das Sprachtag der Zeichenfolgen in dieser Manifestdatei auf oberster Ebene.|

### <a name="localizationinfoadditionallanguages"></a>localizationInfo.additionalLanguages

Ein Array von Objekten, die zusätzliche Sprachübersetzungen angeben.

|Name| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|
|`languageTag`|4 Zeichen|✔|Das Sprachtag der Zeichenfolgen in der bereitgestellten Datei.|
|`file`|4 Zeichen|✔|Ein relativer Dateipfad zu einer .json-Datei, die die übersetzten Zeichenfolgen enthält.|

## <a name="name"></a>name

**Required**

Der Name Ihrer App-Erfahrung, der Benutzern in der Teams angezeigt wird. Für apps submitted to AppSource, these values must match the information in your AppSource entry. Die Werte von `short` und sollten nicht identisch `full` sein.

|Name| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|
|`short`|30 Zeichen|✔|Der kurze Anzeigename für die App.|
|`full`|100 Zeichen||Der vollständige Name der App, der verwendet wird, wenn der vollständige Name der App 30 Zeichen überschreitet.|

## <a name="description"></a>description

**Required**

Beschreibt Ihre App für Benutzer. Für apps submitted to AppSource, these values must match the information in your AppSource entry.

Stellen Sie sicher, dass Ihre Beschreibung Ihre Erfahrung genau beschreibt und Informationen enthält, mit deren Hilfe potenzielle Kunden besser verstehen können, was Ihre Erfahrung bedeutet. Beachten Sie auch in der vollständigen Beschreibung, ob ein externes Konto für die Verwendung erforderlich ist. Die Werte von `short` und sollten nicht identisch `full` sein.  Ihre kurze Beschreibung darf nicht innerhalb der langen Beschreibung wiederholt werden und darf keinen anderen App-Namen enthalten.

|Name| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|
|`short`|80 Zeichen|✔|Eine kurze Beschreibung Ihrer App-Erfahrung, die bei begrenztem Speicherplatz verwendet wird.|
|`full`|4000 Zeichen|✔|Die vollständige Beschreibung Ihrer App.|

## <a name="icons"></a>Symbole

**Required**

Symbole, die innerhalb der Teams werden. Die Symboldateien müssen als Teil des Uploadpakets enthalten sein.

|Name| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|
|`outline`|2048 Zeichen|✔|Ein relativer Dateipfad zu einem transparenten 32 x 32 PNG-Gliederungssymbol.|
|`color`|2048 Zeichen|✔|Ein relativer Dateipfad zu einem vollfarbigen 192 x 192-PNG-Symbol.|

## <a name="accentcolor"></a>accentColor

**Erforderlich** &ndash; Zeichenfolge

Eine Farbe, die in Verbindung mit und als Hintergrund für Ihre Gliederungssymbole verwendet werden soll.

Der Wert muss ein gültiger #A0 sein, der mit "#" beginnt, z. B. `#4464ee` .

## <a name="configurabletabs"></a>configurableTabs

**Optional**

Wird verwendet, wenn Ihre App über eine Registerkartenerfahrung im Teamkanal verfügt, die eine zusätzliche Konfiguration erfordert, bevor sie hinzugefügt wird. Konfigurierbare Registerkarten werden nur im Bereich Teams unterstützt, und derzeit wird nur eine Registerkarte pro App unterstützt.

Das Objekt ist ein Array mit allen Elementen des Typs `object` . Dieser Block ist nur für Lösungen erforderlich, die eine konfigurierbare Kanalregisterkartenlösung bereitstellen.

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`configurationUrl`|String|2048 Zeichen|✔|Die https:// URL, die beim Konfigurieren der Registerkarte verwendet werden soll.|
|`canUpdateConfiguration`|Boolesch|||Ein Wert, der angibt, ob eine Instanz der Registerkartenkonfiguration vom Benutzer nach der Erstellung aktualisiert werden kann. Standard: `true`|
|`scopes`|Array von Enumerationen|1|✔|Derzeit unterstützen konfigurierbare Registerkarten nur die `team` Bereiche `groupchat` und. |
|`sharePointPreviewImage`|String|2048||Ein relativer Dateipfad zu einem Registerkartenvorschaubild zur Verwendung in SharePoint. Größe 1024 x 768. |
|`supportedSharePointHosts`|Array von Enumerationen|1||Definiert, wie Ihre Registerkarte in der SharePoint. Optionen sind `sharePointFullPage` und `sharePointWebPart` |

## <a name="statictabs"></a>staticTabs

**Optional**

Definiert eine Reihe von Registerkarten, die standardmäßig angeheftet werden können, ohne dass der Benutzer sie manuell hinzufügungen muss. Statische Registerkarten, die im Bereich deklariert sind, werden immer an die persönliche Be benutzererfahrung `personal` der App angeheftet. Statische Registerkarten, die im Bereich `team` deklariert sind, werden derzeit nicht unterstützt.

Das Objekt ist ein Array (maximal 16 Elemente) mit allen Elementen des Typs `object` . Dieser Block ist nur für Lösungen erforderlich, die eine statische Registerkartenlösung bereitstellen.

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`entityId`|String|64 Zeichen|✔|Ein eindeutiger Bezeichner für die Entität, die auf der Registerkarte angezeigt wird.|
|`name`|String|128 Zeichen|✔|Der Anzeigename der Registerkarte in der Kanalschnittstelle.|
|`contentUrl`|String|2048 Zeichen|✔|Die https://-URL, die auf die Entitätsbenutzeroberfläche verweist, die im Zeichenbereich Teams werden soll.|
|`websiteUrl`|String|2048 Zeichen||Die https:// URL, auf die verweisen soll, wenn sich ein Benutzer für die Anzeige in einem Browser entscheidet.|
|`scopes`|Array von Enumerationen|1|✔|Derzeit unterstützen statische Registerkarten nur den Bereich, d. h., er kann nur als Teil der `personal` persönlichen Erfahrung bereitgestellt werden.|

## <a name="bots"></a>Bots

**Optional**

Definiert eine Botlösung zusammen mit optionalen Informationen, z. B. Standardbefehlseigenschaften.

Das Objekt ist ein Array (maximal 1 Element ist derzeit nur ein Bot pro App zulässig) mit allen Elementen &mdash; des Typs `object` . Dieser Block ist nur für Lösungen erforderlich, die eine Boterfahrung bieten.

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`botId`|String|64 Zeichen|✔|Die eindeutige Microsoft-App-ID für den Bot, wie bei Bot Framework registriert. Dies kann mit der allgemeinen [App-ID identisch sein.](#id)|
|`needsChannelSelector`|Boolesch|||Beschreibt, ob der Bot einen Benutzerhinweis verwendet, um den Bot einem bestimmten Kanal hinzuzufügen. Standard: `false`|
|`isNotificationOnly`|Boolesch|||Gibt an, ob ein Bot ein unidirektionaler Bot ausschließlich für Benachrichtigungen ist (im Gegensatz zu einem dialogorientierten Bot). Standard: `false`|
|`supportsFiles`|Boolesch|||Gibt an, ob der Bot die Möglichkeit zum Hochladen/Herunterladen von Dateien in persönliche Chats unterstützt. Standard: `false`|
|`scopes`|Array von Enumerationen|3|✔|Gibt an, ob der Bot eine Umgebung im Kontext eines Kanals in einem `team` oder Gruppenchat (`groupchat`) ist, oder aber eine Umgebung einzig für einen bestimmten Benutzer (`personal`). Diese Optionen sind nicht exklusiv.|

### <a name="botscommandlists"></a>bots.commandLists

Eine optionale Liste von Befehlen, die Ihr Bot Benutzern empfehlen kann. Das Objekt ist ein Array (maximal 2 Elemente) mit allen Elementen des Typs. Sie müssen eine separate Befehlsliste für jeden Bereich definieren, den `object` Ihr Bot unterstützt. Weitere Informationen finden Sie unter [Bot-Menüs](~/bots/how-to/create-a-bot-commands-menu.md).

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`items.scopes`|Array von Enumerationen|3|✔|Gibt den Bereich an, für den die Befehlsliste gültig ist. Mögliche Optionen sind `team`, `personal` und `groupchat`.|
|`items.commands`|Array von Objekten|10|✔|Ein Array von Befehlen, die der Bot unterstützt:<br>`title`: der Name des Botbefehls (Zeichenfolge, 32).<br>`description`: eine einfache Beschreibung oder ein Beispiel für die Befehlssyntax und ihr Argument (Zeichenfolge, 128).|

## <a name="connectors"></a>Connectors

**Optional**

Der `connectors` Block definiert einen Office 365 Connector für die App.

Das Objekt ist ein Array (maximal 1 Element) mit allen Elementen vom Typ `object` . Dieser Block ist nur für Lösungen erforderlich, die einen Connector bereitstellen.

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`configurationUrl`|String|2048 Zeichen|✔|Die https://-URL, die beim Konfigurieren des Connectors verwendet werden soll.|
|`connectorId`|String|64 Zeichen|✔|Ein eindeutiger Bezeichner für den Connector, der seiner ID im [Connectors Developer Dashboard entspricht.](https://aka.ms/connectorsdashboard)|
|`scopes`|Array von Enumerationen|1|✔|Gibt an, ob der Connector eine Benutzeroberfläche im Kontext eines Kanals in einem oder eine Benutzeroberfläche bietet, die auf einen einzelnen Benutzer `team` begrenzt ist ( `personal` ). Derzeit wird nur `team` der Bereich unterstützt.|

## <a name="composeextensions"></a>composeExtensions

**Optional**

Definiert eine Messagingerweiterung für die App.

> [!NOTE]
> Der Name des Features wurde im November 2017 von "Verfassenerweiterung" in "Messagingerweiterung" geändert, der Manifestname bleibt jedoch unverändert, damit vorhandene Erweiterungen weiterhin funktionieren.

Das Objekt ist ein Array (maximal 1 Element) mit allen Elementen vom Typ `object` . Dieser Block ist nur für Lösungen erforderlich, die eine Messagingerweiterung bereitstellen.

|Name| Typ | Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`botId`|String|64|✔|Die eindeutige Microsoft-App-ID für den Bot, der die Messagingerweiterung unterstützt, wie beim Bot Framework registriert. Dies kann mit der allgemeinen [App-ID identisch sein.](#id)|
|`canUpdateConfiguration`|Boolesch|||Ein Wert, der angibt, ob die Konfiguration einer Messagingerweiterung vom Benutzer aktualisiert werden kann. Der Standardwert lautet `false`.|
|`commands`|Array des Objekts|10|✔|Array von Befehlen, die von der Messagingerweiterung unterstützt werden|

### <a name="composeextensionscommands"></a>composeExtensions.commands

Ihre Messagingerweiterung sollte einen oder mehrere Befehle deklarieren. Jeder Befehl wird in Microsoft Teams als potenzielle Interaktion vom benutzeroberflächenbasierten Einstiegspunkt angezeigt. Es gibt maximal 10 Befehle.

Jedes Befehlselement ist ein Objekt mit der folgenden Struktur:

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`id`|String|64 Zeichen|✔|Die ID für den Befehl.|
|`type`|String|64 Zeichen||Typ des Befehls. Einer oder `query` `action` . Standard: `query`|
|`title`|String|32 Zeichen|✔|Der benutzerfreundliche Befehlsname.|
|`description`|String|128 Zeichen||Die Beschreibung, die Benutzern angezeigt wird, um den Zweck dieses Befehls anzugeben.|
|`initialRun`|Boolesch|||Ein boolescher Wert, der angibt, ob der Befehl zunächst ohne Parameter ausgeführt werden soll. Standard: `false`|
|`context`|Array von Zeichenfolgen|3||Definiert, von wo aus die Nachrichtenerweiterung aufgerufen werden kann. Beliebige Kombination aus `compose` , `commandBox` , `message` . Standard ist `["compose", "commandBox"]`|
|`fetchTask`|Boolesch|||Ein boolescher Wert, der angibt, ob das Aufgabenmodul dynamisch abgerufen werden soll.|
|`taskInfo`|Object|||Geben Sie das Aufgabenmodul an, das beim Verwenden eines Befehls für die Messagingerweiterung vorab geladen werden soll.|
|`taskInfo.title`|String|64||Titel des ersten Dialogfelds.|
|`taskInfo.width`|String|||Dialogbreite – entweder eine Zahl in Pixel oder ein Standardlayout wie "groß", "mittel" oder "klein".|
|`taskInfo.height`|String|||Dialoghöhe – entweder eine Zahl in Pixel oder ein Standardlayout wie "groß", "mittel" oder "klein".|
|`taskInfo.url`|String|||Anfängliche Webview-URL.|
|`messageHandlers`|Array von Objekten|5 ||Eine Liste von Handlern, mit denen Apps aufgerufen werden können, wenn bestimmte Bedingungen erfüllt sind. Domänen müssen auch in aufgeführt `validDomains` werden.|
|`messageHandlers.type`|String|||Der Typ des Nachrichtenhandlers. Muss `"link"` sein.|
|`messageHandlers.value.domains`|Array von Zeichenfolgen|||Array von Domänen, für die der Linknachrichtenhandler registrieren kann.|
|`parameters`|Array des Objekts|5 |✔|Die Liste der Parameter, die der Befehl verwendet. Minimum: 1; maximum: 5|
|`parameter.name`|String|64 Zeichen|✔|Der Name des Parameters, wie er im Client angezeigt wird. Dies ist in der Benutzeranforderung enthalten.|
|`parameter.title`|String|32 Zeichen|✔|Benutzerfreundlicher Titel für den Parameter.|
|`parameter.description`|String|128 Zeichen||Benutzerfreundliche Zeichenfolge, die den Zweck dieses Parameters beschreibt.|
|`parameter.inputType`|String|128 Zeichen||Definiert den Typ des Steuerelements, das in einem Aufgabenmodul für angezeigt `fetchTask: true` wird. Einer von `text` , , , , , `textarea` `number` `date` `time` `toggle` `choiceset` .|
|`parameter.choices`|Array von Objekten|10||Die Auswahloptionen für `choiceset` . Verwenden Sie nur, `parameter.inputType` wenn `choiceset` .|
|`parameter.choices.title`|String|128||Titel der Auswahl.|
|`parameter.choices.value`|String|512||Value of the choice.|

## <a name="permissions"></a>Berechtigungen

**Optional**

Ein Array von dem angibt, welche Berechtigungen die App anfordert, wodurch Endbenutzer wissen, `string` wie die Erweiterung funktioniert. Die folgenden Optionen sind nicht exklusiv:

* `identity`&emsp;Erfordert Benutzeridentitätsinformationen.
* `messageTeamMembers`&emsp;Erfordert die Berechtigung zum Senden von Direktnachrichten an Teammitglieder.

Wenn Sie diese Berechtigungen beim Aktualisieren Ihrer App ändern, wiederholen Ihre Benutzer den Zustimmungsprozess, wenn sie die aktualisierte App zum ersten Mal ausführen.

## <a name="devicepermissions"></a>devicePermissions

**Optional** Array von Zeichenfolgen

Gibt die systemeigenen Features auf dem Gerät eines Benutzers an, auf die Ihre App möglicherweise Zugriff anfordern kann. Mögliche Optionen sind:

* `geolocation`
* `media`
* `notifications`
* `midi`
* `openExternal`

## <a name="validdomains"></a>validDomains

**Optional**, mit **Ausnahme erforderlich,** sofern angegeben

Eine Liste der gültigen Domänen, von denen die App erwartet, dass alle Inhalte geladen werden. Domänenauflistungen können Platzhalter enthalten, z. B. `*.example.com` . Dies entspricht genau einem Abschnitt der Domäne. wenn Sie übereinstimmen müssen, `a.b.example.com` verwenden Sie `*.*.example.com` . Wenn Ihre Registerkartenkonfiguration oder Inhaltsbenutzeroberfläche neben der für die Registerkartenkonfiguration verwendeten Domäne zu einer anderen Domäne navigieren muss, muss diese Domäne hier angegeben werden.

Es ist **jedoch nicht** erforderlich, die Domänen von Identitätsanbietern, die Sie unterstützen möchten, in Ihre App zu verwenden. Um sich z. B. mit einer Google-ID zu authentifizieren, müssen Sie zu accounts.google.com umleiten, sie sollten jedoch keine accounts.google.com in `validDomains[]` enthalten.

> [!IMPORTANT]
> Fügen Sie keine Domänen hinzu, die sich außerhalb Ihres Steuerelements befinden, weder direkt noch über Platzhalter. Beispielsweise ist `yourapp.onmicrosoft.com` gültig, aber `*.onmicrosoft.com` nicht gültig.

Das Objekt ist ein Array mit allen Elementen des Typs `string` .

## <a name="webapplicationinfo"></a>webApplicationInfo

**Optional**

Geben Sie Ihre AAD-App-ID Graph, um Benutzern die nahtlose Anmeldung bei Ihrer AAD-App zu ermöglichen.

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`id`|String|36 Zeichen|✔|AAD-Anwendungs-ID der App. Diese ID muss eine GUID sein.|
|`resource`|String|2048 Zeichen|✔|Ressourcen-URL der App zum Abrufen des Authentifizierungstokens für SSO.|

## <a name="configurableproperties"></a>configurableProperties

**Optional** – Array

Der `configurableProperties` Block definiert die App-Eigenschaften, die Teams Administrator anpassen kann. Weitere Informationen finden Sie unter [Anpassen von Apps in Microsoft Teams.](/MicrosoftTeams/customize-apps)

> [!NOTE]
> Mindestens eine Eigenschaft muss definiert werden. Sie können in diesem Block maximal neun Eigenschaften definieren.
> Als bewährte Methode müssen Sie Anpassungsrichtlinien für App-Benutzer und -Kunden bereitstellen, die sie beim Anpassen Ihrer App befolgen müssen. 

Sie können eine der folgenden Eigenschaften definieren:
* `name`: Ermöglicht administratoren das Ändern des Anzeigenamens der App.
* `shortDescription`: Ermöglicht Administratoren das Ändern der Kurzbeschreibung der App.
* `longDescription`: Ermöglicht Administratoren das Ändern der detaillierten Beschreibung der App.
* `smallImageUrl`: Es handelt sich `outline` um die Eigenschaft im Block des `icons` Manifests.
* `largeImageUrl`: Es handelt sich `color` um die Eigenschaft im Block des `icons` Manifests.
* `accentColor`: Es ist die Farbe, die in Verbindung mit und als Hintergrund für Ihre Gliederungssymbole verwendet werden soll.
* `websiteUrl`: Es ist die https://-URL zur Website des Entwicklers.
* `privacyUrl`: Es ist die https://-URL zur Datenschutzrichtlinie des Entwicklers.
* `termsOfUseUrl`: Es ist die https:// URL zu den Nutzungsbedingungen des Entwicklers.

## <a name="defaultinstallscope"></a>defaultInstallScope

**Optional** – Zeichenfolge

Gibt den für diese App definierten Installationsbereich standardmäßig an. Der definierte Bereich ist die Option, die auf der Schaltfläche angezeigt wird, wenn ein Benutzer versucht, die App hinzuzufügen. Mögliche Optionen sind:
* `personal`
* `team`
* `groupchat`
* `meetings`

## <a name="defaultgroupcapability"></a>defaultGroupCapability

**Optional** - -Objekt

Wenn ein Gruppeninstallationsbereich ausgewählt ist, wird die Standardfunktion definiert, wenn der Benutzer die App installiert. Mögliche Optionen sind:
* `team`
* `groupchat`
* `meetings`
 
|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`team`|string|||Wenn der ausgewählte Installationsbereich ausgewählt ist, gibt `team` dieses Feld die verfügbare Standardfunktion an. Optionen: `tab` , `bot` oder `connector` .|
|`groupchat`|Zeichenfolge|||Wenn der ausgewählte Installationsbereich ausgewählt ist, gibt `groupchat` dieses Feld die verfügbare Standardfunktion an. Optionen: `tab` , `bot` oder `connector` .|
|`meetings`|Zeichenfolge|||Wenn der ausgewählte Installationsbereich ausgewählt ist, gibt `meetings` dieses Feld die verfügbare Standardfunktion an. Optionen: `tab` , `bot` oder `connector` .|

