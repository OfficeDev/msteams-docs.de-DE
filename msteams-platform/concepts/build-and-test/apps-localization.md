---
title: Lokalisierung für Team-apps
description: Beschreibt Probleme beim Lokalisieren Ihrer APP.
keywords: Teams veröffentlichen Store Office Publishing AppSource Localization Language
ms.date: 05/15/2018
ms.openlocfilehash: 30e4a2589bf5c1093723406c78cff2258554c486
ms.sourcegitcommit: 6c786434b56cc8c2765a14aa1f6149870245f309
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/06/2020
ms.locfileid: "44590858"
---
# <a name="localization-for-microsoft-teams-apps"></a><span data-ttu-id="54a39-104">Lokalisierung für Microsoft Teams-apps</span><span class="sxs-lookup"><span data-stu-id="54a39-104">Localization for Microsoft Teams apps</span></span>

<span data-ttu-id="54a39-105">Beim Lokalisieren Ihrer Microsoft Teams-App gibt es drei wichtige Bereiche, die Sie berücksichtigen müssen.</span><span class="sxs-lookup"><span data-stu-id="54a39-105">When localizing your Microsoft Teams app there are three major areas you need to consider.</span></span>

1. <span data-ttu-id="54a39-106">Ihr AppSource-Eintrag (falls Sie im App Store veröffentlicht werden).</span><span class="sxs-lookup"><span data-stu-id="54a39-106">Your AppSource listing (if you're publishing to the app store).</span></span>
1. <span data-ttu-id="54a39-107">Die benutzerbezogenen Zeichenfolgen in Ihrem App-Manifest (beispielsweise bot-Befehle).</span><span class="sxs-lookup"><span data-stu-id="54a39-107">The end-user facing strings in your app manifest (for example bot commands).</span></span>
1. <span data-ttu-id="54a39-108">Reagieren auf lokalisierten Text, der von Ihren Benutzern übermittelt wurde.</span><span class="sxs-lookup"><span data-stu-id="54a39-108">Responding to localized text submitted from your users.</span></span>

## <a name="localizing-your-appsource-listing"></a><span data-ttu-id="54a39-109">Lokalisieren Ihres AppSource-Eintrags</span><span class="sxs-lookup"><span data-stu-id="54a39-109">Localizing your AppSource listing</span></span>

<span data-ttu-id="54a39-110">Wenn Sie im App Store veröffentlichen, müssen Sie beachten, dass die Lokalisierung Ihres AppSource-Eintrags noch nicht unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="54a39-110">If you're publishing to the app store, you need to be aware that localizing your AppSource listing is not yet supported.</span></span> <span data-ttu-id="54a39-111">In Vorbereitung auf die Unterstützung lokalisierter Auflistungen im App Store können Sie jedoch weitere Sprachen zu Ihrem Angebot hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="54a39-111">However, in preparation for support for localized listings in the app store you can add additional languages to your listing.</span></span> <span data-ttu-id="54a39-112">Derzeit werden nur die standardmäßigen (englischsprachigen) Informationen, die Sie im [Partner Center](/dev/store/use-partner-center-to-submit-to-appsource) für Ihr Angebot angeben, im [AppSource-Website](https://appsource.microsoft.com/marketplace/apps?product=office%3Bteams&page=1) Eintrag für Ihre APP angezeigt.</span><span class="sxs-lookup"><span data-stu-id="54a39-112">Currently only the default (English) language information you provide in [Partner Center](/dev/store/use-partner-center-to-submit-to-appsource) for your listing will appear in the [AppSource website](https://appsource.microsoft.com/marketplace/apps?product=office%3Bteams&page=1) listing for your app.</span></span>

<span data-ttu-id="54a39-113">Zum Konfigurieren einer zusätzlichen Sprache für Ihre APP wählen Sie im [Partner Center](/dev/store/use-partner-center-to-submit-to-appsource)sowohl Englisch als auch die zusätzliche Sprache der APP aus.</span><span class="sxs-lookup"><span data-stu-id="54a39-113">To configure an additional language for your app, in [Partner Center](/dev/store/use-partner-center-to-submit-to-appsource), select both English and the additional language of the app.</span></span> <span data-ttu-id="54a39-114">In diesem Beispiel wird Französisch verwendet.</span><span class="sxs-lookup"><span data-stu-id="54a39-114">French is used in this example.</span></span>

1. <span data-ttu-id="54a39-115">Englische Sprache hinzufügen</span><span class="sxs-lookup"><span data-stu-id="54a39-115">Add English language</span></span>
    * <span data-ttu-id="54a39-116">Geben Sie den APP-Namen ein.</span><span class="sxs-lookup"><span data-stu-id="54a39-116">Fill in the app name.</span></span>
    * <span data-ttu-id="54a39-117">Geben Sie eine kurze Beschreibung der app in englischer Sprache ein.</span><span class="sxs-lookup"><span data-stu-id="54a39-117">Fill in a short description of the app in English.</span></span>
    * <span data-ttu-id="54a39-118">Geben Sie die lange Beschreibung der app in Englisch ein.</span><span class="sxs-lookup"><span data-stu-id="54a39-118">Fill in the long description of the app in English.</span></span>
    * <span data-ttu-id="54a39-119">In der langen Beschreibung fügen Sie bitte auch die-"diese APP ist in Französisch" zur Verfügung.</span><span class="sxs-lookup"><span data-stu-id="54a39-119">In the long description, please also add the line “This app is available in “French”.</span></span>
    * <span data-ttu-id="54a39-120">Laden Sie die Bilder der App-Benutzeroberfläche hoch (in englischer Sprache).</span><span class="sxs-lookup"><span data-stu-id="54a39-120">Upload the images of your app UI (in English).</span></span>
2. <span data-ttu-id="54a39-121">Französisch-Sprache hinzufügen</span><span class="sxs-lookup"><span data-stu-id="54a39-121">Add French language</span></span>
    * <span data-ttu-id="54a39-122">Geben Sie den APP-Namen ein.</span><span class="sxs-lookup"><span data-stu-id="54a39-122">Fill in the app name.</span></span>
    * <span data-ttu-id="54a39-123">Geben Sie eine kurze Beschreibung der app in Französisch ein.</span><span class="sxs-lookup"><span data-stu-id="54a39-123">Fill in a short description of the app in French.</span></span>
    * <span data-ttu-id="54a39-124">Geben Sie die lange Beschreibung der app in Französisch ein.</span><span class="sxs-lookup"><span data-stu-id="54a39-124">Fill in the long description of the app in French.</span></span>
    * <span data-ttu-id="54a39-125">Laden Sie die Bilder der App-Benutzeroberfläche (in Französisch) hoch.</span><span class="sxs-lookup"><span data-stu-id="54a39-125">Upload the images of your app UI (in French).</span></span>

<span data-ttu-id="54a39-126">Die Bilder, die Sie mit der englischen Sprache hochladen, werden in AppSource verwendet.</span><span class="sxs-lookup"><span data-stu-id="54a39-126">The images you upload with the English language will be the ones used in AppSource.</span></span>

## <a name="localizing-the-strings-in-your-app-manifest"></a><span data-ttu-id="54a39-127">Lokalisieren der Zeichenfolgen in Ihrem App-Manifest</span><span class="sxs-lookup"><span data-stu-id="54a39-127">Localizing the strings in your app manifest</span></span>

<span data-ttu-id="54a39-128">Sie müssen das Microsoft Teams-App-Schema v 1.5 + verwenden, um Ihre APP ordnungsgemäß zu lokalisieren.</span><span class="sxs-lookup"><span data-stu-id="54a39-128">You must use the Microsoft Teams app schema v1.5+ to properly localize your app.</span></span> <span data-ttu-id="54a39-129">Sie können dies tun, indem Sie das `$schema` -Attribut in ihrer Manifest. JSON-Datei auf ' https://developer.microsoft.com/json-schemas/teams/v1.7/MicrosoftTeams.schema.json ' festlegen und die Eigenschaft ' manifestVersion ' auf ' 1,5 ' aktualisieren.</span><span class="sxs-lookup"><span data-stu-id="54a39-129">You can do this by setting the `$schema` attribute in your manifest.json file to 'https://developer.microsoft.com/json-schemas/teams/v1.7/MicrosoftTeams.schema.json' and updating the 'manifestVersion' property to '1.5'.</span></span>

### <a name="example-manifestjson-change"></a><span data-ttu-id="54a39-130">Beispiel für Manifest. JSON-Änderung</span><span class="sxs-lookup"><span data-stu-id="54a39-130">Example manifest.json change</span></span>

```json
{
  "$schema": "https://developer.microsoft.com/json-schemas/teams/v1.7/MicrosoftTeams.schema.json",
  "manifestVersion": "1.5",
  ...
}
```

<span data-ttu-id="54a39-131">Anschließend möchten Sie die Eigenschaft "localizationInfo" mit der Standardsprache hinzufügen, die von der Anwendung unterstützt wird.</span><span class="sxs-lookup"><span data-stu-id="54a39-131">You will then want to add the 'localizationInfo' property with the default language that your application supports.</span></span> <span data-ttu-id="54a39-132">Die Standardsprache wird als endgültige Fallbacksprache verwendet, wenn die Clienteinstellungen des Benutzers nicht mit einer ihrer zusätzlichen Sprachen übereinstimmen.</span><span class="sxs-lookup"><span data-stu-id="54a39-132">The default language is used as the final fallback language if the user's client settings do not match any of your additional languages.</span></span>

### <a name="example-manifestjson-change"></a><span data-ttu-id="54a39-133">Beispiel für Manifest. JSON-Änderung</span><span class="sxs-lookup"><span data-stu-id="54a39-133">Example manifest.json change</span></span>

```json
{
  ...
  "localizationInfo": {
    "defaultLanguageTag": "en"
  }
  ...
}
```

<span data-ttu-id="54a39-134">Sie können zusätzliche JSON-Dateien mit Übersetzungen aller Benutzerzeichenfolgen in ihrem Manifest bereitstellen.</span><span class="sxs-lookup"><span data-stu-id="54a39-134">You can provide additional .json files with translations of all the user facing strings in your manifest.</span></span> <span data-ttu-id="54a39-135">Diese Dateien müssen dem [JSON-Schema der Lokalisierungsdatei](../../resources/schema/localization-schema.md) entsprechen, und Sie müssen der Eigenschaft "localizationInfo" des Manifests hinzugefügt werden.</span><span class="sxs-lookup"><span data-stu-id="54a39-135">These files must adhere to the [Localization file JSON schema](../../resources/schema/localization-schema.md) and they must be added to the 'localizationInfo' property of your manifest.</span></span> <span data-ttu-id="54a39-136">Jede Datei korreliert mit einem Language-Tag, das der Microsoft Teams-Client verwendet, um die entsprechenden Zeichenfolgen auszuwählen.</span><span class="sxs-lookup"><span data-stu-id="54a39-136">Each file correlates to a language tag which the Teams client uses to choose the appropriate strings.</span></span> <span data-ttu-id="54a39-137">Das sprach-Tag hat die Form, <language> - <region> aber es wird empfohlen, den Teil auszulassen, der <region> auf alle Regionen abzielt, die die gewünschte Sprache unterstützen.</span><span class="sxs-lookup"><span data-stu-id="54a39-137">The language tag takes the form of <language>-<region> but it is recommended to omit the <region> portion to target all regions that support the desired language.</span></span>

<span data-ttu-id="54a39-138">Der Microsoft Teams-Client wendet die Zeichenfolgen in dieser Reihenfolge an: Standardsprachen Zeichenfolgen – > Sprache des Benutzers nur Zeichenfolgen – > Benutzersprache + Benutzer Regions Zeichenfolgen.</span><span class="sxs-lookup"><span data-stu-id="54a39-138">The Teams client will apply the strings in this order: default language strings -> user's language only strings -> user's language + user's region strings.</span></span>

<span data-ttu-id="54a39-139">Sie geben beispielsweise eine Standardsprache von "fr" (Französisch, alle Regionen) und zusätzliche Sprachdateien für "en" (Englisch, alle Regionen) und "en-GB" (Englisch, Großbritannien) an.</span><span class="sxs-lookup"><span data-stu-id="54a39-139">For example, you provide a default language of 'fr' (French, all regions), and additional language files for 'en' (English, all regions) and 'en-gb' (English, Great Britain).</span></span> <span data-ttu-id="54a39-140">Wenn die Sprache des Benutzers auf "en-GB" festgelegt ist:</span><span class="sxs-lookup"><span data-stu-id="54a39-140">If the user's language is set to 'en-gb':</span></span>

1. <span data-ttu-id="54a39-141">Der Microsoft Teams-Client nimmt die Zeichenfolgen "fr" mit den Zeichenfolgen "en" überschrieben.</span><span class="sxs-lookup"><span data-stu-id="54a39-141">The Teams client will take the 'fr' strings overwrite them with the 'en' strings.</span></span>
2. <span data-ttu-id="54a39-142">Überschreiben Sie diese mit den Zeichenfolgen "en-GB".</span><span class="sxs-lookup"><span data-stu-id="54a39-142">Overwrite those with the 'en-gb' strings.</span></span>

<span data-ttu-id="54a39-143">Wenn die Sprache des Benutzers auf "en-ca" festgelegt ist:</span><span class="sxs-lookup"><span data-stu-id="54a39-143">If the user's language is set to 'en-ca':</span></span> 

1. <span data-ttu-id="54a39-144">Der Microsoft Teams-Client nimmt die Zeichenfolgen "fr" mit den Zeichenfolgen "en" überschrieben.</span><span class="sxs-lookup"><span data-stu-id="54a39-144">The Teams client will take the 'fr' strings overwrite them with the 'en' strings.</span></span>
2. <span data-ttu-id="54a39-145">Da keine "en-ca"-Lokalisierung bereitgestellt wird, werden die "en"-Lokalisierungen verwendet.</span><span class="sxs-lookup"><span data-stu-id="54a39-145">Since no 'en-ca' localization is supplied, the 'en' localizations will be used.</span></span>

<span data-ttu-id="54a39-146">Wenn die Sprache des Benutzers auf "es-es" festgelegt ist, übernimmt der Microsoft Teams-Client die Zeichenfolgen "fr" und setzt diese nicht mit einer der Sprachdateien außer Kraft.</span><span class="sxs-lookup"><span data-stu-id="54a39-146">If the user's language is set to 'es-es', the Teams client will take the 'fr' strings and will not override them with any of the language files.</span></span>

<span data-ttu-id="54a39-147">Daher wird dringend empfohlen, nur Übersetzungen auf oberster Ebene in ihrem Manifest ("en" anstelle von "en-US") bereitzustellen und nur Überschreibungen auf Regionsebene für die wenigen Zeichenfolgen bereitzustellen, die Sie benötigen.</span><span class="sxs-lookup"><span data-stu-id="54a39-147">Therefore, it is strongly recommended to provide top-level, language-only translations in your manifest ('en' instead of 'en-us') and only provide region-level overrides for the few strings that need them.</span></span>

### <a name="example-manifestjson-change"></a><span data-ttu-id="54a39-148">Beispiel für Manifest. JSON-Änderung</span><span class="sxs-lookup"><span data-stu-id="54a39-148">Example manifest.json change</span></span>

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

### <a name="example-localization-json-file"></a><span data-ttu-id="54a39-149">Beispiel für die Datei "Localization. JSON"</span><span class="sxs-lookup"><span data-stu-id="54a39-149">Example localization .json file</span></span>

```json
{
  "$schema": "https://developer.microsoft.com/json-schemas/teams/v1.7/MicrosoftTeams.schema.json",
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

## <a name="handling-localized-text-submissions-from-your-users"></a><span data-ttu-id="54a39-150">Behandeln lokalisierter Text Übermittlungen von Benutzern</span><span class="sxs-lookup"><span data-stu-id="54a39-150">Handling localized text submissions from your users</span></span>

<span data-ttu-id="54a39-151">Wenn Ihre lokalisierten Versionen Ihrer Anwendung bereitstellen, ist es sehr wahrscheinlich, dass Ihre Benutzer mit der gleichen Sprache Antworten werden.</span><span class="sxs-lookup"><span data-stu-id="54a39-151">If your provide localized versions of your application it is very likely that your users will respond with the same language.</span></span> <span data-ttu-id="54a39-152">Die Benutzereingaben werden von Microsoft Teams nicht wieder in die Standardsprache übersetzt, sodass Ihre APP dies verarbeiten muss.</span><span class="sxs-lookup"><span data-stu-id="54a39-152">Teams does not translate the user submissions back to the default language, so your app will need to handle that.</span></span> <span data-ttu-id="54a39-153">Wenn Sie beispielsweise eine lokalisierte bereitstellen `commandList` , sind die Antworten auf Ihren bot der lokalisierte Text des Befehls und nicht die Standardsprache.</span><span class="sxs-lookup"><span data-stu-id="54a39-153">For example, if you provide a localized `commandList`, the responses to your bot will be the localized text of the command, not the default language.</span></span> <span data-ttu-id="54a39-154">Ihre APP muss entsprechend reagiert werden.</span><span class="sxs-lookup"><span data-stu-id="54a39-154">Your app will need to respond appropriately.</span></span>
