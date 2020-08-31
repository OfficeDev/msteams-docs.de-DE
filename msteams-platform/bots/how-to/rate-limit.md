---
title: Ratenbegrenzung
description: Ratenbegrenzung und bewährte Methoden in Microsoft Teams
keywords: Teams Bots Ratenbegrenzung
ms.openlocfilehash: 2e401b59df075688cb6d459a881e6b813f2cf8e6
ms.sourcegitcommit: b3962a7b36f260aef1af9124d14d71ae08b01ac4
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/28/2020
ms.locfileid: "47303710"
---
# <a name="optimize-your-bot-rate-limiting-and-best-practices-in-microsoft-teams"></a>Optimieren Ihres bot: Ratenbegrenzung und bewährte Methoden in Microsoft Teams

Als allgemeiner Grundsatz sollte Ihre Anwendung die Anzahl der Nachrichten begrenzen, die Sie an eine einzelne Chat-oder Kanal Unterhaltung sendet. Dadurch wird eine optimale Oberfläche gewährleistet, bei der die Endbenutzer nicht "spammy" empfinden.

Um Microsoft Teams und seine Benutzer zu schützen, begrenzen die bot-APIs eingehende Anforderungen. Apps, die diesen Grenzwert überschreiten, erhalten einen `HTTP 429 Too Many Requests` Fehlerstatus. Alle Anforderungen unterliegen der gleichen Richtlinie zur Ratenbegrenzung, einschließlich Senden von Nachrichten, Kanal Aufzählungen und Dienstplan abrufen.

Da die genauen Werte von Raten Grenzwerten geändert werden können, wird empfohlen, dass Ihre Anwendung das entsprechende Backoff-Verhalten implementiert, wenn die API zurückgegeben wird `HTTP 429 Too Many Requests` .

## <a name="handling-rate-limits"></a>Grenzwerte für die Handhabungs Rate

Beim Ausgeben eines bot-Generator-SDK-Vorgangs können Sie `Microsoft.Rest.HttpOperationException` den Statuscode verarbeiten und überprüfen.

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

Im Allgemeinen sollten Sie einfache Vorkehrungen treffen, um den Empfang von Antworten zu vermeiden `HTTP 429` . Vermeiden Sie beispielsweise das ausgeben mehrerer Anforderungen an dieselbe persönliche oder Kanal Unterhaltung. Verwenden Sie stattdessen die Batchverarbeitung der API-Anforderungen.

Das Verwenden einer exponentiellen Backoff mit einem willkürlichen Jitter ist die empfohlene Vorgehensweise zum Behandeln von 429er. Dadurch wird sichergestellt, dass mehrere Anforderungen keine Kollisionen bei Wiederholungsversuchen einführen.

## <a name="example-detecting-transient-exceptions"></a>Beispiel: Erkennen von vorübergehenden Ausnahmen

Im folgenden finden Sie ein Beispiel für die Verwendung eines exponentiellen Backoff über den Anwendungs Block der transienten Fehlerbehandlung.

Sie können Backoff und Wiederholungsversuche mit [vorübergehender Fehlerbehandlung](/previous-versions/msp-n-p/hh675232%28v%3dpandp.10%29)durchführen. Richtlinien zum beziehen und Installieren des NuGet-Pakets finden Sie unter [Hinzufügen des Anwendungsblocks der vorübergehenden Fehlerbehandlung zu Ihrer Lösung](/previous-versions/msp-n-p/dn440719(v=pandp.60)?redirectedfrom=MSDN)). *Siehe auch* [transient Fault Handling](/azure/architecture/best-practices/transient-faults).

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

Zusätzlich zur Ermittlung von Raten Grenzwerten können Sie auch eine exponentielle Backoff ausführen.

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

Sie können auch eine `System.Action` Methodenausführung mit der oben beschriebenen Wiederholungs Richtlinie ausführen. Mit der referenzierten Bibliothek können Sie auch ein festes Intervall oder einen linearen Backoff-Mechanismus angeben.

Es wird empfohlen, den Wert und die Strategie in einer Konfigurationsdatei zu speichern, um Werte zur Laufzeit zu optimieren und zu optimieren.

Weitere Informationen finden Sie in diesem handlichen Leitfaden für verschiedene Wiederholungsmuster: [Wiederholungsmuster](/azure/architecture/patterns/retry).

## <a name="per-bot-per-thread-limit"></a>Pro bot pro Thread-Grenzwert

>[!NOTE]
>Die Nachrichten Aufteilung auf Dienstebene führt zu höheren als erwarteten Anforderungen pro Sekunde (RPS). Wenn Sie Bedenken haben, sich an die Grenzwerte zu wenden, sollten Sie die oben beschriebene Backoff-Strategie implementieren. Die unten angegebenen Werte dienen nur der Schätzung.

Dieser Grenzwert steuert den Datenverkehr, den ein bot für eine einzelne Unterhaltung generieren darf. Eine Unterhaltung ist 1:1 zwischen bot und Benutzer, einem Gruppenchat oder einem Kanal in einem Team.

| **Szenario** | **Zeitraum (Sek.)** | **Max. zulässige Vorgänge** |
| --- | --- | --- |
| An Unterhaltung senden | 1  | 7  |
| An Unterhaltung senden | 2  | 8  |
| An Unterhaltung senden | 30 | 60 |
| An Unterhaltung senden | 3600 | 1800 |
| Unterhaltung erstellen | 1  | 7  |
| Unterhaltung erstellen | 2  | 8  |
| Unterhaltung erstellen | 30 | 60 |
| Unterhaltung erstellen | 3600 | 1800 |
| Abrufen von Unterhaltungs Mitgliedern| 1  | 14  |
| Abrufen von Unterhaltungs Mitgliedern| 2  | 16  |
| Abrufen von Unterhaltungs Mitgliedern| 30 | 120 |
| Abrufen von Unterhaltungs Mitgliedern| 3600 | 3600 |
| Unterhaltungen abrufen | 1  | 14  |
| Unterhaltungen abrufen | 2  | 16  |
| Unterhaltungen abrufen | 30 | 120 |
| Unterhaltungen abrufen | 3600 | 3600 |

## <a name="per-thread-limit-for-all-bots"></a>Grenzwert pro Thread für alle Bots

Dieser Grenzwert steuert den Datenverkehr, den alle Bots in einer einzigen Unterhaltung generieren dürfen. Eine Unterhaltung ist 1:1 zwischen bot und Benutzer, einem Gruppenchat oder einem Kanal in einem Team.

| **Szenario** | **Zeitraum (Sek.)** | **Max. zulässige Vorgänge** |
| --- | --- | --- |
| An Unterhaltung senden | 1  | 14  |
| An Unterhaltung senden | 2  | 16  |
| Unterhaltung erstellen | 1  | 14  |
| Unterhaltung erstellen | 2  | 16  |
| Createconversation| 1  | 14  |
| Createconversation| 2  | 16  |
| Abrufen von Unterhaltungs Mitgliedern| 1  | 28 |
| Abrufen von Unterhaltungs Mitgliedern| 2  | 32 |
| Unterhaltungen abrufen | 1  | 28 |
| Unterhaltungen abrufen | 2  | 32 |
