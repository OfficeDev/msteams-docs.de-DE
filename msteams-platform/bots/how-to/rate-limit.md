---
title: Optimieren eines Bots mit Ratenbegrenzung in Teams
description: In codebeispielen erfahren Sie mehr über die Handhabung der Ratengrenze für Bots mit pro Bot-pro-Thread-Limit und pro Grenzwert für alle Bots. Darüber hinaus lernen Sie, die Best Practices in Microsoft Teams zu begrenzen.
ms.topic: conceptual
ms.localizationpriority: medium
keywords: Teams-Bots – Begrenzung der Raten
ms.openlocfilehash: 5f0eba162215aeda2c0f1e433b223f21628ea5e1
ms.sourcegitcommit: 8a0ffd21c800eecfcd6d1b5c4abd8c107fcf3d33
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2022
ms.locfileid: "63453376"
---
# <a name="optimize-your-bot-with-rate-limiting-in-teams"></a>Optimieren eines Bots mit Ratenbegrenzung in Teams

Die Geschwindigkeitsbegrenzung ist eine Methode, um Nachrichten auf eine bestimmte maximale Häufigkeit zu beschränken. Im Allgemeinen muss Ihre Anwendung die Anzahl der Nachrichten beschränken, die sie an einen einzelnen Chat oder eine Kanalunterhaltung sendet. Dadurch wird eine optimale Benutzererfahrung sichergestellt, und Nachrichten werden Ihren Benutzern nicht als Spam angezeigt.

Um Microsoft Teams und seine Benutzer zu schützen, bieten die Bot-APIs eine Ratenbegrenzung für eingehende Anforderungen. Apps, die diesen Grenzwert überschreiten, erhalten einen `HTTP 429 Too Many Requests` Fehlerstatus. Alle Anforderungen unterliegen derselben Richtlinie für die Begrenzung der Raten, einschließlich des Sendens von Nachrichten, Kanalenumerationen und Listenabrufen.

Da sich die genauen Werte von Zinslimits ändern können, muss Ihre Anwendung das entsprechende Backoff-Verhalten implementieren, wenn die API zurückgibt `HTTP 429 Too Many Requests`.

## <a name="handle-rate-limits"></a>Behandeln von Ratenlimits

Beim Ausgeben eines Bot Builder SDK-Vorgangs können Sie den Statuscode behandeln `Microsoft.Rest.HttpOperationException` und überprüfen.

Der folgende Code zeigt ein Beispiel für die Behandlung von Ratengrenzen:

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

Nachdem Sie die Ratenlimits für Bots behandelt haben, können Sie Antworten mithilfe eines exponentiellen Backoffs verarbeiten `HTTP 429` .

## <a name="handle-http-429-responses"></a>Behandeln von `HTTP 429` Antworten

Im Allgemeinen müssen Sie einfache Vorsichtsmaßnahmen ergreifen, um antworten zu vermeiden `HTTP 429` . Vermeiden Sie beispielsweise das Ausstellen mehrerer Anforderungen an dieselbe persönliche Unterhaltung oder Kanalunterhaltung. Erstellen Sie stattdessen einen Batch der API-Anforderungen.

Die Verwendung eines exponentiellen Backoffs mit einem zufälligen Jitter ist die empfohlene Methode zum Behandeln von 429s. Dadurch wird sichergestellt, dass mehrere Anforderungen bei Wiederholungsversuche keine Konflikte auslösen.

Nachdem Sie Antworten behandelt `HTTP 429` haben, können Sie das Beispiel zum Erkennen vorübergehender Ausnahmen durchgehen.

> [!NOTE]
> Zusätzlich zur Wiederholung des Fehlercodes **429** müssen auch die Fehlercodes **412**, **502** und **504** wiederholt werden.

## <a name="detect-transient-exceptions-example"></a>Beispiel zum Erkennen vorübergehender Ausnahmen

Der folgende Code zeigt ein Beispiel für die Verwendung eines exponentiellen Backoffs mithilfe des Vorübergehenden Anwendungsblocks für die Fehlerbehandlung:

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

Sie können Backoffs und Wiederholungsversuche mithilfe [der vorübergehenden Fehlerbehandlung](/previous-versions/msp-n-p/hh675232%28v%3dpandp.10%29) ausführen. Richtlinien zum Abrufen und Installieren des NuGet-Pakets finden Sie unter [Hinzufügen des Vorübergehenden Fehlerbehandlungsanwendungsblocks zu Ihrer Lösung](/previous-versions/msp-n-p/dn440719(v=pandp.60)?redirectedfrom=MSDN). Siehe auch [vorübergehende Fehlerbehandlung](/azure/architecture/best-practices/transient-faults).

Nachdem Sie das Beispiel zum Erkennen vorübergehender Ausnahmen durchgehen, durchlaufen Sie das exponentielle Backoff-Beispiel. Sie können exponentielles Backoff verwenden, anstatt fehlerweise erneut zu versuchen.

## <a name="backoff-example"></a>Backoff-Beispiel

Zusätzlich zum Erkennen von Zinslimits können Sie auch ein exponentielles Backoff ausführen.

Der folgende Code zeigt ein Beispiel für einen exponentiellen Backoff:

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

Sie können auch eine `System.Action` Methodenausführung mit der in diesem Abschnitt beschriebenen Wiederholungsrichtlinie ausführen. In der referenzierten Bibliothek können Sie auch ein festes Intervall oder einen linearen Backoff-Mechanismus angeben.

Store den Wert und die Strategie in einer Konfigurationsdatei, um die Werte zur Laufzeit zu optimieren und zu optimieren.

Weitere Informationen finden Sie unter [Wiederholungsmuster](/azure/architecture/patterns/retry).

Sie können die Ratenbegrenzung auch mithilfe des Grenzwerts pro Bot und Thread behandeln.

## <a name="per-bot-per-thread-limit"></a>Pro Bot pro Threadlimit

Der Grenzwert pro Bot und Thread steuert den Datenverkehr, den ein Bot in einer einzigen Unterhaltung generieren darf. Eine Unterhaltung ist 1:1 zwischen Bot und Benutzer, einem Gruppenchat oder einem Kanal in einem Team. Wenn die Anwendung also eine Bot-Nachricht an jeden Benutzer sendet, wird der Threadgrenzwert nicht gedrosselt.

>[!NOTE]
>
> * Das Threadlimit von 3600 Sekunden und 1800 Vorgängen gilt nur, wenn mehrere Bot-Nachrichten an einen einzelnen Benutzer gesendet werden.
> * Das globale Limit pro App und Mandant beträgt 50 Anforderungen pro Sekunde (RPS). Daher darf die Gesamtzahl der Botnachrichten pro Sekunde das Threadlimit nicht überschreiten.
> * Das Teilen von Nachrichten auf Dienstebene führt zu einem höheren RPS als erwartet. Wenn Sie sich Sorgen machen, die Grenzwerte zu erreichen, müssen Sie die [Backoff-Strategie](#backoff-example) implementieren. Die in diesem Abschnitt angegebenen Werte dienen nur der Schätzung.

Die folgende Tabelle enthält die Grenzwerte pro Bot und Thread:

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
| Abrufen von Unterhaltungsmitgliedern| 1 | 14  |
| Abrufen von Unterhaltungsmitgliedern| 2 | 16 |
| Abrufen von Unterhaltungsmitgliedern| 30 | 120 |
| Abrufen von Unterhaltungsmitgliedern| 3600 | 3600 |
| Unterhaltungen abrufen | 1 | 14  |
| Unterhaltungen abrufen | 2 | 16 |
| Unterhaltungen abrufen | 30 | 120 |
| Unterhaltungen abrufen | 3600 | 3600 |

>[!NOTE]
> Frühere Versionen von `TeamsInfo.getMembers` und `TeamsInfo.GetMembersAsync` APIs sind veraltet. Sie werden auf fünf Anforderungen pro Minute gedrosselt und geben maximal 10.000 Mitglieder pro Team zurück. Informationen zum Aktualisieren Ihres Bot Framework SDK und des Codes für die Verwendung der neuesten paginierten API-Endpunkte finden Sie unter [Bot-API-Änderungen für Team- und Chatmitglieder](../../resources/team-chat-member-api-changes.md).

Sie können die Ratenbegrenzung auch mithilfe des Grenzwerts pro Thread für alle Bots behandeln.

## <a name="per-thread-limit-for-all-bots"></a>Grenzwert pro Thread für alle Bots

Der Grenzwert pro Thread für alle Bots steuert den Datenverkehr, den alle Bots in einer einzigen Unterhaltung generieren dürfen. Eine Unterhaltung hier ist 1:1 zwischen Bot und Benutzer, einem Gruppenchat oder einem Kanal in einem Team.

Die folgende Tabelle enthält den Grenzwert pro Thread für alle Bots:

| Szenario | Zeitraum in Sekunden | Maximal zulässige Vorgänge |
| --- | --- | --- |
| An Unterhaltung senden | 1 | 14  |
| An Unterhaltung senden | 2 | 16 |
| Unterhaltung erstellen | 1 | 14  |
| Unterhaltung erstellen | 2 | 16 |
| Unterhaltung erstellen| 1 | 14  |
| Unterhaltung erstellen| 2 | 16 |
| Abrufen von Unterhaltungsmitgliedern| 1 | 28 |
| Abrufen von Unterhaltungsmitgliedern| 2 | 32 |
| Unterhaltungen abrufen | 1 | 28 |
| Unterhaltungen abrufen | 2 | 32 |

## <a name="next-step"></a>Nächster Schritt

> [!div class="nextstepaction"]
> [Bots für Anrufe und Besprechungen](~/bots/calls-and-meetings/calls-meetings-bots-overview.md)
