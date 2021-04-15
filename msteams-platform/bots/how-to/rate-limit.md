---
title: Optimieren eines Bots mit Ratenbegrenzung in Teams
description: Geschwindigkeitsbegrenzung und bewährte Methoden in Microsoft Teams
ms.topic: conceptual
keywords: Beschränkung der Rate von Teams-Bots
ms.openlocfilehash: 245c51fc736e5f888299535c3e50ec6232183623
ms.sourcegitcommit: 79e6bccfb513d4c16a58ffc03521edcf134fa518
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/13/2021
ms.locfileid: "51696997"
---
# <a name="optimize-your-bot-with-rate-limiting-in-teams"></a><span data-ttu-id="8c2c7-104">Optimieren eines Bots mit Ratenbegrenzung in Teams</span><span class="sxs-lookup"><span data-stu-id="8c2c7-104">Optimize your bot with rate limiting in Teams</span></span>

<span data-ttu-id="8c2c7-105">Die Geschwindigkeitsbegrenzung ist eine Methode, um Nachrichten auf eine bestimmte maximale Häufigkeit zu beschränken.</span><span class="sxs-lookup"><span data-stu-id="8c2c7-105">Rate limiting is a method to limit messages to a certain maximum frequency.</span></span> <span data-ttu-id="8c2c7-106">Als allgemeines Prinzip muss Ihre Anwendung die Anzahl der Von ihr gesendeten Nachrichten auf eine einzelne Chat- oder Kanal unterhaltung beschränken.</span><span class="sxs-lookup"><span data-stu-id="8c2c7-106">As a general principle, your application must limit the number of messages it posts to an individual chat or channel conversation.</span></span> <span data-ttu-id="8c2c7-107">Dadurch wird eine optimale Benutzererfahrung sichergestellt, und Nachrichten werden ihren Benutzern nicht als Spam angezeigt.</span><span class="sxs-lookup"><span data-stu-id="8c2c7-107">This ensures an optimal experience and messages do not appear as spam to your users.</span></span>

<span data-ttu-id="8c2c7-108">Zum Schutz von Microsoft Teams und seinen Benutzern bieten die Bot-APIs eine Geschwindigkeitsbeschränkung für eingehende Anforderungen.</span><span class="sxs-lookup"><span data-stu-id="8c2c7-108">To protect Microsoft Teams and its users, the bot APIs provide a rate limit for incoming requests.</span></span> <span data-ttu-id="8c2c7-109">Apps, die diesen Grenzwert überschreiten, erhalten einen `HTTP 429 Too Many Requests` Fehlerstatus.</span><span class="sxs-lookup"><span data-stu-id="8c2c7-109">Apps that go over this limit receive an `HTTP 429 Too Many Requests` error status.</span></span> <span data-ttu-id="8c2c7-110">Alle Anforderungen unterliegen der gleichen Richtlinie zur Begrenzung der Rate, einschließlich des Sendens von Nachrichten, Kanalaufzählungen und Abrufen von Dienstplans.</span><span class="sxs-lookup"><span data-stu-id="8c2c7-110">All requests are subject to the same rate limiting policy, including sending messages, channel enumerations, and roster fetches.</span></span>

<span data-ttu-id="8c2c7-111">Da sich die genauen Werte der Zinsgrenzen ändern können, muss Ihre Anwendung das entsprechende Backoff-Verhalten implementieren, wenn die API `HTTP 429 Too Many Requests` zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="8c2c7-111">As the exact values of rate limits are subject to change, your application must implement the appropriate backoff behavior when the API returns `HTTP 429 Too Many Requests`.</span></span>

## <a name="handle-rate-limits"></a><span data-ttu-id="8c2c7-112">Behandeln von Satzbegrenzungen</span><span class="sxs-lookup"><span data-stu-id="8c2c7-112">Handle rate limits</span></span>

<span data-ttu-id="8c2c7-113">Beim Ausstellen eines Bot Builder-SDK-Vorgangs können Sie den Statuscode `Microsoft.Rest.HttpOperationException` behandeln und überprüfen.</span><span class="sxs-lookup"><span data-stu-id="8c2c7-113">When issuing a Bot Builder SDK operation, you can handle `Microsoft.Rest.HttpOperationException` and check for the status code.</span></span>

<span data-ttu-id="8c2c7-114">Der folgende Code zeigt ein Beispiel für die Behandlung von Geschwindigkeitsbeschränkungen:</span><span class="sxs-lookup"><span data-stu-id="8c2c7-114">The following code shows an example of handling rate limits:</span></span>

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

<span data-ttu-id="8c2c7-115">Nachdem Sie die Geschwindigkeitsbeschränkungen für Bots umgangen haben, können Sie Antworten mithilfe eines `HTTP 429` exponentiellen Backoffs behandeln.</span><span class="sxs-lookup"><span data-stu-id="8c2c7-115">After you handle rate limits for bots, you can handle `HTTP 429` responses using an exponential backoff.</span></span>

## <a name="handle-http-429-responses"></a><span data-ttu-id="8c2c7-116">Behandeln von `HTTP 429` Antworten</span><span class="sxs-lookup"><span data-stu-id="8c2c7-116">Handle `HTTP 429` responses</span></span>

<span data-ttu-id="8c2c7-117">Im Allgemeinen müssen Sie einfache Vorsichtsmaßnahmen ergreifen, um den Empfang von Antworten `HTTP 429` zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="8c2c7-117">In general, you must take simple precautions to avoid receiving `HTTP 429` responses.</span></span> <span data-ttu-id="8c2c7-118">Vermeiden Sie beispielsweise, mehrere Anforderungen an dieselbe persönliche Unterhaltung oder eine Kanal unterhaltung ausstellen.</span><span class="sxs-lookup"><span data-stu-id="8c2c7-118">For example, avoid issuing multiple requests to the same personal or channel conversation.</span></span> <span data-ttu-id="8c2c7-119">Erstellen Sie stattdessen einen Batch der API-Anforderungen.</span><span class="sxs-lookup"><span data-stu-id="8c2c7-119">Instead, create a batch of the API requests.</span></span>

<span data-ttu-id="8c2c7-120">Die Verwendung eines exponentiellen Backoffs mit einem zufälligen Jitter ist die empfohlene Methode zum Verarbeiten von 429s.</span><span class="sxs-lookup"><span data-stu-id="8c2c7-120">Using an exponential backoff with a random jitter is the recommended way to handle 429s.</span></span> <span data-ttu-id="8c2c7-121">Dadurch wird sichergestellt, dass bei Wiederholungsversuchen bei mehreren Anforderungen keine Kollisionen auftut.</span><span class="sxs-lookup"><span data-stu-id="8c2c7-121">This ensures that multiple requests do not introduce collisions on retries.</span></span>

<span data-ttu-id="8c2c7-122">Nachdem Sie Antworten behandeln, können Sie das Beispiel `HTTP 429` zum Erkennen vorübergehender Ausnahmen durchgehen.</span><span class="sxs-lookup"><span data-stu-id="8c2c7-122">After you handle `HTTP 429` responses, you can go through the example for detecting transient exceptions.</span></span>

## <a name="detect-transient-exceptions-example"></a><span data-ttu-id="8c2c7-123">Erkennen vorübergehender Ausnahmen (Beispiel)</span><span class="sxs-lookup"><span data-stu-id="8c2c7-123">Detect transient exceptions example</span></span>

<span data-ttu-id="8c2c7-124">Der folgende Code zeigt ein Beispiel für die Verwendung eines exponentiellen Backoffs mithilfe des Anwendungsblocks für die vorübergehende Fehlerbehandlung:</span><span class="sxs-lookup"><span data-stu-id="8c2c7-124">The following code shows an example of using exponential backoff using the transient fault handling application block:</span></span>

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

<span data-ttu-id="8c2c7-125">Sie können Backoff- und Wiederholungsversuche mithilfe der [vorübergehenden Fehlerbehandlung ausführen.](/previous-versions/msp-n-p/hh675232%28v%3dpandp.10%29)</span><span class="sxs-lookup"><span data-stu-id="8c2c7-125">You can perform backoff and retries using [transient fault handling](/previous-versions/msp-n-p/hh675232%28v%3dpandp.10%29).</span></span> <span data-ttu-id="8c2c7-126">Richtlinien zum Abrufen und Installieren des NuGet-Pakets finden Sie unter Hinzufügen des Anwendungsblocks für die vorübergehende [Fehlerbehandlung zu Ihrer Lösung.](/previous-versions/msp-n-p/dn440719(v=pandp.60)?redirectedfrom=MSDN)</span><span class="sxs-lookup"><span data-stu-id="8c2c7-126">For guidelines on obtaining and installing the NuGet package, see [adding the transient fault handling application block to your solution](/previous-versions/msp-n-p/dn440719(v=pandp.60)?redirectedfrom=MSDN).</span></span> <span data-ttu-id="8c2c7-127">Siehe auch [vorübergehende Fehlerbehandlung](/azure/architecture/best-practices/transient-faults).</span><span class="sxs-lookup"><span data-stu-id="8c2c7-127">See also [transient fault handling](/azure/architecture/best-practices/transient-faults).</span></span>

<span data-ttu-id="8c2c7-128">Nachdem Sie das Beispiel zum Erkennen vorübergehender Ausnahmen durchgehen, gehen Sie durch das exponentielle Backoff-Beispiel.</span><span class="sxs-lookup"><span data-stu-id="8c2c7-128">After you go through the example for detecting transient exceptions, go through the exponential backoff example.</span></span> <span data-ttu-id="8c2c7-129">Sie können exponentielles Backoff verwenden, anstatt Fehler erneut zu wiederholen.</span><span class="sxs-lookup"><span data-stu-id="8c2c7-129">You can use exponential backoff instead of retrying on failures.</span></span>

## <a name="backoff-example"></a><span data-ttu-id="8c2c7-130">Backoff-Beispiel</span><span class="sxs-lookup"><span data-stu-id="8c2c7-130">Backoff example</span></span>

<span data-ttu-id="8c2c7-131">Sie können nicht nur Geschwindigkeitsbegrenzungen erkennen, sondern auch ein exponentielles Backoff ausführen.</span><span class="sxs-lookup"><span data-stu-id="8c2c7-131">In addition to detecting rate limits, you can also perform an exponential backoff.</span></span>

<span data-ttu-id="8c2c7-132">Der folgende Code zeigt ein Beispiel für exponentielles Backoff:</span><span class="sxs-lookup"><span data-stu-id="8c2c7-132">The following code shows an example of exponential backoff:</span></span>

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

<span data-ttu-id="8c2c7-133">Sie können auch eine Methodenausführung mit der in diesem Abschnitt beschriebenen `System.Action` Wiederholungsrichtlinie ausführen.</span><span class="sxs-lookup"><span data-stu-id="8c2c7-133">You can also perform a `System.Action` method execution with the retry policy described in this section.</span></span> <span data-ttu-id="8c2c7-134">Mit der referenzierten Bibliothek können Sie auch ein festes Intervall oder einen linearen Backoffmechanismus angeben.</span><span class="sxs-lookup"><span data-stu-id="8c2c7-134">The referenced library also allows you to specify a fixed interval or a linear backoff mechanism.</span></span>

<span data-ttu-id="8c2c7-135">Speichern Sie den Wert und die Strategie in einer Konfigurationsdatei, um Werte zur Laufzeit zu optimieren und zu optimieren.</span><span class="sxs-lookup"><span data-stu-id="8c2c7-135">Store the value and strategy in a configuration file to fine-tune and tweak values at run time.</span></span>

<span data-ttu-id="8c2c7-136">Weitere Informationen finden Sie unter [Wiederholungsmuster](/azure/architecture/patterns/retry).</span><span class="sxs-lookup"><span data-stu-id="8c2c7-136">For more information, see [retry patterns](/azure/architecture/patterns/retry).</span></span>

<span data-ttu-id="8c2c7-137">Sie können auch die Geschwindigkeitsbegrenzung mithilfe der Pro-Bot-Pro-Thread-Grenze behandeln.</span><span class="sxs-lookup"><span data-stu-id="8c2c7-137">You can also handle rate limit using the per bot per thread limit.</span></span>

## <a name="per-bot-per-thread-limit"></a><span data-ttu-id="8c2c7-138">Pro Bot pro Threadgrenzwert</span><span class="sxs-lookup"><span data-stu-id="8c2c7-138">Per bot per thread limit</span></span>

>[!NOTE]
> <span data-ttu-id="8c2c7-139">Die Nachrichtenteilung auf Dienstebene führt zu höheren Anforderungen pro Sekunde (RPS).</span><span class="sxs-lookup"><span data-stu-id="8c2c7-139">Message splitting at the service level results in higher than expected requests per second (RPS).</span></span> <span data-ttu-id="8c2c7-140">Wenn Sie sich Sorgen machen, die Grenzwerte zu überschreiten, müssen Sie die [Backoff-Strategie implementieren.](#backoff-example)</span><span class="sxs-lookup"><span data-stu-id="8c2c7-140">If you are concerned about approaching the limits, you must implement the [backoff strategy](#backoff-example).</span></span> <span data-ttu-id="8c2c7-141">Die in diesem Abschnitt angegebenen Werte sind nur zur Schätzung vorgesehen.</span><span class="sxs-lookup"><span data-stu-id="8c2c7-141">The values provided in this section are for estimation only.</span></span>

<span data-ttu-id="8c2c7-142">Der Grenzwert pro Bot pro Thread steuert den Datenverkehr, den ein Bot für eine einzelne Unterhaltung generieren darf.</span><span class="sxs-lookup"><span data-stu-id="8c2c7-142">The per bot per thread limit controls the traffic that a bot is allowed to generate on a single conversation.</span></span> <span data-ttu-id="8c2c7-143">Eine Unterhaltung hier ist 1:1 zwischen Bot und Benutzer, einem Gruppenchat oder einem Kanal in einem Team.</span><span class="sxs-lookup"><span data-stu-id="8c2c7-143">A conversation here is 1:1 between bot and user, a group chat, or a channel in a team.</span></span>

<span data-ttu-id="8c2c7-144">In der folgenden Tabelle sind die Grenzwerte pro Bot pro Thread aufgeführt:</span><span class="sxs-lookup"><span data-stu-id="8c2c7-144">The following table provides the per bot per thread limits:</span></span>

| <span data-ttu-id="8c2c7-145">Szenario</span><span class="sxs-lookup"><span data-stu-id="8c2c7-145">Scenario</span></span> | <span data-ttu-id="8c2c7-146">Zeitraum in Sekunden</span><span class="sxs-lookup"><span data-stu-id="8c2c7-146">Time period in seconds</span></span> | <span data-ttu-id="8c2c7-147">Maximal zulässige Vorgänge</span><span class="sxs-lookup"><span data-stu-id="8c2c7-147">Maximum allowed operations</span></span> |
| --- | --- | --- |
| <span data-ttu-id="8c2c7-148">An Unterhaltung senden</span><span class="sxs-lookup"><span data-stu-id="8c2c7-148">Send to conversation</span></span> | <span data-ttu-id="8c2c7-149">1</span><span class="sxs-lookup"><span data-stu-id="8c2c7-149">1</span></span> | <span data-ttu-id="8c2c7-150">7 </span><span class="sxs-lookup"><span data-stu-id="8c2c7-150">7</span></span> |
| <span data-ttu-id="8c2c7-151">An Unterhaltung senden</span><span class="sxs-lookup"><span data-stu-id="8c2c7-151">Send to conversation</span></span> | <span data-ttu-id="8c2c7-152">2</span><span class="sxs-lookup"><span data-stu-id="8c2c7-152">2</span></span> | <span data-ttu-id="8c2c7-153">8 </span><span class="sxs-lookup"><span data-stu-id="8c2c7-153">8</span></span> |
| <span data-ttu-id="8c2c7-154">An Unterhaltung senden</span><span class="sxs-lookup"><span data-stu-id="8c2c7-154">Send to conversation</span></span> | <span data-ttu-id="8c2c7-155">30</span><span class="sxs-lookup"><span data-stu-id="8c2c7-155">30</span></span> | <span data-ttu-id="8c2c7-156">60</span><span class="sxs-lookup"><span data-stu-id="8c2c7-156">60</span></span> |
| <span data-ttu-id="8c2c7-157">An Unterhaltung senden</span><span class="sxs-lookup"><span data-stu-id="8c2c7-157">Send to conversation</span></span> | <span data-ttu-id="8c2c7-158">3600</span><span class="sxs-lookup"><span data-stu-id="8c2c7-158">3600</span></span> | <span data-ttu-id="8c2c7-159">1800</span><span class="sxs-lookup"><span data-stu-id="8c2c7-159">1800</span></span> |
| <span data-ttu-id="8c2c7-160">Unterhaltung erstellen</span><span class="sxs-lookup"><span data-stu-id="8c2c7-160">Create conversation</span></span> | <span data-ttu-id="8c2c7-161">1</span><span class="sxs-lookup"><span data-stu-id="8c2c7-161">1</span></span> | <span data-ttu-id="8c2c7-162">7 </span><span class="sxs-lookup"><span data-stu-id="8c2c7-162">7</span></span> |
| <span data-ttu-id="8c2c7-163">Unterhaltung erstellen</span><span class="sxs-lookup"><span data-stu-id="8c2c7-163">Create conversation</span></span> | <span data-ttu-id="8c2c7-164">2</span><span class="sxs-lookup"><span data-stu-id="8c2c7-164">2</span></span> | <span data-ttu-id="8c2c7-165">8 </span><span class="sxs-lookup"><span data-stu-id="8c2c7-165">8</span></span> |
| <span data-ttu-id="8c2c7-166">Unterhaltung erstellen</span><span class="sxs-lookup"><span data-stu-id="8c2c7-166">Create conversation</span></span> | <span data-ttu-id="8c2c7-167">30</span><span class="sxs-lookup"><span data-stu-id="8c2c7-167">30</span></span> | <span data-ttu-id="8c2c7-168">60</span><span class="sxs-lookup"><span data-stu-id="8c2c7-168">60</span></span> |
| <span data-ttu-id="8c2c7-169">Unterhaltung erstellen</span><span class="sxs-lookup"><span data-stu-id="8c2c7-169">Create conversation</span></span> | <span data-ttu-id="8c2c7-170">3600</span><span class="sxs-lookup"><span data-stu-id="8c2c7-170">3600</span></span> | <span data-ttu-id="8c2c7-171">1800</span><span class="sxs-lookup"><span data-stu-id="8c2c7-171">1800</span></span> |
| <span data-ttu-id="8c2c7-172">Unterhaltungsmitglieder erhalten</span><span class="sxs-lookup"><span data-stu-id="8c2c7-172">Get conversation members</span></span>| <span data-ttu-id="8c2c7-173">1</span><span class="sxs-lookup"><span data-stu-id="8c2c7-173">1</span></span> | <span data-ttu-id="8c2c7-174">14 </span><span class="sxs-lookup"><span data-stu-id="8c2c7-174">14</span></span> |
| <span data-ttu-id="8c2c7-175">Unterhaltungsmitglieder erhalten</span><span class="sxs-lookup"><span data-stu-id="8c2c7-175">Get conversation members</span></span>| <span data-ttu-id="8c2c7-176">2</span><span class="sxs-lookup"><span data-stu-id="8c2c7-176">2</span></span> | <span data-ttu-id="8c2c7-177">16 </span><span class="sxs-lookup"><span data-stu-id="8c2c7-177">16</span></span> |
| <span data-ttu-id="8c2c7-178">Unterhaltungsmitglieder erhalten</span><span class="sxs-lookup"><span data-stu-id="8c2c7-178">Get conversation members</span></span>| <span data-ttu-id="8c2c7-179">30</span><span class="sxs-lookup"><span data-stu-id="8c2c7-179">30</span></span> | <span data-ttu-id="8c2c7-180">120</span><span class="sxs-lookup"><span data-stu-id="8c2c7-180">120</span></span> |
| <span data-ttu-id="8c2c7-181">Unterhaltungsmitglieder erhalten</span><span class="sxs-lookup"><span data-stu-id="8c2c7-181">Get conversation members</span></span>| <span data-ttu-id="8c2c7-182">3600</span><span class="sxs-lookup"><span data-stu-id="8c2c7-182">3600</span></span> | <span data-ttu-id="8c2c7-183">3600</span><span class="sxs-lookup"><span data-stu-id="8c2c7-183">3600</span></span> |
| <span data-ttu-id="8c2c7-184">Unterhaltungen erhalten</span><span class="sxs-lookup"><span data-stu-id="8c2c7-184">Get conversations</span></span> | <span data-ttu-id="8c2c7-185">1</span><span class="sxs-lookup"><span data-stu-id="8c2c7-185">1</span></span> | <span data-ttu-id="8c2c7-186">14 </span><span class="sxs-lookup"><span data-stu-id="8c2c7-186">14</span></span> |
| <span data-ttu-id="8c2c7-187">Unterhaltungen erhalten</span><span class="sxs-lookup"><span data-stu-id="8c2c7-187">Get conversations</span></span> | <span data-ttu-id="8c2c7-188">2</span><span class="sxs-lookup"><span data-stu-id="8c2c7-188">2</span></span> | <span data-ttu-id="8c2c7-189">16 </span><span class="sxs-lookup"><span data-stu-id="8c2c7-189">16</span></span> |
| <span data-ttu-id="8c2c7-190">Unterhaltungen erhalten</span><span class="sxs-lookup"><span data-stu-id="8c2c7-190">Get conversations</span></span> | <span data-ttu-id="8c2c7-191">30</span><span class="sxs-lookup"><span data-stu-id="8c2c7-191">30</span></span> | <span data-ttu-id="8c2c7-192">120</span><span class="sxs-lookup"><span data-stu-id="8c2c7-192">120</span></span> |
| <span data-ttu-id="8c2c7-193">Unterhaltungen erhalten</span><span class="sxs-lookup"><span data-stu-id="8c2c7-193">Get conversations</span></span> | <span data-ttu-id="8c2c7-194">3600</span><span class="sxs-lookup"><span data-stu-id="8c2c7-194">3600</span></span> | <span data-ttu-id="8c2c7-195">3600</span><span class="sxs-lookup"><span data-stu-id="8c2c7-195">3600</span></span> |

>[!NOTE]
> <span data-ttu-id="8c2c7-196">Frühere Versionen `TeamsInfo.getMembers` von und `TeamsInfo.GetMembersAsync` APIs sind veraltet.</span><span class="sxs-lookup"><span data-stu-id="8c2c7-196">Previous versions of `TeamsInfo.getMembers` and `TeamsInfo.GetMembersAsync` APIs are being deprecated.</span></span> <span data-ttu-id="8c2c7-197">Sie werden auf fünf Anforderungen pro Minute gedrosselt und geben maximal 10.000 Mitglieder pro Team zurück.</span><span class="sxs-lookup"><span data-stu-id="8c2c7-197">They are throttled to five requests per minute and return a maximum of 10K members per team.</span></span> <span data-ttu-id="8c2c7-198">Informationen zum Aktualisieren Ihres Bot Framework SDK und des Codes zur Verwendung der neuesten paginierten API-Endpunkte finden Sie unter [Bot-API-Änderungen für Team- und Chatmitglieder.](../../resources/team-chat-member-api-changes.md)</span><span class="sxs-lookup"><span data-stu-id="8c2c7-198">To update your Bot Framework SDK and the code to use the latest paginated API endpoints, see [Bot API changes for team and chat members](../../resources/team-chat-member-api-changes.md).</span></span>

<span data-ttu-id="8c2c7-199">Sie können die Geschwindigkeitsbegrenzung auch mithilfe des Pro-Thread-Grenzwerts für alle Bots behandeln.</span><span class="sxs-lookup"><span data-stu-id="8c2c7-199">You can also handle rate limit using the per thread limit for all bots.</span></span>

## <a name="per-thread-limit-for-all-bots"></a><span data-ttu-id="8c2c7-200">Grenzwert pro Thread für alle Bots</span><span class="sxs-lookup"><span data-stu-id="8c2c7-200">Per thread limit for all bots</span></span>

<span data-ttu-id="8c2c7-201">Der Grenzwert pro Thread für alle Bots steuert den Datenverkehr, den alle Bots über eine einzelne Unterhaltung generieren dürfen.</span><span class="sxs-lookup"><span data-stu-id="8c2c7-201">The per thread limit for all bots controls the traffic that all bots are allowed to generate across a single conversation.</span></span> <span data-ttu-id="8c2c7-202">Eine Unterhaltung hier ist 1:1 zwischen Bot und Benutzer, einem Gruppenchat oder einem Kanal in einem Team.</span><span class="sxs-lookup"><span data-stu-id="8c2c7-202">A conversation here is 1:1 between bot and user, a group chat, or a channel in a team.</span></span>

<span data-ttu-id="8c2c7-203">In der folgenden Tabelle ist der Grenzwert pro Thread für alle Bots aufgeführt:</span><span class="sxs-lookup"><span data-stu-id="8c2c7-203">The following table provides the per thread limit for all bots:</span></span>

| <span data-ttu-id="8c2c7-204">Szenario</span><span class="sxs-lookup"><span data-stu-id="8c2c7-204">Scenario</span></span> | <span data-ttu-id="8c2c7-205">Zeitraum in Sekunden</span><span class="sxs-lookup"><span data-stu-id="8c2c7-205">Time period in seconds</span></span> | <span data-ttu-id="8c2c7-206">Maximal zulässige Vorgänge</span><span class="sxs-lookup"><span data-stu-id="8c2c7-206">Maximum allowed operations</span></span> |
| --- | --- | --- |
| <span data-ttu-id="8c2c7-207">An Unterhaltung senden</span><span class="sxs-lookup"><span data-stu-id="8c2c7-207">Send to conversation</span></span> | <span data-ttu-id="8c2c7-208">1</span><span class="sxs-lookup"><span data-stu-id="8c2c7-208">1</span></span> | <span data-ttu-id="8c2c7-209">14 </span><span class="sxs-lookup"><span data-stu-id="8c2c7-209">14</span></span> |
| <span data-ttu-id="8c2c7-210">An Unterhaltung senden</span><span class="sxs-lookup"><span data-stu-id="8c2c7-210">Send to conversation</span></span> | <span data-ttu-id="8c2c7-211">2</span><span class="sxs-lookup"><span data-stu-id="8c2c7-211">2</span></span> | <span data-ttu-id="8c2c7-212">16 </span><span class="sxs-lookup"><span data-stu-id="8c2c7-212">16</span></span> |
| <span data-ttu-id="8c2c7-213">Unterhaltung erstellen</span><span class="sxs-lookup"><span data-stu-id="8c2c7-213">Create conversation</span></span> | <span data-ttu-id="8c2c7-214">1</span><span class="sxs-lookup"><span data-stu-id="8c2c7-214">1</span></span> | <span data-ttu-id="8c2c7-215">14 </span><span class="sxs-lookup"><span data-stu-id="8c2c7-215">14</span></span> |
| <span data-ttu-id="8c2c7-216">Unterhaltung erstellen</span><span class="sxs-lookup"><span data-stu-id="8c2c7-216">Create conversation</span></span> | <span data-ttu-id="8c2c7-217">2</span><span class="sxs-lookup"><span data-stu-id="8c2c7-217">2</span></span> | <span data-ttu-id="8c2c7-218">16 </span><span class="sxs-lookup"><span data-stu-id="8c2c7-218">16</span></span> |
| <span data-ttu-id="8c2c7-219">Unterhaltung erstellen</span><span class="sxs-lookup"><span data-stu-id="8c2c7-219">Create conversation</span></span>| <span data-ttu-id="8c2c7-220">1</span><span class="sxs-lookup"><span data-stu-id="8c2c7-220">1</span></span> | <span data-ttu-id="8c2c7-221">14 </span><span class="sxs-lookup"><span data-stu-id="8c2c7-221">14</span></span> |
| <span data-ttu-id="8c2c7-222">Unterhaltung erstellen</span><span class="sxs-lookup"><span data-stu-id="8c2c7-222">Create conversation</span></span>| <span data-ttu-id="8c2c7-223">2</span><span class="sxs-lookup"><span data-stu-id="8c2c7-223">2</span></span> | <span data-ttu-id="8c2c7-224">16 </span><span class="sxs-lookup"><span data-stu-id="8c2c7-224">16</span></span> |
| <span data-ttu-id="8c2c7-225">Unterhaltungsmitglieder erhalten</span><span class="sxs-lookup"><span data-stu-id="8c2c7-225">Get conversation members</span></span>| <span data-ttu-id="8c2c7-226">1</span><span class="sxs-lookup"><span data-stu-id="8c2c7-226">1</span></span> | <span data-ttu-id="8c2c7-227">28</span><span class="sxs-lookup"><span data-stu-id="8c2c7-227">28</span></span> |
| <span data-ttu-id="8c2c7-228">Unterhaltungsmitglieder erhalten</span><span class="sxs-lookup"><span data-stu-id="8c2c7-228">Get conversation members</span></span>| <span data-ttu-id="8c2c7-229">2</span><span class="sxs-lookup"><span data-stu-id="8c2c7-229">2</span></span> | <span data-ttu-id="8c2c7-230">32</span><span class="sxs-lookup"><span data-stu-id="8c2c7-230">32</span></span> |
| <span data-ttu-id="8c2c7-231">Unterhaltungen erhalten</span><span class="sxs-lookup"><span data-stu-id="8c2c7-231">Get conversations</span></span> | <span data-ttu-id="8c2c7-232">1</span><span class="sxs-lookup"><span data-stu-id="8c2c7-232">1</span></span> | <span data-ttu-id="8c2c7-233">28</span><span class="sxs-lookup"><span data-stu-id="8c2c7-233">28</span></span> |
| <span data-ttu-id="8c2c7-234">Unterhaltungen erhalten</span><span class="sxs-lookup"><span data-stu-id="8c2c7-234">Get conversations</span></span> | <span data-ttu-id="8c2c7-235">2</span><span class="sxs-lookup"><span data-stu-id="8c2c7-235">2</span></span> | <span data-ttu-id="8c2c7-236">32</span><span class="sxs-lookup"><span data-stu-id="8c2c7-236">32</span></span> |

## <a name="next-step"></a><span data-ttu-id="8c2c7-237">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="8c2c7-237">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="8c2c7-238">Anrufe und Besprechungsbots</span><span class="sxs-lookup"><span data-stu-id="8c2c7-238">Calls and meetings bots</span></span>](~/bots/calls-and-meetings/calls-meetings-bots-overview.md)

