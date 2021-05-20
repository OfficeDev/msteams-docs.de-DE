---
title: Senden von Nachrichten an Connectors und Webhooks
description: Beschreibt die Verwendung von Office 365-Connectors in Microsoft Teams
ms.topic: how-to
localization_priority: Normal
keywords: Teams O365-Connector
ms.openlocfilehash: f9546b3550b3c53452c5856cfb87fdc6d71f2ad0
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566523"
---
# <a name="sending-messages-to-connectors-and-webhooks"></a>Senden von Nachrichten an Connectors und Webhooks

Wenn Sie eine Nachricht über Ihren Office 365-Connector oder eingehenden Webhook senden möchten, senden Sie eine JSON-Nutzlast an die Webhook-URL. Normalerweise wird diese Nutzlast in einer [Office 365-Connectorkarte](~/task-modules-and-cards/cards/cards-reference.md#office-365-connector-card) bestehen.

Sie können diesen JSON-Code auch zum Erstellen von Karten mit umfassenden Eingabeoptionen verwenden, wie z. B. Texteingabe, Mehrfachauswahl oder Auswählen eines Datums und einer Uhrzeit. Der Code, der die Karte generiert und an die Webhook-URL sendet, kann auf jedem gehosteten Dienst ausgeführt werden. Diese Karten sind als Bestandteil von Nachrichten mit Aktionen definiert und werden auch in [Karten](~/task-modules-and-cards/what-are-cards.md) unterstützt, die in Microsoft Teams-Bots und Messaging-Erweiterungen verwendet werden.

### <a name="example-connector-message"></a>Connector-Beispielnachricht

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

Diese Meldung erzeugt die folgende Karte im Kanal:

![Screenshot einer Connectorkarte](~/assets/images/connectors/connector_message.png)

## <a name="creating-actionable-messages"></a>Erstellen von Nachrichten mit Aktionen

Das Beispiel im vorherigen Abschnitt umfasst drei sichtbare Schaltflächen auf der Karte. Jede Schaltfläche wird in der `potentialAction`-Eigenschaft der Nachricht mithilfe von `ActionCard`-Aktionen definiert, die jeweils einen Eingabetyp enthalten: ein Textfeld, eine Datumsauswahl oder eine Mehrfachauswahlliste. Jeder `ActionCard`-Aktion ist eine Aktion zugeordnet, z. B. `HttpPOST`.

Connectorkarten unterstützen drei Arten von Aktionen:

- `ActionCard`: Zeigt einen oder mehrere Eingabetypen sowie die zugeordneten Aktionen an
- `HttpPOST`: Sendet eine POST-Anforderung an eine URL
- `OpenUri`: Öffnet einen URI in einem separaten Browser oder in einer anderen App; zielt optional unterschiedliche URIs basierend auf Betriebssystemen an

Die `ActionCard`-Aktion unterstützt drei Eingabetypen:

- `TextInput`: Ein ein- oder mehrzeiliges Textfeld mit optionaler Längenbegrenzung
- `DateInput`: Datumsauswahl mit optionaler Zeitauswahl
- `MultichoiceInput`: Eine Liste mit Auswahlmöglichkeiten, die entweder die Auswahl einer einzelnen Option oder mehrerer Optionen bietet

`MultichoiceInput` unterstützt eine `style`-Eigenschaft über die festgelegt wird, ob die Liste anfänglich vollständig erweitert angezeigt wird. Der Standardwert von `style` hängt vom `isMultiSelect`-Wert ab.

| `isMultiSelect` | `style`-Standardeinstellung |
| --- | --- |
| `false` oder nicht angegeben | `compact` |
| `true` | `expanded` |

Wenn Sie möchten, dass eine Liste mit Mehrfachauswahl zuerst kompakt angezeigt wird, müssen Sie sowohl `"isMultiSelect": true` als auch `"style": true` angeben.

Weitere Informationen zu Aktionen der Connectorkarte finden Sie unter **[Aktionen]**(/outlook/actionable-messages/card-reference#actions) in der Referenz der verwertbaren Nachrichtenkarte.

> [!NOTE]
> Die Angabe von `compact` für die `style`-Eigenschaft in Microsoft Teams entspricht der Angabe von `normal` für die `style`-Eigenschaft in Microsoft Outlook.
> 
> Bei der HttpPOST-Aktion ist das Bearertoken in den Anforderungen enthalten. Dieses Token enthält die Azure AD-Identität des Office 365-Benutzers, der die Aktion ausgeführt hat.

## <a name="setting-up-a-custom-incoming-webhook"></a>Einrichten eines benutzerdefinierten eingehenden Webhooks

Führen Sie die folgenden Schritte aus, um zu erfahren, wie Sie eine einfache Karte an einen Connector senden:

1. Wählen Sie in Microsoft Teams **Weitere Optionen** (**&#8943;**) neben dem Kanalnamen aus, und wählen Sie dann **Connectors** aus.
1. Scrollen Sie durch die Liste der Connectors bis zu **Eingehender Webhook**, und wählen Sie **Hinzufügen** aus.
1. Geben Sie einen Namen für den Webhook ein, laden Sie ein Bild hoch, das mit Daten aus dem Webhook verknüpft werden soll, und wählen Sie **Erstellen** aus.
1. Kopieren Sie den Webhook in die Zwischenablage, und speichern Sie ihn. Sie benötigen die Webhook-URL zum Senden von Informationen an Microsoft Teams.
1. Klicken Sie auf **Fertig**.

### <a name="post-a-message-to-the-webhook-using-curl"></a>Senden einer Nachricht an den Webhook mithilfe von cURL

In den folgenden Schritten wird [cURL](https://curl.haxx.se/) verwendet. Wir gehen davon aus, dass Sie es installiert haben und mit den Grundlagen seiner Nutzung vertraut sind.

1. Geben Sie den folgenden cURL-Befehl in die Befehlszeile ein:

   ```bash
   // on macOS or Linux
   curl -H 'Content-Type: application/json' -d '{"text": "Hello World"}' <YOUR WEBHOOK URL>
   ```

   ```bash
   // on Windows
   curl.exe -H "Content-Type:application/json" -d "{'text':'Hello World'}" <YOUR WEBHOOK URL>
   ```

1. Wenn die POST-Anforderung erfolgreich ist, sollte eine einfache **1** durch `curl` ausgegeben werden.
1. Überprüfen Sie den Microsoft Teams-Client. Die neue Karte sollte nun im Team bereitgestellt werden.

### <a name="post-a-message-to-the-webhook-using-powershell"></a>Senden einer Nachricht an den Webhook mithilfe von PowerShell

In den folgenden Schritten wird PowerShell verwendet. Wir gehen davon aus, dass Sie es installiert haben und mit den Grundlagen seiner Nutzung vertraut sind.

1. Geben Sie in der PowerShell-Eingabeaufforderung den folgenden Befehl ein:

   ```powershell
   Invoke-RestMethod -Method post -ContentType 'Application/Json' -Body '{"text":"Hello World!"}' -Uri <YOUR WEBHOOK URL>
   ```

1. Wenn die POST-Anforderung erfolgreich ist, sollte eine einfache **1** durch `Invoke-RestMethod` ausgegeben werden.
1. Überprüfen Sie den Microsoft Teams-Kanal, der der Webhook-URL zugeordnet ist. Die neue Karte sollte nun im Kanal bereitgestellt werden.

- [Zwei Symbole einschließen](../../concepts/build-and-test/apps-package.md#app-icons).
- Ändern Sie den `icons`-Teil des Manifests so, dass er auf die Dateinamen der Symbole anstelle von URLs verweist.

Die folgende manifest.jsin der Datei enthält die grundlegenden Elemente, die zum Testen und Übermitteln Ihrer App erforderlich sind:

> [!NOTE]
> Ersetzen Sie im folgenden Beispiel `id` und `connectorId` mit der GUID des Connectors.

#### <a name="example-manifestjson-with-connector"></a>Beispiel-manifest.JSON mit Connector

```json
{
  "$schema": "https://developer.microsoft.com/json-schemas/teams/v1.8/MicrosoftTeams.schema.json",
  "manifestVersion": "1.5",
  "id": "e9343a03-0a5e-4c1f-95a8-263a565505a5",
  "version": "1.0",
  "packageName": "com.sampleapp",
  "developer": {
    "name": "Publisher",
    "websiteUrl": "https://www.microsoft.com",
    "privacyUrl": "https://www.microsoft.com",
    "termsOfUseUrl": "https://www.microsoft.com"
  },
  "description": {
    "full": "This is a small sample app we made for you! This app has samples of all capabilities Microsoft Teams supports.",
    "short": "This is a small sample app we made for you!"
  },
  "icons": {
    "outline": "sampleapp-outline.png",
    "color": "sampleapp-color.png"
  },
  "connectors": [
    {
      "connectorId": "e9343a03-0a5e-4c1f-95a8-263a565505a5",
      "scopes": [
        "team"
      ]
    }
  ],
  "name": {
    "short": "Sample App",
    "full": "Sample App"
  },
  "accentColor": "#FFFFFF",
  "needsIdentity": "true"
}
```

## <a name="send-adaptive-cards-using-an-incoming-webhook"></a>Senden von adaptiven Karten mithilfe eines eingehenden Webhooks

> [!NOTE]
>
> ✔ Alle systemeigenen adaptiven Kartenschemaelemente, mit Ausnahme von `Action.Submit`, werden vollständig unterstützt.
>
> ✔ Die unterstützten Aktionen sind [**Action.OpenURL**](https://adaptivecards.io/explorer/Action.OpenUrl.html), [**Action.ShowCard**](https://adaptivecards.io/explorer/Action.ShowCard.html) und [**Action.ToggleVisibility**](https://adaptivecards.io/explorer/Action.ToggleVisibility.html).

### <a name="the-flow-for-sending-adaptive-cards-via-an-incoming-webhook-is-as-follows"></a>Der Datenstrom zum Senden von [adaptiven Karten](../../task-modules-and-cards/cards/cards-reference.md#adaptive-card) über einen eingehenden Webhook lautet wie folgt:

1. [Richten Sie einen benutzerdefinierten Webhook](#setting-up-a-custom-incoming-webhook) in Teams ein.</br></br>
1. Erstellen Sie Ihre JSON-Datei mit adaptiver Karte:

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

    > [!div class="checklist"]
    >
    > - Das Feld `"type"` muss vom Typ `"message"` sein.
    > - Das Array `"attachments"` enthält eine Reihe von Kartenobjekten.
    > - Das Feld `"contentType"` muss auf den Typ „adaptive Karte“ festgelegt werden.
    > - Das Objekt `"content"` ist die in JSON formatierte Karte.

1. Testen Sie Ihre adaptive Karte mit Postman.

Sie können Ihre adaptive Karte mithilfe von [Postman](https://www.postman.com) testen, um eine POST-Anforderung an die URL zu senden, die Sie beim Einrichten Ihres eingehenden Webhooks erstellt haben. Fügen Sie Ihre JSON-Datei in den Textkörper der Anforderung ein, und zeigen Sie die Nachricht Ihrer adaptiven Karte in Teams an.

>[!TIP]
> Sie können den Code der adaptiven Karte [Beispiele und Vorlagen](https://adaptivecards.io/samples) für den Textkörper Ihrer POST-Testanforderung verwenden.

## <a name="testing-your-connector"></a>Testen des Connectors

Um den Connector zu testen, laden Sie ihn wie jede andere App in ein Team hoch. Sie können ein .zip Paket mithilfe der Manifestdatei aus dem Connectors Developer Dashboard erstellen, das wie im vorherigen Abschnitt und den beiden Symboldateien geändert wurde.

Nachdem Sie die App hochgeladen haben, öffnen Sie die Liste der Connectors von einem beliebigen Kanal aus. Scrollen Sie nach unten, um Ihre App im Abschnitt **Hochgeladen** anzuzeigen:

![Screenshot des Abschnitts "Hochgeladen" im Connector-Dialogfeld](~/assets/images/connectors/connector_dialog_uploaded.png)

Sie können nun die Konfigurationsfunktion starten. Denken Sie daran, dass dieser Vorgang innerhalb von Microsoft Teams über ein Popupfenster erfolgt. Derzeit unterscheidet sich dieses Verhalten von der Konfigurationsfunktion in den von uns erstellten Connectoren. Wir arbeiten an einer Vereinheitlichung der Benutzererfahrung.

Um zu überprüfen, ob eine `HttpPOST`-Aktion ordnungsgemäß funktioniert, verwenden Sie Ihren [benutzerdefinierten eingehenden Webhook](#setting-up-a-custom-incoming-webhook).

## <a name="rate-limiting-for-connectors"></a>Begrenzung der Datenübertragungsrate für Connectors

Die Grenzwerte für die Anwendungsdatenübertragungsrate steuern den Datenverkehr, der von einem Connector oder eingehenden Webhook in einem Kanal generiert werden darf. Teams verfolgt Anforderungen über ein Fenster mit fester Datenübertragungsrate und einen inkrementellen Zähler, der in Sekunden gemessen wird.  Wenn zu viele Anforderungen gestellt werden, wird die Clientverbindung gedrosselt, bis das Fenster aktualisiert wird, d. h. für die Dauer der festen Datenübertragungsrate.

### <a name="transactions-per-second-thresholds"></a>**Schwellenwerte für Transaktionen pro Sekunde**

| Zeit (Sekunden)  | Maximal zulässige Anforderungen  |
|---|---|
| 1   | 4   |  
| 30   | 60  |  
| 3600   | 100  |
| 7200 | 150  |
| 86400  | 1800  |

Eine [Wiederholungslogik mit exponentiellem Backoff](/azure/architecture/patterns/retry) wie unten würde die Begrenzung der Datenübertragungsrate in Fällen abmildern, in denen Anforderungen die Grenzwerte innerhalb einer Sekunde überschreiten. Lesen Sie die [HTTP 429-Antworten](../../bots/how-to/rate-limit.md#handle-http-429-responses), um zu vermeiden, dass die Ratenbegrenzungen überschritten werden.

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
 
Diese Limits haben den Zweck, das Spamming eines Kanals durch einen Connector zu verringern und Ihren Endbenutzer eine optimale Benutzererfahrung zu gewährleisten.

## <a name="see-also"></a>Siehe auch

[Office 365 Steckverbinder — Microsoft Teams](/connectors/teams/)