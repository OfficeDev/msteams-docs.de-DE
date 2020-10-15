---
title: Verwenden von Microsoft Graph zum Importieren von Nachrichten für externe Plattformen in Teams
description: Beschreibt, wie Microsoft Graph zum Importieren von Nachrichten von einer externen Plattform in Teams verwendet wird.
localization_priority: Normal
author: laujan
ms.author: lajanuar
ms.topic: Overview
keywords: Teams Importieren von Nachrichten API Graph Microsoft migrate Migration Post
ms.openlocfilehash: 0f53e27ec849e18be49f233a754658587343f68b
ms.sourcegitcommit: 25afe104d10c9a6a2849decf5ec1d08969d827c3
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 10/14/2020
ms.locfileid: "48465908"
---
# <a name="import-third-party-platform-messages-to-teams-using-microsoft-graph"></a>Plattform-Nachrichten von Drittanbietern mithilfe von Microsoft Graph in Teams importieren

>[!IMPORTANT]
> Microsoft Graph und Microsoft Teams öffentliche Vorschauen stehen für den frühzeitigen Zugriff und das Feedback zur Verfügung. Obwohl diese Version umfangreiche Tests unterzogen wurde, ist Sie nicht für die Verwendung in der Produktion vorgesehen.

Mit Microsoft Graph können Sie den vorhandenen Nachrichtenverlauf und die Daten von Benutzern aus einem externen System in einen Teams-Kanal migrieren. Durch die Aktivierung einer Drittanbieter-Platt Form Messaging-Hierarchie in Microsoft Teams können Benutzer ihre Kommunikation nahtlos fortsetzen und ohne Unterbrechung fortfahren.

## <a name="import-overview"></a>Import (Übersicht)

Auf hohem Niveau besteht der Importvorgang aus folgenden Elementen:

1. [Erstellen eines Teams mit einem Back-in-Time-Zeitstempel](#step-one-create-a-team)
1. [Erstellen eines Kanals mit einem Back-in-Time-Zeitstempel](#step-two-create-a-channel)  
1. [Importieren externer Back-in-Time datierter Nachrichten](#step-three-import-messages)
1. [Abschließen des Migrationsprozesses für Teams und Kanäle](#step-four-complete-migration-mode)
1. [Hinzufügen von Teammitgliedern](#step-five-add-team-members)

## <a name="necessary-requirements"></a>Erforderliche Anforderungen

### <a name="analyze-and-prepare-message-data"></a>Analysieren und Vorbereiten von Nachrichtendaten

✔ Überprüfen Sie die drittanbieterdaten, um zu entscheiden, was migriert werden soll.  
✔ Extrahieren Sie die ausgewählten Daten aus dem Drittanbieter-Chat System.  
✔ Ordnen Sie die Chat Struktur eines Drittanbieters der Teams-Struktur zu.  
✔ Konvertieren von Importdaten in Format, das für die Migration benötigt wird.  

### <a name="set-up-your-office-365-tenant"></a>Einrichten des Office 365-Mandanten

✔ Sicherstellen, dass ein Office 365 Mandant für die Importdaten vorhanden ist. Weitere Informationen zum Einrichten eines Office 365 Mandanten für Teams *finden Sie unter* [Vorbereiten des Office 365 Mandanten](../../concepts/build-and-test/prepare-your-o365-tenant.md).  
✔ Stellen Sie sicher, dass sich die Teammitglieder in Azure Active Directory (AAD) befinden.  Weitere Informationen *finden Sie unter* [Hinzufügen eines neuen Benutzers](/azure/active-directory/fundamentals/add-users-azure-active-directory) zu Azure Active Directory.

## <a name="step-one-create-a-team"></a>Schritt 1: Erstellen eines Teams

Da vorhandene Daten migriert werden, sind die Beibehaltung der ursprünglichen Nachrichtenzeitstempel und das verhindern von Messaging Aktivitäten während des Migrationsprozesses entscheidend, um den vorhandenen Nachrichtenfluss des Benutzers in Microsoft Teams neu zu erstellen. Dies wird wie folgt erreicht:

> [Erstellen Sie ein neues Team](/graph/api/team-post?view=graph-rest-beta&tabs=http&preserve-view=true) mit einem Back-in-Time-Zeitstempel mithilfe der Team Resource  `createdDateTime`  -Eigenschaft. Platzieren Sie das neue Team in `migration mode` , einem besonderen Status, der Benutzer von den meisten Aktivitäten innerhalb des Teams bis zum Abschluss des Migrationsvorgangs verriegelt. Fügen `teamCreationMode` Sie das Instanz-Attribut mit dem `migration` Wert in die Post-Anforderung ein, um das neue Team explizit als für die Migration erstellt zu identifizieren.  

> **Hinweis**: das `createdDateTime` Feld wird nur für Instanzen eines Teams oder Kanals aufgefüllt, die migriert wurden.

<!-- markdownlint-disable MD001 -->

#### <a name="permissions"></a>Berechtigungen

|ScopeName|DisplayName|Beschreibung|Typ|Zustimmung des Administrators?|Behandelte Entitäten/APIs|
|-|-|-|-|-|-|
|`Teamwork.Migrate.All`|Migration zu Microsoft Teams verwalten|Erstellen und Verwalten von Ressourcen für die Migration zu Microsoft Teams|**Nur Anwendung**|**Ja**|`POST /teams`|

#### <a name="request-create-a-team-in-migration-state"></a>Anforderung (Erstellen eines Teams im Migrationsstatus)

```http
POST https://graph.microsoft.com/beta/teams

Content-Type: application/json
{
  "@microsoft.graph.teamCreationMode": "migration",
  "template@odata.bind": "https://graph.microsoft.com/beta/teamsTemplates('standard')",
  "displayName": "My Sample Team",
  "description": "My Sample Team’s Description"
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

* `createdDateTime`  für Zukunft festgelegt.
* `createdDateTime`  richtig angegeben, `teamCreationMode`  das Instanz-Attribut fehlt oder ist auf ungültigen Wert festgelegt.

## <a name="step-two-create-a-channel"></a>Schritt 2: Erstellen eines Kanals

Das Erstellen eines Kanals für die importierten Nachrichten ähnelt dem Szenario zum Erstellen eines Teams:

> Erstellen Sie mithilfe der Channel-Ressourceneigenschaft [einen neuen Kanal](/graph/api/channel-post?view=graph-rest-beta&tabs=http&preserve-view=true) mit einem Back-in-Time-Zeitstempel `createdDateTime` . Platzieren Sie den neuen Kanal in `migration mode` , einen besonderen Status, der Benutzer von den meisten chataktivitäten innerhalb des Kanals bis zum Abschluss des Migrationsprozesses verriegelt.  Fügen `channelCreationMode` Sie das Instanz-Attribut mit dem `migration` Wert in die Post-Anforderung ein, um das neue Team explizit als für die Migration erstellt zu identifizieren.  
<!-- markdownlint-disable MD024 -->
#### <a name="permissions"></a>Berechtigungen

|ScopeName|DisplayName|Beschreibung|Typ|Zustimmung des Administrators?|Behandelte Entitäten/APIs|
|-|-|-|-|-|-|
|`Teamwork.Migrate.All`|Migration zu Microsoft Teams verwalten|Erstellen und Verwalten von Ressourcen für die Migration zu Microsoft Teams|**Nur Anwendung**|**Ja**|`POST /teams`|

#### <a name="request-create-a-channel-in-migration-state"></a>Anforderung (Kanal im Migrationsstatus erstellen)

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

#### Error message

```http
400 Bad Request
```

* `createdDateTime`  für Zukunft festgelegt.
* `createdDateTime`  richtig angegeben `channelCreationMode`  , das Instanz-Attribut fehlt oder ist auf ungültigen Wert festgelegt.

## <a name="step-three-import-messages"></a>Schritt 3: Importieren von Nachrichten

Nachdem das Team und der Kanal erstellt wurden, können Sie mit dem Senden von Back-in-Time-Nachrichten mit den `createdDateTime`  und- `from`  Tasten im Anforderungstext beginnen. **Hinweis**: Nachrichten, `createdDateTime` die zuvor mit dem Nachrichtenthread importiert wurden `createdDateTime` , werden nicht unterstützt.

> [!NOTE]
> createdDateTime muss für Nachrichten in demselben Thread eindeutig sein.

#### <a name="request-post-message-that-is-text-only"></a>Request (Nachricht nur Text bereitstellen)

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

#### <a name="request-post-a-message-with-inline-image"></a>Anforderung (Senden einer Nachricht mit Inlinebild)

> **Hinweis**: in diesem Szenario gibt es keine speziellen Berechtigungs Bereiche, da die Anforderung Teil von Chat Message ist; Bereiche für Chat Message gelten auch hier.

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

## <a name="step-four-complete-migration-mode"></a>Schritt 4: vollständiger Migrationsmodus

Nachdem der Nachrichten Migrationsprozess abgeschlossen ist, werden sowohl das Team als auch der Kanal mithilfe der-Methode aus dem Migrationsmodus genommen  `completeMigration`  . In diesem Schritt werden die Team-und Kanal Ressourcen für die allgemeine Verwendung durch Teammitglieder geöffnet. Die Aktion ist an die `team` Instanz gebunden.

#### <a name="request-end-team-migration-mode"></a>Anforderung (Ende Team Migrationsmodus)

```http
POST https://graph.microsoft.com/beta/teams/teamId/completeMigration

```

#### <a name="response"></a>Antwort

```http
HTTP/1.1 204 NoContent
```

#### <a name="request-end-channel-migration-mode"></a>Request (End Channel-Migrationsmodus)

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

* Aktion mit dem Namen "a" `team` oder " `channel` nicht in" aufgerufen `migrationMode` .

## <a name="step-five-add-team-members"></a>Schritt 5: Hinzufügen von Teammitgliedern

Sie können ein Mitglied zu einem Team hinzufügen, [indem Sie die Benutzeroberfläche von Teams oder die](https://support.microsoft.com/office/add-members-to-a-team-in-teams-aff2249d-b456-4bc3-81e7-52327b6b38e9) [Add Member](/graph/api/group-post-members?view=graph-rest-beta&tabs=http&preserve-view=true) -API von Microsoft Graph verwenden:

#### <a name="request-add-member"></a>Request (Add Member)

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

* Sie können Nachrichten von Benutzern importieren, die sich nicht in Microsoft Teams befinden. **Hinweis**: Nachrichten, die für Benutzer importiert werden, die nicht im Mandanten vorhanden sind, können während der öffentlichen Vorschau nicht in den Teams-Client-oder Compliance-Portalen durchsucht werden.

* Nachdem die `completeMigration` Anforderung gestellt wurde, können Sie keine weiteren Nachrichten in das Team importieren.

* Teammitglieder können dem neuen Team nur hinzugefügt werden, nachdem die `completeMigration` Anforderung eine erfolgreiche Antwort zurückgegeben hat.

* Drosselung: Nachrichten werden mit 5 RPS pro Kanal importiert.

* Wenn Sie eine Korrektur an den Migrations Ergebnissen vornehmen müssen, müssen Sie das Team löschen und die Schritte wiederholen, um das Team zu erstellen und die Nachrichten erneut zu migrieren.

> [!NOTE]
> Derzeit sind Inline Bilder die einzige Art von Medien, die vom API-Schema für die Import Nachrichten unterstützt wird.

##### <a name="import-content-scope"></a>Inhaltsbereich importieren

|Im Bereich | Derzeit außerhalb des Bereichs|
|----------|--------------------------|
|Team-und Kanal Nachrichten|1:1-und Gruppenchatnachrichten|
|Erstellter Zeitpunkt der ursprünglichen Nachricht|Private Kanäle|
|Inline Bilder als Teil der Nachricht|Unter Erwähnungen|
|Links zu vorhandenen Dateien in SpO/OneDrive|Reaktionen|
|Nachrichten mit Rich-Text|Videos|
|Nachrichten Antwort Kette|Announcements|
|Verarbeitung mit hohem Durchsatz|Codeausschnitte|
||Adaptive Karten|
||Sticker|
||Emojis|
||Anführungszeichen|
||Cross-Posts zwischen Kanälen|

> [!div class="nextstepaction"]
>[Weitere Informationen zur Integration von Microsoft Graph und Microsoft Teams](/graph/teams-concept-overview)
