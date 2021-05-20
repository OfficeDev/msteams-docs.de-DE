---
title: Manifestschemaverweis
description: Beschreibt das Manifestschema für Microsoft Teams
ms.topic: reference
ms.author: lajanuar
localization_priority: Normal
keywords: Teams-Manifestschema
ms.openlocfilehash: 6c7cd02480f78d19aed269b5d78d0c6f470621d2
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566446"
---
# <a name="reference-manifest-schema-for-microsoft-teams"></a>Referenz: Manifestschema für Microsoft Teams

Das Teams-Manifest beschreibt, wie sich die App in das Microsoft Teams Produkt integriert. Das Manifest muss dem Schema entsprechen, das unter gehostet [`https://developer.microsoft.com/json-schemas/teams/v1.10/MicrosoftTeams.schema.json`]( https://developer.microsoft.com/json-schemas/teams/v1.10/MicrosoftTeams.schema.json) wird. Frühere Versionen 1.0, 1.1,..., 1.6 usw. werden ebenfalls unterstützt (mit "v1.x" in der URL).

Das folgende Schemabeispiel zeigt alle Erweiterbarkeitsoptionen:

## <a name="sample-full-manifest"></a>Beispiel-Vollmanifest

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
     "websiteUrl",
     "privacyUrl",
     "termsOfUseUrl"        
  ]              
}
```

Das Schema definiert die folgenden Eigenschaften:

## <a name="schema"></a>$schema

Optional, aber empfohlen — Zeichenfolge

Die https:// URL, die auf das JSON-Schema für das Manifest verweist.

## <a name="manifestversion"></a>manifestVersion

**Erforderlich** — Zeichenfolge

Die Version des Manifestschemas, die dieses Manifest verwendet. Es muss 1.10. sein.

## <a name="version"></a>Version

**Erforderlich** — Zeichenfolge

Die Version einer bestimmten App. Wenn Sie etwas in Ihrem Manifest aktualisieren, muss die Version ebenfalls erhöht werden. Auf diese Weise überschreibt das neue Manifest bei der Installation des neuen Manifests das vorhandene Manifest, und der Benutzer erhält die neue Funktionalität. Wenn diese App an den Store übermittelt wurde, muss das neue Manifest erneut übermittelt und erneut überprüft werden. Die App-Benutzer erhalten das neue aktualisierte Manifest automatisch innerhalb weniger Stunden nach der Genehmigung des Manifests.

Wenn sich die App-Anforderungen an Berechtigungen ändern, werden die Benutzer aufgefordert, ein Upgrade durchzuführen und die App erneut zu zustimmen.

Diese Versionszeichenfolge muss dem [Semver-Standard](http://semver.org/) (MAJOR. kleiner. PATCH).

## <a name="id"></a>id

**Erforderlich** – Microsoft App ID

Die ID ist ein eindeutiger von Microsoft generierter Bezeichner für die App. Sie haben eine ID, wenn Ihr Bot über die Microsoft Bot Framework registriert ist oder sich die Web-App Ihres Tabs bereits bei Microsoft anmeldet. Sie müssen die ID hier eingeben. Andernfalls müssen Sie eine neue ID im [Microsoft Application Registration Portal](https://aka.ms/appregistrations)generieren. Verwenden Sie dieselbe ID, wenn Sie einen Bot hinzufügen.

> [!NOTE]
> Wenn Sie ein Update für Ihre vorhandene App in AppSource übermitteln, darf die ID in Ihrem Manifest nicht geändert werden.

## <a name="developer"></a>developer

**Erforderlich** — Objekt

Gibt Informationen zu Ihrem Unternehmen an. Bei Apps, die an den Teams-Store gesendet werden, müssen diese Werte mit den Informationen in Ihrem Store-Eintrag übereinstimmen. Weitere Informationen finden Sie in den Richtlinien für die [Veröffentlichung Teams .-](~/concepts/deploy-and-publish/appsource/publish.md)

|Name| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|
|`name`|32 Zeichen|✔|Der Anzeigename für den Entwickler.|
|`websiteUrl`|2048 Zeichen|✔|Die https:// URL auf die Website des Entwicklers. Dieser Link muss Benutzer zu Ihrem Unternehmen oder Ihrer produktspezifischen Zielseite führen.|
|`privacyUrl`|2048 Zeichen|✔|Die https:// URL zur Datenschutzrichtlinie des Entwicklers.|
|`termsOfUseUrl`|2048 Zeichen|✔|Die https:// URL zu den Nutzungsbedingungen des Entwicklers.|
|`mpnId`|10 Zeichen| |**Optional** Die Microsoft Partner Network ID, die die Partnerorganisation identifiziert, die die App erstellen.|

## <a name="name"></a>name

**Erforderlich** — Objekt

Der Name Ihrer App-Erfahrung, der Benutzern im Teams angezeigt wird. Bei Apps, die an AppSource gesendet werden, müssen diese Werte mit den Informationen in Ihrem AppSource-Eintrag übereinstimmen. Die Werte von `short` und `full` müssen unterschiedlich sein.

|Name| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|
|`short`|30 Zeichen|✔|Der kurze Anzeigename für die App.|
|`full`|100 Zeichen||Der vollständige Name der App, der verwendet wird, wenn der vollständige App-Name 30 Zeichen überschreitet.|

## <a name="description"></a>description

**Erforderlich** — Objekt

Beschreibt Ihre App für Benutzer. Bei Apps, die an AppSource gesendet werden, müssen diese Werte mit den Informationen in Ihrem AppSource-Eintrag übereinstimmen.

Stellen Sie sicher, dass Ihre Beschreibung Ihre Erfahrung genau beschreibt und Informationen bereitstellt, die potenziellen Kunden helfen, ihre Erfahrung zu verstehen. Sie müssen in der vollständigen Beschreibung beachten, ob ein externes Konto für die Verwendung erforderlich ist. Die Werte von `short` und `full` müssen unterschiedlich sein. Ihre Kurzbeschreibung darf nicht innerhalb der langen Beschreibung wiederholt werden und darf keinen anderen App-Namen enthalten.

|Name| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|
|`short`|80 Zeichen|✔|Eine kurze Beschreibung Ihrer App-Erfahrung, die verwendet wird, wenn der Speicherplatz begrenzt ist.|
|`full`|4000 Zeichen|✔|Die vollständige Beschreibung Ihrer App.|

## <a name="packagename"></a>Packagename

**Optional** — Zeichenfolge

Ein eindeutiger Bezeichner für die App in umgekehrter Domänennotation; z. B. com.example.myapp. Maximale Länge: 64 Zeichen.

## <a name="localizationinfo"></a>lokalisierungInfo

**Optional** — Objekt

Ermöglicht die Angabe einer Standardsprache sowie Zeiger auf zusätzliche Sprachdateien. Weitere Informationen finden Sie unter [Lokalisierung](~/concepts/build-and-test/apps-localization.md).

|Name| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|
|`defaultLanguageTag`||✔|Das Sprachtag der Zeichenfolgen in dieser Manifestdatei der obersten Ebene.|

### <a name="localizationinfoadditionallanguages"></a>lokalisierungInfo.additionalSprachen

Ein Array von Objekten, die zusätzliche Sprachübersetzungen angeben.

|Name| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|
|`languageTag`||✔|Das Sprachtag der Zeichenfolgen in der bereitgestellten Datei.|
|`file`||✔|Ein relativer Dateipfad zu einer JSon-Datei, die die übersetzten Zeichenfolgen enthält.|

## <a name="icons"></a>Symbole

**Erforderlich** — Objekt

Symbole, die in der Teams-App verwendet werden. Die Symboldateien müssen als Teil des Upload-Pakets enthalten sein. Weitere Informationen finden Sie unter [Symbole.](../../concepts/build-and-test/apps-package.md#app-icons)

|Name| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|
|`outline`|32 x 32 Pixel|✔|Ein relativer Dateipfad zu einem transparenten 32x32 PNG-Umrisssymbol.|
|`color`|192 x 192 Pixel|✔|Ein relativer Dateipfad zu einem 192x192 PNG-Symbol in voller Farbe.|

## <a name="accentcolor"></a>accentFarbe

**Optional** — HTML Hex Farbcode

Eine Farbe, die in Verbindung mit und als Hintergrund für Ihre Gliederungssymbole verwendet werden soll.

Der Wert muss ein gültiger HTML-Farbcode sein, der z. B. mit ''' `#4464ee` beginnt.

## <a name="configurabletabs"></a>konfigurierbareTabs

**Optional** — Array

Wird verwendet, wenn Ihre App-Erfahrung über eine Teamkanal-Registerkarte verfügt, die eine zusätzliche Konfiguration erfordert, bevor sie hinzugefügt wird. Konfigurierbare Registerkarten werden nur im Teamsbereich unterstützt, und Sie können dieselben Registerkarten mehrmals konfigurieren. Sie können es jedoch nur einmal im Manifest definieren.

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`configurationUrl`|string|2048 Zeichen|✔|Die https:// URL, die beim Konfigurieren der Registerkarte verwendet werden soll.|
|`scopes`|Array von Enumeraten|1|✔|Derzeit unterstützen konfigurierbare Registerkarten nur die `team` `groupchat` und-Bereiche. |
|`canUpdateConfiguration`|boolean|||Ein Wert, der angibt, ob eine Instanz der Registerkartenkonfiguration vom Benutzer nach der Erstellung aktualisiert werden kann. Standard: **true**.|
|`context` |Array von Enumeraten|6 ||Der Satz von `contextItem` Bereichen, in denen eine [Registerkarte unterstützt wird](../../tabs/how-to/access-teams-context.md). Standard: **[channelTab, privateChatTab, meetingChatTab, meetingDetailsTab]**.|
|`sharePointPreviewImage`|Zeichenfolge|2048||Ein relativer Dateipfad zu einem Registerkartenvorschaubild zur Verwendung in SharePoint. Größe 1024x768. |
|`supportedSharePointHosts`|Array von Enumeraten|1||Definiert, wie Ihre Registerkarte in SharePoint verfügbar gemacht wird. Optionen sind `sharePointFullPage` und `sharePointWebPart` |

## <a name="statictabs"></a>staticTabs

**Optional** — Array

Definiert eine Reihe von Registerkarten, die standardmäßig "angeheftet" werden können, ohne dass der Benutzer sie manuell hinzufügt. Statische Registerkarten, die im `personal` Gültigkeitsbereich deklariert sind, werden immer an die persönliche Erfahrung der App angeheftet. Statische Registerkarten, die im Bereich deklariert `team` sind, werden derzeit nicht unterstützt.

Bei diesem Element handelt es sich um ein Array (maximal 16 Elemente) mit allen Elementen des Typs `object` . Dieser Block ist nur für Lösungen erforderlich, die eine statische Registerkartenlösung bereitstellen.

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`entityId`|string|64 Zeichen|✔|Ein eindeutiger Bezeichner für die Entität, die auf der Registerkarte angezeigt wird.|
|`name`|Zeichenfolge|128 Zeichen|✔|Der Anzeigename der Registerkarte in der Kanalschnittstelle.|
|`contentUrl`|Zeichenfolge||✔|Die https:// URL, die auf die Entitätsbenutzeroberfläche verweist, die im Teams-Canvas angezeigt werden soll.|
|`websiteUrl`|Zeichenfolge|||Die https:// URL, auf die angezeigt werden soll, wenn ein Benutzer sich für die Anzeige in einem Browser entscheidet.|
|`searchUrl`|Zeichenfolge|||Die https:// URL, auf die für die Suchabfragen eines Benutzers verweisen soll.|
|`scopes`|Array von Enumeraten|1|✔|Derzeit unterstützen statische Registerkarten nur den `personal` Bereich, d. h., er kann nur als Teil der persönlichen Erfahrung bereitgestellt werden.|
|`context` | Array von Enumeraten| 2|| Der Satz von `contextItem` Bereichen, in denen eine Registerkarte unterstützt wird.|

> [!NOTE]
>  Die searchUrl-Funktion ist für Drittanbieter-Entwickler nicht verfügbar.
> Wenn Ihre Registerkarten kontextabhängige Informationen zum Anzeigen relevanter Inhalte oder zum Einsieren eines Authentifizierungsflusses erfordern, finden Sie weitere Informationen unter [Kontext abrufen für Ihre Registerkarte Microsoft Teams](../../tabs/how-to/access-teams-context.md).

## <a name="bots"></a>Bots

**Optional** — Array

Definiert eine Bot-Lösung zusammen mit optionalen Informationen wie Standardbefehlseigenschaften.

Das Element ist ein Array (maximal nur 1 Element &mdash; ist derzeit nur ein Bot pro App erlaubt) mit allen Elementen des Typs `object` . Dieser Block ist nur für Lösungen erforderlich, die ein Bot-Erlebnis bieten.

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`botId`|string|64 Zeichen|✔|Die eindeutige Microsoft-App-ID für den Bot, wie bei Bot Framework registriert. Dies kann durchaus mit der gesamten [App-ID](#id)identisch sein.|
|`scopes`|Array von Enumeraten|3|✔|Gibt an, ob der Bot eine Umgebung im Kontext eines Kanals in einem `team` oder Gruppenchat (`groupchat`) ist, oder aber eine Umgebung einzig für einen bestimmten Benutzer (`personal`). Diese Optionen sind nicht exklusiv.|
|`needsChannelSelector`|boolean|||Beschreibt, ob der Bot einen Benutzerhinweis verwendet, um den Bot einem bestimmten Kanal hinzuzufügen. Standard: **`false`**|
|`isNotificationOnly`|boolean|||Gibt an, ob ein Bot ein unidirektionaler Bot ausschließlich für Benachrichtigungen ist (im Gegensatz zu einem dialogorientierten Bot). Standard: **`false`**|
|`supportsFiles`|boolean|||Gibt an, ob der Bot die Möglichkeit zum Hochladen/Herunterladen von Dateien in persönliche Chats unterstützt. Standard: **`false`**|
|`supportsCalling`|boolean|||Ein Wert, der angibt, wo ein Bot Audioanrufe unterstützt. **WICHTIG**: Diese Eigenschaft ist derzeit experimentell. Experimentelle Eigenschaften sind möglicherweise nicht vollständig und können Änderungen erfahren, bevor sie vollständig verfügbar sind.  Es wird nur zu Test- und Explorationszwecken bereitgestellt und darf nicht in Produktionsanwendungen verwendet werden. Standard: **`false`**|
|`supportsVideo`|boolean|||Ein Wert, der angibt, wo ein Bot Videoanrufe unterstützt. **WICHTIG**: Diese Eigenschaft ist derzeit experimentell. Experimentelle Eigenschaften sind möglicherweise nicht vollständig und können Änderungen erfahren, bevor sie vollständig verfügbar sind.  Es wird nur zu Test- und Explorationszwecken bereitgestellt und darf nicht in Produktionsanwendungen verwendet werden. Standard: **`false`**|

### <a name="botscommandlists"></a>bots.commandListen

Eine optionale Liste von Befehlen, die Ihr Bot Benutzern empfehlen kann. Das Objekt ist ein Array (maximal 2 Elemente) mit allen Elementen des `object` Typs; Sie müssen eine separate Befehlsliste für jeden Bereich definieren, den Ihr Bot unterstützt. Weitere Informationen finden Sie in [Bot-Menüs.](~/bots/how-to/create-a-bot-commands-menu.md)

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`items.scopes`|Array von Enumeraten|3|✔|Gibt den Bereich an, für den die Befehlsliste gültig ist. Mögliche Optionen sind `team`, `personal` und `groupchat`.|
|`items.commands`|Array von Objekten|10|✔|Ein Array von Befehlen, die der Bot unterstützt:<br>`title`: Name des Bot-Befehls (string, 32)<br>`description`: eine einfache Beschreibung oder ein Beispiel für die Befehlssyntax und ihr Argument (Zeichenfolge, 128).|

### <a name="botscommandlistscommands"></a>bots.commandLists.commands

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|title|string|12 |✔|Der Bot-Befehlsname.|
|description|Zeichenfolge|128 Zeichen|✔|Eine einfache Textbeschreibung oder ein Beispiel für die Befehlssyntax und ihre Argumente.|

## <a name="connectors"></a>Steckverbinder

**Optional** — Array

Der `connectors` Block definiert einen Office 365 Connector für die App.

Das Objekt ist ein Array (maximal 1 Element) mit allen Elementen des Typs `object` . Dieser Block ist nur für Lösungen erforderlich, die einen Connector bereitstellen.

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`configurationUrl`|string|2048 Zeichen|✔|Die https:// URL, die beim Konfigurieren des Connectors verwendet werden soll.|
|`scopes`|Array von Enumeraten|1|✔|Gibt an, ob der Connector eine Erfahrung im Kontext eines Kanals in einem bietet, oder eine Erfahrung, die nur für einen einzelnen Benutzer ( ) `team` gilt. `personal` Derzeit wird nur der `team` Bereich unterstützt.|
|`connectorId`|Zeichenfolge|64 Zeichen|✔|Ein eindeutiger Bezeichner für den Connector, der mit seiner ID im [Connectors Developer Dashboard](https://aka.ms/connectorsdashboard)übereinstimmt.|

## <a name="composeextensions"></a>composeExtensions

**Optional** — Array

Definiert eine Messagingerweiterung für die App.

> [!NOTE]
> Der Name des Features wurde im November 2017 von "Komponenerweiterung" in "Messaging-Erweiterung" geändert, aber der Manifestname bleibt derselbe, sodass vorhandene Erweiterungen weiterhin funktionieren.

Das Element ist ein Array (maximal 1 Element) mit allen Elementen des Typs `object` . Dieser Block ist nur für Lösungen erforderlich, die eine Messagingerweiterung bereitstellen.

|Name| Typ | Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`botId`|string|64|✔|Die eindeutige Microsoft-App-ID für den Bot, die die Messagingerweiterung unterstützt, wie sie im Bot Framework registriert ist. Dies kann durchaus mit der gesamten App-ID identisch sein.|
|`commands`|Array von Objekten|10|✔|Array von Befehlen, die von der Messagingerweiterung unterstützt werden.|
|`canUpdateConfiguration`|boolean|||Ein Wert, der angibt, ob die Konfiguration einer Messagingerweiterung vom Benutzer aktualisiert werden kann. Standard: **False**.|
|`messageHandlers`|Array von Objekten|5 ||Eine Liste von Handlern, mit denen Apps aufgerufen werden können, wenn bestimmte Bedingungen erfüllt sind.|
|`messageHandlers.type`|Zeichenfolge|||Der Typ des Nachrichtenhandlers. Muss `"link"` sein.|
|`messageHandlers.value.domains`|Array von Strings|||Array von Domänen, für die der Linknachrichtenhandler registrieren kann.|

### <a name="composeextensionscommands"></a>composeExtensions.commands

Ihre Messagingerweiterung muss einen oder mehrere Befehle deklarieren. Jeder Befehl wird in Microsoft Teams als potenzielle Interaktion vom UI-basierten Einstiegspunkt angezeigt. Es gibt maximal 10 Befehle.

Jedes Befehlselement ist ein Objekt mit der folgenden Struktur:

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`id`|string|64 Zeichen|✔|Die ID für den Befehl.|
|`title`|Zeichenfolge|32 Zeichen|✔|Der benutzerfreundliche Befehlsname.|
|`type`|Zeichenfolge|64 Zeichen||Typ des Befehls. Einer von `query` oder `action` . Standard: **Abfrage**.|
|`description`|Zeichenfolge|128 Zeichen||Die Beschreibung, die Benutzern angezeigt wird, um den Zweck dieses Befehls anzugeben.|
|`initialRun`|boolean|||Ein boolescher Wert gibt an, ob der Befehl anfänglich ohne Parameter ausgeführt wird. Der Standardwert ist **false**.|
|`context`|Array von Strings|3||Definiert, von wo aus die Nachrichtenerweiterung aufgerufen werden kann. Jede Beliebige Kombination von `compose` , `commandBox` . `message` Der Standardwert ist `["compose","commandBox"]`.|
|`fetchTask`|boolean|||Ein boolescher Wert, der angibt, ob er das Taskmodul dynamisch abrufen muss. Der Standardwert ist **false**.|
|`taskInfo`|Objekt|||Geben Sie den Taskmodul an, der vorab geladen werden soll, wenn ein Messagingerweiterungsbefehl verwendet wird.|
|`taskInfo.title`|Zeichenfolge|64 Zeichen||Erster Dialogtitel.|
|`taskInfo.width`|Zeichenfolge|||Dialogbreite - entweder eine Zahl in Pixel oder ein Standardlayout wie 'large', 'medium' oder 'small'.|
|`taskInfo.height`|Zeichenfolge|||Dialoghöhe - entweder eine Zahl in Pixel oder ein Standardlayout wie 'large', 'medium' oder 'small'.|
|`taskInfo.url`|Zeichenfolge|||Erste Webview-URL.|
|`parameters`|Array des Objekts|5 Artikel|✔|Die Liste der Parameter, die der Befehl verwendet. Minimum: 1; maximal: 5.|
|`parameters.name`|Zeichenfolge|64 Zeichen|✔|Der Name des Parameters, wie er im Client angezeigt wird. Dies ist in der Benutzeranforderung enthalten.|
|`parameters.title`|Zeichenfolge|32 Zeichen|✔|Benutzerfreundlicher Titel für den Parameter.|
|`parameters.description`|Zeichenfolge|128 Zeichen||Benutzerfreundliche Zeichenfolge, die den Zweck dieses Parameters beschreibt.|
|`parameters.value`|Zeichenfolge|512 Zeichen||Anfangswert für den Parameter.|
|`parameters.inputType`|Zeichenfolge|128 Zeichen||Definiert den Typ des Steuerelements, das in einem Taskmodul für angezeigt `fetchTask: true` wird. Einer von `text, textarea, number, date, time, toggle, choiceset` .|
|`parameters.choices`|Array von Objekten|10 Artikel||Die Auswahloptionen für die `choiceset` . Nur verwenden, wenn `parameter.inputType` es sich um `choiceset` .|
|`parameters.choices.title`|Zeichenfolge|128 Zeichen|✔|Titel der Wahl.|
|`parameters.choices.value`|Zeichenfolge|512 Zeichen|✔|Value of the choice.|

## <a name="permissions"></a>Berechtigungen

**Optional** — Array von Zeichenfolgen

Ein Array, dessen `string` Berechtigung die App anfordert, damit Endbenutzer wissen, wie die Erweiterung funktioniert. Die folgenden Optionen sind nicht exklusiv:

* `identity`&emsp;Erfordert Benutzeridentitätsinformationen.
* `messageTeamMembers`&emsp;Erfordert die Berechtigung zum Senden direkter Nachrichten an Teammitglieder.

Wenn Sie diese Berechtigungen während der App-Aktualisierung ändern, werden die Zustimmungsprozesse von Benutzern wiederholt, nachdem sie die aktualisierte App ausgeführt haben. Weitere Informationen finden Sie unter [Aktualisieren Ihrer App.](~/concepts/deploy-and-publish/appsource/post-publish/overview.md)

## <a name="devicepermissions"></a>devicePermissions

**Optional** — Array von Zeichenfolgen

Stellt die systemeigenen Features auf dem Gerät eines Benutzers bereit, auf die Ihre App Zugriff anfordert. Mögliche Optionen sind:

* `geolocation`
* `media`
* `notifications`
* `midi`
* `openExternal`

## <a name="validdomains"></a>validDomains

**Optional**, außer **Erforderlich,** sofern angegeben.

Eine Liste gültiger Domänen für Websites, die die App im Teams Client laden soll. Domänenlisten können Platzhalter enthalten, z. `*.example.com` B. . Dies entspricht genau einem Segment der Domäne; wenn Sie übereinstimmen müssen, `a.b.example.com` verwenden Sie `*.*.example.com` . Wenn Ihre Registerkartenkonfiguration oder Inhaltsbenutzeroberfläche zu einer anderen Domäne als der für die Registerkartenkonfiguration verwendenden Domäne navigieren muss, muss diese Domäne hier angegeben werden.

Es ist **nicht** erforderlich, die Domänen von Identitätsanbietern, die Sie unterstützen möchten, in Ihre App aufzunehmen. Um sich beispielsweise mit einer Google-ID zu authentifizieren, muss sie zu accounts.google.com umleiten, Sie dürfen jedoch accounts.google.com nicht in `validDomains[]` .

Teams Apps, für die eigene Sharepoint-URLs gut funktionieren, enthält in ihrer gültigen Domänenliste die Liste "-teamsitedomain".

> [!IMPORTANT]
> Fügen Sie keine Domänen hinzu, die sich außerhalb Ihres Steuerelements befinden, weder direkt noch über Platzhalter. Zum Beispiel `yourapp.onmicrosoft.com` ist gültig, ist jedoch `*.onmicrosoft.com` nicht gültig.

Das Objekt ist ein Array mit allen Elementen des Typs `string` .

## <a name="webapplicationinfo"></a>webApplicationInfo

**Optional** — Objekt

Geben Sie Ihre Azure Active Directory (AAD)-App-ID und Microsoft-Graph-Informationen an, damit sich Benutzer nahtlos bei Ihrer App anmelden können. Wenn Ihre App in AAD registriert ist, müssen Sie die App-ID angeben, damit Administratoren Berechtigungen und Zustimmung in Teams Admin Center problemlos überprüfen können.

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`id`|string|36 Zeichen|✔|AAD-Anwendungs-ID der App. Diese ID muss eine GUID sein.|
|`resource`|Zeichenfolge|2048 Zeichen|✔|Ressourcen-URL der App zum Abrufen eines Authentifizierungstokens für SSO. </br> **HINWEIS:** Wenn Sie SSO nicht verwenden, stellen Sie sicher, dass Sie einen Dummy-Zeichenfolgenwert in dieses Feld in Ihr App-Manifest eingeben, um z. https://notapplicable B. eine Fehlerantwort zu vermeiden. |
|`applicationPermissions`|array of strings|128 Zeichen||Geben Sie eine granulare [ressourcenspezifische Zustimmung an.](../../graph-api/rsc/resource-specific-consent.md#resource-specific-permissions)|

## <a name="showloadingindicator"></a>showLoadingIndicator

**Optional** — boolesch

Gibt an, ob die Ladeanzeige angezeigt werden soll, wenn eine App oder Registerkarte geladen wird. Der Standardwert ist **false**.
>[!NOTE]
>Wenn Sie `showLoadingIndicator` in Ihrem App-Manifest true auswählen, ändern Sie die Inhaltsseiten Ihrer Registerkarten und Aufgabenmodule, wie unter [Anzeigen eines systemeigenen Ladeindikatordokuments](../../tabs/how-to/create-tab-pages/content-page.md#show-a-native-loading-indicator) anzeigen beschrieben, um die Seite richtig zu laden.


## <a name="isfullscreen"></a>isFullScreen

 **Optional** — boolesch

Geben Sie an, wo eine persönliche App mit oder ohne Tab-Headerleiste gerendert wird. Der Standardwert ist **false**.

## <a name="activities"></a>Aktivitäten

**Optional** — Objekt

Definieren Sie die Eigenschaften, die Ihre App zum Buchen eines Benutzeraktivitätsfeeds verwendet.

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`activityTypes`|Array von Objekten|128 Artikel| | Geben Sie die Arten von Aktivitäten an, die Ihre App in einem Benutzeraktivitätsfeed bereitstellen kann.|

### <a name="activitiesactivitytypes"></a>aktivitäten.activityTypen

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`type`|string|32 Zeichen|✔|Der Benachrichtigungstyp. *Siehe unten*.|
|`description`|Zeichenfolge|128 Zeichen|✔|Eine kurze Beschreibung der Meldung. *Siehe unten*.|
|`templateText`|Zeichenfolge|128 Zeichen|✔|Ex: "-actor" erstellte Aufgabe 'taskId' für Sie"|

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


