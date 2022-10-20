---
title: Erstellen von Apps für anonyme Benutzer
author: v-sdhakshina
description: Erfahren Sie, wie Sie Apps für anonyme Benutzer erstellen und die Erfahrung testen, die anonymen Benutzern in Besprechungs-Apps mit allen Administratoreinstellungen bereitgestellt wird.
ms.topic: conceptual
ms.author: v-sdhakshina
ms.localizationpriority: medium
ms.openlocfilehash: ff897c5135740557e12898e7e5d231557b2e2823
ms.sourcegitcommit: 40d4bde10b6820c62e49e2400b10ab3569c8c815
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/20/2022
ms.locfileid: "68615478"
---
# <a name="build-apps-for-anonymous-users"></a>Erstellen von Apps für anonyme Benutzer

Sie können Bots, Messaging-Erweiterungen, Karten und Aufgabenmodule in Ihrer App erstellen, um mit anonymen Besprechungsteilnehmern in Kontakt zu treten.

Um die App-Erfahrung für anonyme Benutzer zu testen, wählen Sie die URL in der Besprechungseinladung aus, und nehmen Sie in einem privaten Browserfenster an der Besprechung teil.

## <a name="admin-setting-for-anonymous-user-app-interaction"></a>Admin Einstellung für die Interaktion mit anonymen Benutzer-Apps

Teams-Administratoren können das Verwaltungsportal verwenden, um die Interaktion mit anonymen Benutzer-Apps für den gesamten Mandanten zu aktivieren oder zu deaktivieren. Diese Einstellung ist standardmäßig aktiviert. Weitere Informationen finden Sie unter ["Zulassen, dass anonyme Benutzer in Besprechungen mit Apps interagieren](/microsoftteams/meeting-settings-in-teams)".

## <a name="in-meeting-getcontext-from-teams-client-sdk"></a>In-Meeting getContext aus dem Teams-Client-SDK

Apps erhalten die folgenden Informationen für einen anonymen Benutzer, wenn sie die `getContext` API aus der freigegebenen App-Phase aufrufen. Sie können anonyme Benutzer erkennen, indem Sie nach dem `userLicenseType` Wert " **Unbekannt**" suchen.

```csharp
"userObjectId": "8:anon:<GUID1>",
"userLicenseType": "Unknown",
"loginHint": "8:teamsvisitor:<ID>",
"userPrincipalName": "8:teamsvisitor:<ID>",
"tid": "<meeting organizer tenant ID>"
```

| **Eigenschaftsname** | **Beschreibung** |
| --- | --- |
| `userObjectId` | Eindeutiger generierter Wert für den anonymen Benutzer. Dieser Wert kann nicht in Aufrufen von Graph-APIs verwendet werden. |
| `userLicenseType` | `Unknown`, stellt anonymen Benutzer dar. |
| `loginHint` | Eindeutiger generierter Wert. Dieser Wert kann nicht als Hinweis in Anmeldeflüssen verwendet werden. |
| `userPrincipalName` | Eindeutiger generierter Wert. Dieser Wert kann nicht in Aufrufen von Graph-APIs verwendet werden. |
| `tid` | Mandanten-ID des Besprechungsorganisators. |

> [!NOTE]
> Wenn ein anonymer Benutzer an einer Besprechung teilnimmt, wird eine neue Benutzer-ID generiert. Immer wenn der anonyme Benutzer erneut an einer Besprechung teilnimmt, wird eine andere Benutzer-ID generiert.

## <a name="bot-activities-and-apis"></a>Bot-Aktivitäten und APIs

Bei einigen Unterschieden sind die an Ihren Bot gesendeten Aktivitäten und die Antworten, die er von Bot-APIs erhält, zwischen anonymen und nicht anonymen Besprechungsteilnehmern konsistent. Allgemein gilt:

* Die Benutzer-ID ist ein generierter Wert, der bei jeder Teilnahme des anonymen Benutzers an der Besprechung unterschiedlich ist.
* Die `aadObjectId` Eigenschaft wird ausgelassen.
* Die `userRole` Eigenschaft ist auf **"anonym**" festgelegt.
* Die bereitgestellte Mandanten-ID wird auf die Mandanten-ID des Besprechungsorganisators festgelegt.

### <a name="get-members-and-get-single-member-apis"></a>Abrufen von Mitgliedern und Abrufen einzelner Member-APIs

Die [APIs zum Abrufen von Mitgliedern](/microsoftteams/platform/bots/how-to/get-teams-context#fetch-the-roster-or-user-profile) und [einzelnen Mitgliedern](/microsoftteams/platform/bots/how-to/get-teams-context#get-single-member-details) geben eingeschränkte Informationen für anonyme Benutzer zurück:

```json
{ 
  "id": "<GUID1>", 
  "name": "<AnonTest (Guest)>",  
  "tenantId": "<GUID2>", 
  "userRole": "anonymous" 
} 
```

| **Eigenschaftsname** | **Beschreibung** |
| --- | --- |
| `id` | Eindeutiger generierter Wert für den anonymen Benutzer. |
| `name` | Name, der vom anonymen Benutzer bei der Teilnahme an der Besprechung angegeben wird. |
| `tenantId` | Mandanten-ID des Besprechungsorganisators. |
| `userRole` | `anonymous`, stellt anonymen Benutzer dar. |

> [!NOTE]
> Die von den Bot-APIs und der Teams-Client-SDK-API empfangene ID ist nicht identisch.

### <a name="conversationupdate-activity-membersadded-and-membersremoved"></a>ConversationUpdate-Aktivität "MembersAdded" und "MembersRemoved"

```csharp
{ 
  "membersAdded": [ 
    { 
      "id": "<GUID1>" 
    } 
  ], 
  "type": "conversationUpdate", 
  "timestamp": "<timestamp>", 
  "id": "<event unique identifier>", 
  "channelId": "msteams", 
  "serviceUrl": "<serviceURL>", 
  "from": { 
    "id": "<GUID2>" 
  }, 
  "conversation": { 
    "isGroup": true, 
    "tenantId": "<tenant id>", 
    "id": "<conversation id>" 
  }, 
  "recipient": { 
    "id": "<bot id>", 
    "name": "<bot name>" 
  }, 
  "channelData": { 
    "tenant": { 
      "id": "<tenant id>" 
    }, 
    "source": null, 
    "meeting": { 
      "id": "<meeting id>" 
    } 
  } 
} 
```

| **Eigenschaftsname** | **Beschreibung** |
| --- | --- |
| `membersAdded.id` | Anonyme Benutzer-ID. |
| `from.id` | Besprechungsorganisator-ID. |
| `conversation.tenantId` | Mandanten-ID des Besprechungsorganisators. |
| `conversation.id` | Unterhaltungs-ID des Besprechungschats. |
| `tenant.id` | Mandanten-ID des Besprechungsorganisators. |

Ähnliche Änderungen gelten für die Aktivitätsnutzlast `membersRemoved` .

> [!NOTE]
>
> Wenn ein anonymer Benutzer an einer Besprechung teilnimmt oder diese verlässt, hat das `from` Objekt in der Nutzlast immer die ID des Besprechungsorganisators, auch wenn die Aktion von einer anderen Person ausgeführt wurde.

### <a name="create-conversation-api"></a>Unterhaltungs-API erstellen

Bots dürfen keine 1:1-Unterhaltung mit einem anonymen Benutzer initiieren. Wenn ein Bot die Api zum Erstellen von Unterhaltungen mit der Benutzer-ID eines anonymen Benutzers aufruft, erhält er einen `400` Statuscode "Ungültige Anforderung" und die folgende Fehlerantwort:

```csharp
{ 
  "error": {
    "code": "BadArgument",
    "message": "Bot cannot create a conversation with an anonymous user"
  }
} 
```

### <a name="adaptive-cards"></a>Adaptive Karten

Anonyme Benutzer können adaptive Karten im Besprechungschat anzeigen und mit ihnen interagieren. Aktionen für adaptive Karten verhalten sich für anonyme und nicht anonyme Benutzer auf die gleiche Weise. Weitere Informationen finden Sie unter [Kartenaktionen](/microsoftteams/platform/task-modules-and-cards/cards/cards-actions?tabs=json).

## <a name="known-issues-and-limitations"></a>Bekannte Probleme und Einschränkungen

* Seitenbereichregister und Inhaltsblasen sind für anonyme Benutzer nicht verfügbar. Anonyme Benutzer können weiterhin App-Inhalte sehen, die für die Besprechungsphase freigegeben wurden.

* Bei einem anonymen Benutzer unterscheiden sich die Benutzer-ID und `getContext` die vom Bot empfangene Benutzer-ID. Es ist nicht möglich, die beiden direkt zu korrelieren. Wenn Sie die Identität des Benutzers zwischen Ihrer Registerkarte und Ihrem Bot nachverfolgen müssen, müssen Sie den Benutzer auffordern, sich bei einem externen Identitätsanbieter zu authentifizieren.

* Anonyme Benutzer sehen ein generisches App-Symbol auf Bot-Nachrichten und -Karten anstelle des tatsächlichen Symbols der App. Beispiel:

    :::image type="content" source="../assets/images/apps-in-meetings/app-icon.png" alt-text="Dieser Screenshot zeigt, wie das App-Symbol für anonyme Benutzer angezeigt wird.":::

## <a name="see-also"></a>Siehe auch

* [Erstellen von Apps für teams-Besprechungsphase](build-apps-for-teams-meeting-stage.md)
* [APIs für Besprechungs-Apps](meeting-apps-apis.md)
* [Funktionsweise von Microsoft Teams-Bots](/azure/bot-service/bot-builder-basics-teams)
