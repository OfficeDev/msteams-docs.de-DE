---
title: Manifest-Schemareferenz
description: Beschreibung des manifest-Schemas für Microsoft Teams
keywords: Team Manifest-Schema
author: laujan
ms.author: lajanuar
ms.openlocfilehash: 3bf8bcc0ff99228b5dafded319df6f21ade56c2b
ms.sourcegitcommit: 64acd30eee8af5fe151e9866c13226ed3f337c72
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/18/2020
ms.locfileid: "49346686"
---
# <a name="reference-manifest-schema-for-microsoft-teams"></a><span data-ttu-id="ccf29-104">Referenz: Manifest-Schema für Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="ccf29-104">Reference: Manifest schema for Microsoft Teams</span></span>

<span data-ttu-id="ccf29-105">Das Microsoft Teams-Manifest beschreibt, wie die app in das Microsoft Teams-Produkt integriert wird.</span><span class="sxs-lookup"><span data-stu-id="ccf29-105">The Microsoft Teams manifest describes how the app integrates into the Microsoft Teams product.</span></span> <span data-ttu-id="ccf29-106">Das Manifest muss dem Schema entsprechen, das unter gehostet wird [`https://developer.microsoft.com/json-schemas/teams/v1.8/MicrosoftTeams.schema.json`]( https://developer.microsoft.com/json-schemas/teams/v1.8/MicrosoftTeams.schema.json) .</span><span class="sxs-lookup"><span data-stu-id="ccf29-106">Your manifest must conform to the schema hosted at [`https://developer.microsoft.com/json-schemas/teams/v1.8/MicrosoftTeams.schema.json`]( https://developer.microsoft.com/json-schemas/teams/v1.8/MicrosoftTeams.schema.json).</span></span> <span data-ttu-id="ccf29-107">Frühere Versionen 1.0-1.4 werden ebenfalls unterstützt (mit "v1. x" in der URL).</span><span class="sxs-lookup"><span data-stu-id="ccf29-107">Previous versions 1.0-1.4 are also supported (using "v1.x" in the URL).</span></span>

<span data-ttu-id="ccf29-108">Das folgende Schemabeispiel zeigt alle Erweiterungsoptionen.</span><span class="sxs-lookup"><span data-stu-id="ccf29-108">The following schema sample shows all extensibility options.</span></span>

## <a name="sample-full-manifest"></a><span data-ttu-id="ccf29-109">Vollständiges Beispiel Manifest</span><span class="sxs-lookup"><span data-stu-id="ccf29-109">Sample full manifest</span></span>

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

<span data-ttu-id="ccf29-110">Das Schema definiert die folgenden Eigenschaften:</span><span class="sxs-lookup"><span data-stu-id="ccf29-110">The schema defines the following properties:</span></span>

## <a name="schema"></a><span data-ttu-id="ccf29-111">$schema</span><span class="sxs-lookup"><span data-stu-id="ccf29-111">$schema</span></span>

<span data-ttu-id="ccf29-112">*Optional, jedoch empfohlen* – Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="ccf29-112">*Optional, but recommended* — string</span></span>

<span data-ttu-id="ccf29-113">Die https://-URL, die auf das JSON-Schema für das Manifest verweist.</span><span class="sxs-lookup"><span data-stu-id="ccf29-113">The https:// URL referencing the JSON Schema for the manifest.</span></span>

## <a name="manifestversion"></a><span data-ttu-id="ccf29-114">manifestVersion</span><span class="sxs-lookup"><span data-stu-id="ccf29-114">manifestVersion</span></span>

<span data-ttu-id="ccf29-115">**Erforderlich** – Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="ccf29-115">**Required** — string</span></span>

<span data-ttu-id="ccf29-116">Die Version des manifest-Schemas, die dieses Manifest verwendet.</span><span class="sxs-lookup"><span data-stu-id="ccf29-116">The version of the manifest schema this manifest is using.</span></span> <span data-ttu-id="ccf29-117">Es sollte "1,7" sein.</span><span class="sxs-lookup"><span data-stu-id="ccf29-117">It should be "1.7".</span></span>

## <a name="version"></a><span data-ttu-id="ccf29-118">Version</span><span class="sxs-lookup"><span data-stu-id="ccf29-118">version</span></span>

<span data-ttu-id="ccf29-119">**Erforderlich** – Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="ccf29-119">**Required** — string</span></span>

<span data-ttu-id="ccf29-120">Die Version der jeweiligen App.</span><span class="sxs-lookup"><span data-stu-id="ccf29-120">The version of the specific app.</span></span> <span data-ttu-id="ccf29-121">Wenn Sie etwas in ihrem Manifest aktualisieren, muss die Version ebenfalls inkrementiert werden.</span><span class="sxs-lookup"><span data-stu-id="ccf29-121">If you update something in your manifest, the version must be incremented as well.</span></span> <span data-ttu-id="ccf29-122">Auf diese Weise wird bei der Installation des neuen Manifests das vorhandene überschrieben, und der Benutzer erhält die neue Funktionalität.</span><span class="sxs-lookup"><span data-stu-id="ccf29-122">This way, when the new manifest is installed, it will overwrite the existing one and the user will get the new functionality.</span></span> <span data-ttu-id="ccf29-123">Wenn diese APP an den Store übermittelt wurde, muss das neue Manifest erneut übermittelt und erneut validiert werden.</span><span class="sxs-lookup"><span data-stu-id="ccf29-123">If this app was submitted to the store, the new manifest will have to be re-submitted and re-validated.</span></span> <span data-ttu-id="ccf29-124">Dann erhalten Benutzer dieser APP das neue aktualisierte Manifest automatisch in ein paar Stunden, nachdem es genehmigt wurde.</span><span class="sxs-lookup"><span data-stu-id="ccf29-124">Then, users of this app will get the new updated manifest automatically in a few hours, after it is approved.</span></span>

<span data-ttu-id="ccf29-125">Wenn sich die angeforderte APP geändert hat, werden die Benutzer aufgefordert, die APP zu aktualisieren und erneut zu genehmigen.</span><span class="sxs-lookup"><span data-stu-id="ccf29-125">If the app requested permissions change, users will be prompted to upgrade and re-consent to the app.</span></span>

<span data-ttu-id="ccf29-126">Diese Versionszeichenfolge muss dem [semver](http://semver.org/) -Standard (Major) entsprechen. Moll. Patch).</span><span class="sxs-lookup"><span data-stu-id="ccf29-126">This version string must follow the [semver](http://semver.org/) standard (MAJOR.MINOR.PATCH).</span></span>

## <a name="id"></a><span data-ttu-id="ccf29-127">id</span><span class="sxs-lookup"><span data-stu-id="ccf29-127">id</span></span>

<span data-ttu-id="ccf29-128">**Erforderlich** – Microsoft App-ID</span><span class="sxs-lookup"><span data-stu-id="ccf29-128">**Required** — Microsoft app ID</span></span>

<span data-ttu-id="ccf29-129">Der eindeutige von Microsoft generierte Bezeichner für diese APP.</span><span class="sxs-lookup"><span data-stu-id="ccf29-129">The unique Microsoft-generated identifier for this app.</span></span> <span data-ttu-id="ccf29-130">Wenn Sie einen bot über das Microsoft bot-Framework registriert haben oder sich die Webanwendung Ihrer Registerkarte bereits bei Microsoft anmeldet, sollten Sie bereits über eine ID verfügen und diese hier eingeben.</span><span class="sxs-lookup"><span data-stu-id="ccf29-130">If you have registered a bot via the Microsoft Bot Framework, or your tab's web app already signs in with Microsoft, you should already have an ID and should enter it here.</span></span> <span data-ttu-id="ccf29-131">Andernfalls sollten Sie eine neue ID im Microsoft-Anwendungs Registrierungs Portal ([meine Anwendungen](https://apps.dev.microsoft.com)) generieren, Sie hier eingeben und dann wieder verwenden, wenn Sie einen bot hinzufügen. Hinweis: Wenn Sie ein Update an Ihre vorhandene app in AppSource übermitteln, darf die ID in ihrem Manifest nicht geändert werden.</span><span class="sxs-lookup"><span data-stu-id="ccf29-131">Otherwise, you should generate a new ID at the Microsoft Application Registration Portal ([My Applications](https://apps.dev.microsoft.com)), enter it here, and then reuse it when you add a bot.Note: If you are submitting an update to your existing app in AppSource, the ID in your manifest must not be modified.</span></span>

## <a name="developer"></a><span data-ttu-id="ccf29-132">developer</span><span class="sxs-lookup"><span data-stu-id="ccf29-132">developer</span></span>

<span data-ttu-id="ccf29-133">**Erforderlich** – Objekt</span><span class="sxs-lookup"><span data-stu-id="ccf29-133">**Required** — object</span></span>

<span data-ttu-id="ccf29-134">Gibt Informationen zu Ihrem Unternehmen an.</span><span class="sxs-lookup"><span data-stu-id="ccf29-134">Specifies information about your company.</span></span> <span data-ttu-id="ccf29-135">Für an AppSource übermittelte Apps (ehemals Office Store) müssen diese Werte mit den Informationen in Ihrem AppSource-Eintrag übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="ccf29-135">For apps submitted to AppSource (formerly Office Store), these values must match the information in your AppSource entry.</span></span> <span data-ttu-id="ccf29-136">Weitere Informationen finden Sie in unseren [Veröffentlichungsrichtlinien](~/concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md) .</span><span class="sxs-lookup"><span data-stu-id="ccf29-136">See our [publishing guidelines](~/concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md) for additional information.</span></span>

|<span data-ttu-id="ccf29-137">Name</span><span class="sxs-lookup"><span data-stu-id="ccf29-137">Name</span></span>| <span data-ttu-id="ccf29-138">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="ccf29-138">Maximum size</span></span> | <span data-ttu-id="ccf29-139">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="ccf29-139">Required</span></span> | <span data-ttu-id="ccf29-140">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ccf29-140">Description</span></span>|
|---|---|---|---|
|`name`|<span data-ttu-id="ccf29-141">32 Zeichen</span><span class="sxs-lookup"><span data-stu-id="ccf29-141">32 characters</span></span>|<span data-ttu-id="ccf29-142">✔</span><span class="sxs-lookup"><span data-stu-id="ccf29-142">✔</span></span>|<span data-ttu-id="ccf29-143">Der Anzeigename für den Entwickler.</span><span class="sxs-lookup"><span data-stu-id="ccf29-143">The display name for the developer.</span></span>|
|`websiteUrl`|<span data-ttu-id="ccf29-144">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="ccf29-144">2048 characters</span></span>|<span data-ttu-id="ccf29-145">✔</span><span class="sxs-lookup"><span data-stu-id="ccf29-145">✔</span></span>|<span data-ttu-id="ccf29-146">Die https://-URL zur Website des Entwicklers.</span><span class="sxs-lookup"><span data-stu-id="ccf29-146">The https:// URL to the developer's website.</span></span> <span data-ttu-id="ccf29-147">Dieser Link sollte Benutzer zu Ihrer Firma oder produktspezifischen Zielseite führen.</span><span class="sxs-lookup"><span data-stu-id="ccf29-147">This link should take users to your company or product-specific landing page.</span></span>|
|`privacyUrl`|<span data-ttu-id="ccf29-148">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="ccf29-148">2048 characters</span></span>|<span data-ttu-id="ccf29-149">✔</span><span class="sxs-lookup"><span data-stu-id="ccf29-149">✔</span></span>|<span data-ttu-id="ccf29-150">Die https://-URL zur Datenschutzrichtlinie des Entwicklers.</span><span class="sxs-lookup"><span data-stu-id="ccf29-150">The https:// URL to the developer's privacy policy.</span></span>|
|`termsOfUseUrl`|<span data-ttu-id="ccf29-151">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="ccf29-151">2048 characters</span></span>|<span data-ttu-id="ccf29-152">✔</span><span class="sxs-lookup"><span data-stu-id="ccf29-152">✔</span></span>|<span data-ttu-id="ccf29-153">Die https://-URL zu den Nutzungsbedingungen des Entwicklers.</span><span class="sxs-lookup"><span data-stu-id="ccf29-153">The https:// URL to the developer's terms of use.</span></span>|
|`mpnId`|<span data-ttu-id="ccf29-154">10 Zeichen</span><span class="sxs-lookup"><span data-stu-id="ccf29-154">10 characters</span></span>| |<span data-ttu-id="ccf29-155">**Optional** Die Microsoft Partner-Netzwerk-ID, die die Partnerorganisation identifiziert, die die APP aufbaut.</span><span class="sxs-lookup"><span data-stu-id="ccf29-155">**Optional** The Microsoft Partner Network ID that identifies the partner organization building the app.</span></span>|

## <a name="name"></a><span data-ttu-id="ccf29-156">name</span><span class="sxs-lookup"><span data-stu-id="ccf29-156">name</span></span>

<span data-ttu-id="ccf29-157">**Erforderlich** – Objekt</span><span class="sxs-lookup"><span data-stu-id="ccf29-157">**Required** — object</span></span>

<span data-ttu-id="ccf29-158">Der Name der APP-Erfahrung, der Benutzern in der Microsoft Teams-Benutzeroberfläche angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="ccf29-158">The name of your app experience, displayed to users in the Teams experience.</span></span> <span data-ttu-id="ccf29-159">Für apps, die an AppSource übermittelt werden, müssen diese Werte mit den Informationen in Ihrem AppSource-Eintrag übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="ccf29-159">For apps submitted to AppSource, these values must match the information in your AppSource entry.</span></span> <span data-ttu-id="ccf29-160">Die Werte von `short` und `full` sollten nicht identisch sein.</span><span class="sxs-lookup"><span data-stu-id="ccf29-160">The values of `short` and `full` should not be the same.</span></span>

|<span data-ttu-id="ccf29-161">Name</span><span class="sxs-lookup"><span data-stu-id="ccf29-161">Name</span></span>| <span data-ttu-id="ccf29-162">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="ccf29-162">Maximum size</span></span> | <span data-ttu-id="ccf29-163">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="ccf29-163">Required</span></span> | <span data-ttu-id="ccf29-164">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ccf29-164">Description</span></span>|
|---|---|---|---|
|`short`|<span data-ttu-id="ccf29-165">30 Zeichen</span><span class="sxs-lookup"><span data-stu-id="ccf29-165">30 characters</span></span>|<span data-ttu-id="ccf29-166">✔</span><span class="sxs-lookup"><span data-stu-id="ccf29-166">✔</span></span>|<span data-ttu-id="ccf29-167">Der kurze Anzeigename für die app.</span><span class="sxs-lookup"><span data-stu-id="ccf29-167">The short display name for the app.</span></span>|
|`full`|<span data-ttu-id="ccf29-168">100 Zeichen</span><span class="sxs-lookup"><span data-stu-id="ccf29-168">100 characters</span></span>||<span data-ttu-id="ccf29-169">Der vollständige Name der APP, der verwendet wird, wenn der vollständige App-Name 30 Zeichen überschreitet.</span><span class="sxs-lookup"><span data-stu-id="ccf29-169">The full name of the app, used if the full app name exceeds 30 characters.</span></span>|

## <a name="description"></a><span data-ttu-id="ccf29-170">description</span><span class="sxs-lookup"><span data-stu-id="ccf29-170">description</span></span>

<span data-ttu-id="ccf29-171">**Erforderlich** – Objekt</span><span class="sxs-lookup"><span data-stu-id="ccf29-171">**Required** — object</span></span>

<span data-ttu-id="ccf29-172">Beschreibt die APP für Benutzer.</span><span class="sxs-lookup"><span data-stu-id="ccf29-172">Describes your app to users.</span></span> <span data-ttu-id="ccf29-173">Für apps, die an AppSource übermittelt werden, müssen diese Werte mit den Informationen in Ihrem AppSource-Eintrag übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="ccf29-173">For apps submitted to AppSource, these values must match the information in your AppSource entry.</span></span>

<span data-ttu-id="ccf29-174">Stellen Sie sicher, dass Ihre Beschreibung ihre Erfahrung genau beschreibt und Informationen bereitstellt, um potenziellen Kunden zu helfen, ihre Erfahrungen zu verstehen.</span><span class="sxs-lookup"><span data-stu-id="ccf29-174">Ensure that your description accurately describes your experience and provides information to help potential customers understand what your experience does.</span></span> <span data-ttu-id="ccf29-175">Beachten Sie auch, dass in der vollständigen Beschreibung ein externes Konto zur Verwendung benötigt wird.</span><span class="sxs-lookup"><span data-stu-id="ccf29-175">You should also note, in the full description, if an external account is required for use.</span></span> <span data-ttu-id="ccf29-176">Die Werte von `short` und `full` sollten nicht identisch sein.</span><span class="sxs-lookup"><span data-stu-id="ccf29-176">The values of `short` and `full` should not be the same.</span></span>  <span data-ttu-id="ccf29-177">Ihre Kurzbeschreibung darf nicht innerhalb der langen Beschreibung wiederholt werden und darf keinen anderen APP-Namen enthalten.</span><span class="sxs-lookup"><span data-stu-id="ccf29-177">Your short description must not be repeated within the long description and must not include any other app name.</span></span>

|<span data-ttu-id="ccf29-178">Name</span><span class="sxs-lookup"><span data-stu-id="ccf29-178">Name</span></span>| <span data-ttu-id="ccf29-179">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="ccf29-179">Maximum size</span></span> | <span data-ttu-id="ccf29-180">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="ccf29-180">Required</span></span> | <span data-ttu-id="ccf29-181">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ccf29-181">Description</span></span>|
|---|---|---|---|
|`short`|<span data-ttu-id="ccf29-182">80 Zeichen</span><span class="sxs-lookup"><span data-stu-id="ccf29-182">80 characters</span></span>|<span data-ttu-id="ccf29-183">✔</span><span class="sxs-lookup"><span data-stu-id="ccf29-183">✔</span></span>|<span data-ttu-id="ccf29-184">Eine kurze Beschreibung Ihrer APP-Erfahrung, die verwendet wird, wenn der Speicherplatz limitiert ist.</span><span class="sxs-lookup"><span data-stu-id="ccf29-184">A short description of your app experience, used when space is limited.</span></span>|
|`full`|<span data-ttu-id="ccf29-185">4000 Zeichen</span><span class="sxs-lookup"><span data-stu-id="ccf29-185">4000 characters</span></span>|<span data-ttu-id="ccf29-186">✔</span><span class="sxs-lookup"><span data-stu-id="ccf29-186">✔</span></span>|<span data-ttu-id="ccf29-187">Die vollständige Beschreibung Ihrer APP.</span><span class="sxs-lookup"><span data-stu-id="ccf29-187">The full description of your app.</span></span>|

## <a name="packagename"></a><span data-ttu-id="ccf29-188">PackageName</span><span class="sxs-lookup"><span data-stu-id="ccf29-188">packageName</span></span>

<span data-ttu-id="ccf29-189">**Optional** – Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="ccf29-189">**Optional** — string</span></span>

<span data-ttu-id="ccf29-190">Ein eindeutiger Bezeichner für diese APP in umgekehrter Domänen Notation; Beispiel: com. Beispiel. MyApp.</span><span class="sxs-lookup"><span data-stu-id="ccf29-190">A unique identifier for this app in reverse domain notation; for example, com.example.myapp.</span></span> <span data-ttu-id="ccf29-191">Maximale Länge: 64 Zeichen.</span><span class="sxs-lookup"><span data-stu-id="ccf29-191">Maximum length: 64 characters.</span></span>

## <a name="localizationinfo"></a><span data-ttu-id="ccf29-192">localizationInfo</span><span class="sxs-lookup"><span data-stu-id="ccf29-192">localizationInfo</span></span>

<span data-ttu-id="ccf29-193">**Optional** – Objekt</span><span class="sxs-lookup"><span data-stu-id="ccf29-193">**Optional** — object</span></span>

<span data-ttu-id="ccf29-194">Ermöglicht die Angabe einer Standardsprache sowie Zeiger auf zusätzliche Sprachdateien.</span><span class="sxs-lookup"><span data-stu-id="ccf29-194">Allows the specification of a default language, as well as pointers to additional language files.</span></span> <span data-ttu-id="ccf29-195">Siehe [Lokalisierung](~/concepts/build-and-test/apps-localization.md).</span><span class="sxs-lookup"><span data-stu-id="ccf29-195">See [localization](~/concepts/build-and-test/apps-localization.md).</span></span>

|<span data-ttu-id="ccf29-196">Name</span><span class="sxs-lookup"><span data-stu-id="ccf29-196">Name</span></span>| <span data-ttu-id="ccf29-197">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="ccf29-197">Maximum size</span></span> | <span data-ttu-id="ccf29-198">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="ccf29-198">Required</span></span> | <span data-ttu-id="ccf29-199">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ccf29-199">Description</span></span>|
|---|---|---|---|
|`defaultLanguageTag`||<span data-ttu-id="ccf29-200">✔</span><span class="sxs-lookup"><span data-stu-id="ccf29-200">✔</span></span>|<span data-ttu-id="ccf29-201">Das Language-Tag der Zeichenfolgen in dieser Manifestdatei der obersten Ebene.</span><span class="sxs-lookup"><span data-stu-id="ccf29-201">The language tag of the strings in this top level manifest file.</span></span>|

### <a name="localizationinfoadditionallanguages"></a><span data-ttu-id="ccf29-202">localizationInfo.additionalLanguages</span><span class="sxs-lookup"><span data-stu-id="ccf29-202">localizationInfo.additionalLanguages</span></span>

<span data-ttu-id="ccf29-203">Ein Array von Objekten, das zusätzliche Sprachübersetzungen angibt.</span><span class="sxs-lookup"><span data-stu-id="ccf29-203">An array of objects specifying additional language translations.</span></span>

|<span data-ttu-id="ccf29-204">Name</span><span class="sxs-lookup"><span data-stu-id="ccf29-204">Name</span></span>| <span data-ttu-id="ccf29-205">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="ccf29-205">Maximum size</span></span> | <span data-ttu-id="ccf29-206">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="ccf29-206">Required</span></span> | <span data-ttu-id="ccf29-207">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ccf29-207">Description</span></span>|
|---|---|---|---|
|`languageTag`||<span data-ttu-id="ccf29-208">✔</span><span class="sxs-lookup"><span data-stu-id="ccf29-208">✔</span></span>|<span data-ttu-id="ccf29-209">Das Language-Tag der Zeichenfolgen in der bereitgestellten Datei.</span><span class="sxs-lookup"><span data-stu-id="ccf29-209">The language tag of the strings in the provided file.</span></span>|
|`file`||<span data-ttu-id="ccf29-210">✔</span><span class="sxs-lookup"><span data-stu-id="ccf29-210">✔</span></span>|<span data-ttu-id="ccf29-211">Ein relativer Dateipfad zu einer JSON-Datei, die die übersetzten Zeichenfolgen enthält.</span><span class="sxs-lookup"><span data-stu-id="ccf29-211">A relative file path to a the .json file containing the translated strings.</span></span>|

## <a name="icons"></a><span data-ttu-id="ccf29-212">Symbole</span><span class="sxs-lookup"><span data-stu-id="ccf29-212">icons</span></span>

<span data-ttu-id="ccf29-213">**Erforderlich** – Objekt</span><span class="sxs-lookup"><span data-stu-id="ccf29-213">**Required** — object</span></span>

<span data-ttu-id="ccf29-214">Symbole, die in der Teams-App verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="ccf29-214">Icons used within the Teams app.</span></span> <span data-ttu-id="ccf29-215">Die Symboldateien müssen als Teil des Upload-Pakets enthalten sein.</span><span class="sxs-lookup"><span data-stu-id="ccf29-215">The icon files must be included as part of the upload package.</span></span> <span data-ttu-id="ccf29-216">Weitere Informationen finden Sie unter [Icons](~/concepts/build-and-test/apps-package.md#icons) .</span><span class="sxs-lookup"><span data-stu-id="ccf29-216">See [Icons](~/concepts/build-and-test/apps-package.md#icons) for more information.</span></span>

|<span data-ttu-id="ccf29-217">Name</span><span class="sxs-lookup"><span data-stu-id="ccf29-217">Name</span></span>| <span data-ttu-id="ccf29-218">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="ccf29-218">Maximum size</span></span> | <span data-ttu-id="ccf29-219">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="ccf29-219">Required</span></span> | <span data-ttu-id="ccf29-220">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ccf29-220">Description</span></span>|
|---|---|---|---|
|`outline`|<span data-ttu-id="ccf29-221">32 x 32 Pixel</span><span class="sxs-lookup"><span data-stu-id="ccf29-221">32 x 32 pixels</span></span>|<span data-ttu-id="ccf29-222">✔</span><span class="sxs-lookup"><span data-stu-id="ccf29-222">✔</span></span>|<span data-ttu-id="ccf29-223">Ein relativer Dateipfad zu einem transparenten 32x32 PNG-Gliederungssymbol.</span><span class="sxs-lookup"><span data-stu-id="ccf29-223">A relative file path to a transparent 32x32 PNG outline icon.</span></span>|
|`color`|<span data-ttu-id="ccf29-224">192 x 192 Pixel</span><span class="sxs-lookup"><span data-stu-id="ccf29-224">192 x 192 pixels</span></span>|<span data-ttu-id="ccf29-225">✔</span><span class="sxs-lookup"><span data-stu-id="ccf29-225">✔</span></span>|<span data-ttu-id="ccf29-226">Ein relativer Dateipfad zu einem vollfarbigen 192x192 PNG-Symbol.</span><span class="sxs-lookup"><span data-stu-id="ccf29-226">A relative file path to a full color 192x192 PNG icon.</span></span>|

## <a name="accentcolor"></a><span data-ttu-id="ccf29-227">accentColor</span><span class="sxs-lookup"><span data-stu-id="ccf29-227">accentColor</span></span>

<span data-ttu-id="ccf29-228">**Optional** – HTML-Hex-Farbcode</span><span class="sxs-lookup"><span data-stu-id="ccf29-228">**Optional** — HTML Hex color code</span></span>

<span data-ttu-id="ccf29-229">Eine Farbe, die in Verbindung mit und als Hintergrund für die Gliederungssymbole verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="ccf29-229">A color to use in conjunction with and as a background for your outline icons.</span></span>

<span data-ttu-id="ccf29-230">Der Wert muss ein gültiger HTML-Farb Code sein, der mit "#" beginnt, beispielsweise `#4464ee` .</span><span class="sxs-lookup"><span data-stu-id="ccf29-230">The value must be a valid HTML color code starting with '#', for example `#4464ee`.</span></span>

## <a name="configurabletabs"></a><span data-ttu-id="ccf29-231">configurableTabs</span><span class="sxs-lookup"><span data-stu-id="ccf29-231">configurableTabs</span></span>

<span data-ttu-id="ccf29-232">**Optional** – Array</span><span class="sxs-lookup"><span data-stu-id="ccf29-232">**Optional** — array</span></span>

<span data-ttu-id="ccf29-233">Wird verwendet, wenn Ihre APP-Erfahrung eine Team Kanal-registerkartenoberfläche aufweist, die eine zusätzliche Konfiguration erfordert, bevor Sie hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="ccf29-233">Used when your app experience has a team channel tab experience that requires extra configuration before it is added.</span></span> <span data-ttu-id="ccf29-234">Konfigurierbare Registerkarten werden nur im Bereich Teams (nicht persönlich) unterstützt, und derzeit wird nur **eine** Registerkarte pro App unterstützt.</span><span class="sxs-lookup"><span data-stu-id="ccf29-234">Configurable tabs are supported only in the teams scope (not personal), and currently only **one** tab per app is supported.</span></span>

|<span data-ttu-id="ccf29-235">Name</span><span class="sxs-lookup"><span data-stu-id="ccf29-235">Name</span></span>| <span data-ttu-id="ccf29-236">Typ</span><span class="sxs-lookup"><span data-stu-id="ccf29-236">Type</span></span>| <span data-ttu-id="ccf29-237">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="ccf29-237">Maximum size</span></span> | <span data-ttu-id="ccf29-238">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="ccf29-238">Required</span></span> | <span data-ttu-id="ccf29-239">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ccf29-239">Description</span></span>|
|---|---|---|---|---|
|`configurationUrl`|<span data-ttu-id="ccf29-240">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="ccf29-240">string</span></span>|<span data-ttu-id="ccf29-241">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="ccf29-241">2048 characters</span></span>|<span data-ttu-id="ccf29-242">✔</span><span class="sxs-lookup"><span data-stu-id="ccf29-242">✔</span></span>|<span data-ttu-id="ccf29-243">Die https://-URL, die beim Konfigurieren der Registerkarte verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="ccf29-243">The https:// URL to use when configuring the tab.</span></span>|
|`scopes`|<span data-ttu-id="ccf29-244">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="ccf29-244">array of enums</span></span>|<span data-ttu-id="ccf29-245">1</span><span class="sxs-lookup"><span data-stu-id="ccf29-245">1</span></span>|<span data-ttu-id="ccf29-246">✔</span><span class="sxs-lookup"><span data-stu-id="ccf29-246">✔</span></span>|<span data-ttu-id="ccf29-247">Derzeit unterstützen konfigurierbare Registerkarten nur die `team` `groupchat` Bereiche und.</span><span class="sxs-lookup"><span data-stu-id="ccf29-247">Currently, configurable tabs support only the `team` and `groupchat` scopes.</span></span> |
|`canUpdateConfiguration`|<span data-ttu-id="ccf29-248">Boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="ccf29-248">boolean</span></span>|||<span data-ttu-id="ccf29-249">Ein Wert, der angibt, ob eine Instanz der Konfiguration der Registerkarte nach der Erstellung vom Benutzer aktualisiert werden kann.</span><span class="sxs-lookup"><span data-stu-id="ccf29-249">A value indicating whether an instance of the tab's configuration can be updated by the user after creation.</span></span> <span data-ttu-id="ccf29-250">Default: **true**.</span><span class="sxs-lookup"><span data-stu-id="ccf29-250">Default: **true**.</span></span>|
|`context` |<span data-ttu-id="ccf29-251">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="ccf29-251">array of enums</span></span>|<span data-ttu-id="ccf29-252">6 </span><span class="sxs-lookup"><span data-stu-id="ccf29-252">6</span></span>||<span data-ttu-id="ccf29-253">Die Gruppe von `contextItem` Bereichen, in denen eine Registerkarte unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="ccf29-253">The set of `contextItem` scopes where a tab is supported.</span></span> <span data-ttu-id="ccf29-254">Standardwert: **[channelTab, privateChatTab, meetingChatTab, meetingDetailsTab]**.</span><span class="sxs-lookup"><span data-stu-id="ccf29-254">Default: **[channelTab, privateChatTab, meetingChatTab, meetingDetailsTab]**.</span></span>|
|`sharePointPreviewImage`|<span data-ttu-id="ccf29-255">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="ccf29-255">string</span></span>|<span data-ttu-id="ccf29-256">2048</span><span class="sxs-lookup"><span data-stu-id="ccf29-256">2048</span></span>||<span data-ttu-id="ccf29-257">Ein relativer Dateipfad zu einem Vorschaubild für die Registerkarte für die Verwendung in SharePoint.</span><span class="sxs-lookup"><span data-stu-id="ccf29-257">A relative file path to a tab preview image for use in SharePoint.</span></span> <span data-ttu-id="ccf29-258">Größe 1024x768.</span><span class="sxs-lookup"><span data-stu-id="ccf29-258">Size 1024x768.</span></span> |
|`supportedSharePointHosts`|<span data-ttu-id="ccf29-259">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="ccf29-259">array of enums</span></span>|<span data-ttu-id="ccf29-260">1</span><span class="sxs-lookup"><span data-stu-id="ccf29-260">1</span></span>||<span data-ttu-id="ccf29-261">Definiert, wie die Registerkarte in SharePoint zur Verfügung gestellt wird.</span><span class="sxs-lookup"><span data-stu-id="ccf29-261">Defines how your tab will be made available in SharePoint.</span></span> <span data-ttu-id="ccf29-262">Optionen sind `sharePointFullPage` und `sharePointWebPart`</span><span class="sxs-lookup"><span data-stu-id="ccf29-262">Options are `sharePointFullPage` and `sharePointWebPart`</span></span> |

## <a name="statictabs"></a><span data-ttu-id="ccf29-263">staticTabs</span><span class="sxs-lookup"><span data-stu-id="ccf29-263">staticTabs</span></span>

<span data-ttu-id="ccf29-264">**Optional** – Array</span><span class="sxs-lookup"><span data-stu-id="ccf29-264">**Optional** — array</span></span>

<span data-ttu-id="ccf29-265">Definiert eine Gruppe von Registerkarten, die standardmäßig "fixiert" werden können, ohne dass der Benutzer Sie manuell hinzufügt.</span><span class="sxs-lookup"><span data-stu-id="ccf29-265">Defines a set of tabs that can be "pinned" by default, without the user adding them manually.</span></span> <span data-ttu-id="ccf29-266">Im Bereich deklarierte statische Registerkarten `personal` werden immer an die persönliche Benutzeroberfläche der APP angeheftet.</span><span class="sxs-lookup"><span data-stu-id="ccf29-266">Static tabs declared in `personal` scope are always pinned to the app's personal experience.</span></span> <span data-ttu-id="ccf29-267">Im Bereich deklarierte statische Registerkarten `team` werden derzeit nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="ccf29-267">Static tabs declared in the `team` scope are currently not supported.</span></span>

<span data-ttu-id="ccf29-268">Dieses Element ist ein Array (maximal 16 Elemente) mit allen Elementen des Typs `object` .</span><span class="sxs-lookup"><span data-stu-id="ccf29-268">This item is an array (maximum of 16 elements) with all elements of the type `object`.</span></span> <span data-ttu-id="ccf29-269">Dieser Block ist nur für Lösungen erforderlich, die eine statische Registerkarten Lösung bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="ccf29-269">This block is required only for solutions that provide a static tab solution.</span></span>

|<span data-ttu-id="ccf29-270">Name</span><span class="sxs-lookup"><span data-stu-id="ccf29-270">Name</span></span>| <span data-ttu-id="ccf29-271">Typ</span><span class="sxs-lookup"><span data-stu-id="ccf29-271">Type</span></span>| <span data-ttu-id="ccf29-272">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="ccf29-272">Maximum size</span></span> | <span data-ttu-id="ccf29-273">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="ccf29-273">Required</span></span> | <span data-ttu-id="ccf29-274">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ccf29-274">Description</span></span>|
|---|---|---|---|---|
|`entityId`|<span data-ttu-id="ccf29-275">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="ccf29-275">string</span></span>|<span data-ttu-id="ccf29-276">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="ccf29-276">64 characters</span></span>|<span data-ttu-id="ccf29-277">✔</span><span class="sxs-lookup"><span data-stu-id="ccf29-277">✔</span></span>|<span data-ttu-id="ccf29-278">Ein eindeutiger Bezeichner für die Entität, die auf der Registerkarte angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="ccf29-278">A unique identifier for the entity that the tab displays.</span></span>|
|`name`|<span data-ttu-id="ccf29-279">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="ccf29-279">string</span></span>|<span data-ttu-id="ccf29-280">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="ccf29-280">128 characters</span></span>|<span data-ttu-id="ccf29-281">✔</span><span class="sxs-lookup"><span data-stu-id="ccf29-281">✔</span></span>|<span data-ttu-id="ccf29-282">Der Anzeigename der Registerkarte in der Kanalschnittstelle.</span><span class="sxs-lookup"><span data-stu-id="ccf29-282">The display name of the tab in the channel interface.</span></span>|
|`contentUrl`|<span data-ttu-id="ccf29-283">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="ccf29-283">string</span></span>||<span data-ttu-id="ccf29-284">✔</span><span class="sxs-lookup"><span data-stu-id="ccf29-284">✔</span></span>|<span data-ttu-id="ccf29-285">Die https://-URL, die auf die Benutzeroberfläche der Entität zeigt, die im Canvas "Teams" angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="ccf29-285">The https:// URL that points to the entity UI to be displayed in the Teams canvas.</span></span>|
|`websiteUrl`|<span data-ttu-id="ccf29-286">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="ccf29-286">string</span></span>|||<span data-ttu-id="ccf29-287">Die https://-URL, auf die verwiesen wird, wenn ein Benutzer sich für die Anzeige in einem Browser entscheidet.</span><span class="sxs-lookup"><span data-stu-id="ccf29-287">The https:// URL to point to if a user opts to view in a browser.</span></span>|
|`searchUrl`|<span data-ttu-id="ccf29-288">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="ccf29-288">string</span></span>|||<span data-ttu-id="ccf29-289">Die https://-URL, auf die für Suchabfragen eines Benutzers verwiesen wird.</span><span class="sxs-lookup"><span data-stu-id="ccf29-289">The https:// URL to point to for a user's search queries.</span></span>|
|`scopes`|<span data-ttu-id="ccf29-290">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="ccf29-290">array of enums</span></span>|<span data-ttu-id="ccf29-291">1</span><span class="sxs-lookup"><span data-stu-id="ccf29-291">1</span></span>|<span data-ttu-id="ccf29-292">✔</span><span class="sxs-lookup"><span data-stu-id="ccf29-292">✔</span></span>|<span data-ttu-id="ccf29-293">Derzeit unterstützen statische Registerkarten nur den `personal` Bereich, was bedeutet, dass Sie nur als Teil der persönlichen Benutzeroberfläche vorgesehen werden kann.</span><span class="sxs-lookup"><span data-stu-id="ccf29-293">Currently, static tabs support only the `personal` scope, which means it can be provisioned only as part of the personal experience.</span></span>|
|`context` | <span data-ttu-id="ccf29-294">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="ccf29-294">array of enums</span></span>| <span data-ttu-id="ccf29-295">2</span><span class="sxs-lookup"><span data-stu-id="ccf29-295">2</span></span>|| <span data-ttu-id="ccf29-296">Die Gruppe von `contextItem` Bereichen, in denen eine Registerkarte unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="ccf29-296">The set of `contextItem` scopes where a tab is supported.</span></span>|

> [!NOTE]
> <span data-ttu-id="ccf29-297">Wenn auf Ihren Registerkartenkontext abhängige Informationen zum Anzeigen relevanter Inhalte oder zum Initiieren eines Authentifizierungs Flusses erforderlich sind, *Lesen Sie* den [Bereich Kontext für Ihre Microsoft Teams-Registerkarte abrufen](../../tabs/how-to/access-teams-context.md).</span><span class="sxs-lookup"><span data-stu-id="ccf29-297">If your tabs require context-dependent information to display relevant content or for initiating an authentication flow, *see* [Get context for your Microsoft Teams tab](../../tabs/how-to/access-teams-context.md).</span></span>

## <a name="bots"></a><span data-ttu-id="ccf29-298">Bots</span><span class="sxs-lookup"><span data-stu-id="ccf29-298">bots</span></span>

<span data-ttu-id="ccf29-299">**Optional** – Array</span><span class="sxs-lookup"><span data-stu-id="ccf29-299">**Optional** — array</span></span>

<span data-ttu-id="ccf29-300">Definiert eine bot-Lösung zusammen mit optionalen Informationen wie Standardbefehls Eigenschaften.</span><span class="sxs-lookup"><span data-stu-id="ccf29-300">Defines a bot solution, along with optional information such as default command properties.</span></span>

<span data-ttu-id="ccf29-301">Das Element ist ein Array (Maximum von nur 1 Element &mdash; , das derzeit nur ein bot pro App zulässig ist) mit allen Elementen des Typs `object` .</span><span class="sxs-lookup"><span data-stu-id="ccf29-301">The item is an array (maximum of only 1 element&mdash;currently only one bot is allowed per app) with all elements of the type `object`.</span></span> <span data-ttu-id="ccf29-302">Dieser Block ist nur für Lösungen erforderlich, die eine bot-Erfahrung bieten.</span><span class="sxs-lookup"><span data-stu-id="ccf29-302">This block is required only for solutions that provide a bot experience.</span></span>

|<span data-ttu-id="ccf29-303">Name</span><span class="sxs-lookup"><span data-stu-id="ccf29-303">Name</span></span>| <span data-ttu-id="ccf29-304">Typ</span><span class="sxs-lookup"><span data-stu-id="ccf29-304">Type</span></span>| <span data-ttu-id="ccf29-305">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="ccf29-305">Maximum size</span></span> | <span data-ttu-id="ccf29-306">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="ccf29-306">Required</span></span> | <span data-ttu-id="ccf29-307">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ccf29-307">Description</span></span>|
|---|---|---|---|---|
|`botId`|<span data-ttu-id="ccf29-308">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="ccf29-308">string</span></span>|<span data-ttu-id="ccf29-309">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="ccf29-309">64 characters</span></span>|<span data-ttu-id="ccf29-310">✔</span><span class="sxs-lookup"><span data-stu-id="ccf29-310">✔</span></span>|<span data-ttu-id="ccf29-311">Die eindeutige Microsoft-App-ID für den Bot, wie bei Bot Framework registriert.</span><span class="sxs-lookup"><span data-stu-id="ccf29-311">The unique Microsoft app ID for the bot as registered with the Bot Framework.</span></span> <span data-ttu-id="ccf29-312">Dies kann auch die gesamte [App-ID](#id)entsprechen.</span><span class="sxs-lookup"><span data-stu-id="ccf29-312">This may well be the same as the overall [app ID](#id).</span></span>|
|`scopes`|<span data-ttu-id="ccf29-313">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="ccf29-313">array of enums</span></span>|<span data-ttu-id="ccf29-314">3</span><span class="sxs-lookup"><span data-stu-id="ccf29-314">3</span></span>|<span data-ttu-id="ccf29-315">✔</span><span class="sxs-lookup"><span data-stu-id="ccf29-315">✔</span></span>|<span data-ttu-id="ccf29-316">Gibt an, ob der Bot eine Umgebung im Kontext eines Kanals in einem `team` oder Gruppenchat (`groupchat`) ist, oder aber eine Umgebung einzig für einen bestimmten Benutzer (`personal`).</span><span class="sxs-lookup"><span data-stu-id="ccf29-316">Specifies whether the bot offers an experience in the context of a channel in a `team`, in a group chat (`groupchat`), or an experience scoped to an individual user alone (`personal`).</span></span> <span data-ttu-id="ccf29-317">Diese Optionen sind nicht exklusiv.</span><span class="sxs-lookup"><span data-stu-id="ccf29-317">These options are non-exclusive.</span></span>|
|`needsChannelSelector`|<span data-ttu-id="ccf29-318">Boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="ccf29-318">boolean</span></span>|||<span data-ttu-id="ccf29-319">Beschreibt, ob der Bot einen Benutzerhinweis verwendet, um den Bot einem bestimmten Kanal hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="ccf29-319">Describes whether or not the bot utilizes a user hint to add the bot to a specific channel.</span></span> <span data-ttu-id="ccf29-320">Standard **`false`**</span><span class="sxs-lookup"><span data-stu-id="ccf29-320">Default: **`false`**</span></span>|
|`isNotificationOnly`|<span data-ttu-id="ccf29-321">Boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="ccf29-321">boolean</span></span>|||<span data-ttu-id="ccf29-322">Gibt an, ob ein Bot ein unidirektionaler Bot ausschließlich für Benachrichtigungen ist (im Gegensatz zu einem dialogorientierten Bot).</span><span class="sxs-lookup"><span data-stu-id="ccf29-322">Indicates whether a bot is a one-way, notification-only bot, as opposed to a conversational bot.</span></span> <span data-ttu-id="ccf29-323">Standard `**false**`</span><span class="sxs-lookup"><span data-stu-id="ccf29-323">Default: `**false**`</span></span>|
|`supportsFiles`|<span data-ttu-id="ccf29-324">Boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="ccf29-324">boolean</span></span>|||<span data-ttu-id="ccf29-325">Gibt an, ob der Bot die Möglichkeit zum Hochladen/Herunterladen von Dateien in persönliche Chats unterstützt.</span><span class="sxs-lookup"><span data-stu-id="ccf29-325">Indicates whether the bot supports the ability to upload/download files in personal chat.</span></span> <span data-ttu-id="ccf29-326">Standard **`false`**</span><span class="sxs-lookup"><span data-stu-id="ccf29-326">Default: **`false`**</span></span>|
|`supportsCalling`|<span data-ttu-id="ccf29-327">Boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="ccf29-327">boolean</span></span>|||<span data-ttu-id="ccf29-328">Ein Wert, der angibt, wo ein bot Audio-Anrufe unterstützt.</span><span class="sxs-lookup"><span data-stu-id="ccf29-328">A value indicating where a bot supports audio calling.</span></span> <span data-ttu-id="ccf29-329">**Wichtig**: Diese Eigenschaft ist derzeit experimentell.</span><span class="sxs-lookup"><span data-stu-id="ccf29-329">**IMPORTANT**: This property is currently experimental.</span></span> <span data-ttu-id="ccf29-330">Experimentelle Eigenschaften sind möglicherweise nicht vollständig und können Änderungen unterzogen werden, bevor Sie vollständig verfügbar werden.</span><span class="sxs-lookup"><span data-stu-id="ccf29-330">Experimental properties may not be complete, and may undergo changes before becoming fully available.</span></span>  <span data-ttu-id="ccf29-331">Sie wird nur zu Test-und Explorations Zwecken bereitgestellt und sollte nicht in Produktionsanwendungen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="ccf29-331">It is provided for testing and exploration purposes only and should not be used in production applications.</span></span> <span data-ttu-id="ccf29-332">Standard **`false`**</span><span class="sxs-lookup"><span data-stu-id="ccf29-332">Default: **`false`**</span></span>|
|`supportsVideo`|<span data-ttu-id="ccf29-333">Boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="ccf29-333">boolean</span></span>|||<span data-ttu-id="ccf29-334">Ein Wert, der angibt, wo ein bot Videoanrufe unterstützt.</span><span class="sxs-lookup"><span data-stu-id="ccf29-334">A value indicating where a bot supports video calling.</span></span> <span data-ttu-id="ccf29-335">**Wichtig**: Diese Eigenschaft ist derzeit experimentell.</span><span class="sxs-lookup"><span data-stu-id="ccf29-335">**IMPORTANT**: This property is currently experimental.</span></span> <span data-ttu-id="ccf29-336">Experimentelle Eigenschaften sind möglicherweise nicht vollständig und können Änderungen unterzogen werden, bevor Sie vollständig verfügbar werden.</span><span class="sxs-lookup"><span data-stu-id="ccf29-336">Experimental properties may not be complete, and may undergo changes before becoming fully available.</span></span>  <span data-ttu-id="ccf29-337">Sie wird nur zu Test-und Explorations Zwecken bereitgestellt und sollte nicht in Produktionsanwendungen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="ccf29-337">It is provided for testing and exploration purposes only and should not be used in production applications.</span></span> <span data-ttu-id="ccf29-338">Standard **`false`**</span><span class="sxs-lookup"><span data-stu-id="ccf29-338">Default: **`false`**</span></span>|

### <a name="botscommandlists"></a><span data-ttu-id="ccf29-339">Bots. commandLists</span><span class="sxs-lookup"><span data-stu-id="ccf29-339">bots.commandLists</span></span>

<span data-ttu-id="ccf29-340">Eine optionale Liste von Befehlen, die ihr bot Benutzern empfehlen kann.</span><span class="sxs-lookup"><span data-stu-id="ccf29-340">An optional list of commands that your bot can recommend to users.</span></span> <span data-ttu-id="ccf29-341">Das Objekt ist ein Array (Maximum von 2 Elementen) mit allen Elementen des Typs `object` ; Sie müssen für jeden Bereich, den Ihr bot unterstützt, eine separate Befehlsliste definieren.</span><span class="sxs-lookup"><span data-stu-id="ccf29-341">The object is an array (maximum of 2 elements) with all elements of type `object`; you must define a separate command list for each scope that your bot supports.</span></span> <span data-ttu-id="ccf29-342">Weitere Informationen finden Sie unter [bot-Menüs](~/bots/how-to/create-a-bot-commands-menu.md) .</span><span class="sxs-lookup"><span data-stu-id="ccf29-342">See [Bot menus](~/bots/how-to/create-a-bot-commands-menu.md) for more information.</span></span>

|<span data-ttu-id="ccf29-343">Name</span><span class="sxs-lookup"><span data-stu-id="ccf29-343">Name</span></span>| <span data-ttu-id="ccf29-344">Typ</span><span class="sxs-lookup"><span data-stu-id="ccf29-344">Type</span></span>| <span data-ttu-id="ccf29-345">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="ccf29-345">Maximum size</span></span> | <span data-ttu-id="ccf29-346">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="ccf29-346">Required</span></span> | <span data-ttu-id="ccf29-347">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ccf29-347">Description</span></span>|
|---|---|---|---|---|
|`items.scopes`|<span data-ttu-id="ccf29-348">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="ccf29-348">array of enums</span></span>|<span data-ttu-id="ccf29-349">3</span><span class="sxs-lookup"><span data-stu-id="ccf29-349">3</span></span>|<span data-ttu-id="ccf29-350">✔</span><span class="sxs-lookup"><span data-stu-id="ccf29-350">✔</span></span>|<span data-ttu-id="ccf29-351">Gibt den Bereich an, für den die Befehlsliste gültig ist.</span><span class="sxs-lookup"><span data-stu-id="ccf29-351">Specifies the scope for which the command list is valid.</span></span> <span data-ttu-id="ccf29-352">Mögliche Optionen sind `team`, `personal` und `groupchat`.</span><span class="sxs-lookup"><span data-stu-id="ccf29-352">Options are `team`, `personal`, and `groupchat`.</span></span>|
|`items.commands`|<span data-ttu-id="ccf29-353">Array von Objekten</span><span class="sxs-lookup"><span data-stu-id="ccf29-353">array of objects</span></span>|<span data-ttu-id="ccf29-354">10 </span><span class="sxs-lookup"><span data-stu-id="ccf29-354">10</span></span>|<span data-ttu-id="ccf29-355">✔</span><span class="sxs-lookup"><span data-stu-id="ccf29-355">✔</span></span>|<span data-ttu-id="ccf29-356">Ein Array von Befehlen, die der Bot unterstützt:</span><span class="sxs-lookup"><span data-stu-id="ccf29-356">An array of commands the bot supports:</span></span><br><span data-ttu-id="ccf29-357">`title`: Name des Bot-Befehls (string, 32)</span><span class="sxs-lookup"><span data-stu-id="ccf29-357">`title`: the bot command name (string, 32)</span></span><br><span data-ttu-id="ccf29-358">`description`: einfache Beschreibung oder Beispiel für die Befehlssyntax und zugehörige Argumente (string, 128)</span><span class="sxs-lookup"><span data-stu-id="ccf29-358">`description`: a simple description or example of the command syntax and its argument (string, 128)</span></span>|

### <a name="botscommandlistscommands"></a><span data-ttu-id="ccf29-359">Bots. commandLists. Commands</span><span class="sxs-lookup"><span data-stu-id="ccf29-359">bots.commandLists.commands</span></span>

|<span data-ttu-id="ccf29-360">Name</span><span class="sxs-lookup"><span data-stu-id="ccf29-360">Name</span></span>| <span data-ttu-id="ccf29-361">Typ</span><span class="sxs-lookup"><span data-stu-id="ccf29-361">Type</span></span>| <span data-ttu-id="ccf29-362">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="ccf29-362">Maximum size</span></span> | <span data-ttu-id="ccf29-363">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="ccf29-363">Required</span></span> | <span data-ttu-id="ccf29-364">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ccf29-364">Description</span></span>|
|---|---|---|---|---|
|<span data-ttu-id="ccf29-365">title</span><span class="sxs-lookup"><span data-stu-id="ccf29-365">title</span></span>|<span data-ttu-id="ccf29-366">string</span><span class="sxs-lookup"><span data-stu-id="ccf29-366">string</span></span>|<span data-ttu-id="ccf29-367">12 </span><span class="sxs-lookup"><span data-stu-id="ccf29-367">12</span></span>|<span data-ttu-id="ccf29-368">✔</span><span class="sxs-lookup"><span data-stu-id="ccf29-368">✔</span></span>|<span data-ttu-id="ccf29-369">Der Name des bot-Befehls</span><span class="sxs-lookup"><span data-stu-id="ccf29-369">The bot command name</span></span>|
|<span data-ttu-id="ccf29-370">description</span><span class="sxs-lookup"><span data-stu-id="ccf29-370">description</span></span>|<span data-ttu-id="ccf29-371">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="ccf29-371">string</span></span>|<span data-ttu-id="ccf29-372">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="ccf29-372">128 characters</span></span>|<span data-ttu-id="ccf29-373">✔</span><span class="sxs-lookup"><span data-stu-id="ccf29-373">✔</span></span>|<span data-ttu-id="ccf29-374">Eine einfache Textbeschreibung oder ein Beispiel für die Befehlssyntax und ihre Argumente.</span><span class="sxs-lookup"><span data-stu-id="ccf29-374">A simple text description or an example of the command syntax and its arguments.</span></span>|

## <a name="connectors"></a><span data-ttu-id="ccf29-375">Connectors</span><span class="sxs-lookup"><span data-stu-id="ccf29-375">connectors</span></span>

<span data-ttu-id="ccf29-376">**Optional** – Array</span><span class="sxs-lookup"><span data-stu-id="ccf29-376">**Optional** — array</span></span>

<span data-ttu-id="ccf29-377">Der `connectors` Block definiert einen Office 365-Konnektor für die app.</span><span class="sxs-lookup"><span data-stu-id="ccf29-377">The `connectors` block defines an Office 365 Connector for the app.</span></span>

<span data-ttu-id="ccf29-378">Das Objekt ist ein Array (Maximum of 1-Element) mit allen Elementen des Typs `object` .</span><span class="sxs-lookup"><span data-stu-id="ccf29-378">The object is an array (maximum of 1 element) with all elements of type `object`.</span></span> <span data-ttu-id="ccf29-379">Dieser Block ist nur für Lösungen erforderlich, die einen Connector bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="ccf29-379">This block is required only for solutions that provide a Connector.</span></span>

|<span data-ttu-id="ccf29-380">Name</span><span class="sxs-lookup"><span data-stu-id="ccf29-380">Name</span></span>| <span data-ttu-id="ccf29-381">Typ</span><span class="sxs-lookup"><span data-stu-id="ccf29-381">Type</span></span>| <span data-ttu-id="ccf29-382">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="ccf29-382">Maximum size</span></span> | <span data-ttu-id="ccf29-383">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="ccf29-383">Required</span></span> | <span data-ttu-id="ccf29-384">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ccf29-384">Description</span></span>|
|---|---|---|---|---|
|`configurationUrl`|<span data-ttu-id="ccf29-385">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="ccf29-385">string</span></span>|<span data-ttu-id="ccf29-386">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="ccf29-386">2048 characters</span></span>|<span data-ttu-id="ccf29-387">✔</span><span class="sxs-lookup"><span data-stu-id="ccf29-387">✔</span></span>|<span data-ttu-id="ccf29-388">Die https://-URL, die beim Konfigurieren des Connectors verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="ccf29-388">The https:// URL to use when configuring the connector.</span></span>|
|`scopes`|<span data-ttu-id="ccf29-389">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="ccf29-389">array of enums</span></span>|<span data-ttu-id="ccf29-390">1</span><span class="sxs-lookup"><span data-stu-id="ccf29-390">1</span></span>|<span data-ttu-id="ccf29-391">✔</span><span class="sxs-lookup"><span data-stu-id="ccf29-391">✔</span></span>|<span data-ttu-id="ccf29-392">Gibt an, ob der Connector eine Erfahrung im Kontext eines Kanals in a bietet `team` oder ein Erlebnis, das allein auf einen einzelnen Benutzer beschränkt ist ( `personal` ).</span><span class="sxs-lookup"><span data-stu-id="ccf29-392">Specifies whether the Connector offers an experience in the context of a channel in a `team`, or an experience scoped to an individual user alone (`personal`).</span></span> <span data-ttu-id="ccf29-393">Derzeit wird nur der `team` Bereich unterstützt.</span><span class="sxs-lookup"><span data-stu-id="ccf29-393">Currently, only the `team` scope is supported.</span></span>|
|`connectorId`|<span data-ttu-id="ccf29-394">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="ccf29-394">string</span></span>|<span data-ttu-id="ccf29-395">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="ccf29-395">64 characters</span></span>|<span data-ttu-id="ccf29-396">✔</span><span class="sxs-lookup"><span data-stu-id="ccf29-396">✔</span></span>|<span data-ttu-id="ccf29-397">Ein eindeutiger Bezeichner für den Connector, der seiner ID im [Entwickler Dashboard für Connectors](https://aka.ms/connectorsdashboard)entspricht.</span><span class="sxs-lookup"><span data-stu-id="ccf29-397">A unique identifier for the Connector that matches its ID in the [Connectors Developer Dashboard](https://aka.ms/connectorsdashboard).</span></span>|

## <a name="composeextensions"></a><span data-ttu-id="ccf29-398">composeExtensions</span><span class="sxs-lookup"><span data-stu-id="ccf29-398">composeExtensions</span></span>

<span data-ttu-id="ccf29-399">**Optional** – Array</span><span class="sxs-lookup"><span data-stu-id="ccf29-399">**Optional** — array</span></span>

<span data-ttu-id="ccf29-400">Definiert eine Messaging Erweiterung für die app.</span><span class="sxs-lookup"><span data-stu-id="ccf29-400">Defines a messaging extension for the app.</span></span>

> [!NOTE]
> <span data-ttu-id="ccf29-401">Der Name des Features wurde von "Erstell Erweiterung" in "Messaging Extension" im November 2017 geändert, aber der Manifestname bleibt unverändert, sodass vorhandene Erweiterungen weiterhin funktionieren.</span><span class="sxs-lookup"><span data-stu-id="ccf29-401">The name of the feature was changed from "compose extension" to "messaging extension" in November, 2017, but the manifest name remains the same so that existing extensions continue to function.</span></span>

<span data-ttu-id="ccf29-402">Das Element ist ein Array (Maximum of 1-Element) mit allen Elementen des Typs `object` .</span><span class="sxs-lookup"><span data-stu-id="ccf29-402">The item is an array (maximum of 1 element) with all elements of type `object`.</span></span> <span data-ttu-id="ccf29-403">Dieser Block ist nur für Lösungen erforderlich, die eine Messaging Erweiterung bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="ccf29-403">This block is required only for solutions that provide a messaging extension.</span></span>

|<span data-ttu-id="ccf29-404">Name</span><span class="sxs-lookup"><span data-stu-id="ccf29-404">Name</span></span>| <span data-ttu-id="ccf29-405">Typ</span><span class="sxs-lookup"><span data-stu-id="ccf29-405">Type</span></span> | <span data-ttu-id="ccf29-406">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="ccf29-406">Maximum Size</span></span> | <span data-ttu-id="ccf29-407">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="ccf29-407">Required</span></span> | <span data-ttu-id="ccf29-408">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ccf29-408">Description</span></span>|
|---|---|---|---|---|
|`botId`|<span data-ttu-id="ccf29-409">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="ccf29-409">string</span></span>|<span data-ttu-id="ccf29-410">64</span><span class="sxs-lookup"><span data-stu-id="ccf29-410">64</span></span>|<span data-ttu-id="ccf29-411">✔</span><span class="sxs-lookup"><span data-stu-id="ccf29-411">✔</span></span>|<span data-ttu-id="ccf29-412">Die eindeutige Microsoft-App-ID für den bot, der die Messaging Erweiterung unterstützt, wie Sie mit dem bot-Framework registriert wurde.</span><span class="sxs-lookup"><span data-stu-id="ccf29-412">The unique Microsoft app ID for the bot that backs the messaging extension, as registered with the Bot Framework.</span></span> <span data-ttu-id="ccf29-413">Dies kann auch die gesamte APP-ID entsprechen.</span><span class="sxs-lookup"><span data-stu-id="ccf29-413">This may well be the same as the overall App ID.</span></span>|
|`commands`|<span data-ttu-id="ccf29-414">Array von Objekten</span><span class="sxs-lookup"><span data-stu-id="ccf29-414">array of objects</span></span>|<span data-ttu-id="ccf29-415">10 </span><span class="sxs-lookup"><span data-stu-id="ccf29-415">10</span></span>|<span data-ttu-id="ccf29-416">✔</span><span class="sxs-lookup"><span data-stu-id="ccf29-416">✔</span></span>|<span data-ttu-id="ccf29-417">Array von Befehlen, die von der Messaging-Erweiterung unterstützt werden</span><span class="sxs-lookup"><span data-stu-id="ccf29-417">array of commands the messaging extension supports</span></span>|
|`canUpdateConfiguration`|<span data-ttu-id="ccf29-418">Boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="ccf29-418">boolean</span></span>|||<span data-ttu-id="ccf29-419">Ein Wert, der angibt, ob die Konfiguration einer Messaging Erweiterung vom Benutzer aktualisiert werden kann.</span><span class="sxs-lookup"><span data-stu-id="ccf29-419">A value indicating whether the configuration of a messaging extension can be updated by the user.</span></span> <span data-ttu-id="ccf29-420">Standard: **False**.</span><span class="sxs-lookup"><span data-stu-id="ccf29-420">Default: **false**.</span></span>|
|`messageHandlers`|<span data-ttu-id="ccf29-421">Array von Objekten</span><span class="sxs-lookup"><span data-stu-id="ccf29-421">array of Objects</span></span>|<span data-ttu-id="ccf29-422">5 </span><span class="sxs-lookup"><span data-stu-id="ccf29-422">5</span></span>||<span data-ttu-id="ccf29-423">Eine Liste von Handlern, mit denen apps aufgerufen werden können, wenn bestimmte Bedingungen erfüllt sind.</span><span class="sxs-lookup"><span data-stu-id="ccf29-423">A list of handlers that allow apps to be invoked when certain conditions are met.</span></span> <span data-ttu-id="ccf29-424">Domänen müssen ebenfalls in aufgeführt sein. `validDomains`</span><span class="sxs-lookup"><span data-stu-id="ccf29-424">Domains must also be listed in `validDomains`</span></span>|
|`messageHandlers.type`|<span data-ttu-id="ccf29-425">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="ccf29-425">string</span></span>|||<span data-ttu-id="ccf29-426">Der Typ des Nachrichten Handlers.</span><span class="sxs-lookup"><span data-stu-id="ccf29-426">The type of message handler.</span></span> <span data-ttu-id="ccf29-427">Muss `"link"` sein.</span><span class="sxs-lookup"><span data-stu-id="ccf29-427">Must be `"link"`.</span></span>|
|`messageHandlers.value.domains`|<span data-ttu-id="ccf29-428">Array von Zeichenfolgen</span><span class="sxs-lookup"><span data-stu-id="ccf29-428">array of Strings</span></span>|||<span data-ttu-id="ccf29-429">Array von Domänen, für die der Link Nachrichtenhandler registriert werden kann.</span><span class="sxs-lookup"><span data-stu-id="ccf29-429">array of domains that the link message handler can register for.</span></span>|

### <a name="composeextensionscommands"></a><span data-ttu-id="ccf29-430">composeExtensions. Commands</span><span class="sxs-lookup"><span data-stu-id="ccf29-430">composeExtensions.commands</span></span>

<span data-ttu-id="ccf29-431">Ihre Messaging Erweiterung sollte einen oder mehrere Befehle deklarieren.</span><span class="sxs-lookup"><span data-stu-id="ccf29-431">Your messaging extension should declare one or more commands.</span></span> <span data-ttu-id="ccf29-432">Jeder Befehl wird in Microsoft Teams als potenzielle Interaktion aus dem Benutzeroberflächen basierten Einstiegspfad angezeigt.</span><span class="sxs-lookup"><span data-stu-id="ccf29-432">Each command appears in Microsoft Teams as a potential interaction from the UI-based entry point.</span></span> <span data-ttu-id="ccf29-433">Es gibt maximal 10 Befehle.</span><span class="sxs-lookup"><span data-stu-id="ccf29-433">There is a maximum of 10 commands.</span></span>

<span data-ttu-id="ccf29-434">Jedes Command-Element ist ein Objekt mit der folgenden Struktur:</span><span class="sxs-lookup"><span data-stu-id="ccf29-434">Each command item is an object with the following structure:</span></span>

|<span data-ttu-id="ccf29-435">Name</span><span class="sxs-lookup"><span data-stu-id="ccf29-435">Name</span></span>| <span data-ttu-id="ccf29-436">Typ</span><span class="sxs-lookup"><span data-stu-id="ccf29-436">Type</span></span>| <span data-ttu-id="ccf29-437">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="ccf29-437">Maximum size</span></span> | <span data-ttu-id="ccf29-438">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="ccf29-438">Required</span></span> | <span data-ttu-id="ccf29-439">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ccf29-439">Description</span></span>|
|---|---|---|---|---|
|`id`|<span data-ttu-id="ccf29-440">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="ccf29-440">string</span></span>|<span data-ttu-id="ccf29-441">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="ccf29-441">64 characters</span></span>|<span data-ttu-id="ccf29-442">✔</span><span class="sxs-lookup"><span data-stu-id="ccf29-442">✔</span></span>|<span data-ttu-id="ccf29-443">Die ID für den Befehl.</span><span class="sxs-lookup"><span data-stu-id="ccf29-443">The ID for the command.</span></span>|
|`title`|<span data-ttu-id="ccf29-444">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="ccf29-444">string</span></span>|<span data-ttu-id="ccf29-445">32 Zeichen</span><span class="sxs-lookup"><span data-stu-id="ccf29-445">32 characters</span></span>|<span data-ttu-id="ccf29-446">✔</span><span class="sxs-lookup"><span data-stu-id="ccf29-446">✔</span></span>|<span data-ttu-id="ccf29-447">Der benutzerfreundliche Befehlsname.</span><span class="sxs-lookup"><span data-stu-id="ccf29-447">The user-friendly command name.</span></span>|
|`type`|<span data-ttu-id="ccf29-448">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="ccf29-448">string</span></span>|<span data-ttu-id="ccf29-449">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="ccf29-449">64 characters</span></span>||<span data-ttu-id="ccf29-450">Der Typ des Befehls.</span><span class="sxs-lookup"><span data-stu-id="ccf29-450">Type of the command.</span></span> <span data-ttu-id="ccf29-451">Einer von `query` oder `action` .</span><span class="sxs-lookup"><span data-stu-id="ccf29-451">One of `query` or `action`.</span></span> <span data-ttu-id="ccf29-452">Standard: **Query**.</span><span class="sxs-lookup"><span data-stu-id="ccf29-452">Default: **query**.</span></span>|
|`description`|<span data-ttu-id="ccf29-453">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="ccf29-453">string</span></span>|<span data-ttu-id="ccf29-454">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="ccf29-454">128 characters</span></span>||<span data-ttu-id="ccf29-455">Die Beschreibung, die den Benutzern angezeigt wird, um den Zweck dieses Befehls anzugeben.</span><span class="sxs-lookup"><span data-stu-id="ccf29-455">The description that appears to users to indicate the purpose of this command.</span></span>|
|`initialRun`|<span data-ttu-id="ccf29-456">Boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="ccf29-456">boolean</span></span>|||<span data-ttu-id="ccf29-457">Ein boolescher Wert, der angibt, ob der Befehl anfänglich ohne Parameter ausgeführt werden soll.</span><span class="sxs-lookup"><span data-stu-id="ccf29-457">A boolean value that indicates whether the command should be run initially with no parameters.</span></span> <span data-ttu-id="ccf29-458">Standard: **False**.</span><span class="sxs-lookup"><span data-stu-id="ccf29-458">Default: **false**.</span></span>|
|`context`|<span data-ttu-id="ccf29-459">Array von Zeichenfolgen</span><span class="sxs-lookup"><span data-stu-id="ccf29-459">array of Strings</span></span>|<span data-ttu-id="ccf29-460">3</span><span class="sxs-lookup"><span data-stu-id="ccf29-460">3</span></span>||<span data-ttu-id="ccf29-461">Definiert, woher die Nachrichten Erweiterung aufgerufen werden kann.</span><span class="sxs-lookup"><span data-stu-id="ccf29-461">Defines where the message extension can be invoked from.</span></span> <span data-ttu-id="ccf29-462">Eine beliebige Kombination von `compose` , `commandBox` , `message` .</span><span class="sxs-lookup"><span data-stu-id="ccf29-462">Any combination of`compose`,`commandBox`,`message` .</span></span> <span data-ttu-id="ccf29-463">Der Standardwert lautet `["compose","commandBox"]`.</span><span class="sxs-lookup"><span data-stu-id="ccf29-463">Default is `["compose","commandBox"]`.</span></span>|
|`fetchTask`|<span data-ttu-id="ccf29-464">Boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="ccf29-464">boolean</span></span>|||<span data-ttu-id="ccf29-465">Ein boolescher Wert, der angibt, ob das Aufgabenmodul dynamisch abgerufen werden soll.</span><span class="sxs-lookup"><span data-stu-id="ccf29-465">A boolean value that indicates if it should fetch the task module dynamically.</span></span> <span data-ttu-id="ccf29-466">Standard: **False**.</span><span class="sxs-lookup"><span data-stu-id="ccf29-466">Default: **false**.</span></span>|
|`taskInfo`|<span data-ttu-id="ccf29-467">Objekt</span><span class="sxs-lookup"><span data-stu-id="ccf29-467">object</span></span>|||<span data-ttu-id="ccf29-468">Geben Sie das Aufgabenmodul an, das beim Verwenden eines Messaging Erweiterungs Befehls vorab zu laden ist.</span><span class="sxs-lookup"><span data-stu-id="ccf29-468">Specify the task module to pre-load when using a messaging extension command.</span></span>|
|`taskInfo.title`|<span data-ttu-id="ccf29-469">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="ccf29-469">string</span></span>|<span data-ttu-id="ccf29-470">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="ccf29-470">64 characters</span></span>||<span data-ttu-id="ccf29-471">Ursprünglicher Dialogtitel.</span><span class="sxs-lookup"><span data-stu-id="ccf29-471">Initial dialog title.</span></span>|
|`taskInfo.width`|<span data-ttu-id="ccf29-472">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="ccf29-472">string</span></span>|||<span data-ttu-id="ccf29-473">Dialog Breite-entweder eine Zahl in Pixel oder ein Standardlayout wie "Large", "Medium" oder "Small".</span><span class="sxs-lookup"><span data-stu-id="ccf29-473">Dialog width - either a number in pixels or default layout such as 'large', 'medium', or 'small'.</span></span>|
|`taskInfo.height`|<span data-ttu-id="ccf29-474">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="ccf29-474">string</span></span>|||<span data-ttu-id="ccf29-475">Dialog Feld Höhe: entweder eine Zahl in Pixel oder ein Standardlayout wie "Large", "Medium" oder "Small".</span><span class="sxs-lookup"><span data-stu-id="ccf29-475">Dialog height - either a number in pixels or default layout such as 'large', 'medium', or 'small'.</span></span>|
|`taskInfo.url`|<span data-ttu-id="ccf29-476">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="ccf29-476">string</span></span>|||<span data-ttu-id="ccf29-477">Anfängliche WebView-URL.</span><span class="sxs-lookup"><span data-stu-id="ccf29-477">Initial webview URL.</span></span>|
|`parameters`|<span data-ttu-id="ccf29-478">Array von Object</span><span class="sxs-lookup"><span data-stu-id="ccf29-478">array of object</span></span>|<span data-ttu-id="ccf29-479">5 Elemente</span><span class="sxs-lookup"><span data-stu-id="ccf29-479">5 items</span></span>|<span data-ttu-id="ccf29-480">✔</span><span class="sxs-lookup"><span data-stu-id="ccf29-480">✔</span></span>|<span data-ttu-id="ccf29-481">Die Liste der Parameter, die der Befehl benötigt.</span><span class="sxs-lookup"><span data-stu-id="ccf29-481">The list of parameters the command takes.</span></span> <span data-ttu-id="ccf29-482">Minimum: 1; Maximum: 5.</span><span class="sxs-lookup"><span data-stu-id="ccf29-482">Minimum: 1; maximum: 5.</span></span>|
|`parameters.name`|<span data-ttu-id="ccf29-483">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="ccf29-483">string</span></span>|<span data-ttu-id="ccf29-484">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="ccf29-484">64 characters</span></span>|<span data-ttu-id="ccf29-485">✔</span><span class="sxs-lookup"><span data-stu-id="ccf29-485">✔</span></span>|<span data-ttu-id="ccf29-486">Der Name des Parameters, wie er im Client angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="ccf29-486">The name of the parameter as it appears in the client.</span></span> <span data-ttu-id="ccf29-487">Dies ist in der Benutzeranforderung enthalten.</span><span class="sxs-lookup"><span data-stu-id="ccf29-487">This is included in the user request.</span></span>|
|`parameters.title`|<span data-ttu-id="ccf29-488">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="ccf29-488">string</span></span>|<span data-ttu-id="ccf29-489">32 Zeichen</span><span class="sxs-lookup"><span data-stu-id="ccf29-489">32 characters</span></span>|<span data-ttu-id="ccf29-490">✔</span><span class="sxs-lookup"><span data-stu-id="ccf29-490">✔</span></span>|<span data-ttu-id="ccf29-491">Benutzerfreundlicher Titel für den Parameter.</span><span class="sxs-lookup"><span data-stu-id="ccf29-491">User-friendly title for the parameter.</span></span>|
|`parameters.description`|<span data-ttu-id="ccf29-492">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="ccf29-492">string</span></span>|<span data-ttu-id="ccf29-493">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="ccf29-493">128 characters</span></span>||<span data-ttu-id="ccf29-494">Benutzerfreundliche Zeichenfolge, die den Zweck dieses Parameters beschreibt.</span><span class="sxs-lookup"><span data-stu-id="ccf29-494">User-friendly string that describes this parameter’s purpose.</span></span>|
|`parameters.value`|<span data-ttu-id="ccf29-495">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="ccf29-495">string</span></span>|<span data-ttu-id="ccf29-496">512 Zeichen</span><span class="sxs-lookup"><span data-stu-id="ccf29-496">512 characters</span></span>||<span data-ttu-id="ccf29-497">Anfangswert für den Parameter.</span><span class="sxs-lookup"><span data-stu-id="ccf29-497">Initial value for the parameter.</span></span>|
|`parameters.inputType`|<span data-ttu-id="ccf29-498">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="ccf29-498">string</span></span>|<span data-ttu-id="ccf29-499">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="ccf29-499">128 characters</span></span>||<span data-ttu-id="ccf29-500">Definiert den Typ des Steuerelements, das in einem Aufgabenmodul für angezeigt wird `fetchTask: true` .</span><span class="sxs-lookup"><span data-stu-id="ccf29-500">Defines the type of control displayed on a task module for`fetchTask: true` .</span></span> <span data-ttu-id="ccf29-501">Einer von `text, textarea, number, date, time, toggle, choiceset` .</span><span class="sxs-lookup"><span data-stu-id="ccf29-501">One of `text, textarea, number, date, time, toggle, choiceset` .</span></span>|
|`parameters.choices`|<span data-ttu-id="ccf29-502">Array von Objekten</span><span class="sxs-lookup"><span data-stu-id="ccf29-502">array of objects</span></span>|<span data-ttu-id="ccf29-503">10 Elemente</span><span class="sxs-lookup"><span data-stu-id="ccf29-503">10 items</span></span>||<span data-ttu-id="ccf29-504">Die Auswahloptionen für `choiceset` .</span><span class="sxs-lookup"><span data-stu-id="ccf29-504">The choice options for the`choiceset`.</span></span> <span data-ttu-id="ccf29-505">Nur verwenden `parameter.inputType` , wenn ist `choiceset` .</span><span class="sxs-lookup"><span data-stu-id="ccf29-505">Use only when`parameter.inputType` is `choiceset`.</span></span>|
|`parameters.choices.title`|<span data-ttu-id="ccf29-506">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="ccf29-506">string</span></span>|<span data-ttu-id="ccf29-507">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="ccf29-507">128 characters</span></span>|<span data-ttu-id="ccf29-508">✔</span><span class="sxs-lookup"><span data-stu-id="ccf29-508">✔</span></span>|<span data-ttu-id="ccf29-509">Titel der Auswahl.</span><span class="sxs-lookup"><span data-stu-id="ccf29-509">Title of the choice.</span></span>|
|`parameters.choices.value`|<span data-ttu-id="ccf29-510">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="ccf29-510">string</span></span>|<span data-ttu-id="ccf29-511">512 Zeichen</span><span class="sxs-lookup"><span data-stu-id="ccf29-511">512 characters</span></span>|<span data-ttu-id="ccf29-512">✔</span><span class="sxs-lookup"><span data-stu-id="ccf29-512">✔</span></span>|<span data-ttu-id="ccf29-513">Value of the choice.</span><span class="sxs-lookup"><span data-stu-id="ccf29-513">Value of the choice.</span></span>|

## <a name="permissions"></a><span data-ttu-id="ccf29-514">Berechtigungen</span><span class="sxs-lookup"><span data-stu-id="ccf29-514">permissions</span></span>

<span data-ttu-id="ccf29-515">**Optional** – Array von Zeichenfolgen</span><span class="sxs-lookup"><span data-stu-id="ccf29-515">**Optional** — array of strings</span></span>

<span data-ttu-id="ccf29-516">Ein Array, das `string` angibt, welche Berechtigungen die APP anfordert, sodass Endbenutzer wissen, wie die Erweiterung ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="ccf29-516">An array of `string` which specifies which permissions the app requests, which lets end users know how the extension will perform.</span></span> <span data-ttu-id="ccf29-517">Die folgenden Optionen sind nicht exklusiv:</span><span class="sxs-lookup"><span data-stu-id="ccf29-517">The following options are non-exclusive:</span></span>

* <span data-ttu-id="ccf29-518">`identity`&emsp;Erfordert Benutzeridentitätsinformationen</span><span class="sxs-lookup"><span data-stu-id="ccf29-518">`identity` &emsp; Requires user identity information</span></span>
* <span data-ttu-id="ccf29-519">`messageTeamMembers`&emsp;Erfordert die Berechtigung zum Senden von direkten Nachrichten an Teammitglieder.</span><span class="sxs-lookup"><span data-stu-id="ccf29-519">`messageTeamMembers` &emsp; Requires permission to send direct messages to team members</span></span>

<span data-ttu-id="ccf29-520">Wenn Sie diese Berechtigungen beim Aktualisieren Ihrer APP ändern, werden die Benutzer beim ersten Ausführen der aktualisierten App den Zustimmungsprozess wiederholen.</span><span class="sxs-lookup"><span data-stu-id="ccf29-520">Changing these permissions when updating your app will cause your users to repeat the consent process the first time they run the updated app.</span></span> <span data-ttu-id="ccf29-521">Weitere Informationen finden Sie unter [Aktualisieren Ihrer APP](~/concepts/deploy-and-publish/appsource/post-publish/overview.md) .</span><span class="sxs-lookup"><span data-stu-id="ccf29-521">See [Updating your app](~/concepts/deploy-and-publish/appsource/post-publish/overview.md) for more information.</span></span>

## <a name="devicepermissions"></a><span data-ttu-id="ccf29-522">devicePermissions</span><span class="sxs-lookup"><span data-stu-id="ccf29-522">devicePermissions</span></span>

<span data-ttu-id="ccf29-523">**Optional** – Array von Zeichenfolgen</span><span class="sxs-lookup"><span data-stu-id="ccf29-523">**Optional** — array of strings</span></span>

<span data-ttu-id="ccf29-524">Gibt die systemeigenen Funktionen auf dem Gerät eines Benutzers an, für die Ihre APP möglicherweise Zugriff anfordern kann.</span><span class="sxs-lookup"><span data-stu-id="ccf29-524">Specifies the native features on a user's device that your app may request access to.</span></span> <span data-ttu-id="ccf29-525">Mögliche Optionen sind:</span><span class="sxs-lookup"><span data-stu-id="ccf29-525">Options are:</span></span>

* `geolocation`
* `media`
* `notifications`
* `midi`
* `openExternal`

## <a name="validdomains"></a><span data-ttu-id="ccf29-526">validDomains</span><span class="sxs-lookup"><span data-stu-id="ccf29-526">validDomains</span></span>

<span data-ttu-id="ccf29-527">**Optional**, sofern angegeben, außer **erforderlich**</span><span class="sxs-lookup"><span data-stu-id="ccf29-527">**Optional**, except **Required** where noted</span></span>

<span data-ttu-id="ccf29-528">Eine Liste gültiger Domänen für Websites, die von der APP im Microsoft Teams-Client zu laden erwartet werden.</span><span class="sxs-lookup"><span data-stu-id="ccf29-528">A list of valid domains for websites the app expects to load within the Teams client.</span></span> <span data-ttu-id="ccf29-529">Domänen Auflistungen können beispielsweise Platzhalterzeichen enthalten `*.example.com` .</span><span class="sxs-lookup"><span data-stu-id="ccf29-529">Domain listings can include wildcards, for example `*.example.com`.</span></span> <span data-ttu-id="ccf29-530">Dies entspricht genau einem Segment der Domäne. Wenn Sie eine Übereinstimmung benötigen, `a.b.example.com` verwenden Sie `*.*.example.com` .</span><span class="sxs-lookup"><span data-stu-id="ccf29-530">This matches exactly one segment of the domain; if you need to match `a.b.example.com` then use `*.*.example.com`.</span></span> <span data-ttu-id="ccf29-531">Wenn Ihre Registerkartenkonfiguration oder Inhalts-UI neben einer Verwendung für die Registerkartenkonfiguration zu einer anderen Domäne navigieren muss, muss diese Domäne hier angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="ccf29-531">If your tab configuration or content UI needs to navigate to any other domain besides the one use for tab configuration, that domain must be specified here.</span></span>

<span data-ttu-id="ccf29-532">Es ist jedoch **nicht** erforderlich, die Domänen von Identitätsanbietern einzubeziehen, die Sie in Ihrer APP unterstützen möchten.</span><span class="sxs-lookup"><span data-stu-id="ccf29-532">It is **not** necessary to include the domains of identity providers you want to support in your app, however.</span></span> <span data-ttu-id="ccf29-533">Um beispielsweise mit einer Google-ID zu authentifizieren, müssen Sie zu Accounts.Google.com umgeleitet werden, aber Sie sollten Accounts.Google.com nicht in einschließen `validDomains[]` .</span><span class="sxs-lookup"><span data-stu-id="ccf29-533">For example, to authenticate using a Google ID, it's necessary to redirect to accounts.google.com, but you should not include accounts.google.com in `validDomains[]`.</span></span>

<span data-ttu-id="ccf29-534">Microsoft Teams-apps, die ihre eigenen SharePoint-URLs benötigen, um gut zu funktionieren, können "{teamsitedomain}" in Ihre gültige Domänenliste einschließen.</span><span class="sxs-lookup"><span data-stu-id="ccf29-534">Teams apps that require their own sharepoint URLs to function well, may include "{teamsitedomain}" in their valid domain list.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ccf29-535">Fügen Sie keine Domänen hinzu, die sich außerhalb des Steuerelements befinden, entweder direkt oder über Platzhalter.</span><span class="sxs-lookup"><span data-stu-id="ccf29-535">Do not add domains that are outside your control, either directly or via wildcards.</span></span> <span data-ttu-id="ccf29-536">Beispielsweise `yourapp.onmicrosoft.com` ist gültig, jedoch ungültig `*.onmicrosoft.com` .</span><span class="sxs-lookup"><span data-stu-id="ccf29-536">For example, `yourapp.onmicrosoft.com` is valid, but `*.onmicrosoft.com` is not valid.</span></span>

<span data-ttu-id="ccf29-537">Das Objekt ist ein Array mit allen Elementen des Typs `string` .</span><span class="sxs-lookup"><span data-stu-id="ccf29-537">The object is an array with all elements of the type `string`.</span></span>

## <a name="webapplicationinfo"></a><span data-ttu-id="ccf29-538">webApplicationInfo</span><span class="sxs-lookup"><span data-stu-id="ccf29-538">webApplicationInfo</span></span>

<span data-ttu-id="ccf29-539">**Optional** – Objekt</span><span class="sxs-lookup"><span data-stu-id="ccf29-539">**Optional** — object</span></span>

<span data-ttu-id="ccf29-540">Geben Sie Ihre Aad-APP-ID und Diagramm Informationen an, damit Benutzer sich nahtlos bei ihrer Aad-App anmelden können.</span><span class="sxs-lookup"><span data-stu-id="ccf29-540">Specify your AAD App ID and Graph information to help users seamlessly sign into your AAD app.</span></span>

|<span data-ttu-id="ccf29-541">Name</span><span class="sxs-lookup"><span data-stu-id="ccf29-541">Name</span></span>| <span data-ttu-id="ccf29-542">Typ</span><span class="sxs-lookup"><span data-stu-id="ccf29-542">Type</span></span>| <span data-ttu-id="ccf29-543">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="ccf29-543">Maximum size</span></span> | <span data-ttu-id="ccf29-544">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="ccf29-544">Required</span></span> | <span data-ttu-id="ccf29-545">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ccf29-545">Description</span></span>|
|---|---|---|---|---|
|`id`|<span data-ttu-id="ccf29-546">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="ccf29-546">string</span></span>|<span data-ttu-id="ccf29-547">36 Zeichen</span><span class="sxs-lookup"><span data-stu-id="ccf29-547">36 characters</span></span>|<span data-ttu-id="ccf29-548">✔</span><span class="sxs-lookup"><span data-stu-id="ccf29-548">✔</span></span>|<span data-ttu-id="ccf29-549">Aad-Anwendungs-ID der app.</span><span class="sxs-lookup"><span data-stu-id="ccf29-549">AAD application id of the app.</span></span> <span data-ttu-id="ccf29-550">Diese ID muss eine GUID sein.</span><span class="sxs-lookup"><span data-stu-id="ccf29-550">This id must be a GUID.</span></span>|
|`resource`|<span data-ttu-id="ccf29-551">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="ccf29-551">string</span></span>|<span data-ttu-id="ccf29-552">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="ccf29-552">2048 characters</span></span>|<span data-ttu-id="ccf29-553">✔</span><span class="sxs-lookup"><span data-stu-id="ccf29-553">✔</span></span>|<span data-ttu-id="ccf29-554">Ressourcen-URL der APP zum Abrufen des Authentifizierungstokens für SSO.</span><span class="sxs-lookup"><span data-stu-id="ccf29-554">Resource url of app for acquiring auth token for SSO.</span></span>|
|`applicationPermissions`|<span data-ttu-id="ccf29-555">array of strings</span><span class="sxs-lookup"><span data-stu-id="ccf29-555">array of strings</span></span>|<span data-ttu-id="ccf29-556">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="ccf29-556">128 characters</span></span>||<span data-ttu-id="ccf29-557">Angeben einer detaillierten [ressourcenspezifischen Zustimmung](../../graph-api/rsc/resource-specific-consent.md#resource-specific-permissions)</span><span class="sxs-lookup"><span data-stu-id="ccf29-557">Specify granular [resource specific consent](../../graph-api/rsc/resource-specific-consent.md#resource-specific-permissions)</span></span>|

## <a name="showloadingindicator"></a><span data-ttu-id="ccf29-558">showLoadingIndicator</span><span class="sxs-lookup"><span data-stu-id="ccf29-558">showLoadingIndicator</span></span>

<span data-ttu-id="ccf29-559">**Optional** – Boolean</span><span class="sxs-lookup"><span data-stu-id="ccf29-559">**Optional** — boolean</span></span>

<span data-ttu-id="ccf29-560">Geben Sie an, ob der Lade Indikator angezeigt werden soll, wenn eine APP/Registerkarte geladen wird.</span><span class="sxs-lookup"><span data-stu-id="ccf29-560">Indicate whether or not to show the loading indicator when an app/tab is loading.</span></span> <span data-ttu-id="ccf29-561">Standard: **False**.</span><span class="sxs-lookup"><span data-stu-id="ccf29-561">Default: **false**.</span></span>
>[!NOTE]
><span data-ttu-id="ccf29-562">Wenn Sie "showLoadingIndicator: true" in Ihrem App-Manifest festgelegt haben, müssen Sie die Inhaltsseiten ihrer Registerkarten und Aufgaben Module gemäß dem in [Anzeigen eines systemeigenen Lade Indikator](../../tabs/how-to/create-tab-pages/content-page.md#show-a-native-loading-indicator) Dokuments beschriebenen Protokoll ändern.</span><span class="sxs-lookup"><span data-stu-id="ccf29-562">If you set "showLoadingIndicator : true" in your app manifest, then for the page to load correctly, you must modify the content pages of your tabs and task modules as per the protocol described in [Show a native loading indicator](../../tabs/how-to/create-tab-pages/content-page.md#show-a-native-loading-indicator) document.</span></span>


## <a name="isfullscreen"></a><span data-ttu-id="ccf29-563">isFullScreen</span><span class="sxs-lookup"><span data-stu-id="ccf29-563">isFullScreen</span></span>

 <span data-ttu-id="ccf29-564">**Optional** – Boolean</span><span class="sxs-lookup"><span data-stu-id="ccf29-564">**Optional** — boolean</span></span>

<span data-ttu-id="ccf29-565">Geben Sie an, wo eine persönliche App mit oder ohne Registerkarten Kopfleiste gerendert wird.</span><span class="sxs-lookup"><span data-stu-id="ccf29-565">Indicate where a personal app is rendered with or without a tab-header bar.</span></span> <span data-ttu-id="ccf29-566">Standard: **False**.</span><span class="sxs-lookup"><span data-stu-id="ccf29-566">Default: **false**.</span></span>

## <a name="activities"></a><span data-ttu-id="ccf29-567">Aktivitäten</span><span class="sxs-lookup"><span data-stu-id="ccf29-567">activities</span></span>

<span data-ttu-id="ccf29-568">**Optional** – Objekt</span><span class="sxs-lookup"><span data-stu-id="ccf29-568">**Optional** — object</span></span>

<span data-ttu-id="ccf29-569">Definieren Sie die Eigenschaften, die Ihre APP für die Bereitstellung in einem Benutzer Aktivitätsfeed verwenden wird.</span><span class="sxs-lookup"><span data-stu-id="ccf29-569">Define the properties your app will use to post to a user activity feed.</span></span>

|<span data-ttu-id="ccf29-570">Name</span><span class="sxs-lookup"><span data-stu-id="ccf29-570">Name</span></span>| <span data-ttu-id="ccf29-571">Typ</span><span class="sxs-lookup"><span data-stu-id="ccf29-571">Type</span></span>| <span data-ttu-id="ccf29-572">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="ccf29-572">Maximum size</span></span> | <span data-ttu-id="ccf29-573">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="ccf29-573">Required</span></span> | <span data-ttu-id="ccf29-574">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ccf29-574">Description</span></span>|
|---|---|---|---|---|
|`activityTypes`|<span data-ttu-id="ccf29-575">Array von Objekten</span><span class="sxs-lookup"><span data-stu-id="ccf29-575">array of Objects</span></span>|<span data-ttu-id="ccf29-576">128 Elemente</span><span class="sxs-lookup"><span data-stu-id="ccf29-576">128 items</span></span>| | <span data-ttu-id="ccf29-577">Geben Sie die Arten von Aktivitäten an, die Ihre APP an einen Benutzer-Aktivitätsfeed senden kann.</span><span class="sxs-lookup"><span data-stu-id="ccf29-577">Specify the types of activities that your app can post to a users activity feed.</span></span>|

### <a name="activitiesactivitytypes"></a><span data-ttu-id="ccf29-578">Activities. activityTypes</span><span class="sxs-lookup"><span data-stu-id="ccf29-578">activities.activityTypes</span></span>

|<span data-ttu-id="ccf29-579">Name</span><span class="sxs-lookup"><span data-stu-id="ccf29-579">Name</span></span>| <span data-ttu-id="ccf29-580">Typ</span><span class="sxs-lookup"><span data-stu-id="ccf29-580">Type</span></span>| <span data-ttu-id="ccf29-581">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="ccf29-581">Maximum size</span></span> | <span data-ttu-id="ccf29-582">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="ccf29-582">Required</span></span> | <span data-ttu-id="ccf29-583">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="ccf29-583">Description</span></span>|
|---|---|---|---|---|
|`type`|<span data-ttu-id="ccf29-584">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="ccf29-584">string</span></span>|<span data-ttu-id="ccf29-585">32 Zeichen</span><span class="sxs-lookup"><span data-stu-id="ccf29-585">32 characters</span></span>|<span data-ttu-id="ccf29-586">✔</span><span class="sxs-lookup"><span data-stu-id="ccf29-586">✔</span></span>|<span data-ttu-id="ccf29-587">Der Typ der Benachrichtigung.</span><span class="sxs-lookup"><span data-stu-id="ccf29-587">The notification type.</span></span> <span data-ttu-id="ccf29-588">*Siehe weiter unten*.</span><span class="sxs-lookup"><span data-stu-id="ccf29-588">*See below*.</span></span>|
|`description`|<span data-ttu-id="ccf29-589">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="ccf29-589">string</span></span>|<span data-ttu-id="ccf29-590">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="ccf29-590">128 characters</span></span>|<span data-ttu-id="ccf29-591">✔</span><span class="sxs-lookup"><span data-stu-id="ccf29-591">✔</span></span>|<span data-ttu-id="ccf29-592">Eine kurze Beschreibung der Benachrichtigung.</span><span class="sxs-lookup"><span data-stu-id="ccf29-592">A brief description of the notification.</span></span> <span data-ttu-id="ccf29-593">*Siehe weiter unten*.</span><span class="sxs-lookup"><span data-stu-id="ccf29-593">*See below*.</span></span>|
|`templateText`|<span data-ttu-id="ccf29-594">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="ccf29-594">string</span></span>|<span data-ttu-id="ccf29-595">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="ccf29-595">128 characters</span></span>|<span data-ttu-id="ccf29-596">✔</span><span class="sxs-lookup"><span data-stu-id="ccf29-596">✔</span></span>|<span data-ttu-id="ccf29-597">Ex: "{Akteur} hat Aufgabe {Task-Nr} für dich erstellt"</span><span class="sxs-lookup"><span data-stu-id="ccf29-597">Ex: "{actor} created task {taskId} for you"</span></span>|

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
