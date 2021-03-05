---
title: Definieren von Befehlen für die Suche nach Nachrichtenerweiterungen
author: clearab
description: Definieren von Befehlen für die Suche nach Nachrichtenerweiterungen für Microsoft Teams-Apps.
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: 18bac3049fec8fead168c12f2832bfbbb72cf609
ms.sourcegitcommit: 5cb3453e918bec1173899e7591b48a48113cf8f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/04/2021
ms.locfileid: "50449269"
---
# <a name="define-messaging-extension-search-commands"></a><span data-ttu-id="84beb-103">Definieren von Befehlen für die Suche nach Nachrichtenerweiterungen</span><span class="sxs-lookup"><span data-stu-id="84beb-103">Define messaging extension search commands</span></span>

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

<span data-ttu-id="84beb-104">Mit der Messaging-Erweiterung von Suchbefehlen können Ihre Benutzer externe Systeme durchsuchen und die Ergebnisse dieser Suche in Form einer Karte in eine Nachricht einfügen.</span><span class="sxs-lookup"><span data-stu-id="84beb-104">Messaging extension search commands allow your users to search external systems and insert the results of that search into a message in the form of a card.</span></span>

> [!NOTE]
> <span data-ttu-id="84beb-105">Die Größenbeschränkung für die Karte beträgt 28 KB.</span><span class="sxs-lookup"><span data-stu-id="84beb-105">The result card size limit is 28 KB.</span></span> <span data-ttu-id="84beb-106">Die Karte wird nicht gesendet, wenn ihre Größe 28 KB überschreitet.</span><span class="sxs-lookup"><span data-stu-id="84beb-106">The card is not sent if its size exceeds 28 KB.</span></span> 

## <a name="choose-messaging-extension-invoke-locations"></a><span data-ttu-id="84beb-107">Auswählen von Speicherorten für den Aufruf von Messagingerweiterungen</span><span class="sxs-lookup"><span data-stu-id="84beb-107">Choose messaging extension invoke locations</span></span>

<span data-ttu-id="84beb-108">Als Erstes müssen Sie entscheiden, von wo ihr Suchbefehl ausgelöst (oder speziell *aufgerufen)* werden kann.</span><span class="sxs-lookup"><span data-stu-id="84beb-108">The first thing you need to decide is where your search command can be triggered (or specifically, *invoked*) from.</span></span> <span data-ttu-id="84beb-109">Der Suchbefehl kann von einem oder beiden der folgenden Speicherorte aufgerufen werden:</span><span class="sxs-lookup"><span data-stu-id="84beb-109">Your search command can be invoked from one or both of the following locations:</span></span>

* <span data-ttu-id="84beb-110">Die Schaltflächen am unteren Rand des Nachrichten verfassenbereichs</span><span class="sxs-lookup"><span data-stu-id="84beb-110">The buttons at the bottom of the compose message area</span></span>
* <span data-ttu-id="84beb-111">By @mentioning in the command box</span><span class="sxs-lookup"><span data-stu-id="84beb-111">By @mentioning in the command box</span></span>

<span data-ttu-id="84beb-112">Wenn sie aus dem Bereich zum Verfassen von Nachrichten aufgerufen werden, hat der Benutzer die Möglichkeit, die Ergebnisse an die Unterhaltung zu senden.</span><span class="sxs-lookup"><span data-stu-id="84beb-112">When invoked from the compose message area, your user will have the option of sending the results to the conversation.</span></span> <span data-ttu-id="84beb-113">Wenn er über das Befehlsfeld aufgerufen wird, kann der Benutzer mit der resultierenden Karte interagieren oder sie zur Verwendung an anderer Stelle kopieren.</span><span class="sxs-lookup"><span data-stu-id="84beb-113">When invoked from the command box, the user can interact with the resulting card, or copy it for use elsewhere.</span></span>

## <a name="add-the-command-to-your-app-manifest"></a><span data-ttu-id="84beb-114">Hinzufügen des Befehls zum App-Manifest</span><span class="sxs-lookup"><span data-stu-id="84beb-114">Add the command to your app manifest</span></span>

<span data-ttu-id="84beb-115">Nachdem Sie nun entschieden haben, wie Benutzer mit Ihrem Suchbefehl interagieren, ist es an der Zeit, ihn ihrem App-Manifest hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="84beb-115">Now that you've decided how users will interact with your search command, it is time to add it to your app manifest.</span></span> <span data-ttu-id="84beb-116">Dazu fügen Sie der obersten Ebene Ihres App-Manifest-JSON ein neues `composeExtension` Objekt hinzu.</span><span class="sxs-lookup"><span data-stu-id="84beb-116">To do this you'll add a new `composeExtension` object to the top level of your app manifest JSON.</span></span> <span data-ttu-id="84beb-117">Sie können dies entweder mithilfe von App Studio oder manuell tun.</span><span class="sxs-lookup"><span data-stu-id="84beb-117">You can either do so with the help of App Studio, or manually.</span></span>

### <a name="create-a-command-using-app-studio"></a><span data-ttu-id="84beb-118">Erstellen eines Befehls mithilfe von App Studio</span><span class="sxs-lookup"><span data-stu-id="84beb-118">Create a command using App Studio</span></span>

<span data-ttu-id="84beb-119">Voraussetzung für das Erstellen eines Suchbefehls ist, dass Sie bereits eine Messagingerweiterung erstellen müssen.</span><span class="sxs-lookup"><span data-stu-id="84beb-119">The prerequisite to create a search command is that you must already create a messaging extension.</span></span> <span data-ttu-id="84beb-120">Informationen zum Erstellen einer Messagingerweiterung finden Sie unter [Create a messaging extension](~/messaging-extensions/how-to/create-messaging-extension.md).</span><span class="sxs-lookup"><span data-stu-id="84beb-120">For information on how to create a messaging extension, see [create a messaging extension](~/messaging-extensions/how-to/create-messaging-extension.md).</span></span>

<span data-ttu-id="84beb-121">**So erstellen Sie einen Suchbefehl**</span><span class="sxs-lookup"><span data-stu-id="84beb-121">**To create a search command**</span></span>

1. <span data-ttu-id="84beb-122">Öffnen Sie im Microsoft Teams-Client **App Studio,** und wählen Sie die **Registerkarte Manifest-Editor** aus.</span><span class="sxs-lookup"><span data-stu-id="84beb-122">From the Microsoft Teams client, open **App Studio**, and select the **Manifest editor** tab.</span></span>
1. <span data-ttu-id="84beb-123">Wenn Sie bereits ein App-Paket im App Studio erstellt **haben,** wählen Sie es aus der Liste aus.</span><span class="sxs-lookup"><span data-stu-id="84beb-123">If you already created an app package in the **App Studio**, choose it from the list.</span></span> <span data-ttu-id="84beb-124">Wenn Sie kein App-Paket erstellt haben, importieren Sie ein vorhandenes.</span><span class="sxs-lookup"><span data-stu-id="84beb-124">If you have not created an app package, import an existing one.</span></span>
1. <span data-ttu-id="84beb-125">Wählen Sie nach dem Importieren eines App-Pakets unter Funktionen die Option **Messagingerweiterungen** **aus.**</span><span class="sxs-lookup"><span data-stu-id="84beb-125">After importing an app package, select **Messaging extensions** under **Capabilities**.</span></span>
1. <span data-ttu-id="84beb-126">Wählen **Sie im** Abschnitt **Befehl** auf der Seite Messagingerweiterungen hinzufügen aus.</span><span class="sxs-lookup"><span data-stu-id="84beb-126">Select **Add** in the **Command** section in the messaging extensions page.</span></span>
1. <span data-ttu-id="84beb-127">Wählen **Sie Benutzer zulassen, um Ihren Dienst nach Informationen zu fragen und diese in eine Nachricht ein.**</span><span class="sxs-lookup"><span data-stu-id="84beb-127">Choose **Allow users to query your service for information and insert that into a message**.</span></span>
1. <span data-ttu-id="84beb-128">Fügen Sie **eine Befehls-ID** und einen **Titel hinzu.**</span><span class="sxs-lookup"><span data-stu-id="84beb-128">Add a **Command Id** and a **Title**.</span></span>
1. <span data-ttu-id="84beb-129">Wählen Sie den Speicherort aus, an dem der Suchbefehl ausgelöst werden muss.</span><span class="sxs-lookup"><span data-stu-id="84beb-129">Select the location from where your search command must be triggered.</span></span> <span data-ttu-id="84beb-130">Das **Auswählen der** Nachricht ändert derzeit nicht das Verhalten Ihres Suchbefehls.</span><span class="sxs-lookup"><span data-stu-id="84beb-130">Selecting **message** does not currently alter the behavior of your search command.</span></span>
1. <span data-ttu-id="84beb-131">Fügen Sie ihren Suchparameter hinzu, und wählen Sie **Speichern aus.**</span><span class="sxs-lookup"><span data-stu-id="84beb-131">Add your search parameter and select **Save**.</span></span>
 
### <a name="manually-create-a-command"></a><span data-ttu-id="84beb-132">Manuelles Erstellen eines Befehls</span><span class="sxs-lookup"><span data-stu-id="84beb-132">Manually create a command</span></span>

<span data-ttu-id="84beb-133">Zum manuellen Hinzufügen des Suchbefehls für die Messagingerweiterung zum App-Manifest müssen Sie dem Array der Objekte die folgenden `composeExtension.commands` Parameter hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="84beb-133">To manually add your messaging extension search command to your app manifest, you'll need to add the following parameters to your `composeExtension.commands` array of objects.</span></span>

| <span data-ttu-id="84beb-134">Eigenschaftenname</span><span class="sxs-lookup"><span data-stu-id="84beb-134">Property name</span></span> | <span data-ttu-id="84beb-135">Zweck</span><span class="sxs-lookup"><span data-stu-id="84beb-135">Purpose</span></span> | <span data-ttu-id="84beb-136">Pflichtfeld?</span><span class="sxs-lookup"><span data-stu-id="84beb-136">Required?</span></span> | <span data-ttu-id="84beb-137">Minimale Manifestversion</span><span class="sxs-lookup"><span data-stu-id="84beb-137">Minimum manifest version</span></span> |
|---|---|---|---|
| `id` | <span data-ttu-id="84beb-138">Eindeutige ID, die Sie diesem Befehl zuweisen.</span><span class="sxs-lookup"><span data-stu-id="84beb-138">Unique ID that you assign to this command.</span></span> <span data-ttu-id="84beb-139">Die Benutzeranforderung enthält diese ID.</span><span class="sxs-lookup"><span data-stu-id="84beb-139">The user request will include this ID.</span></span> | <span data-ttu-id="84beb-140">Ja</span><span class="sxs-lookup"><span data-stu-id="84beb-140">Yes</span></span> | <span data-ttu-id="84beb-141">1.0</span><span class="sxs-lookup"><span data-stu-id="84beb-141">1.0</span></span> |
| `title` | <span data-ttu-id="84beb-142">Befehlsname.</span><span class="sxs-lookup"><span data-stu-id="84beb-142">Command name.</span></span> <span data-ttu-id="84beb-143">Dieser Wert wird auf der Benutzeroberfläche angezeigt.</span><span class="sxs-lookup"><span data-stu-id="84beb-143">This value appears in the UI.</span></span> | <span data-ttu-id="84beb-144">Ja</span><span class="sxs-lookup"><span data-stu-id="84beb-144">Yes</span></span> | <span data-ttu-id="84beb-145">1.0</span><span class="sxs-lookup"><span data-stu-id="84beb-145">1.0</span></span> |
| `description` | <span data-ttu-id="84beb-146">Hilfetext, der angibt, was dieser Befehl macht.</span><span class="sxs-lookup"><span data-stu-id="84beb-146">Help text indicating what this command does.</span></span> <span data-ttu-id="84beb-147">Dieser Wert wird auf der Benutzeroberfläche angezeigt.</span><span class="sxs-lookup"><span data-stu-id="84beb-147">This value appears in the UI.</span></span> | <span data-ttu-id="84beb-148">Ja</span><span class="sxs-lookup"><span data-stu-id="84beb-148">Yes</span></span> | <span data-ttu-id="84beb-149">1.0</span><span class="sxs-lookup"><span data-stu-id="84beb-149">1.0</span></span> |
| `type` | <span data-ttu-id="84beb-150">Muss `query` sein.</span><span class="sxs-lookup"><span data-stu-id="84beb-150">Must be `query`</span></span> | <span data-ttu-id="84beb-151">Nein</span><span class="sxs-lookup"><span data-stu-id="84beb-151">No</span></span> | <span data-ttu-id="84beb-152">1.4</span><span class="sxs-lookup"><span data-stu-id="84beb-152">1.4</span></span> |
|`initialRun` | <span data-ttu-id="84beb-153">Wenn dieser Wert **auf true** festgelegt ist, wird angegeben, dass dieser Befehl ausgeführt werden soll, sobald der Benutzer diesen Befehl auf der Benutzeroberfläche ausgibt.</span><span class="sxs-lookup"><span data-stu-id="84beb-153">If set to **true**, indicates this command should be executed as soon as the user chooses this command in the UI.</span></span> | <span data-ttu-id="84beb-154">Nein</span><span class="sxs-lookup"><span data-stu-id="84beb-154">No</span></span> | <span data-ttu-id="84beb-155">1.0</span><span class="sxs-lookup"><span data-stu-id="84beb-155">1.0</span></span> |
| `context` | <span data-ttu-id="84beb-156">Optionales Array von Werten, das den Kontext definiert, in dem die Suchaktion verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="84beb-156">Optional array of values that defines the context the search action is available in.</span></span> <span data-ttu-id="84beb-157">Mögliche Werte sind `message` , `compose` oder `commandBox` .</span><span class="sxs-lookup"><span data-stu-id="84beb-157">Possible values are `message`, `compose`, or `commandBox`.</span></span> <span data-ttu-id="84beb-158">Der Standardwert ist `["compose", "commandBox"]`.</span><span class="sxs-lookup"><span data-stu-id="84beb-158">Default is `["compose", "commandBox"]`.</span></span> | <span data-ttu-id="84beb-159">Nein</span><span class="sxs-lookup"><span data-stu-id="84beb-159">No</span></span> | <span data-ttu-id="84beb-160">1,5</span><span class="sxs-lookup"><span data-stu-id="84beb-160">1.5</span></span> |

<span data-ttu-id="84beb-161">Sie müssen auch die Details des Suchparameters hinzufügen, der den Text definiert, der für Den Benutzer im Teams-Client sichtbar ist.</span><span class="sxs-lookup"><span data-stu-id="84beb-161">You'll also need to add the details of the search parameter, which will define the text visible to your user in the Teams client.</span></span>

| <span data-ttu-id="84beb-162">Eigenschaftenname</span><span class="sxs-lookup"><span data-stu-id="84beb-162">Property name</span></span> | <span data-ttu-id="84beb-163">Zweck</span><span class="sxs-lookup"><span data-stu-id="84beb-163">Purpose</span></span> | <span data-ttu-id="84beb-164">Pflichtfeld?</span><span class="sxs-lookup"><span data-stu-id="84beb-164">Required?</span></span> | <span data-ttu-id="84beb-165">Minimale Manifestversion</span><span class="sxs-lookup"><span data-stu-id="84beb-165">Minimum manifest version</span></span> |
|---|---|---|---|
| `parameters` | <span data-ttu-id="84beb-166">Statische Liste der Parameter für den Befehl.</span><span class="sxs-lookup"><span data-stu-id="84beb-166">Static list of parameters for the command.</span></span> | <span data-ttu-id="84beb-167">Nein</span><span class="sxs-lookup"><span data-stu-id="84beb-167">No</span></span> | <span data-ttu-id="84beb-168">1.0</span><span class="sxs-lookup"><span data-stu-id="84beb-168">1.0</span></span> |
| `parameter.name` | <span data-ttu-id="84beb-169">Der Name des Parameters.</span><span class="sxs-lookup"><span data-stu-id="84beb-169">The name of the parameter.</span></span> <span data-ttu-id="84beb-170">Dies wird in der Benutzeranforderung an Ihren Dienst gesendet.</span><span class="sxs-lookup"><span data-stu-id="84beb-170">This is sent to your service in the user request.</span></span> | <span data-ttu-id="84beb-171">Ja</span><span class="sxs-lookup"><span data-stu-id="84beb-171">Yes</span></span> | <span data-ttu-id="84beb-172">1.0</span><span class="sxs-lookup"><span data-stu-id="84beb-172">1.0</span></span> |
| `parameter.description` | <span data-ttu-id="84beb-173">Beschreibt die Zwecke oder das Beispiel dieses Parameters für den wert, der bereitgestellt werden soll.</span><span class="sxs-lookup"><span data-stu-id="84beb-173">Describes this parameter’s purposes or example of the value that should be provided.</span></span> <span data-ttu-id="84beb-174">Dieser Wert wird auf der Benutzeroberfläche angezeigt.</span><span class="sxs-lookup"><span data-stu-id="84beb-174">This value appears in the UI.</span></span> | <span data-ttu-id="84beb-175">Ja</span><span class="sxs-lookup"><span data-stu-id="84beb-175">Yes</span></span> | <span data-ttu-id="84beb-176">1.0</span><span class="sxs-lookup"><span data-stu-id="84beb-176">1.0</span></span> |
| `parameter.title` | <span data-ttu-id="84beb-177">Kurze benutzerfreundlicher Parametertitel oder -bezeichnung.</span><span class="sxs-lookup"><span data-stu-id="84beb-177">Short user-friendly parameter title or label.</span></span> | <span data-ttu-id="84beb-178">Ja</span><span class="sxs-lookup"><span data-stu-id="84beb-178">Yes</span></span> | <span data-ttu-id="84beb-179">1.0</span><span class="sxs-lookup"><span data-stu-id="84beb-179">1.0</span></span> |
| `parameter.inputType` | <span data-ttu-id="84beb-180">Auf den typ der erforderlichen Eingabe festgelegt.</span><span class="sxs-lookup"><span data-stu-id="84beb-180">Set to the type of input required.</span></span> <span data-ttu-id="84beb-181">Mögliche Werte sind `text` , , , , `textarea` `number` `date` `time` `toggle` .</span><span class="sxs-lookup"><span data-stu-id="84beb-181">Possible values include `text`, `textarea`, `number`, `date`, `time`, `toggle`.</span></span> <span data-ttu-id="84beb-182">Standard ist auf festgelegt `text`</span><span class="sxs-lookup"><span data-stu-id="84beb-182">Default is set to `text`</span></span> | <span data-ttu-id="84beb-183">Nein</span><span class="sxs-lookup"><span data-stu-id="84beb-183">No</span></span> | <span data-ttu-id="84beb-184">1.4</span><span class="sxs-lookup"><span data-stu-id="84beb-184">1.4</span></span> |

#### <a name="app-manifest-example"></a><span data-ttu-id="84beb-185">Beispiel für ein App-Manifest</span><span class="sxs-lookup"><span data-stu-id="84beb-185">App manifest example</span></span>

<span data-ttu-id="84beb-186">Im Folgenden finden Sie ein Beispiel für ein `composeExtensions` Objekt, das einen Suchbefehl definiert.</span><span class="sxs-lookup"><span data-stu-id="84beb-186">Below is an example of a `composeExtensions` object defining a search command.</span></span> <span data-ttu-id="84beb-187">Es ist kein Beispiel für das vollständige Manifest, für das vollständige App-Manifestschema siehe: [App-Manifestschema](~/resources/schema/manifest-schema.md).</span><span class="sxs-lookup"><span data-stu-id="84beb-187">It is not an example of the complete manifest, for the full app manifest schema see: [App manifest schema](~/resources/schema/manifest-schema.md).</span></span>

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

## <a name="next-steps"></a><span data-ttu-id="84beb-188">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="84beb-188">Next steps</span></span>

<span data-ttu-id="84beb-189">Nachdem Sie den Suchbefehl hinzugefügt haben, müssen Sie die [Suchanforderung behandeln.](~/messaging-extensions/how-to/search-commands/respond-to-search.md)</span><span class="sxs-lookup"><span data-stu-id="84beb-189">Now that you've added your search command, you'll need to [handle the search request](~/messaging-extensions/how-to/search-commands/respond-to-search.md).</span></span>

[!include[messaging-extension-learn-more](~/includes/messaging-extensions/learn-more.md)]
