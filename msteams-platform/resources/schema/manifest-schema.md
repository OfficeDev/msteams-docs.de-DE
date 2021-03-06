---
title: Manifestschemareferenz
description: Beschreibt das Manifestschema für Microsoft Teams
ms.topic: reference
ms.author: lajanuar
keywords: Teams-Manifestschema
ms.openlocfilehash: 291d748d546dec16fa4bf748318b8749b7d0275d
ms.sourcegitcommit: 9cfbc44912980a33d2d7c7c85739aeea6ccb41de
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/05/2021
ms.locfileid: "50479855"
---
# <a name="reference-manifest-schema-for-microsoft-teams"></a><span data-ttu-id="55c88-104">Referenz: Manifestschema für Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="55c88-104">Reference: Manifest schema for Microsoft Teams</span></span>

<span data-ttu-id="55c88-105">Das Microsoft Teams-Manifest beschreibt, wie die App in das Microsoft Teams-Produkt integriert wird.</span><span class="sxs-lookup"><span data-stu-id="55c88-105">The Teams manifest describes how the app integrates into the Microsoft Teams product.</span></span> <span data-ttu-id="55c88-106">Ihr Manifest muss dem schema entsprechen, das unter gehostet [`https://developer.microsoft.com/json-schemas/teams/v1.8/MicrosoftTeams.schema.json`]( https://developer.microsoft.com/json-schemas/teams/v1.8/MicrosoftTeams.schema.json) wird.</span><span class="sxs-lookup"><span data-stu-id="55c88-106">Your manifest must conform to the schema hosted at [`https://developer.microsoft.com/json-schemas/teams/v1.8/MicrosoftTeams.schema.json`]( https://developer.microsoft.com/json-schemas/teams/v1.8/MicrosoftTeams.schema.json).</span></span> <span data-ttu-id="55c88-107">Frühere Versionen 1.0-1.4 werden ebenfalls unterstützt (unter Verwendung von "v1.x" in der URL).</span><span class="sxs-lookup"><span data-stu-id="55c88-107">Previous versions 1.0-1.4 are also supported (using "v1.x" in the URL).</span></span>

<span data-ttu-id="55c88-108">Das folgende Schemabeispiel zeigt alle Erweiterbarkeitsoptionen.</span><span class="sxs-lookup"><span data-stu-id="55c88-108">The following schema sample shows all extensibility options.</span></span>

## <a name="sample-full-manifest"></a><span data-ttu-id="55c88-109">Beispiel für vollständiges Manifest</span><span class="sxs-lookup"><span data-stu-id="55c88-109">Sample full manifest</span></span>

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
  },
  "defaultInstallScope": {
     "type": "string",
     "enum": [
        "personal",
        "team",
        "groupchat",
        "meetings"
      ],
      "description": "The install scope is defined for this app by default. It is the option displayed on the button when a user tries to add the app."
    },
  "defaultGroupCapability": {
      "type": "object",
      "properties": {
        "team": {
          "type": "string",
          "enum": [
            "tab",
            "bot",
            "connector"
          ],
          "description": "When the selected install scope is Team, this field specifies the default capability available."
    },
    "groupchat": {
      "type": "string",
      "enum": [
            "tab",
            "bot",
            "connector"
      ],
      "description": "When the selected install scope is Group Chat, this field specifies the default capability available."
    },
    "meetings": {
      "type": "string",
      "enum": [
            "tab",
            "bot",
            "connector"
      ],
      "description": "When the selected install scope is Meetings, this field specifies the default capability available."
      }
    },
    "description": "When a group install scope is selected, this defines the default capability when the user installs the app.",
    "additionalProperties": false

}
```

<span data-ttu-id="55c88-110">Das Schema definiert die folgenden Eigenschaften:</span><span class="sxs-lookup"><span data-stu-id="55c88-110">The schema defines the following properties:</span></span>

## <a name="schema"></a><span data-ttu-id="55c88-111">$schema</span><span class="sxs-lookup"><span data-stu-id="55c88-111">$schema</span></span>

<span data-ttu-id="55c88-112">Optional, aber empfohlen – Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="55c88-112">Optional, but recommended — string</span></span>

<span data-ttu-id="55c88-113">Die https://-URL, die auf das JSON-Schema für das Manifest verweist.</span><span class="sxs-lookup"><span data-stu-id="55c88-113">The https:// URL referencing the JSON Schema for the manifest.</span></span>

## <a name="manifestversion"></a><span data-ttu-id="55c88-114">manifestVersion</span><span class="sxs-lookup"><span data-stu-id="55c88-114">manifestVersion</span></span>

<span data-ttu-id="55c88-115">**Erforderlich** – Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="55c88-115">**Required** — string</span></span>

<span data-ttu-id="55c88-116">Die Version des Manifestschemas, das dieses Manifest verwendet.</span><span class="sxs-lookup"><span data-stu-id="55c88-116">The version of manifest schema this manifest is using.</span></span> <span data-ttu-id="55c88-117">Er muss 1,7 sein.</span><span class="sxs-lookup"><span data-stu-id="55c88-117">It must be 1.7.</span></span>

## <a name="version"></a><span data-ttu-id="55c88-118">Version</span><span class="sxs-lookup"><span data-stu-id="55c88-118">version</span></span>

<span data-ttu-id="55c88-119">**Erforderlich** – Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="55c88-119">**Required** — string</span></span>

<span data-ttu-id="55c88-120">Die Version einer bestimmten App.</span><span class="sxs-lookup"><span data-stu-id="55c88-120">The version of a specific app.</span></span> <span data-ttu-id="55c88-121">Wenn Sie etwas in Ihrem Manifest aktualisieren, muss auch die Version erhöht werden.</span><span class="sxs-lookup"><span data-stu-id="55c88-121">If you update something in your manifest, the version must be incremented too.</span></span> <span data-ttu-id="55c88-122">Auf diese Weise wird das vorhandene Manifest überschrieben, wenn das neue Manifest installiert wird, und der Benutzer erhält die neue Funktionalität.</span><span class="sxs-lookup"><span data-stu-id="55c88-122">This way, when the new manifest is installed, it overwrites the existing one and the user receives the new functionality.</span></span> <span data-ttu-id="55c88-123">Wenn diese App an den Store übermittelt wurde, muss das neue Manifest erneut übermittelt und erneut überprüft werden.</span><span class="sxs-lookup"><span data-stu-id="55c88-123">If this app was submitted to the store, the new manifest must be re-submitted and re-validated.</span></span> <span data-ttu-id="55c88-124">Die App-Benutzer erhalten das neue aktualisierte Manifest automatisch innerhalb weniger Stunden nach der Genehmigung des Manifests.</span><span class="sxs-lookup"><span data-stu-id="55c88-124">The app users receive the new updated manifest automatically within few hours after the manifest is approved.</span></span>

<span data-ttu-id="55c88-125">Wenn sich die App-Anforderungen für Berechtigungen ändern, werden die Benutzer aufgefordert, ein Upgrade zu starten und der App erneut zu zustimmen.</span><span class="sxs-lookup"><span data-stu-id="55c88-125">If the app requests for permissions change, the users are prompted to upgrade and re-consent to the app.</span></span>

<span data-ttu-id="55c88-126">Diese Versionszeichenfolge muss dem [semver-Standard](http://semver.org/) (MAJOR. MINOR. PATCH).</span><span class="sxs-lookup"><span data-stu-id="55c88-126">This version string must follow the [semver](http://semver.org/) standard (MAJOR.MINOR.PATCH).</span></span>

## <a name="id"></a><span data-ttu-id="55c88-127">id</span><span class="sxs-lookup"><span data-stu-id="55c88-127">id</span></span>

<span data-ttu-id="55c88-128">**Erforderlich** – Microsoft-App-ID</span><span class="sxs-lookup"><span data-stu-id="55c88-128">**Required** — Microsoft app ID</span></span>

<span data-ttu-id="55c88-129">Die ID ist ein eindeutiger von Microsoft generierter Bezeichner für die App.</span><span class="sxs-lookup"><span data-stu-id="55c88-129">The ID is a unique Microsoft-generated identifier for the app.</span></span> <span data-ttu-id="55c88-130">Sie haben eine ID, wenn Ihr Bot über das Microsoft Bot Framework registriert ist oder sich die Web-App Ihrer Registerkarte bereits bei Microsoft angemeldet hat.</span><span class="sxs-lookup"><span data-stu-id="55c88-130">You have an ID if your bot is registered through the Microsoft Bot Framework or your tab's web app already signs in with Microsoft.</span></span> <span data-ttu-id="55c88-131">Sie müssen hier die ID eingeben.</span><span class="sxs-lookup"><span data-stu-id="55c88-131">You must enter the ID here.</span></span> <span data-ttu-id="55c88-132">Andernfalls müssen Sie eine neue ID im Microsoft Application Registration Portal ( Meine Anwendungen )[generieren.](https://apps.dev.microsoft.com)</span><span class="sxs-lookup"><span data-stu-id="55c88-132">Otherwise, you must generate a new ID at the Microsoft Application Registration Portal ([My Applications](https://apps.dev.microsoft.com)).</span></span> <span data-ttu-id="55c88-133">Verwenden Sie dieselbe ID, wenn Sie einen Bot hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="55c88-133">Use the same ID if you add a bot.</span></span>

> [!NOTE]
> <span data-ttu-id="55c88-134">Wenn Sie ein Update an Ihre vorhandene App in AppSource übermitteln, darf die ID in Ihrem Manifest nicht geändert werden.</span><span class="sxs-lookup"><span data-stu-id="55c88-134">If you are submitting an update to your existing app in AppSource, the ID in your manifest must not be modified.</span></span>

## <a name="developer"></a><span data-ttu-id="55c88-135">developer</span><span class="sxs-lookup"><span data-stu-id="55c88-135">developer</span></span>

<span data-ttu-id="55c88-136">**Erforderlich** – Objekt</span><span class="sxs-lookup"><span data-stu-id="55c88-136">**Required** — object</span></span>

<span data-ttu-id="55c88-137">Gibt Informationen zu Ihrem Unternehmen.</span><span class="sxs-lookup"><span data-stu-id="55c88-137">Gives information about your company.</span></span> <span data-ttu-id="55c88-138">Für apps submitted to AppSource (formerly Office Store), these values must match the information in your AppSource entry.</span><span class="sxs-lookup"><span data-stu-id="55c88-138">For apps submitted to AppSource (formerly Office Store), these values must match the information in your AppSource entry.</span></span> <span data-ttu-id="55c88-139">Weitere Informationen [finden Sie in den Veröffentlichungsrichtlinien.](~/concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md)</span><span class="sxs-lookup"><span data-stu-id="55c88-139">See the [publishing guidelines](~/concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md) for additional information.</span></span>

|<span data-ttu-id="55c88-140">Name</span><span class="sxs-lookup"><span data-stu-id="55c88-140">Name</span></span>| <span data-ttu-id="55c88-141">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="55c88-141">Maximum size</span></span> | <span data-ttu-id="55c88-142">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="55c88-142">Required</span></span> | <span data-ttu-id="55c88-143">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="55c88-143">Description</span></span>|
|---|---|---|---|
|`name`|<span data-ttu-id="55c88-144">32 Zeichen</span><span class="sxs-lookup"><span data-stu-id="55c88-144">32 characters</span></span>|<span data-ttu-id="55c88-145">✔</span><span class="sxs-lookup"><span data-stu-id="55c88-145">✔</span></span>|<span data-ttu-id="55c88-146">Der Anzeigename für den Entwickler.</span><span class="sxs-lookup"><span data-stu-id="55c88-146">The display name for the developer.</span></span>|
|`websiteUrl`|<span data-ttu-id="55c88-147">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="55c88-147">2048 characters</span></span>|<span data-ttu-id="55c88-148">✔</span><span class="sxs-lookup"><span data-stu-id="55c88-148">✔</span></span>|<span data-ttu-id="55c88-149">Die https://-URL zur Website des Entwicklers.</span><span class="sxs-lookup"><span data-stu-id="55c88-149">The https:// URL to the developer's website.</span></span> <span data-ttu-id="55c88-150">Dieser Link muss Benutzer zu Ihrer unternehmens- oder produktspezifischen Angebotsseite gelangen.</span><span class="sxs-lookup"><span data-stu-id="55c88-150">This link must take users to your company or product-specific landing page.</span></span>|
|`privacyUrl`|<span data-ttu-id="55c88-151">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="55c88-151">2048 characters</span></span>|<span data-ttu-id="55c88-152">✔</span><span class="sxs-lookup"><span data-stu-id="55c88-152">✔</span></span>|<span data-ttu-id="55c88-153">Die https:// url to the developer's privacy policy.</span><span class="sxs-lookup"><span data-stu-id="55c88-153">The https:// URL to the developer's privacy policy.</span></span>|
|`termsOfUseUrl`|<span data-ttu-id="55c88-154">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="55c88-154">2048 characters</span></span>|<span data-ttu-id="55c88-155">✔</span><span class="sxs-lookup"><span data-stu-id="55c88-155">✔</span></span>|<span data-ttu-id="55c88-156">Die https:// URL zu den Nutzungsbedingungen des Entwicklers.</span><span class="sxs-lookup"><span data-stu-id="55c88-156">The https:// URL to the developer's terms of use.</span></span>|
|`mpnId`|<span data-ttu-id="55c88-157">10 Zeichen</span><span class="sxs-lookup"><span data-stu-id="55c88-157">10 characters</span></span>| |<span data-ttu-id="55c88-158">**Optional** Die Microsoft Partner Network ID, die die Partnerorganisation identifiziert, die die App erstellt.</span><span class="sxs-lookup"><span data-stu-id="55c88-158">**Optional** The Microsoft Partner Network ID that identifies the partner organization building the app.</span></span>|

## <a name="name"></a><span data-ttu-id="55c88-159">name</span><span class="sxs-lookup"><span data-stu-id="55c88-159">name</span></span>

<span data-ttu-id="55c88-160">**Erforderlich** – Objekt</span><span class="sxs-lookup"><span data-stu-id="55c88-160">**Required** — object</span></span>

<span data-ttu-id="55c88-161">Der Name Ihrer App-Erfahrung, der Benutzern in der Teams-Erfahrung angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="55c88-161">The name of your app experience, displayed to users in the Teams experience.</span></span> <span data-ttu-id="55c88-162">Für apps submitted to AppSource, these values must match the information in your AppSource entry.</span><span class="sxs-lookup"><span data-stu-id="55c88-162">For apps submitted to AppSource, these values must match the information in your AppSource entry.</span></span> <span data-ttu-id="55c88-163">Die Werte von `short` und `full` müssen unterschiedlich sein.</span><span class="sxs-lookup"><span data-stu-id="55c88-163">The values of `short` and `full` must be different.</span></span>

|<span data-ttu-id="55c88-164">Name</span><span class="sxs-lookup"><span data-stu-id="55c88-164">Name</span></span>| <span data-ttu-id="55c88-165">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="55c88-165">Maximum size</span></span> | <span data-ttu-id="55c88-166">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="55c88-166">Required</span></span> | <span data-ttu-id="55c88-167">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="55c88-167">Description</span></span>|
|---|---|---|---|
|`short`|<span data-ttu-id="55c88-168">30 Zeichen</span><span class="sxs-lookup"><span data-stu-id="55c88-168">30 characters</span></span>|<span data-ttu-id="55c88-169">✔</span><span class="sxs-lookup"><span data-stu-id="55c88-169">✔</span></span>|<span data-ttu-id="55c88-170">Der kurze Anzeigename für die App.</span><span class="sxs-lookup"><span data-stu-id="55c88-170">The short display name for the app.</span></span>|
|`full`|<span data-ttu-id="55c88-171">100 Zeichen</span><span class="sxs-lookup"><span data-stu-id="55c88-171">100 characters</span></span>||<span data-ttu-id="55c88-172">Der vollständige Name der App, der verwendet wird, wenn der vollständige Name der App 30 Zeichen überschreitet.</span><span class="sxs-lookup"><span data-stu-id="55c88-172">The full name of the app, used if the full app name exceeds 30 characters.</span></span>|

## <a name="description"></a><span data-ttu-id="55c88-173">description</span><span class="sxs-lookup"><span data-stu-id="55c88-173">description</span></span>

<span data-ttu-id="55c88-174">**Erforderlich** – Objekt</span><span class="sxs-lookup"><span data-stu-id="55c88-174">**Required** — object</span></span>

<span data-ttu-id="55c88-175">Beschreibt Ihre App für Benutzer.</span><span class="sxs-lookup"><span data-stu-id="55c88-175">Describes your app to users.</span></span> <span data-ttu-id="55c88-176">Für apps submitted to AppSource, these values must match the information in your AppSource entry.</span><span class="sxs-lookup"><span data-stu-id="55c88-176">For apps submitted to AppSource, these values must match the information in your AppSource entry.</span></span>

<span data-ttu-id="55c88-177">Stellen Sie sicher, dass Ihre Beschreibung Ihre Erfahrung genau beschreibt und Informationen enthält, mit deren Hilfe potenzielle Kunden besser verstehen können, was Ihre Erfahrung bedeutet.</span><span class="sxs-lookup"><span data-stu-id="55c88-177">Ensure that your description accurately describes your experience and provides information to help potential customers understand what your experience does.</span></span> <span data-ttu-id="55c88-178">Sie müssen in der vollständigen Beschreibung notieren, ob ein externes Konto für die Verwendung erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="55c88-178">You must note in the full description, if an external account is required for use.</span></span> <span data-ttu-id="55c88-179">Die Werte von `short` und `full` müssen unterschiedlich sein.</span><span class="sxs-lookup"><span data-stu-id="55c88-179">The values of `short` and `full` must be different.</span></span> <span data-ttu-id="55c88-180">Ihre kurze Beschreibung darf nicht innerhalb der langen Beschreibung wiederholt werden und darf keinen anderen App-Namen enthalten.</span><span class="sxs-lookup"><span data-stu-id="55c88-180">Your short description must not be repeated within the long description and must not include any other app name.</span></span>

|<span data-ttu-id="55c88-181">Name</span><span class="sxs-lookup"><span data-stu-id="55c88-181">Name</span></span>| <span data-ttu-id="55c88-182">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="55c88-182">Maximum size</span></span> | <span data-ttu-id="55c88-183">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="55c88-183">Required</span></span> | <span data-ttu-id="55c88-184">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="55c88-184">Description</span></span>|
|---|---|---|---|
|`short`|<span data-ttu-id="55c88-185">80 Zeichen</span><span class="sxs-lookup"><span data-stu-id="55c88-185">80 characters</span></span>|<span data-ttu-id="55c88-186">✔</span><span class="sxs-lookup"><span data-stu-id="55c88-186">✔</span></span>|<span data-ttu-id="55c88-187">Eine kurze Beschreibung Ihrer App-Erfahrung, die bei begrenztem Speicherplatz verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="55c88-187">A short description of your app experience, used when space is limited.</span></span>|
|`full`|<span data-ttu-id="55c88-188">4000 Zeichen</span><span class="sxs-lookup"><span data-stu-id="55c88-188">4000 characters</span></span>|<span data-ttu-id="55c88-189">✔</span><span class="sxs-lookup"><span data-stu-id="55c88-189">✔</span></span>|<span data-ttu-id="55c88-190">Die vollständige Beschreibung Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="55c88-190">The full description of your app.</span></span>|

## <a name="packagename"></a><span data-ttu-id="55c88-191">packageName</span><span class="sxs-lookup"><span data-stu-id="55c88-191">packageName</span></span>

<span data-ttu-id="55c88-192">**Optional –** Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="55c88-192">**Optional** — string</span></span>

<span data-ttu-id="55c88-193">Ein eindeutiger Bezeichner für die App in umgekehrter Domänen-Notation; z. B. com.example.myapp.</span><span class="sxs-lookup"><span data-stu-id="55c88-193">A unique identifier for the app in reverse domain notation; for example, com.example.myapp.</span></span> <span data-ttu-id="55c88-194">Maximale Länge: 64 Zeichen.</span><span class="sxs-lookup"><span data-stu-id="55c88-194">Maximum length: 64 characters.</span></span>

## <a name="localizationinfo"></a><span data-ttu-id="55c88-195">localizationInfo</span><span class="sxs-lookup"><span data-stu-id="55c88-195">localizationInfo</span></span>

<span data-ttu-id="55c88-196">**Optional** – -Objekt</span><span class="sxs-lookup"><span data-stu-id="55c88-196">**Optional** — object</span></span>

<span data-ttu-id="55c88-197">Ermöglicht die Angabe einer Standardsprache sowie Zeiger auf zusätzliche Sprachdateien.</span><span class="sxs-lookup"><span data-stu-id="55c88-197">Allows the specification of a default language, as well as pointers to additional language files.</span></span> <span data-ttu-id="55c88-198">Weitere [Informationen finden Sie unter Lokalisierung](~/concepts/build-and-test/apps-localization.md).</span><span class="sxs-lookup"><span data-stu-id="55c88-198">See [localization](~/concepts/build-and-test/apps-localization.md).</span></span>

|<span data-ttu-id="55c88-199">Name</span><span class="sxs-lookup"><span data-stu-id="55c88-199">Name</span></span>| <span data-ttu-id="55c88-200">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="55c88-200">Maximum size</span></span> | <span data-ttu-id="55c88-201">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="55c88-201">Required</span></span> | <span data-ttu-id="55c88-202">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="55c88-202">Description</span></span>|
|---|---|---|---|
|`defaultLanguageTag`||<span data-ttu-id="55c88-203">✔</span><span class="sxs-lookup"><span data-stu-id="55c88-203">✔</span></span>|<span data-ttu-id="55c88-204">Das Sprachtag der Zeichenfolgen in dieser Manifestdatei auf oberster Ebene.</span><span class="sxs-lookup"><span data-stu-id="55c88-204">The language tag of the strings in this top level manifest file.</span></span>|

### <a name="localizationinfoadditionallanguages"></a><span data-ttu-id="55c88-205">localizationInfo.additionalLanguages</span><span class="sxs-lookup"><span data-stu-id="55c88-205">localizationInfo.additionalLanguages</span></span>

<span data-ttu-id="55c88-206">Ein Array von Objekten, die zusätzliche Sprachübersetzungen angeben.</span><span class="sxs-lookup"><span data-stu-id="55c88-206">An array of objects specifying additional language translations.</span></span>

|<span data-ttu-id="55c88-207">Name</span><span class="sxs-lookup"><span data-stu-id="55c88-207">Name</span></span>| <span data-ttu-id="55c88-208">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="55c88-208">Maximum size</span></span> | <span data-ttu-id="55c88-209">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="55c88-209">Required</span></span> | <span data-ttu-id="55c88-210">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="55c88-210">Description</span></span>|
|---|---|---|---|
|`languageTag`||<span data-ttu-id="55c88-211">✔</span><span class="sxs-lookup"><span data-stu-id="55c88-211">✔</span></span>|<span data-ttu-id="55c88-212">Das Sprachtag der Zeichenfolgen in der bereitgestellten Datei.</span><span class="sxs-lookup"><span data-stu-id="55c88-212">The language tag of the strings in the provided file.</span></span>|
|`file`||<span data-ttu-id="55c88-213">✔</span><span class="sxs-lookup"><span data-stu-id="55c88-213">✔</span></span>|<span data-ttu-id="55c88-214">Ein relativer Dateipfad zu einer .json-Datei, die die übersetzten Zeichenfolgen enthält.</span><span class="sxs-lookup"><span data-stu-id="55c88-214">A relative file path to a the .json file containing the translated strings.</span></span>|

## <a name="icons"></a><span data-ttu-id="55c88-215">Symbole</span><span class="sxs-lookup"><span data-stu-id="55c88-215">icons</span></span>

<span data-ttu-id="55c88-216">**Erforderlich** – Objekt</span><span class="sxs-lookup"><span data-stu-id="55c88-216">**Required** — object</span></span>

<span data-ttu-id="55c88-217">Symbole, die in der Teams-App verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="55c88-217">Icons used within the Teams app.</span></span> <span data-ttu-id="55c88-218">Die Symboldateien müssen als Teil des Uploadpakets enthalten sein.</span><span class="sxs-lookup"><span data-stu-id="55c88-218">The icon files must be included as part of the upload package.</span></span> <span data-ttu-id="55c88-219">Weitere Informationen finden Sie unter [Symbole.](../../concepts/build-and-test/apps-package.md#app-icons)</span><span class="sxs-lookup"><span data-stu-id="55c88-219">See [Icons](../../concepts/build-and-test/apps-package.md#app-icons) for more information.</span></span>

|<span data-ttu-id="55c88-220">Name</span><span class="sxs-lookup"><span data-stu-id="55c88-220">Name</span></span>| <span data-ttu-id="55c88-221">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="55c88-221">Maximum size</span></span> | <span data-ttu-id="55c88-222">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="55c88-222">Required</span></span> | <span data-ttu-id="55c88-223">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="55c88-223">Description</span></span>|
|---|---|---|---|
|`outline`|<span data-ttu-id="55c88-224">32 x 32 Pixel</span><span class="sxs-lookup"><span data-stu-id="55c88-224">32 x 32 pixels</span></span>|<span data-ttu-id="55c88-225">✔</span><span class="sxs-lookup"><span data-stu-id="55c88-225">✔</span></span>|<span data-ttu-id="55c88-226">Ein relativer Dateipfad zu einem transparenten 32 x 32 PNG-Gliederungssymbol.</span><span class="sxs-lookup"><span data-stu-id="55c88-226">A relative file path to a transparent 32x32 PNG outline icon.</span></span>|
|`color`|<span data-ttu-id="55c88-227">192 x 192 Pixel</span><span class="sxs-lookup"><span data-stu-id="55c88-227">192 x 192 pixels</span></span>|<span data-ttu-id="55c88-228">✔</span><span class="sxs-lookup"><span data-stu-id="55c88-228">✔</span></span>|<span data-ttu-id="55c88-229">Ein relativer Dateipfad zu einem vollfarbigen 192 x 192-PNG-Symbol.</span><span class="sxs-lookup"><span data-stu-id="55c88-229">A relative file path to a full color 192x192 PNG icon.</span></span>|

## <a name="accentcolor"></a><span data-ttu-id="55c88-230">accentColor</span><span class="sxs-lookup"><span data-stu-id="55c88-230">accentColor</span></span>

<span data-ttu-id="55c88-231">**Optional** – HTML-Hex-Farbcode</span><span class="sxs-lookup"><span data-stu-id="55c88-231">**Optional** — HTML Hex color code</span></span>

<span data-ttu-id="55c88-232">Eine Farbe, die in Verbindung mit und als Hintergrund für Ihre Gliederungssymbole verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="55c88-232">A color to use in conjunction with and as a background for your outline icons.</span></span>

<span data-ttu-id="55c88-233">Der Wert muss ein gültiger #A0 sein, der mit "#" beginnt, z. B. `#4464ee` .</span><span class="sxs-lookup"><span data-stu-id="55c88-233">The value must be a valid HTML color code starting with '#', for example `#4464ee`.</span></span>

## <a name="configurabletabs"></a><span data-ttu-id="55c88-234">configurableTabs</span><span class="sxs-lookup"><span data-stu-id="55c88-234">configurableTabs</span></span>

<span data-ttu-id="55c88-235">**Optional** – Array</span><span class="sxs-lookup"><span data-stu-id="55c88-235">**Optional** — array</span></span>

<span data-ttu-id="55c88-236">Wird verwendet, wenn Ihre App über eine Registerkartenerfahrung im Teamkanal verfügt, die eine zusätzliche Konfiguration erfordert, bevor sie hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="55c88-236">Used when your app experience has a team channel tab experience that requires extra configuration before it is added.</span></span> <span data-ttu-id="55c88-237">Konfigurierbare Registerkarten werden nur im Teambereich (nicht persönlich) unterstützt, und derzeit wird nur eine **Registerkarte** pro App unterstützt.</span><span class="sxs-lookup"><span data-stu-id="55c88-237">Configurable tabs are supported only in the teams scope (not personal), and currently only **one** tab per app is supported.</span></span>

|<span data-ttu-id="55c88-238">Name</span><span class="sxs-lookup"><span data-stu-id="55c88-238">Name</span></span>| <span data-ttu-id="55c88-239">Typ</span><span class="sxs-lookup"><span data-stu-id="55c88-239">Type</span></span>| <span data-ttu-id="55c88-240">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="55c88-240">Maximum size</span></span> | <span data-ttu-id="55c88-241">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="55c88-241">Required</span></span> | <span data-ttu-id="55c88-242">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="55c88-242">Description</span></span>|
|---|---|---|---|---|
|`configurationUrl`|<span data-ttu-id="55c88-243">string</span><span class="sxs-lookup"><span data-stu-id="55c88-243">string</span></span>|<span data-ttu-id="55c88-244">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="55c88-244">2048 characters</span></span>|<span data-ttu-id="55c88-245">✔</span><span class="sxs-lookup"><span data-stu-id="55c88-245">✔</span></span>|<span data-ttu-id="55c88-246">Die https:// URL, die beim Konfigurieren der Registerkarte verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="55c88-246">The https:// URL to use when configuring the tab.</span></span>|
|`scopes`|<span data-ttu-id="55c88-247">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="55c88-247">array of enums</span></span>|<span data-ttu-id="55c88-248">1 </span><span class="sxs-lookup"><span data-stu-id="55c88-248">1</span></span>|<span data-ttu-id="55c88-249">✔</span><span class="sxs-lookup"><span data-stu-id="55c88-249">✔</span></span>|<span data-ttu-id="55c88-250">Derzeit unterstützen konfigurierbare Registerkarten nur die `team` Bereiche `groupchat` und.</span><span class="sxs-lookup"><span data-stu-id="55c88-250">Currently, configurable tabs support only the `team` and `groupchat` scopes.</span></span> |
|`canUpdateConfiguration`|<span data-ttu-id="55c88-251">Boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="55c88-251">boolean</span></span>|||<span data-ttu-id="55c88-252">Ein Wert, der angibt, ob eine Instanz der Registerkartenkonfiguration vom Benutzer nach der Erstellung aktualisiert werden kann.</span><span class="sxs-lookup"><span data-stu-id="55c88-252">A value indicating whether an instance of the tab's configuration can be updated by the user after creation.</span></span> <span data-ttu-id="55c88-253">Standard: **true**.</span><span class="sxs-lookup"><span data-stu-id="55c88-253">Default: **true**.</span></span>|
|`context` |<span data-ttu-id="55c88-254">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="55c88-254">array of enums</span></span>|<span data-ttu-id="55c88-255">6 </span><span class="sxs-lookup"><span data-stu-id="55c88-255">6</span></span>||<span data-ttu-id="55c88-256">Der Satz von `contextItem` Bereich, in dem eine Registerkarte unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="55c88-256">The set of `contextItem` scopes where a tab is supported.</span></span> <span data-ttu-id="55c88-257">Standard: **[channelTab, privateChatTab, meetingChatTab, meetingDetailsTab]**.</span><span class="sxs-lookup"><span data-stu-id="55c88-257">Default: **[channelTab, privateChatTab, meetingChatTab, meetingDetailsTab]**.</span></span>|
|`sharePointPreviewImage`|<span data-ttu-id="55c88-258">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="55c88-258">string</span></span>|<span data-ttu-id="55c88-259">2048</span><span class="sxs-lookup"><span data-stu-id="55c88-259">2048</span></span>||<span data-ttu-id="55c88-260">Ein relativer Dateipfad zu einem Registerkartenvorschaubild zur Verwendung in SharePoint.</span><span class="sxs-lookup"><span data-stu-id="55c88-260">A relative file path to a tab preview image for use in SharePoint.</span></span> <span data-ttu-id="55c88-261">Größe 1024 x 768.</span><span class="sxs-lookup"><span data-stu-id="55c88-261">Size 1024x768.</span></span> |
|`supportedSharePointHosts`|<span data-ttu-id="55c88-262">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="55c88-262">array of enums</span></span>|<span data-ttu-id="55c88-263">1 </span><span class="sxs-lookup"><span data-stu-id="55c88-263">1</span></span>||<span data-ttu-id="55c88-264">Definiert, wie Ihre Registerkarte in SharePoint verfügbar gemacht wird.</span><span class="sxs-lookup"><span data-stu-id="55c88-264">Defines how your tab is made available in SharePoint.</span></span> <span data-ttu-id="55c88-265">Optionen sind `sharePointFullPage` und `sharePointWebPart`</span><span class="sxs-lookup"><span data-stu-id="55c88-265">Options are `sharePointFullPage` and `sharePointWebPart`</span></span> |

## <a name="statictabs"></a><span data-ttu-id="55c88-266">staticTabs</span><span class="sxs-lookup"><span data-stu-id="55c88-266">staticTabs</span></span>

<span data-ttu-id="55c88-267">**Optional** – Array</span><span class="sxs-lookup"><span data-stu-id="55c88-267">**Optional** — array</span></span>

<span data-ttu-id="55c88-268">Definiert eine Reihe von Registerkarten, die standardmäßig angeheftet werden können, ohne dass der Benutzer sie manuell hinzufügungen muss.</span><span class="sxs-lookup"><span data-stu-id="55c88-268">Defines a set of tabs that can be "pinned" by default, without the user adding them manually.</span></span> <span data-ttu-id="55c88-269">Statische Registerkarten, die im Bereich deklariert sind, werden immer an die persönliche Be benutzererfahrung `personal` der App angeheftet.</span><span class="sxs-lookup"><span data-stu-id="55c88-269">Static tabs declared in `personal` scope are always pinned to the app's personal experience.</span></span> <span data-ttu-id="55c88-270">Statische Registerkarten, die im Bereich `team` deklariert sind, werden derzeit nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="55c88-270">Static tabs declared in the `team` scope are currently not supported.</span></span>

<span data-ttu-id="55c88-271">Dieses Element ist ein Array (maximal 16 Elemente) mit allen Elementen des Typs `object` .</span><span class="sxs-lookup"><span data-stu-id="55c88-271">This item is an array (maximum of 16 elements) with all elements of the type `object`.</span></span> <span data-ttu-id="55c88-272">Dieser Block ist nur für Lösungen erforderlich, die eine statische Registerkartenlösung bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="55c88-272">This block is required only for solutions that provide a static tab solution.</span></span>

|<span data-ttu-id="55c88-273">Name</span><span class="sxs-lookup"><span data-stu-id="55c88-273">Name</span></span>| <span data-ttu-id="55c88-274">Typ</span><span class="sxs-lookup"><span data-stu-id="55c88-274">Type</span></span>| <span data-ttu-id="55c88-275">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="55c88-275">Maximum size</span></span> | <span data-ttu-id="55c88-276">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="55c88-276">Required</span></span> | <span data-ttu-id="55c88-277">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="55c88-277">Description</span></span>|
|---|---|---|---|---|
|`entityId`|<span data-ttu-id="55c88-278">string</span><span class="sxs-lookup"><span data-stu-id="55c88-278">string</span></span>|<span data-ttu-id="55c88-279">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="55c88-279">64 characters</span></span>|<span data-ttu-id="55c88-280">✔</span><span class="sxs-lookup"><span data-stu-id="55c88-280">✔</span></span>|<span data-ttu-id="55c88-281">Ein eindeutiger Bezeichner für die Entität, die auf der Registerkarte angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="55c88-281">A unique identifier for the entity that the tab displays.</span></span>|
|`name`|<span data-ttu-id="55c88-282">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="55c88-282">string</span></span>|<span data-ttu-id="55c88-283">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="55c88-283">128 characters</span></span>|<span data-ttu-id="55c88-284">✔</span><span class="sxs-lookup"><span data-stu-id="55c88-284">✔</span></span>|<span data-ttu-id="55c88-285">Der Anzeigename der Registerkarte in der Kanalschnittstelle.</span><span class="sxs-lookup"><span data-stu-id="55c88-285">The display name of the tab in the channel interface.</span></span>|
|`contentUrl`|<span data-ttu-id="55c88-286">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="55c88-286">string</span></span>||<span data-ttu-id="55c88-287">✔</span><span class="sxs-lookup"><span data-stu-id="55c88-287">✔</span></span>|<span data-ttu-id="55c88-288">Die https://-URL, die auf die Entitätsbenutzeroberfläche verweist, die im Teams-Canvas angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="55c88-288">The https:// URL that points to the entity UI to be displayed in the Teams canvas.</span></span>|
|`websiteUrl`|<span data-ttu-id="55c88-289">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="55c88-289">string</span></span>|||<span data-ttu-id="55c88-290">Die https:// URL, auf die verweisen soll, wenn sich ein Benutzer für die Anzeige in einem Browser entscheidet.</span><span class="sxs-lookup"><span data-stu-id="55c88-290">The https:// URL to point to if a user opts to view in a browser.</span></span>|
|`searchUrl`|<span data-ttu-id="55c88-291">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="55c88-291">string</span></span>|||<span data-ttu-id="55c88-292">Die https:// URL, auf die für die Suchabfragen eines Benutzers verweisen soll.</span><span class="sxs-lookup"><span data-stu-id="55c88-292">The https:// URL to point to for a user's search queries.</span></span>|
|`scopes`|<span data-ttu-id="55c88-293">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="55c88-293">array of enums</span></span>|<span data-ttu-id="55c88-294">1 </span><span class="sxs-lookup"><span data-stu-id="55c88-294">1</span></span>|<span data-ttu-id="55c88-295">✔</span><span class="sxs-lookup"><span data-stu-id="55c88-295">✔</span></span>|<span data-ttu-id="55c88-296">Derzeit unterstützen statische Registerkarten nur den Bereich, d. h., er kann nur als Teil der `personal` persönlichen Erfahrung bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="55c88-296">Currently, static tabs support only the `personal` scope, which means it can be provisioned only as part of the personal experience.</span></span>|
|`context` | <span data-ttu-id="55c88-297">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="55c88-297">array of enums</span></span>| <span data-ttu-id="55c88-298">2 </span><span class="sxs-lookup"><span data-stu-id="55c88-298">2</span></span>|| <span data-ttu-id="55c88-299">Der Satz von `contextItem` Bereich, in dem eine Registerkarte unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="55c88-299">The set of `contextItem` scopes where a tab is supported.</span></span>|

> [!NOTE]
> <span data-ttu-id="55c88-300">Wenn Für Ihre Registerkarten kontextabhängige Informationen zum Anzeigen relevanter Inhalte oder zum Initiieren eines Authentifizierungsflusses erforderlich sind, finden Sie *weitere* Informationen unter [Get context for your Microsoft Teams tab](../../tabs/how-to/access-teams-context.md).</span><span class="sxs-lookup"><span data-stu-id="55c88-300">If your tabs require context-dependent information to display relevant content or for initiating an authentication flow, *see* [Get context for your Microsoft Teams tab](../../tabs/how-to/access-teams-context.md).</span></span>

## <a name="bots"></a><span data-ttu-id="55c88-301">Bots</span><span class="sxs-lookup"><span data-stu-id="55c88-301">bots</span></span>

<span data-ttu-id="55c88-302">**Optional** – Array</span><span class="sxs-lookup"><span data-stu-id="55c88-302">**Optional** — array</span></span>

<span data-ttu-id="55c88-303">Definiert eine Botlösung zusammen mit optionalen Informationen, z. B. Standardbefehlseigenschaften.</span><span class="sxs-lookup"><span data-stu-id="55c88-303">Defines a bot solution, along with optional information such as default command properties.</span></span>

<span data-ttu-id="55c88-304">Das Element ist ein Array (maximal 1 Element ist derzeit nur ein Bot pro App zulässig) mit allen Elementen &mdash; des Typs `object` .</span><span class="sxs-lookup"><span data-stu-id="55c88-304">The item is an array (maximum of only 1 element&mdash;currently only one bot is allowed per app) with all elements of the type `object`.</span></span> <span data-ttu-id="55c88-305">Dieser Block ist nur für Lösungen erforderlich, die eine Boterfahrung bieten.</span><span class="sxs-lookup"><span data-stu-id="55c88-305">This block is required only for solutions that provide a bot experience.</span></span>

|<span data-ttu-id="55c88-306">Name</span><span class="sxs-lookup"><span data-stu-id="55c88-306">Name</span></span>| <span data-ttu-id="55c88-307">Typ</span><span class="sxs-lookup"><span data-stu-id="55c88-307">Type</span></span>| <span data-ttu-id="55c88-308">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="55c88-308">Maximum size</span></span> | <span data-ttu-id="55c88-309">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="55c88-309">Required</span></span> | <span data-ttu-id="55c88-310">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="55c88-310">Description</span></span>|
|---|---|---|---|---|
|`botId`|<span data-ttu-id="55c88-311">string</span><span class="sxs-lookup"><span data-stu-id="55c88-311">string</span></span>|<span data-ttu-id="55c88-312">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="55c88-312">64 characters</span></span>|<span data-ttu-id="55c88-313">✔</span><span class="sxs-lookup"><span data-stu-id="55c88-313">✔</span></span>|<span data-ttu-id="55c88-314">Die eindeutige Microsoft-App-ID für den Bot, wie bei Bot Framework registriert.</span><span class="sxs-lookup"><span data-stu-id="55c88-314">The unique Microsoft app ID for the bot as registered with the Bot Framework.</span></span> <span data-ttu-id="55c88-315">Dies kann mit der allgemeinen [App-ID identisch sein.](#id)</span><span class="sxs-lookup"><span data-stu-id="55c88-315">This may well be the same as the overall [app ID](#id).</span></span>|
|`scopes`|<span data-ttu-id="55c88-316">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="55c88-316">array of enums</span></span>|<span data-ttu-id="55c88-317">3 </span><span class="sxs-lookup"><span data-stu-id="55c88-317">3</span></span>|<span data-ttu-id="55c88-318">✔</span><span class="sxs-lookup"><span data-stu-id="55c88-318">✔</span></span>|<span data-ttu-id="55c88-319">Gibt an, ob der Bot eine Umgebung im Kontext eines Kanals in einem `team` oder Gruppenchat (`groupchat`) ist, oder aber eine Umgebung einzig für einen bestimmten Benutzer (`personal`).</span><span class="sxs-lookup"><span data-stu-id="55c88-319">Specifies whether the bot offers an experience in the context of a channel in a `team`, in a group chat (`groupchat`), or an experience scoped to an individual user alone (`personal`).</span></span> <span data-ttu-id="55c88-320">Diese Optionen sind nicht exklusiv.</span><span class="sxs-lookup"><span data-stu-id="55c88-320">These options are non-exclusive.</span></span>|
|`needsChannelSelector`|<span data-ttu-id="55c88-321">Boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="55c88-321">boolean</span></span>|||<span data-ttu-id="55c88-322">Beschreibt, ob der Bot einen Benutzerhinweis verwendet, um den Bot einem bestimmten Kanal hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="55c88-322">Describes whether or not the bot utilizes a user hint to add the bot to a specific channel.</span></span> <span data-ttu-id="55c88-323">Standard: **`false`**</span><span class="sxs-lookup"><span data-stu-id="55c88-323">Default: **`false`**</span></span>|
|`isNotificationOnly`|<span data-ttu-id="55c88-324">Boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="55c88-324">boolean</span></span>|||<span data-ttu-id="55c88-325">Gibt an, ob ein Bot ein unidirektionaler Bot ausschließlich für Benachrichtigungen ist (im Gegensatz zu einem dialogorientierten Bot).</span><span class="sxs-lookup"><span data-stu-id="55c88-325">Indicates whether a bot is a one-way, notification-only bot, as opposed to a conversational bot.</span></span> <span data-ttu-id="55c88-326">Standard: **`false`**</span><span class="sxs-lookup"><span data-stu-id="55c88-326">Default: **`false`**</span></span>|
|`supportsFiles`|<span data-ttu-id="55c88-327">Boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="55c88-327">boolean</span></span>|||<span data-ttu-id="55c88-328">Gibt an, ob der Bot die Möglichkeit zum Hochladen/Herunterladen von Dateien in persönliche Chats unterstützt.</span><span class="sxs-lookup"><span data-stu-id="55c88-328">Indicates whether the bot supports the ability to upload/download files in personal chat.</span></span> <span data-ttu-id="55c88-329">Standard: **`false`**</span><span class="sxs-lookup"><span data-stu-id="55c88-329">Default: **`false`**</span></span>|
|`supportsCalling`|<span data-ttu-id="55c88-330">Boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="55c88-330">boolean</span></span>|||<span data-ttu-id="55c88-331">Ein Wert, der angibt, wo ein Bot Audioanrufe unterstützt.</span><span class="sxs-lookup"><span data-stu-id="55c88-331">A value indicating where a bot supports audio calling.</span></span> <span data-ttu-id="55c88-332">**WICHTIG**: Diese Eigenschaft ist derzeit experimentell.</span><span class="sxs-lookup"><span data-stu-id="55c88-332">**IMPORTANT**: This property is currently experimental.</span></span> <span data-ttu-id="55c88-333">Experimentelle Eigenschaften sind möglicherweise nicht vollständig und werden möglicherweise geändert, bevor sie vollständig verfügbar werden.</span><span class="sxs-lookup"><span data-stu-id="55c88-333">Experimental properties may not be complete, and may undergo changes before becoming fully available.</span></span>  <span data-ttu-id="55c88-334">Es wird nur zu Test- und Explorationszwecken bereitgestellt und darf nicht in Produktionsanwendungen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="55c88-334">It is provided for testing and exploration purposes only and must not be used in production applications.</span></span> <span data-ttu-id="55c88-335">Standard: **`false`**</span><span class="sxs-lookup"><span data-stu-id="55c88-335">Default: **`false`**</span></span>|
|`supportsVideo`|<span data-ttu-id="55c88-336">Boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="55c88-336">boolean</span></span>|||<span data-ttu-id="55c88-337">Ein Wert, der angibt, wo ein Bot Videoanrufe unterstützt.</span><span class="sxs-lookup"><span data-stu-id="55c88-337">A value indicating where a bot supports video calling.</span></span> <span data-ttu-id="55c88-338">**WICHTIG**: Diese Eigenschaft ist derzeit experimentell.</span><span class="sxs-lookup"><span data-stu-id="55c88-338">**IMPORTANT**: This property is currently experimental.</span></span> <span data-ttu-id="55c88-339">Experimentelle Eigenschaften sind möglicherweise nicht vollständig und werden möglicherweise geändert, bevor sie vollständig verfügbar werden.</span><span class="sxs-lookup"><span data-stu-id="55c88-339">Experimental properties may not be complete, and may undergo changes before becoming fully available.</span></span>  <span data-ttu-id="55c88-340">Es wird nur zu Test- und Explorationszwecken bereitgestellt und darf nicht in Produktionsanwendungen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="55c88-340">It is provided for testing and exploration purposes only and must not be used in production applications.</span></span> <span data-ttu-id="55c88-341">Standard: **`false`**</span><span class="sxs-lookup"><span data-stu-id="55c88-341">Default: **`false`**</span></span>|

### <a name="botscommandlists"></a><span data-ttu-id="55c88-342">bots.commandLists</span><span class="sxs-lookup"><span data-stu-id="55c88-342">bots.commandLists</span></span>

<span data-ttu-id="55c88-343">Eine optionale Liste von Befehlen, die Ihr Bot Benutzern empfehlen kann.</span><span class="sxs-lookup"><span data-stu-id="55c88-343">An optional list of commands that your bot can recommend to users.</span></span> <span data-ttu-id="55c88-344">Das Objekt ist ein Array (maximal 2 Elemente) mit allen Elementen des Typs. Sie müssen eine separate Befehlsliste für jeden Bereich definieren, den `object` Ihr Bot unterstützt.</span><span class="sxs-lookup"><span data-stu-id="55c88-344">The object is an array (maximum of 2 elements) with all elements of type `object`; you must define a separate command list for each scope that your bot supports.</span></span> <span data-ttu-id="55c88-345">Weitere [Informationen finden Sie unter Bot-Menüs.](~/bots/how-to/create-a-bot-commands-menu.md)</span><span class="sxs-lookup"><span data-stu-id="55c88-345">See [Bot menus](~/bots/how-to/create-a-bot-commands-menu.md) for more information.</span></span>

|<span data-ttu-id="55c88-346">Name</span><span class="sxs-lookup"><span data-stu-id="55c88-346">Name</span></span>| <span data-ttu-id="55c88-347">Typ</span><span class="sxs-lookup"><span data-stu-id="55c88-347">Type</span></span>| <span data-ttu-id="55c88-348">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="55c88-348">Maximum size</span></span> | <span data-ttu-id="55c88-349">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="55c88-349">Required</span></span> | <span data-ttu-id="55c88-350">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="55c88-350">Description</span></span>|
|---|---|---|---|---|
|`items.scopes`|<span data-ttu-id="55c88-351">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="55c88-351">array of enums</span></span>|<span data-ttu-id="55c88-352">3 </span><span class="sxs-lookup"><span data-stu-id="55c88-352">3</span></span>|<span data-ttu-id="55c88-353">✔</span><span class="sxs-lookup"><span data-stu-id="55c88-353">✔</span></span>|<span data-ttu-id="55c88-354">Gibt den Bereich an, für den die Befehlsliste gültig ist.</span><span class="sxs-lookup"><span data-stu-id="55c88-354">Specifies the scope for which the command list is valid.</span></span> <span data-ttu-id="55c88-355">Mögliche Optionen sind `team`, `personal` und `groupchat`.</span><span class="sxs-lookup"><span data-stu-id="55c88-355">Options are `team`, `personal`, and `groupchat`.</span></span>|
|`items.commands`|<span data-ttu-id="55c88-356">Array von Objekten</span><span class="sxs-lookup"><span data-stu-id="55c88-356">array of objects</span></span>|<span data-ttu-id="55c88-357">10  </span><span class="sxs-lookup"><span data-stu-id="55c88-357">10</span></span>|<span data-ttu-id="55c88-358">✔</span><span class="sxs-lookup"><span data-stu-id="55c88-358">✔</span></span>|<span data-ttu-id="55c88-359">Ein Array von Befehlen, die der Bot unterstützt:</span><span class="sxs-lookup"><span data-stu-id="55c88-359">An array of commands the bot supports:</span></span><br><span data-ttu-id="55c88-360">`title`: Name des Bot-Befehls (string, 32)</span><span class="sxs-lookup"><span data-stu-id="55c88-360">`title`: the bot command name (string, 32)</span></span><br><span data-ttu-id="55c88-361">`description`: einfache Beschreibung oder Beispiel für die Befehlssyntax und zugehörige Argumente (string, 128)</span><span class="sxs-lookup"><span data-stu-id="55c88-361">`description`: a simple description or example of the command syntax and its argument (string, 128)</span></span>|

### <a name="botscommandlistscommands"></a><span data-ttu-id="55c88-362">bots.commandLists.commands</span><span class="sxs-lookup"><span data-stu-id="55c88-362">bots.commandLists.commands</span></span>

|<span data-ttu-id="55c88-363">Name</span><span class="sxs-lookup"><span data-stu-id="55c88-363">Name</span></span>| <span data-ttu-id="55c88-364">Typ</span><span class="sxs-lookup"><span data-stu-id="55c88-364">Type</span></span>| <span data-ttu-id="55c88-365">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="55c88-365">Maximum size</span></span> | <span data-ttu-id="55c88-366">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="55c88-366">Required</span></span> | <span data-ttu-id="55c88-367">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="55c88-367">Description</span></span>|
|---|---|---|---|---|
|<span data-ttu-id="55c88-368">title</span><span class="sxs-lookup"><span data-stu-id="55c88-368">title</span></span>|<span data-ttu-id="55c88-369">string</span><span class="sxs-lookup"><span data-stu-id="55c88-369">string</span></span>|<span data-ttu-id="55c88-370">12 </span><span class="sxs-lookup"><span data-stu-id="55c88-370">12</span></span>|<span data-ttu-id="55c88-371">✔</span><span class="sxs-lookup"><span data-stu-id="55c88-371">✔</span></span>|<span data-ttu-id="55c88-372">Name des Botbefehls</span><span class="sxs-lookup"><span data-stu-id="55c88-372">The bot command name</span></span>|
|<span data-ttu-id="55c88-373">description</span><span class="sxs-lookup"><span data-stu-id="55c88-373">description</span></span>|<span data-ttu-id="55c88-374">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="55c88-374">string</span></span>|<span data-ttu-id="55c88-375">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="55c88-375">128 characters</span></span>|<span data-ttu-id="55c88-376">✔</span><span class="sxs-lookup"><span data-stu-id="55c88-376">✔</span></span>|<span data-ttu-id="55c88-377">Eine einfache Textbeschreibung oder ein Beispiel für die Befehlssyntax und deren Argumente.</span><span class="sxs-lookup"><span data-stu-id="55c88-377">A simple text description or an example of the command syntax and its arguments.</span></span>|

## <a name="connectors"></a><span data-ttu-id="55c88-378">Connectors</span><span class="sxs-lookup"><span data-stu-id="55c88-378">connectors</span></span>

<span data-ttu-id="55c88-379">**Optional** – Array</span><span class="sxs-lookup"><span data-stu-id="55c88-379">**Optional** — array</span></span>

<span data-ttu-id="55c88-380">Der `connectors` Block definiert einen Office 365 Connector für die App.</span><span class="sxs-lookup"><span data-stu-id="55c88-380">The `connectors` block defines an Office 365 Connector for the app.</span></span>

<span data-ttu-id="55c88-381">Das Objekt ist ein Array (maximal 1 Element) mit allen Elementen vom Typ `object` .</span><span class="sxs-lookup"><span data-stu-id="55c88-381">The object is an array (maximum of 1 element) with all elements of type `object`.</span></span> <span data-ttu-id="55c88-382">Dieser Block ist nur für Lösungen erforderlich, die einen Connector bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="55c88-382">This block is required only for solutions that provide a Connector.</span></span>

|<span data-ttu-id="55c88-383">Name</span><span class="sxs-lookup"><span data-stu-id="55c88-383">Name</span></span>| <span data-ttu-id="55c88-384">Typ</span><span class="sxs-lookup"><span data-stu-id="55c88-384">Type</span></span>| <span data-ttu-id="55c88-385">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="55c88-385">Maximum size</span></span> | <span data-ttu-id="55c88-386">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="55c88-386">Required</span></span> | <span data-ttu-id="55c88-387">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="55c88-387">Description</span></span>|
|---|---|---|---|---|
|`configurationUrl`|<span data-ttu-id="55c88-388">string</span><span class="sxs-lookup"><span data-stu-id="55c88-388">string</span></span>|<span data-ttu-id="55c88-389">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="55c88-389">2048 characters</span></span>|<span data-ttu-id="55c88-390">✔</span><span class="sxs-lookup"><span data-stu-id="55c88-390">✔</span></span>|<span data-ttu-id="55c88-391">Die https://-URL, die beim Konfigurieren des Connectors verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="55c88-391">The https:// URL to use when configuring the connector.</span></span>|
|`scopes`|<span data-ttu-id="55c88-392">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="55c88-392">array of enums</span></span>|<span data-ttu-id="55c88-393">1 </span><span class="sxs-lookup"><span data-stu-id="55c88-393">1</span></span>|<span data-ttu-id="55c88-394">✔</span><span class="sxs-lookup"><span data-stu-id="55c88-394">✔</span></span>|<span data-ttu-id="55c88-395">Gibt an, ob der Connector eine Benutzeroberfläche im Kontext eines Kanals in einem oder eine Benutzeroberfläche bietet, die auf einen einzelnen Benutzer `team` begrenzt ist ( `personal` ).</span><span class="sxs-lookup"><span data-stu-id="55c88-395">Specifies whether the Connector offers an experience in the context of a channel in a `team`, or an experience scoped to an individual user alone (`personal`).</span></span> <span data-ttu-id="55c88-396">Derzeit wird nur `team` der Bereich unterstützt.</span><span class="sxs-lookup"><span data-stu-id="55c88-396">Currently, only the `team` scope is supported.</span></span>|
|`connectorId`|<span data-ttu-id="55c88-397">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="55c88-397">string</span></span>|<span data-ttu-id="55c88-398">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="55c88-398">64 characters</span></span>|<span data-ttu-id="55c88-399">✔</span><span class="sxs-lookup"><span data-stu-id="55c88-399">✔</span></span>|<span data-ttu-id="55c88-400">Ein eindeutiger Bezeichner für den Connector, der seiner ID im [Connectors Developer Dashboard entspricht.](https://aka.ms/connectorsdashboard)</span><span class="sxs-lookup"><span data-stu-id="55c88-400">A unique identifier for the Connector that matches its ID in the [Connectors Developer Dashboard](https://aka.ms/connectorsdashboard).</span></span>|

## <a name="composeextensions"></a><span data-ttu-id="55c88-401">composeExtensions</span><span class="sxs-lookup"><span data-stu-id="55c88-401">composeExtensions</span></span>

<span data-ttu-id="55c88-402">**Optional** – Array</span><span class="sxs-lookup"><span data-stu-id="55c88-402">**Optional** — array</span></span>

<span data-ttu-id="55c88-403">Definiert eine Messagingerweiterung für die App.</span><span class="sxs-lookup"><span data-stu-id="55c88-403">Defines a messaging extension for the app.</span></span>

> [!NOTE]
> <span data-ttu-id="55c88-404">Der Name des Features wurde im November 2017 von "Verfassenerweiterung" in "Messagingerweiterung" geändert, der Manifestname bleibt jedoch unverändert, damit vorhandene Erweiterungen weiterhin funktionieren.</span><span class="sxs-lookup"><span data-stu-id="55c88-404">The name of the feature was changed from "compose extension" to "messaging extension" in November, 2017, but the manifest name remains the same so that existing extensions continue to function.</span></span>

<span data-ttu-id="55c88-405">Das Element ist ein Array (maximal 1 Element) mit allen Elementen vom Typ `object` .</span><span class="sxs-lookup"><span data-stu-id="55c88-405">The item is an array (maximum of 1 element) with all elements of type `object`.</span></span> <span data-ttu-id="55c88-406">Dieser Block ist nur für Lösungen erforderlich, die eine Messagingerweiterung bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="55c88-406">This block is required only for solutions that provide a messaging extension.</span></span>

|<span data-ttu-id="55c88-407">Name</span><span class="sxs-lookup"><span data-stu-id="55c88-407">Name</span></span>| <span data-ttu-id="55c88-408">Typ</span><span class="sxs-lookup"><span data-stu-id="55c88-408">Type</span></span> | <span data-ttu-id="55c88-409">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="55c88-409">Maximum Size</span></span> | <span data-ttu-id="55c88-410">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="55c88-410">Required</span></span> | <span data-ttu-id="55c88-411">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="55c88-411">Description</span></span>|
|---|---|---|---|---|
|`botId`|<span data-ttu-id="55c88-412">string</span><span class="sxs-lookup"><span data-stu-id="55c88-412">string</span></span>|<span data-ttu-id="55c88-413">64</span><span class="sxs-lookup"><span data-stu-id="55c88-413">64</span></span>|<span data-ttu-id="55c88-414">✔</span><span class="sxs-lookup"><span data-stu-id="55c88-414">✔</span></span>|<span data-ttu-id="55c88-415">Die eindeutige Microsoft-App-ID für den Bot, der die Messagingerweiterung unterstützt, wie beim Bot Framework registriert.</span><span class="sxs-lookup"><span data-stu-id="55c88-415">The unique Microsoft app ID for the bot that backs the messaging extension, as registered with the Bot Framework.</span></span> <span data-ttu-id="55c88-416">Dies kann mit der allgemeinen App-ID identisch sein.</span><span class="sxs-lookup"><span data-stu-id="55c88-416">This may well be the same as the overall App ID.</span></span>|
|`commands`|<span data-ttu-id="55c88-417">Array von Objekten</span><span class="sxs-lookup"><span data-stu-id="55c88-417">array of objects</span></span>|<span data-ttu-id="55c88-418">10  </span><span class="sxs-lookup"><span data-stu-id="55c88-418">10</span></span>|<span data-ttu-id="55c88-419">✔</span><span class="sxs-lookup"><span data-stu-id="55c88-419">✔</span></span>|<span data-ttu-id="55c88-420">Array von Befehlen, die von der Messagingerweiterung unterstützt werden</span><span class="sxs-lookup"><span data-stu-id="55c88-420">Array of commands the messaging extension supports</span></span>|
|`canUpdateConfiguration`|<span data-ttu-id="55c88-421">Boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="55c88-421">boolean</span></span>|||<span data-ttu-id="55c88-422">Ein Wert, der angibt, ob die Konfiguration einer Messagingerweiterung vom Benutzer aktualisiert werden kann.</span><span class="sxs-lookup"><span data-stu-id="55c88-422">A value indicating whether the configuration of a messaging extension can be updated by the user.</span></span> <span data-ttu-id="55c88-423">Standard: **False**.</span><span class="sxs-lookup"><span data-stu-id="55c88-423">Default: **false**.</span></span>|
|`messageHandlers`|<span data-ttu-id="55c88-424">Array von Objekten</span><span class="sxs-lookup"><span data-stu-id="55c88-424">array of Objects</span></span>|<span data-ttu-id="55c88-425">5 </span><span class="sxs-lookup"><span data-stu-id="55c88-425">5</span></span>||<span data-ttu-id="55c88-426">Eine Liste von Handlern, mit denen Apps aufgerufen werden können, wenn bestimmte Bedingungen erfüllt sind.</span><span class="sxs-lookup"><span data-stu-id="55c88-426">A list of handlers that allow apps to be invoked when certain conditions are met.</span></span>|
|`messageHandlers.type`|<span data-ttu-id="55c88-427">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="55c88-427">string</span></span>|||<span data-ttu-id="55c88-428">Der Typ des Nachrichtenhandlers.</span><span class="sxs-lookup"><span data-stu-id="55c88-428">The type of message handler.</span></span> <span data-ttu-id="55c88-429">Muss `"link"` sein.</span><span class="sxs-lookup"><span data-stu-id="55c88-429">Must be `"link"`.</span></span>|
|`messageHandlers.value.domains`|<span data-ttu-id="55c88-430">Array von Zeichenfolgen</span><span class="sxs-lookup"><span data-stu-id="55c88-430">array of Strings</span></span>|||<span data-ttu-id="55c88-431">Array von Domänen, für die der Linknachrichtenhandler registrieren kann.</span><span class="sxs-lookup"><span data-stu-id="55c88-431">Array of domains that the link message handler can register for.</span></span>|

### <a name="composeextensionscommands"></a><span data-ttu-id="55c88-432">composeExtensions.commands</span><span class="sxs-lookup"><span data-stu-id="55c88-432">composeExtensions.commands</span></span>

<span data-ttu-id="55c88-433">Ihre Messagingerweiterung muss einen oder mehrere Befehle deklarieren.</span><span class="sxs-lookup"><span data-stu-id="55c88-433">Your messaging extension must declare one or more commands.</span></span> <span data-ttu-id="55c88-434">Jeder Befehl wird in Microsoft Teams als potenzielle Interaktion vom benutzeroberflächenbasierten Einstiegspunkt angezeigt.</span><span class="sxs-lookup"><span data-stu-id="55c88-434">Each command appears in Microsoft Teams as a potential interaction from the UI-based entry point.</span></span> <span data-ttu-id="55c88-435">Es gibt maximal 10 Befehle.</span><span class="sxs-lookup"><span data-stu-id="55c88-435">There is a maximum of 10 commands.</span></span>

<span data-ttu-id="55c88-436">Jedes Befehlselement ist ein Objekt mit der folgenden Struktur:</span><span class="sxs-lookup"><span data-stu-id="55c88-436">Each command item is an object with the following structure:</span></span>

|<span data-ttu-id="55c88-437">Name</span><span class="sxs-lookup"><span data-stu-id="55c88-437">Name</span></span>| <span data-ttu-id="55c88-438">Typ</span><span class="sxs-lookup"><span data-stu-id="55c88-438">Type</span></span>| <span data-ttu-id="55c88-439">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="55c88-439">Maximum size</span></span> | <span data-ttu-id="55c88-440">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="55c88-440">Required</span></span> | <span data-ttu-id="55c88-441">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="55c88-441">Description</span></span>|
|---|---|---|---|---|
|`id`|<span data-ttu-id="55c88-442">string</span><span class="sxs-lookup"><span data-stu-id="55c88-442">string</span></span>|<span data-ttu-id="55c88-443">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="55c88-443">64 characters</span></span>|<span data-ttu-id="55c88-444">✔</span><span class="sxs-lookup"><span data-stu-id="55c88-444">✔</span></span>|<span data-ttu-id="55c88-445">Die ID für den Befehl.</span><span class="sxs-lookup"><span data-stu-id="55c88-445">The ID for the command.</span></span>|
|`title`|<span data-ttu-id="55c88-446">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="55c88-446">string</span></span>|<span data-ttu-id="55c88-447">32 Zeichen</span><span class="sxs-lookup"><span data-stu-id="55c88-447">32 characters</span></span>|<span data-ttu-id="55c88-448">✔</span><span class="sxs-lookup"><span data-stu-id="55c88-448">✔</span></span>|<span data-ttu-id="55c88-449">Der benutzerfreundliche Befehlsname.</span><span class="sxs-lookup"><span data-stu-id="55c88-449">The user-friendly command name.</span></span>|
|`type`|<span data-ttu-id="55c88-450">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="55c88-450">string</span></span>|<span data-ttu-id="55c88-451">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="55c88-451">64 characters</span></span>||<span data-ttu-id="55c88-452">Typ des Befehls.</span><span class="sxs-lookup"><span data-stu-id="55c88-452">Type of the command.</span></span> <span data-ttu-id="55c88-453">Einer oder `query` `action` .</span><span class="sxs-lookup"><span data-stu-id="55c88-453">One of `query` or `action`.</span></span> <span data-ttu-id="55c88-454">Standard: **Abfrage**.</span><span class="sxs-lookup"><span data-stu-id="55c88-454">Default: **query**.</span></span>|
|`description`|<span data-ttu-id="55c88-455">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="55c88-455">string</span></span>|<span data-ttu-id="55c88-456">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="55c88-456">128 characters</span></span>||<span data-ttu-id="55c88-457">Die Beschreibung, die Benutzern angezeigt wird, um den Zweck dieses Befehls anzugeben.</span><span class="sxs-lookup"><span data-stu-id="55c88-457">The description that appears to users to indicate the purpose of this command.</span></span>|
|`initialRun`|<span data-ttu-id="55c88-458">Boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="55c88-458">boolean</span></span>|||<span data-ttu-id="55c88-459">Ein boolescher Wert gibt an, ob der Befehl anfangs ohne Parameter ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="55c88-459">A boolean value indicates whether the command runs initially with no parameters.</span></span> <span data-ttu-id="55c88-460">Der Standardwert ist **false**.</span><span class="sxs-lookup"><span data-stu-id="55c88-460">Default is **false**.</span></span>|
|`context`|<span data-ttu-id="55c88-461">Array von Zeichenfolgen</span><span class="sxs-lookup"><span data-stu-id="55c88-461">array of Strings</span></span>|<span data-ttu-id="55c88-462">3 </span><span class="sxs-lookup"><span data-stu-id="55c88-462">3</span></span>||<span data-ttu-id="55c88-463">Definiert, von wo aus die Nachrichtenerweiterung aufgerufen werden kann.</span><span class="sxs-lookup"><span data-stu-id="55c88-463">Defines where the message extension can be invoked from.</span></span> <span data-ttu-id="55c88-464">Beliebige Kombination aus `compose` , `commandBox` , `message` .</span><span class="sxs-lookup"><span data-stu-id="55c88-464">Any combination of`compose`,`commandBox`,`message`.</span></span> <span data-ttu-id="55c88-465">Der Standardwert ist `["compose","commandBox"]`.</span><span class="sxs-lookup"><span data-stu-id="55c88-465">Default is `["compose","commandBox"]`.</span></span>|
|`fetchTask`|<span data-ttu-id="55c88-466">Boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="55c88-466">boolean</span></span>|||<span data-ttu-id="55c88-467">Ein boolescher Wert, der angibt, ob das Aufgabenmodul dynamisch abgerufen werden muss.</span><span class="sxs-lookup"><span data-stu-id="55c88-467">A boolean value that indicates if it must fetch the task module dynamically.</span></span> <span data-ttu-id="55c88-468">Der Standardwert ist **false**.</span><span class="sxs-lookup"><span data-stu-id="55c88-468">Default is **false**.</span></span>|
|`taskInfo`|<span data-ttu-id="55c88-469">Objekt</span><span class="sxs-lookup"><span data-stu-id="55c88-469">object</span></span>|||<span data-ttu-id="55c88-470">Geben Sie das Aufgabenmodul an, das beim Verwenden eines Befehls für die Messagingerweiterung vor dem Laden geladen werden soll.</span><span class="sxs-lookup"><span data-stu-id="55c88-470">Specify the task module to pre-load when using a messaging extension command.</span></span>|
|`taskInfo.title`|<span data-ttu-id="55c88-471">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="55c88-471">string</span></span>|<span data-ttu-id="55c88-472">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="55c88-472">64 characters</span></span>||<span data-ttu-id="55c88-473">Titel des ersten Dialogfelds.</span><span class="sxs-lookup"><span data-stu-id="55c88-473">Initial dialog title.</span></span>|
|`taskInfo.width`|<span data-ttu-id="55c88-474">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="55c88-474">string</span></span>|||<span data-ttu-id="55c88-475">Dialogbreite – entweder eine Zahl in Pixel oder ein Standardlayout wie "groß", "mittel" oder "klein".</span><span class="sxs-lookup"><span data-stu-id="55c88-475">Dialog width - either a number in pixels or default layout such as 'large', 'medium', or 'small'.</span></span>|
|`taskInfo.height`|<span data-ttu-id="55c88-476">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="55c88-476">string</span></span>|||<span data-ttu-id="55c88-477">Dialoghöhe – entweder eine Zahl in Pixel oder ein Standardlayout wie "groß", "mittel" oder "klein".</span><span class="sxs-lookup"><span data-stu-id="55c88-477">Dialog height - either a number in pixels or default layout such as 'large', 'medium', or 'small'.</span></span>|
|`taskInfo.url`|<span data-ttu-id="55c88-478">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="55c88-478">string</span></span>|||<span data-ttu-id="55c88-479">Anfängliche Webview-URL.</span><span class="sxs-lookup"><span data-stu-id="55c88-479">Initial webview URL.</span></span>|
|`parameters`|<span data-ttu-id="55c88-480">Array des Objekts</span><span class="sxs-lookup"><span data-stu-id="55c88-480">array of object</span></span>|<span data-ttu-id="55c88-481">5 Elemente</span><span class="sxs-lookup"><span data-stu-id="55c88-481">5 items</span></span>|<span data-ttu-id="55c88-482">✔</span><span class="sxs-lookup"><span data-stu-id="55c88-482">✔</span></span>|<span data-ttu-id="55c88-483">Die Liste der Parameter, die der Befehl verwendet.</span><span class="sxs-lookup"><span data-stu-id="55c88-483">The list of parameters the command takes.</span></span> <span data-ttu-id="55c88-484">Minimum: 1; maximum: 5.</span><span class="sxs-lookup"><span data-stu-id="55c88-484">Minimum: 1; maximum: 5.</span></span>|
|`parameters.name`|<span data-ttu-id="55c88-485">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="55c88-485">string</span></span>|<span data-ttu-id="55c88-486">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="55c88-486">64 characters</span></span>|<span data-ttu-id="55c88-487">✔</span><span class="sxs-lookup"><span data-stu-id="55c88-487">✔</span></span>|<span data-ttu-id="55c88-488">Der Name des Parameters, wie er im Client angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="55c88-488">The name of the parameter as it appears in the client.</span></span> <span data-ttu-id="55c88-489">Dies ist in der Benutzeranforderung enthalten.</span><span class="sxs-lookup"><span data-stu-id="55c88-489">This is included in the user request.</span></span>|
|`parameters.title`|<span data-ttu-id="55c88-490">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="55c88-490">string</span></span>|<span data-ttu-id="55c88-491">32 Zeichen</span><span class="sxs-lookup"><span data-stu-id="55c88-491">32 characters</span></span>|<span data-ttu-id="55c88-492">✔</span><span class="sxs-lookup"><span data-stu-id="55c88-492">✔</span></span>|<span data-ttu-id="55c88-493">Benutzerfreundlicher Titel für den Parameter.</span><span class="sxs-lookup"><span data-stu-id="55c88-493">User-friendly title for the parameter.</span></span>|
|`parameters.description`|<span data-ttu-id="55c88-494">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="55c88-494">string</span></span>|<span data-ttu-id="55c88-495">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="55c88-495">128 characters</span></span>||<span data-ttu-id="55c88-496">Benutzerfreundliche Zeichenfolge, die den Zweck dieses Parameters beschreibt.</span><span class="sxs-lookup"><span data-stu-id="55c88-496">User-friendly string that describes this parameter’s purpose.</span></span>|
|`parameters.value`|<span data-ttu-id="55c88-497">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="55c88-497">string</span></span>|<span data-ttu-id="55c88-498">512 Zeichen</span><span class="sxs-lookup"><span data-stu-id="55c88-498">512 characters</span></span>||<span data-ttu-id="55c88-499">Anfangswert für den Parameter.</span><span class="sxs-lookup"><span data-stu-id="55c88-499">Initial value for the parameter.</span></span>|
|`parameters.inputType`|<span data-ttu-id="55c88-500">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="55c88-500">string</span></span>|<span data-ttu-id="55c88-501">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="55c88-501">128 characters</span></span>||<span data-ttu-id="55c88-502">Definiert den Typ des Steuerelements, das in einem Aufgabenmodul für angezeigt `fetchTask: true` wird.</span><span class="sxs-lookup"><span data-stu-id="55c88-502">Defines the type of control displayed on a task module for`fetchTask: true` .</span></span> <span data-ttu-id="55c88-503">Einer von `text, textarea, number, date, time, toggle, choiceset` .</span><span class="sxs-lookup"><span data-stu-id="55c88-503">One of `text, textarea, number, date, time, toggle, choiceset` .</span></span>|
|`parameters.choices`|<span data-ttu-id="55c88-504">Array von Objekten</span><span class="sxs-lookup"><span data-stu-id="55c88-504">array of objects</span></span>|<span data-ttu-id="55c88-505">10 Elemente</span><span class="sxs-lookup"><span data-stu-id="55c88-505">10 items</span></span>||<span data-ttu-id="55c88-506">Die Auswahloptionen für `choiceset` .</span><span class="sxs-lookup"><span data-stu-id="55c88-506">The choice options for the`choiceset`.</span></span> <span data-ttu-id="55c88-507">Verwenden Sie nur, `parameter.inputType` wenn `choiceset` .</span><span class="sxs-lookup"><span data-stu-id="55c88-507">Use only when`parameter.inputType` is `choiceset`.</span></span>|
|`parameters.choices.title`|<span data-ttu-id="55c88-508">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="55c88-508">string</span></span>|<span data-ttu-id="55c88-509">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="55c88-509">128 characters</span></span>|<span data-ttu-id="55c88-510">✔</span><span class="sxs-lookup"><span data-stu-id="55c88-510">✔</span></span>|<span data-ttu-id="55c88-511">Titel der Auswahl.</span><span class="sxs-lookup"><span data-stu-id="55c88-511">Title of the choice.</span></span>|
|`parameters.choices.value`|<span data-ttu-id="55c88-512">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="55c88-512">string</span></span>|<span data-ttu-id="55c88-513">512 Zeichen</span><span class="sxs-lookup"><span data-stu-id="55c88-513">512 characters</span></span>|<span data-ttu-id="55c88-514">✔</span><span class="sxs-lookup"><span data-stu-id="55c88-514">✔</span></span>|<span data-ttu-id="55c88-515">Value of the choice.</span><span class="sxs-lookup"><span data-stu-id="55c88-515">Value of the choice.</span></span>|

## <a name="permissions"></a><span data-ttu-id="55c88-516">Berechtigungen</span><span class="sxs-lookup"><span data-stu-id="55c88-516">permissions</span></span>

<span data-ttu-id="55c88-517">**Optional** – Array von Zeichenfolgen</span><span class="sxs-lookup"><span data-stu-id="55c88-517">**Optional** — array of strings</span></span>

<span data-ttu-id="55c88-518">Ein Array von dem angibt, welche Berechtigungen die App anfordert, wodurch Endbenutzer wissen, `string` wie die Erweiterung funktioniert.</span><span class="sxs-lookup"><span data-stu-id="55c88-518">An array of `string` which specifies which permissions the app requests, which lets end users know how the extension performs.</span></span> <span data-ttu-id="55c88-519">Die folgenden Optionen sind nicht exklusiv:</span><span class="sxs-lookup"><span data-stu-id="55c88-519">The following options are non-exclusive:</span></span>

* <span data-ttu-id="55c88-520">`identity`&emsp;Erfordert Benutzeridentitätsinformationen</span><span class="sxs-lookup"><span data-stu-id="55c88-520">`identity` &emsp; Requires user identity information</span></span>
* <span data-ttu-id="55c88-521">`messageTeamMembers`&emsp;Erfordert die Berechtigung zum Senden von Direktnachrichten an Teammitglieder</span><span class="sxs-lookup"><span data-stu-id="55c88-521">`messageTeamMembers` &emsp; Requires permission to send direct messages to team members</span></span>

<span data-ttu-id="55c88-522">Wenn Sie diese Berechtigungen während des App-Updates ändern, wiederholen Ihre Benutzer den Zustimmungsprozess, nachdem sie die aktualisierte App ausgeführt haben.</span><span class="sxs-lookup"><span data-stu-id="55c88-522">Changing these permissions during app update, causes your users to repeat the consent process after they run the updated app.</span></span> <span data-ttu-id="55c88-523">Weitere [Informationen finden Sie unter Aktualisieren](~/concepts/deploy-and-publish/appsource/post-publish/overview.md) Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="55c88-523">See [Updating your app](~/concepts/deploy-and-publish/appsource/post-publish/overview.md) for more information.</span></span>

## <a name="devicepermissions"></a><span data-ttu-id="55c88-524">devicePermissions</span><span class="sxs-lookup"><span data-stu-id="55c88-524">devicePermissions</span></span>

<span data-ttu-id="55c88-525">**Optional** – Array von Zeichenfolgen</span><span class="sxs-lookup"><span data-stu-id="55c88-525">**Optional** — array of strings</span></span>

<span data-ttu-id="55c88-526">Stellt die systemeigenen Features auf dem Gerät eines Benutzers zur Verfügung, auf das Ihre App Zugriff anfordert.</span><span class="sxs-lookup"><span data-stu-id="55c88-526">Provides the native features on a user's device that your app requests access to.</span></span> <span data-ttu-id="55c88-527">Mögliche Optionen sind:</span><span class="sxs-lookup"><span data-stu-id="55c88-527">Options are:</span></span>

* `geolocation`
* `media`
* `notifications`
* `midi`
* `openExternal`

## <a name="validdomains"></a><span data-ttu-id="55c88-528">validDomains</span><span class="sxs-lookup"><span data-stu-id="55c88-528">validDomains</span></span>

<span data-ttu-id="55c88-529">**Optional**, mit **Ausnahme erforderlich,** sofern angegeben</span><span class="sxs-lookup"><span data-stu-id="55c88-529">**Optional**, except **Required** where noted</span></span>

<span data-ttu-id="55c88-530">Eine Liste der gültigen Domänen für Websites, die die App im Teams-Client laden soll.</span><span class="sxs-lookup"><span data-stu-id="55c88-530">A list of valid domains for websites the app expects to load within the Teams client.</span></span> <span data-ttu-id="55c88-531">Domänenauflistungen können Platzhalter enthalten, z. B. `*.example.com` .</span><span class="sxs-lookup"><span data-stu-id="55c88-531">Domain listings can include wildcards, for example, `*.example.com`.</span></span> <span data-ttu-id="55c88-532">Dies entspricht genau einem Abschnitt der Domäne. wenn Sie übereinstimmen müssen, `a.b.example.com` verwenden Sie `*.*.example.com` .</span><span class="sxs-lookup"><span data-stu-id="55c88-532">This matches exactly one segment of the domain; if you need to match `a.b.example.com` then use `*.*.example.com`.</span></span> <span data-ttu-id="55c88-533">Wenn Ihre Registerkartenkonfiguration oder Inhaltsbenutzeroberfläche neben der für die Registerkartenkonfiguration verwendeten Domäne zu einer anderen Domäne navigieren muss, muss diese Domäne hier angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="55c88-533">If your tab configuration or content UI needs to navigate to any other domain besides the one use for tab configuration, that domain must be specified here.</span></span>

<span data-ttu-id="55c88-534">Es ist **nicht** erforderlich, die Domänen von Identitätsanbietern, die Sie unterstützen möchten, in Ihre App zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="55c88-534">It is **not** necessary to include the domains of identity providers you want to support in your app.</span></span> <span data-ttu-id="55c88-535">Um sich z. B. mithilfe einer Google-ID zu authentifizieren, müssen Sie an accounts.google.com umleiten, sie dürfen jedoch accounts.google.com in nicht `validDomains[]` enthalten.</span><span class="sxs-lookup"><span data-stu-id="55c88-535">For example, to authenticate using a Google ID, it is required to redirect to accounts.google.com, however, you must not include accounts.google.com in `validDomains[]`.</span></span>

<span data-ttu-id="55c88-536">Teams-Apps, für die eigene Sharepoint-URLs ordnungsgemäß funktionieren müssen, enthalten "{teamsitedomain}" in ihrer gültigen Domänenliste.</span><span class="sxs-lookup"><span data-stu-id="55c88-536">Teams apps that require their own sharepoint URLs to function well, includes "{teamsitedomain}" in their valid domain list.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="55c88-537">Fügen Sie keine Domänen hinzu, die sich außerhalb Ihres Steuerelements befinden, weder direkt noch über Platzhalter.</span><span class="sxs-lookup"><span data-stu-id="55c88-537">Do not add domains that are outside your control, either directly or through wildcards.</span></span> <span data-ttu-id="55c88-538">Ist z. `yourapp.onmicrosoft.com` B. gültig, ist `*.onmicrosoft.com` jedoch ungültig.</span><span class="sxs-lookup"><span data-stu-id="55c88-538">For example, `yourapp.onmicrosoft.com` is valid, however, `*.onmicrosoft.com` is not valid.</span></span>

<span data-ttu-id="55c88-539">Das Objekt ist ein Array mit allen Elementen des Typs `string` .</span><span class="sxs-lookup"><span data-stu-id="55c88-539">The object is an array with all elements of the type `string`.</span></span>

## <a name="webapplicationinfo"></a><span data-ttu-id="55c88-540">webApplicationInfo</span><span class="sxs-lookup"><span data-stu-id="55c88-540">webApplicationInfo</span></span>

<span data-ttu-id="55c88-541">**Optional** – -Objekt</span><span class="sxs-lookup"><span data-stu-id="55c88-541">**Optional** — object</span></span>

<span data-ttu-id="55c88-542">Stellen Sie Ihre Azure Active Directory (AAD)-App-ID und Microsoft Graph-Informationen bereit, um Benutzern die nahtlose Anmeldung bei Ihrer App zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="55c88-542">Provide your Azure Active Directory (AAD) App ID and Microsoft Graph information to help users seamlessly sign into your app.</span></span> <span data-ttu-id="55c88-543">Wenn Ihre App in AAD registriert ist, müssen Sie die App-ID bereitstellen, damit Administratoren die Berechtigungen problemlos überprüfen und im Teams Admin Center zustimmen können.</span><span class="sxs-lookup"><span data-stu-id="55c88-543">If your app is registered in AAD, you must provide the App ID, so that administrators can easily review permissions and grant consent in Teams admin center.</span></span>

|<span data-ttu-id="55c88-544">Name</span><span class="sxs-lookup"><span data-stu-id="55c88-544">Name</span></span>| <span data-ttu-id="55c88-545">Typ</span><span class="sxs-lookup"><span data-stu-id="55c88-545">Type</span></span>| <span data-ttu-id="55c88-546">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="55c88-546">Maximum size</span></span> | <span data-ttu-id="55c88-547">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="55c88-547">Required</span></span> | <span data-ttu-id="55c88-548">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="55c88-548">Description</span></span>|
|---|---|---|---|---|
|`id`|<span data-ttu-id="55c88-549">string</span><span class="sxs-lookup"><span data-stu-id="55c88-549">string</span></span>|<span data-ttu-id="55c88-550">36 Zeichen</span><span class="sxs-lookup"><span data-stu-id="55c88-550">36 characters</span></span>|<span data-ttu-id="55c88-551">✔</span><span class="sxs-lookup"><span data-stu-id="55c88-551">✔</span></span>|<span data-ttu-id="55c88-552">AAD-Anwendungs-ID der App.</span><span class="sxs-lookup"><span data-stu-id="55c88-552">AAD application id of the app.</span></span> <span data-ttu-id="55c88-553">Diese ID muss eine GUID sein.</span><span class="sxs-lookup"><span data-stu-id="55c88-553">This id must be a GUID.</span></span>|
|`resource`|<span data-ttu-id="55c88-554">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="55c88-554">string</span></span>|<span data-ttu-id="55c88-555">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="55c88-555">2048 characters</span></span>|<span data-ttu-id="55c88-556">✔</span><span class="sxs-lookup"><span data-stu-id="55c88-556">✔</span></span>|<span data-ttu-id="55c88-557">Ressourcen-URL der App zum Abrufen des Authentifizierungstokens für SSO.</span><span class="sxs-lookup"><span data-stu-id="55c88-557">Resource URL of app for acquiring auth token for SSO.</span></span> </br> <span data-ttu-id="55c88-558">**HINWEIS:** Wenn Sie SSO nicht verwenden, stellen Sie sicher, dass Sie in diesem Feld einen Schnullerzeichenfolgenwert in Ihr App-Manifest eingeben, um beispielsweise eine https://notapplicable Fehlerantwort zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="55c88-558">**NOTE:** If you are not using SSO, ensure that you enter a dummy string value in this field to your app manifest, for example, https://notapplicable to avoid an error response.</span></span> |
|`applicationPermissions`|<span data-ttu-id="55c88-559">array of strings</span><span class="sxs-lookup"><span data-stu-id="55c88-559">array of strings</span></span>|<span data-ttu-id="55c88-560">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="55c88-560">128 characters</span></span>||<span data-ttu-id="55c88-561">Geben Sie [granulare ressourcenspezifische Zustimmung an.](../../graph-api/rsc/resource-specific-consent.md#resource-specific-permissions)</span><span class="sxs-lookup"><span data-stu-id="55c88-561">Specify granular [resource specific consent](../../graph-api/rsc/resource-specific-consent.md#resource-specific-permissions).</span></span>|

## <a name="showloadingindicator"></a><span data-ttu-id="55c88-562">showLoadingIndicator</span><span class="sxs-lookup"><span data-stu-id="55c88-562">showLoadingIndicator</span></span>

<span data-ttu-id="55c88-563">**Optional** – boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="55c88-563">**Optional** — boolean</span></span>

<span data-ttu-id="55c88-564">Gibt an, ob die Ladeanzeige angezeigt werden soll, wenn eine App oder Registerkarte geladen wird.</span><span class="sxs-lookup"><span data-stu-id="55c88-564">Indicates whether or not to show the loading indicator when an app or tab is loading.</span></span> <span data-ttu-id="55c88-565">Der Standardwert ist **false**.</span><span class="sxs-lookup"><span data-stu-id="55c88-565">Default is **false**.</span></span>
>[!NOTE]
><span data-ttu-id="55c88-566">Wenn Sie im App-Manifest als true auswählen, ändern Sie die Inhaltsseiten Ihrer Registerkarten und Aufgabenmodule, um die Seite ordnungsgemäß zu laden, wie unter Anzeigen eines nativen Ladeindikatordokuments `showLoadingIndicator` beschrieben. [](../../tabs/how-to/create-tab-pages/content-page.md#show-a-native-loading-indicator)</span><span class="sxs-lookup"><span data-stu-id="55c88-566">If you select`showLoadingIndicator` as true in your app manifest, to load the page correctly, modify the content pages of your tabs and task modules as described in [Show a native loading indicator](../../tabs/how-to/create-tab-pages/content-page.md#show-a-native-loading-indicator) document.</span></span>


## <a name="isfullscreen"></a><span data-ttu-id="55c88-567">isFullScreen</span><span class="sxs-lookup"><span data-stu-id="55c88-567">isFullScreen</span></span>

 <span data-ttu-id="55c88-568">**Optional** – boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="55c88-568">**Optional** — boolean</span></span>

<span data-ttu-id="55c88-569">Geben Sie an, wo eine persönliche App mit oder ohne Registerkartenkopfleiste gerendert wird.</span><span class="sxs-lookup"><span data-stu-id="55c88-569">Indicate where a personal app is rendered with or without a tab header bar.</span></span> <span data-ttu-id="55c88-570">Der Standardwert ist **false**.</span><span class="sxs-lookup"><span data-stu-id="55c88-570">Default is **false**.</span></span>

## <a name="activities"></a><span data-ttu-id="55c88-571">Aktivitäten</span><span class="sxs-lookup"><span data-stu-id="55c88-571">activities</span></span>

<span data-ttu-id="55c88-572">**Optional** – -Objekt</span><span class="sxs-lookup"><span data-stu-id="55c88-572">**Optional** — object</span></span>

<span data-ttu-id="55c88-573">Definieren Sie die Eigenschaften, die Ihre App zum Posten eines Benutzeraktivitätsfeeds verwendet.</span><span class="sxs-lookup"><span data-stu-id="55c88-573">Define the properties your app uses to post a user activity feed.</span></span>

|<span data-ttu-id="55c88-574">Name</span><span class="sxs-lookup"><span data-stu-id="55c88-574">Name</span></span>| <span data-ttu-id="55c88-575">Typ</span><span class="sxs-lookup"><span data-stu-id="55c88-575">Type</span></span>| <span data-ttu-id="55c88-576">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="55c88-576">Maximum size</span></span> | <span data-ttu-id="55c88-577">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="55c88-577">Required</span></span> | <span data-ttu-id="55c88-578">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="55c88-578">Description</span></span>|
|---|---|---|---|---|
|`activityTypes`|<span data-ttu-id="55c88-579">Array von Objekten</span><span class="sxs-lookup"><span data-stu-id="55c88-579">array of Objects</span></span>|<span data-ttu-id="55c88-580">128 Elemente</span><span class="sxs-lookup"><span data-stu-id="55c88-580">128 items</span></span>| | <span data-ttu-id="55c88-581">Stellen Sie die Arten von Aktivitäten zur Verfügung, die Ihre App an einen Benutzeraktivitätsfeed posten kann.</span><span class="sxs-lookup"><span data-stu-id="55c88-581">Provide the types of activities that your app can post to a users activity feed.</span></span>|

### <a name="activitiesactivitytypes"></a><span data-ttu-id="55c88-582">activities.activityTypes</span><span class="sxs-lookup"><span data-stu-id="55c88-582">activities.activityTypes</span></span>

|<span data-ttu-id="55c88-583">Name</span><span class="sxs-lookup"><span data-stu-id="55c88-583">Name</span></span>| <span data-ttu-id="55c88-584">Typ</span><span class="sxs-lookup"><span data-stu-id="55c88-584">Type</span></span>| <span data-ttu-id="55c88-585">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="55c88-585">Maximum size</span></span> | <span data-ttu-id="55c88-586">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="55c88-586">Required</span></span> | <span data-ttu-id="55c88-587">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="55c88-587">Description</span></span>|
|---|---|---|---|---|
|`type`|<span data-ttu-id="55c88-588">string</span><span class="sxs-lookup"><span data-stu-id="55c88-588">string</span></span>|<span data-ttu-id="55c88-589">32 Zeichen</span><span class="sxs-lookup"><span data-stu-id="55c88-589">32 characters</span></span>|<span data-ttu-id="55c88-590">✔</span><span class="sxs-lookup"><span data-stu-id="55c88-590">✔</span></span>|<span data-ttu-id="55c88-591">Der Benachrichtigungstyp.</span><span class="sxs-lookup"><span data-stu-id="55c88-591">The notification type.</span></span> <span data-ttu-id="55c88-592">*Siehe unten*.</span><span class="sxs-lookup"><span data-stu-id="55c88-592">*See below*.</span></span>|
|`description`|<span data-ttu-id="55c88-593">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="55c88-593">string</span></span>|<span data-ttu-id="55c88-594">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="55c88-594">128 characters</span></span>|<span data-ttu-id="55c88-595">✔</span><span class="sxs-lookup"><span data-stu-id="55c88-595">✔</span></span>|<span data-ttu-id="55c88-596">Eine kurze Beschreibung der Benachrichtigung.</span><span class="sxs-lookup"><span data-stu-id="55c88-596">A brief description of the notification.</span></span> <span data-ttu-id="55c88-597">*Siehe unten*.</span><span class="sxs-lookup"><span data-stu-id="55c88-597">*See below*.</span></span>|
|`templateText`|<span data-ttu-id="55c88-598">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="55c88-598">string</span></span>|<span data-ttu-id="55c88-599">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="55c88-599">128 characters</span></span>|<span data-ttu-id="55c88-600">✔</span><span class="sxs-lookup"><span data-stu-id="55c88-600">✔</span></span>|<span data-ttu-id="55c88-601">Ex: "{actor}- erstellter Task {taskId} für Sie"</span><span class="sxs-lookup"><span data-stu-id="55c88-601">Ex: "{actor} created task {taskId} for you"</span></span>|

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
