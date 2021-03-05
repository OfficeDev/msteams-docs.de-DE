---
title: Hinzufügen der Authentifizierung zu Ihrer Messagingerweiterung
author: clearab
description: Hinzufügen der Authentifizierung zu einer Messagingerweiterung
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: d673f52e63ba845675f6631470af68d65c7297ad
ms.sourcegitcommit: 5cb3453e918bec1173899e7591b48a48113cf8f0
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/04/2021
ms.locfileid: "50449570"
---
# <a name="add-authentication-to-your-messaging-extension"></a>Hinzufügen der Authentifizierung zu Ihrer Messagingerweiterung

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

## <a name="identify-the-user"></a>Identifizieren des Benutzers

Jede Anforderung an Ihre Dienste enthält die verschleierte ID des Benutzers, der die Anforderung ausgeführt hat, sowie den Anzeigenamen des Benutzers und die Azure Active Directory-Objekt-ID.

```json
"from": {
  "id": "29:1C7dbRrC_5yzN1RGtZIrcWT0xz88KPGP9sxdpVpV8sODlgPHeQE9RqQ02hnpuKzy6zZ-AaZx6swUOMj_Dsdse3TQ4sIaeebbFBF-VgjJy_nY",
  "name": "Larry Jin",
  "aadObjectId": "cd723fa0-0591-416a-9290-e93ecf3a9b92"
},
```

Die `id` Werte und sind garantiert der des `aadObjectId` authentifizierten Teams-Benutzers. Sie können als Schlüssel verwendet werden, um Anmeldeinformationen oder einen beliebigen zwischengespeicherten Status in Ihrem Dienst nach zu suchen. Darüber hinaus enthält jede Anforderung die Azure Active Directory-Mandanten-ID des Benutzers, mit der die Organisation des Benutzers identifiziert werden kann. Falls zutreffend, enthält die Anforderung auch die Team- und Kanal-IDs, von denen die Anforderung stammt.

## <a name="authentication"></a>Authentifizierung

Wenn ihr Dienst eine Benutzerauthentifizierung erfordert, müssen Sie sich beim Benutzer anmelden, bevor er die Messagingerweiterung verwenden kann. Wenn Sie einen Bot oder eine Registerkarte geschrieben haben, die sich im Benutzer signiert, sollte dieser Abschnitt vertraut sein.

Die Reihenfolge lautet wie folgt:

1. Der Benutzer gibt eine Abfrage aus, oder die Standardabfrage wird automatisch an Ihren Dienst gesendet.
2. Ihr Dienst überprüft, ob sich der Benutzer zuerst authentifiziert hat, indem er die Teams-Benutzer-ID überprüft.
3. Wenn sich der Benutzer nicht authentifiziert hat, senden Sie eine Antwort mit einer vorgeschlagenen `auth` `openUrl` Aktion zurück, einschließlich der Authentifizierungs-URL.
4. Der Microsoft Teams-Client startet ein Popupfenster, in dem Ihre Webseite mit der angegebenen Authentifizierungs-URL hosten wird.
5. Nach der Anmeldung des Benutzers sollten Sie ihr Fenster schließen und einen "Authentifizierungscode" an den Teams-Client senden.
6. Der Teams-Client gibt die Abfrage dann erneut an Ihren Dienst weiter, der den in Schritt 5 übergebenen Authentifizierungscode enthält.

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
> Damit die Anmeldeerfahrung in einem Teams-Popup gehostet wird, muss sich der Domänenteil der URL in der Liste der gültigen Domänen Ihrer App befinden. (Siehe [validDomains](~/resources/schema/manifest-schema.md#validdomains) im Manifestschema.)

### <a name="start-the-sign-in-flow"></a>Starten des Anmeldeflusses

Ihre Anmeldeerfahrung sollte reaktionsfähig sein und in ein Popupfenster passen. Es sollte in das [Microsoft Teams JavaScript-Client-SDK](/javascript/api/overview/msteams-client)integriert werden, das die Nachrichtenübertragung verwendet.

Wie bei anderen eingebetteten Erfahrungen, die in Microsoft Teams ausgeführt werden, muss Ihr Code im Fenster zuerst `microsoftTeams.initialize()` aufrufen. Wenn Ihr Code einen OAuth-Fluss ausführt, können Sie die Teams-Benutzer-ID an Ihr Fenster übergeben, die sie dann an die OAuth-Anmelde-URL übergeben kann.

### <a name="complete-the-sign-in-flow"></a>Abschließen des Anmeldeflusses

Wenn die Anmeldeanforderung abgeschlossen ist und wieder zu Ihrer Seite umgeleitet wird, sollten sie die folgenden Schritte ausführen:

1. Generieren Sie einen Sicherheitscode. (Dies kann eine Zufallszahl sein.) Sie müssen diesen Code in Ihrem Dienst zusammen mit den Anmeldeinformationen zwischenspeichern, die über den Anmeldefluss (z. B. OAuth 2.0-Token) erhalten wurden.
2. Rufen `microsoftTeams.authentication.notifySuccess` Sie den Sicherheitscode auf, und übergeben Sie ihn.

An diesem Punkt wird das Fenster geschlossen, und das Steuerelement wird an den Teams-Client übergeben. Der Client kann nun die ursprüngliche Benutzerabfrage zusammen mit dem Sicherheitscode in der Eigenschaft erneut `state` ausführen. Ihr Code kann den Sicherheitscode verwenden, um die zuvor gespeicherten Anmeldeinformationen nach zu suchen, um die Authentifizierungssequenz zu vervollständigen und dann die Benutzeranforderung zu vervollständigen.

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

 
