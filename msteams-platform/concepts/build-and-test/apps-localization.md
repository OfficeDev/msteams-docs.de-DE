---
title: Lokalisierung für Ihre App
description: Beschreibt Überlegungen zum Lokalisieren Ihrer Microsoft Teams-App.
ms.topic: conceptual
keywords: Teams veröffentlichen Office-Veröffentlichungs-AppSource-Lokalisierungssprache
ms.date: 05/15/2018
ms.openlocfilehash: 69bee0ee11238dc0e461e4fddf8ed01f0cfcccde
ms.sourcegitcommit: 976e870cc925f61b76c3830ec04ba6e4bdfde32f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/27/2021
ms.locfileid: "50014299"
---
# <a name="localization-for-microsoft-teams-apps"></a><span data-ttu-id="cc33a-104">Lokalisierung für Microsoft Teams-Apps</span><span class="sxs-lookup"><span data-stu-id="cc33a-104">Localization for Microsoft Teams apps</span></span>

<span data-ttu-id="cc33a-105">Beim Lokalisieren Ihrer Microsoft Teams-App müssen Sie drei wichtige Bereiche berücksichtigen.</span><span class="sxs-lookup"><span data-stu-id="cc33a-105">When localizing your Microsoft Teams app there are three major areas you need to consider.</span></span>

1. <span data-ttu-id="cc33a-106">Ihr AppSource-Eintrag (wenn Sie im App Store veröffentlichen).</span><span class="sxs-lookup"><span data-stu-id="cc33a-106">Your AppSource listing (if you're publishing to the app store).</span></span>
1. <span data-ttu-id="cc33a-107">Die zeichenfolgen, die dem Endbenutzer in Ihrem App-Manifest angezeigt werden (z. B. Botbefehle).</span><span class="sxs-lookup"><span data-stu-id="cc33a-107">The end-user facing strings in your app manifest (for example bot commands).</span></span>
1. <span data-ttu-id="cc33a-108">Reagieren auf lokalisierten Text, der von Ihren Benutzern übermittelt wurde.</span><span class="sxs-lookup"><span data-stu-id="cc33a-108">Responding to localized text submitted from your users.</span></span>

## <a name="localizing-your-appsource-listing"></a><span data-ttu-id="cc33a-109">Lokalisieren ihres AppSource-Eintrags</span><span class="sxs-lookup"><span data-stu-id="cc33a-109">Localizing your AppSource listing</span></span>

<span data-ttu-id="cc33a-110">Wenn Sie im App Store veröffentlichen, müssen Sie beachten, dass die Lokalisierung Ihres AppSource-Eintrags noch nicht unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="cc33a-110">If you're publishing to the app store, you need to be aware that localizing your AppSource listing is not yet supported.</span></span> <span data-ttu-id="cc33a-111">Zur Vorbereitung auf die Unterstützung lokalisierter Einträge im App Store können Sie ihrem Eintrag jedoch zusätzliche Sprachen hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="cc33a-111">However, in preparation for support for localized listings in the app store you can add additional languages to your listing.</span></span> <span data-ttu-id="cc33a-112">Derzeit werden nur die standardmäßigen (englischen) Sprachinformationen, die Sie im [Partner Center](/office/dev/store/submit-to-appsource-via-partner-center) für Ihren Eintrag bereitstellen, im Eintrag der [AppSource-Website](https://appsource.microsoft.com/marketplace/apps?product=office%3Bteams&page=1) für Ihre App angezeigt.</span><span class="sxs-lookup"><span data-stu-id="cc33a-112">Currently only the default (English) language information you provide in [Partner Center](/office/dev/store/submit-to-appsource-via-partner-center) for your listing will appear in the [AppSource website](https://appsource.microsoft.com/marketplace/apps?product=office%3Bteams&page=1) listing for your app.</span></span>

<span data-ttu-id="cc33a-113">Um eine zusätzliche Sprache für Ihre App zu konfigurieren, wählen Sie im [Partner Center](/office/dev/store/submit-to-appsource-via-partner-center)sowohl Englisch als auch die zusätzliche Sprache der App aus.</span><span class="sxs-lookup"><span data-stu-id="cc33a-113">To configure an additional language for your app, in [Partner Center](/office/dev/store/submit-to-appsource-via-partner-center), select both English and the additional language of the app.</span></span> <span data-ttu-id="cc33a-114">In diesem Beispiel wird Französisch verwendet.</span><span class="sxs-lookup"><span data-stu-id="cc33a-114">French is used in this example.</span></span>

1. <span data-ttu-id="cc33a-115">Hinzufügen von Englisch</span><span class="sxs-lookup"><span data-stu-id="cc33a-115">Add English language</span></span>
    * <span data-ttu-id="cc33a-116">Geben Sie den Namen der App ein.</span><span class="sxs-lookup"><span data-stu-id="cc33a-116">Fill in the app name.</span></span>
    * <span data-ttu-id="cc33a-117">Geben Sie eine kurze Beschreibung der App in Englisch ein.</span><span class="sxs-lookup"><span data-stu-id="cc33a-117">Fill in a short description of the app in English.</span></span>
    * <span data-ttu-id="cc33a-118">Füllen Sie die lange Beschreibung der App in Englisch aus.</span><span class="sxs-lookup"><span data-stu-id="cc33a-118">Fill in the long description of the app in English.</span></span>
    * <span data-ttu-id="cc33a-119">Fügen Sie in der langen Beschreibung auch die Zeile "Diese App ist in Französisch verfügbar" hinzu.</span><span class="sxs-lookup"><span data-stu-id="cc33a-119">In the long description, please also add the line “This app is available in “French”.</span></span>
    * <span data-ttu-id="cc33a-120">Laden Sie die Bilder ihrer App-UI hoch (in Englisch).</span><span class="sxs-lookup"><span data-stu-id="cc33a-120">Upload the images of your app UI (in English).</span></span>
2. <span data-ttu-id="cc33a-121">Hinzufügen von Französisch</span><span class="sxs-lookup"><span data-stu-id="cc33a-121">Add French language</span></span>
    * <span data-ttu-id="cc33a-122">Geben Sie den Namen der App ein.</span><span class="sxs-lookup"><span data-stu-id="cc33a-122">Fill in the app name.</span></span>
    * <span data-ttu-id="cc33a-123">Geben Sie eine kurze Beschreibung der App auf Französisch ein.</span><span class="sxs-lookup"><span data-stu-id="cc33a-123">Fill in a short description of the app in French.</span></span>
    * <span data-ttu-id="cc33a-124">Füllen Sie die lange Beschreibung der App in Französisch aus.</span><span class="sxs-lookup"><span data-stu-id="cc33a-124">Fill in the long description of the app in French.</span></span>
    * <span data-ttu-id="cc33a-125">Laden Sie die Bilder ihrer App-UI hoch (in Französisch).</span><span class="sxs-lookup"><span data-stu-id="cc33a-125">Upload the images of your app UI (in French).</span></span>

<span data-ttu-id="cc33a-126">Die Bilder, die Sie mit der englischen Sprache hochladen, werden in AppSource verwendet.</span><span class="sxs-lookup"><span data-stu-id="cc33a-126">The images you upload with the English language will be the ones used in AppSource.</span></span>

## <a name="localizing-the-strings-in-your-app-manifest"></a><span data-ttu-id="cc33a-127">Lokalisieren der Zeichenfolgen in Ihrem App-Manifest</span><span class="sxs-lookup"><span data-stu-id="cc33a-127">Localizing the strings in your app manifest</span></span>

<span data-ttu-id="cc33a-128">Sie müssen das Microsoft Teams-App-Schema v1.5+ verwenden, um Ihre App ordnungsgemäß zu lokalisieren.</span><span class="sxs-lookup"><span data-stu-id="cc33a-128">You must use the Microsoft Teams app schema v1.5+ to properly localize your app.</span></span> <span data-ttu-id="cc33a-129">Dazu können Sie das Attribut in Ihrem manifest.json-Datei auf ' ' festlegen und die Eigenschaft `$schema` https://developer.microsoft.com/en-us/json-schemas/teams/v1.8/MicrosoftTeams.Localization.schema.json "manifestVersion" auf "1.7" aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="cc33a-129">You can do this by setting the `$schema` attribute in your manifest.json file to 'https://developer.microsoft.com/en-us/json-schemas/teams/v1.8/MicrosoftTeams.Localization.schema.json' and updating the 'manifestVersion' property to '1.7'.</span></span>

### <a name="example-manifestjson-change"></a><span data-ttu-id="cc33a-130">Beispiel manifest.jsbei Änderung</span><span class="sxs-lookup"><span data-stu-id="cc33a-130">Example manifest.json change</span></span>

```json
{
  "$schema": "https://developer.microsoft.com/en-us/json-schemas/teams/v1.8/MicrosoftTeams.Localization.schema.json",
  "manifestVersion": "1.5",
  ...
}
```

<span data-ttu-id="cc33a-131">Anschließend möchten Sie die Eigenschaft "localizationInfo" mit der Standardsprache hinzufügen, die ihre Anwendung unterstützt.</span><span class="sxs-lookup"><span data-stu-id="cc33a-131">You will then want to add the 'localizationInfo' property with the default language that your application supports.</span></span> <span data-ttu-id="cc33a-132">Die Standardsprache wird als endgültige Fallbacksprache verwendet, wenn die Clienteinstellungen des Benutzers nicht mit einer Ihrer zusätzlichen Sprachen übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="cc33a-132">The default language is used as the final fallback language if the user's client settings do not match any of your additional languages.</span></span>

### <a name="example-manifestjson-change"></a><span data-ttu-id="cc33a-133">Beispiel manifest.jsbei Änderung</span><span class="sxs-lookup"><span data-stu-id="cc33a-133">Example manifest.json change</span></span>

```json
{
  ...
  "localizationInfo": {
    "defaultLanguageTag": "en"
  }
  ...
}
```

<span data-ttu-id="cc33a-134">Sie können zusätzliche .json-Dateien mit Übersetzungen aller vom Benutzer angezeigten Zeichenfolgen in Ihrem Manifest bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="cc33a-134">You can provide additional .json files with translations of all the user facing strings in your manifest.</span></span> <span data-ttu-id="cc33a-135">Diese Dateien müssen [](../../resources/schema/localization-schema.md) dem Lokalisierungsdatei-JSON-Schema entsprechen und der Eigenschaft "localizationInfo" Ihres Manifests hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="cc33a-135">These files must adhere to the [Localization file JSON schema](../../resources/schema/localization-schema.md) and they must be added to the 'localizationInfo' property of your manifest.</span></span> <span data-ttu-id="cc33a-136">Jede Datei korreliert mit einem Sprachtag, das der Teams-Client verwendet, um die entsprechenden Zeichenfolgen zu wählen.</span><span class="sxs-lookup"><span data-stu-id="cc33a-136">Each file correlates to a language tag which the Teams client uses to choose the appropriate strings.</span></span> <span data-ttu-id="cc33a-137">Das Sprachtag hat die Form, es wird jedoch empfohlen, den Teil weglassen, um alle Regionen anzielen, die <language> - <region> die gewünschte <region> Sprache unterstützen.</span><span class="sxs-lookup"><span data-stu-id="cc33a-137">The language tag takes the form of <language>-<region> but it is recommended to omit the <region> portion to target all regions that support the desired language.</span></span>

<span data-ttu-id="cc33a-138">Der Teams-Client wird die Zeichenfolgen in der reihenfolge anwenden: Standardsprachzeichenfolgen -> Sprache des Benutzers nur Zeichenfolgen -> Sprache des Benutzers + Regionenzeichenfolgen des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="cc33a-138">The Teams client will apply the strings in this order: default language strings -> user's language only strings -> user's language + user's region strings.</span></span>

<span data-ttu-id="cc33a-139">Sie stellen beispielsweise die Standardsprache "fr" (Französisch, alle Regionen) und zusätzliche Sprachdateien für "en" (Englisch, alle Regionen) und "en-gb" (Englisch, Großbritannien) zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="cc33a-139">For example, you provide a default language of 'fr' (French, all regions), and additional language files for 'en' (English, all regions) and 'en-gb' (English, Great Britain).</span></span> <span data-ttu-id="cc33a-140">Wenn die Sprache des Benutzers auf "en-gb" festgelegt ist:</span><span class="sxs-lookup"><span data-stu-id="cc33a-140">If the user's language is set to 'en-gb':</span></span>

1. <span data-ttu-id="cc33a-141">Der Teams-Client überschreibt die "fr"-Zeichenfolgen mit den "en"-Zeichenfolgen.</span><span class="sxs-lookup"><span data-stu-id="cc33a-141">The Teams client will take the 'fr' strings overwrite them with the 'en' strings.</span></span>
2. <span data-ttu-id="cc33a-142">Überschreiben Sie diese Zeichenfolgen mit den Zeichenfolgen "en-gb".</span><span class="sxs-lookup"><span data-stu-id="cc33a-142">Overwrite those with the 'en-gb' strings.</span></span>

<span data-ttu-id="cc33a-143">Wenn die Sprache des Benutzers auf "en-ca" festgelegt ist:</span><span class="sxs-lookup"><span data-stu-id="cc33a-143">If the user's language is set to 'en-ca':</span></span> 

1. <span data-ttu-id="cc33a-144">Der Teams-Client überschreibt die "fr"-Zeichenfolgen mit den "en"-Zeichenfolgen.</span><span class="sxs-lookup"><span data-stu-id="cc33a-144">The Teams client will take the 'fr' strings overwrite them with the 'en' strings.</span></span>
2. <span data-ttu-id="cc33a-145">Da keine Lokalisierung von "en-ca" bereitgestellt wird, werden die "en"-Lokalisierungen verwendet.</span><span class="sxs-lookup"><span data-stu-id="cc33a-145">Since no 'en-ca' localization is supplied, the 'en' localizations will be used.</span></span>

<span data-ttu-id="cc33a-146">Wenn die Sprache des Benutzers auf "es-es" festgelegt ist, verwendet der Teams-Client die "fr"-Zeichenfolgen und überschreibt sie nicht mit einer der Sprachdateien.</span><span class="sxs-lookup"><span data-stu-id="cc33a-146">If the user's language is set to 'es-es', the Teams client will take the 'fr' strings and will not override them with any of the language files.</span></span>

<span data-ttu-id="cc33a-147">Aus diesem Grund wird dringend empfohlen, Nur-Sprach-Übersetzungen auf oberster Ebene in Ihrem Manifest ('en' anstelle von 'en-us') und nur Außerkraftsetzungen auf Regionsebene für die wenigen Zeichenfolgen zu bieten, die sie benötigen.</span><span class="sxs-lookup"><span data-stu-id="cc33a-147">Therefore, it is strongly recommended to provide top-level, language-only translations in your manifest ('en' instead of 'en-us') and only provide region-level overrides for the few strings that need them.</span></span>

### <a name="example-manifestjson-change"></a><span data-ttu-id="cc33a-148">Beispiel manifest.jsbei Änderung</span><span class="sxs-lookup"><span data-stu-id="cc33a-148">Example manifest.json change</span></span>

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

### <a name="example-localization-json-file"></a><span data-ttu-id="cc33a-149">Beispiel für lokalisierungs-JSON-Datei</span><span class="sxs-lookup"><span data-stu-id="cc33a-149">Example localization .json file</span></span>

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

## <a name="handling-localized-text-submissions-from-your-users"></a><span data-ttu-id="cc33a-150">Behandeln lokalisierter Textübermittlungen von Benutzern</span><span class="sxs-lookup"><span data-stu-id="cc33a-150">Handling localized text submissions from your users</span></span>

<span data-ttu-id="cc33a-151">Wenn Sie lokalisierte Versionen Ihrer Anwendung bereitstellen, ist es sehr wahrscheinlich, dass die Benutzer mit derselben Sprache antworten.</span><span class="sxs-lookup"><span data-stu-id="cc33a-151">If your provide localized versions of your application it is very likely that your users will respond with the same language.</span></span> <span data-ttu-id="cc33a-152">Teams übersetzt die Benutzerübermittlungen nicht zurück in die Standardsprache, daher muss Ihre App dies behandeln.</span><span class="sxs-lookup"><span data-stu-id="cc33a-152">Teams does not translate the user submissions back to the default language, so your app will need to handle that.</span></span> <span data-ttu-id="cc33a-153">Wenn Sie beispielsweise eine lokalisierte Antwort bereitstellen, sind die Antworten auf Ihren Bot der lokalisierte Text des Befehls, nicht `commandList` die Standardsprache.</span><span class="sxs-lookup"><span data-stu-id="cc33a-153">For example, if you provide a localized `commandList`, the responses to your bot will be the localized text of the command, not the default language.</span></span> <span data-ttu-id="cc33a-154">Ihre App muss entsprechend reagieren.</span><span class="sxs-lookup"><span data-stu-id="cc33a-154">Your app will need to respond appropriately.</span></span>
