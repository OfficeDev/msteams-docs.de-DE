---
title: Optimieren eines Bots mit Ratenbegrenzung in Teams
description: Erfahren Sie anhand von Beispielcodes mehr über das Behandeln von Ratenbegrenzungen für Bots mit Pro Bot pro Thread-Grenzwert und pro Grenzwert für alle Bots. Darüber hinaus lernen Sie bewährte Methoden der Ratenbegrenzung in Microsoft Teams kennen.
ms.topic: conceptual
ms.localizationpriority: medium
keywords: Teams Bots Ratenbegrenzung
ms.openlocfilehash: a864970bd837ef4af3ccebe0b09ca4d38ac7b76b
ms.sourcegitcommit: eeaa8cbb10b9dfa97e9c8e169e9940ddfe683a7b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/27/2022
ms.locfileid: "65757150"
---
# <a name="optimize-your-bot-with-rate-limiting-in-teams"></a>Optimieren eines Bots mit Ratenbegrenzung in Teams

Ratenbegrenzung ist eine Methode, um Nachrichten auf eine bestimmte maximale Häufigkeit zu beschränken. Als allgemeines Prinzip muss Ihre Anwendung die Anzahl der Nachrichten beschränken, die sie auf einen einzelnen Chat oder eine Kanalunterhaltung sendet. Dadurch wird sichergestellt, dass eine optimale Benutzererfahrung erzielt wird und Nachrichten ihren Benutzern nicht als Spam angezeigt werden.

Um Microsoft Teams und seine Benutzer zu schützen, bieten die Bot-APIs eine Ratenbegrenzung für eingehende Anforderungen. Apps, die diesen Grenzwert überschreiten, erhalten den Fehlerstatus `HTTP 429 Too Many Requests`. Alle Anforderungen unterliegen derselben Richtlinie zur Begrenzung der Rate, einschließlich senden von Nachrichten, Kanalaufzählungen und Listenabrufen.

Da sich die genauen Werte von Ratenbegrenzungen ändern können, muss Ihre Anwendung das entsprechende Backoff-Verhalten implementieren, wenn die API `HTTP 429 Too Many Requests` zurückgibt.

## <a name="handle-rate-limits"></a>Behandeln von Ratenbegrenzungen

Beim Ausgeben eines Bot Builder SDK-Vorgangs können Sie `Microsoft.Rest.HttpOperationException` behandeln und den Statuscode überprüfen.

Der folgende Code zeigt ein Beispiel für das Behandeln von Ratenbegrenzungen:

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

Nachdem Sie Ratenbegrenzungen für Bots behandelt haben, können Sie `HTTP 429`-Antworten mit einem exponentiellen Backoff verarbeiten.

## <a name="handle-http-429-responses"></a>Behandeln von `HTTP 429`-Anworten

Im Allgemeinen müssen Sie einfache Vorsichtsmaßnahmen treffen, um `HTTP 429`-Anworten zu vermeiden. Vermeiden Sie beispielsweise, mehrere Anforderungen an dieselbe persönliche oder Kanalunterhaltung auszustellen. Erstellen Sie stattdessen einen Batch der API-Anforderungen.

Die empfohlene Methode zum Behandeln von 429-Ausnahmen ist die Verwendung eines exponentiellen Backoffs mit einem zufälligen Jitter. Dadurch wird sichergestellt, dass mehrere Anforderungen keine Kollisionen bei Wiederholungsversuchen verursachen.

Nachdem Sie `HTTP 429`-Antworten behandelt haben, können Sie das Beispiel zum Erkennen vorübergehender Ausnahmen durchgehen.

> [!NOTE]
> Neben dem Wiederholen des Fehlercodes **429** müssen auch die Fehlercodes **412**, **502** und **504** wiederholt werden.

## <a name="detect-transient-exceptions-example"></a>Beispiel für das Erkennen vorübergehender Ausnahmen

Der folgende Code zeigt ein Beispiel für die Verwendung des exponentiellen Backoffs mithilfe des Anwendungsblocks für die Behandlung vorübergehender Fehler:

```csharp
public class BotSdkTransientExceptionDetectionStrategy : ITransientErrorDetectionStrategy
    {
        // List of error codes to retry on
        List<int> transientErrorStatusCodes = new List<int>() { 429 };

        public static bool IsTransient(Exception ex)
          {
              if (ex.Message.Contains("429"))
                  return true;

              HttpResponseMessageWrapper? response = null;
              if (ex is HttpOperationException httpOperationException)
              {
                  response = httpOperationException.Response;
              }
              else
              if (ex is ErrorResponseException errorResponseException)
              {
                  response = errorResponseException.Response;
              }
              return response != null && transientErrorStatusCodes.Contains((int)response.StatusCode);
          }
    }
```

Sie können Backoff- und Wiederholungsversuche mithilfe der [Behandlung vorübergehender Fehler](/previous-versions/msp-n-p/hh675232%28v%3dpandp.10%29) durchführen. Richtlinien zum Abrufen und Installieren des NuGet-Pakets finden Sie unter [Hinzufügen des Anwendungsblocks für die Behandlung vorübergehender Fehler zu Ihrer Lösung](/previous-versions/msp-n-p/dn440719(v=pandp.60)?redirectedfrom=MSDN). Weitere Informationen finden Sie unter [Behandlung vorübergehender Fehler](/azure/architecture/best-practices/transient-faults).

Nachdem Sie das Beispiel zum Erkennen vorübergehender Ausnahmen durchgearbeitet haben, arbeiten Sie das exponentielle Backoff-Beispiel durch. Sie können statt Wiederholversuchen bei Fehlern einen exponentiellen Backoff verwenden.

## <a name="backoff-example"></a>Backoff-Beispiel

Zusätzlich zum Erkennen von Ratenbegrenzungen können Sie auch einen exponentiellen Backoff durchführen.

Der folgende Code zeigt ein Beispiel für diesen Backoff:

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

Sie können auch eine `System.Action`-Methodenausführung mit der in diesem Abschnitt beschriebenen Wiederholungsrichtlinie ausführen. Mit der Referenzbibliothek können Sie auch ein festes Intervall oder einen linearen Backoff-Mechanismus angeben.

Speichern Sie den Wert und die Strategie in einer Konfigurationsdatei, um Werte zur Laufzeit fein abzustimmen und zu optimieren.

Weitere Informationen finden Sie unter [Wiederholungsmuster](/azure/architecture/patterns/retry).

Sie können die Ratenbegrenzung auch mithilfe des Grenzwerts „Pro Bot pro Thread“ behandeln.

## <a name="per-bot-per-thread-limit"></a>Pro Bot pro Thread-Grenzwert

Der Grenzwert „Pro Bot pro Thread“ steuert den Datenverkehr, den ein Bot in einer einzigen Unterhaltung generieren darf. Eine Unterhaltung ist 1:1 zwischen Bot und Benutzer, einem Gruppenchat oder einem Kanal in einem Team. Wenn die Anwendung also eine Botnachricht an jeden Benutzer sendet, wird der Threadgrenzwert nicht gedrosselt.

>[!NOTE]
>
> * Der Threadgrenzwert von 3600 Sekunden und 1800 Vorgängen gilt nur, wenn mehrere Bot-Nachrichten an einen einzelnen Benutzer gesendet werden.
> * Der globale Grenzwert pro App und Mandant beträgt 50 Anforderungen pro Sekunde (RPS). Daher darf die Gesamtzahl der Bot-Nachrichten pro Sekunde den Threadgrenzwert nicht überschreiten.
> * Die Nachrichtenaufteilung auf Dienstebene führt zu führt zu höheren RPS als erwartet. Wenn Sie Bedenken haben, sich den Grenzen zu nähern, müssen Sie die [Backoff-Strategie](#backoff-example) implementieren. Die in diesem Abschnitt angegebenen Werte dienen nur der Schätzung.

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
| Abrufen von Unterhaltungsmitgliedern| 1 | 14 |
| Abrufen von Unterhaltungsmitgliedern| 2 | 16 |
| Abrufen von Unterhaltungsmitgliedern| 30 | 120 |
| Abrufen von Unterhaltungsmitgliedern| 3600 | 3600 |
| Abrufen von Unterhaltungen | 1 | 14 |
| Abrufen von Unterhaltungen | 2 | 16 |
| Abrufen von Unterhaltungen | 30 | 120 |
| Abrufen von Unterhaltungen | 3600 | 3600 |

>[!NOTE]
> Frühere Versionen der APIs `TeamsInfo.getMembers` und `TeamsInfo.GetMembersAsync` sind veraltet. Sie werden auf fünf Anforderungen pro Minute gedrosselt und geben maximal 10K-Mitglieder pro Team zurück. Informationen zum Aktualisieren Ihres Bot-Framework-SDK und des Codes für die Verwendung der neuesten paginierten API-Endpunkte finden Sie unter [Bot-API-Änderungen für Team- und Chatmitglieder](../../resources/team-chat-member-api-changes.md).

Sie können Ratenbegrenzungsausnahmen auch mithilfe des Grenzwerts „Pro Thread“ für alle Bots behandeln.

## <a name="per-thread-limit-for-all-bots"></a>Grenzwert pro Thread für alle Bots

Der Grenzwert pro Thread für alle Bots steuert den Datenverkehr, den alle Bots in einer einzigen Unterhaltung generieren dürfen. Eine Unterhaltung hier ist 1:1 zwischen Bot und Benutzer, einem Gruppenchat oder einem Kanal in einem Team.

Die folgende Tabelle enthält den Grenzwert pro Thread für alle Bots:

| Szenario | Zeitraum in Sekunden | Maximal zulässige Vorgänge |
| --- | --- | --- |
| An Unterhaltung senden | 1 | 14 |
| An Unterhaltung senden | 2 | 16 |
| Unterhaltung erstellen | 1 | 14 |
| Unterhaltung erstellen | 2 | 16 |
| Unterhaltung erstellen| 1 | 14 |
| Unterhaltung erstellen| 2 | 16 |
| Abrufen von Unterhaltungsmitgliedern| 1 | 28 |
| Abrufen von Unterhaltungsmitgliedern| 2 | 32 |
| Abrufen von Unterhaltungen | 1 | 28 |
| Abrufen von Unterhaltungen | 2 | 32 |

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Bots für Anrufe und Besprechungen](~/bots/calls-and-meetings/calls-meetings-bots-overview.md)
