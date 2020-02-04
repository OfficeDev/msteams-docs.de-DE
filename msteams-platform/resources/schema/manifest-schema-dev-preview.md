---
title: Manifest-Schemareferenz für Entwicklervorschau
description: Beschreibt das vom Manifest für Microsoft Teams unterstützte Schema.
keywords: Entwicklervorschau für Teams-Manifest-Schema
ms.date: 05/20/2019
ms.openlocfilehash: b99e1ae99b7fd1edd4c695f43f3ac25270f0c710
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674104"
---
# <a name="developer-preview-manifest-schema-for-microsoft-teams"></a><span data-ttu-id="38cc7-104">Manifest-Schema für Entwicklervorschau für Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="38cc7-104">Developer preview manifest schema for Microsoft Teams</span></span>

> [!NOTE]
> <span data-ttu-id="38cc7-105">Informationen zum Programm und dazu, wie Sie teilnehmen können, finden Sie unter [Developer Preview](~/resources/dev-preview/developer-preview-intro.md) .</span><span class="sxs-lookup"><span data-stu-id="38cc7-105">See [Developer Preview](~/resources/dev-preview/developer-preview-intro.md) for information on the program and how you can join.</span></span>
> <span data-ttu-id="38cc7-106">Wenn Sie die Entwicklervorschau nicht verwenden, sollten Sie diese Version des Manifests nicht verwenden.</span><span class="sxs-lookup"><span data-stu-id="38cc7-106">If you are not using the developer preview you should not be using this version of the manifest.</span></span> <span data-ttu-id="38cc7-107">Siehe [Referenz: Manifest-Schema für Microsoft Teams](~/resources/schema/manifest-schema.md) für die öffentliche Version des Manifests.</span><span class="sxs-lookup"><span data-stu-id="38cc7-107">See [Reference: Manifest schema for Microsoft Teams](~/resources/schema/manifest-schema.md) for the public version of the manifest.</span></span>

<span data-ttu-id="38cc7-108">Das Microsoft Teams-Manifest beschreibt, wie die app in das Microsoft Teams-Produkt integriert wird.</span><span class="sxs-lookup"><span data-stu-id="38cc7-108">The Microsoft Teams manifest describes how the app integrates into the Microsoft Teams product.</span></span> <span data-ttu-id="38cc7-109">Das Manifest muss dem Schema entsprechen, das unter [`https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json`](https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json)gehostet wird.</span><span class="sxs-lookup"><span data-stu-id="38cc7-109">Your manifest must conform to the schema hosted at [`https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json`](https://raw.githubusercontent.com/OfficeDev/microsoft-teams-app-schema/preview/DevPreview/MicrosoftTeams.schema.json).</span></span>

<span data-ttu-id="38cc7-110">Weitere Informationen zu den verfügbaren Features finden Sie unter: [Features in der Public Developer Preview für Microsoft Teams](~/resources/dev-preview/developer-preview-features.md).</span><span class="sxs-lookup"><span data-stu-id="38cc7-110">For more information on the features available see: [Features in the Public Developer Preview for Microsoft Teams](~/resources/dev-preview/developer-preview-features.md).</span></span>

## <a name="sample-full-manifest"></a><span data-ttu-id="38cc7-111">Vollständiges Beispiel Manifest</span><span class="sxs-lookup"><span data-stu-id="38cc7-111">Sample full manifest</span></span>

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

<span data-ttu-id="38cc7-112">Das Schema definiert die folgenden Eigenschaften:</span><span class="sxs-lookup"><span data-stu-id="38cc7-112">The schema defines the following properties:</span></span>

## <a name="schema"></a><span data-ttu-id="38cc7-113">$schema</span><span class="sxs-lookup"><span data-stu-id="38cc7-113">$schema</span></span>

<span data-ttu-id="38cc7-114">*Optionale, aber empfohlene* &ndash; Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="38cc7-114">*Optional, but recommended* &ndash; String</span></span>

<span data-ttu-id="38cc7-115">Die https://-URL, die auf das JSON-Schema für das Manifest verweist.</span><span class="sxs-lookup"><span data-stu-id="38cc7-115">The https:// URL referencing the JSON Schema for the manifest.</span></span>

## <a name="manifestversion"></a><span data-ttu-id="38cc7-116">manifestVersion</span><span class="sxs-lookup"><span data-stu-id="38cc7-116">manifestVersion</span></span>

<span data-ttu-id="38cc7-117">**Erforderliche** &ndash; Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="38cc7-117">**Required** &ndash; String</span></span>

<span data-ttu-id="38cc7-118">Die Version des manifest-Schemas, die dieses Manifest verwendet.</span><span class="sxs-lookup"><span data-stu-id="38cc7-118">The version of the manifest schema this manifest is using.</span></span> <span data-ttu-id="38cc7-119">Es sollte "devPreview" sein.</span><span class="sxs-lookup"><span data-stu-id="38cc7-119">It should be "devPreview".</span></span>

## <a name="version"></a><span data-ttu-id="38cc7-120">Version</span><span class="sxs-lookup"><span data-stu-id="38cc7-120">version</span></span>

<span data-ttu-id="38cc7-121">**Erforderliche** &ndash; Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="38cc7-121">**Required** &ndash; String</span></span>

<span data-ttu-id="38cc7-122">Die Version der jeweiligen App.</span><span class="sxs-lookup"><span data-stu-id="38cc7-122">The version of the specific app.</span></span> <span data-ttu-id="38cc7-123">Wenn Sie etwas in ihrem Manifest aktualisieren, muss die Version ebenfalls inkrementiert werden.</span><span class="sxs-lookup"><span data-stu-id="38cc7-123">If you update something in your manifest, the version must be incremented as well.</span></span> <span data-ttu-id="38cc7-124">Auf diese Weise wird bei der Installation des neuen Manifests das vorhandene überschrieben, und der Benutzer erhält die neue Funktionalität.</span><span class="sxs-lookup"><span data-stu-id="38cc7-124">This way, when the new manifest is installed, it will overwrite the existing one and the user will get the new functionality.</span></span> <span data-ttu-id="38cc7-125">Wenn diese APP an den Store übermittelt wurde, muss das neue Manifest erneut übermittelt und erneut validiert werden.</span><span class="sxs-lookup"><span data-stu-id="38cc7-125">If this app was submitted to the store, the new manifest will have to be re-submitted and re-validated.</span></span> <span data-ttu-id="38cc7-126">Dann erhalten Benutzer dieser APP das neue aktualisierte Manifest automatisch in ein paar Stunden, nachdem es genehmigt wurde.</span><span class="sxs-lookup"><span data-stu-id="38cc7-126">Then, users of this app will get the new updated manifest automatically in a few hours, after it is approved.</span></span>

<span data-ttu-id="38cc7-127">Wenn sich die angeforderte APP geändert hat, werden die Benutzer aufgefordert, die APP zu aktualisieren und erneut zu genehmigen.</span><span class="sxs-lookup"><span data-stu-id="38cc7-127">If the app requested permissions change, users will be prompted to upgrade and re-consent to the app.</span></span>

<span data-ttu-id="38cc7-128">Diese Versionszeichenfolge muss dem [semver](http://semver.org/) -Standard (Major) entsprechen. Moll. Patch).</span><span class="sxs-lookup"><span data-stu-id="38cc7-128">This version string must follow the [semver](http://semver.org/) standard (MAJOR.MINOR.PATCH).</span></span>

## <a name="id"></a><span data-ttu-id="38cc7-129">id</span><span class="sxs-lookup"><span data-stu-id="38cc7-129">id</span></span>

<span data-ttu-id="38cc7-130">**Erforderliche** &ndash; Microsoft-App-ID</span><span class="sxs-lookup"><span data-stu-id="38cc7-130">**Required** &ndash; Microsoft app ID</span></span>

<span data-ttu-id="38cc7-131">Der eindeutige von Microsoft generierte Bezeichner für diese APP.</span><span class="sxs-lookup"><span data-stu-id="38cc7-131">The unique Microsoft-generated identifier for this app.</span></span> <span data-ttu-id="38cc7-132">Wenn Sie einen bot über das Microsoft bot-Framework registriert haben oder sich die Webanwendung Ihrer Registerkarte bereits bei Microsoft anmeldet, sollten Sie bereits über eine ID verfügen und diese hier eingeben.</span><span class="sxs-lookup"><span data-stu-id="38cc7-132">If you have registered a bot via the Microsoft Bot Framework, or your tab's web app already signs in with Microsoft, you should already have an ID and should enter it here.</span></span> <span data-ttu-id="38cc7-133">Andernfalls sollten Sie eine neue ID im Microsoft-Anwendungs Registrierungs Portal ([meine Anwendungen](https://apps.dev.microsoft.com)) generieren, Sie hier eingeben und dann wieder verwenden, wenn Sie [einen bot hinzufügen](~/bots/how-to/create-a-bot-for-teams.md).</span><span class="sxs-lookup"><span data-stu-id="38cc7-133">Otherwise, you should generate a new ID at the Microsoft Application Registration Portal ([My Applications](https://apps.dev.microsoft.com)), enter it here, and then reuse it when you [add a bot](~/bots/how-to/create-a-bot-for-teams.md).</span></span>

## <a name="packagename"></a><span data-ttu-id="38cc7-134">PackageName</span><span class="sxs-lookup"><span data-stu-id="38cc7-134">packageName</span></span>

<span data-ttu-id="38cc7-135">**Erforderliche** &ndash; Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="38cc7-135">**Required** &ndash; String</span></span>

<span data-ttu-id="38cc7-136">Ein eindeutiger Bezeichner für diese APP in umgekehrter Domänen Notation; Beispiel: com. Beispiel. MyApp.</span><span class="sxs-lookup"><span data-stu-id="38cc7-136">A unique identifier for this app in reverse domain notation; for example, com.example.myapp.</span></span>

## <a name="developer"></a><span data-ttu-id="38cc7-137">developer</span><span class="sxs-lookup"><span data-stu-id="38cc7-137">developer</span></span>

<span data-ttu-id="38cc7-138">**Required**</span><span class="sxs-lookup"><span data-stu-id="38cc7-138">**Required**</span></span>

<span data-ttu-id="38cc7-139">Gibt Informationen zu Ihrem Unternehmen an.</span><span class="sxs-lookup"><span data-stu-id="38cc7-139">Specifies information about your company.</span></span> <span data-ttu-id="38cc7-140">Für an AppSource übermittelte Apps (ehemals Office Store) müssen diese Werte mit den Informationen in Ihrem AppSource-Eintrag übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="38cc7-140">For apps submitted to AppSource (formerly Office Store), these values must match the information in your AppSource entry.</span></span>

|<span data-ttu-id="38cc7-141">Name</span><span class="sxs-lookup"><span data-stu-id="38cc7-141">Name</span></span>| <span data-ttu-id="38cc7-142">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="38cc7-142">Maximum size</span></span> | <span data-ttu-id="38cc7-143">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="38cc7-143">Required</span></span> | <span data-ttu-id="38cc7-144">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="38cc7-144">Description</span></span>|
|---|---|---|---|
|`name`|<span data-ttu-id="38cc7-145">32 Zeichen</span><span class="sxs-lookup"><span data-stu-id="38cc7-145">32 characters</span></span>|<span data-ttu-id="38cc7-146">✔</span><span class="sxs-lookup"><span data-stu-id="38cc7-146">✔</span></span>|<span data-ttu-id="38cc7-147">Der Anzeigename für den Entwickler.</span><span class="sxs-lookup"><span data-stu-id="38cc7-147">The display name for the developer.</span></span>|
|`websiteUrl`|<span data-ttu-id="38cc7-148">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="38cc7-148">2048 characters</span></span>|<span data-ttu-id="38cc7-149">✔</span><span class="sxs-lookup"><span data-stu-id="38cc7-149">✔</span></span>|<span data-ttu-id="38cc7-150">Die https://-URL zur Website des Entwicklers.</span><span class="sxs-lookup"><span data-stu-id="38cc7-150">The https:// URL to the developer's website.</span></span> <span data-ttu-id="38cc7-151">Dieser Link sollte Benutzer zu Ihrer Firma oder produktspezifischen Zielseite führen.</span><span class="sxs-lookup"><span data-stu-id="38cc7-151">This link should take users to your company or product-specific landing page.</span></span>|
|`privacyUrl`|<span data-ttu-id="38cc7-152">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="38cc7-152">2048 characters</span></span>|<span data-ttu-id="38cc7-153">✔</span><span class="sxs-lookup"><span data-stu-id="38cc7-153">✔</span></span>|<span data-ttu-id="38cc7-154">Die https://-URL zur Datenschutzrichtlinie des Entwicklers.</span><span class="sxs-lookup"><span data-stu-id="38cc7-154">The https:// URL to the developer's privacy policy.</span></span>|
|`termsOfUseUrl`|<span data-ttu-id="38cc7-155">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="38cc7-155">2048 characters</span></span>|<span data-ttu-id="38cc7-156">✔</span><span class="sxs-lookup"><span data-stu-id="38cc7-156">✔</span></span>|<span data-ttu-id="38cc7-157">Die https://-URL zu den Nutzungsbedingungen des Entwicklers.</span><span class="sxs-lookup"><span data-stu-id="38cc7-157">The https:// URL to the developer's terms of use.</span></span>|
|`mpnId`|<span data-ttu-id="38cc7-158">10 Zeichen</span><span class="sxs-lookup"><span data-stu-id="38cc7-158">10 characters</span></span>|<span data-ttu-id="38cc7-159">✔</span><span class="sxs-lookup"><span data-stu-id="38cc7-159">✔</span></span>|<span data-ttu-id="38cc7-160">**Optional** Die Microsoft Partner-Netzwerk-ID, die die Partnerorganisation identifiziert, die die APP aufbaut.</span><span class="sxs-lookup"><span data-stu-id="38cc7-160">**Optional** The Microsoft Partner Network ID that identifies the partner organization building the app.</span></span>|

## <a name="localizationinfo"></a><span data-ttu-id="38cc7-161">localizationInfo</span><span class="sxs-lookup"><span data-stu-id="38cc7-161">localizationInfo</span></span>

<span data-ttu-id="38cc7-162">**Optional**</span><span class="sxs-lookup"><span data-stu-id="38cc7-162">**Optional**</span></span>

<span data-ttu-id="38cc7-163">Ermöglicht die Angabe einer Standardsprache sowie Zeiger auf zusätzliche Sprachdateien.</span><span class="sxs-lookup"><span data-stu-id="38cc7-163">Allows the specification of a default language, as well as pointers to additional language files.</span></span> <span data-ttu-id="38cc7-164">Siehe [Lokalisierung](~/concepts/build-and-test/apps-localization.md).</span><span class="sxs-lookup"><span data-stu-id="38cc7-164">See [localization](~/concepts/build-and-test/apps-localization.md).</span></span>

|<span data-ttu-id="38cc7-165">Name</span><span class="sxs-lookup"><span data-stu-id="38cc7-165">Name</span></span>| <span data-ttu-id="38cc7-166">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="38cc7-166">Maximum size</span></span> | <span data-ttu-id="38cc7-167">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="38cc7-167">Required</span></span> | <span data-ttu-id="38cc7-168">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="38cc7-168">Description</span></span>|
|---|---|---|---|
|`defaultLanguageTag`|<span data-ttu-id="38cc7-169">4 Zeichen</span><span class="sxs-lookup"><span data-stu-id="38cc7-169">4 characters</span></span>|<span data-ttu-id="38cc7-170">✔</span><span class="sxs-lookup"><span data-stu-id="38cc7-170">✔</span></span>|<span data-ttu-id="38cc7-171">Das Language-Tag der Zeichenfolgen in dieser Manifestdatei der obersten Ebene.</span><span class="sxs-lookup"><span data-stu-id="38cc7-171">The language tag of the strings in this top level manifest file.</span></span>|

### <a name="localizationinfoadditionallanguages"></a><span data-ttu-id="38cc7-172">localizationInfo.additionalLanguages</span><span class="sxs-lookup"><span data-stu-id="38cc7-172">localizationInfo.additionalLanguages</span></span>

<span data-ttu-id="38cc7-173">Ein Array von Objekten, das zusätzliche Sprachübersetzungen angibt.</span><span class="sxs-lookup"><span data-stu-id="38cc7-173">An array of objects specifying additional language translations.</span></span>

|<span data-ttu-id="38cc7-174">Name</span><span class="sxs-lookup"><span data-stu-id="38cc7-174">Name</span></span>| <span data-ttu-id="38cc7-175">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="38cc7-175">Maximum size</span></span> | <span data-ttu-id="38cc7-176">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="38cc7-176">Required</span></span> | <span data-ttu-id="38cc7-177">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="38cc7-177">Description</span></span>|
|---|---|---|---|
|`languageTag`|<span data-ttu-id="38cc7-178">4 Zeichen</span><span class="sxs-lookup"><span data-stu-id="38cc7-178">4 characters</span></span>|<span data-ttu-id="38cc7-179">✔</span><span class="sxs-lookup"><span data-stu-id="38cc7-179">✔</span></span>|<span data-ttu-id="38cc7-180">Das Language-Tag der Zeichenfolgen in der bereitgestellten Datei.</span><span class="sxs-lookup"><span data-stu-id="38cc7-180">The language tag of the strings in the provided file.</span></span>|
|`file`|<span data-ttu-id="38cc7-181">4 Zeichen</span><span class="sxs-lookup"><span data-stu-id="38cc7-181">4 characters</span></span>|<span data-ttu-id="38cc7-182">✔</span><span class="sxs-lookup"><span data-stu-id="38cc7-182">✔</span></span>|<span data-ttu-id="38cc7-183">Ein relativer Dateipfad zu einer JSON-Datei, die die übersetzten Zeichenfolgen enthält.</span><span class="sxs-lookup"><span data-stu-id="38cc7-183">A relative file path to a the .json file containing the translated strings.</span></span>|

## <a name="name"></a><span data-ttu-id="38cc7-184">Name</span><span class="sxs-lookup"><span data-stu-id="38cc7-184">name</span></span>

<span data-ttu-id="38cc7-185">**Required**</span><span class="sxs-lookup"><span data-stu-id="38cc7-185">**Required**</span></span>

<span data-ttu-id="38cc7-186">Der Name der APP-Erfahrung, der Benutzern in der Microsoft Teams-Benutzeroberfläche angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="38cc7-186">The name of your app experience, displayed to users in the Teams experience.</span></span> <span data-ttu-id="38cc7-187">Für apps, die an AppSource übermittelt werden, müssen diese Werte mit den Informationen in Ihrem AppSource-Eintrag übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="38cc7-187">For apps submitted to AppSource, these values must match the information in your AppSource entry.</span></span> <span data-ttu-id="38cc7-188">Die Werte von `short` und `full` sollten nicht identisch sein.</span><span class="sxs-lookup"><span data-stu-id="38cc7-188">The values of `short` and `full` should not be the same.</span></span>

|<span data-ttu-id="38cc7-189">Name</span><span class="sxs-lookup"><span data-stu-id="38cc7-189">Name</span></span>| <span data-ttu-id="38cc7-190">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="38cc7-190">Maximum size</span></span> | <span data-ttu-id="38cc7-191">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="38cc7-191">Required</span></span> | <span data-ttu-id="38cc7-192">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="38cc7-192">Description</span></span>|
|---|---|---|---|
|`short`|<span data-ttu-id="38cc7-193">30 Zeichen</span><span class="sxs-lookup"><span data-stu-id="38cc7-193">30 characters</span></span>|<span data-ttu-id="38cc7-194">✔</span><span class="sxs-lookup"><span data-stu-id="38cc7-194">✔</span></span>|<span data-ttu-id="38cc7-195">Der kurze Anzeigename für die app.</span><span class="sxs-lookup"><span data-stu-id="38cc7-195">The short display name for the app.</span></span>|
|`full`|<span data-ttu-id="38cc7-196">100 Zeichen</span><span class="sxs-lookup"><span data-stu-id="38cc7-196">100 characters</span></span>||<span data-ttu-id="38cc7-197">Der vollständige Name der APP, der verwendet wird, wenn der vollständige App-Name 30 Zeichen überschreitet.</span><span class="sxs-lookup"><span data-stu-id="38cc7-197">The full name of the app, used if the full app name exceeds 30 characters.</span></span>|

## <a name="description"></a><span data-ttu-id="38cc7-198">description</span><span class="sxs-lookup"><span data-stu-id="38cc7-198">description</span></span>

<span data-ttu-id="38cc7-199">**Required**</span><span class="sxs-lookup"><span data-stu-id="38cc7-199">**Required**</span></span>

<span data-ttu-id="38cc7-200">Beschreibt die APP für Benutzer.</span><span class="sxs-lookup"><span data-stu-id="38cc7-200">Describes your app to users.</span></span> <span data-ttu-id="38cc7-201">Für apps, die an AppSource übermittelt werden, müssen diese Werte mit den Informationen in Ihrem AppSource-Eintrag übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="38cc7-201">For apps submitted to AppSource, these values must match the information in your AppSource entry.</span></span>

<span data-ttu-id="38cc7-202">Stellen Sie sicher, dass Ihre Beschreibung ihre Erfahrung genau beschreibt und Informationen bereitstellt, um potenziellen Kunden zu helfen, ihre Erfahrungen zu verstehen.</span><span class="sxs-lookup"><span data-stu-id="38cc7-202">Ensure that your description accurately describes your experience and provides information to help potential customers understand what your experience does.</span></span> <span data-ttu-id="38cc7-203">Beachten Sie auch, dass in der vollständigen Beschreibung ein externes Konto zur Verwendung benötigt wird.</span><span class="sxs-lookup"><span data-stu-id="38cc7-203">You should also note, in the full description, if an external account is required for use.</span></span> <span data-ttu-id="38cc7-204">Die Werte von `short` und `full` sollten nicht identisch sein.</span><span class="sxs-lookup"><span data-stu-id="38cc7-204">The values of `short` and `full` should not be the same.</span></span>  <span data-ttu-id="38cc7-205">Ihre Kurzbeschreibung darf nicht innerhalb der langen Beschreibung wiederholt werden und darf keinen anderen APP-Namen enthalten.</span><span class="sxs-lookup"><span data-stu-id="38cc7-205">Your short description must not be repeated within the long description and must not include any other app name.</span></span>

|<span data-ttu-id="38cc7-206">Name</span><span class="sxs-lookup"><span data-stu-id="38cc7-206">Name</span></span>| <span data-ttu-id="38cc7-207">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="38cc7-207">Maximum size</span></span> | <span data-ttu-id="38cc7-208">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="38cc7-208">Required</span></span> | <span data-ttu-id="38cc7-209">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="38cc7-209">Description</span></span>|
|---|---|---|---|
|`short`|<span data-ttu-id="38cc7-210">80 Zeichen</span><span class="sxs-lookup"><span data-stu-id="38cc7-210">80 characters</span></span>|<span data-ttu-id="38cc7-211">✔</span><span class="sxs-lookup"><span data-stu-id="38cc7-211">✔</span></span>|<span data-ttu-id="38cc7-212">Eine kurze Beschreibung Ihrer APP-Erfahrung, die verwendet wird, wenn der Speicherplatz limitiert ist.</span><span class="sxs-lookup"><span data-stu-id="38cc7-212">A short description of your app experience, used when space is limited.</span></span>|
|`full`|<span data-ttu-id="38cc7-213">4000 Zeichen</span><span class="sxs-lookup"><span data-stu-id="38cc7-213">4000 characters</span></span>|<span data-ttu-id="38cc7-214">✔</span><span class="sxs-lookup"><span data-stu-id="38cc7-214">✔</span></span>|<span data-ttu-id="38cc7-215">Die vollständige Beschreibung Ihrer APP.</span><span class="sxs-lookup"><span data-stu-id="38cc7-215">The full description of your app.</span></span>|

## <a name="icons"></a><span data-ttu-id="38cc7-216">Symbole</span><span class="sxs-lookup"><span data-stu-id="38cc7-216">icons</span></span>

<span data-ttu-id="38cc7-217">**Required**</span><span class="sxs-lookup"><span data-stu-id="38cc7-217">**Required**</span></span>

<span data-ttu-id="38cc7-218">Symbole, die in der Teams-App verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="38cc7-218">Icons used within the Teams app.</span></span> <span data-ttu-id="38cc7-219">Die Symboldateien müssen als Teil des Upload-Pakets enthalten sein.</span><span class="sxs-lookup"><span data-stu-id="38cc7-219">The icon files must be included as part of the upload package.</span></span>

|<span data-ttu-id="38cc7-220">Name</span><span class="sxs-lookup"><span data-stu-id="38cc7-220">Name</span></span>| <span data-ttu-id="38cc7-221">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="38cc7-221">Maximum size</span></span> | <span data-ttu-id="38cc7-222">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="38cc7-222">Required</span></span> | <span data-ttu-id="38cc7-223">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="38cc7-223">Description</span></span>|
|---|---|---|---|
|`outline`|<span data-ttu-id="38cc7-224">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="38cc7-224">2048 characters</span></span>|<span data-ttu-id="38cc7-225">✔</span><span class="sxs-lookup"><span data-stu-id="38cc7-225">✔</span></span>|<span data-ttu-id="38cc7-226">Ein relativer Dateipfad zu einem transparenten 32x32 PNG-Gliederungssymbol.</span><span class="sxs-lookup"><span data-stu-id="38cc7-226">A relative file path to a transparent 32x32 PNG outline icon.</span></span>|
|`color`|<span data-ttu-id="38cc7-227">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="38cc7-227">2048 characters</span></span>|<span data-ttu-id="38cc7-228">✔</span><span class="sxs-lookup"><span data-stu-id="38cc7-228">✔</span></span>|<span data-ttu-id="38cc7-229">Ein relativer Dateipfad zu einem vollfarbigen 192x192 PNG-Symbol.</span><span class="sxs-lookup"><span data-stu-id="38cc7-229">A relative file path to a full color 192x192 PNG icon.</span></span>|

## <a name="accentcolor"></a><span data-ttu-id="38cc7-230">accentColor</span><span class="sxs-lookup"><span data-stu-id="38cc7-230">accentColor</span></span>

<span data-ttu-id="38cc7-231">**Erforderliche** &ndash; Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="38cc7-231">**Required** &ndash; String</span></span>

<span data-ttu-id="38cc7-232">Eine Farbe, die in Verbindung mit und als Hintergrund für die Gliederungssymbole verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="38cc7-232">A color to use in conjunction with and as a background for your outline icons.</span></span>

<span data-ttu-id="38cc7-233">Der Wert muss ein gültiger HTML-Farb Code sein, der mit "#" beginnt `#4464ee`, beispielsweise.</span><span class="sxs-lookup"><span data-stu-id="38cc7-233">The value must be a valid HTML color code starting with '#', for example `#4464ee`.</span></span>

## <a name="configurabletabs"></a><span data-ttu-id="38cc7-234">configurableTabs</span><span class="sxs-lookup"><span data-stu-id="38cc7-234">configurableTabs</span></span>

<span data-ttu-id="38cc7-235">**Optional**</span><span class="sxs-lookup"><span data-stu-id="38cc7-235">**Optional**</span></span>

<span data-ttu-id="38cc7-236">Wird verwendet, wenn Ihre APP-Erfahrung eine Team Kanal-registerkartenoberfläche aufweist, die eine zusätzliche Konfiguration erfordert, bevor Sie hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="38cc7-236">Used when your app experience has a team channel tab experience that requires extra configuration before it is added.</span></span> <span data-ttu-id="38cc7-237">Konfigurierbare Registerkarten werden nur im Bereich Teams unterstützt, und derzeit wird nur eine Registerkarte pro App unterstützt.</span><span class="sxs-lookup"><span data-stu-id="38cc7-237">Configurable tabs are supported only in the teams scope, and currently only one tab per app is supported.</span></span>

<span data-ttu-id="38cc7-238">Das Objekt ist ein Array mit allen Elementen des Typs `object`.</span><span class="sxs-lookup"><span data-stu-id="38cc7-238">The object is an array with all elements of the type `object`.</span></span> <span data-ttu-id="38cc7-239">Dieser Block ist nur für Lösungen erforderlich, die eine konfigurierbare Kanal Registerkarten Lösung bieten.</span><span class="sxs-lookup"><span data-stu-id="38cc7-239">This block is required only for solutions that provide a configurable channel tab solution.</span></span>

|<span data-ttu-id="38cc7-240">Name</span><span class="sxs-lookup"><span data-stu-id="38cc7-240">Name</span></span>| <span data-ttu-id="38cc7-241">Typ</span><span class="sxs-lookup"><span data-stu-id="38cc7-241">Type</span></span>| <span data-ttu-id="38cc7-242">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="38cc7-242">Maximum size</span></span> | <span data-ttu-id="38cc7-243">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="38cc7-243">Required</span></span> | <span data-ttu-id="38cc7-244">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="38cc7-244">Description</span></span>|
|---|---|---|---|---|
|`configurationUrl`|<span data-ttu-id="38cc7-245">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="38cc7-245">String</span></span>|<span data-ttu-id="38cc7-246">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="38cc7-246">2048 characters</span></span>|<span data-ttu-id="38cc7-247">✔</span><span class="sxs-lookup"><span data-stu-id="38cc7-247">✔</span></span>|<span data-ttu-id="38cc7-248">Die https://-URL, die beim Konfigurieren der Registerkarte verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="38cc7-248">The https:// URL to use when configuring the tab.</span></span>|
|`canUpdateConfiguration`|<span data-ttu-id="38cc7-249">Boolesch</span><span class="sxs-lookup"><span data-stu-id="38cc7-249">Boolean</span></span>|||<span data-ttu-id="38cc7-250">Ein Wert, der angibt, ob eine Instanz der Konfiguration der Registerkarte nach der Erstellung vom Benutzer aktualisiert werden kann.</span><span class="sxs-lookup"><span data-stu-id="38cc7-250">A value indicating whether an instance of the tab's configuration can be updated by the user after creation.</span></span> <span data-ttu-id="38cc7-251">Standard`true`</span><span class="sxs-lookup"><span data-stu-id="38cc7-251">Default: `true`</span></span>|
|`scopes`|<span data-ttu-id="38cc7-252">Array von Enum</span><span class="sxs-lookup"><span data-stu-id="38cc7-252">Array of enum</span></span>|<span data-ttu-id="38cc7-253">1 </span><span class="sxs-lookup"><span data-stu-id="38cc7-253">1</span></span>|<span data-ttu-id="38cc7-254">✔</span><span class="sxs-lookup"><span data-stu-id="38cc7-254">✔</span></span>|<span data-ttu-id="38cc7-255">Derzeit unterstützen konfigurierbare Registerkarten `team` nur `groupchat` die Bereiche und.</span><span class="sxs-lookup"><span data-stu-id="38cc7-255">Currently, configurable tabs support only the `team` and `groupchat` scopes.</span></span> |
|`sharePointPreviewImage`|<span data-ttu-id="38cc7-256">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="38cc7-256">String</span></span>|<span data-ttu-id="38cc7-257">2048</span><span class="sxs-lookup"><span data-stu-id="38cc7-257">2048</span></span>||<span data-ttu-id="38cc7-258">Ein relativer Dateipfad zu einem Vorschaubild für die Registerkarte für die Verwendung in SharePoint.</span><span class="sxs-lookup"><span data-stu-id="38cc7-258">A relative file path to a tab preview image for use in SharePoint.</span></span> <span data-ttu-id="38cc7-259">Größe 1024x768.</span><span class="sxs-lookup"><span data-stu-id="38cc7-259">Size 1024x768.</span></span> |
|`supportedSharePointHosts`|<span data-ttu-id="38cc7-260">Array von Enum</span><span class="sxs-lookup"><span data-stu-id="38cc7-260">Array of enum</span></span>|<span data-ttu-id="38cc7-261">1 </span><span class="sxs-lookup"><span data-stu-id="38cc7-261">1</span></span>||<span data-ttu-id="38cc7-262">Definiert, wie die Registerkarte in SharePoint zur Verfügung gestellt wird.</span><span class="sxs-lookup"><span data-stu-id="38cc7-262">Defines how your tab will be made available in SharePoint.</span></span> <span data-ttu-id="38cc7-263">Optionen sind `sharePointFullPage` und`sharePointWebPart`</span><span class="sxs-lookup"><span data-stu-id="38cc7-263">Options are `sharePointFullPage` and `sharePointWebPart`</span></span> |

## <a name="statictabs"></a><span data-ttu-id="38cc7-264">staticTabs</span><span class="sxs-lookup"><span data-stu-id="38cc7-264">staticTabs</span></span>

<span data-ttu-id="38cc7-265">**Optional**</span><span class="sxs-lookup"><span data-stu-id="38cc7-265">**Optional**</span></span>

<span data-ttu-id="38cc7-266">Definiert eine Gruppe von Registerkarten, die standardmäßig "fixiert" werden können, ohne dass der Benutzer Sie manuell hinzufügt.</span><span class="sxs-lookup"><span data-stu-id="38cc7-266">Defines a set of tabs that can be "pinned" by default, without the user adding them manually.</span></span> <span data-ttu-id="38cc7-267">Im `personal` Bereich deklarierte statische Registerkarten werden immer an die persönliche Benutzeroberfläche der APP angeheftet.</span><span class="sxs-lookup"><span data-stu-id="38cc7-267">Static tabs declared in `personal` scope are always pinned to the app's personal experience.</span></span> <span data-ttu-id="38cc7-268">Im `team` Bereich deklarierte statische Registerkarten werden derzeit nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="38cc7-268">Static tabs declared in the `team` scope are currently not supported.</span></span>

<span data-ttu-id="38cc7-269">Bei dem Objekt handelt es sich um ein Array (maximal 16 Elemente) mit allen Elementen `object`des Typs.</span><span class="sxs-lookup"><span data-stu-id="38cc7-269">The object is an array (maximum of 16 elements) with all elements of the type `object`.</span></span> <span data-ttu-id="38cc7-270">Dieser Block ist nur für Lösungen erforderlich, die eine statische Registerkarten Lösung bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="38cc7-270">This block is required only for solutions that provide a static tab solution.</span></span>

|<span data-ttu-id="38cc7-271">Name</span><span class="sxs-lookup"><span data-stu-id="38cc7-271">Name</span></span>| <span data-ttu-id="38cc7-272">Typ</span><span class="sxs-lookup"><span data-stu-id="38cc7-272">Type</span></span>| <span data-ttu-id="38cc7-273">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="38cc7-273">Maximum size</span></span> | <span data-ttu-id="38cc7-274">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="38cc7-274">Required</span></span> | <span data-ttu-id="38cc7-275">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="38cc7-275">Description</span></span>|
|---|---|---|---|---|
|`entityId`|<span data-ttu-id="38cc7-276">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="38cc7-276">String</span></span>|<span data-ttu-id="38cc7-277">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="38cc7-277">64 characters</span></span>|<span data-ttu-id="38cc7-278">✔</span><span class="sxs-lookup"><span data-stu-id="38cc7-278">✔</span></span>|<span data-ttu-id="38cc7-279">Ein eindeutiger Bezeichner für die Entität, die auf der Registerkarte angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="38cc7-279">A unique identifier for the entity that the tab displays.</span></span>|
|`name`|<span data-ttu-id="38cc7-280">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="38cc7-280">String</span></span>|<span data-ttu-id="38cc7-281">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="38cc7-281">128 characters</span></span>|<span data-ttu-id="38cc7-282">✔</span><span class="sxs-lookup"><span data-stu-id="38cc7-282">✔</span></span>|<span data-ttu-id="38cc7-283">Der Anzeigename der Registerkarte in der Kanalschnittstelle.</span><span class="sxs-lookup"><span data-stu-id="38cc7-283">The display name of the tab in the channel interface.</span></span>|
|`contentUrl`|<span data-ttu-id="38cc7-284">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="38cc7-284">String</span></span>|<span data-ttu-id="38cc7-285">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="38cc7-285">2048 characters</span></span>|<span data-ttu-id="38cc7-286">✔</span><span class="sxs-lookup"><span data-stu-id="38cc7-286">✔</span></span>|<span data-ttu-id="38cc7-287">Die https://-URL, die auf die Benutzeroberfläche der Entität zeigt, die im Canvas "Teams" angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="38cc7-287">The https:// URL that points to the entity UI to be displayed in the Teams canvas.</span></span>|
|`websiteUrl`|<span data-ttu-id="38cc7-288">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="38cc7-288">String</span></span>|<span data-ttu-id="38cc7-289">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="38cc7-289">2048 characters</span></span>||<span data-ttu-id="38cc7-290">Die https://-URL, auf die verwiesen wird, wenn ein Benutzer sich für die Anzeige in einem Browser entscheidet.</span><span class="sxs-lookup"><span data-stu-id="38cc7-290">The https:// URL to point at if a user opts to view in a browser.</span></span>|
|`scopes`|<span data-ttu-id="38cc7-291">Array von Enum</span><span class="sxs-lookup"><span data-stu-id="38cc7-291">Array of enum</span></span>|<span data-ttu-id="38cc7-292">1 </span><span class="sxs-lookup"><span data-stu-id="38cc7-292">1</span></span>|<span data-ttu-id="38cc7-293">✔</span><span class="sxs-lookup"><span data-stu-id="38cc7-293">✔</span></span>|<span data-ttu-id="38cc7-294">Derzeit unterstützen statische Registerkarten nur `personal` den Bereich, was bedeutet, dass Sie nur als Teil der persönlichen Benutzeroberfläche vorgesehen werden kann.</span><span class="sxs-lookup"><span data-stu-id="38cc7-294">Currently, static tabs support only the `personal` scope, which means it can be provisioned only as part of the personal experience.</span></span>|

## <a name="bots"></a><span data-ttu-id="38cc7-295">Bots</span><span class="sxs-lookup"><span data-stu-id="38cc7-295">bots</span></span>

<span data-ttu-id="38cc7-296">**Optional**</span><span class="sxs-lookup"><span data-stu-id="38cc7-296">**Optional**</span></span>

<span data-ttu-id="38cc7-297">Definiert eine bot-Lösung zusammen mit optionalen Informationen wie Standardbefehls Eigenschaften.</span><span class="sxs-lookup"><span data-stu-id="38cc7-297">Defines a bot solution, along with optional information such as default command properties.</span></span>

<span data-ttu-id="38cc7-298">Das Objekt ist ein Array (Maximum von nur 1 Element&mdash;, das derzeit nur ein bot pro App zulässig ist) mit allen Elementen des `object`Typs.</span><span class="sxs-lookup"><span data-stu-id="38cc7-298">The object is an array (maximum of only 1 element&mdash;currently only one bot is allowed per app) with all elements of the type `object`.</span></span> <span data-ttu-id="38cc7-299">Dieser Block ist nur für Lösungen erforderlich, die eine bot-Erfahrung bieten.</span><span class="sxs-lookup"><span data-stu-id="38cc7-299">This block is required only for solutions that provide a bot experience.</span></span>

|<span data-ttu-id="38cc7-300">Name</span><span class="sxs-lookup"><span data-stu-id="38cc7-300">Name</span></span>| <span data-ttu-id="38cc7-301">Typ</span><span class="sxs-lookup"><span data-stu-id="38cc7-301">Type</span></span>| <span data-ttu-id="38cc7-302">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="38cc7-302">Maximum size</span></span> | <span data-ttu-id="38cc7-303">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="38cc7-303">Required</span></span> | <span data-ttu-id="38cc7-304">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="38cc7-304">Description</span></span>|
|---|---|---|---|---|
|`botId`|<span data-ttu-id="38cc7-305">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="38cc7-305">String</span></span>|<span data-ttu-id="38cc7-306">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="38cc7-306">64 characters</span></span>|<span data-ttu-id="38cc7-307">✔</span><span class="sxs-lookup"><span data-stu-id="38cc7-307">✔</span></span>|<span data-ttu-id="38cc7-308">Die eindeutige Microsoft-App-ID für den bot, die im bot-Framework registriert ist.</span><span class="sxs-lookup"><span data-stu-id="38cc7-308">The unique Microsoft app ID for the bot as registered with the Bot Framework.</span></span> <span data-ttu-id="38cc7-309">Dies kann auch die gesamte [App-ID](#id)entsprechen.</span><span class="sxs-lookup"><span data-stu-id="38cc7-309">This may well be the same as the overall [app ID](#id).</span></span>|
|`needsChannelSelector`|<span data-ttu-id="38cc7-310">Boolesch</span><span class="sxs-lookup"><span data-stu-id="38cc7-310">Boolean</span></span>|||<span data-ttu-id="38cc7-311">Beschreibt, ob der bot einen Benutzerhinweis verwendet, um den bot einem bestimmten Kanal hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="38cc7-311">Describes whether or not the bot utilizes a user hint to add the bot to a specific channel.</span></span> <span data-ttu-id="38cc7-312">Standard`false`</span><span class="sxs-lookup"><span data-stu-id="38cc7-312">Default: `false`</span></span>|
|`isNotificationOnly`|<span data-ttu-id="38cc7-313">Boolesch</span><span class="sxs-lookup"><span data-stu-id="38cc7-313">Boolean</span></span>|||<span data-ttu-id="38cc7-314">Gibt an, ob ein bot ein unidirektionaler, nur für Benachrichtigungen gestellter bot ist, im Gegensatz zu einem Unterhaltungs bot.</span><span class="sxs-lookup"><span data-stu-id="38cc7-314">Indicates whether a bot is a one-way, notification-only bot, as opposed to a conversational bot.</span></span> <span data-ttu-id="38cc7-315">Standard`false`</span><span class="sxs-lookup"><span data-stu-id="38cc7-315">Default: `false`</span></span>|
|`supportsFiles`|<span data-ttu-id="38cc7-316">Boolesch</span><span class="sxs-lookup"><span data-stu-id="38cc7-316">Boolean</span></span>|||<span data-ttu-id="38cc7-317">Gibt an, ob der bot die Möglichkeit unterstützt, Dateien im persönlichen Chat hoch-/herunterzuladen.</span><span class="sxs-lookup"><span data-stu-id="38cc7-317">Indicates whether the bot supports the ability to upload/download files in personal chat.</span></span> <span data-ttu-id="38cc7-318">Standard`false`</span><span class="sxs-lookup"><span data-stu-id="38cc7-318">Default: `false`</span></span>|
|`scopes`|<span data-ttu-id="38cc7-319">Array von Enum</span><span class="sxs-lookup"><span data-stu-id="38cc7-319">Array of enum</span></span>|<span data-ttu-id="38cc7-320">3 </span><span class="sxs-lookup"><span data-stu-id="38cc7-320">3</span></span>|<span data-ttu-id="38cc7-321">✔</span><span class="sxs-lookup"><span data-stu-id="38cc7-321">✔</span></span>|<span data-ttu-id="38cc7-322">Gibt an, ob der bot eine Erfahrung im Kontext eines Kanals in a `team`, in einem Gruppenchat (`groupchat`) oder eine Erfahrung bietet, die auf einen einzelnen Benutzer allein beschränkt`personal`ist ().</span><span class="sxs-lookup"><span data-stu-id="38cc7-322">Specifies whether the bot offers an experience in the context of a channel in a `team`, in a group chat (`groupchat`), or an experience scoped to an individual user alone (`personal`).</span></span> <span data-ttu-id="38cc7-323">Diese Optionen sind nicht exklusiv.</span><span class="sxs-lookup"><span data-stu-id="38cc7-323">These options are non-exclusive.</span></span>|

### <a name="botscommandlists"></a><span data-ttu-id="38cc7-324">Bots. commandLists</span><span class="sxs-lookup"><span data-stu-id="38cc7-324">bots.commandLists</span></span>

<span data-ttu-id="38cc7-325">Eine optionale Liste von Befehlen, die ihr bot Benutzern empfehlen kann.</span><span class="sxs-lookup"><span data-stu-id="38cc7-325">An optional list of commands that your bot can recommend to users.</span></span> <span data-ttu-id="38cc7-326">Das Objekt ist ein Array (Maximum von 2 Elementen) mit allen Elementen des Typs `object`; Sie müssen für jeden Bereich, den Ihr bot unterstützt, eine separate Befehlsliste definieren.</span><span class="sxs-lookup"><span data-stu-id="38cc7-326">The object is an array (maximum of 2 elements) with all elements of type `object`; you must define a separate command list for each scope that your bot supports.</span></span> <span data-ttu-id="38cc7-327">Weitere Informationen finden Sie unter [bot-Menüs](~/bots/how-to/create-a-bot-commands-menu.md) .</span><span class="sxs-lookup"><span data-stu-id="38cc7-327">See [Bot menus](~/bots/how-to/create-a-bot-commands-menu.md) for more information.</span></span>

|<span data-ttu-id="38cc7-328">Name</span><span class="sxs-lookup"><span data-stu-id="38cc7-328">Name</span></span>| <span data-ttu-id="38cc7-329">Typ</span><span class="sxs-lookup"><span data-stu-id="38cc7-329">Type</span></span>| <span data-ttu-id="38cc7-330">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="38cc7-330">Maximum size</span></span> | <span data-ttu-id="38cc7-331">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="38cc7-331">Required</span></span> | <span data-ttu-id="38cc7-332">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="38cc7-332">Description</span></span>|
|---|---|---|---|---|
|`items.scopes`|<span data-ttu-id="38cc7-333">Array von Enum</span><span class="sxs-lookup"><span data-stu-id="38cc7-333">array of enum</span></span>|<span data-ttu-id="38cc7-334">3 </span><span class="sxs-lookup"><span data-stu-id="38cc7-334">3</span></span>|<span data-ttu-id="38cc7-335">✔</span><span class="sxs-lookup"><span data-stu-id="38cc7-335">✔</span></span>|<span data-ttu-id="38cc7-336">Gibt den Bereich an, für den die Befehlsliste gültig ist.</span><span class="sxs-lookup"><span data-stu-id="38cc7-336">Specifies the scope for which the command list is valid.</span></span> <span data-ttu-id="38cc7-337">Optionen sind `team`, `personal`und `groupchat`.</span><span class="sxs-lookup"><span data-stu-id="38cc7-337">Options are `team`, `personal`, and `groupchat`.</span></span>|
|`items.commands`|<span data-ttu-id="38cc7-338">Array von Objekten</span><span class="sxs-lookup"><span data-stu-id="38cc7-338">array of objects</span></span>|<span data-ttu-id="38cc7-339">10  </span><span class="sxs-lookup"><span data-stu-id="38cc7-339">10</span></span>|<span data-ttu-id="38cc7-340">✔</span><span class="sxs-lookup"><span data-stu-id="38cc7-340">✔</span></span>|<span data-ttu-id="38cc7-341">Ein Array von Befehlen, die der bot unterstützt:</span><span class="sxs-lookup"><span data-stu-id="38cc7-341">An array of commands the bot supports:</span></span><br><span data-ttu-id="38cc7-342">`title`: der Name des bot-Befehls (String, 32)</span><span class="sxs-lookup"><span data-stu-id="38cc7-342">`title`: the bot command name (string, 32)</span></span><br><span data-ttu-id="38cc7-343">`description`: eine einfache Beschreibung oder ein Beispiel für die Befehlssyntax und das zugehörige Argument (String, 128)</span><span class="sxs-lookup"><span data-stu-id="38cc7-343">`description`: a simple description or example of the command syntax and its argument (string, 128)</span></span>|

## <a name="connectors"></a><span data-ttu-id="38cc7-344">Connectors</span><span class="sxs-lookup"><span data-stu-id="38cc7-344">connectors</span></span>

<span data-ttu-id="38cc7-345">**Optional**</span><span class="sxs-lookup"><span data-stu-id="38cc7-345">**Optional**</span></span>

<span data-ttu-id="38cc7-346">Der `connectors` Block definiert einen Office 365-Konnektor für die app.</span><span class="sxs-lookup"><span data-stu-id="38cc7-346">The `connectors` block defines an Office 365 Connector for the app.</span></span>

<span data-ttu-id="38cc7-347">Das Objekt ist ein Array (Maximum of 1-Element) mit allen Elementen des `object`Typs.</span><span class="sxs-lookup"><span data-stu-id="38cc7-347">The object is an array (maximum of 1 element) with all elements of type `object`.</span></span> <span data-ttu-id="38cc7-348">Dieser Block ist nur für Lösungen erforderlich, die einen Connector bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="38cc7-348">This block is required only for solutions that provide a Connector.</span></span>

|<span data-ttu-id="38cc7-349">Name</span><span class="sxs-lookup"><span data-stu-id="38cc7-349">Name</span></span>| <span data-ttu-id="38cc7-350">Typ</span><span class="sxs-lookup"><span data-stu-id="38cc7-350">Type</span></span>| <span data-ttu-id="38cc7-351">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="38cc7-351">Maximum size</span></span> | <span data-ttu-id="38cc7-352">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="38cc7-352">Required</span></span> | <span data-ttu-id="38cc7-353">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="38cc7-353">Description</span></span>|
|---|---|---|---|---|
|`configurationUrl`|<span data-ttu-id="38cc7-354">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="38cc7-354">String</span></span>|<span data-ttu-id="38cc7-355">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="38cc7-355">2048 characters</span></span>|<span data-ttu-id="38cc7-356">✔</span><span class="sxs-lookup"><span data-stu-id="38cc7-356">✔</span></span>|<span data-ttu-id="38cc7-357">Die https://-URL, die beim Konfigurieren des Connectors verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="38cc7-357">The https:// URL to use when configuring the connector.</span></span>|
|`connectorId`|<span data-ttu-id="38cc7-358">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="38cc7-358">String</span></span>|<span data-ttu-id="38cc7-359">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="38cc7-359">64 characters</span></span>|<span data-ttu-id="38cc7-360">✔</span><span class="sxs-lookup"><span data-stu-id="38cc7-360">✔</span></span>|<span data-ttu-id="38cc7-361">Ein eindeutiger Bezeichner für den Connector, der seiner ID im [Entwickler Dashboard für Connectors](https://aka.ms/connectorsdashboard)entspricht.</span><span class="sxs-lookup"><span data-stu-id="38cc7-361">A unique identifier for the Connector that matches its ID in the [Connectors Developer Dashboard](https://aka.ms/connectorsdashboard).</span></span>|
|`scopes`|<span data-ttu-id="38cc7-362">Array von Enum</span><span class="sxs-lookup"><span data-stu-id="38cc7-362">Array of enum</span></span>|<span data-ttu-id="38cc7-363">1 </span><span class="sxs-lookup"><span data-stu-id="38cc7-363">1</span></span>|<span data-ttu-id="38cc7-364">✔</span><span class="sxs-lookup"><span data-stu-id="38cc7-364">✔</span></span>|<span data-ttu-id="38cc7-365">Gibt an, ob der Connector eine Erfahrung im Kontext eines Kanals in a `team`bietet oder ein Erlebnis, das allein auf einen einzelnen Benutzer beschränkt`personal`ist ().</span><span class="sxs-lookup"><span data-stu-id="38cc7-365">Specifies whether the Connector offers an experience in the context of a channel in a `team`, or an experience scoped to an individual user alone (`personal`).</span></span> <span data-ttu-id="38cc7-366">Derzeit wird nur der `team` Bereich unterstützt.</span><span class="sxs-lookup"><span data-stu-id="38cc7-366">Currently, only the `team` scope is supported.</span></span>|

## <a name="composeextensions"></a><span data-ttu-id="38cc7-367">composeExtensions</span><span class="sxs-lookup"><span data-stu-id="38cc7-367">composeExtensions</span></span>

<span data-ttu-id="38cc7-368">**Optional**</span><span class="sxs-lookup"><span data-stu-id="38cc7-368">**Optional**</span></span>

<span data-ttu-id="38cc7-369">Definiert eine Messaging Erweiterung für die app.</span><span class="sxs-lookup"><span data-stu-id="38cc7-369">Defines a messaging extension for the app.</span></span>

> [!NOTE]
> <span data-ttu-id="38cc7-370">Der Name des Features wurde von "Erstell Erweiterung" in "Messaging Extension" im November 2017 geändert, aber der Manifestname bleibt unverändert, sodass vorhandene Erweiterungen weiterhin funktionieren.</span><span class="sxs-lookup"><span data-stu-id="38cc7-370">The name of the feature was changed from "compose extension" to "messaging extension" in November, 2017, but the manifest name remains the same so that existing extensions continue to function.</span></span>

<span data-ttu-id="38cc7-371">Das Objekt ist ein Array (Maximum of 1-Element) mit allen Elementen des `object`Typs.</span><span class="sxs-lookup"><span data-stu-id="38cc7-371">The object is an array (maximum of 1 element) with all elements of type `object`.</span></span> <span data-ttu-id="38cc7-372">Dieser Block ist nur für Lösungen erforderlich, die eine Messaging Erweiterung bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="38cc7-372">This block is required only for solutions that provide a messaging extension.</span></span>

|<span data-ttu-id="38cc7-373">Name</span><span class="sxs-lookup"><span data-stu-id="38cc7-373">Name</span></span>| <span data-ttu-id="38cc7-374">Typ</span><span class="sxs-lookup"><span data-stu-id="38cc7-374">Type</span></span> | <span data-ttu-id="38cc7-375">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="38cc7-375">Maximum Size</span></span> | <span data-ttu-id="38cc7-376">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="38cc7-376">Required</span></span> | <span data-ttu-id="38cc7-377">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="38cc7-377">Description</span></span>|
|---|---|---|---|---|
|`botId`|<span data-ttu-id="38cc7-378">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="38cc7-378">String</span></span>|<span data-ttu-id="38cc7-379">64</span><span class="sxs-lookup"><span data-stu-id="38cc7-379">64</span></span>|<span data-ttu-id="38cc7-380">✔</span><span class="sxs-lookup"><span data-stu-id="38cc7-380">✔</span></span>|<span data-ttu-id="38cc7-381">Die eindeutige Microsoft-App-ID für den bot, der die Messaging Erweiterung unterstützt, wie Sie mit dem bot-Framework registriert wurde.</span><span class="sxs-lookup"><span data-stu-id="38cc7-381">The unique Microsoft app ID for the bot that backs the messaging extension, as registered with the Bot Framework.</span></span> <span data-ttu-id="38cc7-382">Dies kann auch die gesamte [App-ID](#id)entsprechen.</span><span class="sxs-lookup"><span data-stu-id="38cc7-382">This may well be the same as the overall [app ID](#id).</span></span>|
|`canUpdateConfiguration`|<span data-ttu-id="38cc7-383">Boolesch</span><span class="sxs-lookup"><span data-stu-id="38cc7-383">Boolean</span></span>|||<span data-ttu-id="38cc7-384">Ein Wert, der angibt, ob die Konfiguration einer Messaging Erweiterung vom Benutzer aktualisiert werden kann.</span><span class="sxs-lookup"><span data-stu-id="38cc7-384">A value indicating whether the configuration of a messaging extension can be updated by the user.</span></span> <span data-ttu-id="38cc7-385">Der Standardwert `false`ist.</span><span class="sxs-lookup"><span data-stu-id="38cc7-385">The default is `false`.</span></span>|
|`commands`|<span data-ttu-id="38cc7-386">Array von Object</span><span class="sxs-lookup"><span data-stu-id="38cc7-386">Array of object</span></span>|<span data-ttu-id="38cc7-387">10  </span><span class="sxs-lookup"><span data-stu-id="38cc7-387">10</span></span>|<span data-ttu-id="38cc7-388">✔</span><span class="sxs-lookup"><span data-stu-id="38cc7-388">✔</span></span>|<span data-ttu-id="38cc7-389">Array von Befehlen, die von der Messaging-Erweiterung unterstützt werden</span><span class="sxs-lookup"><span data-stu-id="38cc7-389">Array of commands the messaging extension supports</span></span>|

### <a name="composeextensionscommands"></a><span data-ttu-id="38cc7-390">composeExtensions. Commands</span><span class="sxs-lookup"><span data-stu-id="38cc7-390">composeExtensions.commands</span></span>

<span data-ttu-id="38cc7-391">Ihre Messaging Erweiterung sollte einen oder mehrere Befehle deklarieren.</span><span class="sxs-lookup"><span data-stu-id="38cc7-391">Your messaging extension should declare one or more commands.</span></span> <span data-ttu-id="38cc7-392">Jeder Befehl wird in Microsoft Teams als potenzielle Interaktion aus dem Benutzeroberflächen basierten Einstiegspfad angezeigt.</span><span class="sxs-lookup"><span data-stu-id="38cc7-392">Each command appears in Microsoft Teams as a potential interaction from the UI-based entry point.</span></span> <span data-ttu-id="38cc7-393">Es gibt maximal 10 Befehle.</span><span class="sxs-lookup"><span data-stu-id="38cc7-393">There is a maximum of 10 commands.</span></span>

<span data-ttu-id="38cc7-394">Jedes Command-Element ist ein Objekt mit der folgenden Struktur:</span><span class="sxs-lookup"><span data-stu-id="38cc7-394">Each command item is an object with the following structure:</span></span>

|<span data-ttu-id="38cc7-395">Name</span><span class="sxs-lookup"><span data-stu-id="38cc7-395">Name</span></span>| <span data-ttu-id="38cc7-396">Typ</span><span class="sxs-lookup"><span data-stu-id="38cc7-396">Type</span></span>| <span data-ttu-id="38cc7-397">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="38cc7-397">Maximum size</span></span> | <span data-ttu-id="38cc7-398">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="38cc7-398">Required</span></span> | <span data-ttu-id="38cc7-399">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="38cc7-399">Description</span></span>|
|---|---|---|---|---|
|`id`|<span data-ttu-id="38cc7-400">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="38cc7-400">String</span></span>|<span data-ttu-id="38cc7-401">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="38cc7-401">64 characters</span></span>|<span data-ttu-id="38cc7-402">✔</span><span class="sxs-lookup"><span data-stu-id="38cc7-402">✔</span></span>|<span data-ttu-id="38cc7-403">Die ID für den Befehl</span><span class="sxs-lookup"><span data-stu-id="38cc7-403">The ID for the command</span></span>|
|`type`|<span data-ttu-id="38cc7-404">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="38cc7-404">String</span></span>|<span data-ttu-id="38cc7-405">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="38cc7-405">64 characters</span></span>||<span data-ttu-id="38cc7-406">Der Typ des Befehls.</span><span class="sxs-lookup"><span data-stu-id="38cc7-406">Type of the command.</span></span> <span data-ttu-id="38cc7-407">Einer von `query` oder `action`.</span><span class="sxs-lookup"><span data-stu-id="38cc7-407">One of `query` or `action`.</span></span> <span data-ttu-id="38cc7-408">Standard`query`</span><span class="sxs-lookup"><span data-stu-id="38cc7-408">Default: `query`</span></span>|
|`title`|<span data-ttu-id="38cc7-409">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="38cc7-409">String</span></span>|<span data-ttu-id="38cc7-410">32 Zeichen</span><span class="sxs-lookup"><span data-stu-id="38cc7-410">32 characters</span></span>|<span data-ttu-id="38cc7-411">✔</span><span class="sxs-lookup"><span data-stu-id="38cc7-411">✔</span></span>|<span data-ttu-id="38cc7-412">Der benutzerfreundliche Befehlsname</span><span class="sxs-lookup"><span data-stu-id="38cc7-412">The user-friendly command name</span></span>|
|`description`|<span data-ttu-id="38cc7-413">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="38cc7-413">String</span></span>|<span data-ttu-id="38cc7-414">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="38cc7-414">128 characters</span></span>||<span data-ttu-id="38cc7-415">Die Beschreibung, die den Benutzern angezeigt wird, um den Zweck dieses Befehls anzugeben</span><span class="sxs-lookup"><span data-stu-id="38cc7-415">The description that appears to users to indicate the purpose of this command</span></span>|
|`initialRun`|<span data-ttu-id="38cc7-416">Boolesch</span><span class="sxs-lookup"><span data-stu-id="38cc7-416">Boolean</span></span>|||<span data-ttu-id="38cc7-417">Ein boolescher Wert, der angibt, ob der Befehl anfänglich ohne Parameter ausgeführt werden soll.</span><span class="sxs-lookup"><span data-stu-id="38cc7-417">A Boolean value that indicates whether the command should be run initially with no parameters.</span></span> <span data-ttu-id="38cc7-418">Standard`false`</span><span class="sxs-lookup"><span data-stu-id="38cc7-418">Default: `false`</span></span>|
|`context`|<span data-ttu-id="38cc7-419">Array von Zeichenfolgen</span><span class="sxs-lookup"><span data-stu-id="38cc7-419">Array of Strings</span></span>|<span data-ttu-id="38cc7-420">3 </span><span class="sxs-lookup"><span data-stu-id="38cc7-420">3</span></span>||<span data-ttu-id="38cc7-421">Definiert, woher die Nachrichten Erweiterung aufgerufen werden kann.</span><span class="sxs-lookup"><span data-stu-id="38cc7-421">Defines where the message extension can be invoked from.</span></span> <span data-ttu-id="38cc7-422">Eine beliebige Kombi `compose`Nation `commandBox`von `message`,,.</span><span class="sxs-lookup"><span data-stu-id="38cc7-422">Any combination of `compose`, `commandBox`, `message`.</span></span> <span data-ttu-id="38cc7-423">Der Standardwert ist`["compose", "commandBox"]`</span><span class="sxs-lookup"><span data-stu-id="38cc7-423">Default is `["compose", "commandBox"]`</span></span>|
|`fetchTask`|<span data-ttu-id="38cc7-424">Boolesch</span><span class="sxs-lookup"><span data-stu-id="38cc7-424">Boolean</span></span>|||<span data-ttu-id="38cc7-425">Ein boolescher Wert, der angibt, ob das Aufgabenmodul dynamisch abgerufen werden soll.</span><span class="sxs-lookup"><span data-stu-id="38cc7-425">A boolean value that indicates if it should fetch the task module dynamically</span></span>|
|`taskInfo`|<span data-ttu-id="38cc7-426">Object</span><span class="sxs-lookup"><span data-stu-id="38cc7-426">Object</span></span>|||<span data-ttu-id="38cc7-427">Angeben des Aufgabenmoduls, das beim Verwenden eines Messaging Erweiterungs Befehls geladen werden soll</span><span class="sxs-lookup"><span data-stu-id="38cc7-427">Specify the task module to preload when using a messaging extension command</span></span>|
|`taskInfo.title`|<span data-ttu-id="38cc7-428">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="38cc7-428">String</span></span>|<span data-ttu-id="38cc7-429">64</span><span class="sxs-lookup"><span data-stu-id="38cc7-429">64</span></span>||<span data-ttu-id="38cc7-430">Ursprünglicher Dialogtitel</span><span class="sxs-lookup"><span data-stu-id="38cc7-430">Initial dialog title</span></span>|
|`taskInfo.width`|<span data-ttu-id="38cc7-431">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="38cc7-431">String</span></span>|||<span data-ttu-id="38cc7-432">Dialog Breite-entweder eine Zahl in Pixel oder ein Standardlayout wie "groß", "Mittel" oder "klein"</span><span class="sxs-lookup"><span data-stu-id="38cc7-432">Dialog width - either a number in pixels or default layout such as 'large', 'medium', or 'small'</span></span>|
|`taskInfo.height`|<span data-ttu-id="38cc7-433">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="38cc7-433">String</span></span>|||<span data-ttu-id="38cc7-434">Dialog Feld Höhe-entweder eine Zahl in Pixel oder ein Standardlayout wie "groß", "Mittel" oder "klein"</span><span class="sxs-lookup"><span data-stu-id="38cc7-434">Dialog height - either a number in pixels or default layout such as 'large', 'medium', or 'small'</span></span>|
|`taskInfo.url`|<span data-ttu-id="38cc7-435">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="38cc7-435">String</span></span>|||<span data-ttu-id="38cc7-436">Anfängliche WebView-URL</span><span class="sxs-lookup"><span data-stu-id="38cc7-436">Initial webview URL</span></span>|
|`messageHandlers`|<span data-ttu-id="38cc7-437">Array von Objekten</span><span class="sxs-lookup"><span data-stu-id="38cc7-437">Array of Objects</span></span>|<span data-ttu-id="38cc7-438">5 </span><span class="sxs-lookup"><span data-stu-id="38cc7-438">5</span></span>||<span data-ttu-id="38cc7-439">Eine Liste von Handlern, mit denen apps aufgerufen werden können, wenn bestimmte Bedingungen erfüllt sind.</span><span class="sxs-lookup"><span data-stu-id="38cc7-439">A list of handlers that allow apps to be invoked when certain conditions are met.</span></span> <span data-ttu-id="38cc7-440">Domänen müssen ebenfalls in aufgeführt sein.`validDomains`</span><span class="sxs-lookup"><span data-stu-id="38cc7-440">Domains must also be listed in `validDomains`</span></span>|
|`messageHandlers.type`|<span data-ttu-id="38cc7-441">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="38cc7-441">String</span></span>|||<span data-ttu-id="38cc7-442">Der Typ des Nachrichten Handlers.</span><span class="sxs-lookup"><span data-stu-id="38cc7-442">The type of message handler.</span></span> <span data-ttu-id="38cc7-443">Muss `"link"` sein.</span><span class="sxs-lookup"><span data-stu-id="38cc7-443">Must be `"link"`.</span></span>|
|`messageHandlers.value.domains`|<span data-ttu-id="38cc7-444">Array von Zeichenfolgen</span><span class="sxs-lookup"><span data-stu-id="38cc7-444">Array of Strings</span></span>|||<span data-ttu-id="38cc7-445">Array von Domänen, für die der Link Nachrichtenhandler registriert werden kann.</span><span class="sxs-lookup"><span data-stu-id="38cc7-445">Array of domains that the link message handler can register for.</span></span>|
|`parameters`|<span data-ttu-id="38cc7-446">Array von Object</span><span class="sxs-lookup"><span data-stu-id="38cc7-446">Array of object</span></span>|<span data-ttu-id="38cc7-447">5 </span><span class="sxs-lookup"><span data-stu-id="38cc7-447">5</span></span>|<span data-ttu-id="38cc7-448">✔</span><span class="sxs-lookup"><span data-stu-id="38cc7-448">✔</span></span>|<span data-ttu-id="38cc7-449">Die Liste der Parameter, die der Befehl benötigt.</span><span class="sxs-lookup"><span data-stu-id="38cc7-449">The list of parameters the command takes.</span></span> <span data-ttu-id="38cc7-450">Minimum: 1; Maximum: 5</span><span class="sxs-lookup"><span data-stu-id="38cc7-450">Minimum: 1; maximum: 5</span></span>|
|`parameter.name`|<span data-ttu-id="38cc7-451">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="38cc7-451">String</span></span>|<span data-ttu-id="38cc7-452">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="38cc7-452">64 characters</span></span>|<span data-ttu-id="38cc7-453">✔</span><span class="sxs-lookup"><span data-stu-id="38cc7-453">✔</span></span>|<span data-ttu-id="38cc7-454">Der Name des Parameters, wie er im Client angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="38cc7-454">The name of the parameter as it appears in the client.</span></span> <span data-ttu-id="38cc7-455">Dies ist in der Benutzeranforderung enthalten.</span><span class="sxs-lookup"><span data-stu-id="38cc7-455">This is included in the user request.</span></span>|
|`parameter.title`|<span data-ttu-id="38cc7-456">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="38cc7-456">String</span></span>|<span data-ttu-id="38cc7-457">32 Zeichen</span><span class="sxs-lookup"><span data-stu-id="38cc7-457">32 characters</span></span>|<span data-ttu-id="38cc7-458">✔</span><span class="sxs-lookup"><span data-stu-id="38cc7-458">✔</span></span>|<span data-ttu-id="38cc7-459">Benutzerfreundlicher Titel für den Parameter.</span><span class="sxs-lookup"><span data-stu-id="38cc7-459">User-friendly title for the parameter.</span></span>|
|`parameter.description`|<span data-ttu-id="38cc7-460">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="38cc7-460">String</span></span>|<span data-ttu-id="38cc7-461">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="38cc7-461">128 characters</span></span>||<span data-ttu-id="38cc7-462">Benutzerfreundliche Zeichenfolge, die den Zweck dieses Parameters beschreibt.</span><span class="sxs-lookup"><span data-stu-id="38cc7-462">User-friendly string that describes this parameter’s purpose.</span></span>|
|`parameter.inputType`|<span data-ttu-id="38cc7-463">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="38cc7-463">String</span></span>|<span data-ttu-id="38cc7-464">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="38cc7-464">128 characters</span></span>||<span data-ttu-id="38cc7-465">Definiert den Typ des Steuerelements, das in einem Aufgaben `fetchTask: true`Modul für angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="38cc7-465">Defines the type of control displayed on a task module for `fetchTask: true`.</span></span> <span data-ttu-id="38cc7-466">Eine von `text`, `textarea`, `number`, `date`, `time`, `toggle`,`choiceset`</span><span class="sxs-lookup"><span data-stu-id="38cc7-466">One of `text`, `textarea`, `number`, `date`, `time`, `toggle`, `choiceset`</span></span>|
|`parameter.choices`|<span data-ttu-id="38cc7-467">Array von Objekten</span><span class="sxs-lookup"><span data-stu-id="38cc7-467">Array of Objects</span></span>|<span data-ttu-id="38cc7-468">10  </span><span class="sxs-lookup"><span data-stu-id="38cc7-468">10</span></span>||<span data-ttu-id="38cc7-469">Die Auswahloptionen für `choiceset`.</span><span class="sxs-lookup"><span data-stu-id="38cc7-469">The choice options for the `choiceset`.</span></span> <span data-ttu-id="38cc7-470">Nur verwenden, `parameter.inputType` wenn`choiceset`</span><span class="sxs-lookup"><span data-stu-id="38cc7-470">Use only when `parameter.inputType` is `choiceset`</span></span>|
|`parameter.choices.title`|<span data-ttu-id="38cc7-471">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="38cc7-471">String</span></span>|<span data-ttu-id="38cc7-472">128</span><span class="sxs-lookup"><span data-stu-id="38cc7-472">128</span></span>||<span data-ttu-id="38cc7-473">Titel der Auswahl</span><span class="sxs-lookup"><span data-stu-id="38cc7-473">Title of the choice</span></span>|
|`parameter.choices.value`|<span data-ttu-id="38cc7-474">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="38cc7-474">String</span></span>|<span data-ttu-id="38cc7-475">512</span><span class="sxs-lookup"><span data-stu-id="38cc7-475">512</span></span>||<span data-ttu-id="38cc7-476">Wert der Auswahl</span><span class="sxs-lookup"><span data-stu-id="38cc7-476">Value of the choice</span></span>|

## <a name="permissions"></a><span data-ttu-id="38cc7-477">Berechtigungen</span><span class="sxs-lookup"><span data-stu-id="38cc7-477">permissions</span></span>

<span data-ttu-id="38cc7-478">**Optional**</span><span class="sxs-lookup"><span data-stu-id="38cc7-478">**Optional**</span></span>

<span data-ttu-id="38cc7-479">Ein Array `string` , das angibt, welche Berechtigungen die APP anfordert, sodass Endbenutzer wissen, wie die Erweiterung ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="38cc7-479">An array of `string` which specifies which permissions the app requests, which lets end users know how the extension will perform.</span></span> <span data-ttu-id="38cc7-480">Die folgenden Optionen sind nicht exklusiv:</span><span class="sxs-lookup"><span data-stu-id="38cc7-480">The following options are non-exclusive:</span></span>

* <span data-ttu-id="38cc7-481">`identity`&emsp; Erfordert Benutzeridentitätsinformationen</span><span class="sxs-lookup"><span data-stu-id="38cc7-481">`identity` &emsp; Requires user identity information</span></span>
* <span data-ttu-id="38cc7-482">`messageTeamMembers`&emsp; Erfordert die Berechtigung zum Senden von direkten Nachrichten an Teammitglieder.</span><span class="sxs-lookup"><span data-stu-id="38cc7-482">`messageTeamMembers` &emsp; Requires permission to send direct messages to team members</span></span>

<span data-ttu-id="38cc7-483">Wenn Sie diese Berechtigungen beim Aktualisieren Ihrer APP ändern, werden die Benutzer beim ersten Ausführen der aktualisierten App den Zustimmungsprozess wiederholen.</span><span class="sxs-lookup"><span data-stu-id="38cc7-483">Changing these permissions when updating your app will cause your users to repeat the consent process the first time they run the updated app.</span></span>

## <a name="devicepermissions"></a><span data-ttu-id="38cc7-484">devicePermissions</span><span class="sxs-lookup"><span data-stu-id="38cc7-484">devicePermissions</span></span>

<span data-ttu-id="38cc7-485">**Optional** Array von Zeichenfolgen</span><span class="sxs-lookup"><span data-stu-id="38cc7-485">**Optional** Array of Strings</span></span>

<span data-ttu-id="38cc7-486">Gibt die systemeigenen Funktionen auf dem Gerät eines Benutzers an, für die Ihre APP möglicherweise Zugriff anfordern kann.</span><span class="sxs-lookup"><span data-stu-id="38cc7-486">Specifies the native features on a user's device that your app may request access to.</span></span> <span data-ttu-id="38cc7-487">Die Optionen lauten wie folgt:</span><span class="sxs-lookup"><span data-stu-id="38cc7-487">Options are:</span></span>

* `geolocation`
* `media`
* `notifications`
* `midi`
* `openExternal`

## <a name="validdomains"></a><span data-ttu-id="38cc7-488">validDomains</span><span class="sxs-lookup"><span data-stu-id="38cc7-488">validDomains</span></span>

<span data-ttu-id="38cc7-489">**Optional**, sofern angegeben, außer **erforderlich**</span><span class="sxs-lookup"><span data-stu-id="38cc7-489">**Optional**, except **Required** where noted</span></span>

<span data-ttu-id="38cc7-490">Eine Liste gültiger Domänen, von denen die APP erwartet, dass Sie Inhalte lädt.</span><span class="sxs-lookup"><span data-stu-id="38cc7-490">A list of valid domains from which the app expects to load any content.</span></span> <span data-ttu-id="38cc7-491">Domänen Auflistungen können beispielsweise `*.example.com`Platzhalterzeichen enthalten.</span><span class="sxs-lookup"><span data-stu-id="38cc7-491">Domain listings can include wildcards, for example `*.example.com`.</span></span> <span data-ttu-id="38cc7-492">Dies entspricht genau einem Segment der Domäne. Wenn Sie eine Übereinstimmung `a.b.example.com` benötigen, `*.*.example.com`verwenden Sie.</span><span class="sxs-lookup"><span data-stu-id="38cc7-492">This matches exactly one segment of the domain; if you need to match `a.b.example.com` then use `*.*.example.com`.</span></span> <span data-ttu-id="38cc7-493">Wenn Ihre Registerkartenkonfiguration oder Inhalts-UI neben einer Verwendung für die Registerkartenkonfiguration zu einer anderen Domäne navigieren muss, muss diese Domäne hier angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="38cc7-493">If your tab configuration or content UI needs to navigate to any other domain besides the one use for tab configuration, that domain must be specified here.</span></span>

<span data-ttu-id="38cc7-494">Es ist jedoch **nicht** erforderlich, die Domänen von Identitätsanbietern einzubeziehen, die Sie in Ihrer APP unterstützen möchten.</span><span class="sxs-lookup"><span data-stu-id="38cc7-494">It is **not** necessary to include the domains of identity providers you want to support in your app, however.</span></span> <span data-ttu-id="38cc7-495">Um beispielsweise mit einer Google-ID zu authentifizieren, müssen Sie zu Accounts.Google.com umgeleitet werden, aber Sie sollten Accounts.Google.com nicht in `validDomains[]`einschließen.</span><span class="sxs-lookup"><span data-stu-id="38cc7-495">For example, to authenticate using a Google ID, it's necessary to redirect to accounts.google.com, but you should not include accounts.google.com in `validDomains[]`.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="38cc7-496">Fügen Sie keine Domänen hinzu, die sich außerhalb des Steuerelements befinden, entweder direkt oder über Platzhalter.</span><span class="sxs-lookup"><span data-stu-id="38cc7-496">Do not add domains that are outside your control, either directly or via wildcards.</span></span> <span data-ttu-id="38cc7-497">Beispielsweise `yourapp.onmicrosoft.com` ist gültig, jedoch `*.onmicrosoft.com` ungültig.</span><span class="sxs-lookup"><span data-stu-id="38cc7-497">For example, `yourapp.onmicrosoft.com` is valid, but `*.onmicrosoft.com` is not valid.</span></span>

<span data-ttu-id="38cc7-498">Das Objekt ist ein Array mit allen Elementen des Typs `string`.</span><span class="sxs-lookup"><span data-stu-id="38cc7-498">The object is an array with all elements of the type `string`.</span></span>

## <a name="webapplicationinfo"></a><span data-ttu-id="38cc7-499">webApplicationInfo</span><span class="sxs-lookup"><span data-stu-id="38cc7-499">webApplicationInfo</span></span>

<span data-ttu-id="38cc7-500">**Optional**</span><span class="sxs-lookup"><span data-stu-id="38cc7-500">**Optional**</span></span>

<span data-ttu-id="38cc7-501">Geben Sie Ihre Aad-APP-ID und Diagramm Informationen an, damit Benutzer sich nahtlos bei ihrer Aad-App anmelden können.</span><span class="sxs-lookup"><span data-stu-id="38cc7-501">Specify your AAD App ID and Graph information to help users seamlessly sign into your AAD app.</span></span>

|<span data-ttu-id="38cc7-502">Name</span><span class="sxs-lookup"><span data-stu-id="38cc7-502">Name</span></span>| <span data-ttu-id="38cc7-503">Typ</span><span class="sxs-lookup"><span data-stu-id="38cc7-503">Type</span></span>| <span data-ttu-id="38cc7-504">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="38cc7-504">Maximum size</span></span> | <span data-ttu-id="38cc7-505">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="38cc7-505">Required</span></span> | <span data-ttu-id="38cc7-506">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="38cc7-506">Description</span></span>|
|---|---|---|---|---|
|`id`|<span data-ttu-id="38cc7-507">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="38cc7-507">String</span></span>|<span data-ttu-id="38cc7-508">36 Zeichen</span><span class="sxs-lookup"><span data-stu-id="38cc7-508">36 characters</span></span>|<span data-ttu-id="38cc7-509">✔</span><span class="sxs-lookup"><span data-stu-id="38cc7-509">✔</span></span>|<span data-ttu-id="38cc7-510">Aad-Anwendungs-ID der app.</span><span class="sxs-lookup"><span data-stu-id="38cc7-510">AAD application id of the app.</span></span> <span data-ttu-id="38cc7-511">Diese ID muss eine GUID sein.</span><span class="sxs-lookup"><span data-stu-id="38cc7-511">This id must be a GUID.</span></span>|
|`resource`|<span data-ttu-id="38cc7-512">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="38cc7-512">String</span></span>|<span data-ttu-id="38cc7-513">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="38cc7-513">2048 characters</span></span>|<span data-ttu-id="38cc7-514">✔</span><span class="sxs-lookup"><span data-stu-id="38cc7-514">✔</span></span>|<span data-ttu-id="38cc7-515">Ressourcen-URL der APP zum Abrufen des Authentifizierungstokens für SSO.</span><span class="sxs-lookup"><span data-stu-id="38cc7-515">Resource url of app for acquiring auth token for SSO.</span></span>|