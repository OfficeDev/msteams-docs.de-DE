---
title: Referenz zum Entwicklervorschaumanifestschema
description: Beschreibt das vom Manifest unterstützte Schema für Microsoft Teams
ms.topic: reference
keywords: Teams-Manifestschema – Entwicklervorschau
localization_priority: Normal
ms.date: 05/20/2019
ms.openlocfilehash: c2009038341a22664b0f055fa9756a9d1eba87b9
ms.sourcegitcommit: 64c1cf2a268ef101a519bc31d171618d0f6cd12a
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/13/2021
ms.locfileid: "52915090"
---
# <a name="developer-preview-manifest-schema-for-microsoft-teams"></a><span data-ttu-id="0f09e-104">Entwicklervorschau-Manifestschema für Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="0f09e-104">Developer preview manifest schema for Microsoft Teams</span></span>

<span data-ttu-id="0f09e-105">Informationen zum Aktivieren der Entwicklervorschau finden Sie in der [öffentlichen Entwicklervorschau für Microsoft Teams.](~/resources/dev-preview/developer-preview-intro.md)</span><span class="sxs-lookup"><span data-stu-id="0f09e-105">For information on how to enable developer preview, see [public developer preview for Microsoft Teams](~/resources/dev-preview/developer-preview-intro.md).</span></span>

> [!NOTE]
> * <span data-ttu-id="0f09e-106">Wenn Sie keine Vorschaufeatures für Entwickler verwenden, verwenden Sie stattdessen das [App-Manifest für GA-Features.](~/resources/schema/manifest-schema.md)</span><span class="sxs-lookup"><span data-stu-id="0f09e-106">If you aren't using developer preview features, use the [app manifest for GA features](~/resources/schema/manifest-schema.md) instead.</span></span>

<span data-ttu-id="0f09e-107">Das Microsoft Teams Manifest beschreibt, wie die App in das Microsoft Teams Produkt integriert wird.</span><span class="sxs-lookup"><span data-stu-id="0f09e-107">The Microsoft Teams manifest describes how the app integrates into the Microsoft Teams product.</span></span> <span data-ttu-id="0f09e-108">Ihr Manifest muss dem schema gehosteten [`https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json`](https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json) entsprechen.</span><span class="sxs-lookup"><span data-stu-id="0f09e-108">Your manifest must conform to the schema hosted at [`https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json`](https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json).</span></span>

<span data-ttu-id="0f09e-109">Weitere Informationen zu den verfügbaren Features finden Sie [unter: Features in der Public Developer Preview für Microsoft Teams](~/resources/dev-preview/developer-preview-features.md).</span><span class="sxs-lookup"><span data-stu-id="0f09e-109">For more information on the features available see: [Features in the Public Developer Preview for Microsoft Teams](~/resources/dev-preview/developer-preview-features.md).</span></span>

## <a name="sample-full-manifest"></a><span data-ttu-id="0f09e-110">Vollständiges Beispielmanifest</span><span class="sxs-lookup"><span data-stu-id="0f09e-110">Sample full manifest</span></span>

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

<span data-ttu-id="0f09e-111">Das Schema definiert die folgenden Eigenschaften:</span><span class="sxs-lookup"><span data-stu-id="0f09e-111">The schema defines the following properties:</span></span>

## <a name="schema"></a><span data-ttu-id="0f09e-112">$schema</span><span class="sxs-lookup"><span data-stu-id="0f09e-112">$schema</span></span>

<span data-ttu-id="0f09e-113">*Optional, aber empfohlen* &ndash; Schnur</span><span class="sxs-lookup"><span data-stu-id="0f09e-113">*Optional, but recommended* &ndash; String</span></span>

<span data-ttu-id="0f09e-114">Die https://-URL, die auf das JSON-Schema für das Manifest verweist.</span><span class="sxs-lookup"><span data-stu-id="0f09e-114">The https:// URL referencing the JSON Schema for the manifest.</span></span>

## <a name="manifestversion"></a><span data-ttu-id="0f09e-115">manifestVersion</span><span class="sxs-lookup"><span data-stu-id="0f09e-115">manifestVersion</span></span>

<span data-ttu-id="0f09e-116">**Erforderlich** &ndash; Schnur</span><span class="sxs-lookup"><span data-stu-id="0f09e-116">**Required** &ndash; String</span></span>

<span data-ttu-id="0f09e-117">Die Version des Manifestschemas, das dieses Manifest verwendet.</span><span class="sxs-lookup"><span data-stu-id="0f09e-117">The version of the manifest schema this manifest is using.</span></span> <span data-ttu-id="0f09e-118">Es sollte "devPreview" sein.</span><span class="sxs-lookup"><span data-stu-id="0f09e-118">It should be "devPreview".</span></span>

## <a name="version"></a><span data-ttu-id="0f09e-119">Version</span><span class="sxs-lookup"><span data-stu-id="0f09e-119">version</span></span>

<span data-ttu-id="0f09e-120">**Erforderlich** &ndash; Schnur</span><span class="sxs-lookup"><span data-stu-id="0f09e-120">**Required** &ndash; String</span></span>

<span data-ttu-id="0f09e-121">Die Version der spezifischen App.</span><span class="sxs-lookup"><span data-stu-id="0f09e-121">The version of the specific app.</span></span> <span data-ttu-id="0f09e-122">Wenn Sie etwas in Ihrem Manifest aktualisieren, muss auch die Version erhöht werden.</span><span class="sxs-lookup"><span data-stu-id="0f09e-122">If you update something in your manifest, the version must be incremented as well.</span></span> <span data-ttu-id="0f09e-123">Auf diese Weise wird bei der Installation des neuen Manifests das vorhandene überschrieben, und der Benutzer erhält die neue Funktionalität.</span><span class="sxs-lookup"><span data-stu-id="0f09e-123">This way, when the new manifest is installed, it will overwrite the existing one and the user will get the new functionality.</span></span> <span data-ttu-id="0f09e-124">Wenn diese App an den Store übermittelt wurde, muss das neue Manifest erneut übermittelt und erneut überprüft werden.</span><span class="sxs-lookup"><span data-stu-id="0f09e-124">If this app was submitted to the store, the new manifest will have to be re-submitted and re-validated.</span></span> <span data-ttu-id="0f09e-125">Anschließend erhalten Benutzer dieser App das neue aktualisierte Manifest automatisch in einigen Stunden, nachdem es genehmigt wurde.</span><span class="sxs-lookup"><span data-stu-id="0f09e-125">Then, users of this app will get the new updated manifest automatically in a few hours, after it is approved.</span></span>

<span data-ttu-id="0f09e-126">Wenn sich die von der App angeforderten Berechtigungen ändern, werden die Benutzer aufgefordert, ein Upgrade durchzuführen und der App erneut zuzustimmen.</span><span class="sxs-lookup"><span data-stu-id="0f09e-126">If the app requested permissions change, users will be prompted to upgrade and re-consent to the app.</span></span>

<span data-ttu-id="0f09e-127">Diese Versionszeichenfolge muss dem [Semverstandard](http://semver.org/) (MAJOR. kleiner. PATCH).</span><span class="sxs-lookup"><span data-stu-id="0f09e-127">This version string must follow the [semver](http://semver.org/) standard (MAJOR.MINOR.PATCH).</span></span>

## <a name="id"></a><span data-ttu-id="0f09e-128">id</span><span class="sxs-lookup"><span data-stu-id="0f09e-128">id</span></span>

<span data-ttu-id="0f09e-129">**Erforderlich** &ndash; Microsoft-App-ID</span><span class="sxs-lookup"><span data-stu-id="0f09e-129">**Required** &ndash; Microsoft app ID</span></span>

<span data-ttu-id="0f09e-130">Der eindeutige von Microsoft generierte Bezeichner für diese App.</span><span class="sxs-lookup"><span data-stu-id="0f09e-130">The unique Microsoft-generated identifier for this app.</span></span> <span data-ttu-id="0f09e-131">Wenn Sie einen Bot über die Microsoft Bot Framework registriert haben oder sich die Web-App Ihrer Registerkarte bereits bei Microsoft anmeldet, sollten Sie bereits über eine ID verfügen und sie hier eingeben.</span><span class="sxs-lookup"><span data-stu-id="0f09e-131">If you have registered a bot via the Microsoft Bot Framework, or your tab's web app already signs in with Microsoft, you should already have an ID and should enter it here.</span></span> <span data-ttu-id="0f09e-132">Andernfalls sollten Sie eine neue ID im Microsoft-Anwendungsregistrierungsportal[(Meine Anwendungen)](https://apps.dev.microsoft.com)generieren, sie hier eingeben und dann wiederverwenden, wenn Sie [einen Bot hinzufügen.](~/bots/how-to/create-a-bot-for-teams.md)</span><span class="sxs-lookup"><span data-stu-id="0f09e-132">Otherwise, you should generate a new ID at the Microsoft Application Registration Portal ([My Applications](https://apps.dev.microsoft.com)), enter it here, and then reuse it when you [add a bot](~/bots/how-to/create-a-bot-for-teams.md).</span></span>

## <a name="packagename"></a><span data-ttu-id="0f09e-133">Packagename</span><span class="sxs-lookup"><span data-stu-id="0f09e-133">packageName</span></span>

<span data-ttu-id="0f09e-134">**Erforderlich** &ndash; Schnur</span><span class="sxs-lookup"><span data-stu-id="0f09e-134">**Required** &ndash; String</span></span>

<span data-ttu-id="0f09e-135">Ein eindeutiger Bezeichner für diese App in umgekehrter Domänenschreibweise; z. B. com.example.myapp.</span><span class="sxs-lookup"><span data-stu-id="0f09e-135">A unique identifier for this app in reverse domain notation; for example, com.example.myapp.</span></span>

## <a name="developer"></a><span data-ttu-id="0f09e-136">developer</span><span class="sxs-lookup"><span data-stu-id="0f09e-136">developer</span></span>

<span data-ttu-id="0f09e-137">**Required**</span><span class="sxs-lookup"><span data-stu-id="0f09e-137">**Required**</span></span>

<span data-ttu-id="0f09e-138">Gibt Informationen zu Ihrem Unternehmen an.</span><span class="sxs-lookup"><span data-stu-id="0f09e-138">Specifies information about your company.</span></span> <span data-ttu-id="0f09e-139">Bei An AppSource übermittelten Apps (früher Office Store) müssen diese Werte mit den Informationen in Ihrem AppSource-Eintrag übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="0f09e-139">For apps submitted to AppSource (formerly Office Store), these values must match the information in your AppSource entry.</span></span>

|<span data-ttu-id="0f09e-140">Name</span><span class="sxs-lookup"><span data-stu-id="0f09e-140">Name</span></span>| <span data-ttu-id="0f09e-141">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="0f09e-141">Maximum size</span></span> | <span data-ttu-id="0f09e-142">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="0f09e-142">Required</span></span> | <span data-ttu-id="0f09e-143">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="0f09e-143">Description</span></span>|
|---|---|---|---|
|`name`|<span data-ttu-id="0f09e-144">32 Zeichen</span><span class="sxs-lookup"><span data-stu-id="0f09e-144">32 characters</span></span>|<span data-ttu-id="0f09e-145">✔</span><span class="sxs-lookup"><span data-stu-id="0f09e-145">✔</span></span>|<span data-ttu-id="0f09e-146">Der Anzeigename für den Entwickler.</span><span class="sxs-lookup"><span data-stu-id="0f09e-146">The display name for the developer.</span></span>|
|`websiteUrl`|<span data-ttu-id="0f09e-147">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="0f09e-147">2048 characters</span></span>|<span data-ttu-id="0f09e-148">✔</span><span class="sxs-lookup"><span data-stu-id="0f09e-148">✔</span></span>|<span data-ttu-id="0f09e-149">Die https:// URL zur Website des Entwicklers.</span><span class="sxs-lookup"><span data-stu-id="0f09e-149">The https:// URL to the developer's website.</span></span> <span data-ttu-id="0f09e-150">Dieser Link sollte Benutzer zu Ihrem Unternehmen oder zu einer produktspezifischen Angebotsseite führen.</span><span class="sxs-lookup"><span data-stu-id="0f09e-150">This link should take users to your company or product-specific landing page.</span></span>|
|`privacyUrl`|<span data-ttu-id="0f09e-151">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="0f09e-151">2048 characters</span></span>|<span data-ttu-id="0f09e-152">✔</span><span class="sxs-lookup"><span data-stu-id="0f09e-152">✔</span></span>|<span data-ttu-id="0f09e-153">Die https:// URL zur Datenschutzrichtlinie des Entwicklers.</span><span class="sxs-lookup"><span data-stu-id="0f09e-153">The https:// URL to the developer's privacy policy.</span></span>|
|`termsOfUseUrl`|<span data-ttu-id="0f09e-154">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="0f09e-154">2048 characters</span></span>|<span data-ttu-id="0f09e-155">✔</span><span class="sxs-lookup"><span data-stu-id="0f09e-155">✔</span></span>|<span data-ttu-id="0f09e-156">Die https:// URL zu den Nutzungsbedingungen des Entwicklers.</span><span class="sxs-lookup"><span data-stu-id="0f09e-156">The https:// URL to the developer's terms of use.</span></span>|
|`mpnId`|<span data-ttu-id="0f09e-157">10 Zeichen</span><span class="sxs-lookup"><span data-stu-id="0f09e-157">10 characters</span></span>|<span data-ttu-id="0f09e-158">✔</span><span class="sxs-lookup"><span data-stu-id="0f09e-158">✔</span></span>|<span data-ttu-id="0f09e-159">**Optional** Die Microsoft Partner Network-ID, die die Partnerorganisation identifiziert, die die App erstellt.</span><span class="sxs-lookup"><span data-stu-id="0f09e-159">**Optional** The Microsoft Partner Network ID that identifies the partner organization building the app.</span></span>|

## <a name="localizationinfo"></a><span data-ttu-id="0f09e-160">localizationInfo</span><span class="sxs-lookup"><span data-stu-id="0f09e-160">localizationInfo</span></span>

<span data-ttu-id="0f09e-161">**Optional**</span><span class="sxs-lookup"><span data-stu-id="0f09e-161">**Optional**</span></span>

<span data-ttu-id="0f09e-162">Ermöglicht die Angabe einer Standardsprache sowie Zeiger auf zusätzliche Sprachdateien.</span><span class="sxs-lookup"><span data-stu-id="0f09e-162">Allows the specification of a default language, as well as pointers to additional language files.</span></span> <span data-ttu-id="0f09e-163">Siehe [Lokalisierung](~/concepts/build-and-test/apps-localization.md).</span><span class="sxs-lookup"><span data-stu-id="0f09e-163">See [localization](~/concepts/build-and-test/apps-localization.md).</span></span>

|<span data-ttu-id="0f09e-164">Name</span><span class="sxs-lookup"><span data-stu-id="0f09e-164">Name</span></span>| <span data-ttu-id="0f09e-165">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="0f09e-165">Maximum size</span></span> | <span data-ttu-id="0f09e-166">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="0f09e-166">Required</span></span> | <span data-ttu-id="0f09e-167">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="0f09e-167">Description</span></span>|
|---|---|---|---|
|`defaultLanguageTag`|<span data-ttu-id="0f09e-168">4 Zeichen</span><span class="sxs-lookup"><span data-stu-id="0f09e-168">4 characters</span></span>|<span data-ttu-id="0f09e-169">✔</span><span class="sxs-lookup"><span data-stu-id="0f09e-169">✔</span></span>|<span data-ttu-id="0f09e-170">Das Sprachtag der Zeichenfolgen in dieser Manifestdatei auf oberster Ebene.</span><span class="sxs-lookup"><span data-stu-id="0f09e-170">The language tag of the strings in this top level manifest file.</span></span>|

### <a name="localizationinfoadditionallanguages"></a><span data-ttu-id="0f09e-171">localizationInfo.additionalLanguages</span><span class="sxs-lookup"><span data-stu-id="0f09e-171">localizationInfo.additionalLanguages</span></span>

<span data-ttu-id="0f09e-172">Ein Array von Objekten, die zusätzliche Sprachübersetzungen angeben.</span><span class="sxs-lookup"><span data-stu-id="0f09e-172">An array of objects specifying additional language translations.</span></span>

|<span data-ttu-id="0f09e-173">Name</span><span class="sxs-lookup"><span data-stu-id="0f09e-173">Name</span></span>| <span data-ttu-id="0f09e-174">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="0f09e-174">Maximum size</span></span> | <span data-ttu-id="0f09e-175">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="0f09e-175">Required</span></span> | <span data-ttu-id="0f09e-176">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="0f09e-176">Description</span></span>|
|---|---|---|---|
|`languageTag`|<span data-ttu-id="0f09e-177">4 Zeichen</span><span class="sxs-lookup"><span data-stu-id="0f09e-177">4 characters</span></span>|<span data-ttu-id="0f09e-178">✔</span><span class="sxs-lookup"><span data-stu-id="0f09e-178">✔</span></span>|<span data-ttu-id="0f09e-179">Das Sprachtag der Zeichenfolgen in der bereitgestellten Datei.</span><span class="sxs-lookup"><span data-stu-id="0f09e-179">The language tag of the strings in the provided file.</span></span>|
|`file`|<span data-ttu-id="0f09e-180">4 Zeichen</span><span class="sxs-lookup"><span data-stu-id="0f09e-180">4 characters</span></span>|<span data-ttu-id="0f09e-181">✔</span><span class="sxs-lookup"><span data-stu-id="0f09e-181">✔</span></span>|<span data-ttu-id="0f09e-182">Ein relativer Dateipfad zu einer JSON-Datei, die die übersetzten Zeichenfolgen enthält.</span><span class="sxs-lookup"><span data-stu-id="0f09e-182">A relative file path to a the .json file containing the translated strings.</span></span>|

## <a name="name"></a><span data-ttu-id="0f09e-183">name</span><span class="sxs-lookup"><span data-stu-id="0f09e-183">name</span></span>

<span data-ttu-id="0f09e-184">**Required**</span><span class="sxs-lookup"><span data-stu-id="0f09e-184">**Required**</span></span>

<span data-ttu-id="0f09e-185">Der Name Ihrer App-Erfahrung, der Benutzern in der Teams angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="0f09e-185">The name of your app experience, displayed to users in the Teams experience.</span></span> <span data-ttu-id="0f09e-186">Für an AppSource übermittelte Apps müssen diese Werte mit den Informationen in Ihrem AppSource-Eintrag übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="0f09e-186">For apps submitted to AppSource, these values must match the information in your AppSource entry.</span></span> <span data-ttu-id="0f09e-187">Die Werte von `short` und sollten nicht identisch `full` sein.</span><span class="sxs-lookup"><span data-stu-id="0f09e-187">The values of `short` and `full` should not be the same.</span></span>

|<span data-ttu-id="0f09e-188">Name</span><span class="sxs-lookup"><span data-stu-id="0f09e-188">Name</span></span>| <span data-ttu-id="0f09e-189">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="0f09e-189">Maximum size</span></span> | <span data-ttu-id="0f09e-190">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="0f09e-190">Required</span></span> | <span data-ttu-id="0f09e-191">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="0f09e-191">Description</span></span>|
|---|---|---|---|
|`short`|<span data-ttu-id="0f09e-192">30 Zeichen</span><span class="sxs-lookup"><span data-stu-id="0f09e-192">30 characters</span></span>|<span data-ttu-id="0f09e-193">✔</span><span class="sxs-lookup"><span data-stu-id="0f09e-193">✔</span></span>|<span data-ttu-id="0f09e-194">Der kurze Anzeigename für die App.</span><span class="sxs-lookup"><span data-stu-id="0f09e-194">The short display name for the app.</span></span>|
|`full`|<span data-ttu-id="0f09e-195">100 Zeichen</span><span class="sxs-lookup"><span data-stu-id="0f09e-195">100 characters</span></span>||<span data-ttu-id="0f09e-196">Der vollständige Name der App, der verwendet wird, wenn der vollständige App-Name 30 Zeichen überschreitet.</span><span class="sxs-lookup"><span data-stu-id="0f09e-196">The full name of the app, used if the full app name exceeds 30 characters.</span></span>|

## <a name="description"></a><span data-ttu-id="0f09e-197">description</span><span class="sxs-lookup"><span data-stu-id="0f09e-197">description</span></span>

<span data-ttu-id="0f09e-198">**Required**</span><span class="sxs-lookup"><span data-stu-id="0f09e-198">**Required**</span></span>

<span data-ttu-id="0f09e-199">Beschreibt Ihre App für Benutzer.</span><span class="sxs-lookup"><span data-stu-id="0f09e-199">Describes your app to users.</span></span> <span data-ttu-id="0f09e-200">Für an AppSource übermittelte Apps müssen diese Werte mit den Informationen in Ihrem AppSource-Eintrag übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="0f09e-200">For apps submitted to AppSource, these values must match the information in your AppSource entry.</span></span>

<span data-ttu-id="0f09e-201">Stellen Sie sicher, dass Ihre Beschreibung Ihre Erfahrung genau beschreibt und Informationen bereitstellt, die potenziellen Kunden helfen, zu verstehen, was Ihre Erfahrung bewirkt.</span><span class="sxs-lookup"><span data-stu-id="0f09e-201">Ensure that your description accurately describes your experience and provides information to help potential customers understand what your experience does.</span></span> <span data-ttu-id="0f09e-202">Beachten Sie in der vollständigen Beschreibung auch, ob für die Verwendung ein externes Konto erforderlich ist.</span><span class="sxs-lookup"><span data-stu-id="0f09e-202">You should also note, in the full description, if an external account is required for use.</span></span> <span data-ttu-id="0f09e-203">Die Werte von `short` und sollten nicht identisch `full` sein.</span><span class="sxs-lookup"><span data-stu-id="0f09e-203">The values of `short` and `full` should not be the same.</span></span>  <span data-ttu-id="0f09e-204">Ihre kurze Beschreibung darf nicht innerhalb der langen Beschreibung wiederholt werden und darf keinen anderen App-Namen enthalten.</span><span class="sxs-lookup"><span data-stu-id="0f09e-204">Your short description must not be repeated within the long description and must not include any other app name.</span></span>

|<span data-ttu-id="0f09e-205">Name</span><span class="sxs-lookup"><span data-stu-id="0f09e-205">Name</span></span>| <span data-ttu-id="0f09e-206">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="0f09e-206">Maximum size</span></span> | <span data-ttu-id="0f09e-207">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="0f09e-207">Required</span></span> | <span data-ttu-id="0f09e-208">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="0f09e-208">Description</span></span>|
|---|---|---|---|
|`short`|<span data-ttu-id="0f09e-209">80 Zeichen</span><span class="sxs-lookup"><span data-stu-id="0f09e-209">80 characters</span></span>|<span data-ttu-id="0f09e-210">✔</span><span class="sxs-lookup"><span data-stu-id="0f09e-210">✔</span></span>|<span data-ttu-id="0f09e-211">Eine kurze Beschreibung der App-Erfahrung, die verwendet wird, wenn der Platz begrenzt ist.</span><span class="sxs-lookup"><span data-stu-id="0f09e-211">A short description of your app experience, used when space is limited.</span></span>|
|`full`|<span data-ttu-id="0f09e-212">4000 Zeichen</span><span class="sxs-lookup"><span data-stu-id="0f09e-212">4000 characters</span></span>|<span data-ttu-id="0f09e-213">✔</span><span class="sxs-lookup"><span data-stu-id="0f09e-213">✔</span></span>|<span data-ttu-id="0f09e-214">Die vollständige Beschreibung Ihrer App.</span><span class="sxs-lookup"><span data-stu-id="0f09e-214">The full description of your app.</span></span>|

## <a name="icons"></a><span data-ttu-id="0f09e-215">Symbole</span><span class="sxs-lookup"><span data-stu-id="0f09e-215">icons</span></span>

<span data-ttu-id="0f09e-216">**Required**</span><span class="sxs-lookup"><span data-stu-id="0f09e-216">**Required**</span></span>

<span data-ttu-id="0f09e-217">Symbole, die in der Teams-App verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="0f09e-217">Icons used within the Teams app.</span></span> <span data-ttu-id="0f09e-218">Die Symboldateien müssen als Teil des Uploadpakets enthalten sein.</span><span class="sxs-lookup"><span data-stu-id="0f09e-218">The icon files must be included as part of the upload package.</span></span>

|<span data-ttu-id="0f09e-219">Name</span><span class="sxs-lookup"><span data-stu-id="0f09e-219">Name</span></span>| <span data-ttu-id="0f09e-220">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="0f09e-220">Maximum size</span></span> | <span data-ttu-id="0f09e-221">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="0f09e-221">Required</span></span> | <span data-ttu-id="0f09e-222">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="0f09e-222">Description</span></span>|
|---|---|---|---|
|`outline`|<span data-ttu-id="0f09e-223">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="0f09e-223">2048 characters</span></span>|<span data-ttu-id="0f09e-224">✔</span><span class="sxs-lookup"><span data-stu-id="0f09e-224">✔</span></span>|<span data-ttu-id="0f09e-225">Ein relativer Dateipfad zu einem transparenten 32 x 32 PNG-Gliederungssymbol.</span><span class="sxs-lookup"><span data-stu-id="0f09e-225">A relative file path to a transparent 32x32 PNG outline icon.</span></span>|
|`color`|<span data-ttu-id="0f09e-226">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="0f09e-226">2048 characters</span></span>|<span data-ttu-id="0f09e-227">✔</span><span class="sxs-lookup"><span data-stu-id="0f09e-227">✔</span></span>|<span data-ttu-id="0f09e-228">Ein relativer Dateipfad zu einem farbigen PNG-Symbol mit 192 x 192.</span><span class="sxs-lookup"><span data-stu-id="0f09e-228">A relative file path to a full color 192x192 PNG icon.</span></span>|

## <a name="accentcolor"></a><span data-ttu-id="0f09e-229">accentColor</span><span class="sxs-lookup"><span data-stu-id="0f09e-229">accentColor</span></span>

<span data-ttu-id="0f09e-230">**Erforderlich** &ndash; Schnur</span><span class="sxs-lookup"><span data-stu-id="0f09e-230">**Required** &ndash; String</span></span>

<span data-ttu-id="0f09e-231">Eine Farbe, die in Verbindung mit und als Hintergrund für Ihre Gliederungssymbole verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="0f09e-231">A color to use in conjunction with and as a background for your outline icons.</span></span>

<span data-ttu-id="0f09e-232">Der Wert muss ein gültiger HTML-Farbcode sein, der mit "#" beginnt, z. `#4464ee` B. .</span><span class="sxs-lookup"><span data-stu-id="0f09e-232">The value must be a valid HTML color code starting with '#', for example `#4464ee`.</span></span>

## <a name="configurabletabs"></a><span data-ttu-id="0f09e-233">configurableTabs</span><span class="sxs-lookup"><span data-stu-id="0f09e-233">configurableTabs</span></span>

<span data-ttu-id="0f09e-234">**Optional**</span><span class="sxs-lookup"><span data-stu-id="0f09e-234">**Optional**</span></span>

<span data-ttu-id="0f09e-235">Wird verwendet, wenn Ihre App-Erfahrung über eine Registerkartenoberfläche im Teamkanal verfügt, die eine zusätzliche Konfiguration erfordert, bevor sie hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="0f09e-235">Used when your app experience has a team channel tab experience that requires extra configuration before it is added.</span></span> <span data-ttu-id="0f09e-236">Konfigurierbare Registerkarten werden nur im Teams-Bereich unterstützt, und derzeit wird nur eine Registerkarte pro App unterstützt.</span><span class="sxs-lookup"><span data-stu-id="0f09e-236">Configurable tabs are supported only in the teams scope, and currently only one tab per app is supported.</span></span>

<span data-ttu-id="0f09e-237">Das Objekt ist ein Array mit allen Elementen des Typs `object` .</span><span class="sxs-lookup"><span data-stu-id="0f09e-237">The object is an array with all elements of the type `object`.</span></span> <span data-ttu-id="0f09e-238">Dieser Block ist nur für Lösungen erforderlich, die eine konfigurierbare Kanalregisterkartenlösung bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="0f09e-238">This block is required only for solutions that provide a configurable channel tab solution.</span></span>

|<span data-ttu-id="0f09e-239">Name</span><span class="sxs-lookup"><span data-stu-id="0f09e-239">Name</span></span>| <span data-ttu-id="0f09e-240">Typ</span><span class="sxs-lookup"><span data-stu-id="0f09e-240">Type</span></span>| <span data-ttu-id="0f09e-241">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="0f09e-241">Maximum size</span></span> | <span data-ttu-id="0f09e-242">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="0f09e-242">Required</span></span> | <span data-ttu-id="0f09e-243">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="0f09e-243">Description</span></span>|
|---|---|---|---|---|
|`configurationUrl`|<span data-ttu-id="0f09e-244">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="0f09e-244">String</span></span>|<span data-ttu-id="0f09e-245">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="0f09e-245">2048 characters</span></span>|<span data-ttu-id="0f09e-246">✔</span><span class="sxs-lookup"><span data-stu-id="0f09e-246">✔</span></span>|<span data-ttu-id="0f09e-247">Die https:// URL, die beim Konfigurieren der Registerkarte verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="0f09e-247">The https:// URL to use when configuring the tab.</span></span>|
|`canUpdateConfiguration`|<span data-ttu-id="0f09e-248">Boolesch</span><span class="sxs-lookup"><span data-stu-id="0f09e-248">Boolean</span></span>|||<span data-ttu-id="0f09e-249">Ein Wert, der angibt, ob eine Instanz der Konfiguration der Registerkarte vom Benutzer nach der Erstellung aktualisiert werden kann.</span><span class="sxs-lookup"><span data-stu-id="0f09e-249">A value indicating whether an instance of the tab's configuration can be updated by the user after creation.</span></span> <span data-ttu-id="0f09e-250">Standard: `true`</span><span class="sxs-lookup"><span data-stu-id="0f09e-250">Default: `true`</span></span>|
|`scopes`|<span data-ttu-id="0f09e-251">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="0f09e-251">Array of enum</span></span>|<span data-ttu-id="0f09e-252">1</span><span class="sxs-lookup"><span data-stu-id="0f09e-252">1</span></span>|<span data-ttu-id="0f09e-253">✔</span><span class="sxs-lookup"><span data-stu-id="0f09e-253">✔</span></span>|<span data-ttu-id="0f09e-254">Derzeit unterstützen konfigurierbare Registerkarten nur die `team` Bereiche und `groupchat` Bereiche.</span><span class="sxs-lookup"><span data-stu-id="0f09e-254">Currently, configurable tabs support only the `team` and `groupchat` scopes.</span></span> |
|`sharePointPreviewImage`|<span data-ttu-id="0f09e-255">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="0f09e-255">String</span></span>|<span data-ttu-id="0f09e-256">2048</span><span class="sxs-lookup"><span data-stu-id="0f09e-256">2048</span></span>||<span data-ttu-id="0f09e-257">Ein relativer Dateipfad zu einem Registerkartenvorschaubild zur Verwendung in SharePoint.</span><span class="sxs-lookup"><span data-stu-id="0f09e-257">A relative file path to a tab preview image for use in SharePoint.</span></span> <span data-ttu-id="0f09e-258">Größe 1024 x 768.</span><span class="sxs-lookup"><span data-stu-id="0f09e-258">Size 1024x768.</span></span> |
|`supportedSharePointHosts`|<span data-ttu-id="0f09e-259">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="0f09e-259">Array of enum</span></span>|<span data-ttu-id="0f09e-260">1</span><span class="sxs-lookup"><span data-stu-id="0f09e-260">1</span></span>||<span data-ttu-id="0f09e-261">Definiert, wie Ihre Registerkarte in SharePoint zur Verfügung gestellt wird.</span><span class="sxs-lookup"><span data-stu-id="0f09e-261">Defines how your tab will be made available in SharePoint.</span></span> <span data-ttu-id="0f09e-262">Optionen sind `sharePointFullPage` und `sharePointWebPart`</span><span class="sxs-lookup"><span data-stu-id="0f09e-262">Options are `sharePointFullPage` and `sharePointWebPart`</span></span> |

## <a name="statictabs"></a><span data-ttu-id="0f09e-263">staticTabs</span><span class="sxs-lookup"><span data-stu-id="0f09e-263">staticTabs</span></span>

<span data-ttu-id="0f09e-264">**Optional**</span><span class="sxs-lookup"><span data-stu-id="0f09e-264">**Optional**</span></span>

<span data-ttu-id="0f09e-265">Definiert eine Gruppe von Registerkarten, die standardmäßig "angeheftet" werden können, ohne dass der Benutzer sie manuell hinzufügt.</span><span class="sxs-lookup"><span data-stu-id="0f09e-265">Defines a set of tabs that can be "pinned" by default, without the user adding them manually.</span></span> <span data-ttu-id="0f09e-266">Im Bereich deklarierte statische `personal` Registerkarten werden immer an die persönliche Benutzeroberfläche der App angeheftet.</span><span class="sxs-lookup"><span data-stu-id="0f09e-266">Static tabs declared in `personal` scope are always pinned to the app's personal experience.</span></span> <span data-ttu-id="0f09e-267">Statische Registerkarten, die im Bereich deklariert `team` sind, werden derzeit nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="0f09e-267">Static tabs declared in the `team` scope are currently not supported.</span></span>

<span data-ttu-id="0f09e-268">Rendern sie Registerkarten mit adaptiven Karten, indem Sie `contentBotId` sie anstelle `contentUrl` des **staticTabs-Blocks** angeben.</span><span class="sxs-lookup"><span data-stu-id="0f09e-268">Render tabs with Adaptive Cards by specifying `contentBotId` instead of `contentUrl` in the **staticTabs** block.</span></span>

<span data-ttu-id="0f09e-269">Das Objekt ist ein Array (maximal 16 Elemente) mit allen Elementen des `object` Typs.</span><span class="sxs-lookup"><span data-stu-id="0f09e-269">The object is an array (maximum of 16 elements) with all elements of the type `object`.</span></span> <span data-ttu-id="0f09e-270">Dieser Block ist nur für Lösungen erforderlich, die eine statische Registerkartenlösung bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="0f09e-270">This block is required only for solutions that provide a static tab solution.</span></span>


|<span data-ttu-id="0f09e-271">Name</span><span class="sxs-lookup"><span data-stu-id="0f09e-271">Name</span></span>| <span data-ttu-id="0f09e-272">Typ</span><span class="sxs-lookup"><span data-stu-id="0f09e-272">Type</span></span>| <span data-ttu-id="0f09e-273">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="0f09e-273">Maximum size</span></span> | <span data-ttu-id="0f09e-274">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="0f09e-274">Required</span></span> | <span data-ttu-id="0f09e-275">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="0f09e-275">Description</span></span>|
|---|---|---|---|---|
|`entityId`|<span data-ttu-id="0f09e-276">String</span><span class="sxs-lookup"><span data-stu-id="0f09e-276">String</span></span>|<span data-ttu-id="0f09e-277">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="0f09e-277">64 characters</span></span>|<span data-ttu-id="0f09e-278">✔</span><span class="sxs-lookup"><span data-stu-id="0f09e-278">✔</span></span>|<span data-ttu-id="0f09e-279">Ein eindeutiger Bezeichner für die Entität, die auf der Registerkarte angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="0f09e-279">A unique identifier for the entity that the tab displays.</span></span>|
|`name`|<span data-ttu-id="0f09e-280">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="0f09e-280">String</span></span>|<span data-ttu-id="0f09e-281">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="0f09e-281">128 characters</span></span>|<span data-ttu-id="0f09e-282">✔</span><span class="sxs-lookup"><span data-stu-id="0f09e-282">✔</span></span>|<span data-ttu-id="0f09e-283">Der Anzeigename der Registerkarte in der Kanalschnittstelle.</span><span class="sxs-lookup"><span data-stu-id="0f09e-283">The display name of the tab in the channel interface.</span></span>|
|`contentUrl`|<span data-ttu-id="0f09e-284">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="0f09e-284">String</span></span>|<span data-ttu-id="0f09e-285">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="0f09e-285">2048 characters</span></span>|<span data-ttu-id="0f09e-286">✔</span><span class="sxs-lookup"><span data-stu-id="0f09e-286">✔</span></span>|<span data-ttu-id="0f09e-287">Die https:// URL, die auf die Entitäts-UI verweist, die im Teams Canvas angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="0f09e-287">The https:// URL that points to the entity UI to be displayed in the Teams canvas.</span></span>|
|`contentBotId`|   | | | <span data-ttu-id="0f09e-288">Die Microsoft Teams App-ID, die für den Bot im Bot Framework-Portal angegeben ist.</span><span class="sxs-lookup"><span data-stu-id="0f09e-288">The Microsoft Teams app ID specified for the bot in the Bot Framework portal.</span></span> |
|`websiteUrl`|<span data-ttu-id="0f09e-289">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="0f09e-289">String</span></span>|<span data-ttu-id="0f09e-290">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="0f09e-290">2048 characters</span></span>||<span data-ttu-id="0f09e-291">Die https:// URL, um darauf hinzuweisen, ob sich ein Benutzer für die Anzeige in einem Browser entscheidet.</span><span class="sxs-lookup"><span data-stu-id="0f09e-291">The https:// URL to point at if a user opts to view in a browser.</span></span>|
|`scopes`|<span data-ttu-id="0f09e-292">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="0f09e-292">Array of enum</span></span>|<span data-ttu-id="0f09e-293">1</span><span class="sxs-lookup"><span data-stu-id="0f09e-293">1</span></span>|<span data-ttu-id="0f09e-294">✔</span><span class="sxs-lookup"><span data-stu-id="0f09e-294">✔</span></span>|<span data-ttu-id="0f09e-295">Derzeit unterstützen statische Registerkarten nur den `personal` Bereich, was bedeutet, dass sie nur als Teil der persönlichen Benutzeroberfläche bereitgestellt werden können.</span><span class="sxs-lookup"><span data-stu-id="0f09e-295">Currently, static tabs support only the `personal` scope, which means it can be provisioned only as part of the personal experience.</span></span>|

## <a name="bots"></a><span data-ttu-id="0f09e-296">Bots</span><span class="sxs-lookup"><span data-stu-id="0f09e-296">bots</span></span>

<span data-ttu-id="0f09e-297">**Optional**</span><span class="sxs-lookup"><span data-stu-id="0f09e-297">**Optional**</span></span>

<span data-ttu-id="0f09e-298">Definiert eine Bot-Lösung zusammen mit optionalen Informationen wie Standardbefehlseigenschaften.</span><span class="sxs-lookup"><span data-stu-id="0f09e-298">Defines a bot solution, along with optional information such as default command properties.</span></span>

<span data-ttu-id="0f09e-299">Das Objekt ist ein Array (maximal 1 Element &mdash; ist derzeit nur ein Bot pro App zulässig) mit allen Elementen des `object` Typs.</span><span class="sxs-lookup"><span data-stu-id="0f09e-299">The object is an array (maximum of only 1 element&mdash;currently only one bot is allowed per app) with all elements of the type `object`.</span></span> <span data-ttu-id="0f09e-300">Dieser Block ist nur für Lösungen erforderlich, die eine Bot-Erfahrung bieten.</span><span class="sxs-lookup"><span data-stu-id="0f09e-300">This block is required only for solutions that provide a bot experience.</span></span>

|<span data-ttu-id="0f09e-301">Name</span><span class="sxs-lookup"><span data-stu-id="0f09e-301">Name</span></span>| <span data-ttu-id="0f09e-302">Typ</span><span class="sxs-lookup"><span data-stu-id="0f09e-302">Type</span></span>| <span data-ttu-id="0f09e-303">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="0f09e-303">Maximum size</span></span> | <span data-ttu-id="0f09e-304">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="0f09e-304">Required</span></span> | <span data-ttu-id="0f09e-305">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="0f09e-305">Description</span></span>|
|---|---|---|---|---|
|`botId`|<span data-ttu-id="0f09e-306">String</span><span class="sxs-lookup"><span data-stu-id="0f09e-306">String</span></span>|<span data-ttu-id="0f09e-307">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="0f09e-307">64 characters</span></span>|<span data-ttu-id="0f09e-308">✔</span><span class="sxs-lookup"><span data-stu-id="0f09e-308">✔</span></span>|<span data-ttu-id="0f09e-309">Die eindeutige Microsoft-App-ID für den Bot, wie bei Bot Framework registriert.</span><span class="sxs-lookup"><span data-stu-id="0f09e-309">The unique Microsoft app ID for the bot as registered with the Bot Framework.</span></span> <span data-ttu-id="0f09e-310">Dies kann durchaus mit der gesamten [App-ID](#id)übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="0f09e-310">This may well be the same as the overall [app ID](#id).</span></span>|
|`needsChannelSelector`|<span data-ttu-id="0f09e-311">Boolesch</span><span class="sxs-lookup"><span data-stu-id="0f09e-311">Boolean</span></span>|||<span data-ttu-id="0f09e-312">Beschreibt, ob der Bot einen Benutzerhinweis verwendet, um den Bot einem bestimmten Kanal hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="0f09e-312">Describes whether or not the bot utilizes a user hint to add the bot to a specific channel.</span></span> <span data-ttu-id="0f09e-313">Standard: `false`</span><span class="sxs-lookup"><span data-stu-id="0f09e-313">Default: `false`</span></span>|
|`isNotificationOnly`|<span data-ttu-id="0f09e-314">Boolesch</span><span class="sxs-lookup"><span data-stu-id="0f09e-314">Boolean</span></span>|||<span data-ttu-id="0f09e-315">Gibt an, ob ein Bot ein unidirektionaler Bot ausschließlich für Benachrichtigungen ist (im Gegensatz zu einem dialogorientierten Bot).</span><span class="sxs-lookup"><span data-stu-id="0f09e-315">Indicates whether a bot is a one-way, notification-only bot, as opposed to a conversational bot.</span></span> <span data-ttu-id="0f09e-316">Standard: `false`</span><span class="sxs-lookup"><span data-stu-id="0f09e-316">Default: `false`</span></span>|
|`supportsFiles`|<span data-ttu-id="0f09e-317">Boolesch</span><span class="sxs-lookup"><span data-stu-id="0f09e-317">Boolean</span></span>|||<span data-ttu-id="0f09e-318">Gibt an, ob der Bot die Möglichkeit zum Hochladen/Herunterladen von Dateien in persönliche Chats unterstützt.</span><span class="sxs-lookup"><span data-stu-id="0f09e-318">Indicates whether the bot supports the ability to upload/download files in personal chat.</span></span> <span data-ttu-id="0f09e-319">Standard: `false`</span><span class="sxs-lookup"><span data-stu-id="0f09e-319">Default: `false`</span></span>|
|`scopes`|<span data-ttu-id="0f09e-320">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="0f09e-320">Array of enum</span></span>|<span data-ttu-id="0f09e-321">3</span><span class="sxs-lookup"><span data-stu-id="0f09e-321">3</span></span>|<span data-ttu-id="0f09e-322">✔</span><span class="sxs-lookup"><span data-stu-id="0f09e-322">✔</span></span>|<span data-ttu-id="0f09e-323">Gibt an, ob der Bot eine Umgebung im Kontext eines Kanals in einem `team` oder Gruppenchat (`groupchat`) ist, oder aber eine Umgebung einzig für einen bestimmten Benutzer (`personal`).</span><span class="sxs-lookup"><span data-stu-id="0f09e-323">Specifies whether the bot offers an experience in the context of a channel in a `team`, in a group chat (`groupchat`), or an experience scoped to an individual user alone (`personal`).</span></span> <span data-ttu-id="0f09e-324">Diese Optionen sind nicht exklusiv.</span><span class="sxs-lookup"><span data-stu-id="0f09e-324">These options are non-exclusive.</span></span>|

### <a name="botscommandlists"></a><span data-ttu-id="0f09e-325">bots.commandLists</span><span class="sxs-lookup"><span data-stu-id="0f09e-325">bots.commandLists</span></span>

<span data-ttu-id="0f09e-326">Eine optionale Liste von Befehlen, die Ihr Bot Benutzern empfehlen kann.</span><span class="sxs-lookup"><span data-stu-id="0f09e-326">An optional list of commands that your bot can recommend to users.</span></span> <span data-ttu-id="0f09e-327">Das Objekt ist ein Array (maximal 2 Elemente) mit allen Elementen des `object` Typs. Sie müssen eine separate Befehlsliste für jeden Bereich definieren, den Ihr Bot unterstützt.</span><span class="sxs-lookup"><span data-stu-id="0f09e-327">The object is an array (maximum of 2 elements) with all elements of type `object`; you must define a separate command list for each scope that your bot supports.</span></span> <span data-ttu-id="0f09e-328">Weitere Informationen finden Sie unter [Bot-Menüs.](~/bots/how-to/create-a-bot-commands-menu.md)</span><span class="sxs-lookup"><span data-stu-id="0f09e-328">For more information, see [Bot menus](~/bots/how-to/create-a-bot-commands-menu.md).</span></span>

|<span data-ttu-id="0f09e-329">Name</span><span class="sxs-lookup"><span data-stu-id="0f09e-329">Name</span></span>| <span data-ttu-id="0f09e-330">Typ</span><span class="sxs-lookup"><span data-stu-id="0f09e-330">Type</span></span>| <span data-ttu-id="0f09e-331">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="0f09e-331">Maximum size</span></span> | <span data-ttu-id="0f09e-332">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="0f09e-332">Required</span></span> | <span data-ttu-id="0f09e-333">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="0f09e-333">Description</span></span>|
|---|---|---|---|---|
|`items.scopes`|<span data-ttu-id="0f09e-334">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="0f09e-334">array of enum</span></span>|<span data-ttu-id="0f09e-335">3</span><span class="sxs-lookup"><span data-stu-id="0f09e-335">3</span></span>|<span data-ttu-id="0f09e-336">✔</span><span class="sxs-lookup"><span data-stu-id="0f09e-336">✔</span></span>|<span data-ttu-id="0f09e-337">Gibt den Bereich an, für den die Befehlsliste gültig ist.</span><span class="sxs-lookup"><span data-stu-id="0f09e-337">Specifies the scope for which the command list is valid.</span></span> <span data-ttu-id="0f09e-338">Mögliche Optionen sind `team`, `personal` und `groupchat`.</span><span class="sxs-lookup"><span data-stu-id="0f09e-338">Options are `team`, `personal`, and `groupchat`.</span></span>|
|`items.commands`|<span data-ttu-id="0f09e-339">Array von Objekten</span><span class="sxs-lookup"><span data-stu-id="0f09e-339">array of objects</span></span>|<span data-ttu-id="0f09e-340">10</span><span class="sxs-lookup"><span data-stu-id="0f09e-340">10</span></span>|<span data-ttu-id="0f09e-341">✔</span><span class="sxs-lookup"><span data-stu-id="0f09e-341">✔</span></span>|<span data-ttu-id="0f09e-342">Ein Array von Befehlen, die der Bot unterstützt:</span><span class="sxs-lookup"><span data-stu-id="0f09e-342">An array of commands the bot supports:</span></span><br><span data-ttu-id="0f09e-343">`title`: der Bot-Befehlsname (Zeichenfolge, 32).</span><span class="sxs-lookup"><span data-stu-id="0f09e-343">`title`: the bot command name (string, 32).</span></span><br><span data-ttu-id="0f09e-344">`description`: eine einfache Beschreibung oder ein Beispiel für die Befehlssyntax und ihr Argument (Zeichenfolge, 128).</span><span class="sxs-lookup"><span data-stu-id="0f09e-344">`description`: a simple description or example of the command syntax and its argument (string, 128).</span></span>|

## <a name="connectors"></a><span data-ttu-id="0f09e-345">Steckverbinder</span><span class="sxs-lookup"><span data-stu-id="0f09e-345">connectors</span></span>

<span data-ttu-id="0f09e-346">**Optional**</span><span class="sxs-lookup"><span data-stu-id="0f09e-346">**Optional**</span></span>

<span data-ttu-id="0f09e-347">Der `connectors` Block definiert einen Office 365 Connector für die App.</span><span class="sxs-lookup"><span data-stu-id="0f09e-347">The `connectors` block defines an Office 365 Connector for the app.</span></span>

<span data-ttu-id="0f09e-348">Das Objekt ist ein Array (maximal 1 Element) mit allen Elementen des Typs `object` .</span><span class="sxs-lookup"><span data-stu-id="0f09e-348">The object is an array (maximum of 1 element) with all elements of type `object`.</span></span> <span data-ttu-id="0f09e-349">Dieser Block ist nur für Lösungen erforderlich, die einen Connector bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="0f09e-349">This block is required only for solutions that provide a Connector.</span></span>

|<span data-ttu-id="0f09e-350">Name</span><span class="sxs-lookup"><span data-stu-id="0f09e-350">Name</span></span>| <span data-ttu-id="0f09e-351">Typ</span><span class="sxs-lookup"><span data-stu-id="0f09e-351">Type</span></span>| <span data-ttu-id="0f09e-352">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="0f09e-352">Maximum size</span></span> | <span data-ttu-id="0f09e-353">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="0f09e-353">Required</span></span> | <span data-ttu-id="0f09e-354">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="0f09e-354">Description</span></span>|
|---|---|---|---|---|
|`configurationUrl`|<span data-ttu-id="0f09e-355">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="0f09e-355">String</span></span>|<span data-ttu-id="0f09e-356">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="0f09e-356">2048 characters</span></span>|<span data-ttu-id="0f09e-357">✔</span><span class="sxs-lookup"><span data-stu-id="0f09e-357">✔</span></span>|<span data-ttu-id="0f09e-358">Die https:// URL, die beim Konfigurieren des Connectors verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="0f09e-358">The https:// URL to use when configuring the connector.</span></span>|
|`connectorId`|<span data-ttu-id="0f09e-359">String</span><span class="sxs-lookup"><span data-stu-id="0f09e-359">String</span></span>|<span data-ttu-id="0f09e-360">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="0f09e-360">64 characters</span></span>|<span data-ttu-id="0f09e-361">✔</span><span class="sxs-lookup"><span data-stu-id="0f09e-361">✔</span></span>|<span data-ttu-id="0f09e-362">Ein eindeutiger Bezeichner für den Connector, der seiner ID im [Connectors Developer Dashboard](https://aka.ms/connectorsdashboard)entspricht.</span><span class="sxs-lookup"><span data-stu-id="0f09e-362">A unique identifier for the Connector that matches its ID in the [Connectors Developer Dashboard](https://aka.ms/connectorsdashboard).</span></span>|
|`scopes`|<span data-ttu-id="0f09e-363">Array von Enumerationen</span><span class="sxs-lookup"><span data-stu-id="0f09e-363">Array of enum</span></span>|<span data-ttu-id="0f09e-364">1</span><span class="sxs-lookup"><span data-stu-id="0f09e-364">1</span></span>|<span data-ttu-id="0f09e-365">✔</span><span class="sxs-lookup"><span data-stu-id="0f09e-365">✔</span></span>|<span data-ttu-id="0f09e-366">Gibt an, ob der Connector eine Erfahrung im Kontext eines Kanals in einem oder `team` eine Benutzeroberfläche bietet, die auf einen einzelnen Benutzer beschränkt ist ( `personal` ).</span><span class="sxs-lookup"><span data-stu-id="0f09e-366">Specifies whether the Connector offers an experience in the context of a channel in a `team`, or an experience scoped to an individual user alone (`personal`).</span></span> <span data-ttu-id="0f09e-367">Derzeit wird nur der `team` Bereich unterstützt.</span><span class="sxs-lookup"><span data-stu-id="0f09e-367">Currently, only the `team` scope is supported.</span></span>|

## <a name="composeextensions"></a><span data-ttu-id="0f09e-368">composeExtensions</span><span class="sxs-lookup"><span data-stu-id="0f09e-368">composeExtensions</span></span>

<span data-ttu-id="0f09e-369">**Optional**</span><span class="sxs-lookup"><span data-stu-id="0f09e-369">**Optional**</span></span>

<span data-ttu-id="0f09e-370">Definiert eine Messaging-Erweiterung für die App.</span><span class="sxs-lookup"><span data-stu-id="0f09e-370">Defines a messaging extension for the app.</span></span>

> [!NOTE]
> <span data-ttu-id="0f09e-371">Der Name des Features wurde im November 2017 von "Erstellerweiterung" in "Messaging-Erweiterung" geändert, aber der Manifestname bleibt unverändert, sodass vorhandene Erweiterungen weiterhin funktionieren.</span><span class="sxs-lookup"><span data-stu-id="0f09e-371">The name of the feature was changed from "compose extension" to "messaging extension" in November, 2017, but the manifest name remains the same so that existing extensions continue to function.</span></span>

<span data-ttu-id="0f09e-372">Das Objekt ist ein Array (maximal 1 Element) mit allen Elementen des Typs `object` .</span><span class="sxs-lookup"><span data-stu-id="0f09e-372">The object is an array (maximum of 1 element) with all elements of type `object`.</span></span> <span data-ttu-id="0f09e-373">Dieser Block ist nur für Lösungen erforderlich, die eine Messaging-Erweiterung bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="0f09e-373">This block is required only for solutions that provide a messaging extension.</span></span>

|<span data-ttu-id="0f09e-374">Name</span><span class="sxs-lookup"><span data-stu-id="0f09e-374">Name</span></span>| <span data-ttu-id="0f09e-375">Typ</span><span class="sxs-lookup"><span data-stu-id="0f09e-375">Type</span></span> | <span data-ttu-id="0f09e-376">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="0f09e-376">Maximum Size</span></span> | <span data-ttu-id="0f09e-377">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="0f09e-377">Required</span></span> | <span data-ttu-id="0f09e-378">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="0f09e-378">Description</span></span>|
|---|---|---|---|---|
|`botId`|<span data-ttu-id="0f09e-379">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="0f09e-379">String</span></span>|<span data-ttu-id="0f09e-380">64</span><span class="sxs-lookup"><span data-stu-id="0f09e-380">64</span></span>|<span data-ttu-id="0f09e-381">✔</span><span class="sxs-lookup"><span data-stu-id="0f09e-381">✔</span></span>|<span data-ttu-id="0f09e-382">Die eindeutige Microsoft-App-ID für den Bot, der die Messaging-Erweiterung unterstützt, wie beim Bot Framework registriert.</span><span class="sxs-lookup"><span data-stu-id="0f09e-382">The unique Microsoft app ID for the bot that backs the messaging extension, as registered with the Bot Framework.</span></span> <span data-ttu-id="0f09e-383">Dies kann durchaus mit der gesamten [App-ID](#id)übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="0f09e-383">This may well be the same as the overall [app ID](#id).</span></span>|
|`canUpdateConfiguration`|<span data-ttu-id="0f09e-384">Boolesch</span><span class="sxs-lookup"><span data-stu-id="0f09e-384">Boolean</span></span>|||<span data-ttu-id="0f09e-385">Ein Wert, der angibt, ob die Konfiguration einer Messaging-Erweiterung vom Benutzer aktualisiert werden kann.</span><span class="sxs-lookup"><span data-stu-id="0f09e-385">A value indicating whether the configuration of a messaging extension can be updated by the user.</span></span> <span data-ttu-id="0f09e-386">Der Standardwert lautet `false`.</span><span class="sxs-lookup"><span data-stu-id="0f09e-386">The default is `false`.</span></span>|
|`commands`|<span data-ttu-id="0f09e-387">Array des Objekts</span><span class="sxs-lookup"><span data-stu-id="0f09e-387">Array of object</span></span>|<span data-ttu-id="0f09e-388">10</span><span class="sxs-lookup"><span data-stu-id="0f09e-388">10</span></span>|<span data-ttu-id="0f09e-389">✔</span><span class="sxs-lookup"><span data-stu-id="0f09e-389">✔</span></span>|<span data-ttu-id="0f09e-390">Array von Befehlen, die von der Messaging-Erweiterung unterstützt werden</span><span class="sxs-lookup"><span data-stu-id="0f09e-390">Array of commands the messaging extension supports</span></span>|

### <a name="composeextensionscommands"></a><span data-ttu-id="0f09e-391">composeExtensions.commands</span><span class="sxs-lookup"><span data-stu-id="0f09e-391">composeExtensions.commands</span></span>

<span data-ttu-id="0f09e-392">Ihre Messaging-Erweiterung sollte einen oder mehrere Befehle deklarieren.</span><span class="sxs-lookup"><span data-stu-id="0f09e-392">Your messaging extension should declare one or more commands.</span></span> <span data-ttu-id="0f09e-393">Jeder Befehl wird in Microsoft Teams als potenzielle Interaktion vom UI-basierten Einstiegspunkt angezeigt.</span><span class="sxs-lookup"><span data-stu-id="0f09e-393">Each command appears in Microsoft Teams as a potential interaction from the UI-based entry point.</span></span> <span data-ttu-id="0f09e-394">Es gibt maximal 10 Befehle.</span><span class="sxs-lookup"><span data-stu-id="0f09e-394">There is a maximum of 10 commands.</span></span>

<span data-ttu-id="0f09e-395">Jedes Befehlselement ist ein Objekt mit der folgenden Struktur:</span><span class="sxs-lookup"><span data-stu-id="0f09e-395">Each command item is an object with the following structure:</span></span>

|<span data-ttu-id="0f09e-396">Name</span><span class="sxs-lookup"><span data-stu-id="0f09e-396">Name</span></span>| <span data-ttu-id="0f09e-397">Typ</span><span class="sxs-lookup"><span data-stu-id="0f09e-397">Type</span></span>| <span data-ttu-id="0f09e-398">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="0f09e-398">Maximum size</span></span> | <span data-ttu-id="0f09e-399">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="0f09e-399">Required</span></span> | <span data-ttu-id="0f09e-400">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="0f09e-400">Description</span></span>|
|---|---|---|---|---|
|`id`|<span data-ttu-id="0f09e-401">String</span><span class="sxs-lookup"><span data-stu-id="0f09e-401">String</span></span>|<span data-ttu-id="0f09e-402">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="0f09e-402">64 characters</span></span>|<span data-ttu-id="0f09e-403">✔</span><span class="sxs-lookup"><span data-stu-id="0f09e-403">✔</span></span>|<span data-ttu-id="0f09e-404">Die ID für den Befehl.</span><span class="sxs-lookup"><span data-stu-id="0f09e-404">The ID for the command.</span></span>|
|`type`|<span data-ttu-id="0f09e-405">String</span><span class="sxs-lookup"><span data-stu-id="0f09e-405">String</span></span>|<span data-ttu-id="0f09e-406">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="0f09e-406">64 characters</span></span>||<span data-ttu-id="0f09e-407">Typ des Befehls.</span><span class="sxs-lookup"><span data-stu-id="0f09e-407">Type of the command.</span></span> <span data-ttu-id="0f09e-408">Eine von `query` oder `action` .</span><span class="sxs-lookup"><span data-stu-id="0f09e-408">One of `query` or `action`.</span></span> <span data-ttu-id="0f09e-409">Standard: `query`</span><span class="sxs-lookup"><span data-stu-id="0f09e-409">Default: `query`</span></span>|
|`title`|<span data-ttu-id="0f09e-410">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="0f09e-410">String</span></span>|<span data-ttu-id="0f09e-411">32 Zeichen</span><span class="sxs-lookup"><span data-stu-id="0f09e-411">32 characters</span></span>|<span data-ttu-id="0f09e-412">✔</span><span class="sxs-lookup"><span data-stu-id="0f09e-412">✔</span></span>|<span data-ttu-id="0f09e-413">Der benutzerfreundliche Befehlsname.</span><span class="sxs-lookup"><span data-stu-id="0f09e-413">The user-friendly command name.</span></span>|
|`description`|<span data-ttu-id="0f09e-414">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="0f09e-414">String</span></span>|<span data-ttu-id="0f09e-415">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="0f09e-415">128 characters</span></span>||<span data-ttu-id="0f09e-416">Die Beschreibung, die Benutzern angezeigt wird, um den Zweck dieses Befehls anzugeben.</span><span class="sxs-lookup"><span data-stu-id="0f09e-416">The description that appears to users to indicate the purpose of this command.</span></span>|
|`initialRun`|<span data-ttu-id="0f09e-417">Boolesch</span><span class="sxs-lookup"><span data-stu-id="0f09e-417">Boolean</span></span>|||<span data-ttu-id="0f09e-418">Ein boolescher Wert, der angibt, ob der Befehl anfänglich ohne Parameter ausgeführt werden soll.</span><span class="sxs-lookup"><span data-stu-id="0f09e-418">A Boolean value that indicates whether the command should be run initially with no parameters.</span></span> <span data-ttu-id="0f09e-419">Standard: `false`</span><span class="sxs-lookup"><span data-stu-id="0f09e-419">Default: `false`</span></span>|
|`context`|<span data-ttu-id="0f09e-420">Array von Zeichenfolgen</span><span class="sxs-lookup"><span data-stu-id="0f09e-420">Array of Strings</span></span>|<span data-ttu-id="0f09e-421">3</span><span class="sxs-lookup"><span data-stu-id="0f09e-421">3</span></span>||<span data-ttu-id="0f09e-422">Definiert, von wo aus die Nachrichtenerweiterung aufgerufen werden kann.</span><span class="sxs-lookup"><span data-stu-id="0f09e-422">Defines where the message extension can be invoked from.</span></span> <span data-ttu-id="0f09e-423">Eine beliebige Kombination von `compose` , `commandBox` , `message` .</span><span class="sxs-lookup"><span data-stu-id="0f09e-423">Any combination of `compose`, `commandBox`, `message`.</span></span> <span data-ttu-id="0f09e-424">Der Standardwert ist `["compose", "commandBox"]`</span><span class="sxs-lookup"><span data-stu-id="0f09e-424">Default is `["compose", "commandBox"]`</span></span>|
|`fetchTask`|<span data-ttu-id="0f09e-425">Boolesch</span><span class="sxs-lookup"><span data-stu-id="0f09e-425">Boolean</span></span>|||<span data-ttu-id="0f09e-426">Ein boolescher Wert, der angibt, ob das Aufgabenmodul dynamisch abgerufen werden soll.</span><span class="sxs-lookup"><span data-stu-id="0f09e-426">A boolean value that indicates if it should fetch the task module dynamically.</span></span>|
|`taskInfo`|<span data-ttu-id="0f09e-427">Objekt</span><span class="sxs-lookup"><span data-stu-id="0f09e-427">Object</span></span>|||<span data-ttu-id="0f09e-428">Geben Sie das Aufgabenmodul an, das vorab geladen werden soll, wenn Sie einen Messaging-Erweiterungsbefehl verwenden.</span><span class="sxs-lookup"><span data-stu-id="0f09e-428">Specify the task module to preload when using a messaging extension command.</span></span>|
|`taskInfo.title`|<span data-ttu-id="0f09e-429">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="0f09e-429">String</span></span>|<span data-ttu-id="0f09e-430">64</span><span class="sxs-lookup"><span data-stu-id="0f09e-430">64</span></span>||<span data-ttu-id="0f09e-431">Titel des ersten Dialogfelds.</span><span class="sxs-lookup"><span data-stu-id="0f09e-431">Initial dialog title.</span></span>|
|`taskInfo.width`|<span data-ttu-id="0f09e-432">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="0f09e-432">String</span></span>|||<span data-ttu-id="0f09e-433">Dialogbreite – entweder eine Zahl in Pixeln oder ein Standardlayout, z. B. "groß", "mittel" oder "klein".</span><span class="sxs-lookup"><span data-stu-id="0f09e-433">Dialog width - either a number in pixels or default layout such as 'large', 'medium', or 'small'.</span></span>|
|`taskInfo.height`|<span data-ttu-id="0f09e-434">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="0f09e-434">String</span></span>|||<span data-ttu-id="0f09e-435">Dialoghöhe – entweder eine Zahl in Pixeln oder ein Standardlayout, z. B. "groß", "mittel" oder "klein".</span><span class="sxs-lookup"><span data-stu-id="0f09e-435">Dialog height - either a number in pixels or default layout such as 'large', 'medium', or 'small'.</span></span>|
|`taskInfo.url`|<span data-ttu-id="0f09e-436">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="0f09e-436">String</span></span>|||<span data-ttu-id="0f09e-437">Ursprüngliche Webansichts-URL.</span><span class="sxs-lookup"><span data-stu-id="0f09e-437">Initial webview URL.</span></span>|
|`messageHandlers`|<span data-ttu-id="0f09e-438">Array von Objekten</span><span class="sxs-lookup"><span data-stu-id="0f09e-438">Array of Objects</span></span>|<span data-ttu-id="0f09e-439">5 </span><span class="sxs-lookup"><span data-stu-id="0f09e-439">5</span></span>||<span data-ttu-id="0f09e-440">Eine Liste von Handlern, mit denen Apps aufgerufen werden können, wenn bestimmte Bedingungen erfüllt sind.</span><span class="sxs-lookup"><span data-stu-id="0f09e-440">A list of handlers that allow apps to be invoked when certain conditions are met.</span></span> <span data-ttu-id="0f09e-441">Domänen müssen auch in aufgeführt `validDomains` werden.</span><span class="sxs-lookup"><span data-stu-id="0f09e-441">Domains must also be listed in `validDomains`.</span></span>|
|`messageHandlers.type`|<span data-ttu-id="0f09e-442">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="0f09e-442">String</span></span>|||<span data-ttu-id="0f09e-443">Der Typ des Nachrichtenhandlers.</span><span class="sxs-lookup"><span data-stu-id="0f09e-443">The type of message handler.</span></span> <span data-ttu-id="0f09e-444">Muss `"link"` sein.</span><span class="sxs-lookup"><span data-stu-id="0f09e-444">Must be `"link"`.</span></span>|
|`messageHandlers.value.domains`|<span data-ttu-id="0f09e-445">Array von Zeichenfolgen</span><span class="sxs-lookup"><span data-stu-id="0f09e-445">Array of Strings</span></span>|||<span data-ttu-id="0f09e-446">Array von Domänen, für die sich der Linknachrichtenhandler registrieren kann.</span><span class="sxs-lookup"><span data-stu-id="0f09e-446">Array of domains that the link message handler can register for.</span></span>|
|`parameters`|<span data-ttu-id="0f09e-447">Array des Objekts</span><span class="sxs-lookup"><span data-stu-id="0f09e-447">Array of object</span></span>|<span data-ttu-id="0f09e-448">5 </span><span class="sxs-lookup"><span data-stu-id="0f09e-448">5</span></span>|<span data-ttu-id="0f09e-449">✔</span><span class="sxs-lookup"><span data-stu-id="0f09e-449">✔</span></span>|<span data-ttu-id="0f09e-450">Die Liste der Parameter, die der Befehl verwendet.</span><span class="sxs-lookup"><span data-stu-id="0f09e-450">The list of parameters the command takes.</span></span> <span data-ttu-id="0f09e-451">Minimum: 1; Maximum: 5</span><span class="sxs-lookup"><span data-stu-id="0f09e-451">Minimum: 1; maximum: 5</span></span>|
|`parameter.name`|<span data-ttu-id="0f09e-452">String</span><span class="sxs-lookup"><span data-stu-id="0f09e-452">String</span></span>|<span data-ttu-id="0f09e-453">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="0f09e-453">64 characters</span></span>|<span data-ttu-id="0f09e-454">✔</span><span class="sxs-lookup"><span data-stu-id="0f09e-454">✔</span></span>|<span data-ttu-id="0f09e-455">Der Name des Parameters, wie er im Client angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="0f09e-455">The name of the parameter as it appears in the client.</span></span> <span data-ttu-id="0f09e-456">Dies ist in der Benutzeranforderung enthalten.</span><span class="sxs-lookup"><span data-stu-id="0f09e-456">This is included in the user request.</span></span>|
|`parameter.title`|<span data-ttu-id="0f09e-457">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="0f09e-457">String</span></span>|<span data-ttu-id="0f09e-458">32 Zeichen</span><span class="sxs-lookup"><span data-stu-id="0f09e-458">32 characters</span></span>|<span data-ttu-id="0f09e-459">✔</span><span class="sxs-lookup"><span data-stu-id="0f09e-459">✔</span></span>|<span data-ttu-id="0f09e-460">Benutzerfreundlicher Titel für den Parameter.</span><span class="sxs-lookup"><span data-stu-id="0f09e-460">User-friendly title for the parameter.</span></span>|
|`parameter.description`|<span data-ttu-id="0f09e-461">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="0f09e-461">String</span></span>|<span data-ttu-id="0f09e-462">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="0f09e-462">128 characters</span></span>||<span data-ttu-id="0f09e-463">Benutzerfreundliche Zeichenfolge, die den Zweck dieses Parameters beschreibt.</span><span class="sxs-lookup"><span data-stu-id="0f09e-463">User-friendly string that describes this parameter’s purpose.</span></span>|
|`parameter.inputType`|<span data-ttu-id="0f09e-464">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="0f09e-464">String</span></span>|<span data-ttu-id="0f09e-465">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="0f09e-465">128 characters</span></span>||<span data-ttu-id="0f09e-466">Definiert den Typ des Steuerelements, das in einem Aufgabenmodul für angezeigt `fetchTask: true` wird.</span><span class="sxs-lookup"><span data-stu-id="0f09e-466">Defines the type of control displayed on a task module for `fetchTask: true`.</span></span> <span data-ttu-id="0f09e-467">Einer von `text` , , , , , , `textarea` `number` `date` `time` `toggle` `choiceset` .</span><span class="sxs-lookup"><span data-stu-id="0f09e-467">One of `text`, `textarea`, `number`, `date`, `time`, `toggle`, `choiceset`.</span></span>|
|`parameter.choices`|<span data-ttu-id="0f09e-468">Array von Objekten</span><span class="sxs-lookup"><span data-stu-id="0f09e-468">Array of Objects</span></span>|<span data-ttu-id="0f09e-469">10</span><span class="sxs-lookup"><span data-stu-id="0f09e-469">10</span></span>||<span data-ttu-id="0f09e-470">Die Auswahloptionen für die `choiceset` .</span><span class="sxs-lookup"><span data-stu-id="0f09e-470">The choice options for the `choiceset`.</span></span> <span data-ttu-id="0f09e-471">Wird nur verwendet, wenn `parameter.inputType` `choiceset` .</span><span class="sxs-lookup"><span data-stu-id="0f09e-471">Use only when `parameter.inputType` is `choiceset`.</span></span>|
|`parameter.choices.title`|<span data-ttu-id="0f09e-472">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="0f09e-472">String</span></span>|<span data-ttu-id="0f09e-473">128</span><span class="sxs-lookup"><span data-stu-id="0f09e-473">128</span></span>||<span data-ttu-id="0f09e-474">Titel der Wahl.</span><span class="sxs-lookup"><span data-stu-id="0f09e-474">Title of the choice.</span></span>|
|`parameter.choices.value`|<span data-ttu-id="0f09e-475">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="0f09e-475">String</span></span>|<span data-ttu-id="0f09e-476">512</span><span class="sxs-lookup"><span data-stu-id="0f09e-476">512</span></span>||<span data-ttu-id="0f09e-477">Value of the choice.</span><span class="sxs-lookup"><span data-stu-id="0f09e-477">Value of the choice.</span></span>|

## <a name="permissions"></a><span data-ttu-id="0f09e-478">Berechtigungen</span><span class="sxs-lookup"><span data-stu-id="0f09e-478">permissions</span></span>

<span data-ttu-id="0f09e-479">**Optional**</span><span class="sxs-lookup"><span data-stu-id="0f09e-479">**Optional**</span></span>

<span data-ttu-id="0f09e-480">Ein `string` Array, das angibt, welche Berechtigungen die App anfordert, wodurch Endbenutzer wissen, wie die Erweiterung ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="0f09e-480">An array of `string` which specifies which permissions the app requests, which lets end users know how the extension will perform.</span></span> <span data-ttu-id="0f09e-481">Die folgenden Optionen sind nicht exklusiv:</span><span class="sxs-lookup"><span data-stu-id="0f09e-481">The following options are non-exclusive:</span></span>

* <span data-ttu-id="0f09e-482">`identity`&emsp;Erfordert Benutzeridentitätsinformationen.</span><span class="sxs-lookup"><span data-stu-id="0f09e-482">`identity` &emsp; Requires user identity information.</span></span>
* <span data-ttu-id="0f09e-483">`messageTeamMembers`&emsp;Erfordert die Berechtigung, direkte Nachrichten an Teammitglieder zu senden.</span><span class="sxs-lookup"><span data-stu-id="0f09e-483">`messageTeamMembers` &emsp; Requires permission to send direct messages to team members.</span></span>

<span data-ttu-id="0f09e-484">Wenn Sie diese Berechtigungen beim Aktualisieren Ihrer App ändern, wiederholen Ihre Benutzer den Zustimmungsprozess bei der ersten Ausführung der aktualisierten App.</span><span class="sxs-lookup"><span data-stu-id="0f09e-484">Changing these permissions when updating your app will cause your users to repeat the consent process the first time they run the updated app.</span></span>

## <a name="devicepermissions"></a><span data-ttu-id="0f09e-485">devicePermissions</span><span class="sxs-lookup"><span data-stu-id="0f09e-485">devicePermissions</span></span>

<span data-ttu-id="0f09e-486">**Optional** Array von Zeichenfolgen</span><span class="sxs-lookup"><span data-stu-id="0f09e-486">**Optional** Array of Strings</span></span>

<span data-ttu-id="0f09e-487">Gibt die systemeigenen Features auf dem Gerät eines Benutzers an, auf die Ihre App Zugriff anfordern kann.</span><span class="sxs-lookup"><span data-stu-id="0f09e-487">Specifies the native features on a user's device that your app may request access to.</span></span> <span data-ttu-id="0f09e-488">Mögliche Optionen sind:</span><span class="sxs-lookup"><span data-stu-id="0f09e-488">Options are:</span></span>

* `geolocation`
* `media`
* `notifications`
* `midi`
* `openExternal`

## <a name="validdomains"></a><span data-ttu-id="0f09e-489">validDomains</span><span class="sxs-lookup"><span data-stu-id="0f09e-489">validDomains</span></span>

<span data-ttu-id="0f09e-490">**Optional,** außer **erforderlich,** sofern angegeben</span><span class="sxs-lookup"><span data-stu-id="0f09e-490">**Optional**, except **Required** where noted</span></span>

<span data-ttu-id="0f09e-491">Eine Liste der gültigen Domänen, von denen die App erwartet, dass inhalte geladen werden.</span><span class="sxs-lookup"><span data-stu-id="0f09e-491">A list of valid domains from which the app expects to load any content.</span></span> <span data-ttu-id="0f09e-492">Domäneneinträge können Platzhalter enthalten, `*.example.com` z. B. .</span><span class="sxs-lookup"><span data-stu-id="0f09e-492">Domain listings can include wildcards, for example `*.example.com`.</span></span> <span data-ttu-id="0f09e-493">Dies entspricht genau einem Segment der Domäne. wenn Sie übereinstimmen `a.b.example.com` müssen, verwenden Sie `*.*.example.com` .</span><span class="sxs-lookup"><span data-stu-id="0f09e-493">This matches exactly one segment of the domain; if you need to match `a.b.example.com` then use `*.*.example.com`.</span></span> <span data-ttu-id="0f09e-494">Wenn Ihre Registerkartenkonfiguration oder Inhalts-UI zu einer anderen Domäne als der für die Registerkartenkonfiguration verwendeten navigieren muss, muss diese Domäne hier angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="0f09e-494">If your tab configuration or content UI needs to navigate to any other domain besides the one use for tab configuration, that domain must be specified here.</span></span>

<span data-ttu-id="0f09e-495">Es ist jedoch **nicht** erforderlich, die Domänen von Identitätsanbietern, die Sie unterstützen möchten, in Ihre App einzuschließen.</span><span class="sxs-lookup"><span data-stu-id="0f09e-495">It is **not** necessary to include the domains of identity providers you want to support in your app, however.</span></span> <span data-ttu-id="0f09e-496">Um sich beispielsweise mithilfe einer Google-ID zu authentifizieren, ist es erforderlich, zu accounts.google.com umzuleiten, sie sollten jedoch keine accounts.google.com in `validDomains[]` einschließen.</span><span class="sxs-lookup"><span data-stu-id="0f09e-496">For example, to authenticate using a Google ID, it's necessary to redirect to accounts.google.com, but you should not include accounts.google.com in `validDomains[]`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="0f09e-497">Fügen Sie keine Domänen hinzu, die sich außerhalb Ihres Steuerelements befinden, entweder direkt oder über Platzhalter.</span><span class="sxs-lookup"><span data-stu-id="0f09e-497">Do not add domains that are outside your control, either directly or via wildcards.</span></span> <span data-ttu-id="0f09e-498">Ist z. `yourapp.onmicrosoft.com` B. gültig, aber `*.onmicrosoft.com` nicht gültig.</span><span class="sxs-lookup"><span data-stu-id="0f09e-498">For example, `yourapp.onmicrosoft.com` is valid, but `*.onmicrosoft.com` is not valid.</span></span>

<span data-ttu-id="0f09e-499">Das Objekt ist ein Array mit allen Elementen des Typs `string` .</span><span class="sxs-lookup"><span data-stu-id="0f09e-499">The object is an array with all elements of the type `string`.</span></span>

## <a name="webapplicationinfo"></a><span data-ttu-id="0f09e-500">webApplicationInfo</span><span class="sxs-lookup"><span data-stu-id="0f09e-500">webApplicationInfo</span></span>

<span data-ttu-id="0f09e-501">**Optional**</span><span class="sxs-lookup"><span data-stu-id="0f09e-501">**Optional**</span></span>

<span data-ttu-id="0f09e-502">Geben Sie Ihre AAD-App-ID und Graph Informationen an, damit sich Benutzer nahtlos bei Ihrer AAD-App anmelden können.</span><span class="sxs-lookup"><span data-stu-id="0f09e-502">Specify your AAD App ID and Graph information to help users seamlessly sign into your AAD app.</span></span>

|<span data-ttu-id="0f09e-503">Name</span><span class="sxs-lookup"><span data-stu-id="0f09e-503">Name</span></span>| <span data-ttu-id="0f09e-504">Typ</span><span class="sxs-lookup"><span data-stu-id="0f09e-504">Type</span></span>| <span data-ttu-id="0f09e-505">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="0f09e-505">Maximum size</span></span> | <span data-ttu-id="0f09e-506">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="0f09e-506">Required</span></span> | <span data-ttu-id="0f09e-507">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="0f09e-507">Description</span></span>|
|---|---|---|---|---|
|`id`|<span data-ttu-id="0f09e-508">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="0f09e-508">String</span></span>|<span data-ttu-id="0f09e-509">36 Zeichen</span><span class="sxs-lookup"><span data-stu-id="0f09e-509">36 characters</span></span>|<span data-ttu-id="0f09e-510">✔</span><span class="sxs-lookup"><span data-stu-id="0f09e-510">✔</span></span>|<span data-ttu-id="0f09e-511">AAD-Anwendungs-ID der App.</span><span class="sxs-lookup"><span data-stu-id="0f09e-511">AAD application id of the app.</span></span> <span data-ttu-id="0f09e-512">Diese ID muss eine GUID sein.</span><span class="sxs-lookup"><span data-stu-id="0f09e-512">This id must be a GUID.</span></span>|
|`resource`|<span data-ttu-id="0f09e-513">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="0f09e-513">String</span></span>|<span data-ttu-id="0f09e-514">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="0f09e-514">2048 characters</span></span>|<span data-ttu-id="0f09e-515">✔</span><span class="sxs-lookup"><span data-stu-id="0f09e-515">✔</span></span>|<span data-ttu-id="0f09e-516">Ressourcen-URL der App zum Abrufen des Authentifizierungstokens für SSO.</span><span class="sxs-lookup"><span data-stu-id="0f09e-516">Resource url of app for acquiring auth token for SSO.</span></span>|
|`applicationPermissions`|<span data-ttu-id="0f09e-517">Array</span><span class="sxs-lookup"><span data-stu-id="0f09e-517">Array</span></span>|<span data-ttu-id="0f09e-518">Maximal 100 Elemente</span><span class="sxs-lookup"><span data-stu-id="0f09e-518">Maximum 100 items</span></span>|<span data-ttu-id="0f09e-519">✔</span><span class="sxs-lookup"><span data-stu-id="0f09e-519">✔</span></span>|<span data-ttu-id="0f09e-520">Ressourcenberechtigungen für die Anwendung.</span><span class="sxs-lookup"><span data-stu-id="0f09e-520">Resource permissions for application.</span></span>|

## <a name="configurableproperties"></a><span data-ttu-id="0f09e-521">configurableProperties</span><span class="sxs-lookup"><span data-stu-id="0f09e-521">configurableProperties</span></span>

<span data-ttu-id="0f09e-522">**Optional** – Array</span><span class="sxs-lookup"><span data-stu-id="0f09e-522">**Optional** - array</span></span>

<span data-ttu-id="0f09e-523">Der `configurableProperties` Block definiert die App-Eigenschaften, die Teams Administratoren anpassen können.</span><span class="sxs-lookup"><span data-stu-id="0f09e-523">The `configurableProperties` block defines the app properties that Teams admins can customize.</span></span> <span data-ttu-id="0f09e-524">Weitere Informationen finden Sie unter Aktivieren der [App-Anpassung.](~/concepts/design/enable-app-customization.md)</span><span class="sxs-lookup"><span data-stu-id="0f09e-524">For more information, see [enable app customization](~/concepts/design/enable-app-customization.md).</span></span>

> [!NOTE]
> <span data-ttu-id="0f09e-525">Es muss mindestens eine Eigenschaft definiert werden.</span><span class="sxs-lookup"><span data-stu-id="0f09e-525">A minimum of one property must be defined.</span></span> <span data-ttu-id="0f09e-526">Sie können maximal neun Eigenschaften in diesem Block definieren.</span><span class="sxs-lookup"><span data-stu-id="0f09e-526">You can define a maximum of nine properties in this block.</span></span>

<span data-ttu-id="0f09e-527">Sie können eine der folgenden Eigenschaften definieren:</span><span class="sxs-lookup"><span data-stu-id="0f09e-527">You can define any of the following properties:</span></span>

* <span data-ttu-id="0f09e-528">`name`: Der Anzeigename der App.</span><span class="sxs-lookup"><span data-stu-id="0f09e-528">`name`: The app's display name.</span></span>
* <span data-ttu-id="0f09e-529">`shortDescription`: Die kurze Beschreibung der App.</span><span class="sxs-lookup"><span data-stu-id="0f09e-529">`shortDescription`: The app's short description.</span></span>
* <span data-ttu-id="0f09e-530">`longDescription`: Die ausführliche Beschreibung der App.</span><span class="sxs-lookup"><span data-stu-id="0f09e-530">`longDescription`: The app's detailed description.</span></span>
* <span data-ttu-id="0f09e-531">`smallImageUrl`: Das Gliederungssymbol der App.</span><span class="sxs-lookup"><span data-stu-id="0f09e-531">`smallImageUrl`: The app's outline icon.</span></span>
* <span data-ttu-id="0f09e-532">`largeImageUrl`: Das Farbsymbol der App.</span><span class="sxs-lookup"><span data-stu-id="0f09e-532">`largeImageUrl`: The app's color icon.</span></span>
* <span data-ttu-id="0f09e-533">`accentColor`: Die Farbe, die in Verbindung mit und als Hintergrund für Ihre Gliederungssymbole verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="0f09e-533">`accentColor`: The color to use in conjunction with and as a background for your outline icons.</span></span>
* <span data-ttu-id="0f09e-534">`developerUrl`: Die HTTPS-URL der Website des Entwicklers.</span><span class="sxs-lookup"><span data-stu-id="0f09e-534">`developerUrl`: The HTTPS URL of the developer's website.</span></span>
* <span data-ttu-id="0f09e-535">`privacyUrl`: Die HTTPS-URL der Datenschutzrichtlinie des Entwicklers.</span><span class="sxs-lookup"><span data-stu-id="0f09e-535">`privacyUrl`: The HTTPS URL of the developer's privacy policy.</span></span>
* <span data-ttu-id="0f09e-536">`termsOfUseUrl`: Die HTTPS-URL der Nutzungsbedingungen des Entwicklers.</span><span class="sxs-lookup"><span data-stu-id="0f09e-536">`termsOfUseUrl`: The HTTPS URL of the developer's terms of use.</span></span>

## <a name="defaultinstallscope"></a><span data-ttu-id="0f09e-537">defaultInstallScope</span><span class="sxs-lookup"><span data-stu-id="0f09e-537">defaultInstallScope</span></span>

<span data-ttu-id="0f09e-538">**Optional** – Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="0f09e-538">**Optional** - string</span></span>

<span data-ttu-id="0f09e-539">Gibt den standardmäßig für diese App definierten Installationsumfang an.</span><span class="sxs-lookup"><span data-stu-id="0f09e-539">Specifies the install scope defined for this app by default.</span></span> <span data-ttu-id="0f09e-540">Der definierte Bereich ist die Option, die auf der Schaltfläche angezeigt wird, wenn ein Benutzer versucht, die App hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="0f09e-540">The defined scope will be the option displayed on the button when a user tries to add the app.</span></span> <span data-ttu-id="0f09e-541">Mögliche Optionen sind:</span><span class="sxs-lookup"><span data-stu-id="0f09e-541">Options are:</span></span>
* `personal`
* `team`
* `groupchat`
* `meetings`

## <a name="defaultgroupcapability"></a><span data-ttu-id="0f09e-542">defaultGroupCapability</span><span class="sxs-lookup"><span data-stu-id="0f09e-542">defaultGroupCapability</span></span>

<span data-ttu-id="0f09e-543">**Optional** – Objekt</span><span class="sxs-lookup"><span data-stu-id="0f09e-543">**Optional** - object</span></span>

<span data-ttu-id="0f09e-544">Wenn ein Gruppeninstallationsbereich ausgewählt ist, wird die Standardfunktion definiert, wenn der Benutzer die App installiert.</span><span class="sxs-lookup"><span data-stu-id="0f09e-544">When a group install scope is selected, it will define the default capability when the user installs the app.</span></span> <span data-ttu-id="0f09e-545">Mögliche Optionen sind:</span><span class="sxs-lookup"><span data-stu-id="0f09e-545">Options are:</span></span>
* `team`
* `groupchat`
* `meetings`
 
|<span data-ttu-id="0f09e-546">Name</span><span class="sxs-lookup"><span data-stu-id="0f09e-546">Name</span></span>| <span data-ttu-id="0f09e-547">Typ</span><span class="sxs-lookup"><span data-stu-id="0f09e-547">Type</span></span>| <span data-ttu-id="0f09e-548">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="0f09e-548">Maximum size</span></span> | <span data-ttu-id="0f09e-549">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="0f09e-549">Required</span></span> | <span data-ttu-id="0f09e-550">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="0f09e-550">Description</span></span>|
|---|---|---|---|---|
|`team`|<span data-ttu-id="0f09e-551">string</span><span class="sxs-lookup"><span data-stu-id="0f09e-551">string</span></span>|||<span data-ttu-id="0f09e-552">Wenn der ausgewählte Installationsbereich ausgewählt `team` ist, gibt dieses Feld die verfügbare Standardfunktion an.</span><span class="sxs-lookup"><span data-stu-id="0f09e-552">When the install scope selected is `team`, this field specifies the default capability available.</span></span> <span data-ttu-id="0f09e-553">Optionen: `tab` `bot` oder `connector` .</span><span class="sxs-lookup"><span data-stu-id="0f09e-553">Options: `tab`, `bot`, or `connector`.</span></span>|
|`groupchat`|<span data-ttu-id="0f09e-554">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="0f09e-554">string</span></span>|||<span data-ttu-id="0f09e-555">Wenn der ausgewählte Installationsbereich ausgewählt `groupchat` ist, gibt dieses Feld die verfügbare Standardfunktion an.</span><span class="sxs-lookup"><span data-stu-id="0f09e-555">When the install scope selected is `groupchat`, this field specifies the default capability available.</span></span> <span data-ttu-id="0f09e-556">Optionen: `tab` `bot` oder `connector` .</span><span class="sxs-lookup"><span data-stu-id="0f09e-556">Options: `tab`, `bot`, or `connector`.</span></span>|
|`meetings`|<span data-ttu-id="0f09e-557">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="0f09e-557">string</span></span>|||<span data-ttu-id="0f09e-558">Wenn der ausgewählte Installationsbereich ausgewählt `meetings` ist, gibt dieses Feld die verfügbare Standardfunktion an.</span><span class="sxs-lookup"><span data-stu-id="0f09e-558">When the install scope selected is `meetings`, this field specifies the default capability available.</span></span> <span data-ttu-id="0f09e-559">Optionen: `tab` `bot` oder `connector` .</span><span class="sxs-lookup"><span data-stu-id="0f09e-559">Options: `tab`, `bot`, or `connector`.</span></span>|
