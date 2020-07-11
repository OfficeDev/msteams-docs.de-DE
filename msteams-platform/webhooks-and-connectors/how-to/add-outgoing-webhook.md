---
title: Hinzufügen von benutzerdefinierten Bots zu Microsoft Teams mit ausgehenden webhooks
author: laujan
description: ''
keywords: Teams-Registerkarten für ausgehende webhooks *
ms.topic: conceptual
ms.author: laujan
ms.openlocfilehash: 4881dc8768c7c51947f6a80a55affe78c28874d3
ms.sourcegitcommit: 3ba5a5a7d9d9d906abc3ee1df9c2177de0cfd767
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 07/11/2020
ms.locfileid: "45102998"
---
# <a name="add-custom-bots-to-microsoft-teams-with-outgoing-webhooks"></a>Hinzufügen von benutzerdefinierten Bots zu Microsoft Teams mit ausgehenden webhooks

## <a name="what-are-outgoing-webhooks-in-teams"></a>Was sind ausgehende webhooks in Microsoft Teams?

Webhooks sind eine hervorragende Möglichkeit für Microsoft Teams, in externe apps zu integrieren. Ein webhook ist im Wesentlichen eine Post-Anforderung, die an eine Rückruf-URL gesendet wird. In Teams bieten ausgehende webhooks eine einfache Möglichkeit, Benutzern das Senden von Nachrichten an Ihren Webdienst zu ermöglichen, ohne den vollständigen Prozess der Erstellung von Bots über das [Microsoft bot-Framework](https://dev.botframework.com/)durchlaufen zu müssen. Ausgehende webhooks senden Daten aus Teams an einen beliebigen Dienst, der eine JSON-Nutzlast akzeptieren kann. Sobald ein ausgehender webhook einem Team hinzugefügt wurde, fungiert er als bot, lauscht in Kanälen für Nachrichten unter Verwendung von ** \@ Erwähnung**, sendet Benachrichtigungen an externe Webdienste und antwortet mit Rich-Nachrichten, die Karten und Bilder enthalten können.

## <a name="outgoing-webhook-key-features"></a>Wichtige Features für ausgehende webhooks

| Feature | Beschreibung |
| ------- | ----------- |
| Bereichsbezogene Konfiguration| Webhooks sind auf Teamebene auf Bereichsebene ausgelegt. Sie müssen den Einrichtungsprozess für jedes Team durchlaufen, dem Sie Ihren ausgehenden Webhook hinzufügen möchten. |
| Reaktive Nachrichten| Benutzer müssen @mention für den webhook verwenden, um Nachrichten zu empfangen. Derzeit können Benutzer nur einen ausgehenden webhook in öffentlichen Kanälen und nicht innerhalb des persönlichen oder privaten Bereichs Nachrichten. |
|Standard-HTTP-Nachrichtenaustausch|Antworten werden in der gleichen Kette wie die ursprüngliche Anforderungsnachricht angezeigt und können alle bot-Framework-Nachrichteninhalte (Rich-Text, Bilder, Karten und Emojis) enthalten. **Hinweis**: Obwohl ausgehende webhooks Karten verwenden können, können Sie keine Karten Aktionen außer verwenden `openURL` .|
| Unterstützung der Teams-API-Methode|In Microsoft Teams senden ausgehende webhooks einen HTTP-Beitrag an einen Webdienst und verarbeiten eine Antwort zurück. Sie können nicht auf andere APIs zugreifen, wie das Dienstprogramm oder die Liste der Kanäle in einem Team abrufen.|

## <a name="adding-outgoing-webhook-processing-to-your-app"></a>Hinzufügen der ausgehenden webhook-Verarbeitung zu Ihrer APP

**Szenario**: Push Change Status Notifications on a Teams Channel Database Server to Your App.  
**Beispiel**: Sie verfügen über eine Branchen-APP, die alle CRUD-Vorgänge aufspürt, die von Microsoft Teams Kanal HR-Benutzer in einer Office 365 Mandantschaft an Mitarbeiterdatensätzen vorgenommen wurden.

### <a name="1-create-a-url-on-your-apps-server-to-accept-and-process-a-post-request-with-a-json-payload"></a>1. Erstellen Sie eine URL auf dem Server Ihrer APP, um eine Post-Anforderung mit einer JSON-Nutzlast zu akzeptieren und zu verarbeiten.

Ihr Dienst erhält Nachrichten im standardmäßigen Azure bot-Dienst-Messagingschema. Der bot-Framework-Connector ist ein Rest-Dienst, mit dem Ihr Dienst den Austausch von JSON-formatierten Nachrichten über HTTPS-Protokolle verarbeiten kann, wie in der [Azure bot Service-API](/bot-framework/rest-api/bot-framework-rest-connector-api-reference)dokumentiert. Alternativ können Sie das [Microsoft bot Framework SDK] zum Verarbeiten und Analysieren von Nachrichten befolgter. *Siehe auch*  [über Azure bot-Dienst](/azure/bot-service/bot-service-overview-introduction?view=azure-bot-service-4.0).

Ausgehende webhooks sind auf die `team` Ebene beschränkt und für alle Mitglieder des Teams sichtbar. Genau wie ein bot müssen Benutzer den Namen des ausgehenden webhooks ** \@ erwähnen** , um ihn im Kanal aufzurufen.

### <a name="2-create-a-method-to-verify-the-outgoing-webhook-hmac-token"></a>2. Erstellen einer Methode zum Überprüfen des ausgehenden webhook-HMAC-Tokens

Um sicherzustellen, dass Ihr Dienst nur Anrufe von tatsächlichen Teams-Clients empfängt, stellt Microsoft Teams einen HMAC-Code im HTTP- `hmac` Header bereit, der immer in Ihrem Authentifizierungsprotokoll enthalten sein sollte.

Ihr Code sollte immer die HMAC-Signatur validieren, die in der Anforderung enthalten ist:

* *Generieren* Sie das HMAC-Token aus dem Anforderungstext der Nachricht. Auf den meisten Plattformen gibt es Standardbibliotheken (*Siehe* [Crypto](https://nodejs.org/api/crypto.html#crypto_crypto) for Node.js oder *See* [Teams webhook Sample](https://github.com/OfficeDev/microsoft-teams-sample-outgoing-webhook/blob/23eb61da5a18634d51c5247944843da9abed01b6/WebhookSampleBot/Models/AuthProvider.cs) for C \# ). Microsoft Teams verwendet die standardmäßige SHA256-HMAC-Kryptografie. Sie müssen den Textkörper in ein Byte-Array in UTF8 umwandeln.
* *Berechnen* Sie den Hash aus dem Bytearray des Sicherheitstokens **, das von Microsoft Teams bereitgestellt wurde** , als Sie den ausgehenden webhook im Microsoft Teams-Client registriert haben.] *Weitere Informationen finden Sie* unter [Erstellen eines ausgehenden webhooks](#create-an-outgoing-webhook).
* *Konvertieren* Sie den Hash mithilfe der UTF-8-Codierung in eine Zeichenfolge.
* *Vergleichen* Sie den Zeichenfolgenwert des generierten Hash mit dem in der HTTP-Anforderung angegebenen Wert.

### <a name="3-create-a-method-to-send-a-success-or-failure-response"></a>3. Erstellen einer Methode zum Senden einer Erfolgs-oder Fehlerantwort

Antworten von Ihrem ausgehenden webhook werden in derselben Antwort Kette angezeigt wie die ursprüngliche Nachricht. Wenn der Benutzer eine Abfrage ausführt, gibt Microsoft Teams eine synchrone http-Anforderung an Ihren Dienst aus, und Ihr Code hat 5 Sekunden, um auf die Nachricht zu antworten, bevor die Verbindung Timeout und beendet wird.

### <a name="example-response"></a>Beispielantwort

```json
{
    "type": "message",
    "text": "This is a reply!"
}
```

## <a name="create-an-outgoing-webhook"></a>Erstellen eines ausgehenden Webhooks

1. Wählen Sie das entsprechende Team aus, und wählen Sie im Dropdownmenü (&#8226;&#8226;&#8226;) die Option **Team verwalten** aus.
1. Klicken Sie in der Navigationsleiste auf die Registerkarte **apps** .
1. Wählen Sie in der unteren rechten Ecke des Fensters **einen ausgehenden webhook erstellen**aus.
1. Füllen Sie im daraufhin angezeigten Popupfenster die erforderlichen Felder aus:

>* **Name** – der webhook-Titel und @mention Tippen Sie auf.
>* **Rückruf-URL** : der HTTPS-Endpunkt, der JSON-Nutzlast akzeptiert und Post-Anforderungen von Microsoft Teams empfängt.
>* **Description** – eine ausführliche Zeichenfolge, die in der Profilkarte und im App-Dashboard auf Team Ebene angezeigt wird.
>* **Profilbild** (optional) ein App-Symbol für Ihren webhook.
>* Wählen Sie die Schaltfläche **Erstellen** in der unteren rechten Ecke des Popupfensters aus, und der ausgehende webhook wird den Kanälen des aktuellen Teams hinzugefügt.
>* Im nächsten Dialogfenster wird ein [HMAC (Hash-based Message Authentication Code)-](https://security.stackexchange.com/questions/20129/how-and-when-do-i-use-hmac/20301) Sicherheitstoken angezeigt, das zum Authentifizieren von anrufen zwischen Teams und dem festgelegten externen Dienst verwendet wird.
>* Wenn die URL gültig ist und die Server-und Client Authentifizierungstoken gleich sind (also ein HMAC-Hand Shake), steht der ausgehende webhook den Benutzern des Teams zur Verfügung.

## <a name="code-samples"></a>Codebeispiele

Sie können ausgehende webhook-Codebeispiele auf GitHub anzeigen:

### <a name="nodejs"></a>Node.js

[OfficeDev/msteams-Samples-Outgoing-webhook-nodejs](https://github.com/OfficeDev/msteams-samples-outgoing-webhook-nodejs)

### <a name="c"></a>C\#

[OfficeDev/Microsoft-Teams-Sample-Outgoing-webhook](https://github.com/OfficeDev/microsoft-teams-sample-outgoing-webhook)
