---
title: Ratenbegrenzung
description: Ratenbegrenzung und bewährte Methoden in Microsoft Teams
keywords: Teams Bots Ratenbegrenzung
ms.openlocfilehash: 9b244053d42aaddaf48c798e401438b614b0e1bd
ms.sourcegitcommit: 61edf47c9dd1dbc1df03d0d9fb83bfedca4c423b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/28/2020
ms.locfileid: "44801315"
---
# <a name="optimize-your-bot-rate-limiting-and-best-practices-in-microsoft-teams"></a><span data-ttu-id="1c48e-104">Optimieren Ihres bot: Ratenbegrenzung und bewährte Methoden in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="1c48e-104">Optimize your bot: rate limiting and best practices in Microsoft Teams</span></span>

<span data-ttu-id="1c48e-105">Als allgemeiner Grundsatz sollte Ihre Anwendung die Anzahl der Nachrichten begrenzen, die Sie an eine einzelne Chat-oder Kanal Unterhaltung sendet.</span><span class="sxs-lookup"><span data-stu-id="1c48e-105">As a general principle, your application should limit the number of messages it posts to an individual chat or channel conversation.</span></span> <span data-ttu-id="1c48e-106">Dadurch wird eine optimale Oberfläche gewährleistet, bei der die Endbenutzer nicht "spammy" empfinden.</span><span class="sxs-lookup"><span data-stu-id="1c48e-106">This ensures an optimal experience that doesn't feel “spammy” to your end users.</span></span>

<span data-ttu-id="1c48e-107">Um Microsoft Teams und seine Benutzer zu schützen, begrenzen die bot-APIs eingehende Anforderungen.</span><span class="sxs-lookup"><span data-stu-id="1c48e-107">To protect Microsoft Teams and its users, the bot APIs rate-limit incoming requests.</span></span> <span data-ttu-id="1c48e-108">Apps, die diesen Grenzwert überschreiten, erhalten einen `HTTP 429 Too Many Requests` Fehlerstatus.</span><span class="sxs-lookup"><span data-stu-id="1c48e-108">Apps that go over this limit receive an `HTTP 429 Too Many Requests` error status.</span></span> <span data-ttu-id="1c48e-109">Alle Anforderungen unterliegen der gleichen Richtlinie zur Ratenbegrenzung, einschließlich Senden von Nachrichten, Kanal Aufzählungen und Dienstplan abrufen.</span><span class="sxs-lookup"><span data-stu-id="1c48e-109">All requests are subject to the same rate-limiting policy, including sending messages, channel enumerations, and roster fetches.</span></span>

<span data-ttu-id="1c48e-110">Da die genauen Werte von Raten Grenzwerten geändert werden können, wird empfohlen, dass Ihre Anwendung das entsprechende Backoff-Verhalten implementiert, wenn die API zurückgegeben wird `HTTP 429 Too Many Requests` .</span><span class="sxs-lookup"><span data-stu-id="1c48e-110">Because the exact values of rate limits are subject to change, we recommend your application implement the appropriate backoff behavior when the API returns `HTTP 429 Too Many Requests`.</span></span>

## <a name="handling-rate-limits"></a><span data-ttu-id="1c48e-111">Grenzwerte für die Handhabungs Rate</span><span class="sxs-lookup"><span data-stu-id="1c48e-111">Handling rate limits</span></span>

<span data-ttu-id="1c48e-112">Beim Ausgeben eines bot-Generator-SDK-Vorgangs können Sie `Microsoft.Rest.HttpOperationException` den Statuscode verarbeiten und überprüfen.</span><span class="sxs-lookup"><span data-stu-id="1c48e-112">When issuing a Bot Builder SDK operation, you can handle `Microsoft.Rest.HttpOperationException` and check for the status code.</span></span>

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

## <a name="best-practices"></a><span data-ttu-id="1c48e-113">Bewährte Methoden</span><span class="sxs-lookup"><span data-stu-id="1c48e-113">Best practices</span></span>

<span data-ttu-id="1c48e-114">Im Allgemeinen sollten Sie einfache Vorkehrungen treffen, um den Empfang von Antworten zu vermeiden `HTTP 429` .</span><span class="sxs-lookup"><span data-stu-id="1c48e-114">In general, you should take simple precautions to avoid receiving `HTTP 429` responses.</span></span> <span data-ttu-id="1c48e-115">Vermeiden Sie beispielsweise das ausgeben mehrerer Anforderungen an dieselbe persönliche oder Kanal Unterhaltung.</span><span class="sxs-lookup"><span data-stu-id="1c48e-115">For instance, avoid issuing multiple requests to the same personal or channel conversation.</span></span> <span data-ttu-id="1c48e-116">Verwenden Sie stattdessen die Batchverarbeitung der API-Anforderungen.</span><span class="sxs-lookup"><span data-stu-id="1c48e-116">Instead, consider batching the API requests.</span></span>

<span data-ttu-id="1c48e-117">Das Verwenden einer exponentiellen Backoff mit einem willkürlichen Jitter ist die empfohlene Vorgehensweise zum Behandeln von 429er.</span><span class="sxs-lookup"><span data-stu-id="1c48e-117">Using an exponential backoff with a random jitter is the recommended way to handle 429s.</span></span> <span data-ttu-id="1c48e-118">Dadurch wird sichergestellt, dass mehrere Anforderungen keine Kollisionen bei Wiederholungsversuchen einführen.</span><span class="sxs-lookup"><span data-stu-id="1c48e-118">This ensures that multiple requests don't introduce collisions on retries.</span></span>

## <a name="example-detecting-transient-exceptions"></a><span data-ttu-id="1c48e-119">Beispiel: Erkennen von vorübergehenden Ausnahmen</span><span class="sxs-lookup"><span data-stu-id="1c48e-119">Example: detecting transient exceptions</span></span>

<span data-ttu-id="1c48e-120">Im folgenden finden Sie ein Beispiel für die Verwendung eines exponentiellen Backoff über den Anwendungs Block der transienten Fehlerbehandlung.</span><span class="sxs-lookup"><span data-stu-id="1c48e-120">Here is a sample using exponential backoff via the Transient Fault Handling Application Block.</span></span>

<span data-ttu-id="1c48e-121">Sie können Backoff und Wiederholungsversuche mit [vorübergehender Fehlerbehandlung](/previous-versions/msp-n-p/hh675232%28v%3dpandp.10%29)durchführen.</span><span class="sxs-lookup"><span data-stu-id="1c48e-121">You can perform backoff and retries using [Transient Fault Handling](/previous-versions/msp-n-p/hh675232%28v%3dpandp.10%29).</span></span> <span data-ttu-id="1c48e-122">Richtlinien zum beziehen und Installieren des NuGet-Pakets finden Sie unter [Hinzufügen des Anwendungsblocks der vorübergehenden Fehlerbehandlung zu Ihrer Lösung](/previous-versions/msp-n-p/dn440719(v=pandp.60)?redirectedfrom=MSDN)).</span><span class="sxs-lookup"><span data-stu-id="1c48e-122">For guidelines on obtaining and installing the NuGet package, see [Adding the Transient Fault Handling Application Block to Your Solution](/previous-versions/msp-n-p/dn440719(v=pandp.60)?redirectedfrom=MSDN)).</span></span> <span data-ttu-id="1c48e-123">*Siehe auch* [transient Fault Handling](/azure/architecture/best-practices/transient-faults).</span><span class="sxs-lookup"><span data-stu-id="1c48e-123">*See also* [Transient fault handling](/azure/architecture/best-practices/transient-faults).</span></span>

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

## <a name="example-backoff"></a><span data-ttu-id="1c48e-124">Beispiel: Backoff</span><span class="sxs-lookup"><span data-stu-id="1c48e-124">Example: backoff</span></span>

<span data-ttu-id="1c48e-125">Zusätzlich zur Ermittlung von Raten Grenzwerten können Sie auch eine exponentielle Backoff ausführen.</span><span class="sxs-lookup"><span data-stu-id="1c48e-125">In addition to detecting rate limits, you can also perform an exponential backoff.</span></span>

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

<span data-ttu-id="1c48e-126">Sie können auch eine `System.Action` Methodenausführung mit der oben beschriebenen Wiederholungs Richtlinie ausführen.</span><span class="sxs-lookup"><span data-stu-id="1c48e-126">You can also perform a `System.Action` method execution with the retry policy described above.</span></span> <span data-ttu-id="1c48e-127">Mit der referenzierten Bibliothek können Sie auch ein festes Intervall oder einen linearen Backoff-Mechanismus angeben.</span><span class="sxs-lookup"><span data-stu-id="1c48e-127">The referenced library also allows you to specify a fixed interval or a linear backoff mechanism.</span></span>

<span data-ttu-id="1c48e-128">Es wird empfohlen, den Wert und die Strategie in einer Konfigurationsdatei zu speichern, um Werte zur Laufzeit zu optimieren und zu optimieren.</span><span class="sxs-lookup"><span data-stu-id="1c48e-128">We recommend storing the value and strategy in a configuration file to fine-tune and tweak values at run time.</span></span>

<span data-ttu-id="1c48e-129">Weitere Informationen finden Sie in diesem handlichen Leitfaden für verschiedene Wiederholungsmuster: [Wiederholungsmuster](/azure/architecture/patterns/retry).</span><span class="sxs-lookup"><span data-stu-id="1c48e-129">For more information, check out this handy guide on various retry patterns: [Retry pattern](/azure/architecture/patterns/retry).</span></span>

## <a name="per-bot-per-thread-limit"></a><span data-ttu-id="1c48e-130">Pro bot pro Thread-Grenzwert</span><span class="sxs-lookup"><span data-stu-id="1c48e-130">Per bot per thread limit</span></span>

>[!NOTE]
><span data-ttu-id="1c48e-131">Die Nachrichten Aufteilung auf Dienstebene führt zu höheren als erwarteten Anforderungen pro Sekunde (RPS).</span><span class="sxs-lookup"><span data-stu-id="1c48e-131">Message splitting at the service level will result in higher than expected requests per second (RPS).</span></span> <span data-ttu-id="1c48e-132">Wenn Sie Bedenken haben, sich an die Grenzwerte zu wenden, sollten Sie die oben beschriebene Backoff-Strategie implementieren.</span><span class="sxs-lookup"><span data-stu-id="1c48e-132">If you're concerned about approaching the limits, you should implement the backoff strategy described above.</span></span> <span data-ttu-id="1c48e-133">Die unten angegebenen Werte dienen nur der Schätzung.</span><span class="sxs-lookup"><span data-stu-id="1c48e-133">The values provided below are for estimation only.</span></span>

<span data-ttu-id="1c48e-134">Dieser Grenzwert steuert den Datenverkehr, den ein bot für eine einzelne Unterhaltung generieren darf.</span><span class="sxs-lookup"><span data-stu-id="1c48e-134">This limit controls the traffic that a bot is allowed to generate on a single conversation.</span></span> <span data-ttu-id="1c48e-135">Eine Unterhaltung ist 1:1 zwischen bot und Benutzer, einem Gruppenchat oder einem Kanal in einem Team.</span><span class="sxs-lookup"><span data-stu-id="1c48e-135">A conversation here is 1:1 between bot and user, a group-chat, or a channel in a team.</span></span>

| <span data-ttu-id="1c48e-136">**Szenario**</span><span class="sxs-lookup"><span data-stu-id="1c48e-136">**Scenario**</span></span> | <span data-ttu-id="1c48e-137">**Zeitraum (Sek.)**</span><span class="sxs-lookup"><span data-stu-id="1c48e-137">**Time-period (sec)**</span></span> | <span data-ttu-id="1c48e-138">**Max. zulässige Vorgänge**</span><span class="sxs-lookup"><span data-stu-id="1c48e-138">**Max allowed operations**</span></span> |
| --- | --- | --- |
| <span data-ttu-id="1c48e-139">An Unterhaltung senden</span><span class="sxs-lookup"><span data-stu-id="1c48e-139">Send to Conversation</span></span> | <span data-ttu-id="1c48e-140">1 </span><span class="sxs-lookup"><span data-stu-id="1c48e-140">1</span></span> | <span data-ttu-id="1c48e-141">7 </span><span class="sxs-lookup"><span data-stu-id="1c48e-141">7</span></span> |
| <span data-ttu-id="1c48e-142">An Unterhaltung senden</span><span class="sxs-lookup"><span data-stu-id="1c48e-142">Send to Conversation</span></span> | <span data-ttu-id="1c48e-143">2</span><span class="sxs-lookup"><span data-stu-id="1c48e-143">2</span></span> | <span data-ttu-id="1c48e-144">8 </span><span class="sxs-lookup"><span data-stu-id="1c48e-144">8</span></span> |
| <span data-ttu-id="1c48e-145">An Unterhaltung senden</span><span class="sxs-lookup"><span data-stu-id="1c48e-145">Send to Conversation</span></span> | <span data-ttu-id="1c48e-146">30</span><span class="sxs-lookup"><span data-stu-id="1c48e-146">30</span></span> | <span data-ttu-id="1c48e-147">60</span><span class="sxs-lookup"><span data-stu-id="1c48e-147">60</span></span> |
| <span data-ttu-id="1c48e-148">An Unterhaltung senden</span><span class="sxs-lookup"><span data-stu-id="1c48e-148">Send to Conversation</span></span> | <span data-ttu-id="1c48e-149">3600</span><span class="sxs-lookup"><span data-stu-id="1c48e-149">3600</span></span> | <span data-ttu-id="1c48e-150">1800</span><span class="sxs-lookup"><span data-stu-id="1c48e-150">1800</span></span> |
| <span data-ttu-id="1c48e-151">Unterhaltung erstellen</span><span class="sxs-lookup"><span data-stu-id="1c48e-151">Create Conversation</span></span> | <span data-ttu-id="1c48e-152">1 </span><span class="sxs-lookup"><span data-stu-id="1c48e-152">1</span></span> | <span data-ttu-id="1c48e-153">7 </span><span class="sxs-lookup"><span data-stu-id="1c48e-153">7</span></span> |
| <span data-ttu-id="1c48e-154">Unterhaltung erstellen</span><span class="sxs-lookup"><span data-stu-id="1c48e-154">Create Conversation</span></span> | <span data-ttu-id="1c48e-155">2</span><span class="sxs-lookup"><span data-stu-id="1c48e-155">2</span></span> | <span data-ttu-id="1c48e-156">8 </span><span class="sxs-lookup"><span data-stu-id="1c48e-156">8</span></span> |
| <span data-ttu-id="1c48e-157">Unterhaltung erstellen</span><span class="sxs-lookup"><span data-stu-id="1c48e-157">Create Conversation</span></span> | <span data-ttu-id="1c48e-158">30</span><span class="sxs-lookup"><span data-stu-id="1c48e-158">30</span></span> | <span data-ttu-id="1c48e-159">60</span><span class="sxs-lookup"><span data-stu-id="1c48e-159">60</span></span> |
| <span data-ttu-id="1c48e-160">Unterhaltung erstellen</span><span class="sxs-lookup"><span data-stu-id="1c48e-160">Create Conversation</span></span> | <span data-ttu-id="1c48e-161">3600</span><span class="sxs-lookup"><span data-stu-id="1c48e-161">3600</span></span> | <span data-ttu-id="1c48e-162">1800</span><span class="sxs-lookup"><span data-stu-id="1c48e-162">1800</span></span> |
| <span data-ttu-id="1c48e-163">Abrufen von Unterhaltungs Mitgliedern</span><span class="sxs-lookup"><span data-stu-id="1c48e-163">Get Conversation Members</span></span>| <span data-ttu-id="1c48e-164">1 </span><span class="sxs-lookup"><span data-stu-id="1c48e-164">1</span></span> | <span data-ttu-id="1c48e-165">14 </span><span class="sxs-lookup"><span data-stu-id="1c48e-165">14</span></span> |
| <span data-ttu-id="1c48e-166">Abrufen von Unterhaltungs Mitgliedern</span><span class="sxs-lookup"><span data-stu-id="1c48e-166">Get Conversation Members</span></span>| <span data-ttu-id="1c48e-167">2</span><span class="sxs-lookup"><span data-stu-id="1c48e-167">2</span></span> | <span data-ttu-id="1c48e-168">16 </span><span class="sxs-lookup"><span data-stu-id="1c48e-168">16</span></span> |
| <span data-ttu-id="1c48e-169">Abrufen von Unterhaltungs Mitgliedern</span><span class="sxs-lookup"><span data-stu-id="1c48e-169">Get Conversation Members</span></span>| <span data-ttu-id="1c48e-170">30</span><span class="sxs-lookup"><span data-stu-id="1c48e-170">30</span></span> | <span data-ttu-id="1c48e-171">120</span><span class="sxs-lookup"><span data-stu-id="1c48e-171">120</span></span> |
| <span data-ttu-id="1c48e-172">Abrufen von Unterhaltungs Mitgliedern</span><span class="sxs-lookup"><span data-stu-id="1c48e-172">Get Conversation Members</span></span>| <span data-ttu-id="1c48e-173">3600</span><span class="sxs-lookup"><span data-stu-id="1c48e-173">3600</span></span> | <span data-ttu-id="1c48e-174">3600</span><span class="sxs-lookup"><span data-stu-id="1c48e-174">3600</span></span> |
| <span data-ttu-id="1c48e-175">Unterhaltungen abrufen</span><span class="sxs-lookup"><span data-stu-id="1c48e-175">Get Conversations</span></span> | <span data-ttu-id="1c48e-176">1 </span><span class="sxs-lookup"><span data-stu-id="1c48e-176">1</span></span> | <span data-ttu-id="1c48e-177">14 </span><span class="sxs-lookup"><span data-stu-id="1c48e-177">14</span></span> |
| <span data-ttu-id="1c48e-178">Unterhaltungen abrufen</span><span class="sxs-lookup"><span data-stu-id="1c48e-178">Get Conversations</span></span> | <span data-ttu-id="1c48e-179">2</span><span class="sxs-lookup"><span data-stu-id="1c48e-179">2</span></span> | <span data-ttu-id="1c48e-180">16 </span><span class="sxs-lookup"><span data-stu-id="1c48e-180">16</span></span> |
| <span data-ttu-id="1c48e-181">Unterhaltungen abrufen</span><span class="sxs-lookup"><span data-stu-id="1c48e-181">Get Conversations</span></span> | <span data-ttu-id="1c48e-182">30</span><span class="sxs-lookup"><span data-stu-id="1c48e-182">30</span></span> | <span data-ttu-id="1c48e-183">120</span><span class="sxs-lookup"><span data-stu-id="1c48e-183">120</span></span> |
| <span data-ttu-id="1c48e-184">Unterhaltungen abrufen</span><span class="sxs-lookup"><span data-stu-id="1c48e-184">Get Conversations</span></span> | <span data-ttu-id="1c48e-185">3600</span><span class="sxs-lookup"><span data-stu-id="1c48e-185">3600</span></span> | <span data-ttu-id="1c48e-186">3600</span><span class="sxs-lookup"><span data-stu-id="1c48e-186">3600</span></span> |

## <a name="per-thread-limit-for-all-bots"></a><span data-ttu-id="1c48e-187">Grenzwert pro Thread für alle Bots</span><span class="sxs-lookup"><span data-stu-id="1c48e-187">Per thread limit for all bots</span></span>

<span data-ttu-id="1c48e-188">Dieser Grenzwert steuert den Datenverkehr, den alle Bots in einer einzigen Unterhaltung generieren dürfen.</span><span class="sxs-lookup"><span data-stu-id="1c48e-188">This limit controls the traffic that all bots are allowed to generate across a single conversation.</span></span> <span data-ttu-id="1c48e-189">Eine Unterhaltung ist 1:1 zwischen bot und Benutzer, einem Gruppenchat oder einem Kanal in einem Team.</span><span class="sxs-lookup"><span data-stu-id="1c48e-189">A conversation here is 1:1 between bot and user, a group-chat, or a channel in a team.</span></span>

| <span data-ttu-id="1c48e-190">**Szenario**</span><span class="sxs-lookup"><span data-stu-id="1c48e-190">**Scenario**</span></span> | <span data-ttu-id="1c48e-191">**Zeitraum (Sek.)**</span><span class="sxs-lookup"><span data-stu-id="1c48e-191">**Time-period (sec)**</span></span> | <span data-ttu-id="1c48e-192">**Max. zulässige Vorgänge**</span><span class="sxs-lookup"><span data-stu-id="1c48e-192">**Max allowed operations**</span></span> |
| --- | --- | --- |
| <span data-ttu-id="1c48e-193">An Unterhaltung senden</span><span class="sxs-lookup"><span data-stu-id="1c48e-193">Send to Conversation</span></span> | <span data-ttu-id="1c48e-194">1 </span><span class="sxs-lookup"><span data-stu-id="1c48e-194">1</span></span> | <span data-ttu-id="1c48e-195">14 </span><span class="sxs-lookup"><span data-stu-id="1c48e-195">14</span></span> |
| <span data-ttu-id="1c48e-196">An Unterhaltung senden</span><span class="sxs-lookup"><span data-stu-id="1c48e-196">Send to Conversation</span></span> | <span data-ttu-id="1c48e-197">2</span><span class="sxs-lookup"><span data-stu-id="1c48e-197">2</span></span> | <span data-ttu-id="1c48e-198">16 </span><span class="sxs-lookup"><span data-stu-id="1c48e-198">16</span></span> |
| <span data-ttu-id="1c48e-199">Unterhaltung erstellen</span><span class="sxs-lookup"><span data-stu-id="1c48e-199">Create Conversation</span></span> | <span data-ttu-id="1c48e-200">1 </span><span class="sxs-lookup"><span data-stu-id="1c48e-200">1</span></span> | <span data-ttu-id="1c48e-201">14 </span><span class="sxs-lookup"><span data-stu-id="1c48e-201">14</span></span> |
| <span data-ttu-id="1c48e-202">Unterhaltung erstellen</span><span class="sxs-lookup"><span data-stu-id="1c48e-202">Create Conversation</span></span> | <span data-ttu-id="1c48e-203">2</span><span class="sxs-lookup"><span data-stu-id="1c48e-203">2</span></span> | <span data-ttu-id="1c48e-204">16 </span><span class="sxs-lookup"><span data-stu-id="1c48e-204">16</span></span> |
| <span data-ttu-id="1c48e-205">Createconversation</span><span class="sxs-lookup"><span data-stu-id="1c48e-205">CreateConversation</span></span>| <span data-ttu-id="1c48e-206">1 </span><span class="sxs-lookup"><span data-stu-id="1c48e-206">1</span></span> | <span data-ttu-id="1c48e-207">14 </span><span class="sxs-lookup"><span data-stu-id="1c48e-207">14</span></span> |
| <span data-ttu-id="1c48e-208">Createconversation</span><span class="sxs-lookup"><span data-stu-id="1c48e-208">CreateConversation</span></span>| <span data-ttu-id="1c48e-209">2</span><span class="sxs-lookup"><span data-stu-id="1c48e-209">2</span></span> | <span data-ttu-id="1c48e-210">16 </span><span class="sxs-lookup"><span data-stu-id="1c48e-210">16</span></span> |
| <span data-ttu-id="1c48e-211">Abrufen von Unterhaltungs Mitgliedern</span><span class="sxs-lookup"><span data-stu-id="1c48e-211">Get Conversation Members</span></span>| <span data-ttu-id="1c48e-212">1 </span><span class="sxs-lookup"><span data-stu-id="1c48e-212">1</span></span> | <span data-ttu-id="1c48e-213">28</span><span class="sxs-lookup"><span data-stu-id="1c48e-213">28</span></span> |
| <span data-ttu-id="1c48e-214">Abrufen von Unterhaltungs Mitgliedern</span><span class="sxs-lookup"><span data-stu-id="1c48e-214">Get Conversation Members</span></span>| <span data-ttu-id="1c48e-215">2</span><span class="sxs-lookup"><span data-stu-id="1c48e-215">2</span></span> | <span data-ttu-id="1c48e-216">32</span><span class="sxs-lookup"><span data-stu-id="1c48e-216">32</span></span> |
| <span data-ttu-id="1c48e-217">Unterhaltungen abrufen</span><span class="sxs-lookup"><span data-stu-id="1c48e-217">Get Conversations</span></span> | <span data-ttu-id="1c48e-218">1 </span><span class="sxs-lookup"><span data-stu-id="1c48e-218">1</span></span> | <span data-ttu-id="1c48e-219">28</span><span class="sxs-lookup"><span data-stu-id="1c48e-219">28</span></span> |
| <span data-ttu-id="1c48e-220">Unterhaltungen abrufen</span><span class="sxs-lookup"><span data-stu-id="1c48e-220">Get Conversations</span></span> | <span data-ttu-id="1c48e-221">2</span><span class="sxs-lookup"><span data-stu-id="1c48e-221">2</span></span> | <span data-ttu-id="1c48e-222">32</span><span class="sxs-lookup"><span data-stu-id="1c48e-222">32</span></span> |

## <a name="bot-per-data-center-limit"></a><span data-ttu-id="1c48e-223">Bot pro Rechenzentrums Grenze</span><span class="sxs-lookup"><span data-stu-id="1c48e-223">Bot per data center limit</span></span>

<span data-ttu-id="1c48e-224">Dieser Grenzwert steuert den Datenverkehr, den ein bot in allen Threads in einem Rechenzentrum (in mehreren Mandanten) generieren darf.</span><span class="sxs-lookup"><span data-stu-id="1c48e-224">This limit controls the traffic that a bot is allowed to generate across all threads in a data center (across multiple tenants).</span></span>

|<span data-ttu-id="1c48e-225">**Zeitraum (Sek.)**</span><span class="sxs-lookup"><span data-stu-id="1c48e-225">**Time-period (sec)**</span></span> | <span data-ttu-id="1c48e-226">**Max. zulässige Vorgänge**</span><span class="sxs-lookup"><span data-stu-id="1c48e-226">**Max allowed operations**</span></span> |
| --- | --- |
| <span data-ttu-id="1c48e-227">1 </span><span class="sxs-lookup"><span data-stu-id="1c48e-227">1</span></span> | <span data-ttu-id="1c48e-228">20</span><span class="sxs-lookup"><span data-stu-id="1c48e-228">20</span></span> |
| <span data-ttu-id="1c48e-229">1800</span><span class="sxs-lookup"><span data-stu-id="1c48e-229">1800</span></span> | <span data-ttu-id="1c48e-230">8000</span><span class="sxs-lookup"><span data-stu-id="1c48e-230">8000</span></span> |
| <span data-ttu-id="1c48e-231">3600</span><span class="sxs-lookup"><span data-stu-id="1c48e-231">3600</span></span> | <span data-ttu-id="1c48e-232">15000</span><span class="sxs-lookup"><span data-stu-id="1c48e-232">15000</span></span> |
