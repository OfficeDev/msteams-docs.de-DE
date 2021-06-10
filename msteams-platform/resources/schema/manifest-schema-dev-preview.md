---
title: Referenz zum Entwicklervorschaumanifestschema
description: Beschreibt das vom Manifest unterstützte Schema für Microsoft Teams
ms.topic: reference
keywords: Teams-Manifestschema – Entwicklervorschau
localization_priority: Normal
ms.date: 05/20/2019
ms.openlocfilehash: c582a6af0505680b9843c86be7fc800fab12129d
ms.sourcegitcommit: 37325179a532897fafbe827dcf9a7ca5fa5e7d0b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/09/2021
ms.locfileid: "52853536"
---
# <a name="developer-preview-manifest-schema-for-microsoft-teams"></a><span data-ttu-id="33174-104">Entwicklervorschau-Manifestschema für Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="33174-104">Developer preview manifest schema for Microsoft Teams</span></span>

> [!NOTE]
> <span data-ttu-id="33174-105">Weitere Informationen zum Programm und wie Sie teilnehmen können, finden Sie in der [Entwicklervorschau.](~/resources/dev-preview/developer-preview-intro.md)</span><span class="sxs-lookup"><span data-stu-id="33174-105">For more information on the program and how you can join,see [Developer Preview](~/resources/dev-preview/developer-preview-intro.md).</span></span>
> <span data-ttu-id="33174-106">Wenn Sie die Entwicklervorschau nicht verwenden, sollten Sie diese Version des Manifests nicht verwenden.</span><span class="sxs-lookup"><span data-stu-id="33174-106">If you are not using the developer preview you should not be using this version of the manifest.</span></span> <span data-ttu-id="33174-107">Siehe [Referenz: Manifestschema für Microsoft Teams](~/resources/schema/manifest-schema.md) für die öffentliche Version des Manifests.</span><span class="sxs-lookup"><span data-stu-id="33174-107">See [Reference: Manifest schema for Microsoft Teams](~/resources/schema/manifest-schema.md) for the public version of the manifest.</span></span>

<span data-ttu-id="33174-108">Das Microsoft Teams Manifest beschreibt, wie die App in das Microsoft Teams Produkt integriert wird.</span><span class="sxs-lookup"><span data-stu-id="33174-108">The Microsoft Teams manifest describes how the app integrates into the Microsoft Teams product.</span></span> <span data-ttu-id="33174-109">Ihr Manifest muss dem schema gehosteten [`https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json`](https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json) entsprechen.</span><span class="sxs-lookup"><span data-stu-id="33174-109">Your manifest must conform to the schema hosted at [`https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json`](https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json).</span></span>

<span data-ttu-id="33174-110">Weitere Informationen zu den verfügbaren Features finden Sie [unter: Features in der Public Developer Preview für Microsoft Teams](~/resources/dev-preview/developer-preview-features.md).</span><span class="sxs-lookup"><span data-stu-id="33174-110">For more information on the features available see: [Features in the Public Developer Preview for Microsoft Teams](~/resources/dev-preview/developer-preview-features.md).</span></span>

## <a name="sample-full-manifest"></a><span data-ttu-id="33174-111">Vollständiges Beispielmanifest</span><span class="sxs-lookup"><span data-stu-id="33174-111">Sample full manifest</span></span>

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
     "developerUrl",
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

<span data-ttu-id="33174-112">Das Schema definiert die folgenden Eigenschaften:</span><span class="sxs-lookup"><span data-stu-id="33174-112">The schema defines the following properties:</span></span>

## <a name="schema"></a><span data-ttu-id="33174-113">$schema</span><span class="sxs-lookup"><span data-stu-id="33174-113">$schema</span></span>

<span data-ttu-id="33174-114">*Optional, aber empfohlen* &ndash; Schnur</span><span class="sxs-lookup"><span data-stu-id="33174-114">*Optional, but recommended* &ndash; String</span></span>

<span data-ttu-id="33174-115">Die https://-URL, die auf das JSON-Schema für das Manifest verweist.</span><span class="sxs-lookup"><span data-stu-id="33174-115">The https:// URL referencing the JSON Schema for the manifest.</span></span>

## <a name="manifestversion"></a><span data-ttu-id="33174-116">manifestVersion</span><span class="sxs-lookup"><span data-stu-id="33174-116">manifestVersion</span></span>

<span data-ttu-id="33174-117">**Erforderlich** &ndash; Schnur</span><span class="sxs-lookup"><span data-stu-id="33174-117">**Required** &ndash; String</span></span>

<span data-ttu-id="33174-118">Die Version des Manifestschemas, das dieses Manifest verwendet.</span><span class="sxs-lookup"><span data-stu-id="33174-118">The version of the manifest schema this manifest is using.</span></span> <span data-ttu-id="33174-119">Es sollte "devPreview" sein.</span><span class="sxs-lookup"><span data-stu-id="33174-119">It should be "devPreview".</span></span>

## <a name="version"></a><span data-ttu-id="33174-120">Version</span><span class="sxs-lookup"><span data-stu-id="33174-120">version</span></span>

<span data-ttu-id="33174-121">**Erforderlich** &ndash; Schnur</span><span class="sxs-lookup"><span data-stu-id="33174-121">**Required** &ndash; String</span></span>

<span data-ttu-id="33174-122">Die Version der spezifischen App.</span><span class="sxs-lookup"><span data-stu-id="33174-122">The version of the specific app.</span></span> <span data-ttu-id="33174-123">Wenn Sie etwas in Ihrem Manifest aktualisieren, muss auch die Version erhöht werden.</span><span class="sxs-lookup"><span data-stu-id="33174-123">If you update something in your manifest, the version must be incremented as well.</span></span> <span data-ttu-id="33174-124">Auf diese Weise wird bei der Installation des neuen Manifests das vorhandene überschrieben, und der Benutzer erhält die neue Funktionalität.</span><span class="sxs-lookup"><span data-stu-id="33174-124">This way, when the new manifest is installed, it will overwrite the existing one and the user will get the new functionality.</span></span> <span data-ttu-id="33174-125">Wenn diese App an den Store übermittelt wurde, muss das neue Manifest erneut übermittelt und erneut überprüft werden.</span><span class="sxs-lookup"><span data-stu-id="33174-125">If this app was submitted to the store, the new manifest will have to be re-submitted and re-validated.</span></span> <span data-ttu-id="33174-126">Anschließend erhalten Benutzer dieser App das neue aktualisierte Manifest automatisch in einigen Stunden, nachdem es genehmigt wurde.</span><span class="sxs-lookup"><span data-stu-id="33174-126">Then, users of this app will get the new updated manifest automatically in a few hours, after it is approved.</span></span>

<span data-ttu-id="33174-127">Wenn sich die von der App angeforderten Berechtigungen ändern, werden die Benutzer aufgefordert, ein Upgrade durchzuführen und der App erneut zuzustimmen.</span><span class="sxs-lookup"><span data-stu-id="33174-127">If the app requested permissions change, users will be prompted to upgrade and re-consent to the app.</span></span>

<span data-ttu-id="33174-128">Diese Versionszeichenfolge muss dem [Semverstandard](http://semver.org/) (MAJOR. kleiner. PATCH).</span><span class="sxs-lookup"><span data-stu-id="33174-128">This version string must follow the [semver](http://semver.org/) standard (MAJOR.MINOR.PATCH).</span></span>

## <a name="id"></a><span data-ttu-id="33174-129">id</span><span class="sxs-lookup"><span data-stu-id="33174-129">id</span></span>

<span data-ttu-id="33174-130">**Erforderlich** &ndash; Microsoft-App-ID</span><span class="sxs-lookup"><span data-stu-id="33174-130">**Required** &ndash; Microsoft app ID</span></span>

<span data-ttu-id="33174-131">Der eindeutige von Microsoft generierte Bezeichner für diese App.</span><span class="sxs-lookup"><span data-stu-id="33174-131">The unique Microsoft-generated identifier for this app.</span></span> <span data-ttu-id="33174-132">Wenn Sie einen Bot über die Microsoft Bot Framework registriert haben oder sich die Web-App Ihrer Registerkarte bereits bei Microsoft anmeldet, sollten Sie bereits über eine ID verfügen und sie hier eingeben.</span><span class="sxs-lookup"><span data-stu-id="33174-132">If you have registered a bot via the Microsoft Bot Framework, or your tab's web app already signs in with Microsoft, you should already have an ID and should enter it here.</span></span> <span data-ttu-id="33174-133">Andernfalls sollten Sie eine neue ID im Microsoft-Anwendungsregistrierungsportal[(Meine Anwendungen)](https://apps.dev.microsoft.com)generieren, sie hier eingeben und dann wiederverwenden, wenn Sie [einen Bot hinzufügen.](~/bots/how-to/create-a-bot-for-teams.md)</span><span class="sxs-lookup"><span data-stu-id="33174-133">Otherwise, you should generate a new ID at the Microsoft Application Registration Portal ([My Applications](https://apps.dev.microsoft.com)), enter it here, and then reuse it when you [add a bot](~/bots/how-to/create-a-bot-for-teams.md).</span></span>

## <a name="packagename"></a><span data-ttu-id="33174-134">Packagename</span><span class="sxs-lookup"><span data-stu-id="33174-134">packageName</span></span>

<span data-ttu-id="33174-135">**Erforderlich** &ndash; Schnur</span><span class="sxs-lookup"><span data-stu-id="33174-135">**Required** &ndash; String</span></span>

<span data-ttu-id="33174-136">Ein eindeutiger Bezeichner für diese App in umgekehrter Domänenschreibweise; z. B. com.example.myapp.</span><span class="sxs-lookup"><span data-stu-id="33174-136">A unique identifier for this app in reverse domain notation; for example, com.example.myapp.</span></span>

## <a name="developer"></a><span data-ttu-id="33174-137">developer</span><span class="sxs-lookup"><span data-stu-id="33174-137">developer</span></span>

<span data-ttu-id="33174-138">**Required**</span><span class="sxs-lookup"><span data-stu-id="33174-138">**Required**</span></span>

<span data-ttu-id="33174-139">Gibt Informationen zu Ihrem Unternehmen an.</span><span class="sxs-lookup"><span data-stu-id="33174-139">Specifies information about your company.</span></span> <span data-ttu-id="33174-140">Bei An AppSource übermittelten Apps (früher Office Store) müssen diese Werte mit den Informationen in Ihrem AppSource-Eintrag übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="33174-140">For apps submitted to AppSource (formerly Office Store), these values must match the information in your AppSource entry.</span></span>

|<span data-ttu-id="33174-141">Name</span><span class="sxs-lookup"><span data-stu-id="33174-141">Name</span></span>| <span data-ttu-id="33174-142">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="33174-142">Maximum size</span></span> | <span data-ttu-id="33174-143">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="33174-143">Required</span></span> | <span data-ttu-id="33174-144">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="33174-144">Description</span></span>|
|---|---|---|---|
|`name`|<span data-ttu-id="33174-145">32 Zeichen</span><span class="sxs-lookup"><span data-stu-id="33174-145">32 characters</span></span>|<span data-ttu-id="33174-146">✔</span><span class="sxs-lookup"><span data-stu-id="33174-146">✔</span></span>|<span data-ttu-id="33174-147">Der Anzeigename für den Entwickler.</span><span class="sxs-lookup"><span data-stu-id="33174-147">The display name for the developer.</span></span>|
|`websiteUrl`|<span data-ttu-id="33174-148">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="33174-148">2048 characters</span></span>|<span data-ttu-id="33174-149">✔</span><span class="sxs-lookup"><span data-stu-id="33174-149">✔</span></span>|<span data-ttu-id="33174-150">Die https:// URL zur Website des Entwicklers.</span><span class="sxs-lookup"><span data-stu-id="33174-150">The https:// URL to the developer's website.</span></span> <span data-ttu-id="33174-151">Dieser Link sollte Benutzer zu Ihrem Unternehmen oder zu einer produktspezifischen Angebotsseite führen.</span><span class="sxs-lookup"><span data-stu-id="33174-151">This link should take users to your company or product-specific landing page.</span></span>|
|`privacyUrl`|<span data-ttu-id="33174-152">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="33174-152">2048 characters</span></span>|<span data-ttu-id="33174-153">✔</span><span class="sxs-lookup"><span data-stu-id="33174-153">✔</span></span>|<span data-ttu-id="33174-154">Die https:// URL zur Datenschutzrichtlinie des Entwicklers.</span><span class="sxs-lookup"><span data-stu-id="33174-154">The https:// URL to the developer's privacy policy.</span></span>|
|`termsOfUseUrl`|<span data-ttu-id="33174-155">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="33174-155">2048 characters</span></span>|<span data-ttu-id="33174-156">✔</span><span class="sxs-lookup"><span data-stu-id="33174-156">✔</span></span>|<span data-ttu-id="33174-157">Die https:// URL zu den Nutzungsbedingungen des Entwicklers.</span><span class="sxs-lookup"><span data-stu-id="33174-157">The https:// URL to the developer's terms of use.</span></span>|
|`mpnId`|<span data-ttu-id="33174-158">10 Zeichen</span><span class="sxs-lookup"><span data-stu-id="33174-158">10 characters</span></span>|<span data-ttu-id="33174-159">✔</span><span class="sxs-lookup"><span data-stu-id="33174-159">✔</span></span>|<span data-ttu-id="33174-160">**Optional** Die Microsoft Partner Network-ID, die die Partnerorganisation identifiziert, die die App erstellt.</span><span class="sxs-lookup"><span data-stu-id="33174-160">**Optional** The Microsoft Partner Network ID that identifies the partner organization building the app.</span></span>|

## <a name="localizationinfo"></a><span data-ttu-id="33174-161">localizationInfo</span><span class="sxs-lookup"><span data-stu-id="33174-161">localizationInfo</span></span>

<span data-ttu-id="33174-162">**Optional**</span><span class="sxs-lookup"><span data-stu-id="33174-162">**Optional**</span></span>

<span data-ttu-id="33174-163">Ermöglicht die Angabe einer Standardsprache sowie Zeiger auf zusätzliche Sprachdateien.</span><span class="sxs-lookup"><span data-stu-id="33174-163">Allows the specification of a default language, as well as pointers to additional language files.</span></span> <span data-ttu-id="33174-164">Siehe [Lokalisierung](~/concepts/build-and-test/apps-localization.md).</span><span class="sxs-lookup"><span data-stu-id="33174-164">See [localization](~/concepts/build-and-test/apps-localization.md).</span></span>

|<span data-ttu-id="33174-165">Name</span><span class="sxs-lookup"><span data-stu-id="33174-165">Name</span></span>| <span data-ttu-id="33174-166">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="33174-166">Maximum size</span></span> | <span data-ttu-id="33174-167">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="33174-167">Required</span></span> | <span data-ttu-id="33174-168">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="33174-168">Description</span></span>|
|---|---|---|---|
|`defaultLanguageTag`|<span data-ttu-id="33174-169">4 Zeichen</span><span class="sxs-lookup"><span data-stu-id="33174-169">4 characters</span></span>|<span data-ttu-id="33174-170">✔</span><span class="sxs-lookup"><span data-stu-id="33174-170">✔</span></span>|<span data-ttu-id="33174-171">Das Sprachtag der Zeichenfolgen in dieser Manifestdatei auf oberster Ebene.</span><span class="sxs-lookup"><span data-stu-id="33174-171">The language tag of the strings in this top level manifest file.</span></span>|

### <a name="localizationinfoadditionallanguages"></a><span data-ttu-id="33174-172">localizationInfo.additionalLanguages</span><span class="sxs-lookup"><span data-stu-id="33174-172">localizationInfo.additionalLanguages</span></span>

<span data-ttu-id="33174-173">Ein Array von Objekten, die zusätzliche Sprachübersetzungen angeben.</span><span class="sxs-lookup"><span data-stu-id="33174-173">An array of objects specifying additional language translations.</span></span>

|<span data-ttu-id="33174-174">Name</span><span class="sxs-lookup"><span data-stu-id="33174-174">Name</span></span>| <span data-ttu-id="33174-175">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="33174-175">Maximum size</span></span> | <span data-ttu-id="33174-176">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="33174-176">Required</span></span> | <span data-ttu-id="33174-177">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="33174-177">Description</span></span>|
|---|---|---|---|
|`languageTag`|<span data-ttu-id="33174-178">4 Zeichen</span><span class="sxs-lookup"><span data-stu-id="33174-178">4 characters</span></span>|<span data-ttu-id="33174-179">✔</span><span class="sxs-lookup"><span data-stu-id="33174-179">✔</span></span>|<span data-ttu-id="33174-180">Das Sprachtag der Zeichenfolgen in der bereitgestellten Datei.</span><span class="sxs-lookup"><span data-stu-id="33174-180">The language tag of the strings in the provided file.</span></span>|
|`file`|<span data-ttu-id="33174-181">4 Zeichen</span><span class="sxs-lookup"><span data-stu-id="33174-181">4 characters</span></span>|<span data-ttu-id="33174-182">✔</span><span class="sxs-lookup"><span data-stu-id="33174-182">✔</span></span>|<span data-ttu-id="33174-183">Ein relativer Dateipfad zu einer JSON-Datei, die die übersetzten Zeichenfolgen enthält.</span><span class="sxs-lookup"><span data-stu-id="33174-183">A relative file path to a the .json file containing the translated strings.</span></span>|

## <a name="name"></a><span data-ttu-id="33174-184">name</span><span class="sxs-lookup"><span data-stu-id="33174-184">name</span></span>

<span data-ttu-id="33174-185">**Required**</span><span class="sxs-lookup"><span data-stu-id="33174-185">**Required**</span></span>

<span data-ttu-id="33174-186">Der Name Ihrer App-Erfahrung, der Benutzern in der Teams angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="33174-186">The name of your app experience, displayed to users in the Teams experience.</span></span> <span data-ttu-id="33174-187">Für an AppSource übermittelte Apps müssen diese Werte mit den Informationen in Ihrem AppSource-Eintrag übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="33174-187">For apps submitted to AppSource, these values must match the information in your AppSource entry.</span></span> <span data-ttu-id="33174-188">Die Werte von `short` und sollten nicht identisch `full` sein.</span><span class="sxs-lookup"><span data-stu-id="33174-188">The values of `short` and `full` should not be the same.</span></span>

|<span data-ttu-id="33174-189">Name</span><span class="sxs-lookup"><span data-stu-id="33174-189">Name</span></span>| <span data-ttu-id="33174-190">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="33174-190">Maximum size</span></span> | <span data-ttu-id="33174-191">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="33174-191">Required</span></span> | <span data-ttu-id="33174-192">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="33174-192">Description</span></span>|
|---|---|---|---|
|`short`|<span data-ttu-id="33174-193">30 Zeichen</span><span class="sxs-lookup"><span data-stu-id="33174-193">30 characters</span></span>|<span data-ttu-id="33174-194">✔</span><span class="sxs-lookup"><span data-stu-id="33174-194">✔</span></span>|<span data-ttu-id="33174-195">Der kurze Anzeigename für die App.</span><span class="sxs-lookup"><span data-stu-id="33174-195">The short display name for the app.</span></span>|
|`full`|<span data-ttu-id="33174-196">100 Zeichen</span><span class="sxs-lookup"><span data-stu-id="33174-196">100 characters</span></span>||<span data-ttu-id="33174-197">Der vollständige Name der App, der verwendet wird, wenn der vollständige App-Name 30 Zeichen überschreitet.</span><span class="sxs-lookup"><span data-stu-id="33174-197">The full name of the app, used if the full app name exceeds 30 characters.</span></span>|

## <a name="description"></a><span data-ttu-id="33174-198">description</span><span class="sxs-lookup"><span data-stu-id="33174-198">description</span></span>

<span data-ttu-id="33174-199">**Required**</span><span class="sxs-lookup"><span data-stu-id="33174-199">**Required**</span></span>

<span data-ttu-id="33174-200">Beschreibt Ihre App für Benutzer.</span><span class="sxs-lookup"><span data-stu-id="33174-200">Describes your app to users.</span></span> <span data-ttu-id="33174-201">Für an AppSource übermittelte Apps müssen diese Werte mit den Informationen in Ihrem AppSource-Eintrag übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="33174-201">For apps submitted to AppSource, these values must match the information in your AppSource entry.</span></span>

<span data-ttu-id="33174-202">Stellen Sie sicher, dass Ihre Beschreibung Ihre Erfahrung genau beschreibt und Informationen bereitstellt, die potenziellen Kunden helfen, zu verstehen, was Ihre Erfahrung bewirkt.</span><span class="sxs-lookup"><span data-stu-id="33174-202">Ensure that your description accurately describes your experience and provides information to help potential customers understand what your experience does.</span></span> <span data-ttu-id="33174-203">Beachten Sie in der vollständigen Beschreibung auch, ob für die Verwendung ein externes Konto erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="33174-203">You should also note, in the full description, if an external account is required for use.</span></span> <span data-ttu-id="33174-204">Die Werte von `short` und sollten nicht identisch `full` sein.</span><span class="sxs-lookup"><span data-stu-id="33174-204">The values of `short` and `full` should not be the same.</span></span>  <span data-ttu-id="33174-205">Ihre kurze Beschreibung darf nicht innerhalb der langen Beschreibung wiederholt werden und darf keinen anderen App-Namen enthalten.</span><span class="sxs-lookup"><span data-stu-id="33174-205">Your short description must not be repeated within the long description and must not include any other app name.</span></span>

|<span data-ttu-id="33174-206">Name</span><span class="sxs-lookup"><span data-stu-id="33174-206">Name</span></span>| <span data-ttu-id="33174-207">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="33174-207">Maximum size</span></span> | <span data-ttu-id="33174-208">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="33174-208">Required</span></span> | <span data-ttu-id="33174-209">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="33174-209">Description</span></span>|
|---|---|---|---|
|`short`|<span data-ttu-id="33174-210">80 Zeichen</span><span class="sxs-lookup"><span data-stu-id="33174-210">80 characters</span></span>|<span data-ttu-id="33174-211">✔</span><span class="sxs-lookup"><span data-stu-id="33174-211">✔</span></span>|<span data-ttu-id="33174-212">Eine kurze Beschreibung der App-Erfahrung, die verwendet wird, wenn der Platz begrenzt ist.</span><span class="sxs-lookup"><span data-stu-id="33174-212">A short description of your app experience, used when space is limited.</span></span>|
|`full`|<span data-ttu-id="33174-213">4000 Zeichen</span><span class="sxs-lookup"><span data-stu-id="33174-213">4000 characters</span></span>|<span data-ttu-id="33174-214">✔</span><span class="sxs-lookup"><span data-stu-id="33174-214">✔</span></span>|<span data-ttu-id="33174-215">Die vollständige Beschreibung Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="33174-215">The full description of your app.</span></span>|

## <a name="icons"></a><span data-ttu-id="33174-216">Symbole</span><span class="sxs-lookup"><span data-stu-id="33174-216">icons</span></span>

<span data-ttu-id="33174-217">**Required**</span><span class="sxs-lookup"><span data-stu-id="33174-217">**Required**</span></span>

<span data-ttu-id="33174-218">Symbole, die in der Teams-App verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="33174-218">Icons used within the Teams app.</span></span> <span data-ttu-id="33174-219">Die Symboldateien müssen als Teil des Uploadpakets enthalten sein.</span><span class="sxs-lookup"><span data-stu-id="33174-219">The icon files must be included as part of the upload package.</span></span>

|<span data-ttu-id="33174-220">Name</span><span class="sxs-lookup"><span data-stu-id="33174-220">Name</span></span>| <span data-ttu-id="33174-221">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="33174-221">Maximum size</span></span> | <span data-ttu-id="33174-222">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="33174-222">Required</span></span> | <span data-ttu-id="33174-223">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="33174-223">Description</span></span>|
|---|---|---|---|
|`outline`|<span data-ttu-id="33174-224">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="33174-224">2048 characters</span></span>|<span data-ttu-id="33174-225">✔</span><span class="sxs-lookup"><span data-stu-id="33174-225">✔</span></span>|<span data-ttu-id="33174-226">Ein relativer Dateipfad zu einem transparenten 32 x 32 PNG-Gliederungssymbol.</span><span class="sxs-lookup"><span data-stu-id="33174-226">A relative file path to a transparent 32x32 PNG outline icon.</span></span>|
|`color`|<span data-ttu-id="33174-227">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="33174-227">2048 characters</span></span>|<span data-ttu-id="33174-228">✔</span><span class="sxs-lookup"><span data-stu-id="33174-228">✔</span></span>|<span data-ttu-id="33174-229">Ein relativer Dateipfad zu einem farbigen PNG-Symbol mit 192 x 192.</span><span class="sxs-lookup"><span data-stu-id="33174-229">A relative file path to a full color 192x192 PNG icon.</span></span>|

## <a name="accentcolor"></a><span data-ttu-id="33174-230">accentColor</span><span class="sxs-lookup"><span data-stu-id="33174-230">accentColor</span></span>

<span data-ttu-id="33174-231">**Erforderlich** &ndash; Schnur</span><span class="sxs-lookup"><span data-stu-id="33174-231">**Required** &ndash; String</span></span>

<span data-ttu-id="33174-232">Eine Farbe, die in Verbindung mit und als Hintergrund für Ihre Gliederungssymbole verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="33174-232">A color to use in conjunction with and as a background for your outline icons.</span></span>

<span data-ttu-id="33174-233">Der Wert muss ein gültiger HTML-Farbcode sein, der mit "#" beginnt, z. `#4464ee` B. .</span><span class="sxs-lookup"><span data-stu-id="33174-233">The value must be a valid HTML color code starting with '#', for example `#4464ee`.</span></span>

## <a name="configurabletabs"></a><span data-ttu-id="33174-234">configurableTabs</span><span class="sxs-lookup"><span data-stu-id="33174-234">configurableTabs</span></span>

<span data-ttu-id="33174-235">**Optional**</span><span class="sxs-lookup"><span data-stu-id="33174-235">**Optional**</span></span>

<span data-ttu-id="33174-236">Wird verwendet, wenn Ihre App-Erfahrung über eine Registerkartenoberfläche im Teamkanal verfügt, die eine zusätzliche Konfiguration erfordert, bevor sie hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="33174-236">Used when your app experience has a team channel tab experience that requires extra configuration before it is added.</span></span> <span data-ttu-id="33174-237">Konfigurierbare Registerkarten werden nur im Teams-Bereich unterstützt, und derzeit wird nur eine Registerkarte pro App unterstützt.</span><span class="sxs-lookup"><span data-stu-id="33174-237">Configurable tabs are supported only in the teams scope, and currently only one tab per app is supported.</span></span>

<span data-ttu-id="33174-238">Das Objekt ist ein Array mit allen Elementen des Typs `object` .</span><span class="sxs-lookup"><span data-stu-id="33174-238">The object is an array with all elements of the type `object`.</span></span> <span data-ttu-id="33174-239">Dieser Block ist nur für Lösungen erforderlich, die eine konfigurierbare Kanalregisterkartenlösung bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="33174-239">This block is required only for solutions that provide a configurable channel tab solution.</span></span>

|<span data-ttu-id="33174-240">Name</span><span class="sxs-lookup"><span data-stu-id="33174-240">Name</span></span>| <span data-ttu-id="33174-241">Typ</span><span class="sxs-lookup"><span data-stu-id="33174-241">Type</span></span>| <span data-ttu-id="33174-242">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="33174-242">Maximum size</span></span> | <span data-ttu-id="33174-243">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="33174-243">Required</span></span> | <span data-ttu-id="33174-244">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="33174-244">Description</span></span>|
|---|---|---|---|---|
|`configurationUrl`|<span data-ttu-id="33174-245">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="33174-245">String</span></span>|<span data-ttu-id="33174-246">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="33174-246">2048 characters</span></span>|<span data-ttu-id="33174-247">✔</span><span class="sxs-lookup"><span data-stu-id="33174-247">✔</span></span>|<span data-ttu-id="33174-248">Die https:// URL, die beim Konfigurieren der Registerkarte verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="33174-248">The https:// URL to use when configuring the tab.</span></span>|
|`canUpdateConfiguration`|<span data-ttu-id="33174-249">Boolesch</span><span class="sxs-lookup"><span data-stu-id="33174-249">Boolean</span></span>|||<span data-ttu-id="33174-250">Ein Wert, der angibt, ob eine Instanz der Konfiguration der Registerkarte vom Benutzer nach der Erstellung aktualisiert werden kann.</span><span class="sxs-lookup"><span data-stu-id="33174-250">A value indicating whether an instance of the tab's configuration can be updated by the user after creation.</span></span> <span data-ttu-id="33174-251">Standard: `true`</span><span class="sxs-lookup"><span data-stu-id="33174-251">Default: `true`</span></span>|
|`scopes`|<span data-ttu-id="33174-252">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="33174-252">Array of enum</span></span>|<span data-ttu-id="33174-253">1</span><span class="sxs-lookup"><span data-stu-id="33174-253">1</span></span>|<span data-ttu-id="33174-254">✔</span><span class="sxs-lookup"><span data-stu-id="33174-254">✔</span></span>|<span data-ttu-id="33174-255">Derzeit unterstützen konfigurierbare Registerkarten nur die `team` Bereiche und `groupchat` Bereiche.</span><span class="sxs-lookup"><span data-stu-id="33174-255">Currently, configurable tabs support only the `team` and `groupchat` scopes.</span></span> |
|`sharePointPreviewImage`|<span data-ttu-id="33174-256">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="33174-256">String</span></span>|<span data-ttu-id="33174-257">2048</span><span class="sxs-lookup"><span data-stu-id="33174-257">2048</span></span>||<span data-ttu-id="33174-258">Ein relativer Dateipfad zu einem Registerkartenvorschaubild zur Verwendung in SharePoint.</span><span class="sxs-lookup"><span data-stu-id="33174-258">A relative file path to a tab preview image for use in SharePoint.</span></span> <span data-ttu-id="33174-259">Größe 1024 x 768.</span><span class="sxs-lookup"><span data-stu-id="33174-259">Size 1024x768.</span></span> |
|`supportedSharePointHosts`|<span data-ttu-id="33174-260">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="33174-260">Array of enum</span></span>|<span data-ttu-id="33174-261">1</span><span class="sxs-lookup"><span data-stu-id="33174-261">1</span></span>||<span data-ttu-id="33174-262">Definiert, wie Ihre Registerkarte in SharePoint zur Verfügung gestellt wird.</span><span class="sxs-lookup"><span data-stu-id="33174-262">Defines how your tab will be made available in SharePoint.</span></span> <span data-ttu-id="33174-263">Optionen sind `sharePointFullPage` und `sharePointWebPart`</span><span class="sxs-lookup"><span data-stu-id="33174-263">Options are `sharePointFullPage` and `sharePointWebPart`</span></span> |

## <a name="statictabs"></a><span data-ttu-id="33174-264">staticTabs</span><span class="sxs-lookup"><span data-stu-id="33174-264">staticTabs</span></span>

<span data-ttu-id="33174-265">**Optional**</span><span class="sxs-lookup"><span data-stu-id="33174-265">**Optional**</span></span>

<span data-ttu-id="33174-266">Definiert eine Gruppe von Registerkarten, die standardmäßig "angeheftet" werden können, ohne dass der Benutzer sie manuell hinzufügt.</span><span class="sxs-lookup"><span data-stu-id="33174-266">Defines a set of tabs that can be "pinned" by default, without the user adding them manually.</span></span> <span data-ttu-id="33174-267">Im Bereich deklarierte statische `personal` Registerkarten werden immer an die persönliche Benutzeroberfläche der App angeheftet.</span><span class="sxs-lookup"><span data-stu-id="33174-267">Static tabs declared in `personal` scope are always pinned to the app's personal experience.</span></span> <span data-ttu-id="33174-268">Statische Registerkarten, die im Bereich deklariert `team` sind, werden derzeit nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="33174-268">Static tabs declared in the `team` scope are currently not supported.</span></span>

<span data-ttu-id="33174-269">Rendern sie Registerkarten mit adaptiven Karten, indem Sie `contentBotId` sie anstelle `contentUrl` des **staticTabs-Blocks** angeben.</span><span class="sxs-lookup"><span data-stu-id="33174-269">Render tabs with Adaptive Cards by specifying `contentBotId` instead of `contentUrl` in the **staticTabs** block.</span></span>

<span data-ttu-id="33174-270">Das Objekt ist ein Array (maximal 16 Elemente) mit allen Elementen des `object` Typs.</span><span class="sxs-lookup"><span data-stu-id="33174-270">The object is an array (maximum of 16 elements) with all elements of the type `object`.</span></span> <span data-ttu-id="33174-271">Dieser Block ist nur für Lösungen erforderlich, die eine statische Registerkartenlösung bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="33174-271">This block is required only for solutions that provide a static tab solution.</span></span>


|<span data-ttu-id="33174-272">Name</span><span class="sxs-lookup"><span data-stu-id="33174-272">Name</span></span>| <span data-ttu-id="33174-273">Typ</span><span class="sxs-lookup"><span data-stu-id="33174-273">Type</span></span>| <span data-ttu-id="33174-274">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="33174-274">Maximum size</span></span> | <span data-ttu-id="33174-275">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="33174-275">Required</span></span> | <span data-ttu-id="33174-276">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="33174-276">Description</span></span>|
|---|---|---|---|---|
|`entityId`|<span data-ttu-id="33174-277">String</span><span class="sxs-lookup"><span data-stu-id="33174-277">String</span></span>|<span data-ttu-id="33174-278">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="33174-278">64 characters</span></span>|<span data-ttu-id="33174-279">✔</span><span class="sxs-lookup"><span data-stu-id="33174-279">✔</span></span>|<span data-ttu-id="33174-280">Ein eindeutiger Bezeichner für die Entität, die auf der Registerkarte angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="33174-280">A unique identifier for the entity that the tab displays.</span></span>|
|`name`|<span data-ttu-id="33174-281">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="33174-281">String</span></span>|<span data-ttu-id="33174-282">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="33174-282">128 characters</span></span>|<span data-ttu-id="33174-283">✔</span><span class="sxs-lookup"><span data-stu-id="33174-283">✔</span></span>|<span data-ttu-id="33174-284">Der Anzeigename der Registerkarte in der Kanalschnittstelle.</span><span class="sxs-lookup"><span data-stu-id="33174-284">The display name of the tab in the channel interface.</span></span>|
|`contentUrl`|<span data-ttu-id="33174-285">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="33174-285">String</span></span>|<span data-ttu-id="33174-286">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="33174-286">2048 characters</span></span>|<span data-ttu-id="33174-287">✔</span><span class="sxs-lookup"><span data-stu-id="33174-287">✔</span></span>|<span data-ttu-id="33174-288">Die https:// URL, die auf die Entitäts-UI verweist, die im Teams Canvas angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="33174-288">The https:// URL that points to the entity UI to be displayed in the Teams canvas.</span></span>|
|`contentBotId`|   | | | <span data-ttu-id="33174-289">Die Microsoft Teams App-ID, die für den Bot im Bot Framework-Portal angegeben ist.</span><span class="sxs-lookup"><span data-stu-id="33174-289">The Microsoft Teams app ID specified for the bot in the Bot Framework portal.</span></span> |
|`websiteUrl`|<span data-ttu-id="33174-290">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="33174-290">String</span></span>|<span data-ttu-id="33174-291">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="33174-291">2048 characters</span></span>||<span data-ttu-id="33174-292">Die https:// URL, um darauf hinzuweisen, ob sich ein Benutzer für die Anzeige in einem Browser entscheidet.</span><span class="sxs-lookup"><span data-stu-id="33174-292">The https:// URL to point at if a user opts to view in a browser.</span></span>|
|`scopes`|<span data-ttu-id="33174-293">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="33174-293">Array of enum</span></span>|<span data-ttu-id="33174-294">1</span><span class="sxs-lookup"><span data-stu-id="33174-294">1</span></span>|<span data-ttu-id="33174-295">✔</span><span class="sxs-lookup"><span data-stu-id="33174-295">✔</span></span>|<span data-ttu-id="33174-296">Derzeit unterstützen statische Registerkarten nur den `personal` Bereich, was bedeutet, dass sie nur als Teil der persönlichen Benutzeroberfläche bereitgestellt werden können.</span><span class="sxs-lookup"><span data-stu-id="33174-296">Currently, static tabs support only the `personal` scope, which means it can be provisioned only as part of the personal experience.</span></span>|

## <a name="bots"></a><span data-ttu-id="33174-297">Bots</span><span class="sxs-lookup"><span data-stu-id="33174-297">bots</span></span>

<span data-ttu-id="33174-298">**Optional**</span><span class="sxs-lookup"><span data-stu-id="33174-298">**Optional**</span></span>

<span data-ttu-id="33174-299">Definiert eine Bot-Lösung zusammen mit optionalen Informationen wie Standardbefehlseigenschaften.</span><span class="sxs-lookup"><span data-stu-id="33174-299">Defines a bot solution, along with optional information such as default command properties.</span></span>

<span data-ttu-id="33174-300">Das Objekt ist ein Array (maximal 1 Element &mdash; ist derzeit nur ein Bot pro App zulässig) mit allen Elementen des `object` Typs.</span><span class="sxs-lookup"><span data-stu-id="33174-300">The object is an array (maximum of only 1 element&mdash;currently only one bot is allowed per app) with all elements of the type `object`.</span></span> <span data-ttu-id="33174-301">Dieser Block ist nur für Lösungen erforderlich, die eine Bot-Erfahrung bieten.</span><span class="sxs-lookup"><span data-stu-id="33174-301">This block is required only for solutions that provide a bot experience.</span></span>

|<span data-ttu-id="33174-302">Name</span><span class="sxs-lookup"><span data-stu-id="33174-302">Name</span></span>| <span data-ttu-id="33174-303">Typ</span><span class="sxs-lookup"><span data-stu-id="33174-303">Type</span></span>| <span data-ttu-id="33174-304">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="33174-304">Maximum size</span></span> | <span data-ttu-id="33174-305">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="33174-305">Required</span></span> | <span data-ttu-id="33174-306">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="33174-306">Description</span></span>|
|---|---|---|---|---|
|`botId`|<span data-ttu-id="33174-307">String</span><span class="sxs-lookup"><span data-stu-id="33174-307">String</span></span>|<span data-ttu-id="33174-308">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="33174-308">64 characters</span></span>|<span data-ttu-id="33174-309">✔</span><span class="sxs-lookup"><span data-stu-id="33174-309">✔</span></span>|<span data-ttu-id="33174-310">Die eindeutige Microsoft-App-ID für den Bot, wie bei Bot Framework registriert.</span><span class="sxs-lookup"><span data-stu-id="33174-310">The unique Microsoft app ID for the bot as registered with the Bot Framework.</span></span> <span data-ttu-id="33174-311">Dies kann durchaus mit der gesamten [App-ID](#id)übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="33174-311">This may well be the same as the overall [app ID](#id).</span></span>|
|`needsChannelSelector`|<span data-ttu-id="33174-312">Boolesch</span><span class="sxs-lookup"><span data-stu-id="33174-312">Boolean</span></span>|||<span data-ttu-id="33174-313">Beschreibt, ob der Bot einen Benutzerhinweis verwendet, um den Bot einem bestimmten Kanal hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="33174-313">Describes whether or not the bot utilizes a user hint to add the bot to a specific channel.</span></span> <span data-ttu-id="33174-314">Standard: `false`</span><span class="sxs-lookup"><span data-stu-id="33174-314">Default: `false`</span></span>|
|`isNotificationOnly`|<span data-ttu-id="33174-315">Boolesch</span><span class="sxs-lookup"><span data-stu-id="33174-315">Boolean</span></span>|||<span data-ttu-id="33174-316">Gibt an, ob ein Bot ein unidirektionaler Bot ausschließlich für Benachrichtigungen ist (im Gegensatz zu einem dialogorientierten Bot).</span><span class="sxs-lookup"><span data-stu-id="33174-316">Indicates whether a bot is a one-way, notification-only bot, as opposed to a conversational bot.</span></span> <span data-ttu-id="33174-317">Standard: `false`</span><span class="sxs-lookup"><span data-stu-id="33174-317">Default: `false`</span></span>|
|`supportsFiles`|<span data-ttu-id="33174-318">Boolesch</span><span class="sxs-lookup"><span data-stu-id="33174-318">Boolean</span></span>|||<span data-ttu-id="33174-319">Gibt an, ob der Bot die Möglichkeit zum Hochladen/Herunterladen von Dateien in persönliche Chats unterstützt.</span><span class="sxs-lookup"><span data-stu-id="33174-319">Indicates whether the bot supports the ability to upload/download files in personal chat.</span></span> <span data-ttu-id="33174-320">Standard: `false`</span><span class="sxs-lookup"><span data-stu-id="33174-320">Default: `false`</span></span>|
|`scopes`|<span data-ttu-id="33174-321">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="33174-321">Array of enum</span></span>|<span data-ttu-id="33174-322">3</span><span class="sxs-lookup"><span data-stu-id="33174-322">3</span></span>|<span data-ttu-id="33174-323">✔</span><span class="sxs-lookup"><span data-stu-id="33174-323">✔</span></span>|<span data-ttu-id="33174-324">Gibt an, ob der Bot eine Umgebung im Kontext eines Kanals in einem `team` oder Gruppenchat (`groupchat`) ist, oder aber eine Umgebung einzig für einen bestimmten Benutzer (`personal`).</span><span class="sxs-lookup"><span data-stu-id="33174-324">Specifies whether the bot offers an experience in the context of a channel in a `team`, in a group chat (`groupchat`), or an experience scoped to an individual user alone (`personal`).</span></span> <span data-ttu-id="33174-325">Diese Optionen sind nicht exklusiv.</span><span class="sxs-lookup"><span data-stu-id="33174-325">These options are non-exclusive.</span></span>|

### <a name="botscommandlists"></a><span data-ttu-id="33174-326">bots.commandLists</span><span class="sxs-lookup"><span data-stu-id="33174-326">bots.commandLists</span></span>

<span data-ttu-id="33174-327">Eine optionale Liste von Befehlen, die Ihr Bot Benutzern empfehlen kann.</span><span class="sxs-lookup"><span data-stu-id="33174-327">An optional list of commands that your bot can recommend to users.</span></span> <span data-ttu-id="33174-328">Das Objekt ist ein Array (maximal 2 Elemente) mit allen Elementen des `object` Typs. Sie müssen eine separate Befehlsliste für jeden Bereich definieren, den Ihr Bot unterstützt.</span><span class="sxs-lookup"><span data-stu-id="33174-328">The object is an array (maximum of 2 elements) with all elements of type `object`; you must define a separate command list for each scope that your bot supports.</span></span> <span data-ttu-id="33174-329">Weitere Informationen finden Sie unter [Bot-Menüs.](~/bots/how-to/create-a-bot-commands-menu.md)</span><span class="sxs-lookup"><span data-stu-id="33174-329">For more information, see [Bot menus](~/bots/how-to/create-a-bot-commands-menu.md).</span></span>

|<span data-ttu-id="33174-330">Name</span><span class="sxs-lookup"><span data-stu-id="33174-330">Name</span></span>| <span data-ttu-id="33174-331">Typ</span><span class="sxs-lookup"><span data-stu-id="33174-331">Type</span></span>| <span data-ttu-id="33174-332">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="33174-332">Maximum size</span></span> | <span data-ttu-id="33174-333">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="33174-333">Required</span></span> | <span data-ttu-id="33174-334">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="33174-334">Description</span></span>|
|---|---|---|---|---|
|`items.scopes`|<span data-ttu-id="33174-335">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="33174-335">array of enum</span></span>|<span data-ttu-id="33174-336">3</span><span class="sxs-lookup"><span data-stu-id="33174-336">3</span></span>|<span data-ttu-id="33174-337">✔</span><span class="sxs-lookup"><span data-stu-id="33174-337">✔</span></span>|<span data-ttu-id="33174-338">Gibt den Bereich an, für den die Befehlsliste gültig ist.</span><span class="sxs-lookup"><span data-stu-id="33174-338">Specifies the scope for which the command list is valid.</span></span> <span data-ttu-id="33174-339">Mögliche Optionen sind `team`, `personal` und `groupchat`.</span><span class="sxs-lookup"><span data-stu-id="33174-339">Options are `team`, `personal`, and `groupchat`.</span></span>|
|`items.commands`|<span data-ttu-id="33174-340">Array von Objekten</span><span class="sxs-lookup"><span data-stu-id="33174-340">array of objects</span></span>|<span data-ttu-id="33174-341">10</span><span class="sxs-lookup"><span data-stu-id="33174-341">10</span></span>|<span data-ttu-id="33174-342">✔</span><span class="sxs-lookup"><span data-stu-id="33174-342">✔</span></span>|<span data-ttu-id="33174-343">Ein Array von Befehlen, die der Bot unterstützt:</span><span class="sxs-lookup"><span data-stu-id="33174-343">An array of commands the bot supports:</span></span><br><span data-ttu-id="33174-344">`title`: der Bot-Befehlsname (Zeichenfolge, 32).</span><span class="sxs-lookup"><span data-stu-id="33174-344">`title`: the bot command name (string, 32).</span></span><br><span data-ttu-id="33174-345">`description`: eine einfache Beschreibung oder ein Beispiel für die Befehlssyntax und ihr Argument (Zeichenfolge, 128).</span><span class="sxs-lookup"><span data-stu-id="33174-345">`description`: a simple description or example of the command syntax and its argument (string, 128).</span></span>|

## <a name="connectors"></a><span data-ttu-id="33174-346">Steckverbinder</span><span class="sxs-lookup"><span data-stu-id="33174-346">connectors</span></span>

<span data-ttu-id="33174-347">**Optional**</span><span class="sxs-lookup"><span data-stu-id="33174-347">**Optional**</span></span>

<span data-ttu-id="33174-348">Der `connectors` Block definiert einen Office 365 Connector für die App.</span><span class="sxs-lookup"><span data-stu-id="33174-348">The `connectors` block defines an Office 365 Connector for the app.</span></span>

<span data-ttu-id="33174-349">Das Objekt ist ein Array (maximal 1 Element) mit allen Elementen des Typs `object` .</span><span class="sxs-lookup"><span data-stu-id="33174-349">The object is an array (maximum of 1 element) with all elements of type `object`.</span></span> <span data-ttu-id="33174-350">Dieser Block ist nur für Lösungen erforderlich, die einen Connector bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="33174-350">This block is required only for solutions that provide a Connector.</span></span>

|<span data-ttu-id="33174-351">Name</span><span class="sxs-lookup"><span data-stu-id="33174-351">Name</span></span>| <span data-ttu-id="33174-352">Typ</span><span class="sxs-lookup"><span data-stu-id="33174-352">Type</span></span>| <span data-ttu-id="33174-353">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="33174-353">Maximum size</span></span> | <span data-ttu-id="33174-354">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="33174-354">Required</span></span> | <span data-ttu-id="33174-355">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="33174-355">Description</span></span>|
|---|---|---|---|---|
|`configurationUrl`|<span data-ttu-id="33174-356">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="33174-356">String</span></span>|<span data-ttu-id="33174-357">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="33174-357">2048 characters</span></span>|<span data-ttu-id="33174-358">✔</span><span class="sxs-lookup"><span data-stu-id="33174-358">✔</span></span>|<span data-ttu-id="33174-359">Die https:// URL, die beim Konfigurieren des Connectors verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="33174-359">The https:// URL to use when configuring the connector.</span></span>|
|`connectorId`|<span data-ttu-id="33174-360">String</span><span class="sxs-lookup"><span data-stu-id="33174-360">String</span></span>|<span data-ttu-id="33174-361">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="33174-361">64 characters</span></span>|<span data-ttu-id="33174-362">✔</span><span class="sxs-lookup"><span data-stu-id="33174-362">✔</span></span>|<span data-ttu-id="33174-363">Ein eindeutiger Bezeichner für den Connector, der seiner ID im [Connectors Developer Dashboard](https://aka.ms/connectorsdashboard)entspricht.</span><span class="sxs-lookup"><span data-stu-id="33174-363">A unique identifier for the Connector that matches its ID in the [Connectors Developer Dashboard](https://aka.ms/connectorsdashboard).</span></span>|
|`scopes`|<span data-ttu-id="33174-364">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="33174-364">Array of enum</span></span>|<span data-ttu-id="33174-365">1</span><span class="sxs-lookup"><span data-stu-id="33174-365">1</span></span>|<span data-ttu-id="33174-366">✔</span><span class="sxs-lookup"><span data-stu-id="33174-366">✔</span></span>|<span data-ttu-id="33174-367">Gibt an, ob der Connector eine Erfahrung im Kontext eines Kanals in einem oder `team` eine Benutzeroberfläche bietet, die auf einen einzelnen Benutzer beschränkt ist ( `personal` ).</span><span class="sxs-lookup"><span data-stu-id="33174-367">Specifies whether the Connector offers an experience in the context of a channel in a `team`, or an experience scoped to an individual user alone (`personal`).</span></span> <span data-ttu-id="33174-368">Derzeit wird nur der `team` Bereich unterstützt.</span><span class="sxs-lookup"><span data-stu-id="33174-368">Currently, only the `team` scope is supported.</span></span>|

## <a name="composeextensions"></a><span data-ttu-id="33174-369">composeExtensions</span><span class="sxs-lookup"><span data-stu-id="33174-369">composeExtensions</span></span>

<span data-ttu-id="33174-370">**Optional**</span><span class="sxs-lookup"><span data-stu-id="33174-370">**Optional**</span></span>

<span data-ttu-id="33174-371">Definiert eine Messaging-Erweiterung für die App.</span><span class="sxs-lookup"><span data-stu-id="33174-371">Defines a messaging extension for the app.</span></span>

> [!NOTE]
> <span data-ttu-id="33174-372">Der Name des Features wurde im November 2017 von "Erstellerweiterung" in "Messaging-Erweiterung" geändert, aber der Manifestname bleibt unverändert, sodass vorhandene Erweiterungen weiterhin funktionieren.</span><span class="sxs-lookup"><span data-stu-id="33174-372">The name of the feature was changed from "compose extension" to "messaging extension" in November, 2017, but the manifest name remains the same so that existing extensions continue to function.</span></span>

<span data-ttu-id="33174-373">Das Objekt ist ein Array (maximal 1 Element) mit allen Elementen des Typs `object` .</span><span class="sxs-lookup"><span data-stu-id="33174-373">The object is an array (maximum of 1 element) with all elements of type `object`.</span></span> <span data-ttu-id="33174-374">Dieser Block ist nur für Lösungen erforderlich, die eine Messaging-Erweiterung bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="33174-374">This block is required only for solutions that provide a messaging extension.</span></span>

|<span data-ttu-id="33174-375">Name</span><span class="sxs-lookup"><span data-stu-id="33174-375">Name</span></span>| <span data-ttu-id="33174-376">Typ</span><span class="sxs-lookup"><span data-stu-id="33174-376">Type</span></span> | <span data-ttu-id="33174-377">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="33174-377">Maximum Size</span></span> | <span data-ttu-id="33174-378">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="33174-378">Required</span></span> | <span data-ttu-id="33174-379">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="33174-379">Description</span></span>|
|---|---|---|---|---|
|`botId`|<span data-ttu-id="33174-380">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="33174-380">String</span></span>|<span data-ttu-id="33174-381">64</span><span class="sxs-lookup"><span data-stu-id="33174-381">64</span></span>|<span data-ttu-id="33174-382">✔</span><span class="sxs-lookup"><span data-stu-id="33174-382">✔</span></span>|<span data-ttu-id="33174-383">Die eindeutige Microsoft-App-ID für den Bot, der die Messaging-Erweiterung unterstützt, wie beim Bot Framework registriert.</span><span class="sxs-lookup"><span data-stu-id="33174-383">The unique Microsoft app ID for the bot that backs the messaging extension, as registered with the Bot Framework.</span></span> <span data-ttu-id="33174-384">Dies kann durchaus mit der gesamten [App-ID](#id)übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="33174-384">This may well be the same as the overall [app ID](#id).</span></span>|
|`canUpdateConfiguration`|<span data-ttu-id="33174-385">Boolesch</span><span class="sxs-lookup"><span data-stu-id="33174-385">Boolean</span></span>|||<span data-ttu-id="33174-386">Ein Wert, der angibt, ob die Konfiguration einer Messaging-Erweiterung vom Benutzer aktualisiert werden kann.</span><span class="sxs-lookup"><span data-stu-id="33174-386">A value indicating whether the configuration of a messaging extension can be updated by the user.</span></span> <span data-ttu-id="33174-387">Der Standardwert lautet `false`.</span><span class="sxs-lookup"><span data-stu-id="33174-387">The default is `false`.</span></span>|
|`commands`|<span data-ttu-id="33174-388">Array des Objekts</span><span class="sxs-lookup"><span data-stu-id="33174-388">Array of object</span></span>|<span data-ttu-id="33174-389">10</span><span class="sxs-lookup"><span data-stu-id="33174-389">10</span></span>|<span data-ttu-id="33174-390">✔</span><span class="sxs-lookup"><span data-stu-id="33174-390">✔</span></span>|<span data-ttu-id="33174-391">Array von Befehlen, die von der Messaging-Erweiterung unterstützt werden</span><span class="sxs-lookup"><span data-stu-id="33174-391">Array of commands the messaging extension supports</span></span>|

### <a name="composeextensionscommands"></a><span data-ttu-id="33174-392">composeExtensions.commands</span><span class="sxs-lookup"><span data-stu-id="33174-392">composeExtensions.commands</span></span>

<span data-ttu-id="33174-393">Ihre Messaging-Erweiterung sollte einen oder mehrere Befehle deklarieren.</span><span class="sxs-lookup"><span data-stu-id="33174-393">Your messaging extension should declare one or more commands.</span></span> <span data-ttu-id="33174-394">Jeder Befehl wird in Microsoft Teams als potenzielle Interaktion vom UI-basierten Einstiegspunkt angezeigt.</span><span class="sxs-lookup"><span data-stu-id="33174-394">Each command appears in Microsoft Teams as a potential interaction from the UI-based entry point.</span></span> <span data-ttu-id="33174-395">Es gibt maximal 10 Befehle.</span><span class="sxs-lookup"><span data-stu-id="33174-395">There is a maximum of 10 commands.</span></span>

<span data-ttu-id="33174-396">Jedes Befehlselement ist ein Objekt mit der folgenden Struktur:</span><span class="sxs-lookup"><span data-stu-id="33174-396">Each command item is an object with the following structure:</span></span>

|<span data-ttu-id="33174-397">Name</span><span class="sxs-lookup"><span data-stu-id="33174-397">Name</span></span>| <span data-ttu-id="33174-398">Typ</span><span class="sxs-lookup"><span data-stu-id="33174-398">Type</span></span>| <span data-ttu-id="33174-399">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="33174-399">Maximum size</span></span> | <span data-ttu-id="33174-400">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="33174-400">Required</span></span> | <span data-ttu-id="33174-401">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="33174-401">Description</span></span>|
|---|---|---|---|---|
|`id`|<span data-ttu-id="33174-402">String</span><span class="sxs-lookup"><span data-stu-id="33174-402">String</span></span>|<span data-ttu-id="33174-403">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="33174-403">64 characters</span></span>|<span data-ttu-id="33174-404">✔</span><span class="sxs-lookup"><span data-stu-id="33174-404">✔</span></span>|<span data-ttu-id="33174-405">Die ID für den Befehl.</span><span class="sxs-lookup"><span data-stu-id="33174-405">The ID for the command.</span></span>|
|`type`|<span data-ttu-id="33174-406">String</span><span class="sxs-lookup"><span data-stu-id="33174-406">String</span></span>|<span data-ttu-id="33174-407">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="33174-407">64 characters</span></span>||<span data-ttu-id="33174-408">Typ des Befehls.</span><span class="sxs-lookup"><span data-stu-id="33174-408">Type of the command.</span></span> <span data-ttu-id="33174-409">Eine von `query` oder `action` .</span><span class="sxs-lookup"><span data-stu-id="33174-409">One of `query` or `action`.</span></span> <span data-ttu-id="33174-410">Standard: `query`</span><span class="sxs-lookup"><span data-stu-id="33174-410">Default: `query`</span></span>|
|`title`|<span data-ttu-id="33174-411">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="33174-411">String</span></span>|<span data-ttu-id="33174-412">32 Zeichen</span><span class="sxs-lookup"><span data-stu-id="33174-412">32 characters</span></span>|<span data-ttu-id="33174-413">✔</span><span class="sxs-lookup"><span data-stu-id="33174-413">✔</span></span>|<span data-ttu-id="33174-414">Der benutzerfreundliche Befehlsname.</span><span class="sxs-lookup"><span data-stu-id="33174-414">The user-friendly command name.</span></span>|
|`description`|<span data-ttu-id="33174-415">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="33174-415">String</span></span>|<span data-ttu-id="33174-416">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="33174-416">128 characters</span></span>||<span data-ttu-id="33174-417">Die Beschreibung, die Benutzern angezeigt wird, um den Zweck dieses Befehls anzugeben.</span><span class="sxs-lookup"><span data-stu-id="33174-417">The description that appears to users to indicate the purpose of this command.</span></span>|
|`initialRun`|<span data-ttu-id="33174-418">Boolesch</span><span class="sxs-lookup"><span data-stu-id="33174-418">Boolean</span></span>|||<span data-ttu-id="33174-419">Ein boolescher Wert, der angibt, ob der Befehl anfänglich ohne Parameter ausgeführt werden soll.</span><span class="sxs-lookup"><span data-stu-id="33174-419">A Boolean value that indicates whether the command should be run initially with no parameters.</span></span> <span data-ttu-id="33174-420">Standard: `false`</span><span class="sxs-lookup"><span data-stu-id="33174-420">Default: `false`</span></span>|
|`context`|<span data-ttu-id="33174-421">Array von Zeichenfolgen</span><span class="sxs-lookup"><span data-stu-id="33174-421">Array of Strings</span></span>|<span data-ttu-id="33174-422">3</span><span class="sxs-lookup"><span data-stu-id="33174-422">3</span></span>||<span data-ttu-id="33174-423">Definiert, von wo aus die Nachrichtenerweiterung aufgerufen werden kann.</span><span class="sxs-lookup"><span data-stu-id="33174-423">Defines where the message extension can be invoked from.</span></span> <span data-ttu-id="33174-424">Eine beliebige Kombination von `compose` , `commandBox` , `message` .</span><span class="sxs-lookup"><span data-stu-id="33174-424">Any combination of `compose`, `commandBox`, `message`.</span></span> <span data-ttu-id="33174-425">Der Standardwert ist `["compose", "commandBox"]`</span><span class="sxs-lookup"><span data-stu-id="33174-425">Default is `["compose", "commandBox"]`</span></span>|
|`fetchTask`|<span data-ttu-id="33174-426">Boolesch</span><span class="sxs-lookup"><span data-stu-id="33174-426">Boolean</span></span>|||<span data-ttu-id="33174-427">Ein boolescher Wert, der angibt, ob das Aufgabenmodul dynamisch abgerufen werden soll.</span><span class="sxs-lookup"><span data-stu-id="33174-427">A boolean value that indicates if it should fetch the task module dynamically.</span></span>|
|`taskInfo`|<span data-ttu-id="33174-428">Objekt</span><span class="sxs-lookup"><span data-stu-id="33174-428">Object</span></span>|||<span data-ttu-id="33174-429">Geben Sie das Aufgabenmodul an, das vorab geladen werden soll, wenn Sie einen Messaging-Erweiterungsbefehl verwenden.</span><span class="sxs-lookup"><span data-stu-id="33174-429">Specify the task module to preload when using a messaging extension command.</span></span>|
|`taskInfo.title`|<span data-ttu-id="33174-430">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="33174-430">String</span></span>|<span data-ttu-id="33174-431">64</span><span class="sxs-lookup"><span data-stu-id="33174-431">64</span></span>||<span data-ttu-id="33174-432">Titel des ersten Dialogfelds.</span><span class="sxs-lookup"><span data-stu-id="33174-432">Initial dialog title.</span></span>|
|`taskInfo.width`|<span data-ttu-id="33174-433">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="33174-433">String</span></span>|||<span data-ttu-id="33174-434">Dialogbreite – entweder eine Zahl in Pixeln oder ein Standardlayout, z. B. "groß", "mittel" oder "klein".</span><span class="sxs-lookup"><span data-stu-id="33174-434">Dialog width - either a number in pixels or default layout such as 'large', 'medium', or 'small'.</span></span>|
|`taskInfo.height`|<span data-ttu-id="33174-435">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="33174-435">String</span></span>|||<span data-ttu-id="33174-436">Dialoghöhe – entweder eine Zahl in Pixeln oder ein Standardlayout, z. B. "groß", "mittel" oder "klein".</span><span class="sxs-lookup"><span data-stu-id="33174-436">Dialog height - either a number in pixels or default layout such as 'large', 'medium', or 'small'.</span></span>|
|`taskInfo.url`|<span data-ttu-id="33174-437">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="33174-437">String</span></span>|||<span data-ttu-id="33174-438">Ursprüngliche Webansichts-URL.</span><span class="sxs-lookup"><span data-stu-id="33174-438">Initial webview URL.</span></span>|
|`messageHandlers`|<span data-ttu-id="33174-439">Array von Objekten</span><span class="sxs-lookup"><span data-stu-id="33174-439">Array of Objects</span></span>|<span data-ttu-id="33174-440">5 </span><span class="sxs-lookup"><span data-stu-id="33174-440">5</span></span>||<span data-ttu-id="33174-441">Eine Liste von Handlern, mit denen Apps aufgerufen werden können, wenn bestimmte Bedingungen erfüllt sind.</span><span class="sxs-lookup"><span data-stu-id="33174-441">A list of handlers that allow apps to be invoked when certain conditions are met.</span></span> <span data-ttu-id="33174-442">Domänen müssen auch in aufgeführt `validDomains` werden.</span><span class="sxs-lookup"><span data-stu-id="33174-442">Domains must also be listed in `validDomains`.</span></span>|
|`messageHandlers.type`|<span data-ttu-id="33174-443">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="33174-443">String</span></span>|||<span data-ttu-id="33174-444">Der Typ des Nachrichtenhandlers.</span><span class="sxs-lookup"><span data-stu-id="33174-444">The type of message handler.</span></span> <span data-ttu-id="33174-445">Muss `"link"` sein.</span><span class="sxs-lookup"><span data-stu-id="33174-445">Must be `"link"`.</span></span>|
|`messageHandlers.value.domains`|<span data-ttu-id="33174-446">Array von Zeichenfolgen</span><span class="sxs-lookup"><span data-stu-id="33174-446">Array of Strings</span></span>|||<span data-ttu-id="33174-447">Array von Domänen, für die sich der Linknachrichtenhandler registrieren kann.</span><span class="sxs-lookup"><span data-stu-id="33174-447">Array of domains that the link message handler can register for.</span></span>|
|`parameters`|<span data-ttu-id="33174-448">Array des Objekts</span><span class="sxs-lookup"><span data-stu-id="33174-448">Array of object</span></span>|<span data-ttu-id="33174-449">5 </span><span class="sxs-lookup"><span data-stu-id="33174-449">5</span></span>|<span data-ttu-id="33174-450">✔</span><span class="sxs-lookup"><span data-stu-id="33174-450">✔</span></span>|<span data-ttu-id="33174-451">Die Liste der Parameter, die der Befehl verwendet.</span><span class="sxs-lookup"><span data-stu-id="33174-451">The list of parameters the command takes.</span></span> <span data-ttu-id="33174-452">Minimum: 1; Maximum: 5</span><span class="sxs-lookup"><span data-stu-id="33174-452">Minimum: 1; maximum: 5</span></span>|
|`parameter.name`|<span data-ttu-id="33174-453">String</span><span class="sxs-lookup"><span data-stu-id="33174-453">String</span></span>|<span data-ttu-id="33174-454">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="33174-454">64 characters</span></span>|<span data-ttu-id="33174-455">✔</span><span class="sxs-lookup"><span data-stu-id="33174-455">✔</span></span>|<span data-ttu-id="33174-456">Der Name des Parameters, wie er im Client angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="33174-456">The name of the parameter as it appears in the client.</span></span> <span data-ttu-id="33174-457">Dies ist in der Benutzeranforderung enthalten.</span><span class="sxs-lookup"><span data-stu-id="33174-457">This is included in the user request.</span></span>|
|`parameter.title`|<span data-ttu-id="33174-458">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="33174-458">String</span></span>|<span data-ttu-id="33174-459">32 Zeichen</span><span class="sxs-lookup"><span data-stu-id="33174-459">32 characters</span></span>|<span data-ttu-id="33174-460">✔</span><span class="sxs-lookup"><span data-stu-id="33174-460">✔</span></span>|<span data-ttu-id="33174-461">Benutzerfreundlicher Titel für den Parameter.</span><span class="sxs-lookup"><span data-stu-id="33174-461">User-friendly title for the parameter.</span></span>|
|`parameter.description`|<span data-ttu-id="33174-462">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="33174-462">String</span></span>|<span data-ttu-id="33174-463">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="33174-463">128 characters</span></span>||<span data-ttu-id="33174-464">Benutzerfreundliche Zeichenfolge, die den Zweck dieses Parameters beschreibt.</span><span class="sxs-lookup"><span data-stu-id="33174-464">User-friendly string that describes this parameter’s purpose.</span></span>|
|`parameter.inputType`|<span data-ttu-id="33174-465">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="33174-465">String</span></span>|<span data-ttu-id="33174-466">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="33174-466">128 characters</span></span>||<span data-ttu-id="33174-467">Definiert den Typ des Steuerelements, das in einem Aufgabenmodul für angezeigt `fetchTask: true` wird.</span><span class="sxs-lookup"><span data-stu-id="33174-467">Defines the type of control displayed on a task module for `fetchTask: true`.</span></span> <span data-ttu-id="33174-468">Einer von `text` , , , , , , `textarea` `number` `date` `time` `toggle` `choiceset` .</span><span class="sxs-lookup"><span data-stu-id="33174-468">One of `text`, `textarea`, `number`, `date`, `time`, `toggle`, `choiceset`.</span></span>|
|`parameter.choices`|<span data-ttu-id="33174-469">Array von Objekten</span><span class="sxs-lookup"><span data-stu-id="33174-469">Array of Objects</span></span>|<span data-ttu-id="33174-470">10</span><span class="sxs-lookup"><span data-stu-id="33174-470">10</span></span>||<span data-ttu-id="33174-471">Die Auswahloptionen für die `choiceset` .</span><span class="sxs-lookup"><span data-stu-id="33174-471">The choice options for the `choiceset`.</span></span> <span data-ttu-id="33174-472">Wird nur verwendet, wenn `parameter.inputType` `choiceset` .</span><span class="sxs-lookup"><span data-stu-id="33174-472">Use only when `parameter.inputType` is `choiceset`.</span></span>|
|`parameter.choices.title`|<span data-ttu-id="33174-473">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="33174-473">String</span></span>|<span data-ttu-id="33174-474">128</span><span class="sxs-lookup"><span data-stu-id="33174-474">128</span></span>||<span data-ttu-id="33174-475">Titel der Wahl.</span><span class="sxs-lookup"><span data-stu-id="33174-475">Title of the choice.</span></span>|
|`parameter.choices.value`|<span data-ttu-id="33174-476">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="33174-476">String</span></span>|<span data-ttu-id="33174-477">512</span><span class="sxs-lookup"><span data-stu-id="33174-477">512</span></span>||<span data-ttu-id="33174-478">Value of the choice.</span><span class="sxs-lookup"><span data-stu-id="33174-478">Value of the choice.</span></span>|

## <a name="permissions"></a><span data-ttu-id="33174-479">Berechtigungen</span><span class="sxs-lookup"><span data-stu-id="33174-479">permissions</span></span>

<span data-ttu-id="33174-480">**Optional**</span><span class="sxs-lookup"><span data-stu-id="33174-480">**Optional**</span></span>

<span data-ttu-id="33174-481">Ein `string` Array, das angibt, welche Berechtigungen die App anfordert, wodurch Endbenutzer wissen, wie die Erweiterung ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="33174-481">An array of `string` which specifies which permissions the app requests, which lets end users know how the extension will perform.</span></span> <span data-ttu-id="33174-482">Die folgenden Optionen sind nicht exklusiv:</span><span class="sxs-lookup"><span data-stu-id="33174-482">The following options are non-exclusive:</span></span>

* <span data-ttu-id="33174-483">`identity`&emsp;Erfordert Benutzeridentitätsinformationen.</span><span class="sxs-lookup"><span data-stu-id="33174-483">`identity` &emsp; Requires user identity information.</span></span>
* <span data-ttu-id="33174-484">`messageTeamMembers`&emsp;Erfordert die Berechtigung, direkte Nachrichten an Teammitglieder zu senden.</span><span class="sxs-lookup"><span data-stu-id="33174-484">`messageTeamMembers` &emsp; Requires permission to send direct messages to team members.</span></span>

<span data-ttu-id="33174-485">Wenn Sie diese Berechtigungen beim Aktualisieren Ihrer App ändern, wiederholen Ihre Benutzer den Zustimmungsprozess bei der ersten Ausführung der aktualisierten App.</span><span class="sxs-lookup"><span data-stu-id="33174-485">Changing these permissions when updating your app will cause your users to repeat the consent process the first time they run the updated app.</span></span>

## <a name="devicepermissions"></a><span data-ttu-id="33174-486">devicePermissions</span><span class="sxs-lookup"><span data-stu-id="33174-486">devicePermissions</span></span>

<span data-ttu-id="33174-487">**Optional** Array von Zeichenfolgen</span><span class="sxs-lookup"><span data-stu-id="33174-487">**Optional** Array of Strings</span></span>

<span data-ttu-id="33174-488">Gibt die systemeigenen Features auf dem Gerät eines Benutzers an, auf die Ihre App Zugriff anfordern kann.</span><span class="sxs-lookup"><span data-stu-id="33174-488">Specifies the native features on a user's device that your app may request access to.</span></span> <span data-ttu-id="33174-489">Mögliche Optionen sind:</span><span class="sxs-lookup"><span data-stu-id="33174-489">Options are:</span></span>

* `geolocation`
* `media`
* `notifications`
* `midi`
* `openExternal`

## <a name="validdomains"></a><span data-ttu-id="33174-490">validDomains</span><span class="sxs-lookup"><span data-stu-id="33174-490">validDomains</span></span>

<span data-ttu-id="33174-491">**Optional,** außer **erforderlich,** sofern angegeben</span><span class="sxs-lookup"><span data-stu-id="33174-491">**Optional**, except **Required** where noted</span></span>

<span data-ttu-id="33174-492">Eine Liste der gültigen Domänen, von denen die App erwartet, dass inhalte geladen werden.</span><span class="sxs-lookup"><span data-stu-id="33174-492">A list of valid domains from which the app expects to load any content.</span></span> <span data-ttu-id="33174-493">Domäneneinträge können Platzhalter enthalten, `*.example.com` z. B. .</span><span class="sxs-lookup"><span data-stu-id="33174-493">Domain listings can include wildcards, for example `*.example.com`.</span></span> <span data-ttu-id="33174-494">Dies entspricht genau einem Segment der Domäne. wenn Sie übereinstimmen `a.b.example.com` müssen, verwenden Sie `*.*.example.com` .</span><span class="sxs-lookup"><span data-stu-id="33174-494">This matches exactly one segment of the domain; if you need to match `a.b.example.com` then use `*.*.example.com`.</span></span> <span data-ttu-id="33174-495">Wenn Ihre Registerkartenkonfiguration oder Inhalts-UI zu einer anderen Domäne als der für die Registerkartenkonfiguration verwendeten navigieren muss, muss diese Domäne hier angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="33174-495">If your tab configuration or content UI needs to navigate to any other domain besides the one use for tab configuration, that domain must be specified here.</span></span>

<span data-ttu-id="33174-496">Es ist jedoch **nicht** erforderlich, die Domänen von Identitätsanbietern, die Sie unterstützen möchten, in Ihre App einzuschließen.</span><span class="sxs-lookup"><span data-stu-id="33174-496">It is **not** necessary to include the domains of identity providers you want to support in your app, however.</span></span> <span data-ttu-id="33174-497">Um sich beispielsweise mithilfe einer Google-ID zu authentifizieren, ist es erforderlich, zu accounts.google.com umzuleiten, sie sollten jedoch keine accounts.google.com in `validDomains[]` einschließen.</span><span class="sxs-lookup"><span data-stu-id="33174-497">For example, to authenticate using a Google ID, it's necessary to redirect to accounts.google.com, but you should not include accounts.google.com in `validDomains[]`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="33174-498">Fügen Sie keine Domänen hinzu, die sich außerhalb Ihres Steuerelements befinden, entweder direkt oder über Platzhalter.</span><span class="sxs-lookup"><span data-stu-id="33174-498">Do not add domains that are outside your control, either directly or via wildcards.</span></span> <span data-ttu-id="33174-499">Ist z. `yourapp.onmicrosoft.com` B. gültig, aber `*.onmicrosoft.com` nicht gültig.</span><span class="sxs-lookup"><span data-stu-id="33174-499">For example, `yourapp.onmicrosoft.com` is valid, but `*.onmicrosoft.com` is not valid.</span></span>

<span data-ttu-id="33174-500">Das Objekt ist ein Array mit allen Elementen des Typs `string` .</span><span class="sxs-lookup"><span data-stu-id="33174-500">The object is an array with all elements of the type `string`.</span></span>

## <a name="webapplicationinfo"></a><span data-ttu-id="33174-501">webApplicationInfo</span><span class="sxs-lookup"><span data-stu-id="33174-501">webApplicationInfo</span></span>

<span data-ttu-id="33174-502">**Optional**</span><span class="sxs-lookup"><span data-stu-id="33174-502">**Optional**</span></span>

<span data-ttu-id="33174-503">Geben Sie Ihre AAD-App-ID und Graph Informationen an, um Benutzern zu helfen, sich nahtlos bei Ihrer AAD-App anzumelden.</span><span class="sxs-lookup"><span data-stu-id="33174-503">Specify your AAD App ID and Graph information to help users seamlessly sign into your AAD app.</span></span>

|<span data-ttu-id="33174-504">Name</span><span class="sxs-lookup"><span data-stu-id="33174-504">Name</span></span>| <span data-ttu-id="33174-505">Typ</span><span class="sxs-lookup"><span data-stu-id="33174-505">Type</span></span>| <span data-ttu-id="33174-506">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="33174-506">Maximum size</span></span> | <span data-ttu-id="33174-507">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="33174-507">Required</span></span> | <span data-ttu-id="33174-508">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="33174-508">Description</span></span>|
|---|---|---|---|---|
|`id`|<span data-ttu-id="33174-509">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="33174-509">String</span></span>|<span data-ttu-id="33174-510">36 Zeichen</span><span class="sxs-lookup"><span data-stu-id="33174-510">36 characters</span></span>|<span data-ttu-id="33174-511">✔</span><span class="sxs-lookup"><span data-stu-id="33174-511">✔</span></span>|<span data-ttu-id="33174-512">AAD-Anwendungs-ID der App.</span><span class="sxs-lookup"><span data-stu-id="33174-512">AAD application id of the app.</span></span> <span data-ttu-id="33174-513">Diese ID muss eine GUID sein.</span><span class="sxs-lookup"><span data-stu-id="33174-513">This id must be a GUID.</span></span>|
|`resource`|<span data-ttu-id="33174-514">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="33174-514">String</span></span>|<span data-ttu-id="33174-515">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="33174-515">2048 characters</span></span>|<span data-ttu-id="33174-516">✔</span><span class="sxs-lookup"><span data-stu-id="33174-516">✔</span></span>|<span data-ttu-id="33174-517">Ressourcen-URL der App zum Abrufen des Authentifizierungstokens für SSO.</span><span class="sxs-lookup"><span data-stu-id="33174-517">Resource url of app for acquiring auth token for SSO.</span></span>|
|`applicationPermissions`|<span data-ttu-id="33174-518">Array</span><span class="sxs-lookup"><span data-stu-id="33174-518">Array</span></span>|<span data-ttu-id="33174-519">Maximal 100 Elemente</span><span class="sxs-lookup"><span data-stu-id="33174-519">Maximum 100 items</span></span>|<span data-ttu-id="33174-520">✔</span><span class="sxs-lookup"><span data-stu-id="33174-520">✔</span></span>|<span data-ttu-id="33174-521">Ressourcenberechtigungen für die Anwendung.</span><span class="sxs-lookup"><span data-stu-id="33174-521">Resource permissions for application.</span></span>|

## <a name="configurableproperties"></a><span data-ttu-id="33174-522">configurableProperties</span><span class="sxs-lookup"><span data-stu-id="33174-522">configurableProperties</span></span>

<span data-ttu-id="33174-523">**Optional** – Array</span><span class="sxs-lookup"><span data-stu-id="33174-523">**Optional** - array</span></span>

<span data-ttu-id="33174-524">Der `configurableProperties` Block definiert die App-Eigenschaften, die Teams Administratoren anpassen können.</span><span class="sxs-lookup"><span data-stu-id="33174-524">The `configurableProperties` block defines the app properties that Teams admins can customize.</span></span> <span data-ttu-id="33174-525">Weitere Informationen finden Sie unter Aktivieren der [App-Anpassung.](~/concepts/design/enable-app-customization.md)</span><span class="sxs-lookup"><span data-stu-id="33174-525">For more information, see [enable app customization](~/concepts/design/enable-app-customization.md).</span></span>

> [!NOTE]
> <span data-ttu-id="33174-526">Es muss mindestens eine Eigenschaft definiert werden.</span><span class="sxs-lookup"><span data-stu-id="33174-526">A minimum of one property must be defined.</span></span> <span data-ttu-id="33174-527">Sie können maximal neun Eigenschaften in diesem Block definieren.</span><span class="sxs-lookup"><span data-stu-id="33174-527">You can define a maximum of nine properties in this block.</span></span>

<span data-ttu-id="33174-528">Sie können eine der folgenden Eigenschaften definieren:</span><span class="sxs-lookup"><span data-stu-id="33174-528">You can define any of the following properties:</span></span>

* <span data-ttu-id="33174-529">`name`: Der Anzeigename der App.</span><span class="sxs-lookup"><span data-stu-id="33174-529">`name`: The app's display name.</span></span>
* <span data-ttu-id="33174-530">`shortDescription`: Die kurze Beschreibung der App.</span><span class="sxs-lookup"><span data-stu-id="33174-530">`shortDescription`: The app's short description.</span></span>
* <span data-ttu-id="33174-531">`longDescription`: Die ausführliche Beschreibung der App.</span><span class="sxs-lookup"><span data-stu-id="33174-531">`longDescription`: The app's detailed description.</span></span>
* <span data-ttu-id="33174-532">`smallImageUrl`: Das Gliederungssymbol der App.</span><span class="sxs-lookup"><span data-stu-id="33174-532">`smallImageUrl`: The app's outline icon.</span></span>
* <span data-ttu-id="33174-533">`largeImageUrl`: Das Farbsymbol der App.</span><span class="sxs-lookup"><span data-stu-id="33174-533">`largeImageUrl`: The app's color icon.</span></span>
* <span data-ttu-id="33174-534">`accentColor`: Die Farbe, die in Verbindung mit und als Hintergrund für Ihre Gliederungssymbole verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="33174-534">`accentColor`: The color to use in conjunction with and as a background for your outline icons.</span></span>
* <span data-ttu-id="33174-535">`developerUrl`: Die HTTPS-URL der Website des Entwicklers.</span><span class="sxs-lookup"><span data-stu-id="33174-535">`developerUrl`: The HTTPS URL of the developer's website.</span></span>
* <span data-ttu-id="33174-536">`privacyUrl`: Die HTTPS-URL der Datenschutzrichtlinie des Entwicklers.</span><span class="sxs-lookup"><span data-stu-id="33174-536">`privacyUrl`: The HTTPS URL of the developer's privacy policy.</span></span>
* <span data-ttu-id="33174-537">`termsOfUseUrl`: Die HTTPS-URL der Nutzungsbedingungen des Entwicklers.</span><span class="sxs-lookup"><span data-stu-id="33174-537">`termsOfUseUrl`: The HTTPS URL of the developer's terms of use.</span></span>

## <a name="defaultinstallscope"></a><span data-ttu-id="33174-538">defaultInstallScope</span><span class="sxs-lookup"><span data-stu-id="33174-538">defaultInstallScope</span></span>

<span data-ttu-id="33174-539">**Optional** – Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="33174-539">**Optional** - string</span></span>

<span data-ttu-id="33174-540">Gibt den standardmäßig für diese App definierten Installationsumfang an.</span><span class="sxs-lookup"><span data-stu-id="33174-540">Specifies the install scope defined for this app by default.</span></span> <span data-ttu-id="33174-541">Der definierte Bereich ist die Option, die auf der Schaltfläche angezeigt wird, wenn ein Benutzer versucht, die App hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="33174-541">The defined scope will be the option displayed on the button when a user tries to add the app.</span></span> <span data-ttu-id="33174-542">Mögliche Optionen sind:</span><span class="sxs-lookup"><span data-stu-id="33174-542">Options are:</span></span>
* `personal`
* `team`
* `groupchat`
* `meetings`

## <a name="defaultgroupcapability"></a><span data-ttu-id="33174-543">defaultGroupCapability</span><span class="sxs-lookup"><span data-stu-id="33174-543">defaultGroupCapability</span></span>

<span data-ttu-id="33174-544">**Optional** – Objekt</span><span class="sxs-lookup"><span data-stu-id="33174-544">**Optional** - object</span></span>

<span data-ttu-id="33174-545">Wenn ein Gruppeninstallationsbereich ausgewählt ist, wird die Standardfunktion definiert, wenn der Benutzer die App installiert.</span><span class="sxs-lookup"><span data-stu-id="33174-545">When a group install scope is selected, it will define the default capability when the user installs the app.</span></span> <span data-ttu-id="33174-546">Mögliche Optionen sind:</span><span class="sxs-lookup"><span data-stu-id="33174-546">Options are:</span></span>
* `team`
* `groupchat`
* `meetings`
 
|<span data-ttu-id="33174-547">Name</span><span class="sxs-lookup"><span data-stu-id="33174-547">Name</span></span>| <span data-ttu-id="33174-548">Typ</span><span class="sxs-lookup"><span data-stu-id="33174-548">Type</span></span>| <span data-ttu-id="33174-549">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="33174-549">Maximum size</span></span> | <span data-ttu-id="33174-550">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="33174-550">Required</span></span> | <span data-ttu-id="33174-551">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="33174-551">Description</span></span>|
|---|---|---|---|---|
|`team`|<span data-ttu-id="33174-552">string</span><span class="sxs-lookup"><span data-stu-id="33174-552">string</span></span>|||<span data-ttu-id="33174-553">Wenn der ausgewählte Installationsbereich ausgewählt `team` ist, gibt dieses Feld die verfügbare Standardfunktion an.</span><span class="sxs-lookup"><span data-stu-id="33174-553">When the install scope selected is `team`, this field specifies the default capability available.</span></span> <span data-ttu-id="33174-554">Optionen: `tab` `bot` oder `connector` .</span><span class="sxs-lookup"><span data-stu-id="33174-554">Options: `tab`, `bot`, or `connector`.</span></span>|
|`groupchat`|<span data-ttu-id="33174-555">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="33174-555">string</span></span>|||<span data-ttu-id="33174-556">Wenn der ausgewählte Installationsbereich ausgewählt `groupchat` ist, gibt dieses Feld die verfügbare Standardfunktion an.</span><span class="sxs-lookup"><span data-stu-id="33174-556">When the install scope selected is `groupchat`, this field specifies the default capability available.</span></span> <span data-ttu-id="33174-557">Optionen: `tab` `bot` oder `connector` .</span><span class="sxs-lookup"><span data-stu-id="33174-557">Options: `tab`, `bot`, or `connector`.</span></span>|
|`meetings`|<span data-ttu-id="33174-558">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="33174-558">string</span></span>|||<span data-ttu-id="33174-559">Wenn der ausgewählte Installationsbereich ausgewählt `meetings` ist, gibt dieses Feld die verfügbare Standardfunktion an.</span><span class="sxs-lookup"><span data-stu-id="33174-559">When the install scope selected is `meetings`, this field specifies the default capability available.</span></span> <span data-ttu-id="33174-560">Optionen: `tab` `bot` oder `connector` .</span><span class="sxs-lookup"><span data-stu-id="33174-560">Options: `tab`, `bot`, or `connector`.</span></span>|
