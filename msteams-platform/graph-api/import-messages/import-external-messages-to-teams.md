---
title: Verwenden von Microsoft Graph zum Importieren externer Plattformnachrichten in Teams
description: Beschreibt, wie Microsoft Graph zum Importieren von Nachrichten von einer externen Plattform in Teams
localization_priority: Normal
author: akjo
ms.author: lajanuar
ms.topic: Overview
keywords: Teams importieren Nachrichten-API-Diagramm Microsoft migrieren Migrationsbeitrag
ms.openlocfilehash: ad4e494264a72a3fdb1d926323bc2878d10cf44d
ms.sourcegitcommit: 623d81eb079d1842813265746a5fe0fe6311b196
ms.translationtype: MT
ms.contentlocale: de-DE
ms.lasthandoff: 06/22/2021
ms.locfileid: "53069137"
---
# <a name="import-third-party-platform-messages-to-teams-using-microsoft-graph"></a>Plattform-Nachrichten von Drittanbietern mithilfe von Microsoft Graph in Teams importieren

Mit Microsoft Graph können Sie den vorhandenen Nachrichtenverlauf und die Daten von Benutzern aus einem externen System in einen Teams Kanal migrieren. Durch die Aktivierung der Neugestaltung einer Drittanbieterplattform-Messaginghierarchie innerhalb Teams können Benutzer ihre Kommunikation nahtlos fortsetzen und ohne Unterbrechung fortfahren.

> [!NOTE] 
> Microsoft kann in Zukunft von Ihnen oder Ihren Kunden fordern, basierend auf der Menge der importierten Daten, zusätzliche Gebühren zu zahlen.

## <a name="import-overview"></a>Übersicht über den Import

Auf hoher Ebene besteht der Importvorgang aus folgenden Komponenten:

1. [Erstellen eines Teams mit einem Back-in-Time-Stempel](#step-one-create-a-team)
1. [Erstellen eines Kanals mit einem Back-in-TimeStamp](#step-two-create-a-channel) 
1. [Importieren externer Back-in-Time-Nachrichten](#step-three-import-messages)
1. [Abschließen des Migrationsprozesses für Team und Kanal](#step-four-complete-migration-mode)
1. [Hinzufügen von Teammitgliedern](#step-five-add-team-members)

## <a name="necessary-requirements"></a>Erforderliche Anforderungen

### <a name="analyze-and-prepare-message-data"></a>Analysieren und Vorbereiten von Nachrichtendaten

✔ Überprüfen Sie die Drittanbieterdaten, um zu entscheiden, was migriert wird.  
✔ Extrahieren der ausgewählten Daten aus dem Drittanbieter-Chatsystem.  
✔ ordnen Sie die Chatstruktur eines Drittanbieters der Teams Struktur zu.  
✔ Konvertieren von Importdaten in das für die Migration erforderliche Format.  

### <a name="set-up-your-office-365-tenant"></a>Einrichten des Office 365-Mandanten

✔ Stellen Sie sicher, dass für die Importdaten ein Office 365 Mandant vorhanden ist. Weitere Informationen zum Einrichten eines Office 365 Mandanten für Teams finden Sie unter [Vorbereiten Ihres Office 365 Mandanten.](../../concepts/build-and-test/prepare-your-o365-tenant.md)  
✔ Stellen Sie sicher, dass sich Teammitglieder in Azure Active Directory (AAD) befinden.  Weitere Informationen finden Sie unter [Hinzufügen eines neuen Benutzers](/azure/active-directory/fundamentals/add-users-azure-active-directory) zu Azure Active Directory.

## <a name="step-one-create-a-team"></a>Schritt 1: Erstellen eines Teams

Da vorhandene Daten migriert werden, sind die Aufrechterhaltung der ursprünglichen Nachrichtenzeitstempel und das Verhindern von Nachrichtenaktivitäten während des Migrationsprozesses entscheidend, um den vorhandenen Nachrichtenfluss des Benutzers in Teams neu zu erstellen. Dies wird wie folgt erreicht:

> [Erstellen Sie ein neues Team](/graph/api/team-post?view=graph-rest-beta&tabs=http&preserve-view=true) mit einem Back-in-Timestamp mithilfe der Teamressourceneigenschaft. `createdDateTime` Platzieren Sie das neue Team in einem speziellen Zustand, der `migration mode` Benutzer von den meisten Aktivitäten innerhalb des Teams ausschließt, bis der Migrationsprozess abgeschlossen ist. Schließen Sie das `teamCreationMode` Instanzattribut mit dem `migration` Wert in die POST-Anforderung ein, um das neue Team explizit als für die Migration erstellt zu identifizieren.  

> [!Note]
> Das `createdDateTime` Feld wird nur für Instanzen eines Teams oder Kanals ausgefüllt, die migriert wurden.

<!-- markdownlint-disable MD001 -->

#### <a name="permissions"></a>Berechtigungen

|ScopeName|DisplayName|Beschreibung|Typ|Administratorzustimmung?|Behandelte Entitäten/APIs|
|-|-|-|-|-|-|
|`Teamwork.Migrate.All`|Migration zu Microsoft Teams verwalten|Erstellen, Verwalten von Ressourcen für die Migration zu Microsoft Teams.|**Nur-Anwendung**|**Ja**|`POST /teams`|

#### <a name="request-create-a-team-in-migration-state"></a>Anforderung (Erstellen eines Teams im Migrationsstatus)

```http
POST https://graph.microsoft.com/v1.0/teams

Content-Type: application/json
{
  "@microsoft.graph.teamCreationMode": "migration",
  "template@odata.bind": "https://graph.microsoft.com/v1.0/teamsTemplates('standard')",
  "displayName": "My Sample Team",
  "description": "My Sample Team’s Description",
  "createdDateTime": "2020-03-14T11:22:17.043Z"
}
```

#### <a name="response"></a>Antwort

```http
HTTP/1.1 202 Accepted
Location: /teams/{team-id}/operations/{operation-id}
Content-Location: /teams/{team-id}
```

#### <a name="error-messages"></a>Fehlermeldungen

```http
400 Bad Request
```

* `createdDateTime`  für die Zukunft festgelegt.
* `createdDateTime`  richtig angegeben, aber `teamCreationMode`  das Instanzattribut fehlt oder ist auf einen ungültigen Wert festgelegt.

## <a name="step-two-create-a-channel"></a>Schritt 2: Erstellen eines Kanals

Das Erstellen eines Kanals für die importierten Nachrichten ähnelt dem Szenario "Team erstellen":

> [Erstellen Sie einen neuen Kanal](/graph/api/channel-post?view=graph-rest-v1.0&tabs=http&preserve-view=true) mit einem Back-in-Timestamp mithilfe der Kanalressourceneigenschaft. `createdDateTime` Platzieren Sie den neuen Kanal in einem speziellen Zustand, der `migration mode` Benutzer von den meisten Chataktivitäten innerhalb des Kanals ausschließt, bis der Migrationsprozess abgeschlossen ist.  Schließen Sie das `channelCreationMode` Instanzattribut mit dem `migration` Wert in die POST-Anforderung ein, um das neue Team explizit als für die Migration erstellt zu identifizieren.  
<!-- markdownlint-disable MD024 -->
#### <a name="permissions"></a>Berechtigungen

|ScopeName|DisplayName|Beschreibung|Typ|Administratorzustimmung?|Behandelte Entitäten/APIs|
|-|-|-|-|-|-|
|`Teamwork.Migrate.All`|Migration zu Microsoft Teams verwalten|Erstellen, Verwalten von Ressourcen für die Migration zu Microsoft Teams.|**Nur-Anwendung**|**Ja**|`POST /teams`|

#### <a name="request-create-a-channel-in-migration-state"></a>Anforderung (Erstellen eines Kanals im Migrationsstatus)

```http
POST https://graph.microsoft.com/v1.0/teams/{team-id}/channels

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
   "@odata.context":"https://graph.microsoft.com/v1.0/$metadata#teams('team-id')/channels/$entity",
   "id":"id-value",
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

Nachdem das Team und der Kanal erstellt wurden, können Sie mit dem Senden von Back-in-Time-Nachrichten mithilfe der `createdDateTime` `from`  Schlüssel im Anforderungstext beginnen. **HINWEIS:** Nachrichten, die mit `createdDateTime` früher als dem Nachrichtenthread importiert `createdDateTime` wurden, werden nicht unterstützt.

> [!NOTE]
> * `createdDateTime` muss nachrichtenübergreifend im selben Thread eindeutig sein.
> * `createdDateTime` unterstützt Zeitstempel mit Millisekunden-Genauigkeit. Wenn die eingehende Anforderungsnachricht beispielsweise den Wert `createdDateTime` *2020-09-16T05:50:31.0025302Z* hat, wird sie in *2020-09-16T05:50:31.002Z* konvertiert, wenn die Nachricht aufgenommen wird.

#### <a name="request-post-message-that-is-text-only"></a>Anforderung (NUR-TEXT-POST-Nachricht)

```http
POST https://graph.microsoft.com/v1.0/teams/team-id/channels/channel-id/messages

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
   "@odata.context":"https://graph.microsoft.com/v1.0/$metadata#teams('team-id')/channels('channel-id')/messages/$entity",
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

#### <a name="request-post-a-message-with-inline-image"></a>Anforderung (POST eine Nachricht mit Inlinebild)

> [!Note]
> In diesem Szenario gibt es keine speziellen Berechtigungsbereiche, da die Anforderung Teil von chatMessage ist. Hier gelten auch Bereiche für chatMessage.

```http
POST https://graph.microsoft.com/v1.0/teams/team-id/channels/channel-id/messages

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
    "@odata.context": "https://graph.microsoft.com/v1.0/$metadata#teams('team-id')/channels('channel-id')/messages/$entity",
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

Sobald der Nachrichtenmigrationsprozess abgeschlossen ist, werden sowohl das Team als auch der Kanal mithilfe der Methode aus dem Migrationsmodus  `completeMigration`  ausgeschlossen. In diesem Schritt werden die Team- und Kanalressourcen für die allgemeine Verwendung durch Teammitglieder geöffnet. Die Aktion ist an die `team` Instanz gebunden. Alle Kanäle müssen außerhalb des Migrationsmodus abgeschlossen werden, bevor das Team abgeschlossen werden kann.

#### <a name="request-end-channel-migration-mode"></a>Anforderung (Ende des Kanalmigrationsmodus)

```http
POST https://graph.microsoft.com/v1.0/teams/team-id/channels/channel-id/completeMigration

```

#### <a name="response"></a>Antwort

```http
HTTP/1.1 204 NoContent
```

#### <a name="request-end-team-migration-mode"></a>Anforderung (Teammigrationsmodus beenden)

```http
POST https://graph.microsoft.com/v1.0/teams/team-id/completeMigration
```

#### <a name="response"></a>Antwort

```http
HTTP/1.1 204 NoContent
```

* Aktion, die für eine `team` aufgerufen wird oder die sich nicht in `channel` `migrationMode` befindet.

## <a name="step-five-add-team-members"></a>Schritt 5: Hinzufügen von Teammitgliedern

Sie können ein Mitglied zu einem Team [hinzufügen, indem Sie die Teams-Benutzeroberfläche](https://support.microsoft.com/office/add-members-to-a-team-in-teams-aff2249d-b456-4bc3-81e7-52327b6b38e9) oder die Microsoft Graph [Mitglieder-API](/graph/api/group-post-members?view=graph-rest-beta&tabs=http&preserve-view=true) verwenden:

#### <a name="request-add-member"></a>Anforderung (Mitglied hinzufügen)

```http
POST https://graph.microsoft.com/beta/teams/{team-id}/members
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

* Sobald die `completeMigration` Anforderung gestellt wurde, können Sie keine weiteren Nachrichten in das Team importieren.

* Teammitglieder können dem neuen Team erst hinzugefügt werden, nachdem die `completeMigration` Anforderung eine erfolgreiche Antwort zurückgegeben hat.

* Einschränkung: Nachrichten werden mit 5 RPS pro Kanal importiert.

* Wenn Sie eine Korrektur an den Migrationsergebnissen vornehmen müssen, müssen Sie das Team löschen und die Schritte wiederholen, um das Team und den Kanal zu erstellen und die Nachrichten erneut zu migrieren.

> [!NOTE]
> Derzeit sind Inlinebilder der einzige Medientyp, der vom Importnachrichten-API-Schema unterstützt wird.

##### <a name="import-content-scope"></a>Importieren des Inhaltsbereichs

|In-Scope | Derzeit außerhalb des Gültigkeitsbereichs|
|----------|--------------------------|
|Team- und Kanalnachrichten|1:1- und Gruppenchatnachrichten|
|Erstellungszeitpunkt der ursprünglichen Nachricht|Private Kanäle|
|Inlinebilder als Teil der Nachricht|Bei Erwähnungen|
|Links zu vorhandenen Dateien in SPO/OneDrive|Reaktionen|
|Nachrichten mit Rich-Text|Videos|
|Nachrichtenantwortkette|Ankündigungen|
|Verarbeitung mit hohem Durchsatz|Codeausschnitte|
||Sticker|
||Emojis|
||Zitate|
||Beiträge zwischen Kanälen querstellen|


## <a name="see-also"></a>Siehe auch

[Weitere Informationen zur Integration von Microsoft Graph und Teams](/graph/teams-concept-overview)
