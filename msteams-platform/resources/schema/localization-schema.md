---
title: Lokalisierungsdatei – JSON-Schemareferenz
description: Beschreibt das Lokalisierungsschema, das von der Lokalisierungsdatei für Microsoft Teams unterstützt wird
ms.topic: reference
keywords: Manifestschemalokalisierung von Teams
ms.date: 05/20/2019
ms.openlocfilehash: 696a65de70a63e767f8fcdb040364fe90cde8716
ms.sourcegitcommit: 976e870cc925f61b76c3830ec04ba6e4bdfde32f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 01/27/2021
ms.locfileid: "50014600"
---
# <a name="reference-localization-file-json-schema"></a><span data-ttu-id="af268-104">Referenz: Lokalisierungsdatei -JSON-Schema</span><span class="sxs-lookup"><span data-stu-id="af268-104">Reference: Localization file JSON schema</span></span>

<span data-ttu-id="af268-105">Die Lokalisierungsdatei von Microsoft Teams beschreibt Sprachübersetzungen, die basierend auf den Clientspracheinstellungen bedient werden.</span><span class="sxs-lookup"><span data-stu-id="af268-105">The Microsoft Teams localization file describes language translations that will be served based on the client language settings.</span></span> <span data-ttu-id="af268-106">Ihre Datei muss dem Schema entsprechen, das unter [`https://developer.microsoft.com/en-us/json-schemas/teams/v1.8/MicrosoftTeams.Localization.schema.json`](https://developer.microsoft.com/en-us/json-schemas/teams/v1.8/MicrosoftTeams.Localization.schema.json) gehostet wird.</span><span class="sxs-lookup"><span data-stu-id="af268-106">Your file must conform to the schema hosted at [`https://developer.microsoft.com/en-us/json-schemas/teams/v1.8/MicrosoftTeams.Localization.schema.json`](https://developer.microsoft.com/en-us/json-schemas/teams/v1.8/MicrosoftTeams.Localization.schema.json).</span></span> <span data-ttu-id="af268-107">Weitere Informationen finden Sie unter ["App-Lokalisierung".](~/concepts/build-and-test/apps-localization.md)</span><span class="sxs-lookup"><span data-stu-id="af268-107">For additional information see [app localization](~/concepts/build-and-test/apps-localization.md).</span></span>

## <a name="sample"></a><span data-ttu-id="af268-108">Beispiel</span><span class="sxs-lookup"><span data-stu-id="af268-108">Sample</span></span>

```json
{
  "$schema": "https://developer.microsoft.com/json-schemas/teams/v1.8/MicrosoftTeams.schema.json",
  "name.short": "Le App Studio",
  "name.full": "App Studio pour Microsoft Teams",
  "description.short": "Créez d'excellentes applications pour Microsoft Teams avec App Studio.",
  "description.full": "Créez de nouvelles applications Microsoft Teams, concevez et prévisualisez des cartes bot, et explorez la documentation avec App Studio.",
  "staticTabs[0].name": "Editeur de manifest",
  "staticTabs[1].name": "Editeur de cartes",
  "staticTabs[2].name": "Bibliothèque de contrôles",
  "bots[0].commandLists[0].commands[0].title": "chercher",
  "bots[0].commandLists[0].commands[0].description": "Rechercher la documentation Teams pertinente"
}
```

<span data-ttu-id="af268-109">Das Schema definiert die folgenden Eigenschaften:</span><span class="sxs-lookup"><span data-stu-id="af268-109">The schema defines the following properties:</span></span>

## <a name="schema"></a><span data-ttu-id="af268-110">$schema</span><span class="sxs-lookup"><span data-stu-id="af268-110">$schema</span></span>

<span data-ttu-id="af268-111">**uri**</span><span class="sxs-lookup"><span data-stu-id="af268-111">**URI**</span></span>

<span data-ttu-id="af268-112">Die https:// URL, die auf das JSON-Schema für das Manifest verweist.</span><span class="sxs-lookup"><span data-stu-id="af268-112">The https:// URL referencing the JSON Schema for the manifest.</span></span>

> [!TIP]
> <span data-ttu-id="af268-113">Geben Sie das Schema am Anfang des Manifests an, um IntelliSense oder ähnliche Unterstützung von Ihrem Codeeditor zu aktivieren: `"$schema": "https://developer.microsoft.com/json-schemas/teams/v1.8/MicrosoftTeams.schema.json",`</span><span class="sxs-lookup"><span data-stu-id="af268-113">Specify the schema at the beginning of your manifest to enable IntelliSense or similar support from your code editor: `"$schema": "https://developer.microsoft.com/json-schemas/teams/v1.8/MicrosoftTeams.schema.json",`</span></span>

## <a name="nameshort"></a><span data-ttu-id="af268-114">name.short</span><span class="sxs-lookup"><span data-stu-id="af268-114">name.short</span></span>

<span data-ttu-id="af268-115">**Zeichenfolge, Max. Länge 30**</span><span class="sxs-lookup"><span data-stu-id="af268-115">**String, Max Length 30**</span></span>

<span data-ttu-id="af268-116">Ersetzt die entsprechende Zeichenfolge aus dem App-Manifest durch den hier angegebenen Wert.</span><span class="sxs-lookup"><span data-stu-id="af268-116">Replaces the corresponding string from the app manifest with the value provided here.</span></span>

## <a name="namefull"></a><span data-ttu-id="af268-117">name.full</span><span class="sxs-lookup"><span data-stu-id="af268-117">name.full</span></span>

<span data-ttu-id="af268-118">**Zeichenfolge, Max. Länge 100**</span><span class="sxs-lookup"><span data-stu-id="af268-118">**String, Max Length 100**</span></span>

<span data-ttu-id="af268-119">Ersetzt die entsprechende Zeichenfolge aus dem App-Manifest durch den hier angegebenen Wert.</span><span class="sxs-lookup"><span data-stu-id="af268-119">Replaces the corresponding string from the app manifest with the value provided here.</span></span>

## <a name="descriptionshort"></a><span data-ttu-id="af268-120">description.short</span><span class="sxs-lookup"><span data-stu-id="af268-120">description.short</span></span>

<span data-ttu-id="af268-121">**Zeichenfolge, Max. Länge 80**</span><span class="sxs-lookup"><span data-stu-id="af268-121">**String, Max Length 80**</span></span>

<span data-ttu-id="af268-122">Ersetzt die entsprechende Zeichenfolge aus dem App-Manifest durch den hier angegebenen Wert.</span><span class="sxs-lookup"><span data-stu-id="af268-122">Replaces the corresponding string from the app manifest with the value provided here.</span></span>

## <a name="descriptionfull"></a><span data-ttu-id="af268-123">description.full</span><span class="sxs-lookup"><span data-stu-id="af268-123">description.full</span></span>

<span data-ttu-id="af268-124">**Zeichenfolge, Max. Länge 4000**</span><span class="sxs-lookup"><span data-stu-id="af268-124">**String, Max Length 4000**</span></span>

<span data-ttu-id="af268-125">Ersetzt die entsprechende Zeichenfolge aus dem App-Manifest durch den hier angegebenen Wert.</span><span class="sxs-lookup"><span data-stu-id="af268-125">Replaces the corresponding string from the app manifest with the value provided here.</span></span>

## <a name="statictabs0-910-5name"></a><span data-ttu-id="af268-126">staticTabs \\ [([0-9]|1[0-5]) \\ ] \\ .name</span><span class="sxs-lookup"><span data-stu-id="af268-126">staticTabs\\[([0-9]|1[0-5])\\]\\.name</span></span>

<span data-ttu-id="af268-127">**Zeichenfolge, Max. Länge 128**</span><span class="sxs-lookup"><span data-stu-id="af268-127">**String, Max Length 128**</span></span>

<span data-ttu-id="af268-128">Ersetzt die entsprechenden Zeichenfolgen aus dem App-Manifest durch den hier angegebenen Wert.</span><span class="sxs-lookup"><span data-stu-id="af268-128">Replaces the corresponding string(s) from the app manifest with the value provided here.</span></span>

## <a name="bots0commandlists0-2commands0-9title"></a><span data-ttu-id="af268-129">Bots \\ [0 \\ ] \\ .commandLists \\ [[0-2] \\ ] \\ .commands \\ [[0-9] \\ ] \\ .title</span><span class="sxs-lookup"><span data-stu-id="af268-129">bots\\[0\\]\\.commandLists\\[[0-2]\\]\\.commands\\[[0-9]\\]\\.title</span></span>

<span data-ttu-id="af268-130">**Zeichenfolge, Max. Länge 32**</span><span class="sxs-lookup"><span data-stu-id="af268-130">**String, Max Length 32**</span></span>

<span data-ttu-id="af268-131">Ersetzt die entsprechenden Zeichenfolgen aus dem App-Manifest durch den hier angegebenen Wert.</span><span class="sxs-lookup"><span data-stu-id="af268-131">Replaces the corresponding string(s) from the app manifest with the value provided here.</span></span>

## <a name="bots0commandlists0-2commands0-9description"></a><span data-ttu-id="af268-132">Bots \\ [0 \\ ] \\ .commandLists \\ [[0-2] \\ ] \\ .commands \\ [[0-9] \\ ] \\ .description</span><span class="sxs-lookup"><span data-stu-id="af268-132">bots\\[0\\]\\.commandLists\\[[0-2]\\]\\.commands\\[[0-9]\\]\\.description</span></span>

<span data-ttu-id="af268-133">**Zeichenfolge, Max. Länge 128**</span><span class="sxs-lookup"><span data-stu-id="af268-133">**String, Max Length 128**</span></span>

<span data-ttu-id="af268-134">Ersetzt die entsprechenden Zeichenfolgen aus dem App-Manifest durch den hier angegebenen Wert.</span><span class="sxs-lookup"><span data-stu-id="af268-134">Replaces the corresponding string(s) from the app manifest with the value provided here.</span></span>

## <a name="composeextensions0commands0-9title"></a><span data-ttu-id="af268-135">composeExtensions \\ [0 \\ ] \\ .commands \\ [[0-9] \\ ] \\ .title</span><span class="sxs-lookup"><span data-stu-id="af268-135">composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.title</span></span>

<span data-ttu-id="af268-136">**Zeichenfolge, Max. Länge 32**</span><span class="sxs-lookup"><span data-stu-id="af268-136">**String, Max Length 32**</span></span>

<span data-ttu-id="af268-137">Ersetzt die entsprechenden Zeichenfolgen aus dem App-Manifest durch den hier angegebenen Wert.</span><span class="sxs-lookup"><span data-stu-id="af268-137">Replaces the corresponding string(s) from the app manifest with the value provided here.</span></span>

## <a name="composeextensions0commands0-9description"></a><span data-ttu-id="af268-138">composeExtensions \\ [0 \\ ] \\ .commands \\ [[0-9] \\ ] \\ .description</span><span class="sxs-lookup"><span data-stu-id="af268-138">composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.description</span></span>

<span data-ttu-id="af268-139">**Zeichenfolge, Max. Länge 128**</span><span class="sxs-lookup"><span data-stu-id="af268-139">**String, Max Length 128**</span></span>

<span data-ttu-id="af268-140">Ersetzt die entsprechenden Zeichenfolgen aus dem App-Manifest durch den hier angegebenen Wert.</span><span class="sxs-lookup"><span data-stu-id="af268-140">Replaces the corresponding string(s) from the app manifest with the value provided here.</span></span>

## <a name="composeextensions0commands0-9parameters0-4title"></a><span data-ttu-id="af268-141">composeExtensions \\ [0 \\ ] \\ .commands \\ [[0-9] \\ ] \\ .parameters \\ [[0-4] \\ ] \\ .title</span><span class="sxs-lookup"><span data-stu-id="af268-141">composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.title</span></span>

<span data-ttu-id="af268-142">**Zeichenfolge, Max. Länge 32**</span><span class="sxs-lookup"><span data-stu-id="af268-142">**String, Max Length 32**</span></span>

<span data-ttu-id="af268-143">Ersetzt die entsprechenden Zeichenfolgen aus dem App-Manifest durch den hier angegebenen Wert.</span><span class="sxs-lookup"><span data-stu-id="af268-143">Replaces the corresponding string(s) from the app manifest with the value provided here.</span></span>

## <a name="composeextensions0commands0-9parameters0-4description"></a><span data-ttu-id="af268-144">composeExtensions \\ [0 \\ ] \\ .commands \\ [[0-9] \\ ] \\ .parameters \\ [[0-4] \\ ] \\ .description</span><span class="sxs-lookup"><span data-stu-id="af268-144">composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.description</span></span>

<span data-ttu-id="af268-145">**Zeichenfolge, Max. Länge 128**</span><span class="sxs-lookup"><span data-stu-id="af268-145">**String, Max Length 128**</span></span>

<span data-ttu-id="af268-146">Ersetzt die entsprechenden Zeichenfolgen aus dem App-Manifest durch den hier angegebenen Wert.</span><span class="sxs-lookup"><span data-stu-id="af268-146">Replaces the corresponding string(s) from the app manifest with the value provided here.</span></span>

## <a name="composeextensions0commands0-9parameters0-4value"></a><span data-ttu-id="af268-147">composeExtensions \\ [0 \\ ] \\ .commands \\ [[0-9] \\ ] \\ .parameters \\ [[0-4] \\ ] \\ .value</span><span class="sxs-lookup"><span data-stu-id="af268-147">composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.value</span></span>

<span data-ttu-id="af268-148">**Zeichenfolge, Max. Länge 512**</span><span class="sxs-lookup"><span data-stu-id="af268-148">**String, Max Length 512**</span></span>

<span data-ttu-id="af268-149">Ersetzt die entsprechenden Zeichenfolgen aus dem App-Manifest durch den hier angegebenen Wert.</span><span class="sxs-lookup"><span data-stu-id="af268-149">Replaces the corresponding string(s) from the app manifest with the value provided here.</span></span>

## <a name="composeextensions0commands0-9parameters0-4choices0-9title"></a><span data-ttu-id="af268-150">composeExtensions \\ [0 \\ ] \\ .commands \\ [[0-9] \\ ] \\ .parameters \\ [[0-4] \\ ] \\ .choices \\ [[0-9] \\ ] \\ .title</span><span class="sxs-lookup"><span data-stu-id="af268-150">composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.choices\\[[0-9]\\]\\.title</span></span>

<span data-ttu-id="af268-151">**Zeichenfolge, Max. Länge 128**</span><span class="sxs-lookup"><span data-stu-id="af268-151">**String, Max Length 128**</span></span>

<span data-ttu-id="af268-152">Ersetzt die entsprechenden Zeichenfolgen aus dem App-Manifest durch den hier angegebenen Wert.</span><span class="sxs-lookup"><span data-stu-id="af268-152">Replaces the corresponding string(s) from the app manifest with the value provided here.</span></span>

## <a name="composeextensions0commands0-9taskinfotitle"></a><span data-ttu-id="af268-153">composeExtensions \\ [0 \\ ] \\ .commands \\ [[0-9] \\ ] \\ .taskInfo \\ .title</span><span class="sxs-lookup"><span data-stu-id="af268-153">composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.taskInfo\\.title</span></span>

<span data-ttu-id="af268-154">**Zeichenfolge, Max. Länge 64**</span><span class="sxs-lookup"><span data-stu-id="af268-154">**String, Max Length 64**</span></span>

<span data-ttu-id="af268-155">Ersetzt die entsprechenden Zeichenfolgen aus dem App-Manifest durch den hier angegebenen Wert.</span><span class="sxs-lookup"><span data-stu-id="af268-155">Replaces the corresponding string(s) from the app manifest with the value provided here.</span></span>
