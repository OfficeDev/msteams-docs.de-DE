---
title: Hinzufügen der Authentifizierung zu Ihrer Nachrichtenerweiterung
author: surbhigupta
description: Erfahren Sie, wie Sie einer Messaging-Erweiterung mithilfe von Codebeispielen eine Authentifizierung hinzufügen, und sehen Sie ein Beispiel.
ms.localizationpriority: high
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: 36a2aa269bfc43f4c07e97a5c214e3081a38ffeb
ms.sourcegitcommit: 591bab4c7e01ac9099b9a540f149b64e6e31e6e8
ms.translationtype: HT
ms.contentlocale: de-DE
ms.lasthandoff: 04/29/2022
ms.locfileid: "65135710"
---
# <a name="add-authentication-to-your-message-extension"></a>Hinzufügen der Authentifizierung zu Ihrer Nachrichtenerweiterung

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

## <a name="identify-the-user"></a>Identifizieren des Benutzers

Jede Anforderung an Ihre Dienste enthält die Benutzer-ID, den Anzeigenamen des Benutzers und die Azure Active Directory-Objekt-ID.

```json
"from": {
  "id": "29:1C7dbRrC_5yzN1RGtZIrcWT0xz88KPGP9sxdpVpV8sODlgPHeQE9RqQ02hnpuKzy6zZ-AaZx6swUOMj_Dsdse3TQ4sIaeebbFBF-VgjJy_nY",
  "name": "Larry Jin",
  "aadObjectId": "cd723fa0-0591-416a-9290-e93ecf3a9b92"
},
```

Die Werte `id` und `aadObjectId` werden für den authentifizierten Teams-Benutzer garantiert. Sie werden als Schlüssel verwendet, um die Anmeldeinformationen oder einen zwischengespeicherten Status in Ihrem Dienst nachzuschlagen. Zusätzlich enthält jede Anforderung die Azure Active Directory-Mandanten-ID, die verwendet wird, um die Organisation des Benutzers zu identifizieren. Falls zutreffend, enthält die Anforderung auch die Team-ID und die Kanal-ID, von der die Anforderung stammt.

## <a name="authentication"></a>Authentifizierung

Wenn Ihr Dienst eine Benutzerauthentifizierung erfordert, müssen sich die Benutzer anmelden, bevor sie die Nachrichtenerweiterung verwenden. Die Authentifizierungsschritte ähneln denen eines Bots oder einer Registerkarte. Die Sequenz sieht wie folgt aus:

1. Der Benutzer stellt eine Abfrage, oder die Standardabfrage wird automatisch an Ihren Dienst gesendet.
1. Ihr Dienst überprüft, ob der Benutzer authentifiziert ist, indem er die Teams-Benutzer-ID untersucht.
1. Wenn der Benutzer nicht authentifiziert ist, senden Sie eine `auth`-Antwort mit einer vorgeschlagenen `openUrl`- Aktion zurück, einschließlich der Authentifizierungs-URL.
1. Der Microsoft Teams-Client startet ein Dialogfeld, in dem Ihre Webseite mithilfe der angegebenen Authentifizierungs-URL gehostet wird.
1. Nachdem sich der Benutzer angemeldet hat, sollten Sie Ihr Fenster schließen und einen **Authentifizierungscode** an den Teams-Client senden.
1. Der Teams-Client stellt dann die Abfrage an Ihren Dienst erneut, einschließlich des in Schritt 5 übergebenen Authentifizierungscodes.

Ihr Dienst sollte überprüfen, ob der in Schritt 6 empfangene Authentifizierungscode mit dem aus Schritt 5 übereinstimmt. Dadurch wird sichergestellt, dass ein bösartiger Benutzer nicht versucht, den Anmeldefluss zu spoofen oder zu kompromittieren. Dies wird effektiv „die Schleife schließen“, um die sichere Authentifizierungssequenz abzuschließen.

### <a name="respond-with-a-sign-in-action"></a>Antworten mit einer Anmeldeaktion

Um einen nicht authentifizierten Benutzer zur Anmeldung aufzufordern, antworten Sie mit einer vorgeschlagenen Aktion vom Typ `openUrl`, welche die Authentifizierungs-URL enthält.

#### <a name="response-example-for-a-sign-in-action"></a>Antwortbeispiel für eine Anmeldeaktion

```json
{
  "composeExtension":{
    "type":"auth",
    "suggestedActions":{
      "actions":[
        {
          "type": "openUrl",
          "value": "https://example.com/auth",
          "title": "Sign in to this app"
        }
      ]
    }
  }
}
```

> [!NOTE]
>
> * Damit die Anmeldeerfahrung in einem Teams-Popupfenster gehostet werden kann, muss sich der Domänenteil der URL in der Liste der gültigen Domänen Ihrer App befinden. Weitere Informationen finden Sie unter [validDomains](~/resources/schema/manifest-schema.md#validdomains) im Manifestschema.
> * Die Größe des Authentifizierungs-Popupfensters kann durch Einschließen von Abfragezeichenfolgenparametern der Breite und Höhe `Value = $"{_siteUrl}/searchSettings.html?height=600&width=600"` definiert werden.

### <a name="start-the-sign-in-flow"></a>Starten des Anmeldeflusses

Ihre Anmeldeerfahrung muss reaktionsfähig sein und in ein Popupfenster passen. Sie sollte in das [Microsoft Teams JavaScript-Client SDK](/javascript/api/overview/msteams-client) integriert werden, das die Nachrichtenübergabe verwendet.

Wie bei anderen eingebetteten Erfahrungen, die innerhalb von Microsoft Teams ausgeführt werden, muss Ihr Code im Fenster zuerst `microsoftTeams.initialize()` aufrufen. Wenn Ihr Code einen OAuth-Fluss ausführt, können Sie die Teams-Benutzer-ID an Ihr Fenster übergeben, das sie dann an die OAuth-Anmelde-URL übergibt.

### <a name="complete-the-sign-in-flow"></a>Abschließen des Anmeldeflusses

Wenn die Anmeldeanforderung abgeschlossen ist und zurück zu Ihrer Seite leitet, müssen die folgenden Schritte ausgeführt werden:

1. Generieren Sie einen Sicherheitscode, eine Zufallszahl. Sie müssen diesen Code in Ihrem Dienst zwischenspeichern, zusammen mit den Anmeldeinformationen, die über den Anmeldefluss erhalten wurden, z. B. OAuth 2.0-Token.
1. Rufen Sie `microsoftTeams.authentication.notifySuccess` auf, und übergeben Sie den Sicherheitscode.

An diesem Punkt wird das Fenster geschlossen, und die Kontrolle wird an den Teams-Client übergeben. Der Client stellt nun die ursprüngliche Benutzerabfrage zusammen mit dem Sicherheitscode in der Eigenschaft `state` erneut aus. Ihr Code kann den Sicherheitscode verwenden, um die zuvor gespeicherten Anmeldeinformationen nachzuschlagen, um die Authentifizierungssequenz abzuschließen und dann die Benutzeranforderung abzuschließen.

#### <a name="reissued-request-example"></a>Beispiel für neu ausgestellte Anforderung

```json
{
    "name": "composeExtension/query",
    "value": {
        "commandId": "insertWiki",
        "parameters": [{
            "name": "searchKeyword",
            "value": "lakers"
        }],
        "state": "12345",
        "queryOptions": {
            "skip": 0,
            "count": 25
        }
    },
    "type": "invoke",
    "timestamp": "2017-04-26T05:18:25.629Z",
    "localTimestamp": "2017-04-25T22:18:25.629-07:00",
    "entities": [{
        "locale": "en-US",
        "country": "US",
        "platform": "Web",
        "type": "clientInfo"
    }],
    "text": "",
    "attachments": [],
    "address": {
        "id": "f:7638210432489287768",
        "channelId": "msteams",
        "user": {
            "id": "29:1A5TJWHkbOwSyu_L9Ktk9QFI1d_kBOEPeNEeO1INscpKHzHTvWfiau5AX_6y3SuiOby-r73dzHJ17HipUWqGPgw",
            "aadObjectId": "fc8ca1c0-d043-4af6-b09f-141536207403"
        },
        "conversation": {
            "id": "19:7705841b240044b297123ad7f9c99217@thread.skype"
        },
        "bot": {
            "id": "28:c073afa8-7e77-4f92-b3e7-aa589e952a3e",
            "name": "maotestbot2"
        },
        "serviceUrl": "https://smba.trafficmanager.net/amer-client-ss.msg/",
        "useAuth": true
    },
    "source": "msteams"
}
```

## <a name="code-sample"></a>Codebeispiel

|**Beispielname** | **Beschreibung** |**.NET** | **Node.js**|
|----------------|-----------------|--------------|----------------|
|Nachrichtenerweiterungen – Authentifizierung und Konfiguration | Eine Nachrichtenerweiterung, die über eine Konfigurationsseite verfügt, Suchanforderungen akzeptiert und Ergebnisse zurückgibt, nachdem sich der Benutzer angemeldet hat. |[View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/52.teams-messaging-extensions-search-auth-config)|[Anzeigen](https://github.com/microsoft/BotBuilder-Samples/blob/main/samples/javascript_nodejs/52.teams-messaging-extensions-search-auth-config)|

## <a name="see-also"></a>Siehe auch

[Unterstützung für Single Sign-On (SSO) für Nachrichtenerweiterungen](~/messaging-extensions/how-to/enable-sso-auth-me.md)
