---
title: Lokalisierung für Ihre App
description: Beschreibt Überlegungen zum Lokalisieren Ihrer Microsoft Teams-App.
ms.topic: conceptual
localization_priority: Normal
keywords: Teams veröffentlichen Store Office Publishing AppSource-Lokalisierungssprache
ms.date: 05/15/2018
ms.openlocfilehash: a55b8af97e5306843858e5844a017dd402ab3516
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566047"
---
# <a name="localization-for-microsoft-teams-apps"></a><span data-ttu-id="9a519-104">Lokalisierung für Microsoft Teams Apps</span><span class="sxs-lookup"><span data-stu-id="9a519-104">Localization for Microsoft Teams apps</span></span>

<span data-ttu-id="9a519-105">Beim Lokalisieren Ihrer Microsoft Teams-App müssen Sie Folgendes berücksichtigen:</span><span class="sxs-lookup"><span data-stu-id="9a519-105">When localizing your Microsoft Teams app, you must consider the following:</span></span>

1. <span data-ttu-id="9a519-106">Ihr Teams-Shop-Eintrag (falls zutreffend).</span><span class="sxs-lookup"><span data-stu-id="9a519-106">Your Teams store listing (if applicable).</span></span>
1. <span data-ttu-id="9a519-107">Die Endbenutzerzeichenfolgen in Ihrem App-Manifest.</span><span class="sxs-lookup"><span data-stu-id="9a519-107">The end-user facing strings in your app manifest.</span></span> <span data-ttu-id="9a519-108">Zum Beispiel Bot-Befehle.</span><span class="sxs-lookup"><span data-stu-id="9a519-108">For example bot commands.</span></span>
1. <span data-ttu-id="9a519-109">Reagieren auf lokalisierten Text, der von Ihren Benutzern gesendet wurde.</span><span class="sxs-lookup"><span data-stu-id="9a519-109">Responding to localized text submitted from your users.</span></span>

## <a name="localizing-your-appsource-listing"></a><span data-ttu-id="9a519-110">Lokalisieren Ihres AppSource-Eintrags</span><span class="sxs-lookup"><span data-stu-id="9a519-110">Localizing your AppSource listing</span></span>

<span data-ttu-id="9a519-111">Wenn Sie im Store veröffentlichen, müssen Sie sich bewusst sein, dass die Lokalisierung Ihres AppSource-Eintrags noch nicht unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="9a519-111">If you're publishing to the store, you need to be aware that localizing your AppSource listing is not yet supported.</span></span> <span data-ttu-id="9a519-112">In Vorbereitung auf die Unterstützung für lokalisierte Angebote im App Store können Sie Ihrem Eintrag jedoch weitere Sprachen hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="9a519-112">However, in preparation for support for localized listings in the app store you can add additional languages to your listing.</span></span> <span data-ttu-id="9a519-113">Derzeit werden nur die Standard-Sprachinformationen (Englisch), die Sie im [Partner Center](/office/dev/store/submit-to-appsource-via-partner-center) für Ihren Eintrag bereitstellen, im [AppSource-Websiteeintrag](https://appsource.microsoft.com/marketplace/apps?product=office%3Bteams&page=1) für Ihre App angezeigt.</span><span class="sxs-lookup"><span data-stu-id="9a519-113">Currently only the default (English) language information you provide in [Partner Center](/office/dev/store/submit-to-appsource-via-partner-center) for your listing will appear in the [AppSource website](https://appsource.microsoft.com/marketplace/apps?product=office%3Bteams&page=1) listing for your app.</span></span>

### <a name="example-of-configuring-localization"></a><span data-ttu-id="9a519-114">Beispiel für die Konfiguration der Lokalisierung</span><span class="sxs-lookup"><span data-stu-id="9a519-114">Example of configuring localization</span></span>

<span data-ttu-id="9a519-115">Um eine zusätzliche Sprache für Ihre App zu konfigurieren, wählen Sie im [Partner Center](/office/dev/store/submit-to-appsource-via-partner-center)sowohl Englisch als auch die zusätzliche Sprache der App aus.</span><span class="sxs-lookup"><span data-stu-id="9a519-115">To configure an additional language for your app, in [Partner Center](/office/dev/store/submit-to-appsource-via-partner-center), select both English and the additional language of the app.</span></span> <span data-ttu-id="9a519-116">In diesem Beispiel wird Französisch verwendet:</span><span class="sxs-lookup"><span data-stu-id="9a519-116">French is used in this example:</span></span>

1. <span data-ttu-id="9a519-117">Englische Sprache hinzufügen</span><span class="sxs-lookup"><span data-stu-id="9a519-117">Add English language</span></span>
    * <span data-ttu-id="9a519-118">Geben Sie den App-Namen ein.</span><span class="sxs-lookup"><span data-stu-id="9a519-118">Fill in the app name.</span></span>
    * <span data-ttu-id="9a519-119">Füllen Sie eine kurze Beschreibung der App in englischer Sprache aus.</span><span class="sxs-lookup"><span data-stu-id="9a519-119">Fill in a short description of the app in English.</span></span>
    * <span data-ttu-id="9a519-120">Füllen Sie die lange Beschreibung der App in englischer Sprache aus.</span><span class="sxs-lookup"><span data-stu-id="9a519-120">Fill in the long description of the app in English.</span></span>
    * <span data-ttu-id="9a519-121">In der langen Beschreibung fügen Sie bitte auch die Zeile "Diese App ist in "Französisch" verfügbar.</span><span class="sxs-lookup"><span data-stu-id="9a519-121">In the long description, please also add the line “This app is available in “French”.</span></span>
    * <span data-ttu-id="9a519-122">Hochladen die Bilder Ihrer App-Benutzeroberfläche (in englischer Sprache).</span><span class="sxs-lookup"><span data-stu-id="9a519-122">Upload the images of your app UI (in English).</span></span>
2. <span data-ttu-id="9a519-123">Französisch hinzufügen</span><span class="sxs-lookup"><span data-stu-id="9a519-123">Add French language</span></span>
    * <span data-ttu-id="9a519-124">Geben Sie den App-Namen ein.</span><span class="sxs-lookup"><span data-stu-id="9a519-124">Fill in the app name.</span></span>
    * <span data-ttu-id="9a519-125">Füllen Sie eine kurze Beschreibung der App auf Französisch aus.</span><span class="sxs-lookup"><span data-stu-id="9a519-125">Fill in a short description of the app in French.</span></span>
    * <span data-ttu-id="9a519-126">Füllen Sie die lange Beschreibung der App auf Französisch aus.</span><span class="sxs-lookup"><span data-stu-id="9a519-126">Fill in the long description of the app in French.</span></span>
    * <span data-ttu-id="9a519-127">Hochladen die Bilder Ihrer App-Benutzeroberfläche (auf Französisch).</span><span class="sxs-lookup"><span data-stu-id="9a519-127">Upload the images of your app UI (in French).</span></span>

<span data-ttu-id="9a519-128">Die Bilder, die Sie mit der englischen Sprache hochladen, werden in AppSource verwendet.</span><span class="sxs-lookup"><span data-stu-id="9a519-128">The images you upload with the English language will be the ones used in AppSource.</span></span>

## <a name="localizing-the-strings-in-your-app-manifest"></a><span data-ttu-id="9a519-129">Lokalisieren der Zeichenfolgen in Ihrem App-Manifest</span><span class="sxs-lookup"><span data-stu-id="9a519-129">Localizing the strings in your app manifest</span></span>

<span data-ttu-id="9a519-130">Sie müssen das Microsoft Teams App-Schema v1.5+ verwenden, um Ihre App ordnungsgemäß zu lokalisieren.</span><span class="sxs-lookup"><span data-stu-id="9a519-130">You must use the Microsoft Teams app schema v1.5+ to properly localize your app.</span></span> <span data-ttu-id="9a519-131">Sie können dies tun, indem Sie das `$schema` Attribut in Ihrem manifest.jsin der Datei auf ' ' setzen und die https://developer.microsoft.com/en-us/json-schemas/teams/v1.8/MicrosoftTeams.Localization.schema.json 'manifestVersion'-Eigenschaft auf '1.7' aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="9a519-131">You can do this by setting the `$schema` attribute in your manifest.json file to 'https://developer.microsoft.com/en-us/json-schemas/teams/v1.8/MicrosoftTeams.Localization.schema.json' and updating the 'manifestVersion' property to '1.7'.</span></span>

### <a name="example-manifestjson-change"></a><span data-ttu-id="9a519-132">Beispiel manifest.jszur Änderung</span><span class="sxs-lookup"><span data-stu-id="9a519-132">Example manifest.json change</span></span>

```json
{
  "$schema": "https://developer.microsoft.com/en-us/json-schemas/teams/v1.8/MicrosoftTeams.Localization.schema.json",
  "manifestVersion": "1.5",
  ...
}
```

<span data-ttu-id="9a519-133">Sie sollten dann die Eigenschaft 'localizationInfo' mit der Standardsprache hinzufügen, die Ihre Anwendung unterstützt.</span><span class="sxs-lookup"><span data-stu-id="9a519-133">You will then want to add the 'localizationInfo' property with the default language that your application supports.</span></span> <span data-ttu-id="9a519-134">Die Standardsprache wird als letzte Fallbacksprache verwendet, wenn die Clienteinstellungen des Benutzers nicht mit einer Ihrer zusätzlichen Sprachen übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="9a519-134">The default language is used as the final fallback language if the user's client settings do not match any of your additional languages.</span></span>

### <a name="example-manifestjson-change"></a><span data-ttu-id="9a519-135">Beispiel manifest.jszur Änderung</span><span class="sxs-lookup"><span data-stu-id="9a519-135">Example manifest.json change</span></span>

```json
{
  ...
  "localizationInfo": {
    "defaultLanguageTag": "en"
  }
  ...
}
```

<span data-ttu-id="9a519-136">Sie können zusätzliche JSon-Dateien mit Übersetzungen aller Benutzerzeichenfolgen in Ihrem Manifest bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="9a519-136">You can provide additional .json files with translations of all the user facing strings in your manifest.</span></span> <span data-ttu-id="9a519-137">Diese Dateien müssen dem [JSON-Schema der Lokalisierungsdatei](../../resources/schema/localization-schema.md) entsprechen und der "localizationInfo"-Eigenschaft Ihres Manifests hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="9a519-137">These files must adhere to the [Localization file JSON schema](../../resources/schema/localization-schema.md) and they must be added to the 'localizationInfo' property of your manifest.</span></span> <span data-ttu-id="9a519-138">Jede Datei korreliert mit einem Sprachtag, das der Teams-Client verwendet, um die entsprechenden Zeichenfolgen auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="9a519-138">Each file correlates to a language tag which the Teams client uses to choose the appropriate strings.</span></span> <span data-ttu-id="9a519-139">Das Sprach-Tag hat die Form <language> - <region> von, aber es wird empfohlen, den <region> Teil wegzulassen, um alle Regionen anzusprechen, die die gewünschte Sprache unterstützen.</span><span class="sxs-lookup"><span data-stu-id="9a519-139">The language tag takes the form of <language>-<region> but it is recommended to omit the <region> portion to target all regions that support the desired language.</span></span>

<span data-ttu-id="9a519-140">Der Teams-Client wendet die Zeichenfolgen in dieser Reihenfolge an: Standard-Sprachzeichenfolgen -> Sprache des Benutzers nur Zeichenfolgen -> Sprache + Die Regionszeichenfolgen des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="9a519-140">The Teams client will apply the strings in this order: default language strings -> user's language only strings -> user's language + user's region strings.</span></span>

<span data-ttu-id="9a519-141">Sie geben z. B. eine Standardsprache von 'fr' (Französisch, alle Regionen) und zusätzliche Sprachdateien für 'en' (Englisch, alle Regionen) und 'en-gb' (Englisch, Großbritannien) an.</span><span class="sxs-lookup"><span data-stu-id="9a519-141">For example, you provide a default language of 'fr' (French, all regions), and additional language files for 'en' (English, all regions) and 'en-gb' (English, Great Britain).</span></span> <span data-ttu-id="9a519-142">Wenn die Sprache des Benutzers auf 'en-gb' gesetzt ist:</span><span class="sxs-lookup"><span data-stu-id="9a519-142">If the user's language is set to 'en-gb':</span></span>

1. <span data-ttu-id="9a519-143">Der Teams-Client übernimmt die 'fr'-Zeichenfolgen, die sie mit den 'en'-Zeichenfolgen überschreiben.</span><span class="sxs-lookup"><span data-stu-id="9a519-143">The Teams client will take the 'fr' strings overwrite them with the 'en' strings.</span></span>
2. <span data-ttu-id="9a519-144">Überschreiben Sie diejenigen mit den Zeichenfolgen 'en-gb'.</span><span class="sxs-lookup"><span data-stu-id="9a519-144">Overwrite those with the 'en-gb' strings.</span></span>

<span data-ttu-id="9a519-145">Wenn die Sprache des Benutzers auf 'en-ca' gesetzt ist:</span><span class="sxs-lookup"><span data-stu-id="9a519-145">If the user's language is set to 'en-ca':</span></span> 

1. <span data-ttu-id="9a519-146">Der Teams-Client übernimmt die 'fr'-Zeichenfolgen, die sie mit den 'en'-Zeichenfolgen überschreiben.</span><span class="sxs-lookup"><span data-stu-id="9a519-146">The Teams client will take the 'fr' strings overwrite them with the 'en' strings.</span></span>
2. <span data-ttu-id="9a519-147">Da keine "en-ca"-Lokalisierung bereitgestellt wird, werden die "en"-Lokalisierungen verwendet.</span><span class="sxs-lookup"><span data-stu-id="9a519-147">Since no 'en-ca' localization is supplied, the 'en' localizations will be used.</span></span>

<span data-ttu-id="9a519-148">Wenn die Sprache des Benutzers auf 'es-es' gesetzt ist, nimmt der Teams Client die 'fr'-Zeichenfolgen und überschreibt sie nicht mit einer der Sprachdateien.</span><span class="sxs-lookup"><span data-stu-id="9a519-148">If the user's language is set to 'es-es', the Teams client will take the 'fr' strings and will not override them with any of the language files.</span></span>

<span data-ttu-id="9a519-149">Daher wird dringend empfohlen, Übersetzungen auf oberster Ebene, nur für Die Sprache, in Ihrem Manifest bereitzustellen ('en' statt 'en-us') und nur Überschreibungen auf Regionsebene für die wenigen Zeichenfolgen bereitzustellen, die sie benötigen.</span><span class="sxs-lookup"><span data-stu-id="9a519-149">Therefore, it is strongly recommended to provide top-level, language-only translations in your manifest ('en' instead of 'en-us') and only provide region-level overrides for the few strings that need them.</span></span>

### <a name="example-manifestjson-change"></a><span data-ttu-id="9a519-150">Beispiel manifest.jszur Änderung</span><span class="sxs-lookup"><span data-stu-id="9a519-150">Example manifest.json change</span></span>

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

### <a name="example-localization-json-file"></a><span data-ttu-id="9a519-151">Beispiellokalisierung .json-Datei</span><span class="sxs-lookup"><span data-stu-id="9a519-151">Example localization .json file</span></span>

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

## <a name="handling-localized-text-submissions-from-your-users"></a><span data-ttu-id="9a519-152">Behandeln lokalisierter Textübermittlungen von Benutzern</span><span class="sxs-lookup"><span data-stu-id="9a519-152">Handling localized text submissions from your users</span></span>

<span data-ttu-id="9a519-153">Wenn Sie lokalisierte Versionen Ihrer Anwendung bereitstellen, ist es sehr wahrscheinlich, dass Ihre Benutzer mit derselben Sprache antworten.</span><span class="sxs-lookup"><span data-stu-id="9a519-153">If your provide localized versions of your application it is very likely that your users will respond with the same language.</span></span> <span data-ttu-id="9a519-154">Teams übersetzt die Benutzerübermittlungen nicht zurück in die Standardsprache, daher muss Ihre App dies verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="9a519-154">Teams does not translate the user submissions back to the default language, so your app will need to handle that.</span></span> <span data-ttu-id="9a519-155">Wenn Sie z. B. einen lokalisierten befehlsgebundenen Befehl angeben, `commandList` sind die Antworten auf Ihren Bot der lokalisierte Text des Befehls und nicht die Standardsprache.</span><span class="sxs-lookup"><span data-stu-id="9a519-155">For example, if you provide a localized `commandList`, the responses to your bot will be the localized text of the command, not the default language.</span></span> <span data-ttu-id="9a519-156">Ihre App muss entsprechend reagieren.</span><span class="sxs-lookup"><span data-stu-id="9a519-156">Your app will need to respond appropriately.</span></span>

## <a name="code-sample"></a><span data-ttu-id="9a519-157">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="9a519-157">Code sample</span></span>

| <span data-ttu-id="9a519-158">Beispielname</span><span class="sxs-lookup"><span data-stu-id="9a519-158">Sample name</span></span> | <span data-ttu-id="9a519-159">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="9a519-159">Description</span></span> | <span data-ttu-id="9a519-160">.NET</span><span class="sxs-lookup"><span data-stu-id="9a519-160">.NET</span></span> |
|-------------|-------------|------|
| <span data-ttu-id="9a519-161">App-Lokalisierung</span><span class="sxs-lookup"><span data-stu-id="9a519-161">App Localization</span></span> | <span data-ttu-id="9a519-162">Microsoft Teams App-Lokalisierung mit Bot und Tab.</span><span class="sxs-lookup"><span data-stu-id="9a519-162">Microsoft Teams app localization using bot and tab.</span></span> | [<span data-ttu-id="9a519-163">View</span><span class="sxs-lookup"><span data-stu-id="9a519-163">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/app-localization/csharp) |


