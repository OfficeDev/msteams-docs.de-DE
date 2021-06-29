---
title: Nachrichten erstellen und senden
author: laujan
description: Beschreibt die Verwendung von Office 365-Connectors in Microsoft Teams
ms.topic: how-to
localization_priority: Normal
keywords: Teams O365-Connector
ms.openlocfilehash: 8835e43ed74a8da5ad3b3b4358b259d63068b469
ms.sourcegitcommit: 85a52119df6c4cb4536572e6d2e7407f0e5e8a23
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/29/2021
ms.locfileid: "53179895"
---
# <a name="create-and-send-messages"></a><span data-ttu-id="d02bb-104">Nachrichten erstellen und senden</span><span class="sxs-lookup"><span data-stu-id="d02bb-104">Create and send messages</span></span>

<span data-ttu-id="d02bb-105">Sie können Nachrichten mit Aktionen erstellen und über eingehenden Webhook oder Office 365 Connector senden.</span><span class="sxs-lookup"><span data-stu-id="d02bb-105">You can create actionable messages and send it through Incoming Webhook or Office 365 Connector.</span></span>

## <a name="create-actionable-messages"></a><span data-ttu-id="d02bb-106">Erstellen von Nachrichten mit Aktionen</span><span class="sxs-lookup"><span data-stu-id="d02bb-106">Create actionable messages</span></span>

<span data-ttu-id="d02bb-107">Die Aktionen erfordernden Nachrichten enthalten drei sichtbare Schaltflächen auf der Karte.</span><span class="sxs-lookup"><span data-stu-id="d02bb-107">The actionable messages include three visible buttons on the card.</span></span> <span data-ttu-id="d02bb-108">Jede Schaltfläche wird in der `potentialAction` Eigenschaft der Nachricht mithilfe von Aktionen `ActionCard` definiert, die jeweils einen Eingabetyp, ein Textfeld, eine Datumsauswahl oder eine Mehrfachauswahlliste enthalten.</span><span class="sxs-lookup"><span data-stu-id="d02bb-108">Each button is defined in the `potentialAction` property of the message by using `ActionCard` actions, each with an input type, a text field, a date picker, or a multi-choice list.</span></span> <span data-ttu-id="d02bb-109">Jeder `ActionCard` hat eine zugeordnete Aktion, `HttpPOST` z. B. .</span><span class="sxs-lookup"><span data-stu-id="d02bb-109">Each `ActionCard` has an associated action, for example `HttpPOST`.</span></span>

<span data-ttu-id="d02bb-110">Die Connectorkarten unterstützen die folgenden Aktionen:</span><span class="sxs-lookup"><span data-stu-id="d02bb-110">The connector cards support the following actions:</span></span>

- <span data-ttu-id="d02bb-111">`ActionCard`: Stellt einen oder mehrere Eingabetypen und zugeordnete Aktionen dar.</span><span class="sxs-lookup"><span data-stu-id="d02bb-111">`ActionCard`: Presents one or more input types and associated actions.</span></span>
- <span data-ttu-id="d02bb-112">`HttpPOST`: Sendet die POST-Anforderung an eine URL.</span><span class="sxs-lookup"><span data-stu-id="d02bb-112">`HttpPOST`: Sends POST request to a URL.</span></span>
- <span data-ttu-id="d02bb-113">`OpenUri`: Öffnet den URI in einem separaten Browser oder einer separaten App und richtet sich optional auf unterschiedliche URIs basierend auf Betriebssystemen.</span><span class="sxs-lookup"><span data-stu-id="d02bb-113">`OpenUri`: Opens URI in a separate browser or app, optionally targets different URIs based on operating systems.</span></span>

<span data-ttu-id="d02bb-114">Die `ActionCard`-Aktion unterstützt drei Eingabetypen:</span><span class="sxs-lookup"><span data-stu-id="d02bb-114">The `ActionCard` action supports three input types:</span></span>

- <span data-ttu-id="d02bb-115">`TextInput`: Ein einzeiliges oder mehrzeiliges Textfeld mit optionaler Längenbeschränkung.</span><span class="sxs-lookup"><span data-stu-id="d02bb-115">`TextInput`: A single line or multiline text field with an optional length limit.</span></span>
- <span data-ttu-id="d02bb-116">`DateInput`: Eine Datumsauswahl mit einer optionalen Uhrzeitauswahl.</span><span class="sxs-lookup"><span data-stu-id="d02bb-116">`DateInput`: A date selector with an optional time selector.</span></span>
- <span data-ttu-id="d02bb-117">`MultichoiceInput`: Eine aufgezählte Liste von Auswahlmöglichkeiten, die entweder eine einzelne oder mehrere Auswahlmöglichkeiten bietet.</span><span class="sxs-lookup"><span data-stu-id="d02bb-117">`MultichoiceInput`: An enumerated list of choices offering either a single selection or multiple selections.</span></span>

<span data-ttu-id="d02bb-118">`MultichoiceInput` unterstützt eine `style`-Eigenschaft über die festgelegt wird, ob die Liste anfänglich vollständig erweitert angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="d02bb-118">`MultichoiceInput` supports a `style` property that controls whether the list initially appears fully expanded.</span></span> <span data-ttu-id="d02bb-119">Der Standardwert `style` von hängt vom Folgenden `isMultiSelect` ab:</span><span class="sxs-lookup"><span data-stu-id="d02bb-119">The default value of `style` depends on the value of `isMultiSelect` as follows:</span></span>

| `isMultiSelect` | <span data-ttu-id="d02bb-120">`style`-Standardeinstellung</span><span class="sxs-lookup"><span data-stu-id="d02bb-120">`style` default</span></span> |
| --- | --- |
| <span data-ttu-id="d02bb-121">`false` oder nicht angegeben</span><span class="sxs-lookup"><span data-stu-id="d02bb-121">`false` or not specified</span></span> | `compact` |
| `true` | `expanded` |

<span data-ttu-id="d02bb-122">Um die Mehrfachauswahlliste im kompakten Format anzuzeigen, müssen Sie beide `"isMultiSelect": true` und `"style": true` angeben.</span><span class="sxs-lookup"><span data-stu-id="d02bb-122">To display the multiselect list in the compact style, you must specify both `"isMultiSelect": true` and `"style": true`.</span></span>

<span data-ttu-id="d02bb-123">Weitere Informationen zu Connectorkartenaktionen finden Sie unter ["Aktionen".](/outlook/actionable-messages/card-reference#actions)</span><span class="sxs-lookup"><span data-stu-id="d02bb-123">For more information on connector card actions, see [Actions](/outlook/actionable-messages/card-reference#actions).</span></span>

> [!NOTE]
> * <span data-ttu-id="d02bb-124">Die Angabe von `compact` für die `style`-Eigenschaft in Microsoft Teams entspricht der Angabe von `normal` für die `style`-Eigenschaft in Microsoft Outlook.</span><span class="sxs-lookup"><span data-stu-id="d02bb-124">Specifying `compact` for the `style` property in Microsoft Teams is the same as specifying `normal` for the `style` property in Microsoft Outlook.</span></span>
> * <span data-ttu-id="d02bb-125">Bei der HttpPOST-Aktion ist das Bearertoken in den Anforderungen enthalten.</span><span class="sxs-lookup"><span data-stu-id="d02bb-125">For the HttpPOST action, the bearer token is included with the requests.</span></span> <span data-ttu-id="d02bb-126">Dieses Token enthält die Azure AD-Identität des Office 365-Benutzers, der die Aktion ausgeführt hat.</span><span class="sxs-lookup"><span data-stu-id="d02bb-126">This token includes the Azure AD identity of the Office 365 user who took the action.</span></span>

## <a name="send-a-message-through-incoming-webhook-or-office-365-connector"></a><span data-ttu-id="d02bb-127">Senden einer Nachricht über eingehenden Webhook oder Office 365 Connector</span><span class="sxs-lookup"><span data-stu-id="d02bb-127">Send a message through Incoming Webhook or Office 365 Connector</span></span>

<span data-ttu-id="d02bb-128">Um eine Nachricht über Ihren eingehenden Webhook oder Office 365 Connector zu senden, posten Sie eine JSON-Nutzlast an die Webhook-URL.</span><span class="sxs-lookup"><span data-stu-id="d02bb-128">To send a message through your Incoming Webhook or Office 365 Connector, post a JSON payload to the webhook URL.</span></span> <span data-ttu-id="d02bb-129">Diese Nutzlast muss in Form einer [Office 365 Connectorkarte](~/task-modules-and-cards/cards/cards-reference.md#office-365-connector-card)sein.</span><span class="sxs-lookup"><span data-stu-id="d02bb-129">This payload must be in the form of an [Office 365 connector card](~/task-modules-and-cards/cards/cards-reference.md#office-365-connector-card).</span></span>

<span data-ttu-id="d02bb-130">Sie können diesen JSON-Code auch verwenden, um Karten mit umfangreichen Eingaben zu erstellen, z. B. Texteingabe, Mehrfachauswahl oder Auswählen von Datum und Uhrzeit.</span><span class="sxs-lookup"><span data-stu-id="d02bb-130">You can also use this JSON to create cards containing rich inputs, such as text entry, multiselect, or selecting date and time.</span></span> <span data-ttu-id="d02bb-131">Der Code, der die Karte generiert und an die Webhook-URL sendet, kann auf jedem gehosteten Dienst ausgeführt werden.</span><span class="sxs-lookup"><span data-stu-id="d02bb-131">The code that generates the card and posts it to the webhook URL can run on any hosted service.</span></span> <span data-ttu-id="d02bb-132">Diese Karten werden als Teil von Nachrichten mit Aktionen definiert und auch in [Karten](~/task-modules-and-cards/what-are-cards.md)unterstützt, die in Teams Bots und Messaging-Erweiterungen verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="d02bb-132">These cards are defined as part of actionable messages and are also supported in [cards](~/task-modules-and-cards/what-are-cards.md), used in Teams bots and messaging extensions.</span></span>

### <a name="example-of-connector-message"></a><span data-ttu-id="d02bb-133">Beispiel für eine Connectornachricht</span><span class="sxs-lookup"><span data-stu-id="d02bb-133">Example of connector message</span></span>

<span data-ttu-id="d02bb-134">Ein Beispiel für eine Connectornachricht ist:</span><span class="sxs-lookup"><span data-stu-id="d02bb-134">An example of connector message is as follows:</span></span>

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

<span data-ttu-id="d02bb-135">Diese Nachricht enthält die folgende Karte im Kanal:</span><span class="sxs-lookup"><span data-stu-id="d02bb-135">This message provides the following card in the channel:</span></span>

![Screenshot einer Connectorkarte](~/assets/images/connectorcard.png)

## <a name="send-messages-using-curl-and-powershell"></a><span data-ttu-id="d02bb-137">Senden von Nachrichten mit cURL und PowerShell</span><span class="sxs-lookup"><span data-stu-id="d02bb-137">Send messages using cURL and PowerShell</span></span>

# <a name="curl"></a>[<span data-ttu-id="d02bb-138">Curl</span><span class="sxs-lookup"><span data-stu-id="d02bb-138">cURL</span></span>](#tab/cURL)

<span data-ttu-id="d02bb-139">**So posten Sie eine Nachricht im Webhook mit cURL**</span><span class="sxs-lookup"><span data-stu-id="d02bb-139">**To post a message in the webhook with cURL**</span></span>

1. <span data-ttu-id="d02bb-140">Installieren Sie cURL mithilfe von: https://curl.haxx.se/ .</span><span class="sxs-lookup"><span data-stu-id="d02bb-140">Install cURL using: https://curl.haxx.se/.</span></span>

1. <span data-ttu-id="d02bb-141">Geben Sie den folgenden cURL-Befehl in die Befehlszeile ein:</span><span class="sxs-lookup"><span data-stu-id="d02bb-141">From the command line, enter the following cURL command:</span></span>

   ```bash
   // on macOS or Linux
   curl -H 'Content-Type: application/json' -d '{"text": "Hello World"}' <YOUR WEBHOOK URL>
   ```

   ```bash
   // on Windows
   curl.exe -H "Content-Type:application/json" -d "{'text':'Hello World'}" <YOUR WEBHOOK URL>
   ```

    > [!NOTE]
    > <span data-ttu-id="d02bb-142">Wenn der POST erfolgreich ist, müssen Sie eine einfache Ausgabe von **1** `curl` sehen.</span><span class="sxs-lookup"><span data-stu-id="d02bb-142">If the POST succeeds, you must see a simple **1** output by `curl`.</span></span>

1. <span data-ttu-id="d02bb-143">Überprüfen Sie den Microsoft Teams-Client für die neue bereitgestellte Karte.</span><span class="sxs-lookup"><span data-stu-id="d02bb-143">Check the Microsoft Teams client for the new card posted.</span></span>

# <a name="powershell"></a>[<span data-ttu-id="d02bb-144">PowerShell</span><span class="sxs-lookup"><span data-stu-id="d02bb-144">PowerShell</span></span>](#tab/PowerShell)

 <span data-ttu-id="d02bb-145">Voraussetzung: Installation von PowerShell und Einarbeitung in die grundlegende Verwendung.</span><span class="sxs-lookup"><span data-stu-id="d02bb-145">Prerequisite: Installation of PowerShell and familiarization with its basic usage.</span></span>

<span data-ttu-id="d02bb-146">**So posten Sie eine Nachricht mit PowerShell an den Webhook**</span><span class="sxs-lookup"><span data-stu-id="d02bb-146">**To post a message to the webhook with PowerShell**</span></span>

1. <span data-ttu-id="d02bb-147">Geben Sie in der PowerShell-Eingabeaufforderung den folgenden Befehl ein:</span><span class="sxs-lookup"><span data-stu-id="d02bb-147">From the PowerShell prompt, enter the following command:</span></span>

   ```powershell
   Invoke-RestMethod -Method post -ContentType 'Application/Json' -Body '{"text":"Hello World!"}' -Uri <YOUR WEBHOOK URL>
   ```

    > [!NOTE]
    > <span data-ttu-id="d02bb-148">Wenn der POST erfolgreich ist, müssen Sie eine einfache Ausgabe von **1** `Invoke-RestMethod` sehen.</span><span class="sxs-lookup"><span data-stu-id="d02bb-148">If the POST succeeds, you must see a simple **1** output by `Invoke-RestMethod`.</span></span>

1. <span data-ttu-id="d02bb-149">Überprüfen Sie den Microsoft Teams-Kanal, der der Webhook-URL zugeordnet ist.</span><span class="sxs-lookup"><span data-stu-id="d02bb-149">Check the Microsoft Teams channel associated with the webhook URL.</span></span> <span data-ttu-id="d02bb-150">Sie können die neue Karte sehen, die im Kanal veröffentlicht wurde.</span><span class="sxs-lookup"><span data-stu-id="d02bb-150">You can see the new card posted to the channel.</span></span> <span data-ttu-id="d02bb-151">Bevor Sie den Connector zum Testen oder Veröffentlichen Ihrer App verwenden, müssen Sie folgendermaßen vorgehen:</span><span class="sxs-lookup"><span data-stu-id="d02bb-151">Before you use the connector to test or publish your app, you must do the following:</span></span>

    - <span data-ttu-id="d02bb-152">[Zwei Symbole einschließen](../../concepts/build-and-test/apps-package.md#app-icons).</span><span class="sxs-lookup"><span data-stu-id="d02bb-152">[Include two icons](../../concepts/build-and-test/apps-package.md#app-icons).</span></span>
    - <span data-ttu-id="d02bb-153">Ändern Sie den `icons` Teil des Manifests an die Dateinamen der Symbole anstelle von URLs.</span><span class="sxs-lookup"><span data-stu-id="d02bb-153">Modify the `icons` portion of the manifest to the file names of the icons instead of URLs.</span></span>

---

## <a name="send-adaptive-cards-using-an-incoming-webhook"></a><span data-ttu-id="d02bb-154">Senden adaptiver Karten mit einem eingehenden Webhook</span><span class="sxs-lookup"><span data-stu-id="d02bb-154">Send Adaptive Cards using an Incoming Webhook</span></span>

> [!NOTE]
> * <span data-ttu-id="d02bb-155">Alle systemeigenen Schemaelemente adaptiver Karten mit Ausnahme `Action.Submit` von , werden vollständig unterstützt.</span><span class="sxs-lookup"><span data-stu-id="d02bb-155">All native Adaptive Card schema elements, except `Action.Submit`, are fully supported.</span></span>
> * <span data-ttu-id="d02bb-156">Die unterstützten Aktionen sind [**Action.OpenURL**](https://adaptivecards.io/explorer/Action.OpenUrl.html), [**Action.ShowCard**](https://adaptivecards.io/explorer/Action.ShowCard.html)und [**Action.ToggleVisibility**](https://adaptivecards.io/explorer/Action.ToggleVisibility.html).</span><span class="sxs-lookup"><span data-stu-id="d02bb-156">The supported actions are [**Action.OpenURL**](https://adaptivecards.io/explorer/Action.OpenUrl.html), [**Action.ShowCard**](https://adaptivecards.io/explorer/Action.ShowCard.html), and [**Action.ToggleVisibility**](https://adaptivecards.io/explorer/Action.ToggleVisibility.html).</span></span>

<span data-ttu-id="d02bb-157">**So senden Sie adaptive Karten über einen eingehenden Webhook**</span><span class="sxs-lookup"><span data-stu-id="d02bb-157">**To send Adaptive Cards through an Incoming Webhook**</span></span>

1. <span data-ttu-id="d02bb-158">[Richten Sie einen benutzerdefinierten Webhook](~/webhooks-and-connectors/how-to/add-incoming-webhook.md) in Teams ein.</span><span class="sxs-lookup"><span data-stu-id="d02bb-158">[Setup a custom webhook](~/webhooks-and-connectors/how-to/add-incoming-webhook.md) in Teams.</span></span>
1. <span data-ttu-id="d02bb-159">Erstellen Sie die JSON-Datei für adaptive Karten mit dem folgenden Code:</span><span class="sxs-lookup"><span data-stu-id="d02bb-159">Create Adaptive Card JSON file using the following code:</span></span>

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

    <span data-ttu-id="d02bb-160">Die Eigenschaften für die JSON-Datei für adaptive Karten sind wie folgt:</span><span class="sxs-lookup"><span data-stu-id="d02bb-160">The properties for Adaptive Card JSON file are as follows:</span></span>

    * <span data-ttu-id="d02bb-161">Das Feld `"type"` muss vom Typ `"message"` sein.</span><span class="sxs-lookup"><span data-stu-id="d02bb-161">The `"type"` field must be `"message"`.</span></span>
    * <span data-ttu-id="d02bb-162">Das Array `"attachments"` enthält eine Reihe von Kartenobjekten.</span><span class="sxs-lookup"><span data-stu-id="d02bb-162">The `"attachments"` array contains a set of card objects.</span></span>
    * <span data-ttu-id="d02bb-163">Das `"contentType"` Feld muss auf den Typ "Adaptive Karte" festgelegt sein.</span><span class="sxs-lookup"><span data-stu-id="d02bb-163">The `"contentType"` field must be set to Adaptive Card type.</span></span>
    * <span data-ttu-id="d02bb-164">Das Objekt `"content"` ist die in JSON formatierte Karte.</span><span class="sxs-lookup"><span data-stu-id="d02bb-164">The `"content"` object is the card formatted in JSON.</span></span>

1. <span data-ttu-id="d02bb-165">Testen Sie Ihre adaptive Karte mit Postman:</span><span class="sxs-lookup"><span data-stu-id="d02bb-165">Test your Adaptive Card with Postman:</span></span>

    * <span data-ttu-id="d02bb-166">Testen Sie die adaptive Karte mit [Postman,](https://www.postman.com) um eine POST-Anforderung an die URL zu senden, die erstellt wurde, um eingehenden Webhook einzurichten.</span><span class="sxs-lookup"><span data-stu-id="d02bb-166">Test the Adaptive Card using [Postman](https://www.postman.com) to send a POST request to the URL, created to set up Incoming Webhook.</span></span>
    * <span data-ttu-id="d02bb-167">Fügen Sie die JSON-Datei in den Textkörper der Anforderung ein, und zeigen Sie die Adaptive Kartennachricht in Teams an.</span><span class="sxs-lookup"><span data-stu-id="d02bb-167">Paste the JSON file in the body of the request and view the Adaptive Card message in Teams.</span></span>

> [!TIP]
> <span data-ttu-id="d02bb-168">Verwenden Sie [Codebeispiele und Vorlagen](https://adaptivecards.io/samples) für adaptive Karten, um den Textkörper der POST-Anforderung zu testen.</span><span class="sxs-lookup"><span data-stu-id="d02bb-168">Use Adaptive Card [code samples and templates](https://adaptivecards.io/samples) to test the body of POST request.</span></span>

## <a name="rate-limiting-for-connectors"></a><span data-ttu-id="d02bb-169">Begrenzung der Datenübertragungsrate für Connectors</span><span class="sxs-lookup"><span data-stu-id="d02bb-169">Rate limiting for connectors</span></span>

<span data-ttu-id="d02bb-170">Anwendungsratenbeschränkungen steuern den Datenverkehr, den ein Connector oder ein eingehender Webhook in einem Kanal generieren darf.</span><span class="sxs-lookup"><span data-stu-id="d02bb-170">Application rate limits control the traffic that a connector or an Incoming Webhook is permitted to generate on a channel.</span></span> <span data-ttu-id="d02bb-171">Teams Anforderungen mithilfe eines Fensters mit fester Rate und eines inkrementellen Indikators in Sekunden nachverfolgen.</span><span class="sxs-lookup"><span data-stu-id="d02bb-171">Teams track requests using a fixed rate window and incremental counter measured in seconds.</span></span> <span data-ttu-id="d02bb-172">Wenn in einer Sekunde mehr als vier Anforderungen gestellt werden, wird die Clientverbindung gedrosselt, bis das Fenster für die Dauer der festen Rate aktualisiert wird.</span><span class="sxs-lookup"><span data-stu-id="d02bb-172">If more than four requests are made in a second, the client connection is throttled until the window refreshes for the duration of the fixed rate.</span></span>

### <a name="transactions-per-second-thresholds"></a><span data-ttu-id="d02bb-173">Schwellenwerte für Transaktionen pro Sekunde</span><span class="sxs-lookup"><span data-stu-id="d02bb-173">Transactions per second thresholds</span></span>

<span data-ttu-id="d02bb-174">Die folgende Tabelle enthält die zeitbasierten Transaktionsdetails:</span><span class="sxs-lookup"><span data-stu-id="d02bb-174">The following table provides the time based transaction details:</span></span>

| <span data-ttu-id="d02bb-175">Zeit in Sekunden</span><span class="sxs-lookup"><span data-stu-id="d02bb-175">Time in seconds</span></span>  | <span data-ttu-id="d02bb-176">Maximal zulässige Anforderungen</span><span class="sxs-lookup"><span data-stu-id="d02bb-176">Maximum allowed requests</span></span>  |
|---|---|
| <span data-ttu-id="d02bb-177">1 </span><span class="sxs-lookup"><span data-stu-id="d02bb-177">1</span></span>   | <span data-ttu-id="d02bb-178">4 </span><span class="sxs-lookup"><span data-stu-id="d02bb-178">4</span></span>  |  
| <span data-ttu-id="d02bb-179">30</span><span class="sxs-lookup"><span data-stu-id="d02bb-179">30</span></span>   | <span data-ttu-id="d02bb-180">60</span><span class="sxs-lookup"><span data-stu-id="d02bb-180">60</span></span>  |  
| <span data-ttu-id="d02bb-181">3600</span><span class="sxs-lookup"><span data-stu-id="d02bb-181">3600</span></span>   | <span data-ttu-id="d02bb-182">100</span><span class="sxs-lookup"><span data-stu-id="d02bb-182">100</span></span>  |
| <span data-ttu-id="d02bb-183">7200</span><span class="sxs-lookup"><span data-stu-id="d02bb-183">7200</span></span> | <span data-ttu-id="d02bb-184">150</span><span class="sxs-lookup"><span data-stu-id="d02bb-184">150</span></span>  |
| <span data-ttu-id="d02bb-185">86400</span><span class="sxs-lookup"><span data-stu-id="d02bb-185">86400</span></span>  | <span data-ttu-id="d02bb-186">1800</span><span class="sxs-lookup"><span data-stu-id="d02bb-186">1800</span></span>  |

<span data-ttu-id="d02bb-187">Eine [Wiederholungslogik mit exponentieller Back-Off](/azure/architecture/patterns/retry) kann die Ratenbegrenzung für Fälle verringern, in denen Anforderungen die Grenzwerte innerhalb einer Sekunde überschreiten.</span><span class="sxs-lookup"><span data-stu-id="d02bb-187">A [retry logic with exponential back-off](/azure/architecture/patterns/retry) can mitigate rate limiting for cases where requests are exceeding the limits within a second.</span></span> <span data-ttu-id="d02bb-188">Befolgen Sie [bewährte Methoden,](../../bots/how-to/rate-limit.md) um zu vermeiden, dass die Ratengrenzen erreicht werden.</span><span class="sxs-lookup"><span data-stu-id="d02bb-188">Follow [best practices](../../bots/how-to/rate-limit.md) to avoid hitting the rate limits.</span></span>

> [!NOTE]
> <span data-ttu-id="d02bb-189">Eine [Wiederholungslogik mit exponentieller Back-Off](/azure/architecture/patterns/retry) kann die Ratenbegrenzung für Fälle verringern, in denen Anforderungen die Grenzwerte innerhalb einer Sekunde überschreiten.</span><span class="sxs-lookup"><span data-stu-id="d02bb-189">A [retry logic with exponential back-off](/azure/architecture/patterns/retry) can mitigate rate limiting for cases where requests are exceeding the limits within a second.</span></span> <span data-ttu-id="d02bb-190">Lesen Sie die [HTTP 429-Antworten](../../bots/how-to/rate-limit.md#handle-http-429-responses), um zu vermeiden, dass die Ratenbegrenzungen überschritten werden.</span><span class="sxs-lookup"><span data-stu-id="d02bb-190">Refer [HTTP 429 responses](../../bots/how-to/rate-limit.md#handle-http-429-responses) to avoid hitting the rate limits.</span></span>

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

<span data-ttu-id="d02bb-191">Diese Grenzwerte sind vorhanden, um das Spamming eines Kanals über einen Connector zu reduzieren und eine optimale Benutzererfahrung sicherzustellen.</span><span class="sxs-lookup"><span data-stu-id="d02bb-191">These limits are in place to reduce spamming a channel by a connector and ensures an optimal experience to users.</span></span>

## <a name="see-also"></a><span data-ttu-id="d02bb-192">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="d02bb-192">See also</span></span>

* [<span data-ttu-id="d02bb-193">Office 365 Connectors für Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="d02bb-193">Office 365 Connectors for Microsoft Teams</span></span>](~/webhooks-and-connectors/how-to/connectors-creating.md)
* [<span data-ttu-id="d02bb-194">Erstellen eines eingehenden Webhooks</span><span class="sxs-lookup"><span data-stu-id="d02bb-194">Create an Incoming Webhook</span></span>](~/webhooks-and-connectors/how-to/add-incoming-webhook.md)
* [<span data-ttu-id="d02bb-195">Erstellen eines ausgehenden Webhooks</span><span class="sxs-lookup"><span data-stu-id="d02bb-195">Create an Outgoing Webhook</span></span>](~/webhooks-and-connectors/how-to/add-outgoing-webhook.md)
