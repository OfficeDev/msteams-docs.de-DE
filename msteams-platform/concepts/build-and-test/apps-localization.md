---
title: Lokalisieren IhrerApp
description: Beschreibt Überlegungen zum Lokalisieren Ihrer Microsoft Teams-App.
ms.topic: conceptual
localization_priority: Normal
keywords: Teams veröffentlichen die AppSource-Lokalisierungssprache für Store-Veröffentlichungen
ms.date: 05/15/2018
ms.openlocfilehash: c73188bb24960b9ef0706955d09d23b618c04e5c
ms.sourcegitcommit: 4d9d1542e04abacfb252511c665a7229d8bb7162
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/25/2021
ms.locfileid: "53140040"
---
# <a name="localize-your-app"></a><span data-ttu-id="72a4e-104">Lokalisieren IhrerApp</span><span class="sxs-lookup"><span data-stu-id="72a4e-104">Localize your app</span></span>

<span data-ttu-id="72a4e-105">Sie müssen die folgenden Faktoren berücksichtigen, um Ihre Microsoft Teams-App zu lokalisieren:</span><span class="sxs-lookup"><span data-stu-id="72a4e-105">You must consider the following factors to localize your Microsoft Teams app:</span></span>

1. <span data-ttu-id="72a4e-106">[Lokalisieren Sie Ihren AppSource-Eintrag.](#localize-your-appsource-listing)</span><span class="sxs-lookup"><span data-stu-id="72a4e-106">[Localize your AppSource listing](#localize-your-appsource-listing).</span></span>
1. <span data-ttu-id="72a4e-107">[Lokalisieren Sie Zeichenfolgen in Ihrem App-Manifest.](#localize-strings-in-your-app-manifest)</span><span class="sxs-lookup"><span data-stu-id="72a4e-107">[Localize strings in your app manifest](#localize-strings-in-your-app-manifest).</span></span> 
1. <span data-ttu-id="72a4e-108">[Behandeln sie lokalisierte Textübermittlungen von Ihren Benutzern.](#handle-localized-text-submissions-from-your-users)</span><span class="sxs-lookup"><span data-stu-id="72a4e-108">[Handle localized text submissions from your users](#handle-localized-text-submissions-from-your-users).</span></span>

## <a name="localize-your-appsource-listing"></a><span data-ttu-id="72a4e-109">Lokalisieren Ihres AppSource-Eintrags</span><span class="sxs-lookup"><span data-stu-id="72a4e-109">Localize your AppSource listing</span></span>

<span data-ttu-id="72a4e-110">Wenn Sie die App im Store veröffentlichen, müssen Sie beachten, dass die Lokalisierung Ihres AppSource-Eintrags noch nicht unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="72a4e-110">If you are publishing the app to the store, you must be aware that localizing your AppSource listing is not yet supported.</span></span> <span data-ttu-id="72a4e-111">Um lokalisierte Einträge im App Store zu unterstützen, können Sie Ihrem Eintrag zusätzliche Sprachen hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="72a4e-111">To support localized listings in the app store, you can add additional languages to your listing.</span></span> <span data-ttu-id="72a4e-112">Die Standardspracheninformationen, die Sie im [Partner Center](/office/dev/store/submit-to-appsource-via-partner-center) für Ihren Eintrag angeben, werden im [AppSource-Websiteeintrag](https://appsource.microsoft.com/marketplace/apps?product=office%3Bteams&page=1) für Ihre App angezeigt.</span><span class="sxs-lookup"><span data-stu-id="72a4e-112">The default language information you provide in [Partner Center](/office/dev/store/submit-to-appsource-via-partner-center) for your listing appears in the [AppSource website](https://appsource.microsoft.com/marketplace/apps?product=office%3Bteams&page=1) listing for your app.</span></span> <span data-ttu-id="72a4e-113">Derzeit lautet die Standardsprache Englisch.</span><span class="sxs-lookup"><span data-stu-id="72a4e-113">Currently, the default language is English.</span></span>

### <a name="configure-localization"></a><span data-ttu-id="72a4e-114">Konfigurieren der Lokalisierung</span><span class="sxs-lookup"><span data-stu-id="72a4e-114">Configure localization</span></span>

<span data-ttu-id="72a4e-115">Um eine zusätzliche Sprache für Ihre App zu konfigurieren, wählen Sie im [Partner Center](/office/dev/store/submit-to-appsource-via-partner-center)sowohl Englisch als auch die zusätzliche Sprache der App aus.</span><span class="sxs-lookup"><span data-stu-id="72a4e-115">To configure an additional language for your app, in [Partner Center](/office/dev/store/submit-to-appsource-via-partner-center), select both English and the additional language of the app.</span></span> <span data-ttu-id="72a4e-116">Französisch wird im folgenden Beispiel als zusätzliche Sprache verwendet:</span><span class="sxs-lookup"><span data-stu-id="72a4e-116">French is used as an additional language in the following example:</span></span>

1. <span data-ttu-id="72a4e-117">Hinzufügen von Englisch</span><span class="sxs-lookup"><span data-stu-id="72a4e-117">Add English language</span></span>
    * <span data-ttu-id="72a4e-118">Geben Sie den App-Namen ein.</span><span class="sxs-lookup"><span data-stu-id="72a4e-118">Enter the app name.</span></span>
    * <span data-ttu-id="72a4e-119">Geben Sie eine kurze Beschreibung der App in Englisch ein.</span><span class="sxs-lookup"><span data-stu-id="72a4e-119">Enter a short description of the app in English.</span></span>
    * <span data-ttu-id="72a4e-120">Geben Sie die lange Beschreibung der App in Englisch ein.</span><span class="sxs-lookup"><span data-stu-id="72a4e-120">Enter the long description of the app in English.</span></span>
    * <span data-ttu-id="72a4e-121">Geben Sie in der langen Beschreibung Folgendes ein: **Diese App ist auf Französisch verfügbar.**</span><span class="sxs-lookup"><span data-stu-id="72a4e-121">In the long description, enter: **This app is available in French**.</span></span>
    * <span data-ttu-id="72a4e-122">Hochladen die Bilder Der App-UI (in Englisch).</span><span class="sxs-lookup"><span data-stu-id="72a4e-122">Upload the images of your app UI (in English).</span></span>
2. <span data-ttu-id="72a4e-123">Hinzufügen der Sprache Französisch</span><span class="sxs-lookup"><span data-stu-id="72a4e-123">Add French language</span></span>
    * <span data-ttu-id="72a4e-124">Geben Sie den App-Namen ein.</span><span class="sxs-lookup"><span data-stu-id="72a4e-124">Enter the app name.</span></span>
    * <span data-ttu-id="72a4e-125">Geben Sie eine kurze Beschreibung der App auf Französisch ein.</span><span class="sxs-lookup"><span data-stu-id="72a4e-125">Enter a short description of the app in French.</span></span>
    * <span data-ttu-id="72a4e-126">Geben Sie die lange Beschreibung der App auf Französisch ein.</span><span class="sxs-lookup"><span data-stu-id="72a4e-126">Enter the long description of the app in French.</span></span>
    * <span data-ttu-id="72a4e-127">Hochladen die Bilder Der App-UI (auf Französisch).</span><span class="sxs-lookup"><span data-stu-id="72a4e-127">Upload the images of your app UI (in French).</span></span>

<span data-ttu-id="72a4e-128">Die Bilder, die Sie mit der englischen Sprache hochladen, werden in AppSource verwendet.</span><span class="sxs-lookup"><span data-stu-id="72a4e-128">The images that you upload with the English language are used in AppSource.</span></span>

## <a name="localize-strings-in-your-app-manifest"></a><span data-ttu-id="72a4e-129">Lokalisieren von Zeichenfolgen im App-Manifest</span><span class="sxs-lookup"><span data-stu-id="72a4e-129">Localize strings in your app manifest</span></span>

<span data-ttu-id="72a4e-130">Sie müssen das Microsoft Teams-App-Schema `v1.5` und höher verwenden, um Ihre App zu lokalisieren.</span><span class="sxs-lookup"><span data-stu-id="72a4e-130">You must use the Microsoft Teams app schema `v1.5` and later to localize your app.</span></span> <span data-ttu-id="72a4e-131">Sie können dies tun, indem Sie das Attribut in Ihrer manifest.jsfür die Datei auf oder höher festlegen `$schema` und die Eigenschaft auf Version aktualisieren **https://developer.microsoft.com/en-us/json-schemas/teams/v1.5/MicrosoftTeams.schema.json** `manifestVersion` `$schema` `1.5` (in diesem Fall).</span><span class="sxs-lookup"><span data-stu-id="72a4e-131">You can do this by setting the `$schema` attribute in your manifest.json file to **https://developer.microsoft.com/en-us/json-schemas/teams/v1.5/MicrosoftTeams.schema.json** or higher and updating the `manifestVersion` property to `$schema` version (`1.5` in this case).</span></span> 

<span data-ttu-id="72a4e-132">Sie müssen die `localizationInfo` Eigenschaft mit der von der Anwendung unterstützten Standardsprache hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="72a4e-132">You must add the `localizationInfo` property with the default language that your application supports.</span></span> <span data-ttu-id="72a4e-133">Die Standardsprache wird als endgültige Fallbacksprache verwendet, wenn die Clienteinstellungen des Benutzers mit keiner ihrer zusätzlichen Sprachen übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="72a4e-133">The default language is used as the final fallback language if the user's client settings do not match with any of your additional languages.</span></span>

### <a name="example-manifestjson-change"></a><span data-ttu-id="72a4e-134">Beispiel manifest.jszur Änderung</span><span class="sxs-lookup"><span data-stu-id="72a4e-134">Example manifest.json change</span></span>

<span data-ttu-id="72a4e-135">Mithilfe der folgenden manifest.jskönnen Sie die `localizationInfo` Eigenschaft mit der Standardsprache hinzufügen, die Ihre Anwendung zusammen mit `additionalLanguages` unterstützt:</span><span class="sxs-lookup"><span data-stu-id="72a4e-135">The following manifest.json helps to add the `localizationInfo` property with the default language that your application supports along with `additionalLanguages`:</span></span>

```json
{
  "$schema": "https://developer.microsoft.com/en-us/json-schemas/teams/v1.5/MicrosoftTeams.schema.json",
  "manifestVersion": "1.5",
  "localizationInfo": {
        "defaultLanguageTag": "en",
        "additionalLanguages": [
            {
                "languageTag": "es-mx",
                "file": "es-mx.json"
            }
        ]
    }
  ...
}
```

### <a name="example-localization-json-change"></a><span data-ttu-id="72a4e-136">Beispiel für eine Json-Lokalisierungsänderung</span><span class="sxs-lookup"><span data-stu-id="72a4e-136">Example localization .json change</span></span>

<span data-ttu-id="72a4e-137">Es folgt ein Beispiel für die Lokalisierung von JSON:</span><span class="sxs-lookup"><span data-stu-id="72a4e-137">Following is an example for localization .json:</span></span>

```json
{
  "$schema": "https://developer.microsoft.com/en-us/json-schemas/teams/v1.5/MicrosoftTeams.Localization.schema.json",
  "manifestVersion": "1.5",
  "name.short": "Localización",
  "name.full": "Aplicación de localización",
  ...
}
```


<span data-ttu-id="72a4e-138">Sie können zusätzliche JSON-Dateien mit Übersetzungen aller benutzerorientierten Zeichenfolgen in Ihrem Manifest bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="72a4e-138">You can provide additional .json files with translations of all the user facing strings in your manifest.</span></span> <span data-ttu-id="72a4e-139">Diese Dateien müssen dem [JSON-Schema der Lokalisierungsdatei](../../resources/schema/localization-schema.md) entsprechen und der Eigenschaft Ihres Manifests hinzugefügt `localizationInfo` werden.</span><span class="sxs-lookup"><span data-stu-id="72a4e-139">These files must adhere to the [Localization file JSON schema](../../resources/schema/localization-schema.md) and they must be added to the `localizationInfo` property of your manifest.</span></span> <span data-ttu-id="72a4e-140">Jede Datei korreliert mit einem Sprachtag, das der Teams Client verwendet, um die entsprechenden Zeichenfolgen auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="72a4e-140">Each file correlates to a language tag, which the Teams client uses to select the appropriate strings.</span></span> <span data-ttu-id="72a4e-141">Das Sprachtag hat die Form, `<language>-<region>` aber Sie können den Teil weglassen, um auf alle Regionen `<region>` abzuzielen, die die gewünschte Sprache unterstützen.</span><span class="sxs-lookup"><span data-stu-id="72a4e-141">The language tag takes the form of `<language>-<region>` but you can omit the `<region>` portion to target all regions that support the desired language.</span></span>

<span data-ttu-id="72a4e-142">Der Teams Client wendet die Zeichenfolgen in der folgenden Reihenfolge an: Standardmäßige Sprachzeichenfolgen – > Nur Sprache des Benutzers – > Sprache des Benutzers + Regionszeichenfolgen des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="72a4e-142">The Teams client applies the strings in the following order: default language strings -> user's language only strings -> user's language + user's region strings.</span></span>

<span data-ttu-id="72a4e-143">Sie geben beispielsweise die Standardsprache "fr" (Französisch, alle Regionen) und zusätzliche Sprachdateien für "en" (Englisch, alle Regionen) und "en-gb" (Englisch, großes Großbritannien) an. Die Sprache des Benutzers ist auf "en-gb" festgelegt.</span><span class="sxs-lookup"><span data-stu-id="72a4e-143">For example, you provide a default language of 'fr' (French, all regions), and additional language files for 'en' (English, all regions) and 'en-gb' (English, Great Britain), the user's language is set to 'en-gb'.</span></span> <span data-ttu-id="72a4e-144">Die folgenden Änderungen erfolgen basierend auf der Sprachauswahl:</span><span class="sxs-lookup"><span data-stu-id="72a4e-144">The following changes take place based on the language selection:</span></span>

1. <span data-ttu-id="72a4e-145">Der Teams Client übernimmt die Zeichenfolgen "fr" und überschreibt sie mit den Zeichenfolgen "en".</span><span class="sxs-lookup"><span data-stu-id="72a4e-145">The Teams client takes the 'fr' strings and overwrite them with the 'en' strings.</span></span>
1. <span data-ttu-id="72a4e-146">Überschreiben Sie die Zeichenfolgen "en" mit den Zeichenfolgen "en-gb".</span><span class="sxs-lookup"><span data-stu-id="72a4e-146">Overwrite the 'en' strings with the 'en-gb' strings.</span></span>

<span data-ttu-id="72a4e-147">Wenn die Sprache des Benutzers auf "en-ca" festgelegt ist, werden die folgenden Änderungen basierend auf der Sprachauswahl vorgenommen:</span><span class="sxs-lookup"><span data-stu-id="72a4e-147">If the user's language is set to 'en-ca', the following changes take place based on the language selection:</span></span> 

1. <span data-ttu-id="72a4e-148">Der Teams Client übernimmt die Zeichenfolgen "fr" und überschreibt sie mit den Zeichenfolgen "en".</span><span class="sxs-lookup"><span data-stu-id="72a4e-148">The Teams client takes the 'fr' strings and overwrite them with the 'en' strings.</span></span>
1. <span data-ttu-id="72a4e-149">Da keine Lokalisierung "en-ca" angegeben wird, werden die "en"-Lokalisierungen verwendet.</span><span class="sxs-lookup"><span data-stu-id="72a4e-149">Since no 'en-ca' localization is supplied, the 'en\` localizations are used.</span></span>

<span data-ttu-id="72a4e-150">Wenn die Sprache des Benutzers auf "es-es" festgelegt ist, übernimmt der Teams Client die Zeichenfolgen "fr".</span><span class="sxs-lookup"><span data-stu-id="72a4e-150">If the user's language is set to 'es-es', the Teams client takes the 'fr' strings.</span></span> <span data-ttu-id="72a4e-151">Der Teams Client überschreibt die Zeichenfolgen nicht mit einer der Sprachdateien, da keine Übersetzung von "es" oder "es-es" bereitgestellt wird.</span><span class="sxs-lookup"><span data-stu-id="72a4e-151">The Teams client does not override the strings with any of the language files as no 'es' or 'es-es' translation is provided.</span></span>

<span data-ttu-id="72a4e-152">Daher müssen Sie nur Übersetzungen auf oberster Ebene in Ihrem Manifest bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="72a4e-152">Therefore, you must provide top level, language only translations in your manifest.</span></span> <span data-ttu-id="72a4e-153">Beispiel: "en" anstelle von "en-us".</span><span class="sxs-lookup"><span data-stu-id="72a4e-153">For example, 'en' instead of 'en-us'.</span></span> <span data-ttu-id="72a4e-154">Sie müssen Außerkraftsetzungen auf Regionsebene nur für die wenigen Zeichenfolgen bereitstellen, die sie benötigen.</span><span class="sxs-lookup"><span data-stu-id="72a4e-154">You must provide region level overrides only for the few strings that need them.</span></span> 

### <a name="example-manifestjson-change"></a><span data-ttu-id="72a4e-155">Beispiel manifest.jszur Änderung</span><span class="sxs-lookup"><span data-stu-id="72a4e-155">Example manifest.json change</span></span>

<span data-ttu-id="72a4e-156">Die manifest.jszur Änderung wird im folgenden Beispiel gezeigt:</span><span class="sxs-lookup"><span data-stu-id="72a4e-156">The manifest.json change is shown in the following example:</span></span>

```json
{
  ...
  "localizationInfo": {
    "defaultLanguageTag": "en",
    "additionalLanguages": [
      {
        "languageTag": "en-gb",
        "file": "en-gb.json"
      },
      {
        "languageTag": "fr",
        "file": "fr.json"
      },
      {
        "languageTag": "pl",
        "file": "pl.json"
      }
    ]
  }
  ...
}
```

### <a name="example-localization-json-file"></a><span data-ttu-id="72a4e-157">Beispiel für die Lokalisierung der JSON-Datei</span><span class="sxs-lookup"><span data-stu-id="72a4e-157">Example localization .json file</span></span>

 <span data-ttu-id="72a4e-158">Die localization.jszur Änderung wird im folgenden Beispiel gezeigt:</span><span class="sxs-lookup"><span data-stu-id="72a4e-158">The localization.json change is shown in the following example:</span></span>

```json
{
  "$schema": "https://developer.microsoft.com/en-us/json-schemas/teams/v1.8/MicrosoftTeams.Localization.schema.json",
  "name.short": "Le App",
  "name.full": "App pour Microsoft Teams",
  "description.short": "Créez d'excellentes applications pour Microsoft Teams avec App.",
  "description.full": "Créez de nouvelles applications Microsoft Teams, concevez et prévisualisez des cartes bot, et explorez la documentation avec App.",
  "staticTabs[0].name": "Editeur de manifest",
  "staticTabs[1].name": "Editeur de cartes",
  "staticTabs[2].name": "Bibliothèque de contrôles",
  "bots[0].commandLists[0].commands[0].title": "chercher",
  "bots[0].commandLists[0].commands[0].description": "Rechercher la documentation Teams pertinente"
}
```

## <a name="handle-localized-text-submissions-from-your-users"></a><span data-ttu-id="72a4e-159">Behandeln lokalisierter Textübermittlungen von Benutzern</span><span class="sxs-lookup"><span data-stu-id="72a4e-159">Handle localized text submissions from your users</span></span>

<span data-ttu-id="72a4e-160">Wenn Sie lokalisierte Versionen Ihrer Anwendung bereitstellen, antworten die Benutzer mit derselben Sprache.</span><span class="sxs-lookup"><span data-stu-id="72a4e-160">If your provide localized versions of your application, the users respond with the same language.</span></span> <span data-ttu-id="72a4e-161">Da Teams die Benutzerübermittlungen nicht zurück in die Standardsprache übersetzt, muss Ihre App die lokalisierten Sprachantworten verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="72a4e-161">As Teams does not translate the user submissions back to the default language, your app must handle the localized language responses.</span></span> <span data-ttu-id="72a4e-162">Wenn Sie beispielsweise einen lokalisierten Befehl `commandList` bereitstellen, sind die Antworten auf Ihren Bot der lokalisierte Text des Befehls und nicht die Standardsprache.</span><span class="sxs-lookup"><span data-stu-id="72a4e-162">For example, if you provide a localized `commandList`, the responses to your bot are the localized text of the command, not the default language.</span></span> <span data-ttu-id="72a4e-163">Ihre App muss entsprechend reagieren.</span><span class="sxs-lookup"><span data-stu-id="72a4e-163">Your app must respond appropriately.</span></span>

## <a name="code-sample"></a><span data-ttu-id="72a4e-164">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="72a4e-164">Code sample</span></span>

| <span data-ttu-id="72a4e-165">Beispielname</span><span class="sxs-lookup"><span data-stu-id="72a4e-165">Sample name</span></span> | <span data-ttu-id="72a4e-166">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="72a4e-166">Description</span></span> | <span data-ttu-id="72a4e-167">.NET</span><span class="sxs-lookup"><span data-stu-id="72a4e-167">.NET</span></span> | <span data-ttu-id="72a4e-168">Node.js</span><span class="sxs-lookup"><span data-stu-id="72a4e-168">Node.js</span></span> |
|-------------|-------------|------|------|
| <span data-ttu-id="72a4e-169">App-Lokalisierung</span><span class="sxs-lookup"><span data-stu-id="72a4e-169">App Localization</span></span> | <span data-ttu-id="72a4e-170">Microsoft Teams App-Lokalisierung mit Bot und Registerkarte.</span><span class="sxs-lookup"><span data-stu-id="72a4e-170">Microsoft Teams app localization using bot and tab.</span></span> | [<span data-ttu-id="72a4e-171">View</span><span class="sxs-lookup"><span data-stu-id="72a4e-171">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-localization/csharp) |[<span data-ttu-id="72a4e-172">View</span><span class="sxs-lookup"><span data-stu-id="72a4e-172">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-localization/nodejs) |

