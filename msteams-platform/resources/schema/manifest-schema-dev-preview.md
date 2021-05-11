---
title: Developer Preview Manifestschemareferenz
description: Beschreibt das schema, das vom Manifest für die Microsoft Teams
ms.topic: reference
keywords: teams manifest schema Developer Preview
localization_priority: Normal
ms.date: 05/20/2019
ms.openlocfilehash: 05a1becbd021a67e2a843a8ddb5f58ea76cf444e
ms.sourcegitcommit: 808a203fb963eeade3a8e32db88d64677e37df7a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/10/2021
ms.locfileid: "52304019"
---
# <a name="developer-preview-manifest-schema-for-microsoft-teams"></a><span data-ttu-id="6b662-104">Entwicklervorschaumanifestschema für Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="6b662-104">Developer preview manifest schema for Microsoft Teams</span></span>

> [!NOTE]
> <span data-ttu-id="6b662-105">Weitere [Developer Preview](~/resources/dev-preview/developer-preview-intro.md) zum Programm und zur Teilnahme finden Sie unter Developer Preview.</span><span class="sxs-lookup"><span data-stu-id="6b662-105">See [Developer Preview](~/resources/dev-preview/developer-preview-intro.md) for information on the program and how you can join.</span></span>
> <span data-ttu-id="6b662-106">Wenn Sie die Entwicklervorschau nicht verwenden, sollten Sie diese Version des Manifests nicht verwenden.</span><span class="sxs-lookup"><span data-stu-id="6b662-106">If you are not using the developer preview you should not be using this version of the manifest.</span></span> <span data-ttu-id="6b662-107">Informationen [zur öffentlichen Version des Manifests finden Microsoft Teams Referenz:](~/resources/schema/manifest-schema.md) Manifestschema.</span><span class="sxs-lookup"><span data-stu-id="6b662-107">See [Reference: Manifest schema for Microsoft Teams](~/resources/schema/manifest-schema.md) for the public version of the manifest.</span></span>

<span data-ttu-id="6b662-108">Das Microsoft Teams-Manifest beschreibt, wie die App in das Microsoft Teams integriert wird.</span><span class="sxs-lookup"><span data-stu-id="6b662-108">The Microsoft Teams manifest describes how the app integrates into the Microsoft Teams product.</span></span> <span data-ttu-id="6b662-109">Ihr Manifest muss dem schema entsprechen, das unter gehostet [`https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json`](https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json) wird.</span><span class="sxs-lookup"><span data-stu-id="6b662-109">Your manifest must conform to the schema hosted at [`https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json`](https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json).</span></span>

<span data-ttu-id="6b662-110">Weitere Informationen zu den verfügbaren Features finden Sie unter Features [in the Public Developer Preview for Microsoft Teams](~/resources/dev-preview/developer-preview-features.md).</span><span class="sxs-lookup"><span data-stu-id="6b662-110">For more information on the features available see: [Features in the Public Developer Preview for Microsoft Teams](~/resources/dev-preview/developer-preview-features.md).</span></span>

## <a name="sample-full-manifest"></a><span data-ttu-id="6b662-111">Beispiel für vollständiges Manifest</span><span class="sxs-lookup"><span data-stu-id="6b662-111">Sample full manifest</span></span>

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

<span data-ttu-id="6b662-112">Das Schema definiert die folgenden Eigenschaften:</span><span class="sxs-lookup"><span data-stu-id="6b662-112">The schema defines the following properties:</span></span>

## <a name="schema"></a><span data-ttu-id="6b662-113">$schema</span><span class="sxs-lookup"><span data-stu-id="6b662-113">$schema</span></span>

<span data-ttu-id="6b662-114">*Optional, aber empfohlen* &ndash; Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="6b662-114">*Optional, but recommended* &ndash; String</span></span>

<span data-ttu-id="6b662-115">Die https://-URL, die auf das JSON-Schema für das Manifest verweist.</span><span class="sxs-lookup"><span data-stu-id="6b662-115">The https:// URL referencing the JSON Schema for the manifest.</span></span>

## <a name="manifestversion"></a><span data-ttu-id="6b662-116">manifestVersion</span><span class="sxs-lookup"><span data-stu-id="6b662-116">manifestVersion</span></span>

<span data-ttu-id="6b662-117">**Erforderlich** &ndash; Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="6b662-117">**Required** &ndash; String</span></span>

<span data-ttu-id="6b662-118">Die Version des Manifestschemas, das dieses Manifest verwendet.</span><span class="sxs-lookup"><span data-stu-id="6b662-118">The version of the manifest schema this manifest is using.</span></span> <span data-ttu-id="6b662-119">Es sollte "devPreview" sein.</span><span class="sxs-lookup"><span data-stu-id="6b662-119">It should be "devPreview".</span></span>

## <a name="version"></a><span data-ttu-id="6b662-120">Version</span><span class="sxs-lookup"><span data-stu-id="6b662-120">version</span></span>

<span data-ttu-id="6b662-121">**Erforderlich** &ndash; Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="6b662-121">**Required** &ndash; String</span></span>

<span data-ttu-id="6b662-122">Die Version der spezifischen App.</span><span class="sxs-lookup"><span data-stu-id="6b662-122">The version of the specific app.</span></span> <span data-ttu-id="6b662-123">Wenn Sie etwas in Ihrem Manifest aktualisieren, muss auch die Version erhöht werden.</span><span class="sxs-lookup"><span data-stu-id="6b662-123">If you update something in your manifest, the version must be incremented as well.</span></span> <span data-ttu-id="6b662-124">Auf diese Weise wird bei der Installation des neuen Manifests das vorhandene überschrieben, und der Benutzer erhält die neue Funktionalität.</span><span class="sxs-lookup"><span data-stu-id="6b662-124">This way, when the new manifest is installed, it will overwrite the existing one and the user will get the new functionality.</span></span> <span data-ttu-id="6b662-125">Wenn diese App an den Store übermittelt wurde, muss das neue Manifest erneut übermittelt und erneut überprüft werden.</span><span class="sxs-lookup"><span data-stu-id="6b662-125">If this app was submitted to the store, the new manifest will have to be re-submitted and re-validated.</span></span> <span data-ttu-id="6b662-126">Anschließend erhalten Benutzer dieser App das neue aktualisierte Manifest automatisch in ein paar Stunden, nachdem es genehmigt wurde.</span><span class="sxs-lookup"><span data-stu-id="6b662-126">Then, users of this app will get the new updated manifest automatically in a few hours, after it is approved.</span></span>

<span data-ttu-id="6b662-127">Wenn sich die Von der App angeforderten Berechtigungen ändern, werden Die Benutzer aufgefordert, ein Upgrade zu starten und der App erneut zu zustimmen.</span><span class="sxs-lookup"><span data-stu-id="6b662-127">If the app requested permissions change, users will be prompted to upgrade and re-consent to the app.</span></span>

<span data-ttu-id="6b662-128">Diese Versionszeichenfolge muss dem [semver-Standard](http://semver.org/) (MAJOR. MINOR. PATCH).</span><span class="sxs-lookup"><span data-stu-id="6b662-128">This version string must follow the [semver](http://semver.org/) standard (MAJOR.MINOR.PATCH).</span></span>

## <a name="id"></a><span data-ttu-id="6b662-129">id</span><span class="sxs-lookup"><span data-stu-id="6b662-129">id</span></span>

<span data-ttu-id="6b662-130">**Erforderlich** &ndash; Microsoft-App-ID</span><span class="sxs-lookup"><span data-stu-id="6b662-130">**Required** &ndash; Microsoft app ID</span></span>

<span data-ttu-id="6b662-131">Der eindeutige von Microsoft generierte Bezeichner für diese App.</span><span class="sxs-lookup"><span data-stu-id="6b662-131">The unique Microsoft-generated identifier for this app.</span></span> <span data-ttu-id="6b662-132">Wenn Sie einen Bot über das Microsoft Bot Framework registriert haben oder sich die Web-App Ihrer Registerkarte bereits bei Microsoft angemeldet hat, sollten Sie bereits über eine ID verfügen und ihn hier eingeben.</span><span class="sxs-lookup"><span data-stu-id="6b662-132">If you have registered a bot via the Microsoft Bot Framework, or your tab's web app already signs in with Microsoft, you should already have an ID and should enter it here.</span></span> <span data-ttu-id="6b662-133">Andernfalls sollten Sie eine neue ID im Microsoft Application Registration Portal ([Meine](https://apps.dev.microsoft.com)Anwendungen ) generieren, sie hier eingeben und dann wiederverwenden, wenn Sie [einen Bot hinzufügen.](~/bots/how-to/create-a-bot-for-teams.md)</span><span class="sxs-lookup"><span data-stu-id="6b662-133">Otherwise, you should generate a new ID at the Microsoft Application Registration Portal ([My Applications](https://apps.dev.microsoft.com)), enter it here, and then reuse it when you [add a bot](~/bots/how-to/create-a-bot-for-teams.md).</span></span>

## <a name="packagename"></a><span data-ttu-id="6b662-134">packageName</span><span class="sxs-lookup"><span data-stu-id="6b662-134">packageName</span></span>

<span data-ttu-id="6b662-135">**Erforderlich** &ndash; Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="6b662-135">**Required** &ndash; String</span></span>

<span data-ttu-id="6b662-136">Ein eindeutiger Bezeichner für diese App in umgekehrter Domänen-Notation; z. B. com.example.myapp.</span><span class="sxs-lookup"><span data-stu-id="6b662-136">A unique identifier for this app in reverse domain notation; for example, com.example.myapp.</span></span>

## <a name="developer"></a><span data-ttu-id="6b662-137">developer</span><span class="sxs-lookup"><span data-stu-id="6b662-137">developer</span></span>

<span data-ttu-id="6b662-138">**Required**</span><span class="sxs-lookup"><span data-stu-id="6b662-138">**Required**</span></span>

<span data-ttu-id="6b662-139">Gibt Informationen zu Ihrem Unternehmen an.</span><span class="sxs-lookup"><span data-stu-id="6b662-139">Specifies information about your company.</span></span> <span data-ttu-id="6b662-140">Für apps submitted to AppSource (formerly Office Store), these values must match the information in your AppSource entry.</span><span class="sxs-lookup"><span data-stu-id="6b662-140">For apps submitted to AppSource (formerly Office Store), these values must match the information in your AppSource entry.</span></span>

|<span data-ttu-id="6b662-141">Name</span><span class="sxs-lookup"><span data-stu-id="6b662-141">Name</span></span>| <span data-ttu-id="6b662-142">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="6b662-142">Maximum size</span></span> | <span data-ttu-id="6b662-143">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="6b662-143">Required</span></span> | <span data-ttu-id="6b662-144">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="6b662-144">Description</span></span>|
|---|---|---|---|
|`name`|<span data-ttu-id="6b662-145">32 Zeichen</span><span class="sxs-lookup"><span data-stu-id="6b662-145">32 characters</span></span>|<span data-ttu-id="6b662-146">✔</span><span class="sxs-lookup"><span data-stu-id="6b662-146">✔</span></span>|<span data-ttu-id="6b662-147">Der Anzeigename für den Entwickler.</span><span class="sxs-lookup"><span data-stu-id="6b662-147">The display name for the developer.</span></span>|
|`websiteUrl`|<span data-ttu-id="6b662-148">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="6b662-148">2048 characters</span></span>|<span data-ttu-id="6b662-149">✔</span><span class="sxs-lookup"><span data-stu-id="6b662-149">✔</span></span>|<span data-ttu-id="6b662-150">Die https://-URL zur Website des Entwicklers.</span><span class="sxs-lookup"><span data-stu-id="6b662-150">The https:// URL to the developer's website.</span></span> <span data-ttu-id="6b662-151">Dieser Link sollte Benutzer zu Ihrer unternehmens- oder produktspezifischen Angebotsseite gelangen.</span><span class="sxs-lookup"><span data-stu-id="6b662-151">This link should take users to your company or product-specific landing page.</span></span>|
|`privacyUrl`|<span data-ttu-id="6b662-152">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="6b662-152">2048 characters</span></span>|<span data-ttu-id="6b662-153">✔</span><span class="sxs-lookup"><span data-stu-id="6b662-153">✔</span></span>|<span data-ttu-id="6b662-154">Die https:// url to the developer's privacy policy.</span><span class="sxs-lookup"><span data-stu-id="6b662-154">The https:// URL to the developer's privacy policy.</span></span>|
|`termsOfUseUrl`|<span data-ttu-id="6b662-155">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="6b662-155">2048 characters</span></span>|<span data-ttu-id="6b662-156">✔</span><span class="sxs-lookup"><span data-stu-id="6b662-156">✔</span></span>|<span data-ttu-id="6b662-157">Die https:// URL zu den Nutzungsbedingungen des Entwicklers.</span><span class="sxs-lookup"><span data-stu-id="6b662-157">The https:// URL to the developer's terms of use.</span></span>|
|`mpnId`|<span data-ttu-id="6b662-158">10 Zeichen</span><span class="sxs-lookup"><span data-stu-id="6b662-158">10 characters</span></span>|<span data-ttu-id="6b662-159">✔</span><span class="sxs-lookup"><span data-stu-id="6b662-159">✔</span></span>|<span data-ttu-id="6b662-160">**Optional** Die Microsoft Partner Network ID, die die Partnerorganisation identifiziert, die die App erstellt.</span><span class="sxs-lookup"><span data-stu-id="6b662-160">**Optional** The Microsoft Partner Network ID that identifies the partner organization building the app.</span></span>|

## <a name="localizationinfo"></a><span data-ttu-id="6b662-161">localizationInfo</span><span class="sxs-lookup"><span data-stu-id="6b662-161">localizationInfo</span></span>

<span data-ttu-id="6b662-162">**Optional**</span><span class="sxs-lookup"><span data-stu-id="6b662-162">**Optional**</span></span>

<span data-ttu-id="6b662-163">Ermöglicht die Angabe einer Standardsprache sowie Zeiger auf zusätzliche Sprachdateien.</span><span class="sxs-lookup"><span data-stu-id="6b662-163">Allows the specification of a default language, as well as pointers to additional language files.</span></span> <span data-ttu-id="6b662-164">Weitere [Informationen finden Sie unter Lokalisierung](~/concepts/build-and-test/apps-localization.md).</span><span class="sxs-lookup"><span data-stu-id="6b662-164">See [localization](~/concepts/build-and-test/apps-localization.md).</span></span>

|<span data-ttu-id="6b662-165">Name</span><span class="sxs-lookup"><span data-stu-id="6b662-165">Name</span></span>| <span data-ttu-id="6b662-166">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="6b662-166">Maximum size</span></span> | <span data-ttu-id="6b662-167">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="6b662-167">Required</span></span> | <span data-ttu-id="6b662-168">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="6b662-168">Description</span></span>|
|---|---|---|---|
|`defaultLanguageTag`|<span data-ttu-id="6b662-169">4 Zeichen</span><span class="sxs-lookup"><span data-stu-id="6b662-169">4 characters</span></span>|<span data-ttu-id="6b662-170">✔</span><span class="sxs-lookup"><span data-stu-id="6b662-170">✔</span></span>|<span data-ttu-id="6b662-171">Das Sprachtag der Zeichenfolgen in dieser Manifestdatei auf oberster Ebene.</span><span class="sxs-lookup"><span data-stu-id="6b662-171">The language tag of the strings in this top level manifest file.</span></span>|

### <a name="localizationinfoadditionallanguages"></a><span data-ttu-id="6b662-172">localizationInfo.additionalLanguages</span><span class="sxs-lookup"><span data-stu-id="6b662-172">localizationInfo.additionalLanguages</span></span>

<span data-ttu-id="6b662-173">Ein Array von Objekten, die zusätzliche Sprachübersetzungen angeben.</span><span class="sxs-lookup"><span data-stu-id="6b662-173">An array of objects specifying additional language translations.</span></span>

|<span data-ttu-id="6b662-174">Name</span><span class="sxs-lookup"><span data-stu-id="6b662-174">Name</span></span>| <span data-ttu-id="6b662-175">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="6b662-175">Maximum size</span></span> | <span data-ttu-id="6b662-176">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="6b662-176">Required</span></span> | <span data-ttu-id="6b662-177">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="6b662-177">Description</span></span>|
|---|---|---|---|
|`languageTag`|<span data-ttu-id="6b662-178">4 Zeichen</span><span class="sxs-lookup"><span data-stu-id="6b662-178">4 characters</span></span>|<span data-ttu-id="6b662-179">✔</span><span class="sxs-lookup"><span data-stu-id="6b662-179">✔</span></span>|<span data-ttu-id="6b662-180">Das Sprachtag der Zeichenfolgen in der bereitgestellten Datei.</span><span class="sxs-lookup"><span data-stu-id="6b662-180">The language tag of the strings in the provided file.</span></span>|
|`file`|<span data-ttu-id="6b662-181">4 Zeichen</span><span class="sxs-lookup"><span data-stu-id="6b662-181">4 characters</span></span>|<span data-ttu-id="6b662-182">✔</span><span class="sxs-lookup"><span data-stu-id="6b662-182">✔</span></span>|<span data-ttu-id="6b662-183">Ein relativer Dateipfad zu einer .json-Datei, die die übersetzten Zeichenfolgen enthält.</span><span class="sxs-lookup"><span data-stu-id="6b662-183">A relative file path to a the .json file containing the translated strings.</span></span>|

## <a name="name"></a><span data-ttu-id="6b662-184">name</span><span class="sxs-lookup"><span data-stu-id="6b662-184">name</span></span>

<span data-ttu-id="6b662-185">**Required**</span><span class="sxs-lookup"><span data-stu-id="6b662-185">**Required**</span></span>

<span data-ttu-id="6b662-186">Der Name Ihrer App-Erfahrung, der Benutzern in der Teams angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="6b662-186">The name of your app experience, displayed to users in the Teams experience.</span></span> <span data-ttu-id="6b662-187">Für apps submitted to AppSource, these values must match the information in your AppSource entry.</span><span class="sxs-lookup"><span data-stu-id="6b662-187">For apps submitted to AppSource, these values must match the information in your AppSource entry.</span></span> <span data-ttu-id="6b662-188">Die Werte von `short` und sollten nicht identisch `full` sein.</span><span class="sxs-lookup"><span data-stu-id="6b662-188">The values of `short` and `full` should not be the same.</span></span>

|<span data-ttu-id="6b662-189">Name</span><span class="sxs-lookup"><span data-stu-id="6b662-189">Name</span></span>| <span data-ttu-id="6b662-190">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="6b662-190">Maximum size</span></span> | <span data-ttu-id="6b662-191">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="6b662-191">Required</span></span> | <span data-ttu-id="6b662-192">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="6b662-192">Description</span></span>|
|---|---|---|---|
|`short`|<span data-ttu-id="6b662-193">30 Zeichen</span><span class="sxs-lookup"><span data-stu-id="6b662-193">30 characters</span></span>|<span data-ttu-id="6b662-194">✔</span><span class="sxs-lookup"><span data-stu-id="6b662-194">✔</span></span>|<span data-ttu-id="6b662-195">Der kurze Anzeigename für die App.</span><span class="sxs-lookup"><span data-stu-id="6b662-195">The short display name for the app.</span></span>|
|`full`|<span data-ttu-id="6b662-196">100 Zeichen</span><span class="sxs-lookup"><span data-stu-id="6b662-196">100 characters</span></span>||<span data-ttu-id="6b662-197">Der vollständige Name der App, der verwendet wird, wenn der vollständige Name der App 30 Zeichen überschreitet.</span><span class="sxs-lookup"><span data-stu-id="6b662-197">The full name of the app, used if the full app name exceeds 30 characters.</span></span>|

## <a name="description"></a><span data-ttu-id="6b662-198">description</span><span class="sxs-lookup"><span data-stu-id="6b662-198">description</span></span>

<span data-ttu-id="6b662-199">**Required**</span><span class="sxs-lookup"><span data-stu-id="6b662-199">**Required**</span></span>

<span data-ttu-id="6b662-200">Beschreibt Ihre App für Benutzer.</span><span class="sxs-lookup"><span data-stu-id="6b662-200">Describes your app to users.</span></span> <span data-ttu-id="6b662-201">Für apps submitted to AppSource, these values must match the information in your AppSource entry.</span><span class="sxs-lookup"><span data-stu-id="6b662-201">For apps submitted to AppSource, these values must match the information in your AppSource entry.</span></span>

<span data-ttu-id="6b662-202">Stellen Sie sicher, dass Ihre Beschreibung Ihre Erfahrung genau beschreibt und Informationen enthält, mit deren Hilfe potenzielle Kunden besser verstehen können, was Ihre Erfahrung bedeutet.</span><span class="sxs-lookup"><span data-stu-id="6b662-202">Ensure that your description accurately describes your experience and provides information to help potential customers understand what your experience does.</span></span> <span data-ttu-id="6b662-203">Beachten Sie auch in der vollständigen Beschreibung, ob ein externes Konto für die Verwendung erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="6b662-203">You should also note, in the full description, if an external account is required for use.</span></span> <span data-ttu-id="6b662-204">Die Werte von `short` und sollten nicht identisch `full` sein.</span><span class="sxs-lookup"><span data-stu-id="6b662-204">The values of `short` and `full` should not be the same.</span></span>  <span data-ttu-id="6b662-205">Ihre kurze Beschreibung darf nicht innerhalb der langen Beschreibung wiederholt werden und darf keinen anderen App-Namen enthalten.</span><span class="sxs-lookup"><span data-stu-id="6b662-205">Your short description must not be repeated within the long description and must not include any other app name.</span></span>

|<span data-ttu-id="6b662-206">Name</span><span class="sxs-lookup"><span data-stu-id="6b662-206">Name</span></span>| <span data-ttu-id="6b662-207">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="6b662-207">Maximum size</span></span> | <span data-ttu-id="6b662-208">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="6b662-208">Required</span></span> | <span data-ttu-id="6b662-209">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="6b662-209">Description</span></span>|
|---|---|---|---|
|`short`|<span data-ttu-id="6b662-210">80 Zeichen</span><span class="sxs-lookup"><span data-stu-id="6b662-210">80 characters</span></span>|<span data-ttu-id="6b662-211">✔</span><span class="sxs-lookup"><span data-stu-id="6b662-211">✔</span></span>|<span data-ttu-id="6b662-212">Eine kurze Beschreibung Ihrer App-Erfahrung, die bei begrenztem Speicherplatz verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="6b662-212">A short description of your app experience, used when space is limited.</span></span>|
|`full`|<span data-ttu-id="6b662-213">4000 Zeichen</span><span class="sxs-lookup"><span data-stu-id="6b662-213">4000 characters</span></span>|<span data-ttu-id="6b662-214">✔</span><span class="sxs-lookup"><span data-stu-id="6b662-214">✔</span></span>|<span data-ttu-id="6b662-215">Die vollständige Beschreibung Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="6b662-215">The full description of your app.</span></span>|

## <a name="icons"></a><span data-ttu-id="6b662-216">Symbole</span><span class="sxs-lookup"><span data-stu-id="6b662-216">icons</span></span>

<span data-ttu-id="6b662-217">**Required**</span><span class="sxs-lookup"><span data-stu-id="6b662-217">**Required**</span></span>

<span data-ttu-id="6b662-218">Symbole, die innerhalb der Teams werden.</span><span class="sxs-lookup"><span data-stu-id="6b662-218">Icons used within the Teams app.</span></span> <span data-ttu-id="6b662-219">Die Symboldateien müssen als Teil des Uploadpakets enthalten sein.</span><span class="sxs-lookup"><span data-stu-id="6b662-219">The icon files must be included as part of the upload package.</span></span>

|<span data-ttu-id="6b662-220">Name</span><span class="sxs-lookup"><span data-stu-id="6b662-220">Name</span></span>| <span data-ttu-id="6b662-221">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="6b662-221">Maximum size</span></span> | <span data-ttu-id="6b662-222">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="6b662-222">Required</span></span> | <span data-ttu-id="6b662-223">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="6b662-223">Description</span></span>|
|---|---|---|---|
|`outline`|<span data-ttu-id="6b662-224">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="6b662-224">2048 characters</span></span>|<span data-ttu-id="6b662-225">✔</span><span class="sxs-lookup"><span data-stu-id="6b662-225">✔</span></span>|<span data-ttu-id="6b662-226">Ein relativer Dateipfad zu einem transparenten 32 x 32 PNG-Gliederungssymbol.</span><span class="sxs-lookup"><span data-stu-id="6b662-226">A relative file path to a transparent 32x32 PNG outline icon.</span></span>|
|`color`|<span data-ttu-id="6b662-227">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="6b662-227">2048 characters</span></span>|<span data-ttu-id="6b662-228">✔</span><span class="sxs-lookup"><span data-stu-id="6b662-228">✔</span></span>|<span data-ttu-id="6b662-229">Ein relativer Dateipfad zu einem vollfarbigen 192 x 192-PNG-Symbol.</span><span class="sxs-lookup"><span data-stu-id="6b662-229">A relative file path to a full color 192x192 PNG icon.</span></span>|

## <a name="accentcolor"></a><span data-ttu-id="6b662-230">accentColor</span><span class="sxs-lookup"><span data-stu-id="6b662-230">accentColor</span></span>

<span data-ttu-id="6b662-231">**Erforderlich** &ndash; Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="6b662-231">**Required** &ndash; String</span></span>

<span data-ttu-id="6b662-232">Eine Farbe, die in Verbindung mit und als Hintergrund für Ihre Gliederungssymbole verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="6b662-232">A color to use in conjunction with and as a background for your outline icons.</span></span>

<span data-ttu-id="6b662-233">Der Wert muss ein gültiger #A0 sein, der mit "#" beginnt, z. B. `#4464ee` .</span><span class="sxs-lookup"><span data-stu-id="6b662-233">The value must be a valid HTML color code starting with '#', for example `#4464ee`.</span></span>

## <a name="configurabletabs"></a><span data-ttu-id="6b662-234">configurableTabs</span><span class="sxs-lookup"><span data-stu-id="6b662-234">configurableTabs</span></span>

<span data-ttu-id="6b662-235">**Optional**</span><span class="sxs-lookup"><span data-stu-id="6b662-235">**Optional**</span></span>

<span data-ttu-id="6b662-236">Wird verwendet, wenn Ihre App über eine Registerkartenerfahrung im Teamkanal verfügt, die eine zusätzliche Konfiguration erfordert, bevor sie hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="6b662-236">Used when your app experience has a team channel tab experience that requires extra configuration before it is added.</span></span> <span data-ttu-id="6b662-237">Konfigurierbare Registerkarten werden nur im Bereich Teams unterstützt, und derzeit wird nur eine Registerkarte pro App unterstützt.</span><span class="sxs-lookup"><span data-stu-id="6b662-237">Configurable tabs are supported only in the teams scope, and currently only one tab per app is supported.</span></span>

<span data-ttu-id="6b662-238">Das Objekt ist ein Array mit allen Elementen des Typs `object` .</span><span class="sxs-lookup"><span data-stu-id="6b662-238">The object is an array with all elements of the type `object`.</span></span> <span data-ttu-id="6b662-239">Dieser Block ist nur für Lösungen erforderlich, die eine konfigurierbare Kanalregisterkartenlösung bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="6b662-239">This block is required only for solutions that provide a configurable channel tab solution.</span></span>

|<span data-ttu-id="6b662-240">Name</span><span class="sxs-lookup"><span data-stu-id="6b662-240">Name</span></span>| <span data-ttu-id="6b662-241">Typ</span><span class="sxs-lookup"><span data-stu-id="6b662-241">Type</span></span>| <span data-ttu-id="6b662-242">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="6b662-242">Maximum size</span></span> | <span data-ttu-id="6b662-243">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="6b662-243">Required</span></span> | <span data-ttu-id="6b662-244">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="6b662-244">Description</span></span>|
|---|---|---|---|---|
|`configurationUrl`|<span data-ttu-id="6b662-245">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="6b662-245">String</span></span>|<span data-ttu-id="6b662-246">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="6b662-246">2048 characters</span></span>|<span data-ttu-id="6b662-247">✔</span><span class="sxs-lookup"><span data-stu-id="6b662-247">✔</span></span>|<span data-ttu-id="6b662-248">Die https:// URL, die beim Konfigurieren der Registerkarte verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="6b662-248">The https:// URL to use when configuring the tab.</span></span>|
|`canUpdateConfiguration`|<span data-ttu-id="6b662-249">Boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="6b662-249">Boolean</span></span>|||<span data-ttu-id="6b662-250">Ein Wert, der angibt, ob eine Instanz der Registerkartenkonfiguration vom Benutzer nach der Erstellung aktualisiert werden kann.</span><span class="sxs-lookup"><span data-stu-id="6b662-250">A value indicating whether an instance of the tab's configuration can be updated by the user after creation.</span></span> <span data-ttu-id="6b662-251">Standard: `true`</span><span class="sxs-lookup"><span data-stu-id="6b662-251">Default: `true`</span></span>|
|`scopes`|<span data-ttu-id="6b662-252">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="6b662-252">Array of enum</span></span>|<span data-ttu-id="6b662-253">1</span><span class="sxs-lookup"><span data-stu-id="6b662-253">1</span></span>|<span data-ttu-id="6b662-254">✔</span><span class="sxs-lookup"><span data-stu-id="6b662-254">✔</span></span>|<span data-ttu-id="6b662-255">Derzeit unterstützen konfigurierbare Registerkarten nur die `team` Bereiche `groupchat` und.</span><span class="sxs-lookup"><span data-stu-id="6b662-255">Currently, configurable tabs support only the `team` and `groupchat` scopes.</span></span> |
|`sharePointPreviewImage`|<span data-ttu-id="6b662-256">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="6b662-256">String</span></span>|<span data-ttu-id="6b662-257">2048</span><span class="sxs-lookup"><span data-stu-id="6b662-257">2048</span></span>||<span data-ttu-id="6b662-258">Ein relativer Dateipfad zu einem Registerkartenvorschaubild zur Verwendung in SharePoint.</span><span class="sxs-lookup"><span data-stu-id="6b662-258">A relative file path to a tab preview image for use in SharePoint.</span></span> <span data-ttu-id="6b662-259">Größe 1024 x 768.</span><span class="sxs-lookup"><span data-stu-id="6b662-259">Size 1024x768.</span></span> |
|`supportedSharePointHosts`|<span data-ttu-id="6b662-260">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="6b662-260">Array of enum</span></span>|<span data-ttu-id="6b662-261">1</span><span class="sxs-lookup"><span data-stu-id="6b662-261">1</span></span>||<span data-ttu-id="6b662-262">Definiert, wie Ihre Registerkarte in der SharePoint.</span><span class="sxs-lookup"><span data-stu-id="6b662-262">Defines how your tab will be made available in SharePoint.</span></span> <span data-ttu-id="6b662-263">Optionen sind `sharePointFullPage` und `sharePointWebPart`</span><span class="sxs-lookup"><span data-stu-id="6b662-263">Options are `sharePointFullPage` and `sharePointWebPart`</span></span> |

## <a name="statictabs"></a><span data-ttu-id="6b662-264">staticTabs</span><span class="sxs-lookup"><span data-stu-id="6b662-264">staticTabs</span></span>

<span data-ttu-id="6b662-265">**Optional**</span><span class="sxs-lookup"><span data-stu-id="6b662-265">**Optional**</span></span>

<span data-ttu-id="6b662-266">Definiert eine Reihe von Registerkarten, die standardmäßig angeheftet werden können, ohne dass der Benutzer sie manuell hinzufügungen muss.</span><span class="sxs-lookup"><span data-stu-id="6b662-266">Defines a set of tabs that can be "pinned" by default, without the user adding them manually.</span></span> <span data-ttu-id="6b662-267">Statische Registerkarten, die im Bereich deklariert sind, werden immer an die persönliche Be benutzererfahrung `personal` der App angeheftet.</span><span class="sxs-lookup"><span data-stu-id="6b662-267">Static tabs declared in `personal` scope are always pinned to the app's personal experience.</span></span> <span data-ttu-id="6b662-268">Statische Registerkarten, die im Bereich `team` deklariert sind, werden derzeit nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="6b662-268">Static tabs declared in the `team` scope are currently not supported.</span></span>

<span data-ttu-id="6b662-269">Das Objekt ist ein Array (maximal 16 Elemente) mit allen Elementen des Typs `object` .</span><span class="sxs-lookup"><span data-stu-id="6b662-269">The object is an array (maximum of 16 elements) with all elements of the type `object`.</span></span> <span data-ttu-id="6b662-270">Dieser Block ist nur für Lösungen erforderlich, die eine statische Registerkartenlösung bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="6b662-270">This block is required only for solutions that provide a static tab solution.</span></span>

|<span data-ttu-id="6b662-271">Name</span><span class="sxs-lookup"><span data-stu-id="6b662-271">Name</span></span>| <span data-ttu-id="6b662-272">Typ</span><span class="sxs-lookup"><span data-stu-id="6b662-272">Type</span></span>| <span data-ttu-id="6b662-273">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="6b662-273">Maximum size</span></span> | <span data-ttu-id="6b662-274">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="6b662-274">Required</span></span> | <span data-ttu-id="6b662-275">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="6b662-275">Description</span></span>|
|---|---|---|---|---|
|`entityId`|<span data-ttu-id="6b662-276">String</span><span class="sxs-lookup"><span data-stu-id="6b662-276">String</span></span>|<span data-ttu-id="6b662-277">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="6b662-277">64 characters</span></span>|<span data-ttu-id="6b662-278">✔</span><span class="sxs-lookup"><span data-stu-id="6b662-278">✔</span></span>|<span data-ttu-id="6b662-279">Ein eindeutiger Bezeichner für die Entität, die auf der Registerkarte angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="6b662-279">A unique identifier for the entity that the tab displays.</span></span>|
|`name`|<span data-ttu-id="6b662-280">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="6b662-280">String</span></span>|<span data-ttu-id="6b662-281">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="6b662-281">128 characters</span></span>|<span data-ttu-id="6b662-282">✔</span><span class="sxs-lookup"><span data-stu-id="6b662-282">✔</span></span>|<span data-ttu-id="6b662-283">Der Anzeigename der Registerkarte in der Kanalschnittstelle.</span><span class="sxs-lookup"><span data-stu-id="6b662-283">The display name of the tab in the channel interface.</span></span>|
|`contentUrl`|<span data-ttu-id="6b662-284">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="6b662-284">String</span></span>|<span data-ttu-id="6b662-285">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="6b662-285">2048 characters</span></span>|<span data-ttu-id="6b662-286">✔</span><span class="sxs-lookup"><span data-stu-id="6b662-286">✔</span></span>|<span data-ttu-id="6b662-287">Die https://-URL, die auf die Entitätsbenutzeroberfläche verweist, die im Zeichenbereich Teams werden soll.</span><span class="sxs-lookup"><span data-stu-id="6b662-287">The https:// URL that points to the entity UI to be displayed in the Teams canvas.</span></span>|
|`websiteUrl`|<span data-ttu-id="6b662-288">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="6b662-288">String</span></span>|<span data-ttu-id="6b662-289">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="6b662-289">2048 characters</span></span>||<span data-ttu-id="6b662-290">Die https:// URL, auf die verweisen soll, wenn sich ein Benutzer für die Anzeige in einem Browser entscheidet.</span><span class="sxs-lookup"><span data-stu-id="6b662-290">The https:// URL to point at if a user opts to view in a browser.</span></span>|
|`scopes`|<span data-ttu-id="6b662-291">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="6b662-291">Array of enum</span></span>|<span data-ttu-id="6b662-292">1</span><span class="sxs-lookup"><span data-stu-id="6b662-292">1</span></span>|<span data-ttu-id="6b662-293">✔</span><span class="sxs-lookup"><span data-stu-id="6b662-293">✔</span></span>|<span data-ttu-id="6b662-294">Derzeit unterstützen statische Registerkarten nur den Bereich, d. h., er kann nur als Teil der `personal` persönlichen Erfahrung bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="6b662-294">Currently, static tabs support only the `personal` scope, which means it can be provisioned only as part of the personal experience.</span></span>|

## <a name="bots"></a><span data-ttu-id="6b662-295">Bots</span><span class="sxs-lookup"><span data-stu-id="6b662-295">bots</span></span>

<span data-ttu-id="6b662-296">**Optional**</span><span class="sxs-lookup"><span data-stu-id="6b662-296">**Optional**</span></span>

<span data-ttu-id="6b662-297">Definiert eine Botlösung zusammen mit optionalen Informationen, z. B. Standardbefehlseigenschaften.</span><span class="sxs-lookup"><span data-stu-id="6b662-297">Defines a bot solution, along with optional information such as default command properties.</span></span>

<span data-ttu-id="6b662-298">Das Objekt ist ein Array (maximal 1 Element ist derzeit nur ein Bot pro App zulässig) mit allen Elementen &mdash; des Typs `object` .</span><span class="sxs-lookup"><span data-stu-id="6b662-298">The object is an array (maximum of only 1 element&mdash;currently only one bot is allowed per app) with all elements of the type `object`.</span></span> <span data-ttu-id="6b662-299">Dieser Block ist nur für Lösungen erforderlich, die eine Boterfahrung bieten.</span><span class="sxs-lookup"><span data-stu-id="6b662-299">This block is required only for solutions that provide a bot experience.</span></span>

|<span data-ttu-id="6b662-300">Name</span><span class="sxs-lookup"><span data-stu-id="6b662-300">Name</span></span>| <span data-ttu-id="6b662-301">Typ</span><span class="sxs-lookup"><span data-stu-id="6b662-301">Type</span></span>| <span data-ttu-id="6b662-302">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="6b662-302">Maximum size</span></span> | <span data-ttu-id="6b662-303">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="6b662-303">Required</span></span> | <span data-ttu-id="6b662-304">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="6b662-304">Description</span></span>|
|---|---|---|---|---|
|`botId`|<span data-ttu-id="6b662-305">String</span><span class="sxs-lookup"><span data-stu-id="6b662-305">String</span></span>|<span data-ttu-id="6b662-306">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="6b662-306">64 characters</span></span>|<span data-ttu-id="6b662-307">✔</span><span class="sxs-lookup"><span data-stu-id="6b662-307">✔</span></span>|<span data-ttu-id="6b662-308">Die eindeutige Microsoft-App-ID für den Bot, wie bei Bot Framework registriert.</span><span class="sxs-lookup"><span data-stu-id="6b662-308">The unique Microsoft app ID for the bot as registered with the Bot Framework.</span></span> <span data-ttu-id="6b662-309">Dies kann mit der allgemeinen [App-ID identisch sein.](#id)</span><span class="sxs-lookup"><span data-stu-id="6b662-309">This may well be the same as the overall [app ID](#id).</span></span>|
|`needsChannelSelector`|<span data-ttu-id="6b662-310">Boolesch</span><span class="sxs-lookup"><span data-stu-id="6b662-310">Boolean</span></span>|||<span data-ttu-id="6b662-311">Beschreibt, ob der Bot einen Benutzerhinweis verwendet, um den Bot einem bestimmten Kanal hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="6b662-311">Describes whether or not the bot utilizes a user hint to add the bot to a specific channel.</span></span> <span data-ttu-id="6b662-312">Standard: `false`</span><span class="sxs-lookup"><span data-stu-id="6b662-312">Default: `false`</span></span>|
|`isNotificationOnly`|<span data-ttu-id="6b662-313">Boolesch</span><span class="sxs-lookup"><span data-stu-id="6b662-313">Boolean</span></span>|||<span data-ttu-id="6b662-314">Gibt an, ob ein Bot ein unidirektionaler Bot ausschließlich für Benachrichtigungen ist (im Gegensatz zu einem dialogorientierten Bot).</span><span class="sxs-lookup"><span data-stu-id="6b662-314">Indicates whether a bot is a one-way, notification-only bot, as opposed to a conversational bot.</span></span> <span data-ttu-id="6b662-315">Standard: `false`</span><span class="sxs-lookup"><span data-stu-id="6b662-315">Default: `false`</span></span>|
|`supportsFiles`|<span data-ttu-id="6b662-316">Boolesch</span><span class="sxs-lookup"><span data-stu-id="6b662-316">Boolean</span></span>|||<span data-ttu-id="6b662-317">Gibt an, ob der Bot die Möglichkeit zum Hochladen/Herunterladen von Dateien in persönliche Chats unterstützt.</span><span class="sxs-lookup"><span data-stu-id="6b662-317">Indicates whether the bot supports the ability to upload/download files in personal chat.</span></span> <span data-ttu-id="6b662-318">Standard: `false`</span><span class="sxs-lookup"><span data-stu-id="6b662-318">Default: `false`</span></span>|
|`scopes`|<span data-ttu-id="6b662-319">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="6b662-319">Array of enum</span></span>|<span data-ttu-id="6b662-320">3</span><span class="sxs-lookup"><span data-stu-id="6b662-320">3</span></span>|<span data-ttu-id="6b662-321">✔</span><span class="sxs-lookup"><span data-stu-id="6b662-321">✔</span></span>|<span data-ttu-id="6b662-322">Gibt an, ob der Bot eine Umgebung im Kontext eines Kanals in einem `team` oder Gruppenchat (`groupchat`) ist, oder aber eine Umgebung einzig für einen bestimmten Benutzer (`personal`).</span><span class="sxs-lookup"><span data-stu-id="6b662-322">Specifies whether the bot offers an experience in the context of a channel in a `team`, in a group chat (`groupchat`), or an experience scoped to an individual user alone (`personal`).</span></span> <span data-ttu-id="6b662-323">Diese Optionen sind nicht exklusiv.</span><span class="sxs-lookup"><span data-stu-id="6b662-323">These options are non-exclusive.</span></span>|

### <a name="botscommandlists"></a><span data-ttu-id="6b662-324">bots.commandLists</span><span class="sxs-lookup"><span data-stu-id="6b662-324">bots.commandLists</span></span>

<span data-ttu-id="6b662-325">Eine optionale Liste von Befehlen, die Ihr Bot Benutzern empfehlen kann.</span><span class="sxs-lookup"><span data-stu-id="6b662-325">An optional list of commands that your bot can recommend to users.</span></span> <span data-ttu-id="6b662-326">Das Objekt ist ein Array (maximal 2 Elemente) mit allen Elementen des Typs. Sie müssen eine separate Befehlsliste für jeden Bereich definieren, den `object` Ihr Bot unterstützt.</span><span class="sxs-lookup"><span data-stu-id="6b662-326">The object is an array (maximum of 2 elements) with all elements of type `object`; you must define a separate command list for each scope that your bot supports.</span></span> <span data-ttu-id="6b662-327">Weitere [Informationen finden Sie unter Bot-Menüs.](~/bots/how-to/create-a-bot-commands-menu.md)</span><span class="sxs-lookup"><span data-stu-id="6b662-327">See [Bot menus](~/bots/how-to/create-a-bot-commands-menu.md) for more information.</span></span>

|<span data-ttu-id="6b662-328">Name</span><span class="sxs-lookup"><span data-stu-id="6b662-328">Name</span></span>| <span data-ttu-id="6b662-329">Typ</span><span class="sxs-lookup"><span data-stu-id="6b662-329">Type</span></span>| <span data-ttu-id="6b662-330">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="6b662-330">Maximum size</span></span> | <span data-ttu-id="6b662-331">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="6b662-331">Required</span></span> | <span data-ttu-id="6b662-332">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="6b662-332">Description</span></span>|
|---|---|---|---|---|
|`items.scopes`|<span data-ttu-id="6b662-333">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="6b662-333">array of enum</span></span>|<span data-ttu-id="6b662-334">3</span><span class="sxs-lookup"><span data-stu-id="6b662-334">3</span></span>|<span data-ttu-id="6b662-335">✔</span><span class="sxs-lookup"><span data-stu-id="6b662-335">✔</span></span>|<span data-ttu-id="6b662-336">Gibt den Bereich an, für den die Befehlsliste gültig ist.</span><span class="sxs-lookup"><span data-stu-id="6b662-336">Specifies the scope for which the command list is valid.</span></span> <span data-ttu-id="6b662-337">Mögliche Optionen sind `team`, `personal` und `groupchat`.</span><span class="sxs-lookup"><span data-stu-id="6b662-337">Options are `team`, `personal`, and `groupchat`.</span></span>|
|`items.commands`|<span data-ttu-id="6b662-338">Array von Objekten</span><span class="sxs-lookup"><span data-stu-id="6b662-338">array of objects</span></span>|<span data-ttu-id="6b662-339">10  </span><span class="sxs-lookup"><span data-stu-id="6b662-339">10</span></span>|<span data-ttu-id="6b662-340">✔</span><span class="sxs-lookup"><span data-stu-id="6b662-340">✔</span></span>|<span data-ttu-id="6b662-341">Ein Array von Befehlen, die der Bot unterstützt:</span><span class="sxs-lookup"><span data-stu-id="6b662-341">An array of commands the bot supports:</span></span><br><span data-ttu-id="6b662-342">`title`: Name des Bot-Befehls (string, 32)</span><span class="sxs-lookup"><span data-stu-id="6b662-342">`title`: the bot command name (string, 32)</span></span><br><span data-ttu-id="6b662-343">`description`: einfache Beschreibung oder Beispiel für die Befehlssyntax und zugehörige Argumente (string, 128)</span><span class="sxs-lookup"><span data-stu-id="6b662-343">`description`: a simple description or example of the command syntax and its argument (string, 128)</span></span>|

## <a name="connectors"></a><span data-ttu-id="6b662-344">Connectors</span><span class="sxs-lookup"><span data-stu-id="6b662-344">connectors</span></span>

<span data-ttu-id="6b662-345">**Optional**</span><span class="sxs-lookup"><span data-stu-id="6b662-345">**Optional**</span></span>

<span data-ttu-id="6b662-346">Der `connectors` Block definiert einen Office 365 Connector für die App.</span><span class="sxs-lookup"><span data-stu-id="6b662-346">The `connectors` block defines an Office 365 Connector for the app.</span></span>

<span data-ttu-id="6b662-347">Das Objekt ist ein Array (maximal 1 Element) mit allen Elementen vom Typ `object` .</span><span class="sxs-lookup"><span data-stu-id="6b662-347">The object is an array (maximum of 1 element) with all elements of type `object`.</span></span> <span data-ttu-id="6b662-348">Dieser Block ist nur für Lösungen erforderlich, die einen Connector bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="6b662-348">This block is required only for solutions that provide a Connector.</span></span>

|<span data-ttu-id="6b662-349">Name</span><span class="sxs-lookup"><span data-stu-id="6b662-349">Name</span></span>| <span data-ttu-id="6b662-350">Typ</span><span class="sxs-lookup"><span data-stu-id="6b662-350">Type</span></span>| <span data-ttu-id="6b662-351">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="6b662-351">Maximum size</span></span> | <span data-ttu-id="6b662-352">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="6b662-352">Required</span></span> | <span data-ttu-id="6b662-353">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="6b662-353">Description</span></span>|
|---|---|---|---|---|
|`configurationUrl`|<span data-ttu-id="6b662-354">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="6b662-354">String</span></span>|<span data-ttu-id="6b662-355">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="6b662-355">2048 characters</span></span>|<span data-ttu-id="6b662-356">✔</span><span class="sxs-lookup"><span data-stu-id="6b662-356">✔</span></span>|<span data-ttu-id="6b662-357">Die https://-URL, die beim Konfigurieren des Connectors verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="6b662-357">The https:// URL to use when configuring the connector.</span></span>|
|`connectorId`|<span data-ttu-id="6b662-358">String</span><span class="sxs-lookup"><span data-stu-id="6b662-358">String</span></span>|<span data-ttu-id="6b662-359">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="6b662-359">64 characters</span></span>|<span data-ttu-id="6b662-360">✔</span><span class="sxs-lookup"><span data-stu-id="6b662-360">✔</span></span>|<span data-ttu-id="6b662-361">Ein eindeutiger Bezeichner für den Connector, der seiner ID im [Connectors Developer Dashboard entspricht.](https://aka.ms/connectorsdashboard)</span><span class="sxs-lookup"><span data-stu-id="6b662-361">A unique identifier for the Connector that matches its ID in the [Connectors Developer Dashboard](https://aka.ms/connectorsdashboard).</span></span>|
|`scopes`|<span data-ttu-id="6b662-362">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="6b662-362">Array of enum</span></span>|<span data-ttu-id="6b662-363">1</span><span class="sxs-lookup"><span data-stu-id="6b662-363">1</span></span>|<span data-ttu-id="6b662-364">✔</span><span class="sxs-lookup"><span data-stu-id="6b662-364">✔</span></span>|<span data-ttu-id="6b662-365">Gibt an, ob der Connector eine Benutzeroberfläche im Kontext eines Kanals in einem oder eine Benutzeroberfläche bietet, die auf einen einzelnen Benutzer `team` begrenzt ist ( `personal` ).</span><span class="sxs-lookup"><span data-stu-id="6b662-365">Specifies whether the Connector offers an experience in the context of a channel in a `team`, or an experience scoped to an individual user alone (`personal`).</span></span> <span data-ttu-id="6b662-366">Derzeit wird nur `team` der Bereich unterstützt.</span><span class="sxs-lookup"><span data-stu-id="6b662-366">Currently, only the `team` scope is supported.</span></span>|

## <a name="composeextensions"></a><span data-ttu-id="6b662-367">composeExtensions</span><span class="sxs-lookup"><span data-stu-id="6b662-367">composeExtensions</span></span>

<span data-ttu-id="6b662-368">**Optional**</span><span class="sxs-lookup"><span data-stu-id="6b662-368">**Optional**</span></span>

<span data-ttu-id="6b662-369">Definiert eine Messagingerweiterung für die App.</span><span class="sxs-lookup"><span data-stu-id="6b662-369">Defines a messaging extension for the app.</span></span>

> [!NOTE]
> <span data-ttu-id="6b662-370">Der Name des Features wurde im November 2017 von "Verfassenerweiterung" in "Messagingerweiterung" geändert, der Manifestname bleibt jedoch unverändert, damit vorhandene Erweiterungen weiterhin funktionieren.</span><span class="sxs-lookup"><span data-stu-id="6b662-370">The name of the feature was changed from "compose extension" to "messaging extension" in November, 2017, but the manifest name remains the same so that existing extensions continue to function.</span></span>

<span data-ttu-id="6b662-371">Das Objekt ist ein Array (maximal 1 Element) mit allen Elementen vom Typ `object` .</span><span class="sxs-lookup"><span data-stu-id="6b662-371">The object is an array (maximum of 1 element) with all elements of type `object`.</span></span> <span data-ttu-id="6b662-372">Dieser Block ist nur für Lösungen erforderlich, die eine Messagingerweiterung bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="6b662-372">This block is required only for solutions that provide a messaging extension.</span></span>

|<span data-ttu-id="6b662-373">Name</span><span class="sxs-lookup"><span data-stu-id="6b662-373">Name</span></span>| <span data-ttu-id="6b662-374">Typ</span><span class="sxs-lookup"><span data-stu-id="6b662-374">Type</span></span> | <span data-ttu-id="6b662-375">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="6b662-375">Maximum Size</span></span> | <span data-ttu-id="6b662-376">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="6b662-376">Required</span></span> | <span data-ttu-id="6b662-377">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="6b662-377">Description</span></span>|
|---|---|---|---|---|
|`botId`|<span data-ttu-id="6b662-378">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="6b662-378">String</span></span>|<span data-ttu-id="6b662-379">64</span><span class="sxs-lookup"><span data-stu-id="6b662-379">64</span></span>|<span data-ttu-id="6b662-380">✔</span><span class="sxs-lookup"><span data-stu-id="6b662-380">✔</span></span>|<span data-ttu-id="6b662-381">Die eindeutige Microsoft-App-ID für den Bot, der die Messagingerweiterung unterstützt, wie beim Bot Framework registriert.</span><span class="sxs-lookup"><span data-stu-id="6b662-381">The unique Microsoft app ID for the bot that backs the messaging extension, as registered with the Bot Framework.</span></span> <span data-ttu-id="6b662-382">Dies kann mit der allgemeinen [App-ID identisch sein.](#id)</span><span class="sxs-lookup"><span data-stu-id="6b662-382">This may well be the same as the overall [app ID](#id).</span></span>|
|`canUpdateConfiguration`|<span data-ttu-id="6b662-383">Boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="6b662-383">Boolean</span></span>|||<span data-ttu-id="6b662-384">Ein Wert, der angibt, ob die Konfiguration einer Messagingerweiterung vom Benutzer aktualisiert werden kann.</span><span class="sxs-lookup"><span data-stu-id="6b662-384">A value indicating whether the configuration of a messaging extension can be updated by the user.</span></span> <span data-ttu-id="6b662-385">Der Standardwert lautet `false`.</span><span class="sxs-lookup"><span data-stu-id="6b662-385">The default is `false`.</span></span>|
|`commands`|<span data-ttu-id="6b662-386">Array des Objekts</span><span class="sxs-lookup"><span data-stu-id="6b662-386">Array of object</span></span>|<span data-ttu-id="6b662-387">10  </span><span class="sxs-lookup"><span data-stu-id="6b662-387">10</span></span>|<span data-ttu-id="6b662-388">✔</span><span class="sxs-lookup"><span data-stu-id="6b662-388">✔</span></span>|<span data-ttu-id="6b662-389">Array von Befehlen, die von der Messagingerweiterung unterstützt werden</span><span class="sxs-lookup"><span data-stu-id="6b662-389">Array of commands the messaging extension supports</span></span>|

### <a name="composeextensionscommands"></a><span data-ttu-id="6b662-390">composeExtensions.commands</span><span class="sxs-lookup"><span data-stu-id="6b662-390">composeExtensions.commands</span></span>

<span data-ttu-id="6b662-391">Ihre Messagingerweiterung sollte einen oder mehrere Befehle deklarieren.</span><span class="sxs-lookup"><span data-stu-id="6b662-391">Your messaging extension should declare one or more commands.</span></span> <span data-ttu-id="6b662-392">Jeder Befehl wird in Microsoft Teams als potenzielle Interaktion vom benutzeroberflächenbasierten Einstiegspunkt angezeigt.</span><span class="sxs-lookup"><span data-stu-id="6b662-392">Each command appears in Microsoft Teams as a potential interaction from the UI-based entry point.</span></span> <span data-ttu-id="6b662-393">Es gibt maximal 10 Befehle.</span><span class="sxs-lookup"><span data-stu-id="6b662-393">There is a maximum of 10 commands.</span></span>

<span data-ttu-id="6b662-394">Jedes Befehlselement ist ein Objekt mit der folgenden Struktur:</span><span class="sxs-lookup"><span data-stu-id="6b662-394">Each command item is an object with the following structure:</span></span>

|<span data-ttu-id="6b662-395">Name</span><span class="sxs-lookup"><span data-stu-id="6b662-395">Name</span></span>| <span data-ttu-id="6b662-396">Typ</span><span class="sxs-lookup"><span data-stu-id="6b662-396">Type</span></span>| <span data-ttu-id="6b662-397">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="6b662-397">Maximum size</span></span> | <span data-ttu-id="6b662-398">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="6b662-398">Required</span></span> | <span data-ttu-id="6b662-399">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="6b662-399">Description</span></span>|
|---|---|---|---|---|
|`id`|<span data-ttu-id="6b662-400">String</span><span class="sxs-lookup"><span data-stu-id="6b662-400">String</span></span>|<span data-ttu-id="6b662-401">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="6b662-401">64 characters</span></span>|<span data-ttu-id="6b662-402">✔</span><span class="sxs-lookup"><span data-stu-id="6b662-402">✔</span></span>|<span data-ttu-id="6b662-403">Die ID für den Befehl</span><span class="sxs-lookup"><span data-stu-id="6b662-403">The ID for the command</span></span>|
|`type`|<span data-ttu-id="6b662-404">String</span><span class="sxs-lookup"><span data-stu-id="6b662-404">String</span></span>|<span data-ttu-id="6b662-405">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="6b662-405">64 characters</span></span>||<span data-ttu-id="6b662-406">Typ des Befehls.</span><span class="sxs-lookup"><span data-stu-id="6b662-406">Type of the command.</span></span> <span data-ttu-id="6b662-407">Einer oder `query` `action` .</span><span class="sxs-lookup"><span data-stu-id="6b662-407">One of `query` or `action`.</span></span> <span data-ttu-id="6b662-408">Standard: `query`</span><span class="sxs-lookup"><span data-stu-id="6b662-408">Default: `query`</span></span>|
|`title`|<span data-ttu-id="6b662-409">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="6b662-409">String</span></span>|<span data-ttu-id="6b662-410">32 Zeichen</span><span class="sxs-lookup"><span data-stu-id="6b662-410">32 characters</span></span>|<span data-ttu-id="6b662-411">✔</span><span class="sxs-lookup"><span data-stu-id="6b662-411">✔</span></span>|<span data-ttu-id="6b662-412">Der benutzerfreundliche Befehlsname</span><span class="sxs-lookup"><span data-stu-id="6b662-412">The user-friendly command name</span></span>|
|`description`|<span data-ttu-id="6b662-413">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="6b662-413">String</span></span>|<span data-ttu-id="6b662-414">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="6b662-414">128 characters</span></span>||<span data-ttu-id="6b662-415">Die Beschreibung, die Benutzern angezeigt wird, um den Zweck dieses Befehls anzugeben.</span><span class="sxs-lookup"><span data-stu-id="6b662-415">The description that appears to users to indicate the purpose of this command</span></span>|
|`initialRun`|<span data-ttu-id="6b662-416">Boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="6b662-416">Boolean</span></span>|||<span data-ttu-id="6b662-417">Ein boolescher Wert, der angibt, ob der Befehl zunächst ohne Parameter ausgeführt werden soll.</span><span class="sxs-lookup"><span data-stu-id="6b662-417">A Boolean value that indicates whether the command should be run initially with no parameters.</span></span> <span data-ttu-id="6b662-418">Standard: `false`</span><span class="sxs-lookup"><span data-stu-id="6b662-418">Default: `false`</span></span>|
|`context`|<span data-ttu-id="6b662-419">Array von Zeichenfolgen</span><span class="sxs-lookup"><span data-stu-id="6b662-419">Array of Strings</span></span>|<span data-ttu-id="6b662-420">3</span><span class="sxs-lookup"><span data-stu-id="6b662-420">3</span></span>||<span data-ttu-id="6b662-421">Definiert, von wo aus die Nachrichtenerweiterung aufgerufen werden kann.</span><span class="sxs-lookup"><span data-stu-id="6b662-421">Defines where the message extension can be invoked from.</span></span> <span data-ttu-id="6b662-422">Beliebige Kombination aus `compose` , `commandBox` , `message` .</span><span class="sxs-lookup"><span data-stu-id="6b662-422">Any combination of `compose`, `commandBox`, `message`.</span></span> <span data-ttu-id="6b662-423">Standard ist `["compose", "commandBox"]`</span><span class="sxs-lookup"><span data-stu-id="6b662-423">Default is `["compose", "commandBox"]`</span></span>|
|`fetchTask`|<span data-ttu-id="6b662-424">Boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="6b662-424">Boolean</span></span>|||<span data-ttu-id="6b662-425">Ein boolescher Wert, der angibt, ob das Aufgabenmodul dynamisch abgerufen werden soll</span><span class="sxs-lookup"><span data-stu-id="6b662-425">A boolean value that indicates if it should fetch the task module dynamically</span></span>|
|`taskInfo`|<span data-ttu-id="6b662-426">Object</span><span class="sxs-lookup"><span data-stu-id="6b662-426">Object</span></span>|||<span data-ttu-id="6b662-427">Angeben des Aufgabenmoduls, das beim Verwenden eines Befehls für die Messagingerweiterung vorladen werden soll</span><span class="sxs-lookup"><span data-stu-id="6b662-427">Specify the task module to preload when using a messaging extension command</span></span>|
|`taskInfo.title`|<span data-ttu-id="6b662-428">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="6b662-428">String</span></span>|<span data-ttu-id="6b662-429">64</span><span class="sxs-lookup"><span data-stu-id="6b662-429">64</span></span>||<span data-ttu-id="6b662-430">Titel des ersten Dialogfelds</span><span class="sxs-lookup"><span data-stu-id="6b662-430">Initial dialog title</span></span>|
|`taskInfo.width`|<span data-ttu-id="6b662-431">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="6b662-431">String</span></span>|||<span data-ttu-id="6b662-432">Dialogbreite – entweder eine Zahl in Pixel oder ein Standardlayout wie "groß", "mittel" oder "klein"</span><span class="sxs-lookup"><span data-stu-id="6b662-432">Dialog width - either a number in pixels or default layout such as 'large', 'medium', or 'small'</span></span>|
|`taskInfo.height`|<span data-ttu-id="6b662-433">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="6b662-433">String</span></span>|||<span data-ttu-id="6b662-434">Dialoghöhe – entweder eine Zahl in Pixel oder ein Standardlayout wie "groß", "mittel" oder "klein"</span><span class="sxs-lookup"><span data-stu-id="6b662-434">Dialog height - either a number in pixels or default layout such as 'large', 'medium', or 'small'</span></span>|
|`taskInfo.url`|<span data-ttu-id="6b662-435">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="6b662-435">String</span></span>|||<span data-ttu-id="6b662-436">Anfängliche Webview-URL</span><span class="sxs-lookup"><span data-stu-id="6b662-436">Initial webview URL</span></span>|
|`messageHandlers`|<span data-ttu-id="6b662-437">Array von Objekten</span><span class="sxs-lookup"><span data-stu-id="6b662-437">Array of Objects</span></span>|<span data-ttu-id="6b662-438">5 </span><span class="sxs-lookup"><span data-stu-id="6b662-438">5</span></span>||<span data-ttu-id="6b662-439">Eine Liste von Handlern, mit denen Apps aufgerufen werden können, wenn bestimmte Bedingungen erfüllt sind.</span><span class="sxs-lookup"><span data-stu-id="6b662-439">A list of handlers that allow apps to be invoked when certain conditions are met.</span></span> <span data-ttu-id="6b662-440">Domänen müssen auch in aufgeführt werden `validDomains`</span><span class="sxs-lookup"><span data-stu-id="6b662-440">Domains must also be listed in `validDomains`</span></span>|
|`messageHandlers.type`|<span data-ttu-id="6b662-441">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="6b662-441">String</span></span>|||<span data-ttu-id="6b662-442">Der Typ des Nachrichtenhandlers.</span><span class="sxs-lookup"><span data-stu-id="6b662-442">The type of message handler.</span></span> <span data-ttu-id="6b662-443">Muss `"link"` sein.</span><span class="sxs-lookup"><span data-stu-id="6b662-443">Must be `"link"`.</span></span>|
|`messageHandlers.value.domains`|<span data-ttu-id="6b662-444">Array von Zeichenfolgen</span><span class="sxs-lookup"><span data-stu-id="6b662-444">Array of Strings</span></span>|||<span data-ttu-id="6b662-445">Array von Domänen, für die der Linknachrichtenhandler registrieren kann.</span><span class="sxs-lookup"><span data-stu-id="6b662-445">Array of domains that the link message handler can register for.</span></span>|
|`parameters`|<span data-ttu-id="6b662-446">Array des Objekts</span><span class="sxs-lookup"><span data-stu-id="6b662-446">Array of object</span></span>|<span data-ttu-id="6b662-447">5 </span><span class="sxs-lookup"><span data-stu-id="6b662-447">5</span></span>|<span data-ttu-id="6b662-448">✔</span><span class="sxs-lookup"><span data-stu-id="6b662-448">✔</span></span>|<span data-ttu-id="6b662-449">Die Liste der Parameter, die der Befehl verwendet.</span><span class="sxs-lookup"><span data-stu-id="6b662-449">The list of parameters the command takes.</span></span> <span data-ttu-id="6b662-450">Minimum: 1; maximum: 5</span><span class="sxs-lookup"><span data-stu-id="6b662-450">Minimum: 1; maximum: 5</span></span>|
|`parameter.name`|<span data-ttu-id="6b662-451">String</span><span class="sxs-lookup"><span data-stu-id="6b662-451">String</span></span>|<span data-ttu-id="6b662-452">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="6b662-452">64 characters</span></span>|<span data-ttu-id="6b662-453">✔</span><span class="sxs-lookup"><span data-stu-id="6b662-453">✔</span></span>|<span data-ttu-id="6b662-454">Der Name des Parameters, wie er im Client angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="6b662-454">The name of the parameter as it appears in the client.</span></span> <span data-ttu-id="6b662-455">Dies ist in der Benutzeranforderung enthalten.</span><span class="sxs-lookup"><span data-stu-id="6b662-455">This is included in the user request.</span></span>|
|`parameter.title`|<span data-ttu-id="6b662-456">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="6b662-456">String</span></span>|<span data-ttu-id="6b662-457">32 Zeichen</span><span class="sxs-lookup"><span data-stu-id="6b662-457">32 characters</span></span>|<span data-ttu-id="6b662-458">✔</span><span class="sxs-lookup"><span data-stu-id="6b662-458">✔</span></span>|<span data-ttu-id="6b662-459">Benutzerfreundlicher Titel für den Parameter.</span><span class="sxs-lookup"><span data-stu-id="6b662-459">User-friendly title for the parameter.</span></span>|
|`parameter.description`|<span data-ttu-id="6b662-460">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="6b662-460">String</span></span>|<span data-ttu-id="6b662-461">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="6b662-461">128 characters</span></span>||<span data-ttu-id="6b662-462">Benutzerfreundliche Zeichenfolge, die den Zweck dieses Parameters beschreibt.</span><span class="sxs-lookup"><span data-stu-id="6b662-462">User-friendly string that describes this parameter’s purpose.</span></span>|
|`parameter.inputType`|<span data-ttu-id="6b662-463">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="6b662-463">String</span></span>|<span data-ttu-id="6b662-464">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="6b662-464">128 characters</span></span>||<span data-ttu-id="6b662-465">Definiert den Typ des Steuerelements, das in einem Aufgabenmodul für angezeigt `fetchTask: true` wird.</span><span class="sxs-lookup"><span data-stu-id="6b662-465">Defines the type of control displayed on a task module for `fetchTask: true`.</span></span> <span data-ttu-id="6b662-466">Einer von `text` , , , , , `textarea` `number` `date` `time` `toggle` , `choiceset`</span><span class="sxs-lookup"><span data-stu-id="6b662-466">One of `text`, `textarea`, `number`, `date`, `time`, `toggle`, `choiceset`</span></span>|
|`parameter.choices`|<span data-ttu-id="6b662-467">Array von Objekten</span><span class="sxs-lookup"><span data-stu-id="6b662-467">Array of Objects</span></span>|<span data-ttu-id="6b662-468">10  </span><span class="sxs-lookup"><span data-stu-id="6b662-468">10</span></span>||<span data-ttu-id="6b662-469">Die Auswahloptionen für `choiceset` .</span><span class="sxs-lookup"><span data-stu-id="6b662-469">The choice options for the `choiceset`.</span></span> <span data-ttu-id="6b662-470">Nur verwenden, `parameter.inputType` wenn dies der `choiceset`</span><span class="sxs-lookup"><span data-stu-id="6b662-470">Use only when `parameter.inputType` is `choiceset`</span></span>|
|`parameter.choices.title`|<span data-ttu-id="6b662-471">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="6b662-471">String</span></span>|<span data-ttu-id="6b662-472">128</span><span class="sxs-lookup"><span data-stu-id="6b662-472">128</span></span>||<span data-ttu-id="6b662-473">Titel der Wahl</span><span class="sxs-lookup"><span data-stu-id="6b662-473">Title of the choice</span></span>|
|`parameter.choices.value`|<span data-ttu-id="6b662-474">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="6b662-474">String</span></span>|<span data-ttu-id="6b662-475">512</span><span class="sxs-lookup"><span data-stu-id="6b662-475">512</span></span>||<span data-ttu-id="6b662-476">Wert der Wahl</span><span class="sxs-lookup"><span data-stu-id="6b662-476">Value of the choice</span></span>|

## <a name="permissions"></a><span data-ttu-id="6b662-477">Berechtigungen</span><span class="sxs-lookup"><span data-stu-id="6b662-477">permissions</span></span>

<span data-ttu-id="6b662-478">**Optional**</span><span class="sxs-lookup"><span data-stu-id="6b662-478">**Optional**</span></span>

<span data-ttu-id="6b662-479">Ein Array von dem angibt, welche Berechtigungen die App anfordert, wodurch Endbenutzer wissen, `string` wie die Erweiterung funktioniert.</span><span class="sxs-lookup"><span data-stu-id="6b662-479">An array of `string` which specifies which permissions the app requests, which lets end users know how the extension will perform.</span></span> <span data-ttu-id="6b662-480">Die folgenden Optionen sind nicht exklusiv:</span><span class="sxs-lookup"><span data-stu-id="6b662-480">The following options are non-exclusive:</span></span>

* <span data-ttu-id="6b662-481">`identity`&emsp;Erfordert Benutzeridentitätsinformationen</span><span class="sxs-lookup"><span data-stu-id="6b662-481">`identity` &emsp; Requires user identity information</span></span>
* <span data-ttu-id="6b662-482">`messageTeamMembers`&emsp;Erfordert die Berechtigung zum Senden von Direktnachrichten an Teammitglieder</span><span class="sxs-lookup"><span data-stu-id="6b662-482">`messageTeamMembers` &emsp; Requires permission to send direct messages to team members</span></span>

<span data-ttu-id="6b662-483">Wenn Sie diese Berechtigungen beim Aktualisieren Ihrer App ändern, wiederholen Ihre Benutzer den Zustimmungsprozess, wenn sie die aktualisierte App zum ersten Mal ausführen.</span><span class="sxs-lookup"><span data-stu-id="6b662-483">Changing these permissions when updating your app will cause your users to repeat the consent process the first time they run the updated app.</span></span>

## <a name="devicepermissions"></a><span data-ttu-id="6b662-484">devicePermissions</span><span class="sxs-lookup"><span data-stu-id="6b662-484">devicePermissions</span></span>

<span data-ttu-id="6b662-485">**Optional** Array von Zeichenfolgen</span><span class="sxs-lookup"><span data-stu-id="6b662-485">**Optional** Array of Strings</span></span>

<span data-ttu-id="6b662-486">Gibt die systemeigenen Features auf dem Gerät eines Benutzers an, auf die Ihre App möglicherweise Zugriff anfordern kann.</span><span class="sxs-lookup"><span data-stu-id="6b662-486">Specifies the native features on a user's device that your app may request access to.</span></span> <span data-ttu-id="6b662-487">Mögliche Optionen sind:</span><span class="sxs-lookup"><span data-stu-id="6b662-487">Options are:</span></span>

* `geolocation`
* `media`
* `notifications`
* `midi`
* `openExternal`

## <a name="validdomains"></a><span data-ttu-id="6b662-488">validDomains</span><span class="sxs-lookup"><span data-stu-id="6b662-488">validDomains</span></span>

<span data-ttu-id="6b662-489">**Optional**, mit **Ausnahme erforderlich,** sofern angegeben</span><span class="sxs-lookup"><span data-stu-id="6b662-489">**Optional**, except **Required** where noted</span></span>

<span data-ttu-id="6b662-490">Eine Liste der gültigen Domänen, von denen die App erwartet, dass alle Inhalte geladen werden.</span><span class="sxs-lookup"><span data-stu-id="6b662-490">A list of valid domains from which the app expects to load any content.</span></span> <span data-ttu-id="6b662-491">Domänenauflistungen können Platzhalter enthalten, z. B. `*.example.com` .</span><span class="sxs-lookup"><span data-stu-id="6b662-491">Domain listings can include wildcards, for example `*.example.com`.</span></span> <span data-ttu-id="6b662-492">Dies entspricht genau einem Abschnitt der Domäne. wenn Sie übereinstimmen müssen, `a.b.example.com` verwenden Sie `*.*.example.com` .</span><span class="sxs-lookup"><span data-stu-id="6b662-492">This matches exactly one segment of the domain; if you need to match `a.b.example.com` then use `*.*.example.com`.</span></span> <span data-ttu-id="6b662-493">Wenn Ihre Registerkartenkonfiguration oder Inhaltsbenutzeroberfläche neben der für die Registerkartenkonfiguration verwendeten Domäne zu einer anderen Domäne navigieren muss, muss diese Domäne hier angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="6b662-493">If your tab configuration or content UI needs to navigate to any other domain besides the one use for tab configuration, that domain must be specified here.</span></span>

<span data-ttu-id="6b662-494">Es ist **jedoch nicht** erforderlich, die Domänen von Identitätsanbietern, die Sie unterstützen möchten, in Ihre App zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="6b662-494">It is **not** necessary to include the domains of identity providers you want to support in your app, however.</span></span> <span data-ttu-id="6b662-495">Um sich z. B. mit einer Google-ID zu authentifizieren, müssen Sie zu accounts.google.com umleiten, sie sollten jedoch keine accounts.google.com in `validDomains[]` enthalten.</span><span class="sxs-lookup"><span data-stu-id="6b662-495">For example, to authenticate using a Google ID, it's necessary to redirect to accounts.google.com, but you should not include accounts.google.com in `validDomains[]`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6b662-496">Fügen Sie keine Domänen hinzu, die sich außerhalb Ihres Steuerelements befinden, weder direkt noch über Platzhalter.</span><span class="sxs-lookup"><span data-stu-id="6b662-496">Do not add domains that are outside your control, either directly or via wildcards.</span></span> <span data-ttu-id="6b662-497">Beispielsweise ist `yourapp.onmicrosoft.com` gültig, aber `*.onmicrosoft.com` nicht gültig.</span><span class="sxs-lookup"><span data-stu-id="6b662-497">For example, `yourapp.onmicrosoft.com` is valid, but `*.onmicrosoft.com` is not valid.</span></span>

<span data-ttu-id="6b662-498">Das Objekt ist ein Array mit allen Elementen des Typs `string` .</span><span class="sxs-lookup"><span data-stu-id="6b662-498">The object is an array with all elements of the type `string`.</span></span>

## <a name="webapplicationinfo"></a><span data-ttu-id="6b662-499">webApplicationInfo</span><span class="sxs-lookup"><span data-stu-id="6b662-499">webApplicationInfo</span></span>

<span data-ttu-id="6b662-500">**Optional**</span><span class="sxs-lookup"><span data-stu-id="6b662-500">**Optional**</span></span>

<span data-ttu-id="6b662-501">Geben Sie Ihre AAD-App-ID Graph, um Benutzern die nahtlose Anmeldung bei Ihrer AAD-App zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="6b662-501">Specify your AAD App ID and Graph information to help users seamlessly sign into your AAD app.</span></span>

|<span data-ttu-id="6b662-502">Name</span><span class="sxs-lookup"><span data-stu-id="6b662-502">Name</span></span>| <span data-ttu-id="6b662-503">Typ</span><span class="sxs-lookup"><span data-stu-id="6b662-503">Type</span></span>| <span data-ttu-id="6b662-504">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="6b662-504">Maximum size</span></span> | <span data-ttu-id="6b662-505">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="6b662-505">Required</span></span> | <span data-ttu-id="6b662-506">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="6b662-506">Description</span></span>|
|---|---|---|---|---|
|`id`|<span data-ttu-id="6b662-507">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="6b662-507">String</span></span>|<span data-ttu-id="6b662-508">36 Zeichen</span><span class="sxs-lookup"><span data-stu-id="6b662-508">36 characters</span></span>|<span data-ttu-id="6b662-509">✔</span><span class="sxs-lookup"><span data-stu-id="6b662-509">✔</span></span>|<span data-ttu-id="6b662-510">AAD-Anwendungs-ID der App.</span><span class="sxs-lookup"><span data-stu-id="6b662-510">AAD application id of the app.</span></span> <span data-ttu-id="6b662-511">Diese ID muss eine GUID sein.</span><span class="sxs-lookup"><span data-stu-id="6b662-511">This id must be a GUID.</span></span>|
|`resource`|<span data-ttu-id="6b662-512">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="6b662-512">String</span></span>|<span data-ttu-id="6b662-513">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="6b662-513">2048 characters</span></span>|<span data-ttu-id="6b662-514">✔</span><span class="sxs-lookup"><span data-stu-id="6b662-514">✔</span></span>|<span data-ttu-id="6b662-515">Ressourcen-URL der App zum Abrufen des Authentifizierungstokens für SSO.</span><span class="sxs-lookup"><span data-stu-id="6b662-515">Resource url of app for acquiring auth token for SSO.</span></span>|

## <a name="configurableproperties"></a><span data-ttu-id="6b662-516">configurableProperties</span><span class="sxs-lookup"><span data-stu-id="6b662-516">configurableProperties</span></span>

<span data-ttu-id="6b662-517">**Optional** – Array</span><span class="sxs-lookup"><span data-stu-id="6b662-517">**Optional** - array</span></span>

<span data-ttu-id="6b662-518">Der `configurableProperties` Block definiert die App-Eigenschaften, die Teams Administrator anpassen kann.</span><span class="sxs-lookup"><span data-stu-id="6b662-518">The `configurableProperties` block defines the app properties that Teams admin can customize.</span></span> <span data-ttu-id="6b662-519">Weitere Informationen finden Sie unter [Anpassen von Apps in Microsoft Teams.](/MicrosoftTeams/customize-apps)</span><span class="sxs-lookup"><span data-stu-id="6b662-519">For more information, see [customize apps in Microsoft Teams](/MicrosoftTeams/customize-apps).</span></span>

> [!NOTE]
> <span data-ttu-id="6b662-520">Mindestens eine Eigenschaft muss definiert werden.</span><span class="sxs-lookup"><span data-stu-id="6b662-520">A minimum of one property must be defined.</span></span> <span data-ttu-id="6b662-521">Sie können in diesem Block maximal neun Eigenschaften definieren.</span><span class="sxs-lookup"><span data-stu-id="6b662-521">You can define a maximum of nine properties in this block.</span></span>
> <span data-ttu-id="6b662-522">Als bewährte Methode müssen Sie Anpassungsrichtlinien für App-Benutzer und -Kunden bereitstellen, die sie beim Anpassen Ihrer App befolgen müssen.</span><span class="sxs-lookup"><span data-stu-id="6b662-522">As a best practice, you must provide customization guidelines for app users and customers to follow when customizing your app.</span></span> 

<span data-ttu-id="6b662-523">Sie können eine der folgenden Eigenschaften definieren:</span><span class="sxs-lookup"><span data-stu-id="6b662-523">You can define any of the following properties:</span></span>
* <span data-ttu-id="6b662-524">`name`: Ermöglicht administratoren das Ändern des Anzeigenamens der App.</span><span class="sxs-lookup"><span data-stu-id="6b662-524">`name`: Allows admin to change the app's display name.</span></span>
* <span data-ttu-id="6b662-525">`shortDescription`: Ermöglicht Administratoren das Ändern der Kurzbeschreibung der App.</span><span class="sxs-lookup"><span data-stu-id="6b662-525">`shortDescription`: Allows admin to change the app's short description.</span></span>
* <span data-ttu-id="6b662-526">`longDescription`: Ermöglicht Administratoren das Ändern der detaillierten Beschreibung der App.</span><span class="sxs-lookup"><span data-stu-id="6b662-526">`longDescription`: Allows admin to change the app's detailed description.</span></span>
* <span data-ttu-id="6b662-527">`smallImageUrl`: Es handelt sich `outline` um die Eigenschaft im Block des `icons` Manifests.</span><span class="sxs-lookup"><span data-stu-id="6b662-527">`smallImageUrl`: It is the `outline` property in the `icons` block of the manifest.</span></span>
* <span data-ttu-id="6b662-528">`largeImageUrl`: Es handelt sich `color` um die Eigenschaft im Block des `icons` Manifests.</span><span class="sxs-lookup"><span data-stu-id="6b662-528">`largeImageUrl`: It is the `color` property in the `icons` block of the manifest.</span></span>
* <span data-ttu-id="6b662-529">`accentColor`: Es ist die Farbe, die in Verbindung mit und als Hintergrund für Ihre Gliederungssymbole verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="6b662-529">`accentColor`: It is the color to use in conjunction with and as a background for your outline icons.</span></span>
* <span data-ttu-id="6b662-530">`websiteUrl`: Es ist die https://-URL zur Website des Entwicklers.</span><span class="sxs-lookup"><span data-stu-id="6b662-530">`websiteUrl`: It is the https:// URL to the developer's website.</span></span>
* <span data-ttu-id="6b662-531">`privacyUrl`: Es ist die https://-URL zur Datenschutzrichtlinie des Entwicklers.</span><span class="sxs-lookup"><span data-stu-id="6b662-531">`privacyUrl`: It is the https:// URL to the developer's privacy policy.</span></span>
* <span data-ttu-id="6b662-532">`termsOfUseUrl`: Es ist die https:// URL zu den Nutzungsbedingungen des Entwicklers.</span><span class="sxs-lookup"><span data-stu-id="6b662-532">`termsOfUseUrl`: It is the https:// URL to the developer's terms of use.</span></span>

## <a name="defaultinstallscope"></a><span data-ttu-id="6b662-533">defaultInstallScope</span><span class="sxs-lookup"><span data-stu-id="6b662-533">defaultInstallScope</span></span>

<span data-ttu-id="6b662-534">**Optional** – Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="6b662-534">**Optional** - string</span></span>

<span data-ttu-id="6b662-535">Gibt den für diese App definierten Installationsbereich standardmäßig an.</span><span class="sxs-lookup"><span data-stu-id="6b662-535">Specifies the install scope defined for this app by default.</span></span> <span data-ttu-id="6b662-536">Der definierte Bereich ist die Option, die auf der Schaltfläche angezeigt wird, wenn ein Benutzer versucht, die App hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="6b662-536">The defined scope will be the option displayed on the button when a user tries to add the app.</span></span> <span data-ttu-id="6b662-537">Mögliche Optionen sind:</span><span class="sxs-lookup"><span data-stu-id="6b662-537">Options are:</span></span>
* `personal`
* `team`
* `groupchat`
* `meetings`

## <a name="defaultgroupcapability"></a><span data-ttu-id="6b662-538">defaultGroupCapability</span><span class="sxs-lookup"><span data-stu-id="6b662-538">defaultGroupCapability</span></span>

<span data-ttu-id="6b662-539">**Optional** - -Objekt</span><span class="sxs-lookup"><span data-stu-id="6b662-539">**Optional** - object</span></span>

<span data-ttu-id="6b662-540">Wenn ein Gruppeninstallationsbereich ausgewählt ist, wird die Standardfunktion definiert, wenn der Benutzer die App installiert.</span><span class="sxs-lookup"><span data-stu-id="6b662-540">When a group install scope is selected, it will define the default capability when the user installs the app.</span></span> <span data-ttu-id="6b662-541">Mögliche Optionen sind:</span><span class="sxs-lookup"><span data-stu-id="6b662-541">Options are:</span></span>
* `team`
* `groupchat`
* `meetings`
 
|<span data-ttu-id="6b662-542">Name</span><span class="sxs-lookup"><span data-stu-id="6b662-542">Name</span></span>| <span data-ttu-id="6b662-543">Typ</span><span class="sxs-lookup"><span data-stu-id="6b662-543">Type</span></span>| <span data-ttu-id="6b662-544">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="6b662-544">Maximum size</span></span> | <span data-ttu-id="6b662-545">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="6b662-545">Required</span></span> | <span data-ttu-id="6b662-546">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="6b662-546">Description</span></span>|
|---|---|---|---|---|
|`team`|<span data-ttu-id="6b662-547">string</span><span class="sxs-lookup"><span data-stu-id="6b662-547">string</span></span>|||<span data-ttu-id="6b662-548">Wenn der ausgewählte Installationsbereich ausgewählt ist, gibt `team` dieses Feld die verfügbare Standardfunktion an.</span><span class="sxs-lookup"><span data-stu-id="6b662-548">When the install scope selected is `team`, this field specifies the default capability available.</span></span> <span data-ttu-id="6b662-549">Optionen: `tab` , `bot` oder `connector` .</span><span class="sxs-lookup"><span data-stu-id="6b662-549">Options: `tab`, `bot`, or `connector`.</span></span>|
|`groupchat`|<span data-ttu-id="6b662-550">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="6b662-550">string</span></span>|||<span data-ttu-id="6b662-551">Wenn der ausgewählte Installationsbereich ausgewählt ist, gibt `groupchat` dieses Feld die verfügbare Standardfunktion an.</span><span class="sxs-lookup"><span data-stu-id="6b662-551">When the install scope selected is `groupchat`, this field specifies the default capability available.</span></span> <span data-ttu-id="6b662-552">Optionen: `tab` , `bot` oder `connector` .</span><span class="sxs-lookup"><span data-stu-id="6b662-552">Options: `tab`, `bot`, or `connector`.</span></span>|
|`meetings`|<span data-ttu-id="6b662-553">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="6b662-553">string</span></span>|||<span data-ttu-id="6b662-554">Wenn der ausgewählte Installationsbereich ausgewählt ist, gibt `meetings` dieses Feld die verfügbare Standardfunktion an.</span><span class="sxs-lookup"><span data-stu-id="6b662-554">When the install scope selected is `meetings`, this field specifies the default capability available.</span></span> <span data-ttu-id="6b662-555">Optionen: `tab` , `bot` oder `connector` .</span><span class="sxs-lookup"><span data-stu-id="6b662-555">Options: `tab`, `bot`, or `connector`.</span></span>|

