---
title: JSON-Schemareferenz für Lokalisierungsdatei
description: Beschreibt das lokalisierungsschema, das von der Lokalisierungsdatei für Microsoft Teams
ms.topic: reference
localization_priority: Normal
keywords: Manifestschemalokalisierung von Teams
ms.date: 05/20/2019
ms.openlocfilehash: 3e4207fb3e862eac18c80ffc49e7c5648ae05c28
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2021
ms.locfileid: "52019706"
---
# <a name="reference-localization-file-json-schema"></a><span data-ttu-id="7a491-104">Referenz: JSON-Schema der Lokalisierungsdatei</span><span class="sxs-lookup"><span data-stu-id="7a491-104">Reference: Localization file JSON schema</span></span>

<span data-ttu-id="7a491-105">In Microsoft Teams werden Sprachübersetzungen beschrieben, die basierend auf den Clientspracheneinstellungen bedient werden.</span><span class="sxs-lookup"><span data-stu-id="7a491-105">The Microsoft Teams localization file describes language translations that will be served based on the client language settings.</span></span> <span data-ttu-id="7a491-106">Ihre Datei muss dem schema entsprechen, das unter gehostet [`https://developer.microsoft.com/en-us/json-schemas/teams/v1.8/MicrosoftTeams.Localization.schema.json`](https://developer.microsoft.com/en-us/json-schemas/teams/v1.8/MicrosoftTeams.Localization.schema.json) wird.</span><span class="sxs-lookup"><span data-stu-id="7a491-106">Your file must conform to the schema hosted at [`https://developer.microsoft.com/en-us/json-schemas/teams/v1.8/MicrosoftTeams.Localization.schema.json`](https://developer.microsoft.com/en-us/json-schemas/teams/v1.8/MicrosoftTeams.Localization.schema.json).</span></span> <span data-ttu-id="7a491-107">Weitere Informationen finden Sie unter [App-Lokalisierung](~/concepts/build-and-test/apps-localization.md).</span><span class="sxs-lookup"><span data-stu-id="7a491-107">For additional information see [app localization](~/concepts/build-and-test/apps-localization.md).</span></span>

## <a name="sample"></a><span data-ttu-id="7a491-108">Beispiel</span><span class="sxs-lookup"><span data-stu-id="7a491-108">Sample</span></span>

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

<span data-ttu-id="7a491-109">Das Schema definiert die folgenden Eigenschaften:</span><span class="sxs-lookup"><span data-stu-id="7a491-109">The schema defines the following properties:</span></span>

## <a name="schema"></a><span data-ttu-id="7a491-110">$schema</span><span class="sxs-lookup"><span data-stu-id="7a491-110">$schema</span></span>

<span data-ttu-id="7a491-111">**uri**</span><span class="sxs-lookup"><span data-stu-id="7a491-111">**URI**</span></span>

<span data-ttu-id="7a491-112">Die https://-URL, die auf das JSON-Schema für das Manifest verweist.</span><span class="sxs-lookup"><span data-stu-id="7a491-112">The https:// URL referencing the JSON Schema for the manifest.</span></span>

> [!TIP]
> <span data-ttu-id="7a491-113">Geben Sie das Schema am Anfang des Manifests an, um IntelliSense oder ähnliche Unterstützung von Ihrem Code-Editor zu aktivieren:`"$schema": "https://developer.microsoft.com/json-schemas/teams/v1.8/MicrosoftTeams.schema.json",`</span><span class="sxs-lookup"><span data-stu-id="7a491-113">Specify the schema at the beginning of your manifest to enable IntelliSense or similar support from your code editor: `"$schema": "https://developer.microsoft.com/json-schemas/teams/v1.8/MicrosoftTeams.schema.json",`</span></span>

## <a name="nameshort"></a><span data-ttu-id="7a491-114">name.short</span><span class="sxs-lookup"><span data-stu-id="7a491-114">name.short</span></span>

<span data-ttu-id="7a491-115">**Zeichenfolge, Max. Länge 30**</span><span class="sxs-lookup"><span data-stu-id="7a491-115">**String, Max Length 30**</span></span>

<span data-ttu-id="7a491-116">Ersetzt die entsprechende Zeichenfolge aus dem App-Manifest durch den hier angegebenen Wert.</span><span class="sxs-lookup"><span data-stu-id="7a491-116">Replaces the corresponding string from the app manifest with the value provided here.</span></span>

## <a name="namefull"></a><span data-ttu-id="7a491-117">name.full</span><span class="sxs-lookup"><span data-stu-id="7a491-117">name.full</span></span>

<span data-ttu-id="7a491-118">**Zeichenfolge, Max. Länge 100**</span><span class="sxs-lookup"><span data-stu-id="7a491-118">**String, Max Length 100**</span></span>

<span data-ttu-id="7a491-119">Ersetzt die entsprechende Zeichenfolge aus dem App-Manifest durch den hier angegebenen Wert.</span><span class="sxs-lookup"><span data-stu-id="7a491-119">Replaces the corresponding string from the app manifest with the value provided here.</span></span>

## <a name="descriptionshort"></a><span data-ttu-id="7a491-120">description.short</span><span class="sxs-lookup"><span data-stu-id="7a491-120">description.short</span></span>

<span data-ttu-id="7a491-121">**Zeichenfolge, Max. Länge 80**</span><span class="sxs-lookup"><span data-stu-id="7a491-121">**String, Max Length 80**</span></span>

<span data-ttu-id="7a491-122">Ersetzt die entsprechende Zeichenfolge aus dem App-Manifest durch den hier angegebenen Wert.</span><span class="sxs-lookup"><span data-stu-id="7a491-122">Replaces the corresponding string from the app manifest with the value provided here.</span></span>

## <a name="descriptionfull"></a><span data-ttu-id="7a491-123">description.full</span><span class="sxs-lookup"><span data-stu-id="7a491-123">description.full</span></span>

<span data-ttu-id="7a491-124">**Zeichenfolge, Max. Länge 4000**</span><span class="sxs-lookup"><span data-stu-id="7a491-124">**String, Max Length 4000**</span></span>

<span data-ttu-id="7a491-125">Ersetzt die entsprechende Zeichenfolge aus dem App-Manifest durch den hier angegebenen Wert.</span><span class="sxs-lookup"><span data-stu-id="7a491-125">Replaces the corresponding string from the app manifest with the value provided here.</span></span>

## <a name="statictabs0-910-5name"></a><span data-ttu-id="7a491-126">staticTabs \\ [([0-9]|1[0-5]) \\ ] \\ .name</span><span class="sxs-lookup"><span data-stu-id="7a491-126">staticTabs\\[([0-9]|1[0-5])\\]\\.name</span></span>

<span data-ttu-id="7a491-127">**Zeichenfolge, Max. Länge 128**</span><span class="sxs-lookup"><span data-stu-id="7a491-127">**String, Max Length 128**</span></span>

<span data-ttu-id="7a491-128">Ersetzt die entsprechenden Zeichenfolgen aus dem App-Manifest durch den hier angegebenen Wert.</span><span class="sxs-lookup"><span data-stu-id="7a491-128">Replaces the corresponding string(s) from the app manifest with the value provided here.</span></span>

## <a name="bots0commandlists0-2commands0-9title"></a><span data-ttu-id="7a491-129">bots \\ [0 \\ ] \\ .commandLists \\ [[0-2] \\ ] \\ .commands \\ [[0-9] \\ ] \\ .title</span><span class="sxs-lookup"><span data-stu-id="7a491-129">bots\\[0\\]\\.commandLists\\[[0-2]\\]\\.commands\\[[0-9]\\]\\.title</span></span>

<span data-ttu-id="7a491-130">**Zeichenfolge, Max. Länge 32**</span><span class="sxs-lookup"><span data-stu-id="7a491-130">**String, Max Length 32**</span></span>

<span data-ttu-id="7a491-131">Ersetzt die entsprechenden Zeichenfolgen aus dem App-Manifest durch den hier angegebenen Wert.</span><span class="sxs-lookup"><span data-stu-id="7a491-131">Replaces the corresponding string(s) from the app manifest with the value provided here.</span></span>

## <a name="bots0commandlists0-2commands0-9description"></a><span data-ttu-id="7a491-132">bots \\ [0 \\ ] \\ .commandLists \\ [[0-2] \\ ] \\ .commands \\ [[0-9] \\ ] \\ .description</span><span class="sxs-lookup"><span data-stu-id="7a491-132">bots\\[0\\]\\.commandLists\\[[0-2]\\]\\.commands\\[[0-9]\\]\\.description</span></span>

<span data-ttu-id="7a491-133">**Zeichenfolge, Max. Länge 128**</span><span class="sxs-lookup"><span data-stu-id="7a491-133">**String, Max Length 128**</span></span>

<span data-ttu-id="7a491-134">Ersetzt die entsprechenden Zeichenfolgen aus dem App-Manifest durch den hier angegebenen Wert.</span><span class="sxs-lookup"><span data-stu-id="7a491-134">Replaces the corresponding string(s) from the app manifest with the value provided here.</span></span>

## <a name="composeextensions0commands0-9title"></a><span data-ttu-id="7a491-135">composeExtensions \\ [0 \\ ] \\ .commands \\ [[0-9] \\ ] \\ .title</span><span class="sxs-lookup"><span data-stu-id="7a491-135">composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.title</span></span>

<span data-ttu-id="7a491-136">**Zeichenfolge, Max. Länge 32**</span><span class="sxs-lookup"><span data-stu-id="7a491-136">**String, Max Length 32**</span></span>

<span data-ttu-id="7a491-137">Ersetzt die entsprechenden Zeichenfolgen aus dem App-Manifest durch den hier angegebenen Wert.</span><span class="sxs-lookup"><span data-stu-id="7a491-137">Replaces the corresponding string(s) from the app manifest with the value provided here.</span></span>

## <a name="composeextensions0commands0-9description"></a><span data-ttu-id="7a491-138">composeExtensions \\ [0 \\ ] \\ .commands \\ [[0-9] \\ ] \\ .description</span><span class="sxs-lookup"><span data-stu-id="7a491-138">composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.description</span></span>

<span data-ttu-id="7a491-139">**Zeichenfolge, Max. Länge 128**</span><span class="sxs-lookup"><span data-stu-id="7a491-139">**String, Max Length 128**</span></span>

<span data-ttu-id="7a491-140">Ersetzt die entsprechenden Zeichenfolgen aus dem App-Manifest durch den hier angegebenen Wert.</span><span class="sxs-lookup"><span data-stu-id="7a491-140">Replaces the corresponding string(s) from the app manifest with the value provided here.</span></span>

## <a name="composeextensions0commands0-9parameters0-4title"></a><span data-ttu-id="7a491-141">composeExtensions \\ [0 \\ ] \\ .commands \\ [[0-9] \\ ] \\ .parameters \\ [[0-4] \\ ] \\ .title</span><span class="sxs-lookup"><span data-stu-id="7a491-141">composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.title</span></span>

<span data-ttu-id="7a491-142">**Zeichenfolge, Max. Länge 32**</span><span class="sxs-lookup"><span data-stu-id="7a491-142">**String, Max Length 32**</span></span>

<span data-ttu-id="7a491-143">Ersetzt die entsprechenden Zeichenfolgen aus dem App-Manifest durch den hier angegebenen Wert.</span><span class="sxs-lookup"><span data-stu-id="7a491-143">Replaces the corresponding string(s) from the app manifest with the value provided here.</span></span>

## <a name="composeextensions0commands0-9parameters0-4description"></a><span data-ttu-id="7a491-144">composeExtensions \\ [0 \\ ] \\ .commands \\ [[0-9] \\ ] \\ .parameters \\ [[0-4] \\ ] \\ .description</span><span class="sxs-lookup"><span data-stu-id="7a491-144">composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.description</span></span>

<span data-ttu-id="7a491-145">**Zeichenfolge, Max. Länge 128**</span><span class="sxs-lookup"><span data-stu-id="7a491-145">**String, Max Length 128**</span></span>

<span data-ttu-id="7a491-146">Ersetzt die entsprechenden Zeichenfolgen aus dem App-Manifest durch den hier angegebenen Wert.</span><span class="sxs-lookup"><span data-stu-id="7a491-146">Replaces the corresponding string(s) from the app manifest with the value provided here.</span></span>

## <a name="composeextensions0commands0-9parameters0-4value"></a><span data-ttu-id="7a491-147">composeExtensions \\ [0 \\ ] \\ .commands \\ [[0-9] \\ ] \\ .parameters \\ [[0-4] \\ ] \\ .value</span><span class="sxs-lookup"><span data-stu-id="7a491-147">composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.value</span></span>

<span data-ttu-id="7a491-148">**Zeichenfolge, Max. Länge 512**</span><span class="sxs-lookup"><span data-stu-id="7a491-148">**String, Max Length 512**</span></span>

<span data-ttu-id="7a491-149">Ersetzt die entsprechenden Zeichenfolgen aus dem App-Manifest durch den hier angegebenen Wert.</span><span class="sxs-lookup"><span data-stu-id="7a491-149">Replaces the corresponding string(s) from the app manifest with the value provided here.</span></span>

## <a name="composeextensions0commands0-9parameters0-4choices0-9title"></a><span data-ttu-id="7a491-150">composeExtensions \\ [0 \\ ] \\ .commands \\ [[0-9] \\ ] \\ .parameters \\ [[0-4] \\ ] \\ .choices \\ [[0-9] \\ ] \\ .title</span><span class="sxs-lookup"><span data-stu-id="7a491-150">composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.parameters\\[[0-4]\\]\\.choices\\[[0-9]\\]\\.title</span></span>

<span data-ttu-id="7a491-151">**Zeichenfolge, Max. Länge 128**</span><span class="sxs-lookup"><span data-stu-id="7a491-151">**String, Max Length 128**</span></span>

<span data-ttu-id="7a491-152">Ersetzt die entsprechenden Zeichenfolgen aus dem App-Manifest durch den hier angegebenen Wert.</span><span class="sxs-lookup"><span data-stu-id="7a491-152">Replaces the corresponding string(s) from the app manifest with the value provided here.</span></span>

## <a name="composeextensions0commands0-9taskinfotitle"></a><span data-ttu-id="7a491-153">composeExtensions \\ [0 \\ ] \\ .commands \\ [[0-9] \\ ] \\ .taskInfo \\ .title</span><span class="sxs-lookup"><span data-stu-id="7a491-153">composeExtensions\\[0\\]\\.commands\\[[0-9]\\]\\.taskInfo\\.title</span></span>

<span data-ttu-id="7a491-154">**Zeichenfolge, Max. Länge 64**</span><span class="sxs-lookup"><span data-stu-id="7a491-154">**String, Max Length 64**</span></span>

<span data-ttu-id="7a491-155">Ersetzt die entsprechenden Zeichenfolgen aus dem App-Manifest durch den hier angegebenen Wert.</span><span class="sxs-lookup"><span data-stu-id="7a491-155">Replaces the corresponding string(s) from the app manifest with the value provided here.</span></span>
