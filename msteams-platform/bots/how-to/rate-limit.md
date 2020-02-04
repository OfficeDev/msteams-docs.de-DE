---
title: Ratenbegrenzung
description: Ratenbegrenzung und bewährte Methoden in Microsoft Teams
keywords: Teams Bots Ratenbegrenzung
ms.openlocfilehash: 4e9efab539ec7817d259fd6c149c438ba02e3ce5
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674207"
---
# <a name="optimize-your-bot-rate-limiting-and-best-practices-in-microsoft-teams"></a><span data-ttu-id="996eb-104">Optimieren Ihres bot: Ratenbegrenzung und bewährte Methoden in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="996eb-104">Optimize your bot: rate limiting and best practices in Microsoft Teams</span></span>

<span data-ttu-id="996eb-105">Als allgemeiner Grundsatz sollte Ihre Anwendung die Anzahl der Nachrichten begrenzen, die Sie an eine einzelne Chat-oder Kanal Unterhaltung sendet.</span><span class="sxs-lookup"><span data-stu-id="996eb-105">As a general principle, your application should limit the number of messages it posts to an individual chat or channel conversation.</span></span> <span data-ttu-id="996eb-106">Dadurch wird eine optimale Oberfläche gewährleistet, bei der die Endbenutzer nicht "spammy" empfinden.</span><span class="sxs-lookup"><span data-stu-id="996eb-106">This ensures an optimal experience that doesn't feel “spammy” to your end users.</span></span>

<span data-ttu-id="996eb-107">Um Microsoft Teams und seine Benutzer zu schützen, begrenzen die bot-APIs eingehende Anforderungen.</span><span class="sxs-lookup"><span data-stu-id="996eb-107">To protect Microsoft Teams and its users, the bot APIs rate-limit incoming requests.</span></span> <span data-ttu-id="996eb-108">Apps, die diesen Grenzwert überschreiten, `HTTP 429 Too Many Requests` erhalten einen Fehlerstatus.</span><span class="sxs-lookup"><span data-stu-id="996eb-108">Apps that go over this limit receive an `HTTP 429 Too Many Requests` error status.</span></span> <span data-ttu-id="996eb-109">Alle Anforderungen unterliegen der gleichen Richtlinie zur Ratenbegrenzung, einschließlich Senden von Nachrichten, Kanal Aufzählungen und Dienstplan abrufen.</span><span class="sxs-lookup"><span data-stu-id="996eb-109">All requests are subject to the same rate-limiting policy, including sending messages, channel enumerations, and roster fetches.</span></span>

<span data-ttu-id="996eb-110">Da die genauen Werte von Raten Grenzwerten geändert werden können, wird empfohlen, dass Ihre Anwendung das entsprechende Backoff-Verhalten implementiert, `HTTP 429 Too Many Requests`wenn die API zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="996eb-110">Because the exact values of rate limits are subject to change, we recommend your application implement the appropriate backoff behavior when the API returns `HTTP 429 Too Many Requests`.</span></span>

## <a name="handling-rate-limits"></a><span data-ttu-id="996eb-111">Grenzwerte für die Handhabungs Rate</span><span class="sxs-lookup"><span data-stu-id="996eb-111">Handling rate limits</span></span>

<span data-ttu-id="996eb-112">Beim Ausgeben eines bot-Generator-SDK-Vorgangs können `Microsoft.Rest.HttpOperationException` Sie den Statuscode verarbeiten und überprüfen.</span><span class="sxs-lookup"><span data-stu-id="996eb-112">When issuing a Bot Builder SDK operation, you can handle `Microsoft.Rest.HttpOperationException` and check for the status code.</span></span>

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

## <a name="best-practices"></a><span data-ttu-id="996eb-113">Bewährte Methoden</span><span class="sxs-lookup"><span data-stu-id="996eb-113">Best practices</span></span>

<span data-ttu-id="996eb-114">Im Allgemeinen sollten Sie einfache Vorkehrungen treffen, um den Empfang `HTTP 429` von Antworten zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="996eb-114">In general, you should take simple precautions to avoid receiving `HTTP 429` responses.</span></span> <span data-ttu-id="996eb-115">Vermeiden Sie beispielsweise das ausgeben mehrerer Anforderungen an dieselbe persönliche oder Kanal Unterhaltung.</span><span class="sxs-lookup"><span data-stu-id="996eb-115">For instance, avoid issuing multiple requests to the same personal or channel conversation.</span></span> <span data-ttu-id="996eb-116">Verwenden Sie stattdessen die Batchverarbeitung der API-Anforderungen.</span><span class="sxs-lookup"><span data-stu-id="996eb-116">Instead, consider batching the API requests.</span></span>

<span data-ttu-id="996eb-117">Das Verwenden einer exponentiellen Backoff mit einem willkürlichen Jitter ist die empfohlene Vorgehensweise zum Behandeln von 429er.</span><span class="sxs-lookup"><span data-stu-id="996eb-117">Using an exponential backoff with a random jitter is the recommended way to handle 429s.</span></span> <span data-ttu-id="996eb-118">Dadurch wird sichergestellt, dass mehrere Anforderungen keine Kollisionen bei Wiederholungsversuchen einführen.</span><span class="sxs-lookup"><span data-stu-id="996eb-118">This ensures that multiple requests don't introduce collisions on retries.</span></span>

## <a name="example-detecting-transient-exceptions"></a><span data-ttu-id="996eb-119">Beispiel: Erkennen von vorübergehenden Ausnahmen</span><span class="sxs-lookup"><span data-stu-id="996eb-119">Example: detecting transient exceptions</span></span>

<span data-ttu-id="996eb-120">Im folgenden finden Sie ein Beispiel für die Verwendung eines exponentiellen Backoff über den Anwendungs Block der transienten Fehlerbehandlung.</span><span class="sxs-lookup"><span data-stu-id="996eb-120">Here is a sample using exponential backoff via the Transient Fault Handling Application Block.</span></span>

<span data-ttu-id="996eb-121">Sie können Backoff und Wiederholungsversuche mit [temporären Fehler Behandlungs Bibliotheken](/previous-versions/msp-n-p/hh680901(v=pandp.50))durchführen.</span><span class="sxs-lookup"><span data-stu-id="996eb-121">You can perform backoff and retries using [Transient Fault Handling libraries](/previous-versions/msp-n-p/hh680901(v=pandp.50)).</span></span> <span data-ttu-id="996eb-122">Richtlinien zum beziehen und Installieren des NuGet-Pakets finden Sie unter [Hinzufügen des Anwendungsblocks der vorübergehenden Fehlerbehandlung zur Lösung](/previous-versions/msp-n-p/hh680891(v=pandp.50)) .</span><span class="sxs-lookup"><span data-stu-id="996eb-122">For guidelines on obtaining and installing the NuGet package, see [Adding the Transient Fault Handling Application Block to Your Solution](/previous-versions/msp-n-p/hh680891(v=pandp.50))</span></span>

```csharp
public class BotSdkTransientExceptionDetectionStrategy : ITransientErrorDetectionStrategy
{
    // List of error codes to retry on
    List<int> transientErrorStatusCodes = new List<int>() { 429 };

    public bool IsTransient(Exception ex)
    {
        var httpOperationException = ex as HttpOperationException;
        if (httpOperationException != null)
        {
            return httpOperationException.Response != null &&
                    transientErrorStatusCodes.Contains((int) httpOperationException.Response.StatusCode);
        }

        return false;
    }
}
```

## <a name="example-backoff"></a><span data-ttu-id="996eb-123">Beispiel: Backoff</span><span class="sxs-lookup"><span data-stu-id="996eb-123">Example: backoff</span></span>

<span data-ttu-id="996eb-124">Zusätzlich zur Ermittlung von Raten Grenzwerten können Sie auch eine exponentielle Backoff ausführen.</span><span class="sxs-lookup"><span data-stu-id="996eb-124">In addition to detecting rate limits, you can also perform an exponential backoff.</span></span>

```csharp
/**
* The first parameter specifies the number of retries before failing the operation.
* The second parameter specifies the minimum and maximum backoff time respectively.
* The last parameter is used to add a randomized  +/- 20% delta to avoid numerous clients retrying simultaneously.
*/
var exponentialBackoffRetryStrategy = new ExponentialBackoff(3, TimeSpan.FromSeconds(2),
                        TimeSpan.FromSeconds(20), TimeSpan.FromSeconds(1));


// Define the Retry Policy
var retryPolicy = new RetryPolicy(new BotSdkTransientExceptionDetectionStrategy(), fixedIntervalRetryStrategy);

//Execute any bot sdk action
await retryPolicy.ExecuteAsync(() => connector.Conversations.ReplyToActivityAsync((Activity)reply)).ConfigureAwait(false);
```

<span data-ttu-id="996eb-125">Sie können auch eine `System.Action` Methodenausführung mit der oben beschriebenen Wiederholungs Richtlinie ausführen.</span><span class="sxs-lookup"><span data-stu-id="996eb-125">You can also perform a `System.Action` method execution with the retry policy described above.</span></span> <span data-ttu-id="996eb-126">Mit der referenzierten Bibliothek können Sie auch ein festes Intervall oder einen linearen Backoff-Mechanismus angeben.</span><span class="sxs-lookup"><span data-stu-id="996eb-126">The referenced library also allows you to specify a fixed interval or a linear backoff mechanism.</span></span>

<span data-ttu-id="996eb-127">Es wird empfohlen, den Wert und die Strategie in einer Konfigurationsdatei zu speichern, um Werte zur Laufzeit zu optimieren und zu optimieren.</span><span class="sxs-lookup"><span data-stu-id="996eb-127">We recommend storing the value and strategy in a configuration file to fine-tune and tweak values at run time.</span></span>

<span data-ttu-id="996eb-128">Weitere Informationen finden Sie in diesem handlichen Leitfaden für verschiedene Wiederholungsmuster: [Wiederholungsmuster](/azure/architecture/patterns/retry).</span><span class="sxs-lookup"><span data-stu-id="996eb-128">For more information, check out this handy guide on various retry patterns: [Retry pattern](/azure/architecture/patterns/retry).</span></span>

## <a name="per-bot-per-thread-limit"></a><span data-ttu-id="996eb-129">Pro bot pro Thread-Grenzwert</span><span class="sxs-lookup"><span data-stu-id="996eb-129">Per bot per thread limit</span></span>

>[!NOTE]
><span data-ttu-id="996eb-130">Die Nachrichten Aufteilung auf Dienstebene führt zu höheren als erwarteten Anforderungen pro Sekunde (RPS).</span><span class="sxs-lookup"><span data-stu-id="996eb-130">Message splitting at the service level will result in higher than expected requests per second (RPS).</span></span> <span data-ttu-id="996eb-131">Wenn Sie Bedenken haben, sich an die Grenzwerte zu wenden, sollten Sie die oben beschriebene Backoff-Strategie implementieren.</span><span class="sxs-lookup"><span data-stu-id="996eb-131">If you're concerned about approaching the limits, you should implement the backoff strategy described above.</span></span> <span data-ttu-id="996eb-132">Die unten angegebenen Werte dienen nur der Schätzung.</span><span class="sxs-lookup"><span data-stu-id="996eb-132">The values provided below are for estimation only.</span></span>

<span data-ttu-id="996eb-133">Dieser Grenzwert steuert den Datenverkehr, den ein bot für eine einzelne Unterhaltung generieren darf.</span><span class="sxs-lookup"><span data-stu-id="996eb-133">This limit controls the traffic that a bot is allowed to generate on a single conversation.</span></span> <span data-ttu-id="996eb-134">Eine Unterhaltung ist 1:1 zwischen bot und Benutzer, einem Gruppenchat oder einem Kanal in einem Team.</span><span class="sxs-lookup"><span data-stu-id="996eb-134">A conversation here is 1:1 between bot and user, a group-chat, or a channel in a team.</span></span>

| <span data-ttu-id="996eb-135">**Szenario**</span><span class="sxs-lookup"><span data-stu-id="996eb-135">**Scenario**</span></span> | <span data-ttu-id="996eb-136">**Zeitraum (Sek.)**</span><span class="sxs-lookup"><span data-stu-id="996eb-136">**Time-period (sec)**</span></span> | <span data-ttu-id="996eb-137">**Max. zulässige Vorgänge**</span><span class="sxs-lookup"><span data-stu-id="996eb-137">**Max allowed operations**</span></span> |
| --- | --- | --- |
| <span data-ttu-id="996eb-138">NewMessage</span><span class="sxs-lookup"><span data-stu-id="996eb-138">NewMessage</span></span> | <span data-ttu-id="996eb-139">1 </span><span class="sxs-lookup"><span data-stu-id="996eb-139">1</span></span> | <span data-ttu-id="996eb-140">7 </span><span class="sxs-lookup"><span data-stu-id="996eb-140">7</span></span> |
| <span data-ttu-id="996eb-141">NewMessage</span><span class="sxs-lookup"><span data-stu-id="996eb-141">NewMessage</span></span> | <span data-ttu-id="996eb-142">2 </span><span class="sxs-lookup"><span data-stu-id="996eb-142">2</span></span> | <span data-ttu-id="996eb-143">8 </span><span class="sxs-lookup"><span data-stu-id="996eb-143">8</span></span> |
| <span data-ttu-id="996eb-144">NewMessage</span><span class="sxs-lookup"><span data-stu-id="996eb-144">NewMessage</span></span> | <span data-ttu-id="996eb-145">30</span><span class="sxs-lookup"><span data-stu-id="996eb-145">30</span></span> | <span data-ttu-id="996eb-146">60</span><span class="sxs-lookup"><span data-stu-id="996eb-146">60</span></span> |
| <span data-ttu-id="996eb-147">NewMessage</span><span class="sxs-lookup"><span data-stu-id="996eb-147">NewMessage</span></span> | <span data-ttu-id="996eb-148">3600</span><span class="sxs-lookup"><span data-stu-id="996eb-148">3600</span></span> | <span data-ttu-id="996eb-149">1800</span><span class="sxs-lookup"><span data-stu-id="996eb-149">1800</span></span> |
| <span data-ttu-id="996eb-150">UpdateMessage</span><span class="sxs-lookup"><span data-stu-id="996eb-150">UpdateMessage</span></span> | <span data-ttu-id="996eb-151">1 </span><span class="sxs-lookup"><span data-stu-id="996eb-151">1</span></span> | <span data-ttu-id="996eb-152">7 </span><span class="sxs-lookup"><span data-stu-id="996eb-152">7</span></span> |
| <span data-ttu-id="996eb-153">UpdateMessage</span><span class="sxs-lookup"><span data-stu-id="996eb-153">UpdateMessage</span></span> | <span data-ttu-id="996eb-154">2 </span><span class="sxs-lookup"><span data-stu-id="996eb-154">2</span></span> | <span data-ttu-id="996eb-155">8 </span><span class="sxs-lookup"><span data-stu-id="996eb-155">8</span></span> |
| <span data-ttu-id="996eb-156">UpdateMessage</span><span class="sxs-lookup"><span data-stu-id="996eb-156">UpdateMessage</span></span> | <span data-ttu-id="996eb-157">30</span><span class="sxs-lookup"><span data-stu-id="996eb-157">30</span></span> | <span data-ttu-id="996eb-158">60</span><span class="sxs-lookup"><span data-stu-id="996eb-158">60</span></span> |
| <span data-ttu-id="996eb-159">UpdateMessage</span><span class="sxs-lookup"><span data-stu-id="996eb-159">UpdateMessage</span></span> | <span data-ttu-id="996eb-160">3600</span><span class="sxs-lookup"><span data-stu-id="996eb-160">3600</span></span> | <span data-ttu-id="996eb-161">1800</span><span class="sxs-lookup"><span data-stu-id="996eb-161">1800</span></span> |
| <span data-ttu-id="996eb-162">NewThread</span><span class="sxs-lookup"><span data-stu-id="996eb-162">NewThread</span></span> | <span data-ttu-id="996eb-163">1 </span><span class="sxs-lookup"><span data-stu-id="996eb-163">1</span></span> | <span data-ttu-id="996eb-164">7 </span><span class="sxs-lookup"><span data-stu-id="996eb-164">7</span></span> |
| <span data-ttu-id="996eb-165">NewThread</span><span class="sxs-lookup"><span data-stu-id="996eb-165">NewThread</span></span> | <span data-ttu-id="996eb-166">2 </span><span class="sxs-lookup"><span data-stu-id="996eb-166">2</span></span> | <span data-ttu-id="996eb-167">8 </span><span class="sxs-lookup"><span data-stu-id="996eb-167">8</span></span> |
| <span data-ttu-id="996eb-168">NewThread</span><span class="sxs-lookup"><span data-stu-id="996eb-168">NewThread</span></span> | <span data-ttu-id="996eb-169">30</span><span class="sxs-lookup"><span data-stu-id="996eb-169">30</span></span> | <span data-ttu-id="996eb-170">60</span><span class="sxs-lookup"><span data-stu-id="996eb-170">60</span></span> |
| <span data-ttu-id="996eb-171">NewThread</span><span class="sxs-lookup"><span data-stu-id="996eb-171">NewThread</span></span> | <span data-ttu-id="996eb-172">3600</span><span class="sxs-lookup"><span data-stu-id="996eb-172">3600</span></span> | <span data-ttu-id="996eb-173">1800</span><span class="sxs-lookup"><span data-stu-id="996eb-173">1800</span></span> |
| <span data-ttu-id="996eb-174">GetThreadMembers</span><span class="sxs-lookup"><span data-stu-id="996eb-174">GetThreadMembers</span></span> | <span data-ttu-id="996eb-175">1 </span><span class="sxs-lookup"><span data-stu-id="996eb-175">1</span></span> | <span data-ttu-id="996eb-176">14 </span><span class="sxs-lookup"><span data-stu-id="996eb-176">14</span></span> |
| <span data-ttu-id="996eb-177">GetThreadMembers</span><span class="sxs-lookup"><span data-stu-id="996eb-177">GetThreadMembers</span></span> | <span data-ttu-id="996eb-178">2 </span><span class="sxs-lookup"><span data-stu-id="996eb-178">2</span></span> | <span data-ttu-id="996eb-179">16 </span><span class="sxs-lookup"><span data-stu-id="996eb-179">16</span></span> |
| <span data-ttu-id="996eb-180">GetThreadMembers</span><span class="sxs-lookup"><span data-stu-id="996eb-180">GetThreadMembers</span></span> | <span data-ttu-id="996eb-181">30</span><span class="sxs-lookup"><span data-stu-id="996eb-181">30</span></span> | <span data-ttu-id="996eb-182">120</span><span class="sxs-lookup"><span data-stu-id="996eb-182">120</span></span> |
| <span data-ttu-id="996eb-183">GetThreadMembers</span><span class="sxs-lookup"><span data-stu-id="996eb-183">GetThreadMembers</span></span> | <span data-ttu-id="996eb-184">3600</span><span class="sxs-lookup"><span data-stu-id="996eb-184">3600</span></span> | <span data-ttu-id="996eb-185">3600</span><span class="sxs-lookup"><span data-stu-id="996eb-185">3600</span></span> |
| <span data-ttu-id="996eb-186">GetThread</span><span class="sxs-lookup"><span data-stu-id="996eb-186">GetThread</span></span> | <span data-ttu-id="996eb-187">1 </span><span class="sxs-lookup"><span data-stu-id="996eb-187">1</span></span> | <span data-ttu-id="996eb-188">14 </span><span class="sxs-lookup"><span data-stu-id="996eb-188">14</span></span> |
| <span data-ttu-id="996eb-189">GetThread</span><span class="sxs-lookup"><span data-stu-id="996eb-189">GetThread</span></span> | <span data-ttu-id="996eb-190">2 </span><span class="sxs-lookup"><span data-stu-id="996eb-190">2</span></span> | <span data-ttu-id="996eb-191">16 </span><span class="sxs-lookup"><span data-stu-id="996eb-191">16</span></span> |
| <span data-ttu-id="996eb-192">GetThread</span><span class="sxs-lookup"><span data-stu-id="996eb-192">GetThread</span></span> | <span data-ttu-id="996eb-193">30</span><span class="sxs-lookup"><span data-stu-id="996eb-193">30</span></span> | <span data-ttu-id="996eb-194">120</span><span class="sxs-lookup"><span data-stu-id="996eb-194">120</span></span> |
| <span data-ttu-id="996eb-195">GetThread</span><span class="sxs-lookup"><span data-stu-id="996eb-195">GetThread</span></span> | <span data-ttu-id="996eb-196">3600</span><span class="sxs-lookup"><span data-stu-id="996eb-196">3600</span></span> | <span data-ttu-id="996eb-197">3600</span><span class="sxs-lookup"><span data-stu-id="996eb-197">3600</span></span> |

## <a name="per-thread-limit-for-all-bots"></a><span data-ttu-id="996eb-198">Grenzwert pro Thread für alle Bots</span><span class="sxs-lookup"><span data-stu-id="996eb-198">Per thread limit for all bots</span></span>

<span data-ttu-id="996eb-199">Dieser Grenzwert steuert den Datenverkehr, den alle Bots in einer einzigen Unterhaltung generieren dürfen.</span><span class="sxs-lookup"><span data-stu-id="996eb-199">This limit controls the traffic that all bots are allowed to generate across a single conversation.</span></span> <span data-ttu-id="996eb-200">Eine Unterhaltung ist 1:1 zwischen bot und Benutzer, einem Gruppenchat oder einem Kanal in einem Team.</span><span class="sxs-lookup"><span data-stu-id="996eb-200">A conversation here is 1:1 between bot and user, a group-chat, or a channel in a team.</span></span>

| <span data-ttu-id="996eb-201">**Szenario**</span><span class="sxs-lookup"><span data-stu-id="996eb-201">**Scenario**</span></span> | <span data-ttu-id="996eb-202">**Zeitraum (Sek.)**</span><span class="sxs-lookup"><span data-stu-id="996eb-202">**Time-period (sec)**</span></span> | <span data-ttu-id="996eb-203">**Max. zulässige Vorgänge**</span><span class="sxs-lookup"><span data-stu-id="996eb-203">**Max allowed operations**</span></span> |
| --- | --- | --- |
| <span data-ttu-id="996eb-204">NewMessage</span><span class="sxs-lookup"><span data-stu-id="996eb-204">NewMessage</span></span> | <span data-ttu-id="996eb-205">1 </span><span class="sxs-lookup"><span data-stu-id="996eb-205">1</span></span> | <span data-ttu-id="996eb-206">14 </span><span class="sxs-lookup"><span data-stu-id="996eb-206">14</span></span> |
| <span data-ttu-id="996eb-207">NewMessage</span><span class="sxs-lookup"><span data-stu-id="996eb-207">NewMessage</span></span> | <span data-ttu-id="996eb-208">2 </span><span class="sxs-lookup"><span data-stu-id="996eb-208">2</span></span> | <span data-ttu-id="996eb-209">16 </span><span class="sxs-lookup"><span data-stu-id="996eb-209">16</span></span> |
| <span data-ttu-id="996eb-210">UpdateMessage</span><span class="sxs-lookup"><span data-stu-id="996eb-210">UpdateMessage</span></span> | <span data-ttu-id="996eb-211">1 </span><span class="sxs-lookup"><span data-stu-id="996eb-211">1</span></span> | <span data-ttu-id="996eb-212">14 </span><span class="sxs-lookup"><span data-stu-id="996eb-212">14</span></span> |
| <span data-ttu-id="996eb-213">UpdateMessage</span><span class="sxs-lookup"><span data-stu-id="996eb-213">UpdateMessage</span></span> | <span data-ttu-id="996eb-214">2 </span><span class="sxs-lookup"><span data-stu-id="996eb-214">2</span></span> | <span data-ttu-id="996eb-215">16 </span><span class="sxs-lookup"><span data-stu-id="996eb-215">16</span></span> |
| <span data-ttu-id="996eb-216">NewThread</span><span class="sxs-lookup"><span data-stu-id="996eb-216">NewThread</span></span> | <span data-ttu-id="996eb-217">1 </span><span class="sxs-lookup"><span data-stu-id="996eb-217">1</span></span> | <span data-ttu-id="996eb-218">14 </span><span class="sxs-lookup"><span data-stu-id="996eb-218">14</span></span> |
| <span data-ttu-id="996eb-219">NewThread</span><span class="sxs-lookup"><span data-stu-id="996eb-219">NewThread</span></span> | <span data-ttu-id="996eb-220">2 </span><span class="sxs-lookup"><span data-stu-id="996eb-220">2</span></span> | <span data-ttu-id="996eb-221">16 </span><span class="sxs-lookup"><span data-stu-id="996eb-221">16</span></span> |
| <span data-ttu-id="996eb-222">GetThreadMembers</span><span class="sxs-lookup"><span data-stu-id="996eb-222">GetThreadMembers</span></span> | <span data-ttu-id="996eb-223">1 </span><span class="sxs-lookup"><span data-stu-id="996eb-223">1</span></span> | <span data-ttu-id="996eb-224">28</span><span class="sxs-lookup"><span data-stu-id="996eb-224">28</span></span> |
| <span data-ttu-id="996eb-225">GetThreadMembers</span><span class="sxs-lookup"><span data-stu-id="996eb-225">GetThreadMembers</span></span> | <span data-ttu-id="996eb-226">2 </span><span class="sxs-lookup"><span data-stu-id="996eb-226">2</span></span> | <span data-ttu-id="996eb-227">32</span><span class="sxs-lookup"><span data-stu-id="996eb-227">32</span></span> |
| <span data-ttu-id="996eb-228">GetThread</span><span class="sxs-lookup"><span data-stu-id="996eb-228">GetThread</span></span> | <span data-ttu-id="996eb-229">1 </span><span class="sxs-lookup"><span data-stu-id="996eb-229">1</span></span> | <span data-ttu-id="996eb-230">28</span><span class="sxs-lookup"><span data-stu-id="996eb-230">28</span></span> |
| <span data-ttu-id="996eb-231">GetThread</span><span class="sxs-lookup"><span data-stu-id="996eb-231">GetThread</span></span> | <span data-ttu-id="996eb-232">2 </span><span class="sxs-lookup"><span data-stu-id="996eb-232">2</span></span> | <span data-ttu-id="996eb-233">32</span><span class="sxs-lookup"><span data-stu-id="996eb-233">32</span></span> |

## <a name="bot-per-data-center-limit"></a><span data-ttu-id="996eb-234">Bot pro Rechenzentrums Grenze</span><span class="sxs-lookup"><span data-stu-id="996eb-234">Bot per data center limit</span></span>

<span data-ttu-id="996eb-235">Dieser Grenzwert steuert den Datenverkehr, den ein bot in allen Threads in einem Rechenzentrum (in mehreren Mandanten) generieren darf.</span><span class="sxs-lookup"><span data-stu-id="996eb-235">This limit controls the traffic that a bot is allowed to generate across all threads in a data center (across multiple tenants).</span></span>

|<span data-ttu-id="996eb-236">**Zeitraum (Sek.)**</span><span class="sxs-lookup"><span data-stu-id="996eb-236">**Time-period (sec)**</span></span> | <span data-ttu-id="996eb-237">**Max. zulässige Vorgänge**</span><span class="sxs-lookup"><span data-stu-id="996eb-237">**Max allowed operations**</span></span> |
| --- | --- |
| <span data-ttu-id="996eb-238">1 </span><span class="sxs-lookup"><span data-stu-id="996eb-238">1</span></span> | <span data-ttu-id="996eb-239">20</span><span class="sxs-lookup"><span data-stu-id="996eb-239">20</span></span> |
| <span data-ttu-id="996eb-240">1800</span><span class="sxs-lookup"><span data-stu-id="996eb-240">1800</span></span> | <span data-ttu-id="996eb-241">8000</span><span class="sxs-lookup"><span data-stu-id="996eb-241">8000</span></span> |
| <span data-ttu-id="996eb-242">3600</span><span class="sxs-lookup"><span data-stu-id="996eb-242">3600</span></span> | <span data-ttu-id="996eb-243">15000</span><span class="sxs-lookup"><span data-stu-id="996eb-243">15000</span></span> |
