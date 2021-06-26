---
title: Erstellen eines ausgehenden Webhooks
author: laujan
description: beschreibt, wie ein ausgehender Webhook erstellt wird
ms.topic: conceptual
localization_priority: Normal
ms.author: lajanuar
keywords: Teams-Registerkarten ausgehende Webhook-Nachricht mit Aktionen überprüfen Webhook
ms.openlocfilehash: c02ff5388e47ba40056afcc1fcf5e8d7ad4437e8
ms.sourcegitcommit: 4d9d1542e04abacfb252511c665a7229d8bb7162
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/25/2021
ms.locfileid: "53140327"
---
# <a name="create-outgoing-webhook"></a><span data-ttu-id="a6edf-104">Erstellen eines ausgehenden Webhooks</span><span class="sxs-lookup"><span data-stu-id="a6edf-104">Create Outgoing Webhook</span></span>

<span data-ttu-id="a6edf-105">Der ausgehende Webhook fungiert als Bot und sucht **mithilfe von @mention** nach Nachrichten in Kanälen.</span><span class="sxs-lookup"><span data-stu-id="a6edf-105">The Outgoing Webhook acts as a bot and search for messages in channels using **@mention**.</span></span> <span data-ttu-id="a6edf-106">Es sendet Benachrichtigungen an externe Webdienste und antwortet mit umfangreichen Nachrichten, die Karten und Bilder enthalten.</span><span class="sxs-lookup"><span data-stu-id="a6edf-106">It sends notifications to external web services and responds with rich messages, which include cards and images.</span></span> <span data-ttu-id="a6edf-107">Es hilft, den Prozess der Erstellung von Bots über die [Microsoft Bot Framework](https://dev.botframework.com/)zu überspringen.</span><span class="sxs-lookup"><span data-stu-id="a6edf-107">It helps to skip the process of creating bots through the [Microsoft Bot Framework](https://dev.botframework.com/).</span></span>

## <a name="key-features-of-outgoing-webhook"></a><span data-ttu-id="a6edf-108">Wichtige Features des ausgehenden Webhooks</span><span class="sxs-lookup"><span data-stu-id="a6edf-108">Key features of Outgoing Webhook</span></span>

<span data-ttu-id="a6edf-109">Die folgende Tabelle enthält die Features und die Beschreibung ausgehender Webhooks:</span><span class="sxs-lookup"><span data-stu-id="a6edf-109">The following table provides the features and description of Outgoing Webhooks:</span></span>

| <span data-ttu-id="a6edf-110">Features</span><span class="sxs-lookup"><span data-stu-id="a6edf-110">Features</span></span> | <span data-ttu-id="a6edf-111">Beschreibung</span><span class="sxs-lookup"><span data-stu-id="a6edf-111">Description</span></span> |
| ------- | ----------- |
| <span data-ttu-id="a6edf-112">Bereichskonfiguration</span><span class="sxs-lookup"><span data-stu-id="a6edf-112">Scoped configuration</span></span>| <span data-ttu-id="a6edf-113">Webhooks sind auf Teamebene beschränkt.</span><span class="sxs-lookup"><span data-stu-id="a6edf-113">Webhooks are scoped at the team level.</span></span> <span data-ttu-id="a6edf-114">Der obligatorische Einrichtungsprozess für jedes Add-In fügt einen ausgehenden Webhook hinzu.</span><span class="sxs-lookup"><span data-stu-id="a6edf-114">Mandatory set up process for each adds an Outgoing Webhook.</span></span> |
| <span data-ttu-id="a6edf-115">Reaktives Messaging</span><span class="sxs-lookup"><span data-stu-id="a6edf-115">Reactive messaging</span></span>| <span data-ttu-id="a6edf-116">Benutzer müssen @mention verwenden, damit der Webhook Nachrichten empfängt.</span><span class="sxs-lookup"><span data-stu-id="a6edf-116">Users must use @mention for the webhook to receive messages.</span></span> <span data-ttu-id="a6edf-117">Derzeit können Benutzer nur einen ausgehenden Webhook in öffentlichen Kanälen und nicht innerhalb des persönlichen oder privaten Bereichs senden.</span><span class="sxs-lookup"><span data-stu-id="a6edf-117">Currently, users can only message an Outgoing Webhook in public channels and not within the personal or private scope.</span></span> |
|<span data-ttu-id="a6edf-118">Standardmäßiger HTTP-Nachrichtenaustausch</span><span class="sxs-lookup"><span data-stu-id="a6edf-118">Standard HTTP message exchange</span></span>|<span data-ttu-id="a6edf-119">Antworten werden in derselben Kette wie die ursprüngliche Anforderungsnachricht angezeigt und können beliebige Bot Framework-Nachrichteninhalte enthalten, z. B. Rich-Text, Bilder, Karten und Emojis.</span><span class="sxs-lookup"><span data-stu-id="a6edf-119">Responses appear in the same chain as the original request message and can include any Bot Framework message content, for example, rich text, images, cards, and emojis.</span></span> <span data-ttu-id="a6edf-120">Ausgehende Webhooks können zwar Karten verwenden, jedoch keine Kartenaktionen außer `openURL` .</span><span class="sxs-lookup"><span data-stu-id="a6edf-120">Although Outgoing Webhooks can use cards, they cannot use any card actions except for `openURL`.</span></span>|
| <span data-ttu-id="a6edf-121">Teams API-Methodenunterstützung</span><span class="sxs-lookup"><span data-stu-id="a6edf-121">Teams API method support</span></span>|<span data-ttu-id="a6edf-122">Ausgehende Webhooks senden einen HTTP POST an einen Webdienst und erhalten eine Antwort.</span><span class="sxs-lookup"><span data-stu-id="a6edf-122">Outgoing Webhooks sends an HTTP POST to a web service and gets a response.</span></span> <span data-ttu-id="a6edf-123">Sie können nicht auf andere APIs zugreifen, z. B. auf die Liste oder die Liste der Kanäle in einem Team.</span><span class="sxs-lookup"><span data-stu-id="a6edf-123">They cannot access any other APIs, such as retrieve the roster or list of channels in a team.</span></span>|

## <a name="create-outgoing-webhooks"></a><span data-ttu-id="a6edf-124">Erstellen ausgehender Webhooks</span><span class="sxs-lookup"><span data-stu-id="a6edf-124">Create Outgoing Webhooks</span></span>

<span data-ttu-id="a6edf-125">Erstellen Sie ausgehende Webhooks, und fügen Sie Teams benutzerdefinierte Bots hinzu.</span><span class="sxs-lookup"><span data-stu-id="a6edf-125">Create Outgoing Webhooks and add custom bots to Teams.</span></span>

<span data-ttu-id="a6edf-126">**So erstellen Sie einen ausgehenden Webhook**</span><span class="sxs-lookup"><span data-stu-id="a6edf-126">**To create an Outgoing Webhook**</span></span>

1. <span data-ttu-id="a6edf-127">Wählen Sie im linken Bereich **Teams** aus.</span><span class="sxs-lookup"><span data-stu-id="a6edf-127">Select **Teams** from the left pane.</span></span> <span data-ttu-id="a6edf-128">Die **Teams** Seite wird angezeigt:</span><span class="sxs-lookup"><span data-stu-id="a6edf-128">The **Teams** page appears:</span></span>

    ![Teams channel](~/assets/images/teamschannel.png)

1. <span data-ttu-id="a6edf-130">Wählen Sie auf der **Seite Teams** das erforderliche Team aus, um einen ausgehenden Webhook zu erstellen, und wählen Sie die &#8226;&#8226;&#8226; aus.</span><span class="sxs-lookup"><span data-stu-id="a6edf-130">In the **Teams** page, select the required team to create an Outgoing Webhook and select the &#8226;&#8226;&#8226;.</span></span> <span data-ttu-id="a6edf-131">Wählen Sie im Dropdownmenü **"Team verwalten"** aus:</span><span class="sxs-lookup"><span data-stu-id="a6edf-131">In the dropdown menu, select **Manage team**:</span></span>

    ![Erstellen eines ausgehenden Webhooks](~/assets/images/outgoingwebhook1.png)

1. <span data-ttu-id="a6edf-133">Wählen Sie die Registerkarte **"Apps"** auf der Kanalseite aus:</span><span class="sxs-lookup"><span data-stu-id="a6edf-133">Select the **Apps** tab on the channel page:</span></span>

    ![Erstellen eines ausgehenden Webhooks](~/assets/images/outgoingwebhook2.png)

1. <span data-ttu-id="a6edf-135">Wählen Sie **"Ausgehenden Webhook erstellen" aus:**</span><span class="sxs-lookup"><span data-stu-id="a6edf-135">Select **Create an Outgoing Webhook**:</span></span>

    ![Erstellen ausgehender Webhooks](~/assets/images/outgoingwebhook3.png)

1. <span data-ttu-id="a6edf-137">Geben Sie die folgenden Details auf der Seite **"Erstellen eines ausgehenden Webhooks" ein:**</span><span class="sxs-lookup"><span data-stu-id="a6edf-137">Type the following details in the **Create an Outgoing Webhook** page:</span></span>

    * <span data-ttu-id="a6edf-138">**Name:** Der Webhook-Titel und @mention Registerkarte.</span><span class="sxs-lookup"><span data-stu-id="a6edf-138">**Name**: The webhook title and @mention tab.</span></span>
    * <span data-ttu-id="a6edf-139">**Rückruf-URL:** Der HTTPS-Endpunkt, der JSON-Nutzlasten akzeptiert und POST-Anforderungen von Teams empfängt.</span><span class="sxs-lookup"><span data-stu-id="a6edf-139">**Callback URL**: The HTTPS endpoint that accepts JSON payloads and receives POST requests from Teams.</span></span>
    * <span data-ttu-id="a6edf-140">**Beschreibung:** Eine detaillierte Zeichenfolge, die auf der Profilkarte und im App-Dashboard auf Teamebene angezeigt wird.</span><span class="sxs-lookup"><span data-stu-id="a6edf-140">**Description**: A detailed string that appears in the profile card and the team-level App dashboard.</span></span>
    * <span data-ttu-id="a6edf-141">**Profilbild:** Ein App-Symbol für Ihren Webhook, das optional ist.</span><span class="sxs-lookup"><span data-stu-id="a6edf-141">**Profile Picture**: An app icon for your webhook, which is optional.</span></span>

1. <span data-ttu-id="a6edf-142">Wählen Sie **Erstellen** aus.</span><span class="sxs-lookup"><span data-stu-id="a6edf-142">Select **Create**.</span></span> <span data-ttu-id="a6edf-143">Der ausgehende Webhook wird dem Kanal des aktuellen Teams hinzugefügt:</span><span class="sxs-lookup"><span data-stu-id="a6edf-143">The Outgoing Webhook is added to the current team's channel:</span></span>

    ![Erstellen von ausgehenden Webhooks](~/assets/images/outgoingwebhook.png)

<span data-ttu-id="a6edf-145">Ein [Hashbasiertes Dialogfeld mit dem Nachrichtenauthentifizierungscode (Message Authentication Code, HMAC)](https://security.stackexchange.com/questions/20129/how-and-when-do-i-use-hmac/20301) wird angezeigt.</span><span class="sxs-lookup"><span data-stu-id="a6edf-145">A [Hash-based Message Authentication Code (HMAC)](https://security.stackexchange.com/questions/20129/how-and-when-do-i-use-hmac/20301) dialogue box appears.</span></span> <span data-ttu-id="a6edf-146">Es handelt sich um ein Sicherheitstoken, das zum Authentifizieren von Aufrufen zwischen Teams und dem angegebenen externen Dienst verwendet wird.</span><span class="sxs-lookup"><span data-stu-id="a6edf-146">It is a security token used to authenticate calls between Teams and the designated outside service.</span></span>

>[!NOTE]
> <span data-ttu-id="a6edf-147">Der ausgehende Webhook ist für die Benutzer des Teams nur verfügbar, wenn die URL gültig ist und die Server- und Clientauthentifizierungstoken gleich sind.</span><span class="sxs-lookup"><span data-stu-id="a6edf-147">The Outgoing Webhook is available to the team's users, only if the URL is valid and the server and client authentication tokens are equal.</span></span> <span data-ttu-id="a6edf-148">Beispielsweise ein HMAC-Handshake.</span><span class="sxs-lookup"><span data-stu-id="a6edf-148">For example, an HMAC handshake.</span></span>

<span data-ttu-id="a6edf-149">Das folgende Szenario enthält die Details zum Hinzufügen eines ausgehenden Webhooks:</span><span class="sxs-lookup"><span data-stu-id="a6edf-149">The following scenario provides the details to add an Outgoing Webhook:</span></span>

* <span data-ttu-id="a6edf-150">Szenario: Pushänderungsstatusbenachrichtigungen auf einem Teams Kanaldatenbankserver an Ihre App.</span><span class="sxs-lookup"><span data-stu-id="a6edf-150">Scenario: Push change status notifications on a Teams channel database server to your app.</span></span>
* <span data-ttu-id="a6edf-151">Beispiel: Sie verfügen über eine Branchen-App, die alle CRUD-Vorgänge verfolgt, z. B. erstellen, lesen, aktualisieren und löschen.</span><span class="sxs-lookup"><span data-stu-id="a6edf-151">Example: You have a line of business app that tracks all CRUD operations, such as create, read, update, and delete.</span></span> <span data-ttu-id="a6edf-152">Diese Vorgänge werden den Mitarbeiterdatensätzen von Teams Kanal-HR-Benutzern über einen Office 365 Mandanten vorgenommen.</span><span class="sxs-lookup"><span data-stu-id="a6edf-152">These operations are made to the employee records by Teams channel HR users across an Office 365 tenancy.</span></span>

# <a name="url-json-payload"></a>[<span data-ttu-id="a6edf-153">JSON-URL-Nutzlast</span><span class="sxs-lookup"><span data-stu-id="a6edf-153">URL JSON payload</span></span>](#tab/urljsonpayload)
<span data-ttu-id="a6edf-154">**Erstellen Sie eine URL auf dem Server Ihrer App, um eine POST-Anforderung mit einer JSON-Nutzlast zu akzeptieren und zu verarbeiten.**</span><span class="sxs-lookup"><span data-stu-id="a6edf-154">**Create a URL on your app's server to accept and process a POST request with a JSON payload**</span></span>

<span data-ttu-id="a6edf-155">Ihr Dienst empfängt Nachrichten in einem standardmäßigen Nachrichtenschema des Azure-Botdiensts.</span><span class="sxs-lookup"><span data-stu-id="a6edf-155">Your service receives messages in a standard Azure bot service messaging schema.</span></span> <span data-ttu-id="a6edf-156">Der Bot Framework-Connector ist ein REST-Dienst, der den Austausch von JSON-formatierten Nachrichten über HTTPS-Protokolle verarbeiten kann, wie in der [Azure Bot Service-API](/bot-framework/rest-api/bot-framework-rest-connector-api-reference)dokumentiert.</span><span class="sxs-lookup"><span data-stu-id="a6edf-156">The Bot Framework connector is a RESTful service that empowers to process the interchange of JSON formatted messages through HTTPS protocols as documented in the [Azure Bot Service API](/bot-framework/rest-api/bot-framework-rest-connector-api-reference).</span></span> <span data-ttu-id="a6edf-157">Alternativ können Sie dem Microsoft Bot Framework SDK folgen, um Nachrichten zu verarbeiten und zu analysieren.</span><span class="sxs-lookup"><span data-stu-id="a6edf-157">Alternatively, you can follow the Microsoft Bot Framework SDK to process and parse messages.</span></span> <span data-ttu-id="a6edf-158">Weitere Informationen finden Sie in [der Übersicht über Azure Bot Service.](/azure/bot-service/bot-service-overview-introduction)</span><span class="sxs-lookup"><span data-stu-id="a6edf-158">For more information, see [overview of Azure Bot Service](/azure/bot-service/bot-service-overview-introduction).</span></span>

<span data-ttu-id="a6edf-159">Ausgehende Webhooks sind auf die Ebene beschränkt `team` und für alle Teammitglieder sichtbar.</span><span class="sxs-lookup"><span data-stu-id="a6edf-159">Outgoing Webhooks are scoped to the `team` level and are visible to all the team members.</span></span> <span data-ttu-id="a6edf-160">Benutzer müssen den Namen des ausgehenden Webhooks **\@ erwähnen,** um ihn im Kanal aufzurufen.</span><span class="sxs-lookup"><span data-stu-id="a6edf-160">Users need to **\@mention** the name of the Outgoing Webhook to invoke it in the channel.</span></span>

# <a name="verify-hmac-token"></a>[<span data-ttu-id="a6edf-161">Überprüfen des HMAC-Tokens</span><span class="sxs-lookup"><span data-stu-id="a6edf-161">Verify HMAC token</span></span>](#tab/verifyhmactoken)
<span data-ttu-id="a6edf-162">**Erstellen einer Methode zum Überprüfen des HMAC-Tokens für ausgehenden Webhook**</span><span class="sxs-lookup"><span data-stu-id="a6edf-162">**Create a method to verify the Outgoing Webhook HMAC token**</span></span>

<span data-ttu-id="a6edf-163">Using example of inbound message and ID: "contoso" of SigningKeyDictionary of {"contoso", "vqF0En+Z0ucuRTM/01o2GuhMH3hKKk/N2bOmlM31zaA=" }.</span><span class="sxs-lookup"><span data-stu-id="a6edf-163">Using example of inbound message and ID: "contoso" of SigningKeyDictionary of {"contoso", "vqF0En+Z0ucuRTM/01o2GuhMH3hKKk/N2bOmlM31zaA=" }.</span></span>

<span data-ttu-id="a6edf-164">Verwenden Sie den Wert "HMAC 03TCao0i55H1eVKUusZOTZRjtvYTs+mO41mPL+R1e1U=" in der Autorisierung des Anforderungsheaders.</span><span class="sxs-lookup"><span data-stu-id="a6edf-164">Use the value "HMAC 03TCao0i55H1eVKUusZOTZRjtvYTs+mO41mPL+R1e1U=" in the authorization of request header.</span></span>

<span data-ttu-id="a6edf-165">Um sicherzustellen, dass Ihr Dienst nur Aufrufe von tatsächlichen Teams Clients empfängt, stellt Teams einen HMAC-Code im `hmac` HTTP-Autorisierungsheader bereit.</span><span class="sxs-lookup"><span data-stu-id="a6edf-165">To ensure that your service is receiving calls only from actual Teams clients, Teams provides an HMAC code in the HTTP `hmac` authorization header.</span></span> <span data-ttu-id="a6edf-166">Fügen Sie immer den Code in Ihr Authentifizierungsprotokoll ein.</span><span class="sxs-lookup"><span data-stu-id="a6edf-166">Always include the code in your authentication protocol.</span></span>

<span data-ttu-id="a6edf-167">Ihr Code muss die in der Anforderung enthaltene HMAC-Signatur immer wie folgt überprüfen:</span><span class="sxs-lookup"><span data-stu-id="a6edf-167">Your code must always validate the HMAC signature included in the request as follows:</span></span>

* <span data-ttu-id="a6edf-168">Generieren Sie das HMAC-Token aus dem Anforderungstext der Nachricht.</span><span class="sxs-lookup"><span data-stu-id="a6edf-168">Generate the HMAC token from the request body of the message.</span></span> <span data-ttu-id="a6edf-169">Es gibt Standardbibliotheken, um dies auf den meisten Plattformen zu tun, z. [B. Crypto](https://nodejs.org/api/crypto.html#crypto_crypto) für Node.js und [Teams Webhook-Beispiel](https://github.com/OfficeDev/microsoft-teams-sample-outgoing-webhook/blob/23eb61da5a18634d51c5247944843da9abed01b6/WebhookSampleBot/Models/AuthProvider.cs) für C \# ).</span><span class="sxs-lookup"><span data-stu-id="a6edf-169">There are standard libraries to do this on most platform, such as [Crypto](https://nodejs.org/api/crypto.html#crypto_crypto) for Node.js and [Teams webhook sample](https://github.com/OfficeDev/microsoft-teams-sample-outgoing-webhook/blob/23eb61da5a18634d51c5247944843da9abed01b6/WebhookSampleBot/Models/AuthProvider.cs) for C\#).</span></span> <span data-ttu-id="a6edf-170">Microsoft Teams verwendet standard SHA256 HMAC-Kryptografie.</span><span class="sxs-lookup"><span data-stu-id="a6edf-170">Microsoft Teams uses standard SHA256 HMAC cryptography.</span></span> <span data-ttu-id="a6edf-171">Sie müssen den Textkörper in UTF8 in ein Bytearray konvertieren.</span><span class="sxs-lookup"><span data-stu-id="a6edf-171">You must convert the body to a byte array in UTF8.</span></span>
* <span data-ttu-id="a6edf-172">Berechnen Sie den Hash aus dem Bytearray des Sicherheitstokens, das von Teams bereitgestellt wird, wenn Sie den ausgehenden Webhook im Teams-Client registriert haben.</span><span class="sxs-lookup"><span data-stu-id="a6edf-172">Compute the hash from the byte array of the security token provided by Teams when you registered the Outgoing Webhook in the Teams client.</span></span> <span data-ttu-id="a6edf-173">Siehe [Erstellen eines ausgehenden Webhooks.](#create-outgoing-webhook)</span><span class="sxs-lookup"><span data-stu-id="a6edf-173">See [create an Outgoing Webhook](#create-outgoing-webhook).</span></span>
* <span data-ttu-id="a6edf-174">Konvertieren Sie den Hash in eine Zeichenfolge mithilfe der UTF-8-Codierung.</span><span class="sxs-lookup"><span data-stu-id="a6edf-174">Convert the hash to a string using UTF-8 encoding.</span></span>
* <span data-ttu-id="a6edf-175">Vergleichen Sie den Zeichenfolgenwert des generierten Hash mit dem in der HTTP-Anforderung angegebenen Wert.</span><span class="sxs-lookup"><span data-stu-id="a6edf-175">Compare the string value of the generated hash with the value provided in the HTTP request.</span></span>

# <a name="method-to-respond"></a>[<span data-ttu-id="a6edf-176">Zu reagierende Methode</span><span class="sxs-lookup"><span data-stu-id="a6edf-176">Method to respond</span></span>](#tab/methodtorespond)
<span data-ttu-id="a6edf-177">**Erstellen einer Methode zum Senden einer Erfolgs- oder Fehlerantwort**</span><span class="sxs-lookup"><span data-stu-id="a6edf-177">**Create a method to send a success or failure response**</span></span>

<span data-ttu-id="a6edf-178">Antworten von ausgehenden Webhooks werden in der gleichen Antwortkette wie die ursprüngliche Nachricht angezeigt.</span><span class="sxs-lookup"><span data-stu-id="a6edf-178">Responses from your Outgoing Webhooks appear in the same reply chain as the original message.</span></span> <span data-ttu-id="a6edf-179">Wenn der Benutzer eine Abfrage ausführt, gibt Microsoft Teams eine synchrone HTTP-Anforderung an Ihren Dienst aus, und Ihr Code erhält fünf Sekunden, um auf die Nachricht zu antworten, bevor die Verbindung ein Zeitüberschreitung auftritt und beendet wird.</span><span class="sxs-lookup"><span data-stu-id="a6edf-179">When the user performs a query, Microsoft Teams issues a synchronous HTTP request to your service and your code gets five seconds to respond to the message before the connection times out and terminates.</span></span>

### <a name="example-response"></a><span data-ttu-id="a6edf-180">Beispielantwort</span><span class="sxs-lookup"><span data-stu-id="a6edf-180">Example response</span></span>

```json
{
    "type": "message",
    "text": "This is a reply!"
}
```
---

> [!NOTE]
> * <span data-ttu-id="a6edf-181">Sie können adaptive Karte, Hero-Karte und Textnachrichten als Anlage mit ausgehenden Webhook senden.</span><span class="sxs-lookup"><span data-stu-id="a6edf-181">You can send Adaptive Card, Hero card, and text messages as attachment with Outgoing Webhook.</span></span>
> * <span data-ttu-id="a6edf-182">Karten unterstützen die Formatierung.</span><span class="sxs-lookup"><span data-stu-id="a6edf-182">Cards support formatting.</span></span> <span data-ttu-id="a6edf-183">Weitere Informationen finden Sie unter [Formatieren von Karten mit Markdown.](~/task-modules-and-cards/cards/cards-format.md?tabs=adaptive-md%2Cconnector-html#format-cards-with-markdown)</span><span class="sxs-lookup"><span data-stu-id="a6edf-183">For more information, see [format cards with markdown](~/task-modules-and-cards/cards/cards-format.md?tabs=adaptive-md%2Cconnector-html#format-cards-with-markdown).</span></span>

<span data-ttu-id="a6edf-184">Die folgenden Codes sind Beispiele für eine Adaptive Kartenantwort:</span><span class="sxs-lookup"><span data-stu-id="a6edf-184">Following codes are examples of an Adaptive Card response:</span></span>

# <a name="cnet"></a>[<span data-ttu-id="a6edf-185">C#/.NET</span><span class="sxs-lookup"><span data-stu-id="a6edf-185">C#/.NET</span></span>](#tab/dotnet)

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

# <a name="javascriptnodejs"></a>[<span data-ttu-id="a6edf-186">JavaScript/Node.js</span><span class="sxs-lookup"><span data-stu-id="a6edf-186">JavaScript/Node.js</span></span>](#tab/javascript)

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

# <a name="json"></a>[<span data-ttu-id="a6edf-187">Json</span><span class="sxs-lookup"><span data-stu-id="a6edf-187">JSON</span></span>](#tab/json)

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

## <a name="code-sample"></a><span data-ttu-id="a6edf-188">Codebeispiel</span><span class="sxs-lookup"><span data-stu-id="a6edf-188">Code sample</span></span>

|<span data-ttu-id="a6edf-189">**Beispielname**</span><span class="sxs-lookup"><span data-stu-id="a6edf-189">**Sample name**</span></span> | <span data-ttu-id="a6edf-190">**Beschreibung**</span><span class="sxs-lookup"><span data-stu-id="a6edf-190">**Description**</span></span> | <span data-ttu-id="a6edf-191">**.NET**</span><span class="sxs-lookup"><span data-stu-id="a6edf-191">**.NET**</span></span> | <span data-ttu-id="a6edf-192">**Node.js**</span><span class="sxs-lookup"><span data-stu-id="a6edf-192">**Node.js**</span></span> |
|----------------|------------------|--------|----------------|
| <span data-ttu-id="a6edf-193">Ausgehende Webhooks</span><span class="sxs-lookup"><span data-stu-id="a6edf-193">Outgoing Webhooks</span></span> | <span data-ttu-id="a6edf-194">Beispiele zum Erstellen von benutzerdefinierten Bots, die in Microsoft Teams verwendet werden.</span><span class="sxs-lookup"><span data-stu-id="a6edf-194">Samples to create custom bots to be used in Microsoft Teams.</span></span>| [<span data-ttu-id="a6edf-195">View</span><span class="sxs-lookup"><span data-stu-id="a6edf-195">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/outgoing-webhook/csharp) | [<span data-ttu-id="a6edf-196">View</span><span class="sxs-lookup"><span data-stu-id="a6edf-196">View</span></span>](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/outgoing-webhook/nodejs)|

## <a name="see-also"></a><span data-ttu-id="a6edf-197">Siehe auch</span><span class="sxs-lookup"><span data-stu-id="a6edf-197">See also</span></span>
* [<span data-ttu-id="a6edf-198">Erstellen eines eingehenden Webhooks</span><span class="sxs-lookup"><span data-stu-id="a6edf-198">Create an Incoming Webhook</span></span>](~/webhooks-and-connectors/how-to/add-incoming-webhook.md)
* [<span data-ttu-id="a6edf-199">Erstellen eines Office 365-Connectors</span><span class="sxs-lookup"><span data-stu-id="a6edf-199">Create an Office 365 Connector</span></span>](~/webhooks-and-connectors/how-to/connectors-creating.md)
* [<span data-ttu-id="a6edf-200">Erstellen und Senden von Nachrichten</span><span class="sxs-lookup"><span data-stu-id="a6edf-200">Create and send messages</span></span>](~/webhooks-and-connectors/how-to/connectors-using.md)
