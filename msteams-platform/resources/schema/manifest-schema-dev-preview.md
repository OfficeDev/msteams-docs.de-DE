---
title: Schemareferenz für öffentliche Entwicklervorschaumanifest
description: Beispielmanifestdatei und Beschreibung aller komponenten, die für Microsoft Teams unterstützt werden
ms.topic: reference
keywords: Teams-Manifestschema Developer Preview
ms.localizationpriority: medium
ms.date: 11/15/2021
ms.openlocfilehash: e388dc955acbe3ba0c116f2a5d5f610d3cbdc3c3
ms.sourcegitcommit: 0117c4e750a388a37cc189bba8fc0deafc3fd230
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/27/2022
ms.locfileid: "65104063"
---
# <a name="reference-public-developer-preview-manifest-schema-for-microsoft-teams"></a>Referenz: Öffentliches Entwicklervorschaumanifestschema für Microsoft Teams

Informationen zum Aktivieren der Entwicklervorschau finden Sie in der [öffentlichen Entwicklervorschau für Microsoft Teams](~/resources/dev-preview/developer-preview-intro.md).

> [!NOTE]
> Wenn Sie keine Entwicklervorschaufeatures verwenden, einschließlich [der Ausführung Teams persönlichen Registerkarten und Nachrichtenerweiterungen in Outlook und Office](../../m365-apps/overview.md), verwenden Sie stattdessen das [App-Manifest für GA-Features](~/resources/schema/manifest-schema.md).

Das Microsoft Teams-Manifest beschreibt, wie die App in die Microsoft Teams Plattform integriert wird. Ihr Manifest muss dem unter [`https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json`](https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json) gehosteten Schema entsprechen.

## <a name="sample-full-manifest"></a>Vollständiges Beispielmanifest

```json
{
    "$schema": "https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json",
    "manifestVersion": "devPreview",
    "version": "1.0.0",
    "id": "%MICROSOFT-APP-ID%",
    "packageName": "com.example.myapp",
    "devicePermissions": [
        "geolocation",
        "media"
    ],
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
            "scopes": [
                "team",
                "groupchat"
            ]"context": []
        }
    ],
    "staticTabs": [
        {
            "entityId": "idForPage",
            "name": "Display name of tab",
            "contentUrl": "https://contoso.com/content?host=msteams",
            "contentBotId": "Specifies to the app that tab is an Adaptive Card Tab. You can either provide the contentBotId or contentUrl.",
            "websiteUrl": "https://contoso.com/content",
            "scopes": [
                "personal"
            ]
        }
    ],
    "bots": [
        {
            "botId": "%MICROSOFT-APP-ID-REGISTERED-WITH-BOT-FRAMEWORK%",
            "needsChannelSelector": false,
            "isNotificationOnly": false,
            "scopes": [
                "team",
                "personal",
                "groupchat"
            ],
            "supportsFiles": true,
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
                            "title": "Command N",
                            "description": "Description of Command N"
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
            "configurationUrl": "https://contoso.com/teamsconnector/configure",
            "scopes": [
                "team"
            ]
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
                    "type": "search",
                    "context": [
                        "compose",
                        "commandBox"
                    ],
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
                    "type": "action",
                    "fetchTask": true,
                    "context": [
                        "message"
                    ],
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
                    "id": "exampleMessageHandler",
                    "title": "Message Handler",
                    "description": "Domains that will create a preview when pasted into the compose box",
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
            ]
        }
    ],
    "permissions": [
        "identity",
        "messageTeamMembers"
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
    },
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

*Optional, aber empfohlen* &ndash; Schnur

Die `https://` URL, die auf das JSON-Schema für das Manifest verweist.

## <a name="manifestversion"></a>manifestVersion

**Erforderlich** &ndash; Schnur

Die Version des Manifestschemas, das von diesem Manifest verwendet wird. Wird `m365DevPreview` nur verwendet, wenn Sie eine Vorschau Teams Apps anzeigen, die [in Office und Outlook ausgeführt](../../m365-apps/overview.md) werden. Andernfalls für alle anderen Teams Vorschaufeatures verwenden`devPreview`.

## <a name="version"></a>Version

**Erforderlich** &ndash; Schnur

Die Version der jeweiligen App. Wenn Sie etwas in Ihrem Manifest aktualisieren, muss die Version ebenfalls erhöht werden. Auf diese Weise wird bei der Installation des neuen Manifests das vorhandene überschrieben, und der Benutzer erhält die neue Funktionalität. Wenn diese App an den Store übermittelt wurde, muss das neue Manifest erneut übermittelt und erneut überprüft werden. Anschließend erhalten Benutzer dieser App das neue aktualisierte Manifest in einigen Stunden automatisch, nachdem es genehmigt wurde.

Wenn die App eine Änderung der Berechtigungen angefordert hat, werden die Benutzer aufgefordert, ein Upgrade auszuführen und der App erneut zuzustimmen.

Diese Versionszeichenfolge muss dem [SemVer](http://semver.org/)-Standard entsprechen (MAJOR.MINOR.PATCH).

## <a name="id"></a>id

**Erforderlich** &ndash; Microsoft-App-ID

Der eindeutige von Microsoft generierte Bezeichner für diese App. Wenn Sie einen Bot über die Microsoft Bot Framework registriert haben oder sich die Web-App Ihrer Registerkarte bereits bei Microsoft anmeldet, sollten Sie bereits über eine ID verfügen und diese hier eingeben. Andernfalls sollten Sie eine neue ID im Microsoft-Anwendungsregistrierungsportal ([Meine Anwendungen](https://apps.dev.microsoft.com)) generieren, sie hier eingeben und sie dann wiederverwenden, wenn Sie [einen Bot hinzufügen](~/bots/how-to/create-a-bot-for-teams.md).

## <a name="packagename"></a>packageName

**Erforderlich** &ndash; Schnur

Ein eindeutiger Bezeichner für diese App in umgekehrter Domänennotation; beispiel: "com.example.myapp".

## <a name="developer"></a>developer

Erforderlich:

Gibt Informationen zu Ihrem Unternehmen an. Für Apps, die an AppSource (früher Office Store) übermittelt wurden, müssen diese Werte mit den Informationen in Ihrem AppSource-Eintrag übereinstimmen.

|Name| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|
|`name`|32 Zeichen|✔|Der Anzeigename für den Entwickler.|
|`websiteUrl`|2048 Zeichen|✔|Die https://-URL zur Website des Entwicklers. Über diesen Link sollten Benutzer zu Ihrer Unternehmens- oder produktspezifischen Startseite gelangen.|
|`privacyUrl`|2048 Zeichen|✔|Die https://-URL zur Datenschutzerklärung des Entwicklers.|
|`termsOfUseUrl`|2048 Zeichen|✔|Die https://-URL zu den Nutzungsbedingungen des Entwicklers.|
|`mpnId`|10 Zeichen|✔|**Optional**: Die Microsoft Partner Network-ID der Partnerorganisation, die die App erstellt.|

## <a name="localizationinfo"></a>localizationInfo

Optional:

Ermöglicht die Angabe einer Standardsprache sowie Zeiger auf zusätzliche Sprachdateien. Siehe [Lokalisierung](~/concepts/build-and-test/apps-localization.md).

|Name| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|
|`defaultLanguageTag`|4 Zeichen|✔|Das Sprachtag der Zeichenfolgen in dieser Manifestdatei der obersten Ebene.|

### <a name="localizationinfoadditionallanguages"></a>localizationInfo.additionalLanguages

Ein Array von Objekten, die zusätzliche Sprachübersetzungen angeben.

|Name| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|
|`languageTag`|4 Zeichen|✔|Das Sprachtag der Zeichenfolgen in der bereitgestellten Datei.|
|`file`|4 Zeichen|✔|Ein relativer Dateipfad zu einer JSON-Datei, die die übersetzten Zeichenfolgen enthält.|

## <a name="name"></a>name

Erforderlich:

Der Name Ihrer App-Lösung, der Benutzern in der Microsoft Teams-Umgebung angezeigt wird. Für Apps, die an AppSource übermittelt werden, müssen diese Werte mit den Informationen in Ihrem AppSource-Eintrag übereinstimmen. Die Werte von `short` und `full` sollten nicht identisch sein.

|Name| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|
|`short`|30 Zeichen|✔|Der Kurzanzeigename für die App.|
|`full`|100 Zeichen||Der vollständige Name der App; wird verwendet, wenn der vollständige App-Name 30 Zeichen überschreitet.|

## <a name="description"></a>description

Erforderlich:

Beschreibt Ihre App für Benutzer. Für an AppSource übermittelte Apps müssen diese Werte mit den Informationen in Ihrem AppSource-Eintrag übereinstimmen.

Stellen Sie sicher, dass Ihre Beschreibung Ihre Erfahrung genau beschreibt und Informationen bereitstellt, um potenziellen Kunden zu helfen, zu verstehen, was Ihre Erfahrung bewirkt. Beachten Sie auch in der vollständigen Beschreibung, ob ein externes Konto für die Verwendung erforderlich ist. Die Werte von `short` und `full` sollten nicht identisch sein.  Ihre kurzbeschreibung darf nicht innerhalb der langen Beschreibung wiederholt werden und darf keinen anderen App-Namen enthalten.

|Name| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|
|`short`|80 Zeichen|✔|Eine kurze Beschreibung der App; wird verwendet, wenn der Platz begrenzt ist.|
|`full`|4.000 Zeichen|✔|Die vollständige Beschreibung Ihrer App.|

## <a name="icons"></a>Symbole

Erforderlich:

Symbole, die in der Microsoft Teams-App verwendet werden. Die Symboldateien müssen als Teil des Uploadpakets enthalten sein.

|Name| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|
|`outline`|2048 Zeichen|✔|Ein relativer Dateipfad zu einem transparenten, 32 x 32 Pixel großen PNG-Kontursymbol.|
|`color`|2048 Zeichen|✔|Ein relativer Dateipfad zu einem farbigen, 192 x 192 Pixel großen PNG-Symbol.|

## <a name="accentcolor"></a>accentColor

**Erforderlich** &ndash; Schnur

Eine Farbe, die in Verbindung mit und als Hintergrund für Ihre Gliederungssymbole verwendet werden soll.

Bei dem Wert muss es sich um einen gültigen HTML-Farbcode handeln, der mit "#" beginnt, z. B. `#4464ee`.

## <a name="configurabletabs"></a>configurableTabs

Optional:

Wird verwendet, wenn Ihre App-Lösung über Teamkanal-Registerkarten verfügt, die eine zusätzliche Konfiguration erfordern, bevor sie hinzugefügt werden. Konfigurierbare Registerkarten werden nur im Teams-Bereich unterstützt, und derzeit wird nur eine Registerkarte pro App unterstützt.

Das Objekt ist ein Array, wobei alle Elemente vom Typ `object` sind. Dieser Block ist nur für Lösungen erforderlich, die eine konfigurierbare Kanalregisterkartenlösung bereitstellen.

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`configurationUrl`|Zeichenfolge|2048 Zeichen|✔|Die https://-URL, die beim Konfigurieren der Registerkarte verwendet werden soll.|
|`canUpdateConfiguration`|Boolesch|||Der Wert, der angibt, ob eine Instanz der Registerkartenkonfiguration nach der Erstellung vom Benutzer aktualisiert werden kann. Standard: `true`|
|`scopes`|Array von Enumerationen|1|✔|Derzeit unterstützen konfigurierbare Registerkarten nur die Bereiche `team` und `groupchat`. |
|`context` |Array von Enumerationen|6 ||Die Gruppe von `contextItem`-Bereichen, in denen eine [Registerkarte unterstützt wird](../../tabs/how-to/access-teams-context.md). Standard: `channelTab`, `privateChatTab`, `meetingChatTab`, `meetingDetailsTab`, `meetingSidePanel`und `meetingStage`.|
|`sharePointPreviewImage`|Zeichenfolge|2048||Ein relativer Dateipfad zu einem Registerkarten-Vorschaubild zur Verwendung in SharePoint. Größe: 1024 x 768. |
|`supportedSharePointHosts`|Array von Enumerationen|1||Definiert, wie Ihre Registerkarte in SharePoint verfügbar gemacht wird. Optionen: `sharePointFullPage` und `sharePointWebPart` |

## <a name="statictabs"></a>staticTabs

Optional:

Definiert eine Reihe von Registerkarten, die standardmäßig "angeheftet" werden können, ohne dass der Benutzer sie manuell hinzufügen muss. Im `personal`-Bereich deklarierte statische Registerkarten werden immer an die persönliche Benutzeroberfläche der App angeheftet. Im `team`-Bereich deklarierte statische Registerkarten werden derzeit nicht unterstützt.

Rendern Sie Registerkarten mit adaptiven Karten, indem Sie sie anstelle `contentUrl` des **staticTabs-Blocks** angeben`contentBotId`.

Das Objekt ist ein Array (maximal 16 Elemente) mit allen Elementen des Typs `object`. Dieser Block ist nur für Lösungen erforderlich, die eine Lösung mit statischen Registerkarten bereitstellen.

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`entityId`|String|64 Zeichen|✔|Ein eindeutiger Bezeichner für die Entität, die auf der Registerkarte angezeigt wird.|
|`name`|Zeichenfolge|128 Zeichen|✔|Der Anzeigename der Registerkarte in der Kanal-Benutzeroberfläche.|
|`contentUrl`|Zeichenfolge|2048 Zeichen|✔|Die https://-URL, die auf die Entitäts-Benutzeroberfläche verweist, die im Microsoft Teams-Canvas angezeigt werden soll.|
|`contentBotId`|   | | | Die Microsoft Teams App-ID, die für den Bot im Bot Framework-Portal angegeben wurde. |
|`websiteUrl`|Zeichenfolge|2048 Zeichen||Die https:// URL, die darauf verweist, wenn ein Benutzer sich für die Anzeige in einem Browser entscheidet.|
|`scopes`|Array von Enumerationen|1|✔|Derzeit unterstützen statische Registerkarten nur den `personal`-Bereich. Das bedeutet, dass sie nur als Teil der persönlichen Benutzeroberfläche bereitgestellt werden können.|

## <a name="bots"></a>Bots

Optional:

Definiert eine Bot-Lösung zusammen mit optionalen Informationen wie Standardbefehlseigenschaften.

Das Objekt ist ein Array (maximal 1 Element&mdash; ist derzeit nur ein Bot pro App zulässig) mit allen Elementen des Typs `object`. Dieser Block ist nur für Lösungen erforderlich, die einen Bot umfassen.

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`botId`|String|64 Zeichen|✔|Die eindeutige Microsoft-App-ID für den Bot, wie bei Bot Framework registriert. Dies kann mit der allgemeinen [App-ID](#id) identisch sein.|
|`needsChannelSelector`|Boolesch|||Beschreibt, ob der Bot einen Benutzerhinweis verwendet, um den Bot einem bestimmten Kanal hinzuzufügen. Standard: `false`|
|`isNotificationOnly`|Boolesch|||Gibt an, ob es sich bei einem Bot um einen unidirektionalen Bot mit nur Benachrichtigungsfunktion und nicht um einen dialogorientierten Bot handelt. Standard: `false`|
|`supportsFiles`|Boolesch|||Gibt an, ob der Bot die Möglichkeit unterstützt, Dateien im persönlichen Chat hoch-/herunterzuladen. Standard: `false`|
|`scopes`|Array von Enumerationen|3|✔|Gibt an, ob der Bot eine Umgebung im Kontext eines Kanals in einem `team` oder Gruppenchat (`groupchat`) bietet, oder aber eine Umgebung einzig für einen bestimmten Benutzer (`personal`). Diese Optionen sind nicht exklusiv.|

### <a name="botscommandlists"></a>bots.commandLists

Eine optionale Liste von Befehlen, die Ihr Bot Benutzern vorschlagen kann. Das Objekt ist ein Array (maximal 2 Elemente) mit allen Elementen des Typs `object`. Sie müssen eine separate Befehlsliste für jeden Bereich definieren, den Ihr Bot unterstützt. Weitere Informationen finden Sie unter [Bot-Menüs](~/bots/how-to/create-a-bot-commands-menu.md).

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`items.scopes`|Array von Enumerationen|3|✔|Gibt den Bereich an, für den die Befehlsliste gültig ist. Optionen sind `team`, `personal` und `groupchat`.|
|`items.commands`|Array von Objekten|10|✔|Ein Array von Befehlen, die der Bot unterstützt:<br>`title`: Der Name des Bot-Befehls (Zeichenfolge, 32).<br>`description`: Eine einfache Beschreibung oder ein Beispiel für die Befehlssyntax und zugehörige Argumente (string, 128)|

## <a name="connectors"></a>connectors

Optional:

Der `connectors`-Block definiert einen Office 365 Connector für die App.

Das Objekt ist ein Array (maximal 1 Element) mit allen Elementen vom Typ `object`. Dieser Block ist nur für Lösungen erforderlich, die einen Connector bereitstellen.

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`configurationUrl`|Zeichenfolge|2048 Zeichen|✔|Die https://-URL, die beim Konfigurieren des Connectors verwendet werden soll.|
|`connectorId`|String|64 Zeichen|✔|Ein eindeutiger Bezeichner für den Connector, der seiner ID im [Connectors Developer Dashboard](https://aka.ms/connectorsdashboard) entspricht.|
|`scopes`|Array von Enumerationen|1|✔|Gibt an, ob der Connector eine Umgebung im Kontext eines Kanals in einem `team` oder aber eine Umgebung einzig für einen bestimmten Benutzer (`personal`) bietet. Derzeit wird nur der `team`-Bereich unterstützt.|

## <a name="composeextensions"></a>composeExtensions

Optional:

Definiert eine Nachrichtenerweiterung für die App.

> [!NOTE]
> Der Name des Features wurde im November 2017 von "Erweiterung verfassen" in "Nachrichtenerweiterung" geändert, der Manifestname bleibt jedoch unverändert, sodass vorhandene Erweiterungen weiterhin funktionieren.

Das Objekt ist ein Array (maximal 1 Element) mit allen Elementen vom Typ `object`. Dieser Block ist nur für Lösungen erforderlich, die eine Nachrichtenerweiterung bereitstellen.

|Name| Typ | Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`botId`|Zeichenfolge|64|✔|Die eindeutige Microsoft-App-ID für den Bot, der die Nachrichtenerweiterung unterstützt, wie sie im Bot Framework registriert ist. Dies kann mit der allgemeinen [App-ID](#id) identisch sein.|
|`canUpdateConfiguration`|Boolesch|||Ein Wert, der angibt, ob die Konfiguration einer Nachrichtenerweiterung vom Benutzer aktualisiert werden kann. Der Standardwert lautet `false`.|
|`commands`|Array des Objekts|10|✔|Array von Befehlen, die die Nachrichtenerweiterung unterstützt|

### <a name="composeextensionscommands"></a>composeExtensions.commands

Ihre Nachrichtenerweiterung sollte mindestens einen Befehl deklarieren. Jeder Befehl wird in Microsoft Teams als potenzielle Interaktion vom Einstiegspunkt in der Benutzeroberfläche angezeigt. Es gibt maximal 10 Befehle.

Jedes Befehlselement ist ein Objekt mit folgender Struktur:

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`id`|String|64 Zeichen|✔|Die ID für den Befehl.|
|`type`|String|64 Zeichen||Der Befehlstyp. Entweder `query` oder `action`. Standard: `query`|
|`title`|Zeichenfolge|32 Zeichen|✔|Der benutzerfreundliche Name des Befehls.|
|`description`|Zeichenfolge|128 Zeichen||Die Beschreibung, die Benutzern angezeigt wird, um den Zweck dieses Befehls anzugeben.|
|`initialRun`|Boolescher Wert|||Ein boolescher Wert, der angibt, ob der Befehl zunächst ohne Parameter ausgeführt werden soll. Standard: `false`|
|`context`|Zeichenfolgenarray|3||Definiert, wo die Nachrichtenerweiterung aufgerufen werden kann. Eine beliebige Kombination von `compose`, `commandBox`, `message`. Der Standardwert ist `["compose", "commandBox"]`|
|`fetchTask`|Boolesch|||Ein boolescher Wert, der angibt, ob das Aufgabenmodul dynamisch abgerufen werden soll.|
|`taskInfo`|Objekt|||Geben Sie das Aufgabenmodul an, das bei Verwendung eines Befehls für die Nachrichtenerweiterung vorab geladen werden soll.|
|`taskInfo.title`|Zeichenfolge|64||Titel des ersten Dialogfelds.|
|`taskInfo.width`|Zeichenfolge|||Dialogfensterbreite: entweder eine Angabe in Pixeln oder ein Standardlayout, z. B. "groß", "mittel" oder "klein".|
|`taskInfo.height`|Zeichenfolge|||Dialogfensterhöhe: entweder eine Angabe in Pixeln oder ein Standardlayout, z. B. "groß", "mittel" oder "klein".|
|`taskInfo.url`|Zeichenfolge|||Anfängliche WebView-URL.|
|`messageHandlers`|Array von Objekten|5||Eine Liste von Handlern, mit denen Apps aufgerufen werden können, wenn bestimmte Bedingungen erfüllt sind. Domänen müssen auch in `validDomains`aufgeführt sein.|
|`messageHandlers.type`|Zeichenfolge|||Der Typ des Nachrichtenhandlers. Muss `"link"` sein.|
|`messageHandlers.value.domains`|Zeichenfolgenarray|||Array von Domänen, für die sich der Link-Nachrichtenhandler registrieren kann.|
|`parameters`|Array des Objekts|5|✔|Die Liste der Parameter, die der Befehl verwendet. Mindestens: 1; maximal: 5|
|`parameter.name`|String|64 Zeichen|✔|Der Name des Parameters, wie er im Client angezeigt wird. Dies ist in der Benutzeranforderung enthalten.|
|`parameter.title`|Zeichenfolge|32 Zeichen|✔|Benutzerfreundlicher Titel für den Parameter.|
|`parameter.description`|Zeichenfolge|128 Zeichen||Benutzerfreundliche Zeichenfolge, die den Zweck dieses Parameters beschreibt.|
|`parameter.inputType`|Zeichenfolge|128 Zeichen||Definiert den Typ des Steuerelements, das in einem Aufgabenmodul für `fetchTask: true`angezeigt wird. Einer von `text`, `textarea`, `number`, `date`, `time`, `toggle`. `choiceset`|
|`parameter.choices`|Array von Objekten|10||Die Auswahloptionen für die `choiceset`. Verwenden Sie nur, wenn `parameter.inputType` `choiceset`ist .|
|`parameter.choices.title`|Zeichenfolge|128||Titel der Auswahl.|
|`parameter.choices.value`|Zeichenfolge|512||Value of the choice.|

## <a name="permissions"></a>Berechtigungen

Optional:

Ein Array, das `string` angibt, welche Berechtigungen die App anfordert, wodurch Endbenutzer wissen, wie die Erweiterung ausgeführt wird. Die folgenden Optionen sind nicht exklusiv:

* `identity` &emsp; Erfordert Benutzeridentitätsinformationen.
* `messageTeamMembers`&emsp; Erfordert die Berechtigung, direkte Nachrichten an Teammitglieder zu senden.

Wenn Sie diese Berechtigungen beim Aktualisieren Ihrer App ändern, wiederholen Die Benutzer den Zustimmungsprozess bei der ersten Ausführung der aktualisierten App.

## <a name="devicepermissions"></a>devicePermissions

**Optional** Zeichenfolgenarray

Gibt die systemeigenen Features auf dem Gerät eines Benutzers an, auf die Ihre App möglicherweise Zugriff anfordern kann. Mögliche Optionen sind:

* `geolocation`
* `media`
* `notifications`
* `midi`
* `openExternal`

## <a name="validdomains"></a>validDomains

**Optional**, mit Ausnahme **von "Erforderlich"** , sofern angegeben

Eine Liste gültiger Domänen, von denen die App erwartet, dass inhalte geladen werden. Domäneneinträge können beispielsweise `*.example.com`Platzhalter enthalten. Dies entspricht genau einem Segment der Domäne. wenn Sie übereinstimmen `a.b.example.com` müssen, verwenden Sie `*.*.example.com`dann . Wenn Ihre Registerkartenkonfiguration oder Inhalts-UI zu einer anderen Domäne außer derjenigen navigieren muss, die für die Registerkartenkonfiguration verwendet wird, muss diese Domäne hier angegeben werden.

Es ist **jedoch nicht** erforderlich, die Domänen von Identitätsanbietern, die Sie unterstützen möchten, in Ihre App aufzunehmen. Um sich beispielsweise mit einer Google-ID zu authentifizieren, ist es erforderlich, zu accounts.google.com umzuleiten, aber Sie sollten accounts.google.com nicht in `validDomains[]`einschließen.

> [!IMPORTANT]
> Fügen Sie keine Domänen hinzu, die sich außerhalb Ihres Steuerelements befinden, weder direkt noch über Platzhalter. Ist z. B. `yourapp.onmicrosoft.com` gültig, aber `*.onmicrosoft.com` ungültig.

Das Objekt ist ein Array, wobei alle Elemente vom Typ `string` sind.

## <a name="webapplicationinfo"></a>webApplicationInfo

Optional:

Geben Sie Ihre Microsoft Azure Active Directory (Azure AD) App-ID und Graph Informationen an, damit sich Benutzer nahtlos bei Ihrer Auzre AD-App anmelden können.

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`id`|Zeichenfolge|36 Zeichen|✔|Microsoft Azure Active Directory (Azure AD)-Anwendungs-ID der App. Diese ID muss eine GUID sein.|
|`resource`|Zeichenfolge|2048 Zeichen|✔|Ressourcen-URL der App zum Abrufen des Authentifizierungstokens für SSO.|
|`applicationPermissions`|Array|Maximal 100 Elemente|✔|Ressourcenberechtigungen für die Anwendung.|

## <a name="configurableproperties"></a>configurableProperties

**Optional** – Array

Der `configurableProperties`-Block definiert die App-Eigenschaften, die Microsoft Teams-Administratoren anpassen können. Weitere Informationen finden Sie unter [Aktivieren der App-Anpassung](~/concepts/design/enable-app-customization.md).

> [!NOTE]
> Es muss mindestens eine Eigenschaft definiert werden. Sie können in diesem Block maximal neun Eigenschaften definieren.

Sie können eine der folgenden Eigenschaften definieren:

* `name`: Der Anzeigename der App.
* `shortDescription`: Die Kurzbeschreibung der App.
* `longDescription`: Die detaillierte Beschreibung der App.
* `smallImageUrl`: Das Kontursymbol der App.
* `largeImageUrl`: Das Farbsymbol der App.
* `accentColor`: Die Farbe, die in Verbindung mit und als Hintergrund für Ihre Gliederungssymbole verwendet werden soll.
* `developerUrl`: Die HTTPS-URL der Website des Entwicklers.
* `privacyUrl`: Die HTTPS-URL der Datenschutzerklärung des Entwicklers.
* `termsOfUseUrl`: Die HTTPS-URL der Nutzungsbedingungen des Entwicklers.

## <a name="defaultinstallscope"></a>defaultInstallScope

**Optional** – Zeichenfolge

Gibt den standardmäßig für diese App definierten Installationsbereich an. Der definierte Bereich ist die Option, die auf der Schaltfläche angezeigt wird, wenn ein Benutzer versucht, die App hinzuzufügen. Mögliche Optionen sind:

* `personal`
* `team`
* `groupchat`
* `meetings`

## <a name="defaultgroupcapability"></a>defaultGroupCapability

**Optional** – Objekt

Wenn ein Gruppeninstallationsbereich ausgewählt ist, wird die Standardfunktion definiert, wenn der Benutzer die App installiert. Die Optionen sind:

* `team`
* `groupchat`
* `meetings`

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`team`|string|||Wenn der ausgewählte Installationsbereich `team` ist, gibt dieses Feld die verfügbare Standardfunktion an. Optionen: `tab`, `bot`, oder `connector`.|
|`groupchat`|string|||Wenn der ausgewählte Installationsbereich `groupchat` ist, gibt dieses Feld die verfügbare Standardfunktion an. Optionen: `tab`, `bot`, oder `connector`.|
|`meetings`|string|||Wenn der ausgewählte Installationsbereich `meetings` ist, gibt dieses Feld die verfügbare Standardfunktion an. Optionen: `tab`, `bot`, oder `connector`.|

## <a name="subscriptionoffer"></a>subscriptionOffer

**Optional** – Objekt

Gibt das Ihrer App zugeordnete SaaS-Angebot an.

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`offerId`| string | 2048 Zeichen | ✔ | Ein eindeutiger Bezeichner, der Ihre Publisher-ID und Angebots-ID enthält. Diese finden Sie im [Partner Center](https://partner.microsoft.com/dashboard). Sie müssen die Zeichenfolge als `publisherId.offerId` formatieren.|

## <a name="meetingextensiondefinition"></a>meetingExtensionDefinition

**Optional** – Objekt

Geben Sie die Definition der Besprechungserweiterung an. Weitere Informationen finden Sie unter [benutzerdefinierten Szenen im Zusammen-Modus in Microsoft Teams](../../apps-in-teams-meetings/teams-together-mode.md).

|Name| Typ| Maximale Größe | Erforderlich | Beschreibung|
|---|---|---|---|---|
|`scenes`|Array von Objekten| 5 Elemente||Unterstützte Besprechungsszenen.|

### <a name="meetingextensiondefinitionscenes"></a>meetingExtensionDefinition.scenes

|Name| Typ|Maximale Größe|Erforderlich |Beschreibung|
|---|---|---|---|---|
|`id`|||✔| Der eindeutige Bezeichner für die Szene. Diese ID muss eine GUID sein. |
|`name`| string | 128 Zeichen |✔| Der Name der Szene. |
|`file`|||✔| Der relative Dateipfad zur JSON-Metadatendatei der Szenen. |
|`preview`|||✔| Der relative Dateipfad zum PNG-Vorschausymbol der Szenen. |
|`maxAudience`| ganze Zahl | 50  |✔| Die maximale Anzahl von Zielgruppen, die in der Szene unterstützt werden. |
|`seatsReservedForOrganizersOrPresenters`| ganze Zahl | 50 |✔| Die Anzahl der Plätze, die für Organisatoren oder Moderatoren reserviert sind.|

## <a name="authorization"></a>Autorisierung

**Optional** – Objekt

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
|`type`|string||✔| Der Typ der ressourcenspezifischen Berechtigung. Optionen: `Application` und `Delegated`.|
|`name`|string|128 Zeichen|✔|Der Name der ressourcenspezifischen Berechtigung. Weitere Informationen finden Sie unter [Ressourcenspezifische Anwendungsberechtigungen](#resource-specific-application-permissions) und [Ressourcenspezifische delegierte Berechtigungen](#resource-specific-delegated-permissions)|

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

* **Ressourcenspezifische delegierte Berechtigungen für Chats oder Besprechungen**

    |**Name**|**Beschreibung**|
    |---|---|
    |`InAppPurchase.Allow.Chat`|Ermöglicht es der App, den Nutzern in diesem Chat und allen damit verbundenen Treffen Marktplatzangebote zu zeigen und ihre Einkäufe innerhalb der App im Namen des angemeldeten Nutzers abzuschließen.|
    |`MeetingStage.Write.Chat`|Ermöglicht es der App, in Meetings, die mit diesem Chat verbunden sind, im Namen des angemeldeten Benutzers Inhalte auf der Meeting-Bühne zu zeigen.|
    |`OnlineMeetingParticipant.Read.Chat`|Ermöglicht es der App, im Namen des angemeldeten Benutzers die Teilnehmerinformationen, einschließlich Name, Rolle, ID, Beitritts- und Austrittszeiten, der mit diesem Chat verbundenen Besprechung zu lesen.|
    |`OnlineMeetingParticipant.ToggleIncomingAudio.Chat`|Ermöglicht der App, eingehende Audiodaten für Teilnehmer an Meetings, die mit diesem Chat verknüpft sind, im Namen des angemeldeten Benutzers umzuschalten.|

* **Ressourcespezifische delegierte Berechtigungen für Benutzer**

    |**Name**|**Beschreibung**|
    |---|---|
    |`InAppPurchase.Allow.User`|Ermöglicht es der App, dem Benutzer Angebote auf dem Marktplatz zu zeigen und die Einkäufe des Benutzers innerhalb der App im Namen des angemeldeten Benutzers abzuschließen.|

## <a name="see-also"></a>Siehe auch

* [Grundlegendes zur Struktur von Microsoft Teams-Apps](~/concepts/design/app-structure.md)
* [Aktivieren der App-Anpassung](~/concepts/design/enable-app-customization.md)
* [Lokalisieren IhrerApp](~/concepts/build-and-test/apps-localization.md)
* [Integrieren von Medienfunktionen](~/concepts/device-capabilities/mobile-camera-image-permissions.md)
