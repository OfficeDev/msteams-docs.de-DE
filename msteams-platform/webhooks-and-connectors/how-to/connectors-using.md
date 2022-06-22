---
title: Nachrichten erstellen und senden
author: laujan
description: In diesem Modul erfahren Sie, wie Sie Office 365-Connectors verwenden und Aktionen erfordernde Nachrichten in Microsoft Teams erstellen und senden.
ms.topic: how-to
ms.localizationpriority: high
ms.openlocfilehash: 1d52760784e3d0bbbd1e4a87c576294530242629
ms.sourcegitcommit: 7bbb7caf729a00b267ceb8af7defffc91903d945
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 06/21/2022
ms.locfileid: "66190105"
---
# <a name="create-and-send-messages"></a>Nachrichten erstellen und senden

Sie können Aktionen erfordernde Nachrichten erstellen und sie über eingehende Webhooks oder Office 365 Connector versenden.

## <a name="create-actionable-messages"></a>Erstellen von Aktionen erfordernden Nachrichten

Aktionen erfordernden Nachrichten umfassen sechs sichtbare Schaltflächen auf der Karte. Jede Schaltfläche wird in der `potentialAction`-Eigenschaft der Nachricht mithilfe von `ActionCard`-Aktionen definiert, die jeweils einen Eingabetyp umfassen: ein Textfeld, eine Datumsauswahl oder eine Mehrfachauswahlliste. Jeder `ActionCard` ist eine Aktion zugeordnet, z. B. `HttpPOST`.

Die Connectorkarten unterstützen die folgenden Aktionen:

* `ActionCard`: Stellt einen oder mehrere Eingabetypen und zugeordnete Aktionen dar.
* `HttpPOST`: Sendet eine POST-Anforderung an eine URL.
* `OpenUri`: Öffnet einen URI in einem separaten Browser oder in einer anderen App; ist optional auf unterschiedliche URIs basierend auf Betriebssystemen ausgerichtet.

Die `ActionCard`-Aktion unterstützt drei Eingabetypen:

* `TextInput`: Ein ein- oder mehrzeiliges Textfeld mit optionaler Längenbegrenzung.
* `DateInput`: Eine Datumsauswahl mit optionaler Zeitauswahl.
* `MultichoiceInput`: Eine Liste mit Auswahlmöglichkeiten, die entweder die Auswahl einer einzelnen Option oder mehrerer Optionen bietet.

`MultichoiceInput` unterstützt eine `style`-Eigenschaft über die festgelegt wird, ob die Liste anfänglich vollständig erweitert angezeigt wird. Der Standardwert von `style` hängt vom Wert von `isMultiSelect` wie folgt ab:

| `isMultiSelect` | `style`-Standardeinstellung |
| --- | --- |
| `false` oder nicht angegeben | `compact` |
| `true` | `expanded` |

Um die Mehrfachauswahlliste im Kompaktformat anzuzeigen, geben Sie `"isMultiSelect": true` und `"style": true` an.

Weitere Informationen zu Connectorkarten-Aktionen finden Sie unter [Aktionen](/outlook/actionable-messages/card-reference#actions).

> [!NOTE]
>
> * Die Angabe von `compact` für die `style`-Eigenschaft in Microsoft Teams entspricht der Angabe von `normal` für die `style`-Eigenschaft in Microsoft Outlook.
> * Bei der HttpPOST-Aktion ist das Bearertoken in den Anforderungen enthalten. Dieses Token enthält die Microsoft Azure Active Directory (Azure AD)-Identität des Office 365-Benutzers, der die Aktion ausgeführt hat.

## <a name="send-a-message-through-incoming-webhook-or-office-365-connector"></a>Senden einer Nachricht über eingehenden Webhook oder Office 365 Connector

Um eine Nachricht über Ihren eingehenden Webhook oder Office 365 Connector zu senden, senden Sie eine JSON-Nutzlast an die Webhook-URL. Diese Nutzlast muss in einer [Office 365- Connectorkarte](~/task-modules-and-cards/cards/cards-reference.md#office-365-connector-card) bestehen.

Sie können diesen JSON-Code auch zum Erstellen von Karten mit umfassenden Eingabeoptionen verwenden, wie z. B. Texteingabe, Mehrfachauswahl oder Auswählen eines Datums und einer Uhrzeit. Der Code, der die Karte generiert und an die Webhook-URL sendet, kann in jedem gehosteten Dienst ausgeführt werden. Diese Karten sind als Bestandteil von Aktionen erfordernde Nachrichten definiert und werden auch in [Karten](~/task-modules-and-cards/what-are-cards.md) unterstützt, die in Microsoft Teams-Bots und Nachrichtenerweiterungen verwendet werden.

### <a name="example-of-connector-message"></a>Beispiel für eine Connectornachricht

Ein Beispiel für eine Connectornachricht:

```json
{
    "@type": "MessageCard",
    "@context": "http://schema.org/extensions",
    "themeColor": "0076D7",
    "summary": "Larry Bryant created a new task",
    "sections": [{
        "activityTitle": "Larry Bryant created a new task",
        "activitySubtitle": "On Project Tango",
        "activityImage": "https://teamsnodesample.azurewebsites.net/static/img/image5.png",
        "facts": [{
            "name": "Assigned to",
            "value": "Unassigned"
        }, {
            "name": "Due date",
            "value": "Mon May 01 2017 17:07:18 GMT-0700 (Pacific Daylight Time)"
        }, {
            "name": "Status",
            "value": "Not started"
        }],
        "markdown": true
    }],
    "potentialAction": [{
        "@type": "ActionCard",
        "name": "Add a comment",
        "inputs": [{
            "@type": "TextInput",
            "id": "comment",
            "isMultiline": false,
            "title": "Add a comment here for this task"
        }],
        "actions": [{
            "@type": "HttpPOST",
            "name": "Add comment",
            "target": "https://docs.microsoft.com/outlook/actionable-messages"
        }]
    }, {
        "@type": "ActionCard",
        "name": "Set due date",
        "inputs": [{
            "@type": "DateInput",
            "id": "dueDate",
            "title": "Enter a due date for this task"
        }],
        "actions": [{
            "@type": "HttpPOST",
            "name": "Save",
            "target": "https://docs.microsoft.com/outlook/actionable-messages"
        }]
    }, {
        "@type": "OpenUri",
        "name": "Learn More",
        "targets": [{
            "os": "default",
            "uri": "https://docs.microsoft.com/outlook/actionable-messages"
        }]
    }, {
        "@type": "ActionCard",
        "name": "Change status",
        "inputs": [{
            "@type": "MultichoiceInput",
            "id": "list",
            "title": "Select a status",
            "isMultiSelect": "false",
            "choices": [{
                "display": "In Progress",
                "value": "1"
            }, {
                "display": "Active",
                "value": "2"
            }, {
                "display": "Closed",
                "value": "3"
            }]
        }],
        "actions": [{
            "@type": "HttpPOST",
            "name": "Save",
            "target": "https://docs.microsoft.com/outlook/actionable-messages"
        }]
    }]
}
```

Diese Nachricht erzeugt die folgende Karte im Kanal:

![Screenshot einer Connectorkarte](~/assets/images/connectorcard.png)

## <a name="send-messages-using-curl-and-powershell"></a>Senden von Nachrichten mit cURL und PowerShell

# <a name="curl"></a>[cURL](#tab/cURL)

Führen Sie die folgenden Schritte aus, um eine Nachricht im Webhook mit cURL zu posten:

1. Installieren Sie cURL von der [cURL-Website](https://curl.haxx.se/).

1. Geben Sie den folgenden cURL-Befehl in die Befehlszeile ein:

   ```bash
   // on macOS or Linux
   curl -H 'Content-Type: application/json' -d '{"text": "Hello World"}' <YOUR WEBHOOK URL>
   ```

   ```bash
   // on Windows
   curl.exe -H "Content-Type:application/json" -d "{'text':'Hello World'}" <YOUR WEBHOOK URL>
   ```

    > [!NOTE]
    > Wenn der POST-Vorgang erfolgreich ist, sollte eine einfache **1** durch `curl` ausgegeben werden.

1. Überprüfen Sie den Teams-Client auf die neue gepostete Karte.

# <a name="powershell"></a>[PowerShell](#tab/PowerShell)

 Voraussetzung: Installation von PowerShell und Vertrautheit mit dessen grundlegender Verwendung.

Führen Sie die folgenden Schritte aus, um eine Nachricht an den Webhook mit PowerShell zu posten:

1. Geben Sie in der PowerShell-Eingabeaufforderung den folgenden Befehl ein:

   ```powershell
   Invoke-RestMethod -Method post -ContentType 'Application/Json' -Body '{"text":"Hello World!"}' -Uri <YOUR WEBHOOK URL>
   ```

    > [!NOTE]
    > Wenn der POST-Vorgang erfolgreich ist, sollte eine einfache **1** durch `Invoke-RestMethod` ausgegeben werden.

1. Überprüfen Sie den Teams-Kanal, welcher der Webhook-URL zugeordnet ist. Die neue Karte wird nun im Kanal angezeigt. Bevor Sie den Connector zum Testen oder Veröffentlichen Ihrer App verwenden, müssen Sie folgendes tun:

    * [Zwei Symbole einschließen](../../concepts/build-and-test/apps-package.md#app-icons).
    * Ändern Sie den `icons`-Teil des Manifests in die Dateinamen der Symbole anstelle von URLs.

---

## <a name="send-adaptive-cards-using-an-incoming-webhook"></a>Senden von adaptiven Karten mithilfe eines eingehenden Webhooks

> [!NOTE]
>
> * Alle systemeigenen Schemaelemente adaptiver Karten, mit Ausnahme von `Action.Submit`, werden vollständig unterstützt.
> * Die unterstützten Aktionen sind [**Action.OpenURL**](https://adaptivecards.io/explorer/Action.OpenUrl.html), [**Action.ShowCard**](https://adaptivecards.io/explorer/Action.ShowCard.html) und [**Action.ToggleVisibility**](https://adaptivecards.io/explorer/Action.ToggleVisibility.html).

Führen Sie die folgenden Schritte aus, um adaptive Karten über einen eingehenden Webhook zu senden:

1. [Richten Sie einen benutzerdefinierten Webhook](~/webhooks-and-connectors/how-to/add-incoming-webhook.md) in Microsoft Teams ein.
1. Erstellen Sie die JSON-Datei für adaptive Karten mithilfe des folgenden Codes:

    ```json
    {
       "type":"message",
       "attachments":[
          {
             "contentType":"application/vnd.microsoft.card.adaptive",
             "contentUrl":null,
             "content":{
                "$schema":"http://adaptivecards.io/schemas/adaptive-card.json",
                "type":"AdaptiveCard",
                "version":"1.2",
                "body":[
                    {
                    "type": "TextBlock",
                    "text": "For Samples and Templates, see [https://adaptivecards.io/samples](https://adaptivecards.io/samples)"
                    }
                ]
             }
          }
       ]
    }
    ```

    Die Eigenschaften für die JSON-Datei für adaptive Karten sind wie folgt:

    * Das Feld `"type"` muss vom Typ `"message"` sein.
    * Das Array `"attachments"` enthält eine Reihe von Kartenobjekten.
    * Das Feld `"contentType"` muss auf den Typ "adaptive Karte" festgelegt werden.
    * Das Objekt `"content"` ist die in JSON formatierte Karte.

1. Testen Sie Ihre adaptive Karte mit Postman:

    * Testen Sie die adaptive Karte mit [Postman](https://www.postman.com), um eine POST-Anforderung an die URL zu senden, die zum Einrichten des eingehenden Webhooks erstellt wurde.
    * Fügen Sie die JSON-Datei in den Textkörper der Anforderung ein, und zeigen Sie die Nachricht der adaptiven Karte in Microsoft Teams an.

> [!TIP]
> Verwenden Sie [Codebeispiele und Vorlagen](https://adaptivecards.io/samples) für adaptive Karten, um den Textkörper der POST-Anforderung zu testen.

## <a name="rate-limiting-for-connectors"></a>Begrenzung der Datenübertragungsrate für Connectors

Die Grenzwerte für die Datenübertragungsrate von Anwendungen steuern, wieviel Datenverkehr von einem Connector oder eingehenden Webhook in einem Kanal generiert werden darf. Microsoft Teams verfolgt Anforderungen anhand eines Fensters mit fester Datenübertragungsrate und über einen inkrementellen Zähler, der in Sekunden misst. Wenn in einer Sekunde mehr als vier Anforderungen gestellt werden, wird die Clientverbindung gedrosselt, bis das Fenster auf die Dauer der festen Datenübertragungsrate aktualisiert wird.

### <a name="transactions-per-second-thresholds"></a>Schwellenwerte für Transaktionen pro Sekunde

Die folgende Tabelle enthält die Details zu zeitbasierten Transaktionen:

| Zeit in Sekunden  | Maximal zulässige Anforderungen  |
|---|---|
| 1   | 4  |  
| 30   | 60  |  
| 3600   | 100  |
| 7200 | 150  |
| 86400  | 1800  |

Eine [Wiederholungslogik mit exponentiellem Backoff](/azure/architecture/patterns/retry) kann die Begrenzung der Datenübertragungsrate in Fällen verringern, in denen Anforderungen die Grenzwerte innerhalb einer Sekunde überschreiten. Befolgen Sie die [bewährten Methoden](../../bots/how-to/rate-limit.md), um zu vermeiden, dass die Ratenbegrenzungen erreicht werden.

> [!NOTE]
> Eine [Wiederholungslogik mit exponentiellem Backoff](/azure/architecture/patterns/retry) kann die Begrenzung der Datenübertragungsrate in Fällen verringern, in denen Anforderungen die Grenzwerte innerhalb einer Sekunde überschreiten. Verweisen Sie auf [HTTP 429-Antworten](../../bots/how-to/rate-limit.md#handle-http-429-responses), um zu vermeiden, dass die Ratenbegrenzungen erreicht werden.

```csharp
// Please note that response body needs to be extracted and read 
// as Connectors do not throw 429s
try
{
    // Perform Connector POST operation     
    var httpResponseMessage = await _client.PostAsync(IncomingWebhookUrl, new StringContent(content));
    // Read response content
    var responseContent = await httpResponseMessage.Content.ReadAsStringAsync();
    if (responseContent.Contains("Microsoft Teams endpoint returned HTTP error 429")) 
    {
        // initiate retry logic
    }
}
```

Diese Begrenzungen haben den Zweck, das Spamming eines Kanals durch einen Connector zu verringern und Endbenutzern eine optimale Benutzererfahrung zu gewährleisten.

## <a name="see-also"></a>Siehe auch

* [Office 365 Connectors für Microsoft Teams](~/webhooks-and-connectors/how-to/connectors-creating.md)
* [Erstellen eines eingehenden Webhooks](~/webhooks-and-connectors/how-to/add-incoming-webhook.md)
* [Erstellen eines ausgehenden Webhooks](~/webhooks-and-connectors/how-to/add-outgoing-webhook.md)
* [Ratenbegrenzungen für Microsoft Teams-Bot-Nachrichten](~/bots/how-to/rate-limit.md)
* [Erstellen von Registerkarten mit adaptiven Karten](~/tabs/how-to/build-adaptive-card-tabs.md)
* [Formatieren von Karten in Microsoft Teams](~/task-modules-and-cards/cards/cards-format.md)
