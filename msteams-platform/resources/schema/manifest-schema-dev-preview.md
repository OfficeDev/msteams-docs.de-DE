---
title: Developer Preview Manifestschemareferenz
description: Beschreibt das vom Manifest für Microsoft Teams unterstützte Schema
ms.topic: reference
keywords: Manifestschema für Teams Developer Preview
ms.date: 05/20/2019
ms.openlocfilehash: 0776ced1704f46c95054308c8a1898ed938e47cb
ms.sourcegitcommit: 976e870cc925f61b76c3830ec04ba6e4bdfde32f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/27/2021
ms.locfileid: "50014103"
---
# <a name="developer-preview-manifest-schema-for-microsoft-teams"></a><span data-ttu-id="69cea-104">Manifestschema der Entwicklervorschau für Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="69cea-104">Developer preview manifest schema for Microsoft Teams</span></span>

> [!NOTE]
> <span data-ttu-id="69cea-105">Weitere [Developer Preview](~/resources/dev-preview/developer-preview-intro.md) zum Programm und zur Teilnahme finden Sie unter Developer Preview.</span><span class="sxs-lookup"><span data-stu-id="69cea-105">See [Developer Preview](~/resources/dev-preview/developer-preview-intro.md) for information on the program and how you can join.</span></span>
> <span data-ttu-id="69cea-106">Wenn Sie die Entwicklervorschau nicht verwenden, sollten Sie diese Version des Manifests nicht verwenden.</span><span class="sxs-lookup"><span data-stu-id="69cea-106">If you are not using the developer preview you should not be using this version of the manifest.</span></span> <span data-ttu-id="69cea-107">Siehe [Referenz: Manifestschema für Microsoft Teams](~/resources/schema/manifest-schema.md) für die öffentliche Version des Manifests.</span><span class="sxs-lookup"><span data-stu-id="69cea-107">See [Reference: Manifest schema for Microsoft Teams](~/resources/schema/manifest-schema.md) for the public version of the manifest.</span></span>

<span data-ttu-id="69cea-108">Das Microsoft Teams-Manifest beschreibt, wie die App in das Microsoft Teams-Produkt integriert wird.</span><span class="sxs-lookup"><span data-stu-id="69cea-108">The Microsoft Teams manifest describes how the app integrates into the Microsoft Teams product.</span></span> <span data-ttu-id="69cea-109">Ihr Manifest muss dem Schema entsprechen, das unter gehostet [`https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json`](https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json) wird.</span><span class="sxs-lookup"><span data-stu-id="69cea-109">Your manifest must conform to the schema hosted at [`https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json`](https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json).</span></span>

<span data-ttu-id="69cea-110">Weitere Informationen zu den verfügbaren Features finden Sie unter: [Features in der öffentlichen Developer Preview für Microsoft Teams](~/resources/dev-preview/developer-preview-features.md).</span><span class="sxs-lookup"><span data-stu-id="69cea-110">For more information on the features available see: [Features in the Public Developer Preview for Microsoft Teams](~/resources/dev-preview/developer-preview-features.md).</span></span>

## <a name="sample-full-manifest"></a><span data-ttu-id="69cea-111">Beispiel für vollständiges Manifest</span><span class="sxs-lookup"><span data-stu-id="69cea-111">Sample full manifest</span></span>

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
  ]
}
```

<span data-ttu-id="69cea-112">Das Schema definiert die folgenden Eigenschaften:</span><span class="sxs-lookup"><span data-stu-id="69cea-112">The schema defines the following properties:</span></span>

## <a name="schema"></a><span data-ttu-id="69cea-113">$schema</span><span class="sxs-lookup"><span data-stu-id="69cea-113">$schema</span></span>

<span data-ttu-id="69cea-114">*Optional, aber empfohlen* &ndash; Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="69cea-114">*Optional, but recommended* &ndash; String</span></span>

<span data-ttu-id="69cea-115">Die https:// URL, die auf das JSON-Schema für das Manifest verweist.</span><span class="sxs-lookup"><span data-stu-id="69cea-115">The https:// URL referencing the JSON Schema for the manifest.</span></span>

## <a name="manifestversion"></a><span data-ttu-id="69cea-116">manifestVersion</span><span class="sxs-lookup"><span data-stu-id="69cea-116">manifestVersion</span></span>

<span data-ttu-id="69cea-117">**Erforderlich** &ndash; Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="69cea-117">**Required** &ndash; String</span></span>

<span data-ttu-id="69cea-118">Die Version des Manifestschemas, das dieses Manifest verwendet.</span><span class="sxs-lookup"><span data-stu-id="69cea-118">The version of the manifest schema this manifest is using.</span></span> <span data-ttu-id="69cea-119">Es sollte "devPreview" sein.</span><span class="sxs-lookup"><span data-stu-id="69cea-119">It should be "devPreview".</span></span>

## <a name="version"></a><span data-ttu-id="69cea-120">Version</span><span class="sxs-lookup"><span data-stu-id="69cea-120">version</span></span>

<span data-ttu-id="69cea-121">**Erforderlich** &ndash; Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="69cea-121">**Required** &ndash; String</span></span>

<span data-ttu-id="69cea-122">Die Version der bestimmten App.</span><span class="sxs-lookup"><span data-stu-id="69cea-122">The version of the specific app.</span></span> <span data-ttu-id="69cea-123">Wenn Sie etwas in Ihrem Manifest aktualisieren, muss auch die Version erhöht werden.</span><span class="sxs-lookup"><span data-stu-id="69cea-123">If you update something in your manifest, the version must be incremented as well.</span></span> <span data-ttu-id="69cea-124">Auf diese Weise wird bei der Installation des neuen Manifests das vorhandene überschrieben, und der Benutzer erhält die neue Funktionalität.</span><span class="sxs-lookup"><span data-stu-id="69cea-124">This way, when the new manifest is installed, it will overwrite the existing one and the user will get the new functionality.</span></span> <span data-ttu-id="69cea-125">Wenn diese App an den Store übermittelt wurde, muss das neue Manifest erneut übermittelt und erneut überprüft werden.</span><span class="sxs-lookup"><span data-stu-id="69cea-125">If this app was submitted to the store, the new manifest will have to be re-submitted and re-validated.</span></span> <span data-ttu-id="69cea-126">Anschließend erhalten Benutzer dieser App das neue aktualisierte Manifest automatisch in ein paar Stunden, nachdem sie genehmigt wurde.</span><span class="sxs-lookup"><span data-stu-id="69cea-126">Then, users of this app will get the new updated manifest automatically in a few hours, after it is approved.</span></span>

<span data-ttu-id="69cea-127">Wenn sich die von der App angeforderten Berechtigungen ändern, werden die Benutzer aufgefordert, ein Upgrade zu starten und der App erneut zu zustimmen.</span><span class="sxs-lookup"><span data-stu-id="69cea-127">If the app requested permissions change, users will be prompted to upgrade and re-consent to the app.</span></span>

<span data-ttu-id="69cea-128">Diese Versionszeichenfolge muss dem [Semverstandard](http://semver.org/) (MAJOR. MINOR. PATCH).</span><span class="sxs-lookup"><span data-stu-id="69cea-128">This version string must follow the [semver](http://semver.org/) standard (MAJOR.MINOR.PATCH).</span></span>

## <a name="id"></a><span data-ttu-id="69cea-129">id</span><span class="sxs-lookup"><span data-stu-id="69cea-129">id</span></span>

<span data-ttu-id="69cea-130">**Erforderlich** &ndash; Microsoft-App-ID</span><span class="sxs-lookup"><span data-stu-id="69cea-130">**Required** &ndash; Microsoft app ID</span></span>

<span data-ttu-id="69cea-131">Der eindeutige von Microsoft generierte Bezeichner für diese App.</span><span class="sxs-lookup"><span data-stu-id="69cea-131">The unique Microsoft-generated identifier for this app.</span></span> <span data-ttu-id="69cea-132">Wenn Sie einen Bot über das Microsoft Bot Framework registriert haben oder sich die Web-App Ihrer Registerkarte bereits bei Microsoft angemeldet hat, sollten Sie bereits über eine ID verfügen und sie hier eingeben.</span><span class="sxs-lookup"><span data-stu-id="69cea-132">If you have registered a bot via the Microsoft Bot Framework, or your tab's web app already signs in with Microsoft, you should already have an ID and should enter it here.</span></span> <span data-ttu-id="69cea-133">Andernfalls sollten Sie eine neue ID im Microsoft-Anwendungsregistrierungsportal[(](https://apps.dev.microsoft.com)Meine Anwendungen) generieren, sie hier eingeben und dann wiederverwenden, wenn Sie einen [Bot hinzufügen.](~/bots/how-to/create-a-bot-for-teams.md)</span><span class="sxs-lookup"><span data-stu-id="69cea-133">Otherwise, you should generate a new ID at the Microsoft Application Registration Portal ([My Applications](https://apps.dev.microsoft.com)), enter it here, and then reuse it when you [add a bot](~/bots/how-to/create-a-bot-for-teams.md).</span></span>

## <a name="packagename"></a><span data-ttu-id="69cea-134">packageName</span><span class="sxs-lookup"><span data-stu-id="69cea-134">packageName</span></span>

<span data-ttu-id="69cea-135">**Erforderlich** &ndash; Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="69cea-135">**Required** &ndash; String</span></span>

<span data-ttu-id="69cea-136">Ein eindeutiger Bezeichner für diese App in umgekehrter Domänen-Notation; Beispiel: com.example.myapp.</span><span class="sxs-lookup"><span data-stu-id="69cea-136">A unique identifier for this app in reverse domain notation; for example, com.example.myapp.</span></span>

## <a name="developer"></a><span data-ttu-id="69cea-137">developer</span><span class="sxs-lookup"><span data-stu-id="69cea-137">developer</span></span>

<span data-ttu-id="69cea-138">**Required**</span><span class="sxs-lookup"><span data-stu-id="69cea-138">**Required**</span></span>

<span data-ttu-id="69cea-139">Gibt Informationen zu Ihrem Unternehmen an.</span><span class="sxs-lookup"><span data-stu-id="69cea-139">Specifies information about your company.</span></span> <span data-ttu-id="69cea-140">Bei an AppSource (früher Office Store) übermittelten Apps müssen diese Werte mit den Informationen in Ihrem Eintrag "AppSource" übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="69cea-140">For apps submitted to AppSource (formerly Office Store), these values must match the information in your AppSource entry.</span></span>

|<span data-ttu-id="69cea-141">Name</span><span class="sxs-lookup"><span data-stu-id="69cea-141">Name</span></span>| <span data-ttu-id="69cea-142">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="69cea-142">Maximum size</span></span> | <span data-ttu-id="69cea-143">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="69cea-143">Required</span></span> | <span data-ttu-id="69cea-144">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="69cea-144">Description</span></span>|
|---|---|---|---|
|`name`|<span data-ttu-id="69cea-145">32 Zeichen</span><span class="sxs-lookup"><span data-stu-id="69cea-145">32 characters</span></span>|<span data-ttu-id="69cea-146">✔</span><span class="sxs-lookup"><span data-stu-id="69cea-146">✔</span></span>|<span data-ttu-id="69cea-147">Der Anzeigename für den Entwickler.</span><span class="sxs-lookup"><span data-stu-id="69cea-147">The display name for the developer.</span></span>|
|`websiteUrl`|<span data-ttu-id="69cea-148">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="69cea-148">2048 characters</span></span>|<span data-ttu-id="69cea-149">✔</span><span class="sxs-lookup"><span data-stu-id="69cea-149">✔</span></span>|<span data-ttu-id="69cea-150">Die https:// URL zur Website des Entwicklers.</span><span class="sxs-lookup"><span data-stu-id="69cea-150">The https:// URL to the developer's website.</span></span> <span data-ttu-id="69cea-151">Über diesen Link sollten Benutzer zu Ihrem Unternehmen oder zu ihrer produktspezifischen Angebotsseite gelangen.</span><span class="sxs-lookup"><span data-stu-id="69cea-151">This link should take users to your company or product-specific landing page.</span></span>|
|`privacyUrl`|<span data-ttu-id="69cea-152">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="69cea-152">2048 characters</span></span>|<span data-ttu-id="69cea-153">✔</span><span class="sxs-lookup"><span data-stu-id="69cea-153">✔</span></span>|<span data-ttu-id="69cea-154">Die https:// URL zur Datenschutzrichtlinie des Entwicklers.</span><span class="sxs-lookup"><span data-stu-id="69cea-154">The https:// URL to the developer's privacy policy.</span></span>|
|`termsOfUseUrl`|<span data-ttu-id="69cea-155">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="69cea-155">2048 characters</span></span>|<span data-ttu-id="69cea-156">✔</span><span class="sxs-lookup"><span data-stu-id="69cea-156">✔</span></span>|<span data-ttu-id="69cea-157">Die https:// URL zu den Nutzungsbedingungen des Entwicklers.</span><span class="sxs-lookup"><span data-stu-id="69cea-157">The https:// URL to the developer's terms of use.</span></span>|
|`mpnId`|<span data-ttu-id="69cea-158">10 Zeichen</span><span class="sxs-lookup"><span data-stu-id="69cea-158">10 characters</span></span>|<span data-ttu-id="69cea-159">✔</span><span class="sxs-lookup"><span data-stu-id="69cea-159">✔</span></span>|<span data-ttu-id="69cea-160">**Optional** Die Microsoft Partner Network-ID, die die Partnerorganisation identifiziert, die die App erstellt.</span><span class="sxs-lookup"><span data-stu-id="69cea-160">**Optional** The Microsoft Partner Network ID that identifies the partner organization building the app.</span></span>|

## <a name="localizationinfo"></a><span data-ttu-id="69cea-161">localizationInfo</span><span class="sxs-lookup"><span data-stu-id="69cea-161">localizationInfo</span></span>

<span data-ttu-id="69cea-162">**Optional**</span><span class="sxs-lookup"><span data-stu-id="69cea-162">**Optional**</span></span>

<span data-ttu-id="69cea-163">Ermöglicht die Angabe einer Standardsprache sowie Zeiger auf zusätzliche Sprachdateien.</span><span class="sxs-lookup"><span data-stu-id="69cea-163">Allows the specification of a default language, as well as pointers to additional language files.</span></span> <span data-ttu-id="69cea-164">Siehe [Lokalisierung](~/concepts/build-and-test/apps-localization.md).</span><span class="sxs-lookup"><span data-stu-id="69cea-164">See [localization](~/concepts/build-and-test/apps-localization.md).</span></span>

|<span data-ttu-id="69cea-165">Name</span><span class="sxs-lookup"><span data-stu-id="69cea-165">Name</span></span>| <span data-ttu-id="69cea-166">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="69cea-166">Maximum size</span></span> | <span data-ttu-id="69cea-167">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="69cea-167">Required</span></span> | <span data-ttu-id="69cea-168">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="69cea-168">Description</span></span>|
|---|---|---|---|
|`defaultLanguageTag`|<span data-ttu-id="69cea-169">4 Zeichen</span><span class="sxs-lookup"><span data-stu-id="69cea-169">4 characters</span></span>|<span data-ttu-id="69cea-170">✔</span><span class="sxs-lookup"><span data-stu-id="69cea-170">✔</span></span>|<span data-ttu-id="69cea-171">Das Sprachtag der Zeichenfolgen in dieser Manifestdatei auf oberster Ebene.</span><span class="sxs-lookup"><span data-stu-id="69cea-171">The language tag of the strings in this top level manifest file.</span></span>|

### <a name="localizationinfoadditionallanguages"></a><span data-ttu-id="69cea-172">localizationInfo.additionalLanguages</span><span class="sxs-lookup"><span data-stu-id="69cea-172">localizationInfo.additionalLanguages</span></span>

<span data-ttu-id="69cea-173">Ein Array von Objekten, die zusätzliche Sprachübersetzungen angeben.</span><span class="sxs-lookup"><span data-stu-id="69cea-173">An array of objects specifying additional language translations.</span></span>

|<span data-ttu-id="69cea-174">Name</span><span class="sxs-lookup"><span data-stu-id="69cea-174">Name</span></span>| <span data-ttu-id="69cea-175">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="69cea-175">Maximum size</span></span> | <span data-ttu-id="69cea-176">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="69cea-176">Required</span></span> | <span data-ttu-id="69cea-177">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="69cea-177">Description</span></span>|
|---|---|---|---|
|`languageTag`|<span data-ttu-id="69cea-178">4 Zeichen</span><span class="sxs-lookup"><span data-stu-id="69cea-178">4 characters</span></span>|<span data-ttu-id="69cea-179">✔</span><span class="sxs-lookup"><span data-stu-id="69cea-179">✔</span></span>|<span data-ttu-id="69cea-180">Das Sprachtag der Zeichenfolgen in der bereitgestellten Datei.</span><span class="sxs-lookup"><span data-stu-id="69cea-180">The language tag of the strings in the provided file.</span></span>|
|`file`|<span data-ttu-id="69cea-181">4 Zeichen</span><span class="sxs-lookup"><span data-stu-id="69cea-181">4 characters</span></span>|<span data-ttu-id="69cea-182">✔</span><span class="sxs-lookup"><span data-stu-id="69cea-182">✔</span></span>|<span data-ttu-id="69cea-183">Ein relativer Dateipfad zu einer JSON-Datei, die die übersetzten Zeichenfolgen enthält.</span><span class="sxs-lookup"><span data-stu-id="69cea-183">A relative file path to a the .json file containing the translated strings.</span></span>|

## <a name="name"></a><span data-ttu-id="69cea-184">name</span><span class="sxs-lookup"><span data-stu-id="69cea-184">name</span></span>

<span data-ttu-id="69cea-185">**Required**</span><span class="sxs-lookup"><span data-stu-id="69cea-185">**Required**</span></span>

<span data-ttu-id="69cea-186">Der Name Ihrer App-Erfahrung, der Benutzern in der Teams-Erfahrung angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="69cea-186">The name of your app experience, displayed to users in the Teams experience.</span></span> <span data-ttu-id="69cea-187">Bei an AppSource übermittelten Apps müssen diese Werte mit den Informationen in Ihrem Eintrag "AppSource" übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="69cea-187">For apps submitted to AppSource, these values must match the information in your AppSource entry.</span></span> <span data-ttu-id="69cea-188">Die Werte von `short` und sollten nicht identisch `full` sein.</span><span class="sxs-lookup"><span data-stu-id="69cea-188">The values of `short` and `full` should not be the same.</span></span>

|<span data-ttu-id="69cea-189">Name</span><span class="sxs-lookup"><span data-stu-id="69cea-189">Name</span></span>| <span data-ttu-id="69cea-190">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="69cea-190">Maximum size</span></span> | <span data-ttu-id="69cea-191">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="69cea-191">Required</span></span> | <span data-ttu-id="69cea-192">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="69cea-192">Description</span></span>|
|---|---|---|---|
|`short`|<span data-ttu-id="69cea-193">30 Zeichen</span><span class="sxs-lookup"><span data-stu-id="69cea-193">30 characters</span></span>|<span data-ttu-id="69cea-194">✔</span><span class="sxs-lookup"><span data-stu-id="69cea-194">✔</span></span>|<span data-ttu-id="69cea-195">Der kurze Anzeigename für die App.</span><span class="sxs-lookup"><span data-stu-id="69cea-195">The short display name for the app.</span></span>|
|`full`|<span data-ttu-id="69cea-196">100 Zeichen</span><span class="sxs-lookup"><span data-stu-id="69cea-196">100 characters</span></span>||<span data-ttu-id="69cea-197">Der vollständige Name der App, der verwendet wird, wenn der vollständige Name der App 30 Zeichen überschreitet.</span><span class="sxs-lookup"><span data-stu-id="69cea-197">The full name of the app, used if the full app name exceeds 30 characters.</span></span>|

## <a name="description"></a><span data-ttu-id="69cea-198">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="69cea-198">description</span></span>

<span data-ttu-id="69cea-199">**Required**</span><span class="sxs-lookup"><span data-stu-id="69cea-199">**Required**</span></span>

<span data-ttu-id="69cea-200">Beschreibt Ihre App für Benutzer.</span><span class="sxs-lookup"><span data-stu-id="69cea-200">Describes your app to users.</span></span> <span data-ttu-id="69cea-201">Bei an AppSource übermittelten Apps müssen diese Werte mit den Informationen in Ihrem Eintrag "AppSource" übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="69cea-201">For apps submitted to AppSource, these values must match the information in your AppSource entry.</span></span>

<span data-ttu-id="69cea-202">Stellen Sie sicher, dass Ihre Beschreibung Ihre Erfahrung genau beschreibt, und stellen Sie Informationen zur Verfügung, mit deren Hilfe potenzielle Kunden ihre Erfahrung besser verstehen können.</span><span class="sxs-lookup"><span data-stu-id="69cea-202">Ensure that your description accurately describes your experience and provides information to help potential customers understand what your experience does.</span></span> <span data-ttu-id="69cea-203">Beachten Sie auch in der vollständigen Beschreibung, ob ein externes Konto für die Verwendung erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="69cea-203">You should also note, in the full description, if an external account is required for use.</span></span> <span data-ttu-id="69cea-204">Die Werte von `short` und sollten nicht identisch `full` sein.</span><span class="sxs-lookup"><span data-stu-id="69cea-204">The values of `short` and `full` should not be the same.</span></span>  <span data-ttu-id="69cea-205">Die kurz beschriebene Beschreibung darf nicht innerhalb der langen Beschreibung wiederholt werden und darf keinen anderen App-Namen enthalten.</span><span class="sxs-lookup"><span data-stu-id="69cea-205">Your short description must not be repeated within the long description and must not include any other app name.</span></span>

|<span data-ttu-id="69cea-206">Name</span><span class="sxs-lookup"><span data-stu-id="69cea-206">Name</span></span>| <span data-ttu-id="69cea-207">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="69cea-207">Maximum size</span></span> | <span data-ttu-id="69cea-208">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="69cea-208">Required</span></span> | <span data-ttu-id="69cea-209">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="69cea-209">Description</span></span>|
|---|---|---|---|
|`short`|<span data-ttu-id="69cea-210">80 Zeichen</span><span class="sxs-lookup"><span data-stu-id="69cea-210">80 characters</span></span>|<span data-ttu-id="69cea-211">✔</span><span class="sxs-lookup"><span data-stu-id="69cea-211">✔</span></span>|<span data-ttu-id="69cea-212">Eine kurze Beschreibung Ihrer App-Erfahrung, die bei begrenztem Platz verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="69cea-212">A short description of your app experience, used when space is limited.</span></span>|
|`full`|<span data-ttu-id="69cea-213">4000 Zeichen</span><span class="sxs-lookup"><span data-stu-id="69cea-213">4000 characters</span></span>|<span data-ttu-id="69cea-214">✔</span><span class="sxs-lookup"><span data-stu-id="69cea-214">✔</span></span>|<span data-ttu-id="69cea-215">Die vollständige Beschreibung Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="69cea-215">The full description of your app.</span></span>|

## <a name="icons"></a><span data-ttu-id="69cea-216">Symbole</span><span class="sxs-lookup"><span data-stu-id="69cea-216">icons</span></span>

<span data-ttu-id="69cea-217">**Required**</span><span class="sxs-lookup"><span data-stu-id="69cea-217">**Required**</span></span>

<span data-ttu-id="69cea-218">Symbole, die in der Teams-App verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="69cea-218">Icons used within the Teams app.</span></span> <span data-ttu-id="69cea-219">Die Symboldateien müssen als Teil des Uploadpakets enthalten sein.</span><span class="sxs-lookup"><span data-stu-id="69cea-219">The icon files must be included as part of the upload package.</span></span>

|<span data-ttu-id="69cea-220">Name</span><span class="sxs-lookup"><span data-stu-id="69cea-220">Name</span></span>| <span data-ttu-id="69cea-221">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="69cea-221">Maximum size</span></span> | <span data-ttu-id="69cea-222">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="69cea-222">Required</span></span> | <span data-ttu-id="69cea-223">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="69cea-223">Description</span></span>|
|---|---|---|---|
|`outline`|<span data-ttu-id="69cea-224">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="69cea-224">2048 characters</span></span>|<span data-ttu-id="69cea-225">✔</span><span class="sxs-lookup"><span data-stu-id="69cea-225">✔</span></span>|<span data-ttu-id="69cea-226">Ein relativer Dateipfad zu einem transparenten 32 x 32 PNG-Gliederungssymbol.</span><span class="sxs-lookup"><span data-stu-id="69cea-226">A relative file path to a transparent 32x32 PNG outline icon.</span></span>|
|`color`|<span data-ttu-id="69cea-227">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="69cea-227">2048 characters</span></span>|<span data-ttu-id="69cea-228">✔</span><span class="sxs-lookup"><span data-stu-id="69cea-228">✔</span></span>|<span data-ttu-id="69cea-229">Ein relativer Dateipfad zu einem vollfarbigen 192 x 192 PNG-Symbol.</span><span class="sxs-lookup"><span data-stu-id="69cea-229">A relative file path to a full color 192x192 PNG icon.</span></span>|

## <a name="accentcolor"></a><span data-ttu-id="69cea-230">accentColor</span><span class="sxs-lookup"><span data-stu-id="69cea-230">accentColor</span></span>

<span data-ttu-id="69cea-231">**Erforderlich** &ndash; Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="69cea-231">**Required** &ndash; String</span></span>

<span data-ttu-id="69cea-232">Eine Farbe, die in Verbindung mit und als Hintergrund für Ihre Gliederungssymbole verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="69cea-232">A color to use in conjunction with and as a background for your outline icons.</span></span>

<span data-ttu-id="69cea-233">Der Wert muss ein gültiger #A0 sein, der mit "#" beginnt, z. B. `#4464ee` .</span><span class="sxs-lookup"><span data-stu-id="69cea-233">The value must be a valid HTML color code starting with '#', for example `#4464ee`.</span></span>

## <a name="configurabletabs"></a><span data-ttu-id="69cea-234">configurableTabs</span><span class="sxs-lookup"><span data-stu-id="69cea-234">configurableTabs</span></span>

<span data-ttu-id="69cea-235">**Optional**</span><span class="sxs-lookup"><span data-stu-id="69cea-235">**Optional**</span></span>

<span data-ttu-id="69cea-236">Wird verwendet, wenn Ihre App über eine Registerkartenerfahrung im Teamkanal verfügt, die eine zusätzliche Konfiguration erfordert, bevor sie hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="69cea-236">Used when your app experience has a team channel tab experience that requires extra configuration before it is added.</span></span> <span data-ttu-id="69cea-237">Konfigurierbare Registerkarten werden nur im Bereich "Teams" unterstützt, und derzeit wird nur eine Registerkarte pro App unterstützt.</span><span class="sxs-lookup"><span data-stu-id="69cea-237">Configurable tabs are supported only in the teams scope, and currently only one tab per app is supported.</span></span>

<span data-ttu-id="69cea-238">Das Objekt ist ein Array mit allen Elementen des Typs `object` .</span><span class="sxs-lookup"><span data-stu-id="69cea-238">The object is an array with all elements of the type `object`.</span></span> <span data-ttu-id="69cea-239">Dieser Block ist nur für Lösungen erforderlich, die eine konfigurierbare Kanalregisterkartenlösung bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="69cea-239">This block is required only for solutions that provide a configurable channel tab solution.</span></span>

|<span data-ttu-id="69cea-240">Name</span><span class="sxs-lookup"><span data-stu-id="69cea-240">Name</span></span>| <span data-ttu-id="69cea-241">Typ</span><span class="sxs-lookup"><span data-stu-id="69cea-241">Type</span></span>| <span data-ttu-id="69cea-242">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="69cea-242">Maximum size</span></span> | <span data-ttu-id="69cea-243">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="69cea-243">Required</span></span> | <span data-ttu-id="69cea-244">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="69cea-244">Description</span></span>|
|---|---|---|---|---|
|`configurationUrl`|<span data-ttu-id="69cea-245">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="69cea-245">String</span></span>|<span data-ttu-id="69cea-246">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="69cea-246">2048 characters</span></span>|<span data-ttu-id="69cea-247">✔</span><span class="sxs-lookup"><span data-stu-id="69cea-247">✔</span></span>|<span data-ttu-id="69cea-248">Die https:// URL, die beim Konfigurieren der Registerkarte verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="69cea-248">The https:// URL to use when configuring the tab.</span></span>|
|`canUpdateConfiguration`|<span data-ttu-id="69cea-249">Boolesch</span><span class="sxs-lookup"><span data-stu-id="69cea-249">Boolean</span></span>|||<span data-ttu-id="69cea-250">Ein Wert, der angibt, ob eine Instanz der Konfiguration der Registerkarte vom Benutzer nach der Erstellung aktualisiert werden kann.</span><span class="sxs-lookup"><span data-stu-id="69cea-250">A value indicating whether an instance of the tab's configuration can be updated by the user after creation.</span></span> <span data-ttu-id="69cea-251">Standard: `true`</span><span class="sxs-lookup"><span data-stu-id="69cea-251">Default: `true`</span></span>|
|`scopes`|<span data-ttu-id="69cea-252">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="69cea-252">Array of enum</span></span>|<span data-ttu-id="69cea-253">1 </span><span class="sxs-lookup"><span data-stu-id="69cea-253">1</span></span>|<span data-ttu-id="69cea-254">✔</span><span class="sxs-lookup"><span data-stu-id="69cea-254">✔</span></span>|<span data-ttu-id="69cea-255">Derzeit unterstützen konfigurierbare Registerkarten nur die `team` Bereiche `groupchat` und die Bereiche.</span><span class="sxs-lookup"><span data-stu-id="69cea-255">Currently, configurable tabs support only the `team` and `groupchat` scopes.</span></span> |
|`sharePointPreviewImage`|<span data-ttu-id="69cea-256">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="69cea-256">String</span></span>|<span data-ttu-id="69cea-257">2048</span><span class="sxs-lookup"><span data-stu-id="69cea-257">2048</span></span>||<span data-ttu-id="69cea-258">Ein relativer Dateipfad zu einem Vorschaubild für Registerkarten zur Verwendung in SharePoint.</span><span class="sxs-lookup"><span data-stu-id="69cea-258">A relative file path to a tab preview image for use in SharePoint.</span></span> <span data-ttu-id="69cea-259">Größe 1024 x 768.</span><span class="sxs-lookup"><span data-stu-id="69cea-259">Size 1024x768.</span></span> |
|`supportedSharePointHosts`|<span data-ttu-id="69cea-260">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="69cea-260">Array of enum</span></span>|<span data-ttu-id="69cea-261">1 </span><span class="sxs-lookup"><span data-stu-id="69cea-261">1</span></span>||<span data-ttu-id="69cea-262">Definiert, wie Ihre Registerkarte in SharePoint verfügbar gemacht wird.</span><span class="sxs-lookup"><span data-stu-id="69cea-262">Defines how your tab will be made available in SharePoint.</span></span> <span data-ttu-id="69cea-263">Optionen sind `sharePointFullPage` und `sharePointWebPart`</span><span class="sxs-lookup"><span data-stu-id="69cea-263">Options are `sharePointFullPage` and `sharePointWebPart`</span></span> |

## <a name="statictabs"></a><span data-ttu-id="69cea-264">staticTabs</span><span class="sxs-lookup"><span data-stu-id="69cea-264">staticTabs</span></span>

<span data-ttu-id="69cea-265">**Optional**</span><span class="sxs-lookup"><span data-stu-id="69cea-265">**Optional**</span></span>

<span data-ttu-id="69cea-266">Definiert eine Reihe von Registerkarten, die standardmäßig "angeheftet" werden können, ohne dass der Benutzer sie manuell hinzufügen muss.</span><span class="sxs-lookup"><span data-stu-id="69cea-266">Defines a set of tabs that can be "pinned" by default, without the user adding them manually.</span></span> <span data-ttu-id="69cea-267">Statische Registerkarten, die im Bereich deklariert sind, werden immer an die persönliche Benutzererfahrung `personal` der App angeheftet.</span><span class="sxs-lookup"><span data-stu-id="69cea-267">Static tabs declared in `personal` scope are always pinned to the app's personal experience.</span></span> <span data-ttu-id="69cea-268">Im Bereich deklarierte statische `team` Registerkarten werden derzeit nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="69cea-268">Static tabs declared in the `team` scope are currently not supported.</span></span>

<span data-ttu-id="69cea-269">Das Objekt ist ein Array (maximal 16 Elemente) mit allen Elementen des Typs `object` .</span><span class="sxs-lookup"><span data-stu-id="69cea-269">The object is an array (maximum of 16 elements) with all elements of the type `object`.</span></span> <span data-ttu-id="69cea-270">Dieser Block ist nur für Lösungen erforderlich, die eine Lösung für statische Registerkarten bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="69cea-270">This block is required only for solutions that provide a static tab solution.</span></span>

|<span data-ttu-id="69cea-271">Name</span><span class="sxs-lookup"><span data-stu-id="69cea-271">Name</span></span>| <span data-ttu-id="69cea-272">Typ</span><span class="sxs-lookup"><span data-stu-id="69cea-272">Type</span></span>| <span data-ttu-id="69cea-273">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="69cea-273">Maximum size</span></span> | <span data-ttu-id="69cea-274">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="69cea-274">Required</span></span> | <span data-ttu-id="69cea-275">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="69cea-275">Description</span></span>|
|---|---|---|---|---|
|`entityId`|<span data-ttu-id="69cea-276">String</span><span class="sxs-lookup"><span data-stu-id="69cea-276">String</span></span>|<span data-ttu-id="69cea-277">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="69cea-277">64 characters</span></span>|<span data-ttu-id="69cea-278">✔</span><span class="sxs-lookup"><span data-stu-id="69cea-278">✔</span></span>|<span data-ttu-id="69cea-279">Ein eindeutiger Bezeichner für die Entität, die auf der Registerkarte angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="69cea-279">A unique identifier for the entity that the tab displays.</span></span>|
|`name`|<span data-ttu-id="69cea-280">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="69cea-280">String</span></span>|<span data-ttu-id="69cea-281">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="69cea-281">128 characters</span></span>|<span data-ttu-id="69cea-282">✔</span><span class="sxs-lookup"><span data-stu-id="69cea-282">✔</span></span>|<span data-ttu-id="69cea-283">Der Anzeigename der Registerkarte in der Kanalschnittstelle.</span><span class="sxs-lookup"><span data-stu-id="69cea-283">The display name of the tab in the channel interface.</span></span>|
|`contentUrl`|<span data-ttu-id="69cea-284">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="69cea-284">String</span></span>|<span data-ttu-id="69cea-285">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="69cea-285">2048 characters</span></span>|<span data-ttu-id="69cea-286">✔</span><span class="sxs-lookup"><span data-stu-id="69cea-286">✔</span></span>|<span data-ttu-id="69cea-287">Die https:// URL, die auf die Entitätsbenutzeroberfläche verweist, die im Zeichenbereich von Teams angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="69cea-287">The https:// URL that points to the entity UI to be displayed in the Teams canvas.</span></span>|
|`websiteUrl`|<span data-ttu-id="69cea-288">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="69cea-288">String</span></span>|<span data-ttu-id="69cea-289">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="69cea-289">2048 characters</span></span>||<span data-ttu-id="69cea-290">Die https:// URL, auf die zeigen soll, wenn sich ein Benutzer für die Anzeige in einem Browser entscheidet.</span><span class="sxs-lookup"><span data-stu-id="69cea-290">The https:// URL to point at if a user opts to view in a browser.</span></span>|
|`scopes`|<span data-ttu-id="69cea-291">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="69cea-291">Array of enum</span></span>|<span data-ttu-id="69cea-292">1 </span><span class="sxs-lookup"><span data-stu-id="69cea-292">1</span></span>|<span data-ttu-id="69cea-293">✔</span><span class="sxs-lookup"><span data-stu-id="69cea-293">✔</span></span>|<span data-ttu-id="69cea-294">Derzeit unterstützen statische Registerkarten nur den Bereich, d. h., er kann nur als Teil der `personal` persönlichen Erfahrung bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="69cea-294">Currently, static tabs support only the `personal` scope, which means it can be provisioned only as part of the personal experience.</span></span>|

## <a name="bots"></a><span data-ttu-id="69cea-295">Bots</span><span class="sxs-lookup"><span data-stu-id="69cea-295">bots</span></span>

<span data-ttu-id="69cea-296">**Optional**</span><span class="sxs-lookup"><span data-stu-id="69cea-296">**Optional**</span></span>

<span data-ttu-id="69cea-297">Definiert eine Botlösung zusammen mit optionalen Informationen wie z. B. Standardbefehlseigenschaften.</span><span class="sxs-lookup"><span data-stu-id="69cea-297">Defines a bot solution, along with optional information such as default command properties.</span></span>

<span data-ttu-id="69cea-298">Das Objekt ist ein Array (maximal 1 Element ist derzeit nur ein Bot pro App zulässig) mit allen Elementen &mdash; des Typs `object` .</span><span class="sxs-lookup"><span data-stu-id="69cea-298">The object is an array (maximum of only 1 element&mdash;currently only one bot is allowed per app) with all elements of the type `object`.</span></span> <span data-ttu-id="69cea-299">Dieser Block ist nur für Lösungen erforderlich, die eine Boterfahrung bieten.</span><span class="sxs-lookup"><span data-stu-id="69cea-299">This block is required only for solutions that provide a bot experience.</span></span>

|<span data-ttu-id="69cea-300">Name</span><span class="sxs-lookup"><span data-stu-id="69cea-300">Name</span></span>| <span data-ttu-id="69cea-301">Typ</span><span class="sxs-lookup"><span data-stu-id="69cea-301">Type</span></span>| <span data-ttu-id="69cea-302">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="69cea-302">Maximum size</span></span> | <span data-ttu-id="69cea-303">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="69cea-303">Required</span></span> | <span data-ttu-id="69cea-304">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="69cea-304">Description</span></span>|
|---|---|---|---|---|
|`botId`|<span data-ttu-id="69cea-305">String</span><span class="sxs-lookup"><span data-stu-id="69cea-305">String</span></span>|<span data-ttu-id="69cea-306">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="69cea-306">64 characters</span></span>|<span data-ttu-id="69cea-307">✔</span><span class="sxs-lookup"><span data-stu-id="69cea-307">✔</span></span>|<span data-ttu-id="69cea-308">Die eindeutige Microsoft-App-ID für den Bot, wie bei Bot Framework registriert.</span><span class="sxs-lookup"><span data-stu-id="69cea-308">The unique Microsoft app ID for the bot as registered with the Bot Framework.</span></span> <span data-ttu-id="69cea-309">Dies kann mit der allgemeinen [App-ID identisch sein.](#id)</span><span class="sxs-lookup"><span data-stu-id="69cea-309">This may well be the same as the overall [app ID](#id).</span></span>|
|`needsChannelSelector`|<span data-ttu-id="69cea-310">Boolesch</span><span class="sxs-lookup"><span data-stu-id="69cea-310">Boolean</span></span>|||<span data-ttu-id="69cea-311">Beschreibt, ob der Bot einen Benutzerhinweis verwendet, um den Bot einem bestimmten Kanal hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="69cea-311">Describes whether or not the bot utilizes a user hint to add the bot to a specific channel.</span></span> <span data-ttu-id="69cea-312">Standard: `false`</span><span class="sxs-lookup"><span data-stu-id="69cea-312">Default: `false`</span></span>|
|`isNotificationOnly`|<span data-ttu-id="69cea-313">Boolesch</span><span class="sxs-lookup"><span data-stu-id="69cea-313">Boolean</span></span>|||<span data-ttu-id="69cea-314">Gibt an, ob ein Bot ein unidirektionaler Bot ausschließlich für Benachrichtigungen ist (im Gegensatz zu einem dialogorientierten Bot).</span><span class="sxs-lookup"><span data-stu-id="69cea-314">Indicates whether a bot is a one-way, notification-only bot, as opposed to a conversational bot.</span></span> <span data-ttu-id="69cea-315">Standard: `false`</span><span class="sxs-lookup"><span data-stu-id="69cea-315">Default: `false`</span></span>|
|`supportsFiles`|<span data-ttu-id="69cea-316">Boolesch</span><span class="sxs-lookup"><span data-stu-id="69cea-316">Boolean</span></span>|||<span data-ttu-id="69cea-317">Gibt an, ob der Bot die Möglichkeit zum Hochladen/Herunterladen von Dateien in persönliche Chats unterstützt.</span><span class="sxs-lookup"><span data-stu-id="69cea-317">Indicates whether the bot supports the ability to upload/download files in personal chat.</span></span> <span data-ttu-id="69cea-318">Standard: `false`</span><span class="sxs-lookup"><span data-stu-id="69cea-318">Default: `false`</span></span>|
|`scopes`|<span data-ttu-id="69cea-319">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="69cea-319">Array of enum</span></span>|<span data-ttu-id="69cea-320">3</span><span class="sxs-lookup"><span data-stu-id="69cea-320">3</span></span>|<span data-ttu-id="69cea-321">✔</span><span class="sxs-lookup"><span data-stu-id="69cea-321">✔</span></span>|<span data-ttu-id="69cea-322">Gibt an, ob der Bot eine Umgebung im Kontext eines Kanals in einem `team` oder Gruppenchat (`groupchat`) ist, oder aber eine Umgebung einzig für einen bestimmten Benutzer (`personal`).</span><span class="sxs-lookup"><span data-stu-id="69cea-322">Specifies whether the bot offers an experience in the context of a channel in a `team`, in a group chat (`groupchat`), or an experience scoped to an individual user alone (`personal`).</span></span> <span data-ttu-id="69cea-323">Diese Optionen sind nicht exklusiv.</span><span class="sxs-lookup"><span data-stu-id="69cea-323">These options are non-exclusive.</span></span>|

### <a name="botscommandlists"></a><span data-ttu-id="69cea-324">bots.commandLists</span><span class="sxs-lookup"><span data-stu-id="69cea-324">bots.commandLists</span></span>

<span data-ttu-id="69cea-325">Eine optionale Liste von Befehlen, die Ihr Bot Benutzern empfehlen kann.</span><span class="sxs-lookup"><span data-stu-id="69cea-325">An optional list of commands that your bot can recommend to users.</span></span> <span data-ttu-id="69cea-326">Das Objekt ist ein Array (maximal 2 Elemente) mit allen Elementen des Typs; Sie müssen eine separate Befehlsliste für jeden Bereich definieren, der von `object` Ihrem Bot unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="69cea-326">The object is an array (maximum of 2 elements) with all elements of type `object`; you must define a separate command list for each scope that your bot supports.</span></span> <span data-ttu-id="69cea-327">Weitere [Informationen finden Sie in den Bot-Menüs.](~/bots/how-to/create-a-bot-commands-menu.md)</span><span class="sxs-lookup"><span data-stu-id="69cea-327">See [Bot menus](~/bots/how-to/create-a-bot-commands-menu.md) for more information.</span></span>

|<span data-ttu-id="69cea-328">Name</span><span class="sxs-lookup"><span data-stu-id="69cea-328">Name</span></span>| <span data-ttu-id="69cea-329">Typ</span><span class="sxs-lookup"><span data-stu-id="69cea-329">Type</span></span>| <span data-ttu-id="69cea-330">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="69cea-330">Maximum size</span></span> | <span data-ttu-id="69cea-331">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="69cea-331">Required</span></span> | <span data-ttu-id="69cea-332">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="69cea-332">Description</span></span>|
|---|---|---|---|---|
|`items.scopes`|<span data-ttu-id="69cea-333">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="69cea-333">array of enum</span></span>|<span data-ttu-id="69cea-334">3</span><span class="sxs-lookup"><span data-stu-id="69cea-334">3</span></span>|<span data-ttu-id="69cea-335">✔</span><span class="sxs-lookup"><span data-stu-id="69cea-335">✔</span></span>|<span data-ttu-id="69cea-336">Gibt den Bereich an, für den die Befehlsliste gültig ist.</span><span class="sxs-lookup"><span data-stu-id="69cea-336">Specifies the scope for which the command list is valid.</span></span> <span data-ttu-id="69cea-337">Mögliche Optionen sind `team`, `personal` und `groupchat`.</span><span class="sxs-lookup"><span data-stu-id="69cea-337">Options are `team`, `personal`, and `groupchat`.</span></span>|
|`items.commands`|<span data-ttu-id="69cea-338">Array von Objekten</span><span class="sxs-lookup"><span data-stu-id="69cea-338">array of objects</span></span>|<span data-ttu-id="69cea-339">10 </span><span class="sxs-lookup"><span data-stu-id="69cea-339">10</span></span>|<span data-ttu-id="69cea-340">✔</span><span class="sxs-lookup"><span data-stu-id="69cea-340">✔</span></span>|<span data-ttu-id="69cea-341">Ein Array von Befehlen, die der Bot unterstützt:</span><span class="sxs-lookup"><span data-stu-id="69cea-341">An array of commands the bot supports:</span></span><br><span data-ttu-id="69cea-342">`title`: Name des Bot-Befehls (string, 32)</span><span class="sxs-lookup"><span data-stu-id="69cea-342">`title`: the bot command name (string, 32)</span></span><br><span data-ttu-id="69cea-343">`description`: einfache Beschreibung oder Beispiel für die Befehlssyntax und zugehörige Argumente (string, 128)</span><span class="sxs-lookup"><span data-stu-id="69cea-343">`description`: a simple description or example of the command syntax and its argument (string, 128)</span></span>|

## <a name="connectors"></a><span data-ttu-id="69cea-344">Connectors</span><span class="sxs-lookup"><span data-stu-id="69cea-344">connectors</span></span>

<span data-ttu-id="69cea-345">**Optional**</span><span class="sxs-lookup"><span data-stu-id="69cea-345">**Optional**</span></span>

<span data-ttu-id="69cea-346">Der `connectors` Block definiert einen Office 365-Connector für die App.</span><span class="sxs-lookup"><span data-stu-id="69cea-346">The `connectors` block defines an Office 365 Connector for the app.</span></span>

<span data-ttu-id="69cea-347">Das Objekt ist ein Array (maximal 1 Element) mit allen Elementen vom `object` Typ .</span><span class="sxs-lookup"><span data-stu-id="69cea-347">The object is an array (maximum of 1 element) with all elements of type `object`.</span></span> <span data-ttu-id="69cea-348">Dieser Block ist nur für Lösungen erforderlich, die einen Connector bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="69cea-348">This block is required only for solutions that provide a Connector.</span></span>

|<span data-ttu-id="69cea-349">Name</span><span class="sxs-lookup"><span data-stu-id="69cea-349">Name</span></span>| <span data-ttu-id="69cea-350">Typ</span><span class="sxs-lookup"><span data-stu-id="69cea-350">Type</span></span>| <span data-ttu-id="69cea-351">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="69cea-351">Maximum size</span></span> | <span data-ttu-id="69cea-352">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="69cea-352">Required</span></span> | <span data-ttu-id="69cea-353">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="69cea-353">Description</span></span>|
|---|---|---|---|---|
|`configurationUrl`|<span data-ttu-id="69cea-354">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="69cea-354">String</span></span>|<span data-ttu-id="69cea-355">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="69cea-355">2048 characters</span></span>|<span data-ttu-id="69cea-356">✔</span><span class="sxs-lookup"><span data-stu-id="69cea-356">✔</span></span>|<span data-ttu-id="69cea-357">Die https:// URL, die beim Konfigurieren des Connectors verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="69cea-357">The https:// URL to use when configuring the connector.</span></span>|
|`connectorId`|<span data-ttu-id="69cea-358">String</span><span class="sxs-lookup"><span data-stu-id="69cea-358">String</span></span>|<span data-ttu-id="69cea-359">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="69cea-359">64 characters</span></span>|<span data-ttu-id="69cea-360">✔</span><span class="sxs-lookup"><span data-stu-id="69cea-360">✔</span></span>|<span data-ttu-id="69cea-361">Ein eindeutiger Bezeichner für den Connector, der seiner ID im [Connectors Developer Dashboard entspricht.](https://aka.ms/connectorsdashboard)</span><span class="sxs-lookup"><span data-stu-id="69cea-361">A unique identifier for the Connector that matches its ID in the [Connectors Developer Dashboard](https://aka.ms/connectorsdashboard).</span></span>|
|`scopes`|<span data-ttu-id="69cea-362">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="69cea-362">Array of enum</span></span>|<span data-ttu-id="69cea-363">1 </span><span class="sxs-lookup"><span data-stu-id="69cea-363">1</span></span>|<span data-ttu-id="69cea-364">✔</span><span class="sxs-lookup"><span data-stu-id="69cea-364">✔</span></span>|<span data-ttu-id="69cea-365">Gibt an, ob der Connector eine Benutzeroberfläche im Kontext eines Kanals in einem oder eine Benutzeroberfläche bietet, die auf einen einzelnen Benutzer `team` begrenzt ist ( `personal` ).</span><span class="sxs-lookup"><span data-stu-id="69cea-365">Specifies whether the Connector offers an experience in the context of a channel in a `team`, or an experience scoped to an individual user alone (`personal`).</span></span> <span data-ttu-id="69cea-366">Derzeit wird nur `team` der Bereich unterstützt.</span><span class="sxs-lookup"><span data-stu-id="69cea-366">Currently, only the `team` scope is supported.</span></span>|

## <a name="composeextensions"></a><span data-ttu-id="69cea-367">composeExtensions</span><span class="sxs-lookup"><span data-stu-id="69cea-367">composeExtensions</span></span>

<span data-ttu-id="69cea-368">**Optional**</span><span class="sxs-lookup"><span data-stu-id="69cea-368">**Optional**</span></span>

<span data-ttu-id="69cea-369">Definiert eine Messagingerweiterung für die App.</span><span class="sxs-lookup"><span data-stu-id="69cea-369">Defines a messaging extension for the app.</span></span>

> [!NOTE]
> <span data-ttu-id="69cea-370">Der Name des Features wurde im November 2017 von "Verfassenerweiterung" in "Messagingerweiterung" geändert, aber der Manifestname bleibt unverändert, damit vorhandene Erweiterungen weiterhin funktionieren.</span><span class="sxs-lookup"><span data-stu-id="69cea-370">The name of the feature was changed from "compose extension" to "messaging extension" in November, 2017, but the manifest name remains the same so that existing extensions continue to function.</span></span>

<span data-ttu-id="69cea-371">Das Objekt ist ein Array (maximal 1 Element) mit allen Elementen vom `object` Typ .</span><span class="sxs-lookup"><span data-stu-id="69cea-371">The object is an array (maximum of 1 element) with all elements of type `object`.</span></span> <span data-ttu-id="69cea-372">Dieser Block ist nur für Lösungen erforderlich, die eine Messagingerweiterung bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="69cea-372">This block is required only for solutions that provide a messaging extension.</span></span>

|<span data-ttu-id="69cea-373">Name</span><span class="sxs-lookup"><span data-stu-id="69cea-373">Name</span></span>| <span data-ttu-id="69cea-374">Typ</span><span class="sxs-lookup"><span data-stu-id="69cea-374">Type</span></span> | <span data-ttu-id="69cea-375">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="69cea-375">Maximum Size</span></span> | <span data-ttu-id="69cea-376">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="69cea-376">Required</span></span> | <span data-ttu-id="69cea-377">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="69cea-377">Description</span></span>|
|---|---|---|---|---|
|`botId`|<span data-ttu-id="69cea-378">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="69cea-378">String</span></span>|<span data-ttu-id="69cea-379">64</span><span class="sxs-lookup"><span data-stu-id="69cea-379">64</span></span>|<span data-ttu-id="69cea-380">✔</span><span class="sxs-lookup"><span data-stu-id="69cea-380">✔</span></span>|<span data-ttu-id="69cea-381">Die eindeutige Microsoft-App-ID für den Bot, der die Messagingerweiterung unterstützt, wie beim Bot Framework registriert.</span><span class="sxs-lookup"><span data-stu-id="69cea-381">The unique Microsoft app ID for the bot that backs the messaging extension, as registered with the Bot Framework.</span></span> <span data-ttu-id="69cea-382">Dies kann mit der allgemeinen [App-ID identisch sein.](#id)</span><span class="sxs-lookup"><span data-stu-id="69cea-382">This may well be the same as the overall [app ID](#id).</span></span>|
|`canUpdateConfiguration`|<span data-ttu-id="69cea-383">Boolesch</span><span class="sxs-lookup"><span data-stu-id="69cea-383">Boolean</span></span>|||<span data-ttu-id="69cea-384">Ein Wert, der angibt, ob die Konfiguration einer Messagingerweiterung vom Benutzer aktualisiert werden kann.</span><span class="sxs-lookup"><span data-stu-id="69cea-384">A value indicating whether the configuration of a messaging extension can be updated by the user.</span></span> <span data-ttu-id="69cea-385">Der Standardwert ist `false` .</span><span class="sxs-lookup"><span data-stu-id="69cea-385">The default is `false`.</span></span>|
|`commands`|<span data-ttu-id="69cea-386">Objektarray</span><span class="sxs-lookup"><span data-stu-id="69cea-386">Array of object</span></span>|<span data-ttu-id="69cea-387">10 </span><span class="sxs-lookup"><span data-stu-id="69cea-387">10</span></span>|<span data-ttu-id="69cea-388">✔</span><span class="sxs-lookup"><span data-stu-id="69cea-388">✔</span></span>|<span data-ttu-id="69cea-389">Array von Befehlen, die von der Messagingerweiterung unterstützt werden</span><span class="sxs-lookup"><span data-stu-id="69cea-389">Array of commands the messaging extension supports</span></span>|

### <a name="composeextensionscommands"></a><span data-ttu-id="69cea-390">composeExtensions.commands</span><span class="sxs-lookup"><span data-stu-id="69cea-390">composeExtensions.commands</span></span>

<span data-ttu-id="69cea-391">Ihre Messagingerweiterung sollte einen oder mehrere Befehle deklarieren.</span><span class="sxs-lookup"><span data-stu-id="69cea-391">Your messaging extension should declare one or more commands.</span></span> <span data-ttu-id="69cea-392">Jeder Befehl wird in Microsoft Teams als potenzielle Interaktion vom benutzeroberflächenbasierten Einstiegspunkt angezeigt.</span><span class="sxs-lookup"><span data-stu-id="69cea-392">Each command appears in Microsoft Teams as a potential interaction from the UI-based entry point.</span></span> <span data-ttu-id="69cea-393">Es gibt maximal 10 Befehle.</span><span class="sxs-lookup"><span data-stu-id="69cea-393">There is a maximum of 10 commands.</span></span>

<span data-ttu-id="69cea-394">Jedes Befehlselement ist ein Objekt mit der folgenden Struktur:</span><span class="sxs-lookup"><span data-stu-id="69cea-394">Each command item is an object with the following structure:</span></span>

|<span data-ttu-id="69cea-395">Name</span><span class="sxs-lookup"><span data-stu-id="69cea-395">Name</span></span>| <span data-ttu-id="69cea-396">Typ</span><span class="sxs-lookup"><span data-stu-id="69cea-396">Type</span></span>| <span data-ttu-id="69cea-397">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="69cea-397">Maximum size</span></span> | <span data-ttu-id="69cea-398">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="69cea-398">Required</span></span> | <span data-ttu-id="69cea-399">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="69cea-399">Description</span></span>|
|---|---|---|---|---|
|`id`|<span data-ttu-id="69cea-400">String</span><span class="sxs-lookup"><span data-stu-id="69cea-400">String</span></span>|<span data-ttu-id="69cea-401">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="69cea-401">64 characters</span></span>|<span data-ttu-id="69cea-402">✔</span><span class="sxs-lookup"><span data-stu-id="69cea-402">✔</span></span>|<span data-ttu-id="69cea-403">Die ID für den Befehl</span><span class="sxs-lookup"><span data-stu-id="69cea-403">The ID for the command</span></span>|
|`type`|<span data-ttu-id="69cea-404">String</span><span class="sxs-lookup"><span data-stu-id="69cea-404">String</span></span>|<span data-ttu-id="69cea-405">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="69cea-405">64 characters</span></span>||<span data-ttu-id="69cea-406">Typ des Befehls.</span><span class="sxs-lookup"><span data-stu-id="69cea-406">Type of the command.</span></span> <span data-ttu-id="69cea-407">Einer von `query` oder `action` .</span><span class="sxs-lookup"><span data-stu-id="69cea-407">One of `query` or `action`.</span></span> <span data-ttu-id="69cea-408">Standard: `query`</span><span class="sxs-lookup"><span data-stu-id="69cea-408">Default: `query`</span></span>|
|`title`|<span data-ttu-id="69cea-409">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="69cea-409">String</span></span>|<span data-ttu-id="69cea-410">32 Zeichen</span><span class="sxs-lookup"><span data-stu-id="69cea-410">32 characters</span></span>|<span data-ttu-id="69cea-411">✔</span><span class="sxs-lookup"><span data-stu-id="69cea-411">✔</span></span>|<span data-ttu-id="69cea-412">Der benutzerfreundliche Befehlsname</span><span class="sxs-lookup"><span data-stu-id="69cea-412">The user-friendly command name</span></span>|
|`description`|<span data-ttu-id="69cea-413">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="69cea-413">String</span></span>|<span data-ttu-id="69cea-414">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="69cea-414">128 characters</span></span>||<span data-ttu-id="69cea-415">Die Beschreibung, die Benutzern angezeigt wird, um den Zweck dieses Befehls anzugeben</span><span class="sxs-lookup"><span data-stu-id="69cea-415">The description that appears to users to indicate the purpose of this command</span></span>|
|`initialRun`|<span data-ttu-id="69cea-416">Boolesch</span><span class="sxs-lookup"><span data-stu-id="69cea-416">Boolean</span></span>|||<span data-ttu-id="69cea-417">Ein boolescher Wert, der angibt, ob der Befehl zunächst ohne Parameter ausgeführt werden soll.</span><span class="sxs-lookup"><span data-stu-id="69cea-417">A Boolean value that indicates whether the command should be run initially with no parameters.</span></span> <span data-ttu-id="69cea-418">Standard: `false`</span><span class="sxs-lookup"><span data-stu-id="69cea-418">Default: `false`</span></span>|
|`context`|<span data-ttu-id="69cea-419">Array von Zeichenfolgen</span><span class="sxs-lookup"><span data-stu-id="69cea-419">Array of Strings</span></span>|<span data-ttu-id="69cea-420">3</span><span class="sxs-lookup"><span data-stu-id="69cea-420">3</span></span>||<span data-ttu-id="69cea-421">Definiert, von wo aus die Nachrichtenerweiterung aufgerufen werden kann.</span><span class="sxs-lookup"><span data-stu-id="69cea-421">Defines where the message extension can be invoked from.</span></span> <span data-ttu-id="69cea-422">Eine beliebige Kombination von `compose` , `commandBox` `message` .</span><span class="sxs-lookup"><span data-stu-id="69cea-422">Any combination of `compose`, `commandBox`, `message`.</span></span> <span data-ttu-id="69cea-423">Der Standardwert ist `["compose", "commandBox"]`</span><span class="sxs-lookup"><span data-stu-id="69cea-423">Default is `["compose", "commandBox"]`</span></span>|
|`fetchTask`|<span data-ttu-id="69cea-424">Boolesch</span><span class="sxs-lookup"><span data-stu-id="69cea-424">Boolean</span></span>|||<span data-ttu-id="69cea-425">Ein boolescher Wert, der angibt, ob das Aufgabenmodul dynamisch abgerufen werden soll</span><span class="sxs-lookup"><span data-stu-id="69cea-425">A boolean value that indicates if it should fetch the task module dynamically</span></span>|
|`taskInfo`|<span data-ttu-id="69cea-426">Object</span><span class="sxs-lookup"><span data-stu-id="69cea-426">Object</span></span>|||<span data-ttu-id="69cea-427">Angeben des Aufgabenmoduls, das beim Verwenden eines Befehls für eine Messagingerweiterung vorab entladen werden soll</span><span class="sxs-lookup"><span data-stu-id="69cea-427">Specify the task module to preload when using a messaging extension command</span></span>|
|`taskInfo.title`|<span data-ttu-id="69cea-428">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="69cea-428">String</span></span>|<span data-ttu-id="69cea-429">64</span><span class="sxs-lookup"><span data-stu-id="69cea-429">64</span></span>||<span data-ttu-id="69cea-430">Titel des anfänglichen Dialogfelds</span><span class="sxs-lookup"><span data-stu-id="69cea-430">Initial dialog title</span></span>|
|`taskInfo.width`|<span data-ttu-id="69cea-431">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="69cea-431">String</span></span>|||<span data-ttu-id="69cea-432">Dialogbreite – entweder eine Zahl in Pixel oder ein Standardlayout wie "groß", "mittel" oder "klein"</span><span class="sxs-lookup"><span data-stu-id="69cea-432">Dialog width - either a number in pixels or default layout such as 'large', 'medium', or 'small'</span></span>|
|`taskInfo.height`|<span data-ttu-id="69cea-433">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="69cea-433">String</span></span>|||<span data-ttu-id="69cea-434">Dialoghöhe – entweder eine Zahl in Pixel oder ein Standardlayout wie "groß", "mittel" oder "klein"</span><span class="sxs-lookup"><span data-stu-id="69cea-434">Dialog height - either a number in pixels or default layout such as 'large', 'medium', or 'small'</span></span>|
|`taskInfo.url`|<span data-ttu-id="69cea-435">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="69cea-435">String</span></span>|||<span data-ttu-id="69cea-436">Anfängliche Webview-URL</span><span class="sxs-lookup"><span data-stu-id="69cea-436">Initial webview URL</span></span>|
|`messageHandlers`|<span data-ttu-id="69cea-437">Array von Objekten</span><span class="sxs-lookup"><span data-stu-id="69cea-437">Array of Objects</span></span>|<span data-ttu-id="69cea-438">5 </span><span class="sxs-lookup"><span data-stu-id="69cea-438">5</span></span>||<span data-ttu-id="69cea-439">Eine Liste von Handlern, mit denen Apps aufgerufen werden können, wenn bestimmte Bedingungen erfüllt sind.</span><span class="sxs-lookup"><span data-stu-id="69cea-439">A list of handlers that allow apps to be invoked when certain conditions are met.</span></span> <span data-ttu-id="69cea-440">Domänen müssen auch in `validDomains`</span><span class="sxs-lookup"><span data-stu-id="69cea-440">Domains must also be listed in `validDomains`</span></span>|
|`messageHandlers.type`|<span data-ttu-id="69cea-441">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="69cea-441">String</span></span>|||<span data-ttu-id="69cea-442">Der Typ des Nachrichtenhandlers.</span><span class="sxs-lookup"><span data-stu-id="69cea-442">The type of message handler.</span></span> <span data-ttu-id="69cea-443">Muss `"link"` sein.</span><span class="sxs-lookup"><span data-stu-id="69cea-443">Must be `"link"`.</span></span>|
|`messageHandlers.value.domains`|<span data-ttu-id="69cea-444">Array von Zeichenfolgen</span><span class="sxs-lookup"><span data-stu-id="69cea-444">Array of Strings</span></span>|||<span data-ttu-id="69cea-445">Array von Domänen, für die sich der Linknachrichtenhandler registrieren kann.</span><span class="sxs-lookup"><span data-stu-id="69cea-445">Array of domains that the link message handler can register for.</span></span>|
|`parameters`|<span data-ttu-id="69cea-446">Objektarray</span><span class="sxs-lookup"><span data-stu-id="69cea-446">Array of object</span></span>|<span data-ttu-id="69cea-447">5 </span><span class="sxs-lookup"><span data-stu-id="69cea-447">5</span></span>|<span data-ttu-id="69cea-448">✔</span><span class="sxs-lookup"><span data-stu-id="69cea-448">✔</span></span>|<span data-ttu-id="69cea-449">Die Liste der Parameter, die der Befehl verwendet.</span><span class="sxs-lookup"><span data-stu-id="69cea-449">The list of parameters the command takes.</span></span> <span data-ttu-id="69cea-450">Minimum: 1; Maximum: 5</span><span class="sxs-lookup"><span data-stu-id="69cea-450">Minimum: 1; maximum: 5</span></span>|
|`parameter.name`|<span data-ttu-id="69cea-451">String</span><span class="sxs-lookup"><span data-stu-id="69cea-451">String</span></span>|<span data-ttu-id="69cea-452">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="69cea-452">64 characters</span></span>|<span data-ttu-id="69cea-453">✔</span><span class="sxs-lookup"><span data-stu-id="69cea-453">✔</span></span>|<span data-ttu-id="69cea-454">Der Name des Parameters, wie er im Client angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="69cea-454">The name of the parameter as it appears in the client.</span></span> <span data-ttu-id="69cea-455">Dies ist in der Benutzeranforderung enthalten.</span><span class="sxs-lookup"><span data-stu-id="69cea-455">This is included in the user request.</span></span>|
|`parameter.title`|<span data-ttu-id="69cea-456">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="69cea-456">String</span></span>|<span data-ttu-id="69cea-457">32 Zeichen</span><span class="sxs-lookup"><span data-stu-id="69cea-457">32 characters</span></span>|<span data-ttu-id="69cea-458">✔</span><span class="sxs-lookup"><span data-stu-id="69cea-458">✔</span></span>|<span data-ttu-id="69cea-459">Benutzerfreundlicher Titel für den Parameter.</span><span class="sxs-lookup"><span data-stu-id="69cea-459">User-friendly title for the parameter.</span></span>|
|`parameter.description`|<span data-ttu-id="69cea-460">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="69cea-460">String</span></span>|<span data-ttu-id="69cea-461">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="69cea-461">128 characters</span></span>||<span data-ttu-id="69cea-462">Benutzerfreundliche Zeichenfolge, die den Zweck dieses Parameters beschreibt.</span><span class="sxs-lookup"><span data-stu-id="69cea-462">User-friendly string that describes this parameter’s purpose.</span></span>|
|`parameter.inputType`|<span data-ttu-id="69cea-463">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="69cea-463">String</span></span>|<span data-ttu-id="69cea-464">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="69cea-464">128 characters</span></span>||<span data-ttu-id="69cea-465">Definiert den Typ des Steuerelements, das in einem Aufgabenmodul für angezeigt `fetchTask: true` wird.</span><span class="sxs-lookup"><span data-stu-id="69cea-465">Defines the type of control displayed on a task module for `fetchTask: true`.</span></span> <span data-ttu-id="69cea-466">Einer von `text` `textarea` , `number` `date` `time` `toggle``choiceset`</span><span class="sxs-lookup"><span data-stu-id="69cea-466">One of `text`, `textarea`, `number`, `date`, `time`, `toggle`, `choiceset`</span></span>|
|`parameter.choices`|<span data-ttu-id="69cea-467">Array von Objekten</span><span class="sxs-lookup"><span data-stu-id="69cea-467">Array of Objects</span></span>|<span data-ttu-id="69cea-468">10 </span><span class="sxs-lookup"><span data-stu-id="69cea-468">10</span></span>||<span data-ttu-id="69cea-469">Die Auswahloptionen für die `choiceset` .</span><span class="sxs-lookup"><span data-stu-id="69cea-469">The choice options for the `choiceset`.</span></span> <span data-ttu-id="69cea-470">Nur verwenden, wenn `parameter.inputType` dies der `choiceset`</span><span class="sxs-lookup"><span data-stu-id="69cea-470">Use only when `parameter.inputType` is `choiceset`</span></span>|
|`parameter.choices.title`|<span data-ttu-id="69cea-471">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="69cea-471">String</span></span>|<span data-ttu-id="69cea-472">128</span><span class="sxs-lookup"><span data-stu-id="69cea-472">128</span></span>||<span data-ttu-id="69cea-473">Titel der Wahl</span><span class="sxs-lookup"><span data-stu-id="69cea-473">Title of the choice</span></span>|
|`parameter.choices.value`|<span data-ttu-id="69cea-474">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="69cea-474">String</span></span>|<span data-ttu-id="69cea-475">512</span><span class="sxs-lookup"><span data-stu-id="69cea-475">512</span></span>||<span data-ttu-id="69cea-476">Wert der Auswahl</span><span class="sxs-lookup"><span data-stu-id="69cea-476">Value of the choice</span></span>|

## <a name="permissions"></a><span data-ttu-id="69cea-477">Berechtigungen</span><span class="sxs-lookup"><span data-stu-id="69cea-477">permissions</span></span>

<span data-ttu-id="69cea-478">**Optional**</span><span class="sxs-lookup"><span data-stu-id="69cea-478">**Optional**</span></span>

<span data-ttu-id="69cea-479">Ein Array, von dem angegeben wird, welche Berechtigungen die App anfordert, wodurch Endbenutzer wissen, `string` wie die Erweiterung funktioniert.</span><span class="sxs-lookup"><span data-stu-id="69cea-479">An array of `string` which specifies which permissions the app requests, which lets end users know how the extension will perform.</span></span> <span data-ttu-id="69cea-480">Die folgenden Optionen sind nicht exklusiv:</span><span class="sxs-lookup"><span data-stu-id="69cea-480">The following options are non-exclusive:</span></span>

* <span data-ttu-id="69cea-481">`identity`&emsp;Erfordert Informationen zur Benutzeridentität</span><span class="sxs-lookup"><span data-stu-id="69cea-481">`identity` &emsp; Requires user identity information</span></span>
* <span data-ttu-id="69cea-482">`messageTeamMembers`&emsp;Erfordert die Berechtigung zum Senden direkter Nachrichten an Teammitglieder</span><span class="sxs-lookup"><span data-stu-id="69cea-482">`messageTeamMembers` &emsp; Requires permission to send direct messages to team members</span></span>

<span data-ttu-id="69cea-483">Wenn Sie diese Berechtigungen beim Aktualisieren Ihrer App ändern, wiederholen Ihre Benutzer den Zustimmungsprozess, wenn sie die aktualisierte App zum ersten Mal ausführen.</span><span class="sxs-lookup"><span data-stu-id="69cea-483">Changing these permissions when updating your app will cause your users to repeat the consent process the first time they run the updated app.</span></span>

## <a name="devicepermissions"></a><span data-ttu-id="69cea-484">devicePermissions</span><span class="sxs-lookup"><span data-stu-id="69cea-484">devicePermissions</span></span>

<span data-ttu-id="69cea-485">**Optional** Array von Zeichenfolgen</span><span class="sxs-lookup"><span data-stu-id="69cea-485">**Optional** Array of Strings</span></span>

<span data-ttu-id="69cea-486">Gibt die systemeigenen Features auf dem Gerät eines Benutzers an, auf die Ihre App Zugriff anfordern kann.</span><span class="sxs-lookup"><span data-stu-id="69cea-486">Specifies the native features on a user's device that your app may request access to.</span></span> <span data-ttu-id="69cea-487">Mögliche Optionen sind:</span><span class="sxs-lookup"><span data-stu-id="69cea-487">Options are:</span></span>

* `geolocation`
* `media`
* `notifications`
* `midi`
* `openExternal`

## <a name="validdomains"></a><span data-ttu-id="69cea-488">validDomains</span><span class="sxs-lookup"><span data-stu-id="69cea-488">validDomains</span></span>

<span data-ttu-id="69cea-489">**Optional**, mit Ausnahme **von "Erforderlich"** (sofern angegeben)</span><span class="sxs-lookup"><span data-stu-id="69cea-489">**Optional**, except **Required** where noted</span></span>

<span data-ttu-id="69cea-490">Eine Liste gültiger Domänen, aus denen die App erwartet, dass Inhalte geladen werden.</span><span class="sxs-lookup"><span data-stu-id="69cea-490">A list of valid domains from which the app expects to load any content.</span></span> <span data-ttu-id="69cea-491">Domänenauflistungen können Platzhalter enthalten, z. B. `*.example.com` .</span><span class="sxs-lookup"><span data-stu-id="69cea-491">Domain listings can include wildcards, for example `*.example.com`.</span></span> <span data-ttu-id="69cea-492">Dies entspricht genau einem Segment der Domäne. Wenn Sie übereinstimmen müssen, `a.b.example.com` verwenden Sie `*.*.example.com` .</span><span class="sxs-lookup"><span data-stu-id="69cea-492">This matches exactly one segment of the domain; if you need to match `a.b.example.com` then use `*.*.example.com`.</span></span> <span data-ttu-id="69cea-493">Wenn Ihre Registerkartenkonfiguration oder Inhaltsbenutzeroberfläche neben der Registerkartenkonfiguration zu einer anderen Domäne navigieren muss, muss diese Domäne hier angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="69cea-493">If your tab configuration or content UI needs to navigate to any other domain besides the one use for tab configuration, that domain must be specified here.</span></span>

<span data-ttu-id="69cea-494">Es ist **jedoch nicht** erforderlich, die Domänen von Identitätsanbietern, die Sie unterstützen möchten, in Ihre App zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="69cea-494">It is **not** necessary to include the domains of identity providers you want to support in your app, however.</span></span> <span data-ttu-id="69cea-495">Um sich z. B. mithilfe einer Google-ID zu authentifizieren, ist es erforderlich, zu accounts.google.com umzuleiten, sie sollten jedoch nicht accounts.google.com `validDomains[]` enthalten.</span><span class="sxs-lookup"><span data-stu-id="69cea-495">For example, to authenticate using a Google ID, it's necessary to redirect to accounts.google.com, but you should not include accounts.google.com in `validDomains[]`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="69cea-496">Fügen Sie keine Domänen hinzu, die sich außerhalb Ihrer Kontrolle befinden, weder direkt noch über Platzhalter.</span><span class="sxs-lookup"><span data-stu-id="69cea-496">Do not add domains that are outside your control, either directly or via wildcards.</span></span> <span data-ttu-id="69cea-497">Beispielsweise ist `yourapp.onmicrosoft.com` er gültig, aber `*.onmicrosoft.com` ungültig.</span><span class="sxs-lookup"><span data-stu-id="69cea-497">For example, `yourapp.onmicrosoft.com` is valid, but `*.onmicrosoft.com` is not valid.</span></span>

<span data-ttu-id="69cea-498">Das Objekt ist ein Array mit allen Elementen des Typs `string` .</span><span class="sxs-lookup"><span data-stu-id="69cea-498">The object is an array with all elements of the type `string`.</span></span>

## <a name="webapplicationinfo"></a><span data-ttu-id="69cea-499">webApplicationInfo</span><span class="sxs-lookup"><span data-stu-id="69cea-499">webApplicationInfo</span></span>

<span data-ttu-id="69cea-500">**Optional**</span><span class="sxs-lookup"><span data-stu-id="69cea-500">**Optional**</span></span>

<span data-ttu-id="69cea-501">Geben Sie Ihre AAD-App-ID und die Graph-Informationen an, um Benutzern bei der nahtlosen Anmeldung bei Ihrer AAD-App zu helfen.</span><span class="sxs-lookup"><span data-stu-id="69cea-501">Specify your AAD App ID and Graph information to help users seamlessly sign into your AAD app.</span></span>

|<span data-ttu-id="69cea-502">Name</span><span class="sxs-lookup"><span data-stu-id="69cea-502">Name</span></span>| <span data-ttu-id="69cea-503">Typ</span><span class="sxs-lookup"><span data-stu-id="69cea-503">Type</span></span>| <span data-ttu-id="69cea-504">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="69cea-504">Maximum size</span></span> | <span data-ttu-id="69cea-505">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="69cea-505">Required</span></span> | <span data-ttu-id="69cea-506">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="69cea-506">Description</span></span>|
|---|---|---|---|---|
|`id`|<span data-ttu-id="69cea-507">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="69cea-507">String</span></span>|<span data-ttu-id="69cea-508">36 Zeichen</span><span class="sxs-lookup"><span data-stu-id="69cea-508">36 characters</span></span>|<span data-ttu-id="69cea-509">✔</span><span class="sxs-lookup"><span data-stu-id="69cea-509">✔</span></span>|<span data-ttu-id="69cea-510">AAD-Anwendungs-ID der App.</span><span class="sxs-lookup"><span data-stu-id="69cea-510">AAD application id of the app.</span></span> <span data-ttu-id="69cea-511">Diese ID muss eine GUID sein.</span><span class="sxs-lookup"><span data-stu-id="69cea-511">This id must be a GUID.</span></span>|
|`resource`|<span data-ttu-id="69cea-512">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="69cea-512">String</span></span>|<span data-ttu-id="69cea-513">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="69cea-513">2048 characters</span></span>|<span data-ttu-id="69cea-514">✔</span><span class="sxs-lookup"><span data-stu-id="69cea-514">✔</span></span>|<span data-ttu-id="69cea-515">Ressourcen-URL der App zum Abrufen des Authentifizierungstokens für SSO.</span><span class="sxs-lookup"><span data-stu-id="69cea-515">Resource url of app for acquiring auth token for SSO.</span></span>|