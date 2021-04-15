---
title: Senden von Nachrichten an Connectors und Webhooks
description: Beschreibt die Verwendung von Office 365-Connectors in Microsoft Teams
ms.topic: how-to
localization_priority: Priority
keywords: Teams O365-Connector
ms.openlocfilehash: 28c1a6e68a0ac83a2eb4785d71596814d5a859d3
ms.sourcegitcommit: 79e6bccfb513d4c16a58ffc03521edcf134fa518
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/13/2021
ms.locfileid: "51696017"
---
# <a name="sending-messages-to-connectors-and-webhooks"></a><span data-ttu-id="a4e2a-104">Senden von Nachrichten an Connectors und Webhooks</span><span class="sxs-lookup"><span data-stu-id="a4e2a-104">Sending messages to connectors and webhooks</span></span>

<span data-ttu-id="a4e2a-105">Wenn Sie eine Nachricht über Ihren Office 365-Connector oder eingehenden Webhook senden möchten, senden Sie eine JSON-Nutzlast an die Webhook-URL.</span><span class="sxs-lookup"><span data-stu-id="a4e2a-105">To send a message through your Office 365 Connector or incoming webhook, you post a JSON payload to the webhook URL.</span></span> <span data-ttu-id="a4e2a-106">Normalerweise wird diese Nutzlast in einer [Office 365-Connectorkarte](~/task-modules-and-cards/cards/cards-reference.md#office-365-connector-card) bestehen.</span><span class="sxs-lookup"><span data-stu-id="a4e2a-106">Typically this payload will be in the form of an [Office 365 Connector Card](~/task-modules-and-cards/cards/cards-reference.md#office-365-connector-card).</span></span>

<span data-ttu-id="a4e2a-107">Sie können diesen JSON-Code auch zum Erstellen von Karten mit umfassenden Eingabeoptionen verwenden, wie z. B. Texteingabe, Mehrfachauswahl oder Auswählen eines Datums und einer Uhrzeit.</span><span class="sxs-lookup"><span data-stu-id="a4e2a-107">You can also use this JSON to create cards containing rich inputs, such as text entry, multi-select, or picking a date and time.</span></span> <span data-ttu-id="a4e2a-108">Der Code, der die Karte generiert und an die Webhook-URL sendet, kann auf jedem gehosteten Dienst ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="a4e2a-108">The code that generates the card and posts to the webhook URL can be running on any hosted service.</span></span> <span data-ttu-id="a4e2a-109">Diese Karten sind als Bestandteil von Nachrichten mit Aktionen definiert und werden auch in [Karten](~/task-modules-and-cards/what-are-cards.md) unterstützt, die in Microsoft Teams-Bots und Messaging-Erweiterungen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="a4e2a-109">These cards are defined as part of actionable messages, and are also supported in [cards](~/task-modules-and-cards/what-are-cards.md) used in Teams bots and Messaging extensions.</span></span>

### <a name="example-connector-message"></a><span data-ttu-id="a4e2a-110">Connector-Beispielnachricht</span><span class="sxs-lookup"><span data-stu-id="a4e2a-110">Example connector message</span></span>

```json
{
    "@type": "MessageCard",
    "@context": "http://schema.org/extensions",
    "themeColor": "0076D7",
    "summary": "Larry Bryant created a new task",
    "sections": [{
        "activityTitle": "Larry Bryant created a new task",
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
            "target": "https://docs.microsoft.com/outlook/actionable-messages"
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
            "target": "https://docs.microsoft.com/outlook/actionable-messages"
        }]
    }, {
        "@type": "OpenUri",
        "name": "Learn More",
        "targets": [{
            "os": "default",
            "uri": "https://docs.microsoft.com/outlook/actionable-messages"
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
            "target": "https://docs.microsoft.com/outlook/actionable-messages"
        }]
    }]
}
```

<span data-ttu-id="a4e2a-111">Diese Meldung erzeugt die folgende Karte im Kanal.</span><span class="sxs-lookup"><span data-stu-id="a4e2a-111">This message produces the following card in the channel.</span></span>

![Screenshot einer Connectorkarte](~/assets/images/connectors/connector_message.png)

## <a name="creating-actionable-messages"></a><span data-ttu-id="a4e2a-113">Erstellen von Nachrichten mit Aktionen</span><span class="sxs-lookup"><span data-stu-id="a4e2a-113">Creating actionable messages</span></span>

<span data-ttu-id="a4e2a-114">Das Beispiel im vorherigen Abschnitt umfasst drei sichtbare Schaltflächen auf der Karte.</span><span class="sxs-lookup"><span data-stu-id="a4e2a-114">The example in the preceding section includes three visible buttons on the card.</span></span> <span data-ttu-id="a4e2a-115">Jede Schaltfläche wird in der `potentialAction`-Eigenschaft der Nachricht mithilfe von `ActionCard`-Aktionen definiert, die jeweils einen Eingabetyp enthalten: ein Textfeld, eine Datumsauswahl oder eine Mehrfachauswahlliste.</span><span class="sxs-lookup"><span data-stu-id="a4e2a-115">Each button is defined in the `potentialAction` property of the message by using `ActionCard` actions, each containing an input type: a text field, a date picker, or a multi-choice list.</span></span> <span data-ttu-id="a4e2a-116">Jeder `ActionCard`-Aktion ist eine Aktion zugeordnet, z. B. `HttpPOST`.</span><span class="sxs-lookup"><span data-stu-id="a4e2a-116">Each `ActionCard` action has an associated action, for example `HttpPOST`.</span></span>

<span data-ttu-id="a4e2a-117">Connectorkarten unterstützen drei Arten von Aktionen:</span><span class="sxs-lookup"><span data-stu-id="a4e2a-117">Connector cards support three types of actions:</span></span>

- <span data-ttu-id="a4e2a-118">`ActionCard`: Zeigt einen oder mehrere Eingabetypen sowie die zugeordneten Aktionen an</span><span class="sxs-lookup"><span data-stu-id="a4e2a-118">`ActionCard` Presents one or more input types and associated actions</span></span>
- <span data-ttu-id="a4e2a-119">`HttpPOST`: Sendet eine POST-Anforderung an eine URL</span><span class="sxs-lookup"><span data-stu-id="a4e2a-119">`HttpPOST` Sends a POST request to a URL</span></span>
- <span data-ttu-id="a4e2a-120">`OpenUri`: Öffnet einen URI in einem separaten Browser oder in einer anderen App; zielt optional unterschiedliche URIs basierend auf Betriebssystemen an</span><span class="sxs-lookup"><span data-stu-id="a4e2a-120">`OpenUri` Opens a URI in a separate browser or app; optionally targets different URIs based on operating systems</span></span>

<span data-ttu-id="a4e2a-121">Die `ActionCard`-Aktion unterstützt drei Eingabetypen:</span><span class="sxs-lookup"><span data-stu-id="a4e2a-121">The `ActionCard` action supports three input types:</span></span>

- <span data-ttu-id="a4e2a-122">`TextInput`: Ein ein- oder mehrzeiliges Textfeld mit optionaler Längenbegrenzung</span><span class="sxs-lookup"><span data-stu-id="a4e2a-122">`TextInput` A single-line or multiline text field with an optional length limit</span></span>
- <span data-ttu-id="a4e2a-123">`DateInput`: Datumsauswahl mit optionaler Zeitauswahl</span><span class="sxs-lookup"><span data-stu-id="a4e2a-123">`DateInput` A date selector with an optional time selector</span></span>
- <span data-ttu-id="a4e2a-124">`MultichoiceInput`: Eine Liste mit Auswahlmöglichkeiten, die entweder die Auswahl einer einzelnen Option oder mehrerer Optionen bietet</span><span class="sxs-lookup"><span data-stu-id="a4e2a-124">`MultichoiceInput` A enumerated list of choices offering either a single selection or multiple selections</span></span>

<span data-ttu-id="a4e2a-125">`MultichoiceInput` unterstützt eine `style`-Eigenschaft über die festgelegt wird, ob die Liste anfänglich vollständig erweitert angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="a4e2a-125">`MultichoiceInput` supports a `style` property that controls whether the list initially appears fully expanded.</span></span> <span data-ttu-id="a4e2a-126">Der Standardwert von `style` hängt vom `isMultiSelect`-Wert ab.</span><span class="sxs-lookup"><span data-stu-id="a4e2a-126">The default value of `style` depends on the value of `isMultiSelect`.</span></span>

| `isMultiSelect` | <span data-ttu-id="a4e2a-127">`style`-Standardeinstellung</span><span class="sxs-lookup"><span data-stu-id="a4e2a-127">`style` default</span></span> |
| --- | --- |
| <span data-ttu-id="a4e2a-128">`false` oder nicht angegeben</span><span class="sxs-lookup"><span data-stu-id="a4e2a-128">`false` or not specified</span></span> | `compact` |
| `true` | `expanded` |

<span data-ttu-id="a4e2a-129">Wenn Sie möchten, dass eine Liste mit Mehrfachauswahl zuerst kompakt angezeigt wird, müssen Sie sowohl `"isMultiSelect": true` als auch `"style": true` angeben.</span><span class="sxs-lookup"><span data-stu-id="a4e2a-129">If you want a multiselect list initially displayed in the compact style, you must specify both `"isMultiSelect": true` and `"style": true`.</span></span>

<span data-ttu-id="a4e2a-130">Weitere Informationen zu Aktionen der Connectorkarte finden Sie unter **[Aktionen]**(/outlook/actionable-messages/card-reference#actions) in der Referenz der verwertbaren Nachrichtenkarte.</span><span class="sxs-lookup"><span data-stu-id="a4e2a-130">For more information on Connector card actions, see **[Actions]**(/outlook/actionable-messages/card-reference#actions) in the actionable message card reference.</span></span>

> [!NOTE]
> <span data-ttu-id="a4e2a-131">Die Angabe von `compact` für die `style`-Eigenschaft in Microsoft Teams entspricht der Angabe von `normal` für die `style`-Eigenschaft in Microsoft Outlook.</span><span class="sxs-lookup"><span data-stu-id="a4e2a-131">Specifying `compact` for the `style` property in Microsoft Teams is the same as specifying `normal` for the `style` property in Microsoft Outlook.</span></span>
> 
> <span data-ttu-id="a4e2a-132">Bei der HttpPOST-Aktion ist das Bearertoken in den Anforderungen enthalten.</span><span class="sxs-lookup"><span data-stu-id="a4e2a-132">For the HttpPOST action, the bearer token is included with the requests.</span></span> <span data-ttu-id="a4e2a-133">Dieses Token enthält die Azure AD-Identität des Office 365-Benutzers, der die Aktion ausgeführt hat.</span><span class="sxs-lookup"><span data-stu-id="a4e2a-133">This token includes the Azure AD identity of the Office 365 user who took the action.</span></span>

## <a name="setting-up-a-custom-incoming-webhook"></a><span data-ttu-id="a4e2a-134">Einrichten eines benutzerdefinierten eingehenden Webhooks</span><span class="sxs-lookup"><span data-stu-id="a4e2a-134">Setting up a custom incoming webhook</span></span>

<span data-ttu-id="a4e2a-135">Führen Sie die folgenden Schritte aus, um zu erfahren, wie Sie eine einfache Karte an einen Connector senden können.</span><span class="sxs-lookup"><span data-stu-id="a4e2a-135">Follow these steps to see how to send a simple card to a Connector.</span></span>

1. <span data-ttu-id="a4e2a-136">Wählen Sie in Microsoft Teams **Weitere Optionen** (**&#8943;**) neben dem Kanalnamen aus, und wählen Sie dann **Connectors** aus.</span><span class="sxs-lookup"><span data-stu-id="a4e2a-136">In Microsoft Teams, choose **More options** (**&#8943;**) next to the channel name and then choose **Connectors**.</span></span>
2. <span data-ttu-id="a4e2a-137">Scrollen Sie durch die Liste der Connectors bis zu **Eingehender Webhook**, und wählen Sie **Hinzufügen** aus.</span><span class="sxs-lookup"><span data-stu-id="a4e2a-137">Scroll through the list of Connectors to **Incoming Webhook**, and choose **Add**.</span></span>
3. <span data-ttu-id="a4e2a-138">Geben Sie einen Namen für den Webhook ein, laden Sie ein Bild hoch, das mit Daten aus dem Webhook verknüpft werden soll, und wählen Sie **Erstellen** aus.</span><span class="sxs-lookup"><span data-stu-id="a4e2a-138">Enter a name for the webhook, upload an image to associate with data from the webhook, and choose **Create**.</span></span>
4. <span data-ttu-id="a4e2a-139">Kopieren Sie den Webhook in die Zwischenablage, und speichern Sie ihn.</span><span class="sxs-lookup"><span data-stu-id="a4e2a-139">Copy the webhook to the clipboard and save it.</span></span> <span data-ttu-id="a4e2a-140">Sie benötigen die Webhook-URL zum Senden von Informationen an Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="a4e2a-140">You'll need the webhook URL for sending information to Microsoft Teams.</span></span>
5. <span data-ttu-id="a4e2a-141">Klicken Sie auf **Fertig**.</span><span class="sxs-lookup"><span data-stu-id="a4e2a-141">Choose **Done**.</span></span>

### <a name="post-a-message-to-the-webhook-using-curl"></a><span data-ttu-id="a4e2a-142">Senden einer Nachricht an den Webhook mithilfe von cURL</span><span class="sxs-lookup"><span data-stu-id="a4e2a-142">Post a message to the webhook using cURL</span></span>

<span data-ttu-id="a4e2a-143">In den folgenden Schritten wird [cURL](https://curl.haxx.se/) verwendet.</span><span class="sxs-lookup"><span data-stu-id="a4e2a-143">The following steps use [cURL](https://curl.haxx.se/).</span></span> <span data-ttu-id="a4e2a-144">Wir gehen davon aus, dass Sie es installiert haben und mit den Grundlagen seiner Nutzung vertraut sind.</span><span class="sxs-lookup"><span data-stu-id="a4e2a-144">We assume that you have this installed and are familiar with its basic usage.</span></span>

1. <span data-ttu-id="a4e2a-145">Geben Sie den folgenden cURL-Befehl in die Befehlszeile ein:</span><span class="sxs-lookup"><span data-stu-id="a4e2a-145">From the command line, enter the following cURL command:</span></span>

   ```bash
   // on macOS or Linux
   curl -H 'Content-Type: application/json' -d '{"text": "Hello World"}' <YOUR WEBHOOK URL>
   ```

   ```bash
   // on Windows
   curl.exe -H "Content-Type:application/json" -d "{'text':'Hello World'}" <YOUR WEBHOOK URL>
   ```

2. <span data-ttu-id="a4e2a-146">Wenn die POST-Anforderung erfolgreich ist, sollte eine einfache **1** durch `curl` ausgegeben werden.</span><span class="sxs-lookup"><span data-stu-id="a4e2a-146">If the POST succeeds, you should see a simple **1** output by `curl`.</span></span>
3. <span data-ttu-id="a4e2a-147">Überprüfen Sie den Microsoft Teams-Client.</span><span class="sxs-lookup"><span data-stu-id="a4e2a-147">Check the Microsoft Team client.</span></span> <span data-ttu-id="a4e2a-148">Die neue Karte sollte nun im Team bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="a4e2a-148">You should see the new card posted to the team.</span></span>

### <a name="post-a-message-to-the-webhook-using-powershell"></a><span data-ttu-id="a4e2a-149">Senden einer Nachricht an den Webhook mithilfe von PowerShell</span><span class="sxs-lookup"><span data-stu-id="a4e2a-149">Post a message to the webhook using PowerShell</span></span>

<span data-ttu-id="a4e2a-150">In den folgenden Schritten wird PowerShell verwendet.</span><span class="sxs-lookup"><span data-stu-id="a4e2a-150">The following steps use PowerShell.</span></span> <span data-ttu-id="a4e2a-151">Wir gehen davon aus, dass Sie es installiert haben und mit den Grundlagen seiner Nutzung vertraut sind.</span><span class="sxs-lookup"><span data-stu-id="a4e2a-151">We assume that you have this installed and are familiar with its basic usage.</span></span>

1. <span data-ttu-id="a4e2a-152">Geben Sie in der PowerShell-Eingabeaufforderung den folgenden Befehl ein:</span><span class="sxs-lookup"><span data-stu-id="a4e2a-152">From the PowerShell prompt, enter the following command:</span></span>

   ```powershell
   Invoke-RestMethod -Method post -ContentType 'Application/Json' -Body '{"text":"Hello World!"}' -Uri <YOUR WEBHOOK URL>
   ```

2. <span data-ttu-id="a4e2a-153">Wenn die POST-Anforderung erfolgreich ist, sollte eine einfache **1** durch `Invoke-RestMethod` ausgegeben werden.</span><span class="sxs-lookup"><span data-stu-id="a4e2a-153">If the POST succeeds, you should see a simple **1** output by `Invoke-RestMethod`.</span></span>
3. <span data-ttu-id="a4e2a-154">Überprüfen Sie den Microsoft Teams-Kanal, der der Webhook-URL zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="a4e2a-154">Check the Microsoft Teams channel associated with the webhook URL.</span></span> <span data-ttu-id="a4e2a-155">Die neue Karte sollte nun im Kanal bereitgestellt werden.</span><span class="sxs-lookup"><span data-stu-id="a4e2a-155">You should see the new card posted to the channel.</span></span>

- <span data-ttu-id="a4e2a-156">[Zwei Symbole einschließen](../../concepts/build-and-test/apps-package.md#app-icons).</span><span class="sxs-lookup"><span data-stu-id="a4e2a-156">[Include two icons](../../concepts/build-and-test/apps-package.md#app-icons).</span></span>
- <span data-ttu-id="a4e2a-157">Ändern Sie den `icons`-Teil des Manifests so, dass er auf die Dateinamen der Symbole anstelle von URLs verweist.</span><span class="sxs-lookup"><span data-stu-id="a4e2a-157">Modify the `icons` portion of the manifest to refer to the file names of the icons instead of URLs.</span></span>

<span data-ttu-id="a4e2a-158">Die folgende manifest.JSON-Datei enthält die grundlegenden Elemente, die zum Testen und Übermitteln Ihrer APP erforderlich sind.</span><span class="sxs-lookup"><span data-stu-id="a4e2a-158">The following manifest.json file contains the basic elements needed to test and submit your app.</span></span>

> [!NOTE]
> <span data-ttu-id="a4e2a-159">Ersetzen Sie im folgenden Beispiel `id` und `connectorId` mit der GUID des Connectors.</span><span class="sxs-lookup"><span data-stu-id="a4e2a-159">Replace `id` and `connectorId` in the following example with the GUID of your Connector.</span></span>

#### <a name="example-manifestjson-with-connector"></a><span data-ttu-id="a4e2a-160">Beispiel-manifest.JSON mit Connector</span><span class="sxs-lookup"><span data-stu-id="a4e2a-160">Example manifest.json with connector</span></span>

```json
{
  "$schema": "https://developer.microsoft.com/json-schemas/teams/v1.8/MicrosoftTeams.schema.json",
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

## <a name="send-adaptive-cards-using-an-incoming-webhook"></a><span data-ttu-id="a4e2a-161">Senden von adaptiven Karten mithilfe eines eingehenden Webhooks</span><span class="sxs-lookup"><span data-stu-id="a4e2a-161">Send adaptive cards using an incoming webhook</span></span>

> [!NOTE]
>
> <span data-ttu-id="a4e2a-162">✔ Alle systemeigenen adaptiven Kartenschemaelemente, mit Ausnahme von `Action.Submit`, werden vollständig unterstützt.</span><span class="sxs-lookup"><span data-stu-id="a4e2a-162">✔ All native adaptive card schema elements, except `Action.Submit`, are fully supported.</span></span>
>
> <span data-ttu-id="a4e2a-163">✔ Die unterstützten Aktionen sind [**Action.OpenURL**](https://adaptivecards.io/explorer/Action.OpenUrl.html), [**Action.ShowCard**](https://adaptivecards.io/explorer/Action.ShowCard.html) und [**Action.ToggleVisibility**](https://adaptivecards.io/explorer/Action.ToggleVisibility.html).</span><span class="sxs-lookup"><span data-stu-id="a4e2a-163">✔ The supported Actions are [**Action.OpenURL**](https://adaptivecards.io/explorer/Action.OpenUrl.html), [**Action.ShowCard**](https://adaptivecards.io/explorer/Action.ShowCard.html), and [**Action.ToggleVisibility**](https://adaptivecards.io/explorer/Action.ToggleVisibility.html).</span></span>

### <a name="the-flow-for-sending-adaptive-cards-via-an-incoming-webhook-is-as-follows"></a><span data-ttu-id="a4e2a-164">Der Datenstrom zum Senden von [adaptiven Karten](../../task-modules-and-cards/cards/cards-reference.md#adaptive-card) über einen eingehenden Webhook lautet wie folgt:</span><span class="sxs-lookup"><span data-stu-id="a4e2a-164">The flow for sending [adaptive cards](../../task-modules-and-cards/cards/cards-reference.md#adaptive-card) via an incoming webhook is as follows:</span></span>

<span data-ttu-id="a4e2a-165">**1.** [Einrichten eines benutzerdefinierten Webhooks](#setting-up-a-custom-incoming-webhook) in Teams.</span><span class="sxs-lookup"><span data-stu-id="a4e2a-165">**1.** [Setup a custom webhook](#setting-up-a-custom-incoming-webhook) in Teams.</span></span></br></br>
<span data-ttu-id="a4e2a-166">**2.** Erstellen Ihrer JSON-Datei für die adaptive Karte:</span><span class="sxs-lookup"><span data-stu-id="a4e2a-166">**2.** Create your adaptive card JSON file:</span></span>

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
                "text": "For Samples and Templates, see [https://adaptivecards.io/samples](https://adaptivecards.io/samples)"
                }
            ]
         }
      }
   ]
}
```

> [!div class="checklist"]
>
> - <span data-ttu-id="a4e2a-167">Das Feld `"type"` muss vom Typ `"message"` sein.</span><span class="sxs-lookup"><span data-stu-id="a4e2a-167">The `"type"` field must be `"message"`.</span></span>
> - <span data-ttu-id="a4e2a-168">Das Array `"attachments"` enthält eine Reihe von Kartenobjekten.</span><span class="sxs-lookup"><span data-stu-id="a4e2a-168">The `"attachments"` array contains a set of card objects.</span></span>
> - <span data-ttu-id="a4e2a-169">Das Feld `"contentType"` muss auf den Typ „adaptive Karte“ festgelegt werden.</span><span class="sxs-lookup"><span data-stu-id="a4e2a-169">The `"contentType"` field must be set to adaptive card type.</span></span>
> - <span data-ttu-id="a4e2a-170">Das Objekt `"content"` ist die in JSON formatierte Karte.</span><span class="sxs-lookup"><span data-stu-id="a4e2a-170">The `"content"` object is the card formatted in JSON.</span></span>

<span data-ttu-id="a4e2a-171">**3.** Testen Ihrer adaptiven Karte mit Postman</span><span class="sxs-lookup"><span data-stu-id="a4e2a-171">**3.** Test your adaptive card with Postman</span></span>

<span data-ttu-id="a4e2a-172">Sie können Ihre adaptive Karte mithilfe von [Postman](https://www.postman.com) testen, um eine POST-Anforderung an die URL zu senden, die Sie beim Einrichten Ihres eingehenden Webhooks erstellt haben.</span><span class="sxs-lookup"><span data-stu-id="a4e2a-172">You can test your adaptive card using [Postman](https://www.postman.com) to send a POST request to the URL that you created when you setup your incoming webhook.</span></span> <span data-ttu-id="a4e2a-173">Fügen Sie Ihre JSON-Datei in den Textkörper der Anforderung ein, und zeigen Sie die Nachricht Ihrer adaptiven Karte in Teams an.</span><span class="sxs-lookup"><span data-stu-id="a4e2a-173">Paste your JSON file in the body of the request and view your adaptive card message in Teams.</span></span>

>[!TIP]
> <span data-ttu-id="a4e2a-174">Sie können den Code der adaptiven Karte [Beispiele und Vorlagen](https://adaptivecards.io/samples) für den Textkörper Ihrer POST-Testanforderung verwenden.</span><span class="sxs-lookup"><span data-stu-id="a4e2a-174">You can use adaptive card code [Samples and Templates](https://adaptivecards.io/samples) for the body of your test Post request.</span></span>

## <a name="testing-your-connector"></a><span data-ttu-id="a4e2a-175">Testen des Connectors</span><span class="sxs-lookup"><span data-stu-id="a4e2a-175">Testing your connector</span></span>

<span data-ttu-id="a4e2a-176">Um den Connector zu testen, laden Sie ihn wie jede andere App in ein Team hoch.</span><span class="sxs-lookup"><span data-stu-id="a4e2a-176">To test your Connector, upload it to a team as you would with any other app.</span></span> <span data-ttu-id="a4e2a-177">Sie können ein ZIP-Paket erstellen und dafür die (wie im vorherigen Abschnitt beschrieben modifizierte) Manifestdatei aus dem Entwicklerdashboard für Connectors sowie die beiden Symboldateien verwenden.</span><span class="sxs-lookup"><span data-stu-id="a4e2a-177">You can create a .zip package using the manifest file from the Connectors Developer Dashboard (modified as directed in the preceding section) and the two icon files.</span></span>

<span data-ttu-id="a4e2a-178">Nachdem Sie die App hochgeladen haben, öffnen Sie die Liste der Connectors von einem beliebigen Kanal aus.</span><span class="sxs-lookup"><span data-stu-id="a4e2a-178">After you upload the app, open the Connectors list from any channel.</span></span> <span data-ttu-id="a4e2a-179">Scrollen Sie ganz nach unten bis zu Ihrer App im Abschnitt **Hochgeladenen**.</span><span class="sxs-lookup"><span data-stu-id="a4e2a-179">Scroll to the bottom to see your app in the **Uploaded** section.</span></span>

![Screenshot des Abschnitts "Hochgeladen" im Connector-Dialogfeld](~/assets/images/connectors/connector_dialog_uploaded.png)

<span data-ttu-id="a4e2a-181">Sie können nun die Konfigurationsfunktion starten.</span><span class="sxs-lookup"><span data-stu-id="a4e2a-181">You can now launch the configuration experience.</span></span> <span data-ttu-id="a4e2a-182">Denken Sie daran, dass dieser Vorgang innerhalb von Microsoft Teams über ein Popupfenster erfolgt.</span><span class="sxs-lookup"><span data-stu-id="a4e2a-182">Be aware that this flow occurs entirely within Microsoft Teams through a pop-up window.</span></span> <span data-ttu-id="a4e2a-183">Derzeit unterscheidet sich dieses Verhalten von der Konfigurationsfunktion in den von uns erstellten Connectoren. Wir arbeiten an einer Vereinheitlichung der Benutzererfahrung.</span><span class="sxs-lookup"><span data-stu-id="a4e2a-183">Currently, this behavior differs from the configuration experience in Connectors that we created; we are working on unifying the experiences.</span></span>

<span data-ttu-id="a4e2a-184">Um zu überprüfen, ob eine `HttpPOST`-Aktion ordnungsgemäß funktioniert, verwenden Sie Ihren [benutzerdefinierten eingehenden Webhook](#setting-up-a-custom-incoming-webhook).</span><span class="sxs-lookup"><span data-stu-id="a4e2a-184">To verify that an `HttpPOST` action is working correctly, use your [custom incoming webhook](#setting-up-a-custom-incoming-webhook).</span></span>

## <a name="rate-limiting-for-connectors"></a><span data-ttu-id="a4e2a-185">Begrenzung der Datenübertragungsrate für Connectors</span><span class="sxs-lookup"><span data-stu-id="a4e2a-185">Rate limiting for connectors</span></span>

<span data-ttu-id="a4e2a-186">Die Grenzwerte für die Anwendungsdatenübertragungsrate steuern den Datenverkehr, der von einem Connector oder eingehenden Webhook in einem Kanal generiert werden darf.</span><span class="sxs-lookup"><span data-stu-id="a4e2a-186">Application rate limits control the traffic that a connector or an incoming webhook is allowed to generate on a channel.</span></span> <span data-ttu-id="a4e2a-187">Teams verfolgt Anforderungen über ein Fenster mit fester Datenübertragungsrate und einen inkrementellen Zähler, der in Sekunden gemessen wird.</span><span class="sxs-lookup"><span data-stu-id="a4e2a-187">Teams tracks requests via a fixed-rate window and incremental counter measured in seconds.</span></span>  <span data-ttu-id="a4e2a-188">Wenn zu viele Anforderungen gestellt werden, wird die Clientverbindung gedrosselt, bis das Fenster aktualisiert wird, d. h. für die Dauer der festen Datenübertragungsrate.</span><span class="sxs-lookup"><span data-stu-id="a4e2a-188">If too many requests are made, the client connection will be throttled until the window refreshes, i.e., for the duration of the fixed rate.</span></span>

### <a name="transactions-per-second-thresholds"></a><span data-ttu-id="a4e2a-189">**Schwellenwerte für Transaktionen pro Sekunde**</span><span class="sxs-lookup"><span data-stu-id="a4e2a-189">**Transactions per second thresholds**</span></span>

| <span data-ttu-id="a4e2a-190">Zeit (Sekunden)</span><span class="sxs-lookup"><span data-stu-id="a4e2a-190">Time (seconds)</span></span>  | <span data-ttu-id="a4e2a-191">Maximal zulässige Anforderungen</span><span class="sxs-lookup"><span data-stu-id="a4e2a-191">Maximum allowed requests</span></span>  |
|---|---|
| <span data-ttu-id="a4e2a-192">1</span><span class="sxs-lookup"><span data-stu-id="a4e2a-192">1</span></span>   | <span data-ttu-id="a4e2a-193">4</span><span class="sxs-lookup"><span data-stu-id="a4e2a-193">4</span></span>  |  
| <span data-ttu-id="a4e2a-194">30</span><span class="sxs-lookup"><span data-stu-id="a4e2a-194">30</span></span>   | <span data-ttu-id="a4e2a-195">60</span><span class="sxs-lookup"><span data-stu-id="a4e2a-195">60</span></span>  |  
| <span data-ttu-id="a4e2a-196">3600</span><span class="sxs-lookup"><span data-stu-id="a4e2a-196">3600</span></span>   | <span data-ttu-id="a4e2a-197">100</span><span class="sxs-lookup"><span data-stu-id="a4e2a-197">100</span></span>  |
| <span data-ttu-id="a4e2a-198">7200</span><span class="sxs-lookup"><span data-stu-id="a4e2a-198">7200</span></span> | <span data-ttu-id="a4e2a-199">150</span><span class="sxs-lookup"><span data-stu-id="a4e2a-199">150</span></span>  |
| <span data-ttu-id="a4e2a-200">86400</span><span class="sxs-lookup"><span data-stu-id="a4e2a-200">86400</span></span>  | <span data-ttu-id="a4e2a-201">1800</span><span class="sxs-lookup"><span data-stu-id="a4e2a-201">1800</span></span>  |

<span data-ttu-id="a4e2a-202">*Siehe auch* [Office 365-Connectors – Microsoft Teams](https://docs.microsoft.com/connectors/teams/)</span><span class="sxs-lookup"><span data-stu-id="a4e2a-202">*See also* [Office 365 Connectors — Microsoft Teams](https://docs.microsoft.com/connectors/teams/)</span></span>

<span data-ttu-id="a4e2a-203">Eine [Wiederholungslogik mit exponentiellem Backoff](/azure/architecture/patterns/retry) wie unten würde die Begrenzung der Datenübertragungsrate in Fällen abmildern, in denen Anforderungen die Grenzwerte innerhalb einer Sekunde überschreiten.</span><span class="sxs-lookup"><span data-stu-id="a4e2a-203">A [retry logic with exponential back-off](/azure/architecture/patterns/retry) like below would mitigate rate limiting for cases where requests are exceeding the limits within a second.</span></span> <span data-ttu-id="a4e2a-204">Lesen Sie die [HTTP 429-Antworten](../../bots/how-to/rate-limit.md#handle-http-429-responses), um zu vermeiden, dass die Ratenbegrenzungen überschritten werden.</span><span class="sxs-lookup"><span data-stu-id="a4e2a-204">Refer [HTTP 429 responses](../../bots/how-to/rate-limit.md#handle-http-429-responses) to avoid hitting the rate limits.</span></span>

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
 
<span data-ttu-id="a4e2a-205">Diese Limits haben den Zweck, das Spamming eines Kanals durch einen Connector zu verringern und Ihren Endbenutzer eine optimale Benutzererfahrung zu gewährleisten.</span><span class="sxs-lookup"><span data-stu-id="a4e2a-205">These limits are in place to reduce spamming a channel by a connector and ensures an optimal experience to your end users.</span></span>
