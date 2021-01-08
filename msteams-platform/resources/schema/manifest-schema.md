---
title: Manifest-Schemareferenz
description: Beschreibung des manifest-Schemas für Microsoft Teams
keywords: Team Manifest-Schema
author: laujan
ms.author: lajanuar
ms.openlocfilehash: c66add190b0492170acf9756980ee16fb1fdf1fd
ms.sourcegitcommit: 5f1d6c12d80d48f403b73586f68bacf15785c855
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 12/30/2020
ms.locfileid: "49739056"
---
# <a name="reference-manifest-schema-for-microsoft-teams"></a>Referenz: Manifest-Schema für Microsoft Teams

Das Microsoft Teams-Manifest beschreibt, wie die app in das Microsoft Teams-Produkt integriert wird. Das Manifest muss dem Schema entsprechen, das unter gehostet wird [`https://developer.microsoft.com/json-schemas/teams/v1.8/MicrosoftTeams.schema.json`]( https://developer.microsoft.com/json-schemas/teams/v1.8/MicrosoftTeams.schema.json) . Frühere Versionen 1.0-1.4 werden ebenfalls unterstützt (mit "v1. x" in der URL).

Das folgende Schemabeispiel zeigt alle Erweiterungsoptionen.

## <a name="sample-full-manifest"></a>Vollständiges Beispiel Manifest

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

*Optional, jedoch empfohlen* – Zeichenfolge

Die https://-URL, die auf das JSON-Schema für das Manifest verweist.

## <a name="manifestversion"></a>manifestVersion

**Erforderlich** – Zeichenfolge

Die Version des manifest-Schemas, die dieses Manifest verwendet. Es sollte "1,7" sein.

## <a name="version"></a>Version

**Erforderlich** – Zeichenfolge

Die Version der jeweiligen App. Wenn Sie etwas in ihrem Manifest aktualisieren, muss die Version ebenfalls inkrementiert werden. Auf diese Weise wird bei der Installation des neuen Manifests das vorhandene überschrieben, und der Benutzer erhält die neue Funktionalität. Wenn diese APP an den Store übermittelt wurde, muss das neue Manifest erneut übermittelt und erneut validiert werden. Dann erhalten Benutzer dieser APP das neue aktualisierte Manifest automatisch in ein paar Stunden, nachdem es genehmigt wurde.

Wenn sich die angeforderte APP geändert hat, werden die Benutzer aufgefordert, die APP zu aktualisieren und erneut zu genehmigen.

Diese Versionszeichenfolge muss dem [semver](http://semver.org/) -Standard (Major) entsprechen. Moll. Patch).

## <a name="id"></a>id

**Erforderlich** – Microsoft App-ID

Der eindeutige von Microsoft generierte Bezeichner für diese APP. Wenn Sie einen bot über das Microsoft bot-Framework registriert haben oder sich die Webanwendung Ihrer Registerkarte bereits bei Microsoft anmeldet, sollten Sie bereits über eine ID verfügen und diese hier eingeben. Andernfalls sollten Sie eine neue ID im Microsoft-Anwendungs Registrierungs Portal ([meine Anwendungen](https://apps.dev.microsoft.com)) generieren, Sie hier eingeben und dann wieder verwenden, wenn Sie einen bot hinzufügen. Hinweis: Wenn Sie ein Update an Ihre vorhandene app in AppSource übermitteln, darf die ID in ihrem Manifest nicht geändert werden.

## <a name="developer"></a>developer

**Erforderlich** – Objekt

Gibt Informationen zu Ihrem Unternehmen an. Für an AppSource übermittelte Apps (ehemals Office Store) müssen diese Werte mit den Informationen in Ihrem AppSource-Eintrag übereinstimmen. Weitere Informationen finden Sie in unseren [Veröffentlichungsrichtlinien](~/concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md) .

|Name| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|
|`name`|32 Zeichen|✔|Der Anzeigename für den Entwickler.|
|`websiteUrl`|2048 Zeichen|✔|Die https://-URL zur Website des Entwicklers. Dieser Link sollte Benutzer zu Ihrer Firma oder produktspezifischen Zielseite führen.|
|`privacyUrl`|2048 Zeichen|✔|Die https://-URL zur Datenschutzrichtlinie des Entwicklers.|
|`termsOfUseUrl`|2048 Zeichen|✔|Die https://-URL zu den Nutzungsbedingungen des Entwicklers.|
|`mpnId`|10 Zeichen| |**Optional** Die Microsoft Partner-Netzwerk-ID, die die Partnerorganisation identifiziert, die die APP aufbaut.|

## <a name="name"></a>Name

**Erforderlich** – Objekt

Der Name der APP-Erfahrung, der Benutzern in der Microsoft Teams-Benutzeroberfläche angezeigt wird. Für apps, die an AppSource übermittelt werden, müssen diese Werte mit den Informationen in Ihrem AppSource-Eintrag übereinstimmen. Die Werte von `short` und `full` sollten nicht identisch sein.

|Name| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|
|`short`|30 Zeichen|✔|Der kurze Anzeigename für die app.|
|`full`|100 Zeichen||Der vollständige Name der APP, der verwendet wird, wenn der vollständige App-Name 30 Zeichen überschreitet.|

## <a name="description"></a>description

**Erforderlich** – Objekt

Beschreibt die APP für Benutzer. Für apps, die an AppSource übermittelt werden, müssen diese Werte mit den Informationen in Ihrem AppSource-Eintrag übereinstimmen.

Stellen Sie sicher, dass Ihre Beschreibung ihre Erfahrung genau beschreibt und Informationen bereitstellt, um potenziellen Kunden zu helfen, ihre Erfahrungen zu verstehen. Beachten Sie auch, dass in der vollständigen Beschreibung ein externes Konto zur Verwendung benötigt wird. Die Werte von `short` und `full` sollten nicht identisch sein.  Ihre Kurzbeschreibung darf nicht innerhalb der langen Beschreibung wiederholt werden und darf keinen anderen APP-Namen enthalten.

|Name| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|
|`short`|80 Zeichen|✔|Eine kurze Beschreibung Ihrer APP-Erfahrung, die verwendet wird, wenn der Speicherplatz limitiert ist.|
|`full`|4000 Zeichen|✔|Die vollständige Beschreibung Ihrer APP.|

## <a name="packagename"></a>PackageName

**Optional** – Zeichenfolge

Ein eindeutiger Bezeichner für diese APP in umgekehrter Domänen Notation; Beispiel: com. Beispiel. MyApp. Maximale Länge: 64 Zeichen.

## <a name="localizationinfo"></a>localizationInfo

**Optional** – Objekt

Ermöglicht die Angabe einer Standardsprache sowie Zeiger auf zusätzliche Sprachdateien. Siehe [Lokalisierung](~/concepts/build-and-test/apps-localization.md).

|Name| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|
|`defaultLanguageTag`||✔|Das Language-Tag der Zeichenfolgen in dieser Manifestdatei der obersten Ebene.|

### <a name="localizationinfoadditionallanguages"></a>localizationInfo.additionalLanguages

Ein Array von Objekten, das zusätzliche Sprachübersetzungen angibt.

|Name| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|
|`languageTag`||✔|Das Language-Tag der Zeichenfolgen in der bereitgestellten Datei.|
|`file`||✔|Ein relativer Dateipfad zu einer JSON-Datei, die die übersetzten Zeichenfolgen enthält.|

## <a name="icons"></a>Symbole

**Erforderlich** – Objekt

Symbole, die in der Teams-App verwendet werden. Die Symboldateien müssen als Teil des Upload-Pakets enthalten sein. Weitere Informationen finden Sie unter [Icons](../../concepts/build-and-test/apps-package.md#app-icons) .

|Name| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|
|`outline`|32 x 32 Pixel|✔|Ein relativer Dateipfad zu einem transparenten 32x32 PNG-Gliederungssymbol.|
|`color`|192 x 192 Pixel|✔|Ein relativer Dateipfad zu einem vollfarbigen 192x192 PNG-Symbol.|

## <a name="accentcolor"></a>accentColor

**Optional** – HTML-Hex-Farbcode

Eine Farbe, die in Verbindung mit und als Hintergrund für die Gliederungssymbole verwendet werden soll.

Der Wert muss ein gültiger HTML-Farb Code sein, der mit "#" beginnt, beispielsweise `#4464ee` .

## <a name="configurabletabs"></a>configurableTabs

**Optional** – Array

Wird verwendet, wenn Ihre APP-Erfahrung eine Team Kanal-registerkartenoberfläche aufweist, die eine zusätzliche Konfiguration erfordert, bevor Sie hinzugefügt wird. Konfigurierbare Registerkarten werden nur im Bereich Teams (nicht persönlich) unterstützt, und derzeit wird nur **eine** Registerkarte pro App unterstützt.

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`configurationUrl`|string|2048 Zeichen|✔|Die https://-URL, die beim Konfigurieren der Registerkarte verwendet werden soll.|
|`scopes`|Array von Enumerationen|1 |✔|Derzeit unterstützen konfigurierbare Registerkarten nur die `team` `groupchat` Bereiche und. |
|`canUpdateConfiguration`|Boolescher Wert|||Ein Wert, der angibt, ob eine Instanz der Konfiguration der Registerkarte nach der Erstellung vom Benutzer aktualisiert werden kann. Default: **true**.|
|`context` |Array von Enumerationen|6 ||Die Gruppe von `contextItem` Bereichen, in denen eine Registerkarte unterstützt wird. Standardwert: **[channelTab, privateChatTab, meetingChatTab, meetingDetailsTab]**.|
|`sharePointPreviewImage`|Zeichenfolge|2048||Ein relativer Dateipfad zu einem Vorschaubild für die Registerkarte für die Verwendung in SharePoint. Größe 1024x768. |
|`supportedSharePointHosts`|Array von Enumerationen|1 ||Definiert, wie die Registerkarte in SharePoint zur Verfügung gestellt wird. Optionen sind `sharePointFullPage` und `sharePointWebPart` |

## <a name="statictabs"></a>staticTabs

**Optional** – Array

Definiert eine Gruppe von Registerkarten, die standardmäßig "fixiert" werden können, ohne dass der Benutzer Sie manuell hinzufügt. Im Bereich deklarierte statische Registerkarten `personal` werden immer an die persönliche Benutzeroberfläche der APP angeheftet. Im Bereich deklarierte statische Registerkarten `team` werden derzeit nicht unterstützt.

Dieses Element ist ein Array (maximal 16 Elemente) mit allen Elementen des Typs `object` . Dieser Block ist nur für Lösungen erforderlich, die eine statische Registerkarten Lösung bereitstellen.

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`entityId`|string|64 Zeichen|✔|Ein eindeutiger Bezeichner für die Entität, die auf der Registerkarte angezeigt wird.|
|`name`|Zeichenfolge|128 Zeichen|✔|Der Anzeigename der Registerkarte in der Kanalschnittstelle.|
|`contentUrl`|Zeichenfolge||✔|Die https://-URL, die auf die Benutzeroberfläche der Entität zeigt, die im Canvas "Teams" angezeigt werden soll.|
|`websiteUrl`|Zeichenfolge|||Die https://-URL, auf die verwiesen wird, wenn ein Benutzer sich für die Anzeige in einem Browser entscheidet.|
|`searchUrl`|Zeichenfolge|||Die https://-URL, auf die für Suchabfragen eines Benutzers verwiesen wird.|
|`scopes`|Array von Enumerationen|1 |✔|Derzeit unterstützen statische Registerkarten nur den `personal` Bereich, was bedeutet, dass Sie nur als Teil der persönlichen Benutzeroberfläche vorgesehen werden kann.|
|`context` | Array von Enumerationen| 2 || Die Gruppe von `contextItem` Bereichen, in denen eine Registerkarte unterstützt wird.|

> [!NOTE]
> Wenn auf Ihren Registerkartenkontext abhängige Informationen zum Anzeigen relevanter Inhalte oder zum Initiieren eines Authentifizierungs Flusses erforderlich sind, *Lesen Sie* den [Bereich Kontext für Ihre Microsoft Teams-Registerkarte abrufen](../../tabs/how-to/access-teams-context.md).

## <a name="bots"></a>Bots

**Optional** – Array

Definiert eine bot-Lösung zusammen mit optionalen Informationen wie Standardbefehls Eigenschaften.

Das Element ist ein Array (Maximum von nur 1 Element &mdash; , das derzeit nur ein bot pro App zulässig ist) mit allen Elementen des Typs `object` . Dieser Block ist nur für Lösungen erforderlich, die eine bot-Erfahrung bieten.

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`botId`|string|64 Zeichen|✔|Die eindeutige Microsoft-App-ID für den Bot, wie bei Bot Framework registriert. Dies kann auch die gesamte [App-ID](#id)entsprechen.|
|`scopes`|Array von Enumerationen|3 |✔|Gibt an, ob der Bot eine Umgebung im Kontext eines Kanals in einem `team` oder Gruppenchat (`groupchat`) ist, oder aber eine Umgebung einzig für einen bestimmten Benutzer (`personal`). Diese Optionen sind nicht exklusiv.|
|`needsChannelSelector`|Boolescher Wert|||Beschreibt, ob der Bot einen Benutzerhinweis verwendet, um den Bot einem bestimmten Kanal hinzuzufügen. Standard **`false`**|
|`isNotificationOnly`|Boolescher Wert|||Gibt an, ob ein Bot ein unidirektionaler Bot ausschließlich für Benachrichtigungen ist (im Gegensatz zu einem dialogorientierten Bot). Standard **`false`**|
|`supportsFiles`|Boolescher Wert|||Gibt an, ob der Bot die Möglichkeit zum Hochladen/Herunterladen von Dateien in persönliche Chats unterstützt. Standard **`false`**|
|`supportsCalling`|Boolescher Wert|||Ein Wert, der angibt, wo ein bot Audio-Anrufe unterstützt. **Wichtig**: Diese Eigenschaft ist derzeit experimentell. Experimentelle Eigenschaften sind möglicherweise nicht vollständig und können Änderungen unterzogen werden, bevor Sie vollständig verfügbar werden.  Sie wird nur zu Test-und Explorations Zwecken bereitgestellt und sollte nicht in Produktionsanwendungen verwendet werden. Standard **`false`**|
|`supportsVideo`|Boolescher Wert|||Ein Wert, der angibt, wo ein bot Videoanrufe unterstützt. **Wichtig**: Diese Eigenschaft ist derzeit experimentell. Experimentelle Eigenschaften sind möglicherweise nicht vollständig und können Änderungen unterzogen werden, bevor Sie vollständig verfügbar werden.  Sie wird nur zu Test-und Explorations Zwecken bereitgestellt und sollte nicht in Produktionsanwendungen verwendet werden. Standard **`false`**|

### <a name="botscommandlists"></a>Bots. commandLists

Eine optionale Liste von Befehlen, die ihr bot Benutzern empfehlen kann. Das Objekt ist ein Array (Maximum von 2 Elementen) mit allen Elementen des Typs `object` ; Sie müssen für jeden Bereich, den Ihr bot unterstützt, eine separate Befehlsliste definieren. Weitere Informationen finden Sie unter [bot-Menüs](~/bots/how-to/create-a-bot-commands-menu.md) .

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`items.scopes`|Array von Enumerationen|3 |✔|Gibt den Bereich an, für den die Befehlsliste gültig ist. Mögliche Optionen sind `team`, `personal` und `groupchat`.|
|`items.commands`|Array von Objekten|10 |✔|Ein Array von Befehlen, die der Bot unterstützt:<br>`title`: Name des Bot-Befehls (string, 32)<br>`description`: einfache Beschreibung oder Beispiel für die Befehlssyntax und zugehörige Argumente (string, 128)|

### <a name="botscommandlistscommands"></a>Bots. commandLists. Commands

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|title|string|12 |✔|Der Name des bot-Befehls|
|description|Zeichenfolge|128 Zeichen|✔|Eine einfache Textbeschreibung oder ein Beispiel für die Befehlssyntax und ihre Argumente.|

## <a name="connectors"></a>Connectors

**Optional** – Array

Der `connectors` Block definiert einen Office 365-Konnektor für die app.

Das Objekt ist ein Array (Maximum of 1-Element) mit allen Elementen des Typs `object` . Dieser Block ist nur für Lösungen erforderlich, die einen Connector bereitstellen.

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`configurationUrl`|string|2048 Zeichen|✔|Die https://-URL, die beim Konfigurieren des Connectors verwendet werden soll.|
|`scopes`|Array von Enumerationen|1 |✔|Gibt an, ob der Connector eine Erfahrung im Kontext eines Kanals in a bietet `team` oder ein Erlebnis, das allein auf einen einzelnen Benutzer beschränkt ist ( `personal` ). Derzeit wird nur der `team` Bereich unterstützt.|
|`connectorId`|Zeichenfolge|64 Zeichen|✔|Ein eindeutiger Bezeichner für den Connector, der seiner ID im [Entwickler Dashboard für Connectors](https://aka.ms/connectorsdashboard)entspricht.|

## <a name="composeextensions"></a>composeExtensions

**Optional** – Array

Definiert eine Messaging Erweiterung für die app.

> [!NOTE]
> Der Name des Features wurde von "Erstell Erweiterung" in "Messaging Extension" im November 2017 geändert, aber der Manifestname bleibt unverändert, sodass vorhandene Erweiterungen weiterhin funktionieren.

Das Element ist ein Array (Maximum of 1-Element) mit allen Elementen des Typs `object` . Dieser Block ist nur für Lösungen erforderlich, die eine Messaging Erweiterung bereitstellen.

|Name| Typ | Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`botId`|string|64|✔|Die eindeutige Microsoft-App-ID für den bot, der die Messaging Erweiterung unterstützt, wie Sie mit dem bot-Framework registriert wurde. Dies kann auch die gesamte APP-ID entsprechen.|
|`commands`|Array von Objekten|10 |✔|Array von Befehlen, die von der Messaging-Erweiterung unterstützt werden|
|`canUpdateConfiguration`|Boolescher Wert|||Ein Wert, der angibt, ob die Konfiguration einer Messaging Erweiterung vom Benutzer aktualisiert werden kann. Standard: **False**.|
|`messageHandlers`|Array von Objekten|5 ||Eine Liste von Handlern, mit denen apps aufgerufen werden können, wenn bestimmte Bedingungen erfüllt sind. Domänen müssen ebenfalls in aufgeführt sein. `validDomains`|
|`messageHandlers.type`|Zeichenfolge|||Der Typ des Nachrichten Handlers. Muss `"link"` sein.|
|`messageHandlers.value.domains`|Array von Zeichenfolgen|||Array von Domänen, für die der Link Nachrichtenhandler registriert werden kann.|

### <a name="composeextensionscommands"></a>composeExtensions. Commands

Ihre Messaging Erweiterung sollte einen oder mehrere Befehle deklarieren. Jeder Befehl wird in Microsoft Teams als potenzielle Interaktion aus dem Benutzeroberflächen basierten Einstiegspfad angezeigt. Es gibt maximal 10 Befehle.

Jedes Command-Element ist ein Objekt mit der folgenden Struktur:

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`id`|string|64 Zeichen|✔|Die ID für den Befehl.|
|`title`|Zeichenfolge|32 Zeichen|✔|Der benutzerfreundliche Befehlsname.|
|`type`|Zeichenfolge|64 Zeichen||Der Typ des Befehls. Einer von `query` oder `action` . Standard: **Query**.|
|`description`|Zeichenfolge|128 Zeichen||Die Beschreibung, die den Benutzern angezeigt wird, um den Zweck dieses Befehls anzugeben.|
|`initialRun`|Boolescher Wert|||Ein boolescher Wert, der angibt, ob der Befehl anfänglich ohne Parameter ausgeführt werden soll. Standard: **False**.|
|`context`|Array von Zeichenfolgen|3 ||Definiert, woher die Nachrichten Erweiterung aufgerufen werden kann. Eine beliebige Kombination von `compose` , `commandBox` , `message` . Der Standardwert lautet `["compose","commandBox"]`.|
|`fetchTask`|Boolescher Wert|||Ein boolescher Wert, der angibt, ob das Aufgabenmodul dynamisch abgerufen werden soll. Standard: **False**.|
|`taskInfo`|Objekt|||Geben Sie das Aufgabenmodul an, das beim Verwenden eines Messaging Erweiterungs Befehls vorab zu laden ist.|
|`taskInfo.title`|Zeichenfolge|64 Zeichen||Ursprünglicher Dialogtitel.|
|`taskInfo.width`|Zeichenfolge|||Dialog Breite-entweder eine Zahl in Pixel oder ein Standardlayout wie "Large", "Medium" oder "Small".|
|`taskInfo.height`|Zeichenfolge|||Dialog Feld Höhe: entweder eine Zahl in Pixel oder ein Standardlayout wie "Large", "Medium" oder "Small".|
|`taskInfo.url`|Zeichenfolge|||Anfängliche WebView-URL.|
|`parameters`|Array von Object|5 Elemente|✔|Die Liste der Parameter, die der Befehl benötigt. Minimum: 1; Maximum: 5.|
|`parameters.name`|Zeichenfolge|64 Zeichen|✔|Der Name des Parameters, wie er im Client angezeigt wird. Dies ist in der Benutzeranforderung enthalten.|
|`parameters.title`|Zeichenfolge|32 Zeichen|✔|Benutzerfreundlicher Titel für den Parameter.|
|`parameters.description`|Zeichenfolge|128 Zeichen||Benutzerfreundliche Zeichenfolge, die den Zweck dieses Parameters beschreibt.|
|`parameters.value`|Zeichenfolge|512 Zeichen||Anfangswert für den Parameter.|
|`parameters.inputType`|Zeichenfolge|128 Zeichen||Definiert den Typ des Steuerelements, das in einem Aufgabenmodul für angezeigt wird `fetchTask: true` . Einer von `text, textarea, number, date, time, toggle, choiceset` .|
|`parameters.choices`|Array von Objekten|10 Elemente||Die Auswahloptionen für `choiceset` . Nur verwenden `parameter.inputType` , wenn ist `choiceset` .|
|`parameters.choices.title`|Zeichenfolge|128 Zeichen|✔|Titel der Auswahl.|
|`parameters.choices.value`|Zeichenfolge|512 Zeichen|✔|Value of the choice.|

## <a name="permissions"></a>Berechtigungen

**Optional** – Array von Zeichenfolgen

Ein Array, das `string` angibt, welche Berechtigungen die APP anfordert, sodass Endbenutzer wissen, wie die Erweiterung ausgeführt wird. Die folgenden Optionen sind nicht exklusiv:

* `identity`&emsp;Erfordert Benutzeridentitätsinformationen
* `messageTeamMembers`&emsp;Erfordert die Berechtigung zum Senden von direkten Nachrichten an Teammitglieder.

Wenn Sie diese Berechtigungen beim Aktualisieren Ihrer APP ändern, werden die Benutzer beim ersten Ausführen der aktualisierten App den Zustimmungsprozess wiederholen. Weitere Informationen finden Sie unter [Aktualisieren Ihrer APP](~/concepts/deploy-and-publish/appsource/post-publish/overview.md) .

## <a name="devicepermissions"></a>devicePermissions

**Optional** – Array von Zeichenfolgen

Gibt die systemeigenen Funktionen auf dem Gerät eines Benutzers an, für die Ihre APP möglicherweise Zugriff anfordern kann. Mögliche Optionen sind:

* `geolocation`
* `media`
* `notifications`
* `midi`
* `openExternal`

## <a name="validdomains"></a>validDomains

**Optional**, sofern angegeben, außer **erforderlich**

Eine Liste gültiger Domänen für Websites, die von der APP im Microsoft Teams-Client zu laden erwartet werden. Domänen Auflistungen können beispielsweise Platzhalterzeichen enthalten `*.example.com` . Dies entspricht genau einem Segment der Domäne. Wenn Sie eine Übereinstimmung benötigen, `a.b.example.com` verwenden Sie `*.*.example.com` . Wenn Ihre Registerkartenkonfiguration oder Inhalts-UI neben einer Verwendung für die Registerkartenkonfiguration zu einer anderen Domäne navigieren muss, muss diese Domäne hier angegeben werden.

Es ist jedoch **nicht** erforderlich, die Domänen von Identitätsanbietern einzubeziehen, die Sie in Ihrer APP unterstützen möchten. Um beispielsweise mit einer Google-ID zu authentifizieren, müssen Sie zu Accounts.Google.com umgeleitet werden, aber Sie sollten Accounts.Google.com nicht in einschließen `validDomains[]` .

Microsoft Teams-apps, die ihre eigenen SharePoint-URLs benötigen, um gut zu funktionieren, können "{teamsitedomain}" in Ihre gültige Domänenliste einschließen.

> [!IMPORTANT]
> Fügen Sie keine Domänen hinzu, die sich außerhalb des Steuerelements befinden, entweder direkt oder über Platzhalter. Beispielsweise `yourapp.onmicrosoft.com` ist gültig, jedoch ungültig `*.onmicrosoft.com` .

Das Objekt ist ein Array mit allen Elementen des Typs `string` .

## <a name="webapplicationinfo"></a>webApplicationInfo

**Optional** – Objekt

Geben Sie Ihre Azure Active Directory (Azure AD)-APP-ID und Microsoft Graph-Informationen an, damit Benutzer sich nahtlos bei ihrer App anmelden können. Wenn Ihre APP in Azure AD registriert ist, müssen Sie die APP-ID angeben, damit Administratoren die Berechtigungen einfach überprüfen und die Zustimmung im Teamadministrator Center erteilen können.

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`id`|string|36 Zeichen|✔|Aad-Anwendungs-ID der app. Diese ID muss eine GUID sein.|
|`resource`|Zeichenfolge|2048 Zeichen|✔|Ressourcen-URL der APP zum Abrufen des Authentifizierungstokens für SSO.|
|`applicationPermissions`|array of strings|128 Zeichen||Angeben einer detaillierten [ressourcenspezifischen Zustimmung](../../graph-api/rsc/resource-specific-consent.md#resource-specific-permissions)|

## <a name="showloadingindicator"></a>showLoadingIndicator

**Optional** – Boolean

Geben Sie an, ob der Lade Indikator angezeigt werden soll, wenn eine APP/Registerkarte geladen wird. Standard: **False**.
>[!NOTE]
>Wenn Sie "showLoadingIndicator: true" in Ihrem App-Manifest festgelegt haben, müssen Sie die Inhaltsseiten ihrer Registerkarten und Aufgaben Module gemäß dem in [Anzeigen eines systemeigenen Lade Indikator](../../tabs/how-to/create-tab-pages/content-page.md#show-a-native-loading-indicator) Dokuments beschriebenen Protokoll ändern.


## <a name="isfullscreen"></a>isFullScreen

 **Optional** – Boolean

Geben Sie an, wo eine persönliche App mit oder ohne Registerkarten Kopfleiste gerendert wird. Standard: **False**.

## <a name="activities"></a>Aktivitäten

**Optional** – Objekt

Definieren Sie die Eigenschaften, die Ihre APP für die Bereitstellung in einem Benutzer Aktivitätsfeed verwenden wird.

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`activityTypes`|Array von Objekten|128 Elemente| | Geben Sie die Arten von Aktivitäten an, die Ihre APP an einen Benutzer-Aktivitätsfeed senden kann.|

### <a name="activitiesactivitytypes"></a>Activities. activityTypes

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`type`|string|32 Zeichen|✔|Der Typ der Benachrichtigung. *Siehe weiter unten*.|
|`description`|Zeichenfolge|128 Zeichen|✔|Eine kurze Beschreibung der Benachrichtigung. *Siehe weiter unten*.|
|`templateText`|Zeichenfolge|128 Zeichen|✔|Ex: "{Akteur} hat Aufgabe {Task-Nr} für dich erstellt"|

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
