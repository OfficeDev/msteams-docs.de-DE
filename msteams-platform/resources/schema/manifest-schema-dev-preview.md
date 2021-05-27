---
title: Developer Preview Manifestschemareferenz
description: Beschreibt das schema, das vom Manifest für die Microsoft Teams
ms.topic: reference
keywords: teams manifest schema Developer Preview
localization_priority: Normal
ms.date: 05/20/2019
ms.openlocfilehash: a5c75046b950484a897fa2720444899c4817989c
ms.sourcegitcommit: 25c02757fe207cdff916ba63aa215f88e24e1d6f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/26/2021
ms.locfileid: "52667418"
---
# <a name="developer-preview-manifest-schema-for-microsoft-teams"></a><span data-ttu-id="74ed9-104">Entwicklervorschaumanifestschema für Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="74ed9-104">Developer preview manifest schema for Microsoft Teams</span></span>

> [!NOTE]
> <span data-ttu-id="74ed9-105">Weitere Informationen zum Programm und zur Teilnahme finden Sie unter [Developer Preview](~/resources/dev-preview/developer-preview-intro.md).</span><span class="sxs-lookup"><span data-stu-id="74ed9-105">For more information on the program and how you can join,see [Developer Preview](~/resources/dev-preview/developer-preview-intro.md).</span></span>
> <span data-ttu-id="74ed9-106">Wenn Sie die Entwicklervorschau nicht verwenden, sollten Sie diese Version des Manifests nicht verwenden.</span><span class="sxs-lookup"><span data-stu-id="74ed9-106">If you are not using the developer preview you should not be using this version of the manifest.</span></span> <span data-ttu-id="74ed9-107">Informationen [zur öffentlichen Version des Manifests finden Microsoft Teams Referenz:](~/resources/schema/manifest-schema.md) Manifestschema.</span><span class="sxs-lookup"><span data-stu-id="74ed9-107">See [Reference: Manifest schema for Microsoft Teams](~/resources/schema/manifest-schema.md) for the public version of the manifest.</span></span>

<span data-ttu-id="74ed9-108">Das Microsoft Teams-Manifest beschreibt, wie die App in das Microsoft Teams integriert wird.</span><span class="sxs-lookup"><span data-stu-id="74ed9-108">The Microsoft Teams manifest describes how the app integrates into the Microsoft Teams product.</span></span> <span data-ttu-id="74ed9-109">Ihr Manifest muss dem schema entsprechen, das unter gehostet [`https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json`](https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json) wird.</span><span class="sxs-lookup"><span data-stu-id="74ed9-109">Your manifest must conform to the schema hosted at [`https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json`](https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json).</span></span>

<span data-ttu-id="74ed9-110">Weitere Informationen zu den verfügbaren Features finden Sie unter Features [in the Public Developer Preview for Microsoft Teams](~/resources/dev-preview/developer-preview-features.md).</span><span class="sxs-lookup"><span data-stu-id="74ed9-110">For more information on the features available see: [Features in the Public Developer Preview for Microsoft Teams](~/resources/dev-preview/developer-preview-features.md).</span></span>

## <a name="sample-full-manifest"></a><span data-ttu-id="74ed9-111">Beispiel für vollständiges Manifest</span><span class="sxs-lookup"><span data-stu-id="74ed9-111">Sample full manifest</span></span>

```json
{
  "$schema": "https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json",
  "manifestVersion": "devPreview",
  "version": "1.0.0",
  "id": "%MICROSOFT-APP-ID%",
  "packageName": "com.example.myapp",
  "devicePermissions" : [ "geolocation", "media" ],
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
      "scopes": [ "team", "groupchat" ]
    }
  ],
  "staticTabs": [
    {
      "entityId": "idForPage",
      "name": "Display name of tab",
      "contentUrl": "https://contoso.com/content?host=msteams",
      "contentBotId": "Specifies to the app that tab is an Adaptive Card Tab. You can either provide the contentBotId or contentUrl.",
      "websiteUrl": "https://contoso.com/content",
      "scopes": [ "personal" ]
    }
  ],
  "bots": [
    {
      "botId": "%MICROSOFT-APP-ID-REGISTERED-WITH-BOT-FRAMEWORK%",
      "needsChannelSelector": false,
      "isNotificationOnly": false,
      "scopes": [ "team", "personal", "groupchat" ],
      "supportsFiles": true,
      "commandLists": [
        {
          "scopes": [ "team", "groupchat" ],
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
          "scopes": [ "personal", "groupchat" ],
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
      "scopes": [ "team"]
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
          "type" : "search",
          "context" : ["compose", "commandBox"],
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
          "type" : "action",
          "fetchTask" : true,
          "context" : ["message"],
          "parameters": [
            {
              "name": "custinfo",
              "title": "Customer name",
              "description": "Enter a customer name",
              "inputType" : "text"
            }
          ]
        },
        {
          "id": "exampleMessageHandler",
          "title": "Message Handler",
          "description": "Domains that will create a preview when pasted into the compose box",
          "messageHandlers": [
            {
              "type" : "link",
              "value" : {
                "domains" : [
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
    "messageTeamMembers",
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
  ],
  "defaultInstallScope": "meetings",
  "defaultGroupCapability": {
    "meetings": "tab", 
    "team": "bot", 
    "groupchat": "bot"
  }
}
```

<span data-ttu-id="74ed9-112">Das Schema definiert die folgenden Eigenschaften:</span><span class="sxs-lookup"><span data-stu-id="74ed9-112">The schema defines the following properties:</span></span>

## <a name="schema"></a><span data-ttu-id="74ed9-113">$schema</span><span class="sxs-lookup"><span data-stu-id="74ed9-113">$schema</span></span>

<span data-ttu-id="74ed9-114">*Optional, aber empfohlen* &ndash; Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="74ed9-114">*Optional, but recommended* &ndash; String</span></span>

<span data-ttu-id="74ed9-115">Die https://-URL, die auf das JSON-Schema für das Manifest verweist.</span><span class="sxs-lookup"><span data-stu-id="74ed9-115">The https:// URL referencing the JSON Schema for the manifest.</span></span>

## <a name="manifestversion"></a><span data-ttu-id="74ed9-116">manifestVersion</span><span class="sxs-lookup"><span data-stu-id="74ed9-116">manifestVersion</span></span>

<span data-ttu-id="74ed9-117">**Erforderlich** &ndash; Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="74ed9-117">**Required** &ndash; String</span></span>

<span data-ttu-id="74ed9-118">Die Version des Manifestschemas, das dieses Manifest verwendet.</span><span class="sxs-lookup"><span data-stu-id="74ed9-118">The version of the manifest schema this manifest is using.</span></span> <span data-ttu-id="74ed9-119">Es sollte "devPreview" sein.</span><span class="sxs-lookup"><span data-stu-id="74ed9-119">It should be "devPreview".</span></span>

## <a name="version"></a><span data-ttu-id="74ed9-120">Version</span><span class="sxs-lookup"><span data-stu-id="74ed9-120">version</span></span>

<span data-ttu-id="74ed9-121">**Erforderlich** &ndash; Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="74ed9-121">**Required** &ndash; String</span></span>

<span data-ttu-id="74ed9-122">Die Version der spezifischen App.</span><span class="sxs-lookup"><span data-stu-id="74ed9-122">The version of the specific app.</span></span> <span data-ttu-id="74ed9-123">Wenn Sie etwas in Ihrem Manifest aktualisieren, muss auch die Version erhöht werden.</span><span class="sxs-lookup"><span data-stu-id="74ed9-123">If you update something in your manifest, the version must be incremented as well.</span></span> <span data-ttu-id="74ed9-124">Auf diese Weise wird bei der Installation des neuen Manifests das vorhandene überschrieben, und der Benutzer erhält die neue Funktionalität.</span><span class="sxs-lookup"><span data-stu-id="74ed9-124">This way, when the new manifest is installed, it will overwrite the existing one and the user will get the new functionality.</span></span> <span data-ttu-id="74ed9-125">Wenn diese App an den Store übermittelt wurde, muss das neue Manifest erneut übermittelt und erneut überprüft werden.</span><span class="sxs-lookup"><span data-stu-id="74ed9-125">If this app was submitted to the store, the new manifest will have to be re-submitted and re-validated.</span></span> <span data-ttu-id="74ed9-126">Anschließend erhalten Benutzer dieser App das neue aktualisierte Manifest automatisch in ein paar Stunden, nachdem es genehmigt wurde.</span><span class="sxs-lookup"><span data-stu-id="74ed9-126">Then, users of this app will get the new updated manifest automatically in a few hours, after it is approved.</span></span>

<span data-ttu-id="74ed9-127">Wenn sich die Von der App angeforderten Berechtigungen ändern, werden Die Benutzer aufgefordert, ein Upgrade zu starten und der App erneut zu zustimmen.</span><span class="sxs-lookup"><span data-stu-id="74ed9-127">If the app requested permissions change, users will be prompted to upgrade and re-consent to the app.</span></span>

<span data-ttu-id="74ed9-128">Diese Versionszeichenfolge muss dem [semver-Standard](http://semver.org/) (MAJOR. MINOR. PATCH).</span><span class="sxs-lookup"><span data-stu-id="74ed9-128">This version string must follow the [semver](http://semver.org/) standard (MAJOR.MINOR.PATCH).</span></span>

## <a name="id"></a><span data-ttu-id="74ed9-129">id</span><span class="sxs-lookup"><span data-stu-id="74ed9-129">id</span></span>

<span data-ttu-id="74ed9-130">**Erforderlich** &ndash; Microsoft-App-ID</span><span class="sxs-lookup"><span data-stu-id="74ed9-130">**Required** &ndash; Microsoft app ID</span></span>

<span data-ttu-id="74ed9-131">Der eindeutige von Microsoft generierte Bezeichner für diese App.</span><span class="sxs-lookup"><span data-stu-id="74ed9-131">The unique Microsoft-generated identifier for this app.</span></span> <span data-ttu-id="74ed9-132">Wenn Sie einen Bot über das Microsoft Bot Framework registriert haben oder sich die Web-App Ihrer Registerkarte bereits bei Microsoft angemeldet hat, sollten Sie bereits über eine ID verfügen und ihn hier eingeben.</span><span class="sxs-lookup"><span data-stu-id="74ed9-132">If you have registered a bot via the Microsoft Bot Framework, or your tab's web app already signs in with Microsoft, you should already have an ID and should enter it here.</span></span> <span data-ttu-id="74ed9-133">Andernfalls sollten Sie eine neue ID im Microsoft Application Registration Portal ([Meine](https://apps.dev.microsoft.com)Anwendungen ) generieren, sie hier eingeben und dann wiederverwenden, wenn Sie [einen Bot hinzufügen.](~/bots/how-to/create-a-bot-for-teams.md)</span><span class="sxs-lookup"><span data-stu-id="74ed9-133">Otherwise, you should generate a new ID at the Microsoft Application Registration Portal ([My Applications](https://apps.dev.microsoft.com)), enter it here, and then reuse it when you [add a bot](~/bots/how-to/create-a-bot-for-teams.md).</span></span>

## <a name="packagename"></a><span data-ttu-id="74ed9-134">packageName</span><span class="sxs-lookup"><span data-stu-id="74ed9-134">packageName</span></span>

<span data-ttu-id="74ed9-135">**Erforderlich** &ndash; Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="74ed9-135">**Required** &ndash; String</span></span>

<span data-ttu-id="74ed9-136">Ein eindeutiger Bezeichner für diese App in umgekehrter Domänen-Notation; z. B. com.example.myapp.</span><span class="sxs-lookup"><span data-stu-id="74ed9-136">A unique identifier for this app in reverse domain notation; for example, com.example.myapp.</span></span>

## <a name="developer"></a><span data-ttu-id="74ed9-137">developer</span><span class="sxs-lookup"><span data-stu-id="74ed9-137">developer</span></span>

<span data-ttu-id="74ed9-138">**Required**</span><span class="sxs-lookup"><span data-stu-id="74ed9-138">**Required**</span></span>

<span data-ttu-id="74ed9-139">Gibt Informationen zu Ihrem Unternehmen an.</span><span class="sxs-lookup"><span data-stu-id="74ed9-139">Specifies information about your company.</span></span> <span data-ttu-id="74ed9-140">Für apps submitted to AppSource (formerly Office Store), these values must match the information in your AppSource entry.</span><span class="sxs-lookup"><span data-stu-id="74ed9-140">For apps submitted to AppSource (formerly Office Store), these values must match the information in your AppSource entry.</span></span>

|<span data-ttu-id="74ed9-141">Name</span><span class="sxs-lookup"><span data-stu-id="74ed9-141">Name</span></span>| <span data-ttu-id="74ed9-142">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="74ed9-142">Maximum size</span></span> | <span data-ttu-id="74ed9-143">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="74ed9-143">Required</span></span> | <span data-ttu-id="74ed9-144">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="74ed9-144">Description</span></span>|
|---|---|---|---|
|`name`|<span data-ttu-id="74ed9-145">32 Zeichen</span><span class="sxs-lookup"><span data-stu-id="74ed9-145">32 characters</span></span>|<span data-ttu-id="74ed9-146">✔</span><span class="sxs-lookup"><span data-stu-id="74ed9-146">✔</span></span>|<span data-ttu-id="74ed9-147">Der Anzeigename für den Entwickler.</span><span class="sxs-lookup"><span data-stu-id="74ed9-147">The display name for the developer.</span></span>|
|`websiteUrl`|<span data-ttu-id="74ed9-148">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="74ed9-148">2048 characters</span></span>|<span data-ttu-id="74ed9-149">✔</span><span class="sxs-lookup"><span data-stu-id="74ed9-149">✔</span></span>|<span data-ttu-id="74ed9-150">Die https://-URL zur Website des Entwicklers.</span><span class="sxs-lookup"><span data-stu-id="74ed9-150">The https:// URL to the developer's website.</span></span> <span data-ttu-id="74ed9-151">Dieser Link sollte Benutzer zu Ihrer unternehmens- oder produktspezifischen Angebotsseite gelangen.</span><span class="sxs-lookup"><span data-stu-id="74ed9-151">This link should take users to your company or product-specific landing page.</span></span>|
|`privacyUrl`|<span data-ttu-id="74ed9-152">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="74ed9-152">2048 characters</span></span>|<span data-ttu-id="74ed9-153">✔</span><span class="sxs-lookup"><span data-stu-id="74ed9-153">✔</span></span>|<span data-ttu-id="74ed9-154">Die https:// url to the developer's privacy policy.</span><span class="sxs-lookup"><span data-stu-id="74ed9-154">The https:// URL to the developer's privacy policy.</span></span>|
|`termsOfUseUrl`|<span data-ttu-id="74ed9-155">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="74ed9-155">2048 characters</span></span>|<span data-ttu-id="74ed9-156">✔</span><span class="sxs-lookup"><span data-stu-id="74ed9-156">✔</span></span>|<span data-ttu-id="74ed9-157">Die https:// URL zu den Nutzungsbedingungen des Entwicklers.</span><span class="sxs-lookup"><span data-stu-id="74ed9-157">The https:// URL to the developer's terms of use.</span></span>|
|`mpnId`|<span data-ttu-id="74ed9-158">10 Zeichen</span><span class="sxs-lookup"><span data-stu-id="74ed9-158">10 characters</span></span>|<span data-ttu-id="74ed9-159">✔</span><span class="sxs-lookup"><span data-stu-id="74ed9-159">✔</span></span>|<span data-ttu-id="74ed9-160">**Optional** Die Microsoft Partner Network ID, die die Partnerorganisation identifiziert, die die App erstellt.</span><span class="sxs-lookup"><span data-stu-id="74ed9-160">**Optional** The Microsoft Partner Network ID that identifies the partner organization building the app.</span></span>|

## <a name="localizationinfo"></a><span data-ttu-id="74ed9-161">localizationInfo</span><span class="sxs-lookup"><span data-stu-id="74ed9-161">localizationInfo</span></span>

<span data-ttu-id="74ed9-162">**Optional**</span><span class="sxs-lookup"><span data-stu-id="74ed9-162">**Optional**</span></span>

<span data-ttu-id="74ed9-163">Ermöglicht die Angabe einer Standardsprache sowie Zeiger auf zusätzliche Sprachdateien.</span><span class="sxs-lookup"><span data-stu-id="74ed9-163">Allows the specification of a default language, as well as pointers to additional language files.</span></span> <span data-ttu-id="74ed9-164">Weitere [Informationen finden Sie unter Lokalisierung](~/concepts/build-and-test/apps-localization.md).</span><span class="sxs-lookup"><span data-stu-id="74ed9-164">See [localization](~/concepts/build-and-test/apps-localization.md).</span></span>

|<span data-ttu-id="74ed9-165">Name</span><span class="sxs-lookup"><span data-stu-id="74ed9-165">Name</span></span>| <span data-ttu-id="74ed9-166">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="74ed9-166">Maximum size</span></span> | <span data-ttu-id="74ed9-167">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="74ed9-167">Required</span></span> | <span data-ttu-id="74ed9-168">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="74ed9-168">Description</span></span>|
|---|---|---|---|
|`defaultLanguageTag`|<span data-ttu-id="74ed9-169">4 Zeichen</span><span class="sxs-lookup"><span data-stu-id="74ed9-169">4 characters</span></span>|<span data-ttu-id="74ed9-170">✔</span><span class="sxs-lookup"><span data-stu-id="74ed9-170">✔</span></span>|<span data-ttu-id="74ed9-171">Das Sprachtag der Zeichenfolgen in dieser Manifestdatei auf oberster Ebene.</span><span class="sxs-lookup"><span data-stu-id="74ed9-171">The language tag of the strings in this top level manifest file.</span></span>|

### <a name="localizationinfoadditionallanguages"></a><span data-ttu-id="74ed9-172">localizationInfo.additionalLanguages</span><span class="sxs-lookup"><span data-stu-id="74ed9-172">localizationInfo.additionalLanguages</span></span>

<span data-ttu-id="74ed9-173">Ein Array von Objekten, die zusätzliche Sprachübersetzungen angeben.</span><span class="sxs-lookup"><span data-stu-id="74ed9-173">An array of objects specifying additional language translations.</span></span>

|<span data-ttu-id="74ed9-174">Name</span><span class="sxs-lookup"><span data-stu-id="74ed9-174">Name</span></span>| <span data-ttu-id="74ed9-175">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="74ed9-175">Maximum size</span></span> | <span data-ttu-id="74ed9-176">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="74ed9-176">Required</span></span> | <span data-ttu-id="74ed9-177">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="74ed9-177">Description</span></span>|
|---|---|---|---|
|`languageTag`|<span data-ttu-id="74ed9-178">4 Zeichen</span><span class="sxs-lookup"><span data-stu-id="74ed9-178">4 characters</span></span>|<span data-ttu-id="74ed9-179">✔</span><span class="sxs-lookup"><span data-stu-id="74ed9-179">✔</span></span>|<span data-ttu-id="74ed9-180">Das Sprachtag der Zeichenfolgen in der bereitgestellten Datei.</span><span class="sxs-lookup"><span data-stu-id="74ed9-180">The language tag of the strings in the provided file.</span></span>|
|`file`|<span data-ttu-id="74ed9-181">4 Zeichen</span><span class="sxs-lookup"><span data-stu-id="74ed9-181">4 characters</span></span>|<span data-ttu-id="74ed9-182">✔</span><span class="sxs-lookup"><span data-stu-id="74ed9-182">✔</span></span>|<span data-ttu-id="74ed9-183">Ein relativer Dateipfad zu einer .json-Datei, die die übersetzten Zeichenfolgen enthält.</span><span class="sxs-lookup"><span data-stu-id="74ed9-183">A relative file path to a the .json file containing the translated strings.</span></span>|

## <a name="name"></a><span data-ttu-id="74ed9-184">name</span><span class="sxs-lookup"><span data-stu-id="74ed9-184">name</span></span>

<span data-ttu-id="74ed9-185">**Required**</span><span class="sxs-lookup"><span data-stu-id="74ed9-185">**Required**</span></span>

<span data-ttu-id="74ed9-186">Der Name Ihrer App-Erfahrung, der Benutzern in der Teams angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="74ed9-186">The name of your app experience, displayed to users in the Teams experience.</span></span> <span data-ttu-id="74ed9-187">Für apps submitted to AppSource, these values must match the information in your AppSource entry.</span><span class="sxs-lookup"><span data-stu-id="74ed9-187">For apps submitted to AppSource, these values must match the information in your AppSource entry.</span></span> <span data-ttu-id="74ed9-188">Die Werte von `short` und sollten nicht identisch `full` sein.</span><span class="sxs-lookup"><span data-stu-id="74ed9-188">The values of `short` and `full` should not be the same.</span></span>

|<span data-ttu-id="74ed9-189">Name</span><span class="sxs-lookup"><span data-stu-id="74ed9-189">Name</span></span>| <span data-ttu-id="74ed9-190">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="74ed9-190">Maximum size</span></span> | <span data-ttu-id="74ed9-191">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="74ed9-191">Required</span></span> | <span data-ttu-id="74ed9-192">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="74ed9-192">Description</span></span>|
|---|---|---|---|
|`short`|<span data-ttu-id="74ed9-193">30 Zeichen</span><span class="sxs-lookup"><span data-stu-id="74ed9-193">30 characters</span></span>|<span data-ttu-id="74ed9-194">✔</span><span class="sxs-lookup"><span data-stu-id="74ed9-194">✔</span></span>|<span data-ttu-id="74ed9-195">Der kurze Anzeigename für die App.</span><span class="sxs-lookup"><span data-stu-id="74ed9-195">The short display name for the app.</span></span>|
|`full`|<span data-ttu-id="74ed9-196">100 Zeichen</span><span class="sxs-lookup"><span data-stu-id="74ed9-196">100 characters</span></span>||<span data-ttu-id="74ed9-197">Der vollständige Name der App, der verwendet wird, wenn der vollständige Name der App 30 Zeichen überschreitet.</span><span class="sxs-lookup"><span data-stu-id="74ed9-197">The full name of the app, used if the full app name exceeds 30 characters.</span></span>|

## <a name="description"></a><span data-ttu-id="74ed9-198">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="74ed9-198">description</span></span>

<span data-ttu-id="74ed9-199">**Required**</span><span class="sxs-lookup"><span data-stu-id="74ed9-199">**Required**</span></span>

<span data-ttu-id="74ed9-200">Beschreibt Ihre App für Benutzer.</span><span class="sxs-lookup"><span data-stu-id="74ed9-200">Describes your app to users.</span></span> <span data-ttu-id="74ed9-201">Für apps submitted to AppSource, these values must match the information in your AppSource entry.</span><span class="sxs-lookup"><span data-stu-id="74ed9-201">For apps submitted to AppSource, these values must match the information in your AppSource entry.</span></span>

<span data-ttu-id="74ed9-202">Stellen Sie sicher, dass Ihre Beschreibung Ihre Erfahrung genau beschreibt und Informationen enthält, mit deren Hilfe potenzielle Kunden besser verstehen können, was Ihre Erfahrung bedeutet.</span><span class="sxs-lookup"><span data-stu-id="74ed9-202">Ensure that your description accurately describes your experience and provides information to help potential customers understand what your experience does.</span></span> <span data-ttu-id="74ed9-203">Beachten Sie auch in der vollständigen Beschreibung, ob ein externes Konto für die Verwendung erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="74ed9-203">You should also note, in the full description, if an external account is required for use.</span></span> <span data-ttu-id="74ed9-204">Die Werte von `short` und sollten nicht identisch `full` sein.</span><span class="sxs-lookup"><span data-stu-id="74ed9-204">The values of `short` and `full` should not be the same.</span></span>  <span data-ttu-id="74ed9-205">Ihre kurze Beschreibung darf nicht innerhalb der langen Beschreibung wiederholt werden und darf keinen anderen App-Namen enthalten.</span><span class="sxs-lookup"><span data-stu-id="74ed9-205">Your short description must not be repeated within the long description and must not include any other app name.</span></span>

|<span data-ttu-id="74ed9-206">Name</span><span class="sxs-lookup"><span data-stu-id="74ed9-206">Name</span></span>| <span data-ttu-id="74ed9-207">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="74ed9-207">Maximum size</span></span> | <span data-ttu-id="74ed9-208">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="74ed9-208">Required</span></span> | <span data-ttu-id="74ed9-209">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="74ed9-209">Description</span></span>|
|---|---|---|---|
|`short`|<span data-ttu-id="74ed9-210">80 Zeichen</span><span class="sxs-lookup"><span data-stu-id="74ed9-210">80 characters</span></span>|<span data-ttu-id="74ed9-211">✔</span><span class="sxs-lookup"><span data-stu-id="74ed9-211">✔</span></span>|<span data-ttu-id="74ed9-212">Eine kurze Beschreibung Ihrer App-Erfahrung, die bei begrenztem Speicherplatz verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="74ed9-212">A short description of your app experience, used when space is limited.</span></span>|
|`full`|<span data-ttu-id="74ed9-213">4000 Zeichen</span><span class="sxs-lookup"><span data-stu-id="74ed9-213">4000 characters</span></span>|<span data-ttu-id="74ed9-214">✔</span><span class="sxs-lookup"><span data-stu-id="74ed9-214">✔</span></span>|<span data-ttu-id="74ed9-215">Die vollständige Beschreibung Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="74ed9-215">The full description of your app.</span></span>|

## <a name="icons"></a><span data-ttu-id="74ed9-216">Symbole</span><span class="sxs-lookup"><span data-stu-id="74ed9-216">icons</span></span>

<span data-ttu-id="74ed9-217">**Required**</span><span class="sxs-lookup"><span data-stu-id="74ed9-217">**Required**</span></span>

<span data-ttu-id="74ed9-218">Symbole, die innerhalb der Teams werden.</span><span class="sxs-lookup"><span data-stu-id="74ed9-218">Icons used within the Teams app.</span></span> <span data-ttu-id="74ed9-219">Die Symboldateien müssen als Teil des Uploadpakets enthalten sein.</span><span class="sxs-lookup"><span data-stu-id="74ed9-219">The icon files must be included as part of the upload package.</span></span>

|<span data-ttu-id="74ed9-220">Name</span><span class="sxs-lookup"><span data-stu-id="74ed9-220">Name</span></span>| <span data-ttu-id="74ed9-221">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="74ed9-221">Maximum size</span></span> | <span data-ttu-id="74ed9-222">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="74ed9-222">Required</span></span> | <span data-ttu-id="74ed9-223">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="74ed9-223">Description</span></span>|
|---|---|---|---|
|`outline`|<span data-ttu-id="74ed9-224">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="74ed9-224">2048 characters</span></span>|<span data-ttu-id="74ed9-225">✔</span><span class="sxs-lookup"><span data-stu-id="74ed9-225">✔</span></span>|<span data-ttu-id="74ed9-226">Ein relativer Dateipfad zu einem transparenten 32 x 32 PNG-Gliederungssymbol.</span><span class="sxs-lookup"><span data-stu-id="74ed9-226">A relative file path to a transparent 32x32 PNG outline icon.</span></span>|
|`color`|<span data-ttu-id="74ed9-227">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="74ed9-227">2048 characters</span></span>|<span data-ttu-id="74ed9-228">✔</span><span class="sxs-lookup"><span data-stu-id="74ed9-228">✔</span></span>|<span data-ttu-id="74ed9-229">Ein relativer Dateipfad zu einem vollfarbigen 192 x 192-PNG-Symbol.</span><span class="sxs-lookup"><span data-stu-id="74ed9-229">A relative file path to a full color 192x192 PNG icon.</span></span>|

## <a name="accentcolor"></a><span data-ttu-id="74ed9-230">accentColor</span><span class="sxs-lookup"><span data-stu-id="74ed9-230">accentColor</span></span>

<span data-ttu-id="74ed9-231">**Erforderlich** &ndash; Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="74ed9-231">**Required** &ndash; String</span></span>

<span data-ttu-id="74ed9-232">Eine Farbe, die in Verbindung mit und als Hintergrund für Ihre Gliederungssymbole verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="74ed9-232">A color to use in conjunction with and as a background for your outline icons.</span></span>

<span data-ttu-id="74ed9-233">Der Wert muss ein gültiger #A0 sein, der mit "#" beginnt, z. B. `#4464ee` .</span><span class="sxs-lookup"><span data-stu-id="74ed9-233">The value must be a valid HTML color code starting with '#', for example `#4464ee`.</span></span>

## <a name="configurabletabs"></a><span data-ttu-id="74ed9-234">configurableTabs</span><span class="sxs-lookup"><span data-stu-id="74ed9-234">configurableTabs</span></span>

<span data-ttu-id="74ed9-235">**Optional**</span><span class="sxs-lookup"><span data-stu-id="74ed9-235">**Optional**</span></span>

<span data-ttu-id="74ed9-236">Wird verwendet, wenn Ihre App über eine Registerkartenerfahrung im Teamkanal verfügt, die eine zusätzliche Konfiguration erfordert, bevor sie hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="74ed9-236">Used when your app experience has a team channel tab experience that requires extra configuration before it is added.</span></span> <span data-ttu-id="74ed9-237">Konfigurierbare Registerkarten werden nur im Bereich Teams unterstützt, und derzeit wird nur eine Registerkarte pro App unterstützt.</span><span class="sxs-lookup"><span data-stu-id="74ed9-237">Configurable tabs are supported only in the teams scope, and currently only one tab per app is supported.</span></span>

<span data-ttu-id="74ed9-238">Das Objekt ist ein Array mit allen Elementen des Typs `object` .</span><span class="sxs-lookup"><span data-stu-id="74ed9-238">The object is an array with all elements of the type `object`.</span></span> <span data-ttu-id="74ed9-239">Dieser Block ist nur für Lösungen erforderlich, die eine konfigurierbare Kanalregisterkartenlösung bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="74ed9-239">This block is required only for solutions that provide a configurable channel tab solution.</span></span>

|<span data-ttu-id="74ed9-240">Name</span><span class="sxs-lookup"><span data-stu-id="74ed9-240">Name</span></span>| <span data-ttu-id="74ed9-241">Typ</span><span class="sxs-lookup"><span data-stu-id="74ed9-241">Type</span></span>| <span data-ttu-id="74ed9-242">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="74ed9-242">Maximum size</span></span> | <span data-ttu-id="74ed9-243">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="74ed9-243">Required</span></span> | <span data-ttu-id="74ed9-244">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="74ed9-244">Description</span></span>|
|---|---|---|---|---|
|`configurationUrl`|<span data-ttu-id="74ed9-245">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="74ed9-245">String</span></span>|<span data-ttu-id="74ed9-246">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="74ed9-246">2048 characters</span></span>|<span data-ttu-id="74ed9-247">✔</span><span class="sxs-lookup"><span data-stu-id="74ed9-247">✔</span></span>|<span data-ttu-id="74ed9-248">Die https:// URL, die beim Konfigurieren der Registerkarte verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="74ed9-248">The https:// URL to use when configuring the tab.</span></span>|
|`canUpdateConfiguration`|<span data-ttu-id="74ed9-249">Boolesch</span><span class="sxs-lookup"><span data-stu-id="74ed9-249">Boolean</span></span>|||<span data-ttu-id="74ed9-250">Ein Wert, der angibt, ob eine Instanz der Registerkartenkonfiguration vom Benutzer nach der Erstellung aktualisiert werden kann.</span><span class="sxs-lookup"><span data-stu-id="74ed9-250">A value indicating whether an instance of the tab's configuration can be updated by the user after creation.</span></span> <span data-ttu-id="74ed9-251">Standard: `true`</span><span class="sxs-lookup"><span data-stu-id="74ed9-251">Default: `true`</span></span>|
|`scopes`|<span data-ttu-id="74ed9-252">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="74ed9-252">Array of enum</span></span>|<span data-ttu-id="74ed9-253">1</span><span class="sxs-lookup"><span data-stu-id="74ed9-253">1</span></span>|<span data-ttu-id="74ed9-254">✔</span><span class="sxs-lookup"><span data-stu-id="74ed9-254">✔</span></span>|<span data-ttu-id="74ed9-255">Derzeit unterstützen konfigurierbare Registerkarten nur die `team` Bereiche `groupchat` und.</span><span class="sxs-lookup"><span data-stu-id="74ed9-255">Currently, configurable tabs support only the `team` and `groupchat` scopes.</span></span> |
|`sharePointPreviewImage`|<span data-ttu-id="74ed9-256">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="74ed9-256">String</span></span>|<span data-ttu-id="74ed9-257">2048</span><span class="sxs-lookup"><span data-stu-id="74ed9-257">2048</span></span>||<span data-ttu-id="74ed9-258">Ein relativer Dateipfad zu einem Registerkartenvorschaubild zur Verwendung in SharePoint.</span><span class="sxs-lookup"><span data-stu-id="74ed9-258">A relative file path to a tab preview image for use in SharePoint.</span></span> <span data-ttu-id="74ed9-259">Größe 1024 x 768.</span><span class="sxs-lookup"><span data-stu-id="74ed9-259">Size 1024x768.</span></span> |
|`supportedSharePointHosts`|<span data-ttu-id="74ed9-260">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="74ed9-260">Array of enum</span></span>|<span data-ttu-id="74ed9-261">1</span><span class="sxs-lookup"><span data-stu-id="74ed9-261">1</span></span>||<span data-ttu-id="74ed9-262">Definiert, wie Ihre Registerkarte in der SharePoint.</span><span class="sxs-lookup"><span data-stu-id="74ed9-262">Defines how your tab will be made available in SharePoint.</span></span> <span data-ttu-id="74ed9-263">Optionen sind `sharePointFullPage` und `sharePointWebPart`</span><span class="sxs-lookup"><span data-stu-id="74ed9-263">Options are `sharePointFullPage` and `sharePointWebPart`</span></span> |

## <a name="statictabs"></a><span data-ttu-id="74ed9-264">staticTabs</span><span class="sxs-lookup"><span data-stu-id="74ed9-264">staticTabs</span></span>

<span data-ttu-id="74ed9-265">**Optional**</span><span class="sxs-lookup"><span data-stu-id="74ed9-265">**Optional**</span></span>

<span data-ttu-id="74ed9-266">Definiert eine Reihe von Registerkarten, die standardmäßig angeheftet werden können, ohne dass der Benutzer sie manuell hinzufügungen muss.</span><span class="sxs-lookup"><span data-stu-id="74ed9-266">Defines a set of tabs that can be "pinned" by default, without the user adding them manually.</span></span> <span data-ttu-id="74ed9-267">Statische Registerkarten, die im Bereich deklariert sind, werden immer an die persönliche Be benutzererfahrung `personal` der App angeheftet.</span><span class="sxs-lookup"><span data-stu-id="74ed9-267">Static tabs declared in `personal` scope are always pinned to the app's personal experience.</span></span> <span data-ttu-id="74ed9-268">Statische Registerkarten, die im Bereich `team` deklariert sind, werden derzeit nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="74ed9-268">Static tabs declared in the `team` scope are currently not supported.</span></span>

<span data-ttu-id="74ed9-269">Rendern von Registerkarten mit adaptiven Karten, indem Sie anstelle des `contentBotId` `contentUrl` **StaticTabs-Blocks angeben.**</span><span class="sxs-lookup"><span data-stu-id="74ed9-269">Render tabs with Adaptive Cards by specifying `contentBotId` instead of `contentUrl` in the **staticTabs** block.</span></span>

<span data-ttu-id="74ed9-270">Das Objekt ist ein Array (maximal 16 Elemente) mit allen Elementen des Typs `object` .</span><span class="sxs-lookup"><span data-stu-id="74ed9-270">The object is an array (maximum of 16 elements) with all elements of the type `object`.</span></span> <span data-ttu-id="74ed9-271">Dieser Block ist nur für Lösungen erforderlich, die eine statische Registerkartenlösung bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="74ed9-271">This block is required only for solutions that provide a static tab solution.</span></span>


|<span data-ttu-id="74ed9-272">Name</span><span class="sxs-lookup"><span data-stu-id="74ed9-272">Name</span></span>| <span data-ttu-id="74ed9-273">Typ</span><span class="sxs-lookup"><span data-stu-id="74ed9-273">Type</span></span>| <span data-ttu-id="74ed9-274">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="74ed9-274">Maximum size</span></span> | <span data-ttu-id="74ed9-275">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="74ed9-275">Required</span></span> | <span data-ttu-id="74ed9-276">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="74ed9-276">Description</span></span>|
|---|---|---|---|---|
|`entityId`|<span data-ttu-id="74ed9-277">String</span><span class="sxs-lookup"><span data-stu-id="74ed9-277">String</span></span>|<span data-ttu-id="74ed9-278">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="74ed9-278">64 characters</span></span>|<span data-ttu-id="74ed9-279">✔</span><span class="sxs-lookup"><span data-stu-id="74ed9-279">✔</span></span>|<span data-ttu-id="74ed9-280">Ein eindeutiger Bezeichner für die Entität, die auf der Registerkarte angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="74ed9-280">A unique identifier for the entity that the tab displays.</span></span>|
|`name`|<span data-ttu-id="74ed9-281">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="74ed9-281">String</span></span>|<span data-ttu-id="74ed9-282">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="74ed9-282">128 characters</span></span>|<span data-ttu-id="74ed9-283">✔</span><span class="sxs-lookup"><span data-stu-id="74ed9-283">✔</span></span>|<span data-ttu-id="74ed9-284">Der Anzeigename der Registerkarte in der Kanalschnittstelle.</span><span class="sxs-lookup"><span data-stu-id="74ed9-284">The display name of the tab in the channel interface.</span></span>|
|`contentUrl`|<span data-ttu-id="74ed9-285">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="74ed9-285">String</span></span>|<span data-ttu-id="74ed9-286">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="74ed9-286">2048 characters</span></span>|<span data-ttu-id="74ed9-287">✔</span><span class="sxs-lookup"><span data-stu-id="74ed9-287">✔</span></span>|<span data-ttu-id="74ed9-288">Die https://-URL, die auf die Entitätsbenutzeroberfläche verweist, die im Zeichenbereich Teams werden soll.</span><span class="sxs-lookup"><span data-stu-id="74ed9-288">The https:// URL that points to the entity UI to be displayed in the Teams canvas.</span></span>|
|`contentBotId`|   | | | <span data-ttu-id="74ed9-289">Die Microsoft Teams App-ID, die für den Bot im Bot Framework-Portal angegeben ist.</span><span class="sxs-lookup"><span data-stu-id="74ed9-289">The Microsoft Teams app ID specified for the bot in the Bot Framework portal.</span></span> |
|`websiteUrl`|<span data-ttu-id="74ed9-290">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="74ed9-290">String</span></span>|<span data-ttu-id="74ed9-291">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="74ed9-291">2048 characters</span></span>||<span data-ttu-id="74ed9-292">Die https:// URL, auf die verweisen soll, wenn sich ein Benutzer für die Anzeige in einem Browser entscheidet.</span><span class="sxs-lookup"><span data-stu-id="74ed9-292">The https:// URL to point at if a user opts to view in a browser.</span></span>|
|`scopes`|<span data-ttu-id="74ed9-293">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="74ed9-293">Array of enum</span></span>|<span data-ttu-id="74ed9-294">1</span><span class="sxs-lookup"><span data-stu-id="74ed9-294">1</span></span>|<span data-ttu-id="74ed9-295">✔</span><span class="sxs-lookup"><span data-stu-id="74ed9-295">✔</span></span>|<span data-ttu-id="74ed9-296">Derzeit unterstützen statische Registerkarten nur den Bereich, d. h., er kann nur als Teil der `personal` persönlichen Erfahrung bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="74ed9-296">Currently, static tabs support only the `personal` scope, which means it can be provisioned only as part of the personal experience.</span></span>|

## <a name="bots"></a><span data-ttu-id="74ed9-297">Bots</span><span class="sxs-lookup"><span data-stu-id="74ed9-297">bots</span></span>

<span data-ttu-id="74ed9-298">**Optional**</span><span class="sxs-lookup"><span data-stu-id="74ed9-298">**Optional**</span></span>

<span data-ttu-id="74ed9-299">Definiert eine Botlösung zusammen mit optionalen Informationen, z. B. Standardbefehlseigenschaften.</span><span class="sxs-lookup"><span data-stu-id="74ed9-299">Defines a bot solution, along with optional information such as default command properties.</span></span>

<span data-ttu-id="74ed9-300">Das Objekt ist ein Array (maximal 1 Element ist derzeit nur ein Bot pro App zulässig) mit allen Elementen &mdash; des Typs `object` .</span><span class="sxs-lookup"><span data-stu-id="74ed9-300">The object is an array (maximum of only 1 element&mdash;currently only one bot is allowed per app) with all elements of the type `object`.</span></span> <span data-ttu-id="74ed9-301">Dieser Block ist nur für Lösungen erforderlich, die eine Boterfahrung bieten.</span><span class="sxs-lookup"><span data-stu-id="74ed9-301">This block is required only for solutions that provide a bot experience.</span></span>

|<span data-ttu-id="74ed9-302">Name</span><span class="sxs-lookup"><span data-stu-id="74ed9-302">Name</span></span>| <span data-ttu-id="74ed9-303">Typ</span><span class="sxs-lookup"><span data-stu-id="74ed9-303">Type</span></span>| <span data-ttu-id="74ed9-304">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="74ed9-304">Maximum size</span></span> | <span data-ttu-id="74ed9-305">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="74ed9-305">Required</span></span> | <span data-ttu-id="74ed9-306">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="74ed9-306">Description</span></span>|
|---|---|---|---|---|
|`botId`|<span data-ttu-id="74ed9-307">String</span><span class="sxs-lookup"><span data-stu-id="74ed9-307">String</span></span>|<span data-ttu-id="74ed9-308">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="74ed9-308">64 characters</span></span>|<span data-ttu-id="74ed9-309">✔</span><span class="sxs-lookup"><span data-stu-id="74ed9-309">✔</span></span>|<span data-ttu-id="74ed9-310">Die eindeutige Microsoft-App-ID für den Bot, wie bei Bot Framework registriert.</span><span class="sxs-lookup"><span data-stu-id="74ed9-310">The unique Microsoft app ID for the bot as registered with the Bot Framework.</span></span> <span data-ttu-id="74ed9-311">Dies kann mit der allgemeinen [App-ID identisch sein.](#id)</span><span class="sxs-lookup"><span data-stu-id="74ed9-311">This may well be the same as the overall [app ID](#id).</span></span>|
|`needsChannelSelector`|<span data-ttu-id="74ed9-312">Boolesch</span><span class="sxs-lookup"><span data-stu-id="74ed9-312">Boolean</span></span>|||<span data-ttu-id="74ed9-313">Beschreibt, ob der Bot einen Benutzerhinweis verwendet, um den Bot einem bestimmten Kanal hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="74ed9-313">Describes whether or not the bot utilizes a user hint to add the bot to a specific channel.</span></span> <span data-ttu-id="74ed9-314">Standard: `false`</span><span class="sxs-lookup"><span data-stu-id="74ed9-314">Default: `false`</span></span>|
|`isNotificationOnly`|<span data-ttu-id="74ed9-315">Boolesch</span><span class="sxs-lookup"><span data-stu-id="74ed9-315">Boolean</span></span>|||<span data-ttu-id="74ed9-316">Gibt an, ob ein Bot ein unidirektionaler Bot ausschließlich für Benachrichtigungen ist (im Gegensatz zu einem dialogorientierten Bot).</span><span class="sxs-lookup"><span data-stu-id="74ed9-316">Indicates whether a bot is a one-way, notification-only bot, as opposed to a conversational bot.</span></span> <span data-ttu-id="74ed9-317">Standard: `false`</span><span class="sxs-lookup"><span data-stu-id="74ed9-317">Default: `false`</span></span>|
|`supportsFiles`|<span data-ttu-id="74ed9-318">Boolesch</span><span class="sxs-lookup"><span data-stu-id="74ed9-318">Boolean</span></span>|||<span data-ttu-id="74ed9-319">Gibt an, ob der Bot die Möglichkeit zum Hochladen/Herunterladen von Dateien in persönliche Chats unterstützt.</span><span class="sxs-lookup"><span data-stu-id="74ed9-319">Indicates whether the bot supports the ability to upload/download files in personal chat.</span></span> <span data-ttu-id="74ed9-320">Standard: `false`</span><span class="sxs-lookup"><span data-stu-id="74ed9-320">Default: `false`</span></span>|
|`scopes`|<span data-ttu-id="74ed9-321">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="74ed9-321">Array of enum</span></span>|<span data-ttu-id="74ed9-322">3</span><span class="sxs-lookup"><span data-stu-id="74ed9-322">3</span></span>|<span data-ttu-id="74ed9-323">✔</span><span class="sxs-lookup"><span data-stu-id="74ed9-323">✔</span></span>|<span data-ttu-id="74ed9-324">Gibt an, ob der Bot eine Umgebung im Kontext eines Kanals in einem `team` oder Gruppenchat (`groupchat`) ist, oder aber eine Umgebung einzig für einen bestimmten Benutzer (`personal`).</span><span class="sxs-lookup"><span data-stu-id="74ed9-324">Specifies whether the bot offers an experience in the context of a channel in a `team`, in a group chat (`groupchat`), or an experience scoped to an individual user alone (`personal`).</span></span> <span data-ttu-id="74ed9-325">Diese Optionen sind nicht exklusiv.</span><span class="sxs-lookup"><span data-stu-id="74ed9-325">These options are non-exclusive.</span></span>|

### <a name="botscommandlists"></a><span data-ttu-id="74ed9-326">bots.commandLists</span><span class="sxs-lookup"><span data-stu-id="74ed9-326">bots.commandLists</span></span>

<span data-ttu-id="74ed9-327">Eine optionale Liste von Befehlen, die Ihr Bot Benutzern empfehlen kann.</span><span class="sxs-lookup"><span data-stu-id="74ed9-327">An optional list of commands that your bot can recommend to users.</span></span> <span data-ttu-id="74ed9-328">Das Objekt ist ein Array (maximal 2 Elemente) mit allen Elementen des Typs. Sie müssen eine separate Befehlsliste für jeden Bereich definieren, den `object` Ihr Bot unterstützt.</span><span class="sxs-lookup"><span data-stu-id="74ed9-328">The object is an array (maximum of 2 elements) with all elements of type `object`; you must define a separate command list for each scope that your bot supports.</span></span> <span data-ttu-id="74ed9-329">Weitere Informationen finden Sie unter [Bot-Menüs](~/bots/how-to/create-a-bot-commands-menu.md).</span><span class="sxs-lookup"><span data-stu-id="74ed9-329">For more information, see [Bot menus](~/bots/how-to/create-a-bot-commands-menu.md).</span></span>

|<span data-ttu-id="74ed9-330">Name</span><span class="sxs-lookup"><span data-stu-id="74ed9-330">Name</span></span>| <span data-ttu-id="74ed9-331">Typ</span><span class="sxs-lookup"><span data-stu-id="74ed9-331">Type</span></span>| <span data-ttu-id="74ed9-332">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="74ed9-332">Maximum size</span></span> | <span data-ttu-id="74ed9-333">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="74ed9-333">Required</span></span> | <span data-ttu-id="74ed9-334">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="74ed9-334">Description</span></span>|
|---|---|---|---|---|
|`items.scopes`|<span data-ttu-id="74ed9-335">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="74ed9-335">array of enum</span></span>|<span data-ttu-id="74ed9-336">3</span><span class="sxs-lookup"><span data-stu-id="74ed9-336">3</span></span>|<span data-ttu-id="74ed9-337">✔</span><span class="sxs-lookup"><span data-stu-id="74ed9-337">✔</span></span>|<span data-ttu-id="74ed9-338">Gibt den Bereich an, für den die Befehlsliste gültig ist.</span><span class="sxs-lookup"><span data-stu-id="74ed9-338">Specifies the scope for which the command list is valid.</span></span> <span data-ttu-id="74ed9-339">Mögliche Optionen sind `team`, `personal` und `groupchat`.</span><span class="sxs-lookup"><span data-stu-id="74ed9-339">Options are `team`, `personal`, and `groupchat`.</span></span>|
|`items.commands`|<span data-ttu-id="74ed9-340">Array von Objekten</span><span class="sxs-lookup"><span data-stu-id="74ed9-340">array of objects</span></span>|<span data-ttu-id="74ed9-341">10</span><span class="sxs-lookup"><span data-stu-id="74ed9-341">10</span></span>|<span data-ttu-id="74ed9-342">✔</span><span class="sxs-lookup"><span data-stu-id="74ed9-342">✔</span></span>|<span data-ttu-id="74ed9-343">Ein Array von Befehlen, die der Bot unterstützt:</span><span class="sxs-lookup"><span data-stu-id="74ed9-343">An array of commands the bot supports:</span></span><br><span data-ttu-id="74ed9-344">`title`: der Name des Botbefehls (Zeichenfolge, 32).</span><span class="sxs-lookup"><span data-stu-id="74ed9-344">`title`: the bot command name (string, 32).</span></span><br><span data-ttu-id="74ed9-345">`description`: eine einfache Beschreibung oder ein Beispiel für die Befehlssyntax und ihr Argument (Zeichenfolge, 128).</span><span class="sxs-lookup"><span data-stu-id="74ed9-345">`description`: a simple description or example of the command syntax and its argument (string, 128).</span></span>|

## <a name="connectors"></a><span data-ttu-id="74ed9-346">Connectors</span><span class="sxs-lookup"><span data-stu-id="74ed9-346">connectors</span></span>

<span data-ttu-id="74ed9-347">**Optional**</span><span class="sxs-lookup"><span data-stu-id="74ed9-347">**Optional**</span></span>

<span data-ttu-id="74ed9-348">Der `connectors` Block definiert einen Office 365 Connector für die App.</span><span class="sxs-lookup"><span data-stu-id="74ed9-348">The `connectors` block defines an Office 365 Connector for the app.</span></span>

<span data-ttu-id="74ed9-349">Das Objekt ist ein Array (maximal 1 Element) mit allen Elementen vom Typ `object` .</span><span class="sxs-lookup"><span data-stu-id="74ed9-349">The object is an array (maximum of 1 element) with all elements of type `object`.</span></span> <span data-ttu-id="74ed9-350">Dieser Block ist nur für Lösungen erforderlich, die einen Connector bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="74ed9-350">This block is required only for solutions that provide a Connector.</span></span>

|<span data-ttu-id="74ed9-351">Name</span><span class="sxs-lookup"><span data-stu-id="74ed9-351">Name</span></span>| <span data-ttu-id="74ed9-352">Typ</span><span class="sxs-lookup"><span data-stu-id="74ed9-352">Type</span></span>| <span data-ttu-id="74ed9-353">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="74ed9-353">Maximum size</span></span> | <span data-ttu-id="74ed9-354">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="74ed9-354">Required</span></span> | <span data-ttu-id="74ed9-355">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="74ed9-355">Description</span></span>|
|---|---|---|---|---|
|`configurationUrl`|<span data-ttu-id="74ed9-356">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="74ed9-356">String</span></span>|<span data-ttu-id="74ed9-357">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="74ed9-357">2048 characters</span></span>|<span data-ttu-id="74ed9-358">✔</span><span class="sxs-lookup"><span data-stu-id="74ed9-358">✔</span></span>|<span data-ttu-id="74ed9-359">Die https://-URL, die beim Konfigurieren des Connectors verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="74ed9-359">The https:// URL to use when configuring the connector.</span></span>|
|`connectorId`|<span data-ttu-id="74ed9-360">String</span><span class="sxs-lookup"><span data-stu-id="74ed9-360">String</span></span>|<span data-ttu-id="74ed9-361">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="74ed9-361">64 characters</span></span>|<span data-ttu-id="74ed9-362">✔</span><span class="sxs-lookup"><span data-stu-id="74ed9-362">✔</span></span>|<span data-ttu-id="74ed9-363">Ein eindeutiger Bezeichner für den Connector, der seiner ID im [Connectors Developer Dashboard entspricht.](https://aka.ms/connectorsdashboard)</span><span class="sxs-lookup"><span data-stu-id="74ed9-363">A unique identifier for the Connector that matches its ID in the [Connectors Developer Dashboard](https://aka.ms/connectorsdashboard).</span></span>|
|`scopes`|<span data-ttu-id="74ed9-364">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="74ed9-364">Array of enum</span></span>|<span data-ttu-id="74ed9-365">1</span><span class="sxs-lookup"><span data-stu-id="74ed9-365">1</span></span>|<span data-ttu-id="74ed9-366">✔</span><span class="sxs-lookup"><span data-stu-id="74ed9-366">✔</span></span>|<span data-ttu-id="74ed9-367">Gibt an, ob der Connector eine Benutzeroberfläche im Kontext eines Kanals in einem oder eine Benutzeroberfläche bietet, die auf einen einzelnen Benutzer `team` begrenzt ist ( `personal` ).</span><span class="sxs-lookup"><span data-stu-id="74ed9-367">Specifies whether the Connector offers an experience in the context of a channel in a `team`, or an experience scoped to an individual user alone (`personal`).</span></span> <span data-ttu-id="74ed9-368">Derzeit wird nur `team` der Bereich unterstützt.</span><span class="sxs-lookup"><span data-stu-id="74ed9-368">Currently, only the `team` scope is supported.</span></span>|

## <a name="composeextensions"></a><span data-ttu-id="74ed9-369">composeExtensions</span><span class="sxs-lookup"><span data-stu-id="74ed9-369">composeExtensions</span></span>

<span data-ttu-id="74ed9-370">**Optional**</span><span class="sxs-lookup"><span data-stu-id="74ed9-370">**Optional**</span></span>

<span data-ttu-id="74ed9-371">Definiert eine Messagingerweiterung für die App.</span><span class="sxs-lookup"><span data-stu-id="74ed9-371">Defines a messaging extension for the app.</span></span>

> [!NOTE]
> <span data-ttu-id="74ed9-372">Der Name des Features wurde im November 2017 von "Verfassenerweiterung" in "Messagingerweiterung" geändert, der Manifestname bleibt jedoch unverändert, damit vorhandene Erweiterungen weiterhin funktionieren.</span><span class="sxs-lookup"><span data-stu-id="74ed9-372">The name of the feature was changed from "compose extension" to "messaging extension" in November, 2017, but the manifest name remains the same so that existing extensions continue to function.</span></span>

<span data-ttu-id="74ed9-373">Das Objekt ist ein Array (maximal 1 Element) mit allen Elementen vom Typ `object` .</span><span class="sxs-lookup"><span data-stu-id="74ed9-373">The object is an array (maximum of 1 element) with all elements of type `object`.</span></span> <span data-ttu-id="74ed9-374">Dieser Block ist nur für Lösungen erforderlich, die eine Messagingerweiterung bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="74ed9-374">This block is required only for solutions that provide a messaging extension.</span></span>

|<span data-ttu-id="74ed9-375">Name</span><span class="sxs-lookup"><span data-stu-id="74ed9-375">Name</span></span>| <span data-ttu-id="74ed9-376">Typ</span><span class="sxs-lookup"><span data-stu-id="74ed9-376">Type</span></span> | <span data-ttu-id="74ed9-377">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="74ed9-377">Maximum Size</span></span> | <span data-ttu-id="74ed9-378">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="74ed9-378">Required</span></span> | <span data-ttu-id="74ed9-379">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="74ed9-379">Description</span></span>|
|---|---|---|---|---|
|`botId`|<span data-ttu-id="74ed9-380">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="74ed9-380">String</span></span>|<span data-ttu-id="74ed9-381">64</span><span class="sxs-lookup"><span data-stu-id="74ed9-381">64</span></span>|<span data-ttu-id="74ed9-382">✔</span><span class="sxs-lookup"><span data-stu-id="74ed9-382">✔</span></span>|<span data-ttu-id="74ed9-383">Die eindeutige Microsoft-App-ID für den Bot, der die Messagingerweiterung unterstützt, wie beim Bot Framework registriert.</span><span class="sxs-lookup"><span data-stu-id="74ed9-383">The unique Microsoft app ID for the bot that backs the messaging extension, as registered with the Bot Framework.</span></span> <span data-ttu-id="74ed9-384">Dies kann mit der allgemeinen [App-ID identisch sein.](#id)</span><span class="sxs-lookup"><span data-stu-id="74ed9-384">This may well be the same as the overall [app ID](#id).</span></span>|
|`canUpdateConfiguration`|<span data-ttu-id="74ed9-385">Boolesch</span><span class="sxs-lookup"><span data-stu-id="74ed9-385">Boolean</span></span>|||<span data-ttu-id="74ed9-386">Ein Wert, der angibt, ob die Konfiguration einer Messagingerweiterung vom Benutzer aktualisiert werden kann.</span><span class="sxs-lookup"><span data-stu-id="74ed9-386">A value indicating whether the configuration of a messaging extension can be updated by the user.</span></span> <span data-ttu-id="74ed9-387">Der Standardwert lautet `false`.</span><span class="sxs-lookup"><span data-stu-id="74ed9-387">The default is `false`.</span></span>|
|`commands`|<span data-ttu-id="74ed9-388">Array des Objekts</span><span class="sxs-lookup"><span data-stu-id="74ed9-388">Array of object</span></span>|<span data-ttu-id="74ed9-389">10</span><span class="sxs-lookup"><span data-stu-id="74ed9-389">10</span></span>|<span data-ttu-id="74ed9-390">✔</span><span class="sxs-lookup"><span data-stu-id="74ed9-390">✔</span></span>|<span data-ttu-id="74ed9-391">Array von Befehlen, die von der Messagingerweiterung unterstützt werden</span><span class="sxs-lookup"><span data-stu-id="74ed9-391">Array of commands the messaging extension supports</span></span>|

### <a name="composeextensionscommands"></a><span data-ttu-id="74ed9-392">composeExtensions.commands</span><span class="sxs-lookup"><span data-stu-id="74ed9-392">composeExtensions.commands</span></span>

<span data-ttu-id="74ed9-393">Ihre Messagingerweiterung sollte einen oder mehrere Befehle deklarieren.</span><span class="sxs-lookup"><span data-stu-id="74ed9-393">Your messaging extension should declare one or more commands.</span></span> <span data-ttu-id="74ed9-394">Jeder Befehl wird in Microsoft Teams als potenzielle Interaktion vom benutzeroberflächenbasierten Einstiegspunkt angezeigt.</span><span class="sxs-lookup"><span data-stu-id="74ed9-394">Each command appears in Microsoft Teams as a potential interaction from the UI-based entry point.</span></span> <span data-ttu-id="74ed9-395">Es gibt maximal 10 Befehle.</span><span class="sxs-lookup"><span data-stu-id="74ed9-395">There is a maximum of 10 commands.</span></span>

<span data-ttu-id="74ed9-396">Jedes Befehlselement ist ein Objekt mit der folgenden Struktur:</span><span class="sxs-lookup"><span data-stu-id="74ed9-396">Each command item is an object with the following structure:</span></span>

|<span data-ttu-id="74ed9-397">Name</span><span class="sxs-lookup"><span data-stu-id="74ed9-397">Name</span></span>| <span data-ttu-id="74ed9-398">Typ</span><span class="sxs-lookup"><span data-stu-id="74ed9-398">Type</span></span>| <span data-ttu-id="74ed9-399">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="74ed9-399">Maximum size</span></span> | <span data-ttu-id="74ed9-400">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="74ed9-400">Required</span></span> | <span data-ttu-id="74ed9-401">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="74ed9-401">Description</span></span>|
|---|---|---|---|---|
|`id`|<span data-ttu-id="74ed9-402">String</span><span class="sxs-lookup"><span data-stu-id="74ed9-402">String</span></span>|<span data-ttu-id="74ed9-403">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="74ed9-403">64 characters</span></span>|<span data-ttu-id="74ed9-404">✔</span><span class="sxs-lookup"><span data-stu-id="74ed9-404">✔</span></span>|<span data-ttu-id="74ed9-405">Die ID für den Befehl.</span><span class="sxs-lookup"><span data-stu-id="74ed9-405">The ID for the command.</span></span>|
|`type`|<span data-ttu-id="74ed9-406">String</span><span class="sxs-lookup"><span data-stu-id="74ed9-406">String</span></span>|<span data-ttu-id="74ed9-407">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="74ed9-407">64 characters</span></span>||<span data-ttu-id="74ed9-408">Typ des Befehls.</span><span class="sxs-lookup"><span data-stu-id="74ed9-408">Type of the command.</span></span> <span data-ttu-id="74ed9-409">Einer oder `query` `action` .</span><span class="sxs-lookup"><span data-stu-id="74ed9-409">One of `query` or `action`.</span></span> <span data-ttu-id="74ed9-410">Standard: `query`</span><span class="sxs-lookup"><span data-stu-id="74ed9-410">Default: `query`</span></span>|
|`title`|<span data-ttu-id="74ed9-411">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="74ed9-411">String</span></span>|<span data-ttu-id="74ed9-412">32 Zeichen</span><span class="sxs-lookup"><span data-stu-id="74ed9-412">32 characters</span></span>|<span data-ttu-id="74ed9-413">✔</span><span class="sxs-lookup"><span data-stu-id="74ed9-413">✔</span></span>|<span data-ttu-id="74ed9-414">Der benutzerfreundliche Befehlsname.</span><span class="sxs-lookup"><span data-stu-id="74ed9-414">The user-friendly command name.</span></span>|
|`description`|<span data-ttu-id="74ed9-415">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="74ed9-415">String</span></span>|<span data-ttu-id="74ed9-416">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="74ed9-416">128 characters</span></span>||<span data-ttu-id="74ed9-417">Die Beschreibung, die Benutzern angezeigt wird, um den Zweck dieses Befehls anzugeben.</span><span class="sxs-lookup"><span data-stu-id="74ed9-417">The description that appears to users to indicate the purpose of this command.</span></span>|
|`initialRun`|<span data-ttu-id="74ed9-418">Boolesch</span><span class="sxs-lookup"><span data-stu-id="74ed9-418">Boolean</span></span>|||<span data-ttu-id="74ed9-419">Ein boolescher Wert, der angibt, ob der Befehl zunächst ohne Parameter ausgeführt werden soll.</span><span class="sxs-lookup"><span data-stu-id="74ed9-419">A Boolean value that indicates whether the command should be run initially with no parameters.</span></span> <span data-ttu-id="74ed9-420">Standard: `false`</span><span class="sxs-lookup"><span data-stu-id="74ed9-420">Default: `false`</span></span>|
|`context`|<span data-ttu-id="74ed9-421">Array von Zeichenfolgen</span><span class="sxs-lookup"><span data-stu-id="74ed9-421">Array of Strings</span></span>|<span data-ttu-id="74ed9-422">3</span><span class="sxs-lookup"><span data-stu-id="74ed9-422">3</span></span>||<span data-ttu-id="74ed9-423">Definiert, von wo aus die Nachrichtenerweiterung aufgerufen werden kann.</span><span class="sxs-lookup"><span data-stu-id="74ed9-423">Defines where the message extension can be invoked from.</span></span> <span data-ttu-id="74ed9-424">Beliebige Kombination aus `compose` , `commandBox` , `message` .</span><span class="sxs-lookup"><span data-stu-id="74ed9-424">Any combination of `compose`, `commandBox`, `message`.</span></span> <span data-ttu-id="74ed9-425">Standard ist `["compose", "commandBox"]`</span><span class="sxs-lookup"><span data-stu-id="74ed9-425">Default is `["compose", "commandBox"]`</span></span>|
|`fetchTask`|<span data-ttu-id="74ed9-426">Boolesch</span><span class="sxs-lookup"><span data-stu-id="74ed9-426">Boolean</span></span>|||<span data-ttu-id="74ed9-427">Ein boolescher Wert, der angibt, ob das Aufgabenmodul dynamisch abgerufen werden soll.</span><span class="sxs-lookup"><span data-stu-id="74ed9-427">A boolean value that indicates if it should fetch the task module dynamically.</span></span>|
|`taskInfo`|<span data-ttu-id="74ed9-428">Objekt</span><span class="sxs-lookup"><span data-stu-id="74ed9-428">Object</span></span>|||<span data-ttu-id="74ed9-429">Geben Sie das Aufgabenmodul an, das beim Verwenden eines Befehls für die Messagingerweiterung vorab geladen werden soll.</span><span class="sxs-lookup"><span data-stu-id="74ed9-429">Specify the task module to preload when using a messaging extension command.</span></span>|
|`taskInfo.title`|<span data-ttu-id="74ed9-430">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="74ed9-430">String</span></span>|<span data-ttu-id="74ed9-431">64</span><span class="sxs-lookup"><span data-stu-id="74ed9-431">64</span></span>||<span data-ttu-id="74ed9-432">Titel des ersten Dialogfelds.</span><span class="sxs-lookup"><span data-stu-id="74ed9-432">Initial dialog title.</span></span>|
|`taskInfo.width`|<span data-ttu-id="74ed9-433">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="74ed9-433">String</span></span>|||<span data-ttu-id="74ed9-434">Dialogbreite – entweder eine Zahl in Pixel oder ein Standardlayout wie "groß", "mittel" oder "klein".</span><span class="sxs-lookup"><span data-stu-id="74ed9-434">Dialog width - either a number in pixels or default layout such as 'large', 'medium', or 'small'.</span></span>|
|`taskInfo.height`|<span data-ttu-id="74ed9-435">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="74ed9-435">String</span></span>|||<span data-ttu-id="74ed9-436">Dialoghöhe – entweder eine Zahl in Pixel oder ein Standardlayout wie "groß", "mittel" oder "klein".</span><span class="sxs-lookup"><span data-stu-id="74ed9-436">Dialog height - either a number in pixels or default layout such as 'large', 'medium', or 'small'.</span></span>|
|`taskInfo.url`|<span data-ttu-id="74ed9-437">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="74ed9-437">String</span></span>|||<span data-ttu-id="74ed9-438">Anfängliche Webview-URL.</span><span class="sxs-lookup"><span data-stu-id="74ed9-438">Initial webview URL.</span></span>|
|`messageHandlers`|<span data-ttu-id="74ed9-439">Array von Objekten</span><span class="sxs-lookup"><span data-stu-id="74ed9-439">Array of Objects</span></span>|<span data-ttu-id="74ed9-440">5 </span><span class="sxs-lookup"><span data-stu-id="74ed9-440">5</span></span>||<span data-ttu-id="74ed9-441">Eine Liste von Handlern, mit denen Apps aufgerufen werden können, wenn bestimmte Bedingungen erfüllt sind.</span><span class="sxs-lookup"><span data-stu-id="74ed9-441">A list of handlers that allow apps to be invoked when certain conditions are met.</span></span> <span data-ttu-id="74ed9-442">Domänen müssen auch in aufgeführt `validDomains` werden.</span><span class="sxs-lookup"><span data-stu-id="74ed9-442">Domains must also be listed in `validDomains`.</span></span>|
|`messageHandlers.type`|<span data-ttu-id="74ed9-443">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="74ed9-443">String</span></span>|||<span data-ttu-id="74ed9-444">Der Typ des Nachrichtenhandlers.</span><span class="sxs-lookup"><span data-stu-id="74ed9-444">The type of message handler.</span></span> <span data-ttu-id="74ed9-445">Muss `"link"` sein.</span><span class="sxs-lookup"><span data-stu-id="74ed9-445">Must be `"link"`.</span></span>|
|`messageHandlers.value.domains`|<span data-ttu-id="74ed9-446">Array von Zeichenfolgen</span><span class="sxs-lookup"><span data-stu-id="74ed9-446">Array of Strings</span></span>|||<span data-ttu-id="74ed9-447">Array von Domänen, für die der Linknachrichtenhandler registrieren kann.</span><span class="sxs-lookup"><span data-stu-id="74ed9-447">Array of domains that the link message handler can register for.</span></span>|
|`parameters`|<span data-ttu-id="74ed9-448">Array des Objekts</span><span class="sxs-lookup"><span data-stu-id="74ed9-448">Array of object</span></span>|<span data-ttu-id="74ed9-449">5 </span><span class="sxs-lookup"><span data-stu-id="74ed9-449">5</span></span>|<span data-ttu-id="74ed9-450">✔</span><span class="sxs-lookup"><span data-stu-id="74ed9-450">✔</span></span>|<span data-ttu-id="74ed9-451">Die Liste der Parameter, die der Befehl verwendet.</span><span class="sxs-lookup"><span data-stu-id="74ed9-451">The list of parameters the command takes.</span></span> <span data-ttu-id="74ed9-452">Minimum: 1; maximum: 5</span><span class="sxs-lookup"><span data-stu-id="74ed9-452">Minimum: 1; maximum: 5</span></span>|
|`parameter.name`|<span data-ttu-id="74ed9-453">String</span><span class="sxs-lookup"><span data-stu-id="74ed9-453">String</span></span>|<span data-ttu-id="74ed9-454">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="74ed9-454">64 characters</span></span>|<span data-ttu-id="74ed9-455">✔</span><span class="sxs-lookup"><span data-stu-id="74ed9-455">✔</span></span>|<span data-ttu-id="74ed9-456">Der Name des Parameters, wie er im Client angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="74ed9-456">The name of the parameter as it appears in the client.</span></span> <span data-ttu-id="74ed9-457">Dies ist in der Benutzeranforderung enthalten.</span><span class="sxs-lookup"><span data-stu-id="74ed9-457">This is included in the user request.</span></span>|
|`parameter.title`|<span data-ttu-id="74ed9-458">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="74ed9-458">String</span></span>|<span data-ttu-id="74ed9-459">32 Zeichen</span><span class="sxs-lookup"><span data-stu-id="74ed9-459">32 characters</span></span>|<span data-ttu-id="74ed9-460">✔</span><span class="sxs-lookup"><span data-stu-id="74ed9-460">✔</span></span>|<span data-ttu-id="74ed9-461">Benutzerfreundlicher Titel für den Parameter.</span><span class="sxs-lookup"><span data-stu-id="74ed9-461">User-friendly title for the parameter.</span></span>|
|`parameter.description`|<span data-ttu-id="74ed9-462">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="74ed9-462">String</span></span>|<span data-ttu-id="74ed9-463">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="74ed9-463">128 characters</span></span>||<span data-ttu-id="74ed9-464">Benutzerfreundliche Zeichenfolge, die den Zweck dieses Parameters beschreibt.</span><span class="sxs-lookup"><span data-stu-id="74ed9-464">User-friendly string that describes this parameter’s purpose.</span></span>|
|`parameter.inputType`|<span data-ttu-id="74ed9-465">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="74ed9-465">String</span></span>|<span data-ttu-id="74ed9-466">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="74ed9-466">128 characters</span></span>||<span data-ttu-id="74ed9-467">Definiert den Typ des Steuerelements, das in einem Aufgabenmodul für angezeigt `fetchTask: true` wird.</span><span class="sxs-lookup"><span data-stu-id="74ed9-467">Defines the type of control displayed on a task module for `fetchTask: true`.</span></span> <span data-ttu-id="74ed9-468">Einer von `text` , , , , , `textarea` `number` `date` `time` `toggle` `choiceset` .</span><span class="sxs-lookup"><span data-stu-id="74ed9-468">One of `text`, `textarea`, `number`, `date`, `time`, `toggle`, `choiceset`.</span></span>|
|`parameter.choices`|<span data-ttu-id="74ed9-469">Array von Objekten</span><span class="sxs-lookup"><span data-stu-id="74ed9-469">Array of Objects</span></span>|<span data-ttu-id="74ed9-470">10</span><span class="sxs-lookup"><span data-stu-id="74ed9-470">10</span></span>||<span data-ttu-id="74ed9-471">Die Auswahloptionen für `choiceset` .</span><span class="sxs-lookup"><span data-stu-id="74ed9-471">The choice options for the `choiceset`.</span></span> <span data-ttu-id="74ed9-472">Verwenden Sie nur, `parameter.inputType` wenn `choiceset` .</span><span class="sxs-lookup"><span data-stu-id="74ed9-472">Use only when `parameter.inputType` is `choiceset`.</span></span>|
|`parameter.choices.title`|<span data-ttu-id="74ed9-473">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="74ed9-473">String</span></span>|<span data-ttu-id="74ed9-474">128</span><span class="sxs-lookup"><span data-stu-id="74ed9-474">128</span></span>||<span data-ttu-id="74ed9-475">Titel der Auswahl.</span><span class="sxs-lookup"><span data-stu-id="74ed9-475">Title of the choice.</span></span>|
|`parameter.choices.value`|<span data-ttu-id="74ed9-476">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="74ed9-476">String</span></span>|<span data-ttu-id="74ed9-477">512</span><span class="sxs-lookup"><span data-stu-id="74ed9-477">512</span></span>||<span data-ttu-id="74ed9-478">Value of the choice.</span><span class="sxs-lookup"><span data-stu-id="74ed9-478">Value of the choice.</span></span>|

## <a name="permissions"></a><span data-ttu-id="74ed9-479">Berechtigungen</span><span class="sxs-lookup"><span data-stu-id="74ed9-479">permissions</span></span>

<span data-ttu-id="74ed9-480">**Optional**</span><span class="sxs-lookup"><span data-stu-id="74ed9-480">**Optional**</span></span>

<span data-ttu-id="74ed9-481">Ein Array von dem angibt, welche Berechtigungen die App anfordert, wodurch Endbenutzer wissen, `string` wie die Erweiterung funktioniert.</span><span class="sxs-lookup"><span data-stu-id="74ed9-481">An array of `string` which specifies which permissions the app requests, which lets end users know how the extension will perform.</span></span> <span data-ttu-id="74ed9-482">Die folgenden Optionen sind nicht exklusiv:</span><span class="sxs-lookup"><span data-stu-id="74ed9-482">The following options are non-exclusive:</span></span>

* <span data-ttu-id="74ed9-483">`identity`&emsp;Erfordert Benutzeridentitätsinformationen.</span><span class="sxs-lookup"><span data-stu-id="74ed9-483">`identity` &emsp; Requires user identity information.</span></span>
* <span data-ttu-id="74ed9-484">`messageTeamMembers`&emsp;Erfordert die Berechtigung zum Senden von Direktnachrichten an Teammitglieder.</span><span class="sxs-lookup"><span data-stu-id="74ed9-484">`messageTeamMembers` &emsp; Requires permission to send direct messages to team members.</span></span>

<span data-ttu-id="74ed9-485">Wenn Sie diese Berechtigungen beim Aktualisieren Ihrer App ändern, wiederholen Ihre Benutzer den Zustimmungsprozess, wenn sie die aktualisierte App zum ersten Mal ausführen.</span><span class="sxs-lookup"><span data-stu-id="74ed9-485">Changing these permissions when updating your app will cause your users to repeat the consent process the first time they run the updated app.</span></span>

## <a name="devicepermissions"></a><span data-ttu-id="74ed9-486">devicePermissions</span><span class="sxs-lookup"><span data-stu-id="74ed9-486">devicePermissions</span></span>

<span data-ttu-id="74ed9-487">**Optional** Array von Zeichenfolgen</span><span class="sxs-lookup"><span data-stu-id="74ed9-487">**Optional** Array of Strings</span></span>

<span data-ttu-id="74ed9-488">Gibt die systemeigenen Features auf dem Gerät eines Benutzers an, auf die Ihre App möglicherweise Zugriff anfordern kann.</span><span class="sxs-lookup"><span data-stu-id="74ed9-488">Specifies the native features on a user's device that your app may request access to.</span></span> <span data-ttu-id="74ed9-489">Mögliche Optionen sind:</span><span class="sxs-lookup"><span data-stu-id="74ed9-489">Options are:</span></span>

* `geolocation`
* `media`
* `notifications`
* `midi`
* `openExternal`

## <a name="validdomains"></a><span data-ttu-id="74ed9-490">validDomains</span><span class="sxs-lookup"><span data-stu-id="74ed9-490">validDomains</span></span>

<span data-ttu-id="74ed9-491">**Optional**, mit **Ausnahme erforderlich,** sofern angegeben</span><span class="sxs-lookup"><span data-stu-id="74ed9-491">**Optional**, except **Required** where noted</span></span>

<span data-ttu-id="74ed9-492">Eine Liste der gültigen Domänen, von denen die App erwartet, dass alle Inhalte geladen werden.</span><span class="sxs-lookup"><span data-stu-id="74ed9-492">A list of valid domains from which the app expects to load any content.</span></span> <span data-ttu-id="74ed9-493">Domänenauflistungen können Platzhalter enthalten, z. B. `*.example.com` .</span><span class="sxs-lookup"><span data-stu-id="74ed9-493">Domain listings can include wildcards, for example `*.example.com`.</span></span> <span data-ttu-id="74ed9-494">Dies entspricht genau einem Abschnitt der Domäne. wenn Sie übereinstimmen müssen, `a.b.example.com` verwenden Sie `*.*.example.com` .</span><span class="sxs-lookup"><span data-stu-id="74ed9-494">This matches exactly one segment of the domain; if you need to match `a.b.example.com` then use `*.*.example.com`.</span></span> <span data-ttu-id="74ed9-495">Wenn Ihre Registerkartenkonfiguration oder Inhaltsbenutzeroberfläche neben der für die Registerkartenkonfiguration verwendeten Domäne zu einer anderen Domäne navigieren muss, muss diese Domäne hier angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="74ed9-495">If your tab configuration or content UI needs to navigate to any other domain besides the one use for tab configuration, that domain must be specified here.</span></span>

<span data-ttu-id="74ed9-496">Es ist **jedoch nicht** erforderlich, die Domänen von Identitätsanbietern, die Sie unterstützen möchten, in Ihre App zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="74ed9-496">It is **not** necessary to include the domains of identity providers you want to support in your app, however.</span></span> <span data-ttu-id="74ed9-497">Um sich z. B. mit einer Google-ID zu authentifizieren, müssen Sie zu accounts.google.com umleiten, sie sollten jedoch keine accounts.google.com in `validDomains[]` enthalten.</span><span class="sxs-lookup"><span data-stu-id="74ed9-497">For example, to authenticate using a Google ID, it's necessary to redirect to accounts.google.com, but you should not include accounts.google.com in `validDomains[]`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="74ed9-498">Fügen Sie keine Domänen hinzu, die sich außerhalb Ihres Steuerelements befinden, weder direkt noch über Platzhalter.</span><span class="sxs-lookup"><span data-stu-id="74ed9-498">Do not add domains that are outside your control, either directly or via wildcards.</span></span> <span data-ttu-id="74ed9-499">Beispielsweise ist `yourapp.onmicrosoft.com` gültig, aber `*.onmicrosoft.com` nicht gültig.</span><span class="sxs-lookup"><span data-stu-id="74ed9-499">For example, `yourapp.onmicrosoft.com` is valid, but `*.onmicrosoft.com` is not valid.</span></span>

<span data-ttu-id="74ed9-500">Das Objekt ist ein Array mit allen Elementen des Typs `string` .</span><span class="sxs-lookup"><span data-stu-id="74ed9-500">The object is an array with all elements of the type `string`.</span></span>

## <a name="webapplicationinfo"></a><span data-ttu-id="74ed9-501">webApplicationInfo</span><span class="sxs-lookup"><span data-stu-id="74ed9-501">webApplicationInfo</span></span>

<span data-ttu-id="74ed9-502">**Optional**</span><span class="sxs-lookup"><span data-stu-id="74ed9-502">**Optional**</span></span>

<span data-ttu-id="74ed9-503">Geben Sie Ihre AAD-App-ID Graph, um Benutzern die nahtlose Anmeldung bei Ihrer AAD-App zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="74ed9-503">Specify your AAD App ID and Graph information to help users seamlessly sign into your AAD app.</span></span>

|<span data-ttu-id="74ed9-504">Name</span><span class="sxs-lookup"><span data-stu-id="74ed9-504">Name</span></span>| <span data-ttu-id="74ed9-505">Typ</span><span class="sxs-lookup"><span data-stu-id="74ed9-505">Type</span></span>| <span data-ttu-id="74ed9-506">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="74ed9-506">Maximum size</span></span> | <span data-ttu-id="74ed9-507">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="74ed9-507">Required</span></span> | <span data-ttu-id="74ed9-508">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="74ed9-508">Description</span></span>|
|---|---|---|---|---|
|`id`|<span data-ttu-id="74ed9-509">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="74ed9-509">String</span></span>|<span data-ttu-id="74ed9-510">36 Zeichen</span><span class="sxs-lookup"><span data-stu-id="74ed9-510">36 characters</span></span>|<span data-ttu-id="74ed9-511">✔</span><span class="sxs-lookup"><span data-stu-id="74ed9-511">✔</span></span>|<span data-ttu-id="74ed9-512">AAD-Anwendungs-ID der App.</span><span class="sxs-lookup"><span data-stu-id="74ed9-512">AAD application id of the app.</span></span> <span data-ttu-id="74ed9-513">Diese ID muss eine GUID sein.</span><span class="sxs-lookup"><span data-stu-id="74ed9-513">This id must be a GUID.</span></span>|
|`resource`|<span data-ttu-id="74ed9-514">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="74ed9-514">String</span></span>|<span data-ttu-id="74ed9-515">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="74ed9-515">2048 characters</span></span>|<span data-ttu-id="74ed9-516">✔</span><span class="sxs-lookup"><span data-stu-id="74ed9-516">✔</span></span>|<span data-ttu-id="74ed9-517">Ressourcen-URL der App zum Abrufen des Authentifizierungstokens für SSO.</span><span class="sxs-lookup"><span data-stu-id="74ed9-517">Resource url of app for acquiring auth token for SSO.</span></span>|
|`applicationPermissions`|<span data-ttu-id="74ed9-518">Array</span><span class="sxs-lookup"><span data-stu-id="74ed9-518">Array</span></span>|<span data-ttu-id="74ed9-519">Maximal 100 Elemente</span><span class="sxs-lookup"><span data-stu-id="74ed9-519">Maximum 100 items</span></span>|<span data-ttu-id="74ed9-520">✔</span><span class="sxs-lookup"><span data-stu-id="74ed9-520">✔</span></span>|<span data-ttu-id="74ed9-521">Ressourcenberechtigungen für die Anwendung.</span><span class="sxs-lookup"><span data-stu-id="74ed9-521">Resource permissions for application.</span></span>|

## <a name="configurableproperties"></a><span data-ttu-id="74ed9-522">configurableProperties</span><span class="sxs-lookup"><span data-stu-id="74ed9-522">configurableProperties</span></span>

<span data-ttu-id="74ed9-523">**Optional** – Array</span><span class="sxs-lookup"><span data-stu-id="74ed9-523">**Optional** - array</span></span>

<span data-ttu-id="74ed9-524">Der `configurableProperties` Block definiert die App-Eigenschaften, die Teams Administrator anpassen kann.</span><span class="sxs-lookup"><span data-stu-id="74ed9-524">The `configurableProperties` block defines the app properties that Teams admin can customize.</span></span> <span data-ttu-id="74ed9-525">Weitere Informationen finden Sie unter [Anpassen von Apps in Microsoft Teams.](/MicrosoftTeams/customize-apps)</span><span class="sxs-lookup"><span data-stu-id="74ed9-525">For more information, see [customize apps in Microsoft Teams](/MicrosoftTeams/customize-apps).</span></span>

> [!NOTE]
> <span data-ttu-id="74ed9-526">Mindestens eine Eigenschaft muss definiert werden.</span><span class="sxs-lookup"><span data-stu-id="74ed9-526">A minimum of one property must be defined.</span></span> <span data-ttu-id="74ed9-527">Sie können in diesem Block maximal neun Eigenschaften definieren.</span><span class="sxs-lookup"><span data-stu-id="74ed9-527">You can define a maximum of nine properties in this block.</span></span>
> <span data-ttu-id="74ed9-528">Als bewährte Methode müssen Sie Anpassungsrichtlinien für App-Benutzer und -Kunden bereitstellen, die sie beim Anpassen Ihrer App befolgen müssen.</span><span class="sxs-lookup"><span data-stu-id="74ed9-528">As a best practice, you must provide customization guidelines for app users and customers to follow when customizing your app.</span></span> 

<span data-ttu-id="74ed9-529">Sie können eine der folgenden Eigenschaften definieren:</span><span class="sxs-lookup"><span data-stu-id="74ed9-529">You can define any of the following properties:</span></span>
* <span data-ttu-id="74ed9-530">`name`: Ermöglicht administratoren das Ändern des Anzeigenamens der App.</span><span class="sxs-lookup"><span data-stu-id="74ed9-530">`name`: Allows admin to change the app's display name.</span></span>
* <span data-ttu-id="74ed9-531">`shortDescription`: Ermöglicht Administratoren das Ändern der Kurzbeschreibung der App.</span><span class="sxs-lookup"><span data-stu-id="74ed9-531">`shortDescription`: Allows admin to change the app's short description.</span></span>
* <span data-ttu-id="74ed9-532">`longDescription`: Ermöglicht Administratoren das Ändern der detaillierten Beschreibung der App.</span><span class="sxs-lookup"><span data-stu-id="74ed9-532">`longDescription`: Allows admin to change the app's detailed description.</span></span>
* <span data-ttu-id="74ed9-533">`smallImageUrl`: Es handelt sich `outline` um die Eigenschaft im Block des `icons` Manifests.</span><span class="sxs-lookup"><span data-stu-id="74ed9-533">`smallImageUrl`: It is the `outline` property in the `icons` block of the manifest.</span></span>
* <span data-ttu-id="74ed9-534">`largeImageUrl`: Es handelt sich `color` um die Eigenschaft im Block des `icons` Manifests.</span><span class="sxs-lookup"><span data-stu-id="74ed9-534">`largeImageUrl`: It is the `color` property in the `icons` block of the manifest.</span></span>
* <span data-ttu-id="74ed9-535">`accentColor`: Es ist die Farbe, die in Verbindung mit und als Hintergrund für Ihre Gliederungssymbole verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="74ed9-535">`accentColor`: It is the color to use in conjunction with and as a background for your outline icons.</span></span>
* <span data-ttu-id="74ed9-536">`websiteUrl`: Es ist die https://-URL zur Website des Entwicklers.</span><span class="sxs-lookup"><span data-stu-id="74ed9-536">`websiteUrl`: It is the https:// URL to the developer's website.</span></span>
* <span data-ttu-id="74ed9-537">`privacyUrl`: Es ist die https://-URL zur Datenschutzrichtlinie des Entwicklers.</span><span class="sxs-lookup"><span data-stu-id="74ed9-537">`privacyUrl`: It is the https:// URL to the developer's privacy policy.</span></span>
* <span data-ttu-id="74ed9-538">`termsOfUseUrl`: Es ist die https:// URL zu den Nutzungsbedingungen des Entwicklers.</span><span class="sxs-lookup"><span data-stu-id="74ed9-538">`termsOfUseUrl`: It is the https:// URL to the developer's terms of use.</span></span>

## <a name="defaultinstallscope"></a><span data-ttu-id="74ed9-539">defaultInstallScope</span><span class="sxs-lookup"><span data-stu-id="74ed9-539">defaultInstallScope</span></span>

<span data-ttu-id="74ed9-540">**Optional** – Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="74ed9-540">**Optional** - string</span></span>

<span data-ttu-id="74ed9-541">Gibt den für diese App definierten Installationsbereich standardmäßig an.</span><span class="sxs-lookup"><span data-stu-id="74ed9-541">Specifies the install scope defined for this app by default.</span></span> <span data-ttu-id="74ed9-542">Der definierte Bereich ist die Option, die auf der Schaltfläche angezeigt wird, wenn ein Benutzer versucht, die App hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="74ed9-542">The defined scope will be the option displayed on the button when a user tries to add the app.</span></span> <span data-ttu-id="74ed9-543">Mögliche Optionen sind:</span><span class="sxs-lookup"><span data-stu-id="74ed9-543">Options are:</span></span>
* `personal`
* `team`
* `groupchat`
* `meetings`

## <a name="defaultgroupcapability"></a><span data-ttu-id="74ed9-544">defaultGroupCapability</span><span class="sxs-lookup"><span data-stu-id="74ed9-544">defaultGroupCapability</span></span>

<span data-ttu-id="74ed9-545">**Optional** - -Objekt</span><span class="sxs-lookup"><span data-stu-id="74ed9-545">**Optional** - object</span></span>

<span data-ttu-id="74ed9-546">Wenn ein Gruppeninstallationsbereich ausgewählt ist, wird die Standardfunktion definiert, wenn der Benutzer die App installiert.</span><span class="sxs-lookup"><span data-stu-id="74ed9-546">When a group install scope is selected, it will define the default capability when the user installs the app.</span></span> <span data-ttu-id="74ed9-547">Mögliche Optionen sind:</span><span class="sxs-lookup"><span data-stu-id="74ed9-547">Options are:</span></span>
* `team`
* `groupchat`
* `meetings`
 
|<span data-ttu-id="74ed9-548">Name</span><span class="sxs-lookup"><span data-stu-id="74ed9-548">Name</span></span>| <span data-ttu-id="74ed9-549">Typ</span><span class="sxs-lookup"><span data-stu-id="74ed9-549">Type</span></span>| <span data-ttu-id="74ed9-550">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="74ed9-550">Maximum size</span></span> | <span data-ttu-id="74ed9-551">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="74ed9-551">Required</span></span> | <span data-ttu-id="74ed9-552">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="74ed9-552">Description</span></span>|
|---|---|---|---|---|
|`team`|<span data-ttu-id="74ed9-553">string</span><span class="sxs-lookup"><span data-stu-id="74ed9-553">string</span></span>|||<span data-ttu-id="74ed9-554">Wenn der ausgewählte Installationsbereich ausgewählt ist, gibt `team` dieses Feld die verfügbare Standardfunktion an.</span><span class="sxs-lookup"><span data-stu-id="74ed9-554">When the install scope selected is `team`, this field specifies the default capability available.</span></span> <span data-ttu-id="74ed9-555">Optionen: `tab` , `bot` oder `connector` .</span><span class="sxs-lookup"><span data-stu-id="74ed9-555">Options: `tab`, `bot`, or `connector`.</span></span>|
|`groupchat`|<span data-ttu-id="74ed9-556">string</span><span class="sxs-lookup"><span data-stu-id="74ed9-556">string</span></span>|||<span data-ttu-id="74ed9-557">Wenn der ausgewählte Installationsbereich ausgewählt ist, gibt `groupchat` dieses Feld die verfügbare Standardfunktion an.</span><span class="sxs-lookup"><span data-stu-id="74ed9-557">When the install scope selected is `groupchat`, this field specifies the default capability available.</span></span> <span data-ttu-id="74ed9-558">Optionen: `tab` , `bot` oder `connector` .</span><span class="sxs-lookup"><span data-stu-id="74ed9-558">Options: `tab`, `bot`, or `connector`.</span></span>|
|`meetings`|<span data-ttu-id="74ed9-559">string</span><span class="sxs-lookup"><span data-stu-id="74ed9-559">string</span></span>|||<span data-ttu-id="74ed9-560">Wenn der ausgewählte Installationsbereich ausgewählt ist, gibt `meetings` dieses Feld die verfügbare Standardfunktion an.</span><span class="sxs-lookup"><span data-stu-id="74ed9-560">When the install scope selected is `meetings`, this field specifies the default capability available.</span></span> <span data-ttu-id="74ed9-561">Optionen: `tab` , `bot` oder `connector` .</span><span class="sxs-lookup"><span data-stu-id="74ed9-561">Options: `tab`, `bot`, or `connector`.</span></span>|

