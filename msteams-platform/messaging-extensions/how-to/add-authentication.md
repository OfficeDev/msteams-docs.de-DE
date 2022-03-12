---
title: Hinzufügen einer Authentifizierung zu Ihrer Messaging-Erweiterung
author: surbhigupta
description: Erfahren Sie, wie Sie einer Messaging-Erweiterung mithilfe von Codebeispielen und Beispielen eine Authentifizierung hinzufügen.
ms.localizationpriority: medium
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: 932f62a086cc87d0d1662a4f27d1b6bdd199b8af
ms.sourcegitcommit: 8a0ffd21c800eecfcd6d1b5c4abd8c107fcf3d33
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 03/12/2022
ms.locfileid: "63452942"
---
# <a name="add-authentication-to-your-messaging-extension"></a>Hinzufügen einer Authentifizierung zu Ihrer Messaging-Erweiterung

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

## <a name="identify-the-user"></a>Identifizieren des Benutzers

Jede Anforderung an Ihre Dienste enthält die Benutzer-ID, den Anzeigenamen des Benutzers und Azure Active Directory Objekt-ID.

```json
"from": {
  "id": "29:1C7dbRrC_5yzN1RGtZIrcWT0xz88KPGP9sxdpVpV8sODlgPHeQE9RqQ02hnpuKzy6zZ-AaZx6swUOMj_Dsdse3TQ4sIaeebbFBF-VgjJy_nY",
  "name": "Larry Jin",
  "aadObjectId": "cd723fa0-0591-416a-9290-e93ecf3a9b92"
},
```

Die `id` und `aadObjectId` die Werte sind für den authentifizierten Teams Benutzer garantiert. Sie werden als Schlüssel verwendet, um die Anmeldeinformationen oder einen zwischengespeicherten Status in Ihrem Dienst nachzuschlagen. Darüber hinaus enthält jede Anforderung die Azure Active Directory Mandanten-ID, die verwendet wird, um die Organisation des Benutzers zu identifizieren. Falls zutreffend, enthält die Anforderung auch die Team-ID und kanal-ID, von denen die Anforderung stammt.

## <a name="authentication"></a>Authentifizierung

Wenn Ihr Dienst eine Benutzerauthentifizierung erfordert, müssen sich die Benutzer anmelden, bevor sie die Messaging-Erweiterung verwenden. Die Authentifizierungsschritte ähneln denen eines Bots oder einer Registerkarte. Die Sequenz sieht wie folgt aus:

1. Der Benutzer gibt eine Abfrage aus, oder die Standardabfrage wird automatisch an Ihren Dienst gesendet.
1. Ihr Dienst überprüft, ob der Benutzer authentifiziert ist, indem er die Teams Benutzer-ID überprüft.
1. Wenn der Benutzer nicht authentifiziert ist, senden Sie eine Antwort mit einer `auth` `openUrl` vorgeschlagenen Aktion einschließlich der Authentifizierungs-URL zurück.
1. Der Microsoft Teams Client startet ein Dialogfeld, in dem Ihre Webseite mithilfe der angegebenen Authentifizierungs-URL gehostet wird.
1. Nachdem sich der Benutzer angemeldet hat, sollten Sie das Fenster schließen und einen **Authentifizierungscode** an den Teams Client senden.
1. Der Teams-Client sendet dann die Abfrage erneut an Ihren Dienst, der den in Schritt 5 übergebenen Authentifizierungscode enthält.

Ihr Dienst sollte überprüfen, ob der in Schritt 6 empfangene Authentifizierungscode mit dem aus Schritt 5 übereinstimmt. Dadurch wird sichergestellt, dass ein böswilliger Benutzer nicht versucht, den Anmeldefluss zu spoofen oder zu kompromittieren. Dadurch wird die Schleife "geschlossen", um die sichere Authentifizierungssequenz abzuschließen.

### <a name="respond-with-a-sign-in-action"></a>Antworten mit einer Anmeldeaktion

Um einen nicht authentifizierten Benutzer zur Anmeldung aufzufordern, antworten Sie mit einer vorgeschlagenen Aktion vom Typ `openUrl` , die die Authentifizierungs-URL enthält.

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
> * Damit die Anmeldeumgebung in einem Teams Popupfenster gehostet werden kann, muss sich der Domänenteil der URL in der Liste der gültigen Domänen Ihrer App befinden. Weitere Informationen finden Sie unter ["validDomains](~/resources/schema/manifest-schema.md#validdomains) " im Manifestschema.
> * Die Größe des Authentifizierungspop-Up kann definiert werden, indem Abfragezeichenfolgenparameter der Breite und Höhe eingeschlossen werden. `Value = $"{_siteUrl}/searchSettings.html?settings={escapedSettings}",`

### <a name="start-the-sign-in-flow"></a>Starten des Anmeldeflusses

Die Anmeldeerfahrung muss reaktionsfähig sein und in ein Popupfenster passen. Es sollte in das [Microsoft Teams JavaScript-Client-SDK](/javascript/api/overview/msteams-client) integriert werden, das die Nachrichtenübergabe verwendet.

Wie bei anderen eingebetteten Oberflächen, die in Microsoft Teams ausgeführt werden, muss Ihr Code innerhalb des Fensters zuerst aufgerufen werden`microsoftTeams.initialize()`. Wenn Ihr Code einen OAuth-Fluss durchführt, können Sie die Teams Benutzer-ID an Ihr Fenster übergeben, das sie dann an die OAuth-Anmelde-URL übergibt.

### <a name="complete-the-sign-in-flow"></a>Abschließen des Anmeldeflusses

Wenn die Anmeldeanforderung abgeschlossen ist und zurück zu Ihrer Seite geleitet wird, müssen die folgenden Schritte ausgeführt werden:

1. Generieren Sie einen Sicherheitscode, eine Zufallszahl. Sie müssen diesen Code in Ihrem Dienst zusammen mit den über den Anmeldefluss abgerufenen Anmeldeinformationen zwischenspeichern, z. B. OAuth 2.0-Token.
1. Rufen Sie den Sicherheitscode auf `microsoftTeams.authentication.notifySuccess` , und übergeben Sie ihn.

An diesem Punkt wird das Fenster geschlossen, und das Steuerelement wird an den Teams Client übergeben. Der Client stellt jetzt die ursprüngliche Benutzerabfrage zusammen mit dem Sicherheitscode in der `state` Eigenschaft neu dar. Ihr Code kann den Sicherheitscode verwenden, um die zuvor gespeicherten Anmeldeinformationen nachzuschlagen, um die Authentifizierungssequenz abzuschließen und dann die Benutzeranforderung abzuschließen.

#### <a name="reissued-request-example"></a>Beispiel für erneutesued-Anforderung

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
|Messaging-Erweiterungen – Authentifizierung und Konfiguration | Eine Messaging-Erweiterung, die über eine Konfigurationsseite verfügt, Suchanforderungen akzeptiert und Ergebnisse zurückgibt, nachdem sich der Benutzer angemeldet hat. |[View](https://github.com/microsoft/BotBuilder-Samples/tree/main/samples/csharp_dotnetcore/52.teams-messaging-extensions-search-auth-config)|[Anzeigen](https://github.com/microsoft/BotBuilder-Samples/blob/main/samples/javascript_nodejs/52.teams-messaging-extensions-search-auth-config)|

## <a name="see-also"></a>Siehe auch

[SSO-Unterstützung (Single Sign-On) für Messaging-Erweiterungen](~/messaging-extensions/how-to/enable-sso-auth-me.md)
