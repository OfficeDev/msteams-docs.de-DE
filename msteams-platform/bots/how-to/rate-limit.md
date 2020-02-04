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
# <a name="optimize-your-bot-rate-limiting-and-best-practices-in-microsoft-teams"></a>Optimieren Ihres bot: Ratenbegrenzung und bewährte Methoden in Microsoft Teams

Als allgemeiner Grundsatz sollte Ihre Anwendung die Anzahl der Nachrichten begrenzen, die Sie an eine einzelne Chat-oder Kanal Unterhaltung sendet. Dadurch wird eine optimale Oberfläche gewährleistet, bei der die Endbenutzer nicht "spammy" empfinden.

Um Microsoft Teams und seine Benutzer zu schützen, begrenzen die bot-APIs eingehende Anforderungen. Apps, die diesen Grenzwert überschreiten, `HTTP 429 Too Many Requests` erhalten einen Fehlerstatus. Alle Anforderungen unterliegen der gleichen Richtlinie zur Ratenbegrenzung, einschließlich Senden von Nachrichten, Kanal Aufzählungen und Dienstplan abrufen.

Da die genauen Werte von Raten Grenzwerten geändert werden können, wird empfohlen, dass Ihre Anwendung das entsprechende Backoff-Verhalten implementiert, `HTTP 429 Too Many Requests`wenn die API zurückgegeben wird.

## <a name="handling-rate-limits"></a>Grenzwerte für die Handhabungs Rate

Beim Ausgeben eines bot-Generator-SDK-Vorgangs können `Microsoft.Rest.HttpOperationException` Sie den Statuscode verarbeiten und überprüfen.

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

Im Allgemeinen sollten Sie einfache Vorkehrungen treffen, um den Empfang `HTTP 429` von Antworten zu vermeiden. Vermeiden Sie beispielsweise das ausgeben mehrerer Anforderungen an dieselbe persönliche oder Kanal Unterhaltung. Verwenden Sie stattdessen die Batchverarbeitung der API-Anforderungen.

Das Verwenden einer exponentiellen Backoff mit einem willkürlichen Jitter ist die empfohlene Vorgehensweise zum Behandeln von 429er. Dadurch wird sichergestellt, dass mehrere Anforderungen keine Kollisionen bei Wiederholungsversuchen einführen.

## <a name="example-detecting-transient-exceptions"></a>Beispiel: Erkennen von vorübergehenden Ausnahmen

Im folgenden finden Sie ein Beispiel für die Verwendung eines exponentiellen Backoff über den Anwendungs Block der transienten Fehlerbehandlung.

Sie können Backoff und Wiederholungsversuche mit [temporären Fehler Behandlungs Bibliotheken](/previous-versions/msp-n-p/hh680901(v=pandp.50))durchführen. Richtlinien zum beziehen und Installieren des NuGet-Pakets finden Sie unter [Hinzufügen des Anwendungsblocks der vorübergehenden Fehlerbehandlung zur Lösung](/previous-versions/msp-n-p/hh680891(v=pandp.50)) .

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
var retryPolicy = new RetryPolicy(new BotSdkTransientExceptionDetectionStrategy(), fixedIntervalRetryStrategy);

//Execute any bot sdk action
await retryPolicy.ExecuteAsync(() => connector.Conversations.ReplyToActivityAsync((Activity)reply)).ConfigureAwait(false);
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
| NewMessage | 1  | 7  |
| NewMessage | 2  | 8  |
| NewMessage | 30 | 60 |
| NewMessage | 3600 | 1800 |
| UpdateMessage | 1  | 7  |
| UpdateMessage | 2  | 8  |
| UpdateMessage | 30 | 60 |
| UpdateMessage | 3600 | 1800 |
| NewThread | 1  | 7  |
| NewThread | 2  | 8  |
| NewThread | 30 | 60 |
| NewThread | 3600 | 1800 |
| GetThreadMembers | 1  | 14  |
| GetThreadMembers | 2  | 16  |
| GetThreadMembers | 30 | 120 |
| GetThreadMembers | 3600 | 3600 |
| GetThread | 1  | 14  |
| GetThread | 2  | 16  |
| GetThread | 30 | 120 |
| GetThread | 3600 | 3600 |

## <a name="per-thread-limit-for-all-bots"></a>Grenzwert pro Thread für alle Bots

Dieser Grenzwert steuert den Datenverkehr, den alle Bots in einer einzigen Unterhaltung generieren dürfen. Eine Unterhaltung ist 1:1 zwischen bot und Benutzer, einem Gruppenchat oder einem Kanal in einem Team.

| **Szenario** | **Zeitraum (Sek.)** | **Max. zulässige Vorgänge** |
| --- | --- | --- |
| NewMessage | 1  | 14  |
| NewMessage | 2  | 16  |
| UpdateMessage | 1  | 14  |
| UpdateMessage | 2  | 16  |
| NewThread | 1  | 14  |
| NewThread | 2  | 16  |
| GetThreadMembers | 1  | 28 |
| GetThreadMembers | 2  | 32 |
| GetThread | 1  | 28 |
| GetThread | 2  | 32 |

## <a name="bot-per-data-center-limit"></a>Bot pro Rechenzentrums Grenze

Dieser Grenzwert steuert den Datenverkehr, den ein bot in allen Threads in einem Rechenzentrum (in mehreren Mandanten) generieren darf.

|**Zeitraum (Sek.)** | **Max. zulässige Vorgänge** |
| --- | --- |
| 1  | 20 |
| 1800 | 8000 |
| 3600 | 15000 |
