---
title: Lokalisierung für Ihre App
description: Beschreibt Überlegungen zum Lokalisieren Microsoft Teams App.
ms.topic: conceptual
localization_priority: Normal
keywords: Teams veröffentlichen Store Office Publishing AppSource-Lokalisierungssprache
ms.date: 05/15/2018
ms.openlocfilehash: 6dbdeb6d16c99aada23f8d74a92d958f9c29b69d
ms.sourcegitcommit: 118f7261d313feeac5b398fef56a44bd90104b2f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/31/2021
ms.locfileid: "52709628"
---
# <a name="localization-for-microsoft-teams-apps"></a><span data-ttu-id="c2a71-104">Lokalisierung für Microsoft Teams Apps</span><span class="sxs-lookup"><span data-stu-id="c2a71-104">Localization for Microsoft Teams apps</span></span>

<span data-ttu-id="c2a71-105">Beim Lokalisieren Microsoft Teams App müssen Sie Folgendes berücksichtigen:</span><span class="sxs-lookup"><span data-stu-id="c2a71-105">When localizing your Microsoft Teams app, you must consider the following:</span></span>

1. <span data-ttu-id="c2a71-106">Ihr Teams Store-Eintrag (falls zutreffend).</span><span class="sxs-lookup"><span data-stu-id="c2a71-106">Your Teams store listing (if applicable).</span></span>
1. <span data-ttu-id="c2a71-107">Die Zeichenfolgen, die dem Endbenutzer in Ihrem App-Manifest angezeigt werden.</span><span class="sxs-lookup"><span data-stu-id="c2a71-107">The end-user facing strings in your app manifest.</span></span> <span data-ttu-id="c2a71-108">Beispiel: Botbefehle.</span><span class="sxs-lookup"><span data-stu-id="c2a71-108">For example bot commands.</span></span>
1. <span data-ttu-id="c2a71-109">Reagieren auf lokalisierten Text, der von Ihren Benutzern übermittelt wurde.</span><span class="sxs-lookup"><span data-stu-id="c2a71-109">Responding to localized text submitted from your users.</span></span>

## <a name="localizing-your-appsource-listing"></a><span data-ttu-id="c2a71-110">Lokalisieren Ihres AppSource-Eintrags</span><span class="sxs-lookup"><span data-stu-id="c2a71-110">Localizing your AppSource listing</span></span>

<span data-ttu-id="c2a71-111">Wenn Sie im Store veröffentlichen, müssen Sie beachten, dass das Lokalisieren Ihres AppSource-Eintrags noch nicht unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="c2a71-111">If you're publishing to the store, you need to be aware that localizing your AppSource listing is not yet supported.</span></span> <span data-ttu-id="c2a71-112">In Vorbereitung auf die Unterstützung lokalisierter Einträge im App Store können Sie ihrem Eintrag jedoch weitere Sprachen hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="c2a71-112">However, in preparation for support for localized listings in the app store you can add additional languages to your listing.</span></span> <span data-ttu-id="c2a71-113">Derzeit werden nur die standardmäßigen (englischen) Sprachinformationen, die Sie im [Partner Center](/office/dev/store/submit-to-appsource-via-partner-center) für Ihren Eintrag bereitstellen, im [AppSource-Websiteeintrag](https://appsource.microsoft.com/marketplace/apps?product=office%3Bteams&page=1) für Ihre App angezeigt.</span><span class="sxs-lookup"><span data-stu-id="c2a71-113">Currently only the default (English) language information you provide in [Partner Center](/office/dev/store/submit-to-appsource-via-partner-center) for your listing will appear in the [AppSource website](https://appsource.microsoft.com/marketplace/apps?product=office%3Bteams&page=1) listing for your app.</span></span>

### <a name="example-of-configuring-localization"></a><span data-ttu-id="c2a71-114">Beispiel für die Konfiguration der Lokalisierung</span><span class="sxs-lookup"><span data-stu-id="c2a71-114">Example of configuring localization</span></span>

<span data-ttu-id="c2a71-115">Um eine zusätzliche Sprache für Ihre App zu konfigurieren, wählen Sie im [Partner Center](/office/dev/store/submit-to-appsource-via-partner-center)sowohl Englisch als auch die zusätzliche Sprache der App aus.</span><span class="sxs-lookup"><span data-stu-id="c2a71-115">To configure an additional language for your app, in [Partner Center](/office/dev/store/submit-to-appsource-via-partner-center), select both English and the additional language of the app.</span></span> <span data-ttu-id="c2a71-116">In diesem Beispiel wird Französisch verwendet:</span><span class="sxs-lookup"><span data-stu-id="c2a71-116">French is used in this example:</span></span>

1. <span data-ttu-id="c2a71-117">Hinzufügen von Englisch</span><span class="sxs-lookup"><span data-stu-id="c2a71-117">Add English language</span></span>
    * <span data-ttu-id="c2a71-118">Geben Sie den Namen der App ein.</span><span class="sxs-lookup"><span data-stu-id="c2a71-118">Fill in the app name.</span></span>
    * <span data-ttu-id="c2a71-119">Geben Sie eine kurze Beschreibung der App in Englisch ein.</span><span class="sxs-lookup"><span data-stu-id="c2a71-119">Fill in a short description of the app in English.</span></span>
    * <span data-ttu-id="c2a71-120">Füllen Sie die lange Beschreibung der App in Englisch aus.</span><span class="sxs-lookup"><span data-stu-id="c2a71-120">Fill in the long description of the app in English.</span></span>
    * <span data-ttu-id="c2a71-121">Fügen Sie in der langen Beschreibung auch die Zeile "Diese App ist in "Französisch" verfügbar.</span><span class="sxs-lookup"><span data-stu-id="c2a71-121">In the long description, please also add the line “This app is available in “French”.</span></span>
    * <span data-ttu-id="c2a71-122">Hochladen die Bilder Ihrer App-UI (in Englisch).</span><span class="sxs-lookup"><span data-stu-id="c2a71-122">Upload the images of your app UI (in English).</span></span>
2. <span data-ttu-id="c2a71-123">Hinzufügen von Französisch</span><span class="sxs-lookup"><span data-stu-id="c2a71-123">Add French language</span></span>
    * <span data-ttu-id="c2a71-124">Geben Sie den Namen der App ein.</span><span class="sxs-lookup"><span data-stu-id="c2a71-124">Fill in the app name.</span></span>
    * <span data-ttu-id="c2a71-125">Geben Sie eine kurze Beschreibung der App auf Französisch ein.</span><span class="sxs-lookup"><span data-stu-id="c2a71-125">Fill in a short description of the app in French.</span></span>
    * <span data-ttu-id="c2a71-126">Füllen Sie die lange Beschreibung der App auf Französisch aus.</span><span class="sxs-lookup"><span data-stu-id="c2a71-126">Fill in the long description of the app in French.</span></span>
    * <span data-ttu-id="c2a71-127">Hochladen die Bilder Ihrer App-UI (auf Französisch).</span><span class="sxs-lookup"><span data-stu-id="c2a71-127">Upload the images of your app UI (in French).</span></span>

<span data-ttu-id="c2a71-128">Die Bilder, die Sie mit der englischen Sprache hochladen, werden in AppSource verwendet.</span><span class="sxs-lookup"><span data-stu-id="c2a71-128">The images you upload with the English language will be the ones used in AppSource.</span></span>

## <a name="localizing-the-strings-in-your-app-manifest"></a><span data-ttu-id="c2a71-129">Lokalisieren der Zeichenfolgen im App-Manifest</span><span class="sxs-lookup"><span data-stu-id="c2a71-129">Localizing the strings in your app manifest</span></span>

<span data-ttu-id="c2a71-130">Sie müssen das Microsoft Teams-App-Schema v1.5+ verwenden, um Ihre App ordnungsgemäß zu lokalisieren.</span><span class="sxs-lookup"><span data-stu-id="c2a71-130">You must use the Microsoft Teams app schema v1.5+ to properly localize your app.</span></span> <span data-ttu-id="c2a71-131">Dazu können Sie das Attribut in Ihrer manifest.json-Datei auf ' ' festlegen und die Eigenschaft `$schema` https://developer.microsoft.com/en-us/json-schemas/teams/v1.8/MicrosoftTeams.Localization.schema.json "manifestVersion" auf "1.7" aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="c2a71-131">You can do this by setting the `$schema` attribute in your manifest.json file to 'https://developer.microsoft.com/en-us/json-schemas/teams/v1.8/MicrosoftTeams.Localization.schema.json' and updating the 'manifestVersion' property to '1.7'.</span></span>

### <a name="example-manifestjson-change"></a><span data-ttu-id="c2a71-132">Beispiel manifest.jsbei Änderung</span><span class="sxs-lookup"><span data-stu-id="c2a71-132">Example manifest.json change</span></span>

```json
{
  "$schema": "https://developer.microsoft.com/en-us/json-schemas/teams/v1.8/MicrosoftTeams.Localization.schema.json",
  "manifestVersion": "1.5",
  ...
}
```

<span data-ttu-id="c2a71-133">Anschließend möchten Sie die Eigenschaft "localizationInfo" mit der Standardsprache hinzufügen, die ihre Anwendung unterstützt.</span><span class="sxs-lookup"><span data-stu-id="c2a71-133">You will then want to add the 'localizationInfo' property with the default language that your application supports.</span></span> <span data-ttu-id="c2a71-134">Die Standardsprache wird als endgültige Fallbacksprache verwendet, wenn die Clienteinstellungen des Benutzers keinem Ihrer zusätzlichen Sprachen entsprechen.</span><span class="sxs-lookup"><span data-stu-id="c2a71-134">The default language is used as the final fallback language if the user's client settings do not match any of your additional languages.</span></span>

### <a name="example-manifestjson-change"></a><span data-ttu-id="c2a71-135">Beispiel manifest.jsbei Änderung</span><span class="sxs-lookup"><span data-stu-id="c2a71-135">Example manifest.json change</span></span>

```json
{
  ...
  "localizationInfo": {
    "defaultLanguageTag": "en"
  }
  ...
}
```

<span data-ttu-id="c2a71-136">Sie können zusätzliche .json-Dateien mit Übersetzungen aller zeichenfolgen angezeigten Benutzer in Ihrem Manifest bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="c2a71-136">You can provide additional .json files with translations of all the user facing strings in your manifest.</span></span> <span data-ttu-id="c2a71-137">Diese Dateien müssen dem [JSON-Schema](../../resources/schema/localization-schema.md) der Lokalisierungsdatei entsprechen und der Eigenschaft "localizationInfo" Ihres Manifests hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="c2a71-137">These files must adhere to the [Localization file JSON schema](../../resources/schema/localization-schema.md) and they must be added to the 'localizationInfo' property of your manifest.</span></span> <span data-ttu-id="c2a71-138">Jede Datei korreliert mit einem Sprachtag, das Teams Client verwendet, um die entsprechenden Zeichenfolgen zu wählen.</span><span class="sxs-lookup"><span data-stu-id="c2a71-138">Each file correlates to a language tag which the Teams client uses to choose the appropriate strings.</span></span> <span data-ttu-id="c2a71-139">Das Sprachtag hat die Form, es wird jedoch empfohlen, den Teil weglassen, um alle Regionen zu verwenden, die <language> - <region> die gewünschte <region> Sprache unterstützen.</span><span class="sxs-lookup"><span data-stu-id="c2a71-139">The language tag takes the form of <language>-<region> but it is recommended to omit the <region> portion to target all regions that support the desired language.</span></span>

<span data-ttu-id="c2a71-140">Der Teams-Client wird die Zeichenfolgen in dieser Reihenfolge anwenden: Standardsprachzeichenfolgen -> der Sprache des Benutzers nur Zeichenfolgen -> Sprache des Benutzers + Regionenzeichenfolgen des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="c2a71-140">The Teams client will apply the strings in this order: default language strings -> user's language only strings -> user's language + user's region strings.</span></span>

<span data-ttu-id="c2a71-141">Sie stellen z. B. die Standardsprache "fr" (Französisch, alle Regionen) und zusätzliche Sprachdateien für "en" (Englisch, alle Regionen) und "en-gb" (Englisch, Großbritannien) zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="c2a71-141">For example, you provide a default language of 'fr' (French, all regions), and additional language files for 'en' (English, all regions) and 'en-gb' (English, Great Britain).</span></span> <span data-ttu-id="c2a71-142">Wenn die Sprache des Benutzers auf "en-gb" festgelegt ist:</span><span class="sxs-lookup"><span data-stu-id="c2a71-142">If the user's language is set to 'en-gb':</span></span>

1. <span data-ttu-id="c2a71-143">Der Teams-Client überschreibt die "fr"-Zeichenfolgen mit den Zeichenfolgen "en".</span><span class="sxs-lookup"><span data-stu-id="c2a71-143">The Teams client will take the 'fr' strings overwrite them with the 'en' strings.</span></span>
2. <span data-ttu-id="c2a71-144">Überschreiben Sie diese mit den Zeichenfolgen "en-gb".</span><span class="sxs-lookup"><span data-stu-id="c2a71-144">Overwrite those with the 'en-gb' strings.</span></span>

<span data-ttu-id="c2a71-145">Wenn die Sprache des Benutzers auf "en-ca" festgelegt ist:</span><span class="sxs-lookup"><span data-stu-id="c2a71-145">If the user's language is set to 'en-ca':</span></span> 

1. <span data-ttu-id="c2a71-146">Der Teams-Client überschreibt die "fr"-Zeichenfolgen mit den Zeichenfolgen "en".</span><span class="sxs-lookup"><span data-stu-id="c2a71-146">The Teams client will take the 'fr' strings overwrite them with the 'en' strings.</span></span>
2. <span data-ttu-id="c2a71-147">Da keine "en-ca"-Lokalisierung bereitgestellt wird, werden die "en"-Lokalisierungen verwendet.</span><span class="sxs-lookup"><span data-stu-id="c2a71-147">Since no 'en-ca' localization is supplied, the 'en' localizations will be used.</span></span>

<span data-ttu-id="c2a71-148">Wenn die Sprache des Benutzers auf "es-es" festgelegt ist, überschreibt der Teams-Client die "fr"-Zeichenfolgen und überschreibt sie nicht mit einer der Sprachdateien.</span><span class="sxs-lookup"><span data-stu-id="c2a71-148">If the user's language is set to 'es-es', the Teams client will take the 'fr' strings and will not override them with any of the language files.</span></span>

<span data-ttu-id="c2a71-149">Daher wird dringend empfohlen, nur Übersetzungen auf oberster Ebene in Ihrem Manifest ('en' statt 'en-us') zur Verfügung zu stellen und nur Überschreibungen auf Regionsebene für die wenigen Zeichenfolgen zur Verfügung zu stellen, die sie benötigen.</span><span class="sxs-lookup"><span data-stu-id="c2a71-149">Therefore, it is strongly recommended to provide top-level, language-only translations in your manifest ('en' instead of 'en-us') and only provide region-level overrides for the few strings that need them.</span></span>

### <a name="example-manifestjson-change"></a><span data-ttu-id="c2a71-150">Beispiel manifest.jsbei Änderung</span><span class="sxs-lookup"><span data-stu-id="c2a71-150">Example manifest.json change</span></span>

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

### <a name="example-localization-json-file"></a><span data-ttu-id="c2a71-151">Beispiel für lokalisierungs-Json-Datei</span><span class="sxs-lookup"><span data-stu-id="c2a71-151">Example localization .json file</span></span>

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

## <a name="handling-localized-text-submissions-from-your-users"></a><span data-ttu-id="c2a71-152">Behandeln lokalisierter Textübermittlungen von Benutzern</span><span class="sxs-lookup"><span data-stu-id="c2a71-152">Handling localized text submissions from your users</span></span>

<span data-ttu-id="c2a71-153">Wenn Sie lokalisierte Versionen Ihrer Anwendung bereitstellen, ist es sehr wahrscheinlich, dass Ihre Benutzer mit derselben Sprache antworten.</span><span class="sxs-lookup"><span data-stu-id="c2a71-153">If your provide localized versions of your application it is very likely that your users will respond with the same language.</span></span> <span data-ttu-id="c2a71-154">Teams Die Benutzerübermittlungen werden nicht in die Standardsprache übersetzt, daher muss Ihre App dies behandeln.</span><span class="sxs-lookup"><span data-stu-id="c2a71-154">Teams does not translate the user submissions back to the default language, so your app will need to handle that.</span></span> <span data-ttu-id="c2a71-155">Wenn Sie z. B. einen lokalisierten Bereitstellen, sind die Antworten auf Ihren Bot der lokalisierte Text des Befehls, nicht `commandList` die Standardsprache.</span><span class="sxs-lookup"><span data-stu-id="c2a71-155">For example, if you provide a localized `commandList`, the responses to your bot will be the localized text of the command, not the default language.</span></span> <span data-ttu-id="c2a71-156">Ihre App muss entsprechend reagieren.</span><span class="sxs-lookup"><span data-stu-id="c2a71-156">Your app will need to respond appropriately.</span></span>

## <a name="code-sample"></a><span data-ttu-id="c2a71-157">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="c2a71-157">Code sample</span></span>

| <span data-ttu-id="c2a71-158">Beispielname</span><span class="sxs-lookup"><span data-stu-id="c2a71-158">Sample name</span></span> | <span data-ttu-id="c2a71-159">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="c2a71-159">Description</span></span> | <span data-ttu-id="c2a71-160">.NET</span><span class="sxs-lookup"><span data-stu-id="c2a71-160">.NET</span></span> | <span data-ttu-id="c2a71-161">Node.js</span><span class="sxs-lookup"><span data-stu-id="c2a71-161">Node.js</span></span> |
|-------------|-------------|------|------|
| <span data-ttu-id="c2a71-162">App-Lokalisierung</span><span class="sxs-lookup"><span data-stu-id="c2a71-162">App Localization</span></span> | <span data-ttu-id="c2a71-163">Microsoft Teams-App-Lokalisierung mithilfe von Bot und Registerkarte.</span><span class="sxs-lookup"><span data-stu-id="c2a71-163">Microsoft Teams app localization using bot and tab.</span></span> | [<span data-ttu-id="c2a71-164">View</span><span class="sxs-lookup"><span data-stu-id="c2a71-164">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-localization/csharp) |[<span data-ttu-id="c2a71-165">View</span><span class="sxs-lookup"><span data-stu-id="c2a71-165">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-localization/nodejs) |


