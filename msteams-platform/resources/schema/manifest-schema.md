---
title: Manifestschemareferenz
description: Beschreibt das Manifestschema für Microsoft Teams
ms.topic: reference
ms.author: lajanuar
localization_priority: Normal
keywords: Teams-Manifestschema
ms.openlocfilehash: 984a5de5b2c8e24f79269e62c3a7fd422ecce63f
ms.sourcegitcommit: 25c9ad27f99682caaa7347840578b118c63b8f69
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/30/2021
ms.locfileid: "52101807"
---
# <a name="reference-manifest-schema-for-microsoft-teams"></a><span data-ttu-id="14013-104">Referenz: Manifestschema für Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="14013-104">Reference: Manifest schema for Microsoft Teams</span></span>

<span data-ttu-id="14013-105">Das Teams beschreibt, wie die App in das Microsoft Teams integriert wird.</span><span class="sxs-lookup"><span data-stu-id="14013-105">The Teams manifest describes how the app integrates into the Microsoft Teams product.</span></span> <span data-ttu-id="14013-106">Ihr Manifest muss dem schema entsprechen, das unter gehostet [`https://developer.microsoft.com/json-schemas/teams/v1.9/MicrosoftTeams.schema.json`]( https://developer.microsoft.com/json-schemas/teams/v1.9/MicrosoftTeams.schema.json) wird.</span><span class="sxs-lookup"><span data-stu-id="14013-106">Your manifest must conform to the schema hosted at [`https://developer.microsoft.com/json-schemas/teams/v1.9/MicrosoftTeams.schema.json`]( https://developer.microsoft.com/json-schemas/teams/v1.9/MicrosoftTeams.schema.json).</span></span> <span data-ttu-id="14013-107">Frühere Versionen 1.0-1.4 werden ebenfalls unterstützt (unter Verwendung von "v1.x" in der URL).</span><span class="sxs-lookup"><span data-stu-id="14013-107">Previous versions 1.0-1.4 are also supported (using "v1.x" in the URL).</span></span>

<span data-ttu-id="14013-108">Das folgende Schemabeispiel zeigt alle Erweiterbarkeitsoptionen.</span><span class="sxs-lookup"><span data-stu-id="14013-108">The following schema sample shows all extensibility options.</span></span>

## <a name="sample-full-manifest"></a><span data-ttu-id="14013-109">Beispiel für vollständiges Manifest</span><span class="sxs-lookup"><span data-stu-id="14013-109">Sample full manifest</span></span>

```json
{
  "$schema": "https://developer.microsoft.com/json-schemas/teams/v1.9/MicrosoftTeams.schema.json",
  "manifestVersion": "1.9",
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
  }
}
```

<span data-ttu-id="14013-110">Das Schema definiert die folgenden Eigenschaften:</span><span class="sxs-lookup"><span data-stu-id="14013-110">The schema defines the following properties:</span></span>

## <a name="schema"></a><span data-ttu-id="14013-111">$schema</span><span class="sxs-lookup"><span data-stu-id="14013-111">$schema</span></span>

<span data-ttu-id="14013-112">Optional, aber empfohlen – Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="14013-112">Optional, but recommended — string</span></span>

<span data-ttu-id="14013-113">Die https://-URL, die auf das JSON-Schema für das Manifest verweist.</span><span class="sxs-lookup"><span data-stu-id="14013-113">The https:// URL referencing the JSON Schema for the manifest.</span></span>

## <a name="manifestversion"></a><span data-ttu-id="14013-114">manifestVersion</span><span class="sxs-lookup"><span data-stu-id="14013-114">manifestVersion</span></span>

<span data-ttu-id="14013-115">**Erforderlich** – Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="14013-115">**Required** — string</span></span>

<span data-ttu-id="14013-116">Die Version des Manifestschemas, das dieses Manifest verwendet.</span><span class="sxs-lookup"><span data-stu-id="14013-116">The version of manifest schema this manifest is using.</span></span> <span data-ttu-id="14013-117">Er muss 1,9 sein.</span><span class="sxs-lookup"><span data-stu-id="14013-117">It must be 1.9.</span></span>

## <a name="version"></a><span data-ttu-id="14013-118">Version</span><span class="sxs-lookup"><span data-stu-id="14013-118">version</span></span>

<span data-ttu-id="14013-119">**Erforderlich** – Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="14013-119">**Required** — string</span></span>

<span data-ttu-id="14013-120">Die Version einer bestimmten App.</span><span class="sxs-lookup"><span data-stu-id="14013-120">The version of a specific app.</span></span> <span data-ttu-id="14013-121">Wenn Sie etwas in Ihrem Manifest aktualisieren, muss auch die Version erhöht werden.</span><span class="sxs-lookup"><span data-stu-id="14013-121">If you update something in your manifest, the version must be incremented too.</span></span> <span data-ttu-id="14013-122">Auf diese Weise wird das vorhandene Manifest überschrieben, wenn das neue Manifest installiert wird, und der Benutzer erhält die neue Funktionalität.</span><span class="sxs-lookup"><span data-stu-id="14013-122">This way, when the new manifest is installed, it overwrites the existing one and the user receives the new functionality.</span></span> <span data-ttu-id="14013-123">Wenn diese App an den Store übermittelt wurde, muss das neue Manifest erneut übermittelt und erneut überprüft werden.</span><span class="sxs-lookup"><span data-stu-id="14013-123">If this app was submitted to the store, the new manifest must be re-submitted and re-validated.</span></span> <span data-ttu-id="14013-124">Die App-Benutzer erhalten das neue aktualisierte Manifest automatisch innerhalb weniger Stunden nach der Genehmigung des Manifests.</span><span class="sxs-lookup"><span data-stu-id="14013-124">The app users receive the new updated manifest automatically within few hours after the manifest is approved.</span></span>

<span data-ttu-id="14013-125">Wenn sich die App-Anforderungen für Berechtigungen ändern, werden die Benutzer aufgefordert, ein Upgrade zu starten und der App erneut zu zustimmen.</span><span class="sxs-lookup"><span data-stu-id="14013-125">If the app requests for permissions change, the users are prompted to upgrade and re-consent to the app.</span></span>

<span data-ttu-id="14013-126">Diese Versionszeichenfolge muss dem [semver-Standard](http://semver.org/) (MAJOR. MINOR. PATCH).</span><span class="sxs-lookup"><span data-stu-id="14013-126">This version string must follow the [semver](http://semver.org/) standard (MAJOR.MINOR.PATCH).</span></span>

## <a name="id"></a><span data-ttu-id="14013-127">id</span><span class="sxs-lookup"><span data-stu-id="14013-127">id</span></span>

<span data-ttu-id="14013-128">**Erforderlich** – Microsoft-App-ID</span><span class="sxs-lookup"><span data-stu-id="14013-128">**Required** — Microsoft app ID</span></span>

<span data-ttu-id="14013-129">Die ID ist ein eindeutiger von Microsoft generierter Bezeichner für die App.</span><span class="sxs-lookup"><span data-stu-id="14013-129">The ID is a unique Microsoft-generated identifier for the app.</span></span> <span data-ttu-id="14013-130">Sie verfügen über eine ID, wenn Ihr Bot über das Microsoft Bot Framework registriert ist oder sich die Web-App Ihrer Registerkarte bereits bei Microsoft angemeldet hat.</span><span class="sxs-lookup"><span data-stu-id="14013-130">You have an ID if your bot is registered through the Microsoft Bot Framework or your tab's web app already signs in with Microsoft.</span></span> <span data-ttu-id="14013-131">Sie müssen hier die ID eingeben.</span><span class="sxs-lookup"><span data-stu-id="14013-131">You must enter the ID here.</span></span> <span data-ttu-id="14013-132">Andernfalls müssen Sie eine neue ID im [Microsoft Application Registration Portal generieren.](https://aka.ms/appregistrations)</span><span class="sxs-lookup"><span data-stu-id="14013-132">Otherwise, you must generate a new ID at the [Microsoft Application Registration Portal](https://aka.ms/appregistrations).</span></span> <span data-ttu-id="14013-133">Verwenden Sie dieselbe ID, wenn Sie einen Bot hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="14013-133">Use the same ID if you add a bot.</span></span>

> [!NOTE]
> <span data-ttu-id="14013-134">Wenn Sie ein Update an Ihre vorhandene App in AppSource übermitteln, darf die ID in Ihrem Manifest nicht geändert werden.</span><span class="sxs-lookup"><span data-stu-id="14013-134">If you are submitting an update to your existing app in AppSource, the ID in your manifest must not be modified.</span></span>

## <a name="developer"></a><span data-ttu-id="14013-135">developer</span><span class="sxs-lookup"><span data-stu-id="14013-135">developer</span></span>

<span data-ttu-id="14013-136">**Erforderlich** – Objekt</span><span class="sxs-lookup"><span data-stu-id="14013-136">**Required** — object</span></span>

<span data-ttu-id="14013-137">Gibt Informationen zu Ihrem Unternehmen an.</span><span class="sxs-lookup"><span data-stu-id="14013-137">Specifies information about your company.</span></span> <span data-ttu-id="14013-138">Für Apps, die an den Teams übermittelt werden, müssen diese Werte mit den Informationen in Ihrem Storeeintrag übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="14013-138">For apps submitted to the Teams store, these values must match the information in your store listing.</span></span> <span data-ttu-id="14013-139">Weitere Informationen finden Sie unter [Teams Store Publishing Guidelines](~/concepts/deploy-and-publish/appsource/publish.md).</span><span class="sxs-lookup"><span data-stu-id="14013-139">For more information, see the [Teams store publishing guidelines](~/concepts/deploy-and-publish/appsource/publish.md).</span></span>

|<span data-ttu-id="14013-140">Name</span><span class="sxs-lookup"><span data-stu-id="14013-140">Name</span></span>| <span data-ttu-id="14013-141">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="14013-141">Maximum size</span></span> | <span data-ttu-id="14013-142">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="14013-142">Required</span></span> | <span data-ttu-id="14013-143">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="14013-143">Description</span></span>|
|---|---|---|---|
|`name`|<span data-ttu-id="14013-144">32 Zeichen</span><span class="sxs-lookup"><span data-stu-id="14013-144">32 characters</span></span>|<span data-ttu-id="14013-145">✔</span><span class="sxs-lookup"><span data-stu-id="14013-145">✔</span></span>|<span data-ttu-id="14013-146">Der Anzeigename für den Entwickler.</span><span class="sxs-lookup"><span data-stu-id="14013-146">The display name for the developer.</span></span>|
|`websiteUrl`|<span data-ttu-id="14013-147">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="14013-147">2048 characters</span></span>|<span data-ttu-id="14013-148">✔</span><span class="sxs-lookup"><span data-stu-id="14013-148">✔</span></span>|<span data-ttu-id="14013-149">Die https://-URL zur Website des Entwicklers.</span><span class="sxs-lookup"><span data-stu-id="14013-149">The https:// URL to the developer's website.</span></span> <span data-ttu-id="14013-150">Dieser Link muss Benutzer zu Ihrer unternehmens- oder produktspezifischen Angebotsseite gelangen.</span><span class="sxs-lookup"><span data-stu-id="14013-150">This link must take users to your company or product-specific landing page.</span></span>|
|`privacyUrl`|<span data-ttu-id="14013-151">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="14013-151">2048 characters</span></span>|<span data-ttu-id="14013-152">✔</span><span class="sxs-lookup"><span data-stu-id="14013-152">✔</span></span>|<span data-ttu-id="14013-153">Die https:// url to the developer's privacy policy.</span><span class="sxs-lookup"><span data-stu-id="14013-153">The https:// URL to the developer's privacy policy.</span></span>|
|`termsOfUseUrl`|<span data-ttu-id="14013-154">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="14013-154">2048 characters</span></span>|<span data-ttu-id="14013-155">✔</span><span class="sxs-lookup"><span data-stu-id="14013-155">✔</span></span>|<span data-ttu-id="14013-156">Die https:// URL zu den Nutzungsbedingungen des Entwicklers.</span><span class="sxs-lookup"><span data-stu-id="14013-156">The https:// URL to the developer's terms of use.</span></span>|
|`mpnId`|<span data-ttu-id="14013-157">10 Zeichen</span><span class="sxs-lookup"><span data-stu-id="14013-157">10 characters</span></span>| |<span data-ttu-id="14013-158">**Optional** Die Microsoft Partner Network ID, die die Partnerorganisation identifiziert, die die App erstellt.</span><span class="sxs-lookup"><span data-stu-id="14013-158">**Optional** The Microsoft Partner Network ID that identifies the partner organization building the app.</span></span>|

## <a name="name"></a><span data-ttu-id="14013-159">name</span><span class="sxs-lookup"><span data-stu-id="14013-159">name</span></span>

<span data-ttu-id="14013-160">**Erforderlich** – Objekt</span><span class="sxs-lookup"><span data-stu-id="14013-160">**Required** — object</span></span>

<span data-ttu-id="14013-161">Der Name Ihrer App-Erfahrung, der Benutzern in der Teams angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="14013-161">The name of your app experience, displayed to users in the Teams experience.</span></span> <span data-ttu-id="14013-162">Für apps submitted to AppSource, these values must match the information in your AppSource entry.</span><span class="sxs-lookup"><span data-stu-id="14013-162">For apps submitted to AppSource, these values must match the information in your AppSource entry.</span></span> <span data-ttu-id="14013-163">Die Werte von `short` und `full` müssen unterschiedlich sein.</span><span class="sxs-lookup"><span data-stu-id="14013-163">The values of `short` and `full` must be different.</span></span>

|<span data-ttu-id="14013-164">Name</span><span class="sxs-lookup"><span data-stu-id="14013-164">Name</span></span>| <span data-ttu-id="14013-165">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="14013-165">Maximum size</span></span> | <span data-ttu-id="14013-166">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="14013-166">Required</span></span> | <span data-ttu-id="14013-167">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="14013-167">Description</span></span>|
|---|---|---|---|
|`short`|<span data-ttu-id="14013-168">30 Zeichen</span><span class="sxs-lookup"><span data-stu-id="14013-168">30 characters</span></span>|<span data-ttu-id="14013-169">✔</span><span class="sxs-lookup"><span data-stu-id="14013-169">✔</span></span>|<span data-ttu-id="14013-170">Der kurze Anzeigename für die App.</span><span class="sxs-lookup"><span data-stu-id="14013-170">The short display name for the app.</span></span>|
|`full`|<span data-ttu-id="14013-171">100 Zeichen</span><span class="sxs-lookup"><span data-stu-id="14013-171">100 characters</span></span>||<span data-ttu-id="14013-172">Der vollständige Name der App, der verwendet wird, wenn der vollständige Name der App 30 Zeichen überschreitet.</span><span class="sxs-lookup"><span data-stu-id="14013-172">The full name of the app, used if the full app name exceeds 30 characters.</span></span>|

## <a name="description"></a><span data-ttu-id="14013-173">description</span><span class="sxs-lookup"><span data-stu-id="14013-173">description</span></span>

<span data-ttu-id="14013-174">**Erforderlich** – Objekt</span><span class="sxs-lookup"><span data-stu-id="14013-174">**Required** — object</span></span>

<span data-ttu-id="14013-175">Beschreibt Ihre App für Benutzer.</span><span class="sxs-lookup"><span data-stu-id="14013-175">Describes your app to users.</span></span> <span data-ttu-id="14013-176">Für apps submitted to AppSource, these values must match the information in your AppSource entry.</span><span class="sxs-lookup"><span data-stu-id="14013-176">For apps submitted to AppSource, these values must match the information in your AppSource entry.</span></span>

<span data-ttu-id="14013-177">Stellen Sie sicher, dass Ihre Beschreibung Ihre Erfahrung genau beschreibt und Informationen enthält, mit deren Hilfe potenzielle Kunden besser verstehen können, was Ihre Erfahrung bedeutet.</span><span class="sxs-lookup"><span data-stu-id="14013-177">Ensure that your description accurately describes your experience and provides information to help potential customers understand what your experience does.</span></span> <span data-ttu-id="14013-178">Sie müssen in der vollständigen Beschreibung notieren, ob ein externes Konto für die Verwendung erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="14013-178">You must note in the full description, if an external account is required for use.</span></span> <span data-ttu-id="14013-179">Die Werte von `short` und `full` müssen unterschiedlich sein.</span><span class="sxs-lookup"><span data-stu-id="14013-179">The values of `short` and `full` must be different.</span></span> <span data-ttu-id="14013-180">Ihre kurze Beschreibung darf nicht innerhalb der langen Beschreibung wiederholt werden und darf keinen anderen App-Namen enthalten.</span><span class="sxs-lookup"><span data-stu-id="14013-180">Your short description must not be repeated within the long description and must not include any other app name.</span></span>

|<span data-ttu-id="14013-181">Name</span><span class="sxs-lookup"><span data-stu-id="14013-181">Name</span></span>| <span data-ttu-id="14013-182">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="14013-182">Maximum size</span></span> | <span data-ttu-id="14013-183">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="14013-183">Required</span></span> | <span data-ttu-id="14013-184">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="14013-184">Description</span></span>|
|---|---|---|---|
|`short`|<span data-ttu-id="14013-185">80 Zeichen</span><span class="sxs-lookup"><span data-stu-id="14013-185">80 characters</span></span>|<span data-ttu-id="14013-186">✔</span><span class="sxs-lookup"><span data-stu-id="14013-186">✔</span></span>|<span data-ttu-id="14013-187">Eine kurze Beschreibung Ihrer App-Erfahrung, die bei begrenztem Speicherplatz verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="14013-187">A short description of your app experience, used when space is limited.</span></span>|
|`full`|<span data-ttu-id="14013-188">4000 Zeichen</span><span class="sxs-lookup"><span data-stu-id="14013-188">4000 characters</span></span>|<span data-ttu-id="14013-189">✔</span><span class="sxs-lookup"><span data-stu-id="14013-189">✔</span></span>|<span data-ttu-id="14013-190">Die vollständige Beschreibung Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="14013-190">The full description of your app.</span></span>|

## <a name="packagename"></a><span data-ttu-id="14013-191">packageName</span><span class="sxs-lookup"><span data-stu-id="14013-191">packageName</span></span>

<span data-ttu-id="14013-192">**Optional –** Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="14013-192">**Optional** — string</span></span>

<span data-ttu-id="14013-193">Ein eindeutiger Bezeichner für die App in umgekehrter Domänen-Notation; z. B. com.example.myapp.</span><span class="sxs-lookup"><span data-stu-id="14013-193">A unique identifier for the app in reverse domain notation; for example, com.example.myapp.</span></span> <span data-ttu-id="14013-194">Maximale Länge: 64 Zeichen.</span><span class="sxs-lookup"><span data-stu-id="14013-194">Maximum length: 64 characters.</span></span>

## <a name="localizationinfo"></a><span data-ttu-id="14013-195">localizationInfo</span><span class="sxs-lookup"><span data-stu-id="14013-195">localizationInfo</span></span>

<span data-ttu-id="14013-196">**Optional** – -Objekt</span><span class="sxs-lookup"><span data-stu-id="14013-196">**Optional** — object</span></span>

<span data-ttu-id="14013-197">Ermöglicht die Angabe einer Standardsprache sowie Zeiger auf zusätzliche Sprachdateien.</span><span class="sxs-lookup"><span data-stu-id="14013-197">Allows the specification of a default language, as well as pointers to additional language files.</span></span> <span data-ttu-id="14013-198">Weitere [Informationen finden Sie unter Lokalisierung](~/concepts/build-and-test/apps-localization.md).</span><span class="sxs-lookup"><span data-stu-id="14013-198">See [localization](~/concepts/build-and-test/apps-localization.md).</span></span>

|<span data-ttu-id="14013-199">Name</span><span class="sxs-lookup"><span data-stu-id="14013-199">Name</span></span>| <span data-ttu-id="14013-200">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="14013-200">Maximum size</span></span> | <span data-ttu-id="14013-201">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="14013-201">Required</span></span> | <span data-ttu-id="14013-202">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="14013-202">Description</span></span>|
|---|---|---|---|
|`defaultLanguageTag`||<span data-ttu-id="14013-203">✔</span><span class="sxs-lookup"><span data-stu-id="14013-203">✔</span></span>|<span data-ttu-id="14013-204">Das Sprachtag der Zeichenfolgen in dieser Manifestdatei auf oberster Ebene.</span><span class="sxs-lookup"><span data-stu-id="14013-204">The language tag of the strings in this top level manifest file.</span></span>|

### <a name="localizationinfoadditionallanguages"></a><span data-ttu-id="14013-205">localizationInfo.additionalLanguages</span><span class="sxs-lookup"><span data-stu-id="14013-205">localizationInfo.additionalLanguages</span></span>

<span data-ttu-id="14013-206">Ein Array von Objekten, die zusätzliche Sprachübersetzungen angeben.</span><span class="sxs-lookup"><span data-stu-id="14013-206">An array of objects specifying additional language translations.</span></span>

|<span data-ttu-id="14013-207">Name</span><span class="sxs-lookup"><span data-stu-id="14013-207">Name</span></span>| <span data-ttu-id="14013-208">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="14013-208">Maximum size</span></span> | <span data-ttu-id="14013-209">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="14013-209">Required</span></span> | <span data-ttu-id="14013-210">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="14013-210">Description</span></span>|
|---|---|---|---|
|`languageTag`||<span data-ttu-id="14013-211">✔</span><span class="sxs-lookup"><span data-stu-id="14013-211">✔</span></span>|<span data-ttu-id="14013-212">Das Sprachtag der Zeichenfolgen in der bereitgestellten Datei.</span><span class="sxs-lookup"><span data-stu-id="14013-212">The language tag of the strings in the provided file.</span></span>|
|`file`||<span data-ttu-id="14013-213">✔</span><span class="sxs-lookup"><span data-stu-id="14013-213">✔</span></span>|<span data-ttu-id="14013-214">Ein relativer Dateipfad zu einer .json-Datei, die die übersetzten Zeichenfolgen enthält.</span><span class="sxs-lookup"><span data-stu-id="14013-214">A relative file path to a the .json file containing the translated strings.</span></span>|

## <a name="icons"></a><span data-ttu-id="14013-215">Symbole</span><span class="sxs-lookup"><span data-stu-id="14013-215">icons</span></span>

<span data-ttu-id="14013-216">**Erforderlich** – Objekt</span><span class="sxs-lookup"><span data-stu-id="14013-216">**Required** — object</span></span>

<span data-ttu-id="14013-217">Symbole, die innerhalb der Teams werden.</span><span class="sxs-lookup"><span data-stu-id="14013-217">Icons used within the Teams app.</span></span> <span data-ttu-id="14013-218">Die Symboldateien müssen als Teil des Uploadpakets enthalten sein.</span><span class="sxs-lookup"><span data-stu-id="14013-218">The icon files must be included as part of the upload package.</span></span> <span data-ttu-id="14013-219">Weitere Informationen finden Sie unter [Symbole.](../../concepts/build-and-test/apps-package.md#app-icons)</span><span class="sxs-lookup"><span data-stu-id="14013-219">See [Icons](../../concepts/build-and-test/apps-package.md#app-icons) for more information.</span></span>

|<span data-ttu-id="14013-220">Name</span><span class="sxs-lookup"><span data-stu-id="14013-220">Name</span></span>| <span data-ttu-id="14013-221">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="14013-221">Maximum size</span></span> | <span data-ttu-id="14013-222">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="14013-222">Required</span></span> | <span data-ttu-id="14013-223">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="14013-223">Description</span></span>|
|---|---|---|---|
|`outline`|<span data-ttu-id="14013-224">32 x 32 Pixel</span><span class="sxs-lookup"><span data-stu-id="14013-224">32 x 32 pixels</span></span>|<span data-ttu-id="14013-225">✔</span><span class="sxs-lookup"><span data-stu-id="14013-225">✔</span></span>|<span data-ttu-id="14013-226">Ein relativer Dateipfad zu einem transparenten 32 x 32 PNG-Gliederungssymbol.</span><span class="sxs-lookup"><span data-stu-id="14013-226">A relative file path to a transparent 32x32 PNG outline icon.</span></span>|
|`color`|<span data-ttu-id="14013-227">192 x 192 Pixel</span><span class="sxs-lookup"><span data-stu-id="14013-227">192 x 192 pixels</span></span>|<span data-ttu-id="14013-228">✔</span><span class="sxs-lookup"><span data-stu-id="14013-228">✔</span></span>|<span data-ttu-id="14013-229">Ein relativer Dateipfad zu einem vollfarbigen 192 x 192-PNG-Symbol.</span><span class="sxs-lookup"><span data-stu-id="14013-229">A relative file path to a full color 192x192 PNG icon.</span></span>|

## <a name="accentcolor"></a><span data-ttu-id="14013-230">accentColor</span><span class="sxs-lookup"><span data-stu-id="14013-230">accentColor</span></span>

<span data-ttu-id="14013-231">**Optional** – HTML-Hex-Farbcode</span><span class="sxs-lookup"><span data-stu-id="14013-231">**Optional** — HTML Hex color code</span></span>

<span data-ttu-id="14013-232">Eine Farbe, die in Verbindung mit und als Hintergrund für Ihre Gliederungssymbole verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="14013-232">A color to use in conjunction with and as a background for your outline icons.</span></span>

<span data-ttu-id="14013-233">Der Wert muss ein gültiger #A0 sein, der mit "#" beginnt, z. B. `#4464ee` .</span><span class="sxs-lookup"><span data-stu-id="14013-233">The value must be a valid HTML color code starting with '#', for example `#4464ee`.</span></span>

## <a name="configurabletabs"></a><span data-ttu-id="14013-234">configurableTabs</span><span class="sxs-lookup"><span data-stu-id="14013-234">configurableTabs</span></span>

<span data-ttu-id="14013-235">**Optional** – Array</span><span class="sxs-lookup"><span data-stu-id="14013-235">**Optional** — array</span></span>

<span data-ttu-id="14013-236">Wird verwendet, wenn Ihre App über eine Registerkartenerfahrung im Teamkanal verfügt, die eine zusätzliche Konfiguration erfordert, bevor sie hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="14013-236">Used when your app experience has a team channel tab experience that requires extra configuration before it is added.</span></span> <span data-ttu-id="14013-237">Konfigurierbare Registerkarten werden nur im Bereich "Teams" unterstützt, und Sie können dieselben Registerkarten mehrmals konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="14013-237">Configurable tabs are supported only in the teams scope and you can configure the same tabs multiple times.</span></span> <span data-ttu-id="14013-238">Sie können sie jedoch nur einmal im Manifest definieren.</span><span class="sxs-lookup"><span data-stu-id="14013-238">However, you can define it in the manifest only once.</span></span>

|<span data-ttu-id="14013-239">Name</span><span class="sxs-lookup"><span data-stu-id="14013-239">Name</span></span>| <span data-ttu-id="14013-240">Typ</span><span class="sxs-lookup"><span data-stu-id="14013-240">Type</span></span>| <span data-ttu-id="14013-241">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="14013-241">Maximum size</span></span> | <span data-ttu-id="14013-242">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="14013-242">Required</span></span> | <span data-ttu-id="14013-243">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="14013-243">Description</span></span>|
|---|---|---|---|---|
|`configurationUrl`|<span data-ttu-id="14013-244">string</span><span class="sxs-lookup"><span data-stu-id="14013-244">string</span></span>|<span data-ttu-id="14013-245">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="14013-245">2048 characters</span></span>|<span data-ttu-id="14013-246">✔</span><span class="sxs-lookup"><span data-stu-id="14013-246">✔</span></span>|<span data-ttu-id="14013-247">Die https:// URL, die beim Konfigurieren der Registerkarte verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="14013-247">The https:// URL to use when configuring the tab.</span></span>|
|`scopes`|<span data-ttu-id="14013-248">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="14013-248">array of enums</span></span>|<span data-ttu-id="14013-249">1</span><span class="sxs-lookup"><span data-stu-id="14013-249">1</span></span>|<span data-ttu-id="14013-250">✔</span><span class="sxs-lookup"><span data-stu-id="14013-250">✔</span></span>|<span data-ttu-id="14013-251">Derzeit unterstützen konfigurierbare Registerkarten nur die `team` Bereiche `groupchat` und.</span><span class="sxs-lookup"><span data-stu-id="14013-251">Currently, configurable tabs support only the `team` and `groupchat` scopes.</span></span> |
|`canUpdateConfiguration`|<span data-ttu-id="14013-252">boolean</span><span class="sxs-lookup"><span data-stu-id="14013-252">boolean</span></span>|||<span data-ttu-id="14013-253">Ein Wert, der angibt, ob eine Instanz der Registerkartenkonfiguration vom Benutzer nach der Erstellung aktualisiert werden kann.</span><span class="sxs-lookup"><span data-stu-id="14013-253">A value indicating whether an instance of the tab's configuration can be updated by the user after creation.</span></span> <span data-ttu-id="14013-254">Standard: **true**.</span><span class="sxs-lookup"><span data-stu-id="14013-254">Default: **true**.</span></span>|
|`context` |<span data-ttu-id="14013-255">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="14013-255">array of enums</span></span>|<span data-ttu-id="14013-256">6 </span><span class="sxs-lookup"><span data-stu-id="14013-256">6</span></span>||<span data-ttu-id="14013-257">Der Satz von `contextItem` Bereich, in [dem eine Registerkarte unterstützt wird.](../../tabs/how-to/access-teams-context.md)</span><span class="sxs-lookup"><span data-stu-id="14013-257">The set of `contextItem` scopes where a [tab is supported](../../tabs/how-to/access-teams-context.md).</span></span> <span data-ttu-id="14013-258">Standard: **[channelTab, privateChatTab, meetingChatTab, meetingDetailsTab]**.</span><span class="sxs-lookup"><span data-stu-id="14013-258">Default: **[channelTab, privateChatTab, meetingChatTab, meetingDetailsTab]**.</span></span>|
|`sharePointPreviewImage`|<span data-ttu-id="14013-259">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="14013-259">string</span></span>|<span data-ttu-id="14013-260">2048</span><span class="sxs-lookup"><span data-stu-id="14013-260">2048</span></span>||<span data-ttu-id="14013-261">Ein relativer Dateipfad zu einem Registerkartenvorschaubild zur Verwendung in SharePoint.</span><span class="sxs-lookup"><span data-stu-id="14013-261">A relative file path to a tab preview image for use in SharePoint.</span></span> <span data-ttu-id="14013-262">Größe 1024 x 768.</span><span class="sxs-lookup"><span data-stu-id="14013-262">Size 1024x768.</span></span> |
|`supportedSharePointHosts`|<span data-ttu-id="14013-263">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="14013-263">array of enums</span></span>|<span data-ttu-id="14013-264">1</span><span class="sxs-lookup"><span data-stu-id="14013-264">1</span></span>||<span data-ttu-id="14013-265">Definiert, wie Ihre Registerkarte in der SharePoint.</span><span class="sxs-lookup"><span data-stu-id="14013-265">Defines how your tab is made available in SharePoint.</span></span> <span data-ttu-id="14013-266">Optionen sind `sharePointFullPage` und `sharePointWebPart`</span><span class="sxs-lookup"><span data-stu-id="14013-266">Options are `sharePointFullPage` and `sharePointWebPart`</span></span> |

## <a name="statictabs"></a><span data-ttu-id="14013-267">staticTabs</span><span class="sxs-lookup"><span data-stu-id="14013-267">staticTabs</span></span>

<span data-ttu-id="14013-268">**Optional** – Array</span><span class="sxs-lookup"><span data-stu-id="14013-268">**Optional** — array</span></span>

<span data-ttu-id="14013-269">Definiert eine Reihe von Registerkarten, die standardmäßig angeheftet werden können, ohne dass der Benutzer sie manuell hinzufügungen muss.</span><span class="sxs-lookup"><span data-stu-id="14013-269">Defines a set of tabs that can be "pinned" by default, without the user adding them manually.</span></span> <span data-ttu-id="14013-270">Statische Registerkarten, die im Bereich deklariert sind, werden immer an die persönliche Be benutzererfahrung `personal` der App angeheftet.</span><span class="sxs-lookup"><span data-stu-id="14013-270">Static tabs declared in `personal` scope are always pinned to the app's personal experience.</span></span> <span data-ttu-id="14013-271">Statische Registerkarten, die im Bereich `team` deklariert sind, werden derzeit nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="14013-271">Static tabs declared in the `team` scope are currently not supported.</span></span>

<span data-ttu-id="14013-272">Dieses Element ist ein Array (maximal 16 Elemente) mit allen Elementen des Typs `object` .</span><span class="sxs-lookup"><span data-stu-id="14013-272">This item is an array (maximum of 16 elements) with all elements of the type `object`.</span></span> <span data-ttu-id="14013-273">Dieser Block ist nur für Lösungen erforderlich, die eine statische Registerkartenlösung bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="14013-273">This block is required only for solutions that provide a static tab solution.</span></span>

|<span data-ttu-id="14013-274">Name</span><span class="sxs-lookup"><span data-stu-id="14013-274">Name</span></span>| <span data-ttu-id="14013-275">Typ</span><span class="sxs-lookup"><span data-stu-id="14013-275">Type</span></span>| <span data-ttu-id="14013-276">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="14013-276">Maximum size</span></span> | <span data-ttu-id="14013-277">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="14013-277">Required</span></span> | <span data-ttu-id="14013-278">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="14013-278">Description</span></span>|
|---|---|---|---|---|
|`entityId`|<span data-ttu-id="14013-279">string</span><span class="sxs-lookup"><span data-stu-id="14013-279">string</span></span>|<span data-ttu-id="14013-280">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="14013-280">64 characters</span></span>|<span data-ttu-id="14013-281">✔</span><span class="sxs-lookup"><span data-stu-id="14013-281">✔</span></span>|<span data-ttu-id="14013-282">Ein eindeutiger Bezeichner für die Entität, die auf der Registerkarte angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="14013-282">A unique identifier for the entity that the tab displays.</span></span>|
|`name`|<span data-ttu-id="14013-283">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="14013-283">string</span></span>|<span data-ttu-id="14013-284">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="14013-284">128 characters</span></span>|<span data-ttu-id="14013-285">✔</span><span class="sxs-lookup"><span data-stu-id="14013-285">✔</span></span>|<span data-ttu-id="14013-286">Der Anzeigename der Registerkarte in der Kanalschnittstelle.</span><span class="sxs-lookup"><span data-stu-id="14013-286">The display name of the tab in the channel interface.</span></span>|
|`contentUrl`|<span data-ttu-id="14013-287">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="14013-287">string</span></span>||<span data-ttu-id="14013-288">✔</span><span class="sxs-lookup"><span data-stu-id="14013-288">✔</span></span>|<span data-ttu-id="14013-289">Die https://-URL, die auf die Entitätsbenutzeroberfläche verweist, die im Zeichenbereich Teams werden soll.</span><span class="sxs-lookup"><span data-stu-id="14013-289">The https:// URL that points to the entity UI to be displayed in the Teams canvas.</span></span>|
|`websiteUrl`|<span data-ttu-id="14013-290">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="14013-290">string</span></span>|||<span data-ttu-id="14013-291">Die https:// URL, auf die verweisen soll, wenn sich ein Benutzer für die Anzeige in einem Browser entscheidet.</span><span class="sxs-lookup"><span data-stu-id="14013-291">The https:// URL to point to if a user opts to view in a browser.</span></span>|
|`searchUrl`|<span data-ttu-id="14013-292">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="14013-292">string</span></span>|||<span data-ttu-id="14013-293">Die https:// URL, auf die für die Suchabfragen eines Benutzers verweisen soll.</span><span class="sxs-lookup"><span data-stu-id="14013-293">The https:// URL to point to for a user's search queries.</span></span>|
|`scopes`|<span data-ttu-id="14013-294">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="14013-294">array of enums</span></span>|<span data-ttu-id="14013-295">1</span><span class="sxs-lookup"><span data-stu-id="14013-295">1</span></span>|<span data-ttu-id="14013-296">✔</span><span class="sxs-lookup"><span data-stu-id="14013-296">✔</span></span>|<span data-ttu-id="14013-297">Derzeit unterstützen statische Registerkarten nur den Bereich, d. h., er kann nur als Teil der `personal` persönlichen Erfahrung bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="14013-297">Currently, static tabs support only the `personal` scope, which means it can be provisioned only as part of the personal experience.</span></span>|
|`context` | <span data-ttu-id="14013-298">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="14013-298">array of enums</span></span>| <span data-ttu-id="14013-299">2</span><span class="sxs-lookup"><span data-stu-id="14013-299">2</span></span>|| <span data-ttu-id="14013-300">Der Satz von `contextItem` Bereich, in dem eine Registerkarte unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="14013-300">The set of `contextItem` scopes where a tab is supported.</span></span>|

> [!NOTE]
>  <span data-ttu-id="14013-301">Das searchUrl-Feature ist für Drittanbieterentwickler nicht verfügbar.</span><span class="sxs-lookup"><span data-stu-id="14013-301">The searchUrl feature is not available for the third-party developers.</span></span>
> <span data-ttu-id="14013-302">Wenn Für Ihre Registerkarten kontextabhängige Informationen zum Anzeigen relevanter Inhalte oder zum Initiieren eines Authentifizierungsflusses erforderlich *sind,* finden Sie unter [Get context for your Microsoft Teams tab](../../tabs/how-to/access-teams-context.md).</span><span class="sxs-lookup"><span data-stu-id="14013-302">If your tabs require context-dependent information to display relevant content or for initiating an authentication flow, *see* [Get context for your Microsoft Teams tab](../../tabs/how-to/access-teams-context.md).</span></span>

## <a name="bots"></a><span data-ttu-id="14013-303">Bots</span><span class="sxs-lookup"><span data-stu-id="14013-303">bots</span></span>

<span data-ttu-id="14013-304">**Optional** – Array</span><span class="sxs-lookup"><span data-stu-id="14013-304">**Optional** — array</span></span>

<span data-ttu-id="14013-305">Definiert eine Botlösung zusammen mit optionalen Informationen, z. B. Standardbefehlseigenschaften.</span><span class="sxs-lookup"><span data-stu-id="14013-305">Defines a bot solution, along with optional information such as default command properties.</span></span>

<span data-ttu-id="14013-306">Das Element ist ein Array (maximal 1 Element ist derzeit nur ein Bot pro App zulässig) mit allen Elementen &mdash; des Typs `object` .</span><span class="sxs-lookup"><span data-stu-id="14013-306">The item is an array (maximum of only 1 element&mdash;currently only one bot is allowed per app) with all elements of the type `object`.</span></span> <span data-ttu-id="14013-307">Dieser Block ist nur für Lösungen erforderlich, die eine Boterfahrung bieten.</span><span class="sxs-lookup"><span data-stu-id="14013-307">This block is required only for solutions that provide a bot experience.</span></span>

|<span data-ttu-id="14013-308">Name</span><span class="sxs-lookup"><span data-stu-id="14013-308">Name</span></span>| <span data-ttu-id="14013-309">Typ</span><span class="sxs-lookup"><span data-stu-id="14013-309">Type</span></span>| <span data-ttu-id="14013-310">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="14013-310">Maximum size</span></span> | <span data-ttu-id="14013-311">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="14013-311">Required</span></span> | <span data-ttu-id="14013-312">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="14013-312">Description</span></span>|
|---|---|---|---|---|
|`botId`|<span data-ttu-id="14013-313">string</span><span class="sxs-lookup"><span data-stu-id="14013-313">string</span></span>|<span data-ttu-id="14013-314">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="14013-314">64 characters</span></span>|<span data-ttu-id="14013-315">✔</span><span class="sxs-lookup"><span data-stu-id="14013-315">✔</span></span>|<span data-ttu-id="14013-316">Die eindeutige Microsoft-App-ID für den Bot, wie bei Bot Framework registriert.</span><span class="sxs-lookup"><span data-stu-id="14013-316">The unique Microsoft app ID for the bot as registered with the Bot Framework.</span></span> <span data-ttu-id="14013-317">Dies kann mit der allgemeinen [App-ID identisch sein.](#id)</span><span class="sxs-lookup"><span data-stu-id="14013-317">This may well be the same as the overall [app ID](#id).</span></span>|
|`scopes`|<span data-ttu-id="14013-318">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="14013-318">array of enums</span></span>|<span data-ttu-id="14013-319">3</span><span class="sxs-lookup"><span data-stu-id="14013-319">3</span></span>|<span data-ttu-id="14013-320">✔</span><span class="sxs-lookup"><span data-stu-id="14013-320">✔</span></span>|<span data-ttu-id="14013-321">Gibt an, ob der Bot eine Umgebung im Kontext eines Kanals in einem `team` oder Gruppenchat (`groupchat`) ist, oder aber eine Umgebung einzig für einen bestimmten Benutzer (`personal`).</span><span class="sxs-lookup"><span data-stu-id="14013-321">Specifies whether the bot offers an experience in the context of a channel in a `team`, in a group chat (`groupchat`), or an experience scoped to an individual user alone (`personal`).</span></span> <span data-ttu-id="14013-322">Diese Optionen sind nicht exklusiv.</span><span class="sxs-lookup"><span data-stu-id="14013-322">These options are non-exclusive.</span></span>|
|`needsChannelSelector`|<span data-ttu-id="14013-323">boolean</span><span class="sxs-lookup"><span data-stu-id="14013-323">boolean</span></span>|||<span data-ttu-id="14013-324">Beschreibt, ob der Bot einen Benutzerhinweis verwendet, um den Bot einem bestimmten Kanal hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="14013-324">Describes whether or not the bot utilizes a user hint to add the bot to a specific channel.</span></span> <span data-ttu-id="14013-325">Standard: **`false`**</span><span class="sxs-lookup"><span data-stu-id="14013-325">Default: **`false`**</span></span>|
|`isNotificationOnly`|<span data-ttu-id="14013-326">boolean</span><span class="sxs-lookup"><span data-stu-id="14013-326">boolean</span></span>|||<span data-ttu-id="14013-327">Gibt an, ob ein Bot ein unidirektionaler Bot ausschließlich für Benachrichtigungen ist (im Gegensatz zu einem dialogorientierten Bot).</span><span class="sxs-lookup"><span data-stu-id="14013-327">Indicates whether a bot is a one-way, notification-only bot, as opposed to a conversational bot.</span></span> <span data-ttu-id="14013-328">Standard: **`false`**</span><span class="sxs-lookup"><span data-stu-id="14013-328">Default: **`false`**</span></span>|
|`supportsFiles`|<span data-ttu-id="14013-329">boolean</span><span class="sxs-lookup"><span data-stu-id="14013-329">boolean</span></span>|||<span data-ttu-id="14013-330">Gibt an, ob der Bot die Möglichkeit zum Hochladen/Herunterladen von Dateien in persönliche Chats unterstützt.</span><span class="sxs-lookup"><span data-stu-id="14013-330">Indicates whether the bot supports the ability to upload/download files in personal chat.</span></span> <span data-ttu-id="14013-331">Standard: **`false`**</span><span class="sxs-lookup"><span data-stu-id="14013-331">Default: **`false`**</span></span>|
|`supportsCalling`|<span data-ttu-id="14013-332">boolean</span><span class="sxs-lookup"><span data-stu-id="14013-332">boolean</span></span>|||<span data-ttu-id="14013-333">Ein Wert, der angibt, wo ein Bot Audioanrufe unterstützt.</span><span class="sxs-lookup"><span data-stu-id="14013-333">A value indicating where a bot supports audio calling.</span></span> <span data-ttu-id="14013-334">**WICHTIG**: Diese Eigenschaft ist derzeit experimentell.</span><span class="sxs-lookup"><span data-stu-id="14013-334">**IMPORTANT**: This property is currently experimental.</span></span> <span data-ttu-id="14013-335">Experimentelle Eigenschaften sind möglicherweise nicht vollständig und werden möglicherweise geändert, bevor sie vollständig verfügbar werden.</span><span class="sxs-lookup"><span data-stu-id="14013-335">Experimental properties may not be complete, and may undergo changes before becoming fully available.</span></span>  <span data-ttu-id="14013-336">Es wird nur zu Test- und Explorationszwecken bereitgestellt und darf nicht in Produktionsanwendungen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="14013-336">It is provided for testing and exploration purposes only and must not be used in production applications.</span></span> <span data-ttu-id="14013-337">Standard: **`false`**</span><span class="sxs-lookup"><span data-stu-id="14013-337">Default: **`false`**</span></span>|
|`supportsVideo`|<span data-ttu-id="14013-338">boolean</span><span class="sxs-lookup"><span data-stu-id="14013-338">boolean</span></span>|||<span data-ttu-id="14013-339">Ein Wert, der angibt, wo ein Bot Videoanrufe unterstützt.</span><span class="sxs-lookup"><span data-stu-id="14013-339">A value indicating where a bot supports video calling.</span></span> <span data-ttu-id="14013-340">**WICHTIG**: Diese Eigenschaft ist derzeit experimentell.</span><span class="sxs-lookup"><span data-stu-id="14013-340">**IMPORTANT**: This property is currently experimental.</span></span> <span data-ttu-id="14013-341">Experimentelle Eigenschaften sind möglicherweise nicht vollständig und werden möglicherweise geändert, bevor sie vollständig verfügbar werden.</span><span class="sxs-lookup"><span data-stu-id="14013-341">Experimental properties may not be complete, and may undergo changes before becoming fully available.</span></span>  <span data-ttu-id="14013-342">Es wird nur zu Test- und Explorationszwecken bereitgestellt und darf nicht in Produktionsanwendungen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="14013-342">It is provided for testing and exploration purposes only and must not be used in production applications.</span></span> <span data-ttu-id="14013-343">Standard: **`false`**</span><span class="sxs-lookup"><span data-stu-id="14013-343">Default: **`false`**</span></span>|

### <a name="botscommandlists"></a><span data-ttu-id="14013-344">bots.commandLists</span><span class="sxs-lookup"><span data-stu-id="14013-344">bots.commandLists</span></span>

<span data-ttu-id="14013-345">Eine optionale Liste von Befehlen, die Ihr Bot Benutzern empfehlen kann.</span><span class="sxs-lookup"><span data-stu-id="14013-345">An optional list of commands that your bot can recommend to users.</span></span> <span data-ttu-id="14013-346">Das Objekt ist ein Array (maximal 2 Elemente) mit allen Elementen des Typs. Sie müssen eine separate Befehlsliste für jeden Bereich definieren, den `object` Ihr Bot unterstützt.</span><span class="sxs-lookup"><span data-stu-id="14013-346">The object is an array (maximum of 2 elements) with all elements of type `object`; you must define a separate command list for each scope that your bot supports.</span></span> <span data-ttu-id="14013-347">Weitere [Informationen finden Sie unter Bot-Menüs.](~/bots/how-to/create-a-bot-commands-menu.md)</span><span class="sxs-lookup"><span data-stu-id="14013-347">See [Bot menus](~/bots/how-to/create-a-bot-commands-menu.md) for more information.</span></span>

|<span data-ttu-id="14013-348">Name</span><span class="sxs-lookup"><span data-stu-id="14013-348">Name</span></span>| <span data-ttu-id="14013-349">Typ</span><span class="sxs-lookup"><span data-stu-id="14013-349">Type</span></span>| <span data-ttu-id="14013-350">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="14013-350">Maximum size</span></span> | <span data-ttu-id="14013-351">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="14013-351">Required</span></span> | <span data-ttu-id="14013-352">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="14013-352">Description</span></span>|
|---|---|---|---|---|
|`items.scopes`|<span data-ttu-id="14013-353">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="14013-353">array of enums</span></span>|<span data-ttu-id="14013-354">3</span><span class="sxs-lookup"><span data-stu-id="14013-354">3</span></span>|<span data-ttu-id="14013-355">✔</span><span class="sxs-lookup"><span data-stu-id="14013-355">✔</span></span>|<span data-ttu-id="14013-356">Gibt den Bereich an, für den die Befehlsliste gültig ist.</span><span class="sxs-lookup"><span data-stu-id="14013-356">Specifies the scope for which the command list is valid.</span></span> <span data-ttu-id="14013-357">Mögliche Optionen sind `team`, `personal` und `groupchat`.</span><span class="sxs-lookup"><span data-stu-id="14013-357">Options are `team`, `personal`, and `groupchat`.</span></span>|
|`items.commands`|<span data-ttu-id="14013-358">Array von Objekten</span><span class="sxs-lookup"><span data-stu-id="14013-358">array of objects</span></span>|<span data-ttu-id="14013-359">10  </span><span class="sxs-lookup"><span data-stu-id="14013-359">10</span></span>|<span data-ttu-id="14013-360">✔</span><span class="sxs-lookup"><span data-stu-id="14013-360">✔</span></span>|<span data-ttu-id="14013-361">Ein Array von Befehlen, die der Bot unterstützt:</span><span class="sxs-lookup"><span data-stu-id="14013-361">An array of commands the bot supports:</span></span><br><span data-ttu-id="14013-362">`title`: Name des Bot-Befehls (string, 32)</span><span class="sxs-lookup"><span data-stu-id="14013-362">`title`: the bot command name (string, 32)</span></span><br><span data-ttu-id="14013-363">`description`: einfache Beschreibung oder Beispiel für die Befehlssyntax und zugehörige Argumente (string, 128)</span><span class="sxs-lookup"><span data-stu-id="14013-363">`description`: a simple description or example of the command syntax and its argument (string, 128)</span></span>|

### <a name="botscommandlistscommands"></a><span data-ttu-id="14013-364">bots.commandLists.commands</span><span class="sxs-lookup"><span data-stu-id="14013-364">bots.commandLists.commands</span></span>

|<span data-ttu-id="14013-365">Name</span><span class="sxs-lookup"><span data-stu-id="14013-365">Name</span></span>| <span data-ttu-id="14013-366">Typ</span><span class="sxs-lookup"><span data-stu-id="14013-366">Type</span></span>| <span data-ttu-id="14013-367">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="14013-367">Maximum size</span></span> | <span data-ttu-id="14013-368">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="14013-368">Required</span></span> | <span data-ttu-id="14013-369">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="14013-369">Description</span></span>|
|---|---|---|---|---|
|<span data-ttu-id="14013-370">title</span><span class="sxs-lookup"><span data-stu-id="14013-370">title</span></span>|<span data-ttu-id="14013-371">string</span><span class="sxs-lookup"><span data-stu-id="14013-371">string</span></span>|<span data-ttu-id="14013-372">12 </span><span class="sxs-lookup"><span data-stu-id="14013-372">12</span></span>|<span data-ttu-id="14013-373">✔</span><span class="sxs-lookup"><span data-stu-id="14013-373">✔</span></span>|<span data-ttu-id="14013-374">Name des Botbefehls</span><span class="sxs-lookup"><span data-stu-id="14013-374">The bot command name</span></span>|
|<span data-ttu-id="14013-375">description</span><span class="sxs-lookup"><span data-stu-id="14013-375">description</span></span>|<span data-ttu-id="14013-376">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="14013-376">string</span></span>|<span data-ttu-id="14013-377">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="14013-377">128 characters</span></span>|<span data-ttu-id="14013-378">✔</span><span class="sxs-lookup"><span data-stu-id="14013-378">✔</span></span>|<span data-ttu-id="14013-379">Eine einfache Textbeschreibung oder ein Beispiel für die Befehlssyntax und deren Argumente.</span><span class="sxs-lookup"><span data-stu-id="14013-379">A simple text description or an example of the command syntax and its arguments.</span></span>|

## <a name="connectors"></a><span data-ttu-id="14013-380">Connectors</span><span class="sxs-lookup"><span data-stu-id="14013-380">connectors</span></span>

<span data-ttu-id="14013-381">**Optional** – Array</span><span class="sxs-lookup"><span data-stu-id="14013-381">**Optional** — array</span></span>

<span data-ttu-id="14013-382">Der `connectors` Block definiert einen Office 365 Connector für die App.</span><span class="sxs-lookup"><span data-stu-id="14013-382">The `connectors` block defines an Office 365 Connector for the app.</span></span>

<span data-ttu-id="14013-383">Das Objekt ist ein Array (maximal 1 Element) mit allen Elementen vom Typ `object` .</span><span class="sxs-lookup"><span data-stu-id="14013-383">The object is an array (maximum of 1 element) with all elements of type `object`.</span></span> <span data-ttu-id="14013-384">Dieser Block ist nur für Lösungen erforderlich, die einen Connector bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="14013-384">This block is required only for solutions that provide a Connector.</span></span>

|<span data-ttu-id="14013-385">Name</span><span class="sxs-lookup"><span data-stu-id="14013-385">Name</span></span>| <span data-ttu-id="14013-386">Typ</span><span class="sxs-lookup"><span data-stu-id="14013-386">Type</span></span>| <span data-ttu-id="14013-387">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="14013-387">Maximum size</span></span> | <span data-ttu-id="14013-388">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="14013-388">Required</span></span> | <span data-ttu-id="14013-389">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="14013-389">Description</span></span>|
|---|---|---|---|---|
|`configurationUrl`|<span data-ttu-id="14013-390">string</span><span class="sxs-lookup"><span data-stu-id="14013-390">string</span></span>|<span data-ttu-id="14013-391">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="14013-391">2048 characters</span></span>|<span data-ttu-id="14013-392">✔</span><span class="sxs-lookup"><span data-stu-id="14013-392">✔</span></span>|<span data-ttu-id="14013-393">Die https://-URL, die beim Konfigurieren des Connectors verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="14013-393">The https:// URL to use when configuring the connector.</span></span>|
|`scopes`|<span data-ttu-id="14013-394">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="14013-394">array of enums</span></span>|<span data-ttu-id="14013-395">1</span><span class="sxs-lookup"><span data-stu-id="14013-395">1</span></span>|<span data-ttu-id="14013-396">✔</span><span class="sxs-lookup"><span data-stu-id="14013-396">✔</span></span>|<span data-ttu-id="14013-397">Gibt an, ob der Connector eine Benutzeroberfläche im Kontext eines Kanals in einem oder eine Benutzeroberfläche bietet, die auf einen einzelnen Benutzer `team` begrenzt ist ( `personal` ).</span><span class="sxs-lookup"><span data-stu-id="14013-397">Specifies whether the Connector offers an experience in the context of a channel in a `team`, or an experience scoped to an individual user alone (`personal`).</span></span> <span data-ttu-id="14013-398">Derzeit wird nur `team` der Bereich unterstützt.</span><span class="sxs-lookup"><span data-stu-id="14013-398">Currently, only the `team` scope is supported.</span></span>|
|`connectorId`|<span data-ttu-id="14013-399">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="14013-399">string</span></span>|<span data-ttu-id="14013-400">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="14013-400">64 characters</span></span>|<span data-ttu-id="14013-401">✔</span><span class="sxs-lookup"><span data-stu-id="14013-401">✔</span></span>|<span data-ttu-id="14013-402">Ein eindeutiger Bezeichner für den Connector, der seiner ID im [Connectors Developer Dashboard entspricht.](https://aka.ms/connectorsdashboard)</span><span class="sxs-lookup"><span data-stu-id="14013-402">A unique identifier for the Connector that matches its ID in the [Connectors Developer Dashboard](https://aka.ms/connectorsdashboard).</span></span>|

## <a name="composeextensions"></a><span data-ttu-id="14013-403">composeExtensions</span><span class="sxs-lookup"><span data-stu-id="14013-403">composeExtensions</span></span>

<span data-ttu-id="14013-404">**Optional** – Array</span><span class="sxs-lookup"><span data-stu-id="14013-404">**Optional** — array</span></span>

<span data-ttu-id="14013-405">Definiert eine Messagingerweiterung für die App.</span><span class="sxs-lookup"><span data-stu-id="14013-405">Defines a messaging extension for the app.</span></span>

> [!NOTE]
> <span data-ttu-id="14013-406">Der Name des Features wurde im November 2017 von "Verfassenerweiterung" in "Messagingerweiterung" geändert, der Manifestname bleibt jedoch unverändert, damit vorhandene Erweiterungen weiterhin funktionieren.</span><span class="sxs-lookup"><span data-stu-id="14013-406">The name of the feature was changed from "compose extension" to "messaging extension" in November, 2017, but the manifest name remains the same so that existing extensions continue to function.</span></span>

<span data-ttu-id="14013-407">Das Element ist ein Array (maximal 1 Element) mit allen Elementen vom Typ `object` .</span><span class="sxs-lookup"><span data-stu-id="14013-407">The item is an array (maximum of 1 element) with all elements of type `object`.</span></span> <span data-ttu-id="14013-408">Dieser Block ist nur für Lösungen erforderlich, die eine Messagingerweiterung bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="14013-408">This block is required only for solutions that provide a messaging extension.</span></span>

|<span data-ttu-id="14013-409">Name</span><span class="sxs-lookup"><span data-stu-id="14013-409">Name</span></span>| <span data-ttu-id="14013-410">Typ</span><span class="sxs-lookup"><span data-stu-id="14013-410">Type</span></span> | <span data-ttu-id="14013-411">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="14013-411">Maximum Size</span></span> | <span data-ttu-id="14013-412">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="14013-412">Required</span></span> | <span data-ttu-id="14013-413">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="14013-413">Description</span></span>|
|---|---|---|---|---|
|`botId`|<span data-ttu-id="14013-414">string</span><span class="sxs-lookup"><span data-stu-id="14013-414">string</span></span>|<span data-ttu-id="14013-415">64</span><span class="sxs-lookup"><span data-stu-id="14013-415">64</span></span>|<span data-ttu-id="14013-416">✔</span><span class="sxs-lookup"><span data-stu-id="14013-416">✔</span></span>|<span data-ttu-id="14013-417">Die eindeutige Microsoft-App-ID für den Bot, der die Messagingerweiterung unterstützt, wie beim Bot Framework registriert.</span><span class="sxs-lookup"><span data-stu-id="14013-417">The unique Microsoft app ID for the bot that backs the messaging extension, as registered with the Bot Framework.</span></span> <span data-ttu-id="14013-418">Dies kann mit der allgemeinen App-ID identisch sein.</span><span class="sxs-lookup"><span data-stu-id="14013-418">This may well be the same as the overall App ID.</span></span>|
|`commands`|<span data-ttu-id="14013-419">Array von Objekten</span><span class="sxs-lookup"><span data-stu-id="14013-419">array of objects</span></span>|<span data-ttu-id="14013-420">10  </span><span class="sxs-lookup"><span data-stu-id="14013-420">10</span></span>|<span data-ttu-id="14013-421">✔</span><span class="sxs-lookup"><span data-stu-id="14013-421">✔</span></span>|<span data-ttu-id="14013-422">Array von Befehlen, die von der Messagingerweiterung unterstützt werden</span><span class="sxs-lookup"><span data-stu-id="14013-422">Array of commands the messaging extension supports</span></span>|
|`canUpdateConfiguration`|<span data-ttu-id="14013-423">boolean</span><span class="sxs-lookup"><span data-stu-id="14013-423">boolean</span></span>|||<span data-ttu-id="14013-424">Ein Wert, der angibt, ob die Konfiguration einer Messagingerweiterung vom Benutzer aktualisiert werden kann.</span><span class="sxs-lookup"><span data-stu-id="14013-424">A value indicating whether the configuration of a messaging extension can be updated by the user.</span></span> <span data-ttu-id="14013-425">Standard: **False**.</span><span class="sxs-lookup"><span data-stu-id="14013-425">Default: **false**.</span></span>|
|`messageHandlers`|<span data-ttu-id="14013-426">Array von Objekten</span><span class="sxs-lookup"><span data-stu-id="14013-426">array of Objects</span></span>|<span data-ttu-id="14013-427">5 </span><span class="sxs-lookup"><span data-stu-id="14013-427">5</span></span>||<span data-ttu-id="14013-428">Eine Liste von Handlern, mit denen Apps aufgerufen werden können, wenn bestimmte Bedingungen erfüllt sind.</span><span class="sxs-lookup"><span data-stu-id="14013-428">A list of handlers that allow apps to be invoked when certain conditions are met.</span></span>|
|`messageHandlers.type`|<span data-ttu-id="14013-429">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="14013-429">string</span></span>|||<span data-ttu-id="14013-430">Der Typ des Nachrichtenhandlers.</span><span class="sxs-lookup"><span data-stu-id="14013-430">The type of message handler.</span></span> <span data-ttu-id="14013-431">Muss `"link"` sein.</span><span class="sxs-lookup"><span data-stu-id="14013-431">Must be `"link"`.</span></span>|
|`messageHandlers.value.domains`|<span data-ttu-id="14013-432">Array von Zeichenfolgen</span><span class="sxs-lookup"><span data-stu-id="14013-432">array of Strings</span></span>|||<span data-ttu-id="14013-433">Array von Domänen, für die der Linknachrichtenhandler registrieren kann.</span><span class="sxs-lookup"><span data-stu-id="14013-433">Array of domains that the link message handler can register for.</span></span>|

### <a name="composeextensionscommands"></a><span data-ttu-id="14013-434">composeExtensions.commands</span><span class="sxs-lookup"><span data-stu-id="14013-434">composeExtensions.commands</span></span>

<span data-ttu-id="14013-435">Ihre Messagingerweiterung muss einen oder mehrere Befehle deklarieren.</span><span class="sxs-lookup"><span data-stu-id="14013-435">Your messaging extension must declare one or more commands.</span></span> <span data-ttu-id="14013-436">Jeder Befehl wird in Microsoft Teams als potenzielle Interaktion vom benutzeroberflächenbasierten Einstiegspunkt angezeigt.</span><span class="sxs-lookup"><span data-stu-id="14013-436">Each command appears in Microsoft Teams as a potential interaction from the UI-based entry point.</span></span> <span data-ttu-id="14013-437">Es gibt maximal 10 Befehle.</span><span class="sxs-lookup"><span data-stu-id="14013-437">There is a maximum of 10 commands.</span></span>

<span data-ttu-id="14013-438">Jedes Befehlselement ist ein Objekt mit der folgenden Struktur:</span><span class="sxs-lookup"><span data-stu-id="14013-438">Each command item is an object with the following structure:</span></span>

|<span data-ttu-id="14013-439">Name</span><span class="sxs-lookup"><span data-stu-id="14013-439">Name</span></span>| <span data-ttu-id="14013-440">Typ</span><span class="sxs-lookup"><span data-stu-id="14013-440">Type</span></span>| <span data-ttu-id="14013-441">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="14013-441">Maximum size</span></span> | <span data-ttu-id="14013-442">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="14013-442">Required</span></span> | <span data-ttu-id="14013-443">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="14013-443">Description</span></span>|
|---|---|---|---|---|
|`id`|<span data-ttu-id="14013-444">string</span><span class="sxs-lookup"><span data-stu-id="14013-444">string</span></span>|<span data-ttu-id="14013-445">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="14013-445">64 characters</span></span>|<span data-ttu-id="14013-446">✔</span><span class="sxs-lookup"><span data-stu-id="14013-446">✔</span></span>|<span data-ttu-id="14013-447">Die ID für den Befehl.</span><span class="sxs-lookup"><span data-stu-id="14013-447">The ID for the command.</span></span>|
|`title`|<span data-ttu-id="14013-448">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="14013-448">string</span></span>|<span data-ttu-id="14013-449">32 Zeichen</span><span class="sxs-lookup"><span data-stu-id="14013-449">32 characters</span></span>|<span data-ttu-id="14013-450">✔</span><span class="sxs-lookup"><span data-stu-id="14013-450">✔</span></span>|<span data-ttu-id="14013-451">Der benutzerfreundliche Befehlsname.</span><span class="sxs-lookup"><span data-stu-id="14013-451">The user-friendly command name.</span></span>|
|`type`|<span data-ttu-id="14013-452">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="14013-452">string</span></span>|<span data-ttu-id="14013-453">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="14013-453">64 characters</span></span>||<span data-ttu-id="14013-454">Typ des Befehls.</span><span class="sxs-lookup"><span data-stu-id="14013-454">Type of the command.</span></span> <span data-ttu-id="14013-455">Einer oder `query` `action` .</span><span class="sxs-lookup"><span data-stu-id="14013-455">One of `query` or `action`.</span></span> <span data-ttu-id="14013-456">Standard: **Abfrage**.</span><span class="sxs-lookup"><span data-stu-id="14013-456">Default: **query**.</span></span>|
|`description`|<span data-ttu-id="14013-457">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="14013-457">string</span></span>|<span data-ttu-id="14013-458">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="14013-458">128 characters</span></span>||<span data-ttu-id="14013-459">Die Beschreibung, die Benutzern angezeigt wird, um den Zweck dieses Befehls anzugeben.</span><span class="sxs-lookup"><span data-stu-id="14013-459">The description that appears to users to indicate the purpose of this command.</span></span>|
|`initialRun`|<span data-ttu-id="14013-460">boolean</span><span class="sxs-lookup"><span data-stu-id="14013-460">boolean</span></span>|||<span data-ttu-id="14013-461">Ein boolescher Wert gibt an, ob der Befehl anfangs ohne Parameter ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="14013-461">A boolean value indicates whether the command runs initially with no parameters.</span></span> <span data-ttu-id="14013-462">Der Standardwert ist **false**.</span><span class="sxs-lookup"><span data-stu-id="14013-462">Default is **false**.</span></span>|
|`context`|<span data-ttu-id="14013-463">Array von Zeichenfolgen</span><span class="sxs-lookup"><span data-stu-id="14013-463">array of Strings</span></span>|<span data-ttu-id="14013-464">3</span><span class="sxs-lookup"><span data-stu-id="14013-464">3</span></span>||<span data-ttu-id="14013-465">Definiert, von wo aus die Nachrichtenerweiterung aufgerufen werden kann.</span><span class="sxs-lookup"><span data-stu-id="14013-465">Defines where the message extension can be invoked from.</span></span> <span data-ttu-id="14013-466">Beliebige Kombination aus `compose` , `commandBox` , `message` .</span><span class="sxs-lookup"><span data-stu-id="14013-466">Any combination of`compose`,`commandBox`,`message`.</span></span> <span data-ttu-id="14013-467">Der Standardwert ist `["compose","commandBox"]`.</span><span class="sxs-lookup"><span data-stu-id="14013-467">Default is `["compose","commandBox"]`.</span></span>|
|`fetchTask`|<span data-ttu-id="14013-468">boolean</span><span class="sxs-lookup"><span data-stu-id="14013-468">boolean</span></span>|||<span data-ttu-id="14013-469">Ein boolescher Wert, der angibt, ob das Aufgabenmodul dynamisch abgerufen werden muss.</span><span class="sxs-lookup"><span data-stu-id="14013-469">A boolean value that indicates if it must fetch the task module dynamically.</span></span> <span data-ttu-id="14013-470">Der Standardwert ist **false**.</span><span class="sxs-lookup"><span data-stu-id="14013-470">Default is **false**.</span></span>|
|`taskInfo`|<span data-ttu-id="14013-471">Objekt</span><span class="sxs-lookup"><span data-stu-id="14013-471">object</span></span>|||<span data-ttu-id="14013-472">Geben Sie das Aufgabenmodul an, das beim Verwenden eines Befehls für die Messagingerweiterung vor dem Laden geladen werden soll.</span><span class="sxs-lookup"><span data-stu-id="14013-472">Specify the task module to pre-load when using a messaging extension command.</span></span>|
|`taskInfo.title`|<span data-ttu-id="14013-473">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="14013-473">string</span></span>|<span data-ttu-id="14013-474">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="14013-474">64 characters</span></span>||<span data-ttu-id="14013-475">Titel des ersten Dialogfelds.</span><span class="sxs-lookup"><span data-stu-id="14013-475">Initial dialog title.</span></span>|
|`taskInfo.width`|<span data-ttu-id="14013-476">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="14013-476">string</span></span>|||<span data-ttu-id="14013-477">Dialogbreite – entweder eine Zahl in Pixel oder ein Standardlayout wie "groß", "mittel" oder "klein".</span><span class="sxs-lookup"><span data-stu-id="14013-477">Dialog width - either a number in pixels or default layout such as 'large', 'medium', or 'small'.</span></span>|
|`taskInfo.height`|<span data-ttu-id="14013-478">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="14013-478">string</span></span>|||<span data-ttu-id="14013-479">Dialoghöhe – entweder eine Zahl in Pixel oder ein Standardlayout wie "groß", "mittel" oder "klein".</span><span class="sxs-lookup"><span data-stu-id="14013-479">Dialog height - either a number in pixels or default layout such as 'large', 'medium', or 'small'.</span></span>|
|`taskInfo.url`|<span data-ttu-id="14013-480">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="14013-480">string</span></span>|||<span data-ttu-id="14013-481">Anfängliche Webview-URL.</span><span class="sxs-lookup"><span data-stu-id="14013-481">Initial webview URL.</span></span>|
|`parameters`|<span data-ttu-id="14013-482">Array des Objekts</span><span class="sxs-lookup"><span data-stu-id="14013-482">array of object</span></span>|<span data-ttu-id="14013-483">5 Elemente</span><span class="sxs-lookup"><span data-stu-id="14013-483">5 items</span></span>|<span data-ttu-id="14013-484">✔</span><span class="sxs-lookup"><span data-stu-id="14013-484">✔</span></span>|<span data-ttu-id="14013-485">Die Liste der Parameter, die der Befehl verwendet.</span><span class="sxs-lookup"><span data-stu-id="14013-485">The list of parameters the command takes.</span></span> <span data-ttu-id="14013-486">Minimum: 1; maximum: 5.</span><span class="sxs-lookup"><span data-stu-id="14013-486">Minimum: 1; maximum: 5.</span></span>|
|`parameters.name`|<span data-ttu-id="14013-487">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="14013-487">string</span></span>|<span data-ttu-id="14013-488">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="14013-488">64 characters</span></span>|<span data-ttu-id="14013-489">✔</span><span class="sxs-lookup"><span data-stu-id="14013-489">✔</span></span>|<span data-ttu-id="14013-490">Der Name des Parameters, wie er im Client angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="14013-490">The name of the parameter as it appears in the client.</span></span> <span data-ttu-id="14013-491">Dies ist in der Benutzeranforderung enthalten.</span><span class="sxs-lookup"><span data-stu-id="14013-491">This is included in the user request.</span></span>|
|`parameters.title`|<span data-ttu-id="14013-492">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="14013-492">string</span></span>|<span data-ttu-id="14013-493">32 Zeichen</span><span class="sxs-lookup"><span data-stu-id="14013-493">32 characters</span></span>|<span data-ttu-id="14013-494">✔</span><span class="sxs-lookup"><span data-stu-id="14013-494">✔</span></span>|<span data-ttu-id="14013-495">Benutzerfreundlicher Titel für den Parameter.</span><span class="sxs-lookup"><span data-stu-id="14013-495">User-friendly title for the parameter.</span></span>|
|`parameters.description`|<span data-ttu-id="14013-496">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="14013-496">string</span></span>|<span data-ttu-id="14013-497">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="14013-497">128 characters</span></span>||<span data-ttu-id="14013-498">Benutzerfreundliche Zeichenfolge, die den Zweck dieses Parameters beschreibt.</span><span class="sxs-lookup"><span data-stu-id="14013-498">User-friendly string that describes this parameter’s purpose.</span></span>|
|`parameters.value`|<span data-ttu-id="14013-499">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="14013-499">string</span></span>|<span data-ttu-id="14013-500">512 Zeichen</span><span class="sxs-lookup"><span data-stu-id="14013-500">512 characters</span></span>||<span data-ttu-id="14013-501">Anfangswert für den Parameter.</span><span class="sxs-lookup"><span data-stu-id="14013-501">Initial value for the parameter.</span></span>|
|`parameters.inputType`|<span data-ttu-id="14013-502">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="14013-502">string</span></span>|<span data-ttu-id="14013-503">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="14013-503">128 characters</span></span>||<span data-ttu-id="14013-504">Definiert den Typ des Steuerelements, das in einem Aufgabenmodul für angezeigt `fetchTask: true` wird.</span><span class="sxs-lookup"><span data-stu-id="14013-504">Defines the type of control displayed on a task module for`fetchTask: true` .</span></span> <span data-ttu-id="14013-505">Einer von `text, textarea, number, date, time, toggle, choiceset` .</span><span class="sxs-lookup"><span data-stu-id="14013-505">One of `text, textarea, number, date, time, toggle, choiceset` .</span></span>|
|`parameters.choices`|<span data-ttu-id="14013-506">Array von Objekten</span><span class="sxs-lookup"><span data-stu-id="14013-506">array of objects</span></span>|<span data-ttu-id="14013-507">10 Elemente</span><span class="sxs-lookup"><span data-stu-id="14013-507">10 items</span></span>||<span data-ttu-id="14013-508">Die Auswahloptionen für `choiceset` .</span><span class="sxs-lookup"><span data-stu-id="14013-508">The choice options for the`choiceset`.</span></span> <span data-ttu-id="14013-509">Verwenden Sie nur, `parameter.inputType` wenn `choiceset` .</span><span class="sxs-lookup"><span data-stu-id="14013-509">Use only when`parameter.inputType` is `choiceset`.</span></span>|
|`parameters.choices.title`|<span data-ttu-id="14013-510">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="14013-510">string</span></span>|<span data-ttu-id="14013-511">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="14013-511">128 characters</span></span>|<span data-ttu-id="14013-512">✔</span><span class="sxs-lookup"><span data-stu-id="14013-512">✔</span></span>|<span data-ttu-id="14013-513">Titel der Auswahl.</span><span class="sxs-lookup"><span data-stu-id="14013-513">Title of the choice.</span></span>|
|`parameters.choices.value`|<span data-ttu-id="14013-514">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="14013-514">string</span></span>|<span data-ttu-id="14013-515">512 Zeichen</span><span class="sxs-lookup"><span data-stu-id="14013-515">512 characters</span></span>|<span data-ttu-id="14013-516">✔</span><span class="sxs-lookup"><span data-stu-id="14013-516">✔</span></span>|<span data-ttu-id="14013-517">Value of the choice.</span><span class="sxs-lookup"><span data-stu-id="14013-517">Value of the choice.</span></span>|

## <a name="permissions"></a><span data-ttu-id="14013-518">Berechtigungen</span><span class="sxs-lookup"><span data-stu-id="14013-518">permissions</span></span>

<span data-ttu-id="14013-519">**Optional** – Array von Zeichenfolgen</span><span class="sxs-lookup"><span data-stu-id="14013-519">**Optional** — array of strings</span></span>

<span data-ttu-id="14013-520">Ein Array von dem angibt, welche Berechtigungen die App anfordert, wodurch Endbenutzer wissen, `string` wie die Erweiterung funktioniert.</span><span class="sxs-lookup"><span data-stu-id="14013-520">An array of `string` which specifies which permissions the app requests, which lets end users know how the extension performs.</span></span> <span data-ttu-id="14013-521">Die folgenden Optionen sind nicht exklusiv:</span><span class="sxs-lookup"><span data-stu-id="14013-521">The following options are non-exclusive:</span></span>

* <span data-ttu-id="14013-522">`identity`&emsp;Erfordert Benutzeridentitätsinformationen</span><span class="sxs-lookup"><span data-stu-id="14013-522">`identity` &emsp; Requires user identity information</span></span>
* <span data-ttu-id="14013-523">`messageTeamMembers`&emsp;Erfordert die Berechtigung zum Senden von Direktnachrichten an Teammitglieder</span><span class="sxs-lookup"><span data-stu-id="14013-523">`messageTeamMembers` &emsp; Requires permission to send direct messages to team members</span></span>

<span data-ttu-id="14013-524">Wenn Sie diese Berechtigungen während des App-Updates ändern, wiederholen Ihre Benutzer den Zustimmungsprozess, nachdem sie die aktualisierte App ausgeführt haben.</span><span class="sxs-lookup"><span data-stu-id="14013-524">Changing these permissions during app update, causes your users to repeat the consent process after they run the updated app.</span></span> <span data-ttu-id="14013-525">Weitere [Informationen finden Sie unter Aktualisieren](~/concepts/deploy-and-publish/appsource/post-publish/overview.md) Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="14013-525">See [Updating your app](~/concepts/deploy-and-publish/appsource/post-publish/overview.md) for more information.</span></span>

## <a name="devicepermissions"></a><span data-ttu-id="14013-526">devicePermissions</span><span class="sxs-lookup"><span data-stu-id="14013-526">devicePermissions</span></span>

<span data-ttu-id="14013-527">**Optional** – Array von Zeichenfolgen</span><span class="sxs-lookup"><span data-stu-id="14013-527">**Optional** — array of strings</span></span>

<span data-ttu-id="14013-528">Stellt die systemeigenen Features auf dem Gerät eines Benutzers zur Verfügung, auf das Ihre App Zugriff anfordert.</span><span class="sxs-lookup"><span data-stu-id="14013-528">Provides the native features on a user's device that your app requests access to.</span></span> <span data-ttu-id="14013-529">Mögliche Optionen sind:</span><span class="sxs-lookup"><span data-stu-id="14013-529">Options are:</span></span>

* `geolocation`
* `media`
* `notifications`
* `midi`
* `openExternal`

## <a name="validdomains"></a><span data-ttu-id="14013-530">validDomains</span><span class="sxs-lookup"><span data-stu-id="14013-530">validDomains</span></span>

<span data-ttu-id="14013-531">**Optional**, mit **Ausnahme erforderlich,** sofern angegeben</span><span class="sxs-lookup"><span data-stu-id="14013-531">**Optional**, except **Required** where noted</span></span>

<span data-ttu-id="14013-532">Eine Liste der gültigen Domänen für Websites, die die App im Client Teams wird.</span><span class="sxs-lookup"><span data-stu-id="14013-532">A list of valid domains for websites the app expects to load within the Teams client.</span></span> <span data-ttu-id="14013-533">Domänenauflistungen können Platzhalter enthalten, z. B. `*.example.com` .</span><span class="sxs-lookup"><span data-stu-id="14013-533">Domain listings can include wildcards, for example, `*.example.com`.</span></span> <span data-ttu-id="14013-534">Dies entspricht genau einem Abschnitt der Domäne. wenn Sie übereinstimmen müssen, `a.b.example.com` verwenden Sie `*.*.example.com` .</span><span class="sxs-lookup"><span data-stu-id="14013-534">This matches exactly one segment of the domain; if you need to match `a.b.example.com` then use `*.*.example.com`.</span></span> <span data-ttu-id="14013-535">Wenn Ihre Registerkartenkonfiguration oder Inhaltsbenutzeroberfläche neben der für die Registerkartenkonfiguration verwendeten Domäne zu einer anderen Domäne navigieren muss, muss diese Domäne hier angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="14013-535">If your tab configuration or content UI needs to navigate to any other domain besides the one use for tab configuration, that domain must be specified here.</span></span>

<span data-ttu-id="14013-536">Es ist **nicht** erforderlich, die Domänen von Identitätsanbietern, die Sie unterstützen möchten, in Ihre App zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="14013-536">It is **not** necessary to include the domains of identity providers you want to support in your app.</span></span> <span data-ttu-id="14013-537">Um sich z. B. mithilfe einer Google-ID zu authentifizieren, müssen Sie an accounts.google.com umleiten, sie dürfen jedoch accounts.google.com in nicht `validDomains[]` enthalten.</span><span class="sxs-lookup"><span data-stu-id="14013-537">For example, to authenticate using a Google ID, it is required to redirect to accounts.google.com, however, you must not include accounts.google.com in `validDomains[]`.</span></span>

<span data-ttu-id="14013-538">Teams apps that require their own sharepoint URLs to function well, includes "{teamsitedomain}" in their valid domain list.</span><span class="sxs-lookup"><span data-stu-id="14013-538">Teams apps that require their own sharepoint URLs to function well, includes "{teamsitedomain}" in their valid domain list.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="14013-539">Fügen Sie keine Domänen hinzu, die sich außerhalb Ihres Steuerelements befinden, weder direkt noch über Platzhalter.</span><span class="sxs-lookup"><span data-stu-id="14013-539">Do not add domains that are outside your control, either directly or through wildcards.</span></span> <span data-ttu-id="14013-540">Ist z. `yourapp.onmicrosoft.com` B. gültig, ist `*.onmicrosoft.com` jedoch ungültig.</span><span class="sxs-lookup"><span data-stu-id="14013-540">For example, `yourapp.onmicrosoft.com` is valid, however, `*.onmicrosoft.com` is not valid.</span></span>

<span data-ttu-id="14013-541">Das Objekt ist ein Array mit allen Elementen des Typs `string` .</span><span class="sxs-lookup"><span data-stu-id="14013-541">The object is an array with all elements of the type `string`.</span></span>

## <a name="webapplicationinfo"></a><span data-ttu-id="14013-542">webApplicationInfo</span><span class="sxs-lookup"><span data-stu-id="14013-542">webApplicationInfo</span></span>

<span data-ttu-id="14013-543">**Optional** – -Objekt</span><span class="sxs-lookup"><span data-stu-id="14013-543">**Optional** — object</span></span>

<span data-ttu-id="14013-544">Geben Sie Azure Active Directory (AAD)-App-ID und Microsoft Graph, um Benutzern die nahtlose Anmeldung bei Ihrer App zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="14013-544">Provide your Azure Active Directory (AAD) App ID and Microsoft Graph information to help users seamlessly sign into your app.</span></span> <span data-ttu-id="14013-545">Wenn Ihre App in AAD registriert ist, müssen Sie die App-ID bereitstellen, damit Administratoren die Berechtigungen problemlos überprüfen und ihre Zustimmung im Teams erteilen können.</span><span class="sxs-lookup"><span data-stu-id="14013-545">If your app is registered in AAD, you must provide the App ID, so that administrators can easily review permissions and grant consent in Teams admin center.</span></span>

|<span data-ttu-id="14013-546">Name</span><span class="sxs-lookup"><span data-stu-id="14013-546">Name</span></span>| <span data-ttu-id="14013-547">Typ</span><span class="sxs-lookup"><span data-stu-id="14013-547">Type</span></span>| <span data-ttu-id="14013-548">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="14013-548">Maximum size</span></span> | <span data-ttu-id="14013-549">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="14013-549">Required</span></span> | <span data-ttu-id="14013-550">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="14013-550">Description</span></span>|
|---|---|---|---|---|
|`id`|<span data-ttu-id="14013-551">string</span><span class="sxs-lookup"><span data-stu-id="14013-551">string</span></span>|<span data-ttu-id="14013-552">36 Zeichen</span><span class="sxs-lookup"><span data-stu-id="14013-552">36 characters</span></span>|<span data-ttu-id="14013-553">✔</span><span class="sxs-lookup"><span data-stu-id="14013-553">✔</span></span>|<span data-ttu-id="14013-554">AAD-Anwendungs-ID der App.</span><span class="sxs-lookup"><span data-stu-id="14013-554">AAD application id of the app.</span></span> <span data-ttu-id="14013-555">Diese ID muss eine GUID sein.</span><span class="sxs-lookup"><span data-stu-id="14013-555">This id must be a GUID.</span></span>|
|`resource`|<span data-ttu-id="14013-556">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="14013-556">string</span></span>|<span data-ttu-id="14013-557">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="14013-557">2048 characters</span></span>|<span data-ttu-id="14013-558">✔</span><span class="sxs-lookup"><span data-stu-id="14013-558">✔</span></span>|<span data-ttu-id="14013-559">Ressourcen-URL der App zum Abrufen des Authentifizierungstokens für SSO.</span><span class="sxs-lookup"><span data-stu-id="14013-559">Resource URL of app for acquiring auth token for SSO.</span></span> </br> <span data-ttu-id="14013-560">**HINWEIS:** Wenn Sie SSO nicht verwenden, stellen Sie sicher, dass Sie in diesem Feld einen Schnullerzeichenfolgenwert in Ihr App-Manifest eingeben, um beispielsweise eine https://notapplicable Fehlerantwort zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="14013-560">**NOTE:** If you are not using SSO, ensure that you enter a dummy string value in this field to your app manifest, for example, https://notapplicable to avoid an error response.</span></span> |
|`applicationPermissions`|<span data-ttu-id="14013-561">array of strings</span><span class="sxs-lookup"><span data-stu-id="14013-561">array of strings</span></span>|<span data-ttu-id="14013-562">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="14013-562">128 characters</span></span>||<span data-ttu-id="14013-563">Geben Sie [granulare ressourcenspezifische Zustimmung an.](../../graph-api/rsc/resource-specific-consent.md#resource-specific-permissions)</span><span class="sxs-lookup"><span data-stu-id="14013-563">Specify granular [resource specific consent](../../graph-api/rsc/resource-specific-consent.md#resource-specific-permissions).</span></span>|

## <a name="showloadingindicator"></a><span data-ttu-id="14013-564">showLoadingIndicator</span><span class="sxs-lookup"><span data-stu-id="14013-564">showLoadingIndicator</span></span>

<span data-ttu-id="14013-565">**Optional** – boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="14013-565">**Optional** — boolean</span></span>

<span data-ttu-id="14013-566">Gibt an, ob die Ladeanzeige angezeigt werden soll, wenn eine App oder Registerkarte geladen wird.</span><span class="sxs-lookup"><span data-stu-id="14013-566">Indicates whether or not to show the loading indicator when an app or tab is loading.</span></span> <span data-ttu-id="14013-567">Der Standardwert ist **false**.</span><span class="sxs-lookup"><span data-stu-id="14013-567">Default is **false**.</span></span>
>[!NOTE]
><span data-ttu-id="14013-568">Wenn Sie im App-Manifest als true auswählen, ändern Sie die Inhaltsseiten Ihrer Registerkarten und Aufgabenmodule, um die Seite ordnungsgemäß zu laden, wie unter Anzeigen eines nativen Ladeindikatordokuments `showLoadingIndicator` beschrieben. [](../../tabs/how-to/create-tab-pages/content-page.md#show-a-native-loading-indicator)</span><span class="sxs-lookup"><span data-stu-id="14013-568">If you select`showLoadingIndicator` as true in your app manifest, to load the page correctly, modify the content pages of your tabs and task modules as described in [Show a native loading indicator](../../tabs/how-to/create-tab-pages/content-page.md#show-a-native-loading-indicator) document.</span></span>


## <a name="isfullscreen"></a><span data-ttu-id="14013-569">isFullScreen</span><span class="sxs-lookup"><span data-stu-id="14013-569">isFullScreen</span></span>

 <span data-ttu-id="14013-570">**Optional** – boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="14013-570">**Optional** — boolean</span></span>

<span data-ttu-id="14013-571">Geben Sie an, wo eine persönliche App mit oder ohne Registerkartenkopfleiste gerendert wird.</span><span class="sxs-lookup"><span data-stu-id="14013-571">Indicate where a personal app is rendered with or without a tab header bar.</span></span> <span data-ttu-id="14013-572">Der Standardwert ist **false**.</span><span class="sxs-lookup"><span data-stu-id="14013-572">Default is **false**.</span></span>

## <a name="activities"></a><span data-ttu-id="14013-573">Aktivitäten</span><span class="sxs-lookup"><span data-stu-id="14013-573">activities</span></span>

<span data-ttu-id="14013-574">**Optional** – -Objekt</span><span class="sxs-lookup"><span data-stu-id="14013-574">**Optional** — object</span></span>

<span data-ttu-id="14013-575">Definieren Sie die Eigenschaften, die Ihre App zum Posten eines Benutzeraktivitätsfeeds verwendet.</span><span class="sxs-lookup"><span data-stu-id="14013-575">Define the properties your app uses to post a user activity feed.</span></span>

|<span data-ttu-id="14013-576">Name</span><span class="sxs-lookup"><span data-stu-id="14013-576">Name</span></span>| <span data-ttu-id="14013-577">Typ</span><span class="sxs-lookup"><span data-stu-id="14013-577">Type</span></span>| <span data-ttu-id="14013-578">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="14013-578">Maximum size</span></span> | <span data-ttu-id="14013-579">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="14013-579">Required</span></span> | <span data-ttu-id="14013-580">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="14013-580">Description</span></span>|
|---|---|---|---|---|
|`activityTypes`|<span data-ttu-id="14013-581">Array von Objekten</span><span class="sxs-lookup"><span data-stu-id="14013-581">array of Objects</span></span>|<span data-ttu-id="14013-582">128 Elemente</span><span class="sxs-lookup"><span data-stu-id="14013-582">128 items</span></span>| | <span data-ttu-id="14013-583">Stellen Sie die Arten von Aktivitäten zur Verfügung, die Ihre App an einen Benutzeraktivitätsfeed posten kann.</span><span class="sxs-lookup"><span data-stu-id="14013-583">Provide the types of activities that your app can post to a users activity feed.</span></span>|

### <a name="activitiesactivitytypes"></a><span data-ttu-id="14013-584">activities.activityTypes</span><span class="sxs-lookup"><span data-stu-id="14013-584">activities.activityTypes</span></span>

|<span data-ttu-id="14013-585">Name</span><span class="sxs-lookup"><span data-stu-id="14013-585">Name</span></span>| <span data-ttu-id="14013-586">Typ</span><span class="sxs-lookup"><span data-stu-id="14013-586">Type</span></span>| <span data-ttu-id="14013-587">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="14013-587">Maximum size</span></span> | <span data-ttu-id="14013-588">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="14013-588">Required</span></span> | <span data-ttu-id="14013-589">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="14013-589">Description</span></span>|
|---|---|---|---|---|
|`type`|<span data-ttu-id="14013-590">string</span><span class="sxs-lookup"><span data-stu-id="14013-590">string</span></span>|<span data-ttu-id="14013-591">32 Zeichen</span><span class="sxs-lookup"><span data-stu-id="14013-591">32 characters</span></span>|<span data-ttu-id="14013-592">✔</span><span class="sxs-lookup"><span data-stu-id="14013-592">✔</span></span>|<span data-ttu-id="14013-593">Der Benachrichtigungstyp.</span><span class="sxs-lookup"><span data-stu-id="14013-593">The notification type.</span></span> <span data-ttu-id="14013-594">*Siehe unten*.</span><span class="sxs-lookup"><span data-stu-id="14013-594">*See below*.</span></span>|
|`description`|<span data-ttu-id="14013-595">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="14013-595">string</span></span>|<span data-ttu-id="14013-596">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="14013-596">128 characters</span></span>|<span data-ttu-id="14013-597">✔</span><span class="sxs-lookup"><span data-stu-id="14013-597">✔</span></span>|<span data-ttu-id="14013-598">Eine kurze Beschreibung der Benachrichtigung.</span><span class="sxs-lookup"><span data-stu-id="14013-598">A brief description of the notification.</span></span> <span data-ttu-id="14013-599">*Siehe unten*.</span><span class="sxs-lookup"><span data-stu-id="14013-599">*See below*.</span></span>|
|`templateText`|<span data-ttu-id="14013-600">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="14013-600">string</span></span>|<span data-ttu-id="14013-601">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="14013-601">128 characters</span></span>|<span data-ttu-id="14013-602">✔</span><span class="sxs-lookup"><span data-stu-id="14013-602">✔</span></span>|<span data-ttu-id="14013-603">Ex: "{actor}- erstellter Task {taskId} für Sie"</span><span class="sxs-lookup"><span data-stu-id="14013-603">Ex: "{actor} created task {taskId} for you"</span></span>|

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

## <a name="defaultinstallscope"></a><span data-ttu-id="14013-604">defaultInstallScope</span><span class="sxs-lookup"><span data-stu-id="14013-604">defaultInstallScope</span></span>

<span data-ttu-id="14013-605">**Optional** – Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="14013-605">**Optional** - string</span></span>

<span data-ttu-id="14013-606">Gibt den für diese App definierten Installationsbereich standardmäßig an.</span><span class="sxs-lookup"><span data-stu-id="14013-606">Specifies the install scope defined for this app by default.</span></span> <span data-ttu-id="14013-607">Der definierte Bereich ist die Option, die auf der Schaltfläche angezeigt wird, wenn ein Benutzer versucht, die App hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="14013-607">The defined scope will be the option displayed on the button when a user tries to add the app.</span></span> <span data-ttu-id="14013-608">Mögliche Optionen sind:</span><span class="sxs-lookup"><span data-stu-id="14013-608">Options are:</span></span>
* `personal`
* `team`
* `groupchat`
* `meetings`

## <a name="defaultgroupcapability"></a><span data-ttu-id="14013-609">defaultGroupCapability</span><span class="sxs-lookup"><span data-stu-id="14013-609">defaultGroupCapability</span></span>

<span data-ttu-id="14013-610">**Optional** - -Objekt</span><span class="sxs-lookup"><span data-stu-id="14013-610">**Optional** - object</span></span>

<span data-ttu-id="14013-611">Wenn ein Gruppeninstallationsbereich ausgewählt ist, wird die Standardfunktion definiert, wenn der Benutzer die App installiert.</span><span class="sxs-lookup"><span data-stu-id="14013-611">When a group install scope is selected, it will define the default capability when the user installs the app.</span></span> <span data-ttu-id="14013-612">Mögliche Optionen sind:</span><span class="sxs-lookup"><span data-stu-id="14013-612">Options are:</span></span>
* `team`
* `groupchat`
* `meetings`
 
|<span data-ttu-id="14013-613">Name</span><span class="sxs-lookup"><span data-stu-id="14013-613">Name</span></span>| <span data-ttu-id="14013-614">Typ</span><span class="sxs-lookup"><span data-stu-id="14013-614">Type</span></span>| <span data-ttu-id="14013-615">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="14013-615">Maximum size</span></span> | <span data-ttu-id="14013-616">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="14013-616">Required</span></span> | <span data-ttu-id="14013-617">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="14013-617">Description</span></span>|
|---|---|---|---|---|
|`team`|<span data-ttu-id="14013-618">string</span><span class="sxs-lookup"><span data-stu-id="14013-618">string</span></span>|||<span data-ttu-id="14013-619">Wenn der ausgewählte Installationsbereich ausgewählt ist, gibt `team` dieses Feld die verfügbare Standardfunktion an.</span><span class="sxs-lookup"><span data-stu-id="14013-619">When the install scope selected is `team`, this field specifies the default capability available.</span></span> <span data-ttu-id="14013-620">Optionen: `tab` , `bot` oder `connector` .</span><span class="sxs-lookup"><span data-stu-id="14013-620">Options: `tab`, `bot`, or `connector`.</span></span>|
|`groupchat`|<span data-ttu-id="14013-621">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="14013-621">string</span></span>|||<span data-ttu-id="14013-622">Wenn der ausgewählte Installationsbereich ausgewählt ist, gibt `groupchat` dieses Feld die verfügbare Standardfunktion an.</span><span class="sxs-lookup"><span data-stu-id="14013-622">When the install scope selected is `groupchat`, this field specifies the default capability available.</span></span> <span data-ttu-id="14013-623">Optionen: `tab` , `bot` oder `connector` .</span><span class="sxs-lookup"><span data-stu-id="14013-623">Options: `tab`, `bot`, or `connector`.</span></span>|
|`meetings`|<span data-ttu-id="14013-624">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="14013-624">string</span></span>|||<span data-ttu-id="14013-625">Wenn der ausgewählte Installationsbereich ausgewählt ist, gibt `meetings` dieses Feld die verfügbare Standardfunktion an.</span><span class="sxs-lookup"><span data-stu-id="14013-625">When the install scope selected is `meetings`, this field specifies the default capability available.</span></span> <span data-ttu-id="14013-626">Optionen: `tab` , `bot` oder `connector` .</span><span class="sxs-lookup"><span data-stu-id="14013-626">Options: `tab`, `bot`, or `connector`.</span></span>|


