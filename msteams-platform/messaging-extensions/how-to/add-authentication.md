---
title: Hinzufügen einer Authentifizierung zu Ihrer Messaging-Erweiterung
author: clearab
description: Hinzufügen der Authentifizierung zu einer Messagingerweiterung
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: 04ece6fe6f5e824873ed6e69385bce017df6927d
ms.sourcegitcommit: 79e6bccfb513d4c16a58ffc03521edcf134fa518
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 04/13/2021
ms.locfileid: "51696773"
---
# <a name="add-authentication-to-your-messaging-extension"></a>Hinzufügen einer Authentifizierung zu Ihrer Messaging-Erweiterung

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

Die `id` Werte und werden für den `aadObjectId` authentifizierten Teams-Benutzer garantiert. Sie werden als Schlüssel verwendet, um die Anmeldeinformationen oder einen beliebigen zwischengespeicherten Status in Ihrem Dienst nach zu suchen. Darüber hinaus enthält jede Anforderung die Azure Active Directory-Mandanten-ID des Benutzers, die zum Identifizieren der Organisation des Benutzers verwendet wird. Falls zutreffend, enthält die Anforderung auch die Team-ID und die Kanal-ID, von der die Anforderung stammt.

## <a name="authentication"></a>Authentifizierung

Wenn ihr Dienst eine Benutzerauthentifizierung erfordert, müssen sich die Benutzer anmelden, bevor sie die Messagingerweiterung verwenden. Die Authentifizierungsschritte ähneln denen eines Bots oder einer Registerkarte. Die Reihenfolge lautet wie folgt:

1. Der Benutzer gibt eine Abfrage aus, oder die Standardabfrage wird automatisch an Ihren Dienst gesendet.
1. Ihr Dienst überprüft, ob der Benutzer authentifiziert ist, indem er die Teams-Benutzer-ID überprüft.
1. Wenn der Benutzer nicht authentifiziert ist, senden Sie eine Antwort mit einer vorgeschlagenen `auth` `openUrl` Aktion zurück, einschließlich der Authentifizierungs-URL.
1. Der Microsoft Teams-Client startet ein Dialogfeld, in dem Ihre Webseite mit der angegebenen Authentifizierungs-URL hosten wird.
1. Nach der Anmeldung des Benutzers sollten Sie das Fenster schließen und einen **Authentifizierungscode** an den Teams-Client senden.
1. Der Teams-Client gibt die Abfrage dann erneut an Ihren Dienst weiter, der den in Schritt 5 übergebenen Authentifizierungscode enthält.

Ihr Dienst sollte überprüfen, ob der in Schritt 6 empfangene Authentifizierungscode mit dem aus Schritt 5 entspricht. Dadurch wird sichergestellt, dass ein böswilliger Benutzer nicht versucht, den Anmeldefluss zu spoofen oder zu schädlich zu machen. Dadurch wird die Schleife geschlossen, um die sichere Authentifizierungssequenz zu beenden.

### <a name="respond-with-a-sign-in-action"></a>Reagieren mit einer Anmeldeaktion

Um einen nicht authentifizierten Benutzer zur Anmeldung auffordert, antworten Sie mit einer vorgeschlagenen Aktion vom Typ, die `openUrl` die Authentifizierungs-URL enthält.

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
> Damit die Anmeldeerfahrung in einem Teams-Popupfenster gehostet wird, muss sich der Domänenteil der URL in der Liste der gültigen Domänen Ihrer App befinden. Weitere Informationen finden Sie [unter validDomains](~/resources/schema/manifest-schema.md#validdomains) im Manifestschema.

### <a name="start-the-sign-in-flow"></a>Starten des Anmeldeflusses

Ihre Anmeldeerfahrung muss reaktionsfähig sein und in ein Popupfenster passen. Es sollte in das [Microsoft Teams JavaScript-Client-SDK](/javascript/api/overview/msteams-client)integriert werden, das die Nachrichtenübertragung verwendet.

Wie bei anderen eingebetteten Erfahrungen, die in Microsoft Teams ausgeführt werden, muss Ihr Code im Fenster zuerst `microsoftTeams.initialize()` aufrufen. Wenn Ihr Code einen OAuth-Fluss ausführt, können Sie die Teams-Benutzer-ID an Ihr Fenster übergeben, das sie dann an die OAuth-Anmelde-URL weitergibt.

### <a name="complete-the-sign-in-flow"></a>Abschließen des Anmeldeflusses

Wenn die Anmeldeanforderung abgeschlossen ist und zurück zu Ihrer Seite umgeleitet wird, müssen sie die folgenden Schritte ausführen:

1. Generieren Sie einen Sicherheitscode. Dies ist eine Zufallszahl. Sie müssen diesen Code in Ihrem Dienst zusammen mit den Anmeldeinformationen zwischenspeichern, die durch den Anmeldefluss erhalten wurden, z. B. OAuth 2.0-Token.
1. Rufen `microsoftTeams.authentication.notifySuccess` Sie den Sicherheitscode auf, und übergeben Sie ihn.

An diesem Punkt wird das Fenster geschlossen, und das Steuerelement wird an den Teams-Client übergeben. Der Client gibt nun die ursprüngliche Benutzerabfrage zusammen mit dem Sicherheitscode in der Eigenschaft `state` neu aus. Ihr Code kann den Sicherheitscode verwenden, um die zuvor gespeicherten Anmeldeinformationen nach zu suchen, um die Authentifizierungssequenz zu vervollständigen und dann die Benutzeranforderung zu vervollständigen.

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
|Messagingerweiterungen – Authentifizierung und Konfiguration | Eine Messagingerweiterung mit einer Konfigurationsseite, die Suchanforderungen akzeptiert und Ergebnisse zurückgibt, nachdem sich der Benutzer angemeldet hat. |[View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/52.teams-messaging-extensions-search-auth-config)|[View](https://github.com/microsoft/BotBuilder-Samples/blob/main/samples/javascript_nodejs/52.teams-messaging-extensions-search-auth-config)| 

 
