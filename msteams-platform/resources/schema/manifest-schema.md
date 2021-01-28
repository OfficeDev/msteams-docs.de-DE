---
title: Manifestschemareferenz
description: Beschreibt das Manifestschema für Microsoft Teams
ms.topic: reference
keywords: Teams-Manifestschema
author: laujan
ms.author: lajanuar
ms.openlocfilehash: 8fff56d229cc137df8356b06214893dc984396a0
ms.sourcegitcommit: 976e870cc925f61b76c3830ec04ba6e4bdfde32f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/27/2021
ms.locfileid: "50014607"
---
# <a name="reference-manifest-schema-for-microsoft-teams"></a><span data-ttu-id="bd65c-104">Referenz: Manifestschema für Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="bd65c-104">Reference: Manifest schema for Microsoft Teams</span></span>

<span data-ttu-id="bd65c-105">Das Microsoft Teams-Manifest beschreibt, wie die App in das Microsoft Teams-Produkt integriert wird.</span><span class="sxs-lookup"><span data-stu-id="bd65c-105">The Microsoft Teams manifest describes how the app integrates into the Microsoft Teams product.</span></span> <span data-ttu-id="bd65c-106">Ihr Manifest muss dem Schema entsprechen, das unter [`https://developer.microsoft.com/json-schemas/teams/v1.8/MicrosoftTeams.schema.json`]( https://developer.microsoft.com/json-schemas/teams/v1.8/MicrosoftTeams.schema.json) gehostet wird.</span><span class="sxs-lookup"><span data-stu-id="bd65c-106">Your manifest must conform to the schema hosted at [`https://developer.microsoft.com/json-schemas/teams/v1.8/MicrosoftTeams.schema.json`]( https://developer.microsoft.com/json-schemas/teams/v1.8/MicrosoftTeams.schema.json).</span></span> <span data-ttu-id="bd65c-107">Frühere Versionen 1.0-1.4 werden ebenfalls unterstützt (unter Verwendung von "v1.x" in der URL).</span><span class="sxs-lookup"><span data-stu-id="bd65c-107">Previous versions 1.0-1.4 are also supported (using "v1.x" in the URL).</span></span>

<span data-ttu-id="bd65c-108">Das folgende Schemabeispiel zeigt alle Erweiterungsoptionen.</span><span class="sxs-lookup"><span data-stu-id="bd65c-108">The following schema sample shows all extensibility options.</span></span>

## <a name="sample-full-manifest"></a><span data-ttu-id="bd65c-109">Beispiel für vollständiges Manifest</span><span class="sxs-lookup"><span data-stu-id="bd65c-109">Sample full manifest</span></span>

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

<span data-ttu-id="bd65c-110">Das Schema definiert die folgenden Eigenschaften:</span><span class="sxs-lookup"><span data-stu-id="bd65c-110">The schema defines the following properties:</span></span>

## <a name="schema"></a><span data-ttu-id="bd65c-111">$schema</span><span class="sxs-lookup"><span data-stu-id="bd65c-111">$schema</span></span>

<span data-ttu-id="bd65c-112">*Optional, aber empfohlen –* Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="bd65c-112">*Optional, but recommended* — string</span></span>

<span data-ttu-id="bd65c-113">Die https:// URL, die auf das JSON-Schema für das Manifest verweist.</span><span class="sxs-lookup"><span data-stu-id="bd65c-113">The https:// URL referencing the JSON Schema for the manifest.</span></span>

## <a name="manifestversion"></a><span data-ttu-id="bd65c-114">manifestVersion</span><span class="sxs-lookup"><span data-stu-id="bd65c-114">manifestVersion</span></span>

<span data-ttu-id="bd65c-115">**Erforderlich** – Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="bd65c-115">**Required** — string</span></span>

<span data-ttu-id="bd65c-116">Die Version des Manifestschemas, das dieses Manifest verwendet.</span><span class="sxs-lookup"><span data-stu-id="bd65c-116">The version of the manifest schema this manifest is using.</span></span> <span data-ttu-id="bd65c-117">Er sollte "1.7" sein.</span><span class="sxs-lookup"><span data-stu-id="bd65c-117">It should be "1.7".</span></span>

## <a name="version"></a><span data-ttu-id="bd65c-118">Version</span><span class="sxs-lookup"><span data-stu-id="bd65c-118">version</span></span>

<span data-ttu-id="bd65c-119">**Erforderlich** – Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="bd65c-119">**Required** — string</span></span>

<span data-ttu-id="bd65c-120">Die Version der bestimmten App.</span><span class="sxs-lookup"><span data-stu-id="bd65c-120">The version of the specific app.</span></span> <span data-ttu-id="bd65c-121">Wenn Sie etwas in Ihrem Manifest aktualisieren, muss auch die Version erhöht werden.</span><span class="sxs-lookup"><span data-stu-id="bd65c-121">If you update something in your manifest, the version must be incremented as well.</span></span> <span data-ttu-id="bd65c-122">Auf diese Weise wird bei der Installation des neuen Manifests das vorhandene überschrieben, und der Benutzer erhält die neue Funktionalität.</span><span class="sxs-lookup"><span data-stu-id="bd65c-122">This way, when the new manifest is installed, it will overwrite the existing one and the user will get the new functionality.</span></span> <span data-ttu-id="bd65c-123">Wenn diese App an den Store übermittelt wurde, muss das neue Manifest erneut übermittelt und erneut überprüft werden.</span><span class="sxs-lookup"><span data-stu-id="bd65c-123">If this app was submitted to the store, the new manifest will have to be re-submitted and re-validated.</span></span> <span data-ttu-id="bd65c-124">Anschließend erhalten Benutzer dieser App das neue aktualisierte Manifest automatisch in ein paar Stunden, nachdem sie genehmigt wurde.</span><span class="sxs-lookup"><span data-stu-id="bd65c-124">Then, users of this app will get the new updated manifest automatically in a few hours, after it is approved.</span></span>

<span data-ttu-id="bd65c-125">Wenn sich die von der App angeforderten Berechtigungen ändern, werden die Benutzer aufgefordert, ein Upgrade zu starten und der App erneut zu zustimmen.</span><span class="sxs-lookup"><span data-stu-id="bd65c-125">If the app requested permissions change, users will be prompted to upgrade and re-consent to the app.</span></span>

<span data-ttu-id="bd65c-126">Diese Versionszeichenfolge muss dem [Semverstandard](http://semver.org/) (MAJOR. MINOR. PATCH).</span><span class="sxs-lookup"><span data-stu-id="bd65c-126">This version string must follow the [semver](http://semver.org/) standard (MAJOR.MINOR.PATCH).</span></span>

## <a name="id"></a><span data-ttu-id="bd65c-127">id</span><span class="sxs-lookup"><span data-stu-id="bd65c-127">id</span></span>

<span data-ttu-id="bd65c-128">**Erforderlich** – Microsoft-App-ID</span><span class="sxs-lookup"><span data-stu-id="bd65c-128">**Required** — Microsoft app ID</span></span>

<span data-ttu-id="bd65c-129">Der eindeutige von Microsoft generierte Bezeichner für diese App.</span><span class="sxs-lookup"><span data-stu-id="bd65c-129">The unique Microsoft-generated identifier for this app.</span></span> <span data-ttu-id="bd65c-130">Wenn Sie einen Bot über das Microsoft Bot Framework registriert haben oder sich die Web-App Ihrer Registerkarte bereits bei Microsoft angemeldet hat, sollten Sie bereits über eine ID verfügen und sie hier eingeben.</span><span class="sxs-lookup"><span data-stu-id="bd65c-130">If you have registered a bot via the Microsoft Bot Framework, or your tab's web app already signs in with Microsoft, you should already have an ID and should enter it here.</span></span> <span data-ttu-id="bd65c-131">Andernfalls sollten Sie eine neue ID im Microsoft-Anwendungsregistrierungsportal[(](https://apps.dev.microsoft.com)Meine Anwendungen) generieren, sie hier eingeben und dann wiederverwenden, wenn Sie einen Bot hinzufügen. Hinweis: Wenn Sie ein Update für Ihre vorhandene App in AppSource übermitteln, darf die ID in Ihrem Manifest nicht geändert werden.</span><span class="sxs-lookup"><span data-stu-id="bd65c-131">Otherwise, you should generate a new ID at the Microsoft Application Registration Portal ([My Applications](https://apps.dev.microsoft.com)), enter it here, and then reuse it when you add a bot.Note: If you are submitting an update to your existing app in AppSource, the ID in your manifest must not be modified.</span></span>

## <a name="developer"></a><span data-ttu-id="bd65c-132">developer</span><span class="sxs-lookup"><span data-stu-id="bd65c-132">developer</span></span>

<span data-ttu-id="bd65c-133">**Erforderlich** – Objekt</span><span class="sxs-lookup"><span data-stu-id="bd65c-133">**Required** — object</span></span>

<span data-ttu-id="bd65c-134">Gibt Informationen zu Ihrem Unternehmen an.</span><span class="sxs-lookup"><span data-stu-id="bd65c-134">Specifies information about your company.</span></span> <span data-ttu-id="bd65c-135">Bei an AppSource (früher Office Store) übermittelten Apps müssen diese Werte mit den Informationen in Ihrem Eintrag "AppSource" übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="bd65c-135">For apps submitted to AppSource (formerly Office Store), these values must match the information in your AppSource entry.</span></span> <span data-ttu-id="bd65c-136">Weitere Informationen [finden Sie in unseren Veröffentlichungsrichtlinien.](~/concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md)</span><span class="sxs-lookup"><span data-stu-id="bd65c-136">See our [publishing guidelines](~/concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md) for additional information.</span></span>

|<span data-ttu-id="bd65c-137">Name</span><span class="sxs-lookup"><span data-stu-id="bd65c-137">Name</span></span>| <span data-ttu-id="bd65c-138">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="bd65c-138">Maximum size</span></span> | <span data-ttu-id="bd65c-139">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="bd65c-139">Required</span></span> | <span data-ttu-id="bd65c-140">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="bd65c-140">Description</span></span>|
|---|---|---|---|
|`name`|<span data-ttu-id="bd65c-141">32 Zeichen</span><span class="sxs-lookup"><span data-stu-id="bd65c-141">32 characters</span></span>|<span data-ttu-id="bd65c-142">✔</span><span class="sxs-lookup"><span data-stu-id="bd65c-142">✔</span></span>|<span data-ttu-id="bd65c-143">Der Anzeigename für den Entwickler.</span><span class="sxs-lookup"><span data-stu-id="bd65c-143">The display name for the developer.</span></span>|
|`websiteUrl`|<span data-ttu-id="bd65c-144">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="bd65c-144">2048 characters</span></span>|<span data-ttu-id="bd65c-145">✔</span><span class="sxs-lookup"><span data-stu-id="bd65c-145">✔</span></span>|<span data-ttu-id="bd65c-146">Die https:// URL zur Website des Entwicklers.</span><span class="sxs-lookup"><span data-stu-id="bd65c-146">The https:// URL to the developer's website.</span></span> <span data-ttu-id="bd65c-147">Über diesen Link sollten Benutzer zu Ihrem Unternehmen oder zu ihrer produktspezifischen Angebotsseite gelangen.</span><span class="sxs-lookup"><span data-stu-id="bd65c-147">This link should take users to your company or product-specific landing page.</span></span>|
|`privacyUrl`|<span data-ttu-id="bd65c-148">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="bd65c-148">2048 characters</span></span>|<span data-ttu-id="bd65c-149">✔</span><span class="sxs-lookup"><span data-stu-id="bd65c-149">✔</span></span>|<span data-ttu-id="bd65c-150">Die https:// URL zur Datenschutzrichtlinie des Entwicklers.</span><span class="sxs-lookup"><span data-stu-id="bd65c-150">The https:// URL to the developer's privacy policy.</span></span>|
|`termsOfUseUrl`|<span data-ttu-id="bd65c-151">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="bd65c-151">2048 characters</span></span>|<span data-ttu-id="bd65c-152">✔</span><span class="sxs-lookup"><span data-stu-id="bd65c-152">✔</span></span>|<span data-ttu-id="bd65c-153">Die https:// URL zu den Nutzungsbedingungen des Entwicklers.</span><span class="sxs-lookup"><span data-stu-id="bd65c-153">The https:// URL to the developer's terms of use.</span></span>|
|`mpnId`|<span data-ttu-id="bd65c-154">10 Zeichen</span><span class="sxs-lookup"><span data-stu-id="bd65c-154">10 characters</span></span>| |<span data-ttu-id="bd65c-155">**Optional** Die Microsoft Partner Network-ID, die die Partnerorganisation identifiziert, die die App erstellt.</span><span class="sxs-lookup"><span data-stu-id="bd65c-155">**Optional** The Microsoft Partner Network ID that identifies the partner organization building the app.</span></span>|

## <a name="name"></a><span data-ttu-id="bd65c-156">name</span><span class="sxs-lookup"><span data-stu-id="bd65c-156">name</span></span>

<span data-ttu-id="bd65c-157">**Erforderlich** – Objekt</span><span class="sxs-lookup"><span data-stu-id="bd65c-157">**Required** — object</span></span>

<span data-ttu-id="bd65c-158">Der Name Ihrer App-Erfahrung, der Benutzern in der Teams-Erfahrung angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="bd65c-158">The name of your app experience, displayed to users in the Teams experience.</span></span> <span data-ttu-id="bd65c-159">Bei an AppSource übermittelten Apps müssen diese Werte mit den Informationen in Ihrem Eintrag "AppSource" übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="bd65c-159">For apps submitted to AppSource, these values must match the information in your AppSource entry.</span></span> <span data-ttu-id="bd65c-160">Die Werte von `short` und sollten nicht identisch `full` sein.</span><span class="sxs-lookup"><span data-stu-id="bd65c-160">The values of `short` and `full` should not be the same.</span></span>

|<span data-ttu-id="bd65c-161">Name</span><span class="sxs-lookup"><span data-stu-id="bd65c-161">Name</span></span>| <span data-ttu-id="bd65c-162">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="bd65c-162">Maximum size</span></span> | <span data-ttu-id="bd65c-163">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="bd65c-163">Required</span></span> | <span data-ttu-id="bd65c-164">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="bd65c-164">Description</span></span>|
|---|---|---|---|
|`short`|<span data-ttu-id="bd65c-165">30 Zeichen</span><span class="sxs-lookup"><span data-stu-id="bd65c-165">30 characters</span></span>|<span data-ttu-id="bd65c-166">✔</span><span class="sxs-lookup"><span data-stu-id="bd65c-166">✔</span></span>|<span data-ttu-id="bd65c-167">Der kurze Anzeigename für die App.</span><span class="sxs-lookup"><span data-stu-id="bd65c-167">The short display name for the app.</span></span>|
|`full`|<span data-ttu-id="bd65c-168">100 Zeichen</span><span class="sxs-lookup"><span data-stu-id="bd65c-168">100 characters</span></span>||<span data-ttu-id="bd65c-169">Der vollständige Name der App, der verwendet wird, wenn der vollständige Name der App 30 Zeichen überschreitet.</span><span class="sxs-lookup"><span data-stu-id="bd65c-169">The full name of the app, used if the full app name exceeds 30 characters.</span></span>|

## <a name="description"></a><span data-ttu-id="bd65c-170">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="bd65c-170">description</span></span>

<span data-ttu-id="bd65c-171">**Erforderlich** – Objekt</span><span class="sxs-lookup"><span data-stu-id="bd65c-171">**Required** — object</span></span>

<span data-ttu-id="bd65c-172">Beschreibt Ihre App für Benutzer.</span><span class="sxs-lookup"><span data-stu-id="bd65c-172">Describes your app to users.</span></span> <span data-ttu-id="bd65c-173">Bei an AppSource übermittelten Apps müssen diese Werte mit den Informationen in Ihrem Eintrag "AppSource" übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="bd65c-173">For apps submitted to AppSource, these values must match the information in your AppSource entry.</span></span>

<span data-ttu-id="bd65c-174">Stellen Sie sicher, dass Ihre Beschreibung Ihre Erfahrung genau beschreibt und Informationen liefert, die potenziellen Kunden helfen, ihre Erfahrung zu verstehen.</span><span class="sxs-lookup"><span data-stu-id="bd65c-174">Ensure that your description accurately describes your experience and provides information to help potential customers understand what your experience does.</span></span> <span data-ttu-id="bd65c-175">Beachten Sie auch in der vollständigen Beschreibung, ob ein externes Konto für die Verwendung erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="bd65c-175">You should also note, in the full description, if an external account is required for use.</span></span> <span data-ttu-id="bd65c-176">Die Werte von `short` und sollten nicht identisch `full` sein.</span><span class="sxs-lookup"><span data-stu-id="bd65c-176">The values of `short` and `full` should not be the same.</span></span>  <span data-ttu-id="bd65c-177">Ihre kurze Beschreibung darf nicht innerhalb der langen Beschreibung wiederholt werden und darf keinen anderen App-Namen enthalten.</span><span class="sxs-lookup"><span data-stu-id="bd65c-177">Your short description must not be repeated within the long description and must not include any other app name.</span></span>

|<span data-ttu-id="bd65c-178">Name</span><span class="sxs-lookup"><span data-stu-id="bd65c-178">Name</span></span>| <span data-ttu-id="bd65c-179">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="bd65c-179">Maximum size</span></span> | <span data-ttu-id="bd65c-180">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="bd65c-180">Required</span></span> | <span data-ttu-id="bd65c-181">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="bd65c-181">Description</span></span>|
|---|---|---|---|
|`short`|<span data-ttu-id="bd65c-182">80 Zeichen</span><span class="sxs-lookup"><span data-stu-id="bd65c-182">80 characters</span></span>|<span data-ttu-id="bd65c-183">✔</span><span class="sxs-lookup"><span data-stu-id="bd65c-183">✔</span></span>|<span data-ttu-id="bd65c-184">Eine kurze Beschreibung Ihrer App-Erfahrung, die bei begrenztem Speicherplatz verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="bd65c-184">A short description of your app experience, used when space is limited.</span></span>|
|`full`|<span data-ttu-id="bd65c-185">4000 Zeichen</span><span class="sxs-lookup"><span data-stu-id="bd65c-185">4000 characters</span></span>|<span data-ttu-id="bd65c-186">✔</span><span class="sxs-lookup"><span data-stu-id="bd65c-186">✔</span></span>|<span data-ttu-id="bd65c-187">Die vollständige Beschreibung Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="bd65c-187">The full description of your app.</span></span>|

## <a name="packagename"></a><span data-ttu-id="bd65c-188">packageName</span><span class="sxs-lookup"><span data-stu-id="bd65c-188">packageName</span></span>

<span data-ttu-id="bd65c-189">**Optional –** Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="bd65c-189">**Optional** — string</span></span>

<span data-ttu-id="bd65c-190">Ein eindeutiger Bezeichner für diese App in umgekehrter Domänen-Notation; Beispiel: com.example.myapp.</span><span class="sxs-lookup"><span data-stu-id="bd65c-190">A unique identifier for this app in reverse domain notation; for example, com.example.myapp.</span></span> <span data-ttu-id="bd65c-191">Maximale Länge: 64 Zeichen.</span><span class="sxs-lookup"><span data-stu-id="bd65c-191">Maximum length: 64 characters.</span></span>

## <a name="localizationinfo"></a><span data-ttu-id="bd65c-192">localizationInfo</span><span class="sxs-lookup"><span data-stu-id="bd65c-192">localizationInfo</span></span>

<span data-ttu-id="bd65c-193">**Optional** – Objekt</span><span class="sxs-lookup"><span data-stu-id="bd65c-193">**Optional** — object</span></span>

<span data-ttu-id="bd65c-194">Ermöglicht die Angabe einer Standardsprache sowie Zeiger auf zusätzliche Sprachdateien.</span><span class="sxs-lookup"><span data-stu-id="bd65c-194">Allows the specification of a default language, as well as pointers to additional language files.</span></span> <span data-ttu-id="bd65c-195">Siehe [Lokalisierung](~/concepts/build-and-test/apps-localization.md).</span><span class="sxs-lookup"><span data-stu-id="bd65c-195">See [localization](~/concepts/build-and-test/apps-localization.md).</span></span>

|<span data-ttu-id="bd65c-196">Name</span><span class="sxs-lookup"><span data-stu-id="bd65c-196">Name</span></span>| <span data-ttu-id="bd65c-197">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="bd65c-197">Maximum size</span></span> | <span data-ttu-id="bd65c-198">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="bd65c-198">Required</span></span> | <span data-ttu-id="bd65c-199">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="bd65c-199">Description</span></span>|
|---|---|---|---|
|`defaultLanguageTag`||<span data-ttu-id="bd65c-200">✔</span><span class="sxs-lookup"><span data-stu-id="bd65c-200">✔</span></span>|<span data-ttu-id="bd65c-201">Das Sprachtag der Zeichenfolgen in dieser Manifestdatei der obersten Ebene.</span><span class="sxs-lookup"><span data-stu-id="bd65c-201">The language tag of the strings in this top level manifest file.</span></span>|

### <a name="localizationinfoadditionallanguages"></a><span data-ttu-id="bd65c-202">localizationInfo.additionalLanguages</span><span class="sxs-lookup"><span data-stu-id="bd65c-202">localizationInfo.additionalLanguages</span></span>

<span data-ttu-id="bd65c-203">Ein Array von Objekten, die zusätzliche Sprachübersetzungen angeben.</span><span class="sxs-lookup"><span data-stu-id="bd65c-203">An array of objects specifying additional language translations.</span></span>

|<span data-ttu-id="bd65c-204">Name</span><span class="sxs-lookup"><span data-stu-id="bd65c-204">Name</span></span>| <span data-ttu-id="bd65c-205">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="bd65c-205">Maximum size</span></span> | <span data-ttu-id="bd65c-206">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="bd65c-206">Required</span></span> | <span data-ttu-id="bd65c-207">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="bd65c-207">Description</span></span>|
|---|---|---|---|
|`languageTag`||<span data-ttu-id="bd65c-208">✔</span><span class="sxs-lookup"><span data-stu-id="bd65c-208">✔</span></span>|<span data-ttu-id="bd65c-209">Das Sprachtag der Zeichenfolgen in der bereitgestellten Datei.</span><span class="sxs-lookup"><span data-stu-id="bd65c-209">The language tag of the strings in the provided file.</span></span>|
|`file`||<span data-ttu-id="bd65c-210">✔</span><span class="sxs-lookup"><span data-stu-id="bd65c-210">✔</span></span>|<span data-ttu-id="bd65c-211">Ein relativer Dateipfad zu einer JSON-Datei, die die übersetzten Zeichenfolgen enthält.</span><span class="sxs-lookup"><span data-stu-id="bd65c-211">A relative file path to a the .json file containing the translated strings.</span></span>|

## <a name="icons"></a><span data-ttu-id="bd65c-212">Symbole</span><span class="sxs-lookup"><span data-stu-id="bd65c-212">icons</span></span>

<span data-ttu-id="bd65c-213">**Erforderlich** – Objekt</span><span class="sxs-lookup"><span data-stu-id="bd65c-213">**Required** — object</span></span>

<span data-ttu-id="bd65c-214">Symbole, die in der Teams-App verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="bd65c-214">Icons used within the Teams app.</span></span> <span data-ttu-id="bd65c-215">Die Symboldateien müssen als Teil des Uploadpakets enthalten sein.</span><span class="sxs-lookup"><span data-stu-id="bd65c-215">The icon files must be included as part of the upload package.</span></span> <span data-ttu-id="bd65c-216">Weitere [Informationen finden Sie](../../concepts/build-and-test/apps-package.md#app-icons) unter "Symbole".</span><span class="sxs-lookup"><span data-stu-id="bd65c-216">See [Icons](../../concepts/build-and-test/apps-package.md#app-icons) for more information.</span></span>

|<span data-ttu-id="bd65c-217">Name</span><span class="sxs-lookup"><span data-stu-id="bd65c-217">Name</span></span>| <span data-ttu-id="bd65c-218">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="bd65c-218">Maximum size</span></span> | <span data-ttu-id="bd65c-219">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="bd65c-219">Required</span></span> | <span data-ttu-id="bd65c-220">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="bd65c-220">Description</span></span>|
|---|---|---|---|
|`outline`|<span data-ttu-id="bd65c-221">32 x 32 Pixel</span><span class="sxs-lookup"><span data-stu-id="bd65c-221">32 x 32 pixels</span></span>|<span data-ttu-id="bd65c-222">✔</span><span class="sxs-lookup"><span data-stu-id="bd65c-222">✔</span></span>|<span data-ttu-id="bd65c-223">Ein relativer Dateipfad zu einem transparenten 32 x 32 PNG-Gliederungssymbol.</span><span class="sxs-lookup"><span data-stu-id="bd65c-223">A relative file path to a transparent 32x32 PNG outline icon.</span></span>|
|`color`|<span data-ttu-id="bd65c-224">192 x 192 Pixel</span><span class="sxs-lookup"><span data-stu-id="bd65c-224">192 x 192 pixels</span></span>|<span data-ttu-id="bd65c-225">✔</span><span class="sxs-lookup"><span data-stu-id="bd65c-225">✔</span></span>|<span data-ttu-id="bd65c-226">Ein relativer Dateipfad zu einem vollfarbigen 192 x 192 PNG-Symbol.</span><span class="sxs-lookup"><span data-stu-id="bd65c-226">A relative file path to a full color 192x192 PNG icon.</span></span>|

## <a name="accentcolor"></a><span data-ttu-id="bd65c-227">accentColor</span><span class="sxs-lookup"><span data-stu-id="bd65c-227">accentColor</span></span>

<span data-ttu-id="bd65c-228">**Optional** – HTML Hex-Farbcode</span><span class="sxs-lookup"><span data-stu-id="bd65c-228">**Optional** — HTML Hex color code</span></span>

<span data-ttu-id="bd65c-229">Eine Farbe, die in Verbindung mit und als Hintergrund für Ihre Gliederungssymbole verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="bd65c-229">A color to use in conjunction with and as a background for your outline icons.</span></span>

<span data-ttu-id="bd65c-230">Der Wert muss ein gültiger #A0 sein, der mit "#" beginnt, z. B. `#4464ee` .</span><span class="sxs-lookup"><span data-stu-id="bd65c-230">The value must be a valid HTML color code starting with '#', for example `#4464ee`.</span></span>

## <a name="configurabletabs"></a><span data-ttu-id="bd65c-231">configurableTabs</span><span class="sxs-lookup"><span data-stu-id="bd65c-231">configurableTabs</span></span>

<span data-ttu-id="bd65c-232">**Optional** – Array</span><span class="sxs-lookup"><span data-stu-id="bd65c-232">**Optional** — array</span></span>

<span data-ttu-id="bd65c-233">Wird verwendet, wenn Ihre App über eine Registerkartenerfahrung im Teamkanal verfügt, die eine zusätzliche Konfiguration erfordert, bevor sie hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="bd65c-233">Used when your app experience has a team channel tab experience that requires extra configuration before it is added.</span></span> <span data-ttu-id="bd65c-234">Konfigurierbare Registerkarten werden nur im Teambereich unterstützt (nicht persönlich), und derzeit wird nur eine Registerkarte pro App unterstützt. </span><span class="sxs-lookup"><span data-stu-id="bd65c-234">Configurable tabs are supported only in the teams scope (not personal), and currently only **one** tab per app is supported.</span></span>

|<span data-ttu-id="bd65c-235">Name</span><span class="sxs-lookup"><span data-stu-id="bd65c-235">Name</span></span>| <span data-ttu-id="bd65c-236">Typ</span><span class="sxs-lookup"><span data-stu-id="bd65c-236">Type</span></span>| <span data-ttu-id="bd65c-237">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="bd65c-237">Maximum size</span></span> | <span data-ttu-id="bd65c-238">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="bd65c-238">Required</span></span> | <span data-ttu-id="bd65c-239">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="bd65c-239">Description</span></span>|
|---|---|---|---|---|
|`configurationUrl`|<span data-ttu-id="bd65c-240">string</span><span class="sxs-lookup"><span data-stu-id="bd65c-240">string</span></span>|<span data-ttu-id="bd65c-241">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="bd65c-241">2048 characters</span></span>|<span data-ttu-id="bd65c-242">✔</span><span class="sxs-lookup"><span data-stu-id="bd65c-242">✔</span></span>|<span data-ttu-id="bd65c-243">Die https:// URL, die beim Konfigurieren der Registerkarte verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="bd65c-243">The https:// URL to use when configuring the tab.</span></span>|
|`scopes`|<span data-ttu-id="bd65c-244">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="bd65c-244">array of enums</span></span>|<span data-ttu-id="bd65c-245">1 </span><span class="sxs-lookup"><span data-stu-id="bd65c-245">1</span></span>|<span data-ttu-id="bd65c-246">✔</span><span class="sxs-lookup"><span data-stu-id="bd65c-246">✔</span></span>|<span data-ttu-id="bd65c-247">Derzeit unterstützen konfigurierbare Registerkarten nur die `team` `groupchat` Bereiche.</span><span class="sxs-lookup"><span data-stu-id="bd65c-247">Currently, configurable tabs support only the `team` and `groupchat` scopes.</span></span> |
|`canUpdateConfiguration`|<span data-ttu-id="bd65c-248">Boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="bd65c-248">boolean</span></span>|||<span data-ttu-id="bd65c-249">Ein Wert, der angibt, ob eine Instanz der Konfiguration der Registerkarte vom Benutzer nach der Erstellung aktualisiert werden kann.</span><span class="sxs-lookup"><span data-stu-id="bd65c-249">A value indicating whether an instance of the tab's configuration can be updated by the user after creation.</span></span> <span data-ttu-id="bd65c-250">Standard: **true**.</span><span class="sxs-lookup"><span data-stu-id="bd65c-250">Default: **true**.</span></span>|
|`context` |<span data-ttu-id="bd65c-251">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="bd65c-251">array of enums</span></span>|<span data-ttu-id="bd65c-252">6 </span><span class="sxs-lookup"><span data-stu-id="bd65c-252">6</span></span>||<span data-ttu-id="bd65c-253">Der `contextItem` Bereich, für den eine Registerkarte unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="bd65c-253">The set of `contextItem` scopes where a tab is supported.</span></span> <span data-ttu-id="bd65c-254">Standard: **[channelTab, privateChatTab, meetingChatTab, meetingDetailsTab]**.</span><span class="sxs-lookup"><span data-stu-id="bd65c-254">Default: **[channelTab, privateChatTab, meetingChatTab, meetingDetailsTab]**.</span></span>|
|`sharePointPreviewImage`|<span data-ttu-id="bd65c-255">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="bd65c-255">string</span></span>|<span data-ttu-id="bd65c-256">2048</span><span class="sxs-lookup"><span data-stu-id="bd65c-256">2048</span></span>||<span data-ttu-id="bd65c-257">Ein relativer Dateipfad zu einem Vorschaubild der Registerkarte für die Verwendung in SharePoint.</span><span class="sxs-lookup"><span data-stu-id="bd65c-257">A relative file path to a tab preview image for use in SharePoint.</span></span> <span data-ttu-id="bd65c-258">Größe 1024 x 768.</span><span class="sxs-lookup"><span data-stu-id="bd65c-258">Size 1024x768.</span></span> |
|`supportedSharePointHosts`|<span data-ttu-id="bd65c-259">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="bd65c-259">array of enums</span></span>|<span data-ttu-id="bd65c-260">1 </span><span class="sxs-lookup"><span data-stu-id="bd65c-260">1</span></span>||<span data-ttu-id="bd65c-261">Definiert, wie Ihre Registerkarte in SharePoint verfügbar gemacht wird.</span><span class="sxs-lookup"><span data-stu-id="bd65c-261">Defines how your tab will be made available in SharePoint.</span></span> <span data-ttu-id="bd65c-262">Optionen sind `sharePointFullPage` und `sharePointWebPart`</span><span class="sxs-lookup"><span data-stu-id="bd65c-262">Options are `sharePointFullPage` and `sharePointWebPart`</span></span> |

## <a name="statictabs"></a><span data-ttu-id="bd65c-263">staticTabs</span><span class="sxs-lookup"><span data-stu-id="bd65c-263">staticTabs</span></span>

<span data-ttu-id="bd65c-264">**Optional** – Array</span><span class="sxs-lookup"><span data-stu-id="bd65c-264">**Optional** — array</span></span>

<span data-ttu-id="bd65c-265">Definiert eine Reihe von Registerkarten, die standardmäßig "angeheftet" werden können, ohne dass sie vom Benutzer manuell hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="bd65c-265">Defines a set of tabs that can be "pinned" by default, without the user adding them manually.</span></span> <span data-ttu-id="bd65c-266">Statische Registerkarten, die im Bereich deklariert sind, werden immer an die persönliche Benutzererfahrung `personal` der App angeheftet.</span><span class="sxs-lookup"><span data-stu-id="bd65c-266">Static tabs declared in `personal` scope are always pinned to the app's personal experience.</span></span> <span data-ttu-id="bd65c-267">Im Bereich deklarierte statische `team` Registerkarten werden derzeit nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="bd65c-267">Static tabs declared in the `team` scope are currently not supported.</span></span>

<span data-ttu-id="bd65c-268">Dieses Element ist ein Array (maximal 16 Elemente) mit allen Elementen des Typs `object` .</span><span class="sxs-lookup"><span data-stu-id="bd65c-268">This item is an array (maximum of 16 elements) with all elements of the type `object`.</span></span> <span data-ttu-id="bd65c-269">Dieser Block ist nur für Lösungen erforderlich, die eine Lösung für statische Registerkarten bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="bd65c-269">This block is required only for solutions that provide a static tab solution.</span></span>

|<span data-ttu-id="bd65c-270">Name</span><span class="sxs-lookup"><span data-stu-id="bd65c-270">Name</span></span>| <span data-ttu-id="bd65c-271">Typ</span><span class="sxs-lookup"><span data-stu-id="bd65c-271">Type</span></span>| <span data-ttu-id="bd65c-272">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="bd65c-272">Maximum size</span></span> | <span data-ttu-id="bd65c-273">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="bd65c-273">Required</span></span> | <span data-ttu-id="bd65c-274">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="bd65c-274">Description</span></span>|
|---|---|---|---|---|
|`entityId`|<span data-ttu-id="bd65c-275">string</span><span class="sxs-lookup"><span data-stu-id="bd65c-275">string</span></span>|<span data-ttu-id="bd65c-276">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="bd65c-276">64 characters</span></span>|<span data-ttu-id="bd65c-277">✔</span><span class="sxs-lookup"><span data-stu-id="bd65c-277">✔</span></span>|<span data-ttu-id="bd65c-278">Ein eindeutiger Bezeichner für die Entität, die auf der Registerkarte angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="bd65c-278">A unique identifier for the entity that the tab displays.</span></span>|
|`name`|<span data-ttu-id="bd65c-279">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="bd65c-279">string</span></span>|<span data-ttu-id="bd65c-280">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="bd65c-280">128 characters</span></span>|<span data-ttu-id="bd65c-281">✔</span><span class="sxs-lookup"><span data-stu-id="bd65c-281">✔</span></span>|<span data-ttu-id="bd65c-282">Der Anzeigename der Registerkarte in der Kanalschnittstelle.</span><span class="sxs-lookup"><span data-stu-id="bd65c-282">The display name of the tab in the channel interface.</span></span>|
|`contentUrl`|<span data-ttu-id="bd65c-283">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="bd65c-283">string</span></span>||<span data-ttu-id="bd65c-284">✔</span><span class="sxs-lookup"><span data-stu-id="bd65c-284">✔</span></span>|<span data-ttu-id="bd65c-285">Die https:// URL, die auf die Entitätsbenutzeroberfläche verweist, die im Zeichenbereich von Teams angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="bd65c-285">The https:// URL that points to the entity UI to be displayed in the Teams canvas.</span></span>|
|`websiteUrl`|<span data-ttu-id="bd65c-286">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="bd65c-286">string</span></span>|||<span data-ttu-id="bd65c-287">Die https:// URL, auf die verweisen soll, wenn ein Benutzer die Anzeige in einem Browser anmeldet.</span><span class="sxs-lookup"><span data-stu-id="bd65c-287">The https:// URL to point to if a user opts to view in a browser.</span></span>|
|`searchUrl`|<span data-ttu-id="bd65c-288">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="bd65c-288">string</span></span>|||<span data-ttu-id="bd65c-289">Die https:// URL, auf die auf die Suchabfragen eines Benutzers verweisen soll.</span><span class="sxs-lookup"><span data-stu-id="bd65c-289">The https:// URL to point to for a user's search queries.</span></span>|
|`scopes`|<span data-ttu-id="bd65c-290">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="bd65c-290">array of enums</span></span>|<span data-ttu-id="bd65c-291">1 </span><span class="sxs-lookup"><span data-stu-id="bd65c-291">1</span></span>|<span data-ttu-id="bd65c-292">✔</span><span class="sxs-lookup"><span data-stu-id="bd65c-292">✔</span></span>|<span data-ttu-id="bd65c-293">Derzeit unterstützen statische Registerkarten nur den Bereich, d. h., er kann nur als Teil der `personal` persönlichen Erfahrung bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="bd65c-293">Currently, static tabs support only the `personal` scope, which means it can be provisioned only as part of the personal experience.</span></span>|
|`context` | <span data-ttu-id="bd65c-294">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="bd65c-294">array of enums</span></span>| <span data-ttu-id="bd65c-295">2 </span><span class="sxs-lookup"><span data-stu-id="bd65c-295">2</span></span>|| <span data-ttu-id="bd65c-296">Der `contextItem` Bereich, für den eine Registerkarte unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="bd65c-296">The set of `contextItem` scopes where a tab is supported.</span></span>|

> [!NOTE]
> <span data-ttu-id="bd65c-297">Wenn Ihre Registerkarten kontextabhängige Informationen zum Anzeigen relevanter Inhalte oder zum Initiieren eines Authentifizierungsflusses *benötigen,* finden Sie weitere Informationen unter Kontext für Ihre [Registerkarte "Microsoft Teams".](../../tabs/how-to/access-teams-context.md)</span><span class="sxs-lookup"><span data-stu-id="bd65c-297">If your tabs require context-dependent information to display relevant content or for initiating an authentication flow, *see* [Get context for your Microsoft Teams tab](../../tabs/how-to/access-teams-context.md).</span></span>

## <a name="bots"></a><span data-ttu-id="bd65c-298">Bots</span><span class="sxs-lookup"><span data-stu-id="bd65c-298">bots</span></span>

<span data-ttu-id="bd65c-299">**Optional** – Array</span><span class="sxs-lookup"><span data-stu-id="bd65c-299">**Optional** — array</span></span>

<span data-ttu-id="bd65c-300">Definiert eine Botlösung zusammen mit optionalen Informationen wie z. B. Standardbefehlseigenschaften.</span><span class="sxs-lookup"><span data-stu-id="bd65c-300">Defines a bot solution, along with optional information such as default command properties.</span></span>

<span data-ttu-id="bd65c-301">Das Element ist ein Array (maximal 1 Element ist derzeit nur ein Bot pro App zulässig) mit allen Elementen &mdash; des Typs `object` .</span><span class="sxs-lookup"><span data-stu-id="bd65c-301">The item is an array (maximum of only 1 element&mdash;currently only one bot is allowed per app) with all elements of the type `object`.</span></span> <span data-ttu-id="bd65c-302">Dieser Block ist nur für Lösungen erforderlich, die eine Boterfahrung bieten.</span><span class="sxs-lookup"><span data-stu-id="bd65c-302">This block is required only for solutions that provide a bot experience.</span></span>

|<span data-ttu-id="bd65c-303">Name</span><span class="sxs-lookup"><span data-stu-id="bd65c-303">Name</span></span>| <span data-ttu-id="bd65c-304">Typ</span><span class="sxs-lookup"><span data-stu-id="bd65c-304">Type</span></span>| <span data-ttu-id="bd65c-305">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="bd65c-305">Maximum size</span></span> | <span data-ttu-id="bd65c-306">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="bd65c-306">Required</span></span> | <span data-ttu-id="bd65c-307">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="bd65c-307">Description</span></span>|
|---|---|---|---|---|
|`botId`|<span data-ttu-id="bd65c-308">string</span><span class="sxs-lookup"><span data-stu-id="bd65c-308">string</span></span>|<span data-ttu-id="bd65c-309">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="bd65c-309">64 characters</span></span>|<span data-ttu-id="bd65c-310">✔</span><span class="sxs-lookup"><span data-stu-id="bd65c-310">✔</span></span>|<span data-ttu-id="bd65c-311">Die eindeutige Microsoft-App-ID für den Bot, wie bei Bot Framework registriert.</span><span class="sxs-lookup"><span data-stu-id="bd65c-311">The unique Microsoft app ID for the bot as registered with the Bot Framework.</span></span> <span data-ttu-id="bd65c-312">Dies kann mit der allgemeinen [App-ID identisch sein.](#id)</span><span class="sxs-lookup"><span data-stu-id="bd65c-312">This may well be the same as the overall [app ID](#id).</span></span>|
|`scopes`|<span data-ttu-id="bd65c-313">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="bd65c-313">array of enums</span></span>|<span data-ttu-id="bd65c-314">3</span><span class="sxs-lookup"><span data-stu-id="bd65c-314">3</span></span>|<span data-ttu-id="bd65c-315">✔</span><span class="sxs-lookup"><span data-stu-id="bd65c-315">✔</span></span>|<span data-ttu-id="bd65c-316">Gibt an, ob der Bot eine Umgebung im Kontext eines Kanals in einem `team` oder Gruppenchat (`groupchat`) ist, oder aber eine Umgebung einzig für einen bestimmten Benutzer (`personal`).</span><span class="sxs-lookup"><span data-stu-id="bd65c-316">Specifies whether the bot offers an experience in the context of a channel in a `team`, in a group chat (`groupchat`), or an experience scoped to an individual user alone (`personal`).</span></span> <span data-ttu-id="bd65c-317">Diese Optionen sind nicht exklusiv.</span><span class="sxs-lookup"><span data-stu-id="bd65c-317">These options are non-exclusive.</span></span>|
|`needsChannelSelector`|<span data-ttu-id="bd65c-318">Boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="bd65c-318">boolean</span></span>|||<span data-ttu-id="bd65c-319">Beschreibt, ob der Bot einen Benutzerhinweis verwendet, um den Bot einem bestimmten Kanal hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="bd65c-319">Describes whether or not the bot utilizes a user hint to add the bot to a specific channel.</span></span> <span data-ttu-id="bd65c-320">Standard: **`false`**</span><span class="sxs-lookup"><span data-stu-id="bd65c-320">Default: **`false`**</span></span>|
|`isNotificationOnly`|<span data-ttu-id="bd65c-321">Boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="bd65c-321">boolean</span></span>|||<span data-ttu-id="bd65c-322">Gibt an, ob ein Bot ein unidirektionaler Bot ausschließlich für Benachrichtigungen ist (im Gegensatz zu einem dialogorientierten Bot).</span><span class="sxs-lookup"><span data-stu-id="bd65c-322">Indicates whether a bot is a one-way, notification-only bot, as opposed to a conversational bot.</span></span> <span data-ttu-id="bd65c-323">Standard: **`false`**</span><span class="sxs-lookup"><span data-stu-id="bd65c-323">Default: **`false`**</span></span>|
|`supportsFiles`|<span data-ttu-id="bd65c-324">Boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="bd65c-324">boolean</span></span>|||<span data-ttu-id="bd65c-325">Gibt an, ob der Bot die Möglichkeit zum Hochladen/Herunterladen von Dateien in persönliche Chats unterstützt.</span><span class="sxs-lookup"><span data-stu-id="bd65c-325">Indicates whether the bot supports the ability to upload/download files in personal chat.</span></span> <span data-ttu-id="bd65c-326">Standard: **`false`**</span><span class="sxs-lookup"><span data-stu-id="bd65c-326">Default: **`false`**</span></span>|
|`supportsCalling`|<span data-ttu-id="bd65c-327">Boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="bd65c-327">boolean</span></span>|||<span data-ttu-id="bd65c-328">Ein Wert, der angibt, wo ein Bot Audioanrufe unterstützt.</span><span class="sxs-lookup"><span data-stu-id="bd65c-328">A value indicating where a bot supports audio calling.</span></span> <span data-ttu-id="bd65c-329">**WICHTIG:** Diese Eigenschaft ist derzeit experimentell.</span><span class="sxs-lookup"><span data-stu-id="bd65c-329">**IMPORTANT**: This property is currently experimental.</span></span> <span data-ttu-id="bd65c-330">Experimentelle Eigenschaften sind möglicherweise nicht vollständig und werden möglicherweise geändert, bevor sie vollständig verfügbar werden.</span><span class="sxs-lookup"><span data-stu-id="bd65c-330">Experimental properties may not be complete, and may undergo changes before becoming fully available.</span></span>  <span data-ttu-id="bd65c-331">Es wird nur zu Test- und Untersuchungszwecken bereitgestellt und sollte nicht in Produktionsanwendungen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="bd65c-331">It is provided for testing and exploration purposes only and should not be used in production applications.</span></span> <span data-ttu-id="bd65c-332">Standard: **`false`**</span><span class="sxs-lookup"><span data-stu-id="bd65c-332">Default: **`false`**</span></span>|
|`supportsVideo`|<span data-ttu-id="bd65c-333">Boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="bd65c-333">boolean</span></span>|||<span data-ttu-id="bd65c-334">Ein Wert, der angibt, wo ein Bot Videoanrufe unterstützt.</span><span class="sxs-lookup"><span data-stu-id="bd65c-334">A value indicating where a bot supports video calling.</span></span> <span data-ttu-id="bd65c-335">**WICHTIG:** Diese Eigenschaft ist derzeit experimentell.</span><span class="sxs-lookup"><span data-stu-id="bd65c-335">**IMPORTANT**: This property is currently experimental.</span></span> <span data-ttu-id="bd65c-336">Experimentelle Eigenschaften sind möglicherweise nicht vollständig und werden möglicherweise geändert, bevor sie vollständig verfügbar werden.</span><span class="sxs-lookup"><span data-stu-id="bd65c-336">Experimental properties may not be complete, and may undergo changes before becoming fully available.</span></span>  <span data-ttu-id="bd65c-337">Es wird nur zu Test- und Untersuchungszwecken bereitgestellt und sollte nicht in Produktionsanwendungen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="bd65c-337">It is provided for testing and exploration purposes only and should not be used in production applications.</span></span> <span data-ttu-id="bd65c-338">Standard: **`false`**</span><span class="sxs-lookup"><span data-stu-id="bd65c-338">Default: **`false`**</span></span>|

### <a name="botscommandlists"></a><span data-ttu-id="bd65c-339">bots.commandLists</span><span class="sxs-lookup"><span data-stu-id="bd65c-339">bots.commandLists</span></span>

<span data-ttu-id="bd65c-340">Eine optionale Liste von Befehlen, die Ihr Bot Benutzern empfehlen kann.</span><span class="sxs-lookup"><span data-stu-id="bd65c-340">An optional list of commands that your bot can recommend to users.</span></span> <span data-ttu-id="bd65c-341">Das Objekt ist ein Array (maximal 2 Elemente) mit allen Elementen des Typs; Sie müssen eine separate Befehlsliste für jeden Bereich definieren, der von `object` Ihrem Bot unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="bd65c-341">The object is an array (maximum of 2 elements) with all elements of type `object`; you must define a separate command list for each scope that your bot supports.</span></span> <span data-ttu-id="bd65c-342">Weitere [Informationen finden Sie in den Bot-Menüs.](~/bots/how-to/create-a-bot-commands-menu.md)</span><span class="sxs-lookup"><span data-stu-id="bd65c-342">See [Bot menus](~/bots/how-to/create-a-bot-commands-menu.md) for more information.</span></span>

|<span data-ttu-id="bd65c-343">Name</span><span class="sxs-lookup"><span data-stu-id="bd65c-343">Name</span></span>| <span data-ttu-id="bd65c-344">Typ</span><span class="sxs-lookup"><span data-stu-id="bd65c-344">Type</span></span>| <span data-ttu-id="bd65c-345">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="bd65c-345">Maximum size</span></span> | <span data-ttu-id="bd65c-346">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="bd65c-346">Required</span></span> | <span data-ttu-id="bd65c-347">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="bd65c-347">Description</span></span>|
|---|---|---|---|---|
|`items.scopes`|<span data-ttu-id="bd65c-348">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="bd65c-348">array of enums</span></span>|<span data-ttu-id="bd65c-349">3</span><span class="sxs-lookup"><span data-stu-id="bd65c-349">3</span></span>|<span data-ttu-id="bd65c-350">✔</span><span class="sxs-lookup"><span data-stu-id="bd65c-350">✔</span></span>|<span data-ttu-id="bd65c-351">Gibt den Bereich an, für den die Befehlsliste gültig ist.</span><span class="sxs-lookup"><span data-stu-id="bd65c-351">Specifies the scope for which the command list is valid.</span></span> <span data-ttu-id="bd65c-352">Mögliche Optionen sind `team`, `personal` und `groupchat`.</span><span class="sxs-lookup"><span data-stu-id="bd65c-352">Options are `team`, `personal`, and `groupchat`.</span></span>|
|`items.commands`|<span data-ttu-id="bd65c-353">Array von Objekten</span><span class="sxs-lookup"><span data-stu-id="bd65c-353">array of objects</span></span>|<span data-ttu-id="bd65c-354">10 </span><span class="sxs-lookup"><span data-stu-id="bd65c-354">10</span></span>|<span data-ttu-id="bd65c-355">✔</span><span class="sxs-lookup"><span data-stu-id="bd65c-355">✔</span></span>|<span data-ttu-id="bd65c-356">Ein Array von Befehlen, die der Bot unterstützt:</span><span class="sxs-lookup"><span data-stu-id="bd65c-356">An array of commands the bot supports:</span></span><br><span data-ttu-id="bd65c-357">`title`: Name des Bot-Befehls (string, 32)</span><span class="sxs-lookup"><span data-stu-id="bd65c-357">`title`: the bot command name (string, 32)</span></span><br><span data-ttu-id="bd65c-358">`description`: einfache Beschreibung oder Beispiel für die Befehlssyntax und zugehörige Argumente (string, 128)</span><span class="sxs-lookup"><span data-stu-id="bd65c-358">`description`: a simple description or example of the command syntax and its argument (string, 128)</span></span>|

### <a name="botscommandlistscommands"></a><span data-ttu-id="bd65c-359">bots.commandLists.commands</span><span class="sxs-lookup"><span data-stu-id="bd65c-359">bots.commandLists.commands</span></span>

|<span data-ttu-id="bd65c-360">Name</span><span class="sxs-lookup"><span data-stu-id="bd65c-360">Name</span></span>| <span data-ttu-id="bd65c-361">Typ</span><span class="sxs-lookup"><span data-stu-id="bd65c-361">Type</span></span>| <span data-ttu-id="bd65c-362">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="bd65c-362">Maximum size</span></span> | <span data-ttu-id="bd65c-363">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="bd65c-363">Required</span></span> | <span data-ttu-id="bd65c-364">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="bd65c-364">Description</span></span>|
|---|---|---|---|---|
|<span data-ttu-id="bd65c-365">title</span><span class="sxs-lookup"><span data-stu-id="bd65c-365">title</span></span>|<span data-ttu-id="bd65c-366">string</span><span class="sxs-lookup"><span data-stu-id="bd65c-366">string</span></span>|<span data-ttu-id="bd65c-367">12 </span><span class="sxs-lookup"><span data-stu-id="bd65c-367">12</span></span>|<span data-ttu-id="bd65c-368">✔</span><span class="sxs-lookup"><span data-stu-id="bd65c-368">✔</span></span>|<span data-ttu-id="bd65c-369">Der Name des Botbefehls</span><span class="sxs-lookup"><span data-stu-id="bd65c-369">The bot command name</span></span>|
|<span data-ttu-id="bd65c-370">description</span><span class="sxs-lookup"><span data-stu-id="bd65c-370">description</span></span>|<span data-ttu-id="bd65c-371">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="bd65c-371">string</span></span>|<span data-ttu-id="bd65c-372">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="bd65c-372">128 characters</span></span>|<span data-ttu-id="bd65c-373">✔</span><span class="sxs-lookup"><span data-stu-id="bd65c-373">✔</span></span>|<span data-ttu-id="bd65c-374">Eine einfache Textbeschreibung oder ein Beispiel für die Befehlssyntax und deren Argumente.</span><span class="sxs-lookup"><span data-stu-id="bd65c-374">A simple text description or an example of the command syntax and its arguments.</span></span>|

## <a name="connectors"></a><span data-ttu-id="bd65c-375">Connectors</span><span class="sxs-lookup"><span data-stu-id="bd65c-375">connectors</span></span>

<span data-ttu-id="bd65c-376">**Optional** – Array</span><span class="sxs-lookup"><span data-stu-id="bd65c-376">**Optional** — array</span></span>

<span data-ttu-id="bd65c-377">Der `connectors` Block definiert einen Office 365-Connector für die App.</span><span class="sxs-lookup"><span data-stu-id="bd65c-377">The `connectors` block defines an Office 365 Connector for the app.</span></span>

<span data-ttu-id="bd65c-378">Das Objekt ist ein Array (maximal 1 Element) mit allen Elementen vom `object` Typ .</span><span class="sxs-lookup"><span data-stu-id="bd65c-378">The object is an array (maximum of 1 element) with all elements of type `object`.</span></span> <span data-ttu-id="bd65c-379">Dieser Block ist nur für Lösungen erforderlich, die einen Connector bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="bd65c-379">This block is required only for solutions that provide a Connector.</span></span>

|<span data-ttu-id="bd65c-380">Name</span><span class="sxs-lookup"><span data-stu-id="bd65c-380">Name</span></span>| <span data-ttu-id="bd65c-381">Typ</span><span class="sxs-lookup"><span data-stu-id="bd65c-381">Type</span></span>| <span data-ttu-id="bd65c-382">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="bd65c-382">Maximum size</span></span> | <span data-ttu-id="bd65c-383">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="bd65c-383">Required</span></span> | <span data-ttu-id="bd65c-384">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="bd65c-384">Description</span></span>|
|---|---|---|---|---|
|`configurationUrl`|<span data-ttu-id="bd65c-385">string</span><span class="sxs-lookup"><span data-stu-id="bd65c-385">string</span></span>|<span data-ttu-id="bd65c-386">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="bd65c-386">2048 characters</span></span>|<span data-ttu-id="bd65c-387">✔</span><span class="sxs-lookup"><span data-stu-id="bd65c-387">✔</span></span>|<span data-ttu-id="bd65c-388">Die https:// URL, die beim Konfigurieren des Connectors verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="bd65c-388">The https:// URL to use when configuring the connector.</span></span>|
|`scopes`|<span data-ttu-id="bd65c-389">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="bd65c-389">array of enums</span></span>|<span data-ttu-id="bd65c-390">1 </span><span class="sxs-lookup"><span data-stu-id="bd65c-390">1</span></span>|<span data-ttu-id="bd65c-391">✔</span><span class="sxs-lookup"><span data-stu-id="bd65c-391">✔</span></span>|<span data-ttu-id="bd65c-392">Gibt an, ob der Connector eine Benutzeroberfläche im Kontext eines Kanals in einem oder eine Benutzeroberfläche bietet, die auf einen einzelnen Benutzer `team` begrenzt ist ( `personal` ).</span><span class="sxs-lookup"><span data-stu-id="bd65c-392">Specifies whether the Connector offers an experience in the context of a channel in a `team`, or an experience scoped to an individual user alone (`personal`).</span></span> <span data-ttu-id="bd65c-393">Derzeit wird nur `team` der Bereich unterstützt.</span><span class="sxs-lookup"><span data-stu-id="bd65c-393">Currently, only the `team` scope is supported.</span></span>|
|`connectorId`|<span data-ttu-id="bd65c-394">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="bd65c-394">string</span></span>|<span data-ttu-id="bd65c-395">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="bd65c-395">64 characters</span></span>|<span data-ttu-id="bd65c-396">✔</span><span class="sxs-lookup"><span data-stu-id="bd65c-396">✔</span></span>|<span data-ttu-id="bd65c-397">Ein eindeutiger Bezeichner für den Connector, der seiner ID im [Connectors Developer Dashboard entspricht.](https://aka.ms/connectorsdashboard)</span><span class="sxs-lookup"><span data-stu-id="bd65c-397">A unique identifier for the Connector that matches its ID in the [Connectors Developer Dashboard](https://aka.ms/connectorsdashboard).</span></span>|

## <a name="composeextensions"></a><span data-ttu-id="bd65c-398">composeExtensions</span><span class="sxs-lookup"><span data-stu-id="bd65c-398">composeExtensions</span></span>

<span data-ttu-id="bd65c-399">**Optional** – Array</span><span class="sxs-lookup"><span data-stu-id="bd65c-399">**Optional** — array</span></span>

<span data-ttu-id="bd65c-400">Definiert eine Messagingerweiterung für die App.</span><span class="sxs-lookup"><span data-stu-id="bd65c-400">Defines a messaging extension for the app.</span></span>

> [!NOTE]
> <span data-ttu-id="bd65c-401">Der Name des Features wurde im November 2017 von "Verfassenerweiterung" in "Messagingerweiterung" geändert, aber der Manifestname bleibt unverändert, damit vorhandene Erweiterungen weiterhin funktionieren.</span><span class="sxs-lookup"><span data-stu-id="bd65c-401">The name of the feature was changed from "compose extension" to "messaging extension" in November, 2017, but the manifest name remains the same so that existing extensions continue to function.</span></span>

<span data-ttu-id="bd65c-402">Das Element ist ein Array (maximal 1 Element) mit allen Elementen vom `object` Typ .</span><span class="sxs-lookup"><span data-stu-id="bd65c-402">The item is an array (maximum of 1 element) with all elements of type `object`.</span></span> <span data-ttu-id="bd65c-403">Dieser Block ist nur für Lösungen erforderlich, die eine Messagingerweiterung bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="bd65c-403">This block is required only for solutions that provide a messaging extension.</span></span>

|<span data-ttu-id="bd65c-404">Name</span><span class="sxs-lookup"><span data-stu-id="bd65c-404">Name</span></span>| <span data-ttu-id="bd65c-405">Typ</span><span class="sxs-lookup"><span data-stu-id="bd65c-405">Type</span></span> | <span data-ttu-id="bd65c-406">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="bd65c-406">Maximum Size</span></span> | <span data-ttu-id="bd65c-407">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="bd65c-407">Required</span></span> | <span data-ttu-id="bd65c-408">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="bd65c-408">Description</span></span>|
|---|---|---|---|---|
|`botId`|<span data-ttu-id="bd65c-409">string</span><span class="sxs-lookup"><span data-stu-id="bd65c-409">string</span></span>|<span data-ttu-id="bd65c-410">64</span><span class="sxs-lookup"><span data-stu-id="bd65c-410">64</span></span>|<span data-ttu-id="bd65c-411">✔</span><span class="sxs-lookup"><span data-stu-id="bd65c-411">✔</span></span>|<span data-ttu-id="bd65c-412">Die eindeutige Microsoft-App-ID für den Bot, der die Messagingerweiterung unterstützt, wie beim Bot Framework registriert.</span><span class="sxs-lookup"><span data-stu-id="bd65c-412">The unique Microsoft app ID for the bot that backs the messaging extension, as registered with the Bot Framework.</span></span> <span data-ttu-id="bd65c-413">Dies kann mit der allgemeinen App-ID identisch sein.</span><span class="sxs-lookup"><span data-stu-id="bd65c-413">This may well be the same as the overall App ID.</span></span>|
|`commands`|<span data-ttu-id="bd65c-414">Array von Objekten</span><span class="sxs-lookup"><span data-stu-id="bd65c-414">array of objects</span></span>|<span data-ttu-id="bd65c-415">10 </span><span class="sxs-lookup"><span data-stu-id="bd65c-415">10</span></span>|<span data-ttu-id="bd65c-416">✔</span><span class="sxs-lookup"><span data-stu-id="bd65c-416">✔</span></span>|<span data-ttu-id="bd65c-417">Array von Befehlen, die von der Messagingerweiterung unterstützt werden</span><span class="sxs-lookup"><span data-stu-id="bd65c-417">Array of commands the messaging extension supports</span></span>|
|`canUpdateConfiguration`|<span data-ttu-id="bd65c-418">Boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="bd65c-418">boolean</span></span>|||<span data-ttu-id="bd65c-419">Ein Wert, der angibt, ob die Konfiguration einer Messagingerweiterung vom Benutzer aktualisiert werden kann.</span><span class="sxs-lookup"><span data-stu-id="bd65c-419">A value indicating whether the configuration of a messaging extension can be updated by the user.</span></span> <span data-ttu-id="bd65c-420">Standard: **False**.</span><span class="sxs-lookup"><span data-stu-id="bd65c-420">Default: **false**.</span></span>|
|`messageHandlers`|<span data-ttu-id="bd65c-421">Array von Objekten</span><span class="sxs-lookup"><span data-stu-id="bd65c-421">array of Objects</span></span>|<span data-ttu-id="bd65c-422">5 </span><span class="sxs-lookup"><span data-stu-id="bd65c-422">5</span></span>||<span data-ttu-id="bd65c-423">Eine Liste von Handlern, mit denen Apps aufgerufen werden können, wenn bestimmte Bedingungen erfüllt sind.</span><span class="sxs-lookup"><span data-stu-id="bd65c-423">A list of handlers that allow apps to be invoked when certain conditions are met.</span></span>|
|`messageHandlers.type`|<span data-ttu-id="bd65c-424">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="bd65c-424">string</span></span>|||<span data-ttu-id="bd65c-425">Der Typ des Nachrichtenhandlers.</span><span class="sxs-lookup"><span data-stu-id="bd65c-425">The type of message handler.</span></span> <span data-ttu-id="bd65c-426">Muss `"link"` sein.</span><span class="sxs-lookup"><span data-stu-id="bd65c-426">Must be `"link"`.</span></span>|
|`messageHandlers.value.domains`|<span data-ttu-id="bd65c-427">Array von Zeichenfolgen</span><span class="sxs-lookup"><span data-stu-id="bd65c-427">array of Strings</span></span>|||<span data-ttu-id="bd65c-428">Array von Domänen, für die sich der Linknachrichtenhandler registrieren kann.</span><span class="sxs-lookup"><span data-stu-id="bd65c-428">Array of domains that the link message handler can register for.</span></span>|

### <a name="composeextensionscommands"></a><span data-ttu-id="bd65c-429">composeExtensions.commands</span><span class="sxs-lookup"><span data-stu-id="bd65c-429">composeExtensions.commands</span></span>

<span data-ttu-id="bd65c-430">Ihre Messagingerweiterung sollte einen oder mehrere Befehle deklarieren.</span><span class="sxs-lookup"><span data-stu-id="bd65c-430">Your messaging extension should declare one or more commands.</span></span> <span data-ttu-id="bd65c-431">Jeder Befehl wird in Microsoft Teams als potenzielle Interaktion vom benutzeroberflächenbasierten Einstiegspunkt angezeigt.</span><span class="sxs-lookup"><span data-stu-id="bd65c-431">Each command appears in Microsoft Teams as a potential interaction from the UI-based entry point.</span></span> <span data-ttu-id="bd65c-432">Es gibt maximal 10 Befehle.</span><span class="sxs-lookup"><span data-stu-id="bd65c-432">There is a maximum of 10 commands.</span></span>

<span data-ttu-id="bd65c-433">Jedes Befehlselement ist ein Objekt mit der folgenden Struktur:</span><span class="sxs-lookup"><span data-stu-id="bd65c-433">Each command item is an object with the following structure:</span></span>

|<span data-ttu-id="bd65c-434">Name</span><span class="sxs-lookup"><span data-stu-id="bd65c-434">Name</span></span>| <span data-ttu-id="bd65c-435">Typ</span><span class="sxs-lookup"><span data-stu-id="bd65c-435">Type</span></span>| <span data-ttu-id="bd65c-436">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="bd65c-436">Maximum size</span></span> | <span data-ttu-id="bd65c-437">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="bd65c-437">Required</span></span> | <span data-ttu-id="bd65c-438">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="bd65c-438">Description</span></span>|
|---|---|---|---|---|
|`id`|<span data-ttu-id="bd65c-439">string</span><span class="sxs-lookup"><span data-stu-id="bd65c-439">string</span></span>|<span data-ttu-id="bd65c-440">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="bd65c-440">64 characters</span></span>|<span data-ttu-id="bd65c-441">✔</span><span class="sxs-lookup"><span data-stu-id="bd65c-441">✔</span></span>|<span data-ttu-id="bd65c-442">Die ID für den Befehl.</span><span class="sxs-lookup"><span data-stu-id="bd65c-442">The ID for the command.</span></span>|
|`title`|<span data-ttu-id="bd65c-443">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="bd65c-443">string</span></span>|<span data-ttu-id="bd65c-444">32 Zeichen</span><span class="sxs-lookup"><span data-stu-id="bd65c-444">32 characters</span></span>|<span data-ttu-id="bd65c-445">✔</span><span class="sxs-lookup"><span data-stu-id="bd65c-445">✔</span></span>|<span data-ttu-id="bd65c-446">Der benutzerfreundlicher Befehlsname.</span><span class="sxs-lookup"><span data-stu-id="bd65c-446">The user-friendly command name.</span></span>|
|`type`|<span data-ttu-id="bd65c-447">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="bd65c-447">string</span></span>|<span data-ttu-id="bd65c-448">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="bd65c-448">64 characters</span></span>||<span data-ttu-id="bd65c-449">Typ des Befehls.</span><span class="sxs-lookup"><span data-stu-id="bd65c-449">Type of the command.</span></span> <span data-ttu-id="bd65c-450">Einer von `query` oder `action` .</span><span class="sxs-lookup"><span data-stu-id="bd65c-450">One of `query` or `action`.</span></span> <span data-ttu-id="bd65c-451">Standard: **Abfrage**.</span><span class="sxs-lookup"><span data-stu-id="bd65c-451">Default: **query**.</span></span>|
|`description`|<span data-ttu-id="bd65c-452">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="bd65c-452">string</span></span>|<span data-ttu-id="bd65c-453">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="bd65c-453">128 characters</span></span>||<span data-ttu-id="bd65c-454">Die Beschreibung, die Benutzern angezeigt wird, um den Zweck dieses Befehls anzugeben.</span><span class="sxs-lookup"><span data-stu-id="bd65c-454">The description that appears to users to indicate the purpose of this command.</span></span>|
|`initialRun`|<span data-ttu-id="bd65c-455">Boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="bd65c-455">boolean</span></span>|||<span data-ttu-id="bd65c-456">Ein boolescher Wert, der angibt, ob der Befehl zunächst ohne Parameter ausgeführt werden soll.</span><span class="sxs-lookup"><span data-stu-id="bd65c-456">A boolean value that indicates whether the command should be run initially with no parameters.</span></span> <span data-ttu-id="bd65c-457">Standard: **False**.</span><span class="sxs-lookup"><span data-stu-id="bd65c-457">Default: **false**.</span></span>|
|`context`|<span data-ttu-id="bd65c-458">Array von Zeichenfolgen</span><span class="sxs-lookup"><span data-stu-id="bd65c-458">array of Strings</span></span>|<span data-ttu-id="bd65c-459">3</span><span class="sxs-lookup"><span data-stu-id="bd65c-459">3</span></span>||<span data-ttu-id="bd65c-460">Definiert, von wo aus die Nachrichtenerweiterung aufgerufen werden kann.</span><span class="sxs-lookup"><span data-stu-id="bd65c-460">Defines where the message extension can be invoked from.</span></span> <span data-ttu-id="bd65c-461">Eine beliebige Kombination von `compose` , `commandBox` `message` .</span><span class="sxs-lookup"><span data-stu-id="bd65c-461">Any combination of`compose`,`commandBox`,`message` .</span></span> <span data-ttu-id="bd65c-462">Der Standardwert lautet `["compose","commandBox"]`.</span><span class="sxs-lookup"><span data-stu-id="bd65c-462">Default is `["compose","commandBox"]`.</span></span>|
|`fetchTask`|<span data-ttu-id="bd65c-463">Boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="bd65c-463">boolean</span></span>|||<span data-ttu-id="bd65c-464">Ein boolescher Wert, der angibt, ob das Aufgabenmodul dynamisch abgerufen werden soll.</span><span class="sxs-lookup"><span data-stu-id="bd65c-464">A boolean value that indicates if it should fetch the task module dynamically.</span></span> <span data-ttu-id="bd65c-465">Standard: **False**.</span><span class="sxs-lookup"><span data-stu-id="bd65c-465">Default: **false**.</span></span>|
|`taskInfo`|<span data-ttu-id="bd65c-466">Objekt</span><span class="sxs-lookup"><span data-stu-id="bd65c-466">object</span></span>|||<span data-ttu-id="bd65c-467">Geben Sie das Aufgabenmodul an, das bei Verwendung eines Befehls für eine Messagingerweiterung vor dem Laden geladen werden soll.</span><span class="sxs-lookup"><span data-stu-id="bd65c-467">Specify the task module to pre-load when using a messaging extension command.</span></span>|
|`taskInfo.title`|<span data-ttu-id="bd65c-468">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="bd65c-468">string</span></span>|<span data-ttu-id="bd65c-469">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="bd65c-469">64 characters</span></span>||<span data-ttu-id="bd65c-470">Titel des ersten Dialogfelds.</span><span class="sxs-lookup"><span data-stu-id="bd65c-470">Initial dialog title.</span></span>|
|`taskInfo.width`|<span data-ttu-id="bd65c-471">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="bd65c-471">string</span></span>|||<span data-ttu-id="bd65c-472">Dialogbreite – entweder eine Zahl in Pixel oder ein Standardlayout wie "groß", "mittel" oder "klein".</span><span class="sxs-lookup"><span data-stu-id="bd65c-472">Dialog width - either a number in pixels or default layout such as 'large', 'medium', or 'small'.</span></span>|
|`taskInfo.height`|<span data-ttu-id="bd65c-473">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="bd65c-473">string</span></span>|||<span data-ttu-id="bd65c-474">Dialoghöhe – entweder eine Zahl in Pixel oder ein Standardlayout wie "groß", "mittel" oder "klein".</span><span class="sxs-lookup"><span data-stu-id="bd65c-474">Dialog height - either a number in pixels or default layout such as 'large', 'medium', or 'small'.</span></span>|
|`taskInfo.url`|<span data-ttu-id="bd65c-475">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="bd65c-475">string</span></span>|||<span data-ttu-id="bd65c-476">Ursprüngliche Webview-URL.</span><span class="sxs-lookup"><span data-stu-id="bd65c-476">Initial webview URL.</span></span>|
|`parameters`|<span data-ttu-id="bd65c-477">Array des Objekts</span><span class="sxs-lookup"><span data-stu-id="bd65c-477">array of object</span></span>|<span data-ttu-id="bd65c-478">5 Elemente</span><span class="sxs-lookup"><span data-stu-id="bd65c-478">5 items</span></span>|<span data-ttu-id="bd65c-479">✔</span><span class="sxs-lookup"><span data-stu-id="bd65c-479">✔</span></span>|<span data-ttu-id="bd65c-480">Die Liste der Parameter, die der Befehl verwendet.</span><span class="sxs-lookup"><span data-stu-id="bd65c-480">The list of parameters the command takes.</span></span> <span data-ttu-id="bd65c-481">Minimum: 1; Maximum: 5.</span><span class="sxs-lookup"><span data-stu-id="bd65c-481">Minimum: 1; maximum: 5.</span></span>|
|`parameters.name`|<span data-ttu-id="bd65c-482">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="bd65c-482">string</span></span>|<span data-ttu-id="bd65c-483">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="bd65c-483">64 characters</span></span>|<span data-ttu-id="bd65c-484">✔</span><span class="sxs-lookup"><span data-stu-id="bd65c-484">✔</span></span>|<span data-ttu-id="bd65c-485">Der Name des Parameters, wie er im Client angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="bd65c-485">The name of the parameter as it appears in the client.</span></span> <span data-ttu-id="bd65c-486">Dies ist in der Benutzeranforderung enthalten.</span><span class="sxs-lookup"><span data-stu-id="bd65c-486">This is included in the user request.</span></span>|
|`parameters.title`|<span data-ttu-id="bd65c-487">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="bd65c-487">string</span></span>|<span data-ttu-id="bd65c-488">32 Zeichen</span><span class="sxs-lookup"><span data-stu-id="bd65c-488">32 characters</span></span>|<span data-ttu-id="bd65c-489">✔</span><span class="sxs-lookup"><span data-stu-id="bd65c-489">✔</span></span>|<span data-ttu-id="bd65c-490">Benutzerfreundlicher Titel für den Parameter.</span><span class="sxs-lookup"><span data-stu-id="bd65c-490">User-friendly title for the parameter.</span></span>|
|`parameters.description`|<span data-ttu-id="bd65c-491">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="bd65c-491">string</span></span>|<span data-ttu-id="bd65c-492">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="bd65c-492">128 characters</span></span>||<span data-ttu-id="bd65c-493">Benutzerfreundliche Zeichenfolge, die den Zweck dieses Parameters beschreibt.</span><span class="sxs-lookup"><span data-stu-id="bd65c-493">User-friendly string that describes this parameter’s purpose.</span></span>|
|`parameters.value`|<span data-ttu-id="bd65c-494">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="bd65c-494">string</span></span>|<span data-ttu-id="bd65c-495">512 Zeichen</span><span class="sxs-lookup"><span data-stu-id="bd65c-495">512 characters</span></span>||<span data-ttu-id="bd65c-496">Anfangswert für den Parameter.</span><span class="sxs-lookup"><span data-stu-id="bd65c-496">Initial value for the parameter.</span></span>|
|`parameters.inputType`|<span data-ttu-id="bd65c-497">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="bd65c-497">string</span></span>|<span data-ttu-id="bd65c-498">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="bd65c-498">128 characters</span></span>||<span data-ttu-id="bd65c-499">Definiert den Typ des Steuerelements, das in einem Aufgabenmodul für angezeigt `fetchTask: true` wird.</span><span class="sxs-lookup"><span data-stu-id="bd65c-499">Defines the type of control displayed on a task module for`fetchTask: true` .</span></span> <span data-ttu-id="bd65c-500">Einer von `text, textarea, number, date, time, toggle, choiceset` .</span><span class="sxs-lookup"><span data-stu-id="bd65c-500">One of `text, textarea, number, date, time, toggle, choiceset` .</span></span>|
|`parameters.choices`|<span data-ttu-id="bd65c-501">Array von Objekten</span><span class="sxs-lookup"><span data-stu-id="bd65c-501">array of objects</span></span>|<span data-ttu-id="bd65c-502">10 Elemente</span><span class="sxs-lookup"><span data-stu-id="bd65c-502">10 items</span></span>||<span data-ttu-id="bd65c-503">Die Auswahloptionen für die `choiceset` .</span><span class="sxs-lookup"><span data-stu-id="bd65c-503">The choice options for the`choiceset`.</span></span> <span data-ttu-id="bd65c-504">Wird nur verwendet, wenn `parameter.inputType` `choiceset` .</span><span class="sxs-lookup"><span data-stu-id="bd65c-504">Use only when`parameter.inputType` is `choiceset`.</span></span>|
|`parameters.choices.title`|<span data-ttu-id="bd65c-505">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="bd65c-505">string</span></span>|<span data-ttu-id="bd65c-506">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="bd65c-506">128 characters</span></span>|<span data-ttu-id="bd65c-507">✔</span><span class="sxs-lookup"><span data-stu-id="bd65c-507">✔</span></span>|<span data-ttu-id="bd65c-508">Der Titel der Auswahl.</span><span class="sxs-lookup"><span data-stu-id="bd65c-508">Title of the choice.</span></span>|
|`parameters.choices.value`|<span data-ttu-id="bd65c-509">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="bd65c-509">string</span></span>|<span data-ttu-id="bd65c-510">512 Zeichen</span><span class="sxs-lookup"><span data-stu-id="bd65c-510">512 characters</span></span>|<span data-ttu-id="bd65c-511">✔</span><span class="sxs-lookup"><span data-stu-id="bd65c-511">✔</span></span>|<span data-ttu-id="bd65c-512">Value of the choice.</span><span class="sxs-lookup"><span data-stu-id="bd65c-512">Value of the choice.</span></span>|

## <a name="permissions"></a><span data-ttu-id="bd65c-513">Berechtigungen</span><span class="sxs-lookup"><span data-stu-id="bd65c-513">permissions</span></span>

<span data-ttu-id="bd65c-514">**Optional** – Zeichenfolgenarray</span><span class="sxs-lookup"><span data-stu-id="bd65c-514">**Optional** — array of strings</span></span>

<span data-ttu-id="bd65c-515">Ein Array, von dem angegeben wird, welche Berechtigungen die App anfordert, wodurch Endbenutzer wissen, `string` wie die Erweiterung funktioniert.</span><span class="sxs-lookup"><span data-stu-id="bd65c-515">An array of `string` which specifies which permissions the app requests, which lets end users know how the extension will perform.</span></span> <span data-ttu-id="bd65c-516">Die folgenden Optionen sind nicht exklusiv:</span><span class="sxs-lookup"><span data-stu-id="bd65c-516">The following options are non-exclusive:</span></span>

* <span data-ttu-id="bd65c-517">`identity`&emsp;Erfordert Informationen zur Benutzeridentität</span><span class="sxs-lookup"><span data-stu-id="bd65c-517">`identity` &emsp; Requires user identity information</span></span>
* <span data-ttu-id="bd65c-518">`messageTeamMembers`&emsp;Erfordert die Berechtigung zum Senden direkter Nachrichten an Teammitglieder</span><span class="sxs-lookup"><span data-stu-id="bd65c-518">`messageTeamMembers` &emsp; Requires permission to send direct messages to team members</span></span>

<span data-ttu-id="bd65c-519">Wenn Sie diese Berechtigungen beim Aktualisieren Ihrer App ändern, wiederholen Ihre Benutzer den Zustimmungsprozess, wenn sie die aktualisierte App zum ersten Mal ausführen.</span><span class="sxs-lookup"><span data-stu-id="bd65c-519">Changing these permissions when updating your app will cause your users to repeat the consent process the first time they run the updated app.</span></span> <span data-ttu-id="bd65c-520">Weitere [Informationen finden Sie unter Aktualisieren](~/concepts/deploy-and-publish/appsource/post-publish/overview.md) Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="bd65c-520">See [Updating your app](~/concepts/deploy-and-publish/appsource/post-publish/overview.md) for more information.</span></span>

## <a name="devicepermissions"></a><span data-ttu-id="bd65c-521">devicePermissions</span><span class="sxs-lookup"><span data-stu-id="bd65c-521">devicePermissions</span></span>

<span data-ttu-id="bd65c-522">**Optional** – Zeichenfolgenarray</span><span class="sxs-lookup"><span data-stu-id="bd65c-522">**Optional** — array of strings</span></span>

<span data-ttu-id="bd65c-523">Gibt die systemeigenen Features auf dem Gerät eines Benutzers an, auf die Ihre App Zugriff anfordern kann.</span><span class="sxs-lookup"><span data-stu-id="bd65c-523">Specifies the native features on a user's device that your app may request access to.</span></span> <span data-ttu-id="bd65c-524">Mögliche Optionen sind:</span><span class="sxs-lookup"><span data-stu-id="bd65c-524">Options are:</span></span>

* `geolocation`
* `media`
* `notifications`
* `midi`
* `openExternal`

## <a name="validdomains"></a><span data-ttu-id="bd65c-525">validDomains</span><span class="sxs-lookup"><span data-stu-id="bd65c-525">validDomains</span></span>

<span data-ttu-id="bd65c-526">**Optional**, mit Ausnahme **von "Erforderlich"** (sofern angegeben)</span><span class="sxs-lookup"><span data-stu-id="bd65c-526">**Optional**, except **Required** where noted</span></span>

<span data-ttu-id="bd65c-527">Eine Liste gültiger Domänen für Websites, die von der App erwartet werden, innerhalb des Teams-Clients zu laden.</span><span class="sxs-lookup"><span data-stu-id="bd65c-527">A list of valid domains for websites the app expects to load within the Teams client.</span></span> <span data-ttu-id="bd65c-528">Domänenauflistungen können Platzhalter enthalten, z. B. `*.example.com` .</span><span class="sxs-lookup"><span data-stu-id="bd65c-528">Domain listings can include wildcards, for example `*.example.com`.</span></span> <span data-ttu-id="bd65c-529">Dies entspricht genau einem Segment der Domäne. Wenn Sie übereinstimmen müssen, `a.b.example.com` verwenden Sie `*.*.example.com` .</span><span class="sxs-lookup"><span data-stu-id="bd65c-529">This matches exactly one segment of the domain; if you need to match `a.b.example.com` then use `*.*.example.com`.</span></span> <span data-ttu-id="bd65c-530">Wenn Ihre Registerkartenkonfiguration oder Inhaltsbenutzeroberfläche neben der Registerkartenkonfiguration zu einer anderen Domäne navigieren muss, muss diese Domäne hier angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="bd65c-530">If your tab configuration or content UI needs to navigate to any other domain besides the one use for tab configuration, that domain must be specified here.</span></span>

<span data-ttu-id="bd65c-531">Es ist **jedoch nicht** erforderlich, die Domänen von Identitätsanbietern, die Sie unterstützen möchten, in Ihre App zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="bd65c-531">It is **not** necessary to include the domains of identity providers you want to support in your app, however.</span></span> <span data-ttu-id="bd65c-532">Um sich z. B. mithilfe einer Google-ID zu authentifizieren, ist es erforderlich, zu accounts.google.com umzuleiten, sie sollten jedoch nicht accounts.google.com `validDomains[]` enthalten.</span><span class="sxs-lookup"><span data-stu-id="bd65c-532">For example, to authenticate using a Google ID, it's necessary to redirect to accounts.google.com, but you should not include accounts.google.com in `validDomains[]`.</span></span>

<span data-ttu-id="bd65c-533">Teams-Apps, für die ihre eigenen SharePoint-URLs ordnungsgemäß funktionieren müssen, enthalten möglicherweise "{teamsitedomain}" in der Liste der gültigen Domänen.</span><span class="sxs-lookup"><span data-stu-id="bd65c-533">Teams apps that require their own sharepoint URLs to function well, may include "{teamsitedomain}" in their valid domain list.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bd65c-534">Fügen Sie keine Domänen hinzu, die sich außerhalb Ihrer Kontrolle befinden, entweder direkt oder über Platzhalter.</span><span class="sxs-lookup"><span data-stu-id="bd65c-534">Do not add domains that are outside your control, either directly or via wildcards.</span></span> <span data-ttu-id="bd65c-535">Beispielsweise ist `yourapp.onmicrosoft.com` er gültig, aber `*.onmicrosoft.com` ungültig.</span><span class="sxs-lookup"><span data-stu-id="bd65c-535">For example, `yourapp.onmicrosoft.com` is valid, but `*.onmicrosoft.com` is not valid.</span></span>

<span data-ttu-id="bd65c-536">Das Objekt ist ein Array mit allen Elementen des Typs `string` .</span><span class="sxs-lookup"><span data-stu-id="bd65c-536">The object is an array with all elements of the type `string`.</span></span>

## <a name="webapplicationinfo"></a><span data-ttu-id="bd65c-537">webApplicationInfo</span><span class="sxs-lookup"><span data-stu-id="bd65c-537">webApplicationInfo</span></span>

<span data-ttu-id="bd65c-538">**Optional** – Objekt</span><span class="sxs-lookup"><span data-stu-id="bd65c-538">**Optional** — object</span></span>

<span data-ttu-id="bd65c-539">Geben Sie Ihre Azure Active Directory (Azure AD)-App-ID und Microsoft Graph-Informationen an, damit sich Benutzer nahtlos bei Ihrer App anmelden können.</span><span class="sxs-lookup"><span data-stu-id="bd65c-539">Specify your Azure Active Directory (Azure AD) App ID and Microsoft Graph information to help users seamlessly sign into your app.</span></span> <span data-ttu-id="bd65c-540">Wenn Ihre App in Azure AD registriert ist, müssen Sie die App-ID bereitstellen, damit Administratoren die Berechtigungen auf einfache Weise überprüfen und die Zustimmung im Teams Admin Center erteilen können.</span><span class="sxs-lookup"><span data-stu-id="bd65c-540">If your app is registered in Azure AD, you must provide the App ID, so that administrators can easily review permissions and grant consent in Teams admin center.</span></span>

|<span data-ttu-id="bd65c-541">Name</span><span class="sxs-lookup"><span data-stu-id="bd65c-541">Name</span></span>| <span data-ttu-id="bd65c-542">Typ</span><span class="sxs-lookup"><span data-stu-id="bd65c-542">Type</span></span>| <span data-ttu-id="bd65c-543">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="bd65c-543">Maximum size</span></span> | <span data-ttu-id="bd65c-544">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="bd65c-544">Required</span></span> | <span data-ttu-id="bd65c-545">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="bd65c-545">Description</span></span>|
|---|---|---|---|---|
|`id`|<span data-ttu-id="bd65c-546">string</span><span class="sxs-lookup"><span data-stu-id="bd65c-546">string</span></span>|<span data-ttu-id="bd65c-547">36 Zeichen</span><span class="sxs-lookup"><span data-stu-id="bd65c-547">36 characters</span></span>|<span data-ttu-id="bd65c-548">✔</span><span class="sxs-lookup"><span data-stu-id="bd65c-548">✔</span></span>|<span data-ttu-id="bd65c-549">AAD-Anwendungs-ID der App.</span><span class="sxs-lookup"><span data-stu-id="bd65c-549">AAD application id of the app.</span></span> <span data-ttu-id="bd65c-550">Diese ID muss eine GUID sein.</span><span class="sxs-lookup"><span data-stu-id="bd65c-550">This id must be a GUID.</span></span>|
|`resource`|<span data-ttu-id="bd65c-551">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="bd65c-551">string</span></span>|<span data-ttu-id="bd65c-552">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="bd65c-552">2048 characters</span></span>|<span data-ttu-id="bd65c-553">✔</span><span class="sxs-lookup"><span data-stu-id="bd65c-553">✔</span></span>|<span data-ttu-id="bd65c-554">Ressourcen-URL der App zum Abrufen des Authentifizierungstokens für SSO.</span><span class="sxs-lookup"><span data-stu-id="bd65c-554">Resource URL of app for acquiring auth token for SSO.</span></span> </br> <span data-ttu-id="bd65c-555">**HINWEIS:** Wenn Sie SSO nicht verwenden, stellen Sie sicher, dass Sie in dieses Feld einen Dummyzeichenfolgenwert in Ihr App-Manifest eingeben, um beispielsweise eine https://notapplicable Fehlerantwort zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="bd65c-555">**NOTE:** If you are not using SSO, ensure that you enter a dummy string value in this field to your app manifest, for example, https://notapplicable to avoid an error response.</span></span> |
|`applicationPermissions`|<span data-ttu-id="bd65c-556">array of strings</span><span class="sxs-lookup"><span data-stu-id="bd65c-556">array of strings</span></span>|<span data-ttu-id="bd65c-557">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="bd65c-557">128 characters</span></span>||<span data-ttu-id="bd65c-558">Geben Sie eine [präzise ressourcenspezifische Zustimmung an.](../../graph-api/rsc/resource-specific-consent.md#resource-specific-permissions)</span><span class="sxs-lookup"><span data-stu-id="bd65c-558">Specify granular [resource specific consent](../../graph-api/rsc/resource-specific-consent.md#resource-specific-permissions).</span></span>|

## <a name="showloadingindicator"></a><span data-ttu-id="bd65c-559">showLoadingIndicator</span><span class="sxs-lookup"><span data-stu-id="bd65c-559">showLoadingIndicator</span></span>

<span data-ttu-id="bd65c-560">**Optional** – boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="bd65c-560">**Optional** — boolean</span></span>

<span data-ttu-id="bd65c-561">Gibt an, ob die Ladeanzeige angezeigt werden soll, wenn eine App/Registerkarte geladen wird.</span><span class="sxs-lookup"><span data-stu-id="bd65c-561">Indicate whether or not to show the loading indicator when an app/tab is loading.</span></span> <span data-ttu-id="bd65c-562">Standard: **False**.</span><span class="sxs-lookup"><span data-stu-id="bd65c-562">Default: **false**.</span></span>
>[!NOTE]
><span data-ttu-id="bd65c-563">Wenn Sie "showLoadingIndicator : true" in Ihrem App-Manifest festlegen, müssen Sie die Inhaltsseiten Ihrer Registerkarten und Aufgabenmodule [](../../tabs/how-to/create-tab-pages/content-page.md#show-a-native-loading-indicator) so ändern, dass das protokoll unter Anzeigen eines nativen Ladeindikatordokuments beschrieben wird.</span><span class="sxs-lookup"><span data-stu-id="bd65c-563">If you set "showLoadingIndicator : true" in your app manifest, then for the page to load correctly, you must modify the content pages of your tabs and task modules as per the protocol described in [Show a native loading indicator](../../tabs/how-to/create-tab-pages/content-page.md#show-a-native-loading-indicator) document.</span></span>


## <a name="isfullscreen"></a><span data-ttu-id="bd65c-564">isFullScreen</span><span class="sxs-lookup"><span data-stu-id="bd65c-564">isFullScreen</span></span>

 <span data-ttu-id="bd65c-565">**Optional** – boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="bd65c-565">**Optional** — boolean</span></span>

<span data-ttu-id="bd65c-566">Geben Sie an, wo eine persönliche App mit oder ohne Tabulatorleiste gerendert wird.</span><span class="sxs-lookup"><span data-stu-id="bd65c-566">Indicate where a personal app is rendered with or without a tab-header bar.</span></span> <span data-ttu-id="bd65c-567">Standard: **False**.</span><span class="sxs-lookup"><span data-stu-id="bd65c-567">Default: **false**.</span></span>

## <a name="activities"></a><span data-ttu-id="bd65c-568">Aktivitäten</span><span class="sxs-lookup"><span data-stu-id="bd65c-568">activities</span></span>

<span data-ttu-id="bd65c-569">**Optional** – Objekt</span><span class="sxs-lookup"><span data-stu-id="bd65c-569">**Optional** — object</span></span>

<span data-ttu-id="bd65c-570">Definieren Sie die Eigenschaften, die Ihre App zum Veröffentlichen in einem Benutzeraktivitätsfeed verwendet.</span><span class="sxs-lookup"><span data-stu-id="bd65c-570">Define the properties your app will use to post to a user activity feed.</span></span>

|<span data-ttu-id="bd65c-571">Name</span><span class="sxs-lookup"><span data-stu-id="bd65c-571">Name</span></span>| <span data-ttu-id="bd65c-572">Typ</span><span class="sxs-lookup"><span data-stu-id="bd65c-572">Type</span></span>| <span data-ttu-id="bd65c-573">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="bd65c-573">Maximum size</span></span> | <span data-ttu-id="bd65c-574">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="bd65c-574">Required</span></span> | <span data-ttu-id="bd65c-575">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="bd65c-575">Description</span></span>|
|---|---|---|---|---|
|`activityTypes`|<span data-ttu-id="bd65c-576">Array von Objekten</span><span class="sxs-lookup"><span data-stu-id="bd65c-576">array of Objects</span></span>|<span data-ttu-id="bd65c-577">128 Elemente</span><span class="sxs-lookup"><span data-stu-id="bd65c-577">128 items</span></span>| | <span data-ttu-id="bd65c-578">Geben Sie die Arten von Aktivitäten an, die Ihre App in einem Benutzeraktivitätsfeed veröffentlichen kann.</span><span class="sxs-lookup"><span data-stu-id="bd65c-578">Specify the types of activities that your app can post to a users activity feed.</span></span>|

### <a name="activitiesactivitytypes"></a><span data-ttu-id="bd65c-579">activities.activityTypes</span><span class="sxs-lookup"><span data-stu-id="bd65c-579">activities.activityTypes</span></span>

|<span data-ttu-id="bd65c-580">Name</span><span class="sxs-lookup"><span data-stu-id="bd65c-580">Name</span></span>| <span data-ttu-id="bd65c-581">Typ</span><span class="sxs-lookup"><span data-stu-id="bd65c-581">Type</span></span>| <span data-ttu-id="bd65c-582">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="bd65c-582">Maximum size</span></span> | <span data-ttu-id="bd65c-583">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="bd65c-583">Required</span></span> | <span data-ttu-id="bd65c-584">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="bd65c-584">Description</span></span>|
|---|---|---|---|---|
|`type`|<span data-ttu-id="bd65c-585">string</span><span class="sxs-lookup"><span data-stu-id="bd65c-585">string</span></span>|<span data-ttu-id="bd65c-586">32 Zeichen</span><span class="sxs-lookup"><span data-stu-id="bd65c-586">32 characters</span></span>|<span data-ttu-id="bd65c-587">✔</span><span class="sxs-lookup"><span data-stu-id="bd65c-587">✔</span></span>|<span data-ttu-id="bd65c-588">Der Benachrichtigungstyp.</span><span class="sxs-lookup"><span data-stu-id="bd65c-588">The notification type.</span></span> <span data-ttu-id="bd65c-589">*Siehe unten*.</span><span class="sxs-lookup"><span data-stu-id="bd65c-589">*See below*.</span></span>|
|`description`|<span data-ttu-id="bd65c-590">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="bd65c-590">string</span></span>|<span data-ttu-id="bd65c-591">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="bd65c-591">128 characters</span></span>|<span data-ttu-id="bd65c-592">✔</span><span class="sxs-lookup"><span data-stu-id="bd65c-592">✔</span></span>|<span data-ttu-id="bd65c-593">Eine kurze Beschreibung der Benachrichtigung.</span><span class="sxs-lookup"><span data-stu-id="bd65c-593">A brief description of the notification.</span></span> <span data-ttu-id="bd65c-594">*Siehe unten*.</span><span class="sxs-lookup"><span data-stu-id="bd65c-594">*See below*.</span></span>|
|`templateText`|<span data-ttu-id="bd65c-595">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="bd65c-595">string</span></span>|<span data-ttu-id="bd65c-596">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="bd65c-596">128 characters</span></span>|<span data-ttu-id="bd65c-597">✔</span><span class="sxs-lookup"><span data-stu-id="bd65c-597">✔</span></span>|<span data-ttu-id="bd65c-598">Beispiel: "{actor}: Aufgabe {taskId} für Sie erstellt"</span><span class="sxs-lookup"><span data-stu-id="bd65c-598">Ex: "{actor} created task {taskId} for you"</span></span>|

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
