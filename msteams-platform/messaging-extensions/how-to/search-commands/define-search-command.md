---
title: Definieren von Befehlen für die Suche nach Nachrichtenerweiterungen
author: clearab
description: Definieren von Suchbefehlen für Messagingerweiterungen für Microsoft Teams Apps.
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: 19f1fdf7bd4efdbb0de11d1abad341ec24bc27bd
ms.sourcegitcommit: 79e6bccfb513d4c16a58ffc03521edcf134fa518
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/13/2021
ms.locfileid: "51696811"
---
# <a name="define-messaging-extension-search-commands"></a><span data-ttu-id="49d78-103">Definieren von Befehlen für die Suche nach Nachrichtenerweiterungen</span><span class="sxs-lookup"><span data-stu-id="49d78-103">Define messaging extension search commands</span></span>

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

<span data-ttu-id="49d78-104">Suchbefehle für Messagingerweiterungen ermöglichen Benutzern das Durchsuchen externer Systeme und das Einfügen der Ergebnisse dieser Suche in eine Nachricht in Form einer Karte.</span><span class="sxs-lookup"><span data-stu-id="49d78-104">Messaging extension search commands allow users to search external systems and insert the results of that search into a message in the form of a card.</span></span> <span data-ttu-id="49d78-105">In diesem Dokument erfahren Sie, wie Sie Suchbefehlsaufrufe auswählen und den Suchbefehl ihrem App-Manifest hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="49d78-105">This document guides you on how to select  search command invoke locations, and add the search command to your app manifest.</span></span>

> [!NOTE]
> <span data-ttu-id="49d78-106">Die Größenbeschränkung für die Karte beträgt 28 KB.</span><span class="sxs-lookup"><span data-stu-id="49d78-106">The result card size limit is 28 KB.</span></span> <span data-ttu-id="49d78-107">Die Karte wird nicht gesendet, wenn ihre Größe 28 KB überschreitet.</span><span class="sxs-lookup"><span data-stu-id="49d78-107">The card is not sent if its size exceeds 28 KB.</span></span>

## <a name="select-search-command-invoke-locations"></a><span data-ttu-id="49d78-108">Auswählen von Suchbefehlsaufrufen</span><span class="sxs-lookup"><span data-stu-id="49d78-108">Select search command invoke locations</span></span>

<span data-ttu-id="49d78-109">Der Suchbefehl wird von einem oder beiden der folgenden Speicherorte aufgerufen:</span><span class="sxs-lookup"><span data-stu-id="49d78-109">The search command is invoked from any one or both of the following locations:</span></span>

* <span data-ttu-id="49d78-110">Bereich "Nachricht verfassen": Die Schaltflächen am unteren Rand des Bereichs "Verfassen von Nachrichten".</span><span class="sxs-lookup"><span data-stu-id="49d78-110">Compose message area: The buttons at the bottom of the compose message area.</span></span>
* <span data-ttu-id="49d78-111">Befehlsfeld: Durch @mentioning im Befehlsfeld.</span><span class="sxs-lookup"><span data-stu-id="49d78-111">Command box: By @mentioning in the command box.</span></span>

<span data-ttu-id="49d78-112">Wenn der Suchbefehl aus dem Bereich zum Verfassen von Nachrichten aufgerufen wird, sendet der Benutzer die Ergebnisse an die Unterhaltung.</span><span class="sxs-lookup"><span data-stu-id="49d78-112">When search command is invoked from the compose message area, the user sends the results to the conversation.</span></span> <span data-ttu-id="49d78-113">Wenn sie über das Befehlsfeld aufgerufen wird, interagiert der Benutzer mit der resultierenden Karte oder kopiert sie zur Verwendung an anderer Stelle.</span><span class="sxs-lookup"><span data-stu-id="49d78-113">When it is invoked from the command box, the user interacts with the resulting card, or copies it for use elsewhere.</span></span>

<span data-ttu-id="49d78-114">In der folgenden Abbildung werden die Aufrufpositionen des Suchbefehls angezeigt:</span><span class="sxs-lookup"><span data-stu-id="49d78-114">The following image displays the invoke locations of the search command:</span></span>

![Suchbefehl ruft Speicherorte auf](~/assets/images/messaging-extension/search-command-invoke-locations.png)

## <a name="add-the-search-command-to-your-app-manifest"></a><span data-ttu-id="49d78-116">Hinzufügen des Suchbefehls zum App-Manifest</span><span class="sxs-lookup"><span data-stu-id="49d78-116">Add the search command to your app manifest</span></span>

<span data-ttu-id="49d78-117">Zum Hinzufügen des Suchbefehls zum App-Manifest müssen Sie der obersten Ebene ihres App-Manifest-JSON ein neues `composeExtension` Objekt hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="49d78-117">To add the search command to your app manifest, you must add a new `composeExtension` object to the top level of your app manifest JSON.</span></span> <span data-ttu-id="49d78-118">Sie können den Suchbefehl entweder mithilfe von App Studio oder manuell hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="49d78-118">You can add the search command either with the help of App Studio, or manually.</span></span>

### <a name="create-a-search-command-using-app-studio"></a><span data-ttu-id="49d78-119">Erstellen eines Suchbefehls mithilfe von App Studio</span><span class="sxs-lookup"><span data-stu-id="49d78-119">Create a search command using App Studio</span></span>

<span data-ttu-id="49d78-120">Voraussetzung für das Erstellen eines Suchbefehls ist, dass Sie bereits eine Messagingerweiterung erstellt haben müssen.</span><span class="sxs-lookup"><span data-stu-id="49d78-120">The prerequisite to create a search command is that you must already have created a messaging extension.</span></span> <span data-ttu-id="49d78-121">Informationen zum Erstellen einer Messagingerweiterung finden Sie unter [Create a messaging extension](~/messaging-extensions/how-to/create-messaging-extension.md).</span><span class="sxs-lookup"><span data-stu-id="49d78-121">For information on how to create a messaging extension, see [create a messaging extension](~/messaging-extensions/how-to/create-messaging-extension.md).</span></span>

<span data-ttu-id="49d78-122">**So erstellen Sie einen Suchbefehl**</span><span class="sxs-lookup"><span data-stu-id="49d78-122">**To create a search command**</span></span>

1. <span data-ttu-id="49d78-123">Öffnen **Sie App Studio** im Microsoft Teams Client, und wählen Sie die Registerkarte **Manifest-Editor** aus.</span><span class="sxs-lookup"><span data-stu-id="49d78-123">Open **App Studio** from the Microsoft Teams client, and select the **Manifest Editor** tab.</span></span>
1.  <span data-ttu-id="49d78-124">Wenn Sie Ihr App-Paket bereits in **App Studio erstellt haben,** wählen Sie aus der Liste aus.</span><span class="sxs-lookup"><span data-stu-id="49d78-124">If you already created your app package in **App Studio**, select from the list.</span></span> <span data-ttu-id="49d78-125">Wenn Sie kein App-Paket erstellt haben, importieren Sie ein vorhandenes.</span><span class="sxs-lookup"><span data-stu-id="49d78-125">If you have not created an app package, import an existing one.</span></span>
1. <span data-ttu-id="49d78-126">Wählen Sie nach dem Importieren des App-Pakets die Option **Messagingerweiterungen** unter **Funktionen aus.**</span><span class="sxs-lookup"><span data-stu-id="49d78-126">After importing app package, select **Messaging extensions** under **Capabilities**.</span></span> <span data-ttu-id="49d78-127">Sie erhalten ein Popupfenster zum Einrichten der Messagingerweiterung.</span><span class="sxs-lookup"><span data-stu-id="49d78-127">You get a pop-up window to set up the messaging extension.</span></span>
1. <span data-ttu-id="49d78-128">Wählen **Sie Einrichten** im Fenster aus, um die Messagingerweiterung in Ihre App-Umgebung zu verwenden.</span><span class="sxs-lookup"><span data-stu-id="49d78-128">Select **Set up** in the window to include the messaging extension in your app experience.</span></span> <span data-ttu-id="49d78-129">In der folgenden Abbildung wird die Seite zum Einrichten der Messagingerweiterung angezeigt:</span><span class="sxs-lookup"><span data-stu-id="49d78-129">The following image displays the messaging extension set up page:</span></span> 

    <img src="~/assets/images/messaging-extension/messaging-extension-set-up.png" alt="messaging extension set up" width="500"/>

1. <span data-ttu-id="49d78-130">Zum Erstellen der Messagingerweiterung benötigen Sie einen von Microsoft registrierten Bot.</span><span class="sxs-lookup"><span data-stu-id="49d78-130">To create the messaging extension, you need a Microsoft registered bot.</span></span> <span data-ttu-id="49d78-131">Sie können entweder einen vorhandenen Bot verwenden oder einen neuen Bot erstellen.</span><span class="sxs-lookup"><span data-stu-id="49d78-131">You can either use an existing bot or create a new bot.</span></span> <span data-ttu-id="49d78-132">Wählen **Sie Die Option Neuer Bot erstellen** aus, geben Sie einen Namen für den neuen Bot ein, und wählen Sie Erstellen **aus.**</span><span class="sxs-lookup"><span data-stu-id="49d78-132">Select **Create new bot** option, give a name for the new bot, and select **Create**.</span></span> <span data-ttu-id="49d78-133">In der folgenden Abbildung wird die Boterstellung für die Messagingerweiterung angezeigt:</span><span class="sxs-lookup"><span data-stu-id="49d78-133">The following image displays bot creation for messaging extension:</span></span>

    <img src="~/assets/images/messaging-extension/create-bot-for-messaging-extension.png" alt="create bot for messaging extension" width="500"/>

1. <span data-ttu-id="49d78-134">Wählen **Sie Im** Abschnitt Befehl **der** Seite Messagingerweiterungen die Option Hinzufügen aus, um die Befehle hinzuzufügen, die das Verhalten der Messagingerweiterung bestimmen.</span><span class="sxs-lookup"><span data-stu-id="49d78-134">Select **Add** in the **Command section** of the messaging extensions page to include the commands which decides the behaviour of messaging extension.</span></span>   
<span data-ttu-id="49d78-135">In der folgenden Abbildung wird die Befehlserweiterung für die Messagingerweiterung angezeigt:</span><span class="sxs-lookup"><span data-stu-id="49d78-135">The following image displays command addition for messaging extension:</span></span>

   <img src="~/assets/images/messaging-extension/include-command.png" alt="include command" width="500"/>
1. <span data-ttu-id="49d78-136">Wählen **Sie Benutzer zulassen aus, um Ihren Dienst nach Informationen zu fragen, und fügen Sie diese in eine Nachricht ein.**</span><span class="sxs-lookup"><span data-stu-id="49d78-136">Select **Allow users to query your service for information and insert that into a message**.</span></span> <span data-ttu-id="49d78-137">In der folgenden Abbildung wird die Auswahl des Suchbefehlsparameters angezeigt:</span><span class="sxs-lookup"><span data-stu-id="49d78-137">The following image displays the search command parameter selection:</span></span>

    <img src="~/assets/images/messaging-extension/search-command-parameter-selection.png" alt="search command parameter selection" width="500"/>

1. <span data-ttu-id="49d78-138">Fügen Sie **eine Befehls-ID** und einen **Titel hinzu.**</span><span class="sxs-lookup"><span data-stu-id="49d78-138">Add a **Command Id** and a **Title**.</span></span>
1. <span data-ttu-id="49d78-139">Wählen Sie den Speicherort aus, an dem der Suchbefehl aufgerufen werden muss.</span><span class="sxs-lookup"><span data-stu-id="49d78-139">Select the location from where your search command must be invoked.</span></span> <span data-ttu-id="49d78-140">Das **Auswählen der** Nachricht ändert derzeit nicht das Verhalten Ihres Suchbefehls.</span><span class="sxs-lookup"><span data-stu-id="49d78-140">Selecting **message** does not currently alter the behavior of your search command.</span></span> <span data-ttu-id="49d78-141">In der folgenden Abbildung wird der Speicherort des Suchbefehls angezeigt:</span><span class="sxs-lookup"><span data-stu-id="49d78-141">The following image displays the search command invoke location:</span></span>

    <img src="~/assets/images/messaging-extension/search-command-invoke-location-selection.png" alt="search command invoke location selection]" width="500"/>

1. <span data-ttu-id="49d78-142">Fügen Sie ihren Suchparameter hinzu, und wählen Sie **Speichern aus.**</span><span class="sxs-lookup"><span data-stu-id="49d78-142">Add your search parameter and select **Save**.</span></span>

### <a name="create-a-search-command-manually"></a><span data-ttu-id="49d78-143">Manuelles Erstellen eines Suchbefehls</span><span class="sxs-lookup"><span data-stu-id="49d78-143">Create a search command manually</span></span> 

<span data-ttu-id="49d78-144">Zum manuellen Hinzufügen des Suchbefehls für die Messagingerweiterung zu Ihrem App-Manifest müssen Sie dem Objektarray die folgenden `composeExtension.commands` Parameter hinzufügen:</span><span class="sxs-lookup"><span data-stu-id="49d78-144">To manually add your messaging extension search command to your app manifest, you must add the following parameters to your `composeExtension.commands` array of objects:</span></span>

| <span data-ttu-id="49d78-145">Eigenschaftenname</span><span class="sxs-lookup"><span data-stu-id="49d78-145">Property name</span></span> | <span data-ttu-id="49d78-146">Zweck</span><span class="sxs-lookup"><span data-stu-id="49d78-146">Purpose</span></span> | <span data-ttu-id="49d78-147">Pflichtfeld?</span><span class="sxs-lookup"><span data-stu-id="49d78-147">Required?</span></span> | <span data-ttu-id="49d78-148">Minimale Manifestversion</span><span class="sxs-lookup"><span data-stu-id="49d78-148">Minimum manifest version</span></span> |
|---|---|---|---|
| `id` | <span data-ttu-id="49d78-149">Diese Eigenschaft ist eine eindeutige ID, die Sie dem Suchbefehl zuweisen.</span><span class="sxs-lookup"><span data-stu-id="49d78-149">This property is an unique ID that you assign to search command.</span></span> <span data-ttu-id="49d78-150">Die Benutzeranforderung enthält diese ID.</span><span class="sxs-lookup"><span data-stu-id="49d78-150">The user request includes this ID.</span></span> | <span data-ttu-id="49d78-151">Ja</span><span class="sxs-lookup"><span data-stu-id="49d78-151">Yes</span></span> | <span data-ttu-id="49d78-152">1.0</span><span class="sxs-lookup"><span data-stu-id="49d78-152">1.0</span></span> |
| `title` | <span data-ttu-id="49d78-153">Diese Eigenschaft ist ein Befehlsname.</span><span class="sxs-lookup"><span data-stu-id="49d78-153">This property is a command name.</span></span> <span data-ttu-id="49d78-154">Dieser Wert wird auf der Benutzeroberfläche angezeigt.</span><span class="sxs-lookup"><span data-stu-id="49d78-154">This value appears in the user interface (UI).</span></span> | <span data-ttu-id="49d78-155">Ja</span><span class="sxs-lookup"><span data-stu-id="49d78-155">Yes</span></span> | <span data-ttu-id="49d78-156">1.0</span><span class="sxs-lookup"><span data-stu-id="49d78-156">1.0</span></span> |
| `description` | <span data-ttu-id="49d78-157">Diese Eigenschaft ist ein Hilfetext, der angibt, was dieser Befehl macht.</span><span class="sxs-lookup"><span data-stu-id="49d78-157">This property is a help text indicating what this command does.</span></span> <span data-ttu-id="49d78-158">Dieser Wert wird auf der Benutzeroberfläche angezeigt.</span><span class="sxs-lookup"><span data-stu-id="49d78-158">This value appears in the UI.</span></span> | <span data-ttu-id="49d78-159">Ja</span><span class="sxs-lookup"><span data-stu-id="49d78-159">Yes</span></span> | <span data-ttu-id="49d78-160">1.0</span><span class="sxs-lookup"><span data-stu-id="49d78-160">1.0</span></span> |
| `type` | <span data-ttu-id="49d78-161">Diese Eigenschaft muss eine `query` sein.</span><span class="sxs-lookup"><span data-stu-id="49d78-161">This property must be a `query`.</span></span> | <span data-ttu-id="49d78-162">Nein</span><span class="sxs-lookup"><span data-stu-id="49d78-162">No</span></span> | <span data-ttu-id="49d78-163">1.4</span><span class="sxs-lookup"><span data-stu-id="49d78-163">1.4</span></span> |
|`initialRun` | <span data-ttu-id="49d78-164">Wenn diese Eigenschaft auf **true** festgelegt ist, gibt sie an, dass dieser Befehl ausgeführt werden soll, sobald der Benutzer diesen Befehl auf der Benutzeroberfläche auswählt.</span><span class="sxs-lookup"><span data-stu-id="49d78-164">If this property is set to **true**, it indicates this command should be executed as soon as the user selects this command in the UI.</span></span> | <span data-ttu-id="49d78-165">Nein</span><span class="sxs-lookup"><span data-stu-id="49d78-165">No</span></span> | <span data-ttu-id="49d78-166">1.0</span><span class="sxs-lookup"><span data-stu-id="49d78-166">1.0</span></span> |
| `context` | <span data-ttu-id="49d78-167">Diese Eigenschaft ist ein optionales Array von Werten, das den Kontext definiert, in dem die Suchaktion verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="49d78-167">This property is an optional array of values that defines the context the search action is available in.</span></span> <span data-ttu-id="49d78-168">Die möglichen Werte sind `message`, `compose` oder `commandBox`.</span><span class="sxs-lookup"><span data-stu-id="49d78-168">The possible values are `message`, `compose`, or `commandBox`.</span></span> <span data-ttu-id="49d78-169">Der Standardwert lautet `["compose", "commandBox"]`.</span><span class="sxs-lookup"><span data-stu-id="49d78-169">The default is `["compose", "commandBox"]`.</span></span> | <span data-ttu-id="49d78-170">Nein</span><span class="sxs-lookup"><span data-stu-id="49d78-170">No</span></span> | <span data-ttu-id="49d78-171">1,5</span><span class="sxs-lookup"><span data-stu-id="49d78-171">1.5</span></span> |

<span data-ttu-id="49d78-172">Sie müssen die Details des Suchparameters hinzufügen, der den text definiert, der für Den Benutzer im Client Teams wird.</span><span class="sxs-lookup"><span data-stu-id="49d78-172">You must add the details of the search parameter, that defines the text visible to your user in the Teams client.</span></span>

| <span data-ttu-id="49d78-173">Eigenschaftenname</span><span class="sxs-lookup"><span data-stu-id="49d78-173">Property name</span></span> | <span data-ttu-id="49d78-174">Zweck</span><span class="sxs-lookup"><span data-stu-id="49d78-174">Purpose</span></span> | <span data-ttu-id="49d78-175">Ist erforderlich?</span><span class="sxs-lookup"><span data-stu-id="49d78-175">Is required?</span></span> | <span data-ttu-id="49d78-176">Minimale Manifestversion</span><span class="sxs-lookup"><span data-stu-id="49d78-176">Minimum manifest version</span></span> |
|---|---|---|---|
| `parameters` | <span data-ttu-id="49d78-177">Diese Eigenschaft definiert eine statische Liste von Parametern für den Befehl.</span><span class="sxs-lookup"><span data-stu-id="49d78-177">This property defines a static list of parameters for the command.</span></span> | <span data-ttu-id="49d78-178">Nein</span><span class="sxs-lookup"><span data-stu-id="49d78-178">No</span></span> | <span data-ttu-id="49d78-179">1.0</span><span class="sxs-lookup"><span data-stu-id="49d78-179">1.0</span></span> |
| `parameter.name` | <span data-ttu-id="49d78-180">Diese Eigenschaft beschreibt den Namen des Parameters.</span><span class="sxs-lookup"><span data-stu-id="49d78-180">This property describes the name of the parameter.</span></span> <span data-ttu-id="49d78-181">Dies wird in der Benutzeranforderung an Ihren Dienst gesendet.</span><span class="sxs-lookup"><span data-stu-id="49d78-181">This is sent to your service in the user request.</span></span> | <span data-ttu-id="49d78-182">Ja</span><span class="sxs-lookup"><span data-stu-id="49d78-182">Yes</span></span> | <span data-ttu-id="49d78-183">1.0</span><span class="sxs-lookup"><span data-stu-id="49d78-183">1.0</span></span> |
| `parameter.description` | <span data-ttu-id="49d78-184">Diese Eigenschaft beschreibt die Zwecke oder das Beispiel des Parameters, der angegeben werden muss.</span><span class="sxs-lookup"><span data-stu-id="49d78-184">This property describes the parameter’s purposes or example of the value that must be provided.</span></span> <span data-ttu-id="49d78-185">Dieser Wert wird auf der Benutzeroberfläche angezeigt.</span><span class="sxs-lookup"><span data-stu-id="49d78-185">This value appears in the UI.</span></span> | <span data-ttu-id="49d78-186">Ja</span><span class="sxs-lookup"><span data-stu-id="49d78-186">Yes</span></span> | <span data-ttu-id="49d78-187">1.0</span><span class="sxs-lookup"><span data-stu-id="49d78-187">1.0</span></span> |
| `parameter.title` | <span data-ttu-id="49d78-188">Diese Eigenschaft ist ein kurzer benutzerfreundlicher Parametertitel oder eine bezeichnung.</span><span class="sxs-lookup"><span data-stu-id="49d78-188">This property is a short user-friendly parameter title or label.</span></span> | <span data-ttu-id="49d78-189">Ja</span><span class="sxs-lookup"><span data-stu-id="49d78-189">Yes</span></span> | <span data-ttu-id="49d78-190">1.0</span><span class="sxs-lookup"><span data-stu-id="49d78-190">1.0</span></span> |
| `parameter.inputType` | <span data-ttu-id="49d78-191">Diese Eigenschaft wird auf den Typ der erforderlichen Eingabe festgelegt.</span><span class="sxs-lookup"><span data-stu-id="49d78-191">This property is set to the type of the input required.</span></span> <span data-ttu-id="49d78-192">Mögliche Werte sind `text` , , , , `textarea` `number` `date` `time` `toggle` .</span><span class="sxs-lookup"><span data-stu-id="49d78-192">Possible values include `text`, `textarea`, `number`, `date`, `time`, `toggle`.</span></span> <span data-ttu-id="49d78-193">Der Standardwert ist auf `text` festgelegt.</span><span class="sxs-lookup"><span data-stu-id="49d78-193">Default is set to `text`.</span></span> | <span data-ttu-id="49d78-194">Nein</span><span class="sxs-lookup"><span data-stu-id="49d78-194">No</span></span> | <span data-ttu-id="49d78-195">1.4</span><span class="sxs-lookup"><span data-stu-id="49d78-195">1.4</span></span> |

#### <a name="example"></a><span data-ttu-id="49d78-196">Beispiel</span><span class="sxs-lookup"><span data-stu-id="49d78-196">Example</span></span>

<span data-ttu-id="49d78-197">Der folgende Abschnitt ist ein Beispiel für das einfache App-Manifest des `composeExtensions` Objekts, das einen Suchbefehl definiert:</span><span class="sxs-lookup"><span data-stu-id="49d78-197">Following section is an example of the simple app manifest of the `composeExtensions` object defining a search command:</span></span> 

```json
{
...
  "composeExtensions": [
    {
      "botId": "57a3c29f-1fc5-4d97-a142-35bb662b7b23",
      "canUpdateConfiguration": true,
      "commands": [{
          "id": "searchCmd",
          "description": "Search Bing for information on the web",
          "title": "Search",
          "initialRun": true,
          "parameters": [{
            "name": "searchKeyword",
            "description": "Enter your search keywords",
            "title": "Keywords"
          }]
        }
      ]
    }
  ],
...
}
```
<span data-ttu-id="49d78-198">Das vollständige App-Manifest finden Sie unter [App-Manifestschema](~/resources/schema/manifest-schema.md).</span><span class="sxs-lookup"><span data-stu-id="49d78-198">For the complete app manifest, see [App manifest schema](~/resources/schema/manifest-schema.md).</span></span>

## <a name="code-sample"></a><span data-ttu-id="49d78-199">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="49d78-199">Code sample</span></span>

| <span data-ttu-id="49d78-200">Beispielname</span><span class="sxs-lookup"><span data-stu-id="49d78-200">Sample Name</span></span>           | <span data-ttu-id="49d78-201">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="49d78-201">Description</span></span> | <span data-ttu-id="49d78-202">.NET</span><span class="sxs-lookup"><span data-stu-id="49d78-202">.NET</span></span>    | <span data-ttu-id="49d78-203">Node.js</span><span class="sxs-lookup"><span data-stu-id="49d78-203">Node.js</span></span>   |   
|:---------------------|:--------------|:---------|:--------|
|<span data-ttu-id="49d78-204">Teams Messagingerweiterungsaktion</span><span class="sxs-lookup"><span data-stu-id="49d78-204">Teams messaging extension action</span></span>| <span data-ttu-id="49d78-205">Beschreibt, wie Sie Aktionsbefehle definieren, Aufgabenmodul erstellen und auf Die Absendenaktion des Aufgabenmoduls reagieren.</span><span class="sxs-lookup"><span data-stu-id="49d78-205">Describes how to define action commands, create task module, and  respond to task module submit action.</span></span> |[<span data-ttu-id="49d78-206">View</span><span class="sxs-lookup"><span data-stu-id="49d78-206">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/51.teams-messaging-extensions-action)|[<span data-ttu-id="49d78-207">View</span><span class="sxs-lookup"><span data-stu-id="49d78-207">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/51.teams-messaging-extensions-action) | 
|<span data-ttu-id="49d78-208">Teams messaging extension search</span><span class="sxs-lookup"><span data-stu-id="49d78-208">Teams messaging extension search</span></span>   |  <span data-ttu-id="49d78-209">Beschreibt, wie Sie Suchbefehle definieren und auf Suchbefehle reagieren.</span><span class="sxs-lookup"><span data-stu-id="49d78-209">Describes how to define search commands and respond to searches.</span></span>        |[<span data-ttu-id="49d78-210">View</span><span class="sxs-lookup"><span data-stu-id="49d78-210">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/50.teams-messaging-extensions-search)|[<span data-ttu-id="49d78-211">View</span><span class="sxs-lookup"><span data-stu-id="49d78-211">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/50.teams-messaging-extensions-search)|

## <a name="next-step"></a><span data-ttu-id="49d78-212">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="49d78-212">Next step</span></span>

> [!div class="nextstepaction"]
> <span data-ttu-id="49d78-213">[Reagieren Sie auf die Suchbefehle](~/messaging-extensions/how-to/search-commands/respond-to-search.md).</span><span class="sxs-lookup"><span data-stu-id="49d78-213">[Respond to the search commands](~/messaging-extensions/how-to/search-commands/respond-to-search.md).</span></span>

