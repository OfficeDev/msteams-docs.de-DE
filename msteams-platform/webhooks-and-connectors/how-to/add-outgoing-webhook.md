---
title: Erstellen eines ausgehenden Webhooks
author: laujan
description: beschreibt, wie ein ausgehender Webhook erstellt wird.
ms.topic: conceptual
ms.localizationpriority: high
ms.author: lajanuar
keywords: Teams-Registerkarten ausgehender Webhook aktionsfähige Nachricht überprüfen Webhook
ms.openlocfilehash: 2b77118e76bfde8c0fac7c74fce4dab1d78c7dd5
ms.sourcegitcommit: 2fdca6fb0ade3f6b460eb9a4dfea0a8e2ab8d3b9
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 03/08/2022
ms.locfileid: "63356294"
---
# <a name="create-outgoing-webhook"></a>Ausgehenden Webhook erstellen

Der ausgehende Webhook fungiert als Bot und sucht mithilfe von **@mention** nach Nachrichten in Kanälen. Es sendet Benachrichtigungen an externe Webdienste und antwortet mit umfangreichen Nachrichten, die Karten und Bilder enthalten. Es hilft, den Erstellungsprozess von Bots über die [Microsoft Bot Framework](https://dev.botframework.com/) zu überspringen.

<!--- TBD: Edit this article.
* Admonitions/alerts may be overused in this article. Check once.
* An important alert at the end of this table does not make sense. Also, it has a code snippet inside it.
* Some screenshots like teamschannel.png may be redundant. Check once.
* Some headings use title case. We use sentence case for titles.
* Check for markdownlint errors. 
* Try using &nbsp; to add spaces in codeblocks for indentation and remove the hard tabs.
* Table with just a row is not really needed. Provide the content without tabulating it.
--->

## <a name="key-features-of-outgoing-webhook"></a>Wichtige Features des ausgehenden Webhooks

Die folgende Tabelle enthält die Features und die Beschreibung ausgehender Webhooks:

| Features | Beschreibung |
| ------- | ----------- |
| Konfigurationsbereich| Webhooks werden auf Teamebene definiert. Der obligatorische Einrichtungsprozess für jeden einzelnen fügt einen ausgehenden Webhook hinzu. |
| Reaktives Messaging| Benutzer müssen @mention verwenden, damit der Webhook Nachrichten empfängt. Derzeit können Benutzer nur eine Nachricht an einen ausgehenden Webhook in öffentlichen Kanälen senden und nicht innerhalb des persönlichen oder privaten Bereichs. |
|Standard-HTTP-Nachrichtenaustausch|Antworten werden in derselben Kette wie die ursprüngliche Anforderungsnachricht angezeigt und können beliebige Bot Framework-Nachrichteninhalte enthalten. Beispielsweise Rich-Text, Bilder, Karten und Emojis. Ausgehende Webhooks können zwar Karten, jedoch keine Kartenaktionen (mit Ausnahme von `openURL`) verwenden.|
| Unterstützung der Teams-API-Methode|Ausgehende Webhooks senden einen HTTP POST an einen Webdienst und erhalten eine Antwort. Sie können nicht auf andere APIs zugreifen, um z. B. die Liste oder die Liste der Kanäle in einem Team abzurufen.|

## <a name="create-outgoing-webhooks"></a>Erstellen ausgehender Webhooks

Erstellen Sie ausgehende Webhooks, und fügen Sie Benutzerdefinierte Bots zu Teams hinzu.

Folgen Sie diesen Schritten, um einen ausgehenden Webhook zu erstellen:

1. Wählen Sie im linken Bereich **Teams** aus. Die **Teams**-Seite wird angezeigt:

    ![Teams channel](~/assets/images/teamschannel.png)

1. Wählen Sie auf der Seite **Teams** das erforderliche Team aus, um einen ausgehenden Webhook zu erstellen, und wählen Sie die &#8226;&#8226;&#8226; aus. Wählen Sie im Dropdownmenü **Team verwalten** aus:

    ![Ausgehenden Webhook erstellen](~/assets/images/outgoingwebhook1.png)

1. Wählen Sie die Registerkarte **Apps** auf der Kanalseite aus:

    ![Erstellen eines ausgehenden Webhooks](~/assets/images/outgoingwebhook2.png)

1. Wählen Sie **Erstellen eines ausgehenden Webhooks** aus:

    ![Erstellen ausgehender Webhooks](~/assets/images/outgoingwebhook3.png)

1. Geben Sie auf der Seite **Erstellen eines ausgehenden Webhooks** die folgenden Details ein:

    * **Name**: Der Webhooktitel und die Registerkarte @mention.
    * **Rückruf-URL**: Der HTTPS-Endpunkt, der JSON-Nutzlasten akzeptiert und POST-Anforderungen von Teams empfängt.
    * **Beschreibung**: Eine ausführliche Zeichenfolge, die auf der Profilkarte und im App-Dashboard auf Teamebene angezeigt wird.
    * **Profilbild**: Ein App-Symbol für Ihren Webhook, das optional ist.

1. Wählen Sie **Erstellen** aus. Der ausgehende Webhook wird dem Kanal des aktuellen Teams hinzugefügt:

    ![Ausgehenden Webhook erstellen](~/assets/images/outgoingwebhook.png)

Ein [Hash-based Message Authentication Code (HMAC)](https://security.stackexchange.com/questions/20129/how-and-when-do-i-use-hmac/20301) Dialogfeld wird angezeigt. Es handelt sich um ein Sicherheitstoken, das zum Authentifizieren von Aufrufen zwischen Teams und dem angegebenen externen Dienst verwendet wird. Das HMAC-Sicherheitstoken läuft nicht ab und ist für jede Konfiguration eindeutig.

>[!NOTE]
> Der ausgehende Webhook steht den Benutzern des Teams nur zur Verfügung, wenn die URL gültig ist und die Server- und Clientauthentifizierungstoken gleich sind. Beispielsweise ein HMAC-Händeschütteln.

Das folgende Szenario enthält die Details zum Hinzufügen eines ausgehenden Webhooks:

* Szenario: Pushen von Änderungsstatusbenachrichtigungen auf einem Teams-Kanaldatenbankserver an Ihre App.
* Beispiel: Sie haben eine Branchen-App, die alle CRUD-Vorgänge (Erstellen, Lesen, Aktualisieren und Löschen) verfolgt. Diese Vorgänge werden von Benutzern der Personalabteilung des Teams-Kanals in einem Office 365-Mandanten an die Mitarbeiterdatensätze vorgenommen.

# <a name="url-json-payload"></a>[JSON-Nutzlast der URL](#tab/urljsonpayload)

**erstellen Sie eine URL auf dem Server Ihrer App, um eine POST-Anforderung mit einer JSON-Nutzlast zu akzeptieren und zu verarbeiten**

Ihr Dienst empfängt Nachrichten in einem standardmäßigen Azure Bot Service-Messagingschema. Der Bot Framework-Connector ist ein RESTful-Dienst, der es ermöglicht, den Austausch von Nachrichten im JSON-Format über HTTPS-Protokolle zu verarbeiten, wie in der [Azure Bot Service-API](/bot-framework/rest-api/bot-framework-rest-connector-api-reference) dokumentiert. Alternativ können Sie dem Microsoft Bot Framework SDK folgen, um Nachrichten zu verarbeiten und zu analysieren. Weitere Informationen finden Sie unter [Übersicht über Azure Bot Service](/azure/bot-service/bot-service-overview-introduction).

Ausgehende Webhooks sind auf die `team`-Ebene beschränkt und für alle Teammitglieder sichtbar. Benutzer müssen den Namen des ausgehenden Webhooks **\@erwähnen**, um ihn im Kanal aufzurufen.

# <a name="verify-hmac-token"></a>[HMAC-Token überprüfen](#tab/verifyhmactoken)

**Erstellen einer Methode zum Überprüfen des HMAC-Tokens für ausgehenden Webhook**

Beispiel für eingehende Nachricht und ID: "contoso" von SigningKeyDictionary von {"contoso", "vqF0En+Z0ucuRTM/01o2GuhMH3hKKk/N2bOmlM31zaA=" }.

Verwenden Sie den Wert "HMAC 03TCao0i55H1eVKUusZOTZRjtvYTs+mO41mPL+R1e1U=" in der Autorisierung des Anforderungsheaders.

Um sicherzustellen, dass Ihr Dienst nur Anrufe von tatsächlichen Teams-Clients empfängt, stellt Teams einen HMAC-Code im HTTP-`hmac`-Autorisierungsheader bereit. Schließen Sie den Code immer in Ihr Authentifizierungsprotokoll ein.

Ihr Code muss die in der Anforderung enthaltene HMAC-Signatur immer wie folgt überprüfen:

* Generieren Sie das HMAC-Token aus dem Anforderungstext der Nachricht. Für die meisten Plattformen gibt es dafür Standardbibliotheken, z. B. [Crypto](https://nodejs.org/api/crypto.html#crypto_crypto) für Node.js und [Teams-Webhookbeispiel](https://github.com/OfficeDev/microsoft-teams-sample-outgoing-webhook/blob/23eb61da5a18634d51c5247944843da9abed01b6/WebhookSampleBot/Models/AuthProvider.cs) für C\#. Microsoft Teams verwendet SHA256 HMAC-Standardkryptografie. Sie müssen den Text in ein Bytearray in UTF8 konvertieren.
* Berechnen Sie den Hash aus dem Bytearray des Sicherheitstokens, das von Teams bereitgestellt wurde, als Sie den ausgehenden Webhook im Teams-Client registriert haben. Siehe [Erstellen eines ausgehenden Webhooks](#create-outgoing-webhook).
* Konvertieren Sie den Hash mithilfe der UTF-8-Codierung in eine Zeichenfolge.
* Vergleichen Sie den Zeichenfolgenwert des generierten Hashs mit dem in der HTTP-Anforderung angegebenen Wert.

# <a name="method-to-respond"></a>[Antwortmethode](#tab/methodtorespond)

**Erstellen einer Methode zum Senden einer Erfolgs- oder Fehlerantwort**

Antworten von ausgehenden Webhooks werden in derselben Antwortkette wie die ursprüngliche Nachricht angezeigt. Wenn der Benutzer eine Abfrage ausführt, gibt Microsoft Teams eine synchrone HTTP-Anforderung an Ihren Dienst aus, und Ihr Code erhält fünf Sekunden Zeit, um auf die Nachricht zu reagieren, bevor ein Timeout der Verbindung auftritt und sie beendet wird.

### <a name="example-response"></a>Beispielantwort

```json
{
    "type": "message",
    "text": "This is a reply!"
}
```

---

> [!NOTE]
> * Sie können mit einem ausgehendem Webhook adaptive Karten, Herokarten und SMS als Anlage senden.
> * Karten unterstützen die Formatierung. Weitere Informationen finden Sie unter [Karten mit Markdown formatieren](~/task-modules-and-cards/cards/cards-format.md?tabs=adaptive-md%2Cconnector-html#format-cards-with-markdown).

Die folgenden Codes sind Beispiele für eine adaptive Kartenantwort:

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

---

## <a name="code-sample"></a>Codebeispiel

|**Beispielname** | **Beschreibung** | **.NET** | **Node.js** |
|----------------|------------------|--------|----------------|
| Ausgehende Webhooks | Beispiele zum Erstellen von benutzerdefinierten Bots für die Verwendung in Microsoft Teams.| [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/outgoing-webhook/csharp) | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/outgoing-webhook/nodejs)|


## <a name="step-by-step-guide"></a>Schrittweise Anleitung

Befolgen Sie die [Schritt-für-Schritt-Anleitung](../../sbs-outgoing-webhooks.yml), um ausgehende Webhooks in Teams zu erstellen.

## <a name="see-also"></a>Siehe auch

* [Erstellen eines eingehenden Webhooks](~/webhooks-and-connectors/how-to/add-incoming-webhook.md)
* [Erstellen eines Office 365-Connectors](~/webhooks-and-connectors/how-to/connectors-creating.md)
* [Nachrichten erstellen und senden](~/webhooks-and-connectors/how-to/connectors-using.md)
