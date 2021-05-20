---
title: Entwicklervorschau-Manifestschemareferenz
description: Beschreibt das Schema, das vom Manifest für Microsoft Teams unterstützt wird
ms.topic: reference
keywords: Teams-Manifestschema Entwicklervorschau
localization_priority: Normal
ms.date: 05/20/2019
ms.openlocfilehash: b52d52f96312dc2978844b07a0f7ebb1d817166d
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566705"
---
# <a name="developer-preview-manifest-schema-for-microsoft-teams"></a><span data-ttu-id="de383-104">Entwicklervorschaumanifestschema für Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="de383-104">Developer preview manifest schema for Microsoft Teams</span></span>

> [!NOTE]
> <span data-ttu-id="de383-105">Informationen zum Programm und zur Teilnahme an dem Programm finden Sie in [der Entwicklervorschau.](~/resources/dev-preview/developer-preview-intro.md)</span><span class="sxs-lookup"><span data-stu-id="de383-105">See [Developer Preview](~/resources/dev-preview/developer-preview-intro.md) for information on the program and how you can join.</span></span>
> <span data-ttu-id="de383-106">Wenn Sie die Entwicklervorschau nicht verwenden, sollten Sie diese Version des Manifests nicht verwenden.</span><span class="sxs-lookup"><span data-stu-id="de383-106">If you are not using the developer preview you should not be using this version of the manifest.</span></span> <span data-ttu-id="de383-107">Siehe [Referenz: Manifestschema für Microsoft Teams](~/resources/schema/manifest-schema.md) für die öffentliche Version des Manifests.</span><span class="sxs-lookup"><span data-stu-id="de383-107">See [Reference: Manifest schema for Microsoft Teams](~/resources/schema/manifest-schema.md) for the public version of the manifest.</span></span>

<span data-ttu-id="de383-108">Das Microsoft Teams-Manifest beschreibt, wie sich die App in das Microsoft Teams Produkt integriert.</span><span class="sxs-lookup"><span data-stu-id="de383-108">The Microsoft Teams manifest describes how the app integrates into the Microsoft Teams product.</span></span> <span data-ttu-id="de383-109">Das Manifest muss dem Schema entsprechen, das unter gehostet [`https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json`](https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json) wird.</span><span class="sxs-lookup"><span data-stu-id="de383-109">Your manifest must conform to the schema hosted at [`https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json`](https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json).</span></span>

<span data-ttu-id="de383-110">Weitere Informationen zu den verfügbaren Funktionen finden Sie unter: [Funktionen in der Öffentlichen Entwicklervorschau für Microsoft Teams](~/resources/dev-preview/developer-preview-features.md).</span><span class="sxs-lookup"><span data-stu-id="de383-110">For more information on the features available see: [Features in the Public Developer Preview for Microsoft Teams](~/resources/dev-preview/developer-preview-features.md).</span></span>

## <a name="sample-full-manifest"></a><span data-ttu-id="de383-111">Beispiel-Vollmanifest</span><span class="sxs-lookup"><span data-stu-id="de383-111">Sample full manifest</span></span>

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

<span data-ttu-id="de383-112">Das Schema definiert die folgenden Eigenschaften:</span><span class="sxs-lookup"><span data-stu-id="de383-112">The schema defines the following properties:</span></span>

## <a name="schema"></a><span data-ttu-id="de383-113">$schema</span><span class="sxs-lookup"><span data-stu-id="de383-113">$schema</span></span>

<span data-ttu-id="de383-114">*Optional, aber empfohlen* &ndash; Schnur</span><span class="sxs-lookup"><span data-stu-id="de383-114">*Optional, but recommended* &ndash; String</span></span>

<span data-ttu-id="de383-115">Die https:// URL, die auf das JSON-Schema für das Manifest verweist.</span><span class="sxs-lookup"><span data-stu-id="de383-115">The https:// URL referencing the JSON Schema for the manifest.</span></span>

## <a name="manifestversion"></a><span data-ttu-id="de383-116">manifestVersion</span><span class="sxs-lookup"><span data-stu-id="de383-116">manifestVersion</span></span>

<span data-ttu-id="de383-117">**Erforderlich** &ndash; Schnur</span><span class="sxs-lookup"><span data-stu-id="de383-117">**Required** &ndash; String</span></span>

<span data-ttu-id="de383-118">Die Version des Manifestschemas, das dieses Manifest verwendet.</span><span class="sxs-lookup"><span data-stu-id="de383-118">The version of the manifest schema this manifest is using.</span></span> <span data-ttu-id="de383-119">Es sollte "devPreview" sein.</span><span class="sxs-lookup"><span data-stu-id="de383-119">It should be "devPreview".</span></span>

## <a name="version"></a><span data-ttu-id="de383-120">Version</span><span class="sxs-lookup"><span data-stu-id="de383-120">version</span></span>

<span data-ttu-id="de383-121">**Erforderlich** &ndash; Schnur</span><span class="sxs-lookup"><span data-stu-id="de383-121">**Required** &ndash; String</span></span>

<span data-ttu-id="de383-122">Die Version der jeweiligen App.</span><span class="sxs-lookup"><span data-stu-id="de383-122">The version of the specific app.</span></span> <span data-ttu-id="de383-123">Wenn Sie etwas in Ihrem Manifest aktualisieren, muss die Version ebenfalls erhöht werden.</span><span class="sxs-lookup"><span data-stu-id="de383-123">If you update something in your manifest, the version must be incremented as well.</span></span> <span data-ttu-id="de383-124">Auf diese Weise wird bei der Installation des neuen Manifests das vorhandene überschrieben, und der Benutzer erhält die neue Funktionalität.</span><span class="sxs-lookup"><span data-stu-id="de383-124">This way, when the new manifest is installed, it will overwrite the existing one and the user will get the new functionality.</span></span> <span data-ttu-id="de383-125">Wenn diese App an den Store übermittelt wurde, muss das neue Manifest erneut übermittelt und erneut überprüft werden.</span><span class="sxs-lookup"><span data-stu-id="de383-125">If this app was submitted to the store, the new manifest will have to be re-submitted and re-validated.</span></span> <span data-ttu-id="de383-126">Dann erhalten Benutzer dieser App das neue aktualisierte Manifest automatisch in wenigen Stunden, nachdem es genehmigt wurde.</span><span class="sxs-lookup"><span data-stu-id="de383-126">Then, users of this app will get the new updated manifest automatically in a few hours, after it is approved.</span></span>

<span data-ttu-id="de383-127">Wenn sich die angeforderten Berechtigungen der App ändern, werden Benutzer aufgefordert, ein Upgrade durchzuführen und die App erneut zuzustimmen.</span><span class="sxs-lookup"><span data-stu-id="de383-127">If the app requested permissions change, users will be prompted to upgrade and re-consent to the app.</span></span>

<span data-ttu-id="de383-128">Diese Versionszeichenfolge muss dem [Semver-Standard](http://semver.org/) (MAJOR. kleiner. PATCH).</span><span class="sxs-lookup"><span data-stu-id="de383-128">This version string must follow the [semver](http://semver.org/) standard (MAJOR.MINOR.PATCH).</span></span>

## <a name="id"></a><span data-ttu-id="de383-129">id</span><span class="sxs-lookup"><span data-stu-id="de383-129">id</span></span>

<span data-ttu-id="de383-130">**Erforderlich** &ndash; Microsoft-App-ID</span><span class="sxs-lookup"><span data-stu-id="de383-130">**Required** &ndash; Microsoft app ID</span></span>

<span data-ttu-id="de383-131">Der eindeutige von Microsoft generierte Bezeichner für diese App.</span><span class="sxs-lookup"><span data-stu-id="de383-131">The unique Microsoft-generated identifier for this app.</span></span> <span data-ttu-id="de383-132">Wenn Sie einen Bot über die Microsoft Bot Framework registriert haben oder sich die Web-App Ihres Tabs bereits bei Microsoft anmeldet, sollten Sie bereits über eine ID verfügen und diese hier eingeben.</span><span class="sxs-lookup"><span data-stu-id="de383-132">If you have registered a bot via the Microsoft Bot Framework, or your tab's web app already signs in with Microsoft, you should already have an ID and should enter it here.</span></span> <span data-ttu-id="de383-133">Andernfalls sollten Sie eine neue ID im Microsoft Application Registration Portal ([Meine Anwendungen](https://apps.dev.microsoft.com)) generieren, hier eingeben und dann wiederverwenden, wenn Sie einen [Bot hinzufügen.](~/bots/how-to/create-a-bot-for-teams.md)</span><span class="sxs-lookup"><span data-stu-id="de383-133">Otherwise, you should generate a new ID at the Microsoft Application Registration Portal ([My Applications](https://apps.dev.microsoft.com)), enter it here, and then reuse it when you [add a bot](~/bots/how-to/create-a-bot-for-teams.md).</span></span>

## <a name="packagename"></a><span data-ttu-id="de383-134">Packagename</span><span class="sxs-lookup"><span data-stu-id="de383-134">packageName</span></span>

<span data-ttu-id="de383-135">**Erforderlich** &ndash; Schnur</span><span class="sxs-lookup"><span data-stu-id="de383-135">**Required** &ndash; String</span></span>

<span data-ttu-id="de383-136">Ein eindeutiger Bezeichner für diese App in umgekehrter Domänennotation; z. B. com.example.myapp.</span><span class="sxs-lookup"><span data-stu-id="de383-136">A unique identifier for this app in reverse domain notation; for example, com.example.myapp.</span></span>

## <a name="developer"></a><span data-ttu-id="de383-137">developer</span><span class="sxs-lookup"><span data-stu-id="de383-137">developer</span></span>

<span data-ttu-id="de383-138">**Required**</span><span class="sxs-lookup"><span data-stu-id="de383-138">**Required**</span></span>

<span data-ttu-id="de383-139">Gibt Informationen zu Ihrem Unternehmen an.</span><span class="sxs-lookup"><span data-stu-id="de383-139">Specifies information about your company.</span></span> <span data-ttu-id="de383-140">Bei Apps, die an AppSource übermittelt werden (früher Office Store), müssen diese Werte mit den Informationen in Ihrem AppSource-Eintrag übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="de383-140">For apps submitted to AppSource (formerly Office Store), these values must match the information in your AppSource entry.</span></span>

|<span data-ttu-id="de383-141">Name</span><span class="sxs-lookup"><span data-stu-id="de383-141">Name</span></span>| <span data-ttu-id="de383-142">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="de383-142">Maximum size</span></span> | <span data-ttu-id="de383-143">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="de383-143">Required</span></span> | <span data-ttu-id="de383-144">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="de383-144">Description</span></span>|
|---|---|---|---|
|`name`|<span data-ttu-id="de383-145">32 Zeichen</span><span class="sxs-lookup"><span data-stu-id="de383-145">32 characters</span></span>|<span data-ttu-id="de383-146">✔</span><span class="sxs-lookup"><span data-stu-id="de383-146">✔</span></span>|<span data-ttu-id="de383-147">Der Anzeigename für den Entwickler.</span><span class="sxs-lookup"><span data-stu-id="de383-147">The display name for the developer.</span></span>|
|`websiteUrl`|<span data-ttu-id="de383-148">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="de383-148">2048 characters</span></span>|<span data-ttu-id="de383-149">✔</span><span class="sxs-lookup"><span data-stu-id="de383-149">✔</span></span>|<span data-ttu-id="de383-150">Die https:// URL auf die Website des Entwicklers.</span><span class="sxs-lookup"><span data-stu-id="de383-150">The https:// URL to the developer's website.</span></span> <span data-ttu-id="de383-151">Dieser Link sollte Benutzer zu Ihrem Unternehmen oder Ihrer produktspezifischen Zielseite führen.</span><span class="sxs-lookup"><span data-stu-id="de383-151">This link should take users to your company or product-specific landing page.</span></span>|
|`privacyUrl`|<span data-ttu-id="de383-152">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="de383-152">2048 characters</span></span>|<span data-ttu-id="de383-153">✔</span><span class="sxs-lookup"><span data-stu-id="de383-153">✔</span></span>|<span data-ttu-id="de383-154">Die https:// URL zur Datenschutzrichtlinie des Entwicklers.</span><span class="sxs-lookup"><span data-stu-id="de383-154">The https:// URL to the developer's privacy policy.</span></span>|
|`termsOfUseUrl`|<span data-ttu-id="de383-155">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="de383-155">2048 characters</span></span>|<span data-ttu-id="de383-156">✔</span><span class="sxs-lookup"><span data-stu-id="de383-156">✔</span></span>|<span data-ttu-id="de383-157">Die https:// URL zu den Nutzungsbedingungen des Entwicklers.</span><span class="sxs-lookup"><span data-stu-id="de383-157">The https:// URL to the developer's terms of use.</span></span>|
|`mpnId`|<span data-ttu-id="de383-158">10 Zeichen</span><span class="sxs-lookup"><span data-stu-id="de383-158">10 characters</span></span>|<span data-ttu-id="de383-159">✔</span><span class="sxs-lookup"><span data-stu-id="de383-159">✔</span></span>|<span data-ttu-id="de383-160">**Optional** Die Microsoft Partner Network ID, die die Partnerorganisation identifiziert, die die App erstellen.</span><span class="sxs-lookup"><span data-stu-id="de383-160">**Optional** The Microsoft Partner Network ID that identifies the partner organization building the app.</span></span>|

## <a name="localizationinfo"></a><span data-ttu-id="de383-161">lokalisierungInfo</span><span class="sxs-lookup"><span data-stu-id="de383-161">localizationInfo</span></span>

<span data-ttu-id="de383-162">**Optional**</span><span class="sxs-lookup"><span data-stu-id="de383-162">**Optional**</span></span>

<span data-ttu-id="de383-163">Ermöglicht die Angabe einer Standardsprache sowie Zeiger auf zusätzliche Sprachdateien.</span><span class="sxs-lookup"><span data-stu-id="de383-163">Allows the specification of a default language, as well as pointers to additional language files.</span></span> <span data-ttu-id="de383-164">Siehe [Lokalisierung](~/concepts/build-and-test/apps-localization.md).</span><span class="sxs-lookup"><span data-stu-id="de383-164">See [localization](~/concepts/build-and-test/apps-localization.md).</span></span>

|<span data-ttu-id="de383-165">Name</span><span class="sxs-lookup"><span data-stu-id="de383-165">Name</span></span>| <span data-ttu-id="de383-166">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="de383-166">Maximum size</span></span> | <span data-ttu-id="de383-167">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="de383-167">Required</span></span> | <span data-ttu-id="de383-168">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="de383-168">Description</span></span>|
|---|---|---|---|
|`defaultLanguageTag`|<span data-ttu-id="de383-169">4 Zeichen</span><span class="sxs-lookup"><span data-stu-id="de383-169">4 characters</span></span>|<span data-ttu-id="de383-170">✔</span><span class="sxs-lookup"><span data-stu-id="de383-170">✔</span></span>|<span data-ttu-id="de383-171">Das Sprachtag der Zeichenfolgen in dieser Manifestdatei der obersten Ebene.</span><span class="sxs-lookup"><span data-stu-id="de383-171">The language tag of the strings in this top level manifest file.</span></span>|

### <a name="localizationinfoadditionallanguages"></a><span data-ttu-id="de383-172">lokalisierungInfo.additionalSprachen</span><span class="sxs-lookup"><span data-stu-id="de383-172">localizationInfo.additionalLanguages</span></span>

<span data-ttu-id="de383-173">Ein Array von Objekten, die zusätzliche Sprachübersetzungen angeben.</span><span class="sxs-lookup"><span data-stu-id="de383-173">An array of objects specifying additional language translations.</span></span>

|<span data-ttu-id="de383-174">Name</span><span class="sxs-lookup"><span data-stu-id="de383-174">Name</span></span>| <span data-ttu-id="de383-175">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="de383-175">Maximum size</span></span> | <span data-ttu-id="de383-176">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="de383-176">Required</span></span> | <span data-ttu-id="de383-177">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="de383-177">Description</span></span>|
|---|---|---|---|
|`languageTag`|<span data-ttu-id="de383-178">4 Zeichen</span><span class="sxs-lookup"><span data-stu-id="de383-178">4 characters</span></span>|<span data-ttu-id="de383-179">✔</span><span class="sxs-lookup"><span data-stu-id="de383-179">✔</span></span>|<span data-ttu-id="de383-180">Das Sprachtag der Zeichenfolgen in der bereitgestellten Datei.</span><span class="sxs-lookup"><span data-stu-id="de383-180">The language tag of the strings in the provided file.</span></span>|
|`file`|<span data-ttu-id="de383-181">4 Zeichen</span><span class="sxs-lookup"><span data-stu-id="de383-181">4 characters</span></span>|<span data-ttu-id="de383-182">✔</span><span class="sxs-lookup"><span data-stu-id="de383-182">✔</span></span>|<span data-ttu-id="de383-183">Ein relativer Dateipfad zu einer JSon-Datei, die die übersetzten Zeichenfolgen enthält.</span><span class="sxs-lookup"><span data-stu-id="de383-183">A relative file path to a the .json file containing the translated strings.</span></span>|

## <a name="name"></a><span data-ttu-id="de383-184">name</span><span class="sxs-lookup"><span data-stu-id="de383-184">name</span></span>

<span data-ttu-id="de383-185">**Required**</span><span class="sxs-lookup"><span data-stu-id="de383-185">**Required**</span></span>

<span data-ttu-id="de383-186">Der Name Ihrer App-Erfahrung, der Benutzern im Teams angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="de383-186">The name of your app experience, displayed to users in the Teams experience.</span></span> <span data-ttu-id="de383-187">Bei Apps, die an AppSource gesendet werden, müssen diese Werte mit den Informationen in Ihrem AppSource-Eintrag übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="de383-187">For apps submitted to AppSource, these values must match the information in your AppSource entry.</span></span> <span data-ttu-id="de383-188">Die Werte von `short` und sollten nicht die gleichen `full` sein.</span><span class="sxs-lookup"><span data-stu-id="de383-188">The values of `short` and `full` should not be the same.</span></span>

|<span data-ttu-id="de383-189">Name</span><span class="sxs-lookup"><span data-stu-id="de383-189">Name</span></span>| <span data-ttu-id="de383-190">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="de383-190">Maximum size</span></span> | <span data-ttu-id="de383-191">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="de383-191">Required</span></span> | <span data-ttu-id="de383-192">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="de383-192">Description</span></span>|
|---|---|---|---|
|`short`|<span data-ttu-id="de383-193">30 Zeichen</span><span class="sxs-lookup"><span data-stu-id="de383-193">30 characters</span></span>|<span data-ttu-id="de383-194">✔</span><span class="sxs-lookup"><span data-stu-id="de383-194">✔</span></span>|<span data-ttu-id="de383-195">Der kurze Anzeigename für die App.</span><span class="sxs-lookup"><span data-stu-id="de383-195">The short display name for the app.</span></span>|
|`full`|<span data-ttu-id="de383-196">100 Zeichen</span><span class="sxs-lookup"><span data-stu-id="de383-196">100 characters</span></span>||<span data-ttu-id="de383-197">Der vollständige Name der App, der verwendet wird, wenn der vollständige App-Name 30 Zeichen überschreitet.</span><span class="sxs-lookup"><span data-stu-id="de383-197">The full name of the app, used if the full app name exceeds 30 characters.</span></span>|

## <a name="description"></a><span data-ttu-id="de383-198">description</span><span class="sxs-lookup"><span data-stu-id="de383-198">description</span></span>

<span data-ttu-id="de383-199">**Required**</span><span class="sxs-lookup"><span data-stu-id="de383-199">**Required**</span></span>

<span data-ttu-id="de383-200">Beschreibt Ihre App für Benutzer.</span><span class="sxs-lookup"><span data-stu-id="de383-200">Describes your app to users.</span></span> <span data-ttu-id="de383-201">Bei Apps, die an AppSource gesendet werden, müssen diese Werte mit den Informationen in Ihrem AppSource-Eintrag übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="de383-201">For apps submitted to AppSource, these values must match the information in your AppSource entry.</span></span>

<span data-ttu-id="de383-202">Stellen Sie sicher, dass Ihre Beschreibung Ihre Erfahrung genau beschreibt und Informationen bereitstellt, die potenziellen Kunden helfen, ihre Erfahrung zu verstehen.</span><span class="sxs-lookup"><span data-stu-id="de383-202">Ensure that your description accurately describes your experience and provides information to help potential customers understand what your experience does.</span></span> <span data-ttu-id="de383-203">Sie sollten auch in der vollständigen Beschreibung notieren, ob ein externes Konto für die Verwendung erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="de383-203">You should also note, in the full description, if an external account is required for use.</span></span> <span data-ttu-id="de383-204">Die Werte von `short` und sollten nicht die gleichen `full` sein.</span><span class="sxs-lookup"><span data-stu-id="de383-204">The values of `short` and `full` should not be the same.</span></span>  <span data-ttu-id="de383-205">Ihre Kurzbeschreibung darf nicht innerhalb der langen Beschreibung wiederholt werden und darf keinen anderen App-Namen enthalten.</span><span class="sxs-lookup"><span data-stu-id="de383-205">Your short description must not be repeated within the long description and must not include any other app name.</span></span>

|<span data-ttu-id="de383-206">Name</span><span class="sxs-lookup"><span data-stu-id="de383-206">Name</span></span>| <span data-ttu-id="de383-207">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="de383-207">Maximum size</span></span> | <span data-ttu-id="de383-208">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="de383-208">Required</span></span> | <span data-ttu-id="de383-209">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="de383-209">Description</span></span>|
|---|---|---|---|
|`short`|<span data-ttu-id="de383-210">80 Zeichen</span><span class="sxs-lookup"><span data-stu-id="de383-210">80 characters</span></span>|<span data-ttu-id="de383-211">✔</span><span class="sxs-lookup"><span data-stu-id="de383-211">✔</span></span>|<span data-ttu-id="de383-212">Eine kurze Beschreibung Ihrer App-Erfahrung, die verwendet wird, wenn der Speicherplatz begrenzt ist.</span><span class="sxs-lookup"><span data-stu-id="de383-212">A short description of your app experience, used when space is limited.</span></span>|
|`full`|<span data-ttu-id="de383-213">4000 Zeichen</span><span class="sxs-lookup"><span data-stu-id="de383-213">4000 characters</span></span>|<span data-ttu-id="de383-214">✔</span><span class="sxs-lookup"><span data-stu-id="de383-214">✔</span></span>|<span data-ttu-id="de383-215">Die vollständige Beschreibung Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="de383-215">The full description of your app.</span></span>|

## <a name="icons"></a><span data-ttu-id="de383-216">Symbole</span><span class="sxs-lookup"><span data-stu-id="de383-216">icons</span></span>

<span data-ttu-id="de383-217">**Required**</span><span class="sxs-lookup"><span data-stu-id="de383-217">**Required**</span></span>

<span data-ttu-id="de383-218">Symbole, die in der Teams-App verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="de383-218">Icons used within the Teams app.</span></span> <span data-ttu-id="de383-219">Die Symboldateien müssen als Teil des Upload-Pakets enthalten sein.</span><span class="sxs-lookup"><span data-stu-id="de383-219">The icon files must be included as part of the upload package.</span></span>

|<span data-ttu-id="de383-220">Name</span><span class="sxs-lookup"><span data-stu-id="de383-220">Name</span></span>| <span data-ttu-id="de383-221">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="de383-221">Maximum size</span></span> | <span data-ttu-id="de383-222">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="de383-222">Required</span></span> | <span data-ttu-id="de383-223">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="de383-223">Description</span></span>|
|---|---|---|---|
|`outline`|<span data-ttu-id="de383-224">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="de383-224">2048 characters</span></span>|<span data-ttu-id="de383-225">✔</span><span class="sxs-lookup"><span data-stu-id="de383-225">✔</span></span>|<span data-ttu-id="de383-226">Ein relativer Dateipfad zu einem transparenten 32x32 PNG-Umrisssymbol.</span><span class="sxs-lookup"><span data-stu-id="de383-226">A relative file path to a transparent 32x32 PNG outline icon.</span></span>|
|`color`|<span data-ttu-id="de383-227">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="de383-227">2048 characters</span></span>|<span data-ttu-id="de383-228">✔</span><span class="sxs-lookup"><span data-stu-id="de383-228">✔</span></span>|<span data-ttu-id="de383-229">Ein relativer Dateipfad zu einem 192x192 PNG-Symbol in voller Farbe.</span><span class="sxs-lookup"><span data-stu-id="de383-229">A relative file path to a full color 192x192 PNG icon.</span></span>|

## <a name="accentcolor"></a><span data-ttu-id="de383-230">accentFarbe</span><span class="sxs-lookup"><span data-stu-id="de383-230">accentColor</span></span>

<span data-ttu-id="de383-231">**Erforderlich** &ndash; Schnur</span><span class="sxs-lookup"><span data-stu-id="de383-231">**Required** &ndash; String</span></span>

<span data-ttu-id="de383-232">Eine Farbe, die in Verbindung mit und als Hintergrund für Ihre Gliederungssymbole verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="de383-232">A color to use in conjunction with and as a background for your outline icons.</span></span>

<span data-ttu-id="de383-233">Der Wert muss ein gültiger HTML-Farbcode sein, der z. B. mit ''' `#4464ee` beginnt.</span><span class="sxs-lookup"><span data-stu-id="de383-233">The value must be a valid HTML color code starting with '#', for example `#4464ee`.</span></span>

## <a name="configurabletabs"></a><span data-ttu-id="de383-234">konfigurierbareTabs</span><span class="sxs-lookup"><span data-stu-id="de383-234">configurableTabs</span></span>

<span data-ttu-id="de383-235">**Optional**</span><span class="sxs-lookup"><span data-stu-id="de383-235">**Optional**</span></span>

<span data-ttu-id="de383-236">Wird verwendet, wenn Ihre App-Erfahrung über eine Teamkanal-Registerkarte verfügt, die eine zusätzliche Konfiguration erfordert, bevor sie hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="de383-236">Used when your app experience has a team channel tab experience that requires extra configuration before it is added.</span></span> <span data-ttu-id="de383-237">Konfigurierbare Registerkarten werden nur im Teamsbereich unterstützt, und derzeit wird nur eine Registerkarte pro App unterstützt.</span><span class="sxs-lookup"><span data-stu-id="de383-237">Configurable tabs are supported only in the teams scope, and currently only one tab per app is supported.</span></span>

<span data-ttu-id="de383-238">Das Objekt ist ein Array mit allen Elementen des Typs `object` .</span><span class="sxs-lookup"><span data-stu-id="de383-238">The object is an array with all elements of the type `object`.</span></span> <span data-ttu-id="de383-239">Dieser Block ist nur für Lösungen erforderlich, die eine konfigurierbare Kanalregisterkartenlösung bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="de383-239">This block is required only for solutions that provide a configurable channel tab solution.</span></span>

|<span data-ttu-id="de383-240">Name</span><span class="sxs-lookup"><span data-stu-id="de383-240">Name</span></span>| <span data-ttu-id="de383-241">Typ</span><span class="sxs-lookup"><span data-stu-id="de383-241">Type</span></span>| <span data-ttu-id="de383-242">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="de383-242">Maximum size</span></span> | <span data-ttu-id="de383-243">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="de383-243">Required</span></span> | <span data-ttu-id="de383-244">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="de383-244">Description</span></span>|
|---|---|---|---|---|
|`configurationUrl`|<span data-ttu-id="de383-245">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="de383-245">String</span></span>|<span data-ttu-id="de383-246">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="de383-246">2048 characters</span></span>|<span data-ttu-id="de383-247">✔</span><span class="sxs-lookup"><span data-stu-id="de383-247">✔</span></span>|<span data-ttu-id="de383-248">Die https:// URL, die beim Konfigurieren der Registerkarte verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="de383-248">The https:// URL to use when configuring the tab.</span></span>|
|`canUpdateConfiguration`|<span data-ttu-id="de383-249">Boolesch</span><span class="sxs-lookup"><span data-stu-id="de383-249">Boolean</span></span>|||<span data-ttu-id="de383-250">Ein Wert, der angibt, ob eine Instanz der Registerkartenkonfiguration vom Benutzer nach der Erstellung aktualisiert werden kann.</span><span class="sxs-lookup"><span data-stu-id="de383-250">A value indicating whether an instance of the tab's configuration can be updated by the user after creation.</span></span> <span data-ttu-id="de383-251">Standard: `true`</span><span class="sxs-lookup"><span data-stu-id="de383-251">Default: `true`</span></span>|
|`scopes`|<span data-ttu-id="de383-252">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="de383-252">Array of enum</span></span>|<span data-ttu-id="de383-253">1</span><span class="sxs-lookup"><span data-stu-id="de383-253">1</span></span>|<span data-ttu-id="de383-254">✔</span><span class="sxs-lookup"><span data-stu-id="de383-254">✔</span></span>|<span data-ttu-id="de383-255">Derzeit unterstützen konfigurierbare Registerkarten nur die `team` `groupchat` und-Bereiche.</span><span class="sxs-lookup"><span data-stu-id="de383-255">Currently, configurable tabs support only the `team` and `groupchat` scopes.</span></span> |
|`sharePointPreviewImage`|<span data-ttu-id="de383-256">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="de383-256">String</span></span>|<span data-ttu-id="de383-257">2048</span><span class="sxs-lookup"><span data-stu-id="de383-257">2048</span></span>||<span data-ttu-id="de383-258">Ein relativer Dateipfad zu einem Registerkartenvorschaubild zur Verwendung in SharePoint.</span><span class="sxs-lookup"><span data-stu-id="de383-258">A relative file path to a tab preview image for use in SharePoint.</span></span> <span data-ttu-id="de383-259">Größe 1024x768.</span><span class="sxs-lookup"><span data-stu-id="de383-259">Size 1024x768.</span></span> |
|`supportedSharePointHosts`|<span data-ttu-id="de383-260">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="de383-260">Array of enum</span></span>|<span data-ttu-id="de383-261">1</span><span class="sxs-lookup"><span data-stu-id="de383-261">1</span></span>||<span data-ttu-id="de383-262">Definiert, wie Ihre Registerkarte in SharePoint zur Verfügung gestellt wird.</span><span class="sxs-lookup"><span data-stu-id="de383-262">Defines how your tab will be made available in SharePoint.</span></span> <span data-ttu-id="de383-263">Optionen sind `sharePointFullPage` und `sharePointWebPart`</span><span class="sxs-lookup"><span data-stu-id="de383-263">Options are `sharePointFullPage` and `sharePointWebPart`</span></span> |

## <a name="statictabs"></a><span data-ttu-id="de383-264">staticTabs</span><span class="sxs-lookup"><span data-stu-id="de383-264">staticTabs</span></span>

<span data-ttu-id="de383-265">**Optional**</span><span class="sxs-lookup"><span data-stu-id="de383-265">**Optional**</span></span>

<span data-ttu-id="de383-266">Definiert eine Reihe von Registerkarten, die standardmäßig "angeheftet" werden können, ohne dass der Benutzer sie manuell hinzufügt.</span><span class="sxs-lookup"><span data-stu-id="de383-266">Defines a set of tabs that can be "pinned" by default, without the user adding them manually.</span></span> <span data-ttu-id="de383-267">Statische Registerkarten, die im `personal` Gültigkeitsbereich deklariert sind, werden immer an die persönliche Erfahrung der App angeheftet.</span><span class="sxs-lookup"><span data-stu-id="de383-267">Static tabs declared in `personal` scope are always pinned to the app's personal experience.</span></span> <span data-ttu-id="de383-268">Statische Registerkarten, die im Bereich deklariert `team` sind, werden derzeit nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="de383-268">Static tabs declared in the `team` scope are currently not supported.</span></span>

<span data-ttu-id="de383-269">Das Objekt ist ein Array (maximal 16 Elemente) mit allen Elementen des Typs `object` .</span><span class="sxs-lookup"><span data-stu-id="de383-269">The object is an array (maximum of 16 elements) with all elements of the type `object`.</span></span> <span data-ttu-id="de383-270">Dieser Block ist nur für Lösungen erforderlich, die eine statische Registerkartenlösung bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="de383-270">This block is required only for solutions that provide a static tab solution.</span></span>

|<span data-ttu-id="de383-271">Name</span><span class="sxs-lookup"><span data-stu-id="de383-271">Name</span></span>| <span data-ttu-id="de383-272">Typ</span><span class="sxs-lookup"><span data-stu-id="de383-272">Type</span></span>| <span data-ttu-id="de383-273">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="de383-273">Maximum size</span></span> | <span data-ttu-id="de383-274">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="de383-274">Required</span></span> | <span data-ttu-id="de383-275">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="de383-275">Description</span></span>|
|---|---|---|---|---|
|`entityId`|<span data-ttu-id="de383-276">String</span><span class="sxs-lookup"><span data-stu-id="de383-276">String</span></span>|<span data-ttu-id="de383-277">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="de383-277">64 characters</span></span>|<span data-ttu-id="de383-278">✔</span><span class="sxs-lookup"><span data-stu-id="de383-278">✔</span></span>|<span data-ttu-id="de383-279">Ein eindeutiger Bezeichner für die Entität, die auf der Registerkarte angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="de383-279">A unique identifier for the entity that the tab displays.</span></span>|
|`name`|<span data-ttu-id="de383-280">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="de383-280">String</span></span>|<span data-ttu-id="de383-281">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="de383-281">128 characters</span></span>|<span data-ttu-id="de383-282">✔</span><span class="sxs-lookup"><span data-stu-id="de383-282">✔</span></span>|<span data-ttu-id="de383-283">Der Anzeigename der Registerkarte in der Kanalschnittstelle.</span><span class="sxs-lookup"><span data-stu-id="de383-283">The display name of the tab in the channel interface.</span></span>|
|`contentUrl`|<span data-ttu-id="de383-284">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="de383-284">String</span></span>|<span data-ttu-id="de383-285">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="de383-285">2048 characters</span></span>|<span data-ttu-id="de383-286">✔</span><span class="sxs-lookup"><span data-stu-id="de383-286">✔</span></span>|<span data-ttu-id="de383-287">Die https:// URL, die auf die Entitätsbenutzeroberfläche verweist, die im Teams-Canvas angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="de383-287">The https:// URL that points to the entity UI to be displayed in the Teams canvas.</span></span>|
|`websiteUrl`|<span data-ttu-id="de383-288">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="de383-288">String</span></span>|<span data-ttu-id="de383-289">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="de383-289">2048 characters</span></span>||<span data-ttu-id="de383-290">Die https:// URL, auf die sie zeigen sollen, wenn ein Benutzer sich für die Anzeige in einem Browser entscheidet.</span><span class="sxs-lookup"><span data-stu-id="de383-290">The https:// URL to point at if a user opts to view in a browser.</span></span>|
|`scopes`|<span data-ttu-id="de383-291">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="de383-291">Array of enum</span></span>|<span data-ttu-id="de383-292">1</span><span class="sxs-lookup"><span data-stu-id="de383-292">1</span></span>|<span data-ttu-id="de383-293">✔</span><span class="sxs-lookup"><span data-stu-id="de383-293">✔</span></span>|<span data-ttu-id="de383-294">Derzeit unterstützen statische Registerkarten nur den `personal` Bereich, d. h., er kann nur als Teil der persönlichen Erfahrung bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="de383-294">Currently, static tabs support only the `personal` scope, which means it can be provisioned only as part of the personal experience.</span></span>|

## <a name="bots"></a><span data-ttu-id="de383-295">Bots</span><span class="sxs-lookup"><span data-stu-id="de383-295">bots</span></span>

<span data-ttu-id="de383-296">**Optional**</span><span class="sxs-lookup"><span data-stu-id="de383-296">**Optional**</span></span>

<span data-ttu-id="de383-297">Definiert eine Bot-Lösung zusammen mit optionalen Informationen wie Standardbefehlseigenschaften.</span><span class="sxs-lookup"><span data-stu-id="de383-297">Defines a bot solution, along with optional information such as default command properties.</span></span>

<span data-ttu-id="de383-298">Das Objekt ist ein Array (maximal nur 1 Element &mdash; ist derzeit nur ein Bot pro App erlaubt) mit allen Elementen des Typs `object` .</span><span class="sxs-lookup"><span data-stu-id="de383-298">The object is an array (maximum of only 1 element&mdash;currently only one bot is allowed per app) with all elements of the type `object`.</span></span> <span data-ttu-id="de383-299">Dieser Block ist nur für Lösungen erforderlich, die ein Bot-Erlebnis bieten.</span><span class="sxs-lookup"><span data-stu-id="de383-299">This block is required only for solutions that provide a bot experience.</span></span>

|<span data-ttu-id="de383-300">Name</span><span class="sxs-lookup"><span data-stu-id="de383-300">Name</span></span>| <span data-ttu-id="de383-301">Typ</span><span class="sxs-lookup"><span data-stu-id="de383-301">Type</span></span>| <span data-ttu-id="de383-302">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="de383-302">Maximum size</span></span> | <span data-ttu-id="de383-303">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="de383-303">Required</span></span> | <span data-ttu-id="de383-304">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="de383-304">Description</span></span>|
|---|---|---|---|---|
|`botId`|<span data-ttu-id="de383-305">String</span><span class="sxs-lookup"><span data-stu-id="de383-305">String</span></span>|<span data-ttu-id="de383-306">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="de383-306">64 characters</span></span>|<span data-ttu-id="de383-307">✔</span><span class="sxs-lookup"><span data-stu-id="de383-307">✔</span></span>|<span data-ttu-id="de383-308">Die eindeutige Microsoft-App-ID für den Bot, wie bei Bot Framework registriert.</span><span class="sxs-lookup"><span data-stu-id="de383-308">The unique Microsoft app ID for the bot as registered with the Bot Framework.</span></span> <span data-ttu-id="de383-309">Dies kann durchaus mit der gesamten [App-ID](#id)identisch sein.</span><span class="sxs-lookup"><span data-stu-id="de383-309">This may well be the same as the overall [app ID](#id).</span></span>|
|`needsChannelSelector`|<span data-ttu-id="de383-310">Boolesch</span><span class="sxs-lookup"><span data-stu-id="de383-310">Boolean</span></span>|||<span data-ttu-id="de383-311">Beschreibt, ob der Bot einen Benutzerhinweis verwendet, um den Bot einem bestimmten Kanal hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="de383-311">Describes whether or not the bot utilizes a user hint to add the bot to a specific channel.</span></span> <span data-ttu-id="de383-312">Standard: `false`</span><span class="sxs-lookup"><span data-stu-id="de383-312">Default: `false`</span></span>|
|`isNotificationOnly`|<span data-ttu-id="de383-313">Boolesch</span><span class="sxs-lookup"><span data-stu-id="de383-313">Boolean</span></span>|||<span data-ttu-id="de383-314">Gibt an, ob ein Bot ein unidirektionaler Bot ausschließlich für Benachrichtigungen ist (im Gegensatz zu einem dialogorientierten Bot).</span><span class="sxs-lookup"><span data-stu-id="de383-314">Indicates whether a bot is a one-way, notification-only bot, as opposed to a conversational bot.</span></span> <span data-ttu-id="de383-315">Standard: `false`</span><span class="sxs-lookup"><span data-stu-id="de383-315">Default: `false`</span></span>|
|`supportsFiles`|<span data-ttu-id="de383-316">Boolesch</span><span class="sxs-lookup"><span data-stu-id="de383-316">Boolean</span></span>|||<span data-ttu-id="de383-317">Gibt an, ob der Bot die Möglichkeit zum Hochladen/Herunterladen von Dateien in persönliche Chats unterstützt.</span><span class="sxs-lookup"><span data-stu-id="de383-317">Indicates whether the bot supports the ability to upload/download files in personal chat.</span></span> <span data-ttu-id="de383-318">Standard: `false`</span><span class="sxs-lookup"><span data-stu-id="de383-318">Default: `false`</span></span>|
|`scopes`|<span data-ttu-id="de383-319">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="de383-319">Array of enum</span></span>|<span data-ttu-id="de383-320">3</span><span class="sxs-lookup"><span data-stu-id="de383-320">3</span></span>|<span data-ttu-id="de383-321">✔</span><span class="sxs-lookup"><span data-stu-id="de383-321">✔</span></span>|<span data-ttu-id="de383-322">Gibt an, ob der Bot eine Umgebung im Kontext eines Kanals in einem `team` oder Gruppenchat (`groupchat`) ist, oder aber eine Umgebung einzig für einen bestimmten Benutzer (`personal`).</span><span class="sxs-lookup"><span data-stu-id="de383-322">Specifies whether the bot offers an experience in the context of a channel in a `team`, in a group chat (`groupchat`), or an experience scoped to an individual user alone (`personal`).</span></span> <span data-ttu-id="de383-323">Diese Optionen sind nicht exklusiv.</span><span class="sxs-lookup"><span data-stu-id="de383-323">These options are non-exclusive.</span></span>|

### <a name="botscommandlists"></a><span data-ttu-id="de383-324">bots.commandListen</span><span class="sxs-lookup"><span data-stu-id="de383-324">bots.commandLists</span></span>

<span data-ttu-id="de383-325">Eine optionale Liste von Befehlen, die Ihr Bot Benutzern empfehlen kann.</span><span class="sxs-lookup"><span data-stu-id="de383-325">An optional list of commands that your bot can recommend to users.</span></span> <span data-ttu-id="de383-326">Das Objekt ist ein Array (maximal 2 Elemente) mit allen Elementen des `object` Typs; Sie müssen eine separate Befehlsliste für jeden Bereich definieren, den Ihr Bot unterstützt.</span><span class="sxs-lookup"><span data-stu-id="de383-326">The object is an array (maximum of 2 elements) with all elements of type `object`; you must define a separate command list for each scope that your bot supports.</span></span> <span data-ttu-id="de383-327">Weitere Informationen finden Sie unter [Bot-Menüs](~/bots/how-to/create-a-bot-commands-menu.md).</span><span class="sxs-lookup"><span data-stu-id="de383-327">For more information, see [Bot menus](~/bots/how-to/create-a-bot-commands-menu.md).</span></span>

|<span data-ttu-id="de383-328">Name</span><span class="sxs-lookup"><span data-stu-id="de383-328">Name</span></span>| <span data-ttu-id="de383-329">Typ</span><span class="sxs-lookup"><span data-stu-id="de383-329">Type</span></span>| <span data-ttu-id="de383-330">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="de383-330">Maximum size</span></span> | <span data-ttu-id="de383-331">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="de383-331">Required</span></span> | <span data-ttu-id="de383-332">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="de383-332">Description</span></span>|
|---|---|---|---|---|
|`items.scopes`|<span data-ttu-id="de383-333">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="de383-333">array of enum</span></span>|<span data-ttu-id="de383-334">3</span><span class="sxs-lookup"><span data-stu-id="de383-334">3</span></span>|<span data-ttu-id="de383-335">✔</span><span class="sxs-lookup"><span data-stu-id="de383-335">✔</span></span>|<span data-ttu-id="de383-336">Gibt den Bereich an, für den die Befehlsliste gültig ist.</span><span class="sxs-lookup"><span data-stu-id="de383-336">Specifies the scope for which the command list is valid.</span></span> <span data-ttu-id="de383-337">Mögliche Optionen sind `team`, `personal` und `groupchat`.</span><span class="sxs-lookup"><span data-stu-id="de383-337">Options are `team`, `personal`, and `groupchat`.</span></span>|
|`items.commands`|<span data-ttu-id="de383-338">Array von Objekten</span><span class="sxs-lookup"><span data-stu-id="de383-338">array of objects</span></span>|<span data-ttu-id="de383-339">10</span><span class="sxs-lookup"><span data-stu-id="de383-339">10</span></span>|<span data-ttu-id="de383-340">✔</span><span class="sxs-lookup"><span data-stu-id="de383-340">✔</span></span>|<span data-ttu-id="de383-341">Ein Array von Befehlen, die der Bot unterstützt:</span><span class="sxs-lookup"><span data-stu-id="de383-341">An array of commands the bot supports:</span></span><br><span data-ttu-id="de383-342">`title`: der Bot-Befehlsname (Zeichenfolge, 32).</span><span class="sxs-lookup"><span data-stu-id="de383-342">`title`: the bot command name (string, 32).</span></span><br><span data-ttu-id="de383-343">`description`: eine einfache Beschreibung oder ein Beispiel für die Befehlssyntax und ihr Argument (Zeichenfolge, 128).</span><span class="sxs-lookup"><span data-stu-id="de383-343">`description`: a simple description or example of the command syntax and its argument (string, 128).</span></span>|

## <a name="connectors"></a><span data-ttu-id="de383-344">Steckverbinder</span><span class="sxs-lookup"><span data-stu-id="de383-344">connectors</span></span>

<span data-ttu-id="de383-345">**Optional**</span><span class="sxs-lookup"><span data-stu-id="de383-345">**Optional**</span></span>

<span data-ttu-id="de383-346">Der `connectors` Block definiert einen Office 365 Connector für die App.</span><span class="sxs-lookup"><span data-stu-id="de383-346">The `connectors` block defines an Office 365 Connector for the app.</span></span>

<span data-ttu-id="de383-347">Das Objekt ist ein Array (maximal 1 Element) mit allen Elementen des Typs `object` .</span><span class="sxs-lookup"><span data-stu-id="de383-347">The object is an array (maximum of 1 element) with all elements of type `object`.</span></span> <span data-ttu-id="de383-348">Dieser Block ist nur für Lösungen erforderlich, die einen Connector bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="de383-348">This block is required only for solutions that provide a Connector.</span></span>

|<span data-ttu-id="de383-349">Name</span><span class="sxs-lookup"><span data-stu-id="de383-349">Name</span></span>| <span data-ttu-id="de383-350">Typ</span><span class="sxs-lookup"><span data-stu-id="de383-350">Type</span></span>| <span data-ttu-id="de383-351">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="de383-351">Maximum size</span></span> | <span data-ttu-id="de383-352">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="de383-352">Required</span></span> | <span data-ttu-id="de383-353">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="de383-353">Description</span></span>|
|---|---|---|---|---|
|`configurationUrl`|<span data-ttu-id="de383-354">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="de383-354">String</span></span>|<span data-ttu-id="de383-355">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="de383-355">2048 characters</span></span>|<span data-ttu-id="de383-356">✔</span><span class="sxs-lookup"><span data-stu-id="de383-356">✔</span></span>|<span data-ttu-id="de383-357">Die https:// URL, die beim Konfigurieren des Connectors verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="de383-357">The https:// URL to use when configuring the connector.</span></span>|
|`connectorId`|<span data-ttu-id="de383-358">String</span><span class="sxs-lookup"><span data-stu-id="de383-358">String</span></span>|<span data-ttu-id="de383-359">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="de383-359">64 characters</span></span>|<span data-ttu-id="de383-360">✔</span><span class="sxs-lookup"><span data-stu-id="de383-360">✔</span></span>|<span data-ttu-id="de383-361">Ein eindeutiger Bezeichner für den Connector, der mit seiner ID im [Connectors Developer Dashboard](https://aka.ms/connectorsdashboard)übereinstimmt.</span><span class="sxs-lookup"><span data-stu-id="de383-361">A unique identifier for the Connector that matches its ID in the [Connectors Developer Dashboard](https://aka.ms/connectorsdashboard).</span></span>|
|`scopes`|<span data-ttu-id="de383-362">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="de383-362">Array of enum</span></span>|<span data-ttu-id="de383-363">1</span><span class="sxs-lookup"><span data-stu-id="de383-363">1</span></span>|<span data-ttu-id="de383-364">✔</span><span class="sxs-lookup"><span data-stu-id="de383-364">✔</span></span>|<span data-ttu-id="de383-365">Gibt an, ob der Connector eine Erfahrung im Kontext eines Kanals in einem bietet, oder eine Erfahrung, die nur für einen einzelnen Benutzer ( ) `team` gilt. `personal`</span><span class="sxs-lookup"><span data-stu-id="de383-365">Specifies whether the Connector offers an experience in the context of a channel in a `team`, or an experience scoped to an individual user alone (`personal`).</span></span> <span data-ttu-id="de383-366">Derzeit wird nur der `team` Bereich unterstützt.</span><span class="sxs-lookup"><span data-stu-id="de383-366">Currently, only the `team` scope is supported.</span></span>|

## <a name="composeextensions"></a><span data-ttu-id="de383-367">composeExtensions</span><span class="sxs-lookup"><span data-stu-id="de383-367">composeExtensions</span></span>

<span data-ttu-id="de383-368">**Optional**</span><span class="sxs-lookup"><span data-stu-id="de383-368">**Optional**</span></span>

<span data-ttu-id="de383-369">Definiert eine Messagingerweiterung für die App.</span><span class="sxs-lookup"><span data-stu-id="de383-369">Defines a messaging extension for the app.</span></span>

> [!NOTE]
> <span data-ttu-id="de383-370">Der Name des Features wurde im November 2017 von "Komponenerweiterung" in "Messaging-Erweiterung" geändert, aber der Manifestname bleibt derselbe, sodass vorhandene Erweiterungen weiterhin funktionieren.</span><span class="sxs-lookup"><span data-stu-id="de383-370">The name of the feature was changed from "compose extension" to "messaging extension" in November, 2017, but the manifest name remains the same so that existing extensions continue to function.</span></span>

<span data-ttu-id="de383-371">Das Objekt ist ein Array (maximal 1 Element) mit allen Elementen des Typs `object` .</span><span class="sxs-lookup"><span data-stu-id="de383-371">The object is an array (maximum of 1 element) with all elements of type `object`.</span></span> <span data-ttu-id="de383-372">Dieser Block ist nur für Lösungen erforderlich, die eine Messagingerweiterung bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="de383-372">This block is required only for solutions that provide a messaging extension.</span></span>

|<span data-ttu-id="de383-373">Name</span><span class="sxs-lookup"><span data-stu-id="de383-373">Name</span></span>| <span data-ttu-id="de383-374">Typ</span><span class="sxs-lookup"><span data-stu-id="de383-374">Type</span></span> | <span data-ttu-id="de383-375">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="de383-375">Maximum Size</span></span> | <span data-ttu-id="de383-376">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="de383-376">Required</span></span> | <span data-ttu-id="de383-377">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="de383-377">Description</span></span>|
|---|---|---|---|---|
|`botId`|<span data-ttu-id="de383-378">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="de383-378">String</span></span>|<span data-ttu-id="de383-379">64</span><span class="sxs-lookup"><span data-stu-id="de383-379">64</span></span>|<span data-ttu-id="de383-380">✔</span><span class="sxs-lookup"><span data-stu-id="de383-380">✔</span></span>|<span data-ttu-id="de383-381">Die eindeutige Microsoft-App-ID für den Bot, die die Messagingerweiterung unterstützt, wie sie im Bot Framework registriert ist.</span><span class="sxs-lookup"><span data-stu-id="de383-381">The unique Microsoft app ID for the bot that backs the messaging extension, as registered with the Bot Framework.</span></span> <span data-ttu-id="de383-382">Dies kann durchaus mit der gesamten [App-ID](#id)identisch sein.</span><span class="sxs-lookup"><span data-stu-id="de383-382">This may well be the same as the overall [app ID](#id).</span></span>|
|`canUpdateConfiguration`|<span data-ttu-id="de383-383">Boolesch</span><span class="sxs-lookup"><span data-stu-id="de383-383">Boolean</span></span>|||<span data-ttu-id="de383-384">Ein Wert, der angibt, ob die Konfiguration einer Messagingerweiterung vom Benutzer aktualisiert werden kann.</span><span class="sxs-lookup"><span data-stu-id="de383-384">A value indicating whether the configuration of a messaging extension can be updated by the user.</span></span> <span data-ttu-id="de383-385">Der Standardwert lautet `false`.</span><span class="sxs-lookup"><span data-stu-id="de383-385">The default is `false`.</span></span>|
|`commands`|<span data-ttu-id="de383-386">Array des Objekts</span><span class="sxs-lookup"><span data-stu-id="de383-386">Array of object</span></span>|<span data-ttu-id="de383-387">10</span><span class="sxs-lookup"><span data-stu-id="de383-387">10</span></span>|<span data-ttu-id="de383-388">✔</span><span class="sxs-lookup"><span data-stu-id="de383-388">✔</span></span>|<span data-ttu-id="de383-389">Array von Befehlen, die von der Messagingerweiterung unterstützt werden</span><span class="sxs-lookup"><span data-stu-id="de383-389">Array of commands the messaging extension supports</span></span>|

### <a name="composeextensionscommands"></a><span data-ttu-id="de383-390">composeExtensions.commands</span><span class="sxs-lookup"><span data-stu-id="de383-390">composeExtensions.commands</span></span>

<span data-ttu-id="de383-391">Ihre Messagingerweiterung sollte einen oder mehrere Befehle deklarieren.</span><span class="sxs-lookup"><span data-stu-id="de383-391">Your messaging extension should declare one or more commands.</span></span> <span data-ttu-id="de383-392">Jeder Befehl wird in Microsoft Teams als potenzielle Interaktion vom UI-basierten Einstiegspunkt angezeigt.</span><span class="sxs-lookup"><span data-stu-id="de383-392">Each command appears in Microsoft Teams as a potential interaction from the UI-based entry point.</span></span> <span data-ttu-id="de383-393">Es gibt maximal 10 Befehle.</span><span class="sxs-lookup"><span data-stu-id="de383-393">There is a maximum of 10 commands.</span></span>

<span data-ttu-id="de383-394">Jedes Befehlselement ist ein Objekt mit der folgenden Struktur:</span><span class="sxs-lookup"><span data-stu-id="de383-394">Each command item is an object with the following structure:</span></span>

|<span data-ttu-id="de383-395">Name</span><span class="sxs-lookup"><span data-stu-id="de383-395">Name</span></span>| <span data-ttu-id="de383-396">Typ</span><span class="sxs-lookup"><span data-stu-id="de383-396">Type</span></span>| <span data-ttu-id="de383-397">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="de383-397">Maximum size</span></span> | <span data-ttu-id="de383-398">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="de383-398">Required</span></span> | <span data-ttu-id="de383-399">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="de383-399">Description</span></span>|
|---|---|---|---|---|
|`id`|<span data-ttu-id="de383-400">String</span><span class="sxs-lookup"><span data-stu-id="de383-400">String</span></span>|<span data-ttu-id="de383-401">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="de383-401">64 characters</span></span>|<span data-ttu-id="de383-402">✔</span><span class="sxs-lookup"><span data-stu-id="de383-402">✔</span></span>|<span data-ttu-id="de383-403">Die ID für den Befehl.</span><span class="sxs-lookup"><span data-stu-id="de383-403">The ID for the command.</span></span>|
|`type`|<span data-ttu-id="de383-404">String</span><span class="sxs-lookup"><span data-stu-id="de383-404">String</span></span>|<span data-ttu-id="de383-405">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="de383-405">64 characters</span></span>||<span data-ttu-id="de383-406">Typ des Befehls.</span><span class="sxs-lookup"><span data-stu-id="de383-406">Type of the command.</span></span> <span data-ttu-id="de383-407">Einer von `query` oder `action` .</span><span class="sxs-lookup"><span data-stu-id="de383-407">One of `query` or `action`.</span></span> <span data-ttu-id="de383-408">Standard: `query`</span><span class="sxs-lookup"><span data-stu-id="de383-408">Default: `query`</span></span>|
|`title`|<span data-ttu-id="de383-409">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="de383-409">String</span></span>|<span data-ttu-id="de383-410">32 Zeichen</span><span class="sxs-lookup"><span data-stu-id="de383-410">32 characters</span></span>|<span data-ttu-id="de383-411">✔</span><span class="sxs-lookup"><span data-stu-id="de383-411">✔</span></span>|<span data-ttu-id="de383-412">Der benutzerfreundliche Befehlsname.</span><span class="sxs-lookup"><span data-stu-id="de383-412">The user-friendly command name.</span></span>|
|`description`|<span data-ttu-id="de383-413">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="de383-413">String</span></span>|<span data-ttu-id="de383-414">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="de383-414">128 characters</span></span>||<span data-ttu-id="de383-415">Die Beschreibung, die Benutzern angezeigt wird, um den Zweck dieses Befehls anzugeben.</span><span class="sxs-lookup"><span data-stu-id="de383-415">The description that appears to users to indicate the purpose of this command.</span></span>|
|`initialRun`|<span data-ttu-id="de383-416">Boolesch</span><span class="sxs-lookup"><span data-stu-id="de383-416">Boolean</span></span>|||<span data-ttu-id="de383-417">Ein boolescher Wert, der angibt, ob der Befehl zunächst ohne Parameter ausgeführt werden soll.</span><span class="sxs-lookup"><span data-stu-id="de383-417">A Boolean value that indicates whether the command should be run initially with no parameters.</span></span> <span data-ttu-id="de383-418">Standard: `false`</span><span class="sxs-lookup"><span data-stu-id="de383-418">Default: `false`</span></span>|
|`context`|<span data-ttu-id="de383-419">Array von Strings</span><span class="sxs-lookup"><span data-stu-id="de383-419">Array of Strings</span></span>|<span data-ttu-id="de383-420">3</span><span class="sxs-lookup"><span data-stu-id="de383-420">3</span></span>||<span data-ttu-id="de383-421">Definiert, von wo aus die Nachrichtenerweiterung aufgerufen werden kann.</span><span class="sxs-lookup"><span data-stu-id="de383-421">Defines where the message extension can be invoked from.</span></span> <span data-ttu-id="de383-422">Jede Beliebige Kombination von `compose` , `commandBox` . `message`</span><span class="sxs-lookup"><span data-stu-id="de383-422">Any combination of `compose`, `commandBox`, `message`.</span></span> <span data-ttu-id="de383-423">Standard ist `["compose", "commandBox"]`</span><span class="sxs-lookup"><span data-stu-id="de383-423">Default is `["compose", "commandBox"]`</span></span>|
|`fetchTask`|<span data-ttu-id="de383-424">Boolesch</span><span class="sxs-lookup"><span data-stu-id="de383-424">Boolean</span></span>|||<span data-ttu-id="de383-425">Ein boolescher Wert, der angibt, ob das Taskmodul dynamisch abgerufen werden soll.</span><span class="sxs-lookup"><span data-stu-id="de383-425">A boolean value that indicates if it should fetch the task module dynamically.</span></span>|
|`taskInfo`|<span data-ttu-id="de383-426">Object</span><span class="sxs-lookup"><span data-stu-id="de383-426">Object</span></span>|||<span data-ttu-id="de383-427">Geben Sie den Taskmodul an, der vorab geladen werden soll, wenn ein Messagingerweiterungsbefehl verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="de383-427">Specify the task module to preload when using a messaging extension command.</span></span>|
|`taskInfo.title`|<span data-ttu-id="de383-428">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="de383-428">String</span></span>|<span data-ttu-id="de383-429">64</span><span class="sxs-lookup"><span data-stu-id="de383-429">64</span></span>||<span data-ttu-id="de383-430">Erster Dialogtitel.</span><span class="sxs-lookup"><span data-stu-id="de383-430">Initial dialog title.</span></span>|
|`taskInfo.width`|<span data-ttu-id="de383-431">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="de383-431">String</span></span>|||<span data-ttu-id="de383-432">Dialogbreite - entweder eine Zahl in Pixel oder ein Standardlayout wie 'large', 'medium' oder 'small'.</span><span class="sxs-lookup"><span data-stu-id="de383-432">Dialog width - either a number in pixels or default layout such as 'large', 'medium', or 'small'.</span></span>|
|`taskInfo.height`|<span data-ttu-id="de383-433">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="de383-433">String</span></span>|||<span data-ttu-id="de383-434">Dialoghöhe - entweder eine Zahl in Pixel oder ein Standardlayout wie 'large', 'medium' oder 'small'.</span><span class="sxs-lookup"><span data-stu-id="de383-434">Dialog height - either a number in pixels or default layout such as 'large', 'medium', or 'small'.</span></span>|
|`taskInfo.url`|<span data-ttu-id="de383-435">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="de383-435">String</span></span>|||<span data-ttu-id="de383-436">Erste Webview-URL.</span><span class="sxs-lookup"><span data-stu-id="de383-436">Initial webview URL.</span></span>|
|`messageHandlers`|<span data-ttu-id="de383-437">Array von Objekten</span><span class="sxs-lookup"><span data-stu-id="de383-437">Array of Objects</span></span>|<span data-ttu-id="de383-438">5 </span><span class="sxs-lookup"><span data-stu-id="de383-438">5</span></span>||<span data-ttu-id="de383-439">Eine Liste von Handlern, mit denen Apps aufgerufen werden können, wenn bestimmte Bedingungen erfüllt sind.</span><span class="sxs-lookup"><span data-stu-id="de383-439">A list of handlers that allow apps to be invoked when certain conditions are met.</span></span> <span data-ttu-id="de383-440">Domänen müssen auch in aufgeführt `validDomains` werden.</span><span class="sxs-lookup"><span data-stu-id="de383-440">Domains must also be listed in `validDomains`.</span></span>|
|`messageHandlers.type`|<span data-ttu-id="de383-441">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="de383-441">String</span></span>|||<span data-ttu-id="de383-442">Der Typ des Nachrichtenhandlers.</span><span class="sxs-lookup"><span data-stu-id="de383-442">The type of message handler.</span></span> <span data-ttu-id="de383-443">Muss `"link"` sein.</span><span class="sxs-lookup"><span data-stu-id="de383-443">Must be `"link"`.</span></span>|
|`messageHandlers.value.domains`|<span data-ttu-id="de383-444">Array von Strings</span><span class="sxs-lookup"><span data-stu-id="de383-444">Array of Strings</span></span>|||<span data-ttu-id="de383-445">Array von Domänen, für die der Linknachrichtenhandler registrieren kann.</span><span class="sxs-lookup"><span data-stu-id="de383-445">Array of domains that the link message handler can register for.</span></span>|
|`parameters`|<span data-ttu-id="de383-446">Array des Objekts</span><span class="sxs-lookup"><span data-stu-id="de383-446">Array of object</span></span>|<span data-ttu-id="de383-447">5 </span><span class="sxs-lookup"><span data-stu-id="de383-447">5</span></span>|<span data-ttu-id="de383-448">✔</span><span class="sxs-lookup"><span data-stu-id="de383-448">✔</span></span>|<span data-ttu-id="de383-449">Die Liste der Parameter, die der Befehl verwendet.</span><span class="sxs-lookup"><span data-stu-id="de383-449">The list of parameters the command takes.</span></span> <span data-ttu-id="de383-450">Minimum: 1; maximal: 5</span><span class="sxs-lookup"><span data-stu-id="de383-450">Minimum: 1; maximum: 5</span></span>|
|`parameter.name`|<span data-ttu-id="de383-451">String</span><span class="sxs-lookup"><span data-stu-id="de383-451">String</span></span>|<span data-ttu-id="de383-452">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="de383-452">64 characters</span></span>|<span data-ttu-id="de383-453">✔</span><span class="sxs-lookup"><span data-stu-id="de383-453">✔</span></span>|<span data-ttu-id="de383-454">Der Name des Parameters, wie er im Client angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="de383-454">The name of the parameter as it appears in the client.</span></span> <span data-ttu-id="de383-455">Dies ist in der Benutzeranforderung enthalten.</span><span class="sxs-lookup"><span data-stu-id="de383-455">This is included in the user request.</span></span>|
|`parameter.title`|<span data-ttu-id="de383-456">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="de383-456">String</span></span>|<span data-ttu-id="de383-457">32 Zeichen</span><span class="sxs-lookup"><span data-stu-id="de383-457">32 characters</span></span>|<span data-ttu-id="de383-458">✔</span><span class="sxs-lookup"><span data-stu-id="de383-458">✔</span></span>|<span data-ttu-id="de383-459">Benutzerfreundlicher Titel für den Parameter.</span><span class="sxs-lookup"><span data-stu-id="de383-459">User-friendly title for the parameter.</span></span>|
|`parameter.description`|<span data-ttu-id="de383-460">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="de383-460">String</span></span>|<span data-ttu-id="de383-461">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="de383-461">128 characters</span></span>||<span data-ttu-id="de383-462">Benutzerfreundliche Zeichenfolge, die den Zweck dieses Parameters beschreibt.</span><span class="sxs-lookup"><span data-stu-id="de383-462">User-friendly string that describes this parameter’s purpose.</span></span>|
|`parameter.inputType`|<span data-ttu-id="de383-463">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="de383-463">String</span></span>|<span data-ttu-id="de383-464">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="de383-464">128 characters</span></span>||<span data-ttu-id="de383-465">Definiert den Typ des Steuerelements, das in einem Taskmodul für angezeigt `fetchTask: true` wird.</span><span class="sxs-lookup"><span data-stu-id="de383-465">Defines the type of control displayed on a task module for `fetchTask: true`.</span></span> <span data-ttu-id="de383-466">Einer von `text` , , , , , , `textarea` `number` `date` `time` `toggle` `choiceset` .</span><span class="sxs-lookup"><span data-stu-id="de383-466">One of `text`, `textarea`, `number`, `date`, `time`, `toggle`, `choiceset`.</span></span>|
|`parameter.choices`|<span data-ttu-id="de383-467">Array von Objekten</span><span class="sxs-lookup"><span data-stu-id="de383-467">Array of Objects</span></span>|<span data-ttu-id="de383-468">10</span><span class="sxs-lookup"><span data-stu-id="de383-468">10</span></span>||<span data-ttu-id="de383-469">Die Auswahloptionen für die `choiceset` .</span><span class="sxs-lookup"><span data-stu-id="de383-469">The choice options for the `choiceset`.</span></span> <span data-ttu-id="de383-470">Nur verwenden, wenn `parameter.inputType` es sich um `choiceset` .</span><span class="sxs-lookup"><span data-stu-id="de383-470">Use only when `parameter.inputType` is `choiceset`.</span></span>|
|`parameter.choices.title`|<span data-ttu-id="de383-471">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="de383-471">String</span></span>|<span data-ttu-id="de383-472">128</span><span class="sxs-lookup"><span data-stu-id="de383-472">128</span></span>||<span data-ttu-id="de383-473">Titel der Wahl.</span><span class="sxs-lookup"><span data-stu-id="de383-473">Title of the choice.</span></span>|
|`parameter.choices.value`|<span data-ttu-id="de383-474">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="de383-474">String</span></span>|<span data-ttu-id="de383-475">512</span><span class="sxs-lookup"><span data-stu-id="de383-475">512</span></span>||<span data-ttu-id="de383-476">Value of the choice.</span><span class="sxs-lookup"><span data-stu-id="de383-476">Value of the choice.</span></span>|

## <a name="permissions"></a><span data-ttu-id="de383-477">Berechtigungen</span><span class="sxs-lookup"><span data-stu-id="de383-477">permissions</span></span>

<span data-ttu-id="de383-478">**Optional**</span><span class="sxs-lookup"><span data-stu-id="de383-478">**Optional**</span></span>

<span data-ttu-id="de383-479">Ein Array, dessen `string` Berechtigung die App anfordert, sodass Endbenutzer wissen, wie die Erweiterung ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="de383-479">An array of `string` which specifies which permissions the app requests, which lets end users know how the extension will perform.</span></span> <span data-ttu-id="de383-480">Die folgenden Optionen sind nicht exklusiv:</span><span class="sxs-lookup"><span data-stu-id="de383-480">The following options are non-exclusive:</span></span>

* <span data-ttu-id="de383-481">`identity`&emsp;Erfordert Benutzeridentitätsinformationen.</span><span class="sxs-lookup"><span data-stu-id="de383-481">`identity` &emsp; Requires user identity information.</span></span>
* <span data-ttu-id="de383-482">`messageTeamMembers`&emsp;Erfordert die Berechtigung zum Senden direkter Nachrichten an Teammitglieder.</span><span class="sxs-lookup"><span data-stu-id="de383-482">`messageTeamMembers` &emsp; Requires permission to send direct messages to team members.</span></span>

<span data-ttu-id="de383-483">Wenn Sie diese Berechtigungen beim Aktualisieren Ihrer App ändern, werden die Benutzer den Zustimmungsprozess beim ersten Ausführen der aktualisierten App wiederholen.</span><span class="sxs-lookup"><span data-stu-id="de383-483">Changing these permissions when updating your app will cause your users to repeat the consent process the first time they run the updated app.</span></span>

## <a name="devicepermissions"></a><span data-ttu-id="de383-484">devicePermissions</span><span class="sxs-lookup"><span data-stu-id="de383-484">devicePermissions</span></span>

<span data-ttu-id="de383-485">**Optional** Array von Strings</span><span class="sxs-lookup"><span data-stu-id="de383-485">**Optional** Array of Strings</span></span>

<span data-ttu-id="de383-486">Gibt die systemeigenen Features auf dem Gerät eines Benutzers an, auf die Ihre App möglicherweise Zugriff anfordert.</span><span class="sxs-lookup"><span data-stu-id="de383-486">Specifies the native features on a user's device that your app may request access to.</span></span> <span data-ttu-id="de383-487">Mögliche Optionen sind:</span><span class="sxs-lookup"><span data-stu-id="de383-487">Options are:</span></span>

* `geolocation`
* `media`
* `notifications`
* `midi`
* `openExternal`

## <a name="validdomains"></a><span data-ttu-id="de383-488">validDomains</span><span class="sxs-lookup"><span data-stu-id="de383-488">validDomains</span></span>

<span data-ttu-id="de383-489">**Optional**, außer **Erforderlich,** sofern angegeben</span><span class="sxs-lookup"><span data-stu-id="de383-489">**Optional**, except **Required** where noted</span></span>

<span data-ttu-id="de383-490">Eine Liste gültiger Domänen, von denen die App erwartet, dass Inhalte geladen werden.</span><span class="sxs-lookup"><span data-stu-id="de383-490">A list of valid domains from which the app expects to load any content.</span></span> <span data-ttu-id="de383-491">Domänenlisten können Platzhalter enthalten, z. `*.example.com` B. .</span><span class="sxs-lookup"><span data-stu-id="de383-491">Domain listings can include wildcards, for example `*.example.com`.</span></span> <span data-ttu-id="de383-492">Dies entspricht genau einem Segment der Domäne; wenn Sie übereinstimmen müssen, `a.b.example.com` verwenden Sie `*.*.example.com` .</span><span class="sxs-lookup"><span data-stu-id="de383-492">This matches exactly one segment of the domain; if you need to match `a.b.example.com` then use `*.*.example.com`.</span></span> <span data-ttu-id="de383-493">Wenn Ihre Registerkartenkonfiguration oder Inhaltsbenutzeroberfläche zu einer anderen Domäne als der für die Registerkartenkonfiguration verwendenden Domäne navigieren muss, muss diese Domäne hier angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="de383-493">If your tab configuration or content UI needs to navigate to any other domain besides the one use for tab configuration, that domain must be specified here.</span></span>

<span data-ttu-id="de383-494">Es ist jedoch **nicht** erforderlich, die Domänen von Identitätsanbietern, die Sie unterstützen möchten, in Ihre App aufzunehmen.</span><span class="sxs-lookup"><span data-stu-id="de383-494">It is **not** necessary to include the domains of identity providers you want to support in your app, however.</span></span> <span data-ttu-id="de383-495">Um sich beispielsweise mit einer Google-ID zu authentifizieren, ist es erforderlich, zu accounts.google.com umzuleiten, aber Sie sollten accounts.google.com nicht in `validDomains[]` .</span><span class="sxs-lookup"><span data-stu-id="de383-495">For example, to authenticate using a Google ID, it's necessary to redirect to accounts.google.com, but you should not include accounts.google.com in `validDomains[]`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="de383-496">Fügen Sie keine Domänen hinzu, die sich außerhalb Ihrer Kontrolle befinden, weder direkt noch über Platzhalter.</span><span class="sxs-lookup"><span data-stu-id="de383-496">Do not add domains that are outside your control, either directly or via wildcards.</span></span> <span data-ttu-id="de383-497">Zum Beispiel `yourapp.onmicrosoft.com` ist gültig, aber `*.onmicrosoft.com` nicht gültig.</span><span class="sxs-lookup"><span data-stu-id="de383-497">For example, `yourapp.onmicrosoft.com` is valid, but `*.onmicrosoft.com` is not valid.</span></span>

<span data-ttu-id="de383-498">Das Objekt ist ein Array mit allen Elementen des Typs `string` .</span><span class="sxs-lookup"><span data-stu-id="de383-498">The object is an array with all elements of the type `string`.</span></span>

## <a name="webapplicationinfo"></a><span data-ttu-id="de383-499">webApplicationInfo</span><span class="sxs-lookup"><span data-stu-id="de383-499">webApplicationInfo</span></span>

<span data-ttu-id="de383-500">**Optional**</span><span class="sxs-lookup"><span data-stu-id="de383-500">**Optional**</span></span>

<span data-ttu-id="de383-501">Geben Sie Ihre AAD-App-ID und Graph Informationen an, damit sich Benutzer nahtlos bei Ihrer AAD-App anmelden können.</span><span class="sxs-lookup"><span data-stu-id="de383-501">Specify your AAD App ID and Graph information to help users seamlessly sign into your AAD app.</span></span>

|<span data-ttu-id="de383-502">Name</span><span class="sxs-lookup"><span data-stu-id="de383-502">Name</span></span>| <span data-ttu-id="de383-503">Typ</span><span class="sxs-lookup"><span data-stu-id="de383-503">Type</span></span>| <span data-ttu-id="de383-504">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="de383-504">Maximum size</span></span> | <span data-ttu-id="de383-505">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="de383-505">Required</span></span> | <span data-ttu-id="de383-506">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="de383-506">Description</span></span>|
|---|---|---|---|---|
|`id`|<span data-ttu-id="de383-507">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="de383-507">String</span></span>|<span data-ttu-id="de383-508">36 Zeichen</span><span class="sxs-lookup"><span data-stu-id="de383-508">36 characters</span></span>|<span data-ttu-id="de383-509">✔</span><span class="sxs-lookup"><span data-stu-id="de383-509">✔</span></span>|<span data-ttu-id="de383-510">AAD-Anwendungs-ID der App.</span><span class="sxs-lookup"><span data-stu-id="de383-510">AAD application id of the app.</span></span> <span data-ttu-id="de383-511">Diese ID muss eine GUID sein.</span><span class="sxs-lookup"><span data-stu-id="de383-511">This id must be a GUID.</span></span>|
|`resource`|<span data-ttu-id="de383-512">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="de383-512">String</span></span>|<span data-ttu-id="de383-513">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="de383-513">2048 characters</span></span>|<span data-ttu-id="de383-514">✔</span><span class="sxs-lookup"><span data-stu-id="de383-514">✔</span></span>|<span data-ttu-id="de383-515">Ressourcen-URL der App zum Abrufen von Authentifizierungstoken für SSO.</span><span class="sxs-lookup"><span data-stu-id="de383-515">Resource url of app for acquiring auth token for SSO.</span></span>|

## <a name="configurableproperties"></a><span data-ttu-id="de383-516">konfigurierbareEigenschaften</span><span class="sxs-lookup"><span data-stu-id="de383-516">configurableProperties</span></span>

<span data-ttu-id="de383-517">**Optional** - Array</span><span class="sxs-lookup"><span data-stu-id="de383-517">**Optional** - array</span></span>

<span data-ttu-id="de383-518">Der `configurableProperties` Block definiert die App-Eigenschaften, die Teams Administrator anpassen kann.</span><span class="sxs-lookup"><span data-stu-id="de383-518">The `configurableProperties` block defines the app properties that Teams admin can customize.</span></span> <span data-ttu-id="de383-519">Weitere Informationen finden Sie unter [Anpassen von Apps in Microsoft Teams](/MicrosoftTeams/customize-apps).</span><span class="sxs-lookup"><span data-stu-id="de383-519">For more information, see [customize apps in Microsoft Teams](/MicrosoftTeams/customize-apps).</span></span>

> [!NOTE]
> <span data-ttu-id="de383-520">Es muss mindestens eine Eigenschaft definiert werden.</span><span class="sxs-lookup"><span data-stu-id="de383-520">A minimum of one property must be defined.</span></span> <span data-ttu-id="de383-521">Sie können maximal neun Eigenschaften in diesem Block definieren.</span><span class="sxs-lookup"><span data-stu-id="de383-521">You can define a maximum of nine properties in this block.</span></span>
> <span data-ttu-id="de383-522">Als bewährte Methode müssen Sie Anpassungsrichtlinien für App-Benutzer und -Kunden bereitstellen, die Sie beim Anpassen Ihrer App befolgen müssen.</span><span class="sxs-lookup"><span data-stu-id="de383-522">As a best practice, you must provide customization guidelines for app users and customers to follow when customizing your app.</span></span> 

<span data-ttu-id="de383-523">Sie können eine der folgenden Eigenschaften definieren:</span><span class="sxs-lookup"><span data-stu-id="de383-523">You can define any of the following properties:</span></span>
* <span data-ttu-id="de383-524">`name`: Ermöglicht es Administratoren, den Anzeigenamen der App zu ändern.</span><span class="sxs-lookup"><span data-stu-id="de383-524">`name`: Allows admin to change the app's display name.</span></span>
* <span data-ttu-id="de383-525">`shortDescription`: Ermöglicht es Admin, die Kurzbeschreibung der App zu ändern.</span><span class="sxs-lookup"><span data-stu-id="de383-525">`shortDescription`: Allows admin to change the app's short description.</span></span>
* <span data-ttu-id="de383-526">`longDescription`: Ermöglicht es Administratoren, die detaillierte Beschreibung der App zu ändern.</span><span class="sxs-lookup"><span data-stu-id="de383-526">`longDescription`: Allows admin to change the app's detailed description.</span></span>
* <span data-ttu-id="de383-527">`smallImageUrl`: Es ist die `outline` Eigenschaft im Block des `icons` Manifests.</span><span class="sxs-lookup"><span data-stu-id="de383-527">`smallImageUrl`: It is the `outline` property in the `icons` block of the manifest.</span></span>
* <span data-ttu-id="de383-528">`largeImageUrl`: Es ist die `color` Eigenschaft im Block des `icons` Manifests.</span><span class="sxs-lookup"><span data-stu-id="de383-528">`largeImageUrl`: It is the `color` property in the `icons` block of the manifest.</span></span>
* <span data-ttu-id="de383-529">`accentColor`: Es ist die Farbe, die in Verbindung mit und als Hintergrund für Ihre Gliederungssymbole verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="de383-529">`accentColor`: It is the color to use in conjunction with and as a background for your outline icons.</span></span>
* <span data-ttu-id="de383-530">`websiteUrl`: Es ist die https:// URL auf der Website des Entwicklers.</span><span class="sxs-lookup"><span data-stu-id="de383-530">`websiteUrl`: It is the https:// URL to the developer's website.</span></span>
* <span data-ttu-id="de383-531">`privacyUrl`: Es ist die https:// URL zur Datenschutzrichtlinie des Entwicklers.</span><span class="sxs-lookup"><span data-stu-id="de383-531">`privacyUrl`: It is the https:// URL to the developer's privacy policy.</span></span>
* <span data-ttu-id="de383-532">`termsOfUseUrl`: Es ist die https:// URL zu den Nutzungsbedingungen des Entwicklers.</span><span class="sxs-lookup"><span data-stu-id="de383-532">`termsOfUseUrl`: It is the https:// URL to the developer's terms of use.</span></span>

## <a name="defaultinstallscope"></a><span data-ttu-id="de383-533">defaultInstallScope</span><span class="sxs-lookup"><span data-stu-id="de383-533">defaultInstallScope</span></span>

<span data-ttu-id="de383-534">**Optional** - String</span><span class="sxs-lookup"><span data-stu-id="de383-534">**Optional** - string</span></span>

<span data-ttu-id="de383-535">Gibt den standardmäßig für diese App definierten Installationsbereich an.</span><span class="sxs-lookup"><span data-stu-id="de383-535">Specifies the install scope defined for this app by default.</span></span> <span data-ttu-id="de383-536">Der definierte Bereich ist die Option, die auf der Schaltfläche angezeigt wird, wenn ein Benutzer versucht, die App hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="de383-536">The defined scope will be the option displayed on the button when a user tries to add the app.</span></span> <span data-ttu-id="de383-537">Mögliche Optionen sind:</span><span class="sxs-lookup"><span data-stu-id="de383-537">Options are:</span></span>
* `personal`
* `team`
* `groupchat`
* `meetings`

## <a name="defaultgroupcapability"></a><span data-ttu-id="de383-538">defaultGroupCapability</span><span class="sxs-lookup"><span data-stu-id="de383-538">defaultGroupCapability</span></span>

<span data-ttu-id="de383-539">**Optional** - Objekt</span><span class="sxs-lookup"><span data-stu-id="de383-539">**Optional** - object</span></span>

<span data-ttu-id="de383-540">Wenn ein Gruppeninstallationsbereich ausgewählt ist, definiert er die Standardfunktion, wenn der Benutzer die App installiert.</span><span class="sxs-lookup"><span data-stu-id="de383-540">When a group install scope is selected, it will define the default capability when the user installs the app.</span></span> <span data-ttu-id="de383-541">Mögliche Optionen sind:</span><span class="sxs-lookup"><span data-stu-id="de383-541">Options are:</span></span>
* `team`
* `groupchat`
* `meetings`
 
|<span data-ttu-id="de383-542">Name</span><span class="sxs-lookup"><span data-stu-id="de383-542">Name</span></span>| <span data-ttu-id="de383-543">Typ</span><span class="sxs-lookup"><span data-stu-id="de383-543">Type</span></span>| <span data-ttu-id="de383-544">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="de383-544">Maximum size</span></span> | <span data-ttu-id="de383-545">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="de383-545">Required</span></span> | <span data-ttu-id="de383-546">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="de383-546">Description</span></span>|
|---|---|---|---|---|
|`team`|<span data-ttu-id="de383-547">string</span><span class="sxs-lookup"><span data-stu-id="de383-547">string</span></span>|||<span data-ttu-id="de383-548">Wenn der ausgewählte Installationsbereich `team` ist , gibt dieses Feld die verfügbare Standardfunktion an.</span><span class="sxs-lookup"><span data-stu-id="de383-548">When the install scope selected is `team`, this field specifies the default capability available.</span></span> <span data-ttu-id="de383-549">Optionen: `tab` `bot` , , oder `connector` .</span><span class="sxs-lookup"><span data-stu-id="de383-549">Options: `tab`, `bot`, or `connector`.</span></span>|
|`groupchat`|<span data-ttu-id="de383-550">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="de383-550">string</span></span>|||<span data-ttu-id="de383-551">Wenn der ausgewählte Installationsbereich `groupchat` ist , gibt dieses Feld die verfügbare Standardfunktion an.</span><span class="sxs-lookup"><span data-stu-id="de383-551">When the install scope selected is `groupchat`, this field specifies the default capability available.</span></span> <span data-ttu-id="de383-552">Optionen: `tab` `bot` , , oder `connector` .</span><span class="sxs-lookup"><span data-stu-id="de383-552">Options: `tab`, `bot`, or `connector`.</span></span>|
|`meetings`|<span data-ttu-id="de383-553">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="de383-553">string</span></span>|||<span data-ttu-id="de383-554">Wenn der ausgewählte Installationsbereich `meetings` ist , gibt dieses Feld die verfügbare Standardfunktion an.</span><span class="sxs-lookup"><span data-stu-id="de383-554">When the install scope selected is `meetings`, this field specifies the default capability available.</span></span> <span data-ttu-id="de383-555">Optionen: `tab` `bot` , , oder `connector` .</span><span class="sxs-lookup"><span data-stu-id="de383-555">Options: `tab`, `bot`, or `connector`.</span></span>|

