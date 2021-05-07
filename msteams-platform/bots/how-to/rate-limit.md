---
title: Optimieren eines Bots mit Ratenbegrenzung in Teams
description: Geschwindigkeitsbegrenzung und bewährte Methoden in Microsoft Teams
ms.topic: conceptual
localization_priority: Normal
keywords: Beschränkung der Rate von Teams-Bots
ms.openlocfilehash: 3b8f80efa50d2fbf44162aec13994b747b9bd7ac
ms.sourcegitcommit: 60561c7cd189c9d6fa5e09e0f2b6c24476f2dff5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/06/2021
ms.locfileid: "52230960"
---
# <a name="optimize-your-bot-with-rate-limiting-in-teams"></a>Optimieren eines Bots mit Ratenbegrenzung in Teams

Die Geschwindigkeitsbegrenzung ist eine Methode, um Nachrichten auf eine bestimmte maximale Häufigkeit zu beschränken. Als allgemeines Prinzip muss Ihre Anwendung die Anzahl der Von ihr gesendeten Nachrichten auf eine einzelne Chat- oder Kanal unterhaltung beschränken. Dadurch wird eine optimale Benutzererfahrung sichergestellt, und Nachrichten werden ihren Benutzern nicht als Spam angezeigt.

Zum Schutz Microsoft Teams und seiner Benutzer bieten die Bot-APIs eine Geschwindigkeitsbegrenzung für eingehende Anforderungen. Apps, die diesen Grenzwert überschreiten, erhalten einen `HTTP 429 Too Many Requests` Fehlerstatus. Alle Anforderungen unterliegen der gleichen Richtlinie zur Begrenzung der Rate, einschließlich des Sendens von Nachrichten, Kanalaufzählungen und Abrufen von Dienstplans.

Da sich die genauen Werte der Zinsgrenzen ändern können, muss Ihre Anwendung das entsprechende Backoff-Verhalten implementieren, wenn die API `HTTP 429 Too Many Requests` zurückgibt.

## <a name="handle-rate-limits"></a>Behandeln von Satzbegrenzungen

Beim Ausstellen eines Bot Builder-SDK-Vorgangs können Sie den Statuscode `Microsoft.Rest.HttpOperationException` behandeln und überprüfen.

Der folgende Code zeigt ein Beispiel für die Behandlung von Geschwindigkeitsbeschränkungen:

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

Nachdem Sie die Geschwindigkeitsbeschränkungen für Bots umgangen haben, können Sie Antworten mithilfe eines `HTTP 429` exponentiellen Backoffs behandeln.

## <a name="handle-http-429-responses"></a>Behandeln von `HTTP 429` Antworten

Im Allgemeinen müssen Sie einfache Vorsichtsmaßnahmen ergreifen, um den Empfang von Antworten `HTTP 429` zu vermeiden. Vermeiden Sie beispielsweise, mehrere Anforderungen an dieselbe persönliche Unterhaltung oder eine Kanal unterhaltung ausstellen. Erstellen Sie stattdessen einen Batch der API-Anforderungen.

Die Verwendung eines exponentiellen Backoffs mit einem zufälligen Jitter ist die empfohlene Methode zum Verarbeiten von 429s. Dadurch wird sichergestellt, dass bei Wiederholungsversuchen bei mehreren Anforderungen keine Kollisionen auftut.

Nachdem Sie Antworten behandeln, können Sie das Beispiel `HTTP 429` zum Erkennen vorübergehender Ausnahmen durchgehen.

> [!NOTE]
> Zusätzlich zum Retyringfehlercode **429** müssen auch die Fehlercodes **412,** **502** und **504** wiederholt werden.

## <a name="detect-transient-exceptions-example"></a>Erkennen vorübergehender Ausnahmen (Beispiel)

Der folgende Code zeigt ein Beispiel für die Verwendung eines exponentiellen Backoffs mithilfe des Anwendungsblocks für die vorübergehende Fehlerbehandlung:

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

Sie können Backoff- und Wiederholungsversuche mithilfe der [vorübergehenden Fehlerbehandlung ausführen.](/previous-versions/msp-n-p/hh675232%28v%3dpandp.10%29) Richtlinien zum Abrufen und Installieren des NuGet finden Sie unter Hinzufügen des Anwendungsblocks für vorübergehende Fehlerbehandlung [zu Ihrer Lösung](/previous-versions/msp-n-p/dn440719(v=pandp.60)?redirectedfrom=MSDN). Siehe auch [vorübergehende Fehlerbehandlung](/azure/architecture/best-practices/transient-faults).

Nachdem Sie das Beispiel zum Erkennen vorübergehender Ausnahmen durchgehen, gehen Sie durch das exponentielle Backoff-Beispiel. Sie können exponentielles Backoff verwenden, anstatt Fehler erneut zu wiederholen.

## <a name="backoff-example"></a>Backoff-Beispiel

Sie können nicht nur Geschwindigkeitsbegrenzungen erkennen, sondern auch ein exponentielles Backoff ausführen.

Der folgende Code zeigt ein Beispiel für exponentielles Backoff:

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

Sie können auch eine Methodenausführung mit der in diesem Abschnitt beschriebenen `System.Action` Wiederholungsrichtlinie ausführen. Mit der referenzierten Bibliothek können Sie auch ein festes Intervall oder einen linearen Backoffmechanismus angeben.

Store wert und strategie in einer Konfigurationsdatei, um Werte zur Laufzeit zu optimieren und zu optimieren.

Weitere Informationen finden Sie unter [Wiederholungsmuster](/azure/architecture/patterns/retry).

Sie können auch die Geschwindigkeitsbegrenzung mithilfe der Pro-Bot-Pro-Thread-Grenze behandeln.

## <a name="per-bot-per-thread-limit"></a>Pro Bot pro Threadgrenzwert

Der Grenzwert pro Bot pro Thread steuert den Datenverkehr, den ein Bot in einer einzigen Unterhaltung generieren darf. Eine Unterhaltung zwischen Bot und Benutzer, einem Gruppenchat oder einem Kanal in einem Team ist 1:1. Wenn die Anwendung also eine Botnachricht an jeden Benutzer sendet, wird der Threadgrenzwert nicht gedrosselt.

>[!NOTE]
> * Der Threadgrenzwert von 3600 Sekunden und 1800 Vorgängen gilt nur, wenn mehrere Botnachrichten an einen einzelnen Benutzer gesendet werden. 
> * Der globale Grenzwert pro App pro Mandant beträgt 50 Anforderungen pro Sekunde (RPS). Daher darf die Gesamtzahl der Botnachrichten pro Sekunde nicht die Threadbegrenzung überschreiten.
> * Die Nachrichtenteilung auf Dienstebene führt zu einem höheren RpS als erwartet. Wenn Sie sich Sorgen machen, die Grenzwerte zu überschreiten, müssen Sie die [Backoff-Strategie implementieren.](#backoff-example) Die in diesem Abschnitt angegebenen Werte sind nur zur Schätzung vorgesehen.

In der folgenden Tabelle sind die Grenzwerte pro Bot pro Thread aufgeführt:

| Szenario | Zeitraum in Sekunden | Maximal zulässige Vorgänge |
| --- | --- | --- |
| An Unterhaltung senden | 1 | 7  |
| An Unterhaltung senden | 2 | 8  |
| An Unterhaltung senden | 30 | 60 |
| An Unterhaltung senden | 3600 | 1800 |
| Unterhaltung erstellen | 1 | 7  |
| Unterhaltung erstellen | 2 | 8  |
| Unterhaltung erstellen | 30 | 60 |
| Unterhaltung erstellen | 3600 | 1800 |
| Unterhaltungsmitglieder erhalten| 1 | 14  |
| Unterhaltungsmitglieder erhalten| 2 | 16  |
| Unterhaltungsmitglieder erhalten| 30 | 120 |
| Unterhaltungsmitglieder erhalten| 3600 | 3600 |
| Unterhaltungen erhalten | 1 | 14  |
| Unterhaltungen erhalten | 2 | 16  |
| Unterhaltungen erhalten | 30 | 120 |
| Unterhaltungen erhalten | 3600 | 3600 |

>[!NOTE]
> Frühere Versionen `TeamsInfo.getMembers` von und `TeamsInfo.GetMembersAsync` APIs sind veraltet. Sie werden auf fünf Anforderungen pro Minute gedrosselt und geben maximal 10.000 Mitglieder pro Team zurück. Informationen zum Aktualisieren Ihres Bot Framework SDK und des Codes zur Verwendung der neuesten paginierten API-Endpunkte finden Sie unter [Bot-API-Änderungen für Team- und Chatmitglieder.](../../resources/team-chat-member-api-changes.md)

Sie können die Geschwindigkeitsbegrenzung auch mithilfe des Pro-Thread-Grenzwerts für alle Bots behandeln.

## <a name="per-thread-limit-for-all-bots"></a>Grenzwert pro Thread für alle Bots

Der Grenzwert pro Thread für alle Bots steuert den Datenverkehr, den alle Bots über eine einzelne Unterhaltung generieren dürfen. Eine Unterhaltung hier ist 1:1 zwischen Bot und Benutzer, einem Gruppenchat oder einem Kanal in einem Team.

In der folgenden Tabelle ist der Grenzwert pro Thread für alle Bots aufgeführt:

| Szenario | Zeitraum in Sekunden | Maximal zulässige Vorgänge |
| --- | --- | --- |
| An Unterhaltung senden | 1 | 14  |
| An Unterhaltung senden | 2 | 16  |
| Unterhaltung erstellen | 1 | 14  |
| Unterhaltung erstellen | 2 | 16  |
| Unterhaltung erstellen| 1 | 14  |
| Unterhaltung erstellen| 2 | 16  |
| Unterhaltungsmitglieder erhalten| 1 | 28 |
| Unterhaltungsmitglieder erhalten| 2 | 32 |
| Unterhaltungen erhalten | 1 | 28 |
| Unterhaltungen erhalten | 2 | 32 |

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Anrufe und Besprechungsbots](~/bots/calls-and-meetings/calls-meetings-bots-overview.md)

