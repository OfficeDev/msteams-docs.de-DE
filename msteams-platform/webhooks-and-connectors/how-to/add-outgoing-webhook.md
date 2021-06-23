---
title: Hinzufügen von benutzerdefinierten Bots zu Microsoft Teams mit ausgehenden Webhooks
description: beschreibt, wie ein ausgehender Webhook hinzugefügt wird
ms.topic: conceptual
ms.author: lajanuar
localization_priority: Normal
keywords: Teams-Registerkarten ausgehende Webhook-Nachricht mit Aktionen überprüfen Webhook
ms.openlocfilehash: 2fac6f42e27a4c8cb3d079ea281d458a4dfe41ed
ms.sourcegitcommit: 623d81eb079d1842813265746a5fe0fe6311b196
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/22/2021
ms.locfileid: "53069182"
---
# <a name="add-custom-bots-to-teams-with-outgoing-webhooks"></a>Hinzufügen von benutzerdefinierten Bots zu Teams mit ausgehenden Webhooks

## <a name="outgoing-webhooks-in-teams"></a>Ausgehende Webhooks in Teams

Webhooks sind eine hervorragende Möglichkeit für Teams die Integration in externe Apps. Ein Webhook ist im Wesentlichen eine POST-Anforderung, die an eine Rückruf-URL gesendet wird. Ausgehende Webhooks ermöglichen Benutzern das Senden von Nachrichten an Ihren Webdienst, ohne den vollständigen Prozess der Erstellung von Bots über die Microsoft Bot Framework durchlaufen zu [müssen.](https://dev.botframework.com/)

Ausgehender Webhook sendet Daten von Teams an einen beliebigen ausgewählten Dienst, der eine JSON-Nutzlast akzeptieren kann. Nachdem sie die ausgehenden Webhooks zu einem Team hinzugefügt haben, fungiert sie als Bot und sucht mit **\@ erwähnungen** nach Nachrichten in Kanälen. Es sendet Benachrichtigungen an externe Webdienste und antwortet mit umfangreichen Nachrichten, die Karten und Bilder enthalten.

## <a name="outgoing-webhook-key-features"></a>Ausgehende Webhook-Schlüsselfeatures

| Feature | Beschreibung |
| ------- | ----------- |
| Bereichskonfiguration| Webhooks sind auf Teamebene beschränkt. Sie müssen den Einrichtungsprozess für jedes Team durchlaufen, in dem Sie Ihren ausgehenden Webhook hinzufügen möchten. |
| Reaktives Messaging| Benutzer müssen @mention verwenden, damit der Webhook Nachrichten empfängt. Derzeit können Benutzer nur einen ausgehenden Webhook in öffentlichen Kanälen und nicht innerhalb des persönlichen oder privaten Bereichs senden. |
|Standardmäßiger HTTP-Nachrichtenaustausch|Antworten werden in derselben Kette wie die ursprüngliche Anforderungsnachricht angezeigt und können beliebige Bot-Framework-Nachrichteninhalte enthalten, z. B. Rich-Text, Bilder, Karten und Emojis. Ausgehende Webhooks können zwar Karten verwenden, jedoch keine Kartenaktionen außer `openURL` .|
| Teams API-Methodenunterstützung|Ausgehender Webhook sendet einen HTTP POST an einen Webdienst und verarbeitet eine Antwort zurück. Sie können nicht auf andere APIs zugreifen, z. B. um die Liste oder die Liste der Kanäle in einem Team abzurufen.|

## <a name="creating-actionable-messages"></a>Erstellen von Nachrichten mit Aktionen

Die Connectorkarten enthalten drei sichtbare Schaltflächen auf der Karte. Jede Schaltfläche wird in der `potentialAction` Eigenschaft der Nachricht mithilfe von Aktionen `ActionCard` definiert. Jeder `ActionCard` enthält einen Eingabetyp, ein Textfeld, eine Datumsauswahl oder eine Mehrfachauswahlliste. Jeder `ActionCard` Aktion ist eine Aktion zugeordnet, `HttpPOST` z. B. .

Connectorkarten unterstützen drei Arten von Aktionen:

| Aktion | Beschreibung |
| ------- | ----------- |
| `ActionCard` |Stellt einen oder mehrere Eingabetypen und zugeordnete Aktionen dar.|
| `HttpPOST` | Sendet eine POST-Anforderung an eine URL. |
| `OpenUri` |  Öffnet einen URI in einem separaten Browser oder einer separaten App und richtet sich optional auf unterschiedliche URIs basierend auf Betriebssystemen.|

Die `ActionCard`-Aktion unterstützt drei Eingabetypen:

| Eingabetyp | Beschreibung |
| ------- | ----------- |
| `TextInput` | Ein einzeiliges oder mehrzeiliges Textfeld mit optionaler Längenbeschränkung. |
| `DateInput` | Eine Datumsauswahl mit einer optionalen Uhrzeitauswahl. |
| `MultichoiceInput` | Eine angegebene Liste von Auswahlmöglichkeiten, die entweder eine einzelne oder mehrere Auswahlmöglichkeiten bietet.|

`MultichoiceInput` unterstützt eine `style` Eigenschaft, die die Anzeige einer vollständig erweiterten Liste steuert. Der Standardwert von `style` hängt vom `isMultiSelect` Wert ab.

| `isMultiSelect` Wert  | `style` Standardwert  |
| --- | --- |
| `false` oder nicht angegeben | Der Standardstil lautet `compact`|
| `true` | Der Standardstil lautet `expanded` |

> [!NOTE]
> * Geben Sie sowohl `"isMultiSelect": true` und , wenn die `"style": true` Mehrfachauswahlliste in einer kompakten Formatvorlage angezeigt werden soll.
> * Das Auswählen `compact` der Eigenschaft in Teams `style` entspricht der Auswahl für die `normal` Eigenschaft in Microsoft `style` Outlook.
> * Webhooks unterstützen nur Office 365 Nachrichtenrückmeldungskarten und adaptive Karten.

Weitere Informationen zu Connectorkartenaktionen finden Sie unter **["Aktionen"](/outlook/actionable-messages/card-reference#actions)** in der Referenz zur Nachrichtenkarte mit Aktionen.

## <a name="adding-outgoing-webhooks-to-your-app"></a>Hinzufügen ausgehender Webhooks zu Ihrer App

**Szenario:** Pushänderungsstatusbenachrichtigungen auf einem Teams Kanaldatenbankserver an Ihre App.  
**Beispiel:** Sie verfügen über eine Branchen-App, die alle CRUD-Vorgänge nachzeichnet, die von Teams Hr-Benutzern über einen Office 365 Mandanten hinweg an Mitarbeiterdatensätzen vorgenommen wurden.

### <a name="1-create-a-url-on-your-apps-server-to-accept-and-process-a-post-request-with-a-json-payload"></a>1. Erstellen Sie eine URL auf dem Server Ihrer App, um eine POST-Anforderung mit einer JSON-Nutzlast zu akzeptieren und zu verarbeiten.

Ihr Dienst empfängt Nachrichten in einem standardmäßigen Nachrichtenschema des Azure-Botdiensts. Der Bot Framework-Connector ist ein REST-Dienst, der Es Ihrem Dienst ermöglicht, den Austausch von JSON-formatierten Nachrichten über HTTPS-Protokolle zu verarbeiten, wie in der [Azure Bot Service-API](/bot-framework/rest-api/bot-framework-rest-connector-api-reference)dokumentiert. Alternativ können Sie dem [Microsoft Bot Framework SDK] folgen, um Nachrichten zu verarbeiten und zu analysieren. Siehe auch [Informationen zum Azure Bot Service.](/azure/bot-service/bot-service-overview-introduction)


Ausgehende Webhooks sind auf die Ebene beschränkt `team` und für alle Teammitglieder sichtbar. Genau wie bei einem Bot müssen Benutzer den Namen des ausgehenden Webhooks **\@ erwähnen,** um ihn im Kanal aufzurufen.

### <a name="2-create-a-method-to-verify-the-outgoing-webhook-hmac-token"></a>2. Erstellen einer Methode zum Überprüfen des ausgehenden Webhook-HMAC-Tokens

#### <a name="hmac-signature-for-testing-with-code-example"></a>HMAC-Signatur für Tests mit Codebeispiel

Using example of inbound message and id: "contoso" of SigningKeyDictionary of {"contoso", "vqF0En+Z0ucuRTM/01o2GuhMH3hKKk/N2bOmlM31zaA=" }.

Verwenden Sie den Wert "HMAC 03TCao0i55H1eVKUusZOTZRjtvYTs+mO41mPL+R1e1U=" in der Autorisierung des Anforderungsheaders.

Um sicherzustellen, dass Ihr Dienst nur Aufrufe von tatsächlichen Teams Clients empfängt, stellt Teams einen HMAC-Code im `hmac` HTTP-Header bereit. Enthalten Sie immer den Code in Ihrem Authentifizierungsprotokoll.

Ihr Code muss immer die HMAC-Signatur überprüfen, die in der Anforderung enthalten ist:

* Generieren Sie das HMAC-Token aus dem Anforderungstext der Nachricht. Es gibt Standardbibliotheken, um dies auf den meisten Plattformen zu tun (siehe [Crypto](https://nodejs.org/api/crypto.html#crypto_crypto) für Node.js oder [Teams Webhook-Beispiel](https://github.com/OfficeDev/microsoft-teams-sample-outgoing-webhook/blob/23eb61da5a18634d51c5247944843da9abed01b6/WebhookSampleBot/Models/AuthProvider.cs) für \# C). Microsoft Teams verwendet standard SHA256 HMAC-Kryptografie. Sie müssen den Textkörper in UTF8 in ein Bytearray konvertieren.
* Berechnen Sie den Hash aus dem Bytearray des Sicherheitstokens, das **von Teams bereitgestellt wird,** wenn Sie den ausgehenden Webhook im Teams-Client registriert haben]. Siehe [Erstellen eines ausgehenden Webhooks.](#create-an-outgoing-webhook)
* Konvertieren Sie den Hash in eine Zeichenfolge mithilfe der UTF-8-Codierung.
* Vergleichen Sie den Zeichenfolgenwert des generierten Hash mit dem in der HTTP-Anforderung angegebenen Wert.

### <a name="3-create-a-method-to-send-a-success-or-failure-response"></a>3. Erstellen einer Methode zum Senden einer Erfolgs- oder Fehlerantwort

Antworten von ausgehenden Webhooks werden in der gleichen Antwortkette wie die ursprüngliche Nachricht angezeigt. Wenn der Benutzer eine Abfrage ausführt, gibt Microsoft Teams eine synchrone HTTP-Anforderung an Ihren Dienst aus, und Ihr Code erhält fünf Sekunden, um auf die Nachricht zu antworten, bevor die Verbindung ein Zeitüberschreitung auftritt und beendet wird.

### <a name="example-response"></a>Beispielantwort

```json
{
    "type": "message",
    "text": "This is a reply!"
}
```

> [!NOTE]
> * Sie können adaptive Karte, Hero-Karte und Textnachrichten als Anlage mit ausgehenden Webhooks senden.
> * Karten unterstützen die Formatierung. Weitere Informationen finden Sie unter [Formatieren von Karten mit Markdown.](~/task-modules-and-cards/cards/cards-format.md?tabs=adaptive-md%2Cconnector-html#formatting-cards-with-markdown)

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

# <a name="json"></a>[Json](#tab/json)

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

## <a name="create-an-outgoing-webhook"></a>Erstellen eines ausgehenden Webhooks

1. Wählen Sie das entsprechende Team aus, und wählen Sie im Dropdownmenü (&#8226;&#8226;&#8226;) die Option **"Team verwalten"** aus.
1. Wählen Sie die Registerkarte **"Apps"** in der Navigationsleiste aus.
1. Wählen Sie in der unteren rechten Ecke des Fensters **einen ausgehenden Webhook erstellen** aus.
1. Füllen Sie im resultierenden Popupfenster die erforderlichen Felder aus:

>* **Name:** Der Webhook-Titel und @mention tippen
>* **Rückruf-URL:** Der HTTPS-Endpunkt, der JSON-Nutzlasten akzeptiert und POST-Anforderungen von Teams
>* **Beschreibung:** Eine detaillierte Zeichenfolge, die auf der Profilkarte und im App-Dashboard auf Teamebene angezeigt wird
>* **Profilbild:** Ein optionales App-Symbol für Ihren Webhook
>* Wählen Sie die Schaltfläche **"Erstellen"** in der unteren rechten Ecke des Popupfensters aus, und der ausgehende Webhook wird den Kanälen des aktuellen Teams hinzugefügt.
>* Im nächsten Dialogfeld wird ein [HMAC-Sicherheitstoken (Hash-based Message Authentication Code)](https://security.stackexchange.com/questions/20129/how-and-when-do-i-use-hmac/20301) angezeigt, das zum Authentifizieren von Aufrufen zwischen Teams und dem angegebenen externen Dienst verwendet wird.
>* Der ausgehende Webhook steht den Benutzern des Teams nur zur Verfügung, wenn die URL gültig ist und die Server- und Clientauthentifizierungstoken gleich sind, z. B. ein HMAC-Handshake.

## <a name="code-sample"></a>Codebeispiel
|**Beispielname** | **Beschreibung** | **.NET** | **Node.js** |
|----------------|------------------|--------|----------------|
| Ausgehende Webhooks | Beispiele zum Erstellen **von benutzerdefinierten Bots** für die Verwendung in Microsoft Teams.| [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/outgoing-webhook/csharp) | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/outgoing-webhook/nodejs)|

