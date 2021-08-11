---
title: Erstellen eines ausgehenden Webhooks
author: laujan
description: beschreibt, wie ein ausgehender Webhook erstellt wird
ms.topic: conceptual
localization_priority: Normal
ms.author: lajanuar
keywords: Teams-Registerkarten ausgehende Webhook-Nachricht mit Aktionen überprüfen Webhook
ms.openlocfilehash: 8dabf78cd27f0f59bd8ce617eb83ded24ecc3dc92478e7233bf8f8bb6a2a4e19
ms.sourcegitcommit: 3ab1cbec41b9783a7abba1e0870a67831282c3b5
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 08/07/2021
ms.locfileid: "57704300"
---
# <a name="create-outgoing-webhook"></a>Erstellen eines ausgehenden Webhooks

Der ausgehende Webhook fungiert als Bot und sucht **mithilfe von @mention** nach Nachrichten in Kanälen. Es sendet Benachrichtigungen an externe Webdienste und antwortet mit umfangreichen Nachrichten, die Karten und Bilder enthalten. Es hilft, den Prozess der Erstellung von Bots über die [Microsoft Bot Framework](https://dev.botframework.com/)zu überspringen.

## <a name="key-features-of-outgoing-webhook"></a>Wichtige Features des ausgehenden Webhooks

Die folgende Tabelle enthält die Features und die Beschreibung ausgehender Webhooks:

| Features | Beschreibung |
| ------- | ----------- |
| Bereichskonfiguration| Webhooks sind auf Teamebene beschränkt. Der obligatorische Einrichtungsprozess für jedes Add-In fügt einen ausgehenden Webhook hinzu. |
| Reaktives Messaging| Benutzer müssen @mention verwenden, damit der Webhook Nachrichten empfängt. Derzeit können Benutzer nur einen ausgehenden Webhook in öffentlichen Kanälen und nicht innerhalb des persönlichen oder privaten Bereichs senden. |
|Standardmäßiger HTTP-Nachrichtenaustausch|Antworten werden in derselben Kette wie die ursprüngliche Anforderungsnachricht angezeigt und können beliebige Bot Framework-Nachrichteninhalte enthalten, z. B. Rich-Text, Bilder, Karten und Emojis. Ausgehende Webhooks können zwar Karten verwenden, jedoch keine Kartenaktionen außer `openURL` .|
| Teams API-Methodenunterstützung|Ausgehende Webhooks senden einen HTTP POST an einen Webdienst und erhalten eine Antwort. Sie können nicht auf andere APIs zugreifen, z. B. auf die Liste oder die Liste der Kanäle in einem Team.|

## <a name="create-outgoing-webhooks"></a>Erstellen ausgehender Webhooks

Erstellen Sie ausgehende Webhooks, und fügen Sie Teams benutzerdefinierte Bots hinzu.

**So erstellen Sie einen ausgehenden Webhook**

1. Wählen Sie im linken Bereich **Teams** aus. Die **Teams** Seite wird angezeigt:

    ![Teams channel](~/assets/images/teamschannel.png)

1. Wählen Sie auf der **Seite Teams** das erforderliche Team aus, um einen ausgehenden Webhook zu erstellen, und wählen Sie die &#8226;&#8226;&#8226; aus. Wählen Sie im Dropdownmenü **"Team verwalten"** aus:

    ![Erstellen eines ausgehenden Webhooks](~/assets/images/outgoingwebhook1.png)

1. Wählen Sie die Registerkarte **"Apps"** auf der Kanalseite aus:

    ![Erstellen eines ausgehenden Webhooks](~/assets/images/outgoingwebhook2.png)

1. Wählen Sie **"Ausgehenden Webhook erstellen" aus:**

    ![Erstellen ausgehender Webhooks](~/assets/images/outgoingwebhook3.png)

1. Geben Sie die folgenden Details auf der Seite **"Erstellen eines ausgehenden Webhooks" ein:**

    * **Name:** Der Webhook-Titel und die Registerkarte @mention.
    * **Rückruf-URL:** Der HTTPS-Endpunkt, der JSON-Nutzlasten akzeptiert und POST-Anforderungen von Teams empfängt.
    * **Beschreibung:** Eine detaillierte Zeichenfolge, die auf der Profilkarte und im App-Dashboard auf Teamebene angezeigt wird.
    * **Profilbild:** Ein App-Symbol für Ihren Webhook, das optional ist.

1. Wählen Sie **Erstellen** aus. Der ausgehende Webhook wird dem Kanal des aktuellen Teams hinzugefügt:

    ![Erstellen von ausgehenden Webhooks](~/assets/images/outgoingwebhook.png)

Ein [Hashbasiertes Dialogfeld mit dem Nachrichtenauthentifizierungscode (Message Authentication Code, HMAC)](https://security.stackexchange.com/questions/20129/how-and-when-do-i-use-hmac/20301) wird angezeigt. Es handelt sich um ein Sicherheitstoken, das zum Authentifizieren von Aufrufen zwischen Teams und dem angegebenen externen Dienst verwendet wird.

>[!NOTE]
> Der ausgehende Webhook ist für die Benutzer des Teams nur verfügbar, wenn die URL gültig ist und die Server- und Clientauthentifizierungstoken gleich sind. Beispielsweise ein HMAC-Handshake.

Das folgende Szenario enthält die Details zum Hinzufügen eines ausgehenden Webhooks:

* Szenario: Push-Änderungsstatusbenachrichtigungen auf einem Teams Kanaldatenbankserver an Ihre App.
* Beispiel: Sie verfügen über eine Branchen-App, die alle CRUD-Vorgänge verfolgt, z. B. erstellen, lesen, aktualisieren und löschen. Diese Vorgänge werden den Mitarbeiterdatensätzen von Teams Kanal-HR-Benutzern in einem Office 365 Mandanten vorgenommen.

# <a name="url-json-payload"></a>[JSON-URL-Nutzlast](#tab/urljsonpayload)
**Erstellen Sie eine URL auf dem Server Ihrer App, um eine POST-Anforderung mit einer JSON-Nutzlast zu akzeptieren und zu verarbeiten.**

Ihr Dienst empfängt Nachrichten in einem standardmäßigen Nachrichtenschema des Azure-Botdiensts. Der Bot Framework-Connector ist ein REST-Dienst, der den Austausch von JSON-formatierten Nachrichten über HTTPS-Protokolle verarbeiten kann, wie in der [Azure Bot Service-API](/bot-framework/rest-api/bot-framework-rest-connector-api-reference)dokumentiert. Alternativ können Sie dem Microsoft Bot Framework SDK folgen, um Nachrichten zu verarbeiten und zu analysieren. Weitere Informationen finden Sie in [der Übersicht über Azure Bot Service.](/azure/bot-service/bot-service-overview-introduction)

Ausgehende Webhooks sind auf die Ebene beschränkt `team` und für alle Teammitglieder sichtbar. Benutzer müssen den Namen des ausgehenden Webhooks **\@ erwähnen,** um ihn im Kanal aufzurufen.

# <a name="verify-hmac-token"></a>[Überprüfen des HMAC-Tokens](#tab/verifyhmactoken)
**Erstellen einer Methode zum Überprüfen des HMAC-Tokens für ausgehenden Webhook**

Using example of inbound message and ID: "contoso" of SigningKeyDictionary of {"contoso", "vqF0En+Z0ucuRTM/01o2GuhMH3hKKk/N2bOmlM31zaA=" }.

Verwenden Sie den Wert "HMAC 03TCao0i55H1eVKUusZOTZRjtvYTs+mO41mPL+R1e1U=" in der Autorisierung des Anforderungsheaders.

Um sicherzustellen, dass Ihr Dienst nur Aufrufe von tatsächlichen Teams Clients empfängt, stellt Teams einen HMAC-Code im `hmac` HTTP-Autorisierungsheader bereit. Fügen Sie immer den Code in Ihr Authentifizierungsprotokoll ein.

Ihr Code muss die in der Anforderung enthaltene HMAC-Signatur immer wie folgt überprüfen:

* Generieren Sie das HMAC-Token aus dem Anforderungstext der Nachricht. Es gibt Standardbibliotheken, um dies auf den meisten Plattformen zu tun, z. [B. Crypto](https://nodejs.org/api/crypto.html#crypto_crypto) für Node.js und [Teams Webhook-Beispiel](https://github.com/OfficeDev/microsoft-teams-sample-outgoing-webhook/blob/23eb61da5a18634d51c5247944843da9abed01b6/WebhookSampleBot/Models/AuthProvider.cs) für C \# ). Microsoft Teams verwendet standardmäßige SHA256 HMAC-Kryptografie. Sie müssen den Textkörper in UTF8 in ein Bytearray konvertieren.
* Berechnen Sie den Hash aus dem Bytearray des Sicherheitstokens, das von Teams bereitgestellt wird, wenn Sie den ausgehenden Webhook im Teams-Client registriert haben. Siehe [Erstellen eines ausgehenden Webhooks.](#create-outgoing-webhook)
* Konvertieren Sie den Hash in eine Zeichenfolge mithilfe der UTF-8-Codierung.
* Vergleichen Sie den Zeichenfolgenwert des generierten Hash mit dem in der HTTP-Anforderung angegebenen Wert.

# <a name="method-to-respond"></a>[Zu reagierende Methode](#tab/methodtorespond)
**Erstellen einer Methode zum Senden einer Erfolgs- oder Fehlerantwort**

Antworten von ausgehenden Webhooks werden in der gleichen Antwortkette wie die ursprüngliche Nachricht angezeigt. Wenn der Benutzer eine Abfrage ausführt, gibt Microsoft Teams eine synchrone HTTP-Anforderung an Ihren Dienst aus, und Ihr Code erhält fünf Sekunden, um auf die Nachricht zu antworten, bevor die Verbindung ein Zeitüberschreitung auftritt und beendet wird.

### <a name="example-response"></a>Beispielantwort

```json
{
    "type": "message",
    "text": "This is a reply!"
}
```
---

> [!NOTE]
> * Sie können adaptive Karte, Hero-Karte und Textnachrichten als Anlage mit ausgehenden Webhook senden.
> * Karten unterstützen die Formatierung. Weitere Informationen finden Sie unter [Formatieren von Karten mit Markdown.](~/task-modules-and-cards/cards/cards-format.md?tabs=adaptive-md%2Cconnector-html#format-cards-with-markdown)

Die folgenden Codes sind Beispiele für eine Adaptive Kartenantwort:

# <a name="cnet"></a>[C#/.NET](#tab/dotnet)

```csharp
string content = await this.Request.Content.ReadAsStringAsync();
Activity incomingActivity = JsonConvert.DeserializeObject<Activity>(content);

var Card = new AdaptiveCard(new AdaptiveSchemaVersion("1.4"))
{
    Body = new List<AdaptiveElement>()
    {
        new AdaptiveTextBlock(){Text= $"Request sent by: {incomingActivity.From.Name}"},
        new AdaptiveImage(){Url=new Uri("https://c.s-microsoft.com/en-us/CMSImages/DesktopContent-04_UPDATED.png?version=43c80870-99dd-7fb1-48c0-59aced085ab6")},
        new AdaptiveTextBlock(){Text="Sample image for Adaptive Card.."}
    }
};

var attachment = new Attachment()
{
    ContentType = AdaptiveCard.ContentType,
    Content = Card
};

var sampleResponseActivity = new Activity
{
    Attachments = new [] { attachment }
};

return sampleResponseActivity;
```

# <a name="javascriptnodejs"></a>[JavaScript/Node.js](#tab/javascript)

```javascript
var receivedMsg = JSON.parse(payload);
var responseMsg = JSON.stringify({
    "type": "message",
    "attachments": [
        {
            "contentType": "application/vnd.microsoft.card.adaptive",
            "contentUrl": null,
            "content": {
                "type": "AdaptiveCard",
                "version": "1.4",
                "body": [
                    {
                        "type": "TextBlock",
                        "text": "Request sent by: " + receivedMsg.from.name
                    },
                    {
                        "type": "Image",
                        "url": "https://c.s-microsoft.com/en-us/CMSImages/DesktopContent-04_UPDATED.png?version=43c80870-99dd-7fb1-48c0-59aced085ab6"
                    },
                    {
                        "type": "TextBlock",
                        "text": "Sample image for Adaptive Card."
                    }
                ]
            },
            "name": null,
            "thumbnailUrl": null
        }
    ]
});
```

# <a name="json"></a>[JSON](#tab/json)

```json
{
    "type": "message",
    "attachments": [
        {
            "contentType": "application/vnd.microsoft.card.adaptive",
            "content": {
                "type": "AdaptiveCard",
                "version": "1.4",
                "body": [
                    {
                        "type": "TextBlock",
                        "text": "Request sent by: Megan"
                    },
                    {
                        "type": "Image",
                        "url": "https://c.s-microsoft.com/en-us/CMSImages/DesktopContent-04_UPDATED.png?version=43c80870-99dd-7fb1-48c0-59aced085ab6"
                    },
                    {
                        "type": "TextBlock",
                        "text": "Sample image for Adaptive Card.."
                    }
                ]
            }
        }
    ]
}
```

* * *

## <a name="code-sample"></a>Codebeispiel

|**Beispielname** | **Beschreibung** | **.NET** | **Node.js** |
|----------------|------------------|--------|----------------|
| Ausgehende Webhooks | Beispiele zum Erstellen von benutzerdefinierten Bots, die in Microsoft Teams verwendet werden.| [Anzeigen](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/outgoing-webhook/csharp) | [Anzeigen](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/outgoing-webhook/nodejs)|

## <a name="see-also"></a>Siehe auch
* [Erstellen eines eingehenden Webhooks](~/webhooks-and-connectors/how-to/add-incoming-webhook.md)
* [Erstellen eines Office 365-Connectors](~/webhooks-and-connectors/how-to/connectors-creating.md)
* [Nachrichten erstellen und senden](~/webhooks-and-connectors/how-to/connectors-using.md)
