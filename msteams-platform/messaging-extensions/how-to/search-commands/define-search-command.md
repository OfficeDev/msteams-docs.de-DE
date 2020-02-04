---
title: Definieren von Suchbefehlen für die Messaging Erweiterung
author: clearab
description: Definieren von Suchbefehlen für die Messaging Erweiterung für Microsoft Teams-apps.
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: b6837fb8a131d8ce3e2bbd0c51c2861dbffda2bc
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674391"
---
# <a name="define-messaging-extension-search-commands"></a><span data-ttu-id="eb01c-103">Definieren von Suchbefehlen für die Messaging Erweiterung</span><span class="sxs-lookup"><span data-stu-id="eb01c-103">Define messaging extension search commands</span></span>

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

<span data-ttu-id="eb01c-104">Mit den Suchbefehlen für die Nachrichten Erweiterung können Benutzer externe Systeme durchsuchen und die Ergebnisse der Suche in eine Nachricht in Form einer Karte einfügen.</span><span class="sxs-lookup"><span data-stu-id="eb01c-104">Messaging extension search commands allow your users to search external systems and insert the results of that search into a message in the form of a card.</span></span>

## <a name="choose-messaging-extension-invoke-locations"></a><span data-ttu-id="eb01c-105">Auswählen von Speicherorten für Messaging Erweiterungs Aufrufe</span><span class="sxs-lookup"><span data-stu-id="eb01c-105">Choose messaging extension invoke locations</span></span>

<span data-ttu-id="eb01c-106">Das erste, was Sie entscheiden müssen, ist, wo Ihr Suchbefehl (oder genauer gesagt, *aufgerufen*) aus ausgelöst werden kann.</span><span class="sxs-lookup"><span data-stu-id="eb01c-106">The first thing you need to decide is where your search command can be triggered (or more specifically, *invoked*) from.</span></span> <span data-ttu-id="eb01c-107">Ihr Suchbefehl kann über einen oder beide der folgenden Speicherorte aufgerufen werden:</span><span class="sxs-lookup"><span data-stu-id="eb01c-107">Your search command can be invoked from one or both of the following locations:</span></span>

* <span data-ttu-id="eb01c-108">Die Schaltflächen am unteren Rand des Bereichs zum Verfassen von Nachrichten</span><span class="sxs-lookup"><span data-stu-id="eb01c-108">The buttons at the bottom of the compose message area</span></span>
* <span data-ttu-id="eb01c-109">Durch @mentioning im Befehlsfeld</span><span class="sxs-lookup"><span data-stu-id="eb01c-109">By @mentioning in the command box</span></span>

<span data-ttu-id="eb01c-110">Wenn der Benutzer im Bereich zum Verfassen von Nachrichten aufgerufen wird, hat er die Möglichkeit, die Ergebnisse an die Unterhaltung zu senden.</span><span class="sxs-lookup"><span data-stu-id="eb01c-110">When invoked from the compose message area, your user will have the option of sending the results to the conversation.</span></span> <span data-ttu-id="eb01c-111">Wenn der Benutzer über das Befehlsfeld aufgerufen wird, kann er mit der resultierenden Karte interagieren oder ihn zur Verwendung an einer anderen Stelle kopieren.</span><span class="sxs-lookup"><span data-stu-id="eb01c-111">When invoked from the command box, the user can interact with the resulting card, or copy it for use elsewhere.</span></span>

## <a name="add-the-command-to-your-app-manifest"></a><span data-ttu-id="eb01c-112">Hinzufügen des Befehls zum App-Manifest</span><span class="sxs-lookup"><span data-stu-id="eb01c-112">Add the command to your app manifest</span></span>

<span data-ttu-id="eb01c-113">Nachdem Sie sich entschieden haben, wie Benutzer mit Ihrem Suchbefehl interagieren sollen, ist es an der Zeit, Sie dem App-Manifest hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="eb01c-113">Now that you've decided how users will interact with your search command, it is time to add it to your app manifest.</span></span> <span data-ttu-id="eb01c-114">Zu diesem Zweck fügen Sie ein neues `composeExtension` Objekt zur obersten Ebene des JSON-App-Manifests hinzu.</span><span class="sxs-lookup"><span data-stu-id="eb01c-114">To do this you'll add a new `composeExtension` object to the top level of your app manifest JSON.</span></span> <span data-ttu-id="eb01c-115">Sie können dies entweder mit Hilfe von App Studio oder manuell tun.</span><span class="sxs-lookup"><span data-stu-id="eb01c-115">You can either do so with the help of App Studio, or manually.</span></span>

### <a name="create-a-command-using-app-studio"></a><span data-ttu-id="eb01c-116">Erstellen eines Befehls mit App Studio</span><span class="sxs-lookup"><span data-stu-id="eb01c-116">Create a command using App Studio</span></span>

<span data-ttu-id="eb01c-117">In den folgenden Schritten wird davon ausgegangen, dass Sie bereits [eine Messaging Erweiterung erstellt](~/messaging-extensions/how-to/create-messaging-extension.md)haben.</span><span class="sxs-lookup"><span data-stu-id="eb01c-117">The following steps assume you've already [created a messaging extension](~/messaging-extensions/how-to/create-messaging-extension.md).</span></span>

1. <span data-ttu-id="eb01c-118">Öffnen Sie auf dem Microsoft Teams-Client **App Studio** , und wählen Sie die Registerkarte **Manifest-Editor** aus.</span><span class="sxs-lookup"><span data-stu-id="eb01c-118">From the Microsoft Teams client, open **App Studio** and select the **Manifest Editor** tab.</span></span>
2. <span data-ttu-id="eb01c-119">Wenn Sie Ihr App-Paket bereits in App Studio erstellt haben, wählen Sie es aus der Liste aus.</span><span class="sxs-lookup"><span data-stu-id="eb01c-119">If you've already created your app package in App Studio, chose it from the list.</span></span> <span data-ttu-id="eb01c-120">Wenn dies nicht der Fall ist, können Sie ein vorhandenes App-Paket importieren.</span><span class="sxs-lookup"><span data-stu-id="eb01c-120">If not, you can import an existing app package.</span></span>
3. <span data-ttu-id="eb01c-121">Klicken Sie im Abschnitt Command auf die Schaltfläche **Hinzufügen** .</span><span class="sxs-lookup"><span data-stu-id="eb01c-121">Click the **Add** button in the Command section.</span></span>
4. <span data-ttu-id="eb01c-122">Wählen Sie **zulassen, dass Benutzer ihren Dienst nach Informationen Abfragen und diesen in eine Nachricht einfügen**.</span><span class="sxs-lookup"><span data-stu-id="eb01c-122">Choose **Allow users to query your service for information and insert that into a message**.</span></span>
5. <span data-ttu-id="eb01c-123">Fügen Sie eine **Befehls-ID** und einen **Titel**hinzu.</span><span class="sxs-lookup"><span data-stu-id="eb01c-123">Add a **Command Id** and a **Title**.</span></span>
6. <span data-ttu-id="eb01c-124">Wählen Sie aus, wo der Suchbefehl ausgelöst werden soll.</span><span class="sxs-lookup"><span data-stu-id="eb01c-124">Select where you want your search command to be triggered from.</span></span> <span data-ttu-id="eb01c-125">Das Auswählen von **Nachricht** ändert derzeit nicht das Verhalten des Suchbefehls.</span><span class="sxs-lookup"><span data-stu-id="eb01c-125">Selecting **message** does not currently alter the behavior of your search command.</span></span>
7. <span data-ttu-id="eb01c-126">Fügen Sie den Suchparameter hinzu.</span><span class="sxs-lookup"><span data-stu-id="eb01c-126">Add your search parameter.</span></span>
8. <span data-ttu-id="eb01c-127">Klicken Sie auf Speichern.</span><span class="sxs-lookup"><span data-stu-id="eb01c-127">Click Save.</span></span>

### <a name="manually-create-a-command"></a><span data-ttu-id="eb01c-128">Manuelles Erstellen eines Befehls</span><span class="sxs-lookup"><span data-stu-id="eb01c-128">Manually create a command</span></span>

<span data-ttu-id="eb01c-129">Um den Suchbefehl für die Messaging-Erweiterung manuell Ihrem App-Manifest hinzuzufügen, müssen Sie dem `composeExtension.commands` Array von Objekten die Parameter "folgt" hinzufügen.</span><span class="sxs-lookup"><span data-stu-id="eb01c-129">To manually add your messaging extension search command to your app manifest, you'll need to add the follow parameters to your `composeExtension.commands` array of objects.</span></span>

| <span data-ttu-id="eb01c-130">Eigenschaftenname</span><span class="sxs-lookup"><span data-stu-id="eb01c-130">Property name</span></span> | <span data-ttu-id="eb01c-131">Zweck</span><span class="sxs-lookup"><span data-stu-id="eb01c-131">Purpose</span></span> | <span data-ttu-id="eb01c-132">Pflichtfeld?</span><span class="sxs-lookup"><span data-stu-id="eb01c-132">Required?</span></span> | <span data-ttu-id="eb01c-133">Minimale Manifestversion</span><span class="sxs-lookup"><span data-stu-id="eb01c-133">Minimum manifest version</span></span> |
|---|---|---|---|
| `id` | <span data-ttu-id="eb01c-134">Eindeutige ID, die Sie diesem Befehl zuweisen.</span><span class="sxs-lookup"><span data-stu-id="eb01c-134">Unique ID that you assign to this command.</span></span> <span data-ttu-id="eb01c-135">Diese ID wird von der Benutzeranforderung eingeschlossen.</span><span class="sxs-lookup"><span data-stu-id="eb01c-135">The user request will include this ID.</span></span> | <span data-ttu-id="eb01c-136">Ja</span><span class="sxs-lookup"><span data-stu-id="eb01c-136">Yes</span></span> | <span data-ttu-id="eb01c-137">1.0</span><span class="sxs-lookup"><span data-stu-id="eb01c-137">1.0</span></span> |
| `title` | <span data-ttu-id="eb01c-138">Befehlsname.</span><span class="sxs-lookup"><span data-stu-id="eb01c-138">Command name.</span></span> <span data-ttu-id="eb01c-139">Dieser Wert wird auf der Benutzeroberfläche angezeigt.</span><span class="sxs-lookup"><span data-stu-id="eb01c-139">This value appears in the UI.</span></span> | <span data-ttu-id="eb01c-140">Ja</span><span class="sxs-lookup"><span data-stu-id="eb01c-140">Yes</span></span> | <span data-ttu-id="eb01c-141">1.0</span><span class="sxs-lookup"><span data-stu-id="eb01c-141">1.0</span></span> |
| `description` | <span data-ttu-id="eb01c-142">Hilfetext, der angibt, was dieser Befehl ausführt.</span><span class="sxs-lookup"><span data-stu-id="eb01c-142">Help text indicating what this command does.</span></span> <span data-ttu-id="eb01c-143">Dieser Wert wird auf der Benutzeroberfläche angezeigt.</span><span class="sxs-lookup"><span data-stu-id="eb01c-143">This value appears in the UI.</span></span> | <span data-ttu-id="eb01c-144">Ja</span><span class="sxs-lookup"><span data-stu-id="eb01c-144">Yes</span></span> | <span data-ttu-id="eb01c-145">1.0</span><span class="sxs-lookup"><span data-stu-id="eb01c-145">1.0</span></span> |
| `type` | <span data-ttu-id="eb01c-146">Muss `query` sein.</span><span class="sxs-lookup"><span data-stu-id="eb01c-146">Must be `query`</span></span> | <span data-ttu-id="eb01c-147">Nein</span><span class="sxs-lookup"><span data-stu-id="eb01c-147">No</span></span> | <span data-ttu-id="eb01c-148">1.4</span><span class="sxs-lookup"><span data-stu-id="eb01c-148">1.4</span></span> |
|`initialRun` | <span data-ttu-id="eb01c-149">Bei Festlegung auf " **true**" gibt an, dass dieser Befehl ausgeführt werden soll, sobald der Benutzer diesen Befehl auf der Benutzeroberfläche auswählt.</span><span class="sxs-lookup"><span data-stu-id="eb01c-149">If set to **true**, indicates this command should be executed as soon as the user chooses this command in the UI.</span></span> | <span data-ttu-id="eb01c-150">Nein</span><span class="sxs-lookup"><span data-stu-id="eb01c-150">No</span></span> | <span data-ttu-id="eb01c-151">1.0</span><span class="sxs-lookup"><span data-stu-id="eb01c-151">1.0</span></span> |
| `context` | <span data-ttu-id="eb01c-152">Optionales Array von Werten, das den Kontext definiert, in dem die Suchaktion verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="eb01c-152">Optional array of values that defines the context the search action is available in.</span></span> <span data-ttu-id="eb01c-153">Mögliche Werte sind `message`, `compose`oder `commandBox`.</span><span class="sxs-lookup"><span data-stu-id="eb01c-153">Possible values are `message`, `compose`, or `commandBox`.</span></span> <span data-ttu-id="eb01c-154">Der Standardwert lautet `["compose", "commandBox"]`.</span><span class="sxs-lookup"><span data-stu-id="eb01c-154">Default is `["compose", "commandBox"]`.</span></span> | <span data-ttu-id="eb01c-155">Nein</span><span class="sxs-lookup"><span data-stu-id="eb01c-155">No</span></span> | <span data-ttu-id="eb01c-156">1,5</span><span class="sxs-lookup"><span data-stu-id="eb01c-156">1.5</span></span> |

<span data-ttu-id="eb01c-157">Außerdem müssen Sie die Details des Such Parameters hinzufügen, mit dem der Text, der für den Benutzer sichtbar ist, im Microsoft Teams-Client definiert wird.</span><span class="sxs-lookup"><span data-stu-id="eb01c-157">You'll also need to add the details of the search parameter, which will define the text visible to your user in the Teams client.</span></span>

| <span data-ttu-id="eb01c-158">Eigenschaftenname</span><span class="sxs-lookup"><span data-stu-id="eb01c-158">Property name</span></span> | <span data-ttu-id="eb01c-159">Zweck</span><span class="sxs-lookup"><span data-stu-id="eb01c-159">Purpose</span></span> | <span data-ttu-id="eb01c-160">Pflichtfeld?</span><span class="sxs-lookup"><span data-stu-id="eb01c-160">Required?</span></span> | <span data-ttu-id="eb01c-161">Minimale Manifestversion</span><span class="sxs-lookup"><span data-stu-id="eb01c-161">Minimum manifest version</span></span> |
|---|---|---|---|
| `parameters` | <span data-ttu-id="eb01c-162">Statische Liste von Parametern für den Befehl.</span><span class="sxs-lookup"><span data-stu-id="eb01c-162">Static list of parameters for the command.</span></span> | <span data-ttu-id="eb01c-163">Nein</span><span class="sxs-lookup"><span data-stu-id="eb01c-163">No</span></span> | <span data-ttu-id="eb01c-164">1.0</span><span class="sxs-lookup"><span data-stu-id="eb01c-164">1.0</span></span> |
| `parameter.name` | <span data-ttu-id="eb01c-165">Der Name des Parameters.</span><span class="sxs-lookup"><span data-stu-id="eb01c-165">The name of the parameter.</span></span> <span data-ttu-id="eb01c-166">Dies wird in der Benutzeranforderung an Ihren Dienst gesendet.</span><span class="sxs-lookup"><span data-stu-id="eb01c-166">This is sent to your service in the user request.</span></span> | <span data-ttu-id="eb01c-167">Ja</span><span class="sxs-lookup"><span data-stu-id="eb01c-167">Yes</span></span> | <span data-ttu-id="eb01c-168">1.0</span><span class="sxs-lookup"><span data-stu-id="eb01c-168">1.0</span></span> |
| `parameter.description` | <span data-ttu-id="eb01c-169">Beschreibt den Zweck oder das Beispiel dieses Parameters des Werts, der angegeben werden sollte.</span><span class="sxs-lookup"><span data-stu-id="eb01c-169">Describes this parameter’s purposes or example of the value that should be provided.</span></span> <span data-ttu-id="eb01c-170">Dieser Wert wird auf der Benutzeroberfläche angezeigt.</span><span class="sxs-lookup"><span data-stu-id="eb01c-170">This value appears in the UI.</span></span> | <span data-ttu-id="eb01c-171">Ja</span><span class="sxs-lookup"><span data-stu-id="eb01c-171">Yes</span></span> | <span data-ttu-id="eb01c-172">1.0</span><span class="sxs-lookup"><span data-stu-id="eb01c-172">1.0</span></span> |
| `parameter.title` | <span data-ttu-id="eb01c-173">Kurzer benutzerfreundlicher Parameter Titel oder Bezeichnung.</span><span class="sxs-lookup"><span data-stu-id="eb01c-173">Short user-friendly parameter title or label.</span></span> | <span data-ttu-id="eb01c-174">Ja</span><span class="sxs-lookup"><span data-stu-id="eb01c-174">Yes</span></span> | <span data-ttu-id="eb01c-175">1.0</span><span class="sxs-lookup"><span data-stu-id="eb01c-175">1.0</span></span> |
| `parameter.inputType` | <span data-ttu-id="eb01c-176">Legt den Typ der erforderlichen Eingabe fest.</span><span class="sxs-lookup"><span data-stu-id="eb01c-176">Set to the type of input required.</span></span> <span data-ttu-id="eb01c-177">Mögliche Werte sind `text`: `textarea`, `number`, `date`, `time`, `toggle`,.</span><span class="sxs-lookup"><span data-stu-id="eb01c-177">Possible values include `text`, `textarea`, `number`, `date`, `time`, `toggle`.</span></span> <span data-ttu-id="eb01c-178">Default ist auf festgelegt`text`</span><span class="sxs-lookup"><span data-stu-id="eb01c-178">Default is set to `text`</span></span> | <span data-ttu-id="eb01c-179">Nein</span><span class="sxs-lookup"><span data-stu-id="eb01c-179">No</span></span> | <span data-ttu-id="eb01c-180">1.4</span><span class="sxs-lookup"><span data-stu-id="eb01c-180">1.4</span></span> |

#### <a name="app-manifest-example"></a><span data-ttu-id="eb01c-181">Beispiel für ein App-Manifest</span><span class="sxs-lookup"><span data-stu-id="eb01c-181">App manifest example</span></span>

<span data-ttu-id="eb01c-182">Im folgenden sehen Sie ein Beispiel für `composeExtensions` ein Objekt, das einen Suchbefehl definiert.</span><span class="sxs-lookup"><span data-stu-id="eb01c-182">The below is an example of a `composeExtensions` object defining a search command.</span></span> <span data-ttu-id="eb01c-183">Es ist kein Beispiel für das vollständige Manifest, für das vollständige App-Manifest-Schema Siehe: [App-Manifest-Schema](~/resources/schema/manifest-schema.md).</span><span class="sxs-lookup"><span data-stu-id="eb01c-183">It is not an example of the complete manifest, for the full app manifest schema see: [App manifest schema](~/resources/schema/manifest-schema.md).</span></span>

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

## <a name="next-steps"></a><span data-ttu-id="eb01c-184">Weitere Schritte</span><span class="sxs-lookup"><span data-stu-id="eb01c-184">Next steps</span></span>

<span data-ttu-id="eb01c-185">Nachdem Sie den Suchbefehl hinzugefügt haben, müssen Sie [die Suchanforderung verarbeiten](~/messaging-extensions/how-to/search-commands/respond-to-search.md).</span><span class="sxs-lookup"><span data-stu-id="eb01c-185">Now that you've added your search command, you'll need to [handle the search request](~/messaging-extensions/how-to/search-commands/respond-to-search.md).</span></span>

[!include[messaging-extension-learn-more](~/includes/messaging-extensions/learn-more.md)]