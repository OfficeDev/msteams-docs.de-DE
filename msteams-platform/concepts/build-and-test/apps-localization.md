---
title: Lokalisierung für Ihre App
description: Beschreibt Überlegungen zum Lokalisieren Ihrer Microsoft Teams-App.
ms.topic: conceptual
localization_priority: Normal
keywords: Teams veröffentlichen Store Office Publishing AppSource-Lokalisierungssprache
ms.date: 05/15/2018
ms.openlocfilehash: 6c63bd5c71934d0a3342b31bc10feda38b8ae0d1
ms.sourcegitcommit: d90c5dafea09e2893dea8da46ee49516bbaa04b0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/28/2021
ms.locfileid: "52075745"
---
# <a name="localization-for-microsoft-teams-apps"></a><span data-ttu-id="40745-104">Lokalisierung für Microsoft Teams-Apps</span><span class="sxs-lookup"><span data-stu-id="40745-104">Localization for Microsoft Teams apps</span></span>

<span data-ttu-id="40745-105">Beim Lokalisieren Ihrer Microsoft Teams-App müssen Sie drei wichtige Bereiche berücksichtigen.</span><span class="sxs-lookup"><span data-stu-id="40745-105">When localizing your Microsoft Teams app there are three major areas you need to consider.</span></span>

1. <span data-ttu-id="40745-106">Ihr AppSource-Eintrag (wenn Sie im App Store veröffentlichen).</span><span class="sxs-lookup"><span data-stu-id="40745-106">Your AppSource listing (if you're publishing to the app store).</span></span>
1. <span data-ttu-id="40745-107">Die Zeichenfolgen, die dem Endbenutzer im App-Manifest angezeigt werden (z. B. Botbefehle).</span><span class="sxs-lookup"><span data-stu-id="40745-107">The end-user facing strings in your app manifest (for example bot commands).</span></span>
1. <span data-ttu-id="40745-108">Reagieren auf lokalisierten Text, der von Ihren Benutzern übermittelt wurde.</span><span class="sxs-lookup"><span data-stu-id="40745-108">Responding to localized text submitted from your users.</span></span>

## <a name="localizing-your-appsource-listing"></a><span data-ttu-id="40745-109">Lokalisieren Ihres AppSource-Eintrags</span><span class="sxs-lookup"><span data-stu-id="40745-109">Localizing your AppSource listing</span></span>

<span data-ttu-id="40745-110">Wenn Sie im App Store veröffentlichen, müssen Sie beachten, dass das Lokalisieren Ihres AppSource-Eintrags noch nicht unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="40745-110">If you're publishing to the app store, you need to be aware that localizing your AppSource listing is not yet supported.</span></span> <span data-ttu-id="40745-111">In Vorbereitung auf die Unterstützung lokalisierter Einträge im App Store können Sie ihrem Eintrag jedoch weitere Sprachen hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="40745-111">However, in preparation for support for localized listings in the app store you can add additional languages to your listing.</span></span> <span data-ttu-id="40745-112">Derzeit werden nur die standardmäßigen (englischen) Sprachinformationen, die Sie im [Partner Center](/office/dev/store/submit-to-appsource-via-partner-center) für Ihren Eintrag bereitstellen, im [AppSource-Websiteeintrag](https://appsource.microsoft.com/marketplace/apps?product=office%3Bteams&page=1) für Ihre App angezeigt.</span><span class="sxs-lookup"><span data-stu-id="40745-112">Currently only the default (English) language information you provide in [Partner Center](/office/dev/store/submit-to-appsource-via-partner-center) for your listing will appear in the [AppSource website](https://appsource.microsoft.com/marketplace/apps?product=office%3Bteams&page=1) listing for your app.</span></span>

<span data-ttu-id="40745-113">Um eine zusätzliche Sprache für Ihre App zu konfigurieren, wählen Sie im [Partner Center](/office/dev/store/submit-to-appsource-via-partner-center)sowohl Englisch als auch die zusätzliche Sprache der App aus.</span><span class="sxs-lookup"><span data-stu-id="40745-113">To configure an additional language for your app, in [Partner Center](/office/dev/store/submit-to-appsource-via-partner-center), select both English and the additional language of the app.</span></span> <span data-ttu-id="40745-114">In diesem Beispiel wird Französisch verwendet.</span><span class="sxs-lookup"><span data-stu-id="40745-114">French is used in this example.</span></span>

1. <span data-ttu-id="40745-115">Hinzufügen von Englisch</span><span class="sxs-lookup"><span data-stu-id="40745-115">Add English language</span></span>
    * <span data-ttu-id="40745-116">Geben Sie den Namen der App ein.</span><span class="sxs-lookup"><span data-stu-id="40745-116">Fill in the app name.</span></span>
    * <span data-ttu-id="40745-117">Geben Sie eine kurze Beschreibung der App in Englisch ein.</span><span class="sxs-lookup"><span data-stu-id="40745-117">Fill in a short description of the app in English.</span></span>
    * <span data-ttu-id="40745-118">Füllen Sie die lange Beschreibung der App in Englisch aus.</span><span class="sxs-lookup"><span data-stu-id="40745-118">Fill in the long description of the app in English.</span></span>
    * <span data-ttu-id="40745-119">Fügen Sie in der langen Beschreibung auch die Zeile "Diese App ist in "Französisch" verfügbar.</span><span class="sxs-lookup"><span data-stu-id="40745-119">In the long description, please also add the line “This app is available in “French”.</span></span>
    * <span data-ttu-id="40745-120">Laden Sie die Bilder ihrer App-UI hoch (in Englisch).</span><span class="sxs-lookup"><span data-stu-id="40745-120">Upload the images of your app UI (in English).</span></span>
2. <span data-ttu-id="40745-121">Hinzufügen von Französisch</span><span class="sxs-lookup"><span data-stu-id="40745-121">Add French language</span></span>
    * <span data-ttu-id="40745-122">Geben Sie den Namen der App ein.</span><span class="sxs-lookup"><span data-stu-id="40745-122">Fill in the app name.</span></span>
    * <span data-ttu-id="40745-123">Geben Sie eine kurze Beschreibung der App auf Französisch ein.</span><span class="sxs-lookup"><span data-stu-id="40745-123">Fill in a short description of the app in French.</span></span>
    * <span data-ttu-id="40745-124">Füllen Sie die lange Beschreibung der App auf Französisch aus.</span><span class="sxs-lookup"><span data-stu-id="40745-124">Fill in the long description of the app in French.</span></span>
    * <span data-ttu-id="40745-125">Laden Sie die Bilder ihrer App-UI hoch (auf Französisch).</span><span class="sxs-lookup"><span data-stu-id="40745-125">Upload the images of your app UI (in French).</span></span>

<span data-ttu-id="40745-126">Die Bilder, die Sie mit der englischen Sprache hochladen, werden in AppSource verwendet.</span><span class="sxs-lookup"><span data-stu-id="40745-126">The images you upload with the English language will be the ones used in AppSource.</span></span>

## <a name="localizing-the-strings-in-your-app-manifest"></a><span data-ttu-id="40745-127">Lokalisieren der Zeichenfolgen im App-Manifest</span><span class="sxs-lookup"><span data-stu-id="40745-127">Localizing the strings in your app manifest</span></span>

<span data-ttu-id="40745-128">Sie müssen das Microsoft Teams-App-Schema v1.5+ verwenden, um Ihre App ordnungsgemäß zu lokalisieren.</span><span class="sxs-lookup"><span data-stu-id="40745-128">You must use the Microsoft Teams app schema v1.5+ to properly localize your app.</span></span> <span data-ttu-id="40745-129">Dazu können Sie das Attribut in Ihrer manifest.json-Datei auf ' ' festlegen und die Eigenschaft `$schema` https://developer.microsoft.com/en-us/json-schemas/teams/v1.8/MicrosoftTeams.Localization.schema.json "manifestVersion" auf "1.7" aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="40745-129">You can do this by setting the `$schema` attribute in your manifest.json file to 'https://developer.microsoft.com/en-us/json-schemas/teams/v1.8/MicrosoftTeams.Localization.schema.json' and updating the 'manifestVersion' property to '1.7'.</span></span>

### <a name="example-manifestjson-change"></a><span data-ttu-id="40745-130">Beispiel manifest.jsbei Änderung</span><span class="sxs-lookup"><span data-stu-id="40745-130">Example manifest.json change</span></span>

```json
{
  "$schema": "https://developer.microsoft.com/en-us/json-schemas/teams/v1.8/MicrosoftTeams.Localization.schema.json",
  "manifestVersion": "1.5",
  ...
}
```

<span data-ttu-id="40745-131">Anschließend möchten Sie die Eigenschaft "localizationInfo" mit der Standardsprache hinzufügen, die ihre Anwendung unterstützt.</span><span class="sxs-lookup"><span data-stu-id="40745-131">You will then want to add the 'localizationInfo' property with the default language that your application supports.</span></span> <span data-ttu-id="40745-132">Die Standardsprache wird als endgültige Fallbacksprache verwendet, wenn die Clienteinstellungen des Benutzers keinem Ihrer zusätzlichen Sprachen entsprechen.</span><span class="sxs-lookup"><span data-stu-id="40745-132">The default language is used as the final fallback language if the user's client settings do not match any of your additional languages.</span></span>

### <a name="example-manifestjson-change"></a><span data-ttu-id="40745-133">Beispiel manifest.jsbei Änderung</span><span class="sxs-lookup"><span data-stu-id="40745-133">Example manifest.json change</span></span>

```json
{
  ...
  "localizationInfo": {
    "defaultLanguageTag": "en"
  }
  ...
}
```

<span data-ttu-id="40745-134">Sie können zusätzliche .json-Dateien mit Übersetzungen aller zeichenfolgen angezeigten Benutzer in Ihrem Manifest bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="40745-134">You can provide additional .json files with translations of all the user facing strings in your manifest.</span></span> <span data-ttu-id="40745-135">Diese Dateien müssen dem [JSON-Schema](../../resources/schema/localization-schema.md) der Lokalisierungsdatei entsprechen und der Eigenschaft "localizationInfo" Ihres Manifests hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="40745-135">These files must adhere to the [Localization file JSON schema](../../resources/schema/localization-schema.md) and they must be added to the 'localizationInfo' property of your manifest.</span></span> <span data-ttu-id="40745-136">Jede Datei korreliert mit einem Sprachtag, das der Teams-Client zum Auswählen der entsprechenden Zeichenfolgen verwendet.</span><span class="sxs-lookup"><span data-stu-id="40745-136">Each file correlates to a language tag which the Teams client uses to choose the appropriate strings.</span></span> <span data-ttu-id="40745-137">Das Sprachtag hat die Form, es wird jedoch empfohlen, den Teil weglassen, um alle Regionen zu verwenden, die <language> - <region> die gewünschte <region> Sprache unterstützen.</span><span class="sxs-lookup"><span data-stu-id="40745-137">The language tag takes the form of <language>-<region> but it is recommended to omit the <region> portion to target all regions that support the desired language.</span></span>

<span data-ttu-id="40745-138">Der Teams-Client verwendet die Zeichenfolgen in dieser Reihenfolge: Standardsprachenzeichenfolgen -> Sprache des Benutzers nur Zeichenfolgen -> Sprache des Benutzers + Regionenzeichenfolgen des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="40745-138">The Teams client will apply the strings in this order: default language strings -> user's language only strings -> user's language + user's region strings.</span></span>

<span data-ttu-id="40745-139">Sie stellen z. B. die Standardsprache "fr" (Französisch, alle Regionen) und zusätzliche Sprachdateien für "en" (Englisch, alle Regionen) und "en-gb" (Englisch, Großbritannien) zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="40745-139">For example, you provide a default language of 'fr' (French, all regions), and additional language files for 'en' (English, all regions) and 'en-gb' (English, Great Britain).</span></span> <span data-ttu-id="40745-140">Wenn die Sprache des Benutzers auf "en-gb" festgelegt ist:</span><span class="sxs-lookup"><span data-stu-id="40745-140">If the user's language is set to 'en-gb':</span></span>

1. <span data-ttu-id="40745-141">Der Teams-Client überschreibt die Zeichenfolgen "fr" mit den Zeichenfolgen "en".</span><span class="sxs-lookup"><span data-stu-id="40745-141">The Teams client will take the 'fr' strings overwrite them with the 'en' strings.</span></span>
2. <span data-ttu-id="40745-142">Überschreiben Sie diese mit den Zeichenfolgen "en-gb".</span><span class="sxs-lookup"><span data-stu-id="40745-142">Overwrite those with the 'en-gb' strings.</span></span>

<span data-ttu-id="40745-143">Wenn die Sprache des Benutzers auf "en-ca" festgelegt ist:</span><span class="sxs-lookup"><span data-stu-id="40745-143">If the user's language is set to 'en-ca':</span></span> 

1. <span data-ttu-id="40745-144">Der Teams-Client überschreibt die Zeichenfolgen "fr" mit den Zeichenfolgen "en".</span><span class="sxs-lookup"><span data-stu-id="40745-144">The Teams client will take the 'fr' strings overwrite them with the 'en' strings.</span></span>
2. <span data-ttu-id="40745-145">Da keine "en-ca"-Lokalisierung bereitgestellt wird, werden die "en"-Lokalisierungen verwendet.</span><span class="sxs-lookup"><span data-stu-id="40745-145">Since no 'en-ca' localization is supplied, the 'en' localizations will be used.</span></span>

<span data-ttu-id="40745-146">Wenn die Sprache des Benutzers auf "es-es" festgelegt ist, überschreibt der Teams-Client die "fr"-Zeichenfolgen und überschreibt sie nicht mit einer der Sprachdateien.</span><span class="sxs-lookup"><span data-stu-id="40745-146">If the user's language is set to 'es-es', the Teams client will take the 'fr' strings and will not override them with any of the language files.</span></span>

<span data-ttu-id="40745-147">Daher wird dringend empfohlen, nur Übersetzungen auf oberster Ebene in Ihrem Manifest ('en' statt 'en-us') zur Verfügung zu stellen und nur Überschreibungen auf Regionsebene für die wenigen Zeichenfolgen zur Verfügung zu stellen, die sie benötigen.</span><span class="sxs-lookup"><span data-stu-id="40745-147">Therefore, it is strongly recommended to provide top-level, language-only translations in your manifest ('en' instead of 'en-us') and only provide region-level overrides for the few strings that need them.</span></span>

### <a name="example-manifestjson-change"></a><span data-ttu-id="40745-148">Beispiel manifest.jsbei Änderung</span><span class="sxs-lookup"><span data-stu-id="40745-148">Example manifest.json change</span></span>

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

### <a name="example-localization-json-file"></a><span data-ttu-id="40745-149">Beispiel für lokalisierungs-Json-Datei</span><span class="sxs-lookup"><span data-stu-id="40745-149">Example localization .json file</span></span>

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

## <a name="handling-localized-text-submissions-from-your-users"></a><span data-ttu-id="40745-150">Behandeln lokalisierter Textübermittlungen von Benutzern</span><span class="sxs-lookup"><span data-stu-id="40745-150">Handling localized text submissions from your users</span></span>

<span data-ttu-id="40745-151">Wenn Sie lokalisierte Versionen Ihrer Anwendung bereitstellen, ist es sehr wahrscheinlich, dass Ihre Benutzer mit derselben Sprache antworten.</span><span class="sxs-lookup"><span data-stu-id="40745-151">If your provide localized versions of your application it is very likely that your users will respond with the same language.</span></span> <span data-ttu-id="40745-152">Teams übersetzt die Benutzerübermittlungen nicht zurück in die Standardsprache, daher muss Ihre App dies behandeln.</span><span class="sxs-lookup"><span data-stu-id="40745-152">Teams does not translate the user submissions back to the default language, so your app will need to handle that.</span></span> <span data-ttu-id="40745-153">Wenn Sie z. B. einen lokalisierten Bereitstellen, sind die Antworten auf Ihren Bot der lokalisierte Text des Befehls, nicht `commandList` die Standardsprache.</span><span class="sxs-lookup"><span data-stu-id="40745-153">For example, if you provide a localized `commandList`, the responses to your bot will be the localized text of the command, not the default language.</span></span> <span data-ttu-id="40745-154">Ihre App muss entsprechend reagieren.</span><span class="sxs-lookup"><span data-stu-id="40745-154">Your app will need to respond appropriately.</span></span>

## <a name="code-sample"></a><span data-ttu-id="40745-155">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="40745-155">Code sample</span></span>

| <span data-ttu-id="40745-156">Beispielname</span><span class="sxs-lookup"><span data-stu-id="40745-156">Sample name</span></span> | <span data-ttu-id="40745-157">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="40745-157">Description</span></span> | <span data-ttu-id="40745-158">.NET</span><span class="sxs-lookup"><span data-stu-id="40745-158">.NET</span></span> |
|-------------|-------------|------|
| <span data-ttu-id="40745-159">App-Lokalisierung</span><span class="sxs-lookup"><span data-stu-id="40745-159">App Localization</span></span> | <span data-ttu-id="40745-160">Microsoft Teams-App-Lokalisierung mithilfe von Bot und Registerkarte.</span><span class="sxs-lookup"><span data-stu-id="40745-160">Microsoft Teams app localization using bot and tab.</span></span> | [<span data-ttu-id="40745-161">View</span><span class="sxs-lookup"><span data-stu-id="40745-161">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-localization/csharp) |


