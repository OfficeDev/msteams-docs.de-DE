---
title: Ratenbegrenzung
description: Ratenbegrenzung und bewährte Methoden in Microsoft Teams
keywords: Teams Bots Ratenbegrenzung
ms.openlocfilehash: 145f65a7e17b833e11631dfc219d9f5732f43bc6
ms.sourcegitcommit: 6c692734a382865531a83b9ebd6f604212f484fc
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/02/2020
ms.locfileid: "42371765"
---
# <a name="optimize-your-bot-rate-limiting-and-best-practices-in-microsoft-teams"></a><span data-ttu-id="d9906-104">Optimieren Ihres bot: Ratenbegrenzung und bewährte Methoden in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="d9906-104">Optimize your bot: rate limiting and best practices in Microsoft Teams</span></span>

<span data-ttu-id="d9906-105">Als allgemeiner Grundsatz sollte Ihre Anwendung die Anzahl der Nachrichten begrenzen, die Sie an eine einzelne Chat-oder Kanal Unterhaltung sendet.</span><span class="sxs-lookup"><span data-stu-id="d9906-105">As a general principle, your application should limit the number of messages it posts to an individual chat or channel conversation.</span></span> <span data-ttu-id="d9906-106">Dadurch wird eine optimale Oberfläche gewährleistet, bei der die Endbenutzer nicht "spammy" empfinden.</span><span class="sxs-lookup"><span data-stu-id="d9906-106">This ensures an optimal experience that doesn't feel “spammy” to your end users.</span></span>

<span data-ttu-id="d9906-107">Um Microsoft Teams und seine Benutzer zu schützen, begrenzen die bot-APIs eingehende Anforderungen.</span><span class="sxs-lookup"><span data-stu-id="d9906-107">To protect Microsoft Teams and its users, the bot APIs rate-limit incoming requests.</span></span> <span data-ttu-id="d9906-108">Apps, die diesen Grenzwert überschreiten, `HTTP 429 Too Many Requests` erhalten einen Fehlerstatus.</span><span class="sxs-lookup"><span data-stu-id="d9906-108">Apps that go over this limit receive an `HTTP 429 Too Many Requests` error status.</span></span> <span data-ttu-id="d9906-109">Alle Anforderungen unterliegen der gleichen Richtlinie zur Ratenbegrenzung, einschließlich Senden von Nachrichten, Kanal Aufzählungen und Dienstplan abrufen.</span><span class="sxs-lookup"><span data-stu-id="d9906-109">All requests are subject to the same rate-limiting policy, including sending messages, channel enumerations, and roster fetches.</span></span>

<span data-ttu-id="d9906-110">Da die genauen Werte von Raten Grenzwerten geändert werden können, wird empfohlen, dass Ihre Anwendung das entsprechende Backoff-Verhalten implementiert, `HTTP 429 Too Many Requests`wenn die API zurückgegeben wird.</span><span class="sxs-lookup"><span data-stu-id="d9906-110">Because the exact values of rate limits are subject to change, we recommend your application implement the appropriate backoff behavior when the API returns `HTTP 429 Too Many Requests`.</span></span>

## <a name="handling-rate-limits"></a><span data-ttu-id="d9906-111">Grenzwerte für die Handhabungs Rate</span><span class="sxs-lookup"><span data-stu-id="d9906-111">Handling rate limits</span></span>

<span data-ttu-id="d9906-112">Beim Ausgeben eines bot-Generator-SDK-Vorgangs können `Microsoft.Rest.HttpOperationException` Sie den Statuscode verarbeiten und überprüfen.</span><span class="sxs-lookup"><span data-stu-id="d9906-112">When issuing a Bot Builder SDK operation, you can handle `Microsoft.Rest.HttpOperationException` and check for the status code.</span></span>

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

## <a name="best-practices"></a><span data-ttu-id="d9906-113">Bewährte Methoden</span><span class="sxs-lookup"><span data-stu-id="d9906-113">Best practices</span></span>

<span data-ttu-id="d9906-114">Im Allgemeinen sollten Sie einfache Vorkehrungen treffen, um den Empfang `HTTP 429` von Antworten zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="d9906-114">In general, you should take simple precautions to avoid receiving `HTTP 429` responses.</span></span> <span data-ttu-id="d9906-115">Vermeiden Sie beispielsweise das ausgeben mehrerer Anforderungen an dieselbe persönliche oder Kanal Unterhaltung.</span><span class="sxs-lookup"><span data-stu-id="d9906-115">For instance, avoid issuing multiple requests to the same personal or channel conversation.</span></span> <span data-ttu-id="d9906-116">Verwenden Sie stattdessen die Batchverarbeitung der API-Anforderungen.</span><span class="sxs-lookup"><span data-stu-id="d9906-116">Instead, consider batching the API requests.</span></span>

<span data-ttu-id="d9906-117">Das Verwenden einer exponentiellen Backoff mit einem willkürlichen Jitter ist die empfohlene Vorgehensweise zum Behandeln von 429er.</span><span class="sxs-lookup"><span data-stu-id="d9906-117">Using an exponential backoff with a random jitter is the recommended way to handle 429s.</span></span> <span data-ttu-id="d9906-118">Dadurch wird sichergestellt, dass mehrere Anforderungen keine Kollisionen bei Wiederholungsversuchen einführen.</span><span class="sxs-lookup"><span data-stu-id="d9906-118">This ensures that multiple requests don't introduce collisions on retries.</span></span>

## <a name="example-detecting-transient-exceptions"></a><span data-ttu-id="d9906-119">Beispiel: Erkennen von vorübergehenden Ausnahmen</span><span class="sxs-lookup"><span data-stu-id="d9906-119">Example: detecting transient exceptions</span></span>

<span data-ttu-id="d9906-120">Im folgenden finden Sie ein Beispiel für die Verwendung eines exponentiellen Backoff über den Anwendungs Block der transienten Fehlerbehandlung.</span><span class="sxs-lookup"><span data-stu-id="d9906-120">Here is a sample using exponential backoff via the Transient Fault Handling Application Block.</span></span>

<span data-ttu-id="d9906-121">Sie können Backoff und Wiederholungsversuche mit [vorübergehender Fehlerbehandlung](/previous-versions/msp-n-p/hh675232%28v%3dpandp.10%29)durchführen.</span><span class="sxs-lookup"><span data-stu-id="d9906-121">You can perform backoff and retries using [Transient Fault Handling](/previous-versions/msp-n-p/hh675232%28v%3dpandp.10%29).</span></span> <span data-ttu-id="d9906-122">Richtlinien zum beziehen und Installieren des NuGet-Pakets finden Sie unter [Hinzufügen des Anwendungsblocks der vorübergehenden Fehlerbehandlung zu Ihrer Lösung](/previous-versions/msp-n-p/dn440719(v=pandp.60)?redirectedfrom=MSDN)).</span><span class="sxs-lookup"><span data-stu-id="d9906-122">For guidelines on obtaining and installing the NuGet package, see [Adding the Transient Fault Handling Application Block to Your Solution](/previous-versions/msp-n-p/dn440719(v=pandp.60)?redirectedfrom=MSDN)).</span></span> <span data-ttu-id="d9906-123">*Siehe auch* [transient Fault Handling](/azure/architecture/best-practices/transient-faults).</span><span class="sxs-lookup"><span data-stu-id="d9906-123">*See also* [Transient fault handling](/azure/architecture/best-practices/transient-faults).</span></span>

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

## <a name="example-backoff"></a><span data-ttu-id="d9906-124">Beispiel: Backoff</span><span class="sxs-lookup"><span data-stu-id="d9906-124">Example: backoff</span></span>

<span data-ttu-id="d9906-125">Zusätzlich zur Ermittlung von Raten Grenzwerten können Sie auch eine exponentielle Backoff ausführen.</span><span class="sxs-lookup"><span data-stu-id="d9906-125">In addition to detecting rate limits, you can also perform an exponential backoff.</span></span>

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

<span data-ttu-id="d9906-126">Sie können auch eine `System.Action` Methodenausführung mit der oben beschriebenen Wiederholungs Richtlinie ausführen.</span><span class="sxs-lookup"><span data-stu-id="d9906-126">You can also perform a `System.Action` method execution with the retry policy described above.</span></span> <span data-ttu-id="d9906-127">Mit der referenzierten Bibliothek können Sie auch ein festes Intervall oder einen linearen Backoff-Mechanismus angeben.</span><span class="sxs-lookup"><span data-stu-id="d9906-127">The referenced library also allows you to specify a fixed interval or a linear backoff mechanism.</span></span>

<span data-ttu-id="d9906-128">Es wird empfohlen, den Wert und die Strategie in einer Konfigurationsdatei zu speichern, um Werte zur Laufzeit zu optimieren und zu optimieren.</span><span class="sxs-lookup"><span data-stu-id="d9906-128">We recommend storing the value and strategy in a configuration file to fine-tune and tweak values at run time.</span></span>

<span data-ttu-id="d9906-129">Weitere Informationen finden Sie in diesem handlichen Leitfaden für verschiedene Wiederholungsmuster: [Wiederholungsmuster](/azure/architecture/patterns/retry).</span><span class="sxs-lookup"><span data-stu-id="d9906-129">For more information, check out this handy guide on various retry patterns: [Retry pattern](/azure/architecture/patterns/retry).</span></span>

## <a name="per-bot-per-thread-limit"></a><span data-ttu-id="d9906-130">Pro bot pro Thread-Grenzwert</span><span class="sxs-lookup"><span data-stu-id="d9906-130">Per bot per thread limit</span></span>

>[!NOTE]
><span data-ttu-id="d9906-131">Die Nachrichten Aufteilung auf Dienstebene führt zu höheren als erwarteten Anforderungen pro Sekunde (RPS).</span><span class="sxs-lookup"><span data-stu-id="d9906-131">Message splitting at the service level will result in higher than expected requests per second (RPS).</span></span> <span data-ttu-id="d9906-132">Wenn Sie Bedenken haben, sich an die Grenzwerte zu wenden, sollten Sie die oben beschriebene Backoff-Strategie implementieren.</span><span class="sxs-lookup"><span data-stu-id="d9906-132">If you're concerned about approaching the limits, you should implement the backoff strategy described above.</span></span> <span data-ttu-id="d9906-133">Die unten angegebenen Werte dienen nur der Schätzung.</span><span class="sxs-lookup"><span data-stu-id="d9906-133">The values provided below are for estimation only.</span></span>

<span data-ttu-id="d9906-134">Dieser Grenzwert steuert den Datenverkehr, den ein bot für eine einzelne Unterhaltung generieren darf.</span><span class="sxs-lookup"><span data-stu-id="d9906-134">This limit controls the traffic that a bot is allowed to generate on a single conversation.</span></span> <span data-ttu-id="d9906-135">Eine Unterhaltung ist 1:1 zwischen bot und Benutzer, einem Gruppenchat oder einem Kanal in einem Team.</span><span class="sxs-lookup"><span data-stu-id="d9906-135">A conversation here is 1:1 between bot and user, a group-chat, or a channel in a team.</span></span>

| <span data-ttu-id="d9906-136">**Szenario**</span><span class="sxs-lookup"><span data-stu-id="d9906-136">**Scenario**</span></span> | <span data-ttu-id="d9906-137">**Zeitraum (Sek.)**</span><span class="sxs-lookup"><span data-stu-id="d9906-137">**Time-period (sec)**</span></span> | <span data-ttu-id="d9906-138">**Max. zulässige Vorgänge**</span><span class="sxs-lookup"><span data-stu-id="d9906-138">**Max allowed operations**</span></span> |
| --- | --- | --- |
|| <span data-ttu-id="d9906-139">1</span><span class="sxs-lookup"><span data-stu-id="d9906-139">1</span></span> | <span data-ttu-id="d9906-140">7</span><span class="sxs-lookup"><span data-stu-id="d9906-140">7</span></span> |
| <span data-ttu-id="d9906-141">An Unterhaltung senden</span><span class="sxs-lookup"><span data-stu-id="d9906-141">Send to Conversation</span></span> | <span data-ttu-id="d9906-142">2</span><span class="sxs-lookup"><span data-stu-id="d9906-142">2</span></span> | <span data-ttu-id="d9906-143">8</span><span class="sxs-lookup"><span data-stu-id="d9906-143">8</span></span> |
| <span data-ttu-id="d9906-144">An Unterhaltung senden</span><span class="sxs-lookup"><span data-stu-id="d9906-144">Send to Conversation</span></span> | <span data-ttu-id="d9906-145">30</span><span class="sxs-lookup"><span data-stu-id="d9906-145">30</span></span> | <span data-ttu-id="d9906-146">60</span><span class="sxs-lookup"><span data-stu-id="d9906-146">60</span></span> |
| <span data-ttu-id="d9906-147">An Unterhaltung senden</span><span class="sxs-lookup"><span data-stu-id="d9906-147">Send to Conversation</span></span> | <span data-ttu-id="d9906-148">3600</span><span class="sxs-lookup"><span data-stu-id="d9906-148">3600</span></span> | <span data-ttu-id="d9906-149">1800</span><span class="sxs-lookup"><span data-stu-id="d9906-149">1800</span></span> |
| <span data-ttu-id="d9906-150">Unterhaltung erstellen</span><span class="sxs-lookup"><span data-stu-id="d9906-150">Create Conversation</span></span> | <span data-ttu-id="d9906-151">1</span><span class="sxs-lookup"><span data-stu-id="d9906-151">1</span></span> | <span data-ttu-id="d9906-152">7</span><span class="sxs-lookup"><span data-stu-id="d9906-152">7</span></span> |
| <span data-ttu-id="d9906-153">Unterhaltung erstellen</span><span class="sxs-lookup"><span data-stu-id="d9906-153">Create Conversation</span></span> | <span data-ttu-id="d9906-154">2</span><span class="sxs-lookup"><span data-stu-id="d9906-154">2</span></span> | <span data-ttu-id="d9906-155">8</span><span class="sxs-lookup"><span data-stu-id="d9906-155">8</span></span> |
| <span data-ttu-id="d9906-156">Unterhaltung erstellen</span><span class="sxs-lookup"><span data-stu-id="d9906-156">Create Conversation</span></span> | <span data-ttu-id="d9906-157">30</span><span class="sxs-lookup"><span data-stu-id="d9906-157">30</span></span> | <span data-ttu-id="d9906-158">60</span><span class="sxs-lookup"><span data-stu-id="d9906-158">60</span></span> |
| <span data-ttu-id="d9906-159">Unterhaltung erstellen</span><span class="sxs-lookup"><span data-stu-id="d9906-159">Create Conversation</span></span> | <span data-ttu-id="d9906-160">3600</span><span class="sxs-lookup"><span data-stu-id="d9906-160">3600</span></span> | <span data-ttu-id="d9906-161">1800</span><span class="sxs-lookup"><span data-stu-id="d9906-161">1800</span></span> |
| <span data-ttu-id="d9906-162">Abrufen von Unterhaltungs Mitgliedern</span><span class="sxs-lookup"><span data-stu-id="d9906-162">Get Conversation Members</span></span>| <span data-ttu-id="d9906-163">1</span><span class="sxs-lookup"><span data-stu-id="d9906-163">1</span></span> | <span data-ttu-id="d9906-164">14 </span><span class="sxs-lookup"><span data-stu-id="d9906-164">14</span></span> |
| <span data-ttu-id="d9906-165">Abrufen von Unterhaltungs Mitgliedern</span><span class="sxs-lookup"><span data-stu-id="d9906-165">Get Conversation Members</span></span>| <span data-ttu-id="d9906-166">2</span><span class="sxs-lookup"><span data-stu-id="d9906-166">2</span></span> | <span data-ttu-id="d9906-167">16 </span><span class="sxs-lookup"><span data-stu-id="d9906-167">16</span></span> |
| <span data-ttu-id="d9906-168">Abrufen von Unterhaltungs Mitgliedern</span><span class="sxs-lookup"><span data-stu-id="d9906-168">Get Conversation Members</span></span>| <span data-ttu-id="d9906-169">30</span><span class="sxs-lookup"><span data-stu-id="d9906-169">30</span></span> | <span data-ttu-id="d9906-170">120</span><span class="sxs-lookup"><span data-stu-id="d9906-170">120</span></span> |
| <span data-ttu-id="d9906-171">Abrufen von Unterhaltungs Mitgliedern</span><span class="sxs-lookup"><span data-stu-id="d9906-171">Get Conversation Members</span></span>| <span data-ttu-id="d9906-172">3600</span><span class="sxs-lookup"><span data-stu-id="d9906-172">3600</span></span> | <span data-ttu-id="d9906-173">3600</span><span class="sxs-lookup"><span data-stu-id="d9906-173">3600</span></span> |
| <span data-ttu-id="d9906-174">Unterhaltungen abrufen</span><span class="sxs-lookup"><span data-stu-id="d9906-174">Get Conversations</span></span> | <span data-ttu-id="d9906-175">1</span><span class="sxs-lookup"><span data-stu-id="d9906-175">1</span></span> | <span data-ttu-id="d9906-176">14 </span><span class="sxs-lookup"><span data-stu-id="d9906-176">14</span></span> |
| <span data-ttu-id="d9906-177">Unterhaltungen abrufen</span><span class="sxs-lookup"><span data-stu-id="d9906-177">Get Conversations</span></span> | <span data-ttu-id="d9906-178">2</span><span class="sxs-lookup"><span data-stu-id="d9906-178">2</span></span> | <span data-ttu-id="d9906-179">16 </span><span class="sxs-lookup"><span data-stu-id="d9906-179">16</span></span> |
| <span data-ttu-id="d9906-180">Unterhaltungen abrufen</span><span class="sxs-lookup"><span data-stu-id="d9906-180">Get Conversations</span></span> | <span data-ttu-id="d9906-181">30</span><span class="sxs-lookup"><span data-stu-id="d9906-181">30</span></span> | <span data-ttu-id="d9906-182">120</span><span class="sxs-lookup"><span data-stu-id="d9906-182">120</span></span> |
| <span data-ttu-id="d9906-183">Unterhaltungen abrufen</span><span class="sxs-lookup"><span data-stu-id="d9906-183">Get Conversations</span></span> | <span data-ttu-id="d9906-184">3600</span><span class="sxs-lookup"><span data-stu-id="d9906-184">3600</span></span> | <span data-ttu-id="d9906-185">3600</span><span class="sxs-lookup"><span data-stu-id="d9906-185">3600</span></span> |

## <a name="per-thread-limit-for-all-bots"></a><span data-ttu-id="d9906-186">Grenzwert pro Thread für alle Bots</span><span class="sxs-lookup"><span data-stu-id="d9906-186">Per thread limit for all bots</span></span>

<span data-ttu-id="d9906-187">Dieser Grenzwert steuert den Datenverkehr, den alle Bots in einer einzigen Unterhaltung generieren dürfen.</span><span class="sxs-lookup"><span data-stu-id="d9906-187">This limit controls the traffic that all bots are allowed to generate across a single conversation.</span></span> <span data-ttu-id="d9906-188">Eine Unterhaltung ist 1:1 zwischen bot und Benutzer, einem Gruppenchat oder einem Kanal in einem Team.</span><span class="sxs-lookup"><span data-stu-id="d9906-188">A conversation here is 1:1 between bot and user, a group-chat, or a channel in a team.</span></span>

| <span data-ttu-id="d9906-189">**Szenario**</span><span class="sxs-lookup"><span data-stu-id="d9906-189">**Scenario**</span></span> | <span data-ttu-id="d9906-190">**Zeitraum (Sek.)**</span><span class="sxs-lookup"><span data-stu-id="d9906-190">**Time-period (sec)**</span></span> | <span data-ttu-id="d9906-191">**Max. zulässige Vorgänge**</span><span class="sxs-lookup"><span data-stu-id="d9906-191">**Max allowed operations**</span></span> |
| --- | --- | --- |
| <span data-ttu-id="d9906-192">An Unterhaltung senden</span><span class="sxs-lookup"><span data-stu-id="d9906-192">Send to Conversation</span></span> | <span data-ttu-id="d9906-193">1</span><span class="sxs-lookup"><span data-stu-id="d9906-193">1</span></span> | <span data-ttu-id="d9906-194">14 </span><span class="sxs-lookup"><span data-stu-id="d9906-194">14</span></span> |
| <span data-ttu-id="d9906-195">An Unterhaltung senden</span><span class="sxs-lookup"><span data-stu-id="d9906-195">Send to Conversation</span></span> | <span data-ttu-id="d9906-196">2</span><span class="sxs-lookup"><span data-stu-id="d9906-196">2</span></span> | <span data-ttu-id="d9906-197">16 </span><span class="sxs-lookup"><span data-stu-id="d9906-197">16</span></span> |
| <span data-ttu-id="d9906-198">Unterhaltung erstellen</span><span class="sxs-lookup"><span data-stu-id="d9906-198">Create Conversation</span></span> | <span data-ttu-id="d9906-199">1</span><span class="sxs-lookup"><span data-stu-id="d9906-199">1</span></span> | <span data-ttu-id="d9906-200">14 </span><span class="sxs-lookup"><span data-stu-id="d9906-200">14</span></span> |
| <span data-ttu-id="d9906-201">Unterhaltung erstellen</span><span class="sxs-lookup"><span data-stu-id="d9906-201">Create Conversation</span></span> | <span data-ttu-id="d9906-202">2</span><span class="sxs-lookup"><span data-stu-id="d9906-202">2</span></span> | <span data-ttu-id="d9906-203">16 </span><span class="sxs-lookup"><span data-stu-id="d9906-203">16</span></span> |
| <span data-ttu-id="d9906-204">Createconversation</span><span class="sxs-lookup"><span data-stu-id="d9906-204">CreateConversation</span></span>| <span data-ttu-id="d9906-205">1</span><span class="sxs-lookup"><span data-stu-id="d9906-205">1</span></span> | <span data-ttu-id="d9906-206">14 </span><span class="sxs-lookup"><span data-stu-id="d9906-206">14</span></span> |
| <span data-ttu-id="d9906-207">Createconversation</span><span class="sxs-lookup"><span data-stu-id="d9906-207">CreateConversation</span></span>| <span data-ttu-id="d9906-208">2</span><span class="sxs-lookup"><span data-stu-id="d9906-208">2</span></span> | <span data-ttu-id="d9906-209">16 </span><span class="sxs-lookup"><span data-stu-id="d9906-209">16</span></span> |
| <span data-ttu-id="d9906-210">Abrufen von Unterhaltungs Mitgliedern</span><span class="sxs-lookup"><span data-stu-id="d9906-210">Get Conversation Members</span></span>| <span data-ttu-id="d9906-211">1</span><span class="sxs-lookup"><span data-stu-id="d9906-211">1</span></span> | <span data-ttu-id="d9906-212">28</span><span class="sxs-lookup"><span data-stu-id="d9906-212">28</span></span> |
| <span data-ttu-id="d9906-213">Abrufen von Unterhaltungs Mitgliedern</span><span class="sxs-lookup"><span data-stu-id="d9906-213">Get Conversation Members</span></span>| <span data-ttu-id="d9906-214">2</span><span class="sxs-lookup"><span data-stu-id="d9906-214">2</span></span> | <span data-ttu-id="d9906-215">32</span><span class="sxs-lookup"><span data-stu-id="d9906-215">32</span></span> |
| <span data-ttu-id="d9906-216">Unterhaltungen abrufen</span><span class="sxs-lookup"><span data-stu-id="d9906-216">Get Conversations</span></span> | <span data-ttu-id="d9906-217">1</span><span class="sxs-lookup"><span data-stu-id="d9906-217">1</span></span> | <span data-ttu-id="d9906-218">28</span><span class="sxs-lookup"><span data-stu-id="d9906-218">28</span></span> |
| <span data-ttu-id="d9906-219">Unterhaltungen abrufen</span><span class="sxs-lookup"><span data-stu-id="d9906-219">Get Conversations</span></span> | <span data-ttu-id="d9906-220">2</span><span class="sxs-lookup"><span data-stu-id="d9906-220">2</span></span> | <span data-ttu-id="d9906-221">32</span><span class="sxs-lookup"><span data-stu-id="d9906-221">32</span></span> |

## <a name="bot-per-data-center-limit"></a><span data-ttu-id="d9906-222">Bot pro Rechenzentrums Grenze</span><span class="sxs-lookup"><span data-stu-id="d9906-222">Bot per data center limit</span></span>

<span data-ttu-id="d9906-223">Dieser Grenzwert steuert den Datenverkehr, den ein bot in allen Threads in einem Rechenzentrum (in mehreren Mandanten) generieren darf.</span><span class="sxs-lookup"><span data-stu-id="d9906-223">This limit controls the traffic that a bot is allowed to generate across all threads in a data center (across multiple tenants).</span></span>

|<span data-ttu-id="d9906-224">**Zeitraum (Sek.)**</span><span class="sxs-lookup"><span data-stu-id="d9906-224">**Time-period (sec)**</span></span> | <span data-ttu-id="d9906-225">**Max. zulässige Vorgänge**</span><span class="sxs-lookup"><span data-stu-id="d9906-225">**Max allowed operations**</span></span> |
| --- | --- |
| <span data-ttu-id="d9906-226">1</span><span class="sxs-lookup"><span data-stu-id="d9906-226">1</span></span> | <span data-ttu-id="d9906-227">20</span><span class="sxs-lookup"><span data-stu-id="d9906-227">20</span></span> |
| <span data-ttu-id="d9906-228">1800</span><span class="sxs-lookup"><span data-stu-id="d9906-228">1800</span></span> | <span data-ttu-id="d9906-229">8000</span><span class="sxs-lookup"><span data-stu-id="d9906-229">8000</span></span> |
| <span data-ttu-id="d9906-230">3600</span><span class="sxs-lookup"><span data-stu-id="d9906-230">3600</span></span> | <span data-ttu-id="d9906-231">15000</span><span class="sxs-lookup"><span data-stu-id="d9906-231">15000</span></span> |
