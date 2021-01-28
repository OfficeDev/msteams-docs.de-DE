---
title: Manifestschemareferenz
description: Beschreibt das Manifestschema für Microsoft Teams
ms.topic: reference
keywords: Teams-Manifestschema
author: laujan
ms.author: lajanuar
ms.openlocfilehash: 8fff56d229cc137df8356b06214893dc984396a0
ms.sourcegitcommit: 976e870cc925f61b76c3830ec04ba6e4bdfde32f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/27/2021
ms.locfileid: "50014607"
---
# <a name="reference-manifest-schema-for-microsoft-teams"></a>Referenz: Manifestschema für Microsoft Teams

Das Microsoft Teams-Manifest beschreibt, wie die App in das Microsoft Teams-Produkt integriert wird. Ihr Manifest muss dem Schema entsprechen, das unter [`https://developer.microsoft.com/json-schemas/teams/v1.8/MicrosoftTeams.schema.json`]( https://developer.microsoft.com/json-schemas/teams/v1.8/MicrosoftTeams.schema.json) gehostet wird. Frühere Versionen 1.0-1.4 werden ebenfalls unterstützt (unter Verwendung von "v1.x" in der URL).

Das folgende Schemabeispiel zeigt alle Erweiterungsoptionen.

## <a name="sample-full-manifest"></a>Beispiel für vollständiges Manifest

```json
{
  "$schema": "https://developer.microsoft.com/json-schemas/teams/v1.8/MicrosoftTeams.schema.json",
  "manifestVersion": "1.8",
  "version": "1.0.0",
  "id": "%MICROSOFT-APP-ID%",
  "packageName": "com.example.myapp",
  "localizationInfo": {
    "defaultLanguageTag": "en-us",
    "additionalLanguages": [
      {
        "languageTag": "es-es",
        "file": "en-us.json"
      }
    ]
  },
  "developer": {
    "name": "Publisher Name",
    "websiteUrl": "https://website.com/",
    "privacyUrl": "https://website.com/privacy",
    "termsOfUseUrl": "https://website.com/app-tos",
    "mpnId": "1234567890"
  },
  "name": {
    "short": "Name of your app (<=30 chars)",
    "full": "Full name of app, if longer than 30 characters (<=100 chars)"
  },
  "description": {
    "short": "Short description of your app (<= 80 chars)",
    "full": "Full description of your app (<= 4000 chars)"
  },
  "icons": {
    "outline": "A relative path to a transparent .png icon — 32px X 32px",
    "color": "A relative path to a full color .png icon — 192px X 192px"
  },
  "accentColor": "A valid HTML color code.",
  "configurableTabs": [
    {
      "configurationUrl": "https://contoso.com/teamstab/configure",
      "scopes": [
        "team",
        "groupchat"
      ],
      "canUpdateConfiguration": true,
      "context":[
        "channelTab",
        "privateChatTab",
        "meetingChatTab",
        "meetingDetailsTab",
        "meetingSidePanel",
        "meetingStage"
      ],
      "sharePointPreviewImage": "Relative path to a tab preview image for use in SharePoint — 1024px X 768",
      "supportedSharePointHosts": [
         "sharePointFullPage",
         "sharePointWebPart"
      ]
    }
  ],
  "staticTabs": [
    {
      "entityId": "unique Id for the page entity",
      "scopes": [
        "personal"
      ],
      "context":[
        "personalTab",
        "channelTab"
        ],
      "name": "Display name of tab",
      "contentUrl": "https://contoso.com/content (displayed in Teams canvas)",
      "websiteUrl": "https://contoso.com/content (displayed in web browser)",
       "searchUrl":  "https://contoso.com/content (displayed in web browser)"
    }
  ],
  "bots": [
    {
      "botId": "%MICROSOFT-APP-ID-REGISTERED-WITH-BOT-FRAMEWORK%",
      "scopes": [
        "team",
        "personal",
        "groupchat"
      ],
      "needsChannelSelector": false,
      "isNotificationOnly": false,
      "supportsFiles": true,
      "supportsCalling": false,
      "supportsVideo": true,
      "commandLists": [
        {
          "scopes": [
            "team",
            "groupchat"
          ],
          "commands": [
            {
              "title": "Command 1",
              "description": "Description of Command 1"
            },
            {
              "title": "Command 2",
              "description": "Description of Command 2"
            }
          ]
        },
        {
          "scopes": [
            "personal",
            "groupchat"
          ],
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
      "scopes": [
        "team"
      ],
      "configurationUrl": "https://contoso.com/teamsconnector/configure"
    }
  ],
  "composeExtensions": [
    {
      "canUpdateConfiguration": true,
      "botId": "%MICROSOFT-APP-ID-REGISTERED-WITH-BOT-FRAMEWORK%",
      "commands": [
        {
          "id": "exampleCmd1",
          "title": "Example Command",
          "type": "query",
          "context": [
            "compose",
            "commandBox"
          ],
          "description": "Command Description; e.g., Search on the web",
          "initialRun": true,
          "fetchTask": false,
          "parameters": [
            {
              "name": "keyword",
              "title": "Search keywords",
              "inputType": "text",
              "description": "Enter the keywords to search for",
              "value": "Initial value for the parameter",
              "choices": [
                {
                  "title": "Title of the choice",
                  "value": "Value of the choice"
                }
              ]
            }
          ]
        },
        {
          "id": "exampleCmd2",
          "title": "Example Command 2",
          "type": "action",
          "context": [
            "message"
          ],
          "description": "Command Description; e.g., Search for a customer",
          "initialRun": true,
          "fetchTask": true,
          "parameters": [
            {
              "name": "custinfo",
              "title": "Customer name",
              "description": "Enter a customer name",
              "inputType": "text"
            }
          ]
        }
      ],
      "taskInfo": {
        "title": "Initial dialog title",
        "width": "Dialog width",
        "height": "Dialog height",
        "url": "Initial webview URL"
      },
      "messageHandlers": [
        {
          "type": "link",
          "value": {
            "domains": [
              "mysite.someplace.com",
              "othersite.someplace.com"
            ]
          }
        }
      ]
    }
  ],
  "permissions": [
    "identity",
    "messageTeamMembers"
  ],
  "devicePermissions": [
    "geolocation",
    "media",
    "notifications",
    "midi",
    "openExternal"
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
  "showLoadingIndicator": false,
  "isFullScreen": false,
  "activities": {
    "activityTypes": [
      {
        "type": "taskCreated",
        "description": "Task created activity",
        "templateText": "<team member> created task <taskId> for you"
      },
      {
        "type": "userMention",
        "description": "Personal mention activity",
        "templateText": "<team member> mentioned you"
      }
    ]
  }
}
```

Das Schema definiert die folgenden Eigenschaften:

## <a name="schema"></a>$schema

*Optional, aber empfohlen –* Zeichenfolge

Die https:// URL, die auf das JSON-Schema für das Manifest verweist.

## <a name="manifestversion"></a>manifestVersion

**Erforderlich** – Zeichenfolge

Die Version des Manifestschemas, das dieses Manifest verwendet. Er sollte "1.7" sein.

## <a name="version"></a>Version

**Erforderlich** – Zeichenfolge

Die Version der bestimmten App. Wenn Sie etwas in Ihrem Manifest aktualisieren, muss auch die Version erhöht werden. Auf diese Weise wird bei der Installation des neuen Manifests das vorhandene überschrieben, und der Benutzer erhält die neue Funktionalität. Wenn diese App an den Store übermittelt wurde, muss das neue Manifest erneut übermittelt und erneut überprüft werden. Anschließend erhalten Benutzer dieser App das neue aktualisierte Manifest automatisch in ein paar Stunden, nachdem sie genehmigt wurde.

Wenn sich die von der App angeforderten Berechtigungen ändern, werden die Benutzer aufgefordert, ein Upgrade zu starten und der App erneut zu zustimmen.

Diese Versionszeichenfolge muss dem [Semverstandard](http://semver.org/) (MAJOR. MINOR. PATCH).

## <a name="id"></a>id

**Erforderlich** – Microsoft-App-ID

Der eindeutige von Microsoft generierte Bezeichner für diese App. Wenn Sie einen Bot über das Microsoft Bot Framework registriert haben oder sich die Web-App Ihrer Registerkarte bereits bei Microsoft angemeldet hat, sollten Sie bereits über eine ID verfügen und sie hier eingeben. Andernfalls sollten Sie eine neue ID im Microsoft-Anwendungsregistrierungsportal[(](https://apps.dev.microsoft.com)Meine Anwendungen) generieren, sie hier eingeben und dann wiederverwenden, wenn Sie einen Bot hinzufügen. Hinweis: Wenn Sie ein Update für Ihre vorhandene App in AppSource übermitteln, darf die ID in Ihrem Manifest nicht geändert werden.

## <a name="developer"></a>developer

**Erforderlich** – Objekt

Gibt Informationen zu Ihrem Unternehmen an. Bei an AppSource (früher Office Store) übermittelten Apps müssen diese Werte mit den Informationen in Ihrem Eintrag "AppSource" übereinstimmen. Weitere Informationen [finden Sie in unseren Veröffentlichungsrichtlinien.](~/concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md)

|Name| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|
|`name`|32 Zeichen|✔|Der Anzeigename für den Entwickler.|
|`websiteUrl`|2048 Zeichen|✔|Die https:// URL zur Website des Entwicklers. Über diesen Link sollten Benutzer zu Ihrem Unternehmen oder zu ihrer produktspezifischen Angebotsseite gelangen.|
|`privacyUrl`|2048 Zeichen|✔|Die https:// URL zur Datenschutzrichtlinie des Entwicklers.|
|`termsOfUseUrl`|2048 Zeichen|✔|Die https:// URL zu den Nutzungsbedingungen des Entwicklers.|
|`mpnId`|10 Zeichen| |**Optional** Die Microsoft Partner Network-ID, die die Partnerorganisation identifiziert, die die App erstellt.|

## <a name="name"></a>name

**Erforderlich** – Objekt

Der Name Ihrer App-Erfahrung, der Benutzern in der Teams-Erfahrung angezeigt wird. Bei an AppSource übermittelten Apps müssen diese Werte mit den Informationen in Ihrem Eintrag "AppSource" übereinstimmen. Die Werte von `short` und sollten nicht identisch `full` sein.

|Name| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|
|`short`|30 Zeichen|✔|Der kurze Anzeigename für die App.|
|`full`|100 Zeichen||Der vollständige Name der App, der verwendet wird, wenn der vollständige Name der App 30 Zeichen überschreitet.|

## <a name="description"></a>Beschreibung

**Erforderlich** – Objekt

Beschreibt Ihre App für Benutzer. Bei an AppSource übermittelten Apps müssen diese Werte mit den Informationen in Ihrem Eintrag "AppSource" übereinstimmen.

Stellen Sie sicher, dass Ihre Beschreibung Ihre Erfahrung genau beschreibt und Informationen liefert, die potenziellen Kunden helfen, ihre Erfahrung zu verstehen. Beachten Sie auch in der vollständigen Beschreibung, ob ein externes Konto für die Verwendung erforderlich ist. Die Werte von `short` und sollten nicht identisch `full` sein.  Ihre kurze Beschreibung darf nicht innerhalb der langen Beschreibung wiederholt werden und darf keinen anderen App-Namen enthalten.

|Name| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|
|`short`|80 Zeichen|✔|Eine kurze Beschreibung Ihrer App-Erfahrung, die bei begrenztem Speicherplatz verwendet wird.|
|`full`|4000 Zeichen|✔|Die vollständige Beschreibung Ihrer App.|

## <a name="packagename"></a>packageName

**Optional –** Zeichenfolge

Ein eindeutiger Bezeichner für diese App in umgekehrter Domänen-Notation; Beispiel: com.example.myapp. Maximale Länge: 64 Zeichen.

## <a name="localizationinfo"></a>localizationInfo

**Optional** – Objekt

Ermöglicht die Angabe einer Standardsprache sowie Zeiger auf zusätzliche Sprachdateien. Siehe [Lokalisierung](~/concepts/build-and-test/apps-localization.md).

|Name| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|
|`defaultLanguageTag`||✔|Das Sprachtag der Zeichenfolgen in dieser Manifestdatei der obersten Ebene.|

### <a name="localizationinfoadditionallanguages"></a>localizationInfo.additionalLanguages

Ein Array von Objekten, die zusätzliche Sprachübersetzungen angeben.

|Name| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|
|`languageTag`||✔|Das Sprachtag der Zeichenfolgen in der bereitgestellten Datei.|
|`file`||✔|Ein relativer Dateipfad zu einer JSON-Datei, die die übersetzten Zeichenfolgen enthält.|

## <a name="icons"></a>Symbole

**Erforderlich** – Objekt

Symbole, die in der Teams-App verwendet werden. Die Symboldateien müssen als Teil des Uploadpakets enthalten sein. Weitere [Informationen finden Sie](../../concepts/build-and-test/apps-package.md#app-icons) unter "Symbole".

|Name| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|
|`outline`|32 x 32 Pixel|✔|Ein relativer Dateipfad zu einem transparenten 32 x 32 PNG-Gliederungssymbol.|
|`color`|192 x 192 Pixel|✔|Ein relativer Dateipfad zu einem vollfarbigen 192 x 192 PNG-Symbol.|

## <a name="accentcolor"></a>accentColor

**Optional** – HTML Hex-Farbcode

Eine Farbe, die in Verbindung mit und als Hintergrund für Ihre Gliederungssymbole verwendet werden soll.

Der Wert muss ein gültiger #A0 sein, der mit "#" beginnt, z. B. `#4464ee` .

## <a name="configurabletabs"></a>configurableTabs

**Optional** – Array

Wird verwendet, wenn Ihre App über eine Registerkartenerfahrung im Teamkanal verfügt, die eine zusätzliche Konfiguration erfordert, bevor sie hinzugefügt wird. Konfigurierbare Registerkarten werden nur im Teambereich unterstützt (nicht persönlich), und derzeit wird nur eine Registerkarte pro App unterstützt. 

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`configurationUrl`|string|2048 Zeichen|✔|Die https:// URL, die beim Konfigurieren der Registerkarte verwendet werden soll.|
|`scopes`|Array von Enumerationen|1 |✔|Derzeit unterstützen konfigurierbare Registerkarten nur die `team` `groupchat` Bereiche. |
|`canUpdateConfiguration`|Boolescher Wert|||Ein Wert, der angibt, ob eine Instanz der Konfiguration der Registerkarte vom Benutzer nach der Erstellung aktualisiert werden kann. Standard: **true**.|
|`context` |Array von Enumerationen|6 ||Der `contextItem` Bereich, für den eine Registerkarte unterstützt wird. Standard: **[channelTab, privateChatTab, meetingChatTab, meetingDetailsTab]**.|
|`sharePointPreviewImage`|Zeichenfolge|2048||Ein relativer Dateipfad zu einem Vorschaubild der Registerkarte für die Verwendung in SharePoint. Größe 1024 x 768. |
|`supportedSharePointHosts`|Array von Enumerationen|1 ||Definiert, wie Ihre Registerkarte in SharePoint verfügbar gemacht wird. Optionen sind `sharePointFullPage` und `sharePointWebPart` |

## <a name="statictabs"></a>staticTabs

**Optional** – Array

Definiert eine Reihe von Registerkarten, die standardmäßig "angeheftet" werden können, ohne dass sie vom Benutzer manuell hinzugefügt werden. Statische Registerkarten, die im Bereich deklariert sind, werden immer an die persönliche Benutzererfahrung `personal` der App angeheftet. Im Bereich deklarierte statische `team` Registerkarten werden derzeit nicht unterstützt.

Dieses Element ist ein Array (maximal 16 Elemente) mit allen Elementen des Typs `object` . Dieser Block ist nur für Lösungen erforderlich, die eine Lösung für statische Registerkarten bereitstellen.

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`entityId`|string|64 Zeichen|✔|Ein eindeutiger Bezeichner für die Entität, die auf der Registerkarte angezeigt wird.|
|`name`|Zeichenfolge|128 Zeichen|✔|Der Anzeigename der Registerkarte in der Kanalschnittstelle.|
|`contentUrl`|Zeichenfolge||✔|Die https:// URL, die auf die Entitätsbenutzeroberfläche verweist, die im Zeichenbereich von Teams angezeigt werden soll.|
|`websiteUrl`|Zeichenfolge|||Die https:// URL, auf die verweisen soll, wenn ein Benutzer die Anzeige in einem Browser anmeldet.|
|`searchUrl`|Zeichenfolge|||Die https:// URL, auf die auf die Suchabfragen eines Benutzers verweisen soll.|
|`scopes`|Array von Enumerationen|1 |✔|Derzeit unterstützen statische Registerkarten nur den Bereich, d. h., er kann nur als Teil der `personal` persönlichen Erfahrung bereitgestellt werden.|
|`context` | Array von Enumerationen| 2 || Der `contextItem` Bereich, für den eine Registerkarte unterstützt wird.|

> [!NOTE]
> Wenn Ihre Registerkarten kontextabhängige Informationen zum Anzeigen relevanter Inhalte oder zum Initiieren eines Authentifizierungsflusses *benötigen,* finden Sie weitere Informationen unter Kontext für Ihre [Registerkarte "Microsoft Teams".](../../tabs/how-to/access-teams-context.md)

## <a name="bots"></a>Bots

**Optional** – Array

Definiert eine Botlösung zusammen mit optionalen Informationen wie z. B. Standardbefehlseigenschaften.

Das Element ist ein Array (maximal 1 Element ist derzeit nur ein Bot pro App zulässig) mit allen Elementen &mdash; des Typs `object` . Dieser Block ist nur für Lösungen erforderlich, die eine Boterfahrung bieten.

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`botId`|string|64 Zeichen|✔|Die eindeutige Microsoft-App-ID für den Bot, wie bei Bot Framework registriert. Dies kann mit der allgemeinen [App-ID identisch sein.](#id)|
|`scopes`|Array von Enumerationen|3|✔|Gibt an, ob der Bot eine Umgebung im Kontext eines Kanals in einem `team` oder Gruppenchat (`groupchat`) ist, oder aber eine Umgebung einzig für einen bestimmten Benutzer (`personal`). Diese Optionen sind nicht exklusiv.|
|`needsChannelSelector`|Boolescher Wert|||Beschreibt, ob der Bot einen Benutzerhinweis verwendet, um den Bot einem bestimmten Kanal hinzuzufügen. Standard: **`false`**|
|`isNotificationOnly`|Boolescher Wert|||Gibt an, ob ein Bot ein unidirektionaler Bot ausschließlich für Benachrichtigungen ist (im Gegensatz zu einem dialogorientierten Bot). Standard: **`false`**|
|`supportsFiles`|Boolescher Wert|||Gibt an, ob der Bot die Möglichkeit zum Hochladen/Herunterladen von Dateien in persönliche Chats unterstützt. Standard: **`false`**|
|`supportsCalling`|Boolescher Wert|||Ein Wert, der angibt, wo ein Bot Audioanrufe unterstützt. **WICHTIG:** Diese Eigenschaft ist derzeit experimentell. Experimentelle Eigenschaften sind möglicherweise nicht vollständig und werden möglicherweise geändert, bevor sie vollständig verfügbar werden.  Es wird nur zu Test- und Untersuchungszwecken bereitgestellt und sollte nicht in Produktionsanwendungen verwendet werden. Standard: **`false`**|
|`supportsVideo`|Boolescher Wert|||Ein Wert, der angibt, wo ein Bot Videoanrufe unterstützt. **WICHTIG:** Diese Eigenschaft ist derzeit experimentell. Experimentelle Eigenschaften sind möglicherweise nicht vollständig und werden möglicherweise geändert, bevor sie vollständig verfügbar werden.  Es wird nur zu Test- und Untersuchungszwecken bereitgestellt und sollte nicht in Produktionsanwendungen verwendet werden. Standard: **`false`**|

### <a name="botscommandlists"></a>bots.commandLists

Eine optionale Liste von Befehlen, die Ihr Bot Benutzern empfehlen kann. Das Objekt ist ein Array (maximal 2 Elemente) mit allen Elementen des Typs; Sie müssen eine separate Befehlsliste für jeden Bereich definieren, der von `object` Ihrem Bot unterstützt wird. Weitere [Informationen finden Sie in den Bot-Menüs.](~/bots/how-to/create-a-bot-commands-menu.md)

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`items.scopes`|Array von Enumerationen|3|✔|Gibt den Bereich an, für den die Befehlsliste gültig ist. Mögliche Optionen sind `team`, `personal` und `groupchat`.|
|`items.commands`|Array von Objekten|10 |✔|Ein Array von Befehlen, die der Bot unterstützt:<br>`title`: Name des Bot-Befehls (string, 32)<br>`description`: einfache Beschreibung oder Beispiel für die Befehlssyntax und zugehörige Argumente (string, 128)|

### <a name="botscommandlistscommands"></a>bots.commandLists.commands

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|title|string|12 |✔|Der Name des Botbefehls|
|description|Zeichenfolge|128 Zeichen|✔|Eine einfache Textbeschreibung oder ein Beispiel für die Befehlssyntax und deren Argumente.|

## <a name="connectors"></a>Connectors

**Optional** – Array

Der `connectors` Block definiert einen Office 365-Connector für die App.

Das Objekt ist ein Array (maximal 1 Element) mit allen Elementen vom `object` Typ . Dieser Block ist nur für Lösungen erforderlich, die einen Connector bereitstellen.

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`configurationUrl`|string|2048 Zeichen|✔|Die https:// URL, die beim Konfigurieren des Connectors verwendet werden soll.|
|`scopes`|Array von Enumerationen|1 |✔|Gibt an, ob der Connector eine Benutzeroberfläche im Kontext eines Kanals in einem oder eine Benutzeroberfläche bietet, die auf einen einzelnen Benutzer `team` begrenzt ist ( `personal` ). Derzeit wird nur `team` der Bereich unterstützt.|
|`connectorId`|Zeichenfolge|64 Zeichen|✔|Ein eindeutiger Bezeichner für den Connector, der seiner ID im [Connectors Developer Dashboard entspricht.](https://aka.ms/connectorsdashboard)|

## <a name="composeextensions"></a>composeExtensions

**Optional** – Array

Definiert eine Messagingerweiterung für die App.

> [!NOTE]
> Der Name des Features wurde im November 2017 von "Verfassenerweiterung" in "Messagingerweiterung" geändert, aber der Manifestname bleibt unverändert, damit vorhandene Erweiterungen weiterhin funktionieren.

Das Element ist ein Array (maximal 1 Element) mit allen Elementen vom `object` Typ . Dieser Block ist nur für Lösungen erforderlich, die eine Messagingerweiterung bereitstellen.

|Name| Typ | Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`botId`|string|64|✔|Die eindeutige Microsoft-App-ID für den Bot, der die Messagingerweiterung unterstützt, wie beim Bot Framework registriert. Dies kann mit der allgemeinen App-ID identisch sein.|
|`commands`|Array von Objekten|10 |✔|Array von Befehlen, die von der Messagingerweiterung unterstützt werden|
|`canUpdateConfiguration`|Boolescher Wert|||Ein Wert, der angibt, ob die Konfiguration einer Messagingerweiterung vom Benutzer aktualisiert werden kann. Standard: **False**.|
|`messageHandlers`|Array von Objekten|5 ||Eine Liste von Handlern, mit denen Apps aufgerufen werden können, wenn bestimmte Bedingungen erfüllt sind.|
|`messageHandlers.type`|Zeichenfolge|||Der Typ des Nachrichtenhandlers. Muss `"link"` sein.|
|`messageHandlers.value.domains`|Array von Zeichenfolgen|||Array von Domänen, für die sich der Linknachrichtenhandler registrieren kann.|

### <a name="composeextensionscommands"></a>composeExtensions.commands

Ihre Messagingerweiterung sollte einen oder mehrere Befehle deklarieren. Jeder Befehl wird in Microsoft Teams als potenzielle Interaktion vom benutzeroberflächenbasierten Einstiegspunkt angezeigt. Es gibt maximal 10 Befehle.

Jedes Befehlselement ist ein Objekt mit der folgenden Struktur:

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`id`|string|64 Zeichen|✔|Die ID für den Befehl.|
|`title`|Zeichenfolge|32 Zeichen|✔|Der benutzerfreundlicher Befehlsname.|
|`type`|Zeichenfolge|64 Zeichen||Typ des Befehls. Einer von `query` oder `action` . Standard: **Abfrage**.|
|`description`|Zeichenfolge|128 Zeichen||Die Beschreibung, die Benutzern angezeigt wird, um den Zweck dieses Befehls anzugeben.|
|`initialRun`|Boolescher Wert|||Ein boolescher Wert, der angibt, ob der Befehl zunächst ohne Parameter ausgeführt werden soll. Standard: **False**.|
|`context`|Array von Zeichenfolgen|3||Definiert, von wo aus die Nachrichtenerweiterung aufgerufen werden kann. Eine beliebige Kombination von `compose` , `commandBox` `message` . Der Standardwert lautet `["compose","commandBox"]`.|
|`fetchTask`|Boolescher Wert|||Ein boolescher Wert, der angibt, ob das Aufgabenmodul dynamisch abgerufen werden soll. Standard: **False**.|
|`taskInfo`|Objekt|||Geben Sie das Aufgabenmodul an, das bei Verwendung eines Befehls für eine Messagingerweiterung vor dem Laden geladen werden soll.|
|`taskInfo.title`|Zeichenfolge|64 Zeichen||Titel des ersten Dialogfelds.|
|`taskInfo.width`|Zeichenfolge|||Dialogbreite – entweder eine Zahl in Pixel oder ein Standardlayout wie "groß", "mittel" oder "klein".|
|`taskInfo.height`|Zeichenfolge|||Dialoghöhe – entweder eine Zahl in Pixel oder ein Standardlayout wie "groß", "mittel" oder "klein".|
|`taskInfo.url`|Zeichenfolge|||Ursprüngliche Webview-URL.|
|`parameters`|Array des Objekts|5 Elemente|✔|Die Liste der Parameter, die der Befehl verwendet. Minimum: 1; Maximum: 5.|
|`parameters.name`|Zeichenfolge|64 Zeichen|✔|Der Name des Parameters, wie er im Client angezeigt wird. Dies ist in der Benutzeranforderung enthalten.|
|`parameters.title`|Zeichenfolge|32 Zeichen|✔|Benutzerfreundlicher Titel für den Parameter.|
|`parameters.description`|Zeichenfolge|128 Zeichen||Benutzerfreundliche Zeichenfolge, die den Zweck dieses Parameters beschreibt.|
|`parameters.value`|Zeichenfolge|512 Zeichen||Anfangswert für den Parameter.|
|`parameters.inputType`|Zeichenfolge|128 Zeichen||Definiert den Typ des Steuerelements, das in einem Aufgabenmodul für angezeigt `fetchTask: true` wird. Einer von `text, textarea, number, date, time, toggle, choiceset` .|
|`parameters.choices`|Array von Objekten|10 Elemente||Die Auswahloptionen für die `choiceset` . Wird nur verwendet, wenn `parameter.inputType` `choiceset` .|
|`parameters.choices.title`|Zeichenfolge|128 Zeichen|✔|Der Titel der Auswahl.|
|`parameters.choices.value`|Zeichenfolge|512 Zeichen|✔|Value of the choice.|

## <a name="permissions"></a>Berechtigungen

**Optional** – Zeichenfolgenarray

Ein Array, von dem angegeben wird, welche Berechtigungen die App anfordert, wodurch Endbenutzer wissen, `string` wie die Erweiterung funktioniert. Die folgenden Optionen sind nicht exklusiv:

* `identity`&emsp;Erfordert Informationen zur Benutzeridentität
* `messageTeamMembers`&emsp;Erfordert die Berechtigung zum Senden direkter Nachrichten an Teammitglieder

Wenn Sie diese Berechtigungen beim Aktualisieren Ihrer App ändern, wiederholen Ihre Benutzer den Zustimmungsprozess, wenn sie die aktualisierte App zum ersten Mal ausführen. Weitere [Informationen finden Sie unter Aktualisieren](~/concepts/deploy-and-publish/appsource/post-publish/overview.md) Ihrer App.

## <a name="devicepermissions"></a>devicePermissions

**Optional** – Zeichenfolgenarray

Gibt die systemeigenen Features auf dem Gerät eines Benutzers an, auf die Ihre App Zugriff anfordern kann. Mögliche Optionen sind:

* `geolocation`
* `media`
* `notifications`
* `midi`
* `openExternal`

## <a name="validdomains"></a>validDomains

**Optional**, mit Ausnahme **von "Erforderlich"** (sofern angegeben)

Eine Liste gültiger Domänen für Websites, die von der App erwartet werden, innerhalb des Teams-Clients zu laden. Domänenauflistungen können Platzhalter enthalten, z. B. `*.example.com` . Dies entspricht genau einem Segment der Domäne. Wenn Sie übereinstimmen müssen, `a.b.example.com` verwenden Sie `*.*.example.com` . Wenn Ihre Registerkartenkonfiguration oder Inhaltsbenutzeroberfläche neben der Registerkartenkonfiguration zu einer anderen Domäne navigieren muss, muss diese Domäne hier angegeben werden.

Es ist **jedoch nicht** erforderlich, die Domänen von Identitätsanbietern, die Sie unterstützen möchten, in Ihre App zu verwenden. Um sich z. B. mithilfe einer Google-ID zu authentifizieren, ist es erforderlich, zu accounts.google.com umzuleiten, sie sollten jedoch nicht accounts.google.com `validDomains[]` enthalten.

Teams-Apps, für die ihre eigenen SharePoint-URLs ordnungsgemäß funktionieren müssen, enthalten möglicherweise "{teamsitedomain}" in der Liste der gültigen Domänen.

> [!IMPORTANT]
> Fügen Sie keine Domänen hinzu, die sich außerhalb Ihrer Kontrolle befinden, entweder direkt oder über Platzhalter. Beispielsweise ist `yourapp.onmicrosoft.com` er gültig, aber `*.onmicrosoft.com` ungültig.

Das Objekt ist ein Array mit allen Elementen des Typs `string` .

## <a name="webapplicationinfo"></a>webApplicationInfo

**Optional** – Objekt

Geben Sie Ihre Azure Active Directory (Azure AD)-App-ID und Microsoft Graph-Informationen an, damit sich Benutzer nahtlos bei Ihrer App anmelden können. Wenn Ihre App in Azure AD registriert ist, müssen Sie die App-ID bereitstellen, damit Administratoren die Berechtigungen auf einfache Weise überprüfen und die Zustimmung im Teams Admin Center erteilen können.

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`id`|string|36 Zeichen|✔|AAD-Anwendungs-ID der App. Diese ID muss eine GUID sein.|
|`resource`|Zeichenfolge|2048 Zeichen|✔|Ressourcen-URL der App zum Abrufen des Authentifizierungstokens für SSO. </br> **HINWEIS:** Wenn Sie SSO nicht verwenden, stellen Sie sicher, dass Sie in dieses Feld einen Dummyzeichenfolgenwert in Ihr App-Manifest eingeben, um beispielsweise eine https://notapplicable Fehlerantwort zu vermeiden. |
|`applicationPermissions`|array of strings|128 Zeichen||Geben Sie eine [präzise ressourcenspezifische Zustimmung an.](../../graph-api/rsc/resource-specific-consent.md#resource-specific-permissions)|

## <a name="showloadingindicator"></a>showLoadingIndicator

**Optional** – boolescher Wert

Gibt an, ob die Ladeanzeige angezeigt werden soll, wenn eine App/Registerkarte geladen wird. Standard: **False**.
>[!NOTE]
>Wenn Sie "showLoadingIndicator : true" in Ihrem App-Manifest festlegen, müssen Sie die Inhaltsseiten Ihrer Registerkarten und Aufgabenmodule [](../../tabs/how-to/create-tab-pages/content-page.md#show-a-native-loading-indicator) so ändern, dass das protokoll unter Anzeigen eines nativen Ladeindikatordokuments beschrieben wird.


## <a name="isfullscreen"></a>isFullScreen

 **Optional** – boolescher Wert

Geben Sie an, wo eine persönliche App mit oder ohne Tabulatorleiste gerendert wird. Standard: **False**.

## <a name="activities"></a>Aktivitäten

**Optional** – Objekt

Definieren Sie die Eigenschaften, die Ihre App zum Veröffentlichen in einem Benutzeraktivitätsfeed verwendet.

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`activityTypes`|Array von Objekten|128 Elemente| | Geben Sie die Arten von Aktivitäten an, die Ihre App in einem Benutzeraktivitätsfeed veröffentlichen kann.|

### <a name="activitiesactivitytypes"></a>activities.activityTypes

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`type`|string|32 Zeichen|✔|Der Benachrichtigungstyp. *Siehe unten*.|
|`description`|Zeichenfolge|128 Zeichen|✔|Eine kurze Beschreibung der Benachrichtigung. *Siehe unten*.|
|`templateText`|Zeichenfolge|128 Zeichen|✔|Beispiel: "{actor}: Aufgabe {taskId} für Sie erstellt"|

```json
{
   "activities":{
      "activityTypes":[
         {
            "type":"taskCreated",
            "description":"Task Created Activity",
            "templateText":"{actor} created task {taskId} for you"
         },
         {
            "type":"teamMention",
            "description":"Team Mention Activity",
            "templateText":"{actor} mentioned team"
         },
         {
            "type":"channelMention",
            "description":"Channel Mention Activity",
            "templateText":"{actor} mentioned channel"
         },
         {
            "type":"userMention",
            "description":"Personal Mention Activity",
            "templateText":"{actor} mentioned user"
         },
         {
            "type":"calendarForward",
            "description":"Forwarding a Calendar Event",
            "templateText":"{actor} sent user an invite on behalf of {eventOwner}"
         },
         {
            "type":"calendarForward",
            "description":"Forwarding a Calendar Event",
            "templateText":"{actor} sent user an invite on behalf of {eventOwner}"
         },
         {
            "type":"creatorTaskCreated",
            "description":"Created Task Created",
            "templateText":"The Creator created task {taskId} for you"
         }
      ]
   }
}
```

***
>
>
