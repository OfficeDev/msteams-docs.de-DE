---
title: Senden von Nachrichten an Connectors und Webhooks
description: Beschreibt die Verwendung von Office 365-Connectors in Microsoft Teams
localization_priority: Priority
keywords: Teams O365-Connector
ms.openlocfilehash: bfcee2c00d30517522621f61142324b4f81a93f8
ms.sourcegitcommit: f9a2f5cedc9d30ef7a9cf78a47d01cfd277e150d
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 09/23/2020
ms.locfileid: "48237965"
---
# <a name="sending-messages-to-connectors-and-webhooks"></a><span data-ttu-id="9f9f4-104">Senden von Nachrichten an Connectors und Webhooks</span><span class="sxs-lookup"><span data-stu-id="9f9f4-104">Sending messages to connectors and webhooks</span></span>

<span data-ttu-id="9f9f4-105">Wenn Sie eine Nachricht über Ihren Office 365-Connector oder eingehenden Webhook senden möchten, senden Sie eine JSON-Nutzlast an die Webhook-URL.</span><span class="sxs-lookup"><span data-stu-id="9f9f4-105">To send a message through your Office 365 Connector or incoming webhook, you post a JSON payload to the webhook URL.</span></span> <span data-ttu-id="9f9f4-106">Normalerweise wird diese Nutzlast in einer [Office 365-Connectorkarte](~/task-modules-and-cards/cards/cards-reference.md#office-365-connector-card) bestehen.</span><span class="sxs-lookup"><span data-stu-id="9f9f4-106">Typically this payload will be in the form of an [Office 365 Connector Card](~/task-modules-and-cards/cards/cards-reference.md#office-365-connector-card).</span></span>

<span data-ttu-id="9f9f4-107">Sie können diesen JSON-Code auch zum Erstellen von Karten mit umfassenden Eingabeoptionen verwenden, wie z. B. Texteingabe, Mehrfachauswahl oder Auswählen eines Datums und einer Uhrzeit.</span><span class="sxs-lookup"><span data-stu-id="9f9f4-107">You can also use this JSON to create cards containing rich inputs, such as text entry, multi-select, or picking a date and time.</span></span> <span data-ttu-id="9f9f4-108">Der Code, der die Karte generiert und an die Webhook-URL sendet, kann auf jedem gehosteten Dienst ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="9f9f4-108">The code that generates the card and posts to the webhook URL can be running on any hosted service.</span></span> <span data-ttu-id="9f9f4-109">Diese Karten sind als Bestandteil von Nachrichten mit Aktionen definiert und werden auch in [Karten](~/task-modules-and-cards/what-are-cards.md) unterstützt, die in Microsoft Teams-Bots und Messaging-Erweiterungen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="9f9f4-109">These cards are defined as part of actionable messages, and are also supported in [cards](~/task-modules-and-cards/what-are-cards.md) used in Teams bots and Messaging extensions.</span></span>

### <a name="example-connector-message"></a><span data-ttu-id="9f9f4-110">Connector-Beispielnachricht</span><span class="sxs-lookup"><span data-stu-id="9f9f4-110">Example connector message</span></span>

```json
{
    "@type": "MessageCard",
    "@context": "http://schema.org/extensions",
    "themeColor": "0076D7",
    "summary": "Larry Bryant created a new task",
    "sections": [{
        "activityTitle": "![TestImage](https://47a92947.ngrok.io/Content/Images/default.png)Larry Bryant created a new task",
        "activitySubtitle": "On Project Tango",
        "activityImage": "https://teamsnodesample.azurewebsites.net/static/img/image5.png",
        "facts": [{
            "name": "Assigned to",
            "value": "Unassigned"
        }, {
            "name": "Due date",
            "value": "Mon May 01 2017 17:07:18 GMT-0700 (Pacific Daylight Time)"
        }, {
            "name": "Status",
            "value": "Not started"
        }],
        "markdown": true
    }],
    "potentialAction": [{
        "@type": "ActionCard",
        "name": "Add a comment",
        "inputs": [{
            "@type": "TextInput",
            "id": "comment",
            "isMultiline": false,
            "title": "Add a comment here for this task"
        }],
        "actions": [{
            "@type": "HttpPOST",
            "name": "Add comment",
            "target": "http://..."
        }]
    }, {
        "@type": "ActionCard",
        "name": "Set due date",
        "inputs": [{
            "@type": "DateInput",
            "id": "dueDate",
            "title": "Enter a due date for this task"
        }],
        "actions": [{
            "@type": "HttpPOST",
            "name": "Save",
            "target": "http://..."
        }]
    }, {
        "@type": "ActionCard",
        "name": "Change status",
        "inputs": [{
            "@type": "MultichoiceInput",
            "id": "list",
            "title": "Select a status",
            "isMultiSelect": "false",
            "choices": [{
                "display": "In Progress",
                "value": "1"
            }, {
                "display": "Active",
                "value": "2"
            }, {
                "display": "Closed",
                "value": "3"
            }]
        }],
        "actions": [{
            "@type": "HttpPOST",
            "name": "Save",
            "target": "http://..."
        }]
    }]
}
```

<span data-ttu-id="9f9f4-111">Diese Meldung erzeugt die folgende Karte im Kanal.</span><span class="sxs-lookup"><span data-stu-id="9f9f4-111">This message produces the following card in the channel.</span></span>

![Screenshot einer Connectorkarte](~/assets/images/connectors/connector_message.png)

## <a name="creating-actionable-messages"></a><span data-ttu-id="9f9f4-113">Erstellen von Nachrichten mit Aktionen</span><span class="sxs-lookup"><span data-stu-id="9f9f4-113">Creating actionable messages</span></span>

<span data-ttu-id="9f9f4-114">Das Beispiel im vorherigen Abschnitt umfasst drei sichtbare Schaltflächen auf der Karte.</span><span class="sxs-lookup"><span data-stu-id="9f9f4-114">The example in the preceding section includes three visible buttons on the card.</span></span> <span data-ttu-id="9f9f4-115">Jede Schaltfläche wird in der `potentialAction`-Eigenschaft der Nachricht mithilfe von `ActionCard`-Aktionen definiert, die jeweils einen Eingabetyp enthalten: ein Textfeld, eine Datumsauswahl oder eine Mehrfachauswahlliste.</span><span class="sxs-lookup"><span data-stu-id="9f9f4-115">Each button is defined in the `potentialAction` property of the message by using `ActionCard` actions, each containing an input type: a text field, a date picker, or a multi-choice list.</span></span> <span data-ttu-id="9f9f4-116">Jeder `ActionCard`-Aktion ist eine Aktion zugeordnet, z. B. `HttpPOST`.</span><span class="sxs-lookup"><span data-stu-id="9f9f4-116">Each `ActionCard` action has an associated action, for example `HttpPOST`.</span></span>

<span data-ttu-id="9f9f4-117">Connectorkarten unterstützen drei Arten von Aktionen:</span><span class="sxs-lookup"><span data-stu-id="9f9f4-117">Connector cards support three types of actions:</span></span>

- <span data-ttu-id="9f9f4-118">`ActionCard`: Zeigt einen oder mehrere Eingabetypen sowie die zugeordneten Aktionen an</span><span class="sxs-lookup"><span data-stu-id="9f9f4-118">`ActionCard` Presents one or more input types and associated actions</span></span>
- <span data-ttu-id="9f9f4-119">`HttpPOST`: Sendet eine POST-Anforderung an eine URL</span><span class="sxs-lookup"><span data-stu-id="9f9f4-119">`HttpPOST` Sends a POST request to a URL</span></span>
- <span data-ttu-id="9f9f4-120">`OpenUri`: Öffnet einen URI in einem separaten Browser oder in einer anderen App; zielt optional unterschiedliche URIs basierend auf Betriebssystemen an</span><span class="sxs-lookup"><span data-stu-id="9f9f4-120">`OpenUri` Opens a URI in a separate browser or app; optionally targets different URIs based on operating systems</span></span>

<span data-ttu-id="9f9f4-121">(Eine vierte Aktion (`ViewAction`) wird weiterhin unterstützt, aber nicht mehr benötigt. Verwenden Sie stattdessen `OpenUri`.)</span><span class="sxs-lookup"><span data-stu-id="9f9f4-121">(A fourth action, `ViewAction`, is still supported but no longer needed; use `OpenUri` instead.)</span></span>

<span data-ttu-id="9f9f4-122">Die `ActionCard`-Aktion unterstützt drei Eingabetypen:</span><span class="sxs-lookup"><span data-stu-id="9f9f4-122">The `ActionCard` action supports three input types:</span></span>

- <span data-ttu-id="9f9f4-123">`TextInput`: Ein ein- oder mehrzeiliges Textfeld mit optionaler Längenbegrenzung</span><span class="sxs-lookup"><span data-stu-id="9f9f4-123">`TextInput` A single-line or multiline text field with an optional length limit</span></span>
- <span data-ttu-id="9f9f4-124">`DateInput`: Datumsauswahl mit optionaler Zeitauswahl</span><span class="sxs-lookup"><span data-stu-id="9f9f4-124">`DateInput` A date selector with an optional time selector</span></span>
- <span data-ttu-id="9f9f4-125">`MultichoiceInput`: Eine Liste mit Auswahlmöglichkeiten, die entweder die Auswahl einer einzelnen Option oder mehrerer Optionen bietet</span><span class="sxs-lookup"><span data-stu-id="9f9f4-125">`MultichoiceInput` A enumerated list of choices offering either a single selection or multiple selections</span></span>

<span data-ttu-id="9f9f4-126">`MultichoiceInput` unterstützt eine `style`-Eigenschaft über die festgelegt wird, ob die Liste anfänglich vollständig erweitert angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="9f9f4-126">`MultichoiceInput` supports a `style` property that controls whether the list initially appears fully expanded.</span></span> <span data-ttu-id="9f9f4-127">Der Standardwert von `style` hängt vom `isMultiSelect`-Wert ab.</span><span class="sxs-lookup"><span data-stu-id="9f9f4-127">The default value of `style` depends on the value of `isMultiSelect`.</span></span>

| `isMultiSelect` | <span data-ttu-id="9f9f4-128">`style`-Standardeinstellung</span><span class="sxs-lookup"><span data-stu-id="9f9f4-128">`style` default</span></span> |
| --- | --- |
| <span data-ttu-id="9f9f4-129">`false` oder nicht angegeben</span><span class="sxs-lookup"><span data-stu-id="9f9f4-129">`false` or not specified</span></span> | `compact` |
| `true` | `expanded` |

<span data-ttu-id="9f9f4-130">Wenn Sie möchten, dass eine Liste mit Mehrfachauswahl zuerst kompakt angezeigt wird, müssen Sie sowohl `"isMultiSelect": true` als auch `"style": true` angeben.</span><span class="sxs-lookup"><span data-stu-id="9f9f4-130">If you want a multiselect list initially displayed in the compact style, you must specify both `"isMultiSelect": true` and `"style": true`.</span></span>

> [!NOTE]
> <span data-ttu-id="9f9f4-131">Die Angabe von `compact` für die `style`-Eigenschaft in Microsoft Teams entspricht der Angabe von `normal` für die `style`-Eigenschaft in Microsoft Outlook.</span><span class="sxs-lookup"><span data-stu-id="9f9f4-131">Specifying `compact` for the `style` property in Microsoft Teams is the same as specifying `normal` for the `style` property in Microsoft Outlook.</span></span>

<span data-ttu-id="9f9f4-132">Weitere Details zu den Aktionen in Connectorkarten finden Sie unter **[Aktionen](/outlook/actionable-messages/card-reference#actions)** in der Referenz zu Nachrichtenkarten mit Aktionen.</span><span class="sxs-lookup"><span data-stu-id="9f9f4-132">For all other details about Connector card actions, see **[Actions](/outlook/actionable-messages/card-reference#actions)** in the actionable message card reference.</span></span>

## <a name="setting-up-a-custom-incoming-webhook"></a><span data-ttu-id="9f9f4-133">Einrichten eines benutzerdefinierten eingehenden Webhooks</span><span class="sxs-lookup"><span data-stu-id="9f9f4-133">Setting up a custom incoming webhook</span></span>

<span data-ttu-id="9f9f4-134">Führen Sie die folgenden Schritte aus, um zu erfahren, wie Sie eine einfache Karte an einen Connector senden können.</span><span class="sxs-lookup"><span data-stu-id="9f9f4-134">Follow these steps to see how to send a simple card to a Connector.</span></span>

1. <span data-ttu-id="9f9f4-135">Wählen Sie in Microsoft Teams **Weitere Optionen** (**&#8943;**) neben dem Kanalnamen aus, und wählen Sie dann **Connectors**aus.</span><span class="sxs-lookup"><span data-stu-id="9f9f4-135">In Microsoft Teams, choose **More options** (**&#8943;**) next to the channel name and then choose **Connectors**.</span></span>
2. <span data-ttu-id="9f9f4-136">Scrollen Sie durch die Liste der Connectors bis zu **Eingehender Webhook**, und wählen Sie **Hinzufügen** aus.</span><span class="sxs-lookup"><span data-stu-id="9f9f4-136">Scroll through the list of Connectors to **Incoming Webhook**, and choose **Add**.</span></span>
3. <span data-ttu-id="9f9f4-137">Geben Sie einen Namen für den Webhook ein, laden Sie ein Bild hoch, das mit Daten aus dem Webhook verknüpft werden soll, und wählen Sie **Erstellen**aus.</span><span class="sxs-lookup"><span data-stu-id="9f9f4-137">Enter a name for the webhook, upload an image to associate with data from the webhook, and choose **Create**.</span></span>
4. <span data-ttu-id="9f9f4-138">Kopieren Sie den Webhook in die Zwischenablage, und speichern Sie ihn.</span><span class="sxs-lookup"><span data-stu-id="9f9f4-138">Copy the webhook to the clipboard and save it.</span></span> <span data-ttu-id="9f9f4-139">Sie benötigen die Webhook-URL zum Senden von Informationen an Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="9f9f4-139">You'll need the webhook URL for sending information to Microsoft Teams.</span></span>
5. <span data-ttu-id="9f9f4-140">Klicken Sie auf **Fertig**.</span><span class="sxs-lookup"><span data-stu-id="9f9f4-140">Choose **Done**.</span></span>

### <a name="post-a-message-to-the-webhook-using-curl"></a><span data-ttu-id="9f9f4-141">Senden einer Nachricht an den Webhook mithilfe von cURL</span><span class="sxs-lookup"><span data-stu-id="9f9f4-141">Post a message to the webhook using cURL</span></span>

<span data-ttu-id="9f9f4-142">In den folgenden Schritten wird [cURL](https://curl.haxx.se/) verwendet.</span><span class="sxs-lookup"><span data-stu-id="9f9f4-142">The following steps use [cURL](https://curl.haxx.se/).</span></span> <span data-ttu-id="9f9f4-143">Wir gehen davon aus, dass Sie es installiert haben und mit den Grundlagen seiner Nutzung vertraut sind.</span><span class="sxs-lookup"><span data-stu-id="9f9f4-143">We assume that you have this installed and are familiar with its basic usage.</span></span>

1. <span data-ttu-id="9f9f4-144">Geben Sie den folgenden cURL-Befehl in die Befehlszeile ein:</span><span class="sxs-lookup"><span data-stu-id="9f9f4-144">From the command line, enter the following cURL command:</span></span>

   ```bash
   // on macOS or Linux
   curl -H 'Content-Type: application/json' -d '{"text": "Hello World"}' <YOUR WEBHOOK URL>
   ```

   ```bash
   // on Windows
   curl.exe -H "Content-Type:application/json" -d "{'text':'Hello World'}" <YOUR WEBHOOK URL>
   ```

2. <span data-ttu-id="9f9f4-145">Wenn die POST-Anforderung erfolgreich ist, sollte eine einfache **1** durch `curl` ausgegeben werden.</span><span class="sxs-lookup"><span data-stu-id="9f9f4-145">If the POST succeeds, you should see a simple **1** output by `curl`.</span></span>
3. <span data-ttu-id="9f9f4-146">Überprüfen Sie den Microsoft Teams-Client.</span><span class="sxs-lookup"><span data-stu-id="9f9f4-146">Check the Microsoft Team client.</span></span> <span data-ttu-id="9f9f4-147">Die neue Karte sollte nun im Team bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="9f9f4-147">You should see the new card posted to the team.</span></span>

### <a name="post-a-message-to-the-webhook-using-powershell"></a><span data-ttu-id="9f9f4-148">Senden einer Nachricht an den Webhook mithilfe von PowerShell</span><span class="sxs-lookup"><span data-stu-id="9f9f4-148">Post a message to the webhook using PowerShell</span></span>

<span data-ttu-id="9f9f4-149">In den folgenden Schritten wird PowerShell verwendet.</span><span class="sxs-lookup"><span data-stu-id="9f9f4-149">The following steps use PowerShell.</span></span> <span data-ttu-id="9f9f4-150">Wir gehen davon aus, dass Sie es installiert haben und mit den Grundlagen seiner Nutzung vertraut sind.</span><span class="sxs-lookup"><span data-stu-id="9f9f4-150">We assume that you have this installed and are familiar with its basic usage.</span></span>

1. <span data-ttu-id="9f9f4-151">Geben Sie in der PowerShell-Eingabeaufforderung den folgenden Befehl ein:</span><span class="sxs-lookup"><span data-stu-id="9f9f4-151">From the PowerShell prompt, enter the following command:</span></span>

   ```powershell
   Invoke-RestMethod -Method post -ContentType 'Application/Json' -Body '{"text":"Hello World!"}' -Uri <YOUR WEBHOOK URL>
   ```

2. <span data-ttu-id="9f9f4-152">Wenn die POST-Anforderung erfolgreich ist, sollte eine einfache **1** durch `Invoke-RestMethod` ausgegeben werden.</span><span class="sxs-lookup"><span data-stu-id="9f9f4-152">If the POST succeeds, you should see a simple **1** output by `Invoke-RestMethod`.</span></span>
3. <span data-ttu-id="9f9f4-153">Überprüfen Sie den Microsoft Teams-Kanal, der der Webhook-URL zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="9f9f4-153">Check the Microsoft Teams channel associated with the webhook URL.</span></span> <span data-ttu-id="9f9f4-154">Die neue Karte sollte nun im Kanal bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="9f9f4-154">You should see the new card posted to the channel.</span></span>

- <span data-ttu-id="9f9f4-155">Schließen Sie zwei Symbole ein, indem Sie den Anweisungen in [Symbole](~/concepts/build-and-test/apps-package.md#icons) folgen.</span><span class="sxs-lookup"><span data-stu-id="9f9f4-155">Include two icons, following the instructions in [Icons](~/concepts/build-and-test/apps-package.md#icons).</span></span>
- <span data-ttu-id="9f9f4-156">Ändern Sie den `icons`-Teil des Manifests so, dass er auf die Dateinamen der Symbole anstelle von URLs verweist.</span><span class="sxs-lookup"><span data-stu-id="9f9f4-156">Modify the `icons` portion of the manifest to refer to the file names of the icons instead of URLs.</span></span>

<span data-ttu-id="9f9f4-157">Die folgende manifest.JSON-Datei enthält die grundlegenden Elemente, die zum Testen und Übermitteln Ihrer APP erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="9f9f4-157">The following manifest.json file contains the basic elements needed to test and submit your app.</span></span>

> [!NOTE]
> <span data-ttu-id="9f9f4-158">Ersetzen Sie im folgenden Beispiel `id` und `connectorId` mit der GUID des Connectors.</span><span class="sxs-lookup"><span data-stu-id="9f9f4-158">Replace `id` and `connectorId` in the following example with the GUID of your Connector.</span></span>

#### <a name="example-manifestjson-with-connector"></a><span data-ttu-id="9f9f4-159">Beispiel-manifest.JSON mit Connector</span><span class="sxs-lookup"><span data-stu-id="9f9f4-159">Example manifest.json with connector</span></span>

```json
{
  "$schema": "https://developer.microsoft.com/json-schemas/teams/v1.7/MicrosoftTeams.schema.json",
  "manifestVersion": "1.5",
  "id": "e9343a03-0a5e-4c1f-95a8-263a565505a5",
  "version": "1.0",
  "packageName": "com.sampleapp",
  "developer": {
    "name": "Publisher",
    "websiteUrl": "https://www.microsoft.com",
    "privacyUrl": "https://www.microsoft.com",
    "termsOfUseUrl": "https://www.microsoft.com"
  },
  "description": {
    "full": "This is a small sample app we made for you! This app has samples of all capabilities Microsoft Teams supports.",
    "short": "This is a small sample app we made for you!"
  },
  "icons": {
    "outline": "sampleapp-outline.png",
    "color": "sampleapp-color.png"
  },
  "connectors": [
    {
      "connectorId": "e9343a03-0a5e-4c1f-95a8-263a565505a5",
      "scopes": [
        "team"
      ]
    }
  ],
  "name": {
    "short": "Sample App",
    "full": "Sample App"
  },
  "accentColor": "#FFFFFF",
  "needsIdentity": "true"
}
```

## <a name="send-adaptive-cards-using-an-incoming-webhook"></a><span data-ttu-id="9f9f4-160">Senden von adaptiven Karten mithilfe eines eingehenden Webhooks</span><span class="sxs-lookup"><span data-stu-id="9f9f4-160">Send adaptive cards using an incoming webhook</span></span>

> [!NOTE]
>
> <span data-ttu-id="9f9f4-161">✔ Alle systemeigenen adaptiven Kartenschemaelemente, mit Ausnahme von `Action.Submit`, werden vollständig unterstützt.</span><span class="sxs-lookup"><span data-stu-id="9f9f4-161">✔ All native adaptive card schema elements, except `Action.Submit`, are fully supported.</span></span>
>
> <span data-ttu-id="9f9f4-162">✔ Die unterstützten Aktionen sind [**Action.OpenURL**](https://adaptivecards.io/explorer/Action.OpenUrl.html), [**Action.ShowCard**](https://adaptivecards.io/explorer/Action.ShowCard.html) und [**Action.ToggleVisibility**](https://adaptivecards.io/explorer/Action.ToggleVisibility.html).</span><span class="sxs-lookup"><span data-stu-id="9f9f4-162">✔ The supported Actions are [**Action.OpenURL**](https://adaptivecards.io/explorer/Action.OpenUrl.html), [**Action.ShowCard**](https://adaptivecards.io/explorer/Action.ShowCard.html), and [**Action.ToggleVisibility**](https://adaptivecards.io/explorer/Action.ToggleVisibility.html).</span></span>

### <a name="the-flow-for-sending-adaptive-cards-via-an-incoming-webhook-is-as-follows"></a><span data-ttu-id="9f9f4-163">Der Datenstrom zum Senden von [adaptiven Karten](../../task-modules-and-cards/cards/cards-reference.md#adaptive-card) über einen eingehenden Webhook lautet wie folgt:</span><span class="sxs-lookup"><span data-stu-id="9f9f4-163">The flow for sending [adaptive cards](../../task-modules-and-cards/cards/cards-reference.md#adaptive-card) via an incoming webhook is as follows:</span></span>

<span data-ttu-id="9f9f4-164">**1.** [Einrichten eines benutzerdefinierten Webhooks](#setting-up-a-custom-incoming-webhook) in Teams.</span><span class="sxs-lookup"><span data-stu-id="9f9f4-164">**1.** [Setup a custom webhook](#setting-up-a-custom-incoming-webhook) in Teams.</span></span></br></br>
<span data-ttu-id="9f9f4-165">**2.** Erstellen Ihrer JSON-Datei für die adaptive Karte:</span><span class="sxs-lookup"><span data-stu-id="9f9f4-165">**2.** Create your adaptive card JSON file:</span></span>

```json
{
   "type":"message",
   "attachments":[
      {
         "contentType":"application/vnd.microsoft.card.adaptive",
         "contentUrl":null,
         "content":{
            "$schema":"http://adaptivecards.io/schemas/adaptive-card.json",
            "type":"AdaptiveCard",
            "version":"1.2",
            "body":[
                {
                "type": "TextBlock",
                "text": "For Samples and Templates, see https://adaptivecards.io/samples](https://adaptivecards.io/samples)",
                }
            ]
         }
      }
   ]
}
```

> [!div class="checklist"]
>
> - <span data-ttu-id="9f9f4-166">Das Feld `"type"` muss vom Typ `"message"` sein.</span><span class="sxs-lookup"><span data-stu-id="9f9f4-166">The `"type"` field must be `"message"`.</span></span>
> - <span data-ttu-id="9f9f4-167">Das Array `"attachments"` enthält eine Reihe von Kartenobjekten.</span><span class="sxs-lookup"><span data-stu-id="9f9f4-167">The `"attachments"` array contains a set of card objects.</span></span>
> - <span data-ttu-id="9f9f4-168">Das Feld `"contentType"` muss auf den Typ „adaptive Karte“ festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="9f9f4-168">The `"contentType"` field must be set to adaptive card type.</span></span>
> - <span data-ttu-id="9f9f4-169">Das Objekt `"content"` ist die in JSON formatierte Karte.</span><span class="sxs-lookup"><span data-stu-id="9f9f4-169">The `"content"` object is the card formatted in JSON.</span></span>

<span data-ttu-id="9f9f4-170">**3.** Testen Ihrer adaptiven Karte mit Postman</span><span class="sxs-lookup"><span data-stu-id="9f9f4-170">**3.** Test your adaptive card with Postman</span></span>

<span data-ttu-id="9f9f4-171">Sie können Ihre adaptive Karte mithilfe von [Postman](https://www.postman.com) testen, um eine POST-Anforderung an die URL zu senden, die Sie beim Einrichten Ihres eingehenden Webhooks erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="9f9f4-171">You can test your adaptive card using [Postman](https://www.postman.com) to send a POST request to the URL that you created when you setup your incoming webhook.</span></span> <span data-ttu-id="9f9f4-172">Fügen Sie Ihre JSON-Datei in den Textkörper der Anforderung ein, und zeigen Sie die Nachricht Ihrer adaptiven Karte in Teams an.</span><span class="sxs-lookup"><span data-stu-id="9f9f4-172">Paste your JSON file in the body of the request and view your adaptive card message in Teams.</span></span>

>[!TIP]
> <span data-ttu-id="9f9f4-173">Sie können den Code der adaptiven Karte [Beispiele und Vorlagen](https://adaptivecards.io/samples) für den Textkörper Ihrer POST-Testanforderung verwenden.</span><span class="sxs-lookup"><span data-stu-id="9f9f4-173">You can use adaptive card code [Samples and Templates](https://adaptivecards.io/samples) for the body of your test Post request.</span></span>

## <a name="testing-your-connector"></a><span data-ttu-id="9f9f4-174">Testen des Connectors</span><span class="sxs-lookup"><span data-stu-id="9f9f4-174">Testing your connector</span></span>

<span data-ttu-id="9f9f4-175">Um den Connector zu testen, laden Sie ihn wie jede andere App in ein Team hoch.</span><span class="sxs-lookup"><span data-stu-id="9f9f4-175">To test your Connector, upload it to a team as you would with any other app.</span></span> <span data-ttu-id="9f9f4-176">Sie können ein ZIP-Paket erstellen und dafür die (wie im vorherigen Abschnitt beschrieben modifizierte) Manifestdatei aus dem Entwicklerdashboard für Connectors sowie die beiden Symboldateien verwenden.</span><span class="sxs-lookup"><span data-stu-id="9f9f4-176">You can create a .zip package using the manifest file from the Connectors Developer Dashboard (modified as directed in the preceding section) and the two icon files.</span></span>

<span data-ttu-id="9f9f4-177">Nachdem Sie die App hochgeladen haben, öffnen Sie die Liste der Connectors von einem beliebigen Kanal aus.</span><span class="sxs-lookup"><span data-stu-id="9f9f4-177">After you upload the app, open the Connectors list from any channel.</span></span> <span data-ttu-id="9f9f4-178">Scrollen Sie ganz nach unten bis zu Ihrer App im Abschnitt **Hochgeladenen**.</span><span class="sxs-lookup"><span data-stu-id="9f9f4-178">Scroll to the bottom to see your app in the **Uploaded** section.</span></span>

![Screenshot des Abschnitts "Hochgeladen" im Connector-Dialogfeld](~/assets/images/connectors/connector_dialog_uploaded.png)

<span data-ttu-id="9f9f4-180">Sie können nun die Konfigurationsfunktion starten.</span><span class="sxs-lookup"><span data-stu-id="9f9f4-180">You can now launch the configuration experience.</span></span> <span data-ttu-id="9f9f4-181">Denken Sie daran, dass dieser Vorgang innerhalb von Microsoft Teams über ein Popupfenster erfolgt.</span><span class="sxs-lookup"><span data-stu-id="9f9f4-181">Be aware that this flow occurs entirely within Microsoft Teams through a pop-up window.</span></span> <span data-ttu-id="9f9f4-182">Derzeit unterscheidet sich dieses Verhalten von der Konfigurationsfunktion in den von uns erstellten Connectoren. Wir arbeiten an einer Vereinheitlichung der Benutzererfahrung.</span><span class="sxs-lookup"><span data-stu-id="9f9f4-182">Currently, this behavior differs from the configuration experience in Connectors that we created; we are working on unifying the experiences.</span></span>

<span data-ttu-id="9f9f4-183">Um zu überprüfen, ob eine `HttpPOST`-Aktion ordnungsgemäß funktioniert, verwenden Sie Ihren [benutzerdefinierten eingehenden Webhook](#setting-up-a-custom-incoming-webhook).</span><span class="sxs-lookup"><span data-stu-id="9f9f4-183">To verify that an `HttpPOST` action is working correctly, use your [custom incoming webhook](#setting-up-a-custom-incoming-webhook).</span></span>

## <a name="rate-limiting-for-connectors"></a><span data-ttu-id="9f9f4-184">Begrenzung der Datenübertragungsrate für Connectors</span><span class="sxs-lookup"><span data-stu-id="9f9f4-184">Rate limiting for connectors</span></span>

<span data-ttu-id="9f9f4-185">Die Grenzwerte für die Anwendungsdatenübertragungsrate steuern den Datenverkehr, der von einem Connector oder eingehenden Webhook in einem Kanal generiert werden darf.</span><span class="sxs-lookup"><span data-stu-id="9f9f4-185">Application rate limits control the traffic that a connector or an incoming webhook is allowed to generate on a channel.</span></span> <span data-ttu-id="9f9f4-186">Teams verfolgt Anforderungen über ein Fenster mit fester Datenübertragungsrate und einen inkrementellen Zähler, der in Sekunden gemessen wird.</span><span class="sxs-lookup"><span data-stu-id="9f9f4-186">Teams tracks requests via a fixed-rate window and incremental counter measured in seconds.</span></span>  <span data-ttu-id="9f9f4-187">Wenn zu viele Anforderungen gestellt werden, wird die Clientverbindung gedrosselt, bis das Fenster aktualisiert wird, d. h. für die Dauer der festen Datenübertragungsrate.</span><span class="sxs-lookup"><span data-stu-id="9f9f4-187">If too many requests are made, the client connection will be throttled until the window refreshes, i.e., for the duration of the fixed rate.</span></span>

### <a name="transactions-per-second-thresholds"></a><span data-ttu-id="9f9f4-188">**Schwellenwerte für Transaktionen pro Sekunde**</span><span class="sxs-lookup"><span data-stu-id="9f9f4-188">**Transactions per second thresholds**</span></span>

| <span data-ttu-id="9f9f4-189">Zeit (Sekunden)</span><span class="sxs-lookup"><span data-stu-id="9f9f4-189">Time (seconds)</span></span>  | <span data-ttu-id="9f9f4-190">Maximal zulässige Anforderungen</span><span class="sxs-lookup"><span data-stu-id="9f9f4-190">Maximum allowed requests</span></span>  |
|---|---|
| <span data-ttu-id="9f9f4-191">1</span><span class="sxs-lookup"><span data-stu-id="9f9f4-191">1</span></span>   | <span data-ttu-id="9f9f4-192">4</span><span class="sxs-lookup"><span data-stu-id="9f9f4-192">4</span></span>  |  
| <span data-ttu-id="9f9f4-193">30</span><span class="sxs-lookup"><span data-stu-id="9f9f4-193">30</span></span>   | <span data-ttu-id="9f9f4-194">60</span><span class="sxs-lookup"><span data-stu-id="9f9f4-194">60</span></span>  |  
| <span data-ttu-id="9f9f4-195">3600</span><span class="sxs-lookup"><span data-stu-id="9f9f4-195">3600</span></span>   | <span data-ttu-id="9f9f4-196">100</span><span class="sxs-lookup"><span data-stu-id="9f9f4-196">100</span></span>  |
| <span data-ttu-id="9f9f4-197">7200</span><span class="sxs-lookup"><span data-stu-id="9f9f4-197">7200</span></span> | <span data-ttu-id="9f9f4-198">150</span><span class="sxs-lookup"><span data-stu-id="9f9f4-198">150</span></span>  |
| <span data-ttu-id="9f9f4-199">86400</span><span class="sxs-lookup"><span data-stu-id="9f9f4-199">86400</span></span>  | <span data-ttu-id="9f9f4-200">1800</span><span class="sxs-lookup"><span data-stu-id="9f9f4-200">1800</span></span>  |

<span data-ttu-id="9f9f4-201">*Siehe auch* [Office 365-Connectors – Microsoft Teams](https://docs.microsoft.com/connectors/teams/)</span><span class="sxs-lookup"><span data-stu-id="9f9f4-201">*See also* [Office 365 Connectors — Microsoft Teams](https://docs.microsoft.com/connectors/teams/)</span></span>

<span data-ttu-id="9f9f4-202">Eine [Wiederholungslogik mit exponentiellem Backoff](/azure/architecture/patterns/retry) wie unten würde die Begrenzung der Datenübertragungsrate in Fällen abmildern, in denen Anforderungen die Grenzwerte innerhalb einer Sekunde überschreiten.</span><span class="sxs-lookup"><span data-stu-id="9f9f4-202">A [retry logic with exponential back-off](/azure/architecture/patterns/retry) like below would mitigate rate limiting for cases where requests are exceeding the limits within a second.</span></span> <span data-ttu-id="9f9f4-203">Wenden Sie bitte [bewährte Methoden](../../bots/how-to/rate-limit.md#best-practices) an, um zu vermeiden, dass die Ratenlimits überschritten werden.</span><span class="sxs-lookup"><span data-stu-id="9f9f4-203">Please follow [best practices](../../bots/how-to/rate-limit.md#best-practices) to avoid hitting the rate limits.</span></span>

```csharp
// Please note that response body needs to be extracted and read 
// as Connectors do not throw 429s
try
{
    // Perform Connector POST operation     
    var httpResponseMessage = await _client.PostAsync(IncomingWebhookUrl, new StringContent(content));
    // Read response content
    var responseContent = await httpResponseMessage.Content.ReadAsStringAsync();
    if (responseContent.Contains("Microsoft Teams endpoint returned HTTP error 429")) 
    {
        // initiate retry logic
    }
}
```
 
<span data-ttu-id="9f9f4-204">Diese Limits haben den Zweck, das Spamming eines Kanals durch einen Connector zu verringern und Ihren Endbenutzer eine optimale Benutzererfahrung zu gewährleisten.</span><span class="sxs-lookup"><span data-stu-id="9f9f4-204">These limits are in place to reduce spamming a channel by a connector and ensures an optimal experience to your end users.</span></span>
