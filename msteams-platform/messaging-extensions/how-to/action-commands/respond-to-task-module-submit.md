---
title: Reagieren auf die Absendenaktion des Aufgabenmoduls
author: clearab
description: Beschreibt, wie sie auf die Aktion zum Übermitteln des Aufgabenmoduls über einen Befehl für die Messagingerweiterungsaktion reagieren.
localization_priority: Normal
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: 3ed682eadde410a545f73768943a51ef95123e49
ms.sourcegitcommit: 825abed2f8784d2bab7407ba7a4455ae17bbd28f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/26/2021
ms.locfileid: "52019832"
---
# <a name="respond-to-the-task-module-submit-action"></a><span data-ttu-id="7bc09-103">Reagieren auf die Absendenaktion des Aufgabenmoduls</span><span class="sxs-lookup"><span data-stu-id="7bc09-103">Respond to the task module submit action</span></span>

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

<span data-ttu-id="7bc09-104">In diesem Dokument erfahren Sie, wie Ihre App auf die Aktionsbefehle reagiert, z. B. die Absendenaktion des Aufgabenmoduls des Benutzers.</span><span class="sxs-lookup"><span data-stu-id="7bc09-104">This document guides you on how your app responds to the action commands, such as user's task module submit action.</span></span>
<span data-ttu-id="7bc09-105">Nachdem ein Benutzer das Aufgabenmodul übermittelt hat, empfängt ihr Webdienst eine Aufrufnachricht mit der Befehls-ID `composeExtension/submitAction` und den Parameterwerten.</span><span class="sxs-lookup"><span data-stu-id="7bc09-105">After a user submits the task module, your web service receives a `composeExtension/submitAction` invoke message with the command ID and parameter values.</span></span> <span data-ttu-id="7bc09-106">Ihre App hat fünf Sekunden Zeit, um auf den Aufruf zu antworten, andernfalls erhält der Benutzer eine Fehlermeldung Nicht erreichbar, und alle Antworten auf den Aufruf werden vom client-Client Teams ignoriert.</span><span class="sxs-lookup"><span data-stu-id="7bc09-106">Your app has five seconds to respond to the invoke, otherwise the user receives an error message **Unable to reach the app**, and any reply to the invoke is ignored by the Teams client.</span></span>

<span data-ttu-id="7bc09-107">Sie haben die folgenden Optionen, um zu antworten:</span><span class="sxs-lookup"><span data-stu-id="7bc09-107">You have the following options to respond:</span></span>

* <span data-ttu-id="7bc09-108">Keine Antwort: Verwenden Sie die Submit-Aktion, um einen Prozess in einem externen System auszulösen, und geben Sie dem Benutzer kein Feedback.</span><span class="sxs-lookup"><span data-stu-id="7bc09-108">No response: Use the submit action to trigger a process in an external system, and not provide any feedback to the user.</span></span> <span data-ttu-id="7bc09-109">Dies ist nützlich für lange laufende Prozesse, und Sie können auswählen, ob Sie feedback abwechselnd bereitstellen möchten.</span><span class="sxs-lookup"><span data-stu-id="7bc09-109">This is useful for long-running processes, and you can select to provide feedback alternately.</span></span> <span data-ttu-id="7bc09-110">Beispielsweise können Sie Feedback mit einer proaktiven [Nachricht geben.](~/bots/how-to/conversations/send-proactive-messages.md)</span><span class="sxs-lookup"><span data-stu-id="7bc09-110">For example, you can give feedback with a [proactive message](~/bots/how-to/conversations/send-proactive-messages.md).</span></span>
* <span data-ttu-id="7bc09-111">[Ein weiteres Aufgabenmodul:](#respond-with-another-task-module)Sie können im Rahmen einer mehrstufigen Interaktion mit einem zusätzlichen Aufgabenmodul antworten.</span><span class="sxs-lookup"><span data-stu-id="7bc09-111">[Another task module](#respond-with-another-task-module): You can respond with an additional task module as part of a multi-step interaction.</span></span>
* <span data-ttu-id="7bc09-112">[Kartenantwort:](#respond-with-a-card-inserted-into-the-compose-message-area)Sie können mit einer Karte antworten, mit der der Benutzer interagieren oder in eine Nachricht einfügen kann.</span><span class="sxs-lookup"><span data-stu-id="7bc09-112">[Card response](#respond-with-a-card-inserted-into-the-compose-message-area): You can respond with a card that the user can interact with or insert into a message.</span></span>
* <span data-ttu-id="7bc09-113">[Adaptive Karte vom Bot:](#bot-response-with-adaptive-card)Fügen Sie eine adaptive Karte direkt in die Unterhaltung ein.</span><span class="sxs-lookup"><span data-stu-id="7bc09-113">[Adaptive Card from bot](#bot-response-with-adaptive-card): Insert an Adaptive Card directly into the conversation.</span></span>
* <span data-ttu-id="7bc09-114">[Fordern Sie den Benutzer zur Authentifizierung an.](~/messaging-extensions/how-to/add-authentication.md)</span><span class="sxs-lookup"><span data-stu-id="7bc09-114">[Request the user to authenticate](~/messaging-extensions/how-to/add-authentication.md).</span></span>
* <span data-ttu-id="7bc09-115">[Fordern Sie den Benutzer auf, eine zusätzliche Konfiguration zur Verfügung zu stellen.](~/messaging-extensions/how-to/add-configuration-page.md)</span><span class="sxs-lookup"><span data-stu-id="7bc09-115">[Request the user to provide additional configuration](~/messaging-extensions/how-to/add-configuration-page.md).</span></span>

<span data-ttu-id="7bc09-116">Für die Authentifizierung oder Konfiguration wird nach Abschluss des Vorgangs der ursprüngliche Aufruf an Den Webdienst erneut senden.</span><span class="sxs-lookup"><span data-stu-id="7bc09-116">For authentication or configuration, after the user completes the process, the original invoke is resent to your web service.</span></span> <span data-ttu-id="7bc09-117">Die folgende Tabelle zeigt, welche Arten von Antworten basierend auf dem Aufrufspeicherort der `commandContext` Messagingerweiterung verfügbar sind:</span><span class="sxs-lookup"><span data-stu-id="7bc09-117">The following table shows which types of responses are available based on the invoke location `commandContext` of the messaging extension:</span></span> 

|<span data-ttu-id="7bc09-118">Antworttyp</span><span class="sxs-lookup"><span data-stu-id="7bc09-118">Response Type</span></span> | <span data-ttu-id="7bc09-119">Verfassen</span><span class="sxs-lookup"><span data-stu-id="7bc09-119">Compose</span></span> | <span data-ttu-id="7bc09-120">Befehlsleiste</span><span class="sxs-lookup"><span data-stu-id="7bc09-120">Command bar</span></span> | <span data-ttu-id="7bc09-121">Message</span><span class="sxs-lookup"><span data-stu-id="7bc09-121">Message</span></span> |
|--------------|:-------------:|:-------------:|:---------:|
|<span data-ttu-id="7bc09-122">Kartenantwort</span><span class="sxs-lookup"><span data-stu-id="7bc09-122">Card response</span></span> | <span data-ttu-id="7bc09-123">✔</span><span class="sxs-lookup"><span data-stu-id="7bc09-123">✔</span></span> | <span data-ttu-id="7bc09-124">✔</span><span class="sxs-lookup"><span data-stu-id="7bc09-124">✔</span></span> | <span data-ttu-id="7bc09-125">✔</span><span class="sxs-lookup"><span data-stu-id="7bc09-125">✔</span></span> |
|<span data-ttu-id="7bc09-126">Ein weiteres Aufgabenmodul</span><span class="sxs-lookup"><span data-stu-id="7bc09-126">Another task module</span></span> | <span data-ttu-id="7bc09-127">✔</span><span class="sxs-lookup"><span data-stu-id="7bc09-127">✔</span></span> | <span data-ttu-id="7bc09-128">✔</span><span class="sxs-lookup"><span data-stu-id="7bc09-128">✔</span></span> | <span data-ttu-id="7bc09-129">✔</span><span class="sxs-lookup"><span data-stu-id="7bc09-129">✔</span></span> |
|<span data-ttu-id="7bc09-130">Bot mit adaptiver Karte</span><span class="sxs-lookup"><span data-stu-id="7bc09-130">Bot with Adaptive Card</span></span> | <span data-ttu-id="7bc09-131">✔</span><span class="sxs-lookup"><span data-stu-id="7bc09-131">✔</span></span> | <span data-ttu-id="7bc09-132">x</span><span class="sxs-lookup"><span data-stu-id="7bc09-132">x</span></span> | <span data-ttu-id="7bc09-133">✔</span><span class="sxs-lookup"><span data-stu-id="7bc09-133">✔</span></span> |
| <span data-ttu-id="7bc09-134">Keine Antwort</span><span class="sxs-lookup"><span data-stu-id="7bc09-134">No response</span></span> | <span data-ttu-id="7bc09-135">✔</span><span class="sxs-lookup"><span data-stu-id="7bc09-135">✔</span></span> | <span data-ttu-id="7bc09-136">✔</span><span class="sxs-lookup"><span data-stu-id="7bc09-136">✔</span></span> | <span data-ttu-id="7bc09-137">✔</span><span class="sxs-lookup"><span data-stu-id="7bc09-137">✔</span></span> |

> [!NOTE]
> * <span data-ttu-id="7bc09-138">Wenn Sie **Action.Submit** through ME-Karten auswählen, sendet sie aufrufaktivität mit dem Namen **composeExtension**, wobei der Wert der üblichen Nutzlast entspricht.</span><span class="sxs-lookup"><span data-stu-id="7bc09-138">When you select **Action.Submit** through ME cards, it sends invoke activity with the name **composeExtension**, where the value is equal to the usual payload.</span></span>
> * <span data-ttu-id="7bc09-139">Wenn Sie **Action.Submit** through conversation auswählen, erhalten Sie Nachrichtenaktivität mit dem Namen **onCardButtonClicked**, wobei der Wert der üblichen Nutzlast entspricht.</span><span class="sxs-lookup"><span data-stu-id="7bc09-139">When you select **Action.Submit** through conversation, you receive message activity with the name **onCardButtonClicked**, where the value is equal to the usual payload.</span></span>

## <a name="the-submitaction-invoke-event"></a><span data-ttu-id="7bc09-140">Das submitAction-Aufrufereignis</span><span class="sxs-lookup"><span data-stu-id="7bc09-140">The submitAction invoke event</span></span>

<span data-ttu-id="7bc09-141">Beispiele für den Empfang der aufrufenden Nachricht sind:</span><span class="sxs-lookup"><span data-stu-id="7bc09-141">Examples of receiving the invoke message are as follows:</span></span>

# <a name="cnet"></a>[<span data-ttu-id="7bc09-142">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="7bc09-142">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task<MessagingExtensionActionResponse> OnTeamsMessagingExtensionSubmitActionAsync(
  ITurnContext<IInvokeActivity> turnContext, MessagingExtensionAction action, CancellationToken cancellationToken) {
  //code to handle the submit action
}
```

# <a name="javascriptnodejs"></a>[<span data-ttu-id="7bc09-143">JavaScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="7bc09-143">JavaScript/Node.js</span></span>](#tab/javascript)

```javascript
class TeamsMessagingExtensionsActionPreview extends TeamsActivityHandler {
  constructor() {
  handleTeamsMessagingExtensionSubmitAction(context, action) {
  
  //code to handle the submit action
    }
  }
}
```

# <a name="json"></a>[<span data-ttu-id="7bc09-144">Json</span><span class="sxs-lookup"><span data-stu-id="7bc09-144">JSON</span></span>](#tab/json)

<span data-ttu-id="7bc09-145">Dies ist ein Beispiel für das JSON-Objekt, das Sie erhalten.</span><span class="sxs-lookup"><span data-stu-id="7bc09-145">This is an example of the JSON object that you receive.</span></span> <span data-ttu-id="7bc09-146">Der `commandContext` Parameter gibt an, von wo ihre Messagingerweiterung ausgelöst wurde.</span><span class="sxs-lookup"><span data-stu-id="7bc09-146">The `commandContext` parameter indicates where your messaging extension was triggered from.</span></span> <span data-ttu-id="7bc09-147">Das Objekt enthält die Felder im Formular als Parameter und die `data` vom Benutzer übermittelten Werte.</span><span class="sxs-lookup"><span data-stu-id="7bc09-147">The `data` object contains the fields on the form as parameters, and the values the user submitted.</span></span> <span data-ttu-id="7bc09-148">Das hier gezeigte JSON-Objekt wird verkürzt, um die relevantesten Felder zu markieren.</span><span class="sxs-lookup"><span data-stu-id="7bc09-148">The JSON object here is shortened to highlight the most relevant fields.</span></span>

```json
{
  "name": "composeExtension/submitAction",
  "imdisplayname": "Bob Smith",
  "serviceUrl": "https://smba.trafficmanager.net/amer/",
  "value": {
    "commandId": "giveKudos",
    "commandContext": "compose",
    "context": {
      "theme": "default"
    },
    "data": {
      "id": "submitButton",
      "formField1": "formField1_value",
      "formField2": "formField2_value",
      "formField3": "formField3_value"
    }
  },
  "conversation": {
    "id": "19:7705841b240044b297123ad7f9c99217@thread.skype"
  }
}
```

* * *

## <a name="respond-with-a-card-inserted-into-the-compose-message-area"></a><span data-ttu-id="7bc09-149">Antworten mit einer Karte, die in den Bereich "Verfassen von Nachrichten" eingefügt wurde</span><span class="sxs-lookup"><span data-stu-id="7bc09-149">Respond with a card inserted into the compose message area</span></span>

<span data-ttu-id="7bc09-150">Die häufigste Möglichkeit, auf die Anforderung zu reagieren, ist eine Karte, die in den Bereich "Verfassen `composeExtension/submitAction` von Nachrichten" eingefügt wird.</span><span class="sxs-lookup"><span data-stu-id="7bc09-150">The most common way to respond to the `composeExtension/submitAction` request is with a card inserted into the compose message area.</span></span> <span data-ttu-id="7bc09-151">Der Benutzer sendet die Karte an die Unterhaltung.</span><span class="sxs-lookup"><span data-stu-id="7bc09-151">The user submits the card to the conversation.</span></span> <span data-ttu-id="7bc09-152">Weitere Informationen zur Verwendung von Karten finden Sie unter [Karten und Kartenaktionen](~/task-modules-and-cards/cards/cards-actions.md).</span><span class="sxs-lookup"><span data-stu-id="7bc09-152">For more information on using cards, see [cards and card actions](~/task-modules-and-cards/cards/cards-actions.md).</span></span>

# <a name="cnet"></a>[<span data-ttu-id="7bc09-153">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="7bc09-153">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task<MessagingExtensionActionResponse> OnTeamsMessagingExtensionSubmitActionAsync(
  ITurnContext<IInvokeActivity> turnContext, MessagingExtensionAction action, CancellationToken cancellationToken)
{
    var response = new MessagingExtensionActionResponse
    {
        ComposeExtension = new MessagingExtensionResult
        {
            AttachmentLayout = "list",
            Type = "result",
        },
    };
    var createCardData = ((JObject)action.Data).ToObject<CreateCardData>();
var card = new HeroCard
{
     Title = createCardData.Title,
     Subtitle = createCardData.Subtitle,
     Text = createCardData.Text,
};
    var attachments = new List<MessagingExtensionAttachment>();
    attachments.Add(new MessagingExtensionAttachment
    {
        Content = card,
        ContentType = HeroCard.ContentType,
        Preview = card.ToAttachment(),
    });
    response.ComposeExtension.Attachments = attachments;
    return response;
}
```

# <a name="javascriptnodejs"></a>[<span data-ttu-id="7bc09-154">JavaScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="7bc09-154">JavaScript/Node.js</span></span>](#tab/javascript)

```javascript
class TeamsMessagingExtensionsActionPreview extends TeamsActivityHandler {
  handleTeamsMessagingExtensionSubmitAction(context, action) {
    const data = action.data;
    const heroCard = CardFactory.heroCard(data.title, data.text);
    heroCard.content.subtitle = data.subTitle;
    const attachment = { contentType: heroCard.contentType, content: heroCard.content, preview: heroCard };

    return {
      composeExtension: {
        type: 'result',
        attachmentLayout: 'list',
        attachments: [
          attachment
        ]
      }
    }
  }
}
```

# <a name="json"></a>[<span data-ttu-id="7bc09-155">Json</span><span class="sxs-lookup"><span data-stu-id="7bc09-155">JSON</span></span>](#tab/json)

```json
{
  "composeExtension": {
    "attachmentLayout": "list",
    "type": "result",
    "attachments": [
      {
        "preview": {
          "contentType": "application/vnd.microsoft.card.hero",
          "content": {
            "title": "formField1_value",
            "subtitle": "formField2_value",
            "text": "formField3_value"
          }
        },
        "contentType": "application/vnd.microsoft.card.hero",
        "content": {
          "title": "formField1_value",
          "subtitle": "formField2_value",
          "text": "formField3_value"
        }
      }
    ]
  }
}
```

* * *

## <a name="respond-with-another-task-module"></a><span data-ttu-id="7bc09-156">Reagieren mit einem anderen Aufgabenmodul</span><span class="sxs-lookup"><span data-stu-id="7bc09-156">Respond with another task module</span></span>

<span data-ttu-id="7bc09-157">Sie können auswählen, ob sie mit einem `submitAction` zusätzlichen Aufgabenmodul auf das Ereignis reagieren möchten.</span><span class="sxs-lookup"><span data-stu-id="7bc09-157">You can select to respond to the `submitAction` event with an additional task module.</span></span> <span data-ttu-id="7bc09-158">Dies ist nützlich, wenn:</span><span class="sxs-lookup"><span data-stu-id="7bc09-158">This is useful when:</span></span>

* <span data-ttu-id="7bc09-159">Sie müssen große Mengen von Informationen sammeln.</span><span class="sxs-lookup"><span data-stu-id="7bc09-159">You need to collect large amounts of information.</span></span>
* <span data-ttu-id="7bc09-160">Sie müssen die von Ihnen gesammelten Informationen basierend auf benutzerbezogenen Eingaben dynamisch ändern.</span><span class="sxs-lookup"><span data-stu-id="7bc09-160">You need to dynamically change the information you are collecting based on user input.</span></span>
* <span data-ttu-id="7bc09-161">Sie müssen die vom Benutzer übermittelten Informationen überprüfen und das Formular erneut mit einer Fehlermeldung senden, wenn etwas nicht stimmt.</span><span class="sxs-lookup"><span data-stu-id="7bc09-161">You need to validate the information submitted by the user and resend the form with an error message if something is wrong.</span></span> 

<span data-ttu-id="7bc09-162">Die Methode für die Antwort ist identisch mit der [Antwort auf das ursprüngliche `fetchTask` Ereignis](~/messaging-extensions/how-to/action-commands/create-task-module.md).</span><span class="sxs-lookup"><span data-stu-id="7bc09-162">The method for response is the same as [responding to the initial `fetchTask` event](~/messaging-extensions/how-to/action-commands/create-task-module.md).</span></span> <span data-ttu-id="7bc09-163">Wenn Sie das Bot Framework SDK verwenden, werden für beide Absendenaktionen dieselben Ereignisauslöser ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="7bc09-163">If you are using the Bot Framework SDK the same event triggers for both submit actions.</span></span> <span data-ttu-id="7bc09-164">Damit dies funktioniert, müssen Sie logik hinzufügen, die die richtige Antwort bestimmt.</span><span class="sxs-lookup"><span data-stu-id="7bc09-164">To make this work, you must add logic that determines the correct response.</span></span>

## <a name="bot-response-with-adaptive-card"></a><span data-ttu-id="7bc09-165">Botantwort mit adaptiver Karte</span><span class="sxs-lookup"><span data-stu-id="7bc09-165">Bot response with Adaptive Card</span></span>

> [!NOTE]
> <span data-ttu-id="7bc09-166">Die Voraussetzung für das Erhalten der Botantwort mit einer adaptiven Karte ist, dass Sie das Objekt zu Ihrem App-Manifest hinzufügen und den erforderlichen Bereich für `bot` den Bot definieren müssen.</span><span class="sxs-lookup"><span data-stu-id="7bc09-166">The prerequisite to get the bot response with an Adaptive card is that you must add the `bot` object to your app manifest, and define the required scope for the bot.</span></span> <span data-ttu-id="7bc09-167">Verwenden Sie die gleiche ID wie Ihre Messagingerweiterung für Ihren Bot.</span><span class="sxs-lookup"><span data-stu-id="7bc09-167">Use the same ID as your messaging extension for your bot.</span></span>
 
<span data-ttu-id="7bc09-168">Sie können auch darauf reagieren, indem Sie eine Nachricht mit einer adaptiven Karte in den Kanal mit `submitAction` einem Bot einfügen.</span><span class="sxs-lookup"><span data-stu-id="7bc09-168">You can also respond to the `submitAction` by inserting a message with an Adaptive Card into the channel with a bot.</span></span> <span data-ttu-id="7bc09-169">Der Benutzer kann eine Vorschau der Nachricht anzeigen, bevor er sie übermittelt.</span><span class="sxs-lookup"><span data-stu-id="7bc09-169">The user can preview the message before submitting it.</span></span> <span data-ttu-id="7bc09-170">Dies ist sehr nützlich in Szenarien, in denen Sie Informationen von den Benutzern sammeln, bevor Sie eine Adaptive Card-Antwort erstellen, oder wenn Sie die Karte aktualisieren, nachdem jemand mit ihr interagiert hat.</span><span class="sxs-lookup"><span data-stu-id="7bc09-170">This is very useful in scenarios where you gather information from the users before creating an Adaptive Card response, or when you update the card after someone interacts with it.</span></span> 

<span data-ttu-id="7bc09-171">Das folgende Szenario zeigt, wie die App Polly eine Umfrage konfiguriert, ohne die Konfigurationsschritte in die Kanalunterhaltung zu verwenden:</span><span class="sxs-lookup"><span data-stu-id="7bc09-171">The following scenario shows how the app Polly configures a poll without including the configuration steps in the channel conversation:</span></span>

<span data-ttu-id="7bc09-172">**So konfigurieren Sie die Abfrage**</span><span class="sxs-lookup"><span data-stu-id="7bc09-172">**To configure the poll**</span></span>

1. <span data-ttu-id="7bc09-173">Der Benutzer wählt die Messagingerweiterung zum Aufrufen des Aufgabenmoduls aus.</span><span class="sxs-lookup"><span data-stu-id="7bc09-173">The user selects the messaging extension to invoke the task module.</span></span>
1. <span data-ttu-id="7bc09-174">Der Benutzer konfiguriert die Abfrage mit dem Aufgabenmodul.</span><span class="sxs-lookup"><span data-stu-id="7bc09-174">The user configures the poll with the task module.</span></span>
1. <span data-ttu-id="7bc09-175">Nach dem Übermitteln des Aufgabenmoduls verwendet die App die bereitgestellten Informationen, um die Umfrage als adaptive Karte zu erstellen, und sendet sie als Antwort `botMessagePreview` an den Client.</span><span class="sxs-lookup"><span data-stu-id="7bc09-175">After submitting the task module, the app uses the information provided to build the poll as an Adaptive Card and sends it as a `botMessagePreview` response to the client.</span></span>
1. <span data-ttu-id="7bc09-176">Der Benutzer kann dann eine Vorschau der Adaptive Card-Nachricht anzeigen, bevor der Bot sie in den Kanal einfüge.</span><span class="sxs-lookup"><span data-stu-id="7bc09-176">The user can then preview the Adaptive Card message before the bot inserts it into the channel.</span></span> <span data-ttu-id="7bc09-177">Wenn die App noch kein Mitglied des Kanals ist, wählen Sie aus, `Send` um sie hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="7bc09-177">If the app is not already a member of the channel, select `Send` to add it.</span></span>

    > [!NOTE] 
    > * <span data-ttu-id="7bc09-178">Die Benutzer können auch die Nachricht `Edit` auswählen, die sie an das ursprüngliche Aufgabenmodul zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="7bc09-178">The users can also select to `Edit` the message, which returns them to the original task module.</span></span> 
    > * <span data-ttu-id="7bc09-179">Durch die Interaktion mit der adaptiven Karte wird die Nachricht vor dem Senden geändert.</span><span class="sxs-lookup"><span data-stu-id="7bc09-179">Interaction with the Adaptive Card changes the message before sending it.</span></span>
1. <span data-ttu-id="7bc09-180">Nachdem der Benutzer den `Send` Bot ausgewählt hat, wird die Nachricht an den Kanal gesendet.</span><span class="sxs-lookup"><span data-stu-id="7bc09-180">After the user selects `Send` the bot posts the message to the channel.</span></span>

## <a name="respond-to-initial-submit-action"></a><span data-ttu-id="7bc09-181">Reagieren auf erste Absendenaktion</span><span class="sxs-lookup"><span data-stu-id="7bc09-181">Respond to initial submit action</span></span>

<span data-ttu-id="7bc09-182">Ihr Aufgabenmodul muss auf die anfängliche Nachricht mit einer Vorschau der Karte reagieren, die der `composeExtension/submitAction` Bot an den Kanal sendet.</span><span class="sxs-lookup"><span data-stu-id="7bc09-182">Your task module must respond to the initial `composeExtension/submitAction` message with a preview of the card that the bot sends to the channel.</span></span> <span data-ttu-id="7bc09-183">Der Benutzer kann die Karte vor dem Senden überprüfen und auch versuchen, den Bot in der Unterhaltung zu installieren, wenn der Bot noch nicht installiert ist.</span><span class="sxs-lookup"><span data-stu-id="7bc09-183">The user can verify the card before sending, and also try to install your bot in the conversation if the bot is not already installed.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="7bc09-184">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="7bc09-184">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task<MessagingExtensionActionResponse> OnTeamsMessagingExtensionSubmitActionAsync(
  ITurnContext<IInvokeActivity> turnContext, MessagingExtensionAction action, CancellationToken cancellationToken)
{
  dynamic createCardData = ((JObject) action.Data).ToObject(typeof(JObject));
  var response = new MessagingExtensionActionResponse
  {
    ComposeExtension = new MessagingExtensionResult
    {
      Type = "botMessagePreview",
      ActivityPreview = MessageFactory.Attachment(new Attachment
      {
        Content = new AdaptiveCard("1.0")
        {
          Body = new List<AdaptiveElement>()
          {
            new AdaptiveTextBlock() { Text = "FormField1 value was:", Size = AdaptiveTextSize.Large },
            new AdaptiveTextBlock() { Text = Data["FormField1"] as string }
          },
          Height = AdaptiveHeight.Auto,
          Actions = new List<AdaptiveAction>()
          {
            new AdaptiveSubmitAction
            {
              Type = AdaptiveSubmitAction.TypeName,
              Title = "Submit",
              Data = new JObject { { "submitLocation", "messagingExtensionFetchTask" } },
            },
          }
        },
        ContentType = AdaptiveCard.ContentType
      }) as Activity
    }
  };

  return response;
}
```

# <a name="javascriptnodejs"></a>[<span data-ttu-id="7bc09-185">JavaScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="7bc09-185">JavaScript/Node.js</span></span>](#tab/javascript)

```javascript
class TeamsMessagingExtensionsActionPreview extends TeamsActivityHandler {
  handleTeamsMessagingExtensionSubmitAction(context, action) {
    const submittedData = action.data;
    const adaptiveCard = CardFactory.adaptiveCard({
      actions: [
        { type: 'Action.Submit', title: 'Submit', data: { submitLocation: 'messagingExtensionSubmit' } }
      ],
      body: [
          { text: 'Adaptive Card from Task Module', type: 'TextBlock', weight: 'bolder' },
          { text: `${ submittedData.Question }`, type: 'TextBlock', id: 'Question' },
          { id: 'Answer', placeholder: 'Answer here...', type: 'Input.Text' },
        {
          choices: [
            { title: submittedData.Option1, value: submittedData.Option1 },
            { title: submittedData.Option2, value: submittedData.Option2 },
            { title: submittedData.Option3, value: submittedData.Option3 }
          ],
          id: 'Choices',
          isMultiSelect: submittedData.MultiSelect,
          style: 'expanded',
          type: 'Input.ChoiceSet'
        }
      ],
      type: 'AdaptiveCard',
      version: '1.0'
    });
    return {
      composeExtension: {
        activityPreview: MessageFactory.attachment(adaptiveCard, null, null, InputHints.ExpectingInput),
        type: 'botMessagePreview'
      }
    };
  }
}
```

# <a name="json"></a>[<span data-ttu-id="7bc09-186">Json</span><span class="sxs-lookup"><span data-stu-id="7bc09-186">JSON</span></span>](#tab/json)

> [!NOTE]
> * <span data-ttu-id="7bc09-187">Der `activityPreview` muss eine Aktivität mit genau einer `message` adaptiven Kartenanlage enthalten.</span><span class="sxs-lookup"><span data-stu-id="7bc09-187">The `activityPreview` must contain a `message` activity with exactly one Adaptive Card attachment.</span></span> <span data-ttu-id="7bc09-188">Der `<< Card Payload >>` Wert ist ein Platzhalter für die Karte, die Sie senden möchten.</span><span class="sxs-lookup"><span data-stu-id="7bc09-188">The `<< Card Payload >>` value is a placeholder for the card you want to send.</span></span>

```json
{
  "composeExtension": {
    "type": "botMessagePreview",
    "activityPreview": {
      "type": "message",
      "attachments":  [
        {
          "contentType": "application/vnd.microsoft.card.adaptive",
          "content": << Card Payload >>
        }
      ]
    }
  }
}
```

* * *

### <a name="the-botmessagepreview-send-and-edit-events"></a><span data-ttu-id="7bc09-189">Die BotMessagePreview-Sende- und -Bearbeitungsereignisse</span><span class="sxs-lookup"><span data-stu-id="7bc09-189">The botMessagePreview send and edit events</span></span>

<span data-ttu-id="7bc09-190">Ihre Messagingerweiterung muss auf zwei neue Arten des Aufrufs `composeExtension/submitAction` reagieren, wobei `value.botMessagePreviewAction = "send"` und `value.botMessagePreviewAction = "edit"` .</span><span class="sxs-lookup"><span data-stu-id="7bc09-190">Your messaging extension must respond to two new types of the `composeExtension/submitAction` invoke, where `value.botMessagePreviewAction = "send"`and `value.botMessagePreviewAction = "edit"`.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="7bc09-191">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="7bc09-191">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task<MessagingExtensionActionResponse> OnTeamsMessagingExtensionBotMessagePreviewEditAsync(
  ITurnContext<IInvokeActivity> turnContext, MessagingExtensionAction action, CancellationToken cancellationToken)
{
  //handle the event
}

protected override async Task<MessagingExtensionActionResponse> OnTeamsMessagingExtensionBotMessagePreviewSendAsync(
  ITurnContext<IInvokeActivity> turnContext, MessagingExtensionAction action, CancellationToken cancellationToken)
{
  //handle the event
}

```

# <a name="javascriptnodejs"></a>[<span data-ttu-id="7bc09-192">JavaScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="7bc09-192">JavaScript/Node.js</span></span>](#tab/javascript)

```javascript
class TeamsMessagingExtensionsActionPreview extends TeamsActivityHandler {
  handleTeamsMessagingExtensionBotMessagePreviewEdit(context, action) {

    //handle the event
  }
  
  handleTeamsMessagingExtensionBotMessagePreviewSend(context, action) {

    //handle the event
  }
}

```

# <a name="json"></a>[<span data-ttu-id="7bc09-193">Json</span><span class="sxs-lookup"><span data-stu-id="7bc09-193">JSON</span></span>](#tab/json)

```json
{
  "name": "composeExtension/submitAction",
  "type": "invoke",
  "conversation": { "id": "19:c366b75791784100b6e8b515fd55b063@thread.skype" },
  "imdisplayname": "Pranav Smith",
  ...
  "value": {
    "botMessagePreviewAction": "edit | send",
    "botActivityPreview": [
      {
        "type": "message/card",
        "attachments": [
          {
            "content":
              {
                "type": "AdaptiveCard",
                "body": [{<<card payload>>}]
              },
            "contentType" : "application/vnd.microsoft.card.adaptive"
          }
        ],
        "context": { "theme": "default" }
      }
    ],
  }
}
```

* * *

### <a name="respond-to-botmessagepreview-edit"></a><span data-ttu-id="7bc09-194">Reagieren auf botMessagePreview-Bearbeitung</span><span class="sxs-lookup"><span data-stu-id="7bc09-194">Respond to botMessagePreview edit</span></span>

<span data-ttu-id="7bc09-195">Wenn der Benutzer die Karte vor dem Senden bearbeitet, erhalten Sie durch Auswählen von **Bearbeiten** einen `composeExtension/submitAction` Aufruf mit `value.botMessagePreviewAction = edit` .</span><span class="sxs-lookup"><span data-stu-id="7bc09-195">If the user edits the card before sending, by selecting **Edit**, you receive a `composeExtension/submitAction` invoke with `value.botMessagePreviewAction = edit`.</span></span> <span data-ttu-id="7bc09-196">Sie müssen antworten, indem Sie das gesendete Aufgabenmodul als Antwort auf den anfänglichen Aufruf zurückgeben, `composeExtension/fetchTask` mit dem die Interaktion begonnen hat.</span><span class="sxs-lookup"><span data-stu-id="7bc09-196">You must respond by returning the task module you sent, in response to the initial `composeExtension/fetchTask` invoke that began the interaction.</span></span> <span data-ttu-id="7bc09-197">Dadurch kann der Benutzer den Prozess durch erneutes Eingeben der ursprünglichen Informationen starten.</span><span class="sxs-lookup"><span data-stu-id="7bc09-197">This allows the user to start the process by re-entering the original information.</span></span> <span data-ttu-id="7bc09-198">Verwenden Sie die verfügbaren Informationen, um das Aufgabenmodul so zu aktualisieren, dass der Benutzer nicht alle Informationen von Grund auf ausfüllen muss.</span><span class="sxs-lookup"><span data-stu-id="7bc09-198">Use the available information to update the task module so that the user need not fill out all information from scratch.</span></span>
<span data-ttu-id="7bc09-199">Weitere Informationen zum Reagieren auf das ursprüngliche Ereignis `fetchTask` finden Sie unter [responding to the initial `fetchTask` event](~/messaging-extensions/how-to/action-commands/create-task-module.md).</span><span class="sxs-lookup"><span data-stu-id="7bc09-199">For more information on responding to the initial `fetchTask` event, see [responding to the initial `fetchTask` event](~/messaging-extensions/how-to/action-commands/create-task-module.md).</span></span>

### <a name="respond-to-botmessagepreview-send"></a><span data-ttu-id="7bc09-200">Reagieren auf botMessagePreview send</span><span class="sxs-lookup"><span data-stu-id="7bc09-200">Respond to botMessagePreview send</span></span>

<span data-ttu-id="7bc09-201">Nachdem der Benutzer die Option **Senden ausgewählt** hat, erhalten Sie einen Aufruf `composeExtension/submitAction` mit `value.botMessagePreviewAction = send` .</span><span class="sxs-lookup"><span data-stu-id="7bc09-201">After the user selects the **Send**, you receive a `composeExtension/submitAction` invoke with `value.botMessagePreviewAction = send`.</span></span> <span data-ttu-id="7bc09-202">Ihr Webdienst muss eine proaktive Nachricht mit der adaptiven Karte an die Unterhaltung erstellen und senden und auch auf den Aufruf antworten.</span><span class="sxs-lookup"><span data-stu-id="7bc09-202">Your web service has to create and send a proactive message with the Adaptive Card to the conversation, and also reply to the invoke.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="7bc09-203">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="7bc09-203">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task<MessagingExtensionActionResponse> OnTeamsMessagingExtensionBotMessagePreviewSendAsync(
  ITurnContext<IInvokeActivity> turnContext, MessagingExtensionAction action, CancellationToken cancellationToken)
{
  var activityPreview = action.BotActivityPreview[0];
  var attachmentContent = activityPreview.Attachments[0].Content;
  var previewedCard = JsonConvert.DeserializeObject<AdaptiveCard>(attachmentContent.ToString(),
          new JsonSerializerSettings { NullValueHandling = NullValueHandling.Ignore });
  
  previewedCard.Version = "1.0";

  var responseActivity = Activity.CreateMessageActivity();
  Attachment attachment = new Attachment()
  {
    ContentType = AdaptiveCard.ContentType,
    Content = previewedCard
  };
  responseActivity.Attachments.Add(attachment);
  
  // Attribute the message to the user on whose behalf the bot is posting
  responseActivity.ChannelData = new {
    OnBehalfOf = new []
    {
      new
      {
        ItemId = 0,
        MentionType = "person",
        Mri = turnContext.Activity.From.Id,
        DisplayName = turnContext.Activity.From.Name
      }  
    }
  };
  
  await turnContext.SendActivityAsync(responseActivity);

  return new MessagingExtensionActionResponse();
}
```

# <a name="javascriptnodejs"></a>[<span data-ttu-id="7bc09-204">JavaScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="7bc09-204">JavaScript/Node.js</span></span>](#tab/javascript)

```javascript
class TeamsMessagingExtensionsActionPreview extends TeamsActivityHandler {
    async handleTeamsMessagingExtensionBotMessagePreviewSend(context, action) {
      // The data has been returned to the bot in the action structure.
      const activityPreview = action.botActivityPreview[0];
      const attachmentContent = activityPreview.attachments[0].content;
      const userText = attachmentContent.body[1].text;
      const choiceSet = attachmentContent.body[3];

      const submitData = {
        MultiSelect: choiceSet.isMultiSelect ? 'true' : 'false',
        Option1: choiceSet.choices[0].title,
        Option2: choiceSet.choices[1].title,
        Option3: choiceSet.choices[2].title,
        Question: userText
      };

      const adaptiveCard = CardFactory.adaptiveCard({
        actions: [
          { type: 'Action.Submit', title: 'Submit', data: { submitLocation: 'messagingExtensionSubmit' } }
        ],
        body: [
          { text: 'Adaptive Card from Task Module', type: 'TextBlock', weight: 'bolder' },
          { text: `${ submitData.Question }`, type: 'TextBlock', id: 'Question' },
          { id: 'Answer', placeholder: 'Answer here...', type: 'Input.Text' },
          {
            choices: [
                { title: submitData.Option1, value: submitData.Option1 },
                { title: submitData.Option2, value: submitData.Option2 },
                { title: submitData.Option3, value: submitData.Option3 }
            ],
            id: 'Choices',
            isMultiSelect: submitData.MultiSelect,
            style: 'expanded',
            type: 'Input.ChoiceSet'
          }
        ],
        type: 'AdaptiveCard',
        version: '1.0'
      });
      const responseActivity = { type: 'message', attachments: [adaptiveCard], channelData: {
          onBehalfOf: [
              { itemId: 0, mentionType: 'person', mri: context.activity.from.id, displayname: context.activity.from.name }
          ]
      }};

      await context.sendActivity(responseActivity);
    }
}
```

# <a name="json"></a>[<span data-ttu-id="7bc09-205">Json</span><span class="sxs-lookup"><span data-stu-id="7bc09-205">JSON</span></span>](#tab/json)

<span data-ttu-id="7bc09-206">Sie erhalten eine neue `composeExtension/submitAction` Nachricht wie die folgende:</span><span class="sxs-lookup"><span data-stu-id="7bc09-206">You receive a new `composeExtension/submitAction` message similar to the following:</span></span>

```json
{
  "name": "composeExtension/submitAction",
  "type": "invoke",
  "conversation": { "id": "19:c366b75791784100b6e8b515fd55b063@thread.skype" },
  "imdisplayname": "Pranav Smith",
  ...
  "value": {
    "botMessagePreviewAction": "send",
    "botActivityPreview": [
      {
        "type": "message/card",
        "attachments": [
          {
            "content":
              {
                "type": "AdaptiveCard",
                "body": [{<<card payload>>}]
              },
            "contentType" : "application/vnd.microsoft.card.adaptive"
          }
        ],
        "context": { "theme": "default" }
      }
    ],
  }
}
```

* * *

### <a name="user-attribution-for-bots-messages"></a><span data-ttu-id="7bc09-207">Benutzerzuschreibung für Bots-Nachrichten</span><span class="sxs-lookup"><span data-stu-id="7bc09-207">User attribution for bots messages</span></span> 

<span data-ttu-id="7bc09-208">In Szenarien, in denen ein Bot Nachrichten im Auftrag eines Benutzers sendet, hilft das Zuweisen der Nachricht an diesen Benutzer bei der Interaktion und zeigt einen natürlicheren Interaktionsfluss.</span><span class="sxs-lookup"><span data-stu-id="7bc09-208">In scenarios where a bot sends messages on behalf of a user, attributing the message to that user helps with engagement and showcase a more natural interaction flow.</span></span> <span data-ttu-id="7bc09-209">Mit diesem Feature können Sie einer Benutzerin, in deren Auftrag sie gesendet wurde, eine Nachricht von Ihrem Bot entributen.</span><span class="sxs-lookup"><span data-stu-id="7bc09-209">This feature allows you to attribute a message from your bot to a user on whose behalf it was sent.</span></span>

<span data-ttu-id="7bc09-210">In der folgenden Abbildung ist links eine Kartennachricht, die von einem Bot ohne Benutzerzuschreibung gesendet wird, und rechts eine Karte, die von einem Bot mit Benutzerzuschreibung gesendet wird.</span><span class="sxs-lookup"><span data-stu-id="7bc09-210">In the following image, on the left is a card message sent by a bot without user attribution and on the right is a card sent by a bot with user attribution.</span></span>

![Benutzer-Attributionsbots](../../../assets/images/messaging-extension/user-attribution-bots.png)

<span data-ttu-id="7bc09-212">Um die Benutzerzuschreibung in Teams zu verwenden, müssen Sie die Erwähnungsentität in Ihrer Nutzlast hinzufügen, die an `OnBehalfOf` `ChannelData` `Activity` Teams.</span><span class="sxs-lookup"><span data-stu-id="7bc09-212">To use the user attribution in teams, you must add the `OnBehalfOf` mention entity to `ChannelData` in your `Activity` payload that is sent to Teams.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="7bc09-213">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="7bc09-213">C#/.NET</span></span>](#tab/dotnet-1)

```csharp
    OnBehalfOf = new []
    {
      new
      {
        ItemId = 0,
        MentionType = "person",
        Mri = turnContext.Activity.From.Id,
        DisplayName = turnContext.Activity.From.Name
      }  
    }

```

# <a name="json"></a>[<span data-ttu-id="7bc09-214">Json</span><span class="sxs-lookup"><span data-stu-id="7bc09-214">JSON</span></span>](#tab/json-1)

```json
{
    "text": "Hello World!",
    "ChannelData": {
        "OnBehalfOf": [{
            "itemid": 0,
            "mentionType": "person",
            "mri": "29:orgid:89e6508d-6c0f-4ffe-9f6a-b58416d965ae",
            "displayName": "Sowrabh N R S"
        }]
    }
}
```

* * *

#### <a name="details-of--onbehalfof-entity-schema"></a><span data-ttu-id="7bc09-215">Details des  `OnBehalfOf` Entitätsschemas</span><span class="sxs-lookup"><span data-stu-id="7bc09-215">Details of  `OnBehalfOf` entity schema</span></span>

<span data-ttu-id="7bc09-216">Der folgende Abschnitt enthält eine Beschreibung der Entitäten im `OnBehalfOf` Array:</span><span class="sxs-lookup"><span data-stu-id="7bc09-216">The following section is a description of the entities in the `OnBehalfOf` Array:</span></span>

|<span data-ttu-id="7bc09-217">Feld</span><span class="sxs-lookup"><span data-stu-id="7bc09-217">Field</span></span>|<span data-ttu-id="7bc09-218">Typ</span><span class="sxs-lookup"><span data-stu-id="7bc09-218">Type</span></span>|<span data-ttu-id="7bc09-219">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="7bc09-219">Description</span></span>|
|:---|:---|:---|
|`itemId`|<span data-ttu-id="7bc09-220">Ganze Zahl</span><span class="sxs-lookup"><span data-stu-id="7bc09-220">Integer</span></span>|<span data-ttu-id="7bc09-221">Beschreibt die Identifikation des Elements.</span><span class="sxs-lookup"><span data-stu-id="7bc09-221">Describes identification of the item.</span></span> <span data-ttu-id="7bc09-222">Der Wert muss `0` sein.</span><span class="sxs-lookup"><span data-stu-id="7bc09-222">Its value must be `0`.</span></span>|
|`mentionType`|<span data-ttu-id="7bc09-223">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="7bc09-223">String</span></span>|<span data-ttu-id="7bc09-224">Beschreibt die Erwähnung einer "Person".</span><span class="sxs-lookup"><span data-stu-id="7bc09-224">Describes the mention of a "person".</span></span>|
|`mri`|<span data-ttu-id="7bc09-225">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="7bc09-225">String</span></span>|<span data-ttu-id="7bc09-226">MrI (Message Resource Identifier) der Person, in deren Auftrag die Nachricht gesendet wird.</span><span class="sxs-lookup"><span data-stu-id="7bc09-226">Message resource identifier (MRI) of the person on whose behalf the message is sent.</span></span> <span data-ttu-id="7bc09-227">Der Name des Absenders der Nachricht würde als " bis " \<user\> \<bot name\> angezeigt.</span><span class="sxs-lookup"><span data-stu-id="7bc09-227">Message sender name would appear as "\<user\> through \<bot name\>".</span></span>|
|`displayName`|<span data-ttu-id="7bc09-228">Zeichenfolge</span><span class="sxs-lookup"><span data-stu-id="7bc09-228">String</span></span>|<span data-ttu-id="7bc09-229">Name der Person.</span><span class="sxs-lookup"><span data-stu-id="7bc09-229">Name of the person.</span></span> <span data-ttu-id="7bc09-230">Wird als Fallback verwendet, wenn die Namensauflösung nicht verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="7bc09-230">Used as fallback in case name resolution is unavailable.</span></span>|
  
## <a name="code-sample"></a><span data-ttu-id="7bc09-231">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="7bc09-231">Code sample</span></span>

| <span data-ttu-id="7bc09-232">Beispielname</span><span class="sxs-lookup"><span data-stu-id="7bc09-232">Sample Name</span></span>           | <span data-ttu-id="7bc09-233">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="7bc09-233">Description</span></span> | <span data-ttu-id="7bc09-234">.NET</span><span class="sxs-lookup"><span data-stu-id="7bc09-234">.NET</span></span>    | <span data-ttu-id="7bc09-235">Node.js</span><span class="sxs-lookup"><span data-stu-id="7bc09-235">Node.js</span></span>   |   
|:---------------------|:--------------|:---------|:--------|
|<span data-ttu-id="7bc09-236">Teams Messagingerweiterungsaktion</span><span class="sxs-lookup"><span data-stu-id="7bc09-236">Teams messaging extension action</span></span>| <span data-ttu-id="7bc09-237">Beschreibt, wie Sie Aktionsbefehle definieren, Aufgabenmodul erstellen und auf Die Absendenaktion des Aufgabenmoduls reagieren.</span><span class="sxs-lookup"><span data-stu-id="7bc09-237">Describes how to define action commands, create task module, and  respond to task module submit action.</span></span> |[<span data-ttu-id="7bc09-238">View</span><span class="sxs-lookup"><span data-stu-id="7bc09-238">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/51.teams-messaging-extensions-action)|[<span data-ttu-id="7bc09-239">View</span><span class="sxs-lookup"><span data-stu-id="7bc09-239">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/51.teams-messaging-extensions-action) | 
|<span data-ttu-id="7bc09-240">Teams messaging extension search</span><span class="sxs-lookup"><span data-stu-id="7bc09-240">Teams messaging extension search</span></span>   |  <span data-ttu-id="7bc09-241">Beschreibt, wie Sie Suchbefehle definieren und auf Suchbefehle reagieren.</span><span class="sxs-lookup"><span data-stu-id="7bc09-241">Describes how to define search commands and respond to searches.</span></span>        |[<span data-ttu-id="7bc09-242">View</span><span class="sxs-lookup"><span data-stu-id="7bc09-242">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/50.teams-messaging-extensions-search)|[<span data-ttu-id="7bc09-243">View</span><span class="sxs-lookup"><span data-stu-id="7bc09-243">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/50.teams-messaging-extensions-search)|

## <a name="next-step"></a><span data-ttu-id="7bc09-244">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="7bc09-244">Next Step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7bc09-245">Definition von Suchbefehlen</span><span class="sxs-lookup"><span data-stu-id="7bc09-245">Define search commands</span></span>](~/messaging-extensions/how-to/search-commands/define-search-command.md)

