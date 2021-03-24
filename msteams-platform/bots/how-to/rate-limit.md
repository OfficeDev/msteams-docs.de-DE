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
# <a name="optimize-your-bot-rate-limiting-and-best-practices-in-microsoft-teams"></a>Optimieren Des Bots: Geschwindigkeitsbegrenzung und bewährte Methoden in Microsoft Teams

Als allgemeines Prinzip sollte Ihre Anwendung die Anzahl der Von ihr gesendeten Nachrichten auf eine einzelne Chat- oder Kanal unterhaltung beschränken. Dadurch wird eine optimale Benutzererfahrung sichergestellt, die sich für Ihre Endbenutzer nicht als "Spam" anfühlt.

Zum Schutz von Microsoft Teams und seinen Benutzern beschränken die Bot-APIs eingehende Anforderungen. Apps, die diesen Grenzwert überschreiten, erhalten einen `HTTP 429 Too Many Requests` Fehlerstatus. Alle Anforderungen unterliegen der gleichen Richtlinie zur Begrenzung der Geschwindigkeit, einschließlich des Sendens von Nachrichten, Kanalaufzählungen und Abrufen von Dienstplans.

Da die genauen Werte von Zinsgrenzen geändert werden können, wird empfohlen, dass Ihre Anwendung das entsprechende Backoff-Verhalten implementiert, wenn die API `HTTP 429 Too Many Requests` zurückgibt.

## <a name="handling-rate-limits"></a>Behandeln von Geschwindigkeitsbeschränkungen

Beim Ausstellen eines Bot Builder-SDK-Vorgangs können Sie den Statuscode `Microsoft.Rest.HttpOperationException` behandeln und überprüfen.

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

## <a name="best-practices"></a>Bewährte Methoden

Im Allgemeinen sollten Sie einfache Vorsichtsmaßnahmen ergreifen, um den Empfang von Antworten `HTTP 429` zu vermeiden. Vermeiden Sie beispielsweise, mehrere Anforderungen an dieselbe persönliche Unterhaltung oder eine Kanal unterhaltung ausstellen. Erwägen Sie stattdessen das Batchen der API-Anforderungen.

Die Verwendung eines exponentiellen Backoffs mit einem zufälligen Jitter ist die empfohlene Methode zum Verarbeiten von 429s. Dadurch wird sichergestellt, dass bei Wiederholungsversuchen bei mehreren Anforderungen keine Kollisionen auftut.

## <a name="example-detecting-transient-exceptions"></a>Beispiel: Erkennen vorübergehender Ausnahmen

Im Folgenden finden Sie ein Beispiel mit exponentiellem Backoff über den Anwendungsblock für die vorübergehende Fehlerbehandlung.

Sie können Backoff- und Wiederholungsversuche mithilfe der [transienten Fehlerbehandlung ausführen.](/previous-versions/msp-n-p/hh675232%28v%3dpandp.10%29) Richtlinien zum Abrufen und Installieren des NuGet-Pakets finden Sie unter [Adding the Transient Fault Handling Application Block to Your Solution](/previous-versions/msp-n-p/dn440719(v=pandp.60)?redirectedfrom=MSDN)). *Siehe auch Vorübergehende* [Fehlerbehandlung](/azure/architecture/best-practices/transient-faults).

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

## <a name="example-backoff"></a>Beispiel: Backoff

Sie können nicht nur Geschwindigkeitsbegrenzungen erkennen, sondern auch ein exponentielles Backoff ausführen.

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

Sie können auch eine Methodenausführung mit der oben beschriebenen `System.Action` Wiederholungsrichtlinie ausführen. Mit der referenzierten Bibliothek können Sie auch ein festes Intervall oder einen linearen Backoffmechanismus angeben.

Es wird empfohlen, den Wert und die Strategie in einer Konfigurationsdatei zu speichern, um Werte zur Laufzeit zu optimieren und zu optimieren.

Weitere Informationen finden Sie in dieser praktischen Anleitung zu verschiedenen Wiederholungsmustern: [Wiederholungsmuster](/azure/architecture/patterns/retry).

## <a name="per-bot-per-thread-limit"></a>Pro Bot pro Threadgrenzwert

>[!NOTE]
>Die Nachrichtenteilung auf Dienstebene führt zu höheren Anforderungen pro Sekunde (RPS). Wenn Sie sich Gedanken darüber machen, die Grenzwerte zu überschreiten, sollten Sie die oben beschriebene Backoffstrategie implementieren. Die unten angegebenen Werte sind nur zur Schätzung vorgesehen.

Dieser Grenzwert steuert den Datenverkehr, den ein Bot für eine einzelne Unterhaltung generieren darf. Eine Unterhaltung hier ist 1:1 zwischen Bot und Benutzer, einem Gruppenchat oder einem Kanal in einem Team.

| **Szenario** | **Zeitraum (Sek.)** | **Maximal zulässige Vorgänge** |
| --- | --- | --- |
| An Unterhaltung senden | 1 | 7  |
| An Unterhaltung senden | 2 | 8  |
| An Unterhaltung senden | 30 | 60 |
| An Unterhaltung senden | 3600 | 1800 |
| Unterhaltung erstellen | 1 | 7  |
| Unterhaltung erstellen | 2 | 8  |
| Unterhaltung erstellen | 30 | 60 |
| Unterhaltung erstellen | 3600 | 1800 |
| Get Conversation Members| 1 | 14  |
| Get Conversation Members| 2 | 16  |
| Get Conversation Members| 30 | 120 |
| Get Conversation Members| 3600 | 3600 |
| Unterhaltungen erhalten | 1 | 14  |
| Unterhaltungen erhalten | 2 | 16  |
| Unterhaltungen erhalten | 30 | 120 |
| Unterhaltungen erhalten | 3600 | 3600 |

>[!NOTE]
> Frühere Versionen `TeamsInfo.getMembers` von und `TeamsInfo.GetMembersAsync` APIs sind veraltet. Sie werden auf 5 Anforderungen pro Minute gedrosselt und geben maximal 10.000 Mitglieder pro Team zurück. Informationen zum Aktualisieren Ihres Bot Framework SDK und des Codes zur Verwendung der neuesten paginierten API-Endpunkte finden Sie unter [Bot-API-Änderungen für Team- und Chatmitglieder.](../../resources/team-chat-member-api-changes.md)

## <a name="per-thread-limit-for-all-bots"></a>Grenzwert pro Thread für alle Bots

Dieser Grenzwert steuert den Datenverkehr, den alle Bots über eine einzelne Unterhaltung generieren dürfen. Eine Unterhaltung hier ist 1:1 zwischen Bot und Benutzer, einem Gruppenchat oder einem Kanal in einem Team.

| **Szenario** | **Zeitraum (Sek.)** | **Maximal zulässige Vorgänge** |
| --- | --- | --- |
| An Unterhaltung senden | 1 | 14  |
| An Unterhaltung senden | 2 | 16  |
| Unterhaltung erstellen | 1 | 14  |
| Unterhaltung erstellen | 2 | 16  |
| CreateConversation| 1 | 14  |
| CreateConversation| 2 | 16  |
| Get Conversation Members| 1 | 28 |
| Get Conversation Members| 2 | 32 |
| Unterhaltungen erhalten | 1 | 28 |
| Unterhaltungen erhalten | 2 | 32 |
