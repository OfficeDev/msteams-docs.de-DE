---
title: Hinzufügen von benutzerdefinierten Bots zu Microsoft Teams mit ausgehenden Webhooks
description: Beschreibt das Hinzufügen eines ausgehenden Webhooks
ms.topic: conceptual
ms.author: lajanuar
localization_priority: Normal
keywords: Teams Registerkarten ausgehenwebhook sifbare Nachricht überprüfen Webhook
ms.openlocfilehash: a5a0cdfc9080ac4567f438b6fb6fd0671df8c19f
ms.sourcegitcommit: 51e4a1464ea58c254ad6bd0317aca03ebf6bf1f6
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 05/19/2021
ms.locfileid: "52566530"
---
# <a name="add-custom-bots-to-teams-with-outgoing-webhooks"></a>Hinzufügen von benutzerdefinierten Bots zu Teams mit ausgehenden Webhooks

## <a name="outgoing-webhooks-in-teams"></a>Ausgehende Webhooks in Teams

Webhooks sind eine hervorragende Möglichkeit für Teams, sich in externe Apps zu integrieren. Ein Webhook ist im Wesentlichen eine POST-Anforderung, die an eine Rückruf-URL gesendet wird. Ausgehende Webhooks ermöglichen es Benutzern, Nachrichten an Ihren Webdienst zu senden, ohne den vollständigen Prozess der Erstellung von Bots über die [Microsoft Bot Framework](https://dev.botframework.com/)zu durchlaufen.

Der ausgehende Webhook sendet Daten von Teams an einen ausgewählten Dienst, der eine JSON-Nutzlast akzeptieren kann. Nach dem Hinzufügen der ausgehenden Webhooks zu einem Team, fungiert es als Bot und sucht nach Nachrichten in Kanälen mit **\@ Erwähnung**. Es sendet Benachrichtigungen an externe Webdienste und antwortet mit umfangreichen Nachrichten, die Karten und Bilder enthalten.

## <a name="outgoing-webhook-key-features"></a>Ausgehende Webhook-Schlüsselfunktionen

| Feature | Beschreibung |
| ------- | ----------- |
| Scoped-Konfiguration| Webhooks werden auf Teamebene bereitgestellt. Sie müssen den Einrichtungsprozess für jedes Team durchlaufen, in dem Sie Ihren ausgehenden Webhook hinzufügen möchten. |
| Reaktives Messaging| Benutzer müssen @mention verwenden, damit der Webhook Nachrichten empfängt. Derzeit können Benutzer einen ausgehenden Webhook nur in öffentlichen Kanälen und nicht im persönlichen oder privaten Bereich senden. |
|Standard-HTTP-Nachrichtenaustausch|Antworten werden in derselben Kette wie die ursprüngliche Anforderungsnachricht angezeigt und können alle Bot-Framework-Nachrichteninhalte enthalten, z. B. Rich-Text, Bilder, Karten und Emojis. Obwohl ausgehende Webhooks Karten verwenden können, können sie keine Kartenaktionen außer für `openURL` verwenden.|
| Teams Unterstützung der API-Methode|Ausgehender Webhook sendet einen HTTP-POST an einen Webdienst und verarbeitet eine Antwort zurück. Sie können nicht auf andere APIs zugreifen, wie z. B. die Liste oder die Liste der Kanäle in einem Team abrufen.|

## <a name="creating-actionable-messages"></a>Erstellen von Nachrichten mit Aktionen

Die Anschlusskarten enthalten drei sichtbare Tasten auf der Karte. Jede Schaltfläche wird in der `potentialAction` Eigenschaft der Nachricht mithilfe von Aktionen `ActionCard` definiert. Jedes `ActionCard` enthält einen Eingabetyp, ein Textfeld, eine Datumsauswahl oder eine Liste mit mehreren Auswahlmöglichkeiten. Jede Aktion verfügt über `ActionCard` eine zugeordnete Aktion, z. `HttpPOST` B. .

Connectorkarten unterstützen drei Arten von Aktionen:

| Aktion | Beschreibung |
| ------- | ----------- |
| `ActionCard` |Stellt einen oder mehrere Eingabetypen und zugehörige Aktionen bereit.|
| `HttpPOST` | Sendet eine POST-Anforderung an eine URL. |
| `OpenUri` |  Öffnet einen URI in einem separaten Browser oder einer separaten App und zielt optional auf verschiedene URIs ab, die auf Betriebssystemen basieren.|

Die `ActionCard`-Aktion unterstützt drei Eingabetypen:

| Eingabetyp | Beschreibung |
| ------- | ----------- |
| `TextInput` | Ein einzeiliges oder mehrzeiliges Textfeld mit einer optionalen Längenbeschränkung. |
| `DateInput` | Ein Datumsselektor mit einem optionalen Zeitwähler. |
| `MultichoiceInput` | Eine angegebene Auswahlliste, die entweder eine einzelne Auswahl oder mehrere Auswahlen bietet.|

`MultichoiceInput` unterstützt eine `style` Eigenschaft, die die Anzeige einer vollständig erweiterten Liste steuert. Der Standardwert von `style` hängt vom `isMultiSelect` Wert ab.

| `isMultiSelect` Wert  | `style` Standardwert  |
| --- | --- |
| `false` oder nicht angegeben | Der Standardstil ist `compact`|
| `true` | Der Standardstil ist `expanded` |

> [!NOTE]
> * Geben Sie beide und ein, wenn die Liste mit `"isMultiSelect": true` `"style": true` mehrfacher Auswahl in einem kompakten Stil angezeigt werden soll.
> * Die Auswahl `compact` für die Eigenschaft in Teams entspricht der Auswahl für die Eigenschaft in Microsoft `style` `normal` `style` Outlook.
> * Webhooks unterstützen nur Office 365 Nachrichten-Back-Karten und adaptiveKarten.

Weitere Informationen zu Connectorkartenaktionen finden Sie unter **[Aktionen](/outlook/actionable-messages/card-reference#actions)** im umsetzbaren Nachrichtenkartenverweis.

## <a name="adding-outgoing-webhooks-to-your-app"></a>Hinzufügen ausgehender Webhooks zu Ihrer App

**Szenario:** Push-Änderungsstatusbenachrichtigungen auf einem Teams-Kanal-Datenbankserver zu Ihrer App.  
**Beispiel:** Sie haben eine Line-of-Business-App, die alle CRUD-Vorgänge nachverfolgt, die von Teams Channel-HR-Benutzern über eine Office 365-Mandanten in Mitarbeiterdatensätzen vorgenommen wurden.

### <a name="1-create-a-url-on-your-apps-server-to-accept-and-process-a-post-request-with-a-json-payload"></a>1. Erstellen Sie eine URL auf dem Server Ihrer App, um eine POST-Anforderung mit einer JSON-Nutzlast zu akzeptieren und zu verarbeiten

Ihr Dienst empfängt Nachrichten in einem standardmäßigen Azure-Botdienst-Messagingschema. Der Botframeworkconnector ist ein RESTful-Dienst, der Ihren Dienst in die Lage versetzt, den Austausch von JSON-formatierten Nachrichten über HTTPS-Protokolle zu verarbeiten, wie in der [Azure Bot Service-API](/bot-framework/rest-api/bot-framework-rest-connector-api-reference)dokumentiert. Alternativ können Sie dem [Microsoft Bot Framework SDK] folgen, um Nachrichten zu verarbeiten und zu analysieren. Siehe auch [Über Azure Bot Service](/azure/bot-service/bot-service-overview-introduction).


Ausgehende Webhooks sind auf die Ebene beschränkt `team` und für alle Teammitglieder sichtbar. Genau wie ein Bot müssen Benutzer den Namen des ausgehenden Webhooks **\@ erwähnen,** um ihn im Kanal aufzurufen.

### <a name="2-create-a-method-to-verify-the-outgoing-webhook-hmac-token"></a>2. Erstellen Sie eine Methode, um das ausgehende Webhook-HMAC-Token zu überprüfen

#### <a name="hmac-signature-for-testing-with-code-example"></a>HMAC-Signatur zum Testen mit Codebeispiel

Anhand des Beispiels für eingehende Nachricht und ID: "contoso" von SigningKeyDictionary von "contoso", "vqF0En+Z0ucuRTM/01o2GuhMH3hKKk/N2bOmlM31zaA=" .

Verwenden Sie den Wert "HMAC 03TCao0i55H1eVKUusZOTZRjtvYTs+mO41mPL+R1e1U=" in der Autorisierung des Anforderungsheaders.

Um sicherzustellen, dass Ihr Dienst Nur Anrufe von tatsächlichen Teams-Clients empfängt, stellt Teams einen HMAC-Code im `hmac` HTTP-Header bereit. Der Code wurde immer in Ihr Authentifizierungsprotokoll aufgenommen.

Ihr Code muss immer die in der Anforderung enthaltene HMAC-Signatur überprüfen:

* Generieren Sie das HMAC-Token aus dem Anforderungstext der Nachricht. Es gibt Standardbibliotheken, um dies auf den meisten Plattformen zu tun (siehe [Crypto](https://nodejs.org/api/crypto.html#crypto_crypto) für Node.js oder siehe [Teams Webhook-Beispiel](https://github.com/OfficeDev/microsoft-teams-sample-outgoing-webhook/blob/23eb61da5a18634d51c5247944843da9abed01b6/WebhookSampleBot/Models/AuthProvider.cs) für C \# ). Microsoft Teams verwendet die standardmäßige SHA256 HMAC-Kryptographie. Sie müssen den Körper in ein Byte-Array in UTF8 konvertieren.
* Berechnen Sie den Hash aus dem Bytearray des Sicherheitstokens, das **von Teams bereitgestellt wird,** als Sie den ausgehenden Webhook im Teams Client] registriert haben. Weitere Informationen finden Sie unter [Erstellen eines ausgehenden Webhooks](#create-an-outgoing-webhook).
* Konvertieren Sie den Hash mithilfe der UTF-8-Codierung in eine Zeichenfolge.
* Vergleichen Sie den Zeichenfolgenwert des generierten Hashs mit dem in der HTTP-Anforderung bereitgestellten Wert.

### <a name="3-create-a-method-to-send-a-success-or-failure-response"></a>3. Erstellen einer Methode zum Senden einer Erfolgs- oder Fehlerantwort

Antworten von Ihren ausgehenden Webhooks werden in derselben Antwortkette wie die ursprüngliche Nachricht angezeigt. Wenn der Benutzer eine Abfrage ausführt, gibt Microsoft Teams eine synchrone HTTP-Anforderung an Ihren Dienst aus, und Der Code erhält fünf Sekunden, um auf die Nachricht zu antworten, bevor die Verbindung beendet und beendet wird.

### <a name="example-response"></a>Beispielantwort

```json
{
    "type": "message",
    "text": "This is a reply!"
}
```

## <a name="create-an-outgoing-webhook"></a>Erstellen eines ausgehenden Webhooks

1. Wählen Sie das entsprechende Team aus, und wählen Sie team **verwalten** aus dem Dropdown-Menü (&#8226;&#8226;&#8226;) aus.
1. Wählen Sie die Registerkarte **Apps** in der Navigationsleiste aus.
1. Wählen Sie in der unteren rechten Ecke des Fensters **einen ausgehenden Webhook** erstellen aus.
1. Füllen Sie im resultierenden Popup-Fenster die erforderlichen Felder aus:

>* **Name**: Der Webhook-Titel und @mention tippen
>* **Rückruf-URL**: Der HTTPS-Endpunkt, der JSON-Nutzlasten akzeptiert und POST-Anforderungen von Teams
>* **Beschreibung**: Eine detaillierte Zeichenfolge, die in der Profilkarte und im App-Dashboard auf Teamebene angezeigt wird
>* **Profilbild**: Ein optionales App-Symbol für Ihren Webhook
>* Wählen Sie die Schaltfläche **Erstellen** in der unteren rechten Ecke des Popupfensters aus, und der ausgehende Webhook wird den Kanälen des aktuellen Teams hinzugefügt.
>* Im nächsten Dialogfeld wird ein [HMAC-Sicherheitstoken (Hash-based Message Authentication Code)](https://security.stackexchange.com/questions/20129/how-and-when-do-i-use-hmac/20301) angezeigt, das zum Authentifizieren von Anrufen zwischen Teams und dem angegebenen externen Dienst verwendet wird.
>* Der ausgehende Webhook steht den Benutzern des Teams nur zur Verfügung, wenn die URL gültig ist und die Server- und Clientauthentifizierungstoken gleich sind, z. B. ein HMAC-Handshake.

## <a name="code-sample"></a>Codebeispiel
|**Beispielname** | **Beschreibung** | **.NET** | **Node.js** |
|----------------|------------------|--------|----------------|
| Ausgehende Webhooks | Beispiele zum Erstellen **von benutzerdefinierten Bots,** die in Microsoft Teams verwendet werden sollen.| [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/outgoing-webhook/csharp) | [View](https://github.com/OfficeDev/Microsoft-Teams-Samples/tree/main/samples/outgoing-webhook/nodejs)|

