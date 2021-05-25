---
title: Developer Preview Manifestschemareferenz
description: Beschreibt das schema, das vom Manifest für die Microsoft Teams
ms.topic: reference
keywords: teams manifest schema Developer Preview
localization_priority: Normal
ms.date: 05/20/2019
ms.openlocfilehash: 333ed556ba8ba59c66f66d7eaa41dd0ea66dca0a
ms.sourcegitcommit: e1fe46c574cec378319814f8213209ad3063b2c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/24/2021
ms.locfileid: "52629865"
---
# <a name="developer-preview-manifest-schema-for-microsoft-teams"></a><span data-ttu-id="b610c-104">Entwicklervorschaumanifestschema für Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="b610c-104">Developer preview manifest schema for Microsoft Teams</span></span>

> [!NOTE]
> <span data-ttu-id="b610c-105">Weitere [Developer Preview](~/resources/dev-preview/developer-preview-intro.md) zum Programm und zur Teilnahme finden Sie unter Developer Preview.</span><span class="sxs-lookup"><span data-stu-id="b610c-105">See [Developer Preview](~/resources/dev-preview/developer-preview-intro.md) for information on the program and how you can join.</span></span>
> <span data-ttu-id="b610c-106">Wenn Sie die Entwicklervorschau nicht verwenden, sollten Sie diese Version des Manifests nicht verwenden.</span><span class="sxs-lookup"><span data-stu-id="b610c-106">If you are not using the developer preview you should not be using this version of the manifest.</span></span> <span data-ttu-id="b610c-107">Informationen [zur öffentlichen Version des Manifests finden Microsoft Teams Referenz:](~/resources/schema/manifest-schema.md) Manifestschema.</span><span class="sxs-lookup"><span data-stu-id="b610c-107">See [Reference: Manifest schema for Microsoft Teams](~/resources/schema/manifest-schema.md) for the public version of the manifest.</span></span>

<span data-ttu-id="b610c-108">Das Microsoft Teams-Manifest beschreibt, wie die App in das Microsoft Teams integriert wird.</span><span class="sxs-lookup"><span data-stu-id="b610c-108">The Microsoft Teams manifest describes how the app integrates into the Microsoft Teams product.</span></span> <span data-ttu-id="b610c-109">Ihr Manifest muss dem schema entsprechen, das unter gehostet [`https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json`](https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json) wird.</span><span class="sxs-lookup"><span data-stu-id="b610c-109">Your manifest must conform to the schema hosted at [`https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json`](https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json).</span></span>

<span data-ttu-id="b610c-110">Weitere Informationen zu den verfügbaren Features finden Sie unter Features [in the Public Developer Preview for Microsoft Teams](~/resources/dev-preview/developer-preview-features.md).</span><span class="sxs-lookup"><span data-stu-id="b610c-110">For more information on the features available see: [Features in the Public Developer Preview for Microsoft Teams](~/resources/dev-preview/developer-preview-features.md).</span></span>

## <a name="sample-full-manifest"></a><span data-ttu-id="b610c-111">Beispiel für vollständiges Manifest</span><span class="sxs-lookup"><span data-stu-id="b610c-111">Sample full manifest</span></span>

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

<span data-ttu-id="b610c-112">Das Schema definiert die folgenden Eigenschaften:</span><span class="sxs-lookup"><span data-stu-id="b610c-112">The schema defines the following properties:</span></span>

## <a name="schema"></a><span data-ttu-id="b610c-113">$schema</span><span class="sxs-lookup"><span data-stu-id="b610c-113">$schema</span></span>

<span data-ttu-id="b610c-114">*Optional, aber empfohlen* &ndash; Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="b610c-114">*Optional, but recommended* &ndash; String</span></span>

<span data-ttu-id="b610c-115">Die https://-URL, die auf das JSON-Schema für das Manifest verweist.</span><span class="sxs-lookup"><span data-stu-id="b610c-115">The https:// URL referencing the JSON Schema for the manifest.</span></span>

## <a name="manifestversion"></a><span data-ttu-id="b610c-116">manifestVersion</span><span class="sxs-lookup"><span data-stu-id="b610c-116">manifestVersion</span></span>

<span data-ttu-id="b610c-117">**Erforderlich** &ndash; Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="b610c-117">**Required** &ndash; String</span></span>

<span data-ttu-id="b610c-118">Die Version des Manifestschemas, das dieses Manifest verwendet.</span><span class="sxs-lookup"><span data-stu-id="b610c-118">The version of the manifest schema this manifest is using.</span></span> <span data-ttu-id="b610c-119">Es sollte "devPreview" sein.</span><span class="sxs-lookup"><span data-stu-id="b610c-119">It should be "devPreview".</span></span>

## <a name="version"></a><span data-ttu-id="b610c-120">Version</span><span class="sxs-lookup"><span data-stu-id="b610c-120">version</span></span>

<span data-ttu-id="b610c-121">**Erforderlich** &ndash; Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="b610c-121">**Required** &ndash; String</span></span>

<span data-ttu-id="b610c-122">Die Version der spezifischen App.</span><span class="sxs-lookup"><span data-stu-id="b610c-122">The version of the specific app.</span></span> <span data-ttu-id="b610c-123">Wenn Sie etwas in Ihrem Manifest aktualisieren, muss auch die Version erhöht werden.</span><span class="sxs-lookup"><span data-stu-id="b610c-123">If you update something in your manifest, the version must be incremented as well.</span></span> <span data-ttu-id="b610c-124">Auf diese Weise wird bei der Installation des neuen Manifests das vorhandene überschrieben, und der Benutzer erhält die neue Funktionalität.</span><span class="sxs-lookup"><span data-stu-id="b610c-124">This way, when the new manifest is installed, it will overwrite the existing one and the user will get the new functionality.</span></span> <span data-ttu-id="b610c-125">Wenn diese App an den Store übermittelt wurde, muss das neue Manifest erneut übermittelt und erneut überprüft werden.</span><span class="sxs-lookup"><span data-stu-id="b610c-125">If this app was submitted to the store, the new manifest will have to be re-submitted and re-validated.</span></span> <span data-ttu-id="b610c-126">Anschließend erhalten Benutzer dieser App das neue aktualisierte Manifest automatisch in ein paar Stunden, nachdem es genehmigt wurde.</span><span class="sxs-lookup"><span data-stu-id="b610c-126">Then, users of this app will get the new updated manifest automatically in a few hours, after it is approved.</span></span>

<span data-ttu-id="b610c-127">Wenn sich die Von der App angeforderten Berechtigungen ändern, werden Die Benutzer aufgefordert, ein Upgrade zu starten und der App erneut zu zustimmen.</span><span class="sxs-lookup"><span data-stu-id="b610c-127">If the app requested permissions change, users will be prompted to upgrade and re-consent to the app.</span></span>

<span data-ttu-id="b610c-128">Diese Versionszeichenfolge muss dem [semver-Standard](http://semver.org/) (MAJOR. MINOR. PATCH).</span><span class="sxs-lookup"><span data-stu-id="b610c-128">This version string must follow the [semver](http://semver.org/) standard (MAJOR.MINOR.PATCH).</span></span>

## <a name="id"></a><span data-ttu-id="b610c-129">id</span><span class="sxs-lookup"><span data-stu-id="b610c-129">id</span></span>

<span data-ttu-id="b610c-130">**Erforderlich** &ndash; Microsoft-App-ID</span><span class="sxs-lookup"><span data-stu-id="b610c-130">**Required** &ndash; Microsoft app ID</span></span>

<span data-ttu-id="b610c-131">Der eindeutige von Microsoft generierte Bezeichner für diese App.</span><span class="sxs-lookup"><span data-stu-id="b610c-131">The unique Microsoft-generated identifier for this app.</span></span> <span data-ttu-id="b610c-132">Wenn Sie einen Bot über das Microsoft Bot Framework registriert haben oder sich die Web-App Ihrer Registerkarte bereits bei Microsoft angemeldet hat, sollten Sie bereits über eine ID verfügen und ihn hier eingeben.</span><span class="sxs-lookup"><span data-stu-id="b610c-132">If you have registered a bot via the Microsoft Bot Framework, or your tab's web app already signs in with Microsoft, you should already have an ID and should enter it here.</span></span> <span data-ttu-id="b610c-133">Andernfalls sollten Sie eine neue ID im Microsoft Application Registration Portal ([Meine](https://apps.dev.microsoft.com)Anwendungen ) generieren, sie hier eingeben und dann wiederverwenden, wenn Sie [einen Bot hinzufügen.](~/bots/how-to/create-a-bot-for-teams.md)</span><span class="sxs-lookup"><span data-stu-id="b610c-133">Otherwise, you should generate a new ID at the Microsoft Application Registration Portal ([My Applications](https://apps.dev.microsoft.com)), enter it here, and then reuse it when you [add a bot](~/bots/how-to/create-a-bot-for-teams.md).</span></span>

## <a name="packagename"></a><span data-ttu-id="b610c-134">packageName</span><span class="sxs-lookup"><span data-stu-id="b610c-134">packageName</span></span>

<span data-ttu-id="b610c-135">**Erforderlich** &ndash; Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="b610c-135">**Required** &ndash; String</span></span>

<span data-ttu-id="b610c-136">Ein eindeutiger Bezeichner für diese App in umgekehrter Domänen-Notation; z. B. com.example.myapp.</span><span class="sxs-lookup"><span data-stu-id="b610c-136">A unique identifier for this app in reverse domain notation; for example, com.example.myapp.</span></span>

## <a name="developer"></a><span data-ttu-id="b610c-137">developer</span><span class="sxs-lookup"><span data-stu-id="b610c-137">developer</span></span>

<span data-ttu-id="b610c-138">**Required**</span><span class="sxs-lookup"><span data-stu-id="b610c-138">**Required**</span></span>

<span data-ttu-id="b610c-139">Gibt Informationen zu Ihrem Unternehmen an.</span><span class="sxs-lookup"><span data-stu-id="b610c-139">Specifies information about your company.</span></span> <span data-ttu-id="b610c-140">Für apps submitted to AppSource (formerly Office Store), these values must match the information in your AppSource entry.</span><span class="sxs-lookup"><span data-stu-id="b610c-140">For apps submitted to AppSource (formerly Office Store), these values must match the information in your AppSource entry.</span></span>

|<span data-ttu-id="b610c-141">Name</span><span class="sxs-lookup"><span data-stu-id="b610c-141">Name</span></span>| <span data-ttu-id="b610c-142">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="b610c-142">Maximum size</span></span> | <span data-ttu-id="b610c-143">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="b610c-143">Required</span></span> | <span data-ttu-id="b610c-144">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b610c-144">Description</span></span>|
|---|---|---|---|
|`name`|<span data-ttu-id="b610c-145">32 Zeichen</span><span class="sxs-lookup"><span data-stu-id="b610c-145">32 characters</span></span>|<span data-ttu-id="b610c-146">✔</span><span class="sxs-lookup"><span data-stu-id="b610c-146">✔</span></span>|<span data-ttu-id="b610c-147">Der Anzeigename für den Entwickler.</span><span class="sxs-lookup"><span data-stu-id="b610c-147">The display name for the developer.</span></span>|
|`websiteUrl`|<span data-ttu-id="b610c-148">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="b610c-148">2048 characters</span></span>|<span data-ttu-id="b610c-149">✔</span><span class="sxs-lookup"><span data-stu-id="b610c-149">✔</span></span>|<span data-ttu-id="b610c-150">Die https://-URL zur Website des Entwicklers.</span><span class="sxs-lookup"><span data-stu-id="b610c-150">The https:// URL to the developer's website.</span></span> <span data-ttu-id="b610c-151">Dieser Link sollte Benutzer zu Ihrer unternehmens- oder produktspezifischen Angebotsseite gelangen.</span><span class="sxs-lookup"><span data-stu-id="b610c-151">This link should take users to your company or product-specific landing page.</span></span>|
|`privacyUrl`|<span data-ttu-id="b610c-152">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="b610c-152">2048 characters</span></span>|<span data-ttu-id="b610c-153">✔</span><span class="sxs-lookup"><span data-stu-id="b610c-153">✔</span></span>|<span data-ttu-id="b610c-154">Die https:// url to the developer's privacy policy.</span><span class="sxs-lookup"><span data-stu-id="b610c-154">The https:// URL to the developer's privacy policy.</span></span>|
|`termsOfUseUrl`|<span data-ttu-id="b610c-155">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="b610c-155">2048 characters</span></span>|<span data-ttu-id="b610c-156">✔</span><span class="sxs-lookup"><span data-stu-id="b610c-156">✔</span></span>|<span data-ttu-id="b610c-157">Die https:// URL zu den Nutzungsbedingungen des Entwicklers.</span><span class="sxs-lookup"><span data-stu-id="b610c-157">The https:// URL to the developer's terms of use.</span></span>|
|`mpnId`|<span data-ttu-id="b610c-158">10 Zeichen</span><span class="sxs-lookup"><span data-stu-id="b610c-158">10 characters</span></span>|<span data-ttu-id="b610c-159">✔</span><span class="sxs-lookup"><span data-stu-id="b610c-159">✔</span></span>|<span data-ttu-id="b610c-160">**Optional** Die Microsoft Partner Network ID, die die Partnerorganisation identifiziert, die die App erstellt.</span><span class="sxs-lookup"><span data-stu-id="b610c-160">**Optional** The Microsoft Partner Network ID that identifies the partner organization building the app.</span></span>|

## <a name="localizationinfo"></a><span data-ttu-id="b610c-161">localizationInfo</span><span class="sxs-lookup"><span data-stu-id="b610c-161">localizationInfo</span></span>

<span data-ttu-id="b610c-162">**Optional**</span><span class="sxs-lookup"><span data-stu-id="b610c-162">**Optional**</span></span>

<span data-ttu-id="b610c-163">Ermöglicht die Angabe einer Standardsprache sowie Zeiger auf zusätzliche Sprachdateien.</span><span class="sxs-lookup"><span data-stu-id="b610c-163">Allows the specification of a default language, as well as pointers to additional language files.</span></span> <span data-ttu-id="b610c-164">Weitere [Informationen finden Sie unter Lokalisierung](~/concepts/build-and-test/apps-localization.md).</span><span class="sxs-lookup"><span data-stu-id="b610c-164">See [localization](~/concepts/build-and-test/apps-localization.md).</span></span>

|<span data-ttu-id="b610c-165">Name</span><span class="sxs-lookup"><span data-stu-id="b610c-165">Name</span></span>| <span data-ttu-id="b610c-166">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="b610c-166">Maximum size</span></span> | <span data-ttu-id="b610c-167">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="b610c-167">Required</span></span> | <span data-ttu-id="b610c-168">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b610c-168">Description</span></span>|
|---|---|---|---|
|`defaultLanguageTag`|<span data-ttu-id="b610c-169">4 Zeichen</span><span class="sxs-lookup"><span data-stu-id="b610c-169">4 characters</span></span>|<span data-ttu-id="b610c-170">✔</span><span class="sxs-lookup"><span data-stu-id="b610c-170">✔</span></span>|<span data-ttu-id="b610c-171">Das Sprachtag der Zeichenfolgen in dieser Manifestdatei auf oberster Ebene.</span><span class="sxs-lookup"><span data-stu-id="b610c-171">The language tag of the strings in this top level manifest file.</span></span>|

### <a name="localizationinfoadditionallanguages"></a><span data-ttu-id="b610c-172">localizationInfo.additionalLanguages</span><span class="sxs-lookup"><span data-stu-id="b610c-172">localizationInfo.additionalLanguages</span></span>

<span data-ttu-id="b610c-173">Ein Array von Objekten, die zusätzliche Sprachübersetzungen angeben.</span><span class="sxs-lookup"><span data-stu-id="b610c-173">An array of objects specifying additional language translations.</span></span>

|<span data-ttu-id="b610c-174">Name</span><span class="sxs-lookup"><span data-stu-id="b610c-174">Name</span></span>| <span data-ttu-id="b610c-175">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="b610c-175">Maximum size</span></span> | <span data-ttu-id="b610c-176">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="b610c-176">Required</span></span> | <span data-ttu-id="b610c-177">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b610c-177">Description</span></span>|
|---|---|---|---|
|`languageTag`|<span data-ttu-id="b610c-178">4 Zeichen</span><span class="sxs-lookup"><span data-stu-id="b610c-178">4 characters</span></span>|<span data-ttu-id="b610c-179">✔</span><span class="sxs-lookup"><span data-stu-id="b610c-179">✔</span></span>|<span data-ttu-id="b610c-180">Das Sprachtag der Zeichenfolgen in der bereitgestellten Datei.</span><span class="sxs-lookup"><span data-stu-id="b610c-180">The language tag of the strings in the provided file.</span></span>|
|`file`|<span data-ttu-id="b610c-181">4 Zeichen</span><span class="sxs-lookup"><span data-stu-id="b610c-181">4 characters</span></span>|<span data-ttu-id="b610c-182">✔</span><span class="sxs-lookup"><span data-stu-id="b610c-182">✔</span></span>|<span data-ttu-id="b610c-183">Ein relativer Dateipfad zu einer .json-Datei, die die übersetzten Zeichenfolgen enthält.</span><span class="sxs-lookup"><span data-stu-id="b610c-183">A relative file path to a the .json file containing the translated strings.</span></span>|

## <a name="name"></a><span data-ttu-id="b610c-184">name</span><span class="sxs-lookup"><span data-stu-id="b610c-184">name</span></span>

<span data-ttu-id="b610c-185">**Required**</span><span class="sxs-lookup"><span data-stu-id="b610c-185">**Required**</span></span>

<span data-ttu-id="b610c-186">Der Name Ihrer App-Erfahrung, der Benutzern in der Teams angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="b610c-186">The name of your app experience, displayed to users in the Teams experience.</span></span> <span data-ttu-id="b610c-187">Für apps submitted to AppSource, these values must match the information in your AppSource entry.</span><span class="sxs-lookup"><span data-stu-id="b610c-187">For apps submitted to AppSource, these values must match the information in your AppSource entry.</span></span> <span data-ttu-id="b610c-188">Die Werte von `short` und sollten nicht identisch `full` sein.</span><span class="sxs-lookup"><span data-stu-id="b610c-188">The values of `short` and `full` should not be the same.</span></span>

|<span data-ttu-id="b610c-189">Name</span><span class="sxs-lookup"><span data-stu-id="b610c-189">Name</span></span>| <span data-ttu-id="b610c-190">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="b610c-190">Maximum size</span></span> | <span data-ttu-id="b610c-191">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="b610c-191">Required</span></span> | <span data-ttu-id="b610c-192">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b610c-192">Description</span></span>|
|---|---|---|---|
|`short`|<span data-ttu-id="b610c-193">30 Zeichen</span><span class="sxs-lookup"><span data-stu-id="b610c-193">30 characters</span></span>|<span data-ttu-id="b610c-194">✔</span><span class="sxs-lookup"><span data-stu-id="b610c-194">✔</span></span>|<span data-ttu-id="b610c-195">Der kurze Anzeigename für die App.</span><span class="sxs-lookup"><span data-stu-id="b610c-195">The short display name for the app.</span></span>|
|`full`|<span data-ttu-id="b610c-196">100 Zeichen</span><span class="sxs-lookup"><span data-stu-id="b610c-196">100 characters</span></span>||<span data-ttu-id="b610c-197">Der vollständige Name der App, der verwendet wird, wenn der vollständige Name der App 30 Zeichen überschreitet.</span><span class="sxs-lookup"><span data-stu-id="b610c-197">The full name of the app, used if the full app name exceeds 30 characters.</span></span>|

## <a name="description"></a><span data-ttu-id="b610c-198">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b610c-198">description</span></span>

<span data-ttu-id="b610c-199">**Required**</span><span class="sxs-lookup"><span data-stu-id="b610c-199">**Required**</span></span>

<span data-ttu-id="b610c-200">Beschreibt Ihre App für Benutzer.</span><span class="sxs-lookup"><span data-stu-id="b610c-200">Describes your app to users.</span></span> <span data-ttu-id="b610c-201">Für apps submitted to AppSource, these values must match the information in your AppSource entry.</span><span class="sxs-lookup"><span data-stu-id="b610c-201">For apps submitted to AppSource, these values must match the information in your AppSource entry.</span></span>

<span data-ttu-id="b610c-202">Stellen Sie sicher, dass Ihre Beschreibung Ihre Erfahrung genau beschreibt und Informationen enthält, mit deren Hilfe potenzielle Kunden besser verstehen können, was Ihre Erfahrung bedeutet.</span><span class="sxs-lookup"><span data-stu-id="b610c-202">Ensure that your description accurately describes your experience and provides information to help potential customers understand what your experience does.</span></span> <span data-ttu-id="b610c-203">Beachten Sie auch in der vollständigen Beschreibung, ob ein externes Konto für die Verwendung erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="b610c-203">You should also note, in the full description, if an external account is required for use.</span></span> <span data-ttu-id="b610c-204">Die Werte von `short` und sollten nicht identisch `full` sein.</span><span class="sxs-lookup"><span data-stu-id="b610c-204">The values of `short` and `full` should not be the same.</span></span>  <span data-ttu-id="b610c-205">Ihre kurze Beschreibung darf nicht innerhalb der langen Beschreibung wiederholt werden und darf keinen anderen App-Namen enthalten.</span><span class="sxs-lookup"><span data-stu-id="b610c-205">Your short description must not be repeated within the long description and must not include any other app name.</span></span>

|<span data-ttu-id="b610c-206">Name</span><span class="sxs-lookup"><span data-stu-id="b610c-206">Name</span></span>| <span data-ttu-id="b610c-207">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="b610c-207">Maximum size</span></span> | <span data-ttu-id="b610c-208">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="b610c-208">Required</span></span> | <span data-ttu-id="b610c-209">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b610c-209">Description</span></span>|
|---|---|---|---|
|`short`|<span data-ttu-id="b610c-210">80 Zeichen</span><span class="sxs-lookup"><span data-stu-id="b610c-210">80 characters</span></span>|<span data-ttu-id="b610c-211">✔</span><span class="sxs-lookup"><span data-stu-id="b610c-211">✔</span></span>|<span data-ttu-id="b610c-212">Eine kurze Beschreibung Ihrer App-Erfahrung, die bei begrenztem Speicherplatz verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="b610c-212">A short description of your app experience, used when space is limited.</span></span>|
|`full`|<span data-ttu-id="b610c-213">4000 Zeichen</span><span class="sxs-lookup"><span data-stu-id="b610c-213">4000 characters</span></span>|<span data-ttu-id="b610c-214">✔</span><span class="sxs-lookup"><span data-stu-id="b610c-214">✔</span></span>|<span data-ttu-id="b610c-215">Die vollständige Beschreibung Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="b610c-215">The full description of your app.</span></span>|

## <a name="icons"></a><span data-ttu-id="b610c-216">Symbole</span><span class="sxs-lookup"><span data-stu-id="b610c-216">icons</span></span>

<span data-ttu-id="b610c-217">**Required**</span><span class="sxs-lookup"><span data-stu-id="b610c-217">**Required**</span></span>

<span data-ttu-id="b610c-218">Symbole, die innerhalb der Teams werden.</span><span class="sxs-lookup"><span data-stu-id="b610c-218">Icons used within the Teams app.</span></span> <span data-ttu-id="b610c-219">Die Symboldateien müssen als Teil des Uploadpakets enthalten sein.</span><span class="sxs-lookup"><span data-stu-id="b610c-219">The icon files must be included as part of the upload package.</span></span>

|<span data-ttu-id="b610c-220">Name</span><span class="sxs-lookup"><span data-stu-id="b610c-220">Name</span></span>| <span data-ttu-id="b610c-221">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="b610c-221">Maximum size</span></span> | <span data-ttu-id="b610c-222">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="b610c-222">Required</span></span> | <span data-ttu-id="b610c-223">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b610c-223">Description</span></span>|
|---|---|---|---|
|`outline`|<span data-ttu-id="b610c-224">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="b610c-224">2048 characters</span></span>|<span data-ttu-id="b610c-225">✔</span><span class="sxs-lookup"><span data-stu-id="b610c-225">✔</span></span>|<span data-ttu-id="b610c-226">Ein relativer Dateipfad zu einem transparenten 32 x 32 PNG-Gliederungssymbol.</span><span class="sxs-lookup"><span data-stu-id="b610c-226">A relative file path to a transparent 32x32 PNG outline icon.</span></span>|
|`color`|<span data-ttu-id="b610c-227">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="b610c-227">2048 characters</span></span>|<span data-ttu-id="b610c-228">✔</span><span class="sxs-lookup"><span data-stu-id="b610c-228">✔</span></span>|<span data-ttu-id="b610c-229">Ein relativer Dateipfad zu einem vollfarbigen 192 x 192-PNG-Symbol.</span><span class="sxs-lookup"><span data-stu-id="b610c-229">A relative file path to a full color 192x192 PNG icon.</span></span>|

## <a name="accentcolor"></a><span data-ttu-id="b610c-230">accentColor</span><span class="sxs-lookup"><span data-stu-id="b610c-230">accentColor</span></span>

<span data-ttu-id="b610c-231">**Erforderlich** &ndash; Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="b610c-231">**Required** &ndash; String</span></span>

<span data-ttu-id="b610c-232">Eine Farbe, die in Verbindung mit und als Hintergrund für Ihre Gliederungssymbole verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="b610c-232">A color to use in conjunction with and as a background for your outline icons.</span></span>

<span data-ttu-id="b610c-233">Der Wert muss ein gültiger #A0 sein, der mit "#" beginnt, z. B. `#4464ee` .</span><span class="sxs-lookup"><span data-stu-id="b610c-233">The value must be a valid HTML color code starting with '#', for example `#4464ee`.</span></span>

## <a name="configurabletabs"></a><span data-ttu-id="b610c-234">configurableTabs</span><span class="sxs-lookup"><span data-stu-id="b610c-234">configurableTabs</span></span>

<span data-ttu-id="b610c-235">**Optional**</span><span class="sxs-lookup"><span data-stu-id="b610c-235">**Optional**</span></span>

<span data-ttu-id="b610c-236">Wird verwendet, wenn Ihre App über eine Registerkartenerfahrung im Teamkanal verfügt, die eine zusätzliche Konfiguration erfordert, bevor sie hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="b610c-236">Used when your app experience has a team channel tab experience that requires extra configuration before it is added.</span></span> <span data-ttu-id="b610c-237">Konfigurierbare Registerkarten werden nur im Bereich Teams unterstützt, und derzeit wird nur eine Registerkarte pro App unterstützt.</span><span class="sxs-lookup"><span data-stu-id="b610c-237">Configurable tabs are supported only in the teams scope, and currently only one tab per app is supported.</span></span>

<span data-ttu-id="b610c-238">Das Objekt ist ein Array mit allen Elementen des Typs `object` .</span><span class="sxs-lookup"><span data-stu-id="b610c-238">The object is an array with all elements of the type `object`.</span></span> <span data-ttu-id="b610c-239">Dieser Block ist nur für Lösungen erforderlich, die eine konfigurierbare Kanalregisterkartenlösung bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="b610c-239">This block is required only for solutions that provide a configurable channel tab solution.</span></span>

|<span data-ttu-id="b610c-240">Name</span><span class="sxs-lookup"><span data-stu-id="b610c-240">Name</span></span>| <span data-ttu-id="b610c-241">Typ</span><span class="sxs-lookup"><span data-stu-id="b610c-241">Type</span></span>| <span data-ttu-id="b610c-242">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="b610c-242">Maximum size</span></span> | <span data-ttu-id="b610c-243">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="b610c-243">Required</span></span> | <span data-ttu-id="b610c-244">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b610c-244">Description</span></span>|
|---|---|---|---|---|
|`configurationUrl`|<span data-ttu-id="b610c-245">String</span><span class="sxs-lookup"><span data-stu-id="b610c-245">String</span></span>|<span data-ttu-id="b610c-246">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="b610c-246">2048 characters</span></span>|<span data-ttu-id="b610c-247">✔</span><span class="sxs-lookup"><span data-stu-id="b610c-247">✔</span></span>|<span data-ttu-id="b610c-248">Die https:// URL, die beim Konfigurieren der Registerkarte verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="b610c-248">The https:// URL to use when configuring the tab.</span></span>|
|`canUpdateConfiguration`|<span data-ttu-id="b610c-249">Boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="b610c-249">Boolean</span></span>|||<span data-ttu-id="b610c-250">Ein Wert, der angibt, ob eine Instanz der Registerkartenkonfiguration vom Benutzer nach der Erstellung aktualisiert werden kann.</span><span class="sxs-lookup"><span data-stu-id="b610c-250">A value indicating whether an instance of the tab's configuration can be updated by the user after creation.</span></span> <span data-ttu-id="b610c-251">Standard: `true`</span><span class="sxs-lookup"><span data-stu-id="b610c-251">Default: `true`</span></span>|
|`scopes`|<span data-ttu-id="b610c-252">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="b610c-252">Array of enum</span></span>|<span data-ttu-id="b610c-253">1</span><span class="sxs-lookup"><span data-stu-id="b610c-253">1</span></span>|<span data-ttu-id="b610c-254">✔</span><span class="sxs-lookup"><span data-stu-id="b610c-254">✔</span></span>|<span data-ttu-id="b610c-255">Derzeit unterstützen konfigurierbare Registerkarten nur die `team` Bereiche `groupchat` und.</span><span class="sxs-lookup"><span data-stu-id="b610c-255">Currently, configurable tabs support only the `team` and `groupchat` scopes.</span></span> |
|`sharePointPreviewImage`|<span data-ttu-id="b610c-256">String</span><span class="sxs-lookup"><span data-stu-id="b610c-256">String</span></span>|<span data-ttu-id="b610c-257">2048</span><span class="sxs-lookup"><span data-stu-id="b610c-257">2048</span></span>||<span data-ttu-id="b610c-258">Ein relativer Dateipfad zu einem Registerkartenvorschaubild zur Verwendung in SharePoint.</span><span class="sxs-lookup"><span data-stu-id="b610c-258">A relative file path to a tab preview image for use in SharePoint.</span></span> <span data-ttu-id="b610c-259">Größe 1024 x 768.</span><span class="sxs-lookup"><span data-stu-id="b610c-259">Size 1024x768.</span></span> |
|`supportedSharePointHosts`|<span data-ttu-id="b610c-260">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="b610c-260">Array of enum</span></span>|<span data-ttu-id="b610c-261">1</span><span class="sxs-lookup"><span data-stu-id="b610c-261">1</span></span>||<span data-ttu-id="b610c-262">Definiert, wie Ihre Registerkarte in der SharePoint.</span><span class="sxs-lookup"><span data-stu-id="b610c-262">Defines how your tab will be made available in SharePoint.</span></span> <span data-ttu-id="b610c-263">Optionen sind `sharePointFullPage` und `sharePointWebPart`</span><span class="sxs-lookup"><span data-stu-id="b610c-263">Options are `sharePointFullPage` and `sharePointWebPart`</span></span> |

## <a name="statictabs"></a><span data-ttu-id="b610c-264">staticTabs</span><span class="sxs-lookup"><span data-stu-id="b610c-264">staticTabs</span></span>

<span data-ttu-id="b610c-265">**Optional**</span><span class="sxs-lookup"><span data-stu-id="b610c-265">**Optional**</span></span>

<span data-ttu-id="b610c-266">Definiert eine Reihe von Registerkarten, die standardmäßig angeheftet werden können, ohne dass der Benutzer sie manuell hinzufügungen muss.</span><span class="sxs-lookup"><span data-stu-id="b610c-266">Defines a set of tabs that can be "pinned" by default, without the user adding them manually.</span></span> <span data-ttu-id="b610c-267">Statische Registerkarten, die im Bereich deklariert sind, werden immer an die persönliche Be benutzererfahrung `personal` der App angeheftet.</span><span class="sxs-lookup"><span data-stu-id="b610c-267">Static tabs declared in `personal` scope are always pinned to the app's personal experience.</span></span> <span data-ttu-id="b610c-268">Statische Registerkarten, die im Bereich `team` deklariert sind, werden derzeit nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="b610c-268">Static tabs declared in the `team` scope are currently not supported.</span></span>

<span data-ttu-id="b610c-269">Das Objekt ist ein Array (maximal 16 Elemente) mit allen Elementen des Typs `object` .</span><span class="sxs-lookup"><span data-stu-id="b610c-269">The object is an array (maximum of 16 elements) with all elements of the type `object`.</span></span> <span data-ttu-id="b610c-270">Dieser Block ist nur für Lösungen erforderlich, die eine statische Registerkartenlösung bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="b610c-270">This block is required only for solutions that provide a static tab solution.</span></span>

|<span data-ttu-id="b610c-271">Name</span><span class="sxs-lookup"><span data-stu-id="b610c-271">Name</span></span>| <span data-ttu-id="b610c-272">Typ</span><span class="sxs-lookup"><span data-stu-id="b610c-272">Type</span></span>| <span data-ttu-id="b610c-273">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="b610c-273">Maximum size</span></span> | <span data-ttu-id="b610c-274">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="b610c-274">Required</span></span> | <span data-ttu-id="b610c-275">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b610c-275">Description</span></span>|
|---|---|---|---|---|
|`entityId`|<span data-ttu-id="b610c-276">String</span><span class="sxs-lookup"><span data-stu-id="b610c-276">String</span></span>|<span data-ttu-id="b610c-277">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="b610c-277">64 characters</span></span>|<span data-ttu-id="b610c-278">✔</span><span class="sxs-lookup"><span data-stu-id="b610c-278">✔</span></span>|<span data-ttu-id="b610c-279">Ein eindeutiger Bezeichner für die Entität, die auf der Registerkarte angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="b610c-279">A unique identifier for the entity that the tab displays.</span></span>|
|`name`|<span data-ttu-id="b610c-280">String</span><span class="sxs-lookup"><span data-stu-id="b610c-280">String</span></span>|<span data-ttu-id="b610c-281">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="b610c-281">128 characters</span></span>|<span data-ttu-id="b610c-282">✔</span><span class="sxs-lookup"><span data-stu-id="b610c-282">✔</span></span>|<span data-ttu-id="b610c-283">Der Anzeigename der Registerkarte in der Kanalschnittstelle.</span><span class="sxs-lookup"><span data-stu-id="b610c-283">The display name of the tab in the channel interface.</span></span>|
|`contentUrl`|<span data-ttu-id="b610c-284">String</span><span class="sxs-lookup"><span data-stu-id="b610c-284">String</span></span>|<span data-ttu-id="b610c-285">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="b610c-285">2048 characters</span></span>|<span data-ttu-id="b610c-286">✔</span><span class="sxs-lookup"><span data-stu-id="b610c-286">✔</span></span>|<span data-ttu-id="b610c-287">Die https://-URL, die auf die Entitätsbenutzeroberfläche verweist, die im Zeichenbereich Teams werden soll.</span><span class="sxs-lookup"><span data-stu-id="b610c-287">The https:// URL that points to the entity UI to be displayed in the Teams canvas.</span></span>|
|`websiteUrl`|<span data-ttu-id="b610c-288">String</span><span class="sxs-lookup"><span data-stu-id="b610c-288">String</span></span>|<span data-ttu-id="b610c-289">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="b610c-289">2048 characters</span></span>||<span data-ttu-id="b610c-290">Die https:// URL, auf die verweisen soll, wenn sich ein Benutzer für die Anzeige in einem Browser entscheidet.</span><span class="sxs-lookup"><span data-stu-id="b610c-290">The https:// URL to point at if a user opts to view in a browser.</span></span>|
|`scopes`|<span data-ttu-id="b610c-291">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="b610c-291">Array of enum</span></span>|<span data-ttu-id="b610c-292">1</span><span class="sxs-lookup"><span data-stu-id="b610c-292">1</span></span>|<span data-ttu-id="b610c-293">✔</span><span class="sxs-lookup"><span data-stu-id="b610c-293">✔</span></span>|<span data-ttu-id="b610c-294">Derzeit unterstützen statische Registerkarten nur den Bereich, d. h., er kann nur als Teil der `personal` persönlichen Erfahrung bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="b610c-294">Currently, static tabs support only the `personal` scope, which means it can be provisioned only as part of the personal experience.</span></span>|

## <a name="bots"></a><span data-ttu-id="b610c-295">Bots</span><span class="sxs-lookup"><span data-stu-id="b610c-295">bots</span></span>

<span data-ttu-id="b610c-296">**Optional**</span><span class="sxs-lookup"><span data-stu-id="b610c-296">**Optional**</span></span>

<span data-ttu-id="b610c-297">Definiert eine Botlösung zusammen mit optionalen Informationen, z. B. Standardbefehlseigenschaften.</span><span class="sxs-lookup"><span data-stu-id="b610c-297">Defines a bot solution, along with optional information such as default command properties.</span></span>

<span data-ttu-id="b610c-298">Das Objekt ist ein Array (maximal 1 Element ist derzeit nur ein Bot pro App zulässig) mit allen Elementen &mdash; des Typs `object` .</span><span class="sxs-lookup"><span data-stu-id="b610c-298">The object is an array (maximum of only 1 element&mdash;currently only one bot is allowed per app) with all elements of the type `object`.</span></span> <span data-ttu-id="b610c-299">Dieser Block ist nur für Lösungen erforderlich, die eine Boterfahrung bieten.</span><span class="sxs-lookup"><span data-stu-id="b610c-299">This block is required only for solutions that provide a bot experience.</span></span>

|<span data-ttu-id="b610c-300">Name</span><span class="sxs-lookup"><span data-stu-id="b610c-300">Name</span></span>| <span data-ttu-id="b610c-301">Typ</span><span class="sxs-lookup"><span data-stu-id="b610c-301">Type</span></span>| <span data-ttu-id="b610c-302">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="b610c-302">Maximum size</span></span> | <span data-ttu-id="b610c-303">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="b610c-303">Required</span></span> | <span data-ttu-id="b610c-304">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b610c-304">Description</span></span>|
|---|---|---|---|---|
|`botId`|<span data-ttu-id="b610c-305">String</span><span class="sxs-lookup"><span data-stu-id="b610c-305">String</span></span>|<span data-ttu-id="b610c-306">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="b610c-306">64 characters</span></span>|<span data-ttu-id="b610c-307">✔</span><span class="sxs-lookup"><span data-stu-id="b610c-307">✔</span></span>|<span data-ttu-id="b610c-308">Die eindeutige Microsoft-App-ID für den Bot, wie bei Bot Framework registriert.</span><span class="sxs-lookup"><span data-stu-id="b610c-308">The unique Microsoft app ID for the bot as registered with the Bot Framework.</span></span> <span data-ttu-id="b610c-309">Dies kann mit der allgemeinen [App-ID identisch sein.](#id)</span><span class="sxs-lookup"><span data-stu-id="b610c-309">This may well be the same as the overall [app ID](#id).</span></span>|
|`needsChannelSelector`|<span data-ttu-id="b610c-310">Boolesch</span><span class="sxs-lookup"><span data-stu-id="b610c-310">Boolean</span></span>|||<span data-ttu-id="b610c-311">Beschreibt, ob der Bot einen Benutzerhinweis verwendet, um den Bot einem bestimmten Kanal hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="b610c-311">Describes whether or not the bot utilizes a user hint to add the bot to a specific channel.</span></span> <span data-ttu-id="b610c-312">Standard: `false`</span><span class="sxs-lookup"><span data-stu-id="b610c-312">Default: `false`</span></span>|
|`isNotificationOnly`|<span data-ttu-id="b610c-313">Boolesch</span><span class="sxs-lookup"><span data-stu-id="b610c-313">Boolean</span></span>|||<span data-ttu-id="b610c-314">Gibt an, ob ein Bot ein unidirektionaler Bot ausschließlich für Benachrichtigungen ist (im Gegensatz zu einem dialogorientierten Bot).</span><span class="sxs-lookup"><span data-stu-id="b610c-314">Indicates whether a bot is a one-way, notification-only bot, as opposed to a conversational bot.</span></span> <span data-ttu-id="b610c-315">Standard: `false`</span><span class="sxs-lookup"><span data-stu-id="b610c-315">Default: `false`</span></span>|
|`supportsFiles`|<span data-ttu-id="b610c-316">Boolesch</span><span class="sxs-lookup"><span data-stu-id="b610c-316">Boolean</span></span>|||<span data-ttu-id="b610c-317">Gibt an, ob der Bot die Möglichkeit zum Hochladen/Herunterladen von Dateien in persönliche Chats unterstützt.</span><span class="sxs-lookup"><span data-stu-id="b610c-317">Indicates whether the bot supports the ability to upload/download files in personal chat.</span></span> <span data-ttu-id="b610c-318">Standard: `false`</span><span class="sxs-lookup"><span data-stu-id="b610c-318">Default: `false`</span></span>|
|`scopes`|<span data-ttu-id="b610c-319">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="b610c-319">Array of enum</span></span>|<span data-ttu-id="b610c-320">3</span><span class="sxs-lookup"><span data-stu-id="b610c-320">3</span></span>|<span data-ttu-id="b610c-321">✔</span><span class="sxs-lookup"><span data-stu-id="b610c-321">✔</span></span>|<span data-ttu-id="b610c-322">Gibt an, ob der Bot eine Umgebung im Kontext eines Kanals in einem `team` oder Gruppenchat (`groupchat`) ist, oder aber eine Umgebung einzig für einen bestimmten Benutzer (`personal`).</span><span class="sxs-lookup"><span data-stu-id="b610c-322">Specifies whether the bot offers an experience in the context of a channel in a `team`, in a group chat (`groupchat`), or an experience scoped to an individual user alone (`personal`).</span></span> <span data-ttu-id="b610c-323">Diese Optionen sind nicht exklusiv.</span><span class="sxs-lookup"><span data-stu-id="b610c-323">These options are non-exclusive.</span></span>|

### <a name="botscommandlists"></a><span data-ttu-id="b610c-324">bots.commandLists</span><span class="sxs-lookup"><span data-stu-id="b610c-324">bots.commandLists</span></span>

<span data-ttu-id="b610c-325">Eine optionale Liste von Befehlen, die Ihr Bot Benutzern empfehlen kann.</span><span class="sxs-lookup"><span data-stu-id="b610c-325">An optional list of commands that your bot can recommend to users.</span></span> <span data-ttu-id="b610c-326">Das Objekt ist ein Array (maximal 2 Elemente) mit allen Elementen des Typs. Sie müssen eine separate Befehlsliste für jeden Bereich definieren, den `object` Ihr Bot unterstützt.</span><span class="sxs-lookup"><span data-stu-id="b610c-326">The object is an array (maximum of 2 elements) with all elements of type `object`; you must define a separate command list for each scope that your bot supports.</span></span> <span data-ttu-id="b610c-327">Weitere Informationen finden Sie unter [Bot-Menüs](~/bots/how-to/create-a-bot-commands-menu.md).</span><span class="sxs-lookup"><span data-stu-id="b610c-327">For more information, see [Bot menus](~/bots/how-to/create-a-bot-commands-menu.md).</span></span>

|<span data-ttu-id="b610c-328">Name</span><span class="sxs-lookup"><span data-stu-id="b610c-328">Name</span></span>| <span data-ttu-id="b610c-329">Typ</span><span class="sxs-lookup"><span data-stu-id="b610c-329">Type</span></span>| <span data-ttu-id="b610c-330">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="b610c-330">Maximum size</span></span> | <span data-ttu-id="b610c-331">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="b610c-331">Required</span></span> | <span data-ttu-id="b610c-332">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b610c-332">Description</span></span>|
|---|---|---|---|---|
|`items.scopes`|<span data-ttu-id="b610c-333">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="b610c-333">array of enum</span></span>|<span data-ttu-id="b610c-334">3</span><span class="sxs-lookup"><span data-stu-id="b610c-334">3</span></span>|<span data-ttu-id="b610c-335">✔</span><span class="sxs-lookup"><span data-stu-id="b610c-335">✔</span></span>|<span data-ttu-id="b610c-336">Gibt den Bereich an, für den die Befehlsliste gültig ist.</span><span class="sxs-lookup"><span data-stu-id="b610c-336">Specifies the scope for which the command list is valid.</span></span> <span data-ttu-id="b610c-337">Mögliche Optionen sind `team`, `personal` und `groupchat`.</span><span class="sxs-lookup"><span data-stu-id="b610c-337">Options are `team`, `personal`, and `groupchat`.</span></span>|
|`items.commands`|<span data-ttu-id="b610c-338">Array von Objekten</span><span class="sxs-lookup"><span data-stu-id="b610c-338">array of objects</span></span>|<span data-ttu-id="b610c-339">10</span><span class="sxs-lookup"><span data-stu-id="b610c-339">10</span></span>|<span data-ttu-id="b610c-340">✔</span><span class="sxs-lookup"><span data-stu-id="b610c-340">✔</span></span>|<span data-ttu-id="b610c-341">Ein Array von Befehlen, die der Bot unterstützt:</span><span class="sxs-lookup"><span data-stu-id="b610c-341">An array of commands the bot supports:</span></span><br><span data-ttu-id="b610c-342">`title`: der Name des Botbefehls (Zeichenfolge, 32).</span><span class="sxs-lookup"><span data-stu-id="b610c-342">`title`: the bot command name (string, 32).</span></span><br><span data-ttu-id="b610c-343">`description`: eine einfache Beschreibung oder ein Beispiel für die Befehlssyntax und ihr Argument (Zeichenfolge, 128).</span><span class="sxs-lookup"><span data-stu-id="b610c-343">`description`: a simple description or example of the command syntax and its argument (string, 128).</span></span>|

## <a name="connectors"></a><span data-ttu-id="b610c-344">Connectors</span><span class="sxs-lookup"><span data-stu-id="b610c-344">connectors</span></span>

<span data-ttu-id="b610c-345">**Optional**</span><span class="sxs-lookup"><span data-stu-id="b610c-345">**Optional**</span></span>

<span data-ttu-id="b610c-346">Der `connectors` Block definiert einen Office 365 Connector für die App.</span><span class="sxs-lookup"><span data-stu-id="b610c-346">The `connectors` block defines an Office 365 Connector for the app.</span></span>

<span data-ttu-id="b610c-347">Das Objekt ist ein Array (maximal 1 Element) mit allen Elementen vom Typ `object` .</span><span class="sxs-lookup"><span data-stu-id="b610c-347">The object is an array (maximum of 1 element) with all elements of type `object`.</span></span> <span data-ttu-id="b610c-348">Dieser Block ist nur für Lösungen erforderlich, die einen Connector bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="b610c-348">This block is required only for solutions that provide a Connector.</span></span>

|<span data-ttu-id="b610c-349">Name</span><span class="sxs-lookup"><span data-stu-id="b610c-349">Name</span></span>| <span data-ttu-id="b610c-350">Typ</span><span class="sxs-lookup"><span data-stu-id="b610c-350">Type</span></span>| <span data-ttu-id="b610c-351">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="b610c-351">Maximum size</span></span> | <span data-ttu-id="b610c-352">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="b610c-352">Required</span></span> | <span data-ttu-id="b610c-353">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b610c-353">Description</span></span>|
|---|---|---|---|---|
|`configurationUrl`|<span data-ttu-id="b610c-354">String</span><span class="sxs-lookup"><span data-stu-id="b610c-354">String</span></span>|<span data-ttu-id="b610c-355">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="b610c-355">2048 characters</span></span>|<span data-ttu-id="b610c-356">✔</span><span class="sxs-lookup"><span data-stu-id="b610c-356">✔</span></span>|<span data-ttu-id="b610c-357">Die https://-URL, die beim Konfigurieren des Connectors verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="b610c-357">The https:// URL to use when configuring the connector.</span></span>|
|`connectorId`|<span data-ttu-id="b610c-358">String</span><span class="sxs-lookup"><span data-stu-id="b610c-358">String</span></span>|<span data-ttu-id="b610c-359">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="b610c-359">64 characters</span></span>|<span data-ttu-id="b610c-360">✔</span><span class="sxs-lookup"><span data-stu-id="b610c-360">✔</span></span>|<span data-ttu-id="b610c-361">Ein eindeutiger Bezeichner für den Connector, der seiner ID im [Connectors Developer Dashboard entspricht.](https://aka.ms/connectorsdashboard)</span><span class="sxs-lookup"><span data-stu-id="b610c-361">A unique identifier for the Connector that matches its ID in the [Connectors Developer Dashboard](https://aka.ms/connectorsdashboard).</span></span>|
|`scopes`|<span data-ttu-id="b610c-362">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="b610c-362">Array of enum</span></span>|<span data-ttu-id="b610c-363">1</span><span class="sxs-lookup"><span data-stu-id="b610c-363">1</span></span>|<span data-ttu-id="b610c-364">✔</span><span class="sxs-lookup"><span data-stu-id="b610c-364">✔</span></span>|<span data-ttu-id="b610c-365">Gibt an, ob der Connector eine Benutzeroberfläche im Kontext eines Kanals in einem oder eine Benutzeroberfläche bietet, die auf einen einzelnen Benutzer `team` begrenzt ist ( `personal` ).</span><span class="sxs-lookup"><span data-stu-id="b610c-365">Specifies whether the Connector offers an experience in the context of a channel in a `team`, or an experience scoped to an individual user alone (`personal`).</span></span> <span data-ttu-id="b610c-366">Derzeit wird nur `team` der Bereich unterstützt.</span><span class="sxs-lookup"><span data-stu-id="b610c-366">Currently, only the `team` scope is supported.</span></span>|

## <a name="composeextensions"></a><span data-ttu-id="b610c-367">composeExtensions</span><span class="sxs-lookup"><span data-stu-id="b610c-367">composeExtensions</span></span>

<span data-ttu-id="b610c-368">**Optional**</span><span class="sxs-lookup"><span data-stu-id="b610c-368">**Optional**</span></span>

<span data-ttu-id="b610c-369">Definiert eine Messagingerweiterung für die App.</span><span class="sxs-lookup"><span data-stu-id="b610c-369">Defines a messaging extension for the app.</span></span>

> [!NOTE]
> <span data-ttu-id="b610c-370">Der Name des Features wurde im November 2017 von "Verfassenerweiterung" in "Messagingerweiterung" geändert, der Manifestname bleibt jedoch unverändert, damit vorhandene Erweiterungen weiterhin funktionieren.</span><span class="sxs-lookup"><span data-stu-id="b610c-370">The name of the feature was changed from "compose extension" to "messaging extension" in November, 2017, but the manifest name remains the same so that existing extensions continue to function.</span></span>

<span data-ttu-id="b610c-371">Das Objekt ist ein Array (maximal 1 Element) mit allen Elementen vom Typ `object` .</span><span class="sxs-lookup"><span data-stu-id="b610c-371">The object is an array (maximum of 1 element) with all elements of type `object`.</span></span> <span data-ttu-id="b610c-372">Dieser Block ist nur für Lösungen erforderlich, die eine Messagingerweiterung bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="b610c-372">This block is required only for solutions that provide a messaging extension.</span></span>

|<span data-ttu-id="b610c-373">Name</span><span class="sxs-lookup"><span data-stu-id="b610c-373">Name</span></span>| <span data-ttu-id="b610c-374">Typ</span><span class="sxs-lookup"><span data-stu-id="b610c-374">Type</span></span> | <span data-ttu-id="b610c-375">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="b610c-375">Maximum Size</span></span> | <span data-ttu-id="b610c-376">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="b610c-376">Required</span></span> | <span data-ttu-id="b610c-377">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b610c-377">Description</span></span>|
|---|---|---|---|---|
|`botId`|<span data-ttu-id="b610c-378">String</span><span class="sxs-lookup"><span data-stu-id="b610c-378">String</span></span>|<span data-ttu-id="b610c-379">64</span><span class="sxs-lookup"><span data-stu-id="b610c-379">64</span></span>|<span data-ttu-id="b610c-380">✔</span><span class="sxs-lookup"><span data-stu-id="b610c-380">✔</span></span>|<span data-ttu-id="b610c-381">Die eindeutige Microsoft-App-ID für den Bot, der die Messagingerweiterung unterstützt, wie beim Bot Framework registriert.</span><span class="sxs-lookup"><span data-stu-id="b610c-381">The unique Microsoft app ID for the bot that backs the messaging extension, as registered with the Bot Framework.</span></span> <span data-ttu-id="b610c-382">Dies kann mit der allgemeinen [App-ID identisch sein.](#id)</span><span class="sxs-lookup"><span data-stu-id="b610c-382">This may well be the same as the overall [app ID](#id).</span></span>|
|`canUpdateConfiguration`|<span data-ttu-id="b610c-383">Boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="b610c-383">Boolean</span></span>|||<span data-ttu-id="b610c-384">Ein Wert, der angibt, ob die Konfiguration einer Messagingerweiterung vom Benutzer aktualisiert werden kann.</span><span class="sxs-lookup"><span data-stu-id="b610c-384">A value indicating whether the configuration of a messaging extension can be updated by the user.</span></span> <span data-ttu-id="b610c-385">Der Standardwert lautet `false`.</span><span class="sxs-lookup"><span data-stu-id="b610c-385">The default is `false`.</span></span>|
|`commands`|<span data-ttu-id="b610c-386">Array des Objekts</span><span class="sxs-lookup"><span data-stu-id="b610c-386">Array of object</span></span>|<span data-ttu-id="b610c-387">10</span><span class="sxs-lookup"><span data-stu-id="b610c-387">10</span></span>|<span data-ttu-id="b610c-388">✔</span><span class="sxs-lookup"><span data-stu-id="b610c-388">✔</span></span>|<span data-ttu-id="b610c-389">Array von Befehlen, die von der Messagingerweiterung unterstützt werden</span><span class="sxs-lookup"><span data-stu-id="b610c-389">Array of commands the messaging extension supports</span></span>|

### <a name="composeextensionscommands"></a><span data-ttu-id="b610c-390">composeExtensions.commands</span><span class="sxs-lookup"><span data-stu-id="b610c-390">composeExtensions.commands</span></span>

<span data-ttu-id="b610c-391">Ihre Messagingerweiterung sollte einen oder mehrere Befehle deklarieren.</span><span class="sxs-lookup"><span data-stu-id="b610c-391">Your messaging extension should declare one or more commands.</span></span> <span data-ttu-id="b610c-392">Jeder Befehl wird in Microsoft Teams als potenzielle Interaktion vom benutzeroberflächenbasierten Einstiegspunkt angezeigt.</span><span class="sxs-lookup"><span data-stu-id="b610c-392">Each command appears in Microsoft Teams as a potential interaction from the UI-based entry point.</span></span> <span data-ttu-id="b610c-393">Es gibt maximal 10 Befehle.</span><span class="sxs-lookup"><span data-stu-id="b610c-393">There is a maximum of 10 commands.</span></span>

<span data-ttu-id="b610c-394">Jedes Befehlselement ist ein Objekt mit der folgenden Struktur:</span><span class="sxs-lookup"><span data-stu-id="b610c-394">Each command item is an object with the following structure:</span></span>

|<span data-ttu-id="b610c-395">Name</span><span class="sxs-lookup"><span data-stu-id="b610c-395">Name</span></span>| <span data-ttu-id="b610c-396">Typ</span><span class="sxs-lookup"><span data-stu-id="b610c-396">Type</span></span>| <span data-ttu-id="b610c-397">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="b610c-397">Maximum size</span></span> | <span data-ttu-id="b610c-398">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="b610c-398">Required</span></span> | <span data-ttu-id="b610c-399">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b610c-399">Description</span></span>|
|---|---|---|---|---|
|`id`|<span data-ttu-id="b610c-400">String</span><span class="sxs-lookup"><span data-stu-id="b610c-400">String</span></span>|<span data-ttu-id="b610c-401">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="b610c-401">64 characters</span></span>|<span data-ttu-id="b610c-402">✔</span><span class="sxs-lookup"><span data-stu-id="b610c-402">✔</span></span>|<span data-ttu-id="b610c-403">Die ID für den Befehl.</span><span class="sxs-lookup"><span data-stu-id="b610c-403">The ID for the command.</span></span>|
|`type`|<span data-ttu-id="b610c-404">String</span><span class="sxs-lookup"><span data-stu-id="b610c-404">String</span></span>|<span data-ttu-id="b610c-405">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="b610c-405">64 characters</span></span>||<span data-ttu-id="b610c-406">Typ des Befehls.</span><span class="sxs-lookup"><span data-stu-id="b610c-406">Type of the command.</span></span> <span data-ttu-id="b610c-407">Einer oder `query` `action` .</span><span class="sxs-lookup"><span data-stu-id="b610c-407">One of `query` or `action`.</span></span> <span data-ttu-id="b610c-408">Standard: `query`</span><span class="sxs-lookup"><span data-stu-id="b610c-408">Default: `query`</span></span>|
|`title`|<span data-ttu-id="b610c-409">String</span><span class="sxs-lookup"><span data-stu-id="b610c-409">String</span></span>|<span data-ttu-id="b610c-410">32 Zeichen</span><span class="sxs-lookup"><span data-stu-id="b610c-410">32 characters</span></span>|<span data-ttu-id="b610c-411">✔</span><span class="sxs-lookup"><span data-stu-id="b610c-411">✔</span></span>|<span data-ttu-id="b610c-412">Der benutzerfreundliche Befehlsname.</span><span class="sxs-lookup"><span data-stu-id="b610c-412">The user-friendly command name.</span></span>|
|`description`|<span data-ttu-id="b610c-413">String</span><span class="sxs-lookup"><span data-stu-id="b610c-413">String</span></span>|<span data-ttu-id="b610c-414">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="b610c-414">128 characters</span></span>||<span data-ttu-id="b610c-415">Die Beschreibung, die Benutzern angezeigt wird, um den Zweck dieses Befehls anzugeben.</span><span class="sxs-lookup"><span data-stu-id="b610c-415">The description that appears to users to indicate the purpose of this command.</span></span>|
|`initialRun`|<span data-ttu-id="b610c-416">Boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="b610c-416">Boolean</span></span>|||<span data-ttu-id="b610c-417">Ein boolescher Wert, der angibt, ob der Befehl zunächst ohne Parameter ausgeführt werden soll.</span><span class="sxs-lookup"><span data-stu-id="b610c-417">A Boolean value that indicates whether the command should be run initially with no parameters.</span></span> <span data-ttu-id="b610c-418">Standard: `false`</span><span class="sxs-lookup"><span data-stu-id="b610c-418">Default: `false`</span></span>|
|`context`|<span data-ttu-id="b610c-419">Array von Zeichenfolgen</span><span class="sxs-lookup"><span data-stu-id="b610c-419">Array of Strings</span></span>|<span data-ttu-id="b610c-420">3</span><span class="sxs-lookup"><span data-stu-id="b610c-420">3</span></span>||<span data-ttu-id="b610c-421">Definiert, von wo aus die Nachrichtenerweiterung aufgerufen werden kann.</span><span class="sxs-lookup"><span data-stu-id="b610c-421">Defines where the message extension can be invoked from.</span></span> <span data-ttu-id="b610c-422">Beliebige Kombination aus `compose` , `commandBox` , `message` .</span><span class="sxs-lookup"><span data-stu-id="b610c-422">Any combination of `compose`, `commandBox`, `message`.</span></span> <span data-ttu-id="b610c-423">Standard ist `["compose", "commandBox"]`</span><span class="sxs-lookup"><span data-stu-id="b610c-423">Default is `["compose", "commandBox"]`</span></span>|
|`fetchTask`|<span data-ttu-id="b610c-424">Boolescher Wert</span><span class="sxs-lookup"><span data-stu-id="b610c-424">Boolean</span></span>|||<span data-ttu-id="b610c-425">Ein boolescher Wert, der angibt, ob das Aufgabenmodul dynamisch abgerufen werden soll.</span><span class="sxs-lookup"><span data-stu-id="b610c-425">A boolean value that indicates if it should fetch the task module dynamically.</span></span>|
|`taskInfo`|<span data-ttu-id="b610c-426">Objekt</span><span class="sxs-lookup"><span data-stu-id="b610c-426">Object</span></span>|||<span data-ttu-id="b610c-427">Geben Sie das Aufgabenmodul an, das beim Verwenden eines Befehls für die Messagingerweiterung vorab geladen werden soll.</span><span class="sxs-lookup"><span data-stu-id="b610c-427">Specify the task module to preload when using a messaging extension command.</span></span>|
|`taskInfo.title`|<span data-ttu-id="b610c-428">String</span><span class="sxs-lookup"><span data-stu-id="b610c-428">String</span></span>|<span data-ttu-id="b610c-429">64</span><span class="sxs-lookup"><span data-stu-id="b610c-429">64</span></span>||<span data-ttu-id="b610c-430">Titel des ersten Dialogfelds.</span><span class="sxs-lookup"><span data-stu-id="b610c-430">Initial dialog title.</span></span>|
|`taskInfo.width`|<span data-ttu-id="b610c-431">String</span><span class="sxs-lookup"><span data-stu-id="b610c-431">String</span></span>|||<span data-ttu-id="b610c-432">Dialogbreite – entweder eine Zahl in Pixel oder ein Standardlayout wie "groß", "mittel" oder "klein".</span><span class="sxs-lookup"><span data-stu-id="b610c-432">Dialog width - either a number in pixels or default layout such as 'large', 'medium', or 'small'.</span></span>|
|`taskInfo.height`|<span data-ttu-id="b610c-433">String</span><span class="sxs-lookup"><span data-stu-id="b610c-433">String</span></span>|||<span data-ttu-id="b610c-434">Dialoghöhe – entweder eine Zahl in Pixel oder ein Standardlayout wie "groß", "mittel" oder "klein".</span><span class="sxs-lookup"><span data-stu-id="b610c-434">Dialog height - either a number in pixels or default layout such as 'large', 'medium', or 'small'.</span></span>|
|`taskInfo.url`|<span data-ttu-id="b610c-435">String</span><span class="sxs-lookup"><span data-stu-id="b610c-435">String</span></span>|||<span data-ttu-id="b610c-436">Anfängliche Webview-URL.</span><span class="sxs-lookup"><span data-stu-id="b610c-436">Initial webview URL.</span></span>|
|`messageHandlers`|<span data-ttu-id="b610c-437">Array von Objekten</span><span class="sxs-lookup"><span data-stu-id="b610c-437">Array of Objects</span></span>|<span data-ttu-id="b610c-438">5 </span><span class="sxs-lookup"><span data-stu-id="b610c-438">5</span></span>||<span data-ttu-id="b610c-439">Eine Liste von Handlern, mit denen Apps aufgerufen werden können, wenn bestimmte Bedingungen erfüllt sind.</span><span class="sxs-lookup"><span data-stu-id="b610c-439">A list of handlers that allow apps to be invoked when certain conditions are met.</span></span> <span data-ttu-id="b610c-440">Domänen müssen auch in aufgeführt `validDomains` werden.</span><span class="sxs-lookup"><span data-stu-id="b610c-440">Domains must also be listed in `validDomains`.</span></span>|
|`messageHandlers.type`|<span data-ttu-id="b610c-441">String</span><span class="sxs-lookup"><span data-stu-id="b610c-441">String</span></span>|||<span data-ttu-id="b610c-442">Der Typ des Nachrichtenhandlers.</span><span class="sxs-lookup"><span data-stu-id="b610c-442">The type of message handler.</span></span> <span data-ttu-id="b610c-443">Muss `"link"` sein.</span><span class="sxs-lookup"><span data-stu-id="b610c-443">Must be `"link"`.</span></span>|
|`messageHandlers.value.domains`|<span data-ttu-id="b610c-444">Array von Zeichenfolgen</span><span class="sxs-lookup"><span data-stu-id="b610c-444">Array of Strings</span></span>|||<span data-ttu-id="b610c-445">Array von Domänen, für die der Linknachrichtenhandler registrieren kann.</span><span class="sxs-lookup"><span data-stu-id="b610c-445">Array of domains that the link message handler can register for.</span></span>|
|`parameters`|<span data-ttu-id="b610c-446">Array des Objekts</span><span class="sxs-lookup"><span data-stu-id="b610c-446">Array of object</span></span>|<span data-ttu-id="b610c-447">5 </span><span class="sxs-lookup"><span data-stu-id="b610c-447">5</span></span>|<span data-ttu-id="b610c-448">✔</span><span class="sxs-lookup"><span data-stu-id="b610c-448">✔</span></span>|<span data-ttu-id="b610c-449">Die Liste der Parameter, die der Befehl verwendet.</span><span class="sxs-lookup"><span data-stu-id="b610c-449">The list of parameters the command takes.</span></span> <span data-ttu-id="b610c-450">Minimum: 1; maximum: 5</span><span class="sxs-lookup"><span data-stu-id="b610c-450">Minimum: 1; maximum: 5</span></span>|
|`parameter.name`|<span data-ttu-id="b610c-451">String</span><span class="sxs-lookup"><span data-stu-id="b610c-451">String</span></span>|<span data-ttu-id="b610c-452">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="b610c-452">64 characters</span></span>|<span data-ttu-id="b610c-453">✔</span><span class="sxs-lookup"><span data-stu-id="b610c-453">✔</span></span>|<span data-ttu-id="b610c-454">Der Name des Parameters, wie er im Client angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="b610c-454">The name of the parameter as it appears in the client.</span></span> <span data-ttu-id="b610c-455">Dies ist in der Benutzeranforderung enthalten.</span><span class="sxs-lookup"><span data-stu-id="b610c-455">This is included in the user request.</span></span>|
|`parameter.title`|<span data-ttu-id="b610c-456">String</span><span class="sxs-lookup"><span data-stu-id="b610c-456">String</span></span>|<span data-ttu-id="b610c-457">32 Zeichen</span><span class="sxs-lookup"><span data-stu-id="b610c-457">32 characters</span></span>|<span data-ttu-id="b610c-458">✔</span><span class="sxs-lookup"><span data-stu-id="b610c-458">✔</span></span>|<span data-ttu-id="b610c-459">Benutzerfreundlicher Titel für den Parameter.</span><span class="sxs-lookup"><span data-stu-id="b610c-459">User-friendly title for the parameter.</span></span>|
|`parameter.description`|<span data-ttu-id="b610c-460">String</span><span class="sxs-lookup"><span data-stu-id="b610c-460">String</span></span>|<span data-ttu-id="b610c-461">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="b610c-461">128 characters</span></span>||<span data-ttu-id="b610c-462">Benutzerfreundliche Zeichenfolge, die den Zweck dieses Parameters beschreibt.</span><span class="sxs-lookup"><span data-stu-id="b610c-462">User-friendly string that describes this parameter’s purpose.</span></span>|
|`parameter.inputType`|<span data-ttu-id="b610c-463">String</span><span class="sxs-lookup"><span data-stu-id="b610c-463">String</span></span>|<span data-ttu-id="b610c-464">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="b610c-464">128 characters</span></span>||<span data-ttu-id="b610c-465">Definiert den Typ des Steuerelements, das in einem Aufgabenmodul für angezeigt `fetchTask: true` wird.</span><span class="sxs-lookup"><span data-stu-id="b610c-465">Defines the type of control displayed on a task module for `fetchTask: true`.</span></span> <span data-ttu-id="b610c-466">Einer von `text` , , , , , `textarea` `number` `date` `time` `toggle` `choiceset` .</span><span class="sxs-lookup"><span data-stu-id="b610c-466">One of `text`, `textarea`, `number`, `date`, `time`, `toggle`, `choiceset`.</span></span>|
|`parameter.choices`|<span data-ttu-id="b610c-467">Array von Objekten</span><span class="sxs-lookup"><span data-stu-id="b610c-467">Array of Objects</span></span>|<span data-ttu-id="b610c-468">10</span><span class="sxs-lookup"><span data-stu-id="b610c-468">10</span></span>||<span data-ttu-id="b610c-469">Die Auswahloptionen für `choiceset` .</span><span class="sxs-lookup"><span data-stu-id="b610c-469">The choice options for the `choiceset`.</span></span> <span data-ttu-id="b610c-470">Verwenden Sie nur, `parameter.inputType` wenn `choiceset` .</span><span class="sxs-lookup"><span data-stu-id="b610c-470">Use only when `parameter.inputType` is `choiceset`.</span></span>|
|`parameter.choices.title`|<span data-ttu-id="b610c-471">String</span><span class="sxs-lookup"><span data-stu-id="b610c-471">String</span></span>|<span data-ttu-id="b610c-472">128</span><span class="sxs-lookup"><span data-stu-id="b610c-472">128</span></span>||<span data-ttu-id="b610c-473">Titel der Auswahl.</span><span class="sxs-lookup"><span data-stu-id="b610c-473">Title of the choice.</span></span>|
|`parameter.choices.value`|<span data-ttu-id="b610c-474">String</span><span class="sxs-lookup"><span data-stu-id="b610c-474">String</span></span>|<span data-ttu-id="b610c-475">512</span><span class="sxs-lookup"><span data-stu-id="b610c-475">512</span></span>||<span data-ttu-id="b610c-476">Value of the choice.</span><span class="sxs-lookup"><span data-stu-id="b610c-476">Value of the choice.</span></span>|

## <a name="permissions"></a><span data-ttu-id="b610c-477">Berechtigungen</span><span class="sxs-lookup"><span data-stu-id="b610c-477">permissions</span></span>

<span data-ttu-id="b610c-478">**Optional**</span><span class="sxs-lookup"><span data-stu-id="b610c-478">**Optional**</span></span>

<span data-ttu-id="b610c-479">Ein Array von dem angibt, welche Berechtigungen die App anfordert, wodurch Endbenutzer wissen, `string` wie die Erweiterung funktioniert.</span><span class="sxs-lookup"><span data-stu-id="b610c-479">An array of `string` which specifies which permissions the app requests, which lets end users know how the extension will perform.</span></span> <span data-ttu-id="b610c-480">Die folgenden Optionen sind nicht exklusiv:</span><span class="sxs-lookup"><span data-stu-id="b610c-480">The following options are non-exclusive:</span></span>

* <span data-ttu-id="b610c-481">`identity`&emsp;Erfordert Benutzeridentitätsinformationen.</span><span class="sxs-lookup"><span data-stu-id="b610c-481">`identity` &emsp; Requires user identity information.</span></span>
* <span data-ttu-id="b610c-482">`messageTeamMembers`&emsp;Erfordert die Berechtigung zum Senden von Direktnachrichten an Teammitglieder.</span><span class="sxs-lookup"><span data-stu-id="b610c-482">`messageTeamMembers` &emsp; Requires permission to send direct messages to team members.</span></span>

<span data-ttu-id="b610c-483">Wenn Sie diese Berechtigungen beim Aktualisieren Ihrer App ändern, wiederholen Ihre Benutzer den Zustimmungsprozess, wenn sie die aktualisierte App zum ersten Mal ausführen.</span><span class="sxs-lookup"><span data-stu-id="b610c-483">Changing these permissions when updating your app will cause your users to repeat the consent process the first time they run the updated app.</span></span>

## <a name="devicepermissions"></a><span data-ttu-id="b610c-484">devicePermissions</span><span class="sxs-lookup"><span data-stu-id="b610c-484">devicePermissions</span></span>

<span data-ttu-id="b610c-485">**Optional** Array von Zeichenfolgen</span><span class="sxs-lookup"><span data-stu-id="b610c-485">**Optional** Array of Strings</span></span>

<span data-ttu-id="b610c-486">Gibt die systemeigenen Features auf dem Gerät eines Benutzers an, auf die Ihre App möglicherweise Zugriff anfordern kann.</span><span class="sxs-lookup"><span data-stu-id="b610c-486">Specifies the native features on a user's device that your app may request access to.</span></span> <span data-ttu-id="b610c-487">Mögliche Optionen sind:</span><span class="sxs-lookup"><span data-stu-id="b610c-487">Options are:</span></span>

* `geolocation`
* `media`
* `notifications`
* `midi`
* `openExternal`

## <a name="validdomains"></a><span data-ttu-id="b610c-488">validDomains</span><span class="sxs-lookup"><span data-stu-id="b610c-488">validDomains</span></span>

<span data-ttu-id="b610c-489">**Optional**, mit **Ausnahme erforderlich,** sofern angegeben</span><span class="sxs-lookup"><span data-stu-id="b610c-489">**Optional**, except **Required** where noted</span></span>

<span data-ttu-id="b610c-490">Eine Liste der gültigen Domänen, von denen die App erwartet, dass alle Inhalte geladen werden.</span><span class="sxs-lookup"><span data-stu-id="b610c-490">A list of valid domains from which the app expects to load any content.</span></span> <span data-ttu-id="b610c-491">Domänenauflistungen können Platzhalter enthalten, z. B. `*.example.com` .</span><span class="sxs-lookup"><span data-stu-id="b610c-491">Domain listings can include wildcards, for example `*.example.com`.</span></span> <span data-ttu-id="b610c-492">Dies entspricht genau einem Abschnitt der Domäne. wenn Sie übereinstimmen müssen, `a.b.example.com` verwenden Sie `*.*.example.com` .</span><span class="sxs-lookup"><span data-stu-id="b610c-492">This matches exactly one segment of the domain; if you need to match `a.b.example.com` then use `*.*.example.com`.</span></span> <span data-ttu-id="b610c-493">Wenn Ihre Registerkartenkonfiguration oder Inhaltsbenutzeroberfläche neben der für die Registerkartenkonfiguration verwendeten Domäne zu einer anderen Domäne navigieren muss, muss diese Domäne hier angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="b610c-493">If your tab configuration or content UI needs to navigate to any other domain besides the one use for tab configuration, that domain must be specified here.</span></span>

<span data-ttu-id="b610c-494">Es ist **jedoch nicht** erforderlich, die Domänen von Identitätsanbietern, die Sie unterstützen möchten, in Ihre App zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="b610c-494">It is **not** necessary to include the domains of identity providers you want to support in your app, however.</span></span> <span data-ttu-id="b610c-495">Um sich z. B. mit einer Google-ID zu authentifizieren, müssen Sie zu accounts.google.com umleiten, sie sollten jedoch keine accounts.google.com in `validDomains[]` enthalten.</span><span class="sxs-lookup"><span data-stu-id="b610c-495">For example, to authenticate using a Google ID, it's necessary to redirect to accounts.google.com, but you should not include accounts.google.com in `validDomains[]`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b610c-496">Fügen Sie keine Domänen hinzu, die sich außerhalb Ihres Steuerelements befinden, weder direkt noch über Platzhalter.</span><span class="sxs-lookup"><span data-stu-id="b610c-496">Do not add domains that are outside your control, either directly or via wildcards.</span></span> <span data-ttu-id="b610c-497">Beispielsweise ist `yourapp.onmicrosoft.com` gültig, aber `*.onmicrosoft.com` nicht gültig.</span><span class="sxs-lookup"><span data-stu-id="b610c-497">For example, `yourapp.onmicrosoft.com` is valid, but `*.onmicrosoft.com` is not valid.</span></span>

<span data-ttu-id="b610c-498">Das Objekt ist ein Array mit allen Elementen des Typs `string` .</span><span class="sxs-lookup"><span data-stu-id="b610c-498">The object is an array with all elements of the type `string`.</span></span>

## <a name="webapplicationinfo"></a><span data-ttu-id="b610c-499">webApplicationInfo</span><span class="sxs-lookup"><span data-stu-id="b610c-499">webApplicationInfo</span></span>

<span data-ttu-id="b610c-500">**Optional**</span><span class="sxs-lookup"><span data-stu-id="b610c-500">**Optional**</span></span>

<span data-ttu-id="b610c-501">Geben Sie Ihre AAD-App-ID Graph, um Benutzern die nahtlose Anmeldung bei Ihrer AAD-App zu ermöglichen.</span><span class="sxs-lookup"><span data-stu-id="b610c-501">Specify your AAD App ID and Graph information to help users seamlessly sign into your AAD app.</span></span>

|<span data-ttu-id="b610c-502">Name</span><span class="sxs-lookup"><span data-stu-id="b610c-502">Name</span></span>| <span data-ttu-id="b610c-503">Typ</span><span class="sxs-lookup"><span data-stu-id="b610c-503">Type</span></span>| <span data-ttu-id="b610c-504">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="b610c-504">Maximum size</span></span> | <span data-ttu-id="b610c-505">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="b610c-505">Required</span></span> | <span data-ttu-id="b610c-506">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b610c-506">Description</span></span>|
|---|---|---|---|---|
|`id`|<span data-ttu-id="b610c-507">String</span><span class="sxs-lookup"><span data-stu-id="b610c-507">String</span></span>|<span data-ttu-id="b610c-508">36 Zeichen</span><span class="sxs-lookup"><span data-stu-id="b610c-508">36 characters</span></span>|<span data-ttu-id="b610c-509">✔</span><span class="sxs-lookup"><span data-stu-id="b610c-509">✔</span></span>|<span data-ttu-id="b610c-510">AAD-Anwendungs-ID der App.</span><span class="sxs-lookup"><span data-stu-id="b610c-510">AAD application id of the app.</span></span> <span data-ttu-id="b610c-511">Diese ID muss eine GUID sein.</span><span class="sxs-lookup"><span data-stu-id="b610c-511">This id must be a GUID.</span></span>|
|`resource`|<span data-ttu-id="b610c-512">String</span><span class="sxs-lookup"><span data-stu-id="b610c-512">String</span></span>|<span data-ttu-id="b610c-513">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="b610c-513">2048 characters</span></span>|<span data-ttu-id="b610c-514">✔</span><span class="sxs-lookup"><span data-stu-id="b610c-514">✔</span></span>|<span data-ttu-id="b610c-515">Ressourcen-URL der App zum Abrufen des Authentifizierungstokens für SSO.</span><span class="sxs-lookup"><span data-stu-id="b610c-515">Resource url of app for acquiring auth token for SSO.</span></span>|
|`applicationPermissions`|<span data-ttu-id="b610c-516">Array</span><span class="sxs-lookup"><span data-stu-id="b610c-516">Array</span></span>|<span data-ttu-id="b610c-517">Maximal 100 Elemente</span><span class="sxs-lookup"><span data-stu-id="b610c-517">Maximum 100 items</span></span>|<span data-ttu-id="b610c-518">✔</span><span class="sxs-lookup"><span data-stu-id="b610c-518">✔</span></span>|<span data-ttu-id="b610c-519">Ressourcenberechtigungen für die Anwendung.</span><span class="sxs-lookup"><span data-stu-id="b610c-519">Resource permissions for application.</span></span>|

## <a name="configurableproperties"></a><span data-ttu-id="b610c-520">configurableProperties</span><span class="sxs-lookup"><span data-stu-id="b610c-520">configurableProperties</span></span>

<span data-ttu-id="b610c-521">**Optional** – Array</span><span class="sxs-lookup"><span data-stu-id="b610c-521">**Optional** - array</span></span>

<span data-ttu-id="b610c-522">Der `configurableProperties` Block definiert die App-Eigenschaften, die Teams Administrator anpassen kann.</span><span class="sxs-lookup"><span data-stu-id="b610c-522">The `configurableProperties` block defines the app properties that Teams admin can customize.</span></span> <span data-ttu-id="b610c-523">Weitere Informationen finden Sie unter [Anpassen von Apps in Microsoft Teams.](/MicrosoftTeams/customize-apps)</span><span class="sxs-lookup"><span data-stu-id="b610c-523">For more information, see [customize apps in Microsoft Teams](/MicrosoftTeams/customize-apps).</span></span>

> [!NOTE]
> <span data-ttu-id="b610c-524">Mindestens eine Eigenschaft muss definiert werden.</span><span class="sxs-lookup"><span data-stu-id="b610c-524">A minimum of one property must be defined.</span></span> <span data-ttu-id="b610c-525">Sie können in diesem Block maximal neun Eigenschaften definieren.</span><span class="sxs-lookup"><span data-stu-id="b610c-525">You can define a maximum of nine properties in this block.</span></span>
> <span data-ttu-id="b610c-526">Als bewährte Methode müssen Sie Anpassungsrichtlinien für App-Benutzer und -Kunden bereitstellen, die sie beim Anpassen Ihrer App befolgen müssen.</span><span class="sxs-lookup"><span data-stu-id="b610c-526">As a best practice, you must provide customization guidelines for app users and customers to follow when customizing your app.</span></span> 

<span data-ttu-id="b610c-527">Sie können eine der folgenden Eigenschaften definieren:</span><span class="sxs-lookup"><span data-stu-id="b610c-527">You can define any of the following properties:</span></span>
* <span data-ttu-id="b610c-528">`name`: Ermöglicht administratoren das Ändern des Anzeigenamens der App.</span><span class="sxs-lookup"><span data-stu-id="b610c-528">`name`: Allows admin to change the app's display name.</span></span>
* <span data-ttu-id="b610c-529">`shortDescription`: Ermöglicht Administratoren das Ändern der Kurzbeschreibung der App.</span><span class="sxs-lookup"><span data-stu-id="b610c-529">`shortDescription`: Allows admin to change the app's short description.</span></span>
* <span data-ttu-id="b610c-530">`longDescription`: Ermöglicht Administratoren das Ändern der detaillierten Beschreibung der App.</span><span class="sxs-lookup"><span data-stu-id="b610c-530">`longDescription`: Allows admin to change the app's detailed description.</span></span>
* <span data-ttu-id="b610c-531">`smallImageUrl`: Es handelt sich `outline` um die Eigenschaft im Block des `icons` Manifests.</span><span class="sxs-lookup"><span data-stu-id="b610c-531">`smallImageUrl`: It is the `outline` property in the `icons` block of the manifest.</span></span>
* <span data-ttu-id="b610c-532">`largeImageUrl`: Es handelt sich `color` um die Eigenschaft im Block des `icons` Manifests.</span><span class="sxs-lookup"><span data-stu-id="b610c-532">`largeImageUrl`: It is the `color` property in the `icons` block of the manifest.</span></span>
* <span data-ttu-id="b610c-533">`accentColor`: Es ist die Farbe, die in Verbindung mit und als Hintergrund für Ihre Gliederungssymbole verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="b610c-533">`accentColor`: It is the color to use in conjunction with and as a background for your outline icons.</span></span>
* <span data-ttu-id="b610c-534">`websiteUrl`: Es ist die https://-URL zur Website des Entwicklers.</span><span class="sxs-lookup"><span data-stu-id="b610c-534">`websiteUrl`: It is the https:// URL to the developer's website.</span></span>
* <span data-ttu-id="b610c-535">`privacyUrl`: Es ist die https://-URL zur Datenschutzrichtlinie des Entwicklers.</span><span class="sxs-lookup"><span data-stu-id="b610c-535">`privacyUrl`: It is the https:// URL to the developer's privacy policy.</span></span>
* <span data-ttu-id="b610c-536">`termsOfUseUrl`: Es ist die https:// URL zu den Nutzungsbedingungen des Entwicklers.</span><span class="sxs-lookup"><span data-stu-id="b610c-536">`termsOfUseUrl`: It is the https:// URL to the developer's terms of use.</span></span>

## <a name="defaultinstallscope"></a><span data-ttu-id="b610c-537">defaultInstallScope</span><span class="sxs-lookup"><span data-stu-id="b610c-537">defaultInstallScope</span></span>

<span data-ttu-id="b610c-538">**Optional** – Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="b610c-538">**Optional** - string</span></span>

<span data-ttu-id="b610c-539">Gibt den für diese App definierten Installationsbereich standardmäßig an.</span><span class="sxs-lookup"><span data-stu-id="b610c-539">Specifies the install scope defined for this app by default.</span></span> <span data-ttu-id="b610c-540">Der definierte Bereich ist die Option, die auf der Schaltfläche angezeigt wird, wenn ein Benutzer versucht, die App hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="b610c-540">The defined scope will be the option displayed on the button when a user tries to add the app.</span></span> <span data-ttu-id="b610c-541">Mögliche Optionen sind:</span><span class="sxs-lookup"><span data-stu-id="b610c-541">Options are:</span></span>
* `personal`
* `team`
* `groupchat`
* `meetings`

## <a name="defaultgroupcapability"></a><span data-ttu-id="b610c-542">defaultGroupCapability</span><span class="sxs-lookup"><span data-stu-id="b610c-542">defaultGroupCapability</span></span>

<span data-ttu-id="b610c-543">**Optional** - -Objekt</span><span class="sxs-lookup"><span data-stu-id="b610c-543">**Optional** - object</span></span>

<span data-ttu-id="b610c-544">Wenn ein Gruppeninstallationsbereich ausgewählt ist, wird die Standardfunktion definiert, wenn der Benutzer die App installiert.</span><span class="sxs-lookup"><span data-stu-id="b610c-544">When a group install scope is selected, it will define the default capability when the user installs the app.</span></span> <span data-ttu-id="b610c-545">Mögliche Optionen sind:</span><span class="sxs-lookup"><span data-stu-id="b610c-545">Options are:</span></span>
* `team`
* `groupchat`
* `meetings`
 
|<span data-ttu-id="b610c-546">Name</span><span class="sxs-lookup"><span data-stu-id="b610c-546">Name</span></span>| <span data-ttu-id="b610c-547">Typ</span><span class="sxs-lookup"><span data-stu-id="b610c-547">Type</span></span>| <span data-ttu-id="b610c-548">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="b610c-548">Maximum size</span></span> | <span data-ttu-id="b610c-549">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="b610c-549">Required</span></span> | <span data-ttu-id="b610c-550">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="b610c-550">Description</span></span>|
|---|---|---|---|---|
|`team`|<span data-ttu-id="b610c-551">string</span><span class="sxs-lookup"><span data-stu-id="b610c-551">string</span></span>|||<span data-ttu-id="b610c-552">Wenn der ausgewählte Installationsbereich ausgewählt ist, gibt `team` dieses Feld die verfügbare Standardfunktion an.</span><span class="sxs-lookup"><span data-stu-id="b610c-552">When the install scope selected is `team`, this field specifies the default capability available.</span></span> <span data-ttu-id="b610c-553">Optionen: `tab` , `bot` oder `connector` .</span><span class="sxs-lookup"><span data-stu-id="b610c-553">Options: `tab`, `bot`, or `connector`.</span></span>|
|`groupchat`|<span data-ttu-id="b610c-554">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="b610c-554">string</span></span>|||<span data-ttu-id="b610c-555">Wenn der ausgewählte Installationsbereich ausgewählt ist, gibt `groupchat` dieses Feld die verfügbare Standardfunktion an.</span><span class="sxs-lookup"><span data-stu-id="b610c-555">When the install scope selected is `groupchat`, this field specifies the default capability available.</span></span> <span data-ttu-id="b610c-556">Optionen: `tab` , `bot` oder `connector` .</span><span class="sxs-lookup"><span data-stu-id="b610c-556">Options: `tab`, `bot`, or `connector`.</span></span>|
|`meetings`|<span data-ttu-id="b610c-557">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="b610c-557">string</span></span>|||<span data-ttu-id="b610c-558">Wenn der ausgewählte Installationsbereich ausgewählt ist, gibt `meetings` dieses Feld die verfügbare Standardfunktion an.</span><span class="sxs-lookup"><span data-stu-id="b610c-558">When the install scope selected is `meetings`, this field specifies the default capability available.</span></span> <span data-ttu-id="b610c-559">Optionen: `tab` , `bot` oder `connector` .</span><span class="sxs-lookup"><span data-stu-id="b610c-559">Options: `tab`, `bot`, or `connector`.</span></span>|

