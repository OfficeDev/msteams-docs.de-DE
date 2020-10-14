---
title: Manifest-Schemareferenz
description: Beschreibt das vom Manifest für Microsoft Teams unterstützte Schema.
keywords: Team Manifest-Schema
author: laujan
ms.author: lajanuar
ms.openlocfilehash: b514bbe8e04e674f5aafb3dff3acfe08072d814f
ms.sourcegitcommit: d61f14053fc695bc1956bf50e83956613c19ccca
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/13/2020
ms.locfileid: "48452736"
---
# <a name="reference-manifest-schema-for-microsoft-teams"></a><span data-ttu-id="8a1d8-104">Referenz: Manifest-Schema für Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="8a1d8-104">Reference: Manifest schema for Microsoft Teams</span></span>

<span data-ttu-id="8a1d8-105">Das Microsoft Teams-Manifest beschreibt, wie die app in das Microsoft Teams-Produkt integriert wird.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-105">The Microsoft Teams manifest describes how the app integrates into the Microsoft Teams product.</span></span> <span data-ttu-id="8a1d8-106">Das Manifest muss dem Schema entsprechen, das unter gehostet wird [`https://developer.microsoft.com/json-schemas/teams/v1.7/MicrosoftTeams.schema.json`]( https://developer.microsoft.com/json-schemas/teams/v1.7/MicrosoftTeams.schema.json) .</span><span class="sxs-lookup"><span data-stu-id="8a1d8-106">Your manifest must conform to the schema hosted at [`https://developer.microsoft.com/json-schemas/teams/v1.7/MicrosoftTeams.schema.json`]( https://developer.microsoft.com/json-schemas/teams/v1.7/MicrosoftTeams.schema.json).</span></span> <span data-ttu-id="8a1d8-107">Frühere Versionen 1.0-1.6 werden ebenfalls unterstützt (mit "v1. x" in der URL).</span><span class="sxs-lookup"><span data-stu-id="8a1d8-107">Previous versions 1.0-1.6 are also supported (using "v1.x" in the URL).</span></span>

<span data-ttu-id="8a1d8-108">Das folgende Schemabeispiel zeigt alle Erweiterungsoptionen.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-108">The following schema sample shows all extensibility options.</span></span>

## <a name="sample-full-manifest"></a><span data-ttu-id="8a1d8-109">Vollständiges Beispiel Manifest</span><span class="sxs-lookup"><span data-stu-id="8a1d8-109">Sample full manifest</span></span>

```json
{
  "$schema": "https://developer.microsoft.com/json-schemas/teams/v1.7/MicrosoftTeams.schema.json",
  "manifestVersion": "1.7",
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
      "sharePointPreviewImage": "Relative path to a tab preview image for use in SharePoint — 1024px X 768",
      "supportedSharePointHosts": "Define how your tab wil be made available in SharePoint (full page or web part)"
    }
  ],
  "staticTabs": [
    {
      "entityId": "unique Id for the page entity",
      "scopes": [
        "personal"
      ],
      "name": "Display name of tab",
      "contentUrl": "https://contoso.com/content (displayed in Teams canvas)",
      "websiteUrl": "https://contoso.com/content (displayed in web browser"
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

<span data-ttu-id="8a1d8-110">Das Schema definiert die folgenden Eigenschaften:</span><span class="sxs-lookup"><span data-stu-id="8a1d8-110">The schema defines the following properties:</span></span>

## <a name="schema"></a><span data-ttu-id="8a1d8-111">$schema</span><span class="sxs-lookup"><span data-stu-id="8a1d8-111">$schema</span></span>

<span data-ttu-id="8a1d8-112">*Optional, jedoch empfohlen* – Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="8a1d8-112">*Optional, but recommended* — string</span></span>

<span data-ttu-id="8a1d8-113">Die https://-URL, die auf das JSON-Schema für das Manifest verweist.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-113">The https:// URL referencing the JSON Schema for the manifest.</span></span>

## <a name="manifestversion"></a><span data-ttu-id="8a1d8-114">manifestVersion</span><span class="sxs-lookup"><span data-stu-id="8a1d8-114">manifestVersion</span></span>

<span data-ttu-id="8a1d8-115">**Erforderlich** – Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="8a1d8-115">**Required** — string</span></span>

<span data-ttu-id="8a1d8-116">Die Version des manifest-Schemas, die dieses Manifest verwendet.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-116">The version of the manifest schema this manifest is using.</span></span> <span data-ttu-id="8a1d8-117">Es sollte "1,7" sein.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-117">It should be "1.7".</span></span>

## <a name="version"></a><span data-ttu-id="8a1d8-118">Version</span><span class="sxs-lookup"><span data-stu-id="8a1d8-118">version</span></span>

<span data-ttu-id="8a1d8-119">**Erforderlich** – Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="8a1d8-119">**Required** — string</span></span>

<span data-ttu-id="8a1d8-120">Die Version der jeweiligen App.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-120">The version of the specific app.</span></span> <span data-ttu-id="8a1d8-121">Wenn Sie etwas in ihrem Manifest aktualisieren, muss die Version ebenfalls inkrementiert werden.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-121">If you update something in your manifest, the version must be incremented as well.</span></span> <span data-ttu-id="8a1d8-122">Auf diese Weise wird bei der Installation des neuen Manifests das vorhandene überschrieben, und der Benutzer erhält die neue Funktionalität.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-122">This way, when the new manifest is installed, it will overwrite the existing one and the user will get the new functionality.</span></span> <span data-ttu-id="8a1d8-123">Wenn diese APP an den Store übermittelt wurde, muss das neue Manifest erneut übermittelt und erneut validiert werden.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-123">If this app was submitted to the store, the new manifest will have to be re-submitted and re-validated.</span></span> <span data-ttu-id="8a1d8-124">Dann erhalten Benutzer dieser APP das neue aktualisierte Manifest automatisch in ein paar Stunden, nachdem es genehmigt wurde.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-124">Then, users of this app will get the new updated manifest automatically in a few hours, after it is approved.</span></span>

<span data-ttu-id="8a1d8-125">Wenn sich die angeforderte APP geändert hat, werden die Benutzer aufgefordert, die APP zu aktualisieren und erneut zu genehmigen.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-125">If the app requested permissions change, users will be prompted to upgrade and re-consent to the app.</span></span>

<span data-ttu-id="8a1d8-126">Diese Versionszeichenfolge muss dem [semver](http://semver.org/) -Standard (Major) entsprechen. Moll. Patch).</span><span class="sxs-lookup"><span data-stu-id="8a1d8-126">This version string must follow the [semver](http://semver.org/) standard (MAJOR.MINOR.PATCH).</span></span>

## <a name="id"></a><span data-ttu-id="8a1d8-127">id</span><span class="sxs-lookup"><span data-stu-id="8a1d8-127">id</span></span>

<span data-ttu-id="8a1d8-128">**Erforderlich** – Microsoft App-ID</span><span class="sxs-lookup"><span data-stu-id="8a1d8-128">**Required** — Microsoft app ID</span></span>

<span data-ttu-id="8a1d8-129">Der eindeutige von Microsoft generierte Bezeichner für diese APP.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-129">The unique Microsoft-generated identifier for this app.</span></span> <span data-ttu-id="8a1d8-130">Wenn Sie einen bot über das Microsoft bot-Framework registriert haben oder sich die Webanwendung Ihrer Registerkarte bereits bei Microsoft anmeldet, sollten Sie bereits über eine ID verfügen und diese hier eingeben.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-130">If you have registered a bot via the Microsoft Bot Framework, or your tab's web app already signs in with Microsoft, you should already have an ID and should enter it here.</span></span> <span data-ttu-id="8a1d8-131">Andernfalls sollten Sie eine neue ID im Microsoft-Anwendungs Registrierungs Portal ([meine Anwendungen](https://apps.dev.microsoft.com)) generieren, Sie hier eingeben und dann wieder verwenden, wenn Sie einen bot hinzufügen. Hinweis: Wenn Sie ein Update an Ihre vorhandene app in AppSource übermitteln, darf die ID in ihrem Manifest nicht geändert werden.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-131">Otherwise, you should generate a new ID at the Microsoft Application Registration Portal ([My Applications](https://apps.dev.microsoft.com)), enter it here, and then reuse it when you add a bot.Note: If you are submitting an update to your existing app in AppSource, the ID in your manifest must not be modified.</span></span>

## <a name="developer"></a><span data-ttu-id="8a1d8-132">developer</span><span class="sxs-lookup"><span data-stu-id="8a1d8-132">developer</span></span>

<span data-ttu-id="8a1d8-133">**Erforderlich** – Objekt</span><span class="sxs-lookup"><span data-stu-id="8a1d8-133">**Required** — object</span></span>

<span data-ttu-id="8a1d8-134">Gibt Informationen zu Ihrem Unternehmen an.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-134">Specifies information about your company.</span></span> <span data-ttu-id="8a1d8-135">Für an AppSource übermittelte Apps (ehemals Office Store) müssen diese Werte mit den Informationen in Ihrem AppSource-Eintrag übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-135">For apps submitted to AppSource (formerly Office Store), these values must match the information in your AppSource entry.</span></span> <span data-ttu-id="8a1d8-136">Weitere Informationen finden Sie in unseren [Veröffentlichungsrichtlinien](~/concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md) .</span><span class="sxs-lookup"><span data-stu-id="8a1d8-136">See our [publishing guidelines](~/concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md) for additional information.</span></span>

|<span data-ttu-id="8a1d8-137">Name</span><span class="sxs-lookup"><span data-stu-id="8a1d8-137">Name</span></span>| <span data-ttu-id="8a1d8-138">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="8a1d8-138">Maximum size</span></span> | <span data-ttu-id="8a1d8-139">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="8a1d8-139">Required</span></span> | <span data-ttu-id="8a1d8-140">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="8a1d8-140">Description</span></span>|
|---|---|---|---|
|`name`|<span data-ttu-id="8a1d8-141">32 Zeichen</span><span class="sxs-lookup"><span data-stu-id="8a1d8-141">32 characters</span></span>|<span data-ttu-id="8a1d8-142">✔</span><span class="sxs-lookup"><span data-stu-id="8a1d8-142">✔</span></span>|<span data-ttu-id="8a1d8-143">Der Anzeigename für den Entwickler.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-143">The display name for the developer.</span></span>|
|`websiteUrl`|<span data-ttu-id="8a1d8-144">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="8a1d8-144">2048 characters</span></span>|<span data-ttu-id="8a1d8-145">✔</span><span class="sxs-lookup"><span data-stu-id="8a1d8-145">✔</span></span>|<span data-ttu-id="8a1d8-146">Die https://-URL zur Website des Entwicklers.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-146">The https:// URL to the developer's website.</span></span> <span data-ttu-id="8a1d8-147">Dieser Link sollte Benutzer zu Ihrer Firma oder produktspezifischen Zielseite führen.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-147">This link should take users to your company or product-specific landing page.</span></span>|
|`privacyUrl`|<span data-ttu-id="8a1d8-148">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="8a1d8-148">2048 characters</span></span>|<span data-ttu-id="8a1d8-149">✔</span><span class="sxs-lookup"><span data-stu-id="8a1d8-149">✔</span></span>|<span data-ttu-id="8a1d8-150">Die https://-URL zur Datenschutzrichtlinie des Entwicklers.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-150">The https:// URL to the developer's privacy policy.</span></span>|
|`termsOfUseUrl`|<span data-ttu-id="8a1d8-151">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="8a1d8-151">2048 characters</span></span>|<span data-ttu-id="8a1d8-152">✔</span><span class="sxs-lookup"><span data-stu-id="8a1d8-152">✔</span></span>|<span data-ttu-id="8a1d8-153">Die https://-URL zu den Nutzungsbedingungen des Entwicklers.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-153">The https:// URL to the developer's terms of use.</span></span>|
|`mpnId`|<span data-ttu-id="8a1d8-154">10 Zeichen</span><span class="sxs-lookup"><span data-stu-id="8a1d8-154">10 characters</span></span>| |<span data-ttu-id="8a1d8-155">**Optional** Die Microsoft Partner-Netzwerk-ID, die die Partnerorganisation identifiziert, die die APP aufbaut.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-155">**Optional** The Microsoft Partner Network ID that identifies the partner organization building the app.</span></span>|

## <a name="name"></a><span data-ttu-id="8a1d8-156">name</span><span class="sxs-lookup"><span data-stu-id="8a1d8-156">name</span></span>

<span data-ttu-id="8a1d8-157">**Erforderlich** – Objekt</span><span class="sxs-lookup"><span data-stu-id="8a1d8-157">**Required** — object</span></span>

<span data-ttu-id="8a1d8-158">Der Name der APP-Erfahrung, der Benutzern in der Microsoft Teams-Benutzeroberfläche angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-158">The name of your app experience, displayed to users in the Teams experience.</span></span> <span data-ttu-id="8a1d8-159">Für apps, die an AppSource übermittelt werden, müssen diese Werte mit den Informationen in Ihrem AppSource-Eintrag übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-159">For apps submitted to AppSource, these values must match the information in your AppSource entry.</span></span> <span data-ttu-id="8a1d8-160">Die Werte von `short` und `full` sollten nicht identisch sein.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-160">The values of `short` and `full` should not be the same.</span></span>

|<span data-ttu-id="8a1d8-161">Name</span><span class="sxs-lookup"><span data-stu-id="8a1d8-161">Name</span></span>| <span data-ttu-id="8a1d8-162">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="8a1d8-162">Maximum size</span></span> | <span data-ttu-id="8a1d8-163">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="8a1d8-163">Required</span></span> | <span data-ttu-id="8a1d8-164">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="8a1d8-164">Description</span></span>|
|---|---|---|---|
|`short`|<span data-ttu-id="8a1d8-165">30 Zeichen</span><span class="sxs-lookup"><span data-stu-id="8a1d8-165">30 characters</span></span>|<span data-ttu-id="8a1d8-166">✔</span><span class="sxs-lookup"><span data-stu-id="8a1d8-166">✔</span></span>|<span data-ttu-id="8a1d8-167">Der kurze Anzeigename für die app.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-167">The short display name for the app.</span></span>|
|`full`|<span data-ttu-id="8a1d8-168">100 Zeichen</span><span class="sxs-lookup"><span data-stu-id="8a1d8-168">100 characters</span></span>||<span data-ttu-id="8a1d8-169">Der vollständige Name der APP, der verwendet wird, wenn der vollständige App-Name 30 Zeichen überschreitet.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-169">The full name of the app, used if the full app name exceeds 30 characters.</span></span>|

## <a name="description"></a><span data-ttu-id="8a1d8-170">description</span><span class="sxs-lookup"><span data-stu-id="8a1d8-170">description</span></span>

<span data-ttu-id="8a1d8-171">**Erforderlich** – Objekt</span><span class="sxs-lookup"><span data-stu-id="8a1d8-171">**Required** — object</span></span>

<span data-ttu-id="8a1d8-172">Beschreibt die APP für Benutzer.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-172">Describes your app to users.</span></span> <span data-ttu-id="8a1d8-173">Für apps, die an AppSource übermittelt werden, müssen diese Werte mit den Informationen in Ihrem AppSource-Eintrag übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-173">For apps submitted to AppSource, these values must match the information in your AppSource entry.</span></span>

<span data-ttu-id="8a1d8-174">Stellen Sie sicher, dass Ihre Beschreibung ihre Erfahrung genau beschreibt und Informationen bereitstellt, um potenziellen Kunden zu helfen, ihre Erfahrungen zu verstehen.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-174">Ensure that your description accurately describes your experience and provides information to help potential customers understand what your experience does.</span></span> <span data-ttu-id="8a1d8-175">Beachten Sie auch, dass in der vollständigen Beschreibung ein externes Konto zur Verwendung benötigt wird.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-175">You should also note, in the full description, if an external account is required for use.</span></span> <span data-ttu-id="8a1d8-176">Die Werte von `short` und `full` sollten nicht identisch sein.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-176">The values of `short` and `full` should not be the same.</span></span>  <span data-ttu-id="8a1d8-177">Ihre Kurzbeschreibung darf nicht innerhalb der langen Beschreibung wiederholt werden und darf keinen anderen APP-Namen enthalten.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-177">Your short description must not be repeated within the long description and must not include any other app name.</span></span>

|<span data-ttu-id="8a1d8-178">Name</span><span class="sxs-lookup"><span data-stu-id="8a1d8-178">Name</span></span>| <span data-ttu-id="8a1d8-179">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="8a1d8-179">Maximum size</span></span> | <span data-ttu-id="8a1d8-180">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="8a1d8-180">Required</span></span> | <span data-ttu-id="8a1d8-181">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="8a1d8-181">Description</span></span>|
|---|---|---|---|
|`short`|<span data-ttu-id="8a1d8-182">80 Zeichen</span><span class="sxs-lookup"><span data-stu-id="8a1d8-182">80 characters</span></span>|<span data-ttu-id="8a1d8-183">✔</span><span class="sxs-lookup"><span data-stu-id="8a1d8-183">✔</span></span>|<span data-ttu-id="8a1d8-184">Eine kurze Beschreibung Ihrer APP-Erfahrung, die verwendet wird, wenn der Speicherplatz limitiert ist.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-184">A short description of your app experience, used when space is limited.</span></span>|
|`full`|<span data-ttu-id="8a1d8-185">4000 Zeichen</span><span class="sxs-lookup"><span data-stu-id="8a1d8-185">4000 characters</span></span>|<span data-ttu-id="8a1d8-186">✔</span><span class="sxs-lookup"><span data-stu-id="8a1d8-186">✔</span></span>|<span data-ttu-id="8a1d8-187">Die vollständige Beschreibung Ihrer APP.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-187">The full description of your app.</span></span>|

## <a name="packagename"></a><span data-ttu-id="8a1d8-188">PackageName</span><span class="sxs-lookup"><span data-stu-id="8a1d8-188">packageName</span></span>

<span data-ttu-id="8a1d8-189">**Optional** – Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="8a1d8-189">**Optional** — string</span></span>

<span data-ttu-id="8a1d8-190">Ein eindeutiger Bezeichner für diese APP in umgekehrter Domänen Notation; Beispiel: com. Beispiel. MyApp.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-190">A unique identifier for this app in reverse domain notation; for example, com.example.myapp.</span></span> <span data-ttu-id="8a1d8-191">Maximale Länge: 64 Zeichen.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-191">Maximum length: 64 characters.</span></span>

## <a name="localizationinfo"></a><span data-ttu-id="8a1d8-192">localizationInfo</span><span class="sxs-lookup"><span data-stu-id="8a1d8-192">localizationInfo</span></span>

<span data-ttu-id="8a1d8-193">**Optional** – Objekt</span><span class="sxs-lookup"><span data-stu-id="8a1d8-193">**Optional** — object</span></span>

<span data-ttu-id="8a1d8-194">Ermöglicht die Angabe einer Standardsprache sowie Zeiger auf zusätzliche Sprachdateien.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-194">Allows the specification of a default language, as well as pointers to additional language files.</span></span> <span data-ttu-id="8a1d8-195">Siehe [Lokalisierung](~/concepts/build-and-test/apps-localization.md).</span><span class="sxs-lookup"><span data-stu-id="8a1d8-195">See [localization](~/concepts/build-and-test/apps-localization.md).</span></span>

|<span data-ttu-id="8a1d8-196">Name</span><span class="sxs-lookup"><span data-stu-id="8a1d8-196">Name</span></span>| <span data-ttu-id="8a1d8-197">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="8a1d8-197">Maximum size</span></span> | <span data-ttu-id="8a1d8-198">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="8a1d8-198">Required</span></span> | <span data-ttu-id="8a1d8-199">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="8a1d8-199">Description</span></span>|
|---|---|---|---|
|`defaultLanguageTag`||<span data-ttu-id="8a1d8-200">✔</span><span class="sxs-lookup"><span data-stu-id="8a1d8-200">✔</span></span>|<span data-ttu-id="8a1d8-201">Das Language-Tag der Zeichenfolgen in dieser Manifestdatei der obersten Ebene.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-201">The language tag of the strings in this top level manifest file.</span></span>|

### <a name="localizationinfoadditionallanguages"></a><span data-ttu-id="8a1d8-202">localizationInfo.additionalLanguages</span><span class="sxs-lookup"><span data-stu-id="8a1d8-202">localizationInfo.additionalLanguages</span></span>

<span data-ttu-id="8a1d8-203">Ein Array von Objekten, das zusätzliche Sprachübersetzungen angibt.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-203">An array of objects specifying additional language translations.</span></span>

|<span data-ttu-id="8a1d8-204">Name</span><span class="sxs-lookup"><span data-stu-id="8a1d8-204">Name</span></span>| <span data-ttu-id="8a1d8-205">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="8a1d8-205">Maximum size</span></span> | <span data-ttu-id="8a1d8-206">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="8a1d8-206">Required</span></span> | <span data-ttu-id="8a1d8-207">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="8a1d8-207">Description</span></span>|
|---|---|---|---|
|`languageTag`||<span data-ttu-id="8a1d8-208">✔</span><span class="sxs-lookup"><span data-stu-id="8a1d8-208">✔</span></span>|<span data-ttu-id="8a1d8-209">Das Language-Tag der Zeichenfolgen in der bereitgestellten Datei.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-209">The language tag of the strings in the provided file.</span></span>|
|`file`||<span data-ttu-id="8a1d8-210">✔</span><span class="sxs-lookup"><span data-stu-id="8a1d8-210">✔</span></span>|<span data-ttu-id="8a1d8-211">Ein relativer Dateipfad zu einer JSON-Datei, die die übersetzten Zeichenfolgen enthält.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-211">A relative file path to a the .json file containing the translated strings.</span></span>|

## <a name="icons"></a><span data-ttu-id="8a1d8-212">Symbole</span><span class="sxs-lookup"><span data-stu-id="8a1d8-212">icons</span></span>

<span data-ttu-id="8a1d8-213">**Erforderlich** – Objekt</span><span class="sxs-lookup"><span data-stu-id="8a1d8-213">**Required** — object</span></span>

<span data-ttu-id="8a1d8-214">Symbole, die in der Teams-App verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-214">Icons used within the Teams app.</span></span> <span data-ttu-id="8a1d8-215">Die Symboldateien müssen als Teil des Upload-Pakets enthalten sein.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-215">The icon files must be included as part of the upload package.</span></span> <span data-ttu-id="8a1d8-216">Weitere Informationen finden Sie unter [Icons](~/concepts/build-and-test/apps-package.md#icons) .</span><span class="sxs-lookup"><span data-stu-id="8a1d8-216">See [Icons](~/concepts/build-and-test/apps-package.md#icons) for more information.</span></span>

|<span data-ttu-id="8a1d8-217">Name</span><span class="sxs-lookup"><span data-stu-id="8a1d8-217">Name</span></span>| <span data-ttu-id="8a1d8-218">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="8a1d8-218">Maximum size</span></span> | <span data-ttu-id="8a1d8-219">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="8a1d8-219">Required</span></span> | <span data-ttu-id="8a1d8-220">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="8a1d8-220">Description</span></span>|
|---|---|---|---|
|`outline`|<span data-ttu-id="8a1d8-221">32 x 32 Pixel</span><span class="sxs-lookup"><span data-stu-id="8a1d8-221">32 x 32 pixels</span></span>|<span data-ttu-id="8a1d8-222">✔</span><span class="sxs-lookup"><span data-stu-id="8a1d8-222">✔</span></span>|<span data-ttu-id="8a1d8-223">Ein relativer Dateipfad zu einem transparenten 32x32 PNG-Gliederungssymbol.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-223">A relative file path to a transparent 32x32 PNG outline icon.</span></span>|
|`color`|<span data-ttu-id="8a1d8-224">192 x 192 Pixel</span><span class="sxs-lookup"><span data-stu-id="8a1d8-224">192 x 192 pixels</span></span>|<span data-ttu-id="8a1d8-225">✔</span><span class="sxs-lookup"><span data-stu-id="8a1d8-225">✔</span></span>|<span data-ttu-id="8a1d8-226">Ein relativer Dateipfad zu einem vollfarbigen 192x192 PNG-Symbol.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-226">A relative file path to a full color 192x192 PNG icon.</span></span>|

## <a name="accentcolor"></a><span data-ttu-id="8a1d8-227">accentColor</span><span class="sxs-lookup"><span data-stu-id="8a1d8-227">accentColor</span></span>

<span data-ttu-id="8a1d8-228">**Optional** – HTML-Hex-Farbcode</span><span class="sxs-lookup"><span data-stu-id="8a1d8-228">**Optional** — HTML Hex color code</span></span>

<span data-ttu-id="8a1d8-229">Eine Farbe, die in Verbindung mit und als Hintergrund für die Gliederungssymbole verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-229">A color to use in conjunction with and as a background for your outline icons.</span></span>

<span data-ttu-id="8a1d8-230">Der Wert muss ein gültiger HTML-Farb Code sein, der mit "#" beginnt, beispielsweise `#4464ee` .</span><span class="sxs-lookup"><span data-stu-id="8a1d8-230">The value must be a valid HTML color code starting with '#', for example `#4464ee`.</span></span>

## <a name="configurabletabs"></a><span data-ttu-id="8a1d8-231">configurableTabs</span><span class="sxs-lookup"><span data-stu-id="8a1d8-231">configurableTabs</span></span>

<span data-ttu-id="8a1d8-232">**Optional** – Array</span><span class="sxs-lookup"><span data-stu-id="8a1d8-232">**Optional** — array</span></span>

<span data-ttu-id="8a1d8-233">Wird verwendet, wenn Ihre APP-Erfahrung eine Team Kanal-registerkartenoberfläche aufweist, die eine zusätzliche Konfiguration erfordert, bevor Sie hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-233">Used when your app experience has a team channel tab experience that requires extra configuration before it is added.</span></span> <span data-ttu-id="8a1d8-234">Konfigurierbare Registerkarten werden nur im Bereich Teams (nicht persönlich) unterstützt, und derzeit wird nur **eine** Registerkarte pro App unterstützt.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-234">Configurable tabs are supported only in the teams scope (not personal), and currently only **one** tab per app is supported.</span></span>

|<span data-ttu-id="8a1d8-235">Name</span><span class="sxs-lookup"><span data-stu-id="8a1d8-235">Name</span></span>| <span data-ttu-id="8a1d8-236">Typ</span><span class="sxs-lookup"><span data-stu-id="8a1d8-236">Type</span></span>| <span data-ttu-id="8a1d8-237">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="8a1d8-237">Maximum size</span></span> | <span data-ttu-id="8a1d8-238">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="8a1d8-238">Required</span></span> | <span data-ttu-id="8a1d8-239">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="8a1d8-239">Description</span></span>|
|---|---|---|---|---|
|`configurationUrl`|<span data-ttu-id="8a1d8-240">string</span><span class="sxs-lookup"><span data-stu-id="8a1d8-240">string</span></span>|<span data-ttu-id="8a1d8-241">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="8a1d8-241">2048 characters</span></span>|<span data-ttu-id="8a1d8-242">✔</span><span class="sxs-lookup"><span data-stu-id="8a1d8-242">✔</span></span>|<span data-ttu-id="8a1d8-243">Die https://-URL, die beim Konfigurieren der Registerkarte verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-243">The https:// URL to use when configuring the tab.</span></span>|
|`scopes`|<span data-ttu-id="8a1d8-244">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="8a1d8-244">array of enum</span></span>|<span data-ttu-id="8a1d8-245">1</span><span class="sxs-lookup"><span data-stu-id="8a1d8-245">1</span></span>|<span data-ttu-id="8a1d8-246">✔</span><span class="sxs-lookup"><span data-stu-id="8a1d8-246">✔</span></span>|<span data-ttu-id="8a1d8-247">Derzeit unterstützen konfigurierbare Registerkarten nur die `team` `groupchat` Bereiche und.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-247">Currently, configurable tabs support only the `team` and `groupchat` scopes.</span></span> |
|`canUpdateConfiguration`|<span data-ttu-id="8a1d8-248">Boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="8a1d8-248">boolean</span></span>|||<span data-ttu-id="8a1d8-249">Ein Wert, der angibt, ob eine Instanz der Konfiguration der Registerkarte nach der Erstellung vom Benutzer aktualisiert werden kann.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-249">A value indicating whether an instance of the tab's configuration can be updated by the user after creation.</span></span> <span data-ttu-id="8a1d8-250">Default: **true**.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-250">Default: **true**.</span></span>|
|`sharePointPreviewImage`|<span data-ttu-id="8a1d8-251">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="8a1d8-251">string</span></span>|<span data-ttu-id="8a1d8-252">2048</span><span class="sxs-lookup"><span data-stu-id="8a1d8-252">2048</span></span>||<span data-ttu-id="8a1d8-253">Ein relativer Dateipfad zu einem Vorschaubild für die Registerkarte für die Verwendung in SharePoint.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-253">A relative file path to a tab preview image for use in SharePoint.</span></span> <span data-ttu-id="8a1d8-254">Größe 1024x768.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-254">Size 1024x768.</span></span> |
|`supportedSharePointHosts`|<span data-ttu-id="8a1d8-255">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="8a1d8-255">array of enum</span></span>|<span data-ttu-id="8a1d8-256">1</span><span class="sxs-lookup"><span data-stu-id="8a1d8-256">1</span></span>||<span data-ttu-id="8a1d8-257">Definiert, wie die Registerkarte in SharePoint zur Verfügung gestellt wird.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-257">Defines how your tab will be made available in SharePoint.</span></span> <span data-ttu-id="8a1d8-258">Optionen sind `sharePointFullPage` und `sharePointWebPart`</span><span class="sxs-lookup"><span data-stu-id="8a1d8-258">Options are `sharePointFullPage` and `sharePointWebPart`</span></span> |

## <a name="statictabs"></a><span data-ttu-id="8a1d8-259">staticTabs</span><span class="sxs-lookup"><span data-stu-id="8a1d8-259">staticTabs</span></span>

<span data-ttu-id="8a1d8-260">**Optional** – Array</span><span class="sxs-lookup"><span data-stu-id="8a1d8-260">**Optional** — array</span></span>

<span data-ttu-id="8a1d8-261">Definiert eine Gruppe von Registerkarten, die standardmäßig "fixiert" werden können, ohne dass der Benutzer Sie manuell hinzufügt.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-261">Defines a set of tabs that can be "pinned" by default, without the user adding them manually.</span></span> <span data-ttu-id="8a1d8-262">Im Bereich deklarierte statische Registerkarten `personal` werden immer an die persönliche Benutzeroberfläche der APP angeheftet.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-262">Static tabs declared in `personal` scope are always pinned to the app's personal experience.</span></span> <span data-ttu-id="8a1d8-263">Im Bereich deklarierte statische Registerkarten `team` werden derzeit nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-263">Static tabs declared in the `team` scope are currently not supported.</span></span>

<span data-ttu-id="8a1d8-264">Dieses Element ist ein Array (maximal 16 Elemente) mit allen Elementen des Typs `object` .</span><span class="sxs-lookup"><span data-stu-id="8a1d8-264">This item is an array (maximum of 16 elements) with all elements of the type `object`.</span></span> <span data-ttu-id="8a1d8-265">Dieser Block ist nur für Lösungen erforderlich, die eine statische Registerkarten Lösung bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-265">This block is required only for solutions that provide a static tab solution.</span></span>

|<span data-ttu-id="8a1d8-266">Name</span><span class="sxs-lookup"><span data-stu-id="8a1d8-266">Name</span></span>| <span data-ttu-id="8a1d8-267">Typ</span><span class="sxs-lookup"><span data-stu-id="8a1d8-267">Type</span></span>| <span data-ttu-id="8a1d8-268">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="8a1d8-268">Maximum size</span></span> | <span data-ttu-id="8a1d8-269">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="8a1d8-269">Required</span></span> | <span data-ttu-id="8a1d8-270">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="8a1d8-270">Description</span></span>|
|---|---|---|---|---|
|`entityId`|<span data-ttu-id="8a1d8-271">string</span><span class="sxs-lookup"><span data-stu-id="8a1d8-271">string</span></span>|<span data-ttu-id="8a1d8-272">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="8a1d8-272">64 characters</span></span>|<span data-ttu-id="8a1d8-273">✔</span><span class="sxs-lookup"><span data-stu-id="8a1d8-273">✔</span></span>|<span data-ttu-id="8a1d8-274">Ein eindeutiger Bezeichner für die Entität, die auf der Registerkarte angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-274">A unique identifier for the entity that the tab displays.</span></span>|
|`name`|<span data-ttu-id="8a1d8-275">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="8a1d8-275">string</span></span>|<span data-ttu-id="8a1d8-276">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="8a1d8-276">128 characters</span></span>|<span data-ttu-id="8a1d8-277">✔</span><span class="sxs-lookup"><span data-stu-id="8a1d8-277">✔</span></span>|<span data-ttu-id="8a1d8-278">Der Anzeigename der Registerkarte in der Kanalschnittstelle.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-278">The display name of the tab in the channel interface.</span></span>|
|`contentUrl`|<span data-ttu-id="8a1d8-279">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="8a1d8-279">string</span></span>|<span data-ttu-id="8a1d8-280">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="8a1d8-280">2048 characters</span></span>|<span data-ttu-id="8a1d8-281">✔</span><span class="sxs-lookup"><span data-stu-id="8a1d8-281">✔</span></span>|<span data-ttu-id="8a1d8-282">Die https://-URL, die auf die Benutzeroberfläche der Entität zeigt, die im Canvas "Teams" angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-282">The https:// URL that points to the entity UI to be displayed in the Teams canvas.</span></span>|
|`websiteUrl`|<span data-ttu-id="8a1d8-283">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="8a1d8-283">string</span></span>|<span data-ttu-id="8a1d8-284">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="8a1d8-284">2048 characters</span></span>||<span data-ttu-id="8a1d8-285">Die https://-URL, auf die verwiesen wird, wenn ein Benutzer sich für die Anzeige in einem Browser entscheidet.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-285">The https:// URL to point at if a user opts to view in a browser.</span></span>|
|`scopes`|<span data-ttu-id="8a1d8-286">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="8a1d8-286">array of enum</span></span>|<span data-ttu-id="8a1d8-287">1</span><span class="sxs-lookup"><span data-stu-id="8a1d8-287">1</span></span>|<span data-ttu-id="8a1d8-288">✔</span><span class="sxs-lookup"><span data-stu-id="8a1d8-288">✔</span></span>|<span data-ttu-id="8a1d8-289">Derzeit unterstützen statische Registerkarten nur den `personal` Bereich, was bedeutet, dass Sie nur als Teil der persönlichen Benutzeroberfläche vorgesehen werden kann.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-289">Currently, static tabs support only the `personal` scope, which means it can be provisioned only as part of the personal experience.</span></span>|

> [!NOTE]
> <span data-ttu-id="8a1d8-290">Wenn auf Ihren Registerkartenkontext abhängige Informationen zum Anzeigen relevanter Inhalte oder zum Initiieren eines Authentifizierungs Flusses erforderlich sind, *Lesen Sie* den [Bereich Kontext für Ihre Microsoft Teams-Registerkarte abrufen](../../tabs/how-to/access-teams-context.md).</span><span class="sxs-lookup"><span data-stu-id="8a1d8-290">If your tabs require context-dependent information to display relevant content or for initiating an authentication flow, *see* [Get context for your Microsoft Teams tab](../../tabs/how-to/access-teams-context.md).</span></span>

## <a name="bots"></a><span data-ttu-id="8a1d8-291">Bots</span><span class="sxs-lookup"><span data-stu-id="8a1d8-291">bots</span></span>

<span data-ttu-id="8a1d8-292">**Optional** – Array</span><span class="sxs-lookup"><span data-stu-id="8a1d8-292">**Optional** — array</span></span>

<span data-ttu-id="8a1d8-293">Definiert eine bot-Lösung zusammen mit optionalen Informationen wie Standardbefehls Eigenschaften.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-293">Defines a bot solution, along with optional information such as default command properties.</span></span>

<span data-ttu-id="8a1d8-294">Das Element ist ein Array (Maximum von nur 1 Element &mdash; , das derzeit nur ein bot pro App zulässig ist) mit allen Elementen des Typs `object` .</span><span class="sxs-lookup"><span data-stu-id="8a1d8-294">The item is an array (maximum of only 1 element&mdash;currently only one bot is allowed per app) with all elements of the type `object`.</span></span> <span data-ttu-id="8a1d8-295">Dieser Block ist nur für Lösungen erforderlich, die eine bot-Erfahrung bieten.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-295">This block is required only for solutions that provide a bot experience.</span></span>

|<span data-ttu-id="8a1d8-296">Name</span><span class="sxs-lookup"><span data-stu-id="8a1d8-296">Name</span></span>| <span data-ttu-id="8a1d8-297">Typ</span><span class="sxs-lookup"><span data-stu-id="8a1d8-297">Type</span></span>| <span data-ttu-id="8a1d8-298">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="8a1d8-298">Maximum size</span></span> | <span data-ttu-id="8a1d8-299">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="8a1d8-299">Required</span></span> | <span data-ttu-id="8a1d8-300">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="8a1d8-300">Description</span></span>|
|---|---|---|---|---|
|`botId`|<span data-ttu-id="8a1d8-301">string</span><span class="sxs-lookup"><span data-stu-id="8a1d8-301">string</span></span>|<span data-ttu-id="8a1d8-302">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="8a1d8-302">64 characters</span></span>|<span data-ttu-id="8a1d8-303">✔</span><span class="sxs-lookup"><span data-stu-id="8a1d8-303">✔</span></span>|<span data-ttu-id="8a1d8-304">Die eindeutige Microsoft-App-ID für den Bot, wie bei Bot Framework registriert.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-304">The unique Microsoft app ID for the bot as registered with the Bot Framework.</span></span> <span data-ttu-id="8a1d8-305">Dies kann auch die gesamte [App-ID](#id)entsprechen.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-305">This may well be the same as the overall [app ID](#id).</span></span>|
|`scopes`|<span data-ttu-id="8a1d8-306">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="8a1d8-306">array of enum</span></span>|<span data-ttu-id="8a1d8-307">3</span><span class="sxs-lookup"><span data-stu-id="8a1d8-307">3</span></span>|<span data-ttu-id="8a1d8-308">✔</span><span class="sxs-lookup"><span data-stu-id="8a1d8-308">✔</span></span>|<span data-ttu-id="8a1d8-309">Gibt an, ob der Bot eine Umgebung im Kontext eines Kanals in einem `team` oder Gruppenchat (`groupchat`) ist, oder aber eine Umgebung einzig für einen bestimmten Benutzer (`personal`).</span><span class="sxs-lookup"><span data-stu-id="8a1d8-309">Specifies whether the bot offers an experience in the context of a channel in a `team`, in a group chat (`groupchat`), or an experience scoped to an individual user alone (`personal`).</span></span> <span data-ttu-id="8a1d8-310">Diese Optionen sind nicht exklusiv.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-310">These options are non-exclusive.</span></span>|
|`needsChannelSelector`|<span data-ttu-id="8a1d8-311">Boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="8a1d8-311">boolean</span></span>|||<span data-ttu-id="8a1d8-312">Beschreibt, ob der Bot einen Benutzerhinweis verwendet, um den Bot einem bestimmten Kanal hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-312">Describes whether or not the bot utilizes a user hint to add the bot to a specific channel.</span></span> <span data-ttu-id="8a1d8-313">Standard **`false`**</span><span class="sxs-lookup"><span data-stu-id="8a1d8-313">Default: **`false`**</span></span>|
|`isNotificationOnly`|<span data-ttu-id="8a1d8-314">Boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="8a1d8-314">boolean</span></span>|||<span data-ttu-id="8a1d8-315">Gibt an, ob ein Bot ein unidirektionaler Bot ausschließlich für Benachrichtigungen ist (im Gegensatz zu einem dialogorientierten Bot).</span><span class="sxs-lookup"><span data-stu-id="8a1d8-315">Indicates whether a bot is a one-way, notification-only bot, as opposed to a conversational bot.</span></span> <span data-ttu-id="8a1d8-316">Standard `**false**`</span><span class="sxs-lookup"><span data-stu-id="8a1d8-316">Default: `**false**`</span></span>|
|`supportsFiles`|<span data-ttu-id="8a1d8-317">Boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="8a1d8-317">boolean</span></span>|||<span data-ttu-id="8a1d8-318">Gibt an, ob der Bot die Möglichkeit zum Hochladen/Herunterladen von Dateien in persönliche Chats unterstützt.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-318">Indicates whether the bot supports the ability to upload/download files in personal chat.</span></span> <span data-ttu-id="8a1d8-319">Standard **`false`**</span><span class="sxs-lookup"><span data-stu-id="8a1d8-319">Default: **`false`**</span></span>|

### <a name="botscommandlists"></a><span data-ttu-id="8a1d8-320">Bots. commandLists</span><span class="sxs-lookup"><span data-stu-id="8a1d8-320">bots.commandLists</span></span>

<span data-ttu-id="8a1d8-321">Eine optionale Liste von Befehlen, die ihr bot Benutzern empfehlen kann.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-321">An optional list of commands that your bot can recommend to users.</span></span> <span data-ttu-id="8a1d8-322">Das Objekt ist ein Array (Maximum von 2 Elementen) mit allen Elementen des Typs `object` ; Sie müssen für jeden Bereich, den Ihr bot unterstützt, eine separate Befehlsliste definieren.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-322">The object is an array (maximum of 2 elements) with all elements of type `object`; you must define a separate command list for each scope that your bot supports.</span></span> <span data-ttu-id="8a1d8-323">Weitere Informationen finden Sie unter [bot-Menüs](~/bots/how-to/create-a-bot-commands-menu.md) .</span><span class="sxs-lookup"><span data-stu-id="8a1d8-323">See [Bot menus](~/bots/how-to/create-a-bot-commands-menu.md) for more information.</span></span>

|<span data-ttu-id="8a1d8-324">Name</span><span class="sxs-lookup"><span data-stu-id="8a1d8-324">Name</span></span>| <span data-ttu-id="8a1d8-325">Typ</span><span class="sxs-lookup"><span data-stu-id="8a1d8-325">Type</span></span>| <span data-ttu-id="8a1d8-326">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="8a1d8-326">Maximum size</span></span> | <span data-ttu-id="8a1d8-327">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="8a1d8-327">Required</span></span> | <span data-ttu-id="8a1d8-328">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="8a1d8-328">Description</span></span>|
|---|---|---|---|---|
|`items.scopes`|<span data-ttu-id="8a1d8-329">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="8a1d8-329">array of enum</span></span>|<span data-ttu-id="8a1d8-330">3</span><span class="sxs-lookup"><span data-stu-id="8a1d8-330">3</span></span>|<span data-ttu-id="8a1d8-331">✔</span><span class="sxs-lookup"><span data-stu-id="8a1d8-331">✔</span></span>|<span data-ttu-id="8a1d8-332">Gibt den Bereich an, für den die Befehlsliste gültig ist.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-332">Specifies the scope for which the command list is valid.</span></span> <span data-ttu-id="8a1d8-333">Mögliche Optionen sind `team`, `personal` und `groupchat`.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-333">Options are `team`, `personal`, and `groupchat`.</span></span>|
|`items.commands`|<span data-ttu-id="8a1d8-334">Array von Objekten</span><span class="sxs-lookup"><span data-stu-id="8a1d8-334">array of objects</span></span>|<span data-ttu-id="8a1d8-335">10 </span><span class="sxs-lookup"><span data-stu-id="8a1d8-335">10</span></span>|<span data-ttu-id="8a1d8-336">✔</span><span class="sxs-lookup"><span data-stu-id="8a1d8-336">✔</span></span>|<span data-ttu-id="8a1d8-337">Ein Array von Befehlen, die der Bot unterstützt:</span><span class="sxs-lookup"><span data-stu-id="8a1d8-337">An array of commands the bot supports:</span></span><br><span data-ttu-id="8a1d8-338">`title`: Name des Bot-Befehls (string, 32)</span><span class="sxs-lookup"><span data-stu-id="8a1d8-338">`title`: the bot command name (string, 32)</span></span><br><span data-ttu-id="8a1d8-339">`description`: einfache Beschreibung oder Beispiel für die Befehlssyntax und zugehörige Argumente (string, 128)</span><span class="sxs-lookup"><span data-stu-id="8a1d8-339">`description`: a simple description or example of the command syntax and its argument (string, 128)</span></span>|

### <a name="botscommandlistscommands"></a><span data-ttu-id="8a1d8-340">Bots. commandLists. Commands</span><span class="sxs-lookup"><span data-stu-id="8a1d8-340">bots.commandLists.commands</span></span>

|<span data-ttu-id="8a1d8-341">Name</span><span class="sxs-lookup"><span data-stu-id="8a1d8-341">Name</span></span>| <span data-ttu-id="8a1d8-342">Typ</span><span class="sxs-lookup"><span data-stu-id="8a1d8-342">Type</span></span>| <span data-ttu-id="8a1d8-343">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="8a1d8-343">Maximum size</span></span> | <span data-ttu-id="8a1d8-344">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="8a1d8-344">Required</span></span> | <span data-ttu-id="8a1d8-345">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="8a1d8-345">Description</span></span>|
|---|---|---|---|---|
|<span data-ttu-id="8a1d8-346">title</span><span class="sxs-lookup"><span data-stu-id="8a1d8-346">title</span></span>|<span data-ttu-id="8a1d8-347">string</span><span class="sxs-lookup"><span data-stu-id="8a1d8-347">string</span></span>|<span data-ttu-id="8a1d8-348">12 </span><span class="sxs-lookup"><span data-stu-id="8a1d8-348">12</span></span>|<span data-ttu-id="8a1d8-349">✔</span><span class="sxs-lookup"><span data-stu-id="8a1d8-349">✔</span></span>|<span data-ttu-id="8a1d8-350">Der Name des bot-Befehls</span><span class="sxs-lookup"><span data-stu-id="8a1d8-350">The bot command name</span></span>|
|<span data-ttu-id="8a1d8-351">description</span><span class="sxs-lookup"><span data-stu-id="8a1d8-351">description</span></span>|<span data-ttu-id="8a1d8-352">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="8a1d8-352">string</span></span>|<span data-ttu-id="8a1d8-353">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="8a1d8-353">128 characters</span></span>|<span data-ttu-id="8a1d8-354">✔</span><span class="sxs-lookup"><span data-stu-id="8a1d8-354">✔</span></span>|<span data-ttu-id="8a1d8-355">Eine einfache Textbeschreibung oder ein Beispiel für die Befehlssyntax und ihre Argumente.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-355">A simple text description or an example of the command syntax and its arguments.</span></span>|

## <a name="connectors"></a><span data-ttu-id="8a1d8-356">Connectors</span><span class="sxs-lookup"><span data-stu-id="8a1d8-356">connectors</span></span>

<span data-ttu-id="8a1d8-357">**Optional** – Array</span><span class="sxs-lookup"><span data-stu-id="8a1d8-357">**Optional** — array</span></span>

<span data-ttu-id="8a1d8-358">Der `connectors` Block definiert einen Office 365-Konnektor für die app.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-358">The `connectors` block defines an Office 365 Connector for the app.</span></span>

<span data-ttu-id="8a1d8-359">Das Objekt ist ein Array (Maximum of 1-Element) mit allen Elementen des Typs `object` .</span><span class="sxs-lookup"><span data-stu-id="8a1d8-359">The object is an array (maximum of 1 element) with all elements of type `object`.</span></span> <span data-ttu-id="8a1d8-360">Dieser Block ist nur für Lösungen erforderlich, die einen Connector bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-360">This block is required only for solutions that provide a Connector.</span></span>

|<span data-ttu-id="8a1d8-361">Name</span><span class="sxs-lookup"><span data-stu-id="8a1d8-361">Name</span></span>| <span data-ttu-id="8a1d8-362">Typ</span><span class="sxs-lookup"><span data-stu-id="8a1d8-362">Type</span></span>| <span data-ttu-id="8a1d8-363">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="8a1d8-363">Maximum size</span></span> | <span data-ttu-id="8a1d8-364">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="8a1d8-364">Required</span></span> | <span data-ttu-id="8a1d8-365">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="8a1d8-365">Description</span></span>|
|---|---|---|---|---|
|`configurationUrl`|<span data-ttu-id="8a1d8-366">string</span><span class="sxs-lookup"><span data-stu-id="8a1d8-366">string</span></span>|<span data-ttu-id="8a1d8-367">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="8a1d8-367">2048 characters</span></span>|<span data-ttu-id="8a1d8-368">✔</span><span class="sxs-lookup"><span data-stu-id="8a1d8-368">✔</span></span>|<span data-ttu-id="8a1d8-369">Die https://-URL, die beim Konfigurieren des Connectors verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-369">The https:// URL to use when configuring the connector.</span></span>|
|`scopes`|<span data-ttu-id="8a1d8-370">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="8a1d8-370">array of enum</span></span>|<span data-ttu-id="8a1d8-371">1</span><span class="sxs-lookup"><span data-stu-id="8a1d8-371">1</span></span>|<span data-ttu-id="8a1d8-372">✔</span><span class="sxs-lookup"><span data-stu-id="8a1d8-372">✔</span></span>|<span data-ttu-id="8a1d8-373">Gibt an, ob der Connector eine Erfahrung im Kontext eines Kanals in a bietet `team` oder ein Erlebnis, das allein auf einen einzelnen Benutzer beschränkt ist ( `personal` ).</span><span class="sxs-lookup"><span data-stu-id="8a1d8-373">Specifies whether the Connector offers an experience in the context of a channel in a `team`, or an experience scoped to an individual user alone (`personal`).</span></span> <span data-ttu-id="8a1d8-374">Derzeit wird nur der `team` Bereich unterstützt.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-374">Currently, only the `team` scope is supported.</span></span>|
|`connectorId`|<span data-ttu-id="8a1d8-375">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="8a1d8-375">string</span></span>|<span data-ttu-id="8a1d8-376">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="8a1d8-376">64 characters</span></span>|<span data-ttu-id="8a1d8-377">✔</span><span class="sxs-lookup"><span data-stu-id="8a1d8-377">✔</span></span>|<span data-ttu-id="8a1d8-378">Ein eindeutiger Bezeichner für den Connector, der seiner ID im [Entwickler Dashboard für Connectors](https://aka.ms/connectorsdashboard)entspricht.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-378">A unique identifier for the Connector that matches its ID in the [Connectors Developer Dashboard](https://aka.ms/connectorsdashboard).</span></span>|

## <a name="composeextensions"></a><span data-ttu-id="8a1d8-379">composeExtensions</span><span class="sxs-lookup"><span data-stu-id="8a1d8-379">composeExtensions</span></span>

<span data-ttu-id="8a1d8-380">**Optional** – Array</span><span class="sxs-lookup"><span data-stu-id="8a1d8-380">**Optional** — array</span></span>

<span data-ttu-id="8a1d8-381">Definiert eine Messaging Erweiterung für die app.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-381">Defines a messaging extension for the app.</span></span>

> [!NOTE]
> <span data-ttu-id="8a1d8-382">Der Name des Features wurde von "Erstell Erweiterung" in "Messaging Extension" im November 2017 geändert, aber der Manifestname bleibt unverändert, sodass vorhandene Erweiterungen weiterhin funktionieren.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-382">The name of the feature was changed from "compose extension" to "messaging extension" in November, 2017, but the manifest name remains the same so that existing extensions continue to function.</span></span>

<span data-ttu-id="8a1d8-383">Das Element ist ein Array (Maximum of 1-Element) mit allen Elementen des Typs `object` .</span><span class="sxs-lookup"><span data-stu-id="8a1d8-383">The item is an array (maximum of 1 element) with all elements of type `object`.</span></span> <span data-ttu-id="8a1d8-384">Dieser Block ist nur für Lösungen erforderlich, die eine Messaging Erweiterung bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-384">This block is required only for solutions that provide a messaging extension.</span></span>

|<span data-ttu-id="8a1d8-385">Name</span><span class="sxs-lookup"><span data-stu-id="8a1d8-385">Name</span></span>| <span data-ttu-id="8a1d8-386">Typ</span><span class="sxs-lookup"><span data-stu-id="8a1d8-386">Type</span></span> | <span data-ttu-id="8a1d8-387">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="8a1d8-387">Maximum Size</span></span> | <span data-ttu-id="8a1d8-388">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="8a1d8-388">Required</span></span> | <span data-ttu-id="8a1d8-389">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="8a1d8-389">Description</span></span>|
|---|---|---|---|---|
|`botId`|<span data-ttu-id="8a1d8-390">string</span><span class="sxs-lookup"><span data-stu-id="8a1d8-390">string</span></span>|<span data-ttu-id="8a1d8-391">64</span><span class="sxs-lookup"><span data-stu-id="8a1d8-391">64</span></span>|<span data-ttu-id="8a1d8-392">✔</span><span class="sxs-lookup"><span data-stu-id="8a1d8-392">✔</span></span>|<span data-ttu-id="8a1d8-393">Die eindeutige Microsoft-App-ID für den bot, der die Messaging Erweiterung unterstützt, wie Sie mit dem bot-Framework registriert wurde.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-393">The unique Microsoft app ID for the bot that backs the messaging extension, as registered with the Bot Framework.</span></span> <span data-ttu-id="8a1d8-394">Dies kann auch die gesamte APP-ID entsprechen.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-394">This may well be the same as the overall App ID.</span></span>|
|`commands`|<span data-ttu-id="8a1d8-395">Array von Objekten</span><span class="sxs-lookup"><span data-stu-id="8a1d8-395">array of objects</span></span>|<span data-ttu-id="8a1d8-396">10 </span><span class="sxs-lookup"><span data-stu-id="8a1d8-396">10</span></span>|<span data-ttu-id="8a1d8-397">✔</span><span class="sxs-lookup"><span data-stu-id="8a1d8-397">✔</span></span>|<span data-ttu-id="8a1d8-398">Array von Befehlen, die von der Messaging-Erweiterung unterstützt werden</span><span class="sxs-lookup"><span data-stu-id="8a1d8-398">array of commands the messaging extension supports</span></span>|
|`canUpdateConfiguration`|<span data-ttu-id="8a1d8-399">Boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="8a1d8-399">boolean</span></span>|||<span data-ttu-id="8a1d8-400">Ein Wert, der angibt, ob die Konfiguration einer Messaging Erweiterung vom Benutzer aktualisiert werden kann.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-400">A value indicating whether the configuration of a messaging extension can be updated by the user.</span></span> <span data-ttu-id="8a1d8-401">Standard: **False**.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-401">Default: **false**.</span></span>|
|`messageHandlers`|<span data-ttu-id="8a1d8-402">Array von Objekten</span><span class="sxs-lookup"><span data-stu-id="8a1d8-402">array of Objects</span></span>|<span data-ttu-id="8a1d8-403">5 </span><span class="sxs-lookup"><span data-stu-id="8a1d8-403">5</span></span>||<span data-ttu-id="8a1d8-404">Eine Liste von Handlern, mit denen apps aufgerufen werden können, wenn bestimmte Bedingungen erfüllt sind.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-404">A list of handlers that allow apps to be invoked when certain conditions are met.</span></span> <span data-ttu-id="8a1d8-405">Domänen müssen ebenfalls in aufgeführt sein. `validDomains`</span><span class="sxs-lookup"><span data-stu-id="8a1d8-405">Domains must also be listed in `validDomains`</span></span>|
|`messageHandlers.type`|<span data-ttu-id="8a1d8-406">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="8a1d8-406">string</span></span>|||<span data-ttu-id="8a1d8-407">Der Typ des Nachrichten Handlers.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-407">The type of message handler.</span></span> <span data-ttu-id="8a1d8-408">Muss `"link"` sein.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-408">Must be `"link"`.</span></span>|
|`messageHandlers.value.domains`|<span data-ttu-id="8a1d8-409">Array von Zeichenfolgen</span><span class="sxs-lookup"><span data-stu-id="8a1d8-409">array of Strings</span></span>|||<span data-ttu-id="8a1d8-410">Array von Domänen, für die der Link Nachrichtenhandler registriert werden kann.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-410">array of domains that the link message handler can register for.</span></span>|

### <a name="composeextensionscommands"></a><span data-ttu-id="8a1d8-411">composeExtensions. Commands</span><span class="sxs-lookup"><span data-stu-id="8a1d8-411">composeExtensions.commands</span></span>

<span data-ttu-id="8a1d8-412">Ihre Messaging Erweiterung sollte einen oder mehrere Befehle deklarieren.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-412">Your messaging extension should declare one or more commands.</span></span> <span data-ttu-id="8a1d8-413">Jeder Befehl wird in Microsoft Teams als potenzielle Interaktion aus dem Benutzeroberflächen basierten Einstiegspfad angezeigt.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-413">Each command appears in Microsoft Teams as a potential interaction from the UI-based entry point.</span></span> <span data-ttu-id="8a1d8-414">Es gibt maximal 10 Befehle.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-414">There is a maximum of 10 commands.</span></span>

<span data-ttu-id="8a1d8-415">Jedes Command-Element ist ein Objekt mit der folgenden Struktur:</span><span class="sxs-lookup"><span data-stu-id="8a1d8-415">Each command item is an object with the following structure:</span></span>

|<span data-ttu-id="8a1d8-416">Name</span><span class="sxs-lookup"><span data-stu-id="8a1d8-416">Name</span></span>| <span data-ttu-id="8a1d8-417">Typ</span><span class="sxs-lookup"><span data-stu-id="8a1d8-417">Type</span></span>| <span data-ttu-id="8a1d8-418">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="8a1d8-418">Maximum size</span></span> | <span data-ttu-id="8a1d8-419">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="8a1d8-419">Required</span></span> | <span data-ttu-id="8a1d8-420">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="8a1d8-420">Description</span></span>|
|---|---|---|---|---|
|`id`|<span data-ttu-id="8a1d8-421">string</span><span class="sxs-lookup"><span data-stu-id="8a1d8-421">string</span></span>|<span data-ttu-id="8a1d8-422">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="8a1d8-422">64 characters</span></span>|<span data-ttu-id="8a1d8-423">✔</span><span class="sxs-lookup"><span data-stu-id="8a1d8-423">✔</span></span>|<span data-ttu-id="8a1d8-424">Die ID für den Befehl.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-424">The ID for the command.</span></span>|
|`title`|<span data-ttu-id="8a1d8-425">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="8a1d8-425">string</span></span>|<span data-ttu-id="8a1d8-426">32 Zeichen</span><span class="sxs-lookup"><span data-stu-id="8a1d8-426">32 characters</span></span>|<span data-ttu-id="8a1d8-427">✔</span><span class="sxs-lookup"><span data-stu-id="8a1d8-427">✔</span></span>|<span data-ttu-id="8a1d8-428">Der benutzerfreundliche Befehlsname.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-428">The user-friendly command name.</span></span>|
|`type`|<span data-ttu-id="8a1d8-429">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="8a1d8-429">string</span></span>|<span data-ttu-id="8a1d8-430">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="8a1d8-430">64 characters</span></span>||<span data-ttu-id="8a1d8-431">Der Typ des Befehls.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-431">Type of the command.</span></span> <span data-ttu-id="8a1d8-432">Einer von `query` oder `action` .</span><span class="sxs-lookup"><span data-stu-id="8a1d8-432">One of `query` or `action`.</span></span> <span data-ttu-id="8a1d8-433">Standard: **Query**.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-433">Default: **query**.</span></span>|
|`description`|<span data-ttu-id="8a1d8-434">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="8a1d8-434">string</span></span>|<span data-ttu-id="8a1d8-435">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="8a1d8-435">128 characters</span></span>||<span data-ttu-id="8a1d8-436">Die Beschreibung, die den Benutzern angezeigt wird, um den Zweck dieses Befehls anzugeben.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-436">The description that appears to users to indicate the purpose of this command.</span></span>|
|`initialRun`|<span data-ttu-id="8a1d8-437">Boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="8a1d8-437">boolean</span></span>|||<span data-ttu-id="8a1d8-438">Ein boolescher Wert, der angibt, ob der Befehl anfänglich ohne Parameter ausgeführt werden soll.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-438">A boolean value that indicates whether the command should be run initially with no parameters.</span></span> <span data-ttu-id="8a1d8-439">Standard: **False**.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-439">Default: **false**.</span></span>|
|`context`|<span data-ttu-id="8a1d8-440">Array von Zeichenfolgen</span><span class="sxs-lookup"><span data-stu-id="8a1d8-440">array of Strings</span></span>|<span data-ttu-id="8a1d8-441">3</span><span class="sxs-lookup"><span data-stu-id="8a1d8-441">3</span></span>||<span data-ttu-id="8a1d8-442">Definiert, woher die Nachrichten Erweiterung aufgerufen werden kann.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-442">Defines where the message extension can be invoked from.</span></span> <span data-ttu-id="8a1d8-443">Eine beliebige Kombination von `compose` , `commandBox` , `message` .</span><span class="sxs-lookup"><span data-stu-id="8a1d8-443">Any combination of`compose`,`commandBox`,`message` .</span></span> <span data-ttu-id="8a1d8-444">Der Standardwert ist `["compose","commandBox"]`.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-444">Default is `["compose","commandBox"]`.</span></span>|
|`fetchTask`|<span data-ttu-id="8a1d8-445">Boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="8a1d8-445">boolean</span></span>|||<span data-ttu-id="8a1d8-446">Ein boolescher Wert, der angibt, ob das Aufgabenmodul dynamisch abgerufen werden soll.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-446">A boolean value that indicates if it should fetch the task module dynamically.</span></span> <span data-ttu-id="8a1d8-447">Standard: **False**.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-447">Default: **false**.</span></span>|
|`taskInfo`|<span data-ttu-id="8a1d8-448">Objekt</span><span class="sxs-lookup"><span data-stu-id="8a1d8-448">object</span></span>|||<span data-ttu-id="8a1d8-449">Geben Sie das Aufgabenmodul an, das beim Verwenden eines Messaging Erweiterungs Befehls vorab zu laden ist.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-449">Specify the task module to pre-load when using a messaging extension command.</span></span>|
|`taskInfo.title`|<span data-ttu-id="8a1d8-450">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="8a1d8-450">string</span></span>|<span data-ttu-id="8a1d8-451">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="8a1d8-451">64 characters</span></span>||<span data-ttu-id="8a1d8-452">Ursprünglicher Dialogtitel.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-452">Initial dialog title.</span></span>|
|`taskInfo.width`|<span data-ttu-id="8a1d8-453">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="8a1d8-453">string</span></span>|||<span data-ttu-id="8a1d8-454">Dialog Breite-entweder eine Zahl in Pixel oder ein Standardlayout wie "Large", "Medium" oder "Small".</span><span class="sxs-lookup"><span data-stu-id="8a1d8-454">Dialog width - either a number in pixels or default layout such as 'large', 'medium', or 'small'.</span></span>|
|`taskInfo.height`|<span data-ttu-id="8a1d8-455">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="8a1d8-455">string</span></span>|||<span data-ttu-id="8a1d8-456">Dialog Feld Höhe: entweder eine Zahl in Pixel oder ein Standardlayout wie "Large", "Medium" oder "Small".</span><span class="sxs-lookup"><span data-stu-id="8a1d8-456">Dialog height - either a number in pixels or default layout such as 'large', 'medium', or 'small'.</span></span>|
|`taskInfo.url`|<span data-ttu-id="8a1d8-457">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="8a1d8-457">string</span></span>|||<span data-ttu-id="8a1d8-458">Anfängliche WebView-URL.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-458">Initial webview URL.</span></span>|
|`parameters`|<span data-ttu-id="8a1d8-459">Array von Object</span><span class="sxs-lookup"><span data-stu-id="8a1d8-459">array of object</span></span>|<span data-ttu-id="8a1d8-460">5 Elemente</span><span class="sxs-lookup"><span data-stu-id="8a1d8-460">5 items</span></span>|<span data-ttu-id="8a1d8-461">✔</span><span class="sxs-lookup"><span data-stu-id="8a1d8-461">✔</span></span>|<span data-ttu-id="8a1d8-462">Die Liste der Parameter, die der Befehl benötigt.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-462">The list of parameters the command takes.</span></span> <span data-ttu-id="8a1d8-463">Minimum: 1; Maximum: 5.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-463">Minimum: 1; maximum: 5.</span></span>|
|`parameters.name`|<span data-ttu-id="8a1d8-464">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="8a1d8-464">string</span></span>|<span data-ttu-id="8a1d8-465">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="8a1d8-465">64 characters</span></span>|<span data-ttu-id="8a1d8-466">✔</span><span class="sxs-lookup"><span data-stu-id="8a1d8-466">✔</span></span>|<span data-ttu-id="8a1d8-467">Der Name des Parameters, wie er im Client angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-467">The name of the parameter as it appears in the client.</span></span> <span data-ttu-id="8a1d8-468">Dies ist in der Benutzeranforderung enthalten.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-468">This is included in the user request.</span></span>|
|`parameters.title`|<span data-ttu-id="8a1d8-469">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="8a1d8-469">string</span></span>|<span data-ttu-id="8a1d8-470">32 Zeichen</span><span class="sxs-lookup"><span data-stu-id="8a1d8-470">32 characters</span></span>|<span data-ttu-id="8a1d8-471">✔</span><span class="sxs-lookup"><span data-stu-id="8a1d8-471">✔</span></span>|<span data-ttu-id="8a1d8-472">Benutzerfreundlicher Titel für den Parameter.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-472">User-friendly title for the parameter.</span></span>|
|`parameters.description`|<span data-ttu-id="8a1d8-473">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="8a1d8-473">string</span></span>|<span data-ttu-id="8a1d8-474">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="8a1d8-474">128 characters</span></span>||<span data-ttu-id="8a1d8-475">Benutzerfreundliche Zeichenfolge, die den Zweck dieses Parameters beschreibt.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-475">User-friendly string that describes this parameter’s purpose.</span></span>|
|`parameters.value`|<span data-ttu-id="8a1d8-476">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="8a1d8-476">string</span></span>|<span data-ttu-id="8a1d8-477">512 Zeichen</span><span class="sxs-lookup"><span data-stu-id="8a1d8-477">512 characters</span></span>||<span data-ttu-id="8a1d8-478">Anfangswert für den Parameter.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-478">Initial value for the parameter.</span></span>|
|`parameters.inputType`|<span data-ttu-id="8a1d8-479">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="8a1d8-479">string</span></span>|<span data-ttu-id="8a1d8-480">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="8a1d8-480">128 characters</span></span>||<span data-ttu-id="8a1d8-481">Definiert den Typ des Steuerelements, das in einem Aufgabenmodul für angezeigt wird `fetchTask: true` .</span><span class="sxs-lookup"><span data-stu-id="8a1d8-481">Defines the type of control displayed on a task module for`fetchTask: true` .</span></span> <span data-ttu-id="8a1d8-482">Einer von `text, textarea, number, date, time, toggle, choiceset` .</span><span class="sxs-lookup"><span data-stu-id="8a1d8-482">One of `text, textarea, number, date, time, toggle, choiceset` .</span></span>|
|`parameters.choices`|<span data-ttu-id="8a1d8-483">Array von Objekten</span><span class="sxs-lookup"><span data-stu-id="8a1d8-483">array of objects</span></span>|<span data-ttu-id="8a1d8-484">10 Elemente</span><span class="sxs-lookup"><span data-stu-id="8a1d8-484">10 items</span></span>||<span data-ttu-id="8a1d8-485">Die Auswahloptionen für `choiceset` .</span><span class="sxs-lookup"><span data-stu-id="8a1d8-485">The choice options for the`choiceset`.</span></span> <span data-ttu-id="8a1d8-486">Nur verwenden `parameter.inputType` , wenn ist `choiceset` .</span><span class="sxs-lookup"><span data-stu-id="8a1d8-486">Use only when`parameter.inputType` is `choiceset`.</span></span>|
|`parameters.choices.title`|<span data-ttu-id="8a1d8-487">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="8a1d8-487">string</span></span>|<span data-ttu-id="8a1d8-488">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="8a1d8-488">128 characters</span></span>|<span data-ttu-id="8a1d8-489">✔</span><span class="sxs-lookup"><span data-stu-id="8a1d8-489">✔</span></span>|<span data-ttu-id="8a1d8-490">Titel der Auswahl.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-490">Title of the choice.</span></span>|
|`parameters.choices.value`|<span data-ttu-id="8a1d8-491">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="8a1d8-491">string</span></span>|<span data-ttu-id="8a1d8-492">512 Zeichen</span><span class="sxs-lookup"><span data-stu-id="8a1d8-492">512 characters</span></span>|<span data-ttu-id="8a1d8-493">✔</span><span class="sxs-lookup"><span data-stu-id="8a1d8-493">✔</span></span>|<span data-ttu-id="8a1d8-494">Value of the choice.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-494">Value of the choice.</span></span>|

## <a name="permissions"></a><span data-ttu-id="8a1d8-495">Berechtigungen</span><span class="sxs-lookup"><span data-stu-id="8a1d8-495">permissions</span></span>

<span data-ttu-id="8a1d8-496">**Optional** – Array von Zeichenfolgen</span><span class="sxs-lookup"><span data-stu-id="8a1d8-496">**Optional** — array of strings</span></span>

<span data-ttu-id="8a1d8-497">Ein Array, das `string` angibt, welche Berechtigungen die APP anfordert, sodass Endbenutzer wissen, wie die Erweiterung ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-497">An array of `string` which specifies which permissions the app requests, which lets end users know how the extension will perform.</span></span> <span data-ttu-id="8a1d8-498">Die folgenden Optionen sind nicht exklusiv:</span><span class="sxs-lookup"><span data-stu-id="8a1d8-498">The following options are non-exclusive:</span></span>

* <span data-ttu-id="8a1d8-499">`identity`&emsp;Erfordert Benutzeridentitätsinformationen</span><span class="sxs-lookup"><span data-stu-id="8a1d8-499">`identity` &emsp; Requires user identity information</span></span>
* <span data-ttu-id="8a1d8-500">`messageTeamMembers`&emsp;Erfordert die Berechtigung zum Senden von direkten Nachrichten an Teammitglieder.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-500">`messageTeamMembers` &emsp; Requires permission to send direct messages to team members</span></span>

<span data-ttu-id="8a1d8-501">Wenn Sie diese Berechtigungen beim Aktualisieren Ihrer APP ändern, werden die Benutzer beim ersten Ausführen der aktualisierten App den Zustimmungsprozess wiederholen.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-501">Changing these permissions when updating your app will cause your users to repeat the consent process the first time they run the updated app.</span></span> <span data-ttu-id="8a1d8-502">Weitere Informationen finden Sie unter [Aktualisieren Ihrer APP](~/concepts/deploy-and-publish/appsource/post-publish/overview.md) .</span><span class="sxs-lookup"><span data-stu-id="8a1d8-502">See [Updating your app](~/concepts/deploy-and-publish/appsource/post-publish/overview.md) for more information.</span></span>

## <a name="devicepermissions"></a><span data-ttu-id="8a1d8-503">devicePermissions</span><span class="sxs-lookup"><span data-stu-id="8a1d8-503">devicePermissions</span></span>

<span data-ttu-id="8a1d8-504">**Optional** – Array von Zeichenfolgen</span><span class="sxs-lookup"><span data-stu-id="8a1d8-504">**Optional** — array of strings</span></span>

<span data-ttu-id="8a1d8-505">Gibt die systemeigenen Funktionen auf dem Gerät eines Benutzers an, für die Ihre APP möglicherweise Zugriff anfordern kann.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-505">Specifies the native features on a user's device that your app may request access to.</span></span> <span data-ttu-id="8a1d8-506">Mögliche Optionen sind:</span><span class="sxs-lookup"><span data-stu-id="8a1d8-506">Options are:</span></span>

* `geolocation`
* `media`
* `notifications`
* `midi`
* `openExternal`

## <a name="validdomains"></a><span data-ttu-id="8a1d8-507">validDomains</span><span class="sxs-lookup"><span data-stu-id="8a1d8-507">validDomains</span></span>

<span data-ttu-id="8a1d8-508">**Optional**, sofern angegeben, außer **erforderlich**</span><span class="sxs-lookup"><span data-stu-id="8a1d8-508">**Optional**, except **Required** where noted</span></span>

<span data-ttu-id="8a1d8-509">Eine Liste gültiger Domänen für Websites, die von der APP im Microsoft Teams-Client zu laden erwartet werden.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-509">A list of valid domains for websites the app expects to load within the Teams client.</span></span> <span data-ttu-id="8a1d8-510">Domänen Auflistungen können beispielsweise Platzhalterzeichen enthalten `*.example.com` .</span><span class="sxs-lookup"><span data-stu-id="8a1d8-510">Domain listings can include wildcards, for example `*.example.com`.</span></span> <span data-ttu-id="8a1d8-511">Dies entspricht genau einem Segment der Domäne. Wenn Sie eine Übereinstimmung benötigen, `a.b.example.com` verwenden Sie `*.*.example.com` .</span><span class="sxs-lookup"><span data-stu-id="8a1d8-511">This matches exactly one segment of the domain; if you need to match `a.b.example.com` then use `*.*.example.com`.</span></span> <span data-ttu-id="8a1d8-512">Wenn Ihre Registerkartenkonfiguration oder Inhalts-UI neben einer Verwendung für die Registerkartenkonfiguration zu einer anderen Domäne navigieren muss, muss diese Domäne hier angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-512">If your tab configuration or content UI needs to navigate to any other domain besides the one use for tab configuration, that domain must be specified here.</span></span>

<span data-ttu-id="8a1d8-513">Es ist jedoch **nicht** erforderlich, die Domänen von Identitätsanbietern einzubeziehen, die Sie in Ihrer APP unterstützen möchten.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-513">It is **not** necessary to include the domains of identity providers you want to support in your app, however.</span></span> <span data-ttu-id="8a1d8-514">Um beispielsweise mit einer Google-ID zu authentifizieren, müssen Sie zu Accounts.Google.com umgeleitet werden, aber Sie sollten Accounts.Google.com nicht in einschließen `validDomains[]` .</span><span class="sxs-lookup"><span data-stu-id="8a1d8-514">For example, to authenticate using a Google ID, it's necessary to redirect to accounts.google.com, but you should not include accounts.google.com in `validDomains[]`.</span></span>

<span data-ttu-id="8a1d8-515">Microsoft Teams-apps, die ihre eigenen SharePoint-URLs benötigen, um gut zu funktionieren, können "{teamsitedomain}" in Ihre gültige Domänenliste einschließen.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-515">Teams apps that require their own sharepoint URLs to function well, may include "{teamsitedomain}" in their valid domain list.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="8a1d8-516">Fügen Sie keine Domänen hinzu, die sich außerhalb des Steuerelements befinden, entweder direkt oder über Platzhalter.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-516">Do not add domains that are outside your control, either directly or via wildcards.</span></span> <span data-ttu-id="8a1d8-517">Beispielsweise `yourapp.onmicrosoft.com` ist gültig, jedoch ungültig `*.onmicrosoft.com` .</span><span class="sxs-lookup"><span data-stu-id="8a1d8-517">For example, `yourapp.onmicrosoft.com` is valid, but `*.onmicrosoft.com` is not valid.</span></span>

<span data-ttu-id="8a1d8-518">Das Objekt ist ein Array mit allen Elementen des Typs `string` .</span><span class="sxs-lookup"><span data-stu-id="8a1d8-518">The object is an array with all elements of the type `string`.</span></span>

## <a name="webapplicationinfo"></a><span data-ttu-id="8a1d8-519">webApplicationInfo</span><span class="sxs-lookup"><span data-stu-id="8a1d8-519">webApplicationInfo</span></span>

<span data-ttu-id="8a1d8-520">**Optional** – Objekt</span><span class="sxs-lookup"><span data-stu-id="8a1d8-520">**Optional** — object</span></span>

<span data-ttu-id="8a1d8-521">Geben Sie Ihre Aad-APP-ID und Diagramm Informationen an, damit Benutzer sich nahtlos bei ihrer Aad-App anmelden können.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-521">Specify your AAD App ID and Graph information to help users seamlessly sign into your AAD app.</span></span>

|<span data-ttu-id="8a1d8-522">Name</span><span class="sxs-lookup"><span data-stu-id="8a1d8-522">Name</span></span>| <span data-ttu-id="8a1d8-523">Typ</span><span class="sxs-lookup"><span data-stu-id="8a1d8-523">Type</span></span>| <span data-ttu-id="8a1d8-524">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="8a1d8-524">Maximum size</span></span> | <span data-ttu-id="8a1d8-525">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="8a1d8-525">Required</span></span> | <span data-ttu-id="8a1d8-526">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="8a1d8-526">Description</span></span>|
|---|---|---|---|---|
|`id`|<span data-ttu-id="8a1d8-527">string</span><span class="sxs-lookup"><span data-stu-id="8a1d8-527">string</span></span>|<span data-ttu-id="8a1d8-528">36 Zeichen</span><span class="sxs-lookup"><span data-stu-id="8a1d8-528">36 characters</span></span>|<span data-ttu-id="8a1d8-529">✔</span><span class="sxs-lookup"><span data-stu-id="8a1d8-529">✔</span></span>|<span data-ttu-id="8a1d8-530">Aad-Anwendungs-ID der app.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-530">AAD application id of the app.</span></span> <span data-ttu-id="8a1d8-531">Diese ID muss eine GUID sein.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-531">This id must be a GUID.</span></span>|
|`resource`|<span data-ttu-id="8a1d8-532">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="8a1d8-532">string</span></span>|<span data-ttu-id="8a1d8-533">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="8a1d8-533">2048 characters</span></span>||<span data-ttu-id="8a1d8-534">Ressourcen-URL der APP zum Abrufen des Authentifizierungstokens für SSO.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-534">Resource url of app for acquiring auth token for SSO.</span></span>|
|`applicationPermissions`|<span data-ttu-id="8a1d8-535">array of strings</span><span class="sxs-lookup"><span data-stu-id="8a1d8-535">array of strings</span></span>|<span data-ttu-id="8a1d8-536">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="8a1d8-536">128 characters</span></span>||<span data-ttu-id="8a1d8-537">Angeben einer detaillierten [ressourcenspezifischen Zustimmung](../../graph-api/rsc/resource-specific-consent.md#resource-specific-permissions)</span><span class="sxs-lookup"><span data-stu-id="8a1d8-537">Specify granular [resource specific consent](../../graph-api/rsc/resource-specific-consent.md#resource-specific-permissions)</span></span>|

## <a name="showloadingindicator"></a><span data-ttu-id="8a1d8-538">showLoadingIndicator</span><span class="sxs-lookup"><span data-stu-id="8a1d8-538">showLoadingIndicator</span></span>

<span data-ttu-id="8a1d8-539">**Optional** – Boolean</span><span class="sxs-lookup"><span data-stu-id="8a1d8-539">**Optional** — boolean</span></span>

<span data-ttu-id="8a1d8-540">Geben Sie an, ob der Lade Indikator angezeigt werden soll, wenn eine APP/Registerkarte geladen wird.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-540">Indicate whether or not to show the loading indicator when an app/tab is loading.</span></span> <span data-ttu-id="8a1d8-541">Standard: **False**.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-541">Default: **false**.</span></span>
>[!NOTE]
><span data-ttu-id="8a1d8-542">Wenn Sie "showLoadingIndicator: true" in Ihrem App-Manifest festgelegt haben, müssen Sie die Inhaltsseiten ihrer Registerkarten und Aufgaben Module gemäß dem in [Anzeigen eines systemeigenen Lade Indikator](../../tabs/how-to/create-tab-pages/content-page.md#show-a-native-loading-indicator) Dokuments beschriebenen Protokoll ändern.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-542">If you set "showLoadingIndicator : true" in your app manifest, then for the page to load correctly, you must modify the content pages of your tabs and task modules as per the protocol described in [Show a native loading indicator](../../tabs/how-to/create-tab-pages/content-page.md#show-a-native-loading-indicator) document.</span></span>


## <a name="isfullscreen"></a><span data-ttu-id="8a1d8-543">isFullScreen</span><span class="sxs-lookup"><span data-stu-id="8a1d8-543">isFullScreen</span></span>

 <span data-ttu-id="8a1d8-544">**Optional** – Boolean</span><span class="sxs-lookup"><span data-stu-id="8a1d8-544">**Optional** — boolean</span></span>

<span data-ttu-id="8a1d8-545">Geben Sie an, wo eine persönliche App mit oder ohne Registerkarten Kopfleiste gerendert wird.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-545">Indicate where a personal app is rendered with or without a tab-header bar.</span></span> <span data-ttu-id="8a1d8-546">Standard: **False**.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-546">Default: **false**.</span></span>

## <a name="activities"></a><span data-ttu-id="8a1d8-547">Aktivitäten</span><span class="sxs-lookup"><span data-stu-id="8a1d8-547">activities</span></span>

<span data-ttu-id="8a1d8-548">**Optional** – Objekt</span><span class="sxs-lookup"><span data-stu-id="8a1d8-548">**Optional** — object</span></span>

<span data-ttu-id="8a1d8-549">Definieren Sie die Eigenschaften, die Ihre APP für die Bereitstellung in einem Benutzer Aktivitätsfeed verwenden wird.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-549">Define the properties your app will use to post to a user activity feed.</span></span>

|<span data-ttu-id="8a1d8-550">Name</span><span class="sxs-lookup"><span data-stu-id="8a1d8-550">Name</span></span>| <span data-ttu-id="8a1d8-551">Typ</span><span class="sxs-lookup"><span data-stu-id="8a1d8-551">Type</span></span>| <span data-ttu-id="8a1d8-552">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="8a1d8-552">Maximum size</span></span> | <span data-ttu-id="8a1d8-553">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="8a1d8-553">Required</span></span> | <span data-ttu-id="8a1d8-554">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="8a1d8-554">Description</span></span>|
|---|---|---|---|---|
|`activityTypes`|<span data-ttu-id="8a1d8-555">Array von Objekten</span><span class="sxs-lookup"><span data-stu-id="8a1d8-555">array of Objects</span></span>|<span data-ttu-id="8a1d8-556">128 Elemente</span><span class="sxs-lookup"><span data-stu-id="8a1d8-556">128 items</span></span>| | <span data-ttu-id="8a1d8-557">Geben Sie die Arten von Aktivitäten an, die Ihre APP an einen Benutzer-Aktivitätsfeed senden kann.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-557">Specify the types of activities that your app can post to a users activity feed.</span></span>|

### <a name="activitiesactivitytypes"></a><span data-ttu-id="8a1d8-558">Activities. activityTypes</span><span class="sxs-lookup"><span data-stu-id="8a1d8-558">activities.activityTypes</span></span>

|<span data-ttu-id="8a1d8-559">Name</span><span class="sxs-lookup"><span data-stu-id="8a1d8-559">Name</span></span>| <span data-ttu-id="8a1d8-560">Typ</span><span class="sxs-lookup"><span data-stu-id="8a1d8-560">Type</span></span>| <span data-ttu-id="8a1d8-561">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="8a1d8-561">Maximum size</span></span> | <span data-ttu-id="8a1d8-562">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="8a1d8-562">Required</span></span> | <span data-ttu-id="8a1d8-563">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="8a1d8-563">Description</span></span>|
|---|---|---|---|---|
|`type`|<span data-ttu-id="8a1d8-564">string</span><span class="sxs-lookup"><span data-stu-id="8a1d8-564">string</span></span>|<span data-ttu-id="8a1d8-565">32 Zeichen</span><span class="sxs-lookup"><span data-stu-id="8a1d8-565">32 characters</span></span>|<span data-ttu-id="8a1d8-566">✔</span><span class="sxs-lookup"><span data-stu-id="8a1d8-566">✔</span></span>|<span data-ttu-id="8a1d8-567">Der Typ der Benachrichtigung.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-567">The notification type.</span></span> <span data-ttu-id="8a1d8-568">*Siehe weiter unten*.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-568">*See below*.</span></span>|
|`description`|<span data-ttu-id="8a1d8-569">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="8a1d8-569">string</span></span>|<span data-ttu-id="8a1d8-570">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="8a1d8-570">128 characters</span></span>|<span data-ttu-id="8a1d8-571">✔</span><span class="sxs-lookup"><span data-stu-id="8a1d8-571">✔</span></span>|<span data-ttu-id="8a1d8-572">Eine kurze Beschreibung der Benachrichtigung.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-572">A brief description of the notification.</span></span> <span data-ttu-id="8a1d8-573">*Siehe weiter unten*.</span><span class="sxs-lookup"><span data-stu-id="8a1d8-573">*See below*.</span></span>|
|`templateText`|<span data-ttu-id="8a1d8-574">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="8a1d8-574">string</span></span>|<span data-ttu-id="8a1d8-575">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="8a1d8-575">128 characters</span></span>|<span data-ttu-id="8a1d8-576">✔</span><span class="sxs-lookup"><span data-stu-id="8a1d8-576">✔</span></span>|<span data-ttu-id="8a1d8-577">Ex: "{Akteur} hat Aufgabe {Task-Nr} für dich erstellt"</span><span class="sxs-lookup"><span data-stu-id="8a1d8-577">Ex: "{actor} created task {taskId} for you"</span></span>|

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
