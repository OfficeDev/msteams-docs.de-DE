---
title: Optimieren eines Bots mit Ratenbegrenzung in Teams
description: Begrenzung der Raten und bewährte Methoden in Microsoft Teams
ms.topic: conceptual
localization_priority: Normal
keywords: Teams-Bots – Begrenzung der Raten
ms.openlocfilehash: 41070bec7905c7003afb917aedcdd08495418602
ms.sourcegitcommit: e327c9766dfa05abb468cdc71319e3cba7c6c79f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/14/2021
ms.locfileid: "53428695"
---
# <a name="optimize-your-bot-with-rate-limiting-in-teams"></a><span data-ttu-id="9163f-104">Optimieren eines Bots mit Ratenbegrenzung in Teams</span><span class="sxs-lookup"><span data-stu-id="9163f-104">Optimize your bot with rate limiting in Teams</span></span>

<span data-ttu-id="9163f-105">Die Geschwindigkeitsbegrenzung ist eine Methode, um Nachrichten auf eine bestimmte maximale Häufigkeit zu beschränken.</span><span class="sxs-lookup"><span data-stu-id="9163f-105">Rate limiting is a method to limit messages to a certain maximum frequency.</span></span> <span data-ttu-id="9163f-106">Im Allgemeinen muss Ihre Anwendung die Anzahl der Nachrichten beschränken, die sie an einen einzelnen Chat oder eine Kanalunterhaltung sendet.</span><span class="sxs-lookup"><span data-stu-id="9163f-106">As a general principle, your application must limit the number of messages it posts to an individual chat or channel conversation.</span></span> <span data-ttu-id="9163f-107">Dadurch wird eine optimale Benutzererfahrung sichergestellt, und Nachrichten werden Ihren Benutzern nicht als Spam angezeigt.</span><span class="sxs-lookup"><span data-stu-id="9163f-107">This ensures an optimal experience and messages do not appear as spam to your users.</span></span>

<span data-ttu-id="9163f-108">Um Microsoft Teams und seine Benutzer zu schützen, bieten die Bot-APIs ein Preislimit für eingehende Anforderungen.</span><span class="sxs-lookup"><span data-stu-id="9163f-108">To protect Microsoft Teams and its users, the bot APIs provide a rate limit for incoming requests.</span></span> <span data-ttu-id="9163f-109">Apps, die diesen Grenzwert überschreiten, erhalten einen `HTTP 429 Too Many Requests` Fehlerstatus.</span><span class="sxs-lookup"><span data-stu-id="9163f-109">Apps that go over this limit receive an `HTTP 429 Too Many Requests` error status.</span></span> <span data-ttu-id="9163f-110">Alle Anforderungen unterliegen derselben Richtlinie für die Begrenzung der Raten, einschließlich des Sendens von Nachrichten, Kanalenumerationen und Listenabrufen.</span><span class="sxs-lookup"><span data-stu-id="9163f-110">All requests are subject to the same rate limiting policy, including sending messages, channel enumerations, and roster fetches.</span></span>

<span data-ttu-id="9163f-111">Da sich die genauen Werte von Zinslimits ändern können, muss Ihre Anwendung das entsprechende Backoff-Verhalten implementieren, wenn die API `HTTP 429 Too Many Requests` zurückgibt.</span><span class="sxs-lookup"><span data-stu-id="9163f-111">As the exact values of rate limits are subject to change, your application must implement the appropriate backoff behavior when the API returns `HTTP 429 Too Many Requests`.</span></span>

## <a name="handle-rate-limits"></a><span data-ttu-id="9163f-112">Behandeln von Ratenlimits</span><span class="sxs-lookup"><span data-stu-id="9163f-112">Handle rate limits</span></span>

<span data-ttu-id="9163f-113">Beim Ausgeben eines Bot Builder SDK-Vorgangs können Sie den Statuscode behandeln `Microsoft.Rest.HttpOperationException` und überprüfen.</span><span class="sxs-lookup"><span data-stu-id="9163f-113">When issuing a Bot Builder SDK operation, you can handle `Microsoft.Rest.HttpOperationException` and check for the status code.</span></span>

<span data-ttu-id="9163f-114">Der folgende Code zeigt ein Beispiel für die Behandlung von Ratengrenzen:</span><span class="sxs-lookup"><span data-stu-id="9163f-114">The following code shows an example of handling rate limits:</span></span>

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

<span data-ttu-id="9163f-115">Nachdem Sie die Ratenlimits für Bots behandelt haben, können Sie `HTTP 429` Antworten mithilfe eines exponentiellen Backoffs verarbeiten.</span><span class="sxs-lookup"><span data-stu-id="9163f-115">After you handle rate limits for bots, you can handle `HTTP 429` responses using an exponential backoff.</span></span>

## <a name="handle-http-429-responses"></a><span data-ttu-id="9163f-116">Behandeln von `HTTP 429` Antworten</span><span class="sxs-lookup"><span data-stu-id="9163f-116">Handle `HTTP 429` responses</span></span>

<span data-ttu-id="9163f-117">Im Allgemeinen müssen Sie einfache Vorsichtsmaßnahmen ergreifen, um antworten zu `HTTP 429` vermeiden.</span><span class="sxs-lookup"><span data-stu-id="9163f-117">In general, you must take simple precautions to avoid receiving `HTTP 429` responses.</span></span> <span data-ttu-id="9163f-118">Vermeiden Sie beispielsweise das Ausstellen mehrerer Anforderungen an dieselbe persönliche Unterhaltung oder Kanalunterhaltung.</span><span class="sxs-lookup"><span data-stu-id="9163f-118">For example, avoid issuing multiple requests to the same personal or channel conversation.</span></span> <span data-ttu-id="9163f-119">Erstellen Sie stattdessen einen Batch der API-Anforderungen.</span><span class="sxs-lookup"><span data-stu-id="9163f-119">Instead, create a batch of the API requests.</span></span>

<span data-ttu-id="9163f-120">Die Verwendung eines exponentiellen Backoffs mit einem zufälligen Jitter ist die empfohlene Methode zum Behandeln von 429s.</span><span class="sxs-lookup"><span data-stu-id="9163f-120">Using an exponential backoff with a random jitter is the recommended way to handle 429s.</span></span> <span data-ttu-id="9163f-121">Dadurch wird sichergestellt, dass mehrere Anforderungen bei Wiederholungsversuche keine Konflikte auslösen.</span><span class="sxs-lookup"><span data-stu-id="9163f-121">This ensures that multiple requests do not introduce collisions on retries.</span></span>

<span data-ttu-id="9163f-122">Nachdem Sie Antworten behandelt `HTTP 429` haben, können Sie das Beispiel zum Erkennen vorübergehender Ausnahmen durchgehen.</span><span class="sxs-lookup"><span data-stu-id="9163f-122">After you handle `HTTP 429` responses, you can go through the example for detecting transient exceptions.</span></span>

> [!NOTE]
> <span data-ttu-id="9163f-123">Zusätzlich zur Wiederholung des Fehlercodes **429** müssen auch die Fehlercodes **412,** **502** und **504** wiederholt werden.</span><span class="sxs-lookup"><span data-stu-id="9163f-123">In addition to retrying error code **429**, error codes **412**, **502**, and **504** must also be retried.</span></span>

## <a name="detect-transient-exceptions-example"></a><span data-ttu-id="9163f-124">Beispiel zum Erkennen vorübergehender Ausnahmen</span><span class="sxs-lookup"><span data-stu-id="9163f-124">Detect transient exceptions example</span></span>

<span data-ttu-id="9163f-125">Der folgende Code zeigt ein Beispiel für die Verwendung eines exponentiellen Backoffs mithilfe des Vorübergehenden Anwendungsblocks für die Fehlerbehandlung:</span><span class="sxs-lookup"><span data-stu-id="9163f-125">The following code shows an example of using exponential backoff using the transient fault handling application block:</span></span>

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

<span data-ttu-id="9163f-126">Sie können Backoff- und Wiederholungsversuche mithilfe [der vorübergehenden Fehlerbehandlung](/previous-versions/msp-n-p/hh675232%28v%3dpandp.10%29)durchführen.</span><span class="sxs-lookup"><span data-stu-id="9163f-126">You can perform backoff and retries using [transient fault handling](/previous-versions/msp-n-p/hh675232%28v%3dpandp.10%29).</span></span> <span data-ttu-id="9163f-127">Richtlinien zum Abrufen und Installieren des NuGet-Pakets finden Sie unter [Hinzufügen des Vorübergehenden Fehlerbehandlungsanwendungsblocks zu Ihrer Lösung.](/previous-versions/msp-n-p/dn440719(v=pandp.60)?redirectedfrom=MSDN)</span><span class="sxs-lookup"><span data-stu-id="9163f-127">For guidelines on obtaining and installing the NuGet package, see [adding the transient fault handling application block to your solution](/previous-versions/msp-n-p/dn440719(v=pandp.60)?redirectedfrom=MSDN).</span></span> <span data-ttu-id="9163f-128">Siehe auch [vorübergehende Fehlerbehandlung.](/azure/architecture/best-practices/transient-faults)</span><span class="sxs-lookup"><span data-stu-id="9163f-128">See also [transient fault handling](/azure/architecture/best-practices/transient-faults).</span></span>

<span data-ttu-id="9163f-129">Nachdem Sie das Beispiel zum Erkennen vorübergehender Ausnahmen durchgehen, durchlaufen Sie das exponentielle Backoff-Beispiel.</span><span class="sxs-lookup"><span data-stu-id="9163f-129">After you go through the example for detecting transient exceptions, go through the exponential backoff example.</span></span> <span data-ttu-id="9163f-130">Sie können exponentielles Backoff verwenden, anstatt fehlerweise erneut zu versuchen.</span><span class="sxs-lookup"><span data-stu-id="9163f-130">You can use exponential backoff instead of retrying on failures.</span></span>

## <a name="backoff-example"></a><span data-ttu-id="9163f-131">Backoff-Beispiel</span><span class="sxs-lookup"><span data-stu-id="9163f-131">Backoff example</span></span>

<span data-ttu-id="9163f-132">Zusätzlich zum Erkennen von Zinslimits können Sie auch ein exponentielles Backoff ausführen.</span><span class="sxs-lookup"><span data-stu-id="9163f-132">In addition to detecting rate limits, you can also perform an exponential backoff.</span></span>

<span data-ttu-id="9163f-133">Der folgende Code zeigt ein Beispiel für einen exponentiellen Backoff:</span><span class="sxs-lookup"><span data-stu-id="9163f-133">The following code shows an example of exponential backoff:</span></span>

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

<span data-ttu-id="9163f-134">Sie können auch eine `System.Action` Methodenausführung mit der in diesem Abschnitt beschriebenen Wiederholungsrichtlinie ausführen.</span><span class="sxs-lookup"><span data-stu-id="9163f-134">You can also perform a `System.Action` method execution with the retry policy described in this section.</span></span> <span data-ttu-id="9163f-135">In der referenzierten Bibliothek können Sie auch ein festes Intervall oder einen linearen Backoff-Mechanismus angeben.</span><span class="sxs-lookup"><span data-stu-id="9163f-135">The referenced library also allows you to specify a fixed interval or a linear backoff mechanism.</span></span>

<span data-ttu-id="9163f-136">Store den Wert und die Strategie in einer Konfigurationsdatei, um die Werte zur Laufzeit zu optimieren und zu optimieren.</span><span class="sxs-lookup"><span data-stu-id="9163f-136">Store the value and strategy in a configuration file to fine-tune and tweak values at run time.</span></span>

<span data-ttu-id="9163f-137">Weitere Informationen finden Sie unter [Wiederholungsmuster.](/azure/architecture/patterns/retry)</span><span class="sxs-lookup"><span data-stu-id="9163f-137">For more information, see [retry patterns](/azure/architecture/patterns/retry).</span></span>

<span data-ttu-id="9163f-138">Sie können die Ratenbegrenzung auch mithilfe des Grenzwerts pro Bot und Thread behandeln.</span><span class="sxs-lookup"><span data-stu-id="9163f-138">You can also handle rate limit using the per bot per thread limit.</span></span>

## <a name="per-bot-per-thread-limit"></a><span data-ttu-id="9163f-139">Pro Bot pro Threadlimit</span><span class="sxs-lookup"><span data-stu-id="9163f-139">Per bot per thread limit</span></span>

<span data-ttu-id="9163f-140">Der Grenzwert pro Bot und Thread steuert den Datenverkehr, den ein Bot in einer einzigen Unterhaltung generieren darf.</span><span class="sxs-lookup"><span data-stu-id="9163f-140">The per bot per thread limit controls the traffic that a bot is allowed to generate in a single conversation.</span></span> <span data-ttu-id="9163f-141">Eine Unterhaltung ist 1:1 zwischen Bot und Benutzer, einem Gruppenchat oder einem Kanal in einem Team.</span><span class="sxs-lookup"><span data-stu-id="9163f-141">A conversation is 1:1 between bot and user, a group chat, or a channel in a team.</span></span> <span data-ttu-id="9163f-142">Wenn die Anwendung also eine Bot-Nachricht an jeden Benutzer sendet, wird der Threadgrenzwert nicht gedrosselt.</span><span class="sxs-lookup"><span data-stu-id="9163f-142">So, if the application sends one bot message to each user, the thread limit does not throttle.</span></span>

>[!NOTE]
> * <span data-ttu-id="9163f-143">Das Threadlimit von 3600 Sekunden und 1800 Vorgängen gilt nur, wenn mehrere Bot-Nachrichten an einen einzelnen Benutzer gesendet werden.</span><span class="sxs-lookup"><span data-stu-id="9163f-143">The thread limit of 3600 seconds and 1800 operations applies only if multiple bot messages are sent to a single user.</span></span> 
> * <span data-ttu-id="9163f-144">Das globale Limit pro App und Mandant beträgt 50 Anforderungen pro Sekunde (RPS).</span><span class="sxs-lookup"><span data-stu-id="9163f-144">The global limit per app per tenant is 50 Requests Per Second (RPS).</span></span> <span data-ttu-id="9163f-145">Daher darf die Gesamtzahl der Botnachrichten pro Sekunde das Threadlimit nicht überschreiten.</span><span class="sxs-lookup"><span data-stu-id="9163f-145">Hence, the total number of bot messages per second must not cross the thread limit.</span></span>
> * <span data-ttu-id="9163f-146">Das Teilen von Nachrichten auf Dienstebene führt zu einem höheren RPS als erwartet.</span><span class="sxs-lookup"><span data-stu-id="9163f-146">Message splitting at the service level results in higher than expected RPS.</span></span> <span data-ttu-id="9163f-147">Wenn Sie sich Sorgen machen, die Grenzwerte zu erreichen, müssen Sie die [Backoff-Strategie](#backoff-example)implementieren.</span><span class="sxs-lookup"><span data-stu-id="9163f-147">If you are concerned about approaching the limits, you must implement the [backoff strategy](#backoff-example).</span></span> <span data-ttu-id="9163f-148">Die in diesem Abschnitt angegebenen Werte dienen nur der Schätzung.</span><span class="sxs-lookup"><span data-stu-id="9163f-148">The values provided in this section are for estimation only.</span></span>

<span data-ttu-id="9163f-149">Die folgende Tabelle enthält die Grenzwerte pro Bot und Thread:</span><span class="sxs-lookup"><span data-stu-id="9163f-149">The following table provides the per bot per thread limits:</span></span>

| <span data-ttu-id="9163f-150">Szenario</span><span class="sxs-lookup"><span data-stu-id="9163f-150">Scenario</span></span> | <span data-ttu-id="9163f-151">Zeitraum in Sekunden</span><span class="sxs-lookup"><span data-stu-id="9163f-151">Time period in seconds</span></span> | <span data-ttu-id="9163f-152">Maximal zulässige Vorgänge</span><span class="sxs-lookup"><span data-stu-id="9163f-152">Maximum allowed operations</span></span> |
| --- | --- | --- |
| <span data-ttu-id="9163f-153">An Unterhaltung senden</span><span class="sxs-lookup"><span data-stu-id="9163f-153">Send to conversation</span></span> | <span data-ttu-id="9163f-154">1</span><span class="sxs-lookup"><span data-stu-id="9163f-154">1</span></span> | <span data-ttu-id="9163f-155">7 </span><span class="sxs-lookup"><span data-stu-id="9163f-155">7</span></span> |
| <span data-ttu-id="9163f-156">An Unterhaltung senden</span><span class="sxs-lookup"><span data-stu-id="9163f-156">Send to conversation</span></span> | <span data-ttu-id="9163f-157">2</span><span class="sxs-lookup"><span data-stu-id="9163f-157">2</span></span> | <span data-ttu-id="9163f-158">8 </span><span class="sxs-lookup"><span data-stu-id="9163f-158">8</span></span> |
| <span data-ttu-id="9163f-159">An Unterhaltung senden</span><span class="sxs-lookup"><span data-stu-id="9163f-159">Send to conversation</span></span> | <span data-ttu-id="9163f-160">30</span><span class="sxs-lookup"><span data-stu-id="9163f-160">30</span></span> | <span data-ttu-id="9163f-161">60</span><span class="sxs-lookup"><span data-stu-id="9163f-161">60</span></span> |
| <span data-ttu-id="9163f-162">An Unterhaltung senden</span><span class="sxs-lookup"><span data-stu-id="9163f-162">Send to conversation</span></span> | <span data-ttu-id="9163f-163">3600</span><span class="sxs-lookup"><span data-stu-id="9163f-163">3600</span></span> | <span data-ttu-id="9163f-164">1800</span><span class="sxs-lookup"><span data-stu-id="9163f-164">1800</span></span> |
| <span data-ttu-id="9163f-165">Unterhaltung erstellen</span><span class="sxs-lookup"><span data-stu-id="9163f-165">Create conversation</span></span> | <span data-ttu-id="9163f-166">1</span><span class="sxs-lookup"><span data-stu-id="9163f-166">1</span></span> | <span data-ttu-id="9163f-167">7 </span><span class="sxs-lookup"><span data-stu-id="9163f-167">7</span></span> |
| <span data-ttu-id="9163f-168">Unterhaltung erstellen</span><span class="sxs-lookup"><span data-stu-id="9163f-168">Create conversation</span></span> | <span data-ttu-id="9163f-169">2</span><span class="sxs-lookup"><span data-stu-id="9163f-169">2</span></span> | <span data-ttu-id="9163f-170">8 </span><span class="sxs-lookup"><span data-stu-id="9163f-170">8</span></span> |
| <span data-ttu-id="9163f-171">Unterhaltung erstellen</span><span class="sxs-lookup"><span data-stu-id="9163f-171">Create conversation</span></span> | <span data-ttu-id="9163f-172">30</span><span class="sxs-lookup"><span data-stu-id="9163f-172">30</span></span> | <span data-ttu-id="9163f-173">60</span><span class="sxs-lookup"><span data-stu-id="9163f-173">60</span></span> |
| <span data-ttu-id="9163f-174">Unterhaltung erstellen</span><span class="sxs-lookup"><span data-stu-id="9163f-174">Create conversation</span></span> | <span data-ttu-id="9163f-175">3600</span><span class="sxs-lookup"><span data-stu-id="9163f-175">3600</span></span> | <span data-ttu-id="9163f-176">1800</span><span class="sxs-lookup"><span data-stu-id="9163f-176">1800</span></span> |
| <span data-ttu-id="9163f-177">Abrufen von Unterhaltungsmitgliedern</span><span class="sxs-lookup"><span data-stu-id="9163f-177">Get conversation members</span></span>| <span data-ttu-id="9163f-178">1</span><span class="sxs-lookup"><span data-stu-id="9163f-178">1</span></span> | <span data-ttu-id="9163f-179">14 </span><span class="sxs-lookup"><span data-stu-id="9163f-179">14</span></span> |
| <span data-ttu-id="9163f-180">Abrufen von Unterhaltungsmitgliedern</span><span class="sxs-lookup"><span data-stu-id="9163f-180">Get conversation members</span></span>| <span data-ttu-id="9163f-181">2</span><span class="sxs-lookup"><span data-stu-id="9163f-181">2</span></span> | <span data-ttu-id="9163f-182">16 </span><span class="sxs-lookup"><span data-stu-id="9163f-182">16</span></span> |
| <span data-ttu-id="9163f-183">Abrufen von Unterhaltungsmitgliedern</span><span class="sxs-lookup"><span data-stu-id="9163f-183">Get conversation members</span></span>| <span data-ttu-id="9163f-184">30</span><span class="sxs-lookup"><span data-stu-id="9163f-184">30</span></span> | <span data-ttu-id="9163f-185">120</span><span class="sxs-lookup"><span data-stu-id="9163f-185">120</span></span> |
| <span data-ttu-id="9163f-186">Abrufen von Unterhaltungsmitgliedern</span><span class="sxs-lookup"><span data-stu-id="9163f-186">Get conversation members</span></span>| <span data-ttu-id="9163f-187">3600</span><span class="sxs-lookup"><span data-stu-id="9163f-187">3600</span></span> | <span data-ttu-id="9163f-188">3600</span><span class="sxs-lookup"><span data-stu-id="9163f-188">3600</span></span> |
| <span data-ttu-id="9163f-189">Unterhaltungen abrufen</span><span class="sxs-lookup"><span data-stu-id="9163f-189">Get conversations</span></span> | <span data-ttu-id="9163f-190">1</span><span class="sxs-lookup"><span data-stu-id="9163f-190">1</span></span> | <span data-ttu-id="9163f-191">14 </span><span class="sxs-lookup"><span data-stu-id="9163f-191">14</span></span> |
| <span data-ttu-id="9163f-192">Unterhaltungen abrufen</span><span class="sxs-lookup"><span data-stu-id="9163f-192">Get conversations</span></span> | <span data-ttu-id="9163f-193">2</span><span class="sxs-lookup"><span data-stu-id="9163f-193">2</span></span> | <span data-ttu-id="9163f-194">16 </span><span class="sxs-lookup"><span data-stu-id="9163f-194">16</span></span> |
| <span data-ttu-id="9163f-195">Unterhaltungen abrufen</span><span class="sxs-lookup"><span data-stu-id="9163f-195">Get conversations</span></span> | <span data-ttu-id="9163f-196">30</span><span class="sxs-lookup"><span data-stu-id="9163f-196">30</span></span> | <span data-ttu-id="9163f-197">120</span><span class="sxs-lookup"><span data-stu-id="9163f-197">120</span></span> |
| <span data-ttu-id="9163f-198">Unterhaltungen abrufen</span><span class="sxs-lookup"><span data-stu-id="9163f-198">Get conversations</span></span> | <span data-ttu-id="9163f-199">3600</span><span class="sxs-lookup"><span data-stu-id="9163f-199">3600</span></span> | <span data-ttu-id="9163f-200">3600</span><span class="sxs-lookup"><span data-stu-id="9163f-200">3600</span></span> |

>[!NOTE]
> <span data-ttu-id="9163f-201">Frühere Versionen `TeamsInfo.getMembers` von und `TeamsInfo.GetMembersAsync` APIs sind veraltet.</span><span class="sxs-lookup"><span data-stu-id="9163f-201">Previous versions of `TeamsInfo.getMembers` and `TeamsInfo.GetMembersAsync` APIs are being deprecated.</span></span> <span data-ttu-id="9163f-202">Sie werden auf fünf Anforderungen pro Minute gedrosselt und geben maximal 10.000 Mitglieder pro Team zurück.</span><span class="sxs-lookup"><span data-stu-id="9163f-202">They are throttled to five requests per minute and return a maximum of 10K members per team.</span></span> <span data-ttu-id="9163f-203">Informationen zum Aktualisieren Ihres Bot Framework SDK und des Codes für die Verwendung der neuesten paginierten API-Endpunkte finden Sie unter [Bot-API-Änderungen für Team- und Chatmitglieder.](../../resources/team-chat-member-api-changes.md)</span><span class="sxs-lookup"><span data-stu-id="9163f-203">To update your Bot Framework SDK and the code to use the latest paginated API endpoints, see [Bot API changes for team and chat members](../../resources/team-chat-member-api-changes.md).</span></span>

<span data-ttu-id="9163f-204">Sie können die Ratenbegrenzung auch mithilfe des Grenzwerts pro Thread für alle Bots behandeln.</span><span class="sxs-lookup"><span data-stu-id="9163f-204">You can also handle rate limit using the per thread limit for all bots.</span></span>

## <a name="per-thread-limit-for-all-bots"></a><span data-ttu-id="9163f-205">Grenzwert pro Thread für alle Bots</span><span class="sxs-lookup"><span data-stu-id="9163f-205">Per thread limit for all bots</span></span>

<span data-ttu-id="9163f-206">Der Grenzwert pro Thread für alle Bots steuert den Datenverkehr, den alle Bots in einer einzigen Unterhaltung generieren dürfen.</span><span class="sxs-lookup"><span data-stu-id="9163f-206">The per thread limit for all bots controls the traffic that all bots are allowed to generate across a single conversation.</span></span> <span data-ttu-id="9163f-207">Eine Unterhaltung hier ist 1:1 zwischen Bot und Benutzer, einem Gruppenchat oder einem Kanal in einem Team.</span><span class="sxs-lookup"><span data-stu-id="9163f-207">A conversation here is 1:1 between bot and user, a group chat, or a channel in a team.</span></span>

<span data-ttu-id="9163f-208">Die folgende Tabelle enthält den Grenzwert pro Thread für alle Bots:</span><span class="sxs-lookup"><span data-stu-id="9163f-208">The following table provides the per thread limit for all bots:</span></span>

| <span data-ttu-id="9163f-209">Szenario</span><span class="sxs-lookup"><span data-stu-id="9163f-209">Scenario</span></span> | <span data-ttu-id="9163f-210">Zeitraum in Sekunden</span><span class="sxs-lookup"><span data-stu-id="9163f-210">Time period in seconds</span></span> | <span data-ttu-id="9163f-211">Maximal zulässige Vorgänge</span><span class="sxs-lookup"><span data-stu-id="9163f-211">Maximum allowed operations</span></span> |
| --- | --- | --- |
| <span data-ttu-id="9163f-212">An Unterhaltung senden</span><span class="sxs-lookup"><span data-stu-id="9163f-212">Send to conversation</span></span> | <span data-ttu-id="9163f-213">1</span><span class="sxs-lookup"><span data-stu-id="9163f-213">1</span></span> | <span data-ttu-id="9163f-214">14 </span><span class="sxs-lookup"><span data-stu-id="9163f-214">14</span></span> |
| <span data-ttu-id="9163f-215">An Unterhaltung senden</span><span class="sxs-lookup"><span data-stu-id="9163f-215">Send to conversation</span></span> | <span data-ttu-id="9163f-216">2</span><span class="sxs-lookup"><span data-stu-id="9163f-216">2</span></span> | <span data-ttu-id="9163f-217">16 </span><span class="sxs-lookup"><span data-stu-id="9163f-217">16</span></span> |
| <span data-ttu-id="9163f-218">Unterhaltung erstellen</span><span class="sxs-lookup"><span data-stu-id="9163f-218">Create conversation</span></span> | <span data-ttu-id="9163f-219">1</span><span class="sxs-lookup"><span data-stu-id="9163f-219">1</span></span> | <span data-ttu-id="9163f-220">14 </span><span class="sxs-lookup"><span data-stu-id="9163f-220">14</span></span> |
| <span data-ttu-id="9163f-221">Unterhaltung erstellen</span><span class="sxs-lookup"><span data-stu-id="9163f-221">Create conversation</span></span> | <span data-ttu-id="9163f-222">2</span><span class="sxs-lookup"><span data-stu-id="9163f-222">2</span></span> | <span data-ttu-id="9163f-223">16 </span><span class="sxs-lookup"><span data-stu-id="9163f-223">16</span></span> |
| <span data-ttu-id="9163f-224">Unterhaltung erstellen</span><span class="sxs-lookup"><span data-stu-id="9163f-224">Create conversation</span></span>| <span data-ttu-id="9163f-225">1</span><span class="sxs-lookup"><span data-stu-id="9163f-225">1</span></span> | <span data-ttu-id="9163f-226">14 </span><span class="sxs-lookup"><span data-stu-id="9163f-226">14</span></span> |
| <span data-ttu-id="9163f-227">Unterhaltung erstellen</span><span class="sxs-lookup"><span data-stu-id="9163f-227">Create conversation</span></span>| <span data-ttu-id="9163f-228">2</span><span class="sxs-lookup"><span data-stu-id="9163f-228">2</span></span> | <span data-ttu-id="9163f-229">16 </span><span class="sxs-lookup"><span data-stu-id="9163f-229">16</span></span> |
| <span data-ttu-id="9163f-230">Abrufen von Unterhaltungsmitgliedern</span><span class="sxs-lookup"><span data-stu-id="9163f-230">Get conversation members</span></span>| <span data-ttu-id="9163f-231">1</span><span class="sxs-lookup"><span data-stu-id="9163f-231">1</span></span> | <span data-ttu-id="9163f-232">28</span><span class="sxs-lookup"><span data-stu-id="9163f-232">28</span></span> |
| <span data-ttu-id="9163f-233">Abrufen von Unterhaltungsmitgliedern</span><span class="sxs-lookup"><span data-stu-id="9163f-233">Get conversation members</span></span>| <span data-ttu-id="9163f-234">2</span><span class="sxs-lookup"><span data-stu-id="9163f-234">2</span></span> | <span data-ttu-id="9163f-235">32</span><span class="sxs-lookup"><span data-stu-id="9163f-235">32</span></span> |
| <span data-ttu-id="9163f-236">Unterhaltungen abrufen</span><span class="sxs-lookup"><span data-stu-id="9163f-236">Get conversations</span></span> | <span data-ttu-id="9163f-237">1</span><span class="sxs-lookup"><span data-stu-id="9163f-237">1</span></span> | <span data-ttu-id="9163f-238">28</span><span class="sxs-lookup"><span data-stu-id="9163f-238">28</span></span> |
| <span data-ttu-id="9163f-239">Unterhaltungen abrufen</span><span class="sxs-lookup"><span data-stu-id="9163f-239">Get conversations</span></span> | <span data-ttu-id="9163f-240">2</span><span class="sxs-lookup"><span data-stu-id="9163f-240">2</span></span> | <span data-ttu-id="9163f-241">32</span><span class="sxs-lookup"><span data-stu-id="9163f-241">32</span></span> |

## <a name="next-step"></a><span data-ttu-id="9163f-242">Nächster Schritt</span><span class="sxs-lookup"><span data-stu-id="9163f-242">Next step</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="9163f-243">Anrufe und Besprechungsbots</span><span class="sxs-lookup"><span data-stu-id="9163f-243">Calls and meetings bots</span></span>](~/bots/calls-and-meetings/calls-meetings-bots-overview.md)

