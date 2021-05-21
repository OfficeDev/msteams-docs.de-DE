---
title: Hinzufügen von benutzerdefinierten Bots Microsoft Teams mit ausgehenden Webhooks
description: beschreibt das Hinzufügen eines ausgehenden Webhooks
ms.topic: conceptual
ms.author: lajanuar
localization_priority: Normal
keywords: Teams tabs outgoing webhook actionable message verify webhook
ms.openlocfilehash: a5a0cdfc9080ac4567f438b6fb6fd0671df8c19f
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566530"
---
# <a name="add-custom-bots-to-teams-with-outgoing-webhooks"></a>Hinzufügen von benutzerdefinierten Bots zu Teams mit ausgehenden Webhooks

## <a name="outgoing-webhooks-in-teams"></a>Ausgehende Webhooks in Teams

Webhooks sind eine hervorragende Möglichkeit für Teams integration in externe Apps. Ein Webhook ist im Wesentlichen eine POST-Anforderung, die an eine Rückruf-URL gesendet wird. Ausgehende Webhooks ermöglichen Benutzern das Senden von Nachrichten an Ihren Webdienst, ohne den vollständigen Prozess des Erstellens von Bots über die [Microsoft Bot Framework.](https://dev.botframework.com/)

Ausgehender Webhook sendet Daten aus Teams an jeden ausgewählten Dienst, der eine JSON-Nutzlast akzeptieren kann. Nach dem Hinzufügen der ausgehenden Webhooks zu einem Team fungiert es als Bot und sucht mithilfe von Erwähnung nach Nachrichten in **\@ Kanälen.** Es sendet Benachrichtigungen an externe Webdienste und antwortet mit reichhaltigen Nachrichten, die Karten und Bilder enthalten.

## <a name="outgoing-webhook-key-features"></a>Wichtige Funktionen für ausgehenden Webhook

| Feature | Beschreibung |
| ------- | ----------- |
| Bereichsierte Konfiguration| Webhooks sind auf Teamebene begrenzt. Sie müssen den Einrichtungsprozess für jedes Team durchgehen, in dem Sie Ihren ausgehenden Webhook hinzufügen möchten. |
| Reaktives Messaging| Benutzer müssen @mention verwenden, damit der Webhook Nachrichten empfangen kann. Derzeit können Benutzer einen ausgehenden Webhook nur in öffentlichen Kanälen und nicht im persönlichen oder privaten Bereich senden. |
|Standardmäßiger HTTP-Nachrichtenaustausch|Antworten werden in der gleichen Kette wie die ursprüngliche Anforderungsnachricht angezeigt und können beliebige Nachrichteninhalte des Botframework enthalten, z. B. Rich Text, Bilder, Karten und Emojis. Obwohl ausgehende Webhooks Karten verwenden können, können sie keine Kartenaktionen außer `openURL` verwenden.|
| Teams Unterstützung der API-Methode|Ausgehender Webhook sendet einen HTTP POST an einen Webdienst und verarbeiten eine Antwort zurück. Sie können nicht auf andere APIs zugreifen, z. B. das Abrufen der Liste oder Liste der Kanäle in einem Team.|

## <a name="creating-actionable-messages"></a>Erstellen von Nachrichten mit Aktionen

Die Connectorkarten enthalten drei sichtbare Schaltflächen auf der Karte. Jede Schaltfläche wird in der `potentialAction` Eigenschaft der Nachricht mithilfe von Aktionen `ActionCard` definiert. Jede `ActionCard` enthält einen Eingabetyp, ein Textfeld, eine Datumsauswahl oder eine Liste mit mehreren Auswahlmöglichkeiten. Jeder `ActionCard` Aktion ist eine Aktion zugeordnet, z. B. `HttpPOST` .

Connectorkarten unterstützen drei Arten von Aktionen:

| Aktion | Beschreibung |
| ------- | ----------- |
| `ActionCard` |Stellt einen oder mehrere Eingabetypen und zugeordnete Aktionen vor.|
| `HttpPOST` | Sendet eine POST-Anforderung an eine URL. |
| `OpenUri` |  Öffnet einen URI in einem separaten Browser oder einer separaten App und richtet sich optional an unterschiedliche URIs basierend auf Betriebssystemen.|

Die `ActionCard`-Aktion unterstützt drei Eingabetypen:

| Eingabetyp | Beschreibung |
| ------- | ----------- |
| `TextInput` | Ein ein- oder mehrzeilenlanges Textfeld mit optionaler Längenbegrenzung. |
| `DateInput` | Eine Datumsauswahl mit optionaler Zeitauswahl. |
| `MultichoiceInput` | Eine angegebene Auswahlliste, die entweder eine einzelne Auswahl oder mehrere Auswahlmöglichkeiten bietet.|

`MultichoiceInput` unterstützt eine Eigenschaft, die die Anzeige einer vollständig erweiterten `style` Liste steuert. Der Standardwert von `style` hängt vom Wert `isMultiSelect` ab.

| `isMultiSelect` value  | `style` Standardwert  |
| --- | --- |
| `false` oder nicht angegeben | Die Standardformatvorlage ist `compact`|
| `true` | Die Standardformatvorlage ist `expanded` |

> [!NOTE]
> * Geben Sie sowohl als auch ein, wenn die Liste mit mehreren Auswahlen in einer `"isMultiSelect": true` `"style": true` kompakten Formatvorlage angezeigt werden soll.
> * Die Auswahl für die Eigenschaft in Teams ist identisch mit der Auswahl `compact` für die Eigenschaft in Microsoft `style` `normal` `style` Outlook.
> * Webhooks unterstützen nur Office 365 Nachrichten-Back-Karten und adaptive Karten.

Weitere Informationen zu Connectorkartenaktionen finden Sie unter **[Aktionen](/outlook/actionable-messages/card-reference#actions)** in der Referenz zur Nachrichtenkarte mit Aktionen.

## <a name="adding-outgoing-webhooks-to-your-app"></a>Hinzufügen ausgehender Webhooks zu Ihrer App

**Szenario**: Push change status notifications on a Teams channel database server to your app.  
**Beispiel:** Sie verfügen über eine Business-Of-Business-App, die alle an Mitarbeiterdatensätzen vorgenommenen CRUD-Vorgänge verfolgt, indem Teams Hr-Benutzer über einen Office 365 kanalen.

### <a name="1-create-a-url-on-your-apps-server-to-accept-and-process-a-post-request-with-a-json-payload"></a>1. Erstellen sie eine URL auf dem Server Ihrer App, um eine POST-Anforderung mit einer JSON-Nutzlast zu akzeptieren und zu verarbeiten

Ihr Dienst empfängt Nachrichten in einem standardmäßigen Azure-Botdienst-Messagingschema. Der Bot-Framework-Connector ist ein RESTful-Dienst, mit dem Ihr Dienst den Austausch von JSON-formatierten Nachrichten über HTTPS-Protokolle verarbeiten kann, wie in der [Azure Bot Service API dokumentiert.](/bot-framework/rest-api/bot-framework-rest-connector-api-reference) Alternativ können Sie dem [Microsoft Bot Framework SDK] folgen, um Nachrichten zu verarbeiten und zu analysieren. Siehe auch [Informationen zu Azure Bot Service](/azure/bot-service/bot-service-overview-introduction).


Ausgehende Webhooks sind auf die Ebene `team` begrenzt und für alle Teammitglieder sichtbar. Genau wie ein Bot müssen Benutzer **\@ den** Namen des ausgehenden Webhooks erwähnen, um ihn im Kanal aufrufen zu können.

### <a name="2-create-a-method-to-verify-the-outgoing-webhook-hmac-token"></a>2. Erstellen einer Methode zum Überprüfen des ausgehenden Webhook-HMAC-Tokens

#### <a name="hmac-signature-for-testing-with-code-example"></a>HMAC-Signatur zum Testen mit Codebeispiel

Using example of inbound message and id: "contoso" of SigningKeyDictionary of {"contoso", "vqF0En+Z0ucuRTM/01o2GuhMH3hKKk/N2bOmlM31zaA=" }.

Verwenden Sie den Wert "HMAC 03TCao0i55H1eVKUusZOTZRjtvYTs+mO41mPL+R1e1U=" in der Autorisierung des Anforderungsheaders.

Um sicherzustellen, dass Ihr Dienst nur Anrufe von tatsächlichen Teams empfängt, stellt Teams einen HMAC-Code im HTTP-Header `hmac` zur Verfügung. Der Code wurde immer in Ihr Authentifizierungsprotokoll aufgenommen.

Ihr Code muss immer die in der Anforderung enthaltene HMAC-Signatur überprüfen:

* Generieren Sie das HMAC-Token aus dem Anforderungstext der Nachricht. Es gibt Standardbibliotheken, um dies auf den meisten Plattformen zu tun (siehe [Crypto](https://nodejs.org/api/crypto.html#crypto_crypto) for Node.js oder siehe [Teams Webhook Sample](https://github.com/OfficeDev/microsoft-teams-sample-outgoing-webhook/blob/23eb61da5a18634d51c5247944843da9abed01b6/WebhookSampleBot/Models/AuthProvider.cs) for C \# ). Microsoft Teams verwendet standardmäßige SHA256 HMAC-Kryptografie. Sie müssen den Textkörper in ein Bytearray in UTF8 konvertieren.
* Berechnen Sie den Hash aus dem Bytearray des von **Teams** bereitgestellten Sicherheitstokens, wenn Sie den ausgehenden Webhook im Teams registriert haben]. Weitere [Informationen finden Sie unter Create an outgoing webhook](#create-an-outgoing-webhook).
* Konvertieren Sie den Hash mithilfe der UTF-8-Codierung in eine Zeichenfolge.
* Vergleichen Sie den Zeichenfolgenwert des generierten Hashs mit dem in der #A0 angegebenen Wert.

### <a name="3-create-a-method-to-send-a-success-or-failure-response"></a>3. Erstellen einer Methode zum Senden einer Erfolgs- oder Fehlerantwort

Antworten aus Ihren ausgehenden Webhooks werden in derselben Antwortkette wie die ursprüngliche Nachricht angezeigt. Wenn der Benutzer eine Abfrage ausführt, gibt Microsoft Teams eine synchrone HTTP-Anforderung an Ihren Dienst aus, und Ihr Code erhält fünf Sekunden, um auf die Nachricht zu antworten, bevor die Verbindung ein Zeit-Out auftritt und beendet wird.

### <a name="example-response"></a>Beispielantwort

```json
{
    "type": "message",
    "text": "This is a reply!"
}
```

## <a name="create-an-outgoing-webhook"></a>Erstellen eines ausgehenden Webhooks

1. Wählen Sie das entsprechende Team aus, und **wählen** Sie im Dropdownmenü (&#8226;&#8226;&#8226;) Team verwalten aus.
1. Wählen Sie **in** der Navigationsleiste die Registerkarte Apps aus.
1. Wählen Sie in der unteren rechten Ecke des Fensters **Ausgehenden Webhook erstellen aus.**
1. Füllen Sie im resultierenden Popupfenster die erforderlichen Felder aus:

>* **Name**: Der Webhooktitel und @mention tippen
>* **Rückruf-URL:** Der HTTPS-Endpunkt, der JSON-Nutzlasten akzeptiert und POST-Anforderungen von Teams
>* **Beschreibung**: Eine detaillierte Zeichenfolge, die auf der Profilkarte und im App-Dashboard auf Teamebene angezeigt wird
>* **Profilbild**: Ein optionales App-Symbol für Ihren Webhook
>* Wählen Sie **in** der unteren rechten Ecke des Popupfensters die Schaltfläche Erstellen aus, und der ausgehende Webhook wird den Kanälen des aktuellen Teams hinzugefügt.
>* Im nächsten Dialogfeld wird ein [Sicherheitstoken (Hash-based Message Authentication Code, HMAC)](https://security.stackexchange.com/questions/20129/how-and-when-do-i-use-hmac/20301) angezeigt, das zum Authentifizieren von Anrufen zwischen Teams und dem angegebenen außerhalb des Diensts verwendet wird.
>* Der ausgehende Webhook steht den Benutzern des Teams nur zur Verfügung, wenn die URL gültig ist und die Server- und Clientauthentifizierungstoken gleich sind, z. B. ein HMAC-Handshake.

## <a name="code-sample"></a>Codebeispiel
|**Beispielname** | **Beschreibung** | **.NET** | **Node.js** |
|----------------|------------------|--------|----------------|
| Ausgehende Webhooks | Beispiele zum Erstellen **von benutzerdefinierten Bots,** die in der Microsoft Teams.| [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/outgoing-webhook/csharp) | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/outgoing-webhook/nodejs)|

