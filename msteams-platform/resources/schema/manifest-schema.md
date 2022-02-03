---
title: Manifestschemareferenz
description: Beschreibung des Manifestschemas für Microsoft Teams
ms.topic: reference
ms.author: lajanuar
ms.localizationpriority: high
keywords: Manifestschema für Microsoft Teams
ms.openlocfilehash: 88fd025229a90ac6e3888763f643829950912633
ms.sourcegitcommit: 7209e5af27e1ebe34f7e26ca1e6b17cb7290bc06
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 01/25/2022
ms.locfileid: "62212019"
---
# <a name="reference-manifest-schema-for-microsoft-teams"></a>Referenz: Manifestschema für Microsoft Teams

Das Microsoft Teams-Manifest beschreibt, wie die App in das Microsoft Teams Produkt integriert wird. Ihr Manifest muss dem unter [`https://developer.microsoft.com/json-schemas/teams/v1.11/MicrosoftTeams.schema.json`]( https://developer.microsoft.com/json-schemas/teams/v1.11/MicrosoftTeams.schema.json) gehosteten Schema entsprechen. Frühere Versionen (1.0, 1.1,..., und 1.11) werden ebenfalls unterstützt (unter Verwendung von "v1.x" in der URL).
Weitere Informationen zu den Änderungen, die in den einzelnen Versionen vorgenommen wurden, finden Sie im [Manifeständerungsprotokoll](https://github.com/OfficeDev/microsoft-teams-app-schema/releases).

Das folgende Schemabeispiel umfasst alle Erweiterbarkeitsoptionen:

## <a name="sample-full-manifest"></a>Vollständiges Beispielmanifest

```json
{
  "$schema": "https://developer.microsoft.com/json-schemas/teams/v1.11/MicrosoftTeams.schema.json",
  "manifestVersion": "1.11",
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
          "description": "Command Description; e.g., Add a customer",
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
        },
         {
          "id": "exampleCmd3",
          "title": "Example Command 3",
          "type": "action",
          "context": [
            "compose",
            "commandBox",
            "message"
          ],
          "description": "Command Description; e.g., Add a customer",
          "fetchTask": false,
          "taskInfo": {
            "title": "Initial dialog title",
            "width": "Dialog width",
            "height": "Dialog height",
            "url": "Initial webview URL"
          }
        }
      ],
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
  "defaultBlockUntilAdminAction": true,
  "publisherDocsUrl": "https://website.com/app-info",
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
 ],
  "subscriptionOffer": {
    "offerId": "publisherId.offerId"
  }
}
```

Das Schema definiert die folgenden Eigenschaften:

## <a name="schema"></a>$schema

Optional, wird jedoch empfohlen – Zeichenfolge

Die https://-URL, die auf das JSON-Schema für das Manifest verweist.

## <a name="manifestversion"></a>manifestVersion

**Erforderlich** – Zeichenfolge

Die Version des Manifestschemas, das dieses Manifest verwendet. Muss 1.10 sein.

## <a name="version"></a>Version

**Erforderlich** – Zeichenfolge

Die Version einer bestimmten App. Wenn Sie etwas in Ihrem Manifest aktualisieren, muss auch die Version erhöht werden. So wird beim Installieren des neuen Manifests das vorhandene überschrieben, und der Benutzer erhält die neuen Funktionen. Wenn die betreffende App an den Store übermittelt wurde, muss das neue Manifest erneut übermittelt und erneut validiert werden. Die App-Benutzer erhalten das neue aktualisierte Manifest automatisch innerhalb weniger Stunden nach dessen Genehmigung.

Wenn sich die App-Berechtigungsanforderungen ändern, werden die Benutzer aufgefordert, ein Upgrade durchzuführen und der App erneut die Berechtigungen zu erteilen.

Diese Versionszeichenfolge muss dem [SemVer](http://semver.org/)-Standard entsprechen (MAJOR.MINOR.PATCH).

## <a name="id"></a>id

**Erforderlich** – Microsoft-App-ID

Die ID ist ein eindeutiger, von Microsoft generierter Bezeichner für die App. Sie verfügen über eine ID, wenn Ihr Bot über das Microsoft Bot Framework registriert ist. Sie verfügen über eine ID, wenn sich die Web-App Ihrer Registerkarte bereits bei Microsoft anmeldet. Sie müssen die ID hier eingeben. Andernfalls müssen Sie eine neue ID im [Microsoft-Anwendungsregistrierungsportal](https://aka.ms/appregistrations) generieren. Verwenden Sie die gleiche ID, wenn Sie einen Bot hinzufügen.

> [!NOTE]
> Wenn Sie ein Update für Ihre vorhandene App in AppSource übermitteln, darf die ID in Ihrem Manifest nicht geändert werden.

## <a name="developer"></a>developer

**Erforderlich** – Objekt

Gibt Informationen zu Ihrem Unternehmen an. Für Apps, die an den Microsoft Teams Store übermittelt werden, müssen diese Werte mit den Informationen in Ihrem Store-Eintrag übereinstimmen. Weitere Informationen finden Sie in den [Richtlinien für die Veröffentlichung im Microsoft Teams Store](~/concepts/deploy-and-publish/appsource/publish.md).

|Name| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|
|`name`|32 Zeichen|✔|Der Anzeigename für den Entwickler.|
|`websiteUrl`|2048 Zeichen|✔|Die https://-URL zur Website des Entwicklers. Dieser Link muss Benutzer zur Landing Page Ihres Unternehmens oder des produktspezifischen Angebots führen.|
|`privacyUrl`|2048 Zeichen|✔|Die https://-URL zur Datenschutzerklärung des Entwicklers.|
|`termsOfUseUrl`|2048 Zeichen|✔|Die https://-URL zu den Nutzungsbedingungen des Entwicklers.|
|`mpnId`|10 Zeichen| |**Optional**: Die Microsoft Partner Network-ID der Partnerorganisation, die die App erstellt.|

## <a name="name"></a>name

**Erforderlich** – Objekt

Der Name Ihrer App-Lösung, der Benutzern in der Microsoft Teams-Umgebung angezeigt wird. Für Apps, die an AppSource übermittelt werden, müssen diese Werte mit den Informationen in Ihrem AppSource-Eintrag übereinstimmen. Die Werte von `short` und `full` müssen unterschiedlich sein.

|Name| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|
|`short`|30 Zeichen|✔|Der Kurzanzeigename für die App.|
|`full`|100 Zeichen||Der vollständige Name der App; wird verwendet, wenn der vollständige App-Name 30 Zeichen überschreitet.|

## <a name="description"></a>description

**Erforderlich** – Objekt

Beschreibt Ihre App für Benutzer. Für Apps, die an AppSource übermittelt werden, müssen diese Werte mit den Informationen in Ihrem AppSource-Eintrag übereinstimmen.

Stellen Sie sicher, dass Ihre Beschreibung Ihre Lösung beschreibt und potenziellen Kunden hilft zu verstehen, worin ihre Funktion besteht. Sie müssen in der vollständigen Beschreibung angeben, ob ein externes Konto für die Verwendung der App erforderlich ist. Die Werte von `short` und `full` müssen unterschiedlich sein. Die Kurzbeschreibung darf nicht innerhalb der ausführlichen Beschreibung wiederholt werden und darf keinen anderen App-Namen enthalten.

|Name| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|
|`short`|80 Zeichen|✔|Eine kurze Beschreibung der App; wird verwendet, wenn der Platz begrenzt ist.|
|`full`|4.000 Zeichen|✔|Die vollständige Beschreibung Ihrer App.|

## <a name="packagename"></a>packageName

**Optional** – Zeichenfolge

Ein eindeutiger Bezeichner für die App in umgekehrter Domänenschreibweise; z. B. "com.example.myapp". Maximale Länge: 64 Zeichen.

## <a name="localizationinfo"></a>localizationInfo

**Optional** – Objekt

Ermöglicht die Angabe einer Standardsprache und stellt Zeiger auf weitere Sprachdateien bereit. Weitere Informationen finden Sie unter [Lokalisierung](~/concepts/build-and-test/apps-localization.md).

|Name| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|
|`defaultLanguageTag`||✔|Das Sprachtag der Zeichenfolgen in dieser Manifestdatei auf oberster Ebene.|

### <a name="localizationinfoadditionallanguages"></a>localizationInfo.additionalLanguages

Ein Array von Objekten, die weitere Sprachübersetzungen angeben.

|Name| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|
|`languageTag`||✔|Das Sprachtag der Zeichenfolgen in der bereitgestellten Datei.|
|`file`||✔|Ein relativer Dateipfad zur JSON-Datei mit den übersetzten Zeichenfolgen.|

## <a name="icons"></a>Symbole

**Erforderlich** – Objekt

Symbole, die in der Microsoft Teams-App verwendet werden. Die Symboldateien müssen als Teil des Uploadpakets enthalten sein. Weitere Informationen finden Sie unter [Symbole](../../concepts/build-and-test/apps-package.md#app-icons).

|Name| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|
|`outline`|32 x 32 Pixel|✔|Ein relativer Dateipfad zu einem transparenten, 32 x 32 Pixel großen PNG-Kontursymbol.|
|`color`|192 x 192 Pixel|✔|Ein relativer Dateipfad zu einem farbigen, 192 x 192 Pixel großen PNG-Symbol.|

## <a name="accentcolor"></a>accentColor

**Erforderlich** – HTML-Hex-Farbcode

Eine Farbe, die als Hintergrund für Ihre Kontursymbole verwendet werden soll.

Bei dem Wert muss es sich um einen gültigen HTML-Farbcode handeln, der mit "#" beginnt, z. B. `#4464ee`.

## <a name="configurabletabs"></a>configurableTabs

**Optional** – Array

Wird verwendet, wenn Ihre App-Lösung über Teamkanal-Registerkarten verfügt, die eine zusätzliche Konfiguration erfordern, bevor sie hinzugefügt werden. Konfigurierbare Registerkarten werden nur in den `team`- und `groupchat`-Bereichen unterstützt, und Sie können dieselben Registerkarten mehrmals konfigurieren. Sie können sie jedoch nur einmal im Manifest definieren.

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`configurationUrl`|string|2048 Zeichen|✔|Die https://-URL, die beim Konfigurieren der Registerkarte verwendet werden soll.|
|`scopes`|Array von Enumerationen|1|✔|Derzeit unterstützen konfigurierbare Registerkarten nur die Bereiche `team` und `groupchat`. |
|`canUpdateConfiguration`|boolean|||Der Wert, der angibt, ob eine Instanz der Registerkartenkonfiguration nach der Erstellung vom Benutzer aktualisiert werden kann. Standard: **true**.|
|`context` |Array von Enumerationen|6 ||Die Gruppe von `contextItem`-Bereichen, in denen eine [Registerkarte unterstützt wird](../../tabs/how-to/access-teams-context.md). Standard: **[channelTab, privateChatTab, meetingChatTab, meetingDetailsTab]**.|
|`sharePointPreviewImage`|string|2048||Ein relativer Dateipfad zu einem Registerkartenvorschaubild zur Verwendung in SharePoint. Größe: 1024 x 768. |
|`supportedSharePointHosts`|Array von Enumerationen|1||Definiert, wie Ihre Registerkarte in SharePoint zur Verfügung gestellt wird. Optionen: `sharePointFullPage` und `sharePointWebPart` |

## <a name="statictabs"></a>staticTabs

**Optional** – Array

Definiert eine Reihe von Registerkarten, die standardmäßig "angeheftet" werden können, ohne dass der Benutzer sie manuell hinzufügen muss. Im `personal`-Bereich deklarierte statische Registerkarten werden immer an die persönliche Benutzeroberfläche der App angeheftet. Im `team`-Bereich deklarierte statische Registerkarten werden derzeit nicht unterstützt.

Dieses Element ist ein Array (maximal 16 Elemente), wobei alle Elemente vom Typ `object` sind. Dieser Block ist nur für Lösungen erforderlich, die eine Lösung mit statischen Registerkarten bereitstellen.

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`entityId`|string|64 Zeichen|✔|Ein eindeutiger Bezeichner für die Entität, die auf der Registerkarte angezeigt wird.|
|`name`|string|128 Zeichen|✔|Der Anzeigename der Registerkarte in der Kanal-Benutzeroberfläche.|
|`contentUrl`|string||✔|Die https://-URL, die auf die Entitäts-Benutzeroberfläche verweist, die im Microsoft Teams-Canvas angezeigt werden soll.|
|`websiteUrl`|string|||Die https://-URL, auf die verwiesen wird, wenn sich ein Benutzer für die Anzeige in einem Browser entscheidet.|
|`searchUrl`|string|||Die https://-URL, auf die für die Suchabfragen eines Benutzers verwiesen wird.|
|`scopes`|Array von Enumerationen|1|✔|Derzeit unterstützen statische Registerkarten nur den `personal`-Bereich. Das bedeutet, dass sie nur als Teil der persönlichen Benutzeroberfläche bereitgestellt werden können.|
|`context` | Array von Enumerationen| 2|| Die Gruppe von `contextItem`-Bereichen, in denen eine Registerkarte unterstützt wird.|

> [!NOTE]
>  Das searchUrl-Feature ist für Drittanbieterentwickler nicht verfügbar.
> Wenn Ihre Registerkarten kontextabhängige Informationen zum Anzeigen relevanter Inhalte oder zum Initiieren eines Authentifizierungsvorgangs benötigen, finden Sie entsprechende Informationen unter [Abrufen von Kontext für Ihre Microsoft Teams-Registerkarte](../../tabs/how-to/access-teams-context.md).

## <a name="bots"></a>Bots

**Optional** – Array

Definiert eine Bot-Lösung zusammen mit optionalen Informationen wie Standardbefehlseigenschaften.

Das Element ist ein Array (maximal ein Element &mdash; derzeit ist nur ein Bot pro App zulässig) mit allen Elementen des Typs `object`. Dieser Block ist nur für Lösungen erforderlich, die einen Bot umfassen.

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`botId`|string|64 Zeichen|✔|Die eindeutige Microsoft-App-ID für den Bot, wie bei Bot Framework registriert. Die ID kann mit der Gesamt-[App-ID](#id)übereinstimmen.|
|`scopes`|Array von Enumerationen|3|✔|Gibt an, ob der Bot eine Umgebung im Kontext eines Kanals in einem `team` oder Gruppenchat (`groupchat`) ist, oder aber eine Umgebung einzig für einen bestimmten Benutzer (`personal`). Diese Optionen sind nicht exklusiv.|
|`needsChannelSelector`|boolean|||Beschreibt, ob der Bot einen Benutzerhinweis verwendet, um den Bot zu einem bestimmten Kanal hinzuzufügen. Standard: **`false`**|
|`isNotificationOnly`|boolean|||Gibt an, ob ein Bot ein unidirektionaler Bot ausschließlich für Benachrichtigungen ist (im Gegensatz zu einem dialogorientierten Bot). Standard: **`false`**|
|`supportsFiles`|boolean|||Gibt an, ob der Bot die Möglichkeit zum Hochladen/Herunterladen von Dateien in persönliche Chats unterstützt. Standard: **`false`**|
|`supportsCalling`|boolean|||Ein Wert, der angibt, wo ein Bot Audioanrufe unterstützt. **WICHTIG**: Dies ist derzeit eine experimentelle Eigenschaft. Experimentelle Eigenschaften sind u. U. nicht komplett und werden möglicherweise geändert, bevor sie vollständig verfügbar sind.  Die Eigenschaft wird nur zu Test- und Erforschungszwecken bereitgestellt und darf nicht in Produktionsanwendungen verwendet werden. Standard: **`false`**|
|`supportsVideo`|boolean|||Ein Wert, der angibt, wo ein Bot Videoanrufe unterstützt. **WICHTIG**: Dies ist derzeit eine experimentelle Eigenschaft. Experimentelle Eigenschaften sind u. U. nicht komplett und werden möglicherweise geändert, bevor sie vollständig verfügbar sind.  Die Eigenschaft wird nur zu Test- und Erforschungszwecken bereitgestellt und darf nicht in Produktionsanwendungen verwendet werden. Standard: **`false`**|

### <a name="botscommandlists"></a>bots.commandLists

Eine optionale Liste von Befehlen, die Ihr Bot Benutzern vorschlagen kann. Das Objekt ist ein Array (maximal zwei Elemente), wobei alle Elemente vom Typ `object` sind. Sie müssen für jeden Bereich, den Ihr Bot unterstützt, eine separate Befehlsliste definieren. Weitere Informationen finden Sie unter [Bot-Menüs](~/bots/how-to/create-a-bot-commands-menu.md).

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`items.scopes`|Array von Enumerationen|3|✔|Gibt den Bereich an, für den die Befehlsliste gültig ist. Mögliche Optionen sind `team`, `personal` und `groupchat`.|
|`items.commands`|Array von Objekten|10|✔|Ein Array von Befehlen, die der Bot unterstützt:<br>`title`: Name des Bot-Befehls (string, 32)<br>`description`: Eine einfache Beschreibung oder ein Beispiel für die Befehlssyntax und zugehörige Argumente (string, 128)|

### <a name="botscommandlistscommands"></a>bots.commandLists.commands

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|title|string|12 |✔|Der Name des Bot-Befehls.|
|description|string|128 Zeichen|✔|Eine einfache Textbeschreibung oder ein Beispiel für die Befehlssyntax und zugehörige Argumente.|

## <a name="connectors"></a>connectors

**Optional** – Array

Der `connectors`-Block definiert einen Office 365 Connector für die App.

Das Objekt ist ein Array (maximal ein Element), wobei alle Elemente vom Typ `object` sind. Dieser Block ist nur für Lösungen erforderlich, die einen Connector bereitstellen.

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`configurationUrl`|string|2048 Zeichen|✔|Die https://-URL, die beim Konfigurieren des Connectors verwendet werden soll.|
|`scopes`|Array von Enumerationen|1|✔|Gibt an, ob der Connector eine Umgebung im Kontext eines Kanals in einem `team` oder aber eine Umgebung einzig für einen bestimmten Benutzer (`personal`) bietet. Derzeit wird nur der `team`-Bereich unterstützt.|
|`connectorId`|string|64 Zeichen|✔|Ein eindeutiger Bezeichner für den Connector, der seiner ID im [Connectors Developer Dashboard](https://aka.ms/connectorsdashboard) entspricht.|

## <a name="composeextensions"></a>composeExtensions

**Optional** – Array

Definiert eine Messaging-Erweiterung für die App.

> [!NOTE]
> Der Name des Features wurde im November 2017 von "Compose-Erweiterung" in "Messaging-Erweiterung" geändert, der Manifestname bleibt jedoch unverändert, sodass vorhandene Erweiterungen weiterhin funktionieren.

Das Element ist ein Array (maximal ein Element), wobei alle Elemente vom Typ `object` sind. Dieser Block ist nur für Lösungen erforderlich, die eine Messaging-Erweiterung bereitstellen.

|Name| Typ | Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`botId`|string|64|✔|Die eindeutige Microsoft-App-ID für den Bot, welcher der Messaging-Erweiterung zugeordnet ist, wie beim Bot Framework registriert. Die ID kann mit der Gesamt-App-ID übereinstimmen.|
|`commands`|Array von Objekten|10|✔|Array von Befehlen, die von der Messaging-Erweiterung unterstützt werden.|
|`canUpdateConfiguration`|boolean|||Ein Wert, der angibt, ob die Konfiguration einer Messaging-Erweiterung vom Benutzer aktualisiert werden kann. Standard: **False**.|
|`messageHandlers`|Array von Objekten|5||Eine Liste von Handlern, mit denen Apps aufgerufen werden können, wenn bestimmte Bedingungen erfüllt sind.|
|`messageHandlers.type`|string|||Der Typ des Nachrichtenhandlers. Muss `"link"` sein.|
|`messageHandlers.value.domains`|Array aus Zeichenfolgen|||Array von Domänen, für die sich der Link-Nachrichtenhandler registrieren kann.|

### <a name="composeextensionscommands"></a>composeExtensions.commands

Ihre Messaging-Erweiterung muss mindestens einen Befehl deklarieren (maximal 10 Befehle insgesamt). Jeder Befehl wird in Microsoft Teams als potenzielle Interaktion vom Einstiegspunkt in der Benutzeroberfläche angezeigt.

Jedes Befehlselement ist ein Objekt mit folgender Struktur:

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`id`|string|64 Zeichen|✔|Die ID für den Befehl.|
|`title`|string|32 Zeichen|✔|Der benutzerfreundliche Name des Befehls.|
|`type`|string|64 Zeichen||Der Befehlstyp. Entweder `query` oder `action`. Standard: **query**.|
|`description`|string|128 Zeichen||Die Beschreibung, die Benutzern angezeigt wird, um den Zweck dieses Befehls anzugeben.|
|`initialRun`|boolean|||Ein boolescher Wert, der angibt, ob der Befehl anfänglich ohne Parameter ausgeführt wird. Der Standardwert ist **false**.|
|`context`|Array aus Zeichenfolgen|3||Definiert, wo die Nachrichtenerweiterung aufgerufen werden kann. Eine beliebige Kombination aus `compose`, `commandBox`, `message`. Der Standardwert ist `["compose","commandBox"]`.|
|`fetchTask`|boolean|||Ein boolescher Wert, der angibt, ob das Aufgabenmodul dynamisch abgerufen werden muss. Der Standardwert ist **false**.|
|`taskInfo`|Objekt|||Geben Sie das Aufgabenmodul an, das vorab geladen werden soll, wenn ein Messaging-Erweiterungsbefehl verwendet wird.|
|`taskInfo.title`|string|64 Zeichen||Titel des ersten Dialogfelds.|
|`taskInfo.width`|string|||Dialogfensterbreite: entweder eine Angabe in Pixeln oder ein Standardlayout, z. B. "groß", "mittel" oder "klein".|
|`taskInfo.height`|string|||Dialogfensterhöhe: entweder eine Angabe in Pixeln oder ein Standardlayout, z. B. "groß", "mittel" oder "klein".|
|`taskInfo.url`|string|||Anfängliche WebView-URL.|
|`parameters`|Objekt-Array|5 Elemente|✔|Die Liste der Parameter, die der Befehl verwendet. Minimum: 1; Maximum: 5.|
|`parameters.name`|string|64 Zeichen|✔|Der Name des Parameters, wie er im Client angezeigt wird. Der Parametername ist in der Benutzeranforderung enthalten.|
|`parameters.title`|string|32 Zeichen|✔|Benutzerfreundlicher Titel für den Parameter.|
|`parameters.description`|string|128 Zeichen||Benutzerfreundliche Zeichenfolge, die den Zweck dieses Parameters beschreibt.|
|`parameters.value`|string|512 Zeichen||Anfangswert für den Parameter. Derzeit wird der Wert nicht unterstützt.|
|`parameters.inputType`|string|128 Zeichen||Definiert den Typ des Steuerelements, das in einem Aufgabenmodul für `fetchTask: true` angezeigt wird. Einer der folgenden: `text, textarea, number, date, time, toggle, choiceset`.|
|`parameters.choices`|Array von Objekten|10 Elemente||Die Auswahloptionen für `choiceset`. Wird nur verwendet, wenn `parameter.inputType` `choiceset` ist.|
|`parameters.choices.title`|string|128 Zeichen|✔|Titel der Auswahl.|
|`parameters.choices.value`|string|512 Zeichen|✔|Value of the choice.|

## <a name="permissions"></a>Berechtigungen

**Optional** – Array von Zeichenfolgen

Ein Array von `string`, das angibt, welche Berechtigungen die App anfordert, wodurch Endbenutzer wissen, wie die Erweiterung funktioniert. Die folgenden Optionen sind nicht exklusiv:

* `identity` &emsp; Erfordert Benutzeridentitätsinformationen.
* `messageTeamMembers`&emsp; Erfordert die Berechtigung, direkte Nachrichten an Teammitglieder zu senden.

Wenn Sie diese Berechtigungen während der App-Aktualisierung ändern, müssen Ihre Benutzer den Zustimmungsprozess wiederholen, nachdem sie die aktualisierte App gestartet haben. Weitere Informationen finden Sie unter [Aktualisieren Ihrer App](~/concepts/deploy-and-publish/appsource/post-publish/overview.md).

## <a name="devicepermissions"></a>devicePermissions

**Optional** – Array von Zeichenfolgen

Stellt die systemeigenen Features auf dem Gerät eines Benutzers bereit, für die Ihre App Zugriff anfordert. Mögliche Optionen sind:

* `geolocation`
* `media`
* `notifications`
* `midi`
* `openExternal`

## <a name="validdomains"></a>validDomains

**Optional**, außer **erforderlich** wo angegeben.

Eine Liste gültiger Domänen für Websites, die von der App im Microsoft Teams-Client geladen werden sollen. Domäneneinträge können Platzhalter enthalten, z. B. `*.example.com`. Die gültige Domäne entspricht genau einem Segment der Domäne. Wenn sie `a.b.example.com` entsprechen muss, verwenden Sie `*.*.example.com`. Wenn Ihre Registerkartenkonfiguration oder Inhalts-UI zu einer anderen Domäne als jener der Registerkartenkonfiguration führt, muss diese Domäne hier angegeben werden.

Schließen Sie **nicht** die Domänen von Identitätsanbietern ein, die in Ihrer App unterstützt werden sollen. Um sich beispielsweise mit einer Google-ID zu authentifizieren, ist es erforderlich, zu accounts.google.com umzuleiten. Sie dürfen jedoch accounts.google.com nicht in `validDomains[]` einschließen.

Microsoft Teams-Apps, die ihre eigenen SharePoint-URLs benötigen, um ordnungsgemäß zu funktionieren, enthalten "{teamsitedomain}" in ihrer Liste zulässiger Domänen.

> [!IMPORTANT]
> Fügen Sie keine Domänen hinzu, die außerhalb Ihrer Kontrolle liegen, weder direkt noch über Platzhalter. Beispiel: `yourapp.onmicrosoft.com` ist gültig, `*.onmicrosoft.com` ist hingegen nicht gültig.

Das Objekt ist ein Array, wobei alle Elemente vom Typ `string` sind.

## <a name="webapplicationinfo"></a>webApplicationInfo

**Optional** – Objekt

Geben Sie Ihre Azure Active Directory-App-ID und Microsoft Graph-Informationen an, um Benutzern zu helfen, sich nahtlos bei Ihrer App anzumelden. Falls Ihre App in Azure AD registriert ist, müssen Sie die App-ID angeben. Administratoren können im Microsoft Teams Admin Center Berechtigungen einfach überprüfen und ihre Zustimmung erteilen.

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`id`|string|36 Zeichen|✔|Azure AD-Anwendungs-ID der App. Diese ID muss eine GUID sein.|
|`resource`|string|2048 Zeichen|✔|Ressourcen-URL der App zum Abrufen des Authentifizierungstokens für Einmaliges Anmelden. </br> **HINWEIS:** Wenn Sie Einmaliges Anmelden nicht verwenden, geben Sie einen Dummyzeichenfolgenwert in dieses Feld in Ihr App-Manifest ein (z. B. https://notapplicable), um eine Fehlermeldung zu vermeiden. |
|`applicationPermissions`|array of strings|128 Zeichen||Geben Sie eine präzise [ressourcenspezifische Einwilligung](../../graph-api/rsc/resource-specific-consent.md#resource-specific-permissions) an.|

## <a name="showloadingindicator"></a>showLoadingIndicator

**Optional** – boolescher Wert

Gibt an, ob die Ladefortschritt angezeigt werden soll, während eine App oder Registerkarte geladen wird. Der Standardwert ist **false**.
>[!NOTE]
>Wenn Sie für `showLoadingIndicator` im App-Manifest "true" auswählen, ändern Sie zum ordnungsgemäßen Laden der Seite die Inhaltsseiten Ihrer Registerkarten und Aufgabenmodule, wie im Dokument [Anzeigen eines systemeigenen Lade-Indikators](../../tabs/how-to/create-tab-pages/content-page.md#show-a-native-loading-indicator).


## <a name="isfullscreen"></a>isFullScreen

 **Optional** – boolescher Wert

Gibt an, wo eine persönliche App mit oder ohne Registerkartenkopfleiste gerendert wird. Der Standardwert ist **false**.

> [!NOTE]
> `isFullScreen` funktioniert nur für Apps, die in Ihrer Organisation veröffentlicht wurden.

## <a name="activities"></a>Aktivitäten

**Optional** – Objekt

Definiert die Eigenschaften, die Ihre App zum Posten eines Benutzeraktivitätsfeeds verwendet.

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`activityTypes`|Array von Objekten|128 Elemente| | Geben Sie die Arten von Aktivitäten an, die Ihre App in einem Benutzeraktivitätsfeed veröffentlichen kann.|

### <a name="activitiesactivitytypes"></a>activities.activityTypes

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`type`|string|32 Zeichen|✔|Der Benachrichtigungstyp. *Siehe unten*.|
|`description`|string|128 Zeichen|✔|Eine kurze Beschreibung der Benachrichtigung. *Siehe unten*.|
|`templateText`|string|128 Zeichen|✔|Beispiel: "{actor} hat die Aufgabe {taskId} für Sie erstellt."|

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

Gibt den standardmäßig für diese App definierten Installationsbereich an. Der definierte Bereich ist die Option, die auf der Schaltfläche angezeigt wird, wenn ein Benutzer versucht, die App hinzuzufügen. Mögliche Optionen sind:
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
|`team`|string|||Wenn der ausgewählte Installationsbereich `team` ist, gibt dieses Feld die verfügbare Standardfunktion an. Optionen: `tab`, `bot` oder `connector`.|
|`groupchat`|string|||Wenn der ausgewählte Installationsbereich `groupchat` ist, gibt dieses Feld die verfügbare Standardfunktion an. Optionen: `tab`, `bot` oder `connector`.|
|`meetings`|string|||Wenn der ausgewählte Installationsbereich `meetings` ist, gibt dieses Feld die verfügbare Standardfunktion an. Optionen: `tab`, `bot` oder `connector`.|

## <a name="configurableproperties"></a>configurableProperties

**Optional** – Array

Der `configurableProperties`-Block definiert die App-Eigenschaften, die Microsoft Teams-Administratoren anpassen können. Weitere Informationen finden Sie unter [Aktivieren der App-Anpassung](~/concepts/design/enable-app-customization.md). Das App-Anpassungsfeature wird in benutzerdefinierten oder branchenspezifischen Apps nicht unterstützt.

> [!NOTE]
> Es muss mindestens eine Eigenschaft definiert werden. Sie können in diesem Block maximal neun Eigenschaften definieren.

Sie können eine der folgenden Eigenschaften definieren:

* `name`: Der Anzeigename der App.
* `shortDescription`: Die Kurzbeschreibung der App.
* `longDescription`: Die ausführliche Beschreibung der App.
* `smallImageUrl`: Das Kontursymbol der App.
* `largeImageUrl`: Das Farbsymbol der App.
* `accentColor`: Die zu verwendende Farbe und ein Hintergrund für Kontursymbole.
* `developerUrl`: Die HTTPS-URL der Website des Entwicklers.
* `privacyUrl`: Die HTTPS-URL der Datenschutzerklärung des Entwicklers.
* `termsOfUseUrl`: Die HTTPS-URL der Nutzungsbedingungen des Entwicklers.

## <a name="defaultblockuntiladminaction"></a>defaultBlockUntilAdminAction

**Optional** – boolescher Wert
 
Wenn die `defaultBlockUntilAdminAction`-Eigenschaft auf **true** festgelegt ist, ist die App so lange standardmäßig für Benutzer ausgeblendet, bis der Administrator sie zulässt. Bei Festlegung auf **true** ist die App für alle Mandanten und Endbenutzer ausgeblendet. Mandantenadministratoren können die App im Microsoft Teams Admin Center sehen und Maßnahmen ergreifen, um sie zuzulassen oder zu blockieren. Der Standardwert ist **false**. Weitere Informationen zum standardmäßigen App-Block finden Sie unter [Ausblenden von Microsoft Teams-App, bis sie vom Administrator genehmigt werden](~/concepts/design/enable-app-customization.md#hide-teams-app-until-admin-approves).

## <a name="publisherdocsurl"></a>publisherDocsUrl

**Optional** – Zeichenfolge

**Maximale Länge**: 128 Zeichen

`publisherDocsUrl` ist eine HTTPS-URL zu einer Informationsseite, auf der Administratoren Anweisungen finden, bevor sie eine App zulassen, die standardmäßig blockiert ist. Sie kann auch verwendet werden, um Anweisungen oder Informationen zur App bereitzustellen, die für den Mandantenadministrator nützlich sein könnten.

## <a name="subscriptionoffer"></a>subscriptionOffer

**Optional** – Objekt

Gibt das Ihrer App zugeordnete SaaS-Angebot an.

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`offerId`| string | 2048 Zeichen | ✔ | Ein eindeutiger Bezeichner, der Ihre Publisher-ID und Angebots-ID enthält. Diese finden Sie im [Partner Center](https://partner.microsoft.com/dashboard). Sie müssen die Zeichenfolge als `publisherId.offerId` formatieren.|

## <a name="see-also"></a>Siehe auch

* [Grundlegendes zur Struktur von Microsoft Teams-Apps](~/concepts/design/app-structure.md)
* [Aktivieren der App-Anpassung](~/concepts/design/enable-app-customization.md)
* [Lokalisieren IhrerApp](~/concepts/build-and-test/apps-localization.md)
* [Integrieren von Medienfunktionen](~/concepts/device-capabilities/mobile-camera-image-permissions.md)
* [Referenz: Entwicklervorschau-Manifestschema – Microsoft Teams](~/resources/schema/manifest-schema-dev-preview.md)
