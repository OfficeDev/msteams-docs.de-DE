---
title: Hinzufügen von benutzerdefinierten Bots zu Microsoft Teams mit ausgehenden Webhooks
description: beschreibt, wie ein ausgehender Webhook hinzugefügt wird
ms.topic: conceptual
ms.author: lajanuar
keywords: Teams tabs outgoing webhook actionable message verify webhook
ms.openlocfilehash: 20d30be7a35b33b94dc4a856439c51d5d0cc441c
ms.sourcegitcommit: f74b74d5bed1df193e59f46121ada443fb57277b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2021
ms.locfileid: "50093253"
---
# <a name="add-custom-bots-to-teams-with-outgoing-webhooks"></a>Hinzufügen von benutzerdefinierten Bots zu Teams mit ausgehenden Webhooks

## <a name="what-are-outgoing-webhooks-in-teams"></a>Was sind ausgehende Webhooks in Teams?

Webhooks sind eine hervorragende Möglichkeit für Teams, sich in externe Apps zu integrieren. Ein Webhook ist im Wesentlichen eine POST-Anforderung, die an eine Rückruf-URL gesendet wird. Ausgehende Webhooks ermöglichen Benutzern das Senden von Nachrichten an Ihren Webdienst, ohne den vollständigen Prozess der Erstellung von Bots über [das Microsoft Bot Framework zu durchgehen.](https://dev.botframework.com/)

Ausgehender Webhook sendet Daten von Teams an jeden ausgewählten Dienst, der eine JSON-Nutzlast akzeptieren kann. Nachdem sie die ausgehenden Webhooks zu einem Team hinzugefügt haben, fungiert sie als Bot und sucht mithilfe von Erwähnungen nach Nachrichten in **\@ Kanälen.** Es sendet Benachrichtigungen an externe Webdienste und antwortet mit reichhaltigen Nachrichten, die Karten und Bilder enthalten.

## <a name="outgoing-webhook-key-features"></a>Wichtige Features für ausgehenden Webhook

| Feature | Beschreibung |
| ------- | ----------- |
| Bereichskonfiguration| Webhooks sind auf Teamebene begrenzt. Sie müssen den Einrichtungsprozess für jedes Team durchgehen, in dem Sie Ihren ausgehenden Webhook hinzufügen möchten. |
| Reaktives Messaging| Benutzer müssen die @mention verwenden, damit der Webhook Nachrichten empfangen kann. Derzeit können Benutzer nur einen ausgehenden Webhook in öffentlichen Kanälen und nicht im persönlichen oder privaten Bereich senden. |
|Standard-HTTP-Nachrichtenaustausch|Antworten werden in derselben Kette wie die ursprüngliche Anforderungsnachricht angezeigt und können beliebige Nachrichteninhalte des Botframework enthalten, z. B. Rich-Text, Bilder, Karten und Emojis. Obwohl ausgehende Webhooks Karten verwenden können, können sie keine Kartenaktionen außer `openURL` .|
| Unterstützung von Teams-API-Methoden|Ausgehender Webhook sendet einen HTTP POST an einen Webdienst und verarbeiten eine Antwort zurück. Sie können nicht auf andere APIs zugreifen, z. B. den Listenplan oder die Liste der Kanäle in einem Team abrufen.|

## <a name="creating-actionable-messages"></a>Erstellen von Nachrichten mit Aktionen

Die Connectorkarten enthalten drei sichtbare Schaltflächen auf der Karte. Jede Schaltfläche wird mithilfe von Aktionen in `potentialAction` der Eigenschaft der Nachricht `ActionCard` definiert. Jede `ActionCard` enthält einen Eingabetyp, ein Textfeld, eine Datumsauswahl oder eine Liste mit mehreren Auswahlmöglichkeiten. Jeder `ActionCard` Aktion ist eine Aktion zugeordnet, z. B. `HttpPOST` .

Connectorkarten unterstützen drei Arten von Aktionen:

| Aktion | Beschreibung |
| ------- | ----------- |
| `ActionCard` |Stellt einen oder mehrere Eingabetypen und zugeordnete Aktionen vor.|
| `HttpPOST` | Sendet eine POST-Anforderung an eine URL. |
| `OpenUri` |  Öffnet einen URI in einem separaten Browser oder einer separaten App und richtet sich optional an unterschiedliche URIs basierend auf Betriebssystemen.|

Die `ActionCard`-Aktion unterstützt drei Eingabetypen:

| Eingabetyp | Beschreibung |
| ------- | ----------- |
| `TextInput` | Ein ein- oder mehrfarbiges Textfeld mit optionaler Längenbeschränkung. |
| `DateInput` | Ein Datumsauswahl mit einer optionalen Zeitauswahl. |
| `MultichoiceInput` | Eine angegebene Liste von Auswahlmöglichkeiten, die entweder eine einzelne Auswahl oder mehrere Auswahlmöglichkeiten bietet.|

`MultichoiceInput` unterstützt eine `style` Eigenschaft, die die Anzeige einer vollständig erweiterten Liste steuert. Der Standardwert hängt `style` vom Wert `isMultiSelect` ab.

| `isMultiSelect` value  | `style` Standardwert  |
| --- | --- |
| `false` oder nicht angegeben | Der Standardstil ist `compact`|
| `true` | Der Standardstil ist `expanded` |

> [!NOTE]
> * Geben Sie sowohl als auch ein, wenn die Mehrfachauswahlliste im kompakten `"isMultiSelect": true` `"style": true` Format angezeigt werden soll.
> * Die Auswahl der Eigenschaft in Teams ist identisch mit der `compact` Auswahl der Eigenschaft in Microsoft `style` `normal` `style` Outlook.
> * Webhooks unterstützen nur Office 365-Rücksendekarten für Nachrichten und adaptive Karten.

Weitere Informationen zu Connectorkartenaktionen finden Sie unter **["Aktionen"](/outlook/actionable-messages/card-reference#actions)** in der Referenz zur Nachrichtenkarte mit Aktionen.

## <a name="adding-outgoing-webhooks-to-your-app"></a>Hinzufügen ausgehender Webhooks zu Ihrer App

**Szenario:** Pushen von Änderungsstatusbenachrichtigungen auf einem Teams-Kanal-Datenbankserver an Ihre App.  
**Beispiel:** Sie verfügen über eine Line-of-Business-App, die alle CRUD-Vorgänge verfolgt, die von Benutzern des Teams-Kanals für Personalwesen über einen Office 365-Mandanz hinweg an Mitarbeiterdatensätzen vorgenommen wurden.

### <a name="1-create-a-url-on-your-apps-server-to-accept-and-process-a-post-request-with-a-json-payload"></a>1. Erstellen Sie eine URL auf dem Server Ihrer App, um eine POST-Anforderung mit einer JSON-Nutzlast zu akzeptieren und zu verarbeiten.

Ihr Dienst empfängt Nachrichten in einem standardmäßigen Azure Bot Service Messaging-Schema. Der Bot-Framework-Connector ist ein RESTful-Dienst, mit dem Ihr Dienst den Austausch von JSON-formatierten Nachrichten über HTTPS-Protokolle verarbeiten kann, wie in der [Azure Bot Service-API dokumentiert.](/bot-framework/rest-api/bot-framework-rest-connector-api-reference) Alternativ können Sie dem [Microsoft Bot Framework SDK] folgen, um Nachrichten zu verarbeiten und zu analysieren. Siehe auch [Informationen zum Azure Bot Service](/azure/bot-service/bot-service-overview-introduction).


Ausgehende Webhooks sind auf die Ebene `team` begrenzt und für alle Teammitglieder sichtbar. Genau wie ein Bot **\@** müssen Benutzer den Namen des ausgehenden Webhooks erwähnen, um ihn im Kanal aufriefen zu können.

### <a name="2-create-a-method-to-verify-the-outgoing-webhook-hmac-token"></a>2. Erstellen einer Methode zum Überprüfen des ausgehenden Webhook-HMAC-Tokens

#### <a name="hmac-signature-for-testing-with-code-example"></a>HMAC-Signatur für Tests mit Codebeispiel

Using example of inbound message and id: "contoso" of SigningKeyDictionary of {"contoso", "vqF0En+Z0ucuRTM/01o2GuhMH3hKKk/N2bOmlM31zaA=" }.

Verwenden Sie den Wert "HMAC 03TCao0i55H1eVKUusZOTZRjtvYTs+mO41mPL+R1e1U=" in der Autorisierung des Anforderungsheaders.

Um sicherzustellen, dass Ihr Dienst nur Anrufe von tatsächlichen Teams-Clients empfängt, stellt Teams einen HMAC-Code im HTTP-Header `hmac` zur Verfügung. Der Code wurde immer in Ihr Authentifizierungsprotokoll aufgenommen.

Ihr Code muss immer die in der Anforderung enthaltene HMAC-Signatur überprüfen:

* Generieren Sie das HMAC-Token aus dem Anforderungstext der Nachricht. Es gibt Standardbibliotheken, um dies auf den meisten Plattformen zu tun (siehe [Crypto](https://nodejs.org/api/crypto.html#crypto_crypto) for Node.js oder [teams Webhook Sample](https://github.com/OfficeDev/microsoft-teams-sample-outgoing-webhook/blob/23eb61da5a18634d51c5247944843da9abed01b6/WebhookSampleBot/Models/AuthProvider.cs) for C \# ). Microsoft Teams verwendet standardmäßige SHA256 HMAC-Kryptografie. Sie müssen den Textkörper in ein Bytearray in UTF8 konvertieren.
* Berechnen Sie den Hash aus dem Bytearray des Sicherheitstokens, das **von Teams** bereitgestellt wird, wenn Sie den ausgehenden Webhook im #A0 registriert haben. Siehe [Erstellen eines ausgehenden Webhooks.](#create-an-outgoing-webhook)
* Konvertieren Sie den Hash mithilfe der UTF-8-Codierung in eine Zeichenfolge.
* Vergleichen Sie den Zeichenfolgenwert des generierten Hashwerts mit dem in der #A0 angegebenen Wert.

### <a name="3-create-a-method-to-send-a-success-or-failure-response"></a>3. Erstellen einer Methode zum Senden einer Erfolgs- oder Fehlerantwort

Antworten von Ihren ausgehenden Webhooks werden in derselben Antwortkette wie die ursprüngliche Nachricht angezeigt. Wenn der Benutzer eine Abfrage ausführt, stellt Microsoft Teams eine synchrone HTTP-Anforderung an Ihren Dienst aus, und Ihr Code erhält fünf Sekunden, um auf die Nachricht zu antworten, bevor die Verbindung abschneidet und beendet wird.

### <a name="example-response"></a>Beispielantwort

```json
{
    "type": "message",
    "text": "This is a reply!"
}
```

## <a name="create-an-outgoing-webhook"></a>Erstellen eines ausgehenden Webhooks

1. Wählen Sie das entsprechende Team **aus,** und wählen Sie im Dropdownmenü (&#8226;&#8226;&#8226;) "Team verwalten" aus.
1. Wählen Sie **in der Navigationsleiste** die Registerkarte "Apps" aus.
1. Wählen Sie in der unteren rechten Ecke des Fensters **"Ausgehenden Webhook erstellen" aus.**
1. Füllen Sie im resultierenden Popupfenster die erforderlichen Felder aus:

>* **Name** – Der Webhooktitel und @mention tippen.
>* **Rückruf-URL:** Der HTTPS-Endpunkt, der die JSON-Nutzlasten akzeptiert und die POST-Anforderungen von Teams empfängt.
>* **Beschreibung** – Eine detaillierte Zeichenfolge, die auf der Profilkarte und im Dashboard der App auf Teamebene angezeigt wird.
>* **Profilbild** ein optionales App-Symbol für Ihren Webhook.
>* Wählen Sie **die Schaltfläche** "Erstellen" in der unteren rechten Ecke des Popupfensters aus, und der ausgehende Webhook wird den Kanälen des aktuellen Teams hinzugefügt.
>* Im nächsten Dialogfeld wird ein [#A0 (Hash-based Message Authentication Code)](https://security.stackexchange.com/questions/20129/how-and-when-do-i-use-hmac/20301) angezeigt, das zum Authentifizieren von Aufrufen zwischen Teams und dem angegebenen außendienst verwendet wird.
>* Der ausgehende Webhook ist für die Benutzer des Teams nur verfügbar, wenn die URL gültig ist und die Server- und Clientauthentifizierungstoken gleich sind, z. B. ein HMAC-Handshake.

## <a name="code-samples"></a>Codebeispiele

Sie können die Codebeispiele für ausgehenden Webhook auf GitHub anzeigen:

### <a name="nodejs"></a>Node.js

[OfficeDev/msteams-samples-outgoing-webhook-nodejs](https://github.com/OfficeDev/msteams-samples-outgoing-webhook-nodejs)

### <a name="c"></a>C\#

[OfficeDev/microsoft-teams-sample-outgoing-webhook](https://github.com/OfficeDev/microsoft-teams-sample-outgoing-webhook)
