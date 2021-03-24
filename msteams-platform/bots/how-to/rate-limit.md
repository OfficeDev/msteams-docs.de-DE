---
title: Geschwindigkeitsbegrenzung
description: Geschwindigkeitsbegrenzung und bewährte Methoden in Microsoft Teams
keywords: Beschränkung der Rate von Teams-Bots
ms.openlocfilehash: 840737178234bcd6e2da1925b0031083717e2b91
ms.sourcegitcommit: 49d1ecda14042bf3f368b14c1971618fe979b914
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/23/2021
ms.locfileid: "51034683"
---
# <a name="optimize-your-bot-rate-limiting-and-best-practices-in-microsoft-teams"></a><span data-ttu-id="e1385-104">Optimieren Des Bots: Geschwindigkeitsbegrenzung und bewährte Methoden in Microsoft Teams</span><span class="sxs-lookup"><span data-stu-id="e1385-104">Optimize your bot: rate limiting and best practices in Microsoft Teams</span></span>

<span data-ttu-id="e1385-105">Als allgemeines Prinzip sollte Ihre Anwendung die Anzahl der Von ihr gesendeten Nachrichten auf eine einzelne Chat- oder Kanal unterhaltung beschränken.</span><span class="sxs-lookup"><span data-stu-id="e1385-105">As a general principle, your application should limit the number of messages it posts to an individual chat or channel conversation.</span></span> <span data-ttu-id="e1385-106">Dadurch wird eine optimale Benutzererfahrung sichergestellt, die sich für Ihre Endbenutzer nicht als "Spam" anfühlt.</span><span class="sxs-lookup"><span data-stu-id="e1385-106">This ensures an optimal experience that doesn't feel “spammy” to your end users.</span></span>

<span data-ttu-id="e1385-107">Zum Schutz von Microsoft Teams und seinen Benutzern beschränken die Bot-APIs eingehende Anforderungen.</span><span class="sxs-lookup"><span data-stu-id="e1385-107">To protect Microsoft Teams and its users, the bot APIs rate-limit incoming requests.</span></span> <span data-ttu-id="e1385-108">Apps, die diesen Grenzwert überschreiten, erhalten einen `HTTP 429 Too Many Requests` Fehlerstatus.</span><span class="sxs-lookup"><span data-stu-id="e1385-108">Apps that go over this limit receive an `HTTP 429 Too Many Requests` error status.</span></span> <span data-ttu-id="e1385-109">Alle Anforderungen unterliegen der gleichen Richtlinie zur Begrenzung der Geschwindigkeit, einschließlich des Sendens von Nachrichten, Kanalaufzählungen und Abrufen von Dienstplans.</span><span class="sxs-lookup"><span data-stu-id="e1385-109">All requests are subject to the same rate-limiting policy, including sending messages, channel enumerations, and roster fetches.</span></span>

<span data-ttu-id="e1385-110">Da die genauen Werte von Zinsgrenzen geändert werden können, wird empfohlen, dass Ihre Anwendung das entsprechende Backoff-Verhalten implementiert, wenn die API `HTTP 429 Too Many Requests` zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="e1385-110">Because the exact values of rate limits are subject to change, we recommend your application implement the appropriate backoff behavior when the API returns `HTTP 429 Too Many Requests`.</span></span>

## <a name="handling-rate-limits"></a><span data-ttu-id="e1385-111">Behandeln von Geschwindigkeitsbeschränkungen</span><span class="sxs-lookup"><span data-stu-id="e1385-111">Handling rate limits</span></span>

<span data-ttu-id="e1385-112">Beim Ausstellen eines Bot Builder-SDK-Vorgangs können Sie den Statuscode `Microsoft.Rest.HttpOperationException` behandeln und überprüfen.</span><span class="sxs-lookup"><span data-stu-id="e1385-112">When issuing a Bot Builder SDK operation, you can handle `Microsoft.Rest.HttpOperationException` and check for the status code.</span></span>

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

## <a name="best-practices"></a><span data-ttu-id="e1385-113">Bewährte Methoden</span><span class="sxs-lookup"><span data-stu-id="e1385-113">Best practices</span></span>

<span data-ttu-id="e1385-114">Im Allgemeinen sollten Sie einfache Vorsichtsmaßnahmen ergreifen, um den Empfang von Antworten `HTTP 429` zu vermeiden.</span><span class="sxs-lookup"><span data-stu-id="e1385-114">In general, you should take simple precautions to avoid receiving `HTTP 429` responses.</span></span> <span data-ttu-id="e1385-115">Vermeiden Sie beispielsweise, mehrere Anforderungen an dieselbe persönliche Unterhaltung oder eine Kanal unterhaltung ausstellen.</span><span class="sxs-lookup"><span data-stu-id="e1385-115">For instance, avoid issuing multiple requests to the same personal or channel conversation.</span></span> <span data-ttu-id="e1385-116">Erwägen Sie stattdessen das Batchen der API-Anforderungen.</span><span class="sxs-lookup"><span data-stu-id="e1385-116">Instead, consider batching the API requests.</span></span>

<span data-ttu-id="e1385-117">Die Verwendung eines exponentiellen Backoffs mit einem zufälligen Jitter ist die empfohlene Methode zum Verarbeiten von 429s.</span><span class="sxs-lookup"><span data-stu-id="e1385-117">Using an exponential backoff with a random jitter is the recommended way to handle 429s.</span></span> <span data-ttu-id="e1385-118">Dadurch wird sichergestellt, dass bei Wiederholungsversuchen bei mehreren Anforderungen keine Kollisionen auftut.</span><span class="sxs-lookup"><span data-stu-id="e1385-118">This ensures that multiple requests don't introduce collisions on retries.</span></span>

## <a name="example-detecting-transient-exceptions"></a><span data-ttu-id="e1385-119">Beispiel: Erkennen vorübergehender Ausnahmen</span><span class="sxs-lookup"><span data-stu-id="e1385-119">Example: detecting transient exceptions</span></span>

<span data-ttu-id="e1385-120">Im Folgenden finden Sie ein Beispiel mit exponentiellem Backoff über den Anwendungsblock für die vorübergehende Fehlerbehandlung.</span><span class="sxs-lookup"><span data-stu-id="e1385-120">Here is a sample using exponential backoff via the Transient Fault Handling Application Block.</span></span>

<span data-ttu-id="e1385-121">Sie können Backoff- und Wiederholungsversuche mithilfe der [transienten Fehlerbehandlung ausführen.](/previous-versions/msp-n-p/hh675232%28v%3dpandp.10%29)</span><span class="sxs-lookup"><span data-stu-id="e1385-121">You can perform backoff and retries using [Transient Fault Handling](/previous-versions/msp-n-p/hh675232%28v%3dpandp.10%29).</span></span> <span data-ttu-id="e1385-122">Richtlinien zum Abrufen und Installieren des NuGet-Pakets finden Sie unter [Adding the Transient Fault Handling Application Block to Your Solution](/previous-versions/msp-n-p/dn440719(v=pandp.60)?redirectedfrom=MSDN)).</span><span class="sxs-lookup"><span data-stu-id="e1385-122">For guidelines on obtaining and installing the NuGet package, see [Adding the Transient Fault Handling Application Block to Your Solution](/previous-versions/msp-n-p/dn440719(v=pandp.60)?redirectedfrom=MSDN)).</span></span> <span data-ttu-id="e1385-123">*Siehe auch Vorübergehende* [Fehlerbehandlung](/azure/architecture/best-practices/transient-faults).</span><span class="sxs-lookup"><span data-stu-id="e1385-123">*See also* [Transient fault handling](/azure/architecture/best-practices/transient-faults).</span></span>

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

## <a name="example-backoff"></a><span data-ttu-id="e1385-124">Beispiel: Backoff</span><span class="sxs-lookup"><span data-stu-id="e1385-124">Example: backoff</span></span>

<span data-ttu-id="e1385-125">Sie können nicht nur Geschwindigkeitsbegrenzungen erkennen, sondern auch ein exponentielles Backoff ausführen.</span><span class="sxs-lookup"><span data-stu-id="e1385-125">In addition to detecting rate limits, you can also perform an exponential backoff.</span></span>

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

<span data-ttu-id="e1385-126">Sie können auch eine Methodenausführung mit der oben beschriebenen `System.Action` Wiederholungsrichtlinie ausführen.</span><span class="sxs-lookup"><span data-stu-id="e1385-126">You can also perform a `System.Action` method execution with the retry policy described above.</span></span> <span data-ttu-id="e1385-127">Mit der referenzierten Bibliothek können Sie auch ein festes Intervall oder einen linearen Backoffmechanismus angeben.</span><span class="sxs-lookup"><span data-stu-id="e1385-127">The referenced library also allows you to specify a fixed interval or a linear backoff mechanism.</span></span>

<span data-ttu-id="e1385-128">Es wird empfohlen, den Wert und die Strategie in einer Konfigurationsdatei zu speichern, um Werte zur Laufzeit zu optimieren und zu optimieren.</span><span class="sxs-lookup"><span data-stu-id="e1385-128">We recommend storing the value and strategy in a configuration file to fine-tune and tweak values at run time.</span></span>

<span data-ttu-id="e1385-129">Weitere Informationen finden Sie in dieser praktischen Anleitung zu verschiedenen Wiederholungsmustern: [Wiederholungsmuster](/azure/architecture/patterns/retry).</span><span class="sxs-lookup"><span data-stu-id="e1385-129">For more information, check out this handy guide on various retry patterns: [Retry pattern](/azure/architecture/patterns/retry).</span></span>

## <a name="per-bot-per-thread-limit"></a><span data-ttu-id="e1385-130">Pro Bot pro Threadgrenzwert</span><span class="sxs-lookup"><span data-stu-id="e1385-130">Per bot per thread limit</span></span>

>[!NOTE]
><span data-ttu-id="e1385-131">Die Nachrichtenteilung auf Dienstebene führt zu höheren Anforderungen pro Sekunde (RPS).</span><span class="sxs-lookup"><span data-stu-id="e1385-131">Message splitting at the service level will result in higher than expected requests per second (RPS).</span></span> <span data-ttu-id="e1385-132">Wenn Sie sich Gedanken darüber machen, die Grenzwerte zu überschreiten, sollten Sie die oben beschriebene Backoffstrategie implementieren.</span><span class="sxs-lookup"><span data-stu-id="e1385-132">If you're concerned about approaching the limits, you should implement the backoff strategy described above.</span></span> <span data-ttu-id="e1385-133">Die unten angegebenen Werte sind nur zur Schätzung vorgesehen.</span><span class="sxs-lookup"><span data-stu-id="e1385-133">The values provided below are for estimation only.</span></span>

<span data-ttu-id="e1385-134">Dieser Grenzwert steuert den Datenverkehr, den ein Bot für eine einzelne Unterhaltung generieren darf.</span><span class="sxs-lookup"><span data-stu-id="e1385-134">This limit controls the traffic that a bot is allowed to generate on a single conversation.</span></span> <span data-ttu-id="e1385-135">Eine Unterhaltung hier ist 1:1 zwischen Bot und Benutzer, einem Gruppenchat oder einem Kanal in einem Team.</span><span class="sxs-lookup"><span data-stu-id="e1385-135">A conversation here is 1:1 between bot and user, a group-chat, or a channel in a team.</span></span>

| <span data-ttu-id="e1385-136">**Szenario**</span><span class="sxs-lookup"><span data-stu-id="e1385-136">**Scenario**</span></span> | <span data-ttu-id="e1385-137">**Zeitraum (Sek.)**</span><span class="sxs-lookup"><span data-stu-id="e1385-137">**Time-period (sec)**</span></span> | <span data-ttu-id="e1385-138">**Maximal zulässige Vorgänge**</span><span class="sxs-lookup"><span data-stu-id="e1385-138">**Max allowed operations**</span></span> |
| --- | --- | --- |
| <span data-ttu-id="e1385-139">An Unterhaltung senden</span><span class="sxs-lookup"><span data-stu-id="e1385-139">Send to Conversation</span></span> | <span data-ttu-id="e1385-140">1</span><span class="sxs-lookup"><span data-stu-id="e1385-140">1</span></span> | <span data-ttu-id="e1385-141">7 </span><span class="sxs-lookup"><span data-stu-id="e1385-141">7</span></span> |
| <span data-ttu-id="e1385-142">An Unterhaltung senden</span><span class="sxs-lookup"><span data-stu-id="e1385-142">Send to Conversation</span></span> | <span data-ttu-id="e1385-143">2</span><span class="sxs-lookup"><span data-stu-id="e1385-143">2</span></span> | <span data-ttu-id="e1385-144">8 </span><span class="sxs-lookup"><span data-stu-id="e1385-144">8</span></span> |
| <span data-ttu-id="e1385-145">An Unterhaltung senden</span><span class="sxs-lookup"><span data-stu-id="e1385-145">Send to Conversation</span></span> | <span data-ttu-id="e1385-146">30</span><span class="sxs-lookup"><span data-stu-id="e1385-146">30</span></span> | <span data-ttu-id="e1385-147">60</span><span class="sxs-lookup"><span data-stu-id="e1385-147">60</span></span> |
| <span data-ttu-id="e1385-148">An Unterhaltung senden</span><span class="sxs-lookup"><span data-stu-id="e1385-148">Send to Conversation</span></span> | <span data-ttu-id="e1385-149">3600</span><span class="sxs-lookup"><span data-stu-id="e1385-149">3600</span></span> | <span data-ttu-id="e1385-150">1800</span><span class="sxs-lookup"><span data-stu-id="e1385-150">1800</span></span> |
| <span data-ttu-id="e1385-151">Unterhaltung erstellen</span><span class="sxs-lookup"><span data-stu-id="e1385-151">Create Conversation</span></span> | <span data-ttu-id="e1385-152">1</span><span class="sxs-lookup"><span data-stu-id="e1385-152">1</span></span> | <span data-ttu-id="e1385-153">7 </span><span class="sxs-lookup"><span data-stu-id="e1385-153">7</span></span> |
| <span data-ttu-id="e1385-154">Unterhaltung erstellen</span><span class="sxs-lookup"><span data-stu-id="e1385-154">Create Conversation</span></span> | <span data-ttu-id="e1385-155">2</span><span class="sxs-lookup"><span data-stu-id="e1385-155">2</span></span> | <span data-ttu-id="e1385-156">8 </span><span class="sxs-lookup"><span data-stu-id="e1385-156">8</span></span> |
| <span data-ttu-id="e1385-157">Unterhaltung erstellen</span><span class="sxs-lookup"><span data-stu-id="e1385-157">Create Conversation</span></span> | <span data-ttu-id="e1385-158">30</span><span class="sxs-lookup"><span data-stu-id="e1385-158">30</span></span> | <span data-ttu-id="e1385-159">60</span><span class="sxs-lookup"><span data-stu-id="e1385-159">60</span></span> |
| <span data-ttu-id="e1385-160">Unterhaltung erstellen</span><span class="sxs-lookup"><span data-stu-id="e1385-160">Create Conversation</span></span> | <span data-ttu-id="e1385-161">3600</span><span class="sxs-lookup"><span data-stu-id="e1385-161">3600</span></span> | <span data-ttu-id="e1385-162">1800</span><span class="sxs-lookup"><span data-stu-id="e1385-162">1800</span></span> |
| <span data-ttu-id="e1385-163">Get Conversation Members</span><span class="sxs-lookup"><span data-stu-id="e1385-163">Get Conversation Members</span></span>| <span data-ttu-id="e1385-164">1</span><span class="sxs-lookup"><span data-stu-id="e1385-164">1</span></span> | <span data-ttu-id="e1385-165">14 </span><span class="sxs-lookup"><span data-stu-id="e1385-165">14</span></span> |
| <span data-ttu-id="e1385-166">Get Conversation Members</span><span class="sxs-lookup"><span data-stu-id="e1385-166">Get Conversation Members</span></span>| <span data-ttu-id="e1385-167">2</span><span class="sxs-lookup"><span data-stu-id="e1385-167">2</span></span> | <span data-ttu-id="e1385-168">16 </span><span class="sxs-lookup"><span data-stu-id="e1385-168">16</span></span> |
| <span data-ttu-id="e1385-169">Get Conversation Members</span><span class="sxs-lookup"><span data-stu-id="e1385-169">Get Conversation Members</span></span>| <span data-ttu-id="e1385-170">30</span><span class="sxs-lookup"><span data-stu-id="e1385-170">30</span></span> | <span data-ttu-id="e1385-171">120</span><span class="sxs-lookup"><span data-stu-id="e1385-171">120</span></span> |
| <span data-ttu-id="e1385-172">Get Conversation Members</span><span class="sxs-lookup"><span data-stu-id="e1385-172">Get Conversation Members</span></span>| <span data-ttu-id="e1385-173">3600</span><span class="sxs-lookup"><span data-stu-id="e1385-173">3600</span></span> | <span data-ttu-id="e1385-174">3600</span><span class="sxs-lookup"><span data-stu-id="e1385-174">3600</span></span> |
| <span data-ttu-id="e1385-175">Unterhaltungen erhalten</span><span class="sxs-lookup"><span data-stu-id="e1385-175">Get Conversations</span></span> | <span data-ttu-id="e1385-176">1</span><span class="sxs-lookup"><span data-stu-id="e1385-176">1</span></span> | <span data-ttu-id="e1385-177">14 </span><span class="sxs-lookup"><span data-stu-id="e1385-177">14</span></span> |
| <span data-ttu-id="e1385-178">Unterhaltungen erhalten</span><span class="sxs-lookup"><span data-stu-id="e1385-178">Get Conversations</span></span> | <span data-ttu-id="e1385-179">2</span><span class="sxs-lookup"><span data-stu-id="e1385-179">2</span></span> | <span data-ttu-id="e1385-180">16 </span><span class="sxs-lookup"><span data-stu-id="e1385-180">16</span></span> |
| <span data-ttu-id="e1385-181">Unterhaltungen erhalten</span><span class="sxs-lookup"><span data-stu-id="e1385-181">Get Conversations</span></span> | <span data-ttu-id="e1385-182">30</span><span class="sxs-lookup"><span data-stu-id="e1385-182">30</span></span> | <span data-ttu-id="e1385-183">120</span><span class="sxs-lookup"><span data-stu-id="e1385-183">120</span></span> |
| <span data-ttu-id="e1385-184">Unterhaltungen erhalten</span><span class="sxs-lookup"><span data-stu-id="e1385-184">Get Conversations</span></span> | <span data-ttu-id="e1385-185">3600</span><span class="sxs-lookup"><span data-stu-id="e1385-185">3600</span></span> | <span data-ttu-id="e1385-186">3600</span><span class="sxs-lookup"><span data-stu-id="e1385-186">3600</span></span> |

>[!NOTE]
> <span data-ttu-id="e1385-187">Frühere Versionen `TeamsInfo.getMembers` von und `TeamsInfo.GetMembersAsync` APIs sind veraltet.</span><span class="sxs-lookup"><span data-stu-id="e1385-187">Previous versions of `TeamsInfo.getMembers` and `TeamsInfo.GetMembersAsync` APIs are being deprecated.</span></span> <span data-ttu-id="e1385-188">Sie werden auf 5 Anforderungen pro Minute gedrosselt und geben maximal 10.000 Mitglieder pro Team zurück.</span><span class="sxs-lookup"><span data-stu-id="e1385-188">They will be throttled to 5 requests per minute and return a maximum of 10K members per team.</span></span> <span data-ttu-id="e1385-189">Informationen zum Aktualisieren Ihres Bot Framework SDK und des Codes zur Verwendung der neuesten paginierten API-Endpunkte finden Sie unter [Bot-API-Änderungen für Team- und Chatmitglieder.](../../resources/team-chat-member-api-changes.md)</span><span class="sxs-lookup"><span data-stu-id="e1385-189">To update your Bot Framework SDK and the code to use the latest paginated API endpoints, see [Bot API changes for team and chat members](../../resources/team-chat-member-api-changes.md).</span></span>

## <a name="per-thread-limit-for-all-bots"></a><span data-ttu-id="e1385-190">Grenzwert pro Thread für alle Bots</span><span class="sxs-lookup"><span data-stu-id="e1385-190">Per thread limit for all bots</span></span>

<span data-ttu-id="e1385-191">Dieser Grenzwert steuert den Datenverkehr, den alle Bots über eine einzelne Unterhaltung generieren dürfen.</span><span class="sxs-lookup"><span data-stu-id="e1385-191">This limit controls the traffic that all bots are allowed to generate across a single conversation.</span></span> <span data-ttu-id="e1385-192">Eine Unterhaltung hier ist 1:1 zwischen Bot und Benutzer, einem Gruppenchat oder einem Kanal in einem Team.</span><span class="sxs-lookup"><span data-stu-id="e1385-192">A conversation here is 1:1 between bot and user, a group-chat, or a channel in a team.</span></span>

| <span data-ttu-id="e1385-193">**Szenario**</span><span class="sxs-lookup"><span data-stu-id="e1385-193">**Scenario**</span></span> | <span data-ttu-id="e1385-194">**Zeitraum (Sek.)**</span><span class="sxs-lookup"><span data-stu-id="e1385-194">**Time-period (sec)**</span></span> | <span data-ttu-id="e1385-195">**Maximal zulässige Vorgänge**</span><span class="sxs-lookup"><span data-stu-id="e1385-195">**Max allowed operations**</span></span> |
| --- | --- | --- |
| <span data-ttu-id="e1385-196">An Unterhaltung senden</span><span class="sxs-lookup"><span data-stu-id="e1385-196">Send to Conversation</span></span> | <span data-ttu-id="e1385-197">1</span><span class="sxs-lookup"><span data-stu-id="e1385-197">1</span></span> | <span data-ttu-id="e1385-198">14 </span><span class="sxs-lookup"><span data-stu-id="e1385-198">14</span></span> |
| <span data-ttu-id="e1385-199">An Unterhaltung senden</span><span class="sxs-lookup"><span data-stu-id="e1385-199">Send to Conversation</span></span> | <span data-ttu-id="e1385-200">2</span><span class="sxs-lookup"><span data-stu-id="e1385-200">2</span></span> | <span data-ttu-id="e1385-201">16 </span><span class="sxs-lookup"><span data-stu-id="e1385-201">16</span></span> |
| <span data-ttu-id="e1385-202">Unterhaltung erstellen</span><span class="sxs-lookup"><span data-stu-id="e1385-202">Create Conversation</span></span> | <span data-ttu-id="e1385-203">1</span><span class="sxs-lookup"><span data-stu-id="e1385-203">1</span></span> | <span data-ttu-id="e1385-204">14 </span><span class="sxs-lookup"><span data-stu-id="e1385-204">14</span></span> |
| <span data-ttu-id="e1385-205">Unterhaltung erstellen</span><span class="sxs-lookup"><span data-stu-id="e1385-205">Create Conversation</span></span> | <span data-ttu-id="e1385-206">2</span><span class="sxs-lookup"><span data-stu-id="e1385-206">2</span></span> | <span data-ttu-id="e1385-207">16 </span><span class="sxs-lookup"><span data-stu-id="e1385-207">16</span></span> |
| <span data-ttu-id="e1385-208">CreateConversation</span><span class="sxs-lookup"><span data-stu-id="e1385-208">CreateConversation</span></span>| <span data-ttu-id="e1385-209">1</span><span class="sxs-lookup"><span data-stu-id="e1385-209">1</span></span> | <span data-ttu-id="e1385-210">14 </span><span class="sxs-lookup"><span data-stu-id="e1385-210">14</span></span> |
| <span data-ttu-id="e1385-211">CreateConversation</span><span class="sxs-lookup"><span data-stu-id="e1385-211">CreateConversation</span></span>| <span data-ttu-id="e1385-212">2</span><span class="sxs-lookup"><span data-stu-id="e1385-212">2</span></span> | <span data-ttu-id="e1385-213">16 </span><span class="sxs-lookup"><span data-stu-id="e1385-213">16</span></span> |
| <span data-ttu-id="e1385-214">Get Conversation Members</span><span class="sxs-lookup"><span data-stu-id="e1385-214">Get Conversation Members</span></span>| <span data-ttu-id="e1385-215">1</span><span class="sxs-lookup"><span data-stu-id="e1385-215">1</span></span> | <span data-ttu-id="e1385-216">28</span><span class="sxs-lookup"><span data-stu-id="e1385-216">28</span></span> |
| <span data-ttu-id="e1385-217">Get Conversation Members</span><span class="sxs-lookup"><span data-stu-id="e1385-217">Get Conversation Members</span></span>| <span data-ttu-id="e1385-218">2</span><span class="sxs-lookup"><span data-stu-id="e1385-218">2</span></span> | <span data-ttu-id="e1385-219">32</span><span class="sxs-lookup"><span data-stu-id="e1385-219">32</span></span> |
| <span data-ttu-id="e1385-220">Unterhaltungen erhalten</span><span class="sxs-lookup"><span data-stu-id="e1385-220">Get Conversations</span></span> | <span data-ttu-id="e1385-221">1</span><span class="sxs-lookup"><span data-stu-id="e1385-221">1</span></span> | <span data-ttu-id="e1385-222">28</span><span class="sxs-lookup"><span data-stu-id="e1385-222">28</span></span> |
| <span data-ttu-id="e1385-223">Unterhaltungen erhalten</span><span class="sxs-lookup"><span data-stu-id="e1385-223">Get Conversations</span></span> | <span data-ttu-id="e1385-224">2</span><span class="sxs-lookup"><span data-stu-id="e1385-224">2</span></span> | <span data-ttu-id="e1385-225">32</span><span class="sxs-lookup"><span data-stu-id="e1385-225">32</span></span> |
