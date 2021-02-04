---
title: Verwenden von Microsoft Graph zum Importieren externer Plattformnachrichten in Teams
description: Beschreibt die Verwendung von Microsoft Graph zum Importieren von Nachrichten von einer externen Plattform in Teams
localization_priority: Normal
author: laujan
ms.author: lajanuar
ms.topic: Overview
keywords: Microsoft Teams import messages api graph microsoft migrate migration post
ms.openlocfilehash: 97f24c34ebb825aad0fd104c9a814e46f9b5fa0d
ms.sourcegitcommit: f74b74d5bed1df193e59f46121ada443fb57277b
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 02/03/2021
ms.locfileid: "50093260"
---
# <a name="import-third-party-platform-messages-to-teams-using-microsoft-graph"></a>Plattform-Nachrichten von Drittanbietern mithilfe von Microsoft Graph in Teams importieren

>[!IMPORTANT]
> Microsoft Graph und Microsoft Teams public previews are available for early-access and feedback. Obwohl diese Version umfassenden Tests unterzogen wurde, ist sie nicht für die Verwendung in der Produktion vorgesehen.

Mit Microsoft Graph können Sie den vorhandenen Nachrichtenverlauf und die Daten von Benutzern aus einem externen System in einen Microsoft Teams-Kanal migrieren. Durch die Neugestaltung einer Drittanbieterplattform-Messaging-Hierarchie in Teams können Benutzer ihre Kommunikation nahtlos fortsetzen und ohne Unterbrechung fortfahren.

## <a name="import-overview"></a>Übersicht über den Import

Der Importvorgang umfasst auf hoher Ebene Folgendes:

1. [Erstellen eines Teams mit einem Back-in-Time-Zeitstempel](#step-one-create-a-team)
1. [Erstellen eines Kanals mit einem Back-in-Time-Zeitstempel](#step-two-create-a-channel)  
1. [Importieren externer Back-in-Time-Nachrichten mit Datum](#step-three-import-messages)
1. [Abschließen des Team- und Kanalmigrationsprozesses](#step-four-complete-migration-mode)
1. [Hinzufügen von Teammitgliedern](#step-five-add-team-members)

## <a name="necessary-requirements"></a>Erforderliche Anforderungen

### <a name="analyze-and-prepare-message-data"></a>Analysieren und Vorbereiten von Nachrichtendaten

✔ Sie die Drittanbieterdaten, um zu entscheiden, was migriert wird.  
✔ extrahieren Sie die ausgewählten Daten aus dem Drittanbieter-Chatsystem.  
✔ Sie die Chatstruktur eines Drittanbieters der Teams-Struktur zu.  
✔ Konvertieren von Importdaten in das für die Migration benötigte Format.  

### <a name="set-up-your-office-365-tenant"></a>Einrichten des Office 365-Mandanten

✔ Stellen Sie sicher, dass ein Office 365-Mandant für die Importdaten vorhanden ist. Weitere Informationen zum Einrichten eines Office 365-Mandanten für Teams finden Sie unter *"* [Vorbereiten Ihres Office 365-Mandanten".](../../concepts/build-and-test/prepare-your-o365-tenant.md)  
✔ Stellen Sie sicher, dass sich Teammitglieder in Azure Active Directory (AAD) befinden.  Weitere Informationen finden *Sie unter* [Hinzufügen eines neuen Benutzers](/azure/active-directory/fundamentals/add-users-azure-active-directory) zu Azure Active Directory.

## <a name="step-one-create-a-team"></a>Schritt 1: Erstellen eines Teams

Da vorhandene Daten migriert werden, sind die Beibehaltung der ursprünglichen Nachrichtenzeitstempel und das Verhindern von Messagingaktivitäten während des Migrationsprozesses entscheidend, um den vorhandenen Nachrichtenfluss des Benutzers in Teams neu zu erstellen. Dies wird wie folgt erreicht:

> [Erstellen Sie ein neues Team](/graph/api/team-post?view=graph-rest-beta&tabs=http&preserve-view=true) mit einem Back-in-Time-Zeitstempel mithilfe der Teamressourceneigenschaft. `createdDateTime` Platzieren Sie das neue Team in einem speziellen Zustand, der Benutzer von den meisten Aktivitäten innerhalb des Teams abgleistet, bis `migration mode` der Migrationsprozess abgeschlossen ist. Schließen Sie das Instanzattribut in den Wert in die POST-Anforderung ein, um das neue Team explizit als `teamCreationMode` für die Migration erstellt zu `migration` identifizieren.  

> **HINWEIS:** Das Feld wird nur für Instanzen eines Teams oder Kanals `createdDateTime` aufgefüllt, die migriert wurden.

<!-- markdownlint-disable MD001 -->

#### <a name="permissions"></a>Berechtigungen

|ScopeName|DisplayName|Beschreibung|Typ|Administrator-Zustimmung?|Behandelte Entitäten/APIs|
|-|-|-|-|-|-|
|`Teamwork.Migrate.All`|Migration zu Microsoft Teams verwalten|Erstellen, Verwalten von Ressourcen für die Migration zu Microsoft Teams|**Nur Anwendung**|**Ja**|`POST /teams`|

#### <a name="request-create-a-team-in-migration-state"></a>Anforderung (Erstellen eines Teams im Migrationsstatus)

```http
POST https://graph.microsoft.com/beta/teams

Content-Type: application/json
{
  "@microsoft.graph.teamCreationMode": "migration",
  "template@odata.bind": "https://graph.microsoft.com/beta/teamsTemplates('standard')",
  "displayName": "My Sample Team",
  "description": "My Sample Team’s Description",
  "createdDateTime": "2020-03-14T11:22:17.043Z"
}
```

#### <a name="response"></a>Antwort

```http
HTTP/1.1 202 Accepted
Location: /teams/{teamId}/operations/{operationId}
Content-Location: /teams/{teamId}
```

#### <a name="error-messages"></a>Fehlermeldungen

```http
400 Bad Request
```

* `createdDateTime`  für die Zukunft festgelegt.
* `createdDateTime`  richtig angegeben, aber `teamCreationMode`  das Instanzattribut fehlt oder ist auf einen ungültigen Wert festgelegt.

## <a name="step-two-create-a-channel"></a>Schritt 2: Erstellen eines Kanals

Das Erstellen eines Kanals für die importierten Nachrichten ähnelt dem Szenario zum Erstellen eines Teams:

> [Erstellen Sie einen neuen Kanal](/graph/api/channel-post?view=graph-rest-beta&tabs=http&preserve-view=true) mit einem Back-in-Time-Zeitstempel mithilfe der Kanalressourceneigenschaft. `createdDateTime` Platzieren Sie den neuen Kanal in einem besonderen Zustand, der Benutzer von den meisten Chataktivitäten innerhalb des Kanals abgleistet, bis der `migration mode` Migrationsprozess abgeschlossen ist.  Schließen Sie das Instanzattribut in den Wert in die POST-Anforderung ein, um das neue Team explizit als `channelCreationMode` für die Migration erstellt zu `migration` identifizieren.  
<!-- markdownlint-disable MD024 -->
#### <a name="permissions"></a>Berechtigungen

|ScopeName|DisplayName|Beschreibung|Typ|Administrator-Zustimmung?|Behandelte Entitäten/APIs|
|-|-|-|-|-|-|
|`Teamwork.Migrate.All`|Migration zu Microsoft Teams verwalten|Erstellen, Verwalten von Ressourcen für die Migration zu Microsoft Teams|**Nur Anwendung**|**Ja**|`POST /teams`|

#### <a name="request-create-a-channel-in-migration-state"></a>Anforderung (Erstellen eines Kanals im Migrationsstatus)

```http
POST https://graph.microsoft.com/beta/teams/{id}/channels

Content-Type: application/json
{
  "@microsoft.graph.channelCreationMode": "migration",
  "displayName": "Architecture Discussion",
  "description": "This channel is where we debate all future architecture plans",
  "membershipType": "standard",
  "createdDateTime": "2020-03-14T11:22:17.047Z"
}
```

#### <a name="response"></a>Antwort

```http
HTTP/1.1 202 Accepted

{
   "@odata.context":"https://canary.graph.microsoft.com/testprodbetateamsgraphsvcncus/$metadata#teams('9cc6d6ab-07d8-4d14-bc2b-7db8995d6d23')/channels/$entity",
   "id":"19:e90f6814ce674072a4126206e7de485e@thread.tacv2",
   "createdDateTime":null,
   "displayName":"Architecture Discussion",
   "description":"This channel is where we debate all future architecture plans",
   "isFavoriteByDefault":null,
   "email":null,
   "webUrl":null,
   "membershipType":null,
   "moderationSettings":null
}
```

#### <a name="error-message"></a>Fehlermeldung

```http
400 Bad Request
```

* `createdDateTime`  für die Zukunft festgelegt.
* `createdDateTime`  richtig angegeben, `channelCreationMode`  aber das Instanzattribut fehlt oder ist auf einen ungültigen Wert festgelegt.

## <a name="step-three-import-messages"></a>Schritt 3: Importieren von Nachrichten

Nachdem das Team und der Kanal erstellt wurden, können Sie mit dem Senden von Back-in-Time-Nachrichten beginnen, indem Sie die Schlüssel im `createdDateTime` `from`  Anforderungstext verwenden. **HINWEIS:** Nachrichten, die mit einer früheren Zeit als `createdDateTime` dem Nachrichtenthread `createdDateTime` importiert wurden, werden nicht unterstützt.

> [!NOTE]
> * `createdDateTime` muss für alle Nachrichten im selben Thread eindeutig sein.
> * `createdDateTime` unterstützt Zeitstempel mit Millisekundengenauigkeit. Wenn die eingehende Anforderungsnachricht beispielsweise den Wert `createdDateTime` *2020-09-16T05:50:31.0025302Z* hat, wird sie in *2020-09-16T05:50:31.002Z* konvertiert, wenn die Nachricht aufgenommen wird.

#### <a name="request-post-message-that-is-text-only"></a>Anforderung (nur Text enthaltende POST-Nachricht)

```http
POST https://graph.microsoft.com/beta/teams/teamId/channels/channelId/messages

{
   "createdDateTime":"2019-02-04T19:58:15.511Z",
   "from":{
      "user":{
         "id":"id-value",
         "displayName":"Joh Doe",
         "userIdentityType":"aadUser"
      }
   },
   "body":{
      "contentType":"html",
      "content":"Hello World"
   }
}
```

#### <a name="response"></a>Antwort

```http
HTTP/1.1 200 OK

{
   "@odata.context":"https://graph.microsoft.com/beta/$metadata#teams('teamId')/channels('channelId')/messages/$entity",
   "id":"id-value",
   "replyToId":null,
   "etag":"id-value",
   "messageType":"message",
   "createdDateTime":"2019-02-04T19:58:15.58Z",
   "lastModifiedDateTime":null,
   "deleted":false,
   "subject":null,
   "summary":null,
   "importance":"normal",
   "locale":"en-us",
   "policyViolation":null,
   "from":{
      "application":null,
      "device":null,
      "conversation":null,
      "user":{
         "id":"id-value",
         "displayName":"Joh Doe",
         "userIdentityType":"aadUser"
      }
   },
   "body":{
      "contentType":"html",
      "content":"Hello World"
   },
   "attachments":[
   ],
   "mentions":[
   ],
   "reactions":[
   ]
}
```

#### <a name="error-messages"></a>Fehlermeldungen

```http
400 Bad Request
```

#### <a name="request-post-a-message-with-inline-image"></a>Anforderung (POST einer Nachricht mit Inlinebild)

> **Hinweis:** In diesem Szenario gibt es keine speziellen Berechtigungsbereiche, da die Anforderung Teil von chatMessage ist. Bereiche für chatMessage gelten auch hier.

```http
POST https://graph.microsoft.com/beta/teams/teamId/channels/channelId/messages

{
  "body": {
        "contentType": "html",
        "content": "<div><div>\n<div><span><img height=\"250\" src=\"../hostedContents/1/$value\" width=\"176.2295081967213\" style=\"vertical-align:bottom; width:176px; height:250px\"></span>\n\n</div>\n\n\n</div>\n</div>"
    },
    "hostedContents":[
        {
            "@microsoft.graph.temporaryId": "1",
            "contentBytes": "iVBORw0KGgoAAAANSUhEUgAAANcAAAExCAYAAADvFzeeAAAXjklEQVR4Ae2d/XNU1RnH+9e0FFrA0RCIyaS8hRA0HV5KbS1gHRgVpjMClY4GHJ3yYm1HCmXaWttaaZUZtIIFKYi8lFAkvOQ9u5vN225IARVBbX9/Os9NbrLZbMjmhCfJPX5+2Lmb3T25y3O+n/M599x7w9f+++UXwoMakIF7n4GvUdR7X1RqSk01A8CFuZm5GGUAuIwKi72wF3ABF+YyygBwGRUWc2Eu4AIuzGWUAeAyKizmwlzABVyYyygDwGVUWMyFuYALuDCXUQaAy6iwmAtzARdwfWXMdeuzT+TGxz3Sfb1LunrapL07IW3pePDQ5/qavqef0c+OdYAELuAac4jGGkLL9rdvfyo9N9ODQAqBGmmrwGlb/R0u3xG4gMspOC5hG882CoRaaCSA8n1ff9doIQMu4PIOrus3u+8ZVNnw6e/Od5AALuDKOyz5hmqiPnfnzi1J9bSbgRWCpvvQfY307wQu4BoxJCOFaDK8rwsQmQsUIQhWW93XSIsewAVckYdLQ24F0Ui/926AARdwRRounZ6Np7GyYdN9DzdFBC7gijRc43GMlQ1U9s/6HXJNjYELuHI<<-----Removed----->>>>",
            "contentType": "image/png"
        }
    ]
}
```

#### <a name="response"></a>Antwort

```http
HTTP/1.1 200 OK

{
    "@odata.context": "https://graph.microsoft.com/beta/$metadata#teams('teamId')/channels('channelId')/messages/$entity",
    "id": "id-value",
    "replyToId": null,
    "etag": "id-value",
    "messageType": "message",
    "createdDateTime": "2019-02-04T19:58:15.511Z",
    "lastModifiedDateTime": null,
    "deleted": false,
    "subject": null,
    "summary": null,
    "importance": "normal",
    "locale": "en-us",
    "policyViolation": null,
    "from": {
        "application": null,
        "device": null,
        "conversation": null,
        "user": {
            "id": "id-value",
            "displayName": "Joh Doe",
            "userIdentityType": "aadUser"
        }
    },
      "body": {
        "contentType": "html",
        "content": "<div><div>\n<div><span><img height=\"250\" src=\"https://graph.microsoft.com/teams/teamId/channels/channelId/messages/id-value/hostedContents/hostedContentId/$value\" width=\"176.2295081967213\" style=\"vertical-align:bottom; width:176px; height:250px\"></span>\n\n</div>\n\n\n</div>\n</div>"
    },
    "attachments": [],
    "mentions": [],
    "reactions": []
}
```

## <a name="step-four-complete-migration-mode"></a>Schritt 4: Abschließen des Migrationsmodus

Sobald der Nachrichtenmigrationsprozess abgeschlossen ist, werden das Team und der Kanal mithilfe der Methode aus dem Migrationsmodus  `completeMigration`  genommen. In diesem Schritt werden die Team- und Kanalressourcen für die allgemeine Verwendung durch Teammitglieder geöffnet. Die Aktion ist an die Instanz `team` gebunden.

#### <a name="request-end-team-migration-mode"></a>Anforderung (Teammigrationsmodus beenden)

```http
POST https://graph.microsoft.com/beta/teams/teamId/completeMigration

```

#### <a name="response"></a>Antwort

```http
HTTP/1.1 204 NoContent
```

#### <a name="request-end-channel-migration-mode"></a>Anforderung (Endkanalmigrationsmodus)

```http
POST https://graph.microsoft.com/beta/teams/teamId/channels/channelId/completeMigration

```

#### <a name="response"></a>Antwort

```http
HTTP/1.1 204 NoContent
```

#### <a name="error-response"></a>Fehlerantwort

```http
400 Bad Request
```

* Aktion aufgerufen für eine `team` oder die sich nicht in `channel` `migrationMode` befindet.

## <a name="step-five-add-team-members"></a>Schritt 5: Hinzufügen von Teammitgliedern

Sie können ein Mitglied mithilfe der [Benutzeroberfläche](https://support.microsoft.com/office/add-members-to-a-team-in-teams-aff2249d-b456-4bc3-81e7-52327b6b38e9) von Teams oder der Microsoft Graph-Mitglieds-API hinzufügen [zu einem Team](/graph/api/group-post-members?view=graph-rest-beta&tabs=http&preserve-view=true) hinzufügen:

#### <a name="request-add-member"></a>Anforderung (Mitglied hinzufügen)

```http
POST https://graph.microsoft.com/beta/teams/{id}/members
Content-type: application/json
Content-length: 30
{
"@odata.type": "#microsoft.graph.aadUserConversationMember",
"roles": [],
"user@odata.bind": "https://graph.microsoft.com/beta/users/{user-id}"
}
```

#### <a name="response"></a>Antwort

```http
HTTP/1.1 204 No Content
```

## <a name="tips-and-additional-information"></a>Tipps und zusätzliche Informationen

<!-- markdownlint-disable MD001 -->
<!-- markdownlint-disable MD026 -->

* Sie können Nachrichten von Benutzern importieren, die sich nicht in Teams befinden. **HINWEIS:** Nachrichten, die für Benutzer importiert wurden, die nicht im Mandanten vorhanden sind, können während der öffentlichen Vorschau nicht im Client- oder Complianceportal von Teams durchsucht werden.

* Nachdem die `completeMigration` Anforderung gestellt wurde, können Sie keine weiteren Nachrichten in das Team importieren.

* Teammitglieder können dem neuen Team erst hinzugefügt werden, nachdem `completeMigration` die Anforderung eine erfolgreiche Antwort zurückgegeben hat.

* Einschränkung: Nachrichten werden mit 5 RPS pro Kanal importiert.

* Wenn Sie eine Korrektur an den Migrationsergebnissen vornehmen müssen, müssen Sie das Team löschen und die Schritte wiederholen, um das Team und den Kanal zu erstellen und die Nachrichten erneut zu migrieren.

> [!NOTE]
> Derzeit sind Inlinebilder die einzige Art von Medien, die vom Schema der Api zum Importieren von Nachrichten unterstützt werden.

##### <a name="import-content-scope"></a>Importieren des Inhaltsbereichs

|In-Scope | Derzeit nicht bereichsbereichsf?n|
|----------|--------------------------|
|Team- und Kanalnachrichten|1:1 und Gruppenchatnachrichten|
|Zeitpunkt der Ursprünglichen Nachricht|Private Kanäle|
|Inlinebilder als Teil der Nachricht|Erwähnungen|
|Links zu vorhandenen Dateien in SPO/OneDrive|Reaktionen|
|Nachrichten mit Rich-Text|Videos|
|Nachrichtenantwortkette|Ankündigungen|
|Verarbeitung mit hohem Durchsatz|Codeausschnitte|
||Adaptive Karten|
||Sticker|
||Emojis|
||Anführungszeichen|
||Übergreifende Beiträge zwischen Kanälen|

> [!div class="nextstepaction"]
>[Weitere Informationen zur Integration von Microsoft Graph und Teams](/graph/teams-concept-overview)
