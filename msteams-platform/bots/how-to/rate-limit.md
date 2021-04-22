---
title: Optimieren eines Bots mit Ratenbegrenzung in Teams
description: Geschwindigkeitsbegrenzung und bewährte Methoden in Microsoft Teams
ms.topic: conceptual
keywords: Beschränkung der Rate von Teams-Bots
ms.openlocfilehash: 690d09e4a3b611c024f32d3776ca73e42d63ee7f
ms.sourcegitcommit: 35bc2a31b92f3f7c6524373108f095a870d9ad09
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/21/2021
ms.locfileid: "51922503"
---
# <a name="optimize-your-bot-with-rate-limiting-in-teams"></a><span data-ttu-id="0532d-104">Optimieren eines Bots mit Ratenbegrenzung in Teams</span><span class="sxs-lookup"><span data-stu-id="0532d-104">Optimize your bot with rate limiting in Teams</span></span>

<span data-ttu-id="0532d-105">Die Geschwindigkeitsbegrenzung ist eine Methode, um Nachrichten auf eine bestimmte maximale Häufigkeit zu beschränken.</span><span class="sxs-lookup"><span data-stu-id="0532d-105">Rate limiting is a method to limit messages to a certain maximum frequency.</span></span> <span data-ttu-id="0532d-106">Als allgemeines Prinzip muss Ihre Anwendung die Anzahl der Von ihr gesendeten Nachrichten auf eine einzelne Chat- oder Kanal unterhaltung beschränken.</span><span class="sxs-lookup"><span data-stu-id="0532d-106">As a general principle, your application must limit the number of messages it posts to an individual chat or channel conversation.</span></span> <span data-ttu-id="0532d-107">Dadurch wird eine optimale Benutzererfahrung sichergestellt, und Nachrichten werden ihren Benutzern nicht als Spam angezeigt.</span><span class="sxs-lookup"><span data-stu-id="0532d-107">This ensures an optimal experience and messages do not appear as spam to your users.</span></span>

<span data-ttu-id="0532d-108">Zum Schutz von Microsoft Teams und seinen Benutzern bieten die Bot-APIs eine Geschwindigkeitsbeschränkung für eingehende Anforderungen.</span><span class="sxs-lookup"><span data-stu-id="0532d-108">To protect Microsoft Teams and its users, the bot APIs provide a rate limit for incoming requests.</span></span> <span data-ttu-id="0532d-109">Apps, die diesen Grenzwert überschreiten, erhalten einen `HTTP 429 Too Many Requests` Fehlerstatus.</span><span class="sxs-lookup"><span data-stu-id="0532d-109">Apps that go over this limit receive an `HTTP 429 Too Many Requests` error status.</span></span> <span data-ttu-id="0532d-110">Alle Anforderungen unterliegen der gleichen Richtlinie zur Begrenzung der Rate, einschließlich des Sendens von Nachrichten, Kanalaufzählungen und Abrufen von Dienstplans.</span><span class="sxs-lookup"><span data-stu-id="0532d-110">All requests are subject to the same rate limiting policy, including sending messages, channel enumerations, and roster fetches.</span></span>

<span data-ttu-id="0532d-111">Da sich die genauen Werte der Zinsgrenzen ändern können, muss Ihre Anwendung das entsprechende Backoff-Verhalten implementieren, wenn die API `HTTP 429 Too Many Requests` zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="0532d-111">As the exact values of rate limits are subject to change, your application must implement the appropriate backoff behavior when the API returns `HTTP 429 Too Many Requests`.</span></span>

## <a name="handle-rate-limits"></a><span data-ttu-id="0532d-112">Behandeln von Satzbegrenzungen</span><span class="sxs-lookup"><span data-stu-id="0532d-112">Handle rate limits</span></span>

<span data-ttu-id="0532d-113">Beim Ausstellen eines Bot Builder-SDK-Vorgangs können Sie den Statuscode `Microsoft.Rest.HttpOperationException` behandeln und überprüfen.</span><span class="sxs-lookup"><span data-stu-id="0532d-113">When issuing a Bot Builder SDK operation, you can handle `Microsoft.Rest.HttpOperationException` and check for the status code.</span></span>

<span data-ttu-id="0532d-114">Der folgende Code zeigt ein Beispiel für die Behandlung von Geschwindigkeitsbeschränkungen:</span><span class="sxs-lookup"><span data-stu-id="0532d-114">The following code shows an example of handling rate limits:</span></span>

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

<span data-ttu-id="0532d-115">Nachdem Sie die Geschwindigkeitsbeschränkungen für Bots umgangen haben, können Sie Antworten mithilfe eines `HTTP 429` exponentiellen Backoffs behandeln.</span><span class="sxs-lookup"><span data-stu-id="0532d-115">After you handle rate limits for bots, you can handle `HTTP 429` responses using an exponential backoff.</span></span>

## <a name="handle-http-429-responses"></a><span data-ttu-id="0532d-116">Behandeln von `HTTP 429` Antworten</span><span class="sxs-lookup"><span data-stu-id="0532d-116">Handle `HTTP 429` responses</span></span>

<span data-ttu-id="0532d-117">Im Allgemeinen müssen Sie einfache Vorsichtsmaßnahmen ergreifen, um den Empfang von Antworten `HTTP 429` zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="0532d-117">In general, you must take simple precautions to avoid receiving `HTTP 429` responses.</span></span> <span data-ttu-id="0532d-118">Vermeiden Sie beispielsweise, mehrere Anforderungen an dieselbe persönliche Unterhaltung oder eine Kanal unterhaltung ausstellen.</span><span class="sxs-lookup"><span data-stu-id="0532d-118">For example, avoid issuing multiple requests to the same personal or channel conversation.</span></span> <span data-ttu-id="0532d-119">Erstellen Sie stattdessen einen Batch der API-Anforderungen.</span><span class="sxs-lookup"><span data-stu-id="0532d-119">Instead, create a batch of the API requests.</span></span>

<span data-ttu-id="0532d-120">Die Verwendung eines exponentiellen Backoffs mit einem zufälligen Jitter ist die empfohlene Methode zum Verarbeiten von 429s.</span><span class="sxs-lookup"><span data-stu-id="0532d-120">Using an exponential backoff with a random jitter is the recommended way to handle 429s.</span></span> <span data-ttu-id="0532d-121">Dadurch wird sichergestellt, dass bei Wiederholungsversuchen bei mehreren Anforderungen keine Kollisionen auftut.</span><span class="sxs-lookup"><span data-stu-id="0532d-121">This ensures that multiple requests do not introduce collisions on retries.</span></span>

<span data-ttu-id="0532d-122">Nachdem Sie Antworten behandeln, können Sie das Beispiel `HTTP 429` zum Erkennen vorübergehender Ausnahmen durchgehen.</span><span class="sxs-lookup"><span data-stu-id="0532d-122">After you handle `HTTP 429` responses, you can go through the example for detecting transient exceptions.</span></span>

## <a name="detect-transient-exceptions-example"></a><span data-ttu-id="0532d-123">Erkennen vorübergehender Ausnahmen (Beispiel)</span><span class="sxs-lookup"><span data-stu-id="0532d-123">Detect transient exceptions example</span></span>

<span data-ttu-id="0532d-124">Der folgende Code zeigt ein Beispiel für die Verwendung eines exponentiellen Backoffs mithilfe des Anwendungsblocks für die vorübergehende Fehlerbehandlung:</span><span class="sxs-lookup"><span data-stu-id="0532d-124">The following code shows an example of using exponential backoff using the transient fault handling application block:</span></span>

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

<span data-ttu-id="0532d-125">Sie können Backoff- und Wiederholungsversuche mithilfe der [vorübergehenden Fehlerbehandlung ausführen.](/previous-versions/msp-n-p/hh675232%28v%3dpandp.10%29)</span><span class="sxs-lookup"><span data-stu-id="0532d-125">You can perform backoff and retries using [transient fault handling](/previous-versions/msp-n-p/hh675232%28v%3dpandp.10%29).</span></span> <span data-ttu-id="0532d-126">Richtlinien zum Abrufen und Installieren des NuGet-Pakets finden Sie unter Hinzufügen des Anwendungsblocks für die vorübergehende [Fehlerbehandlung zu Ihrer Lösung.](/previous-versions/msp-n-p/dn440719(v=pandp.60)?redirectedfrom=MSDN)</span><span class="sxs-lookup"><span data-stu-id="0532d-126">For guidelines on obtaining and installing the NuGet package, see [adding the transient fault handling application block to your solution](/previous-versions/msp-n-p/dn440719(v=pandp.60)?redirectedfrom=MSDN).</span></span> <span data-ttu-id="0532d-127">Siehe auch [vorübergehende Fehlerbehandlung](/azure/architecture/best-practices/transient-faults).</span><span class="sxs-lookup"><span data-stu-id="0532d-127">See also [transient fault handling](/azure/architecture/best-practices/transient-faults).</span></span>

<span data-ttu-id="0532d-128">Nachdem Sie das Beispiel zum Erkennen vorübergehender Ausnahmen durchgehen, gehen Sie durch das exponentielle Backoff-Beispiel.</span><span class="sxs-lookup"><span data-stu-id="0532d-128">After you go through the example for detecting transient exceptions, go through the exponential backoff example.</span></span> <span data-ttu-id="0532d-129">Sie können exponentielles Backoff verwenden, anstatt Fehler erneut zu wiederholen.</span><span class="sxs-lookup"><span data-stu-id="0532d-129">You can use exponential backoff instead of retrying on failures.</span></span>

## <a name="backoff-example"></a><span data-ttu-id="0532d-130">Backoff-Beispiel</span><span class="sxs-lookup"><span data-stu-id="0532d-130">Backoff example</span></span>

<span data-ttu-id="0532d-131">Sie können nicht nur Geschwindigkeitsbegrenzungen erkennen, sondern auch ein exponentielles Backoff ausführen.</span><span class="sxs-lookup"><span data-stu-id="0532d-131">In addition to detecting rate limits, you can also perform an exponential backoff.</span></span>

<span data-ttu-id="0532d-132">Der folgende Code zeigt ein Beispiel für exponentielles Backoff:</span><span class="sxs-lookup"><span data-stu-id="0532d-132">The following code shows an example of exponential backoff:</span></span>

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

<span data-ttu-id="0532d-133">Sie können auch eine Methodenausführung mit der in diesem Abschnitt beschriebenen `System.Action` Wiederholungsrichtlinie ausführen.</span><span class="sxs-lookup"><span data-stu-id="0532d-133">You can also perform a `System.Action` method execution with the retry policy described in this section.</span></span> <span data-ttu-id="0532d-134">Mit der referenzierten Bibliothek können Sie auch ein festes Intervall oder einen linearen Backoffmechanismus angeben.</span><span class="sxs-lookup"><span data-stu-id="0532d-134">The referenced library also allows you to specify a fixed interval or a linear backoff mechanism.</span></span>

<span data-ttu-id="0532d-135">Speichern Sie den Wert und die Strategie in einer Konfigurationsdatei, um Werte zur Laufzeit zu optimieren und zu optimieren.</span><span class="sxs-lookup"><span data-stu-id="0532d-135">Store the value and strategy in a configuration file to fine-tune and tweak values at run time.</span></span>

<span data-ttu-id="0532d-136">Weitere Informationen finden Sie unter [Wiederholungsmuster](/azure/architecture/patterns/retry).</span><span class="sxs-lookup"><span data-stu-id="0532d-136">For more information, see [retry patterns](/azure/architecture/patterns/retry).</span></span>

<span data-ttu-id="0532d-137">Sie können auch die Geschwindigkeitsbegrenzung mithilfe der Pro-Bot-Pro-Thread-Grenze behandeln.</span><span class="sxs-lookup"><span data-stu-id="0532d-137">You can also handle rate limit using the per bot per thread limit.</span></span>

## <a name="per-bot-per-thread-limit"></a><span data-ttu-id="0532d-138">Pro Bot pro Threadgrenzwert</span><span class="sxs-lookup"><span data-stu-id="0532d-138">Per bot per thread limit</span></span>

<span data-ttu-id="0532d-139">Der Grenzwert pro Bot pro Thread steuert den Datenverkehr, den ein Bot in einer einzigen Unterhaltung generieren darf.</span><span class="sxs-lookup"><span data-stu-id="0532d-139">The per bot per thread limit controls the traffic that a bot is allowed to generate in a single conversation.</span></span> <span data-ttu-id="0532d-140">Eine Unterhaltung zwischen Bot und Benutzer, einem Gruppenchat oder einem Kanal in einem Team ist 1:1.</span><span class="sxs-lookup"><span data-stu-id="0532d-140">A conversation is 1:1 between bot and user, a group chat, or a channel in a team.</span></span> <span data-ttu-id="0532d-141">Wenn die Anwendung also eine Botnachricht an jeden Benutzer sendet, wird der Threadgrenzwert nicht gedrosselt.</span><span class="sxs-lookup"><span data-stu-id="0532d-141">So, if the application sends one bot message to each user, the thread limit does not throttle.</span></span>

>[!NOTE]
> * <span data-ttu-id="0532d-142">Der Threadgrenzwert von 3600 Sekunden und 1800 Vorgängen gilt nur, wenn mehrere Botnachrichten an einen einzelnen Benutzer gesendet werden.</span><span class="sxs-lookup"><span data-stu-id="0532d-142">The thread limit of 3600 seconds and 1800 operations applies only if multiple bot messages are sent to a single user.</span></span> 
> * <span data-ttu-id="0532d-143">Der globale Grenzwert pro App pro Mandant beträgt 30 Anforderungen pro Sekunde (RPS).</span><span class="sxs-lookup"><span data-stu-id="0532d-143">The global limit per app per tenant is 30 Requests Per Second (RPS).</span></span> <span data-ttu-id="0532d-144">Daher darf die Gesamtzahl der Botnachrichten pro Sekunde nicht die Threadbegrenzung überschreiten.</span><span class="sxs-lookup"><span data-stu-id="0532d-144">Hence, the total number of bot messages per second must not cross the thread limit.</span></span>
> * <span data-ttu-id="0532d-145">Die Nachrichtenteilung auf Dienstebene führt zu einem höheren RpS als erwartet.</span><span class="sxs-lookup"><span data-stu-id="0532d-145">Message splitting at the service level results in higher than expected RPS.</span></span> <span data-ttu-id="0532d-146">Wenn Sie sich Sorgen machen, die Grenzwerte zu überschreiten, müssen Sie die [Backoff-Strategie implementieren.](#backoff-example)</span><span class="sxs-lookup"><span data-stu-id="0532d-146">If you are concerned about approaching the limits, you must implement the [backoff strategy](#backoff-example).</span></span> <span data-ttu-id="0532d-147">Die in diesem Abschnitt angegebenen Werte sind nur zur Schätzung vorgesehen.</span><span class="sxs-lookup"><span data-stu-id="0532d-147">The values provided in this section are for estimation only.</span></span>

<span data-ttu-id="0532d-148">In der folgenden Tabelle sind die Grenzwerte pro Bot pro Thread aufgeführt:</span><span class="sxs-lookup"><span data-stu-id="0532d-148">The following table provides the per bot per thread limits:</span></span>

| <span data-ttu-id="0532d-149">Szenario</span><span class="sxs-lookup"><span data-stu-id="0532d-149">Scenario</span></span> | <span data-ttu-id="0532d-150">Zeitraum in Sekunden</span><span class="sxs-lookup"><span data-stu-id="0532d-150">Time period in seconds</span></span> | <span data-ttu-id="0532d-151">Maximal zulässige Vorgänge</span><span class="sxs-lookup"><span data-stu-id="0532d-151">Maximum allowed operations</span></span> |
| --- | --- | --- |
| <span data-ttu-id="0532d-152">An Unterhaltung senden</span><span class="sxs-lookup"><span data-stu-id="0532d-152">Send to conversation</span></span> | <span data-ttu-id="0532d-153">1</span><span class="sxs-lookup"><span data-stu-id="0532d-153">1</span></span> | <span data-ttu-id="0532d-154">7 </span><span class="sxs-lookup"><span data-stu-id="0532d-154">7</span></span> |
| <span data-ttu-id="0532d-155">An Unterhaltung senden</span><span class="sxs-lookup"><span data-stu-id="0532d-155">Send to conversation</span></span> | <span data-ttu-id="0532d-156">2</span><span class="sxs-lookup"><span data-stu-id="0532d-156">2</span></span> | <span data-ttu-id="0532d-157">8 </span><span class="sxs-lookup"><span data-stu-id="0532d-157">8</span></span> |
| <span data-ttu-id="0532d-158">An Unterhaltung senden</span><span class="sxs-lookup"><span data-stu-id="0532d-158">Send to conversation</span></span> | <span data-ttu-id="0532d-159">30</span><span class="sxs-lookup"><span data-stu-id="0532d-159">30</span></span> | <span data-ttu-id="0532d-160">60</span><span class="sxs-lookup"><span data-stu-id="0532d-160">60</span></span> |
| <span data-ttu-id="0532d-161">An Unterhaltung senden</span><span class="sxs-lookup"><span data-stu-id="0532d-161">Send to conversation</span></span> | <span data-ttu-id="0532d-162">3600</span><span class="sxs-lookup"><span data-stu-id="0532d-162">3600</span></span> | <span data-ttu-id="0532d-163">1800</span><span class="sxs-lookup"><span data-stu-id="0532d-163">1800</span></span> |
| <span data-ttu-id="0532d-164">Unterhaltung erstellen</span><span class="sxs-lookup"><span data-stu-id="0532d-164">Create conversation</span></span> | <span data-ttu-id="0532d-165">1</span><span class="sxs-lookup"><span data-stu-id="0532d-165">1</span></span> | <span data-ttu-id="0532d-166">7 </span><span class="sxs-lookup"><span data-stu-id="0532d-166">7</span></span> |
| <span data-ttu-id="0532d-167">Unterhaltung erstellen</span><span class="sxs-lookup"><span data-stu-id="0532d-167">Create conversation</span></span> | <span data-ttu-id="0532d-168">2</span><span class="sxs-lookup"><span data-stu-id="0532d-168">2</span></span> | <span data-ttu-id="0532d-169">8 </span><span class="sxs-lookup"><span data-stu-id="0532d-169">8</span></span> |
| <span data-ttu-id="0532d-170">Unterhaltung erstellen</span><span class="sxs-lookup"><span data-stu-id="0532d-170">Create conversation</span></span> | <span data-ttu-id="0532d-171">30</span><span class="sxs-lookup"><span data-stu-id="0532d-171">30</span></span> | <span data-ttu-id="0532d-172">60</span><span class="sxs-lookup"><span data-stu-id="0532d-172">60</span></span> |
| <span data-ttu-id="0532d-173">Unterhaltung erstellen</span><span class="sxs-lookup"><span data-stu-id="0532d-173">Create conversation</span></span> | <span data-ttu-id="0532d-174">3600</span><span class="sxs-lookup"><span data-stu-id="0532d-174">3600</span></span> | <span data-ttu-id="0532d-175">1800</span><span class="sxs-lookup"><span data-stu-id="0532d-175">1800</span></span> |
| <span data-ttu-id="0532d-176">Unterhaltungsmitglieder erhalten</span><span class="sxs-lookup"><span data-stu-id="0532d-176">Get conversation members</span></span>| <span data-ttu-id="0532d-177">1</span><span class="sxs-lookup"><span data-stu-id="0532d-177">1</span></span> | <span data-ttu-id="0532d-178">14 </span><span class="sxs-lookup"><span data-stu-id="0532d-178">14</span></span> |
| <span data-ttu-id="0532d-179">Unterhaltungsmitglieder erhalten</span><span class="sxs-lookup"><span data-stu-id="0532d-179">Get conversation members</span></span>| <span data-ttu-id="0532d-180">2</span><span class="sxs-lookup"><span data-stu-id="0532d-180">2</span></span> | <span data-ttu-id="0532d-181">16 </span><span class="sxs-lookup"><span data-stu-id="0532d-181">16</span></span> |
| <span data-ttu-id="0532d-182">Unterhaltungsmitglieder erhalten</span><span class="sxs-lookup"><span data-stu-id="0532d-182">Get conversation members</span></span>| <span data-ttu-id="0532d-183">30</span><span class="sxs-lookup"><span data-stu-id="0532d-183">30</span></span> | <span data-ttu-id="0532d-184">120</span><span class="sxs-lookup"><span data-stu-id="0532d-184">120</span></span> |
| <span data-ttu-id="0532d-185">Unterhaltungsmitglieder erhalten</span><span class="sxs-lookup"><span data-stu-id="0532d-185">Get conversation members</span></span>| <span data-ttu-id="0532d-186">3600</span><span class="sxs-lookup"><span data-stu-id="0532d-186">3600</span></span> | <span data-ttu-id="0532d-187">3600</span><span class="sxs-lookup"><span data-stu-id="0532d-187">3600</span></span> |
| <span data-ttu-id="0532d-188">Unterhaltungen erhalten</span><span class="sxs-lookup"><span data-stu-id="0532d-188">Get conversations</span></span> | <span data-ttu-id="0532d-189">1</span><span class="sxs-lookup"><span data-stu-id="0532d-189">1</span></span> | <span data-ttu-id="0532d-190">14 </span><span class="sxs-lookup"><span data-stu-id="0532d-190">14</span></span> |
| <span data-ttu-id="0532d-191">Unterhaltungen erhalten</span><span class="sxs-lookup"><span data-stu-id="0532d-191">Get conversations</span></span> | <span data-ttu-id="0532d-192">2</span><span class="sxs-lookup"><span data-stu-id="0532d-192">2</span></span> | <span data-ttu-id="0532d-193">16 </span><span class="sxs-lookup"><span data-stu-id="0532d-193">16</span></span> |
| <span data-ttu-id="0532d-194">Unterhaltungen erhalten</span><span class="sxs-lookup"><span data-stu-id="0532d-194">Get conversations</span></span> | <span data-ttu-id="0532d-195">30</span><span class="sxs-lookup"><span data-stu-id="0532d-195">30</span></span> | <span data-ttu-id="0532d-196">120</span><span class="sxs-lookup"><span data-stu-id="0532d-196">120</span></span> |
| <span data-ttu-id="0532d-197">Unterhaltungen erhalten</span><span class="sxs-lookup"><span data-stu-id="0532d-197">Get conversations</span></span> | <span data-ttu-id="0532d-198">3600</span><span class="sxs-lookup"><span data-stu-id="0532d-198">3600</span></span> | <span data-ttu-id="0532d-199">3600</span><span class="sxs-lookup"><span data-stu-id="0532d-199">3600</span></span> |

>[!NOTE]
> <span data-ttu-id="0532d-200">Frühere Versionen `TeamsInfo.getMembers` von und `TeamsInfo.GetMembersAsync` APIs sind veraltet.</span><span class="sxs-lookup"><span data-stu-id="0532d-200">Previous versions of `TeamsInfo.getMembers` and `TeamsInfo.GetMembersAsync` APIs are being deprecated.</span></span> <span data-ttu-id="0532d-201">Sie werden auf fünf Anforderungen pro Minute gedrosselt und geben maximal 10.000 Mitglieder pro Team zurück.</span><span class="sxs-lookup"><span data-stu-id="0532d-201">They are throttled to five requests per minute and return a maximum of 10K members per team.</span></span> <span data-ttu-id="0532d-202">Informationen zum Aktualisieren Ihres Bot Framework SDK und des Codes zur Verwendung der neuesten paginierten API-Endpunkte finden Sie unter [Bot-API-Änderungen für Team- und Chatmitglieder.](../../resources/team-chat-member-api-changes.md)</span><span class="sxs-lookup"><span data-stu-id="0532d-202">To update your Bot Framework SDK and the code to use the latest paginated API endpoints, see [Bot API changes for team and chat members](../../resources/team-chat-member-api-changes.md).</span></span>

<span data-ttu-id="0532d-203">Sie können die Geschwindigkeitsbegrenzung auch mithilfe des Pro-Thread-Grenzwerts für alle Bots behandeln.</span><span class="sxs-lookup"><span data-stu-id="0532d-203">You can also handle rate limit using the per thread limit for all bots.</span></span>

## <a name="per-thread-limit-for-all-bots"></a><span data-ttu-id="0532d-204">Grenzwert pro Thread für alle Bots</span><span class="sxs-lookup"><span data-stu-id="0532d-204">Per thread limit for all bots</span></span>

<span data-ttu-id="0532d-205">Der Grenzwert pro Thread für alle Bots steuert den Datenverkehr, den alle Bots über eine einzelne Unterhaltung generieren dürfen.</span><span class="sxs-lookup"><span data-stu-id="0532d-205">The per thread limit for all bots controls the traffic that all bots are allowed to generate across a single conversation.</span></span> <span data-ttu-id="0532d-206">Eine Unterhaltung hier ist 1:1 zwischen Bot und Benutzer, einem Gruppenchat oder einem Kanal in einem Team.</span><span class="sxs-lookup"><span data-stu-id="0532d-206">A conversation here is 1:1 between bot and user, a group chat, or a channel in a team.</span></span>

<span data-ttu-id="0532d-207">In der folgenden Tabelle ist der Grenzwert pro Thread für alle Bots aufgeführt:</span><span class="sxs-lookup"><span data-stu-id="0532d-207">The following table provides the per thread limit for all bots:</span></span>

| <span data-ttu-id="0532d-208">Szenario</span><span class="sxs-lookup"><span data-stu-id="0532d-208">Scenario</span></span> | <span data-ttu-id="0532d-209">Zeitraum in Sekunden</span><span class="sxs-lookup"><span data-stu-id="0532d-209">Time period in seconds</span></span> | <span data-ttu-id="0532d-210">Maximal zulässige Vorgänge</span><span class="sxs-lookup"><span data-stu-id="0532d-210">Maximum allowed operations</span></span> |
| --- | --- | --- |
| <span data-ttu-id="0532d-211">An Unterhaltung senden</span><span class="sxs-lookup"><span data-stu-id="0532d-211">Send to conversation</span></span> | <span data-ttu-id="0532d-212">1</span><span class="sxs-lookup"><span data-stu-id="0532d-212">1</span></span> | <span data-ttu-id="0532d-213">14 </span><span class="sxs-lookup"><span data-stu-id="0532d-213">14</span></span> |
| <span data-ttu-id="0532d-214">An Unterhaltung senden</span><span class="sxs-lookup"><span data-stu-id="0532d-214">Send to conversation</span></span> | <span data-ttu-id="0532d-215">2</span><span class="sxs-lookup"><span data-stu-id="0532d-215">2</span></span> | <span data-ttu-id="0532d-216">16 </span><span class="sxs-lookup"><span data-stu-id="0532d-216">16</span></span> |
| <span data-ttu-id="0532d-217">Unterhaltung erstellen</span><span class="sxs-lookup"><span data-stu-id="0532d-217">Create conversation</span></span> | <span data-ttu-id="0532d-218">1</span><span class="sxs-lookup"><span data-stu-id="0532d-218">1</span></span> | <span data-ttu-id="0532d-219">14 </span><span class="sxs-lookup"><span data-stu-id="0532d-219">14</span></span> |
| <span data-ttu-id="0532d-220">Unterhaltung erstellen</span><span class="sxs-lookup"><span data-stu-id="0532d-220">Create conversation</span></span> | <span data-ttu-id="0532d-221">2</span><span class="sxs-lookup"><span data-stu-id="0532d-221">2</span></span> | <span data-ttu-id="0532d-222">16 </span><span class="sxs-lookup"><span data-stu-id="0532d-222">16</span></span> |
| <span data-ttu-id="0532d-223">Unterhaltung erstellen</span><span class="sxs-lookup"><span data-stu-id="0532d-223">Create conversation</span></span>| <span data-ttu-id="0532d-224">1</span><span class="sxs-lookup"><span data-stu-id="0532d-224">1</span></span> | <span data-ttu-id="0532d-225">14 </span><span class="sxs-lookup"><span data-stu-id="0532d-225">14</span></span> |
| <span data-ttu-id="0532d-226">Unterhaltung erstellen</span><span class="sxs-lookup"><span data-stu-id="0532d-226">Create conversation</span></span>| <span data-ttu-id="0532d-227">2</span><span class="sxs-lookup"><span data-stu-id="0532d-227">2</span></span> | <span data-ttu-id="0532d-228">16 </span><span class="sxs-lookup"><span data-stu-id="0532d-228">16</span></span> |
| <span data-ttu-id="0532d-229">Unterhaltungsmitglieder erhalten</span><span class="sxs-lookup"><span data-stu-id="0532d-229">Get conversation members</span></span>| <span data-ttu-id="0532d-230">1</span><span class="sxs-lookup"><span data-stu-id="0532d-230">1</span></span> | <span data-ttu-id="0532d-231">28</span><span class="sxs-lookup"><span data-stu-id="0532d-231">28</span></span> |
| <span data-ttu-id="0532d-232">Unterhaltungsmitglieder erhalten</span><span class="sxs-lookup"><span data-stu-id="0532d-232">Get conversation members</span></span>| <span data-ttu-id="0532d-233">2</span><span class="sxs-lookup"><span data-stu-id="0532d-233">2</span></span> | <span data-ttu-id="0532d-234">32</span><span class="sxs-lookup"><span data-stu-id="0532d-234">32</span></span> |
| <span data-ttu-id="0532d-235">Unterhaltungen erhalten</span><span class="sxs-lookup"><span data-stu-id="0532d-235">Get conversations</span></span> | <span data-ttu-id="0532d-236">1</span><span class="sxs-lookup"><span data-stu-id="0532d-236">1</span></span> | <span data-ttu-id="0532d-237">28</span><span class="sxs-lookup"><span data-stu-id="0532d-237">28</span></span> |
| <span data-ttu-id="0532d-238">Unterhaltungen erhalten</span><span class="sxs-lookup"><span data-stu-id="0532d-238">Get conversations</span></span> | <span data-ttu-id="0532d-239">2</span><span class="sxs-lookup"><span data-stu-id="0532d-239">2</span></span> | <span data-ttu-id="0532d-240">32</span><span class="sxs-lookup"><span data-stu-id="0532d-240">32</span></span> |

## <a name="next-step"></a><span data-ttu-id="0532d-241">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="0532d-241">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="0532d-242">Anrufe und Besprechungsbots</span><span class="sxs-lookup"><span data-stu-id="0532d-242">Calls and meetings bots</span></span>](~/bots/calls-and-meetings/calls-meetings-bots-overview.md)

