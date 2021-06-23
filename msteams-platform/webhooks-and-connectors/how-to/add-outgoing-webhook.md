---
title: Hinzufügen von benutzerdefinierten Bots zu Microsoft Teams mit ausgehenden Webhooks
description: beschreibt, wie ein ausgehender Webhook hinzugefügt wird
ms.topic: conceptual
ms.author: lajanuar
localization_priority: Normal
keywords: Teams-Registerkarten ausgehende Webhook-Nachricht mit Aktionen überprüfen Webhook
ms.openlocfilehash: 2fac6f42e27a4c8cb3d079ea281d458a4dfe41ed
ms.sourcegitcommit: 623d81eb079d1842813265746a5fe0fe6311b196
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/22/2021
ms.locfileid: "53069182"
---
# <a name="add-custom-bots-to-teams-with-outgoing-webhooks"></a><span data-ttu-id="269a7-104">Hinzufügen von benutzerdefinierten Bots zu Teams mit ausgehenden Webhooks</span><span class="sxs-lookup"><span data-stu-id="269a7-104">Add custom bots to Teams with outgoing webhooks</span></span>

## <a name="outgoing-webhooks-in-teams"></a><span data-ttu-id="269a7-105">Ausgehende Webhooks in Teams</span><span class="sxs-lookup"><span data-stu-id="269a7-105">Outgoing webhooks in Teams</span></span>

<span data-ttu-id="269a7-106">Webhooks sind eine hervorragende Möglichkeit für Teams die Integration in externe Apps.</span><span class="sxs-lookup"><span data-stu-id="269a7-106">Webhooks are an eminent way for Teams to integrate with external apps.</span></span> <span data-ttu-id="269a7-107">Ein Webhook ist im Wesentlichen eine POST-Anforderung, die an eine Rückruf-URL gesendet wird.</span><span class="sxs-lookup"><span data-stu-id="269a7-107">A webhook is essentially a POST request sent to a callback URL.</span></span> <span data-ttu-id="269a7-108">Ausgehende Webhooks ermöglichen Benutzern das Senden von Nachrichten an Ihren Webdienst, ohne den vollständigen Prozess der Erstellung von Bots über die Microsoft Bot Framework durchlaufen zu [müssen.](https://dev.botframework.com/)</span><span class="sxs-lookup"><span data-stu-id="269a7-108">Outgoing webhooks allow users to send messages to your web service without going through the full process of creating bots via the [Microsoft Bot Framework](https://dev.botframework.com/).</span></span>

<span data-ttu-id="269a7-109">Ausgehender Webhook sendet Daten von Teams an einen beliebigen ausgewählten Dienst, der eine JSON-Nutzlast akzeptieren kann.</span><span class="sxs-lookup"><span data-stu-id="269a7-109">Outgoing webhook sends data from Teams to any chosen service capable of accepting a JSON payload.</span></span> <span data-ttu-id="269a7-110">Nachdem sie die ausgehenden Webhooks zu einem Team hinzugefügt haben, fungiert sie als Bot und sucht mit **\@ erwähnungen** nach Nachrichten in Kanälen.</span><span class="sxs-lookup"><span data-stu-id="269a7-110">After adding the outgoing webhooks to a team, it acts as a bot and looks for messages in channels using **\@mention**.</span></span> <span data-ttu-id="269a7-111">Es sendet Benachrichtigungen an externe Webdienste und antwortet mit umfangreichen Nachrichten, die Karten und Bilder enthalten.</span><span class="sxs-lookup"><span data-stu-id="269a7-111">It sends notifications to external web services and responds with rich messages, which include cards and images.</span></span>

## <a name="outgoing-webhook-key-features"></a><span data-ttu-id="269a7-112">Ausgehende Webhook-Schlüsselfeatures</span><span class="sxs-lookup"><span data-stu-id="269a7-112">Outgoing webhook key features</span></span>

| <span data-ttu-id="269a7-113">Feature</span><span class="sxs-lookup"><span data-stu-id="269a7-113">Feature</span></span> | <span data-ttu-id="269a7-114">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="269a7-114">Description</span></span> |
| ------- | ----------- |
| <span data-ttu-id="269a7-115">Bereichskonfiguration</span><span class="sxs-lookup"><span data-stu-id="269a7-115">Scoped configuration</span></span>| <span data-ttu-id="269a7-116">Webhooks sind auf Teamebene beschränkt.</span><span class="sxs-lookup"><span data-stu-id="269a7-116">Webhooks are scoped at the team level.</span></span> <span data-ttu-id="269a7-117">Sie müssen den Einrichtungsprozess für jedes Team durchlaufen, in dem Sie Ihren ausgehenden Webhook hinzufügen möchten.</span><span class="sxs-lookup"><span data-stu-id="269a7-117">You must go through the setup process for each team where you want to add your outgoing webhook.</span></span> |
| <span data-ttu-id="269a7-118">Reaktives Messaging</span><span class="sxs-lookup"><span data-stu-id="269a7-118">Reactive messaging</span></span>| <span data-ttu-id="269a7-119">Benutzer müssen @mention verwenden, damit der Webhook Nachrichten empfängt.</span><span class="sxs-lookup"><span data-stu-id="269a7-119">Users must use @mention for the webhook to receive messages.</span></span> <span data-ttu-id="269a7-120">Derzeit können Benutzer nur einen ausgehenden Webhook in öffentlichen Kanälen und nicht innerhalb des persönlichen oder privaten Bereichs senden.</span><span class="sxs-lookup"><span data-stu-id="269a7-120">Currently, users can only message an outgoing webhook in public channels and not within the personal or private scope.</span></span> |
|<span data-ttu-id="269a7-121">Standardmäßiger HTTP-Nachrichtenaustausch</span><span class="sxs-lookup"><span data-stu-id="269a7-121">Standard HTTP message exchange</span></span>|<span data-ttu-id="269a7-122">Antworten werden in derselben Kette wie die ursprüngliche Anforderungsnachricht angezeigt und können beliebige Bot-Framework-Nachrichteninhalte enthalten, z. B. Rich-Text, Bilder, Karten und Emojis.</span><span class="sxs-lookup"><span data-stu-id="269a7-122">Responses appear in the same chain as the original request message and can include any bot framework message content, for example, rich text, images, cards, and emojis.</span></span> <span data-ttu-id="269a7-123">Ausgehende Webhooks können zwar Karten verwenden, jedoch keine Kartenaktionen außer `openURL` .</span><span class="sxs-lookup"><span data-stu-id="269a7-123">Although outgoing webhooks can use cards, they cannot use any card actions except for `openURL`.</span></span>|
| <span data-ttu-id="269a7-124">Teams API-Methodenunterstützung</span><span class="sxs-lookup"><span data-stu-id="269a7-124">Teams API method support</span></span>|<span data-ttu-id="269a7-125">Ausgehender Webhook sendet einen HTTP POST an einen Webdienst und verarbeitet eine Antwort zurück.</span><span class="sxs-lookup"><span data-stu-id="269a7-125">Outgoing webhook sends an HTTP POST to a web service and process a response back.</span></span> <span data-ttu-id="269a7-126">Sie können nicht auf andere APIs zugreifen, z. B. um die Liste oder die Liste der Kanäle in einem Team abzurufen.</span><span class="sxs-lookup"><span data-stu-id="269a7-126">They cannot access any other APIs like retrieve the roster or list of channels in a team.</span></span>|

## <a name="creating-actionable-messages"></a><span data-ttu-id="269a7-127">Erstellen von Nachrichten mit Aktionen</span><span class="sxs-lookup"><span data-stu-id="269a7-127">Creating actionable messages</span></span>

<span data-ttu-id="269a7-128">Die Connectorkarten enthalten drei sichtbare Schaltflächen auf der Karte.</span><span class="sxs-lookup"><span data-stu-id="269a7-128">The connector cards include three visible buttons on the card.</span></span> <span data-ttu-id="269a7-129">Jede Schaltfläche wird in der `potentialAction` Eigenschaft der Nachricht mithilfe von Aktionen `ActionCard` definiert.</span><span class="sxs-lookup"><span data-stu-id="269a7-129">Each button is defined in the `potentialAction` property of the message by using `ActionCard` actions.</span></span> <span data-ttu-id="269a7-130">Jeder `ActionCard` enthält einen Eingabetyp, ein Textfeld, eine Datumsauswahl oder eine Mehrfachauswahlliste.</span><span class="sxs-lookup"><span data-stu-id="269a7-130">Each `ActionCard` contains an input type; a text field, a date picker, or a multi-choice list.</span></span> <span data-ttu-id="269a7-131">Jeder `ActionCard` Aktion ist eine Aktion zugeordnet, `HttpPOST` z. B. .</span><span class="sxs-lookup"><span data-stu-id="269a7-131">Each `ActionCard` action has an associated action, for example, `HttpPOST`.</span></span>

<span data-ttu-id="269a7-132">Connectorkarten unterstützen drei Arten von Aktionen:</span><span class="sxs-lookup"><span data-stu-id="269a7-132">Connector cards support three types of actions:</span></span>

| <span data-ttu-id="269a7-133">Aktion</span><span class="sxs-lookup"><span data-stu-id="269a7-133">Action</span></span> | <span data-ttu-id="269a7-134">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="269a7-134">Description</span></span> |
| ------- | ----------- |
| `ActionCard` |<span data-ttu-id="269a7-135">Stellt einen oder mehrere Eingabetypen und zugeordnete Aktionen dar.</span><span class="sxs-lookup"><span data-stu-id="269a7-135">Presents one or more input types and associated actions.</span></span>|
| `HttpPOST` | <span data-ttu-id="269a7-136">Sendet eine POST-Anforderung an eine URL.</span><span class="sxs-lookup"><span data-stu-id="269a7-136">Sends a POST request to a URL.</span></span> |
| `OpenUri` |  <span data-ttu-id="269a7-137">Öffnet einen URI in einem separaten Browser oder einer separaten App und richtet sich optional auf unterschiedliche URIs basierend auf Betriebssystemen.</span><span class="sxs-lookup"><span data-stu-id="269a7-137">Opens a URI in a separate browser or app, optionally targets different URIs based on operating systems.</span></span>|

<span data-ttu-id="269a7-138">Die `ActionCard`-Aktion unterstützt drei Eingabetypen:</span><span class="sxs-lookup"><span data-stu-id="269a7-138">The `ActionCard` action supports three input types:</span></span>

| <span data-ttu-id="269a7-139">Eingabetyp</span><span class="sxs-lookup"><span data-stu-id="269a7-139">Input type</span></span> | <span data-ttu-id="269a7-140">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="269a7-140">Description</span></span> |
| ------- | ----------- |
| `TextInput` | <span data-ttu-id="269a7-141">Ein einzeiliges oder mehrzeiliges Textfeld mit optionaler Längenbeschränkung.</span><span class="sxs-lookup"><span data-stu-id="269a7-141">A single-line or multiline text field with an optional length limit.</span></span> |
| `DateInput` | <span data-ttu-id="269a7-142">Eine Datumsauswahl mit einer optionalen Uhrzeitauswahl.</span><span class="sxs-lookup"><span data-stu-id="269a7-142">A date selector with an optional time selector.</span></span> |
| `MultichoiceInput` | <span data-ttu-id="269a7-143">Eine angegebene Liste von Auswahlmöglichkeiten, die entweder eine einzelne oder mehrere Auswahlmöglichkeiten bietet.</span><span class="sxs-lookup"><span data-stu-id="269a7-143">A specified list of choices, offering either a single selection or multiple selections.</span></span>|

<span data-ttu-id="269a7-144">`MultichoiceInput` unterstützt eine `style` Eigenschaft, die die Anzeige einer vollständig erweiterten Liste steuert.</span><span class="sxs-lookup"><span data-stu-id="269a7-144">`MultichoiceInput` supports a `style` property that controls the display of a fully expanded list.</span></span> <span data-ttu-id="269a7-145">Der Standardwert von `style` hängt vom `isMultiSelect` Wert ab.</span><span class="sxs-lookup"><span data-stu-id="269a7-145">The default value of `style` depends on the `isMultiSelect` value.</span></span>

| <span data-ttu-id="269a7-146">`isMultiSelect` Wert</span><span class="sxs-lookup"><span data-stu-id="269a7-146">`isMultiSelect` value</span></span>  | <span data-ttu-id="269a7-147">`style` Standardwert</span><span class="sxs-lookup"><span data-stu-id="269a7-147">`style` default value</span></span>  |
| --- | --- |
| <span data-ttu-id="269a7-148">`false` oder nicht angegeben</span><span class="sxs-lookup"><span data-stu-id="269a7-148">`false` or not specified</span></span> | <span data-ttu-id="269a7-149">Der Standardstil lautet `compact`</span><span class="sxs-lookup"><span data-stu-id="269a7-149">The default style is `compact`</span></span>|
| `true` | <span data-ttu-id="269a7-150">Der Standardstil lautet `expanded`</span><span class="sxs-lookup"><span data-stu-id="269a7-150">The default style is `expanded`</span></span> |

> [!NOTE]
> * <span data-ttu-id="269a7-151">Geben Sie sowohl `"isMultiSelect": true` und , wenn die `"style": true` Mehrfachauswahlliste in einer kompakten Formatvorlage angezeigt werden soll.</span><span class="sxs-lookup"><span data-stu-id="269a7-151">Enter both `"isMultiSelect": true` and `"style": true`, if you want the multi-select list to be displayed in a compact style.</span></span>
> * <span data-ttu-id="269a7-152">Das Auswählen `compact` der Eigenschaft in Teams `style` entspricht der Auswahl für die `normal` Eigenschaft in Microsoft `style` Outlook.</span><span class="sxs-lookup"><span data-stu-id="269a7-152">Selecting `compact` for the `style` property in Teams is the same as selecting `normal` for the `style` property in Microsoft Outlook.</span></span>
> * <span data-ttu-id="269a7-153">Webhooks unterstützen nur Office 365 Nachrichtenrückmeldungskarten und adaptive Karten.</span><span class="sxs-lookup"><span data-stu-id="269a7-153">Webhooks support only Office 365 message back cards and adaptive cards.</span></span>

<span data-ttu-id="269a7-154">Weitere Informationen zu Connectorkartenaktionen finden Sie unter **["Aktionen"](/outlook/actionable-messages/card-reference#actions)** in der Referenz zur Nachrichtenkarte mit Aktionen.</span><span class="sxs-lookup"><span data-stu-id="269a7-154">For all other details about connector card actions, see **[Actions](/outlook/actionable-messages/card-reference#actions)** in the actionable message card reference.</span></span>

## <a name="adding-outgoing-webhooks-to-your-app"></a><span data-ttu-id="269a7-155">Hinzufügen ausgehender Webhooks zu Ihrer App</span><span class="sxs-lookup"><span data-stu-id="269a7-155">Adding outgoing webhooks to your app</span></span>

<span data-ttu-id="269a7-156">**Szenario:** Pushänderungsstatusbenachrichtigungen auf einem Teams Kanaldatenbankserver an Ihre App.</span><span class="sxs-lookup"><span data-stu-id="269a7-156">**Scenario**: Push change status notifications on a Teams channel database server to your app.</span></span>  
<span data-ttu-id="269a7-157">**Beispiel:** Sie verfügen über eine Branchen-App, die alle CRUD-Vorgänge nachzeichnet, die von Teams Hr-Benutzern über einen Office 365 Mandanten hinweg an Mitarbeiterdatensätzen vorgenommen wurden.</span><span class="sxs-lookup"><span data-stu-id="269a7-157">**Example**: You have a line-of-business app that tracks all CRUD operations made to employee records by Teams channel HR users across an Office 365 tenancy.</span></span>

### <a name="1-create-a-url-on-your-apps-server-to-accept-and-process-a-post-request-with-a-json-payload"></a><span data-ttu-id="269a7-158">1. Erstellen Sie eine URL auf dem Server Ihrer App, um eine POST-Anforderung mit einer JSON-Nutzlast zu akzeptieren und zu verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="269a7-158">1. Create a URL on your app's server to accept and process a POST request with a JSON payload</span></span>

<span data-ttu-id="269a7-159">Ihr Dienst empfängt Nachrichten in einem standardmäßigen Nachrichtenschema des Azure-Botdiensts.</span><span class="sxs-lookup"><span data-stu-id="269a7-159">Your service receives messages in a standard Azure bot service messaging schema.</span></span> <span data-ttu-id="269a7-160">Der Bot Framework-Connector ist ein REST-Dienst, der Es Ihrem Dienst ermöglicht, den Austausch von JSON-formatierten Nachrichten über HTTPS-Protokolle zu verarbeiten, wie in der [Azure Bot Service-API](/bot-framework/rest-api/bot-framework-rest-connector-api-reference)dokumentiert.</span><span class="sxs-lookup"><span data-stu-id="269a7-160">The bot framework connector is a RESTful service that empowers your service to process the interchange of JSON formatted messages via HTTPS protocols as documented in the [Azure Bot Service API](/bot-framework/rest-api/bot-framework-rest-connector-api-reference).</span></span> <span data-ttu-id="269a7-161">Alternativ können Sie dem [Microsoft Bot Framework SDK] folgen, um Nachrichten zu verarbeiten und zu analysieren.</span><span class="sxs-lookup"><span data-stu-id="269a7-161">Alternatively, you can follow the [Microsoft Bot Framework SDK] to process and parse messages.</span></span> <span data-ttu-id="269a7-162">Siehe auch [Informationen zum Azure Bot Service.](/azure/bot-service/bot-service-overview-introduction)</span><span class="sxs-lookup"><span data-stu-id="269a7-162">See also [About Azure Bot Service](/azure/bot-service/bot-service-overview-introduction).</span></span>


<span data-ttu-id="269a7-163">Ausgehende Webhooks sind auf die Ebene beschränkt `team` und für alle Teammitglieder sichtbar.</span><span class="sxs-lookup"><span data-stu-id="269a7-163">Outgoing webhooks are scoped to the `team` level and are visible to all the team members.</span></span> <span data-ttu-id="269a7-164">Genau wie bei einem Bot müssen Benutzer den Namen des ausgehenden Webhooks **\@ erwähnen,** um ihn im Kanal aufzurufen.</span><span class="sxs-lookup"><span data-stu-id="269a7-164">Just like a bot, users need to **\@mention** the name of the outgoing webhook to invoke it in the channel.</span></span>

### <a name="2-create-a-method-to-verify-the-outgoing-webhook-hmac-token"></a><span data-ttu-id="269a7-165">2. Erstellen einer Methode zum Überprüfen des ausgehenden Webhook-HMAC-Tokens</span><span class="sxs-lookup"><span data-stu-id="269a7-165">2. Create a method to verify the outgoing webhook HMAC token</span></span>

#### <a name="hmac-signature-for-testing-with-code-example"></a><span data-ttu-id="269a7-166">HMAC-Signatur für Tests mit Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="269a7-166">HMAC signature for testing with code example</span></span>

<span data-ttu-id="269a7-167">Using example of inbound message and id: "contoso" of SigningKeyDictionary of {"contoso", "vqF0En+Z0ucuRTM/01o2GuhMH3hKKk/N2bOmlM31zaA=" }.</span><span class="sxs-lookup"><span data-stu-id="269a7-167">Using example of inbound message and id: "contoso" of SigningKeyDictionary of {"contoso", "vqF0En+Z0ucuRTM/01o2GuhMH3hKKk/N2bOmlM31zaA=" }.</span></span>

<span data-ttu-id="269a7-168">Verwenden Sie den Wert "HMAC 03TCao0i55H1eVKUusZOTZRjtvYTs+mO41mPL+R1e1U=" in der Autorisierung des Anforderungsheaders.</span><span class="sxs-lookup"><span data-stu-id="269a7-168">Use the value "HMAC 03TCao0i55H1eVKUusZOTZRjtvYTs+mO41mPL+R1e1U=" in the authorization of request header.</span></span>

<span data-ttu-id="269a7-169">Um sicherzustellen, dass Ihr Dienst nur Aufrufe von tatsächlichen Teams Clients empfängt, stellt Teams einen HMAC-Code im `hmac` HTTP-Header bereit.</span><span class="sxs-lookup"><span data-stu-id="269a7-169">To ensure that your service is receiving calls only from actual Teams clients, Teams provides an HMAC code in the HTTP `hmac` header.</span></span> <span data-ttu-id="269a7-170">Enthalten Sie immer den Code in Ihrem Authentifizierungsprotokoll.</span><span class="sxs-lookup"><span data-stu-id="269a7-170">Always included the code in your authentication protocol.</span></span>

<span data-ttu-id="269a7-171">Ihr Code muss immer die HMAC-Signatur überprüfen, die in der Anforderung enthalten ist:</span><span class="sxs-lookup"><span data-stu-id="269a7-171">Your code must always validate the HMAC signature included in the request:</span></span>

* <span data-ttu-id="269a7-172">Generieren Sie das HMAC-Token aus dem Anforderungstext der Nachricht.</span><span class="sxs-lookup"><span data-stu-id="269a7-172">Generate the HMAC token from the request body of the message.</span></span> <span data-ttu-id="269a7-173">Es gibt Standardbibliotheken, um dies auf den meisten Plattformen zu tun (siehe [Crypto](https://nodejs.org/api/crypto.html#crypto_crypto) für Node.js oder [Teams Webhook-Beispiel](https://github.com/OfficeDev/microsoft-teams-sample-outgoing-webhook/blob/23eb61da5a18634d51c5247944843da9abed01b6/WebhookSampleBot/Models/AuthProvider.cs) für \# C).</span><span class="sxs-lookup"><span data-stu-id="269a7-173">There are standard libraries to do this on most platforms (see [Crypto](https://nodejs.org/api/crypto.html#crypto_crypto) for Node.js or see [Teams Webhook Sample](https://github.com/OfficeDev/microsoft-teams-sample-outgoing-webhook/blob/23eb61da5a18634d51c5247944843da9abed01b6/WebhookSampleBot/Models/AuthProvider.cs) for C\#).</span></span> <span data-ttu-id="269a7-174">Microsoft Teams verwendet standard SHA256 HMAC-Kryptografie.</span><span class="sxs-lookup"><span data-stu-id="269a7-174">Microsoft Teams uses standard SHA256 HMAC cryptography.</span></span> <span data-ttu-id="269a7-175">Sie müssen den Textkörper in UTF8 in ein Bytearray konvertieren.</span><span class="sxs-lookup"><span data-stu-id="269a7-175">You need to convert the body to a byte array in UTF8.</span></span>
* <span data-ttu-id="269a7-176">Berechnen Sie den Hash aus dem Bytearray des Sicherheitstokens, das **von Teams bereitgestellt wird,** wenn Sie den ausgehenden Webhook im Teams-Client registriert haben].</span><span class="sxs-lookup"><span data-stu-id="269a7-176">Compute the hash from the byte array of the security token **provided by Teams** when you registered the outgoing webhook in the Teams client].</span></span> <span data-ttu-id="269a7-177">Siehe [Erstellen eines ausgehenden Webhooks.](#create-an-outgoing-webhook)</span><span class="sxs-lookup"><span data-stu-id="269a7-177">See [Create an outgoing webhook](#create-an-outgoing-webhook).</span></span>
* <span data-ttu-id="269a7-178">Konvertieren Sie den Hash in eine Zeichenfolge mithilfe der UTF-8-Codierung.</span><span class="sxs-lookup"><span data-stu-id="269a7-178">Convert the hash to a string using UTF-8 encoding.</span></span>
* <span data-ttu-id="269a7-179">Vergleichen Sie den Zeichenfolgenwert des generierten Hash mit dem in der HTTP-Anforderung angegebenen Wert.</span><span class="sxs-lookup"><span data-stu-id="269a7-179">Compare the string value of the generated hash with the value provided in the HTTP request.</span></span>

### <a name="3-create-a-method-to-send-a-success-or-failure-response"></a><span data-ttu-id="269a7-180">3. Erstellen einer Methode zum Senden einer Erfolgs- oder Fehlerantwort</span><span class="sxs-lookup"><span data-stu-id="269a7-180">3. Create a method to send a success or failure response</span></span>

<span data-ttu-id="269a7-181">Antworten von ausgehenden Webhooks werden in der gleichen Antwortkette wie die ursprüngliche Nachricht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="269a7-181">Responses from your outgoing webhooks appear in the same reply chain as the original message.</span></span> <span data-ttu-id="269a7-182">Wenn der Benutzer eine Abfrage ausführt, gibt Microsoft Teams eine synchrone HTTP-Anforderung an Ihren Dienst aus, und Ihr Code erhält fünf Sekunden, um auf die Nachricht zu antworten, bevor die Verbindung ein Zeitüberschreitung auftritt und beendet wird.</span><span class="sxs-lookup"><span data-stu-id="269a7-182">When the user performs a query, Microsoft Teams issues a synchronous HTTP request to your service and your code gets five seconds to respond to the message before the connection times out and terminates.</span></span>

### <a name="example-response"></a><span data-ttu-id="269a7-183">Beispielantwort</span><span class="sxs-lookup"><span data-stu-id="269a7-183">Example response</span></span>

```json
{
    "type": "message",
    "text": "This is a reply!"
}
```

> [!NOTE]
> * <span data-ttu-id="269a7-184">Sie können adaptive Karte, Hero-Karte und Textnachrichten als Anlage mit ausgehenden Webhooks senden.</span><span class="sxs-lookup"><span data-stu-id="269a7-184">You can send Adaptive Card, Hero card, and text messages as attachment with outgoing webhook.</span></span>
> * <span data-ttu-id="269a7-185">Karten unterstützen die Formatierung.</span><span class="sxs-lookup"><span data-stu-id="269a7-185">Cards support formatting.</span></span> <span data-ttu-id="269a7-186">Weitere Informationen finden Sie unter [Formatieren von Karten mit Markdown.](~/task-modules-and-cards/cards/cards-format.md?tabs=adaptive-md%2Cconnector-html#formatting-cards-with-markdown)</span><span class="sxs-lookup"><span data-stu-id="269a7-186">For more information, see [format cards with markdown](~/task-modules-and-cards/cards/cards-format.md?tabs=adaptive-md%2Cconnector-html#formatting-cards-with-markdown).</span></span>

<span data-ttu-id="269a7-187">Die folgenden Codes sind Beispiele für eine Adaptive Kartenantwort:</span><span class="sxs-lookup"><span data-stu-id="269a7-187">Following codes are examples of an Adaptive Card response:</span></span>

# <a name="cnet"></a>[<span data-ttu-id="269a7-188">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="269a7-188">C#/.NET</span></span>](#tab/dotnet)

```csharp
string content = await this.Request.Content.ReadAsStringAsync();
Activity incomingActivity = JsonConvert.DeserializeObject<Activity>(content);

var Card = new AdaptiveCard(new AdaptiveSchemaVersion("1.4"))
{
    Body = new List<AdaptiveElement>()
    {
        new AdaptiveTextBlock(){Text= $"Request sent by: {incomingActivity.From.Name}"},
        new AdaptiveImage(){Url=new Uri("https://c.s-microsoft.com/en-us/CMSImages/DesktopContent-04_UPDATED.png?version=43c80870-99dd-7fb1-48c0-59aced085ab6")},
        new AdaptiveTextBlock(){Text="Sample image for Adaptive Card.."}
    }
};

var attachment = new Attachment()
{
    ContentType = AdaptiveCard.ContentType,
    Content = Card
};

var sampleResponseActivity = new Activity
{
    Attachments = new [] { attachment }
};

return sampleResponseActivity;
```

# <a name="javascriptnodejs"></a>[<span data-ttu-id="269a7-189">JavaScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="269a7-189">JavaScript/Node.js</span></span>](#tab/javascript)

```javascript
var receivedMsg = JSON.parse(payload);
var responseMsg = JSON.stringify({
    "type": "message",
    "attachments": [
        {
            "contentType": "application/vnd.microsoft.card.adaptive",
            "contentUrl": null,
            "content": {
                "type": "AdaptiveCard",
                "version": "1.4",
                "body": [
                    {
                        "type": "TextBlock",
                        "text": "Request sent by: " + receivedMsg.from.name
                    },
                    {
                        "type": "Image",
                        "url": "https://c.s-microsoft.com/en-us/CMSImages/DesktopContent-04_UPDATED.png?version=43c80870-99dd-7fb1-48c0-59aced085ab6"
                    },
                    {
                        "type": "TextBlock",
                        "text": "Sample image for Adaptive Card."
                    }
                ]
            },
            "name": null,
            "thumbnailUrl": null
        }
    ]
});
```

# <a name="json"></a>[<span data-ttu-id="269a7-190">Json</span><span class="sxs-lookup"><span data-stu-id="269a7-190">JSON</span></span>](#tab/json)

```json
{
    "type": "message",
    "attachments": [
        {
            "contentType": "application/vnd.microsoft.card.adaptive",
            "content": {
                "type": "AdaptiveCard",
                "version": "1.4",
                "body": [
                    {
                        "type": "TextBlock",
                        "text": "Request sent by: Megan"
                    },
                    {
                        "type": "Image",
                        "url": "https://c.s-microsoft.com/en-us/CMSImages/DesktopContent-04_UPDATED.png?version=43c80870-99dd-7fb1-48c0-59aced085ab6"
                    },
                    {
                        "type": "TextBlock",
                        "text": "Sample image for Adaptive Card.."
                    }
                ]
            }
        }
    ]
}
```

* * *

## <a name="create-an-outgoing-webhook"></a><span data-ttu-id="269a7-191">Erstellen eines ausgehenden Webhooks</span><span class="sxs-lookup"><span data-stu-id="269a7-191">Create an outgoing webhook</span></span>

1. <span data-ttu-id="269a7-192">Wählen Sie das entsprechende Team aus, und wählen Sie im Dropdownmenü (&#8226;&#8226;&#8226;) die Option **"Team verwalten"** aus.</span><span class="sxs-lookup"><span data-stu-id="269a7-192">Select the appropriate team and choose **Manage team** from the (&#8226;&#8226;&#8226;) drop-down menu.</span></span>
1. <span data-ttu-id="269a7-193">Wählen Sie die Registerkarte **"Apps"** in der Navigationsleiste aus.</span><span class="sxs-lookup"><span data-stu-id="269a7-193">Choose the **Apps** tab from the navigation bar.</span></span>
1. <span data-ttu-id="269a7-194">Wählen Sie in der unteren rechten Ecke des Fensters **einen ausgehenden Webhook erstellen** aus.</span><span class="sxs-lookup"><span data-stu-id="269a7-194">From the window's lower right corner select **Create an outgoing webhook**.</span></span>
1. <span data-ttu-id="269a7-195">Füllen Sie im resultierenden Popupfenster die erforderlichen Felder aus:</span><span class="sxs-lookup"><span data-stu-id="269a7-195">In the resulting popup window complete the required fields:</span></span>

>* <span data-ttu-id="269a7-196">**Name:** Der Webhook-Titel und @mention tippen</span><span class="sxs-lookup"><span data-stu-id="269a7-196">**Name**: The webhook title and @mention tap</span></span>
>* <span data-ttu-id="269a7-197">**Rückruf-URL:** Der HTTPS-Endpunkt, der JSON-Nutzlasten akzeptiert und POST-Anforderungen von Teams</span><span class="sxs-lookup"><span data-stu-id="269a7-197">**Callback URL**: The HTTPS endpoint that accepts JSON payloads and receives POST requests from Teams</span></span>
>* <span data-ttu-id="269a7-198">**Beschreibung:** Eine detaillierte Zeichenfolge, die auf der Profilkarte und im App-Dashboard auf Teamebene angezeigt wird</span><span class="sxs-lookup"><span data-stu-id="269a7-198">**Description**: A detailed string that appear in the profile card and the team-level App dashboard</span></span>
>* <span data-ttu-id="269a7-199">**Profilbild:** Ein optionales App-Symbol für Ihren Webhook</span><span class="sxs-lookup"><span data-stu-id="269a7-199">**Profile Picture**: An optional app icon for your webhook</span></span>
>* <span data-ttu-id="269a7-200">Wählen Sie die Schaltfläche **"Erstellen"** in der unteren rechten Ecke des Popupfensters aus, und der ausgehende Webhook wird den Kanälen des aktuellen Teams hinzugefügt.</span><span class="sxs-lookup"><span data-stu-id="269a7-200">Select the **Create** button from the lower right corner of the pop-up window and the outgoing webhook are added to the current team's channels.</span></span>
>* <span data-ttu-id="269a7-201">Im nächsten Dialogfeld wird ein [HMAC-Sicherheitstoken (Hash-based Message Authentication Code)](https://security.stackexchange.com/questions/20129/how-and-when-do-i-use-hmac/20301) angezeigt, das zum Authentifizieren von Aufrufen zwischen Teams und dem angegebenen externen Dienst verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="269a7-201">The next dialog window displays an [Hash-based Message Authentication Code (HMAC)](https://security.stackexchange.com/questions/20129/how-and-when-do-i-use-hmac/20301) security token that is used to authenticate calls between Teams and the designated outside service.</span></span>
>* <span data-ttu-id="269a7-202">Der ausgehende Webhook steht den Benutzern des Teams nur zur Verfügung, wenn die URL gültig ist und die Server- und Clientauthentifizierungstoken gleich sind, z. B. ein HMAC-Handshake.</span><span class="sxs-lookup"><span data-stu-id="269a7-202">The outgoing webhook is available to the team's users, only if the URL is valid and the server and client authentication tokens are equal for example, an HMAC handshake.</span></span>

## <a name="code-sample"></a><span data-ttu-id="269a7-203">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="269a7-203">Code sample</span></span>
|<span data-ttu-id="269a7-204">**Beispielname**</span><span class="sxs-lookup"><span data-stu-id="269a7-204">**Sample name**</span></span> | <span data-ttu-id="269a7-205">**Beschreibung**</span><span class="sxs-lookup"><span data-stu-id="269a7-205">**Description**</span></span> | <span data-ttu-id="269a7-206">**.NET**</span><span class="sxs-lookup"><span data-stu-id="269a7-206">**.NET**</span></span> | <span data-ttu-id="269a7-207">**Node.js**</span><span class="sxs-lookup"><span data-stu-id="269a7-207">**Node.js**</span></span> |
|----------------|------------------|--------|----------------|
| <span data-ttu-id="269a7-208">Ausgehende Webhooks</span><span class="sxs-lookup"><span data-stu-id="269a7-208">Outgoing webhooks</span></span> | <span data-ttu-id="269a7-209">Beispiele zum Erstellen **von benutzerdefinierten Bots** für die Verwendung in Microsoft Teams.</span><span class="sxs-lookup"><span data-stu-id="269a7-209">Samples to create **Custom Bots** to be used in Microsoft Teams.</span></span>| [<span data-ttu-id="269a7-210">View</span><span class="sxs-lookup"><span data-stu-id="269a7-210">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/outgoing-webhook/csharp) | [<span data-ttu-id="269a7-211">View</span><span class="sxs-lookup"><span data-stu-id="269a7-211">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/outgoing-webhook/nodejs)|

