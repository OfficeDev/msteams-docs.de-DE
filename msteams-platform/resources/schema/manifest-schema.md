---
title: Manifestschemareferenz
description: In diesem Artikel verfügen Sie über die neueste Version des öffentlichen Manifestschemas für Microsoft Teams-Referenz, Schema und vollständiges Beispielmanifest.
ms.topic: reference
ms.localizationpriority: high
ms.openlocfilehash: 2638c668bf1363a0f997786bcb958689626c70c6
ms.sourcegitcommit: 637b8f93b103297b1ff9f1af181680fca6f4499d
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/07/2022
ms.locfileid: "68499174"
---
# <a name="app-manifest-schema-for-teams"></a>App-Manifestschema für Teams

Das Microsoft Teams-App-Manifest beschreibt, wie Ihre App in das Microsoft Teams-Produkt integriert wird. Ihr App-Manifest muss dem Schema entsprechen, das auf [`https://developer.microsoft.com/json-schemas/teams/v1.14/MicrosoftTeams.schema.json`]( https://developer.microsoft.com/json-schemas/teams/v1.14/MicrosoftTeams.schema.json)gehostet wird. Frühere Versionen 1.0, 1.1,...,1.13 und die aktuelle Version 1.14 werden jeweils unterstützt (mit "v1.x" in der URL).
Weitere Informationen zu den Änderungen, die in den einzelnen Versionen vorgenommen wurden, finden Sie im [Manifeständerungsprotokoll](https://github.com/OfficeDev/microsoft-teams-app-schema/releases).

In der folgenden Tabelle sind die TeamsJS-Version und die Versionen der App-Manifeste für die verschiedenen App-Szenarien aufgeführt:

[!INCLUDE [pre-release-label](~/includes/teamjs-version-details.md)]

Das folgende Schemabeispiel umfasst alle Erweiterbarkeitsoptionen:

## <a name="sample-full-manifest"></a>Vollständiges Beispielmanifest

```json
{
    "$schema": "https://developer.microsoft.com/json-schemas/teams/v1.14/MicrosoftTeams.schema.json",
    "manifestVersion": "1.14",
    "version": "1.0.0",
    "id": "%MICROSOFT-APP-ID%",
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
            "context": [
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
            "context": [
                "personalTab",
                "channelTab"
            ],
            "name": "Display name of tab",
            "contentUrl": "https://contoso.com/content (displayed in Teams canvas)",
            "websiteUrl": "https://contoso.com/content (displayed in web browser)",
            "searchUrl": "https://contoso.com/content (displayed in web browser)"
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
                    "fetchTask": false ,
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
        "resource": "Resource URL for acquiring auth token for SSO"
    },
    "authorization": {
        "permissions": {
            "resourceSpecific": [
                {
                    "type": "Application",
                    "name": "ChannelSettings.Read.Group"
                },
                {
                    "type": "Delegated",
                    "name": "ChannelMeetingParticipant.Read.Group"
                }
            ]
        }
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
    },
    "meetingExtensionDefinition": {
        "scenes": [
            {
                "id": "9082c811-7e6a-4174-8173-6ccd57d377e6",
                "name": "Getting started sample",
                "file": "scenes/sceneMetadata.json",
                "preview": "scenes/scenePreview.png",
                "maxAudience": 15,
                "seatsReservedForOrganizersOrPresenters": 0
            },
            {
                "id": "afeaed22-f89b-48e1-98b4-46a514344e4a",
                "name": "Sample-1",
                "file": "scenes/sceneMetadata.json",
                "preview": "scenes/scenePreview.png",
                "maxAudience": 15,
                "seatsReservedForOrganizersOrPresenters": 3
            }
        ]
    }
}
```

Das Schema definiert die folgenden Eigenschaften:

## <a name="schema"></a>$schema

Optional, wird jedoch empfohlen – Zeichenfolge

Die https://-URL, die auf das JSON-Schema für das Manifest verweist.

## <a name="manifestversion"></a>manifestVersion

**Erforderlich** – Zeichenfolge

Die Version des Manifestschemas, die dieses Manifest verwendet. Verwenden Sie `1.13`, um die Unterstützung von Teams-Apps in Outlook und Office zu aktivieren. verwenden Sie `1.12` (oder früher) für Apps nur für Teams.

## <a name="version"></a>Version

**Erforderlich** – Zeichenfolge

Die Version einer bestimmten App. Wenn Sie etwas in Ihrem Manifest aktualisieren, muss auch die Version erhöht werden. So wird beim Installieren des neuen Manifests das vorhandene überschrieben, und der Benutzer erhält die neuen Funktionen. Wenn die betreffende App an den Store übermittelt wurde, muss das neue Manifest erneut übermittelt und erneut validiert werden. Die App-Benutzer erhalten das neue aktualisierte Manifest automatisch innerhalb weniger Stunden nach dessen Genehmigung.

Wenn sich die App-Berechtigungsanforderungen ändern, werden die Benutzer aufgefordert, ein Upgrade durchzuführen und der App erneut die Berechtigungen zu erteilen.

Diese Versionszeichenfolge muss dem [SemVer](http://semver.org/)-Standard entsprechen (MAJOR.MINOR.PATCH).

## <a name="id"></a>ID

**Erforderlich** – Microsoft-App-ID

Die ID ist ein eindeutiger, von Microsoft generierter Bezeichner für die App. Sie verfügen über eine ID, wenn Ihr Bot über das Microsoft Bot Framework registriert ist. Sie verfügen über eine ID, wenn sich die Web-App Ihrer Registerkarte bereits bei Microsoft anmeldet. Sie müssen die ID hier eingeben. Andernfalls müssen Sie eine neue ID im [Microsoft-Anwendungsregistrierungsportal](https://aka.ms/appregistrations) generieren. Verwenden Sie die gleiche ID, wenn Sie einen Bot hinzufügen.

> [!NOTE]
> Wenn Sie ein Update für Ihre vorhandene App in AppSource übermitteln, darf die ID in Ihrem Manifest nicht geändert werden.

## <a name="developer"></a>developer

**Erforderlich** – Objekt

Gibt Informationen zu Ihrem Unternehmen an. Für Apps, die an den Microsoft Teams Store übermittelt werden, müssen diese Werte mit den Informationen in Ihrem Store-Eintrag übereinstimmen. Weitere Informationen finden Sie in den [Richtlinien für die Veröffentlichung im Microsoft Teams Store](~/concepts/deploy-and-publish/appsource/publish.md).

|Name| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|
|`name`|32 Zeichen|✔️|Der Anzeigename für den Entwickler.|
|`websiteUrl`|2048 Zeichen|✔️|Die https://-URL zur Website des Entwicklers. Dieser Link muss Benutzer zur Landing Page Ihres Unternehmens oder des produktspezifischen Angebots führen.|
|`privacyUrl`|2048 Zeichen|✔️|Die https://-URL zur Datenschutzerklärung des Entwicklers.|
|`termsOfUseUrl`|2048 Zeichen|✔️|Die https://-URL zu den Nutzungsbedingungen des Entwicklers.|
|`mpnId`|10 Zeichen| |**Optional**: Die Microsoft Partner Network-ID der Partnerorganisation, die die App erstellt.|

## <a name="name"></a>name

**Erforderlich** – Objekt

Der Name Ihrer App-Lösung, der Benutzern in der Microsoft Teams-Umgebung angezeigt wird. Für Apps, die an AppSource übermittelt werden, müssen diese Werte mit den Informationen in Ihrem AppSource-Eintrag übereinstimmen. Die Werte von `short` und `full` müssen unterschiedlich sein.

|Name| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|
|`short`|30 Zeichen|✔️|Der Kurzanzeigename für die App.|
|`full`|100 Zeichen||Der vollständige Name der App; wird verwendet, wenn der vollständige App-Name 30 Zeichen überschreitet.|

## <a name="description"></a>description

**Erforderlich** – Objekt

Beschreibt Ihre App für Benutzer. Für Apps, die an AppSource übermittelt werden, müssen diese Werte mit den Informationen in Ihrem AppSource-Eintrag übereinstimmen.

Stellen Sie sicher, dass Ihre Beschreibung Ihre Lösung beschreibt und potenziellen Kunden hilft zu verstehen, worin ihre Funktion besteht. Sie müssen in der vollständigen Beschreibung angeben, ob ein externes Konto für die Verwendung der App erforderlich ist. Die Werte von `short` und `full` müssen unterschiedlich sein. Ihre kurze Beschreibung kann in der langen Beschreibung nicht wiederholt werden und darf keinen anderen App-Namen enthalten.

|Name| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|
|`short`|80 Zeichen|✔️|Eine kurze Beschreibung der App; wird verwendet, wenn der Platz begrenzt ist.|
|`full`|4.000 Zeichen|✔️|Die vollständige Beschreibung Ihrer App.|

## <a name="localizationinfo"></a>localizationInfo

**Optional** – Objekt

Allows the specification of a default language and provides pointers to more language files. For more information, see [localization](~/concepts/build-and-test/apps-localization.md).

|Name| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|
|`defaultLanguageTag`||✔️|Das Sprachtag der Zeichenfolgen in dieser Manifestdatei auf oberster Ebene.|

### <a name="localizationinfoadditionallanguages"></a>localizationInfo.additionalLanguages

Ein Array von Objekten, die weitere Sprachübersetzungen angeben.

|Name| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|
|`languageTag`||✔️|Das Sprachtag der Zeichenfolgen in der bereitgestellten Datei.|
|`file`||✔️|Ein relativer Dateipfad zur JSON-Datei mit den übersetzten Zeichenfolgen.|

## <a name="icons"></a>Symbole

**Erforderlich** – Objekt

Symbole, die in der Microsoft Teams-App verwendet werden. Die Symboldateien müssen als Teil des Uploadpakets enthalten sein. Weitere Informationen finden Sie unter [Symbole](../../concepts/build-and-test/apps-package.md#app-icons).

|Name| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|
|`outline`|32 x 32 Pixel|✔️|Ein relativer Dateipfad zu einem transparenten, 32 x 32 Pixel großen PNG-Kontursymbol.|
|`color`|192 x 192 Pixel|✔️|Ein relativer Dateipfad zu einem farbigen, 192 x 192 Pixel großen PNG-Symbol.|

## <a name="accentcolor"></a>accentColor

**Erforderlich** – HTML-Hex-Farbcode

Eine Farbe, die als Hintergrund für Ihre Kontursymbole verwendet werden soll.

Bei dem Wert muss es sich um einen gültigen HTML-Farbcode handeln, der mit "#" beginnt, z. B. `#4464ee`.

## <a name="configurabletabs"></a>configurableTabs

**Optional** – Array

Wird verwendet, wenn Ihre App über eine Teamkanal-Registerkartenoberfläche verfügt, die zusätzliche Konfiguration erfordert, bevor sie hinzugefügt wird. Konfigurierbare Registerkarten werden nur in den `team`- und `groupchat`-Bereichen unterstützt, und Sie können dieselben Registerkarten mehrmals konfigurieren. Sie können sie jedoch nur einmal im Manifest definieren.

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`configurationUrl`|string|2048 Zeichen|✔️|Die https://-URL, die beim Konfigurieren der Registerkarte verwendet werden soll.|
|`scopes`|Array von Enumerationen|1|✔️|Derzeit unterstützen konfigurierbare Registerkarten nur die Bereiche `team` und `groupchat`. |
|`canUpdateConfiguration`|Boolescher Wert|||A value indicating whether an instance of the tab's configuration can be updated by the user after creation. Default: **true**.|
|`context` |Array von Enumerationen|6 ||Die Gruppe von `contextItem`-Bereichen, in denen eine [Registerkarte unterstützt wird](../../tabs/how-to/access-teams-context.md). Standard: **[channelTab, privateChatTab, meetingChatTab, meetingDetailsTab]**.|
|`sharePointPreviewImage`|string|2048||A relative file path to a tab preview image for use in SharePoint. Size 1024x768. |
|`supportedSharePointHosts`|Array von Enumerationen|1||Defines how your tab is made available in SharePoint. Options are `sharePointFullPage` and `sharePointWebPart` |

## <a name="statictabs"></a>staticTabs

**Optional** – Array

Definiert eine Reihe von Registerkarten, die standardmäßig "angeheftet" werden können, ohne dass der Benutzer sie manuell hinzufügen muss. Im `personal`-Bereich deklarierte statische Registerkarten werden immer an die persönliche Benutzeroberfläche der App angeheftet. Im `team`-Bereich deklarierte statische Registerkarten werden derzeit nicht unterstützt.

Dieses Element ist ein Array (maximal 16 Elemente), wobei alle Elemente vom Typ `object` sind. Dieser Block ist nur für Lösungen erforderlich, die eine Lösung mit statischen Registerkarten bereitstellen.

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`entityId`|string|64 Zeichen|✔️|Ein eindeutiger Bezeichner für die Entität, die auf der Registerkarte angezeigt wird.|
|`name`|string|128 Zeichen|✔️|Der Anzeigename der Registerkarte in der Kanal-Benutzeroberfläche.|
|`contentUrl`|string||✔️|Die https://-URL, die auf die Entitäts-Benutzeroberfläche verweist, die im Microsoft Teams-Canvas angezeigt werden soll.|
|`websiteUrl`|string|||Die https://-URL, auf die verwiesen wird, wenn sich ein Benutzer für die Anzeige in einem Browser entscheidet.|
|`searchUrl`|string|||Die https://-URL, auf die für die Suchabfragen eines Benutzers verwiesen wird.|
|`scopes`|Array von Enumerationen|1|✔️|Derzeit unterstützen statische Registerkarten nur den `personal`-Bereich. Das bedeutet, dass sie nur als Teil der persönlichen Benutzeroberfläche bereitgestellt werden können.|
|`context` | Array von Enumerationen| 2|| Die Gruppe von `contextItem`-Bereichen, in denen eine Registerkarte unterstützt wird.|

> [!NOTE]
> The searchUrl feature is not available for the third-party developers.
> If your tabs require context-dependent information to display relevant content or for initiating an authentication flow, For more information, see [Get context for your Microsoft Teams tab](../../tabs/how-to/access-teams-context.md).

## <a name="bots"></a>Bots

**Optional** – Array

Definiert eine Bot-Lösung zusammen mit optionalen Informationen wie Standardbefehlseigenschaften.

Das Element ist ein Array (maximal ein Element &mdash; derzeit ist nur ein Bot pro App zulässig) mit allen Elementen des Typs `object`. Dieser Block ist nur für Lösungen erforderlich, die einen Bot umfassen.

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`botId`|string|64 Zeichen|✔️|Die eindeutige Microsoft-App-ID für den Bot, wie bei Bot Framework registriert. Die ID kann mit der Gesamt-[App-ID](#id)übereinstimmen.|
|`scopes`|Array von Enumerationen|3|✔️|Specifies whether the bot offers an experience in the context of a channel in a `team`, in a group chat (`groupchat`), or an experience scoped to an individual user alone (`personal`). These options are non-exclusive.|
|`needsChannelSelector`|Boolesch|||Describes whether or not the bot uses a user hint to add the bot to a specific channel. Default: **`false`**|
|`isNotificationOnly`|Boolescher Wert|||Indicates whether a bot is a one-way, notification-only bot, as opposed to a conversational bot. Default: **`false`**|
|`supportsFiles`|Boolescher Wert|||Indicates whether the bot supports the ability to upload/download files in personal chat. Default: **`false`**|
|`supportsCalling`|Boolesch|||Ein Wert, der angibt, wo ein Bot Audioanrufe unterstützt. **WICHTIG**: Dies ist derzeit eine experimentelle Eigenschaft. Experimentelle Eigenschaften sind u. U. nicht komplett und werden möglicherweise geändert, bevor sie vollständig verfügbar sind.  Die Eigenschaft wird nur zu Test- und Erforschungszwecken bereitgestellt und darf nicht in Produktionsanwendungen verwendet werden. Standard: **`false`**|
|`supportsVideo`|Boolescher Wert|||Ein Wert, der angibt, wo ein Bot Videoanrufe unterstützt. **WICHTIG**: Dies ist derzeit eine experimentelle Eigenschaft. Experimentelle Eigenschaften sind u. U. nicht komplett und werden möglicherweise geändert, bevor sie vollständig verfügbar sind.  Die Eigenschaft wird nur zu Test- und Erforschungszwecken bereitgestellt und darf nicht in Produktionsanwendungen verwendet werden. Standard: **`false`**|

### <a name="botscommandlists"></a>bots.commandLists

Eine Liste der Befehle, die Ihr Bot Benutzern empfehlen kann. Das Objekt ist ein Array (maximal zwei Elemente), wobei alle Elemente vom Typ `object` sind. Sie müssen für jeden Bereich, den Ihr Bot unterstützt, eine separate Befehlsliste definieren. Weitere Informationen finden Sie unter [Bot-Menüs](~/bots/how-to/create-a-bot-commands-menu.md).

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`items.scopes`|Array von Enumerationen|3|✔️|Specifies the scope for which the command list is valid. Options are `team`, `personal`, and `groupchat`.|
|`items.commands`|Array von Objekten|10|✔️|Ein Array von Befehlen, die der Bot unterstützt:<br>`title`: Name des Bot-Befehls (string, 32)<br>`description`: Eine einfache Beschreibung oder ein Beispiel für die Befehlssyntax und zugehörige Argumente (string, 128)|

### <a name="botscommandlistscommands"></a>bots.commandLists.commands

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|title|string|12 |✔️|Der Name des Bot-Befehls.|
|description|string|128 Zeichen|✔️|Eine einfache Textbeschreibung oder ein Beispiel für die Befehlssyntax und zugehörige Argumente.|

## <a name="connectors"></a>connectors

**Optional** – Array

Der `connectors`-Block definiert einen Office 365 Connector für die App.

Das Objekt ist ein Array (maximal ein Element), wobei alle Elemente vom Typ `object` sind. Dieser Block ist nur für Lösungen erforderlich, die einen Connector bereitstellen.

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`configurationUrl`|string|2048 Zeichen|✔️|Die https://-URL, die beim Konfigurieren des Connectors verwendet werden soll.|
|`scopes`|Array von Enumerationen|1|✔️|Specifies whether the Connector offers an experience in the context of a channel in a `team`, or an experience scoped to an individual user alone (`personal`). Currently, only the `team` scope is supported.|
|`connectorId`|string|64 Zeichen|✔️|Ein eindeutiger Bezeichner für den Connector, der seiner ID im [Connectors Developer Dashboard](https://aka.ms/connectorsdashboard) entspricht.|

## <a name="composeextensions"></a>composeExtensions

**Optional** – Array

Definiert eine Nachrichtenerweiterung für die App.

> [!NOTE]
> Der Name des Features wurde im November 2017 von "Compose-Erweiterung" in "Nachrichtenerweiterung" geändert, der Manifestname bleibt jedoch unverändert, sodass vorhandene Erweiterungen weiterhin funktionieren.

Das Element ist ein Array (maximal ein Element), wobei alle Elemente vom Typ `object` sind. Dieser Block ist nur für Lösungen erforderlich, die eine Nachrichtenerweiterung bereitstellen.

|Name| Typ | Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`botId`|string|64|✔️|Die eindeutige Microsoft-App-ID für den Bot, welcher der Nachrichtenerweiterung zugeordnet ist, wie beim Bot Framework registriert. Die ID kann mit der Gesamt-App-ID übereinstimmen.|
|`commands`|Array von Objekten|10|✔️|Array von Befehlen, die von der Nachrichtenerweiterung unterstützt werden.|
|`canUpdateConfiguration`|Boolesch|||A value indicating whether the configuration of a message extension can be updated by the user. Default: **false**.|
|`messageHandlers`|Array von Objekten|5 ||Eine Liste von Handlern, mit denen Apps aufgerufen werden können, wenn bestimmte Bedingungen erfüllt sind.|
|`messageHandlers.type`|string|||The type of message handler. Must be `"link"`.|
|`messageHandlers.value.domains`|Array aus Zeichenfolgen|||Array von Domänen, für die sich der Link-Nachrichtenhandler registrieren kann.|

### <a name="composeextensionscommands"></a>composeExtensions.commands

Ihre Nachrichtenerweiterung muss mindestens einen Befehl deklarieren (maximal 10 Befehle insgesamt). Jeder Befehl wird in Microsoft Teams als potenzielle Interaktion vom Einstiegspunkt in der Benutzeroberfläche angezeigt.

Jedes Befehlselement ist ein Objekt mit folgender Struktur:

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`id`|string|64 Zeichen|✔️|Die ID für den Befehl.|
|`title`|string|32 Zeichen|✔️|Der benutzerfreundliche Name des Befehls.|
|`type`|string|64 Zeichen||Der Befehlstyp. Entweder `query` oder `action`. Standard: **query**.|
|`description`|string|128 Zeichen||Die Beschreibung, die Benutzern angezeigt wird, um den Zweck dieses Befehls anzugeben.|
|`initialRun`|Boolescher Wert|||A Boolean value indicates whether the command runs initially with no parameters. Default is **false**.|
|`context`|Array aus Zeichenfolgen|3||Definiert, wo die Nachrichtenerweiterung aufgerufen werden kann. Eine beliebige Kombination aus `compose`, `commandBox`, `message`. Der Standardwert ist `["compose","commandBox"]`.|
|`fetchTask`|Boolescher Wert|||A Boolean value that indicates if it must fetch the task module dynamically. Default is **false**.|
|`taskInfo`|Objekt|||Geben Sie das Aufgabenmodul an, das vorab geladen werden soll, wenn ein Nachrichtenerweiterungsbefehl verwendet wird.|
|`taskInfo.title`|string|64 Zeichen||Titel des ersten Dialogfelds.|
|`taskInfo.width`|string|||Dialogfensterbreite: entweder eine Angabe in Pixeln oder ein Standardlayout, z. B. "groß", "mittel" oder "klein".|
|`taskInfo.height`|string|||Dialogfensterhöhe: entweder eine Angabe in Pixeln oder ein Standardlayout, z. B. "groß", "mittel" oder "klein".|
|`taskInfo.url`|string|||Anfängliche WebView-URL.|
|`parameters`|Objekt-Array|5 Elemente|✔️|Die Liste der Parameter, die der Befehl verwendet. Minimum: 1; Maximum: 5.|
|`parameters.name`|string|64 Zeichen|✔️|The name of the parameter as it appears in the client. The parameter name is included in the user request.|
|`parameters.title`|string|32 Zeichen|✔️|Benutzerfreundlicher Titel für den Parameter.|
|`parameters.description`|string|128 Zeichen||Benutzerfreundliche Zeichenfolge, die den Zweck dieses Parameters beschreibt.|
|`parameters.value`|string|512 Zeichen||Anfangswert für den Parameter. Der Wert wird derzeit nicht unterstützt.|
|`parameters.inputType`|string|128 Zeichen||Defines the type of control displayed on a task module for`fetchTask: false` . One of `text, textarea, number, date, time, toggle, choiceset` .|
|`parameters.choices`|Array von Objekten|10 Elemente||Die Auswahloptionen für `choiceset`. Wird nur verwendet, wenn `parameter.inputType` `choiceset` ist.|
|`parameters.choices.title`|string|128 Zeichen|✔️|Titel der Auswahl.|
|`parameters.choices.value`|string|512 Zeichen|✔️|Value of the choice.|

## <a name="permissions"></a>Berechtigungen

**Optional** – Array von Zeichenfolgen

An array of `string`, which specifies which permissions the app requests, which let end users know how the extension does. The following options are non-exclusive:

* `identity` &emsp; Erfordert Benutzeridentitätsinformationen.
* `messageTeamMembers`&emsp; Erfordert die Berechtigung, direkte Nachrichten an Teammitglieder zu senden.

Changing these permissions during app update, causes your users to repeat the consent process after they run the updated app. For more information, see [Updating your app](~/concepts/deploy-and-publish/appsource/post-publish/overview.md).

> [!NOTE]
> Berechtigungen sind jetzt veraltet.

## <a name="devicepermissions"></a>devicePermissions

**Optional** – Array von Zeichenfolgen

Provides the native features on a user's device that your app requests access to. Options are:

* `geolocation`
* `media`
* `notifications`
* `midi`
* `openExternal`

## <a name="validdomains"></a>validDomains

**Optional**, außer **erforderlich** wo angegeben.

Eine Liste gültiger Domänen für Websites, die von der App im Microsoft Teams-Client geladen werden sollen. Domäneneinträge können Platzhalter enthalten, z. B. `*.example.com`. Die gültige Domäne entspricht genau einem Segment der Domäne. Wenn sie `a.b.example.com` entsprechen muss, verwenden Sie `*.*.example.com`. Wenn Ihre Registerkartenkonfiguration oder Inhalts-UI zu einer anderen Domäne als jener der Registerkartenkonfiguration führt, muss diese Domäne hier angegeben werden.

Schließen Sie **nicht** die Domänen von Identitätsanbietern ein, die in Ihrer App unterstützt werden sollen. Um sich beispielsweise mit einer Google-ID zu authentifizieren, ist es erforderlich, zu accounts.google.com umzuleiten, sie dürfen jedoch keine accounts.google.com in `validDomains[]`einschließen.

Microsoft Teams-Apps, die ihre eigenen SharePoint-URLs benötigen, um ordnungsgemäß zu funktionieren, enthalten "{teamsitedomain}" in ihrer Liste zulässiger Domänen.

> [!IMPORTANT]
> Fügen Sie keine Domänen hinzu, die außerhalb Ihrer Kontrolle liegen, weder direkt noch über Platzhalter. Beispiel: `yourapp.onmicrosoft.com` ist gültig, `*.onmicrosoft.com` ist hingegen nicht gültig.

Das Objekt ist ein Array, wobei alle Elemente vom Typ `string` sind.

## <a name="webapplicationinfo"></a>webApplicationInfo

**Optional** – Objekt

Geben Sie Ihre Azure Active Directory-App-ID und Microsoft Graph-Informationen an, um Benutzern zu helfen, sich nahtlos bei Ihrer App anzumelden. Falls Ihre App in Microsoft Azure Active Directory (Azure AD) registriert ist, müssen Sie die App-ID angeben. Administratoren können im Microsoft Teams Admin Center Berechtigungen einfach überprüfen und ihre Zustimmung erteilen.

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`id`|string|36 Zeichen|✔️|Azure AD-Anwendungs-ID der App. Diese ID muss eine GUID sein.|
|`resource`|string|2048 Zeichen|✔️|Ressourcen-URL der App zum Abrufen des Authentifizierungstokens für Einmaliges Anmelden. </br> **HINWEIS:** Wenn Sie SSO nicht verwenden, stellen Sie sicher, dass Sie einen Dummy-Zeichenfolgenwert in dieses Feld in Ihr App-Manifest eingeben, `https://notapplicable` um beispielsweise eine Fehlerantwort zu vermeiden. |

## <a name="graphconnector"></a>graphConnector

**Optional** – Objekt

Geben Sie die Graph-Connectorkonfiguration der App an. Wenn dies vorhanden ist, müssen [auch webApplicationInfo.id](#webapplicationinfo) angegeben werden.

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`notificationUrl`|string|2048 Zeichen|✔️|Die URL, an die Graph-Connector-Benachrichtigungen für die Anwendung gesendet werden sollen.|

## <a name="showloadingindicator"></a>showLoadingIndicator

**Optional** – Boolescher Wert

Gibt an, ob die Ladefortschritt angezeigt werden soll, während eine App oder Registerkarte geladen wird. Der Standardwert ist **false**.
>[!NOTE]
>Wenn Sie in Ihrem App-Manifest die Option "True" auswählen `showLoadingIndicator` , ändern Sie zum ordnungsgemäßen Laden der Seite die Inhaltsseiten Ihrer Registerkarten und Aufgabenmodule wie unter ["Anzeigen eines systemeigenen Ladeindikatordokuments](../../tabs/how-to/create-tab-pages/content-page.md#show-a-native-loading-indicator) " beschrieben.

## <a name="isfullscreen"></a>isFullScreen

 **Optional** – Boolescher Wert

Gibt an, ob eine persönliche App ohne Registerkartenkopfleiste gerendert wird (was den Vollbildmodus anzeigt). Der Standardwert ist **false**.

> [!NOTE]
>
> * `isFullScreen` funktioniert nur für Apps, die in Ihrer Organisation veröffentlicht wurden. Quergeladene und veröffentlichte Drittanbieter-Apps können diese Eigenschaft nicht verwenden. (Sie wird ignoriert.)
>
> * `isFullScreen=true` entfernt die von Teams bereitgestellte Kopfzeile und den Titel aus persönlichen Apps und Aufgabenmoduldialogfeldern.

## <a name="activities"></a>Aktivitäten

**Optional** – Objekt

Definiert die Eigenschaften, die Ihre App zum Posten eines Benutzeraktivitätsfeeds verwendet.

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`activityTypes`|Array von Objekten|128 Elemente| | Geben Sie die Arten von Aktivitäten an, die Ihre App in einem Benutzeraktivitätsfeed veröffentlichen kann.|

### <a name="activitiesactivitytypes"></a>activities.activityTypes

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`type`|string|32 Zeichen|✔️|Der Benachrichtigungstyp. *Siehe unten*.|
|`description`|string|128 Zeichen|✔️|A brief description of the notification. *See below*.|
|`templateText`|string|128 Zeichen|✔️|Beispiel: "{actor} hat die Aufgabe {taskId} für Sie erstellt."|

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

When a group install scope is selected, it will define the default capability when the user installs the app. Options are:

* `team`
* `groupchat`
* `meetings`

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`team`|string|||When the install scope selected is `team`, this field specifies the default capability available. Options: `tab`, `bot`, or `connector`.|
|`groupchat`|string|||When the install scope selected is `groupchat`, this field specifies the default capability available. Options: `tab`, `bot`, or `connector`.|
|`meetings`|string|||When the install scope selected is `meetings`, this field specifies the default capability available. Options: `tab`, `bot`, or `connector`.|

## <a name="configurableproperties"></a>configurableProperties

**Optional** – Array

Der `configurableProperties`-Block definiert die App-Eigenschaften, die Microsoft Teams-Administratoren anpassen können. Weitere Informationen finden Sie unter [Aktivieren der App-Anpassung](~/concepts/design/enable-app-customization.md). Das App-Anpassungsfeature wird in benutzerdefinierten oder branchenspezifischen Apps nicht unterstützt.

> [!NOTE]
> Es muss mindestens eine Eigenschaft definiert werden. Sie können in diesem Block maximal neun Eigenschaften definieren.

Sie können eine der folgenden Eigenschaften definieren:

* [Name](#name): Der Anzeigename der App.
* [shortDescription](#description): Die Kurzbeschreibung der App.
* [longDescription](#description): Die lange Beschreibung der App.
* [smallImageUrl](#icons): Das Gliederungssymbol der App.
* [largeImageUrl](#icons): Das Farbsymbol der App.
* [accentColor](#accentcolor): Die zu verwendenden Farben und ein Hintergrund für Ihre Gliederungssymbole.
* [developerUrl](#developer): Die HTTPS-URL der Website des Entwicklers.
* [privacyUrl](#developer): Die HTTPS-URL der Datenschutzrichtlinie des Entwicklers.
* [termsOfUseUrl](#developer): Die HTTPS-URL der Nutzungsbedingungen des Entwicklers.

## <a name="supportedchanneltypes"></a>supportedChannelTypes

**Optional** – Array

Aktiviert Ihre App in Kanälen die keine Standardkanäle sind. Wenn Ihre App einen Teambereich unterstützt und diese Eigenschaft definiert ist, aktiviert Microsoft Teams Ihre App in jedem Kanaltyp entsprechend. Derzeit werden die Kanaltypen „Privat“ und „Freigegeben“ unterstützt.

> [!NOTE]
>
> * Wenn Ihre App einen Teambereich unterstützt, funktioniert dieser in den Standardkanälen unabhängig von den in dieser Eigenschaft definierten Werten.
> * Ihre Anwendung kann die individuellen Eigenschaften der einzelnen Kanaltypen berücksichtigen, um ordnungsgemäß zu funktionieren. Informationen zum Aktivieren Ihrer Registerkarte für private und freigegebene Kanäle finden [Sie unter Abrufen des Kontexts in privaten Kanälen](~/tabs/how-to/access-teams-context.md#retrieve-context-in-private-channels) und [Abrufen von Kontext in freigegebenen Kanälen](../../tabs/how-to/access-teams-context.md#get-context-in-shared-channels)

## <a name="defaultblockuntiladminaction"></a>defaultBlockUntilAdminAction

**Optional** – Boolescher Wert

Wenn die `defaultBlockUntilAdminAction`-Eigenschaft auf **true** festgelegt ist, ist die App so lange standardmäßig für Benutzer ausgeblendet, bis der Administrator sie zulässt. Bei Festlegung auf **true** ist die App für alle Mandanten und Endbenutzer ausgeblendet. Mandantenadministratoren können die App im Microsoft Teams Admin Center sehen und Maßnahmen ergreifen, um sie zuzulassen oder zu blockieren. Der Standardwert ist **false**. Weitere Informationen zum Standardmäßigen App-Block finden Sie unter ["Apps standardmäßig blockieren" für Benutzer, bis ein Administrator dies genehmigt.](../../concepts/design/enable-app-customization.md#block-apps-by-default-for-users-until-an-admin-approves)

## <a name="publisherdocsurl"></a>publisherDocsUrl

**Optional** – Zeichenfolge

**Maximale Länge**: 128 Zeichen

`publisherDocsUrl` ist eine HTTPS-URL zu einer Informationsseite, auf der Administratoren Anweisungen finden, bevor sie eine App zulassen, die standardmäßig blockiert ist. Sie kann auch verwendet werden, um Anweisungen oder Informationen zur App bereitzustellen, die für den Mandantenadministrator nützlich sein könnten.

## <a name="subscriptionoffer"></a>subscriptionOffer

**Optional** – Objekt

Gibt das Ihrer App zugeordnete SaaS-Angebot an.

|Name| Typ|Maximale Größe|Erforderlich|Beschreibung|
|---|---|---|---|---|
|`offerId`| string | 2048 Zeichen | ✔️ | A unique identifier that includes your Publisher ID and Offer ID, which you can find in [Partner Center](https://partner.microsoft.com/dashboard). You must format the string as `publisherId.offerId`.|

## <a name="meetingextensiondefinition"></a>meetingExtensionDefinition

**Optional** – Objekt

Specify meeting extension definition. For more information, see [custom Together Mode scenes in Teams](../../apps-in-teams-meetings/teams-together-mode.md).

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`scenes`|Array von Objekten| 5 Elemente||Unterstützte Besprechungsszenen.|
|`supportsStreaming`|Boolesch|||Ein Wert, der angibt, ob eine App die Audio- und Videoinhalte der Besprechung auf einen RTMP-Endpunkt (Real-Time Meeting Protocol) streamen kann. Der Standardwert ist **false**.|

### <a name="meetingextensiondefinitionscenes"></a>meetingExtensionDefinition.scenes

|Name| Typ|Maximale Größe|Erforderlich |Beschreibung|
|---|---|---|---|---|
|`id`|||✔️| Der eindeutige Bezeichner für die Szene. Diese ID muss eine GUID sein. |
|`name`| string | 128 Zeichen |✔️| Der Name der Szene. |
|`file`|||✔️| Der relative Dateipfad zur JSON-Metadatendatei der Szenen. |
|`preview`|||✔️| Der relative Dateipfad zum PNG-Vorschausymbol der Szenen. |
|`maxAudience`| ganze Zahl | 50  |✔️| Die maximale Anzahl von Zielgruppen, die in der Szene unterstützt werden. |
|`seatsReservedForOrganizersOrPresenters`| ganze Zahl | 50 |✔️| Die Anzahl der Plätze, die für Organisatoren oder Moderatoren reserviert sind.|

## <a name="authorization"></a>Autorisierung

**Optional** – Objekt

> [!NOTE]
> If you set the `manifestVersion` property to 1.12, the authorization property is incompatible with the older versions (version 1.11 or earlier) of the manifest. Authorization is supported for manifest version 1.12.

Spezifizieren und konsolidieren Sie autorisierungsbezogene Informationen für die App.

|Name| Typ|Maximale Größe|Erforderlich |Beschreibung|
|---|---|---|---|---|
|`permissions`||||Liste der Berechtigungen, welche die App benötigt, um zu funktionieren.|

### <a name="authorizationpermissions"></a>authorization.permissions

|Name| Typ|Maximale Größe|Erforderlich |Beschreibung|
|---|---|---|---|---|
|`resourceSpecific`| Array von Objekten|16 Elemente||Berechtigungen, die den Datenzugriff auf Ebene der Ressourceninstanz schützen.|

### <a name="authorizationpermissionsresourcespecific"></a>authorization.permissions.resourceSpecific

|Name| Typ|Maximale Größe|Erforderlich |Beschreibung|
|---|---|---|---|---|
|`type`|string||✔️| The type of the resource-specific permission. Options: `Application` and `Delegated`.|
|`name`|string|128 Zeichen|✔️|Der Name der ressourcenspezifischen Berechtigung. Weitere Informationen finden Sie unter [Ressourcenspezifische Anwendungsberechtigungen](#resource-specific-application-permissions) und [Ressourcenspezifische delegierte Berechtigungen](#resource-specific-delegated-permissions)|

#### <a name="resource-specific-application-permissions"></a>Ressourcenspezifische Anwendungsberechtigungen

Anwendungsberechtigungen ermöglichen der App den Zugriff auf Daten, ohne dass ein Benutzer angemeldet ist. Informationen zu Anwendungsberechtigungen finden Sie unter [Ressourcenspezifische Zustimmung für MS Graph und MS BotSDK](../../graph-api/rsc/resource-specific-consent.md).

#### <a name="resource-specific-delegated-permissions"></a>Ressourcenspezifische delegierte Berechtigungen

Delegierte Berechtigungen ermöglichen der App den Zugriff auf Daten im Namen des angemeldeten Benutzers.

* **Ressourcenspezifische delegierte Berechtigungen für Teams**

    |**Name**|**Beschreibung**|
    |---|---|
    |`ChannelMeetingParticipant.Read.Group`| Ermöglicht es der App, im Namen des angemeldeten Benutzers die Teilnehmerinformationen (Name, Rolle, ID, Beitritts- und Abwesenheitszeiten) von Channel-Meetings zu lesen, die mit diesem Team verbunden sind.|
    |`InAppPurchase.Allow.Group`| Ermöglicht der App, Marketplace-Angebote für Benutzer in diesem Team anzuzeigen und ihre Käufe innerhalb der App im Namen des angemeldeten Benutzers abzuschließen.|
    |`ChannelMeetingStage.Write.Group`| Ermöglicht es der App, in Channel-Meetings, die mit diesem Team verbunden sind, im Namen des angemeldeten Benutzers Inhalte auf der Meetingbühne anzuzeigen.|
    |`LiveShareSession.ReadWrite.Group`|Ermöglicht der App, Live-Freigabesitzungen für Besprechungen zu erstellen und zu synchronisieren, die diesem Team zugeordnet sind, und im Namen des angemeldeten Benutzers auf verwandte Informationen über die Teilnehmerliste der Besprechung zuzugreifen, z. B. die Besprechungsrolle des Mitglieds.|

* **Ressourcenspezifische delegierte Berechtigungen für Chats oder Besprechungen**

    |**Name**|**Beschreibung**|
    |---|---|
    |`InAppPurchase.Allow.Chat`|Ermöglicht es der App, den Nutzern in diesem Chat und allen damit verbundenen Treffen Marktplatzangebote zu zeigen und ihre Einkäufe innerhalb der App im Namen des angemeldeten Nutzers abzuschließen.|
    |`MeetingStage.Write.Chat`|Ermöglicht es der App, in Meetings, die mit diesem Chat verbunden sind, im Namen des angemeldeten Benutzers Inhalte auf der Meeting-Bühne zu zeigen.|
    |`OnlineMeetingParticipant.Read.Chat`|Ermöglicht es der App, im Namen des angemeldeten Benutzers die Teilnehmerinformationen, einschließlich Name, Rolle, ID, Beitritts- und Austrittszeiten, der mit diesem Chat verbundenen Besprechung zu lesen.|
    |`OnlineMeetingParticipant.ToggleIncomingAudio.Chat`|Ermöglicht der App, eingehende Audiodaten für Teilnehmer an Meetings, die mit diesem Chat verknüpft sind, im Namen des angemeldeten Benutzers umzuschalten.|
    |`LiveShareSession.ReadWrite.Chat`|Ermöglicht der App, Live-Freigabesitzungen für Besprechungen im Zusammenhang mit diesem Chat zu erstellen und zu synchronisieren und im Namen des angemeldeten Benutzers auf verwandte Informationen über die Teilnehmerliste der Besprechung zuzugreifen, z. B. die Besprechungsrolle des Mitglieds.|
   |`OnlineMeetingIncomingAudio.Detect.Chat`|Ermöglicht der App, Änderungen am Status eingehender Audiodaten in Besprechungen im Zusammenhang mit diesem Chat im Namen des angemeldeten Benutzers zu erkennen.|

* **Ressourcespezifische delegierte Berechtigungen für Benutzer**

    |**Name**|**Beschreibung**|
    |---|---|
    |`InAppPurchase.Allow.User`|Ermöglicht es der App, dem Benutzer Angebote auf dem Marktplatz zu zeigen und die Einkäufe des Benutzers innerhalb der App im Namen des angemeldeten Benutzers abzuschließen.|

## <a name="create-a-manifest-file"></a>Erstellen einer Manifestdatei

Wenn Ihre App nicht über eine Teams-App-Manifestdatei verfügt, müssen Sie diese erstellen.

So erstellen Sie eine Teams-App-Manifestdatei:

1. Verwenden Sie das [Beispielmanifestschema](#sample-full-manifest), um eine JSON-Datei zu erstellen.
1. Speichern Sie diese im Stammverzeichnis Ihres Projektordners als `manifest.json`.

<br>
<details>
<summary>Hier ist ein Beispiel für ein Manifestschema für eine Registerkarten-App mit aktiviertem SSO:</summary>
<br>

> [!NOTE]
> Der hier gezeigte Inhalt des Manifestbeispiels gilt nur für eine Registerkarten-App. Es werden Beispielwerte für den Subdomänen-URI verwendet. Weitere Informationen finden Sie unter [Beispielmanifestschema](#sample-full-manifest).

  ```json
{ 
  "$schema": "https://developer.microsoft.com/json-schemas/teams/v1.11/MicrosoftTeams.schema.json", 
 "manifestVersion": "1.12", 
 "version": "1.0.0", 
 "id": "{new GUID for this Teams app - not the Azure AD App ID}", 
 "developer": { 
 "name": "Microsoft", 
 "websiteUrl": "https://www.microsoft.com", 
 "privacyUrl": "https://www.microsoft.com/privacy", 
 "termsOfUseUrl": "https://www.microsoft.com/termsofuse" 
  }, 

  "name": { 
    "short": "Teams Auth SSO", 
    "full": "Teams Auth SSO" 
  }, 


  "description": { 
    "short": "Teams Auth SSO app", 
    "full": "The Teams Auth SSO app" 
  }, 

  "icons": { 
    "outline": "outline.png", 
    "color": "color.png" 
  }, 

  "accentColor": "#60A18E", 
  "staticTabs": [ 
    { 
     "entityId": "auth", 
     "name": "Auth", 
     "contentUrl": "https://https://subdomain.example.com/Home/Index", 
     "scopes": [ "personal" ] 
    } 
  ], 

  "configurableTabs": [ 
    { 
     "configurationUrl": "https://subdomain.example.com/Home/Configure", 
     "canUpdateConfiguration": true, 
     "scopes": [ 
     "team" 
      ] 
    } 
  ], 
  "permissions": [ "identity", "messageTeamMembers" ], 
  "validDomains": [ 
   "{subdomain or ngrok url}" 
  ], 
  "webApplicationInfo": { 
    "id": "{Azure AD AppId}", 
    "resource": "api://subdomain.example.com/{Azure AD AppId}" 
  }
} 
```

</details>

## <a name="see-also"></a>Siehe auch

* [Grundlegendes zur Struktur von Microsoft Teams-Apps](~/concepts/design/app-structure.md)
* [Aktivieren der App-Anpassung](~/concepts/design/enable-app-customization.md)
* [Lokalisieren IhrerApp](~/concepts/build-and-test/apps-localization.md)
* [Integrieren von Medienfunktionen](~/concepts/device-capabilities/media-capabilities.md)
* [Öffentliche Entwickler-Vorschau des Manifest-Schemas für Microsoft Teams](manifest-schema-dev-preview.md)
