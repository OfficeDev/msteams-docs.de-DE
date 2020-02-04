---
title: Reagieren auf die Aufgabe Modul Submit-Aktion
author: clearab
description: Beschreibt, wie auf die Aufgabenmodul Aktion über einen Aktionsbefehl für die Nachrichten Erweiterung reagiert wird.
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: 33a9388ee84dcf03a5bda59c5a5139c6f49bde6c
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674396"
---
# <a name="respond-to-the-task-module-submit-action"></a><span data-ttu-id="c9f6b-103">Reagieren auf die Aufgabe Modul Submit-Aktion</span><span class="sxs-lookup"><span data-stu-id="c9f6b-103">Respond to the task module submit action</span></span>

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

<span data-ttu-id="c9f6b-104">Sobald ein Benutzer das Aufgabenmodul übermittelt hat, erhält der Webdienst eine `composeExtension/submitAction` Invoke-Meldung mit den festgelegten Befehls-ID-und Parameterwerten.</span><span class="sxs-lookup"><span data-stu-id="c9f6b-104">Once a user submits the task module, your web service will receive a `composeExtension/submitAction` invoke message with the command id and parameter values set.</span></span> <span data-ttu-id="c9f6b-105">Ihre APP hat fünf Sekunden Zeit, um auf den Aufruf zu reagieren, andernfalls erhält der Benutzer die Fehlermeldung "die APP kann nicht erreicht werden", und jede Antwort auf die Invoke wird vom Microsoft Teams-Client ignoriert.</span><span class="sxs-lookup"><span data-stu-id="c9f6b-105">Your app will have five seconds to respond to the invoke, otherwise the user will receive an "Unable to reach the app" error message, and any reply to the invoke will be ignored by the Teams client.</span></span>

<span data-ttu-id="c9f6b-106">Sie haben die folgenden Optionen für die Antwort.</span><span class="sxs-lookup"><span data-stu-id="c9f6b-106">You have the following options for responding.</span></span>

* <span data-ttu-id="c9f6b-107">Keine Antwort: Sie können die Submit-Aktion verwenden, um einen Prozess in einem externen System auszulösen und kein Feedback für den Benutzer bereitzustellen.</span><span class="sxs-lookup"><span data-stu-id="c9f6b-107">No response - You can choose to use the submit action to trigger a process in an external system, and not provide any feedback to the user.</span></span> <span data-ttu-id="c9f6b-108">Dies kann für langwierige Prozesse nützlich sein, und Sie können auswählen, dass Sie Feedback auf andere Weise bereitstellen möchten (beispielsweise mit einer [proaktiven Nachricht](~/bots/how-to/conversations/send-proactive-messages.md).</span><span class="sxs-lookup"><span data-stu-id="c9f6b-108">This can be useful for long-running processes, and you may choose to provide feedback in another manner (for example, with a [proactive message](~/bots/how-to/conversations/send-proactive-messages.md).</span></span>
* <span data-ttu-id="c9f6b-109">[Ein weiterer Aufgabenmodul](#respond-with-another-task-module) -Sie können mit einem zusätzlichen Aufgabenmodul als Teil einer mehrstufigen Interaktion Antworten.</span><span class="sxs-lookup"><span data-stu-id="c9f6b-109">[Another task module](#respond-with-another-task-module) - You can respond with an additional task module as part of a multi-step interaction.</span></span>
* <span data-ttu-id="c9f6b-110">[Karten Antwort](#respond-with-a-card-inserted-into-the-compose-message-area) : Sie können mit einer Karte Antworten, mit der der Benutzer interagieren und/oder in eine Nachricht einfügen kann.</span><span class="sxs-lookup"><span data-stu-id="c9f6b-110">[Card response](#respond-with-a-card-inserted-into-the-compose-message-area) - You can respond with a card that the user can then interact with and/or insert into a message.</span></span>
* <span data-ttu-id="c9f6b-111">[Adaptive Karte von bot](#bot-response-with-adaptive-card) – fügen Sie eine Adaptive Karte direkt in die Unterhaltung ein.</span><span class="sxs-lookup"><span data-stu-id="c9f6b-111">[Adaptive Card from bot](#bot-response-with-adaptive-card) - Insert an Adaptive Card directly into the conversation.</span></span>
* [<span data-ttu-id="c9f6b-112">Anfordern der Authentifizierung durch den Benutzer</span><span class="sxs-lookup"><span data-stu-id="c9f6b-112">Request the user authenticate</span></span>](~/messaging-extensions/how-to/add-authentication.md)
* [<span data-ttu-id="c9f6b-113">Anforderung des Benutzers zur Bereitstellung zusätzlicher Konfiguration</span><span class="sxs-lookup"><span data-stu-id="c9f6b-113">Request the user provide additional configuration</span></span>](~/messaging-extensions/how-to/add-configuration-page.md)

<span data-ttu-id="c9f6b-114">Die folgende Tabelle zeigt, welche Arten von Antworten basierend auf dem Aufruf Speicherort (`commandContext`) der Messaging Erweiterung zur Verfügung stehen.</span><span class="sxs-lookup"><span data-stu-id="c9f6b-114">The table below shows which types of responses are available based on the invoke location (`commandContext`) of the messaging extension.</span></span> <span data-ttu-id="c9f6b-115">Wenn der Benutzer den Fluss abgeschlossen hat, wird der ursprüngliche Aufruf für die Authentifizierung oder Konfiguration erneut an den Webdienst gesendet.</span><span class="sxs-lookup"><span data-stu-id="c9f6b-115">For authentication or configuration, once the user completes the flow the original invoke will be re-sent to your web service.</span></span>

|<span data-ttu-id="c9f6b-116">Antworttyp</span><span class="sxs-lookup"><span data-stu-id="c9f6b-116">Response Type</span></span> | <span data-ttu-id="c9f6b-117">Verfassen</span><span class="sxs-lookup"><span data-stu-id="c9f6b-117">compose</span></span> | <span data-ttu-id="c9f6b-118">Befehlsleiste</span><span class="sxs-lookup"><span data-stu-id="c9f6b-118">command bar</span></span> | <span data-ttu-id="c9f6b-119">message</span><span class="sxs-lookup"><span data-stu-id="c9f6b-119">message</span></span> |
|--------------|:-------------:|:-------------:|:---------:|
|<span data-ttu-id="c9f6b-120">Karten Antwort</span><span class="sxs-lookup"><span data-stu-id="c9f6b-120">Card response</span></span> | <span data-ttu-id="c9f6b-121">x</span><span class="sxs-lookup"><span data-stu-id="c9f6b-121">x</span></span> | <span data-ttu-id="c9f6b-122">x</span><span class="sxs-lookup"><span data-stu-id="c9f6b-122">x</span></span> | <span data-ttu-id="c9f6b-123">x</span><span class="sxs-lookup"><span data-stu-id="c9f6b-123">x</span></span> |
|<span data-ttu-id="c9f6b-124">Ein weiteres Aufgabenmodul</span><span class="sxs-lookup"><span data-stu-id="c9f6b-124">Another task module</span></span> | <span data-ttu-id="c9f6b-125">x</span><span class="sxs-lookup"><span data-stu-id="c9f6b-125">x</span></span> | <span data-ttu-id="c9f6b-126">x</span><span class="sxs-lookup"><span data-stu-id="c9f6b-126">x</span></span> | <span data-ttu-id="c9f6b-127">x</span><span class="sxs-lookup"><span data-stu-id="c9f6b-127">x</span></span> |
|<span data-ttu-id="c9f6b-128">Bot mit adaptiver Karte</span><span class="sxs-lookup"><span data-stu-id="c9f6b-128">Bot with Adaptive Card</span></span> | <span data-ttu-id="c9f6b-129">x</span><span class="sxs-lookup"><span data-stu-id="c9f6b-129">x</span></span> |  | <span data-ttu-id="c9f6b-130">x</span><span class="sxs-lookup"><span data-stu-id="c9f6b-130">x</span></span> |
| <span data-ttu-id="c9f6b-131">Keine Antwort</span><span class="sxs-lookup"><span data-stu-id="c9f6b-131">No response</span></span> | <span data-ttu-id="c9f6b-132">x</span><span class="sxs-lookup"><span data-stu-id="c9f6b-132">x</span></span> | <span data-ttu-id="c9f6b-133">x</span><span class="sxs-lookup"><span data-stu-id="c9f6b-133">x</span></span> | <span data-ttu-id="c9f6b-134">x</span><span class="sxs-lookup"><span data-stu-id="c9f6b-134">x</span></span> |

## <a name="the-submitaction-invoke-event"></a><span data-ttu-id="c9f6b-135">Das Submit-Aufrufereignis</span><span class="sxs-lookup"><span data-stu-id="c9f6b-135">The submitAction invoke event</span></span>

<span data-ttu-id="c9f6b-136">Im folgenden finden Sie Beispiele für den Empfang der Invoke-Nachricht.</span><span class="sxs-lookup"><span data-stu-id="c9f6b-136">Below are examples of receiving the invoke message.</span></span>

# <a name="cnettabdotnet"></a>[<span data-ttu-id="c9f6b-137">C#-/.net</span><span class="sxs-lookup"><span data-stu-id="c9f6b-137">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task<MessagingExtensionActionResponse> OnTeamsMessagingExtensionSubmitActionAsync(
  ITurnContext<IInvokeActivity> turnContext, MessagingExtensionAction action, CancellationToken cancellationToken) {
  //code to handle the submit action
}
```

# <a name="javascriptnodejstabjavascript"></a>[<span data-ttu-id="c9f6b-138">JavaScript/Node. js</span><span class="sxs-lookup"><span data-stu-id="c9f6b-138">JavaScript/Node.js</span></span>](#tab/javascript)

```javascript
class TeamsMessagingExtensionsActionPreview extends TeamsActivityHandler {
  constructor() {
  handleTeamsMessagingExtensionSubmitAction(context, action) {
  
  //code to handle the submit action
    }
  }
}
```

# <a name="jsontabjson"></a>[<span data-ttu-id="c9f6b-139">Json</span><span class="sxs-lookup"><span data-stu-id="c9f6b-139">JSON</span></span>](#tab/json)

<span data-ttu-id="c9f6b-140">Dies ist ein Beispiel für das JSON-Objekt, das Sie erhalten werden.</span><span class="sxs-lookup"><span data-stu-id="c9f6b-140">This is an example of the JSON object you will receive.</span></span> <span data-ttu-id="c9f6b-141">Der `commandContext` Parameter gibt an, woher Ihre Messaging-Erweiterung ausgelöst wurde.</span><span class="sxs-lookup"><span data-stu-id="c9f6b-141">The `commandContext` parameter indicates where your messaging extension was triggered from.</span></span> <span data-ttu-id="c9f6b-142">Das `data` -Objekt enthält die Felder auf dem Formular als Parameter und die Werte, die der Benutzer übermittelt hat.</span><span class="sxs-lookup"><span data-stu-id="c9f6b-142">The `data` object contains the fields on the form as parameters, and the values the user submitted.</span></span> <span data-ttu-id="c9f6b-143">Das JSON-Objekt wird hier verkürzt, um die relevantesten Felder hervorzuheben.</span><span class="sxs-lookup"><span data-stu-id="c9f6b-143">The JSON object here is shortened to highlight the most relevant fields.</span></span>

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

## <a name="respond-with-a-card-inserted-into-the-compose-message-area"></a><span data-ttu-id="c9f6b-144">Antworten mit einer im Nachrichtenbereich "Verfassen" eingefügten Karte</span><span class="sxs-lookup"><span data-stu-id="c9f6b-144">Respond with a card inserted into the compose message area</span></span>

<span data-ttu-id="c9f6b-145">Die häufigste Möglichkeit zur Reaktion auf die `composeExtension/submitAction` Anforderung ist eine Karte, die in den Bereich zum Verfassen von Nachrichten eingefügt wird.</span><span class="sxs-lookup"><span data-stu-id="c9f6b-145">The most common way to respond to the `composeExtension/submitAction` request is with a card inserted into the compose message area.</span></span> <span data-ttu-id="c9f6b-146">Der Benutzer kann dann beschließen, die Karte an die Unterhaltung zu senden.</span><span class="sxs-lookup"><span data-stu-id="c9f6b-146">The user can then choose to submit the card to the conversation.</span></span> <span data-ttu-id="c9f6b-147">Weitere Informationen zur Verwendung von Karten finden Sie unter [Cards and Card Actions](~/task-modules-and-cards/cards/cards-actions.md).</span><span class="sxs-lookup"><span data-stu-id="c9f6b-147">For more information on using cards see [cards and card actions](~/task-modules-and-cards/cards/cards-actions.md).</span></span>

# <a name="cnettabdotnet"></a>[<span data-ttu-id="c9f6b-148">C#-/.net</span><span class="sxs-lookup"><span data-stu-id="c9f6b-148">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task<MessagingExtensionActionResponse> OnTeamsMessagingExtensionSubmitActionAsync(
  ITurnContext<IInvokeActivity> turnContext, MessagingExtensionAction action, CancellationToken cancellationToken)
{
    dynamic Data = JObject.Parse(action.Data.ToString());
    var response = new MessagingExtensionActionResponse
    {
        ComposeExtension = new MessagingExtensionResult
        {
            AttachmentLayout = "list",
            Type = "result",
        },
    };
    var card = new HeroCard
    {
        Title = Data["formField1"] as string,
        Subtitle = Data["formField2"]  as string,
        Text = Data["formField3"]  as string,
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

# <a name="javascriptnodejstabjavascript"></a>[<span data-ttu-id="c9f6b-149">JavaScript/Node. js</span><span class="sxs-lookup"><span data-stu-id="c9f6b-149">JavaScript/Node.js</span></span>](#tab/javascript)

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

# <a name="jsontabjson"></a>[<span data-ttu-id="c9f6b-150">Json</span><span class="sxs-lookup"><span data-stu-id="c9f6b-150">JSON</span></span>](#tab/json)

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

## <a name="respond-with-another-task-module"></a><span data-ttu-id="c9f6b-151">Antworten mit einem anderen Aufgabenmodul</span><span class="sxs-lookup"><span data-stu-id="c9f6b-151">Respond with another task module</span></span>

<span data-ttu-id="c9f6b-152">Sie können beschließen, auf das `submitAction` Ereignis mit einem zusätzlichen Aufgabenmodul zu reagieren.</span><span class="sxs-lookup"><span data-stu-id="c9f6b-152">You can choose to respond to the `submitAction` event with an additional task module.</span></span> <span data-ttu-id="c9f6b-153">Dies kann hilfreich sein, wenn:</span><span class="sxs-lookup"><span data-stu-id="c9f6b-153">This can be useful when:</span></span>

* <span data-ttu-id="c9f6b-154">Sie müssen große Mengen an Informationen sammeln.</span><span class="sxs-lookup"><span data-stu-id="c9f6b-154">You need to collect large amounts of information.</span></span>
* <span data-ttu-id="c9f6b-155">Wenn Sie die gesammelten Informationen dynamisch basierend auf der Benutzereingabe ändern müssen</span><span class="sxs-lookup"><span data-stu-id="c9f6b-155">If you need to dynamically change what information you're collecting based on user input</span></span>
* <span data-ttu-id="c9f6b-156">Wenn Sie die vom Benutzer übermittelten Informationen validieren und das Formular möglicherweise mit einer Fehlermeldung erneut senden müssen, wenn etwas nicht stimmt.</span><span class="sxs-lookup"><span data-stu-id="c9f6b-156">If you need to validate the information submitted by the user and potentially resend the form with an error message if something is wrong.</span></span> 

<span data-ttu-id="c9f6b-157">Die Methode für die Antwort ist identisch mit der Reaktion [auf das `fetchTask` anfängliche Ereignis](~/messaging-extensions/how-to/action-commands/create-task-module.md).</span><span class="sxs-lookup"><span data-stu-id="c9f6b-157">The method for response is the same as [responding to the initial `fetchTask` event](~/messaging-extensions/how-to/action-commands/create-task-module.md).</span></span> <span data-ttu-id="c9f6b-158">Wenn Sie das bot Framework SDK verwenden, wird für beide Submit-Aktionen dasselbe Ereignis ausgelöst.</span><span class="sxs-lookup"><span data-stu-id="c9f6b-158">If you're using the Bot Framework SDK the same event will trigger for both submit actions.</span></span> <span data-ttu-id="c9f6b-159">Dies bedeutet, dass Sie unbedingt Logik hinzufügen müssen, die die richtige Antwort bestimmt.</span><span class="sxs-lookup"><span data-stu-id="c9f6b-159">This mean you need to be sure to add logic which determines the correct response.</span></span>

## <a name="bot-response-with-adaptive-card"></a><span data-ttu-id="c9f6b-160">Bot-Antwort mit adaptiver Karte</span><span class="sxs-lookup"><span data-stu-id="c9f6b-160">Bot response with Adaptive Card</span></span>

>[!Note]
><span data-ttu-id="c9f6b-161">Für diesen Fluss ist es erforderlich, `bot` dass Sie das Objekt Ihrem App-Manifest hinzufügen und dass Sie den erforderlichen Bereich für den bot definiert haben.</span><span class="sxs-lookup"><span data-stu-id="c9f6b-161">This flow requires that you add the `bot` object to your app manifest, and that you have the necessary scope defined for the bot.</span></span> <span data-ttu-id="c9f6b-162">Verwenden Sie dieselbe ID wie Ihre Messaging Erweiterung für Ihren bot.</span><span class="sxs-lookup"><span data-stu-id="c9f6b-162">Use the same Id as your messaging extension for your bot.</span></span>

<span data-ttu-id="c9f6b-163">Sie können auch auf die Submit-Aktion reagieren, indem Sie eine Nachricht mit einer adaptiven Karte in den Kanal mit einem bot einfügen.</span><span class="sxs-lookup"><span data-stu-id="c9f6b-163">You can also respond to the submit action by inserting a message with an Adaptive Card into the channel with a bot.</span></span> <span data-ttu-id="c9f6b-164">Der Benutzer kann die Nachricht in einer Vorschau anzeigen, bevor er ihn sendet, und möglicherweise auch mit ihm bearbeiten/interagieren.</span><span class="sxs-lookup"><span data-stu-id="c9f6b-164">Your user will be able to preview the message before submitting it, and potentially edit/interact with it as well.</span></span> <span data-ttu-id="c9f6b-165">Dies kann in Szenarien hilfreich sein, in denen Sie Informationen von Ihren Benutzern sammeln müssen, bevor Sie eine Adaptive Karten Antwort erstellen, oder wenn Sie die Karte aktualisieren müssen, nachdem eine Person mit ihr interagiert.</span><span class="sxs-lookup"><span data-stu-id="c9f6b-165">This can be very useful in scenarios where you need to gather information from your users before creating an adaptive card response, or when you're going to need to update the card after someone interacts with it.</span></span> <span data-ttu-id="c9f6b-166">Das folgende Szenario zeigt, wie die APP Polly diesen Fluss verwendet, um eine Umfrage zu konfigurieren, ohne die Konfigurationsschritte in der Kanal Unterhaltung zu unterbinden.</span><span class="sxs-lookup"><span data-stu-id="c9f6b-166">The following scenario shows how the app Polly uses this flow to configure a poll without including the configuration steps in the channel conversation.</span></span>

1. <span data-ttu-id="c9f6b-167">Der Benutzer klickt auf die Messaging Erweiterung, um den Aufgabenmodul auszulösen.</span><span class="sxs-lookup"><span data-stu-id="c9f6b-167">The user clicks the messaging extension to trigger the task module.</span></span>
2. <span data-ttu-id="c9f6b-168">Der Benutzer konfiguriert die Umfrage mit dem Task moudule.</span><span class="sxs-lookup"><span data-stu-id="c9f6b-168">The user configures the poll with the task moudule.</span></span>
3. <span data-ttu-id="c9f6b-169">Nach dem Senden des Aufgabenmoduls verwendet die APP die bereitgestellten Informationen, um die Umfrage als Adaptive Karte `botMessagePreview` zu erstellen und sendet sie als Antwort an den Client.</span><span class="sxs-lookup"><span data-stu-id="c9f6b-169">After submitting the task module the app uses the information provided to build the poll as an Adaptive Card and sends it as a `botMessagePreview` response to the client.</span></span>
4. <span data-ttu-id="c9f6b-170">Der Benutzer kann dann eine Vorschau der adaptiven Karten Nachricht anzeigen, bevor der bot ihn in den Kanal einfügt.</span><span class="sxs-lookup"><span data-stu-id="c9f6b-170">The user can then preview the adaptive card message before the bot inserts it into the channel.</span></span> <span data-ttu-id="c9f6b-171">Wenn die APP noch kein Mitglied des Kanals ist, wird Sie `Send` durch Klicken hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="c9f6b-171">If the app is not already a member of the channel, clicking `Send` will add the it.</span></span>
   1. <span data-ttu-id="c9f6b-172">Der Benutzer kann auch `Edit` die Nachricht auswählen, die Sie an das ursprüngliche Aufgabenmodul zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="c9f6b-172">The user can also chose to `Edit` the message, which returns them to the original task module.</span></span>
5. <span data-ttu-id="c9f6b-173">Bei der Interaktion mit der adaptiven Karte wird die Nachricht vor dem Senden geändert.</span><span class="sxs-lookup"><span data-stu-id="c9f6b-173">Interacting with the adaptive card changes the message before sending it.</span></span>
6. <span data-ttu-id="c9f6b-174">Nachdem der Benutzer auf `Send` den bot geklickt hat, sendet er die Nachricht an den Kanal.</span><span class="sxs-lookup"><span data-stu-id="c9f6b-174">Once the user clicks `Send` the bot posts the message to the channel.</span></span>

### <a name="respond-to-initial-submit-action"></a><span data-ttu-id="c9f6b-175">Reagieren auf die anfängliche Submit-Aktion</span><span class="sxs-lookup"><span data-stu-id="c9f6b-175">Respond to initial submit action</span></span>

<span data-ttu-id="c9f6b-176">Um diesen Fluss zu aktivieren, sollte Ihr Aufgabenmodul auf die `composeExtension/submitAction` anfängliche Nachricht mit einer Vorschau der Karte Antworten, die der bot an den Kanal senden wird.</span><span class="sxs-lookup"><span data-stu-id="c9f6b-176">To enable this flow your task module should respond to the initial `composeExtension/submitAction` message with a preview of the card that the bot will send to the channel.</span></span> <span data-ttu-id="c9f6b-177">Dies gibt dem Benutzer die Möglichkeit, die Karte vor dem senden zu überprüfen, und versucht außerdem, den bot in der Unterhaltung zu installieren, falls er noch nicht installiert ist.</span><span class="sxs-lookup"><span data-stu-id="c9f6b-177">This gives the user the opportunity to verify the card before sending, and also will attempt to install your bot in the conversation if it is not already installed.</span></span>

# <a name="cnettabdotnet"></a>[<span data-ttu-id="c9f6b-178">C#-/.net</span><span class="sxs-lookup"><span data-stu-id="c9f6b-178">C#/.NET</span></span>](#tab/dotnet)

```csharp
protected override async Task<MessagingExtensionActionResponse> OnTeamsMessagingExtensionSubmitActionAsync(
  ITurnContext<IInvokeActivity> turnContext, MessagingExtensionAction action, CancellationToken cancellationToken)
{
  dynamic Data = JObject.Parse(action.Data.ToString());
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

# <a name="javascriptnodejstabjavascript"></a>[<span data-ttu-id="c9f6b-179">JavaScript/Node. js</span><span class="sxs-lookup"><span data-stu-id="c9f6b-179">JavaScript/Node.js</span></span>](#tab/javascript)

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

# <a name="jsontabjson"></a>[<span data-ttu-id="c9f6b-180">Json</span><span class="sxs-lookup"><span data-stu-id="c9f6b-180">JSON</span></span>](#tab/json)

>[!Note]
><span data-ttu-id="c9f6b-181">Das `activityPreview` muss eine `message` Aktivität mit genau 1 adaptiver Karten Anlage enthalten.</span><span class="sxs-lookup"><span data-stu-id="c9f6b-181">The `activityPreview` must contain a `message` activity with exactly 1 adaptive card attachment.</span></span> <span data-ttu-id="c9f6b-182">Der `<< Card Payload >>` Wert ist ein Platzhalter für die Karte, die Sie senden möchten.</span><span class="sxs-lookup"><span data-stu-id="c9f6b-182">The `<< Card Payload >>` value is a placeholder for the card you wish to send.</span></span>

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

### <a name="the-botmessagepreview-send-and-edit-events"></a><span data-ttu-id="c9f6b-183">Das botMessagePreview-Ereignis zum Senden und bearbeiten</span><span class="sxs-lookup"><span data-stu-id="c9f6b-183">The botMessagePreview send and edit events</span></span>

<span data-ttu-id="c9f6b-184">Die Nachrichten Erweiterung muss nun auf zwei neue Varianten des `composeExtension/submitAction` Invoke-Objektes reagieren, wobei `value.botMessagePreviewAction = "send"`und `value.botMessagePreviewAction = "edit"`ist.</span><span class="sxs-lookup"><span data-stu-id="c9f6b-184">Your message extension will now need to respond to two new varieties of the `composeExtension/submitAction` invoke, where `value.botMessagePreviewAction = "send"`and `value.botMessagePreviewAction = "edit"`.</span></span>

# <a name="cnettabdotnet"></a>[<span data-ttu-id="c9f6b-185">C#-/.net</span><span class="sxs-lookup"><span data-stu-id="c9f6b-185">C#/.NET</span></span>](#tab/dotnet)

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

# <a name="javascriptnodejstabjavascript"></a>[<span data-ttu-id="c9f6b-186">JavaScript/Node. js</span><span class="sxs-lookup"><span data-stu-id="c9f6b-186">JavaScript/Node.js</span></span>](#tab/javascript)

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

# <a name="jsontabjson"></a>[<span data-ttu-id="c9f6b-187">Json</span><span class="sxs-lookup"><span data-stu-id="c9f6b-187">JSON</span></span>](#tab/json)

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

### <a name="respond-to-botmessagepreview-edit"></a><span data-ttu-id="c9f6b-188">Reagieren auf botMessagePreview Edit</span><span class="sxs-lookup"><span data-stu-id="c9f6b-188">Respond to botMessagePreview edit</span></span>

<span data-ttu-id="c9f6b-189">Wenn der Benutzer entscheidet, die Karte vor dem senden zu bearbeiten, \*\*\*\* indem er auf die Schaltfläche Bearbeiten `composeExtension/submitAction` klickt, `value.botMessagePreviewAction = edit`wird ein Invoke mit angezeigt.</span><span class="sxs-lookup"><span data-stu-id="c9f6b-189">If the user decides to edit the card before sending by clicking the **Edit** button, you will receive a `composeExtension/submitAction` invoke with `value.botMessagePreviewAction = edit`.</span></span> <span data-ttu-id="c9f6b-190">Sie sollten in der Regel durch Zurückgeben des Aufgabenmoduls Antworten, das Sie `composeExtension/fetchTask` als Antwort auf die anfängliche Invoke gesendet haben, die die Interaktion begann.</span><span class="sxs-lookup"><span data-stu-id="c9f6b-190">You should typically respond by returning the task module you sent in response to the initial `composeExtension/fetchTask` invoke that began the interaction.</span></span> <span data-ttu-id="c9f6b-191">Dadurch kann der Benutzer den Prozess über die erneute Eingabe der ursprünglichen Informationen starten.</span><span class="sxs-lookup"><span data-stu-id="c9f6b-191">This allows the user to start the process over by re-entering the original information.</span></span> <span data-ttu-id="c9f6b-192">Sie sollten auch die Informationen verwenden, die Sie jetzt zur Verfügung haben, um den Aufgabenmodul vorab aufzufüllen, damit der Benutzer nicht alle Informationen aus dem nichts ausfüllt.</span><span class="sxs-lookup"><span data-stu-id="c9f6b-192">You should also consider using the information you now have available to pre-populate the task module so the user doesn't have fill out all of the information from scratch.</span></span>

<span data-ttu-id="c9f6b-193">Siehe [Antworten auf das `fetchTask` anfängliche Ereignis](~/messaging-extensions/how-to/action-commands/create-task-module.md).</span><span class="sxs-lookup"><span data-stu-id="c9f6b-193">See [responding to the initial `fetchTask` event](~/messaging-extensions/how-to/action-commands/create-task-module.md).</span></span>

### <a name="respond-to-botmessagepreview-send"></a><span data-ttu-id="c9f6b-194">Auf botMessagePreview senden Antworten</span><span class="sxs-lookup"><span data-stu-id="c9f6b-194">Respond to botMessagePreview send</span></span>

<span data-ttu-id="c9f6b-195">Nachdem der Benutzer auf die Schaltfläche **senden** geklickt hat, wird `composeExtension/submitAction` ein Aufruf `value.botMessagePreviewAction = send`mit angezeigt.</span><span class="sxs-lookup"><span data-stu-id="c9f6b-195">Once the user clicks the **Send** button, you will receive a `composeExtension/submitAction` invoke with `value.botMessagePreviewAction = send`.</span></span> <span data-ttu-id="c9f6b-196">Ihr Webdienst muss eine proaktive Nachricht mit der adaptiven Karte an die Unterhaltung erstellen und senden und auch auf die Invoke Antworten.</span><span class="sxs-lookup"><span data-stu-id="c9f6b-196">Your web service will need to create and send a proactive message with the Adaptive Card to the conversation, and also reply to the invoke.</span></span>

# <a name="cnettabdotnet"></a>[<span data-ttu-id="c9f6b-197">C#-/.net</span><span class="sxs-lookup"><span data-stu-id="c9f6b-197">C#/.NET</span></span>](#tab/dotnet)

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
  
  await turnContext.SendActivityAsync(responseActivity);

  return new MessagingExtensionActionResponse();
}
```

# <a name="javascriptnodejstabjavascript"></a>[<span data-ttu-id="c9f6b-198">JavaScript/Node. js</span><span class="sxs-lookup"><span data-stu-id="c9f6b-198">JavaScript/Node.js</span></span>](#tab/javascript)

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
      const responseActivity = { type: 'message', attachments: [adaptiveCard] };
    
      await context.sendActivity(responseActivity);
    }
}
```

# <a name="jsontabjson"></a>[<span data-ttu-id="c9f6b-199">Json</span><span class="sxs-lookup"><span data-stu-id="c9f6b-199">JSON</span></span>](#tab/json)

<span data-ttu-id="c9f6b-200">Sie erhalten eine neue `composeExtension/submitAction` Nachricht, die der folgenden ähnlich ist.</span><span class="sxs-lookup"><span data-stu-id="c9f6b-200">You will receive a new `composeExtension/submitAction` message similar to the one below.</span></span>

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

## <a name="next-steps"></a><span data-ttu-id="c9f6b-201">Nächste Schritte</span><span class="sxs-lookup"><span data-stu-id="c9f6b-201">Next Steps</span></span>

<span data-ttu-id="c9f6b-202">Hinzufügen eines Suchbefehls</span><span class="sxs-lookup"><span data-stu-id="c9f6b-202">Add a search command</span></span>

* [<span data-ttu-id="c9f6b-203">Definieren von Suchbefehlen</span><span class="sxs-lookup"><span data-stu-id="c9f6b-203">Define search commands</span></span>](~/messaging-extensions/how-to/search-commands/define-search-command.md)

[!include[messaging-extension-learn-more](~/includes/messaging-extensions/learn-more.md)]
