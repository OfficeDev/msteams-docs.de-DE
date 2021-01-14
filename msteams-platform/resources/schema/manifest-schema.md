---
title: Manifestschemareferenz
description: Beschreibt das Manifestschema für Microsoft Teams
keywords: Teams-Manifestschema
author: laujan
ms.author: lajanuar
ms.openlocfilehash: cf80251abd22f0c89388cbe5a6287a02dedce1fb
ms.sourcegitcommit: bf61ae5ad2afa4efdb0311158184d0cbb9c40174
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/13/2021
ms.locfileid: "49845630"
---
# <a name="reference-manifest-schema-for-microsoft-teams"></a><span data-ttu-id="9e9f2-104">Referenz: Manifestschema für Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="9e9f2-104">Reference: Manifest schema for Microsoft Teams</span></span>

<span data-ttu-id="9e9f2-105">Das Microsoft Teams-Manifest beschreibt, wie die App in das Microsoft Teams-Produkt integriert wird.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-105">The Microsoft Teams manifest describes how the app integrates into the Microsoft Teams product.</span></span> <span data-ttu-id="9e9f2-106">Ihr Manifest muss dem Schema entsprechen, das unter [`https://developer.microsoft.com/json-schemas/teams/v1.8/MicrosoftTeams.schema.json`]( https://developer.microsoft.com/json-schemas/teams/v1.8/MicrosoftTeams.schema.json) gehostet wird.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-106">Your manifest must conform to the schema hosted at [`https://developer.microsoft.com/json-schemas/teams/v1.8/MicrosoftTeams.schema.json`]( https://developer.microsoft.com/json-schemas/teams/v1.8/MicrosoftTeams.schema.json).</span></span> <span data-ttu-id="9e9f2-107">Frühere Versionen 1.0-1.4 werden ebenfalls unterstützt (unter Verwendung von "v1.x" in der URL).</span><span class="sxs-lookup"><span data-stu-id="9e9f2-107">Previous versions 1.0-1.4 are also supported (using "v1.x" in the URL).</span></span>

<span data-ttu-id="9e9f2-108">Das folgende Schemabeispiel zeigt alle Erweiterungsoptionen.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-108">The following schema sample shows all extensibility options.</span></span>

## <a name="sample-full-manifest"></a><span data-ttu-id="9e9f2-109">Beispiel für vollständiges Manifest</span><span class="sxs-lookup"><span data-stu-id="9e9f2-109">Sample full manifest</span></span>

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

<span data-ttu-id="9e9f2-110">Das Schema definiert die folgenden Eigenschaften:</span><span class="sxs-lookup"><span data-stu-id="9e9f2-110">The schema defines the following properties:</span></span>

## <a name="schema"></a><span data-ttu-id="9e9f2-111">$schema</span><span class="sxs-lookup"><span data-stu-id="9e9f2-111">$schema</span></span>

<span data-ttu-id="9e9f2-112">*Optional, aber empfohlen –* Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="9e9f2-112">*Optional, but recommended* — string</span></span>

<span data-ttu-id="9e9f2-113">Die https:// URL, die auf das JSON-Schema für das Manifest verweist.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-113">The https:// URL referencing the JSON Schema for the manifest.</span></span>

## <a name="manifestversion"></a><span data-ttu-id="9e9f2-114">manifestVersion</span><span class="sxs-lookup"><span data-stu-id="9e9f2-114">manifestVersion</span></span>

<span data-ttu-id="9e9f2-115">**Erforderlich** – Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="9e9f2-115">**Required** — string</span></span>

<span data-ttu-id="9e9f2-116">Die Version des Manifestschemas, das dieses Manifest verwendet.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-116">The version of the manifest schema this manifest is using.</span></span> <span data-ttu-id="9e9f2-117">Er sollte "1.7" sein.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-117">It should be "1.7".</span></span>

## <a name="version"></a><span data-ttu-id="9e9f2-118">Version</span><span class="sxs-lookup"><span data-stu-id="9e9f2-118">version</span></span>

<span data-ttu-id="9e9f2-119">**Erforderlich** – Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="9e9f2-119">**Required** — string</span></span>

<span data-ttu-id="9e9f2-120">Die Version der bestimmten App.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-120">The version of the specific app.</span></span> <span data-ttu-id="9e9f2-121">Wenn Sie etwas in Ihrem Manifest aktualisieren, muss auch die Version erhöht werden.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-121">If you update something in your manifest, the version must be incremented as well.</span></span> <span data-ttu-id="9e9f2-122">Auf diese Weise wird bei der Installation des neuen Manifests das vorhandene überschrieben, und der Benutzer erhält die neue Funktionalität.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-122">This way, when the new manifest is installed, it will overwrite the existing one and the user will get the new functionality.</span></span> <span data-ttu-id="9e9f2-123">Wenn diese App an den Store übermittelt wurde, muss das neue Manifest erneut übermittelt und überprüft werden.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-123">If this app was submitted to the store, the new manifest will have to be re-submitted and re-validated.</span></span> <span data-ttu-id="9e9f2-124">Anschließend erhalten Benutzer dieser App das neue aktualisierte Manifest automatisch in ein paar Stunden, nachdem sie genehmigt wurde.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-124">Then, users of this app will get the new updated manifest automatically in a few hours, after it is approved.</span></span>

<span data-ttu-id="9e9f2-125">Wenn sich die von der App angeforderten Berechtigungen ändern, werden die Benutzer aufgefordert, ein Upgrade zu starten und der App erneut zu zustimmen.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-125">If the app requested permissions change, users will be prompted to upgrade and re-consent to the app.</span></span>

<span data-ttu-id="9e9f2-126">Diese Versionszeichenfolge muss dem [Semverstandard](http://semver.org/) (MAJOR. MINOR. PATCH).</span><span class="sxs-lookup"><span data-stu-id="9e9f2-126">This version string must follow the [semver](http://semver.org/) standard (MAJOR.MINOR.PATCH).</span></span>

## <a name="id"></a><span data-ttu-id="9e9f2-127">id</span><span class="sxs-lookup"><span data-stu-id="9e9f2-127">id</span></span>

<span data-ttu-id="9e9f2-128">**Erforderlich** – Microsoft-App-ID</span><span class="sxs-lookup"><span data-stu-id="9e9f2-128">**Required** — Microsoft app ID</span></span>

<span data-ttu-id="9e9f2-129">Der eindeutige von Microsoft generierte Bezeichner für diese App.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-129">The unique Microsoft-generated identifier for this app.</span></span> <span data-ttu-id="9e9f2-130">Wenn Sie einen Bot über das Microsoft Bot Framework registriert haben oder sich die Web-App Ihrer Registerkarte bereits bei Microsoft angemeldet hat, sollten Sie bereits über eine ID verfügen und sie hier eingeben.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-130">If you have registered a bot via the Microsoft Bot Framework, or your tab's web app already signs in with Microsoft, you should already have an ID and should enter it here.</span></span> <span data-ttu-id="9e9f2-131">Andernfalls sollten Sie eine neue ID im Microsoft-Anwendungsregistrierungsportal[(](https://apps.dev.microsoft.com)Meine Anwendungen) generieren, sie hier eingeben und dann wiederverwenden, wenn Sie einen Bot hinzufügen. Hinweis: Wenn Sie ein Update für Ihre vorhandene App in AppSource übermitteln, darf die ID in Ihrem Manifest nicht geändert werden.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-131">Otherwise, you should generate a new ID at the Microsoft Application Registration Portal ([My Applications](https://apps.dev.microsoft.com)), enter it here, and then reuse it when you add a bot.Note: If you are submitting an update to your existing app in AppSource, the ID in your manifest must not be modified.</span></span>

## <a name="developer"></a><span data-ttu-id="9e9f2-132">developer</span><span class="sxs-lookup"><span data-stu-id="9e9f2-132">developer</span></span>

<span data-ttu-id="9e9f2-133">**Erforderlich** – Objekt</span><span class="sxs-lookup"><span data-stu-id="9e9f2-133">**Required** — object</span></span>

<span data-ttu-id="9e9f2-134">Gibt Informationen zu Ihrem Unternehmen an.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-134">Specifies information about your company.</span></span> <span data-ttu-id="9e9f2-135">Bei an AppSource (früher Office Store) übermittelten Apps müssen diese Werte mit den Informationen in Ihrem Eintrag "AppSource" übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-135">For apps submitted to AppSource (formerly Office Store), these values must match the information in your AppSource entry.</span></span> <span data-ttu-id="9e9f2-136">Weitere Informationen [finden Sie in unseren Veröffentlichungsrichtlinien.](~/concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md)</span><span class="sxs-lookup"><span data-stu-id="9e9f2-136">See our [publishing guidelines](~/concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md) for additional information.</span></span>

|<span data-ttu-id="9e9f2-137">Name</span><span class="sxs-lookup"><span data-stu-id="9e9f2-137">Name</span></span>| <span data-ttu-id="9e9f2-138">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="9e9f2-138">Maximum size</span></span> | <span data-ttu-id="9e9f2-139">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="9e9f2-139">Required</span></span> | <span data-ttu-id="9e9f2-140">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="9e9f2-140">Description</span></span>|
|---|---|---|---|
|`name`|<span data-ttu-id="9e9f2-141">32 Zeichen</span><span class="sxs-lookup"><span data-stu-id="9e9f2-141">32 characters</span></span>|<span data-ttu-id="9e9f2-142">✔</span><span class="sxs-lookup"><span data-stu-id="9e9f2-142">✔</span></span>|<span data-ttu-id="9e9f2-143">Der Anzeigename für den Entwickler.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-143">The display name for the developer.</span></span>|
|`websiteUrl`|<span data-ttu-id="9e9f2-144">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="9e9f2-144">2048 characters</span></span>|<span data-ttu-id="9e9f2-145">✔</span><span class="sxs-lookup"><span data-stu-id="9e9f2-145">✔</span></span>|<span data-ttu-id="9e9f2-146">Die https:// URL zur Website des Entwicklers.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-146">The https:// URL to the developer's website.</span></span> <span data-ttu-id="9e9f2-147">Über diesen Link sollten Benutzer zu Ihrem Unternehmen oder zu ihrer produktspezifischen Angebotsseite gelangen.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-147">This link should take users to your company or product-specific landing page.</span></span>|
|`privacyUrl`|<span data-ttu-id="9e9f2-148">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="9e9f2-148">2048 characters</span></span>|<span data-ttu-id="9e9f2-149">✔</span><span class="sxs-lookup"><span data-stu-id="9e9f2-149">✔</span></span>|<span data-ttu-id="9e9f2-150">Die https:// URL zur Datenschutzrichtlinie des Entwicklers.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-150">The https:// URL to the developer's privacy policy.</span></span>|
|`termsOfUseUrl`|<span data-ttu-id="9e9f2-151">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="9e9f2-151">2048 characters</span></span>|<span data-ttu-id="9e9f2-152">✔</span><span class="sxs-lookup"><span data-stu-id="9e9f2-152">✔</span></span>|<span data-ttu-id="9e9f2-153">Die https:// URL zu den Nutzungsbedingungen des Entwicklers.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-153">The https:// URL to the developer's terms of use.</span></span>|
|`mpnId`|<span data-ttu-id="9e9f2-154">10 Zeichen</span><span class="sxs-lookup"><span data-stu-id="9e9f2-154">10 characters</span></span>| |<span data-ttu-id="9e9f2-155">**Optional** Die Microsoft Partner Network-ID, die die Partnerorganisation identifiziert, die die App erstellt.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-155">**Optional** The Microsoft Partner Network ID that identifies the partner organization building the app.</span></span>|

## <a name="name"></a><span data-ttu-id="9e9f2-156">name</span><span class="sxs-lookup"><span data-stu-id="9e9f2-156">name</span></span>

<span data-ttu-id="9e9f2-157">**Erforderlich** – Objekt</span><span class="sxs-lookup"><span data-stu-id="9e9f2-157">**Required** — object</span></span>

<span data-ttu-id="9e9f2-158">Der Name Ihrer App-Erfahrung, der Benutzern in der Teams-Erfahrung angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-158">The name of your app experience, displayed to users in the Teams experience.</span></span> <span data-ttu-id="9e9f2-159">Bei an AppSource übermittelten Apps müssen diese Werte mit den Informationen in Ihrem Eintrag "AppSource" übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-159">For apps submitted to AppSource, these values must match the information in your AppSource entry.</span></span> <span data-ttu-id="9e9f2-160">Die Werte von `short` und sollten nicht identisch `full` sein.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-160">The values of `short` and `full` should not be the same.</span></span>

|<span data-ttu-id="9e9f2-161">Name</span><span class="sxs-lookup"><span data-stu-id="9e9f2-161">Name</span></span>| <span data-ttu-id="9e9f2-162">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="9e9f2-162">Maximum size</span></span> | <span data-ttu-id="9e9f2-163">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="9e9f2-163">Required</span></span> | <span data-ttu-id="9e9f2-164">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="9e9f2-164">Description</span></span>|
|---|---|---|---|
|`short`|<span data-ttu-id="9e9f2-165">30 Zeichen</span><span class="sxs-lookup"><span data-stu-id="9e9f2-165">30 characters</span></span>|<span data-ttu-id="9e9f2-166">✔</span><span class="sxs-lookup"><span data-stu-id="9e9f2-166">✔</span></span>|<span data-ttu-id="9e9f2-167">Der kurze Anzeigename für die App.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-167">The short display name for the app.</span></span>|
|`full`|<span data-ttu-id="9e9f2-168">100 Zeichen</span><span class="sxs-lookup"><span data-stu-id="9e9f2-168">100 characters</span></span>||<span data-ttu-id="9e9f2-169">Der vollständige Name der App, der verwendet wird, wenn der vollständige Name der App 30 Zeichen überschreitet.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-169">The full name of the app, used if the full app name exceeds 30 characters.</span></span>|

## <a name="description"></a><span data-ttu-id="9e9f2-170">description</span><span class="sxs-lookup"><span data-stu-id="9e9f2-170">description</span></span>

<span data-ttu-id="9e9f2-171">**Erforderlich** – Objekt</span><span class="sxs-lookup"><span data-stu-id="9e9f2-171">**Required** — object</span></span>

<span data-ttu-id="9e9f2-172">Beschreibt Ihre App für Benutzer.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-172">Describes your app to users.</span></span> <span data-ttu-id="9e9f2-173">Bei an AppSource übermittelten Apps müssen diese Werte mit den Informationen in Ihrem Eintrag "AppSource" übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-173">For apps submitted to AppSource, these values must match the information in your AppSource entry.</span></span>

<span data-ttu-id="9e9f2-174">Stellen Sie sicher, dass Ihre Beschreibung Ihre Erfahrung genau beschreibt, und stellen Sie Informationen zur Verfügung, mit deren Hilfe potenzielle Kunden ihre Erfahrung besser verstehen können.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-174">Ensure that your description accurately describes your experience and provides information to help potential customers understand what your experience does.</span></span> <span data-ttu-id="9e9f2-175">Beachten Sie auch in der vollständigen Beschreibung, ob ein externes Konto für die Verwendung erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-175">You should also note, in the full description, if an external account is required for use.</span></span> <span data-ttu-id="9e9f2-176">Die Werte von `short` und sollten nicht identisch `full` sein.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-176">The values of `short` and `full` should not be the same.</span></span>  <span data-ttu-id="9e9f2-177">Ihre kurze Beschreibung darf nicht innerhalb der langen Beschreibung wiederholt werden und darf keinen anderen App-Namen enthalten.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-177">Your short description must not be repeated within the long description and must not include any other app name.</span></span>

|<span data-ttu-id="9e9f2-178">Name</span><span class="sxs-lookup"><span data-stu-id="9e9f2-178">Name</span></span>| <span data-ttu-id="9e9f2-179">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="9e9f2-179">Maximum size</span></span> | <span data-ttu-id="9e9f2-180">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="9e9f2-180">Required</span></span> | <span data-ttu-id="9e9f2-181">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="9e9f2-181">Description</span></span>|
|---|---|---|---|
|`short`|<span data-ttu-id="9e9f2-182">80 Zeichen</span><span class="sxs-lookup"><span data-stu-id="9e9f2-182">80 characters</span></span>|<span data-ttu-id="9e9f2-183">✔</span><span class="sxs-lookup"><span data-stu-id="9e9f2-183">✔</span></span>|<span data-ttu-id="9e9f2-184">Eine kurze Beschreibung Ihrer App-Erfahrung, die bei begrenztem Platz verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-184">A short description of your app experience, used when space is limited.</span></span>|
|`full`|<span data-ttu-id="9e9f2-185">4000 Zeichen</span><span class="sxs-lookup"><span data-stu-id="9e9f2-185">4000 characters</span></span>|<span data-ttu-id="9e9f2-186">✔</span><span class="sxs-lookup"><span data-stu-id="9e9f2-186">✔</span></span>|<span data-ttu-id="9e9f2-187">Die vollständige Beschreibung Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-187">The full description of your app.</span></span>|

## <a name="packagename"></a><span data-ttu-id="9e9f2-188">packageName</span><span class="sxs-lookup"><span data-stu-id="9e9f2-188">packageName</span></span>

<span data-ttu-id="9e9f2-189">**Optional** – Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="9e9f2-189">**Optional** — string</span></span>

<span data-ttu-id="9e9f2-190">Ein eindeutiger Bezeichner für diese App in umgekehrter Domänen-Notation; Beispiel: com.example.myapp.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-190">A unique identifier for this app in reverse domain notation; for example, com.example.myapp.</span></span> <span data-ttu-id="9e9f2-191">Maximale Länge: 64 Zeichen.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-191">Maximum length: 64 characters.</span></span>

## <a name="localizationinfo"></a><span data-ttu-id="9e9f2-192">localizationInfo</span><span class="sxs-lookup"><span data-stu-id="9e9f2-192">localizationInfo</span></span>

<span data-ttu-id="9e9f2-193">**Optional** – Objekt</span><span class="sxs-lookup"><span data-stu-id="9e9f2-193">**Optional** — object</span></span>

<span data-ttu-id="9e9f2-194">Ermöglicht die Angabe einer Standardsprache sowie Zeiger auf zusätzliche Sprachdateien.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-194">Allows the specification of a default language, as well as pointers to additional language files.</span></span> <span data-ttu-id="9e9f2-195">Siehe [Lokalisierung](~/concepts/build-and-test/apps-localization.md).</span><span class="sxs-lookup"><span data-stu-id="9e9f2-195">See [localization](~/concepts/build-and-test/apps-localization.md).</span></span>

|<span data-ttu-id="9e9f2-196">Name</span><span class="sxs-lookup"><span data-stu-id="9e9f2-196">Name</span></span>| <span data-ttu-id="9e9f2-197">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="9e9f2-197">Maximum size</span></span> | <span data-ttu-id="9e9f2-198">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="9e9f2-198">Required</span></span> | <span data-ttu-id="9e9f2-199">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="9e9f2-199">Description</span></span>|
|---|---|---|---|
|`defaultLanguageTag`||<span data-ttu-id="9e9f2-200">✔</span><span class="sxs-lookup"><span data-stu-id="9e9f2-200">✔</span></span>|<span data-ttu-id="9e9f2-201">Das Sprachtag der Zeichenfolgen in dieser Manifestdatei auf oberster Ebene.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-201">The language tag of the strings in this top level manifest file.</span></span>|

### <a name="localizationinfoadditionallanguages"></a><span data-ttu-id="9e9f2-202">localizationInfo.additionalLanguages</span><span class="sxs-lookup"><span data-stu-id="9e9f2-202">localizationInfo.additionalLanguages</span></span>

<span data-ttu-id="9e9f2-203">Ein Array von Objekten, die zusätzliche Sprachübersetzungen angeben.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-203">An array of objects specifying additional language translations.</span></span>

|<span data-ttu-id="9e9f2-204">Name</span><span class="sxs-lookup"><span data-stu-id="9e9f2-204">Name</span></span>| <span data-ttu-id="9e9f2-205">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="9e9f2-205">Maximum size</span></span> | <span data-ttu-id="9e9f2-206">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="9e9f2-206">Required</span></span> | <span data-ttu-id="9e9f2-207">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="9e9f2-207">Description</span></span>|
|---|---|---|---|
|`languageTag`||<span data-ttu-id="9e9f2-208">✔</span><span class="sxs-lookup"><span data-stu-id="9e9f2-208">✔</span></span>|<span data-ttu-id="9e9f2-209">Das Sprachtag der Zeichenfolgen in der bereitgestellten Datei.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-209">The language tag of the strings in the provided file.</span></span>|
|`file`||<span data-ttu-id="9e9f2-210">✔</span><span class="sxs-lookup"><span data-stu-id="9e9f2-210">✔</span></span>|<span data-ttu-id="9e9f2-211">Ein relativer Dateipfad zu einer JSON-Datei, die die übersetzten Zeichenfolgen enthält.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-211">A relative file path to a the .json file containing the translated strings.</span></span>|

## <a name="icons"></a><span data-ttu-id="9e9f2-212">Symbole</span><span class="sxs-lookup"><span data-stu-id="9e9f2-212">icons</span></span>

<span data-ttu-id="9e9f2-213">**Erforderlich** – Objekt</span><span class="sxs-lookup"><span data-stu-id="9e9f2-213">**Required** — object</span></span>

<span data-ttu-id="9e9f2-214">Symbole, die in der Teams-App verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-214">Icons used within the Teams app.</span></span> <span data-ttu-id="9e9f2-215">Die Symboldateien müssen als Teil des Uploadpakets enthalten sein.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-215">The icon files must be included as part of the upload package.</span></span> <span data-ttu-id="9e9f2-216">Weitere [Informationen finden Sie](../../concepts/build-and-test/apps-package.md#app-icons) unter "Symbole".</span><span class="sxs-lookup"><span data-stu-id="9e9f2-216">See [Icons](../../concepts/build-and-test/apps-package.md#app-icons) for more information.</span></span>

|<span data-ttu-id="9e9f2-217">Name</span><span class="sxs-lookup"><span data-stu-id="9e9f2-217">Name</span></span>| <span data-ttu-id="9e9f2-218">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="9e9f2-218">Maximum size</span></span> | <span data-ttu-id="9e9f2-219">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="9e9f2-219">Required</span></span> | <span data-ttu-id="9e9f2-220">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="9e9f2-220">Description</span></span>|
|---|---|---|---|
|`outline`|<span data-ttu-id="9e9f2-221">32 x 32 Pixel</span><span class="sxs-lookup"><span data-stu-id="9e9f2-221">32 x 32 pixels</span></span>|<span data-ttu-id="9e9f2-222">✔</span><span class="sxs-lookup"><span data-stu-id="9e9f2-222">✔</span></span>|<span data-ttu-id="9e9f2-223">Ein relativer Dateipfad zu einem transparenten 32 x 32 PNG-Gliederungssymbol.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-223">A relative file path to a transparent 32x32 PNG outline icon.</span></span>|
|`color`|<span data-ttu-id="9e9f2-224">192 x 192 Pixel</span><span class="sxs-lookup"><span data-stu-id="9e9f2-224">192 x 192 pixels</span></span>|<span data-ttu-id="9e9f2-225">✔</span><span class="sxs-lookup"><span data-stu-id="9e9f2-225">✔</span></span>|<span data-ttu-id="9e9f2-226">Ein relativer Dateipfad zu einem vollfarbigen 192 x 192 PNG-Symbol.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-226">A relative file path to a full color 192x192 PNG icon.</span></span>|

## <a name="accentcolor"></a><span data-ttu-id="9e9f2-227">accentColor</span><span class="sxs-lookup"><span data-stu-id="9e9f2-227">accentColor</span></span>

<span data-ttu-id="9e9f2-228">**Optional** – HTML Hex-Farbcode</span><span class="sxs-lookup"><span data-stu-id="9e9f2-228">**Optional** — HTML Hex color code</span></span>

<span data-ttu-id="9e9f2-229">Eine Farbe, die in Verbindung mit und als Hintergrund für Ihre Gliederungssymbole verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-229">A color to use in conjunction with and as a background for your outline icons.</span></span>

<span data-ttu-id="9e9f2-230">Der Wert muss ein gültiger #A0 sein, der mit "#" beginnt, z. B. `#4464ee` .</span><span class="sxs-lookup"><span data-stu-id="9e9f2-230">The value must be a valid HTML color code starting with '#', for example `#4464ee`.</span></span>

## <a name="configurabletabs"></a><span data-ttu-id="9e9f2-231">configurableTabs</span><span class="sxs-lookup"><span data-stu-id="9e9f2-231">configurableTabs</span></span>

<span data-ttu-id="9e9f2-232">**Optional** – Array</span><span class="sxs-lookup"><span data-stu-id="9e9f2-232">**Optional** — array</span></span>

<span data-ttu-id="9e9f2-233">Wird verwendet, wenn Ihre App über eine Registerkartenerfahrung im Teamkanal verfügt, die eine zusätzliche Konfiguration erfordert, bevor sie hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-233">Used when your app experience has a team channel tab experience that requires extra configuration before it is added.</span></span> <span data-ttu-id="9e9f2-234">Konfigurierbare Registerkarten werden nur im Teambereich unterstützt (nicht persönlich), und derzeit wird nur eine Registerkarte pro App unterstützt. </span><span class="sxs-lookup"><span data-stu-id="9e9f2-234">Configurable tabs are supported only in the teams scope (not personal), and currently only **one** tab per app is supported.</span></span>

|<span data-ttu-id="9e9f2-235">Name</span><span class="sxs-lookup"><span data-stu-id="9e9f2-235">Name</span></span>| <span data-ttu-id="9e9f2-236">Typ</span><span class="sxs-lookup"><span data-stu-id="9e9f2-236">Type</span></span>| <span data-ttu-id="9e9f2-237">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="9e9f2-237">Maximum size</span></span> | <span data-ttu-id="9e9f2-238">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="9e9f2-238">Required</span></span> | <span data-ttu-id="9e9f2-239">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="9e9f2-239">Description</span></span>|
|---|---|---|---|---|
|`configurationUrl`|<span data-ttu-id="9e9f2-240">string</span><span class="sxs-lookup"><span data-stu-id="9e9f2-240">string</span></span>|<span data-ttu-id="9e9f2-241">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="9e9f2-241">2048 characters</span></span>|<span data-ttu-id="9e9f2-242">✔</span><span class="sxs-lookup"><span data-stu-id="9e9f2-242">✔</span></span>|<span data-ttu-id="9e9f2-243">Die https:// URL, die beim Konfigurieren der Registerkarte verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-243">The https:// URL to use when configuring the tab.</span></span>|
|`scopes`|<span data-ttu-id="9e9f2-244">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="9e9f2-244">array of enums</span></span>|<span data-ttu-id="9e9f2-245">1 </span><span class="sxs-lookup"><span data-stu-id="9e9f2-245">1</span></span>|<span data-ttu-id="9e9f2-246">✔</span><span class="sxs-lookup"><span data-stu-id="9e9f2-246">✔</span></span>|<span data-ttu-id="9e9f2-247">Derzeit unterstützen konfigurierbare Registerkarten nur die `team` Bereiche `groupchat` und die Bereiche.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-247">Currently, configurable tabs support only the `team` and `groupchat` scopes.</span></span> |
|`canUpdateConfiguration`|<span data-ttu-id="9e9f2-248">Boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="9e9f2-248">boolean</span></span>|||<span data-ttu-id="9e9f2-249">Ein Wert, der angibt, ob eine Instanz der Konfiguration der Registerkarte vom Benutzer nach der Erstellung aktualisiert werden kann.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-249">A value indicating whether an instance of the tab's configuration can be updated by the user after creation.</span></span> <span data-ttu-id="9e9f2-250">Standard: **true**.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-250">Default: **true**.</span></span>|
|`context` |<span data-ttu-id="9e9f2-251">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="9e9f2-251">array of enums</span></span>|<span data-ttu-id="9e9f2-252">6 </span><span class="sxs-lookup"><span data-stu-id="9e9f2-252">6</span></span>||<span data-ttu-id="9e9f2-253">Der `contextItem` Bereich, für den eine Registerkarte unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-253">The set of `contextItem` scopes where a tab is supported.</span></span> <span data-ttu-id="9e9f2-254">Standard: **[channelTab, privateChatTab, meetingChatTab, meetingDetailsTab]**.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-254">Default: **[channelTab, privateChatTab, meetingChatTab, meetingDetailsTab]**.</span></span>|
|`sharePointPreviewImage`|<span data-ttu-id="9e9f2-255">string</span><span class="sxs-lookup"><span data-stu-id="9e9f2-255">string</span></span>|<span data-ttu-id="9e9f2-256">2048</span><span class="sxs-lookup"><span data-stu-id="9e9f2-256">2048</span></span>||<span data-ttu-id="9e9f2-257">Ein relativer Dateipfad zu einem Vorschaubild für Registerkarten zur Verwendung in SharePoint.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-257">A relative file path to a tab preview image for use in SharePoint.</span></span> <span data-ttu-id="9e9f2-258">Größe 1024 x 768.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-258">Size 1024x768.</span></span> |
|`supportedSharePointHosts`|<span data-ttu-id="9e9f2-259">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="9e9f2-259">array of enums</span></span>|<span data-ttu-id="9e9f2-260">1 </span><span class="sxs-lookup"><span data-stu-id="9e9f2-260">1</span></span>||<span data-ttu-id="9e9f2-261">Definiert, wie Ihre Registerkarte in SharePoint verfügbar gemacht wird.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-261">Defines how your tab will be made available in SharePoint.</span></span> <span data-ttu-id="9e9f2-262">Optionen sind `sharePointFullPage` und `sharePointWebPart`</span><span class="sxs-lookup"><span data-stu-id="9e9f2-262">Options are `sharePointFullPage` and `sharePointWebPart`</span></span> |

## <a name="statictabs"></a><span data-ttu-id="9e9f2-263">staticTabs</span><span class="sxs-lookup"><span data-stu-id="9e9f2-263">staticTabs</span></span>

<span data-ttu-id="9e9f2-264">**Optional** – Array</span><span class="sxs-lookup"><span data-stu-id="9e9f2-264">**Optional** — array</span></span>

<span data-ttu-id="9e9f2-265">Definiert eine Reihe von Registerkarten, die standardmäßig "angeheftet" werden können, ohne dass der Benutzer sie manuell hinzufügen muss.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-265">Defines a set of tabs that can be "pinned" by default, without the user adding them manually.</span></span> <span data-ttu-id="9e9f2-266">Statische Registerkarten, die im Bereich deklariert sind, werden immer an die persönliche Benutzererfahrung `personal` der App angeheftet.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-266">Static tabs declared in `personal` scope are always pinned to the app's personal experience.</span></span> <span data-ttu-id="9e9f2-267">Im Bereich deklarierte statische `team` Registerkarten werden derzeit nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-267">Static tabs declared in the `team` scope are currently not supported.</span></span>

<span data-ttu-id="9e9f2-268">Dieses Element ist ein Array (maximal 16 Elemente) mit allen Elementen des Typs `object` .</span><span class="sxs-lookup"><span data-stu-id="9e9f2-268">This item is an array (maximum of 16 elements) with all elements of the type `object`.</span></span> <span data-ttu-id="9e9f2-269">Dieser Block ist nur für Lösungen erforderlich, die eine Lösung für statische Registerkarten bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-269">This block is required only for solutions that provide a static tab solution.</span></span>

|<span data-ttu-id="9e9f2-270">Name</span><span class="sxs-lookup"><span data-stu-id="9e9f2-270">Name</span></span>| <span data-ttu-id="9e9f2-271">Typ</span><span class="sxs-lookup"><span data-stu-id="9e9f2-271">Type</span></span>| <span data-ttu-id="9e9f2-272">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="9e9f2-272">Maximum size</span></span> | <span data-ttu-id="9e9f2-273">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="9e9f2-273">Required</span></span> | <span data-ttu-id="9e9f2-274">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="9e9f2-274">Description</span></span>|
|---|---|---|---|---|
|`entityId`|<span data-ttu-id="9e9f2-275">string</span><span class="sxs-lookup"><span data-stu-id="9e9f2-275">string</span></span>|<span data-ttu-id="9e9f2-276">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="9e9f2-276">64 characters</span></span>|<span data-ttu-id="9e9f2-277">✔</span><span class="sxs-lookup"><span data-stu-id="9e9f2-277">✔</span></span>|<span data-ttu-id="9e9f2-278">Ein eindeutiger Bezeichner für die Entität, die auf der Registerkarte angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-278">A unique identifier for the entity that the tab displays.</span></span>|
|`name`|<span data-ttu-id="9e9f2-279">string</span><span class="sxs-lookup"><span data-stu-id="9e9f2-279">string</span></span>|<span data-ttu-id="9e9f2-280">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="9e9f2-280">128 characters</span></span>|<span data-ttu-id="9e9f2-281">✔</span><span class="sxs-lookup"><span data-stu-id="9e9f2-281">✔</span></span>|<span data-ttu-id="9e9f2-282">Der Anzeigename der Registerkarte in der Kanalschnittstelle.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-282">The display name of the tab in the channel interface.</span></span>|
|`contentUrl`|<span data-ttu-id="9e9f2-283">string</span><span class="sxs-lookup"><span data-stu-id="9e9f2-283">string</span></span>||<span data-ttu-id="9e9f2-284">✔</span><span class="sxs-lookup"><span data-stu-id="9e9f2-284">✔</span></span>|<span data-ttu-id="9e9f2-285">Die https:// URL, die auf die Entitätsbenutzeroberfläche verweist, die im Zeichenbereich von Teams angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-285">The https:// URL that points to the entity UI to be displayed in the Teams canvas.</span></span>|
|`websiteUrl`|<span data-ttu-id="9e9f2-286">string</span><span class="sxs-lookup"><span data-stu-id="9e9f2-286">string</span></span>|||<span data-ttu-id="9e9f2-287">Die https:// URL, auf die verweisen soll, wenn ein Benutzer die Anzeige in einem Browser anmeldet.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-287">The https:// URL to point to if a user opts to view in a browser.</span></span>|
|`searchUrl`|<span data-ttu-id="9e9f2-288">string</span><span class="sxs-lookup"><span data-stu-id="9e9f2-288">string</span></span>|||<span data-ttu-id="9e9f2-289">Die https:// URL, auf die auf die Suchabfragen eines Benutzers verweisen soll.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-289">The https:// URL to point to for a user's search queries.</span></span>|
|`scopes`|<span data-ttu-id="9e9f2-290">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="9e9f2-290">array of enums</span></span>|<span data-ttu-id="9e9f2-291">1 </span><span class="sxs-lookup"><span data-stu-id="9e9f2-291">1</span></span>|<span data-ttu-id="9e9f2-292">✔</span><span class="sxs-lookup"><span data-stu-id="9e9f2-292">✔</span></span>|<span data-ttu-id="9e9f2-293">Derzeit unterstützen statische Registerkarten nur den Bereich, was bedeutet, dass er nur als Teil der persönlichen `personal` Erfahrung bereitgestellt werden kann.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-293">Currently, static tabs support only the `personal` scope, which means it can be provisioned only as part of the personal experience.</span></span>|
|`context` | <span data-ttu-id="9e9f2-294">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="9e9f2-294">array of enums</span></span>| <span data-ttu-id="9e9f2-295">2 </span><span class="sxs-lookup"><span data-stu-id="9e9f2-295">2</span></span>|| <span data-ttu-id="9e9f2-296">Der `contextItem` Bereich, für den eine Registerkarte unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-296">The set of `contextItem` scopes where a tab is supported.</span></span>|

> [!NOTE]
> <span data-ttu-id="9e9f2-297">Wenn Für Ihre Registerkarten kontextabhängige Informationen zum Anzeigen relevanter Inhalte oder zum Initiieren eines Authentifizierungsflusses erforderlich *sind,* finden Sie weitere Informationen unter "Kontext für [Ihre Microsoft Teams-Registerkarte".](../../tabs/how-to/access-teams-context.md)</span><span class="sxs-lookup"><span data-stu-id="9e9f2-297">If your tabs require context-dependent information to display relevant content or for initiating an authentication flow, *see* [Get context for your Microsoft Teams tab](../../tabs/how-to/access-teams-context.md).</span></span>

## <a name="bots"></a><span data-ttu-id="9e9f2-298">Bots</span><span class="sxs-lookup"><span data-stu-id="9e9f2-298">bots</span></span>

<span data-ttu-id="9e9f2-299">**Optional** – Array</span><span class="sxs-lookup"><span data-stu-id="9e9f2-299">**Optional** — array</span></span>

<span data-ttu-id="9e9f2-300">Definiert eine Botlösung zusammen mit optionalen Informationen wie z. B. Standardbefehlseigenschaften.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-300">Defines a bot solution, along with optional information such as default command properties.</span></span>

<span data-ttu-id="9e9f2-301">Das Element ist ein Array (maximal 1 Element ist derzeit nur ein Bot pro App zulässig) mit allen Elementen &mdash; des Typs `object` .</span><span class="sxs-lookup"><span data-stu-id="9e9f2-301">The item is an array (maximum of only 1 element&mdash;currently only one bot is allowed per app) with all elements of the type `object`.</span></span> <span data-ttu-id="9e9f2-302">Dieser Block ist nur für Lösungen erforderlich, die eine Boterfahrung bieten.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-302">This block is required only for solutions that provide a bot experience.</span></span>

|<span data-ttu-id="9e9f2-303">Name</span><span class="sxs-lookup"><span data-stu-id="9e9f2-303">Name</span></span>| <span data-ttu-id="9e9f2-304">Typ</span><span class="sxs-lookup"><span data-stu-id="9e9f2-304">Type</span></span>| <span data-ttu-id="9e9f2-305">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="9e9f2-305">Maximum size</span></span> | <span data-ttu-id="9e9f2-306">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="9e9f2-306">Required</span></span> | <span data-ttu-id="9e9f2-307">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="9e9f2-307">Description</span></span>|
|---|---|---|---|---|
|`botId`|<span data-ttu-id="9e9f2-308">string</span><span class="sxs-lookup"><span data-stu-id="9e9f2-308">string</span></span>|<span data-ttu-id="9e9f2-309">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="9e9f2-309">64 characters</span></span>|<span data-ttu-id="9e9f2-310">✔</span><span class="sxs-lookup"><span data-stu-id="9e9f2-310">✔</span></span>|<span data-ttu-id="9e9f2-311">Die eindeutige Microsoft-App-ID für den Bot, wie bei Bot Framework registriert.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-311">The unique Microsoft app ID for the bot as registered with the Bot Framework.</span></span> <span data-ttu-id="9e9f2-312">Dies kann mit der allgemeinen [App-ID identisch sein.](#id)</span><span class="sxs-lookup"><span data-stu-id="9e9f2-312">This may well be the same as the overall [app ID](#id).</span></span>|
|`scopes`|<span data-ttu-id="9e9f2-313">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="9e9f2-313">array of enums</span></span>|<span data-ttu-id="9e9f2-314">3 </span><span class="sxs-lookup"><span data-stu-id="9e9f2-314">3</span></span>|<span data-ttu-id="9e9f2-315">✔</span><span class="sxs-lookup"><span data-stu-id="9e9f2-315">✔</span></span>|<span data-ttu-id="9e9f2-316">Gibt an, ob der Bot eine Umgebung im Kontext eines Kanals in einem `team` oder Gruppenchat (`groupchat`) ist, oder aber eine Umgebung einzig für einen bestimmten Benutzer (`personal`).</span><span class="sxs-lookup"><span data-stu-id="9e9f2-316">Specifies whether the bot offers an experience in the context of a channel in a `team`, in a group chat (`groupchat`), or an experience scoped to an individual user alone (`personal`).</span></span> <span data-ttu-id="9e9f2-317">Diese Optionen sind nicht exklusiv.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-317">These options are non-exclusive.</span></span>|
|`needsChannelSelector`|<span data-ttu-id="9e9f2-318">Boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="9e9f2-318">boolean</span></span>|||<span data-ttu-id="9e9f2-319">Beschreibt, ob der Bot einen Benutzerhinweis verwendet, um den Bot einem bestimmten Kanal hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-319">Describes whether or not the bot utilizes a user hint to add the bot to a specific channel.</span></span> <span data-ttu-id="9e9f2-320">Standard: **`false`**</span><span class="sxs-lookup"><span data-stu-id="9e9f2-320">Default: **`false`**</span></span>|
|`isNotificationOnly`|<span data-ttu-id="9e9f2-321">Boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="9e9f2-321">boolean</span></span>|||<span data-ttu-id="9e9f2-322">Gibt an, ob ein Bot ein unidirektionaler Bot ausschließlich für Benachrichtigungen ist (im Gegensatz zu einem dialogorientierten Bot).</span><span class="sxs-lookup"><span data-stu-id="9e9f2-322">Indicates whether a bot is a one-way, notification-only bot, as opposed to a conversational bot.</span></span> <span data-ttu-id="9e9f2-323">Standard: **`false`**</span><span class="sxs-lookup"><span data-stu-id="9e9f2-323">Default: **`false`**</span></span>|
|`supportsFiles`|<span data-ttu-id="9e9f2-324">Boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="9e9f2-324">boolean</span></span>|||<span data-ttu-id="9e9f2-325">Gibt an, ob der Bot die Möglichkeit zum Hochladen/Herunterladen von Dateien in persönliche Chats unterstützt.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-325">Indicates whether the bot supports the ability to upload/download files in personal chat.</span></span> <span data-ttu-id="9e9f2-326">Standard: **`false`**</span><span class="sxs-lookup"><span data-stu-id="9e9f2-326">Default: **`false`**</span></span>|
|`supportsCalling`|<span data-ttu-id="9e9f2-327">Boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="9e9f2-327">boolean</span></span>|||<span data-ttu-id="9e9f2-328">Ein Wert, der angibt, wo ein Bot Audioanrufe unterstützt.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-328">A value indicating where a bot supports audio calling.</span></span> <span data-ttu-id="9e9f2-329">**WICHTIG:** Diese Eigenschaft ist derzeit experimentell.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-329">**IMPORTANT**: This property is currently experimental.</span></span> <span data-ttu-id="9e9f2-330">Experimentelle Eigenschaften sind möglicherweise nicht vollständig und werden möglicherweise geändert, bevor sie vollständig verfügbar werden.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-330">Experimental properties may not be complete, and may undergo changes before becoming fully available.</span></span>  <span data-ttu-id="9e9f2-331">Es wird nur zu Test- und Untersuchungszwecken bereitgestellt und sollte nicht in Produktionsanwendungen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-331">It is provided for testing and exploration purposes only and should not be used in production applications.</span></span> <span data-ttu-id="9e9f2-332">Standard: **`false`**</span><span class="sxs-lookup"><span data-stu-id="9e9f2-332">Default: **`false`**</span></span>|
|`supportsVideo`|<span data-ttu-id="9e9f2-333">Boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="9e9f2-333">boolean</span></span>|||<span data-ttu-id="9e9f2-334">Ein Wert, der angibt, wo ein Bot Videoanrufe unterstützt.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-334">A value indicating where a bot supports video calling.</span></span> <span data-ttu-id="9e9f2-335">**WICHTIG:** Diese Eigenschaft ist derzeit experimentell.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-335">**IMPORTANT**: This property is currently experimental.</span></span> <span data-ttu-id="9e9f2-336">Experimentelle Eigenschaften sind möglicherweise nicht vollständig und werden möglicherweise geändert, bevor sie vollständig verfügbar werden.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-336">Experimental properties may not be complete, and may undergo changes before becoming fully available.</span></span>  <span data-ttu-id="9e9f2-337">Es wird nur zu Test- und Untersuchungszwecken bereitgestellt und sollte nicht in Produktionsanwendungen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-337">It is provided for testing and exploration purposes only and should not be used in production applications.</span></span> <span data-ttu-id="9e9f2-338">Standard: **`false`**</span><span class="sxs-lookup"><span data-stu-id="9e9f2-338">Default: **`false`**</span></span>|

### <a name="botscommandlists"></a><span data-ttu-id="9e9f2-339">bots.commandLists</span><span class="sxs-lookup"><span data-stu-id="9e9f2-339">bots.commandLists</span></span>

<span data-ttu-id="9e9f2-340">Eine optionale Liste von Befehlen, die Ihr Bot Benutzern empfehlen kann.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-340">An optional list of commands that your bot can recommend to users.</span></span> <span data-ttu-id="9e9f2-341">Das Objekt ist ein Array (maximal 2 Elemente) mit allen Elementen des Typs; Sie müssen eine separate Befehlsliste für jeden Bereich definieren, der von `object` Ihrem Bot unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-341">The object is an array (maximum of 2 elements) with all elements of type `object`; you must define a separate command list for each scope that your bot supports.</span></span> <span data-ttu-id="9e9f2-342">Weitere [Informationen finden Sie in den Bot-Menüs.](~/bots/how-to/create-a-bot-commands-menu.md)</span><span class="sxs-lookup"><span data-stu-id="9e9f2-342">See [Bot menus](~/bots/how-to/create-a-bot-commands-menu.md) for more information.</span></span>

|<span data-ttu-id="9e9f2-343">Name</span><span class="sxs-lookup"><span data-stu-id="9e9f2-343">Name</span></span>| <span data-ttu-id="9e9f2-344">Typ</span><span class="sxs-lookup"><span data-stu-id="9e9f2-344">Type</span></span>| <span data-ttu-id="9e9f2-345">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="9e9f2-345">Maximum size</span></span> | <span data-ttu-id="9e9f2-346">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="9e9f2-346">Required</span></span> | <span data-ttu-id="9e9f2-347">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="9e9f2-347">Description</span></span>|
|---|---|---|---|---|
|`items.scopes`|<span data-ttu-id="9e9f2-348">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="9e9f2-348">array of enums</span></span>|<span data-ttu-id="9e9f2-349">3 </span><span class="sxs-lookup"><span data-stu-id="9e9f2-349">3</span></span>|<span data-ttu-id="9e9f2-350">✔</span><span class="sxs-lookup"><span data-stu-id="9e9f2-350">✔</span></span>|<span data-ttu-id="9e9f2-351">Gibt den Bereich an, für den die Befehlsliste gültig ist.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-351">Specifies the scope for which the command list is valid.</span></span> <span data-ttu-id="9e9f2-352">Mögliche Optionen sind `team`, `personal` und `groupchat`.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-352">Options are `team`, `personal`, and `groupchat`.</span></span>|
|`items.commands`|<span data-ttu-id="9e9f2-353">Array von Objekten</span><span class="sxs-lookup"><span data-stu-id="9e9f2-353">array of objects</span></span>|<span data-ttu-id="9e9f2-354">10 </span><span class="sxs-lookup"><span data-stu-id="9e9f2-354">10</span></span>|<span data-ttu-id="9e9f2-355">✔</span><span class="sxs-lookup"><span data-stu-id="9e9f2-355">✔</span></span>|<span data-ttu-id="9e9f2-356">Ein Array von Befehlen, die der Bot unterstützt:</span><span class="sxs-lookup"><span data-stu-id="9e9f2-356">An array of commands the bot supports:</span></span><br><span data-ttu-id="9e9f2-357">`title`: Name des Bot-Befehls (string, 32)</span><span class="sxs-lookup"><span data-stu-id="9e9f2-357">`title`: the bot command name (string, 32)</span></span><br><span data-ttu-id="9e9f2-358">`description`: einfache Beschreibung oder Beispiel für die Befehlssyntax und zugehörige Argumente (string, 128)</span><span class="sxs-lookup"><span data-stu-id="9e9f2-358">`description`: a simple description or example of the command syntax and its argument (string, 128)</span></span>|

### <a name="botscommandlistscommands"></a><span data-ttu-id="9e9f2-359">bots.commandLists.commands</span><span class="sxs-lookup"><span data-stu-id="9e9f2-359">bots.commandLists.commands</span></span>

|<span data-ttu-id="9e9f2-360">Name</span><span class="sxs-lookup"><span data-stu-id="9e9f2-360">Name</span></span>| <span data-ttu-id="9e9f2-361">Typ</span><span class="sxs-lookup"><span data-stu-id="9e9f2-361">Type</span></span>| <span data-ttu-id="9e9f2-362">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="9e9f2-362">Maximum size</span></span> | <span data-ttu-id="9e9f2-363">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="9e9f2-363">Required</span></span> | <span data-ttu-id="9e9f2-364">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="9e9f2-364">Description</span></span>|
|---|---|---|---|---|
|<span data-ttu-id="9e9f2-365">title</span><span class="sxs-lookup"><span data-stu-id="9e9f2-365">title</span></span>|<span data-ttu-id="9e9f2-366">string</span><span class="sxs-lookup"><span data-stu-id="9e9f2-366">string</span></span>|<span data-ttu-id="9e9f2-367">12 </span><span class="sxs-lookup"><span data-stu-id="9e9f2-367">12</span></span>|<span data-ttu-id="9e9f2-368">✔</span><span class="sxs-lookup"><span data-stu-id="9e9f2-368">✔</span></span>|<span data-ttu-id="9e9f2-369">Der Name des Botbefehls</span><span class="sxs-lookup"><span data-stu-id="9e9f2-369">The bot command name</span></span>|
|<span data-ttu-id="9e9f2-370">description</span><span class="sxs-lookup"><span data-stu-id="9e9f2-370">description</span></span>|<span data-ttu-id="9e9f2-371">string</span><span class="sxs-lookup"><span data-stu-id="9e9f2-371">string</span></span>|<span data-ttu-id="9e9f2-372">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="9e9f2-372">128 characters</span></span>|<span data-ttu-id="9e9f2-373">✔</span><span class="sxs-lookup"><span data-stu-id="9e9f2-373">✔</span></span>|<span data-ttu-id="9e9f2-374">Eine einfache Textbeschreibung oder ein Beispiel für die Befehlssyntax und deren Argumente.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-374">A simple text description or an example of the command syntax and its arguments.</span></span>|

## <a name="connectors"></a><span data-ttu-id="9e9f2-375">Connectors</span><span class="sxs-lookup"><span data-stu-id="9e9f2-375">connectors</span></span>

<span data-ttu-id="9e9f2-376">**Optional** – Array</span><span class="sxs-lookup"><span data-stu-id="9e9f2-376">**Optional** — array</span></span>

<span data-ttu-id="9e9f2-377">Der `connectors` Block definiert einen Office 365-Connector für die App.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-377">The `connectors` block defines an Office 365 Connector for the app.</span></span>

<span data-ttu-id="9e9f2-378">Das Objekt ist ein Array (maximal 1 Element) mit allen Elementen vom `object` Typ .</span><span class="sxs-lookup"><span data-stu-id="9e9f2-378">The object is an array (maximum of 1 element) with all elements of type `object`.</span></span> <span data-ttu-id="9e9f2-379">Dieser Block ist nur für Lösungen erforderlich, die einen Connector bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-379">This block is required only for solutions that provide a Connector.</span></span>

|<span data-ttu-id="9e9f2-380">Name</span><span class="sxs-lookup"><span data-stu-id="9e9f2-380">Name</span></span>| <span data-ttu-id="9e9f2-381">Typ</span><span class="sxs-lookup"><span data-stu-id="9e9f2-381">Type</span></span>| <span data-ttu-id="9e9f2-382">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="9e9f2-382">Maximum size</span></span> | <span data-ttu-id="9e9f2-383">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="9e9f2-383">Required</span></span> | <span data-ttu-id="9e9f2-384">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="9e9f2-384">Description</span></span>|
|---|---|---|---|---|
|`configurationUrl`|<span data-ttu-id="9e9f2-385">string</span><span class="sxs-lookup"><span data-stu-id="9e9f2-385">string</span></span>|<span data-ttu-id="9e9f2-386">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="9e9f2-386">2048 characters</span></span>|<span data-ttu-id="9e9f2-387">✔</span><span class="sxs-lookup"><span data-stu-id="9e9f2-387">✔</span></span>|<span data-ttu-id="9e9f2-388">Die https:// URL, die beim Konfigurieren des Connectors verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-388">The https:// URL to use when configuring the connector.</span></span>|
|`scopes`|<span data-ttu-id="9e9f2-389">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="9e9f2-389">array of enums</span></span>|<span data-ttu-id="9e9f2-390">1 </span><span class="sxs-lookup"><span data-stu-id="9e9f2-390">1</span></span>|<span data-ttu-id="9e9f2-391">✔</span><span class="sxs-lookup"><span data-stu-id="9e9f2-391">✔</span></span>|<span data-ttu-id="9e9f2-392">Gibt an, ob der Connector eine Benutzeroberfläche im Kontext eines Kanals in einem oder eine Benutzeroberfläche bietet, die auf einen einzelnen Benutzer `team` begrenzt ist ( `personal` ).</span><span class="sxs-lookup"><span data-stu-id="9e9f2-392">Specifies whether the Connector offers an experience in the context of a channel in a `team`, or an experience scoped to an individual user alone (`personal`).</span></span> <span data-ttu-id="9e9f2-393">Derzeit wird nur `team` der Bereich unterstützt.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-393">Currently, only the `team` scope is supported.</span></span>|
|`connectorId`|<span data-ttu-id="9e9f2-394">string</span><span class="sxs-lookup"><span data-stu-id="9e9f2-394">string</span></span>|<span data-ttu-id="9e9f2-395">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="9e9f2-395">64 characters</span></span>|<span data-ttu-id="9e9f2-396">✔</span><span class="sxs-lookup"><span data-stu-id="9e9f2-396">✔</span></span>|<span data-ttu-id="9e9f2-397">Ein eindeutiger Bezeichner für den Connector, der seiner ID im [Connectors Developer Dashboard entspricht.](https://aka.ms/connectorsdashboard)</span><span class="sxs-lookup"><span data-stu-id="9e9f2-397">A unique identifier for the Connector that matches its ID in the [Connectors Developer Dashboard](https://aka.ms/connectorsdashboard).</span></span>|

## <a name="composeextensions"></a><span data-ttu-id="9e9f2-398">composeExtensions</span><span class="sxs-lookup"><span data-stu-id="9e9f2-398">composeExtensions</span></span>

<span data-ttu-id="9e9f2-399">**Optional** – Array</span><span class="sxs-lookup"><span data-stu-id="9e9f2-399">**Optional** — array</span></span>

<span data-ttu-id="9e9f2-400">Definiert eine Messagingerweiterung für die App.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-400">Defines a messaging extension for the app.</span></span>

> [!NOTE]
> <span data-ttu-id="9e9f2-401">Der Name des Features wurde im November 2017 von "Verfassenerweiterung" in "Messagingerweiterung" geändert, aber der Manifestname bleibt unverändert, damit vorhandene Erweiterungen weiterhin funktionieren.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-401">The name of the feature was changed from "compose extension" to "messaging extension" in November, 2017, but the manifest name remains the same so that existing extensions continue to function.</span></span>

<span data-ttu-id="9e9f2-402">Das Element ist ein Array (maximal 1 Element) mit allen Elementen vom `object` Typ .</span><span class="sxs-lookup"><span data-stu-id="9e9f2-402">The item is an array (maximum of 1 element) with all elements of type `object`.</span></span> <span data-ttu-id="9e9f2-403">Dieser Block ist nur für Lösungen erforderlich, die eine Messagingerweiterung bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-403">This block is required only for solutions that provide a messaging extension.</span></span>

|<span data-ttu-id="9e9f2-404">Name</span><span class="sxs-lookup"><span data-stu-id="9e9f2-404">Name</span></span>| <span data-ttu-id="9e9f2-405">Typ</span><span class="sxs-lookup"><span data-stu-id="9e9f2-405">Type</span></span> | <span data-ttu-id="9e9f2-406">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="9e9f2-406">Maximum Size</span></span> | <span data-ttu-id="9e9f2-407">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="9e9f2-407">Required</span></span> | <span data-ttu-id="9e9f2-408">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="9e9f2-408">Description</span></span>|
|---|---|---|---|---|
|`botId`|<span data-ttu-id="9e9f2-409">string</span><span class="sxs-lookup"><span data-stu-id="9e9f2-409">string</span></span>|<span data-ttu-id="9e9f2-410">64</span><span class="sxs-lookup"><span data-stu-id="9e9f2-410">64</span></span>|<span data-ttu-id="9e9f2-411">✔</span><span class="sxs-lookup"><span data-stu-id="9e9f2-411">✔</span></span>|<span data-ttu-id="9e9f2-412">Die eindeutige Microsoft-App-ID für den Bot, der die Messagingerweiterung unterstützt, wie beim Bot Framework registriert.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-412">The unique Microsoft app ID for the bot that backs the messaging extension, as registered with the Bot Framework.</span></span> <span data-ttu-id="9e9f2-413">Dies kann mit der allgemeinen App-ID identisch sein.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-413">This may well be the same as the overall App ID.</span></span>|
|`commands`|<span data-ttu-id="9e9f2-414">Array von Objekten</span><span class="sxs-lookup"><span data-stu-id="9e9f2-414">array of objects</span></span>|<span data-ttu-id="9e9f2-415">10 </span><span class="sxs-lookup"><span data-stu-id="9e9f2-415">10</span></span>|<span data-ttu-id="9e9f2-416">✔</span><span class="sxs-lookup"><span data-stu-id="9e9f2-416">✔</span></span>|<span data-ttu-id="9e9f2-417">Array von Befehlen, die von der Messagingerweiterung unterstützt werden</span><span class="sxs-lookup"><span data-stu-id="9e9f2-417">Array of commands the messaging extension supports</span></span>|
|`canUpdateConfiguration`|<span data-ttu-id="9e9f2-418">Boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="9e9f2-418">boolean</span></span>|||<span data-ttu-id="9e9f2-419">Ein Wert, der angibt, ob die Konfiguration einer Messagingerweiterung vom Benutzer aktualisiert werden kann.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-419">A value indicating whether the configuration of a messaging extension can be updated by the user.</span></span> <span data-ttu-id="9e9f2-420">Standard: **False**.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-420">Default: **false**.</span></span>|
|`messageHandlers`|<span data-ttu-id="9e9f2-421">Array von Objekten</span><span class="sxs-lookup"><span data-stu-id="9e9f2-421">array of Objects</span></span>|<span data-ttu-id="9e9f2-422">5 </span><span class="sxs-lookup"><span data-stu-id="9e9f2-422">5</span></span>||<span data-ttu-id="9e9f2-423">Eine Liste von Handlern, mit denen Apps aufgerufen werden können, wenn bestimmte Bedingungen erfüllt sind.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-423">A list of handlers that allow apps to be invoked when certain conditions are met.</span></span>|
|`messageHandlers.type`|<span data-ttu-id="9e9f2-424">string</span><span class="sxs-lookup"><span data-stu-id="9e9f2-424">string</span></span>|||<span data-ttu-id="9e9f2-425">Der Typ des Nachrichtenhandlers.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-425">The type of message handler.</span></span> <span data-ttu-id="9e9f2-426">Muss `"link"` sein.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-426">Must be `"link"`.</span></span>|
|`messageHandlers.value.domains`|<span data-ttu-id="9e9f2-427">Array von Zeichenfolgen</span><span class="sxs-lookup"><span data-stu-id="9e9f2-427">array of Strings</span></span>|||<span data-ttu-id="9e9f2-428">Array von Domänen, für die sich der Linknachrichtenhandler registrieren kann.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-428">Array of domains that the link message handler can register for.</span></span>|

### <a name="composeextensionscommands"></a><span data-ttu-id="9e9f2-429">composeExtensions.commands</span><span class="sxs-lookup"><span data-stu-id="9e9f2-429">composeExtensions.commands</span></span>

<span data-ttu-id="9e9f2-430">Ihre Messagingerweiterung sollte einen oder mehrere Befehle deklarieren.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-430">Your messaging extension should declare one or more commands.</span></span> <span data-ttu-id="9e9f2-431">Jeder Befehl wird in Microsoft Teams als potenzielle Interaktion vom benutzeroberflächenbasierten Einstiegspunkt angezeigt.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-431">Each command appears in Microsoft Teams as a potential interaction from the UI-based entry point.</span></span> <span data-ttu-id="9e9f2-432">Es gibt maximal 10 Befehle.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-432">There is a maximum of 10 commands.</span></span>

<span data-ttu-id="9e9f2-433">Jedes Befehlselement ist ein Objekt mit der folgenden Struktur:</span><span class="sxs-lookup"><span data-stu-id="9e9f2-433">Each command item is an object with the following structure:</span></span>

|<span data-ttu-id="9e9f2-434">Name</span><span class="sxs-lookup"><span data-stu-id="9e9f2-434">Name</span></span>| <span data-ttu-id="9e9f2-435">Typ</span><span class="sxs-lookup"><span data-stu-id="9e9f2-435">Type</span></span>| <span data-ttu-id="9e9f2-436">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="9e9f2-436">Maximum size</span></span> | <span data-ttu-id="9e9f2-437">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="9e9f2-437">Required</span></span> | <span data-ttu-id="9e9f2-438">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="9e9f2-438">Description</span></span>|
|---|---|---|---|---|
|`id`|<span data-ttu-id="9e9f2-439">string</span><span class="sxs-lookup"><span data-stu-id="9e9f2-439">string</span></span>|<span data-ttu-id="9e9f2-440">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="9e9f2-440">64 characters</span></span>|<span data-ttu-id="9e9f2-441">✔</span><span class="sxs-lookup"><span data-stu-id="9e9f2-441">✔</span></span>|<span data-ttu-id="9e9f2-442">Die ID für den Befehl.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-442">The ID for the command.</span></span>|
|`title`|<span data-ttu-id="9e9f2-443">string</span><span class="sxs-lookup"><span data-stu-id="9e9f2-443">string</span></span>|<span data-ttu-id="9e9f2-444">32 Zeichen</span><span class="sxs-lookup"><span data-stu-id="9e9f2-444">32 characters</span></span>|<span data-ttu-id="9e9f2-445">✔</span><span class="sxs-lookup"><span data-stu-id="9e9f2-445">✔</span></span>|<span data-ttu-id="9e9f2-446">Der benutzerfreundliche Befehlsname.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-446">The user-friendly command name.</span></span>|
|`type`|<span data-ttu-id="9e9f2-447">string</span><span class="sxs-lookup"><span data-stu-id="9e9f2-447">string</span></span>|<span data-ttu-id="9e9f2-448">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="9e9f2-448">64 characters</span></span>||<span data-ttu-id="9e9f2-449">Typ des Befehls.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-449">Type of the command.</span></span> <span data-ttu-id="9e9f2-450">Einer von `query` oder `action` .</span><span class="sxs-lookup"><span data-stu-id="9e9f2-450">One of `query` or `action`.</span></span> <span data-ttu-id="9e9f2-451">Standard: **Abfrage**.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-451">Default: **query**.</span></span>|
|`description`|<span data-ttu-id="9e9f2-452">string</span><span class="sxs-lookup"><span data-stu-id="9e9f2-452">string</span></span>|<span data-ttu-id="9e9f2-453">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="9e9f2-453">128 characters</span></span>||<span data-ttu-id="9e9f2-454">Die Beschreibung, die Benutzern angezeigt wird, um den Zweck dieses Befehls anzugeben.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-454">The description that appears to users to indicate the purpose of this command.</span></span>|
|`initialRun`|<span data-ttu-id="9e9f2-455">Boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="9e9f2-455">boolean</span></span>|||<span data-ttu-id="9e9f2-456">Ein boolescher Wert, der angibt, ob der Befehl zunächst ohne Parameter ausgeführt werden soll.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-456">A boolean value that indicates whether the command should be run initially with no parameters.</span></span> <span data-ttu-id="9e9f2-457">Standard: **False**.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-457">Default: **false**.</span></span>|
|`context`|<span data-ttu-id="9e9f2-458">Array von Zeichenfolgen</span><span class="sxs-lookup"><span data-stu-id="9e9f2-458">array of Strings</span></span>|<span data-ttu-id="9e9f2-459">3 </span><span class="sxs-lookup"><span data-stu-id="9e9f2-459">3</span></span>||<span data-ttu-id="9e9f2-460">Definiert, von wo aus die Nachrichtenerweiterung aufgerufen werden kann.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-460">Defines where the message extension can be invoked from.</span></span> <span data-ttu-id="9e9f2-461">Eine beliebige Kombination von `compose` , `commandBox` `message` .</span><span class="sxs-lookup"><span data-stu-id="9e9f2-461">Any combination of`compose`,`commandBox`,`message` .</span></span> <span data-ttu-id="9e9f2-462">Der Standardwert lautet `["compose","commandBox"]`.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-462">Default is `["compose","commandBox"]`.</span></span>|
|`fetchTask`|<span data-ttu-id="9e9f2-463">Boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="9e9f2-463">boolean</span></span>|||<span data-ttu-id="9e9f2-464">Ein boolescher Wert, der angibt, ob das Aufgabenmodul dynamisch abgerufen werden soll.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-464">A boolean value that indicates if it should fetch the task module dynamically.</span></span> <span data-ttu-id="9e9f2-465">Standard: **False**.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-465">Default: **false**.</span></span>|
|`taskInfo`|<span data-ttu-id="9e9f2-466">Objekt</span><span class="sxs-lookup"><span data-stu-id="9e9f2-466">object</span></span>|||<span data-ttu-id="9e9f2-467">Geben Sie das Aufgabenmodul an, das bei Verwendung eines Befehls für eine Messagingerweiterung vor dem Laden geladen werden soll.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-467">Specify the task module to pre-load when using a messaging extension command.</span></span>|
|`taskInfo.title`|<span data-ttu-id="9e9f2-468">string</span><span class="sxs-lookup"><span data-stu-id="9e9f2-468">string</span></span>|<span data-ttu-id="9e9f2-469">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="9e9f2-469">64 characters</span></span>||<span data-ttu-id="9e9f2-470">Titel des ersten Dialogfelds.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-470">Initial dialog title.</span></span>|
|`taskInfo.width`|<span data-ttu-id="9e9f2-471">string</span><span class="sxs-lookup"><span data-stu-id="9e9f2-471">string</span></span>|||<span data-ttu-id="9e9f2-472">Dialogbreite – entweder eine Zahl in Pixel oder ein Standardlayout wie "groß", "mittel" oder "klein".</span><span class="sxs-lookup"><span data-stu-id="9e9f2-472">Dialog width - either a number in pixels or default layout such as 'large', 'medium', or 'small'.</span></span>|
|`taskInfo.height`|<span data-ttu-id="9e9f2-473">string</span><span class="sxs-lookup"><span data-stu-id="9e9f2-473">string</span></span>|||<span data-ttu-id="9e9f2-474">Dialoghöhe – entweder eine Zahl in Pixel oder ein Standardlayout wie "groß", "mittel" oder "klein".</span><span class="sxs-lookup"><span data-stu-id="9e9f2-474">Dialog height - either a number in pixels or default layout such as 'large', 'medium', or 'small'.</span></span>|
|`taskInfo.url`|<span data-ttu-id="9e9f2-475">string</span><span class="sxs-lookup"><span data-stu-id="9e9f2-475">string</span></span>|||<span data-ttu-id="9e9f2-476">Ursprüngliche Webview-URL.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-476">Initial webview URL.</span></span>|
|`parameters`|<span data-ttu-id="9e9f2-477">Array des Objekts</span><span class="sxs-lookup"><span data-stu-id="9e9f2-477">array of object</span></span>|<span data-ttu-id="9e9f2-478">5 Elemente</span><span class="sxs-lookup"><span data-stu-id="9e9f2-478">5 items</span></span>|<span data-ttu-id="9e9f2-479">✔</span><span class="sxs-lookup"><span data-stu-id="9e9f2-479">✔</span></span>|<span data-ttu-id="9e9f2-480">Die Liste der Parameter, die der Befehl verwendet.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-480">The list of parameters the command takes.</span></span> <span data-ttu-id="9e9f2-481">Minimum: 1; Maximum: 5.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-481">Minimum: 1; maximum: 5.</span></span>|
|`parameters.name`|<span data-ttu-id="9e9f2-482">string</span><span class="sxs-lookup"><span data-stu-id="9e9f2-482">string</span></span>|<span data-ttu-id="9e9f2-483">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="9e9f2-483">64 characters</span></span>|<span data-ttu-id="9e9f2-484">✔</span><span class="sxs-lookup"><span data-stu-id="9e9f2-484">✔</span></span>|<span data-ttu-id="9e9f2-485">Der Name des Parameters, wie er im Client angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-485">The name of the parameter as it appears in the client.</span></span> <span data-ttu-id="9e9f2-486">Dies ist in der Benutzeranforderung enthalten.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-486">This is included in the user request.</span></span>|
|`parameters.title`|<span data-ttu-id="9e9f2-487">string</span><span class="sxs-lookup"><span data-stu-id="9e9f2-487">string</span></span>|<span data-ttu-id="9e9f2-488">32 Zeichen</span><span class="sxs-lookup"><span data-stu-id="9e9f2-488">32 characters</span></span>|<span data-ttu-id="9e9f2-489">✔</span><span class="sxs-lookup"><span data-stu-id="9e9f2-489">✔</span></span>|<span data-ttu-id="9e9f2-490">Benutzerfreundlicher Titel für den Parameter.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-490">User-friendly title for the parameter.</span></span>|
|`parameters.description`|<span data-ttu-id="9e9f2-491">string</span><span class="sxs-lookup"><span data-stu-id="9e9f2-491">string</span></span>|<span data-ttu-id="9e9f2-492">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="9e9f2-492">128 characters</span></span>||<span data-ttu-id="9e9f2-493">Benutzerfreundliche Zeichenfolge, die den Zweck dieses Parameters beschreibt.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-493">User-friendly string that describes this parameter’s purpose.</span></span>|
|`parameters.value`|<span data-ttu-id="9e9f2-494">string</span><span class="sxs-lookup"><span data-stu-id="9e9f2-494">string</span></span>|<span data-ttu-id="9e9f2-495">512 Zeichen</span><span class="sxs-lookup"><span data-stu-id="9e9f2-495">512 characters</span></span>||<span data-ttu-id="9e9f2-496">Anfangswert für den Parameter.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-496">Initial value for the parameter.</span></span>|
|`parameters.inputType`|<span data-ttu-id="9e9f2-497">string</span><span class="sxs-lookup"><span data-stu-id="9e9f2-497">string</span></span>|<span data-ttu-id="9e9f2-498">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="9e9f2-498">128 characters</span></span>||<span data-ttu-id="9e9f2-499">Definiert den Typ des Steuerelements, das in einem Aufgabenmodul für angezeigt `fetchTask: true` wird.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-499">Defines the type of control displayed on a task module for`fetchTask: true` .</span></span> <span data-ttu-id="9e9f2-500">Einer von `text, textarea, number, date, time, toggle, choiceset` .</span><span class="sxs-lookup"><span data-stu-id="9e9f2-500">One of `text, textarea, number, date, time, toggle, choiceset` .</span></span>|
|`parameters.choices`|<span data-ttu-id="9e9f2-501">Array von Objekten</span><span class="sxs-lookup"><span data-stu-id="9e9f2-501">array of objects</span></span>|<span data-ttu-id="9e9f2-502">10 Elemente</span><span class="sxs-lookup"><span data-stu-id="9e9f2-502">10 items</span></span>||<span data-ttu-id="9e9f2-503">Die Auswahloptionen für die `choiceset` .</span><span class="sxs-lookup"><span data-stu-id="9e9f2-503">The choice options for the`choiceset`.</span></span> <span data-ttu-id="9e9f2-504">Wird nur verwendet, wenn `parameter.inputType` `choiceset` .</span><span class="sxs-lookup"><span data-stu-id="9e9f2-504">Use only when`parameter.inputType` is `choiceset`.</span></span>|
|`parameters.choices.title`|<span data-ttu-id="9e9f2-505">string</span><span class="sxs-lookup"><span data-stu-id="9e9f2-505">string</span></span>|<span data-ttu-id="9e9f2-506">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="9e9f2-506">128 characters</span></span>|<span data-ttu-id="9e9f2-507">✔</span><span class="sxs-lookup"><span data-stu-id="9e9f2-507">✔</span></span>|<span data-ttu-id="9e9f2-508">Der Titel der Auswahl.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-508">Title of the choice.</span></span>|
|`parameters.choices.value`|<span data-ttu-id="9e9f2-509">string</span><span class="sxs-lookup"><span data-stu-id="9e9f2-509">string</span></span>|<span data-ttu-id="9e9f2-510">512 Zeichen</span><span class="sxs-lookup"><span data-stu-id="9e9f2-510">512 characters</span></span>|<span data-ttu-id="9e9f2-511">✔</span><span class="sxs-lookup"><span data-stu-id="9e9f2-511">✔</span></span>|<span data-ttu-id="9e9f2-512">Value of the choice.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-512">Value of the choice.</span></span>|

## <a name="permissions"></a><span data-ttu-id="9e9f2-513">Berechtigungen</span><span class="sxs-lookup"><span data-stu-id="9e9f2-513">permissions</span></span>

<span data-ttu-id="9e9f2-514">**Optional** – Zeichenfolgenarray</span><span class="sxs-lookup"><span data-stu-id="9e9f2-514">**Optional** — array of strings</span></span>

<span data-ttu-id="9e9f2-515">Ein Array, von dem angegeben wird, welche Berechtigungen die App anfordert, wodurch Endbenutzer wissen, `string` wie die Erweiterung funktioniert.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-515">An array of `string` which specifies which permissions the app requests, which lets end users know how the extension will perform.</span></span> <span data-ttu-id="9e9f2-516">Die folgenden Optionen sind nicht exklusiv:</span><span class="sxs-lookup"><span data-stu-id="9e9f2-516">The following options are non-exclusive:</span></span>

* <span data-ttu-id="9e9f2-517">`identity`&emsp;Erfordert Informationen zur Benutzeridentität</span><span class="sxs-lookup"><span data-stu-id="9e9f2-517">`identity` &emsp; Requires user identity information</span></span>
* <span data-ttu-id="9e9f2-518">`messageTeamMembers`&emsp;Erfordert die Berechtigung zum Senden direkter Nachrichten an Teammitglieder</span><span class="sxs-lookup"><span data-stu-id="9e9f2-518">`messageTeamMembers` &emsp; Requires permission to send direct messages to team members</span></span>

<span data-ttu-id="9e9f2-519">Wenn Sie diese Berechtigungen beim Aktualisieren Ihrer App ändern, wiederholen Ihre Benutzer den Zustimmungsprozess, wenn sie die aktualisierte App zum ersten Mal ausführen.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-519">Changing these permissions when updating your app will cause your users to repeat the consent process the first time they run the updated app.</span></span> <span data-ttu-id="9e9f2-520">Weitere [Informationen finden Sie unter Aktualisieren](~/concepts/deploy-and-publish/appsource/post-publish/overview.md) Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-520">See [Updating your app](~/concepts/deploy-and-publish/appsource/post-publish/overview.md) for more information.</span></span>

## <a name="devicepermissions"></a><span data-ttu-id="9e9f2-521">devicePermissions</span><span class="sxs-lookup"><span data-stu-id="9e9f2-521">devicePermissions</span></span>

<span data-ttu-id="9e9f2-522">**Optional** – Zeichenfolgenarray</span><span class="sxs-lookup"><span data-stu-id="9e9f2-522">**Optional** — array of strings</span></span>

<span data-ttu-id="9e9f2-523">Gibt die systemeigenen Features auf dem Gerät eines Benutzers an, auf die Ihre App Zugriff anfordern kann.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-523">Specifies the native features on a user's device that your app may request access to.</span></span> <span data-ttu-id="9e9f2-524">Mögliche Optionen sind:</span><span class="sxs-lookup"><span data-stu-id="9e9f2-524">Options are:</span></span>

* `geolocation`
* `media`
* `notifications`
* `midi`
* `openExternal`

## <a name="validdomains"></a><span data-ttu-id="9e9f2-525">validDomains</span><span class="sxs-lookup"><span data-stu-id="9e9f2-525">validDomains</span></span>

<span data-ttu-id="9e9f2-526">**Optional**, mit Ausnahme **von "Erforderlich"** (sofern angegeben)</span><span class="sxs-lookup"><span data-stu-id="9e9f2-526">**Optional**, except **Required** where noted</span></span>

<span data-ttu-id="9e9f2-527">Eine Liste gültiger Domänen für Websites, die von der App erwartet werden, innerhalb des Teams-Clients zu laden.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-527">A list of valid domains for websites the app expects to load within the Teams client.</span></span> <span data-ttu-id="9e9f2-528">Domänenauflistungen können Platzhalter enthalten, z. B. `*.example.com` .</span><span class="sxs-lookup"><span data-stu-id="9e9f2-528">Domain listings can include wildcards, for example `*.example.com`.</span></span> <span data-ttu-id="9e9f2-529">Dies entspricht genau einem Segment der Domäne. Wenn Sie übereinstimmen müssen, `a.b.example.com` verwenden Sie `*.*.example.com` .</span><span class="sxs-lookup"><span data-stu-id="9e9f2-529">This matches exactly one segment of the domain; if you need to match `a.b.example.com` then use `*.*.example.com`.</span></span> <span data-ttu-id="9e9f2-530">Wenn Ihre Registerkartenkonfiguration oder Inhaltsbenutzeroberfläche neben der Für die Registerkartenkonfiguration verwendeten Domäne zu einer anderen Domäne navigieren muss, muss diese Domäne hier angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-530">If your tab configuration or content UI needs to navigate to any other domain besides the one use for tab configuration, that domain must be specified here.</span></span>

<span data-ttu-id="9e9f2-531">Es ist **jedoch nicht** erforderlich, die Domänen von Identitätsanbietern, die Sie unterstützen möchten, in Ihre App zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-531">It is **not** necessary to include the domains of identity providers you want to support in your app, however.</span></span> <span data-ttu-id="9e9f2-532">Um sich z. B. mithilfe einer Google-ID zu authentifizieren, ist es erforderlich, zu accounts.google.com umzuleiten, sie sollten jedoch nicht accounts.google.com `validDomains[]` enthalten.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-532">For example, to authenticate using a Google ID, it's necessary to redirect to accounts.google.com, but you should not include accounts.google.com in `validDomains[]`.</span></span>

<span data-ttu-id="9e9f2-533">Teams-Apps, für die ihre eigenen SharePoint-URLs ordnungsgemäß funktionieren müssen, enthalten möglicherweise "{teamsitedomain}" in der Liste der gültigen Domänen.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-533">Teams apps that require their own sharepoint URLs to function well, may include "{teamsitedomain}" in their valid domain list.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9e9f2-534">Fügen Sie keine Domänen hinzu, die sich außerhalb Ihrer Kontrolle befinden, weder direkt noch über Platzhalter.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-534">Do not add domains that are outside your control, either directly or via wildcards.</span></span> <span data-ttu-id="9e9f2-535">Beispielsweise ist `yourapp.onmicrosoft.com` er gültig, aber `*.onmicrosoft.com` ungültig.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-535">For example, `yourapp.onmicrosoft.com` is valid, but `*.onmicrosoft.com` is not valid.</span></span>

<span data-ttu-id="9e9f2-536">Das Objekt ist ein Array mit allen Elementen des Typs `string` .</span><span class="sxs-lookup"><span data-stu-id="9e9f2-536">The object is an array with all elements of the type `string`.</span></span>

## <a name="webapplicationinfo"></a><span data-ttu-id="9e9f2-537">webApplicationInfo</span><span class="sxs-lookup"><span data-stu-id="9e9f2-537">webApplicationInfo</span></span>

<span data-ttu-id="9e9f2-538">**Optional** – Objekt</span><span class="sxs-lookup"><span data-stu-id="9e9f2-538">**Optional** — object</span></span>

<span data-ttu-id="9e9f2-539">Geben Sie Ihre Azure Active Directory (Azure AD)-App-ID und Microsoft Graph-Informationen an, damit sich Benutzer nahtlos bei Ihrer App anmelden können.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-539">Specify your Azure Active Directory (Azure AD) App ID and Microsoft Graph information to help users seamlessly sign into your app.</span></span> <span data-ttu-id="9e9f2-540">Wenn Ihre App in Azure AD registriert ist, müssen Sie die App-ID bereitstellen, damit Administratoren die Berechtigungen auf einfache Weise überprüfen und die Zustimmung im Teams Admin Center erteilen können.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-540">If your app is registered in Azure AD, you must provide the App ID, so that administrators can easily review permissions and grant consent in Teams admin center.</span></span>

|<span data-ttu-id="9e9f2-541">Name</span><span class="sxs-lookup"><span data-stu-id="9e9f2-541">Name</span></span>| <span data-ttu-id="9e9f2-542">Typ</span><span class="sxs-lookup"><span data-stu-id="9e9f2-542">Type</span></span>| <span data-ttu-id="9e9f2-543">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="9e9f2-543">Maximum size</span></span> | <span data-ttu-id="9e9f2-544">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="9e9f2-544">Required</span></span> | <span data-ttu-id="9e9f2-545">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="9e9f2-545">Description</span></span>|
|---|---|---|---|---|
|`id`|<span data-ttu-id="9e9f2-546">string</span><span class="sxs-lookup"><span data-stu-id="9e9f2-546">string</span></span>|<span data-ttu-id="9e9f2-547">36 Zeichen</span><span class="sxs-lookup"><span data-stu-id="9e9f2-547">36 characters</span></span>|<span data-ttu-id="9e9f2-548">✔</span><span class="sxs-lookup"><span data-stu-id="9e9f2-548">✔</span></span>|<span data-ttu-id="9e9f2-549">AAD-Anwendungs-ID der App.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-549">AAD application id of the app.</span></span> <span data-ttu-id="9e9f2-550">Diese ID muss eine GUID sein.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-550">This id must be a GUID.</span></span>|
|`resource`|<span data-ttu-id="9e9f2-551">string</span><span class="sxs-lookup"><span data-stu-id="9e9f2-551">string</span></span>|<span data-ttu-id="9e9f2-552">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="9e9f2-552">2048 characters</span></span>|<span data-ttu-id="9e9f2-553">✔</span><span class="sxs-lookup"><span data-stu-id="9e9f2-553">✔</span></span>|<span data-ttu-id="9e9f2-554">Ressourcen-URL der App zum Abrufen des Authentifizierungstokens für SSO.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-554">Resource URL of app for acquiring auth token for SSO.</span></span> </br> <span data-ttu-id="9e9f2-555">**HINWEIS:** Wenn Sie SSO nicht verwenden, stellen Sie sicher, dass Sie in dieses Feld einen Dummyzeichenfolgenwert in Ihr App-Manifest eingeben, um beispielsweise eine https://notapplicable Fehlerantwort zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-555">**NOTE:** If you are not using SSO, ensure that you enter a dummy string value in this field to your app manifest, for example, https://notapplicable to avoid an error response.</span></span> |
|`applicationPermissions`|<span data-ttu-id="9e9f2-556">array of strings</span><span class="sxs-lookup"><span data-stu-id="9e9f2-556">array of strings</span></span>|<span data-ttu-id="9e9f2-557">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="9e9f2-557">128 characters</span></span>||<span data-ttu-id="9e9f2-558">Geben Sie eine [präzise ressourcenspezifische Zustimmung an.](../../graph-api/rsc/resource-specific-consent.md#resource-specific-permissions)</span><span class="sxs-lookup"><span data-stu-id="9e9f2-558">Specify granular [resource specific consent](../../graph-api/rsc/resource-specific-consent.md#resource-specific-permissions).</span></span>|

## <a name="showloadingindicator"></a><span data-ttu-id="9e9f2-559">showLoadingIndicator</span><span class="sxs-lookup"><span data-stu-id="9e9f2-559">showLoadingIndicator</span></span>

<span data-ttu-id="9e9f2-560">**Optional** – boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="9e9f2-560">**Optional** — boolean</span></span>

<span data-ttu-id="9e9f2-561">Gibt an, ob die Ladeanzeige angezeigt werden soll, wenn eine App/Registerkarte geladen wird.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-561">Indicate whether or not to show the loading indicator when an app/tab is loading.</span></span> <span data-ttu-id="9e9f2-562">Standard: **False**.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-562">Default: **false**.</span></span>
>[!NOTE]
><span data-ttu-id="9e9f2-563">Wenn Sie "showLoadingIndicator : true" in Ihrem App-Manifest festlegen, müssen Sie die Inhaltsseiten Ihrer Registerkarten und Aufgabenmodule [](../../tabs/how-to/create-tab-pages/content-page.md#show-a-native-loading-indicator) so ändern, dass das protokoll unter Anzeigen eines nativen Ladeindikatordokuments beschrieben wird.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-563">If you set "showLoadingIndicator : true" in your app manifest, then for the page to load correctly, you must modify the content pages of your tabs and task modules as per the protocol described in [Show a native loading indicator](../../tabs/how-to/create-tab-pages/content-page.md#show-a-native-loading-indicator) document.</span></span>


## <a name="isfullscreen"></a><span data-ttu-id="9e9f2-564">isFullScreen</span><span class="sxs-lookup"><span data-stu-id="9e9f2-564">isFullScreen</span></span>

 <span data-ttu-id="9e9f2-565">**Optional** – boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="9e9f2-565">**Optional** — boolean</span></span>

<span data-ttu-id="9e9f2-566">Geben Sie an, wo eine persönliche App mit oder ohne Tabulatorleiste gerendert wird.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-566">Indicate where a personal app is rendered with or without a tab-header bar.</span></span> <span data-ttu-id="9e9f2-567">Standard: **False**.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-567">Default: **false**.</span></span>

## <a name="activities"></a><span data-ttu-id="9e9f2-568">Aktivitäten</span><span class="sxs-lookup"><span data-stu-id="9e9f2-568">activities</span></span>

<span data-ttu-id="9e9f2-569">**Optional** – Objekt</span><span class="sxs-lookup"><span data-stu-id="9e9f2-569">**Optional** — object</span></span>

<span data-ttu-id="9e9f2-570">Definieren Sie die Eigenschaften, die Ihre App zum Veröffentlichen in einem Benutzeraktivitätsfeed verwendet.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-570">Define the properties your app will use to post to a user activity feed.</span></span>

|<span data-ttu-id="9e9f2-571">Name</span><span class="sxs-lookup"><span data-stu-id="9e9f2-571">Name</span></span>| <span data-ttu-id="9e9f2-572">Typ</span><span class="sxs-lookup"><span data-stu-id="9e9f2-572">Type</span></span>| <span data-ttu-id="9e9f2-573">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="9e9f2-573">Maximum size</span></span> | <span data-ttu-id="9e9f2-574">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="9e9f2-574">Required</span></span> | <span data-ttu-id="9e9f2-575">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="9e9f2-575">Description</span></span>|
|---|---|---|---|---|
|`activityTypes`|<span data-ttu-id="9e9f2-576">Array von Objekten</span><span class="sxs-lookup"><span data-stu-id="9e9f2-576">array of Objects</span></span>|<span data-ttu-id="9e9f2-577">128 Elemente</span><span class="sxs-lookup"><span data-stu-id="9e9f2-577">128 items</span></span>| | <span data-ttu-id="9e9f2-578">Geben Sie die Arten von Aktivitäten an, die Ihre App in einem Benutzeraktivitätsfeed veröffentlichen kann.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-578">Specify the types of activities that your app can post to a users activity feed.</span></span>|

### <a name="activitiesactivitytypes"></a><span data-ttu-id="9e9f2-579">activities.activityTypes</span><span class="sxs-lookup"><span data-stu-id="9e9f2-579">activities.activityTypes</span></span>

|<span data-ttu-id="9e9f2-580">Name</span><span class="sxs-lookup"><span data-stu-id="9e9f2-580">Name</span></span>| <span data-ttu-id="9e9f2-581">Typ</span><span class="sxs-lookup"><span data-stu-id="9e9f2-581">Type</span></span>| <span data-ttu-id="9e9f2-582">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="9e9f2-582">Maximum size</span></span> | <span data-ttu-id="9e9f2-583">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="9e9f2-583">Required</span></span> | <span data-ttu-id="9e9f2-584">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="9e9f2-584">Description</span></span>|
|---|---|---|---|---|
|`type`|<span data-ttu-id="9e9f2-585">string</span><span class="sxs-lookup"><span data-stu-id="9e9f2-585">string</span></span>|<span data-ttu-id="9e9f2-586">32 Zeichen</span><span class="sxs-lookup"><span data-stu-id="9e9f2-586">32 characters</span></span>|<span data-ttu-id="9e9f2-587">✔</span><span class="sxs-lookup"><span data-stu-id="9e9f2-587">✔</span></span>|<span data-ttu-id="9e9f2-588">Der Benachrichtigungstyp.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-588">The notification type.</span></span> <span data-ttu-id="9e9f2-589">*Siehe unten*.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-589">*See below*.</span></span>|
|`description`|<span data-ttu-id="9e9f2-590">string</span><span class="sxs-lookup"><span data-stu-id="9e9f2-590">string</span></span>|<span data-ttu-id="9e9f2-591">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="9e9f2-591">128 characters</span></span>|<span data-ttu-id="9e9f2-592">✔</span><span class="sxs-lookup"><span data-stu-id="9e9f2-592">✔</span></span>|<span data-ttu-id="9e9f2-593">Eine kurze Beschreibung der Benachrichtigung.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-593">A brief description of the notification.</span></span> <span data-ttu-id="9e9f2-594">*Siehe unten*.</span><span class="sxs-lookup"><span data-stu-id="9e9f2-594">*See below*.</span></span>|
|`templateText`|<span data-ttu-id="9e9f2-595">string</span><span class="sxs-lookup"><span data-stu-id="9e9f2-595">string</span></span>|<span data-ttu-id="9e9f2-596">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="9e9f2-596">128 characters</span></span>|<span data-ttu-id="9e9f2-597">✔</span><span class="sxs-lookup"><span data-stu-id="9e9f2-597">✔</span></span>|<span data-ttu-id="9e9f2-598">Beispiel: "{actor}: Aufgabe {taskId} für Sie erstellt"</span><span class="sxs-lookup"><span data-stu-id="9e9f2-598">Ex: "{actor} created task {taskId} for you"</span></span>|

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
