---
title: Reagieren auf die Sendeaktion des Aufgabenmoduls
author: surbhigupta
description: Beschreibt, wie auf die Aufgabenmodul-Sendeaktion über einen Aktionsbefehl für Messaging-Erweiterungen reagiert wird
localization_priority: Normal
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: 9d0690a620efc3e658372cfaecf31504787b3d71
ms.sourcegitcommit: 623d81eb079d1842813265746a5fe0fe6311b196
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/22/2021
ms.locfileid: "53068956"
---
# <a name="respond-to-the-task-module-submit-action"></a><span data-ttu-id="1d068-103">Reagieren auf die Sendeaktion des Aufgabenmoduls</span><span class="sxs-lookup"><span data-stu-id="1d068-103">Respond to the task module submit action</span></span>

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

<span data-ttu-id="1d068-104">In diesem Dokument erfahren Sie, wie Ihre App auf die Aktionsbefehle reagiert, z. B. das Aufgabenmodul des Benutzers, um eine Aktion zu übermitteln.</span><span class="sxs-lookup"><span data-stu-id="1d068-104">This document guides you on how your app responds to the action commands, such as user's task module submit action.</span></span>
<span data-ttu-id="1d068-105">Nachdem ein Benutzer das Aufgabenmodul übermittelt hat, empfängt Ihr Webdienst eine `composeExtension/submitAction` Aufrufnachricht mit der Befehls-ID und den Parameterwerten.</span><span class="sxs-lookup"><span data-stu-id="1d068-105">After a user submits the task module, your web service receives a `composeExtension/submitAction` invoke message with the command ID and parameter values.</span></span> <span data-ttu-id="1d068-106">Ihre App hat fünf Sekunden Zeit, um auf den Aufruf zu reagieren. Andernfalls erhält der Benutzer die Fehlermeldung **"Die App kann nicht erreicht** werden", und jede Antwort auf den Aufruf wird vom Teams Client ignoriert.</span><span class="sxs-lookup"><span data-stu-id="1d068-106">Your app has five seconds to respond to the invoke, otherwise the user receives an error message **Unable to reach the app**, and any reply to the invoke is ignored by the Teams client.</span></span>

<span data-ttu-id="1d068-107">Sie haben die folgenden Optionen, um zu antworten:</span><span class="sxs-lookup"><span data-stu-id="1d068-107">You have the following options to respond:</span></span>

* <span data-ttu-id="1d068-108">Keine Antwort: Verwenden Sie die Sendeaktion, um einen Prozess in einem externen System auszulösen und dem Benutzer kein Feedback zu geben.</span><span class="sxs-lookup"><span data-stu-id="1d068-108">No response: Use the submit action to trigger a process in an external system, and not provide any feedback to the user.</span></span> <span data-ttu-id="1d068-109">Dies ist nützlich für lange ausgeführte Prozesse, und Sie können wählen, alternativ Feedback zu geben.</span><span class="sxs-lookup"><span data-stu-id="1d068-109">This is useful for long-running processes, and you can select to provide feedback alternately.</span></span> <span data-ttu-id="1d068-110">Sie können z. B. Feedback mit einer [proaktiven Nachricht](~/bots/how-to/conversations/send-proactive-messages.md)geben.</span><span class="sxs-lookup"><span data-stu-id="1d068-110">For example, you can give feedback with a [proactive message](~/bots/how-to/conversations/send-proactive-messages.md).</span></span>
* <span data-ttu-id="1d068-111">[Ein weiteres Aufgabenmodul:](#respond-with-another-task-module)Sie können im Rahmen einer mehrstufigen Interaktion mit einem zusätzlichen Aufgabenmodul antworten.</span><span class="sxs-lookup"><span data-stu-id="1d068-111">[Another task module](#respond-with-another-task-module): You can respond with an additional task module as part of a multi-step interaction.</span></span>
* <span data-ttu-id="1d068-112">[Kartenantwort:](#respond-with-a-card-inserted-into-the-compose-message-area)Sie können mit einer Karte antworten, mit der der Benutzer interagieren oder in eine Nachricht einfügen kann.</span><span class="sxs-lookup"><span data-stu-id="1d068-112">[Card response](#respond-with-a-card-inserted-into-the-compose-message-area): You can respond with a card that the user can interact with or insert into a message.</span></span>
* <span data-ttu-id="1d068-113">[Adaptive Karte vom Bot:](#bot-response-with-adaptive-card)Fügen Sie eine adaptive Karte direkt in die Unterhaltung ein.</span><span class="sxs-lookup"><span data-stu-id="1d068-113">[Adaptive Card from bot](#bot-response-with-adaptive-card): Insert an Adaptive Card directly into the conversation.</span></span>
* <span data-ttu-id="1d068-114">[Fordern Sie den Benutzer auf, sich zu authentifizieren.](~/messaging-extensions/how-to/add-authentication.md)</span><span class="sxs-lookup"><span data-stu-id="1d068-114">[Request the user to authenticate](~/messaging-extensions/how-to/add-authentication.md).</span></span>
* <span data-ttu-id="1d068-115">[Fordern Sie den Benutzer auf, eine zusätzliche Konfiguration bereitzustellen]~/get-started/first-message-extension.md).</span><span class="sxs-lookup"><span data-stu-id="1d068-115">[Request the user to provide additional configuration]~/get-started/first-message-extension.md).</span></span>

<span data-ttu-id="1d068-116">Bei der Authentifizierung oder Konfiguration wird der ursprüngliche Aufruf nach Abschluss des Prozesses erneut an Ihren Webdienst senden.</span><span class="sxs-lookup"><span data-stu-id="1d068-116">For authentication or configuration, after the user completes the process, the original invoke is resent to your web service.</span></span> <span data-ttu-id="1d068-117">Die folgende Tabelle zeigt, welche Arten von Antworten basierend auf dem Aufrufspeicherort `commandContext` der Messaging-Erweiterung verfügbar sind:</span><span class="sxs-lookup"><span data-stu-id="1d068-117">The following table shows which types of responses are available based on the invoke location `commandContext` of the messaging extension:</span></span> 

|<span data-ttu-id="1d068-118">Antworttyp</span><span class="sxs-lookup"><span data-stu-id="1d068-118">Response Type</span></span> | <span data-ttu-id="1d068-119">Verfassen</span><span class="sxs-lookup"><span data-stu-id="1d068-119">Compose</span></span> | <span data-ttu-id="1d068-120">Befehlsleiste</span><span class="sxs-lookup"><span data-stu-id="1d068-120">Command bar</span></span> | <span data-ttu-id="1d068-121">Meldung</span><span class="sxs-lookup"><span data-stu-id="1d068-121">Message</span></span> |
|--------------|:-------------:|:-------------:|:---------:|
|<span data-ttu-id="1d068-122">Kartenantwort</span><span class="sxs-lookup"><span data-stu-id="1d068-122">Card response</span></span> | <span data-ttu-id="1d068-123">✔</span><span class="sxs-lookup"><span data-stu-id="1d068-123">✔</span></span> | <span data-ttu-id="1d068-124">✔</span><span class="sxs-lookup"><span data-stu-id="1d068-124">✔</span></span> | <span data-ttu-id="1d068-125">✔</span><span class="sxs-lookup"><span data-stu-id="1d068-125">✔</span></span> |
|<span data-ttu-id="1d068-126">Ein weiteres Aufgabenmodul</span><span class="sxs-lookup"><span data-stu-id="1d068-126">Another task module</span></span> | <span data-ttu-id="1d068-127">✔</span><span class="sxs-lookup"><span data-stu-id="1d068-127">✔</span></span> | <span data-ttu-id="1d068-128">✔</span><span class="sxs-lookup"><span data-stu-id="1d068-128">✔</span></span> | <span data-ttu-id="1d068-129">✔</span><span class="sxs-lookup"><span data-stu-id="1d068-129">✔</span></span> |
|<span data-ttu-id="1d068-130">Bot mit adaptiver Karte</span><span class="sxs-lookup"><span data-stu-id="1d068-130">Bot with Adaptive Card</span></span> | <span data-ttu-id="1d068-131">✔</span><span class="sxs-lookup"><span data-stu-id="1d068-131">✔</span></span> | <span data-ttu-id="1d068-132">x</span><span class="sxs-lookup"><span data-stu-id="1d068-132">x</span></span> | <span data-ttu-id="1d068-133">✔</span><span class="sxs-lookup"><span data-stu-id="1d068-133">✔</span></span> |
| <span data-ttu-id="1d068-134">Keine Antwort</span><span class="sxs-lookup"><span data-stu-id="1d068-134">No response</span></span> | <span data-ttu-id="1d068-135">✔</span><span class="sxs-lookup"><span data-stu-id="1d068-135">✔</span></span> | <span data-ttu-id="1d068-136">✔</span><span class="sxs-lookup"><span data-stu-id="1d068-136">✔</span></span> | <span data-ttu-id="1d068-137">✔</span><span class="sxs-lookup"><span data-stu-id="1d068-137">✔</span></span> |

> [!NOTE]
> * <span data-ttu-id="1d068-138">Wenn Sie **Action.Submit** über ME-Karten auswählen, sendet sie Aufrufaktivitäten mit dem Namen **composeExtension,** wobei der Wert der üblichen Nutzlast entspricht.</span><span class="sxs-lookup"><span data-stu-id="1d068-138">When you select **Action.Submit** through ME cards, it sends invoke activity with the name **composeExtension**, where the value is equal to the usual payload.</span></span>
> * <span data-ttu-id="1d068-139">Wenn Sie **"Action.Submit** through conversation" auswählen, erhalten Sie eine Nachrichtenaktivität mit dem Namen **"onCardButtonClicked",** wobei der Wert der üblichen Nutzlast entspricht.</span><span class="sxs-lookup"><span data-stu-id="1d068-139">When you select **Action.Submit** through conversation, you receive message activity with the name **onCardButtonClicked**, where the value is equal to the usual payload.</span></span>

## <a name="the-submitaction-invoke-event"></a><span data-ttu-id="1d068-140">Das submitAction-Aufrufereignis</span><span class="sxs-lookup"><span data-stu-id="1d068-140">The submitAction invoke event</span></span>

<span data-ttu-id="1d068-141">Beispiele für den Empfang der Aufrufnachricht sind:</span><span class="sxs-lookup"><span data-stu-id="1d068-141">Examples of receiving the invoke message are as follows:</span></span>

# <a name="cnet"></a>[<span data-ttu-id="1d068-142">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="1d068-142">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task<MessagingExtensionActionResponse> OnTeamsMessagingExtensionSubmitActionAsync(
  ITurnContext<IInvokeActivity> turnContext, MessagingExtensionAction action, CancellationToken cancellationToken) {
  //code to handle the submit action
}
```

# <a name="javascriptnodejs"></a>[<span data-ttu-id="1d068-143">JavaScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="1d068-143">JavaScript/Node.js</span></span>](#tab/javascript)

```javascript
class TeamsMessagingExtensionsActionPreview extends TeamsActivityHandler {
  constructor() {
  handleTeamsMessagingExtensionSubmitAction(context, action) {
  
  //code to handle the submit action
    }
  }
}
```

# <a name="json"></a>[<span data-ttu-id="1d068-144">Json</span><span class="sxs-lookup"><span data-stu-id="1d068-144">JSON</span></span>](#tab/json)

<span data-ttu-id="1d068-145">Dies ist ein Beispiel für das JSON-Objekt, das Sie erhalten.</span><span class="sxs-lookup"><span data-stu-id="1d068-145">This is an example of the JSON object that you receive.</span></span> <span data-ttu-id="1d068-146">Der `commandContext` Parameter gibt an, von wo ihre Messaging-Erweiterung ausgelöst wurde.</span><span class="sxs-lookup"><span data-stu-id="1d068-146">The `commandContext` parameter indicates where your messaging extension was triggered from.</span></span> <span data-ttu-id="1d068-147">Das `data` Objekt enthält die Felder auf dem Formular als Parameter und die Werte, die der Benutzer übermittelt hat.</span><span class="sxs-lookup"><span data-stu-id="1d068-147">The `data` object contains the fields on the form as parameters, and the values the user submitted.</span></span> <span data-ttu-id="1d068-148">Das JSON-Objekt hier wird gekürzt, um die relevantesten Felder hervorzuheben.</span><span class="sxs-lookup"><span data-stu-id="1d068-148">The JSON object here is shortened to highlight the most relevant fields.</span></span>

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

## <a name="respond-with-a-card-inserted-into-the-compose-message-area"></a><span data-ttu-id="1d068-149">Antworten mit einer Karte, die in den Bereich zum Verfassen von Nachrichten eingefügt wurde</span><span class="sxs-lookup"><span data-stu-id="1d068-149">Respond with a card inserted into the compose message area</span></span>

<span data-ttu-id="1d068-150">Die gängigste Möglichkeit, auf die Anforderung zu `composeExtension/submitAction` antworten, ist eine Karte, die in den Bereich zum Verfassen von Nachrichten eingefügt wird.</span><span class="sxs-lookup"><span data-stu-id="1d068-150">The most common way to respond to the `composeExtension/submitAction` request is with a card inserted into the compose message area.</span></span> <span data-ttu-id="1d068-151">Der Benutzer sendet die Karte an die Unterhaltung.</span><span class="sxs-lookup"><span data-stu-id="1d068-151">The user submits the card to the conversation.</span></span> <span data-ttu-id="1d068-152">Weitere Informationen zum Verwenden von Karten finden Sie unter [Karten und Kartenaktionen.](~/task-modules-and-cards/cards/cards-actions.md)</span><span class="sxs-lookup"><span data-stu-id="1d068-152">For more information on using cards, see [cards and card actions](~/task-modules-and-cards/cards/cards-actions.md).</span></span>

# <a name="cnet"></a>[<span data-ttu-id="1d068-153">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="1d068-153">C#/.NET</span></span>](#tab/dotnet)

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

# <a name="javascriptnodejs"></a>[<span data-ttu-id="1d068-154">JavaScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="1d068-154">JavaScript/Node.js</span></span>](#tab/javascript)

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

# <a name="json"></a>[<span data-ttu-id="1d068-155">Json</span><span class="sxs-lookup"><span data-stu-id="1d068-155">JSON</span></span>](#tab/json)

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

## <a name="respond-with-another-task-module"></a><span data-ttu-id="1d068-156">Antworten mit einem anderen Aufgabenmodul</span><span class="sxs-lookup"><span data-stu-id="1d068-156">Respond with another task module</span></span>

<span data-ttu-id="1d068-157">Sie können auswählen, um auf das `submitAction` Ereignis mit einem zusätzlichen Aufgabenmodul zu reagieren.</span><span class="sxs-lookup"><span data-stu-id="1d068-157">You can select to respond to the `submitAction` event with an additional task module.</span></span> <span data-ttu-id="1d068-158">Dies ist in folgenden Fällen hilfreich:</span><span class="sxs-lookup"><span data-stu-id="1d068-158">This is useful when:</span></span>

* <span data-ttu-id="1d068-159">Sie müssen große Mengen an Informationen sammeln.</span><span class="sxs-lookup"><span data-stu-id="1d068-159">You need to collect large amounts of information.</span></span>
* <span data-ttu-id="1d068-160">Sie müssen die gesammelten Informationen basierend auf benutzereingaben dynamisch ändern.</span><span class="sxs-lookup"><span data-stu-id="1d068-160">You need to dynamically change the information you are collecting based on user input.</span></span>
* <span data-ttu-id="1d068-161">Sie müssen die vom Benutzer übermittelten Informationen überprüfen und das Formular erneut mit einer Fehlermeldung senden, wenn etwas nicht stimmt.</span><span class="sxs-lookup"><span data-stu-id="1d068-161">You need to validate the information submitted by the user and resend the form with an error message if something is wrong.</span></span> 

<span data-ttu-id="1d068-162">Die Antwortmethode ist identisch mit [der Antwort auf das ursprüngliche `fetchTask` Ereignis.](~/messaging-extensions/how-to/action-commands/create-task-module.md)</span><span class="sxs-lookup"><span data-stu-id="1d068-162">The method for response is the same as [responding to the initial `fetchTask` event](~/messaging-extensions/how-to/action-commands/create-task-module.md).</span></span> <span data-ttu-id="1d068-163">Wenn Sie das Bot Framework SDK verwenden, löst dasselbe Ereignis für beide Sendeaktionen aus.</span><span class="sxs-lookup"><span data-stu-id="1d068-163">If you are using the Bot Framework SDK the same event triggers for both submit actions.</span></span> <span data-ttu-id="1d068-164">Damit dies funktioniert, müssen Sie Logik hinzufügen, die die richtige Antwort bestimmt.</span><span class="sxs-lookup"><span data-stu-id="1d068-164">To make this work, you must add logic that determines the correct response.</span></span>

## <a name="bot-response-with-adaptive-card"></a><span data-ttu-id="1d068-165">Bot-Antwort mit adaptiver Karte</span><span class="sxs-lookup"><span data-stu-id="1d068-165">Bot response with Adaptive Card</span></span>

> [!NOTE]
> <span data-ttu-id="1d068-166">Die Voraussetzung für das Abrufen der Bot-Antwort mit einer adaptiven Karte besteht darin, dass Sie das `bot` Objekt Ihrem App-Manifest hinzufügen und den erforderlichen Bereich für den Bot definieren müssen.</span><span class="sxs-lookup"><span data-stu-id="1d068-166">The prerequisite to get the bot response with an Adaptive card is that you must add the `bot` object to your app manifest, and define the required scope for the bot.</span></span> <span data-ttu-id="1d068-167">Verwenden Sie die gleiche ID wie Ihre Messaging-Erweiterung für Ihren Bot.</span><span class="sxs-lookup"><span data-stu-id="1d068-167">Use the same ID as your messaging extension for your bot.</span></span>
 
<span data-ttu-id="1d068-168">Sie können auch darauf reagieren, indem Sie `submitAction` eine Nachricht mit einer adaptiven Karte mit einem Bot in den Kanal einfügen.</span><span class="sxs-lookup"><span data-stu-id="1d068-168">You can also respond to the `submitAction` by inserting a message with an Adaptive Card into the channel with a bot.</span></span> <span data-ttu-id="1d068-169">Der Benutzer kann eine Vorschau der Nachricht anzeigen, bevor er sie übermittelt.</span><span class="sxs-lookup"><span data-stu-id="1d068-169">The user can preview the message before submitting it.</span></span> <span data-ttu-id="1d068-170">Dies ist sehr nützlich in Szenarien, in denen Sie Informationen von den Benutzern sammeln, bevor Sie eine Adaptive Kartenantwort erstellen, oder wenn Sie die Karte aktualisieren, nachdem jemand damit interagiert.</span><span class="sxs-lookup"><span data-stu-id="1d068-170">This is very useful in scenarios where you gather information from the users before creating an Adaptive Card response, or when you update the card after someone interacts with it.</span></span> 

<span data-ttu-id="1d068-171">Das folgende Szenario zeigt, wie die App Polly eine Abfrage konfiguriert, ohne die Konfigurationsschritte in die Kanalunterhaltung aufzunehmen:</span><span class="sxs-lookup"><span data-stu-id="1d068-171">The following scenario shows how the app Polly configures a poll without including the configuration steps in the channel conversation:</span></span>

<span data-ttu-id="1d068-172">**So konfigurieren Sie die Abfrage**</span><span class="sxs-lookup"><span data-stu-id="1d068-172">**To configure the poll**</span></span>

1. <span data-ttu-id="1d068-173">Der Benutzer wählt die Messaging-Erweiterung aus, um das Aufgabenmodul aufzurufen.</span><span class="sxs-lookup"><span data-stu-id="1d068-173">The user selects the messaging extension to invoke the task module.</span></span>
1. <span data-ttu-id="1d068-174">Der Benutzer konfiguriert die Abfrage mit dem Aufgabenmodul.</span><span class="sxs-lookup"><span data-stu-id="1d068-174">The user configures the poll with the task module.</span></span>
1. <span data-ttu-id="1d068-175">Nach dem Übermitteln des Aufgabenmoduls verwendet die App die bereitgestellten Informationen, um die Abfrage als adaptive Karte zu erstellen, und sendet sie als `botMessagePreview` Antwort an den Client.</span><span class="sxs-lookup"><span data-stu-id="1d068-175">After submitting the task module, the app uses the information provided to build the poll as an Adaptive Card and sends it as a `botMessagePreview` response to the client.</span></span>
1. <span data-ttu-id="1d068-176">Der Benutzer kann dann eine Vorschau der Adaptive Card-Nachricht anzeigen, bevor der Bot sie in den Kanal einfügt.</span><span class="sxs-lookup"><span data-stu-id="1d068-176">The user can then preview the Adaptive Card message before the bot inserts it into the channel.</span></span> <span data-ttu-id="1d068-177">Wenn die App noch kein Mitglied des Kanals ist, wählen Sie diese Option `Send` aus, um sie hinzuzufügen.</span><span class="sxs-lookup"><span data-stu-id="1d068-177">If the app is not already a member of the channel, select `Send` to add it.</span></span>

    > [!NOTE] 
    > * <span data-ttu-id="1d068-178">Die Benutzer können auch die `Edit` Nachricht auswählen, die sie an das ursprüngliche Aufgabenmodul zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="1d068-178">The users can also select to `Edit` the message, which returns them to the original task module.</span></span> 
    > * <span data-ttu-id="1d068-179">Die Interaktion mit der adaptiven Karte ändert die Nachricht vor dem Senden.</span><span class="sxs-lookup"><span data-stu-id="1d068-179">Interaction with the Adaptive Card changes the message before sending it.</span></span>
1. <span data-ttu-id="1d068-180">Nachdem der Benutzer den Bot ausgewählt `Send` hat, wird die Nachricht an den Kanal veröffentlicht.</span><span class="sxs-lookup"><span data-stu-id="1d068-180">After the user selects `Send` the bot posts the message to the channel.</span></span>

## <a name="respond-to-initial-submit-action"></a><span data-ttu-id="1d068-181">Reagieren auf anfängliche Übermittlungsaktion</span><span class="sxs-lookup"><span data-stu-id="1d068-181">Respond to initial submit action</span></span>

<span data-ttu-id="1d068-182">Ihr Aufgabenmodul muss auf die anfängliche `composeExtension/submitAction` Nachricht mit einer Vorschau der Karte antworten, die der Bot an den Kanal sendet.</span><span class="sxs-lookup"><span data-stu-id="1d068-182">Your task module must respond to the initial `composeExtension/submitAction` message with a preview of the card that the bot sends to the channel.</span></span> <span data-ttu-id="1d068-183">Der Benutzer kann die Karte vor dem Senden überprüfen und auch versuchen, ihren Bot in der Unterhaltung zu installieren, wenn der Bot noch nicht installiert ist.</span><span class="sxs-lookup"><span data-stu-id="1d068-183">The user can verify the card before sending, and also try to install your bot in the conversation if the bot is not already installed.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="1d068-184">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="1d068-184">C#/.NET</span></span>](#tab/dotnet)

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

# <a name="javascriptnodejs"></a>[<span data-ttu-id="1d068-185">JavaScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="1d068-185">JavaScript/Node.js</span></span>](#tab/javascript)

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

# <a name="json"></a>[<span data-ttu-id="1d068-186">Json</span><span class="sxs-lookup"><span data-stu-id="1d068-186">JSON</span></span>](#tab/json)

> [!NOTE]
> * <span data-ttu-id="1d068-187">Die `activityPreview` Muss eine Aktivität mit genau einer Adaptive `message` Card-Anlage enthalten.</span><span class="sxs-lookup"><span data-stu-id="1d068-187">The `activityPreview` must contain a `message` activity with exactly one Adaptive Card attachment.</span></span> <span data-ttu-id="1d068-188">Der `<< Card Payload >>` Wert ist ein Platzhalter für die Karte, die Sie senden möchten.</span><span class="sxs-lookup"><span data-stu-id="1d068-188">The `<< Card Payload >>` value is a placeholder for the card you want to send.</span></span>

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

### <a name="the-botmessagepreview-send-and-edit-events"></a><span data-ttu-id="1d068-189">Das botMessagePreview-Sende- und Bearbeitungsereignis</span><span class="sxs-lookup"><span data-stu-id="1d068-189">The botMessagePreview send and edit events</span></span>

<span data-ttu-id="1d068-190">Ihre Messaging-Erweiterung muss auf zwei neue Arten des `composeExtension/submitAction` Aufrufs reagieren, wobei `value.botMessagePreviewAction = "send"` und `value.botMessagePreviewAction = "edit"` .</span><span class="sxs-lookup"><span data-stu-id="1d068-190">Your messaging extension must respond to two new types of the `composeExtension/submitAction` invoke, where `value.botMessagePreviewAction = "send"`and `value.botMessagePreviewAction = "edit"`.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="1d068-191">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="1d068-191">C#/.NET</span></span>](#tab/dotnet)

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

# <a name="javascriptnodejs"></a>[<span data-ttu-id="1d068-192">JavaScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="1d068-192">JavaScript/Node.js</span></span>](#tab/javascript)

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

# <a name="json"></a>[<span data-ttu-id="1d068-193">Json</span><span class="sxs-lookup"><span data-stu-id="1d068-193">JSON</span></span>](#tab/json)

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

### <a name="respond-to-botmessagepreview-edit"></a><span data-ttu-id="1d068-194">Antworten auf botMessagePreview-Bearbeitung</span><span class="sxs-lookup"><span data-stu-id="1d068-194">Respond to botMessagePreview edit</span></span>

<span data-ttu-id="1d068-195">Wenn der Benutzer die Karte vor dem Senden bearbeitet, erhalten Sie durch Auswählen von **"Bearbeiten"** einen `composeExtension/submitAction` Aufruf mit `value.botMessagePreviewAction = edit` .</span><span class="sxs-lookup"><span data-stu-id="1d068-195">If the user edits the card before sending, by selecting **Edit**, you receive a `composeExtension/submitAction` invoke with `value.botMessagePreviewAction = edit`.</span></span> <span data-ttu-id="1d068-196">Sie müssen antworten, indem Sie das von Ihnen gesendete Aufgabenmodul als Reaktion auf den anfänglichen Aufruf zurückgeben, `composeExtension/fetchTask` der die Interaktion begonnen hat.</span><span class="sxs-lookup"><span data-stu-id="1d068-196">You must respond by returning the task module you sent, in response to the initial `composeExtension/fetchTask` invoke that began the interaction.</span></span> <span data-ttu-id="1d068-197">Dadurch kann der Benutzer den Prozess starten, indem er die ursprünglichen Informationen erneut eingibt.</span><span class="sxs-lookup"><span data-stu-id="1d068-197">This allows the user to start the process by re-entering the original information.</span></span> <span data-ttu-id="1d068-198">Verwenden Sie die verfügbaren Informationen, um das Aufgabenmodul so zu aktualisieren, dass der Benutzer nicht alle Informationen von Grund auf ausfüllen muss.</span><span class="sxs-lookup"><span data-stu-id="1d068-198">Use the available information to update the task module so that the user need not fill out all information from scratch.</span></span>
<span data-ttu-id="1d068-199">Weitere Informationen zum Reagieren auf das ursprüngliche `fetchTask` Ereignis finden Sie unter ["Reagieren auf das ursprüngliche `fetchTask` Ereignis".](~/messaging-extensions/how-to/action-commands/create-task-module.md)</span><span class="sxs-lookup"><span data-stu-id="1d068-199">For more information on responding to the initial `fetchTask` event, see [responding to the initial `fetchTask` event](~/messaging-extensions/how-to/action-commands/create-task-module.md).</span></span>

### <a name="respond-to-botmessagepreview-send"></a><span data-ttu-id="1d068-200">Antworten auf botMessagePreview-Senden</span><span class="sxs-lookup"><span data-stu-id="1d068-200">Respond to botMessagePreview send</span></span>

<span data-ttu-id="1d068-201">Nachdem der Benutzer **"Senden"** ausgewählt hat, erhalten Sie einen `composeExtension/submitAction` Aufruf mit `value.botMessagePreviewAction = send` .</span><span class="sxs-lookup"><span data-stu-id="1d068-201">After the user selects the **Send**, you receive a `composeExtension/submitAction` invoke with `value.botMessagePreviewAction = send`.</span></span> <span data-ttu-id="1d068-202">Ihr Webdienst muss eine proaktive Nachricht mit der adaptiven Karte erstellen und an die Unterhaltung senden sowie auf den Aufruf antworten.</span><span class="sxs-lookup"><span data-stu-id="1d068-202">Your web service has to create and send a proactive message with the Adaptive Card to the conversation, and also reply to the invoke.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="1d068-203">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="1d068-203">C#/.NET</span></span>](#tab/dotnet)

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

# <a name="javascriptnodejs"></a>[<span data-ttu-id="1d068-204">JavaScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="1d068-204">JavaScript/Node.js</span></span>](#tab/javascript)

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

# <a name="json"></a>[<span data-ttu-id="1d068-205">Json</span><span class="sxs-lookup"><span data-stu-id="1d068-205">JSON</span></span>](#tab/json)

<span data-ttu-id="1d068-206">Sie erhalten eine neue `composeExtension/submitAction` Nachricht, die der folgenden ähnelt:</span><span class="sxs-lookup"><span data-stu-id="1d068-206">You receive a new `composeExtension/submitAction` message similar to the following:</span></span>

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

### <a name="user-attribution-for-bots-messages"></a><span data-ttu-id="1d068-207">Benutzerzuordnung für Bots-Nachrichten</span><span class="sxs-lookup"><span data-stu-id="1d068-207">User attribution for bots messages</span></span> 

<span data-ttu-id="1d068-208">In Szenarien, in denen ein Bot Nachrichten im Namen eines Benutzers sendet, hilft die Zuweisung der Nachricht an diesen Benutzer bei der Interaktion und zeigt einen natürlicheren Interaktionsfluss.</span><span class="sxs-lookup"><span data-stu-id="1d068-208">In scenarios where a bot sends messages on behalf of a user, attributing the message to that user helps with engagement and showcase a more natural interaction flow.</span></span> <span data-ttu-id="1d068-209">Mit diesem Feature können Sie einem Benutzer, in dessen Auftrag er gesendet wurde, eine Nachricht von Ihrem Bot zuordnen.</span><span class="sxs-lookup"><span data-stu-id="1d068-209">This feature allows you to attribute a message from your bot to a user on whose behalf it was sent.</span></span>

<span data-ttu-id="1d068-210">In der folgenden Abbildung befindet sich auf der linken Seite eine Kartennachricht, die von einem Bot ohne Benutzerzuschreibung gesendet wird, und auf der rechten Seite befindet sich eine Karte, die von einem Bot mit Benutzerzuschreibung gesendet wird.</span><span class="sxs-lookup"><span data-stu-id="1d068-210">In the following image, on the left is a card message sent by a bot without user attribution and on the right is a card sent by a bot with user attribution.</span></span>

![Benutzerzuschreibungs-Bots](../../../assets/images/messaging-extension/user-attribution-bots.png)

<span data-ttu-id="1d068-212">Um die Benutzerzuordnung in Teams zu verwenden, müssen Sie die `OnBehalfOf` Erwähnungsentität `ChannelData` in Ihrer Nutzlast `Activity` hinzufügen, die an Teams gesendet wird.</span><span class="sxs-lookup"><span data-stu-id="1d068-212">To use the user attribution in teams, you must add the `OnBehalfOf` mention entity to `ChannelData` in your `Activity` payload that is sent to Teams.</span></span>

# <a name="cnet"></a>[<span data-ttu-id="1d068-213">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="1d068-213">C#/.NET</span></span>](#tab/dotnet-1)

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

# <a name="json"></a>[<span data-ttu-id="1d068-214">Json</span><span class="sxs-lookup"><span data-stu-id="1d068-214">JSON</span></span>](#tab/json-1)

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

#### <a name="details-of--onbehalfof-entity-schema"></a><span data-ttu-id="1d068-215">Details zum  `OnBehalfOf` Entitätsschema</span><span class="sxs-lookup"><span data-stu-id="1d068-215">Details of  `OnBehalfOf` entity schema</span></span>

<span data-ttu-id="1d068-216">Der folgende Abschnitt enthält eine Beschreibung der Entitäten im `OnBehalfOf` Array:</span><span class="sxs-lookup"><span data-stu-id="1d068-216">The following section is a description of the entities in the `OnBehalfOf` Array:</span></span>

|<span data-ttu-id="1d068-217">Feld</span><span class="sxs-lookup"><span data-stu-id="1d068-217">Field</span></span>|<span data-ttu-id="1d068-218">Typ</span><span class="sxs-lookup"><span data-stu-id="1d068-218">Type</span></span>|<span data-ttu-id="1d068-219">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="1d068-219">Description</span></span>|
|:---|:---|:---|
|`itemId`|<span data-ttu-id="1d068-220">Ganze Zahl</span><span class="sxs-lookup"><span data-stu-id="1d068-220">Integer</span></span>|<span data-ttu-id="1d068-221">Beschreibt die Identifikation des Elements.</span><span class="sxs-lookup"><span data-stu-id="1d068-221">Describes identification of the item.</span></span> <span data-ttu-id="1d068-222">Der Wert muss `0` .</span><span class="sxs-lookup"><span data-stu-id="1d068-222">Its value must be `0`.</span></span>|
|`mentionType`|<span data-ttu-id="1d068-223">String</span><span class="sxs-lookup"><span data-stu-id="1d068-223">String</span></span>|<span data-ttu-id="1d068-224">Beschreibt die Erwähnung einer "Person".</span><span class="sxs-lookup"><span data-stu-id="1d068-224">Describes the mention of a "person".</span></span>|
|`mri`|<span data-ttu-id="1d068-225">String</span><span class="sxs-lookup"><span data-stu-id="1d068-225">String</span></span>|<span data-ttu-id="1d068-226">Nachrichtenressourcenbezeichner (Message Resource Identifier, MRI) der Person, in deren Auftrag die Nachricht gesendet wird.</span><span class="sxs-lookup"><span data-stu-id="1d068-226">Message resource identifier (MRI) of the person on whose behalf the message is sent.</span></span> <span data-ttu-id="1d068-227">Der Name des Absenders der Nachricht würde als " \<user\> bis \<bot name\> " angezeigt.</span><span class="sxs-lookup"><span data-stu-id="1d068-227">Message sender name would appear as "\<user\> through \<bot name\>".</span></span>|
|`displayName`|<span data-ttu-id="1d068-228">String</span><span class="sxs-lookup"><span data-stu-id="1d068-228">String</span></span>|<span data-ttu-id="1d068-229">Name der Person.</span><span class="sxs-lookup"><span data-stu-id="1d068-229">Name of the person.</span></span> <span data-ttu-id="1d068-230">Wird als Fallback verwendet, wenn die Namensauflösung nicht verfügbar ist.</span><span class="sxs-lookup"><span data-stu-id="1d068-230">Used as fallback in case name resolution is unavailable.</span></span>|
  
## <a name="code-sample"></a><span data-ttu-id="1d068-231">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="1d068-231">Code sample</span></span>

| <span data-ttu-id="1d068-232">Beispielname</span><span class="sxs-lookup"><span data-stu-id="1d068-232">Sample Name</span></span>           | <span data-ttu-id="1d068-233">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="1d068-233">Description</span></span> | <span data-ttu-id="1d068-234">.NET</span><span class="sxs-lookup"><span data-stu-id="1d068-234">.NET</span></span>    | <span data-ttu-id="1d068-235">Node.js</span><span class="sxs-lookup"><span data-stu-id="1d068-235">Node.js</span></span>   |   
|:---------------------|:--------------|:---------|:--------|
|<span data-ttu-id="1d068-236">Teams Messaging-Erweiterungsaktion</span><span class="sxs-lookup"><span data-stu-id="1d068-236">Teams messaging extension action</span></span>| <span data-ttu-id="1d068-237">Beschreibt, wie Aktionsbefehle definiert, Aufgabenmodul erstellt und auf Aufgabenmodul-Sendeaktion reagiert wird.</span><span class="sxs-lookup"><span data-stu-id="1d068-237">Describes how to define action commands, create task module, and  respond to task module submit action.</span></span> |[<span data-ttu-id="1d068-238">View</span><span class="sxs-lookup"><span data-stu-id="1d068-238">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/51.teams-messaging-extensions-action)|[<span data-ttu-id="1d068-239">View</span><span class="sxs-lookup"><span data-stu-id="1d068-239">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/51.teams-messaging-extensions-action) | 
|<span data-ttu-id="1d068-240">Teams Messaging-Erweiterungssuche</span><span class="sxs-lookup"><span data-stu-id="1d068-240">Teams messaging extension search</span></span>   |  <span data-ttu-id="1d068-241">Beschreibt, wie Suchbefehle definiert und auf Suchvorgänge reagiert wird.</span><span class="sxs-lookup"><span data-stu-id="1d068-241">Describes how to define search commands and respond to searches.</span></span>        |[<span data-ttu-id="1d068-242">View</span><span class="sxs-lookup"><span data-stu-id="1d068-242">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/csharp_dotnetcore/50.teams-messaging-extensions-search)|[<span data-ttu-id="1d068-243">View</span><span class="sxs-lookup"><span data-stu-id="1d068-243">View</span></span>](https://github.com/microsoft/BotBuilder-Samples/tree/master/samples/javascript_nodejs/50.teams-messaging-extensions-search)|

## <a name="next-step"></a><span data-ttu-id="1d068-244">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="1d068-244">Next Step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="1d068-245">Definition von Suchbefehlen</span><span class="sxs-lookup"><span data-stu-id="1d068-245">Define search commands</span></span>](~/messaging-extensions/how-to/search-commands/define-search-command.md)

