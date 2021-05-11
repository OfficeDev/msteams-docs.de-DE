---
title: Optimieren eines Bots mit Ratenbegrenzung in Teams
description: Geschwindigkeitsbegrenzung und bewährte Methoden in Microsoft Teams
ms.topic: conceptual
localization_priority: Normal
keywords: Beschränkung der Rate von Teams-Bots
ms.openlocfilehash: 3b8f80efa50d2fbf44162aec13994b747b9bd7ac
ms.sourcegitcommit: 60561c7cd189c9d6fa5e09e0f2b6c24476f2dff5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/06/2021
ms.locfileid: "52230960"
---
# <a name="optimize-your-bot-with-rate-limiting-in-teams"></a><span data-ttu-id="7abf1-104">Optimieren eines Bots mit Ratenbegrenzung in Teams</span><span class="sxs-lookup"><span data-stu-id="7abf1-104">Optimize your bot with rate limiting in Teams</span></span>

<span data-ttu-id="7abf1-105">Die Geschwindigkeitsbegrenzung ist eine Methode, um Nachrichten auf eine bestimmte maximale Häufigkeit zu beschränken.</span><span class="sxs-lookup"><span data-stu-id="7abf1-105">Rate limiting is a method to limit messages to a certain maximum frequency.</span></span> <span data-ttu-id="7abf1-106">Als allgemeines Prinzip muss Ihre Anwendung die Anzahl der Von ihr gesendeten Nachrichten auf eine einzelne Chat- oder Kanal unterhaltung beschränken.</span><span class="sxs-lookup"><span data-stu-id="7abf1-106">As a general principle, your application must limit the number of messages it posts to an individual chat or channel conversation.</span></span> <span data-ttu-id="7abf1-107">Dadurch wird eine optimale Benutzererfahrung sichergestellt, und Nachrichten werden ihren Benutzern nicht als Spam angezeigt.</span><span class="sxs-lookup"><span data-stu-id="7abf1-107">This ensures an optimal experience and messages do not appear as spam to your users.</span></span>

<span data-ttu-id="7abf1-108">Zum Schutz Microsoft Teams und seiner Benutzer bieten die Bot-APIs eine Geschwindigkeitsbegrenzung für eingehende Anforderungen.</span><span class="sxs-lookup"><span data-stu-id="7abf1-108">To protect Microsoft Teams and its users, the bot APIs provide a rate limit for incoming requests.</span></span> <span data-ttu-id="7abf1-109">Apps, die diesen Grenzwert überschreiten, erhalten einen `HTTP 429 Too Many Requests` Fehlerstatus.</span><span class="sxs-lookup"><span data-stu-id="7abf1-109">Apps that go over this limit receive an `HTTP 429 Too Many Requests` error status.</span></span> <span data-ttu-id="7abf1-110">Alle Anforderungen unterliegen der gleichen Richtlinie zur Begrenzung der Rate, einschließlich des Sendens von Nachrichten, Kanalaufzählungen und Abrufen von Dienstplans.</span><span class="sxs-lookup"><span data-stu-id="7abf1-110">All requests are subject to the same rate limiting policy, including sending messages, channel enumerations, and roster fetches.</span></span>

<span data-ttu-id="7abf1-111">Da sich die genauen Werte der Zinsgrenzen ändern können, muss Ihre Anwendung das entsprechende Backoff-Verhalten implementieren, wenn die API `HTTP 429 Too Many Requests` zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="7abf1-111">As the exact values of rate limits are subject to change, your application must implement the appropriate backoff behavior when the API returns `HTTP 429 Too Many Requests`.</span></span>

## <a name="handle-rate-limits"></a><span data-ttu-id="7abf1-112">Behandeln von Satzbegrenzungen</span><span class="sxs-lookup"><span data-stu-id="7abf1-112">Handle rate limits</span></span>

<span data-ttu-id="7abf1-113">Beim Ausstellen eines Bot Builder-SDK-Vorgangs können Sie den Statuscode `Microsoft.Rest.HttpOperationException` behandeln und überprüfen.</span><span class="sxs-lookup"><span data-stu-id="7abf1-113">When issuing a Bot Builder SDK operation, you can handle `Microsoft.Rest.HttpOperationException` and check for the status code.</span></span>

<span data-ttu-id="7abf1-114">Der folgende Code zeigt ein Beispiel für die Behandlung von Geschwindigkeitsbeschränkungen:</span><span class="sxs-lookup"><span data-stu-id="7abf1-114">The following code shows an example of handling rate limits:</span></span>

```csharp
try
{
    // Perform Bot Framework operation
    // for example, await connector.Conversations.UpdateActivityAsync(reply);
}
catch (HttpOperationException ex)
{
    if (ex.Response != null && (uint)ex.Response.StatusCode ==  429)
    {
        //Perform retry of the above operation/Action method
    }
}
```

<span data-ttu-id="7abf1-115">Nachdem Sie die Geschwindigkeitsbeschränkungen für Bots umgangen haben, können Sie Antworten mithilfe eines `HTTP 429` exponentiellen Backoffs behandeln.</span><span class="sxs-lookup"><span data-stu-id="7abf1-115">After you handle rate limits for bots, you can handle `HTTP 429` responses using an exponential backoff.</span></span>

## <a name="handle-http-429-responses"></a><span data-ttu-id="7abf1-116">Behandeln von `HTTP 429` Antworten</span><span class="sxs-lookup"><span data-stu-id="7abf1-116">Handle `HTTP 429` responses</span></span>

<span data-ttu-id="7abf1-117">Im Allgemeinen müssen Sie einfache Vorsichtsmaßnahmen ergreifen, um den Empfang von Antworten `HTTP 429` zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="7abf1-117">In general, you must take simple precautions to avoid receiving `HTTP 429` responses.</span></span> <span data-ttu-id="7abf1-118">Vermeiden Sie beispielsweise, mehrere Anforderungen an dieselbe persönliche Unterhaltung oder eine Kanal unterhaltung ausstellen.</span><span class="sxs-lookup"><span data-stu-id="7abf1-118">For example, avoid issuing multiple requests to the same personal or channel conversation.</span></span> <span data-ttu-id="7abf1-119">Erstellen Sie stattdessen einen Batch der API-Anforderungen.</span><span class="sxs-lookup"><span data-stu-id="7abf1-119">Instead, create a batch of the API requests.</span></span>

<span data-ttu-id="7abf1-120">Die Verwendung eines exponentiellen Backoffs mit einem zufälligen Jitter ist die empfohlene Methode zum Verarbeiten von 429s.</span><span class="sxs-lookup"><span data-stu-id="7abf1-120">Using an exponential backoff with a random jitter is the recommended way to handle 429s.</span></span> <span data-ttu-id="7abf1-121">Dadurch wird sichergestellt, dass bei Wiederholungsversuchen bei mehreren Anforderungen keine Kollisionen auftut.</span><span class="sxs-lookup"><span data-stu-id="7abf1-121">This ensures that multiple requests do not introduce collisions on retries.</span></span>

<span data-ttu-id="7abf1-122">Nachdem Sie Antworten behandeln, können Sie das Beispiel `HTTP 429` zum Erkennen vorübergehender Ausnahmen durchgehen.</span><span class="sxs-lookup"><span data-stu-id="7abf1-122">After you handle `HTTP 429` responses, you can go through the example for detecting transient exceptions.</span></span>

> [!NOTE]
> <span data-ttu-id="7abf1-123">Zusätzlich zum Retyringfehlercode **429** müssen auch die Fehlercodes **412,** **502** und **504** wiederholt werden.</span><span class="sxs-lookup"><span data-stu-id="7abf1-123">In addition to retyring error code **429**, error codes **412**, **502**, and **504** must also be retried.</span></span>

## <a name="detect-transient-exceptions-example"></a><span data-ttu-id="7abf1-124">Erkennen vorübergehender Ausnahmen (Beispiel)</span><span class="sxs-lookup"><span data-stu-id="7abf1-124">Detect transient exceptions example</span></span>

<span data-ttu-id="7abf1-125">Der folgende Code zeigt ein Beispiel für die Verwendung eines exponentiellen Backoffs mithilfe des Anwendungsblocks für die vorübergehende Fehlerbehandlung:</span><span class="sxs-lookup"><span data-stu-id="7abf1-125">The following code shows an example of using exponential backoff using the transient fault handling application block:</span></span>

```csharp
public class BotSdkTransientExceptionDetectionStrategy : ITransientErrorDetectionStrategy
    {
        // List of error codes to retry on
        List<int> transientErrorStatusCodes = new List<int>() { 429 };

        public bool IsTransient(Exception ex)
        {
            if (ex.Message.Contains("429"))
                return true;

            var httpOperationException = ex as HttpOperationException;
            if (httpOperationException != null)
            {
                return httpOperationException.Response != null &&
                        transientErrorStatusCodes.Contains((int)httpOperationException.Response.StatusCode);
            }

            return false;
        }
    }
```

<span data-ttu-id="7abf1-126">Sie können Backoff- und Wiederholungsversuche mithilfe der [vorübergehenden Fehlerbehandlung ausführen.](/previous-versions/msp-n-p/hh675232%28v%3dpandp.10%29)</span><span class="sxs-lookup"><span data-stu-id="7abf1-126">You can perform backoff and retries using [transient fault handling](/previous-versions/msp-n-p/hh675232%28v%3dpandp.10%29).</span></span> <span data-ttu-id="7abf1-127">Richtlinien zum Abrufen und Installieren des NuGet finden Sie unter Hinzufügen des Anwendungsblocks für vorübergehende Fehlerbehandlung [zu Ihrer Lösung](/previous-versions/msp-n-p/dn440719(v=pandp.60)?redirectedfrom=MSDN).</span><span class="sxs-lookup"><span data-stu-id="7abf1-127">For guidelines on obtaining and installing the NuGet package, see [adding the transient fault handling application block to your solution](/previous-versions/msp-n-p/dn440719(v=pandp.60)?redirectedfrom=MSDN).</span></span> <span data-ttu-id="7abf1-128">Siehe auch [vorübergehende Fehlerbehandlung](/azure/architecture/best-practices/transient-faults).</span><span class="sxs-lookup"><span data-stu-id="7abf1-128">See also [transient fault handling](/azure/architecture/best-practices/transient-faults).</span></span>

<span data-ttu-id="7abf1-129">Nachdem Sie das Beispiel zum Erkennen vorübergehender Ausnahmen durchgehen, gehen Sie durch das exponentielle Backoff-Beispiel.</span><span class="sxs-lookup"><span data-stu-id="7abf1-129">After you go through the example for detecting transient exceptions, go through the exponential backoff example.</span></span> <span data-ttu-id="7abf1-130">Sie können exponentielles Backoff verwenden, anstatt Fehler erneut zu wiederholen.</span><span class="sxs-lookup"><span data-stu-id="7abf1-130">You can use exponential backoff instead of retrying on failures.</span></span>

## <a name="backoff-example"></a><span data-ttu-id="7abf1-131">Backoff-Beispiel</span><span class="sxs-lookup"><span data-stu-id="7abf1-131">Backoff example</span></span>

<span data-ttu-id="7abf1-132">Sie können nicht nur Geschwindigkeitsbegrenzungen erkennen, sondern auch ein exponentielles Backoff ausführen.</span><span class="sxs-lookup"><span data-stu-id="7abf1-132">In addition to detecting rate limits, you can also perform an exponential backoff.</span></span>

<span data-ttu-id="7abf1-133">Der folgende Code zeigt ein Beispiel für exponentielles Backoff:</span><span class="sxs-lookup"><span data-stu-id="7abf1-133">The following code shows an example of exponential backoff:</span></span>

```csharp
/**
* The first parameter specifies the number of retries before failing the operation.
* The second parameter specifies the minimum and maximum backoff time respectively.
* The last parameter is used to add a randomized  +/- 20% delta to avoid numerous clients retrying simultaneously.
*/
var exponentialBackoffRetryStrategy = new ExponentialBackoff(3, TimeSpan.FromSeconds(2),
                        TimeSpan.FromSeconds(20), TimeSpan.FromSeconds(1));


// Define the Retry Policy
var retryPolicy = new RetryPolicy(new BotSdkTransientExceptionDetectionStrategy(), exponentialBackoffRetryStrategy);

//Execute any bot sdk action
await retryPolicy.ExecuteAsync(() => connector.Conversations.ReplyToActivityAsync( (Activity)reply) ).ConfigureAwait(false);
```

<span data-ttu-id="7abf1-134">Sie können auch eine Methodenausführung mit der in diesem Abschnitt beschriebenen `System.Action` Wiederholungsrichtlinie ausführen.</span><span class="sxs-lookup"><span data-stu-id="7abf1-134">You can also perform a `System.Action` method execution with the retry policy described in this section.</span></span> <span data-ttu-id="7abf1-135">Mit der referenzierten Bibliothek können Sie auch ein festes Intervall oder einen linearen Backoffmechanismus angeben.</span><span class="sxs-lookup"><span data-stu-id="7abf1-135">The referenced library also allows you to specify a fixed interval or a linear backoff mechanism.</span></span>

<span data-ttu-id="7abf1-136">Store wert und strategie in einer Konfigurationsdatei, um Werte zur Laufzeit zu optimieren und zu optimieren.</span><span class="sxs-lookup"><span data-stu-id="7abf1-136">Store the value and strategy in a configuration file to fine-tune and tweak values at run time.</span></span>

<span data-ttu-id="7abf1-137">Weitere Informationen finden Sie unter [Wiederholungsmuster](/azure/architecture/patterns/retry).</span><span class="sxs-lookup"><span data-stu-id="7abf1-137">For more information, see [retry patterns](/azure/architecture/patterns/retry).</span></span>

<span data-ttu-id="7abf1-138">Sie können auch die Geschwindigkeitsbegrenzung mithilfe der Pro-Bot-Pro-Thread-Grenze behandeln.</span><span class="sxs-lookup"><span data-stu-id="7abf1-138">You can also handle rate limit using the per bot per thread limit.</span></span>

## <a name="per-bot-per-thread-limit"></a><span data-ttu-id="7abf1-139">Pro Bot pro Threadgrenzwert</span><span class="sxs-lookup"><span data-stu-id="7abf1-139">Per bot per thread limit</span></span>

<span data-ttu-id="7abf1-140">Der Grenzwert pro Bot pro Thread steuert den Datenverkehr, den ein Bot in einer einzigen Unterhaltung generieren darf.</span><span class="sxs-lookup"><span data-stu-id="7abf1-140">The per bot per thread limit controls the traffic that a bot is allowed to generate in a single conversation.</span></span> <span data-ttu-id="7abf1-141">Eine Unterhaltung zwischen Bot und Benutzer, einem Gruppenchat oder einem Kanal in einem Team ist 1:1.</span><span class="sxs-lookup"><span data-stu-id="7abf1-141">A conversation is 1:1 between bot and user, a group chat, or a channel in a team.</span></span> <span data-ttu-id="7abf1-142">Wenn die Anwendung also eine Botnachricht an jeden Benutzer sendet, wird der Threadgrenzwert nicht gedrosselt.</span><span class="sxs-lookup"><span data-stu-id="7abf1-142">So, if the application sends one bot message to each user, the thread limit does not throttle.</span></span>

>[!NOTE]
> * <span data-ttu-id="7abf1-143">Der Threadgrenzwert von 3600 Sekunden und 1800 Vorgängen gilt nur, wenn mehrere Botnachrichten an einen einzelnen Benutzer gesendet werden.</span><span class="sxs-lookup"><span data-stu-id="7abf1-143">The thread limit of 3600 seconds and 1800 operations applies only if multiple bot messages are sent to a single user.</span></span> 
> * <span data-ttu-id="7abf1-144">Der globale Grenzwert pro App pro Mandant beträgt 50 Anforderungen pro Sekunde (RPS).</span><span class="sxs-lookup"><span data-stu-id="7abf1-144">The global limit per app per tenant is 50 Requests Per Second (RPS).</span></span> <span data-ttu-id="7abf1-145">Daher darf die Gesamtzahl der Botnachrichten pro Sekunde nicht die Threadbegrenzung überschreiten.</span><span class="sxs-lookup"><span data-stu-id="7abf1-145">Hence, the total number of bot messages per second must not cross the thread limit.</span></span>
> * <span data-ttu-id="7abf1-146">Die Nachrichtenteilung auf Dienstebene führt zu einem höheren RpS als erwartet.</span><span class="sxs-lookup"><span data-stu-id="7abf1-146">Message splitting at the service level results in higher than expected RPS.</span></span> <span data-ttu-id="7abf1-147">Wenn Sie sich Sorgen machen, die Grenzwerte zu überschreiten, müssen Sie die [Backoff-Strategie implementieren.](#backoff-example)</span><span class="sxs-lookup"><span data-stu-id="7abf1-147">If you are concerned about approaching the limits, you must implement the [backoff strategy](#backoff-example).</span></span> <span data-ttu-id="7abf1-148">Die in diesem Abschnitt angegebenen Werte sind nur zur Schätzung vorgesehen.</span><span class="sxs-lookup"><span data-stu-id="7abf1-148">The values provided in this section are for estimation only.</span></span>

<span data-ttu-id="7abf1-149">In der folgenden Tabelle sind die Grenzwerte pro Bot pro Thread aufgeführt:</span><span class="sxs-lookup"><span data-stu-id="7abf1-149">The following table provides the per bot per thread limits:</span></span>

| <span data-ttu-id="7abf1-150">Szenario</span><span class="sxs-lookup"><span data-stu-id="7abf1-150">Scenario</span></span> | <span data-ttu-id="7abf1-151">Zeitraum in Sekunden</span><span class="sxs-lookup"><span data-stu-id="7abf1-151">Time period in seconds</span></span> | <span data-ttu-id="7abf1-152">Maximal zulässige Vorgänge</span><span class="sxs-lookup"><span data-stu-id="7abf1-152">Maximum allowed operations</span></span> |
| --- | --- | --- |
| <span data-ttu-id="7abf1-153">An Unterhaltung senden</span><span class="sxs-lookup"><span data-stu-id="7abf1-153">Send to conversation</span></span> | <span data-ttu-id="7abf1-154">1</span><span class="sxs-lookup"><span data-stu-id="7abf1-154">1</span></span> | <span data-ttu-id="7abf1-155">7 </span><span class="sxs-lookup"><span data-stu-id="7abf1-155">7</span></span> |
| <span data-ttu-id="7abf1-156">An Unterhaltung senden</span><span class="sxs-lookup"><span data-stu-id="7abf1-156">Send to conversation</span></span> | <span data-ttu-id="7abf1-157">2</span><span class="sxs-lookup"><span data-stu-id="7abf1-157">2</span></span> | <span data-ttu-id="7abf1-158">8 </span><span class="sxs-lookup"><span data-stu-id="7abf1-158">8</span></span> |
| <span data-ttu-id="7abf1-159">An Unterhaltung senden</span><span class="sxs-lookup"><span data-stu-id="7abf1-159">Send to conversation</span></span> | <span data-ttu-id="7abf1-160">30</span><span class="sxs-lookup"><span data-stu-id="7abf1-160">30</span></span> | <span data-ttu-id="7abf1-161">60</span><span class="sxs-lookup"><span data-stu-id="7abf1-161">60</span></span> |
| <span data-ttu-id="7abf1-162">An Unterhaltung senden</span><span class="sxs-lookup"><span data-stu-id="7abf1-162">Send to conversation</span></span> | <span data-ttu-id="7abf1-163">3600</span><span class="sxs-lookup"><span data-stu-id="7abf1-163">3600</span></span> | <span data-ttu-id="7abf1-164">1800</span><span class="sxs-lookup"><span data-stu-id="7abf1-164">1800</span></span> |
| <span data-ttu-id="7abf1-165">Unterhaltung erstellen</span><span class="sxs-lookup"><span data-stu-id="7abf1-165">Create conversation</span></span> | <span data-ttu-id="7abf1-166">1</span><span class="sxs-lookup"><span data-stu-id="7abf1-166">1</span></span> | <span data-ttu-id="7abf1-167">7 </span><span class="sxs-lookup"><span data-stu-id="7abf1-167">7</span></span> |
| <span data-ttu-id="7abf1-168">Unterhaltung erstellen</span><span class="sxs-lookup"><span data-stu-id="7abf1-168">Create conversation</span></span> | <span data-ttu-id="7abf1-169">2</span><span class="sxs-lookup"><span data-stu-id="7abf1-169">2</span></span> | <span data-ttu-id="7abf1-170">8 </span><span class="sxs-lookup"><span data-stu-id="7abf1-170">8</span></span> |
| <span data-ttu-id="7abf1-171">Unterhaltung erstellen</span><span class="sxs-lookup"><span data-stu-id="7abf1-171">Create conversation</span></span> | <span data-ttu-id="7abf1-172">30</span><span class="sxs-lookup"><span data-stu-id="7abf1-172">30</span></span> | <span data-ttu-id="7abf1-173">60</span><span class="sxs-lookup"><span data-stu-id="7abf1-173">60</span></span> |
| <span data-ttu-id="7abf1-174">Unterhaltung erstellen</span><span class="sxs-lookup"><span data-stu-id="7abf1-174">Create conversation</span></span> | <span data-ttu-id="7abf1-175">3600</span><span class="sxs-lookup"><span data-stu-id="7abf1-175">3600</span></span> | <span data-ttu-id="7abf1-176">1800</span><span class="sxs-lookup"><span data-stu-id="7abf1-176">1800</span></span> |
| <span data-ttu-id="7abf1-177">Unterhaltungsmitglieder erhalten</span><span class="sxs-lookup"><span data-stu-id="7abf1-177">Get conversation members</span></span>| <span data-ttu-id="7abf1-178">1</span><span class="sxs-lookup"><span data-stu-id="7abf1-178">1</span></span> | <span data-ttu-id="7abf1-179">14 </span><span class="sxs-lookup"><span data-stu-id="7abf1-179">14</span></span> |
| <span data-ttu-id="7abf1-180">Unterhaltungsmitglieder erhalten</span><span class="sxs-lookup"><span data-stu-id="7abf1-180">Get conversation members</span></span>| <span data-ttu-id="7abf1-181">2</span><span class="sxs-lookup"><span data-stu-id="7abf1-181">2</span></span> | <span data-ttu-id="7abf1-182">16 </span><span class="sxs-lookup"><span data-stu-id="7abf1-182">16</span></span> |
| <span data-ttu-id="7abf1-183">Unterhaltungsmitglieder erhalten</span><span class="sxs-lookup"><span data-stu-id="7abf1-183">Get conversation members</span></span>| <span data-ttu-id="7abf1-184">30</span><span class="sxs-lookup"><span data-stu-id="7abf1-184">30</span></span> | <span data-ttu-id="7abf1-185">120</span><span class="sxs-lookup"><span data-stu-id="7abf1-185">120</span></span> |
| <span data-ttu-id="7abf1-186">Unterhaltungsmitglieder erhalten</span><span class="sxs-lookup"><span data-stu-id="7abf1-186">Get conversation members</span></span>| <span data-ttu-id="7abf1-187">3600</span><span class="sxs-lookup"><span data-stu-id="7abf1-187">3600</span></span> | <span data-ttu-id="7abf1-188">3600</span><span class="sxs-lookup"><span data-stu-id="7abf1-188">3600</span></span> |
| <span data-ttu-id="7abf1-189">Unterhaltungen erhalten</span><span class="sxs-lookup"><span data-stu-id="7abf1-189">Get conversations</span></span> | <span data-ttu-id="7abf1-190">1</span><span class="sxs-lookup"><span data-stu-id="7abf1-190">1</span></span> | <span data-ttu-id="7abf1-191">14 </span><span class="sxs-lookup"><span data-stu-id="7abf1-191">14</span></span> |
| <span data-ttu-id="7abf1-192">Unterhaltungen erhalten</span><span class="sxs-lookup"><span data-stu-id="7abf1-192">Get conversations</span></span> | <span data-ttu-id="7abf1-193">2</span><span class="sxs-lookup"><span data-stu-id="7abf1-193">2</span></span> | <span data-ttu-id="7abf1-194">16 </span><span class="sxs-lookup"><span data-stu-id="7abf1-194">16</span></span> |
| <span data-ttu-id="7abf1-195">Unterhaltungen erhalten</span><span class="sxs-lookup"><span data-stu-id="7abf1-195">Get conversations</span></span> | <span data-ttu-id="7abf1-196">30</span><span class="sxs-lookup"><span data-stu-id="7abf1-196">30</span></span> | <span data-ttu-id="7abf1-197">120</span><span class="sxs-lookup"><span data-stu-id="7abf1-197">120</span></span> |
| <span data-ttu-id="7abf1-198">Unterhaltungen erhalten</span><span class="sxs-lookup"><span data-stu-id="7abf1-198">Get conversations</span></span> | <span data-ttu-id="7abf1-199">3600</span><span class="sxs-lookup"><span data-stu-id="7abf1-199">3600</span></span> | <span data-ttu-id="7abf1-200">3600</span><span class="sxs-lookup"><span data-stu-id="7abf1-200">3600</span></span> |

>[!NOTE]
> <span data-ttu-id="7abf1-201">Frühere Versionen `TeamsInfo.getMembers` von und `TeamsInfo.GetMembersAsync` APIs sind veraltet.</span><span class="sxs-lookup"><span data-stu-id="7abf1-201">Previous versions of `TeamsInfo.getMembers` and `TeamsInfo.GetMembersAsync` APIs are being deprecated.</span></span> <span data-ttu-id="7abf1-202">Sie werden auf fünf Anforderungen pro Minute gedrosselt und geben maximal 10.000 Mitglieder pro Team zurück.</span><span class="sxs-lookup"><span data-stu-id="7abf1-202">They are throttled to five requests per minute and return a maximum of 10K members per team.</span></span> <span data-ttu-id="7abf1-203">Informationen zum Aktualisieren Ihres Bot Framework SDK und des Codes zur Verwendung der neuesten paginierten API-Endpunkte finden Sie unter [Bot-API-Änderungen für Team- und Chatmitglieder.](../../resources/team-chat-member-api-changes.md)</span><span class="sxs-lookup"><span data-stu-id="7abf1-203">To update your Bot Framework SDK and the code to use the latest paginated API endpoints, see [Bot API changes for team and chat members](../../resources/team-chat-member-api-changes.md).</span></span>

<span data-ttu-id="7abf1-204">Sie können die Geschwindigkeitsbegrenzung auch mithilfe des Pro-Thread-Grenzwerts für alle Bots behandeln.</span><span class="sxs-lookup"><span data-stu-id="7abf1-204">You can also handle rate limit using the per thread limit for all bots.</span></span>

## <a name="per-thread-limit-for-all-bots"></a><span data-ttu-id="7abf1-205">Grenzwert pro Thread für alle Bots</span><span class="sxs-lookup"><span data-stu-id="7abf1-205">Per thread limit for all bots</span></span>

<span data-ttu-id="7abf1-206">Der Grenzwert pro Thread für alle Bots steuert den Datenverkehr, den alle Bots über eine einzelne Unterhaltung generieren dürfen.</span><span class="sxs-lookup"><span data-stu-id="7abf1-206">The per thread limit for all bots controls the traffic that all bots are allowed to generate across a single conversation.</span></span> <span data-ttu-id="7abf1-207">Eine Unterhaltung hier ist 1:1 zwischen Bot und Benutzer, einem Gruppenchat oder einem Kanal in einem Team.</span><span class="sxs-lookup"><span data-stu-id="7abf1-207">A conversation here is 1:1 between bot and user, a group chat, or a channel in a team.</span></span>

<span data-ttu-id="7abf1-208">In der folgenden Tabelle ist der Grenzwert pro Thread für alle Bots aufgeführt:</span><span class="sxs-lookup"><span data-stu-id="7abf1-208">The following table provides the per thread limit for all bots:</span></span>

| <span data-ttu-id="7abf1-209">Szenario</span><span class="sxs-lookup"><span data-stu-id="7abf1-209">Scenario</span></span> | <span data-ttu-id="7abf1-210">Zeitraum in Sekunden</span><span class="sxs-lookup"><span data-stu-id="7abf1-210">Time period in seconds</span></span> | <span data-ttu-id="7abf1-211">Maximal zulässige Vorgänge</span><span class="sxs-lookup"><span data-stu-id="7abf1-211">Maximum allowed operations</span></span> |
| --- | --- | --- |
| <span data-ttu-id="7abf1-212">An Unterhaltung senden</span><span class="sxs-lookup"><span data-stu-id="7abf1-212">Send to conversation</span></span> | <span data-ttu-id="7abf1-213">1</span><span class="sxs-lookup"><span data-stu-id="7abf1-213">1</span></span> | <span data-ttu-id="7abf1-214">14 </span><span class="sxs-lookup"><span data-stu-id="7abf1-214">14</span></span> |
| <span data-ttu-id="7abf1-215">An Unterhaltung senden</span><span class="sxs-lookup"><span data-stu-id="7abf1-215">Send to conversation</span></span> | <span data-ttu-id="7abf1-216">2</span><span class="sxs-lookup"><span data-stu-id="7abf1-216">2</span></span> | <span data-ttu-id="7abf1-217">16 </span><span class="sxs-lookup"><span data-stu-id="7abf1-217">16</span></span> |
| <span data-ttu-id="7abf1-218">Unterhaltung erstellen</span><span class="sxs-lookup"><span data-stu-id="7abf1-218">Create conversation</span></span> | <span data-ttu-id="7abf1-219">1</span><span class="sxs-lookup"><span data-stu-id="7abf1-219">1</span></span> | <span data-ttu-id="7abf1-220">14 </span><span class="sxs-lookup"><span data-stu-id="7abf1-220">14</span></span> |
| <span data-ttu-id="7abf1-221">Unterhaltung erstellen</span><span class="sxs-lookup"><span data-stu-id="7abf1-221">Create conversation</span></span> | <span data-ttu-id="7abf1-222">2</span><span class="sxs-lookup"><span data-stu-id="7abf1-222">2</span></span> | <span data-ttu-id="7abf1-223">16 </span><span class="sxs-lookup"><span data-stu-id="7abf1-223">16</span></span> |
| <span data-ttu-id="7abf1-224">Unterhaltung erstellen</span><span class="sxs-lookup"><span data-stu-id="7abf1-224">Create conversation</span></span>| <span data-ttu-id="7abf1-225">1</span><span class="sxs-lookup"><span data-stu-id="7abf1-225">1</span></span> | <span data-ttu-id="7abf1-226">14 </span><span class="sxs-lookup"><span data-stu-id="7abf1-226">14</span></span> |
| <span data-ttu-id="7abf1-227">Unterhaltung erstellen</span><span class="sxs-lookup"><span data-stu-id="7abf1-227">Create conversation</span></span>| <span data-ttu-id="7abf1-228">2</span><span class="sxs-lookup"><span data-stu-id="7abf1-228">2</span></span> | <span data-ttu-id="7abf1-229">16 </span><span class="sxs-lookup"><span data-stu-id="7abf1-229">16</span></span> |
| <span data-ttu-id="7abf1-230">Unterhaltungsmitglieder erhalten</span><span class="sxs-lookup"><span data-stu-id="7abf1-230">Get conversation members</span></span>| <span data-ttu-id="7abf1-231">1</span><span class="sxs-lookup"><span data-stu-id="7abf1-231">1</span></span> | <span data-ttu-id="7abf1-232">28</span><span class="sxs-lookup"><span data-stu-id="7abf1-232">28</span></span> |
| <span data-ttu-id="7abf1-233">Unterhaltungsmitglieder erhalten</span><span class="sxs-lookup"><span data-stu-id="7abf1-233">Get conversation members</span></span>| <span data-ttu-id="7abf1-234">2</span><span class="sxs-lookup"><span data-stu-id="7abf1-234">2</span></span> | <span data-ttu-id="7abf1-235">32</span><span class="sxs-lookup"><span data-stu-id="7abf1-235">32</span></span> |
| <span data-ttu-id="7abf1-236">Unterhaltungen erhalten</span><span class="sxs-lookup"><span data-stu-id="7abf1-236">Get conversations</span></span> | <span data-ttu-id="7abf1-237">1</span><span class="sxs-lookup"><span data-stu-id="7abf1-237">1</span></span> | <span data-ttu-id="7abf1-238">28</span><span class="sxs-lookup"><span data-stu-id="7abf1-238">28</span></span> |
| <span data-ttu-id="7abf1-239">Unterhaltungen erhalten</span><span class="sxs-lookup"><span data-stu-id="7abf1-239">Get conversations</span></span> | <span data-ttu-id="7abf1-240">2</span><span class="sxs-lookup"><span data-stu-id="7abf1-240">2</span></span> | <span data-ttu-id="7abf1-241">32</span><span class="sxs-lookup"><span data-stu-id="7abf1-241">32</span></span> |

## <a name="next-step"></a><span data-ttu-id="7abf1-242">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="7abf1-242">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7abf1-243">Anrufe und Besprechungsbots</span><span class="sxs-lookup"><span data-stu-id="7abf1-243">Calls and meetings bots</span></span>](~/bots/calls-and-meetings/calls-meetings-bots-overview.md)

