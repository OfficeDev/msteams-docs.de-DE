---
title: Manifest-Schemareferenz
description: Beschreibt das vom Manifest für Microsoft Teams unterstützte Schema.
keywords: Team Manifest-Schema
ms.openlocfilehash: d4a2864c18a5066673bafab42a46733a0ab5f116
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674357"
---
# <a name="reference-manifest-schema-for-microsoft-teams"></a><span data-ttu-id="74dbe-104">Referenz: Manifest-Schema für Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="74dbe-104">Reference: Manifest schema for Microsoft Teams</span></span>

<span data-ttu-id="74dbe-105">Das Microsoft Teams-Manifest beschreibt, wie die app in das Microsoft Teams-Produkt integriert wird.</span><span class="sxs-lookup"><span data-stu-id="74dbe-105">The Microsoft Teams manifest describes how the app integrates into the Microsoft Teams product.</span></span> <span data-ttu-id="74dbe-106">Das Manifest muss dem Schema entsprechen, das unter [`https://developer.microsoft.com/json-schemas/teams/v1.5/MicrosoftTeams.schema.json`]( https://developer.microsoft.com/json-schemas/teams/v1.5/MicrosoftTeams.schema.json)gehostet wird.</span><span class="sxs-lookup"><span data-stu-id="74dbe-106">Your manifest must conform to the schema hosted at [`https://developer.microsoft.com/json-schemas/teams/v1.5/MicrosoftTeams.schema.json`]( https://developer.microsoft.com/json-schemas/teams/v1.5/MicrosoftTeams.schema.json).</span></span> <span data-ttu-id="74dbe-107">Frühere Versionen 1.0-1.4 werden ebenfalls unterstützt (mit "v1. x" in der URL).</span><span class="sxs-lookup"><span data-stu-id="74dbe-107">Previous versions 1.0-1.4 are also supported (using "v1.x" in the URL).</span></span>

<span data-ttu-id="74dbe-108">Das folgende Schemabeispiel zeigt alle Erweiterungsoptionen.</span><span class="sxs-lookup"><span data-stu-id="74dbe-108">The following schema sample shows all extensibility options.</span></span>

## <a name="sample-full-manifest"></a><span data-ttu-id="74dbe-109">Vollständiges Beispiel Manifest</span><span class="sxs-lookup"><span data-stu-id="74dbe-109">Sample full manifest</span></span>

```json
{
  "$schema": "https://developer.microsoft.com/json-schemas/teams/v1.5/MicrosoftTeams.schema.json",
  "manifestVersion": "1.5",
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
    "defaultLanguageTag": "en-us",
    "additionalLanguages": [
      {
        "languageTag": "es-es",
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
        }
      ],
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
  ],
  "permissions": [
    "identity",
    "messageTeamMembers"
  ],
  "validDomains": [
     "contoso.com",
     "mysite.someplace.com",
     "othersite.someplace.com"
  ]
}
```

<span data-ttu-id="74dbe-110">Das Schema definiert die folgenden Eigenschaften:</span><span class="sxs-lookup"><span data-stu-id="74dbe-110">The schema defines the following properties:</span></span>

## <a name="schema"></a><span data-ttu-id="74dbe-111">$schema</span><span class="sxs-lookup"><span data-stu-id="74dbe-111">$schema</span></span>

<span data-ttu-id="74dbe-112">*Optionale, aber empfohlene* &ndash; Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="74dbe-112">*Optional, but recommended* &ndash; String</span></span>

<span data-ttu-id="74dbe-113">Die https://-URL, die auf das JSON-Schema für das Manifest verweist.</span><span class="sxs-lookup"><span data-stu-id="74dbe-113">The https:// URL referencing the JSON Schema for the manifest.</span></span>

## <a name="manifestversion"></a><span data-ttu-id="74dbe-114">manifestVersion</span><span class="sxs-lookup"><span data-stu-id="74dbe-114">manifestVersion</span></span>

<span data-ttu-id="74dbe-115">**Erforderliche** &ndash; Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="74dbe-115">**Required** &ndash; String</span></span>

<span data-ttu-id="74dbe-116">Die Version des manifest-Schemas, die dieses Manifest verwendet.</span><span class="sxs-lookup"><span data-stu-id="74dbe-116">The version of the manifest schema this manifest is using.</span></span> <span data-ttu-id="74dbe-117">Es sollte "1,5" sein.</span><span class="sxs-lookup"><span data-stu-id="74dbe-117">It should be "1.5".</span></span>

## <a name="version"></a><span data-ttu-id="74dbe-118">Version</span><span class="sxs-lookup"><span data-stu-id="74dbe-118">version</span></span>

<span data-ttu-id="74dbe-119">**Erforderliche** &ndash; Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="74dbe-119">**Required** &ndash; String</span></span>

<span data-ttu-id="74dbe-120">Die Version der jeweiligen App.</span><span class="sxs-lookup"><span data-stu-id="74dbe-120">The version of the specific app.</span></span> <span data-ttu-id="74dbe-121">Wenn Sie etwas in ihrem Manifest aktualisieren, muss die Version ebenfalls inkrementiert werden.</span><span class="sxs-lookup"><span data-stu-id="74dbe-121">If you update something in your manifest, the version must be incremented as well.</span></span> <span data-ttu-id="74dbe-122">Auf diese Weise wird bei der Installation des neuen Manifests das vorhandene überschrieben, und der Benutzer erhält die neue Funktionalität.</span><span class="sxs-lookup"><span data-stu-id="74dbe-122">This way, when the new manifest is installed, it will overwrite the existing one and the user will get the new functionality.</span></span> <span data-ttu-id="74dbe-123">Wenn diese APP an den Store übermittelt wurde, muss das neue Manifest erneut übermittelt und erneut validiert werden.</span><span class="sxs-lookup"><span data-stu-id="74dbe-123">If this app was submitted to the store, the new manifest will have to be re-submitted and re-validated.</span></span> <span data-ttu-id="74dbe-124">Dann erhalten Benutzer dieser APP das neue aktualisierte Manifest automatisch in ein paar Stunden, nachdem es genehmigt wurde.</span><span class="sxs-lookup"><span data-stu-id="74dbe-124">Then, users of this app will get the new updated manifest automatically in a few hours, after it is approved.</span></span>

<span data-ttu-id="74dbe-125">Wenn sich die angeforderte APP geändert hat, werden die Benutzer aufgefordert, die APP zu aktualisieren und erneut zu genehmigen.</span><span class="sxs-lookup"><span data-stu-id="74dbe-125">If the app requested permissions change, users will be prompted to upgrade and re-consent to the app.</span></span>

<span data-ttu-id="74dbe-126">Diese Versionszeichenfolge muss dem [semver](http://semver.org/) -Standard (Major) entsprechen. Moll. Patch).</span><span class="sxs-lookup"><span data-stu-id="74dbe-126">This version string must follow the [semver](http://semver.org/) standard (MAJOR.MINOR.PATCH).</span></span>

## <a name="id"></a><span data-ttu-id="74dbe-127">id</span><span class="sxs-lookup"><span data-stu-id="74dbe-127">id</span></span>

<span data-ttu-id="74dbe-128">**Erforderliche** &ndash; Microsoft-App-ID</span><span class="sxs-lookup"><span data-stu-id="74dbe-128">**Required** &ndash; Microsoft app ID</span></span>

<span data-ttu-id="74dbe-129">Der eindeutige von Microsoft generierte Bezeichner für diese APP.</span><span class="sxs-lookup"><span data-stu-id="74dbe-129">The unique Microsoft-generated identifier for this app.</span></span> <span data-ttu-id="74dbe-130">Wenn Sie einen bot über das Microsoft bot-Framework registriert haben oder sich die Webanwendung Ihrer Registerkarte bereits bei Microsoft anmeldet, sollten Sie bereits über eine ID verfügen und diese hier eingeben.</span><span class="sxs-lookup"><span data-stu-id="74dbe-130">If you have registered a bot via the Microsoft Bot Framework, or your tab's web app already signs in with Microsoft, you should already have an ID and should enter it here.</span></span> <span data-ttu-id="74dbe-131">Andernfalls sollten Sie eine neue ID im Microsoft-Anwendungs Registrierungs Portal ([meine Anwendungen](https://apps.dev.microsoft.com)) generieren, Sie hier eingeben und dann wieder verwenden, wenn Sie einen bot hinzufügen. Hinweis: Wenn Sie ein Update an Ihre vorhandene app in AppSource übermitteln, darf die ID in ihrem Manifest nicht geändert werden.</span><span class="sxs-lookup"><span data-stu-id="74dbe-131">Otherwise, you should generate a new ID at the Microsoft Application Registration Portal ([My Applications](https://apps.dev.microsoft.com)), enter it here, and then reuse it when you add a bot.Note: If you are submitting an update to your existing app in AppSource, the ID in your manifest must not be modified.</span></span>

## <a name="packagename"></a><span data-ttu-id="74dbe-132">PackageName</span><span class="sxs-lookup"><span data-stu-id="74dbe-132">packageName</span></span>

<span data-ttu-id="74dbe-133">**Erforderliche** &ndash; Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="74dbe-133">**Required** &ndash; String</span></span>

<span data-ttu-id="74dbe-134">Ein eindeutiger Bezeichner für diese APP in umgekehrter Domänen Notation; Beispiel: com. Beispiel. MyApp.</span><span class="sxs-lookup"><span data-stu-id="74dbe-134">A unique identifier for this app in reverse domain notation; for example, com.example.myapp.</span></span>

## <a name="developer"></a><span data-ttu-id="74dbe-135">developer</span><span class="sxs-lookup"><span data-stu-id="74dbe-135">developer</span></span>

<span data-ttu-id="74dbe-136">**Required**</span><span class="sxs-lookup"><span data-stu-id="74dbe-136">**Required**</span></span>

<span data-ttu-id="74dbe-137">Gibt Informationen zu Ihrem Unternehmen an.</span><span class="sxs-lookup"><span data-stu-id="74dbe-137">Specifies information about your company.</span></span> <span data-ttu-id="74dbe-138">Für an AppSource übermittelte Apps (ehemals Office Store) müssen diese Werte mit den Informationen in Ihrem AppSource-Eintrag übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="74dbe-138">For apps submitted to AppSource (formerly Office Store), these values must match the information in your AppSource entry.</span></span> <span data-ttu-id="74dbe-139">Weitere Informationen finden Sie in unseren [Veröffentlichungsrichtlinien](~/concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md) .</span><span class="sxs-lookup"><span data-stu-id="74dbe-139">See our [publishing guidelines](~/concepts/deploy-and-publish/appsource/prepare/frequently-failed-cases.md) for additional information.</span></span>

|<span data-ttu-id="74dbe-140">Name</span><span class="sxs-lookup"><span data-stu-id="74dbe-140">Name</span></span>| <span data-ttu-id="74dbe-141">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="74dbe-141">Maximum size</span></span> | <span data-ttu-id="74dbe-142">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="74dbe-142">Required</span></span> | <span data-ttu-id="74dbe-143">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="74dbe-143">Description</span></span>|
|---|---|---|---|
|`name`|<span data-ttu-id="74dbe-144">32 Zeichen</span><span class="sxs-lookup"><span data-stu-id="74dbe-144">32 characters</span></span>|<span data-ttu-id="74dbe-145">✔</span><span class="sxs-lookup"><span data-stu-id="74dbe-145">✔</span></span>|<span data-ttu-id="74dbe-146">Der Anzeigename für den Entwickler.</span><span class="sxs-lookup"><span data-stu-id="74dbe-146">The display name for the developer.</span></span>|
|`websiteUrl`|<span data-ttu-id="74dbe-147">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="74dbe-147">2048 characters</span></span>|<span data-ttu-id="74dbe-148">✔</span><span class="sxs-lookup"><span data-stu-id="74dbe-148">✔</span></span>|<span data-ttu-id="74dbe-149">Die https://-URL zur Website des Entwicklers.</span><span class="sxs-lookup"><span data-stu-id="74dbe-149">The https:// URL to the developer's website.</span></span> <span data-ttu-id="74dbe-150">Dieser Link sollte Benutzer zu Ihrer Firma oder produktspezifischen Zielseite führen.</span><span class="sxs-lookup"><span data-stu-id="74dbe-150">This link should take users to your company or product-specific landing page.</span></span>|
|`privacyUrl`|<span data-ttu-id="74dbe-151">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="74dbe-151">2048 characters</span></span>|<span data-ttu-id="74dbe-152">✔</span><span class="sxs-lookup"><span data-stu-id="74dbe-152">✔</span></span>|<span data-ttu-id="74dbe-153">Die https://-URL zur Datenschutzrichtlinie des Entwicklers.</span><span class="sxs-lookup"><span data-stu-id="74dbe-153">The https:// URL to the developer's privacy policy.</span></span>|
|`termsOfUseUrl`|<span data-ttu-id="74dbe-154">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="74dbe-154">2048 characters</span></span>|<span data-ttu-id="74dbe-155">✔</span><span class="sxs-lookup"><span data-stu-id="74dbe-155">✔</span></span>|<span data-ttu-id="74dbe-156">Die https://-URL zu den Nutzungsbedingungen des Entwicklers.</span><span class="sxs-lookup"><span data-stu-id="74dbe-156">The https:// URL to the developer's terms of use.</span></span>|
|`mpnId`|<span data-ttu-id="74dbe-157">10 Zeichen</span><span class="sxs-lookup"><span data-stu-id="74dbe-157">10 characters</span></span>| |<span data-ttu-id="74dbe-158">**Optional** Die Microsoft Partner-Netzwerk-ID, die die Partnerorganisation identifiziert, die die APP aufbaut.</span><span class="sxs-lookup"><span data-stu-id="74dbe-158">**Optional** The Microsoft Partner Network ID that identifies the partner organization building the app.</span></span>|

## <a name="localizationinfo"></a><span data-ttu-id="74dbe-159">localizationInfo</span><span class="sxs-lookup"><span data-stu-id="74dbe-159">localizationInfo</span></span>

<span data-ttu-id="74dbe-160">**Optional**</span><span class="sxs-lookup"><span data-stu-id="74dbe-160">**Optional**</span></span>

<span data-ttu-id="74dbe-161">Ermöglicht die Angabe einer Standardsprache sowie Zeiger auf zusätzliche Sprachdateien.</span><span class="sxs-lookup"><span data-stu-id="74dbe-161">Allows the specification of a default language, as well as pointers to additional language files.</span></span> <span data-ttu-id="74dbe-162">Siehe [Lokalisierung](~/concepts/build-and-test/apps-localization.md).</span><span class="sxs-lookup"><span data-stu-id="74dbe-162">See [localization](~/concepts/build-and-test/apps-localization.md).</span></span>

|<span data-ttu-id="74dbe-163">Name</span><span class="sxs-lookup"><span data-stu-id="74dbe-163">Name</span></span>| <span data-ttu-id="74dbe-164">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="74dbe-164">Maximum size</span></span> | <span data-ttu-id="74dbe-165">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="74dbe-165">Required</span></span> | <span data-ttu-id="74dbe-166">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="74dbe-166">Description</span></span>|
|---|---|---|---|
|`defaultLanguageTag`||<span data-ttu-id="74dbe-167">✔</span><span class="sxs-lookup"><span data-stu-id="74dbe-167">✔</span></span>|<span data-ttu-id="74dbe-168">Das Language-Tag der Zeichenfolgen in dieser Manifestdatei der obersten Ebene.</span><span class="sxs-lookup"><span data-stu-id="74dbe-168">The language tag of the strings in this top level manifest file.</span></span>|

### <a name="localizationinfoadditionallanguages"></a><span data-ttu-id="74dbe-169">localizationInfo.additionalLanguages</span><span class="sxs-lookup"><span data-stu-id="74dbe-169">localizationInfo.additionalLanguages</span></span>

<span data-ttu-id="74dbe-170">Ein Array von Objekten, das zusätzliche Sprachübersetzungen angibt.</span><span class="sxs-lookup"><span data-stu-id="74dbe-170">An array of objects specifying additional language translations.</span></span>

|<span data-ttu-id="74dbe-171">Name</span><span class="sxs-lookup"><span data-stu-id="74dbe-171">Name</span></span>| <span data-ttu-id="74dbe-172">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="74dbe-172">Maximum size</span></span> | <span data-ttu-id="74dbe-173">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="74dbe-173">Required</span></span> | <span data-ttu-id="74dbe-174">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="74dbe-174">Description</span></span>|
|---|---|---|---|
|`languageTag`||<span data-ttu-id="74dbe-175">✔</span><span class="sxs-lookup"><span data-stu-id="74dbe-175">✔</span></span>|<span data-ttu-id="74dbe-176">Das Language-Tag der Zeichenfolgen in der bereitgestellten Datei.</span><span class="sxs-lookup"><span data-stu-id="74dbe-176">The language tag of the strings in the provided file.</span></span>|
|`file`||<span data-ttu-id="74dbe-177">✔</span><span class="sxs-lookup"><span data-stu-id="74dbe-177">✔</span></span>|<span data-ttu-id="74dbe-178">Ein relativer Dateipfad zu einer JSON-Datei, die die übersetzten Zeichenfolgen enthält.</span><span class="sxs-lookup"><span data-stu-id="74dbe-178">A relative file path to a the .json file containing the translated strings.</span></span>|

## <a name="name"></a><span data-ttu-id="74dbe-179">Name</span><span class="sxs-lookup"><span data-stu-id="74dbe-179">name</span></span>

<span data-ttu-id="74dbe-180">**Required**</span><span class="sxs-lookup"><span data-stu-id="74dbe-180">**Required**</span></span>

<span data-ttu-id="74dbe-181">Der Name der APP-Erfahrung, der Benutzern in der Microsoft Teams-Benutzeroberfläche angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="74dbe-181">The name of your app experience, displayed to users in the Teams experience.</span></span> <span data-ttu-id="74dbe-182">Für apps, die an AppSource übermittelt werden, müssen diese Werte mit den Informationen in Ihrem AppSource-Eintrag übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="74dbe-182">For apps submitted to AppSource, these values must match the information in your AppSource entry.</span></span> <span data-ttu-id="74dbe-183">Die Werte von `short` und `full` sollten nicht identisch sein.</span><span class="sxs-lookup"><span data-stu-id="74dbe-183">The values of `short` and `full` should not be the same.</span></span>

|<span data-ttu-id="74dbe-184">Name</span><span class="sxs-lookup"><span data-stu-id="74dbe-184">Name</span></span>| <span data-ttu-id="74dbe-185">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="74dbe-185">Maximum size</span></span> | <span data-ttu-id="74dbe-186">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="74dbe-186">Required</span></span> | <span data-ttu-id="74dbe-187">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="74dbe-187">Description</span></span>|
|---|---|---|---|
|`short`|<span data-ttu-id="74dbe-188">30 Zeichen</span><span class="sxs-lookup"><span data-stu-id="74dbe-188">30 characters</span></span>|<span data-ttu-id="74dbe-189">✔</span><span class="sxs-lookup"><span data-stu-id="74dbe-189">✔</span></span>|<span data-ttu-id="74dbe-190">Der kurze Anzeigename für die app.</span><span class="sxs-lookup"><span data-stu-id="74dbe-190">The short display name for the app.</span></span>|
|`full`|<span data-ttu-id="74dbe-191">100 Zeichen</span><span class="sxs-lookup"><span data-stu-id="74dbe-191">100 characters</span></span>||<span data-ttu-id="74dbe-192">Der vollständige Name der APP, der verwendet wird, wenn der vollständige App-Name 30 Zeichen überschreitet.</span><span class="sxs-lookup"><span data-stu-id="74dbe-192">The full name of the app, used if the full app name exceeds 30 characters.</span></span>|

## <a name="description"></a><span data-ttu-id="74dbe-193">description</span><span class="sxs-lookup"><span data-stu-id="74dbe-193">description</span></span>

<span data-ttu-id="74dbe-194">**Required**</span><span class="sxs-lookup"><span data-stu-id="74dbe-194">**Required**</span></span>

<span data-ttu-id="74dbe-195">Beschreibt die APP für Benutzer.</span><span class="sxs-lookup"><span data-stu-id="74dbe-195">Describes your app to users.</span></span> <span data-ttu-id="74dbe-196">Für apps, die an AppSource übermittelt werden, müssen diese Werte mit den Informationen in Ihrem AppSource-Eintrag übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="74dbe-196">For apps submitted to AppSource, these values must match the information in your AppSource entry.</span></span>

<span data-ttu-id="74dbe-197">Stellen Sie sicher, dass Ihre Beschreibung ihre Erfahrung genau beschreibt und Informationen bereitstellt, um potenziellen Kunden zu helfen, ihre Erfahrungen zu verstehen.</span><span class="sxs-lookup"><span data-stu-id="74dbe-197">Ensure that your description accurately describes your experience and provides information to help potential customers understand what your experience does.</span></span> <span data-ttu-id="74dbe-198">Beachten Sie auch, dass in der vollständigen Beschreibung ein externes Konto zur Verwendung benötigt wird.</span><span class="sxs-lookup"><span data-stu-id="74dbe-198">You should also note, in the full description, if an external account is required for use.</span></span> <span data-ttu-id="74dbe-199">Die Werte von `short` und `full` sollten nicht identisch sein.</span><span class="sxs-lookup"><span data-stu-id="74dbe-199">The values of `short` and `full` should not be the same.</span></span>  <span data-ttu-id="74dbe-200">Ihre Kurzbeschreibung darf nicht innerhalb der langen Beschreibung wiederholt werden und darf keinen anderen APP-Namen enthalten.</span><span class="sxs-lookup"><span data-stu-id="74dbe-200">Your short description must not be repeated within the long description and must not include any other app name.</span></span>

|<span data-ttu-id="74dbe-201">Name</span><span class="sxs-lookup"><span data-stu-id="74dbe-201">Name</span></span>| <span data-ttu-id="74dbe-202">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="74dbe-202">Maximum size</span></span> | <span data-ttu-id="74dbe-203">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="74dbe-203">Required</span></span> | <span data-ttu-id="74dbe-204">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="74dbe-204">Description</span></span>|
|---|---|---|---|
|`short`|<span data-ttu-id="74dbe-205">80 Zeichen</span><span class="sxs-lookup"><span data-stu-id="74dbe-205">80 characters</span></span>|<span data-ttu-id="74dbe-206">✔</span><span class="sxs-lookup"><span data-stu-id="74dbe-206">✔</span></span>|<span data-ttu-id="74dbe-207">Eine kurze Beschreibung Ihrer APP-Erfahrung, die verwendet wird, wenn der Speicherplatz limitiert ist.</span><span class="sxs-lookup"><span data-stu-id="74dbe-207">A short description of your app experience, used when space is limited.</span></span>|
|`full`|<span data-ttu-id="74dbe-208">4000 Zeichen</span><span class="sxs-lookup"><span data-stu-id="74dbe-208">4000 characters</span></span>|<span data-ttu-id="74dbe-209">✔</span><span class="sxs-lookup"><span data-stu-id="74dbe-209">✔</span></span>|<span data-ttu-id="74dbe-210">Die vollständige Beschreibung Ihrer APP.</span><span class="sxs-lookup"><span data-stu-id="74dbe-210">The full description of your app.</span></span>|

## <a name="icons"></a><span data-ttu-id="74dbe-211">Symbole</span><span class="sxs-lookup"><span data-stu-id="74dbe-211">icons</span></span>

<span data-ttu-id="74dbe-212">**Required**</span><span class="sxs-lookup"><span data-stu-id="74dbe-212">**Required**</span></span>

<span data-ttu-id="74dbe-213">Symbole, die in der Teams-App verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="74dbe-213">Icons used within the Teams app.</span></span> <span data-ttu-id="74dbe-214">Die Symboldateien müssen als Teil des Upload-Pakets enthalten sein.</span><span class="sxs-lookup"><span data-stu-id="74dbe-214">The icon files must be included as part of the upload package.</span></span> <span data-ttu-id="74dbe-215">Weitere Informationen finden Sie unter [Icons](~/concepts/build-and-test/apps-package.md#icons) .</span><span class="sxs-lookup"><span data-stu-id="74dbe-215">See [Icons](~/concepts/build-and-test/apps-package.md#icons) for more information.</span></span>

|<span data-ttu-id="74dbe-216">Name</span><span class="sxs-lookup"><span data-stu-id="74dbe-216">Name</span></span>| <span data-ttu-id="74dbe-217">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="74dbe-217">Maximum size</span></span> | <span data-ttu-id="74dbe-218">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="74dbe-218">Required</span></span> | <span data-ttu-id="74dbe-219">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="74dbe-219">Description</span></span>|
|---|---|---|---|
|`outline`|<span data-ttu-id="74dbe-220">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="74dbe-220">2048 characters</span></span>|<span data-ttu-id="74dbe-221">✔</span><span class="sxs-lookup"><span data-stu-id="74dbe-221">✔</span></span>|<span data-ttu-id="74dbe-222">Ein relativer Dateipfad zu einem transparenten 32x32 PNG-Gliederungssymbol.</span><span class="sxs-lookup"><span data-stu-id="74dbe-222">A relative file path to a transparent 32x32 PNG outline icon.</span></span>|
|`color`|<span data-ttu-id="74dbe-223">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="74dbe-223">2048 characters</span></span>|<span data-ttu-id="74dbe-224">✔</span><span class="sxs-lookup"><span data-stu-id="74dbe-224">✔</span></span>|<span data-ttu-id="74dbe-225">Ein relativer Dateipfad zu einem vollfarbigen 192x192 PNG-Symbol.</span><span class="sxs-lookup"><span data-stu-id="74dbe-225">A relative file path to a full color 192x192 PNG icon.</span></span>|

## <a name="accentcolor"></a><span data-ttu-id="74dbe-226">accentColor</span><span class="sxs-lookup"><span data-stu-id="74dbe-226">accentColor</span></span>

<span data-ttu-id="74dbe-227">**Erforderliche** &ndash; Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="74dbe-227">**Required** &ndash; String</span></span>

<span data-ttu-id="74dbe-228">Eine Farbe, die in Verbindung mit und als Hintergrund für die Gliederungssymbole verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="74dbe-228">A color to use in conjunction with and as a background for your outline icons.</span></span>

<span data-ttu-id="74dbe-229">Der Wert muss ein gültiger HTML-Farb Code sein, der mit "#" beginnt `#4464ee`, beispielsweise.</span><span class="sxs-lookup"><span data-stu-id="74dbe-229">The value must be a valid HTML color code starting with '#', for example `#4464ee`.</span></span>

## <a name="configurabletabs"></a><span data-ttu-id="74dbe-230">configurableTabs</span><span class="sxs-lookup"><span data-stu-id="74dbe-230">configurableTabs</span></span>

<span data-ttu-id="74dbe-231">**Optional**</span><span class="sxs-lookup"><span data-stu-id="74dbe-231">**Optional**</span></span>

<span data-ttu-id="74dbe-232">Wird verwendet, wenn Ihre APP-Erfahrung eine Team Kanal-registerkartenoberfläche aufweist, die eine zusätzliche Konfiguration erfordert, bevor Sie hinzugefügt wird.</span><span class="sxs-lookup"><span data-stu-id="74dbe-232">Used when your app experience has a team channel tab experience that requires extra configuration before it is added.</span></span> <span data-ttu-id="74dbe-233">Konfigurierbare Registerkarten werden nur im Bereich Teams unterstützt, und derzeit wird nur eine Registerkarte pro App unterstützt.</span><span class="sxs-lookup"><span data-stu-id="74dbe-233">Configurable tabs are supported only in the teams scope, and currently only one tab per app is supported.</span></span>

<span data-ttu-id="74dbe-234">Das Objekt ist ein Array mit allen Elementen des Typs `object`.</span><span class="sxs-lookup"><span data-stu-id="74dbe-234">The object is an array with all elements of the type `object`.</span></span> <span data-ttu-id="74dbe-235">Dieser Block ist nur für Lösungen erforderlich, die eine konfigurierbare Kanal Registerkarten Lösung bieten.</span><span class="sxs-lookup"><span data-stu-id="74dbe-235">This block is required only for solutions that provide a configurable channel tab solution.</span></span>

|<span data-ttu-id="74dbe-236">Name</span><span class="sxs-lookup"><span data-stu-id="74dbe-236">Name</span></span>| <span data-ttu-id="74dbe-237">Typ</span><span class="sxs-lookup"><span data-stu-id="74dbe-237">Type</span></span>| <span data-ttu-id="74dbe-238">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="74dbe-238">Maximum size</span></span> | <span data-ttu-id="74dbe-239">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="74dbe-239">Required</span></span> | <span data-ttu-id="74dbe-240">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="74dbe-240">Description</span></span>|
|---|---|---|---|---|
|`configurationUrl`|<span data-ttu-id="74dbe-241">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="74dbe-241">String</span></span>|<span data-ttu-id="74dbe-242">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="74dbe-242">2048 characters</span></span>|<span data-ttu-id="74dbe-243">✔</span><span class="sxs-lookup"><span data-stu-id="74dbe-243">✔</span></span>|<span data-ttu-id="74dbe-244">Die https://-URL, die beim Konfigurieren der Registerkarte verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="74dbe-244">The https:// URL to use when configuring the tab.</span></span>|
|`canUpdateConfiguration`|<span data-ttu-id="74dbe-245">Boolesch</span><span class="sxs-lookup"><span data-stu-id="74dbe-245">Boolean</span></span>|||<span data-ttu-id="74dbe-246">Ein Wert, der angibt, ob eine Instanz der Konfiguration der Registerkarte nach der Erstellung vom Benutzer aktualisiert werden kann.</span><span class="sxs-lookup"><span data-stu-id="74dbe-246">A value indicating whether an instance of the tab's configuration can be updated by the user after creation.</span></span> <span data-ttu-id="74dbe-247">Standard`true`</span><span class="sxs-lookup"><span data-stu-id="74dbe-247">Default: `true`</span></span>|
|`scopes`|<span data-ttu-id="74dbe-248">Array von Enum</span><span class="sxs-lookup"><span data-stu-id="74dbe-248">Array of enum</span></span>|<span data-ttu-id="74dbe-249">1 </span><span class="sxs-lookup"><span data-stu-id="74dbe-249">1</span></span>|<span data-ttu-id="74dbe-250">✔</span><span class="sxs-lookup"><span data-stu-id="74dbe-250">✔</span></span>|<span data-ttu-id="74dbe-251">Derzeit unterstützen konfigurierbare Registerkarten `team` nur `groupchat` die Bereiche und.</span><span class="sxs-lookup"><span data-stu-id="74dbe-251">Currently, configurable tabs support only the `team` and `groupchat` scopes.</span></span> |
|`sharePointPreviewImage`|<span data-ttu-id="74dbe-252">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="74dbe-252">String</span></span>|<span data-ttu-id="74dbe-253">2048</span><span class="sxs-lookup"><span data-stu-id="74dbe-253">2048</span></span>||<span data-ttu-id="74dbe-254">Ein relativer Dateipfad zu einem Vorschaubild für die Registerkarte für die Verwendung in SharePoint.</span><span class="sxs-lookup"><span data-stu-id="74dbe-254">A relative file path to a tab preview image for use in SharePoint.</span></span> <span data-ttu-id="74dbe-255">Größe 1024x768.</span><span class="sxs-lookup"><span data-stu-id="74dbe-255">Size 1024x768.</span></span> |
|`supportedSharePointHosts`|<span data-ttu-id="74dbe-256">Array von Enum</span><span class="sxs-lookup"><span data-stu-id="74dbe-256">Array of enum</span></span>|<span data-ttu-id="74dbe-257">1 </span><span class="sxs-lookup"><span data-stu-id="74dbe-257">1</span></span>||<span data-ttu-id="74dbe-258">Definiert, wie die Registerkarte in SharePoint zur Verfügung gestellt wird.</span><span class="sxs-lookup"><span data-stu-id="74dbe-258">Defines how your tab will be made available in SharePoint.</span></span> <span data-ttu-id="74dbe-259">Optionen sind `sharePointFullPage` und`sharePointWebPart`</span><span class="sxs-lookup"><span data-stu-id="74dbe-259">Options are `sharePointFullPage` and `sharePointWebPart`</span></span> |

## <a name="statictabs"></a><span data-ttu-id="74dbe-260">staticTabs</span><span class="sxs-lookup"><span data-stu-id="74dbe-260">staticTabs</span></span>

<span data-ttu-id="74dbe-261">**Optional**</span><span class="sxs-lookup"><span data-stu-id="74dbe-261">**Optional**</span></span>

<span data-ttu-id="74dbe-262">Definiert eine Gruppe von Registerkarten, die standardmäßig "fixiert" werden können, ohne dass der Benutzer Sie manuell hinzufügt.</span><span class="sxs-lookup"><span data-stu-id="74dbe-262">Defines a set of tabs that can be "pinned" by default, without the user adding them manually.</span></span> <span data-ttu-id="74dbe-263">Im `personal` Bereich deklarierte statische Registerkarten werden immer an die persönliche Benutzeroberfläche der APP angeheftet.</span><span class="sxs-lookup"><span data-stu-id="74dbe-263">Static tabs declared in `personal` scope are always pinned to the app's personal experience.</span></span> <span data-ttu-id="74dbe-264">Im `team` Bereich deklarierte statische Registerkarten werden derzeit nicht unterstützt.</span><span class="sxs-lookup"><span data-stu-id="74dbe-264">Static tabs declared in the `team` scope are currently not supported.</span></span>

<span data-ttu-id="74dbe-265">Bei dem Objekt handelt es sich um ein Array (maximal 16 Elemente) mit allen Elementen `object`des Typs.</span><span class="sxs-lookup"><span data-stu-id="74dbe-265">The object is an array (maximum of 16 elements) with all elements of the type `object`.</span></span> <span data-ttu-id="74dbe-266">Dieser Block ist nur für Lösungen erforderlich, die eine statische Registerkarten Lösung bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="74dbe-266">This block is required only for solutions that provide a static tab solution.</span></span>

|<span data-ttu-id="74dbe-267">Name</span><span class="sxs-lookup"><span data-stu-id="74dbe-267">Name</span></span>| <span data-ttu-id="74dbe-268">Typ</span><span class="sxs-lookup"><span data-stu-id="74dbe-268">Type</span></span>| <span data-ttu-id="74dbe-269">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="74dbe-269">Maximum size</span></span> | <span data-ttu-id="74dbe-270">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="74dbe-270">Required</span></span> | <span data-ttu-id="74dbe-271">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="74dbe-271">Description</span></span>|
|---|---|---|---|---|
|`entityId`|<span data-ttu-id="74dbe-272">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="74dbe-272">String</span></span>|<span data-ttu-id="74dbe-273">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="74dbe-273">64 characters</span></span>|<span data-ttu-id="74dbe-274">✔</span><span class="sxs-lookup"><span data-stu-id="74dbe-274">✔</span></span>|<span data-ttu-id="74dbe-275">Ein eindeutiger Bezeichner für die Entität, die auf der Registerkarte angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="74dbe-275">A unique identifier for the entity that the tab displays.</span></span>|
|`name`|<span data-ttu-id="74dbe-276">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="74dbe-276">String</span></span>|<span data-ttu-id="74dbe-277">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="74dbe-277">128 characters</span></span>|<span data-ttu-id="74dbe-278">✔</span><span class="sxs-lookup"><span data-stu-id="74dbe-278">✔</span></span>|<span data-ttu-id="74dbe-279">Der Anzeigename der Registerkarte in der Kanalschnittstelle.</span><span class="sxs-lookup"><span data-stu-id="74dbe-279">The display name of the tab in the channel interface.</span></span>|
|`contentUrl`|<span data-ttu-id="74dbe-280">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="74dbe-280">String</span></span>|<span data-ttu-id="74dbe-281">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="74dbe-281">2048 characters</span></span>|<span data-ttu-id="74dbe-282">✔</span><span class="sxs-lookup"><span data-stu-id="74dbe-282">✔</span></span>|<span data-ttu-id="74dbe-283">Die https://-URL, die auf die Benutzeroberfläche der Entität zeigt, die im Canvas "Teams" angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="74dbe-283">The https:// URL that points to the entity UI to be displayed in the Teams canvas.</span></span>|
|`websiteUrl`|<span data-ttu-id="74dbe-284">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="74dbe-284">String</span></span>|<span data-ttu-id="74dbe-285">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="74dbe-285">2048 characters</span></span>||<span data-ttu-id="74dbe-286">Die https://-URL, auf die verwiesen wird, wenn ein Benutzer sich für die Anzeige in einem Browser entscheidet.</span><span class="sxs-lookup"><span data-stu-id="74dbe-286">The https:// URL to point at if a user opts to view in a browser.</span></span>|
|`scopes`|<span data-ttu-id="74dbe-287">Array von Enum</span><span class="sxs-lookup"><span data-stu-id="74dbe-287">Array of enum</span></span>|<span data-ttu-id="74dbe-288">1 </span><span class="sxs-lookup"><span data-stu-id="74dbe-288">1</span></span>|<span data-ttu-id="74dbe-289">✔</span><span class="sxs-lookup"><span data-stu-id="74dbe-289">✔</span></span>|<span data-ttu-id="74dbe-290">Derzeit unterstützen statische Registerkarten nur `personal` den Bereich, was bedeutet, dass Sie nur als Teil der persönlichen Benutzeroberfläche vorgesehen werden kann.</span><span class="sxs-lookup"><span data-stu-id="74dbe-290">Currently, static tabs support only the `personal` scope, which means it can be provisioned only as part of the personal experience.</span></span>|

## <a name="bots"></a><span data-ttu-id="74dbe-291">Bots</span><span class="sxs-lookup"><span data-stu-id="74dbe-291">bots</span></span>

<span data-ttu-id="74dbe-292">**Optional**</span><span class="sxs-lookup"><span data-stu-id="74dbe-292">**Optional**</span></span>

<span data-ttu-id="74dbe-293">Definiert eine bot-Lösung zusammen mit optionalen Informationen wie Standardbefehls Eigenschaften.</span><span class="sxs-lookup"><span data-stu-id="74dbe-293">Defines a bot solution, along with optional information such as default command properties.</span></span>

<span data-ttu-id="74dbe-294">Das Objekt ist ein Array (Maximum von nur 1 Element&mdash;, das derzeit nur ein bot pro App zulässig ist) mit allen Elementen des `object`Typs.</span><span class="sxs-lookup"><span data-stu-id="74dbe-294">The object is an array (maximum of only 1 element&mdash;currently only one bot is allowed per app) with all elements of the type `object`.</span></span> <span data-ttu-id="74dbe-295">Dieser Block ist nur für Lösungen erforderlich, die eine bot-Erfahrung bieten.</span><span class="sxs-lookup"><span data-stu-id="74dbe-295">This block is required only for solutions that provide a bot experience.</span></span>

|<span data-ttu-id="74dbe-296">Name</span><span class="sxs-lookup"><span data-stu-id="74dbe-296">Name</span></span>| <span data-ttu-id="74dbe-297">Typ</span><span class="sxs-lookup"><span data-stu-id="74dbe-297">Type</span></span>| <span data-ttu-id="74dbe-298">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="74dbe-298">Maximum size</span></span> | <span data-ttu-id="74dbe-299">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="74dbe-299">Required</span></span> | <span data-ttu-id="74dbe-300">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="74dbe-300">Description</span></span>|
|---|---|---|---|---|
|`botId`|<span data-ttu-id="74dbe-301">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="74dbe-301">String</span></span>|<span data-ttu-id="74dbe-302">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="74dbe-302">64 characters</span></span>|<span data-ttu-id="74dbe-303">✔</span><span class="sxs-lookup"><span data-stu-id="74dbe-303">✔</span></span>|<span data-ttu-id="74dbe-304">Die eindeutige Microsoft-App-ID für den bot, die im bot-Framework registriert ist.</span><span class="sxs-lookup"><span data-stu-id="74dbe-304">The unique Microsoft app ID for the bot as registered with the Bot Framework.</span></span> <span data-ttu-id="74dbe-305">Dies kann auch die gesamte [App-ID](#id)entsprechen.</span><span class="sxs-lookup"><span data-stu-id="74dbe-305">This may well be the same as the overall [app ID](#id).</span></span>|
|`needsChannelSelector`|<span data-ttu-id="74dbe-306">Boolesch</span><span class="sxs-lookup"><span data-stu-id="74dbe-306">Boolean</span></span>|||<span data-ttu-id="74dbe-307">Beschreibt, ob der bot einen Benutzerhinweis verwendet, um den bot einem bestimmten Kanal hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="74dbe-307">Describes whether or not the bot utilizes a user hint to add the bot to a specific channel.</span></span> <span data-ttu-id="74dbe-308">Standard`false`</span><span class="sxs-lookup"><span data-stu-id="74dbe-308">Default: `false`</span></span>|
|`isNotificationOnly`|<span data-ttu-id="74dbe-309">Boolesch</span><span class="sxs-lookup"><span data-stu-id="74dbe-309">Boolean</span></span>|||<span data-ttu-id="74dbe-310">Gibt an, ob ein bot ein unidirektionaler, nur für Benachrichtigungen gestellter bot ist, im Gegensatz zu einem Unterhaltungs bot.</span><span class="sxs-lookup"><span data-stu-id="74dbe-310">Indicates whether a bot is a one-way, notification-only bot, as opposed to a conversational bot.</span></span> <span data-ttu-id="74dbe-311">Standard`false`</span><span class="sxs-lookup"><span data-stu-id="74dbe-311">Default: `false`</span></span>|
|`supportsFiles`|<span data-ttu-id="74dbe-312">Boolesch</span><span class="sxs-lookup"><span data-stu-id="74dbe-312">Boolean</span></span>|||<span data-ttu-id="74dbe-313">Gibt an, ob der bot die Möglichkeit unterstützt, Dateien im persönlichen Chat hoch-/herunterzuladen.</span><span class="sxs-lookup"><span data-stu-id="74dbe-313">Indicates whether the bot supports the ability to upload/download files in personal chat.</span></span> <span data-ttu-id="74dbe-314">Standard`false`</span><span class="sxs-lookup"><span data-stu-id="74dbe-314">Default: `false`</span></span>|
|`scopes`|<span data-ttu-id="74dbe-315">Array von Enum</span><span class="sxs-lookup"><span data-stu-id="74dbe-315">Array of enum</span></span>|<span data-ttu-id="74dbe-316">3 </span><span class="sxs-lookup"><span data-stu-id="74dbe-316">3</span></span>|<span data-ttu-id="74dbe-317">✔</span><span class="sxs-lookup"><span data-stu-id="74dbe-317">✔</span></span>|<span data-ttu-id="74dbe-318">Gibt an, ob der bot eine Erfahrung im Kontext eines Kanals in a `team`, in einem Gruppenchat (`groupchat`) oder eine Erfahrung bietet, die auf einen einzelnen Benutzer allein beschränkt`personal`ist ().</span><span class="sxs-lookup"><span data-stu-id="74dbe-318">Specifies whether the bot offers an experience in the context of a channel in a `team`, in a group chat (`groupchat`), or an experience scoped to an individual user alone (`personal`).</span></span> <span data-ttu-id="74dbe-319">Diese Optionen sind nicht exklusiv.</span><span class="sxs-lookup"><span data-stu-id="74dbe-319">These options are non-exclusive.</span></span>|

### <a name="botscommandlists"></a><span data-ttu-id="74dbe-320">Bots. commandLists</span><span class="sxs-lookup"><span data-stu-id="74dbe-320">bots.commandLists</span></span>

<span data-ttu-id="74dbe-321">Eine optionale Liste von Befehlen, die ihr bot Benutzern empfehlen kann.</span><span class="sxs-lookup"><span data-stu-id="74dbe-321">An optional list of commands that your bot can recommend to users.</span></span> <span data-ttu-id="74dbe-322">Das Objekt ist ein Array (Maximum von 2 Elementen) mit allen Elementen des Typs `object`; Sie müssen für jeden Bereich, den Ihr bot unterstützt, eine separate Befehlsliste definieren.</span><span class="sxs-lookup"><span data-stu-id="74dbe-322">The object is an array (maximum of 2 elements) with all elements of type `object`; you must define a separate command list for each scope that your bot supports.</span></span> <span data-ttu-id="74dbe-323">Weitere Informationen finden Sie unter [bot-Menüs](~/bots/how-to/create-a-bot-commands-menu.md) .</span><span class="sxs-lookup"><span data-stu-id="74dbe-323">See [Bot menus](~/bots/how-to/create-a-bot-commands-menu.md) for more information.</span></span>

|<span data-ttu-id="74dbe-324">Name</span><span class="sxs-lookup"><span data-stu-id="74dbe-324">Name</span></span>| <span data-ttu-id="74dbe-325">Typ</span><span class="sxs-lookup"><span data-stu-id="74dbe-325">Type</span></span>| <span data-ttu-id="74dbe-326">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="74dbe-326">Maximum size</span></span> | <span data-ttu-id="74dbe-327">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="74dbe-327">Required</span></span> | <span data-ttu-id="74dbe-328">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="74dbe-328">Description</span></span>|
|---|---|---|---|---|
|`items.scopes`|<span data-ttu-id="74dbe-329">Array von Enum</span><span class="sxs-lookup"><span data-stu-id="74dbe-329">array of enum</span></span>|<span data-ttu-id="74dbe-330">3 </span><span class="sxs-lookup"><span data-stu-id="74dbe-330">3</span></span>|<span data-ttu-id="74dbe-331">✔</span><span class="sxs-lookup"><span data-stu-id="74dbe-331">✔</span></span>|<span data-ttu-id="74dbe-332">Gibt den Bereich an, für den die Befehlsliste gültig ist.</span><span class="sxs-lookup"><span data-stu-id="74dbe-332">Specifies the scope for which the command list is valid.</span></span> <span data-ttu-id="74dbe-333">Optionen sind `team`, `personal`und `groupchat`.</span><span class="sxs-lookup"><span data-stu-id="74dbe-333">Options are `team`, `personal`, and `groupchat`.</span></span>|
|`items.commands`|<span data-ttu-id="74dbe-334">Array von Objekten</span><span class="sxs-lookup"><span data-stu-id="74dbe-334">array of objects</span></span>|<span data-ttu-id="74dbe-335">10  </span><span class="sxs-lookup"><span data-stu-id="74dbe-335">10</span></span>|<span data-ttu-id="74dbe-336">✔</span><span class="sxs-lookup"><span data-stu-id="74dbe-336">✔</span></span>|<span data-ttu-id="74dbe-337">Ein Array von Befehlen, die der bot unterstützt:</span><span class="sxs-lookup"><span data-stu-id="74dbe-337">An array of commands the bot supports:</span></span><br><span data-ttu-id="74dbe-338">`title`: der Name des bot-Befehls (String, 32)</span><span class="sxs-lookup"><span data-stu-id="74dbe-338">`title`: the bot command name (string, 32)</span></span><br><span data-ttu-id="74dbe-339">`description`: eine einfache Beschreibung oder ein Beispiel für die Befehlssyntax und das zugehörige Argument (String, 128)</span><span class="sxs-lookup"><span data-stu-id="74dbe-339">`description`: a simple description or example of the command syntax and its argument (string, 128)</span></span>|

## <a name="connectors"></a><span data-ttu-id="74dbe-340">Connectors</span><span class="sxs-lookup"><span data-stu-id="74dbe-340">connectors</span></span>

<span data-ttu-id="74dbe-341">**Optional**</span><span class="sxs-lookup"><span data-stu-id="74dbe-341">**Optional**</span></span>

<span data-ttu-id="74dbe-342">Der `connectors` Block definiert einen Office 365-Konnektor für die app.</span><span class="sxs-lookup"><span data-stu-id="74dbe-342">The `connectors` block defines an Office 365 Connector for the app.</span></span>

<span data-ttu-id="74dbe-343">Das Objekt ist ein Array (Maximum of 1-Element) mit allen Elementen des `object`Typs.</span><span class="sxs-lookup"><span data-stu-id="74dbe-343">The object is an array (maximum of 1 element) with all elements of type `object`.</span></span> <span data-ttu-id="74dbe-344">Dieser Block ist nur für Lösungen erforderlich, die einen Connector bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="74dbe-344">This block is required only for solutions that provide a Connector.</span></span>

|<span data-ttu-id="74dbe-345">Name</span><span class="sxs-lookup"><span data-stu-id="74dbe-345">Name</span></span>| <span data-ttu-id="74dbe-346">Typ</span><span class="sxs-lookup"><span data-stu-id="74dbe-346">Type</span></span>| <span data-ttu-id="74dbe-347">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="74dbe-347">Maximum size</span></span> | <span data-ttu-id="74dbe-348">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="74dbe-348">Required</span></span> | <span data-ttu-id="74dbe-349">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="74dbe-349">Description</span></span>|
|---|---|---|---|---|
|`configurationUrl`|<span data-ttu-id="74dbe-350">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="74dbe-350">String</span></span>|<span data-ttu-id="74dbe-351">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="74dbe-351">2048 characters</span></span>|<span data-ttu-id="74dbe-352">✔</span><span class="sxs-lookup"><span data-stu-id="74dbe-352">✔</span></span>|<span data-ttu-id="74dbe-353">Die https://-URL, die beim Konfigurieren des Connectors verwendet werden soll.</span><span class="sxs-lookup"><span data-stu-id="74dbe-353">The https:// URL to use when configuring the connector.</span></span>|
|`connectorId`|<span data-ttu-id="74dbe-354">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="74dbe-354">String</span></span>|<span data-ttu-id="74dbe-355">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="74dbe-355">64 characters</span></span>|<span data-ttu-id="74dbe-356">✔</span><span class="sxs-lookup"><span data-stu-id="74dbe-356">✔</span></span>|<span data-ttu-id="74dbe-357">Ein eindeutiger Bezeichner für den Connector, der seiner ID im [Entwickler Dashboard für Connectors](https://aka.ms/connectorsdashboard)entspricht.</span><span class="sxs-lookup"><span data-stu-id="74dbe-357">A unique identifier for the Connector that matches its ID in the [Connectors Developer Dashboard](https://aka.ms/connectorsdashboard).</span></span>|
|`scopes`|<span data-ttu-id="74dbe-358">Array von Enum</span><span class="sxs-lookup"><span data-stu-id="74dbe-358">Array of enum</span></span>|<span data-ttu-id="74dbe-359">1 </span><span class="sxs-lookup"><span data-stu-id="74dbe-359">1</span></span>|<span data-ttu-id="74dbe-360">✔</span><span class="sxs-lookup"><span data-stu-id="74dbe-360">✔</span></span>|<span data-ttu-id="74dbe-361">Gibt an, ob der Connector eine Erfahrung im Kontext eines Kanals in a `team`bietet oder ein Erlebnis, das allein auf einen einzelnen Benutzer beschränkt`personal`ist ().</span><span class="sxs-lookup"><span data-stu-id="74dbe-361">Specifies whether the Connector offers an experience in the context of a channel in a `team`, or an experience scoped to an individual user alone (`personal`).</span></span> <span data-ttu-id="74dbe-362">Derzeit wird nur der `team` Bereich unterstützt.</span><span class="sxs-lookup"><span data-stu-id="74dbe-362">Currently, only the `team` scope is supported.</span></span>|

## <a name="composeextensions"></a><span data-ttu-id="74dbe-363">composeExtensions</span><span class="sxs-lookup"><span data-stu-id="74dbe-363">composeExtensions</span></span>

<span data-ttu-id="74dbe-364">**Optional**</span><span class="sxs-lookup"><span data-stu-id="74dbe-364">**Optional**</span></span>

<span data-ttu-id="74dbe-365">Definiert eine Messaging Erweiterung für die app.</span><span class="sxs-lookup"><span data-stu-id="74dbe-365">Defines a messaging extension for the app.</span></span>

> [!NOTE]
> <span data-ttu-id="74dbe-366">Der Name des Features wurde von "Erstell Erweiterung" in "Messaging Extension" im November 2017 geändert, aber der Manifestname bleibt unverändert, sodass vorhandene Erweiterungen weiterhin funktionieren.</span><span class="sxs-lookup"><span data-stu-id="74dbe-366">The name of the feature was changed from "compose extension" to "messaging extension" in November, 2017, but the manifest name remains the same so that existing extensions continue to function.</span></span>

<span data-ttu-id="74dbe-367">Das Objekt ist ein Array (Maximum of 1-Element) mit allen Elementen des `object`Typs.</span><span class="sxs-lookup"><span data-stu-id="74dbe-367">The object is an array (maximum of 1 element) with all elements of type `object`.</span></span> <span data-ttu-id="74dbe-368">Dieser Block ist nur für Lösungen erforderlich, die eine Messaging Erweiterung bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="74dbe-368">This block is required only for solutions that provide a messaging extension.</span></span>

|<span data-ttu-id="74dbe-369">Name</span><span class="sxs-lookup"><span data-stu-id="74dbe-369">Name</span></span>| <span data-ttu-id="74dbe-370">Typ</span><span class="sxs-lookup"><span data-stu-id="74dbe-370">Type</span></span> | <span data-ttu-id="74dbe-371">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="74dbe-371">Maximum Size</span></span> | <span data-ttu-id="74dbe-372">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="74dbe-372">Required</span></span> | <span data-ttu-id="74dbe-373">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="74dbe-373">Description</span></span>|
|---|---|---|---|---|
|`botId`|<span data-ttu-id="74dbe-374">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="74dbe-374">String</span></span>|<span data-ttu-id="74dbe-375">64</span><span class="sxs-lookup"><span data-stu-id="74dbe-375">64</span></span>|<span data-ttu-id="74dbe-376">✔</span><span class="sxs-lookup"><span data-stu-id="74dbe-376">✔</span></span>|<span data-ttu-id="74dbe-377">Die eindeutige Microsoft-App-ID für den bot, der die Messaging Erweiterung unterstützt, wie Sie mit dem bot-Framework registriert wurde.</span><span class="sxs-lookup"><span data-stu-id="74dbe-377">The unique Microsoft app ID for the bot that backs the messaging extension, as registered with the Bot Framework.</span></span> <span data-ttu-id="74dbe-378">Dies kann auch die gesamte APP-ID entsprechen.</span><span class="sxs-lookup"><span data-stu-id="74dbe-378">This may well be the same as the overall App ID.</span></span>|
|`canUpdateConfiguration`|<span data-ttu-id="74dbe-379">Boolesch</span><span class="sxs-lookup"><span data-stu-id="74dbe-379">Boolean</span></span>|||<span data-ttu-id="74dbe-380">Ein Wert, der angibt, ob die Konfiguration einer Messaging Erweiterung vom Benutzer aktualisiert werden kann.</span><span class="sxs-lookup"><span data-stu-id="74dbe-380">A value indicating whether the configuration of a messaging extension can be updated by the user.</span></span> <span data-ttu-id="74dbe-381">Der Standardwert `false`ist.</span><span class="sxs-lookup"><span data-stu-id="74dbe-381">The default is `false`.</span></span>|
|`commands`|<span data-ttu-id="74dbe-382">Array von Object</span><span class="sxs-lookup"><span data-stu-id="74dbe-382">Array of object</span></span>|<span data-ttu-id="74dbe-383">10  </span><span class="sxs-lookup"><span data-stu-id="74dbe-383">10</span></span>|<span data-ttu-id="74dbe-384">✔</span><span class="sxs-lookup"><span data-stu-id="74dbe-384">✔</span></span>|<span data-ttu-id="74dbe-385">Array von Befehlen, die von der Messaging-Erweiterung unterstützt werden</span><span class="sxs-lookup"><span data-stu-id="74dbe-385">Array of commands the messaging extension supports</span></span>|
|`messageHandlers`|<span data-ttu-id="74dbe-386">Array von Objekten</span><span class="sxs-lookup"><span data-stu-id="74dbe-386">Array of Objects</span></span>|<span data-ttu-id="74dbe-387">5 </span><span class="sxs-lookup"><span data-stu-id="74dbe-387">5</span></span>||<span data-ttu-id="74dbe-388">Eine Liste von Handlern, mit denen apps aufgerufen werden können, wenn bestimmte Bedingungen erfüllt sind.</span><span class="sxs-lookup"><span data-stu-id="74dbe-388">A list of handlers that allow apps to be invoked when certain conditions are met.</span></span> <span data-ttu-id="74dbe-389">Domänen müssen ebenfalls in aufgeführt sein.`validDomains`</span><span class="sxs-lookup"><span data-stu-id="74dbe-389">Domains must also be listed in `validDomains`</span></span>|
|`messageHandlers.type`|<span data-ttu-id="74dbe-390">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="74dbe-390">String</span></span>|||<span data-ttu-id="74dbe-391">Der Typ des Nachrichten Handlers.</span><span class="sxs-lookup"><span data-stu-id="74dbe-391">The type of message handler.</span></span> <span data-ttu-id="74dbe-392">Muss `"link"` sein.</span><span class="sxs-lookup"><span data-stu-id="74dbe-392">Must be `"link"`.</span></span>|
|`messageHandlers.value.domains`|<span data-ttu-id="74dbe-393">Array von Zeichenfolgen</span><span class="sxs-lookup"><span data-stu-id="74dbe-393">Array of Strings</span></span>|||<span data-ttu-id="74dbe-394">Array von Domänen, für die der Link Nachrichtenhandler registriert werden kann.</span><span class="sxs-lookup"><span data-stu-id="74dbe-394">Array of domains that the link message handler can register for.</span></span>|

### <a name="composeextensionscommands"></a><span data-ttu-id="74dbe-395">composeExtensions. Commands</span><span class="sxs-lookup"><span data-stu-id="74dbe-395">composeExtensions.commands</span></span>

<span data-ttu-id="74dbe-396">Ihre Messaging Erweiterung sollte einen oder mehrere Befehle deklarieren.</span><span class="sxs-lookup"><span data-stu-id="74dbe-396">Your messaging extension should declare one or more commands.</span></span> <span data-ttu-id="74dbe-397">Jeder Befehl wird in Microsoft Teams als potenzielle Interaktion aus dem Benutzeroberflächen basierten Einstiegspfad angezeigt.</span><span class="sxs-lookup"><span data-stu-id="74dbe-397">Each command appears in Microsoft Teams as a potential interaction from the UI-based entry point.</span></span> <span data-ttu-id="74dbe-398">Es gibt maximal 10 Befehle.</span><span class="sxs-lookup"><span data-stu-id="74dbe-398">There is a maximum of 10 commands.</span></span>

<span data-ttu-id="74dbe-399">Jedes Command-Element ist ein Objekt mit der folgenden Struktur:</span><span class="sxs-lookup"><span data-stu-id="74dbe-399">Each command item is an object with the following structure:</span></span>

|<span data-ttu-id="74dbe-400">Name</span><span class="sxs-lookup"><span data-stu-id="74dbe-400">Name</span></span>| <span data-ttu-id="74dbe-401">Typ</span><span class="sxs-lookup"><span data-stu-id="74dbe-401">Type</span></span>| <span data-ttu-id="74dbe-402">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="74dbe-402">Maximum size</span></span> | <span data-ttu-id="74dbe-403">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="74dbe-403">Required</span></span> | <span data-ttu-id="74dbe-404">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="74dbe-404">Description</span></span>|
|---|---|---|---|---|
|`id`|<span data-ttu-id="74dbe-405">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="74dbe-405">String</span></span>|<span data-ttu-id="74dbe-406">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="74dbe-406">64 characters</span></span>|<span data-ttu-id="74dbe-407">✔</span><span class="sxs-lookup"><span data-stu-id="74dbe-407">✔</span></span>|<span data-ttu-id="74dbe-408">Die ID für den Befehl</span><span class="sxs-lookup"><span data-stu-id="74dbe-408">The ID for the command</span></span>|
|`type`|<span data-ttu-id="74dbe-409">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="74dbe-409">String</span></span>|<span data-ttu-id="74dbe-410">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="74dbe-410">64 characters</span></span>||<span data-ttu-id="74dbe-411">Der Typ des Befehls.</span><span class="sxs-lookup"><span data-stu-id="74dbe-411">Type of the command.</span></span> <span data-ttu-id="74dbe-412">Einer von `query` oder `action`.</span><span class="sxs-lookup"><span data-stu-id="74dbe-412">One of `query` or `action`.</span></span> <span data-ttu-id="74dbe-413">Standard`query`</span><span class="sxs-lookup"><span data-stu-id="74dbe-413">Default: `query`</span></span>|
|`title`|<span data-ttu-id="74dbe-414">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="74dbe-414">String</span></span>|<span data-ttu-id="74dbe-415">32 Zeichen</span><span class="sxs-lookup"><span data-stu-id="74dbe-415">32 characters</span></span>|<span data-ttu-id="74dbe-416">✔</span><span class="sxs-lookup"><span data-stu-id="74dbe-416">✔</span></span>|<span data-ttu-id="74dbe-417">Der benutzerfreundliche Befehlsname</span><span class="sxs-lookup"><span data-stu-id="74dbe-417">The user-friendly command name</span></span>|
|`description`|<span data-ttu-id="74dbe-418">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="74dbe-418">String</span></span>|<span data-ttu-id="74dbe-419">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="74dbe-419">128 characters</span></span>||<span data-ttu-id="74dbe-420">Die Beschreibung, die den Benutzern angezeigt wird, um den Zweck dieses Befehls anzugeben</span><span class="sxs-lookup"><span data-stu-id="74dbe-420">The description that appears to users to indicate the purpose of this command</span></span>|
|`initialRun`|<span data-ttu-id="74dbe-421">Boolesch</span><span class="sxs-lookup"><span data-stu-id="74dbe-421">Boolean</span></span>|||<span data-ttu-id="74dbe-422">Ein boolescher Wert, der angibt, ob der Befehl anfänglich ohne Parameter ausgeführt werden soll.</span><span class="sxs-lookup"><span data-stu-id="74dbe-422">A Boolean value that indicates whether the command should be run initially with no parameters.</span></span> <span data-ttu-id="74dbe-423">Standard`false`</span><span class="sxs-lookup"><span data-stu-id="74dbe-423">Default: `false`</span></span>|
|`context`|<span data-ttu-id="74dbe-424">Array von Zeichenfolgen</span><span class="sxs-lookup"><span data-stu-id="74dbe-424">Array of Strings</span></span>|<span data-ttu-id="74dbe-425">3 </span><span class="sxs-lookup"><span data-stu-id="74dbe-425">3</span></span>||<span data-ttu-id="74dbe-426">Definiert, woher die Nachrichten Erweiterung aufgerufen werden kann.</span><span class="sxs-lookup"><span data-stu-id="74dbe-426">Defines where the message extension can be invoked from.</span></span> <span data-ttu-id="74dbe-427">Eine beliebige Kombi `compose`Nation `commandBox`von `message`,,.</span><span class="sxs-lookup"><span data-stu-id="74dbe-427">Any combination of `compose`, `commandBox`, `message`.</span></span> <span data-ttu-id="74dbe-428">Der Standardwert ist`["compose", "commandBox"]`</span><span class="sxs-lookup"><span data-stu-id="74dbe-428">Default is `["compose", "commandBox"]`</span></span>|
|`fetchTask`|<span data-ttu-id="74dbe-429">Boolesch</span><span class="sxs-lookup"><span data-stu-id="74dbe-429">Boolean</span></span>|||<span data-ttu-id="74dbe-430">Ein boolescher Wert, der angibt, ob das Aufgabenmodul dynamisch abgerufen werden soll.</span><span class="sxs-lookup"><span data-stu-id="74dbe-430">A boolean value that indicates if it should fetch the task module dynamically</span></span>|
|`taskInfo`|<span data-ttu-id="74dbe-431">Object</span><span class="sxs-lookup"><span data-stu-id="74dbe-431">Object</span></span>|||<span data-ttu-id="74dbe-432">Angeben des Aufgabenmoduls, das beim Verwenden eines Messaging Erweiterungs Befehls geladen werden soll</span><span class="sxs-lookup"><span data-stu-id="74dbe-432">Specify the task module to preload when using a messaging extension command</span></span>|
|`taskInfo.title`|<span data-ttu-id="74dbe-433">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="74dbe-433">String</span></span>|<span data-ttu-id="74dbe-434">64</span><span class="sxs-lookup"><span data-stu-id="74dbe-434">64</span></span>||<span data-ttu-id="74dbe-435">Ursprünglicher Dialogtitel</span><span class="sxs-lookup"><span data-stu-id="74dbe-435">Initial dialog title</span></span>|
|`taskInfo.width`|<span data-ttu-id="74dbe-436">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="74dbe-436">String</span></span>|||<span data-ttu-id="74dbe-437">Dialog Breite-entweder eine Zahl in Pixel oder ein Standardlayout wie "groß", "Mittel" oder "klein"</span><span class="sxs-lookup"><span data-stu-id="74dbe-437">Dialog width - either a number in pixels or default layout such as 'large', 'medium', or 'small'</span></span>|
|`taskInfo.height`|<span data-ttu-id="74dbe-438">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="74dbe-438">String</span></span>|||<span data-ttu-id="74dbe-439">Dialog Feld Höhe-entweder eine Zahl in Pixel oder ein Standardlayout wie "groß", "Mittel" oder "klein"</span><span class="sxs-lookup"><span data-stu-id="74dbe-439">Dialog height - either a number in pixels or default layout such as 'large', 'medium', or 'small'</span></span>|
|`taskInfo.url`|<span data-ttu-id="74dbe-440">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="74dbe-440">String</span></span>|||<span data-ttu-id="74dbe-441">Anfängliche WebView-URL</span><span class="sxs-lookup"><span data-stu-id="74dbe-441">Initial webview URL</span></span>|
|`parameters`|<span data-ttu-id="74dbe-442">Array von Object</span><span class="sxs-lookup"><span data-stu-id="74dbe-442">Array of object</span></span>|<span data-ttu-id="74dbe-443">5 </span><span class="sxs-lookup"><span data-stu-id="74dbe-443">5</span></span>|<span data-ttu-id="74dbe-444">✔</span><span class="sxs-lookup"><span data-stu-id="74dbe-444">✔</span></span>|<span data-ttu-id="74dbe-445">Die Liste der Parameter, die der Befehl benötigt.</span><span class="sxs-lookup"><span data-stu-id="74dbe-445">The list of parameters the command takes.</span></span> <span data-ttu-id="74dbe-446">Minimum: 1; Maximum: 5</span><span class="sxs-lookup"><span data-stu-id="74dbe-446">Minimum: 1; maximum: 5</span></span>|
|`parameter.name`|<span data-ttu-id="74dbe-447">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="74dbe-447">String</span></span>|<span data-ttu-id="74dbe-448">64 Zeichen</span><span class="sxs-lookup"><span data-stu-id="74dbe-448">64 characters</span></span>|<span data-ttu-id="74dbe-449">✔</span><span class="sxs-lookup"><span data-stu-id="74dbe-449">✔</span></span>|<span data-ttu-id="74dbe-450">Der Name des Parameters, wie er im Client angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="74dbe-450">The name of the parameter as it appears in the client.</span></span> <span data-ttu-id="74dbe-451">Dies ist in der Benutzeranforderung enthalten.</span><span class="sxs-lookup"><span data-stu-id="74dbe-451">This is included in the user request.</span></span>|
|`parameter.title`|<span data-ttu-id="74dbe-452">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="74dbe-452">String</span></span>|<span data-ttu-id="74dbe-453">32 Zeichen</span><span class="sxs-lookup"><span data-stu-id="74dbe-453">32 characters</span></span>|<span data-ttu-id="74dbe-454">✔</span><span class="sxs-lookup"><span data-stu-id="74dbe-454">✔</span></span>|<span data-ttu-id="74dbe-455">Benutzerfreundlicher Titel für den Parameter.</span><span class="sxs-lookup"><span data-stu-id="74dbe-455">User-friendly title for the parameter.</span></span>|
|`parameter.description`|<span data-ttu-id="74dbe-456">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="74dbe-456">String</span></span>|<span data-ttu-id="74dbe-457">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="74dbe-457">128 characters</span></span>||<span data-ttu-id="74dbe-458">Benutzerfreundliche Zeichenfolge, die den Zweck dieses Parameters beschreibt.</span><span class="sxs-lookup"><span data-stu-id="74dbe-458">User-friendly string that describes this parameter’s purpose.</span></span>|
|`parameter.inputType`|<span data-ttu-id="74dbe-459">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="74dbe-459">String</span></span>|<span data-ttu-id="74dbe-460">128 Zeichen</span><span class="sxs-lookup"><span data-stu-id="74dbe-460">128 characters</span></span>||<span data-ttu-id="74dbe-461">Definiert den Typ des Steuerelements, das in einem Aufgaben `fetchTask: true`Modul für angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="74dbe-461">Defines the type of control displayed on a task module for `fetchTask: true`.</span></span> <span data-ttu-id="74dbe-462">Eine von `text`, `textarea`, `number`, `date`, `time`, `toggle`,`choiceset`</span><span class="sxs-lookup"><span data-stu-id="74dbe-462">One of `text`, `textarea`, `number`, `date`, `time`, `toggle`, `choiceset`</span></span>|
|`parameter.choices`|<span data-ttu-id="74dbe-463">Array von Objekten</span><span class="sxs-lookup"><span data-stu-id="74dbe-463">Array of Objects</span></span>|<span data-ttu-id="74dbe-464">10  </span><span class="sxs-lookup"><span data-stu-id="74dbe-464">10</span></span>||<span data-ttu-id="74dbe-465">Die Auswahloptionen für `choiceset`.</span><span class="sxs-lookup"><span data-stu-id="74dbe-465">The choice options for the `choiceset`.</span></span> <span data-ttu-id="74dbe-466">Nur verwenden, `parameter.inputType` wenn`choiceset`</span><span class="sxs-lookup"><span data-stu-id="74dbe-466">Use only when `parameter.inputType` is `choiceset`</span></span>|
|`parameter.choices.title`|<span data-ttu-id="74dbe-467">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="74dbe-467">String</span></span>|<span data-ttu-id="74dbe-468">128</span><span class="sxs-lookup"><span data-stu-id="74dbe-468">128</span></span>||<span data-ttu-id="74dbe-469">Titel der Auswahl</span><span class="sxs-lookup"><span data-stu-id="74dbe-469">Title of the choice</span></span>|
|`parameter.choices.value`|<span data-ttu-id="74dbe-470">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="74dbe-470">String</span></span>|<span data-ttu-id="74dbe-471">512</span><span class="sxs-lookup"><span data-stu-id="74dbe-471">512</span></span>||<span data-ttu-id="74dbe-472">Wert der Auswahl</span><span class="sxs-lookup"><span data-stu-id="74dbe-472">Value of the choice</span></span>|

## <a name="permissions"></a><span data-ttu-id="74dbe-473">Berechtigungen</span><span class="sxs-lookup"><span data-stu-id="74dbe-473">permissions</span></span>

<span data-ttu-id="74dbe-474">**Optional**</span><span class="sxs-lookup"><span data-stu-id="74dbe-474">**Optional**</span></span>

<span data-ttu-id="74dbe-475">Ein Array `string` , das angibt, welche Berechtigungen die APP anfordert, sodass Endbenutzer wissen, wie die Erweiterung ausgeführt wird.</span><span class="sxs-lookup"><span data-stu-id="74dbe-475">An array of `string` which specifies which permissions the app requests, which lets end users know how the extension will perform.</span></span> <span data-ttu-id="74dbe-476">Die folgenden Optionen sind nicht exklusiv:</span><span class="sxs-lookup"><span data-stu-id="74dbe-476">The following options are non-exclusive:</span></span>

* <span data-ttu-id="74dbe-477">`identity`&emsp; Erfordert Benutzeridentitätsinformationen</span><span class="sxs-lookup"><span data-stu-id="74dbe-477">`identity` &emsp; Requires user identity information</span></span>
* <span data-ttu-id="74dbe-478">`messageTeamMembers`&emsp; Erfordert die Berechtigung zum Senden von direkten Nachrichten an Teammitglieder.</span><span class="sxs-lookup"><span data-stu-id="74dbe-478">`messageTeamMembers` &emsp; Requires permission to send direct messages to team members</span></span>

<span data-ttu-id="74dbe-479">Wenn Sie diese Berechtigungen beim Aktualisieren Ihrer APP ändern, werden die Benutzer beim ersten Ausführen der aktualisierten App den Zustimmungsprozess wiederholen.</span><span class="sxs-lookup"><span data-stu-id="74dbe-479">Changing these permissions when updating your app will cause your users to repeat the consent process the first time they run the updated app.</span></span> <span data-ttu-id="74dbe-480">Weitere Informationen finden Sie unter [Aktualisieren Ihrer APP](~/concepts/deploy-and-publish/appsource/post-publish/overview.md) .</span><span class="sxs-lookup"><span data-stu-id="74dbe-480">See [Updating your app](~/concepts/deploy-and-publish/appsource/post-publish/overview.md) for more information.</span></span>

## <a name="devicepermissions"></a><span data-ttu-id="74dbe-481">devicePermissions</span><span class="sxs-lookup"><span data-stu-id="74dbe-481">devicePermissions</span></span>

<span data-ttu-id="74dbe-482">**Optional** Array von Zeichenfolgen</span><span class="sxs-lookup"><span data-stu-id="74dbe-482">**Optional** Array of Strings</span></span>

<span data-ttu-id="74dbe-483">Gibt die systemeigenen Funktionen auf dem Gerät eines Benutzers an, für die Ihre APP möglicherweise Zugriff anfordern kann.</span><span class="sxs-lookup"><span data-stu-id="74dbe-483">Specifies the native features on a user's device that your app may request access to.</span></span> <span data-ttu-id="74dbe-484">Die Optionen lauten wie folgt:</span><span class="sxs-lookup"><span data-stu-id="74dbe-484">Options are:</span></span>

* `geolocation`
* `media`
* `notifications`
* `midi`
* `openExternal`

## <a name="validdomains"></a><span data-ttu-id="74dbe-485">validDomains</span><span class="sxs-lookup"><span data-stu-id="74dbe-485">validDomains</span></span>

<span data-ttu-id="74dbe-486">**Optional**, sofern angegeben, außer **erforderlich**</span><span class="sxs-lookup"><span data-stu-id="74dbe-486">**Optional**, except **Required** where noted</span></span>

<span data-ttu-id="74dbe-487">Eine Liste gültiger Domänen für Websites, die von der APP im Microsoft Teams-Client zu laden erwartet werden.</span><span class="sxs-lookup"><span data-stu-id="74dbe-487">A list of valid domains for websites the app expects to load within the Teams client.</span></span> <span data-ttu-id="74dbe-488">Domänen Auflistungen können beispielsweise `*.example.com`Platzhalterzeichen enthalten.</span><span class="sxs-lookup"><span data-stu-id="74dbe-488">Domain listings can include wildcards, for example `*.example.com`.</span></span> <span data-ttu-id="74dbe-489">Dies entspricht genau einem Segment der Domäne. Wenn Sie eine Übereinstimmung `a.b.example.com` benötigen, `*.*.example.com`verwenden Sie.</span><span class="sxs-lookup"><span data-stu-id="74dbe-489">This matches exactly one segment of the domain; if you need to match `a.b.example.com` then use `*.*.example.com`.</span></span> <span data-ttu-id="74dbe-490">Wenn Ihre Registerkartenkonfiguration oder Inhalts-UI neben einer Verwendung für die Registerkartenkonfiguration zu einer anderen Domäne navigieren muss, muss diese Domäne hier angegeben werden.</span><span class="sxs-lookup"><span data-stu-id="74dbe-490">If your tab configuration or content UI needs to navigate to any other domain besides the one use for tab configuration, that domain must be specified here.</span></span>

<span data-ttu-id="74dbe-491">Es ist jedoch **nicht** erforderlich, die Domänen von Identitätsanbietern einzubeziehen, die Sie in Ihrer APP unterstützen möchten.</span><span class="sxs-lookup"><span data-stu-id="74dbe-491">It is **not** necessary to include the domains of identity providers you want to support in your app, however.</span></span> <span data-ttu-id="74dbe-492">Um beispielsweise mit einer Google-ID zu authentifizieren, müssen Sie zu Accounts.Google.com umgeleitet werden, aber Sie sollten Accounts.Google.com nicht in `validDomains[]`einschließen.</span><span class="sxs-lookup"><span data-stu-id="74dbe-492">For example, to authenticate using a Google ID, it's necessary to redirect to accounts.google.com, but you should not include accounts.google.com in `validDomains[]`.</span></span>

<span data-ttu-id="74dbe-493">Microsoft Teams-apps, die ihre eigenen SharePoint-URLs benötigen, um gut zu funktionieren, können "{teamsitedomain}" in Ihre gültige Domänenliste einschließen.</span><span class="sxs-lookup"><span data-stu-id="74dbe-493">Teams apps that require their own sharepoint URLs to function well, may include "{teamsitedomain}" in their valid domain list.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="74dbe-494">Fügen Sie keine Domänen hinzu, die sich außerhalb des Steuerelements befinden, entweder direkt oder über Platzhalter.</span><span class="sxs-lookup"><span data-stu-id="74dbe-494">Do not add domains that are outside your control, either directly or via wildcards.</span></span> <span data-ttu-id="74dbe-495">Beispielsweise `yourapp.onmicrosoft.com` ist gültig, jedoch `*.onmicrosoft.com` ungültig.</span><span class="sxs-lookup"><span data-stu-id="74dbe-495">For example, `yourapp.onmicrosoft.com` is valid, but `*.onmicrosoft.com` is not valid.</span></span>

<span data-ttu-id="74dbe-496">Das Objekt ist ein Array mit allen Elementen des Typs `string`.</span><span class="sxs-lookup"><span data-stu-id="74dbe-496">The object is an array with all elements of the type `string`.</span></span>

## <a name="webapplicationinfo"></a><span data-ttu-id="74dbe-497">webApplicationInfo</span><span class="sxs-lookup"><span data-stu-id="74dbe-497">webApplicationInfo</span></span>

<span data-ttu-id="74dbe-498">**Optional**</span><span class="sxs-lookup"><span data-stu-id="74dbe-498">**Optional**</span></span>

<span data-ttu-id="74dbe-499">Geben Sie Ihre Aad-APP-ID und Diagramm Informationen an, damit Benutzer sich nahtlos bei ihrer Aad-App anmelden können.</span><span class="sxs-lookup"><span data-stu-id="74dbe-499">Specify your AAD App ID and Graph information to help users seamlessly sign into your AAD app.</span></span>

|<span data-ttu-id="74dbe-500">Name</span><span class="sxs-lookup"><span data-stu-id="74dbe-500">Name</span></span>| <span data-ttu-id="74dbe-501">Typ</span><span class="sxs-lookup"><span data-stu-id="74dbe-501">Type</span></span>| <span data-ttu-id="74dbe-502">Maximale Größe</span><span class="sxs-lookup"><span data-stu-id="74dbe-502">Maximum size</span></span> | <span data-ttu-id="74dbe-503">Erforderlich</span><span class="sxs-lookup"><span data-stu-id="74dbe-503">Required</span></span> | <span data-ttu-id="74dbe-504">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="74dbe-504">Description</span></span>|
|---|---|---|---|---|
|`id`|<span data-ttu-id="74dbe-505">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="74dbe-505">String</span></span>|<span data-ttu-id="74dbe-506">36 Zeichen</span><span class="sxs-lookup"><span data-stu-id="74dbe-506">36 characters</span></span>|<span data-ttu-id="74dbe-507">✔</span><span class="sxs-lookup"><span data-stu-id="74dbe-507">✔</span></span>|<span data-ttu-id="74dbe-508">Aad-Anwendungs-ID der app.</span><span class="sxs-lookup"><span data-stu-id="74dbe-508">AAD application id of the app.</span></span> <span data-ttu-id="74dbe-509">Diese ID muss eine GUID sein.</span><span class="sxs-lookup"><span data-stu-id="74dbe-509">This id must be a GUID.</span></span>|
|`resource`|<span data-ttu-id="74dbe-510">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="74dbe-510">String</span></span>|<span data-ttu-id="74dbe-511">2048 Zeichen</span><span class="sxs-lookup"><span data-stu-id="74dbe-511">2048 characters</span></span>|<span data-ttu-id="74dbe-512">✔</span><span class="sxs-lookup"><span data-stu-id="74dbe-512">✔</span></span>|<span data-ttu-id="74dbe-513">Ressourcen-URL der APP zum Abrufen des Authentifizierungstokens für SSO.</span><span class="sxs-lookup"><span data-stu-id="74dbe-513">Resource url of app for acquiring auth token for SSO.</span></span>|
