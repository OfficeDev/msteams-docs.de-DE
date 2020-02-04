---
title: Hinzufügen von Authentifizierung zu Ihrer Messaging Erweiterung
author: clearab
description: Hinzufügen einer Authentifizierung zu einer Messaging Erweiterung
ms.topic: conceptual
ms.author: anclear
ms.openlocfilehash: f7ebbcd99b1ec35900de7ec2f54f93263918e945
ms.sourcegitcommit: 4329a94918263c85d6c65ff401f571556b80307b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/01/2020
ms.locfileid: "41674145"
---
# <a name="add-authentication-to-your-messaging-extension"></a>Hinzufügen von Authentifizierung zu Ihrer Messaging Erweiterung

[!include[v4-to-v3-SDK-pointer](~/includes/v4-to-v3-pointer-me.md)]

## <a name="identify-the-user"></a>Identifizieren des Benutzers

Jede Anforderung an ihre Dienste umfasst die verborgene ID des Benutzers, der die Anforderung ausgeführt hat, sowie den Anzeigenamen des Benutzers und die Azure Active Directory Objekt-ID.

```json
"from": {
  "id": "29:1C7dbRrC_5yzN1RGtZIrcWT0xz88KPGP9sxdpVpV8sODlgPHeQE9RqQ02hnpuKzy6zZ-AaZx6swUOMj_Dsdse3TQ4sIaeebbFBF-VgjJy_nY",
  "name": "Larry Jin",
  "aadObjectId": "cd723fa0-0591-416a-9290-e93ecf3a9b92"
},
```

Die `id` Werte `aadObjectId` und sind garantiert die des authentifizierten Teams-Benutzers. Sie können als Schlüssel zum Nachschlagen von Anmeldeinformationen oder einem beliebigen zwischengespeicherten Zustand in Ihrem Dienst verwendet werden. Darüber hinaus enthält jede Anforderung die Azure Active Directory Mandanten-ID des Benutzers, die zum Identifizieren der Organisation des Benutzers verwendet werden kann. Wenn zutreffend, enthält die Anforderung auch die Team-und Kanal-IDs, aus denen die Anforderung stammt.

## <a name="authentication"></a>Authentifizierung

Wenn Ihr Dienst eine Benutzerauthentifizierung erfordert, müssen Sie sich beim Benutzer anmelden, bevor er die Messaging Erweiterung verwenden kann. Wenn Sie einen bot oder eine Registerkarte geschrieben haben, die den Benutzer signiert, sollte dieser Abschnitt vertraut sein.

Die Sequenz lautet wie folgt:

1. Der Benutzer gibt eine Abfrage aus, oder die Standardabfrage wird automatisch an den Dienst gesendet.
2. Der Dienst überprüft, ob der Benutzer zuerst authentifiziert wurde, indem er die Benutzer-ID des Teams überprüft.
3. Wenn der Benutzer nicht authentifiziert wurde, senden Sie eine `auth` Antwort mit einer `openUrl` vorgeschlagenen Aktion einschließlich der Authentifizierungs-URL zurück.
4. Der Microsoft Teams-Client startet ein Popupfenster, das Ihre Webseite unter Verwendung der angegebenen Authentifizierungs-URL hostet.
5. Nachdem sich der Benutzer angemeldet hat, sollten Sie das Fenster schließen und einen "Authentifizierungscode" an den Microsoft Teams-Client senden.
6. Der Microsoft Teams-Client gibt dann die Abfrage erneut an Ihren Dienst aus, der den in Schritt 5 übergebenen Authentifizierungscode enthält.

Ihr Dienst sollte überprüfen, ob der in Schritt 6 empfangene Authentifizierungscode mit dem in Schritt 5 übereinstimmt. Dadurch wird sichergestellt, dass ein böswilliger Benutzer nicht versucht, den Anmelde Ablauf vorzutäuschen oder zu gefährden. Dies effektiv "schließt die Schleife", um die sichere Authentifizierungssequenz abzuschließen.

### <a name="respond-with-a-sign-in-action"></a>Reagieren mit einer Anmeldeaktion

Um einen nicht authentifizierten Benutzer zur Anmeldung aufzufordern, Antworten Sie mit einer vorgeschlagenen Aktion `openUrl` vom Typ, die die Authentifizierungs-URL enthält.

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
> Damit die Anmelde Umgebung in einem Teams-Popup gehostet werden kann, muss der Domänenteil der URL in der Liste der gültigen Domänen in Ihrer APP aufgeführt sein. (Weitere Informationen finden Sie unter [validDomains](~/resources/schema/manifest-schema.md#validdomains) im Manifest-Schema.)

### <a name="start-the-sign-in-flow"></a>Starten des Anmelde Flusses

Ihre Anmelde Erfahrung sollte reagieren und in ein Popupfenster passt. Sie sollte in das [Microsoft Teams JavaScript Client SDK](/javascript/api/overview/msteams-client)integriert werden, das die Nachrichtenübergabe verwendet.

Wie bei anderen eingebetteten Erfahrungen, die in Microsoft Teams durchführen, muss der Code im Fenster zuerst `microsoftTeams.initialize()`aufgerufen werden. Wenn Ihr Code einen OAuth-Fluss ausführt, können Sie die Benutzer-ID des Teams an das Fenster übergeben, das dann an die OAuth-Anmelde-URL übergeben werden kann.

### <a name="complete-the-sign-in-flow"></a>Abschließen des Anmelde Flusses

Wenn die Anmeldeanforderung abgeschlossen wird und zu Ihrer Seite zurückgeleitet wird, sollten Sie die folgenden Schritte ausführen:

1. Generieren Sie einen Sicherheitscode. (Dies kann eine Zufallszahl sein.) Sie müssen diesen Code in Ihrem Dienst Zwischenspeichern, zusammen mit den Anmeldeinformationen, die über den Anmelde Fluss abgerufen werden (beispielsweise OAuth 2,0-Token).
2. Rufen `microsoftTeams.authentication.notifySuccess` Sie den Sicherheitscode an, und übergeben Sie ihn.

Zu diesem Zeitpunkt wird das Fenster geschlossen, und die Steuerung wird an den Microsoft Teams-Client übergeben. Der Client kann jetzt die ursprüngliche Benutzerabfrage erneut ausgeben, zusammen mit dem Sicherheitscode in der `state` -Eigenschaft. Ihr Code kann den Sicherheitscode verwenden, um die zuvor gespeicherten Anmeldeinformationen nachzuschlagen, um die Authentifizierungssequenz abzuschließen und dann die Benutzeranforderung abzuschließen.

#### <a name="reissued-request-example"></a>Beispiel für eine erneut aufgegebene Anforderung

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

