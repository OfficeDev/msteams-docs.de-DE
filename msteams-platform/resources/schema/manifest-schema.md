---
title: Manifestschemareferenz
description: Beschreibt das Manifestschema für Microsoft Teams
ms.topic: reference
ms.author: lajanuar
localization_priority: Normal
keywords: Teams-Manifestschema
ms.openlocfilehash: 75c29a1cf9c2897d7b419b45bfc1a4f0447c7aa3
ms.sourcegitcommit: 37325179a532897fafbe827dcf9a7ca5fa5e7d0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2021
ms.locfileid: "52853529"
---
# <a name="reference-manifest-schema-for-microsoft-teams"></a><span data-ttu-id="c2685-104">Referenz: Manifestschema für Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="c2685-104">Reference: Manifest schema for Microsoft Teams</span></span>

<span data-ttu-id="c2685-105">Das Teams-Manifest beschreibt, wie die App in das Microsoft Teams-Produkt integriert wird.</span><span class="sxs-lookup"><span data-stu-id="c2685-105">The Teams manifest describes how the app integrates into the Microsoft Teams product.</span></span> <span data-ttu-id="c2685-106">Ihr Manifest muss dem schema gehosteten [`https://developer.microsoft.com/json-schemas/teams/v1.10/MicrosoftTeams.schema.json`]( https://developer.microsoft.com/json-schemas/teams/v1.10/MicrosoftTeams.schema.json) entsprechen.</span><span class="sxs-lookup"><span data-stu-id="c2685-106">Your manifest must conform to the schema hosted at [`https://developer.microsoft.com/json-schemas/teams/v1.10/MicrosoftTeams.schema.json`]( https://developer.microsoft.com/json-schemas/teams/v1.10/MicrosoftTeams.schema.json).</span></span> <span data-ttu-id="c2685-107">Frühere Versionen 1.0, 1.1,..., 1.6 usw. werden ebenfalls unterstützt (unter Verwendung von "v1.x" in der URL).</span><span class="sxs-lookup"><span data-stu-id="c2685-107">Previous versions 1.0, 1.1,..., 1.6, and so on are also supported (using "v1.x" in the URL).</span></span>
<span data-ttu-id="c2685-108">Weitere Informationen zu den Änderungen, die in jeder Version vorgenommen wurden, finden Sie im [Manifeständerungsprotokoll.](https://github.com/OfficeDev/microsoft-teams-app-schema/releases)</span><span class="sxs-lookup"><span data-stu-id="c2685-108">For more information on the changes made in each version, see [manifest change log](https://github.com/OfficeDev/microsoft-teams-app-schema/releases).</span></span>

<span data-ttu-id="c2685-109">Das folgende Schemabeispiel zeigt alle Erweiterbarkeitsoptionen:</span><span class="sxs-lookup"><span data-stu-id="c2685-109">The following schema sample shows all extensibility options:</span></span>

## <a name="sample-full-manifest"></a><span data-ttu-id="c2685-110">Vollständiges Beispielmanifest</span><span class="sxs-lookup"><span data-stu-id="c2685-110">Sample full manifest</span></span>

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
     "developerUrl",
     "privacyUrl",
     "termsOfUseUrl"        
  ]              
}
```

<span data-ttu-id="c2685-111">Das Schema definiert die folgenden Eigenschaften:</span><span class="sxs-lookup"><span data-stu-id="c2685-111">The schema defines the following properties:</span></span>

## <a name="schema"></a><span data-ttu-id="c2685-112">$schema</span><span class="sxs-lookup"><span data-stu-id="c2685-112">$schema</span></span>

<span data-ttu-id="c2685-113">Optional, aber empfohlen – Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="c2685-113">Optional, but recommended — string</span></span>

<span data-ttu-id="c2685-114">Die https://-URL, die auf das JSON-Schema für das Manifest verweist.</span><span class="sxs-lookup"><span data-stu-id="c2685-114">The https:// URL referencing the JSON Schema for the manifest.</span></span>

## <a name="manifestversion"></a><span data-ttu-id="c2685-115">manifestVersion</span><span class="sxs-lookup"><span data-stu-id="c2685-115">manifestVersion</span></span>

<span data-ttu-id="c2685-116">**Erforderlich** – Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="c2685-116">**Required** — string</span></span>

<span data-ttu-id="c2685-117">Die Version des Manifestschemas, das dieses Manifest verwendet.</span><span class="sxs-lookup"><span data-stu-id="c2685-117">The version of manifest schema this manifest is using.</span></span> <span data-ttu-id="c2685-118">Es muss 1.10 sein.</span><span class="sxs-lookup"><span data-stu-id="c2685-118">It must be 1.10.</span></span>

## <a name="version"></a><span data-ttu-id="c2685-119">Version</span><span class="sxs-lookup"><span data-stu-id="c2685-119">version</span></span>

<span data-ttu-id="c2685-120">**Erforderlich** – Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="c2685-120">**Required** — string</span></span>

<span data-ttu-id="c2685-121">Die Version einer bestimmten App.</span><span class="sxs-lookup"><span data-stu-id="c2685-121">The version of a specific app.</span></span> <span data-ttu-id="c2685-122">Wenn Sie etwas in Ihrem Manifest aktualisieren, muss auch die Version erhöht werden.</span><span class="sxs-lookup"><span data-stu-id="c2685-122">If you update something in your manifest, the version must be incremented too.</span></span> <span data-ttu-id="c2685-123">Auf diese Weise wird bei der Installation des neuen Manifests das vorhandene überschrieben, und der Benutzer erhält die neue Funktionalität.</span><span class="sxs-lookup"><span data-stu-id="c2685-123">This way, when the new manifest is installed, it overwrites the existing one and the user receives the new functionality.</span></span> <span data-ttu-id="c2685-124">Wenn diese App an den Store übermittelt wurde, muss das neue Manifest erneut übermittelt und erneut überprüft werden.</span><span class="sxs-lookup"><span data-stu-id="c2685-124">If this app was submitted to the store, the new manifest must be re-submitted and re-validated.</span></span> <span data-ttu-id="c2685-125">Die App-Benutzer erhalten das neue aktualisierte Manifest automatisch innerhalb weniger Stunden nach der Genehmigung des Manifests.</span><span class="sxs-lookup"><span data-stu-id="c2685-125">The app users receive the new updated manifest automatically within few hours after the manifest is approved.</span></span>

<span data-ttu-id="c2685-126">Wenn sich die App-Anforderungen für Berechtigungen ändern, werden die Benutzer aufgefordert, ein Upgrade durchzuführen und der App erneut zuzustimmen.</span><span class="sxs-lookup"><span data-stu-id="c2685-126">If the app requests for permissions change, the users are prompted to upgrade and re-consent to the app.</span></span>

<span data-ttu-id="c2685-127">Diese Versionszeichenfolge muss dem [Semverstandard](http://semver.org/) (MAJOR. kleiner. PATCH).</span><span class="sxs-lookup"><span data-stu-id="c2685-127">This version string must follow the [semver](http://semver.org/) standard (MAJOR.MINOR.PATCH).</span></span>

## <a name="id"></a><span data-ttu-id="c2685-128">id</span><span class="sxs-lookup"><span data-stu-id="c2685-128">id</span></span>

<span data-ttu-id="c2685-129">**Erforderlich** – Microsoft-App-ID</span><span class="sxs-lookup"><span data-stu-id="c2685-129">**Required** — Microsoft app ID</span></span>

<span data-ttu-id="c2685-130">Die ID ist ein eindeutiger von Microsoft generierter Bezeichner für die App.</span><span class="sxs-lookup"><span data-stu-id="c2685-130">The ID is a unique Microsoft-generated identifier for the app.</span></span> <span data-ttu-id="c2685-131">Sie haben eine ID, wenn Ihr Bot über das Microsoft Bot Framework registriert ist oder sich die Web-App Ihrer Registerkarte bereits bei Microsoft anmeldet.</span><span class="sxs-lookup"><span data-stu-id="c2685-131">You have an ID if your bot is registered through the Microsoft Bot Framework or your tab's web app already signs in with Microsoft.</span></span> <span data-ttu-id="c2685-132">Sie müssen die ID hier eingeben.</span><span class="sxs-lookup"><span data-stu-id="c2685-132">You must enter the ID here.</span></span> <span data-ttu-id="c2685-133">Andernfalls müssen Sie eine neue ID im [Microsoft-Anwendungsregistrierungsportal](https://aka.ms/appregistrations)generieren.</span><span class="sxs-lookup"><span data-stu-id="c2685-133">Otherwise, you must generate a new ID at the [Microsoft Application Registration Portal](https://aka.ms/appregistrations).</span></span> <span data-ttu-id="c2685-134">Verwenden Sie die gleiche ID, wenn Sie einen Bot hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="c2685-134">Use the same ID if you add a bot.</span></span>

> [!NOTE]
> <span data-ttu-id="c2685-135">Wenn Sie ein Update für Ihre vorhandene App in AppSource übermitteln, darf die ID in Ihrem Manifest nicht geändert werden.</span><span class="sxs-lookup"><span data-stu-id="c2685-135">If you are submitting an update to your existing app in AppSource, the ID in your manifest must not be modified.</span></span>

## <a name="developer"></a><span data-ttu-id="c2685-136">developer</span><span class="sxs-lookup"><span data-stu-id="c2685-136">developer</span></span>

<span data-ttu-id="c2685-137">**Erforderlich** – Objekt</span><span class="sxs-lookup"><span data-stu-id="c2685-137">**Required** — object</span></span>

<span data-ttu-id="c2685-138">Gibt Informationen zu Ihrem Unternehmen an.</span><span class="sxs-lookup"><span data-stu-id="c2685-138">Specifies information about your company.</span></span> <span data-ttu-id="c2685-139">Bei An den Teams Store übermittelten Apps müssen diese Werte mit den Informationen in Ihrem Store-Eintrag übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="c2685-139">For apps submitted to the Teams store, these values must match the information in your store listing.</span></span> <span data-ttu-id="c2685-140">Weitere Informationen finden Sie in den Richtlinien für die Veröffentlichung des [Teams-Stores.](~/concepts/deploy-and-publish/appsource/publish.md)</span><span class="sxs-lookup"><span data-stu-id="c2685-140">For more information, see the [Teams store publishing guidelines](~/concepts/deploy-and-publish/appsource/publish.md).</span></span>

|<span data-ttu-id="c2685-141">Name</span><span class="sxs-lookup"><span data-stu-id="c2685-141">Name</span></span>| <span data-ttu-id="c2685-142">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="c2685-142">Maximum size</span></span> | <span data-ttu-id="c2685-143">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="c2685-143">Required</span></span> | <span data-ttu-id="c2685-144">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="c2685-144">Description</span></span>|
|---|---|---|---|
|`name`|<span data-ttu-id="c2685-145">32 Zeichen</span><span class="sxs-lookup"><span data-stu-id="c2685-145">32 characters</span></span>|<span data-ttu-id="c2685-146">✔</span><span class="sxs-lookup"><span data-stu-id="c2685-146">✔</span></span>|<span data-ttu-id="c2685-147">Der Anzeigename für den Entwickler.</span><span class="sxs-lookup"><span data-stu-id="c2685-147">The display name for the developer.</span></span>|
|`websiteUrl`|<span data-ttu-id="c2685-148">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="c2685-148">2048 characters</span></span>|<span data-ttu-id="c2685-149">✔</span><span class="sxs-lookup"><span data-stu-id="c2685-149">✔</span></span>|<span data-ttu-id="c2685-150">Die https:// URL zur Website des Entwicklers.</span><span class="sxs-lookup"><span data-stu-id="c2685-150">The https:// URL to the developer's website.</span></span> <span data-ttu-id="c2685-151">Dieser Link muss Benutzer zu Ihrem Unternehmen oder ihrer produktspezifischen Angebotsseite bringen.</span><span class="sxs-lookup"><span data-stu-id="c2685-151">This link must take users to your company or product-specific landing page.</span></span>|
|`privacyUrl`|<span data-ttu-id="c2685-152">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="c2685-152">2048 characters</span></span>|<span data-ttu-id="c2685-153">✔</span><span class="sxs-lookup"><span data-stu-id="c2685-153">✔</span></span>|<span data-ttu-id="c2685-154">Die https:// URL zur Datenschutzrichtlinie des Entwicklers.</span><span class="sxs-lookup"><span data-stu-id="c2685-154">The https:// URL to the developer's privacy policy.</span></span>|
|`termsOfUseUrl`|<span data-ttu-id="c2685-155">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="c2685-155">2048 characters</span></span>|<span data-ttu-id="c2685-156">✔</span><span class="sxs-lookup"><span data-stu-id="c2685-156">✔</span></span>|<span data-ttu-id="c2685-157">Die https:// URL zu den Nutzungsbedingungen des Entwicklers.</span><span class="sxs-lookup"><span data-stu-id="c2685-157">The https:// URL to the developer's terms of use.</span></span>|
|`mpnId`|<span data-ttu-id="c2685-158">10 Zeichen</span><span class="sxs-lookup"><span data-stu-id="c2685-158">10 characters</span></span>| |<span data-ttu-id="c2685-159">**Optional** Die Microsoft Partner Network-ID, die die Partnerorganisation identifiziert, die die App erstellt.</span><span class="sxs-lookup"><span data-stu-id="c2685-159">**Optional** The Microsoft Partner Network ID that identifies the partner organization building the app.</span></span>|

## <a name="name"></a><span data-ttu-id="c2685-160">name</span><span class="sxs-lookup"><span data-stu-id="c2685-160">name</span></span>

<span data-ttu-id="c2685-161">**Erforderlich** – Objekt</span><span class="sxs-lookup"><span data-stu-id="c2685-161">**Required** — object</span></span>

<span data-ttu-id="c2685-162">Der Name Ihrer App-Erfahrung, der Benutzern in der Teams-Benutzeroberfläche angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="c2685-162">The name of your app experience, displayed to users in the Teams experience.</span></span> <span data-ttu-id="c2685-163">Für an AppSource übermittelte Apps müssen diese Werte mit den Informationen in Ihrem AppSource-Eintrag übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="c2685-163">For apps submitted to AppSource, these values must match the information in your AppSource entry.</span></span> <span data-ttu-id="c2685-164">Die Werte von `short` und `full` müssen unterschiedlich sein.</span><span class="sxs-lookup"><span data-stu-id="c2685-164">The values of `short` and `full` must be different.</span></span>

|<span data-ttu-id="c2685-165">Name</span><span class="sxs-lookup"><span data-stu-id="c2685-165">Name</span></span>| <span data-ttu-id="c2685-166">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="c2685-166">Maximum size</span></span> | <span data-ttu-id="c2685-167">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="c2685-167">Required</span></span> | <span data-ttu-id="c2685-168">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="c2685-168">Description</span></span>|
|---|---|---|---|
|`short`|<span data-ttu-id="c2685-169">30 Zeichen</span><span class="sxs-lookup"><span data-stu-id="c2685-169">30 characters</span></span>|<span data-ttu-id="c2685-170">✔</span><span class="sxs-lookup"><span data-stu-id="c2685-170">✔</span></span>|<span data-ttu-id="c2685-171">Der kurze Anzeigename für die App.</span><span class="sxs-lookup"><span data-stu-id="c2685-171">The short display name for the app.</span></span>|
|`full`|<span data-ttu-id="c2685-172">100 Zeichen</span><span class="sxs-lookup"><span data-stu-id="c2685-172">100 characters</span></span>||<span data-ttu-id="c2685-173">Der vollständige Name der App, der verwendet wird, wenn der vollständige App-Name 30 Zeichen überschreitet.</span><span class="sxs-lookup"><span data-stu-id="c2685-173">The full name of the app, used if the full app name exceeds 30 characters.</span></span>|

## <a name="description"></a><span data-ttu-id="c2685-174">description</span><span class="sxs-lookup"><span data-stu-id="c2685-174">description</span></span>

<span data-ttu-id="c2685-175">**Erforderlich** – Objekt</span><span class="sxs-lookup"><span data-stu-id="c2685-175">**Required** — object</span></span>

<span data-ttu-id="c2685-176">Beschreibt Ihre App für Benutzer.</span><span class="sxs-lookup"><span data-stu-id="c2685-176">Describes your app to users.</span></span> <span data-ttu-id="c2685-177">Für an AppSource übermittelte Apps müssen diese Werte mit den Informationen in Ihrem AppSource-Eintrag übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="c2685-177">For apps submitted to AppSource, these values must match the information in your AppSource entry.</span></span>

<span data-ttu-id="c2685-178">Stellen Sie sicher, dass Ihre Beschreibung Ihre Erfahrung genau beschreibt und Informationen bereitstellt, die potenziellen Kunden helfen, zu verstehen, was Ihre Erfahrung bewirkt.</span><span class="sxs-lookup"><span data-stu-id="c2685-178">Ensure that your description accurately describes your experience and provides information to help potential customers understand what your experience does.</span></span> <span data-ttu-id="c2685-179">Sie müssen in der vollständigen Beschreibung notieren, ob ein externes Konto für die Verwendung erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="c2685-179">You must note in the full description, if an external account is required for use.</span></span> <span data-ttu-id="c2685-180">Die Werte von `short` und `full` müssen unterschiedlich sein.</span><span class="sxs-lookup"><span data-stu-id="c2685-180">The values of `short` and `full` must be different.</span></span> <span data-ttu-id="c2685-181">Ihre kurze Beschreibung darf nicht innerhalb der langen Beschreibung wiederholt werden und darf keinen anderen App-Namen enthalten.</span><span class="sxs-lookup"><span data-stu-id="c2685-181">Your short description must not be repeated within the long description and must not include any other app name.</span></span>

|<span data-ttu-id="c2685-182">Name</span><span class="sxs-lookup"><span data-stu-id="c2685-182">Name</span></span>| <span data-ttu-id="c2685-183">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="c2685-183">Maximum size</span></span> | <span data-ttu-id="c2685-184">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="c2685-184">Required</span></span> | <span data-ttu-id="c2685-185">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="c2685-185">Description</span></span>|
|---|---|---|---|
|`short`|<span data-ttu-id="c2685-186">80 Zeichen</span><span class="sxs-lookup"><span data-stu-id="c2685-186">80 characters</span></span>|<span data-ttu-id="c2685-187">✔</span><span class="sxs-lookup"><span data-stu-id="c2685-187">✔</span></span>|<span data-ttu-id="c2685-188">Eine kurze Beschreibung der App-Erfahrung, die verwendet wird, wenn der Platz begrenzt ist.</span><span class="sxs-lookup"><span data-stu-id="c2685-188">A short description of your app experience, used when space is limited.</span></span>|
|`full`|<span data-ttu-id="c2685-189">4000 Zeichen</span><span class="sxs-lookup"><span data-stu-id="c2685-189">4000 characters</span></span>|<span data-ttu-id="c2685-190">✔</span><span class="sxs-lookup"><span data-stu-id="c2685-190">✔</span></span>|<span data-ttu-id="c2685-191">Die vollständige Beschreibung Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="c2685-191">The full description of your app.</span></span>|

## <a name="packagename"></a><span data-ttu-id="c2685-192">Packagename</span><span class="sxs-lookup"><span data-stu-id="c2685-192">packageName</span></span>

<span data-ttu-id="c2685-193">**Optional** – Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="c2685-193">**Optional** — string</span></span>

<span data-ttu-id="c2685-194">Ein eindeutiger Bezeichner für die App in umgekehrter Domänenschreibweise; z. B. com.example.myapp.</span><span class="sxs-lookup"><span data-stu-id="c2685-194">A unique identifier for the app in reverse domain notation; for example, com.example.myapp.</span></span> <span data-ttu-id="c2685-195">Maximale Länge: 64 Zeichen.</span><span class="sxs-lookup"><span data-stu-id="c2685-195">Maximum length: 64 characters.</span></span>

## <a name="localizationinfo"></a><span data-ttu-id="c2685-196">localizationInfo</span><span class="sxs-lookup"><span data-stu-id="c2685-196">localizationInfo</span></span>

<span data-ttu-id="c2685-197">**Optional** - Objekt</span><span class="sxs-lookup"><span data-stu-id="c2685-197">**Optional** — object</span></span>

<span data-ttu-id="c2685-198">Ermöglicht die Angabe einer Standardsprache sowie Zeiger auf zusätzliche Sprachdateien.</span><span class="sxs-lookup"><span data-stu-id="c2685-198">Allows the specification of a default language, as well as pointers to additional language files.</span></span> <span data-ttu-id="c2685-199">Weitere Informationen finden Sie unter [Lokalisierung.](~/concepts/build-and-test/apps-localization.md)</span><span class="sxs-lookup"><span data-stu-id="c2685-199">For more information, see [localization](~/concepts/build-and-test/apps-localization.md).</span></span>

|<span data-ttu-id="c2685-200">Name</span><span class="sxs-lookup"><span data-stu-id="c2685-200">Name</span></span>| <span data-ttu-id="c2685-201">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="c2685-201">Maximum size</span></span> | <span data-ttu-id="c2685-202">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="c2685-202">Required</span></span> | <span data-ttu-id="c2685-203">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="c2685-203">Description</span></span>|
|---|---|---|---|
|`defaultLanguageTag`||<span data-ttu-id="c2685-204">✔</span><span class="sxs-lookup"><span data-stu-id="c2685-204">✔</span></span>|<span data-ttu-id="c2685-205">Das Sprachtag der Zeichenfolgen in dieser Manifestdatei auf oberster Ebene.</span><span class="sxs-lookup"><span data-stu-id="c2685-205">The language tag of the strings in this top level manifest file.</span></span>|

### <a name="localizationinfoadditionallanguages"></a><span data-ttu-id="c2685-206">localizationInfo.additionalLanguages</span><span class="sxs-lookup"><span data-stu-id="c2685-206">localizationInfo.additionalLanguages</span></span>

<span data-ttu-id="c2685-207">Ein Array von Objekten, die zusätzliche Sprachübersetzungen angeben.</span><span class="sxs-lookup"><span data-stu-id="c2685-207">An array of objects specifying additional language translations.</span></span>

|<span data-ttu-id="c2685-208">Name</span><span class="sxs-lookup"><span data-stu-id="c2685-208">Name</span></span>| <span data-ttu-id="c2685-209">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="c2685-209">Maximum size</span></span> | <span data-ttu-id="c2685-210">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="c2685-210">Required</span></span> | <span data-ttu-id="c2685-211">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="c2685-211">Description</span></span>|
|---|---|---|---|
|`languageTag`||<span data-ttu-id="c2685-212">✔</span><span class="sxs-lookup"><span data-stu-id="c2685-212">✔</span></span>|<span data-ttu-id="c2685-213">Das Sprachtag der Zeichenfolgen in der bereitgestellten Datei.</span><span class="sxs-lookup"><span data-stu-id="c2685-213">The language tag of the strings in the provided file.</span></span>|
|`file`||<span data-ttu-id="c2685-214">✔</span><span class="sxs-lookup"><span data-stu-id="c2685-214">✔</span></span>|<span data-ttu-id="c2685-215">Ein relativer Dateipfad zu einer JSON-Datei, die die übersetzten Zeichenfolgen enthält.</span><span class="sxs-lookup"><span data-stu-id="c2685-215">A relative file path to a the .json file containing the translated strings.</span></span>|

## <a name="icons"></a><span data-ttu-id="c2685-216">Symbole</span><span class="sxs-lookup"><span data-stu-id="c2685-216">icons</span></span>

<span data-ttu-id="c2685-217">**Erforderlich** – Objekt</span><span class="sxs-lookup"><span data-stu-id="c2685-217">**Required** — object</span></span>

<span data-ttu-id="c2685-218">Symbole, die in der Teams-App verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="c2685-218">Icons used within the Teams app.</span></span> <span data-ttu-id="c2685-219">Die Symboldateien müssen als Teil des Uploadpakets enthalten sein.</span><span class="sxs-lookup"><span data-stu-id="c2685-219">The icon files must be included as part of the upload package.</span></span> <span data-ttu-id="c2685-220">Weitere Informationen finden Sie unter ["Symbole".](../../concepts/build-and-test/apps-package.md#app-icons)</span><span class="sxs-lookup"><span data-stu-id="c2685-220">See [Icons](../../concepts/build-and-test/apps-package.md#app-icons) for more information.</span></span>

|<span data-ttu-id="c2685-221">Name</span><span class="sxs-lookup"><span data-stu-id="c2685-221">Name</span></span>| <span data-ttu-id="c2685-222">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="c2685-222">Maximum size</span></span> | <span data-ttu-id="c2685-223">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="c2685-223">Required</span></span> | <span data-ttu-id="c2685-224">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="c2685-224">Description</span></span>|
|---|---|---|---|
|`outline`|<span data-ttu-id="c2685-225">32 x 32 Pixel</span><span class="sxs-lookup"><span data-stu-id="c2685-225">32 x 32 pixels</span></span>|<span data-ttu-id="c2685-226">✔</span><span class="sxs-lookup"><span data-stu-id="c2685-226">✔</span></span>|<span data-ttu-id="c2685-227">Ein relativer Dateipfad zu einem transparenten 32 x 32 PNG-Gliederungssymbol.</span><span class="sxs-lookup"><span data-stu-id="c2685-227">A relative file path to a transparent 32x32 PNG outline icon.</span></span>|
|`color`|<span data-ttu-id="c2685-228">192 x 192 Pixel</span><span class="sxs-lookup"><span data-stu-id="c2685-228">192 x 192 pixels</span></span>|<span data-ttu-id="c2685-229">✔</span><span class="sxs-lookup"><span data-stu-id="c2685-229">✔</span></span>|<span data-ttu-id="c2685-230">Ein relativer Dateipfad zu einem farbigen PNG-Symbol mit 192 x 192.</span><span class="sxs-lookup"><span data-stu-id="c2685-230">A relative file path to a full color 192x192 PNG icon.</span></span>|

## <a name="accentcolor"></a><span data-ttu-id="c2685-231">accentColor</span><span class="sxs-lookup"><span data-stu-id="c2685-231">accentColor</span></span>

<span data-ttu-id="c2685-232">**Optional** – HTML Hex-Farbcode</span><span class="sxs-lookup"><span data-stu-id="c2685-232">**Optional** — HTML Hex color code</span></span>

<span data-ttu-id="c2685-233">Eine Farbe, die in Verbindung mit und als Hintergrund für Ihre Gliederungssymbole verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="c2685-233">A color to use in conjunction with and as a background for your outline icons.</span></span>

<span data-ttu-id="c2685-234">Der Wert muss ein gültiger HTML-Farbcode sein, der mit "#" beginnt, z. `#4464ee` B. .</span><span class="sxs-lookup"><span data-stu-id="c2685-234">The value must be a valid HTML color code starting with '#', for example `#4464ee`.</span></span>

## <a name="configurabletabs"></a><span data-ttu-id="c2685-235">configurableTabs</span><span class="sxs-lookup"><span data-stu-id="c2685-235">configurableTabs</span></span>

<span data-ttu-id="c2685-236">**Optional** – Array</span><span class="sxs-lookup"><span data-stu-id="c2685-236">**Optional** — array</span></span>

<span data-ttu-id="c2685-237">Wird verwendet, wenn Ihre App-Erfahrung über eine Registerkartenoberfläche im Teamkanal verfügt, die eine zusätzliche Konfiguration erfordert, bevor sie hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="c2685-237">Used when your app experience has a team channel tab experience that requires extra configuration before it is added.</span></span> <span data-ttu-id="c2685-238">Konfigurierbare Registerkarten werden nur im Teams-Bereich unterstützt, und Sie können dieselben Registerkarten mehrmals konfigurieren.</span><span class="sxs-lookup"><span data-stu-id="c2685-238">Configurable tabs are supported only in the teams scope and you can configure the same tabs multiple times.</span></span> <span data-ttu-id="c2685-239">Sie können sie jedoch nur einmal im Manifest definieren.</span><span class="sxs-lookup"><span data-stu-id="c2685-239">However, you can define it in the manifest only once.</span></span>

|<span data-ttu-id="c2685-240">Name</span><span class="sxs-lookup"><span data-stu-id="c2685-240">Name</span></span>| <span data-ttu-id="c2685-241">Typ</span><span class="sxs-lookup"><span data-stu-id="c2685-241">Type</span></span>| <span data-ttu-id="c2685-242">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="c2685-242">Maximum size</span></span> | <span data-ttu-id="c2685-243">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="c2685-243">Required</span></span> | <span data-ttu-id="c2685-244">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="c2685-244">Description</span></span>|
|---|---|---|---|---|
|`configurationUrl`|<span data-ttu-id="c2685-245">string</span><span class="sxs-lookup"><span data-stu-id="c2685-245">string</span></span>|<span data-ttu-id="c2685-246">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="c2685-246">2048 characters</span></span>|<span data-ttu-id="c2685-247">✔</span><span class="sxs-lookup"><span data-stu-id="c2685-247">✔</span></span>|<span data-ttu-id="c2685-248">Die https:// URL, die beim Konfigurieren der Registerkarte verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="c2685-248">The https:// URL to use when configuring the tab.</span></span>|
|`scopes`|<span data-ttu-id="c2685-249">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="c2685-249">array of enums</span></span>|<span data-ttu-id="c2685-250">1</span><span class="sxs-lookup"><span data-stu-id="c2685-250">1</span></span>|<span data-ttu-id="c2685-251">✔</span><span class="sxs-lookup"><span data-stu-id="c2685-251">✔</span></span>|<span data-ttu-id="c2685-252">Derzeit unterstützen konfigurierbare Registerkarten nur die `team` Bereiche und `groupchat` Bereiche.</span><span class="sxs-lookup"><span data-stu-id="c2685-252">Currently, configurable tabs support only the `team` and `groupchat` scopes.</span></span> |
|`canUpdateConfiguration`|<span data-ttu-id="c2685-253">Boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="c2685-253">boolean</span></span>|||<span data-ttu-id="c2685-254">Ein Wert, der angibt, ob eine Instanz der Konfiguration der Registerkarte vom Benutzer nach der Erstellung aktualisiert werden kann.</span><span class="sxs-lookup"><span data-stu-id="c2685-254">A value indicating whether an instance of the tab's configuration can be updated by the user after creation.</span></span> <span data-ttu-id="c2685-255">Standard: **true**.</span><span class="sxs-lookup"><span data-stu-id="c2685-255">Default: **true**.</span></span>|
|`context` |<span data-ttu-id="c2685-256">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="c2685-256">array of enums</span></span>|<span data-ttu-id="c2685-257">6 </span><span class="sxs-lookup"><span data-stu-id="c2685-257">6</span></span>||<span data-ttu-id="c2685-258">Die Gruppe von `contextItem` Bereichen, in denen eine [Registerkarte unterstützt wird.](../../tabs/how-to/access-teams-context.md)</span><span class="sxs-lookup"><span data-stu-id="c2685-258">The set of `contextItem` scopes where a [tab is supported](../../tabs/how-to/access-teams-context.md).</span></span> <span data-ttu-id="c2685-259">Standard: **[channelTab, privateChatTab, meetingChatTab, meetingDetailsTab]**.</span><span class="sxs-lookup"><span data-stu-id="c2685-259">Default: **[channelTab, privateChatTab, meetingChatTab, meetingDetailsTab]**.</span></span>|
|`sharePointPreviewImage`|<span data-ttu-id="c2685-260">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="c2685-260">string</span></span>|<span data-ttu-id="c2685-261">2048</span><span class="sxs-lookup"><span data-stu-id="c2685-261">2048</span></span>||<span data-ttu-id="c2685-262">Ein relativer Dateipfad zu einem Registerkartenvorschaubild zur Verwendung in SharePoint.</span><span class="sxs-lookup"><span data-stu-id="c2685-262">A relative file path to a tab preview image for use in SharePoint.</span></span> <span data-ttu-id="c2685-263">Größe 1024 x 768.</span><span class="sxs-lookup"><span data-stu-id="c2685-263">Size 1024x768.</span></span> |
|`supportedSharePointHosts`|<span data-ttu-id="c2685-264">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="c2685-264">array of enums</span></span>|<span data-ttu-id="c2685-265">1</span><span class="sxs-lookup"><span data-stu-id="c2685-265">1</span></span>||<span data-ttu-id="c2685-266">Definiert, wie Ihre Registerkarte in SharePoint zur Verfügung gestellt wird.</span><span class="sxs-lookup"><span data-stu-id="c2685-266">Defines how your tab is made available in SharePoint.</span></span> <span data-ttu-id="c2685-267">Optionen sind `sharePointFullPage` und `sharePointWebPart`</span><span class="sxs-lookup"><span data-stu-id="c2685-267">Options are `sharePointFullPage` and `sharePointWebPart`</span></span> |

## <a name="statictabs"></a><span data-ttu-id="c2685-268">staticTabs</span><span class="sxs-lookup"><span data-stu-id="c2685-268">staticTabs</span></span>

<span data-ttu-id="c2685-269">**Optional** – Array</span><span class="sxs-lookup"><span data-stu-id="c2685-269">**Optional** — array</span></span>

<span data-ttu-id="c2685-270">Definiert eine Gruppe von Registerkarten, die standardmäßig "angeheftet" werden können, ohne dass der Benutzer sie manuell hinzufügt.</span><span class="sxs-lookup"><span data-stu-id="c2685-270">Defines a set of tabs that can be "pinned" by default, without the user adding them manually.</span></span> <span data-ttu-id="c2685-271">Im Bereich deklarierte statische `personal` Registerkarten werden immer an die persönliche Benutzeroberfläche der App angeheftet.</span><span class="sxs-lookup"><span data-stu-id="c2685-271">Static tabs declared in `personal` scope are always pinned to the app's personal experience.</span></span> <span data-ttu-id="c2685-272">Statische Registerkarten, die im Bereich deklariert `team` sind, werden derzeit nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="c2685-272">Static tabs declared in the `team` scope are currently not supported.</span></span>

<span data-ttu-id="c2685-273">Dieses Element ist ein Array (maximal 16 Elemente) mit allen Elementen des `object` Typs.</span><span class="sxs-lookup"><span data-stu-id="c2685-273">This item is an array (maximum of 16 elements) with all elements of the type `object`.</span></span> <span data-ttu-id="c2685-274">Dieser Block ist nur für Lösungen erforderlich, die eine statische Registerkartenlösung bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="c2685-274">This block is required only for solutions that provide a static tab solution.</span></span>

|<span data-ttu-id="c2685-275">Name</span><span class="sxs-lookup"><span data-stu-id="c2685-275">Name</span></span>| <span data-ttu-id="c2685-276">Typ</span><span class="sxs-lookup"><span data-stu-id="c2685-276">Type</span></span>| <span data-ttu-id="c2685-277">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="c2685-277">Maximum size</span></span> | <span data-ttu-id="c2685-278">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="c2685-278">Required</span></span> | <span data-ttu-id="c2685-279">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="c2685-279">Description</span></span>|
|---|---|---|---|---|
|`entityId`|<span data-ttu-id="c2685-280">string</span><span class="sxs-lookup"><span data-stu-id="c2685-280">string</span></span>|<span data-ttu-id="c2685-281">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="c2685-281">64 characters</span></span>|<span data-ttu-id="c2685-282">✔</span><span class="sxs-lookup"><span data-stu-id="c2685-282">✔</span></span>|<span data-ttu-id="c2685-283">Ein eindeutiger Bezeichner für die Entität, die auf der Registerkarte angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="c2685-283">A unique identifier for the entity that the tab displays.</span></span>|
|`name`|<span data-ttu-id="c2685-284">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="c2685-284">string</span></span>|<span data-ttu-id="c2685-285">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="c2685-285">128 characters</span></span>|<span data-ttu-id="c2685-286">✔</span><span class="sxs-lookup"><span data-stu-id="c2685-286">✔</span></span>|<span data-ttu-id="c2685-287">Der Anzeigename der Registerkarte in der Kanalschnittstelle.</span><span class="sxs-lookup"><span data-stu-id="c2685-287">The display name of the tab in the channel interface.</span></span>|
|`contentUrl`|<span data-ttu-id="c2685-288">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="c2685-288">string</span></span>||<span data-ttu-id="c2685-289">✔</span><span class="sxs-lookup"><span data-stu-id="c2685-289">✔</span></span>|<span data-ttu-id="c2685-290">Die https:// URL, die auf die Entitäts-UI verweist, die im Teams Canvas angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="c2685-290">The https:// URL that points to the entity UI to be displayed in the Teams canvas.</span></span>|
|`websiteUrl`|<span data-ttu-id="c2685-291">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="c2685-291">string</span></span>|||<span data-ttu-id="c2685-292">Die https:// URL, auf die verweist, wenn sich ein Benutzer für die Anzeige in einem Browser entscheidet.</span><span class="sxs-lookup"><span data-stu-id="c2685-292">The https:// URL to point to if a user opts to view in a browser.</span></span>|
|`searchUrl`|<span data-ttu-id="c2685-293">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="c2685-293">string</span></span>|||<span data-ttu-id="c2685-294">Die https:// URL, auf die für die Suchabfragen eines Benutzers verweist.</span><span class="sxs-lookup"><span data-stu-id="c2685-294">The https:// URL to point to for a user's search queries.</span></span>|
|`scopes`|<span data-ttu-id="c2685-295">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="c2685-295">array of enums</span></span>|<span data-ttu-id="c2685-296">1</span><span class="sxs-lookup"><span data-stu-id="c2685-296">1</span></span>|<span data-ttu-id="c2685-297">✔</span><span class="sxs-lookup"><span data-stu-id="c2685-297">✔</span></span>|<span data-ttu-id="c2685-298">Derzeit unterstützen statische Registerkarten nur den `personal` Bereich, was bedeutet, dass sie nur als Teil der persönlichen Benutzeroberfläche bereitgestellt werden können.</span><span class="sxs-lookup"><span data-stu-id="c2685-298">Currently, static tabs support only the `personal` scope, which means it can be provisioned only as part of the personal experience.</span></span>|
|`context` | <span data-ttu-id="c2685-299">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="c2685-299">array of enums</span></span>| <span data-ttu-id="c2685-300">2</span><span class="sxs-lookup"><span data-stu-id="c2685-300">2</span></span>|| <span data-ttu-id="c2685-301">Die Gruppe von `contextItem` Bereichen, in denen eine Registerkarte unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="c2685-301">The set of `contextItem` scopes where a tab is supported.</span></span>|

> [!NOTE]
>  <span data-ttu-id="c2685-302">Das searchUrl-Feature ist für Drittanbieterentwickler nicht verfügbar.</span><span class="sxs-lookup"><span data-stu-id="c2685-302">The searchUrl feature is not available for the third-party developers.</span></span>
> <span data-ttu-id="c2685-303">Wenn Ihre Registerkarten kontextabhängige Informationen zum Anzeigen relevanter Inhalte oder zum Initiieren eines Authentifizierungsflusses benötigen, finden Sie weitere Informationen unter ["Kontext für Ihre Microsoft Teams Registerkarte abrufen".](../../tabs/how-to/access-teams-context.md)</span><span class="sxs-lookup"><span data-stu-id="c2685-303">If your tabs require context-dependent information to display relevant content or for initiating an authentication flow, For more information, see [Get context for your Microsoft Teams tab](../../tabs/how-to/access-teams-context.md).</span></span>

## <a name="bots"></a><span data-ttu-id="c2685-304">Bots</span><span class="sxs-lookup"><span data-stu-id="c2685-304">bots</span></span>

<span data-ttu-id="c2685-305">**Optional** – Array</span><span class="sxs-lookup"><span data-stu-id="c2685-305">**Optional** — array</span></span>

<span data-ttu-id="c2685-306">Definiert eine Bot-Lösung zusammen mit optionalen Informationen wie Standardbefehlseigenschaften.</span><span class="sxs-lookup"><span data-stu-id="c2685-306">Defines a bot solution, along with optional information such as default command properties.</span></span>

<span data-ttu-id="c2685-307">Das Element ist ein Array (maximal 1 Element &mdash; ist derzeit nur ein Bot pro App zulässig) mit allen Elementen des `object` Typs.</span><span class="sxs-lookup"><span data-stu-id="c2685-307">The item is an array (maximum of only 1 element&mdash;currently only one bot is allowed per app) with all elements of the type `object`.</span></span> <span data-ttu-id="c2685-308">Dieser Block ist nur für Lösungen erforderlich, die eine Bot-Erfahrung bieten.</span><span class="sxs-lookup"><span data-stu-id="c2685-308">This block is required only for solutions that provide a bot experience.</span></span>

|<span data-ttu-id="c2685-309">Name</span><span class="sxs-lookup"><span data-stu-id="c2685-309">Name</span></span>| <span data-ttu-id="c2685-310">Typ</span><span class="sxs-lookup"><span data-stu-id="c2685-310">Type</span></span>| <span data-ttu-id="c2685-311">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="c2685-311">Maximum size</span></span> | <span data-ttu-id="c2685-312">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="c2685-312">Required</span></span> | <span data-ttu-id="c2685-313">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="c2685-313">Description</span></span>|
|---|---|---|---|---|
|`botId`|<span data-ttu-id="c2685-314">string</span><span class="sxs-lookup"><span data-stu-id="c2685-314">string</span></span>|<span data-ttu-id="c2685-315">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="c2685-315">64 characters</span></span>|<span data-ttu-id="c2685-316">✔</span><span class="sxs-lookup"><span data-stu-id="c2685-316">✔</span></span>|<span data-ttu-id="c2685-317">Die eindeutige Microsoft-App-ID für den Bot, wie bei Bot Framework registriert.</span><span class="sxs-lookup"><span data-stu-id="c2685-317">The unique Microsoft app ID for the bot as registered with the Bot Framework.</span></span> <span data-ttu-id="c2685-318">Dies kann durchaus mit der gesamten [App-ID](#id)übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="c2685-318">This may well be the same as the overall [app ID](#id).</span></span>|
|`scopes`|<span data-ttu-id="c2685-319">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="c2685-319">array of enums</span></span>|<span data-ttu-id="c2685-320">3</span><span class="sxs-lookup"><span data-stu-id="c2685-320">3</span></span>|<span data-ttu-id="c2685-321">✔</span><span class="sxs-lookup"><span data-stu-id="c2685-321">✔</span></span>|<span data-ttu-id="c2685-322">Gibt an, ob der Bot eine Umgebung im Kontext eines Kanals in einem `team` oder Gruppenchat (`groupchat`) ist, oder aber eine Umgebung einzig für einen bestimmten Benutzer (`personal`).</span><span class="sxs-lookup"><span data-stu-id="c2685-322">Specifies whether the bot offers an experience in the context of a channel in a `team`, in a group chat (`groupchat`), or an experience scoped to an individual user alone (`personal`).</span></span> <span data-ttu-id="c2685-323">Diese Optionen sind nicht exklusiv.</span><span class="sxs-lookup"><span data-stu-id="c2685-323">These options are non-exclusive.</span></span>|
|`needsChannelSelector`|<span data-ttu-id="c2685-324">Boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="c2685-324">boolean</span></span>|||<span data-ttu-id="c2685-325">Beschreibt, ob der Bot einen Benutzerhinweis verwendet, um den Bot einem bestimmten Kanal hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="c2685-325">Describes whether or not the bot utilizes a user hint to add the bot to a specific channel.</span></span> <span data-ttu-id="c2685-326">Standard: **`false`**</span><span class="sxs-lookup"><span data-stu-id="c2685-326">Default: **`false`**</span></span>|
|`isNotificationOnly`|<span data-ttu-id="c2685-327">Boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="c2685-327">boolean</span></span>|||<span data-ttu-id="c2685-328">Gibt an, ob ein Bot ein unidirektionaler Bot ausschließlich für Benachrichtigungen ist (im Gegensatz zu einem dialogorientierten Bot).</span><span class="sxs-lookup"><span data-stu-id="c2685-328">Indicates whether a bot is a one-way, notification-only bot, as opposed to a conversational bot.</span></span> <span data-ttu-id="c2685-329">Standard: **`false`**</span><span class="sxs-lookup"><span data-stu-id="c2685-329">Default: **`false`**</span></span>|
|`supportsFiles`|<span data-ttu-id="c2685-330">Boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="c2685-330">boolean</span></span>|||<span data-ttu-id="c2685-331">Gibt an, ob der Bot die Möglichkeit zum Hochladen/Herunterladen von Dateien in persönliche Chats unterstützt.</span><span class="sxs-lookup"><span data-stu-id="c2685-331">Indicates whether the bot supports the ability to upload/download files in personal chat.</span></span> <span data-ttu-id="c2685-332">Standard: **`false`**</span><span class="sxs-lookup"><span data-stu-id="c2685-332">Default: **`false`**</span></span>|
|`supportsCalling`|<span data-ttu-id="c2685-333">Boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="c2685-333">boolean</span></span>|||<span data-ttu-id="c2685-334">Ein Wert, der angibt, wo ein Bot Audioanrufe unterstützt.</span><span class="sxs-lookup"><span data-stu-id="c2685-334">A value indicating where a bot supports audio calling.</span></span> <span data-ttu-id="c2685-335">**WICHTIG:** Diese Eigenschaft ist derzeit experimentell.</span><span class="sxs-lookup"><span data-stu-id="c2685-335">**IMPORTANT**: This property is currently experimental.</span></span> <span data-ttu-id="c2685-336">Experimentelle Eigenschaften sind möglicherweise nicht vollständig und werden möglicherweise geändert, bevor sie vollständig verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="c2685-336">Experimental properties may not be complete, and may undergo changes before becoming fully available.</span></span>  <span data-ttu-id="c2685-337">Es wird nur zu Test- und Untersuchungszwecken bereitgestellt und darf nicht in Produktionsanwendungen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="c2685-337">It is provided for testing and exploration purposes only and must not be used in production applications.</span></span> <span data-ttu-id="c2685-338">Standard: **`false`**</span><span class="sxs-lookup"><span data-stu-id="c2685-338">Default: **`false`**</span></span>|
|`supportsVideo`|<span data-ttu-id="c2685-339">Boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="c2685-339">boolean</span></span>|||<span data-ttu-id="c2685-340">Ein Wert, der angibt, wo ein Bot Videoanrufe unterstützt.</span><span class="sxs-lookup"><span data-stu-id="c2685-340">A value indicating where a bot supports video calling.</span></span> <span data-ttu-id="c2685-341">**WICHTIG:** Diese Eigenschaft ist derzeit experimentell.</span><span class="sxs-lookup"><span data-stu-id="c2685-341">**IMPORTANT**: This property is currently experimental.</span></span> <span data-ttu-id="c2685-342">Experimentelle Eigenschaften sind möglicherweise nicht vollständig und werden möglicherweise geändert, bevor sie vollständig verfügbar sind.</span><span class="sxs-lookup"><span data-stu-id="c2685-342">Experimental properties may not be complete, and may undergo changes before becoming fully available.</span></span>  <span data-ttu-id="c2685-343">Es wird nur zu Test- und Untersuchungszwecken bereitgestellt und darf nicht in Produktionsanwendungen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="c2685-343">It is provided for testing and exploration purposes only and must not be used in production applications.</span></span> <span data-ttu-id="c2685-344">Standard: **`false`**</span><span class="sxs-lookup"><span data-stu-id="c2685-344">Default: **`false`**</span></span>|

### <a name="botscommandlists"></a><span data-ttu-id="c2685-345">bots.commandLists</span><span class="sxs-lookup"><span data-stu-id="c2685-345">bots.commandLists</span></span>

<span data-ttu-id="c2685-346">Eine optionale Liste von Befehlen, die Ihr Bot Benutzern empfehlen kann.</span><span class="sxs-lookup"><span data-stu-id="c2685-346">An optional list of commands that your bot can recommend to users.</span></span> <span data-ttu-id="c2685-347">Das Objekt ist ein Array (maximal 2 Elemente) mit allen Elementen des `object` Typs. Sie müssen eine separate Befehlsliste für jeden Bereich definieren, den Ihr Bot unterstützt.</span><span class="sxs-lookup"><span data-stu-id="c2685-347">The object is an array (maximum of 2 elements) with all elements of type `object`; you must define a separate command list for each scope that your bot supports.</span></span> <span data-ttu-id="c2685-348">Weitere Informationen finden Sie [in den Bot-Menüs.](~/bots/how-to/create-a-bot-commands-menu.md)</span><span class="sxs-lookup"><span data-stu-id="c2685-348">See [Bot menus](~/bots/how-to/create-a-bot-commands-menu.md) for more information.</span></span>

|<span data-ttu-id="c2685-349">Name</span><span class="sxs-lookup"><span data-stu-id="c2685-349">Name</span></span>| <span data-ttu-id="c2685-350">Typ</span><span class="sxs-lookup"><span data-stu-id="c2685-350">Type</span></span>| <span data-ttu-id="c2685-351">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="c2685-351">Maximum size</span></span> | <span data-ttu-id="c2685-352">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="c2685-352">Required</span></span> | <span data-ttu-id="c2685-353">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="c2685-353">Description</span></span>|
|---|---|---|---|---|
|`items.scopes`|<span data-ttu-id="c2685-354">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="c2685-354">array of enums</span></span>|<span data-ttu-id="c2685-355">3</span><span class="sxs-lookup"><span data-stu-id="c2685-355">3</span></span>|<span data-ttu-id="c2685-356">✔</span><span class="sxs-lookup"><span data-stu-id="c2685-356">✔</span></span>|<span data-ttu-id="c2685-357">Gibt den Bereich an, für den die Befehlsliste gültig ist.</span><span class="sxs-lookup"><span data-stu-id="c2685-357">Specifies the scope for which the command list is valid.</span></span> <span data-ttu-id="c2685-358">Mögliche Optionen sind `team`, `personal` und `groupchat`.</span><span class="sxs-lookup"><span data-stu-id="c2685-358">Options are `team`, `personal`, and `groupchat`.</span></span>|
|`items.commands`|<span data-ttu-id="c2685-359">Array von Objekten</span><span class="sxs-lookup"><span data-stu-id="c2685-359">array of objects</span></span>|<span data-ttu-id="c2685-360">10</span><span class="sxs-lookup"><span data-stu-id="c2685-360">10</span></span>|<span data-ttu-id="c2685-361">✔</span><span class="sxs-lookup"><span data-stu-id="c2685-361">✔</span></span>|<span data-ttu-id="c2685-362">Ein Array von Befehlen, die der Bot unterstützt:</span><span class="sxs-lookup"><span data-stu-id="c2685-362">An array of commands the bot supports:</span></span><br><span data-ttu-id="c2685-363">`title`: Name des Bot-Befehls (string, 32)</span><span class="sxs-lookup"><span data-stu-id="c2685-363">`title`: the bot command name (string, 32)</span></span><br><span data-ttu-id="c2685-364">`description`: eine einfache Beschreibung oder ein Beispiel für die Befehlssyntax und ihr Argument (Zeichenfolge, 128).</span><span class="sxs-lookup"><span data-stu-id="c2685-364">`description`: a simple description or example of the command syntax and its argument (string, 128).</span></span>|

### <a name="botscommandlistscommands"></a><span data-ttu-id="c2685-365">bots.commandLists.commands</span><span class="sxs-lookup"><span data-stu-id="c2685-365">bots.commandLists.commands</span></span>

|<span data-ttu-id="c2685-366">Name</span><span class="sxs-lookup"><span data-stu-id="c2685-366">Name</span></span>| <span data-ttu-id="c2685-367">Typ</span><span class="sxs-lookup"><span data-stu-id="c2685-367">Type</span></span>| <span data-ttu-id="c2685-368">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="c2685-368">Maximum size</span></span> | <span data-ttu-id="c2685-369">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="c2685-369">Required</span></span> | <span data-ttu-id="c2685-370">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="c2685-370">Description</span></span>|
|---|---|---|---|---|
|<span data-ttu-id="c2685-371">title</span><span class="sxs-lookup"><span data-stu-id="c2685-371">title</span></span>|<span data-ttu-id="c2685-372">string</span><span class="sxs-lookup"><span data-stu-id="c2685-372">string</span></span>|<span data-ttu-id="c2685-373">12 </span><span class="sxs-lookup"><span data-stu-id="c2685-373">12</span></span>|<span data-ttu-id="c2685-374">✔</span><span class="sxs-lookup"><span data-stu-id="c2685-374">✔</span></span>|<span data-ttu-id="c2685-375">Der Bot-Befehlsname.</span><span class="sxs-lookup"><span data-stu-id="c2685-375">The bot command name.</span></span>|
|<span data-ttu-id="c2685-376">description</span><span class="sxs-lookup"><span data-stu-id="c2685-376">description</span></span>|<span data-ttu-id="c2685-377">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="c2685-377">string</span></span>|<span data-ttu-id="c2685-378">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="c2685-378">128 characters</span></span>|<span data-ttu-id="c2685-379">✔</span><span class="sxs-lookup"><span data-stu-id="c2685-379">✔</span></span>|<span data-ttu-id="c2685-380">Eine einfache Textbeschreibung oder ein Beispiel für die Befehlssyntax und deren Argumente.</span><span class="sxs-lookup"><span data-stu-id="c2685-380">A simple text description or an example of the command syntax and its arguments.</span></span>|

## <a name="connectors"></a><span data-ttu-id="c2685-381">Steckverbinder</span><span class="sxs-lookup"><span data-stu-id="c2685-381">connectors</span></span>

<span data-ttu-id="c2685-382">**Optional** – Array</span><span class="sxs-lookup"><span data-stu-id="c2685-382">**Optional** — array</span></span>

<span data-ttu-id="c2685-383">Der `connectors` Block definiert einen Office 365 Connector für die App.</span><span class="sxs-lookup"><span data-stu-id="c2685-383">The `connectors` block defines an Office 365 Connector for the app.</span></span>

<span data-ttu-id="c2685-384">Das Objekt ist ein Array (maximal 1 Element) mit allen Elementen des Typs `object` .</span><span class="sxs-lookup"><span data-stu-id="c2685-384">The object is an array (maximum of 1 element) with all elements of type `object`.</span></span> <span data-ttu-id="c2685-385">Dieser Block ist nur für Lösungen erforderlich, die einen Connector bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="c2685-385">This block is required only for solutions that provide a Connector.</span></span>

|<span data-ttu-id="c2685-386">Name</span><span class="sxs-lookup"><span data-stu-id="c2685-386">Name</span></span>| <span data-ttu-id="c2685-387">Typ</span><span class="sxs-lookup"><span data-stu-id="c2685-387">Type</span></span>| <span data-ttu-id="c2685-388">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="c2685-388">Maximum size</span></span> | <span data-ttu-id="c2685-389">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="c2685-389">Required</span></span> | <span data-ttu-id="c2685-390">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="c2685-390">Description</span></span>|
|---|---|---|---|---|
|`configurationUrl`|<span data-ttu-id="c2685-391">string</span><span class="sxs-lookup"><span data-stu-id="c2685-391">string</span></span>|<span data-ttu-id="c2685-392">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="c2685-392">2048 characters</span></span>|<span data-ttu-id="c2685-393">✔</span><span class="sxs-lookup"><span data-stu-id="c2685-393">✔</span></span>|<span data-ttu-id="c2685-394">Die https:// URL, die beim Konfigurieren des Connectors verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="c2685-394">The https:// URL to use when configuring the connector.</span></span>|
|`scopes`|<span data-ttu-id="c2685-395">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="c2685-395">array of enums</span></span>|<span data-ttu-id="c2685-396">1</span><span class="sxs-lookup"><span data-stu-id="c2685-396">1</span></span>|<span data-ttu-id="c2685-397">✔</span><span class="sxs-lookup"><span data-stu-id="c2685-397">✔</span></span>|<span data-ttu-id="c2685-398">Gibt an, ob der Connector eine Erfahrung im Kontext eines Kanals in einem oder `team` eine Benutzeroberfläche bietet, die auf einen einzelnen Benutzer beschränkt ist ( `personal` ).</span><span class="sxs-lookup"><span data-stu-id="c2685-398">Specifies whether the Connector offers an experience in the context of a channel in a `team`, or an experience scoped to an individual user alone (`personal`).</span></span> <span data-ttu-id="c2685-399">Derzeit wird nur der `team` Bereich unterstützt.</span><span class="sxs-lookup"><span data-stu-id="c2685-399">Currently, only the `team` scope is supported.</span></span>|
|`connectorId`|<span data-ttu-id="c2685-400">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="c2685-400">string</span></span>|<span data-ttu-id="c2685-401">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="c2685-401">64 characters</span></span>|<span data-ttu-id="c2685-402">✔</span><span class="sxs-lookup"><span data-stu-id="c2685-402">✔</span></span>|<span data-ttu-id="c2685-403">Ein eindeutiger Bezeichner für den Connector, der seiner ID im [Connectors Developer Dashboard](https://aka.ms/connectorsdashboard)entspricht.</span><span class="sxs-lookup"><span data-stu-id="c2685-403">A unique identifier for the Connector that matches its ID in the [Connectors Developer Dashboard](https://aka.ms/connectorsdashboard).</span></span>|

## <a name="composeextensions"></a><span data-ttu-id="c2685-404">composeExtensions</span><span class="sxs-lookup"><span data-stu-id="c2685-404">composeExtensions</span></span>

<span data-ttu-id="c2685-405">**Optional** – Array</span><span class="sxs-lookup"><span data-stu-id="c2685-405">**Optional** — array</span></span>

<span data-ttu-id="c2685-406">Definiert eine Messaging-Erweiterung für die App.</span><span class="sxs-lookup"><span data-stu-id="c2685-406">Defines a messaging extension for the app.</span></span>

> [!NOTE]
> <span data-ttu-id="c2685-407">Der Name des Features wurde im November 2017 von "Erstellerweiterung" in "Messaging-Erweiterung" geändert, aber der Manifestname bleibt unverändert, sodass vorhandene Erweiterungen weiterhin funktionieren.</span><span class="sxs-lookup"><span data-stu-id="c2685-407">The name of the feature was changed from "compose extension" to "messaging extension" in November, 2017, but the manifest name remains the same so that existing extensions continue to function.</span></span>

<span data-ttu-id="c2685-408">Das Element ist ein Array (maximal 1 Element) mit allen Elementen des Typs `object` .</span><span class="sxs-lookup"><span data-stu-id="c2685-408">The item is an array (maximum of 1 element) with all elements of type `object`.</span></span> <span data-ttu-id="c2685-409">Dieser Block ist nur für Lösungen erforderlich, die eine Messaging-Erweiterung bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="c2685-409">This block is required only for solutions that provide a messaging extension.</span></span>

|<span data-ttu-id="c2685-410">Name</span><span class="sxs-lookup"><span data-stu-id="c2685-410">Name</span></span>| <span data-ttu-id="c2685-411">Typ</span><span class="sxs-lookup"><span data-stu-id="c2685-411">Type</span></span> | <span data-ttu-id="c2685-412">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="c2685-412">Maximum Size</span></span> | <span data-ttu-id="c2685-413">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="c2685-413">Required</span></span> | <span data-ttu-id="c2685-414">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="c2685-414">Description</span></span>|
|---|---|---|---|---|
|`botId`|<span data-ttu-id="c2685-415">string</span><span class="sxs-lookup"><span data-stu-id="c2685-415">string</span></span>|<span data-ttu-id="c2685-416">64</span><span class="sxs-lookup"><span data-stu-id="c2685-416">64</span></span>|<span data-ttu-id="c2685-417">✔</span><span class="sxs-lookup"><span data-stu-id="c2685-417">✔</span></span>|<span data-ttu-id="c2685-418">Die eindeutige Microsoft-App-ID für den Bot, der die Messaging-Erweiterung unterstützt, wie beim Bot Framework registriert.</span><span class="sxs-lookup"><span data-stu-id="c2685-418">The unique Microsoft app ID for the bot that backs the messaging extension, as registered with the Bot Framework.</span></span> <span data-ttu-id="c2685-419">Dies kann durchaus mit der gesamten App-ID übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="c2685-419">This may well be the same as the overall App ID.</span></span>|
|`commands`|<span data-ttu-id="c2685-420">Array von Objekten</span><span class="sxs-lookup"><span data-stu-id="c2685-420">array of objects</span></span>|<span data-ttu-id="c2685-421">10</span><span class="sxs-lookup"><span data-stu-id="c2685-421">10</span></span>|<span data-ttu-id="c2685-422">✔</span><span class="sxs-lookup"><span data-stu-id="c2685-422">✔</span></span>|<span data-ttu-id="c2685-423">Array von Befehlen, die von der Messaging-Erweiterung unterstützt werden.</span><span class="sxs-lookup"><span data-stu-id="c2685-423">Array of commands the messaging extension supports.</span></span>|
|`canUpdateConfiguration`|<span data-ttu-id="c2685-424">Boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="c2685-424">boolean</span></span>|||<span data-ttu-id="c2685-425">Ein Wert, der angibt, ob die Konfiguration einer Messaging-Erweiterung vom Benutzer aktualisiert werden kann.</span><span class="sxs-lookup"><span data-stu-id="c2685-425">A value indicating whether the configuration of a messaging extension can be updated by the user.</span></span> <span data-ttu-id="c2685-426">Standard: **False**.</span><span class="sxs-lookup"><span data-stu-id="c2685-426">Default: **false**.</span></span>|
|`messageHandlers`|<span data-ttu-id="c2685-427">Array von Objekten</span><span class="sxs-lookup"><span data-stu-id="c2685-427">array of Objects</span></span>|<span data-ttu-id="c2685-428">5 </span><span class="sxs-lookup"><span data-stu-id="c2685-428">5</span></span>||<span data-ttu-id="c2685-429">Eine Liste von Handlern, mit denen Apps aufgerufen werden können, wenn bestimmte Bedingungen erfüllt sind.</span><span class="sxs-lookup"><span data-stu-id="c2685-429">A list of handlers that allow apps to be invoked when certain conditions are met.</span></span>|
|`messageHandlers.type`|<span data-ttu-id="c2685-430">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="c2685-430">string</span></span>|||<span data-ttu-id="c2685-431">Der Typ des Nachrichtenhandlers.</span><span class="sxs-lookup"><span data-stu-id="c2685-431">The type of message handler.</span></span> <span data-ttu-id="c2685-432">Muss `"link"` sein.</span><span class="sxs-lookup"><span data-stu-id="c2685-432">Must be `"link"`.</span></span>|
|`messageHandlers.value.domains`|<span data-ttu-id="c2685-433">Array von Zeichenfolgen</span><span class="sxs-lookup"><span data-stu-id="c2685-433">array of Strings</span></span>|||<span data-ttu-id="c2685-434">Array von Domänen, für die sich der Linknachrichtenhandler registrieren kann.</span><span class="sxs-lookup"><span data-stu-id="c2685-434">Array of domains that the link message handler can register for.</span></span>|

### <a name="composeextensionscommands"></a><span data-ttu-id="c2685-435">composeExtensions.commands</span><span class="sxs-lookup"><span data-stu-id="c2685-435">composeExtensions.commands</span></span>

<span data-ttu-id="c2685-436">Ihre Messaging-Erweiterung muss einen oder mehrere Befehle deklarieren.</span><span class="sxs-lookup"><span data-stu-id="c2685-436">Your messaging extension must declare one or more commands.</span></span> <span data-ttu-id="c2685-437">Jeder Befehl wird in Microsoft Teams als potenzielle Interaktion vom UI-basierten Einstiegspunkt angezeigt.</span><span class="sxs-lookup"><span data-stu-id="c2685-437">Each command appears in Microsoft Teams as a potential interaction from the UI-based entry point.</span></span> <span data-ttu-id="c2685-438">Es gibt maximal 10 Befehle.</span><span class="sxs-lookup"><span data-stu-id="c2685-438">There is a maximum of 10 commands.</span></span>

<span data-ttu-id="c2685-439">Jedes Befehlselement ist ein Objekt mit der folgenden Struktur:</span><span class="sxs-lookup"><span data-stu-id="c2685-439">Each command item is an object with the following structure:</span></span>

|<span data-ttu-id="c2685-440">Name</span><span class="sxs-lookup"><span data-stu-id="c2685-440">Name</span></span>| <span data-ttu-id="c2685-441">Typ</span><span class="sxs-lookup"><span data-stu-id="c2685-441">Type</span></span>| <span data-ttu-id="c2685-442">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="c2685-442">Maximum size</span></span> | <span data-ttu-id="c2685-443">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="c2685-443">Required</span></span> | <span data-ttu-id="c2685-444">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="c2685-444">Description</span></span>|
|---|---|---|---|---|
|`id`|<span data-ttu-id="c2685-445">string</span><span class="sxs-lookup"><span data-stu-id="c2685-445">string</span></span>|<span data-ttu-id="c2685-446">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="c2685-446">64 characters</span></span>|<span data-ttu-id="c2685-447">✔</span><span class="sxs-lookup"><span data-stu-id="c2685-447">✔</span></span>|<span data-ttu-id="c2685-448">Die ID für den Befehl.</span><span class="sxs-lookup"><span data-stu-id="c2685-448">The ID for the command.</span></span>|
|`title`|<span data-ttu-id="c2685-449">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="c2685-449">string</span></span>|<span data-ttu-id="c2685-450">32 Zeichen</span><span class="sxs-lookup"><span data-stu-id="c2685-450">32 characters</span></span>|<span data-ttu-id="c2685-451">✔</span><span class="sxs-lookup"><span data-stu-id="c2685-451">✔</span></span>|<span data-ttu-id="c2685-452">Der benutzerfreundliche Befehlsname.</span><span class="sxs-lookup"><span data-stu-id="c2685-452">The user-friendly command name.</span></span>|
|`type`|<span data-ttu-id="c2685-453">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="c2685-453">string</span></span>|<span data-ttu-id="c2685-454">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="c2685-454">64 characters</span></span>||<span data-ttu-id="c2685-455">Typ des Befehls.</span><span class="sxs-lookup"><span data-stu-id="c2685-455">Type of the command.</span></span> <span data-ttu-id="c2685-456">Eine von `query` oder `action` .</span><span class="sxs-lookup"><span data-stu-id="c2685-456">One of `query` or `action`.</span></span> <span data-ttu-id="c2685-457">Standard: **Abfrage**.</span><span class="sxs-lookup"><span data-stu-id="c2685-457">Default: **query**.</span></span>|
|`description`|<span data-ttu-id="c2685-458">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="c2685-458">string</span></span>|<span data-ttu-id="c2685-459">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="c2685-459">128 characters</span></span>||<span data-ttu-id="c2685-460">Die Beschreibung, die Benutzern angezeigt wird, um den Zweck dieses Befehls anzugeben.</span><span class="sxs-lookup"><span data-stu-id="c2685-460">The description that appears to users to indicate the purpose of this command.</span></span>|
|`initialRun`|<span data-ttu-id="c2685-461">Boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="c2685-461">boolean</span></span>|||<span data-ttu-id="c2685-462">Ein boolescher Wert gibt an, ob der Befehl anfänglich ohne Parameter ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="c2685-462">A boolean value indicates whether the command runs initially with no parameters.</span></span> <span data-ttu-id="c2685-463">Der Standardwert ist **false**.</span><span class="sxs-lookup"><span data-stu-id="c2685-463">Default is **false**.</span></span>|
|`context`|<span data-ttu-id="c2685-464">Array von Zeichenfolgen</span><span class="sxs-lookup"><span data-stu-id="c2685-464">array of Strings</span></span>|<span data-ttu-id="c2685-465">3</span><span class="sxs-lookup"><span data-stu-id="c2685-465">3</span></span>||<span data-ttu-id="c2685-466">Definiert, von wo aus die Nachrichtenerweiterung aufgerufen werden kann.</span><span class="sxs-lookup"><span data-stu-id="c2685-466">Defines where the message extension can be invoked from.</span></span> <span data-ttu-id="c2685-467">Eine beliebige Kombination von `compose` , `commandBox` , `message` .</span><span class="sxs-lookup"><span data-stu-id="c2685-467">Any combination of`compose`,`commandBox`,`message`.</span></span> <span data-ttu-id="c2685-468">Der Standardwert ist `["compose","commandBox"]`.</span><span class="sxs-lookup"><span data-stu-id="c2685-468">Default is `["compose","commandBox"]`.</span></span>|
|`fetchTask`|<span data-ttu-id="c2685-469">Boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="c2685-469">boolean</span></span>|||<span data-ttu-id="c2685-470">Ein boolescher Wert, der angibt, ob das Aufgabenmodul dynamisch abgerufen werden muss.</span><span class="sxs-lookup"><span data-stu-id="c2685-470">A boolean value that indicates if it must fetch the task module dynamically.</span></span> <span data-ttu-id="c2685-471">Der Standardwert ist **false**.</span><span class="sxs-lookup"><span data-stu-id="c2685-471">Default is **false**.</span></span>|
|`taskInfo`|<span data-ttu-id="c2685-472">Objekt</span><span class="sxs-lookup"><span data-stu-id="c2685-472">object</span></span>|||<span data-ttu-id="c2685-473">Geben Sie das Aufgabenmodul an, das vorab geladen werden soll, wenn Sie einen Messaging-Erweiterungsbefehl verwenden.</span><span class="sxs-lookup"><span data-stu-id="c2685-473">Specify the task module to pre-load when using a messaging extension command.</span></span>|
|`taskInfo.title`|<span data-ttu-id="c2685-474">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="c2685-474">string</span></span>|<span data-ttu-id="c2685-475">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="c2685-475">64 characters</span></span>||<span data-ttu-id="c2685-476">Titel des ersten Dialogfelds.</span><span class="sxs-lookup"><span data-stu-id="c2685-476">Initial dialog title.</span></span>|
|`taskInfo.width`|<span data-ttu-id="c2685-477">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="c2685-477">string</span></span>|||<span data-ttu-id="c2685-478">Dialogbreite – entweder eine Zahl in Pixeln oder ein Standardlayout, z. B. "groß", "mittel" oder "klein".</span><span class="sxs-lookup"><span data-stu-id="c2685-478">Dialog width - either a number in pixels or default layout such as 'large', 'medium', or 'small'.</span></span>|
|`taskInfo.height`|<span data-ttu-id="c2685-479">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="c2685-479">string</span></span>|||<span data-ttu-id="c2685-480">Dialoghöhe – entweder eine Zahl in Pixeln oder ein Standardlayout, z. B. "groß", "mittel" oder "klein".</span><span class="sxs-lookup"><span data-stu-id="c2685-480">Dialog height - either a number in pixels or default layout such as 'large', 'medium', or 'small'.</span></span>|
|`taskInfo.url`|<span data-ttu-id="c2685-481">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="c2685-481">string</span></span>|||<span data-ttu-id="c2685-482">Ursprüngliche Webansichts-URL.</span><span class="sxs-lookup"><span data-stu-id="c2685-482">Initial webview URL.</span></span>|
|`parameters`|<span data-ttu-id="c2685-483">Array des Objekts</span><span class="sxs-lookup"><span data-stu-id="c2685-483">array of object</span></span>|<span data-ttu-id="c2685-484">5 Elemente</span><span class="sxs-lookup"><span data-stu-id="c2685-484">5 items</span></span>|<span data-ttu-id="c2685-485">✔</span><span class="sxs-lookup"><span data-stu-id="c2685-485">✔</span></span>|<span data-ttu-id="c2685-486">Die Liste der Parameter, die der Befehl verwendet.</span><span class="sxs-lookup"><span data-stu-id="c2685-486">The list of parameters the command takes.</span></span> <span data-ttu-id="c2685-487">Minimum: 1; Maximum: 5.</span><span class="sxs-lookup"><span data-stu-id="c2685-487">Minimum: 1; maximum: 5.</span></span>|
|`parameters.name`|<span data-ttu-id="c2685-488">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="c2685-488">string</span></span>|<span data-ttu-id="c2685-489">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="c2685-489">64 characters</span></span>|<span data-ttu-id="c2685-490">✔</span><span class="sxs-lookup"><span data-stu-id="c2685-490">✔</span></span>|<span data-ttu-id="c2685-491">Der Name des Parameters, wie er im Client angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="c2685-491">The name of the parameter as it appears in the client.</span></span> <span data-ttu-id="c2685-492">Dies ist in der Benutzeranforderung enthalten.</span><span class="sxs-lookup"><span data-stu-id="c2685-492">This is included in the user request.</span></span>|
|`parameters.title`|<span data-ttu-id="c2685-493">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="c2685-493">string</span></span>|<span data-ttu-id="c2685-494">32 Zeichen</span><span class="sxs-lookup"><span data-stu-id="c2685-494">32 characters</span></span>|<span data-ttu-id="c2685-495">✔</span><span class="sxs-lookup"><span data-stu-id="c2685-495">✔</span></span>|<span data-ttu-id="c2685-496">Benutzerfreundlicher Titel für den Parameter.</span><span class="sxs-lookup"><span data-stu-id="c2685-496">User-friendly title for the parameter.</span></span>|
|`parameters.description`|<span data-ttu-id="c2685-497">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="c2685-497">string</span></span>|<span data-ttu-id="c2685-498">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="c2685-498">128 characters</span></span>||<span data-ttu-id="c2685-499">Benutzerfreundliche Zeichenfolge, die den Zweck dieses Parameters beschreibt.</span><span class="sxs-lookup"><span data-stu-id="c2685-499">User-friendly string that describes this parameter’s purpose.</span></span>|
|`parameters.value`|<span data-ttu-id="c2685-500">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="c2685-500">string</span></span>|<span data-ttu-id="c2685-501">512 Zeichen</span><span class="sxs-lookup"><span data-stu-id="c2685-501">512 characters</span></span>||<span data-ttu-id="c2685-502">Anfangswert für den Parameter.</span><span class="sxs-lookup"><span data-stu-id="c2685-502">Initial value for the parameter.</span></span>|
|`parameters.inputType`|<span data-ttu-id="c2685-503">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="c2685-503">string</span></span>|<span data-ttu-id="c2685-504">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="c2685-504">128 characters</span></span>||<span data-ttu-id="c2685-505">Definiert den Typ des Steuerelements, das in einem Aufgabenmodul für angezeigt `fetchTask: true` wird.</span><span class="sxs-lookup"><span data-stu-id="c2685-505">Defines the type of control displayed on a task module for`fetchTask: true` .</span></span> <span data-ttu-id="c2685-506">Eine von `text, textarea, number, date, time, toggle, choiceset` .</span><span class="sxs-lookup"><span data-stu-id="c2685-506">One of `text, textarea, number, date, time, toggle, choiceset` .</span></span>|
|`parameters.choices`|<span data-ttu-id="c2685-507">Array von Objekten</span><span class="sxs-lookup"><span data-stu-id="c2685-507">array of objects</span></span>|<span data-ttu-id="c2685-508">10 Elemente</span><span class="sxs-lookup"><span data-stu-id="c2685-508">10 items</span></span>||<span data-ttu-id="c2685-509">Die Auswahloptionen für die `choiceset` .</span><span class="sxs-lookup"><span data-stu-id="c2685-509">The choice options for the`choiceset`.</span></span> <span data-ttu-id="c2685-510">Wird nur verwendet, wenn `parameter.inputType` `choiceset` .</span><span class="sxs-lookup"><span data-stu-id="c2685-510">Use only when`parameter.inputType` is `choiceset`.</span></span>|
|`parameters.choices.title`|<span data-ttu-id="c2685-511">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="c2685-511">string</span></span>|<span data-ttu-id="c2685-512">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="c2685-512">128 characters</span></span>|<span data-ttu-id="c2685-513">✔</span><span class="sxs-lookup"><span data-stu-id="c2685-513">✔</span></span>|<span data-ttu-id="c2685-514">Titel der Wahl.</span><span class="sxs-lookup"><span data-stu-id="c2685-514">Title of the choice.</span></span>|
|`parameters.choices.value`|<span data-ttu-id="c2685-515">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="c2685-515">string</span></span>|<span data-ttu-id="c2685-516">512 Zeichen</span><span class="sxs-lookup"><span data-stu-id="c2685-516">512 characters</span></span>|<span data-ttu-id="c2685-517">✔</span><span class="sxs-lookup"><span data-stu-id="c2685-517">✔</span></span>|<span data-ttu-id="c2685-518">Value of the choice.</span><span class="sxs-lookup"><span data-stu-id="c2685-518">Value of the choice.</span></span>|

## <a name="permissions"></a><span data-ttu-id="c2685-519">Berechtigungen</span><span class="sxs-lookup"><span data-stu-id="c2685-519">permissions</span></span>

<span data-ttu-id="c2685-520">**Optional** – Array von Zeichenfolgen</span><span class="sxs-lookup"><span data-stu-id="c2685-520">**Optional** — array of strings</span></span>

<span data-ttu-id="c2685-521">Ein `string` Array, das angibt, welche Berechtigungen die App anfordert, wodurch Endbenutzer wissen, wie die Erweiterung funktioniert.</span><span class="sxs-lookup"><span data-stu-id="c2685-521">An array of `string` which specifies which permissions the app requests, which lets end users know how the extension performs.</span></span> <span data-ttu-id="c2685-522">Die folgenden Optionen sind nicht exklusiv:</span><span class="sxs-lookup"><span data-stu-id="c2685-522">The following options are non-exclusive:</span></span>

* <span data-ttu-id="c2685-523">`identity`&emsp;Erfordert Benutzeridentitätsinformationen.</span><span class="sxs-lookup"><span data-stu-id="c2685-523">`identity` &emsp; Requires user identity information.</span></span>
* <span data-ttu-id="c2685-524">`messageTeamMembers`&emsp;Erfordert die Berechtigung, direkte Nachrichten an Teammitglieder zu senden.</span><span class="sxs-lookup"><span data-stu-id="c2685-524">`messageTeamMembers` &emsp; Requires permission to send direct messages to team members.</span></span>

<span data-ttu-id="c2685-525">Wenn Sie diese Berechtigungen während des App-Updates ändern, müssen Ihre Benutzer den Zustimmungsprozess wiederholen, nachdem sie die aktualisierte App ausgeführt haben.</span><span class="sxs-lookup"><span data-stu-id="c2685-525">Changing these permissions during app update, causes your users to repeat the consent process after they run the updated app.</span></span> <span data-ttu-id="c2685-526">Weitere Informationen finden Sie unter [Aktualisieren Ihrer App.](~/concepts/deploy-and-publish/appsource/post-publish/overview.md)</span><span class="sxs-lookup"><span data-stu-id="c2685-526">See [Updating your app](~/concepts/deploy-and-publish/appsource/post-publish/overview.md) for more information.</span></span>

## <a name="devicepermissions"></a><span data-ttu-id="c2685-527">devicePermissions</span><span class="sxs-lookup"><span data-stu-id="c2685-527">devicePermissions</span></span>

<span data-ttu-id="c2685-528">**Optional** – Array von Zeichenfolgen</span><span class="sxs-lookup"><span data-stu-id="c2685-528">**Optional** — array of strings</span></span>

<span data-ttu-id="c2685-529">Stellt die systemeigenen Features auf dem Gerät eines Benutzers bereit, auf die Ihre App Zugriff anfordert.</span><span class="sxs-lookup"><span data-stu-id="c2685-529">Provides the native features on a user's device that your app requests access to.</span></span> <span data-ttu-id="c2685-530">Mögliche Optionen sind:</span><span class="sxs-lookup"><span data-stu-id="c2685-530">Options are:</span></span>

* `geolocation`
* `media`
* `notifications`
* `midi`
* `openExternal`

## <a name="validdomains"></a><span data-ttu-id="c2685-531">validDomains</span><span class="sxs-lookup"><span data-stu-id="c2685-531">validDomains</span></span>

<span data-ttu-id="c2685-532">**Optional,** außer **erforderlich,** sofern angegeben.</span><span class="sxs-lookup"><span data-stu-id="c2685-532">**Optional**, except **Required** where noted.</span></span>

<span data-ttu-id="c2685-533">Eine Liste der gültigen Domänen für Websites, die die App im Teams-Client laden möchte.</span><span class="sxs-lookup"><span data-stu-id="c2685-533">A list of valid domains for websites the app expects to load within the Teams client.</span></span> <span data-ttu-id="c2685-534">Domäneneinträge können Platzhalter enthalten, `*.example.com` z. B. .</span><span class="sxs-lookup"><span data-stu-id="c2685-534">Domain listings can include wildcards, for example, `*.example.com`.</span></span> <span data-ttu-id="c2685-535">Dies entspricht genau einem Segment der Domäne. wenn Sie übereinstimmen `a.b.example.com` müssen, verwenden Sie `*.*.example.com` .</span><span class="sxs-lookup"><span data-stu-id="c2685-535">This matches exactly one segment of the domain; if you need to match `a.b.example.com` then use `*.*.example.com`.</span></span> <span data-ttu-id="c2685-536">Wenn Ihre Registerkartenkonfiguration oder Inhalts-UI zu einer anderen Domäne als der für die Registerkartenkonfiguration verwendeten navigieren muss, muss diese Domäne hier angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="c2685-536">If your tab configuration or content UI needs to navigate to any other domain besides the one use for tab configuration, that domain must be specified here.</span></span>

<span data-ttu-id="c2685-537">Es ist **nicht** erforderlich, die Domänen von Identitätsanbietern, die Sie in Ihrer App unterstützen möchten, einzuschließen.</span><span class="sxs-lookup"><span data-stu-id="c2685-537">It is **not** necessary to include the domains of identity providers you want to support in your app.</span></span> <span data-ttu-id="c2685-538">Um sich beispielsweise mit einer Google-ID zu authentifizieren, ist es erforderlich, zu accounts.google.com umzuleiten. Sie dürfen jedoch keine accounts.google.com in `validDomains[]` einschließen.</span><span class="sxs-lookup"><span data-stu-id="c2685-538">For example, to authenticate using a Google ID, it is required to redirect to accounts.google.com, however, you must not include accounts.google.com in `validDomains[]`.</span></span>

<span data-ttu-id="c2685-539">Teams Apps, für die ihre eigenen SharePoint-URLs ordnungsgemäß funktionieren müssen, enthält "{teamsitedomain}" in ihrer gültigen Domänenliste.</span><span class="sxs-lookup"><span data-stu-id="c2685-539">Teams apps that require their own sharepoint URLs to function well, includes "{teamsitedomain}" in their valid domain list.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c2685-540">Fügen Sie keine Domänen hinzu, die sich außerhalb Ihres Steuerelements befinden, entweder direkt oder über Platzhalter.</span><span class="sxs-lookup"><span data-stu-id="c2685-540">Do not add domains that are outside your control, either directly or through wildcards.</span></span> <span data-ttu-id="c2685-541">Ist z. `yourapp.onmicrosoft.com` B. gültig, ist jedoch `*.onmicrosoft.com` ungültig.</span><span class="sxs-lookup"><span data-stu-id="c2685-541">For example, `yourapp.onmicrosoft.com` is valid, however, `*.onmicrosoft.com` is not valid.</span></span>

<span data-ttu-id="c2685-542">Das Objekt ist ein Array mit allen Elementen des Typs `string` .</span><span class="sxs-lookup"><span data-stu-id="c2685-542">The object is an array with all elements of the type `string`.</span></span>

## <a name="webapplicationinfo"></a><span data-ttu-id="c2685-543">webApplicationInfo</span><span class="sxs-lookup"><span data-stu-id="c2685-543">webApplicationInfo</span></span>

<span data-ttu-id="c2685-544">**Optional** - Objekt</span><span class="sxs-lookup"><span data-stu-id="c2685-544">**Optional** — object</span></span>

<span data-ttu-id="c2685-545">Geben Sie Ihre Azure Active Directory (AAD)-App-ID und Microsoft Graph Informationen an, um Benutzern zu helfen, sich nahtlos bei Ihrer App anzumelden.</span><span class="sxs-lookup"><span data-stu-id="c2685-545">Provide your Azure Active Directory (AAD) App ID and Microsoft Graph information to help users seamlessly sign into your app.</span></span> <span data-ttu-id="c2685-546">Wenn Ihre App in AAD registriert ist, müssen Sie die App-ID angeben, damit Administratoren berechtigungen einfach überprüfen und ihre Zustimmung im Teams Admin Center erteilen können.</span><span class="sxs-lookup"><span data-stu-id="c2685-546">If your app is registered in AAD, you must provide the App ID, so that administrators can easily review permissions and grant consent in Teams admin center.</span></span>

|<span data-ttu-id="c2685-547">Name</span><span class="sxs-lookup"><span data-stu-id="c2685-547">Name</span></span>| <span data-ttu-id="c2685-548">Typ</span><span class="sxs-lookup"><span data-stu-id="c2685-548">Type</span></span>| <span data-ttu-id="c2685-549">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="c2685-549">Maximum size</span></span> | <span data-ttu-id="c2685-550">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="c2685-550">Required</span></span> | <span data-ttu-id="c2685-551">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="c2685-551">Description</span></span>|
|---|---|---|---|---|
|`id`|<span data-ttu-id="c2685-552">string</span><span class="sxs-lookup"><span data-stu-id="c2685-552">string</span></span>|<span data-ttu-id="c2685-553">36 Zeichen</span><span class="sxs-lookup"><span data-stu-id="c2685-553">36 characters</span></span>|<span data-ttu-id="c2685-554">✔</span><span class="sxs-lookup"><span data-stu-id="c2685-554">✔</span></span>|<span data-ttu-id="c2685-555">AAD-Anwendungs-ID der App.</span><span class="sxs-lookup"><span data-stu-id="c2685-555">AAD application id of the app.</span></span> <span data-ttu-id="c2685-556">Diese ID muss eine GUID sein.</span><span class="sxs-lookup"><span data-stu-id="c2685-556">This id must be a GUID.</span></span>|
|`resource`|<span data-ttu-id="c2685-557">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="c2685-557">string</span></span>|<span data-ttu-id="c2685-558">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="c2685-558">2048 characters</span></span>|<span data-ttu-id="c2685-559">✔</span><span class="sxs-lookup"><span data-stu-id="c2685-559">✔</span></span>|<span data-ttu-id="c2685-560">Ressourcen-URL der App zum Abrufen des Authentifizierungstokens für SSO.</span><span class="sxs-lookup"><span data-stu-id="c2685-560">Resource URL of app for acquiring auth token for SSO.</span></span> </br> <span data-ttu-id="c2685-561">**HINWEIS:** Wenn Sie SSO nicht verwenden, stellen Sie sicher, dass Sie einen Pseudozeichenfolgenwert in dieses Feld in Ihr App-Manifest eingeben, um beispielsweise https://notapplicable eine Fehlerantwort zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="c2685-561">**NOTE:** If you are not using SSO, ensure that you enter a dummy string value in this field to your app manifest, for example, https://notapplicable to avoid an error response.</span></span> |
|`applicationPermissions`|<span data-ttu-id="c2685-562">array of strings</span><span class="sxs-lookup"><span data-stu-id="c2685-562">array of strings</span></span>|<span data-ttu-id="c2685-563">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="c2685-563">128 characters</span></span>||<span data-ttu-id="c2685-564">Geben Sie eine präzise [ressourcenspezifische Zustimmung an.](../../graph-api/rsc/resource-specific-consent.md#resource-specific-permissions)</span><span class="sxs-lookup"><span data-stu-id="c2685-564">Specify granular [resource specific consent](../../graph-api/rsc/resource-specific-consent.md#resource-specific-permissions).</span></span>|

## <a name="showloadingindicator"></a><span data-ttu-id="c2685-565">showLoadingIndicator</span><span class="sxs-lookup"><span data-stu-id="c2685-565">showLoadingIndicator</span></span>

<span data-ttu-id="c2685-566">**Optional** – boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="c2685-566">**Optional** — boolean</span></span>

<span data-ttu-id="c2685-567">Gibt an, ob die Ladeanzeige angezeigt werden soll, wenn eine App oder Registerkarte geladen wird.</span><span class="sxs-lookup"><span data-stu-id="c2685-567">Indicates whether or not to show the loading indicator when an app or tab is loading.</span></span> <span data-ttu-id="c2685-568">Der Standardwert ist **false**.</span><span class="sxs-lookup"><span data-stu-id="c2685-568">Default is **false**.</span></span>
>[!NOTE]
><span data-ttu-id="c2685-569">Wenn Sie `showLoadingIndicator` im App-Manifest "true" auswählen, ändern Sie zum ordnungsgemäßen Laden der Seite die Inhaltsseiten Ihrer Registerkarten und Aufgabenmodule, wie unter ["Anzeigen eines systemeigenen Ladeindikatordokuments"](../../tabs/how-to/create-tab-pages/content-page.md#show-a-native-loading-indicator) beschrieben.</span><span class="sxs-lookup"><span data-stu-id="c2685-569">If you select`showLoadingIndicator` as true in your app manifest, to load the page correctly, modify the content pages of your tabs and task modules as described in [Show a native loading indicator](../../tabs/how-to/create-tab-pages/content-page.md#show-a-native-loading-indicator) document.</span></span>


## <a name="isfullscreen"></a><span data-ttu-id="c2685-570">isFullScreen</span><span class="sxs-lookup"><span data-stu-id="c2685-570">isFullScreen</span></span>

 <span data-ttu-id="c2685-571">**Optional** – boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="c2685-571">**Optional** — boolean</span></span>

<span data-ttu-id="c2685-572">Gibt an, wo eine persönliche App mit oder ohne Registerkartenkopfleiste gerendert wird.</span><span class="sxs-lookup"><span data-stu-id="c2685-572">Indicate where a personal app is rendered with or without a tab header bar.</span></span> <span data-ttu-id="c2685-573">Der Standardwert ist **false**.</span><span class="sxs-lookup"><span data-stu-id="c2685-573">Default is **false**.</span></span>

## <a name="activities"></a><span data-ttu-id="c2685-574">Aktivitäten</span><span class="sxs-lookup"><span data-stu-id="c2685-574">activities</span></span>

<span data-ttu-id="c2685-575">**Optional** - Objekt</span><span class="sxs-lookup"><span data-stu-id="c2685-575">**Optional** — object</span></span>

<span data-ttu-id="c2685-576">Definieren Sie die Eigenschaften, die Ihre App zum Posten eines Benutzeraktivitätsfeeds verwendet.</span><span class="sxs-lookup"><span data-stu-id="c2685-576">Define the properties your app uses to post a user activity feed.</span></span>

|<span data-ttu-id="c2685-577">Name</span><span class="sxs-lookup"><span data-stu-id="c2685-577">Name</span></span>| <span data-ttu-id="c2685-578">Typ</span><span class="sxs-lookup"><span data-stu-id="c2685-578">Type</span></span>| <span data-ttu-id="c2685-579">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="c2685-579">Maximum size</span></span> | <span data-ttu-id="c2685-580">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="c2685-580">Required</span></span> | <span data-ttu-id="c2685-581">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="c2685-581">Description</span></span>|
|---|---|---|---|---|
|`activityTypes`|<span data-ttu-id="c2685-582">Array von Objekten</span><span class="sxs-lookup"><span data-stu-id="c2685-582">array of Objects</span></span>|<span data-ttu-id="c2685-583">128 Elemente</span><span class="sxs-lookup"><span data-stu-id="c2685-583">128 items</span></span>| | <span data-ttu-id="c2685-584">Stellen Sie die Arten von Aktivitäten bereit, die Ihre App in einem Benutzeraktivitätsfeed veröffentlichen kann.</span><span class="sxs-lookup"><span data-stu-id="c2685-584">Provide the types of activities that your app can post to a users activity feed.</span></span>|

### <a name="activitiesactivitytypes"></a><span data-ttu-id="c2685-585">activities.activityTypes</span><span class="sxs-lookup"><span data-stu-id="c2685-585">activities.activityTypes</span></span>

|<span data-ttu-id="c2685-586">Name</span><span class="sxs-lookup"><span data-stu-id="c2685-586">Name</span></span>| <span data-ttu-id="c2685-587">Typ</span><span class="sxs-lookup"><span data-stu-id="c2685-587">Type</span></span>| <span data-ttu-id="c2685-588">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="c2685-588">Maximum size</span></span> | <span data-ttu-id="c2685-589">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="c2685-589">Required</span></span> | <span data-ttu-id="c2685-590">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="c2685-590">Description</span></span>|
|---|---|---|---|---|
|`type`|<span data-ttu-id="c2685-591">string</span><span class="sxs-lookup"><span data-stu-id="c2685-591">string</span></span>|<span data-ttu-id="c2685-592">32 Zeichen</span><span class="sxs-lookup"><span data-stu-id="c2685-592">32 characters</span></span>|<span data-ttu-id="c2685-593">✔</span><span class="sxs-lookup"><span data-stu-id="c2685-593">✔</span></span>|<span data-ttu-id="c2685-594">Der Benachrichtigungstyp.</span><span class="sxs-lookup"><span data-stu-id="c2685-594">The notification type.</span></span> <span data-ttu-id="c2685-595">*Siehe unten*.</span><span class="sxs-lookup"><span data-stu-id="c2685-595">*See below*.</span></span>|
|`description`|<span data-ttu-id="c2685-596">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="c2685-596">string</span></span>|<span data-ttu-id="c2685-597">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="c2685-597">128 characters</span></span>|<span data-ttu-id="c2685-598">✔</span><span class="sxs-lookup"><span data-stu-id="c2685-598">✔</span></span>|<span data-ttu-id="c2685-599">Eine kurze Beschreibung der Benachrichtigung.</span><span class="sxs-lookup"><span data-stu-id="c2685-599">A brief description of the notification.</span></span> <span data-ttu-id="c2685-600">*Siehe unten*.</span><span class="sxs-lookup"><span data-stu-id="c2685-600">*See below*.</span></span>|
|`templateText`|<span data-ttu-id="c2685-601">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="c2685-601">string</span></span>|<span data-ttu-id="c2685-602">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="c2685-602">128 characters</span></span>|<span data-ttu-id="c2685-603">✔</span><span class="sxs-lookup"><span data-stu-id="c2685-603">✔</span></span>|<span data-ttu-id="c2685-604">Beispiel: "{actor} erstellt Aufgabe {taskId} für Sie"</span><span class="sxs-lookup"><span data-stu-id="c2685-604">Ex: "{actor} created task {taskId} for you"</span></span>|

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

## <a name="defaultinstallscope"></a><span data-ttu-id="c2685-605">defaultInstallScope</span><span class="sxs-lookup"><span data-stu-id="c2685-605">defaultInstallScope</span></span>

<span data-ttu-id="c2685-606">**Optional** – Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="c2685-606">**Optional** - string</span></span>

<span data-ttu-id="c2685-607">Gibt den standardmäßig für diese App definierten Installationsumfang an.</span><span class="sxs-lookup"><span data-stu-id="c2685-607">Specifies the install scope defined for this app by default.</span></span> <span data-ttu-id="c2685-608">Der definierte Bereich ist die Option, die auf der Schaltfläche angezeigt wird, wenn ein Benutzer versucht, die App hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="c2685-608">The defined scope will be the option displayed on the button when a user tries to add the app.</span></span> <span data-ttu-id="c2685-609">Mögliche Optionen sind:</span><span class="sxs-lookup"><span data-stu-id="c2685-609">Options are:</span></span>
* `personal`
* `team`
* `groupchat`
* `meetings`

## <a name="defaultgroupcapability"></a><span data-ttu-id="c2685-610">defaultGroupCapability</span><span class="sxs-lookup"><span data-stu-id="c2685-610">defaultGroupCapability</span></span>

<span data-ttu-id="c2685-611">**Optional** – Objekt</span><span class="sxs-lookup"><span data-stu-id="c2685-611">**Optional** - object</span></span>

<span data-ttu-id="c2685-612">Wenn ein Gruppeninstallationsbereich ausgewählt ist, wird die Standardfunktion definiert, wenn der Benutzer die App installiert.</span><span class="sxs-lookup"><span data-stu-id="c2685-612">When a group install scope is selected, it will define the default capability when the user installs the app.</span></span> <span data-ttu-id="c2685-613">Mögliche Optionen sind:</span><span class="sxs-lookup"><span data-stu-id="c2685-613">Options are:</span></span>
* `team`
* `groupchat`
* `meetings`
 
|<span data-ttu-id="c2685-614">Name</span><span class="sxs-lookup"><span data-stu-id="c2685-614">Name</span></span>| <span data-ttu-id="c2685-615">Typ</span><span class="sxs-lookup"><span data-stu-id="c2685-615">Type</span></span>| <span data-ttu-id="c2685-616">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="c2685-616">Maximum size</span></span> | <span data-ttu-id="c2685-617">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="c2685-617">Required</span></span> | <span data-ttu-id="c2685-618">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="c2685-618">Description</span></span>|
|---|---|---|---|---|
|`team`|<span data-ttu-id="c2685-619">string</span><span class="sxs-lookup"><span data-stu-id="c2685-619">string</span></span>|||<span data-ttu-id="c2685-620">Wenn der ausgewählte Installationsbereich ausgewählt `team` ist, gibt dieses Feld die verfügbare Standardfunktion an.</span><span class="sxs-lookup"><span data-stu-id="c2685-620">When the install scope selected is `team`, this field specifies the default capability available.</span></span> <span data-ttu-id="c2685-621">Optionen: `tab` `bot` oder `connector` .</span><span class="sxs-lookup"><span data-stu-id="c2685-621">Options: `tab`, `bot`, or `connector`.</span></span>|
|`groupchat`|<span data-ttu-id="c2685-622">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="c2685-622">string</span></span>|||<span data-ttu-id="c2685-623">Wenn der ausgewählte Installationsbereich ausgewählt `groupchat` ist, gibt dieses Feld die verfügbare Standardfunktion an.</span><span class="sxs-lookup"><span data-stu-id="c2685-623">When the install scope selected is `groupchat`, this field specifies the default capability available.</span></span> <span data-ttu-id="c2685-624">Optionen: `tab` `bot` oder `connector` .</span><span class="sxs-lookup"><span data-stu-id="c2685-624">Options: `tab`, `bot`, or `connector`.</span></span>|
|`meetings`|<span data-ttu-id="c2685-625">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="c2685-625">string</span></span>|||<span data-ttu-id="c2685-626">Wenn der ausgewählte Installationsbereich ausgewählt `meetings` ist, gibt dieses Feld die verfügbare Standardfunktion an.</span><span class="sxs-lookup"><span data-stu-id="c2685-626">When the install scope selected is `meetings`, this field specifies the default capability available.</span></span> <span data-ttu-id="c2685-627">Optionen: `tab` `bot` oder `connector` .</span><span class="sxs-lookup"><span data-stu-id="c2685-627">Options: `tab`, `bot`, or `connector`.</span></span>|

## <a name="configurableproperties"></a><span data-ttu-id="c2685-628">configurableProperties</span><span class="sxs-lookup"><span data-stu-id="c2685-628">configurableProperties</span></span>

<span data-ttu-id="c2685-629">**Optional** – Array</span><span class="sxs-lookup"><span data-stu-id="c2685-629">**Optional** - array</span></span>

<span data-ttu-id="c2685-630">Der `configurableProperties` Block definiert die App-Eigenschaften, die Teams Administratoren anpassen können.</span><span class="sxs-lookup"><span data-stu-id="c2685-630">The `configurableProperties` block defines the app properties that Teams admins can customize.</span></span> <span data-ttu-id="c2685-631">Weitere Informationen finden Sie unter Aktivieren der [App-Anpassung.](~/concepts/design/enable-app-customization.md)</span><span class="sxs-lookup"><span data-stu-id="c2685-631">For more information, see [enable app customization](~/concepts/design/enable-app-customization.md).</span></span>

> [!NOTE]
> <span data-ttu-id="c2685-632">Es muss mindestens eine Eigenschaft definiert werden.</span><span class="sxs-lookup"><span data-stu-id="c2685-632">A minimum of one property must be defined.</span></span> <span data-ttu-id="c2685-633">Sie können maximal neun Eigenschaften in diesem Block definieren.</span><span class="sxs-lookup"><span data-stu-id="c2685-633">You can define a maximum of nine properties in this block.</span></span>

<span data-ttu-id="c2685-634">Sie können eine der folgenden Eigenschaften definieren:</span><span class="sxs-lookup"><span data-stu-id="c2685-634">You can define any of the following properties:</span></span>

* <span data-ttu-id="c2685-635">`name`: Der Anzeigename der App.</span><span class="sxs-lookup"><span data-stu-id="c2685-635">`name`: The app's display name.</span></span>
* <span data-ttu-id="c2685-636">`shortDescription`: Die kurze Beschreibung der App.</span><span class="sxs-lookup"><span data-stu-id="c2685-636">`shortDescription`: The app's short description.</span></span>
* <span data-ttu-id="c2685-637">`longDescription`: Die ausführliche Beschreibung der App.</span><span class="sxs-lookup"><span data-stu-id="c2685-637">`longDescription`: The app's detailed description.</span></span>
* <span data-ttu-id="c2685-638">`smallImageUrl`: Das Gliederungssymbol der App.</span><span class="sxs-lookup"><span data-stu-id="c2685-638">`smallImageUrl`: The app's outline icon.</span></span>
* <span data-ttu-id="c2685-639">`largeImageUrl`: Das Farbsymbol der App.</span><span class="sxs-lookup"><span data-stu-id="c2685-639">`largeImageUrl`: The app's color icon.</span></span>
* <span data-ttu-id="c2685-640">`accentColor`: Die Farbe, die in Verbindung mit und als Hintergrund für Ihre Gliederungssymbole verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="c2685-640">`accentColor`: The color to use in conjunction with and as a background for your outline icons.</span></span>
* <span data-ttu-id="c2685-641">`developerUrl`: Die HTTPS-URL der Website des Entwicklers.</span><span class="sxs-lookup"><span data-stu-id="c2685-641">`developerUrl`: The HTTPS URL of the developer's website.</span></span>
* <span data-ttu-id="c2685-642">`privacyUrl`: Die HTTPS-URL der Datenschutzrichtlinie des Entwicklers.</span><span class="sxs-lookup"><span data-stu-id="c2685-642">`privacyUrl`: The HTTPS URL of the developer's privacy policy.</span></span>
* <span data-ttu-id="c2685-643">`termsOfUseUrl`: Die HTTPS-URL der Nutzungsbedingungen des Entwicklers.</span><span class="sxs-lookup"><span data-stu-id="c2685-643">`termsOfUseUrl`: The HTTPS URL of the developer's terms of use.</span></span>
