---
title: Nachrichten erstellen und senden
author: laujan
description: Beschreibt die Verwendung von Office 365-Connectors in Microsoft Teams
ms.topic: how-to
ms.localizationpriority: medium
keywords: Teams O365-Connector
ms.openlocfilehash: 6d10a173079fb31db303e98bfaf0800ff048a187
ms.sourcegitcommit: fc9f906ea1316028d85b41959980b81f2c23ef2f
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 09/12/2021
ms.locfileid: "59156997"
---
# <a name="create-and-send-messages"></a>Nachrichten erstellen und senden

Sie können Nachrichten mit Aktionen erstellen und über eingehenden Webhook oder Office 365 Connector senden.

## <a name="create-actionable-messages"></a>Erstellen von Nachrichten mit Aktionen

Die Aktionen erfordernden Nachrichten enthalten drei sichtbare Schaltflächen auf der Karte. Jede Schaltfläche wird in der `potentialAction` Eigenschaft der Nachricht mithilfe von Aktionen `ActionCard` definiert, die jeweils einen Eingabetyp, ein Textfeld, eine Datumsauswahl oder eine Mehrfachauswahlliste enthalten. Jeder `ActionCard` hat eine zugeordnete Aktion, `HttpPOST` z. B. .

Die Connectorkarten unterstützen die folgenden Aktionen:

- `ActionCard`: Stellt einen oder mehrere Eingabetypen und zugeordnete Aktionen dar.
- `HttpPOST`: Sendet die POST-Anforderung an eine URL.
- `OpenUri`: Öffnet den URI in einem separaten Browser oder einer separaten App und richtet sich optional auf unterschiedliche URIs basierend auf Betriebssystemen.

Die `ActionCard`-Aktion unterstützt drei Eingabetypen:

- `TextInput`: Ein einzeiliges oder mehrzeiliges Textfeld mit optionaler Längenbeschränkung.
- `DateInput`: Eine Datumsauswahl mit einer optionalen Uhrzeitauswahl.
- `MultichoiceInput`: Eine aufgezählte Liste von Auswahlmöglichkeiten, die entweder eine einzelne oder mehrere Auswahlmöglichkeiten bietet.

`MultichoiceInput` unterstützt eine `style`-Eigenschaft über die festgelegt wird, ob die Liste anfänglich vollständig erweitert angezeigt wird. Der Standardwert `style` von hängt vom Folgenden `isMultiSelect` ab:

| `isMultiSelect` | `style`-Standardeinstellung |
| --- | --- |
| `false` oder nicht angegeben | `compact` |
| `true` | `expanded` |

Um die Mehrfachauswahlliste im kompakten Format anzuzeigen, müssen Sie beide `"isMultiSelect": true` und `"style": true` angeben.

Weitere Informationen zu Connectorkartenaktionen finden Sie unter ["Aktionen".](/outlook/actionable-messages/card-reference#actions)

> [!NOTE]
> * Die Angabe von `compact` für die `style`-Eigenschaft in Microsoft Teams entspricht der Angabe von `normal` für die `style`-Eigenschaft in Microsoft Outlook.
> * Bei der HttpPOST-Aktion ist das Bearertoken in den Anforderungen enthalten. Dieses Token enthält die Azure AD-Identität des Office 365-Benutzers, der die Aktion ausgeführt hat.

## <a name="send-a-message-through-incoming-webhook-or-office-365-connector"></a>Senden einer Nachricht über eingehenden Webhook oder Office 365 Connector

Um eine Nachricht über Ihren eingehenden Webhook oder Office 365 Connector zu senden, posten Sie eine JSON-Nutzlast an die Webhook-URL. Diese Nutzlast muss in Form einer [Office 365 Connectorkarte](~/task-modules-and-cards/cards/cards-reference.md#office-365-connector-card)sein.

Sie können diesen JSON-Code auch verwenden, um Karten mit umfangreichen Eingaben zu erstellen, z. B. Texteingabe, Mehrfachauswahl oder Auswählen von Datum und Uhrzeit. Der Code, der die Karte generiert und an die Webhook-URL sendet, kann auf jedem gehosteten Dienst ausgeführt werden. Diese Karten werden als Teil von Nachrichten mit Aktionen definiert und auch in [Karten](~/task-modules-and-cards/what-are-cards.md)unterstützt, die in Teams Bots und Messaging-Erweiterungen verwendet werden.

### <a name="example-of-connector-message"></a>Beispiel für eine Connectornachricht

Ein Beispiel für eine Connectornachricht ist:

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

Diese Nachricht enthält die folgende Karte im Kanal:

![Screenshot einer Connectorkarte](~/assets/images/connectorcard.png)

## <a name="send-messages-using-curl-and-powershell"></a>Senden von Nachrichten mit cURL und PowerShell

# <a name="curl"></a>[Curl](#tab/cURL)

**So posten Sie eine Nachricht im Webhook mit cURL**

1. Installieren Sie cURL mithilfe von: https://curl.haxx.se/ .

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
    > Wenn der POST erfolgreich ist, müssen Sie eine einfache Ausgabe von **1** `curl` sehen.

1. Überprüfen Sie den Microsoft Teams-Client für die neue bereitgestellte Karte.

# <a name="powershell"></a>[PowerShell](#tab/PowerShell)

 Voraussetzung: Installation von PowerShell und Einarbeitung in die grundlegende Verwendung.

**So posten Sie eine Nachricht mit PowerShell an den Webhook**

1. Geben Sie in der PowerShell-Eingabeaufforderung den folgenden Befehl ein:

   ```powershell
   Invoke-RestMethod -Method post -ContentType 'Application/Json' -Body '{"text":"Hello World!"}' -Uri <YOUR WEBHOOK URL>
   ```

    > [!NOTE]
    > Wenn der POST erfolgreich ist, müssen Sie eine einfache Ausgabe von **1** `Invoke-RestMethod` sehen.

1. Überprüfen Sie den Microsoft Teams-Kanal, der der Webhook-URL zugeordnet ist. Sie können die neue Karte sehen, die im Kanal veröffentlicht wurde. Bevor Sie den Connector zum Testen oder Veröffentlichen Ihrer App verwenden, müssen Sie folgendermaßen vorgehen:

    - [Zwei Symbole einschließen](../../concepts/build-and-test/apps-package.md#app-icons).
    - Ändern Sie den `icons` Teil des Manifests an die Dateinamen der Symbole anstelle von URLs.

---

## <a name="send-adaptive-cards-using-an-incoming-webhook"></a>Senden adaptiver Karten mit einem eingehenden Webhook

> [!NOTE]
> * Alle systemeigenen Schemaelemente adaptiver Karten mit Ausnahme `Action.Submit` von , werden vollständig unterstützt.
> * Die unterstützten Aktionen sind [**Action.OpenURL**](https://adaptivecards.io/explorer/Action.OpenUrl.html), [**Action.ShowCard**](https://adaptivecards.io/explorer/Action.ShowCard.html)und [**Action.ToggleVisibility**](https://adaptivecards.io/explorer/Action.ToggleVisibility.html).

**So senden Sie adaptive Karten über einen eingehenden Webhook**

1. [Richten Sie einen benutzerdefinierten Webhook](~/webhooks-and-connectors/how-to/add-incoming-webhook.md) in Teams ein.
1. Erstellen Sie die JSON-Datei für adaptive Karten mit dem folgenden Code:

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
    * Das `"contentType"` Feld muss auf den Typ "Adaptive Karte" festgelegt sein.
    * Das Objekt `"content"` ist die in JSON formatierte Karte.

1. Testen Sie Ihre adaptive Karte mit Postman:

    * Testen Sie die adaptive Karte mit [Postman,](https://www.postman.com) um eine POST-Anforderung an die URL zu senden, die erstellt wurde, um eingehenden Webhook einzurichten.
    * Fügen Sie die JSON-Datei in den Textkörper der Anforderung ein, und zeigen Sie die Adaptive Kartennachricht in Teams an.

> [!TIP]
> Verwenden Sie [Codebeispiele und Vorlagen](https://adaptivecards.io/samples) für adaptive Karten, um den Textkörper der POST-Anforderung zu testen.

## <a name="rate-limiting-for-connectors"></a>Begrenzung der Datenübertragungsrate für Connectors

Anwendungsratenbeschränkungen steuern den Datenverkehr, den ein Connector oder ein eingehender Webhook in einem Kanal generieren darf. Teams Anforderungen mithilfe eines Fensters mit fester Rate und eines inkrementellen Indikators in Sekunden nachverfolgen. Wenn in einer Sekunde mehr als vier Anforderungen gestellt werden, wird die Clientverbindung gedrosselt, bis das Fenster für die Dauer der festen Rate aktualisiert wird.

### <a name="transactions-per-second-thresholds"></a>Schwellenwerte für Transaktionen pro Sekunde

Die folgende Tabelle enthält die zeitbasierten Transaktionsdetails:

| Zeit in Sekunden  | Maximal zulässige Anforderungen  |
|---|---|
| 1   | 4   |  
| 30   | 60  |  
| 3600   | 100  |
| 7200 | 150  |
| 86400  | 1800  |

Eine [Wiederholungslogik mit exponentieller Back-Off](/azure/architecture/patterns/retry) kann die Ratenbegrenzung für Fälle verringern, in denen Anforderungen die Grenzwerte innerhalb einer Sekunde überschreiten. Befolgen Sie [bewährte Methoden,](../../bots/how-to/rate-limit.md) um zu vermeiden, dass die Ratengrenzen erreicht werden.

> [!NOTE]
> Eine [Wiederholungslogik mit exponentieller Back-Off](/azure/architecture/patterns/retry) kann die Ratenbegrenzung für Fälle verringern, in denen Anforderungen die Grenzwerte innerhalb einer Sekunde überschreiten. Lesen Sie die [HTTP 429-Antworten](../../bots/how-to/rate-limit.md#handle-http-429-responses), um zu vermeiden, dass die Ratenbegrenzungen überschritten werden.

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

Diese Grenzwerte sind vorhanden, um das Spamming eines Kanals über einen Connector zu reduzieren und eine optimale Benutzererfahrung sicherzustellen.

## <a name="see-also"></a>Siehe auch

* [Office 365 Connectors für Microsoft Teams](~/webhooks-and-connectors/how-to/connectors-creating.md)
* [Erstellen eines eingehenden Webhooks](~/webhooks-and-connectors/how-to/add-incoming-webhook.md)
* [Erstellen eines ausgehenden Webhooks](~/webhooks-and-connectors/how-to/add-outgoing-webhook.md)
