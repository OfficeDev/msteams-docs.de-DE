---
title: Manifestschemareferenz
description: Beschreibt das Manifestschema für Microsoft Teams
ms.topic: reference
ms.author: lajanuar
localization_priority: Normal
keywords: Teams-Manifestschema
ms.openlocfilehash: 44bae986d5ea78a044cb66d48e6e093d489f4473
ms.sourcegitcommit: 99b1f151e4e36a86c6a5d2ccbde01bf45b61f526
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/21/2021
ms.locfileid: "53037628"
---
# <a name="reference-manifest-schema-for-microsoft-teams"></a>Referenz: Manifestschema für Microsoft Teams

Das Teams-Manifest beschreibt, wie die App in das Microsoft Teams Produkt integriert wird. Ihr Manifest muss dem schema gehosteten [`https://developer.microsoft.com/json-schemas/teams/v1.10/MicrosoftTeams.schema.json`]( https://developer.microsoft.com/json-schemas/teams/v1.10/MicrosoftTeams.schema.json) entsprechen. Frühere Versionen 1.0, 1.1,..., 1.6 usw. werden ebenfalls unterstützt (unter Verwendung von "v1.x" in der URL).
Weitere Informationen zu den Änderungen, die in jeder Version vorgenommen wurden, finden Sie im [Manifeständerungsprotokoll.](https://github.com/OfficeDev/microsoft-teams-app-schema/releases)

Das folgende Schemabeispiel zeigt alle Erweiterbarkeitsoptionen:

## <a name="sample-full-manifest"></a>Vollständiges Beispielmanifest

```json
{
  "$schema": "https://developer.microsoft.com/json-schemas/teams/v1.10/MicrosoftTeams.schema.json",
  "manifestVersion": "1.10",
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
    ]
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
  },
  "defaultInstallScope": "meetings",
  "defaultGroupCapability": {
    "meetings": "tab", 
    "team": "bot", 
    "groupchat": "bot"
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
  ]              
}
```

Das Schema definiert die folgenden Eigenschaften:

## <a name="schema"></a>$schema

Optional, aber empfohlen – Zeichenfolge

Die https:// URL, die auf das JSON-Schema für das Manifest verweist.

## <a name="manifestversion"></a>manifestVersion

**Erforderlich** – Zeichenfolge

Die Version des Manifestschemas, das dieses Manifest verwendet. Es muss 1.10 sein.

## <a name="version"></a>Version

**Erforderlich** – Zeichenfolge

Die Version einer bestimmten App. Wenn Sie etwas in Ihrem Manifest aktualisieren, muss auch die Version erhöht werden. Auf diese Weise wird bei der Installation des neuen Manifests das vorhandene überschrieben, und der Benutzer erhält die neue Funktionalität. Wenn diese App an den Store übermittelt wurde, muss das neue Manifest erneut übermittelt und erneut überprüft werden. Die App-Benutzer erhalten das neue aktualisierte Manifest automatisch innerhalb weniger Stunden nach der Genehmigung des Manifests.

Wenn sich die App-Anforderungen für Berechtigungen ändern, werden die Benutzer aufgefordert, ein Upgrade durchzuführen und der App erneut zuzustimmen.

Diese Versionszeichenfolge muss dem [Semverstandard](http://semver.org/) (MAJOR. kleiner. PATCH).

## <a name="id"></a>id

**Erforderlich** – Microsoft-App-ID

Die ID ist ein eindeutiger von Microsoft generierter Bezeichner für die App. Sie haben eine ID, wenn Ihr Bot über die Microsoft Bot Framework registriert ist oder sich die Web-App Ihrer Registerkarte bereits bei Microsoft anmeldet. Sie müssen die ID hier eingeben. Andernfalls müssen Sie eine neue ID im [Microsoft-Anwendungsregistrierungsportal](https://aka.ms/appregistrations)generieren. Verwenden Sie die gleiche ID, wenn Sie einen Bot hinzufügen.

> [!NOTE]
> Wenn Sie ein Update für Ihre vorhandene App in AppSource übermitteln, darf die ID in Ihrem Manifest nicht geändert werden.

## <a name="developer"></a>developer

**Erforderlich** – Objekt

Gibt Informationen zu Ihrem Unternehmen an. Für An den Teams Store übermittelte Apps müssen diese Werte mit den Informationen in Ihrem Store-Eintrag übereinstimmen. Weitere Informationen finden Sie in den [Richtlinien für die Teams Store-Veröffentlichung.](~/concepts/deploy-and-publish/appsource/publish.md)

|Name| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|
|`name`|32 Zeichen|✔|Der Anzeigename für den Entwickler.|
|`websiteUrl`|2048 Zeichen|✔|Die https:// URL zur Website des Entwicklers. Dieser Link muss Benutzer zu Ihrem Unternehmen oder ihrer produktspezifischen Angebotsseite bringen.|
|`privacyUrl`|2048 Zeichen|✔|Die https:// URL zur Datenschutzrichtlinie des Entwicklers.|
|`termsOfUseUrl`|2048 Zeichen|✔|Die https:// URL zu den Nutzungsbedingungen des Entwicklers.|
|`mpnId`|10 Zeichen| |**Optional** Die Microsoft Partner Network-ID, die die Partnerorganisation identifiziert, die die App erstellt.|

## <a name="name"></a>name

**Erforderlich** – Objekt

Der Name Ihrer App-Erfahrung, der Benutzern in der Teams angezeigt wird. Für an AppSource übermittelte Apps müssen diese Werte mit den Informationen in Ihrem AppSource-Eintrag übereinstimmen. Die Werte von `short` und `full` müssen unterschiedlich sein.

|Name| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|
|`short`|30 Zeichen|✔|Der kurze Anzeigename für die App.|
|`full`|100 Zeichen||Der vollständige Name der App, der verwendet wird, wenn der vollständige App-Name 30 Zeichen überschreitet.|

## <a name="description"></a>description

**Erforderlich** – Objekt

Beschreibt Ihre App für Benutzer. Für an AppSource übermittelte Apps müssen diese Werte mit den Informationen in Ihrem AppSource-Eintrag übereinstimmen.

Stellen Sie sicher, dass Ihre Beschreibung Ihre Erfahrung genau beschreibt und Informationen bereitstellt, die potenziellen Kunden helfen, zu verstehen, was Ihre Erfahrung bewirkt. Sie müssen in der vollständigen Beschreibung notieren, ob ein externes Konto für die Verwendung erforderlich ist. Die Werte von `short` und `full` müssen unterschiedlich sein. Ihre kurze Beschreibung darf nicht innerhalb der langen Beschreibung wiederholt werden und darf keinen anderen App-Namen enthalten.

|Name| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|
|`short`|80 Zeichen|✔|Eine kurze Beschreibung der App-Erfahrung, die verwendet wird, wenn der Platz begrenzt ist.|
|`full`|4000 Zeichen|✔|Die vollständige Beschreibung Ihrer App.|

## <a name="packagename"></a>Packagename

**Optional** – Zeichenfolge

Ein eindeutiger Bezeichner für die App in umgekehrter Domänenschreibweise; z. B. com.example.myapp. Maximale Länge: 64 Zeichen.

## <a name="localizationinfo"></a>localizationInfo

**Optional** - Objekt

Ermöglicht die Angabe einer Standardsprache sowie Zeiger auf zusätzliche Sprachdateien. Weitere Informationen finden Sie unter [Lokalisierung.](~/concepts/build-and-test/apps-localization.md)

|Name| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|
|`defaultLanguageTag`||✔|Das Sprachtag der Zeichenfolgen in dieser Manifestdatei auf oberster Ebene.|

### <a name="localizationinfoadditionallanguages"></a>localizationInfo.additionalLanguages

Ein Array von Objekten, die zusätzliche Sprachübersetzungen angeben.

|Name| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|
|`languageTag`||✔|Das Sprachtag der Zeichenfolgen in der bereitgestellten Datei.|
|`file`||✔|Ein relativer Dateipfad zu einer JSON-Datei, die die übersetzten Zeichenfolgen enthält.|

## <a name="icons"></a>Symbole

**Erforderlich** – Objekt

Symbole, die in der Teams-App verwendet werden. Die Symboldateien müssen als Teil des Uploadpakets enthalten sein. Weitere Informationen finden Sie unter ["Symbole".](../../concepts/build-and-test/apps-package.md#app-icons)

|Name| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|
|`outline`|32 x 32 Pixel|✔|Ein relativer Dateipfad zu einem transparenten 32 x 32 PNG-Gliederungssymbol.|
|`color`|192 x 192 Pixel|✔|Ein relativer Dateipfad zu einem farbigen PNG-Symbol mit 192 x 192.|

## <a name="accentcolor"></a>accentColor

**Optional** – HTML Hex-Farbcode

Eine Farbe, die in Verbindung mit und als Hintergrund für Ihre Gliederungssymbole verwendet werden soll.

Der Wert muss ein gültiger HTML-Farbcode sein, der mit "#" beginnt, z. `#4464ee` B. .

## <a name="configurabletabs"></a>configurableTabs

**Optional** – Array

Wird verwendet, wenn Ihre App-Erfahrung über eine Registerkartenoberfläche im Teamkanal verfügt, die eine zusätzliche Konfiguration erfordert, bevor sie hinzugefügt wird. Konfigurierbare Registerkarten werden nur im Teams-Bereich unterstützt, und Sie können dieselben Registerkarten mehrmals konfigurieren. Sie können sie jedoch nur einmal im Manifest definieren.

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`configurationUrl`|string|2048 Zeichen|✔|Die https:// URL, die beim Konfigurieren der Registerkarte verwendet werden soll.|
|`scopes`|Array von Enumerationen|1|✔|Derzeit unterstützen konfigurierbare Registerkarten nur die `team` Bereiche und `groupchat` Bereiche. |
|`canUpdateConfiguration`|Boolescher Wert|||Ein Wert, der angibt, ob eine Instanz der Konfiguration der Registerkarte vom Benutzer nach der Erstellung aktualisiert werden kann. Standard: **true**.|
|`context` |Array von Enumerationen|6 ||Die Gruppe von `contextItem` Bereichen, in denen eine [Registerkarte unterstützt wird.](../../tabs/how-to/access-teams-context.md) Standard: **[channelTab, privateChatTab, meetingChatTab, meetingDetailsTab]**.|
|`sharePointPreviewImage`|Zeichenfolge|2048||Ein relativer Dateipfad zu einem Registerkartenvorschaubild zur Verwendung in SharePoint. Größe 1024 x 768. |
|`supportedSharePointHosts`|Array von Enumerationen|1||Definiert, wie Ihre Registerkarte in SharePoint zur Verfügung gestellt wird. Optionen sind `sharePointFullPage` und `sharePointWebPart` |

## <a name="statictabs"></a>staticTabs

**Optional** – Array

Definiert eine Gruppe von Registerkarten, die standardmäßig "angeheftet" werden können, ohne dass der Benutzer sie manuell hinzufügt. Im Bereich deklarierte statische `personal` Registerkarten werden immer an die persönliche Benutzeroberfläche der App angeheftet. Statische Registerkarten, die im Bereich deklariert `team` sind, werden derzeit nicht unterstützt.

Dieses Element ist ein Array (maximal 16 Elemente) mit allen Elementen des `object` Typs. Dieser Block ist nur für Lösungen erforderlich, die eine statische Registerkartenlösung bereitstellen.

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`entityId`|string|64 Zeichen|✔|Ein eindeutiger Bezeichner für die Entität, die auf der Registerkarte angezeigt wird.|
|`name`|Zeichenfolge|128 Zeichen|✔|Der Anzeigename der Registerkarte in der Kanalschnittstelle.|
|`contentUrl`|Zeichenfolge||✔|Die https:// URL, die auf die Entitäts-UI verweist, die im Teams Canvas angezeigt werden soll.|
|`websiteUrl`|Zeichenfolge|||Die https:// URL, auf die verweist, wenn sich ein Benutzer für die Anzeige in einem Browser entscheidet.|
|`searchUrl`|Zeichenfolge|||Die https:// URL, auf die für die Suchabfragen eines Benutzers verweist.|
|`scopes`|Array von Enumerationen|1|✔|Derzeit unterstützen statische Registerkarten nur den `personal` Bereich, was bedeutet, dass sie nur als Teil der persönlichen Benutzeroberfläche bereitgestellt werden können.|
|`context` | Array von Enumerationen| 2|| Die Gruppe von `contextItem` Bereichen, in denen eine Registerkarte unterstützt wird.|

> [!NOTE]
>  Das searchUrl-Feature ist für Drittanbieterentwickler nicht verfügbar.
> Wenn Ihre Registerkarten kontextabhängige Informationen zum Anzeigen relevanter Inhalte oder zum Initiieren eines Authentifizierungsflusses benötigen, finden Sie weitere Informationen unter ["Kontext für Ihre Microsoft Teams Registerkarte abrufen".](../../tabs/how-to/access-teams-context.md)

## <a name="bots"></a>Bots

**Optional** – Array

Definiert eine Bot-Lösung zusammen mit optionalen Informationen wie Standardbefehlseigenschaften.

Das Element ist ein Array (maximal 1 Element &mdash; ist derzeit nur ein Bot pro App zulässig) mit allen Elementen des `object` Typs. Dieser Block ist nur für Lösungen erforderlich, die eine Bot-Erfahrung bieten.

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`botId`|string|64 Zeichen|✔|Die eindeutige Microsoft-App-ID für den Bot, wie bei Bot Framework registriert. Dies kann durchaus mit der gesamten [App-ID](#id)übereinstimmen.|
|`scopes`|Array von Enumerationen|3|✔|Gibt an, ob der Bot eine Umgebung im Kontext eines Kanals in einem `team` oder Gruppenchat (`groupchat`) ist, oder aber eine Umgebung einzig für einen bestimmten Benutzer (`personal`). Diese Optionen sind nicht exklusiv.|
|`needsChannelSelector`|Boolescher Wert|||Beschreibt, ob der Bot einen Benutzerhinweis verwendet, um den Bot einem bestimmten Kanal hinzuzufügen. Standard: **`false`**|
|`isNotificationOnly`|Boolescher Wert|||Gibt an, ob ein Bot ein unidirektionaler Bot ausschließlich für Benachrichtigungen ist (im Gegensatz zu einem dialogorientierten Bot). Standard: **`false`**|
|`supportsFiles`|Boolescher Wert|||Gibt an, ob der Bot die Möglichkeit zum Hochladen/Herunterladen von Dateien in persönliche Chats unterstützt. Standard: **`false`**|
|`supportsCalling`|Boolescher Wert|||Ein Wert, der angibt, wo ein Bot Audioanrufe unterstützt. **WICHTIG:** Diese Eigenschaft ist derzeit experimentell. Experimentelle Eigenschaften sind möglicherweise nicht vollständig und werden möglicherweise geändert, bevor sie vollständig verfügbar sind.  Es wird nur zu Test- und Untersuchungszwecken bereitgestellt und darf nicht in Produktionsanwendungen verwendet werden. Standard: **`false`**|
|`supportsVideo`|Boolescher Wert|||Ein Wert, der angibt, wo ein Bot Videoanrufe unterstützt. **WICHTIG:** Diese Eigenschaft ist derzeit experimentell. Experimentelle Eigenschaften sind möglicherweise nicht vollständig und werden möglicherweise geändert, bevor sie vollständig verfügbar sind.  Es wird nur zu Test- und Untersuchungszwecken bereitgestellt und darf nicht in Produktionsanwendungen verwendet werden. Standard: **`false`**|

### <a name="botscommandlists"></a>bots.commandLists

Eine optionale Liste von Befehlen, die Ihr Bot Benutzern empfehlen kann. Das Objekt ist ein Array (maximal 2 Elemente) mit allen Elementen des `object` Typs. Sie müssen eine separate Befehlsliste für jeden Bereich definieren, den Ihr Bot unterstützt. Weitere Informationen finden Sie [in den Bot-Menüs.](~/bots/how-to/create-a-bot-commands-menu.md)

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`items.scopes`|Array von Enumerationen|3|✔|Gibt den Bereich an, für den die Befehlsliste gültig ist. Mögliche Optionen sind `team`, `personal` und `groupchat`.|
|`items.commands`|Array von Objekten|10|✔|Ein Array von Befehlen, die der Bot unterstützt:<br>`title`: Name des Bot-Befehls (string, 32)<br>`description`: eine einfache Beschreibung oder ein Beispiel für die Befehlssyntax und ihr Argument (Zeichenfolge, 128).|

### <a name="botscommandlistscommands"></a>bots.commandLists.commands

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|title|string|12 |✔|Der Bot-Befehlsname.|
|description|Zeichenfolge|128 Zeichen|✔|Eine einfache Textbeschreibung oder ein Beispiel für die Befehlssyntax und deren Argumente.|

## <a name="connectors"></a>Steckverbinder

**Optional** – Array

Der `connectors` Block definiert einen Office 365 Connector für die App.

Das Objekt ist ein Array (maximal 1 Element) mit allen Elementen des Typs `object` . Dieser Block ist nur für Lösungen erforderlich, die einen Connector bereitstellen.

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`configurationUrl`|string|2048 Zeichen|✔|Die https:// URL, die beim Konfigurieren des Connectors verwendet werden soll.|
|`scopes`|Array von Enumerationen|1|✔|Gibt an, ob der Connector eine Erfahrung im Kontext eines Kanals in einem oder `team` eine Benutzeroberfläche bietet, die auf einen einzelnen Benutzer beschränkt ist ( `personal` ). Derzeit wird nur der `team` Bereich unterstützt.|
|`connectorId`|Zeichenfolge|64 Zeichen|✔|Ein eindeutiger Bezeichner für den Connector, der seiner ID im [Connectors Developer Dashboard](https://aka.ms/connectorsdashboard)entspricht.|

## <a name="composeextensions"></a>composeExtensions

**Optional** – Array

Definiert eine Messaging-Erweiterung für die App.

> [!NOTE]
> Der Name des Features wurde im November 2017 von "Erstellerweiterung" in "Messaging-Erweiterung" geändert, aber der Manifestname bleibt unverändert, sodass vorhandene Erweiterungen weiterhin funktionieren.

Das Element ist ein Array (maximal 1 Element) mit allen Elementen des Typs `object` . Dieser Block ist nur für Lösungen erforderlich, die eine Messaging-Erweiterung bereitstellen.

|Name| Typ | Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`botId`|string|64|✔|Die eindeutige Microsoft-App-ID für den Bot, der die Messaging-Erweiterung unterstützt, wie beim Bot Framework registriert. Dies kann durchaus mit der gesamten App-ID übereinstimmen.|
|`commands`|Array von Objekten|10|✔|Array von Befehlen, die von der Messaging-Erweiterung unterstützt werden.|
|`canUpdateConfiguration`|Boolescher Wert|||Ein Wert, der angibt, ob die Konfiguration einer Messaging-Erweiterung vom Benutzer aktualisiert werden kann. Standard: **False**.|
|`messageHandlers`|Array von Objekten|5 ||Eine Liste von Handlern, mit denen Apps aufgerufen werden können, wenn bestimmte Bedingungen erfüllt sind.|
|`messageHandlers.type`|Zeichenfolge|||Der Typ des Nachrichtenhandlers. Muss `"link"` sein.|
|`messageHandlers.value.domains`|Array von Zeichenfolgen|||Array von Domänen, für die sich der Linknachrichtenhandler registrieren kann.|

### <a name="composeextensionscommands"></a>composeExtensions.commands

Ihre Messaging-Erweiterung muss einen oder mehrere Befehle deklarieren. Jeder Befehl wird in Microsoft Teams als potenzielle Interaktion vom UI-basierten Einstiegspunkt angezeigt. Es gibt maximal 10 Befehle.

Jedes Befehlselement ist ein Objekt mit der folgenden Struktur:

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`id`|string|64 Zeichen|✔|Die ID für den Befehl.|
|`title`|Zeichenfolge|32 Zeichen|✔|Der benutzerfreundliche Befehlsname.|
|`type`|Zeichenfolge|64 Zeichen||Typ des Befehls. Eine von `query` oder `action` . Standard: **Abfrage**.|
|`description`|Zeichenfolge|128 Zeichen||Die Beschreibung, die Benutzern angezeigt wird, um den Zweck dieses Befehls anzugeben.|
|`initialRun`|Boolescher Wert|||Ein boolescher Wert gibt an, ob der Befehl anfänglich ohne Parameter ausgeführt wird. Der Standardwert ist **false**.|
|`context`|Array von Zeichenfolgen|3||Definiert, von wo aus die Nachrichtenerweiterung aufgerufen werden kann. Eine beliebige Kombination von `compose` , `commandBox` , `message` . Der Standardwert ist `["compose","commandBox"]`.|
|`fetchTask`|Boolescher Wert|||Ein boolescher Wert, der angibt, ob das Aufgabenmodul dynamisch abgerufen werden muss. Der Standardwert ist **false**.|
|`taskInfo`|Objekt|||Geben Sie das Aufgabenmodul an, das vorab geladen werden soll, wenn Sie einen Messaging-Erweiterungsbefehl verwenden.|
|`taskInfo.title`|Zeichenfolge|64 Zeichen||Titel des ersten Dialogfelds.|
|`taskInfo.width`|Zeichenfolge|||Dialogbreite – entweder eine Zahl in Pixeln oder ein Standardlayout, z. B. "groß", "mittel" oder "klein".|
|`taskInfo.height`|Zeichenfolge|||Dialoghöhe – entweder eine Zahl in Pixeln oder ein Standardlayout, z. B. "groß", "mittel" oder "klein".|
|`taskInfo.url`|Zeichenfolge|||Ursprüngliche Webansichts-URL.|
|`parameters`|Array des Objekts|5 Elemente|✔|Die Liste der Parameter, die der Befehl verwendet. Minimum: 1; Maximum: 5.|
|`parameters.name`|Zeichenfolge|64 Zeichen|✔|Der Name des Parameters, wie er im Client angezeigt wird. Dies ist in der Benutzeranforderung enthalten.|
|`parameters.title`|Zeichenfolge|32 Zeichen|✔|Benutzerfreundlicher Titel für den Parameter.|
|`parameters.description`|Zeichenfolge|128 Zeichen||Benutzerfreundliche Zeichenfolge, die den Zweck dieses Parameters beschreibt.|
|`parameters.value`|Zeichenfolge|512 Zeichen||Anfangswert für den Parameter.|
|`parameters.inputType`|Zeichenfolge|128 Zeichen||Definiert den Typ des Steuerelements, das in einem Aufgabenmodul für angezeigt `fetchTask: true` wird. Eine von `text, textarea, number, date, time, toggle, choiceset` .|
|`parameters.choices`|Array von Objekten|10 Elemente||Die Auswahloptionen für die `choiceset` . Wird nur verwendet, wenn `parameter.inputType` `choiceset` .|
|`parameters.choices.title`|Zeichenfolge|128 Zeichen|✔|Titel der Wahl.|
|`parameters.choices.value`|Zeichenfolge|512 Zeichen|✔|Value of the choice.|

## <a name="permissions"></a>Berechtigungen

**Optional** – Array von Zeichenfolgen

Ein `string` Array, das angibt, welche Berechtigungen die App anfordert, wodurch Endbenutzer wissen, wie die Erweiterung funktioniert. Die folgenden Optionen sind nicht exklusiv:

* `identity`&emsp;Erfordert Benutzeridentitätsinformationen.
* `messageTeamMembers`&emsp;Erfordert die Berechtigung, direkte Nachrichten an Teammitglieder zu senden.

Wenn Sie diese Berechtigungen während des App-Updates ändern, müssen Ihre Benutzer den Zustimmungsprozess wiederholen, nachdem sie die aktualisierte App ausgeführt haben. Weitere Informationen finden Sie unter [Aktualisieren Ihrer App.](~/concepts/deploy-and-publish/appsource/post-publish/overview.md)

## <a name="devicepermissions"></a>devicePermissions

**Optional** – Array von Zeichenfolgen

Stellt die systemeigenen Features auf dem Gerät eines Benutzers bereit, auf die Ihre App Zugriff anfordert. Mögliche Optionen sind:

* `geolocation`
* `media`
* `notifications`
* `midi`
* `openExternal`

## <a name="validdomains"></a>validDomains

**Optional,** außer **erforderlich,** sofern angegeben.

Eine Liste der gültigen Domänen für Websites, die die App innerhalb des Teams-Clients laden soll. Domäneneinträge können Platzhalter enthalten, `*.example.com` z. B. . Dies entspricht genau einem Segment der Domäne. wenn Sie übereinstimmen `a.b.example.com` müssen, verwenden Sie `*.*.example.com` . Wenn Ihre Registerkartenkonfiguration oder Inhalts-UI zu einer anderen Domäne als der für die Registerkartenkonfiguration verwendeten navigieren muss, muss diese Domäne hier angegeben werden.

Es ist **nicht** erforderlich, die Domänen von Identitätsanbietern, die Sie in Ihrer App unterstützen möchten, einzuschließen. Um sich beispielsweise mit einer Google-ID zu authentifizieren, ist es erforderlich, zu accounts.google.com umzuleiten. Sie dürfen jedoch keine accounts.google.com in `validDomains[]` einschließen.

Teams Apps, die ihre eigenen SharePoint-URLs benötigen, um ordnungsgemäß zu funktionieren, enthalten "{teamsitedomain}" in ihrer gültigen Domänenliste.

> [!IMPORTANT]
> Fügen Sie keine Domänen hinzu, die sich außerhalb Ihres Steuerelements befinden, entweder direkt oder über Platzhalter. Ist z. `yourapp.onmicrosoft.com` B. gültig, ist jedoch `*.onmicrosoft.com` ungültig.

Das Objekt ist ein Array mit allen Elementen des Typs `string` .

## <a name="webapplicationinfo"></a>webApplicationInfo

**Optional** - Objekt

Geben Sie Ihre Azure Active Directory (AAD)-App-ID und Microsoft Graph Informationen an, damit sich Benutzer nahtlos bei Ihrer App anmelden können. Wenn Ihre App in AAD registriert ist, müssen Sie die App-ID angeben, damit Administratoren berechtigungen einfach überprüfen und ihre Zustimmung im Teams Admin Center erteilen können.

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`id`|string|36 Zeichen|✔|AAD-Anwendungs-ID der App. Diese ID muss eine GUID sein.|
|`resource`|Zeichenfolge|2048 Zeichen|✔|Ressourcen-URL der App zum Abrufen des Authentifizierungstokens für SSO. </br> **HINWEIS:** Wenn Sie SSO nicht verwenden, stellen Sie sicher, dass Sie einen Pseudozeichenfolgenwert in dieses Feld in Ihr App-Manifest eingeben, um beispielsweise https://notapplicable eine Fehlerantwort zu vermeiden. |
|`applicationPermissions`|array of strings|128 Zeichen||Geben Sie eine präzise [ressourcenspezifische Zustimmung an.](../../graph-api/rsc/resource-specific-consent.md#resource-specific-permissions)|

## <a name="showloadingindicator"></a>showLoadingIndicator

**Optional** – boolescher Wert

Gibt an, ob die Ladeanzeige angezeigt werden soll, wenn eine App oder Registerkarte geladen wird. Der Standardwert ist **false**.
>[!NOTE]
>Wenn Sie `showLoadingIndicator` im App-Manifest "true" auswählen, ändern Sie zum ordnungsgemäßen Laden der Seite die Inhaltsseiten Ihrer Registerkarten und Aufgabenmodule, wie unter ["Anzeigen eines systemeigenen Ladeindikatordokuments"](../../tabs/how-to/create-tab-pages/content-page.md#show-a-native-loading-indicator) beschrieben.


## <a name="isfullscreen"></a>isFullScreen

 **Optional** – boolescher Wert

Gibt an, wo eine persönliche App mit oder ohne Registerkartenkopfleiste gerendert wird. Der Standardwert ist **false**.

## <a name="activities"></a>Aktivitäten

**Optional** - Objekt

Definieren Sie die Eigenschaften, die Ihre App zum Posten eines Benutzeraktivitätsfeeds verwendet.

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`activityTypes`|Array von Objekten|128 Elemente| | Stellen Sie die Arten von Aktivitäten bereit, die Ihre App in einem Benutzeraktivitätsfeed veröffentlichen kann.|

### <a name="activitiesactivitytypes"></a>activities.activityTypes

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`type`|string|32 Zeichen|✔|Der Benachrichtigungstyp. *Siehe unten*.|
|`description`|Zeichenfolge|128 Zeichen|✔|Eine kurze Beschreibung der Benachrichtigung. *Siehe unten*.|
|`templateText`|Zeichenfolge|128 Zeichen|✔|Beispiel: "{actor} erstellt Aufgabe {taskId} für Sie"|

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
