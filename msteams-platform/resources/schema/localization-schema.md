---
title: JSON-Schemareferenz für Lokalisierungsdatei
description: Beschreibt das von der Lokalisierungsdatei für Microsoft Teams unterstützte Lokalisierungs Schema.
keywords: Schema Lokalisierung für Teams-Manifestdatei
ms.date: 05/20/2019
ms.openlocfilehash: 2c0f449ef0b018e0ed377ea8f5d79b285b36e829
ms.sourcegitcommit: 0aeb60027f423d8ceff3b377db8c3efbb6da4d17
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 11/11/2020
ms.locfileid: "48997965"
---
# <a name="reference-localization-file-json-schema"></a><span data-ttu-id="0ca58-104">Referenz: JSON-Schema der Lokalisierungsdatei</span><span class="sxs-lookup"><span data-stu-id="0ca58-104">Reference: Localization file JSON schema</span></span>

<span data-ttu-id="0ca58-105">In der Microsoft Teams-Lokalisierungsdatei werden Sprachübersetzungen beschrieben, die basierend auf den Clientspracheinstellungen bedient werden.</span><span class="sxs-lookup"><span data-stu-id="0ca58-105">The Microsoft Teams localization file describes language translations that will be served based on the client language settings.</span></span> <span data-ttu-id="0ca58-106">Die Datei muss dem Schema entsprechen, das unter gehostet wird [`https://developer.microsoft.com/en-us/json-schemas/teams/v1.8/MicrosoftTeams.Localization.schema.json`](https://developer.microsoft.com/en-us/json-schemas/teams/v1.8/MicrosoftTeams.Localization.schema.json) .</span><span class="sxs-lookup"><span data-stu-id="0ca58-106">Your file must conform to the schema hosted at [`https://developer.microsoft.com/en-us/json-schemas/teams/v1.8/MicrosoftTeams.Localization.schema.json`](https://developer.microsoft.com/en-us/json-schemas/teams/v1.8/MicrosoftTeams.Localization.schema.json).</span></span> <span data-ttu-id="0ca58-107">Weitere Informationen finden Sie unter [App-Lokalisierung](~/concepts/build-and-test/apps-localization.md).</span><span class="sxs-lookup"><span data-stu-id="0ca58-107">For additional information see [app localization](~/concepts/build-and-test/apps-localization.md).</span></span>

## <a name="sample"></a><span data-ttu-id="0ca58-108">Beispiel</span><span class="sxs-lookup"><span data-stu-id="0ca58-108">Sample</span></span>

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

<span data-ttu-id="0ca58-109">Das Schema definiert die folgenden Eigenschaften:</span><span class="sxs-lookup"><span data-stu-id="0ca58-109">The schema defines the following properties:</span></span>

## <a name="schema"></a><span data-ttu-id="0ca58-110">$schema</span><span class="sxs-lookup"><span data-stu-id="0ca58-110">$schema</span></span>

<span data-ttu-id="0ca58-111">**uri**</span><span class="sxs-lookup"><span data-stu-id="0ca58-111">**URI**</span></span>

<span data-ttu-id="0ca58-112">Die https://-URL, die auf das JSON-Schema für das Manifest verweist.</span><span class="sxs-lookup"><span data-stu-id="0ca58-112">The https:// URL referencing the JSON Schema for the manifest.</span></span>

> [!TIP]
> <span data-ttu-id="0ca58-113">Geben Sie das Schema am Anfang des Manifests an, um IntelliSense oder ähnliche Unterstützung aus Ihrem Code-Editor zu aktivieren: `"$schema": "https://developer.microsoft.com/json-schemas/teams/v1.8/MicrosoftTeams.schema.json",`</span><span class="sxs-lookup"><span data-stu-id="0ca58-113">Specify the schema at the beginning of your manifest to enable IntelliSense or similar support from your code editor: `"$schema": "https://developer.microsoft.com/json-schemas/teams/v1.8/MicrosoftTeams.schema.json",`</span></span>

## <a name="nameshort"></a><span data-ttu-id="0ca58-114">Name. Short</span><span class="sxs-lookup"><span data-stu-id="0ca58-114">name.short</span></span>

<span data-ttu-id="0ca58-115">**Zeichenfolge, maximale Länge 30**</span><span class="sxs-lookup"><span data-stu-id="0ca58-115">**String, Max Length 30**</span></span>

<span data-ttu-id="0ca58-116">Ersetzt die entsprechende Zeichenfolge aus dem App-Manifest durch den hier angegebenen Wert.</span><span class="sxs-lookup"><span data-stu-id="0ca58-116">Replaces the corresponding string from the app manifest with the value provided here.</span></span>

## <a name="namefull"></a><span data-ttu-id="0ca58-117">Name. Full</span><span class="sxs-lookup"><span data-stu-id="0ca58-117">name.full</span></span>

<span data-ttu-id="0ca58-118">**Zeichenfolge, maximale Länge 100**</span><span class="sxs-lookup"><span data-stu-id="0ca58-118">**String, Max Length 100**</span></span>

<span data-ttu-id="0ca58-119">Ersetzt die entsprechende Zeichenfolge aus dem App-Manifest durch den hier angegebenen Wert.</span><span class="sxs-lookup"><span data-stu-id="0ca58-119">Replaces the corresponding string from the app manifest with the value provided here.</span></span>

## <a name="descriptionshort"></a><span data-ttu-id="0ca58-120">Description. Short</span><span class="sxs-lookup"><span data-stu-id="0ca58-120">description.short</span></span>

<span data-ttu-id="0ca58-121">**Zeichenfolge, maximale Länge 80**</span><span class="sxs-lookup"><span data-stu-id="0ca58-121">**String, Max Length 80**</span></span>

<span data-ttu-id="0ca58-122">Ersetzt die entsprechende Zeichenfolge aus dem App-Manifest durch den hier angegebenen Wert.</span><span class="sxs-lookup"><span data-stu-id="0ca58-122">Replaces the corresponding string from the app manifest with the value provided here.</span></span>

## <a name="descriptionfull"></a><span data-ttu-id="0ca58-123">Description. Full</span><span class="sxs-lookup"><span data-stu-id="0ca58-123">description.full</span></span>

<span data-ttu-id="0ca58-124">**Zeichenfolge, maximale Länge 4000**</span><span class="sxs-lookup"><span data-stu-id="0ca58-124">**String, Max Length 4000**</span></span>

<span data-ttu-id="0ca58-125">Ersetzt die entsprechende Zeichenfolge aus dem App-Manifest durch den hier angegebenen Wert.</span><span class="sxs-lookup"><span data-stu-id="0ca58-125">Replaces the corresponding string from the app manifest with the value provided here.</span></span>

## <a name="statictabs0-910-5name"></a><span data-ttu-id="0ca58-126">staticTabs \\ [([0-9] | 1 [0-5]) \\ ] \\ . Name</span><span class="sxs-lookup"><span data-stu-id="0ca58-126">staticTabs\\[([0-9]|1[0-5])\\]\\.name</span></span>

<span data-ttu-id="0ca58-127">**Zeichenfolge, maximale Länge 128**</span><span class="sxs-lookup"><span data-stu-id="0ca58-127">**String, Max Length 128**</span></span>

<span data-ttu-id="0ca58-128">Ersetzt die entsprechenden Zeichenfolgen (en) aus dem App-Manifest durch den hier angegebenen Wert.</span><span class="sxs-lookup"><span data-stu-id="0ca58-128">Replaces the corresponding string(s) from the app manifest with the value provided here.</span></span>

## <a name="bots0commandlists0-2commands0-9title"></a><span data-ttu-id="0ca58-129">Bots \\ [0 \\ ] \\ . commandLists \\ [[0-2] \\ ] \\ . Commands \\ [[0-9] \\ ] \\ . Title</span><span class="sxs-lookup"><span data-stu-id="0ca58-129">bots\\[0\\]\\.commandLists\\[[0-2]\\]\\.commands\\[[0-9]\\]\\.title</span></span>

<span data-ttu-id="0ca58-130">**Zeichenfolge, maximale Länge 32**</span><span class="sxs-lookup"><span data-stu-id="0ca58-130">**String, Max Length 32**</span></span>

<span data-ttu-id="0ca58-131">Ersetzt die entsprechenden Zeichenfolgen (en) aus dem App-Manifest durch den hier angegebenen Wert.</span><span class="sxs-lookup"><span data-stu-id="0ca58-131">Replaces the corresponding string(s) from the app manifest with the value provided here.</span></span>

## <a name="bots0commandlists0-2commands0-9description"></a><span data-ttu-id="0ca58-132">Bots \\ [0 \\ ] \\ . commandLists \\ [[0-2] \\ ] \\ . Commands \\ [[0-9] \\ ] \\ . Description</span><span class="sxs-lookup"><span data-stu-id="0ca58-132">bots\\[0\\]\\.commandLists\\[[0-2]\\]\\.commands\\[[0-9]\\]\\.description</span></span>

<span data-ttu-id="0ca58-133">**Zeichenfolge, maximale Länge 128**</span><span class="sxs-lookup"><span data-stu-id="0ca58-133">**String, Max Length 128**</span></span>

<span data-ttu-id="0ca58-134">Ersetzt die entsprechenden Zeichenfolgen (en) aus dem App-Manifest durch den hier angegebenen Wert.</span><span class="sxs-lookup"><span data-stu-id="0ca58-134">Replaces the corresponding string(s) from the app manifest with the value provided here.</span></span>

## <a name="composeextensions0commands0-9title"></a><span data-ttu-id="0ca58-135">composeExtensions \\ [0 \\ ] \\ . Commands \\ [[0-9] \\ ] \\ . Title</span><span class="sxs-lookup"><span data-stu-id="0ca58-135">composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.title</span></span>

<span data-ttu-id="0ca58-136">**Zeichenfolge, maximale Länge 32**</span><span class="sxs-lookup"><span data-stu-id="0ca58-136">**String, Max Length 32**</span></span>

<span data-ttu-id="0ca58-137">Ersetzt die entsprechenden Zeichenfolgen (en) aus dem App-Manifest durch den hier angegebenen Wert.</span><span class="sxs-lookup"><span data-stu-id="0ca58-137">Replaces the corresponding string(s) from the app manifest with the value provided here.</span></span>

## <a name="composeextensions0commands0-9description"></a><span data-ttu-id="0ca58-138">composeExtensions \\ [0 \\ ] \\ . Commands \\ [[0-9] \\ ] \\ . Description</span><span class="sxs-lookup"><span data-stu-id="0ca58-138">composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.description</span></span>

<span data-ttu-id="0ca58-139">**Zeichenfolge, maximale Länge 128**</span><span class="sxs-lookup"><span data-stu-id="0ca58-139">**String, Max Length 128**</span></span>

<span data-ttu-id="0ca58-140">Ersetzt die entsprechenden Zeichenfolgen (en) aus dem App-Manifest durch den hier angegebenen Wert.</span><span class="sxs-lookup"><span data-stu-id="0ca58-140">Replaces the corresponding string(s) from the app manifest with the value provided here.</span></span>

## <a name="composeextensions0commands0-9parameters0-4title"></a><span data-ttu-id="0ca58-141">composeExtensions \\ [0 \\ ] \\ . Commands \\ [[0-9] \\ ] \\ . Parameters \\ [[0-4] \\ ] \\ . Title</span><span class="sxs-lookup"><span data-stu-id="0ca58-141">composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.title</span></span>

<span data-ttu-id="0ca58-142">**Zeichenfolge, maximale Länge 32**</span><span class="sxs-lookup"><span data-stu-id="0ca58-142">**String, Max Length 32**</span></span>

<span data-ttu-id="0ca58-143">Ersetzt die entsprechenden Zeichenfolgen (en) aus dem App-Manifest durch den hier angegebenen Wert.</span><span class="sxs-lookup"><span data-stu-id="0ca58-143">Replaces the corresponding string(s) from the app manifest with the value provided here.</span></span>

## <a name="composeextensions0commands0-9parameters0-4description"></a><span data-ttu-id="0ca58-144">composeExtensions \\ [0 \\ ] \\ . Commands \\ [[0-9] \\ ] \\ . Parameters \\ [[0-4] \\ ] \\ . Description</span><span class="sxs-lookup"><span data-stu-id="0ca58-144">composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.description</span></span>

<span data-ttu-id="0ca58-145">**Zeichenfolge, maximale Länge 128**</span><span class="sxs-lookup"><span data-stu-id="0ca58-145">**String, Max Length 128**</span></span>

<span data-ttu-id="0ca58-146">Ersetzt die entsprechenden Zeichenfolgen (en) aus dem App-Manifest durch den hier angegebenen Wert.</span><span class="sxs-lookup"><span data-stu-id="0ca58-146">Replaces the corresponding string(s) from the app manifest with the value provided here.</span></span>

## <a name="composeextensions0commands0-9parameters0-4value"></a><span data-ttu-id="0ca58-147">composeExtensions \\ [0 \\ ] \\ . Commands \\ [[0-9] \\ ] \\ . Parameters \\ [[0-4] \\ ] \\ . Value</span><span class="sxs-lookup"><span data-stu-id="0ca58-147">composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.value</span></span>

<span data-ttu-id="0ca58-148">**Zeichenfolge, maximale Länge 512**</span><span class="sxs-lookup"><span data-stu-id="0ca58-148">**String, Max Length 512**</span></span>

<span data-ttu-id="0ca58-149">Ersetzt die entsprechenden Zeichenfolgen (en) aus dem App-Manifest durch den hier angegebenen Wert.</span><span class="sxs-lookup"><span data-stu-id="0ca58-149">Replaces the corresponding string(s) from the app manifest with the value provided here.</span></span>

## <a name="composeextensions0commands0-9parameters0-4choices0-9title"></a><span data-ttu-id="0ca58-150">composeExtensions \\ [0 \\ ] \\ . Commands \\ [[0-9] \\ ] \\ . Parameters \\ [[0-4] \\ ] \\ . Choices \\ [[0-9] \\ ] \\ . Title</span><span class="sxs-lookup"><span data-stu-id="0ca58-150">composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.choices\\[[0-9]\\]\\.title</span></span>

<span data-ttu-id="0ca58-151">**Zeichenfolge, maximale Länge 128**</span><span class="sxs-lookup"><span data-stu-id="0ca58-151">**String, Max Length 128**</span></span>

<span data-ttu-id="0ca58-152">Ersetzt die entsprechenden Zeichenfolgen (en) aus dem App-Manifest durch den hier angegebenen Wert.</span><span class="sxs-lookup"><span data-stu-id="0ca58-152">Replaces the corresponding string(s) from the app manifest with the value provided here.</span></span>

## <a name="composeextensions0commands0-9taskinfotitle"></a><span data-ttu-id="0ca58-153">composeExtensions \\ [0 \\ ] \\ . Commands \\ [[0-9] \\ ] \\ . taskInfo \\ . Title</span><span class="sxs-lookup"><span data-stu-id="0ca58-153">composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.taskInfo\\.title</span></span>

<span data-ttu-id="0ca58-154">**Zeichenfolge, maximale Länge 64**</span><span class="sxs-lookup"><span data-stu-id="0ca58-154">**String, Max Length 64**</span></span>

<span data-ttu-id="0ca58-155">Ersetzt die entsprechenden Zeichenfolgen (en) aus dem App-Manifest durch den hier angegebenen Wert.</span><span class="sxs-lookup"><span data-stu-id="0ca58-155">Replaces the corresponding string(s) from the app manifest with the value provided here.</span></span>
