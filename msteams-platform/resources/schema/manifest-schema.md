---
title: Manifestschemareferenz
description: Beschreibt das Manifestschema für Microsoft Teams
ms.topic: reference
ms.author: lajanuar
localization_priority: Normal
keywords: Teams-Manifestschema
ms.openlocfilehash: d8427d23ba2caa73cecd173f6d1ef0d041252b3b
ms.sourcegitcommit: e50cdeb6b7f481e12911b2bb74a8da22af0bffac
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/01/2021
ms.locfileid: "52710627"
---
# <a name="reference-manifest-schema-for-microsoft-teams"></a><span data-ttu-id="84c9d-104">Referenz: Manifestschema für Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="84c9d-104">Reference: Manifest schema for Microsoft Teams</span></span>

<span data-ttu-id="84c9d-105">Das Teams beschreibt, wie die App in das Microsoft Teams integriert wird.</span><span class="sxs-lookup"><span data-stu-id="84c9d-105">The Teams manifest describes how the app integrates into the Microsoft Teams product.</span></span> <span data-ttu-id="84c9d-106">Ihr Manifest muss dem schema entsprechen, das unter gehostet [`https://developer.microsoft.com/json-schemas/teams/v1.10/MicrosoftTeams.schema.json`]( https://developer.microsoft.com/json-schemas/teams/v1.10/MicrosoftTeams.schema.json) wird.</span><span class="sxs-lookup"><span data-stu-id="84c9d-106">Your manifest must conform to the schema hosted at [`https://developer.microsoft.com/json-schemas/teams/v1.10/MicrosoftTeams.schema.json`]( https://developer.microsoft.com/json-schemas/teams/v1.10/MicrosoftTeams.schema.json).</span></span> <span data-ttu-id="84c9d-107">Frühere Versionen 1.0, 1.1,..., 1.6 und so weiter werden ebenfalls unterstützt (unter Verwendung von "v1.x" in der URL).</span><span class="sxs-lookup"><span data-stu-id="84c9d-107">Previous versions 1.0, 1.1,..., 1.6, and so on are also supported (using "v1.x" in the URL).</span></span>
<span data-ttu-id="84c9d-108">Weitere Informationen zu den in den einzelnen Versionen vorgenommenen Änderungen finden Sie unter [Manifeständerungsprotokoll](https://github.com/OfficeDev/microsoft-teams-app-schema/releases).</span><span class="sxs-lookup"><span data-stu-id="84c9d-108">For more information on the changes made in each version, see [manifest change log](https://github.com/OfficeDev/microsoft-teams-app-schema/releases).</span></span>

<span data-ttu-id="84c9d-109">Das folgende Schemabeispiel zeigt alle Erweiterbarkeitsoptionen:</span><span class="sxs-lookup"><span data-stu-id="84c9d-109">The following schema sample shows all extensibility options:</span></span>

## <a name="sample-full-manifest"></a><span data-ttu-id="84c9d-110">Beispiel für vollständiges Manifest</span><span class="sxs-lookup"><span data-stu-id="84c9d-110">Sample full manifest</span></span>

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

<span data-ttu-id="84c9d-111">Das Schema definiert die folgenden Eigenschaften:</span><span class="sxs-lookup"><span data-stu-id="84c9d-111">The schema defines the following properties:</span></span>

## <a name="schema"></a><span data-ttu-id="84c9d-112">$schema</span><span class="sxs-lookup"><span data-stu-id="84c9d-112">$schema</span></span>

<span data-ttu-id="84c9d-113">Optional, aber empfohlen – Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="84c9d-113">Optional, but recommended — string</span></span>

<span data-ttu-id="84c9d-114">Die https://-URL, die auf das JSON-Schema für das Manifest verweist.</span><span class="sxs-lookup"><span data-stu-id="84c9d-114">The https:// URL referencing the JSON Schema for the manifest.</span></span>

## <a name="manifestversion"></a><span data-ttu-id="84c9d-115">manifestVersion</span><span class="sxs-lookup"><span data-stu-id="84c9d-115">manifestVersion</span></span>

<span data-ttu-id="84c9d-116">**Erforderlich** – Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="84c9d-116">**Required** — string</span></span>

<span data-ttu-id="84c9d-117">Die Version des Manifestschemas, das dieses Manifest verwendet.</span><span class="sxs-lookup"><span data-stu-id="84c9d-117">The version of manifest schema this manifest is using.</span></span> <span data-ttu-id="84c9d-118">Er muss 1,10 sein.</span><span class="sxs-lookup"><span data-stu-id="84c9d-118">It must be 1.10.</span></span>

## <a name="version"></a><span data-ttu-id="84c9d-119">Version</span><span class="sxs-lookup"><span data-stu-id="84c9d-119">version</span></span>

<span data-ttu-id="84c9d-120">**Erforderlich** – Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="84c9d-120">**Required** — string</span></span>

<span data-ttu-id="84c9d-121">Die Version einer bestimmten App.</span><span class="sxs-lookup"><span data-stu-id="84c9d-121">The version of a specific app.</span></span> <span data-ttu-id="84c9d-122">Wenn Sie etwas in Ihrem Manifest aktualisieren, muss auch die Version erhöht werden.</span><span class="sxs-lookup"><span data-stu-id="84c9d-122">If you update something in your manifest, the version must be incremented too.</span></span> <span data-ttu-id="84c9d-123">Auf diese Weise wird das vorhandene Manifest überschrieben, wenn das neue Manifest installiert wird, und der Benutzer erhält die neue Funktionalität.</span><span class="sxs-lookup"><span data-stu-id="84c9d-123">This way, when the new manifest is installed, it overwrites the existing one and the user receives the new functionality.</span></span> <span data-ttu-id="84c9d-124">Wenn diese App an den Store übermittelt wurde, muss das neue Manifest erneut übermittelt und erneut überprüft werden.</span><span class="sxs-lookup"><span data-stu-id="84c9d-124">If this app was submitted to the store, the new manifest must be re-submitted and re-validated.</span></span> <span data-ttu-id="84c9d-125">Die App-Benutzer erhalten das neue aktualisierte Manifest automatisch innerhalb weniger Stunden nach der Genehmigung des Manifests.</span><span class="sxs-lookup"><span data-stu-id="84c9d-125">The app users receive the new updated manifest automatically within few hours after the manifest is approved.</span></span>

<span data-ttu-id="84c9d-126">Wenn sich die App-Anforderungen für Berechtigungen ändern, werden die Benutzer aufgefordert, ein Upgrade zu starten und der App erneut zu zustimmen.</span><span class="sxs-lookup"><span data-stu-id="84c9d-126">If the app requests for permissions change, the users are prompted to upgrade and re-consent to the app.</span></span>

<span data-ttu-id="84c9d-127">Diese Versionszeichenfolge muss dem [semver-Standard](http://semver.org/) (MAJOR. MINOR. PATCH).</span><span class="sxs-lookup"><span data-stu-id="84c9d-127">This version string must follow the [semver](http://semver.org/) standard (MAJOR.MINOR.PATCH).</span></span>

## <a name="id"></a><span data-ttu-id="84c9d-128">id</span><span class="sxs-lookup"><span data-stu-id="84c9d-128">id</span></span>

<span data-ttu-id="84c9d-129">**Erforderlich** – Microsoft-App-ID</span><span class="sxs-lookup"><span data-stu-id="84c9d-129">**Required** — Microsoft app ID</span></span>

<span data-ttu-id="84c9d-130">Die ID ist ein eindeutiger von Microsoft generierter Bezeichner für die App.</span><span class="sxs-lookup"><span data-stu-id="84c9d-130">The ID is a unique Microsoft-generated identifier for the app.</span></span> <span data-ttu-id="84c9d-131">Sie verfügen über eine ID, wenn Ihr Bot über das Microsoft Bot Framework registriert ist oder sich die Web-App Ihrer Registerkarte bereits bei Microsoft angemeldet hat.</span><span class="sxs-lookup"><span data-stu-id="84c9d-131">You have an ID if your bot is registered through the Microsoft Bot Framework or your tab's web app already signs in with Microsoft.</span></span> <span data-ttu-id="84c9d-132">Sie müssen hier die ID eingeben.</span><span class="sxs-lookup"><span data-stu-id="84c9d-132">You must enter the ID here.</span></span> <span data-ttu-id="84c9d-133">Andernfalls müssen Sie eine neue ID im [Microsoft Application Registration Portal generieren.](https://aka.ms/appregistrations)</span><span class="sxs-lookup"><span data-stu-id="84c9d-133">Otherwise, you must generate a new ID at the [Microsoft Application Registration Portal](https://aka.ms/appregistrations).</span></span> <span data-ttu-id="84c9d-134">Verwenden Sie dieselbe ID, wenn Sie einen Bot hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="84c9d-134">Use the same ID if you add a bot.</span></span>

> [!NOTE]
> <span data-ttu-id="84c9d-135">Wenn Sie ein Update an Ihre vorhandene App in AppSource übermitteln, darf die ID in Ihrem Manifest nicht geändert werden.</span><span class="sxs-lookup"><span data-stu-id="84c9d-135">If you are submitting an update to your existing app in AppSource, the ID in your manifest must not be modified.</span></span>

## <a name="developer"></a><span data-ttu-id="84c9d-136">developer</span><span class="sxs-lookup"><span data-stu-id="84c9d-136">developer</span></span>

<span data-ttu-id="84c9d-137">**Erforderlich** – Objekt</span><span class="sxs-lookup"><span data-stu-id="84c9d-137">**Required** — object</span></span>

<span data-ttu-id="84c9d-138">Gibt Informationen zu Ihrem Unternehmen an.</span><span class="sxs-lookup"><span data-stu-id="84c9d-138">Specifies information about your company.</span></span> <span data-ttu-id="84c9d-139">Für Apps, die an den Teams übermittelt werden, müssen diese Werte mit den Informationen in Ihrem Storeeintrag übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="84c9d-139">For apps submitted to the Teams store, these values must match the information in your store listing.</span></span> <span data-ttu-id="84c9d-140">Weitere Informationen finden Sie unter [Teams Store Publishing Guidelines](~/concepts/deploy-and-publish/appsource/publish.md).</span><span class="sxs-lookup"><span data-stu-id="84c9d-140">For more information, see the [Teams store publishing guidelines](~/concepts/deploy-and-publish/appsource/publish.md).</span></span>

|<span data-ttu-id="84c9d-141">Name</span><span class="sxs-lookup"><span data-stu-id="84c9d-141">Name</span></span>| <span data-ttu-id="84c9d-142">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="84c9d-142">Maximum size</span></span> | <span data-ttu-id="84c9d-143">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="84c9d-143">Required</span></span> | <span data-ttu-id="84c9d-144">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="84c9d-144">Description</span></span>|
|---|---|---|---|
|`name`|<span data-ttu-id="84c9d-145">32 Zeichen</span><span class="sxs-lookup"><span data-stu-id="84c9d-145">32 characters</span></span>|<span data-ttu-id="84c9d-146">✔</span><span class="sxs-lookup"><span data-stu-id="84c9d-146">✔</span></span>|<span data-ttu-id="84c9d-147">Der Anzeigename für den Entwickler.</span><span class="sxs-lookup"><span data-stu-id="84c9d-147">The display name for the developer.</span></span>|
|`websiteUrl`|<span data-ttu-id="84c9d-148">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="84c9d-148">2048 characters</span></span>|<span data-ttu-id="84c9d-149">✔</span><span class="sxs-lookup"><span data-stu-id="84c9d-149">✔</span></span>|<span data-ttu-id="84c9d-150">Die https://-URL zur Website des Entwicklers.</span><span class="sxs-lookup"><span data-stu-id="84c9d-150">The https:// URL to the developer's website.</span></span> <span data-ttu-id="84c9d-151">Dieser Link muss Benutzer zu Ihrer unternehmens- oder produktspezifischen Angebotsseite gelangen.</span><span class="sxs-lookup"><span data-stu-id="84c9d-151">This link must take users to your company or product-specific landing page.</span></span>|
|`privacyUrl`|<span data-ttu-id="84c9d-152">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="84c9d-152">2048 characters</span></span>|<span data-ttu-id="84c9d-153">✔</span><span class="sxs-lookup"><span data-stu-id="84c9d-153">✔</span></span>|<span data-ttu-id="84c9d-154">Die https:// url to the developer's privacy policy.</span><span class="sxs-lookup"><span data-stu-id="84c9d-154">The https:// URL to the developer's privacy policy.</span></span>|
|`termsOfUseUrl`|<span data-ttu-id="84c9d-155">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="84c9d-155">2048 characters</span></span>|<span data-ttu-id="84c9d-156">✔</span><span class="sxs-lookup"><span data-stu-id="84c9d-156">✔</span></span>|<span data-ttu-id="84c9d-157">Die https:// URL zu den Nutzungsbedingungen des Entwicklers.</span><span class="sxs-lookup"><span data-stu-id="84c9d-157">The https:// URL to the developer's terms of use.</span></span>|
|`mpnId`|<span data-ttu-id="84c9d-158">10 Zeichen</span><span class="sxs-lookup"><span data-stu-id="84c9d-158">10 characters</span></span>| |<span data-ttu-id="84c9d-159">**Optional** Die Microsoft Partner Network ID, die die Partnerorganisation identifiziert, die die App erstellt.</span><span class="sxs-lookup"><span data-stu-id="84c9d-159">**Optional** The Microsoft Partner Network ID that identifies the partner organization building the app.</span></span>|

## <a name="name"></a><span data-ttu-id="84c9d-160">name</span><span class="sxs-lookup"><span data-stu-id="84c9d-160">name</span></span>

<span data-ttu-id="84c9d-161">**Erforderlich** – Objekt</span><span class="sxs-lookup"><span data-stu-id="84c9d-161">**Required** — object</span></span>

<span data-ttu-id="84c9d-162">Der Name Ihrer App-Erfahrung, der Benutzern in der Teams angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="84c9d-162">The name of your app experience, displayed to users in the Teams experience.</span></span> <span data-ttu-id="84c9d-163">Für apps submitted to AppSource, these values must match the information in your AppSource entry.</span><span class="sxs-lookup"><span data-stu-id="84c9d-163">For apps submitted to AppSource, these values must match the information in your AppSource entry.</span></span> <span data-ttu-id="84c9d-164">Die Werte von `short` und `full` müssen unterschiedlich sein.</span><span class="sxs-lookup"><span data-stu-id="84c9d-164">The values of `short` and `full` must be different.</span></span>

|<span data-ttu-id="84c9d-165">Name</span><span class="sxs-lookup"><span data-stu-id="84c9d-165">Name</span></span>| <span data-ttu-id="84c9d-166">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="84c9d-166">Maximum size</span></span> | <span data-ttu-id="84c9d-167">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="84c9d-167">Required</span></span> | <span data-ttu-id="84c9d-168">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="84c9d-168">Description</span></span>|
|---|---|---|---|
|`short`|<span data-ttu-id="84c9d-169">30 Zeichen</span><span class="sxs-lookup"><span data-stu-id="84c9d-169">30 characters</span></span>|<span data-ttu-id="84c9d-170">✔</span><span class="sxs-lookup"><span data-stu-id="84c9d-170">✔</span></span>|<span data-ttu-id="84c9d-171">Der kurze Anzeigename für die App.</span><span class="sxs-lookup"><span data-stu-id="84c9d-171">The short display name for the app.</span></span>|
|`full`|<span data-ttu-id="84c9d-172">100 Zeichen</span><span class="sxs-lookup"><span data-stu-id="84c9d-172">100 characters</span></span>||<span data-ttu-id="84c9d-173">Der vollständige Name der App, der verwendet wird, wenn der vollständige Name der App 30 Zeichen überschreitet.</span><span class="sxs-lookup"><span data-stu-id="84c9d-173">The full name of the app, used if the full app name exceeds 30 characters.</span></span>|

## <a name="description"></a><span data-ttu-id="84c9d-174">description</span><span class="sxs-lookup"><span data-stu-id="84c9d-174">description</span></span>

<span data-ttu-id="84c9d-175">**Erforderlich** – Objekt</span><span class="sxs-lookup"><span data-stu-id="84c9d-175">**Required** — object</span></span>

<span data-ttu-id="84c9d-176">Beschreibt Ihre App für Benutzer.</span><span class="sxs-lookup"><span data-stu-id="84c9d-176">Describes your app to users.</span></span> <span data-ttu-id="84c9d-177">Für apps submitted to AppSource, these values must match the information in your AppSource entry.</span><span class="sxs-lookup"><span data-stu-id="84c9d-177">For apps submitted to AppSource, these values must match the information in your AppSource entry.</span></span>

<span data-ttu-id="84c9d-178">Stellen Sie sicher, dass Ihre Beschreibung Ihre Erfahrung genau beschreibt und Informationen enthält, mit deren Hilfe potenzielle Kunden besser verstehen können, was Ihre Erfahrung bedeutet.</span><span class="sxs-lookup"><span data-stu-id="84c9d-178">Ensure that your description accurately describes your experience and provides information to help potential customers understand what your experience does.</span></span> <span data-ttu-id="84c9d-179">Sie müssen in der vollständigen Beschreibung notieren, ob ein externes Konto für die Verwendung erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="84c9d-179">You must note in the full description, if an external account is required for use.</span></span> <span data-ttu-id="84c9d-180">Die Werte von `short` und `full` müssen unterschiedlich sein.</span><span class="sxs-lookup"><span data-stu-id="84c9d-180">The values of `short` and `full` must be different.</span></span> <span data-ttu-id="84c9d-181">Ihre kurze Beschreibung darf nicht innerhalb der langen Beschreibung wiederholt werden und darf keinen anderen App-Namen enthalten.</span><span class="sxs-lookup"><span data-stu-id="84c9d-181">Your short description must not be repeated within the long description and must not include any other app name.</span></span>

|<span data-ttu-id="84c9d-182">Name</span><span class="sxs-lookup"><span data-stu-id="84c9d-182">Name</span></span>| <span data-ttu-id="84c9d-183">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="84c9d-183">Maximum size</span></span> | <span data-ttu-id="84c9d-184">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="84c9d-184">Required</span></span> | <span data-ttu-id="84c9d-185">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="84c9d-185">Description</span></span>|
|---|---|---|---|
|`short`|<span data-ttu-id="84c9d-186">80 Zeichen</span><span class="sxs-lookup"><span data-stu-id="84c9d-186">80 characters</span></span>|<span data-ttu-id="84c9d-187">✔</span><span class="sxs-lookup"><span data-stu-id="84c9d-187">✔</span></span>|<span data-ttu-id="84c9d-188">Eine kurze Beschreibung Ihrer App-Erfahrung, die bei begrenztem Speicherplatz verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="84c9d-188">A short description of your app experience, used when space is limited.</span></span>|
|`full`|<span data-ttu-id="84c9d-189">4000 Zeichen</span><span class="sxs-lookup"><span data-stu-id="84c9d-189">4000 characters</span></span>|<span data-ttu-id="84c9d-190">✔</span><span class="sxs-lookup"><span data-stu-id="84c9d-190">✔</span></span>|<span data-ttu-id="84c9d-191">Die vollständige Beschreibung Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="84c9d-191">The full description of your app.</span></span>|

## <a name="packagename"></a><span data-ttu-id="84c9d-192">packageName</span><span class="sxs-lookup"><span data-stu-id="84c9d-192">packageName</span></span>

<span data-ttu-id="84c9d-193">**Optional –** Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="84c9d-193">**Optional** — string</span></span>

<span data-ttu-id="84c9d-194">Ein eindeutiger Bezeichner für die App in umgekehrter Domänen-Notation; z. B. com.example.myapp.</span><span class="sxs-lookup"><span data-stu-id="84c9d-194">A unique identifier for the app in reverse domain notation; for example, com.example.myapp.</span></span> <span data-ttu-id="84c9d-195">Maximale Länge: 64 Zeichen.</span><span class="sxs-lookup"><span data-stu-id="84c9d-195">Maximum length: 64 characters.</span></span>

## <a name="localizationinfo"></a><span data-ttu-id="84c9d-196">localizationInfo</span><span class="sxs-lookup"><span data-stu-id="84c9d-196">localizationInfo</span></span>

<span data-ttu-id="84c9d-197">**Optional** – -Objekt</span><span class="sxs-lookup"><span data-stu-id="84c9d-197">**Optional** — object</span></span>

<span data-ttu-id="84c9d-198">Ermöglicht die Angabe einer Standardsprache sowie Zeiger auf zusätzliche Sprachdateien.</span><span class="sxs-lookup"><span data-stu-id="84c9d-198">Allows the specification of a default language, as well as pointers to additional language files.</span></span> <span data-ttu-id="84c9d-199">Weitere Informationen finden Sie unter [Lokalisierung](~/concepts/build-and-test/apps-localization.md).</span><span class="sxs-lookup"><span data-stu-id="84c9d-199">For more information, see [localization](~/concepts/build-and-test/apps-localization.md).</span></span>

|<span data-ttu-id="84c9d-200">Name</span><span class="sxs-lookup"><span data-stu-id="84c9d-200">Name</span></span>| <span data-ttu-id="84c9d-201">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="84c9d-201">Maximum size</span></span> | <span data-ttu-id="84c9d-202">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="84c9d-202">Required</span></span> | <span data-ttu-id="84c9d-203">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="84c9d-203">Description</span></span>|
|---|---|---|---|
|`defaultLanguageTag`||<span data-ttu-id="84c9d-204">✔</span><span class="sxs-lookup"><span data-stu-id="84c9d-204">✔</span></span>|<span data-ttu-id="84c9d-205">Das Sprachtag der Zeichenfolgen in dieser Manifestdatei auf oberster Ebene.</span><span class="sxs-lookup"><span data-stu-id="84c9d-205">The language tag of the strings in this top level manifest file.</span></span>|

### <a name="localizationinfoadditionallanguages"></a><span data-ttu-id="84c9d-206">localizationInfo.additionalLanguages</span><span class="sxs-lookup"><span data-stu-id="84c9d-206">localizationInfo.additionalLanguages</span></span>

<span data-ttu-id="84c9d-207">Ein Array von Objekten, die zusätzliche Sprachübersetzungen angeben.</span><span class="sxs-lookup"><span data-stu-id="84c9d-207">An array of objects specifying additional language translations.</span></span>

|<span data-ttu-id="84c9d-208">Name</span><span class="sxs-lookup"><span data-stu-id="84c9d-208">Name</span></span>| <span data-ttu-id="84c9d-209">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="84c9d-209">Maximum size</span></span> | <span data-ttu-id="84c9d-210">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="84c9d-210">Required</span></span> | <span data-ttu-id="84c9d-211">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="84c9d-211">Description</span></span>|
|---|---|---|---|
|`languageTag`||<span data-ttu-id="84c9d-212">✔</span><span class="sxs-lookup"><span data-stu-id="84c9d-212">✔</span></span>|<span data-ttu-id="84c9d-213">Das Sprachtag der Zeichenfolgen in der bereitgestellten Datei.</span><span class="sxs-lookup"><span data-stu-id="84c9d-213">The language tag of the strings in the provided file.</span></span>|
|`file`||<span data-ttu-id="84c9d-214">✔</span><span class="sxs-lookup"><span data-stu-id="84c9d-214">✔</span></span>|<span data-ttu-id="84c9d-215">Ein relativer Dateipfad zu einer .json-Datei, die die übersetzten Zeichenfolgen enthält.</span><span class="sxs-lookup"><span data-stu-id="84c9d-215">A relative file path to a the .json file containing the translated strings.</span></span>|

## <a name="icons"></a><span data-ttu-id="84c9d-216">Symbole</span><span class="sxs-lookup"><span data-stu-id="84c9d-216">icons</span></span>

<span data-ttu-id="84c9d-217">**Erforderlich** – Objekt</span><span class="sxs-lookup"><span data-stu-id="84c9d-217">**Required** — object</span></span>

<span data-ttu-id="84c9d-218">Symbole, die innerhalb der Teams werden.</span><span class="sxs-lookup"><span data-stu-id="84c9d-218">Icons used within the Teams app.</span></span> <span data-ttu-id="84c9d-219">Die Symboldateien müssen als Teil des Uploadpakets enthalten sein.</span><span class="sxs-lookup"><span data-stu-id="84c9d-219">The icon files must be included as part of the upload package.</span></span> <span data-ttu-id="84c9d-220">Weitere Informationen finden Sie unter [Symbole.](../../concepts/build-and-test/apps-package.md#app-icons)</span><span class="sxs-lookup"><span data-stu-id="84c9d-220">See [Icons](../../concepts/build-and-test/apps-package.md#app-icons) for more information.</span></span>

|<span data-ttu-id="84c9d-221">Name</span><span class="sxs-lookup"><span data-stu-id="84c9d-221">Name</span></span>| <span data-ttu-id="84c9d-222">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="84c9d-222">Maximum size</span></span> | <span data-ttu-id="84c9d-223">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="84c9d-223">Required</span></span> | <span data-ttu-id="84c9d-224">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="84c9d-224">Description</span></span>|
|---|---|---|---|
|`outline`|<span data-ttu-id="84c9d-225">32 x 32 Pixel</span><span class="sxs-lookup"><span data-stu-id="84c9d-225">32 x 32 pixels</span></span>|<span data-ttu-id="84c9d-226">✔</span><span class="sxs-lookup"><span data-stu-id="84c9d-226">✔</span></span>|<span data-ttu-id="84c9d-227">Ein relativer Dateipfad zu einem transparenten 32 x 32 PNG-Gliederungssymbol.</span><span class="sxs-lookup"><span data-stu-id="84c9d-227">A relative file path to a transparent 32x32 PNG outline icon.</span></span>|
|`color`|<span data-ttu-id="84c9d-228">192 x 192 Pixel</span><span class="sxs-lookup"><span data-stu-id="84c9d-228">192 x 192 pixels</span></span>|<span data-ttu-id="84c9d-229">✔</span><span class="sxs-lookup"><span data-stu-id="84c9d-229">✔</span></span>|<span data-ttu-id="84c9d-230">Ein relativer Dateipfad zu einem vollfarbigen 192 x 192-PNG-Symbol.</span><span class="sxs-lookup"><span data-stu-id="84c9d-230">A relative file path to a full color 192x192 PNG icon.</span></span>|

## <a name="accentcolor"></a><span data-ttu-id="84c9d-231">accentColor</span><span class="sxs-lookup"><span data-stu-id="84c9d-231">accentColor</span></span>

<span data-ttu-id="84c9d-232">**Optional** – HTML-Hex-Farbcode</span><span class="sxs-lookup"><span data-stu-id="84c9d-232">**Optional** — HTML Hex color code</span></span>

<span data-ttu-id="84c9d-233">Eine Farbe, die in Verbindung mit und als Hintergrund für Ihre Gliederungssymbole verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="84c9d-233">A color to use in conjunction with and as a background for your outline icons.</span></span>

<span data-ttu-id="84c9d-234">Der Wert muss ein gültiger #A0 sein, der mit "#" beginnt, z. B. `#4464ee` .</span><span class="sxs-lookup"><span data-stu-id="84c9d-234">The value must be a valid HTML color code starting with '#', for example `#4464ee`.</span></span>

## <a name="configurabletabs"></a><span data-ttu-id="84c9d-235">configurableTabs</span><span class="sxs-lookup"><span data-stu-id="84c9d-235">configurableTabs</span></span>

<span data-ttu-id="84c9d-236">**Optional** – Array</span><span class="sxs-lookup"><span data-stu-id="84c9d-236">**Optional** — array</span></span>

<span data-ttu-id="84c9d-237">Wird verwendet, wenn Ihre App über eine Registerkartenerfahrung im Teamkanal verfügt, die eine zusätzliche Konfiguration erfordert, bevor sie hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="84c9d-237">Used when your app experience has a team channel tab experience that requires extra configuration before it is added.</span></span> <span data-ttu-id="84c9d-238">Konfigurierbare Registerkarten werden nur im Bereich "Teams" unterstützt, und Sie können dieselben Registerkarten mehrmals konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="84c9d-238">Configurable tabs are supported only in the teams scope and you can configure the same tabs multiple times.</span></span> <span data-ttu-id="84c9d-239">Sie können sie jedoch nur einmal im Manifest definieren.</span><span class="sxs-lookup"><span data-stu-id="84c9d-239">However, you can define it in the manifest only once.</span></span>

|<span data-ttu-id="84c9d-240">Name</span><span class="sxs-lookup"><span data-stu-id="84c9d-240">Name</span></span>| <span data-ttu-id="84c9d-241">Typ</span><span class="sxs-lookup"><span data-stu-id="84c9d-241">Type</span></span>| <span data-ttu-id="84c9d-242">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="84c9d-242">Maximum size</span></span> | <span data-ttu-id="84c9d-243">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="84c9d-243">Required</span></span> | <span data-ttu-id="84c9d-244">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="84c9d-244">Description</span></span>|
|---|---|---|---|---|
|`configurationUrl`|<span data-ttu-id="84c9d-245">string</span><span class="sxs-lookup"><span data-stu-id="84c9d-245">string</span></span>|<span data-ttu-id="84c9d-246">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="84c9d-246">2048 characters</span></span>|<span data-ttu-id="84c9d-247">✔</span><span class="sxs-lookup"><span data-stu-id="84c9d-247">✔</span></span>|<span data-ttu-id="84c9d-248">Die https:// URL, die beim Konfigurieren der Registerkarte verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="84c9d-248">The https:// URL to use when configuring the tab.</span></span>|
|`scopes`|<span data-ttu-id="84c9d-249">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="84c9d-249">array of enums</span></span>|<span data-ttu-id="84c9d-250">1</span><span class="sxs-lookup"><span data-stu-id="84c9d-250">1</span></span>|<span data-ttu-id="84c9d-251">✔</span><span class="sxs-lookup"><span data-stu-id="84c9d-251">✔</span></span>|<span data-ttu-id="84c9d-252">Derzeit unterstützen konfigurierbare Registerkarten nur die `team` Bereiche `groupchat` und.</span><span class="sxs-lookup"><span data-stu-id="84c9d-252">Currently, configurable tabs support only the `team` and `groupchat` scopes.</span></span> |
|`canUpdateConfiguration`|<span data-ttu-id="84c9d-253">Boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="84c9d-253">boolean</span></span>|||<span data-ttu-id="84c9d-254">Ein Wert, der angibt, ob eine Instanz der Registerkartenkonfiguration vom Benutzer nach der Erstellung aktualisiert werden kann.</span><span class="sxs-lookup"><span data-stu-id="84c9d-254">A value indicating whether an instance of the tab's configuration can be updated by the user after creation.</span></span> <span data-ttu-id="84c9d-255">Standard: **true**.</span><span class="sxs-lookup"><span data-stu-id="84c9d-255">Default: **true**.</span></span>|
|`context` |<span data-ttu-id="84c9d-256">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="84c9d-256">array of enums</span></span>|<span data-ttu-id="84c9d-257">6 </span><span class="sxs-lookup"><span data-stu-id="84c9d-257">6</span></span>||<span data-ttu-id="84c9d-258">Der Satz von `contextItem` Bereich, in [dem eine Registerkarte unterstützt wird.](../../tabs/how-to/access-teams-context.md)</span><span class="sxs-lookup"><span data-stu-id="84c9d-258">The set of `contextItem` scopes where a [tab is supported](../../tabs/how-to/access-teams-context.md).</span></span> <span data-ttu-id="84c9d-259">Standard: **[channelTab, privateChatTab, meetingChatTab, meetingDetailsTab]**.</span><span class="sxs-lookup"><span data-stu-id="84c9d-259">Default: **[channelTab, privateChatTab, meetingChatTab, meetingDetailsTab]**.</span></span>|
|`sharePointPreviewImage`|<span data-ttu-id="84c9d-260">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="84c9d-260">string</span></span>|<span data-ttu-id="84c9d-261">2048</span><span class="sxs-lookup"><span data-stu-id="84c9d-261">2048</span></span>||<span data-ttu-id="84c9d-262">Ein relativer Dateipfad zu einem Registerkartenvorschaubild zur Verwendung in SharePoint.</span><span class="sxs-lookup"><span data-stu-id="84c9d-262">A relative file path to a tab preview image for use in SharePoint.</span></span> <span data-ttu-id="84c9d-263">Größe 1024 x 768.</span><span class="sxs-lookup"><span data-stu-id="84c9d-263">Size 1024x768.</span></span> |
|`supportedSharePointHosts`|<span data-ttu-id="84c9d-264">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="84c9d-264">array of enums</span></span>|<span data-ttu-id="84c9d-265">1</span><span class="sxs-lookup"><span data-stu-id="84c9d-265">1</span></span>||<span data-ttu-id="84c9d-266">Definiert, wie Ihre Registerkarte in der SharePoint.</span><span class="sxs-lookup"><span data-stu-id="84c9d-266">Defines how your tab is made available in SharePoint.</span></span> <span data-ttu-id="84c9d-267">Optionen sind `sharePointFullPage` und `sharePointWebPart`</span><span class="sxs-lookup"><span data-stu-id="84c9d-267">Options are `sharePointFullPage` and `sharePointWebPart`</span></span> |

## <a name="statictabs"></a><span data-ttu-id="84c9d-268">staticTabs</span><span class="sxs-lookup"><span data-stu-id="84c9d-268">staticTabs</span></span>

<span data-ttu-id="84c9d-269">**Optional** – Array</span><span class="sxs-lookup"><span data-stu-id="84c9d-269">**Optional** — array</span></span>

<span data-ttu-id="84c9d-270">Definiert eine Reihe von Registerkarten, die standardmäßig angeheftet werden können, ohne dass der Benutzer sie manuell hinzufügungen muss.</span><span class="sxs-lookup"><span data-stu-id="84c9d-270">Defines a set of tabs that can be "pinned" by default, without the user adding them manually.</span></span> <span data-ttu-id="84c9d-271">Statische Registerkarten, die im Bereich deklariert sind, werden immer an die persönliche Be benutzererfahrung `personal` der App angeheftet.</span><span class="sxs-lookup"><span data-stu-id="84c9d-271">Static tabs declared in `personal` scope are always pinned to the app's personal experience.</span></span> <span data-ttu-id="84c9d-272">Statische Registerkarten, die im Bereich `team` deklariert sind, werden derzeit nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="84c9d-272">Static tabs declared in the `team` scope are currently not supported.</span></span>

<span data-ttu-id="84c9d-273">Dieses Element ist ein Array (maximal 16 Elemente) mit allen Elementen des Typs `object` .</span><span class="sxs-lookup"><span data-stu-id="84c9d-273">This item is an array (maximum of 16 elements) with all elements of the type `object`.</span></span> <span data-ttu-id="84c9d-274">Dieser Block ist nur für Lösungen erforderlich, die eine statische Registerkartenlösung bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="84c9d-274">This block is required only for solutions that provide a static tab solution.</span></span>

|<span data-ttu-id="84c9d-275">Name</span><span class="sxs-lookup"><span data-stu-id="84c9d-275">Name</span></span>| <span data-ttu-id="84c9d-276">Typ</span><span class="sxs-lookup"><span data-stu-id="84c9d-276">Type</span></span>| <span data-ttu-id="84c9d-277">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="84c9d-277">Maximum size</span></span> | <span data-ttu-id="84c9d-278">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="84c9d-278">Required</span></span> | <span data-ttu-id="84c9d-279">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="84c9d-279">Description</span></span>|
|---|---|---|---|---|
|`entityId`|<span data-ttu-id="84c9d-280">string</span><span class="sxs-lookup"><span data-stu-id="84c9d-280">string</span></span>|<span data-ttu-id="84c9d-281">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="84c9d-281">64 characters</span></span>|<span data-ttu-id="84c9d-282">✔</span><span class="sxs-lookup"><span data-stu-id="84c9d-282">✔</span></span>|<span data-ttu-id="84c9d-283">Ein eindeutiger Bezeichner für die Entität, die auf der Registerkarte angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="84c9d-283">A unique identifier for the entity that the tab displays.</span></span>|
|`name`|<span data-ttu-id="84c9d-284">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="84c9d-284">string</span></span>|<span data-ttu-id="84c9d-285">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="84c9d-285">128 characters</span></span>|<span data-ttu-id="84c9d-286">✔</span><span class="sxs-lookup"><span data-stu-id="84c9d-286">✔</span></span>|<span data-ttu-id="84c9d-287">Der Anzeigename der Registerkarte in der Kanalschnittstelle.</span><span class="sxs-lookup"><span data-stu-id="84c9d-287">The display name of the tab in the channel interface.</span></span>|
|`contentUrl`|<span data-ttu-id="84c9d-288">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="84c9d-288">string</span></span>||<span data-ttu-id="84c9d-289">✔</span><span class="sxs-lookup"><span data-stu-id="84c9d-289">✔</span></span>|<span data-ttu-id="84c9d-290">Die https://-URL, die auf die Entitätsbenutzeroberfläche verweist, die im Zeichenbereich Teams werden soll.</span><span class="sxs-lookup"><span data-stu-id="84c9d-290">The https:// URL that points to the entity UI to be displayed in the Teams canvas.</span></span>|
|`websiteUrl`|<span data-ttu-id="84c9d-291">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="84c9d-291">string</span></span>|||<span data-ttu-id="84c9d-292">Die https:// URL, auf die verweisen soll, wenn sich ein Benutzer für die Anzeige in einem Browser entscheidet.</span><span class="sxs-lookup"><span data-stu-id="84c9d-292">The https:// URL to point to if a user opts to view in a browser.</span></span>|
|`searchUrl`|<span data-ttu-id="84c9d-293">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="84c9d-293">string</span></span>|||<span data-ttu-id="84c9d-294">Die https:// URL, auf die für die Suchabfragen eines Benutzers verweisen soll.</span><span class="sxs-lookup"><span data-stu-id="84c9d-294">The https:// URL to point to for a user's search queries.</span></span>|
|`scopes`|<span data-ttu-id="84c9d-295">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="84c9d-295">array of enums</span></span>|<span data-ttu-id="84c9d-296">1</span><span class="sxs-lookup"><span data-stu-id="84c9d-296">1</span></span>|<span data-ttu-id="84c9d-297">✔</span><span class="sxs-lookup"><span data-stu-id="84c9d-297">✔</span></span>|<span data-ttu-id="84c9d-298">Derzeit unterstützen statische Registerkarten nur den Bereich, d. h., er kann nur als Teil der `personal` persönlichen Erfahrung bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="84c9d-298">Currently, static tabs support only the `personal` scope, which means it can be provisioned only as part of the personal experience.</span></span>|
|`context` | <span data-ttu-id="84c9d-299">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="84c9d-299">array of enums</span></span>| <span data-ttu-id="84c9d-300">2</span><span class="sxs-lookup"><span data-stu-id="84c9d-300">2</span></span>|| <span data-ttu-id="84c9d-301">Der Satz von `contextItem` Bereich, in dem eine Registerkarte unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="84c9d-301">The set of `contextItem` scopes where a tab is supported.</span></span>|

> [!NOTE]
>  <span data-ttu-id="84c9d-302">Das searchUrl-Feature ist für Drittanbieterentwickler nicht verfügbar.</span><span class="sxs-lookup"><span data-stu-id="84c9d-302">The searchUrl feature is not available for the third-party developers.</span></span>
> <span data-ttu-id="84c9d-303">Wenn Ihre Registerkarten kontextabhängige Informationen zum Anzeigen relevanter Inhalte oder zum Initiieren eines Authentifizierungsflusses benötigen, finden Sie weitere Informationen unter [Get context for your Microsoft Teams tab](../../tabs/how-to/access-teams-context.md).</span><span class="sxs-lookup"><span data-stu-id="84c9d-303">If your tabs require context-dependent information to display relevant content or for initiating an authentication flow, For more information, see [Get context for your Microsoft Teams tab](../../tabs/how-to/access-teams-context.md).</span></span>

## <a name="bots"></a><span data-ttu-id="84c9d-304">Bots</span><span class="sxs-lookup"><span data-stu-id="84c9d-304">bots</span></span>

<span data-ttu-id="84c9d-305">**Optional** – Array</span><span class="sxs-lookup"><span data-stu-id="84c9d-305">**Optional** — array</span></span>

<span data-ttu-id="84c9d-306">Definiert eine Botlösung zusammen mit optionalen Informationen, z. B. Standardbefehlseigenschaften.</span><span class="sxs-lookup"><span data-stu-id="84c9d-306">Defines a bot solution, along with optional information such as default command properties.</span></span>

<span data-ttu-id="84c9d-307">Das Element ist ein Array (maximal 1 Element ist derzeit nur ein Bot pro App zulässig) mit allen Elementen &mdash; des Typs `object` .</span><span class="sxs-lookup"><span data-stu-id="84c9d-307">The item is an array (maximum of only 1 element&mdash;currently only one bot is allowed per app) with all elements of the type `object`.</span></span> <span data-ttu-id="84c9d-308">Dieser Block ist nur für Lösungen erforderlich, die eine Boterfahrung bieten.</span><span class="sxs-lookup"><span data-stu-id="84c9d-308">This block is required only for solutions that provide a bot experience.</span></span>

|<span data-ttu-id="84c9d-309">Name</span><span class="sxs-lookup"><span data-stu-id="84c9d-309">Name</span></span>| <span data-ttu-id="84c9d-310">Typ</span><span class="sxs-lookup"><span data-stu-id="84c9d-310">Type</span></span>| <span data-ttu-id="84c9d-311">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="84c9d-311">Maximum size</span></span> | <span data-ttu-id="84c9d-312">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="84c9d-312">Required</span></span> | <span data-ttu-id="84c9d-313">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="84c9d-313">Description</span></span>|
|---|---|---|---|---|
|`botId`|<span data-ttu-id="84c9d-314">string</span><span class="sxs-lookup"><span data-stu-id="84c9d-314">string</span></span>|<span data-ttu-id="84c9d-315">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="84c9d-315">64 characters</span></span>|<span data-ttu-id="84c9d-316">✔</span><span class="sxs-lookup"><span data-stu-id="84c9d-316">✔</span></span>|<span data-ttu-id="84c9d-317">Die eindeutige Microsoft-App-ID für den Bot, wie bei Bot Framework registriert.</span><span class="sxs-lookup"><span data-stu-id="84c9d-317">The unique Microsoft app ID for the bot as registered with the Bot Framework.</span></span> <span data-ttu-id="84c9d-318">Dies kann mit der allgemeinen [App-ID identisch sein.](#id)</span><span class="sxs-lookup"><span data-stu-id="84c9d-318">This may well be the same as the overall [app ID](#id).</span></span>|
|`scopes`|<span data-ttu-id="84c9d-319">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="84c9d-319">array of enums</span></span>|<span data-ttu-id="84c9d-320">3</span><span class="sxs-lookup"><span data-stu-id="84c9d-320">3</span></span>|<span data-ttu-id="84c9d-321">✔</span><span class="sxs-lookup"><span data-stu-id="84c9d-321">✔</span></span>|<span data-ttu-id="84c9d-322">Gibt an, ob der Bot eine Umgebung im Kontext eines Kanals in einem `team` oder Gruppenchat (`groupchat`) ist, oder aber eine Umgebung einzig für einen bestimmten Benutzer (`personal`).</span><span class="sxs-lookup"><span data-stu-id="84c9d-322">Specifies whether the bot offers an experience in the context of a channel in a `team`, in a group chat (`groupchat`), or an experience scoped to an individual user alone (`personal`).</span></span> <span data-ttu-id="84c9d-323">Diese Optionen sind nicht exklusiv.</span><span class="sxs-lookup"><span data-stu-id="84c9d-323">These options are non-exclusive.</span></span>|
|`needsChannelSelector`|<span data-ttu-id="84c9d-324">Boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="84c9d-324">boolean</span></span>|||<span data-ttu-id="84c9d-325">Beschreibt, ob der Bot einen Benutzerhinweis verwendet, um den Bot einem bestimmten Kanal hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="84c9d-325">Describes whether or not the bot utilizes a user hint to add the bot to a specific channel.</span></span> <span data-ttu-id="84c9d-326">Standard: **`false`**</span><span class="sxs-lookup"><span data-stu-id="84c9d-326">Default: **`false`**</span></span>|
|`isNotificationOnly`|<span data-ttu-id="84c9d-327">Boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="84c9d-327">boolean</span></span>|||<span data-ttu-id="84c9d-328">Gibt an, ob ein Bot ein unidirektionaler Bot ausschließlich für Benachrichtigungen ist (im Gegensatz zu einem dialogorientierten Bot).</span><span class="sxs-lookup"><span data-stu-id="84c9d-328">Indicates whether a bot is a one-way, notification-only bot, as opposed to a conversational bot.</span></span> <span data-ttu-id="84c9d-329">Standard: **`false`**</span><span class="sxs-lookup"><span data-stu-id="84c9d-329">Default: **`false`**</span></span>|
|`supportsFiles`|<span data-ttu-id="84c9d-330">Boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="84c9d-330">boolean</span></span>|||<span data-ttu-id="84c9d-331">Gibt an, ob der Bot die Möglichkeit zum Hochladen/Herunterladen von Dateien in persönliche Chats unterstützt.</span><span class="sxs-lookup"><span data-stu-id="84c9d-331">Indicates whether the bot supports the ability to upload/download files in personal chat.</span></span> <span data-ttu-id="84c9d-332">Standard: **`false`**</span><span class="sxs-lookup"><span data-stu-id="84c9d-332">Default: **`false`**</span></span>|
|`supportsCalling`|<span data-ttu-id="84c9d-333">Boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="84c9d-333">boolean</span></span>|||<span data-ttu-id="84c9d-334">Ein Wert, der angibt, wo ein Bot Audioanrufe unterstützt.</span><span class="sxs-lookup"><span data-stu-id="84c9d-334">A value indicating where a bot supports audio calling.</span></span> <span data-ttu-id="84c9d-335">**WICHTIG**: Diese Eigenschaft ist derzeit experimentell.</span><span class="sxs-lookup"><span data-stu-id="84c9d-335">**IMPORTANT**: This property is currently experimental.</span></span> <span data-ttu-id="84c9d-336">Experimentelle Eigenschaften sind möglicherweise nicht vollständig und werden möglicherweise geändert, bevor sie vollständig verfügbar werden.</span><span class="sxs-lookup"><span data-stu-id="84c9d-336">Experimental properties may not be complete, and may undergo changes before becoming fully available.</span></span>  <span data-ttu-id="84c9d-337">Es wird nur zu Test- und Explorationszwecken bereitgestellt und darf nicht in Produktionsanwendungen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="84c9d-337">It is provided for testing and exploration purposes only and must not be used in production applications.</span></span> <span data-ttu-id="84c9d-338">Standard: **`false`**</span><span class="sxs-lookup"><span data-stu-id="84c9d-338">Default: **`false`**</span></span>|
|`supportsVideo`|<span data-ttu-id="84c9d-339">Boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="84c9d-339">boolean</span></span>|||<span data-ttu-id="84c9d-340">Ein Wert, der angibt, wo ein Bot Videoanrufe unterstützt.</span><span class="sxs-lookup"><span data-stu-id="84c9d-340">A value indicating where a bot supports video calling.</span></span> <span data-ttu-id="84c9d-341">**WICHTIG**: Diese Eigenschaft ist derzeit experimentell.</span><span class="sxs-lookup"><span data-stu-id="84c9d-341">**IMPORTANT**: This property is currently experimental.</span></span> <span data-ttu-id="84c9d-342">Experimentelle Eigenschaften sind möglicherweise nicht vollständig und werden möglicherweise geändert, bevor sie vollständig verfügbar werden.</span><span class="sxs-lookup"><span data-stu-id="84c9d-342">Experimental properties may not be complete, and may undergo changes before becoming fully available.</span></span>  <span data-ttu-id="84c9d-343">Es wird nur zu Test- und Explorationszwecken bereitgestellt und darf nicht in Produktionsanwendungen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="84c9d-343">It is provided for testing and exploration purposes only and must not be used in production applications.</span></span> <span data-ttu-id="84c9d-344">Standard: **`false`**</span><span class="sxs-lookup"><span data-stu-id="84c9d-344">Default: **`false`**</span></span>|

### <a name="botscommandlists"></a><span data-ttu-id="84c9d-345">bots.commandLists</span><span class="sxs-lookup"><span data-stu-id="84c9d-345">bots.commandLists</span></span>

<span data-ttu-id="84c9d-346">Eine optionale Liste von Befehlen, die Ihr Bot Benutzern empfehlen kann.</span><span class="sxs-lookup"><span data-stu-id="84c9d-346">An optional list of commands that your bot can recommend to users.</span></span> <span data-ttu-id="84c9d-347">Das Objekt ist ein Array (maximal 2 Elemente) mit allen Elementen des Typs. Sie müssen eine separate Befehlsliste für jeden Bereich definieren, den `object` Ihr Bot unterstützt.</span><span class="sxs-lookup"><span data-stu-id="84c9d-347">The object is an array (maximum of 2 elements) with all elements of type `object`; you must define a separate command list for each scope that your bot supports.</span></span> <span data-ttu-id="84c9d-348">Weitere [Informationen finden Sie unter Bot-Menüs.](~/bots/how-to/create-a-bot-commands-menu.md)</span><span class="sxs-lookup"><span data-stu-id="84c9d-348">See [Bot menus](~/bots/how-to/create-a-bot-commands-menu.md) for more information.</span></span>

|<span data-ttu-id="84c9d-349">Name</span><span class="sxs-lookup"><span data-stu-id="84c9d-349">Name</span></span>| <span data-ttu-id="84c9d-350">Typ</span><span class="sxs-lookup"><span data-stu-id="84c9d-350">Type</span></span>| <span data-ttu-id="84c9d-351">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="84c9d-351">Maximum size</span></span> | <span data-ttu-id="84c9d-352">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="84c9d-352">Required</span></span> | <span data-ttu-id="84c9d-353">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="84c9d-353">Description</span></span>|
|---|---|---|---|---|
|`items.scopes`|<span data-ttu-id="84c9d-354">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="84c9d-354">array of enums</span></span>|<span data-ttu-id="84c9d-355">3</span><span class="sxs-lookup"><span data-stu-id="84c9d-355">3</span></span>|<span data-ttu-id="84c9d-356">✔</span><span class="sxs-lookup"><span data-stu-id="84c9d-356">✔</span></span>|<span data-ttu-id="84c9d-357">Gibt den Bereich an, für den die Befehlsliste gültig ist.</span><span class="sxs-lookup"><span data-stu-id="84c9d-357">Specifies the scope for which the command list is valid.</span></span> <span data-ttu-id="84c9d-358">Mögliche Optionen sind `team`, `personal` und `groupchat`.</span><span class="sxs-lookup"><span data-stu-id="84c9d-358">Options are `team`, `personal`, and `groupchat`.</span></span>|
|`items.commands`|<span data-ttu-id="84c9d-359">Array von Objekten</span><span class="sxs-lookup"><span data-stu-id="84c9d-359">array of objects</span></span>|<span data-ttu-id="84c9d-360">10</span><span class="sxs-lookup"><span data-stu-id="84c9d-360">10</span></span>|<span data-ttu-id="84c9d-361">✔</span><span class="sxs-lookup"><span data-stu-id="84c9d-361">✔</span></span>|<span data-ttu-id="84c9d-362">Ein Array von Befehlen, die der Bot unterstützt:</span><span class="sxs-lookup"><span data-stu-id="84c9d-362">An array of commands the bot supports:</span></span><br><span data-ttu-id="84c9d-363">`title`: Name des Bot-Befehls (string, 32)</span><span class="sxs-lookup"><span data-stu-id="84c9d-363">`title`: the bot command name (string, 32)</span></span><br><span data-ttu-id="84c9d-364">`description`: eine einfache Beschreibung oder ein Beispiel für die Befehlssyntax und ihr Argument (Zeichenfolge, 128).</span><span class="sxs-lookup"><span data-stu-id="84c9d-364">`description`: a simple description or example of the command syntax and its argument (string, 128).</span></span>|

### <a name="botscommandlistscommands"></a><span data-ttu-id="84c9d-365">bots.commandLists.commands</span><span class="sxs-lookup"><span data-stu-id="84c9d-365">bots.commandLists.commands</span></span>

|<span data-ttu-id="84c9d-366">Name</span><span class="sxs-lookup"><span data-stu-id="84c9d-366">Name</span></span>| <span data-ttu-id="84c9d-367">Typ</span><span class="sxs-lookup"><span data-stu-id="84c9d-367">Type</span></span>| <span data-ttu-id="84c9d-368">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="84c9d-368">Maximum size</span></span> | <span data-ttu-id="84c9d-369">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="84c9d-369">Required</span></span> | <span data-ttu-id="84c9d-370">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="84c9d-370">Description</span></span>|
|---|---|---|---|---|
|<span data-ttu-id="84c9d-371">title</span><span class="sxs-lookup"><span data-stu-id="84c9d-371">title</span></span>|<span data-ttu-id="84c9d-372">string</span><span class="sxs-lookup"><span data-stu-id="84c9d-372">string</span></span>|<span data-ttu-id="84c9d-373">12 </span><span class="sxs-lookup"><span data-stu-id="84c9d-373">12</span></span>|<span data-ttu-id="84c9d-374">✔</span><span class="sxs-lookup"><span data-stu-id="84c9d-374">✔</span></span>|<span data-ttu-id="84c9d-375">Der Name des Bot-Befehls.</span><span class="sxs-lookup"><span data-stu-id="84c9d-375">The bot command name.</span></span>|
|<span data-ttu-id="84c9d-376">description</span><span class="sxs-lookup"><span data-stu-id="84c9d-376">description</span></span>|<span data-ttu-id="84c9d-377">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="84c9d-377">string</span></span>|<span data-ttu-id="84c9d-378">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="84c9d-378">128 characters</span></span>|<span data-ttu-id="84c9d-379">✔</span><span class="sxs-lookup"><span data-stu-id="84c9d-379">✔</span></span>|<span data-ttu-id="84c9d-380">Eine einfache Textbeschreibung oder ein Beispiel für die Befehlssyntax und deren Argumente.</span><span class="sxs-lookup"><span data-stu-id="84c9d-380">A simple text description or an example of the command syntax and its arguments.</span></span>|

## <a name="connectors"></a><span data-ttu-id="84c9d-381">Connectors</span><span class="sxs-lookup"><span data-stu-id="84c9d-381">connectors</span></span>

<span data-ttu-id="84c9d-382">**Optional** – Array</span><span class="sxs-lookup"><span data-stu-id="84c9d-382">**Optional** — array</span></span>

<span data-ttu-id="84c9d-383">Der `connectors` Block definiert einen Office 365 Connector für die App.</span><span class="sxs-lookup"><span data-stu-id="84c9d-383">The `connectors` block defines an Office 365 Connector for the app.</span></span>

<span data-ttu-id="84c9d-384">Das Objekt ist ein Array (maximal 1 Element) mit allen Elementen vom Typ `object` .</span><span class="sxs-lookup"><span data-stu-id="84c9d-384">The object is an array (maximum of 1 element) with all elements of type `object`.</span></span> <span data-ttu-id="84c9d-385">Dieser Block ist nur für Lösungen erforderlich, die einen Connector bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="84c9d-385">This block is required only for solutions that provide a Connector.</span></span>

|<span data-ttu-id="84c9d-386">Name</span><span class="sxs-lookup"><span data-stu-id="84c9d-386">Name</span></span>| <span data-ttu-id="84c9d-387">Typ</span><span class="sxs-lookup"><span data-stu-id="84c9d-387">Type</span></span>| <span data-ttu-id="84c9d-388">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="84c9d-388">Maximum size</span></span> | <span data-ttu-id="84c9d-389">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="84c9d-389">Required</span></span> | <span data-ttu-id="84c9d-390">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="84c9d-390">Description</span></span>|
|---|---|---|---|---|
|`configurationUrl`|<span data-ttu-id="84c9d-391">string</span><span class="sxs-lookup"><span data-stu-id="84c9d-391">string</span></span>|<span data-ttu-id="84c9d-392">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="84c9d-392">2048 characters</span></span>|<span data-ttu-id="84c9d-393">✔</span><span class="sxs-lookup"><span data-stu-id="84c9d-393">✔</span></span>|<span data-ttu-id="84c9d-394">Die https://-URL, die beim Konfigurieren des Connectors verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="84c9d-394">The https:// URL to use when configuring the connector.</span></span>|
|`scopes`|<span data-ttu-id="84c9d-395">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="84c9d-395">array of enums</span></span>|<span data-ttu-id="84c9d-396">1</span><span class="sxs-lookup"><span data-stu-id="84c9d-396">1</span></span>|<span data-ttu-id="84c9d-397">✔</span><span class="sxs-lookup"><span data-stu-id="84c9d-397">✔</span></span>|<span data-ttu-id="84c9d-398">Gibt an, ob der Connector eine Benutzeroberfläche im Kontext eines Kanals in einem oder eine Benutzeroberfläche bietet, die auf einen einzelnen Benutzer `team` begrenzt ist ( `personal` ).</span><span class="sxs-lookup"><span data-stu-id="84c9d-398">Specifies whether the Connector offers an experience in the context of a channel in a `team`, or an experience scoped to an individual user alone (`personal`).</span></span> <span data-ttu-id="84c9d-399">Derzeit wird nur `team` der Bereich unterstützt.</span><span class="sxs-lookup"><span data-stu-id="84c9d-399">Currently, only the `team` scope is supported.</span></span>|
|`connectorId`|<span data-ttu-id="84c9d-400">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="84c9d-400">string</span></span>|<span data-ttu-id="84c9d-401">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="84c9d-401">64 characters</span></span>|<span data-ttu-id="84c9d-402">✔</span><span class="sxs-lookup"><span data-stu-id="84c9d-402">✔</span></span>|<span data-ttu-id="84c9d-403">Ein eindeutiger Bezeichner für den Connector, der seiner ID im [Connectors Developer Dashboard entspricht.](https://aka.ms/connectorsdashboard)</span><span class="sxs-lookup"><span data-stu-id="84c9d-403">A unique identifier for the Connector that matches its ID in the [Connectors Developer Dashboard](https://aka.ms/connectorsdashboard).</span></span>|

## <a name="composeextensions"></a><span data-ttu-id="84c9d-404">composeExtensions</span><span class="sxs-lookup"><span data-stu-id="84c9d-404">composeExtensions</span></span>

<span data-ttu-id="84c9d-405">**Optional** – Array</span><span class="sxs-lookup"><span data-stu-id="84c9d-405">**Optional** — array</span></span>

<span data-ttu-id="84c9d-406">Definiert eine Messagingerweiterung für die App.</span><span class="sxs-lookup"><span data-stu-id="84c9d-406">Defines a messaging extension for the app.</span></span>

> [!NOTE]
> <span data-ttu-id="84c9d-407">Der Name des Features wurde im November 2017 von "Verfassenerweiterung" in "Messagingerweiterung" geändert, der Manifestname bleibt jedoch unverändert, damit vorhandene Erweiterungen weiterhin funktionieren.</span><span class="sxs-lookup"><span data-stu-id="84c9d-407">The name of the feature was changed from "compose extension" to "messaging extension" in November, 2017, but the manifest name remains the same so that existing extensions continue to function.</span></span>

<span data-ttu-id="84c9d-408">Das Element ist ein Array (maximal 1 Element) mit allen Elementen vom Typ `object` .</span><span class="sxs-lookup"><span data-stu-id="84c9d-408">The item is an array (maximum of 1 element) with all elements of type `object`.</span></span> <span data-ttu-id="84c9d-409">Dieser Block ist nur für Lösungen erforderlich, die eine Messagingerweiterung bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="84c9d-409">This block is required only for solutions that provide a messaging extension.</span></span>

|<span data-ttu-id="84c9d-410">Name</span><span class="sxs-lookup"><span data-stu-id="84c9d-410">Name</span></span>| <span data-ttu-id="84c9d-411">Typ</span><span class="sxs-lookup"><span data-stu-id="84c9d-411">Type</span></span> | <span data-ttu-id="84c9d-412">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="84c9d-412">Maximum Size</span></span> | <span data-ttu-id="84c9d-413">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="84c9d-413">Required</span></span> | <span data-ttu-id="84c9d-414">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="84c9d-414">Description</span></span>|
|---|---|---|---|---|
|`botId`|<span data-ttu-id="84c9d-415">string</span><span class="sxs-lookup"><span data-stu-id="84c9d-415">string</span></span>|<span data-ttu-id="84c9d-416">64</span><span class="sxs-lookup"><span data-stu-id="84c9d-416">64</span></span>|<span data-ttu-id="84c9d-417">✔</span><span class="sxs-lookup"><span data-stu-id="84c9d-417">✔</span></span>|<span data-ttu-id="84c9d-418">Die eindeutige Microsoft-App-ID für den Bot, der die Messagingerweiterung unterstützt, wie beim Bot Framework registriert.</span><span class="sxs-lookup"><span data-stu-id="84c9d-418">The unique Microsoft app ID for the bot that backs the messaging extension, as registered with the Bot Framework.</span></span> <span data-ttu-id="84c9d-419">Dies kann mit der allgemeinen App-ID identisch sein.</span><span class="sxs-lookup"><span data-stu-id="84c9d-419">This may well be the same as the overall App ID.</span></span>|
|`commands`|<span data-ttu-id="84c9d-420">Array von Objekten</span><span class="sxs-lookup"><span data-stu-id="84c9d-420">array of objects</span></span>|<span data-ttu-id="84c9d-421">10</span><span class="sxs-lookup"><span data-stu-id="84c9d-421">10</span></span>|<span data-ttu-id="84c9d-422">✔</span><span class="sxs-lookup"><span data-stu-id="84c9d-422">✔</span></span>|<span data-ttu-id="84c9d-423">Array von Befehlen, die von der Messagingerweiterung unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="84c9d-423">Array of commands the messaging extension supports.</span></span>|
|`canUpdateConfiguration`|<span data-ttu-id="84c9d-424">Boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="84c9d-424">boolean</span></span>|||<span data-ttu-id="84c9d-425">Ein Wert, der angibt, ob die Konfiguration einer Messagingerweiterung vom Benutzer aktualisiert werden kann.</span><span class="sxs-lookup"><span data-stu-id="84c9d-425">A value indicating whether the configuration of a messaging extension can be updated by the user.</span></span> <span data-ttu-id="84c9d-426">Standard: **False**.</span><span class="sxs-lookup"><span data-stu-id="84c9d-426">Default: **false**.</span></span>|
|`messageHandlers`|<span data-ttu-id="84c9d-427">Array von Objekten</span><span class="sxs-lookup"><span data-stu-id="84c9d-427">array of Objects</span></span>|<span data-ttu-id="84c9d-428">5 </span><span class="sxs-lookup"><span data-stu-id="84c9d-428">5</span></span>||<span data-ttu-id="84c9d-429">Eine Liste von Handlern, mit denen Apps aufgerufen werden können, wenn bestimmte Bedingungen erfüllt sind.</span><span class="sxs-lookup"><span data-stu-id="84c9d-429">A list of handlers that allow apps to be invoked when certain conditions are met.</span></span>|
|`messageHandlers.type`|<span data-ttu-id="84c9d-430">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="84c9d-430">string</span></span>|||<span data-ttu-id="84c9d-431">Der Typ des Nachrichtenhandlers.</span><span class="sxs-lookup"><span data-stu-id="84c9d-431">The type of message handler.</span></span> <span data-ttu-id="84c9d-432">Muss `"link"` sein.</span><span class="sxs-lookup"><span data-stu-id="84c9d-432">Must be `"link"`.</span></span>|
|`messageHandlers.value.domains`|<span data-ttu-id="84c9d-433">Array von Zeichenfolgen</span><span class="sxs-lookup"><span data-stu-id="84c9d-433">array of Strings</span></span>|||<span data-ttu-id="84c9d-434">Array von Domänen, für die der Linknachrichtenhandler registrieren kann.</span><span class="sxs-lookup"><span data-stu-id="84c9d-434">Array of domains that the link message handler can register for.</span></span>|

### <a name="composeextensionscommands"></a><span data-ttu-id="84c9d-435">composeExtensions.commands</span><span class="sxs-lookup"><span data-stu-id="84c9d-435">composeExtensions.commands</span></span>

<span data-ttu-id="84c9d-436">Ihre Messagingerweiterung muss einen oder mehrere Befehle deklarieren.</span><span class="sxs-lookup"><span data-stu-id="84c9d-436">Your messaging extension must declare one or more commands.</span></span> <span data-ttu-id="84c9d-437">Jeder Befehl wird in Microsoft Teams als potenzielle Interaktion vom benutzeroberflächenbasierten Einstiegspunkt angezeigt.</span><span class="sxs-lookup"><span data-stu-id="84c9d-437">Each command appears in Microsoft Teams as a potential interaction from the UI-based entry point.</span></span> <span data-ttu-id="84c9d-438">Es gibt maximal 10 Befehle.</span><span class="sxs-lookup"><span data-stu-id="84c9d-438">There is a maximum of 10 commands.</span></span>

<span data-ttu-id="84c9d-439">Jedes Befehlselement ist ein Objekt mit der folgenden Struktur:</span><span class="sxs-lookup"><span data-stu-id="84c9d-439">Each command item is an object with the following structure:</span></span>

|<span data-ttu-id="84c9d-440">Name</span><span class="sxs-lookup"><span data-stu-id="84c9d-440">Name</span></span>| <span data-ttu-id="84c9d-441">Typ</span><span class="sxs-lookup"><span data-stu-id="84c9d-441">Type</span></span>| <span data-ttu-id="84c9d-442">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="84c9d-442">Maximum size</span></span> | <span data-ttu-id="84c9d-443">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="84c9d-443">Required</span></span> | <span data-ttu-id="84c9d-444">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="84c9d-444">Description</span></span>|
|---|---|---|---|---|
|`id`|<span data-ttu-id="84c9d-445">string</span><span class="sxs-lookup"><span data-stu-id="84c9d-445">string</span></span>|<span data-ttu-id="84c9d-446">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="84c9d-446">64 characters</span></span>|<span data-ttu-id="84c9d-447">✔</span><span class="sxs-lookup"><span data-stu-id="84c9d-447">✔</span></span>|<span data-ttu-id="84c9d-448">Die ID für den Befehl.</span><span class="sxs-lookup"><span data-stu-id="84c9d-448">The ID for the command.</span></span>|
|`title`|<span data-ttu-id="84c9d-449">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="84c9d-449">string</span></span>|<span data-ttu-id="84c9d-450">32 Zeichen</span><span class="sxs-lookup"><span data-stu-id="84c9d-450">32 characters</span></span>|<span data-ttu-id="84c9d-451">✔</span><span class="sxs-lookup"><span data-stu-id="84c9d-451">✔</span></span>|<span data-ttu-id="84c9d-452">Der benutzerfreundliche Befehlsname.</span><span class="sxs-lookup"><span data-stu-id="84c9d-452">The user-friendly command name.</span></span>|
|`type`|<span data-ttu-id="84c9d-453">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="84c9d-453">string</span></span>|<span data-ttu-id="84c9d-454">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="84c9d-454">64 characters</span></span>||<span data-ttu-id="84c9d-455">Typ des Befehls.</span><span class="sxs-lookup"><span data-stu-id="84c9d-455">Type of the command.</span></span> <span data-ttu-id="84c9d-456">Einer oder `query` `action` .</span><span class="sxs-lookup"><span data-stu-id="84c9d-456">One of `query` or `action`.</span></span> <span data-ttu-id="84c9d-457">Standard: **Abfrage**.</span><span class="sxs-lookup"><span data-stu-id="84c9d-457">Default: **query**.</span></span>|
|`description`|<span data-ttu-id="84c9d-458">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="84c9d-458">string</span></span>|<span data-ttu-id="84c9d-459">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="84c9d-459">128 characters</span></span>||<span data-ttu-id="84c9d-460">Die Beschreibung, die Benutzern angezeigt wird, um den Zweck dieses Befehls anzugeben.</span><span class="sxs-lookup"><span data-stu-id="84c9d-460">The description that appears to users to indicate the purpose of this command.</span></span>|
|`initialRun`|<span data-ttu-id="84c9d-461">Boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="84c9d-461">boolean</span></span>|||<span data-ttu-id="84c9d-462">Ein boolescher Wert gibt an, ob der Befehl anfangs ohne Parameter ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="84c9d-462">A boolean value indicates whether the command runs initially with no parameters.</span></span> <span data-ttu-id="84c9d-463">Der Standardwert ist **false**.</span><span class="sxs-lookup"><span data-stu-id="84c9d-463">Default is **false**.</span></span>|
|`context`|<span data-ttu-id="84c9d-464">Array von Zeichenfolgen</span><span class="sxs-lookup"><span data-stu-id="84c9d-464">array of Strings</span></span>|<span data-ttu-id="84c9d-465">3</span><span class="sxs-lookup"><span data-stu-id="84c9d-465">3</span></span>||<span data-ttu-id="84c9d-466">Definiert, von wo aus die Nachrichtenerweiterung aufgerufen werden kann.</span><span class="sxs-lookup"><span data-stu-id="84c9d-466">Defines where the message extension can be invoked from.</span></span> <span data-ttu-id="84c9d-467">Beliebige Kombination aus `compose` , `commandBox` , `message` .</span><span class="sxs-lookup"><span data-stu-id="84c9d-467">Any combination of`compose`,`commandBox`,`message`.</span></span> <span data-ttu-id="84c9d-468">Der Standardwert ist `["compose","commandBox"]`.</span><span class="sxs-lookup"><span data-stu-id="84c9d-468">Default is `["compose","commandBox"]`.</span></span>|
|`fetchTask`|<span data-ttu-id="84c9d-469">Boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="84c9d-469">boolean</span></span>|||<span data-ttu-id="84c9d-470">Ein boolescher Wert, der angibt, ob das Aufgabenmodul dynamisch abgerufen werden muss.</span><span class="sxs-lookup"><span data-stu-id="84c9d-470">A boolean value that indicates if it must fetch the task module dynamically.</span></span> <span data-ttu-id="84c9d-471">Der Standardwert ist **false**.</span><span class="sxs-lookup"><span data-stu-id="84c9d-471">Default is **false**.</span></span>|
|`taskInfo`|<span data-ttu-id="84c9d-472">Objekt</span><span class="sxs-lookup"><span data-stu-id="84c9d-472">object</span></span>|||<span data-ttu-id="84c9d-473">Geben Sie das Aufgabenmodul an, das beim Verwenden eines Befehls für die Messagingerweiterung vor dem Laden geladen werden soll.</span><span class="sxs-lookup"><span data-stu-id="84c9d-473">Specify the task module to pre-load when using a messaging extension command.</span></span>|
|`taskInfo.title`|<span data-ttu-id="84c9d-474">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="84c9d-474">string</span></span>|<span data-ttu-id="84c9d-475">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="84c9d-475">64 characters</span></span>||<span data-ttu-id="84c9d-476">Titel des ersten Dialogfelds.</span><span class="sxs-lookup"><span data-stu-id="84c9d-476">Initial dialog title.</span></span>|
|`taskInfo.width`|<span data-ttu-id="84c9d-477">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="84c9d-477">string</span></span>|||<span data-ttu-id="84c9d-478">Dialogbreite – entweder eine Zahl in Pixel oder ein Standardlayout wie "groß", "mittel" oder "klein".</span><span class="sxs-lookup"><span data-stu-id="84c9d-478">Dialog width - either a number in pixels or default layout such as 'large', 'medium', or 'small'.</span></span>|
|`taskInfo.height`|<span data-ttu-id="84c9d-479">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="84c9d-479">string</span></span>|||<span data-ttu-id="84c9d-480">Dialoghöhe – entweder eine Zahl in Pixel oder ein Standardlayout wie "groß", "mittel" oder "klein".</span><span class="sxs-lookup"><span data-stu-id="84c9d-480">Dialog height - either a number in pixels or default layout such as 'large', 'medium', or 'small'.</span></span>|
|`taskInfo.url`|<span data-ttu-id="84c9d-481">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="84c9d-481">string</span></span>|||<span data-ttu-id="84c9d-482">Anfängliche Webview-URL.</span><span class="sxs-lookup"><span data-stu-id="84c9d-482">Initial webview URL.</span></span>|
|`parameters`|<span data-ttu-id="84c9d-483">Array des Objekts</span><span class="sxs-lookup"><span data-stu-id="84c9d-483">array of object</span></span>|<span data-ttu-id="84c9d-484">5 Elemente</span><span class="sxs-lookup"><span data-stu-id="84c9d-484">5 items</span></span>|<span data-ttu-id="84c9d-485">✔</span><span class="sxs-lookup"><span data-stu-id="84c9d-485">✔</span></span>|<span data-ttu-id="84c9d-486">Die Liste der Parameter, die der Befehl verwendet.</span><span class="sxs-lookup"><span data-stu-id="84c9d-486">The list of parameters the command takes.</span></span> <span data-ttu-id="84c9d-487">Minimum: 1; maximum: 5.</span><span class="sxs-lookup"><span data-stu-id="84c9d-487">Minimum: 1; maximum: 5.</span></span>|
|`parameters.name`|<span data-ttu-id="84c9d-488">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="84c9d-488">string</span></span>|<span data-ttu-id="84c9d-489">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="84c9d-489">64 characters</span></span>|<span data-ttu-id="84c9d-490">✔</span><span class="sxs-lookup"><span data-stu-id="84c9d-490">✔</span></span>|<span data-ttu-id="84c9d-491">Der Name des Parameters, wie er im Client angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="84c9d-491">The name of the parameter as it appears in the client.</span></span> <span data-ttu-id="84c9d-492">Dies ist in der Benutzeranforderung enthalten.</span><span class="sxs-lookup"><span data-stu-id="84c9d-492">This is included in the user request.</span></span>|
|`parameters.title`|<span data-ttu-id="84c9d-493">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="84c9d-493">string</span></span>|<span data-ttu-id="84c9d-494">32 Zeichen</span><span class="sxs-lookup"><span data-stu-id="84c9d-494">32 characters</span></span>|<span data-ttu-id="84c9d-495">✔</span><span class="sxs-lookup"><span data-stu-id="84c9d-495">✔</span></span>|<span data-ttu-id="84c9d-496">Benutzerfreundlicher Titel für den Parameter.</span><span class="sxs-lookup"><span data-stu-id="84c9d-496">User-friendly title for the parameter.</span></span>|
|`parameters.description`|<span data-ttu-id="84c9d-497">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="84c9d-497">string</span></span>|<span data-ttu-id="84c9d-498">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="84c9d-498">128 characters</span></span>||<span data-ttu-id="84c9d-499">Benutzerfreundliche Zeichenfolge, die den Zweck dieses Parameters beschreibt.</span><span class="sxs-lookup"><span data-stu-id="84c9d-499">User-friendly string that describes this parameter’s purpose.</span></span>|
|`parameters.value`|<span data-ttu-id="84c9d-500">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="84c9d-500">string</span></span>|<span data-ttu-id="84c9d-501">512 Zeichen</span><span class="sxs-lookup"><span data-stu-id="84c9d-501">512 characters</span></span>||<span data-ttu-id="84c9d-502">Anfangswert für den Parameter.</span><span class="sxs-lookup"><span data-stu-id="84c9d-502">Initial value for the parameter.</span></span>|
|`parameters.inputType`|<span data-ttu-id="84c9d-503">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="84c9d-503">string</span></span>|<span data-ttu-id="84c9d-504">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="84c9d-504">128 characters</span></span>||<span data-ttu-id="84c9d-505">Definiert den Typ des Steuerelements, das in einem Aufgabenmodul für angezeigt `fetchTask: true` wird.</span><span class="sxs-lookup"><span data-stu-id="84c9d-505">Defines the type of control displayed on a task module for`fetchTask: true` .</span></span> <span data-ttu-id="84c9d-506">Einer von `text, textarea, number, date, time, toggle, choiceset` .</span><span class="sxs-lookup"><span data-stu-id="84c9d-506">One of `text, textarea, number, date, time, toggle, choiceset` .</span></span>|
|`parameters.choices`|<span data-ttu-id="84c9d-507">Array von Objekten</span><span class="sxs-lookup"><span data-stu-id="84c9d-507">array of objects</span></span>|<span data-ttu-id="84c9d-508">10 Elemente</span><span class="sxs-lookup"><span data-stu-id="84c9d-508">10 items</span></span>||<span data-ttu-id="84c9d-509">Die Auswahloptionen für `choiceset` .</span><span class="sxs-lookup"><span data-stu-id="84c9d-509">The choice options for the`choiceset`.</span></span> <span data-ttu-id="84c9d-510">Verwenden Sie nur, `parameter.inputType` wenn `choiceset` .</span><span class="sxs-lookup"><span data-stu-id="84c9d-510">Use only when`parameter.inputType` is `choiceset`.</span></span>|
|`parameters.choices.title`|<span data-ttu-id="84c9d-511">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="84c9d-511">string</span></span>|<span data-ttu-id="84c9d-512">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="84c9d-512">128 characters</span></span>|<span data-ttu-id="84c9d-513">✔</span><span class="sxs-lookup"><span data-stu-id="84c9d-513">✔</span></span>|<span data-ttu-id="84c9d-514">Titel der Auswahl.</span><span class="sxs-lookup"><span data-stu-id="84c9d-514">Title of the choice.</span></span>|
|`parameters.choices.value`|<span data-ttu-id="84c9d-515">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="84c9d-515">string</span></span>|<span data-ttu-id="84c9d-516">512 Zeichen</span><span class="sxs-lookup"><span data-stu-id="84c9d-516">512 characters</span></span>|<span data-ttu-id="84c9d-517">✔</span><span class="sxs-lookup"><span data-stu-id="84c9d-517">✔</span></span>|<span data-ttu-id="84c9d-518">Value of the choice.</span><span class="sxs-lookup"><span data-stu-id="84c9d-518">Value of the choice.</span></span>|

## <a name="permissions"></a><span data-ttu-id="84c9d-519">Berechtigungen</span><span class="sxs-lookup"><span data-stu-id="84c9d-519">permissions</span></span>

<span data-ttu-id="84c9d-520">**Optional** – Array von Zeichenfolgen</span><span class="sxs-lookup"><span data-stu-id="84c9d-520">**Optional** — array of strings</span></span>

<span data-ttu-id="84c9d-521">Ein Array von dem angibt, welche Berechtigungen die App anfordert, wodurch Endbenutzer wissen, `string` wie die Erweiterung funktioniert.</span><span class="sxs-lookup"><span data-stu-id="84c9d-521">An array of `string` which specifies which permissions the app requests, which lets end users know how the extension performs.</span></span> <span data-ttu-id="84c9d-522">Die folgenden Optionen sind nicht exklusiv:</span><span class="sxs-lookup"><span data-stu-id="84c9d-522">The following options are non-exclusive:</span></span>

* <span data-ttu-id="84c9d-523">`identity`&emsp;Erfordert Benutzeridentitätsinformationen.</span><span class="sxs-lookup"><span data-stu-id="84c9d-523">`identity` &emsp; Requires user identity information.</span></span>
* <span data-ttu-id="84c9d-524">`messageTeamMembers`&emsp;Erfordert die Berechtigung zum Senden von Direktnachrichten an Teammitglieder.</span><span class="sxs-lookup"><span data-stu-id="84c9d-524">`messageTeamMembers` &emsp; Requires permission to send direct messages to team members.</span></span>

<span data-ttu-id="84c9d-525">Wenn Sie diese Berechtigungen während des App-Updates ändern, wiederholen Ihre Benutzer den Zustimmungsprozess, nachdem sie die aktualisierte App ausgeführt haben.</span><span class="sxs-lookup"><span data-stu-id="84c9d-525">Changing these permissions during app update, causes your users to repeat the consent process after they run the updated app.</span></span> <span data-ttu-id="84c9d-526">Weitere [Informationen finden Sie unter Aktualisieren](~/concepts/deploy-and-publish/appsource/post-publish/overview.md) Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="84c9d-526">See [Updating your app](~/concepts/deploy-and-publish/appsource/post-publish/overview.md) for more information.</span></span>

## <a name="devicepermissions"></a><span data-ttu-id="84c9d-527">devicePermissions</span><span class="sxs-lookup"><span data-stu-id="84c9d-527">devicePermissions</span></span>

<span data-ttu-id="84c9d-528">**Optional** – Array von Zeichenfolgen</span><span class="sxs-lookup"><span data-stu-id="84c9d-528">**Optional** — array of strings</span></span>

<span data-ttu-id="84c9d-529">Stellt die systemeigenen Features auf dem Gerät eines Benutzers zur Verfügung, auf das Ihre App Zugriff anfordert.</span><span class="sxs-lookup"><span data-stu-id="84c9d-529">Provides the native features on a user's device that your app requests access to.</span></span> <span data-ttu-id="84c9d-530">Mögliche Optionen sind:</span><span class="sxs-lookup"><span data-stu-id="84c9d-530">Options are:</span></span>

* `geolocation`
* `media`
* `notifications`
* `midi`
* `openExternal`

## <a name="validdomains"></a><span data-ttu-id="84c9d-531">validDomains</span><span class="sxs-lookup"><span data-stu-id="84c9d-531">validDomains</span></span>

<span data-ttu-id="84c9d-532">**Optional**, außer **Erforderlich,** sofern angegeben.</span><span class="sxs-lookup"><span data-stu-id="84c9d-532">**Optional**, except **Required** where noted.</span></span>

<span data-ttu-id="84c9d-533">Eine Liste der gültigen Domänen für Websites, die die App im Client Teams wird.</span><span class="sxs-lookup"><span data-stu-id="84c9d-533">A list of valid domains for websites the app expects to load within the Teams client.</span></span> <span data-ttu-id="84c9d-534">Domänenauflistungen können Platzhalter enthalten, z. B. `*.example.com` .</span><span class="sxs-lookup"><span data-stu-id="84c9d-534">Domain listings can include wildcards, for example, `*.example.com`.</span></span> <span data-ttu-id="84c9d-535">Dies entspricht genau einem Abschnitt der Domäne. wenn Sie übereinstimmen müssen, `a.b.example.com` verwenden Sie `*.*.example.com` .</span><span class="sxs-lookup"><span data-stu-id="84c9d-535">This matches exactly one segment of the domain; if you need to match `a.b.example.com` then use `*.*.example.com`.</span></span> <span data-ttu-id="84c9d-536">Wenn Ihre Registerkartenkonfiguration oder Inhaltsbenutzeroberfläche neben der für die Registerkartenkonfiguration verwendeten Domäne zu einer anderen Domäne navigieren muss, muss diese Domäne hier angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="84c9d-536">If your tab configuration or content UI needs to navigate to any other domain besides the one use for tab configuration, that domain must be specified here.</span></span>

<span data-ttu-id="84c9d-537">Es ist **nicht** erforderlich, die Domänen von Identitätsanbietern, die Sie unterstützen möchten, in Ihre App zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="84c9d-537">It is **not** necessary to include the domains of identity providers you want to support in your app.</span></span> <span data-ttu-id="84c9d-538">Um sich z. B. mithilfe einer Google-ID zu authentifizieren, müssen Sie an accounts.google.com umleiten, sie dürfen jedoch accounts.google.com in nicht `validDomains[]` enthalten.</span><span class="sxs-lookup"><span data-stu-id="84c9d-538">For example, to authenticate using a Google ID, it is required to redirect to accounts.google.com, however, you must not include accounts.google.com in `validDomains[]`.</span></span>

<span data-ttu-id="84c9d-539">Teams apps that require their own sharepoint URLs to function well, includes "{teamsitedomain}" in their valid domain list.</span><span class="sxs-lookup"><span data-stu-id="84c9d-539">Teams apps that require their own sharepoint URLs to function well, includes "{teamsitedomain}" in their valid domain list.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="84c9d-540">Fügen Sie keine Domänen hinzu, die sich außerhalb Ihres Steuerelements befinden, weder direkt noch über Platzhalter.</span><span class="sxs-lookup"><span data-stu-id="84c9d-540">Do not add domains that are outside your control, either directly or through wildcards.</span></span> <span data-ttu-id="84c9d-541">Ist z. `yourapp.onmicrosoft.com` B. gültig, ist `*.onmicrosoft.com` jedoch ungültig.</span><span class="sxs-lookup"><span data-stu-id="84c9d-541">For example, `yourapp.onmicrosoft.com` is valid, however, `*.onmicrosoft.com` is not valid.</span></span>

<span data-ttu-id="84c9d-542">Das Objekt ist ein Array mit allen Elementen des Typs `string` .</span><span class="sxs-lookup"><span data-stu-id="84c9d-542">The object is an array with all elements of the type `string`.</span></span>

## <a name="webapplicationinfo"></a><span data-ttu-id="84c9d-543">webApplicationInfo</span><span class="sxs-lookup"><span data-stu-id="84c9d-543">webApplicationInfo</span></span>

<span data-ttu-id="84c9d-544">**Optional** – -Objekt</span><span class="sxs-lookup"><span data-stu-id="84c9d-544">**Optional** — object</span></span>

<span data-ttu-id="84c9d-545">Geben Sie Azure Active Directory (AAD)-App-ID und Microsoft Graph, um Benutzern die nahtlose Anmeldung bei Ihrer App zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="84c9d-545">Provide your Azure Active Directory (AAD) App ID and Microsoft Graph information to help users seamlessly sign into your app.</span></span> <span data-ttu-id="84c9d-546">Wenn Ihre App in AAD registriert ist, müssen Sie die App-ID bereitstellen, damit Administratoren die Berechtigungen problemlos überprüfen und ihre Zustimmung im Teams erteilen können.</span><span class="sxs-lookup"><span data-stu-id="84c9d-546">If your app is registered in AAD, you must provide the App ID, so that administrators can easily review permissions and grant consent in Teams admin center.</span></span>

|<span data-ttu-id="84c9d-547">Name</span><span class="sxs-lookup"><span data-stu-id="84c9d-547">Name</span></span>| <span data-ttu-id="84c9d-548">Typ</span><span class="sxs-lookup"><span data-stu-id="84c9d-548">Type</span></span>| <span data-ttu-id="84c9d-549">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="84c9d-549">Maximum size</span></span> | <span data-ttu-id="84c9d-550">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="84c9d-550">Required</span></span> | <span data-ttu-id="84c9d-551">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="84c9d-551">Description</span></span>|
|---|---|---|---|---|
|`id`|<span data-ttu-id="84c9d-552">string</span><span class="sxs-lookup"><span data-stu-id="84c9d-552">string</span></span>|<span data-ttu-id="84c9d-553">36 Zeichen</span><span class="sxs-lookup"><span data-stu-id="84c9d-553">36 characters</span></span>|<span data-ttu-id="84c9d-554">✔</span><span class="sxs-lookup"><span data-stu-id="84c9d-554">✔</span></span>|<span data-ttu-id="84c9d-555">AAD-Anwendungs-ID der App.</span><span class="sxs-lookup"><span data-stu-id="84c9d-555">AAD application id of the app.</span></span> <span data-ttu-id="84c9d-556">Diese ID muss eine GUID sein.</span><span class="sxs-lookup"><span data-stu-id="84c9d-556">This id must be a GUID.</span></span>|
|`resource`|<span data-ttu-id="84c9d-557">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="84c9d-557">string</span></span>|<span data-ttu-id="84c9d-558">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="84c9d-558">2048 characters</span></span>|<span data-ttu-id="84c9d-559">✔</span><span class="sxs-lookup"><span data-stu-id="84c9d-559">✔</span></span>|<span data-ttu-id="84c9d-560">Ressourcen-URL der App zum Abrufen des Authentifizierungstokens für SSO.</span><span class="sxs-lookup"><span data-stu-id="84c9d-560">Resource URL of app for acquiring auth token for SSO.</span></span> </br> <span data-ttu-id="84c9d-561">**HINWEIS:** Wenn Sie SSO nicht verwenden, stellen Sie sicher, dass Sie in diesem Feld einen Schnullerzeichenfolgenwert in Ihr App-Manifest eingeben, um beispielsweise eine https://notapplicable Fehlerantwort zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="84c9d-561">**NOTE:** If you are not using SSO, ensure that you enter a dummy string value in this field to your app manifest, for example, https://notapplicable to avoid an error response.</span></span> |
|`applicationPermissions`|<span data-ttu-id="84c9d-562">array of strings</span><span class="sxs-lookup"><span data-stu-id="84c9d-562">array of strings</span></span>|<span data-ttu-id="84c9d-563">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="84c9d-563">128 characters</span></span>||<span data-ttu-id="84c9d-564">Geben Sie [granulare ressourcenspezifische Zustimmung an.](../../graph-api/rsc/resource-specific-consent.md#resource-specific-permissions)</span><span class="sxs-lookup"><span data-stu-id="84c9d-564">Specify granular [resource specific consent](../../graph-api/rsc/resource-specific-consent.md#resource-specific-permissions).</span></span>|

## <a name="showloadingindicator"></a><span data-ttu-id="84c9d-565">showLoadingIndicator</span><span class="sxs-lookup"><span data-stu-id="84c9d-565">showLoadingIndicator</span></span>

<span data-ttu-id="84c9d-566">**Optional** – boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="84c9d-566">**Optional** — boolean</span></span>

<span data-ttu-id="84c9d-567">Gibt an, ob die Ladeanzeige angezeigt werden soll, wenn eine App oder Registerkarte geladen wird.</span><span class="sxs-lookup"><span data-stu-id="84c9d-567">Indicates whether or not to show the loading indicator when an app or tab is loading.</span></span> <span data-ttu-id="84c9d-568">Der Standardwert ist **false**.</span><span class="sxs-lookup"><span data-stu-id="84c9d-568">Default is **false**.</span></span>
>[!NOTE]
><span data-ttu-id="84c9d-569">Wenn Sie im App-Manifest als true auswählen, ändern Sie die Inhaltsseiten Ihrer Registerkarten und Aufgabenmodule, um die Seite ordnungsgemäß zu laden, wie unter Anzeigen eines nativen Ladeindikatordokuments `showLoadingIndicator` beschrieben. [](../../tabs/how-to/create-tab-pages/content-page.md#show-a-native-loading-indicator)</span><span class="sxs-lookup"><span data-stu-id="84c9d-569">If you select`showLoadingIndicator` as true in your app manifest, to load the page correctly, modify the content pages of your tabs and task modules as described in [Show a native loading indicator](../../tabs/how-to/create-tab-pages/content-page.md#show-a-native-loading-indicator) document.</span></span>


## <a name="isfullscreen"></a><span data-ttu-id="84c9d-570">isFullScreen</span><span class="sxs-lookup"><span data-stu-id="84c9d-570">isFullScreen</span></span>

 <span data-ttu-id="84c9d-571">**Optional** – boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="84c9d-571">**Optional** — boolean</span></span>

<span data-ttu-id="84c9d-572">Geben Sie an, wo eine persönliche App mit oder ohne Registerkartenkopfleiste gerendert wird.</span><span class="sxs-lookup"><span data-stu-id="84c9d-572">Indicate where a personal app is rendered with or without a tab header bar.</span></span> <span data-ttu-id="84c9d-573">Der Standardwert ist **false**.</span><span class="sxs-lookup"><span data-stu-id="84c9d-573">Default is **false**.</span></span>

## <a name="activities"></a><span data-ttu-id="84c9d-574">Aktivitäten</span><span class="sxs-lookup"><span data-stu-id="84c9d-574">activities</span></span>

<span data-ttu-id="84c9d-575">**Optional** – -Objekt</span><span class="sxs-lookup"><span data-stu-id="84c9d-575">**Optional** — object</span></span>

<span data-ttu-id="84c9d-576">Definieren Sie die Eigenschaften, die Ihre App zum Posten eines Benutzeraktivitätsfeeds verwendet.</span><span class="sxs-lookup"><span data-stu-id="84c9d-576">Define the properties your app uses to post a user activity feed.</span></span>

|<span data-ttu-id="84c9d-577">Name</span><span class="sxs-lookup"><span data-stu-id="84c9d-577">Name</span></span>| <span data-ttu-id="84c9d-578">Typ</span><span class="sxs-lookup"><span data-stu-id="84c9d-578">Type</span></span>| <span data-ttu-id="84c9d-579">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="84c9d-579">Maximum size</span></span> | <span data-ttu-id="84c9d-580">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="84c9d-580">Required</span></span> | <span data-ttu-id="84c9d-581">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="84c9d-581">Description</span></span>|
|---|---|---|---|---|
|`activityTypes`|<span data-ttu-id="84c9d-582">Array von Objekten</span><span class="sxs-lookup"><span data-stu-id="84c9d-582">array of Objects</span></span>|<span data-ttu-id="84c9d-583">128 Elemente</span><span class="sxs-lookup"><span data-stu-id="84c9d-583">128 items</span></span>| | <span data-ttu-id="84c9d-584">Stellen Sie die Arten von Aktivitäten zur Verfügung, die Ihre App an einen Benutzeraktivitätsfeed posten kann.</span><span class="sxs-lookup"><span data-stu-id="84c9d-584">Provide the types of activities that your app can post to a users activity feed.</span></span>|

### <a name="activitiesactivitytypes"></a><span data-ttu-id="84c9d-585">activities.activityTypes</span><span class="sxs-lookup"><span data-stu-id="84c9d-585">activities.activityTypes</span></span>

|<span data-ttu-id="84c9d-586">Name</span><span class="sxs-lookup"><span data-stu-id="84c9d-586">Name</span></span>| <span data-ttu-id="84c9d-587">Typ</span><span class="sxs-lookup"><span data-stu-id="84c9d-587">Type</span></span>| <span data-ttu-id="84c9d-588">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="84c9d-588">Maximum size</span></span> | <span data-ttu-id="84c9d-589">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="84c9d-589">Required</span></span> | <span data-ttu-id="84c9d-590">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="84c9d-590">Description</span></span>|
|---|---|---|---|---|
|`type`|<span data-ttu-id="84c9d-591">string</span><span class="sxs-lookup"><span data-stu-id="84c9d-591">string</span></span>|<span data-ttu-id="84c9d-592">32 Zeichen</span><span class="sxs-lookup"><span data-stu-id="84c9d-592">32 characters</span></span>|<span data-ttu-id="84c9d-593">✔</span><span class="sxs-lookup"><span data-stu-id="84c9d-593">✔</span></span>|<span data-ttu-id="84c9d-594">Der Benachrichtigungstyp.</span><span class="sxs-lookup"><span data-stu-id="84c9d-594">The notification type.</span></span> <span data-ttu-id="84c9d-595">*Siehe unten*.</span><span class="sxs-lookup"><span data-stu-id="84c9d-595">*See below*.</span></span>|
|`description`|<span data-ttu-id="84c9d-596">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="84c9d-596">string</span></span>|<span data-ttu-id="84c9d-597">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="84c9d-597">128 characters</span></span>|<span data-ttu-id="84c9d-598">✔</span><span class="sxs-lookup"><span data-stu-id="84c9d-598">✔</span></span>|<span data-ttu-id="84c9d-599">Eine kurze Beschreibung der Benachrichtigung.</span><span class="sxs-lookup"><span data-stu-id="84c9d-599">A brief description of the notification.</span></span> <span data-ttu-id="84c9d-600">*Siehe unten*.</span><span class="sxs-lookup"><span data-stu-id="84c9d-600">*See below*.</span></span>|
|`templateText`|<span data-ttu-id="84c9d-601">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="84c9d-601">string</span></span>|<span data-ttu-id="84c9d-602">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="84c9d-602">128 characters</span></span>|<span data-ttu-id="84c9d-603">✔</span><span class="sxs-lookup"><span data-stu-id="84c9d-603">✔</span></span>|<span data-ttu-id="84c9d-604">Ex: "{actor}- erstellter Task {taskId} für Sie"</span><span class="sxs-lookup"><span data-stu-id="84c9d-604">Ex: "{actor} created task {taskId} for you"</span></span>|

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

## <a name="defaultinstallscope"></a><span data-ttu-id="84c9d-605">defaultInstallScope</span><span class="sxs-lookup"><span data-stu-id="84c9d-605">defaultInstallScope</span></span>

<span data-ttu-id="84c9d-606">**Optional** – Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="84c9d-606">**Optional** - string</span></span>

<span data-ttu-id="84c9d-607">Gibt den für diese App definierten Installationsbereich standardmäßig an.</span><span class="sxs-lookup"><span data-stu-id="84c9d-607">Specifies the install scope defined for this app by default.</span></span> <span data-ttu-id="84c9d-608">Der definierte Bereich ist die Option, die auf der Schaltfläche angezeigt wird, wenn ein Benutzer versucht, die App hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="84c9d-608">The defined scope will be the option displayed on the button when a user tries to add the app.</span></span> <span data-ttu-id="84c9d-609">Mögliche Optionen sind:</span><span class="sxs-lookup"><span data-stu-id="84c9d-609">Options are:</span></span>
* `personal`
* `team`
* `groupchat`
* `meetings`

## <a name="defaultgroupcapability"></a><span data-ttu-id="84c9d-610">defaultGroupCapability</span><span class="sxs-lookup"><span data-stu-id="84c9d-610">defaultGroupCapability</span></span>

<span data-ttu-id="84c9d-611">**Optional** - -Objekt</span><span class="sxs-lookup"><span data-stu-id="84c9d-611">**Optional** - object</span></span>

<span data-ttu-id="84c9d-612">Wenn ein Gruppeninstallationsbereich ausgewählt ist, wird die Standardfunktion definiert, wenn der Benutzer die App installiert.</span><span class="sxs-lookup"><span data-stu-id="84c9d-612">When a group install scope is selected, it will define the default capability when the user installs the app.</span></span> <span data-ttu-id="84c9d-613">Mögliche Optionen sind:</span><span class="sxs-lookup"><span data-stu-id="84c9d-613">Options are:</span></span>
* `team`
* `groupchat`
* `meetings`
 
|<span data-ttu-id="84c9d-614">Name</span><span class="sxs-lookup"><span data-stu-id="84c9d-614">Name</span></span>| <span data-ttu-id="84c9d-615">Typ</span><span class="sxs-lookup"><span data-stu-id="84c9d-615">Type</span></span>| <span data-ttu-id="84c9d-616">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="84c9d-616">Maximum size</span></span> | <span data-ttu-id="84c9d-617">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="84c9d-617">Required</span></span> | <span data-ttu-id="84c9d-618">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="84c9d-618">Description</span></span>|
|---|---|---|---|---|
|`team`|<span data-ttu-id="84c9d-619">string</span><span class="sxs-lookup"><span data-stu-id="84c9d-619">string</span></span>|||<span data-ttu-id="84c9d-620">Wenn der ausgewählte Installationsbereich ausgewählt ist, gibt `team` dieses Feld die verfügbare Standardfunktion an.</span><span class="sxs-lookup"><span data-stu-id="84c9d-620">When the install scope selected is `team`, this field specifies the default capability available.</span></span> <span data-ttu-id="84c9d-621">Optionen: `tab` , `bot` oder `connector` .</span><span class="sxs-lookup"><span data-stu-id="84c9d-621">Options: `tab`, `bot`, or `connector`.</span></span>|
|`groupchat`|<span data-ttu-id="84c9d-622">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="84c9d-622">string</span></span>|||<span data-ttu-id="84c9d-623">Wenn der ausgewählte Installationsbereich ausgewählt ist, gibt `groupchat` dieses Feld die verfügbare Standardfunktion an.</span><span class="sxs-lookup"><span data-stu-id="84c9d-623">When the install scope selected is `groupchat`, this field specifies the default capability available.</span></span> <span data-ttu-id="84c9d-624">Optionen: `tab` , `bot` oder `connector` .</span><span class="sxs-lookup"><span data-stu-id="84c9d-624">Options: `tab`, `bot`, or `connector`.</span></span>|
|`meetings`|<span data-ttu-id="84c9d-625">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="84c9d-625">string</span></span>|||<span data-ttu-id="84c9d-626">Wenn der ausgewählte Installationsbereich ausgewählt ist, gibt `meetings` dieses Feld die verfügbare Standardfunktion an.</span><span class="sxs-lookup"><span data-stu-id="84c9d-626">When the install scope selected is `meetings`, this field specifies the default capability available.</span></span> <span data-ttu-id="84c9d-627">Optionen: `tab` , `bot` oder `connector` .</span><span class="sxs-lookup"><span data-stu-id="84c9d-627">Options: `tab`, `bot`, or `connector`.</span></span>|

## <a name="configurableproperties"></a><span data-ttu-id="84c9d-628">configurableProperties</span><span class="sxs-lookup"><span data-stu-id="84c9d-628">configurableProperties</span></span>

<span data-ttu-id="84c9d-629">**Optional** – Array</span><span class="sxs-lookup"><span data-stu-id="84c9d-629">**Optional** - array</span></span>

<span data-ttu-id="84c9d-630">Der `configurableProperties` Block definiert die App-Eigenschaften, die Teams Administrator anpassen kann.</span><span class="sxs-lookup"><span data-stu-id="84c9d-630">The `configurableProperties` block defines the app properties that Teams admin can customize.</span></span> <span data-ttu-id="84c9d-631">Weitere Informationen finden Sie unter [Anpassen von Apps in Microsoft Teams.](/MicrosoftTeams/customize-apps)</span><span class="sxs-lookup"><span data-stu-id="84c9d-631">For more information, see [customize apps in Microsoft Teams](/MicrosoftTeams/customize-apps).</span></span>

> [!NOTE]
> <span data-ttu-id="84c9d-632">Mindestens eine Eigenschaft muss definiert werden.</span><span class="sxs-lookup"><span data-stu-id="84c9d-632">A minimum of one property must be defined.</span></span> <span data-ttu-id="84c9d-633">Sie können in diesem Block maximal neun Eigenschaften definieren.</span><span class="sxs-lookup"><span data-stu-id="84c9d-633">You can define a maximum of nine properties in this block.</span></span>
> <span data-ttu-id="84c9d-634">Als bewährte Methode müssen Sie Anpassungsrichtlinien für App-Benutzer und -Kunden bereitstellen, die sie beim Anpassen Ihrer App befolgen müssen.</span><span class="sxs-lookup"><span data-stu-id="84c9d-634">As a best practice, you must provide customization guidelines for app users and customers to follow when customizing your app.</span></span>

<span data-ttu-id="84c9d-635">Sie können eine der folgenden Eigenschaften definieren:</span><span class="sxs-lookup"><span data-stu-id="84c9d-635">You can define any of the following properties:</span></span>
* <span data-ttu-id="84c9d-636">`name`: Ermöglicht administratoren das Ändern des Anzeigenamens der App.</span><span class="sxs-lookup"><span data-stu-id="84c9d-636">`name`: Allows admin to change the app's display name.</span></span>
* <span data-ttu-id="84c9d-637">`shortDescription`: Ermöglicht Administratoren das Ändern der Kurzbeschreibung der App.</span><span class="sxs-lookup"><span data-stu-id="84c9d-637">`shortDescription`: Allows admin to change the app's short description.</span></span>
* <span data-ttu-id="84c9d-638">`longDescription`: Ermöglicht Administratoren das Ändern der detaillierten Beschreibung der App.</span><span class="sxs-lookup"><span data-stu-id="84c9d-638">`longDescription`: Allows admin to change the app's detailed description.</span></span>
* <span data-ttu-id="84c9d-639">`smallImageUrl`: Es handelt sich `outline` um die Eigenschaft im Block des `icons` Manifests.</span><span class="sxs-lookup"><span data-stu-id="84c9d-639">`smallImageUrl`: It is the `outline` property in the `icons` block of the manifest.</span></span>
* <span data-ttu-id="84c9d-640">`largeImageUrl`: Es handelt sich `color` um die Eigenschaft im Block des `icons` Manifests.</span><span class="sxs-lookup"><span data-stu-id="84c9d-640">`largeImageUrl`: It is the `color` property in the `icons` block of the manifest.</span></span>
* <span data-ttu-id="84c9d-641">`accentColor`: Es ist die Farbe, die in Verbindung mit und als Hintergrund für Ihre Gliederungssymbole verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="84c9d-641">`accentColor`: It is the color to use in conjunction with and as a background for your outline icons.</span></span>
* <span data-ttu-id="84c9d-642">`websiteUrl`: Es ist die https://-URL zur Website des Entwicklers.</span><span class="sxs-lookup"><span data-stu-id="84c9d-642">`websiteUrl`: It is the https:// URL to the developer's website.</span></span>
* <span data-ttu-id="84c9d-643">`privacyUrl`: Es ist die https://-URL zur Datenschutzrichtlinie des Entwicklers.</span><span class="sxs-lookup"><span data-stu-id="84c9d-643">`privacyUrl`: It is the https:// URL to the developer's privacy policy.</span></span>
* <span data-ttu-id="84c9d-644">`termsOfUseUrl`: Es ist die https:// URL zu den Nutzungsbedingungen des Entwicklers.</span><span class="sxs-lookup"><span data-stu-id="84c9d-644">`termsOfUseUrl`: It is the https:// URL to the developer's terms of use.</span></span>


